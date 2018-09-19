---
author: andrewleader
Description: This article describes how to send a local tile notification to a primary tile and a secondary tile using adaptive tile templates.
title: Senden einer lokalen Kachelbenachrichtigung
ms.assetid: D34B0514-AEC6-4C41-B318-F0985B51AF8A
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 7e91d4bd481188f4d29af68af2c4572b26d446ae
ms.sourcegitcommit: 68fcac3288d5698a13dbcbd57f51b30592f24860
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2018
ms.locfileid: "4059198"
---
# <a name="send-a-local-tile-notification"></a>Senden einer lokalen Kachelbenachrichtigung
 

Primäre App-Kacheln in Windows 10 werden im App-Manifest definiert, sekundäre Kacheln werden dagegen programmgesteuert erstellt und vom App-Code definiert. In diesem Artikel wird beschrieben, wie Sie eine lokale Benachrichtigung an eine primäre Kachel und an eine sekundäre Kachel mit adaptiven Kachelvorlagen senden. (Eine lokale Benachrichtigung wird vom App-Code gesendet, im Gegensatz zu Benachrichtigungen, die ein Webserver per Push oder Pull sendet.)

![Standardkachel und Kachel mit Benachrichtigung](images/sending-local-tile-01.png)

> [!NOTE] 
>Weitere Informationen über das [Erstellen von adaptiven Kacheln](create-adaptive-tiles.md) und das [Kachelinhaltsschema](../tiles-and-notifications/tile-schema.md).

 

## <a name="install-the-nuget-package"></a>Installieren des NuGet-Pakets


Wir empfehlen die Installation des [NuGet-Pakets aus der Benachrichtigungsbibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/), das Kachelnutzlasten mit Objekten anstelle von unformatiertem XML generiert und damit vieles vereinfacht.

Die Inlinecodebeispiele in diesem Artikel beziehen sich auf C# unter Verwendung der Benachrichtigungsbibliothek. (Wenn Sie eigenen XML-Code erstellen möchten, finden Sie am Ende des Artikels Codebeispiele ohne Benachrichtigungsbibliothek.)

## <a name="add-namespace-declarations"></a>Hinzufügen von Namespacedeklarationen


Um auf die Kachel-APIs zuzugreifen, beziehen Sie den [**Windows.UI.Notifications**](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications)-Namespace ein. Es wird darüber hinaus empfohlen, den **Microsoft.Toolkit.Uwp.Notifications**-Namespace einzubeziehen, damit Sie die Kachel-Hilfs-APIs nutzen können. (Sie müssen das NuGet-Paket aus der [Benachrichtigungsbibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) installieren, um auf diese APIs zugreifen zu können.)

```csharp
using Windows.UI.Notifications;
using Microsoft.Toolkit.Uwp.Notifications; // Notifications library
```

## <a name="create-the-notification-content"></a>Erstellen des Benachrichtigungsinhalts


In Windows10 werden Kachelnutzlasten mit adaptiven Kachelvorlagen definiert, mit denen Sie benutzerdefinierte visuelle Layouts für Ihre Benachrichtigungen erstellen können. (Informationen darüber, was mit adaptiven Kacheln möglich ist, finden Sie unter [Erstellen adaptiver Kacheln und Vorlagen für adaptive Kacheln](create-adaptive-tiles.md).)

Dieses Codebeispiel erstellt adaptive Kachelinhalte für mittelgroße und breite Kacheln.

```csharp
// In a real app, these would be initialized with actual data
string from = "Jennifer Parker";
string subject = "Photos from our trip";
string body = "Check out these awesome photos I took while in New Zealand!";
 
 
// Construct the tile content
TileContent content = new TileContent()
{
    Visual = new TileVisual()
    {
        TileMedium = new TileBinding()
        {
            Content = new TileBindingContentAdaptive()
            {
                Children =
                {
                    new AdaptiveText()
                    {
                        Text = from
                    },

                    new AdaptiveText()
                    {
                        Text = subject,
                        HintStyle = AdaptiveTextStyle.CaptionSubtle
                    },

                    new AdaptiveText()
                    {
                        Text = body,
                        HintStyle = AdaptiveTextStyle.CaptionSubtle
                    }
                }
            }
        },

        TileWide = new TileBinding()
        {
            Content = new TileBindingContentAdaptive()
            {
                Children =
                {
                    new AdaptiveText()
                    {
                        Text = from,
                        HintStyle = AdaptiveTextStyle.Subtitle
                    },

                    new AdaptiveText()
                    {
                        Text = subject,
                        HintStyle = AdaptiveTextStyle.CaptionSubtle
                    },

                    new AdaptiveText()
                    {
                        Text = body,
                        HintStyle = AdaptiveTextStyle.CaptionSubtle
                    }
                }
            }
        }
    }
};
```

Auf einer mittelgroßen Kachel wird der Inhalt der Benachrichtigung wie folgt angezeigt:

