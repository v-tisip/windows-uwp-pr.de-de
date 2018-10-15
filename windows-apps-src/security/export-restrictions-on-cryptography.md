---
title: Exportbeschränkungen hinsichtlich Kryptografie
description: Anhand der Informationen in diesem Abschnitt können Sie ermitteln, ob Ihre App Kryptografiefunktionen in einer Weise verwendet, die unter Umständen dazu führt, dass sie im Microsoft Store nicht angezeigt wird.
ms.assetid: 204C7D1D-6F08-4AEE-A333-434D715E7617
author: msatranjr
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Sicherheit
ms.localizationpriority: medium
ms.openlocfilehash: 842d26a2bb257dd182813832c5e6480237a9f220
ms.sourcegitcommit: 106aec1e59ba41aae2ac00f909b81bf7121a6ef1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2018
ms.locfileid: "4613091"
---
# <a name="export-restrictions-on-cryptography"></a><span data-ttu-id="d0682-104">Exportbeschränkungen hinsichtlich Kryptografie</span><span class="sxs-lookup"><span data-stu-id="d0682-104">Export restrictions on cryptography</span></span>



<span data-ttu-id="d0682-105">Anhand der Informationen in diesem Abschnitt können Sie ermitteln, ob Ihre App Kryptografiefunktionen in einer Weise verwendet, die unter Umständen dazu führt, dass sie im Microsoft Store nicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d0682-105">Use this info to determine if your app uses cryptography in a way that might prevent it from being listed in the Microsoft Store.</span></span>

<span data-ttu-id="d0682-106">Das Bureau of Industry and Security (BIS) im United States Department of Commerce kontrolliert den Export von Technologie, die bestimmte Arten von Verschlüsselung verwendet.</span><span class="sxs-lookup"><span data-stu-id="d0682-106">The Bureau of Industry and Security in the United States Department of Commerce regulates the export of technology that uses certain types of encryption.</span></span> <span data-ttu-id="d0682-107">Bei allen im Microsoft Store aufgelisteten Apps müssen diese Gesetze und Bestimmungen beachtet werden, da die App-Dateien in den USA gespeichert werden können.</span><span class="sxs-lookup"><span data-stu-id="d0682-107">All apps listed in the Microsoft Store must comply with these laws and regulations because the app files can be stored in the United States.</span></span> <span data-ttu-id="d0682-108">Sogar bei Apps, die von App-Entwicklern aus anderen Ländern zur Verteilung außerhalb der USA hochgeladen werden, müssen diese Bestimmungen befolgt werden.</span><span class="sxs-lookup"><span data-stu-id="d0682-108">Even apps that are uploaded by app developers from other countries for distribution outside of the United States must comply with these regulations.</span></span> <span data-ttu-id="d0682-109">Daher müssen alle App-Entwickler beim Übermitteln einer App an den Microsoft Store bestätigen, dass ihre Apps keine Technologien enthalten, die gemäß diesen Bestimmungen eingeschränkt sind.</span><span class="sxs-lookup"><span data-stu-id="d0682-109">Consequently, when submitting an app to the Microsoft Store, all app developers must make sure that their apps don't contain any technology that is restricted by these regulations.</span></span>

> <span data-ttu-id="d0682-110">**Hinweis**  In den hier bereitgestellten Informationen finden Sie einige Richtlinien. Sie sind jedoch als App-Entwickler, der Apps im Microsoft Store veröffentlicht, für die Einhaltung aller geltenden Gesetze und Bestimmungen verantwortlich.</span><span class="sxs-lookup"><span data-stu-id="d0682-110">**Note**  The information provided here provides some guidance, but it is your responsibility as the app developer who is publishing apps in the Microsoft Store to make sure that your app complies with all applicable laws and regulations.</span></span>

 

