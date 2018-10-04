---
title: Biometrischer Fingerabdruck
description: In diesem Artikel wird erläutert, wie Sie die Funktion des biometrischen Fingerabdrucks in Ihrer UWP-App (Universelle Windows-Plattform) hinzufügen.
ms.assetid: 55483729-5F8A-401A-8072-3CD611DDFED2
author: PatrickFarley
ms.author: pafarley
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Sicherheit
ms.localizationpriority: medium
ms.openlocfilehash: 287b2b0fedac112f57f0342420a7830db5aa13be
ms.sourcegitcommit: 5c9a47b135c5f587214675e39c1ac058c0380f4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2018
ms.locfileid: "4353193"
---
# <a name="fingerprint-biometrics"></a><span data-ttu-id="39b7c-104">Biometrischer Fingerabdruck</span><span class="sxs-lookup"><span data-stu-id="39b7c-104">Fingerprint biometrics</span></span>




<span data-ttu-id="39b7c-105">In diesem Artikel wird erläutert, wie Sie die Funktion des biometrischen Fingerabdrucks in Ihrer UWP-App (Universelle Windows-Plattform) hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="39b7c-105">This article explains how to add fingerprint biometrics to your Universal Windows Platform (UWP) app.</span></span> <span data-ttu-id="39b7c-106">Sie können die Sicherheit Ihrer App erhöhen, indem Sie die Anforderung einer Authentifizierung per Fingerabdruck integrieren, wenn die Zustimmung des Benutzers für eine bestimmte Aktion erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="39b7c-106">Including a request for fingerprint authentication when the user must consent to a particular action increases the security of your app.</span></span> <span data-ttu-id="39b7c-107">So können Sie beispielsweise die Authentifizierung per Fingerabdruck vor der Autorisierung eines In-App-Kaufs oder vor dem Zugriff auf eingeschränkte Ressourcen anfordern.</span><span class="sxs-lookup"><span data-stu-id="39b7c-107">For example, you could require fingerprint authentication before authorizing an in-app purchase, or access to restricted resources.</span></span> <span data-ttu-id="39b7c-108">Die Verwaltung der Authentifizierung per Fingerabdruck erfolgt mithilfe der [**UserConsentVerifier**](https://msdn.microsoft.com/library/windows/apps/dn279134)-Klasse im [**Windows.Security.Credentials.UI**](https://msdn.microsoft.com/library/windows/apps/hh701356)-Namespace.</span><span class="sxs-lookup"><span data-stu-id="39b7c-108">Fingerprint authentication is managed using the [**UserConsentVerifier**](https://msdn.microsoft.com/library/windows/apps/dn279134) class in the [**Windows.Security.Credentials.UI**](https://msdn.microsoft.com/library/windows/apps/hh701356) namespace.</span></span>

## <a name="check-the-device-for-a-fingerprint-reader"></a><span data-ttu-id="39b7c-109">Suchen nach einem Fingerabdruckleser</span><span class="sxs-lookup"><span data-stu-id="39b7c-109">Check the device for a fingerprint reader</span></span>


<span data-ttu-id="39b7c-110">Durch Aufrufen der [**UserConsentVerifier.CheckAvailabilityAsync**](https://msdn.microsoft.com/library/windows/apps/dn279138)-Methode kann ermittelt werden, ob das Gerät über einen Fingerabdruckleser verfügt.</span><span class="sxs-lookup"><span data-stu-id="39b7c-110">To find out whether the device has a fingerprint reader, call [**UserConsentVerifier.CheckAvailabilityAsync**](https://msdn.microsoft.com/library/windows/apps/dn279138).</span></span> <span data-ttu-id="39b7c-111">Auch wenn ein Gerät die Authentifizierung per Fingerabdruck unterstützt, sollte die App in den Einstellungen eine Option enthalten, mit der die Authentifizierung per Fingerabdruck aktiviert oder deaktiviert werden kann.</span><span class="sxs-lookup"><span data-stu-id="39b7c-111">Even if a device supports fingerprint authentication, your app should still provide users with an option in Settings to enable or disable it.</span></span>

```cs
public async System.Threading.Tasks.Task<string> CheckFingerprintAvailability()
{
    string returnMessage = "";

    try
    {
        // Check the availability of fingerprint authentication.
        var ucvAvailability = await Windows.Security.Credentials.UI.UserConsentVerifier.CheckAvailabilityAsync();

        switch (ucvAvailability)
        {
            case Windows.Security.Credentials.UI.UserConsentVerifierAvailability.Available:
                returnMessage = "Fingerprint verification is available.";
                break;
            case Windows.Security.Credentials.UI.UserConsentVerifierAvailability.DeviceBusy:
                returnMessage = "Biometric device is busy.";
                break;
            case Windows.Security.Credentials.UI.UserConsentVerifierAvailability.DeviceNotPresent:
                returnMessage = "No biometric device found.";
                break;
            case Windows.Security.Credentials.UI.UserConsentVerifierAvailability.DisabledByPolicy:
                returnMessage = "Biometric verification is disabled by policy.";
                break;
            case Windows.Security.Credentials.UI.UserConsentVerifierAvailability.NotConfiguredForUser:
                returnMessage = "The user has no fingerprints registered. Please add a fingerprint to the " +
                                "fingerprint database and try again.";
                break;
            default:
                returnMessage = "Fingerprints verification is currently unavailable.";
                break;
        }
    }
    catch (Exception ex)
    {
        returnMessage = "Fingerprint authentication availability check failed: " + ex.ToString();
    }

    return returnMessage;
}
```

## <a name="request-consent-and-return-results"></a><span data-ttu-id="39b7c-112">Anfordern der Zustimmung und Zurückgeben von Ergebnissen</span><span class="sxs-lookup"><span data-stu-id="39b7c-112">Request consent and return results</span></span>


<span data-ttu-id="39b7c-113">Wenn Sie die Benutzerzustimmung mithilfe eines Fingerabdruckscans anfordern möchten, rufen Sie die [**UserConsentVerifier.RequestVerificationAsync**](https://msdn.microsoft.com/library/windows/apps/dn279139)-Methode auf.</span><span class="sxs-lookup"><span data-stu-id="39b7c-113">To request user consent from a fingerprint scan, call the [**UserConsentVerifier.RequestVerificationAsync**](https://msdn.microsoft.com/library/windows/apps/dn279139) method.</span></span> <span data-ttu-id="39b7c-114">Damit die Authentifizierung per Fingerabdruck funktioniert, muss der Benutzer vorher einen Fingerabdruck in der Fingerabdruckdatenbank hinterlegt haben.</span><span class="sxs-lookup"><span data-stu-id="39b7c-114">For fingerprint authentication to work, the user must have previously added a fingerprint "signature" to the fingerprint database.</span></span>

<span data-ttu-id="39b7c-115">Beim Aufrufen von [**UserConsentVerifier.RequestVerificationAsync**](https://msdn.microsoft.com/library/windows/apps/dn279139) wird dem Benutzer ein modales Dialogfeld angezeigt, in dem ein Fingerabdruckscan angefordert wird.</span><span class="sxs-lookup"><span data-stu-id="39b7c-115">When you call the [**UserConsentVerifier.RequestVerificationAsync**](https://msdn.microsoft.com/library/windows/apps/dn279139), the user is presented with a modal dialog requesting a fingerprint scan.</span></span> <span data-ttu-id="39b7c-116">Sie können in der Methode **UserConsentVerifier.RequestVerificationAsync** eine Meldung bereitstellen, die dem Benutzer im modalen Dialogfeld angezeigt wird (siehe folgende Abbildung).</span><span class="sxs-lookup"><span data-stu-id="39b7c-116">You can supply a message to the **UserConsentVerifier.RequestVerificationAsync** method that will be displayed to the user as part of the modal dialog, as shown in the following image.</span></span>

```cs
private async System.Threading.Tasks.Task<string> RequestConsent(string userMessage)
{
    string returnMessage;

    if (String.IsNullOrEmpty(userMessage))
    {
        userMessage = "Please provide fingerprint verification.";
    }

    try
    {
        // Request the logged on user's consent via fingerprint swipe.
        var consentResult = await Windows.Security.Credentials.UI.UserConsentVerifier.RequestVerificationAsync(userMessage);

        switch (consentResult)
        {
            case Windows.Security.Credentials.UI.UserConsentVerificationResult.Verified:
                returnMessage = "Fingerprint verified.";
                break;
            case Windows.Security.Credentials.UI.UserConsentVerificationResult.DeviceBusy:
                returnMessage = "Biometric device is busy.";
                break;
            case Windows.Security.Credentials.UI.UserConsentVerificationResult.DeviceNotPresent:
                returnMessage = "No biometric device found.";
                break;
            case Windows.Security.Credentials.UI.UserConsentVerificationResult.DisabledByPolicy:
                returnMessage = "Biometric verification is disabled by policy.";
                break;
            case Windows.Security.Credentials.UI.UserConsentVerificationResult.NotConfiguredForUser:
                returnMessage = "The user has no fingerprints registered. Please add a fingerprint to the " +
                                "fingerprint database and try again.";
                break;
            case Windows.Security.Credentials.UI.UserConsentVerificationResult.RetriesExhausted:
                returnMessage = "There have been too many failed attempts. Fingerprint authentication canceled.";
                break;
            case Windows.Security.Credentials.UI.UserConsentVerificationResult.Canceled:
                returnMessage = "Fingerprint authentication canceled.";
                break;
            default:
                returnMessage = "Fingerprint authentication is currently unavailable.";
                break;
        }
    }
    catch (Exception ex)
    {
        returnMessage = "Fingerprint authentication failed: " + ex.ToString();
    }

    return returnMessage;
}
```