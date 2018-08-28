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
ms.sourcegitcommit: 9a17266f208ec415fc718e5254d5b4c08835150c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2018
ms.locfileid: "2888805"
---
# <a name="product-declarations"></a><span data-ttu-id="e68ce-103">Produktdeklarationen</span><span class="sxs-lookup"><span data-stu-id="e68ce-103">Product declarations</span></span>

<span data-ttu-id="e68ce-104">**Produkt** Deklarationsabschnitt der [Eigenschaftenseite des [den Prozess zum Absenden](app-submissions.md) ](enter-app-properties.md) kann, stellen Sie sicher, Ihre app entsprechend angezeigt und Angeboten den richtigen Satz von Kunden und hilft ihnen verstehen, wie sie Ihre app verwenden können.</span><span class="sxs-lookup"><span data-stu-id="e68ce-104">The **Product declarations** section of the [Properties](enter-app-properties.md) page of the [submission process](app-submissions.md) helps make sure your app is displayed appropriately and offered to the right set of customers, and helps them understand how they can use your app.</span></span>

<span data-ttu-id="e68ce-105">In den folgenden Abschnitten werden einige der Deklarationen und was Sie benötigen, beachten Sie beim bestimmen, ob jede Deklaration für Ihre app gilt beschrieben.</span><span class="sxs-lookup"><span data-stu-id="e68ce-105">The following sections describe some of the declarations and what you need to consider when determining whether each declaration applies to your app.</span></span> <span data-ttu-id="e68ce-106">Beachten Sie, dass zwei dieser Deklarationen standardmäßig überprüft werden (siehe die nachfolgende Beschreibung). Je nach Ihrer Produktkategorie sehen Sie auch zusätzliche Deklarationen.</span><span class="sxs-lookup"><span data-stu-id="e68ce-106">Note that two of these declarations are checked by default (as described below.) Depending on your product's category, you may also see additional declarations.</span></span> <span data-ttu-id="e68ce-107">Achten Sie darauf, überprüfen Sie die Deklarationen und sicherstellen, dass sie Ihre Bereitstellung genau widerspiegeln.</span><span class="sxs-lookup"><span data-stu-id="e68ce-107">Be sure to review all of the declarations and ensure they accurately reflect your submission.</span></span>

## <a name="this-app-allows-users-to-make-purchases-but-does-not-use-the-microsoft-store-commerce-system"></a><span data-ttu-id="e68ce-108">Diese app ermöglicht es Benutzern, Einkäufe tätigen, aber Microsoft Store-Commerce-System wird nicht verwendet.</span><span class="sxs-lookup"><span data-stu-id="e68ce-108">This app allows users to make purchases, but does not use the Microsoft Store commerce system.</span></span>

