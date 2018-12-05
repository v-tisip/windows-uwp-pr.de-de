---
Description: Use pop-up animations to show and hide pop-up UI for flyouts or custom pop-up UI elements. Pop-up elements are containers that appear over the app's content and are dismissed if the user taps or clicks outside of the pop-up element.
title: Animationen für Popupbenutzeroberflächen in UWP-Apps
ms.assetid: 4E9025CE-FC90-4d4c-9DE6-EC6B6F2AD9DF
label: Motion--Pop-up animations
template: detail.hbs
ms.date: 05/19/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: d79c369e14236b827bdc18aba6c74349528728b3
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8732885"
---
# <a name="pop-up-ui-animations"></a><span data-ttu-id="db8ab-103">Animationen für Popupbenutzeroberflächen</span><span class="sxs-lookup"><span data-stu-id="db8ab-103">Pop-up UI animations</span></span>



<span data-ttu-id="db8ab-104">Verwenden Sie Popupanimationen, um Popup-UI-Elemente für Flyouts oder benutzerdefinierte Popup-UI-Elemente anzuzeigen und auszublenden.</span><span class="sxs-lookup"><span data-stu-id="db8ab-104">Use pop-up animations to show and hide pop-up UI for flyouts or custom pop-up UI elements.</span></span> <span data-ttu-id="db8ab-105">Popupelemente sind Container, die über dem Inhalt der App angezeigt werden und ausgeblendet werden, wenn Benutzer außerhalb des Popupelements tippen oder klicken.</span><span class="sxs-lookup"><span data-stu-id="db8ab-105">Pop-up elements are containers that appear over the app's content and are dismissed if the user taps or clicks outside of the pop-up element.</span></span>

> <span data-ttu-id="db8ab-106">**Wichtige APIs**: [**PopInThemeAnimation class**](https://msdn.microsoft.com/library/windows/apps/br210383), [**PopupThemeTransition class**](https://msdn.microsoft.com/library/windows/apps/hh969172)</span><span class="sxs-lookup"><span data-stu-id="db8ab-106">**Important APIs**: [**PopInThemeAnimation class**](https://msdn.microsoft.com/library/windows/apps/br210383), [**PopupThemeTransition class**](https://msdn.microsoft.com/library/windows/apps/hh969172)</span></span>


## <a name="dos-and-donts"></a><span data-ttu-id="db8ab-107">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="db8ab-107">Do's and don'ts</span></span>


-   <span data-ttu-id="db8ab-108">Verwenden Sie Popupanimationen zum Anzeigen oder Ausblenden benutzerdefinierter Popup-UI-Elemente, die nicht Teil der eigentlichen App-Seite sind.</span><span class="sxs-lookup"><span data-stu-id="db8ab-108">Use pop-up animations to show or hide custom pop-up UI elements that aren't a part of the app page itself.</span></span> <span data-ttu-id="db8ab-109">In die von Windows bereitgestellten allgemeinen Steuerelemente sind diese Animationen bereits integriert.</span><span class="sxs-lookup"><span data-stu-id="db8ab-109">The common controls provided by Windows already have these animations built in.</span></span>
-   <span data-ttu-id="db8ab-110">Verwenden Sie Popupanimationen nicht für QuickInfos oder Dialogfelder.</span><span class="sxs-lookup"><span data-stu-id="db8ab-110">Don't use pop-up animations for tooltips or dialogs.</span></span>
-   <span data-ttu-id="db8ab-111">Verwenden Sie Popupanimationen nicht zum Anzeigen oder Ausblenden von Benutzeroberflächen innerhalb des Hauptinhalts der App. Verwenden Sie Popupanimationen nur, um einen Popupcontainer anzuzeigen oder auszublenden, der über dem Hauptinhalt der App angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="db8ab-111">Don't use pop-up animations to show or hide UI within the main content of your app; only use pop-up animations to show or hide a pop-up container that displays on top of the main app content.</span></span>

## <a name="related-articles"></a><span data-ttu-id="db8ab-112">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="db8ab-112">Related articles</span></span>

* [<span data-ttu-id="db8ab-113">Übersicht über Animationen</span><span class="sxs-lookup"><span data-stu-id="db8ab-113">Animations overview</span></span>](https://msdn.microsoft.com/library/windows/apps/mt187350)
* [<span data-ttu-id="db8ab-114">Animieren von Popupbenutzeroberflächen</span><span class="sxs-lookup"><span data-stu-id="db8ab-114">Animating pop-up UI</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/jj649433)
* [<span data-ttu-id="db8ab-115">Schnellstart: Animieren der Benutzeroberfläche mithilfe von Bibliotheksanimationen</span><span class="sxs-lookup"><span data-stu-id="db8ab-115">Quickstart: Animating your UI using library animations</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/hh452703)
* [**<span data-ttu-id="db8ab-116">PopInThemeAnimation-Klasse</span><span class="sxs-lookup"><span data-stu-id="db8ab-116">PopInThemeAnimation class</span></span>**](https://msdn.microsoft.com/library/windows/apps/br210383)
* [**<span data-ttu-id="db8ab-117">PopOutThemeAnimation-Klasse</span><span class="sxs-lookup"><span data-stu-id="db8ab-117">PopOutThemeAnimation class</span></span>**](https://msdn.microsoft.com/library/windows/apps/br210391)
* [**<span data-ttu-id="db8ab-118">PopupThemeTransition-Klasse</span><span class="sxs-lookup"><span data-stu-id="db8ab-118">PopupThemeTransition class</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh969172)

 

 




