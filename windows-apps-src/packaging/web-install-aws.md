---
author: laurenhughes
title: Hosten von UWP-App-Paketen auf AWS für die Webinstallation
description: Lernprogramm für die AWS-Webserver einrichten, Überprüfen von app-Installation über App-Installer-App
ms.author: cdon
ms.date: 05/30/2018
ms.topic: article
keywords: Windows 10, Windows 10, UWP, app-Installer, AppInstaller, querladen, im Zusammenhang mit festgelegten optionale Pakete, AWS
ms.localizationpriority: medium
ms.openlocfilehash: f24abac93e2444a3c9f454c8883902e5db4d31be
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6967898"
---
# <a name="hosting-uwp-app-packages-on-aws-for-web-install"></a>Hosten von UWP-App-Paketen auf AWS für die Webinstallation

Mit der App-Installer-App können Entwickler und IT-Spezialisten Windows10-Apps verteilen, indem sie diese in ihrem eigenen Content Delivery Network (CDN) hosten. Das ist nützlich für Unternehmen, die ihre Apps nicht im Microsoft Store veröffentlichen möchten oder müssen, aber weiterhin die Windows10-Verpackungs- und -Bereitstellungsplattform nutzen möchten.

In diesem Thema werden die Schritte zum Konfigurieren einer Website Amazon Web Services (AWS), um UWP-app-Pakete hosten und wie Sie die App-Installer-app verwenden, um die app-Pakete zu installieren.

## <a name="setup"></a>Setup

Für eine erfolgreiche Durchführung dieses Lernprogramms benötigen Sie Folgendes:
 
1. AWS Abonnement 
2. Webseite
3. UWP-App-Paket – das App-Paket, die Sie verteilen möchten

