---
author: drewbatgit
ms.assetid: DD8FFA8C-DFF0-41E3-8F7A-345C5A248FC2
description: "In diesem Abschnitt wird beschrieben, wie Sie Ihrer UWP-App (Universelle Windows-Plattform) PlayReady-geschützte Medieninhalte hinzufügen."
title: PlayReady DRM
ms.author: drewbat
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 803070143a3d07bfbdbb4f3e1b7b70858b75e0f9
ms.sourcegitcommit: cd9b4bdc9c3a0b537a6e910a15df8541b49abf9c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2017
---
# <a name="playready-drm"></a><span data-ttu-id="0d35c-104">PlayReady DRM</span><span class="sxs-lookup"><span data-stu-id="0d35c-104">PlayReady DRM</span></span>

<span data-ttu-id="0d35c-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="0d35c-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="0d35c-106">Artikel zu Windows 8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="0d35c-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>


<span data-ttu-id="0d35c-107">In diesem Abschnitt wird beschrieben, wie Sie Ihrer UWP-App (Universelle Windows-Plattform) PlayReady-geschützte Medieninhalte hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="0d35c-107">This topic describes how to add PlayReady protected media content to your Universal Windows Platform (UWP) app.</span></span>

<span data-ttu-id="0d35c-108">PlayReady DRM ermöglicht Entwicklern das Erstellen von UWP-Apps, die PlayReady-geschützte Inhalte für den Benutzer bereitstellen und gleichzeitig vom Inhaltsanbieter definierte Regeln erzwingen können.</span><span class="sxs-lookup"><span data-stu-id="0d35c-108">PlayReady DRM enables developers to create UWP apps capable of providing PlayReady content to the user while enforcing the access rules defined by the content provider.</span></span> <span data-ttu-id="0d35c-109">In diesem Abschnitt werden die Änderungen beschrieben, die für Windows 10 am Microsoft PlayReady DRM vorgenommen wurden. Außerdem wird erläutert, wie Sie Ihre UWP-App mit PlayReady ändern, um die Änderungen in der Windows 10-Version (gegenüber der Windows 8.1-Version) zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="0d35c-109">This section describes changes made to Microsoft PlayReady DRM for Windows 10 and how to modify your PlayReady UWP app to support the changes made from the previous Windows 8.1 version to the Windows 10 version.</span></span>
 
| <span data-ttu-id="0d35c-110">Thema</span><span class="sxs-lookup"><span data-stu-id="0d35c-110">Topic</span></span>                                                                     | <span data-ttu-id="0d35c-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0d35c-111">Description</span></span>                                                                                                                                                                                                                                                                             |
|---------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [<span data-ttu-id="0d35c-112">Hardware-DRM</span><span class="sxs-lookup"><span data-stu-id="0d35c-112">Hardware DRM</span></span>](hardware-drm.md)                                           | <span data-ttu-id="0d35c-113">Dieses Thema enthält eine Übersicht über das Hinzufügen der hardwarebasierten Verwaltung digitaler Rechte (Digital Rights Management, DRM) mit PlayReady zu Ihrer UWP-App.</span><span class="sxs-lookup"><span data-stu-id="0d35c-113">This topic provides an overview of how to add PlayReady hardware-based digital rights management (DRM) to your UWP app.</span></span>                                                                                                                                                                 |
| [<span data-ttu-id="0d35c-114">Adaptives Streaming mit PlayReady</span><span class="sxs-lookup"><span data-stu-id="0d35c-114">Adaptive streaming with PlayReady</span></span>](adaptive-streaming-with-playready.md) | <span data-ttu-id="0d35c-115">In diesem Artikel wird beschrieben, wie Sie einer UWP-App (Universelle Windows-Plattform) adaptives Streaming von Multimediainhalten mit Microsoft PlayReady-Inhaltsschutz hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="0d35c-115">This article describes how to add adaptive streaming of multimedia content with Microsoft PlayReady content protection to a Universal Windows Platform (UWP) app.</span></span> <span data-ttu-id="0d35c-116">Dieses Feature unterstützt derzeit die Wiedergabe von HTTP Live Streaming(HLS)- und Dynamic Streaming over HTTP(DASH)-Inhalten.</span><span class="sxs-lookup"><span data-stu-id="0d35c-116">This feature currently supports playback of Http Live Streaming (HLS) and Dynamic Streaming over HTTP (DASH) content.</span></span> |

## <a name="whats-new-in-playready-drm"></a><span data-ttu-id="0d35c-117">Neuigkeiten bei PlayReady DRM</span><span class="sxs-lookup"><span data-stu-id="0d35c-117">What's new in PlayReady DRM</span></span>

<span data-ttu-id="0d35c-118">In der folgenden Liste werden die neuen Features und Änderungen von PlayReady DRM unter Windows10 beschrieben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-118">The following list describes the new features and changes made to PlayReady DRM for Windows 10.</span></span>

-   <span data-ttu-id="0d35c-119">Hardwarebasierte Verwaltung digitaler Rechte (Hardware Digital Rights Management, HWDRM) wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-119">Added hardware digital rights management (HWDRM).</span></span>

    <span data-ttu-id="0d35c-120">Die Unterstützung für hardwarebasierten Inhaltsschutz ermöglicht die sichere Wiedergabe von High-Definition(HD)- und Ultra-High-Definition(UHD)-Inhalten auf mehreren Geräteplattformen.</span><span class="sxs-lookup"><span data-stu-id="0d35c-120">Hardware-based content protection support enables secure playback of high definition (HD) and ultra-high definition (UHD) content on multiple device platforms.</span></span> <span data-ttu-id="0d35c-121">Schlüsselmaterial (einschließlich privater Schlüssel, Inhaltsschlüssel und anderer Schlüsselmaterialien zum Ableiten oder Entsperren dieser Schlüssel) sowie entschlüsselte komprimierte und nicht komprimierte Videobeispiele werden durch Hardwaresicherheit geschützt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-121">Key material (including private keys, content keys, and any other key material used to derive or unlock said keys), and decrypted compressed and uncompressed video samples are protected by leveraging hardware security.</span></span> <span data-ttu-id="0d35c-122">Bei Verwendung des Hardware-DRM sind unbekannte Aktivierungen (Wiedergabe auf unbekannter Ausgabe/Wiedergabe auf unbekannter Ausgabe mit „downres”) irrelevant, da die HWDRM-Pipeline die verwendete Ausgabe immer kennt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-122">When Hardware DRM is being used, neither unknown enabler (play to unknown / play to unknown with downres) has meaning as the HWDRM pipeline always knows the output being used.</span></span> <span data-ttu-id="0d35c-123">Weitere Informationen finden Sie unter [Hardware-DRM](hardware-drm.md).</span><span class="sxs-lookup"><span data-stu-id="0d35c-123">For more information, see [Hardware DRM](hardware-drm.md).</span></span>

