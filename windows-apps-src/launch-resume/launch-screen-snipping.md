---
title: Ausschnitt & Skizze starten
description: Dieses Thema beschreibt die ms-Screenclip und ms-Screensketch-URI-Schemas. Ihre app kann diese URI-Schemas zum Starten der Ausschnitt & Skizze app oder einen neuen Ausschnitt Öffnen verwenden.
ms.date: 08/09/2017
ms.topic: article
keywords: Windows 10, Uwp, Uri, Ausschneiden, Skizze
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 06e988387f574b74d511b14a2ebca24b0a149158
ms.sourcegitcommit: 079801609165bc7eb69670d771a05bffe236d483
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/27/2019
ms.locfileid: "9116172"
---
# <a name="launch-screen-snipping"></a><span data-ttu-id="99f12-105">Ausschnitt & Skizze starten</span><span class="sxs-lookup"><span data-stu-id="99f12-105">Launch screen snipping</span></span>

<span data-ttu-id="99f12-106">Die **ms-Screenclip:** und **ms-Screensketch:** URI-Schemas ermöglicht es Ihnen, snipping oder Bearbeiten von Screenshots zu initiieren.</span><span class="sxs-lookup"><span data-stu-id="99f12-106">The **ms-screenclip:** and **ms-screensketch:** URI schemes allows you to initiate snipping or editing screenshots.</span></span>

## <a name="open-a-new-snip-from-your-app"></a><span data-ttu-id="99f12-107">Öffnen Sie einen neuen Ausschnitt aus Ihrer app</span><span class="sxs-lookup"><span data-stu-id="99f12-107">Open a new snip from your app</span></span>

<span data-ttu-id="99f12-108">Die **ms-Screenclip:** URI kann Ihre app automatisch öffnen, und starten einen neuen Ausschnitt.</span><span class="sxs-lookup"><span data-stu-id="99f12-108">The **ms-screenclip:** URI allows your app to automatically open up and start a new snip.</span></span> <span data-ttu-id="99f12-109">Der resultierende Ausschnitt wird in die Zwischenablage des Benutzers kopiert, jedoch nicht automatisch zurück an die öffnen-app übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="99f12-109">The resulting snip is copied to the user's clipboard, but is not automatically passed back to the opening app.</span></span>

<span data-ttu-id="99f12-110">**ms-Screenclip:** hat die folgenden Parameter:</span><span class="sxs-lookup"><span data-stu-id="99f12-110">**ms-screenclip:** takes the following parameters:</span></span>

| <span data-ttu-id="99f12-111">Parameter</span><span class="sxs-lookup"><span data-stu-id="99f12-111">Parameter</span></span> | <span data-ttu-id="99f12-112">Typ</span><span class="sxs-lookup"><span data-stu-id="99f12-112">Type</span></span> | <span data-ttu-id="99f12-113">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="99f12-113">Required</span></span> | <span data-ttu-id="99f12-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="99f12-114">Description</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="99f12-115">Quelle</span><span class="sxs-lookup"><span data-stu-id="99f12-115">source</span></span> | <span data-ttu-id="99f12-116">string</span><span class="sxs-lookup"><span data-stu-id="99f12-116">string</span></span> | <span data-ttu-id="99f12-117">Nein</span><span class="sxs-lookup"><span data-stu-id="99f12-117">no</span></span> | <span data-ttu-id="99f12-118">Eine formfreie Zeichenfolge an, dass die Quelle, die den URI gestartet.</span><span class="sxs-lookup"><span data-stu-id="99f12-118">A freeform string to indicate the source that launched the URI.</span></span> |
| <span data-ttu-id="99f12-119">delayInSeconds</span><span class="sxs-lookup"><span data-stu-id="99f12-119">delayInSeconds</span></span> | <span data-ttu-id="99f12-120">int</span><span class="sxs-lookup"><span data-stu-id="99f12-120">int</span></span> | <span data-ttu-id="99f12-121">nein</span><span class="sxs-lookup"><span data-stu-id="99f12-121">no</span></span> | <span data-ttu-id="99f12-122">Eine ganze Zahl von 1 bis 30.</span><span class="sxs-lookup"><span data-stu-id="99f12-122">An integer value, from 1 to 30.</span></span> <span data-ttu-id="99f12-123">Gibt die Verzögerung in vollständige Sekunden zwischen dem URI-Aufruf und wann snipping beginnt.</span><span class="sxs-lookup"><span data-stu-id="99f12-123">Specifies the delay, in full seconds, between the URI call and when snipping begins.</span></span> |
| <span data-ttu-id="99f12-124">callbackformat</span><span class="sxs-lookup"><span data-stu-id="99f12-124">callbackformat</span></span> | <span data-ttu-id="99f12-125">string</span><span class="sxs-lookup"><span data-stu-id="99f12-125">string</span></span> | <span data-ttu-id="99f12-126">Nein</span><span class="sxs-lookup"><span data-stu-id="99f12-126">no</span></span> | <span data-ttu-id="99f12-127">Dieser Parameter ist nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="99f12-127">This parameter is unavailable.</span></span> |

