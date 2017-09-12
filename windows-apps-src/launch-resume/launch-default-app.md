---
author: TylerMSFT
title: "Starten der Standard-App für einen URI"
description: "Erfahren Sie, wie Sie die Standard-App für einen Uniform Resource Identifier (URI) starten. URIs ermöglichen den Start einer anderen App zum Ausführen einer bestimmten Aufgabe. Dieses Thema enthält auch eine Übersicht über die zahlreichen in Windows integrierten URI-Schemas."
ms.assetid: 7B0D0AF5-D89E-4DB0-9B79-90201D79974F
ms.author: twhitney
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.openlocfilehash: 0fe93670739a89c9416fdbfc28117a794a6a345d
ms.sourcegitcommit: ca060f051e696da2c1e26e9dd4d2da3fa030103d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2017
---
# <a name="launch-the-default-app-for-a-uri"></a><span data-ttu-id="d3aab-106">Starten der Standard-App für einen URI</span><span class="sxs-lookup"><span data-stu-id="d3aab-106">Launch the default app for a URI</span></span>

<span data-ttu-id="d3aab-107">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="d3aab-107">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="d3aab-108">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="d3aab-108">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

**<span data-ttu-id="d3aab-109">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="d3aab-109">Important APIs</span></span>**

- [**<span data-ttu-id="d3aab-110">LaunchUriAsync</span><span class="sxs-lookup"><span data-stu-id="d3aab-110">LaunchUriAsync</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh701476)
-  [**<span data-ttu-id="d3aab-111">PreferredApplicationPackageFamilyName</span><span class="sxs-lookup"><span data-stu-id="d3aab-111">PreferredApplicationPackageFamilyName</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh965482)
- [**<span data-ttu-id="d3aab-112">DesiredRemainingView</span><span class="sxs-lookup"><span data-stu-id="d3aab-112">DesiredRemainingView</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn298314)

<span data-ttu-id="d3aab-113">Hier erfahren Sie, wie Sie die Standard-App für einen Uniform Resource Identifier (URI) starten.</span><span class="sxs-lookup"><span data-stu-id="d3aab-113">Learn how to launch the default app for a Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="d3aab-114">URIs ermöglichen den Start einer anderen App zum Ausführen einer bestimmten Aufgabe.</span><span class="sxs-lookup"><span data-stu-id="d3aab-114">URIs allow you to launch another app to perform a specific task.</span></span> <span data-ttu-id="d3aab-115">Dieses Thema enthält auch eine Übersicht über die vielen in Windows integrierten URI-Schemas.</span><span class="sxs-lookup"><span data-stu-id="d3aab-115">This topic also provides an overview of the many URI schemes built into Windows.</span></span> <span data-ttu-id="d3aab-116">Sie können außerdem benutzerdefinierte URIs starten.</span><span class="sxs-lookup"><span data-stu-id="d3aab-116">You can launch custom URIs too.</span></span> <span data-ttu-id="d3aab-117">Weitere Informationen zum Registrieren eines benutzerdefinierten URI-Schemas und Behandeln der URI-Aktivierung finden Sie unter [Behandeln der URI-Aktivierung](handle-uri-activation.md).</span><span class="sxs-lookup"><span data-stu-id="d3aab-117">For more info about registering a custom URI scheme and handling URI activation, see [Handle URI activation](handle-uri-activation.md).</span></span>


<span data-ttu-id="d3aab-118">Mit URI-Schemas können Sie Apps öffnen, indem Sie auf Hyperlinks klicken.</span><span class="sxs-lookup"><span data-stu-id="d3aab-118">URI schemes let you open apps by clicking hyperlinks.</span></span> <span data-ttu-id="d3aab-119">Genau wie Sie eine neue E-Mail mit **mailto:** öffnen, können Sie den Standardwebbrowser mit **http:** öffnen.</span><span class="sxs-lookup"><span data-stu-id="d3aab-119">Just as you can start a new email using **mailto:**, you can open the default web browser using **http:**</span></span>

<span data-ttu-id="d3aab-120">In diesem Thema werden einige der folgenden URI-Schemas beschrieben, die in Windows integriert sind:</span><span class="sxs-lookup"><span data-stu-id="d3aab-120">This topic describes the following URI schemes built into Windows:</span></span>

