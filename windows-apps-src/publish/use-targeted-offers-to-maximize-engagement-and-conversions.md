---
author: JnHs
Description: Target specific segments of your customers with personalized content to increase engagement, retention, and monetization.
title: Verwenden Sie gezielte Angebote, um Interaktionen und Abschlüsse zu maximieren.
ms.author: wdg-dev-content
ms.date: 11/10/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, gezielte Angebote, Angebote, Benachrichtigungen
ms.localizationpriority: medium
ms.openlocfilehash: 727c438bacf51fd2ead03df72421363116c4701b
ms.sourcegitcommit: 49aab071aa2bd88f1c165438ee7e5c854b3e4f61
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2018
ms.locfileid: "4462531"
---
# <a name="use-targeted-offers-to-maximize-engagement-and-conversions"></a><span data-ttu-id="86cd2-103">Verwenden Sie gezielte Angebote, um Interaktionen und Abschlüsse zu maximieren.</span><span class="sxs-lookup"><span data-stu-id="86cd2-103">Use targeted offers to maximize engagement and conversions</span></span>

<span data-ttu-id="86cd2-104">Sprechen Sie für bessere Interaktion, Kundenbindung und Monetarisierung bestimmte Segmente Ihrer Kunden mit attraktivem, personalisiertem Inhalt an.</span><span class="sxs-lookup"><span data-stu-id="86cd2-104">Target specific segments of your customers with attractive, personalized content to increase engagement, retention, and monetization.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86cd2-105">Zielgerichtete Angebote können nur mit UWP-Apps verwendet werden, die Add-Ons enthalten.</span><span class="sxs-lookup"><span data-stu-id="86cd2-105">Targeted offers can only be used with UWP apps that include add-ons.</span></span>

## <a name="targeted-offer-overview"></a><span data-ttu-id="86cd2-106">Übersicht über zielgerichtete Angebote</span><span class="sxs-lookup"><span data-stu-id="86cd2-106">Targeted offer overview</span></span>

<span data-ttu-id="86cd2-107">Allgemein gesagt müssen Sie drei durchführen, um die zielgerichteten Angebote zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="86cd2-107">At a high level, you need to do three things to use targeted offers:</span></span>

1. **<span data-ttu-id="86cd2-108">Erstellen Sie das Angebot auf Ihrem Dashboard.</span><span class="sxs-lookup"><span data-stu-id="86cd2-108">Create the offer in your dashboard.</span></span>** <span data-ttu-id="86cd2-109">Navigieren Sie zur Seite **Bewerben > zielgerichtete Angebote**, um Angebote zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="86cd2-109">Navigate to the **Engage > Targeted offers** page to create offers.</span></span> <span data-ttu-id="86cd2-110">Weitere Informationen zu diesem Prozess sind im Folgenden beschrieben.</span><span class="sxs-lookup"><span data-stu-id="86cd2-110">More info about this process is described below.</span></span>
2. **<span data-ttu-id="86cd2-111">Implementieren Sie das In-App-Angebot.</span><span class="sxs-lookup"><span data-stu-id="86cd2-111">Implement the in-app offer experience.</span></span>** <span data-ttu-id="86cd2-112">Verwenden Sie die *Microsoft Store für gezielte Angebote API* in Ihrem app Code, um die verfügbaren Angebote für einen bestimmten Benutzer abzurufen.</span><span class="sxs-lookup"><span data-stu-id="86cd2-112">Use the *Microsoft Store targeted offers API* in your app's code to retrieve the available offers for a given user.</span></span> <span data-ttu-id="86cd2-113">Sie müssen auch die In-App-Umgebung für das gezielte Angebot erstellen.</span><span class="sxs-lookup"><span data-stu-id="86cd2-113">You'll also need to create the in-app experience for the targeted offer.</span></span> <span data-ttu-id="86cd2-114">Weitere Informationen finden Sie unter [Verwalten gezielter Angebote mithilfe von Store-Diensten](../monetize/manage-targeted-offers-using-windows-store-services.md).</span><span class="sxs-lookup"><span data-stu-id="86cd2-114">For more info, see [Manage targeted offers using Store services](../monetize/manage-targeted-offers-using-windows-store-services.md).</span></span>
3. **<span data-ttu-id="86cd2-115">Übermitteln Ihrer App an den Store.</span><span class="sxs-lookup"><span data-stu-id="86cd2-115">Submit your app to the Store.</span></span>** <span data-ttu-id="86cd2-116">Ihre App muss mit dem integrierten In-App-Angebot veröffentlicht werden, damit die Angebote für Kunden verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="86cd2-116">Your app must be published with the in-app offer experience in place in order for the offer(s) be made available to customers.</span></span>