## <a name="launching-the-snip--sketch-app"></a><span data-ttu-id="99f12-128">Starten der Ausschnitt & Skizze-App</span><span class="sxs-lookup"><span data-stu-id="99f12-128">Launching the Snip & Sketch App</span></span>

<span data-ttu-id="99f12-129">Die **ms-Screensketch:** URI können Sie programmgesteuert Starten der Ausschnitt & Skizze-app, und öffnen Sie ein bestimmtes Bild in der app für Anmerkung.</span><span class="sxs-lookup"><span data-stu-id="99f12-129">The **ms-screensketch:** URI allows you to programatically launch the Snip & Sketch app, and open a specific image in that app for annotation.</span></span>

<span data-ttu-id="99f12-130">**ms-Screensketch:** hat die folgenden Parameter:</span><span class="sxs-lookup"><span data-stu-id="99f12-130">**ms-screensketch:** takes the following parameters:</span></span>

| <span data-ttu-id="99f12-131">Parameter</span><span class="sxs-lookup"><span data-stu-id="99f12-131">Parameter</span></span> | <span data-ttu-id="99f12-132">Typ</span><span class="sxs-lookup"><span data-stu-id="99f12-132">Type</span></span> | <span data-ttu-id="99f12-133">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="99f12-133">Required</span></span> | <span data-ttu-id="99f12-134">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="99f12-134">Description</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="99f12-135">sharedAccessToken</span><span class="sxs-lookup"><span data-stu-id="99f12-135">sharedAccessToken</span></span> | <span data-ttu-id="99f12-136">string</span><span class="sxs-lookup"><span data-stu-id="99f12-136">string</span></span> | <span data-ttu-id="99f12-137">Nein</span><span class="sxs-lookup"><span data-stu-id="99f12-137">no</span></span> | <span data-ttu-id="99f12-138">Ein Token, identifizieren die Datei in der Ausschnitt & Skizze app zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="99f12-138">A token identifying the file to open in the Snip & Sketch app.</span></span> <span data-ttu-id="99f12-139">Aus [SharedStorageAccessManager.AddFile](https://docs.microsoft.com/uwp/api/windows.applicationmodel.datatransfer.sharedstorageaccessmanager.addfile)abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="99f12-139">Retrieved from [SharedStorageAccessManager.AddFile](https://docs.microsoft.com/uwp/api/windows.applicationmodel.datatransfer.sharedstorageaccessmanager.addfile).</span></span> <span data-ttu-id="99f12-140">Wenn dieser Parameter ausgelassen wird, wird die app ohne Öffnen der Datei gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="99f12-140">If this parameter is omitted, the app will be launched without a file open.</span></span> |
| <span data-ttu-id="99f12-141">secondarySharedAccessToken</span><span class="sxs-lookup"><span data-stu-id="99f12-141">secondarySharedAccessToken</span></span> | <span data-ttu-id="99f12-142">string</span><span class="sxs-lookup"><span data-stu-id="99f12-142">string</span></span> | <span data-ttu-id="99f12-143">Nein</span><span class="sxs-lookup"><span data-stu-id="99f12-143">no</span></span> | <span data-ttu-id="99f12-144">Eine Zeichenfolge, die eine JSON-Datei mit Metadaten zu den Ausschnitt identifiziert.</span><span class="sxs-lookup"><span data-stu-id="99f12-144">A string identifying a JSON file with metadata about the snip.</span></span> <span data-ttu-id="99f12-145">Die Metadaten können ein **ClipPoints** Feld ein Array von x, y-Koordinaten und/oder ein [UserActivity](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity)enthalten.</span><span class="sxs-lookup"><span data-stu-id="99f12-145">The metadata may include a **clipPoints** field with an array of x,y coordinates, and/or a [userActivity](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity).</span></span> |
| <span data-ttu-id="99f12-146">Quelle</span><span class="sxs-lookup"><span data-stu-id="99f12-146">source</span></span> | <span data-ttu-id="99f12-147">string</span><span class="sxs-lookup"><span data-stu-id="99f12-147">string</span></span> | <span data-ttu-id="99f12-148">Nein</span><span class="sxs-lookup"><span data-stu-id="99f12-148">no</span></span> | <span data-ttu-id="99f12-149">Eine formfreie Zeichenfolge an, dass die Quelle, die den URI gestartet.</span><span class="sxs-lookup"><span data-stu-id="99f12-149">A freeform string to indicate the source that launched the URI.</span></span> |
| <span data-ttu-id="99f12-150">isTemporary</span><span class="sxs-lookup"><span data-stu-id="99f12-150">isTemporary</span></span> | <span data-ttu-id="99f12-151">bool</span><span class="sxs-lookup"><span data-stu-id="99f12-151">bool</span></span> | <span data-ttu-id="99f12-152">nein</span><span class="sxs-lookup"><span data-stu-id="99f12-152">no</span></span> | <span data-ttu-id="99f12-153">Wenn auf True festgelegt, Bildschirmskizzen versucht, die Datei zu löschen, nachdem sie geöffnet.</span><span class="sxs-lookup"><span data-stu-id="99f12-153">If set to True, Screen Sketch will try to delete the file after opening it.</span></span> |

<span data-ttu-id="99f12-154">Das folgende Beispiel ruft die [LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_) -Methode, um ein Bild an Ausschnitt & Skizze aus des Benutzers app zu senden.</span><span class="sxs-lookup"><span data-stu-id="99f12-154">The following example calls the [LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_) method to send an image to Snip & Sketch from the user's app.</span></span>

```csharp

bool result = await Windows.System.Launcher.LaunchUriAsync(new Uri("ms-screensketch:edit?source=MyApp&isTemporary=false&sharedAccessToken=2C37ADDA-B054-40B5-8B38-11CED1E1A2D"));

```

<span data-ttu-id="99f12-155">Das folgende Beispiel veranschaulicht, wie eine Datei, die durch den **SecondarySharedAccessToken** -Parameter des **ms-Screensketch** angegebenen enthalten kann:</span><span class="sxs-lookup"><span data-stu-id="99f12-155">The following example illustrates what a file specified by the **secondarySharedAccessToken** parameter of **ms-screensketch** might contain:</span></span>

```json
{
  "clipPoints": [
    {
      "x": 0,
      "y": 0
    },
    {
      "x": 2080,
      "y": 0
    },
    {
      "x": 2080,
      "y": 780
    },
    {
      "x": 0,
      "y": 780
    }
  ],
  "userActivity": "{\"$schema\":\"http://activity.windows.com/user-activity.json\",\"UserActivity\":\"type\",\"1.0\":\"version\",\"cross-platform-identifiers\":[{\"platform\":\"windows_universal\",\"application\":\"Microsoft.MicrosoftEdge_8wekyb3d8bbwe!MicrosoftEdge\"},{\"platform\":\"host\",\"application\":\"edge.activity.windows.com\"}],\"activationUrl\":\"microsoft-edge:https://support.microsoft.com/en-us/help/13776/windows-use-snipping-tool-to-capture-screenshots\",\"contentUrl\":\"https://support.microsoft.com/en-us/help/13776/windows-use-snipping-tool-to-capture-screenshots\",\"visualElements\":{\"attribution\":{\"iconUrl\":\"https://www.microsoft.com/favicon.ico?v2\",\"alternateText\":\"microsoft.com\"},\"description\":\"https://support.microsoft.com/en-us/help/13776/windows-use-snipping-tool-to-capture-screenshots\",\"backgroundColor\":\"#FF0078D7\",\"displayText\":\"Use snipping tool to capture screenshots - Windows Help\",\"content\":{\"$schema\":\"http://adaptivecards.io/schemas/adaptive-card.json\",\"type\":\"AdaptiveCard\",\"version\":\"1.0\",\"body\":[{\"type\":\"Container\",\"items\":[{\"type\":\"TextBlock\",\"text\":\"Use snipping tool to capture screenshots - Windows Help\",\"weight\":\"bolder\",\"size\":\"large\",\"wrap\":true,\"maxLines\":3},{\"type\":\"TextBlock\",\"text\":\"https://support.microsoft.com/en-us/help/13776/windows-use-snipping-tool-to-capture-screenshots\",\"size\":\"normal\",\"wrap\":true,\"maxLines\":3}]}]}},\"isRoamable\":true,\"appActivityId\":\"https://support.microsoft.com/en-us/help/13776/windows-use-snipping-tool-to-capture-screenshots\"}"
}

```
