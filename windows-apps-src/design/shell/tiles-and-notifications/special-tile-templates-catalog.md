---
author: andrewleader
Description: Special tile templates are unique templates that are either animated, or just allow you to do things that aren't possible with adaptive tiles.
title: Spezielle Kachelvorlagen
ms.assetid: 1322C9BA-D5B2-45E2-B813-865884A467FF
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 74b915e4d698503a13c5066348f4e46ebd3125c8
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7289145"
---
# <a name="special-tile-templates"></a><span data-ttu-id="a0200-103">Spezielle Kachelvorlagen</span><span class="sxs-lookup"><span data-stu-id="a0200-103">Special tile templates</span></span>
 

<span data-ttu-id="a0200-104">Spezielle Kachelvorlagen sind individuelle Vorlagen, die animiert sind oder mit denen Sie Vorgänge durchführen können, die mit adaptiven Kacheln nicht möglich sind.</span><span class="sxs-lookup"><span data-stu-id="a0200-104">Special tile templates are unique templates that are either animated, or just allow you to do things that aren't possible with adaptive tiles.</span></span> <span data-ttu-id="a0200-105">Jede spezielle kachelvorlage wurde speziell für Windows 10, mit Ausnahme der iconic-kachelvorlage, eine klassische spezialvorlage erstellt, die für Windows 10 aktualisiert wurde.</span><span class="sxs-lookup"><span data-stu-id="a0200-105">Each special tile template was specifically built for Windows10, except for the iconic tile template, a classic special template that has been updated for Windows10.</span></span> <span data-ttu-id="a0200-106">In diesem Artikel werden drei spezielle Kachelvorlagen behandelt: Iconic, Fotos und Kontakte.</span><span class="sxs-lookup"><span data-stu-id="a0200-106">This article covers three special tile templates: Iconic, Photos, and People.</span></span>

## <a name="iconic-tile-template"></a><span data-ttu-id="a0200-107">Iconic-Kachelvorlage</span><span class="sxs-lookup"><span data-stu-id="a0200-107">Iconic tile template</span></span>


<span data-ttu-id="a0200-108">Mit der Iconic-Vorlage (auch als „IconWithBadge“-Vorlage bezeichnet) können Sie ein kleines Bild in der Mitte der Kachel anzeigen.</span><span class="sxs-lookup"><span data-stu-id="a0200-108">The iconic template (also known as the "IconWithBadge" template) lets you display a small image in the center of the tile.</span></span> <span data-ttu-id="a0200-109">Windows 10 unterstützt die Vorlage auf Handy und Tablets/Desktops.</span><span class="sxs-lookup"><span data-stu-id="a0200-109">Windows10 supports the template on both phone and tablet/desktop.</span></span>

![Kleine und mittelgroße E-Mail-Kacheln](images/iconic-template-mail-2sizes.png)

### <a name="how-to-create-an-iconic-tile"></a><span data-ttu-id="a0200-111">Erstellen einer ikonischen Kachel</span><span class="sxs-lookup"><span data-stu-id="a0200-111">How to create an iconic tile</span></span>

<span data-ttu-id="a0200-112">Die folgenden Schritte behandelt alles, was Sie zum Erstellen einer iconic-Kachel für Windows 10 wissen müssen.</span><span class="sxs-lookup"><span data-stu-id="a0200-112">The following steps cover everything you need to know to create an iconic tile for Windows10.</span></span> <span data-ttu-id="a0200-113">Auf hoher Ebene benötigen Sie Ihre Iconic-Bildressource. Dann senden Sie mithilfe der Iconic-Vorlage eine Benachrichtigung an die Kachel und senden schließlich eine Signalbenachrichtigung, die die auf der Kachel anzuzeigende Zahl bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="a0200-113">At a high level, you need your iconic image asset, then you send a notification to the tile using the iconic template, and finally you send a badge notification that provides the number to be displayed on the tile.</span></span>

![Entwicklerablauf der Iconic-Kachel](images/iconic-template-dev-flow.png)

**<span data-ttu-id="a0200-115">Schritt 1: Erstellen Ihrer Bildressourcen im PNG-Format</span><span class="sxs-lookup"><span data-stu-id="a0200-115">Step 1: Create your image assets in PNG format</span></span>**

