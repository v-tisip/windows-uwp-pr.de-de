---
author: andrewleader
Description: This article describes how to send a local tile notification to a primary tile and a secondary tile using adaptive tile templates.
title: Senden einer lokalen Kachelbenachrichtigung
ms.assetid: D34B0514-AEC6-4C41-B318-F0985B51AF8A
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 76af980aeb759905259a043fdb9b4b828a90d819
ms.sourcegitcommit: b7e3d222e229cdbf04e837fcb94fb7d84a93de09
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5594612"
---
# <a name="send-a-local-tile-notification"></a><span data-ttu-id="d620e-103">Senden einer lokalen Kachelbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="d620e-103">Send a local tile notification</span></span>
 

<span data-ttu-id="d620e-104">Primäre app-Kacheln in Windows 10 werden in Ihrem app-Manifest definiert, während sekundäre Kacheln programmgesteuert erstellt und vom app-Code definiert sind.</span><span class="sxs-lookup"><span data-stu-id="d620e-104">Primary app tiles in Windows10 are defined in your app manifest, while secondary tiles are programmatically created and defined by your app code.</span></span> <span data-ttu-id="d620e-105">In diesem Artikel wird beschrieben, wie Sie eine lokale Benachrichtigung an eine primäre Kachel und an eine sekundäre Kachel mit adaptiven Kachelvorlagen senden.</span><span class="sxs-lookup"><span data-stu-id="d620e-105">This article describes how to send a local tile notification to a primary tile and a secondary tile using adaptive tile templates.</span></span> <span data-ttu-id="d620e-106">(Eine lokale Benachrichtigung wird vom App-Code gesendet, im Gegensatz zu Benachrichtigungen, die ein Webserver per Push oder Pull sendet.)</span><span class="sxs-lookup"><span data-stu-id="d620e-106">(A local notification is one that's sent from app code as opposed to one that's pushed or pulled from a web server.)</span></span>

![Standardkachel und Kachel mit Benachrichtigung](images/sending-local-tile-01.png)

> [!NOTE] 
><span data-ttu-id="d620e-108">Weitere Informationen über das [Erstellen von adaptiven Kacheln](create-adaptive-tiles.md) und das [Kachelinhaltsschema](../tiles-and-notifications/tile-schema.md).</span><span class="sxs-lookup"><span data-stu-id="d620e-108">Learn about [creating adaptive tiles](create-adaptive-tiles.md) and [tile content schema](../tiles-and-notifications/tile-schema.md).</span></span>

 

## <a name="install-the-nuget-package"></a><span data-ttu-id="d620e-109">Installieren des NuGet-Pakets</span><span class="sxs-lookup"><span data-stu-id="d620e-109">Install the NuGet package</span></span>


<span data-ttu-id="d620e-110">Wir empfehlen die Installation des [NuGet-Pakets aus der Benachrichtigungsbibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/), das Kachelnutzlasten mit Objekten anstelle von unformatiertem XML generiert und damit vieles vereinfacht.</span><span class="sxs-lookup"><span data-stu-id="d620e-110">We recommend installing the [Notifications library NuGet package](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/), which simplifies things by generating tile payloads with objects instead of raw XML.</span></span>

<span data-ttu-id="d620e-111">Die Inlinecodebeispiele in diesem Artikel beziehen sich auf C# unter Verwendung der Benachrichtigungsbibliothek.</span><span class="sxs-lookup"><span data-stu-id="d620e-111">The inline code examples in this article are for C# using the Notifications library.</span></span> <span data-ttu-id="d620e-112">(Wenn Sie eigenen XML-Code erstellen möchten, finden Sie am Ende des Artikels Codebeispiele ohne Benachrichtigungsbibliothek.)</span><span class="sxs-lookup"><span data-stu-id="d620e-112">(If you'd prefer to create your own XML, you can find code examples without the Notifications library toward the end of the article.)</span></span>

## <a name="add-namespace-declarations"></a><span data-ttu-id="d620e-113">Hinzufügen von Namespacedeklarationen</span><span class="sxs-lookup"><span data-stu-id="d620e-113">Add namespace declarations</span></span>


