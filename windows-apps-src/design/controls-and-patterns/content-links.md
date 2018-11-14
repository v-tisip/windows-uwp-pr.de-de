---
author: jwmsft
Description: Use content links to embed rich data in your text controls.
title: Links zu Inhalten in Textsteuerelementen
label: Content links
template: detail.hbs
ms.author: jimwalk
ms.date: 03/07/2018
ms.topic: article
keywords: Windows10, UWP
pm-contact: miguelrb
design-contact: ''
doc-status: Draft
ms.localizationpriority: medium
ms.openlocfilehash: 3939995aa2f29f4590c8c71a877b69f0cb81d2ec
ms.sourcegitcommit: bdc40b08cbcd46fc379feeda3c63204290e055af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/08/2018
ms.locfileid: "6147866"
---
# <a name="content-links-in-text-controls"></a><span data-ttu-id="1de77-103">Links zu Inhalten in Textsteuerelementen</span><span class="sxs-lookup"><span data-stu-id="1de77-103">Content links in text controls</span></span>

<span data-ttu-id="1de77-104">Links zu Inhalten bieten eine Möglichkeit, umfangreiche Daten in Textsteuerelemente einzubetten, wodurch Benutzer weitere Informationen zu einer Person oder einem Ort finden und verwenden können, ohne den Kontext Ihrer App verlassen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="1de77-104">Content links provide a way to embed rich data in your text controls, which lets a user find and use more information about a person or place without leaving the context of your app.</span></span>

<span data-ttu-id="1de77-105">Wenn der Benutzer einem Eintrag in einer RichEditBox ein kaufmännisches Und-Zeichen (@) als Präfix hinzufügt, wird eine Liste der Personen und/oder Ortsvorschläge angezeigt, die mit dem Eintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="1de77-105">When the user prefixes an entry with an ampersand (@) symbol in a RichEditBox, they’re shown a list of people and/or place suggestions that matches the entry.</span></span> <span data-ttu-id="1de77-106">Wenn der Benutzer dann beispielsweise einen Ort auswählt, wird ein ContentLink für diesen Ort in den Text eingefügt.</span><span class="sxs-lookup"><span data-stu-id="1de77-106">Then, for example, when the user picks a place, a ContentLink for that place is inserted into the text.</span></span> <span data-ttu-id="1de77-107">Wenn der Benutzer den Link zu dem Inhalt aus der RichEditBox aufruft, werden ein Flyout mit einer Karte und zusätzliche Informationen zu dem Ort angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1de77-107">When the user invokes the content link from the RichEditBox, a flyout is shown with a map and additional info about the place.</span></span>

> <span data-ttu-id="1de77-108">**Wichtige APIs**: [ContentLink class](/uwp/api/windows.ui.xaml.documents.contentlink), [ContentLinkInfo class](/uwp/api/windows.ui.text.contentlinkinfo), [RichEditTextRange class](/uwp/api/windows.ui.text.richedittextrange)</span><span class="sxs-lookup"><span data-stu-id="1de77-108">**Important APIs**: [ContentLink class](/uwp/api/windows.ui.xaml.documents.contentlink), [ContentLinkInfo class](/uwp/api/windows.ui.text.contentlinkinfo), [RichEditTextRange class](/uwp/api/windows.ui.text.richedittextrange)</span></span>

> [!NOTE]
> <span data-ttu-id="1de77-109">Die APIs für Links zu Inhalten, die auf die folgenden Namespaces verteilt sind: Windows.UI.Xaml.Controls, Windows.UI.Xaml.Documents und Windows.UI.Text.</span><span class="sxs-lookup"><span data-stu-id="1de77-109">The APIs for content links are spread across the following namespaces: Windows.UI.Xaml.Controls, Windows.UI.Xaml.Documents, and Windows.UI.Text.</span></span>



## <a name="content-links-in-rich-edit-vs-text-block-controls"></a><span data-ttu-id="1de77-110">Links zu Inhalten in Rich-Edit- oder Textblock-Steuerelementen</span><span class="sxs-lookup"><span data-stu-id="1de77-110">Content links in rich edit vs. text block controls</span></span>

<span data-ttu-id="1de77-111">Es gibt zwei unterschiedliche Methoden, Links zu Inhalten zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="1de77-111">There are two distinct ways to use content links:</span></span>

1. <span data-ttu-id="1de77-112">In einem [RichEditBox](/uwp/api/windows.ui.xaml.controls.richeditbox) kann der Benutzer eine Auswahl zum Hinzufügen eines Links öffnen, indem dem Text ein @-Symbol als Präfix angefügt wird.</span><span class="sxs-lookup"><span data-stu-id="1de77-112">In a [RichEditBox](/uwp/api/windows.ui.xaml.controls.richeditbox), the user can open a picker to add a content link by prefixing text with an @ symbol.</span></span> <span data-ttu-id="1de77-113">Der Link zu Inhalten wird als Teil des Rich-Text-Inhalts gespeichert.</span><span class="sxs-lookup"><span data-stu-id="1de77-113">The content link is stored as part the rich text content.</span></span>
1. <span data-ttu-id="1de77-114">In einem [TextBlock](/uwp/api/windows.ui.xaml.controls.textblock) oder [RichTextBlock](/uwp/api/windows.ui.xaml.controls.richtextblock) ist der Link zu Inhalten ein Textelement, dessen Verwendung und Verhalten weitestgehend einem [Hyperlink](/uwp/api/windows.ui.xaml.documents.hyperlink) ähnelt.</span><span class="sxs-lookup"><span data-stu-id="1de77-114">In a [TextBlock](/uwp/api/windows.ui.xaml.controls.textblock) or [RichTextBlock](/uwp/api/windows.ui.xaml.controls.richtextblock), the content link is a text element with usage and behavior much like a [Hyperlink](/uwp/api/windows.ui.xaml.documents.hyperlink).</span></span>

<span data-ttu-id="1de77-115">So sehen Links zu Inhalten standardmäßig in einem RichEditBox und einem Textblock aus.</span><span class="sxs-lookup"><span data-stu-id="1de77-115">Here's how content links look by default in a RichEditBox and in a TextBlock.</span></span>

![<span data-ttu-id="1de77-116">Link zu Inhalten im Rich-Edit-Feld](images/content-link-default-richedit.png)
![Link zu Inhalten im Textblock</span><span class="sxs-lookup"><span data-stu-id="1de77-116">content link in rich edit box](images/content-link-default-richedit.png)
![content link in text block</span></span>](images/content-link-default-textblock.png)