<span data-ttu-id="a0200-116">Erstellen Sie die Symbolressourcen für die Kachel, und platzieren Sie diese mit den anderen Ressourcen in Ihren Projektressourcen.</span><span class="sxs-lookup"><span data-stu-id="a0200-116">Create the icon assets for your tile and place those in your project resources with your other assets.</span></span> <span data-ttu-id="a0200-117">Erstellen Sie mindestens ein Symbol mit 200 x 200 Pixeln, das für kleine und mittelgroße Kacheln auf dem Telefon und dem Desktop funktioniert.</span><span class="sxs-lookup"><span data-stu-id="a0200-117">At a bare minimum, create a 200x200 pixel icon, which works for both small and medium tiles on phone and desktop.</span></span> <span data-ttu-id="a0200-118">Um die bestmögliche Benutzerfreundlichkeit bereitzustellen, erstellen Sie für jede Größe ein eigenes Symbol.</span><span class="sxs-lookup"><span data-stu-id="a0200-118">To provide the best user experience, create an icon for each size.</span></span> <span data-ttu-id="a0200-119">Auf diese Ressourcen ist kein Abstand erforderlich.</span><span class="sxs-lookup"><span data-stu-id="a0200-119">No padding is needed on these assets.</span></span> <span data-ttu-id="a0200-120">Informationen zu den Größen finden Sie im Bild unten.</span><span class="sxs-lookup"><span data-stu-id="a0200-120">See sizing details in the below image.</span></span>

<span data-ttu-id="a0200-121">Speichern Sie Symbolressourcen im PNG-Format und mit Transparenz.</span><span class="sxs-lookup"><span data-stu-id="a0200-121">Save icon assets in PNG format and with transparency.</span></span> <span data-ttu-id="a0200-122">Unter Windows Phone wird jedes nicht transparente Pixel weiß (RGB-Wert 255, 255, 255) angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a0200-122">On Windows Phone, every non-transparent pixel is displayed as white (RGB 255, 255, 255).</span></span> <span data-ttu-id="a0200-123">Verwenden Sie aus Gründen der Konsistenz und Einfachheit weiß auch für Desktopsymbole.</span><span class="sxs-lookup"><span data-stu-id="a0200-123">For consistency and simplicity, use white for desktop icons as well.</span></span>

<span data-ttu-id="a0200-124">Windows 10 auf Tablet, Laptop und Desktop unterstützt nur quadratische Symbolressourcen.</span><span class="sxs-lookup"><span data-stu-id="a0200-124">Windows 10 on tablet, laptop, and desktop only supports square icon assets.</span></span> <span data-ttu-id="a0200-125">Windows Phone unterstützt quadratische Ressourcen und Ressourcen, die höher als breit sind, bis zu einem Breite-Höhe-Verhältnis von 2:3, was für Bilder, z.B. ein Telefonsymbol, nützlich ist.</span><span class="sxs-lookup"><span data-stu-id="a0200-125">Phone supports both square assets and assets that are taller than they are wide, up to a 2:3 width:height ratio, which is useful for images such as a phone icon.</span></span>

![Symbolgrößen auf kleinen und mittelgroßen Kacheln auf Telefon und Desktop](images/iconic-template-sizing-info.png)

![Größen für Ressourcen mit und ohne Signal](images/assetguidance24.png)

<span data-ttu-id="a0200-128">Für quadratische Ressourcen erfolgt eine automatische Zentrierung innerhalb des Containers:</span><span class="sxs-lookup"><span data-stu-id="a0200-128">For square assets, automatic centering within the container occurs:</span></span>

![Größe einer quadratischen Ressource, mit und ohne Signal](images/assetguidance25.png)

<span data-ttu-id="a0200-130">Bei nicht quadratischen Ressourcen erfolgt eine automatische horizontale/vertikale Zentrierung und ein Andocken an die Breite bzw. Höhe des Containers:</span><span class="sxs-lookup"><span data-stu-id="a0200-130">For non-square assets, automatic horizontal/vertical centering and snapping to the width/height of the container occurs:</span></span>

