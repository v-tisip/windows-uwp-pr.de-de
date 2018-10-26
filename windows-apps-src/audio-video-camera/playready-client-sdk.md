---
author: drewbatgit
ms.assetid: DD8FFA8C-DFF0-41E3-8F7A-345C5A248FC2
description: In diesem Abschnitt wird beschrieben, wie Sie Ihrer UWP-App (Universelle Windows-Plattform) PlayReady-geschützte Medieninhalte hinzufügen.
title: PlayReady DRM
ms.author: drewbat
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 773216dc392f7bb234e232f3dd3e7c2190a22de1
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "5543767"
---
# <a name="playready-drm"></a><span data-ttu-id="e41b6-104">PlayReady DRM</span><span class="sxs-lookup"><span data-stu-id="e41b6-104">PlayReady DRM</span></span>



<span data-ttu-id="e41b6-105">In diesem Abschnitt wird beschrieben, wie Sie Ihrer UWP-App (Universelle Windows-Plattform) PlayReady-geschützte Medieninhalte hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e41b6-105">This topic describes how to add PlayReady protected media content to your Universal Windows Platform (UWP) app.</span></span>

<span data-ttu-id="e41b6-106">PlayReady DRM ermöglicht Entwicklern das Erstellen von UWP-Apps, die PlayReady-geschützte Inhalte für den Benutzer bereitstellen und gleichzeitig vom Inhaltsanbieter definierte Regeln erzwingen können.</span><span class="sxs-lookup"><span data-stu-id="e41b6-106">PlayReady DRM enables developers to create UWP apps capable of providing PlayReady content to the user while enforcing the access rules defined by the content provider.</span></span> <span data-ttu-id="e41b6-107">Dieser Abschnitt beschreibt die Änderungen an Microsoft PlayReady DRM für Windows 10 sowie zum Ändern Ihrer PlayReady-UWP-app, um die Änderungen, die aus der vorherigen Version Windows8.1 in die Windows 10-Version zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="e41b6-107">This section describes changes made to Microsoft PlayReady DRM for Windows10 and how to modify your PlayReady UWP app to support the changes made from the previous Windows8.1 version to the Windows10 version.</span></span>
 
| <span data-ttu-id="e41b6-108">Thema</span><span class="sxs-lookup"><span data-stu-id="e41b6-108">Topic</span></span>                                                                     | <span data-ttu-id="e41b6-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e41b6-109">Description</span></span>                                                                                                                                                                                                                                                                             |
|---------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [<span data-ttu-id="e41b6-110">Hardware-DRM</span><span class="sxs-lookup"><span data-stu-id="e41b6-110">Hardware DRM</span></span>](hardware-drm.md)                                           | <span data-ttu-id="e41b6-111">Dieses Thema enthält eine Übersicht über das Hinzufügen der hardwarebasierten Verwaltung digitaler Rechte (Digital Rights Management, DRM) mit PlayReady zu Ihrer UWP-App.</span><span class="sxs-lookup"><span data-stu-id="e41b6-111">This topic provides an overview of how to add PlayReady hardware-based digital rights management (DRM) to your UWP app.</span></span>                                                                                                                                                                 |
| [<span data-ttu-id="e41b6-112">Adaptives Streaming mit PlayReady</span><span class="sxs-lookup"><span data-stu-id="e41b6-112">Adaptive streaming with PlayReady</span></span>](adaptive-streaming-with-playready.md) | <span data-ttu-id="e41b6-113">In diesem Artikel wird beschrieben, wie Sie einer UWP-App (Universelle Windows-Plattform) adaptives Streaming von Multimediainhalten mit Microsoft PlayReady-Inhaltsschutz hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e41b6-113">This article describes how to add adaptive streaming of multimedia content with Microsoft PlayReady content protection to a Universal Windows Platform (UWP) app.</span></span> <span data-ttu-id="e41b6-114">Dieses Feature unterstützt derzeit die Wiedergabe von HTTP Live Streaming(HLS)- und Dynamic Streaming over HTTP(DASH)-Inhalten.</span><span class="sxs-lookup"><span data-stu-id="e41b6-114">This feature currently supports playback of Http Live Streaming (HLS) and Dynamic Streaming over HTTP (DASH) content.</span></span> |

## <a name="whats-new-in-playready-drm"></a><span data-ttu-id="e41b6-115">Neuigkeiten bei PlayReady DRM</span><span class="sxs-lookup"><span data-stu-id="e41b6-115">What's new in PlayReady DRM</span></span>

<span data-ttu-id="e41b6-116">Die folgende Liste beschreibt die neuen Features und Änderungen von PlayReady DRM für Windows 10.</span><span class="sxs-lookup"><span data-stu-id="e41b6-116">The following list describes the new features and changes made to PlayReady DRM for Windows10.</span></span>

-   <span data-ttu-id="e41b6-117">Hardwarebasierte Verwaltung digitaler Rechte (Hardware Digital Rights Management, HWDRM) wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-117">Added hardware digital rights management (HWDRM).</span></span>

    <span data-ttu-id="e41b6-118">Die Unterstützung für hardwarebasierten Inhaltsschutz ermöglicht die sichere Wiedergabe von High-Definition(HD)- und Ultra-High-Definition(UHD)-Inhalten auf mehreren Geräteplattformen.</span><span class="sxs-lookup"><span data-stu-id="e41b6-118">Hardware-based content protection support enables secure playback of high definition (HD) and ultra-high definition (UHD) content on multiple device platforms.</span></span> <span data-ttu-id="e41b6-119">Schlüsselmaterial (einschließlich privater Schlüssel, Inhaltsschlüssel und anderer Schlüsselmaterialien zum Ableiten oder Entsperren dieser Schlüssel) sowie entschlüsselte komprimierte und nicht komprimierte Videobeispiele werden durch Hardwaresicherheit geschützt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-119">Key material (including private keys, content keys, and any other key material used to derive or unlock said keys), and decrypted compressed and uncompressed video samples are protected by leveraging hardware security.</span></span> <span data-ttu-id="e41b6-120">Bei Verwendung des Hardware-DRM sind unbekannte Aktivierungen (Wiedergabe auf unbekannter Ausgabe/Wiedergabe auf unbekannter Ausgabe mit „downres”) irrelevant, da die HWDRM-Pipeline die verwendete Ausgabe immer kennt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-120">When Hardware DRM is being used, neither unknown enabler (play to unknown / play to unknown with downres) has meaning as the HWDRM pipeline always knows the output being used.</span></span> <span data-ttu-id="e41b6-121">Weitere Informationen finden Sie unter [Hardware-DRM](hardware-drm.md).</span><span class="sxs-lookup"><span data-stu-id="e41b6-121">For more information, see [Hardware DRM](hardware-drm.md).</span></span>

