---
author: normesta
description: Diese Anleitung hilft Ihnen, Fluent-basierte UWP-UIs direkt in einer WPF- oder Windows Forms-Anwendung zu erstellen.
title: Hosten von UWP-Steuerelementen in WPF- und Windows Forms-Anwendungen
ms.author: normesta
ms.date: 05/03/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp, windows forms, wpf
keywords: Windows 10, UWP, Windows Forms, WPF
ms.localizationpriority: medium
ms.openlocfilehash: 4823654bce3373ace5b04ced8ec14c4b6c1b6f1d
ms.sourcegitcommit: 3500825bc2e5698394a8b1d2efece7f071f296c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2018
ms.locfileid: "1862069"
---
# <a name="host-uwp-controls-in-wpf-and-windows-forms-applications"></a><span data-ttu-id="0ea69-104">Hosten von UWP-Steuerelementen in WPF- und Windows Forms-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="0ea69-104">Host UWP controls in WPF and Windows Forms applications</span></span>

> [!NOTE]
> <span data-ttu-id="0ea69-105">Einige Informationen beziehen sich auf die Vorabversion, die vor der kommerziellen Freigabe möglicherweise wesentlichen Änderungen unterliegt.</span><span class="sxs-lookup"><span data-stu-id="0ea69-105">Some information relates to pre-released product which may be substantially modified before it’s commercially released.</span></span> <span data-ttu-id="0ea69-106">Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.</span><span class="sxs-lookup"><span data-stu-id="0ea69-106">Microsoft makes no warranties, express or implied, with respect to the information provided here.</span></span>

<span data-ttu-id="0ea69-107">Wir bringen UWP-Steuerelemente auf den Desktop, damit Sie das Aussehen, Verhalten und die Funktionalität Ihrer vorhandenen WPF- oder Windows-Anwendungen mit Fluent Design-Features verbessern können.</span><span class="sxs-lookup"><span data-stu-id="0ea69-107">We're bringing UWP controls to the desktop so that you can enhance the look, feel, and functionality of your existing WPF or Windows applications with Fluent Design features.</span></span> <span data-ttu-id="0ea69-108">Dazu gibt es zwei Möglichkeiten.</span><span class="sxs-lookup"><span data-stu-id="0ea69-108">There's two ways to do this.</span></span>

