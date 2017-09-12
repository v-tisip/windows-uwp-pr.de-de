---
description: "Erfahren Sie, wie Sie eine UWP-App entwerfen und kodieren, die eine einfache Navigation besitzt und auf vielen Geräten und Bildschirmen verschiedener Größen großartig aussieht."
title: "Layoutdesign von UWP-Apps – Entwicklung von Windows-Apps"
author: mijacobs
keywords: Layout von UWP-Apps, universelle Windows-Plattform, App-Design, Schnittstelle
label: Layout
template: detail.hbs
ms.author: mijacobs
ms.date: 08/9/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.assetid: 1aa12606-8a99-4db3-8311-90e02fde9cf1
ms.openlocfilehash: 4c1b4617b3b58cb613bcca8d5df456621af730fa
ms.sourcegitcommit: 0d5b3daddb3ae74f91178c58e35cbab33854cb7f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2017
---
# <a name="layout-for-uwp-apps"></a><span data-ttu-id="9fd4e-104">Layout für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="9fd4e-104">Layout for UWP apps</span></span>
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

<span data-ttu-id="9fd4e-105">App-Struktur, Seitenlayout und Navigation bilden die Grundlage der Benutzerumgebung Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="9fd4e-105">App structure, page layout, and navigation are the foundation of your app's user experience.</span></span> <span data-ttu-id="9fd4e-106">Die Artikel in diesem Abschnitt verwenden das Fluent Design System und helfen Ihnen, eine App zu erstellen, in der Benutzer leicht navigieren können und die auf einer Vielzahl von Geräten und Bildschirmgrößen hervorragend aussieht.</span><span class="sxs-lookup"><span data-stu-id="9fd4e-106">The articles in this section use the Fluent Design System to help you create an app that is easy to navigate and looks great on a variety of devices and screen sizes.</span></span>

## <a name="intro"></a><span data-ttu-id="9fd4e-107">Einführung</span><span class="sxs-lookup"><span data-stu-id="9fd4e-107">Intro</span></span>

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
  <p><b>[<span data-ttu-id="9fd4e-108">Einführung in das UI-Design von Apps</span><span class="sxs-lookup"><span data-stu-id="9fd4e-108">Intro to app UI design</span></span>](design-and-ui-intro.md)</b><br />
<span data-ttu-id="9fd4e-109">Der Entwurf einer UWP-App umfasst auch die Erstellung einer Benutzeroberfläche, die für eine Vielzahl von Geräten mit unterschiedlichen Monitorgrößen geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="9fd4e-109">When you design a UWP app, you create a user interface that suits a variety of devices with different display sizes.</span></span> <span data-ttu-id="9fd4e-110">Dieser Artikel enthält eine Einführung in das Fluent Design System und eine Übersicht über UI-bezogene Features und Vorteile von UWP-Apps sowie Tipps und Tricks für das Entwerfen einer reaktionsfähigen Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="9fd4e-110">This article provides an introduction to the Fluent Design System, an overview of UI-related features and benefits of UWP apps and some tips & tricks for designing a responsive UI.</span></span> </p>
  </div>
  <div class="side-by-side-content-right">
    ![Eine App, die auf mehreren Geräten ausgeführt wird](images/rspd-reposition-type1-sm.png)
  </div>
</div>
</div>