<span data-ttu-id="e68ce-109">Für die fast jeder Übermittlung sollten Sie dieses Kontrollkästchen deaktiviert lassen, seit apps, die Möglichkeiten zum Kauf anbieten müssen Elementen, die sind oder können verbraucht oder Ihrer App verwendet den Microsoft Store-app-Einkauf API verwenden, um erstellen und senden die Add-ons.</span><span class="sxs-lookup"><span data-stu-id="e68ce-109">For nearly every submission, you should leave this box unchecked, since apps which offer opportunities to purchase items which are or can be consumed or used within your app must use the Microsoft Store in-app purchase API to create and submit the add-ons.</span></span> <span data-ttu-id="e68ce-110">Pro [App Developer Vereinbarung](https://docs.microsoft.com/legal/windows/agreements/app-developer-agreement)konnte apps, die erstellt und vor dem 29 Juni 2015 übermittelt wurden weiterhin-app-Einkauf Funktionen anbieten ohne Verwendung von Microsoft Commerce-Moduls, solange die Bestellung Funktionalität der [entspricht Richtlinien für Microsoft](https://docs.microsoft.com/legal/windows/agreements/store-policies#108-financial-transactions).</span><span class="sxs-lookup"><span data-stu-id="e68ce-110">Per the [App Developer Agreement](https://docs.microsoft.com/legal/windows/agreements/app-developer-agreement), apps that were created and submitted prior to June 29, 2015, could continue to offer in-app purchasing functionality without using Microsoft's commerce engine, so long as the purchase functionality complies with the [Microsoft Store Policies](https://docs.microsoft.com/legal/windows/agreements/store-policies#108-financial-transactions).</span></span> <span data-ttu-id="e68ce-111">Wenn dies auf Ihre App zutrifft, müssen Sie dieses Kontrollkästchen aktivieren.</span><span class="sxs-lookup"><span data-stu-id="e68ce-111">If this applies to your app, you must check this box.</span></span> <span data-ttu-id="e68ce-112">Lassen Sie das Kontrollkästchen andernfalls deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="e68ce-112">Otherwise, leave it unchecked.</span></span>

## <a name="this-app-has-been-tested-to-meet-accessibility-guidelines"></a><span data-ttu-id="e68ce-113">Diese App wurde auf Einhaltung der Richtlinien zur Barrierefreiheit getestet.</span><span class="sxs-lookup"><span data-stu-id="e68ce-113">This app has been tested to meet accessibility guidelines.</span></span>

<span data-ttu-id="e68ce-114">Wenn Sie dieses Kontrollkästchen aktivieren, kann die App von Kunden gefunden werden, die im Store speziell nach barrierefreien Apps suchen.</span><span class="sxs-lookup"><span data-stu-id="e68ce-114">Checking this box makes your app discoverable to customers who are specifically looking for accessible apps in the Store.</span></span>

<span data-ttu-id="e68ce-115">Sie sollten dieses Kontrollkästchen erst aktivieren, nachdem Sie die folgenden Schritte erledigt haben:</span><span class="sxs-lookup"><span data-stu-id="e68ce-115">You should only check this box if you have done all of the following items:</span></span>

-   <span data-ttu-id="e68ce-116">Alle relevanten Barrierefreiheitsinfos für UI-Elemente festlegen, z.B. barrierefreie Namen</span><span class="sxs-lookup"><span data-stu-id="e68ce-116">Set all the relevant accessibility info for UI elements, such as accessible names.</span></span>
-   <span data-ttu-id="e68ce-117">Tastaturnavigation und -vorgänge unter Berücksichtigung der Registerkartenreihenfolge, Tastaturaktivierung, Navigation mit Pfeiltasten und Tastenkombinationen implementieren</span><span class="sxs-lookup"><span data-stu-id="e68ce-117">Implemented keyboard navigation and operations, taking into account tab order, keyboard activation, arrow keys navigation, shortcuts.</span></span>
-   <span data-ttu-id="e68ce-118">Barrierefreie visuelle Darstellung sicherstellen, z. B. durch Berücksichtigen eines Textkontrastverhältnisses von 4,5:1 (und nicht nur durch die Verwendung farblich gekennzeichneter Informationen)</span><span class="sxs-lookup"><span data-stu-id="e68ce-118">Ensured an accessible visual experience by including such things as a 4.5:1 text contrast ratio, and don't rely on color alone to convey info to the user.</span></span>
-   <span data-ttu-id="e68ce-119">Tools zum Testen der Barrierefreiheit verwenden, z.B. Inspect oder AccChecker, um Ihre App zu überprüfen und alle von diesen Tools ermittelten Fehler mit hoher Priorität zu beheben</span><span class="sxs-lookup"><span data-stu-id="e68ce-119">Used accessibility testing tools, such as Inspect or AccChecker, to verify your app, and resolve all high-priority errors detected by those tools.</span></span>
-   <span data-ttu-id="e68ce-120">Die wichtigsten Szenarien der App unter Verwendung von Funktionen und Tools wie „Sprachausgabe“, „Bildschirmlupe“, „Bildschirmtastatur“, „Hoher Kontrast“ und „Hoher DPI-Wert“ vollständig überprüfen</span><span class="sxs-lookup"><span data-stu-id="e68ce-120">Verified the app’s key scenarios from end to end using such facilities and tools as Narrator, Magnifier, On Screen Keyboard, High Contrast, and High DPI.</span></span>

<span data-ttu-id="e68ce-121">Wenn Sie Ihre App als barrierefrei ausweisen, erklären Sie ausdrücklich, dass Ihre App eine Barrierefreiheit für alle Kunden aufweist, einschließlich für Personen mit Behinderungen.</span><span class="sxs-lookup"><span data-stu-id="e68ce-121">When you declare your app as accessible, you agree that your app is accessible to all customers, including those with disabilities.</span></span> <span data-ttu-id="e68ce-122">Das bedeutet beispielsweise, dass Sie die App im Modus mit hohem Kontrast und die Sprachausgabe getestet haben.</span><span class="sxs-lookup"><span data-stu-id="e68ce-122">For example, this means you have tested the app with high-contrast mode and with a screen reader.</span></span> <span data-ttu-id="e68ce-123">Sie haben außerdem sichergestellt, dass die Benutzeroberfläche ordnungsgemäß mit der Tastatur, der Bildschirmlupe und weiteren Tools zur Unterstützung der Barrierefreiheit funktioniert.</span><span class="sxs-lookup"><span data-stu-id="e68ce-123">You've also verified that the user interface functions correctly with a keyboard, the Magnifier, and other accessibility tools.</span></span>

<span data-ttu-id="e68ce-124">Weitere Informationen finden Sie unter [Eingabehilfen](../design/accessibility/accessibility.md), [Eingabehilfen testen](../design/accessibility/accessibility-testing.md)und [Eingabehilfen im Speicher](../design/accessibility/accessibility-in-the-store.md).</span><span class="sxs-lookup"><span data-stu-id="e68ce-124">For more info, see [Accessibility](../design/accessibility/accessibility.md), [Accessibility testing](../design/accessibility/accessibility-testing.md), and [Accessibility in the Store](../design/accessibility/accessibility-in-the-store.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e68ce-125">Weisen Sie die App nur dann als barrierefrei aus, wenn Sie sie ausdrücklich für diesen Zweck entwickelt und getestet haben.</span><span class="sxs-lookup"><span data-stu-id="e68ce-125">Don't list your app as accessible unless you have specifically engineered and tested it for that purpose.</span></span> <span data-ttu-id="e68ce-126">Falls Ihre App als barrierefrei ausgewiesen ist, jedoch eigentlich keine Barrierefreiheit unterstützt, werden Sie wahrscheinlich negatives Feedback von der Community erhalten.</span><span class="sxs-lookup"><span data-stu-id="e68ce-126">If your app is declared as accessible, but it doesn’t actually support accessibility, you'll probably receive negative feedback from the community.</span></span>

## <a name="customers-can-install-this-app-to-alternate-drives-or-removable-storage"></a><span data-ttu-id="e68ce-127">Kunden können diese App auf alternativen Laufwerken oder Wechselmedien installieren.</span><span class="sxs-lookup"><span data-stu-id="e68ce-127">Customers can install this app to alternate drives or removable storage.</span></span>

<span data-ttu-id="e68ce-128">In diesem Feld wird in der Standardeinstellung können Kunden Ihre app auf externe oder austauschbaren Speicher installieren, die Media wie etwa einer SD-Karte oder auf einen Systemdatenträger wie ein externes Laufwerk Laufwerk überprüft.</span><span class="sxs-lookup"><span data-stu-id="e68ce-128">This box is checked by default, to allow customers to install your app to external or removable storage media such as an SD card, or to a non-system volume drive such as an external drive.</span></span> <span data-ttu-id="e68ce-129">(Für Windows Phone 8.1, wurde dieser zuvor über StoreManifest.xml angezeigt.)</span><span class="sxs-lookup"><span data-stu-id="e68ce-129">(For Windows Phone 8.1, this was previously indicated via StoreManifest.xml.)</span></span>

<span data-ttu-id="e68ce-130">Wenn Sie verhindern, dass Ihre app auf alternative Laufwerke oder Wechselspeicher installiert wird und Installation auf die interne Festplatte auf ihrem Gerät nur zulassen möchten, deaktivieren Sie dieses Kontrollkästchen.</span><span class="sxs-lookup"><span data-stu-id="e68ce-130">If you want to prevent your app from being installed to alternate drives or removable storage, and only allow installation to the internal hard drive on their device, uncheck this box.</span></span>

<span data-ttu-id="e68ce-131">Beachten Sie, dass es keine Option Installation einschränken gibt, sodass eine app kann *nur* werden auf Speichermedien installiert.</span><span class="sxs-lookup"><span data-stu-id="e68ce-131">Note that there is no option to restrict installation so that an app can *only* be installed to removable storage media.</span></span>


## <a name="windows-can-include-this-apps-data-in-automatic-backups-to-onedrive"></a><span data-ttu-id="e68ce-132">Windows kann die Daten dieser App in automatische Sicherungen auf OneDrive einschließen.</span><span class="sxs-lookup"><span data-stu-id="e68ce-132">Windows can include this app's data in automatic backups to OneDrive.</span></span>

<span data-ttu-id="e68ce-133">Dieses Kontrollkästchen ist standardmäßig aktiviert, damit die Daten Ihrer App eingeschlossen werden können, wenn ein Kunde automatische OneDrive-Sicherungen von Windows erstellen lässt.</span><span class="sxs-lookup"><span data-stu-id="e68ce-133">This box is checked by default, to allow your app's data to be included when a customer chooses to have Windows make automated backups to OneDrive.</span></span> <span data-ttu-id="e68ce-134">(Für Windows Phone 8.1, wurde dieser zuvor über StoreManifest.xml angezeigt.)</span><span class="sxs-lookup"><span data-stu-id="e68ce-134">(For Windows Phone 8.1, this was previously indicated via StoreManifest.xml.)</span></span>

<span data-ttu-id="e68ce-135">Wenn Sie verhindern möchten, dass die App-Daten in automatische Sicherungen eingeschlossen werden, deaktivieren Sie das Kontrollkästchen.</span><span class="sxs-lookup"><span data-stu-id="e68ce-135">If you want to prevent your app's data from being included in automated backups, uncheck this box.</span></span>


## <a name="this-app-sends-kinect-data-to-external-services"></a><span data-ttu-id="e68ce-136">Diese app sendet Kinect Daten an externe Dienste an.</span><span class="sxs-lookup"><span data-stu-id="e68ce-136">This app sends Kinect data to external services.</span></span> 

<span data-ttu-id="e68ce-137">Wenn Ihre app Kinect Daten verwendet und ihn an einen externen Dienst sendet, müssen Sie dieses Kontrollkästchen.</span><span class="sxs-lookup"><span data-stu-id="e68ce-137">If your app uses Kinect data and sends it to any external service, you must check this box.</span></span>



 

 

 




