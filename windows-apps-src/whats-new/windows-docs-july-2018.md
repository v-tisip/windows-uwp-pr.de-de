---
author: QuinnRadich
title: Was ist neu in Windows-Dokumente im Juli 2018 – Entwickeln von apps UWP
description: Neue Features, Videos, Beispiele und Anleitungen für Entwickler wurden in der Windows-10-Entwicklerdokumentation für Juli 2018 hinzugefügt.
keywords: Neues in, Update, Features, Developer Leitfaden für die Windows-10, Juli
ms.author: quradic
ms.date: 7/11/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: f41d25fd6757e5d3f80d00de341168de4f34e946
ms.sourcegitcommit: f2f4820dd2026f1b47a2b1bf2bc89d7220a79c1a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "2802061"
---
# <a name="whats-new-in-the-windows-developer-docs-in-july-2018"></a><span data-ttu-id="68a33-104">Was ist neu in der Windows-Entwicklerdokumente im Juli 2018</span><span class="sxs-lookup"><span data-stu-id="68a33-104">What's New in the Windows Developer Docs in July 2018</span></span>

<span data-ttu-id="68a33-105">Die Entwicklerdokumentation für die Windows-Plattform wird ständig mit Informationen über neue Features für Entwickler aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="68a33-105">The Windows Developer Documentation is constantly being updated with information on new features available to developers across the Windows platform.</span></span> <span data-ttu-id="68a33-106">Die folgenden Featureübersichten, Hinweise für Entwickler, Videos und Beispiele wurden im Juli verfügbar gemacht wurden.</span><span class="sxs-lookup"><span data-stu-id="68a33-106">The following feature overviews, developer guidance, videos, and samples have been made available in the month of July.</span></span>

