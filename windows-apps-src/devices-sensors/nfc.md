---
author: msatranjr
title: NFC
description: Dieser Abschnitt enthält Artikel mit Anweisungen zum Integrieren von NFC in UWP-Apps (Universelle Windows-Plattform).
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.assetid: 15a113b5-8231-41c9-b724-ce5add813967
ms.localizationpriority: medium
ms.openlocfilehash: 01e8e5a94092312b953dd2a183cd6902a1df5505
ms.sourcegitcommit: e38b334edb82bf2b1474ba686990f4299b8f59c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6841826"
---
# <a name="nfc"></a><span data-ttu-id="1d616-104">NFC</span><span class="sxs-lookup"><span data-stu-id="1d616-104">NFC</span></span>


<span data-ttu-id="1d616-105">Dieser Abschnitt enthält Artikel mit Anweisungen zum Integrieren von NFC in UWP-Apps (Universelle Windows-Plattform).</span><span class="sxs-lookup"><span data-stu-id="1d616-105">This section contains articles on how to integrate NFC into Universal Windows Platform (UWP) apps.</span></span>

|<span data-ttu-id="1d616-106">Thema</span><span class="sxs-lookup"><span data-stu-id="1d616-106">Topic</span></span> |<span data-ttu-id="1d616-107">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="1d616-107">Description</span></span>|
|--------|------------------|
| [<span data-ttu-id="1d616-108">Erstellen einer NFC-Smartcard-App</span><span class="sxs-lookup"><span data-stu-id="1d616-108">Create an NFC Smart Card app</span></span>](host-card-emulation.md)   | <span data-ttu-id="1d616-109">Windows Phone8.1 hat Apps mit NFC-Kartenemulation per SIM-basiertem sicherem Element unterstützt. Für dieses Modell war es aber erforderlich, dass Apps für das sichere Bezahlen eng mit den Betreibern von mobilen Netzwerken gekoppelt waren.</span><span class="sxs-lookup"><span data-stu-id="1d616-109">Windows Phone 8.1 supported NFC card emulation apps using a SIM-based secure element, but that model required secure payment apps to be tightly coupled with mobile-network operators (MNO).</span></span> <span data-ttu-id="1d616-110">Dadurch wurde die Vielfältigkeit möglicher Zahlungslösungen anderer Händler oder Entwickler eingeschränkt, die nicht mit Betreibern von mobilen Netzwerken gekoppelt waren.</span><span class="sxs-lookup"><span data-stu-id="1d616-110">This limited the variety of possible payment solutions by other merchants or developers that are not coupled with MNOs.</span></span> <span data-ttu-id="1d616-111">In Windows10 Mobile haben wir eine neue Technologie für die Kartenemulation eingeführt, die die Bezeichnung „Host-Kartenemulation“ (Host Card Emulation, HCE) trägt.</span><span class="sxs-lookup"><span data-stu-id="1d616-111">In Windows 10 Mobile, we have introduced a new card emulation technology called, Host Card Emulation (HCE).</span></span> <span data-ttu-id="1d616-112">Dieser Artikel dient als Leitfaden bei der Entwicklung einer HCE-App.</span><span class="sxs-lookup"><span data-stu-id="1d616-112">This article serves as a guide to develop an HCE app.</span></span>   |