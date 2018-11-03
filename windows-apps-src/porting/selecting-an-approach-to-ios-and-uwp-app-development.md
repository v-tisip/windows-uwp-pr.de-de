---
author: stevewhims
description: Welche Optionen gibt es beim Entwickeln von plattformübergreifenden Apps?
title: Auswählen eines Ansatzes für die Entwicklung von iOS- und UWP-Apps
ms.assetid: 5CDAB313-07B7-4A32-A49B-026361DCC853
ms.author: stwhi
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: c62624e83d1e8334cce711869088817e2f9dc5e0
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2018
ms.locfileid: "5995073"
---
# <a name="selecting-an-approach-to-ios-and-uwp-app-development"></a><span data-ttu-id="9b78b-104">Auswählen eines Ansatzes für die Entwicklung von iOS- und UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="9b78b-104">Selecting an approach to iOS and UWP app development</span></span>


<span data-ttu-id="9b78b-105">Welche Optionen gibt es beim Entwickeln von plattformübergreifenden Apps?</span><span class="sxs-lookup"><span data-stu-id="9b78b-105">What are the choices when developing cross-platform apps?</span></span>

## <a name="whats-the-best-way-to-support-both-ios-and-windows"></a><span data-ttu-id="9b78b-106">Wie werden iOS und Windows am besten unterstützt?</span><span class="sxs-lookup"><span data-stu-id="9b78b-106">What's the best way to support both iOS and Windows?</span></span>

<span data-ttu-id="9b78b-107">Windows und iOS sind anscheinend sehr unterschiedlich, es stehen jedoch immer mehr Tools und Methoden zur Verfügung, mit denen Sie Apps entwickeln können, die beide Plattformen (sowie Android) unterstützen.</span><span class="sxs-lookup"><span data-stu-id="9b78b-107">Windows and iOS may seem to be very different beasts, but a growing number of tools and techniques can greatly assist you if you need to write apps that support both platforms (and Android too).</span></span> <span data-ttu-id="9b78b-108">Die beste Lösung hängt vom Typ der App ab, die Sie entwickeln. Ausschlaggebend ist zudem auch, ob Sie die App von Grund auf neu erstellen oder ein vorhandenes Projekt portieren.</span><span class="sxs-lookup"><span data-stu-id="9b78b-108">The best solution depends on the type of app you are writing, and whether you are starting from scratch or porting an existing project.</span></span>

## <a name="writing-a-new-app"></a><span data-ttu-id="9b78b-109">Schreiben einer neuen App</span><span class="sxs-lookup"><span data-stu-id="9b78b-109">Writing a new app</span></span>

<span data-ttu-id="9b78b-110">Wenn Sie eine neue App erstellen, stehen zahlreiche Optionen zur Verfügung, u.a.:</span><span class="sxs-lookup"><span data-stu-id="9b78b-110">With a clean slate, you have many options at your disposal, including:</span></span>

-   [<span data-ttu-id="9b78b-111">Xamarin</span><span class="sxs-lookup"><span data-stu-id="9b78b-111">Xamarin</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=320484)

    <span data-ttu-id="9b78b-112">Mit Xamarin können Sie Ihre App in C# schreiben, sie unter Windows ausführen und zudem systemeigene iOS-Apps entwickeln.</span><span class="sxs-lookup"><span data-stu-id="9b78b-112">With Xamarin, you can write your app in C#, have it run on Windows, and create native iOS apps too.</span></span> <span data-ttu-id="9b78b-113">Unterstützung für Xamarin ist in Visual Studio integriert. Wählen Sie einfach den richtigen Projekttyp aus.</span><span class="sxs-lookup"><span data-stu-id="9b78b-113">Support for Xamarin is built into Visual Studio; just select the correct project type.</span></span>

-   [<span data-ttu-id="9b78b-114">Apache Cordova</span><span class="sxs-lookup"><span data-stu-id="9b78b-114">Apache Cordova</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=400439)

    <span data-ttu-id="9b78b-115">Falls Sie Javascript und HTML bevorzugen, unterstützt Sie Apache Cordova (auch als PhoneGap bezeichnet) beim Entwickeln plattformübergreifender Apps für iOS, Windows und Android.</span><span class="sxs-lookup"><span data-stu-id="9b78b-115">If Javascript and HTML is more your thing, Apache Cordova (aka PhoneGap) will help you create cross-platform apps for iOS, Windows, and Android.</span></span> <span data-ttu-id="9b78b-116">Dieser Projekttyp ist ebenfalls in Visual Studio integriert.</span><span class="sxs-lookup"><span data-stu-id="9b78b-116">This project type is also built into Visual Studio.</span></span>

