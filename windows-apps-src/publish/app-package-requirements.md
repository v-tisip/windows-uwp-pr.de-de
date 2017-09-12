---
author: jnHs
Description: "Halten Sie die folgenden Richtlinien ein, wenn Sie die App-Pakete für die Übermittlung an den Windows Store vorbereiten."
title: App-Paketanforderungen
ms.assetid: 651B82BA-9D0C-45AC-8997-88CD93DC903C
ms.author: wdg-dev-content
ms.date: 06/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 39926699a81ce6882a46f4ec89b863d6147717dd
ms.sourcegitcommit: bfa61aae632cca0c68dbfb0168424d38fd607f84
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2017
---
# <a name="app-package-requirements"></a><span data-ttu-id="ac09f-104">App-Paketanforderungen</span><span class="sxs-lookup"><span data-stu-id="ac09f-104">App package requirements</span></span>

<span data-ttu-id="ac09f-105">Halten Sie die folgenden Richtlinien ein, wenn Sie die App-Pakete für die Übermittlung an den Windows Store vorbereiten.</span><span class="sxs-lookup"><span data-stu-id="ac09f-105">Follow these guidelines to prepare your app's packages for submission to the Windows Store.</span></span>

## <a name="before-you-build-your-apps-package-for-the-windows-store"></a><span data-ttu-id="ac09f-106">Vor dem Erstellen des App-Pakets für den Windows Store</span><span class="sxs-lookup"><span data-stu-id="ac09f-106">Before you build your app's package for the Windows Store</span></span>

<span data-ttu-id="ac09f-107">Denken Sie daran, [Ihre App mit dem Zertifizierungskit für Windows-Apps zu testen](../debug-test-perf/windows-app-certification-kit.md).</span><span class="sxs-lookup"><span data-stu-id="ac09f-107">Make sure to [test your app with the Windows App Certification Kit](../debug-test-perf/windows-app-certification-kit.md).</span></span> <span data-ttu-id="ac09f-108">Außerdem wird empfohlen, Ihre App mit verschiedenen Hardwaretypen zu testen.</span><span class="sxs-lookup"><span data-stu-id="ac09f-108">We also recommend that you test your app on different types of hardware.</span></span> <span data-ttu-id="ac09f-109">Beachten Sie, dass Ihre App nur auf Computern mit Entwicklerlizenzen installiert und ausgeführt werden kann, bis wir die App zertifiziert und im Windows Store verfügbar gemacht haben.</span><span class="sxs-lookup"><span data-stu-id="ac09f-109">Note that until we certify your app and make it available from the Windows Store, it can only be installed and run on computers that have developer licenses.</span></span>

## <a name="building-the-app-package-using-microsoft-visual-studio"></a><span data-ttu-id="ac09f-110">Erstellen des App-Pakets mit Microsoft Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ac09f-110">Building the app package using Microsoft Visual Studio</span></span>

<span data-ttu-id="ac09f-111">Wenn Sie Microsoft Visual Studio als Entwicklungsumgebung verwenden, verfügen Sie bereits über integrierte Tools zum schnellen und einfachen Erstellen eines App-Pakets.</span><span class="sxs-lookup"><span data-stu-id="ac09f-111">If you're using Microsoft Visual Studio as your development environment, you already have built-in tools that make creating an app package a quick and easy process.</span></span> <span data-ttu-id="ac09f-112">Weitere Informationen finden Sie unter [Verpacken von Apps](../packaging/index.md).</span><span class="sxs-lookup"><span data-stu-id="ac09f-112">For more info, see [Packaging apps](../packaging/index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="ac09f-113">Achten Sie darauf, für alle Dateinamen ANSI zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="ac09f-113">Be sure that all your filenames use ANSI.</span></span> 