## <a name="app-layout-and-structure"></a><span data-ttu-id="9fd4e-112">App-Layout und -Struktur</span><span class="sxs-lookup"><span data-stu-id="9fd4e-112">App layout and structure</span></span>
<span data-ttu-id="9fd4e-113">Sehen Sie sich diese Empfehlungen für das Strukturieren Ihrer App und das Verwenden der drei Arten von UI-Elementen an: Navigation, Befehle und Inhalte.</span><span class="sxs-lookup"><span data-stu-id="9fd4e-113">Check out these recommendations for structuring your app and using the three types of UI elements: navigation, command, and content.</span></span>

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
<p>
<b>[<span data-ttu-id="9fd4e-114">Navigationsgrundlagen</span><span class="sxs-lookup"><span data-stu-id="9fd4e-114">Navigation basics</span></span>](navigation-basics.md)</b><br/>
<span data-ttu-id="9fd4e-115">Die Navigation in UWP-Apps basiert auf einem flexiblen Modell aus Navigationsstrukturen, Navigationselementen und Funktionen auf Systemebene.</span><span class="sxs-lookup"><span data-stu-id="9fd4e-115">Navigation in UWP apps is based on a flexible model of navigation structures, navigation elements, and system-level features.</span></span> <span data-ttu-id="9fd4e-116">Dieser Artikel führt Sie in diese Komponenten ein und zeigt, wie Sie diese gemeinsam verwenden, um eine gute Navigationsumgebung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="9fd4e-116">This article introduces you to these components and shows you how to use them together to create a good navigation experience.</span></span>
</p>
<p>
<b>[<span data-ttu-id="9fd4e-117">Inhaltsgrundlagen</span><span class="sxs-lookup"><span data-stu-id="9fd4e-117">Content basics</span></span>](content-basics.md)</b><br/>
<span data-ttu-id="9fd4e-118">Der Hauptzweck jeder App ist das Bereitstellen von Zugriff auf Content: In einer Fotobearbeitungs-App sind Fotos der Content, in einer Reise-App Karten und Informationen über die Reiseziele usw.</span><span class="sxs-lookup"><span data-stu-id="9fd4e-118">The main purpose of any app is to provide access to content: in a photo-editing app, the photo is the content; in a travel app, maps and info about travel destinations is the content; and so on.</span></span> <span data-ttu-id="9fd4e-119">Dieser Artikel stellt Empfehlungen für das Design von Inhalten für die drei Inhaltsszenarien bereit: Nutzung, Erstellung und Interaktion.</span><span class="sxs-lookup"><span data-stu-id="9fd4e-119">This article provides content design recommendations for the three content scenarios: consumption, creation, and interaction.</span></span>
</p> 
  </div>
  <div class="side-by-side-content-right">
<p><b>[<span data-ttu-id="9fd4e-120">Befehlsgrundlagen</span><span class="sxs-lookup"><span data-stu-id="9fd4e-120">Command basics</span></span>](commanding-basics.md)</b> <br />
<span data-ttu-id="9fd4e-121">Befehlselementen sind die interaktiven UI-Elemente, mit denen der Benutzer Aktionen ausführen kann, um beispielsweise eine E-Mail zu senden, ein Element zu löschen oder ein Formular zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="9fd4e-121">Command elements are the interactive UI elements that enable the user to perform actions, such as sending an email, deleting an item, or submitting a form.</span></span> <span data-ttu-id="9fd4e-122">Dieser Artikel beschreibt Befehlselemente wie Schaltflächen und Kontrollkästchen, die unterstützten Interaktionen sowie die Befehlsoberflächen (wie etwa Befehlsleisten und Kontextmenüs), auf denen sie sich befinden können.</span><span class="sxs-lookup"><span data-stu-id="9fd4e-122">This article describes the command elements, such as buttons and check boxes, the interactions they support, and the command surfaces (such as command bars and context menus) for hosting them.</span></span></p>
  </div>
</div>
</div>

## <a name="page-layout"></a><span data-ttu-id="9fd4e-123">Seitenlayout</span><span class="sxs-lookup"><span data-stu-id="9fd4e-123">Page layout</span></span> 
<span data-ttu-id="9fd4e-124">Diese Artikel unterstützen Sie beim Erstellen einer flexiblen Benutzeroberfläche, die auch bei verschiedenen Bildschirmgrößen, Fenstergrößen, Auflösungen und Ausrichtungen hervorragend aussieht.</span><span class="sxs-lookup"><span data-stu-id="9fd4e-124">These articles help you create a flexible UI that looks great on different screen sizes, window sizes, resolutions, and orientations.</span></span> 

<div style="column-count: 2; column-gap: 40px; margin-top: 40px;">

