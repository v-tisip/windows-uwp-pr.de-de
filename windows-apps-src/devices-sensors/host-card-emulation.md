---
author: msatranjr
ms.assetid: 26834A51-512B-485B-84C8-ABF713787588
title: Erstellen einer NFC-Smartcard-App
description: Windows Phone8.1 hat Apps mit NFC-Kartenemulation per SIM-basiertem sicherem Element unterstützt. Für dieses Modell war es aber erforderlich, dass Apps für das sichere Bezahlen eng mit den Betreibern von mobilen Netzwerken gekoppelt waren.
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: bc8064cd5446ca4c481c60b08cdf626ec85be646
ms.sourcegitcommit: 64cfb79fd27b09d49df99e8c9c46792c884593a7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.locfileid: "235726"
---
# <a name="create-an-nfc-smart-card-app"></a><span data-ttu-id="40ba5-104">Erstellen einer NFC-Smartcard-App</span><span class="sxs-lookup"><span data-stu-id="40ba5-104">Create an NFC Smart Card app</span></span>

<span data-ttu-id="40ba5-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="40ba5-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="40ba5-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="40ba5-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="40ba5-107">**Wichtig**  Dieses Thema trifft nur auf Windows10 Mobile zu.</span><span class="sxs-lookup"><span data-stu-id="40ba5-107">**Important**  This topic applies to Windows 10 Mobile only.</span></span>

<span data-ttu-id="40ba5-108">Windows Phone8.1 hat Apps mit NFC-Kartenemulation per SIM-basiertem sicherem Element unterstützt. Für dieses Modell war es aber erforderlich, dass Apps für das sichere Bezahlen eng mit den Betreibern von mobilen Netzwerken gekoppelt waren.</span><span class="sxs-lookup"><span data-stu-id="40ba5-108">Windows Phone 8.1 supported NFC card emulation apps using a SIM-based secure element, but that model required secure payment apps to be tightly coupled with mobile-network operators (MNO).</span></span> <span data-ttu-id="40ba5-109">Dadurch wurde die Vielfältigkeit möglicher Zahlungslösungen anderer Händler oder Entwickler eingeschränkt, die nicht mit Betreibern von mobilen Netzwerken gekoppelt waren.</span><span class="sxs-lookup"><span data-stu-id="40ba5-109">This limited the variety of possible payment solutions by other merchants or developers that are not coupled with MNOs.</span></span> <span data-ttu-id="40ba5-110">In Windows10 Mobile haben wir eine neue Technologie für die Kartenemulation eingeführt, die die Bezeichnung „Host-Kartenemulation“ (Host Card Emulation, HCE) trägt.</span><span class="sxs-lookup"><span data-stu-id="40ba5-110">In Windows 10 Mobile, we have introduced a new card emulation technology called, Host Card Emulation (HCE).</span></span> <span data-ttu-id="40ba5-111">Mithilfe von HCE-Technologie kann Ihre App direkt mit einem NFC-Kartenleser kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="40ba5-111">HCE technology allows your app to directly communicate with an NFC card reader.</span></span> <span data-ttu-id="40ba5-112">In diesem Thema wird veranschaulicht, wie die Host-Kartenemulation (HCE) für Windows10 Mobile-Geräte funktioniert und wie Sie eine HCE-App entwickeln können, bei der Kunden ohne Zusammenarbeit mit dem Betreiber eines mobilen Netzwerks per Smartphone auf Ihre Dienste zugreifen können, anstatt mit einer physischen Karte.</span><span class="sxs-lookup"><span data-stu-id="40ba5-112">This topic illustrates how Host Card Emulation (HCE) works on Windows 10 Mobile devices and how you can develop an HCE app so that your customers can access your services through their phone instead of a physical card without collaborating with an MNO.</span></span>

## <a name="what-you-need-to-develop-an-hce-app"></a><span data-ttu-id="40ba5-113">Voraussetzungen für die Entwicklung einer HCE-App</span><span class="sxs-lookup"><span data-stu-id="40ba5-113">What you need to develop an HCE app</span></span>


