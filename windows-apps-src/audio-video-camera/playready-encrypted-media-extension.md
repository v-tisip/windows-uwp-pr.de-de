---
author: drewbatgit
ms.assetid: 79C284CA-C53A-4C24-807E-6D4CE1A29BFA
description: In diesem Abschnitt wird beschrieben, wie Sie Ihre Web-App mit PlayReady ändern, um die Änderungen zu unterstützen, die gegenüber der Windows 8.1-Version in der Version für Windows 10 vorgenommen wurden.
title: Verschlüsselte Medienerweiterung von PlayReady
ms.author: drewbat
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: a8cc35115b2805b2191424edca671c53c252c549
ms.sourcegitcommit: cd9b4bdc9c3a0b537a6e910a15df8541b49abf9c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2017
ms.locfileid: "907152"
---
# <a name="playready-encrypted-media-extension"></a><span data-ttu-id="735ec-104">Verschlüsselte Medienerweiterung von PlayReady</span><span class="sxs-lookup"><span data-stu-id="735ec-104">PlayReady Encrypted Media Extension</span></span>

<span data-ttu-id="735ec-105">\[ Aktualisiert für UWP-Apps unter Windows 10.</span><span class="sxs-lookup"><span data-stu-id="735ec-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="735ec-106">Artikel zu Windows 8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \].</span><span class="sxs-lookup"><span data-stu-id="735ec-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>


<span data-ttu-id="735ec-107">In diesem Abschnitt wird beschrieben, wie Sie Ihre Web-App mit PlayReady ändern, um die Änderungen zu unterstützen, die gegenüber der Windows 8.1-Version in der Version für Windows 10 vorgenommen wurden.</span><span class="sxs-lookup"><span data-stu-id="735ec-107">This section describes how to modify your PlayReady web app to support the changes made from the previous Windows 8.1 version to the Windows 10 version.</span></span>

<span data-ttu-id="735ec-108">Die Verwendung von PlayReady-Medienelementen in Internet Explorer ermöglicht Entwicklern das Erstellen von Web-Apps, die PlayReady-geschützte Inhalte für den Benutzer bereitstellen und gleichzeitig vom Inhaltsanbieter definierte Regeln erzwingen können.</span><span class="sxs-lookup"><span data-stu-id="735ec-108">Using PlayReady media elements in Internet Explorer enables developers to create web apps capable of providing PlayReady content to the user while enforcing the access rules defined by the content provider.</span></span> <span data-ttu-id="735ec-109">In diesem Abschnitt wird beschrieben, wie Sie Ihren vorhandenen Web-Apps PlayReady-Medienelemente hinzufügen, indem Sie nur HTML5 und JavaScript verwenden.</span><span class="sxs-lookup"><span data-stu-id="735ec-109">This section describes how to add PlayReady media elements to your existing web apps by using only HTML5 and JavaScript.</span></span>

## <a name="whats-new-in-playready-encrypted-media-extension"></a><span data-ttu-id="735ec-110">Neuigkeiten in der verschlüsselten Medienerweiterung von PlayReady</span><span class="sxs-lookup"><span data-stu-id="735ec-110">What's new in PlayReady Encrypted Media Extension</span></span>

<span data-ttu-id="735ec-111">Dieser Abschnitt enthält eine Liste der Änderungen, die an der verschlüsselten Medienerweiterung (EME) von PlayReady vorgenommen wurden, um PlayReady-Inhaltsschutz unter Windows 10 bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="735ec-111">This section provides a list of changes made to the PlayReady Encrypted Media Extension (EME) to enable PlayReady content protection on Windows 10.</span></span>

<span data-ttu-id="735ec-112">In der folgenden Liste werden die neuen Features und Änderungen der verschlüsselten Medienerweiterung von PlayReady unter Windows 10 beschrieben:</span><span class="sxs-lookup"><span data-stu-id="735ec-112">The following list describes the new features and changes made to PlayReady Encrypted Media Extension for Windows 10:</span></span>

-   <span data-ttu-id="735ec-113">Hardwarebasierte Verwaltung digitaler Rechte (Digital Rights Management, DRM) wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="735ec-113">Added hardware digital rights management (DRM).</span></span>

    <span data-ttu-id="735ec-114">Die Unterstützung für hardwarebasierten Inhaltsschutz ermöglicht die sichere Wiedergabe von High-Definition (HD)- und Ultra-High-Definition (UHD)-Inhalten auf mehreren Geräteplattformen.</span><span class="sxs-lookup"><span data-stu-id="735ec-114">Hardware-based content protection support enables secure playback of high definition (HD) and ultra-high definition (UHD) content on multiple device platforms.</span></span> <span data-ttu-id="735ec-115">Schlüsselmaterial (einschließlich privater Schlüssel, Inhaltsschlüssel und anderer Schlüsselmaterialien zum Ableiten oder Entsperren dieser Schlüssel) sowie entschlüsselte komprimierte und nicht komprimierte Videobeispiele werden durch Hardwaresicherheit geschützt.</span><span class="sxs-lookup"><span data-stu-id="735ec-115">Key material (including private keys, content keys, and any other key material used to derive or unlock said keys), and decrypted compressed and uncompressed video samples are protected by leveraging hardware security.</span></span>

-   <span data-ttu-id="735ec-116">Unterstützt das proaktive Abrufen nicht persistenter Lizenzen.</span><span class="sxs-lookup"><span data-stu-id="735ec-116">Provides proactive acquisition of non-persistent licenses.</span></span>
-   <span data-ttu-id="735ec-117">Unterstützt das Abrufen mehrerer Lizenzen in einer Nachricht.</span><span class="sxs-lookup"><span data-stu-id="735ec-117">Provides acquisition of multiple licenses in one message.</span></span>

    <span data-ttu-id="735ec-118">Sie können entweder wie in Windows 8.1 ein PlayReady-Objekt mit mehreren Schlüsselkennungen (KeyIDs) oder [Content Decryption Model (CDM)-Daten (CDMData)](https://go.microsoft.com/fwlink/p/?LinkID=626819) mit mehreren KeyIDs verwenden.</span><span class="sxs-lookup"><span data-stu-id="735ec-118">You can either use a PlayReady object with multiple key identifiers (KeyIDs) as in Windows 8.1, or use [content decryption model data (CDMData)](https://go.microsoft.com/fwlink/p/?LinkID=626819) with multiple KeyIDs.</span></span>

    > [!NOTE]
    > <span data-ttu-id="735ec-119">In Windows10 werden mehrere Schlüsselkennungen unter &lt;KeyID&gt; in CDMData unterstützt.</span><span class="sxs-lookup"><span data-stu-id="735ec-119">In Windows 10, multiple key identifiers are supported under &lt;KeyID&gt; in CDMData.</span></span>

-   <span data-ttu-id="735ec-120">Unterstützung für den Echtzeitablauf, d. h. einer Lizenz mit begrenzter Dauer (Limited Duration License, LDL), wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="735ec-120">Added real time expiration support, or limited duration license (LDL).</span></span>

    <span data-ttu-id="735ec-121">Bietet die Möglichkeit, den Echtzeitablauf für Lizenzen festzulegen.</span><span class="sxs-lookup"><span data-stu-id="735ec-121">Provides the ability to set real-time expiration on licenses.</span></span>

-   <span data-ttu-id="735ec-122">Richtlinienunterstützung für HDCP Typ 1 (Version 2.2) wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="735ec-122">Added HDCP Type 1 (version 2.2) policy support.</span></span>
-   <span data-ttu-id="735ec-123">Miracast ist jetzt als Ausgabe implizit.</span><span class="sxs-lookup"><span data-stu-id="735ec-123">Miracast is now implicit as an output.</span></span>
-   <span data-ttu-id="735ec-124">Sicheres Beenden wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="735ec-124">Added secure stop.</span></span>

    <span data-ttu-id="735ec-125">Dank des sicheren Beendens kann ein PlayReady-Gerät einem Medienstreamingdienst zuverlässig bestätigen, dass die Medienwiedergabe für einen bestimmten Inhalt beendet wurde.</span><span class="sxs-lookup"><span data-stu-id="735ec-125">Secure stop provides the means for a PlayReady device to confidently assert to a media streaming service that media playback has stopped for any given piece of content.</span></span>

-   <span data-ttu-id="735ec-126">Audio- und Videolizenztrennung wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="735ec-126">Added audio and video license separation.</span></span>

    <span data-ttu-id="735ec-127">Separate Spuren verhindern, dass Videos als Audio decodiert werden. Dadurch wird ein stabilerer Inhaltsschutz gewährleistet.</span><span class="sxs-lookup"><span data-stu-id="735ec-127">Separate tracks prevent video from being decoded as audio; enabling more robust content protection.</span></span> <span data-ttu-id="735ec-128">Neue Standards erfordern separate Schlüssel für Audio- und Videospuren.</span><span class="sxs-lookup"><span data-stu-id="735ec-128">Emerging standards are requiring separate keys for audio and visual tracks.</span></span>

-   <span data-ttu-id="735ec-129">MaxResDecode-Feature hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="735ec-129">Added MaxResDecode.</span></span>

    <span data-ttu-id="735ec-130">Dieses Feature wurde hinzugefügt, um die Wiedergabe von Inhalten auf eine maximale Auflösung zu beschränken, auch wenn der Benutzer einen leistungsfähigeren Schlüssel (aber keine Lizenz) besitzt.</span><span class="sxs-lookup"><span data-stu-id="735ec-130">This feature was added to limit playback of content to a maximum resolution even when in possession of a more capable key (but not a license).</span></span> <span data-ttu-id="735ec-131">Dadurch werden Szenarien unterstützt, in denen mehrere Datenstromgrößen mit einem einzelnen Schlüssel codiert werden.</span><span class="sxs-lookup"><span data-stu-id="735ec-131">It supports cases where multiple stream sizes are encoded with a single key.</span></span>

## <a name="encrypted-media-extension-support-in-playready"></a><span data-ttu-id="735ec-132">Unterstützung von verschlüsselten Medienerweiterungen in PlayReady</span><span class="sxs-lookup"><span data-stu-id="735ec-132">Encrypted Media Extension support in PlayReady</span></span>

<span data-ttu-id="735ec-133">In diesem Abschnitt wird die Version der verschlüsselten Medienerweiterungen von W3C beschrieben, die von PlayReady unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="735ec-133">This section describes the version of the W3C Encrypted Media Extension supported by PlayReady.</span></span>

<span data-ttu-id="735ec-134">PlayReady für Web-Apps ist derzeit an die Entwurfsversion vom 10.Mai2013 ([W3C Encrypted Media Extension (EME) draft of May 10, 2013](http://www.w3.org/TR/2013/WD-encrypted-media-20130510/)) gebunden.</span><span class="sxs-lookup"><span data-stu-id="735ec-134">PlayReady for Web Apps is currently bound to the [W3C Encrypted Media Extension (EME) draft of May 10, 2013](http://www.w3.org/TR/2013/WD-encrypted-media-20130510/).</span></span> <span data-ttu-id="735ec-135">Für zukünftige Versionen von Windows wird diese Unterstützung in die aktualisierte EME-Spezifikation geändert.</span><span class="sxs-lookup"><span data-stu-id="735ec-135">This support will be changed to the updated EME specification in future versions of Windows.</span></span>

## <a name="use-hardware-drm"></a><span data-ttu-id="735ec-136">Verwenden des Hardware-DRM</span><span class="sxs-lookup"><span data-stu-id="735ec-136">Use hardware DRM</span></span>

<span data-ttu-id="735ec-137">In diesem Abschnitt wird beschrieben, wie Ihre Web-App das Hardware-DRM mit PlayReady verwenden kann und wie Sie das Hardware-DRM deaktivieren, wenn der geschützte Inhalt es nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="735ec-137">This section describes how your web app can use PlayReady hardware DRM, and how to disable hardware DRM if the protected content does not support it.</span></span>

<span data-ttu-id="735ec-138">Um das Hardware-DRM mit PlayReady zu verwenden, sollte Ihre JavaScript-Web-App die EME-Methode **isTypeSupported** mit einem `com.microsoft.playready.hardware`-Schlüsselsystembezeichner verwenden, um die Unterstützung des Hardware-DRM mit PlayReady vom Browser abzufragen.</span><span class="sxs-lookup"><span data-stu-id="735ec-138">To use PlayReady hardware DRM, your JavaScript web app should use the **isTypeSupported** EME method with a key system identifier of `com.microsoft.playready.hardware` to query for PlayReady hardware DRM support from the browser.</span></span>

<span data-ttu-id="735ec-139">Mitunter werden Inhalte jedoch nicht vom Hardware-DRM unterstützt.</span><span class="sxs-lookup"><span data-stu-id="735ec-139">Occasionally, some content is not supported in hardware DRM.</span></span> <span data-ttu-id="735ec-140">Cocktail-Inhalte werden nie vom Hardware-DRM unterstützt. Wenn Sie Cocktail-Inhalte wiedergeben möchten, müssen Sie das Hardware-DRM außer Kraft setzen.</span><span class="sxs-lookup"><span data-stu-id="735ec-140">Cocktail content is never supported in hardware DRM; if you want to play cocktail content, you must opt out of hardware DRM.</span></span> <span data-ttu-id="735ec-141">Einige Hardware-DRM-Typen unterstützen HEVC, andere dagegen nicht. Wenn Sie HEVC-Inhalte wiedergeben möchten und diese nicht vom Hardware-DRM unterstützt werden, sollten Sie das Hardware-DRM in diesem Fall ebenfalls außer Kraft setzen.</span><span class="sxs-lookup"><span data-stu-id="735ec-141">Some hardware DRM will support HEVC and some will not; if you want to play HEVC content and hardware DRM doesn’t support it, you will want to opt out as well.</span></span>

> [!NOTE]
> <span data-ttu-id="735ec-142">Um festzustellen, ob HEVC-Inhalte unterstützt werden, verwenden Sie nach der Instanziierung von `com.microsoft.playready` die [**PlayReadyStatics.CheckSupportedHardware**](https://msdn.microsoft.com/library/windows/apps/dn986441)-Methode.</span><span class="sxs-lookup"><span data-stu-id="735ec-142">To determine whether HEVC content is supported, after instantiating `com.microsoft.playready`, use the [**PlayReadyStatics.CheckSupportedHardware**](https://msdn.microsoft.com/library/windows/apps/dn986441) method.</span></span>

## <a name="add-secure-stop-to-your-web-app"></a><span data-ttu-id="735ec-143">Hinzufügen des sicheren Beendens zur Web-App</span><span class="sxs-lookup"><span data-stu-id="735ec-143">Add secure stop to your web app</span></span>

<span data-ttu-id="735ec-144">In diesem Abschnitt wird beschrieben, wie Sie Ihrer Web-App die Funktion für sicheres Beenden hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="735ec-144">This section describes how to add secure stop to your web app.</span></span>

<span data-ttu-id="735ec-145">Dank des sicheren Beendens kann ein PlayReady-Gerät einem Medienstreamingdienst zuverlässig bestätigen, dass die Medienwiedergabe für einen bestimmten Inhalt beendet wurde.</span><span class="sxs-lookup"><span data-stu-id="735ec-145">Secure stop provides the means for a PlayReady device to confidently assert to a media streaming service that media playback has stopped for any given piece of content.</span></span> <span data-ttu-id="735ec-146">Mit dieser Funktion wird sichergestellt, dass Ihre Medienstreamingdienste präzise Erzwingung und Berichte zu Nutzungseinschränkungen auf verschiedenen Geräten für ein bestimmtes Konto bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="735ec-146">This capability ensures your media streaming services provide accurate enforcement and reporting of usage limitations on different devices for a given account.</span></span>

<span data-ttu-id="735ec-147">Es gibt zwei primäre Szenarien für das Senden einer Abfrage für sicheres Beenden:</span><span class="sxs-lookup"><span data-stu-id="735ec-147">There are two primary scenarios for sending a secure stop challenge:</span></span>

-   <span data-ttu-id="735ec-148">Wenn die Mediendarstellung beendet wird, weil das Ende des Inhalts erreicht wurde, oder wenn die Mediendarstellung vor ihrem Ende vom Benutzer beendet wurde.</span><span class="sxs-lookup"><span data-stu-id="735ec-148">When the media presentation stops because end of content was reached or when the user stopped the media presentation somewhere in the middle.</span></span>
-   <span data-ttu-id="735ec-149">Wenn die vorherige Sitzung unerwartet beendet wurde (z.B. aufgrund eines System- oder App-Absturzes).</span><span class="sxs-lookup"><span data-stu-id="735ec-149">When the previous session ends unexpectedly (for example, due to a system or app crash).</span></span> <span data-ttu-id="735ec-150">Die App muss beim Starten oder Herunterfahren alle ausstehenden Sitzungen für sicheres Beenden abfragen und von anderen Medienwiedergaben getrennte Abfragen senden.</span><span class="sxs-lookup"><span data-stu-id="735ec-150">The app will need to query, either at startup or shutdown, for any outstanding secure stop sessions and send challenge(s) separate from any other media playback.</span></span>

<span data-ttu-id="735ec-151">In den folgenden Verfahren wird beschrieben, wie Sie das sichere Beenden für verschiedene Szenarien einrichten.</span><span class="sxs-lookup"><span data-stu-id="735ec-151">The following procedures describe how to set up secure stop for various scenarios.</span></span>

<span data-ttu-id="735ec-152">So richten Sie das sichere Beenden für die normale Beendigung einer Mediendarstellung ein</span><span class="sxs-lookup"><span data-stu-id="735ec-152">To set up secure stop for a normal end of a presentation:</span></span>

1.  <span data-ttu-id="735ec-153">Registrieren Sie das **onEnded**-Ereignis vor dem Start der Wiedergabe.</span><span class="sxs-lookup"><span data-stu-id="735ec-153">Register the **onEnded** event before playback starts.</span></span>
2.  <span data-ttu-id="735ec-154">Der **onEnded**-Ereignishandler muss `removeAttribute(“src”)` über das Video-/Audioelementobjekt aufrufen, um die Quelle auf **NULL** festzulegen, damit Media Foundation die Topologie unterbricht, die Decryptors zerstört und den Beendigungszustand festlegt.</span><span class="sxs-lookup"><span data-stu-id="735ec-154">The **onEnded** event handler needs to call `removeAttribute(“src”)` from the video/audio element object to set the source to **NULL** which will trigger the media foundation to tear down the topology, destroy the decryptor(s), and set the stop state.</span></span>
3.  <span data-ttu-id="735ec-155">Sie können die CDM-Sitzung für sicheres Beenden innerhalb des Handlers oder an späterer Stelle starten, um die Abfrage für sicheres Beenden an den Server zu senden und ihn darüber zu benachrichtigen, dass die Wiedergabe beendet wurde.</span><span class="sxs-lookup"><span data-stu-id="735ec-155">You can start the secure stop CDM session inside the handler to send the secure stop challenge to the server to notify the playback has stopped at this time, but it can be done later as well.</span></span>

<span data-ttu-id="735ec-156">So richten Sie das sichere Beenden für den Fall ein, dass der Benutzer die Seite verlässt oder die Registerkarte oder den Browser schließt</span><span class="sxs-lookup"><span data-stu-id="735ec-156">To set up secure stop if the user navigates away from the page or closes down the tab or browser:</span></span>

-   <span data-ttu-id="735ec-157">Zum Aufzeichnen des Beendigungszustands ist keine App-Aktion erforderlich. Der Zustand wird automatisch aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="735ec-157">No app action is required to record the stop state; it will be recorded for you.</span></span>

<span data-ttu-id="735ec-158">So richten Sie das sichere Beenden für benutzerdefinierte Steuerelemente oder Benutzeraktionen ein (z.B. benutzerdefinierte Navigationsschaltflächen oder das Starten einer neuen Mediendarstellung vor Abschluss der aktuellen Mediendarstellung)</span><span class="sxs-lookup"><span data-stu-id="735ec-158">To set up secure stop for custom page controls or user actions (such as custom navigation buttons or starting a new presentation before the current presentation completed):</span></span>

-   <span data-ttu-id="735ec-159">Wenn die benutzerdefinierte Aktion stattfindet, muss die App die Quelle auf **NULL** festlegen, damit Media Foundation die Topologie unterbricht, die Decryptors zerstört und den Beendigungszustand festlegt.</span><span class="sxs-lookup"><span data-stu-id="735ec-159">When custom user action occurs, the app needs to set the source to **NULL** which will trigger the media foundation to tear down the topology, destroy the decryptor(s), and set the stop state.</span></span>

<span data-ttu-id="735ec-160">Das folgende Beispiel zeigt, wie Sie das sichere Beenden in Ihrer Web-App verwenden:</span><span class="sxs-lookup"><span data-stu-id="735ec-160">The following example demonstrates how to use secure stop in your web app:</span></span>

```JavaScript
// JavaScript source code

var g_prkey = null;
var g_keySession = null;
var g_fUseSpecificSecureStopSessionID = false;
var g_encodedMeteringCert = 'Base64 encoded of your metering cert (aka publisher cert)';

// Note: g_encodedLASessionId is the CDM session ID of the proactive or reactive license acquisition 
//       that we want to initiate the secure stop process.
var g_encodedLASessionId = null;

function main()
{
    ...

    g_prkey = new MSMediaKeys("com.microsoft.playready");

    ...

    // add 'onended' event handler to the video element
    // Assume 'myvideo' is the ID of the video element
    var videoElement = document.getElementById("myvideo");
    videoElement.onended = function (e) { 

        //
        // Calling removeAttribute("src") will set the source to null
        // which will trigger the MF to tear down the topology, destroy the
        // decryptor(s) and set the stop state.  This is required in order
        // to set the stop state.
        //
        videoElement.removeAttribute("src");
        videoElement.load();

        onEndOfStream();
    };
}

function onEndOfStream()
{
    ...

    createSecureStopCDMSession();

    ...    
}

function createSecureStopCDMSession()
{
    try{    
        var targetMediaCodec = "video/mp4";
        var customData = "my custom data";

        var encodedSessionId = g_encodedLASessionId;
        if( !g_fUseSpecificSecureStopSessionID )
        {
            // Use "*" (wildcard) as the session ID to include all secure stop sessions
            // TODO: base64 encode "*" and place encoded result to encodedSessionId
        }

        var int8ArrayCDMdata = formatSecureStopCDMData( encodedSessionId, customData,  g_encodedMeteringCert );
        var emptyArrayofInitData = new Uint8Array();

        g_keySession = g_prkey.createSession(targetMediaCodec, emptyArrayofInitData, int8ArrayCDMdata);

        addPlayreadyKeyEventHandler();

    } catch( e )
    {
        // TODO: Handle exception
    }
}

function addPlayreadyKeyEventHandler()
{
    // add 'keymessage' eventhandler   
    g_keySession.addEventListener('mskeymessage', function (event) {

        // TODO: Get the keyMessage from event.message.buffer which contains the secure stop challenge
        //       The keyMessage format for the secure stop is similar to LA as below:
        //
        //            <PlayReadyKeyMessage type="SecureStop" >
        //              <SecureStop version="1.0" >
        //                <Challenge encoding="base64encoded">
        //                    secure stop challenge
        //                </Challenge>
        //                <HttpHeaders>
        //                    <HttpHeader>
        //                      <name>Content-Type</name>
        //                         <value>"content type data"</value>
        //                    </HttpHeader>
        //                    <HttpHeader>
        //                         <name>SOAPAction</name>
        //                         <value>soap action</value>
        //                     </HttpHeader>
        //                    ....
        //                </HttpHeaders>
        //              </SecureStop>
        //            </PlayReadyKeyMessage>
                
        // TODO: send the secure stop challenge to a server that handles the secure stop challenge

        // TODO: Recevie and response and call event.target.Update() to proecess the response
    });
    
    // add 'keyerror' eventhandler
    g_keySession.addEventListener('mskeyerror', function (event) {
        var session = event.target;
        
        ...

        session.close();
    });
    
    // add 'keyadded' eventhandler
    g_keySession.addEventListener('mskeyadded', function (event) {
        
        var session = event.target;

        ...

        session.close();             
    });
}

/**
* desc@ formatSecureStopCDMData
*   generate playready CDMData
*   CDMData is in xml format:
*   <PlayReadyCDMData type="SecureStop">
*     <SecureStop version="1.0">
*       <SessionID>B64 encoded session ID</SessionID>
*       <CustomData>B64 encoded custom data</CustomData>
*       <ServerCert>B64 encoded server cert</ServerCert>
*     </SecureCert>
* </PlayReadyCDMData>        
*/
function formatSecureStopCDMData(encodedSessionId, customData, encodedPublisherCert) 
{
    var encodedCustomData = null;

    // TODO: base64 encode the custom data and place the encoded result to encodedCustomData

    var CDMDataStr = "<PlayReadyCDMData type=\"SecureStop\">" +
                     "<SecureStop version=\"1.0\" >" +
                     "<SessionID>" + encodedSessionId + "</SessionID>" +
                     "<CustomData>" + encodedCustomData + "</CustomData>" +
                     "<ServerCert>" + encodedPublisherCert + "</ServerCert>" +
                     "</SecureStop></PlayReadyCDMData>";
    
    var int8ArrayCDMdata = null

    // TODO: Convert CDMDataStr to Uint8 byte array and palce the converted result to int8ArrayCDMdata

    return int8ArrayCDMdata;
}
```

> [!NOTE]
> <span data-ttu-id="735ec-161">Für die Sitzungs-ID `<SessionID>B64 encoded session ID</SessionID>` der Daten für sicheres Beenden im obigen Beispiel kann ein Sternchen (\*) angegeben werden. Das Sternchen ist ein Platzhalter für alle aufgezeichneten Sitzungen für sicheres Beenden.</span><span class="sxs-lookup"><span data-stu-id="735ec-161">The secure stop data’s `<SessionID>B64 encoded session ID</SessionID>` in the sample above can be an asterisk (\*), which is a wild card for all the secure stop sessions recorded.</span></span> <span data-ttu-id="735ec-162">Beim **SessionID**-Tag kann es sich also um eine bestimmte Sitzung oder einen Platzhalter (\*) zur Auswahl aller Sitzungen für sicheres Beenden handeln.</span><span class="sxs-lookup"><span data-stu-id="735ec-162">That is, the **SessionID** tag can be a specific session, or a wild card (\*) to select all the secure stop sessions.</span></span>

## <a name="programming-considerations-for-encrypted-media-extension"></a><span data-ttu-id="735ec-163">Überlegungen zur Programmierung für verschlüsselte Medienerweiterungen (Encrypted Media Extensions, EME)</span><span class="sxs-lookup"><span data-stu-id="735ec-163">Programming considerations for Encrypted Media Extension</span></span>

<span data-ttu-id="735ec-164">Dieser Abschnitt enthält Hinweise zur Programmierung, die Sie beim Erstellen Ihrer PlayReady-fähigen Web-App für Windows 10 berücksichtigen sollten.</span><span class="sxs-lookup"><span data-stu-id="735ec-164">This section lists the programming considerations that you should take into account when creating your PlayReady-enabled web app for Windows 10.</span></span>

<span data-ttu-id="735ec-165">Die von Ihrer App erstellten Objekte **MSMediaKeys** und **MSMediaKeySession** müssen aktiv bleiben, bis die App geschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="735ec-165">The **MSMediaKeys** and **MSMediaKeySession** objects created by your app must be kept alive until your app closes.</span></span> <span data-ttu-id="735ec-166">Eine Möglichkeit, um sicherzustellen, dass diese Objekte aktiv bleiben, ist deren Zuweisung als globale Variablen (die Variablen würden den Gültigkeitsbereich verlassen und der Garbage Collection zugeführt, wenn sie innerhalb einer Funktion als lokale Variable deklariert werden).</span><span class="sxs-lookup"><span data-stu-id="735ec-166">One way of ensuring these objects stay alive is to assign them as global variables (the variables would become out of scope and subject to garbage collection if declared as a local variable inside of a function).</span></span> <span data-ttu-id="735ec-167">Im folgende Beispiel werden z. B. die Variablen *g\_msMediaKeys* und *g\_mediaKeySession* als globale Variablen zugewiesen, die dann den Objekten **MSMediaKeys** und **MSMediaKeySession** in der Funktion zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="735ec-167">For example, the following sample assigns the variables *g\_msMediaKeys* and *g\_mediaKeySession* as global variables, which are then assigned to the **MSMediaKeys** and **MSMediaKeySession** objects in the function.</span></span>

``` syntax
var g_msMediaKeys;
var g_mediaKeySession;

function foo() {
  ...
  g_msMediaKeys = new MSMediaKeys("com.microsoft.playready");
  ...
  g_mediaKeySession = g_msMediaKeys.createSession("video/mp4", intiData, null);
  g_mediaKeySession.addEventListener(this.KEYMESSAGE_EVENT, function (e) 
  {
    ...
    downloadPlayReadyKey(url, keyMessage, function (data) 
    {
      g_mediaKeySession.update(data);
    });
  });
  g_mediaKeySession.addEventListener(this.KEYADDED_EVENT, function () 
  {
    ...
    g_mediaKeySession.close();
    g_mediaKeySession = null;
  });
}
```

<span data-ttu-id="735ec-168">Weitere Informationen finden Sie in den [Beispielanwendungen](https://code.msdn.microsoft.com/windowsapps/PlayReady-samples-for-124a3738).</span><span class="sxs-lookup"><span data-stu-id="735ec-168">For more information, see the [sample applications](https://code.msdn.microsoft.com/windowsapps/PlayReady-samples-for-124a3738).</span></span>

## <a name="see-also"></a><span data-ttu-id="735ec-169">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="735ec-169">See also</span></span>
- [<span data-ttu-id="735ec-170">PlayReady DRM</span><span class="sxs-lookup"><span data-stu-id="735ec-170">PlayReady DRM</span></span>](playready-client-sdk.md)