<div style="-webkit-column-break-inside: avoid; page-break-inside: avoid; break-inside: avoid;">
<p style="margin-top: 0px; padding-top: 0px;"><b>[<span data-ttu-id="9fd4e-125">Bildschirmgrößen und Haltepunkte</span><span class="sxs-lookup"><span data-stu-id="9fd4e-125">Screen sizes and breakpoints</span></span>](screen-sizes-and-breakpoints-for-responsive-design.md)</b><br/>
<span data-ttu-id="9fd4e-126">Die Anzahl der Geräteziele und Bildschirmgrößen bei Windows 10 ist zu groß, um alle beim Optimieren der Benutzeroberfläche zu bedenken.</span><span class="sxs-lookup"><span data-stu-id="9fd4e-126">The number of device targets and screen sizes across the Windows 10 ecosystem is too great to worry about optimizing your UI for each one.</span></span> <span data-ttu-id="9fd4e-127">Stattdessen wird empfohlen, für einige wichtige Bildschirmbreiten (auch als „Haltepunkte“ bezeichnet) zu entwickeln: 360, 640, 1024 und 1366 Epx.</span><span class="sxs-lookup"><span data-stu-id="9fd4e-127">Instead, we recommended designing for a few key widths (also called "breakpoints"): 360, 640, 1024 and 1366 epx.</span></span></p>
</div>

<div style="-webkit-column-break-inside: avoid; page-break-inside: avoid; break-inside: avoid;">
  <p><b>[<span data-ttu-id="9fd4e-128">Definieren von Layouts mit XAML</span><span class="sxs-lookup"><span data-stu-id="9fd4e-128">Define layouts with XAML</span></span>](layouts-with-xaml.md)</b> <br/>
<span data-ttu-id="9fd4e-129">Hier wird gezeigt, wie Sie XAML-Eigenschaften und Layoutpanels verwenden, um eine reaktionsfähige und adaptive App zu entwickeln.</span><span class="sxs-lookup"><span data-stu-id="9fd4e-129">How to use XAML properties and layout panels to make your app responsive and adaptive.</span></span></p>
</div>
<div style="-webkit-column-break-inside: avoid; page-break-inside: avoid; break-inside: avoid;">
   <p><b>[<span data-ttu-id="9fd4e-130">Layoutpanels</span><span class="sxs-lookup"><span data-stu-id="9fd4e-130">Layout panels</span></span>](layout-panels.md)</b> <br />
<span data-ttu-id="9fd4e-131">Erfahren Sie mehr über die einzelnen Arten von Layoutpaneln und wie diese für das Layout von XAML-UI-Elementen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="9fd4e-131">Learn about each type of layout each panel and show how to use them to layout XAML UI elements.</span></span></p> 
</div>
<div style="-webkit-column-break-inside: avoid; page-break-inside: avoid; break-inside: avoid;">
 <p><b>[<span data-ttu-id="9fd4e-132">Ausrichtung, Ränder und Abstand</span><span class="sxs-lookup"><span data-stu-id="9fd4e-132">Alignment, margins, and padding</span></span>](alignment-margin-padding.md)</b> <br />
<span data-ttu-id="9fd4e-133">Neben Abmessungseigenschaften (Breite, Höhe und Beschränkungen) können Elemente auch Ausrichtungs-, Rand- und Abstandseigenschaften aufweisen, die das Layoutverhalten beeinflussen, wenn ein Element einen Layoutdurchlauf ausführt und in einer Benutzeroberfläche dargestellt wird.</span><span class="sxs-lookup"><span data-stu-id="9fd4e-133">In addition to dimension properties (width, height, and constraints) elements can also have alignment, margin, and padding properties that influence the layout behavior when an element goes through a layout pass and is rendered in a UI.</span></span></p> 
</div>
<div style="-webkit-column-break-inside: avoid; page-break-inside: avoid; break-inside: avoid;">
 <p><b>[<span data-ttu-id="9fd4e-134">Erstellen von App-Layouts mit Grid und StackPanel</span><span class="sxs-lookup"><span data-stu-id="9fd4e-134">Create layouts with Grid and StackPanel</span></span>](grid-tutorial.md)</b> <br />
<span data-ttu-id="9fd4e-135">Verwenden Sie zum Erstellen des Layouts für eine einfache Wetter-App mit XAML die Elemente Grid und StackPanel.</span><span class="sxs-lookup"><span data-stu-id="9fd4e-135">Use XAML to create the layout for a simple weather app using the Grid and StackPanel elements.</span></span> </p> 
</div>

</div>