-   <span data-ttu-id="9b78b-117">Spielengines</span><span class="sxs-lookup"><span data-stu-id="9b78b-117">Game-engines</span></span>

    <span data-ttu-id="9b78b-118">Mit Tools wie [Unity3D](http://go.microsoft.com/fwlink/p/?LinkID=320479) und [Unreal Engine](http://go.microsoft.com/fwlink/p/?LinkID=394062) können Sie Spiele in AAA-Qualität für Windows und zahlreiche andere Plattformen, einschließlich iOS, programmieren.</span><span class="sxs-lookup"><span data-stu-id="9b78b-118">With tools like [Unity3D](http://go.microsoft.com/fwlink/p/?LinkID=320479) and [Unreal Engine](http://go.microsoft.com/fwlink/p/?LinkID=394062) at your disposal, you can write AAA-quality games for Windows and many other platforms, including iOS.</span></span> <span data-ttu-id="9b78b-119">Unity unterstützt C#-Skripting, Unreal verwendet C++.</span><span class="sxs-lookup"><span data-stu-id="9b78b-119">Unity supports C# scripting; Unreal uses C++.</span></span>

-   [<span data-ttu-id="9b78b-120">MonoGame</span><span class="sxs-lookup"><span data-stu-id="9b78b-120">MonoGame</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=320483)

    <span data-ttu-id="9b78b-121">Der geistige Nachfolger von XNA.</span><span class="sxs-lookup"><span data-stu-id="9b78b-121">The spiritual successor to XNA.</span></span> <span data-ttu-id="9b78b-122">Nun handelt es sich dabei um ein plattformübergreifendes OpenSource-Framework. Das bedeutet, Sie können Apps in C# für zahlreiche Plattformen mit Unterstützung für Physik-Engines sowie 2D- und 3D-Grafiken schreiben.</span><span class="sxs-lookup"><span data-stu-id="9b78b-122">Now, it's an open-source cross-platform framework, which means you can write apps in C# for many platforms with support for physics engines, and 2D and 3D graphics.</span></span>

## <a name="adapting-an-existing-app"></a><span data-ttu-id="9b78b-123">Anpassen einer vorhandenen App</span><span class="sxs-lookup"><span data-stu-id="9b78b-123">Adapting an existing app</span></span>

<span data-ttu-id="9b78b-124">Bei einer vorhandenen iOS-App stehen weniger Optionen zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="9b78b-124">With an existing iOS app, your options are a little more limited.</span></span> <span data-ttu-id="9b78b-125">Es ist jedoch nicht alles verloren.</span><span class="sxs-lookup"><span data-stu-id="9b78b-125">However, all is most certainly not lost.</span></span>

-   [<span data-ttu-id="9b78b-126">Windows-Brücke für iOS</span><span class="sxs-lookup"><span data-stu-id="9b78b-126">Windows Bridge for iOS</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=619014)

    <span data-ttu-id="9b78b-127">Dieses noch in der Entwicklung befindliche Tool ist auch unter dem Namen „Projekt Islandwood“ bekannt. Mit ihm können Xcode-Projekte direkt in Visual Studio importiert werden.</span><span class="sxs-lookup"><span data-stu-id="9b78b-127">Also known as Project Islandwood, this is a still-in-development tool that can import Xcode projects directly into Visual Studio.</span></span> <span data-ttu-id="9b78b-128">Die Erstellung und das Debugging von Objective-C-Code kann in Visual Studio ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="9b78b-128">Objective-C code can be built and debugged from within Visual Studio.</span></span> <span data-ttu-id="9b78b-129">Falls Ihr Projekt Bibliotheken verwendet, beispielsweise Cocos für Grafiken, ist dies möglicherweise eine praktische Möglichkeit zum schnellen Portieren Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="9b78b-129">If your project makes use of libraries such as Cocos for graphics, you might find this a useful way to quickly port your app.</span></span>

-   <span data-ttu-id="9b78b-130">Sie können Ihren C++-Code wiederverwenden.</span><span class="sxs-lookup"><span data-stu-id="9b78b-130">Repurpose your C++ code.</span></span>

    <span data-ttu-id="9b78b-131">Wenn die Kerngeschäftslogik nicht in Objective-C oder Swift, sondern in C++ geschrieben ist, können Sie diesen Code häufig mit geringfügigen Änderungen in Ihrem Projekt verwenden.</span><span class="sxs-lookup"><span data-stu-id="9b78b-131">If your core business logic is written in C++, rather than Objective-C or Swift, you can often use this code with only minor changes in your project.</span></span> <span data-ttu-id="9b78b-132">Anschließend können Sie wie bei anderen Windows-Apps mithilfe von XAML die Benutzeroberfläche definieren und den C++-Code bei Bedarf nutzen.</span><span class="sxs-lookup"><span data-stu-id="9b78b-132">You can then use XAML to define your UI, as with other Windows apps, and call into the C++ code when necessary.</span></span>

-   [<span data-ttu-id="9b78b-133">Verwenden von ANGLE zum Ausführen von OpenGL ES unter Windows</span><span class="sxs-lookup"><span data-stu-id="9b78b-133">Use ANGLE to run OpenGL ES on Windows</span></span>](http://go.microsoft.com/fwlink/p/?linkid=618387)

    <span data-ttu-id="9b78b-134">Ein Zwischenschritt zum Portieren Ihres OpenGL ES2.0-Projekts ist die Verwendung von ANGLE.</span><span class="sxs-lookup"><span data-stu-id="9b78b-134">An intermediate step to porting your OpenGL ES 2.0 project is to use ANGLE.</span></span> <span data-ttu-id="9b78b-135">Mit ANGLE können Sie OpenGL ES-Inhalte unter Windows ausführen, indem Sie OpenGL ES-API-Aufrufe in DirectX11-API-Aufrufe übersetzen.</span><span class="sxs-lookup"><span data-stu-id="9b78b-135">ANGLE allows you to run OpenGL ES content on Windows by translating OpenGL ES API calls to DirectX 11 API calls.</span></span>

## <a name="other-cross-platform-authoring-tools"></a><span data-ttu-id="9b78b-136">Andere plattformübergreifende Erstellungstools</span><span class="sxs-lookup"><span data-stu-id="9b78b-136">Other cross-platform authoring tools</span></span>

-   [<span data-ttu-id="9b78b-137">GameSalad</span><span class="sxs-lookup"><span data-stu-id="9b78b-137">GameSalad</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=320480)

    <span data-ttu-id="9b78b-138">Eine Spielerstellungsumgebung</span><span class="sxs-lookup"><span data-stu-id="9b78b-138">A game authoring environment.</span></span>

-   [<span data-ttu-id="9b78b-139">Construct 2</span><span class="sxs-lookup"><span data-stu-id="9b78b-139">Construct 2</span></span>]( http://go.microsoft.com/fwlink/p/?LinkID=320481)

    <span data-ttu-id="9b78b-140">Eine Spielerstellungsumgebung</span><span class="sxs-lookup"><span data-stu-id="9b78b-140">A game authoring environment.</span></span>

-   [<span data-ttu-id="9b78b-141">Titanium Studio</span><span class="sxs-lookup"><span data-stu-id="9b78b-141">Titanium Studio</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=320482)

    <span data-ttu-id="9b78b-142">Eine plattformübergreifende Erstellungsumgebung</span><span class="sxs-lookup"><span data-stu-id="9b78b-142">A cross-platform authoring environment.</span></span>

-   [<span data-ttu-id="9b78b-143">Cocos2D-x</span><span class="sxs-lookup"><span data-stu-id="9b78b-143">Cocos2D-x</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=320485)

    <span data-ttu-id="9b78b-144">Eine plattformübergreifende Codebibliothek zur Spritebehandlung und Physikmodellierung</span><span class="sxs-lookup"><span data-stu-id="9b78b-144">A cross-platform code library for sprite handling and physics modeling.</span></span>

-   [<span data-ttu-id="9b78b-145">Impact.js</span><span class="sxs-lookup"><span data-stu-id="9b78b-145">Impact.js</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=320486)

    <span data-ttu-id="9b78b-146">Eine HTML-basierte Spielbibliothek.</span><span class="sxs-lookup"><span data-stu-id="9b78b-146">An HTML based game library.</span></span>

-   [<span data-ttu-id="9b78b-147">Marmalade</span><span class="sxs-lookup"><span data-stu-id="9b78b-147">Marmalade</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=320487)

    <span data-ttu-id="9b78b-148">Ein plattformübergreifendes SDK</span><span class="sxs-lookup"><span data-stu-id="9b78b-148">A cross-platform SDK.</span></span>

-   [<span data-ttu-id="9b78b-149">OpenFL</span><span class="sxs-lookup"><span data-stu-id="9b78b-149">OpenFL</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=320488)

    <span data-ttu-id="9b78b-150">Ein plattformübergreifendes Entwicklungstool</span><span class="sxs-lookup"><span data-stu-id="9b78b-150">A cross-platform development tool.</span></span>

-   [<span data-ttu-id="9b78b-151">GameMaker</span><span class="sxs-lookup"><span data-stu-id="9b78b-151">GameMaker</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=320490)

    <span data-ttu-id="9b78b-152">Eine spezielle Entwicklungsumgebung für Spiele</span><span class="sxs-lookup"><span data-stu-id="9b78b-152">An authoring environment specifically for games.</span></span>

-   [<span data-ttu-id="9b78b-153">PlayCanvas</span><span class="sxs-lookup"><span data-stu-id="9b78b-153">PlayCanvas</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=394061)

    <span data-ttu-id="9b78b-154">Ein HTML-basiertes Tool für die Spielentwicklung</span><span class="sxs-lookup"><span data-stu-id="9b78b-154">An HTML based game development tool.</span></span>