<span data-ttu-id="1de77-117">Unterschiede bei der Verwendung, beim Rendering und beim Verhalten werden in den folgenden Abschnitten ausführlich behandelt.</span><span class="sxs-lookup"><span data-stu-id="1de77-117">Differences in usage, rendering, and behavior are covered in detail in the following sections.</span></span> <span data-ttu-id="1de77-118">Diese Tabelle bietet einen kurzen Vergleich der Hauptunterschiede zwischen einem Link zu Inhalten in einem RichEditBox und einem Textblock.</span><span class="sxs-lookup"><span data-stu-id="1de77-118">This table gives a quick comparison of the main differences between a content link in a RichEditBox and a text block.</span></span>

| <span data-ttu-id="1de77-119">Funktion</span><span class="sxs-lookup"><span data-stu-id="1de77-119">Feature</span></span>   | <span data-ttu-id="1de77-120">RichEditBox</span><span class="sxs-lookup"><span data-stu-id="1de77-120">RichEditBox</span></span> | <span data-ttu-id="1de77-121">Textblock</span><span class="sxs-lookup"><span data-stu-id="1de77-121">text block</span></span> |
| --------- | ----------- | ---------- |
| <span data-ttu-id="1de77-122">Verwendung</span><span class="sxs-lookup"><span data-stu-id="1de77-122">Usage</span></span> | <span data-ttu-id="1de77-123">ContentLinkInfo-Instanz</span><span class="sxs-lookup"><span data-stu-id="1de77-123">ContentLinkInfo instance</span></span> | <span data-ttu-id="1de77-124">ContentLink-Textelement</span><span class="sxs-lookup"><span data-stu-id="1de77-124">ContentLink text element</span></span> |
| <span data-ttu-id="1de77-125">Cursor</span><span class="sxs-lookup"><span data-stu-id="1de77-125">Cursor</span></span> | <span data-ttu-id="1de77-126">Wird durch den Typ des Links zu Inhalten bestimmt, kann nicht geändert werden</span><span class="sxs-lookup"><span data-stu-id="1de77-126">Determined by type of content link, can't be changed</span></span> | <span data-ttu-id="1de77-127">Wird durch die Cursor-Eigenschaft bestimmt, standardmäßig **null**</span><span class="sxs-lookup"><span data-stu-id="1de77-127">Determined by Cursor property, **null** by default</span></span> |
| <span data-ttu-id="1de77-128">ToolTip</span><span class="sxs-lookup"><span data-stu-id="1de77-128">ToolTip</span></span> | <span data-ttu-id="1de77-129">Nicht gerendert</span><span class="sxs-lookup"><span data-stu-id="1de77-129">Not rendered</span></span> | <span data-ttu-id="1de77-130">Zeigt sekundären Text an</span><span class="sxs-lookup"><span data-stu-id="1de77-130">Shows secondary text</span></span> |

## <a name="enable-content-links-in-a-richeditbox"></a><span data-ttu-id="1de77-131">Aktiviert Links zu Inhalten in einem RichEditBox</span><span class="sxs-lookup"><span data-stu-id="1de77-131">Enable content links in a RichEditBox</span></span>

<span data-ttu-id="1de77-132">Ein Link zu Inhalten wird am häufigsten verwendet, um einem Benutzer das schnelle Hinzufügen von Informationen zu ermöglichen, indem dem Namen einer Person oder eines Ortes ein kaufmännische Und-Zeichen (@) im entsprechenden Text vorangestellt wird.</span><span class="sxs-lookup"><span data-stu-id="1de77-132">The most common use of a content link is to let a user quickly add information by prefixing a person or place name with an ampersand (@) symbol in their text.</span></span> <span data-ttu-id="1de77-133">Bei Aktivierung in einem [RichEditBox](/uwp/api/windows.ui.xaml.controls.richeditbox) wird eine Auswahl geöffnet und der Benutzer kann eine Person aus seiner Kontaktliste oder, je aktivierter Option, einen nahegelegenen Ort hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="1de77-133">When enabled in a [RichEditBox](/uwp/api/windows.ui.xaml.controls.richeditbox), this opens a picker and lets the user insert a person from their contact list, or a nearby place, depending on what you’ve enabled.</span></span>

<span data-ttu-id="1de77-134">Der Link zu Inhalten kann mit dem Rich-Text-Inhalt gespeichert werden, und Sie können ihn zur Verwendung in anderen Bereichen Ihrer App extrahieren.</span><span class="sxs-lookup"><span data-stu-id="1de77-134">The content link can be saved with the rich text content, and you can extract it to use in other parts of your app.</span></span> <span data-ttu-id="1de77-135">In einer E-Mail-App können Sie beispielsweise die persönlichen Informationen extrahieren und verwenden, um das Feld „An“ mit einer E-Mail-Adresse zu füllen.</span><span class="sxs-lookup"><span data-stu-id="1de77-135">For example, in an email app, you might extract the person info and use it to populate the To box with an email address.</span></span>

> [!NOTE]
> <span data-ttu-id="1de77-136">Die Auswahl von Links zu Inhalten ist eine App, die Teil von Windows ist und daher in einem separaten Prozess über Ihre App ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="1de77-136">The content link picker is an app that’s part of Windows, so it runs in a separate process from your app.</span></span>

### <a name="content-link-providers"></a><span data-ttu-id="1de77-137">Anbieter von Links zu Inhalten</span><span class="sxs-lookup"><span data-stu-id="1de77-137">Content link providers</span></span>

<span data-ttu-id="1de77-138">Links zu Inhalten werden in einem RichEditBox aktiviert, indem mindestens ein Anbieter für Links zu Inhalten der Sammlung [RichEditBox.ContentLinkProviders](/uwp/api/windows.ui.xaml.controls.richeditbox.ContentLinkProviders) hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="1de77-138">You enable content links in a RichEditBox by adding one or more content link providers to the [RichEditBox.ContentLinkProviders](/uwp/api/windows.ui.xaml.controls.richeditbox.ContentLinkProviders) collection.</span></span> <span data-ttu-id="1de77-139">Es gibt zwei Anbieter für Links zu Inhalten, die in das XAML-Framework integriert sind.</span><span class="sxs-lookup"><span data-stu-id="1de77-139">There are 2 content link providers built into the XAML framework.</span></span>