<span data-ttu-id="ac09f-114">Um Ihr Paket in Visual Studio zu erstellen, müssen Sie sich mit demselben Konto anmelden, das Ihrem Entwicklerkonto zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="ac09f-114">When you create your package in Visual Studio, make sure you are signed in with the same account associated with your developer account.</span></span> <span data-ttu-id="ac09f-115">Einige Teile des Paketmanifests enthalten spezifische kontobezogene Details.</span><span class="sxs-lookup"><span data-stu-id="ac09f-115">Some parts of the package manifest have specific details related to your account.</span></span> <span data-ttu-id="ac09f-116">Diese Informationen werden erkannt und automatisch hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="ac09f-116">This info is detected and added automatically.</span></span> <span data-ttu-id="ac09f-117">Ohne die zusätzlichen Informationen, die dem Manifest hinzugefügt wurden, können beim Hochladen von Paketen Fehler auftreten.</span><span class="sxs-lookup"><span data-stu-id="ac09f-117">Without the additional information added to the manifest, you may encounter package upload failures.</span></span> 

<span data-ttu-id="ac09f-118">Beim Erstellen der App-Pakete kann Visual Studio eine APPX-Datei oder eine APPXUPLOAD-Datei erstellen (bzw. eine XAP-Datei für Windows Phone 8.1 und frühere Versionen).</span><span class="sxs-lookup"><span data-stu-id="ac09f-118">When you build your app's packages, Visual Studio can create an .appx file or an .appxupload file (or a .xap file for Windows Phone 8.1 and earlier).</span></span> <span data-ttu-id="ac09f-119">Bei Apps für Windows 10 laden Sie immer die APPXUPLOAD-Datei auf die Seite [Pakete](upload-app-packages.md) hoch.</span><span class="sxs-lookup"><span data-stu-id="ac09f-119">For apps that target Windows 10, always upload the .appxupload file in the [Packages](upload-app-packages.md) page.</span></span> <span data-ttu-id="ac09f-120">Weitere Informationen zum Verpacken von UWP-Apps für den Store finden Sie unter [Verpacken universeller Windows-Apps für Windows 10](http://go.microsoft.com/fwlink/p/?LinkId=620193 ).</span><span class="sxs-lookup"><span data-stu-id="ac09f-120">For more info about packaging UWP apps for the Store, see [Packaging Universal Windows apps for Windows 10](http://go.microsoft.com/fwlink/p/?LinkId=620193 ).</span></span>

<span data-ttu-id="ac09f-121">App-Pakete müssen nicht mit einem Stammzertifikat einer vertrauenswürdigen Zertifizierungsstelle signiert werden.</span><span class="sxs-lookup"><span data-stu-id="ac09f-121">Your app's packages don't have to be signed with a certificate rooted in a trusted certificate authority.</span></span>


### <a name="app-bundles"></a><span data-ttu-id="ac09f-122">App-Bündel</span><span class="sxs-lookup"><span data-stu-id="ac09f-122">App bundles</span></span>

<span data-ttu-id="ac09f-123">Für Apps, die für Windows 8.1, Windows Phone 8.1 und höhere Versionen entwickelt werden, kann Visual Studio ein App-Bündel (.appxbundle) erzeugen, um die Downloadgröße der App für den Benutzer zu reduzieren.</span><span class="sxs-lookup"><span data-stu-id="ac09f-123">For apps that target Windows 8.1, Windows Phone 8.1, and later, Visual Studio can generate an app bundle (.appxbundle) to reduce the size of the app that users download.</span></span> <span data-ttu-id="ac09f-124">Dieser Schritt ist in der Regel sinnvoll, wenn Sie sprachspezifische Ressourcen, mehrere Ressourcen für die Bildgröße oder Ressourcen für bestimmte Versionen von Microsoft DirectX definiert haben.</span><span class="sxs-lookup"><span data-stu-id="ac09f-124">This can be helpful if you've defined language-specific assets, a variety of image-scale assets, or resources that apply to specific versions of Microsoft DirectX.</span></span>

