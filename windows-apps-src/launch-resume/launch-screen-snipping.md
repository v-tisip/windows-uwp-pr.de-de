---
title: Ausschnitt & Skizze starten
description: Dieses Thema beschreibt die ms-Screenclip und ms-Screensketch URI-Schemas. Ihre app kann diese URI-Schemas zum Starten der app Ausschnitt & Skizze oder einen neuen Ausschnitt Öffnen verwenden.
ms.date: 8/1/2017
ms.topic: article
keywords: Windows 10, Uwp, Uri, Ausschneiden, Skizze
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 7aa0b70aee50c79088a68378fa75664711c3d564
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7850424"
---
# <a name="launch-screen-snipping"></a><span data-ttu-id="81a42-105">Ausschnitt & Skizze starten</span><span class="sxs-lookup"><span data-stu-id="81a42-105">Launch screen snipping</span></span>

<span data-ttu-id="81a42-106">Die **ms-Screenclip:** und **ms-Screensketch:** URI-Schemas können Sie starten snipping oder Screenshots bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="81a42-106">The **ms-screenclip:** and **ms-screensketch:** URI schemes allows you to initiate snipping or editing screenshots.</span></span>

## <a name="open-a-new-snip-from-your-app"></a><span data-ttu-id="81a42-107">Öffnen Sie einen neuen Ausschnitt aus Ihrer app</span><span class="sxs-lookup"><span data-stu-id="81a42-107">Open a new snip from your app</span></span>

<span data-ttu-id="81a42-108">Die **ms-Screenclip:** URI kann Ihre app automatisch öffnen, und starten Sie einen neuen Ausschnitt.</span><span class="sxs-lookup"><span data-stu-id="81a42-108">The **ms-screenclip:** URI allows your app to automatically open up and start a new snip.</span></span> <span data-ttu-id="81a42-109">Der resultierende Ausschnitt wird in die Zwischenablage des Benutzers kopiert, jedoch nicht automatisch zurück an die öffnen-app übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="81a42-109">The resulting snip is copied to the user's clipboard, but is not automatically passed back to the opening app.</span></span>

<span data-ttu-id="81a42-110">**ms-Screenclip:** hat die folgenden Parameter:</span><span class="sxs-lookup"><span data-stu-id="81a42-110">**ms-screenclip:** takes the following parameters:</span></span>

| <span data-ttu-id="81a42-111">Parameter</span><span class="sxs-lookup"><span data-stu-id="81a42-111">Parameter</span></span> | <span data-ttu-id="81a42-112">Typ</span><span class="sxs-lookup"><span data-stu-id="81a42-112">Type</span></span> | <span data-ttu-id="81a42-113">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="81a42-113">Required</span></span> | <span data-ttu-id="81a42-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="81a42-114">Description</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="81a42-115">Quelle</span><span class="sxs-lookup"><span data-stu-id="81a42-115">source</span></span> | <span data-ttu-id="81a42-116">string</span><span class="sxs-lookup"><span data-stu-id="81a42-116">string</span></span> | <span data-ttu-id="81a42-117">Nein</span><span class="sxs-lookup"><span data-stu-id="81a42-117">no</span></span> | <span data-ttu-id="81a42-118">Eine formfreie Zeichenfolge an, dass die Quelle, die den URI gestartet.</span><span class="sxs-lookup"><span data-stu-id="81a42-118">A freeform string to indicate the source that launched the URI.</span></span> |
| <span data-ttu-id="81a42-119">delayInSeconds</span><span class="sxs-lookup"><span data-stu-id="81a42-119">delayInSeconds</span></span> | <span data-ttu-id="81a42-120">int</span><span class="sxs-lookup"><span data-stu-id="81a42-120">int</span></span> | <span data-ttu-id="81a42-121">nein</span><span class="sxs-lookup"><span data-stu-id="81a42-121">no</span></span> | <span data-ttu-id="81a42-122">Eine ganze Zahl von 1 bis zu 30.</span><span class="sxs-lookup"><span data-stu-id="81a42-122">An integer value, from 1 to 30.</span></span> <span data-ttu-id="81a42-123">Gibt die Verzögerung in vollständige Sekunden zwischen dem URI-Aufruf und wann snipping beginnt.</span><span class="sxs-lookup"><span data-stu-id="81a42-123">Specifies the delay, in full seconds, between the URI call and when snipping begins.</span></span> |

## <a name="launching-the-snip--sketch-app"></a><span data-ttu-id="81a42-124">Starten der Ausschnitt & Skizze App</span><span class="sxs-lookup"><span data-stu-id="81a42-124">Launching the Snip & Sketch App</span></span>

