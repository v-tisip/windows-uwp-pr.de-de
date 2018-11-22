---
author: QuinnRadich
title: Neuigkeiten in der Windows-Dokumentation im Juli 2017 – Entwicklung von UWP-Apps
description: Neue Features, Beispiele und Entwicklerleitfäden in der Entwicklerdokumentation für Windows10 im Juli2017
keywords: Neuigkeiten, Update, Features, Anleitungen für Entwickler, Windows10
ms.author: quradic
ms.date: 07/05/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 62afbef1cc1f47bbc88c45a166572deca28d47a4
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2018
ms.locfileid: "7579538"
---
# <a name="whats-new-in-the-windows-developer-docs-in-july-2017"></a><span data-ttu-id="d4db1-104">Neuigkeiten in der Windows-Entwicklerdokumentation im Juli 2017</span><span class="sxs-lookup"><span data-stu-id="d4db1-104">What's New in the Windows Developer Docs in July 2017</span></span>

<span data-ttu-id="d4db1-105">Die Entwicklerdokumentation für die Windows-Plattform wird ständig mit Informationen über neue Features für Entwickler aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="d4db1-105">The Windows Developer Documentation is constantly being updated with information on new features available to developers across the Windows platform.</span></span> <span data-ttu-id="d4db1-106">Die folgenden Featureübersichten, Entwicklerleitfäden und Codebeispiele wurden erst kürzlich bereitgestellt und enthalten neue oder aktualisierte Informationen für Windows-Entwickler.</span><span class="sxs-lookup"><span data-stu-id="d4db1-106">The following feature overviews, developer guidance, and code samples have recently been made available, containing new and updated information for Windows developers.</span></span>

