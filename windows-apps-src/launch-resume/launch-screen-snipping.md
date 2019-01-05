---
title: Ausschnitt & Skizze starten
description: In diesem Thema wird das ms-Screenclip und ms-Screensketch URI-Schemas. Ihre app kann diese URI-Schemas zum Starten der app Ausschnitt & Skizze oder öffnen Sie einen neuen Ausschnitt verwenden.
ms.date: 8/1/2017
ms.topic: article
keywords: Windows 10, Uwp, Uri, Ausschneiden, Skizze
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 07c095e661327ba1b64c4ba897937c8e3e905140
ms.sourcegitcommit: d705a79d037baa764790d3d8daa9321ed0ac9ebc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2019
ms.locfileid: "8992190"
---
# <a name="launch-screen-snipping"></a><span data-ttu-id="4fd42-105">Ausschnitt & Skizze starten</span><span class="sxs-lookup"><span data-stu-id="4fd42-105">Launch screen snipping</span></span>

<span data-ttu-id="4fd42-106">Die **ms-Screenclip:** und **ms-Screensketch:** URI-Schemas können Sie initiieren snipping oder Screenshots bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="4fd42-106">The **ms-screenclip:** and **ms-screensketch:** URI schemes allows you to initiate snipping or editing screenshots.</span></span>

## <a name="open-a-new-snip-from-your-app"></a><span data-ttu-id="4fd42-107">Öffnen Sie einen neuen Ausschnitt aus Ihrer app</span><span class="sxs-lookup"><span data-stu-id="4fd42-107">Open a new snip from your app</span></span>

<span data-ttu-id="4fd42-108">Die **ms-Screenclip:** URI kann Ihre app automatisch öffnen, und starten Sie einen neuen Ausschnitt.</span><span class="sxs-lookup"><span data-stu-id="4fd42-108">The **ms-screenclip:** URI allows your app to automatically open up and start a new snip.</span></span> <span data-ttu-id="4fd42-109">Die resultierende Ausschnitt wird in die Zwischenablage des Benutzers kopiert, jedoch nicht automatisch zurück an die öffnen-app übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="4fd42-109">The resulting snip is copied to the user's clipboard, but is not automatically passed back to the opening app.</span></span>

<span data-ttu-id="4fd42-110">**ms-Screenclip:** hat die folgenden Parameter:</span><span class="sxs-lookup"><span data-stu-id="4fd42-110">**ms-screenclip:** takes the following parameters:</span></span>

| <span data-ttu-id="4fd42-111">Parameter</span><span class="sxs-lookup"><span data-stu-id="4fd42-111">Parameter</span></span> | <span data-ttu-id="4fd42-112">Typ</span><span class="sxs-lookup"><span data-stu-id="4fd42-112">Type</span></span> | <span data-ttu-id="4fd42-113">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="4fd42-113">Required</span></span> | <span data-ttu-id="4fd42-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4fd42-114">Description</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="4fd42-115">Quelle</span><span class="sxs-lookup"><span data-stu-id="4fd42-115">source</span></span> | <span data-ttu-id="4fd42-116">string</span><span class="sxs-lookup"><span data-stu-id="4fd42-116">string</span></span> | <span data-ttu-id="4fd42-117">Nein</span><span class="sxs-lookup"><span data-stu-id="4fd42-117">no</span></span> | <span data-ttu-id="4fd42-118">Eine formfreie Zeichenfolge an der Quelle, die den URI gestartet.</span><span class="sxs-lookup"><span data-stu-id="4fd42-118">A freeform string to indicate the source that launched the URI.</span></span> |
| <span data-ttu-id="4fd42-119">delayInSeconds</span><span class="sxs-lookup"><span data-stu-id="4fd42-119">delayInSeconds</span></span> | <span data-ttu-id="4fd42-120">int</span><span class="sxs-lookup"><span data-stu-id="4fd42-120">int</span></span> | <span data-ttu-id="4fd42-121">nein</span><span class="sxs-lookup"><span data-stu-id="4fd42-121">no</span></span> | <span data-ttu-id="4fd42-122">Eine ganze Zahl von 1 bis zu 30.</span><span class="sxs-lookup"><span data-stu-id="4fd42-122">An integer value, from 1 to 30.</span></span> <span data-ttu-id="4fd42-123">Gibt die Verzögerung in vollständige Sekunden zwischen dem URI-Aufruf und wann snipping beginnt.</span><span class="sxs-lookup"><span data-stu-id="4fd42-123">Specifies the delay, in full seconds, between the URI call and when snipping begins.</span></span> |

## <a name="launching-the-snip--sketch-app"></a><span data-ttu-id="4fd42-124">Starten die Ausschneiden und Sketch-App</span><span class="sxs-lookup"><span data-stu-id="4fd42-124">Launching the Snip & Sketch App</span></span>

<span data-ttu-id="4fd42-125">Die **ms-Screensketch:** URI können Sie programmgesteuert Starten der app Ausschnitt & Skizze, und öffnen Sie ein bestimmtes Bild in der app für Anmerkung.</span><span class="sxs-lookup"><span data-stu-id="4fd42-125">The **ms-screensketch:** URI allows you to programatically launch the Snip & Sketch app, and open a specific image in that app for annotation.</span></span>

<span data-ttu-id="4fd42-126">**ms-Screensketch:** hat die folgenden Parameter:</span><span class="sxs-lookup"><span data-stu-id="4fd42-126">**ms-screensketch:** takes the following parameters:</span></span>