<span data-ttu-id="81a42-125">Die **ms-Screensketch:** URI können Sie programmgesteuert Starten der app Ausschnitt & Skizze, und öffnen Sie ein bestimmtes Bild in der app für Anmerkung.</span><span class="sxs-lookup"><span data-stu-id="81a42-125">The **ms-screensketch:** URI allows you to programatically launch the Snip & Sketch app, and open a specific image in that app for annotation.</span></span>

<span data-ttu-id="81a42-126">**ms-Screensketch:** hat die folgenden Parameter:</span><span class="sxs-lookup"><span data-stu-id="81a42-126">**ms-screensketch:** takes the following parameters:</span></span>

| <span data-ttu-id="81a42-127">Parameter</span><span class="sxs-lookup"><span data-stu-id="81a42-127">Parameter</span></span> | <span data-ttu-id="81a42-128">Typ</span><span class="sxs-lookup"><span data-stu-id="81a42-128">Type</span></span> | <span data-ttu-id="81a42-129">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="81a42-129">Required</span></span> | <span data-ttu-id="81a42-130">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="81a42-130">Description</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="81a42-131">sharedAccessToken</span><span class="sxs-lookup"><span data-stu-id="81a42-131">sharedAccessToken</span></span> | <span data-ttu-id="81a42-132">string</span><span class="sxs-lookup"><span data-stu-id="81a42-132">string</span></span> | <span data-ttu-id="81a42-133">Nein</span><span class="sxs-lookup"><span data-stu-id="81a42-133">no</span></span> | <span data-ttu-id="81a42-134">Ein Token, identifizieren die Datei in der app Ausschnitt & Skizze geöffnet.</span><span class="sxs-lookup"><span data-stu-id="81a42-134">A token identifying the file to open in the Snip & Sketch app.</span></span> <span data-ttu-id="81a42-135">Aus [SharedStorageAccessManager.AddFile](https://docs.microsoft.com/uwp/api/windows.applicationmodel.datatransfer.sharedstorageaccessmanager.addfile)abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="81a42-135">Retrieved from [SharedStorageAccessManager.AddFile](https://docs.microsoft.com/uwp/api/windows.applicationmodel.datatransfer.sharedstorageaccessmanager.addfile).</span></span> <span data-ttu-id="81a42-136">Wenn dieser Parameter nicht angegeben ist, wird die app ohne Öffnen der Datei gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="81a42-136">If this parameter is omitted, the app will be launched without a file open.</span></span> |
| <span data-ttu-id="81a42-137">Quelle</span><span class="sxs-lookup"><span data-stu-id="81a42-137">source</span></span> | <span data-ttu-id="81a42-138">string</span><span class="sxs-lookup"><span data-stu-id="81a42-138">string</span></span> | <span data-ttu-id="81a42-139">Nein</span><span class="sxs-lookup"><span data-stu-id="81a42-139">no</span></span> | <span data-ttu-id="81a42-140">Eine formfreie Zeichenfolge an, dass die Quelle, die den URI gestartet.</span><span class="sxs-lookup"><span data-stu-id="81a42-140">A freeform string to indicate the source that launched the URI.</span></span> |
| <span data-ttu-id="81a42-141">isTemporary</span><span class="sxs-lookup"><span data-stu-id="81a42-141">isTemporary</span></span> | <span data-ttu-id="81a42-142">bool</span><span class="sxs-lookup"><span data-stu-id="81a42-142">bool</span></span> | <span data-ttu-id="81a42-143">nein</span><span class="sxs-lookup"><span data-stu-id="81a42-143">no</span></span> | <span data-ttu-id="81a42-144">Wenn auf True festgelegt, Bildschirmskizzen versucht, die Datei zu löschen, nachdem sie geöffnet.</span><span class="sxs-lookup"><span data-stu-id="81a42-144">If set to True, Screen Sketch will try to delete the file after opening it.</span></span> |

<span data-ttu-id="81a42-145">Das folgende Beispiel ruft die [LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_) -Methode, um ein Bild an Ausschnitt & Skizze aus der Benutzer app zu senden.</span><span class="sxs-lookup"><span data-stu-id="81a42-145">The following example calls the [LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_) method to send an image to Snip & Sketch from the user's app.</span></span>

```csharp

bool result = await Windows.System.Launcher.LaunchUriAsync(new Uri("ms-screensketch:edit?source=MyApp&isTemporary=false&sharedAccessToken=2C37ADDA-B054-40B5-8B38-11CED1E1A2D"));

```
