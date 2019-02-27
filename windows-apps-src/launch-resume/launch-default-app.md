---
title: Starten der Standard-App für einen URI
description: Erfahren Sie, wie Sie die Standard-App für einen Uniform Resource Identifier (URI) starten. URIs ermöglichen den Start einer anderen App zum Ausführen einer bestimmten Aufgabe. Dieses Thema enthält auch eine Übersicht über die zahlreichen in Windows integrierten URI-Schemas.
ms.assetid: 7B0D0AF5-D89E-4DB0-9B79-90201D79974F
ms.date: 06/26/2017
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 6c5c8b99ec3646d1eebbb922557f97c9e9304ed4
ms.sourcegitcommit: 079801609165bc7eb69670d771a05bffe236d483
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/27/2019
ms.locfileid: "9116462"
---
# <a name="launch-the-default-app-for-a-uri"></a><span data-ttu-id="b3d84-106">Starten der Standard-App für einen URI</span><span class="sxs-lookup"><span data-stu-id="b3d84-106">Launch the default app for a URI</span></span>


**<span data-ttu-id="b3d84-107">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="b3d84-107">Important APIs</span></span>**

- [**<span data-ttu-id="b3d84-108">LaunchUriAsync</span><span class="sxs-lookup"><span data-stu-id="b3d84-108">LaunchUriAsync</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh701476)
- [**<span data-ttu-id="b3d84-109">PreferredApplicationPackageFamilyName</span><span class="sxs-lookup"><span data-stu-id="b3d84-109">PreferredApplicationPackageFamilyName</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh965482)
- [**<span data-ttu-id="b3d84-110">DesiredRemainingView</span><span class="sxs-lookup"><span data-stu-id="b3d84-110">DesiredRemainingView</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn298314)

<span data-ttu-id="b3d84-111">Hier erfahren Sie, wie Sie die Standard-App für einen Uniform Resource Identifier (URI) starten.</span><span class="sxs-lookup"><span data-stu-id="b3d84-111">Learn how to launch the default app for a Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="b3d84-112">URIs ermöglichen den Start einer anderen App zum Ausführen einer bestimmten Aufgabe.</span><span class="sxs-lookup"><span data-stu-id="b3d84-112">URIs allow you to launch another app to perform a specific task.</span></span> <span data-ttu-id="b3d84-113">Dieses Thema enthält auch eine Übersicht über die vielen in Windows integrierten URI-Schemas.</span><span class="sxs-lookup"><span data-stu-id="b3d84-113">This topic also provides an overview of the many URI schemes built into Windows.</span></span> <span data-ttu-id="b3d84-114">Sie können außerdem benutzerdefinierte URIs starten.</span><span class="sxs-lookup"><span data-stu-id="b3d84-114">You can launch custom URIs too.</span></span> <span data-ttu-id="b3d84-115">Weitere Informationen zum Registrieren eines benutzerdefinierten URI-Schemas und Behandeln der URI-Aktivierung finden Sie unter [Behandeln der URI-Aktivierung](handle-uri-activation.md).</span><span class="sxs-lookup"><span data-stu-id="b3d84-115">For more info about registering a custom URI scheme and handling URI activation, see [Handle URI activation](handle-uri-activation.md).</span></span>

<span data-ttu-id="b3d84-116">Mit URI-Schemas können Sie Apps öffnen, indem Sie auf Hyperlinks klicken.</span><span class="sxs-lookup"><span data-stu-id="b3d84-116">URI schemes let you open apps by clicking hyperlinks.</span></span> <span data-ttu-id="b3d84-117">Genau wie Sie eine neue E-Mail mit **mailto:** öffnen, können Sie den Standardwebbrowser mit **http:** öffnen.</span><span class="sxs-lookup"><span data-stu-id="b3d84-117">Just as you can start a new email using **mailto:**, you can open the default web browser using **http:**</span></span>

<span data-ttu-id="b3d84-118">In diesem Thema werden einige der folgenden URI-Schemas beschrieben, die in Windows integriert sind:</span><span class="sxs-lookup"><span data-stu-id="b3d84-118">This topic describes the following URI schemes built into Windows:</span></span>

