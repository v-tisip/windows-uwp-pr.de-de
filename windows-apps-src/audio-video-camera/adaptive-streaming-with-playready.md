---
ms.assetid: BF877F23-1238-4586-9C16-246F3F25AE35
description: In diesem Artikel wird beschrieben, wie Sie einer UWP-App (Universelle Windows-Plattform) adaptives Streaming von Multimediainhalten mit Microsoft PlayReady-Inhaltsschutz hinzufügen.
title: Adaptives Streaming mit PlayReady
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 36cd006b4608d82999281ebd407fd32e168ae38b
ms.sourcegitcommit: d2517e522cacc5240f7dffd5bc1eaa278e3f7768
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8352324"
---
# <a name="adaptive-streaming-with-playready"></a><span data-ttu-id="e50e6-104">Adaptives Streaming mit PlayReady</span><span class="sxs-lookup"><span data-stu-id="e50e6-104">Adaptive streaming with PlayReady</span></span>


<span data-ttu-id="e50e6-105">In diesem Artikel wird beschrieben, wie Sie einer UWP-App (Universelle Windows-Plattform) adaptives Streaming von Multimediainhalten mit Microsoft PlayReady-Inhaltsschutz hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e50e6-105">This article describes how to add adaptive streaming of multimedia content with Microsoft PlayReady content protection to a Universal Windows Platform (UWP) app.</span></span> 

<span data-ttu-id="e50e6-106">Dieses Feature unterstützt derzeit die Wiedergabe von Dynamic Streaming over HTTP (DASH)-Inhalten.</span><span class="sxs-lookup"><span data-stu-id="e50e6-106">This feature currently supports playback of Dynamic streaming over HTTP (DASH) content.</span></span>

