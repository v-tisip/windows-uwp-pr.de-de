---
author: QuinnRadich
title: Was ist neu in Windows-Dokumente im August 2018 – Entwickeln von apps UWP
description: Neue Features, Videos, Beispiele und Anleitungen für Entwickler wurden in der Windows-10-Entwicklerdokumentation für August 2018 hinzugefügt.
keywords: Neues in, Update, Features, Developer Leitfaden für die Windows-10, august
ms.author: quradic
ms.date: 8/9/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: 06eef0c115675ba9673a81459c91e0f08f6fab71
ms.sourcegitcommit: be5b71a8ec7b686d5f93d56d10cb9a50c3c5bb4a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "2748868"
---
# <a name="whats-new-in-the-windows-developer-docs-in-august-2018"></a><span data-ttu-id="3c32e-104">Was ist neu in der Windows-Entwicklerdokumente im August 2018</span><span class="sxs-lookup"><span data-stu-id="3c32e-104">What's New in the Windows Developer Docs in August 2018</span></span>

<span data-ttu-id="3c32e-105">Die Entwicklerdokumentation für die Windows-Plattform wird ständig mit Informationen über neue Features für Entwickler aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="3c32e-105">The Windows Developer Documentation is constantly being updated with information on new features available to developers across the Windows platform.</span></span> <span data-ttu-id="3c32e-106">Die folgenden Featureübersichten, Developer Anleitungen und Videos sind in den Monat August verfügbar gemacht wurden.</span><span class="sxs-lookup"><span data-stu-id="3c32e-106">The following feature overviews, developer guidance, and videos have been made available in the month of August.</span></span>

