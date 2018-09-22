---
author: andrewleader
Description: Adaptive tile templates are a new feature in Windows 10, allowing you to design your own tile notification content using a simple and flexible markup language that adapts to different screen densities.
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
ms.localizationpriority: medium
ms.openlocfilehash: 761d87654ef340f4b539dbefa0950c58f627d310
ms.sourcegitcommit: a160b91a554f8352de963d9fa37f7df89f8a0e23
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/21/2018
ms.locfileid: "4122393"
---
# <a name="create-adaptive-tiles"></a><span data-ttu-id="91846-103">Erstellen adaptiver Kacheln</span><span class="sxs-lookup"><span data-stu-id="91846-103">Create adaptive tiles</span></span>

<span data-ttu-id="91846-104">Vorlagen für adaptive Kacheln sind ein neues Feature in Windows 10 und ermöglichen den Entwurf eigener Inhalte für Kachelbenachrichtigungen mithilfe einer einfachen, flexiblen Markupsprache, die sich an unterschiedliche Bildschirmdichten anpasst.</span><span class="sxs-lookup"><span data-stu-id="91846-104">Adaptive tile templates are a new feature in Windows 10, allowing you to design your own tile notification content using a simple and flexible markup language that adapts to different screen densities.</span></span> <span data-ttu-id="91846-105">Dieser Artikel beschreibt, wie Sie adaptive Live-Kacheln für Ihre UWP-App (Universelle Windows-Plattform) erstellen.</span><span class="sxs-lookup"><span data-stu-id="91846-105">This article tells you how to create adaptive live tiles for your Universal Windows Platform (UWP) app.</span></span> <span data-ttu-id="91846-106">Die vollständige Liste adaptiver Elemente und Attribute finden Sie unter [Adaptives Kachelschema](../tiles-and-notifications/tile-schema.md).</span><span class="sxs-lookup"><span data-stu-id="91846-106">For the complete list of adaptive elements and attributes, see the [Adaptive tiles schema](../tiles-and-notifications/tile-schema.md).</span></span>