<span data-ttu-id="68a33-107">Nach der [Installation der Tools und des SDKs](http://go.microsoft.com/fwlink/?LinkId=821431) unter Windows10 können Sie entweder [eine neue universelle Windows-App erstellen](../get-started/create-uwp-apps.md) oder sich mit der Verwendung von [vorhandenem App-Code unter Windows](../porting/index.md) vertraut machen.</span><span class="sxs-lookup"><span data-stu-id="68a33-107">[Install the tools and SDK](http://go.microsoft.com/fwlink/?LinkId=821431) on Windows 10 and you’re ready to either [create a new Universal Windows app](../get-started/create-uwp-apps.md) or explore how you can use your [existing app code on Windows](../porting/index.md).</span></span>

## <a name="features"></a><span data-ttu-id="68a33-108">Features</span><span class="sxs-lookup"><span data-stu-id="68a33-108">Features</span></span>

### <a name="progressive-web-apps-on-windows"></a><span data-ttu-id="68a33-109">Progressiv Web Apps in Windows</span><span class="sxs-lookup"><span data-stu-id="68a33-109">Progressive Web Apps on Windows</span></span>

<span data-ttu-id="68a33-110">[Progressiv Web Apps (PWAs)](https://developer.microsoft.com/windows/pwa) werden einfach Web-apps, die mit systemeigenen app-ähnliche Features zur Unterstützung der Plattformen und Module an Browser, wie Einführung von Startseite Installation, offline-Unterstützung und Push [stetig verbesserte](https://wikipedia.org/wiki/Progressive_enhancement) sind Benachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="68a33-110">[Progressive Web Apps (PWAs)](https://developer.microsoft.com/windows/pwa) are simply web apps that are [progressively enhanced](https://wikipedia.org/wiki/Progressive_enhancement) with native app-like features on supporting platforms and browser engines, such as launch-from-homescreen installation, offline support, and push notifications.</span></span> <span data-ttu-id="68a33-111">Auf Windows-10 mit der Microsoft Edge (EdgeHTML) Engine, PWAs genießen Sie den zusätzlichen Vorteil Ausführung [unabhängig von der Browserfenster als UWP apps.](https://docs.microsoft.com/microsoft-edge/progressive-web-apps/windows-features)</span><span class="sxs-lookup"><span data-stu-id="68a33-111">On Windows 10 with the Microsoft Edge (EdgeHTML) engine, PWAs enjoy the added advantage of running [independently of the browser window as UWP apps.](https://docs.microsoft.com/microsoft-edge/progressive-web-apps/windows-features)</span></span>

![Ein Bild des PWAs in Aktion](images/progressive-web-apps.jpg)

<span data-ttu-id="68a33-113">Schauen Sie sich unsere PWA Leitzeichen hinzu:</span><span class="sxs-lookup"><span data-stu-id="68a33-113">Check out our PWA guides to:</span></span>

* [<span data-ttu-id="68a33-114">Erstellen einer einfachen Web-app als eine PWA</span><span class="sxs-lookup"><span data-stu-id="68a33-114">Build a simple web app as a PWA</span></span>](https://docs.microsoft.com/microsoft-edge/progressive-web-apps/get-started)
* [<span data-ttu-id="68a33-115">Verbessern Sie Ihre PWA mit Windows-Runtime</span><span class="sxs-lookup"><span data-stu-id="68a33-115">Enhance your PWA with the Windows Runtime</span></span>](https://docs.microsoft.com/en-us/microsoft-edge/progressive-web-apps/windows-features)
* [<span data-ttu-id="68a33-116">Veröffentlichen Sie Ihre PWA an den Microsoft-Store</span><span class="sxs-lookup"><span data-stu-id="68a33-116">Publish your PWA to the Microsoft Store</span></span>](https://docs.microsoft.com/microsoft-edge/progressive-web-apps/microsoft-store)

### <a name="notepad"></a><span data-ttu-id="68a33-117">Windows-Editor</span><span class="sxs-lookup"><span data-stu-id="68a33-117">Notepad</span></span>

<span data-ttu-id="68a33-118">Verfügbar in Windows 10 Insider Vorschau erstellen 17713, [Editor viele neue Features aktualisiert wurde](http://aka.ms/ant-man).</span><span class="sxs-lookup"><span data-stu-id="68a33-118">Available in Windows 10 Insider Preview Build 17713, [Notepad has been updated with many new features](http://aka.ms/ant-man).</span></span> <span data-ttu-id="68a33-119">Zoomen, umgeben Suchen/Ersetzen und Unterstützung für Unix/Linux (LF) und Mac (CR) Zeilenenden sind [Windows-Insider](https://insider.windows.com/)zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="68a33-119">Zooming, wrap-around find/replace, and support for Unix/Linux (LF) and Mac (CR) line endings are now available to [Windows Insiders](https://insider.windows.com/).</span></span> 

## <a name="developer-guidance"></a><span data-ttu-id="68a33-120">Anleitungen für Entwickler</span><span class="sxs-lookup"><span data-stu-id="68a33-120">Developer Guidance</span></span>

### <a name="design-landing-page"></a><span data-ttu-id="68a33-121">Design-Angebotsseite</span><span class="sxs-lookup"><span data-stu-id="68a33-121">Design landing page</span></span>

<span data-ttu-id="68a33-122">Checken Sie die [Design Angebotsseite aktualisiert](https://developer.microsoft.com/windows/apps/design) eine auf einen Blick Übersicht über UWP Design Bereiche und Informationen über die neusten Fluent Entwurf.</span><span class="sxs-lookup"><span data-stu-id="68a33-122">Check out the [updated Design landing page](https://developer.microsoft.com/windows/apps/design) for an at-a-glance overview of UWP design areas, and information on the latest additions to Fluent Design.</span></span>

### <a name="design-toolkits"></a><span data-ttu-id="68a33-123">Design-Toolkits</span><span class="sxs-lookup"><span data-stu-id="68a33-123">Design toolkits</span></span>

<span data-ttu-id="68a33-124">Adobe XD und Adobe Illustrator-Toolkits wurden mit neuen Features aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="68a33-124">The Adobe XD and Adobe Illustrator toolkits have been updated with new features.</span></span> <span data-ttu-id="68a33-125">Mit diesen Entwurf Toolkits bieten Steuerelemente und Layoutvorlagen für das Entwerfen von UWP apps.</span><span class="sxs-lookup"><span data-stu-id="68a33-125">These design toolkits provide controls and layout templates for designing UWP apps.</span></span> [<span data-ttu-id="68a33-126">Überprüfen sie hier.</span><span class="sxs-lookup"><span data-stu-id="68a33-126">Check them out here.</span></span>](../design/downloads/index.md)

### <a name="webvr"></a><span data-ttu-id="68a33-127">WebVR</span><span class="sxs-lookup"><span data-stu-id="68a33-127">WebVR</span></span>

<span data-ttu-id="68a33-128">Wir haben mehrere neue Themen in der [Dokumentation zu WebVR](https://docs.microsoft.com/microsoft-edge/webvr/
)hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="68a33-128">We've added several new topics to the [WebVR documentation](https://docs.microsoft.com/microsoft-edge/webvr/
):</span></span>

* [<span data-ttu-id="68a33-129">Was ist WebVR?</span><span class="sxs-lookup"><span data-stu-id="68a33-129">What is WebVR?</span></span>](https://docs.microsoft.com/microsoft-edge/webvr/what-is-webvr
) <span data-ttu-id="68a33-130">Erläutert, was WebVR ist, warum Sie es verwenden sollten und wie Sie die ersten Schritte beim Entwickeln von dafür.</span><span class="sxs-lookup"><span data-stu-id="68a33-130">Explains what WebVR is, why you should use it, and how to get started developing for it.</span></span>

* <span data-ttu-id="68a33-131">[WebVR in progressiv Web-Apps](https://docs.microsoft.com/microsoft-edge/webvr/webvr-in-pwas): Hier erfahren Sie, wie WebVR zum schrittweisen Web App (PWA) hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="68a33-131">[WebVR in Progressive Web Apps](https://docs.microsoft.com/microsoft-edge/webvr/webvr-in-pwas): Learn how to add WebVR to a Progressive Web App (PWA).</span></span>

* <span data-ttu-id="68a33-132">[In der Webansicht WebVR](https://docs.microsoft.com/microsoft-edge/webvr/webvr-in-webview): Hier erfahren Sie, wie ein Steuerelement Webansicht in einer Windows-10-Anwendung WebVR hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="68a33-132">[WebVR in WebView](https://docs.microsoft.com/microsoft-edge/webvr/webvr-in-webview): Learn how to add WebVR to a WebView control in a Windows 10 application.</span></span>

* <span data-ttu-id="68a33-133">[WebVR Demos](https://docs.microsoft.com/microsoft-edge/webvr/demos): Einige WebVR Demos mithilfe von Microsoft Edge und einer gemischten Windows-Realität fesselnden Kopfhörer Auschecken.</span><span class="sxs-lookup"><span data-stu-id="68a33-133">[WebVR demos](https://docs.microsoft.com/microsoft-edge/webvr/demos): Check out some WebVR demos using Microsoft Edge and a Windows Mixed Reality immersive headset.</span></span>

<span data-ttu-id="68a33-134">Darüber hinaus haben wir einige Updates zu vorhandenen Seiten vorgenommen:</span><span class="sxs-lookup"><span data-stu-id="68a33-134">In addition, we've made some updates to existing pages:</span></span>

* <span data-ttu-id="68a33-135">Das Inhaltsverzeichnis ist jetzt besser organisiert werden in vier unterschiedlichen auf oberster Ebene Buckets: **Grundlagen**, **Entwicklung**, **Ressourcen**und **Demos**.</span><span class="sxs-lookup"><span data-stu-id="68a33-135">The table of contents is now better organized into four distinct top-level buckets: **Fundamentals**, **Development**, **Resources**, and **Demos**.</span></span>

* <span data-ttu-id="68a33-136">[WebVR-Entwicklerhandbuch (Angebotsseite)](https://docs.microsoft.com/microsoft-edge/webvr/): aktualisiert Aussehen und Verhalten mit größere Bilder und Symbole und neue Demo.</span><span class="sxs-lookup"><span data-stu-id="68a33-136">[WebVR Developer's Guide (landing page)](https://docs.microsoft.com/microsoft-edge/webvr/): Refreshed look and feel, with larger images and icons and new demo.</span></span>

* <span data-ttu-id="68a33-137">[Mithilfe von WebVR mit Microsoft Edge](https://docs.microsoft.com/microsoft-edge/webvr/webvr-with-edge): aktualisierte Informationen über die Windows 10 April 2018 aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="68a33-137">[Using WebVR with Microsoft Edge](https://docs.microsoft.com/microsoft-edge/webvr/webvr-with-edge): Updated to include information about the Windows 10 April 2018 Update.</span></span>

## <a name="videos"></a><span data-ttu-id="68a33-138">Videos</span><span class="sxs-lookup"><span data-stu-id="68a33-138">Videos</span></span>

### <a name="get-started-for-devs-create-and-customize-a-form-on-windows-10"></a><span data-ttu-id="68a33-139">Erste Schritte für Entwickler: Erstellen und Anpassen eines Formulars auf Windows-10</span><span class="sxs-lookup"><span data-stu-id="68a33-139">Get Started for Devs: Create and customize a form on Windows 10</span></span>

<span data-ttu-id="68a33-140">Unsere [Einstieg in die Dokumente](../get-started/index.md) für Windows-Entwickler bieten jetzt praktische Erfahrung mit grundlegenden app Entwicklungsaufgabe.</span><span class="sxs-lookup"><span data-stu-id="68a33-140">Our [Get Started docs](../get-started/index.md) for Windows developers now provide hands-on experience with basic app development task.</span></span> <span data-ttu-id="68a33-141">In diesem Video führt Sie durch eine diese Themen und die Grundlagen der Erstellung eines Formulars Benutzeroberfläche in Ihrer app behandelt.</span><span class="sxs-lookup"><span data-stu-id="68a33-141">This video walks you through one of those topics, and covers the basics of creating a form UI in your app.</span></span> <span data-ttu-id="68a33-142">[Video ansehen](https://www.youtube.com/watch?v=AgngKzq4hKI&feature=youtu.be) , sehen Sie den Code in der Praxis, klicken Sie dann [checken Sie das Thema selbst.](http://aka.ms/CreateForms)</span><span class="sxs-lookup"><span data-stu-id="68a33-142">[Watch the video](https://www.youtube.com/watch?v=AgngKzq4hKI&feature=youtu.be) to see the code in action, then [check out the topic yourself.](http://aka.ms/CreateForms)</span></span>

### <a name="enhance-your-bot-with-project-personality-chat"></a><span data-ttu-id="68a33-143">Verbessern Sie Ihre Bot mit Project Persönlichkeit chat</span><span class="sxs-lookup"><span data-stu-id="68a33-143">Enhance your Bot with Project Personality chat</span></span>

<span data-ttu-id="68a33-144">Projekt Persönlichkeit Chat können Sie Ihre Chat Bots eine anpassbare Rolle hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="68a33-144">Project Personality Chat lets you add a customizable persona to your chat bots.</span></span> <span data-ttu-id="68a33-145">Durch die Integration mit Microsoft Bot Framework SDK, können Sie kleine-Talk-Funktionen für mehr gesprochene Möglichkeit zur Interaktion mit den Kunden hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="68a33-145">By integrating with the Microsoft Bot Framework SDK, you can add small-talk capabilities for a more conversational way to interact with the customers.</span></span> <span data-ttu-id="68a33-146">[Video ansehen](https://www.youtube.com/watch?v=5C_uD8g2QKg&feature=youtu.be) , erfahren, wie es ausführen und [Testen die interaktive Demo](http://aka.ms/PersonalityChat) Hands-On-Erfahrung zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="68a33-146">[Watch the video](https://www.youtube.com/watch?v=5C_uD8g2QKg&feature=youtu.be) to learn how to implement it, then [try out the interactive demo](http://aka.ms/PersonalityChat) for a hands-on experience.</span></span>

### <a name="one-dev-question"></a><span data-ttu-id="68a33-147">Eine Dev Frage</span><span class="sxs-lookup"><span data-stu-id="68a33-147">One Dev Question</span></span>

<span data-ttu-id="68a33-148">In der eine Dev Frage Videoserie behandelt seit Microsoft Entwickler eine Reihe von Fragen zu Windows-Entwicklung, Teamkultur und Verlauf.</span><span class="sxs-lookup"><span data-stu-id="68a33-148">In the One Dev Question video series, longtime Microsoft developers cover a series of questions about Windows development, team culture, and history.</span></span> <span data-ttu-id="68a33-149">Nachfolgend finden Sie die neuesten Fragen, die wir angenommen haben!</span><span class="sxs-lookup"><span data-stu-id="68a33-149">Here's the latest questions that we've answered!</span></span>

<span data-ttu-id="68a33-150">Raymond Chen:</span><span class="sxs-lookup"><span data-stu-id="68a33-150">Raymond Chen:</span></span>

* [<span data-ttu-id="68a33-151">Warum zuweisen Sie Microsoft?</span><span class="sxs-lookup"><span data-stu-id="68a33-151">Why did you apply to Microsoft?</span></span>](https://www.youtube.com/watch?v=oL8ymamkEMU&feature=youtu.be)

<span data-ttu-id="68a33-152">Larry Osterman:</span><span class="sxs-lookup"><span data-stu-id="68a33-152">Larry Osterman:</span></span>

* [<span data-ttu-id="68a33-153">Warum lassen wir nicht Entwickler Standardaudiogerät ändern?</span><span class="sxs-lookup"><span data-stu-id="68a33-153">Why don't we let developers change the default audio device?</span></span>](https://www.youtube.com/watch?v=6aNUoVfbnmg&feature=youtu.be)
* [<span data-ttu-id="68a33-154">Warum sind so viele UWP Funktionen Async?</span><span class="sxs-lookup"><span data-stu-id="68a33-154">Why are so many UWP functions async?</span></span>](https://www.youtube.com/watch?v=5M724QIy1Mk&feature=youtu.be)

## <a name="samples"></a><span data-ttu-id="68a33-155">Beispiele</span><span class="sxs-lookup"><span data-stu-id="68a33-155">Samples</span></span>

### <a name="photo-editor-cwinrt"></a><span data-ttu-id="68a33-156">Photo Editor C + / WinRT</span><span class="sxs-lookup"><span data-stu-id="68a33-156">Photo Editor C++/WinRT</span></span>

<span data-ttu-id="68a33-157">Die Photo Editor Beispiel-app werden die Entwicklung mit der [C + / WinRT](../cpp-and-winrt-apis/intro-to-using-cpp-with-winrt.md) Sprache Projektion.</span><span class="sxs-lookup"><span data-stu-id="68a33-157">The Photo Editor sample app showcases development with the [C++/WinRT](../cpp-and-winrt-apis/intro-to-using-cpp-with-winrt.md) language projection.</span></span> <span data-ttu-id="68a33-158">Die app können Sie Fotos aus **der Bildbibliothek** abrufen, und klicken Sie dann bearbeiten eine markierte Bild mit zugeordneten fotoeffekten.</span><span class="sxs-lookup"><span data-stu-id="68a33-158">The app allows you to retrieve photos from the **Pictures** library, and then edit a elected image with associated photo effects.</span></span> [<span data-ttu-id="68a33-159">Klonen oder das Beispiel hier herunterladen.</span><span class="sxs-lookup"><span data-stu-id="68a33-159">Clone or download the sample here.</span></span>](https://github.com/Microsoft/Windows-appsample-photo-editor)

![Ein Beispiel für das Beispiel in Aktion](images/photo-editor-banner.png)