-   <span data-ttu-id="e41b6-122">PlayReady ist keine AppX-Framework-Komponente mehr, sondern stattdessen eine integrierte Betriebssystemkomponente.</span><span class="sxs-lookup"><span data-stu-id="e41b6-122">PlayReady is no longer an appX framework component, but instead is an in-box operating system component.</span></span> <span data-ttu-id="e41b6-123">Der Namespace wurde von **Microsoft.Media.PlayReadyClient** in [**Windows.Media.Protection.PlayReady**](https://msdn.microsoft.com/library/windows/apps/dn986454) geändert.</span><span class="sxs-lookup"><span data-stu-id="e41b6-123">The namespace was changed from **Microsoft.Media.PlayReadyClient** to [**Windows.Media.Protection.PlayReady**](https://msdn.microsoft.com/library/windows/apps/dn986454).</span></span>
-   <span data-ttu-id="e41b6-124">Die folgenden Header zur Definition der PlayReady-Fehlercodes sind jetzt Teil des Windows Software Development Kit (SDK): „Windows.Media.Protection.PlayReadyErrors.h” und „Windows.Media.Protection.PlayReadyResults.h”.</span><span class="sxs-lookup"><span data-stu-id="e41b6-124">The following headers defining the PlayReady error codes are now part of the Windows Software Development Kit (SDK): Windows.Media.Protection.PlayReadyErrors.h and Windows.Media.Protection.PlayReadyResults.h.</span></span>
-   <span data-ttu-id="e41b6-125">Unterstützt das proaktive Abrufen nicht persistenter Lizenzen.</span><span class="sxs-lookup"><span data-stu-id="e41b6-125">Provides proactive acquisition of non-persistent licenses.</span></span>

    <span data-ttu-id="e41b6-126">Das proaktive Abrufen nicht persistenter Lizenzen wurde von Vorgängerversionen von PlayReady DRM nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-126">Previous versions of PlayReady DRM did not support proactive acquisition of non-persistent licenses.</span></span> <span data-ttu-id="e41b6-127">Diese Funktion wurde in dieser Version hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-127">This capability has been added to this version.</span></span> <span data-ttu-id="e41b6-128">Mit ihrer Hilfe kann die Zeit bis zum ersten Frame verkürzt werden.</span><span class="sxs-lookup"><span data-stu-id="e41b6-128">This can decrease the time to first frame.</span></span> <span data-ttu-id="e41b6-129">Weitere Informationen finden Sie unter [Proaktives Abrufen einer nicht persistenten Lizenz vor der Wiedergabe](#proactively-acquire-a-non-persistent-license-before-playback).</span><span class="sxs-lookup"><span data-stu-id="e41b6-129">For more information, see [Proactively Acquire a Non-Persistent License Before Playback](#proactively-acquire-a-non-persistent-license-before-playback).</span></span>

-   <span data-ttu-id="e41b6-130">Unterstützt das Abrufen mehrerer Lizenzen in einer Nachricht.</span><span class="sxs-lookup"><span data-stu-id="e41b6-130">Provides acquisition of multiple licenses in one message.</span></span>

    <span data-ttu-id="e41b6-131">Ermöglicht der Client-App das Abrufen mehrerer nicht persistenter Lizenzen in einer Lizenzabrufnachricht.</span><span class="sxs-lookup"><span data-stu-id="e41b6-131">Allows the client app to acquire multiple non-persistent licenses in one license acquisition message.</span></span> <span data-ttu-id="e41b6-132">Da Lizenzen für mehrere Inhalte abgerufen werden, während der Benutzer noch die Inhaltsbibliothek durchsucht, kann dies die Zeit bis zum ersten Frame verkürzen. Diese Funktion verhindert, dass beim Abrufen der Lizenz eine Verzögerung erfolgt, wenn der Benutzer die wiederzugebenden Inhalte auswählt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-132">This can decrease the time to first frame by acquiring licenses for multiple pieces of content while the user is still browsing your content library; this prevents a delay for license acquisition when the user selects the content to play.</span></span> <span data-ttu-id="e41b6-133">Darüber hinaus können Audio- und Videodatenströme verschlüsselt werden, um Schlüssel zu trennen, indem ein Inhaltsheader aktiviert wird, der mehrere Schlüsselkennungen (KIDs) enthält. Dadurch können mit einem einzigen Lizenzabruf alle Lizenzen für alle Datenströme in einer Inhaltsdatei abgerufen werden, anstatt zu diesem Zweck benutzerdefinierte Logik und mehrere Lizenzabrufanforderungen verwenden zu müssen.</span><span class="sxs-lookup"><span data-stu-id="e41b6-133">In addition, it allows audio and video streams to be encrypted to separate keys by enabling a content header that includes multiple key identifiers (KIDs); this enables a single license acquisition to acquire all licenses for all streams within a content file instead of having to use custom logic and multiple license acquisition requests to achieve the same result.</span></span>

-   <span data-ttu-id="e41b6-134">Unterstützung für den Echtzeitablauf, d.h. einer Lizenz mit begrenzter Dauer (Limited Duration License, LDL), wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-134">Added real time expiration support, or limited duration license (LDL).</span></span>

    <span data-ttu-id="e41b6-135">Bietet die Möglichkeit, einen Echtzeitablauf für Lizenzen festzulegen und während der Wiedergabe einen reibungslosen Wechsel zwischen einer ablaufenden Lizenz und einer anderen (gültigen) Lizenz sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="e41b6-135">Provides the ability to set real-time expiration on licenses and smoothly transition from an expiring license to another (valid) license in the middle of playback.</span></span> <span data-ttu-id="e41b6-136">In Kombination mit dem Abruf mehrerer Lizenzen in einer Nachricht kann eine App so mehrere LDLs asynchron abrufen, während der Benutzer noch die Inhaltsbibliothek durchsucht, und nur eine Lizenz mit längerer Dauer abrufen, sobald der Benutzer den wiederzugebenden Inhalt ausgewählt hat.</span><span class="sxs-lookup"><span data-stu-id="e41b6-136">When combined with acquisition of multiple licenses in one message, this allows an app to acquire several LDLs asynchronously while the user is still browsing the content library and only acquire a longer duration license once the user has selected content to playback.</span></span> <span data-ttu-id="e41b6-137">Die Wiedergabe wird dann schneller gestartet (weil bereits eine Lizenz verfügbar ist), und da die App beim Ablauf der LDL bereits eine Lizenz mit längerer Dauer abgerufen hat, wird die Wiedergabe unterbrechungsfrei bis zum Ende des Inhalts fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-137">Playback will then start more quickly (because a license is already available) and, since the app will have acquired a longer duration license by the time the LDL expires, smoothly continue playback to the end of the content without interruption.</span></span>

-   <span data-ttu-id="e41b6-138">Nicht persistente Lizenzketten wurden hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-138">Added non-persistent license chains.</span></span>
-   <span data-ttu-id="e41b6-139">Unterstützung für zeitbasierte Einschränkungen (einschließlich Ablauf, Ablauf nach der ersten Wiedergabe und Echtzeitablauf) für nicht persistente Lizenzen wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-139">Added support for time-based restrictions (including expiration, expire after first play, and real time expiration) on non-persistent licenses.</span></span>
-   <span data-ttu-id="e41b6-140">Richtlinienunterstützung für HDCPTyp1 (Version2.2 unter Windows10) wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-140">Added HDCP Type 1 (version 2.2 on Windows 10) policy support.</span></span>

    <span data-ttu-id="e41b6-141">Weitere Informationen finden Sie unter [Zu berücksichtigende Informationen](#things-to-consider).</span><span class="sxs-lookup"><span data-stu-id="e41b6-141">See [Things to Consider](#things-to-consider) for more information.</span></span>

-   <span data-ttu-id="e41b6-142">Miracast ist jetzt als Ausgabe implizit.</span><span class="sxs-lookup"><span data-stu-id="e41b6-142">Miracast is now implicit as an output.</span></span>
-   <span data-ttu-id="e41b6-143">Sicheres Beenden wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-143">Added secure stop.</span></span>

    <span data-ttu-id="e41b6-144">Dank des sicheren Beendens kann ein PlayReady-Gerät einem Medienstreamingdienst zuverlässig bestätigen, dass die Medienwiedergabe für einen bestimmten Inhalt beendet wurde.</span><span class="sxs-lookup"><span data-stu-id="e41b6-144">Secure stop provides the means for a PlayReady device to confidently assert to a media streaming service that media playback has stopped for any given piece of content.</span></span> <span data-ttu-id="e41b6-145">Mit dieser Funktion wird sichergestellt, dass Ihre Medienstreamingdienste präzise Erzwingung und Berichte zu Nutzungseinschränkungen auf verschiedenen Geräten für ein bestimmtes Konto bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="e41b6-145">This capability ensures your media streaming services provide accurate enforcement and reporting of usage limitations on different devices for a given account.</span></span>

-   <span data-ttu-id="e41b6-146">Audio- und Videolizenztrennung wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-146">Added audio and video license separation.</span></span>

    <span data-ttu-id="e41b6-147">Separate Spuren verhindern, dass Videos als Audio decodiert werden. Dadurch wird ein stabilerer Inhaltsschutz gewährleistet.</span><span class="sxs-lookup"><span data-stu-id="e41b6-147">Separate tracks prevent video from being decoded as audio; enabling more robust content protection.</span></span> <span data-ttu-id="e41b6-148">Neue Standards erfordern separate Schlüssel für Audio- und Videospuren.</span><span class="sxs-lookup"><span data-stu-id="e41b6-148">Emerging standards are requiring separate keys for audio and visual tracks.</span></span>

-   <span data-ttu-id="e41b6-149">MaxResDecode-Feature hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-149">Added MaxResDecode.</span></span>

    <span data-ttu-id="e41b6-150">Dieses Feature wurde hinzugefügt, um die Wiedergabe von Inhalten auf eine maximale Auflösung zu beschränken, auch wenn der Benutzer einen leistungsfähigeren Schlüssel (aber keine Lizenz) besitzt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-150">This feature was added to limit playback of content to a maximum resolution even when in possession of a more capable key (but not a license).</span></span> <span data-ttu-id="e41b6-151">Dadurch werden Szenarien unterstützt, in denen mehrere Datenstromgrößen mit einem einzelnen Schlüssel codiert werden.</span><span class="sxs-lookup"><span data-stu-id="e41b6-151">It supports cases where multiple stream sizes are encoded with a single key.</span></span>

<span data-ttu-id="e41b6-152">PlayReady DRM wurden die folgenden neuen Schnittstellen, Klassen und Enumerationen hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="e41b6-152">The following new interfaces, classes, and enumerations were added to PlayReady DRM:</span></span>

-   <span data-ttu-id="e41b6-153">[**IPlayReadyLicenseAcquisitionServiceRequest**
            ](https://msdn.microsoft.com/library/windows/apps/dn986077)-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="e41b6-153">[**IPlayReadyLicenseAcquisitionServiceRequest**](https://msdn.microsoft.com/library/windows/apps/dn986077) interface</span></span>
-   <span data-ttu-id="e41b6-154">[**IPlayReadyLicenseSession**
            ](https://msdn.microsoft.com/library/windows/apps/dn986080)-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="e41b6-154">[**IPlayReadyLicenseSession**](https://msdn.microsoft.com/library/windows/apps/dn986080) interface</span></span>
-   <span data-ttu-id="e41b6-155">[**IPlayReadySecureStopServiceRequest**
            ](https://msdn.microsoft.com/library/windows/apps/dn986090)-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="e41b6-155">[**IPlayReadySecureStopServiceRequest**](https://msdn.microsoft.com/library/windows/apps/dn986090) interface</span></span>
-   <span data-ttu-id="e41b6-156">[**PlayReadyLicenseSession**
            ](https://msdn.microsoft.com/library/windows/apps/dn986309)-Klasse</span><span class="sxs-lookup"><span data-stu-id="e41b6-156">[**PlayReadyLicenseSession**](https://msdn.microsoft.com/library/windows/apps/dn986309) class</span></span>
-   <span data-ttu-id="e41b6-157">[**PlayReadySecureStopIterable**
            ](https://msdn.microsoft.com/library/windows/apps/dn986371)-Klasse</span><span class="sxs-lookup"><span data-stu-id="e41b6-157">[**PlayReadySecureStopIterable**](https://msdn.microsoft.com/library/windows/apps/dn986371) class</span></span>
-   <span data-ttu-id="e41b6-158">[**PlayReadySecureStopIterator**
            ](https://msdn.microsoft.com/library/windows/apps/dn986375)-Klasse</span><span class="sxs-lookup"><span data-stu-id="e41b6-158">[**PlayReadySecureStopIterator**](https://msdn.microsoft.com/library/windows/apps/dn986375) class</span></span>
-   <span data-ttu-id="e41b6-159">[**PlayReadyHardwareDRMFeatures**
            ](https://msdn.microsoft.com/library/windows/apps/dn986265)-Enumerator</span><span class="sxs-lookup"><span data-stu-id="e41b6-159">[**PlayReadyHardwareDRMFeatures**](https://msdn.microsoft.com/library/windows/apps/dn986265) enumerator</span></span>

<span data-ttu-id="e41b6-160">Es wurde ein neues Beispiel erstellt, um die Verwendung der neuen Features von PlayReady DRM zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="e41b6-160">A new sample has been created to demonstrate how to use the new features of PlayReady DRM.</span></span> <span data-ttu-id="e41b6-161">Das Beispiel können Sie hier [http://go.microsoft.com/fwlink/p/?linkid=331670&clcid=0x409](http://go.microsoft.com/fwlink/p/?linkid=331670) herunterladen.</span><span class="sxs-lookup"><span data-stu-id="e41b6-161">The sample can be downloaded from [http://go.microsoft.com/fwlink/p/?linkid=331670&clcid=0x409](http://go.microsoft.com/fwlink/p/?linkid=331670).</span></span>

## <a name="things-to-consider"></a><span data-ttu-id="e41b6-162">Zu berücksichtigende Informationen</span><span class="sxs-lookup"><span data-stu-id="e41b6-162">Things to consider</span></span>

-   <span data-ttu-id="e41b6-163">PlayReady DRM unterstützt jetzt HDCP Typ1 (unterstützt in HDCP-Version2.1 oder höher).</span><span class="sxs-lookup"><span data-stu-id="e41b6-163">PlayReady DRM now supports HDCP Type 1 (supported in HDCP version 2.1 or later).</span></span> <span data-ttu-id="e41b6-164">PlayReady enthält in der Lizenz eine zu erzwingende HDCP-Typeinschränkungsrichtlinie für das Gerät.</span><span class="sxs-lookup"><span data-stu-id="e41b6-164">PlayReady carries an HDCP Type Restriction policy in the license for the device to enforce.</span></span> <span data-ttu-id="e41b6-165">Unter Windows10 erzwingt diese Richtlinie die Einbindung von HDCP2.2 oder höher.</span><span class="sxs-lookup"><span data-stu-id="e41b6-165">On Windows 10, this policy will enforce that HDCP 2.2 or later is engaged.</span></span> <span data-ttu-id="e41b6-166">Dieses Feature kann in der PlayReady Serverv3.0SDK-Lizenz aktiviert werden. (Der Server steuert diese Richtlinie in der Lizenz mit der GUID der HDCP-Typeinschränkung).</span><span class="sxs-lookup"><span data-stu-id="e41b6-166">This feature can be enabled in your PlayReady Server v3.0 SDK license (the server controls this policy in the license using the HDCP Type Restriction GUID).</span></span> <span data-ttu-id="e41b6-167">Weitere Informationen finden Sie unter [PlayReady-Kompatibilität und Stabilitätsregeln](http://www.microsoft.com/playready/licensing/compliance/).</span><span class="sxs-lookup"><span data-stu-id="e41b6-167">For more information, see the [PlayReady Compliance and Robustness Rules](http://www.microsoft.com/playready/licensing/compliance/).</span></span>
-   <span data-ttu-id="e41b6-168">Windows Media Video (auch bekannt als VC-1) wird nicht vom Hardware-DRM unterstützt (siehe [Außerkraftsetzen des Hardware-DRM](hardware-drm.md#override-hardware-drm)).</span><span class="sxs-lookup"><span data-stu-id="e41b6-168">Windows Media Video (also known as VC-1) is not supported in hardware DRM (see [Override Hardware DRM](hardware-drm.md#override-hardware-drm)).</span></span>
-   <span data-ttu-id="e41b6-169">PlayReady DRM unterstützt jetzt den High Efficiency Video Coding (HEVC/H.265)-Videokomprimierungsstandard.</span><span class="sxs-lookup"><span data-stu-id="e41b6-169">PlayReady DRM now supports the High Efficiency Video Coding (HEVC /H.265) video compression standard.</span></span> <span data-ttu-id="e41b6-170">Zur Unterstützung von HEVC muss Ihre App Inhalte mit Common Encryption Scheme (CENC) Version2 verwenden, d.h. die Slice-Header des Inhalts bleiben unverschlüsselt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-170">To support HEVC, your app must use Common Encryption Scheme (CENC) version 2 content which includes leaving the content's slice headers in the clear.</span></span> <span data-ttu-id="e41b6-171">Weitere Informationen finden Sie in ISO/IEC 23001-7 (Information technology – MPEG systems technologies – Part 7: Common encryption in ISO base media file format files; Spezifikationsversion ISO/IEC 23001-7:2015 oder höher).</span><span class="sxs-lookup"><span data-stu-id="e41b6-171">Refer to ISO/IEC 23001-7 Information technology -- MPEG systems technologies -- Part 7: Common encryption in ISO base media file format files (Spec version ISO/IEC 23001-7:2015 or higher is required.) for more information.</span></span> <span data-ttu-id="e41b6-172">Microsoft empfiehlt außerdem die Verwendung von CENC Version2 für alle HWDRM-Inhalte.</span><span class="sxs-lookup"><span data-stu-id="e41b6-172">Microsoft also recommends using CENC version 2 for all HWDRM content.</span></span> <span data-ttu-id="e41b6-173">Zudem wird HEVC nicht von allen Hardware-DRM-Typen unterstützt (siehe [Außerkraftsetzen des Hardware-DRM](hardware-drm.md#override-hardware-drm)).</span><span class="sxs-lookup"><span data-stu-id="e41b6-173">In addition, some hardware DRM will support HEVC and some will not (see [Override Hardware DRM](hardware-drm.md#override-hardware-drm)).</span></span>
-   <span data-ttu-id="e41b6-174">Um bestimmte neue Features von PlayReady3.0 nutzen zu können (u.a. SL3000 für hardwarebasierte Clients, Abruf mehrerer nicht persistenter Lizenzen in einer Lizenzabrufnachricht und zeitbasierte Einschränkungen für nicht persistente Lizenzen), muss für den PlayReady-Server Microsoft PlayReady Server Software Development Kit v3.0.2769 oder höher verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e41b6-174">To take advantage of certain new PlayReady 3.0 features (including, but not limited to, SL3000 for hardware-based clients, acquiring multiple non-persistent licenses in one license acquisition message, and time-based restrictions on non-persistent licenses), the PlayReady server is required to be the Microsoft PlayReady Server Software Development Kit v3.0.2769 Release version or later.</span></span>
-   <span data-ttu-id="e41b6-175">Je nachdem, welche Ausgabeschutzrichtlinie in der Inhaltslizenz festgelegt ist, kann die Medienwiedergabe für Endbenutzer fehlschlagen, wenn die verbundene Ausgabe der Benutzer diese Anforderungen nicht erfüllt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-175">Depending on the Output Protection Policy specified in the content license, media playback may fail for end users if their connected output does not support those requirements.</span></span> <span data-ttu-id="e41b6-176">In der folgenden Tabelle sind die Fehler aufgeführt, die in diesem Zusammenhang häufig auftreten.</span><span class="sxs-lookup"><span data-stu-id="e41b6-176">The following table lists the set of common errors that occur as a result.</span></span> <span data-ttu-id="e41b6-177">Weitere Informationen finden Sie unter [PlayReady-Kompatibilität und Stabilitätsregeln](http://www.microsoft.com/playready/licensing/compliance/).</span><span class="sxs-lookup"><span data-stu-id="e41b6-177">For more information, see the [PlayReady Compliance and Robustness Rules](http://www.microsoft.com/playready/licensing/compliance/).</span></span>

| <span data-ttu-id="e41b6-178">Fehler</span><span class="sxs-lookup"><span data-stu-id="e41b6-178">Error</span></span>                                                   | <span data-ttu-id="e41b6-179">Wert</span><span class="sxs-lookup"><span data-stu-id="e41b6-179">Value</span></span>      | <span data-ttu-id="e41b6-180">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e41b6-180">Description</span></span>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|---------------------------------------------------------|------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e41b6-181">ERROR\_GRAPHICS\_OPM\_OUTPUT\_DOES\_NOT\_SUPPORT\_HDCP</span><span class="sxs-lookup"><span data-stu-id="e41b6-181">ERROR\_GRAPHICS\_OPM\_OUTPUT\_DOES\_NOT\_SUPPORT\_HDCP</span></span>  | <span data-ttu-id="e41b6-182">0xC0262513</span><span class="sxs-lookup"><span data-stu-id="e41b6-182">0xC0262513</span></span> | <span data-ttu-id="e41b6-183">Die Ausgabeschutzrichtlinie der Lizenz erfordert, dass der Monitor HDCP einbindet, die Einbindung war aber nicht möglich.</span><span class="sxs-lookup"><span data-stu-id="e41b6-183">The license's Output Protection Policy requires the monitor to engage HDCP, but HDCP was unable to be engaged.</span></span>                                                                                                                                                                                                                                                                                                                                                                                              |
| <span data-ttu-id="e41b6-184">MF\_E\_POLICY\_UNSUPPORTED</span><span class="sxs-lookup"><span data-stu-id="e41b6-184">MF\_E\_POLICY\_UNSUPPORTED</span></span>                              | <span data-ttu-id="e41b6-185">0xC00D7159</span><span class="sxs-lookup"><span data-stu-id="e41b6-185">0xC00D7159</span></span> | <span data-ttu-id="e41b6-186">Die Ausgabeschutzrichtlinie der Lizenz erfordert, dass der Monitor HDCP Typ 1 einbindet, die Einbindung war aber nicht möglich.</span><span class="sxs-lookup"><span data-stu-id="e41b6-186">The license's Output Protection Policy requires the monitor to engage HDCP Type 1, but HDCP Type 1 was unable to be engaged.</span></span>                                                                                                                                                                                                                                                                                                                                                                                |
| <span data-ttu-id="e41b6-187">DRM\_E\_TEE\_OUTPUT\_PROTECTION\_REQUIREMENTS\_NOT\_MET</span><span class="sxs-lookup"><span data-stu-id="e41b6-187">DRM\_E\_TEE\_OUTPUT\_PROTECTION\_REQUIREMENTS\_NOT\_MET</span></span> | <span data-ttu-id="e41b6-188">0x8004CD22</span><span class="sxs-lookup"><span data-stu-id="e41b6-188">0x8004CD22</span></span> | <span data-ttu-id="e41b6-189">Dieser Fehlercode tritt nur bei der Verwendung des Hardware-DRM auf.</span><span class="sxs-lookup"><span data-stu-id="e41b6-189">This error code only occurs when running under hardware DRM.</span></span> <span data-ttu-id="e41b6-190">Die Ausgabeschutzrichtlinie der Lizenz erfordert, dass der Monitor HDCP einbindet oder die effektive Auflösung des Inhalts verringert, die Einbindung von HDCP war jedoch nicht möglich, und die effektive Auflösung des Inhalts konnte nicht verringert werden, weil das Hardware-DRM die Verringerung der effektiven Auflösung von Inhalten nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-190">The license's Output Protection Policy requires the monitor to engage HDCP or to reduce the content's effective resolution, but HDCP was unable to be engaged and the content's effective resolution could not be reduced because hardware DRM does not support reducing the content's resolution.</span></span> <span data-ttu-id="e41b6-191">Bei Verwendung des Software-DRM wird der Inhalt wiedergegeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-191">Under software DRM, the content plays.</span></span> <span data-ttu-id="e41b6-192">Weitere Informationen finden Sie unter [Überlegungen zur Verwendung des Hardware-DRM](hardware-drm.md#considerations-for-using-hardware-drm).</span><span class="sxs-lookup"><span data-stu-id="e41b6-192">See [Considerations for Using Hardware DRM](hardware-drm.md#considerations-for-using-hardware-drm).</span></span> |
| <span data-ttu-id="e41b6-193">ERROR\_GRAPHICS\_OPM\_NOT\_SUPPORTED</span><span class="sxs-lookup"><span data-stu-id="e41b6-193">ERROR\_GRAPHICS\_OPM\_NOT\_SUPPORTED</span></span>                    | <span data-ttu-id="e41b6-194">0xc0262500</span><span class="sxs-lookup"><span data-stu-id="e41b6-194">0xc0262500</span></span> | <span data-ttu-id="e41b6-195">Der Grafiktreiber unterstützt Ausgabeschutz nicht.</span><span class="sxs-lookup"><span data-stu-id="e41b6-195">The graphics driver does not support Output Protection.</span></span> <span data-ttu-id="e41b6-196">Dies kann z.B. der Fall sein, wenn der Monitor über VGA verbunden ist oder kein entsprechender Grafiktreiber für die digitale Ausgabe installiert ist.</span><span class="sxs-lookup"><span data-stu-id="e41b6-196">For example, the monitor is connected through VGA or an appropriate graphics driver for the digital output is not installed.</span></span> <span data-ttu-id="e41b6-197">In letzterem Fall ist in der Regel der Treiber „Microsoft Basic Display Adapter” installiert, und das Problem kann durch Installieren eines entsprechenden Grafiktreibers behoben werden.</span><span class="sxs-lookup"><span data-stu-id="e41b6-197">In the latter case, the typical driver that is installed is the Microsoft Basic Display Adapter and installing an appropriate graphics driver will resolve the issue.</span></span>                                                                                                                                                  |

## <a name="output-protection"></a><span data-ttu-id="e41b6-198">Ausgabeschutz</span><span class="sxs-lookup"><span data-stu-id="e41b6-198">Output protection</span></span>

<span data-ttu-id="e41b6-199">Im folgenden Abschnitt wird das Verhalten bei Verwendung von PlayReady DRM für Windows10 mit Ausgabeschutzrichtlinien in einer PlayReady-Lizenz beschrieben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-199">The following section describes the behavior when using PlayReady DRM for Windows 10 with output protection policies in a PlayReady license.</span></span>

<span data-ttu-id="e41b6-200">PlayReady DRM unterstützt die Ausgabeschutzebenen in der **erweiterbaren Medienrechtespezifikation von Microsoft PlayReady**.</span><span class="sxs-lookup"><span data-stu-id="e41b6-200">PlayReady DRM supports output protection levels contained in the **Microsoft PlayReady Extensible Media Rights Specification**.</span></span> <span data-ttu-id="e41b6-201">Dieses Dokument ist Teil des Dokumentationspakets, das zusammen mit lizenzierten PlayReady-Produkten bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="e41b6-201">This document can be found in the documentation pack that comes with PlayReady licensed products.</span></span>

> [!NOTE]
> <span data-ttu-id="e41b6-202">Die zulässigen Werte für Ausgabesicherheitsebenen, die von einem Lizenzserver festgelegt werden können, unterliegen den [PlayReady-Kompatibilitätsregeln](https://www.microsoft.com/playready/licensing/compliance/).</span><span class="sxs-lookup"><span data-stu-id="e41b6-202">The allowed values for output protection levels that can be set by a licensing server are governed by the [PlayReady Compliance Rules](https://www.microsoft.com/playready/licensing/compliance/).</span></span>

<span data-ttu-id="e41b6-203">PlayReady DRM ermöglicht die Wiedergabe von Inhalten mit Ausgabeschutzrichtlinien nur über Ausgabeanschlüsse gemäß Angabe in den PlayReady-Kompatibilitätsregeln.</span><span class="sxs-lookup"><span data-stu-id="e41b6-203">PlayReady DRM allows playback of content with output protection policies only on output connectors as specified in the PlayReady Compliance Rules.</span></span> <span data-ttu-id="e41b6-204">Weitere Informationen zu in den PlayReady-Kompatibilitätsregeln angegebenen Ausgabeanschlussbedingungen finden Sie in den [definierten Bedingungen für PlayReady-Kompatibilität und Stabilitätsregeln](https://www.microsoft.com/playready/licensing/compliance/).</span><span class="sxs-lookup"><span data-stu-id="e41b6-204">For more information about output connector terms specified in the PlayReady Compliance Rules, see [Defined Terms for PlayReady Compliance and Robustness Rules](https://www.microsoft.com/playready/licensing/compliance/).</span></span>

<span data-ttu-id="e41b6-205">Dieser Abschnitt konzentriert sich auf Ausgabeschutzszenarien mit PlayReady DRM für Windows10 und PlayReady Hardware DRM für Windows10 (auch auf einigen Windows-Clients verfügbar).</span><span class="sxs-lookup"><span data-stu-id="e41b6-205">This section focuses on output protection scenarios with PlayReady DRM for Windows 10 and PlayReady Hardware DRM for Windows 10, which is also available on some Windows clients.</span></span> <span data-ttu-id="e41b6-206">Mit PlayReady HWDRM wird der gesamte Ausgabeschutz innerhalb der Windows-TEE-Implementierung erzwungen (siehe [Hardware-DRM](hardware-drm.md)).</span><span class="sxs-lookup"><span data-stu-id="e41b6-206">With PlayReady HWDRM, all output protections are enforced from within the Windows TEE implementation (see [Hardware DRM](hardware-drm.md)).</span></span> <span data-ttu-id="e41b6-207">Aus diesem Grund unterscheidet sich das Verhalten in einigen Fällen von der Verwendung von PlayReady SWDRM (Software-DRM):</span><span class="sxs-lookup"><span data-stu-id="e41b6-207">As a result, some behaviors differ from when using PlayReady SWDRM (software DRM):</span></span>

* <span data-ttu-id="e41b6-208">Unterstützung der Ausgabeschutzebene270 (Output Protection Level, OPL) für nicht komprimierte digitale Videos: PlayReady HWDRM für Windows10 unterstützt keine Abwärtsauflösung und erzwingt die Einbindung von HDCP (High-bandwidth Digital Content Protection).</span><span class="sxs-lookup"><span data-stu-id="e41b6-208">Support for Output Protection Level (OPL) for Uncompressed Digital Video 270: PlayReady HWDRM for Windows 10 doesn't support down-resolution and will enforce that HDCP (High-bandwidth Digital Content Protection) is engaged.</span></span> <span data-ttu-id="e41b6-209">Es empfiehlt sich, bei HD-Inhalten für das HWDRM einen OPL-Wert zu verwenden, der größer als270 ist (dies ist jedoch nicht zwingend erforderlich).</span><span class="sxs-lookup"><span data-stu-id="e41b6-209">It is recommended that high definition content for HWDRM have an OPL greater than 270 (although it is not required).</span></span> <span data-ttu-id="e41b6-210">Darüber hinaus sollten Sie die HDCP-Typeinschränkung in der Lizenz festlegen (HDCP-Version2.2 oder höher).</span><span class="sxs-lookup"><span data-stu-id="e41b6-210">Additionally, you should set HDCP type restriction in the license (HDCP version 2.2 or later).</span></span>
* <span data-ttu-id="e41b6-211">Im Gegensatz zum SWDRM wird beim HWDRM der Ausgabeschutz für alle Monitore basierend auf dem langsamsten Monitor erzwungen.</span><span class="sxs-lookup"><span data-stu-id="e41b6-211">Unlike SWDRM, with HWDRM, output protections are enforced on all monitors based on the least capable monitor.</span></span> <span data-ttu-id="e41b6-212">Wenn der Benutzer beispielsweise zwei Monitore angeschlossen hat und nur einer davon HDCP unterstützt, ist die Wiedergabe nicht möglich, falls die Lizenz HDCP erfordert. Dies gilt auch dann, wenn der Inhalt nur auf dem Monitor gerendert wird, der HDCP unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-212">For example, if the user has two monitors connected where one supports HDCP and the other doesn't, playback will fail if the license requires HDCP even if the content is only being rendered on the monitor that supports HDCP.</span></span> <span data-ttu-id="e41b6-213">Beim SWDRM wird der Inhalt wiedergegeben, solange das Rendering nur auf dem Monitor erfolgt, der HDCP unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-213">In SWDRM, content will play back as long as it's only being rendered on the monitor that supports HDCP.</span></span>
* <span data-ttu-id="e41b6-214">Es ist nicht garantiert, dass das HWDRM vom Client verwendet wird und dass das Verfahren sicher ist, es sei denn, von den Inhaltsschlüsseln und -lizenzen werden die folgenden Bedingungen erfüllt:</span><span class="sxs-lookup"><span data-stu-id="e41b6-214">HWDRM is not guaranteed to be used by the client and secure unless the following conditions are met by the content keys and licenses:</span></span>
    * <span data-ttu-id="e41b6-215">Die für den Videoinhaltsschlüssel verwendete Lizenz muss mindestens die Sicherheitsstufe3.000 besitzen.</span><span class="sxs-lookup"><span data-stu-id="e41b6-215">The license used for the video content key must have a minimum security level of 3000.</span></span>
    * <span data-ttu-id="e41b6-216">Audiodaten müssen mit einem anderen Inhaltsschlüssel verschlüsselt werden als Videodaten, und die für Audiodaten verwendete Lizenz muss mindestens die Sicherheitsstufe2.000 besitzen.</span><span class="sxs-lookup"><span data-stu-id="e41b6-216">Audio must be encrypted to a different content key than video, and the license used for audio must have a minimum security level of 2000.</span></span> <span data-ttu-id="e41b6-217">Alternativ können Audiodaten auch unverschlüsselt bleiben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-217">Alternatively, audio could be left in the clear.</span></span>
* <span data-ttu-id="e41b6-218">In allen SWDRM-Szenarien darf die Sicherheitsebene der PlayReady-Lizenz für den Audio- und/oder Videoinhaltsschlüssel maximal2.000 betragen.</span><span class="sxs-lookup"><span data-stu-id="e41b6-218">All SWDRM scenarios require that the minimum security level of the PlayReady license used for the audio and/or video content key is lower or equal to 2000.</span></span>

### <a name="output-protection-levels"></a><span data-ttu-id="e41b6-219">Ausgabeschutzebenen</span><span class="sxs-lookup"><span data-stu-id="e41b6-219">Output protection levels</span></span>

<span data-ttu-id="e41b6-220">Die folgende Tabelle veranschaulicht die Zuordnungen zwischen verschiedenen OPLs in der PlayReady-Lizenz und deren Erzwingung durch PlayReady DRM für Windows10:</span><span class="sxs-lookup"><span data-stu-id="e41b6-220">The following table outlines the mappings between various OPLs in the PlayReady license and how PlayReady DRM for Windows 10 enforces them.</span></span>

#### <a name="video"></a><span data-ttu-id="e41b6-221">Video</span><span class="sxs-lookup"><span data-stu-id="e41b6-221">Video</span></span>

<table>
    <tr>
        <th rowspan="2"><span data-ttu-id="e41b6-222">OPL</span><span class="sxs-lookup"><span data-stu-id="e41b6-222">OPL</span></span></th>
        <th><span data-ttu-id="e41b6-223">Komprimierte digitale Videos</span><span class="sxs-lookup"><span data-stu-id="e41b6-223">Compressed digital video</span></span></th>
        <th colspan="2"><span data-ttu-id="e41b6-224">Unkomprimierte digitale Videos</span><span class="sxs-lookup"><span data-stu-id="e41b6-224">Uncompressed digital video</span></span></th>
        <th><span data-ttu-id="e41b6-225">TV (analog)</span><span class="sxs-lookup"><span data-stu-id="e41b6-225">Analog TV</span></span></th>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-226">Beliebig</span><span class="sxs-lookup"><span data-stu-id="e41b6-226">Any</span></span></th>
        <th colspan="2"><span data-ttu-id="e41b6-227">HDMI, DVI, DisplayPort, MHL</span><span class="sxs-lookup"><span data-stu-id="e41b6-227">HDMI, DVI, DisplayPort, MHL</span></span></th>
        <th><span data-ttu-id="e41b6-228">Komponente, Composite</span><span class="sxs-lookup"><span data-stu-id="e41b6-228">Component, Composite</span></span></th>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-229">100</span><span class="sxs-lookup"><span data-stu-id="e41b6-229">100</span></span></th>
        <td rowspan="6"><span data-ttu-id="e41b6-230">Nicht zutreffend\*</span><span class="sxs-lookup"><span data-stu-id="e41b6-230">N/A\*</span></span></td>
        <td colspan="2"><span data-ttu-id="e41b6-231">Inhalt wird übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-231">Passes content</span></span></td>
        <td><span data-ttu-id="e41b6-232">Inhalt wird übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-232">Passes content</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-233">150</span><span class="sxs-lookup"><span data-stu-id="e41b6-233">150</span></span></th>
        <td colspan="2" rowspan="2"><span data-ttu-id="e41b6-234">Nicht zutreffend\*</span><span class="sxs-lookup"><span data-stu-id="e41b6-234">N/A\*</span></span></td>
        <td><span data-ttu-id="e41b6-235">Inhalt wird übergeben, wenn CGMS-A CopyNever eingebunden wird oder CGMS-A nicht eingebunden werden kann.</span><span class="sxs-lookup"><span data-stu-id="e41b6-235">Passes content when CGMS-A CopyNever is engaged or if CGMS-A can't be engaged</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-236">200</span><span class="sxs-lookup"><span data-stu-id="e41b6-236">200</span></span></th>
        <td><span data-ttu-id="e41b6-237">Inhalt wird übergeben, wenn CGMS-A CopyNever eingebunden wird.</span><span class="sxs-lookup"><span data-stu-id="e41b6-237">Passes content when CGMS-A CopyNever is engaged</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-238">250</span><span class="sxs-lookup"><span data-stu-id="e41b6-238">250</span></span></th>
        <td colspan="2"><span data-ttu-id="e41b6-239">Versucht, HDCP einzubinden, der Inhalt wird jedoch unabhängig vom Ergebnis übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-239">Attempts to engage HDCP, but passes content regardless of result</span></span></td>
        <td rowspan="5"><span data-ttu-id="e41b6-240">Nicht zutreffend\*</span><span class="sxs-lookup"><span data-stu-id="e41b6-240">N/A\*</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-241">270</span><span class="sxs-lookup"><span data-stu-id="e41b6-241">270</span></span></th>
        <td><span data-ttu-id="e41b6-242"><b>SWDRM</b>: Versucht, HDCP einzubinden.</span><span class="sxs-lookup"><span data-stu-id="e41b6-242"><b>SWDRM</b>: Attempts to engage HDCP.</span></span> <span data-ttu-id="e41b6-243">Sollte die Einbindung von HDCP nicht möglich sein, schränkt der PC die effektive Auflösung auf 520.000Pixel pro Frame ein und übergibt den Inhalt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-243">If HDCP fails to engage, the PC will constrain the effective resolution to 520,000 pixels per frame and pass the content</span></span></td>
        <td><span data-ttu-id="e41b6-244"><b>HWDRM</b>: Inhalt wird mit HDCP übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-244"><b>HWDRM</b>: Passes content with HDCP.</span></span> <span data-ttu-id="e41b6-245">Wenn die Einbindung von HDCP nicht möglich ist, wird die Wiedergabe über HDMI/DVI-Anschlüsse blockiert.</span><span class="sxs-lookup"><span data-stu-id="e41b6-245">If HDCP fails to engage, playback to HDMI/DVI ports is blocked</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-246">300</span><span class="sxs-lookup"><span data-stu-id="e41b6-246">300</span></span></th>
        <td colspan="2">
            <p><span data-ttu-id="e41b6-247">
                \*\*Wenn die HDCP-Typbeschränkung NICHT definiert ist:\*\* Inhalt wird mit HDCP übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-247">
                \*\*When HDCP type restriction is NOT defined:\*\* Passes content with HDCP.</span></span> <span data-ttu-id="e41b6-248">Sollte die Einbindung von HDCP nicht möglich sein, wird die Wiedergabe über HDMI/DVI-Anschlüsse blockiert.</span><span class="sxs-lookup"><span data-stu-id="e41b6-248">If HDCP fails to engage, playback to HDMI/DVI ports is blocked.</span></span>
            </p>
            <p><span data-ttu-id="e41b6-249">
                \*\*Wenn die HDCP-Typeinschränkung definiert ist\*\*: Inhalt wird mit HDCP2.2 und Inhaltsdatenstrom-Typ„1“ übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-249">
                \*\*When HDCP type restriction IS defined\*\*: Passes content with HDCP 2.2 and content stream type set to 1.</span></span> <span data-ttu-id="e41b6-250">Wenn die Einbindung von HDCP nicht möglich ist oder der Inhaltsdatenstromtyp nicht auf 1 festgelegt werden kann, wird die Wiedergabe über HDMI/DVI-Anschlüsse blockiert.</span><span class="sxs-lookup"><span data-stu-id="e41b6-250">If HDCP fails to engage or content stream type can't be set to 1, playback to HDMI/DVI ports is blocked.</span></span>
            </p>
        </td>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-251">400</span><span class="sxs-lookup"><span data-stu-id="e41b6-251">400</span></span></th>
        <td rowspan="2"><span data-ttu-id="e41b6-252">Windows10 übergibt komprimierte digitale Videoinhalte niemals an Ausgaben, unabhängig vom nachfolgenden OPL-Wert.</span><span class="sxs-lookup"><span data-stu-id="e41b6-252">Windows 10 never passes compressed digital video content to outputs, regardless of the subsequent OPL value.</span></span> <span data-ttu-id="e41b6-253">Weitere Informationen zu komprimierten digitalen Videoinhalten finden Sie in den <a href="https://www.microsoft.com/playready/licensing/compliance/">Kompatibilitätsregeln für PlayReady-Produkte</a>.</span><span class="sxs-lookup"><span data-stu-id="e41b6-253">For more information about compressed digital video content, see the <a href="https://www.microsoft.com/playready/licensing/compliance/">Compliance Rules for PlayReady Products</a>.</span></span></td>
        <td colspan="2" rowspan="2"><span data-ttu-id="e41b6-254">Nicht zutreffend\*</span><span class="sxs-lookup"><span data-stu-id="e41b6-254">N/A\*</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-255">500</span><span class="sxs-lookup"><span data-stu-id="e41b6-255">500</span></span></th>
    </tr>
</table>
<br/>

<span data-ttu-id="e41b6-256">\* Nicht alle Werte für Ausgabeschutzebenen können von einem Lizenzserver festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="e41b6-256">\* Not all values for output protection levels can be set by a licensing server.</span></span> <span data-ttu-id="e41b6-257">Weitere Informationen finden Sie unter [PlayReady-Kompatibilitätsregeln](https://www.microsoft.com/playready/licensing/compliance/).</span><span class="sxs-lookup"><span data-stu-id="e41b6-257">For more information, see the [PlayReady Compliance Rules](https://www.microsoft.com/playready/licensing/compliance/).</span></span>

#### <a name="audio"></a><span data-ttu-id="e41b6-258">Audio</span><span class="sxs-lookup"><span data-stu-id="e41b6-258">Audio</span></span>

<table>
    <tr>
        <th rowspan="2"><span data-ttu-id="e41b6-259">OPL</span><span class="sxs-lookup"><span data-stu-id="e41b6-259">OPL</span></span></th>
        <th><span data-ttu-id="e41b6-260">Komprimierte digitale Audiodaten</span><span class="sxs-lookup"><span data-stu-id="e41b6-260">Compressed digital audio</span></span></th>
        <th><span data-ttu-id="e41b6-261">Unkomprimierte digitale Audiodaten</span><span class="sxs-lookup"><span data-stu-id="e41b6-261">Uncompressed digital audio</span></span></th>
        <th><span data-ttu-id="e41b6-262">Analog- oder USB-Audio</span><span class="sxs-lookup"><span data-stu-id="e41b6-262">Analog or USB audio</span></span></th>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-263">HDMI, DisplayPort, MHL</span><span class="sxs-lookup"><span data-stu-id="e41b6-263">HDMI, DisplayPort, MHL</span></span></th>
        <th><span data-ttu-id="e41b6-264">HDMI, DisplayPort, MHL</span><span class="sxs-lookup"><span data-stu-id="e41b6-264">HDMI, DisplayPort, MHL</span></span></th>
        <th><span data-ttu-id="e41b6-265">Any</span><span class="sxs-lookup"><span data-stu-id="e41b6-265">Any</span></span></th>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-266">100</span><span class="sxs-lookup"><span data-stu-id="e41b6-266">100</span></span></th>
        <td rowspan="3"><span data-ttu-id="e41b6-267">Inhalt wird übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-267">Passes content</span></span></td>
        <td><span data-ttu-id="e41b6-268">Inhalt wird übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-268">Passes content</span></span></td>
        <td rowspan="5"><span data-ttu-id="e41b6-269">Inhalt wird übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-269">Passes content</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-270">150</span><span class="sxs-lookup"><span data-stu-id="e41b6-270">150</span></span></th>
        <td rowspan="4"><span data-ttu-id="e41b6-271">Inhalt wird NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-271">Does NOT pass content</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-272">200</span><span class="sxs-lookup"><span data-stu-id="e41b6-272">200</span></span></th>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-273">250</span><span class="sxs-lookup"><span data-stu-id="e41b6-273">250</span></span></th>
        <td><span data-ttu-id="e41b6-274">Inhalt wird übergeben, wenn HDCP für HDMI, DisplayPort oder MHL eingebunden wird oder SCMS eingebunden und auf „CopyNever“ festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="e41b6-274">Passes content when HDCP is engaged on HDMI, DisplayPort, or MHL, or when SCMS is engaged and set to CopyNever</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-275">300</span><span class="sxs-lookup"><span data-stu-id="e41b6-275">300</span></span></th>
        <td><span data-ttu-id="e41b6-276">Inhalt wird übergeben, wenn HDCP für HDMI, DisplayPort oder MHL eingebunden wird.</span><span class="sxs-lookup"><span data-stu-id="e41b6-276">Passes content when HDCP is engaged on HDMI, DisplayPort, or MHL</span></span></td>
    </tr>
</table>
<br/>

### <a name="miracast"></a><span data-ttu-id="e41b6-277">Miracast</span><span class="sxs-lookup"><span data-stu-id="e41b6-277">Miracast</span></span>

<span data-ttu-id="e41b6-278">PlayReady DRM ermöglicht die Wiedergabe von Inhalten per Miracast-Ausgabe, sobald HDCP2.0 oder höher eingebunden wird.</span><span class="sxs-lookup"><span data-stu-id="e41b6-278">PlayReady DRM allows you to play content over Miracast output as soon as HDCP 2.0 or later is engaged.</span></span> <span data-ttu-id="e41b6-279">Unter Windows10 gilt Miracast jedoch als *digitale* Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="e41b6-279">On Windows 10, however, Miracast is considered a *digital* output.</span></span> <span data-ttu-id="e41b6-280">Weitere Informationen zu Miracast-Szenarien finden Sie in den [PlayReady-Kompatibilitätsregeln](https://www.microsoft.com/playready/licensing/compliance/).</span><span class="sxs-lookup"><span data-stu-id="e41b6-280">For more information about Miracast scenarios, see the [PlayReady Compliance Rules](https://www.microsoft.com/playready/licensing/compliance/).</span></span> <span data-ttu-id="e41b6-281">Die folgende Tabelle veranschaulicht die Zuordnungen zwischen verschiedenen OPLs in der PlayReady-Lizenz und deren Erzwingung durch PlayReady DRM für Miracast-Ausgaben:</span><span class="sxs-lookup"><span data-stu-id="e41b6-281">The following table outlines the mappings between various OPLs in the PlayReady license and how PlayReady DRM enforces them on Miracast outputs.</span></span>

<table>
    <tr>
        <th><span data-ttu-id="e41b6-282">OPL</span><span class="sxs-lookup"><span data-stu-id="e41b6-282">OPL</span></span></th>
        <th><span data-ttu-id="e41b6-283">Komprimierte digitale Audiodaten</span><span class="sxs-lookup"><span data-stu-id="e41b6-283">Compressed digital audio</span></span></th>
        <th><span data-ttu-id="e41b6-284">Unkomprimierte digitale Audiodaten</span><span class="sxs-lookup"><span data-stu-id="e41b6-284">Uncompressed digital audio</span></span></th>
        <th><span data-ttu-id="e41b6-285">Komprimierte digitale Videos</span><span class="sxs-lookup"><span data-stu-id="e41b6-285">Compressed digital video</span></span></th>
        <th><span data-ttu-id="e41b6-286">Unkomprimierte digitale Videos</span><span class="sxs-lookup"><span data-stu-id="e41b6-286">Uncompressed digital video</span></span></th>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-287">100</span><span class="sxs-lookup"><span data-stu-id="e41b6-287">100</span></span></th>
        <td rowspan="4"><span data-ttu-id="e41b6-288">Inhalt wird übergeben, wenn HDCP2.0 oder höher eingebunden wird.</span><span class="sxs-lookup"><span data-stu-id="e41b6-288">Passes content when HDCP 2.0 or later is engaged.</span></span> <span data-ttu-id="e41b6-289">Wenn die Einbindung nicht erfolgreich ist, wird der Inhalt NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-289">If it fails to engage, it does NOT pass content</span></span></td>
        <td><span data-ttu-id="e41b6-290">Inhalt wird übergeben, wenn HDCP2.0 oder höher eingebunden wird.</span><span class="sxs-lookup"><span data-stu-id="e41b6-290">Passes content when HDCP 2.0 or later is engaged.</span></span> <span data-ttu-id="e41b6-291">Wenn die Einbindung nicht erfolgreich ist, wird der Inhalt NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-291">If it fails to engage, it does NOT pass content</span></span></td>
        <td rowspan="6"><span data-ttu-id="e41b6-292">Nicht zutreffend\*</span><span class="sxs-lookup"><span data-stu-id="e41b6-292">N/A\*</span></span></td>
        <td><span data-ttu-id="e41b6-293">Inhalt wird übergeben, wenn HDCP2.0 oder höher eingebunden wird.</span><span class="sxs-lookup"><span data-stu-id="e41b6-293">Passes content when HDCP 2.0 or later is engaged.</span></span> <span data-ttu-id="e41b6-294">Wenn die Einbindung nicht erfolgreich ist, wird der Inhalt NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-294">If it fails to engage, it does NOT pass content</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-295">150</span><span class="sxs-lookup"><span data-stu-id="e41b6-295">150</span></span></th>
        <td rowspan="3"><span data-ttu-id="e41b6-296">Inhalt wird NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-296">Does NOT pass content</span></span></td>
        <td rowspan="2"><span data-ttu-id="e41b6-297">Nicht zutreffend\*</span><span class="sxs-lookup"><span data-stu-id="e41b6-297">N/A\*</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-298">200</span><span class="sxs-lookup"><span data-stu-id="e41b6-298">200</span></span></th>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-299">250</span><span class="sxs-lookup"><span data-stu-id="e41b6-299">250</span></span></th>
        <td rowspan="2"><span data-ttu-id="e41b6-300">Inhalt wird übergeben, wenn HDCP2.0 oder höher eingebunden wird.</span><span class="sxs-lookup"><span data-stu-id="e41b6-300">Passes content when HDCP 2.0 or later is engaged.</span></span> <span data-ttu-id="e41b6-301">Wenn die Einbindung nicht erfolgreich ist, wird der Inhalt NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-301">If it fails to engage, it does NOT pass content</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-302">270</span><span class="sxs-lookup"><span data-stu-id="e41b6-302">270</span></span></th>
        <td colspan="2"><span data-ttu-id="e41b6-303">Nicht zutreffend\*</span><span class="sxs-lookup"><span data-stu-id="e41b6-303">N/A\*</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-304">300</span><span class="sxs-lookup"><span data-stu-id="e41b6-304">300</span></span></th>
        <td><span data-ttu-id="e41b6-305">Inhalt wird übergeben, wenn HDCP2.0 oder höher eingebunden wird.</span><span class="sxs-lookup"><span data-stu-id="e41b6-305">Passes content when HDCP 2.0 or later is engaged.</span></span> <span data-ttu-id="e41b6-306">Wenn die Einbindung nicht erfolgreich ist, wird der Inhalt NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-306">If it fails to engage, it does NOT pass content</span></span></td>
        <td><span data-ttu-id="e41b6-307">Inhalt wird NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-307">Does NOT pass content</span></span></td>
        <td>
            <p><span data-ttu-id="e41b6-308">
                \*\*Wenn die HDCP-Typeinschränkung NICHT definiert ist:\*\* Inhalt wird übergeben, wenn HDCP2.0 oder höher aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="e41b6-308">
                \*\*When HDCP type restriction is NOT defined:\*\* Passes content when HDCP 2.0 or later is engaged.</span></span> <span data-ttu-id="e41b6-309">Wenn die Einbindung nicht erfolgreich ist, wird der Inhalt NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-309">If it fails to engage, it does NOT pass content.</span></span>
            </p>
            <p><span data-ttu-id="e41b6-310">
                \*\*Wenn die HDCP-Typeinschränkung definiert ist\*\*: Inhalt wird mit HDCP2.2 und Inhaltsdatenstrom-Typ„1“ übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-310">
                \*\*When HDCP type restriction IS defined:\*\* Passes content with HDCP 2.2 and content stream type set to 1.</span></span> <span data-ttu-id="e41b6-311">Wenn die Einbindung von HDCP nicht möglich ist oder der Inhaltsdatenstromtyp nicht auf 1 festgelegt werden kann, wird der Inhalt NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-311">If HDCP fails to engage or content stream type can't be set to 1, it does NOT pass content.</span></span>
            </p>        
        </td>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-312">400</span><span class="sxs-lookup"><span data-stu-id="e41b6-312">400</span></span></th>
        <td rowspan="2" colspan="2"><span data-ttu-id="e41b6-313">Nicht zutreffend\*</span><span class="sxs-lookup"><span data-stu-id="e41b6-313">N/A\*</span></span></td>
        <td rowspan="2"><span data-ttu-id="e41b6-314">Windows10 übergibt komprimierte digitale Videoinhalte niemals an Ausgaben, unabhängig vom nachfolgenden OPL-Wert.</span><span class="sxs-lookup"><span data-stu-id="e41b6-314">Windows 10 never passes compressed digital video content to outputs, regardless of the subsequent OPL value.</span></span> <span data-ttu-id="e41b6-315">Weitere Informationen zu komprimierten digitalen Videoinhalten finden Sie in den <a href="https://www.microsoft.com/playready/licensing/compliance/">Kompatibilitätsregeln für PlayReady-Produkte</a>.</span><span class="sxs-lookup"><span data-stu-id="e41b6-315">For more information about compressed digital video content, see the <a href="https://www.microsoft.com/playready/licensing/compliance/">Compliance Rules for PlayReady Products</a>.</span></span></td>
        <td rowspan="2"><span data-ttu-id="e41b6-316">Nicht zutreffend\*</span><span class="sxs-lookup"><span data-stu-id="e41b6-316">N/A\*</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-317">500</span><span class="sxs-lookup"><span data-stu-id="e41b6-317">500</span></span></th>
    </tr>
</table>
<br/>

<span data-ttu-id="e41b6-318">\* Nicht alle Werte für Ausgabeschutzebenen können von einem Lizenzserver festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="e41b6-318">\* Not all values for output protection levels can be set by a licensing server.</span></span> <span data-ttu-id="e41b6-319">Weitere Informationen finden Sie unter [PlayReady-Kompatibilitätsregeln](https://www.microsoft.com/playready/licensing/compliance/).</span><span class="sxs-lookup"><span data-stu-id="e41b6-319">For more information, see the [PlayReady Compliance Rules](https://www.microsoft.com/playready/licensing/compliance/).</span></span>

### <a name="additional-explicit-output-restrictions"></a><span data-ttu-id="e41b6-320">Zusätzliche explizite Ausgabeeinschränkungen</span><span class="sxs-lookup"><span data-stu-id="e41b6-320">Additional explicit output restrictions</span></span>

<span data-ttu-id="e41b6-321">Die folgende Tabelle beschreibt die Implementierung expliziter Einschränkungen des Ausgabeschutzes für digitale Videos von PlayReady DRM für Windows10:</span><span class="sxs-lookup"><span data-stu-id="e41b6-321">The following table describes the PlayReady DRM for Windows 10 implementation of explicit digital video output protection restrictions.</span></span>

<table>
    <tr>
        <th><span data-ttu-id="e41b6-322">Szenario</span><span class="sxs-lookup"><span data-stu-id="e41b6-322">Scenario</span></span></th>
        <th><span data-ttu-id="e41b6-323">GUID</span><span class="sxs-lookup"><span data-stu-id="e41b6-323">GUID</span></span></th>
        <th><span data-ttu-id="e41b6-324">Situation</span><span class="sxs-lookup"><span data-stu-id="e41b6-324">If...</span></span></th>
        <th><span data-ttu-id="e41b6-325">Folge</span><span class="sxs-lookup"><span data-stu-id="e41b6-325">Then...</span></span></th>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-326">Maximale effektive Auflösung (Decodierungsgröße)</span><span class="sxs-lookup"><span data-stu-id="e41b6-326">Maximum effective resolution decode size</span></span></th>
        <td><span data-ttu-id="e41b6-327">9645E831-E01D-4FFF-8342-0A720E3E028F</span><span class="sxs-lookup"><span data-stu-id="e41b6-327">9645E831-E01D-4FFF-8342-0A720E3E028F</span></span></td>
        <td><span data-ttu-id="e41b6-328">Verbundene Ausgabe: digitale Videoausgabe, Miracast, HDMI, DVI usw.</span><span class="sxs-lookup"><span data-stu-id="e41b6-328">Connected output is: digital video output, Miracast, HDMI, DVI, etc.</span></span></td>
        <td>
            <p>
                <span data-ttu-id="e41b6-329">Inhalt wird übergeben, wenn folgende Einschränkungen vorliegen:</span><span class="sxs-lookup"><span data-stu-id="e41b6-329">Passes content when constrained to:</span></span>  
            </p>
            <ul>
                <li><span data-ttu-id="e41b6-330">(a) Die Breite des Frames muss kleiner oder gleich der maximalen Framebreite (in Pixel) und die Höhe des Frames muss kleiner oder gleich der maximalen Framehöhe (in Pixel) sein. Oder:</span><span class="sxs-lookup"><span data-stu-id="e41b6-330">(a) the width of the frame must be less than or equal to the maximum frame width in pixels and the height of the frame less than or equal to the maximum frame height in pixels, or</span></span></li>
                <li><span data-ttu-id="e41b6-331">(a) Die Höhe des Frames muss kleiner oder gleich der maximalen Framebreite (in Pixel) und die Breite des Frames muss kleiner oder gleich der maximalen Framehöhe (in Pixel) sein.</span><span class="sxs-lookup"><span data-stu-id="e41b6-331">(b) the height of the frame must be less than or equal to the maximum frame width in pixels and the width of the frame less than or equal to the maximum frame height in pixels</span></span></li>
            </ul>                   
        </td>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-332">HDCP-Typeinschränkung</span><span class="sxs-lookup"><span data-stu-id="e41b6-332">HDCP type restriction</span></span></th>
        <td><span data-ttu-id="e41b6-333">ABB2C6F1-E663-4625-A945-972D17B231E7</span><span class="sxs-lookup"><span data-stu-id="e41b6-333">ABB2C6F1-E663-4625-A945-972D17B231E7</span></span></td>
        <td><span data-ttu-id="e41b6-334">Verbundene Ausgabe: digitale Videoausgabe, Miracast, HDMI, DVI usw.</span><span class="sxs-lookup"><span data-stu-id="e41b6-334">Connected output is: digital video output, Miracast, HDMI, DVI, etc.</span></span></td>
        <td><span data-ttu-id="e41b6-335">Inhalt wird mit HDCP2.2 und Inhaltsdatenstrom-Typ „1“ übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-335">Passes content with HDCP 2.2 and the content stream type set to 1.</span></span> <span data-ttu-id="e41b6-336">Sollte die Einbindung von HDCP2.2 nicht möglich sein oder der Inhaltsdatenstrom-Typ nicht auf „1“ festgelegt werden können, wird der Inhalt NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-336">If HDCP 2.2 fails to engage or the content stream type can't be set to 1, it does NOT pass content.</span></span> <span data-ttu-id="e41b6-337">Außerdem muss die Ausgabeschutzebene für unkomprimierte digitale Videos muss mindestens auf271 festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="e41b6-337">Uncompressed digital video output protection level of a value greater than or equal to 271 must also be specified</span></span></td>
    </tr>
</table>
<br/>

<span data-ttu-id="e41b6-338">Die folgende Tabelle beschreibt die Implementierung expliziter Einschränkungen des Ausgabeschutzes für analoge Videos von PlayReady DRM für Windows10.</span><span class="sxs-lookup"><span data-stu-id="e41b6-338">The following table describes the PlayReady DRM for Windows 10 implementation of explicit analog video output protection restrictions.</span></span>

<table>
    <tr>
        <th><span data-ttu-id="e41b6-339">Szenario</span><span class="sxs-lookup"><span data-stu-id="e41b6-339">Scenario</span></span></th>
        <th><span data-ttu-id="e41b6-340">GUID</span><span class="sxs-lookup"><span data-stu-id="e41b6-340">GUID</span></span></th>
        <th><span data-ttu-id="e41b6-341">Situation</span><span class="sxs-lookup"><span data-stu-id="e41b6-341">If...</span></span></th>
        <th colspan="2"><span data-ttu-id="e41b6-342">Folge</span><span class="sxs-lookup"><span data-stu-id="e41b6-342">Then...</span></span></th>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-343">Analoger Computermonitor</span><span class="sxs-lookup"><span data-stu-id="e41b6-343">Analog computer monitor</span></span></th>
        <td><span data-ttu-id="e41b6-344">D783A191-E083-4BAF-B2DA-E69F910B3772</span><span class="sxs-lookup"><span data-stu-id="e41b6-344">D783A191-E083-4BAF-B2DA-E69F910B3772</span></span></td>
        <td><span data-ttu-id="e41b6-345">Verbundene Ausgabe: VGA, DVI&ndash;analog usw.</span><span class="sxs-lookup"><span data-stu-id="e41b6-345">Connected output is: VGA, DVI&ndash;analog, etc.</span></span></td>
        <td><span data-ttu-id="e41b6-346"><b>SWDRM:</b> Der PC schränkt die effektive Auflösung auf 520.000epx pro Frame ein und übergibt den Inhalt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-346"><b>SWDRM:</b> PC will constrain effective resolution to 520,000 epx per frame and pass content</span></span></td>
        <td><span data-ttu-id="e41b6-347"><b>HWDRM:</b> Inhalt wird NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-347"><b>HWDRM:</b> Does NOT pass content</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-348">Analoge Komponente</span><span class="sxs-lookup"><span data-stu-id="e41b6-348">Analog component</span></span></th>
        <td><span data-ttu-id="e41b6-349">811C5110-46C8-4C6E-8163-C0482A15D47E</span><span class="sxs-lookup"><span data-stu-id="e41b6-349">811C5110-46C8-4C6E-8163-C0482A15D47E</span></span></td>
        <td><span data-ttu-id="e41b6-350">Verbundene Ausgabe: Komponente</span><span class="sxs-lookup"><span data-stu-id="e41b6-350">Connected output is: component</span></span></td>
        <td><span data-ttu-id="e41b6-351"><b>SWDRM:</b> Der PC schränkt die effektive Auflösung auf 520.000epx pro Frame ein und übergibt den Inhalt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-351"><b>SWDRM:</b> PC will constrain effective resolution to 520,000 epx per frame and pass content</span></span></td>
        <td><span data-ttu-id="e41b6-352"><b>HWDRM:</b> Inhalt wird NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-352"><b>HWDRM:</b> Does NOT pass content</span></span></td>
    </tr>
    <tr>
        <th rowspan="2"><span data-ttu-id="e41b6-353">Analoge TV-Ausgaben</span><span class="sxs-lookup"><span data-stu-id="e41b6-353">Analog TV outputs</span></span></th>
        <td><span data-ttu-id="e41b6-354">2098DE8D-7DDD-4BAB-96C6-32EBB6FABEA3</span><span class="sxs-lookup"><span data-stu-id="e41b6-354">2098DE8D-7DDD-4BAB-96C6-32EBB6FABEA3</span></span></td>
        <td><span data-ttu-id="e41b6-355">OPL für Analog-TV ist kleiner als151.</span><span class="sxs-lookup"><span data-stu-id="e41b6-355">Analog TV OPL is less than 151</span></span></td>
        <td colspan="2"><span data-ttu-id="e41b6-356">CGMS-A muss eingebunden werden.</span><span class="sxs-lookup"><span data-stu-id="e41b6-356">CGMS-A must be engaged</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="e41b6-357">225CD36F-F132-49EF-BA8C-C91EA28E4369</span><span class="sxs-lookup"><span data-stu-id="e41b6-357">225CD36F-F132-49EF-BA8C-C91EA28E4369</span></span></td>
        <td><span data-ttu-id="e41b6-358">OPL für Analog-TV ist kleiner als101, und „2098DE8D-7DDD-4BAB-96C6-32EBB6FABEA3“ ist nicht in der Lizenz enthalten.</span><span class="sxs-lookup"><span data-stu-id="e41b6-358">Analog TV OPL is less than 101 and license doesn't contain 2098DE8D-7DDD-4BAB-96C6-32EBB6FABEA3</span></span></td>
        <td colspan="2"><span data-ttu-id="e41b6-359">Einbindung von CGMS-A muss versucht werden, der Inhalt kann jedoch unabhängig vom Ergebnis wiedergegeben werden.</span><span class="sxs-lookup"><span data-stu-id="e41b6-359">CGMS-A engagement must be attempted, but content may play regardless of result</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-360">Automatische Verstärkungsregelung und Farbstreifen</span><span class="sxs-lookup"><span data-stu-id="e41b6-360">Automatic gain control and color stripe</span></span></th>
        <td><span data-ttu-id="e41b6-361">C3FD11C6-F8B7-4D20-B008-1DB17D61F2DA</span><span class="sxs-lookup"><span data-stu-id="e41b6-361">C3FD11C6-F8B7-4D20-B008-1DB17D61F2DA</span></span></td>
        <td><span data-ttu-id="e41b6-362">Inhalt wird mit einer Auflösung von maximal 520.000Pixeln an eine analoge TV-Ausgabe übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-362">Passing content with resolution less than or equal to 520,000 px to analog TV output</span></span></td>
        <td colspan="2"><span data-ttu-id="e41b6-363">Die automatische Verstärkungsregelung wird nur für Komponentenvideos und den PAL-Modus festgelegt, wenn die Auflösung weniger als 520.000Pixel beträgt. Automatische Verstärkungsregelung und Farbstreifeninformationen für NTSC werden festgelegt, wenn die Auflösung weniger als 520.000Pixel beträgt (siehe Tabelle3.5.7.3.</span><span class="sxs-lookup"><span data-stu-id="e41b6-363">Sets AGC only for component video and PAL mode when resolution is less than 520,000 px and sets AGC and color stripe information for NTSC when resolution is less than 520,000 px, according to table 3.5.7.3.</span></span> <span data-ttu-id="e41b6-364">in den Kompatibilitätsregeln).</span><span class="sxs-lookup"><span data-stu-id="e41b6-364">in Compliance Rules</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-365">Nur digitale Ausgabe</span><span class="sxs-lookup"><span data-stu-id="e41b6-365">Digital-only output</span></span></th>
        <td><span data-ttu-id="e41b6-366">760AE755-682A-41E0-B1B3-DCDF836A7306</span><span class="sxs-lookup"><span data-stu-id="e41b6-366">760AE755-682A-41E0-B1B3-DCDF836A7306</span></span></td>
        <td><span data-ttu-id="e41b6-367">Die verbundene Ausgabe ist analog.</span><span class="sxs-lookup"><span data-stu-id="e41b6-367">Connected output is analog</span></span></td>
        <td colspan="2"><span data-ttu-id="e41b6-368">Inhalt wird nicht übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-368">Does not pass content</span></span></td>
    </tr>
</table>
<br/>

> [!NOTE]
> <span data-ttu-id="e41b6-369">Wenn für die Wiedergabe ein Adapterdongle wie Mini-DisplayPort auf VGA verwendet wird, wird die Ausgabe von Windows10 als digitale Videoausgabe betrachtet, sodass keine Richtlinien für analoge Videos durchgesetzt werden können.</span><span class="sxs-lookup"><span data-stu-id="e41b6-369">When using an adapter dongle such as "Mini DisplayPort to VGA" for playback, Windows 10 sees the output as digital video output, and can't enforce analog video policies.</span></span>

<span data-ttu-id="e41b6-370">Die folgende Tabelle beschreibt die Implementierung von PlayReady DRM für Windows10 für die Wiedergabe in anderen Fällen:</span><span class="sxs-lookup"><span data-stu-id="e41b6-370">The following table describes the PlayReady DRM for Windows 10 implementation that enables playing in other circumstances.</span></span>

<table>
    <tr>
        <th><span data-ttu-id="e41b6-371">Szenario</span><span class="sxs-lookup"><span data-stu-id="e41b6-371">Scenario</span></span></th>
        <th><span data-ttu-id="e41b6-372">GUID</span><span class="sxs-lookup"><span data-stu-id="e41b6-372">GUID</span></span></th>
        <th><span data-ttu-id="e41b6-373">Situation</span><span class="sxs-lookup"><span data-stu-id="e41b6-373">If...</span></span></th>
        <th colspan="2"><span data-ttu-id="e41b6-374">Folge</span><span class="sxs-lookup"><span data-stu-id="e41b6-374">Then...</span></span></th>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-375">Unbekannte Ausgabe</span><span class="sxs-lookup"><span data-stu-id="e41b6-375">Unknown output</span></span></th>
        <td><span data-ttu-id="e41b6-376">786627D8-C2A6-44BE-8F88-08AE255B01A7</span><span class="sxs-lookup"><span data-stu-id="e41b6-376">786627D8-C2A6-44BE-8F88-08AE255B01A7</span></span></td>
        <td><span data-ttu-id="e41b6-377">Die Ausgabe kann nicht vernünftig ermittelt werden, oder für den Grafiktreiber ist kein OPM möglich.</span><span class="sxs-lookup"><span data-stu-id="e41b6-377">If output can't reasonably be determined, or OPM can't be established with graphics driver</span></span></td>
        <td><span data-ttu-id="e41b6-378"><b>SWDRM:</b> Inhalt wird übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-378"><b>SWDRM:</b> Passes content</span></span></td>
        <td><span data-ttu-id="e41b6-379"><b>HWDRM:</b> Inhalt wird NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-379"><b>HWDRM:</b> Does NOT pass content</span></span></td>
    </tr>
    <tr>
        <th><span data-ttu-id="e41b6-380">Unbekannte Ausgabe mit Einschränkung</span><span class="sxs-lookup"><span data-stu-id="e41b6-380">Unknown output with constriction</span></span></th>
        <td><span data-ttu-id="e41b6-381">B621D91F-EDCC-4035-8D4B-DC71760D43E9</span><span class="sxs-lookup"><span data-stu-id="e41b6-381">B621D91F-EDCC-4035-8D4B-DC71760D43E9</span></span></td>
        <td><span data-ttu-id="e41b6-382">Die Ausgabe kann nicht vernünftig ermittelt werden, oder für den Grafiktreiber ist kein OPM möglich.</span><span class="sxs-lookup"><span data-stu-id="e41b6-382">If output can't reasonably be determined, or OPM can't be established with graphics driver</span></span></td>
        <td><span data-ttu-id="e41b6-383"><b>SWDRM:</b> Der PC schränkt die effektive Auflösung auf 520.000epx pro Frame ein und übergibt den Inhalt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-383"><b>SWDRM:</b> PC will constrain effective resolution to 520,000 epx per frame and pass content</span></span></td>
        <td><span data-ttu-id="e41b6-384"><b>HWDRM:</b> Inhalt wird NICHT übergeben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-384"><b>HWDRM:</b> Does NOT pass content</span></span></td>
    </tr>
</table>
<br/>

## <a name="prerequisites"></a><span data-ttu-id="e41b6-385">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="e41b6-385">Prerequisites</span></span>

<span data-ttu-id="e41b6-386">Bevor Sie mit der Erstellung Ihrer PlayReady-geschützten UWP-App beginnen, müssen Sie die folgende Software auf Ihrem System installieren:</span><span class="sxs-lookup"><span data-stu-id="e41b6-386">Before you begin creating your PlayReady-protected UWP app, the following software needs to be installed on your system:</span></span>

-   <span data-ttu-id="e41b6-387">Windows 10.</span><span class="sxs-lookup"><span data-stu-id="e41b6-387">Windows10.</span></span>
-   <span data-ttu-id="e41b6-388">Wenn Sie die Beispiele für PlayReady DRM für UWP-apps kompilieren, müssen Sie Microsoft Visual Studio2015 verwenden oder höher zum Kompilieren der Beispiele.</span><span class="sxs-lookup"><span data-stu-id="e41b6-388">If you are compiling any of the samples for PlayReady DRM for UWP apps, you must use Microsoft Visual Studio2015 or later to compile the samples.</span></span> <span data-ttu-id="e41b6-389">Sie können Microsoft Visual Studio2013 weiterhin zum Kompilieren der Beispiele aus PlayReady DRM für Windows8.1 Store-Apps verwenden.</span><span class="sxs-lookup"><span data-stu-id="e41b6-389">You can still use Microsoft Visual Studio2013 to compile any of the samples from PlayReady DRM for Windows8.1 Store Apps.</span></span>

<!--This is no longer available-->
<!--If you are planning to play back MPEG-2/H.262 content on your app, you must also download and install [Windows 8.1 Media Center Pack](http://go.microsoft.com/fwlink/p/?LinkId=626876).-->

## <a name="playready-uwp-app-migration-guide"></a><span data-ttu-id="e41b6-390">Migrationshandbuch für UWP-Apps mit PlayReady</span><span class="sxs-lookup"><span data-stu-id="e41b6-390">PlayReady UWP app migration guide</span></span>

<span data-ttu-id="e41b6-391">Dieser Abschnitt enthält Informationen zum Migrieren Ihrer vorhandenen PlayReady Windows 8.x-Store-apps zu Windows 10.</span><span class="sxs-lookup"><span data-stu-id="e41b6-391">This section includes information on how to migrate your existing PlayReady Windows 8.x Store apps to Windows10.</span></span>

<span data-ttu-id="e41b6-392">Der Namespace für PlayReady-UWP-apps unter Windows 10 wurde von **Microsoft.Media.PlayReadyClient** in [**Windows.Media.Protection.PlayReady**](https://msdn.microsoft.com/library/windows/apps/dn986454)geändert.</span><span class="sxs-lookup"><span data-stu-id="e41b6-392">The namespace for PlayReady UWP apps on Windows10 was changed from **Microsoft.Media.PlayReadyClient** to [**Windows.Media.Protection.PlayReady**](https://msdn.microsoft.com/library/windows/apps/dn986454).</span></span> <span data-ttu-id="e41b6-393">Sie müssen also in Ihrem Code den alten Namespace suchen und durch den neuen Namespace ersetzen.</span><span class="sxs-lookup"><span data-stu-id="e41b6-393">This means that you will need to search and replace the old namespace with the new one in your code.</span></span> <span data-ttu-id="e41b6-394">Sie verweisen weiterhin auf eine WINMD-Datei.</span><span class="sxs-lookup"><span data-stu-id="e41b6-394">You will still be referencing a winmd file.</span></span> <span data-ttu-id="e41b6-395">Es ist Teil des windows.media.winmd des Betriebssystems Windows 10.</span><span class="sxs-lookup"><span data-stu-id="e41b6-395">It is part of windows.media.winmd on the Windows10 operating system.</span></span> <span data-ttu-id="e41b6-396">Sie ist in „windows.winmd“ als Teil des TH WindowsSDK enthalten.</span><span class="sxs-lookup"><span data-stu-id="e41b6-396">It is in windows.winmd as part of the TH’s Windows SDK.</span></span> <span data-ttu-id="e41b6-397">Bei UWP wird darauf in „windows.foundation.univeralappcontract.winmd“ verwiesen.</span><span class="sxs-lookup"><span data-stu-id="e41b6-397">For UWP, it’s referenced in windows.foundation.univeralappcontract.winmd.</span></span>

<span data-ttu-id="e41b6-398">Zum Wiedergeben von PlayReady-geschützten High-Definition (HD)-Inhalten (1080p) und Ultra-High-Definition (UHD)-Inhalten müssen Sie das Hardware-DRM mit PlayReady implementieren.</span><span class="sxs-lookup"><span data-stu-id="e41b6-398">To play back PlayReady-protected high definition (HD) content (1080p) and ultra-high definition (UHD) content, you will need to implement PlayReady hardware DRM.</span></span> <span data-ttu-id="e41b6-399">Informationen zum Implementieren des Hardware-DRM mit PlayReady finden Sie unter [Hardware-DRM](hardware-drm.md).</span><span class="sxs-lookup"><span data-stu-id="e41b6-399">For information on how to implement PlayReady hardware DRM, see [Hardware DRM](hardware-drm.md).</span></span>

<span data-ttu-id="e41b6-400">Manche Inhalte werden nicht vom Hardware-DRM unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-400">Some content is not supported in hardware DRM.</span></span> <span data-ttu-id="e41b6-401">Informationen zum Deaktivieren des Hardware-DRM und Aktivieren des Software-DRM finden Sie unter [Außerkraftsetzen des Hardware-DRM](hardware-drm.md#override-hardware-drm).</span><span class="sxs-lookup"><span data-stu-id="e41b6-401">For information on disabling hardware DRM and enabling software DRM, see [Override Hardware DRM](hardware-drm.md#override-hardware-drm).</span></span>

<span data-ttu-id="e41b6-402">Stellen Sie im Medienschutz-Manager sicher, dass für Ihren Code die folgenden Einstellungen festgelegt sind (sofern noch nicht geschehen):</span><span class="sxs-lookup"><span data-stu-id="e41b6-402">Regarding the media protection manager, make sure your code has the following settings if it doesn’t already:</span></span>

```cs
var mediaProtectionManager = new Windows.Media.Protection.MediaProtectionManager();

mediaProtectionManager.Properties["Windows.Media.Protection.MediaProtectionSystemId"] = 
             '{F4637010-03C3-42CD-B932-B48ADF3A6A54}'
var cpsystems = new Windows.Foundation.Collections.PropertySet();
cpsystems["{F4637010-03C3-42CD-B932-B48ADF3A6A54}"] = 
                "Windows.Media.Protection.PlayReady.PlayReadyWinRTTrustedInput";
mediaProtectionManager.Properties["Windows.Media.Protection.MediaProtectionSystemIdMapping"] = cpsystems;

mediaProtectionManager.Properties["Windows.Media.Protection.MediaProtectionContainerGuid"] = 
                "{9A04F079-9840-4286-AB92-E65BE0885F95}";
```

## <a name="proactively-acquire-a-non-persistent-license-before-playback"></a><span data-ttu-id="e41b6-403">Proaktives Abrufen einer nicht persistenten Lizenz vor der Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="e41b6-403">Proactively acquire a non-persistent license before playback</span></span>

<span data-ttu-id="e41b6-404">In diesem Abschnitt wird beschrieben, wie Sie vor dem Start der Wiedergabe proaktiv nicht persistente Lizenzen abrufen.</span><span class="sxs-lookup"><span data-stu-id="e41b6-404">This section describes how to acquire non-persistent licenses proactively before playback begins.</span></span>

<span data-ttu-id="e41b6-405">In früheren Versionen von PlayReady DRM konnten nicht persistente Lizenzen nur reaktiv während der Wiedergabe abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="e41b6-405">In previous versions of PlayReady DRM, non-persistent licenses could only be acquired reactively during playback.</span></span> <span data-ttu-id="e41b6-406">In dieser Version können Sie nicht persistente Lizenzen proaktiv abrufen, bevor die Wiedergabe beginnt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-406">In this version, you can acquire non-persistent licenses proactively before playback begins.</span></span>

1.  <span data-ttu-id="e41b6-407">Erstellen Sie proaktiv eine Wiedergabesitzung, in der die nicht persistente Lizenz gespeichert werden kann.</span><span class="sxs-lookup"><span data-stu-id="e41b6-407">Proactively create a playback session where the non-persistent license can be stored.</span></span> <span data-ttu-id="e41b6-408">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="e41b6-408">For example:</span></span>

    ```cs
    var cpsystems = new Windows.Foundation.Collections.PropertySet();       
    cpsystems["{F4637010-03C3-42CD-B932-B48ADF3A6A54}"] = "Windows.Media.Protection.PlayReady.PlayReadyWinRTTrustedInput"; // PlayReady

    var pmpSystemInfo = new Windows.Foundation.Collections.PropertySet();
    pmpSystemInfo["Windows.Media.Protection.MediaProtectionSystemId"] = "{F4637010-03C3-42CD-B932-B48ADF3A6A54}";
    pmpSystemInfo["Windows.Media.Protection.MediaProtectionSystemIdMapping"] = cpsystems;
    var pmpServer = new Windows.Media.Protection.MediaProtectionPMPServer( pmpSystemInfo );
    ```

2.  <span data-ttu-id="e41b6-409">Binden Sie die Wiedergabesitzung an die Lizenzabrufklasse.</span><span class="sxs-lookup"><span data-stu-id="e41b6-409">Tie that playback session to the license acquisition class.</span></span> <span data-ttu-id="e41b6-410">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="e41b6-410">For example:</span></span>

    ```cs
    var licenseSessionProperties = new Windows.Foundation.Collections.PropertySet();
    licenseSessionProperties["Windows.Media.Protection.MediaProtectionPMPServer"] = pmpServer;
    var licenseSession = new Windows.Media.Protection.PlayReady.PlayReadyLicenseSession( licenseSessionProperties );
    ```

3.  <span data-ttu-id="e41b6-411">Erstellen Sie eine Lizenzserviceanfrage.</span><span class="sxs-lookup"><span data-stu-id="e41b6-411">Create a license service request.</span></span> <span data-ttu-id="e41b6-412">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="e41b6-412">For example:</span></span>

    ```cs
    var laSR = licenseSession.CreateLAServiceRequest();
    ```

4.  <span data-ttu-id="e41b6-413">Führen Sie den Lizenzerwerb mit der Serviceanfrage aus, die Sie in Schritt 3 erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="e41b6-413">Perform the license acquisition using the service request created from step 3.</span></span> <span data-ttu-id="e41b6-414">Die Lizenz wird in der Wiedergabesitzung gespeichert.</span><span class="sxs-lookup"><span data-stu-id="e41b6-414">The license will be stored in the playback session.</span></span>
5.  <span data-ttu-id="e41b6-415">Binden Sie die Wiedergabesitzung an die Medienquelle für die Wiedergabe.</span><span class="sxs-lookup"><span data-stu-id="e41b6-415">Tie the playback session to the media source for playback.</span></span> <span data-ttu-id="e41b6-416">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="e41b6-416">For example:</span></span>

    ```cs
    licenseSession.configureMediaProtectionManager( mediaProtectionManager );
    videoPlayer.msSetMediaProtectionManager( mediaProtectionManager );
    ```
    
## <a name="query-for-protection-capabilities"></a><span data-ttu-id="e41b6-417">Abfrage der Schutzmöglichkeiten</span><span class="sxs-lookup"><span data-stu-id="e41b6-417">Query for protection capabilities</span></span>
<span data-ttu-id="e41b6-418">Ab Windows10, Version 1703, können Sie Hardware-DRM-Funktionen abfragen, z.B. für Decodierung, Auflösung und Ausgabeschutz (HDCP).</span><span class="sxs-lookup"><span data-stu-id="e41b6-418">Starting with Windows 10, version 1703, you can query HW DRM capabilities, such as decode codecs, resolution, and output protections (HDCP).</span></span> <span data-ttu-id="e41b6-419">Abfragen erfolgen mit der Methode [**IsTypeSupported**](https://docs.microsoft.com/uwp/api/windows.media.protection.protectioncapabilities.istypesupported). Diese erwartet eine Zeichenfolge, welche die Funktionen angibt, nach deren Unterstützung gefragt wird, und eine Zeichenfolge, die das Schlüsselsystem angibt, für das die Abfrage gilt.</span><span class="sxs-lookup"><span data-stu-id="e41b6-419">Queries are performed with the [**IsTypeSupported**](https://docs.microsoft.com/uwp/api/windows.media.protection.protectioncapabilities.istypesupported) method which takes a string representing the capabilities for which support is queried and a string specifying the key system to which the query applies.</span></span> <span data-ttu-id="e41b6-420">Eine Liste der unterstützten Zeichenfolgenwerte finden Sie auf der API-Referenzseite für [**IsTypeSupported**](https://docs.microsoft.com/uwp/api/windows.media.protection.protectioncapabilities.istypesupported).</span><span class="sxs-lookup"><span data-stu-id="e41b6-420">For a list of supported string values, see the API reference page for [**IsTypeSupported**](https://docs.microsoft.com/uwp/api/windows.media.protection.protectioncapabilities.istypesupported).</span></span> <span data-ttu-id="e41b6-421">Das folgende Codebeispiel veranschaulicht die Verwendung dieser Methode.</span><span class="sxs-lookup"><span data-stu-id="e41b6-421">The following code example illustrates the usage of this method.</span></span>  

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
## <a name="add-secure-stop"></a><span data-ttu-id="e41b6-422">Hinzufügen des sicheren Beendens</span><span class="sxs-lookup"><span data-stu-id="e41b6-422">Add secure stop</span></span>

<span data-ttu-id="e41b6-423">In diesem Abschnitt wird beschrieben, wie Sie Ihrer UWP-App die Funktion für sicheres Beenden hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e41b6-423">This section describes how to add secure stop to your UWP app.</span></span>

<span data-ttu-id="e41b6-424">Dank des sicheren Beendens kann ein PlayReady-Gerät einem Medienstreamingdienst zuverlässig bestätigen, dass die Medienwiedergabe für einen bestimmten Inhalt beendet wurde.</span><span class="sxs-lookup"><span data-stu-id="e41b6-424">Secure stop provides the means for a PlayReady device to confidently assert to a media streaming service that media playback has stopped for any given piece of content.</span></span> <span data-ttu-id="e41b6-425">Mit dieser Funktion wird sichergestellt, dass Ihre Medienstreamingdienste präzise Erzwingung und Berichte zu Nutzungseinschränkungen auf verschiedenen Geräten für ein bestimmtes Konto bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="e41b6-425">This capability ensures your media streaming services provide accurate enforcement and reporting of usage limitations on different devices for a given account.</span></span>

<span data-ttu-id="e41b6-426">Es gibt zwei primäre Szenarien für das Senden einer Abfrage für sicheres Beenden:</span><span class="sxs-lookup"><span data-stu-id="e41b6-426">There are two primary scenarios for sending a secure stop challenge:</span></span>

-   <span data-ttu-id="e41b6-427">Wenn die Mediendarstellung beendet wird, weil das Ende des Inhalts erreicht wurde, oder wenn die Mediendarstellung vor ihrem Ende vom Benutzer beendet wurde.</span><span class="sxs-lookup"><span data-stu-id="e41b6-427">When the media presentation stops because end of content was reached or when the user stopped the media presentation somewhere in the middle.</span></span>
-   <span data-ttu-id="e41b6-428">Wenn die vorherige Sitzung unerwartet beendet wurde (z.B. aufgrund eines System- oder App-Absturzes).</span><span class="sxs-lookup"><span data-stu-id="e41b6-428">When the previous session ends unexpectedly (for example, due to a system or app crash).</span></span> <span data-ttu-id="e41b6-429">Die App muss beim Starten oder Herunterfahren alle ausstehenden Sitzungen für sicheres Beenden abfragen und von anderen Medienwiedergaben getrennte Abfragen senden.</span><span class="sxs-lookup"><span data-stu-id="e41b6-429">The app will need to query, either at startup or shutdown, for any outstanding secure stop sessions and send challenge(s) separate from any other media playback.</span></span>

<span data-ttu-id="e41b6-430">Eine Beispielimplementierung für das sichere Beenden finden Sie in der Datei „securestop.cs” im PlayReady-Beispiel unter [http://go.microsoft.com/fwlink/p/?linkid=331670&clcid=0x409](http://go.microsoft.com/fwlink/p/?linkid=331670).</span><span class="sxs-lookup"><span data-stu-id="e41b6-430">For a sample implementation of secure stop, see the securestop.cs file in the PlayReady sample located at [http://go.microsoft.com/fwlink/p/?linkid=331670&clcid=0x409](http://go.microsoft.com/fwlink/p/?linkid=331670).</span></span>

## <a name="use-playready-drm-on-xbox-one"></a><span data-ttu-id="e41b6-431">Verwenden von PlayReady DRM auf Xbox One</span><span class="sxs-lookup"><span data-stu-id="e41b6-431">Use PlayReady DRM on Xbox One</span></span>

<span data-ttu-id="e41b6-432">Um PlayReady-DRM in einer UWP-App auf Xbox One zu verwenden, müssen Sie zunächst das Dev Center-Konto, das Sie zum Veröffentlichen der App verwenden, für die Autorisierung zur PlayReady-Verwendung registrieren.</span><span class="sxs-lookup"><span data-stu-id="e41b6-432">To use PlayReady DRM in a UWP app on Xbox One, you will first need to register your Dev Center account that you're using to publish the app for authorization to use PlayReady.</span></span> <span data-ttu-id="e41b6-433">Hierzu stehen Ihnen zwei Möglichkeiten zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="e41b6-433">You can do this in one of two ways:</span></span>

* <span data-ttu-id="e41b6-434">Ihr Microsoft-Kontakt kann die Berechtigung anfordern.</span><span class="sxs-lookup"><span data-stu-id="e41b6-434">Have your contact at Microsoft request permission.</span></span>
* <span data-ttu-id="e41b6-435">Fordern Sie die Autorisierung an, indem Sie Ihr Dev Center-Konto und den Unternehmensnamen an [pronxbox@microsoft.com](mailto:pronxbox@microsoft.com) senden.</span><span class="sxs-lookup"><span data-stu-id="e41b6-435">Apply for authorization by sending your Dev Center account and company name to [pronxbox@microsoft.com](mailto:pronxbox@microsoft.com).</span></span>

<span data-ttu-id="e41b6-436">Wenn Sie die Autorisierung erhalten haben, müssen Sie dem App-Manifest eine zusätzliche `<DeviceCapability>` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e41b6-436">Once you receive authorization, you'll need to add an additional `<DeviceCapability>` to the app manifest.</span></span> <span data-ttu-id="e41b6-437">Sie müssen diese manuell hinzufügen, da derzeit im App Manifest Designer keine Einstellung verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="e41b6-437">You'll have to add this manually because there is currently no setting available in the App Manifest Designer.</span></span> <span data-ttu-id="e41b6-438">Führen Sie folgende Schritte durch, um dies zu konfigurieren:</span><span class="sxs-lookup"><span data-stu-id="e41b6-438">Follow these steps to configure it:</span></span>

1. <span data-ttu-id="e41b6-439">Öffnen Sie das Projekt in Visual Studio, öffnen Sie den **Solution Explorer**, und klicken Sie mit der rechten Maustaste auf **Package.appxmanifest**.</span><span class="sxs-lookup"><span data-stu-id="e41b6-439">With the project open in Visual Studio, open the **Solution Explorer** and right-click **Package.appxmanifest**.</span></span>
2. <span data-ttu-id="e41b6-440">Wählen Sie \*\*Öffnen mit... \*\* und anschließend **XML (Text) Editor**, und klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="e41b6-440">Select **Open With...**, choose **XML (Text) Editor**, and click **OK**.</span></span>
3. <span data-ttu-id="e41b6-441">Fügen Sie zwischen den `<Capabilities>`-Tags die folgende `<DeviceCapability>` ein:</span><span class="sxs-lookup"><span data-stu-id="e41b6-441">Between the `<Capabilities>` tags, add the following `<DeviceCapability>`:</span></span>

    ```xml
    <DeviceCapability Name="6a7e5907-885c-4bcb-b40a-073c067bd3d5" />
    ```

4. <span data-ttu-id="e41b6-442">Speichern Sie die Datei.</span><span class="sxs-lookup"><span data-stu-id="e41b6-442">Save the file.</span></span>

<span data-ttu-id="e41b6-443">Beachten Sie bei der Verwendung von PlayReady auf Xbox One jedoch auch Folgendes: Auf Entwicklungskits besteht eine SL150-Beschränkung (d.h. SL2000- oder SL3000-Inhalte können nicht wiedergegeben werden).</span><span class="sxs-lookup"><span data-stu-id="e41b6-443">Finally, there is one last consideration when using PlayReady on Xbox One: on development kits, there is an SL150 limit (that is, they can't play SL2000 or SL3000 content).</span></span> <span data-ttu-id="e41b6-444">Einzelhandelsgeräte können Inhalte mit höheren Sicherheitsebenen wiedergeben. Sie müssen jedoch SL150-Inhalte verwenden, um Ihre App in einem Entwicklungskit zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="e41b6-444">Retail devices are able to play content with higher security levels, but to test your app on a dev kit, you'll need to use SL150 content.</span></span> <span data-ttu-id="e41b6-445">Zum Testen dieser Inhalte stehen Ihnen folgende Möglichkeiten zur Verfügung:</span><span class="sxs-lookup"><span data-stu-id="e41b6-445">You can test this content in one of the following ways:</span></span>

* <span data-ttu-id="e41b6-446">Verwenden Sie speziell zusammengestellte Testinhalte, die SL150-Lizenzen erfordern.</span><span class="sxs-lookup"><span data-stu-id="e41b6-446">Use curated test content that requires SL150 licenses.</span></span>
* <span data-ttu-id="e41b6-447">Implementieren Sie eine Logik, sodass nur bestimmte authentifizierte Testkonten SL150-Lizenzen für bestimmte Inhalte erhalten können.</span><span class="sxs-lookup"><span data-stu-id="e41b6-447">Implement logic so that only certain authenticated test accounts are able to acquire SL150 licenses for certain content.</span></span>

<span data-ttu-id="e41b6-448">Gehen Sie so vor, wie es für Ihr Unternehmen und Ihr Produkt am praktischsten ist.</span><span class="sxs-lookup"><span data-stu-id="e41b6-448">Use the approach that makes the most sense for your company and your product.</span></span>


## <a name="see-also"></a><span data-ttu-id="e41b6-449">Weitere Informationen finden Sie unter</span><span class="sxs-lookup"><span data-stu-id="e41b6-449">See also</span></span>
- [<span data-ttu-id="e41b6-450">Medienwiedergabe</span><span class="sxs-lookup"><span data-stu-id="e41b6-450">Media playback</span></span>](media-playback.md)




