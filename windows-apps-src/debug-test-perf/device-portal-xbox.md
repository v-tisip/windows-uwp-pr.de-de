---
author: PatrickFarley
ms.assetid: bf0a8b01-79f1-4944-9d78-9741e235dbe9
title: Geräteportal für Xbox
description: Hier erfahren Sie, wie Sie das Device Portal für Xbox One aktivieren.
ms.author: pafarley
ms.date: 02/12/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, geräteportal
ms.localizationpriority: medium
ms.openlocfilehash: 404db3963d2f9508d7c81053abf96b0e742103f7
ms.sourcegitcommit: 3727445c1d6374401b867c78e4ff8b07d92b7adc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2018
ms.locfileid: "2910311"
---
# <a name="device-portal-for-xbox"></a><span data-ttu-id="888fc-104">Device Portal für Xbox</span><span class="sxs-lookup"><span data-stu-id="888fc-104">Device Portal for Xbox</span></span>

## <a name="set-up-device-portal-on-xbox"></a><span data-ttu-id="888fc-105">Einrichten des Geräteportals für Xbox</span><span class="sxs-lookup"><span data-stu-id="888fc-105">Set up Device Portal on Xbox</span></span>

<span data-ttu-id="888fc-106">Die folgenden Schritte zeigen, wie Sie das Xbox-Geräteportal aktivieren, das Ihnen den Remotezugriff auf Ihre Xbox ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="888fc-106">The following steps show how to enable the Xbox Device Portal, which gives you remote access to your development Xbox.</span></span>

1. <span data-ttu-id="888fc-107">Öffnen Sie Dev Home.</span><span class="sxs-lookup"><span data-stu-id="888fc-107">Open Dev Home.</span></span> <span data-ttu-id="888fc-108">Dies sollte standardmäßig beim Booten der Xbox geöffnet werden, aber Sie können es auch auf von der Startseite aus öffnen.</span><span class="sxs-lookup"><span data-stu-id="888fc-108">This should open by default when you boot up your development Xbox, but you can also open it from the home screen.</span></span>

    ![„Dev Home“ im Geräteportal](images/device-portal-xbox-1.png)

2. <span data-ttu-id="888fc-110">Navigieren Sie in Dev Home zur Registerkarte **Home**, und wählen Sie im Abschnitt **Remotezugriff** die Option **Remotezugriffseinstellungen** aus.</span><span class="sxs-lookup"><span data-stu-id="888fc-110">Within Dev Home, on the **Home** tab, under **Remote Access**, select **Remote Access Settings**.</span></span>

    ![Geräteportal-RemoteManagement-Tool](images/device-portal-xbox-15.png)

3. <span data-ttu-id="888fc-112">Markieren Sie die Einstellung **Xbox-Geräteportal aktivieren**.</span><span class="sxs-lookup"><span data-stu-id="888fc-112">Check the **Enable Xbox Device Portal** setting.</span></span>

4. <span data-ttu-id="888fc-113">Wählen Sie unter **Authentifizierung** die Option **Benutzername und Kennwort festlegen**.</span><span class="sxs-lookup"><span data-stu-id="888fc-113">Under **Authentication**, select **Set username and password**.</span></span> <span data-ttu-id="888fc-114">Geben Sie einen **Benutzernamen** und ein **Kennwort** ein, um den Zugriff auf Ihr Dev-Kit über einen Browser zu authentifizieren und **speichern** Sie diese.</span><span class="sxs-lookup"><span data-stu-id="888fc-114">Enter a **User name** and **Password** to use to authenticate access to your dev kit from a browser, and **Save** them.</span></span>

5. <span data-ttu-id="888fc-115">**Schließen** Sie die Seite **Remotezugriff** und notieren Sie die unter **Remotezugriff** auf der Registerkarte **Startseite** aufgeführte URL.</span><span class="sxs-lookup"><span data-stu-id="888fc-115">**Close** the **Remote Access** page and note the URL listed under **Remote Access** on the **Home** tab.</span></span>

6. <span data-ttu-id="888fc-116">Geben Sie die URL in Ihrem Browser ein, und melden Sie sich mit den Anmeldeinformationen an, die Sie konfiguriert haben.</span><span class="sxs-lookup"><span data-stu-id="888fc-116">Enter the URL in your browser, and then sign in with the credentials you configured.</span></span>

