---
author: QuinnRadich
title: Bildschirm snipping starten
description: Dieses Thema beschreibt die ms-Screenclip und ms-Screensketch URI-Schemas. Ihre app kann diese URI-Schemas zum Starten der app Ausschnitt & Skizze oder öffnen Sie einen neuen Ausschnitt verwenden.
ms.author: quradic
ms.date: 8/1/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Uri, Ausschneiden, Skizze
ms.localizationpriority: medium
ms.openlocfilehash: e18662125ef72051a289b3f1d0f3dc09b452d256
ms.sourcegitcommit: e6daa7ff878f2f0c7015aca9787e7f2730abcfbf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2018
ms.locfileid: "4315708"
---
# <a name="launch-screen-snipping"></a><span data-ttu-id="60dbd-105">Bildschirm snipping starten</span><span class="sxs-lookup"><span data-stu-id="60dbd-105">Launch screen snipping</span></span>

<span data-ttu-id="60dbd-106">Die **ms-Screenclip:** und **ms-Screensketch:** URI-Schemas können Sie starten snipping oder Screenshots bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="60dbd-106">The **ms-screenclip:** and **ms-screensketch:** URI schemes allows you to initiate snipping or editing screenshots.</span></span>

## <a name="open-a-new-snip-from-your-app"></a><span data-ttu-id="60dbd-107">Öffnen Sie einen neuen Ausschnitt aus Ihrer app</span><span class="sxs-lookup"><span data-stu-id="60dbd-107">Open a new snip from your app</span></span>

<span data-ttu-id="60dbd-108">Die **ms-Screenclip:** URI kann Ihre app automatisch öffnen, und starten Sie einen neuen Ausschnitt.</span><span class="sxs-lookup"><span data-stu-id="60dbd-108">The **ms-screenclip:** URI allows your app to automatically open up and start a new snip.</span></span> <span data-ttu-id="60dbd-109">Der resultierende Ausschnitt wird in die Zwischenablage des Benutzers kopiert, jedoch nicht automatisch zurück an die öffnen-app übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="60dbd-109">The resulting snip is copied to the user's clipboard, but is not automatically passed back to the opening app.</span></span>

<span data-ttu-id="60dbd-110">**ms-Screenclip:** hat die folgenden Parameter:</span><span class="sxs-lookup"><span data-stu-id="60dbd-110">**ms-screenclip:** takes the following parameters:</span></span>

| <span data-ttu-id="60dbd-111">Parameter</span><span class="sxs-lookup"><span data-stu-id="60dbd-111">Parameter</span></span> | <span data-ttu-id="60dbd-112">Typ</span><span class="sxs-lookup"><span data-stu-id="60dbd-112">Type</span></span> | <span data-ttu-id="60dbd-113">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="60dbd-113">Required</span></span> | <span data-ttu-id="60dbd-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="60dbd-114">Description</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="60dbd-115">Quelle</span><span class="sxs-lookup"><span data-stu-id="60dbd-115">source</span></span> | <span data-ttu-id="60dbd-116">string</span><span class="sxs-lookup"><span data-stu-id="60dbd-116">string</span></span> | <span data-ttu-id="60dbd-117">Nein</span><span class="sxs-lookup"><span data-stu-id="60dbd-117">no</span></span> | <span data-ttu-id="60dbd-118">Eine formfreie Zeichenfolge an, dass die Quelle, die den URI gestartet.</span><span class="sxs-lookup"><span data-stu-id="60dbd-118">A freeform string to indicate the source that launched the URI.</span></span> |
| <span data-ttu-id="60dbd-119">delayInSeconds</span><span class="sxs-lookup"><span data-stu-id="60dbd-119">delayInSeconds</span></span> | <span data-ttu-id="60dbd-120">int</span><span class="sxs-lookup"><span data-stu-id="60dbd-120">int</span></span> | <span data-ttu-id="60dbd-121">nein</span><span class="sxs-lookup"><span data-stu-id="60dbd-121">no</span></span> | <span data-ttu-id="60dbd-122">Eine ganze Zahl von 1 bis zu 30.</span><span class="sxs-lookup"><span data-stu-id="60dbd-122">An integer value, from 1 to 30.</span></span> <span data-ttu-id="60dbd-123">Gibt die Verzögerung in vollständige Sekunden zwischen dem URI-Aufruf und wann snipping beginnt.</span><span class="sxs-lookup"><span data-stu-id="60dbd-123">Specifies the delay, in full seconds, between the URI call and when snipping begins.</span></span> |

## <a name="launching-the-snip--sketch-app"></a><span data-ttu-id="60dbd-124">Starten der Ausschnitt & Skizze App</span><span class="sxs-lookup"><span data-stu-id="60dbd-124">Launching the Snip & Sketch App</span></span>

