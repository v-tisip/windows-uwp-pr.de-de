---
author: jnHs
Description: "Im WindowsDevCenter-Dashboard können Sie Details zu einzelnen Apps verwalten und anzeigen sowie Dienste wie Benachrichtigungen, A/B-Tests und Karten konfigurieren."
title: App-Verwaltung und -Dienste
ms.assetid: 99DA2BC1-9B5D-4746-8BC0-EC723D516EEF
ms.author: wdg-dev-content
ms.date: 06/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 2ff75a5e85a37f4f47b6b32f3e8338524752bb2f
ms.sourcegitcommit: fadde8afee46238443ec1cb71846d36c91db9fb9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2017
---
# <a name="app-management-and-services"></a><span data-ttu-id="4ae45-104">App-Verwaltung und -Dienste</span><span class="sxs-lookup"><span data-stu-id="4ae45-104">App management and services</span></span>

<span data-ttu-id="4ae45-105">Im WindowsDevCenter-Dashboard können Sie Details zu einzelnen Apps verwalten und anzeigen sowie Dienste wie Benachrichtigungen, A/B-Tests und Karten konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="4ae45-105">You can manage and view details related to each of your apps in the Windows Dev Center dashboard, and configure services such as notifications, A/B testing, and maps.</span></span>

<span data-ttu-id="4ae45-106">Wenn Sie in Ihrem Dashboard mit einer App arbeiten, sehen Sie im linken Navigationsmenü Abschnitte für **Dienste** und **App-Verwaltung**.</span><span class="sxs-lookup"><span data-stu-id="4ae45-106">When working with an app in your dashboard, you'll see sections in the left navigation menu for **Services** and **App management**.</span></span> <span data-ttu-id="4ae45-107">Sie können diese Abschnitte erweitern, um auf die unten beschriebenen Funktionen zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="4ae45-107">You can expand these sections to access the functionality described below.</span></span>

## <a name="services"></a><span data-ttu-id="4ae45-108">Dienste</span><span class="sxs-lookup"><span data-stu-id="4ae45-108">Services</span></span>

<span data-ttu-id="4ae45-109">Im Abschnitt **Dienste** können Sie verschiedene Dienste für Ihre Apps verwalten.</span><span class="sxs-lookup"><span data-stu-id="4ae45-109">The **Services** section lets you manage several different services for your apps.</span></span>

## <a name="push-notifications"></a><span data-ttu-id="4ae45-110">Pushbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="4ae45-110">Push notifications</span></span>

