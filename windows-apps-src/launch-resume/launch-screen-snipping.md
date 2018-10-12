---
author: QuinnRadich
title: Starten Sie Bildschirm snipping
description: In diesem Thema wird das ms-Screenclip und ms-Screensketch URI-Schemas. Ihre app kann diese URI-Schemas zum Starten der app Ausschnitt & Skizze oder um einen neuen Ausschnitt Öffnen verwenden.
ms.author: quradic
ms.date: 8/1/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Uri, Ausschneiden, Skizze
ms.localizationpriority: medium
ms.openlocfilehash: e18662125ef72051a289b3f1d0f3dc09b452d256
ms.sourcegitcommit: d10fb9eb5f75f2d10e1c543a177402b50fe4019e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "4566566"
---
# <a name="launch-screen-snipping"></a><span data-ttu-id="b9692-105">Starten Sie Bildschirm snipping</span><span class="sxs-lookup"><span data-stu-id="b9692-105">Launch screen snipping</span></span>

<span data-ttu-id="b9692-106">Die **ms-Screenclip:** und **ms-Screensketch:** URI-Schemas ermöglicht es Ihnen, snipping oder Bearbeiten von Screenshots zu initiieren.</span><span class="sxs-lookup"><span data-stu-id="b9692-106">The **ms-screenclip:** and **ms-screensketch:** URI schemes allows you to initiate snipping or editing screenshots.</span></span>

## <a name="open-a-new-snip-from-your-app"></a><span data-ttu-id="b9692-107">Öffnen Sie einen neuen Ausschnitt aus Ihrer app</span><span class="sxs-lookup"><span data-stu-id="b9692-107">Open a new snip from your app</span></span>

<span data-ttu-id="b9692-108">Die **ms-Screenclip:** URI kann Ihre app automatisch öffnen, und starten Sie einen neuen Ausschnitt.</span><span class="sxs-lookup"><span data-stu-id="b9692-108">The **ms-screenclip:** URI allows your app to automatically open up and start a new snip.</span></span> <span data-ttu-id="b9692-109">Die resultierende Ausschnitt wird in die Zwischenablage des Benutzers kopiert, jedoch nicht automatisch wieder an die öffnen-app übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="b9692-109">The resulting snip is copied to the user's clipboard, but is not automatically passed back to the opening app.</span></span>

<span data-ttu-id="b9692-110">**ms-Screenclip:** hat die folgenden Parameter:</span><span class="sxs-lookup"><span data-stu-id="b9692-110">**ms-screenclip:** takes the following parameters:</span></span>

| <span data-ttu-id="b9692-111">Parameter</span><span class="sxs-lookup"><span data-stu-id="b9692-111">Parameter</span></span> | <span data-ttu-id="b9692-112">Typ</span><span class="sxs-lookup"><span data-stu-id="b9692-112">Type</span></span> | <span data-ttu-id="b9692-113">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="b9692-113">Required</span></span> | <span data-ttu-id="b9692-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b9692-114">Description</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="b9692-115">Quelle</span><span class="sxs-lookup"><span data-stu-id="b9692-115">source</span></span> | <span data-ttu-id="b9692-116">string</span><span class="sxs-lookup"><span data-stu-id="b9692-116">string</span></span> | <span data-ttu-id="b9692-117">Nein</span><span class="sxs-lookup"><span data-stu-id="b9692-117">no</span></span> | <span data-ttu-id="b9692-118">Eine formfreie Zeichenfolge an, dass die Quelle, die den URI gestartet.</span><span class="sxs-lookup"><span data-stu-id="b9692-118">A freeform string to indicate the source that launched the URI.</span></span> |
| <span data-ttu-id="b9692-119">delayInSeconds</span><span class="sxs-lookup"><span data-stu-id="b9692-119">delayInSeconds</span></span> | <span data-ttu-id="b9692-120">int</span><span class="sxs-lookup"><span data-stu-id="b9692-120">int</span></span> | <span data-ttu-id="b9692-121">nein</span><span class="sxs-lookup"><span data-stu-id="b9692-121">no</span></span> | <span data-ttu-id="b9692-122">Eine ganze Zahl von 1 bis zu 30.</span><span class="sxs-lookup"><span data-stu-id="b9692-122">An integer value, from 1 to 30.</span></span> <span data-ttu-id="b9692-123">Gibt die Verzögerung in vollständige Sekunden zwischen der URI-Aufruf und wann beginnt snipping an.</span><span class="sxs-lookup"><span data-stu-id="b9692-123">Specifies the delay, in full seconds, between the URI call and when snipping begins.</span></span> |

