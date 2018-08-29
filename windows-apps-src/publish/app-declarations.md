---
author: jnHs
Description: Product declarations help make sure your app is displayed appropriately in the Microsoft Store and offered to the right set of customers.
title: Produktdeklarationen
ms.assetid: 3AF618F3-2B47-4A57-B7E8-1DF979D4A82C
ms.author: wdg-dev-content
ms.date: 12/05/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 959e056d5edf5e1fe7a1c51a2f855c9e11512cb0
ms.sourcegitcommit: 3727445c1d6374401b867c78e4ff8b07d92b7adc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2018
ms.locfileid: "2918811"
---
# <a name="product-declarations"></a><span data-ttu-id="93423-103">Produktdeklarationen</span><span class="sxs-lookup"><span data-stu-id="93423-103">Product declarations</span></span>

<span data-ttu-id="93423-104">Abschnitt **produktdeklarationen** der [Eigenschaftenseite des [Übermittlungsprozesses](app-submissions.md) ](enter-app-properties.md) hilft dabei, stellen Sie sicher, dass Ihre app entsprechend angezeigt und die richtigen Kunden und hilft ihnen verstehen, wie sie Ihre app verwenden können angeboten wird.</span><span class="sxs-lookup"><span data-stu-id="93423-104">The **Product declarations** section of the [Properties](enter-app-properties.md) page of the [submission process](app-submissions.md) helps make sure your app is displayed appropriately and offered to the right set of customers, and helps them understand how they can use your app.</span></span>

<span data-ttu-id="93423-105">Den folgenden Abschnitten werden einige der Deklarationen und was Sie bei der Entscheidung, ob sich eine Deklaration für Ihre app gilt berücksichtigen müssen.</span><span class="sxs-lookup"><span data-stu-id="93423-105">The following sections describe some of the declarations and what you need to consider when determining whether each declaration applies to your app.</span></span> <span data-ttu-id="93423-106">Beachten Sie, dass zwei dieser Deklarationen standardmäßig aktiviert sind (wie unten beschrieben). Je nach Kategorie des Produkts können Sie auch zusätzliche Deklarationen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="93423-106">Note that two of these declarations are checked by default (as described below.) Depending on your product's category, you may also see additional declarations.</span></span> <span data-ttu-id="93423-107">Achten Sie darauf, dass der Deklarationen überprüfen und sicherzustellen, dass sie Ihre Übermittlung genau wiedergeben.</span><span class="sxs-lookup"><span data-stu-id="93423-107">Be sure to review all of the declarations and ensure they accurately reflect your submission.</span></span>

## <a name="this-app-allows-users-to-make-purchases-but-does-not-use-the-microsoft-store-commerce-system"></a><span data-ttu-id="93423-108">Diese app ermöglicht es Benutzern, Einkäufe zu tätigen, verwendet jedoch nicht die Microsoft Store-e-Commerce-Systems.</span><span class="sxs-lookup"><span data-stu-id="93423-108">This app allows users to make purchases, but does not use the Microsoft Store commerce system.</span></span>