- <span data-ttu-id="1de77-140">[ContactContentLinkProvider](/uwp/api/windows.ui.xaml.documents.contactcontentlinkprovider) – Sucht mithilfe der **Personen** App nach Kontakten.</span><span class="sxs-lookup"><span data-stu-id="1de77-140">[ContactContentLinkProvider](/uwp/api/windows.ui.xaml.documents.contactcontentlinkprovider) – looks up contacts using the **People** app.</span></span>
- <span data-ttu-id="1de77-141">[PlaceContentLinkProvider](/uwp/api/windows.ui.xaml.documents.placecontentlinkprovider) – Sucht mithilfe der **Karten**-App nach Inhalten.</span><span class="sxs-lookup"><span data-stu-id="1de77-141">[PlaceContentLinkProvider](/uwp/api/windows.ui.xaml.documents.placecontentlinkprovider) – looks up places using the **Maps** app.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1de77-142">Der Standardwert für die RichEditBox.ContentLinkProviders-Eigenschaft ist **null**, nicht etwa eine leere Sammlung.</span><span class="sxs-lookup"><span data-stu-id="1de77-142">The default value for the RichEditBox.ContentLinkProviders property is **null**, not an empty collection.</span></span> <span data-ttu-id="1de77-143">Sie müssen ausdrücklich die [ContentLinkProviderCollection](/uwp/api/windows.ui.xaml.documents.contentlinkprovidercollection) erstellen, bevor Sie Anbieter für Links zu Inhalten hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="1de77-143">You need to explicity create the [ContentLinkProviderCollection](/uwp/api/windows.ui.xaml.documents.contentlinkprovidercollection) before you add content link providers.</span></span>

<span data-ttu-id="1de77-144">Hier erfahren Sie, wie Sie die Anbieter für Links zu Inhalten in XAML hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="1de77-144">Here’s how to add the content link providers in XAML.</span></span>

```xaml
<RichEditBox>
    <RichEditBox.ContentLinkProviders>
        <ContentLinkProviderCollection>
            <ContactContentLinkProvider/>
            <PlaceContentLinkProvider/>
        </ContentLinkProviderCollection>
    </RichEditBox.ContentLinkProviders>
</RichEditBox>
```

<span data-ttu-id="1de77-145">Sie können Anbieter für Links zu Inhalten auch in einem Stil hinzufügen und ihn auf mehrere RichEditBoxes wie dieses anwenden.</span><span class="sxs-lookup"><span data-stu-id="1de77-145">You can also add content link providers in a Style and apply it to multiple RichEditBoxes like this.</span></span>

```xaml
<Page.Resources>
    <Style TargetType="RichEditBox" x:Key="ContentLinkStyle">
        <Setter Property="ContentLinkProviders">
            <Setter.Value>
                <ContentLinkProviderCollection>
                    <PlaceContentLinkProvider/>
                    <ContactContentLinkProvider/>
                </ContentLinkProviderCollection>
            </Setter.Value>
        </Setter>
    </Style>
</Page.Resources>

<RichEditBox x:Name="RichEditBox01" Style="{StaticResource ContentLinkStyle}" />
<RichEditBox x:Name="RichEditBox02" Style="{StaticResource ContentLinkStyle}" />
```

<span data-ttu-id="1de77-146">Hier erfahren Sie, wie Sie die Anbieter für Links zu Inhalten in Code hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="1de77-146">Here's how to add content link providers in code.</span></span>

```csharp
RichEditBox editor = new RichEditBox();
editor.ContentLinkProviders = new ContentLinkProviderCollection
{
    new ContactContentLinkProvider(),
    new PlaceContentLinkProvider()
};
```

### <a name="content-link-colors"></a><span data-ttu-id="1de77-147">Farben für Links zu Inhalten</span><span class="sxs-lookup"><span data-stu-id="1de77-147">Content link colors</span></span>

<span data-ttu-id="1de77-148">Das Aussehen eines Links zu Inhalten wird durch dessen Vordergrund, Hintergrund und Symbol bestimmt.</span><span class="sxs-lookup"><span data-stu-id="1de77-148">The appearance of a content link is determined by its foreground, background, and icon.</span></span> <span data-ttu-id="1de77-149">In einer RichEditBox können Sie die Eigenschaften [ContentLinkForegroundColor](/uwp/api/windows.ui.xaml.controls.richeditbox.ContentLinkForegroundColor) und [ContentLinkBackgroundColor](/uwp/api/windows.ui.xaml.controls.richeditbox.ContentLinkBackgroundColor) so festlegen, dass die Standardfarben geändert werden.</span><span class="sxs-lookup"><span data-stu-id="1de77-149">In a RichEditBox, you can set the [ContentLinkForegroundColor](/uwp/api/windows.ui.xaml.controls.richeditbox.ContentLinkForegroundColor) and [ContentLinkBackgroundColor](/uwp/api/windows.ui.xaml.controls.richeditbox.ContentLinkBackgroundColor) properties to change the default colors.</span></span> 

<span data-ttu-id="1de77-150">Der Cursor kann nicht festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="1de77-150">You can't set the cursor.</span></span> <span data-ttu-id="1de77-151">Der Cursor wird durch das RichEditbox basierend auf dem Typ des Links zu Inhalten gerendert – ein [Person](/uwp/api/windows.ui.core.corecursortype)-Cursor für einen Link zu einer Person oder ein [Pin](/uwp/api/windows.ui.core.corecursortype)-Cursor für einen Link zu einem Ort.</span><span class="sxs-lookup"><span data-stu-id="1de77-151">The cursor is rendered by the RichEditbox based on the type of content link - a [Person](/uwp/api/windows.ui.core.corecursortype) cursor for a person link, or a [Pin](/uwp/api/windows.ui.core.corecursortype) cursor for a place link.</span></span>

### <a name="the-contentlinkinfo-object"></a><span data-ttu-id="1de77-152">Das ContentLinkInfo-Objekt</span><span class="sxs-lookup"><span data-stu-id="1de77-152">The ContentLinkInfo object</span></span>

<span data-ttu-id="1de77-153">Wenn der Benutzer eine Auswahl über die Personen- oder Ortsauswahl vornimmt, erstellt das System ein [ContentLinkInfo](/uwp/api/windows.ui.text.contentlinkinfo)-Objekt und fügt es der **ContentLinkInfo**-Eigenschaft des aktuellen [RichEditTextRange ](/uwp/api/windows.ui.text.richedittextrange) hinzu.</span><span class="sxs-lookup"><span data-stu-id="1de77-153">When the user makes a selection from the people or places picker, the system creates a [ContentLinkInfo](/uwp/api/windows.ui.text.contentlinkinfo) object and adds it to the **ContentLinkInfo** property of the current [RichEditTextRange](/uwp/api/windows.ui.text.richedittextrange).</span></span>

