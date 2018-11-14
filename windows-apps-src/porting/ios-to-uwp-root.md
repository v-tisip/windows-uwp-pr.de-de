---
author: stevewhims
description: Wechsel von iOS zu UWP
Search.SourceType: Video
title: Wechsel von iOS zu UWP
ms.assetid: 7a05751d-02df-4240-9ba5-d95f65a7a9c5
ms.author: stwhi
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: c769876b13eede84a776676aed69274d34e4bbbf
ms.sourcegitcommit: bdc40b08cbcd46fc379feeda3c63204290e055af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/08/2018
ms.locfileid: "6157172"
---
# <a name="move-from-ios-to-uwp"></a><span data-ttu-id="5d72d-104">Wechsel von iOS zu UWP</span><span class="sxs-lookup"><span data-stu-id="5d72d-104">Move from iOS to UWP</span></span>

<span data-ttu-id="5d72d-105">Wenn Sie ein iOS-Entwickler sind und sich fragen, wie Sie Ihre Benutzerbasis auf Windows10 und die universelle Windows-Plattform (UWP) erweitern können, dann gibt es eine zunehmende Zahl von Tools, die Sie dabei unterstützen können.</span><span class="sxs-lookup"><span data-stu-id="5d72d-105">If you are an iOS developer wondering how to expand your user base to include Windows 10 and the Universal Windows Platform (UWP), there are a growing number of tools to help you.</span></span> <span data-ttu-id="5d72d-106">Die Methoden, die Sie anwenden können, sind von der Art der App, an der Sie arbeiten (Spiel, Lifestyle, Unternehmen usw.) und davon abhängig, in welcher Phase des Entwicklungsprozesses Sie sich befinden.</span><span class="sxs-lookup"><span data-stu-id="5d72d-106">The approaches you can take depend on the type of app you are working on (game, lifestyle, enterprise, and so on) and how far along you are in the development process.</span></span> <span data-ttu-id="5d72d-107">Beispielsweise ist ein fertiges oder beinahe fertiges Spiel, das in hohem Maß von OpenGL oder Cocos2D abhängig ist, ein idealer Kandidat für die [Windows-Brücke für iOS](https://dev.windows.com/bridges/ios). Wenn Sie jedoch eine plattformübergreifende App für ein kleines Unternehmen planen, sollten Sie [Xamarin.Forms](https://www.xamarin.com/forms) in Betracht ziehen.</span><span class="sxs-lookup"><span data-stu-id="5d72d-107">For example, a completed or nearly completed game that is heavily dependent on OpenGL or Cocos2D is an ideal candidate for the [Windows Bridge for iOS](https://dev.windows.com/bridges/ios), whereas if you are planning a cross-platform app for a small business, you should be considering using [Xamarin.Forms](https://www.xamarin.com/forms).</span></span> <span data-ttu-id="5d72d-108">Wenn Sie Ihre App in einem plattformübergreifenden Tool wie Unity geschrieben haben, ist die [Veröffentlichung für Windows](http://blogs.unity3d.com/2015/09/09/windows-10-universal-apps-in-unity-5-2/) ziemlich einfach.</span><span class="sxs-lookup"><span data-stu-id="5d72d-108">And if you have written your app in a cross-platform tool such as Unity, [publishing to Windows](http://blogs.unity3d.com/2015/09/09/windows-10-universal-apps-in-unity-5-2/) is quite straightforward.</span></span>

## <a name="why-windows"></a><span data-ttu-id="5d72d-109">Weshalb Windows?</span><span class="sxs-lookup"><span data-stu-id="5d72d-109">Why Windows?</span></span>

<span data-ttu-id="5d72d-110">Windows wird heute auf einer großen Anzahl von Geräten ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="5d72d-110">Today, Windows is running on a huge number of devices.</span></span> <span data-ttu-id="5d72d-111">Die UWP bietet Entwicklern eine Reihe moderner APIs, mit denen sie äußerst reaktionsfähige Benutzeroberflächen für so unterschiedliche Geräte wie Desktopcomputer, Spielekonsolen und holographische Displays entwickeln können.</span><span class="sxs-lookup"><span data-stu-id="5d72d-111">The UWP provides developers with a set of modern APIs, designed to create beautifully responsive user interfaces across devices as diverse as desktop computers, games consoles and holographic displays.</span></span> <span data-ttu-id="5d72d-112">Dank einer zentralen Visual Studio-Lösung und Benutzeroberflächen-Steuerelementen, die intelligent genug sind, um sich selbst für unterschiedliche Plattformen zu optimieren, werden Sie häufig feststellen, dass Sie weniger Code schreiben und diesen auf einer größeren Zahl von Hardwaregeräten ausführen.</span><span class="sxs-lookup"><span data-stu-id="5d72d-112">With one Visual Studio solution, and with user interface controls that are smart enough to automatically optimize themselves for multiple platforms , you'll often find that you are writing less code and running it on more hardware.</span></span>

> [!VIDEO https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-Convert-your-iOS-app-to-Windows/player]

| <span data-ttu-id="5d72d-113">Thema</span><span class="sxs-lookup"><span data-stu-id="5d72d-113">Topic</span></span> | <span data-ttu-id="5d72d-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5d72d-114">Description</span></span> |
|-------|-------------|
| [<span data-ttu-id="5d72d-115">Auswählen eines Ansatzes für die Entwicklung von iOS- und UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="5d72d-115">Selecting an approach to iOS and UWP app development</span></span>](selecting-an-approach-to-ios-and-uwp-app-development.md) | <span data-ttu-id="5d72d-116">Welche Optionen gibt es beim Entwickeln von plattformübergreifenden Apps?</span><span class="sxs-lookup"><span data-stu-id="5d72d-116">What are the choices when developing cross-platform apps?</span></span> |
| [<span data-ttu-id="5d72d-117">Erste Schritte mit UWP für iOS-Entwickler</span><span class="sxs-lookup"><span data-stu-id="5d72d-117">Getting started with UWP for iOS developers</span></span>](getting-started-with-uwp-for-ios-developers.md) | <span data-ttu-id="5d72d-118">Wenn Sie iOS-Entwickler sind und die Entwicklung für Windows10 in Erwägung ziehen, bieten diese Dokumente einen sehr guten Einstieg.</span><span class="sxs-lookup"><span data-stu-id="5d72d-118">If you're an iOS developer considering developing for Windows 10, these docs are a great place to start.</span></span> |
| [<span data-ttu-id="5d72d-119">Einrichten von Windows 10 auf Ihrem Mac</span><span class="sxs-lookup"><span data-stu-id="5d72d-119">Setting up your Mac with Windows 10</span></span>](setting-up-your-mac-with-windows-10.md) | <span data-ttu-id="5d72d-120">Verwenden Sie Ihren aktuellen Mac-Computer zum Entwickeln von Apps für Windows.</span><span class="sxs-lookup"><span data-stu-id="5d72d-120">Use your current Mac computer to develop apps for Windows.</span></span> |

## <a name="related-topics"></a><span data-ttu-id="5d72d-121">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="5d72d-121">Related topics</span></span>

**<span data-ttu-id="5d72d-122">Für Designer und Entwickler</span><span class="sxs-lookup"><span data-stu-id="5d72d-122">For designers and developers</span></span>**
* [<span data-ttu-id="5d72d-123">Erstellen Universeller Windows-Apps für alle Windows-Geräte</span><span class="sxs-lookup"><span data-stu-id="5d72d-123">Building Universal Windows apps for all Windows devices</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=397871)
* [<span data-ttu-id="5d72d-124">Herunterladen von Designobjekten für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="5d72d-124">Download design assets for UWP apps</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/bg125377.aspx)
