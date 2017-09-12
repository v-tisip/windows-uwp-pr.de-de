---
author: Jwmsft
Description: "Verwenden Sie ein Label, um den Benutzer darauf hinzuweisen, was er in ein benachbartes Steuerelement eingeben soll. Sie können auch eine Gruppe verwandter Steuerelemente beschriften oder in der Nähe davon Anweisungstexte anzeigen."
title: Label
ms.assetid: CFACCCD4-749F-43FB-947E-2591AE673804
label: Labels
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
pm-contact: miguelrb
design-contact: ksulliv
doc-status: Published
ms.openlocfilehash: 2a3f3d6795276df6e3436c5ae6eff42551d03478
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="labels"></a><span data-ttu-id="6010e-105">Label</span><span class="sxs-lookup"><span data-stu-id="6010e-105">Labels</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

<span data-ttu-id="6010e-106">Ein Label ist der Name bzw. Titel eines Steuerelements oder einer Gruppe verwandter Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="6010e-106">A label is the name or title of a control or a group of related controls.</span></span>

> <span data-ttu-id="6010e-107">**Wichtige APIs**: Header-Eigenschaft, [TextBlock-Klasse](https://msdn.microsoft.com/library/windows/apps/br209652)</span><span class="sxs-lookup"><span data-stu-id="6010e-107">**Important APIs**: Header property, [TextBlock class](https://msdn.microsoft.com/library/windows/apps/br209652)</span></span>

<span data-ttu-id="6010e-108">In XAML verfügen zahlreiche Steuerelemente über eine integrierte Header-Eigenschaft, die Sie zum Anzeigen der Beschriftung verwenden.</span><span class="sxs-lookup"><span data-stu-id="6010e-108">In XAML, many controls have a built-in Header property that you use to display the label.</span></span> <span data-ttu-id="6010e-109">Für Steuerelemente ohne Header-Eigenschaft oder zum Beschriften von Steuerelementgruppen können Sie stattdessen ein [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652)-Element verwenden.</span><span class="sxs-lookup"><span data-stu-id="6010e-109">For controls that don't have a Header property, or to label groups of controls, you can use a [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652) instead.</span></span>

![Bildschirmfoto mit einem standardmäßigen Beschriftungssteuerelement](images/label-standard.png)

## <a name="recommendations"></a><span data-ttu-id="6010e-111">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="6010e-111">Recommendations</span></span>


-   <span data-ttu-id="6010e-112">Verwenden Sie eine Beschriftung, um den Benutzer darauf hinzuweisen, was er in ein benachbartes Steuerelement eingeben soll.</span><span class="sxs-lookup"><span data-stu-id="6010e-112">Use a label to indicate to the user what they should enter into an adjacent control.</span></span> <span data-ttu-id="6010e-113">Sie können auch eine Gruppe verwandter Steuerelemente beschriften oder in der Nähe davon Anweisungstexte anzeigen.</span><span class="sxs-lookup"><span data-stu-id="6010e-113">You can also label a group of related controls, or display instructional text near a group of related controls.</span></span>
-   <span data-ttu-id="6010e-114">Wenn Sie Steuerelemente beschriften, formulieren Sie die Beschriftung als Substantiv oder als präzisen substantivierten Ausdruck und nicht als Satz oder Anweisungstext.</span><span class="sxs-lookup"><span data-stu-id="6010e-114">When labeling controls, write the label as a noun or a concise noun phrase, not as a sentence, and not as instructional text.</span></span> <span data-ttu-id="6010e-115">Vermeiden Sie die Verwendung von Doppelpunkten oder anderen Satzzeichen.</span><span class="sxs-lookup"><span data-stu-id="6010e-115">Avoid colons or other punctuation.</span></span>
-   <span data-ttu-id="6010e-116">Wenn Sie in einer Bezeichnung Anweisungstext nutzen, können Sie bei der Länge von Textzeichenfolgen großzügiger sein und auch Satzzeichen verwenden.</span><span class="sxs-lookup"><span data-stu-id="6010e-116">When you do have instructional text in a label, you can be more generous with text-string length and also use punctuation.</span></span>


## <a name="get-the-sample-code"></a><span data-ttu-id="6010e-117">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="6010e-117">Get the sample code</span></span>
* [<span data-ttu-id="6010e-118">Beispiel für XAML-UI-Grundlagen</span><span class="sxs-lookup"><span data-stu-id="6010e-118">XAML UI basics sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/XamlUIBasics)

## <a name="related-topics"></a><span data-ttu-id="6010e-119">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="6010e-119">Related topics</span></span>
* [<span data-ttu-id="6010e-120">Textsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="6010e-120">Text controls</span></span>](text-controls.md)
* [<span data-ttu-id="6010e-121">TextBox.Header-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="6010e-121">TextBox.Header property</span></span>](https://msdn.microsoft.com/library/windows/apps/dn252861)
* [<span data-ttu-id="6010e-122">Eigenschaft „PasswordBox.Header“</span><span class="sxs-lookup"><span data-stu-id="6010e-122">PasswordBox.Header property</span></span>](https://msdn.microsoft.com/library/windows/apps/dn299051)
* [<span data-ttu-id="6010e-123">Eigenschaft „ToggleSwitch.Header“</span><span class="sxs-lookup"><span data-stu-id="6010e-123">ToggleSwitch.Header property</span></span>](https://msdn.microsoft.com/library/windows/apps/br209713)
* [<span data-ttu-id="6010e-124">Eigenschaft „DatePicker.Header“</span><span class="sxs-lookup"><span data-stu-id="6010e-124">DatePicker.Header property</span></span>](https://msdn.microsoft.com/library/windows/apps/dn279460)
* [<span data-ttu-id="6010e-125">Eigenschaft „TimePicker.Header“</span><span class="sxs-lookup"><span data-stu-id="6010e-125">TimePicker.Header property</span></span>](https://msdn.microsoft.com/library/windows/apps/dn299286)
* [<span data-ttu-id="6010e-126">Eigenschaft „Slider.Header“</span><span class="sxs-lookup"><span data-stu-id="6010e-126">Slider.Header property</span></span>](https://msdn.microsoft.com/library/windows/apps/dn252829)
* [<span data-ttu-id="6010e-127">Eigenschaft „ComboBox.Header“</span><span class="sxs-lookup"><span data-stu-id="6010e-127">ComboBox.Header property</span></span>](https://msdn.microsoft.com/library/windows/apps/dn279416)
* [<span data-ttu-id="6010e-128">Eigenschaft „RichEditBox.Header“</span><span class="sxs-lookup"><span data-stu-id="6010e-128">RichEditBox.Header property</span></span>](https://msdn.microsoft.com/library/windows/apps/dn252726)
* [<span data-ttu-id="6010e-129">Klasse „TextBlock“</span><span class="sxs-lookup"><span data-stu-id="6010e-129">TextBlock class</span></span>](https://msdn.microsoft.com/library/windows/apps/br209652)

 

 




