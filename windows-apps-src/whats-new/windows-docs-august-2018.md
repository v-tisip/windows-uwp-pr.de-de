---
author: QuinnRadich
title: Neuigkeiten in Windows-Dokumentation im August 2018 – Entwicklung von UWP-apps
description: Neue Features, Videos, Beispiele und entwicklerleitfäden wurden in der Windows 10-Entwicklerdokumentation für August 2018 hinzugefügt.
keywords: Neues in, Update, Features, Anleitungen für Entwickler, Windows 10, august
ms.author: quradic
ms.date: 08/14/2018
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 76de6c5c1e8925dd8b166a8d99c39116bf66141d
ms.sourcegitcommit: f2c9a050a9137a473f28b613968d5782866142c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6254749"
---
# <a name="whats-new-in-the-windows-developer-docs-in-august-2018"></a><span data-ttu-id="3eb41-104">Neuigkeiten in der Windows-Entwicklerdokumentation im August 2018</span><span class="sxs-lookup"><span data-stu-id="3eb41-104">What's New in the Windows Developer Docs in August 2018</span></span>

<span data-ttu-id="3eb41-105">Die Entwicklerdokumentation für die Windows-Plattform wird ständig mit Informationen über neue Features für Entwickler aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="3eb41-105">The Windows Developer Documentation is constantly being updated with information on new features available to developers across the Windows platform.</span></span> <span data-ttu-id="3eb41-106">Die folgenden Featureübersichten, entwicklerleitfäden und Videos wurden im Monat August zur Verfügung gestellt.</span><span class="sxs-lookup"><span data-stu-id="3eb41-106">The following feature overviews, developer guidance, and videos have been made available in the month of August.</span></span>