> [!NOTE]
> <span data-ttu-id="ac09f-125">Ein App-Bündel kann Ihre Pakete für alle Architekturen enthalten.</span><span class="sxs-lookup"><span data-stu-id="ac09f-125">One app bundle can contain your packages for all architectures.</span></span> <span data-ttu-id="ac09f-126">Pro Zielbetriebssystem sollte nur ein App-Bündel eingereicht werden.</span><span class="sxs-lookup"><span data-stu-id="ac09f-126">You should submit only one bundle for each targeted OS.</span></span>

<span data-ttu-id="ac09f-127">Bei einem App-Bündel lädt der Benutzer nicht alle vorhandenen Ressourcen, sondern nur relevante Dateien herunter.</span><span class="sxs-lookup"><span data-stu-id="ac09f-127">With an app bundle, a user will only download the relevant files, rather than all possible resources.</span></span> <span data-ttu-id="ac09f-128">Weitere Informationen zu App-Bündeln finden Sie unter [Verpacken von Apps](../packaging/index.md) und [Verpacken von UWP-App mit Visual Studio](../packaging/packaging-uwp-apps.md).</span><span class="sxs-lookup"><span data-stu-id="ac09f-128">For more info about app bundles, see [Packaging apps](../packaging/index.md) and [Package a UWP app with Visual Studio](../packaging/packaging-uwp-apps.md).</span></span>


## <a name="building-the-app-package-manually"></a><span data-ttu-id="ac09f-129">Manuelles Erstellen des App-Pakets</span><span class="sxs-lookup"><span data-stu-id="ac09f-129">Building the app package manually</span></span>

