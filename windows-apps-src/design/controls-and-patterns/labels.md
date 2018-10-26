---
author: Jwmsft
Description: Use a label to indicate to the user what they should enter into an adjacent control. You can also label a group of related controls, or display instructional text near a group of related controls.
title: Label
ms.assetid: CFACCCD4-749F-43FB-947E-2591AE673804
label: Labels
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
keywords: Windows 10, UWP
pm-contact: miguelrb
design-contact: ksulliv
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: c17b2a539a01572bed984b86f72f5439896fac87
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5571603"
---
# <a name="labels"></a><span data-ttu-id="73855-103">Label</span><span class="sxs-lookup"><span data-stu-id="73855-103">Labels</span></span>

 

<span data-ttu-id="73855-104">Ein Label ist der Name bzw. Titel eines Steuerelements oder einer Gruppe verwandter Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="73855-104">A label is the name or title of a control or a group of related controls.</span></span>

> <span data-ttu-id="73855-105">**Wichtige APIs**: Header-Eigenschaft, [TextBlock-Klasse](https://msdn.microsoft.com/library/windows/apps/br209652)</span><span class="sxs-lookup"><span data-stu-id="73855-105">**Important APIs**: Header property, [TextBlock class](https://msdn.microsoft.com/library/windows/apps/br209652)</span></span>

<span data-ttu-id="73855-106">In XAML verfügen zahlreiche Steuerelemente über eine integrierte Header-Eigenschaft, die Sie zum Anzeigen der Beschriftung verwenden.</span><span class="sxs-lookup"><span data-stu-id="73855-106">In XAML, many controls have a built-in Header property that you use to display the label.</span></span> <span data-ttu-id="73855-107">Für Steuerelemente ohne Header-Eigenschaft oder zum Beschriften von Steuerelementgruppen können Sie stattdessen ein [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652)-Element verwenden.</span><span class="sxs-lookup"><span data-stu-id="73855-107">For controls that don't have a Header property, or to label groups of controls, you can use a [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652) instead.</span></span>

![Bildschirmfoto mit einem standardmäßigen Beschriftungssteuerelement](images/label-standard.png)

## <a name="recommendations"></a><span data-ttu-id="73855-109">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="73855-109">Recommendations</span></span>


-   <span data-ttu-id="73855-110">Verwenden Sie eine Beschriftung, um den Benutzer darauf hinzuweisen, was er in ein benachbartes Steuerelement eingeben soll.</span><span class="sxs-lookup"><span data-stu-id="73855-110">Use a label to indicate to the user what they should enter into an adjacent control.</span></span> <span data-ttu-id="73855-111">Sie können auch eine Gruppe verwandter Steuerelemente beschriften oder in der Nähe davon Anweisungstexte anzeigen.</span><span class="sxs-lookup"><span data-stu-id="73855-111">You can also label a group of related controls, or display instructional text near a group of related controls.</span></span>
-   <span data-ttu-id="73855-112">Wenn Sie Steuerelemente beschriften, formulieren Sie die Beschriftung als Substantiv oder als präzisen substantivierten Ausdruck und nicht als Satz oder Anweisungstext.</span><span class="sxs-lookup"><span data-stu-id="73855-112">When labeling controls, write the label as a noun or a concise noun phrase, not as a sentence, and not as instructional text.</span></span> <span data-ttu-id="73855-113">Vermeiden Sie die Verwendung von Doppelpunkten oder anderen Satzzeichen.</span><span class="sxs-lookup"><span data-stu-id="73855-113">Avoid colons or other punctuation.</span></span>
-   <span data-ttu-id="73855-114">Wenn Sie in einer Bezeichnung Anweisungstext nutzen, können Sie bei der Länge von Textzeichenfolgen großzügiger sein und auch Satzzeichen verwenden.</span><span class="sxs-lookup"><span data-stu-id="73855-114">When you do have instructional text in a label, you can be more generous with text-string length and also use punctuation.</span></span>


## <a name="get-the-sample-code"></a><span data-ttu-id="73855-115">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="73855-115">Get the sample code</span></span>
* [<span data-ttu-id="73855-116">Beispiel für XAML-UI-Grundlagen</span><span class="sxs-lookup"><span data-stu-id="73855-116">XAML UI basics sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/XamlUIBasics)

## <a name="related-topics"></a><span data-ttu-id="73855-117">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="73855-117">Related topics</span></span>
* [<span data-ttu-id="73855-118">Textsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="73855-118">Text controls</span></span>](text-controls.md)
* [<span data-ttu-id="73855-119">TextBox.Header-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="73855-119">TextBox.Header property</span></span>](https://msdn.microsoft.com/library/windows/apps/dn252861)
* [<span data-ttu-id="73855-120">Eigenschaft „PasswordBox.Header“</span><span class="sxs-lookup"><span data-stu-id="73855-120">PasswordBox.Header property</span></span>](https://msdn.microsoft.com/library/windows/apps/dn299051)
* [<span data-ttu-id="73855-121">Eigenschaft „ToggleSwitch.Header“</span><span class="sxs-lookup"><span data-stu-id="73855-121">ToggleSwitch.Header property</span></span>](https://msdn.microsoft.com/library/windows/apps/br209713)
* [<span data-ttu-id="73855-122">Eigenschaft „DatePicker.Header“</span><span class="sxs-lookup"><span data-stu-id="73855-122">DatePicker.Header property</span></span>](https://msdn.microsoft.com/library/windows/apps/dn279460)
* [<span data-ttu-id="73855-123">Eigenschaft „TimePicker.Header“</span><span class="sxs-lookup"><span data-stu-id="73855-123">TimePicker.Header property</span></span>](https://msdn.microsoft.com/library/windows/apps/dn299286)
* [<span data-ttu-id="73855-124">Eigenschaft „Slider.Header“</span><span class="sxs-lookup"><span data-stu-id="73855-124">Slider.Header property</span></span>](https://msdn.microsoft.com/library/windows/apps/dn252829)
* [<span data-ttu-id="73855-125">Eigenschaft „ComboBox.Header“</span><span class="sxs-lookup"><span data-stu-id="73855-125">ComboBox.Header property</span></span>](https://msdn.microsoft.com/library/windows/apps/dn279416)
* [<span data-ttu-id="73855-126">Eigenschaft „RichEditBox.Header“</span><span class="sxs-lookup"><span data-stu-id="73855-126">RichEditBox.Header property</span></span>](https://msdn.microsoft.com/library/windows/apps/dn252726)
* [<span data-ttu-id="73855-127">Klasse „TextBlock“</span><span class="sxs-lookup"><span data-stu-id="73855-127">TextBlock class</span></span>](https://msdn.microsoft.com/library/windows/apps/br209652)

 

 




