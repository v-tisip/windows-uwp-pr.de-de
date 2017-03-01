---
title: Biometrischer Fingerabdruck
description: "In diesem Artikel wird beschrieben, wie Sie Biometrie für Fingerabdrücke in Ihrer UWP-App (Universelle Windows-Plattform) verarbeiten können."
ms.assetid: 55483729-5F8A-401A-8072-3CD611DDFED2
author: awkoren
ms.author: alkoren
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP"
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 84e191df23f10f81a3588662f9ba1505cee12e21
ms.lasthandoff: 02/07/2017

---

# <a name="fingerprint-biometrics"></a>Biometrischer Fingerabdruck


\[ Aktualisiert für UWP-Apps unter Windows 10. Artikel zu Windows 8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132). \]


In diesem Artikel wird beschrieben, wie Sie Biometrie für Fingerabdrücke in Ihrer UWP-App (Universelle Windows-Plattform) verarbeiten können. Sie können die Sicherheit Ihrer App erhöhen, indem Sie die Anforderung einer Authentifizierung per Fingerabdruck integrieren, wenn die Zustimmung des Benutzers für eine bestimmte Aktion erforderlich ist. So können Sie beispielsweise die Authentifizierung per Fingerabdruck vor der Autorisierung eines In-App-Kaufs oder vor dem Zugriff auf eingeschränkte Ressourcen anfordern. Die Verwaltung der Authentifizierung per Fingerabdruck erfolgt mithilfe der [**UserConsentVerifier**](https://msdn.microsoft.com/library/windows/apps/dn279134)-Klasse im [**Windows.Security.Credentials.UI**](https://msdn.microsoft.com/library/windows/apps/hh701356)-Namespace.

## <a name="check-the-device-for-a-fingerprint-reader"></a>Suchen nach einem Fingerabdruckleser


Durch Aufrufen der [**UserConsentVerifier.CheckAvailabilityAsync**](https://msdn.microsoft.com/library/windows/apps/dn279138)-Methode kann ermittelt werden, ob das Gerät über einen Fingerabdruckleser verfügt. Auch wenn ein Gerät die Authentifizierung per Fingerabdruck unterstützt, sollte die App in den Einstellungen eine Option enthalten, mit der die Authentifizierung per Fingerabdruck aktiviert oder deaktiviert werden kann.

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

## <a name="request-consent-and-return-results"></a>Anfordern der Zustimmung und Zurückgeben von Ergebnissen


Wenn Sie die Benutzerzustimmung mithilfe eines Fingerabdruckscans anfordern möchten, rufen Sie die [**UserConsentVerifier.RequestVerificationAsync**](https://msdn.microsoft.com/library/windows/apps/dn279139)-Methode auf. Damit die Authentifizierung per Fingerabdruck funktioniert, muss der Benutzer vorher einen Fingerabdruck in der Fingerabdruckdatenbank hinterlegt haben.

Beim Aufrufen von [**UserConsentVerifier.RequestVerificationAsync**](https://msdn.microsoft.com/library/windows/apps/dn279139) wird dem Benutzer ein modales Dialogfeld angezeigt, in dem ein Fingerabdruckscan angefordert wird. Sie können in der Methode **UserConsentVerifier.RequestVerificationAsync** eine Meldung bereitstellen, die dem Benutzer im modalen Dialogfeld angezeigt wird (siehe folgende Abbildung).

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