| <span data-ttu-id="d3aab-121">URI-Schema</span><span class="sxs-lookup"><span data-stu-id="d3aab-121">URI Scheme</span></span> | <span data-ttu-id="d3aab-122">Startet</span><span class="sxs-lookup"><span data-stu-id="d3aab-122">Launches</span></span> |
| -------|--------------|
|[<span data-ttu-id="d3aab-123">bingmaps:, ms-drive-to: und ms-walk-to:</span><span class="sxs-lookup"><span data-stu-id="d3aab-123">bingmaps:, ms-drive-to:, and ms-walk-to:</span></span> ](#maps-app-uri-schemes) | <span data-ttu-id="d3aab-124">Karten-App</span><span class="sxs-lookup"><span data-stu-id="d3aab-124">Maps app</span></span> |
|[<span data-ttu-id="d3aab-125">http:</span><span class="sxs-lookup"><span data-stu-id="d3aab-125">http:</span></span>](#http-uri-scheme) | <span data-ttu-id="d3aab-126">Standardwebbrowser</span><span class="sxs-lookup"><span data-stu-id="d3aab-126">Default web browser</span></span> |
|[<span data-ttu-id="d3aab-127">mailto:</span><span class="sxs-lookup"><span data-stu-id="d3aab-127">mailto:</span></span>](#email-uri-scheme) | <span data-ttu-id="d3aab-128">Standard-E-Mail-App</span><span class="sxs-lookup"><span data-stu-id="d3aab-128">Default email app</span></span> |
|[<span data-ttu-id="d3aab-129">ms-call:</span><span class="sxs-lookup"><span data-stu-id="d3aab-129">ms-call:</span></span>](#call-app-uri-scheme) |  <span data-ttu-id="d3aab-130">Anruf-App</span><span class="sxs-lookup"><span data-stu-id="d3aab-130">Call app</span></span> |
|[<span data-ttu-id="d3aab-131">ms-chat:</span><span class="sxs-lookup"><span data-stu-id="d3aab-131">ms-chat:</span></span>](#messaging-app-uri-scheme) | <span data-ttu-id="d3aab-132">Messaging-App</span><span class="sxs-lookup"><span data-stu-id="d3aab-132">Messaging app</span></span> |
|[<span data-ttu-id="d3aab-133">ms-people:</span><span class="sxs-lookup"><span data-stu-id="d3aab-133">ms-people:</span></span>](#people-app-uri-scheme) | <span data-ttu-id="d3aab-134">Kontakte-App</span><span class="sxs-lookup"><span data-stu-id="d3aab-134">People app</span></span> |
|[<span data-ttu-id="d3aab-135">ms-settings:</span><span class="sxs-lookup"><span data-stu-id="d3aab-135">ms-settings:</span></span>](#settings-app-uri-scheme) | <span data-ttu-id="d3aab-136">Einstellungs-App</span><span class="sxs-lookup"><span data-stu-id="d3aab-136">Settings app</span></span> |
|[<span data-ttu-id="d3aab-137">ms-store:</span><span class="sxs-lookup"><span data-stu-id="d3aab-137">ms-store:</span></span>](#store-app-uri-scheme)  | <span data-ttu-id="d3aab-138">Store-App</span><span class="sxs-lookup"><span data-stu-id="d3aab-138">Store app</span></span> |
|[<span data-ttu-id="d3aab-139">ms-tonepicker:</span><span class="sxs-lookup"><span data-stu-id="d3aab-139">ms-tonepicker:</span></span>](#tone-picker-uri-scheme) | <span data-ttu-id="d3aab-140">Tonauswahl</span><span class="sxs-lookup"><span data-stu-id="d3aab-140">Tone picker</span></span> |
|[<span data-ttu-id="d3aab-141">ms-yellowpage:</span><span class="sxs-lookup"><span data-stu-id="d3aab-141">ms-yellowpage:</span></span>](#nearby-numbers-app-uri-scheme) | <span data-ttu-id="d3aab-142">Nearby Numbers-App</span><span class="sxs-lookup"><span data-stu-id="d3aab-142">Nearby Numbers app</span></span> |

<br> <span data-ttu-id="d3aab-143">Der folgende URI öffnet beispielsweise den Standardbrowser und zeigt die Bing-Website an.</span><span class="sxs-lookup"><span data-stu-id="d3aab-143">For example, the following URI opens the default browser and displays the Bing web site.</span></span>

`http://bing.com`

<span data-ttu-id="d3aab-144">Sie können außerdem benutzerdefinierte URI-Schemas starten.</span><span class="sxs-lookup"><span data-stu-id="d3aab-144">You can also launch custom URI schemes too.</span></span> <span data-ttu-id="d3aab-145">Wenn zum Behandeln dieses URI keine App installiert ist, können Sie dem Benutzer die Installation einer App empfehlen.</span><span class="sxs-lookup"><span data-stu-id="d3aab-145">If there is no app installed to handle that URI, you can recommend an app for the user to install.</span></span> <span data-ttu-id="d3aab-146">Weitere Informationen erhalten Sie unter [Empfehlen einer App, wenn keine App zur Behandlung des URI verfügbar ist](#recommend-an-app-if-one-is-not-available-to-handle-the-uri).</span><span class="sxs-lookup"><span data-stu-id="d3aab-146">For more info, see [Recommend an app if one is not available to handle the URI](#recommend-an-app-if-one-is-not-available-to-handle-the-uri).</span></span>

<span data-ttu-id="d3aab-147">Im Allgemeinen kann die App nicht die App auswählen, die gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="d3aab-147">In general, your app can't select the app that is launched.</span></span> <span data-ttu-id="d3aab-148">Der Benutzer entscheidet, welche App gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="d3aab-148">The user determines which app is launched.</span></span> <span data-ttu-id="d3aab-149">Zum Behandeln desselben URI-Schemas kann mehr als eine App registriert werden.</span><span class="sxs-lookup"><span data-stu-id="d3aab-149">More than one app can register to handle the same URI scheme.</span></span> <span data-ttu-id="d3aab-150">Die einzige Ausnahme sind reservierte URI-Schemas.</span><span class="sxs-lookup"><span data-stu-id="d3aab-150">The exception to this is for reserved URI schemes.</span></span> <span data-ttu-id="d3aab-151">Registrierungen der reservierten URI-Schemas werden ignoriert.</span><span class="sxs-lookup"><span data-stu-id="d3aab-151">Registrations of reserved URI schemes are ignored.</span></span> <span data-ttu-id="d3aab-152">Die vollständige Liste der reservierten URI-Schemas finden Sie unter [Behandeln der URI-Aktivierung](handle-uri-activation.md).</span><span class="sxs-lookup"><span data-stu-id="d3aab-152">For the full list of reserved URI schemes, see [Handle URI activation](handle-uri-activation.md).</span></span> <span data-ttu-id="d3aab-153">In Fällen, in denen mehrere Apps das gleiche URI-Schema registriert haben, kann Ihre App das Starten einer bestimmten App empfehlen.</span><span class="sxs-lookup"><span data-stu-id="d3aab-153">In cases where more than one app may have registered the same URI scheme, your app can recommend a specific app to be launched.</span></span> <span data-ttu-id="d3aab-154">Weitere Informationen finden Sie unter [Empfehlen einer App, wenn keine App zur Behandlung des URI verfügbar ist](#recommend-an-app-if-one-is-not-available-to-handle-the-uri).</span><span class="sxs-lookup"><span data-stu-id="d3aab-154">For more info, see [Recommend an app if one is not available to handle the URI](#recommend-an-app-if-one-is-not-available-to-handle-the-uri).</span></span>

### <a name="call-launchuriasync-to-launch-a-uri"></a><span data-ttu-id="d3aab-155">Aufruf von „LaunchUriAsync“ zum Starten eines URI</span><span class="sxs-lookup"><span data-stu-id="d3aab-155">Call LaunchUriAsync to launch a URI</span></span>

<span data-ttu-id="d3aab-156">Verwenden Sie die Methode [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476), um einen URI zu starten.</span><span class="sxs-lookup"><span data-stu-id="d3aab-156">Use the [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476) method to launch a URI.</span></span> <span data-ttu-id="d3aab-157">Beim Aufrufen dieser Methode muss Ihre App im Vordergrund ausgeführt werden, d.h., sie muss für den Benutzer sichtbar sein.</span><span class="sxs-lookup"><span data-stu-id="d3aab-157">When you call this method, your app must be the foreground app, that is, it must be visible to the user.</span></span> <span data-ttu-id="d3aab-158">Mithilfe dieser Anforderung wird sichergestellt, dass der Benutzer zu jedem Zeitpunkt die Kontrolle behält.</span><span class="sxs-lookup"><span data-stu-id="d3aab-158">This requirement helps ensure that the user remains in control.</span></span> <span data-ttu-id="d3aab-159">Verknüpfen Sie alle URI-Startvorgänge direkt mit der Benutzeroberfläche Ihrer App, um sicherzustellen, dass diese Anforderung erfüllt wird.</span><span class="sxs-lookup"><span data-stu-id="d3aab-159">To meet this requirement, make sure that you tie all URI launches directly to the UI of your app.</span></span> <span data-ttu-id="d3aab-160">Der Benutzer muss immer eine Aktion ausführen, um einen URI zu starten.</span><span class="sxs-lookup"><span data-stu-id="d3aab-160">The user must always take some action to initiate a URI launch.</span></span> <span data-ttu-id="d3aab-161">Wenn Sie versuchen, einen URI zu starten, und Ihre App befindet sich nicht im Vordergrund, schlägt der Start fehl und Ihr Fehlerrückruf wird aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="d3aab-161">If you attempt to launch a URI and your app isn't in the foreground, the launch will fail and your error callback will be invoked.</span></span>

<span data-ttu-id="d3aab-162">Erstellen Sie zunächst ein [**System.Uri**](https://msdn.microsoft.com/library/windows/apps/system.uri.aspx)-Objekt, das den URI darstellt, und übergeben Sie es anschließend an die Methode [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476).</span><span class="sxs-lookup"><span data-stu-id="d3aab-162">First create a [**System.Uri**](https://msdn.microsoft.com/library/windows/apps/system.uri.aspx) object to represent the URI, then pass that to the [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476) method.</span></span> <span data-ttu-id="d3aab-163">Verwenden Sie das Ergebnis, um zu überprüfen, ob der Aufruf erfolgreich war, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="d3aab-163">Use the return result to see if the call succeeded, as shown in the following example.</span></span>

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

<span data-ttu-id="d3aab-164">In einigen Fällen fordert das Betriebssystem den Benutzer dazu auf, zu prüfen, ob er tatsächlich Apps wechseln möchte.</span><span class="sxs-lookup"><span data-stu-id="d3aab-164">In some cases, the operating system will prompt the user to see if they actually want to switch apps.</span></span>

![Überlagerndes Warndialogfeld in der App auf grauem Hintergrund.](images/warningdialog.png)

<span data-ttu-id="d3aab-168">Wenn diese Aufforderung stets erfolgen soll, verwenden Sie die Eigenschaft [**Windows.System.LauncherOptions.TreatAsUntrusted**](https://msdn.microsoft.com/library/windows/apps/hh701442), um anzugeben, dass das Betriebssystem eine Warnung anzeigen soll.</span><span class="sxs-lookup"><span data-stu-id="d3aab-168">If you always want this prompt to occur, use the [**Windows.System.LauncherOptions.TreatAsUntrusted**](https://msdn.microsoft.com/library/windows/apps/hh701442) property to tell the operating system to display a warning.</span></span>

```cs
// The URI to launch
var uriBing = new Uri(@"http://www.bing.com");

// Set the option to show a warning
var promptOptions = new Windows.System.LauncherOptions();
promptOptions.TreatAsUntrusted = true;

// Launch the URI
var success = await Windows.System.Launcher.LaunchUriAsync(uriBing, promptOptions);
```

### <a name="recommend-an-app-if-one-is-not-available-to-handle-the-uri"></a><span data-ttu-id="d3aab-169">Empfehlen einer App, wenn keine App zur Behandlung des URI verfügbar ist</span><span class="sxs-lookup"><span data-stu-id="d3aab-169">Recommend an app if one is not available to handle the URI</span></span>

<span data-ttu-id="d3aab-170">Es kann jedoch sein, dass der Benutzer nicht über die erforderliche App zum Bearbeiten des aufgerufenen URI verfügt.</span><span class="sxs-lookup"><span data-stu-id="d3aab-170">In some cases, the user might not have an app installed to handle the URI that you are launching.</span></span> <span data-ttu-id="d3aab-171">In diesen Fällen bietet das Betriebssystem standardmäßig einen Link an, über den Benutzer im Store nach einer geeigneten App suchen können.</span><span class="sxs-lookup"><span data-stu-id="d3aab-171">By default, the operating system handles these cases by providing the user with a link to search for an appropriate app on the store.</span></span> <span data-ttu-id="d3aab-172">Wenn Sie dem Benutzer eine bestimmte App für dieses spezifische Szenario empfehlen möchten, können Sie die Empfehlung zusammen mit dem gestarteten URI übergeben.</span><span class="sxs-lookup"><span data-stu-id="d3aab-172">If you want to give the user a specific recommendation for which app to acquire in this scenario, you can do so by passing that recommendation along with the URI that you are launching.</span></span>

<span data-ttu-id="d3aab-173">Empfehlungen sind auch nützlich, wenn mehr als eine App zum Behandeln eines URI-Schema registriert wurde.</span><span class="sxs-lookup"><span data-stu-id="d3aab-173">Recommendations are also useful when more than one app has registered to handle a URI scheme.</span></span> <span data-ttu-id="d3aab-174">Durch die Empfehlung einer bestimmten App öffnet Windows die App, wenn sie bereits installiert ist.</span><span class="sxs-lookup"><span data-stu-id="d3aab-174">By recommending a specific app, Windows will open that app if it is already installed.</span></span>

<span data-ttu-id="d3aab-175">Rufen Sie dazu die Methode [**Windows.System.Launcher.LaunchUriAsync(Uri, LauncherOptions)**](https://msdn.microsoft.com/library/windows/apps/hh701484) auf, wobei [**LauncherOptions.preferredApplicationPackageFamilyName**](https://msdn.microsoft.com/library/windows/apps/hh965482) auf den Paketfamiliennamen der empfohlenen App im Store festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="d3aab-175">To make a recommendation, call the [**Windows.System.Launcher.LaunchUriAsync(Uri, LauncherOptions)**](https://msdn.microsoft.com/library/windows/apps/hh701484) method with [**LauncherOptions.preferredApplicationPackageFamilyName**](https://msdn.microsoft.com/library/windows/apps/hh965482) set to the package family name of the app in the store that you want to recommend.</span></span> <span data-ttu-id="d3aab-176">Diese Info wird vom Betriebssystem verwendet, um die allgemeine Option zum Suchen einer App im Store durch eine spezifische Option zum Erwerben der empfohlenen App im Store zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="d3aab-176">The operating system uses this info to replace the general option to search for an app in the store with a specific option to acquire the recommended app from the store.</span></span>

```cs
// Set the recommended app
var options = new Windows.System.LauncherOptions();
options.PreferredApplicationPackageFamilyName = "Contoso.URIApp_8wknc82po1e";
options.PreferredApplicationDisplayName = "Contoso URI Ap";

// Launch the URI and pass in the recommended app
// in case the user has no apps installed to handle the URI
var success = await Windows.System.Launcher.LaunchUriAsync(uriContoso, options);
```

### <a name="set-remaining-view-preference"></a><span data-ttu-id="d3aab-177">Festlegen der verbleibenden Ansichtseinstellung</span><span class="sxs-lookup"><span data-stu-id="d3aab-177">Set remaining view preference</span></span>

<span data-ttu-id="d3aab-178">Quell-Apps, die [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476) aufrufen, können anfordern, nach dem Start eines URIs auf dem Bildschirm zu verbleiben.</span><span class="sxs-lookup"><span data-stu-id="d3aab-178">Source apps that call [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476) can request that they remain on screen after a URI launch.</span></span> <span data-ttu-id="d3aab-179">Standardmäßig wird von Windows versucht, den gesamten verfügbaren Speicherplatz gleichmäßig zwischen der Quell- und der Ziel-App aufzuteilen, die den URI verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="d3aab-179">By default, Windows attempts to share all available space equally between the source app and the target app that handles the URI.</span></span> <span data-ttu-id="d3aab-180">Quell-Apps können die Eigenschaft [**DesiredRemainingView**](https://msdn.microsoft.com/library/windows/apps/dn298314) verwenden. Hiermit geben sie dem Betriebssystem an, mehr oder weniger des verfügbaren Speicherplatzes für ihr App-Fenster zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="d3aab-180">Source apps can use the [**DesiredRemainingView**](https://msdn.microsoft.com/library/windows/apps/dn298314) property to indicate to the operating system that they prefer their app window to take up more or less of the available space.</span></span> <span data-ttu-id="d3aab-181">**DesiredRemainingView** kann auch verwendet werden, um anzugeben, dass die Quell-App nach dem Start des URI nicht weiter auf dem Bildschirm angezeigt werden muss und vollständig durch die Ziel-App ersetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="d3aab-181">**DesiredRemainingView** can also be used to indicate that the source app doesn't need to remain on screen after the URI launch and can be completely replaced by the target app.</span></span> <span data-ttu-id="d3aab-182">Mit dieser Eigenschaft wird nur die bevorzugte Fenstergröße der aufrufenden App angegeben.</span><span class="sxs-lookup"><span data-stu-id="d3aab-182">This property only specifies the preferred window size of the calling app.</span></span> <span data-ttu-id="d3aab-183">Es wird nicht das Verhalten anderer Apps angegeben, die ggf. zur gleichen Zeit auf dem Bildschirm angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d3aab-183">It doesn't specify the behavior of other apps that may happen to also be on screen at the same time.</span></span>

<span data-ttu-id="d3aab-184">**Hinweis**  Windows bestimmt die endgültige Fenstergröße einer Quell-App anhand zahlreicher Faktoren (z.B. Einstellung der Quell-App, Anzahl der Apps auf dem Bildschirm, Bildschirmausrichtung).</span><span class="sxs-lookup"><span data-stu-id="d3aab-184">**Note**  Windows takes into account multiple different factors when it determines the source app's final window size, for example, the preference of the source app, the number of apps on screen, the screen orientation, and so on.</span></span> <span data-ttu-id="d3aab-185">Das Festlegen von [**DesiredRemainingView**](https://msdn.microsoft.com/library/windows/apps/dn298314) garantiert kein bestimmtes Fensterverhalten für die Quell-App.</span><span class="sxs-lookup"><span data-stu-id="d3aab-185">By setting [**DesiredRemainingView**](https://msdn.microsoft.com/library/windows/apps/dn298314), you aren't guaranteed a specific windowing behavior for the source app.</span></span>

```cs
// Set the desired remaining view.
var options = new Windows.System.LauncherOptions();
options.DesiredRemainingView = Windows.UI.ViewManagement.ViewSizePreference.UseLess;

// Launch the URI
var success = await Windows.System.Launcher.LaunchUriAsync(uriContoso, options);
```

## <a name="uri-schemes"></a><span data-ttu-id="d3aab-186">URI-Schemas</span><span class="sxs-lookup"><span data-stu-id="d3aab-186">URI Schemes</span></span> ##

<span data-ttu-id="d3aab-187">Die verschiedenen URI-Schemas werden im Folgenden beschrieben.</span><span class="sxs-lookup"><span data-stu-id="d3aab-187">The various URI schemes are described below.</span></span>
<br>

### <a name="call-app-uri-scheme"></a><span data-ttu-id="d3aab-188">URI-Schema für das Aufrufen einer App</span><span class="sxs-lookup"><span data-stu-id="d3aab-188">Call app URI scheme</span></span>

<span data-ttu-id="d3aab-189">Ihre App kann das URI-Schema **ms-call:** zum Starten der Anruf-App verwenden.</span><span class="sxs-lookup"><span data-stu-id="d3aab-189">Your app can use the **ms-call:** URI scheme to launch the Call app.</span></span>

| <span data-ttu-id="d3aab-190">URI-Schema</span><span class="sxs-lookup"><span data-stu-id="d3aab-190">URI Scheme</span></span>       | <span data-ttu-id="d3aab-191">Ergebnis</span><span class="sxs-lookup"><span data-stu-id="d3aab-191">Result</span></span>                   |
|------------------|--------------------------|
| <span data-ttu-id="d3aab-192">ms-call:settings</span><span class="sxs-lookup"><span data-stu-id="d3aab-192">ms-call:settings</span></span> | <span data-ttu-id="d3aab-193">Einstellungsseite der Anruf-App.</span><span class="sxs-lookup"><span data-stu-id="d3aab-193">Calls app settings page.</span></span> | 
<br>
### <a name="email-uri-scheme"></a><span data-ttu-id="d3aab-194">URI-Schema für E-Mail</span><span class="sxs-lookup"><span data-stu-id="d3aab-194">Email URI scheme</span></span>

<span data-ttu-id="d3aab-195">Ihre App kann das URI-Schema **mailto:** verwenden, um die Standard-E-Mail-App zu starten.</span><span class="sxs-lookup"><span data-stu-id="d3aab-195">Your app can use the **mailto:** URI scheme to launch the default mail app.</span></span>

| <span data-ttu-id="d3aab-196">URI-Schema</span><span class="sxs-lookup"><span data-stu-id="d3aab-196">URI Scheme</span></span>               | <span data-ttu-id="d3aab-197">Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="d3aab-197">Results</span></span>                                                                                                                                                     |
|--------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d3aab-198">mailto:</span><span class="sxs-lookup"><span data-stu-id="d3aab-198">mailto:</span></span>                  | <span data-ttu-id="d3aab-199">Startet die Standard-E-Mail-App.</span><span class="sxs-lookup"><span data-stu-id="d3aab-199">Launches the default email app.</span></span>                                                                                                                             |
| <span data-ttu-id="d3aab-200">mailto:\[email address\]</span><span class="sxs-lookup"><span data-stu-id="d3aab-200">mailto:\[email address\]</span></span> | <span data-ttu-id="d3aab-201">Startet die E-Mail-App und erstellt eine neue Nachricht mit der angegebenen E-Mail-Adresse in der Zeile „An“.</span><span class="sxs-lookup"><span data-stu-id="d3aab-201">Launches the email app and creates a new message with the specified email address on the To line.</span></span> <span data-ttu-id="d3aab-202">Beachten Sie, dass die E-Mail nicht gesendet wird, bis der Benutzer auf „Senden“ tippt.</span><span class="sxs-lookup"><span data-stu-id="d3aab-202">Note that the email is not sent until the user taps send.</span></span> |
<br>
### <a name="http-uri-scheme"></a><span data-ttu-id="d3aab-203">HTTP-URI-Schema</span><span class="sxs-lookup"><span data-stu-id="d3aab-203">HTTP URI scheme</span></span>

<span data-ttu-id="d3aab-204">Ihre App kann das URI-Schema **http:** verwenden, um den Standard-Webbrowser zu starten.</span><span class="sxs-lookup"><span data-stu-id="d3aab-204">Your app can use the **http:** URI scheme to launch the default web browser.</span></span>

| <span data-ttu-id="d3aab-205">URI-Schema</span><span class="sxs-lookup"><span data-stu-id="d3aab-205">URI Scheme</span></span> | <span data-ttu-id="d3aab-206">Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="d3aab-206">Results</span></span>                           |
|------------|-----------------------------------|
| <span data-ttu-id="d3aab-207">http:</span><span class="sxs-lookup"><span data-stu-id="d3aab-207">http:</span></span>      | <span data-ttu-id="d3aab-208">Startet den Standardwebbrowser.</span><span class="sxs-lookup"><span data-stu-id="d3aab-208">Launches the default web browser.</span></span> |
<br>
### <a name="maps-app-uri-schemes"></a><span data-ttu-id="d3aab-209">URI-Schemas für die Karten-App</span><span class="sxs-lookup"><span data-stu-id="d3aab-209">Maps app URI schemes</span></span>

<span data-ttu-id="d3aab-210">Ihre App kann die URI-Schemas **bingmaps:**, **ms-drive-to:** und **ms-walk-to:** zum [Starten der Windows-Karten-App](launch-maps-app.md) für bestimmte Karten, Wegbeschreibungen und Suchergebnisse verwenden.</span><span class="sxs-lookup"><span data-stu-id="d3aab-210">Your app can use the **bingmaps:**, **ms-drive-to:**, and **ms-walk-to:** URI schemes to [launch the Windows Maps app](launch-maps-app.md) to specific maps, directions, and search results.</span></span> <span data-ttu-id="d3aab-211">Der folgende URI startet beispielsweise die Windows-Karten-App und zeigt eine über New York City zentrierte Karte an.</span><span class="sxs-lookup"><span data-stu-id="d3aab-211">For example, the following URI opens the Windows Maps app and displays a map centered over New York City.</span></span>

`bingmaps:?cp=40.726966~-74.006076`

![Ein Beispiel der Windows-Karten-App.](images/mapnyc.png)

<span data-ttu-id="d3aab-213">Weitere Informationen finden Sie unter [Starten der Windows-Karten-App](launch-maps-app.md).</span><span class="sxs-lookup"><span data-stu-id="d3aab-213">For more info, see [Launch the Windows Maps app](launch-maps-app.md).</span></span> <span data-ttu-id="d3aab-214">Informationen zum Verwenden des Kartensteuerelements in Ihrer eigenen App finden Sie unter [Anzeigen von Karten mit 2D-, 3D- und Streetside-Ansichten](https://msdn.microsoft.com/library/windows/apps/mt219695).</span><span class="sxs-lookup"><span data-stu-id="d3aab-214">To use the map control in your own app, see [Display maps with 2D, 3D, and Streetside views](https://msdn.microsoft.com/library/windows/apps/mt219695).</span></span>
<br>
### <a name="messaging-app-uri-scheme"></a><span data-ttu-id="d3aab-215">URI-Schema für die Messaging-App</span><span class="sxs-lookup"><span data-stu-id="d3aab-215">Messaging app URI scheme</span></span>

<span data-ttu-id="d3aab-216">Ihre App kann das URI-Schema **ms-chat:** zum Starten der Windows Messaging-App verwenden.</span><span class="sxs-lookup"><span data-stu-id="d3aab-216">Your app can use the **ms-chat:** URI scheme to launch the Windows Messaging app.</span></span>

<span data-ttu-id="d3aab-217">| URISchema |Ergebnisse | |-- ---------|--------| | ms-chat:   | Startet die Messaging-App.</span><span class="sxs-lookup"><span data-stu-id="d3aab-217">| URI scheme |Results | |-- ---------|--------| | ms-chat:   | Launches the Messaging app.</span></span> <span data-ttu-id="d3aab-218">| | ms-chat:?ContactID={contacted}  |  Ermöglicht das Starten der Messaging-Anwendung mit den Informationen eines bestimmten Kontakts.</span><span class="sxs-lookup"><span data-stu-id="d3aab-218">| | ms-chat:?ContactID={contacted}  |  Allows the messaging application to be launched with a particular contact’s information.</span></span>   <span data-ttu-id="d3aab-219">| | ms-chat:?Body={body} | Ermöglicht das Starten der Messaging-Anwendung mit einer Zeichenfolge, die als Inhalt der Nachricht verwendet werden soll.| | ms-chat:?Addresses={address}&Body={body} | Ermöglicht das Starten der Messaging-Anwendung mit den Informationen eines bestimmten Empfängers und mit einer Zeichenfolge, die als Inhalt der Nachricht verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="d3aab-219">| | ms-chat:?Body={body} | Allows the messaging application to be launched with a string to use as the content of the message.| | ms-chat:?Addresses={address}&Body={body} | Allows the messaging application to be launched with a particular addresses' information, and with a string to use as the content of the message.</span></span> <span data-ttu-id="d3aab-220">Hinweis: Die Adressen können verkettet werden.</span><span class="sxs-lookup"><span data-stu-id="d3aab-220">Note: Addresses can be concatenated.</span></span> <span data-ttu-id="d3aab-221">| | ms-chat:?TransportId={transportId}  | Ermöglicht das Starten der Messaging-Anwendung mit einer bestimmten Transport-ID.</span><span class="sxs-lookup"><span data-stu-id="d3aab-221">| | ms-chat:?TransportId={transportId}  | Allows the messaging application to be launched with a particular transport ID.</span></span> |
<br>
### <a name="tone-picker-uri-scheme"></a><span data-ttu-id="d3aab-222">URI-Schema für die Tonauswahl</span><span class="sxs-lookup"><span data-stu-id="d3aab-222">Tone picker URI scheme</span></span>

<span data-ttu-id="d3aab-223">Ihre App kann das URI-Schema **ms-tonepicker:** verwenden, um Klingeltöne, Alarmtöne und Systemtöne zu wählen.</span><span class="sxs-lookup"><span data-stu-id="d3aab-223">Your app can use the **ms-tonepicker:** URI scheme to choose ringtones, alarms, and system tones.</span></span> <span data-ttu-id="d3aab-224">Außerdem können Sie neue Klingeltöne speichern und den Anzeigenamen eines Tons abrufen.</span><span class="sxs-lookup"><span data-stu-id="d3aab-224">You can also save new ringtones and get the display name of a tone.</span></span>

| <span data-ttu-id="d3aab-225">URI-Schema</span><span class="sxs-lookup"><span data-stu-id="d3aab-225">URI Scheme</span></span> | <span data-ttu-id="d3aab-226">Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="d3aab-226">Results</span></span> |
|------------|---------|
| <span data-ttu-id="d3aab-227">ms-tonepicker:</span><span class="sxs-lookup"><span data-stu-id="d3aab-227">ms-tonepicker:</span></span> | <span data-ttu-id="d3aab-228">Wählen Sie Klingeltöne, Alarmtöne und Systemtöne aus.</span><span class="sxs-lookup"><span data-stu-id="d3aab-228">Pick ringtones, alarms, and system tones.</span></span> |

<span data-ttu-id="d3aab-229">Die Parameter werden über einen [ValueSet](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset.aspx) an die LaunchURI-API übergeben.</span><span class="sxs-lookup"><span data-stu-id="d3aab-229">Parameters are passed via a [ValueSet](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset.aspx) to the LaunchURI API.</span></span> <span data-ttu-id="d3aab-230">Weitere Informationen finden Sie unter [Auswählen und Speichern von Tönen mit dem URI-Schema „ms-tonepicker“](launch-ringtone-picker.md).</span><span class="sxs-lookup"><span data-stu-id="d3aab-230">See [Choose and save tones using the ms-tonepicker URI scheme](launch-ringtone-picker.md) for details.</span></span>

### <a name="nearby-numbers-app-uri-scheme"></a><span data-ttu-id="d3aab-231">URI-Schema für die Nearby Numbers-App</span><span class="sxs-lookup"><span data-stu-id="d3aab-231">Nearby Numbers app URI scheme</span></span>
<br>
<span data-ttu-id="d3aab-232">Die App kann das URI-Schema **ms-yellowpage:** zum Starten der Nearby Numbers-App verwenden.</span><span class="sxs-lookup"><span data-stu-id="d3aab-232">Your app can use the **ms-yellowpage:** URI scheme to launch the Nearby Numbers app.</span></span>

| <span data-ttu-id="d3aab-233">URI-Schema</span><span class="sxs-lookup"><span data-stu-id="d3aab-233">URI Scheme</span></span> | <span data-ttu-id="d3aab-234">Ergebnisse</span><span class="sxs-lookup"><span data-stu-id="d3aab-234">Results</span></span> |
|------------|---------|
| <span data-ttu-id="d3aab-235">ms-yellowpage:?input=\[keyword\]&method=\[String oder T9\]</span><span class="sxs-lookup"><span data-stu-id="d3aab-235">ms-yellowpage:?input=\[keyword\]&method=\[String or T9\]</span></span> | <span data-ttu-id="d3aab-236">Startet die Nearby Numbers-App.</span><span class="sxs-lookup"><span data-stu-id="d3aab-236">Launches the Nearby Numbers app.</span></span> `input` <span data-ttu-id="d3aab-237">bezieht sich auf das Schlüsselwort, nach dem Sie suchen möchten.</span><span class="sxs-lookup"><span data-stu-id="d3aab-237">refers to the keyword you want to search.</span></span> `method` <span data-ttu-id="d3aab-238">bezieht sich auf den Typ der Suche (Zeichenfolge- oder T9-Suche).</span><span class="sxs-lookup"><span data-stu-id="d3aab-238">refers to the type of search (string or T9 search).</span></span> <br> <span data-ttu-id="d3aab-239">Wenn `method` `T9` ist (eine Art der Tastatur), dann sollte `keyword` eine numerische Zeichenfolge sein, die der T9-Tastatur Buchstaben zuordnet, nach denen gesucht werden soll.</span><span class="sxs-lookup"><span data-stu-id="d3aab-239">If `method` is `T9` (a type of keyboard) then `keyword` should be a numeric string that maps to the T9 keyboard letters to search for.</span></span><br><span data-ttu-id="d3aab-240">Wenn `method` `String` ist, dann ist `keyword` das Schlüsselwort, nach dem gesucht werden soll.</span><span class="sxs-lookup"><span data-stu-id="d3aab-240">If `method` is `String` then `keyword` is the keyword to search for.</span></span> |
 
<br>
### <a name="people-app-uri-scheme"></a><span data-ttu-id="d3aab-241">URI-Schema für die Kontakte-App</span><span class="sxs-lookup"><span data-stu-id="d3aab-241">People app URI scheme</span></span>

<span data-ttu-id="d3aab-242">Ihre App kann das URI-Schema **ms-people:** zum Starten der Kontakte-App verwenden.</span><span class="sxs-lookup"><span data-stu-id="d3aab-242">Your app can use the **ms-people:** URI scheme to launch the People app.</span></span>
<span data-ttu-id="d3aab-243">Weitere Informationen finden Sie unter [Starten der Kontakte-App](launch-people-apps.md).</span><span class="sxs-lookup"><span data-stu-id="d3aab-243">For more info, see [Launch the People app](launch-people-apps.md).</span></span>

<br>
### <a name="settings-app-uri-scheme"></a><span data-ttu-id="d3aab-244">URI-Schema für die Einstellungs-App</span><span class="sxs-lookup"><span data-stu-id="d3aab-244">Settings app URI scheme</span></span>

<span data-ttu-id="d3aab-245">Ihre App kann das URI-Schema **ms-settings:** zum [Starten der Windows-Einstellungs-App](launch-settings-app.md) verwenden.</span><span class="sxs-lookup"><span data-stu-id="d3aab-245">Your app can use the **ms-settings:** URI scheme to [launch the Windows Settings app](launch-settings-app.md).</span></span> <span data-ttu-id="d3aab-246">Das Starten der Einstellungs-App ist ein wichtiger Bestandteil beim Schreiben einer App mit Berücksichtigung von Datenschutz.</span><span class="sxs-lookup"><span data-stu-id="d3aab-246">Launching to the Settings app is an important part of writing a privacy-aware app.</span></span> <span data-ttu-id="d3aab-247">Wenn Ihre App nicht auf eine sensible Ressource zugreifen kann, wird empfohlen, dem Benutzer einen praktischen Link zu den Datenschutzeinstellungen für diese Ressource bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="d3aab-247">If your app can't access a sensitive resource, we recommend providing the user a convenient link to the privacy settings for that resource.</span></span> <span data-ttu-id="d3aab-248">Folgender URI öffnet beispielsweise die Einstellungs-App und zeigt die Datenschutzeinstellungen für die Kamera an.</span><span class="sxs-lookup"><span data-stu-id="d3aab-248">For example, the following URI opens the Settings app and displays the camera privacy settings.</span></span>

`ms-settings:privacy-webcam`

![Datenschutzeinstellungen für die Kamera.](images/privacyawarenesssettingsapp.png)

<span data-ttu-id="d3aab-250">Weitere Informationen finden Sie unter [Starten der Einstellungs-App von Windows](launch-settings-app.md) und [Richtlinien für Apps mit Berücksichtigung von Datenschutz](https://msdn.microsoft.com/library/windows/apps/hh768223).</span><span class="sxs-lookup"><span data-stu-id="d3aab-250">For more info, see [Launch the Windows Settings app](launch-settings-app.md) and [Guidelines for privacy-aware apps](https://msdn.microsoft.com/library/windows/apps/hh768223).</span></span>

<br>
### <a name="store-app-uri-scheme"></a><span data-ttu-id="d3aab-251">URI-Schema für die Store-App</span><span class="sxs-lookup"><span data-stu-id="d3aab-251">Store app URI scheme</span></span>

<span data-ttu-id="d3aab-252">Ihre App kann das URI-Schema **ms-windows-store:** zum [Starten der Windows Store-App](launch-store-app.md) verwenden.</span><span class="sxs-lookup"><span data-stu-id="d3aab-252">Your app can use the **ms-windows-store:** URI scheme to [Launch the Windows Store app](launch-store-app.md).</span></span> <span data-ttu-id="d3aab-253">Öffnen Sie Seiten mit Produktdetails, Produktbewertungen sowie Suchseiten. Der folgende URI öffnet z.B. die Windows Store-App und startet die Store-Startseite.</span><span class="sxs-lookup"><span data-stu-id="d3aab-253">Open product detail pages, product review pages, and search pages, etc. For example, the following URI opens the Windows Store app and launches the home page of the Store.</span></span>

`ms-windows-store://home/`

<span data-ttu-id="d3aab-254">Weitere Informationen finden Sie unter [Starten der Windows Store-App](launch-store-app.md).</span><span class="sxs-lookup"><span data-stu-id="d3aab-254">For more info, see [Launch the Windows Store app](launch-store-app.md).</span></span>