<span data-ttu-id="60dbd-125">Die **ms-Screensketch:** URI können Sie programmgesteuert Starten der app Ausschnitt & Skizze, und öffnen Sie ein bestimmtes Bild in der app für Anmerkung.</span><span class="sxs-lookup"><span data-stu-id="60dbd-125">The **ms-screensketch:** URI allows you to programatically launch the Snip & Sketch app, and open a specific image in that app for annotation.</span></span>

<span data-ttu-id="60dbd-126">**ms-Screensketch:** hat die folgenden Parameter:</span><span class="sxs-lookup"><span data-stu-id="60dbd-126">**ms-screensketch:** takes the following parameters:</span></span>

| <span data-ttu-id="60dbd-127">Parameter</span><span class="sxs-lookup"><span data-stu-id="60dbd-127">Parameter</span></span> | <span data-ttu-id="60dbd-128">Typ</span><span class="sxs-lookup"><span data-stu-id="60dbd-128">Type</span></span> | <span data-ttu-id="60dbd-129">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="60dbd-129">Required</span></span> | <span data-ttu-id="60dbd-130">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="60dbd-130">Description</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="60dbd-131">sharedAccessToken</span><span class="sxs-lookup"><span data-stu-id="60dbd-131">sharedAccessToken</span></span> | <span data-ttu-id="60dbd-132">string</span><span class="sxs-lookup"><span data-stu-id="60dbd-132">string</span></span> | <span data-ttu-id="60dbd-133">Nein</span><span class="sxs-lookup"><span data-stu-id="60dbd-133">no</span></span> | <span data-ttu-id="60dbd-134">Ein Token, identifizieren die Datei in der app Ausschnitt & Skizze geöffnet.</span><span class="sxs-lookup"><span data-stu-id="60dbd-134">A token identifying the file to open in the Snip & Sketch app.</span></span> <span data-ttu-id="60dbd-135">Aus [SharedStorageAccessManager.AddFile](https://docs.microsoft.com/uwp/api/windows.applicationmodel.datatransfer.sharedstorageaccessmanager.addfile)abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="60dbd-135">Retrieved from [SharedStorageAccessManager.AddFile](https://docs.microsoft.com/uwp/api/windows.applicationmodel.datatransfer.sharedstorageaccessmanager.addfile).</span></span> <span data-ttu-id="60dbd-136">Wenn dieser Parameter ausgelassen wird, wird die app ohne Öffnen der Datei gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="60dbd-136">If this parameter is omitted, the app will be launched without a file open.</span></span> |
| <span data-ttu-id="60dbd-137">Quelle</span><span class="sxs-lookup"><span data-stu-id="60dbd-137">source</span></span> | <span data-ttu-id="60dbd-138">string</span><span class="sxs-lookup"><span data-stu-id="60dbd-138">string</span></span> | <span data-ttu-id="60dbd-139">Nein</span><span class="sxs-lookup"><span data-stu-id="60dbd-139">no</span></span> | <span data-ttu-id="60dbd-140">Eine formfreie Zeichenfolge an, dass die Quelle, die den URI gestartet.</span><span class="sxs-lookup"><span data-stu-id="60dbd-140">A freeform string to indicate the source that launched the URI.</span></span> |
| <span data-ttu-id="60dbd-141">isTemporary</span><span class="sxs-lookup"><span data-stu-id="60dbd-141">isTemporary</span></span> | <span data-ttu-id="60dbd-142">bool</span><span class="sxs-lookup"><span data-stu-id="60dbd-142">bool</span></span> | <span data-ttu-id="60dbd-143">nein</span><span class="sxs-lookup"><span data-stu-id="60dbd-143">no</span></span> | <span data-ttu-id="60dbd-144">Wenn auf True festgelegt, Bildschirmskizzen versucht, die Datei zu löschen, nachdem sie geöffnet.</span><span class="sxs-lookup"><span data-stu-id="60dbd-144">If set to True, Screen Sketch will try to delete the file after opening it.</span></span> |

<span data-ttu-id="60dbd-145">Das folgende Beispiel ruft die [LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_) -Methode, um ein Bild an Ausschnitt & Skizze aus der Benutzer die app zu senden.</span><span class="sxs-lookup"><span data-stu-id="60dbd-145">The following example calls the [LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_) method to send an image to Snip & Sketch from the user's app.</span></span>

```csharp

bool result = await Windows.System.Launcher.LaunchUriAsync(new Uri("ms-screensketch:edit?source=MyApp&isTemporary=false&sharedAccessToken=2C37ADDA-B054-40B5-8B38-11CED1E1A2D"));

```