<span data-ttu-id="3eb41-107">Nach der [Installation der Tools und des SDKs](http://go.microsoft.com/fwlink/?LinkId=821431) unter Windows10 können Sie entweder [eine neue universelle Windows-App erstellen](../get-started/create-uwp-apps.md) oder sich mit der Verwendung von [vorhandenem App-Code unter Windows](../porting/index.md) vertraut machen.</span><span class="sxs-lookup"><span data-stu-id="3eb41-107">[Install the tools and SDK](http://go.microsoft.com/fwlink/?LinkId=821431) on Windows 10 and you’re ready to either [create a new Universal Windows app](../get-started/create-uwp-apps.md) or explore how you can use your [existing app code on Windows](../porting/index.md).</span></span>

## <a name="features"></a><span data-ttu-id="3eb41-108">Features</span><span class="sxs-lookup"><span data-stu-id="3eb41-108">Features</span></span>

### <a name="design"></a><span data-ttu-id="3eb41-109">Entwerfen</span><span class="sxs-lookup"><span data-stu-id="3eb41-109">Design</span></span>

<span data-ttu-id="3eb41-110">Die folgenden Features wurde der Windows Insider Preview-Builds, über das [Windows-Insider-](https://insider.windows.com/) Programm verfügbar hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="3eb41-110">The following features have been added to the Windows Insider Preview builds, available through the [Windows Insider](https://insider.windows.com/) program.</span></span>

* <span data-ttu-id="3eb41-111">Der [Windows-UI-Bibliothek](https://aka.ms/winui-docs) ist ein Satz von NuGet-Pakete, die Steuerelemente und andere Elemente einer interfact für UWP-apps bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="3eb41-111">The [Windows UI Library](https://aka.ms/winui-docs) is a set of NuGet packages that provide controls and other user interfact elements for UWP apps.</span></span> <span data-ttu-id="3eb41-112">Diese Pakete sind auch kompatibel mit früheren Versionen von Windows 10, damit Ihre app funktioniert, selbst wenn Ihre Benutzer nicht die neueste Version des Betriebssystems ist.</span><span class="sxs-lookup"><span data-stu-id="3eb41-112">These packages are also compatable with earlier versions of Windows 10, so your app works even if your users don't have the latest OS version.</span></span>

* <span data-ttu-id="3eb41-113">[DropDownButton](../design/controls-and-patterns/buttons.md#create-a-drop-down-button) [SplitButton](../design/controls-and-patterns/buttons.md#create-a-split-button)und [ToggleSplitButton](../design/controls-and-patterns/buttons.md#create-a-toggle-split-button) bieten Schaltflächensteuerelementen mit speziellen Features zur Verbesserung der Benutzeroberfläche Ihrer app.</span><span class="sxs-lookup"><span data-stu-id="3eb41-113">[DropDownButton](../design/controls-and-patterns/buttons.md#create-a-drop-down-button), [SplitButton](../design/controls-and-patterns/buttons.md#create-a-split-button), and [ToggleSplitButton](../design/controls-and-patterns/buttons.md#create-a-toggle-split-button) provide button controls with specialized features to enhance your app's user interface.</span></span>

![Eine geteilte Schaltfläche zum Auswählen von Vordergrundfarbe](../design/controls-and-patterns/images/split-button-rtb.png)

* <span data-ttu-id="3eb41-115">NavigationView unterstützt jetzt in der [oberen Navigationsleiste](../design/controls-and-patterns/navigationview.md)für Fälle, in dem Ihre app verfügt über weniger Navigationsoptionen und mehr Platz für den Inhalt Ihrer app erforderlich.</span><span class="sxs-lookup"><span data-stu-id="3eb41-115">NavigationView now supports [Top navigation](../design/controls-and-patterns/navigationview.md), for cases in which your app has a smaller number of navigation options and require more space for your app's content.</span></span>

* <span data-ttu-id="3eb41-116">Strukturansicht wurde zur Unterstützung von erweitert [Daten binden, Elementvorlagen, und Drag & drop.](../design/controls-and-patterns/tree-view.md)</span><span class="sxs-lookup"><span data-stu-id="3eb41-116">TreeView has been enhanced to support [data binding, item templates, and drag and drop.](../design/controls-and-patterns/tree-view.md)</span></span>

### <a name="package-support-framework"></a><span data-ttu-id="3eb41-117">Paket-Support-Framework</span><span class="sxs-lookup"><span data-stu-id="3eb41-117">Package Support Framework</span></span>

<span data-ttu-id="3eb41-118">Das Paket-Support-Framework ist ein Open-Source-Kit, das hilft Ihnen das Anwenden von Updates für Ihre win32-Anwendung, wenn Sie keinen Zugriff auf den Quellcode haben, damit sie in einem MSIX-Container ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="3eb41-118">The package support framework is an open-source kit that helps you apply fixes to your win32 application when you don’t have access to the source code, so that it can run in an MSIX container.</span></span>

<span data-ttu-id="3eb41-119">Um mehr zu erfahren, finden Sie in der [Übernehmen Runtime behebt ein MSIX-Paket mit dem Paket Support-Framework](../porting/package-support-framework.md).</span><span class="sxs-lookup"><span data-stu-id="3eb41-119">To learn more, see [Apply runtime fixes to an MSIX package by using the Package Support Framework](../porting/package-support-framework.md).</span></span>

## <a name="developer-guidance"></a><span data-ttu-id="3eb41-120">Anleitungen für Entwickler</span><span class="sxs-lookup"><span data-stu-id="3eb41-120">Developer Guidance</span></span>

### <a name="web-api-extensions"></a><span data-ttu-id="3eb41-121">Web-API-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="3eb41-121">Web API extensions</span></span>

<span data-ttu-id="3eb41-122">Eine Liste der [Erweiterungen für ältere Microsoft-API](https://developer.mozilla.org/docs/Web/API/Microsoft_API_extensions) wurde in der Dokumentation Mozilla Developer Network browserübergreifende Webentwicklung hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="3eb41-122">A list of [legacy Microsoft API extensions](https://developer.mozilla.org/docs/Web/API/Microsoft_API_extensions) has been added to the Mozilla Developer Network documentation for cross-browser web development.</span></span> <span data-ttu-id="3eb41-123">Diese API-Erweiterungen sind spezifisch für Internet Explorer oder Microsoft Edge, und ergänzen vorhandene Informationen zur Kompatibilität und Browser-Unterstützung in der MDN Web-Dokumentation. Ältere Microsoft [CSS-Erweiterungen](https://developer.mozilla.org/docs/Web/CSS/Microsoft_Extensions) und [JavaScript-Erweiterungen](https://developer.mozilla.org/docs/Web/JavaScript/Microsoft_JavaScript_extensions) sind auch verfügbar, und finden Sie umfassende Web-API-Informationen aus MDN Warnungen direkt in [Visual Studio Code.](https://code.visualstudio.com/updates/v1_25#_new-css-pseudo-selectors-and-pseudo-elements-from-mdn)</span><span class="sxs-lookup"><span data-stu-id="3eb41-123">These API extensions are unique to Internet Explorer or Microsoft Edge, and supplement existing information about compatibility and broswer support in the MDN web docs. Legacy Microsoft [CSS extensions](https://developer.mozilla.org/docs/Web/CSS/Microsoft_Extensions) and [JavaScript extensions](https://developer.mozilla.org/docs/Web/JavaScript/Microsoft_JavaScript_extensions) are also available, and you can find rich web API information from MDN surfaced directly in [Visual Studio Code.](https://code.visualstudio.com/updates/v1_25#_new-css-pseudo-selectors-and-pseudo-elements-from-mdn)</span></span>

### <a name="cwinrt-code-examples"></a><span data-ttu-id="3eb41-124">C++ / WinRT-Code-Beispiele</span><span class="sxs-lookup"><span data-stu-id="3eb41-124">C++/WinRT Code examples</span></span>

<span data-ttu-id="3eb41-125">Wir haben 250 hinzugefügt [C++ / WinRT](../cpp-and-winrt-apis/index.md) Einträge zu Themen in unserer Dokumentation, begleitende vorhandenen C++-code / CX-Code-Beispiele.</span><span class="sxs-lookup"><span data-stu-id="3eb41-125">We've added 250 [C++/WinRT](../cpp-and-winrt-apis/index.md) code listings to topics in our docs, accompanying existing C++/CX code examples.</span></span>

### <a name="project-rome"></a><span data-ttu-id="3eb41-126">Projekt Rome</span><span class="sxs-lookup"><span data-stu-id="3eb41-126">Project Rome</span></span>

<span data-ttu-id="3eb41-127">Die Website [Project Rome Dokumente](https://docs.microsoft.com/windows/project-rome/) wurde in einen Ansatz Feature ausgelegt neu organisiert.</span><span class="sxs-lookup"><span data-stu-id="3eb41-127">The [Project Rome docs](https://docs.microsoft.com/windows/project-rome/) site has been reorganized into a feature-first approach.</span></span> <span data-ttu-id="3eb41-128">Dies sollte einfacher für Entwickler zu finden, was sie suchen und Features ihrer Wahl für mehrere Plattformen zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="3eb41-128">This should make it easier for developers to find what they're looking for, and to implement features of their choice across multiple platforms.</span></span>

## <a name="videos"></a><span data-ttu-id="3eb41-129">Videos</span><span class="sxs-lookup"><span data-stu-id="3eb41-129">Videos</span></span>

### <a name="xbox-live-unity-plugin"></a><span data-ttu-id="3eb41-130">Xbox Live Unity-Plug-in</span><span class="sxs-lookup"><span data-stu-id="3eb41-130">Xbox Live Unity plugin</span></span>

<span data-ttu-id="3eb41-131">Die Xbox Live-Plug-In für Unity enthält Unterstützung für das Hinzufügen von Xbox Live zu signieren, Statistiken, Freunde-Listen, Cloud-Speicher und Bestenlisten um Ihrem Titel.</span><span class="sxs-lookup"><span data-stu-id="3eb41-131">The Xbox Live plugin for Unity contains support for adding Xbox Live signing, stats, friends lists, cloud storage, and leaderboards to your title.</span></span> <span data-ttu-id="3eb41-132">[Das Video ansehen](https://youtu.be/fVQZ-YgwNpY) , um mehr zu erfahren, und [das GitHub-Paket herunterzuladen](https://aka.ms/UnityPlugin) , für den Einstieg.</span><span class="sxs-lookup"><span data-stu-id="3eb41-132">[Watch the video](https://youtu.be/fVQZ-YgwNpY) to learn more, then [download the GitHub package](https://aka.ms/UnityPlugin) to get started.</span></span>

### <a name="one-dev-question"></a><span data-ttu-id="3eb41-133">One Dev Frage</span><span class="sxs-lookup"><span data-stu-id="3eb41-133">One Dev Question</span></span>

<span data-ttu-id="3eb41-134">In der eine Dev Frage Videoserie behandelt seit Microsoft-Entwicklern eine Reihe von Fragen zur Windows-Entwicklung, Teamkultur, und zum Verlauf.</span><span class="sxs-lookup"><span data-stu-id="3eb41-134">In the One Dev Question video series, longtime Microsoft developers cover a series of questions about Windows development, team culture, and history.</span></span> <span data-ttu-id="3eb41-135">Hier ist die neueste Fragen, die wir beantwortet haben!</span><span class="sxs-lookup"><span data-stu-id="3eb41-135">Here's the latest questions that we've answered!</span></span>

<span data-ttu-id="3eb41-136">Raymond Chen:</span><span class="sxs-lookup"><span data-stu-id="3eb41-136">Raymond Chen:</span></span>

* [<span data-ttu-id="3eb41-137">Woher weiß der Kernel bei Videotreibers neu gestartet?</span><span class="sxs-lookup"><span data-stu-id="3eb41-137">How does the kernel know when to restart a video driver?</span></span>](https://youtu.be/3SNAdyO1l5c)

<span data-ttu-id="3eb41-138">Larry Osterman:</span><span class="sxs-lookup"><span data-stu-id="3eb41-138">Larry Osterman:</span></span>

* [<span data-ttu-id="3eb41-139">Was ist die Story hinter dem Burgermaster-Objekt in Windows?</span><span class="sxs-lookup"><span data-stu-id="3eb41-139">What's the story behind the Burgermaster object in Windows?</span></span>](https://youtu.be/0TDSbyAIvX0)