<span data-ttu-id="91846-107">(Wenn gewünscht, können Sie weiterhin die voreingestellten Vorlagen aus dem [Windows8-Kachelvorlagenkatalog](https://msdn.microsoft.com/library/windows/apps/hh761491) beim Entwerfen von Benachrichtigungen für Windows10 verwenden.)</span><span class="sxs-lookup"><span data-stu-id="91846-107">(If you'd like, you can still use the preset templates from the [Windows 8 tile template catalog](https://msdn.microsoft.com/library/windows/apps/hh761491) when designing notifications for Windows 10.)</span></span>


## <a name="getting-started"></a><span data-ttu-id="91846-108">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="91846-108">Getting started</span></span>

**<span data-ttu-id="91846-109">Installieren Sie die Benachrichtigungsbibliothek.</span><span class="sxs-lookup"><span data-stu-id="91846-109">Install Notifications library.</span></span>** <span data-ttu-id="91846-110">Wenn Sie C# anstelle von XML verwenden möchten, um Benachrichtigungen zu generieren, installieren Sie das NuGet-Paket mit dem Namen [Microsoft.Toolkit.Uwp.Notifications](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/). (Suchen Sie nach „Benachrichtigungen UWP“.)</span><span class="sxs-lookup"><span data-stu-id="91846-110">If you'd like to use C# instead of XML to generate notifications, install the NuGet package named [Microsoft.Toolkit.Uwp.Notifications](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) (search for "notifications uwp").</span></span> <span data-ttu-id="91846-111">Die in diesem Artikel bereitgestellten C#-Beispiele verwenden Version 1.0.0 des NuGet-Pakets.</span><span class="sxs-lookup"><span data-stu-id="91846-111">The C# samples provided in this article use version 1.0.0 of the NuGet package.</span></span>

**<span data-ttu-id="91846-112">Installieren Sie den Notifications Visualizer.</span><span class="sxs-lookup"><span data-stu-id="91846-112">Install Notifications Visualizer.</span></span>** <span data-ttu-id="91846-113">Diese kostenlose UWP-App erleichtert das Entwerfen adaptiver Live-Kacheln, indem Ihre Kachel während der Bearbeitung in einer sofortigen visuellen Vorschau dargestellt wird, die mit dem XAML-Editor bzw. der Entwurfsansicht in Visual Studio vergleichbar ist.</span><span class="sxs-lookup"><span data-stu-id="91846-113">This free UWP app helps you design adaptive live tiles by providing an instant visual preview of your tile as you edit it, similar to Visual Studio's XAML editor/design view.</span></span> <span data-ttu-id="91846-114">Weitere Informationen finden Sie unter [Notifications Visualizer](notifications-visualizer.md) oder [Notifications Visualizer aus dem Store herunterladen](https://www.microsoft.com/store/apps/notifications-visualizer/9nblggh5xsl1).</span><span class="sxs-lookup"><span data-stu-id="91846-114">See [Notifications Visualizer](notifications-visualizer.md) for more information, or [download Notifications Visualizer from the Store](https://www.microsoft.com/store/apps/notifications-visualizer/9nblggh5xsl1).</span></span>


## <a name="how-to-send-a-tile-notification"></a><span data-ttu-id="91846-115">Senden einer Kachelbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="91846-115">How to send a tile notification</span></span>

<span data-ttu-id="91846-116">Lesen Sie den [Schnellstart zum Senden von lokalen Kachelbenachrichtigungen](sending-a-local-tile-notification.md).</span><span class="sxs-lookup"><span data-stu-id="91846-116">Please read our [Quickstart on sending local tile notifications](sending-a-local-tile-notification.md).</span></span> <span data-ttu-id="91846-117">Die Dokumentation unten beschreibt alle visuellen UI-Möglichkeiten, die Ihnen mit anpassbaren Kacheln zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="91846-117">The documentation below explains all the visual UI possibilities you have with adaptive tiles.</span></span>


## <a name="usage-guidance"></a><span data-ttu-id="91846-118">Informationen zur Verwendung</span><span class="sxs-lookup"><span data-stu-id="91846-118">Usage guidance</span></span>


<span data-ttu-id="91846-119">Adaptive Vorlagen werden für die Unterstützung verschiedener Formfaktoren und Benachrichtigungstypen konzipiert.</span><span class="sxs-lookup"><span data-stu-id="91846-119">Adaptive templates are designed to work across different form factors and notification types.</span></span> <span data-ttu-id="91846-120">Elemente wie Gruppen und Untergruppen verknüpfen Inhalte miteinander und implizieren selbst kein bestimmtes visuelles Verhalten.</span><span class="sxs-lookup"><span data-stu-id="91846-120">Elements such as group and subgroup link together content and don't imply a particular visual behavior on their own.</span></span> <span data-ttu-id="91846-121">Die endgültige Darstellung einer Benachrichtigung sollte auf dem spezifischen Gerät basieren, auf dem sie angezeigt wird, beispielsweise einem Smartphone, Tablet, Desktop oder anderen Gerät.</span><span class="sxs-lookup"><span data-stu-id="91846-121">The final appearance of a notification should be based on the specific device on which it will appear, whether it's phone, tablet, or desktop, or another device.</span></span>

<span data-ttu-id="91846-122">Hinweise sind optionale Attribute, die Elementen hinzugefügt werden können, um ein bestimmtes visuelles Verhalten zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="91846-122">Hints are optional attributes that can be added to elements in order to achieve a specific visual behavior.</span></span> <span data-ttu-id="91846-123">Hinweise können spezifisch für Geräte oder Benachrichtigungen sein.</span><span class="sxs-lookup"><span data-stu-id="91846-123">Hints can be device-specific or notification-specific.</span></span>

## <a name="a-basic-example"></a><span data-ttu-id="91846-124">Ein einfaches Beispiel</span><span class="sxs-lookup"><span data-stu-id="91846-124">A basic example</span></span>


<span data-ttu-id="91846-125">Dieses Beispiel veranschaulicht, was Vorlagen für adaptive Kacheln leisten können.</span><span class="sxs-lookup"><span data-stu-id="91846-125">This example demonstrates what the adaptive tile templates can produce.</span></span>

```xml
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

```csharp
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

**<span data-ttu-id="91846-126">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="91846-126">Result:</span></span>**

![Kurzes Beispiel für eine Kachel](images/adaptive-tiles-quicksample.png)

## <a name="tile-sizes"></a><span data-ttu-id="91846-128">Kachelgrößen</span><span class="sxs-lookup"><span data-stu-id="91846-128">Tile sizes</span></span>


<span data-ttu-id="91846-129">Der Inhalt für jede Kachelgröße wird einzeln in getrennten [TileBinding](../tiles-and-notifications/tile-schema.md#tilebinding)-Elementen innerhalb der XML-Nutzlast angegeben.</span><span class="sxs-lookup"><span data-stu-id="91846-129">Content for each tile size is individually specified in separate [TileBinding](../tiles-and-notifications/tile-schema.md#tilebinding) elements within the XML payload.</span></span> <span data-ttu-id="91846-130">Wählen Sie die Zielgröße aus, indem Sie das template-Attribut auf einen der folgenden Werte festlegen:</span><span class="sxs-lookup"><span data-stu-id="91846-130">Choose the target size by setting the template attribute to one of the following values:</span></span>

-   <span data-ttu-id="91846-131">TileSmall</span><span class="sxs-lookup"><span data-stu-id="91846-131">TileSmall</span></span>
-   <span data-ttu-id="91846-132">TileMedium</span><span class="sxs-lookup"><span data-stu-id="91846-132">TileMedium</span></span>
-   <span data-ttu-id="91846-133">TileWide</span><span class="sxs-lookup"><span data-stu-id="91846-133">TileWide</span></span>
-   <span data-ttu-id="91846-134">TileLarge (nur für Desktop)</span><span class="sxs-lookup"><span data-stu-id="91846-134">TileLarge (only for desktop)</span></span>

<span data-ttu-id="91846-135">Geben Sie für die XML-Nutzlast einer einzelnen Kachelbenachrichtigung &lt;binding&gt;-Elemente für jede zu unterstützende Kachelgröße an, wie im folgenden Beispiel dargestellt:</span><span class="sxs-lookup"><span data-stu-id="91846-135">For a single tile notification XML payload, provide &lt;binding&gt; elements for each tile size that you'd like to support, as shown in this example:</span></span>

```xml
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

```csharp
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

**<span data-ttu-id="91846-136">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="91846-136">Result:</span></span>**

![Größen für adaptive Kacheln: klein, mittel, breit und groß](images/adaptive-tiles-sizes.png)

## <a name="branding"></a><span data-ttu-id="91846-138">Branding</span><span class="sxs-lookup"><span data-stu-id="91846-138">Branding</span></span>


<span data-ttu-id="91846-139">Sie können das Branding am unteren Rand einer Live-Kachel (den Anzeigenamen und das Cornerlogo) mit dem branding-Attribut in der Benachrichtigungsnutzlast steuern.</span><span class="sxs-lookup"><span data-stu-id="91846-139">You can control the branding on the bottom of a live tile (the display name and corner logo) by using the branding attribute on the notification payload.</span></span> <span data-ttu-id="91846-140">Mit „none“ wird nichts angezeigt, mit „name“ nur der Name, mit „logo“ nur das Logo, und mit „nameAndLogo“ werden Name und Logo angezeigt.</span><span class="sxs-lookup"><span data-stu-id="91846-140">You can choose to display "none," only the "name," only the "logo," or both with "nameAndLogo."</span></span>

<span data-ttu-id="91846-141">**Hinweis**  Da Windows Mobile kein Cornerlogo unterstützt, wird unter Mobile anstelle von „logo“ und „nameAndLogo“ standardmäßig „name” verwendet.</span><span class="sxs-lookup"><span data-stu-id="91846-141">**Note**  Windows Mobile doesn't support the corner logo, so "logo" and "nameAndLogo" default to "name" on Mobile.</span></span>

 

```xml
<visual branding="logo">
  ...
</visual>
```

```csharp
new TileVisual()
{
    Branding = TileBranding.Logo,
    ...
}
```

**<span data-ttu-id="91846-142">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="91846-142">Result:</span></span>**

![Adaptive Kacheln, Name und Logo](images/adaptive-tiles-namelogo.png)

<span data-ttu-id="91846-144">Das Branding kann für bestimmte Kachelgrößen auf zwei Weisen angewendet werden:</span><span class="sxs-lookup"><span data-stu-id="91846-144">Branding can be applied for specific tile sizes one of two ways:</span></span>

1. <span data-ttu-id="91846-145">Indem das Attribut auf das [TileBinding](../tiles-and-notifications/tile-schema.md#tilebinding)-Element angewendet wird</span><span class="sxs-lookup"><span data-stu-id="91846-145">By applying the attribute on the [TileBinding](../tiles-and-notifications/tile-schema.md#tilebinding) element</span></span>
2. <span data-ttu-id="91846-146">Durch Anwenden des Attributs auf das [TileVisual](../tiles-and-notifications/tile-schema.md#tilevisual)-Element, was sich auf die gesamte Benachrichtigungsnutzlast auswirkt. Wenn Sie für eine Bindung kein Branding angeben, wird das Branding verwendet, das auf dem visual-Element bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="91846-146">By applying the attribute on the [TileVisual](../tiles-and-notifications/tile-schema.md#tilevisual) element, which affects the entire notification payload If you don't specify branding for a binding, it will use the branding that's provided on the visual element.</span></span>

```xml
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

```csharp
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

**<span data-ttu-id="91846-147">Ergebnis bei Standardbranding:</span><span class="sxs-lookup"><span data-stu-id="91846-147">Default branding result:</span></span>**

![Standardbranding für Kacheln](images/adaptive-tiles-defaultbranding.png)

<span data-ttu-id="91846-149">Wenn Sie in der Benachrichtigungsnutzlast kein Branding angeben, wird das Branding durch die Eigenschaften der Basiskachel bestimmt.</span><span class="sxs-lookup"><span data-stu-id="91846-149">If you don't specify the branding in your notification payload, the base tile's properties will determine the branding.</span></span> <span data-ttu-id="91846-150">Wenn auf der Basiskachel der Anzeigename dargestellt ist, wird für das Branding standardmäßig „name“ verwendet.</span><span class="sxs-lookup"><span data-stu-id="91846-150">If the base tile shows the display name, then the branding will default to "name."</span></span> <span data-ttu-id="91846-151">Wenn kein Anzeigename vorhanden ist, wird für das Branding standardmäßig „none“ verwendet.</span><span class="sxs-lookup"><span data-stu-id="91846-151">Otherwise, the branding will default to "none" if the display name isn't shown.</span></span>

<span data-ttu-id="91846-152">**Hinweis**  Dies ist eine Änderung gegenüber Windows 8.x, wo das Standardbranding „logo“ lautete.</span><span class="sxs-lookup"><span data-stu-id="91846-152">**Note**   This is a change from Windows 8.x, in which the default branding was "logo."</span></span>

 

## <a name="display-name"></a><span data-ttu-id="91846-153">Anzeigename</span><span class="sxs-lookup"><span data-stu-id="91846-153">Display name</span></span>


<span data-ttu-id="91846-154">Sie können den Anzeigenamen einer Benachrichtigung überschreiben, indem Sie für das **displayName**-Attribut die gewünschte Textzeichenfolge eingeben.</span><span class="sxs-lookup"><span data-stu-id="91846-154">You can override the display name of a notification by entering the text string of your choice with the **displayName** attribute.</span></span> <span data-ttu-id="91846-155">Wie beim Branding können Sie dies für das [TileVisual](../tiles-and-notifications/tile-schema.md#tilevisual)-Element angeben, was sich auf die gesamte Benachrichtigungsnutzlast auswirkt, oder für das [TileBinding](../tiles-and-notifications/tile-schema.md#tilebinding)-Element, was nur einzelne Kacheln betrifft.</span><span class="sxs-lookup"><span data-stu-id="91846-155">As with branding, you can specify this on the [TileVisual](../tiles-and-notifications/tile-schema.md#tilevisual) element, which affects the entire notification payload, or on the [TileBinding](../tiles-and-notifications/tile-schema.md#tilebinding) element, which only affects individual tiles.</span></span>

<span data-ttu-id="91846-156">**Bekanntes Problem**  Wenn Sie unter Windows Mobile „ShortName“ für die Kachel angeben, wird der in der Benachrichtigung angegebene Anzeigename nicht verwendet (stattdessen wird immer „ShortName“ angezeigt).</span><span class="sxs-lookup"><span data-stu-id="91846-156">**Known Issue**  On Windows Mobile, if you specify a ShortName for your Tile, the display name provided in your notification will not be used (the ShortName will always be displayed).</span></span> 

```xml
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

```csharp
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

**<span data-ttu-id="91846-157">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="91846-157">Result:</span></span>**

![Anzeigename adaptiver Kacheln](images/adaptive-tiles-displayname.png)

## <a name="text"></a><span data-ttu-id="91846-159">Text</span><span class="sxs-lookup"><span data-stu-id="91846-159">Text</span></span>


<span data-ttu-id="91846-160">Das [AdaptiveText](../tiles-and-notifications/tile-schema.md#adaptivetext)-Element wird zum Anzeigen von Text verwendet.</span><span class="sxs-lookup"><span data-stu-id="91846-160">The [AdaptiveText](../tiles-and-notifications/tile-schema.md#adaptivetext) element is used to display text.</span></span> <span data-ttu-id="91846-161">Mithilfe von Hinweisen können Sie die Darstellung von Text anpassen.</span><span class="sxs-lookup"><span data-stu-id="91846-161">You can use hints to modify how text appears.</span></span>

```xml
<text>This is a line of text</text>
```


```csharp
new AdaptiveText()
{
    Text = "This is a line of text"
};
```

**<span data-ttu-id="91846-162">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="91846-162">Result:</span></span>**

![Text adaptiver Kacheln](images/adaptive-tiles-text.png)

## <a name="text-wrapping"></a><span data-ttu-id="91846-164">Textumbruch</span><span class="sxs-lookup"><span data-stu-id="91846-164">Text wrapping</span></span>


<span data-ttu-id="91846-165">Text wird standardmäßig nicht umbrochen und verläuft über den Kachelrand hinaus.</span><span class="sxs-lookup"><span data-stu-id="91846-165">By default, text doesn't wrap and will continue off the edge of the tile.</span></span> <span data-ttu-id="91846-166">Verwenden Sie das **hint-wrap**-Attribut, um den Textumbruch für ein text-Element festzulegen.</span><span class="sxs-lookup"><span data-stu-id="91846-166">Use the **hint-wrap** attribute to set text wrapping on a text element.</span></span> <span data-ttu-id="91846-167">Mit **hint-minLines** und **hint-maxLines**, die beide positive ganze Zahlen akzeptieren, können Sie auch die minimale und maximale Zeilenanzahl steuern.</span><span class="sxs-lookup"><span data-stu-id="91846-167">You can also control the minimum and maximum number of lines by using **hint-minLines** and **hint-maxLines**, both of which accept positive integers.</span></span>

```xml
<text hint-wrap="true">This is a line of wrapping text</text>
```


```csharp
new AdaptiveText()
{
    Text = "This is a line of wrapping text",
    HintWrap = true
};
```

**<span data-ttu-id="91846-168">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="91846-168">Result:</span></span>**

![Adaptive Kachel mit Textumbruch](images/adaptive-tiles-textwrapping.png)

## <a name="text-styles"></a><span data-ttu-id="91846-170">Textstile</span><span class="sxs-lookup"><span data-stu-id="91846-170">Text styles</span></span>


<span data-ttu-id="91846-171">Stile steuern den Schriftgrad, die Schriftfarbe und Schriftbreite von text-Elementen.</span><span class="sxs-lookup"><span data-stu-id="91846-171">Styles control the font size, color, and weight of text elements.</span></span> <span data-ttu-id="91846-172">Es sind mehrere Stile verfügbar. Zusätzlich gibt es leichte („subtle“) Variationen jedes Stils, durch die die Deckkraft auf 60% festgelegt und die Textfarbe normalerweise in einem hellgrauen Farbton angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="91846-172">There are a number of available styles, including a "subtle" variation of each style that sets the opacity to 60%, which usually makes the text color a shade of light gray.</span></span>

```xml
<text hint-style="base">Header content</text>
<text hint-style="captionSubtle">Subheader content</text>
```

```csharp
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

**<span data-ttu-id="91846-173">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="91846-173">Result:</span></span>**

![Textstile adaptiver Kacheln](images/adaptive-tiles-textstyles.png)

<span data-ttu-id="91846-175">**Hinweis**  Wenn „hint-style“ nicht angegeben ist, wird für den Stil standardmäßig „caption“ verwendet.</span><span class="sxs-lookup"><span data-stu-id="91846-175">**Note**  The style defaults to caption if hint-style isn't specified.</span></span>

 

**<span data-ttu-id="91846-176">Allgemeine Textstile</span><span class="sxs-lookup"><span data-stu-id="91846-176">Basic text styles</span></span>**

|                                |                           |             |
|--------------------------------|---------------------------|-------------|
| <span data-ttu-id="91846-177">&lt;text hint-style="\*" /&gt;</span><span class="sxs-lookup"><span data-stu-id="91846-177">&lt;text hint-style="\*" /&gt;</span></span> | <span data-ttu-id="91846-178">Zeichenhöhe</span><span class="sxs-lookup"><span data-stu-id="91846-178">Font height</span></span>               | <span data-ttu-id="91846-179">Schriftbreite</span><span class="sxs-lookup"><span data-stu-id="91846-179">Font weight</span></span> |
| <span data-ttu-id="91846-180">caption</span><span class="sxs-lookup"><span data-stu-id="91846-180">caption</span></span>                        | <span data-ttu-id="91846-181">12 effektive Pixel (epx)</span><span class="sxs-lookup"><span data-stu-id="91846-181">12 effective pixels (epx)</span></span> | <span data-ttu-id="91846-182">Regular</span><span class="sxs-lookup"><span data-stu-id="91846-182">Regular</span></span>     |
| <span data-ttu-id="91846-183">body</span><span class="sxs-lookup"><span data-stu-id="91846-183">body</span></span>                           | <span data-ttu-id="91846-184">15Epx</span><span class="sxs-lookup"><span data-stu-id="91846-184">15 epx</span></span>                    | <span data-ttu-id="91846-185">Regular</span><span class="sxs-lookup"><span data-stu-id="91846-185">Regular</span></span>     |
| <span data-ttu-id="91846-186">base</span><span class="sxs-lookup"><span data-stu-id="91846-186">base</span></span>                           | <span data-ttu-id="91846-187">15Epx</span><span class="sxs-lookup"><span data-stu-id="91846-187">15 epx</span></span>                    | <span data-ttu-id="91846-188">Semibold</span><span class="sxs-lookup"><span data-stu-id="91846-188">Semibold</span></span>    |
| <span data-ttu-id="91846-189">subtitle</span><span class="sxs-lookup"><span data-stu-id="91846-189">subtitle</span></span>                       | <span data-ttu-id="91846-190">20Epx</span><span class="sxs-lookup"><span data-stu-id="91846-190">20 epx</span></span>                    | <span data-ttu-id="91846-191">Regular</span><span class="sxs-lookup"><span data-stu-id="91846-191">Regular</span></span>     |
| <span data-ttu-id="91846-192">title</span><span class="sxs-lookup"><span data-stu-id="91846-192">title</span></span>                          | <span data-ttu-id="91846-193">24Epx</span><span class="sxs-lookup"><span data-stu-id="91846-193">24 epx</span></span>                    | <span data-ttu-id="91846-194">Semilight</span><span class="sxs-lookup"><span data-stu-id="91846-194">Semilight</span></span>   |
| <span data-ttu-id="91846-195">subheader</span><span class="sxs-lookup"><span data-stu-id="91846-195">subheader</span></span>                      | <span data-ttu-id="91846-196">34Epx</span><span class="sxs-lookup"><span data-stu-id="91846-196">34 epx</span></span>                    | <span data-ttu-id="91846-197">Light</span><span class="sxs-lookup"><span data-stu-id="91846-197">Light</span></span>       |
| <span data-ttu-id="91846-198">header</span><span class="sxs-lookup"><span data-stu-id="91846-198">header</span></span>                         | <span data-ttu-id="91846-199">46Epx</span><span class="sxs-lookup"><span data-stu-id="91846-199">46 epx</span></span>                    | <span data-ttu-id="91846-200">Light</span><span class="sxs-lookup"><span data-stu-id="91846-200">Light</span></span>       |

 

**<span data-ttu-id="91846-201">Numerische Variationen des Textstils</span><span class="sxs-lookup"><span data-stu-id="91846-201">Numeral text style variations</span></span>**

<span data-ttu-id="91846-202">Durch diese Variationen wird die Zeilenhöhe verringert, sodass der Abstand zu Inhalten über und unter der Zeile deutlich kleiner wird.</span><span class="sxs-lookup"><span data-stu-id="91846-202">These variations reduce the line height so that content above and below come much closer to the text.</span></span>

|                  |
|------------------|
| <span data-ttu-id="91846-203">titleNumeral</span><span class="sxs-lookup"><span data-stu-id="91846-203">titleNumeral</span></span>     |
| <span data-ttu-id="91846-204">subheaderNumeral</span><span class="sxs-lookup"><span data-stu-id="91846-204">subheaderNumeral</span></span> |
| <span data-ttu-id="91846-205">headerNumeral</span><span class="sxs-lookup"><span data-stu-id="91846-205">headerNumeral</span></span>    |

 

**<span data-ttu-id="91846-206">Leichte Variationen des Textstils</span><span class="sxs-lookup"><span data-stu-id="91846-206">Subtle text style variations</span></span>**

<span data-ttu-id="91846-207">Jeder Stil weist eine leichte Variation auf, durch die der Text eine 60%-ige Deckkraft erhält und normalerweise in einem hellgrauen Farbton angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="91846-207">Each style has a subtle variation that gives the text a 60% opacity, which usually makes the text color a shade of light gray.</span></span>

|                        |
|------------------------|
| <span data-ttu-id="91846-208">captionSubtle</span><span class="sxs-lookup"><span data-stu-id="91846-208">captionSubtle</span></span>          |
| <span data-ttu-id="91846-209">bodySubtle</span><span class="sxs-lookup"><span data-stu-id="91846-209">bodySubtle</span></span>             |
| <span data-ttu-id="91846-210">baseSubtle</span><span class="sxs-lookup"><span data-stu-id="91846-210">baseSubtle</span></span>             |
| <span data-ttu-id="91846-211">subtitleSubtle</span><span class="sxs-lookup"><span data-stu-id="91846-211">subtitleSubtle</span></span>         |
| <span data-ttu-id="91846-212">titleSubtle</span><span class="sxs-lookup"><span data-stu-id="91846-212">titleSubtle</span></span>            |
| <span data-ttu-id="91846-213">titleNumeralSubtle</span><span class="sxs-lookup"><span data-stu-id="91846-213">titleNumeralSubtle</span></span>     |
| <span data-ttu-id="91846-214">subheaderSubtle</span><span class="sxs-lookup"><span data-stu-id="91846-214">subheaderSubtle</span></span>        |
| <span data-ttu-id="91846-215">subheaderNumeralSubtle</span><span class="sxs-lookup"><span data-stu-id="91846-215">subheaderNumeralSubtle</span></span> |
| <span data-ttu-id="91846-216">headerSubtle</span><span class="sxs-lookup"><span data-stu-id="91846-216">headerSubtle</span></span>           |
| <span data-ttu-id="91846-217">headerNumeralSubtle</span><span class="sxs-lookup"><span data-stu-id="91846-217">headerNumeralSubtle</span></span>    |

 

## <a name="text-alignment"></a><span data-ttu-id="91846-218">Textausrichtung</span><span class="sxs-lookup"><span data-stu-id="91846-218">Text alignment</span></span>


<span data-ttu-id="91846-219">Text kann horizontal, linksbündig, zentriert oder rechtsbündig ausgerichtet sein.</span><span class="sxs-lookup"><span data-stu-id="91846-219">Text can be horizontally aligned left, center, or right.</span></span> <span data-ttu-id="91846-220">Bei einer von links nach rechts gelesenen Sprache, wie Deutsch, ist Text standardmäßig linksbündig ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="91846-220">In left-to-right languages like English, text defaults to left-aligned.</span></span> <span data-ttu-id="91846-221">Bei einer von rechts nach links gelesenen Sprache, wie Arabisch, ist Text standardmäßig rechtsbündig ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="91846-221">In right-to-left languages like Arabic, text defaults to right-aligned.</span></span> <span data-ttu-id="91846-222">Mit dem **hint-align**-Attribut können Sie die Ausrichtung für Elemente manuell festlegen.</span><span class="sxs-lookup"><span data-stu-id="91846-222">You can manually set alignment with the **hint-align** attribute on elements.</span></span>

```xml
<text hint-align="center">Hello</text>
```


```csharp
new AdaptiveText()
{
    Text = "Hello",
    HintAlign = AdaptiveTextAlign.Center
};
```

**<span data-ttu-id="91846-223">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="91846-223">Result:</span></span>**

![Textausrichtung adaptiver Kacheln](images/adaptive-tiles-textalignment.png)

## <a name="groups-and-subgroups"></a><span data-ttu-id="91846-225">Gruppen und Untergruppen</span><span class="sxs-lookup"><span data-stu-id="91846-225">Groups and subgroups</span></span>


<span data-ttu-id="91846-226">Mit Gruppen können Sie semantisch deklarieren, dass sich Inhalte in der Gruppe aufeinander beziehen und vollständig angezeigt werden müssen, damit sie Sinn ergeben.</span><span class="sxs-lookup"><span data-stu-id="91846-226">Groups allow you to semantically declare that the content inside the group is related and must be displayed in its entirety for the content to make sense.</span></span> <span data-ttu-id="91846-227">Beispielsweise können Sie über zwei text-Elemente in Form einer Überschrift und einer Unterüberschrift verfügen, und es würde keinen Sinn ergeben, wenn nur die Überschrift angezeigt würde.</span><span class="sxs-lookup"><span data-stu-id="91846-227">For example, you might have two text elements, a header, and a subheader, and it would not make sense for only the header to be shown.</span></span> <span data-ttu-id="91846-228">Durch die Gruppierung dieser Elemente innerhalb einer Untergruppe werden entweder alle Elemente angezeigt (sofern sie in den Anzeigebereich passen) oder keine Elemente angezeigt (wenn nicht genügend Platz vorhanden ist).</span><span class="sxs-lookup"><span data-stu-id="91846-228">By grouping those elements inside a subgroup, the elements will either all be displayed (if they can fit) or not be displayed at all (because they can't fit).</span></span>

<span data-ttu-id="91846-229">Um optimale Ergebnisse auf unterschiedlichen Geräten und Bildschirmen zu erzielen, sollten Sie mehrere Gruppen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="91846-229">To provide the best experience across devices and screens, provide multiple groups.</span></span> <span data-ttu-id="91846-230">Mit mehreren Gruppen kann sich die Kachel an größere Bildschirme anpassen.</span><span class="sxs-lookup"><span data-stu-id="91846-230">Having multiple groups allows your tile to adapt to larger screens.</span></span>

<span data-ttu-id="91846-231">**Hinweis**  Das einzige gültige untergeordnete Element einer Gruppe ist eine Untergruppe.</span><span class="sxs-lookup"><span data-stu-id="91846-231">**Note**  The only valid child of a group is a subgroup.</span></span>

 

```xml
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

```csharp
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

**<span data-ttu-id="91846-232">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="91846-232">Result:</span></span>**

![Gruppen und Untergruppen adaptiver Kacheln](images/adaptive-tiles-groups-subgroups.png)

## <a name="subgroups-columns"></a><span data-ttu-id="91846-234">Untergruppen (Spalten)</span><span class="sxs-lookup"><span data-stu-id="91846-234">Subgroups (columns)</span></span>


<span data-ttu-id="91846-235">Mithilfe von Untergruppen können Sie Daten außerdem in semantische Abschnitte innerhalb einer Gruppe unterteilen.</span><span class="sxs-lookup"><span data-stu-id="91846-235">Subgroups also allow you to divide data into semantic sections within a group.</span></span> <span data-ttu-id="91846-236">Bei Live-Kacheln werden Untergruppen visuell als Spalten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="91846-236">For live tiles, this visually translates to columns.</span></span>

<span data-ttu-id="91846-237">Mit dem **hint-weight**-Attribut wird die Breite von Spalten gesteuert.</span><span class="sxs-lookup"><span data-stu-id="91846-237">The **hint-weight** attribute lets you to control the widths of columns.</span></span> <span data-ttu-id="91846-238">Der **hint-weight**-Wert wird als gewichteter Anteil am verfügbaren Platz ausgedrückt, was mit dem **GridUnitType.Star**-Verhalten übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="91846-238">The value of **hint-weight** is expressed as a weighted proportion of available space, which is identical to **GridUnitType.Star** behavior.</span></span> <span data-ttu-id="91846-239">Weisen Sie jeder Gewichtung 1 zu, um Spalten mit gleicher Breite zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="91846-239">For equal-width columns, assign each weight to 1.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="91846-240">hint-weight</span><span class="sxs-lookup"><span data-stu-id="91846-240">hint-weight</span></span></td>
<td align="left"><span data-ttu-id="91846-241">Prozentuale Breite</span><span class="sxs-lookup"><span data-stu-id="91846-241">Percentage of width</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="91846-242">1</span><span class="sxs-lookup"><span data-stu-id="91846-242">1</span></span></td>
<td align="left"><span data-ttu-id="91846-243">25 %</span><span class="sxs-lookup"><span data-stu-id="91846-243">25%</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="91846-244">1</span><span class="sxs-lookup"><span data-stu-id="91846-244">1</span></span></td>
<td align="left"><span data-ttu-id="91846-245">25 %</span><span class="sxs-lookup"><span data-stu-id="91846-245">25%</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="91846-246">1</span><span class="sxs-lookup"><span data-stu-id="91846-246">1</span></span></td>
<td align="left"><span data-ttu-id="91846-247">25 %</span><span class="sxs-lookup"><span data-stu-id="91846-247">25%</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="91846-248">1</span><span class="sxs-lookup"><span data-stu-id="91846-248">1</span></span></td>
<td align="left"><span data-ttu-id="91846-249">25 %</span><span class="sxs-lookup"><span data-stu-id="91846-249">25%</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="91846-250">Gesamtgewichtung: 4</span><span class="sxs-lookup"><span data-stu-id="91846-250">Total weight: 4</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

![Untergruppen, Spalten mit gleicher Breite](images/adaptive-tiles-subgroups01.png)

<span data-ttu-id="91846-252">Um eine Spalte doppelt so groß wie eine andere Spalte darzustellen, weisen Sie der kleineren Spalte die Gewichtung 1 und der größeren Spalte die Gewichtung 2 zu.</span><span class="sxs-lookup"><span data-stu-id="91846-252">To make one column twice as large as another column, assign the smaller column a weight of 1 and the larger column a weight of 2.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="91846-253">hint-weight</span><span class="sxs-lookup"><span data-stu-id="91846-253">hint-weight</span></span></td>
<td align="left"><span data-ttu-id="91846-254">Prozentuale Breite</span><span class="sxs-lookup"><span data-stu-id="91846-254">Percentage of width</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="91846-255">1</span><span class="sxs-lookup"><span data-stu-id="91846-255">1</span></span></td>
<td align="left"><span data-ttu-id="91846-256">33,3 %</span><span class="sxs-lookup"><span data-stu-id="91846-256">33.3%</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="91846-257">2</span><span class="sxs-lookup"><span data-stu-id="91846-257">2</span></span></td>
<td align="left"><span data-ttu-id="91846-258">66,7 %</span><span class="sxs-lookup"><span data-stu-id="91846-258">66.7%</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="91846-259">Gesamtgewichtung: 3</span><span class="sxs-lookup"><span data-stu-id="91846-259">Total weight: 3</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

![Untergruppen, eine Spalte ist doppelt so groß wie die andere](images/adaptive-tiles-subgroups02.png)

<span data-ttu-id="91846-261">Wenn Ihre erste Spalte 20% und die zweite Spalte 80% der gesamten Breite einnehmen soll, weisen Sie der ersten Gewichtung 20 und der zweiten Gewichtung 80 zu.</span><span class="sxs-lookup"><span data-stu-id="91846-261">If you want your first column to take up 20% of the total width and your second column to take up 80% of the total width, assign the first weight to 20 and the second weight to 80.</span></span> <span data-ttu-id="91846-262">Wenn die Gewichtungen insgesamt 100 ergeben, werden sie prozentual ausgedrückt.</span><span class="sxs-lookup"><span data-stu-id="91846-262">If your total weights equal 100, they'll act as percentages.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="91846-263">hint-weight</span><span class="sxs-lookup"><span data-stu-id="91846-263">hint-weight</span></span></td>
<td align="left"><span data-ttu-id="91846-264">Prozentuale Breite</span><span class="sxs-lookup"><span data-stu-id="91846-264">Percentage of width</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="91846-265">20</span><span class="sxs-lookup"><span data-stu-id="91846-265">20</span></span></td>
<td align="left"><span data-ttu-id="91846-266">20 %</span><span class="sxs-lookup"><span data-stu-id="91846-266">20%</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="91846-267">80</span><span class="sxs-lookup"><span data-stu-id="91846-267">80</span></span></td>
<td align="left"><span data-ttu-id="91846-268">80%</span><span class="sxs-lookup"><span data-stu-id="91846-268">80%</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="91846-269">Gesamtgewichtung: 100</span><span class="sxs-lookup"><span data-stu-id="91846-269">Total weight: 100</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

 

![Untergruppen mit einer Gesamtgewichtung von 100](images/adaptive-tiles-subgroups03.png)

<span data-ttu-id="91846-271">**Hinweis**  Zwischen Spalten wird automatisch ein Rand von 8 Pixeln eingefügt.</span><span class="sxs-lookup"><span data-stu-id="91846-271">**Note**  An 8-pixel margin is automatically added between the columns.</span></span>

 

<span data-ttu-id="91846-272">Wenn Sie über mehr als zwei Untergruppen verfügen, geben Sie **hint-weight** an (akzeptiert nur positive ganze Zahlen).</span><span class="sxs-lookup"><span data-stu-id="91846-272">When you have more than two subgroups, you should specify the **hint-weight**, which only accepts positive integers.</span></span> <span data-ttu-id="91846-273">Wenn Sie für die erste Untergruppe „hint-weight“ nicht angeben, wird ihr die Gewichtung 50 zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="91846-273">If you don't specify hint-weight for the first subgroup, it will be assigned a weight of 50.</span></span> <span data-ttu-id="91846-274">Der nächsten Untergruppe, für die „hint-weight“ nicht angegeben wurde, wird die Gewichtung 100 abzüglich der Summe der vorherigen Gewichtungen oder 1 zugewiesen, wenn das Ergebnis 0 (null) ist.</span><span class="sxs-lookup"><span data-stu-id="91846-274">The next subgroup that doesn't have a specified hint-weight will be assigned a weight equal to 100 minus the sum of the preceding weights, or to 1 if the result is zero.</span></span> <span data-ttu-id="91846-275">Den übrigen Untergruppen, für die „hint-weight“ nicht angegeben wurde, wird die Gewichtung 1 zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="91846-275">The remaining subgroups that don't have specified hint-weights will be assigned a weight of 1.</span></span>

<span data-ttu-id="91846-276">Im Folgenden sehen Sie den Beispielcode für eine Wetter-Kachel, die zeigt, wie Sie eine Kachel mit fünf gleich breiten Spalten erhalten:</span><span class="sxs-lookup"><span data-stu-id="91846-276">Here's sample code for a weather tile that shows how you can achieve a tile with five columns of equal width:</span></span>

```xml
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

```csharp
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

**<span data-ttu-id="91846-277">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="91846-277">Result:</span></span>**

![Beispiel für eine Wetter-Kachel](images/adaptive-tiles-weathertile.png)

## <a name="images"></a><span data-ttu-id="91846-279">Bilder</span><span class="sxs-lookup"><span data-stu-id="91846-279">Images</span></span>


<span data-ttu-id="91846-280">Mithilfe des &lt;image&gt;-Elements werden Bilder auf der Kachelbenachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="91846-280">The &lt;image&gt; element is used to display images on the tile notification.</span></span> <span data-ttu-id="91846-281">Bilder können als Inlinebilder im Kachelinhalt (Standard), als Hintergrundbild hinter dem Inhalt oder als animiertes Vorschaubild, das von oben in die Benachrichtigung hineingleitet, konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="91846-281">Images can be placed inline within the tile content (default), as a background image behind your content, or as a peek image that animates in from the top of the notification.</span></span>

> [!NOTE]
> <span data-ttu-id="91846-282">Die verwendeten Bilder können aus dem App-Paket, dem lokalen Speicher der App oder aus dem Web stammen.</span><span class="sxs-lookup"><span data-stu-id="91846-282">Images can be used from the app's package, the app's local storage, or from the web.</span></span> <span data-ttu-id="91846-283">Im Fall Creators Update kann die Größe der Webbilder 3MB für normale Verbindungen und 1MB für getaktete Verbindungen betragen.</span><span class="sxs-lookup"><span data-stu-id="91846-283">As of the Fall Creators Update, web images can be up to 3 MB on normal connections and 1 MB on metered connections.</span></span> <span data-ttu-id="91846-284">Auf Geräten, die noch nicht das Fall Creators Update haben, dürfen Webbilder nicht größer als 200KB sein.</span><span class="sxs-lookup"><span data-stu-id="91846-284">On devices not yet running the Fall Creators Update, web images must be no larger than 200 KB.</span></span>

 

<span data-ttu-id="91846-285">Wenn kein zusätzliches Verhalten angegeben wird, verkleinern bzw. vergrößern sich Bilder gleichmäßig in Anpassung an die verfügbare Breite.</span><span class="sxs-lookup"><span data-stu-id="91846-285">With no extra behaviors specified, images will uniformly shrink or expand to fill the available width.</span></span> <span data-ttu-id="91846-286">Das folgende Beispiel zeigt eine Kachel mit zwei Spalten und Inlinebildern.</span><span class="sxs-lookup"><span data-stu-id="91846-286">This example shows a tile using two columns and inline images.</span></span> <span data-ttu-id="91846-287">Die Inlinebilder werden gestreckt, um die Spaltenbreite auszufüllen.</span><span class="sxs-lookup"><span data-stu-id="91846-287">The inline images stretch to fill the width of the column.</span></span>

```xml
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

```csharp
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

**<span data-ttu-id="91846-288">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="91846-288">Result:</span></span>**

![Bildbeispiel](images/adaptive-tiles-images01.png)

<span data-ttu-id="91846-290">Bilder, die im &lt;binding&gt;-Stammelement oder in der ersten Gruppe enthalten sind, werden ebenfalls gestreckt, um die verfügbare Höhe auszunutzen.</span><span class="sxs-lookup"><span data-stu-id="91846-290">Images placed in the &lt;binding&gt; root, or in the first group, will also stretch to fit the available height.</span></span>

### <a name="image-alignment"></a><span data-ttu-id="91846-291">Bildausrichtung</span><span class="sxs-lookup"><span data-stu-id="91846-291">Image alignment</span></span>

<span data-ttu-id="91846-292">Bilder können mit dem **hint-align**-Attribut linksbündig, zentriert oder rechtsbündig ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="91846-292">Images can be set to align left, center, or right using the **hint-align** attribute.</span></span> <span data-ttu-id="91846-293">Dies bewirkt auch, dass Bilder in ihrer systemeigenen Auflösung angezeigt und nicht gestreckt werden, um die gesamte Breite auszufüllen.</span><span class="sxs-lookup"><span data-stu-id="91846-293">This will also cause images to display at their native resolution instead of stretching to fill width.</span></span>

```xml
<binding template="TileLarge">
  <image src="Assets/fable.jpg" hint-align="center"/>
</binding>
```

```csharp
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

**<span data-ttu-id="91846-294">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="91846-294">Result:</span></span>**

![Beispiel für die Bildausrichtung (linksbündig, zentriert, rechtsbündig)](images/adaptive-tiles-imagealignment.png)

### <a name="image-margins"></a><span data-ttu-id="91846-296">Bildränder</span><span class="sxs-lookup"><span data-stu-id="91846-296">Image margins</span></span>

<span data-ttu-id="91846-297">Zwischen Inlinebildern und darüber oder darunter angeordneten Inhalten befindet sich standardmäßig ein Rand von 8 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="91846-297">By default, inline images have an 8-pixel margin between any content above or below the image.</span></span> <span data-ttu-id="91846-298">Dieser Rand kann entfernt werden, indem Sie das **hint-removeMargin**-Attribut für das Bild verwenden.</span><span class="sxs-lookup"><span data-stu-id="91846-298">This margin can be removed by using the **hint-removeMargin** attribute on the image.</span></span> <span data-ttu-id="91846-299">Für Bilder wird allerdings immer der 8-Pixel-Rand vom Rand der Kachel und für Untergruppen (Spalten) immer der 8-Pixel-Abstand zwischen Spalten beibehalten.</span><span class="sxs-lookup"><span data-stu-id="91846-299">However, images always retain the 8-pixel margin from the edge of the tile, and subgroups (columns) always retain the 8-pixel padding between columns.</span></span>

```xml
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

```csharp
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

### <a name="image-cropping"></a><span data-ttu-id="91846-301">Zuschneiden von Bildern</span><span class="sxs-lookup"><span data-stu-id="91846-301">Image cropping</span></span>

<span data-ttu-id="91846-302">Bilder können mit dem **hint-crop**-Attribut, das derzeit nur die Werte „none“ (Standard) oder „circle“ unterstützt, kreisförmig zugeschnitten werden.</span><span class="sxs-lookup"><span data-stu-id="91846-302">Images can be cropped into a circle using the **hint-crop** attribute, which currently only supports the values "none" (default) or "circle."</span></span>

```xml
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

```csharp
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

**<span data-ttu-id="91846-303">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="91846-303">Result:</span></span>**

![Beispiel für das Zuschneiden eines Bilds](images/adaptive-tiles-imagecropping.png)

### <a name="background-image"></a><span data-ttu-id="91846-305">Hintergrundbild</span><span class="sxs-lookup"><span data-stu-id="91846-305">Background image</span></span>

<span data-ttu-id="91846-306">Um ein Hintergrundbild festzulegen, platzieren Sie ein image-Element im Stamm von &lt;binding&gt; und legen das placement-Attribut auf „background“ fest.</span><span class="sxs-lookup"><span data-stu-id="91846-306">To set a background image, place an image element in the root of the &lt;binding&gt; and set the placement attribute to "background."</span></span>

```xml
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

```csharp
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

**<span data-ttu-id="91846-307">Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="91846-307">Result:</span></span>**

![Beispiel für ein Hintergrundbild](images/adaptive-tiles-backgroundimage.png)

### <a name="peek-image"></a><span data-ttu-id="91846-309">Vorschaubild</span><span class="sxs-lookup"><span data-stu-id="91846-309">Peek image</span></span>

<span data-ttu-id="91846-310">Sie können ein Bild angeben, das von oben in die Kachel hineingleitet.</span><span class="sxs-lookup"><span data-stu-id="91846-310">You can specify an image that "peeks" in from the top of the tile.</span></span> <span data-ttu-id="91846-311">Das Vorschaubild gleitet mithilfe einer Animation von oben in die Kachel hinein, ist kurz auf der Kachel zu sehen und gleitet danach wieder nach oben heraus, um den Blick auf den Hauptinhalt der Kachel freizugeben.</span><span class="sxs-lookup"><span data-stu-id="91846-311">The peek image uses an animation to slide down/up from the top of the tile, peeking into view, and then later sliding back out to reveal the main content on the tile.</span></span> <span data-ttu-id="91846-312">Um ein Vorschaubild festzulegen, platzieren Sie ein image-Element im Stamm von &lt;binding&gt; und legen das placement-Attribut auf „peek“ fest.</span><span class="sxs-lookup"><span data-stu-id="91846-312">To set a peek image, place an image element in the root of the &lt;binding&gt;, and set the placement attribute to "peek."</span></span>

```xml
<binding template="TileMedium" branding="name">
  <image placement="peek" src="Assets/Apps/Hipstame/hipster.jpg"/>
  <text>New Message</text>
  <text hint-style="captionsubtle" hint-wrap="true">Hey, have you tried Windows 10 yet?</text>
</binding>
```

```csharp
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

**<span data-ttu-id="91846-314">Kreisförmiges Zuschneiden für Vorschau- und Hintergrundbilder</span><span class="sxs-lookup"><span data-stu-id="91846-314">Circle crop for peek and background images</span></span>**

<span data-ttu-id="91846-315">Wenden Sie das hint-crop-Attribut auf Vorschau- und Hintergrundbilder an, um einen kreisförmigen Zuschnitt zu erhalten:</span><span class="sxs-lookup"><span data-stu-id="91846-315">Use the hint-crop attribute on peek and background images to do a circle crop:</span></span>

```xml
<image placement="peek" hint-crop="circle" src="Assets/Apps/Hipstame/hipster.jpg"/>
```

```csharp
new TilePeekImage()
{
    HintCrop = TilePeekImageCrop.Circle,
    Source = "Assets/Apps/Hipstame/hipster.jpg"
}
```

<span data-ttu-id="91846-316">Das Ergebnis sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="91846-316">The result will look like this:</span></span>

![Kreisförmiges Zuschneiden für Vorschau- und Hintergrundbilder](images/circlecrop-image.png)

**<span data-ttu-id="91846-318">Verwenden eines Vorschau- und eines Hintergrundbilds</span><span class="sxs-lookup"><span data-stu-id="91846-318">Use both peek and background image</span></span>**

<span data-ttu-id="91846-319">Zur Verwendung eines Vorschau- und eines Hintergrundbilds auf einer Kachelbenachrichtigung geben Sie in der Benachrichtigungsnutzlast sowohl ein Vorschau- als auch ein Hintergrundbild an.</span><span class="sxs-lookup"><span data-stu-id="91846-319">To use both a peek and a background image on a tile notification, specify both a peek image and a background image in your notification payload.</span></span>

<span data-ttu-id="91846-320">Das Ergebnis sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="91846-320">The result will look like this:</span></span>

![Gleichzeitiges Verwenden von Vorschau- und Hintergrundbild](images/peekandbackground.png)


### <a name="peek-and-background-image-overlays"></a><span data-ttu-id="91846-322">Overlays von Vorschau- und Hintergrundbild</span><span class="sxs-lookup"><span data-stu-id="91846-322">Peek and background image overlays</span></span>

<span data-ttu-id="91846-323">Sie können mit **hint-overlay** eine schwarze Überlagerung für Hintergrund- und Vorschaubild festlegen. Das Attribut akzeptiert ganze Zahlen von 0 bis 100, wobei 0 keine Überlagerung und 100 eine vollständige schwarze Überlagerung angibt.</span><span class="sxs-lookup"><span data-stu-id="91846-323">You can set a black overlay on your background and peek images using **hint-overlay**, which accepts integers from 0-100, with 0 being no overlay and 100 being full black overlay.</span></span> <span data-ttu-id="91846-324">Sie können das Overlay verwenden, um sicherzustellen, dass der Text auf der Kachel lesbar ist.</span><span class="sxs-lookup"><span data-stu-id="91846-324">You can use the overlay to help ensure that text on your tile is readable.</span></span>

**<span data-ttu-id="91846-325">Verwenden von „hint-overlay“ für ein Hintergrundbild</span><span class="sxs-lookup"><span data-stu-id="91846-325">Use hint-overlay on a background image</span></span>**

<span data-ttu-id="91846-326">Das Hintergrundbild wird standardmäßig auf eine Überlagerung von 20% festgelegt, solange es in der Nutzlast Textelemente gibt. (Andernfalls wird standardmäßig eine Überlagerung von 0% festgelegt.)</span><span class="sxs-lookup"><span data-stu-id="91846-326">Your background image will default to 20% overlay as long as you have some text elements in your payload (otherwise it will default to 0% overlay).</span></span>

```xml
<binding template="TileWide">
  <image placement="background" hint-overlay="60" src="Assets\Mostly Cloudy-Background.jpg"/>
  ...
</binding>
```

```csharp
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

**<span data-ttu-id="91846-327">Ergebnis von „hint-overlay“:</span><span class="sxs-lookup"><span data-stu-id="91846-327">hint-overlay Result:</span></span>**

![Beispiel für ein Bild mit angewendetem „hint-overlay“](images/adaptive-tiles-image-hintoverlay.png)

**<span data-ttu-id="91846-329">Verwenden von „hint-overlay“ für ein Vorschaubild</span><span class="sxs-lookup"><span data-stu-id="91846-329">Use hint-overlay on a peek image</span></span>**

<span data-ttu-id="91846-330">In Version 1511 von Windows10 unterstützen wir Überlagerungen für Vorschaubilder, genau wie für Hintergrundbilder.</span><span class="sxs-lookup"><span data-stu-id="91846-330">In Version 1511 of Windows 10, we support an overlay for your peek image too, just like your background image.</span></span> <span data-ttu-id="91846-331">Geben Sie „hint-overlay“ für das Vorschaubildelement als ganze Zahl von 0 bis 100 an.</span><span class="sxs-lookup"><span data-stu-id="91846-331">Specify hint-overlay on the peek image element as an integer from 0-100.</span></span> <span data-ttu-id="91846-332">Die Standardüberlagerung für Vorschaubilder ist 0 (keine Überlagerung).</span><span class="sxs-lookup"><span data-stu-id="91846-332">The default overlay for peek images is 0 (no overlay).</span></span>

```xml
<binding template="TileMedium">
  <image hint-overlay="20" src="Assets\Map.jpg" placement="peek"/>
  ...
</binding>
```

```csharp
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

<span data-ttu-id="91846-333">Dieses Beispiel zeigt ein Vorschaubild mit 20% Deckkraft (links) und 0% Deckkraft (rechts):</span><span class="sxs-lookup"><span data-stu-id="91846-333">This example shows a peek image at 20% opacity (left) and at 0% opacity (right):</span></span>

![„hint-overlay“ für ein Vorschaubild](images/hintoverlay.png)

## <a name="vertical-alignment-text-stacking"></a><span data-ttu-id="91846-335">Vertikale Ausrichtung (hint-textStacking)</span><span class="sxs-lookup"><span data-stu-id="91846-335">Vertical alignment (text stacking)</span></span>


<span data-ttu-id="91846-336">Sie können die vertikale Ausrichtung der Inhalte auf einer Kachel steuern, indem Sie das **hint-textStacking**-Attribut sowohl für das [TileBinding](../tiles-and-notifications/tile-schema.md#tilebinding)-Element als auch das [AdaptiveSubgroup](../tiles-and-notifications/tile-schema.md#adaptivesubgroup)-Element verwenden.</span><span class="sxs-lookup"><span data-stu-id="91846-336">You can control the vertical alignment of content on your tile by using the **hint-textStacking** attribute on both the [TileBinding](../tiles-and-notifications/tile-schema.md#tilebinding) element and [AdaptiveSubgroup](../tiles-and-notifications/tile-schema.md#adaptivesubgroup) element.</span></span> <span data-ttu-id="91846-337">Der gesamte Inhalt wird standardmäßig vertikal am oberen Rand ausgerichtet, kann aber auch in der Mitte oder am unteren Rand ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="91846-337">By default, everything is vertically aligned to the top, but you can also align content to the bottom or center.</span></span>

### <a name="text-stacking-on-binding-element"></a><span data-ttu-id="91846-338">Gestapelter Text für binding-Element</span><span class="sxs-lookup"><span data-stu-id="91846-338">Text stacking on binding element</span></span>

<span data-ttu-id="91846-339">Bei Anwendung auf die [TileBinding](../tiles-and-notifications/tile-schema.md#tilebinding)-Ebene wird durch Textstapelung die vertikale Ausrichtung des Benachrichtigungsinhalts als Ganzes festgelegt und im verfügbaren vertikalen Bereich über dem Branding-/Signalbereich ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="91846-339">When applied at the [TileBinding](../tiles-and-notifications/tile-schema.md#tilebinding) level, text stacking sets the vertical alignment of the notification content as a whole, aligning in the available vertical space above the branding/badge area.</span></span>

```xml
<binding template="TileMedium" hint-textStacking="center" branding="logo">
  <text hint-style="base" hint-align="center">Hi,</text>
  <text hint-style="captionSubtle" hint-align="center">MasterHip</text>
</binding>
```

```csharp
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

### <a name="text-stacking-on-subgroup-element"></a><span data-ttu-id="91846-341">Gestapelter Text für subgroup-Element</span><span class="sxs-lookup"><span data-stu-id="91846-341">Text stacking on subgroup element</span></span>

<span data-ttu-id="91846-342">Bei Anwendung auf die [AdaptiveSubgroup](../tiles-and-notifications/tile-schema.md#adaptivesubgroup)-Ebene wird die vertikale Ausrichtung des Inhalts der Untergruppe (Spalte) durch „hint-textStacking” festgelegt und im verfügbaren vertikalen Bereich innerhalb der gesamten Gruppe ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="91846-342">When applied at the [AdaptiveSubgroup](../tiles-and-notifications/tile-schema.md#adaptivesubgroup) level, text stacking sets the vertical alignment of the subgroup (column) content, aligning in the available vertical space within the entire group.</span></span>

```xml
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

```csharp
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

## <a name="related-topics"></a><span data-ttu-id="91846-343">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="91846-343">Related topics</span></span>
* [<span data-ttu-id="91846-344">Kachelinhaltsschema</span><span class="sxs-lookup"><span data-stu-id="91846-344">Tile content schema</span></span>](../tiles-and-notifications/tile-schema.md)
* [<span data-ttu-id="91846-345">Senden einer lokalen Kachelbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="91846-345">Send a local tile notification</span></span>](sending-a-local-tile-notification.md)
* [<span data-ttu-id="91846-346">Spezielle Kachelvorlagen</span><span class="sxs-lookup"><span data-stu-id="91846-346">Special tile templates</span></span>](special-tile-templates-catalog.md)
* [<span data-ttu-id="91846-347">UWP Community Toolkit – Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="91846-347">UWP Community Toolkit - Notifications</span></span>](https://github.com/Microsoft/UWPCommunityToolkit/tree/master/Microsoft.Toolkit.Uwp.Notifications)
* [<span data-ttu-id="91846-348">Windows-Benachrichtigung auf GitHub</span><span class="sxs-lookup"><span data-stu-id="91846-348">Windows Notifications on GitHub</span></span>](https://github.com/WindowsNotifications)

 

 




