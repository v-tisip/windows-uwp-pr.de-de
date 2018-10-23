---
author: Xansky
description: Hier erfahren Sie, wie Sie Ihre App aktualisieren, damit Sie die neuesten unterstützten Microsoft Advertising-Bibliotheken verwenden können und Ihre App weiterhin Banneranzeigen erhält.
title: Aktualisieren Ihrer App auf die neuesten Advertising-Bibliotheken für Banneranzeigen
ms.author: mhopkins
ms.date: 08/23/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Anzeigen, Werbung, AdControl, AdMediatorControl, Migrieren
ms.assetid: f8d5b2ad-fcdb-4891-bd68-39eeabdf799c
ms.localizationpriority: medium
ms.openlocfilehash: 87cd734196e66021555002a43cb41719c88a1cf8
ms.sourcegitcommit: c4d3115348c8b54fcc92aae8e18fdabc3deb301d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2018
ms.locfileid: "5407663"
---
# <a name="update-your-app-to-the-latest-advertising-libraries-for-banner-ads"></a><span data-ttu-id="9fa96-104">Aktualisieren Ihrer App auf die neuesten Advertising-Bibliotheken für Banneranzeigen</span><span class="sxs-lookup"><span data-stu-id="9fa96-104">Update your app to the latest advertising libraries for banner ads</span></span>

<span data-ttu-id="9fa96-105">Am dem 1.April2017 werden Banneranzeigen nicht mehr für Apps bereitgestellt, die nicht unterstützte Advertising-SDK-Versionen verwenden.</span><span class="sxs-lookup"><span data-stu-id="9fa96-105">As of April 1, 2017, we no longer serve banner ads to apps that use an unsupported advertising SDK release.</span></span> <span data-ttu-id="9fa96-106">Bei Verwendung von **AdControl** zum Anzeigen von Banneranzeigen in Ihrer universellen Windows-Plattform-App (UWP), verwenden Sie die Informationen in diesem Artikel, um herauszufinden, ob Sie eine nicht unterstützte Advertising-SDK verwenden und migrieren Sie Ihre App zu einem unterstützten SDK.</span><span class="sxs-lookup"><span data-stu-id="9fa96-106">If you use **AdControl** to display banner ads in your Universal Windows Platform (UWP) app, use the information in this article to determine whether you are using an unsupported advertising SDK and migrate your app to a supported SDK.</span></span>

## <a name="overview"></a><span data-ttu-id="9fa96-107">Übersicht</span><span class="sxs-lookup"><span data-stu-id="9fa96-107">Overview</span></span>