<span data-ttu-id="4ae45-111">Im Abschnitt **Pushbenachrichtigungen** können Sie Benachrichtigungen für die Kunden Ihrer App erstellen und senden.</span><span class="sxs-lookup"><span data-stu-id="4ae45-111">The **Push notifications** section lets you create and send notifications to your app's customers.</span></span> <span data-ttu-id="4ae45-112">Sie können die Benachrichtigungen an alle Kunden Ihrer App oder an eine Teilmenge Ihrer Windows10-Kunden senden, die die in einem [Kundensegment](create-customer-segments.md) definierten Kriterien erfüllen.</span><span class="sxs-lookup"><span data-stu-id="4ae45-112">You can send them to all of your app's customers, or you can target a subset of your Windows 10 customers who meet the criteria you’ve defined in a [customer segment](create-customer-segments.md).</span></span> <span data-ttu-id="4ae45-113">Weitere Informationen finden Sie unter [Senden von Benachrichtigung an die Kunden Ihrer App](send-push-notifications-to-your-apps-customers.md).</span><span class="sxs-lookup"><span data-stu-id="4ae45-113">For more info, see [Send notifications to your app's customers](send-push-notifications-to-your-apps-customers.md).</span></span>

<span data-ttu-id="4ae45-114">Je nach Pakettyp Ihrer App und den jeweiligen Anforderungen können Sie auch eine der folgenden Optionen für Pushbenachrichtigungen verwenden, indem Sie im linken Navigationsmenü auf **WNS/MPNS** klicken:</span><span class="sxs-lookup"><span data-stu-id="4ae45-114">Depending on your app's package type and its specific requirements, you can also use one of the following options for push notifications by clicking **WNS/MPNS** in the left navigation menu:</span></span> 

-   <span data-ttu-id="4ae45-115">**Windows-Pushbenachrichtigungsdienste (Windows Push Notification Services, WNS)** ermöglichen es, Popup-, Kachel- und Badgeupdates sowie unformatierte Updates von Ihren eigenen Clouddiensten aus zu senden.</span><span class="sxs-lookup"><span data-stu-id="4ae45-115">**Windows Push Notification Services (WNS)** lets you send toast, tile, badge, and raw updates from your own cloud service.</span></span> <span data-ttu-id="4ae45-116">Weitere Informationen finden Sie unter [Übersicht über den Windows-Pushbenachrichtigungsdienst (Windows Push Notification Service, WNS)](https://msdn.microsoft.com/library/windows/apps/mt187203).</span><span class="sxs-lookup"><span data-stu-id="4ae45-116">For more info, see [Windows Push Notification Services (WNS) overview](https://msdn.microsoft.com/library/windows/apps/mt187203).</span></span>

-   <span data-ttu-id="4ae45-117">**Microsoft Azure Mobile Apps** ermöglichen das Senden von Pushbenachrichtigungen, die Authentifizierung und Verwaltung von App-Benutzern und das Speichern von App-Daten in der Cloud.</span><span class="sxs-lookup"><span data-stu-id="4ae45-117">**Microsoft Azure Mobile Apps** lets you send push notifications, authenticate and manage app users, and store app data in the cloud.</span></span> <span data-ttu-id="4ae45-118">Weitere Informationen finden Sie in der [MobileApps-Dokumentation](http://go.microsoft.com/fwlink/p/?LinkId=221116).</span><span class="sxs-lookup"><span data-stu-id="4ae45-118">For more info, see the [Mobile Apps documentation](http://go.microsoft.com/fwlink/p/?LinkId=221116).</span></span>

-   <span data-ttu-id="4ae45-119">Der **Microsoft-Pushbenachrichtigungsdienst (Microsoft Push Notification Service, MPNS)** kann mit Ihren XAP-Paketen für Windows Phone verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="4ae45-119">**Microsoft Push Notifications Service (MPNS)** can be used with your .xap packages for Windows Phone.</span></span> <span data-ttu-id="4ae45-120">Sie können eine begrenzte Anzahl nicht authentifizierter Benachrichtigungen senden, ohne hier eine Konfiguration vorzunehmen. Zur Vermeidung von Drosselungslimits wird jedoch empfohlen, authentifizierte Benachrichtigungen zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="4ae45-120">You can send a limited number of unauthenticated notifications without doing any configuration here, although we recommend using authenticated notifications to avoid throttling limits.</span></span> <span data-ttu-id="4ae45-121">Wenn Sie diesen Dienst verwenden, müssen Sie ein Zertifikat in das auf der Seite **Pushbenachrichtigungen** bereitgestellte Feld hochladen.</span><span class="sxs-lookup"><span data-stu-id="4ae45-121">If you're using MPNS, you'll need to upload a certificate to the field provided on the **Push notifications** page.</span></span> <span data-ttu-id="4ae45-122">Weitere Informationen finden Sie unter [Einrichten eines authentifizierten Webdiensts zum Senden von Pushbenachrichtigungen für Windows Phone 8](http://go.microsoft.com/fwlink/p/?LinkId=528736).</span><span class="sxs-lookup"><span data-stu-id="4ae45-122">For more info, see [Setting up an authenticated web service to send push notifications for Windows Phone 8](http://go.microsoft.com/fwlink/p/?LinkId=528736).</span></span>

## <a name="experimentation"></a><span data-ttu-id="4ae45-123">Experimentation</span><span class="sxs-lookup"><span data-stu-id="4ae45-123">Experimentation</span></span>

<span data-ttu-id="4ae45-124">Auf der Seite **Experimentation** können Sie Experimente mit A/B-Tests für Ihre Apps für die universelle Windows-Plattform (UWP) erstellen und ausführen.</span><span class="sxs-lookup"><span data-stu-id="4ae45-124">Use the **Experimentation** page to create and run experiments for your Universal Windows Platform (UWP) apps with A/B testing.</span></span> <span data-ttu-id="4ae45-125">Bei einem A/B-Test wird die Effektivität von Featureänderungen (oder Abweichungen) in Ihrer App für einige Kunden ermittelt, bevor die Änderungen für die Allgemeinheit aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="4ae45-125">In an A/B test, you measure the effectiveness of feature changes (or variations) in your app on some customers before you enable the changes for everyone.</span></span>

<span data-ttu-id="4ae45-126">Weitere Informationen finden Sie unter [Ausführen von App-Experimenten mit A/B-Tests](../monetize/run-app-experiments-with-a-b-testing.md).</span><span class="sxs-lookup"><span data-stu-id="4ae45-126">For more info, see [Run app experiments with A/B testing](../monetize/run-app-experiments-with-a-b-testing.md).</span></span>

## <a name="maps"></a><span data-ttu-id="4ae45-127">Karten</span><span class="sxs-lookup"><span data-stu-id="4ae45-127">Maps</span></span>

<span data-ttu-id="4ae45-128">Wenn Sie Kartendienste in Apps unter Windows Phone8.1 und früheren Versionen verwenden möchten, müssen Sie eine Kartendienst-Anwendungs-ID und ein Token in Ihren App-Code einfügen.</span><span class="sxs-lookup"><span data-stu-id="4ae45-128">To use map services in apps for Windows Phone 8.1 and earlier, you need a map service application ID and a token to include in your app's code.</span></span> <span data-ttu-id="4ae45-129">Sie finden das Token auf der Seite **Karten** im Abschnitt **Dienste**.</span><span class="sxs-lookup"><span data-stu-id="4ae45-129">You can get this token on the **Maps** page in the **Services** section.</span></span>

> [!NOTE]
> <span data-ttu-id="4ae45-130">Um Kartendienste in Apps zu verwenden, die auf Windows 10 or Windows 8.x ausgerichtet sind, besuchen Sie das [Bing Karten Dev Center](http://go.microsoft.com/fwlink/p/?LinkId=614880).</span><span class="sxs-lookup"><span data-stu-id="4ae45-130">To use map services in apps targeting Windows 10 or Windows 8.x, visit the [Bing Maps Dev Center](http://go.microsoft.com/fwlink/p/?LinkId=614880).</span></span> <span data-ttu-id="4ae45-131">Weitere Informationen finden Sie unter [Anfordern eines Kartenauthentifizierungsschlüssels](https://msdn.microsoft.com/library/windows/apps/mt219694).</span><span class="sxs-lookup"><span data-stu-id="4ae45-131">See [Request a maps authentication key](https://msdn.microsoft.com/library/windows/apps/mt219694) for more info.</span></span>

<span data-ttu-id="4ae45-132">Weitere Informationen finden Sie unter [Verwenden von Kartendiensten](use-map-services.md).</span><span class="sxs-lookup"><span data-stu-id="4ae45-132">For more info, see [Use map services](use-map-services.md).</span></span>

## <a name="product-collections-and-purchases"></a><span data-ttu-id="4ae45-133">Produktsammlungen und Einkäufe</span><span class="sxs-lookup"><span data-stu-id="4ae45-133">Product collections and purchases</span></span>

<span data-ttu-id="4ae45-134">Zur Verwendung der Windows Store-Sammlungs-API und der Windows Store-Einkaufs-API für den Zugriff auf Besitzerinformationen für Apps und Add-Ons müssen Sie hier die zugehörigen Azure AD-Client-IDs eingeben.</span><span class="sxs-lookup"><span data-stu-id="4ae45-134">To use the Windows Store collection API and the Windows Store purchase API to access ownership information for apps and add-ons, you need to enter the associated Azure AD client IDs here.</span></span> <span data-ttu-id="4ae45-135">Beachten Sie, dass es bis zu 16 Stunden dauern kann, bis diese Änderungen wirksam werden.</span><span class="sxs-lookup"><span data-stu-id="4ae45-135">Note that it may take up to 16 hours for these changes to take effect.</span></span>

<span data-ttu-id="4ae45-136">Weitere Informationen finden Sie unter [Verwalten von Produktansprüchen aus einem Dienst](../monetize/view-and-grant-products-from-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="4ae45-136">For more info, see [Manage product entitlements from a service](../monetize/view-and-grant-products-from-a-service.md).</span></span>

## <a name="app-management"></a><span data-ttu-id="4ae45-137">App-Verwaltung</span><span class="sxs-lookup"><span data-stu-id="4ae45-137">App management</span></span>

<span data-ttu-id="4ae45-138">Im Abschnitt **App-Verwaltung** können Sie Identitäts- und Paketdetails anzeigen sowie die Namen Ihrer App verwalten.</span><span class="sxs-lookup"><span data-stu-id="4ae45-138">The **App management** section lets you view identity and package details and manage names for your app.</span></span>

## <a name="app-identity"></a><span data-ttu-id="4ae45-139">App-Identität</span><span class="sxs-lookup"><span data-stu-id="4ae45-139">App identity</span></span>

<span data-ttu-id="4ae45-140">Diese Seite enthält die Details zur eindeutigen App-Identität im Store, einschließlich den URL(s) zur Verknüpfung der App mit dem App-Eintrag.</span><span class="sxs-lookup"><span data-stu-id="4ae45-140">This page shows you details related to your app's unique identity within the Store, including the URL(s) to link to your app's listing.</span></span>

<span data-ttu-id="4ae45-141">Weitere Informationen finden Sie unter [Anzeigen von Details zur App-Identität](view-app-identity-details.md).</span><span class="sxs-lookup"><span data-stu-id="4ae45-141">For more info, see [View app identity details](view-app-identity-details.md).</span></span>

## <a name="manage-app-names"></a><span data-ttu-id="4ae45-142">Verwalten von App-Namen</span><span class="sxs-lookup"><span data-stu-id="4ae45-142">Manage app names</span></span>

<span data-ttu-id="4ae45-143">Auf dieser Seite können Sie alle für Ihre App reservierten Namen anzeigen.</span><span class="sxs-lookup"><span data-stu-id="4ae45-143">This is where you can view all of the names that you've reserved for your app.</span></span> <span data-ttu-id="4ae45-144">Sie können hier auch zusätzliche Namen reservieren oder nicht mehr verwendete Namen löschen.</span><span class="sxs-lookup"><span data-stu-id="4ae45-144">You can reserve additional names here, or delete names you're no longer using.</span></span>

<span data-ttu-id="4ae45-145">Weitere Informationen finden Sie unter [Verwalten von App-Namen](manage-app-names.md).</span><span class="sxs-lookup"><span data-stu-id="4ae45-145">For more info, see [Manage app names](manage-app-names.md).</span></span>

## <a name="current-packages"></a><span data-ttu-id="4ae45-146">Aktuelle Pakete</span><span class="sxs-lookup"><span data-stu-id="4ae45-146">Current packages</span></span>

<span data-ttu-id="4ae45-147">Auf dieser Seite können Sie Details zu allen veröffentlichten Paketen anzeigen.</span><span class="sxs-lookup"><span data-stu-id="4ae45-147">This page lets you view details related to all of your published packages.</span></span>

> [!NOTE]
> <span data-ttu-id="4ae45-148">Hier werden erst Informationen angezeigt, wenn Ihre App veröffentlicht wurde.</span><span class="sxs-lookup"><span data-stu-id="4ae45-148">You won't see any info here until your app has been published.</span></span>

<span data-ttu-id="4ae45-149">Der Name, die Version und die Architektur der einzelnen Pakete werden angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4ae45-149">The name, version, and architecture of each package is shown.</span></span> <span data-ttu-id="4ae45-150">Klicken Sie auf **Details**, um zusätzliche Informationen wie z. B. unterstützte Sprache, App-Funktionen und Dateigrößen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="4ae45-150">Click **Details** to show additional info such as supported language, app capabilities, and file sizes.</span></span> <span data-ttu-id="4ae45-151">Welche Informationen jeweils für ein Paket angezeigt werden, variiert abhängig vom Zielbetriebssystem und anderen Faktoren.</span><span class="sxs-lookup"><span data-stu-id="4ae45-151">The info you see for each package may vary depending on its targeted operating system and other factors.</span></span> 

<span data-ttu-id="4ae45-152">Entwickler mit OEM-Berechtigungen können auf der Seite **Aktuelle Pakete** außerdem [Vorinstallationspakete generieren](generate-preinstall-packages-for-oems.md).</span><span class="sxs-lookup"><span data-stu-id="4ae45-152">Developers with OEM permissions can also [generate preinstall packages](generate-preinstall-packages-for-oems.md) from the **Current packages** page.</span></span>

 

 
