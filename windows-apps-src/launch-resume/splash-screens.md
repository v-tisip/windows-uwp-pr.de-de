---
author: PatrickFarley
title: Begrüßungsbildschirme
description: In diesem Abschnitt werden Einrichten und Konfigurieren des Begrüßungsbildschirms einer App beschrieben.
ms.assetid: 6b954bb3-e5b0-46d1-8afc-fb805536cf6d
ms.author: pafarley
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 45609a0feb244f746fb8dfbf3dee0dacbe541fc6
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "5933694"
---
# <a name="splash-screens"></a><span data-ttu-id="83c80-104">Begrüßungsbildschirme</span><span class="sxs-lookup"><span data-stu-id="83c80-104">Splash screens</span></span>

<span data-ttu-id="83c80-105">Alle UWP-Apps müssen einen Begrüßungsbildschirm besitzen, der sich aus einem Bild und einer Hintergrundfarbe zusammensetzt. Beide Komponenten können angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="83c80-105">All UWP apps must have a splash screen, which is a composite of an image and a background color, both of which can be customized.</span></span>

<span data-ttu-id="83c80-106">Ihr Begrüßungsbildschirm wird sofort angezeigt, wenn Benutzer die App starten.</span><span class="sxs-lookup"><span data-stu-id="83c80-106">Your splash screen is displayed immediately when the user launches your app.</span></span> <span data-ttu-id="83c80-107">Dadurch erhalten die Benutzer eine sofortige Rückmeldung, während die App-Ressourcen initialisiert werden.</span><span class="sxs-lookup"><span data-stu-id="83c80-107">This provides immediate feedback to users while app resources are initialized.</span></span> <span data-ttu-id="83c80-108">Sobald die App bereit für Interaktionen ist, wird der Begrüßungsbildschirm geschlossen.</span><span class="sxs-lookup"><span data-stu-id="83c80-108">As soon as your app is ready for interaction, the splash screen is dismissed.</span></span>

<span data-ttu-id="83c80-109">Durch einen gut gestalteten Begrüßungsbildschirm kann Ihre App einladender wirken.</span><span class="sxs-lookup"><span data-stu-id="83c80-109">A well-designed splash screen can make your app more inviting.</span></span> <span data-ttu-id="83c80-110">Hier ist ein einfacher unauffälliger Begrüßungsbildschirm:</span><span class="sxs-lookup"><span data-stu-id="83c80-110">Here's a simple, understated splash screen:</span></span>

![Eine auf 75% skalierte Bildschirmaufnahme des Begrüßungsbildschirms aus dem Begrüßungsbildschirmbeispiel.](images/regularsplashscreen.png)

<span data-ttu-id="83c80-112">Dieser Begrüßungsbildschirm wird durch Kombinieren eines grünen Hintergrunds mit einem transparenten Hintergrundbild im PNG-Format erstellt.</span><span class="sxs-lookup"><span data-stu-id="83c80-112">This splash screen is created by combining a green background color with a transparent-background PNG image.</span></span>

<span data-ttu-id="83c80-113">Ein einfaches Bild mit einer Hintergrundfarbe sieht unabhängig von dem Gerät, auf dem Ihre App ausgeführt wird, gut aus.</span><span class="sxs-lookup"><span data-stu-id="83c80-113">A simple image with a background color looks good regardless of the device your app is running on.</span></span> <span data-ttu-id="83c80-114">Nur die Größe des Hintergrunds wird verändert, um verschiedene Bildschirmgrößen zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="83c80-114">Only the size of the background changes to compensate for a variety of screen sizes.</span></span> <span data-ttu-id="83c80-115">Ihr Bild bleibt stets unverändert.</span><span class="sxs-lookup"><span data-stu-id="83c80-115">Your image always remains intact.</span></span>

<span data-ttu-id="83c80-116">Außerdem können Sie mit der [**SplashScreen**](https://msdn.microsoft.com/library/windows/apps/br224763)-Klasse den Start Ihrer App anpassen.</span><span class="sxs-lookup"><span data-stu-id="83c80-116">Additionally, you can use the [**SplashScreen**](https://msdn.microsoft.com/library/windows/apps/br224763) class to customize your app's launch experience.</span></span> <span data-ttu-id="83c80-117">Sie können einen erweiterten, von Ihnen erstellten Begrüßungsbildschirm platzieren, damit Ihre App mehr Zeit für das Ausführen zusätzlicher Aufgaben, wie Vorbereiten der UI oder Abschließen von Netzwerkvorgängen, hat.</span><span class="sxs-lookup"><span data-stu-id="83c80-117">You can position an extended splash screen, which you create, to give your app more time to complete additional tasks like preparing app UI or completing networking operations.</span></span> <span data-ttu-id="83c80-118">Mit der **SplashScreen**-Klasse können Sie sich auch über das Schließen des Begrüßungsbildschirms benachrichtigen lassen, damit Sie Einführungsanimationen starten können.</span><span class="sxs-lookup"><span data-stu-id="83c80-118">You can also use the **SplashScreen** class to notify you when the splash screen is dismissed, so that you can begin entrance animations.</span></span>

| <span data-ttu-id="83c80-119">Thema</span><span class="sxs-lookup"><span data-stu-id="83c80-119">Topic</span></span> | <span data-ttu-id="83c80-120">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="83c80-120">Description</span></span> |
|-------|-------------|
| [<span data-ttu-id="83c80-121">Hinzufügen eines Begrüßungsbildschirms</span><span class="sxs-lookup"><span data-stu-id="83c80-121">Add a splash screen</span></span>](add-a-splash-screen.md) | <span data-ttu-id="83c80-122">Legen Sie das Bild und die Hintergrundfarbe des Begrüßungsbildschirms Ihrer App fest.</span><span class="sxs-lookup"><span data-stu-id="83c80-122">Set your app's splash screen image and background color.</span></span> |
| [<span data-ttu-id="83c80-123">Längere Anzeige des Begrüßungsbildschirms</span><span class="sxs-lookup"><span data-stu-id="83c80-123">Display a splash screen for more time</span></span>](create-a-customized-splash-screen.md) | <span data-ttu-id="83c80-124">Verlängern Sie die Anzeige eines Begrüßungsbildschirms, indem Sie für die App einen erweiterten Begrüßungsbildschirm erstellen.</span><span class="sxs-lookup"><span data-stu-id="83c80-124">Display a splash screen for more time by creating an extended splash screen for your app.</span></span> <span data-ttu-id="83c80-125">Mit diesem erweiterten Bildschirm wird der beim Starten der App angezeigte Begrüßungsbildschirm imitiert, der angepasst werden kann.</span><span class="sxs-lookup"><span data-stu-id="83c80-125">This extended screen imitates the splash screen shown when your app is launched, and can be customized.</span></span> |