7. <span data-ttu-id="888fc-117">Sie erhalten eine Warnung zum Zertifikat, das bereitgestellt wurde, ähnlich der Warnung in der folgenden Abbildung.</span><span class="sxs-lookup"><span data-stu-id="888fc-117">You will receive a warning about the certificate that was provided, similar to that pictured below.</span></span> <span data-ttu-id="888fc-118">Klicken Sie in Edge auf **Details** und auf **Weiter zur Webseite**, um auf das Xbox-Geräteportal zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="888fc-118">In Edge, click on **Details** and then **Go on to the webpage** to access the Xbox Device Portal.</span></span> <span data-ttu-id="888fc-119">Geben Sie in dem sich öffnenden Dialog den Benutzernamen und das Kennwort ein, die Sie zuvor auf Ihrer Xbox eingegeben haben.</span><span class="sxs-lookup"><span data-stu-id="888fc-119">In the dialog that pops up, enter the username and password that you entered previously on your Xbox.</span></span>

    ![Fehler beim Zertifikat für das Geräteportal](images/device-portal-xbox-3.png)

## <a name="device-portal-pages"></a><span data-ttu-id="888fc-121">Seiten des Geräteportals</span><span class="sxs-lookup"><span data-stu-id="888fc-121">Device Portal pages</span></span>

<span data-ttu-id="888fc-122">Das Xbox-Geräteportal bietet eine Reihe von Standardseiten ähnlich dem, was im Windows-Geräteportal verfügbar ist. Dazu gibt es mehrere Seiten, die einzigartig sind.</span><span class="sxs-lookup"><span data-stu-id="888fc-122">The Xbox Device Portal provides a set of standard pages similar to what's available on the Windows Device Portal, as well as several pages that are unique.</span></span> <span data-ttu-id="888fc-123">Ausführliche Beschreibungen der gemeinsamen Seiten finden Sie unter [Übersicht über das Windows-Geräteportal](device-portal.md).</span><span class="sxs-lookup"><span data-stu-id="888fc-123">For detailed descriptions of the former, see [Windows Device Portal overview](device-portal.md).</span></span> <span data-ttu-id="888fc-124">Die folgenden Abschnitte beschreiben die Seiten, die es nur im Xbox-Geräteportal gibt.</span><span class="sxs-lookup"><span data-stu-id="888fc-124">The following sections describe the pages that are unique to the Xbox Device Portal.</span></span>

### <a name="home"></a><span data-ttu-id="888fc-125">Startseite</span><span class="sxs-lookup"><span data-stu-id="888fc-125">Home</span></span>

<span data-ttu-id="888fc-126">Ähnlich wie die **Apps-Manager**-Seite des Windows-Geräteportals zeigt die **Startseite** des Xbox-Geräteportals unter **Meine Spiele und Apps** eine Liste der installierten Spiele und Apps an.</span><span class="sxs-lookup"><span data-stu-id="888fc-126">Similar to the Windows Device Portal's **Apps manager** page, the Xbox Device Portal's **Home** page displays a list of installed games and apps under **My games & apps**.</span></span> <span data-ttu-id="888fc-127">Sie können auf den Namen eines Spiels oder einer App klicken, um weitere Details zu sehen, z. B. den **Paketfamiliennamen**.</span><span class="sxs-lookup"><span data-stu-id="888fc-127">You can click on the name of a game or app to see more details about it, such as the **Package family name**.</span></span> <span data-ttu-id="888fc-128">In der Dropdown-Liste **Aktionen** können Sie Aktionen für das Spiel oder die App ausführen, z. B. **Starten**.</span><span class="sxs-lookup"><span data-stu-id="888fc-128">In the **Actions** drop down, you can take action on the game or app, such as **Launch** it.</span></span>

<span data-ttu-id="888fc-129">Unter **Xbox Live-Testkonten** können Sie die mit Ihrer Xbox verbundenen Konten verwalten.</span><span class="sxs-lookup"><span data-stu-id="888fc-129">Under **Xbox Live test accounts**, you can manage the accounts associated with your Xbox.</span></span> <span data-ttu-id="888fc-130">Sie können Benutzer und Gastkonten hinzufügen, neue Benutzer anlegen, Benutzer an- und abmelden und Konten entfernen.</span><span class="sxs-lookup"><span data-stu-id="888fc-130">You can add users and guest accounts, create new users, sign users in and out, and remove accounts.</span></span>

![Startseite](images/device-portal-xbox-16.png)

### <a name="xbox-live-game-saves"></a><span data-ttu-id="888fc-132">Xbox Live (Gespeicherte Spiele)</span><span class="sxs-lookup"><span data-stu-id="888fc-132">Xbox Live (Game saves)</span></span>

