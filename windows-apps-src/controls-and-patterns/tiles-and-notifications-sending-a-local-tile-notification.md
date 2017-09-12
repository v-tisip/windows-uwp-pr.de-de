---
author: mijacobs
Description: "In diesem Artikel wird beschrieben, wie Sie mit adaptiven Kachelvorlagen eine lokale Benachrichtigung an eine primäre Kachel und an eine sekundäre Kachel senden."
title: Senden einer lokalen Kachelbenachrichtigung
ms.assetid: D34B0514-AEC6-4C41-B318-F0985B51AF8A
label: TBD
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.openlocfilehash: 5b1c5765b98268020213ccc4284912dd531ba3b4
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="send-a-local-tile-notification"></a><span data-ttu-id="540df-104">Senden einer lokalen Kachelbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="540df-104">Send a local tile notification</span></span>
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

<span data-ttu-id="540df-105">Primäre App-Kacheln in Windows 10 werden im App-Manifest definiert, sekundäre Kacheln werden dagegen programmgesteuert erstellt und vom App-Code definiert.</span><span class="sxs-lookup"><span data-stu-id="540df-105">Primary app tiles in Windows 10 are defined in your app manifest, while secondary tiles are programmatically created and defined by your app code.</span></span> <span data-ttu-id="540df-106">In diesem Artikel wird beschrieben, wie Sie eine lokale Benachrichtigung an eine primäre Kachel und an eine sekundäre Kachel mit adaptiven Kachelvorlagen senden.</span><span class="sxs-lookup"><span data-stu-id="540df-106">This article describes how to send a local tile notification to a primary tile and a secondary tile using adaptive tile templates.</span></span> <span data-ttu-id="540df-107">(Eine lokale Benachrichtigung wird vom App-Code gesendet, im Gegensatz zu Benachrichtigungen, die ein Webserver per Push oder Pull sendet.)</span><span class="sxs-lookup"><span data-stu-id="540df-107">(A local notification is one that's sent from app code as opposed to one that's pushed or pulled from a web server.)</span></span>

![Standardkachel und Kachel mit Benachrichtigung](images/sending-local-tile-01.png)

> [!NOTE] 
><span data-ttu-id="540df-109">Weitere Informationen über das [Erstellen von adaptiven Kacheln](tiles-and-notifications-create-adaptive-tiles.md) und das [Vorlageschema für adaptive Kacheln](tiles-and-notifications-adaptive-tiles-schema.md).</span><span class="sxs-lookup"><span data-stu-id="540df-109">Learn about [creating adaptive tiles](tiles-and-notifications-create-adaptive-tiles.md) and [adaptive tile template schema](tiles-and-notifications-adaptive-tiles-schema.md).</span></span>

 

## <a name="install-the-nuget-package"></a><span data-ttu-id="540df-110">Installieren des NuGet-Pakets</span><span class="sxs-lookup"><span data-stu-id="540df-110">Install the NuGet package</span></span>


<span data-ttu-id="540df-111">Wir empfehlen die Installation des [NuGet-Pakets aus der Benachrichtigungsbibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/), das Kachelnutzlasten mit Objekten anstelle von unformatiertem XML generiert und damit vieles vereinfacht.</span><span class="sxs-lookup"><span data-stu-id="540df-111">We recommend installing the [Notifications library NuGet package](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/), which simplifies things by generating tile payloads with objects instead of raw XML.</span></span>

<span data-ttu-id="540df-112">Die Inlinecodebeispiele in diesem Artikel beziehen sich auf C# unter Verwendung der Benachrichtigungsbibliothek.</span><span class="sxs-lookup"><span data-stu-id="540df-112">The inline code examples in this article are for C# using the Notifications library.</span></span> <span data-ttu-id="540df-113">(Wenn Sie eigenen XML-Code erstellen möchten, finden Sie am Ende des Artikels Codebeispiele ohne Benachrichtigungsbibliothek.)</span><span class="sxs-lookup"><span data-stu-id="540df-113">(If you'd prefer to create your own XML, you can find code examples without the Notifications library toward the end of the article.)</span></span>

