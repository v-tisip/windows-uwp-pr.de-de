---
author: msatranjr
title: NFC
description: Dieser Abschnitt enthält Artikel mit Anweisungen zum Integrieren von NFC in UWP-Apps (Universelle Windows-Plattform).
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.assetid: 15a113b5-8231-41c9-b724-ce5add813967
ms.openlocfilehash: 8e2438793ed154e083cca5bdd881012ddd90f42b
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: MT
ms.contentlocale: de-DE
ms.locfileid: "233538"
---
# <a name="nfc"></a><span data-ttu-id="a7779-104">NFC</span><span class="sxs-lookup"><span data-stu-id="a7779-104">NFC</span></span>

<span data-ttu-id="a7779-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="a7779-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="a7779-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \].</span><span class="sxs-lookup"><span data-stu-id="a7779-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="a7779-107">Dieser Abschnitt enthält Artikel mit Anweisungen zum Integrieren von NFC in UWP-Apps (Universelle Windows-Plattform).</span><span class="sxs-lookup"><span data-stu-id="a7779-107">This section contains articles on how to integrate NFC into Universal Windows Platform (UWP) apps.</span></span>

|<span data-ttu-id="a7779-108">Thema</span><span class="sxs-lookup"><span data-stu-id="a7779-108">Topic</span></span> |<span data-ttu-id="a7779-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a7779-109">Description</span></span>|
|--------|------------------|
| [<span data-ttu-id="a7779-110">Erstellen einer NFC-Smartcard-App</span><span class="sxs-lookup"><span data-stu-id="a7779-110">Create an NFC Smart Card app</span></span>](host-card-emulation.md)   | <span data-ttu-id="a7779-111">Windows Phone8.1 hat Apps mit NFC-Kartenemulation per SIM-basiertem sicherem Element unterstützt. Für dieses Modell war es aber erforderlich, dass Apps für das sichere Bezahlen eng mit den Betreibern von mobilen Netzwerken gekoppelt waren.</span><span class="sxs-lookup"><span data-stu-id="a7779-111">Windows Phone 8.1 supported NFC card emulation apps using a SIM-based secure element, but that model required secure payment apps to be tightly coupled with mobile-network operators (MNO).</span></span> <span data-ttu-id="a7779-112">Dadurch wurde die Vielfältigkeit möglicher Zahlungslösungen anderer Händler oder Entwickler eingeschränkt, die nicht mit Betreibern von mobilen Netzwerken gekoppelt waren.</span><span class="sxs-lookup"><span data-stu-id="a7779-112">This limited the variety of possible payment solutions by other merchants or developers that are not coupled with MNOs.</span></span> <span data-ttu-id="a7779-113">In Windows10 Mobile haben wir eine neue Technologie für die Kartenemulation eingeführt, die die Bezeichnung „Host-Kartenemulation“ (Host Card Emulation, HCE) trägt.</span><span class="sxs-lookup"><span data-stu-id="a7779-113">In Windows 10 Mobile, we have introduced a new card emulation technology called, Host Card Emulation (HCE).</span></span> <span data-ttu-id="a7779-114">Dieser Artikel dient als Leitfaden bei der Entwicklung einer HCE-App.</span><span class="sxs-lookup"><span data-stu-id="a7779-114">This article serves as a guide to develop an HCE app.</span></span>   |