<span data-ttu-id="ac09f-130">Wenn Sie Ihr Paket nicht mit Visual Studio erstellen, müssen Sie Ihr [Paketmanifest manuell erstellen](https://msdn.microsoft.com/library/windows/apps/br211476).</span><span class="sxs-lookup"><span data-stu-id="ac09f-130">If you don't use Visual Studio to create your package, you must [create your package manifest manually](https://msdn.microsoft.com/library/windows/apps/br211476).</span></span>

<span data-ttu-id="ac09f-131">Ausführliche Informationen und die Anforderungen für Manifeste finden Sie in der Dokumentation zum [App-Paketmanifest](https://msdn.microsoft.com/library/windows/apps/br211474).</span><span class="sxs-lookup"><span data-stu-id="ac09f-131">Be sure to review the [App package manifest](https://msdn.microsoft.com/library/windows/apps/br211474) documentation for complete manifest details and requirements.</span></span> <span data-ttu-id="ac09f-132">Es werden nur Apps zertifiziert, deren Manifest dem Paketmanifestschema entspricht.</span><span class="sxs-lookup"><span data-stu-id="ac09f-132">Your manifest must follow the package manifest schema in order to pass certification.</span></span>

<span data-ttu-id="ac09f-133">Ihr Manifest muss spezifische konto- und App-bezogene Informationen enthalten.</span><span class="sxs-lookup"><span data-stu-id="ac09f-133">Your manifest must include some specific info about your account and your app.</span></span> <span data-ttu-id="ac09f-134">Sie finden diese Informationen unter [Anzeigen von Details zur App-Identität](view-app-identity-details.md) im Abschnitt **App-Verwaltung** der App-Übersichtsseite im Dashboard.</span><span class="sxs-lookup"><span data-stu-id="ac09f-134">You can find this info by looking at [View app identity details](view-app-identity-details.md) in the **App management** section of your app's overview page in the dashboard.</span></span>

> [!NOTE]
> <span data-ttu-id="ac09f-135">Bei den Werten im Manifest wird die Groß-/Kleinschreibung berücksichtigt.</span><span class="sxs-lookup"><span data-stu-id="ac09f-135">Values in the manifest are case-sensitive.</span></span> <span data-ttu-id="ac09f-136">Leerzeichen und Satzzeichen müssen ebenfalls übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="ac09f-136">Spaces and other punctuation must also match.</span></span> <span data-ttu-id="ac09f-137">Geben Sie die Werte richtig ein, und überprüfen Sie sie anschließend auf ihre Korrektheit.</span><span class="sxs-lookup"><span data-stu-id="ac09f-137">Enter the values carefully and review them to ensure that they are correct.</span></span>


<span data-ttu-id="ac09f-138">App-Bündel verwenden ein anderes Manifest.</span><span class="sxs-lookup"><span data-stu-id="ac09f-138">App bundles use a different manifest.</span></span> <span data-ttu-id="ac09f-139">Ausführliche Informationen und die Anforderungen für App-Bündel finden Sie in der Dokumentation zum [Bündelmanifest](https://docs.microsoft.com/uwp/schemas/bundlemanifestschema/bundle-manifest).</span><span class="sxs-lookup"><span data-stu-id="ac09f-139">Review the [Bundle manifest](https://docs.microsoft.com/uwp/schemas/bundlemanifestschema/bundle-manifest) documentation for the details and requirements for app bundle manifests.</span></span>

> [!TIP]
> <span data-ttu-id="ac09f-140">Führen Sie vor dem Einreichen Ihrer Pakete unbedingt das [Zertifizierungskit für Windows-Apps](../debug-test-perf/windows-app-certification-kit.md) aus.</span><span class="sxs-lookup"><span data-stu-id="ac09f-140">Be sure to run the [Windows App Certification Kit](../debug-test-perf/windows-app-certification-kit.md) before you submit your packages.</span></span> <span data-ttu-id="ac09f-141">So können Sie feststellen, ob es mit Ihrem Manifest Probleme gibt, die Zertifizierungs- oder Einreichungsfehler verursachen können.</span><span class="sxs-lookup"><span data-stu-id="ac09f-141">This can you help determine if your manifest has any problems that might cause certification or submission failures.</span></span>

<span data-ttu-id="ac09f-142">Wenn Ihre App mehrere Pakete enthält, müssen die folgenden App-Manifestelemente in allen Paketen gleich sein (pro Zielbetriebssystem):</span><span class="sxs-lookup"><span data-stu-id="ac09f-142">If your app has more than one package, these app manifest elements must be the same in each package (per targeted OS):</span></span>

-   [**<span data-ttu-id="ac09f-143">Paket/Funktionen</span><span class="sxs-lookup"><span data-stu-id="ac09f-143">Package/Capabilities</span></span>**](https://msdn.microsoft.com/library/windows/apps/br211422)
-   [**<span data-ttu-id="ac09f-144">Paket/Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="ac09f-144">Package/Dependencies</span></span>**](https://msdn.microsoft.com/library/windows/apps/br211428)
-   [**<span data-ttu-id="ac09f-145">Paket/Ressourcen</span><span class="sxs-lookup"><span data-stu-id="ac09f-145">Package/Resources</span></span>**](https://msdn.microsoft.com/library/windows/apps/br211462)


## <a name="package-format-requirements"></a><span data-ttu-id="ac09f-146">Paketformatanforderungen</span><span class="sxs-lookup"><span data-stu-id="ac09f-146">Package format requirements</span></span>

<span data-ttu-id="ac09f-147">Ihre App-Pakete müssen die folgenden Anforderungen erfüllen:</span><span class="sxs-lookup"><span data-stu-id="ac09f-147">Your app’s packages must comply with these requirements.</span></span>

| <span data-ttu-id="ac09f-148">App-Paketeigenschaft</span><span class="sxs-lookup"><span data-stu-id="ac09f-148">App package property</span></span> | <span data-ttu-id="ac09f-149">Anforderung</span><span class="sxs-lookup"><span data-stu-id="ac09f-149">Requirement</span></span>                                                          |
|----------------------|----------------------------------------------------------------------|
| <span data-ttu-id="ac09f-150">Paketgröße</span><span class="sxs-lookup"><span data-stu-id="ac09f-150">Package size</span></span>         | <span data-ttu-id="ac09f-151">APPX-Bündel: maximal 25GB pro Bündel</span><span class="sxs-lookup"><span data-stu-id="ac09f-151">.appxbundle: 25 GB maximum per bundle</span></span> <br><span data-ttu-id="ac09f-152">APPX-Pakete für Windows 10: maximal 25 GB pro Paket</span><span class="sxs-lookup"><span data-stu-id="ac09f-152">.appx packages targeting Windows 10: 25 GB maximum per package</span></span><br><span data-ttu-id="ac09f-153">APPX-Pakete für Windows 8.1: maximal 8 GB pro Paket</span><span class="sxs-lookup"><span data-stu-id="ac09f-153">.appx packages targeting Windows 8.1: 8 GB maximum per package</span></span> <br> <span data-ttu-id="ac09f-154">APPX-Pakete für Windows 8: maximal 2 GB pro Paket</span><span class="sxs-lookup"><span data-stu-id="ac09f-154">.appx packages targeting Windows 8: 2 GB maximum per package</span></span> <br> <span data-ttu-id="ac09f-155">APPX-Pakete für WindowsPhone 8.1: maximal 4GB pro Paket</span><span class="sxs-lookup"><span data-stu-id="ac09f-155">.appx packages targeting Windows Phone 8.1: 4 GB maximum per package</span></span> <br> <span data-ttu-id="ac09f-156">XAP-Pakete: maximal 1 GB pro Paket</span><span class="sxs-lookup"><span data-stu-id="ac09f-156">.xap packages: 1 GB maximum per package</span></span>                                                                           |
| <span data-ttu-id="ac09f-157">Hashes für Blockzuordnung</span><span class="sxs-lookup"><span data-stu-id="ac09f-157">Block map hashes</span></span>     | <span data-ttu-id="ac09f-158">SHA2-256-Algorithmus</span><span class="sxs-lookup"><span data-stu-id="ac09f-158">SHA2-256 algorithm</span></span>                                                   |
 

## <a name="storemanifest-xml-file"></a><span data-ttu-id="ac09f-159">Datei „StoreManifest.xml“</span><span class="sxs-lookup"><span data-stu-id="ac09f-159">StoreManifest XML file</span></span>

<span data-ttu-id="ac09f-160">„StoreManifest.xml“ ist eine optionale Konfigurationsdatei, die in App-Pakete aufgenommen werden kann.</span><span class="sxs-lookup"><span data-stu-id="ac09f-160">StoreManifest.xml is an optional configuration file that may be included in app packages.</span></span> <span data-ttu-id="ac09f-161">Sie dient zum Aktivieren von Features, die vom Paketmanifest nicht abgedeckt werden – beispielsweise Features zum Deklarieren Ihrer App als Windows Store-Geräte-App oder zum Deklarieren von Anforderungen, die für ein Paket erfüllt werden müssen, damit es auf ein Gerät angewendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="ac09f-161">Its purpose is to enable features, such as declaring your app as a Windows Store device app or declaring requirements that a package depends on to be applicable to a device, that the package manifest does not cover.</span></span> <span data-ttu-id="ac09f-162">„StoreManifest.xml“ wird mit dem App-Paket eingereicht und muss sich im Stammordner des App-Hauptprojekts befinden.</span><span class="sxs-lookup"><span data-stu-id="ac09f-162">StoreManifest.xml is submitted with the app package and must be in the root folder of your app's main project.</span></span> <span data-ttu-id="ac09f-163">Weitere Informationen finden Sie unter [StoreManifest-Schema](https://docs.microsoft.com/uwp/schemas/storemanifest/store-manifest-schema-portal).</span><span class="sxs-lookup"><span data-stu-id="ac09f-163">For more info, see [StoreManifest schema](https://docs.microsoft.com/uwp/schemas/storemanifest/store-manifest-schema-portal).</span></span>

 

 