Optional: [Startprojekt](https://github.com/AppInstaller/MySampleWebApp) auf GitHub. Dies ist hilfreich, wenn Sie kein App-Paket oder keine Webseite zum Arbeiten verfügbar haben, aber dennoch lernen möchten, wie Sie dieses Feature verwenden.

In diesem Lernprogramm wird über eine Webseite und Host-Paketen auf AWS einrichten geleitet. Dies ist ein AWS-Abonnement erforderlich. Je nach der Skalierung der des Vorgangs können Sie ihre kostenlose Mitgliedschaft verwenden, um dieses Lernprogramms. 

## <a name="step-1---aws-membership"></a>Schritt 1: AWS-Mitgliedschaft
Um eine AWS-Mitgliedschaft erhalten, finden Sie auf der [Detailseite für das Konto AWS](https://aws.amazon.com/free/). Für die Zwecke dieses Lernprogramms können Sie eine kostenlose Mitgliedschaft verwenden.

## <a name="step-2---create-an-amazon-s3-bucket"></a>Schritt 2: Erstellen einer Amazon S3 Buckets

Amazon Simple Storage Service (S3) ist eine Lösung für die Erfassung, speichern und Analysieren von Daten AWS. S3 Buckets handelt es sich um eine praktische Möglichkeit zum UWP-app-Pakete hosten und Webseiten für die Verteilung. 

Nach der Anmeldung an AWS mit Ihren Anmeldeinformationen unter `Services` suchen `S3`. 

Wählen Sie **Buckets erstellen**, und geben Sie einen **Namen Buckets** für Ihre Website. Befolgen Sie die Anweisungen im Dialogfeld zum Festlegen von Eigenschaften und Berechtigungen. Um sicherzustellen, dass Ihre UWP-app aus Ihrer Website verteilt werden kann, aktivieren Sie **Lesen** und **Schreiben** von Berechtigungen für Ihre Buckets zu, und wählen Sie **Öffentliche Lesezugriff auf dieser Zelle gewähren**.

![Festlegen von Berechtigungen für Amazon S3 Buckets](images/aws-permissions.png) 

Überprüfen Sie die Zusammenfassung, um sicherzustellen, dass die ausgewählten Optionen angezeigt werden. Klicken Sie auf **Buckets erstellen** , um diesen Schritt abgeschlossen haben. 

## <a name="step-3---upload-uwp-app-package-and-web-pages-to-an-s3-bucket"></a>Schritt 3: Hochladen von UWP-app-Paket und Webseiten in einer S3 Buckets

Eine haben Sie eine Amazon S3 Buckets erstellt, können in Ihrer Amazon S3-Ansicht angezeigt. Hier ist ein Beispiel wie unsere Demo Buckets aussieht:

![Amazon S3 Buckets Ansicht](images/aws-post-create.png)

Wir sind jetzt Hochladen der app-Pakete und Webseiten, die wir in unserem Amazon S3 Buckets hosten möchten. 

Klicken Sie auf die neu erstellte Buckets zum Hochladen von Inhalten. Die Buckets ist derzeit leer, da nichts noch nicht hochgeladen wurde. Klicken Sie auf die Schaltfläche **Hochladen** , und wählen Sie die app-Pakete und die Webseite-Dateien, die Sie hochladen möchten.

> [!NOTE]
> Sie können das App-Paket verwenden, das Teil des bereitgestellten [Startprojekt](https://github.com/AppInstaller/MySampleWebApp)-Repositorys auf GitHub ist, falls Ihnen kein App-Paket zur Verfügung steht. Die Zertifikat (MySampleApp.cer), mit dem das Paket signiert wurde, ist ebenfalls im Beispiel auf GitHub enthalten. Sie müssen das Zertifikat vor der Installation der App auf Ihrem Gerät installieren.

![Hochladen von app-Paket](images/aws-upload-package.png)

Ähnlich wie die Berechtigungen für die Erstellung einer Amazon S3 Buckets, muss der Inhalt der Buckets auch **Lesen**, **Schreiben**und **öffentlichen Lesezugriff auf diese Objekte Grant** -Berechtigungen verfügen.

Wenn Sie Testen einer Webseite hochladen möchten, aber nicht eine haben, können Sie die Beispiel-html-Seite (default.html) aus dem [Startprojekt](https://github.com/AppInstaller/MySampleWebApp/blob/master/MySampleWebApp/default.html).

> [!IMPORTANT]
> Bevor Sie die Webseite hochgeladen haben, stellen Sie sicher, dass die app-Paket auf der Webseite korrekt sind. 

Zum Abrufen der Referenz zur app-Paket zuerst Hochladen von app-Paket, und kopieren Sie die app-Paket-URL. Bearbeiten Sie die html-Webseite entsprechend den Pfad der richtigen app-Paket. Finden Sie im Codebeispiel für weitere Details. 

Wählen Sie die hochgeladenen app-Paket-Datei auf den Referenzlink zum app-Paket abrufen, ähnlich wie in diesem Beispiel wird:

![hochgeladene Paketpfad](images/aws-package-path.png)

**Kopieren** der Link zur app Verpacken und fügen Sie den Verweis auf der Webseite hinzu. 

```html
<html>
    <head>
        <meta charset="utf-8" />
        <title> Install My Sample App</title>
    </head>
    <body>
        <a href="ms-appinstaller:?source=https://s3-us-west-2.amazonaws.com/appinstaller-aws-demo/MySampleApp.appxbundle"> Install My Sample App</a>
    </body>
</html>
```
Hochladen der HTML-Datei für Ihre Amazon S3 Buckets. Denken Sie daran, die Berechtigungen zum **Lesen** und **Schreiben** Zugriff zu ermöglichen.

## <a name="step-4---test"></a>Schritt 4: Test

Nachdem der Webseite in Ihre Amazon S3 Buckets hochgeladen wurde, rufen Sie den Link zu der Webseite durch die Auswahl der hochgeladenen HTML-Datei.

Verwenden Sie den Link, um die Webseite zu öffnen. Da wir Berechtigungen gewähren öffentlichen Zugriff auf die app-Paket und die Webseite festgelegt, kann alle Personen mit einem Link zu der Webseite darauf zugreifen, und installieren Ihre UWP-app-Pakete mithilfe von App-Installer. Beachten Sie, dass App-Installer Teil von Windows 10-Plattform ist. Als Entwickler müssen Sie keine Features oder zusätzlichen Code zu Ihrer app für die Verwendung der App-Installer ermöglichen hinzufügen. 

## <a name="troubleshooting"></a>Fehlerbehebung

### <a name="app-installer-fails-to-install"></a>App-Installer Fehler bei der Installation 

App-Installation schlägt fehl, wenn das Zertifikat, dem das app-Paket signiert ist nicht auf dem Gerät installiert ist. Um dieses Problem zu beheben, müssen Sie das Zertifikat vor der Installation der App installieren. Wenn Sie ein app-Paket für die öffentliche Verteilung hosten, hat es empfohlen, um Ihr app-Paket mit einem Zertifikat von einer Zertifizierungsstelle zu signieren. 