| <span data-ttu-id="4fd42-127">Parameter</span><span class="sxs-lookup"><span data-stu-id="4fd42-127">Parameter</span></span> | <span data-ttu-id="4fd42-128">Typ</span><span class="sxs-lookup"><span data-stu-id="4fd42-128">Type</span></span> | <span data-ttu-id="4fd42-129">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="4fd42-129">Required</span></span> | <span data-ttu-id="4fd42-130">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="4fd42-130">Description</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="4fd42-131">sharedAccessToken</span><span class="sxs-lookup"><span data-stu-id="4fd42-131">sharedAccessToken</span></span> | <span data-ttu-id="4fd42-132">string</span><span class="sxs-lookup"><span data-stu-id="4fd42-132">string</span></span> | <span data-ttu-id="4fd42-133">Nein</span><span class="sxs-lookup"><span data-stu-id="4fd42-133">no</span></span> | <span data-ttu-id="4fd42-134">Ein Token, identifizieren die Datei in der Ausschnitt und Sketch-app zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="4fd42-134">A token identifying the file to open in the Snip & Sketch app.</span></span> <span data-ttu-id="4fd42-135">Aus [SharedStorageAccessManager.AddFile](https://docs.microsoft.com/uwp/api/windows.applicationmodel.datatransfer.sharedstorageaccessmanager.addfile)abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="4fd42-135">Retrieved from [SharedStorageAccessManager.AddFile](https://docs.microsoft.com/uwp/api/windows.applicationmodel.datatransfer.sharedstorageaccessmanager.addfile).</span></span> <span data-ttu-id="4fd42-136">Wenn dieser Parameter nicht angegeben ist, wird die app ohne Öffnen der Datei gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="4fd42-136">If this parameter is omitted, the app will be launched without a file open.</span></span> |
| <span data-ttu-id="4fd42-137">secondarySharedAccessToken</span><span class="sxs-lookup"><span data-stu-id="4fd42-137">secondarySharedAccessToken</span></span> | <span data-ttu-id="4fd42-138">string</span><span class="sxs-lookup"><span data-stu-id="4fd42-138">string</span></span> | <span data-ttu-id="4fd42-139">Nein</span><span class="sxs-lookup"><span data-stu-id="4fd42-139">no</span></span> | <span data-ttu-id="4fd42-140">Eine Zeichenfolge, die eine JSON-Datei mit Metadaten zu den Ausschnitt identifiziert.</span><span class="sxs-lookup"><span data-stu-id="4fd42-140">A string identifying a JSON file with metadata about the snip.</span></span> <span data-ttu-id="4fd42-141">Die Metadaten können ein **ClipPoints** -Feld, mit der ein Array von x, y-Koordinaten bzw. ein [UserActivity](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity)enthalten.</span><span class="sxs-lookup"><span data-stu-id="4fd42-141">The metadata may include a **clipPoints** field with an array of x,y coordinates, and/or a [userActivity](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity).</span></span> |
| <span data-ttu-id="4fd42-142">Quelle</span><span class="sxs-lookup"><span data-stu-id="4fd42-142">source</span></span> | <span data-ttu-id="4fd42-143">string</span><span class="sxs-lookup"><span data-stu-id="4fd42-143">string</span></span> | <span data-ttu-id="4fd42-144">Nein</span><span class="sxs-lookup"><span data-stu-id="4fd42-144">no</span></span> | <span data-ttu-id="4fd42-145">Eine formfreie Zeichenfolge an der Quelle, die den URI gestartet.</span><span class="sxs-lookup"><span data-stu-id="4fd42-145">A freeform string to indicate the source that launched the URI.</span></span> |
| <span data-ttu-id="4fd42-146">isTemporary</span><span class="sxs-lookup"><span data-stu-id="4fd42-146">isTemporary</span></span> | <span data-ttu-id="4fd42-147">bool</span><span class="sxs-lookup"><span data-stu-id="4fd42-147">bool</span></span> | <span data-ttu-id="4fd42-148">nein</span><span class="sxs-lookup"><span data-stu-id="4fd42-148">no</span></span> | <span data-ttu-id="4fd42-149">Wenn auf True festgelegt, Bildschirmskizzen versucht, die Datei zu löschen, nachdem sie geöffnet.</span><span class="sxs-lookup"><span data-stu-id="4fd42-149">If set to True, Screen Sketch will try to delete the file after opening it.</span></span> |

<span data-ttu-id="4fd42-150">Das folgende Beispiel ruft die [LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_) -Methode, um ein Bild an Ausschnitt & Skizze aus der Benutzer die app zu senden.</span><span class="sxs-lookup"><span data-stu-id="4fd42-150">The following example calls the [LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_) method to send an image to Snip & Sketch from the user's app.</span></span>

```csharp

bool result = await Windows.System.Launcher.LaunchUriAsync(new Uri("ms-screensketch:edit?source=MyApp&isTemporary=false&sharedAccessToken=2C37ADDA-B054-40B5-8B38-11CED1E1A2D"));

```

<span data-ttu-id="4fd42-151">Im folgenden Beispiel wird veranschaulicht, wie eine Datei, die von der **SecondarySharedAccessToken** -Parameter für **ms-Screensketch** angegebenen enthalten kann:</span><span class="sxs-lookup"><span data-stu-id="4fd42-151">The following example illustrates what a file specified by the **secondarySharedAccessToken** parameter of **ms-screensketch** might contain:</span></span>

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