| <span data-ttu-id="b3d84-119">URI-Schema</span><span class="sxs-lookup"><span data-stu-id="b3d84-119">URI Scheme</span></span> | <span data-ttu-id="b3d84-120">Startet</span><span class="sxs-lookup"><span data-stu-id="b3d84-120">Launches</span></span> |
| ----------:|----------|
|[<span data-ttu-id="b3d84-121">bingmaps:, ms-drive-to: und ms-walk-to:</span><span class="sxs-lookup"><span data-stu-id="b3d84-121">bingmaps:, ms-drive-to:, and ms-walk-to:</span></span> ](#maps-app-uri-schemes) | <span data-ttu-id="b3d84-122">Karten-App</span><span class="sxs-lookup"><span data-stu-id="b3d84-122">Maps app</span></span> |
|[<span data-ttu-id="b3d84-123">http:</span><span class="sxs-lookup"><span data-stu-id="b3d84-123">http:</span></span>](#http-uri-scheme) | <span data-ttu-id="b3d84-124">Standardwebbrowser</span><span class="sxs-lookup"><span data-stu-id="b3d84-124">Default web browser</span></span> |
|[<span data-ttu-id="b3d84-125">mailto:</span><span class="sxs-lookup"><span data-stu-id="b3d84-125">mailto:</span></span>](#email-uri-scheme) | <span data-ttu-id="b3d84-126">Standard-E-Mail-App</span><span class="sxs-lookup"><span data-stu-id="b3d84-126">Default email app</span></span> |
|[<span data-ttu-id="b3d84-127">ms-call:</span><span class="sxs-lookup"><span data-stu-id="b3d84-127">ms-call:</span></span>](#call-app-uri-scheme) |  <span data-ttu-id="b3d84-128">Anruf-App</span><span class="sxs-lookup"><span data-stu-id="b3d84-128">Call app</span></span> |
|[<span data-ttu-id="b3d84-129">ms-chat:</span><span class="sxs-lookup"><span data-stu-id="b3d84-129">ms-chat:</span></span>](#messaging-app-uri-scheme) | <span data-ttu-id="b3d84-130">Messaging-App</span><span class="sxs-lookup"><span data-stu-id="b3d84-130">Messaging app</span></span> |
|[<span data-ttu-id="b3d84-131">ms-people:</span><span class="sxs-lookup"><span data-stu-id="b3d84-131">ms-people:</span></span>](#people-app-uri-scheme) | <span data-ttu-id="b3d84-132">Kontakte-App</span><span class="sxs-lookup"><span data-stu-id="b3d84-132">People app</span></span> |
|[<span data-ttu-id="b3d84-133">ms-photos:</span><span class="sxs-lookup"><span data-stu-id="b3d84-133">ms-photos:</span></span>](#photos-app-uri-scheme) | <span data-ttu-id="b3d84-134">Fotos-App</span><span class="sxs-lookup"><span data-stu-id="b3d84-134">Photos app</span></span> |
|[<span data-ttu-id="b3d84-135">ms-settings:</span><span class="sxs-lookup"><span data-stu-id="b3d84-135">ms-settings:</span></span>](#settings-app-uri-scheme) | <span data-ttu-id="b3d84-136">Einstellungs-App</span><span class="sxs-lookup"><span data-stu-id="b3d84-136">Settings app</span></span> |
|[<span data-ttu-id="b3d84-137">ms-store:</span><span class="sxs-lookup"><span data-stu-id="b3d84-137">ms-store:</span></span>](#store-app-uri-scheme)  | <span data-ttu-id="b3d84-138">Store-App</span><span class="sxs-lookup"><span data-stu-id="b3d84-138">Store app</span></span> |
|[<span data-ttu-id="b3d84-139">ms-tonepicker:</span><span class="sxs-lookup"><span data-stu-id="b3d84-139">ms-tonepicker:</span></span>](#tone-picker-uri-scheme) | <span data-ttu-id="b3d84-140">Tonauswahl</span><span class="sxs-lookup"><span data-stu-id="b3d84-140">Tone picker</span></span> |
|[<span data-ttu-id="b3d84-141">ms-yellowpage:</span><span class="sxs-lookup"><span data-stu-id="b3d84-141">ms-yellowpage:</span></span>](#nearby-numbers-app-uri-scheme) | <span data-ttu-id="b3d84-142">Nearby Numbers-App</span><span class="sxs-lookup"><span data-stu-id="b3d84-142">Nearby Numbers app</span></span> |
|[<span data-ttu-id="b3d84-143">Msnweather:</span><span class="sxs-lookup"><span data-stu-id="b3d84-143">msnweather:</span></span>](#weather-app-uri-scheme) | <span data-ttu-id="b3d84-144">Wetter-App</span><span class="sxs-lookup"><span data-stu-id="b3d84-144">Weather app</span></span> |

<br>
<span data-ttu-id="b3d84-145">Der folgende URI öffnet beispielsweise den Standardbrowser und zeigt die Bing-Website an.</span><span class="sxs-lookup"><span data-stu-id="b3d84-145">For example, the following URI opens the default browser and displays the Bing web site.</span></span>

`https://bing.com`

<span data-ttu-id="b3d84-146">Sie können außerdem benutzerdefinierte URI-Schemas starten.</span><span class="sxs-lookup"><span data-stu-id="b3d84-146">You can also launch custom URI schemes too.</span></span> <span data-ttu-id="b3d84-147">Wenn zum Behandeln dieses URI keine App installiert ist, können Sie dem Benutzer die Installation einer App empfehlen.</span><span class="sxs-lookup"><span data-stu-id="b3d84-147">If there is no app installed to handle that URI, you can recommend an app for the user to install.</span></span> <span data-ttu-id="b3d84-148">Weitere Informationen erhalten Sie unter [Empfehlen einer App, wenn keine App zur Behandlung des URI verfügbar ist](#recommend-an-app-if-one-is-not-available-to-handle-the-uri).</span><span class="sxs-lookup"><span data-stu-id="b3d84-148">For more info, see [Recommend an app if one is not available to handle the URI](#recommend-an-app-if-one-is-not-available-to-handle-the-uri).</span></span>

<span data-ttu-id="b3d84-149">Im Allgemeinen kann die App nicht die App auswählen, die gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="b3d84-149">In general, your app can't select the app that is launched.</span></span> <span data-ttu-id="b3d84-150">Der Benutzer entscheidet, welche App gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="b3d84-150">The user determines which app is launched.</span></span> <span data-ttu-id="b3d84-151">Zum Behandeln desselben URI-Schemas kann mehr als eine App registriert werden.</span><span class="sxs-lookup"><span data-stu-id="b3d84-151">More than one app can register to handle the same URI scheme.</span></span> <span data-ttu-id="b3d84-152">Die einzige Ausnahme sind reservierte URI-Schemas.</span><span class="sxs-lookup"><span data-stu-id="b3d84-152">The exception to this is for reserved URI schemes.</span></span> <span data-ttu-id="b3d84-153">Registrierungen der reservierten URI-Schemas werden ignoriert.</span><span class="sxs-lookup"><span data-stu-id="b3d84-153">Registrations of reserved URI schemes are ignored.</span></span> <span data-ttu-id="b3d84-154">Die vollständige Liste der reservierten URI-Schemas finden Sie unter [Behandeln der URI-Aktivierung](handle-uri-activation.md).</span><span class="sxs-lookup"><span data-stu-id="b3d84-154">For the full list of reserved URI schemes, see [Handle URI activation](handle-uri-activation.md).</span></span> <span data-ttu-id="b3d84-155">In Fällen, in denen mehrere Apps das gleiche URI-Schema registriert haben, kann Ihre App das Starten einer bestimmten App empfehlen.</span><span class="sxs-lookup"><span data-stu-id="b3d84-155">In cases where more than one app may have registered the same URI scheme, your app can recommend a specific app to be launched.</span></span> <span data-ttu-id="b3d84-156">Weitere Informationen finden Sie unter [Empfehlen einer App, wenn keine App zur Behandlung des URI verfügbar ist](#recommend-an-app-if-one-is-not-available-to-handle-the-uri).</span><span class="sxs-lookup"><span data-stu-id="b3d84-156">For more info, see [Recommend an app if one is not available to handle the URI](#recommend-an-app-if-one-is-not-available-to-handle-the-uri).</span></span>

### <a name="call-launchuriasync-to-launch-a-uri"></a><span data-ttu-id="b3d84-157">Aufruf von „LaunchUriAsync“ zum Starten eines URI</span><span class="sxs-lookup"><span data-stu-id="b3d84-157">Call LaunchUriAsync to launch a URI</span></span>

<span data-ttu-id="b3d84-158">Verwenden Sie die Methode [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476), um einen URI zu starten.</span><span class="sxs-lookup"><span data-stu-id="b3d84-158">Use the [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476) method to launch a URI.</span></span> <span data-ttu-id="b3d84-159">Beim Aufrufen dieser Methode muss Ihre App im Vordergrund ausgeführt werden, d.h., sie muss für den Benutzer sichtbar sein.</span><span class="sxs-lookup"><span data-stu-id="b3d84-159">When you call this method, your app must be the foreground app, that is, it must be visible to the user.</span></span> <span data-ttu-id="b3d84-160">Mithilfe dieser Anforderung wird sichergestellt, dass der Benutzer zu jedem Zeitpunkt die Kontrolle behält.</span><span class="sxs-lookup"><span data-stu-id="b3d84-160">This requirement helps ensure that the user remains in control.</span></span> <span data-ttu-id="b3d84-161">Verknüpfen Sie alle URI-Startvorgänge direkt mit der Benutzeroberfläche Ihrer App, um sicherzustellen, dass diese Anforderung erfüllt wird.</span><span class="sxs-lookup"><span data-stu-id="b3d84-161">To meet this requirement, make sure that you tie all URI launches directly to the UI of your app.</span></span> <span data-ttu-id="b3d84-162">Der Benutzer muss immer eine Aktion ausführen, um einen URI zu starten.</span><span class="sxs-lookup"><span data-stu-id="b3d84-162">The user must always take some action to initiate a URI launch.</span></span> <span data-ttu-id="b3d84-163">Wenn Sie versuchen, einen URI zu starten, und Ihre App befindet sich nicht im Vordergrund, schlägt der Start fehl und Ihr Fehlerrückruf wird aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="b3d84-163">If you attempt to launch a URI and your app isn't in the foreground, the launch will fail and your error callback will be invoked.</span></span>

<span data-ttu-id="b3d84-164">Erstellen Sie zunächst ein [**System.Uri**](https://msdn.microsoft.com/library/windows/apps/system.uri.aspx)-Objekt, das den URI darstellt, und übergeben Sie es anschließend an die Methode [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476).</span><span class="sxs-lookup"><span data-stu-id="b3d84-164">First create a [**System.Uri**](https://msdn.microsoft.com/library/windows/apps/system.uri.aspx) object to represent the URI, then pass that to the [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476) method.</span></span> <span data-ttu-id="b3d84-165">Verwenden Sie das Ergebnis, um zu überprüfen, ob der Aufruf erfolgreich war, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="b3d84-165">Use the return result to see if the call succeeded, as shown in the following example.</span></span>

```cs
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // The URI to launch
   var uriBing = new Uri(@"http://www.bing.com");

   // Launch the URI
   var success = await Windows.System.Launcher.LaunchUriAsync(uriBing);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

<span data-ttu-id="b3d84-166">In einigen Fällen fordert das Betriebssystem den Benutzer dazu auf, zu prüfen, ob er tatsächlich Apps wechseln möchte.</span><span class="sxs-lookup"><span data-stu-id="b3d84-166">In some cases, the operating system will prompt the user to see if they actually want to switch apps.</span></span>

![Überlagerndes Warndialogfeld in der App auf grauem Hintergrund.](images/warningdialog.png)

<span data-ttu-id="b3d84-170">Wenn diese Aufforderung stets erfolgen soll, verwenden Sie die Eigenschaft [**Windows.System.LauncherOptions.TreatAsUntrusted**](https://msdn.microsoft.com/library/windows/apps/hh701442), um anzugeben, dass das Betriebssystem eine Warnung anzeigen soll.</span><span class="sxs-lookup"><span data-stu-id="b3d84-170">If you always want this prompt to occur, use the [**Windows.System.LauncherOptions.TreatAsUntrusted**](https://msdn.microsoft.com/library/windows/apps/hh701442) property to tell the operating system to display a warning.</span></span>

```cs
// The URI to launch
var uriBing = new Uri(@"http://www.bing.com");

// Set the option to show a warning
var promptOptions = new Windows.System.LauncherOptions();
promptOptions.TreatAsUntrusted = true;

// Launch the URI
var success = await Windows.System.Launcher.LaunchUriAsync(uriBing, promptOptions);
```

### <a name="recommend-an-app-if-one-is-not-available-to-handle-the-uri"></a><span data-ttu-id="b3d84-171">Empfehlen einer App, wenn keine App zur Behandlung des URI verfügbar ist</span><span class="sxs-lookup"><span data-stu-id="b3d84-171">Recommend an app if one is not available to handle the URI</span></span>

<span data-ttu-id="b3d84-172">Es kann jedoch sein, dass der Benutzer nicht über die erforderliche App zum Bearbeiten des aufgerufenen URI verfügt.</span><span class="sxs-lookup"><span data-stu-id="b3d84-172">In some cases, the user might not have an app installed to handle the URI that you are launching.</span></span> <span data-ttu-id="b3d84-173">In diesen Fällen bietet das Betriebssystem standardmäßig einen Link an, über den Benutzer im Store nach einer geeigneten App suchen können.</span><span class="sxs-lookup"><span data-stu-id="b3d84-173">By default, the operating system handles these cases by providing the user with a link to search for an appropriate app on the store.</span></span> <span data-ttu-id="b3d84-174">Wenn Sie dem Benutzer eine bestimmte App für dieses spezifische Szenario empfehlen möchten, können Sie die Empfehlung zusammen mit dem gestarteten URI übergeben.</span><span class="sxs-lookup"><span data-stu-id="b3d84-174">If you want to give the user a specific recommendation for which app to acquire in this scenario, you can do so by passing that recommendation along with the URI that you are launching.</span></span>

<span data-ttu-id="b3d84-175">Empfehlungen sind auch nützlich, wenn mehr als eine App zum Behandeln eines URI-Schema registriert wurde.</span><span class="sxs-lookup"><span data-stu-id="b3d84-175">Recommendations are also useful when more than one app has registered to handle a URI scheme.</span></span> <span data-ttu-id="b3d84-176">Durch die Empfehlung einer bestimmten App öffnet Windows die App, wenn sie bereits installiert ist.</span><span class="sxs-lookup"><span data-stu-id="b3d84-176">By recommending a specific app, Windows will open that app if it is already installed.</span></span>

<span data-ttu-id="b3d84-177">Rufen Sie dazu die Methode [**Windows.System.Launcher.LaunchUriAsync(Uri, LauncherOptions)**](https://msdn.microsoft.com/library/windows/apps/hh701484) auf, wobei [**LauncherOptions.preferredApplicationPackageFamilyName**](https://msdn.microsoft.com/library/windows/apps/hh965482) auf den Paketfamiliennamen der empfohlenen App im Store festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="b3d84-177">To make a recommendation, call the [**Windows.System.Launcher.LaunchUriAsync(Uri, LauncherOptions)**](https://msdn.microsoft.com/library/windows/apps/hh701484) method with [**LauncherOptions.preferredApplicationPackageFamilyName**](https://msdn.microsoft.com/library/windows/apps/hh965482) set to the package family name of the app in the store that you want to recommend.</span></span> <span data-ttu-id="b3d84-178">Diese Info wird vom Betriebssystem verwendet, um die allgemeine Option zum Suchen einer App im Store durch eine spezifische Option zum Erwerben der empfohlenen App im Store zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="b3d84-178">The operating system uses this info to replace the general option to search for an app in the store with a specific option to acquire the recommended app from the store.</span></span>

```cs
// Set the recommended app
var options = new Windows.System.LauncherOptions();
options.PreferredApplicationPackageFamilyName = "Contoso.URIApp_8wknc82po1e";
options.PreferredApplicationDisplayName = "Contoso URI Ap";

// Launch the URI and pass in the recommended app
// in case the user has no apps installed to handle the URI
var success = await Windows.System.Launcher.LaunchUriAsync(uriContoso, options);
```

### <a name="set-remaining-view-preference"></a><span data-ttu-id="b3d84-179">Festlegen der verbleibenden Ansichtseinstellung</span><span class="sxs-lookup"><span data-stu-id="b3d84-179">Set remaining view preference</span></span>

<span data-ttu-id="b3d84-180">Quell-Apps, die [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476) aufrufen, können anfordern, nach dem Start eines URIs auf dem Bildschirm zu verbleiben.</span><span class="sxs-lookup"><span data-stu-id="b3d84-180">Source apps that call [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476) can request that they remain on screen after a URI launch.</span></span> <span data-ttu-id="b3d84-181">Standardmäßig wird von Windows versucht, den gesamten verfügbaren Speicherplatz gleichmäßig zwischen der Quell- und der Ziel-App aufzuteilen, die den URI verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="b3d84-181">By default, Windows attempts to share all available space equally between the source app and the target app that handles the URI.</span></span> <span data-ttu-id="b3d84-182">Quell-Apps können die Eigenschaft [**DesiredRemainingView**](https://msdn.microsoft.com/library/windows/apps/dn298314) verwenden. Hiermit geben sie dem Betriebssystem an, mehr oder weniger des verfügbaren Speicherplatzes für ihr App-Fenster zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="b3d84-182">Source apps can use the [**DesiredRemainingView**](https://msdn.microsoft.com/library/windows/apps/dn298314) property to indicate to the operating system that they prefer their app window to take up more or less of the available space.</span></span> <span data-ttu-id="b3d84-183">**DesiredRemainingView** kann auch verwendet werden, um anzugeben, dass die Quell-App nach dem Start des URI nicht weiter auf dem Bildschirm angezeigt werden muss und vollständig durch die Ziel-App ersetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="b3d84-183">**DesiredRemainingView** can also be used to indicate that the source app doesn't need to remain on screen after the URI launch and can be completely replaced by the target app.</span></span> <span data-ttu-id="b3d84-184">Mit dieser Eigenschaft wird nur die bevorzugte Fenstergröße der aufrufenden App angegeben.</span><span class="sxs-lookup"><span data-stu-id="b3d84-184">This property only specifies the preferred window size of the calling app.</span></span> <span data-ttu-id="b3d84-185">Es wird nicht das Verhalten anderer Apps angegeben, die ggf. zur gleichen Zeit auf dem Bildschirm angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b3d84-185">It doesn't specify the behavior of other apps that may happen to also be on screen at the same time.</span></span>

<span data-ttu-id="b3d84-186">**Hinweis:** Windows berücksichtigt zahlreicher Faktoren die Quell-app endgültige Fenstergröße, z. B. bestimmt, die Einstellung der Quell-app, die Anzahl der apps auf dem Bildschirm, bildschirmausrichtung und So weiter.</span><span class="sxs-lookup"><span data-stu-id="b3d84-186">**Note**Windows takes into account multiple different factors when it determines the source app's final window size, for example, the preference of the source app, the number of apps on screen, the screen orientation, and so on.</span></span> <span data-ttu-id="b3d84-187">Das Festlegen von [**DesiredRemainingView**](https://msdn.microsoft.com/library/windows/apps/dn298314) garantiert kein bestimmtes Fensterverhalten für die Quell-App.</span><span class="sxs-lookup"><span data-stu-id="b3d84-187">By setting [**DesiredRemainingView**](https://msdn.microsoft.com/library/windows/apps/dn298314), you aren't guaranteed a specific windowing behavior for the source app.</span></span>

```cs
// Set the desired remaining view.
var options = new Windows.System.LauncherOptions();
options.DesiredRemainingView = Windows.UI.ViewManagement.ViewSizePreference.UseLess;

// Launch the URI
var success = await Windows.System.Launcher.LaunchUriAsync(uriContoso, options);
```

## <a name="uri-schemes"></a><span data-ttu-id="b3d84-188">URI-Schemas</span><span class="sxs-lookup"><span data-stu-id="b3d84-188">URI Schemes</span></span> ##

<span data-ttu-id="b3d84-189">Die verschiedenen URI-Schemas werden im Folgenden beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b3d84-189">The various URI schemes are described below.</span></span>

### <a name="call-app-uri-scheme"></a><span data-ttu-id="b3d84-190">URI-Schema für das Aufrufen einer App</span><span class="sxs-lookup"><span data-stu-id="b3d84-190">Call app URI scheme</span></span>

<span data-ttu-id="b3d84-191">Sie können das URI-Schema **ms-call:** zum Starten der Anruf-App verwenden.</span><span class="sxs-lookup"><span data-stu-id="b3d84-191">Use the **ms-call:** URI scheme to launch the Call app.</span></span>

| <span data-ttu-id="b3d84-192">URI-Schema</span><span class="sxs-lookup"><span data-stu-id="b3d84-192">URI Scheme</span></span>       | <span data-ttu-id="b3d84-193">Ergebnis</span><span class="sxs-lookup"><span data-stu-id="b3d84-193">Result</span></span>                   |
|------------------|--------------------------|
| <span data-ttu-id="b3d84-194">ms-call:settings</span><span class="sxs-lookup"><span data-stu-id="b3d84-194">ms-call:settings</span></span> | <span data-ttu-id="b3d84-195">Einstellungsseite der Anruf-App.</span><span class="sxs-lookup"><span data-stu-id="b3d84-195">Calls app settings page.</span></span> |

### <a name="email-uri-scheme"></a><span data-ttu-id="b3d84-196">URI-Schema für E-Mail</span><span class="sxs-lookup"><span data-stu-id="b3d84-196">Email URI scheme</span></span>

<span data-ttu-id="b3d84-197">Sie können das URI-Schema **mailto:** verwenden, um die Standard-E-Mail-App zu starten.</span><span class="sxs-lookup"><span data-stu-id="b3d84-197">Use the **mailto:** URI scheme to launch the default mail app.</span></span>

| <span data-ttu-id="b3d84-198">URI-Schema</span><span class="sxs-lookup"><span data-stu-id="b3d84-198">URI Scheme</span></span> |<span data-ttu-id="b3d84-199">Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="b3d84-199">Results</span></span>                          |
|------------|---------------------------------|
| <span data-ttu-id="b3d84-200">mailto:</span><span class="sxs-lookup"><span data-stu-id="b3d84-200">mailto:</span></span>    | <span data-ttu-id="b3d84-201">Startet die Standard-E-Mail-App.</span><span class="sxs-lookup"><span data-stu-id="b3d84-201">Launches the default email app.</span></span> |
| <span data-ttu-id="b3d84-202">mailto:\[email address\]</span><span class="sxs-lookup"><span data-stu-id="b3d84-202">mailto:\[email address\]</span></span> | <span data-ttu-id="b3d84-203">Startet die E-Mail-App und erstellt eine neue Nachricht mit der angegebenen E-Mail-Adresse in der Zeile „An“.</span><span class="sxs-lookup"><span data-stu-id="b3d84-203">Launches the email app and creates a new message with the specified email address on the To line.</span></span> <span data-ttu-id="b3d84-204">Beachten Sie, dass die E-Mail nicht gesendet wird, bis der Benutzer auf „Senden“ tippt.</span><span class="sxs-lookup"><span data-stu-id="b3d84-204">Note that the email is not sent until the user taps send.</span></span> |

### <a name="http-uri-scheme"></a><span data-ttu-id="b3d84-205">HTTP-URI-Schema</span><span class="sxs-lookup"><span data-stu-id="b3d84-205">HTTP URI scheme</span></span>

<span data-ttu-id="b3d84-206">Sie können das URI-Schema **http:** verwenden, um den Standard-Webbrowser zu starten.</span><span class="sxs-lookup"><span data-stu-id="b3d84-206">Use the **http:** URI scheme to launch the default web browser.</span></span>

| <span data-ttu-id="b3d84-207">URI-Schema</span><span class="sxs-lookup"><span data-stu-id="b3d84-207">URI Scheme</span></span> | <span data-ttu-id="b3d84-208">Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="b3d84-208">Results</span></span>                           |
|------------|-----------------------------------|
| <span data-ttu-id="b3d84-209">http:</span><span class="sxs-lookup"><span data-stu-id="b3d84-209">http:</span></span>      | <span data-ttu-id="b3d84-210">Startet den Standardwebbrowser.</span><span class="sxs-lookup"><span data-stu-id="b3d84-210">Launches the default web browser.</span></span> |

### <a name="maps-app-uri-schemes"></a><span data-ttu-id="b3d84-211">URI-Schemas für die Karten-App</span><span class="sxs-lookup"><span data-stu-id="b3d84-211">Maps app URI schemes</span></span>

<span data-ttu-id="b3d84-212">Sie können die URI-Schemas **bingmaps:**, **ms-drive-to:** und **ms-walk-to:** zum [Starten der Windows-Karten-App](launch-maps-app.md) für bestimmte Karten, Wegbeschreibungen und Suchergebnisse verwenden.</span><span class="sxs-lookup"><span data-stu-id="b3d84-212">Use the **bingmaps:**, **ms-drive-to:**, and **ms-walk-to:** URI schemes to [launch the Windows Maps app](launch-maps-app.md) to specific maps, directions, and search results.</span></span> <span data-ttu-id="b3d84-213">Der folgende URI startet beispielsweise die Windows-Karten-App und zeigt eine über New York City zentrierte Karte an.</span><span class="sxs-lookup"><span data-stu-id="b3d84-213">For example, the following URI opens the Windows Maps app and displays a map centered over New York City.</span></span>

`bingmaps:?cp=40.726966~-74.006076`

![Ein Beispiel der Windows-Karten-App.](images/mapnyc.png)

<span data-ttu-id="b3d84-215">Weitere Informationen finden Sie unter [Starten der Windows-Karten-App](launch-maps-app.md).</span><span class="sxs-lookup"><span data-stu-id="b3d84-215">For more info, see [Launch the Windows Maps app](launch-maps-app.md).</span></span> <span data-ttu-id="b3d84-216">Informationen zum Verwenden des Kartensteuerelements in Ihrer eigenen App finden Sie unter [Anzeigen von Karten mit 2D-, 3D- und Streetside-Ansichten](https://msdn.microsoft.com/library/windows/apps/mt219695).</span><span class="sxs-lookup"><span data-stu-id="b3d84-216">To use the map control in your own app, see [Display maps with 2D, 3D, and Streetside views](https://msdn.microsoft.com/library/windows/apps/mt219695).</span></span>

### <a name="messaging-app-uri-scheme"></a><span data-ttu-id="b3d84-217">URI-Schema für die Messaging-App</span><span class="sxs-lookup"><span data-stu-id="b3d84-217">Messaging app URI scheme</span></span>

<span data-ttu-id="b3d84-218">Sie können das URI-Schema **ms-chat:** zum Starten der Windows Messaging-App verwenden.</span><span class="sxs-lookup"><span data-stu-id="b3d84-218">Use the **ms-chat:** URI scheme to launch the Windows Messaging app.</span></span>

| <span data-ttu-id="b3d84-219">URI-Schema</span><span class="sxs-lookup"><span data-stu-id="b3d84-219">URI scheme</span></span> |<span data-ttu-id="b3d84-220">Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="b3d84-220">Results</span></span> |
|------------|--------|
| <span data-ttu-id="b3d84-221">ms-chat:</span><span class="sxs-lookup"><span data-stu-id="b3d84-221">ms-chat:</span></span>   | <span data-ttu-id="b3d84-222">Startet die Messaging-App.</span><span class="sxs-lookup"><span data-stu-id="b3d84-222">Launches the Messaging app.</span></span> |
| <span data-ttu-id="b3d84-223">ms-chat:?ContactID={contacted}</span><span class="sxs-lookup"><span data-stu-id="b3d84-223">ms-chat:?ContactID={contacted}</span></span>  |  <span data-ttu-id="b3d84-224">Damit kann die Messaging-Anwendung mit den Informationen eines bestimmten Kontakts gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="b3d84-224">Allows the messaging application to be launched with a particular contact’s information.</span></span>   |
| <span data-ttu-id="b3d84-225">ms-chat:?Body={body}</span><span class="sxs-lookup"><span data-stu-id="b3d84-225">ms-chat:?Body={body}</span></span> | <span data-ttu-id="b3d84-226">Damit kann die Messaging-Anwendung mit einer Zeichenfolge gestartet werden, die als Inhalt der Nachricht verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b3d84-226">Allows the messaging application to be launched with a string to use as the content of the message.</span></span>|
| <span data-ttu-id="b3d84-227">ms-chat:?Addresses={address}&Body={body}</span><span class="sxs-lookup"><span data-stu-id="b3d84-227">ms-chat:?Addresses={address}&Body={body}</span></span> | <span data-ttu-id="b3d84-228">Damit kann die Messaging-Anwendung mit bestimmten Adressinformationen und einer Zeichenfolge gestartet werden, die als Inhalt der Nachricht verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="b3d84-228">Allows the messaging application to be launched with a particular addresses' information, and with a string to use as the content of the message.</span></span> <span data-ttu-id="b3d84-229">Hinweis: Die Adressen können verkettet werden.</span><span class="sxs-lookup"><span data-stu-id="b3d84-229">Note: Addresses can be concatenated.</span></span> |
| <span data-ttu-id="b3d84-230">ms-chat:?TransportId={transportId}</span><span class="sxs-lookup"><span data-stu-id="b3d84-230">ms-chat:?TransportId={transportId}</span></span>  | <span data-ttu-id="b3d84-231">Ermöglicht das Starten der Messaging-Anwendung mit einer bestimmten Transport-ID.</span><span class="sxs-lookup"><span data-stu-id="b3d84-231">Allows the messaging application to be launched with a particular transport ID.</span></span> |

### <a name="tone-picker-uri-scheme"></a><span data-ttu-id="b3d84-232">URI-Schema für die Tonauswahl</span><span class="sxs-lookup"><span data-stu-id="b3d84-232">Tone picker URI scheme</span></span>

<span data-ttu-id="b3d84-233">Sie können das URI-Schema **ms-tonepicker:** verwenden, um Klingeltöne, Alarmtöne und Systemtöne zu wählen.</span><span class="sxs-lookup"><span data-stu-id="b3d84-233">Use the **ms-tonepicker:** URI scheme to choose ringtones, alarms, and system tones.</span></span> <span data-ttu-id="b3d84-234">Außerdem können Sie neue Klingeltöne speichern und den Anzeigenamen eines Tons abrufen.</span><span class="sxs-lookup"><span data-stu-id="b3d84-234">You can also save new ringtones and get the display name of a tone.</span></span>

| <span data-ttu-id="b3d84-235">URI-Schema</span><span class="sxs-lookup"><span data-stu-id="b3d84-235">URI Scheme</span></span> | <span data-ttu-id="b3d84-236">Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="b3d84-236">Results</span></span> |
|------------|---------|
| <span data-ttu-id="b3d84-237">ms-tonepicker:</span><span class="sxs-lookup"><span data-stu-id="b3d84-237">ms-tonepicker:</span></span> | <span data-ttu-id="b3d84-238">Wählen Sie Klingeltöne, Alarmtöne und Systemtöne aus.</span><span class="sxs-lookup"><span data-stu-id="b3d84-238">Pick ringtones, alarms, and system tones.</span></span> |

<span data-ttu-id="b3d84-239">Die Parameter werden über einen [ValueSet](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset.aspx) an die LaunchURI-API übergeben.</span><span class="sxs-lookup"><span data-stu-id="b3d84-239">Parameters are passed via a [ValueSet](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset.aspx) to the LaunchURI API.</span></span> <span data-ttu-id="b3d84-240">Weitere Informationen finden Sie unter [Auswählen und Speichern von Tönen mit dem URI-Schema „ms-tonepicker“](launch-ringtone-picker.md).</span><span class="sxs-lookup"><span data-stu-id="b3d84-240">See [Choose and save tones using the ms-tonepicker URI scheme](launch-ringtone-picker.md) for details.</span></span>

### <a name="nearby-numbers-app-uri-scheme"></a><span data-ttu-id="b3d84-241">URI-Schema für die Nearby Numbers-App</span><span class="sxs-lookup"><span data-stu-id="b3d84-241">Nearby Numbers app URI scheme</span></span>

<span data-ttu-id="b3d84-242">Sie können das URI-Schema **ms-yellowpage:** zum Starten der Nearby Numbers-App verwenden.</span><span class="sxs-lookup"><span data-stu-id="b3d84-242">Use the **ms-yellowpage:** URI scheme to launch the Nearby Numbers app.</span></span>

| <span data-ttu-id="b3d84-243">URI-Schema</span><span class="sxs-lookup"><span data-stu-id="b3d84-243">URI Scheme</span></span> | <span data-ttu-id="b3d84-244">Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="b3d84-244">Results</span></span> |
|------------|---------|
| <span data-ttu-id="b3d84-245">ms-yellowpage:?input=\[keyword\]&method=\[String oder T9\]</span><span class="sxs-lookup"><span data-stu-id="b3d84-245">ms-yellowpage:?input=\[keyword\]&method=\[String or T9\]</span></span> | <span data-ttu-id="b3d84-246">Startet die Nearby Numbers-App.</span><span class="sxs-lookup"><span data-stu-id="b3d84-246">Launches the Nearby Numbers app.</span></span><br>`input` <span data-ttu-id="b3d84-247">bezieht sich auf das Schlüsselwort, nach dem Sie suchen möchten.</span><span class="sxs-lookup"><span data-stu-id="b3d84-247">refers to the keyword you want to search.</span></span><br>`method` <span data-ttu-id="b3d84-248">bezieht sich auf den Typ der Suche (Zeichenfolge- oder T9-Suche).</span><span class="sxs-lookup"><span data-stu-id="b3d84-248">refers to the type of search (string or T9 search).</span></span><br><span data-ttu-id="b3d84-249">Wenn `method` `T9` ist (eine Art der Tastatur), dann sollte `keyword` eine numerische Zeichenfolge sein, die der T9-Tastatur Buchstaben zuordnet, nach denen gesucht werden soll.</span><span class="sxs-lookup"><span data-stu-id="b3d84-249">If `method` is `T9` (a type of keyboard) then `keyword` should be a numeric string that maps to the T9 keyboard letters to search for.</span></span><br><span data-ttu-id="b3d84-250">Wenn `method` `String` ist, dann ist `keyword` das Schlüsselwort, nach dem gesucht werden soll.</span><span class="sxs-lookup"><span data-stu-id="b3d84-250">If `method` is `String` then `keyword` is the keyword to search for.</span></span> |

### <a name="people-app-uri-scheme"></a><span data-ttu-id="b3d84-251">URI-Schema für die Kontakte-App</span><span class="sxs-lookup"><span data-stu-id="b3d84-251">People app URI scheme</span></span>

<span data-ttu-id="b3d84-252">Sie können das URI-Schema **ms-people:** zum Starten der Kontakte-App verwenden.</span><span class="sxs-lookup"><span data-stu-id="b3d84-252">Use the **ms-people:** URI scheme to launch the People app.</span></span>
<span data-ttu-id="b3d84-253">Weitere Informationen finden Sie unter [Starten der Kontakte-App](launch-people-apps.md).</span><span class="sxs-lookup"><span data-stu-id="b3d84-253">For more info, see [Launch the People app](launch-people-apps.md).</span></span>

### <a name="photos-app-uri-scheme"></a><span data-ttu-id="b3d84-254">URI-Schema für die Fotos-App</span><span class="sxs-lookup"><span data-stu-id="b3d84-254">Photos app URI scheme</span></span>

<span data-ttu-id="b3d84-255">Sie können das URI-Schema **ms-Fotos:** zum Starten der Fotos-App verwenden, um ein Bild anzuzeigen oder ein Video zu bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="b3d84-255">Use the **ms-photos:** URI scheme to launch the Photos app to view an image or edit a video.</span></span> <span data-ttu-id="b3d84-256">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="b3d84-256">For example:</span></span>  
<span data-ttu-id="b3d84-257">So zeigen Sie ein Bild an:</span><span class="sxs-lookup"><span data-stu-id="b3d84-257">To view an image:</span></span> `ms-photos:viewer?fileName=c:\users\userName\Pictures\image.jpg`  
<span data-ttu-id="b3d84-258">Alternativ können Sie so ein Video bearbeiten:</span><span class="sxs-lookup"><span data-stu-id="b3d84-258">Or to edit a video:</span></span> `ms-photos:videoedit?InputToken=123abc&Action=Trim&StartTime=01:02:03`  

> [!NOTE]
> <span data-ttu-id="b3d84-259">Die URIs zum Bearbeiten von Videos oder Anzeigen von Bildern sind nur auf dem Desktop verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b3d84-259">The URIs to edit a video or display an image are only available on desktop.</span></span>

| <span data-ttu-id="b3d84-260">URI-Schema</span><span class="sxs-lookup"><span data-stu-id="b3d84-260">URI scheme</span></span> |<span data-ttu-id="b3d84-261">Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="b3d84-261">Results</span></span> |
|------------|--------|
| <span data-ttu-id="b3d84-262">ms-photos:viewer?fileName={filename}</span><span class="sxs-lookup"><span data-stu-id="b3d84-262">ms-photos:viewer?fileName={filename}</span></span> | <span data-ttu-id="b3d84-263">Startet die Fotos-App, um das gewünschte Bild anzuzeigen. {filename} muss ein vollqualifizierter Pfadname sein.</span><span class="sxs-lookup"><span data-stu-id="b3d84-263">Launches the Photos app to view the specified image where {filename} is a fully-qualified path name.</span></span> <span data-ttu-id="b3d84-264">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="b3d84-264">For example:</span></span> `c:\users\userName\Pictures\ImageToView.jpg` |
| <span data-ttu-id="b3d84-265">ms-photos:videoedit?InputToken={input token}</span><span class="sxs-lookup"><span data-stu-id="b3d84-265">ms-photos:videoedit?InputToken={input token}</span></span> | <span data-ttu-id="b3d84-266">Startet die Fotos-App im Videobearbeitungsmodus für die Datei, die durch das Dateitoken dargestellt wird.</span><span class="sxs-lookup"><span data-stu-id="b3d84-266">Launches the Photos app in video editing mode for the file represented by the file token.</span></span> <span data-ttu-id="b3d84-267">**InputToken** ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="b3d84-267">**InputToken** is required.</span></span> <span data-ttu-id="b3d84-268">Sie können den [SharedStorageAccessManager](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.DataTransfer.SharedStorageAccessManager) verwenden, um ein Dateitoken zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="b3d84-268">Use the  [SharedStorageAccessManager](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.DataTransfer.SharedStorageAccessManager) to get a token for a file.</span></span> |
| <span data-ttu-id="b3d84-269">ms-photos:videoedit?Action={action}</span><span class="sxs-lookup"><span data-stu-id="b3d84-269">ms-photos:videoedit?Action={action}</span></span> | <span data-ttu-id="b3d84-270">Ein optionaler Parameter, der die Fotos-App im angegebenen Videobearbeitungsmodus öffnet. {Action} steht für eine der folgenden Optionen: **SlowMotion**, **FrameExtraction**, **Kürzen**, **Ansicht**, **Freihand**.</span><span class="sxs-lookup"><span data-stu-id="b3d84-270">An optional parameter that opens the Photos app in the specified video editing mode where {action} is one of: **SlowMotion**, **FrameExtraction**, **Trim**, **View**, **Ink**.</span></span> <span data-ttu-id="b3d84-271">Wenn keine Angabe erfolgt, wird standardmäßig **Ansicht** verwendet</span><span class="sxs-lookup"><span data-stu-id="b3d84-271">If not specified, defaults to **View**</span></span> |
| <span data-ttu-id="b3d84-272">ms-photos:videoedit?StartTime={timespan}</span><span class="sxs-lookup"><span data-stu-id="b3d84-272">ms-photos:videoedit?StartTime={timespan}</span></span> | <span data-ttu-id="b3d84-273">Ein optionaler Parameter, der angibt, wo die Wiedergabe des Videos beginnt.</span><span class="sxs-lookup"><span data-stu-id="b3d84-273">An optional parameter that specifies where to start playing the video.</span></span> `{timespan}` <span data-ttu-id="b3d84-274">muss im Format `"hh:mm:ss.ffff"` vorliegen.</span><span class="sxs-lookup"><span data-stu-id="b3d84-274">must be in the format `"hh:mm:ss.ffff"`.</span></span> <span data-ttu-id="b3d84-275">Wenn keine Angabe erfolgt:</span><span class="sxs-lookup"><span data-stu-id="b3d84-275">If not specified, defaults to</span></span> `00:00:00.0000` |

### <a name="settings-app-uri-scheme"></a><span data-ttu-id="b3d84-276">URI-Schema für die Einstellungs-App</span><span class="sxs-lookup"><span data-stu-id="b3d84-276">Settings app URI scheme</span></span>

<span data-ttu-id="b3d84-277">Sie können das URI-Schema **ms-settings:** zum [Starten der Windows-Einstellungs-App](launch-settings-app.md) verwenden.</span><span class="sxs-lookup"><span data-stu-id="b3d84-277">Use the **ms-settings:** URI scheme to [launch the Windows Settings app](launch-settings-app.md).</span></span> <span data-ttu-id="b3d84-278">Das Starten der Einstellungs-App ist ein wichtiger Bestandteil beim Schreiben einer App mit Berücksichtigung von Datenschutz.</span><span class="sxs-lookup"><span data-stu-id="b3d84-278">Launching to the Settings app is an important part of writing a privacy-aware app.</span></span> <span data-ttu-id="b3d84-279">Wenn Ihre App nicht auf eine sensible Ressource zugreifen kann, wird empfohlen, dem Benutzer einen praktischen Link zu den Datenschutzeinstellungen für diese Ressource bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="b3d84-279">If your app can't access a sensitive resource, we recommend providing the user a convenient link to the privacy settings for that resource.</span></span> <span data-ttu-id="b3d84-280">Folgender URI öffnet beispielsweise die Einstellungs-App und zeigt die Datenschutzeinstellungen für die Kamera an.</span><span class="sxs-lookup"><span data-stu-id="b3d84-280">For example, the following URI opens the Settings app and displays the camera privacy settings.</span></span>

`ms-settings:privacy-webcam`

![Datenschutzeinstellungen für die Kamera.](images/privacyawarenesssettingsapp.png)

<span data-ttu-id="b3d84-282">Weitere Informationen finden Sie unter [Starten der Einstellungs-App von Windows](launch-settings-app.md) und [Richtlinien für Apps mit Berücksichtigung von Datenschutz](https://msdn.microsoft.com/library/windows/apps/hh768223).</span><span class="sxs-lookup"><span data-stu-id="b3d84-282">For more info, see [Launch the Windows Settings app](launch-settings-app.md) and [Guidelines for privacy-aware apps](https://msdn.microsoft.com/library/windows/apps/hh768223).</span></span>

### <a name="store-app-uri-scheme"></a><span data-ttu-id="b3d84-283">URI-Schema für die Store-App</span><span class="sxs-lookup"><span data-stu-id="b3d84-283">Store app URI scheme</span></span>

<span data-ttu-id="b3d84-284">Sie können das URI-Schema **ms-windows-store:** zum [Starten der UWP-App](launch-store-app.md) verwenden.</span><span class="sxs-lookup"><span data-stu-id="b3d84-284">Use the **ms-windows-store:** URI scheme to [Launch the UWP app](launch-store-app.md).</span></span> <span data-ttu-id="b3d84-285">Öffnen Sie Seiten mit Produktdetails, Produktbewertungen sowie Suchseiten. Der folgende URI öffnet z.B. die UWP-App und startet die Store-Startseite.</span><span class="sxs-lookup"><span data-stu-id="b3d84-285">Open product detail pages, product review pages, and search pages, etc. For example, the following URI opens the UWP app and launches the home page of the Store.</span></span>

`ms-windows-store://home/`

<span data-ttu-id="b3d84-286">Weitere Informationen finden Sie unter [Starten der UWP-App](launch-store-app.md).</span><span class="sxs-lookup"><span data-stu-id="b3d84-286">For more info, see [Launch the UWP app](launch-store-app.md).</span></span>

### <a name="weather-app-uri-scheme"></a><span data-ttu-id="b3d84-287">URI-Schema für Wetter-app</span><span class="sxs-lookup"><span data-stu-id="b3d84-287">Weather app URI scheme</span></span>

<span data-ttu-id="b3d84-288">Verwenden der **Msnweather:** zum Starten der Wetter-app-URI-Schema.</span><span class="sxs-lookup"><span data-stu-id="b3d84-288">Use the **msnweather:** URI scheme to launch the Weather app.</span></span>

| <span data-ttu-id="b3d84-289">URI-Schema</span><span class="sxs-lookup"><span data-stu-id="b3d84-289">URI Scheme</span></span> | <span data-ttu-id="b3d84-290">Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="b3d84-290">Results</span></span> |
|------------|---------|
| <span data-ttu-id="b3d84-291">Msnweather://Forecast?LA= \[latitude\]&lo=\[longitude\]</span><span class="sxs-lookup"><span data-stu-id="b3d84-291">msnweather://forecast?la=\[latitude\]&lo=\[longitude\]</span></span> | <span data-ttu-id="b3d84-292">Startet die Wetter-app in die Planung Seite basierend auf einen geografischen Standort-Koordinaten.</span><span class="sxs-lookup"><span data-stu-id="b3d84-292">Launches the Weather app in the Forecast page based on a location geographic coordinates.</span></span><br>`latitude` <span data-ttu-id="b3d84-293">bezieht sich auf der Breitengrad des Speicherorts.</span><span class="sxs-lookup"><span data-stu-id="b3d84-293">refers to the latitude of the location.</span></span><br> `longitude` <span data-ttu-id="b3d84-294">bezieht sich auf die Länge der Position.</span><span class="sxs-lookup"><span data-stu-id="b3d84-294">refers to the longitude of the location.</span></span><br> |