## <a name="launching-the-snip--sketch-app"></a><span data-ttu-id="b9692-124">Starten der Ausschnitt & Skizze App</span><span class="sxs-lookup"><span data-stu-id="b9692-124">Launching the Snip & Sketch App</span></span>

<span data-ttu-id="b9692-125">Die **ms-Screensketch:** URI können Sie programmgesteuert Starten der app Ausschnitt & Skizze, und öffnen Sie ein bestimmtes Bild in der app für Anmerkung.</span><span class="sxs-lookup"><span data-stu-id="b9692-125">The **ms-screensketch:** URI allows you to programatically launch the Snip & Sketch app, and open a specific image in that app for annotation.</span></span>

<span data-ttu-id="b9692-126">**ms-Screensketch:** hat die folgenden Parameter:</span><span class="sxs-lookup"><span data-stu-id="b9692-126">**ms-screensketch:** takes the following parameters:</span></span>

| <span data-ttu-id="b9692-127">Parameter</span><span class="sxs-lookup"><span data-stu-id="b9692-127">Parameter</span></span> | <span data-ttu-id="b9692-128">Typ</span><span class="sxs-lookup"><span data-stu-id="b9692-128">Type</span></span> | <span data-ttu-id="b9692-129">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="b9692-129">Required</span></span> | <span data-ttu-id="b9692-130">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b9692-130">Description</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="b9692-131">sharedAccessToken</span><span class="sxs-lookup"><span data-stu-id="b9692-131">sharedAccessToken</span></span> | <span data-ttu-id="b9692-132">string</span><span class="sxs-lookup"><span data-stu-id="b9692-132">string</span></span> | <span data-ttu-id="b9692-133">Nein</span><span class="sxs-lookup"><span data-stu-id="b9692-133">no</span></span> | <span data-ttu-id="b9692-134">Ein Token, identifizieren die Datei in der app Ausschnitt & Skizze geöffnet.</span><span class="sxs-lookup"><span data-stu-id="b9692-134">A token identifying the file to open in the Snip & Sketch app.</span></span> <span data-ttu-id="b9692-135">Aus [SharedStorageAccessManager.AddFile](https://docs.microsoft.com/uwp/api/windows.applicationmodel.datatransfer.sharedstorageaccessmanager.addfile)abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="b9692-135">Retrieved from [SharedStorageAccessManager.AddFile](https://docs.microsoft.com/uwp/api/windows.applicationmodel.datatransfer.sharedstorageaccessmanager.addfile).</span></span> <span data-ttu-id="b9692-136">Wenn dieser Parameter ausgelassen wird, wird die app ohne Öffnen der Datei gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="b9692-136">If this parameter is omitted, the app will be launched without a file open.</span></span> |
| <span data-ttu-id="b9692-137">Quelle</span><span class="sxs-lookup"><span data-stu-id="b9692-137">source</span></span> | <span data-ttu-id="b9692-138">string</span><span class="sxs-lookup"><span data-stu-id="b9692-138">string</span></span> | <span data-ttu-id="b9692-139">Nein</span><span class="sxs-lookup"><span data-stu-id="b9692-139">no</span></span> | <span data-ttu-id="b9692-140">Eine formfreie Zeichenfolge an, dass die Quelle, die den URI gestartet.</span><span class="sxs-lookup"><span data-stu-id="b9692-140">A freeform string to indicate the source that launched the URI.</span></span> |
| <span data-ttu-id="b9692-141">isTemporary</span><span class="sxs-lookup"><span data-stu-id="b9692-141">isTemporary</span></span> | <span data-ttu-id="b9692-142">bool</span><span class="sxs-lookup"><span data-stu-id="b9692-142">bool</span></span> | <span data-ttu-id="b9692-143">nein</span><span class="sxs-lookup"><span data-stu-id="b9692-143">no</span></span> | <span data-ttu-id="b9692-144">Wenn auf True festgelegt, Bildschirmskizzen versucht, die Datei zu löschen, nachdem sie geöffnet.</span><span class="sxs-lookup"><span data-stu-id="b9692-144">If set to True, Screen Sketch will try to delete the file after opening it.</span></span> |

<span data-ttu-id="b9692-145">Das folgende Beispiel ruft die [LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_) -Methode, um ein Bild an Ausschnitt & Skizze aus der Benutzer app zu senden.</span><span class="sxs-lookup"><span data-stu-id="b9692-145">The following example calls the [LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_) method to send an image to Snip & Sketch from the user's app.</span></span>

```csharp

bool result = await Windows.System.Launcher.LaunchUriAsync(new Uri("ms-screensketch:edit?source=MyApp&isTemporary=false&sharedAccessToken=2C37ADDA-B054-40B5-8B38-11CED1E1A2D"));

```