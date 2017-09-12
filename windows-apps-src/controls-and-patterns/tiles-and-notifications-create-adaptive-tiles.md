---
author: mijacobs
Description: "Vorlagen für adaptive Kacheln sind ein neues Feature in Windows 10 und ermöglichen den Entwurf eigener Inhalte für Kachelbenachrichtigungen mithilfe einer einfachen, flexiblen Markupsprache, die sich an unterschiedliche Bildschirmdichten anpasst."
title: Erstellen adaptiver Kacheln
ms.assetid: 1246B58E-D6E3-48C7-AD7F-475D113600F9
label: Create adaptive tiles
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.openlocfilehash: b80772109f0349f23feb6ff7f7440ab2e9242288
ms.sourcegitcommit: 9a1310468970c8d1ade0fb200126dff56ea8c9e1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/14/2017
---
# <a name="create-adaptive-tiles"></a><span data-ttu-id="c615a-104">Erstellen adaptiver Kacheln</span><span class="sxs-lookup"><span data-stu-id="c615a-104">Create adaptive tiles</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 


<span data-ttu-id="c615a-105">Vorlagen für adaptive Kacheln sind ein neues Feature in Windows 10 und ermöglichen den Entwurf eigener Inhalte für Kachelbenachrichtigungen mithilfe einer einfachen, flexiblen Markupsprache, die sich an unterschiedliche Bildschirmdichten anpasst.</span><span class="sxs-lookup"><span data-stu-id="c615a-105">Adaptive tile templates are a new feature in Windows 10, allowing you to design your own tile notification content using a simple and flexible markup language that adapts to different screen densities.</span></span> <span data-ttu-id="c615a-106">Dieser Artikel beschreibt, wie Sie adaptive Live-Kacheln für Ihre UWP-App (Universelle Windows-Plattform) erstellen.</span><span class="sxs-lookup"><span data-stu-id="c615a-106">This article tells you how to create adaptive live tiles for your Universal Windows Platform (UWP) app.</span></span> <span data-ttu-id="c615a-107">Die vollständige Liste adaptiver Elemente und Attribute finden Sie unter [Adaptives Kachelschema](tiles-and-notifications-adaptive-tiles-schema.md).</span><span class="sxs-lookup"><span data-stu-id="c615a-107">For the complete list of adaptive elements and attributes, see the [Adaptive tiles schema](tiles-and-notifications-adaptive-tiles-schema.md).</span></span>