<span data-ttu-id="d4db1-107">Nach der [Installation der Tools und des SDKs](http://go.microsoft.com/fwlink/?LinkId=821431) unter Windows10 können Sie entweder [eine neue universelle Windows-App erstellen](../get-started/your-first-app.md) oder sich mit der Verwendung von [vorhandenem App-Code unter Windows](../porting/index.md) vertraut machen.</span><span class="sxs-lookup"><span data-stu-id="d4db1-107">[Install the tools and SDK](http://go.microsoft.com/fwlink/?LinkId=821431) on Windows 10 and you’re ready to either [create a new Universal Windows app](../get-started/your-first-app.md) or explore how you can use your [existing app code on Windows](../porting/index.md).</span></span>

## <a name="features"></a><span data-ttu-id="d4db1-108">Features</span><span class="sxs-lookup"><span data-stu-id="d4db1-108">Features</span></span>

### <a name="fluent-design"></a><span data-ttu-id="d4db1-109">Fluent Design</span><span class="sxs-lookup"><span data-stu-id="d4db1-109">Fluent Design</span></span>

<span data-ttu-id="d4db1-110">Diese neuen, jetzt für [Windows-Insider](https://insider.windows.com/) in SDK Preview Builds verfügbaren Effekte verwenden Tiefe, Perspektive und Bewegung, sodass die Benutzer sich auf wichtige Elemente der Benutzeroberfläche konzentrieren können.</span><span class="sxs-lookup"><span data-stu-id="d4db1-110">Available to [Windows Insiders](https://insider.windows.com/) in SDK Preview Builds, these new effects use depth, perspective, and movement to help users focus on important UI elements.</span></span>

<span data-ttu-id="d4db1-111">[Acrylmaterial](../design/style/acrylic.md) ist eine Art von Pinsel, der eine teilweise transparente Textur erzeugt.</span><span class="sxs-lookup"><span data-stu-id="d4db1-111">[Acrylic material](../design/style/acrylic.md) is a type of brush that creates transparent textures.</span></span> 

![Acryl im hellen Design](../design/style/images/Acrylic_DarkTheme_Base.png)

<span data-ttu-id="d4db1-113">Der [Parallaxeneffekt](../design/motion/parallax.md) fügt Ihrer App dreidimensionale Tiefe und Perspektive hinzu.</span><span class="sxs-lookup"><span data-stu-id="d4db1-113">The [Parallax effect](../design/motion/parallax.md) adds three-dimensional depth and perspective to your app.</span></span>

![Beispiel für Parallax mit einer Liste und einem Hintergrundbild](../design/style/images/_Parallax_v2.gif)

<span data-ttu-id="d4db1-115">[Einblendungen](../design/style/reveal.md) heben wichtige Elemente Ihrer App hervor.</span><span class="sxs-lookup"><span data-stu-id="d4db1-115">[Reveal](../design/style/reveal.md) highlights important elements of your app.</span></span> 

![Einblendeanzeige](../design/style/images/Nav_Reveal_Animation.gif)

### <a name="ui-controls"></a><span data-ttu-id="d4db1-117">UI-Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="d4db1-117">UI Controls</span></span>

<span data-ttu-id="d4db1-118">Diese neuen Steuerelemente für [Windows-Insider](https://insider.windows.com/) in SDK Preview-Builds erleichtern die Erstellung einer gut gestalteten Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="d4db1-118">Available to [Windows Insiders](https://insider.windows.com/) in SDK Preview Builds, these new controls make it easier to quickly build a great looking UI.</span></span>

<span data-ttu-id="d4db1-119">Das [Farbauswahl-Steuerelement](../design/controls-and-patterns/color-picker.md) ermöglicht es Benutzern, Farben zu durchsuchen und auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="d4db1-119">The [color picker control](../design/controls-and-patterns/color-picker.md) enables users to browse through and select colors.</span></span>  

![Eine Standard-Farbauswahl](../design/controls-and-patterns/images/color-picker-default.png)

<span data-ttu-id="d4db1-121">Mit dem [Navigationsansichts-Steuerelement](../design/controls-and-patterns/navigationview.md) lassen sich ganz einfach Navigationselemente auf oberster Ebene zu Ihrer App hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="d4db1-121">The [navigation view control](../design/controls-and-patterns/navigationview.md) makes it easy to add top-level navigation to your app.</span></span>

![Abschnitte von NavigationView](../design/controls-and-patterns/images/navview_sections.png)

<span data-ttu-id="d4db1-123">Das [Steuerelement für Bilder von Personen](../design/controls-and-patterns/person-picture.md) zeigt das Avatarbild für eine Person an.</span><span class="sxs-lookup"><span data-stu-id="d4db1-123">The [person picture control](../design/controls-and-patterns/person-picture.md) displays the avatar image for a person.</span></span>

![Das Steuerelement für Bilder von Personen](../design/controls-and-patterns/images/person-picture/person-picture_hero.png)

<span data-ttu-id="d4db1-125">Das [Bewertungssteuerelement](../design/controls-and-patterns/rating.md) ermöglicht es Benutzern, auf einfache Weise Bewertungen anzuzeigen und festzulegen, die den Grad der Zufriedenheit mit Inhalten und Diensten widerspiegeln.</span><span class="sxs-lookup"><span data-stu-id="d4db1-125">The [rating control](../design/controls-and-patterns/rating.md) enables users to easily view and set ratings that reflect degrees of satisfaction with content and services.</span></span>

![Beispiel mit einem Bewertungssteuerelement](../design/controls-and-patterns/images/rating_rs2_doc_ratings_intro.png)

### <a name="design-toolkits"></a><span data-ttu-id="d4db1-127">Design-Toolkits</span><span class="sxs-lookup"><span data-stu-id="d4db1-127">Design Toolkits</span></span>

<span data-ttu-id="d4db1-128">Die [Design-Toolkits und Ressourcen für UWP-Apps](../design/downloads/index.md) wurden um die Sketch- and Adobe XD-Toolkits erweitert.</span><span class="sxs-lookup"><span data-stu-id="d4db1-128">The [design toolkits and resources for UWP apps](../design/downloads/index.md) have been expanded with the addition of the Sketch and Adobe XD toolkits.</span></span> <span data-ttu-id="d4db1-129">Zudem wurden die bisherigen Toolkits aktualisiert und überarbeitet. Sie enthalten nun robustere Steuerelemente und Layoutvorlagen für Ihre UWP-Apps.</span><span class="sxs-lookup"><span data-stu-id="d4db1-129">The previously-existing toolkits have also been updated and revamped, providing more robust controls and layout templates for your UWP apps.</span></span>

### <a name="dashboard-monetization-and-store-services"></a><span data-ttu-id="d4db1-130">Dashboard, Monetarisierung und Store-Dienste</span><span class="sxs-lookup"><span data-stu-id="d4db1-130">Dashboard, monetization and Store services</span></span>

<span data-ttu-id="d4db1-131">Die folgenden neuen Features sind nun verfügbar:</span><span class="sxs-lookup"><span data-stu-id="d4db1-131">The following new features are now available:</span></span>

* <span data-ttu-id="d4db1-132">Das Microsoft Advertising-SDK ermöglicht nun die Darstellung [nativer Anzeigen](../monetize/native-ads.md) in Ihren Apps.</span><span class="sxs-lookup"><span data-stu-id="d4db1-132">The Microsoft Advertising SDK now enables you to show [native ads](../monetize/native-ads.md) in your apps.</span></span> <span data-ttu-id="d4db1-133">Eine native Anzeige ist ein komponentengestütztes Anzeigenformat, bei dem jedes Element der Anzeige (Titel, Bild, Beschreibung und Handlungsaufforderungstext) eigenständig an Ihre App übermittelt wird.</span><span class="sxs-lookup"><span data-stu-id="d4db1-133">A native ad is a component-based ad format where each piece of the ad creative (such as the title, image, description, and call-to-action text) is delivered to your app as an individual element.</span></span> <span data-ttu-id="d4db1-134">Native Anzeigen sind zurzeit nur für Entwickler in einem Pilotprogramm verfügbar, aber wir beabsichtigen, dieses Feature bald allen Entwicklern zur Verfügung zu stellen.</span><span class="sxs-lookup"><span data-stu-id="d4db1-134">Native ads are currently only available to developers who join a pilot program, but we intend to make this feature available to all developers soon.</span></span>

* <span data-ttu-id="d4db1-135">Die [Microsoft Store-Analyse-API](../monetize/access-analytics-data-using-windows-store-services.md) verfügt nun über eine Methode, um die [CAB-Datei für einen App-Fehler herunterzuladen](../monetize/download-the-cab-file-for-an-error-in-your-app.md).</span><span class="sxs-lookup"><span data-stu-id="d4db1-135">The [Microsoft Store analytics API](../monetize/access-analytics-data-using-windows-store-services.md) now provides a method you can use to [download the CAB file for an error in your app](../monetize/download-the-cab-file-for-an-error-in-your-app.md).</span></span>

* <span data-ttu-id="d4db1-136">Mit [gezielten Angeboten](../publish/use-targeted-offers-to-maximize-engagement-and-conversions.md) können Sie bestimmte Kundensegmente mit attraktivem, personalisiertem Inhalt ansprechen, um Kundenbindung und Monetarisierung zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="d4db1-136">[Targeted offers](../publish/use-targeted-offers-to-maximize-engagement-and-conversions.md) let you target specific segments of your customers with attractive, personalized content to increase engagement, retention, and monetization.</span></span> 

* <span data-ttu-id="d4db1-137">Der Store-Eintrag für Ihre App kann nun [Videotrailer](../publish/app-screenshots-and-images.md#trailers) enthalten.</span><span class="sxs-lookup"><span data-stu-id="d4db1-137">Your app's Store listing can now include [video trailers](../publish/app-screenshots-and-images.md#trailers).</span></span>

* <span data-ttu-id="d4db1-138">Mit neuen Optionen für Preisgestaltung und Verfügbarkeit können Sie [Preisänderungen planen](../publish/set-and-schedule-app-pricing.md) und [genaue Freigabetermine festlegen](..//publish/configure-precise-release-scheduling.md).</span><span class="sxs-lookup"><span data-stu-id="d4db1-138">New pricing and availability options let you [schedule price changes](../publish/set-and-schedule-app-pricing.md) and [set precise release dates](..//publish/configure-precise-release-scheduling.md).</span></span>

* <span data-ttu-id="d4db1-139">Sie können einen [Store-Eintrag importieren und exportieren](../publish/import-and-export-store-listings.md) und damit Updates beschleunigen, insbesondere dann, wenn Sie über Einträge in vielen Sprachen verfügen.</span><span class="sxs-lookup"><span data-stu-id="d4db1-139">You can [import and export Store listings](../publish/import-and-export-store-listings.md) to make updates faster, especially if you have listings in many languages.</span></span>

### <a name="my-people"></a><span data-ttu-id="d4db1-140">Meine Kontakte</span><span class="sxs-lookup"><span data-stu-id="d4db1-140">My People</span></span>

<span data-ttu-id="d4db1-141">Das neue Feature „Meine Kontakte” ist für [Windows-Insider](https://insider.windows.com/) in SDK Preview-Builds verfügbar. Damit können Benutzer Kontakte aus einer Anwendung direkt an die Taskleiste anheften.</span><span class="sxs-lookup"><span data-stu-id="d4db1-141">Available to [Windows Insiders](https://insider.windows.com/) in SDK Preview Builds, the upcoming My People feature allows users to pin contacts from an application directly to their taskbar.</span></span> [<span data-ttu-id="d4db1-142">Erfahren Sie, wie Sie „Meine Kontakte” in Ihre Anwendung einfügen.</span><span class="sxs-lookup"><span data-stu-id="d4db1-142">Learn how to add My People support to your application.</span></span>](../contacts-and-calendar/my-people-support.md)

![„Meine Kontakte”-Kontaktliste](images/my-people.png)

<span data-ttu-id="d4db1-144">Mit [Für meine Kontakte freigeben](../contacts-and-calendar/my-people-sharing.md) können Benutzer Dateien mithilfe Ihrer Anwendung direkt über die Taskleiste freigeben.</span><span class="sxs-lookup"><span data-stu-id="d4db1-144">[My People sharing](../contacts-and-calendar/my-people-sharing.md) allows users to share files through your application, right from the taskbar.</span></span>

![Für meine Kontakte freigeben](images/my-people-sharing.png)

<span data-ttu-id="d4db1-146">[Benachrichtigungen für Meine Kontakte](../contacts-and-calendar/my-people-support.md) sind eine neue Art von Popupbenachrichtigungen, die Benutzer an ihre angehefteten Kontakte senden können.</span><span class="sxs-lookup"><span data-stu-id="d4db1-146">[My People notifications](../contacts-and-calendar/my-people-support.md) are a new kind of toast notification that users can send to their pinned contacts.</span></span>

![Benachrichtigungen für Meine Kontakte](images/my-people-notification.png)

### <a name="pin-to-taskbar"></a><span data-ttu-id="d4db1-148">An Taskleiste anheften</span><span class="sxs-lookup"><span data-stu-id="d4db1-148">Pin to Taskbar</span></span>

<span data-ttu-id="d4db1-149">Die neue TaskbarManager-Klasse ist für [Windows-Insider](https://insider.windows.com/) in SDK Preview-Builds verfügbar. Sie können Benutzer damit auffordern, [die App an die Taskleiste anzuheften](../design/shell/pin-to-taskbar.md).</span><span class="sxs-lookup"><span data-stu-id="d4db1-149">Available to [Windows Insiders](https://insider.windows.com/) in SDK Preview Builds, the new TaskbarManager class allows you to ask your user to [pin your app to the taskbar](../design/shell/pin-to-taskbar.md).</span></span>

## <a name="developer-guidance"></a><span data-ttu-id="d4db1-150">Anleitungen für Entwickler</span><span class="sxs-lookup"><span data-stu-id="d4db1-150">Developer Guidance</span></span>

### <a name="media-playback"></a><span data-ttu-id="d4db1-151">Medienwiedergabe</span><span class="sxs-lookup"><span data-stu-id="d4db1-151">Media Playback</span></span>

<span data-ttu-id="d4db1-152">Dem grundlegenden Artikel [Wiedergeben von Audio- und Videoinhalten mit MediaPlayer](../audio-video-camera/play-audio-and-video-with-mediaplayer.md) wurden neue Abschnitte hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="d4db1-152">New sections have been added to the basic media playback article, [Play audio and video with MediaPlayer](../audio-video-camera/play-audio-and-video-with-mediaplayer.md).</span></span> <span data-ttu-id="d4db1-153">Im Abschnitt [Wiedergeben von sphärischen Videos mit MediaPlayer](../audio-video-camera/play-audio-and-video-with-mediaplayer.md) wird gezeigt, wie Sie sphärisch codiertes Videomaterial wiedergeben und Sichtfeld sowie Ausrichtung für unterstützte Videoformate anpassen.</span><span class="sxs-lookup"><span data-stu-id="d4db1-153">The section [Play spherical video with MediaPlayer](../audio-video-camera/play-audio-and-video-with-mediaplayer.md) shows you how to playback spherically encodeded video, including adjusting the field of view and view orientation for supported formats.</span></span> <span data-ttu-id="d4db1-154">Der Abschnitt [Verwenden von MediaPlayer im Frame-Server-Modus](../audio-video-camera/play-audio-and-video-with-mediaplayer.md#use-mediaplayer-in-frame-server-mode) erläutert, wie Sie Frames aus einer Medienwiedergabe mit [MediaPlayer](https://docs.microsoft.com/uwp/api/Windows.Media.Playback.MediaPlayer) auf eine Direct3D-Oberfläche kopieren.</span><span class="sxs-lookup"><span data-stu-id="d4db1-154">The section [Use MediaPlayer in frame server mode](../audio-video-camera/play-audio-and-video-with-mediaplayer.md#use-mediaplayer-in-frame-server-mode) shows you how to copy frames from media played back with [MediaPlayer](https://docs.microsoft.com/uwp/api/Windows.Media.Playback.MediaPlayer) to a Direct3D surface.</span></span> <span data-ttu-id="d4db1-155">Dies ermöglicht Szenarien wie z.B. das Anwenden von Echtzeiteffekten mit Pixel-Shadern.</span><span class="sxs-lookup"><span data-stu-id="d4db1-155">This enables scenarios such as applying real-time effects with pixel shaders.</span></span> <span data-ttu-id="d4db1-156">Der Beispielcode zeigt die schnelle Implementierung eines Weichzeichnereffekts für die Wiedergabe von Videos mithilfe von Win2D.</span><span class="sxs-lookup"><span data-stu-id="d4db1-156">The example code shows a quick implementation of a blur effect for video playback using Win2D.</span></span>

### <a name="media-capture"></a><span data-ttu-id="d4db1-157">Medienerfassung</span><span class="sxs-lookup"><span data-stu-id="d4db1-157">Media Capture</span></span>

<span data-ttu-id="d4db1-158">Der Artikel [Verarbeiten von Medienframes mit MediaFrameReader](../audio-video-camera/process-media-frames-with-mediaframereader.md) wurde aktualisiert, um die Verwendung der neuen Klasse [MultiSourceMediaFrameReader](https://docs.microsoft.com/uwp/api/windows.media.capture.frames.multisourcemediaframereader) zu erläutern, mit deren Hilfe Sie zeitkorrelierte Frames aus mehreren Medienquellen abrufen können.</span><span class="sxs-lookup"><span data-stu-id="d4db1-158">The article [Process media frames with MediaFrameReader](../audio-video-camera/process-media-frames-with-mediaframereader.md) has been updated to show the usage of the new [MultiSourceMediaFrameReader](https://docs.microsoft.com/uwp/api/windows.media.capture.frames.multisourcemediaframereader) class, which allows you to obtain time-correlated frames from multiple media sources.</span></span> <span data-ttu-id="d4db1-159">Dies ist hilfreich, wenn Sie Frames aus anderen Quellen wie einer Tiefenkamera oder Farbkamera verarbeiten und dabei sicherstellen müssen, dass die Frames aus jeder Quelle zeitnah zueinander erfasst wurden.</span><span class="sxs-lookup"><span data-stu-id="d4db1-159">This is useful if you need to process frames from different sources, such as a depth camera and an color camera, and you need to make sure that the frames from each source were captured close to each other in time.</span></span> <span data-ttu-id="d4db1-160">Weitere Informationen finden Sie unter [Verwenden von MultiSourceMediaFrameReader zum Abrufen zeitkorrelierter Frames aus mehreren Quellen](../audio-video-camera/process-media-frames-with-mediaframereader.md#use-multisourcemediaframereader-to-get-time-corellated-frames-from-multiple-sources).</span><span class="sxs-lookup"><span data-stu-id="d4db1-160">For more information, see [Use MultiSourceMediaFrameReader to get time-corellated frames from multiple sources](../audio-video-camera/process-media-frames-with-mediaframereader.md#use-multisourcemediaframereader-to-get-time-corellated-frames-from-multiple-sources).</span></span>

### <a name="scoped-search"></a><span data-ttu-id="d4db1-161">Begrenzter Suchbereich</span><span class="sxs-lookup"><span data-stu-id="d4db1-161">Scoped Search</span></span>

<span data-ttu-id="d4db1-162">Der [konzeptionellen UWP-Dokumentation](../get-started/universal-application-platform-guide.md) und der [API-Referenz](https://docs.microsoft.com/en-us/uwp/api/) auf docs.microsoft.com wurde der Bereich „UWP” hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="d4db1-162">A "UWP" scope has been added to the [UWP conceptual](../get-started/universal-application-platform-guide.md) and [API reference](https://docs.microsoft.com/en-us/uwp/api/) documentation on docs.microsoft.com.</span></span> <span data-ttu-id="d4db1-163">Bis dieser Bereich deaktiviert ist, liefern Suchvorgänge in diesen Umgebungen nur UWP-Dokumente.</span><span class="sxs-lookup"><span data-stu-id="d4db1-163">Unless this scope is deactivated, searches made from within these areas will return UWP docs only.</span></span>

![Begrenzter Suchbereich](images/scoped-search.png)

### <a name="test-your-windows-app-for-windows-10-s"></a><span data-ttu-id="d4db1-165">Testen Ihrer Windows-App für Windows10 S</span><span class="sxs-lookup"><span data-stu-id="d4db1-165">Test your Windows app for Windows 10 S</span></span>

<span data-ttu-id="d4db1-166">Testen Sie Ihre Windows-App, um sicherzustellen, dass sie korrekt auf Geräten unter Windows S ausgeführt wird. Anleitungen dazu finden Sie in [diesem neuen Handbuch](../porting/desktop-to-uwp-test-windows-s.md).</span><span class="sxs-lookup"><span data-stu-id="d4db1-166">Test your Windows app to ensure that it will operate correctly on devices that run Windows S. Use [this new guide](../porting/desktop-to-uwp-test-windows-s.md) to learn how.</span></span> 

## <a name="samples"></a><span data-ttu-id="d4db1-167">Beispiele</span><span class="sxs-lookup"><span data-stu-id="d4db1-167">Samples</span></span>

### <a name="annotated-audio-app-sample"></a><span data-ttu-id="d4db1-168">Beispiel für eine kommentierte Audio-App</span><span class="sxs-lookup"><span data-stu-id="d4db1-168">Annotated audio app sample</span></span>

<span data-ttu-id="d4db1-169">[Ein Beispiel für eine Mini-App mit Audio-, Freihand- und OneDrive-Datenroamingszenarien.](https://github.com/Microsoft/Windows-appsample-annotated-audio)</span><span class="sxs-lookup"><span data-stu-id="d4db1-169">[A mini-app sample that demonstrates audio, ink, and OneDrive data roaming scenarios](https://github.com/Microsoft/Windows-appsample-annotated-audio).</span></span> <span data-ttu-id="d4db1-170">Dieses Beispiel zeichnet Audio auf und erlaubt gleichzeitig die synchronisierte Erfassung von Freihandanmerkungen, sodass Sie später nachvollziehen können, was besprochen wurde, als Sie die Notiz erstellt haben</span><span class="sxs-lookup"><span data-stu-id="d4db1-170">This sample records audio while allowing the synchronized capture of ink annotations so that you can later recall what was being discussed at the time a note was taken.</span></span>

![Bildschirmfoto der kommentierten Audioaufzeichnung](images/Playback.png)  

### <a name="shopping-app-sample"></a><span data-ttu-id="d4db1-172">Beispiel für eine Shopping-App</span><span class="sxs-lookup"><span data-stu-id="d4db1-172">Shopping app sample</span></span>

<span data-ttu-id="d4db1-173">[Ein Mini-App für einen einfachen Einkaufsvorgang, bei dem ein Benutzer Emojis erwerben kann](https://github.com/Microsoft/Windows-appsample-shopping).</span><span class="sxs-lookup"><span data-stu-id="d4db1-173">[A mini-app that presents a basic shopping experience where a user can buy emoji](https://github.com/Microsoft/Windows-appsample-shopping).</span></span> <span data-ttu-id="d4db1-174">Diese App veranschaulicht, wie die Kaufabwicklung mit den [Payment Request-APIs](https://docs.microsoft.com/uwp/api/windows.applicationmodel.payments) zu implementieren ist.</span><span class="sxs-lookup"><span data-stu-id="d4db1-174">This app shows how to use the [Payment Request APIs](https://docs.microsoft.com/uwp/api/windows.applicationmodel.payments) to implement the checkout experience.</span></span>

![Bildschirmfoto des Shopping-App-Beispiels](images/shoppingcart.png)  

## <a name="videos"></a><span data-ttu-id="d4db1-176">Videos</span><span class="sxs-lookup"><span data-stu-id="d4db1-176">Videos</span></span>

### <a name="accessibility"></a><span data-ttu-id="d4db1-177">Bedienungshilfen</span><span class="sxs-lookup"><span data-stu-id="d4db1-177">Accessibility</span></span>

<span data-ttu-id="d4db1-178">Durch Bedienungshilfen in Ihren Apps erreichen Sie viel größere Zielgruppen.</span><span class="sxs-lookup"><span data-stu-id="d4db1-178">Building accessibility into your apps opens them up to a much wider audience.</span></span> <span data-ttu-id="d4db1-179">[Sehen Sie sich das Video an](https://channel9.msdn.com/Blogs/One-Dev-Minute/Developing-Apps-for-Accessibility), und erfahren Sie dann mehr über das [Entwickeln von Apps mit Barrierefreiheit](https://developer.microsoft.com/en-us/windows/accessible-apps).</span><span class="sxs-lookup"><span data-stu-id="d4db1-179">[Watch the video](https://channel9.msdn.com/Blogs/One-Dev-Minute/Developing-Apps-for-Accessibility), then learn more about [developing apps for accessibility](https://developer.microsoft.com/en-us/windows/accessible-apps).</span></span>

### <a name="payments-request-api"></a><span data-ttu-id="d4db1-180">Payments Request-API</span><span class="sxs-lookup"><span data-stu-id="d4db1-180">Payments Request API</span></span>

<span data-ttu-id="d4db1-181">Die Payment Request-API ermöglicht Kunden und Verkäufern eine nahtlose, verbesserte Onlineverkaufsabwicklung.</span><span class="sxs-lookup"><span data-stu-id="d4db1-181">The Payment Request API helps custoemrs and sellers seamlessly complete the online checkout process.</span></span> <span data-ttu-id="d4db1-182">[Sehen Sie sich das Video](https://channel9.msdn.com/Blogs/One-Dev-Minute/Using-the-Payments-Request-API), und lesen Sie anschließend die [Payment Request-Dokumentation](https://channel9.msdn.com/Blogs/One-Dev-Minute/Using-the-Payments-Request-API).</span><span class="sxs-lookup"><span data-stu-id="d4db1-182">[Watch the video](https://channel9.msdn.com/Blogs/One-Dev-Minute/Using-the-Payments-Request-API), then explore the [Payment Request documentation](https://channel9.msdn.com/Blogs/One-Dev-Minute/Using-the-Payments-Request-API).</span></span>

### <a name="windows-10-iot-core"></a><span data-ttu-id="d4db1-183">Windows10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="d4db1-183">Windows 10 IoT Core</span></span>

<span data-ttu-id="d4db1-184">Windows10 IoT Core und die Universelle Windows-Plattform ermöglichen, schnell Prototypen und Projekte mit unterschiedlichen Komponenten zu erstellen. Ein Beispiel ist diese Tür, die Ihr Haustier erkennt.</span><span class="sxs-lookup"><span data-stu-id="d4db1-184">With Windows 10 IoT Core and the Universal Windows Platform, you can quickly protoype and build projects with vision and component connections, such as this Pet Recognition Door.</span></span> <span data-ttu-id="d4db1-185">[Sehen Sie sich das Video an](https://channel9.msdn.com/Blogs/One-Dev-Minute/Building-a-Pet-Recognition-Door-Using-Windows-10-IoT-Core), und erfahren Sie dann mehr über [erste Schrittemit Windows10 IoT Core](https://developer.microsoft.com/en-us/windows/iot).</span><span class="sxs-lookup"><span data-stu-id="d4db1-185">[Watch the video](https://channel9.msdn.com/Blogs/One-Dev-Minute/Building-a-Pet-Recognition-Door-Using-Windows-10-IoT-Core), then learn more about how to [get started with Windows 10 IoT Core](https://developer.microsoft.com/en-us/windows/iot).</span></span>