<span data-ttu-id="0ea69-109">Zunächst können Sie der Entwurfsoberfläche Ihres WPF- oder Windows Forms-Projekts Steuerelemente direkt hinzufügen und sie dann wie jedes andere Steuerelement im Designer verwenden.</span><span class="sxs-lookup"><span data-stu-id="0ea69-109">First, you can add controls directly to the design surface of your WPF or Windows Forms project, and then use them like any other control in your designer.</span></span>  <span data-ttu-id="0ea69-110">Testen Sie das mit dem neuen **WebView**-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="0ea69-110">Try this out today with the new **WebView** control.</span></span> <span data-ttu-id="0ea69-111">Dieses Steuerelement, das bisher nur für UWP-Anwendungen verfügbar war, verwendet das Renderingmodul aus Microsoft Edge.</span><span class="sxs-lookup"><span data-stu-id="0ea69-111">This control uses the Microsoft Edge rendering engine, and until now, this control was available only to UWP applications.</span></span> <span data-ttu-id="0ea69-112">Sie finden **WebView** im aktuellen [Windows-Community Toolkit](https://docs.microsoft.com/windows/uwpcommunitytoolkit/).</span><span class="sxs-lookup"><span data-stu-id="0ea69-112">You can find the **WebView** in the latest release of the [Windows Community Toolkit](https://docs.microsoft.com/windows/uwpcommunitytoolkit/).</span></span>

<span data-ttu-id="0ea69-113">Bald haben Sie auch Zugriff auf andere Fluent Design-Features, denn wir werden ein Steuerelement bereitstellen, mit dem Sie eine Vielzahl von UWP-Steuerelementen hosten können.</span><span class="sxs-lookup"><span data-stu-id="0ea69-113">Soon, you'll have access to even more Fluent Design features: we'll be providing a control that lets you host a variety of UWP controls.</span></span> <span data-ttu-id="0ea69-114">Sie werden dieses und viele weitere Steuerelemente demnächst im Windows Community Toolkit finden.</span><span class="sxs-lookup"><span data-stu-id="0ea69-114">Look for this control and many other controls in future releases of the Windows Community Toolkit.</span></span>

<span data-ttu-id="0ea69-115">Nachfolgend ist dargestellt, wie diese Steuerelemente architektonisch organisiert sind.</span><span class="sxs-lookup"><span data-stu-id="0ea69-115">Here's a quick look at how these controls are organized architecturally.</span></span> <span data-ttu-id="0ea69-116">Die in diesem Diagramm verwendeten Namen werden möglicherweise noch geändert.</span><span class="sxs-lookup"><span data-stu-id="0ea69-116">The names used in this diagram are subject to change.</span></span>  

![Hoststeuerelement-Architektur](images/host-controls.png)

<span data-ttu-id="0ea69-118">Die am Diagrammende aufgeführten APIs sind im Lieferumfang des Windows SDK enthalten.</span><span class="sxs-lookup"><span data-stu-id="0ea69-118">The APIs that appear at the bottom of this diagram ship with the Windows SDK.</span></span>  <span data-ttu-id="0ea69-119">Die Steuerelemente für den Designer sind als Nuget-Pakete im Windows Community Toolkit geliefert enthalten.</span><span class="sxs-lookup"><span data-stu-id="0ea69-119">The controls that you'll add to your designer ship as Nuget packages in the Windows Community Toolkit.</span></span>

<span data-ttu-id="0ea69-120">Diese neuen Steuerelemente haben noch Einschränkungen. Bevor Sie die Steuerelemente verwenden, sollten Sie sich einen Moment Zeit nehmen und lesen, was noch nicht unterstützt wird oder nur mit Problemumgehungen funktioniert.</span><span class="sxs-lookup"><span data-stu-id="0ea69-120">These new controls have limitations so before you use them, please take a moment to review what's not yet supported, and what's functional only with workarounds.</span></span>

### <a name="whats-supported"></a><span data-ttu-id="0ea69-121">Nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="0ea69-121">What's supported</span></span>

<span data-ttu-id="0ea69-122">In den meisten Fällen wird nur die Funktionalität nicht unterstützt, die in der folgenden Liste aufgeführt ist.</span><span class="sxs-lookup"><span data-stu-id="0ea69-122">For the most part, everything is supported unless explicitly called out in the list below.</span></span>

### <a name="whats-supported-only-with-workarounds"></a><span data-ttu-id="0ea69-123">Nur mit Problemumgehungen unterstützt</span><span class="sxs-lookup"><span data-stu-id="0ea69-123">What's supported only with workarounds</span></span>

<span data-ttu-id="0ea69-124">:heavy_check_mark: Hosting mehrerer Inbox-Steuerelemente innerhalb mehrerer Fenster</span><span class="sxs-lookup"><span data-stu-id="0ea69-124">:heavy_check_mark: Hosting multiple inbox controls inside of multiple windows.</span></span> <span data-ttu-id="0ea69-125">Sie müssen jedes Fenster in seinem eigenen Thread platzieren.</span><span class="sxs-lookup"><span data-stu-id="0ea69-125">You'll have to place each window in its own thread.</span></span>

<span data-ttu-id="0ea69-126">:heavy_check_mark: Verwendung von ``x:Bind`` mit gehosteten Steuerelementen</span><span class="sxs-lookup"><span data-stu-id="0ea69-126">:heavy_check_mark: Using ``x:Bind`` with hosted controls.</span></span> <span data-ttu-id="0ea69-127">Sie müssen das Datenmodell in einer .NET Standardbibliothek deklarieren.</span><span class="sxs-lookup"><span data-stu-id="0ea69-127">You'll have to declare the data model in a .NET Standard library.</span></span>

<span data-ttu-id="0ea69-128">:heavy_check_mark: C#-basierte Drittanbieter-Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="0ea69-128">:heavy_check_mark: C#-based third-party controls.</span></span> <span data-ttu-id="0ea69-129">Wenn Sie über den Quellcode eines Drittanbieter-Steuerelements verfügen, können Sie ihn kompilieren.</span><span class="sxs-lookup"><span data-stu-id="0ea69-129">If you have the source code to a third-party control, you can compile against it.</span></span>

### <a name="whats-not-yet-supported"></a><span data-ttu-id="0ea69-130">Noch nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="0ea69-130">What's not yet supported</span></span>

<span data-ttu-id="0ea69-131">:no_entry_sign: Tools mit Bedienungshilfen, die gleichartig für die Anwendung und die gehosteten Steuerelemente funktionieren</span><span class="sxs-lookup"><span data-stu-id="0ea69-131">:no_entry_sign: Accessibility tools that work seamlessly across the application and hosted controls.</span></span>

<span data-ttu-id="0ea69-132">:no_entry_sign: Lokalisierter Inhalt in Steuerelementen für Anwendungen, die kein Windows-App-Paket enthalten</span><span class="sxs-lookup"><span data-stu-id="0ea69-132">:no_entry_sign: Localized content in controls that you add to applications which don't contain a Windows app package.</span></span>

<span data-ttu-id="0ea69-133">:no_entry_sign: Asset-Verweise in XAML innerhalb von Anwendungen, die kein Windows-App-Paket enthalten</span><span class="sxs-lookup"><span data-stu-id="0ea69-133">:no_entry_sign: Asset references made in XAML within applications that don't contain a Windows app package.</span></span>

<span data-ttu-id="0ea69-134">:no_entry_sign: Steuerelemente, die korrekt bezüglich Änderungen von DPI und Skalierung reagieren</span><span class="sxs-lookup"><span data-stu-id="0ea69-134">:no_entry_sign: Controls properly responding to changes in DPI and scale.</span></span>

<span data-ttu-id="0ea69-135">:no_entry_sign: Hinzufügen eines **WebView**-Steuerelements zu einem benutzerdefinierten Steuerelement (entweder „on-thread”, „off-thread” oder „out of proc”)</span><span class="sxs-lookup"><span data-stu-id="0ea69-135">:no_entry_sign: Adding a **WebView** control to a custom user control, (Either on-thread, off-thread, or out of proc).</span></span>

<span data-ttu-id="0ea69-136">:no_entry_sign: Der Fluent-Effekt [Reveal Highlight](https://docs.microsoft.com/windows/uwp/design/style/reveal)</span><span class="sxs-lookup"><span data-stu-id="0ea69-136">:no_entry_sign: The [Reveal highlight](https://docs.microsoft.com/windows/uwp/design/style/reveal) Fluent effect.</span></span>

<span data-ttu-id="0ea69-137">:no_entry_sign: Inline-Freihandeingabe, @Places und @People für Eingabesteuerelemente</span><span class="sxs-lookup"><span data-stu-id="0ea69-137">:no_entry_sign: Inline inking, @Places, and @People for input controls.</span></span>

<span data-ttu-id="0ea69-138">:no_entry_sign: Zuweisen von Zugriffstasten</span><span class="sxs-lookup"><span data-stu-id="0ea69-138">:no_entry_sign: Assigning accelerator keys.</span></span>

<span data-ttu-id="0ea69-139">:no_entry_sign: C++-basierte Steuerelemente von Drittanbietern</span><span class="sxs-lookup"><span data-stu-id="0ea69-139">:no_entry_sign: C++-based third-party controls.</span></span>

<span data-ttu-id="0ea69-140">:no_entry_sign: Hosten benutzerdefinierter Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="0ea69-140">:no_entry_sign: Hosting custom user controls.</span></span>

<span data-ttu-id="0ea69-141">Die Elemente in dieser Liste werden sich wahrscheinlich ändern, da wir ständig daran arbeiten, Fluent auf dem Desktop zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="0ea69-141">The items in this list will likely change as we continue to improve the experience of bringing Fluent to the desktop.</span></span>  