<span data-ttu-id="1de77-154">Das ContentLinkInfo-Objekt enthält die Informationen, die zum Anzeigen, Aufrufen und Verwalten des Links zu Inhalten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1de77-154">The ContentLinkInfo object contains the information used to display, invoke, and manage the content link.</span></span>

- <span data-ttu-id="1de77-155">**Anzeigetext** – Dies ist die Zeichenfolge, die beim Rendern des Links zu Inhalten angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="1de77-155">**DisplayText** – This is the string that is shown when the content link is rendered.</span></span> <span data-ttu-id="1de77-156">In einem RichEditBox kann der Benutzer den Text eines Links zu Inhalten nach dem Erstellen bearbeiten, wodurch der Wert dieser Eigenschaft geändert wird.</span><span class="sxs-lookup"><span data-stu-id="1de77-156">In a RichEditBox, the user can edit the text of a content link after it’s created, which alters the value of this property.</span></span>
- <span data-ttu-id="1de77-157">**SecondaryText** – Diese Zeichenfolge wird in der QuickInfo eines gerenderten Links zu Inhalten angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1de77-157">**SecondaryText** – This string is shown in the ToolTip of a rendered content link.</span></span>
  - <span data-ttu-id="1de77-158">In einem Link zu Inhalten für Orte, der über die Auswahl erstellt wurde, enthält sie die Adresse des Ortes, falls verfügbar.</span><span class="sxs-lookup"><span data-stu-id="1de77-158">In a Place content link created by the picker, it contains the address of the location, if available.</span></span>
- <span data-ttu-id="1de77-159">**URI** – Der Link zu weiteren Informationen zum Betreff des Links zu Inhalten.</span><span class="sxs-lookup"><span data-stu-id="1de77-159">**Uri** – The link to more information about the subject of the content link.</span></span> <span data-ttu-id="1de77-160">Mit diesem URI kann eine installierte App oder eine Website geöffnet werden.</span><span class="sxs-lookup"><span data-stu-id="1de77-160">This Uri can open an installed app or a website.</span></span>
- <span data-ttu-id="1de77-161">**ID** – Dies ist ein schreibgeschützter Zähler für das jeweilige Steuerelement, der durch das RichEditBox-Steuerelement erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="1de77-161">**Id** - This is a read-only, per control, counter created by the RichEditBox control.</span></span> <span data-ttu-id="1de77-162">Er dient zum Nachverfolgen dieser ContentLinkInfo, wenn beispielsweise Lösch- oder Bearbeitungsaktionen durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="1de77-162">It’s used to track this ContentLinkInfo during actions such as delete or edit.</span></span> <span data-ttu-id="1de77-163">Wenn das ContentLinkInfo-Objekt ausgeschnitten und wieder in das Steuerelement eingefügt wird, erhält es eine neue ID. ID-Werte sind inkrementell.</span><span class="sxs-lookup"><span data-stu-id="1de77-163">If the ContentLinkInfo is cut and paste back into the control, it will get a new Id. Id values are incremental.</span></span>
- <span data-ttu-id="1de77-164">**LinkContentKind** – Eine Zeichenfolge, die den Typ des Links zu Inhalten beschreibt.</span><span class="sxs-lookup"><span data-stu-id="1de77-164">**LinkContentKind** – A string that describes the type of the content link.</span></span> <span data-ttu-id="1de77-165">Die integrierten Inhaltstypen sind _Orte_ und _Kontakte_.</span><span class="sxs-lookup"><span data-stu-id="1de77-165">The built-in content types are _Places_ and _Contacts_.</span></span> <span data-ttu-id="1de77-166">Beim Wert wird die Groß-/Kleinschreibung berücksichtigt.</span><span class="sxs-lookup"><span data-stu-id="1de77-166">The value is case sensitive.</span></span>

#### <a name="link-content-kind"></a><span data-ttu-id="1de77-167">Art des Links zu Inhalten</span><span class="sxs-lookup"><span data-stu-id="1de77-167">Link content kind</span></span>

<span data-ttu-id="1de77-168">Es gibt verschiedene Situationen, in denen die LinkContentKind wichtig ist.</span><span class="sxs-lookup"><span data-stu-id="1de77-168">There are several situations where the LinkContentKind is important.</span></span>

- <span data-ttu-id="1de77-169">Wenn ein Benutzer einen Link zu Inhalten aus einem RichEditBox kopiert und ihn in ein anderes RichEditBox einfügt, müssen beide Steuerelemente über einen ContentLinkProvider für diesen Inhaltstyp verfügen.</span><span class="sxs-lookup"><span data-stu-id="1de77-169">When a user copies a content link from a RichEditBox and pastes it into another RichEditBox, both controls must have a ContentLinkProvider for that content type.</span></span> <span data-ttu-id="1de77-170">Wenn dies nicht der Fall ist, wird der Link als Text eingefügt.</span><span class="sxs-lookup"><span data-stu-id="1de77-170">If not, the link is pasted as text.</span></span>
- <span data-ttu-id="1de77-171">Sie können LinkContentKind in einem [ContentLinkChanged](/uwp/api/windows.ui.xaml.controls.richeditbox.ContentLinkChanged)-Ereignishandler verwenden, um zu bestimmen, welche Aktion mit einem Content Link ausgeführt werden soll, wenn Sie ihn in anderen Bereichen Ihrer App verwenden.</span><span class="sxs-lookup"><span data-stu-id="1de77-171">You can use LinkContentKind in a [ContentLinkChanged](/uwp/api/windows.ui.xaml.controls.richeditbox.ContentLinkChanged) event handler to determine what to do with a content link when you use it in other parts of your app.</span></span> <span data-ttu-id="1de77-172">Weitere Informationen finden Sie im Abschnitt „Beispiel“.</span><span class="sxs-lookup"><span data-stu-id="1de77-172">See the Example section for more info.</span></span>
- <span data-ttu-id="1de77-173">Die LinkContentKind wirkt sich darauf aus, wie das System den URI öffnet, wenn der Link aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="1de77-173">The LinkContentKind influences how the system opens the Uri when the link is invoked.</span></span> <span data-ttu-id="1de77-174">Weitere Informationen hierzu, erhalten Sie im folgenden Abschnitt zum Starten von URIs.</span><span class="sxs-lookup"><span data-stu-id="1de77-174">We’ll see this in the discussion of Uri launching next.</span></span>

