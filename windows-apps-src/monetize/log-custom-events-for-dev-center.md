---
author: Xansky
Description: You can log custom events from your UWP app and review those events in the Usage report in Partner Center.
title: Protokollieren benutzerdefinierter Ereignisse im Partner Center
ms.author: mhopkins
ms.date: 06/01/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Services-SDK, Ereignisse protokollieren
ms.assetid: 4aa591e0-c22a-4c90-b316-0b5d0410af19
ms.localizationpriority: medium
ms.openlocfilehash: 47c1eb02434dc71cb7da949d58ec38cf3b4cf65a
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7567476"
---
# <a name="log-custom-events-for-partner-center"></a><span data-ttu-id="168d7-103">Protokollieren benutzerdefinierter Ereignisse im Partner Center</span><span class="sxs-lookup"><span data-stu-id="168d7-103">Log custom events for Partner Center</span></span>

<span data-ttu-id="168d7-104">Der [Bericht "Nutzung"](https://msdn.microsoft.com/windows/uwp/publish/usage-report) im Partner Center können Sie Informationen zu benutzerdefinierten Ereignissen, die Sie in Ihrer app (universelle Windows Plattform) definiert haben.</span><span class="sxs-lookup"><span data-stu-id="168d7-104">The [Usage report](https://msdn.microsoft.com/windows/uwp/publish/usage-report) in Partner Center lets you get info about custom events that you've defined in your Universal Windows Platform (UWP) app.</span></span> <span data-ttu-id="168d7-105">Ein benutzerdefiniertes Ereignis ist eine beliebige Zeichenfolge, die ein Ereignis oder eine Aktivität in Ihrer App repräsentiert.</span><span class="sxs-lookup"><span data-stu-id="168d7-105">A custom event is an arbitrary string that represents an event or activity in your app.</span></span> <span data-ttu-id="168d7-106">Beispielsweise kann ein Spiel benutzerdefinierte Ereignisse mit den Bezeichnungen *FirstLevelPassed*, *SecondLevelPassed*usw. definieren, die protokolliert werden, wenn der Benutzer die einzelnen Levels des Spiels durchläuft.</span><span class="sxs-lookup"><span data-stu-id="168d7-106">For example, a game might define custom events named *firstLevelPassed*, *secondLevelPassed*, and so on, which are logged when the user passes each level in the game.</span></span>

<span data-ttu-id="168d7-107">Um ein benutzerdefiniertes Ereignis aus Ihrer App zu protokollieren, übergeben Sie die Zeichenfolge des benutzerdefinierten Ereignisses an die [Log](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicescustomeventlogger.log)-Methode des Microsoft Store Services SDK.</span><span class="sxs-lookup"><span data-stu-id="168d7-107">To log a custom event from your app, pass the custom event string to the [Log](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicescustomeventlogger.log) method provided by the Microsoft Store Services SDK.</span></span> <span data-ttu-id="168d7-108">Sie können alle Instanzen für Ihre benutzerdefinierten Ereignisse im Abschnitt **benutzerdefinierte Ereignisse** im [Bericht "Nutzung"](https://msdn.microsoft.com/windows/uwp/publish/usage-report) im Partner Center überprüfen.</span><span class="sxs-lookup"><span data-stu-id="168d7-108">You can review the total occurrences for your custom events in the **Custom events** section of the [Usage report](https://msdn.microsoft.com/windows/uwp/publish/usage-report) in Partner Center.</span></span>

> [!NOTE]
> <span data-ttu-id="168d7-109">Benutzerdefinierte Ereignisse, die Sie in das Partner Center anmelden, werden nicht im Zusammenhang mit [Windows-Ereignisse](https://msdn.microsoft.com/library/windows/desktop/aa964766.aspx), und sie werden nicht in der **Ereignisanzeige**angezeigt.</span><span class="sxs-lookup"><span data-stu-id="168d7-109">Custom events that you log to Partner Center are unrelated to [Windows events](https://msdn.microsoft.com/library/windows/desktop/aa964766.aspx), and they do not appear in **Event Viewer**.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="168d7-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="168d7-110">Prerequisites</span></span>

<span data-ttu-id="168d7-111">Bevor Sie benutzerdefinierte Protokollereignisse im **Bericht "Nutzung"** für Ihre app im Partner Center überprüfen können, muss Ihre app im Store veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="168d7-111">Before you can review custom logging events in the **Usage report** for your app in Partner Center, your app must be published in the Store.</span></span>

## <a name="how-to-log-custom-events"></a><span data-ttu-id="168d7-112">Protokollieren von benutzerdefinierten Ereignissen</span><span class="sxs-lookup"><span data-stu-id="168d7-112">How to log custom events</span></span>

1. <span data-ttu-id="168d7-113">Falls noch nicht geschehen, [installieren Sie das Microsoft Store Services SDK](microsoft-store-services-sdk.md#install-the-sdk) auf Ihrem Entwicklungscomputer.</span><span class="sxs-lookup"><span data-stu-id="168d7-113">If you have not done so already, [Install the Microsoft Store Services SDK](microsoft-store-services-sdk.md#install-the-sdk) on your development computer.</span></span>

2. <span data-ttu-id="168d7-114">Öffnen Sie das Projekt in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="168d7-114">Open your project in Visual Studio.</span></span>

3. <span data-ttu-id="168d7-115">Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Knoten **Verweise** für Ihr Projekt, und wählen Sie anschließend **Verweis hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="168d7-115">In Solution Explorer, right-click the **References** node for your project and click **Add Reference**.</span></span>

4. <span data-ttu-id="168d7-116">Erweitern Sie im **Verweis-Manager** die Option **Universelle Windows-App**, und klicken Sie auf **Erweiterungen**.</span><span class="sxs-lookup"><span data-stu-id="168d7-116">In **Reference Manager**, expand **Universal Windows** and click **Extensions**.</span></span>

5. <span data-ttu-id="168d7-117">Klicken Sie in der Liste der SDKs auf das Kontrollkästchen neben **Microsoft Engagement Framework** und anschließend auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="168d7-117">In the list of SDKs, click the check box next to **Microsoft Engagement Framework** and click **OK**.</span></span>

6. <span data-ttu-id="168d7-118">Fügen Sie die folgende Anweisung am Anfang jeder Codedatei hinzu, in der Sie benutzerdefinierte Ereignisse protokollieren möchten.</span><span class="sxs-lookup"><span data-stu-id="168d7-118">Add the following statement to the top of each code file where you want to log custom events.</span></span>
    [!code-cs[EventLogger](./code/StoreSDKSamples/cs/LogEvents.cs#EngagementNamespace)]

7. <span data-ttu-id="168d7-119">Rufen Sie in jedem Abschnittdes Codes, in dem Sie ein benutzerdefiniertes Ereignis protokollieren möchten, ein [StoreServicesCustomEventLogger](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicescustomeventlogger.log)-Objekt ab, und rufen Sie dann die [Protokoll](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicescustomeventlogger.log)-Methode auf.</span><span class="sxs-lookup"><span data-stu-id="168d7-119">In each section of your code where you want to log a custom event, get a [StoreServicesCustomEventLogger](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicescustomeventlogger.log) object and then call the [Log](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicescustomeventlogger.log) method.</span></span> <span data-ttu-id="168d7-120">Übergeben Sie die Zeichenfolge für das benutzerdefinierte Ereignis an die Methode.</span><span class="sxs-lookup"><span data-stu-id="168d7-120">Pass your custom event string to the method.</span></span>
    [!code-cs[EventLogger](./code/StoreSDKSamples/cs/LogEvents.cs#Log)]

    > [!NOTE]
    > <span data-ttu-id="168d7-121">Möglicherweise dauert das Laden des [Nutzungsberichts](https://msdn.microsoft.com/windows/uwp/publish/usage-report) lange, wenn Ihre App viele benutzerdefinierte Ereignisse mit langen Namen protokolliert.</span><span class="sxs-lookup"><span data-stu-id="168d7-121">The [Usage report](https://msdn.microsoft.com/windows/uwp/publish/usage-report) may take a long time to load if your app logs many custom events with long names.</span></span> <span data-ttu-id="168d7-122">Es wird empfohlen, dass kurze Namen für Ihre benutzerdefinierten Ereignisse zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="168d7-122">We recommend that you use brief names for your custom events.</span></span> 

## <a name="related-topics"></a><span data-ttu-id="168d7-123">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="168d7-123">Related topics</span></span>

* [<span data-ttu-id="168d7-124">Nutzungsbericht</span><span class="sxs-lookup"><span data-stu-id="168d7-124">Usage report</span></span>](https://msdn.microsoft.com/windows/uwp/publish/usage-report)
* [<span data-ttu-id="168d7-125">Protokollierungsmethode</span><span class="sxs-lookup"><span data-stu-id="168d7-125">Log method</span></span>](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicescustomeventlogger.log)
* [<span data-ttu-id="168d7-126">Microsoft Store Services SDK</span><span class="sxs-lookup"><span data-stu-id="168d7-126">Microsoft Store Services SDK</span></span>](https://msdn.microsoft.com/windows/uwp/monetize/microsoft-store-services-sdk)