<span data-ttu-id="e50e6-107">HLS (Apple HTTP Live Streaming) wird mit PlayReady nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="e50e6-107">HLS (Apple's HTTP Live Streaming) is not supported with PlayReady.</span></span>

<span data-ttu-id="e50e6-108">Smooth Streaming wird zurzeit ebenfalls nicht nativ unterstützt. PlayReady ist jedoch erweiterbar, und mithilfe von zusätzlichem Code oder zusätzlichen Bibliotheken kann PlayReady-geschütztes Smooth Streaming unterstützt werden, um die Nutzung von Software- oder sogar Hardware-DRM (Digital Rights Management) zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="e50e6-108">Smooth streaming is also currently not supported natively; however, PlayReady is extensible and by using additional code or libraries, PlayReady-protected Smooth streaming can be supported, leveraging software or even hardware DRM (digital rights management).</span></span>

<span data-ttu-id="e50e6-109">Dieser Artikel befasst sich nur mit den Aspekten des für PlayReady spezifischen adaptiven Streamings.</span><span class="sxs-lookup"><span data-stu-id="e50e6-109">This article only deals with the aspects of adaptive streaming specific to PlayReady.</span></span> <span data-ttu-id="e50e6-110">Informationen zur allgemeinen Implementierung des adaptiven Streamings finden Sie unter [Adaptives Streaming](adaptive-streaming.md).</span><span class="sxs-lookup"><span data-stu-id="e50e6-110">For information about implementing adaptive streaming in general, see [Adaptive streaming](adaptive-streaming.md).</span></span>

<span data-ttu-id="e50e6-111">In diesem Artikel wird Code aus dem [Beispiel zu adaptivem Streaming](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AdaptiveStreaming) im Microsoft-Repository **Beispiele für die Universelle Windows-Plattform** auf GitHub verwendet.</span><span class="sxs-lookup"><span data-stu-id="e50e6-111">This article uses code from the [Adaptive streaming sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AdaptiveStreaming) in Microsoft's **Windows-universal-samples** repository on GitHub.</span></span> <span data-ttu-id="e50e6-112">Szenario 4 behandelt adaptives Streaming mit PlayReady.</span><span class="sxs-lookup"><span data-stu-id="e50e6-112">Scenario 4 deals with using adaptive streaming with PlayReady.</span></span> <span data-ttu-id="e50e6-113">Sie können das Repository als ZIP-Datei herunterladen, indem Sie auf die Stammebene des Repository navigieren und die Schaltfläche **ZIP-Datei herunterladen** wählen.</span><span class="sxs-lookup"><span data-stu-id="e50e6-113">You can download the repo in a ZIP file by navigating to the root level of the repository and selecting the **Download ZIP** button.</span></span>

<span data-ttu-id="e50e6-114">Sie benötigen die folgenden **using**-Anweisungen:</span><span class="sxs-lookup"><span data-stu-id="e50e6-114">You will need the following **using** statements:</span></span>

```csharp
using LicenseRequest;
using System;
using System.Net.Http;
using System.Net.Http.Headers;
using System.Runtime.InteropServices;
using System.Threading.Tasks;
using Windows.Foundation.Collections;
using Windows.Media.Protection;
using Windows.Media.Protection.PlayReady;
using Windows.Media.Streaming.Adaptive;
using Windows.UI.Xaml.Controls;
```

<span data-ttu-id="e50e6-115">Der Namespace **LicenseRequest** stammt aus **CommonLicenseRequest.cs**, einer PlayReady-Datei, die Lizenznehmern von Microsoft zur Verfügung gestellt wird.</span><span class="sxs-lookup"><span data-stu-id="e50e6-115">The **LicenseRequest** namespace is from **CommonLicenseRequest.cs**, a PlayReady file provided by Microsoft to licensees.</span></span>

<span data-ttu-id="e50e6-116">Sie müssen einige globale Variablen deklarieren:</span><span class="sxs-lookup"><span data-stu-id="e50e6-116">You will need to declare a few global variables:</span></span>

```csharp
private AdaptiveMediaSource ams = null;
private MediaProtectionManager protectionManager = null;
private string playReadyLicenseUrl = "";
private string playReadyChallengeCustomData = "";
```

<span data-ttu-id="e50e6-117">Sie sollten auch die folgende Konstante deklarieren:</span><span class="sxs-lookup"><span data-stu-id="e50e6-117">You will also want to declare the following constant:</span></span>

```csharp
private const uint MSPR_E_CONTENT_ENABLING_ACTION_REQUIRED = 0x8004B895;
```

## <a name="setting-up-the-mediaprotectionmanager"></a><span data-ttu-id="e50e6-118">Einrichten von „MediaProtectionManager“</span><span class="sxs-lookup"><span data-stu-id="e50e6-118">Setting up the MediaProtectionManager</span></span>

<span data-ttu-id="e50e6-119">Um Ihrer UWP-App PlayReady-Inhaltsschutz hinzuzufügen, müssen Sie ein [MediaProtectionManager](https://msdn.microsoft.com/library/windows/apps/br207040)-Objekt einrichten.</span><span class="sxs-lookup"><span data-stu-id="e50e6-119">To add PlayReady content protection to your UWP app, you will need to set up a [MediaProtectionManager](https://msdn.microsoft.com/library/windows/apps/br207040) object.</span></span> <span data-ttu-id="e50e6-120">Diese Einrichtung erfolgt beim Initialisieren Ihres [**AdaptiveMediaSource**](https://msdn.microsoft.com/library/windows/apps/dn946912)-Objekts.</span><span class="sxs-lookup"><span data-stu-id="e50e6-120">You do this when initializing your [**AdaptiveMediaSource**](https://msdn.microsoft.com/library/windows/apps/dn946912) object.</span></span>

<span data-ttu-id="e50e6-121">Mit dem folgenden Code wird ein [MediaProtectionManager](https://msdn.microsoft.com/library/windows/apps/br207040)-Objekt eingerichtet:</span><span class="sxs-lookup"><span data-stu-id="e50e6-121">The following code sets up a [MediaProtectionManager](https://msdn.microsoft.com/library/windows/apps/br207040):</span></span>

```csharp
private void SetUpProtectionManager(ref MediaElement mediaElement)
{
    protectionManager = new MediaProtectionManager();

    protectionManager.ComponentLoadFailed += 
        new ComponentLoadFailedEventHandler(ProtectionManager_ComponentLoadFailed);

    protectionManager.ServiceRequested += 
        new ServiceRequestedEventHandler(ProtectionManager_ServiceRequested);

    PropertySet cpSystems = new PropertySet();

    cpSystems.Add(
        "{F4637010-03C3-42CD-B932-B48ADF3A6A54}", 
        "Windows.Media.Protection.PlayReady.PlayReadyWinRTTrustedInput");

    protectionManager.Properties.Add("Windows.Media.Protection.MediaProtectionSystemIdMapping", cpSystems);

    protectionManager.Properties.Add(
        "Windows.Media.Protection.MediaProtectionSystemId", 
        "{F4637010-03C3-42CD-B932-B48ADF3A6A54}");

    protectionManager.Properties.Add(
        "Windows.Media.Protection.MediaProtectionContainerGuid", 
        "{9A04F079-9840-4286-AB92-E65BE0885F95}");

    mediaElement.ProtectionManager = protectionManager;
}
```

<span data-ttu-id="e50e6-122">Dieser Code kann einfach in Ihre App kopiert werden, da er für die Einrichtung des Inhaltsschutzes erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="e50e6-122">This code can simply be copied to your app, since it is mandatory for setting up content protection.</span></span>

<span data-ttu-id="e50e6-123">Das [ComponentLoadFailed](https://msdn.microsoft.com/library/windows/apps/br207041)-Ereignis wird ausgelöst, wenn das Laden von Binärdaten fehlschlägt.</span><span class="sxs-lookup"><span data-stu-id="e50e6-123">The [ComponentLoadFailed](https://msdn.microsoft.com/library/windows/apps/br207041) event is fired when the load of binary data fails.</span></span> <span data-ttu-id="e50e6-124">Zum Behandeln dieses Ereignisses müssen wir einen Ereignishandler hinzufügen, der signalisiert, dass das Laden nicht abgeschlossen wurde:</span><span class="sxs-lookup"><span data-stu-id="e50e6-124">We need to add an event handler to handle this, signaling that the load did not complete:</span></span>

```csharp
private void ProtectionManager_ComponentLoadFailed(
    MediaProtectionManager sender, 
    ComponentLoadFailedEventArgs e)
{
    e.Completion.Complete(false);
}
```

<span data-ttu-id="e50e6-125">Ebenso müssen wir einen Ereignishandler für das [ServiceRequested](https://msdn.microsoft.com/library/windows/apps/br207045)-Ereignis hinzufügen, das beim Anfordern eines Diensts ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="e50e6-125">Similarly, we need to add an event handler for the [ServiceRequested](https://msdn.microsoft.com/library/windows/apps/br207045) event, which fires when a service is requested.</span></span> <span data-ttu-id="e50e6-126">Dieser Code überprüft, um welche Art von Anforderung es sich handelt, und reagiert entsprechend:</span><span class="sxs-lookup"><span data-stu-id="e50e6-126">This code checks what kind of request it is, and responds appropriately:</span></span>

```csharp
private async void ProtectionManager_ServiceRequested(
    MediaProtectionManager sender, 
    ServiceRequestedEventArgs e)
{
    if (e.Request is PlayReadyIndividualizationServiceRequest)
    {
        PlayReadyIndividualizationServiceRequest IndivRequest = 
            e.Request as PlayReadyIndividualizationServiceRequest;

        bool bResultIndiv = await ReactiveIndivRequest(IndivRequest, e.Completion);
    }
    else if (e.Request is PlayReadyLicenseAcquisitionServiceRequest)
    {
        PlayReadyLicenseAcquisitionServiceRequest licenseRequest = 
            e.Request as PlayReadyLicenseAcquisitionServiceRequest;

        LicenseAcquisitionRequest(
            licenseRequest, 
            e.Completion, 
            playReadyLicenseUrl, 
            playReadyChallengeCustomData);
    }
}
```

## <a name="individualization-service-requests"></a><span data-ttu-id="e50e6-127">Individualisierungsdienstanforderung</span><span class="sxs-lookup"><span data-stu-id="e50e6-127">Individualization service requests</span></span>

<span data-ttu-id="e50e6-128">Der folgende Code sendet reaktiv eine PlayReady-Individualisierungsdienstanforderung.</span><span class="sxs-lookup"><span data-stu-id="e50e6-128">The following code reactively makes a PlayReady individualization service request.</span></span> <span data-ttu-id="e50e6-129">Wir übergeben die Anforderung als Parameter an die Funktion.</span><span class="sxs-lookup"><span data-stu-id="e50e6-129">We pass in the request as a parameter to the function.</span></span> <span data-ttu-id="e50e6-130">Wir platzieren den Aufruf in einem try/catch-Block. Wenn keine Ausnahmen auftreten, wurde die Anforderung in unseren Augen erfolgreich abgeschlossen:</span><span class="sxs-lookup"><span data-stu-id="e50e6-130">We surround the call in a try/catch block, and if there are no exceptions, we say the request completed successfully:</span></span>

```csharp
async Task<bool> ReactiveIndivRequest(
    PlayReadyIndividualizationServiceRequest IndivRequest, 
    MediaProtectionServiceCompletion CompletionNotifier)
{
    bool bResult = false;
    Exception exception = null;

    try
    {
        await IndivRequest.BeginServiceRequest();
    }
    catch (Exception ex)
    {
        exception = ex;
    }
    finally
    {
        if (exception == null)
        {
            bResult = true;
        }
        else
        {
            COMException comException = exception as COMException;
            if (comException != null && comException.HResult == MSPR_E_CONTENT_ENABLING_ACTION_REQUIRED)
            {
                IndivRequest.NextServiceRequest();
            }
        }
    }

    if (CompletionNotifier != null) CompletionNotifier.Complete(bResult);
    return bResult;
}
```

<span data-ttu-id="e50e6-131">Alternativ soll vielleicht proaktiv eine Individualisierungsdienstanforderung gesendet werden. In diesem Fall wird anstelle des Codes, mit dem `ReactiveIndivRequest` in `ProtectionManager_ServiceRequested` aufgerufen wird, die folgende Funktion aufgerufen:</span><span class="sxs-lookup"><span data-stu-id="e50e6-131">Alternatively, we may want to proactively make an individualization service request, in which case we call the following function in place of the code calling `ReactiveIndivRequest` in `ProtectionManager_ServiceRequested`:</span></span>

```csharp
async void ProActiveIndivRequest()
{
    PlayReadyIndividualizationServiceRequest indivRequest = new PlayReadyIndividualizationServiceRequest();
    bool bResultIndiv = await ReactiveIndivRequest(indivRequest, null);
}
```

## <a name="license-acquisition-service-requests"></a><span data-ttu-id="e50e6-132">Lizenzerwerb-Dienstanforderungen</span><span class="sxs-lookup"><span data-stu-id="e50e6-132">License acquisition service requests</span></span>

<span data-ttu-id="e50e6-133">Falls es sich bei der Anforderung stattdessen um [PlayReadyLicenseAcquisitionServiceRequest](https://msdn.microsoft.com/library/windows/apps/dn986285) handelt, rufen wir die folgende Funktion auf, um die PlayReady-Lizenz anzufordern und zu erwerben.</span><span class="sxs-lookup"><span data-stu-id="e50e6-133">If instead the request was a [PlayReadyLicenseAcquisitionServiceRequest](https://msdn.microsoft.com/library/windows/apps/dn986285), we call the following function to request and acquire the PlayReady license.</span></span> <span data-ttu-id="e50e6-134">Wir teilen dem übergebenen **MediaProtectionServiceCompletion**-Objekt mit, ob die Anforderung erfolgreich war, und schließen die Anforderung ab:</span><span class="sxs-lookup"><span data-stu-id="e50e6-134">We tell the **MediaProtectionServiceCompletion** object that we passed in whether the request was successful or not, and we complete the request:</span></span>

```csharp
async void LicenseAcquisitionRequest(
    PlayReadyLicenseAcquisitionServiceRequest licenseRequest, 
    MediaProtectionServiceCompletion CompletionNotifier, 
    string Url, 
    string ChallengeCustomData)
{
    bool bResult = false;
    string ExceptionMessage = string.Empty;

    try
    {
        if (!string.IsNullOrEmpty(Url))
        {
            if (!string.IsNullOrEmpty(ChallengeCustomData))
            {
                System.Text.UTF8Encoding encoding = new System.Text.UTF8Encoding();
                byte[] b = encoding.GetBytes(ChallengeCustomData);
                licenseRequest.ChallengeCustomData = Convert.ToBase64String(b, 0, b.Length);
            }

            PlayReadySoapMessage soapMessage = licenseRequest.GenerateManualEnablingChallenge();

            byte[] messageBytes = soapMessage.GetMessageBody();
            HttpContent httpContent = new ByteArrayContent(messageBytes);

            IPropertySet propertySetHeaders = soapMessage.MessageHeaders;

            foreach (string strHeaderName in propertySetHeaders.Keys)
            {
                string strHeaderValue = propertySetHeaders[strHeaderName].ToString();

                if (strHeaderName.Equals("Content-Type", StringComparison.OrdinalIgnoreCase))
                {
                    httpContent.Headers.ContentType = MediaTypeHeaderValue.Parse(strHeaderValue);
                }
                else
                {
                    httpContent.Headers.Add(strHeaderName.ToString(), strHeaderValue);
                }
            }

            CommonLicenseRequest licenseAcquision = new CommonLicenseRequest();

            HttpContent responseHttpContent = 
                await licenseAcquision.AcquireLicense(new Uri(Url), httpContent);

            if (responseHttpContent != null)
            {
                Exception exResult = licenseRequest.ProcessManualEnablingResponse(
                                         await responseHttpContent.ReadAsByteArrayAsync());

                if (exResult != null)
                {
                    throw exResult;
                }
                bResult = true;
            }
            else
            {
                ExceptionMessage = licenseAcquision.GetLastErrorMessage();
            }
        }
        else
        {
            await licenseRequest.BeginServiceRequest();
            bResult = true;
        }
    }
    catch (Exception e)
    {
        ExceptionMessage = e.Message;
    }

    CompletionNotifier.Complete(bResult);
}
```

## <a name="initializing-the-adaptivemediasource"></a><span data-ttu-id="e50e6-135">Initialisieren von „AdaptiveMediaSource“</span><span class="sxs-lookup"><span data-stu-id="e50e6-135">Initializing the AdaptiveMediaSource</span></span>

<span data-ttu-id="e50e6-136">Schließlich benötigen Sie eine Funktion zum Initialisieren des [AdaptiveMediaSource](https://msdn.microsoft.com/library/windows/apps/dn946912)-Objekts, das aus einem bestimmten [Uri](https://msdn.microsoft.com/library/windows/apps/xaml/system.uri.aspx)- und [MediaElement](https://msdn.microsoft.com/library/windows/apps/br242926)-Objekt erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="e50e6-136">Finally, you will need a function to initialize the [AdaptiveMediaSource](https://msdn.microsoft.com/library/windows/apps/dn946912), created from a given [Uri](https://msdn.microsoft.com/library/windows/apps/xaml/system.uri.aspx) and [MediaElement](https://msdn.microsoft.com/library/windows/apps/br242926).</span></span> <span data-ttu-id="e50e6-137">Bei **Uri** sollte es sich um den Link zur Mediendatei (HLS oder DASH) handeln. **MediaElement** muss in Ihrem XAML-Code definiert werden.</span><span class="sxs-lookup"><span data-stu-id="e50e6-137">The **Uri** should be the link to the media file (HLS or DASH); the **MediaElement** should be defined in your XAML.</span></span>

```csharp
async private void InitializeAdaptiveMediaSource(System.Uri uri, MediaElement m)
{
    AdaptiveMediaSourceCreationResult result = await AdaptiveMediaSource.CreateFromUriAsync(uri);
    if (result.Status == AdaptiveMediaSourceCreationStatus.Success)
    {
        ams = result.MediaSource;
        SetUpProtectionManager(ref m);
        m.SetMediaStreamSource(ams);
    }
    else
    {
        // Error handling
    }
}
```

<span data-ttu-id="e50e6-138">Sie können diese Funktion in jedem Ereignis aufrufen, das den Start des adaptiven Streamings behandelt, z.B. in einem Click-Ereignis für eine Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="e50e6-138">You can call this function in whichever event handles the start of adaptive streaming; for example, in a button click event.</span></span>

## <a name="see-also"></a><span data-ttu-id="e50e6-139">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="e50e6-139">See also</span></span>
- [<span data-ttu-id="e50e6-140">PlayReady DRM</span><span class="sxs-lookup"><span data-stu-id="e50e6-140">PlayReady DRM</span></span>](playready-client-sdk.md)