#### <a name="uri-launching"></a><span data-ttu-id="1de77-175">Starten des URI</span><span class="sxs-lookup"><span data-stu-id="1de77-175">Uri launching</span></span>

<span data-ttu-id="1de77-176">Die Uri-Eigenschaft funktioniert ähnlich wie die NavigateUri-Eigenschaft eines Hyperlinks.</span><span class="sxs-lookup"><span data-stu-id="1de77-176">The Uri property works much like the NavigateUri property of a Hyperlink.</span></span> <span data-ttu-id="1de77-177">Wenn ein Benutzer darauf klickt, wird der URI im Standardbrowser oder in der App gestartet, die für das spezielle im URI-Wert angegebene Protokoll registriert ist.</span><span class="sxs-lookup"><span data-stu-id="1de77-177">When a user clicks it, it launches the Uri in the default browser, or in the app that's registered for the particular protocol specified in the Uri value.</span></span>

<span data-ttu-id="1de77-178">Hier wird das spezifische Verhalten für die beiden integrierten Arten von Link-Inhalten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="1de77-178">The specific behavior for the 2 built in kinds of link content are described here.</span></span>

##### <a name="places"></a><span data-ttu-id="1de77-179">Orte</span><span class="sxs-lookup"><span data-stu-id="1de77-179">Places</span></span>

<span data-ttu-id="1de77-180">Die Ortsauswahl erstellt ContentLinkInfo mit dem URI-Stamm https://maps.windows.com/.</span><span class="sxs-lookup"><span data-stu-id="1de77-180">The Places picker creates a ContentLinkInfo with a Uri root of https://maps.windows.com/.</span></span> <span data-ttu-id="1de77-181">Es gibt drei Möglichkeiten, diesen Link zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="1de77-181">This link can be opened in 3 ways:</span></span>

- <span data-ttu-id="1de77-182">Wenn LinkContentKind „Orte“ entspricht, wird eine Infokarte in einem Flyout geöffnet.</span><span class="sxs-lookup"><span data-stu-id="1de77-182">If LinkContentKind = "Places", it opens an info card in a flyout.</span></span> <span data-ttu-id="1de77-183">Das Flyout ist vergleichbar mit dem Auswahl-Flyout für Links zu Inhalten.</span><span class="sxs-lookup"><span data-stu-id="1de77-183">The flyout is similar to the content link picker flyout.</span></span> <span data-ttu-id="1de77-184">Es ist Bestandteil von Windows und wird in einem separaten Prozess von Ihrer App ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="1de77-184">It’s part of Windows, and runs in a separate process from your app.</span></span>
- <span data-ttu-id="1de77-185">Wenn LinkContentKind nicht „Orte“ entspricht, wird versucht, die **Karten**-App am angegebenen Speicherort zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="1de77-185">If LinkContentKind is not "Places", it attempts to open the **Maps** app to the specified location.</span></span> <span data-ttu-id="1de77-186">Dies kann beispielsweise der Fall sein, wenn Sie die LinkContentKind im ContentLinkChanged-Ereignishandler geändert haben.</span><span class="sxs-lookup"><span data-stu-id="1de77-186">For example, this can happen if you’ve modified the LinkContentKind in the ContentLinkChanged event handler.</span></span>
- <span data-ttu-id="1de77-187">Wenn der URI nicht in der Karten-App geöffnet werden kann, wird die Karte im Standardbrowser geöffnet.</span><span class="sxs-lookup"><span data-stu-id="1de77-187">If the Uri can’t be opened in the Maps app, the map is opened in the default browser.</span></span> <span data-ttu-id="1de77-188">Dies ist in der Regel dann der Fall, wenn die _Apps für Websites_-Einstellungen des Benutzers das Öffnen der URI mit der **Karten**-App nicht zulassen.</span><span class="sxs-lookup"><span data-stu-id="1de77-188">This typically happens when the user's _Apps for websites_ settings don’t allow opening the Uri with the **Maps** app.</span></span>

##### <a name="people"></a><span data-ttu-id="1de77-189">Personen</span><span class="sxs-lookup"><span data-stu-id="1de77-189">People</span></span>

<span data-ttu-id="1de77-190">Die Personenauswahl erstellt eine ContentLinkInfo mit einem Uri, der das **ms-People**-Protokoll verwendet.</span><span class="sxs-lookup"><span data-stu-id="1de77-190">The People picker creates a ContentLinkInfo with a Uri that uses the **ms-people** protocol.</span></span>

- <span data-ttu-id="1de77-191">Wenn LinkContentKind „Personen“ entspricht, wird eine Infokarte in einem Flyout geöffnet.</span><span class="sxs-lookup"><span data-stu-id="1de77-191">If LinkContentKind = "People", it opens an info card in a flyout.</span></span> <span data-ttu-id="1de77-192">Das Flyout ist vergleichbar mit dem Auswahl-Flyout für Links zu Inhalten.</span><span class="sxs-lookup"><span data-stu-id="1de77-192">The flyout is similar to the content link picker flyout.</span></span> <span data-ttu-id="1de77-193">Es ist Bestandteil von Windows und wird in einem separaten Prozess von Ihrer App ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="1de77-193">It’s part of Windows, and runs in a separate process from your app.</span></span>
- <span data-ttu-id="1de77-194">Wenn LinkContentKind nicht „Personen“ entspricht, wird die **Personen**-App geöffnet.</span><span class="sxs-lookup"><span data-stu-id="1de77-194">If LinkContentKind is not "People", it opens the **People** app.</span></span> <span data-ttu-id="1de77-195">Dies kann beispielsweise der Fall sein, wenn Sie die LinkContentKind im ContentLinkChanged-Ereignishandler geändert haben.</span><span class="sxs-lookup"><span data-stu-id="1de77-195">For example, this can happen if you’ve modified the LinkContentKind in the ContentLinkChanged event handler.</span></span>

> [!TIP]
> <span data-ttu-id="1de77-196">Weitere Informationen zum Öffnen von anderen apps und Websites über Ihre app finden Sie unter den Themen unter [Starten einer app mit einem Uri](/windows/uwp/launch-resume/launch-app-with-uri).</span><span class="sxs-lookup"><span data-stu-id="1de77-196">For more info about opening other apps and websites from your app, see the topics under [Launch an app with a Uri](/windows/uwp/launch-resume/launch-app-with-uri).</span></span>

