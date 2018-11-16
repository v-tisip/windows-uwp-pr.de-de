---
author: drewbatgit
ms.assetid: 79C284CA-C53A-4C24-807E-6D4CE1A29BFA
description: In diesem Abschnitt wird beschrieben, wie zum Ändern Ihrer PlayReady-Web-app, um die Änderungen, die aus der vorherigen Version Windows8.1 in die Windows 10-Version zu unterstützen.
title: Verschlüsselte Medienerweiterung von PlayReady
ms.author: drewbat
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: b73464ea10aa835b82df17605e983ebdfb9cd890
ms.sourcegitcommit: e38b334edb82bf2b1474ba686990f4299b8f59c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6837647"
---
# <a name="playready-encrypted-media-extension"></a><span data-ttu-id="d8579-104">Verschlüsselte Medienerweiterung von PlayReady</span><span class="sxs-lookup"><span data-stu-id="d8579-104">PlayReady Encrypted Media Extension</span></span>



<span data-ttu-id="d8579-105">In diesem Abschnitt wird beschrieben, wie zum Ändern Ihrer PlayReady-Web-app, um die Änderungen, die aus der vorherigen Version Windows8.1 in die Windows 10-Version zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="d8579-105">This section describes how to modify your PlayReady web app to support the changes made from the previous Windows8.1 version to the Windows10 version.</span></span>

<span data-ttu-id="d8579-106">Die Verwendung von PlayReady-Medienelementen in Internet Explorer ermöglicht Entwicklern das Erstellen von Web-Apps, die PlayReady-geschützte Inhalte für den Benutzer bereitstellen und gleichzeitig vom Inhaltsanbieter definierte Regeln erzwingen können.</span><span class="sxs-lookup"><span data-stu-id="d8579-106">Using PlayReady media elements in Internet Explorer enables developers to create web apps capable of providing PlayReady content to the user while enforcing the access rules defined by the content provider.</span></span> <span data-ttu-id="d8579-107">In diesem Abschnitt wird beschrieben, wie Sie Ihren vorhandenen Web-Apps PlayReady-Medienelemente hinzufügen, indem Sie nur HTML5 und JavaScript verwenden.</span><span class="sxs-lookup"><span data-stu-id="d8579-107">This section describes how to add PlayReady media elements to your existing web apps by using only HTML5 and JavaScript.</span></span>

## <a name="whats-new-in-playready-encrypted-media-extension"></a><span data-ttu-id="d8579-108">Neuigkeiten in der verschlüsselten Medienerweiterung von PlayReady</span><span class="sxs-lookup"><span data-stu-id="d8579-108">What's new in PlayReady Encrypted Media Extension</span></span>

<span data-ttu-id="d8579-109">Dieser Abschnitt enthält eine Liste der Änderungen, die PlayReady verschlüsselten Extension (EME) um PlayReady-Inhaltsschutz unter Windows 10 zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="d8579-109">This section provides a list of changes made to the PlayReady Encrypted Media Extension (EME) to enable PlayReady content protection on Windows10.</span></span>

<span data-ttu-id="d8579-110">Die folgende Liste beschreibt die neuen Features und Änderungen an verschlüsselten Medienerweiterung von PlayReady für Windows 10:</span><span class="sxs-lookup"><span data-stu-id="d8579-110">The following list describes the new features and changes made to PlayReady Encrypted Media Extension for Windows10:</span></span>

-   <span data-ttu-id="d8579-111">Hardwarebasierte Verwaltung digitaler Rechte (Digital Rights Management, DRM) wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="d8579-111">Added hardware digital rights management (DRM).</span></span>

    <span data-ttu-id="d8579-112">Die Unterstützung für hardwarebasierten Inhaltsschutz ermöglicht die sichere Wiedergabe von High-Definition (HD)- und Ultra-High-Definition (UHD)-Inhalten auf mehreren Geräteplattformen.</span><span class="sxs-lookup"><span data-stu-id="d8579-112">Hardware-based content protection support enables secure playback of high definition (HD) and ultra-high definition (UHD) content on multiple device platforms.</span></span> <span data-ttu-id="d8579-113">Schlüsselmaterial (einschließlich privater Schlüssel, Inhaltsschlüssel und anderer Schlüsselmaterialien zum Ableiten oder Entsperren dieser Schlüssel) sowie entschlüsselte komprimierte und nicht komprimierte Videobeispiele werden durch Hardwaresicherheit geschützt.</span><span class="sxs-lookup"><span data-stu-id="d8579-113">Key material (including private keys, content keys, and any other key material used to derive or unlock said keys), and decrypted compressed and uncompressed video samples are protected by leveraging hardware security.</span></span>