<span data-ttu-id="3c32e-107">Nach der [Installation der Tools und des SDKs](http://go.microsoft.com/fwlink/?LinkId=821431) unter Windows10 können Sie entweder [eine neue universelle Windows-App erstellen](../get-started/create-uwp-apps.md) oder sich mit der Verwendung von [vorhandenem App-Code unter Windows](../porting/index.md) vertraut machen.</span><span class="sxs-lookup"><span data-stu-id="3c32e-107">[Install the tools and SDK](http://go.microsoft.com/fwlink/?LinkId=821431) on Windows 10 and you’re ready to either [create a new Universal Windows app](../get-started/create-uwp-apps.md) or explore how you can use your [existing app code on Windows](../porting/index.md).</span></span>

## <a name="features"></a><span data-ttu-id="3c32e-108">Features</span><span class="sxs-lookup"><span data-stu-id="3c32e-108">Features</span></span>

### <a name="design"></a><span data-ttu-id="3c32e-109">Entwerfen</span><span class="sxs-lookup"><span data-stu-id="3c32e-109">Design</span></span>

<span data-ttu-id="3c32e-110">Die folgenden Features wurden an den Windows Insider Preview Builds, über die [Windows-Insider](https://insider.windows.com/) -Anwendung hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="3c32e-110">The following features have been added to the Windows Insider Preview builds, available through the [Windows Insider](https://insider.windows.com/) program.</span></span>

* <span data-ttu-id="3c32e-111">Die [UI-Bibliothek für Windows](https://aka.ms/winui-docs) ist eine Reihe von NuGet-Pakete, die Steuerelemente und andere interfact Elemente für apps UWP bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="3c32e-111">The [Windows UI Library](https://aka.ms/winui-docs) is a set of NuGet packages that provide controls and other user interfact elements for UWP apps.</span></span> <span data-ttu-id="3c32e-112">Diese Pakete sind auch kompatibel mit früheren Versionen von Windows 10, damit Ihre app funktioniert, auch wenn die Benutzer nicht über die neueste Version des Betriebssystems verfügen.</span><span class="sxs-lookup"><span data-stu-id="3c32e-112">These packages are also compatable with earlier versions of Windows 10, so your app works even if your users don't have the latest OS version.</span></span>

* <span data-ttu-id="3c32e-113">[DropDownButton, SplitButton, und ToggleSplitButton](../design/controls-and-patterns/buttons.md) bieten Schaltflächensteuerelemente mit speziellen Features Ihrer app-Benutzeroberfläche optimiert.</span><span class="sxs-lookup"><span data-stu-id="3c32e-113">[DropDownButton, SplitButton, and ToggleSplitButton](../design/controls-and-patterns/buttons.md) provide button controls with specialized features to enhance your app's user experience.</span></span>

* <span data-ttu-id="3c32e-114">NavigationView unterstützt [der oberen Navigationsleiste](../design/controls-and-patterns/navigationview.md) für Fälle, in denen Ihre app eine kleinere Anzahl von Optionen für die Websitenavigation verfügt, und erfordern mehr Speicherplatz für Ihre app Inhalte.</span><span class="sxs-lookup"><span data-stu-id="3c32e-114">NavigationView now supports [Top navigation,](../design/controls-and-patterns/navigationview.md) for cases in which your app has a smaller number of navigation options and require more space for your app's content.</span></span>

* <span data-ttu-id="3c32e-115">"TreeView" wurde verbessert zur Unterstützung der [Datenbindung, Elementvorlagen, und Dragon and -Drop.](../design/controls-and-patterns/tree-view.md)</span><span class="sxs-lookup"><span data-stu-id="3c32e-115">TreeView has been enhanced to support [data binding, item templates, and dragon and drop.](../design/controls-and-patterns/tree-view.md)</span></span>

![Eine Trennschaltfläche für die Auswahl von Vordergrundfarbe](../design/controls-and-patterns/images/split-button-rtb.png)

### <a name="package-support-framework"></a><span data-ttu-id="3c32e-117">Paket-Support-Framework</span><span class="sxs-lookup"><span data-stu-id="3c32e-117">Package Support Framework</span></span>

<span data-ttu-id="3c32e-118">Das Paket Support-Framework ist ein open-Source-Kit, die Dank gelten Korrekturen für Ihre Win32-Anwendung, wenn Sie nicht über Zugriff auf den Quellcode verfügen, damit es in einem MSIX-Container ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="3c32e-118">The package support framework is an open source kit that helps you apply fixes to your win32 application when you don’t have access to the source code, so that it can run in an MSIX container.</span></span>  

<span data-ttu-id="3c32e-119">Weitere Informationen finden Sie unter [Übernehmen Runtime behebt zu einem Paket MSIX mithilfe des Paket-Support-Frameworks](../porting/package-support-framework.md).</span><span class="sxs-lookup"><span data-stu-id="3c32e-119">To learn more, see [Apply runtime fixes to an MSIX package by using the Package Support Framework](../porting/package-support-framework.md).</span></span>

## <a name="developer-guidance"></a><span data-ttu-id="3c32e-120">Anleitungen für Entwickler</span><span class="sxs-lookup"><span data-stu-id="3c32e-120">Developer Guidance</span></span>

### <a name="web-api-extensions"></a><span data-ttu-id="3c32e-121">Web-API-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="3c32e-121">Web API extensions</span></span>

<span data-ttu-id="3c32e-122">Eine Liste mit [älteren Microsoft-API-Erweiterungen](https://developer.mozilla.org/docs/Web/API/Microsoft_API_extensions) wurde der Mozilla Developer Network-Dokumentation für browserübergreifende Webentwicklung hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="3c32e-122">A list of [legacy Microsoft API extensions](https://developer.mozilla.org/docs/Web/API/Microsoft_API_extensions) has been added to the Mozilla Developer Network documentation for cross-browser web development.</span></span> <span data-ttu-id="3c32e-123">Diese API-Erweiterungen stehen nur in Internet Explorer oder Microsoft Edge, und vorhandene Informationen zur Kompatibilität und Browser-Unterstützung in der Webdokumente MDN ergänzen. Ältere Microsoft [CSS-Erweiterungen](https://developer.mozilla.org/docs/Web/CSS/Microsoft_Extensions) und [JavaScript-Erweiterungen](https://developer.mozilla.org/docs/Web/JavaScript/Microsoft_JavaScript_extensions) stehen ebenfalls zur Verfügung, und finden Sie rich-Web-API-Informationen aus MDN verfügbar gemacht, direkt in [Visual Studio-Code.](https://code.visualstudio.com/updates/v1_25#_new-css-pseudo-selectors-and-pseudo-elements-from-mdn)</span><span class="sxs-lookup"><span data-stu-id="3c32e-123">These API extensions are unique to Internet Explorer or Microsoft Edge, and supplement existing information about compatibility and broswer support in the MDN web docs. Legacy Microsoft [CSS extensions](https://developer.mozilla.org/docs/Web/CSS/Microsoft_Extensions) and [JavaScript extensions](https://developer.mozilla.org/docs/Web/JavaScript/Microsoft_JavaScript_extensions) are also available, and you can find rich web API information from MDN surfaced directly in [Visual Studio Code.](https://code.visualstudio.com/updates/v1_25#_new-css-pseudo-selectors-and-pseudo-elements-from-mdn)</span></span>

### <a name="cwinrt-code-examples"></a><span data-ttu-id="3c32e-124">C + / WinRT-Codebeispiele</span><span class="sxs-lookup"><span data-stu-id="3c32e-124">C++/WinRT Code examples</span></span>

<span data-ttu-id="3c32e-125">Wir haben 250 hinzugefügt [C + / WinRT](../cpp-and-winrt-apis/index.md) Codeausschnitte zu Themen, die in unserer Dokumente, die begleitenden vorhandenen C + / CX-Codebeispiele.</span><span class="sxs-lookup"><span data-stu-id="3c32e-125">We've added 250 [C++/WinRT](../cpp-and-winrt-apis/index.md) code snippets to topics in our docs, accompanying existing C++/CX code examples.</span></span>

### <a name="project-rome"></a><span data-ttu-id="3c32e-126">Projekt Rome</span><span class="sxs-lookup"><span data-stu-id="3c32e-126">Project Rome</span></span>

<span data-ttu-id="3c32e-127">Die [Projekt-ROM-Dokumente](https://docs.microsoft.com/windows/project-rome/) Website wurde in einer Feature-First-Ansatz neu organisiert.</span><span class="sxs-lookup"><span data-stu-id="3c32e-127">The [Project Rome docs](https://docs.microsoft.com/windows/project-rome/) site has been reorganized into a feature-first approach.</span></span> <span data-ttu-id="3c32e-128">Dies sollte erleichtern für Entwickler zu finden, wonach sie suchen und Funktionen ihrer Wahl plattformübergreifend implementieren.</span><span class="sxs-lookup"><span data-stu-id="3c32e-128">This should make it easier for developers to find what they're looking for, and to implement features of their choice across multiple platforms.</span></span>

## <a name="videos"></a><span data-ttu-id="3c32e-129">Videos</span><span class="sxs-lookup"><span data-stu-id="3c32e-129">Videos</span></span>

### <a name="xbox-live-unity-plugin"></a><span data-ttu-id="3c32e-130">Xbox Live-eins-Plug-in</span><span class="sxs-lookup"><span data-stu-id="3c32e-130">Xbox Live Unity plugin</span></span>

<span data-ttu-id="3c32e-131">Die Xbox Live-Plug-Ins für Einheit enthält Unterstützung für das Hinzufügen von Xbox Live Signieren, Stats, Freunde-Listen, Cloud-Speicher und setzen, Ihren Titel.</span><span class="sxs-lookup"><span data-stu-id="3c32e-131">The Xbox Live plugin for Unity contains support for adding Xbox Live signing, stats, friends lists, cloud storage, and leaderboards to your title.</span></span> <span data-ttu-id="3c32e-132">[Video ansehen](https://youtu.be/fVQZ-YgwNpY) , um mehr zu erfahren, und klicken Sie dann auf die ersten Schritte beim [Herunterladen des Pakets GitHub](https://aka.ms/UnityPlugin) .</span><span class="sxs-lookup"><span data-stu-id="3c32e-132">[Watch the video](https://youtu.be/fVQZ-YgwNpY) to learn more, then [download the GitHub package](https://aka.ms/UnityPlugin) to get started.</span></span>

### <a name="one-dev-question"></a><span data-ttu-id="3c32e-133">Eine Dev Frage</span><span class="sxs-lookup"><span data-stu-id="3c32e-133">One Dev Question</span></span>

<span data-ttu-id="3c32e-134">In der eine Dev Frage Videoserie behandelt seit Microsoft Entwickler eine Reihe von Fragen zu Windows-Entwicklung, Teamkultur und Verlauf.</span><span class="sxs-lookup"><span data-stu-id="3c32e-134">In the One Dev Question video series, longtime Microsoft developers cover a series of questions about Windows development, team culture, and history.</span></span> <span data-ttu-id="3c32e-135">Nachfolgend finden Sie die neuesten Fragen, die wir angenommen haben!</span><span class="sxs-lookup"><span data-stu-id="3c32e-135">Here's the latest questions that we've answered!</span></span>

<span data-ttu-id="3c32e-136">Raymond Chen:</span><span class="sxs-lookup"><span data-stu-id="3c32e-136">Raymond Chen:</span></span>

* [<span data-ttu-id="3c32e-137">Woher weiß Kernel wann einen Grafiktreiber neu starten?</span><span class="sxs-lookup"><span data-stu-id="3c32e-137">How does the kernel know when to restart a video driver?</span></span>](https://youtu.be/3SNAdyO1l5c)

<span data-ttu-id="3c32e-138">Larry Osterman:</span><span class="sxs-lookup"><span data-stu-id="3c32e-138">Larry Osterman:</span></span>

* [<span data-ttu-id="3c32e-139">Was ist die Geschichte des Burgermaster-Objekts in Windows?</span><span class="sxs-lookup"><span data-stu-id="3c32e-139">What's the story behind the Burgermaster object in Windows?</span></span>](https://youtu.be/0TDSbyAIvX0)