#### <a name="invoked"></a><span data-ttu-id="1de77-197">Aufgerufen</span><span class="sxs-lookup"><span data-stu-id="1de77-197">Invoked</span></span>

<span data-ttu-id="1de77-198">Wenn der Benutzer einen Link zu Inhalten aufruft, wird das [ContentLinkInvoked](/uwp/api/windows.ui.xaml.controls.richeditbox.ContentLinkInvoked)-Ereignis vor dem Standardverhalten zum Starten des URI ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="1de77-198">When the user invokes a content link, the [ContentLinkInvoked](/uwp/api/windows.ui.xaml.controls.richeditbox.ContentLinkInvoked) event is raised before the default behavior of launching the Uri happens.</span></span> <span data-ttu-id="1de77-199">Sie können dieses Ereignis behandeln, um das Standardverhalten außer Kraft zu setzen oder abzubrechen.</span><span class="sxs-lookup"><span data-stu-id="1de77-199">You can handle this event to override or cancel the default behavior.</span></span>

<span data-ttu-id="1de77-200">Dieses Beispiel zeigt, wie Sie das standardmäßige Startverhalten für einen Link zu Inhalten für Orte außer Kraft setzen können.</span><span class="sxs-lookup"><span data-stu-id="1de77-200">This example shows how you can override the default launching behavior for a Place content link.</span></span> <span data-ttu-id="1de77-201">Anstatt die Karte in einer Infokarte für Orte, einer Karten-App oder im Standard-Webbrowser zu öffnen, markieren Sie das Ereignis als verarbeitet, und öffnen Sie die Karte im [WebView](/uwp/api/windows.ui.xaml.controls.webview)-Steuerelement einer In-App.</span><span class="sxs-lookup"><span data-stu-id="1de77-201">Instead of opening the map in a Place info card, Maps app, or default web browser, you mark the event as Handled and open the map in an in-app [WebView](/uwp/api/windows.ui.xaml.controls.webview) control.</span></span>

```xaml
<RichEditBox x:Name="editor"
             ContentLinkInvoked="editor_ContentLinkInvoked">
    <RichEditBox.ContentLinkProviders>
        <ContentLinkProviderCollection>
            <PlaceContentLinkProvider/>
        </ContentLinkProviderCollection>
    </RichEditBox.ContentLinkProviders>
</RichEditBox>

<WebView x:Name="webView1"/>
```

```csharp
private void editor_ContentLinkInvoked(RichEditBox sender, ContentLinkInvokedEventArgs args)
{
    if (args.ContentLinkInfo.LinkContentKind == "Places")
    {
        args.Handled = true;
        webView1.Navigate(args.ContentLinkInfo.Uri);
    }
}
```

#### <a name="contentlinkchanged"></a><span data-ttu-id="1de77-202">ContentLinkChanged</span><span class="sxs-lookup"><span data-stu-id="1de77-202">ContentLinkChanged</span></span>

<span data-ttu-id="1de77-203">Sie können das [ContentLinkChanged](/uwp/api/windows.ui.xaml.controls.richeditbox.ContentLinkChanged) -Ereignis verwenden, um benachrichtigt zu werden, wenn ein Link zu Inhalten hinzugefügt, geändert oder entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="1de77-203">You can use the [ContentLinkChanged](/uwp/api/windows.ui.xaml.controls.richeditbox.ContentLinkChanged) event to be notified when a content link is added, modified, or removed.</span></span> <span data-ttu-id="1de77-204">Auf diese Weise können Sie den Link zu Inhalten aus dem Text extrahieren und ihn in anderen Bereichen Ihrer App verwenden.</span><span class="sxs-lookup"><span data-stu-id="1de77-204">This lets you extract the content link from the text and use it in other places in your app.</span></span> <span data-ttu-id="1de77-205">Dies wird später im Abschnitt „Beispiele“ veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="1de77-205">This is shown later in the Examples section.</span></span>

<span data-ttu-id="1de77-206">Die Eigenschaften der [ContentLinkChangedEventArgs](/uwp/api/windows.ui.xaml.controls.contentlinkchangedeventargs) lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="1de77-206">The properties of the [ContentLinkChangedEventArgs](/uwp/api/windows.ui.xaml.controls.contentlinkchangedeventargs) are:</span></span>

- <span data-ttu-id="1de77-207">**ChangedKind** – Diese ContentLinkChangeKind-Enumeration ist die Aktion innerhalb des ContentLink.</span><span class="sxs-lookup"><span data-stu-id="1de77-207">**ChangedKind** - This ContentLinkChangeKind enum is the action within the ContentLink.</span></span> <span data-ttu-id="1de77-208">Wenn der ContentLink beispielsweise eingefügt, entfernt oder bearbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="1de77-208">For example, if the ContentLink is inserted, removed, or edited.</span></span>
- <span data-ttu-id="1de77-209">**Info** – Die ContentLinkInfo, die das Ziel der Aktion war.</span><span class="sxs-lookup"><span data-stu-id="1de77-209">**Info** - The ContentLinkInfo that was the target of the action.</span></span>

<span data-ttu-id="1de77-210">Dieses Ereignis wird für jede ContentLinkInfo-Aktion ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="1de77-210">This event is raised for each ContentLinkInfo action.</span></span> <span data-ttu-id="1de77-211">Wenn der Benutzer beispielsweise mehrere Links zu Inhalten gleichzeitig kopiert und in das RichEditBox einfügt, wird dieses Ereignis für jedes hinzugefügte Element ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="1de77-211">For example, if the user copies and pastes several content links into the RichEditBox at once, this event is raised for each added item.</span></span> <span data-ttu-id="1de77-212">Oder wenn der Benutzer mehrere Links zu Inhalten gleichzeitig auswählt und löscht, wird dieses Ereignis für jedes gelöschte Element ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="1de77-212">Or if the user selects and deletes several content links at the same time, this event is raised for each deleted item.</span></span>

<span data-ttu-id="1de77-213">Dieses Ereignis wird nach dem **TextChanging**-Ereignis und vor dem **TextChanged**-Ereignis für das RichEditBox ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="1de77-213">This event is raised on the RichEditBox after the **TextChanging** event and before the **TextChanged** event.</span></span>

#### <a name="enumerate-content-links-in-a-richeditbox"></a><span data-ttu-id="1de77-214">Aufzählen von Links zu Inhalten in einem RichEditBox</span><span class="sxs-lookup"><span data-stu-id="1de77-214">Enumerate content links in a RichEditBox</span></span>