-   <span data-ttu-id="d8579-114">Unterstützt das proaktive Abrufen nicht persistenter Lizenzen.</span><span class="sxs-lookup"><span data-stu-id="d8579-114">Provides proactive acquisition of non-persistent licenses.</span></span>
-   <span data-ttu-id="d8579-115">Unterstützt das Abrufen mehrerer Lizenzen in einer Nachricht.</span><span class="sxs-lookup"><span data-stu-id="d8579-115">Provides acquisition of multiple licenses in one message.</span></span>

    <span data-ttu-id="d8579-116">Sie können entweder ein PlayReady-Objekt mit mehreren schlüsselkennungen (KeyIDs) wie Windows8.1 verwenden oder [Inhalte Entschlüsselung Modell-Daten (CDMData)](https://go.microsoft.com/fwlink/p/?LinkID=626819) mit mehreren KeyIDs verwenden.</span><span class="sxs-lookup"><span data-stu-id="d8579-116">You can either use a PlayReady object with multiple key identifiers (KeyIDs) as in Windows8.1, or use [content decryption model data (CDMData)](https://go.microsoft.com/fwlink/p/?LinkID=626819) with multiple KeyIDs.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d8579-117">In Windows 10, werden mehrere schlüsselkennungen unter unterstützt &lt;KeyID&gt; in CDMData.</span><span class="sxs-lookup"><span data-stu-id="d8579-117">In Windows10, multiple key identifiers are supported under &lt;KeyID&gt; in CDMData.</span></span>

-   <span data-ttu-id="d8579-118">Unterstützung für den Echtzeitablauf, d. h. einer Lizenz mit begrenzter Dauer (Limited Duration License, LDL), wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="d8579-118">Added real time expiration support, or limited duration license (LDL).</span></span>

    <span data-ttu-id="d8579-119">Bietet die Möglichkeit, den Echtzeitablauf für Lizenzen festzulegen.</span><span class="sxs-lookup"><span data-stu-id="d8579-119">Provides the ability to set real-time expiration on licenses.</span></span>

-   <span data-ttu-id="d8579-120">Richtlinienunterstützung für HDCP Typ 1 (Version 2.2) wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="d8579-120">Added HDCP Type 1 (version 2.2) policy support.</span></span>
-   <span data-ttu-id="d8579-121">Miracast ist jetzt als Ausgabe implizit.</span><span class="sxs-lookup"><span data-stu-id="d8579-121">Miracast is now implicit as an output.</span></span>
-   <span data-ttu-id="d8579-122">Sicheres Beenden wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="d8579-122">Added secure stop.</span></span>

    <span data-ttu-id="d8579-123">Dank des sicheren Beendens kann ein PlayReady-Gerät einem Medienstreamingdienst zuverlässig bestätigen, dass die Medienwiedergabe für einen bestimmten Inhalt beendet wurde.</span><span class="sxs-lookup"><span data-stu-id="d8579-123">Secure stop provides the means for a PlayReady device to confidently assert to a media streaming service that media playback has stopped for any given piece of content.</span></span>

-   <span data-ttu-id="d8579-124">Audio- und Videolizenztrennung wurde hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="d8579-124">Added audio and video license separation.</span></span>

    <span data-ttu-id="d8579-125">Separate Spuren verhindern, dass Videos als Audio decodiert werden. Dadurch wird ein stabilerer Inhaltsschutz gewährleistet.</span><span class="sxs-lookup"><span data-stu-id="d8579-125">Separate tracks prevent video from being decoded as audio; enabling more robust content protection.</span></span> <span data-ttu-id="d8579-126">Neue Standards erfordern separate Schlüssel für Audio- und Videospuren.</span><span class="sxs-lookup"><span data-stu-id="d8579-126">Emerging standards are requiring separate keys for audio and visual tracks.</span></span>

-   <span data-ttu-id="d8579-127">MaxResDecode-Feature hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="d8579-127">Added MaxResDecode.</span></span>

    <span data-ttu-id="d8579-128">Dieses Feature wurde hinzugefügt, um die Wiedergabe von Inhalten auf eine maximale Auflösung zu beschränken, auch wenn der Benutzer einen leistungsfähigeren Schlüssel (aber keine Lizenz) besitzt.</span><span class="sxs-lookup"><span data-stu-id="d8579-128">This feature was added to limit playback of content to a maximum resolution even when in possession of a more capable key (but not a license).</span></span> <span data-ttu-id="d8579-129">Dadurch werden Szenarien unterstützt, in denen mehrere Datenstromgrößen mit einem einzelnen Schlüssel codiert werden.</span><span class="sxs-lookup"><span data-stu-id="d8579-129">It supports cases where multiple stream sizes are encoded with a single key.</span></span>

## <a name="encrypted-media-extension-support-in-playready"></a><span data-ttu-id="d8579-130">Unterstützung von verschlüsselten Medienerweiterungen in PlayReady</span><span class="sxs-lookup"><span data-stu-id="d8579-130">Encrypted Media Extension support in PlayReady</span></span>

<span data-ttu-id="d8579-131">In diesem Abschnitt wird die Version der verschlüsselten Medienerweiterungen von W3C beschrieben, die von PlayReady unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="d8579-131">This section describes the version of the W3C Encrypted Media Extension supported by PlayReady.</span></span>

<span data-ttu-id="d8579-132">PlayReady für Web-Apps ist derzeit an die Entwurfsversion vom 10.Mai2013 ([W3C Encrypted Media Extension (EME) draft of May 10, 2013](http://www.w3.org/TR/2013/WD-encrypted-media-20130510/)) gebunden.</span><span class="sxs-lookup"><span data-stu-id="d8579-132">PlayReady for Web Apps is currently bound to the [W3C Encrypted Media Extension (EME) draft of May 10, 2013](http://www.w3.org/TR/2013/WD-encrypted-media-20130510/).</span></span> <span data-ttu-id="d8579-133">Für zukünftige Versionen von Windows wird diese Unterstützung in die aktualisierte EME-Spezifikation geändert.</span><span class="sxs-lookup"><span data-stu-id="d8579-133">This support will be changed to the updated EME specification in future versions of Windows.</span></span>

## <a name="use-hardware-drm"></a><span data-ttu-id="d8579-134">Verwenden des Hardware-DRM</span><span class="sxs-lookup"><span data-stu-id="d8579-134">Use hardware DRM</span></span>

<span data-ttu-id="d8579-135">In diesem Abschnitt wird beschrieben, wie Ihre Web-App das Hardware-DRM mit PlayReady verwenden kann und wie Sie das Hardware-DRM deaktivieren, wenn der geschützte Inhalt es nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d8579-135">This section describes how your web app can use PlayReady hardware DRM, and how to disable hardware DRM if the protected content does not support it.</span></span>

<span data-ttu-id="d8579-136">Um das Hardware-DRM mit PlayReady zu verwenden, sollte Ihre JavaScript-Web-App die EME-Methode **isTypeSupported** mit einem `com.microsoft.playready.hardware`-Schlüsselsystembezeichner verwenden, um die Unterstützung des Hardware-DRM mit PlayReady vom Browser abzufragen.</span><span class="sxs-lookup"><span data-stu-id="d8579-136">To use PlayReady hardware DRM, your JavaScript web app should use the **isTypeSupported** EME method with a key system identifier of `com.microsoft.playready.hardware` to query for PlayReady hardware DRM support from the browser.</span></span>

<span data-ttu-id="d8579-137">Mitunter werden Inhalte jedoch nicht vom Hardware-DRM unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d8579-137">Occasionally, some content is not supported in hardware DRM.</span></span> <span data-ttu-id="d8579-138">Cocktail-Inhalte werden nie vom Hardware-DRM unterstützt. Wenn Sie Cocktail-Inhalte wiedergeben möchten, müssen Sie das Hardware-DRM außer Kraft setzen.</span><span class="sxs-lookup"><span data-stu-id="d8579-138">Cocktail content is never supported in hardware DRM; if you want to play cocktail content, you must opt out of hardware DRM.</span></span> <span data-ttu-id="d8579-139">Einige Hardware-DRM-Typen unterstützen HEVC, andere dagegen nicht. Wenn Sie HEVC-Inhalte wiedergeben möchten und diese nicht vom Hardware-DRM unterstützt werden, sollten Sie das Hardware-DRM in diesem Fall ebenfalls außer Kraft setzen.</span><span class="sxs-lookup"><span data-stu-id="d8579-139">Some hardware DRM will support HEVC and some will not; if you want to play HEVC content and hardware DRM doesn’t support it, you will want to opt out as well.</span></span>

> [!NOTE]
> <span data-ttu-id="d8579-140">Um festzustellen, ob HEVC-Inhalte unterstützt werden, verwenden Sie nach der Instanziierung von `com.microsoft.playready` die [**PlayReadyStatics.CheckSupportedHardware**](https://msdn.microsoft.com/library/windows/apps/dn986441)-Methode.</span><span class="sxs-lookup"><span data-stu-id="d8579-140">To determine whether HEVC content is supported, after instantiating `com.microsoft.playready`, use the [**PlayReadyStatics.CheckSupportedHardware**](https://msdn.microsoft.com/library/windows/apps/dn986441) method.</span></span>

## <a name="add-secure-stop-to-your-web-app"></a><span data-ttu-id="d8579-141">Hinzufügen des sicheren Beendens zur Web-App</span><span class="sxs-lookup"><span data-stu-id="d8579-141">Add secure stop to your web app</span></span>

<span data-ttu-id="d8579-142">In diesem Abschnitt wird beschrieben, wie Sie Ihrer Web-App die Funktion für sicheres Beenden hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="d8579-142">This section describes how to add secure stop to your web app.</span></span>

<span data-ttu-id="d8579-143">Dank des sicheren Beendens kann ein PlayReady-Gerät einem Medienstreamingdienst zuverlässig bestätigen, dass die Medienwiedergabe für einen bestimmten Inhalt beendet wurde.</span><span class="sxs-lookup"><span data-stu-id="d8579-143">Secure stop provides the means for a PlayReady device to confidently assert to a media streaming service that media playback has stopped for any given piece of content.</span></span> <span data-ttu-id="d8579-144">Mit dieser Funktion wird sichergestellt, dass Ihre Medienstreamingdienste präzise Erzwingung und Berichte zu Nutzungseinschränkungen auf verschiedenen Geräten für ein bestimmtes Konto bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="d8579-144">This capability ensures your media streaming services provide accurate enforcement and reporting of usage limitations on different devices for a given account.</span></span>

<span data-ttu-id="d8579-145">Es gibt zwei primäre Szenarien für das Senden einer Abfrage für sicheres Beenden:</span><span class="sxs-lookup"><span data-stu-id="d8579-145">There are two primary scenarios for sending a secure stop challenge:</span></span>

-   <span data-ttu-id="d8579-146">Wenn die Mediendarstellung beendet wird, weil das Ende des Inhalts erreicht wurde, oder wenn die Mediendarstellung vor ihrem Ende vom Benutzer beendet wurde.</span><span class="sxs-lookup"><span data-stu-id="d8579-146">When the media presentation stops because end of content was reached or when the user stopped the media presentation somewhere in the middle.</span></span>
-   <span data-ttu-id="d8579-147">Wenn die vorherige Sitzung unerwartet beendet wurde (z.B. aufgrund eines System- oder App-Absturzes).</span><span class="sxs-lookup"><span data-stu-id="d8579-147">When the previous session ends unexpectedly (for example, due to a system or app crash).</span></span> <span data-ttu-id="d8579-148">Die App muss beim Starten oder Herunterfahren alle ausstehenden Sitzungen für sicheres Beenden abfragen und von anderen Medienwiedergaben getrennte Abfragen senden.</span><span class="sxs-lookup"><span data-stu-id="d8579-148">The app will need to query, either at startup or shutdown, for any outstanding secure stop sessions and send challenge(s) separate from any other media playback.</span></span>

<span data-ttu-id="d8579-149">In den folgenden Verfahren wird beschrieben, wie Sie das sichere Beenden für verschiedene Szenarien einrichten.</span><span class="sxs-lookup"><span data-stu-id="d8579-149">The following procedures describe how to set up secure stop for various scenarios.</span></span>

<span data-ttu-id="d8579-150">So richten Sie das sichere Beenden für die normale Beendigung einer Mediendarstellung ein</span><span class="sxs-lookup"><span data-stu-id="d8579-150">To set up secure stop for a normal end of a presentation:</span></span>

1.  <span data-ttu-id="d8579-151">Registrieren Sie das **onEnded**-Ereignis vor dem Start der Wiedergabe.</span><span class="sxs-lookup"><span data-stu-id="d8579-151">Register the **onEnded** event before playback starts.</span></span>
2.  <span data-ttu-id="d8579-152">Der **onEnded**-Ereignishandler muss `removeAttribute(“src”)` über das Video-/Audioelementobjekt aufrufen, um die Quelle auf **NULL** festzulegen, damit Media Foundation die Topologie unterbricht, die Decryptors zerstört und den Beendigungszustand festlegt.</span><span class="sxs-lookup"><span data-stu-id="d8579-152">The **onEnded** event handler needs to call `removeAttribute(“src”)` from the video/audio element object to set the source to **NULL** which will trigger the media foundation to tear down the topology, destroy the decryptor(s), and set the stop state.</span></span>
3.  <span data-ttu-id="d8579-153">Sie können die CDM-Sitzung für sicheres Beenden innerhalb des Handlers oder an späterer Stelle starten, um die Abfrage für sicheres Beenden an den Server zu senden und ihn darüber zu benachrichtigen, dass die Wiedergabe beendet wurde.</span><span class="sxs-lookup"><span data-stu-id="d8579-153">You can start the secure stop CDM session inside the handler to send the secure stop challenge to the server to notify the playback has stopped at this time, but it can be done later as well.</span></span>

<span data-ttu-id="d8579-154">So richten Sie das sichere Beenden für den Fall ein, dass der Benutzer die Seite verlässt oder die Registerkarte oder den Browser schließt</span><span class="sxs-lookup"><span data-stu-id="d8579-154">To set up secure stop if the user navigates away from the page or closes down the tab or browser:</span></span>

-   <span data-ttu-id="d8579-155">Zum Aufzeichnen des Beendigungszustands ist keine App-Aktion erforderlich. Der Zustand wird automatisch aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="d8579-155">No app action is required to record the stop state; it will be recorded for you.</span></span>

<span data-ttu-id="d8579-156">So richten Sie das sichere Beenden für benutzerdefinierte Steuerelemente oder Benutzeraktionen ein (z.B. benutzerdefinierte Navigationsschaltflächen oder das Starten einer neuen Mediendarstellung vor Abschluss der aktuellen Mediendarstellung)</span><span class="sxs-lookup"><span data-stu-id="d8579-156">To set up secure stop for custom page controls or user actions (such as custom navigation buttons or starting a new presentation before the current presentation completed):</span></span>

-   <span data-ttu-id="d8579-157">Wenn die benutzerdefinierte Aktion stattfindet, muss die App die Quelle auf **NULL** festlegen, damit Media Foundation die Topologie unterbricht, die Decryptors zerstört und den Beendigungszustand festlegt.</span><span class="sxs-lookup"><span data-stu-id="d8579-157">When custom user action occurs, the app needs to set the source to **NULL** which will trigger the media foundation to tear down the topology, destroy the decryptor(s), and set the stop state.</span></span>

<span data-ttu-id="d8579-158">Das folgende Beispiel zeigt, wie Sie das sichere Beenden in Ihrer Web-App verwenden:</span><span class="sxs-lookup"><span data-stu-id="d8579-158">The following example demonstrates how to use secure stop in your web app:</span></span>

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
> <span data-ttu-id="d8579-159">Für die Sitzungs-ID `<SessionID>B64 encoded session ID</SessionID>` der Daten für sicheres Beenden im obigen Beispiel kann ein Sternchen (\*) angegeben werden. Das Sternchen ist ein Platzhalter für alle aufgezeichneten Sitzungen für sicheres Beenden.</span><span class="sxs-lookup"><span data-stu-id="d8579-159">The secure stop data’s `<SessionID>B64 encoded session ID</SessionID>` in the sample above can be an asterisk (\*), which is a wild card for all the secure stop sessions recorded.</span></span> <span data-ttu-id="d8579-160">Beim **SessionID**-Tag kann es sich also um eine bestimmte Sitzung oder einen Platzhalter (\*) zur Auswahl aller Sitzungen für sicheres Beenden handeln.</span><span class="sxs-lookup"><span data-stu-id="d8579-160">That is, the **SessionID** tag can be a specific session, or a wild card (\*) to select all the secure stop sessions.</span></span>

## <a name="programming-considerations-for-encrypted-media-extension"></a><span data-ttu-id="d8579-161">Überlegungen zur Programmierung für verschlüsselte Medienerweiterungen (Encrypted Media Extensions, EME)</span><span class="sxs-lookup"><span data-stu-id="d8579-161">Programming considerations for Encrypted Media Extension</span></span>

<span data-ttu-id="d8579-162">Dieser Abschnitt enthält Hinweise zur Programmierung, die Sie berücksichtigen sollten bei der Erstellung Ihrer PlayReady-fähigen Web-app für Windows 10.</span><span class="sxs-lookup"><span data-stu-id="d8579-162">This section lists the programming considerations that you should take into account when creating your PlayReady-enabled web app for Windows10.</span></span>

<span data-ttu-id="d8579-163">Die von Ihrer App erstellten Objekte **MSMediaKeys** und **MSMediaKeySession** müssen aktiv bleiben, bis die App geschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="d8579-163">The **MSMediaKeys** and **MSMediaKeySession** objects created by your app must be kept alive until your app closes.</span></span> <span data-ttu-id="d8579-164">Eine Möglichkeit, um sicherzustellen, dass diese Objekte aktiv bleiben, ist deren Zuweisung als globale Variablen (die Variablen würden den Gültigkeitsbereich verlassen und der Garbage Collection zugeführt, wenn sie innerhalb einer Funktion als lokale Variable deklariert werden).</span><span class="sxs-lookup"><span data-stu-id="d8579-164">One way of ensuring these objects stay alive is to assign them as global variables (the variables would become out of scope and subject to garbage collection if declared as a local variable inside of a function).</span></span> <span data-ttu-id="d8579-165">Im folgende Beispiel werden z. B. die Variablen *g\_msMediaKeys* und *g\_mediaKeySession* als globale Variablen zugewiesen, die dann den Objekten **MSMediaKeys** und **MSMediaKeySession** in der Funktion zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="d8579-165">For example, the following sample assigns the variables *g\_msMediaKeys* and *g\_mediaKeySession* as global variables, which are then assigned to the **MSMediaKeys** and **MSMediaKeySession** objects in the function.</span></span>

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

<span data-ttu-id="d8579-166">Weitere Informationen finden Sie in den [Beispielanwendungen](https://code.msdn.microsoft.com/windowsapps/PlayReady-samples-for-124a3738).</span><span class="sxs-lookup"><span data-stu-id="d8579-166">For more information, see the [sample applications](https://code.msdn.microsoft.com/windowsapps/PlayReady-samples-for-124a3738).</span></span>

## <a name="see-also"></a><span data-ttu-id="d8579-167">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d8579-167">See also</span></span>
- [<span data-ttu-id="d8579-168">PlayReady DRM</span><span class="sxs-lookup"><span data-stu-id="d8579-168">PlayReady DRM</span></span>](playready-client-sdk.md)




