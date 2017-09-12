---
author: TylerMSFT
title: Starten der Einstellungs-App von Windows
description: "Erfahren Sie, wie Sie die Windows-Einstellungs-App aus Ihrer App starten können. In diesem Thema wird das ms-settings-URI-Schema beschrieben. Verwenden Sie dieses URI-Schema, um die Windows-Einstellungs-App mit bestimmten Einstellungsseiten zu starten."
ms.assetid: C84D4BEE-1FEE-4648-AD7D-8321EAC70290
ms.author: twhitney
ms.date: 06/12/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.openlocfilehash: 2a30e14f7c275c48f52253157fc9c67bf05d259e
ms.sourcegitcommit: 00c3f5a1208bd0125f5b275f972cf2a82d8eb9b6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/13/2017
---
# <a name="launch-the-windows-settings-app"></a><span data-ttu-id="2b982-106">Starten der Windows-Einstellungs-App</span><span class="sxs-lookup"><span data-stu-id="2b982-106">Launch the Windows Settings app</span></span>

<span data-ttu-id="2b982-107">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="2b982-107">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="2b982-108">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="2b982-108">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

**<span data-ttu-id="2b982-109">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="2b982-109">Important APIs</span></span>**

-   [**<span data-ttu-id="2b982-110">LaunchUriAsync</span><span class="sxs-lookup"><span data-stu-id="2b982-110">LaunchUriAsync</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh701476)
-   [**<span data-ttu-id="2b982-111">PreferredApplicationPackageFamilyName</span><span class="sxs-lookup"><span data-stu-id="2b982-111">PreferredApplicationPackageFamilyName</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh965482)
-   [**<span data-ttu-id="2b982-112">DesiredRemainingView</span><span class="sxs-lookup"><span data-stu-id="2b982-112">DesiredRemainingView</span></span>**](https://msdn.microsoft.com/library/windows/apps/dn298314)

<span data-ttu-id="2b982-113">Erfahren Sie, wie Sie die Windows-Einstellungs-App aus Ihrer App starten können.</span><span class="sxs-lookup"><span data-stu-id="2b982-113">Learn how to launch the Windows Settings app from your app.</span></span> <span data-ttu-id="2b982-114">In diesem Thema wird das **ms-settings:**-URI-Schema beschrieben.</span><span class="sxs-lookup"><span data-stu-id="2b982-114">This topic describes the **ms-settings:** URI scheme.</span></span> <span data-ttu-id="2b982-115">Verwenden Sie dieses URI-Schema, um die Windows-Einstellungs-App mit bestimmten Einstellungsseiten zu starten.</span><span class="sxs-lookup"><span data-stu-id="2b982-115">Use this URI scheme to launch the Windows Settings app to specific settings pages.</span></span>

<span data-ttu-id="2b982-116">Das Starten der Einstellungs-App ist ein wichtiger Bestandteil beim Schreiben einer datenschutzbewussten App.</span><span class="sxs-lookup"><span data-stu-id="2b982-116">Launching to the Settings app is an important part of writing a privacy-aware app.</span></span> <span data-ttu-id="2b982-117">Wenn Ihre App nicht auf eine sensible Ressource zugreifen kann, wird empfohlen, dem Benutzer einen praktischen Link zu den Datenschutzeinstellungen für diese Ressource bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="2b982-117">If your app can't access a sensitive resource, we recommend providing the user a convenient link to the privacy settings for that resource.</span></span> <span data-ttu-id="2b982-118">Weitere Informationen finden Sie unter [Richtlinien für Apps mit Berücksichtigung von Datenschutz](https://msdn.microsoft.com/library/windows/apps/hh768223).</span><span class="sxs-lookup"><span data-stu-id="2b982-118">For more info, see [Guidelines for privacy-aware apps](https://msdn.microsoft.com/library/windows/apps/hh768223).</span></span>

## <a name="how-to-launch-the-settings-app"></a><span data-ttu-id="2b982-119">So starten Sie die Einstellungs-App</span><span class="sxs-lookup"><span data-stu-id="2b982-119">How to launch the Settings app</span></span>

<span data-ttu-id="2b982-120">Um die **Einstellungs**-App zu starten, verwenden Sie das in den folgenden Beispielen beschriebene URI-Schema `ms-settings:`.</span><span class="sxs-lookup"><span data-stu-id="2b982-120">To launch the **Settings** app, use the `ms-settings:` URI scheme as shown in the following examples.</span></span>

<span data-ttu-id="2b982-121">In diesem Beispiel wird ein Hyperlink-XAML-Steuerelement verwendet, um die Datenschutzeinstellungsseite für das Mikrofon mit der `ms-settings:privacy-microphone`-URI zu starten.</span><span class="sxs-lookup"><span data-stu-id="2b982-121">In this example, a Hyperlink XAML control is used to launch the privacy settings page for the microphone using the `ms-settings:privacy-microphone` URI.</span></span>

```xml
<!--Set Visibility to Visible when access to the microphone is denied -->  
<TextBlock x:Name="LocationDisabledMessage" FontStyle="Italic"
                 Visibility="Collapsed" Margin="0,15,0,0" TextWrapping="Wrap" >
          <Run Text="This app is not able to access the microphone. Go to " />
              <Hyperlink NavigateUri="ms-settings:privacy-microphone">
                  <Run Text="Settings" />
              </Hyperlink>
          <Run Text=" to check the microphone privacy settings."/>
</TextBlock>
```

<span data-ttu-id="2b982-122">Alternativ kann Ihre App die [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476)-Methode aufrufen, um die **Einstellungs**-App per Code zu starten.</span><span class="sxs-lookup"><span data-stu-id="2b982-122">Alternatively, your app can call the [**LaunchUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701476) method to launch the **Settings** app from code.</span></span> <span data-ttu-id="2b982-123">In diesem Beispiel wird gezeigt, wie die Datenschutzeinstellungsseite für die Kamera mit dem `ms-settings:privacy-webcam`-URI gestartet werden kann.</span><span class="sxs-lookup"><span data-stu-id="2b982-123">This example shows how to launch to the privacy settings page for the camera using the `ms-settings:privacy-webcam` URI.</span></span>

```cs
bool result = await Windows.System.Launcher.LaunchUriAsync(new Uri("ms-settings:privacy-webcam"));
```

<span data-ttu-id="2b982-124">Der eben gezeigte Code startet die Datenschutzeinstellungsseite für die Kamera:</span><span class="sxs-lookup"><span data-stu-id="2b982-124">The code above launches the privacy settings page for the camera:</span></span>

![Datenschutzeinstellungen für die Kamera.](images/privacyawarenesssettingsapp.png)

<span data-ttu-id="2b982-126">Weitere Informationen zum Starten von URIs finden Sie unter [Starten der Standard-App für einen URI](launch-default-app.md).</span><span class="sxs-lookup"><span data-stu-id="2b982-126">For more info about launching URIs, see [Launch the default app for a URI](launch-default-app.md).</span></span>

## <a name="ms-settings-uri-scheme-reference"></a><span data-ttu-id="2b982-127">ms-settings: URI-Schemareferenz</span><span class="sxs-lookup"><span data-stu-id="2b982-127">ms-settings: URI scheme reference</span></span>

<span data-ttu-id="2b982-128">Verwenden Sie die folgenden URIs, um verschiedenen Seiten der Einstellungs-App zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="2b982-128">Use the following URIs to open various pages of the Settings app.</span></span>

> <span data-ttu-id="2b982-129">Hinweis: ob die Seite "Einstellungen" verfügbar ist, variiert je nach Windows-SKU.</span><span class="sxs-lookup"><span data-stu-id="2b982-129">Note that whether a settings page is available varies by Windows SKU.</span></span> <span data-ttu-id="2b982-130">Nicht alle Einstellungsseiten von Windows10 für Desktop sind für Windows10 Mobile verfügbar und umgekehrt.</span><span class="sxs-lookup"><span data-stu-id="2b982-130">Not all settings page available on Windows 10 for desktop are available on Windows 10 Mobile, and vice-versa.</span></span> <span data-ttu-id="2b982-131">Der Bereich „Anmerkungen” in dieser Spalte erfasst auch zusätzliche Anforderungen, die erfüllt sein müssen, damit eine Seite zur Verfügung steht.</span><span class="sxs-lookup"><span data-stu-id="2b982-131">The notes column also captures additional requirements that must be met for a page to be available.</span></span>

<table border="1">
 <tr>
  <th><span data-ttu-id="2b982-132">Kategorie</span><span class="sxs-lookup"><span data-stu-id="2b982-132">Category</span></span></th>
  <th><span data-ttu-id="2b982-133">Einstellungsseite</span><span class="sxs-lookup"><span data-stu-id="2b982-133">Settings page</span></span></th>
  <th><span data-ttu-id="2b982-134">URI</span><span class="sxs-lookup"><span data-stu-id="2b982-134">URI</span></span></th>
  <th><span data-ttu-id="2b982-135">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="2b982-135">Notes</span></span></th>
 </tr>
 <tr>
  <td rowspan="6"><span data-ttu-id="2b982-136">Konten</span><span class="sxs-lookup"><span data-stu-id="2b982-136">Accounts</span></span></td>
  <td><span data-ttu-id="2b982-137">Geschäfts- oder Schulkonto öffnen</span><span class="sxs-lookup"><span data-stu-id="2b982-137">Access work or school</span></span></td>
  <td><span data-ttu-id="2b982-138">ms-settings:workplace</span><span class="sxs-lookup"><span data-stu-id="2b982-138">ms-settings:workplace</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-139">E-Mail- & App-Konten</span><span class="sxs-lookup"><span data-stu-id="2b982-139">Email & app accounts</span></span></td>
  <td><span data-ttu-id="2b982-140">ms-settings:emailandaccounts</span><span class="sxs-lookup"><span data-stu-id="2b982-140">ms-settings:emailandaccounts</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-141">Familie und andere Personen</span><span class="sxs-lookup"><span data-stu-id="2b982-141">Family & other people</span></span></td>
  <td><span data-ttu-id="2b982-142">ms-settings:otherusers</span><span class="sxs-lookup"><span data-stu-id="2b982-142">ms-settings:otherusers</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-143">Anmeldeoptionen</span><span class="sxs-lookup"><span data-stu-id="2b982-143">Sign-in options</span></span></td>
  <td><span data-ttu-id="2b982-144">ms-settings:signinoptions</span><span class="sxs-lookup"><span data-stu-id="2b982-144">ms-settings:signinoptions</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-145">Synchronisieren von Einstellungen</span><span class="sxs-lookup"><span data-stu-id="2b982-145">Sync your settings</span></span></td>
  <td><span data-ttu-id="2b982-146">ms-settings:sync</span><span class="sxs-lookup"><span data-stu-id="2b982-146">ms-settings:sync</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-147">Ihre Informationen</span><span class="sxs-lookup"><span data-stu-id="2b982-147">Your info</span></span></td>
  <td><span data-ttu-id="2b982-148">ms-settings:yourinfo</span><span class="sxs-lookup"><span data-stu-id="2b982-148">ms-settings:yourinfo</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td rowspan="4"><span data-ttu-id="2b982-149">Apps</span><span class="sxs-lookup"><span data-stu-id="2b982-149">Apps</span></span></td>
  <td><span data-ttu-id="2b982-150">Apps & Features</span><span class="sxs-lookup"><span data-stu-id="2b982-150">Apps & Features</span></span></td>
  <td><span data-ttu-id="2b982-151">ms-settings:appsfeatures</span><span class="sxs-lookup"><span data-stu-id="2b982-151">ms-settings:appsfeatures</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-152">Apps für Websites</span><span class="sxs-lookup"><span data-stu-id="2b982-152">Apps for websites</span></span></td>
  <td><span data-ttu-id="2b982-153">ms-settings:appsforwebsites</span><span class="sxs-lookup"><span data-stu-id="2b982-153">ms-settings:appsforwebsites</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-154">Standard-Apps</span><span class="sxs-lookup"><span data-stu-id="2b982-154">Default apps</span></span></td>
  <td><span data-ttu-id="2b982-155">ms-settings:defaultapps</span><span class="sxs-lookup"><span data-stu-id="2b982-155">ms-settings:defaultapps</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-156">Apps & Features</span><span class="sxs-lookup"><span data-stu-id="2b982-156">Apps & features</span></span></td>
  <td><span data-ttu-id="2b982-157">ms-settings:optionalfeatures</span><span class="sxs-lookup"><span data-stu-id="2b982-157">ms-settings:optionalfeatures</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td rowspan="12"><span data-ttu-id="2b982-158">Geräte</span><span class="sxs-lookup"><span data-stu-id="2b982-158">Devices</span></span></td>
  <td><span data-ttu-id="2b982-159">USB</span><span class="sxs-lookup"><span data-stu-id="2b982-159">USB</span></span></td>
  <td><span data-ttu-id="2b982-160">ms-settings:usb</span><span class="sxs-lookup"><span data-stu-id="2b982-160">ms-settings:usb</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-161">Audio und Sprache</span><span class="sxs-lookup"><span data-stu-id="2b982-161">Audio and speech</span></span></td>
  <td><span data-ttu-id="2b982-162">ms-settings:holographic-audio</span><span class="sxs-lookup"><span data-stu-id="2b982-162">ms-settings:holographic-audio</span></span></td>
  <td><span data-ttu-id="2b982-163">Ist nur verfügbar, wenn das App Mixed Reality-Portal installiert ist (verfügbar im Windows Store)</span><span class="sxs-lookup"><span data-stu-id="2b982-163">Only available if the Mixed Reality Portal app is installed (available in the Windows Store)</span></span></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-164">Automatische Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="2b982-164">AutoPlay</span></span></td>
  <td><span data-ttu-id="2b982-165">ms-settings:autoplay</span><span class="sxs-lookup"><span data-stu-id="2b982-165">ms-settings:autoplay</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-166">Touchpad</span><span class="sxs-lookup"><span data-stu-id="2b982-166">Touchpad</span></span></td>
  <td><span data-ttu-id="2b982-167">ms-settings:devices-touchpad</span><span class="sxs-lookup"><span data-stu-id="2b982-167">ms-settings:devices-touchpad</span></span></td>
  <td><span data-ttu-id="2b982-168">Ist nur verfügbar, wenn Touchpad-Hardware vorhanden ist</span><span class="sxs-lookup"><span data-stu-id="2b982-168">Only available if touchpad hardware is present</span></span></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-169">Stift & Windows Ink</span><span class="sxs-lookup"><span data-stu-id="2b982-169">Pen & Windows Ink</span></span></td>
  <td><span data-ttu-id="2b982-170">ms-settings:pen</span><span class="sxs-lookup"><span data-stu-id="2b982-170">ms-settings:pen</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-171">Drucker und Scanner</span><span class="sxs-lookup"><span data-stu-id="2b982-171">Printers & scanners</span></span></td>
  <td><span data-ttu-id="2b982-172">ms-settings:printers</span><span class="sxs-lookup"><span data-stu-id="2b982-172">ms-settings:printers</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-173">Tippen</span><span class="sxs-lookup"><span data-stu-id="2b982-173">Typing</span></span></td>
  <td><span data-ttu-id="2b982-174">ms-settings:typing</span><span class="sxs-lookup"><span data-stu-id="2b982-174">ms-settings:typing</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-175">Wheel</span><span class="sxs-lookup"><span data-stu-id="2b982-175">Wheel</span></span></td>
  <td><span data-ttu-id="2b982-176">ms-settings:wheel</span><span class="sxs-lookup"><span data-stu-id="2b982-176">ms-settings:wheel</span></span></td>
  <td><span data-ttu-id="2b982-177">Ist nur verfügbar, wenn die Einwahl gekoppelt ist</span><span class="sxs-lookup"><span data-stu-id="2b982-177">Only available if Dial is paired</span></span></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-178">Standardkamera</span><span class="sxs-lookup"><span data-stu-id="2b982-178">Default camera</span></span></td>
  <td><span data-ttu-id="2b982-179">ms-settings:camera</span><span class="sxs-lookup"><span data-stu-id="2b982-179">ms-settings:camera</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-180">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="2b982-180">Bluetooth</span></span></td>
  <td><span data-ttu-id="2b982-181">ms-settings:bluetooth</span><span class="sxs-lookup"><span data-stu-id="2b982-181">ms-settings:bluetooth</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-182">Verbundene Geräte</span><span class="sxs-lookup"><span data-stu-id="2b982-182">Connected Devices</span></span></td>
  <td><span data-ttu-id="2b982-183">ms-settings:connecteddevices</span><span class="sxs-lookup"><span data-stu-id="2b982-183">ms-settings:connecteddevices</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-184">Maus und Touchpad</span><span class="sxs-lookup"><span data-stu-id="2b982-184">Mouse & touchpad</span></span></td>
  <td><span data-ttu-id="2b982-185">ms-settings:mousetouchpad</span><span class="sxs-lookup"><span data-stu-id="2b982-185">ms-settings:mousetouchpad</span></span></td>
  <td><span data-ttu-id="2b982-186">Touchpadeinstellungen nur auf Geräten mit Touchpad verfügbar</span><span class="sxs-lookup"><span data-stu-id="2b982-186">Touchpad settings only available on devices that have a touchpad</span></span></td>
 </tr>
 <tr>
  <td rowspan="7"><span data-ttu-id="2b982-187">Erleichterte Bedienung</span><span class="sxs-lookup"><span data-stu-id="2b982-187">Ease of Access</span></span></td>
  <td><span data-ttu-id="2b982-188">Sprachausgabe</span><span class="sxs-lookup"><span data-stu-id="2b982-188">Narrator</span></span></td>
  <td><span data-ttu-id="2b982-189">ms-settings:easeofaccess-narrator</span><span class="sxs-lookup"><span data-stu-id="2b982-189">ms-settings:easeofaccess-narrator</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-190">Bildschirmlupe</span><span class="sxs-lookup"><span data-stu-id="2b982-190">Magnifier</span></span></td>
  <td><span data-ttu-id="2b982-191">ms-settings:easeofaccess-magnifier</span><span class="sxs-lookup"><span data-stu-id="2b982-191">ms-settings:easeofaccess-magnifier</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-192">Hoher Kontrast</span><span class="sxs-lookup"><span data-stu-id="2b982-192">High contrast</span></span></td>
  <td><span data-ttu-id="2b982-193">ms-settings:easeofaccess-highcontrast</span><span class="sxs-lookup"><span data-stu-id="2b982-193">ms-settings:easeofaccess-highcontrast</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-194">Untertitel</span><span class="sxs-lookup"><span data-stu-id="2b982-194">Closed captions</span></span></td>
  <td><span data-ttu-id="2b982-195">ms-settings:easeofaccess-closedcaptioning</span><span class="sxs-lookup"><span data-stu-id="2b982-195">ms-settings:easeofaccess-closedcaptioning</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-196">Tastatur</span><span class="sxs-lookup"><span data-stu-id="2b982-196">Keyboard</span></span></td>
  <td><span data-ttu-id="2b982-197">ms-settings:easeofaccess-keyboard</span><span class="sxs-lookup"><span data-stu-id="2b982-197">ms-settings:easeofaccess-keyboard</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-198">Maus</span><span class="sxs-lookup"><span data-stu-id="2b982-198">Mouse</span></span></td>
  <td><span data-ttu-id="2b982-199">ms-settings:easeofaccess-mouse</span><span class="sxs-lookup"><span data-stu-id="2b982-199">ms-settings:easeofaccess-mouse</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-200">Andere Optionen</span><span class="sxs-lookup"><span data-stu-id="2b982-200">Other options</span></span></td>
  <td><span data-ttu-id="2b982-201">ms-settings:easeofaccess-otheroptions</span><span class="sxs-lookup"><span data-stu-id="2b982-201">ms-settings:easeofaccess-otheroptions</span></span></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-202">Extras</span><span class="sxs-lookup"><span data-stu-id="2b982-202">Extras</span></span></td>
  <td><span data-ttu-id="2b982-203">Extras</span><span class="sxs-lookup"><span data-stu-id="2b982-203">Extras</span></span></td>
  <td><span data-ttu-id="2b982-204">ms-settings:extras</span><span class="sxs-lookup"><span data-stu-id="2b982-204">ms-settings:extras</span></span></td>
  <td><span data-ttu-id="2b982-205">Ist nur verfügbar, wenn "Apps-Einstellungen" installiert sind (z.B. von Drittanbietern)</span><span class="sxs-lookup"><span data-stu-id="2b982-205">Only available if "settings apps" are installed (e.g. by 3rd party)</span></span></td>
 </tr>
 <tr>
  <td rowspan="4"><span data-ttu-id="2b982-206">Spiele</span><span class="sxs-lookup"><span data-stu-id="2b982-206">Gaming</span></span></td>
  <td><span data-ttu-id="2b982-207">Senden</span><span class="sxs-lookup"><span data-stu-id="2b982-207">Broadcasting</span></span></td>
  <td><span data-ttu-id="2b982-208">ms-settings:gaming-broadcasting</span><span class="sxs-lookup"><span data-stu-id="2b982-208">ms-settings:gaming-broadcasting</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-209">Spieleleiste</span><span class="sxs-lookup"><span data-stu-id="2b982-209">Game bar</span></span></td>
  <td><span data-ttu-id="2b982-210">ms-settings:gaming-gamebar</span><span class="sxs-lookup"><span data-stu-id="2b982-210">ms-settings:gaming-gamebar</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-211">Game DVR</span><span class="sxs-lookup"><span data-stu-id="2b982-211">Game DVR</span></span></td>
  <td><span data-ttu-id="2b982-212">ms-settings:gaming-gamedvr</span><span class="sxs-lookup"><span data-stu-id="2b982-212">ms-settings:gaming-gamedvr</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-213">Spielmodus</span><span class="sxs-lookup"><span data-stu-id="2b982-213">Game Mode</span></span></td>
  <td><span data-ttu-id="2b982-214">ms-settings:gaming-gamemode</span><span class="sxs-lookup"><span data-stu-id="2b982-214">ms-settings:gaming-gamemode</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-215">Startseite</span><span class="sxs-lookup"><span data-stu-id="2b982-215">Home page</span></span></td>
  <td><span data-ttu-id="2b982-216">Angebotsseite für Einstellungen</span><span class="sxs-lookup"><span data-stu-id="2b982-216">Landing page for Settings</span></span></td>
  <td><span data-ttu-id="2b982-217">ms-settings:</span><span class="sxs-lookup"><span data-stu-id="2b982-217">ms-settings:</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td rowspan="10"><span data-ttu-id="2b982-218">Netzwerk und Internet</span><span class="sxs-lookup"><span data-stu-id="2b982-218">Network & internet</span></span></td>
  <td><span data-ttu-id="2b982-219">Ethernet</span><span class="sxs-lookup"><span data-stu-id="2b982-219">Ethernet</span></span></td>
  <td><span data-ttu-id="2b982-220">ms-settings:network-ethernet</span><span class="sxs-lookup"><span data-stu-id="2b982-220">ms-settings:network-ethernet</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-221">VPN</span><span class="sxs-lookup"><span data-stu-id="2b982-221">VPN</span></span></td>
  <td><span data-ttu-id="2b982-222">ms-settings:network-vpn</span><span class="sxs-lookup"><span data-stu-id="2b982-222">ms-settings:network-vpn</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-223">DFÜ-Verbindung</span><span class="sxs-lookup"><span data-stu-id="2b982-223">Dial-up</span></span></td>
  <td><span data-ttu-id="2b982-224">ms-settings:network-dialup</span><span class="sxs-lookup"><span data-stu-id="2b982-224">ms-settings:network-dialup</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-225">DirectAccess</span><span class="sxs-lookup"><span data-stu-id="2b982-225">DirectAccess</span></span></td>
  <td><span data-ttu-id="2b982-226">ms-settings:network-directaccess</span><span class="sxs-lookup"><span data-stu-id="2b982-226">ms-settings:network-directaccess</span></span></td>
  <td><span data-ttu-id="2b982-227">Ist nur verfügbar, wenn DirectAccess aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="2b982-227">Only available if DirectAccess is enabled</span></span></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-228">WLAN-Anruf</span><span class="sxs-lookup"><span data-stu-id="2b982-228">Wi-Fi Calling</span></span></td>
  <td><span data-ttu-id="2b982-229">ms-settings:network-wificalling</span><span class="sxs-lookup"><span data-stu-id="2b982-229">ms-settings:network-wificalling</span></span></td>
  <td><span data-ttu-id="2b982-230">Ist nur verfügbar, wenn WLAN aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="2b982-230">Only available if Wi-Fi calling is enabled</span></span></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-231">Datennutzung</span><span class="sxs-lookup"><span data-stu-id="2b982-231">Data usage</span></span></td>
  <td><span data-ttu-id="2b982-232">ms-settings:datausage</span><span class="sxs-lookup"><span data-stu-id="2b982-232">ms-settings:datausage</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-233">Mobilfunk und SIM</span><span class="sxs-lookup"><span data-stu-id="2b982-233">Cellular & SIM</span></span></td>
  <td><span data-ttu-id="2b982-234">ms-settings:network-cellular</span><span class="sxs-lookup"><span data-stu-id="2b982-234">ms-settings:network-cellular</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-235">Mobiler Hotspot</span><span class="sxs-lookup"><span data-stu-id="2b982-235">Mobile hotspot</span></span></td>
  <td><span data-ttu-id="2b982-236">ms-settings:network-mobilehotspot</span><span class="sxs-lookup"><span data-stu-id="2b982-236">ms-settings:network-mobilehotspot</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-237">Proxy</span><span class="sxs-lookup"><span data-stu-id="2b982-237">Proxy</span></span></td>
  <td><span data-ttu-id="2b982-238">ms-settings:network-proxy</span><span class="sxs-lookup"><span data-stu-id="2b982-238">ms-settings:network-proxy</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-239">Status</span><span class="sxs-lookup"><span data-stu-id="2b982-239">Status</span></span></td>
  <td><span data-ttu-id="2b982-240">ms-settings:network-status</span><span class="sxs-lookup"><span data-stu-id="2b982-240">ms-settings:network-status</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-241">Bekannte Netzwerke verwalten</span><span class="sxs-lookup"><span data-stu-id="2b982-241">Manage known networks</span></span></td>
  <td><span data-ttu-id="2b982-242">ms-settings:network-wifisettings</span><span class="sxs-lookup"><span data-stu-id="2b982-242">ms-settings:network-wifisettings</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td rowspan="3"><span data-ttu-id="2b982-243">Netzwerk und WLAN</span><span class="sxs-lookup"><span data-stu-id="2b982-243">Network & wireless</span></span></td>
  <td><span data-ttu-id="2b982-244">NFC</span><span class="sxs-lookup"><span data-stu-id="2b982-244">NFC</span></span></td>
  <td><span data-ttu-id="2b982-245">ms-settings:nfctransactions</span><span class="sxs-lookup"><span data-stu-id="2b982-245">ms-settings:nfctransactions</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-246">WLAN</span><span class="sxs-lookup"><span data-stu-id="2b982-246">Wi-Fi</span></span></td>
  <td><span data-ttu-id="2b982-247">ms-settings:network-wifi</span><span class="sxs-lookup"><span data-stu-id="2b982-247">ms-settings:network-wifi</span></span></td>
  <td><span data-ttu-id="2b982-248">Ist nur verfügbar, wenn das Gerät über einen WLAN-Adapter verfügt</span><span class="sxs-lookup"><span data-stu-id="2b982-248">Only available if the device has a wifi adaptor</span></span></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-249">Flugzeugmodus</span><span class="sxs-lookup"><span data-stu-id="2b982-249">Airplane mode</span></span></td>
  <td><span data-ttu-id="2b982-250">ms-settings:network-airplanemode</span><span class="sxs-lookup"><span data-stu-id="2b982-250">ms-settings:network-airplanemode</span></span></td>
  <td><span data-ttu-id="2b982-251">Verwenden Sie ms-settings:proximity auf Windows 8.x</span><span class="sxs-lookup"><span data-stu-id="2b982-251">Use ms-settings:proximity on Windows 8.x</span></span></td>
 </tr>
 <tr>
  <td rowspan="10"><span data-ttu-id="2b982-252">Personalisierung</span><span class="sxs-lookup"><span data-stu-id="2b982-252">Personalization</span></span></td>
  <td><span data-ttu-id="2b982-253">Start</span><span class="sxs-lookup"><span data-stu-id="2b982-253">Start</span></span></td>
  <td><span data-ttu-id="2b982-254">ms-settings:personalization-start</span><span class="sxs-lookup"><span data-stu-id="2b982-254">ms-settings:personalization-start</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-255">Designs</span><span class="sxs-lookup"><span data-stu-id="2b982-255">Themes</span></span></td>
  <td><span data-ttu-id="2b982-256">ms-settings:themes</span><span class="sxs-lookup"><span data-stu-id="2b982-256">ms-settings:themes</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-257">Blick</span><span class="sxs-lookup"><span data-stu-id="2b982-257">Glance</span></span></td>
  <td><span data-ttu-id="2b982-258">ms-settings:personalization-glance</span><span class="sxs-lookup"><span data-stu-id="2b982-258">ms-settings:personalization-glance</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-259">Navigationsleiste</span><span class="sxs-lookup"><span data-stu-id="2b982-259">Navigation bar</span></span></td>
  <td><span data-ttu-id="2b982-260">ms-settings:personalization-navbar</span><span class="sxs-lookup"><span data-stu-id="2b982-260">ms-settings:personalization-navbar</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-261">Personalisierung (Kategorie)</span><span class="sxs-lookup"><span data-stu-id="2b982-261">Personalization (category)</span></span></td>
   <td><span data-ttu-id="2b982-262">ms-settings:personalization</span><span class="sxs-lookup"><span data-stu-id="2b982-262">ms-settings:personalization</span></span></td>
   <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-263">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="2b982-263">Background</span></span></td>
   <td><span data-ttu-id="2b982-264">ms-settings:personalization-background</span><span class="sxs-lookup"><span data-stu-id="2b982-264">ms-settings:personalization-background</span></span></td>
   <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-265">Farben</span><span class="sxs-lookup"><span data-stu-id="2b982-265">Colors</span></span></td>
   <td><span data-ttu-id="2b982-266">ms-settings:personalization-colors</span><span class="sxs-lookup"><span data-stu-id="2b982-266">ms-settings:personalization-colors</span></span></td>
   <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-267">Sounds</span><span class="sxs-lookup"><span data-stu-id="2b982-267">Sounds</span></span></td>
   <td><span data-ttu-id="2b982-268">ms-settings:sounds</span><span class="sxs-lookup"><span data-stu-id="2b982-268">ms-settings:sounds</span></span></td>
   <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-269">Sperrbildschirm</span><span class="sxs-lookup"><span data-stu-id="2b982-269">Lock screen</span></span></td>
   <td><span data-ttu-id="2b982-270">ms-settings:lockscreen</span><span class="sxs-lookup"><span data-stu-id="2b982-270">ms-settings:lockscreen</span></span></td>
   <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-271">Task-Leiste</span><span class="sxs-lookup"><span data-stu-id="2b982-271">Task Bar</span></span></td>
   <td><span data-ttu-id="2b982-272">ms-settings:taskbar</span><span class="sxs-lookup"><span data-stu-id="2b982-272">ms-settings:taskbar</span></span></td>
   <td></td>
 </tr>
 <tr>
  <td rowspan="22"><span data-ttu-id="2b982-273">Vertraulichkeit</span><span class="sxs-lookup"><span data-stu-id="2b982-273">Privacy</span></span></td>
  <td><span data-ttu-id="2b982-274">App-Diagnose</span><span class="sxs-lookup"><span data-stu-id="2b982-274">App diagnostics</span></span></td>
   <td><span data-ttu-id="2b982-275">ms-settings:privacy-appdiagnostics</span><span class="sxs-lookup"><span data-stu-id="2b982-275">ms-settings:privacy-appdiagnostics</span></span></td>
   <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-276">Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="2b982-276">Notifications</span></span></td>
   <td><span data-ttu-id="2b982-277">ms-settings:privacy-notifications</span><span class="sxs-lookup"><span data-stu-id="2b982-277">ms-settings:privacy-notifications</span></span></td>
   <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-278">Aufgaben</span><span class="sxs-lookup"><span data-stu-id="2b982-278">Tasks</span></span></td>
   <td><span data-ttu-id="2b982-279">ms-settings:privacy-tasks</span><span class="sxs-lookup"><span data-stu-id="2b982-279">ms-settings:privacy-tasks</span></span></td>
   <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-280">Allgemein</span><span class="sxs-lookup"><span data-stu-id="2b982-280">General</span></span></td>
   <td><span data-ttu-id="2b982-281">ms-settings:privacy-general</span><span class="sxs-lookup"><span data-stu-id="2b982-281">ms-settings:privacy-general</span></span></td>
   <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-282">Zubehör-Apps</span><span class="sxs-lookup"><span data-stu-id="2b982-282">Accessory apps</span></span></td>
   <td><span data-ttu-id="2b982-283">ms-settings:privacy-accessoryapps</span><span class="sxs-lookup"><span data-stu-id="2b982-283">ms-settings:privacy-accessoryapps</span></span></td>
   <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-284">Werbe-ID</span><span class="sxs-lookup"><span data-stu-id="2b982-284">Advertising ID</span></span></td>
   <td><span data-ttu-id="2b982-285">ms-settings:privacy-advertisingid</span><span class="sxs-lookup"><span data-stu-id="2b982-285">ms-settings:privacy-advertisingid</span></span></td>
   <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-286">Telefonanrufe</span><span class="sxs-lookup"><span data-stu-id="2b982-286">Phone calls</span></span></td>
   <td><span data-ttu-id="2b982-287">ms-settings:privacy-phonecall</span><span class="sxs-lookup"><span data-stu-id="2b982-287">ms-settings:privacy-phonecall</span></span></td>
   <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-288">Pfad</span><span class="sxs-lookup"><span data-stu-id="2b982-288">Location</span></span></td>
   <td><span data-ttu-id="2b982-289">ms-settings:privacy-location</span><span class="sxs-lookup"><span data-stu-id="2b982-289">ms-settings:privacy-location</span></span></td>
   <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-290">Kamera</span><span class="sxs-lookup"><span data-stu-id="2b982-290">Camera</span></span></td>
   <td><span data-ttu-id="2b982-291">ms-settings:privacy-webcam</span><span class="sxs-lookup"><span data-stu-id="2b982-291">ms-settings:privacy-webcam</span></span></td>
   <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-292">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="2b982-292">Microphone</span></span></td>
   <td><span data-ttu-id="2b982-293">ms-settings:privacy-microphone</span><span class="sxs-lookup"><span data-stu-id="2b982-293">ms-settings:privacy-microphone</span></span></td>
   <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-294">Bewegung</span><span class="sxs-lookup"><span data-stu-id="2b982-294">Motion</span></span></td>
   <td><span data-ttu-id="2b982-295">ms-settings:privacy-motion</span><span class="sxs-lookup"><span data-stu-id="2b982-295">ms-settings:privacy-motion</span></span></td>
   <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-296">Spracherkennung, Freihand und Eingabe</span><span class="sxs-lookup"><span data-stu-id="2b982-296">Speech, inking & typing</span></span></td>
   <td><span data-ttu-id="2b982-297">ms-settings:privacy-speechtyping</span><span class="sxs-lookup"><span data-stu-id="2b982-297">ms-settings:privacy-speechtyping</span></span></td>
   <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-298">Kontoinformationen</span><span class="sxs-lookup"><span data-stu-id="2b982-298">Account info</span></span></td>
   <td><span data-ttu-id="2b982-299">ms-settings:privacy-accountinfo</span><span class="sxs-lookup"><span data-stu-id="2b982-299">ms-settings:privacy-accountinfo</span></span></td>
   <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-300">Kontakte</span><span class="sxs-lookup"><span data-stu-id="2b982-300">Contacts</span></span></td>
   <td><span data-ttu-id="2b982-301">ms-settings:privacy-contacts</span><span class="sxs-lookup"><span data-stu-id="2b982-301">ms-settings:privacy-contacts</span></span></td>
   <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-302">Kalender</span><span class="sxs-lookup"><span data-stu-id="2b982-302">Calendar</span></span></td>
   <td><span data-ttu-id="2b982-303">ms-settings:privacy-calendar</span><span class="sxs-lookup"><span data-stu-id="2b982-303">ms-settings:privacy-calendar</span></span></td>
   <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-304">Anrufliste</span><span class="sxs-lookup"><span data-stu-id="2b982-304">Call history</span></span></td>
   <td><span data-ttu-id="2b982-305">ms-settings:privacy-callhistory</span><span class="sxs-lookup"><span data-stu-id="2b982-305">ms-settings:privacy-callhistory</span></span></td>
   <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-306">E-Mail</span><span class="sxs-lookup"><span data-stu-id="2b982-306">Email</span></span></td>
  <td><span data-ttu-id="2b982-307">ms-settings:privacy-email</span><span class="sxs-lookup"><span data-stu-id="2b982-307">ms-settings:privacy-email</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-308">Nachrichten</span><span class="sxs-lookup"><span data-stu-id="2b982-308">Messaging</span></span></td>
    <td><span data-ttu-id="2b982-309">ms-settings:privacy-messaging</span><span class="sxs-lookup"><span data-stu-id="2b982-309">ms-settings:privacy-messaging</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-310">Funkempfang</span><span class="sxs-lookup"><span data-stu-id="2b982-310">Radios</span></span></td>
    <td><span data-ttu-id="2b982-311">ms-settings:privacy-radios</span><span class="sxs-lookup"><span data-stu-id="2b982-311">ms-settings:privacy-radios</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-312">Hintergrund-Apps</span><span class="sxs-lookup"><span data-stu-id="2b982-312">Background Apps</span></span></td>
    <td><span data-ttu-id="2b982-313">ms-settings:privacy-backgroundapps</span><span class="sxs-lookup"><span data-stu-id="2b982-313">ms-settings:privacy-backgroundapps</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-314">Weitere Geräte</span><span class="sxs-lookup"><span data-stu-id="2b982-314">Other devices</span></span></td>
    <td><span data-ttu-id="2b982-315">ms-settings:privacy-customdevices</span><span class="sxs-lookup"><span data-stu-id="2b982-315">ms-settings:privacy-customdevices</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-316">Feedback und Diagnose</span><span class="sxs-lookup"><span data-stu-id="2b982-316">Feedback & diagnostics</span></span></td>
    <td><span data-ttu-id="2b982-317">ms-settings:privacy-feedback</span><span class="sxs-lookup"><span data-stu-id="2b982-317">ms-settings:privacy-feedback</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td rowspan="5"><span data-ttu-id="2b982-318">Surface Hub</span><span class="sxs-lookup"><span data-stu-id="2b982-318">Surface Hub</span></span></td>
  <td><span data-ttu-id="2b982-319">Konten</span><span class="sxs-lookup"><span data-stu-id="2b982-319">Accounts</span></span></td>
    <td><span data-ttu-id="2b982-320">ms-settings:surfacehub-accounts</span><span class="sxs-lookup"><span data-stu-id="2b982-320">ms-settings:surfacehub-accounts</span></span></td>
      <td></td>
  </tr>
  <tr>
    <td><span data-ttu-id="2b982-321">Team-Konferenz</span><span class="sxs-lookup"><span data-stu-id="2b982-321">Team Conferencing</span></span></td>
      <td><span data-ttu-id="2b982-322">ms-settings:surfacehub-calling</span><span class="sxs-lookup"><span data-stu-id="2b982-322">ms-settings:surfacehub-calling</span></span></td>
      <td></td>
  </tr>
  <tr>
    <td><span data-ttu-id="2b982-323">Team-Geräteverwaltung</span><span class="sxs-lookup"><span data-stu-id="2b982-323">Team device management</span></span></td>
      <td><span data-ttu-id="2b982-324">ms-settings:surfacehub-devicemanagenent</span><span class="sxs-lookup"><span data-stu-id="2b982-324">ms-settings:surfacehub-devicemanagenent</span></span></td>
      <td></td>
  </tr>
  <tr>
    <td><span data-ttu-id="2b982-325">Bereinigung der Sitzung</span><span class="sxs-lookup"><span data-stu-id="2b982-325">Session cleanup</span></span></td>
      <td><span data-ttu-id="2b982-326">ms-settings:surfacehub-sessioncleanup</span><span class="sxs-lookup"><span data-stu-id="2b982-326">ms-settings:surfacehub-sessioncleanup</span></span></td>
      <td></td>
  </tr>
  <tr>
    <td><span data-ttu-id="2b982-327">Willkommensseite</span><span class="sxs-lookup"><span data-stu-id="2b982-327">Welcome screen</span></span></td>
      <td><span data-ttu-id="2b982-328">ms-settings:surfacehub-welcome</span><span class="sxs-lookup"><span data-stu-id="2b982-328">ms-settings:surfacehub-welcome</span></span></td>
      <td></td>
  </tr>
    <td rowspan="19"><span data-ttu-id="2b982-329">System</span><span class="sxs-lookup"><span data-stu-id="2b982-329">System</span></span></td>
    <td><span data-ttu-id="2b982-330">Gemeinsame Erfahrung</span><span class="sxs-lookup"><span data-stu-id="2b982-330">Shared experiences</span></span></td>
      <td><span data-ttu-id="2b982-331">ms-settings:crossdevice</span><span class="sxs-lookup"><span data-stu-id="2b982-331">ms-settings:crossdevice</span></span></td>
    <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-332">Anzeige</span><span class="sxs-lookup"><span data-stu-id="2b982-332">Display</span></span></td>
    <td><span data-ttu-id="2b982-333">ms-settings:display</span><span class="sxs-lookup"><span data-stu-id="2b982-333">ms-settings:display</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-334">Multitasking</span><span class="sxs-lookup"><span data-stu-id="2b982-334">Multitasking</span></span></td>
    <td><span data-ttu-id="2b982-335">ms-settings:multitasking</span><span class="sxs-lookup"><span data-stu-id="2b982-335">ms-settings:multitasking</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-336">Projizieren auf diesen PC</span><span class="sxs-lookup"><span data-stu-id="2b982-336">Projecting to this PC</span></span></td>
    <td><span data-ttu-id="2b982-337">ms-settings:project</span><span class="sxs-lookup"><span data-stu-id="2b982-337">ms-settings:project</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-338">Tabletmodus</span><span class="sxs-lookup"><span data-stu-id="2b982-338">Tablet mode</span></span></td>
    <td><span data-ttu-id="2b982-339">ms-settings:tabletmode</span><span class="sxs-lookup"><span data-stu-id="2b982-339">ms-settings:tabletmode</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-340">Taskleiste</span><span class="sxs-lookup"><span data-stu-id="2b982-340">Taskbar</span></span></td>
    <td><span data-ttu-id="2b982-341">ms-settings:taskbar</span><span class="sxs-lookup"><span data-stu-id="2b982-341">ms-settings:taskbar</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-342">Telefon</span><span class="sxs-lookup"><span data-stu-id="2b982-342">Phone</span></span></td>
    <td><span data-ttu-id="2b982-343">ms-settings:phone-defaultapps</span><span class="sxs-lookup"><span data-stu-id="2b982-343">ms-settings:phone-defaultapps</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-344">Anzeige</span><span class="sxs-lookup"><span data-stu-id="2b982-344">Display</span></span></td>
    <td><span data-ttu-id="2b982-345">ms-settings:screenrotation</span><span class="sxs-lookup"><span data-stu-id="2b982-345">ms-settings:screenrotation</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-346">Benachrichtigungen & Infos</span><span class="sxs-lookup"><span data-stu-id="2b982-346">Notifications & actions</span></span></td>
    <td><span data-ttu-id="2b982-347">ms-settings:notifications</span><span class="sxs-lookup"><span data-stu-id="2b982-347">ms-settings:notifications</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-348">Telefon</span><span class="sxs-lookup"><span data-stu-id="2b982-348">Phone</span></span></td>
    <td><span data-ttu-id="2b982-349">ms-settings:phone</span><span class="sxs-lookup"><span data-stu-id="2b982-349">ms-settings:phone</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-350">Nachrichten</span><span class="sxs-lookup"><span data-stu-id="2b982-350">Messaging</span></span></td>
    <td><span data-ttu-id="2b982-351">ms-settings:messaging</span><span class="sxs-lookup"><span data-stu-id="2b982-351">ms-settings:messaging</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-352">Stromsparmodus</span><span class="sxs-lookup"><span data-stu-id="2b982-352">Battery Saver</span></span></td>
  <td><span data-ttu-id="2b982-353">ms-settings:batterysaver</span><span class="sxs-lookup"><span data-stu-id="2b982-353">ms-settings:batterysaver</span></span></td>
  <td><span data-ttu-id="2b982-354">Nur auf Geräten mit Akku verfügbar, z.B. Tablets</span><span class="sxs-lookup"><span data-stu-id="2b982-354">Only available on devices that have a battery, such as a tablet</span></span></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-355">Akkubetrieb</span><span class="sxs-lookup"><span data-stu-id="2b982-355">Battery use</span></span></td>
  <td><span data-ttu-id="2b982-356">ms-settings:batterysaver-usagedetails</span><span class="sxs-lookup"><span data-stu-id="2b982-356">ms-settings:batterysaver-usagedetails</span></span></td>
  <td><span data-ttu-id="2b982-357">Nur auf Geräten mit Akku verfügbar, z.B. Tablets</span><span class="sxs-lookup"><span data-stu-id="2b982-357">Only available on devices that have a battery, such as a tablet</span></span></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-358">Ein/Aus und Standbymodus</span><span class="sxs-lookup"><span data-stu-id="2b982-358">Power & sleep</span></span></td>
  <td><span data-ttu-id="2b982-359">ms-settings:powersleep</span><span class="sxs-lookup"><span data-stu-id="2b982-359">ms-settings:powersleep</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-360">Info</span><span class="sxs-lookup"><span data-stu-id="2b982-360">About</span></span></td>
    <td><span data-ttu-id="2b982-361">ms-settings:about</span><span class="sxs-lookup"><span data-stu-id="2b982-361">ms-settings:about</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-362">Speicher</span><span class="sxs-lookup"><span data-stu-id="2b982-362">Storage</span></span></td>
    <td><span data-ttu-id="2b982-363">ms-settings:storagesense</span><span class="sxs-lookup"><span data-stu-id="2b982-363">ms-settings:storagesense</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-364">Speicheroptimierung</span><span class="sxs-lookup"><span data-stu-id="2b982-364">Storage Sense</span></span></td>
    <td><span data-ttu-id="2b982-365">ms-settings:storagepolicies</span><span class="sxs-lookup"><span data-stu-id="2b982-365">ms-settings:storagepolicies</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-366">Verschlüsselung</span><span class="sxs-lookup"><span data-stu-id="2b982-366">Encryption</span></span></td>
    <td><span data-ttu-id="2b982-367">ms-settings:deviceencryption</span><span class="sxs-lookup"><span data-stu-id="2b982-367">ms-settings:deviceencryption</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-368">Offlinekarten</span><span class="sxs-lookup"><span data-stu-id="2b982-368">Offline Maps</span></span></td>
    <td><span data-ttu-id="2b982-369">ms-settings:maps</span><span class="sxs-lookup"><span data-stu-id="2b982-369">ms-settings:maps</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td rowspan="5"><span data-ttu-id="2b982-370">Zeit und Sprache</span><span class="sxs-lookup"><span data-stu-id="2b982-370">Time and language</span></span></td>
  <td><span data-ttu-id="2b982-371">Datum und Uhrzeit</span><span class="sxs-lookup"><span data-stu-id="2b982-371">Date & time</span></span></td>
    <td><span data-ttu-id="2b982-372">ms-settings:dateandtime</span><span class="sxs-lookup"><span data-stu-id="2b982-372">ms-settings:dateandtime</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-373">Region & Sprache</span><span class="sxs-lookup"><span data-stu-id="2b982-373">Region & language</span></span></td>
    <td><span data-ttu-id="2b982-374">ms-settings:regionlanguage</span><span class="sxs-lookup"><span data-stu-id="2b982-374">ms-settings:regionlanguage</span></span></td>
  <td></td>
 </tr>
 <tr>
     <td><span data-ttu-id="2b982-375">Spracherkennungssprache</span><span class="sxs-lookup"><span data-stu-id="2b982-375">Speech Language</span></span></td>
     <td><span data-ttu-id="2b982-376">ms-settings:speech</span><span class="sxs-lookup"><span data-stu-id="2b982-376">ms-settings:speech</span></span></td>
     <td></td>
 </tr>
 <tr>
     <td><span data-ttu-id="2b982-377">Pinyin-Tastatur</span><span class="sxs-lookup"><span data-stu-id="2b982-377">Pinyin keyboard</span></span></td>
     <td><span data-ttu-id="2b982-378">ms-settings:regionlanguage-chsime-pinyin</span><span class="sxs-lookup"><span data-stu-id="2b982-378">ms-settings:regionlanguage-chsime-pinyin</span></span></td>
     <td><span data-ttu-id="2b982-379">Verfügbar, wenn der Microsoft Pinyin-Eingabemethoden-Editor installiert ist</span><span class="sxs-lookup"><span data-stu-id="2b982-379">Available if the Microsoft Pinyin input method editor is installed</span></span></td>
 </tr>
 <tr>
     <td><span data-ttu-id="2b982-380">Wubi-Eingabemodus</span><span class="sxs-lookup"><span data-stu-id="2b982-380">Wubi input mode</span></span></td>
     <td><span data-ttu-id="2b982-381">ms-settings:regionlanguage-chsime-wubi</span><span class="sxs-lookup"><span data-stu-id="2b982-381">ms-settings:regionlanguage-chsime-wubi</span></span></td>
     <td><span data-ttu-id="2b982-382">Verfügbar, wenn der Microsoft Wubi-Eingabemethoden-Editor installiert ist</span><span class="sxs-lookup"><span data-stu-id="2b982-382">Available if the Microsoft Wubi input method editor is installed</span></span></td>
 </tr>
 <tr>
  <td rowspan="13"><span data-ttu-id="2b982-383">Update und Sicherheit</span><span class="sxs-lookup"><span data-stu-id="2b982-383">Update & security</span></span></td>
  <td><span data-ttu-id="2b982-384">Einrichten von Windows Hello</span><span class="sxs-lookup"><span data-stu-id="2b982-384">Windows Hello setup</span></span></td>
    <td><span data-ttu-id="2b982-385">ms-settings:signinoptions-launchfaceenrollment</span><span class="sxs-lookup"><span data-stu-id="2b982-385">ms-settings:signinoptions-launchfaceenrollment</span></span><br><span data-ttu-id="2b982-386">ms-settings:signinoptions-launchfingerprintenrollment</span><span class="sxs-lookup"><span data-stu-id="2b982-386">ms-settings:signinoptions-launchfingerprintenrollment</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="2b982-387">Sicherung</span><span class="sxs-lookup"><span data-stu-id="2b982-387">Backup</span></span></td>
      <td><span data-ttu-id="2b982-388">ms-settings:backup</span><span class="sxs-lookup"><span data-stu-id="2b982-388">ms-settings:backup</span></span></td>
    <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-389">Mein Gerät suchen</span><span class="sxs-lookup"><span data-stu-id="2b982-389">Find My Device</span></span></td>
    <td><span data-ttu-id="2b982-390">ms-settings:findmydevice</span><span class="sxs-lookup"><span data-stu-id="2b982-390">ms-settings:findmydevice</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-391">Windows-Insider-Programm</span><span class="sxs-lookup"><span data-stu-id="2b982-391">Windows Insider Program</span></span></td>
  <td><span data-ttu-id="2b982-392">ms-settings:windowsinsider</span><span class="sxs-lookup"><span data-stu-id="2b982-392">ms-settings:windowsinsider</span></span></td>
  <td><span data-ttu-id="2b982-393">Nur vorhanden Sie, wenn der Benutzer bei WIP registriert ist</span><span class="sxs-lookup"><span data-stu-id="2b982-393">Only present if user is enrolled in WIP</span></span></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-394">Windows Update</span><span class="sxs-lookup"><span data-stu-id="2b982-394">Windows Update</span></span></td>
  <td><span data-ttu-id="2b982-395">ms-settings:windowsupdate</span><span class="sxs-lookup"><span data-stu-id="2b982-395">ms-settings:windowsupdate</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-396">Windows Update</span><span class="sxs-lookup"><span data-stu-id="2b982-396">Windows Update</span></span></td>
    <td><span data-ttu-id="2b982-397">ms-settings:windowsupdate-history</span><span class="sxs-lookup"><span data-stu-id="2b982-397">ms-settings:windowsupdate-history</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-398">Windows Update</span><span class="sxs-lookup"><span data-stu-id="2b982-398">Windows Update</span></span></td>
    <td><span data-ttu-id="2b982-399">ms-settings:windowsupdate-options</span><span class="sxs-lookup"><span data-stu-id="2b982-399">ms-settings:windowsupdate-options</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-400">Windows Update</span><span class="sxs-lookup"><span data-stu-id="2b982-400">Windows Update</span></span></td>
    <td><span data-ttu-id="2b982-401">ms-settings:windowsupdate-restartoptions</span><span class="sxs-lookup"><span data-stu-id="2b982-401">ms-settings:windowsupdate-restartoptions</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-402">Windows Update</span><span class="sxs-lookup"><span data-stu-id="2b982-402">Windows Update</span></span></td>
    <td><span data-ttu-id="2b982-403">ms-settings:windowsupdate-action</span><span class="sxs-lookup"><span data-stu-id="2b982-403">ms-settings:windowsupdate-action</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-404">Aktivierung</span><span class="sxs-lookup"><span data-stu-id="2b982-404">Activation</span></span></td>
    <td><span data-ttu-id="2b982-405">ms-settings:activation</span><span class="sxs-lookup"><span data-stu-id="2b982-405">ms-settings:activation</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-406">Wiederherstellung</span><span class="sxs-lookup"><span data-stu-id="2b982-406">Recovery</span></span></td>
    <td><span data-ttu-id="2b982-407">ms-settings:recovery</span><span class="sxs-lookup"><span data-stu-id="2b982-407">ms-settings:recovery</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-408">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="2b982-408">Troubleshoot</span></span></td>
    <td><span data-ttu-id="2b982-409">ms-settings:troubleshoot</span><span class="sxs-lookup"><span data-stu-id="2b982-409">ms-settings:troubleshoot</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-410">WindowsDefender</span><span class="sxs-lookup"><span data-stu-id="2b982-410">Windows Defender</span></span></td>
    <td><span data-ttu-id="2b982-411">ms-settings:windowsdefender</span><span class="sxs-lookup"><span data-stu-id="2b982-411">ms-settings:windowsdefender</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-412">Für Entwickler</span><span class="sxs-lookup"><span data-stu-id="2b982-412">For developers</span></span></td>
    <td><span data-ttu-id="2b982-413">ms-settings:developers</span><span class="sxs-lookup"><span data-stu-id="2b982-413">ms-settings:developers</span></span></td>
  <td></td>
 </tr>
 <tr>
  <td rowspan="2"><span data-ttu-id="2b982-414">Benutzerkonten</span><span class="sxs-lookup"><span data-stu-id="2b982-414">User  Accounts</span></span></td>
  <td><span data-ttu-id="2b982-415">Windows Anywhere</span><span class="sxs-lookup"><span data-stu-id="2b982-415">Windows Anywhere</span></span></td>
  <td><span data-ttu-id="2b982-416">ms-settings:windowsanywhere</span><span class="sxs-lookup"><span data-stu-id="2b982-416">ms-settings:windowsanywhere</span></span></td>
  <td><span data-ttu-id="2b982-417">Gerät muss Windows Anywhere-fähig sein</span><span class="sxs-lookup"><span data-stu-id="2b982-417">Device must be Windows Anywhere-capable</span></span></td>
 </tr>
 <tr>
  <td><span data-ttu-id="2b982-418">Bereitstellung</span><span class="sxs-lookup"><span data-stu-id="2b982-418">Provisioning</span></span></td>
  <td><span data-ttu-id="2b982-419">ms-settings:workplace-provisioning</span><span class="sxs-lookup"><span data-stu-id="2b982-419">ms-settings:workplace-provisioning</span></span></td>
  <td><span data-ttu-id="2b982-420">Ist nur verfügbar, wenn Enterprise ein Bereitstellungspaket bereitgestellt hat</span><span class="sxs-lookup"><span data-stu-id="2b982-420">Only available if enterprise has deployed a provisioning package</span></span></td>
 </tr>
</table><br/>  