<span data-ttu-id="888fc-133">Sowohl das Windows-Geräteportal als auch das Xbox-Geräteportal haben eine **Xbox Live**-Seite.</span><span class="sxs-lookup"><span data-stu-id="888fc-133">Both the Windows Device Portal and the Xbox Device Portal have an **Xbox Live** page.</span></span> <span data-ttu-id="888fc-134">Allerdings hat das Xbox-Geräteportal einen einzigartigen Bereich namens **Gespeicherte Xbox Live-Spiele**, in dem Sie Daten für Spiele, die auf Ihrer Xbox installiert sind, speichern können.</span><span class="sxs-lookup"><span data-stu-id="888fc-134">However, the Xbox Device Portal has a unique section, **Xbox Live game saves**, where you can save data for games installed on your Xbox.</span></span> <span data-ttu-id="888fc-135">Geben Sie die **Service-Konfigurations-ID (SCID)** (siehe [Xbox Live-Service-Konfiguration](../xbox-live/xbox-live-service-configuration.md#get-your-ids)), den **Membernamen (MSA)** und den **Paketfamiliennamen (PFN)** ein, die dem Titel und dem Spiel zugeordnet sind, suchen Sie nach der **Eingabedatei (JSON oder XML)** und wählen Sie dann eine der Schaltflächen (**Zurücksetzen**, **Importieren**, **Exportieren** und **Löschen**) aus, um die gespeicherten Daten zu bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="888fc-135">Enter the **Service Configuration ID (SCID)** (see [Xbox Live service configuration](../xbox-live/xbox-live-service-configuration.md#get-your-ids) for more information), **Membername (MSA)**, and **Package Family Name (PFN)** associated with the title and game save, browse for the **Input File (.json or .xml)**, and then select one of the buttons (**Reset**, **Import**, **Export**, and **Delete**) to manipulate the save data.</span></span>

<span data-ttu-id="888fc-136">Im Abschnitt **Generieren** können Sie Dummy-Daten erzeugen und in der angegebenen Eingabedatei speichern.</span><span class="sxs-lookup"><span data-stu-id="888fc-136">In the **Generate** section, you can generate dummy data and save to the specified input file.</span></span> <span data-ttu-id="888fc-137">Geben Sie einfach **Container (Standardwert: 2)**, **Blobs (Standardwert: 3)** und **Blob-Größe (Standardwert: 1024)** ein und wählen Sie **Generieren** aus.</span><span class="sxs-lookup"><span data-stu-id="888fc-137">Simply enter the **Containers (default 2)**, **Blobs (default 3)**, and **Blob Size (default 1024)**, and select **Generate**.</span></span>

![Xbox Live](images/device-portal-xbox-17.png)

### <a name="http-monitor"></a><span data-ttu-id="888fc-139">HTTP-Monitor</span><span class="sxs-lookup"><span data-stu-id="888fc-139">HTTP monitor</span></span>

<span data-ttu-id="888fc-140">Der HTTP-Monitor ermöglicht es Ihnen, den entschlüsselten HTTP- und HTTPS-Datenverkehr Ihrer Anwendung oder Ihres Spiels anzuzeigen, wenn dieses auf Ihrer Xbox One läuft.</span><span class="sxs-lookup"><span data-stu-id="888fc-140">The HTTP Monitor allows you to view decrypted HTTP and HTTPS traffic from your app or game when it's running on your Xbox One.</span></span>

![HTTP-Monitor](images/device-portal-xbox-18.png)

<span data-ttu-id="888fc-142">Um ihn zu aktivieren, öffnen Sie Dev Home auf Ihrer Xbox One, gehen Sie auf die Registerkarte **Einstellungen** und aktivieren Sie im Feld **HTTP-Monitor-Einstellungen** die Option **HTTP-Monitor aktivieren**.</span><span class="sxs-lookup"><span data-stu-id="888fc-142">To enable it, open Dev Home on your Xbox One, go to the **Settings** tab, and in the **HTTP Monitor Settings** box, check **Enable HTTP Monitor**.</span></span>

![Dev Home: Networking](images/device-portal-xbox-14.png)

<span data-ttu-id="888fc-144">Sobald aktiviert, können Sie im Xbox-Geräteportal den HTTP- und HTTPS-Datenverkehr **stoppen**, **löschen** und **speichern**, indem Sie die entsprechenden Schaltflächen auswählen.</span><span class="sxs-lookup"><span data-stu-id="888fc-144">Once enabled, in the Xbox Device Portal, you can **Stop**, **Clear**, and **Save to file** HTTP and HTTPS traffic by selecting the respective buttons.</span></span>

### <a name="network-fiddler-tracing"></a><span data-ttu-id="888fc-145">Netzwerk (Fiddler-Ablaufverfolgung)</span><span class="sxs-lookup"><span data-stu-id="888fc-145">Network (Fiddler tracing)</span></span>

<span data-ttu-id="888fc-146">Die Seite **Netzwerk** im Xbox-Geräteportal ist fast identisch mit der Seite **Networking** im Windows-Geräteportal. **Fiddler-Nachverfolgung** gibt es jedoch nur im Xbox-Geräteportal.</span><span class="sxs-lookup"><span data-stu-id="888fc-146">The **Network** page in the Xbox Device Portal is almost identical to the **Networking** page in the Windows Device Portal, with the exception of **Fiddler tracing**, which is unique to the Xbox Device Portal.</span></span> <span data-ttu-id="888fc-147">Dadurch können Sie Fiddler auf Ihrem PC ausführen, um den HTTP- und HTTPS-Datenverkehr zwischen Ihrer Xbox One und dem Internet zu protokollieren und zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="888fc-147">This allows you to run Fiddler on your PC to log and inspect HTTP and HTTPS traffic between your Xbox One and the internet.</span></span> <span data-ttu-id="888fc-148">Weitere Informationen finden Sie unter [Verwendung von Fiddler mit Xbox One bei der Entwicklung für UWP](../xbox-apps/uwp-fiddler.md).</span><span class="sxs-lookup"><span data-stu-id="888fc-148">See [How to use Fiddler with Xbox One when developing for UWP](../xbox-apps/uwp-fiddler.md) for more information.</span></span>

![Netzwerk](images/device-portal-xbox-19.png)

### <a name="media-capture"></a><span data-ttu-id="888fc-150">Medienaufzeichnung</span><span class="sxs-lookup"><span data-stu-id="888fc-150">Media capture</span></span>

<span data-ttu-id="888fc-151">Auf der Seite **Medienaufzeichnung** können Sie **Screenshot erstellen** auswählen, um einen Screenshot von Ihrer Xbox One zu machen.</span><span class="sxs-lookup"><span data-stu-id="888fc-151">On the **Media capture** page, you can select **Capture Screenshot** to take a screenshot of your Xbox One.</span></span> <span data-ttu-id="888fc-152">Danach werden Sie von Ihrem Browser aufgefordert, die Datei herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="888fc-152">Once you do, your browser will prompt you to download the file.</span></span> <span data-ttu-id="888fc-153">Sie können **HDR bevorzugen** aktivieren, wenn Sie den Screenshot in HDR machen wollen (wenn die Konsole dies unterstützt).</span><span class="sxs-lookup"><span data-stu-id="888fc-153">You can check **Prefer HDR** if you want to take the screenshot in HDR (if the console supports it).</span></span>

![Medienaufzeichnung](images/device-portal-xbox-12.png)

### <a name="settings"></a><span data-ttu-id="888fc-155">Einstellungen</span><span class="sxs-lookup"><span data-stu-id="888fc-155">Settings</span></span>

<span data-ttu-id="888fc-156">Auf der Seite **Einstellungen** können Sie verschiedene Einstellungen für Ihre Xbox One anzeigen und bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="888fc-156">On the **Settings** page, you can view and edit several settings for your Xbox One.</span></span> <span data-ttu-id="888fc-157">Oben können Sie **Importieren** auswählen, um Einstellungen aus einer Datei zu importieren und **Exportieren**, um die aktuellen Einstellungen in eine TXT-Datei zu exportieren.</span><span class="sxs-lookup"><span data-stu-id="888fc-157">At the top, you can select **Import** to import settings from a file and **Export** to export the current settings to a .txt file.</span></span> <span data-ttu-id="888fc-158">Das Importieren von Einstellungen kann die Massenbearbeitung erleichtern, insbesondere bei der Konfiguration mehrerer Konsolen.</span><span class="sxs-lookup"><span data-stu-id="888fc-158">Importing settings can make bulk editing easier, especially when configuring multiple consoles.</span></span> <span data-ttu-id="888fc-159">Um eine zu importierende Einstellungsdatei zu erstellen, ändern Sie die Einstellungen so, wie Sie sie haben möchten, und exportieren Sie die Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="888fc-159">To create a settings file to import, change the settings to how you want them to be, and then export the settings.</span></span> <span data-ttu-id="888fc-160">Dann können Sie diese Datei verwenden, um Einstellungen schnell und einfach für andere Konsolen zu importieren.</span><span class="sxs-lookup"><span data-stu-id="888fc-160">Then you can use this file to import settings quickly and easily for other consoles.</span></span>

<span data-ttu-id="888fc-161">Es gibt mehrere Abschnitte mit unterschiedlichen Einstellungen zum Anzeigen und/oder Bearbeiten, die im Folgenden erläutert werden.</span><span class="sxs-lookup"><span data-stu-id="888fc-161">There are several sections with different settings to view and/or edit, which are explained below.</span></span>

![Einstellungen](images/device-portal-xbox-20.png)

![Einstellungen](images/device-portal-xbox-21.png)

#### <a name="device-information"></a><span data-ttu-id="888fc-164">Geräteinformationen</span><span class="sxs-lookup"><span data-stu-id="888fc-164">Device Information</span></span>

* <span data-ttu-id="888fc-165">**Gerätename**: Der Name des Gerätes.</span><span class="sxs-lookup"><span data-stu-id="888fc-165">**Device name**: The name of the device.</span></span> <span data-ttu-id="888fc-166">Zum Bearbeiten ändern Sie den Namen im Feld und wählen Sie **Speichern** aus.</span><span class="sxs-lookup"><span data-stu-id="888fc-166">To edit, change the name in the box and select **Save**.</span></span>

* <span data-ttu-id="888fc-167">**BS-Version**: Schreibgeschützt.</span><span class="sxs-lookup"><span data-stu-id="888fc-167">**OS version**: Read-only.</span></span> <span data-ttu-id="888fc-168">Die Versionsnummer des Betriebssystems.</span><span class="sxs-lookup"><span data-stu-id="888fc-168">The version number of the operating system.</span></span>

* <span data-ttu-id="888fc-169">**BS-Edition**: Schreibgeschützt.</span><span class="sxs-lookup"><span data-stu-id="888fc-169">**OS edition**: Read-only.</span></span> <span data-ttu-id="888fc-170">Der Name der Hauptversion des Betriebssystems.</span><span class="sxs-lookup"><span data-stu-id="888fc-170">The name of the major release of the operating system.</span></span>

* <span data-ttu-id="888fc-171">**Xbox Live-Geräte-ID**: Schreibgeschützt.</span><span class="sxs-lookup"><span data-stu-id="888fc-171">**Xbox Live device ID**: Read-only.</span></span>

* <span data-ttu-id="888fc-172">**Konsolen-ID**: Schreibgeschützt.</span><span class="sxs-lookup"><span data-stu-id="888fc-172">**Console ID**: Read-only.</span></span>

* <span data-ttu-id="888fc-173">**Seriennummer**: Schreibgeschützt.</span><span class="sxs-lookup"><span data-stu-id="888fc-173">**Serial number**: Read-only.</span></span>

* <span data-ttu-id="888fc-174">**Konsolentyp**: Schreibgeschützt.</span><span class="sxs-lookup"><span data-stu-id="888fc-174">**Console Type**: Read-only.</span></span> <span data-ttu-id="888fc-175">Der Typ des Xbox One-Geräts (Xbox One, Xbox One S oder Xbox One X).</span><span class="sxs-lookup"><span data-stu-id="888fc-175">The type of Xbox One device (Xbox One, Xbox One S, or Xbox One X).</span></span>

* <span data-ttu-id="888fc-176">**Dev-Modus**: Schreibgeschützt.</span><span class="sxs-lookup"><span data-stu-id="888fc-176">**Dev Mode**: Read-only.</span></span> <span data-ttu-id="888fc-177">Der Entwicklermodus, in dem sich das Gerät befindet.</span><span class="sxs-lookup"><span data-stu-id="888fc-177">The developer mode that the device is in.</span></span>

#### <a name="audio-settings"></a><span data-ttu-id="888fc-178">Audioeinstellungen</span><span class="sxs-lookup"><span data-stu-id="888fc-178">Audio Settings</span></span>

* <span data-ttu-id="888fc-179">**Audio-Bitstream-Format**: Das Format der Audiodaten.</span><span class="sxs-lookup"><span data-stu-id="888fc-179">**Audio bitstream format**: The format of the audio data.</span></span>

* <span data-ttu-id="888fc-180">**HDMI-Audio**: Die Art des Audiosignals über den HDMI-Anschluss.</span><span class="sxs-lookup"><span data-stu-id="888fc-180">**HDMI audio**: The type of audio through the HDMI port.</span></span>

* <span data-ttu-id="888fc-181">**Headset-Format**: Das Format des Audiosignals, das über Kopfhörer kommt.</span><span class="sxs-lookup"><span data-stu-id="888fc-181">**Headset format**: The format of the audio that comes through headphones.</span></span>

* <span data-ttu-id="888fc-182">**Optisches Audio**: Die Art des Audiosignals über den optischen Anschluss.</span><span class="sxs-lookup"><span data-stu-id="888fc-182">**Optical audio**: The type of audio through the optical port.</span></span>

* <span data-ttu-id="888fc-183">**Verwenden eines HDMI- oder optischen Audio-Headsets**: Aktivieren Sie dieses Kontrollkästchen, wenn Sie ein Headset verwenden, das über HDMI oder optisch angeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="888fc-183">**Use HDMI or optical audio headset**: Check this box if you are using a headset connected via HDMI or optical.</span></span>

#### <a name="display-settings"></a><span data-ttu-id="888fc-184">Anzeigeeinstellungen</span><span class="sxs-lookup"><span data-stu-id="888fc-184">Display Settings</span></span>

* <span data-ttu-id="888fc-185">**Farbtiefe**: Die Anzahl der Bits, die für jede Farbkomponente eines einzelnen Pixels verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="888fc-185">**Color depth**: The number of bits used for each color component of a single pixel.</span></span>

* <span data-ttu-id="888fc-186">**Farbraum**: Der dem Display zur Verfügung stehende Farbraum.</span><span class="sxs-lookup"><span data-stu-id="888fc-186">**Color space**: The color gamut available to the display.</span></span>

* <span data-ttu-id="888fc-187">**Bildschirmauflösung**: Die Auflösung des Displays.</span><span class="sxs-lookup"><span data-stu-id="888fc-187">**Display resolution**: The resolution of the display.</span></span>

* <span data-ttu-id="888fc-188">**Display-Verbindung**: Die Art der Verbindung zum Display.</span><span class="sxs-lookup"><span data-stu-id="888fc-188">**Display connection**: The type of connection to the display.</span></span>

* <span data-ttu-id="888fc-189">**High Dynamic Range (HDR) zulassen**: Aktiviert von HDR auf dem Display.</span><span class="sxs-lookup"><span data-stu-id="888fc-189">**Allow high dynamic range (HDR)**: Enables HDR on the display.</span></span> <span data-ttu-id="888fc-190">Nur für kompatible Displays verfügbar.</span><span class="sxs-lookup"><span data-stu-id="888fc-190">Only available to compatible displays.</span></span>

* <span data-ttu-id="888fc-191">**4K zulassen**: Aktiviert die 4K-Auflösung auf dem Display.</span><span class="sxs-lookup"><span data-stu-id="888fc-191">**Allow 4K**: Enables 4K resolution on the display.</span></span> <span data-ttu-id="888fc-192">Nur für kompatible Displays verfügbar.</span><span class="sxs-lookup"><span data-stu-id="888fc-192">Only available to compatible displays.</span></span>

* <span data-ttu-id="888fc-193">**Variable Aktualisierungsrate (VRR) zulassen**: Aktivieren von VRR auf dem Display.</span><span class="sxs-lookup"><span data-stu-id="888fc-193">**Allow Variable Refresh Rate (VRR)**: Enable VRR on the display.</span></span> <span data-ttu-id="888fc-194">Nur für kompatible Displays verfügbar.</span><span class="sxs-lookup"><span data-stu-id="888fc-194">Only available to compatible displays.</span></span>

#### <a name="kinect-settings"></a><span data-ttu-id="888fc-195">Kinect Einstellungen</span><span class="sxs-lookup"><span data-stu-id="888fc-195">Kinect Settings</span></span>

<span data-ttu-id="888fc-196">Um diese Einstellungen zu ändern, muss ein Kinect-Sensor an die Konsole angeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="888fc-196">A Kinect sensor must be connected to the console in order to change these settings.</span></span>

* <span data-ttu-id="888fc-197">**Kinect aktivieren**: Aktivieren des angeschlossenen Kinect-Sensors.</span><span class="sxs-lookup"><span data-stu-id="888fc-197">**Enable Kinect**: Enable the attached Kinect sensor.</span></span>

* <span data-ttu-id="888fc-198">**Kinect-Neuladen bei App-Änderung erzwingen**: Neuladen des angeschlossenen Kinect-Sensors, wenn eine andere App oder ein anderes Spiel ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="888fc-198">**Force Kinect reload on app change**: Reload the attached Kinect sensor whenever a different app or game is run.</span></span>

#### <a name="localization-settings"></a><span data-ttu-id="888fc-199">Lokalisierungseinstellungen</span><span class="sxs-lookup"><span data-stu-id="888fc-199">Localization Settings</span></span>

* <span data-ttu-id="888fc-200">**Geographische Region**: Die geographische Region, auf die das Gerät eingestellt ist.</span><span class="sxs-lookup"><span data-stu-id="888fc-200">**Geographic region**: The geographic region that the device is set to.</span></span> <span data-ttu-id="888fc-201">Muss ein spezifischer, zweistellige Ländercode sein (z. B. **DE** für Deutschland).</span><span class="sxs-lookup"><span data-stu-id="888fc-201">Must be the specific 2-character country code (for example, **US** for United States).</span></span>

* <span data-ttu-id="888fc-202">**Bevorzugte Sprache(n)**: Die Sprache, auf die das Gerät eingestellt ist.</span><span class="sxs-lookup"><span data-stu-id="888fc-202">**Preferred language(s)**: The language that the device is set to.</span></span>

* <span data-ttu-id="888fc-203">**Zeitzone**: Die Zeitzone, auf die das Gerät eingestellt ist.</span><span class="sxs-lookup"><span data-stu-id="888fc-203">**Time zone**: The time zone that the device is set to.</span></span>

#### <a name="network-settings"></a><span data-ttu-id="888fc-204">Netzwerkeinstellungen</span><span class="sxs-lookup"><span data-stu-id="888fc-204">Network Settings</span></span>

* <span data-ttu-id="888fc-205">**Funkeinstellungen**: Die Funkeinstellungen des Geräts (unabhängig davon, ob bestimmte Aspekte wie WLAN ein- oder ausgeschaltet sind).</span><span class="sxs-lookup"><span data-stu-id="888fc-205">**Wireless radio settings**: The wireless settings of the device (whether certain aspects such as wireless LAN are on or off).</span></span>

#### <a name="power-settings"></a><span data-ttu-id="888fc-206">Energieeinstellungen</span><span class="sxs-lookup"><span data-stu-id="888fc-206">Power Settings</span></span>

* <span data-ttu-id="888fc-207">**Im Ruhezustand den Bildschirm nach (Minuten) dimmen**: Der Bildschirm wird abgedunkelt, nachdem das Gerät für diese Zeit im Leerlauf war.</span><span class="sxs-lookup"><span data-stu-id="888fc-207">**When idle, dim screen after (minutes)**: The screen will dim after the device has been idle for this amount of time.</span></span> <span data-ttu-id="888fc-208">Auf **0** setzen, um den Bildschirm nie zu dimmen.</span><span class="sxs-lookup"><span data-stu-id="888fc-208">Set to **0** to never dim the screen.</span></span>

* <span data-ttu-id="888fc-209">**Im Leerlauf ausschalten nach**: Das Gerät schaltet sich nach dieser Zeit im Leerlauf ab.</span><span class="sxs-lookup"><span data-stu-id="888fc-209">**When idle, turn off after**: The device will shut down after it has been idle for this amount of time.</span></span>

* <span data-ttu-id="888fc-210">**Energiesparmodus**: Der Energiesparmodus des Gerätes.</span><span class="sxs-lookup"><span data-stu-id="888fc-210">**Power mode**: The power mode of the device.</span></span> <span data-ttu-id="888fc-211">Weitere Informationen finden Sie unter [Informationen zum Energiesparmodus und schnellen Hochfahren](http://support.xbox.com/xbox-one/console/learn-about-power-modes).</span><span class="sxs-lookup"><span data-stu-id="888fc-211">See [About energy-saving and instant-on power modes](http://support.xbox.com/xbox-one/console/learn-about-power-modes) for more information.</span></span>

* <span data-ttu-id="888fc-212">**Automatisches Booten der Konsole beim Anschluss an das Stromnetz**: Das Gerät schaltet sich automatisch ein, wenn es an eine Stromquelle angeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="888fc-212">**Automatically boot console when connected to power**: The device will automatically turn on when it is connected to a power source.</span></span>

#### <a name="preference-settings"></a><span data-ttu-id="888fc-213">Präferenzeinstellungen</span><span class="sxs-lookup"><span data-stu-id="888fc-213">Preference Settings</span></span>

* <span data-ttu-id="888fc-214">**Standard-Startoberfläche**: Legt fest, welcher Startbildschirm beim Einschalten des Geräts angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="888fc-214">**Default home experience**: Sets which home screen appears when the device is turned on.</span></span>

* <span data-ttu-id="888fc-215">**Verbindungen von der Xbox-App zulassen**: Die Xbox-App auf einem anderen Gerät (z. B. einem Windows 10 PC) kann sich mit dieser Konsole verbinden.</span><span class="sxs-lookup"><span data-stu-id="888fc-215">**Allow connections from the Xbox app**: The Xbox app on another device (such as a Windows 10 PC) can connect to this console.</span></span>

* <span data-ttu-id="888fc-216">**UWP-App standardmäßig als Spiele behandeln**: Spiele und Apps erhalten auf der Xbox verschiedene Ressourcen zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="888fc-216">**Treat UWP apps as games by default**: Games and apps get different resources allocated to them on Xbox.</span></span> <span data-ttu-id="888fc-217">Wenn Sie dieses Kontrollkästchen aktivieren, werden alle UWP-Pakete als Spiele identifiziert und erhalten somit mehr Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="888fc-217">If you check this box, all UWP packages will be identified as games and thus will get more resources.</span></span>

#### <a name="user-settings"></a><span data-ttu-id="888fc-218">Benutzereinstellungen</span><span class="sxs-lookup"><span data-stu-id="888fc-218">User Settings</span></span>

* <span data-ttu-id="888fc-219">**Benutzer automatisch anmelden**: Automatische Anmeldung des ausgewählten Benutzers beim Einschalten des Geräts.</span><span class="sxs-lookup"><span data-stu-id="888fc-219">**Auto sign in user**: Automatically signs in the selected user when the device is turned on.</span></span>

* <span data-ttu-id="888fc-220">**Benutzer-Controller automatisch anmelden**: Verknüpft automatisch einen bestimmten Controllertyp mit einem bestimmten Benutzer.</span><span class="sxs-lookup"><span data-stu-id="888fc-220">**Auto sign in user controller**: Automatically associates a particular controller type with a particular user.</span></span>

#### <a name="xbox-live-sandbox"></a><span data-ttu-id="888fc-221">Xbox Live-Sandbox</span><span class="sxs-lookup"><span data-stu-id="888fc-221">Xbox Live Sandbox</span></span>

<span data-ttu-id="888fc-222">Hier können Sie die Xbox Live-Sandbox ändern, in der sich das Gerät befindet.</span><span class="sxs-lookup"><span data-stu-id="888fc-222">Here you can change the Xbox Live sandbox that the device is in.</span></span> <span data-ttu-id="888fc-223">Geben Sie den Namen der Sandbox in das Feld ein und wählen Sie **Ändern** aus.</span><span class="sxs-lookup"><span data-stu-id="888fc-223">Enter the name of the sandbox in the box, and select **Change**.</span></span>

### <a name="scratch"></a><span data-ttu-id="888fc-224">Entwurf</span><span class="sxs-lookup"><span data-stu-id="888fc-224">Scratch</span></span>

<span data-ttu-id="888fc-225">Dies ist ein leerer Arbeitsbereich, den Sie nach Belieben anpassen können.</span><span class="sxs-lookup"><span data-stu-id="888fc-225">This is a blank workspace, which you can customize to your liking.</span></span> <span data-ttu-id="888fc-226">Sie können das Menü verwenden (klicken Sie auf die Menü-Schaltfläche oben links), um Tools hinzuzufügen (wählen Sie **Tools zum Arbeitsbereich hinzufügen**, dann die Tools und dann **Hinzufügen** aus).</span><span class="sxs-lookup"><span data-stu-id="888fc-226">You can use the menu (click the menu button at the top left) to add tools (select **Add tools to workspace**, then the tools that you want to add, then **Add**).</span></span> <span data-ttu-id="888fc-227">Beachten Sie, dass Sie dieses Menü verwenden können, um Tools zu jedem Arbeitsbereich hinzuzufügen und die Arbeitsbereiche selbst zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="888fc-227">Note that you can use this menu to add tools to any workspace, as well as manage the workspaces themselves.</span></span>

![Tools zum Arbeitsbereich hinzufügen](images/device-portal-xbox-13.png)

### <a name="game-event-data"></a><span data-ttu-id="888fc-229">Spiel Ereignisdaten</span><span class="sxs-lookup"><span data-stu-id="888fc-229">Game event data</span></span>

<span data-ttu-id="888fc-230">Auf der Seite **Spiel Ereignisdaten** können Sie eine Echtzeit-Diagramm die Streams der Anzahl der derzeit auf Ihrer Xbox One aufgezeichnete Ereignisse der Event Tracing for Windows (ETW)-Spiel anzeigen.</span><span class="sxs-lookup"><span data-stu-id="888fc-230">On the **Game event data** page, you can view a realtime graph that streams in the number of Event Tracing for Windows (ETW) game events currently recorded on your Xbox One.</span></span> <span data-ttu-id="888fc-231">Wenn Spiel Ereignisse, die aufgezeichnet, auf dem System vorhanden sind, können Sie auch Details (Ereignisnamen, Ereignis vorkommen und den Titel des Spiels) anzeigen, jedes Ereignis in einer Datentabelle unter der Diagramm-Daten beschreibt.</span><span class="sxs-lookup"><span data-stu-id="888fc-231">If there are game events recorded on the system, you can also view details (event name, event occurrence, and the game title) describing each event in a data table below the data graph.</span></span> <span data-ttu-id="888fc-232">In der Tabelle ist nur verfügbar, wenn Ereignisse aufgezeichnet vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="888fc-232">The table is only available if there are events recorded.</span></span>

![Spiel Ereignisdaten](images/device-portal-xbox-22.PNG)

## <a name="see-also"></a><span data-ttu-id="888fc-234">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="888fc-234">See also</span></span>

* [<span data-ttu-id="888fc-235">Übersicht über das Windows Geräteportal</span><span class="sxs-lookup"><span data-stu-id="888fc-235">Windows Device Portal overview</span></span>](device-portal.md)
* [<span data-ttu-id="888fc-236">Referenz zu Kern-APIs des Geräteportal</span><span class="sxs-lookup"><span data-stu-id="888fc-236">Device Portal core API reference</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)