<span data-ttu-id="d620e-114">Um auf die Kachel-APIs zuzugreifen, beziehen Sie den [**Windows.UI.Notifications**](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications)-Namespace ein.</span><span class="sxs-lookup"><span data-stu-id="d620e-114">To access the tile APIs, include the [**Windows.UI.Notifications**](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications) namespace.</span></span> <span data-ttu-id="d620e-115">Es wird darüber hinaus empfohlen, den **Microsoft.Toolkit.Uwp.Notifications**-Namespace einzubeziehen, damit Sie die Kachel-Hilfs-APIs nutzen können. (Sie müssen das NuGet-Paket aus der [Benachrichtigungsbibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) installieren, um auf diese APIs zugreifen zu können.)</span><span class="sxs-lookup"><span data-stu-id="d620e-115">We also recommend including the **Microsoft.Toolkit.Uwp.Notifications** namespace so that you can take advantage of our tile helper APIs (you must install the [Notifications library](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) NuGet package to access these APIs).</span></span>

```csharp
using Windows.UI.Notifications;
using Microsoft.Toolkit.Uwp.Notifications; // Notifications library
```

## <a name="create-the-notification-content"></a><span data-ttu-id="d620e-116">Erstellen des Benachrichtigungsinhalts</span><span class="sxs-lookup"><span data-stu-id="d620e-116">Create the notification content</span></span>


