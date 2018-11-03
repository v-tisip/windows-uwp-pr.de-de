---
author: Xansky
Description: Describes the requirements for declaring your Universal Windows Platform (UWP) app as accessible in the Microsoft Store.
ms.assetid: 59FA3B87-75A6-4B30-BA7C-A0E769D68050
title: Barrierefreiheit im Store
label: Accessibility in the Store
template: detail.hbs
ms.author: mhopkins
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 990af773c600c2c87cfe6bc477ed1d6799379fb2
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5988547"
---
# <a name="accessibility-in-the-store"></a><span data-ttu-id="4a7b0-103">Barrierefreiheit im Store</span><span class="sxs-lookup"><span data-stu-id="4a7b0-103">Accessibility in the Store</span></span>  



<span data-ttu-id="4a7b0-104">Hier werden die Anforderungen beschrieben, die Sie erfüllen müssen, wenn Sie Ihre App für die Universelle Windows-Plattform (UWP) im Microsoft Store als barrierefrei deklarieren möchten.</span><span class="sxs-lookup"><span data-stu-id="4a7b0-104">Describes the requirements for declaring your Universal Windows Platform (UWP) app as accessible in the Microsoft Store.</span></span>

<span data-ttu-id="4a7b0-105">Während Sie Ihre App zur Zertifizierung an den Microsoft Store übermitteln, können Sie sie als barrierefrei deklarieren.</span><span class="sxs-lookup"><span data-stu-id="4a7b0-105">While submitting your app to the Microsoft Store for certification, you can declare your app as accessible.</span></span> <span data-ttu-id="4a7b0-106">Indem Sie Ihre App als barrierefrei deklarieren, kann sie von Benutzern, die an barrierefreien Apps interessiert sind (z.B. Benutzer mit Sehschwächen), leichter gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="4a7b0-106">Declaring your app as accessible makes it easier to discover for users who are interested in accessible apps, such as users who have visual impairments.</span></span> <span data-ttu-id="4a7b0-107">Benutzer entdecken barrierefreie Apps, indem sie beim Durchsuchen des Microsoft Store den Filter **Barrierefrei** verwenden.</span><span class="sxs-lookup"><span data-stu-id="4a7b0-107">Users discover accessible apps by using the **Accessible** filter while searching the Microsoft Store.</span></span> <span data-ttu-id="4a7b0-108">Wenn Sie Ihre App als barrierefrei deklarieren, wird der Beschreibung Ihrer App auch das Kennzeichen **Barrierefrei** hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="4a7b0-108">Declaring your app as accessible also adds the **Accessible** tag to your app’s description.</span></span>

<span data-ttu-id="4a7b0-109">Indem Sie Ihre App als barrierefrei deklarieren, erklären Sie, dass sie über die [grundlegenden Informationen zur Barrierefreiheit](basic-accessibility-information.md) verfügt, die Benutzer für wichtige Szenarien unter Verwendung einer oder mehrerer der folgenden Dinge benötigen:</span><span class="sxs-lookup"><span data-stu-id="4a7b0-109">By declaring your app as accessible, you state that it has the [basic accessibility information](basic-accessibility-information.md) that users need for primary scenarios using one or more of the following:</span></span>

* <span data-ttu-id="4a7b0-110">Die Tastatur.</span><span class="sxs-lookup"><span data-stu-id="4a7b0-110">The keyboard.</span></span>
* <span data-ttu-id="4a7b0-111">Ein Design mit hohem Kontrast.</span><span class="sxs-lookup"><span data-stu-id="4a7b0-111">A high contrast theme.</span></span>
* <span data-ttu-id="4a7b0-112">Eine variable dpi-Einstellung (dots per inch).</span><span class="sxs-lookup"><span data-stu-id="4a7b0-112">A variable dots per inch (dpi) setting.</span></span>
* <span data-ttu-id="4a7b0-113">Allgemeine Hilfstechnologien wie z.B. die Windows-Eingabehilfefunktionen, darunter Sprachausgabe, Bildschirmlupe und Bildschirmtastatur.</span><span class="sxs-lookup"><span data-stu-id="4a7b0-113">Common assistive technology such as the Windows accessibility features, including Narrator, Magnifier, and On-Screen Keyboard.</span></span>

<span data-ttu-id="4a7b0-114">Sie sollten Ihre App als barrierefrei erklären, wenn Sie diese unter Berücksichtigung der Barrierefreiheit erstellt und getestet haben.</span><span class="sxs-lookup"><span data-stu-id="4a7b0-114">You should declare your app as accessible if you built and tested it for accessibility.</span></span> <span data-ttu-id="4a7b0-115">Dafür müssen Sie Folgendes gemacht haben:</span><span class="sxs-lookup"><span data-stu-id="4a7b0-115">This means that you did the following:</span></span>