<span data-ttu-id="86cd2-117">Nachdem Sie diese Schritte abgeschlossen haben, werden Kunden, die Ihre App verwenden, die Angebote angezeigt, die zu diesem Zeitpunkt für ihn verfügbar sind, basierend auf seiner Mitgliedschaft in dem diesem Angebot zugeordneten Segment.</span><span class="sxs-lookup"><span data-stu-id="86cd2-117">After you complete these steps, customers using your app will see the offers that are available to them at that time, based in their membership in the segment(s) associated with your offers.</span></span> <span data-ttu-id="86cd2-118">Beachten Sie, dass wir zwar bemüht sind, alle verfügbaren Angebote für Ihre Kunden anzuzeigen, es jedoch gelegentlich zu Problemen kommen kann, die die Angebotsverfügbarkeit beeinträchtigen.</span><span class="sxs-lookup"><span data-stu-id="86cd2-118">Please note that while we’ll make every effort to show all available offers to your customers, there may occasionally be issues that impact offer availability.</span></span>


## <a name="to-create-and-send-a-targeted-offer"></a><span data-ttu-id="86cd2-119">So erstellen und senden Sie ein gezieltes Angebot</span><span class="sxs-lookup"><span data-stu-id="86cd2-119">To create and send a targeted offer</span></span>

<span data-ttu-id="86cd2-120">Führen Sie diese Schritte aus, um ein gezieltes Angebot im Dashboard zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="86cd2-120">Follow these steps to create a targeted offer in the dashboard.</span></span>

1.  <span data-ttu-id="86cd2-121">Erweitern Sie im Windows Dev Center-Dashboard **Einbeziehen** im linken Navigationsmenü und wählen Sie dann **zielgerichtete Angebote** aus.</span><span class="sxs-lookup"><span data-stu-id="86cd2-121">In the Windows Dev Center dashboard, expand **Engage** in the left navigation menu, then select **Targeted offers**.</span></span>
2.  <span data-ttu-id="86cd2-122">Überprüfen Sie auf der Seite **zielgerichtete Angebote** die verfügbaren Angebote.</span><span class="sxs-lookup"><span data-stu-id="86cd2-122">On the **Targeted offers** page, review the available offers.</span></span> <span data-ttu-id="86cd2-123">Wählen Sie **Create new offer** für ein Angebot, das Sie implementieren möchten.</span><span class="sxs-lookup"><span data-stu-id="86cd2-123">Select **Create new offer** for any offer you wish to implement.</span></span>

    > [!NOTE]
    > <span data-ttu-id="86cd2-124">Die angezeigten verfügbaren Angebote ändern sich im Laufe der Zeit und auf der Grundlage von Kontokriterien.</span><span class="sxs-lookup"><span data-stu-id="86cd2-124">The available offers you will see may vary over time and based on account criteria.</span></span>