<span data-ttu-id="d620e-117">In Windows 10 werden kachelnutzlasten mit Vorlagen für adaptive Kacheln, die Ihnen ermöglichen, erstellen Sie benutzerdefinierte visuelle Layouts für Ihre Benachrichtigungen definiert.</span><span class="sxs-lookup"><span data-stu-id="d620e-117">In Windows10, tile payloads are defined using adaptive tile templates, which allow you to create custom visual layouts for your notifications.</span></span> <span data-ttu-id="d620e-118">(Informationen darüber, was mit adaptiven Kacheln möglich ist, finden Sie unter [Erstellen adaptiver Kacheln und Vorlagen für adaptive Kacheln](create-adaptive-tiles.md).)</span><span class="sxs-lookup"><span data-stu-id="d620e-118">(To learn what's possible with adaptive tiles, see [Create adaptive tiles](create-adaptive-tiles.md).)</span></span>

<span data-ttu-id="d620e-119">Dieses Codebeispiel erstellt adaptive Kachelinhalte für mittelgroße und breite Kacheln.</span><span class="sxs-lookup"><span data-stu-id="d620e-119">This code example creates adaptive tile content for medium and wide tiles.</span></span>

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

<span data-ttu-id="d620e-120">Auf einer mittelgroßen Kachel wird der Inhalt der Benachrichtigung wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="d620e-120">The notification content looks like the following when displayed on a medium tile:</span></span>

![Inhalt der Benachrichtigung auf einer mittelgroßen Kachel](images/sending-local-tile-02.png)

## <a name="create-the-notification"></a><span data-ttu-id="d620e-122">Erstellen der Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="d620e-122">Create the notification</span></span>


<span data-ttu-id="d620e-123">Wenn Sie den Inhalt der Benachrichtigung erstellt haben, müssen Sie eine neue [**TileNotification**](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.TileNotification)-Klasse erstellen.</span><span class="sxs-lookup"><span data-stu-id="d620e-123">Once you have your notification content, you'll need to create a new [**TileNotification**](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.TileNotification).</span></span> <span data-ttu-id="d620e-124">Der **TileNotification**-Konstruktor akzeptiert ein Windows-Runtime-[**XmlDocument**](https://docs.microsoft.com/uwp/api/windows.data.xml.dom.xmldocument)-Objekt, das Sie aus der **TileContent.GetXml**-Methode abrufen können, wenn Sie die [Benachrichtigungsbibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) verwenden.</span><span class="sxs-lookup"><span data-stu-id="d620e-124">The **TileNotification** constructor takes a Windows Runtime [**XmlDocument**](https://docs.microsoft.com/uwp/api/windows.data.xml.dom.xmldocument) object, which you can obtain from the **TileContent.GetXml** method if you're using the [Notifications library](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/).</span></span>

<span data-ttu-id="d620e-125">Mit diesem Codebeispiel wird eine Benachrichtigung für eine neue Kachel erstellt.</span><span class="sxs-lookup"><span data-stu-id="d620e-125">This code example creates a notification for a new tile.</span></span>

```csharp
// Create the tile notification
var notification = new TileNotification(content.GetXml());
```

## <a name="set-an-expiration-time-for-the-notification-optional"></a><span data-ttu-id="d620e-126">Festlegen einer Ablaufzeit für die Benachrichtigung (optional)</span><span class="sxs-lookup"><span data-stu-id="d620e-126">Set an expiration time for the notification (optional)</span></span>


<span data-ttu-id="d620e-127">Standardmäßig laufen lokale Kachel- und Signalbenachrichtigungen nicht ab, während Pushbenachrichtigungen sowie regelmäßige und geplante Benachrichtigungen nach drei Tagen ablaufen.</span><span class="sxs-lookup"><span data-stu-id="d620e-127">By default, local tile and badge notifications don't expire, while push, periodic, and scheduled notifications expire after three days.</span></span> <span data-ttu-id="d620e-128">Weil Kachelinhalt nur so lange wie notwendig beibehalten werden soll, sollten Sie, insbesondere für lokale Kachel- und Signalbenachrichtigungen, eine Gültigkeitsdauer festlegen, die für Ihre App sinnvoll ist.</span><span class="sxs-lookup"><span data-stu-id="d620e-128">Because tile content shouldn't persist longer than necessary, it's a best practice to set an expiration time that makes sense for your app, especially on local tile and badge notifications.</span></span>

<span data-ttu-id="d620e-129">In diesem Codebeispiel wird eine Benachrichtigung erstellt, die nach zehn Minuten abläuft und von der Kachel entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="d620e-129">This code example creates a notification that expires and will be removed from the tile after ten minutes.</span></span>

```csharp
tileNotification.ExpirationTime = DateTimeOffset.UtcNow.AddMinutes(10);
```

## <a name="send-the-notification"></a><span data-ttu-id="d620e-130">Senden der Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="d620e-130">Send the notification</span></span>


<span data-ttu-id="d620e-131">Das lokale Senden einer Kachelbenachrichtigung ist einfach, das Senden der Benachrichtigung an eine primäre oder sekundäre Kachel weicht aber etwas davon ab.</span><span class="sxs-lookup"><span data-stu-id="d620e-131">Although locally sending a tile notification is simple, sending the notification to a primary or secondary tile is a bit different.</span></span>

**<span data-ttu-id="d620e-132">Primäre Kachel</span><span class="sxs-lookup"><span data-stu-id="d620e-132">Primary tile</span></span>**

<span data-ttu-id="d620e-133">Verwenden Sie zum Senden einer Benachrichtigung an eine primäre Kachel den [**TileUpdateManager**](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.TileUpdateManager), um für die primäre Kachel eine Kachelaktualisierung zu erstellen und die Benachrichtigung durch Aufrufen von „Update” zu senden.</span><span class="sxs-lookup"><span data-stu-id="d620e-133">To send a notification to a primary tile, use the [**TileUpdateManager**](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.TileUpdateManager) to create a tile updater for the primary tile, and send the notification by calling "Update".</span></span> <span data-ttu-id="d620e-134">Die primäre Kachel Ihrer App ist immer vorhanden, selbst wenn sie nicht sichtbar ist. Daher können Sie Benachrichtigungen an die Kachel senden, auch wenn sie nicht angeheftet ist.</span><span class="sxs-lookup"><span data-stu-id="d620e-134">Regardless of whether it's visible, your app's primary tile always exists, so you can send notifications to it even when it's not pinned.</span></span> <span data-ttu-id="d620e-135">Wenn der Benutzer später die primäre Kachel anheftet, werden die Benachrichtigungen, die Sie gesendet haben, angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d620e-135">If the user pins your primary tile later, the notifications that you sent will appear then.</span></span>

<span data-ttu-id="d620e-136">Mit diesem Codebeispiel wird eine Benachrichtigung an eine primäre Kachel gesendet.</span><span class="sxs-lookup"><span data-stu-id="d620e-136">This code example sends a notification to a primary tile.</span></span>


```csharp
// Send the notification to the primary tile
TileUpdateManager.CreateTileUpdaterForApplication().Update(notification);
```

**<span data-ttu-id="d620e-137">Sekundäre Kachel</span><span class="sxs-lookup"><span data-stu-id="d620e-137">Secondary tile</span></span>**

<span data-ttu-id="d620e-138">Um eine Benachrichtigung an eine sekundäre Kachel zu senden, müssen Sie zuerst sicherstellen Sie, dass die sekundäre Kachel vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="d620e-138">To send a notification to a secondary tile, first make sure that the secondary tile exists.</span></span> <span data-ttu-id="d620e-139">Wenn Sie versuchen, eine Kachelaktualisierung für eine sekundäre Kachel zu erstellen, die nicht vorhanden ist (z.B. wenn der Benutzer die sekundäre Kachel gelöst hat), wird eine Ausnahme ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="d620e-139">If you try to create a tile updater for a secondary tile that doesn't exist (for example, if the user unpinned the secondary tile), an exception will be thrown.</span></span> <span data-ttu-id="d620e-140">Sie können mit [**SecondaryTile.Exists**](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_Exists_System_String_)(tileId) ermitteln, ob die sekundäre Kachel angeheftet ist, und dann eine Kachelaktualisierung für eine sekundäre Kachel erstellen und die Benachrichtigung senden.</span><span class="sxs-lookup"><span data-stu-id="d620e-140">You can use [**SecondaryTile.Exists**](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_Exists_System_String_)(tileId) to discover if your secondary tile is pinned, and then create a tile updater for the secondary tile and send the notification.</span></span>

<span data-ttu-id="d620e-141">Mit diesem Codebeispiel wird eine Benachrichtigung an eine sekundäre Kachel gesendet.</span><span class="sxs-lookup"><span data-stu-id="d620e-141">This code example sends a notification to a secondary tile.</span></span>

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

## <a name="clear-notifications-on-the-tile-optional"></a><span data-ttu-id="d620e-143">Löschen von Benachrichtigungen auf der Kachel (optional)</span><span class="sxs-lookup"><span data-stu-id="d620e-143">Clear notifications on the tile (optional)</span></span>


<span data-ttu-id="d620e-144">In den meisten Fällen sollten Sie eine Benachrichtigung löschen, sobald der Benutzer mit diesem Inhalt interagiert hat.</span><span class="sxs-lookup"><span data-stu-id="d620e-144">In most cases, you should clear a notification once the user has interacted with that content.</span></span> <span data-ttu-id="d620e-145">Zum Beispiel sollten Sie alle Benachrichtigungen auf der Kachel löschen, wenn der Benutzer die App startet.</span><span class="sxs-lookup"><span data-stu-id="d620e-145">For example, when the user launches your app, you might want to clear all the notifications from the tile.</span></span> <span data-ttu-id="d620e-146">Wenn die Benachrichtigungen zeitabhängig sind, sollten Sie eine Ablaufzeit für die Benachrichtigung festlegen, anstatt sie explizit zu löschen.</span><span class="sxs-lookup"><span data-stu-id="d620e-146">If your notifications are time-bound, we recommend that you set an expiration time on the notification instead of explicitly clearing the notification.</span></span>

<span data-ttu-id="d620e-147">In diesem Codebeispiel wird die Kachelbenachrichtigung für die primäre Kachel gelöscht.</span><span class="sxs-lookup"><span data-stu-id="d620e-147">This code example clears the tile notification for the primary tile.</span></span> <span data-ttu-id="d620e-148">Sie können diesen Vorgang auf sekundäre Kacheln anwenden, indem Sie für die sekundäre Kachel eine Kachelaktualisierung erstellen.</span><span class="sxs-lookup"><span data-stu-id="d620e-148">You can do the same for secondary tiles by creating a tile updater for the secondary tile.</span></span>

```csharp
TileUpdateManager.CreateTileUpdaterForApplication().Clear();
```

<span data-ttu-id="d620e-149">Bei einer Kachel mit aktivierter Benachrichtigungswarteschlange und Benachrichtigungen in der Warteschlange wird durch Aufrufen der Clear-Methode die Warteschlange gelöscht.</span><span class="sxs-lookup"><span data-stu-id="d620e-149">For a tile with the notification queue enabled and notifications in the queue, calling the Clear method empties the queue.</span></span> <span data-ttu-id="d620e-150">Es ist aber nicht möglich ist, eine Benachrichtigung über den Server Ihrer App zu löschen; Benachrichtigungen können nur durch lokalen App-Code gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="d620e-150">You can't, however, clear a notification via your app's server; only the local app code can clear notifications.</span></span>

<span data-ttu-id="d620e-151">Durch regelmäßige oder Push-Benachrichtigungen können nur neue Benachrichtigungen hinzugefügt oder vorhandene Benachrichtigungen ersetzt werden.</span><span class="sxs-lookup"><span data-stu-id="d620e-151">Periodic or push notifications can only add new notifications or replace existing notifications.</span></span> <span data-ttu-id="d620e-152">Mit einem lokalen Aufruf der Clear-Methode wird die Kachel gelöscht, unabhängig davon, ob die Benachrichtigungen selbst per Push, regelmäßig oder lokal gesendet wurden.</span><span class="sxs-lookup"><span data-stu-id="d620e-152">A local call to the Clear method will clear the tile whether or not the notifications themselves came via push, periodic, or local.</span></span> <span data-ttu-id="d620e-153">Geplante Benachrichtigungen, die noch nicht angezeigt wurden, werden durch diese Methode nicht gelöscht.</span><span class="sxs-lookup"><span data-stu-id="d620e-153">Scheduled notifications that haven't yet appeared are not cleared by this method.</span></span>

![Kachel mit Benachrichtigung und Kachel nach dem Löschen](images/sending-local-tile-03.png)

## <a name="next-steps"></a><span data-ttu-id="d620e-155">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="d620e-155">Next steps</span></span>


**<span data-ttu-id="d620e-156">Verwenden der Benachrichtigungswarteschlange</span><span class="sxs-lookup"><span data-stu-id="d620e-156">Using the notification queue</span></span>**

<span data-ttu-id="d620e-157">Nachdem Sie Ihre erste Kachelaktualisierung ausgeführt haben, können Sie die Funktionalität der Kachel erweitern, indem Sie eine [Benachrichtigungswarteschlange](https://msdn.microsoft.com/library/windows/apps/xaml/hh868234) aktivieren.</span><span class="sxs-lookup"><span data-stu-id="d620e-157">Now that you have done your first tile update, you can expand the functionality of the tile by enabling a [notification queue](https://msdn.microsoft.com/library/windows/apps/xaml/hh868234).</span></span>

**<span data-ttu-id="d620e-158">Andere Methoden für die Benachrichtigungsübermittlung</span><span class="sxs-lookup"><span data-stu-id="d620e-158">Other notification delivery methods</span></span>**

<span data-ttu-id="d620e-159">In diesem Artikel wird erläutert, wie die Kachelaktualisierung als Benachrichtigung gesendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="d620e-159">This article shows you how to send the tile update as a notification.</span></span> <span data-ttu-id="d620e-160">Informationen zu anderen Methoden der Benachrichtigungsübermittlung, einschließlich geplanter, regelmäßiger und Push-Benachrichtigungen, finden Sie unter [Zustellen von Benachrichtigungen](choosing-a-notification-delivery-method.md).</span><span class="sxs-lookup"><span data-stu-id="d620e-160">To explore other methods of notification delivery, including scheduled, periodic, and push, see [Delivering notifications](choosing-a-notification-delivery-method.md).</span></span>

**<span data-ttu-id="d620e-161">XmlEncode-Übermittlungsmethode</span><span class="sxs-lookup"><span data-stu-id="d620e-161">XmlEncode delivery method</span></span>**

<span data-ttu-id="d620e-162">Wenn Sie die [Benachrichtigungsbibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) nicht verwenden, bietet diese Methode für die Benachrichtigungsübermittlung eine weitere Alternative.</span><span class="sxs-lookup"><span data-stu-id="d620e-162">If you're not using the [Notifications library](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/), this notification delivery method is another alternative.</span></span>


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

## <a name="code-examples-without-notifications-library"></a><span data-ttu-id="d620e-163">Codebeispiele ohne Benachrichtigungsbibliothek</span><span class="sxs-lookup"><span data-stu-id="d620e-163">Code examples without Notifications library</span></span>


<span data-ttu-id="d620e-164">Wenn Sie mit unformatiertem XML anstatt mit dem NuGet-Paket aus der [Benachrichtigungsbibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) arbeiten möchten, verwenden Sie diese alternativen Codebeispiele für die ersten drei Beispiele in diesem Artikel.</span><span class="sxs-lookup"><span data-stu-id="d620e-164">If you prefer to work with raw XML instead of the [Notifications library](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) NuGet package, use these alternate code examples to first three examples provided in this article.</span></span> <span data-ttu-id="d620e-165">Die restlichen Codebeispiele können entweder mit der [Benachrichtigungsbibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) oder mit unformatiertem XML verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="d620e-165">The rest of the code examples can be used either with the [Notifications library](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) or with raw XML.</span></span>

<span data-ttu-id="d620e-166">Hinzufügen von Namespacedeklarationen</span><span class="sxs-lookup"><span data-stu-id="d620e-166">Add namespace declarations</span></span>

```csharp
using Windows.UI.Notifications;
using Windows.Data.Xml.Dom;
```

<span data-ttu-id="d620e-167">Erstellen des Benachrichtigungsinhalts</span><span class="sxs-lookup"><span data-stu-id="d620e-167">Create the notification content</span></span>

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

<span data-ttu-id="d620e-168">Erstellen der Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="d620e-168">Create the notification</span></span>

```csharp
// Load the string into an XmlDocument
XmlDocument doc = new XmlDocument();
doc.LoadXml(content);
 
// Then create the tile notification
var notification = new TileNotification(doc);
```

## <a name="related-topics"></a><span data-ttu-id="d620e-169">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="d620e-169">Related topics</span></span>

* [<span data-ttu-id="d620e-170">Erstellen adaptiver Kacheln</span><span class="sxs-lookup"><span data-stu-id="d620e-170">Create adaptive tiles</span></span>](create-adaptive-tiles.md)
* [<span data-ttu-id="d620e-171">Kachelinhaltsschema</span><span class="sxs-lookup"><span data-stu-id="d620e-171">Tile content schema</span></span>](../tiles-and-notifications/tile-schema.md)
* [<span data-ttu-id="d620e-172">Benachrichtigungsbibliothek</span><span class="sxs-lookup"><span data-stu-id="d620e-172">Notifications library</span></span>](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/)
* [<span data-ttu-id="d620e-173">Vollständiges Codebeispiel auf GitHub</span><span class="sxs-lookup"><span data-stu-id="d620e-173">Full code sample on GitHub</span></span>](https://github.com/WindowsNotifications/quickstart-sending-local-tile-win10)
* [**<span data-ttu-id="d620e-174">Windows.UI.Notifications-Namespace</span><span class="sxs-lookup"><span data-stu-id="d620e-174">Windows.UI.Notifications namespace</span></span>**](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications)
* [<span data-ttu-id="d620e-175">So wird’s gemacht: Verwenden der Benachrichtigungswarteschlange (XAML)</span><span class="sxs-lookup"><span data-stu-id="d620e-175">How to use the notification queue (XAML)</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh868234)
* [<span data-ttu-id="d620e-176">Zustellen von Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="d620e-176">Delivering notifications</span></span>](choosing-a-notification-delivery-method.md)
 

 