<span data-ttu-id="d0682-111">Weitere Informationen zum United States Department of Commerce und dem BIS finden Sie unter [Informationen zum Bureau of Industry and Security](http://go.microsoft.com/fwlink/p/?LinkID=245644).</span><span class="sxs-lookup"><span data-stu-id="d0682-111">For more info about the U.S. Department of Commerce and the Bureau of Industry and Security, see [About the Bureau of Industry and Security](http://go.microsoft.com/fwlink/p/?LinkID=245644).</span></span>

<span data-ttu-id="d0682-112">Informationen zu den Export Administration Regulations (EAR), die den Export von Technologien regeln, die Verschlüsselung enthalten, finden Sie unter [EAR-Bestimmungen für Waren, die Verschlüsselung nutzen](http://go.microsoft.com/fwlink/p/?LinkID=245645).</span><span class="sxs-lookup"><span data-stu-id="d0682-112">For info about the Export Administration Regulations (EAR) that govern the export of technology that includes encryption, see [EAR Controls for Items That Use Encryption](http://go.microsoft.com/fwlink/p/?LinkID=245645).</span></span>

## <a name="governed-uses"></a><span data-ttu-id="d0682-113">Eingeschränkte Verwendungsarten</span><span class="sxs-lookup"><span data-stu-id="d0682-113">Governed uses</span></span>

<span data-ttu-id="d0682-114">Ermitteln Sie zunächst, ob Ihre App eine Art von Kryptografie verwendet, die durch die Export Administration Regulations geregelt wird.</span><span class="sxs-lookup"><span data-stu-id="d0682-114">First, determine if your app uses a type of cryptography that is governed by the Export Administration Regulations.</span></span> <span data-ttu-id="d0682-115">Die Frage enthält die in der Liste enthaltenen Beispiele. Diese Liste enthält jedoch nicht alle möglichen Anwendungsmöglichkeiten von Kryptografie.</span><span class="sxs-lookup"><span data-stu-id="d0682-115">The question includes the examples shown in the list here; but remember that this list doesn't include every possible application of cryptography.</span></span>

> <span data-ttu-id="d0682-116">**Wichtig**  Berücksichtigen Sie hierbei nicht nur den Code, den Sie für die App geschrieben haben, sondern auch alle Softwarebibliotheken, Hilfsprogramme und Betriebssystemkomponenten, die Ihre App enthält oder mit denen sie verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="d0682-116">**Important**  Consider not only the code you wrote for your app, but also all the software libraries, utilities and operating system components that your app includes or links to.</span></span>

-   <span data-ttu-id="d0682-117">Jede Verwendung einer digitalen Signatur, z.B. Authentifizierung oder Integritätsprüfung</span><span class="sxs-lookup"><span data-stu-id="d0682-117">Any use of a digital signature, such as authentication or integrity checking</span></span>
-   <span data-ttu-id="d0682-118">Verschlüsselung von Daten oder Dateien, die die App verwendet oder auf die sie zugreift</span><span class="sxs-lookup"><span data-stu-id="d0682-118">Encryption of any data or files that your app uses or accesses</span></span>
-   <span data-ttu-id="d0682-119">Schlüsselverwaltung, Zertifikatverwaltung oder Vorgänge, die mit einer Public Key-Infrastruktur interagieren</span><span class="sxs-lookup"><span data-stu-id="d0682-119">Key management, certificate management, or anything that interacts with a public key infrastructure</span></span>
-   <span data-ttu-id="d0682-120">Verwendung eines sicheren Kommunikationskanals, z.B. NTLM, Kerberos, Secure Sockets Layer (SSL) oder Transport Layer Security (TLS)</span><span class="sxs-lookup"><span data-stu-id="d0682-120">Using a secure communication channel such as NTLM, Kerberos, Secure Sockets Layer (SSL), or Transport Layer Security (TLS)</span></span>
-   <span data-ttu-id="d0682-121">Verschlüsselung von Kennwörtern oder andere Arten der Datensicherheit</span><span class="sxs-lookup"><span data-stu-id="d0682-121">Encrypting passwords or other forms of information security</span></span>
-   <span data-ttu-id="d0682-122">Kopierschutz oder Verwaltung digitaler Rechte (Digital Rights Management, DRM)</span><span class="sxs-lookup"><span data-stu-id="d0682-122">Copy protection or digital rights management (DRM)</span></span>
-   <span data-ttu-id="d0682-123">Virenschutz</span><span class="sxs-lookup"><span data-stu-id="d0682-123">Antivirus protection</span></span>

<span data-ttu-id="d0682-124">Eine vollständige und aktuelle Liste kryptografischer Anwendungen finden Sie unter [EAR-Bestimmungen für Waren, die Verschlüsselung nutzen](http://go.microsoft.com/fwlink/p/?LinkID=245645).</span><span class="sxs-lookup"><span data-stu-id="d0682-124">For the complete and current list of cryptographic applications, see [EAR Controls for Items That Use Encryption](http://go.microsoft.com/fwlink/p/?LinkID=245645).</span></span>

## <a name="non-restricted-uses"></a><span data-ttu-id="d0682-125">Nicht eingeschränkte Verwendungsarten</span><span class="sxs-lookup"><span data-stu-id="d0682-125">Non-restricted uses</span></span>

<span data-ttu-id="d0682-126">Beachten Sie, dass einige Verwendungsarten von Kryptografie nicht eingeschränkt sind.</span><span class="sxs-lookup"><span data-stu-id="d0682-126">Note that some of the applications of cryptography are not restricted.</span></span> <span data-ttu-id="d0682-127">Hier ein Überblick über die unbeschränkten Aufgaben:</span><span class="sxs-lookup"><span data-stu-id="d0682-127">Here are the unrestricted tasks:</span></span>

-   <span data-ttu-id="d0682-128">Kennwortverschlüsselung</span><span class="sxs-lookup"><span data-stu-id="d0682-128">Password encryption</span></span>
-   <span data-ttu-id="d0682-129">Kopierschutz</span><span class="sxs-lookup"><span data-stu-id="d0682-129">Copy protection</span></span>
-   <span data-ttu-id="d0682-130">Authentifizierung</span><span class="sxs-lookup"><span data-stu-id="d0682-130">Authentication</span></span>
-   <span data-ttu-id="d0682-131">Verwaltung digitaler Rechte (DRM)</span><span class="sxs-lookup"><span data-stu-id="d0682-131">Digital rights management</span></span>
-   <span data-ttu-id="d0682-132">Verwendung digitaler Signaturen</span><span class="sxs-lookup"><span data-stu-id="d0682-132">Using digital signatures</span></span>

<span data-ttu-id="d0682-133">Eine vollständige und aktuelle Liste kryptografischer Anwendungen finden Sie unter [EAR-Bestimmungen für Waren, die Verschlüsselung nutzen](http://go.microsoft.com/fwlink/p/?LinkID=245645).</span><span class="sxs-lookup"><span data-stu-id="d0682-133">For the complete and current list of cryptographic applications, see [EAR Controls for Items That Use Encryption](http://go.microsoft.com/fwlink/p/?LinkID=245645).</span></span>

<span data-ttu-id="d0682-134">Wenn Ihre App Kryptografie- oder Verschlüsselungsfunktionen für eine Aufgabe aufruft, unterstützt, enthält oder verwendet, die nicht in dieser Liste enthalten ist, ist für die App eine ECCN (Export Commodity Classification Number) erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d0682-134">If your app calls, supports, contains, or uses cryptography or encryption for any task that is not in this list, it needs an Export Commodity Classification Number (ECCN).</span></span>

<span data-ttu-id="d0682-135">Wenn Sie keine ECCN besitzen, informieren Sie sich unter [Fragen und Antworten zur ECCN](http://go.microsoft.com/fwlink/p/?LinkID=245646).</span><span class="sxs-lookup"><span data-stu-id="d0682-135">If you don't have an ECCN, see [ECCN Questions and Answers](http://go.microsoft.com/fwlink/p/?LinkID=245646).</span></span>