![Inhalt der Benachrichtigung auf einer mittelgroßen Kachel](images/sending-local-tile-02.png)

## <a name="create-the-notification"></a>Erstellen der Benachrichtigung


Wenn Sie den Inhalt der Benachrichtigung erstellt haben, müssen Sie eine neue [**TileNotification**](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.TileNotification)-Klasse erstellen. Der **TileNotification**-Konstruktor akzeptiert ein Windows-Runtime-[**XmlDocument**](https://docs.microsoft.com/uwp/api/windows.data.xml.dom.xmldocument)-Objekt, das Sie aus der **TileContent.GetXml**-Methode abrufen können, wenn Sie die [Benachrichtigungsbibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) verwenden.

Mit diesem Codebeispiel wird eine Benachrichtigung für eine neue Kachel erstellt.

```csharp
// Create the tile notification
var notification = new TileNotification(content.GetXml());
```

## <a name="set-an-expiration-time-for-the-notification-optional"></a>Festlegen einer Ablaufzeit für die Benachrichtigung (optional)


Standardmäßig laufen lokale Kachel- und Signalbenachrichtigungen nicht ab, während Pushbenachrichtigungen sowie regelmäßige und geplante Benachrichtigungen nach drei Tagen ablaufen. Weil Kachelinhalt nur so lange wie notwendig beibehalten werden soll, sollten Sie, insbesondere für lokale Kachel- und Signalbenachrichtigungen, eine Gültigkeitsdauer festlegen, die für Ihre App sinnvoll ist.

In diesem Codebeispiel wird eine Benachrichtigung erstellt, die nach zehn Minuten abläuft und von der Kachel entfernt wird.

```csharp
tileNotification.ExpirationTime = DateTimeOffset.UtcNow.AddMinutes(10);
```

## <a name="send-the-notification"></a>Senden der Benachrichtigung


Das lokale Senden einer Kachelbenachrichtigung ist einfach, das Senden der Benachrichtigung an eine primäre oder sekundäre Kachel weicht aber etwas davon ab.

**Primäre Kachel**

Verwenden Sie zum Senden einer Benachrichtigung an eine primäre Kachel den [**TileUpdateManager**](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.TileUpdateManager), um für die primäre Kachel eine Kachelaktualisierung zu erstellen und die Benachrichtigung durch Aufrufen von „Update” zu senden. Die primäre Kachel Ihrer App ist immer vorhanden, selbst wenn sie nicht sichtbar ist. Daher können Sie Benachrichtigungen an die Kachel senden, auch wenn sie nicht angeheftet ist. Wenn der Benutzer später die primäre Kachel anheftet, werden die Benachrichtigungen, die Sie gesendet haben, angezeigt.

Mit diesem Codebeispiel wird eine Benachrichtigung an eine primäre Kachel gesendet.


```csharp
// Send the notification to the primary tile
TileUpdateManager.CreateTileUpdaterForApplication().Update(notification);
```

**Sekundäre Kachel**

Um eine Benachrichtigung an eine sekundäre Kachel zu senden, müssen Sie zuerst sicherstellen Sie, dass die sekundäre Kachel vorhanden ist. Wenn Sie versuchen, eine Kachelaktualisierung für eine sekundäre Kachel zu erstellen, die nicht vorhanden ist (z.B. wenn der Benutzer die sekundäre Kachel gelöst hat), wird eine Ausnahme ausgelöst. Sie können mit [**SecondaryTile.Exists**](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_Exists_System_String_)(tileId) ermitteln, ob die sekundäre Kachel angeheftet ist, und dann eine Kachelaktualisierung für eine sekundäre Kachel erstellen und die Benachrichtigung senden.

Mit diesem Codebeispiel wird eine Benachrichtigung an eine sekundäre Kachel gesendet.

```csharp
// If the secondary tile is pinned
if (SecondaryTile.Exists("MySecondaryTile"))
{
    // Get its updater
    var updater = TileUpdateManager.CreateTileUpdaterForSecondaryTile("MySecondaryTile");
 
    // And send the notification
    updater.Update(notification);
}
```

![Standardkachel und Kachel mit Benachrichtigung](images/sending-local-tile-01.png)

## <a name="clear-notifications-on-the-tile-optional"></a>Löschen von Benachrichtigungen auf der Kachel (optional)


In den meisten Fällen sollten Sie eine Benachrichtigung löschen, sobald der Benutzer mit diesem Inhalt interagiert hat. Zum Beispiel sollten Sie alle Benachrichtigungen auf der Kachel löschen, wenn der Benutzer die App startet. Wenn die Benachrichtigungen zeitabhängig sind, sollten Sie eine Ablaufzeit für die Benachrichtigung festlegen, anstatt sie explizit zu löschen.

In diesem Codebeispiel wird die Kachelbenachrichtigung für die primäre Kachel gelöscht. Sie können diesen Vorgang auf sekundäre Kacheln anwenden, indem Sie für die sekundäre Kachel eine Kachelaktualisierung erstellen.

```csharp
TileUpdateManager.CreateTileUpdaterForApplication().Clear();
```

Bei einer Kachel mit aktivierter Benachrichtigungswarteschlange und Benachrichtigungen in der Warteschlange wird durch Aufrufen der Clear-Methode die Warteschlange gelöscht. Es ist aber nicht möglich ist, eine Benachrichtigung über den Server Ihrer App zu löschen; Benachrichtigungen können nur durch lokalen App-Code gelöscht werden.

Durch regelmäßige oder Push-Benachrichtigungen können nur neue Benachrichtigungen hinzugefügt oder vorhandene Benachrichtigungen ersetzt werden. Mit einem lokalen Aufruf der Clear-Methode wird die Kachel gelöscht, unabhängig davon, ob die Benachrichtigungen selbst per Push, regelmäßig oder lokal gesendet wurden. Geplante Benachrichtigungen, die noch nicht angezeigt wurden, werden durch diese Methode nicht gelöscht.

![Kachel mit Benachrichtigung und Kachel nach dem Löschen](images/sending-local-tile-03.png)

## <a name="next-steps"></a>Nächste Schritte


**Verwenden der Benachrichtigungswarteschlange**

Nachdem Sie Ihre erste Kachelaktualisierung ausgeführt haben, können Sie die Funktionalität der Kachel erweitern, indem Sie eine [Benachrichtigungswarteschlange](https://msdn.microsoft.com/library/windows/apps/xaml/hh868234) aktivieren.

**Andere Methoden für die Benachrichtigungsübermittlung**

In diesem Artikel wird erläutert, wie die Kachelaktualisierung als Benachrichtigung gesendet werden kann. Informationen zu anderen Methoden der Benachrichtigungsübermittlung, einschließlich geplanter, regelmäßiger und Push-Benachrichtigungen, finden Sie unter [Zustellen von Benachrichtigungen](choosing-a-notification-delivery-method.md).

**XmlEncode-Übermittlungsmethode**

Wenn Sie die [Benachrichtigungsbibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) nicht verwenden, bietet diese Methode für die Benachrichtigungsübermittlung eine weitere Alternative.


```csharp
public string XmlEncode(string text)
{
    StringBuilder builder = new StringBuilder();
    using (var writer = XmlWriter.Create(builder))
    {
        writer.WriteString(text);
    }

    return builder.ToString();
}
```

## <a name="code-examples-without-notifications-library"></a>Codebeispiele ohne Benachrichtigungsbibliothek


Wenn Sie mit unformatiertem XML anstatt mit dem NuGet-Paket aus der [Benachrichtigungsbibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) arbeiten möchten, verwenden Sie diese alternativen Codebeispiele für die ersten drei Beispiele in diesem Artikel. Die restlichen Codebeispiele können entweder mit der [Benachrichtigungsbibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) oder mit unformatiertem XML verwendet werden.

Hinzufügen von Namespacedeklarationen

```csharp
using Windows.UI.Notifications;
using Windows.Data.Xml.Dom;
```

Erstellen des Benachrichtigungsinhalts

```csharp
// In a real app, these would be initialized with actual data
string from = "Jennifer Parker";
string subject = "Photos from our trip";
string body = "Check out these awesome photos I took while in New Zealand!";
 
 
// TODO - all values need to be XML escaped
 
 
// Construct the tile content as a string
string content = $@"
<tile>
    <visual>
 
        <binding template='TileMedium'>
            <text>{from}</text>
            <text hint-style='captionSubtle'>{subject}</text>
            <text hint-style='captionSubtle'>{body}</text>
        </binding>
 
        <binding template='TileWide'>
            <text hint-style='subtitle'>{from}</text>
            <text hint-style='captionSubtle'>{subject}</text>
            <text hint-style='captionSubtle'>{body}</text>
        </binding>
 
    </visual>
</tile>";
```

Erstellen der Benachrichtigung

```csharp
// Load the string into an XmlDocument
XmlDocument doc = new XmlDocument();
doc.LoadXml(content);
 
// Then create the tile notification
var notification = new TileNotification(doc);
```

## <a name="related-topics"></a>Verwandte Themen

* [Erstellen adaptiver Kacheln](create-adaptive-tiles.md)
* [Kachelinhaltsschema](../tiles-and-notifications/tile-schema.md)
* [Benachrichtigungsbibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/)
* [Vollständiges Codebeispiel auf GitHub](https://github.com/WindowsNotifications/quickstart-sending-local-tile-win10)
* [**Windows.UI.Notifications-Namespace**](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications)
* [So wird’s gemacht: Verwenden der Benachrichtigungswarteschlange (XAML)](https://msdn.microsoft.com/library/windows/apps/xaml/hh868234)
* [Zustellen von Benachrichtigungen](choosing-a-notification-delivery-method.md)
 

 