<span data-ttu-id="1de77-215">Sie können die RichEditTextRange.ContentLink-Eigenschaft verwenden, um einen Link zu Inhalten aus einem Rich-Edit-Dokument abzurufen.</span><span class="sxs-lookup"><span data-stu-id="1de77-215">You can use the RichEditTextRange.ContentLink property to get a content link from a rich edit document.</span></span> <span data-ttu-id="1de77-216">Die TextRangeUnit-Enumeration hat den Wert ContentLink, um den Link zu Inhalten als eine Einheit festzulegen, die beim Navigieren in einem Textbereich verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="1de77-216">The TextRangeUnit enumeration has the value ContentLink to specify the content link as a unit to use when navigating a text range.</span></span>

<span data-ttu-id="1de77-217">Dieses Beispiel zeigt, wie Sie alle Links zu Inhalten in einem RichEditBox auflisten und die Personen in einer Liste extrahieren können.</span><span class="sxs-lookup"><span data-stu-id="1de77-217">This example shows how you can enumerate all the content links in a RichEditBox, and extract the people into a list.</span></span>

```xaml
<StackPanel Width="300">
    <RichEditBox x:Name="Editor" Height="200">
        <RichEditBox.ContentLinkProviders>
            <ContentLinkProviderCollection>
                <ContactContentLinkProvider/>
                <PlaceContentLinkProvider/>
            </ContentLinkProviderCollection>
        </RichEditBox.ContentLinkProviders>
    </RichEditBox>

    <Button Content="Get people" Click="Button_Click"/>

    <ListView x:Name="PeopleList" Header="People">
        <ListView.ItemTemplate>
            <DataTemplate x:DataType="ContentLinkInfo">
                <TextBlock>
                    <ContentLink Info="{x:Bind}" Background="Transparent"/>
                </TextBlock>
            </DataTemplate>
        </ListView.ItemTemplate>
    </ListView>
</StackPanel>
```

```csharp
private void Button_Click(object sender, RoutedEventArgs e)
{
    PeopleList.Items.Clear();
    RichEditTextRange textRange = Editor.Document.GetRange(0, 0) as RichEditTextRange;

    do
    {
        // The Expand method expands the Range EndPosition 
        // until it finds a ContentLink range. 
        textRange.Expand(TextRangeUnit.ContentLink);
        if (textRange.ContentLinkInfo != null
            && textRange.ContentLinkInfo.LinkContentKind == "People")
        {
            PeopleList.Items.Add(textRange.ContentLinkInfo);
        }
    } while (textRange.MoveStart(TextRangeUnit.ContentLink, 1) > 0);
}
```

## <a name="contentlink-text-element"></a><span data-ttu-id="1de77-218">ContentLink-Textelement</span><span class="sxs-lookup"><span data-stu-id="1de77-218">ContentLink text element</span></span>

<span data-ttu-id="1de77-219">Um einen Link zu Inhalten in einem TextBlock- oder RichTextBlock-Steuerelement verwenden zu können, verwenden Sie das [ContentLink](/uwp/api/windows.ui.xaml.documents.contentlink)-Textelement (aus dem Windows.UI.Xaml.Documents-Namespace).</span><span class="sxs-lookup"><span data-stu-id="1de77-219">To use a content link in a TextBlock or RichTextBlock control, you use the [ContentLink](/uwp/api/windows.ui.xaml.documents.contentlink) text element (from the Windows.UI.Xaml.Documents namespace).</span></span>

<span data-ttu-id="1de77-220">Nachfolgend finden Sie typische Quellen für einen ContentLink in einem Textblock:</span><span class="sxs-lookup"><span data-stu-id="1de77-220">Typical sources for a ContentLink in a text block are:</span></span>

- <span data-ttu-id="1de77-221">Ein von einer Auswahl erstellter Link zu Inhalten, den Sie aus einem RichTextBlock-Steuerelement extrahiert haben.</span><span class="sxs-lookup"><span data-stu-id="1de77-221">A content link created by a picker that you extracted from a RichTextBlock control.</span></span>
- <span data-ttu-id="1de77-222">Ein Link zu Inhalten für einen Ort, den Sie in Ihrem Code erstellen.</span><span class="sxs-lookup"><span data-stu-id="1de77-222">A content link for a place that you create in your code.</span></span>

<span data-ttu-id="1de77-223">In anderen Situationen ist ein Hyperlink-Textelement in der Regel geeignet.</span><span class="sxs-lookup"><span data-stu-id="1de77-223">For other situations, a Hyperlink text element is usually appropriate.</span></span>

### <a name="contentlink-appearance"></a><span data-ttu-id="1de77-224">ContentLink-Aussehen</span><span class="sxs-lookup"><span data-stu-id="1de77-224">ContentLink appearance</span></span>

<span data-ttu-id="1de77-225">Das Aussehen eines Links zu Inhalten wird durch dessen Vordergrund, Hintergrund und Cursor bestimmt.</span><span class="sxs-lookup"><span data-stu-id="1de77-225">The appearance of a content link is determined by its foreground, background, and cursor.</span></span> <span data-ttu-id="1de77-226">In einem Textblock können Sie die Vordergrund- (von TextElement) und [Hintergrund](/uwp/api/windows.ui.xaml.documents.contentlink.background)-Eigenschaften so festlegen, dass die Standardfarben geändert werden.</span><span class="sxs-lookup"><span data-stu-id="1de77-226">In a text block, you can set the Foreground (from TextElement) and [Background](/uwp/api/windows.ui.xaml.documents.contentlink.background) properties to change the default colors.</span></span>

<span data-ttu-id="1de77-227">Der [Hand](/uwp/api/windows.ui.core.corecursortype)-Cursor wird standardmäßig angezeigt, wenn der Benutzer mit der Maus auf den Link zu Inhalten zeigt.</span><span class="sxs-lookup"><span data-stu-id="1de77-227">By default, the [Hand](/uwp/api/windows.ui.core.corecursortype) cursor is shown when the user hovers over the content link.</span></span> <span data-ttu-id="1de77-228">Im Gegensatz zum RichEditBlock ändern TextBlock-Steuerelemente den Cursor nicht automatisch basierend auf den Linktyp.</span><span class="sxs-lookup"><span data-stu-id="1de77-228">Unlike RichEditBlock, text block controls don't change the cursor automatically based on the link type.</span></span> <span data-ttu-id="1de77-229">Sie können die [Cursor](/uwp/api/windows.ui.xaml.documents.contentlink.Cursor)-Eigenschaft so festlegen, dass der Cursor basierend auf dem Linktyp oder anderen Faktoren geändert wird.</span><span class="sxs-lookup"><span data-stu-id="1de77-229">You can set the [Cursor](/uwp/api/windows.ui.xaml.documents.contentlink.Cursor) property to change the cursor based on link type or other factors.</span></span>