## <a name="add-namespace-declarations"></a><span data-ttu-id="540df-114">Hinzufügen von Namespacedeklarationen</span><span class="sxs-lookup"><span data-stu-id="540df-114">Add namespace declarations</span></span>


<span data-ttu-id="540df-115">Um auf die Kachel-APIs zuzugreifen, beziehen Sie den [**Windows.UI.Notifications**](https://msdn.microsoft.com/library/windows/apps/br208661)-Namespace ein.</span><span class="sxs-lookup"><span data-stu-id="540df-115">To access the tile APIs, include the [**Windows.UI.Notifications**](https://msdn.microsoft.com/library/windows/apps/br208661) namespace.</span></span> <span data-ttu-id="540df-116">Es wird darüber hinaus empfohlen, den **NotificationsExtensions.Tiles**-Namespace einzubeziehen, damit Sie die Kachel-Hilfs-APIs nutzen können. (Sie müssen das NuGet-Paket aus der [Benachrichtigungsbibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) installieren, um auf diese APIs zugreifen zu können.)</span><span class="sxs-lookup"><span data-stu-id="540df-116">We also recommend including the **NotificationsExtensions.Tiles** namespace so that you can take advantage of our tile helper APIs (you must install the [Notifications library](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) NuGet package to access these APIs).</span></span>

```CSharp
using Windows.UI.Notifications;
using Microsoft.Toolkit.Uwp.Notifications; // Notifications library
```

## <a name="create-the-notification-content"></a><span data-ttu-id="540df-117">Erstellen des Benachrichtigungsinhalts</span><span class="sxs-lookup"><span data-stu-id="540df-117">Create the notification content</span></span>


<span data-ttu-id="540df-118">In Windows10 werden Kachelnutzlasten mit adaptiven Kachelvorlagen definiert, mit denen Sie benutzerdefinierte visuelle Layouts für Ihre Benachrichtigungen erstellen können.</span><span class="sxs-lookup"><span data-stu-id="540df-118">In Windows 10, tile payloads are defined using adaptive tile templates, which allow you to create custom visual layouts for your notifications.</span></span> <span data-ttu-id="540df-119">(Informationen darüber, was mit adaptiven Kacheln möglich ist, finden Sie in den Artikeln [Erstellen adaptiver Kacheln](tiles-and-notifications-create-adaptive-tiles.md) und [Vorlagen für adaptive Kacheln](tiles-and-notifications-adaptive-tiles-schema.md).)</span><span class="sxs-lookup"><span data-stu-id="540df-119">(To learn what's possible with adaptive tiles, see the [Create adaptive tiles](tiles-and-notifications-create-adaptive-tiles.md) and [Adaptive tile templates](tiles-and-notifications-adaptive-tiles-schema.md) articles.)</span></span>

<span data-ttu-id="540df-120">Dieses Codebeispiel erstellt adaptive Kachelinhalte für mittelgroße und breite Kacheln.</span><span class="sxs-lookup"><span data-stu-id="540df-120">This code example creates adaptive tile content for medium and wide tiles.</span></span>

```CSharp
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

<span data-ttu-id="540df-121">Auf einer mittelgroßen Kachel wird der Inhalt der Benachrichtigung wie folgt angezeigt:</span><span class="sxs-lookup"><span data-stu-id="540df-121">The notification content looks like the following when displayed on a medium tile:</span></span>

![Inhalt der Benachrichtigung auf einer mittelgroßen Kachel](images/sending-local-tile-02.png)

## <a name="create-the-notification"></a><span data-ttu-id="540df-123">Erstellen der Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="540df-123">Create the notification</span></span>


<span data-ttu-id="540df-124">Wenn Sie den Inhalt der Benachrichtigung erstellt haben, müssen Sie eine neue [**TileNotification**](https://msdn.microsoft.com/library/windows/apps/br208616)-Klasse erstellen.</span><span class="sxs-lookup"><span data-stu-id="540df-124">Once you have your notification content, you'll need to create a new [**TileNotification**](https://msdn.microsoft.com/library/windows/apps/br208616).</span></span> <span data-ttu-id="540df-125">Der **TileNotification**-Konstruktor akzeptiert ein Windows-Runtime-[**XmlDocument**](https://msdn.microsoft.com/library/windows/apps/br208620)-Objekt, das Sie aus der **TileContent.GetXml**-Methode abrufen können, wenn Sie die [Benachrichtigungsbibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) verwenden.</span><span class="sxs-lookup"><span data-stu-id="540df-125">The **TileNotification** constructor takes a Windows Runtime [**XmlDocument**](https://msdn.microsoft.com/library/windows/apps/br208620) object, which you can obtain from the **TileContent.GetXml** method if you're using the [Notifications library](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/).</span></span>

<span data-ttu-id="540df-126">Mit diesem Codebeispiel wird eine Benachrichtigung für eine neue Kachel erstellt.</span><span class="sxs-lookup"><span data-stu-id="540df-126">This code example creates a notification for a new tile.</span></span>

```CSharp
// Create the tile notification
var notification = new TileNotification(content.GetXml());
```

## <a name="set-an-expiration-time-for-the-notification-optional"></a><span data-ttu-id="540df-127">Festlegen einer Ablaufzeit für die Benachrichtigung (optional)</span><span class="sxs-lookup"><span data-stu-id="540df-127">Set an expiration time for the notification (optional)</span></span>


<span data-ttu-id="540df-128">Standardmäßig laufen lokale Kachel- und Signalbenachrichtigungen nicht ab, während Pushbenachrichtigungen sowie regelmäßige und geplante Benachrichtigungen nach drei Tagen ablaufen.</span><span class="sxs-lookup"><span data-stu-id="540df-128">By default, local tile and badge notifications don't expire, while push, periodic, and scheduled notifications expire after three days.</span></span> <span data-ttu-id="540df-129">Weil Kachelinhalt nur so lange wie notwendig beibehalten werden soll, sollten Sie, insbesondere für lokale Kachel- und Signalbenachrichtigungen, eine Gültigkeitsdauer festlegen, die für Ihre App sinnvoll ist.</span><span class="sxs-lookup"><span data-stu-id="540df-129">Because tile content shouldn't persist longer than necessary, it's a best practice to set an expiration time that makes sense for your app, especially on local tile and badge notifications.</span></span>

<span data-ttu-id="540df-130">In diesem Codebeispiel wird eine Benachrichtigung erstellt, die nach zehn Minuten abläuft und von der Kachel entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="540df-130">This code example creates a notification that expires and will be removed from the tile after ten minutes.</span></span>

```CSharp
tileNotification.ExpirationTime = DateTimeOffset.UtcNow.AddMinutes(10);
```

## <a name="send-the-notification"></a><span data-ttu-id="540df-131">Senden der Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="540df-131">Send the notification</span></span>


<span data-ttu-id="540df-132">Das lokale Senden einer Kachelbenachrichtigung ist einfach, das Senden der Benachrichtigung an eine primäre oder sekundäre Kachel weicht aber etwas davon ab.</span><span class="sxs-lookup"><span data-stu-id="540df-132">Although locally sending a tile notification is simple, sending the notification to a primary or secondary tile is a bit different.</span></span>

**<span data-ttu-id="540df-133">Primäre Kachel</span><span class="sxs-lookup"><span data-stu-id="540df-133">Primary tile</span></span>**

<span data-ttu-id="540df-134">Verwenden Sie zum Senden einer Benachrichtigung an eine primäre Kachel den [**TileUpdateManager**](https://msdn.microsoft.com/library/windows/apps/br208622), um für die primäre Kachel eine Kachelaktualisierung zu erstellen und die Benachrichtigung durch Aufrufen von „Update” zu senden.</span><span class="sxs-lookup"><span data-stu-id="540df-134">To send a notification to a primary tile, use the [**TileUpdateManager**](https://msdn.microsoft.com/library/windows/apps/br208622) to create a tile updater for the primary tile, and send the notification by calling "Update".</span></span> <span data-ttu-id="540df-135">Die primäre Kachel Ihrer App ist immer vorhanden, selbst wenn sie nicht sichtbar ist. Daher können Sie Benachrichtigungen an die Kachel senden, auch wenn sie nicht angeheftet ist.</span><span class="sxs-lookup"><span data-stu-id="540df-135">Regardless of whether it's visible, your app's primary tile always exists, so you can send notifications to it even when it's not pinned.</span></span> <span data-ttu-id="540df-136">Wenn der Benutzer später die primäre Kachel anheftet, werden die Benachrichtigungen, die Sie gesendet haben, angezeigt.</span><span class="sxs-lookup"><span data-stu-id="540df-136">If the user pins your primary tile later, the notifications that you sent will appear then.</span></span>

<span data-ttu-id="540df-137">Mit diesem Codebeispiel wird eine Benachrichtigung an eine primäre Kachel gesendet.</span><span class="sxs-lookup"><span data-stu-id="540df-137">This code example sends a notification to a primary tile.</span></span>


```CSharp
// Send the notification to the primary tile
TileUpdateManager.CreateTileUpdaterForApplication().Update(notification);
```

**<span data-ttu-id="540df-138">Sekundäre Kachel</span><span class="sxs-lookup"><span data-stu-id="540df-138">Secondary tile</span></span>**

<span data-ttu-id="540df-139">Um eine Benachrichtigung an eine sekundäre Kachel zu senden, müssen Sie zuerst sicherstellen Sie, dass die sekundäre Kachel vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="540df-139">To send a notification to a secondary tile, first make sure that the secondary tile exists.</span></span> <span data-ttu-id="540df-140">Wenn Sie versuchen, eine Kachelaktualisierung für eine sekundäre Kachel zu erstellen, die nicht vorhanden ist (z.B. wenn der Benutzer die sekundäre Kachel gelöst hat), wird eine Ausnahme ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="540df-140">If you try to create a tile updater for a secondary tile that doesn't exist (for example, if the user unpinned the secondary tile), an exception will be thrown.</span></span> <span data-ttu-id="540df-141">Sie können mit [**SecondaryTile.Exists**](https://msdn.microsoft.com/library/windows/apps/br242205)(tileId) ermitteln, ob die sekundäre Kachel angeheftet ist, und dann eine Kachelaktualisierung für eine sekundäre Kachel erstellen und die Benachrichtigung senden.</span><span class="sxs-lookup"><span data-stu-id="540df-141">You can use [**SecondaryTile.Exists**](https://msdn.microsoft.com/library/windows/apps/br242205)(tileId) to discover if your secondary tile is pinned, and then create a tile updater for the secondary tile and send the notification.</span></span>

<span data-ttu-id="540df-142">Mit diesem Codebeispiel wird eine Benachrichtigung an eine sekundäre Kachel gesendet.</span><span class="sxs-lookup"><span data-stu-id="540df-142">This code example sends a notification to a secondary tile.</span></span>

```CSharp
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

## <a name="clear-notifications-on-the-tile-optional"></a><span data-ttu-id="540df-144">Löschen von Benachrichtigungen auf der Kachel (optional)</span><span class="sxs-lookup"><span data-stu-id="540df-144">Clear notifications on the tile (optional)</span></span>


<span data-ttu-id="540df-145">In den meisten Fällen sollten Sie eine Benachrichtigung löschen, sobald der Benutzer mit diesem Inhalt interagiert hat.</span><span class="sxs-lookup"><span data-stu-id="540df-145">In most cases, you should clear a notification once the user has interacted with that content.</span></span> <span data-ttu-id="540df-146">Zum Beispiel sollten Sie alle Benachrichtigungen auf der Kachel löschen, wenn der Benutzer die App startet.</span><span class="sxs-lookup"><span data-stu-id="540df-146">For example, when the user launches your app, you might want to clear all the notifications from the tile.</span></span> <span data-ttu-id="540df-147">Wenn die Benachrichtigungen zeitabhängig sind, sollten Sie eine Ablaufzeit für die Benachrichtigung festlegen, anstatt sie explizit zu löschen.</span><span class="sxs-lookup"><span data-stu-id="540df-147">If your notifications are time-bound, we recommend that you set an expiration time on the notification instead of explicitly clearing the notification.</span></span>

<span data-ttu-id="540df-148">In diesem Codebeispiel wird die Kachelbenachrichtigung für die primäre Kachel gelöscht.</span><span class="sxs-lookup"><span data-stu-id="540df-148">This code example clears the tile notification for the primary tile.</span></span> <span data-ttu-id="540df-149">Sie können diesen Vorgang auf sekundäre Kacheln anwenden, indem Sie für die sekundäre Kachel eine Kachelaktualisierung erstellen.</span><span class="sxs-lookup"><span data-stu-id="540df-149">You can do the same for secondary tiles by creating a tile updater for the secondary tile.</span></span>

```CSharp
TileUpdateManager.CreateTileUpdaterForApplication().Clear();
```

<span data-ttu-id="540df-150">Bei einer Kachel mit aktivierter Benachrichtigungswarteschlange und Benachrichtigungen in der Warteschlange wird durch Aufrufen der Clear-Methode die Warteschlange gelöscht.</span><span class="sxs-lookup"><span data-stu-id="540df-150">For a tile with the notification queue enabled and notifications in the queue, calling the Clear method empties the queue.</span></span> <span data-ttu-id="540df-151">Es ist aber nicht möglich ist, eine Benachrichtigung über den Server Ihrer App zu löschen; Benachrichtigungen können nur durch lokalen App-Code gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="540df-151">You can't, however, clear a notification via your app's server; only the local app code can clear notifications.</span></span>

<span data-ttu-id="540df-152">Durch regelmäßige oder Push-Benachrichtigungen können nur neue Benachrichtigungen hinzugefügt oder vorhandene Benachrichtigungen ersetzt werden.</span><span class="sxs-lookup"><span data-stu-id="540df-152">Periodic or push notifications can only add new notifications or replace existing notifications.</span></span> <span data-ttu-id="540df-153">Mit einem lokalen Aufruf der Clear-Methode wird die Kachel gelöscht, unabhängig davon, ob die Benachrichtigungen selbst per Push, regelmäßig oder lokal gesendet wurden.</span><span class="sxs-lookup"><span data-stu-id="540df-153">A local call to the Clear method will clear the tile whether or not the notifications themselves came via push, periodic, or local.</span></span> <span data-ttu-id="540df-154">Geplante Benachrichtigungen, die noch nicht angezeigt wurden, werden durch diese Methode nicht gelöscht.</span><span class="sxs-lookup"><span data-stu-id="540df-154">Scheduled notifications that haven't yet appeared are not cleared by this method.</span></span>

![Kachel mit Benachrichtigung und Kachel nach dem Löschen](images/sending-local-tile-03.png)

## <a name="next-steps"></a><span data-ttu-id="540df-156">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="540df-156">Next steps</span></span>


**<span data-ttu-id="540df-157">Verwenden der Benachrichtigungswarteschlange</span><span class="sxs-lookup"><span data-stu-id="540df-157">Using the notification queue</span></span>**

<span data-ttu-id="540df-158">Nachdem Sie Ihre erste Kachelaktualisierung ausgeführt haben, können Sie die Funktionalität der Kachel erweitern, indem Sie eine [Benachrichtigungswarteschlange](https://msdn.microsoft.com/library/windows/apps/xaml/hh868234) aktivieren.</span><span class="sxs-lookup"><span data-stu-id="540df-158">Now that you have done your first tile update, you can expand the functionality of the tile by enabling a [notification queue](https://msdn.microsoft.com/library/windows/apps/xaml/hh868234).</span></span>

**<span data-ttu-id="540df-159">Andere Methoden für die Benachrichtigungsübermittlung</span><span class="sxs-lookup"><span data-stu-id="540df-159">Other notification delivery methods</span></span>**

<span data-ttu-id="540df-160">In diesem Artikel wird erläutert, wie die Kachelaktualisierung als Benachrichtigung gesendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="540df-160">This article shows you how to send the tile update as a notification.</span></span> <span data-ttu-id="540df-161">Informationen zu anderen Methoden der Benachrichtigungsübermittlung, einschließlich geplanter, regelmäßiger und Push-Benachrichtigungen, finden Sie unter [Zustellen von Benachrichtigungen](tiles-and-notifications-choosing-a-notification-delivery-method.md).</span><span class="sxs-lookup"><span data-stu-id="540df-161">To explore other methods of notification delivery, including scheduled, periodic, and push, see [Delivering notifications](tiles-and-notifications-choosing-a-notification-delivery-method.md).</span></span>

**<span data-ttu-id="540df-162">XmlEncode-Übermittlungsmethode</span><span class="sxs-lookup"><span data-stu-id="540df-162">XmlEncode delivery method</span></span>**

<span data-ttu-id="540df-163">Wenn Sie die [Benachrichtigungsbibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) nicht verwenden, bietet diese Methode für die Benachrichtigungsübermittlung eine weitere Alternative.</span><span class="sxs-lookup"><span data-stu-id="540df-163">If you're not using the [Notifications library](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/), this notification delivery method is another alternative.</span></span>


```CSharp
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

## <a name="code-examples-without-notifications-library"></a><span data-ttu-id="540df-164">Codebeispiele ohne Benachrichtigungsbibliothek</span><span class="sxs-lookup"><span data-stu-id="540df-164">Code examples without Notifications library</span></span>


<span data-ttu-id="540df-165">Wenn Sie mit unformatiertem XML anstatt mit dem NuGet-Paket aus der [Benachrichtigungsbibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) arbeiten möchten, verwenden Sie diese alternativen Codebeispiele für die ersten drei Beispiele in diesem Artikel.</span><span class="sxs-lookup"><span data-stu-id="540df-165">If you prefer to work with raw XML instead of the [Notifications library](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) NuGet package, use these alternate code examples to first three examples provided in this article.</span></span> <span data-ttu-id="540df-166">Die restlichen Codebeispiele können entweder mit der [Benachrichtigungsbibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) oder mit unformatiertem XML verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="540df-166">The rest of the code examples can be used either with the [Notifications library](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) or with raw XML.</span></span>

<span data-ttu-id="540df-167">Hinzufügen von Namespacedeklarationen</span><span class="sxs-lookup"><span data-stu-id="540df-167">Add namespace declarations</span></span>

```CSharp
using Windows.UI.Notifications;
using Windows.Data.Xml.Dom;
```

<span data-ttu-id="540df-168">Erstellen des Benachrichtigungsinhalts</span><span class="sxs-lookup"><span data-stu-id="540df-168">Create the notification content</span></span>

```CSharp
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

<span data-ttu-id="540df-169">Erstellen der Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="540df-169">Create the notification</span></span>

```CSharp
// Load the string into an XmlDocument
XmlDocument doc = new XmlDocument();
doc.LoadXml(content);
 
// Then create the tile notification
var notification = new TileNotification(doc);
```

## <a name="related-topics"></a><span data-ttu-id="540df-170">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="540df-170">Related topics</span></span>

* [<span data-ttu-id="540df-171">Erstellen adaptiver Kacheln</span><span class="sxs-lookup"><span data-stu-id="540df-171">Create adaptive tiles</span></span>](tiles-and-notifications-create-adaptive-tiles.md)
* [<span data-ttu-id="540df-172">Vorlagen für adaptive Kacheln: Schema und Dokumentation</span><span class="sxs-lookup"><span data-stu-id="540df-172">Adaptive tile templates: schema and documentation</span></span>](tiles-and-notifications-adaptive-tiles-schema.md)
* [<span data-ttu-id="540df-173">Benachrichtigungsbibliothek</span><span class="sxs-lookup"><span data-stu-id="540df-173">Notifications library</span></span>](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/)
* [<span data-ttu-id="540df-174">Vollständiges Codebeispiel auf GitHub</span><span class="sxs-lookup"><span data-stu-id="540df-174">Full code sample on GitHub</span></span>](https://github.com/WindowsNotifications/quickstart-sending-local-tile-win10)
* [**<span data-ttu-id="540df-175">Windows.UI.Notifications-Namespace</span><span class="sxs-lookup"><span data-stu-id="540df-175">Windows.UI.Notifications namespace</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208661)
* [<span data-ttu-id="540df-176">So wird’s gemacht: Verwenden der Benachrichtigungswarteschlange (XAML)</span><span class="sxs-lookup"><span data-stu-id="540df-176">How to use the notification queue (XAML)</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh868234)
* [<span data-ttu-id="540df-177">Zustellen von Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="540df-177">Delivering notifications</span></span>](tiles-and-notifications-choosing-a-notification-delivery-method.md)
 

 