![Größe einer nicht quadratischen Ressource, mit und ohne Signal](images/assetguidance26a.png)

![Größe einer nicht quadratischen Ressource, mit und ohne Signal](images/assetguidance26b.png)

**<span data-ttu-id="a0200-133">Schritt 2: Erstellen der Basiskachel</span><span class="sxs-lookup"><span data-stu-id="a0200-133">Step 2: Create your base tile</span></span>**

<span data-ttu-id="a0200-134">Sie können die Iconic-Vorlage für primäre und sekundäre Kacheln verwenden.</span><span class="sxs-lookup"><span data-stu-id="a0200-134">You can use the iconic template on both primary and secondary tiles.</span></span> <span data-ttu-id="a0200-135">Wenn Sie sie für eine sekundäre Kachel verwenden, müssen Sie zuerst die sekundäre Kachel erstellen oder eine bereits angeheftete sekundäre Kachel verwenden.</span><span class="sxs-lookup"><span data-stu-id="a0200-135">If you're using it on a secondary tile, you'll first have to create the secondary tile or use an already-pinned secondary tile.</span></span> <span data-ttu-id="a0200-136">Primäre Kacheln sind implizit angeheftet, und Sie können jederzeit Benachrichtigungen an sie senden.</span><span class="sxs-lookup"><span data-stu-id="a0200-136">Primary tiles are implicitly pinned and can always be sent notifications.</span></span>

**<span data-ttu-id="a0200-137">Schritt 3: Senden einer Benachrichtigung an die Kachel</span><span class="sxs-lookup"><span data-stu-id="a0200-137">Step 3: Send a notification to your tile</span></span>**

<span data-ttu-id="a0200-138">Obwohl dieser Schritt variieren kann, je nachdem, ob die Benachrichtigung lokal oder per Serverpush gesendet wird, bleibt die gesendete XML-Nutzlast identisch.</span><span class="sxs-lookup"><span data-stu-id="a0200-138">Although this step can vary based on whether the notification is sent locally or via server push, the XML payload that you send remains the same.</span></span> <span data-ttu-id="a0200-139">Um eine lokale Kachelbenachrichtigung zu senden, erstellen Sie einen [**TileUpdater**](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.TileUpdater) für die Kachel (entweder primäre oder sekundäre Kachel), und senden Sie dann eine Benachrichtigung an die Kachel, die die Iconic-Kachelvorlage verwendet, wie unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="a0200-139">To send a local tile notification, create a [**TileUpdater**](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.TileUpdater) for your tile (either primary or secondary tile), then send a notification to the tile that uses the iconic tile template as seen below.</span></span> <span data-ttu-id="a0200-140">Im Idealfall sollten Sie auch Bindungen für breite und große Kachelgrößen mit [adaptiven Kachelvorlagen](create-adaptive-tiles.md) einschließen.</span><span class="sxs-lookup"><span data-stu-id="a0200-140">Ideally, you should also include bindings for wide and large tile sizes using [adaptive tile templates](create-adaptive-tiles.md).</span></span>

<span data-ttu-id="a0200-141">Hier sehen Sie einen Beispielcode für die XML-Nutzlast:</span><span class="sxs-lookup"><span data-stu-id="a0200-141">Here's sample code for the XML payload:</span></span>

```xml
<tile>
  <visual>

    <binding template="TileSquare150x150IconWithBadge">
      <image id="1" src="Iconic.png" alt="alt text"/>
    </binding>
    
    <binding template="TileSquare71x71IconWithBadge">
      <image id="1" src="Iconic.png" alt="alt text"/>
    </binding>

  </visual>
</tile>
```

<span data-ttu-id="a0200-142">Die XML-Nutzlast dieser Iconic-Kachelvorlage verwendet ein Bildelement, das auf das Bild verweist, das Sie in Schritt 1 erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="a0200-142">This iconic tile template XML payload uses an image element that points to the image that you created in Step 1.</span></span> <span data-ttu-id="a0200-143">Jetzt kann die Kachel das Signal neben Ihrem Symbol anzeigen, wenn Signalbenachrichtigungen gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="a0200-143">Now your tile is ready to display the badge next to your icon; all that's left is sending badge notifications.</span></span>