<span data-ttu-id="1de77-230">Im Folgenden finden Sie ein Beispiel für einen ContentLink, der in einem TextBlock verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="1de77-230">Here's an example of a ContentLink used in a TextBlock.</span></span> <span data-ttu-id="1de77-231">Die ContentLinkInfo wird im Code erstellt und der Info-Eigenschaft des ContentLink-Textelements zugewiesen, das in XAML erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="1de77-231">The ContentLinkInfo is created in code and assigned to the Info property of the ContentLink text element that's created in XAML.</span></span>

```xaml
<StackPanel>
    <TextBlock>
        <Span xml:space="preserve">
            <Run>This valcano erupted in 1980: </Run><ContentLink x:Name="placeContentLink" Cursor="Pin"/>
            <LineBreak/>
        </Span>
    </TextBlock>

    <Button Content="Show" Click="Button_Click"/>
</StackPanel>
```

```csharp
private void Button_Click(object sender, RoutedEventArgs e)
{
    var info = new Windows.UI.Text.ContentLinkInfo();
    info.DisplayText = "Mount St. Helens";
    info.SecondaryText = "Washington State";
    info.LinkContentKind = "Places";
    info.Uri = new Uri("https://maps.windows.com?cp=46.1912~-122.1944");
    placeContentLink.Info = info;
}
```

> [!TIP]
> <span data-ttu-id="1de77-232">Wenn Sie einen ContentLink in einem Textsteuerelement mit anderen Textelementen in XAML verwenden, platzieren Sie den Inhalt in einem [Span](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.documents.span.aspx)-Container und wenden das Attribut `xml:space="preserve"` auf den Span-Container an, um die Leerstelle zwischen dem ContentLink und anderen Elementen beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="1de77-232">When you use a ContentLink in a text control with other text elements in XAML, place the content in a [Span](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.documents.span.aspx) container and apply the `xml:space="preserve"` attribute to the Span to keep the white space between the ContentLink and other elements.</span></span>

## <a name="examples"></a><span data-ttu-id="1de77-233">Beispiele</span><span class="sxs-lookup"><span data-stu-id="1de77-233">Examples</span></span>

<span data-ttu-id="1de77-234">In diesem Beispiel kann ein Benutzer einen Link zu Inhalten für eine Person oder einen Ort eingeben oder in einem RickTextBlock platzieren.</span><span class="sxs-lookup"><span data-stu-id="1de77-234">In this example, a user can enter a person or place content link into a RickTextBlock.</span></span> <span data-ttu-id="1de77-235">Sie verarbeiten das ContentLinkChanged-Ereignis, um die Links zu Inhalten zu extrahieren und sie in einer Personen- oder Ortsliste auf dem neuesten Stand zu halten.</span><span class="sxs-lookup"><span data-stu-id="1de77-235">You handle the ContentLinkChanged event to extract the content links and keep them up-to-date in either a people list or places list.</span></span>

<span data-ttu-id="1de77-236">In der Elementvorlagen für die Listen können Sie einen TextBlock mit einem ContentLink-Textelement verwenden, um die Informationen zum Link zu Inhalten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="1de77-236">In the item templates for the lists, you use a TextBlock with a ContentLink text element to show the content link info.</span></span> <span data-ttu-id="1de77-237">Die ListView stellt ihren eigenen Hintergrund für jedes Element bereit, sodass der ContentLink-Hintergrund auf transparent gesetzt wird.</span><span class="sxs-lookup"><span data-stu-id="1de77-237">The ListView provides its own background for each item, so the ContentLink background is set to Transparent.</span></span>

```xaml
<StackPanel Orientation="Horizontal" Grid.Row="1">
    <RichEditBox x:Name="Editor"
                 ContentLinkChanged="Editor_ContentLinkChanged"
                 Margin="20" Width="300" Height="200"
                 VerticalAlignment="Top">
        <RichEditBox.ContentLinkProviders>
            <ContentLinkProviderCollection>
                <ContactContentLinkProvider/>
                <PlaceContentLinkProvider/>
            </ContentLinkProviderCollection>
        </RichEditBox.ContentLinkProviders>
    </RichEditBox>

    <ListView x:Name="PeopleList" Header="People">
        <ListView.ItemTemplate>
            <DataTemplate x:DataType="ContentLinkInfo">
                <TextBlock>
                    <ContentLink Info="{x:Bind}"
                                 Background="Transparent"
                                 Cursor="Person"/>
                </TextBlock>
            </DataTemplate>
        </ListView.ItemTemplate>
    </ListView>

    <ListView x:Name="PlacesList" Header="Places">
        <ListView.ItemTemplate>
            <DataTemplate x:DataType="ContentLinkInfo">
                <TextBlock>
                    <ContentLink Info="{x:Bind}"
                                 Background="Transparent"
                                 Cursor="Pin"/>
                </TextBlock>
            </DataTemplate>
        </ListView.ItemTemplate>
    </ListView>
</StackPanel>
```

```csharp
private void Editor_ContentLinkChanged(RichEditBox sender, ContentLinkChangedEventArgs args)
{
    var info = args.ContentLinkInfo;
    var change = args.ChangeKind;
    ListViewBase list = null;

    // Determine whether to update the people or places list.
    if (info.LinkContentKind == "People")
    {
        list = PeopleList;
    }
    else if (info.LinkContentKind == "Places")
    {
        list = PlacesList;
    }

    // Determine whether to add, delete, or edit.
    if (change == ContentLinkChangeKind.Inserted)
    {
        Add();
    }
    else if (args.ChangeKind == ContentLinkChangeKind.Removed)
    {
        Remove();
    }
    else if (change == ContentLinkChangeKind.Edited)
    {
        Remove();
        Add();
    }

    // Add content link info to the list. It's bound to the
    // Info property of a ContentLink in XAML.
    void Add()
    {
        list.Items.Add(info);
    }

    // Use ContentLinkInfo.Id to find the item,
    // then remove it from the list using its index.
    void Remove()
    {
        var items = list.Items.Where(i => ((ContentLinkInfo)i).Id == info.Id);
        var item = items.FirstOrDefault();
        var idx = list.Items.IndexOf(item);

        list.Items.RemoveAt(idx);
    }
}
```