3.  <span data-ttu-id="86cd2-125">Wählen Sie in der neuen Zeile, die unter den verfügbaren Angebote angezeigt wird, das Produkt (App) aus, in dem das Angebot zur Verfügung steht.</span><span class="sxs-lookup"><span data-stu-id="86cd2-125">In the new row that appears below the available offers, choose the product (app) in which the offer will be available.</span></span> <span data-ttu-id="86cd2-126">Wählen Sie dann das Add-On aus, das Sie dem Angebot zuordnen möchten.</span><span class="sxs-lookup"><span data-stu-id="86cd2-126">Then, select the add-on that you want to associate with the offer.</span></span>
4.  <span data-ttu-id="86cd2-127">Wiederholen Sie die Schritte2 und 3, wenn Sie weitere Angebote erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="86cd2-127">Repeat steps 2 and 3 if you'd like to create additional offers.</span></span> <span data-ttu-id="86cd2-128">Sie können den gleichen Angebotstyp mehrmals in derselben App implementieren, solange Sie für jedes Angebot andere Add-Ons auswählen.</span><span class="sxs-lookup"><span data-stu-id="86cd2-128">You can implement the same offer type more than once for the same app, as long as you select different add-ons for each offer.</span></span> <span data-ttu-id="86cd2-129">Darüber hinaus können Sie das gleiche Add-On mehr als einem Angebotstyp zuordnen.</span><span class="sxs-lookup"><span data-stu-id="86cd2-129">Additionally, you can associate the same add-on with more than one offer type.</span></span>
5.  <span data-ttu-id="86cd2-130">Klicken Sie auf **Speichern**, wenn Sie mit dem Erstellen der Angebote fertig sind.</span><span class="sxs-lookup"><span data-stu-id="86cd2-130">When you are finished creating offers, click **Save**.</span></span>

<span data-ttu-id="86cd2-131">Nachdem Sie Ihr Angebot implementiert haben, können Sie die Gesamtanzahl von Abschlüssen für jedes Angebot auf der Seite **Zielgerichtete Angebote** in Ihrem Dashboard anzeigen.</span><span class="sxs-lookup"><span data-stu-id="86cd2-131">After you've implemented your offers, you can return to the **Targeted offers** page in your dashboard to view the total conversions for each offer.</span></span>

<span data-ttu-id="86cd2-132">Wenn Sie sich entscheiden, kein Angebot zu verwenden (oder wenn Sie es nicht mehr verwenden möchten), klicken Sie auf **Löschen**.</span><span class="sxs-lookup"><span data-stu-id="86cd2-132">If you decide not to use an offer (or if you no longer want to keep using it, click **Delete.**</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86cd2-133">Achten Sie darauf, dass Sie den Code veröffentlichen, um die verfügbaren Angebote für einen bestimmten Benutzer abzurufen und die In-App-Umgebung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="86cd2-133">Be sure you have published the code to retrieve the available offers for a given user, and to create the in-app experience.</span></span> <span data-ttu-id="86cd2-134">Weitere Informationen finden Sie unter [Verwalten gezielter Angebote mithilfe von Store-Diensten](../monetize/manage-targeted-offers-using-windows-store-services.md).</span><span class="sxs-lookup"><span data-stu-id="86cd2-134">For more info, see [Manage targeted offers using Store services](../monetize/manage-targeted-offers-using-windows-store-services.md).</span></span>
>
> <span data-ttu-id="86cd2-135">Beachten Sie bei den Inhalten gezielter Angebote, dass sie wie der gesamte App-Inhalt die [Inhaltsrichtlinien](https://docs.microsoft.com/en-us/legal/windows/agreements/store-policies) des Stores erfüllen müssen.</span><span class="sxs-lookup"><span data-stu-id="86cd2-135">When considering the content of your targeted offers, keep in mind that, as with all app content, the content in your offers must comply with the Store [Content Policies](https://docs.microsoft.com/en-us/legal/windows/agreements/store-policies).</span></span>
>
> <span data-ttu-id="86cd2-136">Beachten Sie außerdem Folgendes: Wenn ein Kunde, der Ihre App verwendet (und zum Zeitpunkt, zu dem die Segmentmitgliedschaft bestimmt wird, mit seinem Microsoft-Konto angemeldet ist) das Gerät später an eine andere Person übergibt, sieht die andere Person unter Umständen das Angebot, das für den ursprünglichen Kunden bestimmt war.</span><span class="sxs-lookup"><span data-stu-id="86cd2-136">Also be aware that if a customer who uses your app (and is signed in with their Microsoft account at the time the segment membership is determined) gives their device to someone else to use, the other person may see offers that were targeted at the original customer.</span></span>