**<span data-ttu-id="a0200-144">Schritt 4: Senden einer Signalbenachrichtigung an die Kachel</span><span class="sxs-lookup"><span data-stu-id="a0200-144">Step 4: Send a badge notification to your tile</span></span>**

<span data-ttu-id="a0200-145">Wie Schritt 3 kann dieser Schritt variieren, je nachdem, ob die Benachrichtigung lokal oder per Serverpush gesendet wird, aber die gesendete XML-Nutzlast bleibt identisch.</span><span class="sxs-lookup"><span data-stu-id="a0200-145">As with step 3, this step can vary based on whether the notification is sent locally or via server push, yet the XML payload that you send remains the same.</span></span> <span data-ttu-id="a0200-146">Erstellen Sie zum Senden einer lokalen Signalbenachrichtigung einen [**BadgeUpdater**](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.BadgeUpdater) für die Kachel (entweder primäre oder sekundäre Kachel), und senden Sie dann eine Signalbenachrichtigung mit dem gewünschten Wert (oder löschen Sie das Signal).</span><span class="sxs-lookup"><span data-stu-id="a0200-146">To send a local badge notification, create a [**BadgeUpdater**](https://docs.microsoft.com/uwp/api/Windows.UI.Notifications.BadgeUpdater) for your tile (either primary or secondary tile), then send a badge notification with your desired value (or clear the badge).</span></span>

<span data-ttu-id="a0200-147">Hier sehen Sie einen Beispielcode für die XML-Nutzlast:</span><span class="sxs-lookup"><span data-stu-id="a0200-147">Here's sample code for the XML payload:</span></span>

```xml
<badge value="2"/>
```

<span data-ttu-id="a0200-148">Das Signal der Kachel wird entsprechend aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="a0200-148">The tile's badge will update accordingly.</span></span>

**<span data-ttu-id="a0200-149">Schritt 5: Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="a0200-149">Step 5: Putting it all together</span></span>**

<span data-ttu-id="a0200-150">Die folgende Abbildung zeigt, wie die verschiedenen APIs und Nutzlasten den einzelnen Aspekten der ikonischen Kachelvorlage zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="a0200-150">The following image illustrates how the various APIs and payloads are associated with each aspect of the iconic tile template.</span></span> <span data-ttu-id="a0200-151">Ein [Kachelbenachrichtigung](https://msdn.microsoft.com/library/windows/apps/hh779724) (die diese &lt;binding&gt;-Elemente enthält) dient zum Angeben der ikonischen Vorlage und der Bildressource. Eine [Signalbenachrichtigung](https://msdn.microsoft.com/library/windows/apps/hh779719) gibt den numerischen Wert an. Kacheleigenschaften steuern den Anzeigenamen, die Farbe und vieles mehr der Kachel.</span><span class="sxs-lookup"><span data-stu-id="a0200-151">A [tile notification](https://msdn.microsoft.com/library/windows/apps/hh779724) (which contains those &lt;binding&gt; elements) is used to specify the iconic template and the image asset; a [badge notification](https://msdn.microsoft.com/library/windows/apps/hh779719) specifies the numerical value; tile properties control your tile's display name, color, and more.</span></span>

![APIs und Nutzlasten, die der Iconic-Kachelvorlage zugeordnet sind](images/iconic-template-properties-info.png)

## <a name="photos-tile-template"></a><span data-ttu-id="a0200-153">Kachelvorlage „Fotos“</span><span class="sxs-lookup"><span data-stu-id="a0200-153">Photos tile template</span></span>


<span data-ttu-id="a0200-154">Mit der Kachelvorlage „Fotos“ können Sie eine Diashow von Fotos auf der Live-Kachel anzeigen.</span><span class="sxs-lookup"><span data-stu-id="a0200-154">The photos tile template lets you display a slideshow of photos on your live tile.</span></span> <span data-ttu-id="a0200-155">Die Vorlage wird für alle Kachelgrößen, einschließlich klein, unterstützt und verhält sich für jede Kachelgröße gleich.</span><span class="sxs-lookup"><span data-stu-id="a0200-155">The template is supported on all tile sizes, including small, and behaves the same on each tile size.</span></span> <span data-ttu-id="a0200-156">Das folgende Beispiel zeigt fünf Frames einer mittelgroßen Kachel, die die Vorlage „Fotos“ verwendet.</span><span class="sxs-lookup"><span data-stu-id="a0200-156">The below example shows five frames of a medium tile that uses the photos template.</span></span> <span data-ttu-id="a0200-157">Die Vorlage verfügt über eine Zoom- und Überblendanimation, die ausgewählte Fotos in einer Endlosschleife durchläuft.</span><span class="sxs-lookup"><span data-stu-id="a0200-157">The template has a zoom and cross-fade animation that cycles through selected photos and loops indefinitely.</span></span>

![Bilddiashow mit Kachelvorlage „Fotos“](images/photo-tile-template-image01.jpg)

### <a name="how-to-use-the-photos-template"></a><span data-ttu-id="a0200-159">Verwenden der Kachelvorlage „Fotos“</span><span class="sxs-lookup"><span data-stu-id="a0200-159">How to use the photos template</span></span>

<span data-ttu-id="a0200-160">Das Verwenden der Vorlage „Fotos“ ist einfach, wenn Sie die [Benachrichtigungsbibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) installiert haben.</span><span class="sxs-lookup"><span data-stu-id="a0200-160">Using the photos template is easy if you've installed the [Notifications library](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/).</span></span> <span data-ttu-id="a0200-161">Obwohl Sie unformatierte XML-Daten verwenden können, empfehlen wir nachdrücklich die Verwendung der Benachrichtigungsbibliothek, damit Sie sich keine Gedanken zum Generieren gültiger XML- oder XML-Escapesequenzinhalte machen müssen.</span><span class="sxs-lookup"><span data-stu-id="a0200-161">Although you can use raw XML, we highly recommend using the library so you don't have to worry about generating valid XML or XML-escaping content.</span></span>

<span data-ttu-id="a0200-162">Windows Phone zeigt bis zu 9 Fotos in einer Diashow an. Auf Tablet, Laptop und Desktop werden bis zu 12 Fotos angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a0200-162">Windows Phone displays up to 9 photos in a slideshow; tablet, laptop, and desktop display up to 12.</span></span>

<span data-ttu-id="a0200-163">Informationen zum Senden der Kachelbenachrichtigung finden Sie im [Artikel zum Senden von Benachrichtigungen](index.md).</span><span class="sxs-lookup"><span data-stu-id="a0200-163">For information about sending the tile notification, see the [Send notifications article](index.md).</span></span>


```xml
<!--
 
To use the Photos template...
 
 - On any adaptive tile binding (like TileMedium or TileWide)
   - Set the hint-presentation attribute to "photos"
   - Add up to 12 images as children of the binding.
    
-->
 
<tile>
  <visual>
     
    <binding template="TileMedium" hint-presentation="photos">
       
      <image src="Assets/1.jpg" />
      <image src="ms-appdata:///local/Images/2.jpg"/>
      <image src="http://msn.com/images/3.jpg"/>
       
      <!--TODO: Can have 12 images total-->
       
    </binding>
     
    <!--TODO: Add bindings for other tile sizes-->
     
  </visual>
</tile>
```

```csharp
/*
 
To use the Photos template...
 
 - On any TileBinding object
   - Set Content property to new instance of TileBindingContentPhotos
   - Add up to 12 images to Images property of TileBindingContentPhotos.
 
*/
 
TileContent content = new TileContent()
{
    Visual = new TileVisual()
    {
        TileMedium = new TileBinding()
        {
            Content = new TileBindingContentPhotos()
            {
                Images =
                {
                    new TileBasicImage() { Source = "Assets/1.jpg" },
                    new TileBasicImage() { Source = "ms-appdata:///local/Images/2.jpg" },
                    new TileBasicImage() { Source = "http://msn.com/images/3.jpg" }
 
                    // TODO: Can have 12 images total
                }
            }
        }
 
        // TODO: Add other tile sizes
    }
};
```

## <a name="people-tile-template"></a><span data-ttu-id="a0200-164">Kachelvorlage „Kontakte“</span><span class="sxs-lookup"><span data-stu-id="a0200-164">People tile template</span></span>


<span data-ttu-id="a0200-165">Die Kontakte-App in Windows 10 verwendet eine spezielle Kachelvorlage, die eine Sammlung von Bildern in Kreisen anzeigt, die sich auf der Kachel vertikal oder horizontal verschieben.</span><span class="sxs-lookup"><span data-stu-id="a0200-165">The People app in Windows 10 uses a special tile template that displays a collection of images in circles that slide around vertically or horizontally on the tile.</span></span> <span data-ttu-id="a0200-166">Diese kachelvorlage wurde seit Windows 10 Build 10572 verfügbar, und alle Personen in ihrer app verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a0200-166">This tile template has been available since Windows10 Build 10572, and anyone is welcome to use it in their app.</span></span>

<span data-ttu-id="a0200-167">Die Kachelvorlage „Kontakte“ funktioniert auf Kacheln folgender Größen:</span><span class="sxs-lookup"><span data-stu-id="a0200-167">The People tile template works on tiles of these sizes:</span></span>

<span data-ttu-id="a0200-168">**Mittelgroße Kachel** (TileMedium)</span><span class="sxs-lookup"><span data-stu-id="a0200-168">**Medium tile** (TileMedium)</span></span>

![Mittelgroße Kachel „Kontakte“](images/people-tile-medium.png)

 

<span data-ttu-id="a0200-170">**Breite Kachel** (TileWide)</span><span class="sxs-lookup"><span data-stu-id="a0200-170">**Wide tile** (TileWide)</span></span>

![Breite Kachel „Kontakte“](images/people-tile-wide.png)

 

<span data-ttu-id="a0200-172">**Große Kachel (nur Desktop)** (TileLarge)</span><span class="sxs-lookup"><span data-stu-id="a0200-172">**Large tile (desktop only)** (TileLarge)</span></span>

![Große Kachel „Kontakte“](images/people-tile-large.png)

 

<span data-ttu-id="a0200-174">Bei Verwendung der [Benachrichtigungsbibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) müssen Sie zum Verwenden der Kachelvorlage „Kontakte“ nur ein neues *TileBindingContentPeople*-Objekt für Ihren *TileBinding*-Inhalt erstellen.</span><span class="sxs-lookup"><span data-stu-id="a0200-174">If you're using the [Notifications library](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/), all you have to do to make use of the People tile template is create a new *TileBindingContentPeople* object for your *TileBinding* content.</span></span> <span data-ttu-id="a0200-175">Die *TileBindingContentPeople*-Klasse verfügt über eine Bildereigenschaft, mit der Sie Ihre Bilder hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="a0200-175">The *TileBindingContentPeople* class has an Images property where you add your images.</span></span>

<span data-ttu-id="a0200-176">Wenn Sie unformatiertes XML verwenden, legen Sie *hint-presentation* auf „Kontakte“ fest, und fügen Sie die Bilder als untergeordnete Elemente des Bindungselements hinzu.</span><span class="sxs-lookup"><span data-stu-id="a0200-176">If you're using raw XML, set the *hint-presentation* to "people" and add your images as children of the binding element.</span></span>

<span data-ttu-id="a0200-177">Das folgende C#-Codebeispiel nimmt an, dass Sie [Benachrichtigungsbibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) verwenden.</span><span class="sxs-lookup"><span data-stu-id="a0200-177">The following C# code sample assumes that you're using the [Notifications library](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/).</span></span>

```csharp
TileContent content = new TileContent()
{
    Visual = new TileVisual()
    {
        TileMedium = new TileBinding()
        {
            Content = new TileBindingContentPeople()
            {
                Images =
                {
                    new TileBasicImage() { Source = "Assets/ProfilePics/1.jpg" },
                    new TileBasicImage() { Source = "Assets/ProfilePics/2.jpg" },
                    new TileBasicImage() { Source = "Assets/ProfilePics/3.jpg" },
                    new TileBasicImage() { Source = "Assets/ProfilePics/4.jpg" },
                    new TileBasicImage() { Source = "Assets/ProfilePics/5.jpg" },
                    new TileBasicImage() { Source = "Assets/ProfilePics/6.jpg" },
                    new TileBasicImage() { Source = "Assets/ProfilePics/7.jpg" },
                    new TileBasicImage() { Source = "Assets/ProfilePics/8.jpg" },
                    new TileBasicImage() { Source = "Assets/ProfilePics/9.jpg" }
                }
            }
        }
    }
};
```

```xml
<tile>
  <visual>
 
    <binding template="TileMedium" hint-presentation="people">
      <image src="Assets/ProfilePics/1.jpg"/>
      <image src="Assets/ProfilePics/2.jpg"/>
      <image src="Assets/ProfilePics/3.jpg"/>
      <image src="Assets/ProfilePics/4.jpg"/>
      <image src="Assets/ProfilePics/5.jpg"/>
      <image src="Assets/ProfilePics/6.jpg"/>
      <image src="Assets/ProfilePics/7.jpg"/>
      <image src="Assets/ProfilePics/8.jpg"/>
      <image src="Assets/ProfilePics/9.jpg"/>
    </binding>
 
  </visual>
</tile>
```

<span data-ttu-id="a0200-178">Um eine optimale Benutzererfahrung bereitzustellen, empfehlen wir die Bereitstellung der folgenden Anzahl von Fotos für die einzelnen Kachelgrößen:</span><span class="sxs-lookup"><span data-stu-id="a0200-178">For the best user experience, we recommend that you provide the following number of photos for each tile size:</span></span>

-   <span data-ttu-id="a0200-179">Mittelgroße Kachel: 9 Fotos</span><span class="sxs-lookup"><span data-stu-id="a0200-179">Medium tile: 9 photos</span></span>
-   <span data-ttu-id="a0200-180">Breite Kachel: 15 Fotos</span><span class="sxs-lookup"><span data-stu-id="a0200-180">Wide tile: 15 photos</span></span>
-   <span data-ttu-id="a0200-181">Große Kachel: 20 Fotos</span><span class="sxs-lookup"><span data-stu-id="a0200-181">Large tile: 20 photos</span></span>

<span data-ttu-id="a0200-182">Durch die Anzahl der Fotos werden einige leere Kreise ermöglicht, was bedeutet, dass die Kachel visuell nicht zu ausgelastet ist.</span><span class="sxs-lookup"><span data-stu-id="a0200-182">Having that number of photos allows for a few empty circles, which means that the tile won't be too visually busy.</span></span> <span data-ttu-id="a0200-183">Sie können die Anzahl der Fotos anpassen, um das gewünschte Erscheinungsbild zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="a0200-183">Feel free to tweak the number of photos to get the look that works best for you.</span></span>

<span data-ttu-id="a0200-184">Informationen zum Senden der Benachrichtigung finden Sie unter [Auswählen einer Methode für die Übermittlung von Benachrichtigungen](choosing-a-notification-delivery-method.md).</span><span class="sxs-lookup"><span data-stu-id="a0200-184">To send the notification, see [Choose a notification delivery method](choosing-a-notification-delivery-method.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="a0200-185">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="a0200-185">Related topics</span></span>


* [<span data-ttu-id="a0200-186">Vollständiges Codebeispiel auf GitHub</span><span class="sxs-lookup"><span data-stu-id="a0200-186">Full code sample on GitHub</span></span>](https://github.com/WindowsNotifications/quickstart-people-tile-template)
* [<span data-ttu-id="a0200-187">Benachrichtigungsbibliothek</span><span class="sxs-lookup"><span data-stu-id="a0200-187">Notifications library</span></span>](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/)
* [<span data-ttu-id="a0200-188">Kacheln, Signale und Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="a0200-188">Tiles, badges, and notifications</span></span>](index.md)
* [<span data-ttu-id="a0200-189">Erstellen adaptiver Kacheln</span><span class="sxs-lookup"><span data-stu-id="a0200-189">Create adaptive tiles</span></span>](create-adaptive-tiles.md)
* [<span data-ttu-id="a0200-190">Kachelinhaltsschema</span><span class="sxs-lookup"><span data-stu-id="a0200-190">Tile content schema</span></span>](../tiles-and-notifications/tile-schema.md)
 

 