<span data-ttu-id="c615a-108">(Wenn gewünscht, können Sie weiterhin die voreingestellten Vorlagen aus dem [Windows8-Kachelvorlagenkatalog](https://msdn.microsoft.com/library/windows/apps/hh761491) beim Entwerfen von Benachrichtigungen für Windows10 verwenden.)</span><span class="sxs-lookup"><span data-stu-id="c615a-108">(If you'd like, you can still use the preset templates from the [Windows 8 tile template catalog](https://msdn.microsoft.com/library/windows/apps/hh761491) when designing notifications for Windows 10.)</span></span>


## <a name="getting-started"></a><span data-ttu-id="c615a-109">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="c615a-109">Getting started</span></span>

**<span data-ttu-id="c615a-110">Installieren Sie die Benachrichtigungsbibliothek.</span><span class="sxs-lookup"><span data-stu-id="c615a-110">Install Notifications library.</span></span>** <span data-ttu-id="c615a-111">Wenn Sie C# anstelle von XML verwenden möchten, um Benachrichtigungen zu generieren, installieren Sie das NuGet-Paket mit dem Namen [Microsoft.Toolkit.Uwp.Notifications](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/). (Suchen Sie nach „Benachrichtigungen UWP“.)</span><span class="sxs-lookup"><span data-stu-id="c615a-111">If you'd like to use C# instead of XML to generate notifications, install the NuGet package named [Microsoft.Toolkit.Uwp.Notifications](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) (search for "notifications uwp").</span></span> <span data-ttu-id="c615a-112">Die in diesem Artikel bereitgestellten C#-Beispiele verwenden Version 1.0.0 des NuGet-Pakets.</span><span class="sxs-lookup"><span data-stu-id="c615a-112">The C# samples provided in this article use version 1.0.0 of the NuGet package.</span></span>

**<span data-ttu-id="c615a-113">Installieren Sie den Notifications Visualizer.</span><span class="sxs-lookup"><span data-stu-id="c615a-113">Install Notifications Visualizer.</span></span>** <span data-ttu-id="c615a-114">Diese kostenlose UWP-App erleichtert das Entwerfen adaptiver Live-Kacheln, indem Ihre Kachel während der Bearbeitung in einer sofortigen visuellen Vorschau dargestellt wird, die mit dem XAML-Editor bzw. der Entwurfsansicht in Visual Studio vergleichbar ist.</span><span class="sxs-lookup"><span data-stu-id="c615a-114">This free UWP app helps you design adaptive live tiles by providing an instant visual preview of your tile as you edit it, similar to Visual Studio's XAML editor/design view.</span></span> <span data-ttu-id="c615a-115">Weitere Informationen finden Sie in [diesem Blogbeitrag](http://blogs.msdn.com/b/tiles_and_toasts/archive/2015/09/22/introducing-notifications-visualizer-for-windows-10.aspx). Der Download von Notifications Visualizer steht [hier](https://www.microsoft.com/store/apps/notifications-visualizer/9nblggh5xsl1) bereit.</span><span class="sxs-lookup"><span data-stu-id="c615a-115">You can read [this blog post](http://blogs.msdn.com/b/tiles_and_toasts/archive/2015/09/22/introducing-notifications-visualizer-for-windows-10.aspx) for more information, and you can download Notifications Visualizer [here](https://www.microsoft.com/store/apps/notifications-visualizer/9nblggh5xsl1).</span></span>


## <a name="how-to-send-a-tile-notification"></a><span data-ttu-id="c615a-116">Senden einer Kachelbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="c615a-116">How to send a tile notification</span></span>

<span data-ttu-id="c615a-117">Lesen Sie den [Schnellstart zum Senden von lokalen Kachelbenachrichtigungen](tiles-and-notifications-sending-a-local-tile-notification.md).</span><span class="sxs-lookup"><span data-stu-id="c615a-117">Please read our [Quickstart on sending local tile notifications](tiles-and-notifications-sending-a-local-tile-notification.md).</span></span> <span data-ttu-id="c615a-118">Die Dokumentation auf dieser Seite beschreibt alle visuellen UI-Möglichkeiten, die Ihnen mit anpassbaren Kacheln zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="c615a-118">The documentation on this page explains all the visual UI possibilities you have with adaptive tiles.</span></span>


## <a name="usage-guidance"></a><span data-ttu-id="c615a-119">Informationen zur Verwendung</span><span class="sxs-lookup"><span data-stu-id="c615a-119">Usage guidance</span></span>


<span data-ttu-id="c615a-120">Adaptive Vorlagen werden für die Unterstützung verschiedener Formfaktoren und Benachrichtigungstypen konzipiert.</span><span class="sxs-lookup"><span data-stu-id="c615a-120">Adaptive templates are designed to work across different form factors and notification types.</span></span> <span data-ttu-id="c615a-121">Elemente wie Gruppen und Untergruppen verknüpfen Inhalte miteinander und implizieren selbst kein bestimmtes visuelles Verhalten.</span><span class="sxs-lookup"><span data-stu-id="c615a-121">Elements such as group and subgroup link together content and don't imply a particular visual behavior on their own.</span></span> <span data-ttu-id="c615a-122">Die endgültige Darstellung einer Benachrichtigung sollte auf dem spezifischen Gerät basieren, auf dem sie angezeigt wird, beispielsweise einem Smartphone, Tablet, Desktop oder anderen Gerät.</span><span class="sxs-lookup"><span data-stu-id="c615a-122">The final appearance of a notification should be based on the specific device on which it will appear, whether it's phone, tablet, or desktop, or another device.</span></span>

<span data-ttu-id="c615a-123">Hinweise sind optionale Attribute, die Elementen hinzugefügt werden können, um ein bestimmtes visuelles Verhalten zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="c615a-123">Hints are optional attributes that can be added to elements in order to achieve a specific visual behavior.</span></span> <span data-ttu-id="c615a-124">Hinweise können spezifisch für Geräte oder Benachrichtigungen sein.</span><span class="sxs-lookup"><span data-stu-id="c615a-124">Hints can be device-specific or notification-specific.</span></span>

## <a name="a-basic-example"></a><span data-ttu-id="c615a-125">Ein einfaches Beispiel</span><span class="sxs-lookup"><span data-stu-id="c615a-125">A basic example</span></span>


<span data-ttu-id="c615a-126">Dieses Beispiel veranschaulicht, was Vorlagen für adaptive Kacheln leisten können.</span><span class="sxs-lookup"><span data-stu-id="c615a-126">This example demonstrates what the adaptive tile templates can produce.</span></span>

```XML
<tile>
  <visual>
  
    <binding template="TileMedium">
      ...
    </binding>
  
    <binding template="TileWide">
      <text hint-style="subtitle">Jennifer Parker</text>
      <text hint-style="captionSubtle">Photos from our trip</text>
      <text hint-style="captionSubtle">Check out these awesome photos I took while in New Zealand!</text>
    </binding>
  
    <binding template="TileLarge">
      ...
    </binding>
  
  </visual>
</tile>
```

```CSharp
TileContent content = new TileContent()
{
    Visual = new TileVisual()
    {
        TileMedium = ...
  
        TileWide = new TileBinding()
        {
            Content = new TileBindingContentAdaptive()
            {
                Children =
                {
                    new AdaptiveText()
                    {
                        Text = "Jennifer Parker",
                        HintStyle = AdaptiveTextStyle.Subtitle
                    },
  
                    new AdaptiveText()
                    {
                        Text = "Photos from our trip",
                        HintStyle = AdaptiveTextStyle.CaptionSubtle
                    },
  
                    new AdaptiveText()
                    {
                        Text = "Check out these awesome photos I took while in New Zealand!",
                        HintStyle = AdaptiveTextStyle.CaptionSubtle
                    }
                }
            }
        },
  
        TileLarge = ...
    }
};
```

**<span data-ttu-id="c615a-127">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="c615a-127">Result:</span></span>**

![Kurzes Beispiel für eine Kachel](images/adaptive-tiles-quicksample.png)

## <a name="tile-sizes"></a><span data-ttu-id="c615a-129">Kachelgrößen</span><span class="sxs-lookup"><span data-stu-id="c615a-129">Tile sizes</span></span>


<span data-ttu-id="c615a-130">Der Inhalt für jede Kachelgröße wird einzeln in getrennten [&lt;binding&gt;](tiles-and-notifications-adaptive-tiles-schema.md)-Elementen innerhalb der XML-Nutzlast angegeben.</span><span class="sxs-lookup"><span data-stu-id="c615a-130">Content for each tile size is individually specified in separate [&lt;binding&gt;](tiles-and-notifications-adaptive-tiles-schema.md) elements within the XML payload.</span></span> <span data-ttu-id="c615a-131">Wählen Sie die Zielgröße aus, indem Sie das template-Attribut auf einen der folgenden Werte festlegen:</span><span class="sxs-lookup"><span data-stu-id="c615a-131">Choose the target size by setting the template attribute to one of the following values:</span></span>

-   <span data-ttu-id="c615a-132">TileSmall</span><span class="sxs-lookup"><span data-stu-id="c615a-132">TileSmall</span></span>
-   <span data-ttu-id="c615a-133">TileMedium</span><span class="sxs-lookup"><span data-stu-id="c615a-133">TileMedium</span></span>
-   <span data-ttu-id="c615a-134">TileWide</span><span class="sxs-lookup"><span data-stu-id="c615a-134">TileWide</span></span>
-   <span data-ttu-id="c615a-135">TileLarge (nur für Desktop)</span><span class="sxs-lookup"><span data-stu-id="c615a-135">TileLarge (only for desktop)</span></span>

<span data-ttu-id="c615a-136">Geben Sie für die XML-Nutzlast einer einzelnen Kachelbenachrichtigung &lt;binding&gt;-Elemente für jede zu unterstützende Kachelgröße an, wie im folgenden Beispiel dargestellt:</span><span class="sxs-lookup"><span data-stu-id="c615a-136">For a single tile notification XML payload, provide &lt;binding&gt; elements for each tile size that you'd like to support, as shown in this example:</span></span>

```XML
<tile>
  <visual>
  
    <binding template="TileSmall">
      <text>Small</text>
    </binding>
  
    <binding template="TileMedium">
      <text>Medium</text>
    </binding>
  
    <binding template="TileWide">
      <text>Wide</text>
    </binding>
  
    <binding template="TileLarge">
      <text>Large</text>
    </binding>
  
  </visual>
</tile>
```

```CSharp
TileContent content = new TileContent()
{
    Visual = new TileVisual()
    {
        TileSmall = new TileBinding()
        {
            Content = new TileBindingContentAdaptive()
            {
                Children =
                {
                    new AdaptiveText() { Text = "Small" }
                }
            }
        },
  
        TileMedium = new TileBinding()
        {
            Content = new TileBindingContentAdaptive()
            {
                Children =
                {
                    new AdaptiveText() { Text = "Medium" }
                }
            }
        },
  
        TileWide = new TileBinding()
        {
            Content = new TileBindingContentAdaptive()
            {
                Children =
                {
                    new AdaptiveText() { Text = "Wide" }
                }
            }
        },
  
        TileLarge = new TileBinding()
        {
            Content = new TileBindingContentAdaptive()
            {
                Children =
                {
                    new AdaptiveText() { Text = "Large" }
                }
            }
        }
    }
};
```

**<span data-ttu-id="c615a-137">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="c615a-137">Result:</span></span>**

![Größen für adaptive Kacheln: klein, mittel, breit und groß](images/adaptive-tiles-sizes.png)

## <a name="branding"></a><span data-ttu-id="c615a-139">Branding</span><span class="sxs-lookup"><span data-stu-id="c615a-139">Branding</span></span>


<span data-ttu-id="c615a-140">Sie können das Branding am unteren Rand einer Live-Kachel (den Anzeigenamen und das Cornerlogo) mit dem branding-Attribut in der Benachrichtigungsnutzlast steuern.</span><span class="sxs-lookup"><span data-stu-id="c615a-140">You can control the branding on the bottom of a live tile (the display name and corner logo) by using the branding attribute on the notification payload.</span></span> <span data-ttu-id="c615a-141">Mit „none“ wird nichts angezeigt, mit „name“ nur der Name, mit „logo“ nur das Logo, und mit „nameAndLogo“ werden Name und Logo angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c615a-141">You can choose to display "none," only the "name," only the "logo," or both with "nameAndLogo."</span></span>

<span data-ttu-id="c615a-142">**Hinweis**  Da Windows Mobile kein Cornerlogo unterstützt, wird unter Mobile anstelle von „logo“ und „nameAndLogo“ standardmäßig „name” verwendet.</span><span class="sxs-lookup"><span data-stu-id="c615a-142">**Note**  Windows Mobile doesn't support the corner logo, so "logo" and "nameAndLogo" default to "name" on Mobile.</span></span>

 

```XML
<visual branding="logo">
  ...
</visual>
```

```CSharp
new TileVisual()
{
    Branding = TileBranding.Logo,
    ...
}
```

**<span data-ttu-id="c615a-143">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="c615a-143">Result:</span></span>**

![Adaptive Kacheln, Name und Logo](images/adaptive-tiles-namelogo.png)

<span data-ttu-id="c615a-145">Das Branding kann für bestimmte Kachelgrößen auf zwei Weisen angewendet werden:</span><span class="sxs-lookup"><span data-stu-id="c615a-145">Branding can be applied for specific tile sizes one of two ways:</span></span>

1. <span data-ttu-id="c615a-146">Durch Anwenden des Attributs auf das [&lt;binding&gt;](tiles-and-notifications-adaptive-tiles-schema.md)-Element</span><span class="sxs-lookup"><span data-stu-id="c615a-146">By applying the attribute on the [&lt;binding&gt;](tiles-and-notifications-adaptive-tiles-schema.md) element</span></span>
2. <span data-ttu-id="c615a-147">Durch Anwenden des Attributs auf das [&lt;visual&gt;](tiles-and-notifications-adaptive-tiles-schema.md) -Element, was sich auf die gesamte Benachrichtigungsnutzlast auswirkt. Wenn Sie für eine Bindung kein Branding angeben, wird das Branding verwendet, das auf dem visual-Element bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="c615a-147">By applying the attribute on the [&lt;visual&gt;](tiles-and-notifications-adaptive-tiles-schema.md) element, which affects the entire notification payload If you don't specify branding for a binding, it will use the branding that's provided on the visual element.</span></span>

```XML
<tile>
  <visual branding="nameAndLogo">
 
    <binding template="TileMedium" branding="logo">
      ...
    </binding>
 
    <!--Inherits branding from visual-->
    <binding template="TileWide">
      ...
    </binding>
 
  </visual>
</tile>
```

```CSharp
TileContent content = new TileContent()
{
    Visual = new TileVisual()
    {
        Branding = TileBranding.NameAndLogo,

        TileMedium = new TileBinding()
        {
            Branding = TileBranding.Logo,
            ...
        },

        // Inherits branding from Visual
        TileWide = new TileBinding()
        {
            ...
        }
    }
};
```

**<span data-ttu-id="c615a-148">Ergebnis bei Standardbranding:</span><span class="sxs-lookup"><span data-stu-id="c615a-148">Default branding result:</span></span>**

![Standardbranding für Kacheln](images/adaptive-tiles-defaultbranding.png)

<span data-ttu-id="c615a-150">Wenn Sie in der Benachrichtigungsnutzlast kein Branding angeben, wird das Branding durch die Eigenschaften der Basiskachel bestimmt.</span><span class="sxs-lookup"><span data-stu-id="c615a-150">If you don't specify the branding in your notification payload, the base tile's properties will determine the branding.</span></span> <span data-ttu-id="c615a-151">Wenn auf der Basiskachel der Anzeigename dargestellt ist, wird für das Branding standardmäßig „name“ verwendet.</span><span class="sxs-lookup"><span data-stu-id="c615a-151">If the base tile shows the display name, then the branding will default to "name."</span></span> <span data-ttu-id="c615a-152">Wenn kein Anzeigename vorhanden ist, wird für das Branding standardmäßig „none“ verwendet.</span><span class="sxs-lookup"><span data-stu-id="c615a-152">Otherwise, the branding will default to "none" if the display name isn't shown.</span></span>

<span data-ttu-id="c615a-153">**Hinweis**  Dies ist eine Änderung gegenüber Windows 8.x, wo das Standardbranding „logo“ lautete.</span><span class="sxs-lookup"><span data-stu-id="c615a-153">**Note**   This is a change from Windows 8.x, in which the default branding was "logo."</span></span>

 

## <a name="display-name"></a><span data-ttu-id="c615a-154">Anzeigename</span><span class="sxs-lookup"><span data-stu-id="c615a-154">Display name</span></span>


<span data-ttu-id="c615a-155">Sie können den Anzeigenamen einer Benachrichtigung überschreiben, indem Sie für das **displayName**-Attribut die gewünschte Textzeichenfolge eingeben.</span><span class="sxs-lookup"><span data-stu-id="c615a-155">You can override the display name of a notification by entering the text string of your choice with the **displayName** attribute.</span></span> <span data-ttu-id="c615a-156">Wie beim Branding können Sie dies für das [&lt;visual&gt;](tiles-and-notifications-adaptive-tiles-schema.md)-Element angeben, was sich auf die gesamte Benachrichtigungsnutzlast auswirkt, oder für das [&lt;binding&gt;](tiles-and-notifications-adaptive-tiles-schema.md)-Element, was nur einzelne Kacheln betrifft.</span><span class="sxs-lookup"><span data-stu-id="c615a-156">As with branding, you can specify this on the [&lt;visual&gt;](tiles-and-notifications-adaptive-tiles-schema.md) element, which affects the entire notification payload, or on the [&lt;binding&gt;](tiles-and-notifications-adaptive-tiles-schema.md) element, which only affects individual tiles.</span></span>

<span data-ttu-id="c615a-157">**Bekanntes Problem**  Wenn Sie unter Windows Mobile „ShortName“ für die Kachel angeben, wird der in der Benachrichtigung angegebene Anzeigename nicht verwendet (stattdessen wird immer „ShortName“ angezeigt).</span><span class="sxs-lookup"><span data-stu-id="c615a-157">**Known Issue**  On Windows Mobile, if you specify a ShortName for your Tile, the display name provided in your notification will not be used (the ShortName will always be displayed).</span></span> 

```XML
<tile>
  <visual branding="nameAndLogo" displayName="Wednesday 22">
 
    <binding template="TileMedium" displayName="Wed. 22">
      ...
    </binding>
 
    <!--Inherits displayName from visual-->
    <binding template="TileWide">
      ...
    </binding>
 
  </visual>
</tile>
```

```CSharp
TileContent content = new TileContent()
{
    Visual = new TileVisual()
    {
        Branding = TileBranding.NameAndLogo,
        DisplayName = "Wednesday 22",

        TileMedium = new TileBinding()
        {
            DisplayName = "Wed. 22",
            ...
        },

        // Inherits DisplayName from Visual
        TileWide = new TileBinding()
        {
            ...
        }
    }
};
```

**<span data-ttu-id="c615a-158">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="c615a-158">Result:</span></span>**

![Anzeigename adaptiver Kacheln](images/adaptive-tiles-displayname.png)

## <a name="text"></a><span data-ttu-id="c615a-160">Text</span><span class="sxs-lookup"><span data-stu-id="c615a-160">Text</span></span>


<span data-ttu-id="c615a-161">Das [&lt;text&gt;](tiles-and-notifications-adaptive-tiles-schema.md)-Element wird zum Anzeigen von Text verwendet.</span><span class="sxs-lookup"><span data-stu-id="c615a-161">The [&lt;text&gt;](tiles-and-notifications-adaptive-tiles-schema.md) element is used to display text.</span></span> <span data-ttu-id="c615a-162">Mithilfe von Hinweisen können Sie die Darstellung von Text anpassen.</span><span class="sxs-lookup"><span data-stu-id="c615a-162">You can use hints to modify how text appears.</span></span>

```XML
<text>This is a line of text</text>
```


```CSharp
new AdaptiveText()
{
    Text = "This is a line of text"
};
```

**<span data-ttu-id="c615a-163">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="c615a-163">Result:</span></span>**

![Text adaptiver Kacheln](images/adaptive-tiles-text.png)

## <a name="text-wrapping"></a><span data-ttu-id="c615a-165">Textumbruch</span><span class="sxs-lookup"><span data-stu-id="c615a-165">Text wrapping</span></span>


<span data-ttu-id="c615a-166">Text wird standardmäßig nicht umbrochen und verläuft über den Kachelrand hinaus.</span><span class="sxs-lookup"><span data-stu-id="c615a-166">By default, text doesn't wrap and will continue off the edge of the tile.</span></span> <span data-ttu-id="c615a-167">Verwenden Sie das **hint-wrap**-Attribut, um den Textumbruch für ein text-Element festzulegen.</span><span class="sxs-lookup"><span data-stu-id="c615a-167">Use the **hint-wrap** attribute to set text wrapping on a text element.</span></span> <span data-ttu-id="c615a-168">Mit **hint-minLines** und **hint-maxLines**, die beide positive ganze Zahlen akzeptieren, können Sie auch die minimale und maximale Zeilenanzahl steuern.</span><span class="sxs-lookup"><span data-stu-id="c615a-168">You can also control the minimum and maximum number of lines by using **hint-minLines** and **hint-maxLines**, both of which accept positive integers.</span></span>

```XML
<text hint-wrap="true">This is a line of wrapping text</text>
```


```CSharp
new AdaptiveText()
{
    Text = "This is a line of wrapping text",
    HintWrap = true
};
```

**<span data-ttu-id="c615a-169">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="c615a-169">Result:</span></span>**

![Adaptive Kachel mit Textumbruch](images/adaptive-tiles-textwrapping.png)

## <a name="text-styles"></a><span data-ttu-id="c615a-171">Textstile</span><span class="sxs-lookup"><span data-stu-id="c615a-171">Text styles</span></span>


<span data-ttu-id="c615a-172">Stile steuern den Schriftgrad, die Schriftfarbe und Schriftbreite von text-Elementen.</span><span class="sxs-lookup"><span data-stu-id="c615a-172">Styles control the font size, color, and weight of text elements.</span></span> <span data-ttu-id="c615a-173">Es sind mehrere Stile verfügbar. Zusätzlich gibt es leichte („subtle“) Variationen jedes Stils, durch die die Deckkraft auf 60% festgelegt und die Textfarbe normalerweise in einem hellgrauen Farbton angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c615a-173">There are a number of available styles, including a "subtle" variation of each style that sets the opacity to 60%, which usually makes the text color a shade of light gray.</span></span>

```XML
<text hint-style="base">Header content</text>
<text hint-style="captionSubtle">Subheader content</text>
```

```CSharp
new AdaptiveText()
{
    Text = "Header content",
    HintStyle = AdaptiveTextStyle.Base
},

new AdaptiveText()
{
    Text = "Subheader content",
    HintStyle = AdaptiveTextStyle.CaptionSubtle
}
```

**<span data-ttu-id="c615a-174">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="c615a-174">Result:</span></span>**

![Textstile adaptiver Kacheln](images/adaptive-tiles-textstyles.png)

<span data-ttu-id="c615a-176">**Hinweis**  Wenn „hint-style“ nicht angegeben ist, wird für den Stil standardmäßig „caption“ verwendet.</span><span class="sxs-lookup"><span data-stu-id="c615a-176">**Note**  The style defaults to caption if hint-style isn't specified.</span></span>

 

**<span data-ttu-id="c615a-177">Allgemeine Textstile</span><span class="sxs-lookup"><span data-stu-id="c615a-177">Basic text styles</span></span>**

|                                |                           |             |
|--------------------------------|---------------------------|-------------|
| <span data-ttu-id="c615a-178">&lt;text hint-style="\*" /&gt;</span><span class="sxs-lookup"><span data-stu-id="c615a-178">&lt;text hint-style="\*" /&gt;</span></span> | <span data-ttu-id="c615a-179">Zeichenhöhe</span><span class="sxs-lookup"><span data-stu-id="c615a-179">Font height</span></span>               | <span data-ttu-id="c615a-180">Schriftbreite</span><span class="sxs-lookup"><span data-stu-id="c615a-180">Font weight</span></span> |
| <span data-ttu-id="c615a-181">caption</span><span class="sxs-lookup"><span data-stu-id="c615a-181">caption</span></span>                        | <span data-ttu-id="c615a-182">12 effektive Pixel (epx)</span><span class="sxs-lookup"><span data-stu-id="c615a-182">12 effective pixels (epx)</span></span> | <span data-ttu-id="c615a-183">Regular</span><span class="sxs-lookup"><span data-stu-id="c615a-183">Regular</span></span>     |
| <span data-ttu-id="c615a-184">body</span><span class="sxs-lookup"><span data-stu-id="c615a-184">body</span></span>                           | <span data-ttu-id="c615a-185">15Epx</span><span class="sxs-lookup"><span data-stu-id="c615a-185">15 epx</span></span>                    | <span data-ttu-id="c615a-186">Regular</span><span class="sxs-lookup"><span data-stu-id="c615a-186">Regular</span></span>     |
| <span data-ttu-id="c615a-187">base</span><span class="sxs-lookup"><span data-stu-id="c615a-187">base</span></span>                           | <span data-ttu-id="c615a-188">15Epx</span><span class="sxs-lookup"><span data-stu-id="c615a-188">15 epx</span></span>                    | <span data-ttu-id="c615a-189">Semibold</span><span class="sxs-lookup"><span data-stu-id="c615a-189">Semibold</span></span>    |
| <span data-ttu-id="c615a-190">subtitle</span><span class="sxs-lookup"><span data-stu-id="c615a-190">subtitle</span></span>                       | <span data-ttu-id="c615a-191">20Epx</span><span class="sxs-lookup"><span data-stu-id="c615a-191">20 epx</span></span>                    | <span data-ttu-id="c615a-192">Regular</span><span class="sxs-lookup"><span data-stu-id="c615a-192">Regular</span></span>     |
| <span data-ttu-id="c615a-193">title</span><span class="sxs-lookup"><span data-stu-id="c615a-193">title</span></span>                          | <span data-ttu-id="c615a-194">24Epx</span><span class="sxs-lookup"><span data-stu-id="c615a-194">24 epx</span></span>                    | <span data-ttu-id="c615a-195">Semilight</span><span class="sxs-lookup"><span data-stu-id="c615a-195">Semilight</span></span>   |
| <span data-ttu-id="c615a-196">subheader</span><span class="sxs-lookup"><span data-stu-id="c615a-196">subheader</span></span>                      | <span data-ttu-id="c615a-197">34Epx</span><span class="sxs-lookup"><span data-stu-id="c615a-197">34 epx</span></span>                    | <span data-ttu-id="c615a-198">Light</span><span class="sxs-lookup"><span data-stu-id="c615a-198">Light</span></span>       |
| <span data-ttu-id="c615a-199">header</span><span class="sxs-lookup"><span data-stu-id="c615a-199">header</span></span>                         | <span data-ttu-id="c615a-200">46Epx</span><span class="sxs-lookup"><span data-stu-id="c615a-200">46 epx</span></span>                    | <span data-ttu-id="c615a-201">Light</span><span class="sxs-lookup"><span data-stu-id="c615a-201">Light</span></span>       |

 

**<span data-ttu-id="c615a-202">Numerische Variationen des Textstils</span><span class="sxs-lookup"><span data-stu-id="c615a-202">Numeral text style variations</span></span>**

<span data-ttu-id="c615a-203">Durch diese Variationen wird die Zeilenhöhe verringert, sodass der Abstand zu Inhalten über und unter der Zeile deutlich kleiner wird.</span><span class="sxs-lookup"><span data-stu-id="c615a-203">These variations reduce the line height so that content above and below come much closer to the text.</span></span>

|                  |
|------------------|
| <span data-ttu-id="c615a-204">titleNumeral</span><span class="sxs-lookup"><span data-stu-id="c615a-204">titleNumeral</span></span>     |
| <span data-ttu-id="c615a-205">subheaderNumeral</span><span class="sxs-lookup"><span data-stu-id="c615a-205">subheaderNumeral</span></span> |
| <span data-ttu-id="c615a-206">headerNumeral</span><span class="sxs-lookup"><span data-stu-id="c615a-206">headerNumeral</span></span>    |

 

**<span data-ttu-id="c615a-207">Leichte Variationen des Textstils</span><span class="sxs-lookup"><span data-stu-id="c615a-207">Subtle text style variations</span></span>**

<span data-ttu-id="c615a-208">Jeder Stil weist eine leichte Variation auf, durch die der Text eine 60%-ige Deckkraft erhält und normalerweise in einem hellgrauen Farbton angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c615a-208">Each style has a subtle variation that gives the text a 60% opacity, which usually makes the text color a shade of light gray.</span></span>

|                        |
|------------------------|
| <span data-ttu-id="c615a-209">captionSubtle</span><span class="sxs-lookup"><span data-stu-id="c615a-209">captionSubtle</span></span>          |
| <span data-ttu-id="c615a-210">bodySubtle</span><span class="sxs-lookup"><span data-stu-id="c615a-210">bodySubtle</span></span>             |
| <span data-ttu-id="c615a-211">baseSubtle</span><span class="sxs-lookup"><span data-stu-id="c615a-211">baseSubtle</span></span>             |
| <span data-ttu-id="c615a-212">subtitleSubtle</span><span class="sxs-lookup"><span data-stu-id="c615a-212">subtitleSubtle</span></span>         |
| <span data-ttu-id="c615a-213">titleSubtle</span><span class="sxs-lookup"><span data-stu-id="c615a-213">titleSubtle</span></span>            |
| <span data-ttu-id="c615a-214">titleNumeralSubtle</span><span class="sxs-lookup"><span data-stu-id="c615a-214">titleNumeralSubtle</span></span>     |
| <span data-ttu-id="c615a-215">subheaderSubtle</span><span class="sxs-lookup"><span data-stu-id="c615a-215">subheaderSubtle</span></span>        |
| <span data-ttu-id="c615a-216">subheaderNumeralSubtle</span><span class="sxs-lookup"><span data-stu-id="c615a-216">subheaderNumeralSubtle</span></span> |
| <span data-ttu-id="c615a-217">headerSubtle</span><span class="sxs-lookup"><span data-stu-id="c615a-217">headerSubtle</span></span>           |
| <span data-ttu-id="c615a-218">headerNumeralSubtle</span><span class="sxs-lookup"><span data-stu-id="c615a-218">headerNumeralSubtle</span></span>    |

 

## <a name="text-alignment"></a><span data-ttu-id="c615a-219">Textausrichtung</span><span class="sxs-lookup"><span data-stu-id="c615a-219">Text alignment</span></span>


<span data-ttu-id="c615a-220">Text kann horizontal, linksbündig, zentriert oder rechtsbündig ausgerichtet sein.</span><span class="sxs-lookup"><span data-stu-id="c615a-220">Text can be horizontally aligned left, center, or right.</span></span> <span data-ttu-id="c615a-221">Bei einer von links nach rechts gelesenen Sprache, wie Deutsch, ist Text standardmäßig linksbündig ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="c615a-221">In left-to-right languages like English, text defaults to left-aligned.</span></span> <span data-ttu-id="c615a-222">Bei einer von rechts nach links gelesenen Sprache, wie Arabisch, ist Text standardmäßig rechtsbündig ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="c615a-222">In right-to-left languages like Arabic, text defaults to right-aligned.</span></span> <span data-ttu-id="c615a-223">Mit dem **hint-align**-Attribut können Sie die Ausrichtung für Elemente manuell festlegen.</span><span class="sxs-lookup"><span data-stu-id="c615a-223">You can manually set alignment with the **hint-align** attribute on elements.</span></span>

```XML
<text hint-align="center">Hello</text>
```


```CSharp
new AdaptiveText()
{
    Text = "Hello",
    HintAlign = AdaptiveTextAlign.Center
};
```

**<span data-ttu-id="c615a-224">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="c615a-224">Result:</span></span>**

![Textausrichtung adaptiver Kacheln](images/adaptive-tiles-textalignment.png)

## <a name="groups-and-subgroups"></a><span data-ttu-id="c615a-226">Gruppen und Untergruppen</span><span class="sxs-lookup"><span data-stu-id="c615a-226">Groups and subgroups</span></span>


<span data-ttu-id="c615a-227">Mit Gruppen können Sie semantisch deklarieren, dass sich Inhalte in der Gruppe aufeinander beziehen und vollständig angezeigt werden müssen, damit sie Sinn ergeben.</span><span class="sxs-lookup"><span data-stu-id="c615a-227">Groups allow you to semantically declare that the content inside the group is related and must be displayed in its entirety for the content to make sense.</span></span> <span data-ttu-id="c615a-228">Beispielsweise können Sie über zwei text-Elemente in Form einer Überschrift und einer Unterüberschrift verfügen, und es würde keinen Sinn ergeben, wenn nur die Überschrift angezeigt würde.</span><span class="sxs-lookup"><span data-stu-id="c615a-228">For example, you might have two text elements, a header, and a subheader, and it would not make sense for only the header to be shown.</span></span> <span data-ttu-id="c615a-229">Durch die Gruppierung dieser Elemente innerhalb einer Untergruppe werden entweder alle Elemente angezeigt (sofern sie in den Anzeigebereich passen) oder keine Elemente angezeigt (wenn nicht genügend Platz vorhanden ist).</span><span class="sxs-lookup"><span data-stu-id="c615a-229">By grouping those elements inside a subgroup, the elements will either all be displayed (if they can fit) or not be displayed at all (because they can't fit).</span></span>

<span data-ttu-id="c615a-230">Um optimale Ergebnisse auf unterschiedlichen Geräten und Bildschirmen zu erzielen, sollten Sie mehrere Gruppen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="c615a-230">To provide the best experience across devices and screens, provide multiple groups.</span></span> <span data-ttu-id="c615a-231">Mit mehreren Gruppen kann sich die Kachel an größere Bildschirme anpassen.</span><span class="sxs-lookup"><span data-stu-id="c615a-231">Having multiple groups allows your tile to adapt to larger screens.</span></span>

<span data-ttu-id="c615a-232">**Hinweis**  Das einzige gültige untergeordnete Element einer Gruppe ist eine Untergruppe.</span><span class="sxs-lookup"><span data-stu-id="c615a-232">**Note**  The only valid child of a group is a subgroup.</span></span>

 

```XML
<binding template="TileWide" branding="nameAndLogo">
  <group>
    <subgroup>
      <text hint-style="subtitle">Jennifer Parker</text>
      <text hint-style="captionSubtle">Photos from our trip</text>
      <text hint-style="captionSubtle">Check out these awesome photos I took while in New Zealand!</text>
    </subgroup>
  </group>
 
  <text />
 
  <group>
    <subgroup>
      <text hint-style="subtitle">Steve Bosniak</text>
      <text hint-style="captionSubtle">Build 2015 Dinner</text>
      <text hint-style="captionSubtle">Want to go out for dinner after Build tonight?</text>
    </subgroup>
  </group>
</binding>
```

```CSharp
TileWide = new TileBinding()
{
    Branding = TileBranding.NameAndLogo,
    Content = new TileBindingContentAdaptive()
    {
        Children =
        {
            CreateGroup(
                from: "Jennifer Parker",
                subject: "Photos from our trip",
                body: "Check out these awesome photos I took while in New Zealand!"),

            // For spacing
            new AdaptiveText(),

            CreateGroup(
                from: "Steve Bosniak",
                subject: "Build 2015 Dinner",
                body: "Want to go out for dinner after Build tonight?")
        }
    }
}

...

private static AdaptiveGroup CreateGroup(string from, string subject, string body)
{
    return new AdaptiveGroup()
    {
        Children =
        {
            new AdaptiveSubgroup()
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
    };
}
```

**<span data-ttu-id="c615a-233">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="c615a-233">Result:</span></span>**

![Gruppen und Untergruppen adaptiver Kacheln](images/adaptive-tiles-groups-subgroups.png)

## <a name="subgroups-columns"></a><span data-ttu-id="c615a-235">Untergruppen (Spalten)</span><span class="sxs-lookup"><span data-stu-id="c615a-235">Subgroups (columns)</span></span>


<span data-ttu-id="c615a-236">Mithilfe von Untergruppen können Sie Daten außerdem in semantische Abschnitte innerhalb einer Gruppe unterteilen.</span><span class="sxs-lookup"><span data-stu-id="c615a-236">Subgroups also allow you to divide data into semantic sections within a group.</span></span> <span data-ttu-id="c615a-237">Bei Live-Kacheln werden Untergruppen visuell als Spalten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c615a-237">For live tiles, this visually translates to columns.</span></span>

<span data-ttu-id="c615a-238">Mit dem **hint-weight**-Attribut wird die Breite von Spalten gesteuert.</span><span class="sxs-lookup"><span data-stu-id="c615a-238">The **hint-weight** attribute lets you to control the widths of columns.</span></span> <span data-ttu-id="c615a-239">Der **hint-weight**-Wert wird als gewichteter Anteil am verfügbaren Platz ausgedrückt, was mit dem **GridUnitType.Star**-Verhalten übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="c615a-239">The value of **hint-weight** is expressed as a weighted proportion of available space, which is identical to **GridUnitType.Star** behavior.</span></span> <span data-ttu-id="c615a-240">Weisen Sie jeder Gewichtung 1 zu, um Spalten mit gleicher Breite zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="c615a-240">For equal-width columns, assign each weight to 1.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="c615a-241">hint-weight</span><span class="sxs-lookup"><span data-stu-id="c615a-241">hint-weight</span></span></td>
<td align="left"><span data-ttu-id="c615a-242">Prozentuale Breite</span><span class="sxs-lookup"><span data-stu-id="c615a-242">Percentage of width</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="c615a-243">1</span><span class="sxs-lookup"><span data-stu-id="c615a-243">1</span></span></td>
<td align="left"><span data-ttu-id="c615a-244">25 %</span><span class="sxs-lookup"><span data-stu-id="c615a-244">25%</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="c615a-245">1</span><span class="sxs-lookup"><span data-stu-id="c615a-245">1</span></span></td>
<td align="left"><span data-ttu-id="c615a-246">25 %</span><span class="sxs-lookup"><span data-stu-id="c615a-246">25%</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="c615a-247">1</span><span class="sxs-lookup"><span data-stu-id="c615a-247">1</span></span></td>
<td align="left"><span data-ttu-id="c615a-248">25 %</span><span class="sxs-lookup"><span data-stu-id="c615a-248">25%</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="c615a-249">1</span><span class="sxs-lookup"><span data-stu-id="c615a-249">1</span></span></td>
<td align="left"><span data-ttu-id="c615a-250">25 %</span><span class="sxs-lookup"><span data-stu-id="c615a-250">25%</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="c615a-251">Gesamtgewichtung: 4</span><span class="sxs-lookup"><span data-stu-id="c615a-251">Total weight: 4</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

![Untergruppen, Spalten mit gleicher Breite](images/adaptive-tiles-subgroups01.png)

<span data-ttu-id="c615a-253">Um eine Spalte doppelt so groß wie eine andere Spalte darzustellen, weisen Sie der kleineren Spalte die Gewichtung 1 und der größeren Spalte die Gewichtung 2 zu.</span><span class="sxs-lookup"><span data-stu-id="c615a-253">To make one column twice as large as another column, assign the smaller column a weight of 1 and the larger column a weight of 2.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="c615a-254">hint-weight</span><span class="sxs-lookup"><span data-stu-id="c615a-254">hint-weight</span></span></td>
<td align="left"><span data-ttu-id="c615a-255">Prozentuale Breite</span><span class="sxs-lookup"><span data-stu-id="c615a-255">Percentage of width</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="c615a-256">1</span><span class="sxs-lookup"><span data-stu-id="c615a-256">1</span></span></td>
<td align="left"><span data-ttu-id="c615a-257">33,3 %</span><span class="sxs-lookup"><span data-stu-id="c615a-257">33.3%</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="c615a-258">2</span><span class="sxs-lookup"><span data-stu-id="c615a-258">2</span></span></td>
<td align="left"><span data-ttu-id="c615a-259">66,7 %</span><span class="sxs-lookup"><span data-stu-id="c615a-259">66.7%</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="c615a-260">Gesamtgewichtung: 3</span><span class="sxs-lookup"><span data-stu-id="c615a-260">Total weight: 3</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

![Untergruppen, eine Spalte ist doppelt so groß wie die andere](images/adaptive-tiles-subgroups02.png)

<span data-ttu-id="c615a-262">Wenn Ihre erste Spalte 20% und die zweite Spalte 80% der gesamten Breite einnehmen soll, weisen Sie der ersten Gewichtung 20 und der zweiten Gewichtung 80 zu.</span><span class="sxs-lookup"><span data-stu-id="c615a-262">If you want your first column to take up 20% of the total width and your second column to take up 80% of the total width, assign the first weight to 20 and the second weight to 80.</span></span> <span data-ttu-id="c615a-263">Wenn die Gewichtungen insgesamt 100 ergeben, werden sie prozentual ausgedrückt.</span><span class="sxs-lookup"><span data-stu-id="c615a-263">If your total weights equal 100, they'll act as percentages.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="c615a-264">hint-weight</span><span class="sxs-lookup"><span data-stu-id="c615a-264">hint-weight</span></span></td>
<td align="left"><span data-ttu-id="c615a-265">Prozentuale Breite</span><span class="sxs-lookup"><span data-stu-id="c615a-265">Percentage of width</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="c615a-266">20</span><span class="sxs-lookup"><span data-stu-id="c615a-266">20</span></span></td>
<td align="left"><span data-ttu-id="c615a-267">20 %</span><span class="sxs-lookup"><span data-stu-id="c615a-267">20%</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="c615a-268">80</span><span class="sxs-lookup"><span data-stu-id="c615a-268">80</span></span></td>
<td align="left"><span data-ttu-id="c615a-269">80%</span><span class="sxs-lookup"><span data-stu-id="c615a-269">80%</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="c615a-270">Gesamtgewichtung: 100</span><span class="sxs-lookup"><span data-stu-id="c615a-270">Total weight: 100</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

![Untergruppen mit einer Gesamtgewichtung von 100](images/adaptive-tiles-subgroups03.png)

<span data-ttu-id="c615a-272">**Hinweis**  Zwischen Spalten wird automatisch ein Rand von 8 Pixeln eingefügt.</span><span class="sxs-lookup"><span data-stu-id="c615a-272">**Note**  An 8-pixel margin is automatically added between the columns.</span></span>

 

<span data-ttu-id="c615a-273">Wenn Sie über mehr als zwei Untergruppen verfügen, geben Sie **hint-weight** an (akzeptiert nur positive ganze Zahlen).</span><span class="sxs-lookup"><span data-stu-id="c615a-273">When you have more than two subgroups, you should specify the **hint-weight**, which only accepts positive integers.</span></span> <span data-ttu-id="c615a-274">Wenn Sie für die erste Untergruppe „hint-weight“ nicht angeben, wird ihr die Gewichtung 50 zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="c615a-274">If you don't specify hint-weight for the first subgroup, it will be assigned a weight of 50.</span></span> <span data-ttu-id="c615a-275">Der nächsten Untergruppe, für die „hint-weight“ nicht angegeben wurde, wird die Gewichtung 100 abzüglich der Summe der vorherigen Gewichtungen oder 1 zugewiesen, wenn das Ergebnis 0 (null) ist.</span><span class="sxs-lookup"><span data-stu-id="c615a-275">The next subgroup that doesn't have a specified hint-weight will be assigned a weight equal to 100 minus the sum of the preceding weights, or to 1 if the result is zero.</span></span> <span data-ttu-id="c615a-276">Den übrigen Untergruppen, für die „hint-weight“ nicht angegeben wurde, wird die Gewichtung 1 zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="c615a-276">The remaining subgroups that don't have specified hint-weights will be assigned a weight of 1.</span></span>

<span data-ttu-id="c615a-277">Im Folgenden sehen Sie den Beispielcode für eine Wetter-Kachel, die zeigt, wie Sie eine Kachel mit fünf gleich breiten Spalten erhalten:</span><span class="sxs-lookup"><span data-stu-id="c615a-277">Here's sample code for a weather tile that shows how you can achieve a tile with five columns of equal width:</span></span>

```XML
<binding template="TileWide" displayName="Seattle" branding="name">
  <group>
    <subgroup hint-weight="1">
      <text hint-align="center">Mon</text>
      <image src="Assets\Weather\Mostly Cloudy.png" hint-removeMargin="true"/>
      <text hint-align="center">63°</text>
      <text hint-align="center" hint-style="captionsubtle">42°</text>
    </subgroup>
    <subgroup hint-weight="1">
      <text hint-align="center">Tue</text>
      <image src="Assets\Weather\Cloudy.png" hint-removeMargin="true"/>
      <text hint-align="center">57°</text>
      <text hint-align="center" hint-style="captionsubtle">38°</text>
    </subgroup>
    <subgroup hint-weight="1">
      <text hint-align="center">Wed</text>
      <image src="Assets\Weather\Sunny.png" hint-removeMargin="true"/>
      <text hint-align="center">59°</text>
      <text hint-align="center" hint-style="captionsubtle">43°</text>
    </subgroup>
    <subgroup hint-weight="1">
      <text hint-align="center">Thu</text>
      <image src="Assets\Weather\Sunny.png" hint-removeMargin="true"/>
      <text hint-align="center">62°</text>
      <text hint-align="center" hint-style="captionsubtle">42°</text>
    </subgroup>
    <subgroup hint-weight="1">
      <text hint-align="center">Fri</text>
      <image src="Assets\Weather\Sunny.png" hint-removeMargin="true"/>
      <text hint-align="center">71°</text>
      <text hint-align="center" hint-style="captionsubtle">66°</text>
    </subgroup>
  </group>
</binding>
```

```CSharp
TileWide = new TileBinding()
{
    DisplayName = "Seattle",
    Branding = TileBranding.Name,
    Content = new TileBindingContentAdaptive()
    {
        Children =
        {
            new AdaptiveGroup()
            {
                Children =
                {
                    CreateSubgroup("Mon", "Mostly Cloudy.png", "63°", "42°"),
                    CreateSubgroup("Tue", "Cloudy.png", "57°", "38°"),
                    CreateSubgroup("Wed", "Sunny.png", "59°", "43°"),
                    CreateSubgroup("Thu", "Sunny.png", "62°", "42°"),
                    CreateSubgroup("Fri", "Sunny.png", "71°", "66°")
                }
            }
        }
    }
}

...

private static AdaptiveSubgroup CreateSubgroup(string day, string image, string highTemp, string lowTemp)
{
    return new AdaptiveSubgroup()
    {
        HintWeight = 1,
        Children =
        {
            new AdaptiveText()
            {
                Text = day,
                HintAlign = AdaptiveTextAlign.Center
            },
            new AdaptiveImage()
            {
                Source = "Assets/Weather/" + image,
                HintRemoveMargin = true
            },
            new AdaptiveText()
            {
                Text = highTemp,
                HintAlign = AdaptiveTextAlign.Center
            },
            new AdaptiveText()
            {
                Text = lowTemp,
                HintAlign = AdaptiveTextAlign.Center,
                HintStyle = AdaptiveTextStyle.CaptionSubtle
            }
        }
    };
}
```

**<span data-ttu-id="c615a-278">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="c615a-278">Result:</span></span>**

![Beispiel für eine Wetter-Kachel](images/adaptive-tiles-weathertile.png)

## <a name="images"></a><span data-ttu-id="c615a-280">Bilder</span><span class="sxs-lookup"><span data-stu-id="c615a-280">Images</span></span>


<span data-ttu-id="c615a-281">Mithilfe des &lt;image&gt;-Elements werden Bilder auf der Kachelbenachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c615a-281">The &lt;image&gt; element is used to display images on the tile notification.</span></span> <span data-ttu-id="c615a-282">Bilder können als Inlinebilder im Kachelinhalt (Standard), als Hintergrundbild hinter dem Inhalt oder als animiertes Vorschaubild, das von oben in die Benachrichtigung hineingleitet, konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="c615a-282">Images can be placed inline within the tile content (default), as a background image behind your content, or as a peek image that animates in from the top of the notification.</span></span>

<span data-ttu-id="c615a-283">**Hinweis**   Für die [Dateigröße und Abmessungen von Bildern](https://msdn.microsoft.com/library/windows/apps/hh781198) gelten Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="c615a-283">**Note**   There are [restrictions on the file size and dimensions of images](https://msdn.microsoft.com/library/windows/apps/hh781198).</span></span>

 

<span data-ttu-id="c615a-284">Wenn kein zusätzliches Verhalten angegeben wird, verkleinern bzw. vergrößern sich Bilder gleichmäßig in Anpassung an die verfügbare Breite.</span><span class="sxs-lookup"><span data-stu-id="c615a-284">With no extra behaviors specified, images will uniformly shrink or expand to fill the available width.</span></span> <span data-ttu-id="c615a-285">Das folgende Beispiel zeigt eine Kachel mit zwei Spalten und Inlinebildern.</span><span class="sxs-lookup"><span data-stu-id="c615a-285">The sample below shows a tile using two columns and inline images.</span></span> <span data-ttu-id="c615a-286">Die Inlinebilder werden gestreckt, um die Spaltenbreite auszufüllen.</span><span class="sxs-lookup"><span data-stu-id="c615a-286">The inline images stretch to fill the width of the column.</span></span>

```XML
<binding template="TileMedium" displayName="Seattle" branding="name">
  <group>
    <subgroup>
      <text hint-align="center">Mon</text>
      <image src="Assets\Apps\Weather\Mostly Cloudy.png" hint-removeMargin="true"/>
      <text hint-align="center">63°</text>
      <text hint-style="captionsubtle" hint-align="center">42°</text>
    </subgroup>
    <subgroup>
      <text hint-align="center">Tue</text>
      <image src="Assets\Apps\Weather\Cloudy.png" hint-removeMargin="true"/>
      <text hint-align="center">57°</text>
      <text hint-style="captionSubtle" hint-align="center">38°</text>
    </subgroup>
  </group>
</binding>
```

```CSharp
TileMedium = new TileBinding()
{
    DisplayName = "Seattle",
    Branding = TileBranding.Name,
    Content = new TileBindingContentAdaptive()
    {
        Children =
        {
            new AdaptiveGroup()
            {
                Children =
                {
                    CreateSubgroup("Mon", "Mostly Cloudy.png", "63°", "42°"),
                    CreateSubgroup("Tue", "Cloudy.png", "57°", "38°")
                }
            }
        }
    }
}
...
private static AdaptiveSubgroup CreateSubgroup(string day, string image, string highTemp, string lowTemp)
{
    return new AdaptiveSubgroup()
    {
        Children =
        {
            new AdaptiveText()
            {
                Text = day,
                HintAlign = AdaptiveTextAlign.Center
            },
            new AdaptiveImage()
            {
                Source = "Assets/Weather/" + image,
                HintRemoveMargin = true
            },
            new AdaptiveText()
            {
                Text = highTemp,
                HintAlign = AdaptiveTextAlign.Center
            },
            new AdaptiveText()
            {
                Text = lowTemp,
                HintAlign = AdaptiveTextAlign.Center,
                HintStyle = AdaptiveTextStyle.CaptionSubtle
            }
        }
    };
}
```

**<span data-ttu-id="c615a-287">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="c615a-287">Result:</span></span>**

![Bildbeispiel](images/adaptive-tiles-images01.png)

<span data-ttu-id="c615a-289">Bilder, die im &lt;binding&gt;-Stammelement oder in der ersten Gruppe enthalten sind, werden ebenfalls gestreckt, um die verfügbare Höhe auszunutzen.</span><span class="sxs-lookup"><span data-stu-id="c615a-289">Images placed in the &lt;binding&gt; root, or in the first group, will also stretch to fit the available height.</span></span>

### <a name="image-alignment"></a><span data-ttu-id="c615a-290">Bildausrichtung</span><span class="sxs-lookup"><span data-stu-id="c615a-290">Image alignment</span></span>

<span data-ttu-id="c615a-291">Bilder können mit dem **hint-align**-Attribut linksbündig, zentriert oder rechtsbündig ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="c615a-291">Images can be set to align left, center, or right using the **hint-align** attribute.</span></span> <span data-ttu-id="c615a-292">Dies bewirkt auch, dass Bilder in ihrer systemeigenen Auflösung angezeigt und nicht gestreckt werden, um die gesamte Breite auszufüllen.</span><span class="sxs-lookup"><span data-stu-id="c615a-292">This will also cause images to display at their native resolution instead of stretching to fill width.</span></span>

```XML
<binding template="TileLarge">
  <image src="Assets/fable.jpg" hint-align="center"/>
</binding>
```

```CSharp
TileLarge = new TileBinding()
{
    Content = new TileBindingContentAdaptive()
    {
        Children =
        {
            new AdaptiveImage()
            {
                Source = "Assets/fable.jpg",
                HintAlign = AdaptiveImageAlign.Center
            }
        }
    }
}
```

**<span data-ttu-id="c615a-293">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="c615a-293">Result:</span></span>**

![Beispiel für die Bildausrichtung (linksbündig, zentriert, rechtsbündig)](images/adaptive-tiles-imagealignment.png)

### <a name="image-margins"></a><span data-ttu-id="c615a-295">Bildränder</span><span class="sxs-lookup"><span data-stu-id="c615a-295">Image margins</span></span>

<span data-ttu-id="c615a-296">Zwischen Inlinebildern und darüber oder darunter angeordneten Inhalten befindet sich standardmäßig ein Rand von 8 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="c615a-296">By default, inline images have an 8-pixel margin between any content above or below the image.</span></span> <span data-ttu-id="c615a-297">Dieser Rand kann entfernt werden, indem Sie das **hint-removeMargin**-Attribut für das Bild verwenden.</span><span class="sxs-lookup"><span data-stu-id="c615a-297">This margin can be removed by using the **hint-removeMargin** attribute on the image.</span></span> <span data-ttu-id="c615a-298">Für Bilder wird allerdings immer der 8-Pixel-Rand vom Rand der Kachel und für Untergruppen (Spalten) immer der 8-Pixel-Abstand zwischen Spalten beibehalten.</span><span class="sxs-lookup"><span data-stu-id="c615a-298">However, images always retain the 8-pixel margin from the edge of the tile, and subgroups (columns) always retain the 8-pixel padding between columns.</span></span>

```XML
<binding template="TileMedium" branding="none">
  <group>
    <subgroup>
      <text hint-align="center">Mon</text>
      <image src="Assets\Numbers\4.jpg" hint-removeMargin="true"/>
      <text hint-align="center">63°</text>
      <text hint-style="captionsubtle" hint-align="center">42°</text>
    </subgroup>
    <subgroup>
      <text hint-align="center">Tue</text>
      <image src="Assets\Numbers\3.jpg" hint-removeMargin="true"/>
      <text hint-align="center">57°</text>
      <text hint-style="captionsubtle" hint-align="center">38°</text>
    </subgroup>
  </group>
</binding>
```

```CSharp
TileMedium = new TileBinding()
{
    Branding = TileBranding.None,
    Content = new TileBindingContentAdaptive()
    {
        Children =
        {
            new AdaptiveGroup()
            {
                Children =
                {
                    CreateSubgroup("Mon", "4.jpg", "63°", "42°"),
                    CreateSubgroup("Tue", "3.jpg", "57°", "38°")
                }
            }
        }
    }
}

...

private static AdaptiveSubgroup CreateSubgroup(string day, string image, string highTemp, string lowTemp)
{
    return new AdaptiveSubgroup()
    {
        HintWeight = 1,
        Children =
        {
            new AdaptiveText()
            {
                Text = day,
                HintAlign = AdaptiveTextAlign.Center
            },
            new AdaptiveImage()
            {
                Source = "Assets/Numbers/" + image,
                HintRemoveMargin = true
            },
            new AdaptiveText()
            {
                Text = highTemp,
                HintAlign = AdaptiveTextAlign.Center
            },
            new AdaptiveText()
            {
                Text = lowTemp,
                HintAlign = AdaptiveTextAlign.Center,
                HintStyle = AdaptiveTextStyle.CaptionSubtle
            }
        }
    };
}
```

![Beispiel für „hint-removeMargin“](images/adaptive-tiles-removemargin.png)

### <a name="image-cropping"></a><span data-ttu-id="c615a-300">Zuschneiden von Bildern</span><span class="sxs-lookup"><span data-stu-id="c615a-300">Image cropping</span></span>

<span data-ttu-id="c615a-301">Bilder können mit dem **hint-crop**-Attribut, das derzeit nur die Werte „none“ (Standard) oder „circle“ unterstützt, kreisförmig zugeschnitten werden.</span><span class="sxs-lookup"><span data-stu-id="c615a-301">Images can be cropped into a circle using the **hint-crop** attribute, which currently only supports the values "none" (default) or "circle."</span></span>

```XML
<binding template="TileLarge" hint-textStacking="center">
  <group>
    <subgroup hint-weight="1"/>
    <subgroup hint-weight="2">
      <image src="Assets/Apps/Hipstame/hipster.jpg" hint-crop="circle"/>
    </subgroup>
    <subgroup hint-weight="1"/>
  </group>
 
  <text hint-style="title" hint-align="center">Hi,</text>
  <text hint-style="subtitleSubtle" hint-align="center">MasterHip</text>
</binding>
```

```CSharp
TileLarge = new TileBinding()
{
    Content = new TileBindingContentAdaptive()
    {
        TextStacking = TileTextStacking.Center,
        Children =
        {
            new AdaptiveGroup()
            {
                Children =
                {
                    new AdaptiveSubgroup() { HintWeight = 1 },
                    new AdaptiveSubgroup()
                    {
                        HintWeight = 2,
                        Children =
                        {
                            new AdaptiveImage()
                            {
                                Source = "Assets/Apps/Hipstame/hipster.jpg",
                                HintCrop = AdaptiveImageCrop.Circle
                            }
                        }
                    },
                    new AdaptiveSubgroup() { HintWeight = 1 }
                }
            },
            new AdaptiveText()
            {
                Text = "Hi,",
                HintStyle = AdaptiveTextStyle.Title,
                HintAlign = AdaptiveTextAlign.Center
            },
            new AdaptiveText()
            {
                Text = "MasterHip",
                HintStyle = AdaptiveTextStyle.SubtitleSubtle,
                HintAlign = AdaptiveTextAlign.Center
            }
        }
    }
}
```

**<span data-ttu-id="c615a-302">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="c615a-302">Result:</span></span>**

![Beispiel für das Zuschneiden eines Bilds](images/adaptive-tiles-imagecropping.png)

### <a name="background-image"></a><span data-ttu-id="c615a-304">Hintergrundbild</span><span class="sxs-lookup"><span data-stu-id="c615a-304">Background image</span></span>

<span data-ttu-id="c615a-305">Um ein Hintergrundbild festzulegen, platzieren Sie ein image-Element im Stamm von &lt;binding&gt; und legen das placement-Attribut auf „background“ fest.</span><span class="sxs-lookup"><span data-stu-id="c615a-305">To set a background image, place an image element in the root of the &lt;binding&gt; and set the placement attribute to "background."</span></span>

```XML
<binding template="TileWide">
  <image src="Assets\Mostly Cloudy-Background.jpg" placement="background"/>
  <group>
    <subgroup hint-weight="1">
      <text hint-align="center">Mon</text>
      <image src="Assets\Weather\Mostly Cloudy.png" hint-removeMargin="true"/>
      <text hint-align="center">63°</text>
      <text hint-align="center" hint-style="captionsubtle">42°</text>
    </subgroup>
    ...
  </group>
</binding>
```

```CSharp
TileWide = new TileBinding()
{
    Content = new TileBindingContentAdaptive()
    {
        BackgroundImage = new TileBackgroundImage()
        {
            Source = "Assets/Mostly Cloudy-Background.jpg"
        },

        Children =
        {
            new AdaptiveGroup()
            {
                Children =
                {
                    CreateSubgroup("Mon", "Mostly Cloudy.png", "63°", "42°")
                    ...
                }
            }
        }
    }
}

...

private static AdaptiveSubgroup CreateSubgroup(string day, string image, string highTemp, string lowTemp)
{
    return new AdaptiveSubgroup()
    {
        HintWeight = 1,
        Children =
        {
            new AdaptiveText()
            {
                Text = day,
                HintAlign = AdaptiveTextAlign.Center
            },
            new AdaptiveImage()
            {
                Source = "Assets/Weather/" + image,
                HintRemoveMargin = true
            },
            new AdaptiveText()
            {
                Text = highTemp,
                HintAlign = AdaptiveTextAlign.Center
            },
            new AdaptiveText()
            {
                Text = lowTemp,
                HintAlign = AdaptiveTextAlign.Center,
                HintStyle = AdaptiveTextStyle.CaptionSubtle
            }
        }
    };
}
```

**<span data-ttu-id="c615a-306">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="c615a-306">Result:</span></span>**

![Beispiel für ein Hintergrundbild](images/adaptive-tiles-backgroundimage.png)

### <a name="peek-image"></a><span data-ttu-id="c615a-308">Vorschaubild</span><span class="sxs-lookup"><span data-stu-id="c615a-308">Peek image</span></span>

<span data-ttu-id="c615a-309">Sie können ein Bild angeben, das von oben in die Kachel hineingleitet.</span><span class="sxs-lookup"><span data-stu-id="c615a-309">You can specify an image that "peeks" in from the top of the tile.</span></span> <span data-ttu-id="c615a-310">Das Vorschaubild gleitet mithilfe einer Animation von oben in die Kachel hinein, ist kurz auf der Kachel zu sehen und gleitet danach wieder nach oben heraus, um den Blick auf den Hauptinhalt der Kachel freizugeben.</span><span class="sxs-lookup"><span data-stu-id="c615a-310">The peek image uses an animation to slide down/up from the top of the tile, peeking into view, and then later sliding back out to reveal the main content on the tile.</span></span> <span data-ttu-id="c615a-311">Um ein Vorschaubild festzulegen, platzieren Sie ein image-Element im Stamm von &lt;binding&gt; und legen das placement-Attribut auf „peek“ fest.</span><span class="sxs-lookup"><span data-stu-id="c615a-311">To set a peek image, place an image element in the root of the &lt;binding&gt;, and set the placement attribute to "peek."</span></span>

```XML
<binding template="TileMedium" branding="name">
  <image placement="peek" src="Assets/Apps/Hipstame/hipster.jpg"/>
  <text>New Message</text>
  <text hint-style="captionsubtle" hint-wrap="true">Hey, have you tried Windows 10 yet?</text>
</binding>
```

```CSharp
TileWide = new TileBinding()
{
    Branding = TileBranding.Name,
    Content = new TileBindingContentAdaptive()
    {
        PeekImage = new TilePeekImage()
        {
            Source = "Assets/Apps/Hipstame/hipster.jpg"
        },
        Children =
        {
            new AdaptiveText()
            {
                Text = "New Message"
            },
            new AdaptiveText()
            {
                Text = "Hey, have you tried Windows 10 yet?",
                HintStyle = AdaptiveTextStyle.CaptionSubtle,
                HintWrap = true
            }
        }
    }
}
```

![Beispiele für Vorschaubilder](images/adaptive-tiles-imagepeeking.png)

**<span data-ttu-id="c615a-313">Kreisförmiges Zuschneiden für Vorschau- und Hintergrundbilder</span><span class="sxs-lookup"><span data-stu-id="c615a-313">Circle crop for peek and background images</span></span>**

<span data-ttu-id="c615a-314">Wenden Sie das hint-crop-Attribut auf Vorschau- und Hintergrundbilder an, um einen kreisförmigen Zuschnitt zu erhalten:</span><span class="sxs-lookup"><span data-stu-id="c615a-314">Use the hint-crop attribute on peek and background images to do a circle crop:</span></span>

```XML
<image placement="peek" hint-crop="circle" src="Assets/Apps/Hipstame/hipster.jpg"/>
```

```CSharp
new TilePeekImage()
{
    HintCrop = TilePeekImageCrop.Circle,
    Source = "Assets/Apps/Hipstame/hipster.jpg"
}
```

<span data-ttu-id="c615a-315">Das Ergebnis sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="c615a-315">The result will look like this:</span></span>

![Kreisförmiges Zuschneiden für Vorschau- und Hintergrundbilder](images/circlecrop-image.png)

**<span data-ttu-id="c615a-317">Verwenden eines Vorschau- und eines Hintergrundbilds</span><span class="sxs-lookup"><span data-stu-id="c615a-317">Use both peek and background image</span></span>**

<span data-ttu-id="c615a-318">Zur Verwendung eines Vorschau- und eines Hintergrundbilds auf einer Kachelbenachrichtigung geben Sie in der Benachrichtigungsnutzlast sowohl ein Vorschau- als auch ein Hintergrundbild an.</span><span class="sxs-lookup"><span data-stu-id="c615a-318">To use both a peek and a background image on a tile notification, specify both a peek image and a background image in your notification payload.</span></span>

<span data-ttu-id="c615a-319">Das Ergebnis sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="c615a-319">The result will look like this:</span></span>

![Gleichzeitiges Verwenden von Vorschau- und Hintergrundbild](images/peekandbackground.png)


### <a name="peek-and-background-image-overlays"></a><span data-ttu-id="c615a-321">Overlays von Vorschau- und Hintergrundbild</span><span class="sxs-lookup"><span data-stu-id="c615a-321">Peek and background image overlays</span></span>

<span data-ttu-id="c615a-322">Sie können mit **hint-overlay** eine schwarze Überlagerung für Hintergrund- und Vorschaubild festlegen. Das Attribut akzeptiert ganze Zahlen von 0 bis 100, wobei 0 keine Überlagerung und 100 eine vollständige schwarze Überlagerung angibt.</span><span class="sxs-lookup"><span data-stu-id="c615a-322">You can set a black overlay on your background and peek images using **hint-overlay**, which accepts integers from 0-100, with 0 being no overlay and 100 being full black overlay.</span></span> <span data-ttu-id="c615a-323">Sie können das Overlay verwenden, um sicherzustellen, dass der Text auf der Kachel lesbar ist.</span><span class="sxs-lookup"><span data-stu-id="c615a-323">You can use the overlay to help ensure that text on your tile is readable.</span></span>

**<span data-ttu-id="c615a-324">Verwenden von „hint-overlay“ für ein Hintergrundbild</span><span class="sxs-lookup"><span data-stu-id="c615a-324">Use hint-overlay on a background image</span></span>**

<span data-ttu-id="c615a-325">Das Hintergrundbild wird standardmäßig auf eine Überlagerung von 20% festgelegt, solange es in der Nutzlast Textelemente gibt. (Andernfalls wird standardmäßig eine Überlagerung von 0% festgelegt.)</span><span class="sxs-lookup"><span data-stu-id="c615a-325">Your background image will default to 20% overlay as long as you have some text elements in your payload (otherwise it will default to 0% overlay).</span></span>

```XML
<binding template="TileWide">
  <image placement="background" hint-overlay="60" src="Assets\Mostly Cloudy-Background.jpg"/>
  ...
</binding>
```

```CSharp
TileWide = new TileBinding()
{
    Content = new TileBindingContentAdaptive()
    {
        BackgroundImage = new TileBackgroundImage()
        {
            Source = "Assets/Mostly Cloudy-Background.jpg",
            HintOverlay = 60
        },

        ...
    }
}
```

**<span data-ttu-id="c615a-326">Ergebnis von „hint-overlay“:</span><span class="sxs-lookup"><span data-stu-id="c615a-326">hint-overlay Result:</span></span>**

![Beispiel für ein Bild mit angewendetem „hint-overlay“](images/adaptive-tiles-image-hintoverlay.png)

**<span data-ttu-id="c615a-328">Verwenden von „hint-overlay“ für ein Vorschaubild</span><span class="sxs-lookup"><span data-stu-id="c615a-328">Use hint-overlay on a peek image</span></span>**

<span data-ttu-id="c615a-329">In Version 1511 von Windows10 unterstützen wir Überlagerungen für Vorschaubilder, genau wie für Hintergrundbilder.</span><span class="sxs-lookup"><span data-stu-id="c615a-329">In Version 1511 of Windows 10, we support an overlay for your peek image too, just like your background image.</span></span> <span data-ttu-id="c615a-330">Geben Sie „hint-overlay“ für das Vorschaubildelement als ganze Zahl von 0 bis 100 an.</span><span class="sxs-lookup"><span data-stu-id="c615a-330">Specify hint-overlay on the peek image element as an integer from 0-100.</span></span> <span data-ttu-id="c615a-331">Die Standardüberlagerung für Vorschaubilder ist 0 (keine Überlagerung).</span><span class="sxs-lookup"><span data-stu-id="c615a-331">The default overlay for peek images is 0 (no overlay).</span></span>

```XML
<binding template="TileMedium">
  <image hint-overlay="20" src="Assets\Map.jpg" placement="peek"/>
  ...
</binding>
```

```CSharp
TileMedium = new TileBinding()
{
    Content = new TileBindingContentAdaptive()
    {
        PeekImage = new TilePeekImage()
        {
            Source = "Assets/Map.jpg",
            HintOverlay = 20
        },
        ...
    }
}
```

<span data-ttu-id="c615a-332">Dieses Beispiel zeigt ein Vorschaubild mit 20% Deckkraft (links) und 0% Deckkraft (rechts):</span><span class="sxs-lookup"><span data-stu-id="c615a-332">This example shows a peek image at 20% opacity (left) and at 0% opacity (right):</span></span>

![„hint-overlay“ für ein Vorschaubild](images/hintoverlay.png)

## <a name="vertical-alignment-text-stacking"></a><span data-ttu-id="c615a-334">Vertikale Ausrichtung (hint-textStacking)</span><span class="sxs-lookup"><span data-stu-id="c615a-334">Vertical alignment (text stacking)</span></span>


<span data-ttu-id="c615a-335">Sie können die vertikale Ausrichtung der Inhalte auf einer Kachel steuern, indem Sie das **hint-textStacking**-Attribut sowohl für das [&lt;binding&gt;](tiles-and-notifications-adaptive-tiles-schema.md)-Element als auch das [&lt;subgroup&gt;](tiles-and-notifications-adaptive-tiles-schema.md)-Element verwenden.</span><span class="sxs-lookup"><span data-stu-id="c615a-335">You can control the vertical alignment of content on your tile by using the **hint-textStacking** attribute on both the [&lt;binding&gt;](tiles-and-notifications-adaptive-tiles-schema.md) element and [&lt;subgroup&gt;](tiles-and-notifications-adaptive-tiles-schema.md) element.</span></span> <span data-ttu-id="c615a-336">Der gesamte Inhalt wird standardmäßig vertikal am oberen Rand ausgerichtet, kann aber auch in der Mitte oder am unteren Rand ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="c615a-336">By default, everything is vertically aligned to the top, but you can also align content to the bottom or center.</span></span>

### <a name="text-stacking-on-binding-element"></a><span data-ttu-id="c615a-337">Gestapelter Text für binding-Element</span><span class="sxs-lookup"><span data-stu-id="c615a-337">Text stacking on binding element</span></span>

<span data-ttu-id="c615a-338">Bei Anwendung auf die [&lt;binding&gt;](tiles-and-notifications-adaptive-tiles-schema.md)-Ebene wird durch Textstapelung die vertikale Ausrichtung des Benachrichtigungsinhalts als Ganzes festgelegt und im verfügbaren vertikalen Bereich über dem Branding-/Signalbereich ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="c615a-338">When applied at the [&lt;binding&gt;](tiles-and-notifications-adaptive-tiles-schema.md) level, text stacking sets the vertical alignment of the notification content as a whole, aligning in the available vertical space above the branding/badge area.</span></span>

```XML
<binding template="TileMedium" hint-textStacking="center" branding="logo">
  <text hint-style="base" hint-align="center">Hi,</text>
  <text hint-style="captionSubtle" hint-align="center">MasterHip</text>
</binding>
```

```CSharp
TileMedium = new TileBinding()
{
    Branding = TileBranding.Logo,
    Content = new TileBindingContentAdaptive()
    {
        TextStacking = TileTextStacking.Center,
        Children =
        {
            new AdaptiveText()
            {
                Text = "Hi,",
                HintStyle = AdaptiveTextStyle.Base,
                HintAlign = AdaptiveTextAlign.Center
            },

            new AdaptiveText()
            {
                Text = "MasterHip",
                HintStyle = AdaptiveTextStyle.CaptionSubtle,
                HintAlign = AdaptiveTextAlign.Center
            }
        }
    }
}
```

![Gestapelter Text für binding-Element](images/adaptive-tiles-textstack-bindingelement.png)

### <a name="text-stacking-on-subgroup-element"></a><span data-ttu-id="c615a-340">Gestapelter Text für subgroup-Element</span><span class="sxs-lookup"><span data-stu-id="c615a-340">Text stacking on subgroup element</span></span>

<span data-ttu-id="c615a-341">Bei Anwendung auf die [&lt;subgroup&gt;](tiles-and-notifications-adaptive-tiles-schema.md)-Ebene wird die vertikale Ausrichtung des Inhalts der Untergruppe (Spalte) durch gestapelten Text festgelegt und im verfügbaren vertikalen Bereich innerhalb der gesamten Gruppe ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="c615a-341">When applied at the [&lt;subgroup&gt;](tiles-and-notifications-adaptive-tiles-schema.md) level, text stacking sets the vertical alignment of the subgroup (column) content, aligning in the available vertical space within the entire group.</span></span>

```XML
<binding template="TileWide" branding="nameAndLogo">
  <group>
    <subgroup hint-weight="33">
      <image src="Assets/Apps/Hipstame/hipster.jpg" hint-crop="circle"/>
    </subgroup>
    <subgroup hint-textStacking="center">
      <text hint-style="subtitle">Hi,</text>
      <text hint-style="bodySubtle">MasterHip</text>
    </subgroup>
  </group>
</binding>
```

```CSharp
TileWide = new TileBinding()
{
    Branding = TileBranding.NameAndLogo,
    Content = new TileBindingContentAdaptive()
    {
        Children =
        {
            new AdaptiveGroup()
            {
                Children =
                {
                    // Image column
                    new AdaptiveSubgroup()
                    {
                        HintWeight = 33,
                        Children =
                        {
                            new AdaptiveImage()
                            {
                                Source = "Assets/Apps/Hipstame/hipster.jpg",
                                HintCrop = AdaptiveImageCrop.Circle
                            }
                        }
                    },

                    // Text column
                    new AdaptiveSubgroup()
                    {
                        // Vertical align its contents
                        TextStacking = TileTextStacking.Center,
                        Children =
                        {
                            new AdaptiveText()
                            {
                                Text = "Hi,",
                                HintStyle = AdaptiveTextStyle.Subtitle
                            },

                            new AdaptiveText()
                            {
                                Text = "MasterHip",
                                HintStyle = AdaptiveTextStyle.BodySubtle
                            }
                        }
                    }
                }
            }
        }
    }
}
```

## <a name="related-topics"></a><span data-ttu-id="c615a-342">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="c615a-342">Related topics</span></span>


* [<span data-ttu-id="c615a-343">Adaptives Kachelschema</span><span class="sxs-lookup"><span data-stu-id="c615a-343">Adaptive tiles schema</span></span>](tiles-and-notifications-adaptive-tiles-schema.md)
* [<span data-ttu-id="c615a-344">Schnellstart: Senden einer lokalen Kachelbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="c615a-344">Quickstart: Send a local tile notification</span></span>](tiles-and-notifications-sending-a-local-tile-notification.md)
* [<span data-ttu-id="c615a-345">Benachrichtigungsbibliothek auf GitHub</span><span class="sxs-lookup"><span data-stu-id="c615a-345">Notifications library on GitHub</span></span>](https://github.com/Microsoft/UWPCommunityToolkit/tree/dev/Notifications)
* [<span data-ttu-id="c615a-346">Katalog für spezielle Kachelvorlagen</span><span class="sxs-lookup"><span data-stu-id="c615a-346">Special tile templates catalog</span></span>](tiles-and-notifications-special-tile-templates-catalog.md)
 

 