* <span data-ttu-id="4a7b0-116">Alle relevanten Barrierefreiheitsinfos für UI-Elemente sind festgelegt, einschließlich Name, Rolle, Wert usw.</span><span class="sxs-lookup"><span data-stu-id="4a7b0-116">Set all the relevant accessibility information for UI elements, including name, role, value, and so on.</span></span>
* <span data-ttu-id="4a7b0-117">Barrierefreiheit für den Tastaturzugriff implementieren. Benutzer haben so folgende Möglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="4a7b0-117">Implemented full keyboard accessibility, enabling the user to:</span></span>
    * <span data-ttu-id="4a7b0-118">Sämtliche wichtigen App-Szenarien nur mithilfe der Tastatur auszuführen.</span><span class="sxs-lookup"><span data-stu-id="4a7b0-118">Accomplish primary app scenarios by using only the keyboard.</span></span>
    * <span data-ttu-id="4a7b0-119">UI-Elemente in einer logischen Reihenfolge durchzugehen.</span><span class="sxs-lookup"><span data-stu-id="4a7b0-119">Tab among UI elements in a logical order.</span></span>
    * <span data-ttu-id="4a7b0-120">Mithilfe der Pfeiltasten zwischen den UI-Elementen eines Steuerelements zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="4a7b0-120">Navigate among UI elements within a control by using the arrow keys.</span></span>
    * <span data-ttu-id="4a7b0-121">Tastenkombinationen für wichtige Funktionen der App zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="4a7b0-121">Use keyboard shortcuts to reach primary app functionality.</span></span>
    * <span data-ttu-id="4a7b0-122">Verwenden von Sprachausgabe-Touchgesten für TAB- und Pfeilnavigation für Geräte ohne Tastatur.</span><span class="sxs-lookup"><span data-stu-id="4a7b0-122">Use Narrator touch gestures for Tab and arrow equivalency for devices with no keyboard.</span></span>
* <span data-ttu-id="4a7b0-123">Visuelle Barrierefreiheit der App-UI sicherstellen: Kontrastverhältnis von mindestens 4.5:1, keine ausschließlich auf Farben basierende Darstellung von Informationen usw.</span><span class="sxs-lookup"><span data-stu-id="4a7b0-123">Ensured that your app UI is visually accessible: has a minimum text contrast ratio of 4.5:1, does not rely on color alone to convey information, and so on.</span></span>
* <span data-ttu-id="4a7b0-124">Tools zum Testen der Barrierefreiheit wurden eingesetzt, z. B. [**Inspect**](https://msdn.microsoft.com/library/windows/desktop/Dd318521) und [**UIAVerify**](https://msdn.microsoft.com/library/windows/desktop/Hh920986), um die Implementierung der Barrierefreiheit zu überprüfen und alle Fehler der Priorität 1 zu beheben, die von diesen Tools gemeldet werden.</span><span class="sxs-lookup"><span data-stu-id="4a7b0-124">Used accessibility testing tools such as [**Inspect**](https://msdn.microsoft.com/library/windows/desktop/Dd318521) and [**UIAVerify**](https://msdn.microsoft.com/library/windows/desktop/Hh920986) to verify your accessibility implementation, and resolved all priority 1 errors reported by such tools.</span></span>
* <span data-ttu-id="4a7b0-125">Die primären Szenarien Ihrer App unter Verwendung von Sprachausgabe, Bildschirmlupe, Bildschirmtastatur, einem Design mit hohem Kontrast und angepassten DPI-Einstellungen wurden überprüft.</span><span class="sxs-lookup"><span data-stu-id="4a7b0-125">Verified your app’s primary scenarios from end to end by using Narrator, Magnifier, On-Screen Keyboard, a high contrast theme, and adjusted dpi settings.</span></span>

<span data-ttu-id="4a7b0-126">Unter [Prüfliste für die Barrierefreiheit](accessibility-checklist.md) werden diese Verfahren erläutert. Zudem finden Sie dort Links zu Ressourcen, die Ihnen beim Durchführen der Verfahren helfen.</span><span class="sxs-lookup"><span data-stu-id="4a7b0-126">See the [Accessibility checklist](accessibility-checklist.md) for a review of these procedures and links to resources that will help you accomplish them.</span></span>

<span id="related_topics"/>

## <a name="related-topics"></a><span data-ttu-id="4a7b0-127">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="4a7b0-127">Related topics</span></span>    
* [<span data-ttu-id="4a7b0-128">Barrierefreiheit</span><span class="sxs-lookup"><span data-stu-id="4a7b0-128">Accessibility</span></span>](accessibility.md) 