<span data-ttu-id="93423-109">Nahezu jede Übermittlung sollten Sie diese Option deaktiviert lassen, seit apps, die Möglichkeiten zum Kauf anbieten müssen Elementen, die sind oder können verbraucht oder innerhalb Ihrer app verwendet die Microsoft Store in-app-Einkaufs-API zum Erstellen und Übermitteln von Add-ons verwenden.</span><span class="sxs-lookup"><span data-stu-id="93423-109">For nearly every submission, you should leave this box unchecked, since apps which offer opportunities to purchase items which are or can be consumed or used within your app must use the Microsoft Store in-app purchase API to create and submit the add-ons.</span></span> <span data-ttu-id="93423-110">Gemäß der [Vereinbarung für App-Entwickler](https://docs.microsoft.com/legal/windows/agreements/app-developer-agreement)könnte apps, die erstellt und vor 29 Juni 2015 eingereicht wurden, weiterhin in-app-einkauffunktionalität anbieten, ohne Verwendung des Microsoft-e-Commerce-Engine, solange die einkaufsfunktionalität die [aber Microsoft Store-Richtlinien](https://docs.microsoft.com/legal/windows/agreements/store-policies#108-financial-transactions).</span><span class="sxs-lookup"><span data-stu-id="93423-110">Per the [App Developer Agreement](https://docs.microsoft.com/legal/windows/agreements/app-developer-agreement), apps that were created and submitted prior to June 29, 2015, could continue to offer in-app purchasing functionality without using Microsoft's commerce engine, so long as the purchase functionality complies with the [Microsoft Store Policies](https://docs.microsoft.com/legal/windows/agreements/store-policies#108-financial-transactions).</span></span> <span data-ttu-id="93423-111">Wenn dies auf Ihre App zutrifft, müssen Sie dieses Kontrollkästchen aktivieren.</span><span class="sxs-lookup"><span data-stu-id="93423-111">If this applies to your app, you must check this box.</span></span> <span data-ttu-id="93423-112">Lassen Sie das Kontrollkästchen andernfalls deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="93423-112">Otherwise, leave it unchecked.</span></span>

## <a name="this-app-has-been-tested-to-meet-accessibility-guidelines"></a><span data-ttu-id="93423-113">Diese App wurde auf Einhaltung der Richtlinien zur Barrierefreiheit getestet.</span><span class="sxs-lookup"><span data-stu-id="93423-113">This app has been tested to meet accessibility guidelines.</span></span>

<span data-ttu-id="93423-114">Wenn Sie dieses Kontrollkästchen aktivieren, kann die App von Kunden gefunden werden, die im Store speziell nach barrierefreien Apps suchen.</span><span class="sxs-lookup"><span data-stu-id="93423-114">Checking this box makes your app discoverable to customers who are specifically looking for accessible apps in the Store.</span></span>

<span data-ttu-id="93423-115">Sie sollten dieses Kontrollkästchen erst aktivieren, nachdem Sie die folgenden Schritte erledigt haben:</span><span class="sxs-lookup"><span data-stu-id="93423-115">You should only check this box if you have done all of the following items:</span></span>

-   <span data-ttu-id="93423-116">Alle relevanten Barrierefreiheitsinfos für UI-Elemente festlegen, z.B. barrierefreie Namen</span><span class="sxs-lookup"><span data-stu-id="93423-116">Set all the relevant accessibility info for UI elements, such as accessible names.</span></span>
-   <span data-ttu-id="93423-117">Tastaturnavigation und -vorgänge unter Berücksichtigung der Registerkartenreihenfolge, Tastaturaktivierung, Navigation mit Pfeiltasten und Tastenkombinationen implementieren</span><span class="sxs-lookup"><span data-stu-id="93423-117">Implemented keyboard navigation and operations, taking into account tab order, keyboard activation, arrow keys navigation, shortcuts.</span></span>
-   <span data-ttu-id="93423-118">Barrierefreie visuelle Darstellung sicherstellen, z. B. durch Berücksichtigen eines Textkontrastverhältnisses von 4,5:1 (und nicht nur durch die Verwendung farblich gekennzeichneter Informationen)</span><span class="sxs-lookup"><span data-stu-id="93423-118">Ensured an accessible visual experience by including such things as a 4.5:1 text contrast ratio, and don't rely on color alone to convey info to the user.</span></span>
-   <span data-ttu-id="93423-119">Tools zum Testen der Barrierefreiheit verwenden, z.B. Inspect oder AccChecker, um Ihre App zu überprüfen und alle von diesen Tools ermittelten Fehler mit hoher Priorität zu beheben</span><span class="sxs-lookup"><span data-stu-id="93423-119">Used accessibility testing tools, such as Inspect or AccChecker, to verify your app, and resolve all high-priority errors detected by those tools.</span></span>
-   <span data-ttu-id="93423-120">Die wichtigsten Szenarien der App unter Verwendung von Funktionen und Tools wie „Sprachausgabe“, „Bildschirmlupe“, „Bildschirmtastatur“, „Hoher Kontrast“ und „Hoher DPI-Wert“ vollständig überprüfen</span><span class="sxs-lookup"><span data-stu-id="93423-120">Verified the app’s key scenarios from end to end using such facilities and tools as Narrator, Magnifier, On Screen Keyboard, High Contrast, and High DPI.</span></span>

<span data-ttu-id="93423-121">Wenn Sie Ihre App als barrierefrei ausweisen, erklären Sie ausdrücklich, dass Ihre App eine Barrierefreiheit für alle Kunden aufweist, einschließlich für Personen mit Behinderungen.</span><span class="sxs-lookup"><span data-stu-id="93423-121">When you declare your app as accessible, you agree that your app is accessible to all customers, including those with disabilities.</span></span> <span data-ttu-id="93423-122">Das bedeutet beispielsweise, dass Sie die App im Modus mit hohem Kontrast und die Sprachausgabe getestet haben.</span><span class="sxs-lookup"><span data-stu-id="93423-122">For example, this means you have tested the app with high-contrast mode and with a screen reader.</span></span> <span data-ttu-id="93423-123">Sie haben außerdem sichergestellt, dass die Benutzeroberfläche ordnungsgemäß mit der Tastatur, der Bildschirmlupe und weiteren Tools zur Unterstützung der Barrierefreiheit funktioniert.</span><span class="sxs-lookup"><span data-stu-id="93423-123">You've also verified that the user interface functions correctly with a keyboard, the Magnifier, and other accessibility tools.</span></span>

<span data-ttu-id="93423-124">Weitere Informationen finden Sie unter [Bedienungshilfen](../design/accessibility/accessibility.md), [zum Testen der Barrierefreiheit](../design/accessibility/accessibility-testing.md)und [Barrierefreiheit im Store](../design/accessibility/accessibility-in-the-store.md).</span><span class="sxs-lookup"><span data-stu-id="93423-124">For more info, see [Accessibility](../design/accessibility/accessibility.md), [Accessibility testing](../design/accessibility/accessibility-testing.md), and [Accessibility in the Store](../design/accessibility/accessibility-in-the-store.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="93423-125">Weisen Sie die App nur dann als barrierefrei aus, wenn Sie sie ausdrücklich für diesen Zweck entwickelt und getestet haben.</span><span class="sxs-lookup"><span data-stu-id="93423-125">Don't list your app as accessible unless you have specifically engineered and tested it for that purpose.</span></span> <span data-ttu-id="93423-126">Falls Ihre App als barrierefrei ausgewiesen ist, jedoch eigentlich keine Barrierefreiheit unterstützt, werden Sie wahrscheinlich negatives Feedback von der Community erhalten.</span><span class="sxs-lookup"><span data-stu-id="93423-126">If your app is declared as accessible, but it doesn’t actually support accessibility, you'll probably receive negative feedback from the community.</span></span>

## <a name="customers-can-install-this-app-to-alternate-drives-or-removable-storage"></a><span data-ttu-id="93423-127">Kunden können diese App auf alternativen Laufwerken oder Wechselmedien installieren.</span><span class="sxs-lookup"><span data-stu-id="93423-127">Customers can install this app to alternate drives or removable storage.</span></span>

<span data-ttu-id="93423-128">Dieses Kontrollkästchen ist standardmäßig aktiviert, damit Kunden Ihre app für externe oder auf Wechseldatenträgern zu installieren, die wie etwa einer SD-Karte oder auf einem systemfremden Volumelaufwerk wie einem externen Laufwerk zu steuern.</span><span class="sxs-lookup"><span data-stu-id="93423-128">This box is checked by default, to allow customers to install your app to external or removable storage media such as an SD card, or to a non-system volume drive such as an external drive.</span></span> <span data-ttu-id="93423-129">(Für Windows Phone 8.1 wurde dies zuvor über "storemanifest.xml" angegeben.)</span><span class="sxs-lookup"><span data-stu-id="93423-129">(For Windows Phone 8.1, this was previously indicated via StoreManifest.xml.)</span></span>

<span data-ttu-id="93423-130">Wenn Sie verhindern, dass Ihre app auf alternativen Laufwerken oder Wechselmedien installiert wird, und nur die Installation auf die interne Festplatte auf dem Gerät zulassen möchten, deaktivieren Sie dieses Kontrollkästchen.</span><span class="sxs-lookup"><span data-stu-id="93423-130">If you want to prevent your app from being installed to alternate drives or removable storage, and only allow installation to the internal hard drive on their device, uncheck this box.</span></span>

<span data-ttu-id="93423-131">Beachten Sie, dass keine Option zum Einschränken der Installation eine app kann *nur* werden auf Wechselmedien installiert.</span><span class="sxs-lookup"><span data-stu-id="93423-131">Note that there is no option to restrict installation so that an app can *only* be installed to removable storage media.</span></span>


## <a name="windows-can-include-this-apps-data-in-automatic-backups-to-onedrive"></a><span data-ttu-id="93423-132">Windows kann die Daten dieser App in automatische Sicherungen auf OneDrive einschließen.</span><span class="sxs-lookup"><span data-stu-id="93423-132">Windows can include this app's data in automatic backups to OneDrive.</span></span>

<span data-ttu-id="93423-133">Dieses Kontrollkästchen ist standardmäßig aktiviert, damit die Daten Ihrer App eingeschlossen werden können, wenn ein Kunde automatische OneDrive-Sicherungen von Windows erstellen lässt.</span><span class="sxs-lookup"><span data-stu-id="93423-133">This box is checked by default, to allow your app's data to be included when a customer chooses to have Windows make automated backups to OneDrive.</span></span> <span data-ttu-id="93423-134">(Für Windows Phone 8.1 wurde dies zuvor über "storemanifest.xml" angegeben.)</span><span class="sxs-lookup"><span data-stu-id="93423-134">(For Windows Phone 8.1, this was previously indicated via StoreManifest.xml.)</span></span>

<span data-ttu-id="93423-135">Wenn Sie verhindern möchten, dass die App-Daten in automatische Sicherungen eingeschlossen werden, deaktivieren Sie das Kontrollkästchen.</span><span class="sxs-lookup"><span data-stu-id="93423-135">If you want to prevent your app's data from being included in automated backups, uncheck this box.</span></span>


## <a name="this-app-sends-kinect-data-to-external-services"></a><span data-ttu-id="93423-136">Diese app sendet Kinect-Daten an externe Dienste.</span><span class="sxs-lookup"><span data-stu-id="93423-136">This app sends Kinect data to external services.</span></span> 

<span data-ttu-id="93423-137">Wenn Ihre app Kinect-Daten verwendet und sie an einem externen-Dienst sendet, müssen Sie dieses Kontrollkästchen aktivieren.</span><span class="sxs-lookup"><span data-stu-id="93423-137">If your app uses Kinect data and sends it to any external service, you must check this box.</span></span>



 

 

 




