---
author: eliotcowley
title: Einführung in Xbox One-Tools
description: Xbox One-spezifisches Tool Dev Home (unter Verwendung des Windows Device Portal).
ms.author: elcowle
ms.date: 10/04/2017
ms.topic: article
keywords: Windows 10, UWP, Xbox One, Tools
ms.assetid: 6eaf376f-0d7c-49de-ad78-38e689b43658
ms.localizationpriority: medium
ms.openlocfilehash: 71fd9f3ad1c3fcf02420502692518310b896f52a
ms.sourcegitcommit: 753e0a7160a88830d9908b446ef0907cc71c64e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "5763686"
---
# <a name="introduction-to-xbox-one-tools"></a><span data-ttu-id="9ce50-104">Einführung in Xbox One-Tools</span><span class="sxs-lookup"><span data-stu-id="9ce50-104">Introduction to Xbox One tools</span></span>

<span data-ttu-id="9ce50-105">In diesem Abschnitt wird erläutert, wie Sie auf das Xbox-Geräteportal über die Dev Home-App zugreifen.</span><span class="sxs-lookup"><span data-stu-id="9ce50-105">This section covers how to access the Xbox Device Portal through the Dev Home app.</span></span>

## <a name="dev-home"></a><span data-ttu-id="9ce50-106">Dev Home</span><span class="sxs-lookup"><span data-stu-id="9ce50-106">Dev Home</span></span>

<span data-ttu-id="9ce50-107">Dev Home ist ein Tool im Xbox One Development Kit, das die Produktivität von Entwicklern unterstützen soll.</span><span class="sxs-lookup"><span data-stu-id="9ce50-107">Dev Home is a tools experience on the Xbox One Development Kit designed to aid developer productivity.</span></span> <span data-ttu-id="9ce50-108">Dev Home bietet Funktionen zum Verwalten und Konfigurieren Ihres Dev Kit.</span><span class="sxs-lookup"><span data-stu-id="9ce50-108">Dev Home offers functionality to manage and configure your dev kit.</span></span>

<span data-ttu-id="9ce50-109">Dev Home ist die Standard-App, die geöffnet wird, wenn Ihre Konsole im Entwicklermodus gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="9ce50-109">Dev Home is the default app that is opened when your console in Developer Mode boots up.</span></span> <span data-ttu-id="9ce50-110">Sie können Dev Home auch über die Kachel **Dev Home** auf dem Startbildschirm öffnen.</span><span class="sxs-lookup"><span data-stu-id="9ce50-110">You can also open Dev Home by selecting the **Dev Home** tile on the home screen.</span></span> <span data-ttu-id="9ce50-111">Ist keine Kachel vorhanden, befindet sich die Konsole nicht im Entwicklermodus.</span><span class="sxs-lookup"><span data-stu-id="9ce50-111">If there is no tile present, the console is not in Developer Mode.</span></span>

<span data-ttu-id="9ce50-112">Weitere Informationen zu Dev Home finden Sie unter [Entwickler-Startbildschirm auf der Konsole (Dev Home)](dev-home.md).</span><span class="sxs-lookup"><span data-stu-id="9ce50-112">For more information about Dev Home, see [Developer Home on the Console (Dev Home)](dev-home.md).</span></span>

## <a name="xbox-device-portal"></a><span data-ttu-id="9ce50-113">Geräteportal für Xbox</span><span class="sxs-lookup"><span data-stu-id="9ce50-113">Xbox Device Portal</span></span>
<span data-ttu-id="9ce50-114">Das Geräteportal für Xbox ist ein browserbasiertes Geräteverwaltungstool, mit dem Sie Spiele und Apps hinzufügen, Xbox Live-Test-Konten hinzufügen, Sandkastenumgebungen ändern und viele andere Aktionen durchführen können.</span><span class="sxs-lookup"><span data-stu-id="9ce50-114">The Xbox Device Portal is a browser-based device management tool that allows you to add games and apps, add Xbox Live test accounts, change sandboxes, and much more.</span></span>

<span data-ttu-id="9ce50-115">So aktivieren Sie das Xbox-Geräteportal auf Ihrer Xbox One Konsole</span><span class="sxs-lookup"><span data-stu-id="9ce50-115">To enable the Xbox Device Portal on your Xbox One console:</span></span>

1. <span data-ttu-id="9ce50-116">Wählen Sie die Kachel **Dev Home** auf dem Startbildschirm aus.</span><span class="sxs-lookup"><span data-stu-id="9ce50-116">Select the **Dev Home** tile on the home screen.</span></span>

  ![Auswählen der Kachel „Dev Home“](images/introduction-to-xbox-one-tools-1.png)

