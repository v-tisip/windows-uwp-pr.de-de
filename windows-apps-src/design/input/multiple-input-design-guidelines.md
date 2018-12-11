---
Description: Just as people use a combination of voice and gesture when communicating with each other, multiple types and modes of input can also be useful when interacting with an app.
title: Entwurfsrichtlinien für mehrere Eingaben
ms.assetid: 03EB5388-080F-467C-B272-C92BE00F2C69
label: Multiple inputs
template: detail.hbs
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: c67430680854e7940d12af15ecd3c07dcd976802
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8928099"
---
# <a name="multiple-inputs"></a><span data-ttu-id="7cf1b-103">Mehrere Eingaben</span><span class="sxs-lookup"><span data-stu-id="7cf1b-103">Multiple inputs</span></span>


<span data-ttu-id="7cf1b-104">Ebenso wie Menschen untereinander mit einer Mischung aus Sprache und Gesten kommunizieren, kann sich auch bei der Interaktion mit einer App die Verwendung mehrerer Eingabearten und -modi als hilfreich erweisen.</span><span class="sxs-lookup"><span data-stu-id="7cf1b-104">Just as people use a combination of voice and gesture when communicating with each other, multiple types and modes of input can also be useful when interacting with an app.</span></span>


<span data-ttu-id="7cf1b-105">Um eine möglichst große Zahl von Benutzern und Geräten zu unterstützen, empfehlen wir, Ihre App für die Kompatibilität mit so vielen Eingabearten wie möglich zu entwickeln(Gesten, Spracherkennung, Toucheingabe, Touchpad, Maus und Tastatur).</span><span class="sxs-lookup"><span data-stu-id="7cf1b-105">To accommodate as many users and devices as possible, we recommend that you design your apps to work with as many input types as possible (gesture, speech, touch, touchpad, mouse, and keyboard).</span></span> <span data-ttu-id="7cf1b-106">Dadurch werden Flexibilität, Benutzerfreundlichkeit und Barrierefreiheit optimiert.</span><span class="sxs-lookup"><span data-stu-id="7cf1b-106">Doing so will maximize flexibility, usability, and accessibility.</span></span>

<span data-ttu-id="7cf1b-107">Um zu beginnen, sollten Sie die verschiedenen Szenarien berücksichtigen, in denen Ihre App Eingaben verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="7cf1b-107">To begin, consider the various scenarios in which your app handles input.</span></span> <span data-ttu-id="7cf1b-108">Versuchen Sie, in der gesamten App konsistent zu sein, und denken Sie daran, dass die Steuerelemente der Plattform integrierte Unterstützung für mehrere Eingabetypen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="7cf1b-108">Try to be consistent throughout your app, and remember that the platform controls provide built-in support for multiple input types.</span></span>

-   <span data-ttu-id="7cf1b-109">Können Benutzer über mehrere Eingabegeräte mit der Anwendung interagieren?</span><span class="sxs-lookup"><span data-stu-id="7cf1b-109">Can users interact with the application through multiple input devices?</span></span>
-   <span data-ttu-id="7cf1b-110">Werden alle Eingabemethoden jederzeit unterstützt?</span><span class="sxs-lookup"><span data-stu-id="7cf1b-110">Are all input methods supported at all times?</span></span> <span data-ttu-id="7cf1b-111">Mit bestimmten Steuerelementen?</span><span class="sxs-lookup"><span data-stu-id="7cf1b-111">With certain controls?</span></span> <span data-ttu-id="7cf1b-112">Zu bestimmten Zeiten oder Umständen?</span><span class="sxs-lookup"><span data-stu-id="7cf1b-112">At specific times or circumstances?</span></span>
-   <span data-ttu-id="7cf1b-113">Hat eine Eingabemethode Priorität?</span><span class="sxs-lookup"><span data-stu-id="7cf1b-113">Does one input method take priority?</span></span>

## <a name="single-or-exclusive-mode-interactions"></a><span data-ttu-id="7cf1b-114">Einzel- (oder Exklusiv)-Modusinteraktionen</span><span class="sxs-lookup"><span data-stu-id="7cf1b-114">Single (or exclusive)-mode interactions</span></span>


<span data-ttu-id="7cf1b-115">Mit Einzelmodusinteraktionen werden mehrere Eingabetypen unterstützt, es kann jedoch nur einer pro Aktion verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7cf1b-115">With single-mode interactions, multiple input types are supported, but only one can be used per action.</span></span> <span data-ttu-id="7cf1b-116">Z. B. Spracherkennung für Befehle und Gesten für die Navigation; oder die Texteingabe per Touch oder Gesten, je nach Näherung.</span><span class="sxs-lookup"><span data-stu-id="7cf1b-116">For example, speech recognition for commands, and gestures for navigation; or, text entry using touch or gestures, depending on proximity.</span></span>

## <a name="multimodal-interactions"></a><span data-ttu-id="7cf1b-117">Kombinierte Interaktionen</span><span class="sxs-lookup"><span data-stu-id="7cf1b-117">Multimodal interactions</span></span>

<span data-ttu-id="7cf1b-118">Mit kombinierten Interaktionen werden nacheinander mehrere Eingabemethoden verwendet, um eine einzelne Aktion auszuführen.</span><span class="sxs-lookup"><span data-stu-id="7cf1b-118">With multimodal interactions, multiple input methods in sequence are used to complete a single action.</span></span>

<span data-ttu-id="7cf1b-119">Spracherkennung + Geste</span><span class="sxs-lookup"><span data-stu-id="7cf1b-119">Speech + gesture</span></span>  
<span data-ttu-id="7cf1b-120">Der Benutzer zeigt auf ein Produkt, und sagt dann „Dem Einkaufswagen hinzufügen“.</span><span class="sxs-lookup"><span data-stu-id="7cf1b-120">The user points to a product, and then says “Add to cart.”</span></span>

<span data-ttu-id="7cf1b-121">Spracherkennung + Toucheingabe</span><span class="sxs-lookup"><span data-stu-id="7cf1b-121">Speech + touch</span></span>  
<span data-ttu-id="7cf1b-122">Der Benutzer wählt ein Foto, indem er dieses gedrückt hält, und sagt dann „Foto senden“.</span><span class="sxs-lookup"><span data-stu-id="7cf1b-122">The user selects a photo using press and hold, and then says “Send photo.”</span></span>



