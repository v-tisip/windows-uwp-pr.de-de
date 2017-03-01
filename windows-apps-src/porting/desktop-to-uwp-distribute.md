---
author: awkoren
Description: "Verteilen Ihrer UWP-App, die mit der Desktop-zu-UWP-Brücke konvertiert wurde"
Search.Product: eADQiWindows 10XVcnh
title: "Verteilen Ihrer UWP-App, die mit der Desktop-zu-UWP-Brücke konvertiert wurde"
ms.author: alkoren
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
ms.assetid: edff3787-cecb-4054-9a2d-1fbefa79efc4
translationtype: Human Translation
ms.sourcegitcommit: 5645eee3dc2ef67b5263b08800b0f96eb8a0a7da
ms.openlocfilehash: 0acb144d79c1d05d68cc7430f4cc99efeadc7c6b
ms.lasthandoff: 02/08/2017

---

# <a name="distribute-apps-converted-with-the-desktop-bridge"></a>Verteilen von Apps, die mit der Desktop-Brücke konvertiert wurden

Es gibt drei Möglichkeiten für die Bereitstellung Ihrer konvertierten App: Bereitstellen im Windows Store, Querladen und Registrieren loser Dateien.  

## <a name="windows-store"></a>Windows Store

Der Windows Store ist die bequemste Möglichkeit für Kunden, Ihre App zu beziehen. Füllen Sie zunächst das Formular unter [Bereitstellen vorhandener Apps und Spiele im Windows Store mithilfe der Desktopbrücke](https://developer.microsoft.com/windows/projects/campaigns/desktop-bridge) aus. Microsoft wird Sie kontaktieren, um den Onboardingprozess zu starten. 

Beachten Sie, dass Sie der Entwickler und/oder Herausgeber der Anwendung oder des Spiels sein müssen, um sie bzw. es im Windows Store bereitstellen zu können. Stellen Sie daher sicher, dass Ihr Name und die E-Mail-Adresse mit der Website übereinstimmen, die Sie unten als URL übermitteln, sodass wir bestätigen können, dass Sie der Entwickler und/oder Herausgeber sind.

## <a name="sideloading"></a>Querladen

Das Querladen ist eine einfache Möglichkeit für die Bereitstellung auf mehreren Computern. Es ist insbesondere in Unternehmens-/Branchenszenarien nützlich, in denen Sie eine bessere Kontrolle über den Verteilungsprozess wünschen, sich aber nicht mit Store-Zertifikaten auseinandersetzen möchten.

Bevor Sie Ihre App per Querladen bereitstellen, müssen Sie sie mit einem Zertifikat signieren. Informationen zum Erstellen eines Zertifikats finden Sie unter [Signieren des Appx-Pakets](https://msdn.microsoft.com/windows/uwp/porting/desktop-to-uwp-run-desktop-app-converter#deploy-your-converted-appx). 

Im Folgenden wird beschrieben, wie Sie ein Zertifikat importieren, das Sie zuvor erstellt haben. Sie können das Zertifikat mit CERTUTIL direkt importieren oder wie der Kunde von einem APPX-Projekt installieren, das Sie signiert haben. 

Um das Zertifikat über CERTUTIL zu installieren, führen Sie über eine Eingabeaufforderung mit Administratorrechten folgenden Befehl aus:

```cmd
Certutil -addStore TrustedPeople <testcert.cer>
```

So importieren Sie das Zertifikat wie ein Kunde aus dem APPX-Projekt:

1.    Klicken Sie im Datei-Explorer mit der rechten Maustaste auf ein APPX-Projekt, das Sie mit einem Testzertifikat signiert haben, und wählen Sie im Kontextmenü **Eigenschaften** aus.
2.    Klicken oder tippen Sie auf die Registerkarte **Digitale Signaturen**.
3.    Klicken oder tippen Sie auf das Zertifikat, und wählen Sie **Details**.
4.    Klicken oder tippen Sie auf **Zertifikat anzeigen**.
5.    Klicken oder tippen Sie auf **Zertifikat installieren**.
6.    Wählen Sie in der Gruppe **Speicherort** die Option **Lokaler Computer**.
7.    Klicken oder tippen Sie auf **Weiter** und **OK**, um das UAC-Dialogfeld zu bestätigen.
8.    Ändern Sie auf dem nächsten Bildschirm des Zertifikatimport-Assistenten die Optionsauswahl zu **Alle Zertifikate in folgendem Speicher speichern**.
9.    Klicken oder tippen Sie auf **Durchsuchen**. Scrollen Sie im Fenster „Zertifikatspeicher auswählen“ nach unten, wählen Sie die Option **Vertrauenswürdige Personen** aus, und tippen Sie dann auf **OK**.
10.    Klicken oder tippen Sie auf **Weiter**. Ein neuer Bildschirm wird angezeigt. Klicken oder tippen Sie auf **Fertig stellen**.
11.    Ein Bestätigungsdialogfeld sollte angezeigt werden. Wenn dies der Fall ist, klicken Sie auf **OK**. Gibt ein anderes Dialogfeld an, dass ein Problem mit dem Zertifikat vorliegt, müssen Sie mögliche Zertifikatfehler behandeln.

Hinweis: Damit Windows dem Zertifikat vertraut, muss sich das Zertifikat entweder im Knoten **Zertifikate (lokaler Computer) > Vertrauenswürdige Stammzertifizierungsstellen > Zertifikate** oder **Zertifikate (lokaler Computer) > Vertrauenswürdige Personen > Zertifikate** befinden. Nur Zertifikaten, die sich in diesen Speicherorten befinden, können auf dem lokalen Computer als vertrauenswürdige Zertifikate festgelegt werden. Andernfalls wird eine Fehlermeldung angezeigt, die der folgenden ähnelt:

```CMD
"Add-AppxPackage : Deployment failed with HRESULT: 0x800B0109, A certificate chain processed,
but terminated in a rootcertificate which is not trusted by the trust provider.
(Exception from HRESULT: 0x800B0109) error 0x800B0109: The root certificate of the signature
in the app package must be trusted."
```

Nachdem das Zertifikat nun als vertrauenswürdig eingestuft wird, gibt es zwei Möglichkeiten, das Paket zu installieren: über PowerShell oder einfach durch Doppelklicken auf die APPX-Paketdatei.  Führen Sie zur Installation über PowerShell das folgende Cmdlet aus:

```powershell
Add-AppxPackage <MyApp>.appx
```

### <a name="loose-file-registration"></a>Registrieren loser Dateien

Das Registrieren loser Dateien eignet sich für das Debuggen, wenn sich die Dateien auf dem Datenträger an einem Ort befinden, der mühelos aktualisiert werden kann und auf den Sie einfach sowie ohne Signatur und Zertifikat zugreifen können.  

Führen Sie zum Bereitstellen der App während der Entwicklung das folgende PowerShell-Cmdlet aus: 

```Add-AppxPackage –Register AppxManifest.xml```

Ersetzen Sie zum Aktualisieren der EXE- oder DLL-Dateien Ihrer App die vorhandenen Dateien in Ihrem Paket einfach durch die neuen, vergrößern Sie die Versionsnummer in der Datei „AppxManifest.xml“, und führen Sie den oben genannten Befehl erneut aus.

Hinweis: 

* Das Laufwerk, auf dem Sie die konvertierte App installieren, muss das NTFS-Format aufweisen.
* Eine konvertierte App wird immer als interaktiver Benutzer ausgeführt.