2. <span data-ttu-id="9ce50-118">Navigieren Sie in Dev Home zur Registerkarte **Home**, und wählen Sie im Abschnitt **Remotezugriff** die Option **Remotezugriffseinstellungen** aus.</span><span class="sxs-lookup"><span data-stu-id="9ce50-118">Within Dev Home, navigate to the **Home** tab, and in the **Remote Access** section, select **Remote Access Settings**.</span></span>

  ![Tool „Remoteverwaltung"](images/introduction-to-xbox-one-tools-2.png)

3. <span data-ttu-id="9ce50-120">Aktivieren Sie das Kontrollkästchen **Xbox-Geräteportal aktivieren**.</span><span class="sxs-lookup"><span data-stu-id="9ce50-120">Select the **Enable Xbox Device Portal** checkbox.</span></span>

4. <span data-ttu-id="9ce50-121">Aktivieren Sie unter **Authentifizierung** das Kontrollkästchen **Authentifizierung für Remotezugriff auf diese Konsole über das Web oder PC-Tools anfordern**.</span><span class="sxs-lookup"><span data-stu-id="9ce50-121">Under **Authentication**, select the **Require authentication to remotely access this console from the web or PC tools** checkbox.</span></span>

5. <span data-ttu-id="9ce50-122">Geben Sie **Benutzername** und __Kennwort__ ein, und wählen Sie **Speichern** aus.</span><span class="sxs-lookup"><span data-stu-id="9ce50-122">Enter a **User name** and __Password__, and select **Save**.</span></span> <span data-ttu-id="9ce50-123">Diese Benutzeranmeldeinformationen werden zum Authentifizieren des Zugriffs auf Ihr Dev Kit über einen Browser verwendet.</span><span class="sxs-lookup"><span data-stu-id="9ce50-123">These credentials are used to authenticate access to your dev kit from a browser.</span></span>

6. <span data-ttu-id="9ce50-124">Wählen Sie **Schließen** aus, und notieren Sie sich auf der Registerkarte **Home** die im Tool **Remoteverwaltung** aufgelistete URL.</span><span class="sxs-lookup"><span data-stu-id="9ce50-124">Select **Close**, and on the **Home** tab, note the URL listed in the **Remote Access** tool.</span></span>

7. <span data-ttu-id="9ce50-125">Geben Sie die URL in Ihrem Browser ein.</span><span class="sxs-lookup"><span data-stu-id="9ce50-125">Enter the URL in your browser.</span></span> <span data-ttu-id="9ce50-126">Sie erhalten eine Warnung zum Zertifikat, das bereitgestellt wurde, ähnlich wie folgender Screenshot, dass das von Ihrer Xbox One Konsole signierte Sicherheitszertifikat nicht als bekannter vertrauenswürdiger Herausgeber betrachtet wird.</span><span class="sxs-lookup"><span data-stu-id="9ce50-126">You will receive a warning about the certificate that was provided, similar to the following screenshot, because the security certificate signed by your Xbox One console is not considered a well-known, trusted publisher.</span></span> <span data-ttu-id="9ce50-127">Klicken Sie in Edge auf **Details** und auf **Weiter zur Webseite**, um auf das Xbox-Geräteportal zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="9ce50-127">On Edge, click **Details** and then **Go on to the webpage** to access the Xbox Device Portal.</span></span>

    ![Sicherheitszertifikatwarnung](images/introduction-to-xbox-one-tools-3.png)

8. <span data-ttu-id="9ce50-129">Melden Sie sich mit den Anmeldeinformationen an, die Sie konfiguriert haben.</span><span class="sxs-lookup"><span data-stu-id="9ce50-129">Sign in with the credentials you configured.</span></span>

## <a name="xbox-dev-mode-companion"></a><span data-ttu-id="9ce50-130">Begleitung für den Xbox-Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="9ce50-130">Xbox Dev Mode Companion</span></span>
<span data-ttu-id="9ce50-131">Die Begleitung für den Xbox-Entwicklermodus ist ein Tool, mit dessen Hilfe Sie auf der Konsole arbeiten können, ohne den PC verlassen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="9ce50-131">Xbox Dev Mode Companion is a tool that allows you to work on your console without leaving your PC.</span></span> <span data-ttu-id="9ce50-132">Die App ermöglicht Ihnen die Anzeige des Konsolenbildschirms und das Senden von Eingaben an diesen.</span><span class="sxs-lookup"><span data-stu-id="9ce50-132">The app allows you to view the console screen and send input to it.</span></span> <span data-ttu-id="9ce50-133">Weitere Informationen finden Sie unter [Begleitung für den Xbox-Entwicklermodus](xbox-dev-mode-companion.md).</span><span class="sxs-lookup"><span data-stu-id="9ce50-133">For more information, see [Xbox Dev Mode Companion](xbox-dev-mode-companion.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9ce50-134">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="9ce50-134">See also</span></span>
- [<span data-ttu-id="9ce50-135">Verwenden von Fiddler mit Xbox One bei der Entwicklung für UWP</span><span class="sxs-lookup"><span data-stu-id="9ce50-135">How to use Fiddler with Xbox One when developing for UWP</span></span>](uwp-fiddler.md)
- [<span data-ttu-id="9ce50-136">Übersicht über das Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="9ce50-136">Windows Device Portal overview</span></span>](../debug-test-perf/device-portal.md)
- [<span data-ttu-id="9ce50-137">UWP auf XboxOne</span><span class="sxs-lookup"><span data-stu-id="9ce50-137">UWP on Xbox One</span></span>](index.md)