-   <span data-ttu-id="0d35c-124">PlayReady ist keine AppX-Framework-Komponente mehr, sondern stattdessen eine integrierte Betriebssystemkomponente.</span><span class="sxs-lookup"><span data-stu-id="0d35c-124">PlayReady is no longer an appX framework component, but instead is an in-box operating system component.</span></span> <span data-ttu-id="0d35c-125">Der Namespace wurde von **Microsoft.Media.PlayReadyClient** in [**Windows.Media.Protection.PlayReady**](https://msdn.microsoft.com/library/windows/apps/dn986454) geändert.</span><span class="sxs-lookup"><span data-stu-id="0d35c-125">The namespace was changed from **Microsoft.Media.PlayReadyClient** to [**Windows.Media.Protection.PlayReady**](https://msdn.microsoft.com/library/windows/apps/dn986454).</span></span>
-   <span data-ttu-id="0d35c-126">Die folgenden Header zur Definition der PlayReady-Fehlercodes sind jetzt Teil des Windows Software Development Kit (SDK): „Windows.Media.Protection.PlayReadyErrors.h” und „Windows.Media.Protection.PlayReadyResults.h”.</span><span class="sxs-lookup"><span data-stu-id="0d35c-126">The following headers defining the PlayReady error codes are now part of the Windows Software Development Kit (SDK): Windows.Media.Protection.PlayReadyErrors.h and Windows.Media.Protection.PlayReadyResults.h.</span></span>
-   <span data-ttu-id="0d35c-127">Unterstützt das proaktive Abrufen nicht persistenter Lizenzen.</span><span class="sxs-lookup"><span data-stu-id="0d35c-127">Provides proactive acquisition of non-persistent licenses.</span></span>

    <span data-ttu-id="0d35c-128">Das proaktive Abrufen nicht persistenter Lizenzen wurde von Vorgängerversionen von PlayReady DRM nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-128">Previous versions of PlayReady DRM did not support proactive acquisition of non-persistent licenses.</span></span> <span data-ttu-id="0d35c-129">Diese Funktion wurde in dieser Version hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-129">This capability has been added to this version.</span></span> <span data-ttu-id="0d35c-130">Mit ihrer Hilfe kann die Zeit bis zum ersten Frame verkürzt werden.</span><span class="sxs-lookup"><span data-stu-id="0d35c-130">This can decrease the time to first frame.</span></span> <span data-ttu-id="0d35c-131">Weitere Informationen finden Sie unter [Proaktives Abrufen einer nicht persistenten Lizenz vor der Wiedergabe](#proactively-acquire-a-non-persistent-license-before-playback).</span><span class="sxs-lookup"><span data-stu-id="0d35c-131">For more information, see [Proactively Acquire a Non-Persistent License Before Playback](#proactively-acquire-a-non-persistent-license-before-playback).</span></span>

-   <span data-ttu-id="0d35c-132">Unterstützt das Abrufen mehrerer Lizenzen in einer Nachricht.</span><span class="sxs-lookup"><span data-stu-id="0d35c-132">Provides acquisition of multiple licenses in one message.</span></span>

    <span data-ttu-id="0d35c-133">Ermöglicht der Client-App das Abrufen mehrerer nicht persistenter Lizenzen in einer Lizenzabrufnachricht.</span><span class="sxs-lookup"><span data-stu-id="0d35c-133">Allows the client app to acquire multiple non-persistent licenses in one license acquisition message.</span></span> <span data-ttu-id="0d35c-134">Da Lizenzen für mehrere Inhalte abgerufen werden, während der Benutzer noch die Inhaltsbibliothek durchsucht, kann dies die Zeit bis zum ersten Frame verkürzen. Diese Funktion verhindert, dass beim Abrufen der Lizenz eine Verzögerung erfolgt, wenn der Benutzer die wiederzugebenden Inhalte auswählt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-134">This can decrease the time to first frame by acquiring licenses for multiple pieces of content while the user is still browsing your content library; this prevents a delay for license acquisition when the user selects the content to play.</span></span> <span data-ttu-id="0d35c-135">Darüber hinaus können Audio- und Videodatenströme verschlüsselt werden, um Schlüssel zu trennen, indem ein Inhaltsheader aktiviert wird, der mehrere Schlüsselkennungen (KIDs) enthält. Dadurch können mit einem einzigen Lizenzabruf alle Lizenzen für alle Datenströme in einer Inhaltsdatei abgerufen werden, anstatt zu diesem Zweck benutzerdefinierte Logik und mehrere Lizenzabrufanforderungen verwenden zu müssen.</span><span class="sxs-lookup"><span data-stu-id="0d35c-135">In addition, it allows audio and video streams to be encrypted to separate keys by enabling a content header that includes multiple key identifiers (KIDs); this enables a single license acquisition to acquire all licenses for all streams within a content file instead of having to use custom logic and multiple license acquisition requests to achieve the same result.</span></span>

-   <span data-ttu-id="0d35c-136">Unterstützung für den Echtzeitablauf, d.h. einer Lizenz mit begrenzter Dauer (Limited Duration License, LDL), wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-136">Added real time expiration support, or limited duration license (LDL).</span></span>

    <span data-ttu-id="0d35c-137">Bietet die Möglichkeit, einen Echtzeitablauf für Lizenzen festzulegen und während der Wiedergabe einen reibungslosen Wechsel zwischen einer ablaufenden Lizenz und einer anderen (gültigen) Lizenz sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="0d35c-137">Provides the ability to set real-time expiration on licenses and smoothly transition from an expiring license to another (valid) license in the middle of playback.</span></span> <span data-ttu-id="0d35c-138">In Kombination mit dem Abruf mehrerer Lizenzen in einer Nachricht kann eine App so mehrere LDLs asynchron abrufen, während der Benutzer noch die Inhaltsbibliothek durchsucht, und nur eine Lizenz mit längerer Dauer abrufen, sobald der Benutzer den wiederzugebenden Inhalt ausgewählt hat.</span><span class="sxs-lookup"><span data-stu-id="0d35c-138">When combined with acquisition of multiple licenses in one message, this allows an app to acquire several LDLs asynchronously while the user is still browsing the content library and only acquire a longer duration license once the user has selected content to playback.</span></span> <span data-ttu-id="0d35c-139">Die Wiedergabe wird dann schneller gestartet (weil bereits eine Lizenz verfügbar ist), und da die App beim Ablauf der LDL bereits eine Lizenz mit längerer Dauer abgerufen hat, wird die Wiedergabe unterbrechungsfrei bis zum Ende des Inhalts fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-139">Playback will then start more quickly (because a license is already available) and, since the app will have acquired a longer duration license by the time the LDL expires, smoothly continue playback to the end of the content without interruption.</span></span>

-   <span data-ttu-id="0d35c-140">Nicht persistente Lizenzketten wurden hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-140">Added non-persistent license chains.</span></span>
-   <span data-ttu-id="0d35c-141">Unterstützung für zeitbasierte Einschränkungen (einschließlich Ablauf, Ablauf nach der ersten Wiedergabe und Echtzeitablauf) für nicht persistente Lizenzen wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-141">Added support for time-based restrictions (including expiration, expire after first play, and real time expiration) on non-persistent licenses.</span></span>
-   <span data-ttu-id="0d35c-142">Richtlinienunterstützung für HDCPTyp1 (Version2.2 unter Windows10) wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-142">Added HDCP Type 1 (version 2.2 on Windows 10) policy support.</span></span>

    <span data-ttu-id="0d35c-143">Weitere Informationen finden Sie unter [Zu berücksichtigende Informationen](#things-to-consider).</span><span class="sxs-lookup"><span data-stu-id="0d35c-143">See [Things to Consider](#things-to-consider) for more information.</span></span>

-   <span data-ttu-id="0d35c-144">Miracast ist jetzt als Ausgabe implizit.</span><span class="sxs-lookup"><span data-stu-id="0d35c-144">Miracast is now implicit as an output.</span></span>
-   <span data-ttu-id="0d35c-145">Sicheres Beenden wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-145">Added secure stop.</span></span>

    <span data-ttu-id="0d35c-146">Dank des sicheren Beendens kann ein PlayReady-Gerät einem Medienstreamingdienst zuverlässig bestätigen, dass die Medienwiedergabe für einen bestimmten Inhalt beendet wurde.</span><span class="sxs-lookup"><span data-stu-id="0d35c-146">Secure stop provides the means for a PlayReady device to confidently assert to a media streaming service that media playback has stopped for any given piece of content.</span></span> <span data-ttu-id="0d35c-147">Mit dieser Funktion wird sichergestellt, dass Ihre Medienstreamingdienste präzise Erzwingung und Berichte zu Nutzungseinschränkungen auf verschiedenen Geräten für ein bestimmtes Konto bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="0d35c-147">This capability ensures your media streaming services provide accurate enforcement and reporting of usage limitations on different devices for a given account.</span></span>

-   <span data-ttu-id="0d35c-148">Audio- und Videolizenztrennung wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-148">Added audio and video license separation.</span></span>

    <span data-ttu-id="0d35c-149">Separate Spuren verhindern, dass Videos als Audio decodiert werden. Dadurch wird ein stabilerer Inhaltsschutz gewährleistet.</span><span class="sxs-lookup"><span data-stu-id="0d35c-149">Separate tracks prevent video from being decoded as audio; enabling more robust content protection.</span></span> <span data-ttu-id="0d35c-150">Neue Standards erfordern separate Schlüssel für Audio- und Videospuren.</span><span class="sxs-lookup"><span data-stu-id="0d35c-150">Emerging standards are requiring separate keys for audio and visual tracks.</span></span>

-   <span data-ttu-id="0d35c-151">MaxResDecode-Feature hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-151">Added MaxResDecode.</span></span>

    <span data-ttu-id="0d35c-152">Dieses Feature wurde hinzugefügt, um die Wiedergabe von Inhalten auf eine maximale Auflösung zu beschränken, auch wenn der Benutzer einen leistungsfähigeren Schlüssel (aber keine Lizenz) besitzt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-152">This feature was added to limit playback of content to a maximum resolution even when in possession of a more capable key (but not a license).</span></span> <span data-ttu-id="0d35c-153">Dadurch werden Szenarien unterstützt, in denen mehrere Datenstromgrößen mit einem einzelnen Schlüssel codiert werden.</span><span class="sxs-lookup"><span data-stu-id="0d35c-153">It supports cases where multiple stream sizes are encoded with a single key.</span></span>

<span data-ttu-id="0d35c-154">PlayReady DRM wurden die folgenden neuen Schnittstellen, Klassen und Enumerationen hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="0d35c-154">The following new interfaces, classes, and enumerations were added to PlayReady DRM:</span></span>

-   <span data-ttu-id="0d35c-155">[**IPlayReadyLicenseAcquisitionServiceRequest**
            ](https://msdn.microsoft.com/library/windows/apps/dn986077)-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="0d35c-155">[**IPlayReadyLicenseAcquisitionServiceRequest**](https://msdn.microsoft.com/library/windows/apps/dn986077) interface</span></span>
-   <span data-ttu-id="0d35c-156">[**IPlayReadyLicenseSession**
            ](https://msdn.microsoft.com/library/windows/apps/dn986080)-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="0d35c-156">[**IPlayReadyLicenseSession**](https://msdn.microsoft.com/library/windows/apps/dn986080) interface</span></span>
-   <span data-ttu-id="0d35c-157">[**IPlayReadySecureStopServiceRequest**
            ](https://msdn.microsoft.com/library/windows/apps/dn986090)-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="0d35c-157">[**IPlayReadySecureStopServiceRequest**](https://msdn.microsoft.com/library/windows/apps/dn986090) interface</span></span>
-   <span data-ttu-id="0d35c-158">[**PlayReadyLicenseSession**
            ](https://msdn.microsoft.com/library/windows/apps/dn986309)-Klasse</span><span class="sxs-lookup"><span data-stu-id="0d35c-158">[**PlayReadyLicenseSession**](https://msdn.microsoft.com/library/windows/apps/dn986309) class</span></span>
-   <span data-ttu-id="0d35c-159">[**PlayReadySecureStopIterable**
            ](https://msdn.microsoft.com/library/windows/apps/dn986371)-Klasse</span><span class="sxs-lookup"><span data-stu-id="0d35c-159">[**PlayReadySecureStopIterable**](https://msdn.microsoft.com/library/windows/apps/dn986371) class</span></span>
-   <span data-ttu-id="0d35c-160">[**PlayReadySecureStopIterator**
            ](https://msdn.microsoft.com/library/windows/apps/dn986375)-Klasse</span><span class="sxs-lookup"><span data-stu-id="0d35c-160">[**PlayReadySecureStopIterator**](https://msdn.microsoft.com/library/windows/apps/dn986375) class</span></span>
-   <span data-ttu-id="0d35c-161">[**PlayReadyHardwareDRMFeatures**
            ](https://msdn.microsoft.com/library/windows/apps/dn986265)-Enumerator</span><span class="sxs-lookup"><span data-stu-id="0d35c-161">[**PlayReadyHardwareDRMFeatures**](https://msdn.microsoft.com/library/windows/apps/dn986265) enumerator</span></span>

<span data-ttu-id="0d35c-162">Es wurde ein neues Beispiel erstellt, um die Verwendung der neuen Features von PlayReady DRM zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="0d35c-162">A new sample has been created to demonstrate how to use the new features of PlayReady DRM.</span></span> <span data-ttu-id="0d35c-163">Das Beispiel kann unter [http://go.microsoft.com/fwlink/p/?linkid=331670&clcid=0x409](http://go.microsoft.com/fwlink/p/?linkid=331670) heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="0d35c-163">The sample can be downloaded from [http://go.microsoft.com/fwlink/p/?linkid=331670&clcid=0x409](http://go.microsoft.com/fwlink/p/?linkid=331670).</span></span>

## <a name="things-to-consider"></a><span data-ttu-id="0d35c-164">Zu berücksichtigende Informationen</span><span class="sxs-lookup"><span data-stu-id="0d35c-164">Things to consider</span></span>

-   <span data-ttu-id="0d35c-165">PlayReady DRM unterstützt jetzt HDCP Typ1 (unterstützt in HDCP-Version2.1 oder höher).</span><span class="sxs-lookup"><span data-stu-id="0d35c-165">PlayReady DRM now supports HDCP Type 1 (supported in HDCP version 2.1 or later).</span></span> <span data-ttu-id="0d35c-166">PlayReady enthält in der Lizenz eine zu erzwingende HDCP-Typeinschränkungsrichtlinie für das Gerät.</span><span class="sxs-lookup"><span data-stu-id="0d35c-166">PlayReady carries an HDCP Type Restriction policy in the license for the device to enforce.</span></span> <span data-ttu-id="0d35c-167">Unter Windows10 erzwingt diese Richtlinie die Einbindung von HDCP2.2 oder höher.</span><span class="sxs-lookup"><span data-stu-id="0d35c-167">On Windows 10, this policy will enforce that HDCP 2.2 or later is engaged.</span></span> <span data-ttu-id="0d35c-168">Dieses Feature kann in der PlayReady Serverv3.0SDK-Lizenz aktiviert werden. (Der Server steuert diese Richtlinie in der Lizenz mit der GUID der HDCP-Typeinschränkung).</span><span class="sxs-lookup"><span data-stu-id="0d35c-168">This feature can be enabled in your PlayReady Server v3.0 SDK license (the server controls this policy in the license using the HDCP Type Restriction GUID).</span></span> <span data-ttu-id="0d35c-169">Weitere Informationen finden Sie unter [PlayReady-Kompatibilität und Stabilitätsregeln](http://www.microsoft.com/playready/licensing/compliance/).</span><span class="sxs-lookup"><span data-stu-id="0d35c-169">For more information, see the [PlayReady Compliance and Robustness Rules](http://www.microsoft.com/playready/licensing/compliance/).</span></span>
-   <span data-ttu-id="0d35c-170">Windows Media Video (auch bekannt als VC-1) wird nicht vom Hardware-DRM unterstützt (siehe [Außerkraftsetzen des Hardware-DRM](hardware-drm.md#override-hardware-drm)).</span><span class="sxs-lookup"><span data-stu-id="0d35c-170">Windows Media Video (also known as VC-1) is not supported in hardware DRM (see [Override Hardware DRM](hardware-drm.md#override-hardware-drm)).</span></span>
-   <span data-ttu-id="0d35c-171">PlayReady DRM unterstützt jetzt den High Efficiency Video Coding (HEVC/H.265)-Videokomprimierungsstandard.</span><span class="sxs-lookup"><span data-stu-id="0d35c-171">PlayReady DRM now supports the High Efficiency Video Coding (HEVC /H.265) video compression standard.</span></span> <span data-ttu-id="0d35c-172">Zur Unterstützung von HEVC muss Ihre App Inhalte mit Common Encryption Scheme (CENC) Version2 verwenden, d.h. die Slice-Header des Inhalts bleiben unverschlüsselt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-172">To support HEVC, your app must use Common Encryption Scheme (CENC) version 2 content which includes leaving the content's slice headers in the clear.</span></span> <span data-ttu-id="0d35c-173">Weitere Informationen finden Sie in ISO/IEC 23001-7 (Information technology – MPEG systems technologies – Part 7: Common encryption in ISO base media file format files; Spezifikationsversion ISO/IEC 23001-7:2015 oder höher).</span><span class="sxs-lookup"><span data-stu-id="0d35c-173">Refer to ISO/IEC 23001-7 Information technology -- MPEG systems technologies -- Part 7: Common encryption in ISO base media file format files (Spec version ISO/IEC 23001-7:2015 or higher is required.) for more information.</span></span> <span data-ttu-id="0d35c-174">Microsoft empfiehlt außerdem die Verwendung von CENC Version2 für alle HWDRM-Inhalte.</span><span class="sxs-lookup"><span data-stu-id="0d35c-174">Microsoft also recommends using CENC version 2 for all HWDRM content.</span></span> <span data-ttu-id="0d35c-175">Zudem wird HEVC nicht von allen Hardware-DRM-Typen unterstützt (siehe [Außerkraftsetzen des Hardware-DRM](hardware-drm.md#override-hardware-drm)).</span><span class="sxs-lookup"><span data-stu-id="0d35c-175">In addition, some hardware DRM will support HEVC and some will not (see [Override Hardware DRM](hardware-drm.md#override-hardware-drm)).</span></span>
-   <span data-ttu-id="0d35c-176">Um bestimmte neue Features von PlayReady3.0 nutzen zu können (u.a. SL3000 für hardwarebasierte Clients, Abruf mehrerer nicht persistenter Lizenzen in einer Lizenzabrufnachricht und zeitbasierte Einschränkungen für nicht persistente Lizenzen), muss für den PlayReady-Server Microsoft PlayReady Server Software Development Kit v3.0.2769 oder höher verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0d35c-176">To take advantage of certain new PlayReady 3.0 features (including, but not limited to, SL3000 for hardware-based clients, acquiring multiple non-persistent licenses in one license acquisition message, and time-based restrictions on non-persistent licenses), the PlayReady server is required to be the Microsoft PlayReady Server Software Development Kit v3.0.2769 Release version or later.</span></span>
-   <span data-ttu-id="0d35c-177">Je nachdem, welche Ausgabeschutzrichtlinie in der Inhaltslizenz festgelegt ist, kann die Medienwiedergabe für Endbenutzer fehlschlagen, wenn die verbundene Ausgabe der Benutzer diese Anforderungen nicht erfüllt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-177">Depending on the Output Protection Policy specified in the content license, media playback may fail for end users if their connected output does not support those requirements.</span></span> <span data-ttu-id="0d35c-178">In der folgenden Tabelle sind die Fehler aufgeführt, die in diesem Zusammenhang häufig auftreten.</span><span class="sxs-lookup"><span data-stu-id="0d35c-178">The following table lists the set of common errors that occur as a result.</span></span> <span data-ttu-id="0d35c-179">Weitere Informationen finden Sie unter [PlayReady-Kompatibilität und Stabilitätsregeln](http://www.microsoft.com/playready/licensing/compliance/).</span><span class="sxs-lookup"><span data-stu-id="0d35c-179">For more information, see the [PlayReady Compliance and Robustness Rules](http://www.microsoft.com/playready/licensing/compliance/).</span></span>

| <span data-ttu-id="0d35c-180">Fehler</span><span class="sxs-lookup"><span data-stu-id="0d35c-180">Error</span></span>                                                   | <span data-ttu-id="0d35c-181">Wert</span><span class="sxs-lookup"><span data-stu-id="0d35c-181">Value</span></span>      | <span data-ttu-id="0d35c-182">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0d35c-182">Description</span></span>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|---------------------------------------------------------|------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="0d35c-183">ERROR\_GRAPHICS\_OPM\_OUTPUT\_DOES\_NOT\_SUPPORT\_HDCP</span><span class="sxs-lookup"><span data-stu-id="0d35c-183">ERROR\_GRAPHICS\_OPM\_OUTPUT\_DOES\_NOT\_SUPPORT\_HDCP</span></span>  | <span data-ttu-id="0d35c-184">0xC0262513</span><span class="sxs-lookup"><span data-stu-id="0d35c-184">0xC0262513</span></span> | <span data-ttu-id="0d35c-185">Die Ausgabeschutzrichtlinie der Lizenz erfordert, dass der Monitor HDCP einbindet, die Einbindung war aber nicht möglich.</span><span class="sxs-lookup"><span data-stu-id="0d35c-185">The license's Output Protection Policy requires the monitor to engage HDCP, but HDCP was unable to be engaged.</span></span>                                                                                                                                                                                                                                                                                                                                                                                              |
| <span data-ttu-id="0d35c-186">MF\_E\_POLICY\_UNSUPPORTED</span><span class="sxs-lookup"><span data-stu-id="0d35c-186">MF\_E\_POLICY\_UNSUPPORTED</span></span>                              | <span data-ttu-id="0d35c-187">0xC00D7159</span><span class="sxs-lookup"><span data-stu-id="0d35c-187">0xC00D7159</span></span> | <span data-ttu-id="0d35c-188">Die Ausgabeschutzrichtlinie der Lizenz erfordert, dass der Monitor HDCP Typ 1 einbindet, die Einbindung war aber nicht möglich.</span><span class="sxs-lookup"><span data-stu-id="0d35c-188">The license's Output Protection Policy requires the monitor to engage HDCP Type 1, but HDCP Type 1 was unable to be engaged.</span></span>                                                                                                                                                                                                                                                                                                                                                                                |
| <span data-ttu-id="0d35c-189">DRM\_E\_TEE\_OUTPUT\_PROTECTION\_REQUIREMENTS\_NOT\_MET</span><span class="sxs-lookup"><span data-stu-id="0d35c-189">DRM\_E\_TEE\_OUTPUT\_PROTECTION\_REQUIREMENTS\_NOT\_MET</span></span> | <span data-ttu-id="0d35c-190">0x8004CD22</span><span class="sxs-lookup"><span data-stu-id="0d35c-190">0x8004CD22</span></span> | <span data-ttu-id="0d35c-191">Dieser Fehlercode tritt nur bei der Verwendung des Hardware-DRM auf.</span><span class="sxs-lookup"><span data-stu-id="0d35c-191">This error code only occurs when running under hardware DRM.</span></span> <span data-ttu-id="0d35c-192">Die Ausgabeschutzrichtlinie der Lizenz erfordert, dass der Monitor HDCP einbindet oder die effektive Auflösung des Inhalts verringert, die Einbindung von HDCP war jedoch nicht möglich, und die effektive Auflösung des Inhalts konnte nicht verringert werden, weil das Hardware-DRM die Verringerung der effektiven Auflösung von Inhalten nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-192">The license's Output Protection Policy requires the monitor to engage HDCP or to reduce the content's effective resolution, but HDCP was unable to be engaged and the content's effective resolution could not be reduced because hardware DRM does not support reducing the content's resolution.</span></span> <span data-ttu-id="0d35c-193">Bei Verwendung des Software-DRM wird der Inhalt wiedergegeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-193">Under software DRM, the content plays.</span></span> <span data-ttu-id="0d35c-194">Weitere Informationen finden Sie unter [Überlegungen zur Verwendung des Hardware-DRM](hardware-drm.md#considerations-for-using-hardware-drm).</span><span class="sxs-lookup"><span data-stu-id="0d35c-194">See [Considerations for Using Hardware DRM](hardware-drm.md#considerations-for-using-hardware-drm).</span></span> |
| <span data-ttu-id="0d35c-195">ERROR\_GRAPHICS\_OPM\_NOT\_SUPPORTED</span><span class="sxs-lookup"><span data-stu-id="0d35c-195">ERROR\_GRAPHICS\_OPM\_NOT\_SUPPORTED</span></span>                    | <span data-ttu-id="0d35c-196">0xc0262500</span><span class="sxs-lookup"><span data-stu-id="0d35c-196">0xc0262500</span></span> | <span data-ttu-id="0d35c-197">Der Grafiktreiber unterstützt Ausgabeschutz nicht.</span><span class="sxs-lookup"><span data-stu-id="0d35c-197">The graphics driver does not support Output Protection.</span></span> <span data-ttu-id="0d35c-198">Dies kann z.B. der Fall sein, wenn der Monitor über VGA verbunden ist oder kein entsprechender Grafiktreiber für die digitale Ausgabe installiert ist.</span><span class="sxs-lookup"><span data-stu-id="0d35c-198">For example, the monitor is connected through VGA or an appropriate graphics driver for the digital output is not installed.</span></span> <span data-ttu-id="0d35c-199">In letzterem Fall ist in der Regel der Treiber „Microsoft Basic Display Adapter” installiert, und das Problem kann durch Installieren eines entsprechenden Grafiktreibers behoben werden.</span><span class="sxs-lookup"><span data-stu-id="0d35c-199">In the latter case, the typical driver that is installed is the Microsoft Basic Display Adapter and installing an appropriate graphics driver will resolve the issue.</span></span>                                                                                                                                                  |

## <a name="output-protection"></a><span data-ttu-id="0d35c-200">Ausgabeschutz</span><span class="sxs-lookup"><span data-stu-id="0d35c-200">Output protection</span></span>

<span data-ttu-id="0d35c-201">Im folgenden Abschnitt wird das Verhalten bei Verwendung von PlayReady DRM für Windows10 mit Ausgabeschutzrichtlinien in einer PlayReady-Lizenz beschrieben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-201">The following section describes the behavior when using PlayReady DRM for Windows 10 with output protection policies in a PlayReady license.</span></span>

<span data-ttu-id="0d35c-202">PlayReady DRM unterstützt die Ausgabeschutzebenen in der **erweiterbaren Medienrechtespezifikation von Microsoft PlayReady**.</span><span class="sxs-lookup"><span data-stu-id="0d35c-202">PlayReady DRM supports output protection levels contained in the **Microsoft PlayReady Extensible Media Rights Specification**.</span></span> <span data-ttu-id="0d35c-203">Dieses Dokument ist Teil des Dokumentationspakets, das zusammen mit lizenzierten PlayReady-Produkten bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="0d35c-203">This document can be found in the documentation pack that comes with PlayReady licensed products.</span></span>

> [!NOTE]
> <span data-ttu-id="0d35c-204">Die zulässigen Werte für Ausgabesicherheitsebenen, die von einem Lizenzserver festgelegt werden können, unterliegen den [PlayReady-Kompatibilitätsregeln](https://www.microsoft.com/playready/licensing/compliance/).</span><span class="sxs-lookup"><span data-stu-id="0d35c-204">The allowed values for output protection levels that can be set by a licensing server are governed by the [PlayReady Compliance Rules](https://www.microsoft.com/playready/licensing/compliance/).</span></span>

<span data-ttu-id="0d35c-205">PlayReady DRM ermöglicht die Wiedergabe von Inhalten mit Ausgabeschutzrichtlinien nur über Ausgabeanschlüsse gemäß Angabe in den PlayReady-Kompatibilitätsregeln.</span><span class="sxs-lookup"><span data-stu-id="0d35c-205">PlayReady DRM allows playback of content with output protection policies only on output connectors as specified in the PlayReady Compliance Rules.</span></span> <span data-ttu-id="0d35c-206">Weitere Informationen zu in den PlayReady-Kompatibilitätsregeln angegebenen Ausgabeanschlussbedingungen finden Sie in den [definierten Bedingungen für PlayReady-Kompatibilität und Stabilitätsregeln](https://www.microsoft.com/playready/licensing/compliance/).</span><span class="sxs-lookup"><span data-stu-id="0d35c-206">For more information about output connector terms specified in the PlayReady Compliance Rules, see [Defined Terms for PlayReady Compliance and Robustness Rules](https://www.microsoft.com/playready/licensing/compliance/).</span></span>

<span data-ttu-id="0d35c-207">Dieser Abschnitt konzentriert sich auf Ausgabeschutzszenarien mit PlayReady DRM für Windows10 und PlayReady Hardware DRM für Windows10 (auch auf einigen Windows-Clients verfügbar).</span><span class="sxs-lookup"><span data-stu-id="0d35c-207">This section focuses on output protection scenarios with PlayReady DRM for Windows 10 and PlayReady Hardware DRM for Windows 10, which is also available on some Windows clients.</span></span> <span data-ttu-id="0d35c-208">Mit PlayReady HWDRM wird der gesamte Ausgabeschutz innerhalb der Windows-TEE-Implementierung erzwungen (siehe [Hardware-DRM](hardware-drm.md)).</span><span class="sxs-lookup"><span data-stu-id="0d35c-208">With PlayReady HWDRM, all output protections are enforced from within the Windows TEE implementation (see [Hardware DRM](hardware-drm.md)).</span></span> <span data-ttu-id="0d35c-209">Aus diesem Grund unterscheidet sich das Verhalten in einigen Fällen von der Verwendung von PlayReady SWDRM (Software-DRM):</span><span class="sxs-lookup"><span data-stu-id="0d35c-209">As a result, some behaviors differ from when using PlayReady SWDRM (software DRM):</span></span>

* <span data-ttu-id="0d35c-210">Unterstützung der Ausgabeschutzebene270 (Output Protection Level, OPL) für nicht komprimierte digitale Videos: PlayReady HWDRM für Windows10 unterstützt keine Abwärtsauflösung und erzwingt die Einbindung von HDCP (High-bandwidth Digital Content Protection).</span><span class="sxs-lookup"><span data-stu-id="0d35c-210">Support for Output Protection Level (OPL) for Uncompressed Digital Video 270: PlayReady HWDRM for Windows 10 doesn't support down-resolution and will enforce that HDCP (High-bandwidth Digital Content Protection) is engaged.</span></span> <span data-ttu-id="0d35c-211">Es empfiehlt sich, bei HD-Inhalten für das HWDRM einen OPL-Wert zu verwenden, der größer als270 ist (dies ist jedoch nicht zwingend erforderlich).</span><span class="sxs-lookup"><span data-stu-id="0d35c-211">It is recommended that high definition content for HWDRM have an OPL greater than 270 (although it is not required).</span></span> <span data-ttu-id="0d35c-212">Darüber hinaus sollten Sie die HDCP-Typeinschränkung in der Lizenz festlegen (HDCP-Version2.2 oder höher).</span><span class="sxs-lookup"><span data-stu-id="0d35c-212">Additionally, you should set HDCP type restriction in the license (HDCP version 2.2 or later).</span></span>
* <span data-ttu-id="0d35c-213">Im Gegensatz zum SWDRM wird beim HWDRM der Ausgabeschutz für alle Monitore basierend auf dem langsamsten Monitor erzwungen.</span><span class="sxs-lookup"><span data-stu-id="0d35c-213">Unlike SWDRM, with HWDRM, output protections are enforced on all monitors based on the least capable monitor.</span></span> <span data-ttu-id="0d35c-214">Wenn der Benutzer beispielsweise zwei Monitore angeschlossen hat und nur einer davon HDCP unterstützt, ist die Wiedergabe nicht möglich, falls die Lizenz HDCP erfordert. Dies gilt auch dann, wenn der Inhalt nur auf dem Monitor gerendert wird, der HDCP unterstützt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-214">For example, if the user has two monitors connected where one supports HDCP and the other doesn't, playback will fail if the license requires HDCP even if the content is only being rendered on the monitor that supports HDCP.</span></span> <span data-ttu-id="0d35c-215">Beim SWDRM wird der Inhalt wiedergegeben, solange das Rendering nur auf dem Monitor erfolgt, der HDCP unterstützt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-215">In SWDRM, content will play back as long as it's only being rendered on the monitor that supports HDCP.</span></span>
* <span data-ttu-id="0d35c-216">Es ist nicht garantiert, dass das HWDRM vom Client verwendet wird und dass das Verfahren sicher ist, es sei denn, von den Inhaltsschlüsseln und -lizenzen werden die folgenden Bedingungen erfüllt:</span><span class="sxs-lookup"><span data-stu-id="0d35c-216">HWDRM is not guaranteed to be used by the client and secure unless the following conditions are met by the content keys and licenses:</span></span>
    * <span data-ttu-id="0d35c-217">Die für den Videoinhaltsschlüssel verwendete Lizenz muss mindestens die Sicherheitsstufe3.000 besitzen.</span><span class="sxs-lookup"><span data-stu-id="0d35c-217">The license used for the video content key must have a minimum security level of 3000.</span></span>
    * <span data-ttu-id="0d35c-218">Audiodaten müssen mit einem anderen Inhaltsschlüssel verschlüsselt werden als Videodaten, und die für Audiodaten verwendete Lizenz muss mindestens die Sicherheitsstufe2.000 besitzen.</span><span class="sxs-lookup"><span data-stu-id="0d35c-218">Audio must be encrypted to a different content key than video, and the license used for audio must have a minimum security level of 2000.</span></span> <span data-ttu-id="0d35c-219">Alternativ können Audiodaten auch unverschlüsselt bleiben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-219">Alternatively, audio could be left in the clear.</span></span>
* <span data-ttu-id="0d35c-220">In allen SWDRM-Szenarien darf die Sicherheitsebene der PlayReady-Lizenz für den Audio- und/oder Videoinhaltsschlüssel maximal2.000 betragen.</span><span class="sxs-lookup"><span data-stu-id="0d35c-220">All SWDRM scenarios require that the minimum security level of the PlayReady license used for the audio and/or video content key is lower or equal to 2000.</span></span>

### <a name="output-protection-levels"></a><span data-ttu-id="0d35c-221">Ausgabeschutzebenen</span><span class="sxs-lookup"><span data-stu-id="0d35c-221">Output protection levels</span></span>

<span data-ttu-id="0d35c-222">Die folgende Tabelle veranschaulicht die Zuordnungen zwischen verschiedenen OPLs in der PlayReady-Lizenz und deren Erzwingung durch PlayReady DRM für Windows10:</span><span class="sxs-lookup"><span data-stu-id="0d35c-222">The following table outlines the mappings between various OPLs in the PlayReady license and how PlayReady DRM for Windows 10 enforces them.</span></span>

#### <a name="video"></a><span data-ttu-id="0d35c-223">Video</span><span class="sxs-lookup"><span data-stu-id="0d35c-223">Video</span></span>

<table>
    <tr>
        <th rowspan="2"><span data-ttu-id="0d35c-224">OPL</span><span class="sxs-lookup"><span data-stu-id="0d35c-224">OPL</span></span></th>
        <th><span data-ttu-id="0d35c-225">Komprimierte digitale Videos</span><span class="sxs-lookup"><span data-stu-id="0d35c-225">Compressed digital video</span></span></th>
        <th colspan="2"><span data-ttu-id="0d35c-226">Unkomprimierte digitale Videos</span><span class="sxs-lookup"><span data-stu-id="0d35c-226">Uncompressed digital video</span></span></th>
        <th><span data-ttu-id="0d35c-227">TV (analog)</span><span class="sxs-lookup"><span data-stu-id="0d35c-227">Analog TV</span></span></th>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-228">Beliebig</span><span class="sxs-lookup"><span data-stu-id="0d35c-228">Any</span></span></th>
        <th colspan="2"><span data-ttu-id="0d35c-229">HDMI, DVI, DisplayPort, MHL</span><span class="sxs-lookup"><span data-stu-id="0d35c-229">HDMI, DVI, DisplayPort, MHL</span></span></th>
        <th><span data-ttu-id="0d35c-230">Komponente, Composite</span><span class="sxs-lookup"><span data-stu-id="0d35c-230">Component, Composite</span></span></th>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-231">100</span><span class="sxs-lookup"><span data-stu-id="0d35c-231">100</span></span></th>
        <td rowspan="6"><span data-ttu-id="0d35c-232">Nicht zutreffend\*</span><span class="sxs-lookup"><span data-stu-id="0d35c-232">N/A\*</span></span></td>
        <td colspan="2"><span data-ttu-id="0d35c-233">Inhalt wird übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-233">Passes content</span></span></td>
        <td><span data-ttu-id="0d35c-234">Inhalt wird übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-234">Passes content</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-235">150</span><span class="sxs-lookup"><span data-stu-id="0d35c-235">150</span></span></th>
        <td colspan="2" rowspan="2"><span data-ttu-id="0d35c-236">Nicht zutreffend\*</span><span class="sxs-lookup"><span data-stu-id="0d35c-236">N/A\*</span></span></td>
        <td><span data-ttu-id="0d35c-237">Inhalt wird übergeben, wenn CGMS-A CopyNever eingebunden wird oder CGMS-A nicht eingebunden werden kann.</span><span class="sxs-lookup"><span data-stu-id="0d35c-237">Passes content when CGMS-A CopyNever is engaged or if CGMS-A can't be engaged</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-238">200</span><span class="sxs-lookup"><span data-stu-id="0d35c-238">200</span></span></th>
        <td><span data-ttu-id="0d35c-239">Inhalt wird übergeben, wenn CGMS-A CopyNever eingebunden wird.</span><span class="sxs-lookup"><span data-stu-id="0d35c-239">Passes content when CGMS-A CopyNever is engaged</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-240">250</span><span class="sxs-lookup"><span data-stu-id="0d35c-240">250</span></span></th>
        <td colspan="2"><span data-ttu-id="0d35c-241">Versucht, HDCP einzubinden, der Inhalt wird jedoch unabhängig vom Ergebnis übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-241">Attempts to engage HDCP, but passes content regardless of result</span></span></td>
        <td rowspan="5"><span data-ttu-id="0d35c-242">Nicht zutreffend\*</span><span class="sxs-lookup"><span data-stu-id="0d35c-242">N/A\*</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-243">270</span><span class="sxs-lookup"><span data-stu-id="0d35c-243">270</span></span></th>
        <td><span data-ttu-id="0d35c-244">**SWDRM**: Versucht, HDCP einzubinden.</span><span class="sxs-lookup"><span data-stu-id="0d35c-244">**SWDRM**: Attempts to engage HDCP.</span></span> <span data-ttu-id="0d35c-245">Sollte die Einbindung von HDCP nicht möglich sein, schränkt der PC die effektive Auflösung auf 520.000Pixel pro Frame ein und übergibt den Inhalt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-245">If HDCP fails to engage, the PC will constrain the effective resolution to 520,000 pixels per frame and pass the content</span></span></td>
        <td><span data-ttu-id="0d35c-246">**HWDRM**: Inhalt wird mit HDCP übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-246">**HWDRM**: Passes content with HDCP.</span></span> <span data-ttu-id="0d35c-247">Wenn die Einbindung von HDCP nicht möglich ist, wird die Wiedergabe über HDMI/DVI-Anschlüsse blockiert.</span><span class="sxs-lookup"><span data-stu-id="0d35c-247">If HDCP fails to engage, playback to HDMI/DVI ports is blocked</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-248">300</span><span class="sxs-lookup"><span data-stu-id="0d35c-248">300</span></span></th>
        <td colspan="2">
            <p><span data-ttu-id="0d35c-249">
                **Wenn die HDCP-Typbeschränkung NICHT definiert ist:** Inhalt wird mit HDCP übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-249">
                **When HDCP type restriction is NOT defined:** Passes content with HDCP.</span></span> <span data-ttu-id="0d35c-250">Sollte die Einbindung von HDCP nicht möglich sein, wird die Wiedergabe über HDMI/DVI-Anschlüsse blockiert.</span><span class="sxs-lookup"><span data-stu-id="0d35c-250">If HDCP fails to engage, playback to HDMI/DVI ports is blocked.</span></span>
            </p>
            <p><span data-ttu-id="0d35c-251">
                **Wenn die HDCP-Typeinschränkung definiert ist**: Inhalt wird mit HDCP2.2 und Inhaltsdatenstrom-Typ„1“ übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-251">
                **When HDCP type restriction IS defined**: Passes content with HDCP 2.2 and content stream type set to 1.</span></span> <span data-ttu-id="0d35c-252">Wenn die Einbindung von HDCP nicht möglich ist oder der Inhaltsdatenstromtyp nicht auf 1 festgelegt werden kann, wird die Wiedergabe über HDMI/DVI-Anschlüsse blockiert.</span><span class="sxs-lookup"><span data-stu-id="0d35c-252">If HDCP fails to engage or content stream type can't be set to 1, playback to HDMI/DVI ports is blocked.</span></span>
            </p>
        </td>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-253">400</span><span class="sxs-lookup"><span data-stu-id="0d35c-253">400</span></span></th>
        <td rowspan="2"><span data-ttu-id="0d35c-254">Windows10 übergibt komprimierte digitale Videoinhalte niemals an Ausgaben, unabhängig vom nachfolgenden OPL-Wert.</span><span class="sxs-lookup"><span data-stu-id="0d35c-254">Windows 10 never passes compressed digital video content to outputs, regardless of the subsequent OPL value.</span></span> <span data-ttu-id="0d35c-255">Weitere Informationen zu komprimierten digitalen Videoinhalten finden Sie in den [Kompatibilitätsregeln für PlayReady-Produkte](https://www.microsoft.com/playready/licensing/compliance/).</span><span class="sxs-lookup"><span data-stu-id="0d35c-255">For more information about compressed digital video content, see the [Compliance Rules for PlayReady Products](https://www.microsoft.com/playready/licensing/compliance/).</span></span></td>
        <td colspan="2" rowspan="2"><span data-ttu-id="0d35c-256">Nicht zutreffend\*</span><span class="sxs-lookup"><span data-stu-id="0d35c-256">N/A\*</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-257">500</span><span class="sxs-lookup"><span data-stu-id="0d35c-257">500</span></span></th>
    </tr>
</table>
<br/>

<span data-ttu-id="0d35c-258">\* Nicht alle Werte für Ausgabeschutzebenen können von einem Lizenzserver festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="0d35c-258">\* Not all values for output protection levels can be set by a licensing server.</span></span> <span data-ttu-id="0d35c-259">Weitere Informationen finden Sie unter [PlayReady-Kompatibilitätsregeln](https://www.microsoft.com/playready/licensing/compliance/).</span><span class="sxs-lookup"><span data-stu-id="0d35c-259">For more information, see the [PlayReady Compliance Rules](https://www.microsoft.com/playready/licensing/compliance/).</span></span>

#### <a name="audio"></a><span data-ttu-id="0d35c-260">Audio</span><span class="sxs-lookup"><span data-stu-id="0d35c-260">Audio</span></span>

<table>
    <tr>
        <th rowspan="2"><span data-ttu-id="0d35c-261">OPL</span><span class="sxs-lookup"><span data-stu-id="0d35c-261">OPL</span></span></th>
        <th><span data-ttu-id="0d35c-262">Komprimierte digitale Audiodaten</span><span class="sxs-lookup"><span data-stu-id="0d35c-262">Compressed digital audio</span></span></th>
        <th><span data-ttu-id="0d35c-263">Unkomprimierte digitale Audiodaten</span><span class="sxs-lookup"><span data-stu-id="0d35c-263">Uncompressed digital audio</span></span></th>
        <th><span data-ttu-id="0d35c-264">Analog- oder USB-Audio</span><span class="sxs-lookup"><span data-stu-id="0d35c-264">Analog or USB audio</span></span></th>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-265">HDMI, DisplayPort, MHL</span><span class="sxs-lookup"><span data-stu-id="0d35c-265">HDMI, DisplayPort, MHL</span></span></th>
        <th><span data-ttu-id="0d35c-266">HDMI, DisplayPort, MHL</span><span class="sxs-lookup"><span data-stu-id="0d35c-266">HDMI, DisplayPort, MHL</span></span></th>
        <th><span data-ttu-id="0d35c-267">Any</span><span class="sxs-lookup"><span data-stu-id="0d35c-267">Any</span></span></th>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-268">100</span><span class="sxs-lookup"><span data-stu-id="0d35c-268">100</span></span></th>
        <td rowspan="3"><span data-ttu-id="0d35c-269">Inhalt wird übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-269">Passes content</span></span></td>
        <td><span data-ttu-id="0d35c-270">Inhalt wird übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-270">Passes content</span></span></td>
        <td rowspan="5"><span data-ttu-id="0d35c-271">Inhalt wird übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-271">Passes content</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-272">150</span><span class="sxs-lookup"><span data-stu-id="0d35c-272">150</span></span></th>
        <td rowspan="4"><span data-ttu-id="0d35c-273">Inhalt wird NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-273">Does NOT pass content</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-274">200</span><span class="sxs-lookup"><span data-stu-id="0d35c-274">200</span></span></th>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-275">250</span><span class="sxs-lookup"><span data-stu-id="0d35c-275">250</span></span></th>
        <td><span data-ttu-id="0d35c-276">Inhalt wird übergeben, wenn HDCP für HDMI, DisplayPort oder MHL eingebunden wird oder SCMS eingebunden und auf „CopyNever“ festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="0d35c-276">Passes content when HDCP is engaged on HDMI, DisplayPort, or MHL, or when SCMS is engaged and set to CopyNever</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-277">300</span><span class="sxs-lookup"><span data-stu-id="0d35c-277">300</span></span></th>
        <td><span data-ttu-id="0d35c-278">Inhalt wird übergeben, wenn HDCP für HDMI, DisplayPort oder MHL eingebunden wird.</span><span class="sxs-lookup"><span data-stu-id="0d35c-278">Passes content when HDCP is engaged on HDMI, DisplayPort, or MHL</span></span></td>
    </tr>
</table>
<br/>

### <a name="miracast"></a><span data-ttu-id="0d35c-279">Miracast</span><span class="sxs-lookup"><span data-stu-id="0d35c-279">Miracast</span></span>

<span data-ttu-id="0d35c-280">PlayReady DRM ermöglicht die Wiedergabe von Inhalten per Miracast-Ausgabe, sobald HDCP2.0 oder höher eingebunden wird.</span><span class="sxs-lookup"><span data-stu-id="0d35c-280">PlayReady DRM allows you to play content over Miracast output as soon as HDCP 2.0 or later is engaged.</span></span> <span data-ttu-id="0d35c-281">Unter Windows10 gilt Miracast jedoch als *digitale* Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="0d35c-281">On Windows 10, however, Miracast is considered a *digital* output.</span></span> <span data-ttu-id="0d35c-282">Weitere Informationen zu Miracast-Szenarien finden Sie in den [PlayReady-Kompatibilitätsregeln](https://www.microsoft.com/playready/licensing/compliance/).</span><span class="sxs-lookup"><span data-stu-id="0d35c-282">For more information about Miracast scenarios, see the [PlayReady Compliance Rules](https://www.microsoft.com/playready/licensing/compliance/).</span></span> <span data-ttu-id="0d35c-283">Die folgende Tabelle veranschaulicht die Zuordnungen zwischen verschiedenen OPLs in der PlayReady-Lizenz und deren Erzwingung durch PlayReady DRM für Miracast-Ausgaben:</span><span class="sxs-lookup"><span data-stu-id="0d35c-283">The following table outlines the mappings between various OPLs in the PlayReady license and how PlayReady DRM enforces them on Miracast outputs.</span></span>

<table>
    <tr>
        <th><span data-ttu-id="0d35c-284">OPL</span><span class="sxs-lookup"><span data-stu-id="0d35c-284">OPL</span></span></th>
        <th><span data-ttu-id="0d35c-285">Komprimierte digitale Audiodaten</span><span class="sxs-lookup"><span data-stu-id="0d35c-285">Compressed digital audio</span></span></th>
        <th><span data-ttu-id="0d35c-286">Unkomprimierte digitale Audiodaten</span><span class="sxs-lookup"><span data-stu-id="0d35c-286">Uncompressed digital audio</span></span></th>
        <th><span data-ttu-id="0d35c-287">Komprimierte digitale Videos</span><span class="sxs-lookup"><span data-stu-id="0d35c-287">Compressed digital video</span></span></th>
        <th><span data-ttu-id="0d35c-288">Unkomprimierte digitale Videos</span><span class="sxs-lookup"><span data-stu-id="0d35c-288">Uncompressed digital video</span></span></th>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-289">100</span><span class="sxs-lookup"><span data-stu-id="0d35c-289">100</span></span></th>
        <td rowspan="4"><span data-ttu-id="0d35c-290">Inhalt wird übergeben, wenn HDCP2.0 oder höher eingebunden wird.</span><span class="sxs-lookup"><span data-stu-id="0d35c-290">Passes content when HDCP 2.0 or later is engaged.</span></span> <span data-ttu-id="0d35c-291">Wenn die Einbindung nicht erfolgreich ist, wird der Inhalt NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-291">If it fails to engage, it does NOT pass content</span></span></td>
        <td><span data-ttu-id="0d35c-292">Inhalt wird übergeben, wenn HDCP2.0 oder höher eingebunden wird.</span><span class="sxs-lookup"><span data-stu-id="0d35c-292">Passes content when HDCP 2.0 or later is engaged.</span></span> <span data-ttu-id="0d35c-293">Wenn die Einbindung nicht erfolgreich ist, wird der Inhalt NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-293">If it fails to engage, it does NOT pass content</span></span></td>
        <td rowspan="6"><span data-ttu-id="0d35c-294">Nicht zutreffend\*</span><span class="sxs-lookup"><span data-stu-id="0d35c-294">N/A\*</span></span></td>
        <td><span data-ttu-id="0d35c-295">Inhalt wird übergeben, wenn HDCP2.0 oder höher eingebunden wird.</span><span class="sxs-lookup"><span data-stu-id="0d35c-295">Passes content when HDCP 2.0 or later is engaged.</span></span> <span data-ttu-id="0d35c-296">Wenn die Einbindung nicht erfolgreich ist, wird der Inhalt NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-296">If it fails to engage, it does NOT pass content</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-297">150</span><span class="sxs-lookup"><span data-stu-id="0d35c-297">150</span></span></th>
        <td rowspan="3"><span data-ttu-id="0d35c-298">Inhalt wird NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-298">Does NOT pass content</span></span></td>
        <td rowspan="2"><span data-ttu-id="0d35c-299">Nicht zutreffend\*</span><span class="sxs-lookup"><span data-stu-id="0d35c-299">N/A\*</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-300">200</span><span class="sxs-lookup"><span data-stu-id="0d35c-300">200</span></span></th>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-301">250</span><span class="sxs-lookup"><span data-stu-id="0d35c-301">250</span></span></th>
        <td rowspan="2"><span data-ttu-id="0d35c-302">Inhalt wird übergeben, wenn HDCP2.0 oder höher eingebunden wird.</span><span class="sxs-lookup"><span data-stu-id="0d35c-302">Passes content when HDCP 2.0 or later is engaged.</span></span> <span data-ttu-id="0d35c-303">Wenn die Einbindung nicht erfolgreich ist, wird der Inhalt NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-303">If it fails to engage, it does NOT pass content</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-304">270</span><span class="sxs-lookup"><span data-stu-id="0d35c-304">270</span></span></th>
        <td colspan="2"><span data-ttu-id="0d35c-305">Nicht zutreffend\*</span><span class="sxs-lookup"><span data-stu-id="0d35c-305">N/A\*</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-306">300</span><span class="sxs-lookup"><span data-stu-id="0d35c-306">300</span></span></th>
        <td><span data-ttu-id="0d35c-307">Inhalt wird übergeben, wenn HDCP2.0 oder höher eingebunden wird.</span><span class="sxs-lookup"><span data-stu-id="0d35c-307">Passes content when HDCP 2.0 or later is engaged.</span></span> <span data-ttu-id="0d35c-308">Wenn die Einbindung nicht erfolgreich ist, wird der Inhalt NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-308">If it fails to engage, it does NOT pass content</span></span></td>
        <td><span data-ttu-id="0d35c-309">Inhalt wird NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-309">Does NOT pass content</span></span></td>
        <td>
            <p><span data-ttu-id="0d35c-310">
                **Wenn die HDCP-Typeinschränkung NICHT definiert ist:** Inhalt wird übergeben, wenn HDCP2.0 oder höher aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="0d35c-310">
                **When HDCP type restriction is NOT defined:** Passes content when HDCP 2.0 or later is engaged.</span></span> <span data-ttu-id="0d35c-311">Wenn die Einbindung nicht erfolgreich ist, wird der Inhalt NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-311">If it fails to engage, it does NOT pass content.</span></span>
            </p>
            <p><span data-ttu-id="0d35c-312">
                **Wenn die HDCP-Typeinschränkung definiert ist**: Inhalt wird mit HDCP2.2 und Inhaltsdatenstrom-Typ„1“ übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-312">
                **When HDCP type restriction IS defined:** Passes content with HDCP 2.2 and content stream type set to 1.</span></span> <span data-ttu-id="0d35c-313">Wenn die Einbindung von HDCP nicht möglich ist oder der Inhaltsdatenstromtyp nicht auf 1 festgelegt werden kann, wird der Inhalt NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-313">If HDCP fails to engage or content stream type can't be set to 1, it does NOT pass content.</span></span>
            </p>        
        </td>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-314">400</span><span class="sxs-lookup"><span data-stu-id="0d35c-314">400</span></span></th>
        <td rowspan="2" colspan="2"><span data-ttu-id="0d35c-315">Nicht zutreffend\*</span><span class="sxs-lookup"><span data-stu-id="0d35c-315">N/A\*</span></span></td>
        <td rowspan="2"><span data-ttu-id="0d35c-316">Windows10 übergibt komprimierte digitale Videoinhalte niemals an Ausgaben, unabhängig vom nachfolgenden OPL-Wert.</span><span class="sxs-lookup"><span data-stu-id="0d35c-316">Windows 10 never passes compressed digital video content to outputs, regardless of the subsequent OPL value.</span></span> <span data-ttu-id="0d35c-317">Weitere Informationen zu komprimierten digitalen Videoinhalten finden Sie in den [Kompatibilitätsregeln für PlayReady-Produkte](https://www.microsoft.com/playready/licensing/compliance/).</span><span class="sxs-lookup"><span data-stu-id="0d35c-317">For more information about compressed digital video content, see the [Compliance Rules for PlayReady Products](https://www.microsoft.com/playready/licensing/compliance/).</span></span></td>
        <td rowspan="2"><span data-ttu-id="0d35c-318">Nicht zutreffend\*</span><span class="sxs-lookup"><span data-stu-id="0d35c-318">N/A\*</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-319">500</span><span class="sxs-lookup"><span data-stu-id="0d35c-319">500</span></span></th>
    </tr>
</table>
<br/>

<span data-ttu-id="0d35c-320">\* Nicht alle Werte für Ausgabeschutzebenen können von einem Lizenzserver festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="0d35c-320">\* Not all values for output protection levels can be set by a licensing server.</span></span> <span data-ttu-id="0d35c-321">Weitere Informationen finden Sie unter [PlayReady-Kompatibilitätsregeln](https://www.microsoft.com/playready/licensing/compliance/).</span><span class="sxs-lookup"><span data-stu-id="0d35c-321">For more information, see the [PlayReady Compliance Rules](https://www.microsoft.com/playready/licensing/compliance/).</span></span>

### <a name="additional-explicit-output-restrictions"></a><span data-ttu-id="0d35c-322">Zusätzliche explizite Ausgabeeinschränkungen</span><span class="sxs-lookup"><span data-stu-id="0d35c-322">Additional explicit output restrictions</span></span>

<span data-ttu-id="0d35c-323">Die folgende Tabelle beschreibt die Implementierung expliziter Einschränkungen des Ausgabeschutzes für digitale Videos von PlayReady DRM für Windows10:</span><span class="sxs-lookup"><span data-stu-id="0d35c-323">The following table describes the PlayReady DRM for Windows 10 implementation of explicit digital video output protection restrictions.</span></span>

<table>
    <tr>
        <th><span data-ttu-id="0d35c-324">Szenario</span><span class="sxs-lookup"><span data-stu-id="0d35c-324">Scenario</span></span></th>
        <th><span data-ttu-id="0d35c-325">GUID</span><span class="sxs-lookup"><span data-stu-id="0d35c-325">GUID</span></span></th>
        <th><span data-ttu-id="0d35c-326">Situation</span><span class="sxs-lookup"><span data-stu-id="0d35c-326">If...</span></span></th>
        <th><span data-ttu-id="0d35c-327">Folge</span><span class="sxs-lookup"><span data-stu-id="0d35c-327">Then...</span></span></th>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-328">Maximale effektive Auflösung (Decodierungsgröße)</span><span class="sxs-lookup"><span data-stu-id="0d35c-328">Maximum effective resolution decode size</span></span></th>
        <td><span data-ttu-id="0d35c-329">9645E831-E01D-4FFF-8342-0A720E3E028F</span><span class="sxs-lookup"><span data-stu-id="0d35c-329">9645E831-E01D-4FFF-8342-0A720E3E028F</span></span></td>
        <td><span data-ttu-id="0d35c-330">Verbundene Ausgabe: digitale Videoausgabe, Miracast, HDMI, DVI usw.</span><span class="sxs-lookup"><span data-stu-id="0d35c-330">Connected output is: digital video output, Miracast, HDMI, DVI, etc.</span></span></td>
        <td>
            <p>
                <span data-ttu-id="0d35c-331">Inhalt wird übergeben, wenn folgende Einschränkungen vorliegen:</span><span class="sxs-lookup"><span data-stu-id="0d35c-331">Passes content when constrained to:</span></span>  
            </p>
            <ul>
                <li><span data-ttu-id="0d35c-332">(a) Die Breite des Frames muss kleiner oder gleich der maximalen Framebreite (in Pixel) und die Höhe des Frames muss kleiner oder gleich der maximalen Framehöhe (in Pixel) sein. Oder:</span><span class="sxs-lookup"><span data-stu-id="0d35c-332">(a) the width of the frame must be less than or equal to the maximum frame width in pixels and the height of the frame less than or equal to the maximum frame height in pixels, or</span></span></li>
                <li><span data-ttu-id="0d35c-333">(a) Die Höhe des Frames muss kleiner oder gleich der maximalen Framebreite (in Pixel) und die Breite des Frames muss kleiner oder gleich der maximalen Framehöhe (in Pixel) sein.</span><span class="sxs-lookup"><span data-stu-id="0d35c-333">(b) the height of the frame must be less than or equal to the maximum frame width in pixels and the width of the frame less than or equal to the maximum frame height in pixels</span></span></li>
            </ul>                   
        </td>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-334">HDCP-Typeinschränkung</span><span class="sxs-lookup"><span data-stu-id="0d35c-334">HDCP type restriction</span></span></th>
        <td><span data-ttu-id="0d35c-335">ABB2C6F1-E663-4625-A945-972D17B231E7</span><span class="sxs-lookup"><span data-stu-id="0d35c-335">ABB2C6F1-E663-4625-A945-972D17B231E7</span></span></td>
        <td><span data-ttu-id="0d35c-336">Verbundene Ausgabe: digitale Videoausgabe, Miracast, HDMI, DVI usw.</span><span class="sxs-lookup"><span data-stu-id="0d35c-336">Connected output is: digital video output, Miracast, HDMI, DVI, etc.</span></span></td>
        <td><span data-ttu-id="0d35c-337">Inhalt wird mit HDCP2.2 und Inhaltsdatenstrom-Typ „1“ übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-337">Passes content with HDCP 2.2 and the content stream type set to 1.</span></span> <span data-ttu-id="0d35c-338">Sollte die Einbindung von HDCP2.2 nicht möglich sein oder der Inhaltsdatenstrom-Typ nicht auf „1“ festgelegt werden können, wird der Inhalt NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-338">If HDCP 2.2 fails to engage or the content stream type can't be set to 1, it does NOT pass content.</span></span> <span data-ttu-id="0d35c-339">Außerdem muss die Ausgabeschutzebene für unkomprimierte digitale Videos muss mindestens auf271 festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="0d35c-339">Uncompressed digital video output protection level of a value greater than or equal to 271 must also be specified</span></span></td>
    </tr>
</table>
<br/>

<span data-ttu-id="0d35c-340">Die folgende Tabelle beschreibt die Implementierung expliziter Einschränkungen des Ausgabeschutzes für analoge Videos von PlayReady DRM für Windows10.</span><span class="sxs-lookup"><span data-stu-id="0d35c-340">The following table describes the PlayReady DRM for Windows 10 implementation of explicit analog video output protection restrictions.</span></span>

<table>
    <tr>
        <th><span data-ttu-id="0d35c-341">Szenario</span><span class="sxs-lookup"><span data-stu-id="0d35c-341">Scenario</span></span></th>
        <th><span data-ttu-id="0d35c-342">GUID</span><span class="sxs-lookup"><span data-stu-id="0d35c-342">GUID</span></span></th>
        <th><span data-ttu-id="0d35c-343">Situation</span><span class="sxs-lookup"><span data-stu-id="0d35c-343">If...</span></span></th>
        <th colspan="2"><span data-ttu-id="0d35c-344">Folge</span><span class="sxs-lookup"><span data-stu-id="0d35c-344">Then...</span></span></th>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-345">Analoger Computermonitor</span><span class="sxs-lookup"><span data-stu-id="0d35c-345">Analog computer monitor</span></span></th>
        <td><span data-ttu-id="0d35c-346">D783A191-E083-4BAF-B2DA-E69F910B3772</span><span class="sxs-lookup"><span data-stu-id="0d35c-346">D783A191-E083-4BAF-B2DA-E69F910B3772</span></span></td>
        <td><span data-ttu-id="0d35c-347">Verbundene Ausgabe: VGA, DVI&ndash;analog usw.</span><span class="sxs-lookup"><span data-stu-id="0d35c-347">Connected output is: VGA, DVI&ndash;analog, etc.</span></span></td>
        <td><span data-ttu-id="0d35c-348">**SWDRM:** Der PC schränkt die effektive Auflösung auf 520.000epx pro Frame ein und übergibt den Inhalt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-348">**SWDRM:** PC will constrain effective resolution to 520,000 epx per frame and pass content</span></span></td>
        <td><span data-ttu-id="0d35c-349">**HWDRM:** Inhalt wird NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-349">**HWDRM:** Does NOT pass content</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-350">Analoge Komponente</span><span class="sxs-lookup"><span data-stu-id="0d35c-350">Analog component</span></span></th>
        <td><span data-ttu-id="0d35c-351">811C5110-46C8-4C6E-8163-C0482A15D47E</span><span class="sxs-lookup"><span data-stu-id="0d35c-351">811C5110-46C8-4C6E-8163-C0482A15D47E</span></span></td>
        <td><span data-ttu-id="0d35c-352">Verbundene Ausgabe: Komponente</span><span class="sxs-lookup"><span data-stu-id="0d35c-352">Connected output is: component</span></span></td>
        <td><span data-ttu-id="0d35c-353">**SWDRM:** Der PC schränkt die effektive Auflösung auf 520.000epx pro Frame ein und übergibt den Inhalt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-353">**SWDRM:** PC will constrain effective resolution to 520,000 epx per frame and pass content</span></span></td>
        <td><span data-ttu-id="0d35c-354">**HWDRM:** Inhalt wird NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-354">**HWDRM:** Does NOT pass content</span></span></td>
    </tr>
    <tr>
        <th rowspan="2"><span data-ttu-id="0d35c-355">Analoge TV-Ausgaben</span><span class="sxs-lookup"><span data-stu-id="0d35c-355">Analog TV outputs</span></span></th>
        <td><span data-ttu-id="0d35c-356">2098DE8D-7DDD-4BAB-96C6-32EBB6FABEA3</span><span class="sxs-lookup"><span data-stu-id="0d35c-356">2098DE8D-7DDD-4BAB-96C6-32EBB6FABEA3</span></span></td>
        <td><span data-ttu-id="0d35c-357">OPL für Analog-TV ist kleiner als151.</span><span class="sxs-lookup"><span data-stu-id="0d35c-357">Analog TV OPL is less than 151</span></span></td>
        <td colspan="2"><span data-ttu-id="0d35c-358">CGMS-A muss eingebunden werden.</span><span class="sxs-lookup"><span data-stu-id="0d35c-358">CGMS-A must be engaged</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="0d35c-359">225CD36F-F132-49EF-BA8C-C91EA28E4369</span><span class="sxs-lookup"><span data-stu-id="0d35c-359">225CD36F-F132-49EF-BA8C-C91EA28E4369</span></span></td>
        <td><span data-ttu-id="0d35c-360">OPL für Analog-TV ist kleiner als101, und „2098DE8D-7DDD-4BAB-96C6-32EBB6FABEA3“ ist nicht in der Lizenz enthalten.</span><span class="sxs-lookup"><span data-stu-id="0d35c-360">Analog TV OPL is less than 101 and license doesn't contain 2098DE8D-7DDD-4BAB-96C6-32EBB6FABEA3</span></span></td>
        <td colspan="2"><span data-ttu-id="0d35c-361">Einbindung von CGMS-A muss versucht werden, der Inhalt kann jedoch unabhängig vom Ergebnis wiedergegeben werden.</span><span class="sxs-lookup"><span data-stu-id="0d35c-361">CGMS-A engagement must be attempted, but content may play regardless of result</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-362">Automatische Verstärkungsregelung und Farbstreifen</span><span class="sxs-lookup"><span data-stu-id="0d35c-362">Automatic gain control and color stripe</span></span></th>
        <td><span data-ttu-id="0d35c-363">C3FD11C6-F8B7-4D20-B008-1DB17D61F2DA</span><span class="sxs-lookup"><span data-stu-id="0d35c-363">C3FD11C6-F8B7-4D20-B008-1DB17D61F2DA</span></span></td>
        <td><span data-ttu-id="0d35c-364">Inhalt wird mit einer Auflösung von maximal 520.000Pixeln an eine analoge TV-Ausgabe übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-364">Passing content with resolution less than or equal to 520,000 px to analog TV output</span></span></td>
        <td colspan="2"><span data-ttu-id="0d35c-365">Die automatische Verstärkungsregelung wird nur für Komponentenvideos und den PAL-Modus festgelegt, wenn die Auflösung weniger als 520.000Pixel beträgt. Automatische Verstärkungsregelung und Farbstreifeninformationen für NTSC werden festgelegt, wenn die Auflösung weniger als 520.000Pixel beträgt (siehe Tabelle3.5.7.3.</span><span class="sxs-lookup"><span data-stu-id="0d35c-365">Sets AGC only for component video and PAL mode when resolution is less than 520,000 px and sets AGC and color stripe information for NTSC when resolution is less than 520,000 px, according to table 3.5.7.3.</span></span> <span data-ttu-id="0d35c-366">in den Kompatibilitätsregeln).</span><span class="sxs-lookup"><span data-stu-id="0d35c-366">in Compliance Rules</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-367">Nur digitale Ausgabe</span><span class="sxs-lookup"><span data-stu-id="0d35c-367">Digital-only output</span></span></th>
        <td><span data-ttu-id="0d35c-368">760AE755-682A-41E0-B1B3-DCDF836A7306</span><span class="sxs-lookup"><span data-stu-id="0d35c-368">760AE755-682A-41E0-B1B3-DCDF836A7306</span></span></td>
        <td><span data-ttu-id="0d35c-369">Die verbundene Ausgabe ist analog.</span><span class="sxs-lookup"><span data-stu-id="0d35c-369">Connected output is analog</span></span></td>
        <td colspan="2"><span data-ttu-id="0d35c-370">Inhalt wird nicht übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-370">Does not pass content</span></span></td>
    </tr>
</table>
<br/>

> [!NOTE]
> <span data-ttu-id="0d35c-371">Wenn für die Wiedergabe ein Adapterdongle wie Mini-DisplayPort auf VGA verwendet wird, wird die Ausgabe von Windows10 als digitale Videoausgabe betrachtet, sodass keine Richtlinien für analoge Videos durchgesetzt werden können.</span><span class="sxs-lookup"><span data-stu-id="0d35c-371">When using an adapter dongle such as "Mini DisplayPort to VGA" for playback, Windows 10 sees the output as digital video output, and can't enforce analog video policies.</span></span>

<span data-ttu-id="0d35c-372">Die folgende Tabelle beschreibt die Implementierung von PlayReady DRM für Windows10 für die Wiedergabe in anderen Fällen:</span><span class="sxs-lookup"><span data-stu-id="0d35c-372">The following table describes the PlayReady DRM for Windows 10 implementation that enables playing in other circumstances.</span></span>

<table>
    <tr>
        <th><span data-ttu-id="0d35c-373">Szenario</span><span class="sxs-lookup"><span data-stu-id="0d35c-373">Scenario</span></span></th>
        <th><span data-ttu-id="0d35c-374">GUID</span><span class="sxs-lookup"><span data-stu-id="0d35c-374">GUID</span></span></th>
        <th><span data-ttu-id="0d35c-375">Situation</span><span class="sxs-lookup"><span data-stu-id="0d35c-375">If...</span></span></th>
        <th colspan="2"><span data-ttu-id="0d35c-376">Folge</span><span class="sxs-lookup"><span data-stu-id="0d35c-376">Then...</span></span></th>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-377">Unbekannte Ausgabe</span><span class="sxs-lookup"><span data-stu-id="0d35c-377">Unknown output</span></span></th>
        <td><span data-ttu-id="0d35c-378">786627D8-C2A6-44BE-8F88-08AE255B01A7</span><span class="sxs-lookup"><span data-stu-id="0d35c-378">786627D8-C2A6-44BE-8F88-08AE255B01A7</span></span></td>
        <td><span data-ttu-id="0d35c-379">Die Ausgabe kann nicht vernünftig ermittelt werden, oder für den Grafiktreiber ist kein OPM möglich.</span><span class="sxs-lookup"><span data-stu-id="0d35c-379">If output can't reasonably be determined, or OPM can't be established with graphics driver</span></span></td>
        <td><span data-ttu-id="0d35c-380">**SWDRM:** Inhalt wird übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-380">**SWDRM:** Passes content</span></span></td>
        <td><span data-ttu-id="0d35c-381">**HWDRM:** Inhalt wird NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-381">**HWDRM:** Does NOT pass content</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="0d35c-382">Unbekannte Ausgabe mit Einschränkung</span><span class="sxs-lookup"><span data-stu-id="0d35c-382">Unknown output with constriction</span></span></th>
        <td><span data-ttu-id="0d35c-383">B621D91F-EDCC-4035-8D4B-DC71760D43E9</span><span class="sxs-lookup"><span data-stu-id="0d35c-383">B621D91F-EDCC-4035-8D4B-DC71760D43E9</span></span></td>
        <td><span data-ttu-id="0d35c-384">Die Ausgabe kann nicht vernünftig ermittelt werden, oder für den Grafiktreiber ist kein OPM möglich.</span><span class="sxs-lookup"><span data-stu-id="0d35c-384">If output can't reasonably be determined, or OPM can't be established with graphics driver</span></span></td>
        <td><span data-ttu-id="0d35c-385">**SWDRM:** Der PC schränkt die effektive Auflösung auf 520.000epx pro Frame ein und übergibt den Inhalt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-385">**SWDRM:** PC will constrain effective resolution to 520,000 epx per frame and pass content</span></span></td>
        <td><span data-ttu-id="0d35c-386">**HWDRM:** Inhalt wird NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-386">**HWDRM:** Does NOT pass content</span></span></td>
    </tr>
</table>
<br/>

## <a name="prerequisites"></a><span data-ttu-id="0d35c-387">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="0d35c-387">Prerequisites</span></span>

<span data-ttu-id="0d35c-388">Bevor Sie mit der Erstellung Ihrer PlayReady-geschützten UWP-App beginnen, müssen Sie die folgende Software auf Ihrem System installieren:</span><span class="sxs-lookup"><span data-stu-id="0d35c-388">Before you begin creating your PlayReady-protected UWP app, the following software needs to be installed on your system:</span></span>

-   <span data-ttu-id="0d35c-389">Windows 10.</span><span class="sxs-lookup"><span data-stu-id="0d35c-389">Windows 10.</span></span>
-   <span data-ttu-id="0d35c-390">Wenn Sie Beispiele für PlayReady DRM für UWP-Apps kompilieren, müssen Sie Microsoft Visual Studio 2015 oder höher zum Kompilieren der Beispiele verwenden.</span><span class="sxs-lookup"><span data-stu-id="0d35c-390">If you are compiling any of the samples for PlayReady DRM for UWP apps, you must use Microsoft Visual Studio 2015 or later to compile the samples.</span></span> <span data-ttu-id="0d35c-391">Microsoft Visual Studio 2013 kann weiterhin zum Kompilieren der Beispiele aus PlayReady DRM für Windows 8.1-Store-Apps verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0d35c-391">You can still use Microsoft Visual Studio 2013 to compile any of the samples from PlayReady DRM for Windows 8.1 Store Apps.</span></span>

<!--This is no longer available-->
<!--If you are planning to play back MPEG-2/H.262 content on your app, you must also download and install [Windows 8.1 Media Center Pack](http://go.microsoft.com/fwlink/p/?LinkId=626876).-->

## <a name="playready-windows-store-app-migration-guide"></a><span data-ttu-id="0d35c-392">Migrationshandbuch für WindowsStore-Apps mit PlayReady</span><span class="sxs-lookup"><span data-stu-id="0d35c-392">PlayReady Windows Store app migration guide</span></span>

<span data-ttu-id="0d35c-393">Dieser Abschnitt enthält Informationen zum Migrieren Ihrer vorhandenen Windows8.x-Store-Apps mit PlayReady zu Windows10.</span><span class="sxs-lookup"><span data-stu-id="0d35c-393">This section includes information on how to migrate your existing PlayReady Windows 8.x Store apps to Windows 10.</span></span>

<span data-ttu-id="0d35c-394">Der Namespace für UWP-Apps mit PlayReady unter Windows 10 wurde von **Microsoft.Media.PlayReadyClient** in [**Windows.Media.Protection.PlayReady**](https://msdn.microsoft.com/library/windows/apps/dn986454) geändert.</span><span class="sxs-lookup"><span data-stu-id="0d35c-394">The namespace for PlayReady UWP apps on Windows 10 was changed from **Microsoft.Media.PlayReadyClient** to [**Windows.Media.Protection.PlayReady**](https://msdn.microsoft.com/library/windows/apps/dn986454).</span></span> <span data-ttu-id="0d35c-395">Sie müssen also in Ihrem Code den alten Namespace suchen und durch den neuen Namespace ersetzen.</span><span class="sxs-lookup"><span data-stu-id="0d35c-395">This means that you will need to search and replace the old namespace with the new one in your code.</span></span> <span data-ttu-id="0d35c-396">Sie verweisen weiterhin auf eine WINMD-Datei.</span><span class="sxs-lookup"><span data-stu-id="0d35c-396">You will still be referencing a winmd file.</span></span> <span data-ttu-id="0d35c-397">Sie ist Teil von „windows.media.winmd“ im Betriebssystem Windows 10.</span><span class="sxs-lookup"><span data-stu-id="0d35c-397">It is part of windows.media.winmd on the Windows 10 operating system.</span></span> <span data-ttu-id="0d35c-398">Sie ist in „windows.winmd“ als Teil des TH WindowsSDK enthalten.</span><span class="sxs-lookup"><span data-stu-id="0d35c-398">It is in windows.winmd as part of the TH’s Windows SDK.</span></span> <span data-ttu-id="0d35c-399">Bei UWP wird darauf in „windows.foundation.univeralappcontract.winmd“ verwiesen.</span><span class="sxs-lookup"><span data-stu-id="0d35c-399">For UWP, it’s referenced in windows.foundation.univeralappcontract.winmd.</span></span>

<span data-ttu-id="0d35c-400">Zum Wiedergeben von PlayReady-geschützten High-Definition (HD)-Inhalten (1080p) und Ultra-High-Definition (UHD)-Inhalten müssen Sie das Hardware-DRM mit PlayReady implementieren.</span><span class="sxs-lookup"><span data-stu-id="0d35c-400">To play back PlayReady-protected high definition (HD) content (1080p) and ultra-high definition (UHD) content, you will need to implement PlayReady hardware DRM.</span></span> <span data-ttu-id="0d35c-401">Informationen zum Implementieren des Hardware-DRM mit PlayReady finden Sie unter [Hardware-DRM](hardware-drm.md).</span><span class="sxs-lookup"><span data-stu-id="0d35c-401">For information on how to implement PlayReady hardware DRM, see [Hardware DRM](hardware-drm.md).</span></span>

<span data-ttu-id="0d35c-402">Manche Inhalte werden nicht vom Hardware-DRM unterstützt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-402">Some content is not supported in hardware DRM.</span></span> <span data-ttu-id="0d35c-403">Informationen zum Deaktivieren des Hardware-DRM und Aktivieren des Software-DRM finden Sie unter [Außerkraftsetzen des Hardware-DRM](hardware-drm.md#override-hardware-drm).</span><span class="sxs-lookup"><span data-stu-id="0d35c-403">For information on disabling hardware DRM and enabling software DRM, see [Override Hardware DRM](hardware-drm.md#override-hardware-drm).</span></span>

<span data-ttu-id="0d35c-404">Stellen Sie im Medienschutz-Manager sicher, dass für Ihren Code die folgenden Einstellungen festgelegt sind (sofern noch nicht geschehen):</span><span class="sxs-lookup"><span data-stu-id="0d35c-404">Regarding the media protection manager, make sure your code has the following settings if it doesn’t already:</span></span>

```cs
var mediaProtectionManager = new Windows.Media.Protection.MediaProtectionManager();

mediaProtectionManager.properties["Windows.Media.Protection.MediaProtectionSystemId"] = 
             '{F4637010-03C3-42CD-B932-B48ADF3A6A54}'
var cpsystems = new Windows.Foundation.Collections.PropertySet();
cpsystems["{F4637010-03C3-42CD-B932-B48ADF3A6A54}"] = 
                "Windows.Media.Protection.PlayReady.PlayReadyWinRTTrustedInput";
mediaProtectionManager.properties["Windows.Media.Protection.MediaProtectionSystemIdMapping"] = cpsystems;

mediaProtectionManager.properties["Windows.Media.Protection.MediaProtectionContainerGuid"] = 
                "{9A04F079-9840-4286-AB92-E65BE0885F95}";
```

## <a name="proactively-acquire-a-non-persistent-license-before-playback"></a><span data-ttu-id="0d35c-405">Proaktives Abrufen einer nicht persistenten Lizenz vor der Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="0d35c-405">Proactively acquire a non-persistent license before playback</span></span>

<span data-ttu-id="0d35c-406">In diesem Abschnitt wird beschrieben, wie Sie vor dem Start der Wiedergabe proaktiv nicht persistente Lizenzen abrufen.</span><span class="sxs-lookup"><span data-stu-id="0d35c-406">This section describes how to acquire non-persistent licenses proactively before playback begins.</span></span>

<span data-ttu-id="0d35c-407">In früheren Versionen von PlayReady DRM konnten nicht persistente Lizenzen nur reaktiv während der Wiedergabe abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="0d35c-407">In previous versions of PlayReady DRM, non-persistent licenses could only be acquired reactively during playback.</span></span> <span data-ttu-id="0d35c-408">In dieser Version können Sie nicht persistente Lizenzen proaktiv abrufen, bevor die Wiedergabe beginnt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-408">In this version, you can acquire non-persistent licenses proactively before playback begins.</span></span>

1.  <span data-ttu-id="0d35c-409">Erstellen Sie proaktiv eine Wiedergabesitzung, in der die nicht persistente Lizenz gespeichert werden kann.</span><span class="sxs-lookup"><span data-stu-id="0d35c-409">Proactively create a playback session where the non-persistent license can be stored.</span></span> <span data-ttu-id="0d35c-410">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="0d35c-410">For example:</span></span>

    ```cs
    var cpsystems = new Windows.Foundation.Collections.PropertySet();       
    cpsystems["{F4637010-03C3-42CD-B932-B48ADF3A6A54}"] = "Windows.Media.Protection.PlayReady.PlayReadyWinRTTrustedInput"; // PlayReady

    var pmpSystemInfo = new Windows.Foundation.Collections.PropertySet();
    pmpSystemInfo["Windows.Media.Protection.MediaProtectionSystemId"] = "{F4637010-03C3-42CD-B932-B48ADF3A6A54}";
    pmpSystemInfo["Windows.Media.Protection.MediaProtectionSystemIdMapping"] = cpsystems;
    var pmpServer = new Windows.Media.Protection.MediaProtectionPMPServer( pmpSystemInfo );
    ```

2.  <span data-ttu-id="0d35c-411">Binden Sie die Wiedergabesitzung an die Lizenzabrufklasse.</span><span class="sxs-lookup"><span data-stu-id="0d35c-411">Tie that playback session to the license acquisition class.</span></span> <span data-ttu-id="0d35c-412">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="0d35c-412">For example:</span></span>

    ```cs
    var licenseSessionProperties = new Windows.Foundation.Collections.PropertySet();
    licenseSessionProperties["Windows.Media.Protection.MediaProtectionPMPServer"] = pmpServer;
    var licenseSession = new Windows.Media.Protection.PlayReady.PlayReadyLicenseSession( licenseSessionProperties );
    ```

3.  <span data-ttu-id="0d35c-413">Erstellen Sie eine Lizenzserviceanfrage.</span><span class="sxs-lookup"><span data-stu-id="0d35c-413">Create a license service request.</span></span> <span data-ttu-id="0d35c-414">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="0d35c-414">For example:</span></span>

    ```cs
    var laSR = licenseSession.CreateLAServiceRequest();
    ```

4.  <span data-ttu-id="0d35c-415">Führen Sie den Lizenzerwerb mit der Serviceanfrage aus, die Sie in Schritt 3 erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="0d35c-415">Perform the license acquisition using the service request created from step 3.</span></span> <span data-ttu-id="0d35c-416">Die Lizenz wird in der Wiedergabesitzung gespeichert.</span><span class="sxs-lookup"><span data-stu-id="0d35c-416">The license will be stored in the playback session.</span></span>
5.  <span data-ttu-id="0d35c-417">Binden Sie die Wiedergabesitzung an die Medienquelle für die Wiedergabe.</span><span class="sxs-lookup"><span data-stu-id="0d35c-417">Tie the playback session to the media source for playback.</span></span> <span data-ttu-id="0d35c-418">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="0d35c-418">For example:</span></span>

    ```cs
    licenseSession.configureMediaProtectionManager( mediaProtectionManager );
    videoPlayer.msSetMediaProtectionManager( mediaProtectionManager );
    ```
    
## <a name="query-for-protection-capabilities"></a><span data-ttu-id="0d35c-419">Abfrage der Schutzmöglichkeiten</span><span class="sxs-lookup"><span data-stu-id="0d35c-419">Query for protection capabilities</span></span>
<span data-ttu-id="0d35c-420">Ab Windows10, Version 1703, können Sie Hardware-DRM-Funktionen abfragen, z.B. für Decodierung, Auflösung und Ausgabeschutz (HDCP).</span><span class="sxs-lookup"><span data-stu-id="0d35c-420">Starting with Windows 10, version 1703, you can query HW DRM capabilities, such as decode codecs, resolution, and output protections (HDCP).</span></span> <span data-ttu-id="0d35c-421">Abfragen erfolgen mit der Methode [**IsTypeSupported**](https://docs.microsoft.com/uwp/api/windows.media.protection.protectioncapabilities#Windows_Media_Protection_ProtectionCapabilities_IsTypeSupported_System_String_System_String_). Diese erwartet eine Zeichenfolge, welche die Funktionen angibt, nach deren Unterstützung gefragt wird, und eine Zeichenfolge, die das Schlüsselsystem angibt, für das die Abfrage gilt.</span><span class="sxs-lookup"><span data-stu-id="0d35c-421">Queries are performed with the [**IsTypeSupported**](https://docs.microsoft.com/uwp/api/windows.media.protection.protectioncapabilities#Windows_Media_Protection_ProtectionCapabilities_IsTypeSupported_System_String_System_String_) method which takes a string representing the capabilities for which support is queried and a string specifying the key system to which the query applies.</span></span> <span data-ttu-id="0d35c-422">Eine Liste der unterstützten Zeichenfolgenwerte finden Sie auf der API-Referenzseite für [**IsTypeSupported**](https://docs.microsoft.com/uwp/api/windows.media.protection.protectioncapabilities#Windows_Media_Protection_ProtectionCapabilities_IsTypeSupported_System_String_System_String_).</span><span class="sxs-lookup"><span data-stu-id="0d35c-422">For a list of supported string values, see the API reference page for [**IsTypeSupported**](https://docs.microsoft.com/uwp/api/windows.media.protection.protectioncapabilities#Windows_Media_Protection_ProtectionCapabilities_IsTypeSupported_System_String_System_String_).</span></span> <span data-ttu-id="0d35c-423">Das folgende Codebeispiel veranschaulicht die Verwendung dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="0d35c-423">The following code example illustrates the usage of this method.</span></span>  

    ```cs
    using namespace Windows::Media::Protection;

    ProtectionCapabilities^ sr = ref new ProtectionCapabilities();

    ProtectionCapabilityResult result = sr->IsTypeSupported(
    L"video/mp4; codecs=\"avc1.640028\"; features=\"decode-bpp=10,decode-fps=29.97,decode-res-x=1920,decode-res-y=1080\"",
    L"com.microsoft.playready");

    switch (result)
    {
        case ProtectionCapabilityResult::Probably:
        // Queue up UHD HW DRM video
        break;

        case ProtectionCapabilityResult::Maybe:
        // Check again after UI or poll for more info.
        break;

        case ProtectionCapabilityResult::NotSupported:
        // Do not queue up UHD HW DRM video.
        break;
    }
    ```
## <a name="add-secure-stop"></a><span data-ttu-id="0d35c-424">Hinzufügen des sicheren Beendens</span><span class="sxs-lookup"><span data-stu-id="0d35c-424">Add secure stop</span></span>

<span data-ttu-id="0d35c-425">In diesem Abschnitt wird beschrieben, wie Sie Ihrer UWP-App die Funktion für sicheres Beenden hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="0d35c-425">This section describes how to add secure stop to your UWP app.</span></span>

<span data-ttu-id="0d35c-426">Dank des sicheren Beendens kann ein PlayReady-Gerät einem Medienstreamingdienst zuverlässig bestätigen, dass die Medienwiedergabe für einen bestimmten Inhalt beendet wurde.</span><span class="sxs-lookup"><span data-stu-id="0d35c-426">Secure stop provides the means for a PlayReady device to confidently assert to a media streaming service that media playback has stopped for any given piece of content.</span></span> <span data-ttu-id="0d35c-427">Mit dieser Funktion wird sichergestellt, dass Ihre Medienstreamingdienste präzise Erzwingung und Berichte zu Nutzungseinschränkungen auf verschiedenen Geräten für ein bestimmtes Konto bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="0d35c-427">This capability ensures your media streaming services provide accurate enforcement and reporting of usage limitations on different devices for a given account.</span></span>

<span data-ttu-id="0d35c-428">Es gibt zwei primäre Szenarien für das Senden einer Abfrage für sicheres Beenden:</span><span class="sxs-lookup"><span data-stu-id="0d35c-428">There are two primary scenarios for sending a secure stop challenge:</span></span>

-   <span data-ttu-id="0d35c-429">Wenn die Mediendarstellung beendet wird, weil das Ende des Inhalts erreicht wurde, oder wenn die Mediendarstellung vor ihrem Ende vom Benutzer beendet wurde.</span><span class="sxs-lookup"><span data-stu-id="0d35c-429">When the media presentation stops because end of content was reached or when the user stopped the media presentation somewhere in the middle.</span></span>
-   <span data-ttu-id="0d35c-430">Wenn die vorherige Sitzung unerwartet beendet wurde (z.B. aufgrund eines System- oder App-Absturzes).</span><span class="sxs-lookup"><span data-stu-id="0d35c-430">When the previous session ends unexpectedly (for example, due to a system or app crash).</span></span> <span data-ttu-id="0d35c-431">Die App muss beim Starten oder Herunterfahren alle ausstehenden Sitzungen für sicheres Beenden abfragen und von anderen Medienwiedergaben getrennte Abfragen senden.</span><span class="sxs-lookup"><span data-stu-id="0d35c-431">The app will need to query, either at startup or shutdown, for any outstanding secure stop sessions and send challenge(s) separate from any other media playback.</span></span>

<span data-ttu-id="0d35c-432">Eine Beispielimplementierung für das sichere Beenden finden Sie in der Datei „securestop.cs” im PlayReady-Beispiel unter [http://go.microsoft.com/fwlink/p/?linkid=331670&clcid=0x409](http://go.microsoft.com/fwlink/p/?linkid=331670).</span><span class="sxs-lookup"><span data-stu-id="0d35c-432">For a sample implementation of secure stop, see the securestop.cs file in the PlayReady sample located at [http://go.microsoft.com/fwlink/p/?linkid=331670&clcid=0x409](http://go.microsoft.com/fwlink/p/?linkid=331670).</span></span>

## <a name="use-playready-drm-on-xbox-one"></a><span data-ttu-id="0d35c-433">Verwenden von PlayReady DRM auf Xbox One</span><span class="sxs-lookup"><span data-stu-id="0d35c-433">Use PlayReady DRM on Xbox One</span></span>

<span data-ttu-id="0d35c-434">Um PlayReady-DRM in einer UWP-App auf Xbox One zu verwenden, müssen Sie zunächst das Dev Center-Konto, das Sie zum Veröffentlichen der App verwenden, für die Autorisierung zur PlayReady-Verwendung registrieren.</span><span class="sxs-lookup"><span data-stu-id="0d35c-434">To use PlayReady DRM in a UWP app on Xbox One, you will first need to register your Dev Center account that you're using to publish the app for authorization to use PlayReady.</span></span> <span data-ttu-id="0d35c-435">Hierzu stehen Ihnen zwei Möglichkeiten zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="0d35c-435">You can do this in one of two ways:</span></span>

* <span data-ttu-id="0d35c-436">Ihr Microsoft-Kontakt kann die Berechtigung anfordern.</span><span class="sxs-lookup"><span data-stu-id="0d35c-436">Have your contact at Microsoft request permission.</span></span>
* <span data-ttu-id="0d35c-437">Fordern Sie die Autorisierung an, indem Sie Ihr Dev Center-Konto und den Unternehmensnamen an [pronxbox@microsoft.com](mailto:pronxbox@microsoft.com) senden.</span><span class="sxs-lookup"><span data-stu-id="0d35c-437">Apply for authorization by sending your Dev Center account and company name to [pronxbox@microsoft.com](mailto:pronxbox@microsoft.com).</span></span>

<span data-ttu-id="0d35c-438">Wenn Sie die Autorisierung erhalten haben, müssen Sie dem App-Manifest eine zusätzliche `<DeviceCapability>` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="0d35c-438">Once you receive authorization, you'll need to add an additional `<DeviceCapability>` to the app manifest.</span></span> <span data-ttu-id="0d35c-439">Sie müssen diese manuell hinzufügen, da derzeit im App Manifest Designer keine Einstellung verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="0d35c-439">You'll have to add this manually because there is currently no setting available in the App Manifest Designer.</span></span> <span data-ttu-id="0d35c-440">Führen Sie folgende Schritte durch, um dies zu konfigurieren:</span><span class="sxs-lookup"><span data-stu-id="0d35c-440">Follow these steps to configure it:</span></span>

1. <span data-ttu-id="0d35c-441">Öffnen Sie das Projekt in Visual Studio, öffnen Sie den **Solution Explorer**, und klicken Sie mit der rechten Maustaste auf **Package.appxmanifest**.</span><span class="sxs-lookup"><span data-stu-id="0d35c-441">With the project open in Visual Studio, open the **Solution Explorer** and right-click **Package.appxmanifest**.</span></span>
2. <span data-ttu-id="0d35c-442">Wählen Sie **Öffnen mit... ** und anschließend **XML (Text) Editor**, und klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="0d35c-442">Select **Open With...**, choose **XML (Text) Editor**, and click **OK**.</span></span>
3. <span data-ttu-id="0d35c-443">Fügen Sie zwischen den `<Capabilities>`-Tags die folgende `<DeviceCapability>` ein:</span><span class="sxs-lookup"><span data-stu-id="0d35c-443">Between the `<Capabilities>` tags, add the following `<DeviceCapability>`:</span></span>

    ```xml
    <DeviceCapability Name="6a7e5907-885c-4bcb-b40a-073c067bd3d5" />
    ```

4. <span data-ttu-id="0d35c-444">Speichern Sie die Datei.</span><span class="sxs-lookup"><span data-stu-id="0d35c-444">Save the file.</span></span>

<span data-ttu-id="0d35c-445">Beachten Sie bei der Verwendung von PlayReady auf Xbox One jedoch auch Folgendes: Auf Entwicklungskits besteht eine SL150-Beschränkung (d.h. SL2000- oder SL3000-Inhalte können nicht wiedergegeben werden).</span><span class="sxs-lookup"><span data-stu-id="0d35c-445">Finally, there is one last consideration when using PlayReady on Xbox One: on development kits, there is an SL150 limit (that is, they can't play SL2000 or SL3000 content).</span></span> <span data-ttu-id="0d35c-446">Einzelhandelsgeräte können Inhalte mit höheren Sicherheitsebenen wiedergeben. Sie müssen jedoch SL150-Inhalte verwenden, um Ihre App in einem Entwicklungskit zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="0d35c-446">Retail devices are able to play content with higher security levels, but to test your app on a dev kit, you'll need to use SL150 content.</span></span> <span data-ttu-id="0d35c-447">Zum Testen dieser Inhalte stehen Ihnen folgende Möglichkeiten zur Verfügung:</span><span class="sxs-lookup"><span data-stu-id="0d35c-447">You can test this content in one of the following ways:</span></span>

* <span data-ttu-id="0d35c-448">Verwenden Sie speziell zusammengestellte Testinhalte, die SL150-Lizenzen erfordern.</span><span class="sxs-lookup"><span data-stu-id="0d35c-448">Use curated test content that requires SL150 licenses.</span></span>
* <span data-ttu-id="0d35c-449">Implementieren Sie eine Logik, sodass nur bestimmte authentifizierte Testkonten SL150-Lizenzen für bestimmte Inhalte erhalten können.</span><span class="sxs-lookup"><span data-stu-id="0d35c-449">Implement logic so that only certain authenticated test accounts are able to acquire SL150 licenses for certain content.</span></span>

<span data-ttu-id="0d35c-450">Gehen Sie so vor, wie es für Ihr Unternehmen und Ihr Produkt am praktischsten ist.</span><span class="sxs-lookup"><span data-stu-id="0d35c-450">Use the approach that makes the most sense for your company and your product.</span></span>


## <a name="see-also"></a><span data-ttu-id="0d35c-451">Weitere Informationen finden Sie unter</span><span class="sxs-lookup"><span data-stu-id="0d35c-451">See also</span></span>
- [<span data-ttu-id="0d35c-452">Medienwiedergabe</span><span class="sxs-lookup"><span data-stu-id="0d35c-452">Media playback</span></span>](media-playback.md)