<span data-ttu-id="40ba5-114">Sie müssen Ihre Entwicklungsumgebung entsprechend vorbereiten, um eine HCE-basierte Kartenemulations-App für Windows10 Mobile entwickeln zu können.</span><span class="sxs-lookup"><span data-stu-id="40ba5-114">To develop an HCE-based card emulation app for Windows 10 Mobile, you will need to get your development environment setup.</span></span> <span data-ttu-id="40ba5-115">Hierzu können Sie die Anwendung Microsoft Visual Studio2015 installieren, die die Windows-Entwicklertools und den Windows10 Mobile-Emulator mit NFC-Emulationsunterstützung enthält.</span><span class="sxs-lookup"><span data-stu-id="40ba5-115">You can get set up by installing Microsoft Visual Studio 2015, which includes the Windows developer tools and the Windows 10 Mobile emulator with NFC emulation support.</span></span> <span data-ttu-id="40ba5-116">Weitere Informationen zur Einrichtung finden Sie unter [Vorbereiten](https://msdn.microsoft.com/library/windows/apps/Dn726766).</span><span class="sxs-lookup"><span data-stu-id="40ba5-116">For more information about getting setup, see, [Get set up](https://msdn.microsoft.com/library/windows/apps/Dn726766)</span></span>

<span data-ttu-id="40ba5-117">Wenn Sie zum Testen anstelle des vorhandenen Windows10 Mobile-Emulators optional ein echtes Windows10 Mobile-Gerät verwenden möchten, benötigen Sie außerdem Folgendes:</span><span class="sxs-lookup"><span data-stu-id="40ba5-117">Optionally, if you want to test with a real Windows 10 Mobile device instead of the included Windows 10 Mobile emulator, you will also need the following items.</span></span>

-   <span data-ttu-id="40ba5-118">Windows10 Mobile-Gerät mit NFC-HCE-Unterstützung.</span><span class="sxs-lookup"><span data-stu-id="40ba5-118">A Windows 10 Mobile device with NFC HCE support.</span></span> <span data-ttu-id="40ba5-119">Derzeit verfügen das Lumia730, 830, 640 und 640XL über die Hardware zur Unterstützung von NFC-HCE-Apps.</span><span class="sxs-lookup"><span data-stu-id="40ba5-119">Currently, the Lumia 730, 830, 640, and the 640 XL have the hardware to support NFC HCE apps.</span></span>
-   <span data-ttu-id="40ba5-120">Lesegeräteinheit, die die Protokolle ISO/IEC14443-4 und ISO/IEC7816-4 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="40ba5-120">A reader terminal that supports protocols ISO/IEC 14443-4 and ISO/IEC 7816-4</span></span>

<span data-ttu-id="40ba5-121">Windows10 Mobile implementiert einen HCE-Dienst mit den folgenden Funktionen:</span><span class="sxs-lookup"><span data-stu-id="40ba5-121">Windows 10 Mobile implements an HCE service that provides the following functionalities.</span></span>

-   <span data-ttu-id="40ba5-122">Apps können die Applet-IDs (AIDs) für die Karten registrieren, die emuliert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="40ba5-122">Apps can register the applet identifiers (AIDs) for the cards they would like to emulate.</span></span>
-   <span data-ttu-id="40ba5-123">Die Konfliktlösung und das Routing des Anwendungsprotokoll-Dateneinheit-Befehls (Application Protocol Data Unit, APDU) und der Antwort werden mit einer der registrierten Apps basierend auf der Auswahl des externen Kartenlesers und der Benutzereinstellung gekoppelt.</span><span class="sxs-lookup"><span data-stu-id="40ba5-123">Conflict resolution and routing of the Application Protocol Data Unit (APDU) command and response pairs to one of the registered apps based on the external reader card selection and user preference.</span></span>
-   <span data-ttu-id="40ba5-124">Behandlung der Ereignisse und Benachrichtigungen für die Apps als Ergebnis von Benutzeraktionen.</span><span class="sxs-lookup"><span data-stu-id="40ba5-124">Handling of events and notifications to the apps as a result of user actions.</span></span>

<span data-ttu-id="40ba5-125">Windows10 unterstützt die Emulation von Smartcards, die auf ISO-DEP (ISO-IEC14443-4) basieren, und kommuniziert über APDUs, die in der ISO-IEC7816-4-Spezifikation definiert sind.</span><span class="sxs-lookup"><span data-stu-id="40ba5-125">Windows 10 supports emulation of smart cards that are based on ISO-DEP (ISO-IEC 14443-4) and communicates using APDUs as defined in the ISO-IEC 7816-4 specification.</span></span> <span data-ttu-id="40ba5-126">Windows10 unterstützt für HCE-Apps die Technologie „ISO/IEC14443-4 TypA“.</span><span class="sxs-lookup"><span data-stu-id="40ba5-126">Windows 10 supports ISO/IEC 14443-4 Type A technology for HCE apps.</span></span> <span data-ttu-id="40ba5-127">Für Technologien wie TypB, TypF und Nicht-ISO-DEP (z.B. MIFARE) wird die Weiterleitung an die SIM standardmäßig durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="40ba5-127">Type B, type F, and non-ISO-DEP (eg MIFARE) technologies are routed to the SIM by default.</span></span>

<span data-ttu-id="40ba5-128">Die Kartenemulationsfunkton ist nur für Windows10 Mobile-Geräte aktiviert.</span><span class="sxs-lookup"><span data-stu-id="40ba5-128">Only Windows 10 Mobile devices are enabled with the card emulation feature.</span></span> <span data-ttu-id="40ba5-129">Die SIM-basierte und HCE-basierte Kartenemulation ist für andere Versionen von Windows10 nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="40ba5-129">SIM-based and HCE-based card emulation is not available on other versions of Windows 10.</span></span>

<span data-ttu-id="40ba5-130">Das folgende Diagramm zeigt die Architektur für die Unterstützung der HCE- und SIM-basierten Kartenemulation.</span><span class="sxs-lookup"><span data-stu-id="40ba5-130">The architecture for HCE and SIM based card emulation support is shown in the diagram below.</span></span>

![Architektur für die HCE- und SIM-Kartenemulation](./images/nfc-architecture.png)

## <a name="app-selection-and-aid-routing"></a><span data-ttu-id="40ba5-132">App-Auswahl und AID-Routing</span><span class="sxs-lookup"><span data-stu-id="40ba5-132">App selection and AID routing</span></span>

<span data-ttu-id="40ba5-133">Für die Entwicklung einer HCE-App müssen Sie wissen, wie bei Windows 10 Mobile-Geräten die Weiterleitung von AIDs an eine bestimmte App funktioniert, da Benutzer mehrere unterschiedliche HCE-Apps installieren können.</span><span class="sxs-lookup"><span data-stu-id="40ba5-133">To develop an HCE app, you must understand how Windows 10 Mobile devices route AIDs to a specific app because users can install multiple different HCE apps.</span></span> <span data-ttu-id="40ba5-134">Jede App kann mehrere HCE- und SIM-basierte Karten registrieren.</span><span class="sxs-lookup"><span data-stu-id="40ba5-134">Each app can register multiple HCE and SIM-based cards.</span></span> <span data-ttu-id="40ba5-135">Ältere SIM-basierte Windows Phone8.1-Apps funktionieren unter Windows10 Mobile weiterhin, solange der Benutzer im Menü mit den NFC-Einstellungen die Option „SIM-Karte“ als standardmäßige Zahlungskarte auswählt.</span><span class="sxs-lookup"><span data-stu-id="40ba5-135">Legacy Windows Phone 8.1 apps that are SIM-based will continue to work on Windows 10 Mobile as long as the user chooses the "SIM Card" option as their default payment card in the NFC Setting menu.</span></span> <span data-ttu-id="40ba5-136">Diese Standardeinstellung wird festgelegt, wenn das Gerät zum ersten Mal eingeschaltet wird.</span><span class="sxs-lookup"><span data-stu-id="40ba5-136">This is set by default when turning the device on for the first time.</span></span>

<span data-ttu-id="40ba5-137">Wenn Benutzer mit ihrem Windows10 Mobile-Gerät ein Terminal berühren, werden die Daten automatisch an die richtige auf dem Gerät installierte App geleitet.</span><span class="sxs-lookup"><span data-stu-id="40ba5-137">When the user taps their Windows 10 Mobile device to a terminal, the data is automatically routed to the proper app installed on the device.</span></span> <span data-ttu-id="40ba5-138">Diese Weiterleitung basiert auf den Applet-IDs (AIDs), bei denen es sich um Bezeichner mit 5-16Byte handelt.</span><span class="sxs-lookup"><span data-stu-id="40ba5-138">This routing is based on the applet IDs (AIDs) which are 5-16 byte identifiers.</span></span> <span data-ttu-id="40ba5-139">Während dieses Vorgangs überträgt das externe Terminal eine SELECT-Befehl-APDU, um die AID anzugeben, an die alle nachfolgenden APDU-Befehle geleitet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="40ba5-139">During a tap, the external terminal will transmit a SELECT command APDU to specify the AID it would like all subsequent APDU commands to be routed to.</span></span> <span data-ttu-id="40ba5-140">Mit den nachfolgenden SELECT-Befehlen wird die Weiterleitung wieder geändert.</span><span class="sxs-lookup"><span data-stu-id="40ba5-140">Subsequent SELECT commands, will change the routing again.</span></span> <span data-ttu-id="40ba5-141">Basierend auf den von Apps registrierten AIDs und den Benutzereinstellungen wird der APDU-Datenverkehr an eine bestimmte App geleitet, die dann eine APDU als Antwort sendet.</span><span class="sxs-lookup"><span data-stu-id="40ba5-141">Based on the AIDs registered by apps and user settings, the APDU traffic is routed to a specific app, which will send a response APDU.</span></span> <span data-ttu-id="40ba5-142">Beachten Sie hierbei, dass ein Terminal während eines Vorgangs unter Umständen versucht, mit mehreren unterschiedlichen Apps zu kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="40ba5-142">Be aware that a terminal may want to communicate with several different apps during the same tap.</span></span> <span data-ttu-id="40ba5-143">Sie müssen also sicherstellen, dass die Hintergrundaufgabe Ihrer App nach der Deaktivierung so schnell wie möglich beendet wird, damit die Hintergrundaufgabe einer anderen App auf die APDU antworten kann.</span><span class="sxs-lookup"><span data-stu-id="40ba5-143">So you must ensure your app's background task exits as quickly as possible when deactivated to make room for another app's background task to respond to the APDU.</span></span> <span data-ttu-id="40ba5-144">Hintergrundaufgaben werden später in diesem Thema beschrieben.</span><span class="sxs-lookup"><span data-stu-id="40ba5-144">We will discuss background tasks later in this topic.</span></span>

<span data-ttu-id="40ba5-145">HCE-Apps müssen sich mit bestimmten AIDs registrieren, die sie verarbeiten können, damit sie APDUs für eine AID erhalten.</span><span class="sxs-lookup"><span data-stu-id="40ba5-145">HCE apps must register themselves with particular AIDs they can handle so they will receive APDUs for an AID.</span></span> <span data-ttu-id="40ba5-146">Apps deklarieren AIDs über AID-Gruppen.</span><span class="sxs-lookup"><span data-stu-id="40ba5-146">Apps decalre AIDs by using AID groups.</span></span> <span data-ttu-id="40ba5-147">Eine AID-Gruppe entspricht vom Konzept her einer individuellen physischen Karte.</span><span class="sxs-lookup"><span data-stu-id="40ba5-147">An AID group is conceptually equivalent to an individual physical card.</span></span> <span data-ttu-id="40ba5-148">Beispielsweise wird eine Kreditkarte mit einer AID-Gruppe deklariert, und eine zweite Kreditkarte einer anderen Bank wird mit einer anderen zweiten AID-Gruppe deklariert, auch wenn beide unter Umständen über die gleiche AID verfügen.</span><span class="sxs-lookup"><span data-stu-id="40ba5-148">For example, one credit card is declared with an AID group and a second credit card from a different bank is declared with a different, second AID group, even though both of them may have the same AID.</span></span>

## <a name="conflict-resolution-for-payment-aid-groups"></a><span data-ttu-id="40ba5-149">Konfliktlösung für AID-Gruppen für die Zahlung</span><span class="sxs-lookup"><span data-stu-id="40ba5-149">Conflict resolution for payment AID groups</span></span>

<span data-ttu-id="40ba5-150">Wenn eine App physische Karten (AID-Gruppen) registriert, kann sie die AID-Gruppenkategorie entweder als „Payment“ (Zahlung) oder „Other“ (Sonstiges) deklarieren.</span><span class="sxs-lookup"><span data-stu-id="40ba5-150">When an app registers physical cards (AID groups), it can declare the AID group category as either "Payment" or "Other."</span></span> <span data-ttu-id="40ba5-151">Es können zwar mehrere AID-Zahlungsgruppen gleichzeitig registriert sein, aber nur jeweils eine dieser AID-Zahlungsgruppen kann für den Vorgang „Bezahlen per Berührung“ aktiviert sein. Die Auswahl erfolgt durch den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="40ba5-151">While there can be multiple payment AID groups registered at any given time, only one of these payment AID groups may be enabled for Tap and Pay at a time, which is selected by the user.</span></span> <span data-ttu-id="40ba5-152">Der Grund für dieses Verhalten ist, dass Benutzer bewusst auswählen möchten, welche Zahlungs-, Kredit- oder Debitkarte jeweils verwendet wird, damit der Bezahlvorgang nicht über eine unerwünschte Karte abgewickelt wird, wenn das Terminal mit dem Gerät berührt wird.</span><span class="sxs-lookup"><span data-stu-id="40ba5-152">This behavior exists because the user expects be in control of consciously choosing a single payment, credit, or debit card to use so they don't pay with a different unintended card when tapping their device to a terminal.</span></span>

<span data-ttu-id="40ba5-153">Gleichzeitig können aber mehrere AID-Gruppen, die unter „Other“ (Sonstiges) registriert sind, ohne Benutzerinteraktion aktiviert sein.</span><span class="sxs-lookup"><span data-stu-id="40ba5-153">However, multiple AID groups registered as "Other" can be enabled at the same time without user interaction.</span></span> <span data-ttu-id="40ba5-154">Dieses Verhalten ist vorhanden, weil für andere Arten von Karten (z.B. Treue-, Gutschein- oder Transit-Karten) erwartet wird, dass sie ohne jegliches Zutun oder Eingaben funktionieren, wenn das Terminal mit dem Smartphone berührt wird.</span><span class="sxs-lookup"><span data-stu-id="40ba5-154">This behavior exists because other types of cards like loyalty, coupons, or transit are expected to just work without any effort or prompting whenever they tap their phone.</span></span>

<span data-ttu-id="40ba5-155">Alle AID-Gruppen, die als „Payment“ (Zahlung) registriert sind, werden auf der Seite mit den NFC-Einstellungen in der Kartenliste angezeigt, sodass Benutzer ihre Standardkarte für Zahlungen auswählen können.</span><span class="sxs-lookup"><span data-stu-id="40ba5-155">All the AID groups that are registered as "Payment" appear in the list of cards in the NFC Settings page, where the user can select their default payment card.</span></span> <span data-ttu-id="40ba5-156">Wenn eine Standardkarte für Zahlungen ausgewählt wird, wird die App, mit der die jeweilige AID-Zahlungsgruppe registriert wurde, zur standardmäßigen App für Zahlungen.</span><span class="sxs-lookup"><span data-stu-id="40ba5-156">When a default payment card is selected, the app that registered this payment AID group becomes the default payment app.</span></span> <span data-ttu-id="40ba5-157">Standardmäßige Apps für Zahlungen können alle eigenen AID-Gruppen ohne Benutzerinteraktion aktivieren und deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="40ba5-157">Default payment apps can enable or disable any of their AID groups without user interaction.</span></span> <span data-ttu-id="40ba5-158">Wenn der Benutzer die Aufforderung zum Wählen der standardmäßigen App für die Bezahlung ablehnt, wird die derzeit als Standard-App ausgewählte App (falls vorhanden) weiter als Standardeinstellung verwendet.</span><span class="sxs-lookup"><span data-stu-id="40ba5-158">If the user declines the default payment app prompt, then the current default payment app (if any) continues to remain as default.</span></span> <span data-ttu-id="40ba5-159">Im folgenden Screenshot ist die Seite mit den NFC-Einstellungen dargestellt.</span><span class="sxs-lookup"><span data-stu-id="40ba5-159">The following screenshot shows the NFC Settings page.</span></span>

![Screenshot der Seite mit NFC-Einstellungen](./images/nfc-settings.png)

<span data-ttu-id="40ba5-161">Gemäß dem obigen Beispiel-Screenshot: Wenn der Benutzer seine Standardkarte für Zahlungen in eine andere Karte ändert, die nicht von „HCE Application1“ registriert wurde, erstellt das System eine Bestätigungsaufforderung, damit der Benutzer seine Zustimmung geben kann.</span><span class="sxs-lookup"><span data-stu-id="40ba5-161">Using the example screenshot above, if the user changes his default payment card to another card that is not registered by "HCE Application 1," the system creates a confirmation prompt for the user’s consent.</span></span> <span data-ttu-id="40ba5-162">Falls der Benutzer seine Standardkarte für Zahlungen aber in eine andere Karte ändert, die von „HCE Application1“ registriert wurde, erstellt das System keine Bestätigungsaufforderung für den Benutzer, weil „HCE Application1“ bereits die Standard-App für Zahlungen ist.</span><span class="sxs-lookup"><span data-stu-id="40ba5-162">However, if the user changes his default payment card to another card that is registered by "HCE Application 1," the system does not create a confirmation prompt for the user, because "HCE Application1" is already the default payment app.</span></span>

## <a name="conflict-resolution-for-non-payment-aid-groups"></a><span data-ttu-id="40ba5-163">Konfliktlösung für andere AID-Gruppen</span><span class="sxs-lookup"><span data-stu-id="40ba5-163">Conflict resolution for non-payment AID groups</span></span>

<span data-ttu-id="40ba5-164">Karten, die nicht für die Bezahlung bestimmt und in der Kategorie „Other“ (Sonstiges) enthalten sind, werden nicht auf der Seite mit den NFC-Einstellungen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="40ba5-164">Non-payment cards categorized as "Other" do not appear in the NFC settings page.</span></span>

<span data-ttu-id="40ba5-165">In Ihrer App können nicht für die Bezahlung bestimmte AID-Gruppen genauso wie AID-Zahlungsgruppen erstellt, registriert und aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="40ba5-165">Your app can create, register and enable non-payment AID groups in the same manner as payment AID groups.</span></span> <span data-ttu-id="40ba5-166">Der Hauptunterschied besteht darin, dass die Emulationskategorie für nicht für die Bezahlung bestimmte AID-Gruppen auf „Other“ (Sonstiges) festgelegt ist und nicht auf „Payment“ (Zahlung).</span><span class="sxs-lookup"><span data-stu-id="40ba5-166">The main difference is that for non-payment AID groups the emulation category is set to "Other" as opposed to "Payment".</span></span> <span data-ttu-id="40ba5-167">Nach dem Registrieren der AID-Gruppe im System müssen Sie die AID-Gruppe aktivieren, damit NFC-Datenverkehr empfangen werden kann.</span><span class="sxs-lookup"><span data-stu-id="40ba5-167">After registering the AID group with the system, you need to enable the AID group to receive NFC traffic.</span></span> <span data-ttu-id="40ba5-168">Wenn Sie versuchen, eine nicht für die Bezahlung bestimmte AID-Gruppe für den Empfang von Datenverkehr zu aktivieren, wird dem Benutzer keine Bestätigungsaufforderung angezeigt. Dies ist nur der Fall, wenn ein Konflikt mit einer der AIDs besteht, die von einer anderen App bereits im System registriert wurden.</span><span class="sxs-lookup"><span data-stu-id="40ba5-168">When you try to enable a non-payment AID group to receive traffic, the user is not prompted for a confirmation unless there is a conflict with one of the AIDs already registered in the system by a different app.</span></span> <span data-ttu-id="40ba5-169">Wenn ein Konflikt besteht, werden dem Benutzer Informationen dazu angezeigt, welche Karte und die dazugehörige App deaktiviert werden, wenn der Benutzer die neu registrierte AID-Gruppe aktiviert.</span><span class="sxs-lookup"><span data-stu-id="40ba5-169">If there is a conflict, the user will be prompted with information about which card and it's associated app will be disabled if the user chooses to enable the newly registered AID group.</span></span>

**<span data-ttu-id="40ba5-170">Koexistenz mit SIM-basierten NFC-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="40ba5-170">Coexistence with SIM based NFC applications</span></span>**

<span data-ttu-id="40ba5-171">In Windows10 Mobile richtet das System die NFC-Controller-Routingtabelle ein, die zum Treffen von Routingentscheidungen auf Controllerebene verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="40ba5-171">In Windows 10 Mobile, the system sets up the NFC controller routing table that is used to make routing decisions at the controller layer.</span></span> <span data-ttu-id="40ba5-172">Die Tabelle enthält Routinginformationen für die folgenden Elemente:</span><span class="sxs-lookup"><span data-stu-id="40ba5-172">The table contains routing information for the following items.</span></span>

-   <span data-ttu-id="40ba5-173">Einzelne AID-Routen</span><span class="sxs-lookup"><span data-stu-id="40ba5-173">Individual AID routes.</span></span>
-   <span data-ttu-id="40ba5-174">Protokollbasierte Route (ISO-DEP)</span><span class="sxs-lookup"><span data-stu-id="40ba5-174">Protocol based route (ISO-DEP).</span></span>
-   <span data-ttu-id="40ba5-175">Technologiebasiertes Routing (NFC-A/B/F)</span><span class="sxs-lookup"><span data-stu-id="40ba5-175">Technology based routing (NFC-A/B/F).</span></span>

<span data-ttu-id="40ba5-176">Wenn eine externe Leseeinheit den Befehl „SELECT AID” sendet, überprüft der NFC-Controller zuerst die AID-Routen in der Routingtabelle auf eine Übereinstimmung.</span><span class="sxs-lookup"><span data-stu-id="40ba5-176">When an external reader sends a "SELECT AID" command, the NFC controller first checks AID routes in the routing table for a match.</span></span> <span data-ttu-id="40ba5-177">Falls keine Übereinstimmung vorhanden ist, wird die protokollbasierte Route als Standardroute für ISO-DEP (14443-4-A)-Datenverkehr verwendet.</span><span class="sxs-lookup"><span data-stu-id="40ba5-177">If there is no match, it will use the protocol-based route as the default route for ISO-DEP (14443-4-A) traffic.</span></span> <span data-ttu-id="40ba5-178">Für anderen Datenverkehr, der nicht auf ISO-DEP basiert, wird das technologiebasierte Routing verwendet.</span><span class="sxs-lookup"><span data-stu-id="40ba5-178">For any other non-ISO-DEP traffic it will use the technology based routing.</span></span>

<span data-ttu-id="40ba5-179">Windows10 Mobile enthält auf der Seite mit den NFC-Einstellungen die Menüoption „SIM-Karte“, damit weiterhin ältere SIM-basierte Windows Phone8.1-Apps genutzt werden können, bei denen die AIDs nicht im System registriert werden.</span><span class="sxs-lookup"><span data-stu-id="40ba5-179">Windows 10 Mobile provides a menu option "SIM Card" in the NFC Settings page to continue to use legacy Windows Phone 8.1 SIM-based apps, which do not register their AIDs with the system.</span></span> <span data-ttu-id="40ba5-180">Wenn Benutzer „SIM-Karte“ als Standardkarte für Zahlungen auswählen, wird die ISO-DEP-Route auf „UICC“ festgelegt. Für alle anderen Auswahlmöglichkeiten im Dropdownmenü verläuft die ISO-DEP-Route zum Host.</span><span class="sxs-lookup"><span data-stu-id="40ba5-180">If the user selects "SIM card" as their default payment card, then the ISO-DEP route is set to UICC, for all other selections in the drop-down menu the ISO-DEP route is to the host.</span></span>

<span data-ttu-id="40ba5-181">Die ISO-DEP-Route wird für Geräte auf „SIM-Karte“ festgelegt, die über eine SE-fähige SIM-Karte verfügen, wenn das Gerät zum ersten Mal mit Windows10 Mobile gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="40ba5-181">The ISO-DEP route is set to "SIM Card" for devices that have an SE enabled SIM card when the device is booted for the first time with Windows 10 Mobile.</span></span> <span data-ttu-id="40ba5-182">Wenn der Benutzer eine HCE-fähige App installiert und diese App HCE-AID-Gruppenregistrierungen aktiviert, zeigt die ISO-DEP-Route auf den Host.</span><span class="sxs-lookup"><span data-stu-id="40ba5-182">When the user installs an HCE enabled app and that app enables any HCE AID group registrations, the ISO-DEP route will be pointed to the host.</span></span> <span data-ttu-id="40ba5-183">Für neue SIM-basierte Anwendungen müssen die AIDs auf der SIM-Karte registriert werden, damit die jeweiligen AID-Routen in die Routingtabelle des Controllers eingefügt werden können.</span><span class="sxs-lookup"><span data-stu-id="40ba5-183">New SIM-based applications need to register the AIDs in the SIM in order for the specific AID routes to be populated in the controller routing table.</span></span>

## <a name="creating-an-hce-based-app"></a><span data-ttu-id="40ba5-184">Erstellen einer HCE-basierten App</span><span class="sxs-lookup"><span data-stu-id="40ba5-184">Creating an HCE based app</span></span>

<span data-ttu-id="40ba5-185">Ihre HCE-App besteht aus zwei Teilen:</span><span class="sxs-lookup"><span data-stu-id="40ba5-185">Your HCE app has two parts.</span></span>

-   <span data-ttu-id="40ba5-186">Vordergrund-App für die Benutzerinteraktion</span><span class="sxs-lookup"><span data-stu-id="40ba5-186">The main foreground app for the user interaction.</span></span>
-   <span data-ttu-id="40ba5-187">Hintergrundaufgabe, die vom System zum Verarbeiten von APDUs für eine bestimmte AID ausgelöst wird</span><span class="sxs-lookup"><span data-stu-id="40ba5-187">A background task that is triggered by the system to process APDUs for a given AID.</span></span>

<span data-ttu-id="40ba5-188">Aufgrund der extrem hohen Leistungsanforderungen in Bezug auf das Laden der Hintergrundaufgabe als Antwort auf eine NFC-Berührung ist es ratsam, die gesamte Hintergrundaufgabe in systemeigenem C++/CX-Code zu implementieren (einschließlich aller erforderlichen Abhängigkeiten, Verweise oder Bibliotheken), anstatt in C# oder verwaltetem Code.</span><span class="sxs-lookup"><span data-stu-id="40ba5-188">Because of the extremely tight performance requirements for loading your background task in response to an NFC tap, we recommend that your entire background task be implementing in C++/CX native code (including any dependencies, references, or libraries you depend on) rather than C# or managed code.</span></span> <span data-ttu-id="40ba5-189">C# und verwalteter Code bieten zwar normalerweise eine gute Leistung, aber es fällt auch Mehraufwand an, z.B. beim Laden von .NET CLR, der durch die Verwendung von C++/CX vermieden werden kann.</span><span class="sxs-lookup"><span data-stu-id="40ba5-189">While C# and managed code normally performs well, there is overhead, like loading the .NET CLR, that can be avoided by writing it in C++/CX.</span></span>
## <a name="create-and-register-your-background-task"></a><span data-ttu-id="40ba5-190">Erstellen und Registrieren einer Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="40ba5-190">Create and register your background task</span></span>

<span data-ttu-id="40ba5-191">Sie müssen in Ihrer HCE-App eine Hintergrundaufgabe für die Verarbeitung und Beantwortung von APDUs erstellen, die vom System weitergeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="40ba5-191">You need to create a background task in your HCE app for processing and responding to APDUs routed to it by the system.</span></span> <span data-ttu-id="40ba5-192">Beim ersten Starten Ihrer App wird im Vordergrund eine HCE-Hintergrundaufgabe registriert, mit der die [**IBackgroundTaskRegistration**](https://msdn.microsoft.com/library/windows/apps/BR224803)-Schnittstelle implementiert wird, wie im folgenden Code gezeigt.</span><span class="sxs-lookup"><span data-stu-id="40ba5-192">During the first time your app is launched, the foreground registers an HCE background task that implements the [**IBackgroundTaskRegistration**](https://msdn.microsoft.com/library/windows/apps/BR224803) interface as shown in the following code.</span></span>

```csharp
var taskBuilder = new BackgroundTaskBuilder();
taskBuilder.Name = bgTaskName;
taskBuilder.TaskEntryPoint = taskEntryPoint;
taskBuilder.SetTrigger(new SmartCardTrigger(SmartCardTriggerType.EmulatorHostApplicationActivated));
bgTask = taskBuilder.Register();
```

<span data-ttu-id="40ba5-193">Beachten Sie, dass der Aufgabentrigger auf [**SmartCardTriggerType**](https://msdn.microsoft.com/library/windows/apps/Dn608017) festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="40ba5-193">Notice that the task trigger is set to [**SmartCardTriggerType**](https://msdn.microsoft.com/library/windows/apps/Dn608017).</span></span> <span data-ttu-id="40ba5-194">**EmulatorHostApplicationActivated**.</span><span class="sxs-lookup"><span data-stu-id="40ba5-194">**EmulatorHostApplicationActivated**.</span></span> <span data-ttu-id="40ba5-195">Dies bedeutet Folgendes: Wenn vom Betriebssystem die APDU eines SELECT AID-Befehls empfangen und für Ihre App aufgelöst wird, wird Ihre Hintergrundaufgabe gestartet.</span><span class="sxs-lookup"><span data-stu-id="40ba5-195">This means that whenever a SELECT AID command APDU is received by the OS resolving to your app, your background task will be launched.</span></span>

## <a name="receive-and-respond-to-apdus"></a><span data-ttu-id="40ba5-196">Empfangen und Beantworten von APDUs</span><span class="sxs-lookup"><span data-stu-id="40ba5-196">Receive and respond to APDUs</span></span>

<span data-ttu-id="40ba5-197">Wenn eine für Ihre App bestimmte APDU vorhanden ist, startet das System Ihre Hintergrundaufgabe.</span><span class="sxs-lookup"><span data-stu-id="40ba5-197">When there is an APDU targeted for your app, the system will launch your background task.</span></span> <span data-ttu-id="40ba5-198">Ihre Hintergrundaufgabe empfängt die APDU, die über die [**CommandApdu**](https://msdn.microsoft.com/library/windows/apps/windows.devices.smartcards.smartcardemulatorapdureceivedeventargs.commandapdu.aspx)-Eigenschaft des [**SmartCardEmulatorApduReceivedEventArgs**](https://msdn.microsoft.com/library/windows/apps/Dn894640)-Objekts übergeben wird, und antwortet auf die APDU mit der [**TryRespondAsync**](https://msdn.microsoft.com/library/windows/apps/mt634299.aspx)-Methode desselben Objekts.</span><span class="sxs-lookup"><span data-stu-id="40ba5-198">Your background task receives the APDU passed through the [**SmartCardEmulatorApduReceivedEventArgs**](https://msdn.microsoft.com/library/windows/apps/Dn894640) object’s [**CommandApdu**](https://msdn.microsoft.com/library/windows/apps/windows.devices.smartcards.smartcardemulatorapdureceivedeventargs.commandapdu.aspx) property and responds to the APDU using the [**TryRespondAsync**](https://msdn.microsoft.com/library/windows/apps/mt634299.aspx) method of the same object.</span></span> <span data-ttu-id="40ba5-199">Erwägen Sie, die Hintergrundaufgabe aus Leistungsgründen für kleinere Vorgänge beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="40ba5-199">Consider keeping your background task for light operations for performance reasons.</span></span> <span data-ttu-id="40ba5-200">Beantworten Sie die APDUs beispielsweise sofort, und beenden Sie die Hintergrundaufgabe, wenn die gesamte Verarbeitung abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="40ba5-200">For example, respond to the APDUs immediately and exit your background task when all processing is complete.</span></span> <span data-ttu-id="40ba5-201">Aufgrund der Art von NFC-Transaktionen tendieren Benutzer dazu, ihr Gerät nur für einen sehr kurzen Zeitraum an die Leseeinheit zu halten.</span><span class="sxs-lookup"><span data-stu-id="40ba5-201">Due to the nature of NFC transactions, users tend to hold their device against the reader for only a very short amount of time.</span></span> <span data-ttu-id="40ba5-202">Die Hintergrundaufgabe empfängt weiter Datenverkehr von der Leseeinheit, bis die Verbindung deaktiviert wird. Sie erhalten dann ein [**SmartCardEmulatorConnectionDeactivatedEventArgs**](https://msdn.microsoft.com/library/windows/apps/Dn894644)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="40ba5-202">Your background task will continue to receive traffic from the reader until your connection is deactivated, in which case you will receive a [**SmartCardEmulatorConnectionDeactivatedEventArgs**](https://msdn.microsoft.com/library/windows/apps/Dn894644) object.</span></span> <span data-ttu-id="40ba5-203">Die Verbindung kann aus den folgenden Gründen deaktiviert werden, wie in der [**SmartCardEmulatorConnectionDeactivatedEventArgs.Reason**](https://msdn.microsoft.com/library/windows/apps/windows.devices.smartcards.smartcardemulatorconnectiondeactivatedeventargs.reason)-Eigenschaft angegeben.</span><span class="sxs-lookup"><span data-stu-id="40ba5-203">Your connection can be deactivated because of the following reasons as indicated in the [**SmartCardEmulatorConnectionDeactivatedEventArgs.Reason**](https://msdn.microsoft.com/library/windows/apps/windows.devices.smartcards.smartcardemulatorconnectiondeactivatedeventargs.reason) property.</span></span>

-   <span data-ttu-id="40ba5-204">Wenn die Verbindung mit dem **ConnectionLost**-Wert deaktiviert wird, bedeutet dies, dass der Benutzer das Gerät von der Leseeinheit entfernt hat.</span><span class="sxs-lookup"><span data-stu-id="40ba5-204">If the connection is deactivated with the **ConnectionLost** value, it means that the user pulled their device away from the reader.</span></span> <span data-ttu-id="40ba5-205">Falls Ihre App eine längere Berührung des Terminals erfordert, können Sie für den Benutzer entsprechendes Feedback anzeigen.</span><span class="sxs-lookup"><span data-stu-id="40ba5-205">If your app needs the user to tap to the terminal longer, you might want to consider prompting them with feedback.</span></span> <span data-ttu-id="40ba5-206">Beenden Sie die Hintergrundaufgabe schnell (per Abschluss der Verzögerung), um sicherzustellen, dass es bei der erneuten Berührung nicht zu einer Verzögerung kommt, weil auf die Beendigung der vorherigen Hintergrundaufgabe gewartet werden muss.</span><span class="sxs-lookup"><span data-stu-id="40ba5-206">You should terminate your background task quickly (by completing your deferral) to ensure if they tap again it won’t be delayed waiting for the previous background task to exit.</span></span>
-   <span data-ttu-id="40ba5-207">Wenn die Verbindung über **ConnectionRedirected** deaktiviert wird, bedeutet dies, dass vom Terminal eine neue SELECT AID-Befehl-APDU für eine andere AID gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="40ba5-207">If the connection is deactivated with the **ConnectionRedirected**, it means that the terminal sent a new SELECT AID command APDU directed to a different AID.</span></span> <span data-ttu-id="40ba5-208">In diesem Fall sollte die App die Hintergrundaufgabe sofort beenden (per Abschluss der Verzögerung), um die Ausführung einer anderen Hintergrundaufgabe zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="40ba5-208">In this case, your app should exit the background task immediately (by completing your deferral) to allow another background task to run.</span></span>

<span data-ttu-id="40ba5-209">Außerdem sollte die Hintergrundaufgabe für das [**Canceled-Ereignis**](https://msdn.microsoft.com/library/windows/apps/BR224798) unter [**IBackgroundTaskInstance interface**](https://msdn.microsoft.com/library/windows/apps/BR224797) registriert werden und auch hier wieder schnell beendet werden (per Abschluss der Verzögerung), da dieses Ereignis vom System ausgelöst wird, wenn die Verarbeitung der Hintergrundaufgabe abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="40ba5-209">The background task should also register for the [**Canceled event**](https://msdn.microsoft.com/library/windows/apps/BR224798) on [**IBackgroundTaskInstance interface**](https://msdn.microsoft.com/library/windows/apps/BR224797), and likewise quickly exit the background task (by completing your deferral) because this event is fired by the system when it is finished with your background task.</span></span> <span data-ttu-id="40ba5-210">Unten ist Code angegeben, mit dem eine Hintergrundaufgabe einer HCE-App veranschaulicht wird.</span><span class="sxs-lookup"><span data-stu-id="40ba5-210">Below is code that demonstrates an HCE app background task.</span></span>

```csharp
void BgTask::Run(
    IBackgroundTaskInstance^ taskInstance)
{
    m_triggerDetails = static_cast<SmartCardTriggerDetails^>(taskInstance->TriggerDetails);
    if (m_triggerDetails == nullptr)
    {
        // May be not a smart card event that triggered us
        return;
    }

    m_emulator = m_triggerDetails->Emulator;
    m_taskInstance = taskInstance;

    switch (m_triggerDetails->TriggerType)
    {
    case SmartCardTriggerType::EmulatorHostApplicationActivated:
        HandleHceActivation();
        break;

    case SmartCardTriggerType::EmulatorAppletIdGroupRegistrationChanged:
        HandleRegistrationChange();
        break;

    default:
        break;
    }
}

void BgTask::HandleHceActivation()
{
 try
 {
        auto lock = m_srwLock.LockShared();
        // Take a deferral to keep this background task alive even after this "Run" method returns
        // You must complete this deferal immediately after you have done processing the current transaction
        m_deferral = m_taskInstance->GetDeferral();

        DebugLog(L"*** HCE Activation Background Task Started ***");

        // Set up a handler for if the background task is cancelled, we must immediately complete our deferral
        m_taskInstance->Canceled += ref new Windows::ApplicationModel::Background::BackgroundTaskCanceledEventHandler(
            [this](
            IBackgroundTaskInstance^ sender,
            BackgroundTaskCancellationReason reason)
        {
            DebugLog(L"Cancelled");
            DebugLog(reason.ToString()->Data());
            EndTask();
        });

        if (Windows::Phone::System::SystemProtection::ScreenLocked)
        {
            auto denyIfLocked = Windows::Storage::ApplicationData::Current->RoamingSettings->Values->Lookup("DenyIfPhoneLocked");
            if (denyIfLocked != nullptr && (bool)denyIfLocked == true)
            {
                // The phone is locked, and our current user setting is to deny transactions while locked so let the user know
                // Denied
                DoLaunch(Denied, L"Phone was locked at the time of tap");

                // We still need to respond to APDUs in a timely manner, even though we will just return failure
                m_fDenyTransactions = true;
            }
        }
        else
        {
            m_fDenyTransactions = false;
        }

        m_emulator->ApduReceived += ref new TypedEventHandler<SmartCardEmulator^, SmartCardEmulatorApduReceivedEventArgs^>(
            this, &BgTask::ApduReceived);

        m_emulator->ConnectionDeactivated += ref new TypedEventHandler<SmartCardEmulator^, SmartCardEmulatorConnectionDeactivatedEventArgs^>(
                [this](
                SmartCardEmulator^ emulator,
                SmartCardEmulatorConnectionDeactivatedEventArgs^ eventArgs)
            {
                DebugLog(L"Connection deactivated");
                EndTask();
            });

  m_emulator->Start();
        DebugLog(L"Emulator started");
 }
 catch (Exception^ e)
 {
        DebugLog(("Exception in Run: " + e->ToString())->Data());
        EndTask();
 }
}
```
## <a name="create-and-register-aid-groups"></a><span data-ttu-id="40ba5-211">Erstellen und Registrieren von AID-Gruppen</span><span class="sxs-lookup"><span data-stu-id="40ba5-211">Create and register AID groups</span></span>

<span data-ttu-id="40ba5-212">Wenn beim ersten Starten der Anwendung die Karte bereitgestellt wird, erstellen und registrieren Sie AID-Gruppen im System.</span><span class="sxs-lookup"><span data-stu-id="40ba5-212">During the first launch of your application when the card is being provisioned, you will create and register AID groups with the system.</span></span> <span data-ttu-id="40ba5-213">Das System bestimmt die App, mit der eine externe Leseeinheit kommunizieren möchte. Die APDUs werden basierend auf den registrierten AIDs und Benutzereinstellungen weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="40ba5-213">The system determines the app that an external reader would like to talk to and route APDUs accordingly based on the registered AIDs and user settings.</span></span>

<span data-ttu-id="40ba5-214">Die meisten Zahlungskarten werden für die gleiche AID (PPSE AID) und für weitere spezielle AIDs für Zahlungsnetzwerke registriert.</span><span class="sxs-lookup"><span data-stu-id="40ba5-214">Most of the payment cards register for the same AID (which is PPSE AID) along with additional payment network card specific AIDs.</span></span> <span data-ttu-id="40ba5-215">Jede AID-Gruppe steht für eine Karte, und wenn Benutzer die Karte aktivieren, werden alle AIDs der Gruppe aktiviert.</span><span class="sxs-lookup"><span data-stu-id="40ba5-215">Each AID group represents a card and when the user enables the card, all AIDs in the group are enabled.</span></span> <span data-ttu-id="40ba5-216">Ebenso werden alle AIDs der Gruppe deaktiviert, wenn der Benutzer die Karte deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="40ba5-216">Similarly, when the user deactivates the card, all AIDs in the group are disabled.</span></span>

<span data-ttu-id="40ba5-217">Zum Registrieren einer AID-Gruppe müssen Sie ein [**SmartCardAppletIdGroup**](https://msdn.microsoft.com/library/windows/apps/Dn910955)-Objekt erstellen und dessen Eigenschaften so festlegen, dass angegeben wird, dass es sich um eine HCE-basierte Zahlungskarte handelt.</span><span class="sxs-lookup"><span data-stu-id="40ba5-217">To register an AID group, you need to create a [**SmartCardAppletIdGroup**](https://msdn.microsoft.com/library/windows/apps/Dn910955) object and set its properties to reflect that this is an HCE-based payment card.</span></span> <span data-ttu-id="40ba5-218">Ihr Anzeigename sollte für Benutzer aussagekräftig sein, da er im Menü mit den NFC-Einstellungen und in Eingabeaufforderungen angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="40ba5-218">Your display name should be descriptive to the user because it will show up in the NFC settings menu as well as user prompts.</span></span> <span data-ttu-id="40ba5-219">Für HCE-Zahlungskarten sollte die [**SmartCardEmulationCategory**](https://msdn.microsoft.com/library/windows/apps/windows.devices.smartcards.smartcardappletidgroup.smartcardemulationcategory.aspx)-Eigenschaft auf **Payment** und die [**SmartCardEmulationType**](https://msdn.microsoft.com/library/windows/apps/windows.devices.smartcards.smartcardappletidgroup.smartcardemulationtype)-Eigenschaft auf **Host** festgelegt sein.</span><span class="sxs-lookup"><span data-stu-id="40ba5-219">For HCE payment cards, the [**SmartCardEmulationCategory**](https://msdn.microsoft.com/library/windows/apps/windows.devices.smartcards.smartcardappletidgroup.smartcardemulationcategory.aspx) property should be set to **Payment** and the [**SmartCardEmulationType**](https://msdn.microsoft.com/library/windows/apps/windows.devices.smartcards.smartcardappletidgroup.smartcardemulationtype) property should be set to **Host**.</span></span>

```csharp
public static byte[] AID_PPSE =
        {
            // File name "2PAY.SYS.DDF01" (14 bytes)
            (byte)'2', (byte)'P', (byte)'A', (byte)'Y',
            (byte)'.', (byte)'S', (byte)'Y', (byte)'S',
            (byte)'.', (byte)'D', (byte)'D', (byte)'F', (byte)'0', (byte)'1'
        };

var appletIdGroup = new SmartCardAppletIdGroup(
                        "Example DisplayName",
                                new List<IBuffer> {AID_PPSE.AsBuffer()},
                                SmartCardEmulationCategory.Payment,
                                SmartCardEmulationType.Host);
```

<span data-ttu-id="40ba5-220">Für nicht für die Zahlung bestimmte HCE-Karten sollte die [**SmartCardEmulationCategory**](https://msdn.microsoft.com/library/windows/apps/windows.devices.smartcards.smartcardappletidgroup.smartcardemulationcategory.aspx)-Eigenschaft auf **Other** und die [**SmartCardEmulationType**](https://msdn.microsoft.com/library/windows/apps/windows.devices.smartcards.smartcardappletidgroup.smartcardemulationtype)-Eigenschaft auf **Host** festgelegt sein.</span><span class="sxs-lookup"><span data-stu-id="40ba5-220">For non-payment HCE cards, the [**SmartCardEmulationCategory**](https://msdn.microsoft.com/library/windows/apps/windows.devices.smartcards.smartcardappletidgroup.smartcardemulationcategory.aspx) property should be set to **Other** and the [**SmartCardEmulationType**](https://msdn.microsoft.com/library/windows/apps/windows.devices.smartcards.smartcardappletidgroup.smartcardemulationtype) property should be set to **Host**.</span></span>

```csharp
public static byte[] AID_OTHER =
        {
            (byte)'1', (byte)'2', (byte)'3', (byte)'4',
            (byte)'5', (byte)'6', (byte)'7', (byte)'8',
            (byte)'O', (byte)'T', (byte)'H', (byte)'E', (byte)'R'
        };

var appletIdGroup = new SmartCardAppletIdGroup(
                        "Example DisplayName",
                                new List<IBuffer> {AID_OTHER.AsBuffer()},
                                SmartCardEmulationCategory.Other,
                                SmartCardEmulationType.Host);
```

<span data-ttu-id="40ba5-221">Sie können bis zu neun AIDs (jeweils mit einer Länge von 5bis 16Byte) pro AID-Gruppe verwenden.</span><span class="sxs-lookup"><span data-stu-id="40ba5-221">You can include up to 9 AIDs (of length 5-16 bytes each) per AID group.</span></span>

<span data-ttu-id="40ba5-222">Verwenden Sie die [**RegisterAppletIdGroupAsync**](https://msdn.microsoft.com/library/windows/apps/Dn894656)-Methode, um Ihre AID-Gruppe im System zu registrieren. Es wird dann ein [**SmartCardAppletIdGroupRegistration**](https://docs.microsoft.com/en-us/uwp/api/windows.devices.smartcards.smartcardappletidgroupregistration)-Objekt zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="40ba5-222">Use the [**RegisterAppletIdGroupAsync**](https://msdn.microsoft.com/library/windows/apps/Dn894656) method to register your AID group with the system, which will return a [**SmartCardAppletIdGroupRegistration**](https://docs.microsoft.com/en-us/uwp/api/windows.devices.smartcards.smartcardappletidgroupregistration) object.</span></span> <span data-ttu-id="40ba5-223">Standardmäßig ist die [**ActivationPolicy**](https://docs.microsoft.com/en-us/uwp/api/windows.devices.smartcards.smartcardappletidgroupregistration)-Eigenschaft des Registrierungsobjekts auf **Disabled** festgelegt.</span><span class="sxs-lookup"><span data-stu-id="40ba5-223">By default, the [**ActivationPolicy**](https://docs.microsoft.com/en-us/uwp/api/windows.devices.smartcards.smartcardappletidgroupregistration) property of the registration object is set to **Disabled**.</span></span> <span data-ttu-id="40ba5-224">Dies bedeutet, dass Ihre AIDs im System zwar registriert sind, aber sie sind noch nicht aktiviert und empfangen auch keinen Datenverkehr.</span><span class="sxs-lookup"><span data-stu-id="40ba5-224">This means even though your AIDs are registered with the system, they are not enabled yet and won’t receive traffic.</span></span>

```csharp
reg = await SmartCardEmulator.RegisterAppletIdGroupAsync(appletIdGroup);
```

<span data-ttu-id="40ba5-225">Sie können Ihre registrierten Karten (AID-Gruppen) aktivieren, indem Sie die [**RequestActivationPolicyChangeAsync**](https://docs.microsoft.com/en-us/uwp/api/windows.devices.smartcards.smartcardappletidgroupregistration)-Methode der [**SmartCardAppletIdGroupRegistration**](https://docs.microsoft.com/en-us/uwp/api/windows.devices.smartcards.smartcardappletidgroupregistration)-Klasse wie unten gezeigt verwenden.</span><span class="sxs-lookup"><span data-stu-id="40ba5-225">You can enable your registered cards (AID groups) by using the [**RequestActivationPolicyChangeAsync**](https://docs.microsoft.com/en-us/uwp/api/windows.devices.smartcards.smartcardappletidgroupregistration) method of the[**SmartCardAppletIdGroupRegistration**](https://docs.microsoft.com/en-us/uwp/api/windows.devices.smartcards.smartcardappletidgroupregistration) class as shown below.</span></span> <span data-ttu-id="40ba5-226">Da im System jeweils nur eine Zahlungskarte aktiviert sein kann, entspricht das Festlegen von [**ActivationPolicy**](https://docs.microsoft.com/en-us/uwp/api/windows.devices.smartcards.smartcardappletidgroupregistration) für eine AID-Zahlungsgruppe auf **Enabled** dem Festlegen als Standardkarte für die Zahlung.</span><span class="sxs-lookup"><span data-stu-id="40ba5-226">Because only a single payment card can be enabled at a time on the system, setting the [**ActivationPolicy**](https://docs.microsoft.com/en-us/uwp/api/windows.devices.smartcards.smartcardappletidgroupregistration) of a payment AID group to **Enabled** is the same as setting the default payment card.</span></span> <span data-ttu-id="40ba5-227">Benutzer werden aufgefordert, diese Karte unabhängig davon als Standardkarte für die Bezahlung zuzulassen, ob bereits eine Standardkarte für die Bezahlung ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="40ba5-227">The user will be prompted to allow this card as a default payment card, regardless of whether there is a default payment card already selected or not.</span></span> <span data-ttu-id="40ba5-228">Diese Aussage trifft nicht zu, wenn Ihre App bereits die Standardanwendung für Zahlungen ist und lediglich ein Wechsel der eigenen AID-Gruppen durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="40ba5-228">This statement is not true if your app is already the default payment application, and is merely changing between it’s own AID groups.</span></span> <span data-ttu-id="40ba5-229">Sie können bis zu zehn AID-Gruppen pro App registrieren.</span><span class="sxs-lookup"><span data-stu-id="40ba5-229">You can register up to 10 AID groups per app.</span></span>

```csharp
reg.RequestActivationPolicyChangeAsync(AppletIdGroupActivationPolicy.Enabled);
```

<span data-ttu-id="40ba5-230">Sie können die von Ihrer App beim Betriebssystem registrierten AID-Gruppen abfragen und deren Aktivierungsrichtlinie mit der [**GetAppletIdGroupRegistrationsAsync**](https://msdn.microsoft.com/library/windows/apps/Dn894654)-Methode überprüfen.</span><span class="sxs-lookup"><span data-stu-id="40ba5-230">You can query your app’s registered AID groups with the OS and check their activation policy using the [**GetAppletIdGroupRegistrationsAsync**](https://msdn.microsoft.com/library/windows/apps/Dn894654) method.</span></span>

<span data-ttu-id="40ba5-231">Benutzern wird nur dann eine Meldung angezeigt, wenn Sie die Aktivierungsrichtlinie einer Zahlungskarte von **Disabled** in **Enabled** ändern, sofern Ihre App nicht bereits die Standard-App für Zahlungen ist.</span><span class="sxs-lookup"><span data-stu-id="40ba5-231">Users will be prompted when you change the activation policy of a payment card from **Disabled** to **Enabled**, only if your app is not already the default payment app.</span></span> <span data-ttu-id="40ba5-232">Benutzern wird nur dann eine Meldung angezeigt, wenn Sie die Aktivierungsrichtlinie einer nicht für Zahlungen bestimmten Karte von **Disabled** in **Enabled** ändern, sofern ein AID-Konflikt vorliegt.</span><span class="sxs-lookup"><span data-stu-id="40ba5-232">Users will only be prompted when you change the activation policy of a non-payment card from **Disabled** to **Enabled** if there is an AID conflict.</span></span>

```csharp
var registrations = await SmartCardEmulator.GetAppletIdGroupRegistrationsAsync();
    foreach (var registration in registrations)
    {
registration.RequestActivationPolicyChangeAsync (AppletIdGroupActivationPolicy.Enabled);
    }
```

**<span data-ttu-id="40ba5-233">Ereignisbenachrichtigung bei Änderung der Aktivierungsrichtlinie</span><span class="sxs-lookup"><span data-stu-id="40ba5-233">Event notification when activation policy change</span></span>**

<span data-ttu-id="40ba5-234">In Ihrer Hintergrundaufgabe können Sie den Empfang von Ereignissen für den Fall einrichten, dass sich die Aktivierungsrichtlinie für eine Ihrer AID-Gruppenregistrierungen außerhalb der App ändert.</span><span class="sxs-lookup"><span data-stu-id="40ba5-234">In your background task, you can register to receive events for when the activation policy of one of your AID group registrations changes outside of your app.</span></span> <span data-ttu-id="40ba5-235">Es kann zum Beispiel sein, dass Benutzer die Standard-App für Zahlungen über das Menü mit den NFC-Einstellungen von einer Ihrer Karten in eine andere Karte ändern, die von einer anderen App gehostet wird.</span><span class="sxs-lookup"><span data-stu-id="40ba5-235">For example, the user may change the default payment app through the NFC settings menu from one of your cards to another card hosted by another app.</span></span> <span data-ttu-id="40ba5-236">Falls Ihre App aus Gründen des internen Setups, z.B. der Aktualisierung von Live-Kacheln, über diese Änderung informiert sein muss, können Sie Ereignisbenachrichtigungen über diese Änderung erhalten und in Ihrer App entsprechende Maßnahmen ergreifen.</span><span class="sxs-lookup"><span data-stu-id="40ba5-236">If your app needs to know about this change for internal setup such as updating live tiles, you can receive event notifications for this change and take action in your app accordingly.</span></span>

```csharp
var taskBuilder = new BackgroundTaskBuilder();
taskBuilder.Name = bgTaskName;
taskBuilder.TaskEntryPoint = taskEntryPoint;
taskBuilder.SetTrigger(new SmartCardTrigger(SmartCardTriggerType.EmulatorAppletIdGroupRegistrationChanged));
bgTask = taskBuilder.Register();
```

## <a name="foreground-override-behavior"></a><span data-ttu-id="40ba5-237">Außerkraftsetzung des Vordergrunds</span><span class="sxs-lookup"><span data-stu-id="40ba5-237">Foreground override behavior</span></span>

<span data-ttu-id="40ba5-238">Sie können die [**ActivationPolicy**](https://docs.microsoft.com/en-us/uwp/api/windows.devices.smartcards.smartcardappletidgroupregistration) für alle AID-Gruppenregistrierungen in **ForegroundOverride** ändern, während sich Ihre App im Vordergrund befindet, ohne Benutzern dies anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="40ba5-238">You can change the [**ActivationPolicy**](https://docs.microsoft.com/en-us/uwp/api/windows.devices.smartcards.smartcardappletidgroupregistration) of any of your AID group registrations to **ForegroundOverride** while your app is in the foreground without prompting the user.</span></span> <span data-ttu-id="40ba5-239">Wenn Benutzer mit ihrem Gerät ein Terminal berühren, während sich Ihre App im Vordergrund befindet, wird der Datenverkehr an Ihre App geleitet. Dies ist auch dann der Fall, wenn vom Benutzer keine Ihrer Zahlungskarten ausgewählt wurde.</span><span class="sxs-lookup"><span data-stu-id="40ba5-239">When the user taps their device to a terminal while your app is in the foreground, the traffic is routed to your app even if none of your payment cards were chosen by the user as their default payment card.</span></span> <span data-ttu-id="40ba5-240">Wenn Sie die Aktivierungsrichtlinie einer Karte in **ForegroundOverride** ändern, ist diese Änderung nur vorübergehend, bis sich Ihre App nicht mehr im Vordergrund befindet. Die aktuelle Standardkarte für Zahlungen, die vom Benutzer festgelegt wurde, ändert sich hierdurch nicht.</span><span class="sxs-lookup"><span data-stu-id="40ba5-240">When you change a card’s activation policy to **ForegroundOverride**, this change is only temporary until your app leaves the foreground and it will not change the current default payment card set by the user.</span></span> <span data-ttu-id="40ba5-241">Sie können die **ActivationPolicy** Ihrer Karten für Zahlungen oder andere Zwecke wie folgt über die App im Vordergrund ändern.</span><span class="sxs-lookup"><span data-stu-id="40ba5-241">You can change the **ActivationPolicy** of your payment or non-payment cards from your foreground app as follows.</span></span> <span data-ttu-id="40ba5-242">Beachten Sie, dass die [**RequestActivationPolicyChangeAsync**](https://docs.microsoft.com/en-us/uwp/api/windows.devices.smartcards.smartcardappletidgroupregistration)-Methode nur von einer App im Vordergrund aufgerufen werden kann, nicht von einer Hintergrundaufgabe.</span><span class="sxs-lookup"><span data-stu-id="40ba5-242">Note that the [**RequestActivationPolicyChangeAsync**](https://docs.microsoft.com/en-us/uwp/api/windows.devices.smartcards.smartcardappletidgroupregistration) method can only be called from a foreground app and cannot be called from a background task.</span></span>

```csharp
reg.RequestActivationPolicyChangeAsync(AppletIdGroupActivationPolicy.ForegroundOverride);
```

<span data-ttu-id="40ba5-243">Außerdem können Sie eine AID-Gruppe registrieren, die aus einer einzelnen AID mit Nulllänge besteht. Das System leitet dann alle APDUs unabhängig von der AID und einschließlich aller Befehls-APDUs weiter, die vor dem Empfang eines SELECT AID-Befehls gesendet wurden.</span><span class="sxs-lookup"><span data-stu-id="40ba5-243">Also, you can register an AID group consisting of a single 0-length AID which will cause the system to route all APDUs regardless of the AID and including any command APDUs sent before a SELECT AID command is received.</span></span> <span data-ttu-id="40ba5-244">Eine AID-Gruppe dieser Art funktioniert aber nur, während sich Ihre App im Vordergrund befindet, da sie nur auf **ForegroundOverride** festgelegt und nicht dauerhaft aktiviert werden kann.</span><span class="sxs-lookup"><span data-stu-id="40ba5-244">However, such an AID group only works while your app is in the foreground because it can only be set to **ForegroundOverride** and cannot be permanently enabled.</span></span> <span data-ttu-id="40ba5-245">Dieses Verfahren funktioniert außerdem sowohl für **Host**-Werte als auch für **UICC**-Werte der [**SmartCardEmulationType**](https://msdn.microsoft.com/library/windows/apps/Dn894639)-Enumeration, um den gesamten Datenverkehr entweder an Ihre HCE-Hintergrundaufgabe oder die SIM-Karte zu leiten.</span><span class="sxs-lookup"><span data-stu-id="40ba5-245">Also, this mechanism works both for **Host** and **UICC** values of the [**SmartCardEmulationType**](https://msdn.microsoft.com/library/windows/apps/Dn894639) enumeration to either route all traffic to your HCE background task, or to the SIM card.</span></span>

```csharp
public static byte[] AID_Foreground =
        {};

var appletIdGroup = new SmartCardAppletIdGroup(
                        "Example DisplayName",
                                new List<IBuffer> {AID_Foreground.AsBuffer()},
                                SmartCardEmulationCategory.Other,
                                SmartCardEmulationType.Host);
reg = await SmartCardEmulator.RegisterAppletIdGroupAsync(appletIdGroup);
reg.RequestActivationPolicyChangeAsync(AppletIdGroupActivationPolicy.ForegroundOverride);
```

## <a name="check-for-nfc-and-hce-support"></a><span data-ttu-id="40ba5-246">Überprüfen auf NFC- und HCE-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="40ba5-246">Check for NFC and HCE support</span></span>

<span data-ttu-id="40ba5-247">Ihre App sollte überprüfen, ob ein Gerät über NFC-Hardware verfügt und die Kartenemulationsfunktion und die Hostkartenemulation unterstützt, bevor diese Features dem Benutzer angeboten werden.</span><span class="sxs-lookup"><span data-stu-id="40ba5-247">Your app should check whether a device has NFC hardware, supports the card emulation feature, and supports host card emulation prior to offering such features to the user.</span></span>

<span data-ttu-id="40ba5-248">Die NFC-Smartcard-Emulationsfunktion wird nur unter Windows10 Mobile aktiviert. Daher kommt es zu Fehlern, wenn versucht wird, Smartcard-Emulator-APIs in anderen Versionen von Windows10 zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="40ba5-248">The NFC smart card emulation feature is only enabled on Windows 10 Mobile, so trying to use the smart card emulator APIs in any other versions of Windows 10, will cause errors.</span></span> <span data-ttu-id="40ba5-249">Sie können die Smartcard-API-Unterstützung im folgenden Codeausschnitt überprüfen.</span><span class="sxs-lookup"><span data-stu-id="40ba5-249">You can check for smart card API support in the following code snippet.</span></span>

```csharp
Windows.Foundation.Metadata.ApiInformation.IsTypePresent("Windows.Devices.SmartCards.SmartCardEmulator");
```

<span data-ttu-id="40ba5-250">Außerdem können Sie überprüfen, ob das Gerät über NFC-Hardware für eine Form der Kartenemulation verfügt, indem Sie ermitteln, ob die [**SmartCardEmulator.GetDefaultAsync**](https://msdn.microsoft.com/library/windows/apps/Dn608008)-Methode Null zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="40ba5-250">You can additionally check to see if the device has NFC hardware capable of some form of card emulation by checking if the [**SmartCardEmulator.GetDefaultAsync**](https://msdn.microsoft.com/library/windows/apps/Dn608008) method returns null.</span></span> <span data-ttu-id="40ba5-251">Wenn ja, wird die NFC-Kartenemulation auf dem Gerät nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="40ba5-251">If it does, then no NFC card emulation is supported on the device.</span></span>

```csharp
var smartcardemulator = await SmartCardEmulator.GetDefaultAsync();<
```

<span data-ttu-id="40ba5-252">Die Unterstützung für HCE- und AID-basiertes UICC-Routing ist nur auf neueren Geräten verfügbar, z.B. Lumia730, 830, 640 und 640XL.</span><span class="sxs-lookup"><span data-stu-id="40ba5-252">Support for HCE and AID-based UICC routing is only available on recently launched devices such as the Lumia 730, 830, 640, and 640 XL.</span></span> <span data-ttu-id="40ba5-253">Alle neuen NFC-fähigen Geräte, auf denen Windows10 Mobile oder höher ausgeführt wird, verfügen normalerweise über Unterstützung für HCE.</span><span class="sxs-lookup"><span data-stu-id="40ba5-253">Any new NFC capable devices running Windows 10 Mobile and after should support HCE.</span></span> <span data-ttu-id="40ba5-254">Ihre App kann die HCE-Unterstützung wie folgt überprüfen.</span><span class="sxs-lookup"><span data-stu-id="40ba5-254">Your app can check for HCE support as follows.</span></span>

```csharp
Smartcardemulator.IsHostCardEmulationSupported();
```

## <a name="lock-screen-and-screen-off-behavior"></a><span data-ttu-id="40ba5-255">Verhalten des Sperrbildschirms und bei „Bildschirm aus“</span><span class="sxs-lookup"><span data-stu-id="40ba5-255">Lock screen and screen off behavior</span></span>

<span data-ttu-id="40ba5-256">Windows10 Mobile enthält Einstellungen für die Kartenemulation auf Geräteebene, die vom Mobilfunknetzbetreiber oder Hersteller des Geräts festgelegt werden können.</span><span class="sxs-lookup"><span data-stu-id="40ba5-256">Windows 10 Mobile has device-level card emulation settings, which can be set by the mobile operator or the manufacturer of the device.</span></span> <span data-ttu-id="40ba5-257">Das Umschalten der Option „Zum Bezahlen berühren“ ist standardmäßig deaktiviert, und die „Aktivierungsrichtlinie auf Geräteebene“ ist auf „Immer“ festgelegt, es sei denn, der Netzbetreiber oder Hersteller überschreibt diese Werte.</span><span class="sxs-lookup"><span data-stu-id="40ba5-257">By default, "tap to pay" toggle is disabled and the "enablement policy at device level" is set to "Always", unless the MO or OEM overwrites these values.</span></span>

<span data-ttu-id="40ba5-258">Ihre Anwendung kann den Wert von [**EnablementPolicy**](https://msdn.microsoft.com/library/windows/apps/Dn608006) auf Geräteebene abfragen und abhängig vom gewünschten Verhalten Ihrer App in den einzelnen Zuständen jeweils Maßnahmen ergreifen.</span><span class="sxs-lookup"><span data-stu-id="40ba5-258">Your application can query the value of the [**EnablementPolicy**](https://msdn.microsoft.com/library/windows/apps/Dn608006) at device level and take action for each case depending on the desired behavior of your app in each state.</span></span>

```csharp
SmartCardEmulator emulator = await SmartCardEmulator.GetDefaultAsync();

switch (emulator.EnablementPolicy)
{
case Never:
// you can take the user to the NFC settings to turn "tap and pay" on
await Windows.System.Launcher.LaunchUriAsync(new Uri("ms-settings-nfctransactions:"));
break;

 case Always:
return "Card emulation always on";

 case ScreenOn:
 return "Card emulation on only when screen is on";

 case ScreenUnlocked:
 return "Card emulation on only when screen unlocked";
}
```

<span data-ttu-id="40ba5-259">Die Hintergrundaufgabe der App wird nur dann gestartet, wenn das Smartphone gesperrt bzw. der Bildschirm ausgeschaltet ist, sofern die externe Leseeinheit eine AID auswählt, die für Ihre App aufgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="40ba5-259">Your app's background task will be launched even if the phone is locked and/or the screen is off only if the external reader selects an AID that resolves to your app.</span></span> <span data-ttu-id="40ba5-260">Sie können auf die Befehle der Leseeinheit in Ihrer Hintergrundaufgabe reagieren, aber wenn Sie Eingaben vom Benutzer benötigen oder dem Benutzer eine Meldung anzeigen möchten, können Sie die Vordergrund-App mit einigen Argumenten starten.</span><span class="sxs-lookup"><span data-stu-id="40ba5-260">You can respond to the commands from the reader in your background task, but if you need any input from the user or if you want to show a message to the user, you can launch your foreground app with some arguments.</span></span> <span data-ttu-id="40ba5-261">Ihre Hintergrundaufgabe kann Ihre Vordergrund-App mit dem folgenden Verhalten starten:</span><span class="sxs-lookup"><span data-stu-id="40ba5-261">Your background task can launch your foreground app with the following behavior.</span></span>

-   <span data-ttu-id="40ba5-262">Unterhalb des Sperrbildschirms eines Geräts (Benutzer sehen die Vordergrund-App erst nach dem Entsperren des Geräts)</span><span class="sxs-lookup"><span data-stu-id="40ba5-262">Under the device lock screen (the user will see your foreground app only after she unlocks the device)</span></span>
-   <span data-ttu-id="40ba5-263">Oberhalb des Sperrbildschirms (das Gerät befindet sich nach dem Schließen Ihrer App durch den Benutzer weiterhin im gesperrten Zustand)</span><span class="sxs-lookup"><span data-stu-id="40ba5-263">Above the device lock screen (after the user dismisses your app, the device is still in locked state)</span></span>

```csharp
        if (Windows::Phone::System::SystemProtection::ScreenLocked)
        {
            // Launch above the lock with some arguments
            var result = await eventDetails.TryLaunchSelfAsync("app-specific arguments", SmartCardLaunchBehavior.AboveLock);
        }
```

## <a name="aid-registration-and-other-updates-for-sim-based-apps"></a><span data-ttu-id="40ba5-264">AID-Registrierung und andere Updates für SIM-basierte Apps</span><span class="sxs-lookup"><span data-stu-id="40ba5-264">AID registration and other updates for SIM based apps</span></span>

<span data-ttu-id="40ba5-265">Kartenemulations-Apps, bei denen die SIM-Karte als sicheres Element verwendet wird, können beim Windows-Dienst registriert werden, um die auf der SIM-Karte unterstützten AIDs zu deklarieren.</span><span class="sxs-lookup"><span data-stu-id="40ba5-265">Card emulation apps that use the SIM as the secure element can register with the Windows service to declare the AIDs supported on the SIM.</span></span> <span data-ttu-id="40ba5-266">Diese Registrierung ähnelt einer HCE-basierten App-Registrierung.</span><span class="sxs-lookup"><span data-stu-id="40ba5-266">This registration is very similar to an HCE-based app registration.</span></span> <span data-ttu-id="40ba5-267">Der einzige Unterschied ist der [**SmartCardEmulationType**](https://msdn.microsoft.com/library/windows/apps/Dn894639), der für SIM-basierte Apps auf „Uicc“ festgelegt werden sollte.</span><span class="sxs-lookup"><span data-stu-id="40ba5-267">The only difference is the [**SmartCardEmulationType**](https://msdn.microsoft.com/library/windows/apps/Dn894639), which should be set to Uicc for SIM-based apps.</span></span> <span data-ttu-id="40ba5-268">Als Ergebnis der Zahlungskartenregistrierung wird der Anzeigename der Karte auch in das Menü mit den NFC-Einstellungen eingefügt.</span><span class="sxs-lookup"><span data-stu-id="40ba5-268">As the result of the payment card registration, the display name of the card will also be populated in the NFC setting menu.</span></span>

```csharp
var appletIdGroup = new SmartCardAppletIdGroup(
                        "Example DisplayName",
                                new List<IBuffer> {AID_PPSE.AsBuffer()},
                                SmartCardEmulationCategory.Payment,
                                SmartCardEmulationType.Uicc);
```

** <span data-ttu-id="40ba5-269">Wichtig</span><span class="sxs-lookup"><span data-stu-id="40ba5-269">Important</span></span> **  
<span data-ttu-id="40ba5-270">Die Legacyunterstützung des binären SMS-Abfangverfahrens in Windows Phone8.1 wurde entfernt und in Windows10 Mobile durch eine neue, umfassendere SMS-Unterstützung ersetzt. Alle älteren Windows Phone8.1-Apps, die hierauf basieren, müssen aktualisiert werden, damit sie die neuen Windows10 Mobile-SMS-APIs nutzen.</span><span class="sxs-lookup"><span data-stu-id="40ba5-270">The legacy binary SMS intercept support in Windows Phone 8.1 has been removed and replaced with new broader SMS support in Windows 10 Mobile, but any legacy Windows Phone 8.1 apps relying on that must update to use the new Windows 10 Mobile SMS APIs.</span></span>