<span data-ttu-id="9fa96-108">UWP-Apps, die Banneranzeige verwenden, müssen **AdControl** aus der Advertising-Bibliotheken verwenden, die in [Microsoft Advertising-SDK](http://aka.ms/ads-sdk-uwp) verteilt werden.</span><span class="sxs-lookup"><span data-stu-id="9fa96-108">UWP apps that show banner ads must use **AdControl** from the advertising libraries that are distributed in the [Microsoft Advertising SDK](http://aka.ms/ads-sdk-uwp).</span></span> <span data-ttu-id="9fa96-109">Diese SDK-Version unterstützt einen mindestens erforderlichen Satz von Funktionen. Dies umfasst auch die Möglichkeit, HTML5-Rich-Media über die [Mobile Rich Media Ad Interface Definitions (MRAID) 1.0-Spezifikation](http://www.iab.com/wp-content/uploads/2015/08/IAB_MRAID_VersionOne.pdf) vom Interactive Advertising Bureau (IAB) zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="9fa96-109">This SDK supports a minimum set of advertising capabilities, including the ability to serve HTML5 rich media via the [Mobile Rich-media Ad Interface Definitions (MRAID) 1.0 specification](http://www.iab.com/wp-content/uploads/2015/08/IAB_MRAID_VersionOne.pdf) from the Interactive Advertising Bureau (IAB).</span></span> <span data-ttu-id="9fa96-110">Viele unserer Werbekunden wünschen sich diese Funktionen und wir setzen voraus, dass App-Entwickler eine dieser SDK-Versionen verwenden, damit unser App-Ökosystem für Werbekunden attraktiver wird und Ihr Umsatz wächst.</span><span class="sxs-lookup"><span data-stu-id="9fa96-110">Many of our advertisers seek these capabilities, and we require app developers to use one of these SDK releases to help make our app ecosystem more attractive to advertisers and ultimately drive more revenue to you.</span></span>

<span data-ttu-id="9fa96-111">Vor der Freigabe dieses SDK wurde die **AdControl**-Klasse in mehreren älteren Advertising-SDK-Versionen angeboten.</span><span class="sxs-lookup"><span data-stu-id="9fa96-111">Before this SDK was released, we previously provided the **AdControl** class in several older advertising SDK releases.</span></span> <span data-ttu-id="9fa96-112">Diese älteren Advertising-SDK-Versionen werden nicht mehr unterstützt, da sie den oben beschriebenen mindestens erforderlichen Satz von Funktionen nicht unterstützen.</span><span class="sxs-lookup"><span data-stu-id="9fa96-112">These older advertising SDK releases are no longer supported because they do not support the minimum advertising capabilities described above.</span></span> <span data-ttu-id="9fa96-113">Am dem 1.April2017 werden Banneranzeigen nicht mehr für Apps bereitgestellt, die nicht unterstützte Advertising-SDK-Versionen verwenden.</span><span class="sxs-lookup"><span data-stu-id="9fa96-113">As of April 1, 2017, we no longer serve banner ads to apps that use an unsupported advertising SDK release.</span></span> <span data-ttu-id="9fa96-114">Wenn Sie eine App besitzen, die weiterhin eine nicht unterstützte Advertising-SDK-Version verwendet, geschieht Folgendes:</span><span class="sxs-lookup"><span data-stu-id="9fa96-114">If you have an app that still uses an unsupported advertising SDK release, you will see the following behavior:</span></span>

* <span data-ttu-id="9fa96-115">Banneranzeigen werden nicht mehr für **AdControl** in Ihrer App bereitgestellt, und Sie erhalten keinen Anzeigenumsatz mehr aus diesen Steuerelementen.</span><span class="sxs-lookup"><span data-stu-id="9fa96-115">Banner ads will no longer be served to any **AdControl** in your app, and you will no longer earn advertising revenue from those controls.</span></span>

* <span data-ttu-id="9fa96-116">Wenn **AdControl** in Ihrer App eine neue Anzeige anfordert, wird ein **ErrorOccurred**-Ereignis des Steuerelements ausgegeben, und die **ErrorCode**-Eigenschaft der Ereignisargumente hat den Wert **NoAdAvailable**.</span><span class="sxs-lookup"><span data-stu-id="9fa96-116">When the **AdControl** in your app requests a new ad, the **ErrorOccurred** event of the control will be raised and the **ErrorCode** property of the event args will have the value **NoAdAvailable**.</span></span>

* <span data-ttu-id="9fa96-117">Alle Anzeigeneinheiten, die Ihrer App zugeordnet sind, werden deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="9fa96-117">Any ad units that are associated with your app will be deactivated.</span></span> <span data-ttu-id="9fa96-118">Sie können diese deaktivierten Anzeigeeinheiten nicht aus Ihrem Dev Center-Konto entfernen.</span><span class="sxs-lookup"><span data-stu-id="9fa96-118">You cannot remove these deactivated ad units from your Dev Center account.</span></span> <span data-ttu-id="9fa96-119">Wenn Sie Ihre App aktualisieren, damit Sie ein unterstütztes [Microsoft Advertising-SDK](http://aka.ms/ads-sdk-uwp) nutzen können, ignorieren Sie diese Anzeigeneinheiten und erstellen Sie neue.</span><span class="sxs-lookup"><span data-stu-id="9fa96-119">If you update your app to use the [Microsoft Advertising SDK](http://aka.ms/ads-sdk-uwp), ignore these ad units and create new ones.</span></span>

* <span data-ttu-id="9fa96-120">Banneranzeigen werden nicht mehr für Anzeigeneinheiten bereitgestellt, die in mehreren Apps verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="9fa96-120">Banner ads will also no longer be served for any ad unit that is used in more than one app.</span></span> <span data-ttu-id="9fa96-121">Stellen Sie sicher, dass Ihre Anzeigeneinheiten jeweils nur in einer App verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="9fa96-121">Make sure that your ad units are each used in only one app.</span></span>

<span data-ttu-id="9fa96-122">Wenn Sie über eine App verfügen (bereits im Store oder noch in Entwicklung), die Banneranzeigen mithilfe von **AdControl** anzeigt, und Sie nicht sicher sind, welches Advertising-SDK von Ihrer App verwendet wird, ermitteln Sie anhand der Anweisungen in diesem Artikel, ob Sie Ihre App auf ein unterstütztes SDK aktualisieren müssen.</span><span class="sxs-lookup"><span data-stu-id="9fa96-122">If you have an existing app (already in the Store or still under development) that displays banner ads using **AdControl** and you aren't sure which advertising SDK is being used by your app, follow the instructions in this article to determine whether you need to update your app to a supported SDK.</span></span> <span data-ttu-id="9fa96-123">Wenn Schwierigkeiten auftreten oder Sie Hilfe benötigen, [wenden Sie sich an den Support](http://go.microsoft.com/fwlink/?LinkId=393643).</span><span class="sxs-lookup"><span data-stu-id="9fa96-123">If you encounter any issues or you need assistance, please [contact support](http://go.microsoft.com/fwlink/?LinkId=393643).</span></span>

> [!NOTE]
> <span data-ttu-id="9fa96-124">Wenn Ihre App bereits [Microsoft Advertising-SDK](http://aka.ms/ads-sdk-uwp) (für UWP-Apps) verwendet müssen für Ihre App keine weiteren Änderungen vorgenommen werden.</span><span class="sxs-lookup"><span data-stu-id="9fa96-124">If your app already uses the [Microsoft Advertising SDK](http://aka.ms/ads-sdk-uwp) (for UWP apps), you do not need to make any further changes to your app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9fa96-125">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="9fa96-125">Prerequisites</span></span>

* <span data-ttu-id="9fa96-126">Der komplette Quellcode und Visual Studio-Projektdateien für Ihre App, die **AdControl** verwendet.</span><span class="sxs-lookup"><span data-stu-id="9fa96-126">The complete source code and Visual Studio project files for your app that uses **AdControl**.</span></span>
* <span data-ttu-id="9fa96-127">Das APPX-Paket für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="9fa96-127">The .appx package for your app.</span></span>

> [!NOTE]
> <span data-ttu-id="9fa96-128">Wenn Sie über das APPX-Paket für Ihre App nicht mehr verfügen, Ihnen aber noch immer ein Entwicklungscomputer mit der Version von Visual Studio und dem Advertising-SDK, das für die App-Erstellung eingesetzt wurde, zur Verfügung steht, können Sie das APPX- Paket in Visual Studio neu generieren.</span><span class="sxs-lookup"><span data-stu-id="9fa96-128">If you no longer have the .appx package for your app but you do still have a development computer with the version of Visual Studio and the advertising SDK that was used to build your app, you can regenerate the .appx package in Visual Studio.</span></span>

<span id="part-1" />

## <a name="part-1-determine-whether-you-need-to-update-your-uwp-app"></a><span data-ttu-id="9fa96-129">Teil 1: Ermitteln, ob Ihre UWP-App aktualisiert werden muss</span><span class="sxs-lookup"><span data-stu-id="9fa96-129">Part 1: Determine whether you need to update your UWP app</span></span>

<span data-ttu-id="9fa96-130">Befolgen Sie die Anweisungen in den folgenden Abschnitten, um festzustellen, ob Sie Ihre App aktualisieren müssen.</span><span class="sxs-lookup"><span data-stu-id="9fa96-130">Follow the instructions in the following sections to determine if you need to update your app.</span></span>

1. <span data-ttu-id="9fa96-131">Erstellen Sie eine Kopie des APPX-Pakets für Ihre App, damit das Original nicht beeinträchtigt wird, benennen Sie die Kopie um, sodass sie die Erweiterung „.zip“ erhält, und extrahieren Sie den Inhalt der Datei.</span><span class="sxs-lookup"><span data-stu-id="9fa96-131">Create a copy of the .appx package for your app so you do not disturb the original, rename the copy so it has a .zip extension, and extract the contents of the file.</span></span>

2. <span data-ttu-id="9fa96-132">Überprüfen Sie den extrahierten Inhalt Ihres App-Pakets:</span><span class="sxs-lookup"><span data-stu-id="9fa96-132">Check the extracted contents of your app package:</span></span>
  * <span data-ttu-id="9fa96-133">Wenn die Datei „Microsoft.Advertising.dll“ vorhanden ist, verwendet Ihre App ein altes SDK, und Sie müssen Ihr Projekt aktualisieren, indem Sie die Anweisungen in den folgenden Abschnitten ausführen.</span><span class="sxs-lookup"><span data-stu-id="9fa96-133">If you see a Microsoft.Advertising.dll file, your app uses an old SDK and you must update your project by following the instructions in the sections below.</span></span> <span data-ttu-id="9fa96-134">Fahren Sie mit [Teil 2](update-your-app-to-the-latest-advertising-libraries.md#part-2) fort.</span><span class="sxs-lookup"><span data-stu-id="9fa96-134">Proceed to [Part 2](update-your-app-to-the-latest-advertising-libraries.md#part-2).</span></span>
  * <span data-ttu-id="9fa96-135">Wenn die Datei „Microsoft.Advertising.dll“ nicht vorhanden ist, verwendet Ihre UWP-App bereits das neueste verfügbare Advertising SDK, und Sie müssen keine Änderungen an Ihrem Projekt vornehmen.</span><span class="sxs-lookup"><span data-stu-id="9fa96-135">If you do not see a Microsoft.Advertising.dll file, your UWP app already uses the latest available advertising SDK and you do not need to make any changes to your project.</span></span>


<span id="part-2" />

## <a name="part-2-install-the-latest-sdk"></a><span data-ttu-id="9fa96-136">Teil 2: Installieren der aktuellen SDK-Version</span><span class="sxs-lookup"><span data-stu-id="9fa96-136">Part 2: Install the latest SDK</span></span>

<span data-ttu-id="9fa96-137">Wenn Ihre App eine alte SDK-Version verwendet, führen Sie diese Anweisungen aus, um sicherzustellen, dass Sie das aktuelle SDK auf Ihrem Entwicklungscomputer verwenden.</span><span class="sxs-lookup"><span data-stu-id="9fa96-137">If your app uses an old SDK release, follow these instructions to make sure you have the latest SDK on your development computer.</span></span>

1. <span data-ttu-id="9fa96-138">Stellen Sie sicher, dass auf Ihrem Entwicklungscomputer Visual Studio2015 oder eine spätere Version installiert ist.</span><span class="sxs-lookup"><span data-stu-id="9fa96-138">Make sure your development computer has Visual Studio 2015 or a later release installed.</span></span>
    > [!NOTE]
    > <span data-ttu-id="9fa96-139">Wenn Visual Studio auf Ihrem Entwicklungscomputer geöffnet ist, schließen Sie es, bevor Sie die folgenden Schritte ausführen.</span><span class="sxs-lookup"><span data-stu-id="9fa96-139">If Visual Studio is open on your development computer, close it before you perform the following steps.</span></span>

1.  <span data-ttu-id="9fa96-140">Deinstallieren Sie alle früheren Versionen des Microsoft Advertising SDK und Ad Mediator SDK auf Ihrem Entwicklungscomputer.</span><span class="sxs-lookup"><span data-stu-id="9fa96-140">Uninstall all prior versions of the Microsoft Advertising SDK and Ad Mediator SDK from your development computer.</span></span>

2.  <span data-ttu-id="9fa96-141">Öffnen Sie ein **Eingabeaufforderungsfenster**, und führen Sie diese Befehle aus, um alle SDK-Versionen zu löschen, die möglicherweise mit Visual Studio installiert wurden und nicht in der Liste der installierten Programme auf Ihrem Computer angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="9fa96-141">Open a **Command Prompt** window and run these commands to clean out any SDK versions that may have been installed with Visual Studio, but which may not appear in the list of installed programs on your computer:</span></span>
    ```syntax
    MsiExec.exe /x{5C87A4DB-31C7-465E-9356-71B485B69EC8}
    MsiExec.exe /x{6AB13C21-C3EC-46E1-8009-6FD5EBEE515B}
    MsiExec.exe /x{6AC81125-8485-463D-9352-3F35A2508C11}
    ```

3.  <span data-ttu-id="9fa96-142">Installieren des [Microsoft Advertising-SDK](http://aka.ms/ads-sdk-uwp).</span><span class="sxs-lookup"><span data-stu-id="9fa96-142">Install the [Microsoft Advertising SDK](http://aka.ms/ads-sdk-uwp).</span></span>

## <a name="part-3-update-your-project"></a><span data-ttu-id="9fa96-143">Teil 3: Aktualisieren Ihres Projekts</span><span class="sxs-lookup"><span data-stu-id="9fa96-143">Part 3: Update your project</span></span>

<span data-ttu-id="9fa96-144">Entfernen Sie alle vorhandenen Verweise auf Microsoft Advertising-Bibliotheken aus dem Projekt, und führen Sie zum Hinzufügen der erforderlichen Verweise [diese Anweisungen](install-the-microsoft-advertising-libraries.md#reference) aus.</span><span class="sxs-lookup"><span data-stu-id="9fa96-144">Remove all existing references to the Microsoft advertising libraries from the project and follow [these instructions](install-the-microsoft-advertising-libraries.md#reference) to add the required references.</span></span> <span data-ttu-id="9fa96-145">Dadurch wird sichergestellt, dass Ihr Projekt die richtigen Bibliotheken verwendet.</span><span class="sxs-lookup"><span data-stu-id="9fa96-145">This will ensure that your project uses the correct libraries.</span></span> <span data-ttu-id="9fa96-146">Sie können Ihr vorhandenes Markup und den Code beibehalten.</span><span class="sxs-lookup"><span data-stu-id="9fa96-146">You can preserve your existing markup and code.</span></span>

## <a name="part-4-test-and-republish-your-app"></a><span data-ttu-id="9fa96-147">Teil 4: Testen und erneutes Veröffentlichen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="9fa96-147">Part 4: Test and republish your app</span></span>

<span data-ttu-id="9fa96-148">Testen Sie Ihre App, um sicherzustellen, dass sie Banneranzeigen korrekt anzeigt.</span><span class="sxs-lookup"><span data-stu-id="9fa96-148">Test your app to make sure it displays banner ads as expected.</span></span>

<span data-ttu-id="9fa96-149">Wenn die vorherige Version Ihrer App bereits im Store verfügbar ist, erstellen Sie im Dev Center-Dashboard [eine neue Übermittlung](../publish/app-submissions.md) für Ihre aktualisierte App, um diese erneut zu veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="9fa96-149">If the previous version of your app is already available in the Store, [create a new submission](../publish/app-submissions.md) for your updated app in the Dev Center dashboard to republish your app.</span></span>
