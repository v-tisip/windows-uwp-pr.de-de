---
Description: The Microsoft Store Services SDK provides libraries and tools that you can use to add features to your apps that help you make more money and gain customers.
title: Kundengewinnung mit Microsoft Store Services SDK
ms.assetid: 518516DB-70A7-49C4-B3B6-CD8A98320B9C
ms.date: 08/21/2017
ms.topic: article
keywords: Windows10, UWP, Microsoft Store Services SDK
ms.localizationpriority: medium
ms.openlocfilehash: 8394a1a44173541e8982a660591e84b25b985205
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7718451"
---
# <a name="engage-customers-with-the-microsoft-store-services-sdk"></a>Kundengewinnung mit Microsoft Store Services SDK

Im Microsoft Store Services SDK bietet Features, mit denen Sie besser mit Kunden interagieren in Ihre universelle Windows-Plattform (UWP)-apps, z. B. benutzerorientierte Benachrichtigungen an Ihre apps senden und Ausführen von A / B-Experimente in Ihren apps durchführen. Dieses SDK ist eine Erweiterung für Visual Studio2015 und neuere Versionen von Visual Studio.

> [!NOTE]
> Verwenden Sie zum Anzeigen von Werbung in Ihren UWP-Apps das [Microsoft Advertising-SDK](http://aka.ms/ads-sdk-uwp) anstelle des Microsoft Store Services SDK. Die Advertising-Bibliotheken wurden von Microsoft Store Services SDK auf Microsoft Advertising-SDK verschoben. Weitere Informationen finden Sie unter [Anzeigen von Werbung in Ihrer App](display-ads-in-your-app.md).



## <a name="scenarios-supported-by-the-microsoft-store-services-sdk"></a>Durch das Microsoft Store Services SDK unterstützte Szenarien

Das Microsoft Store Services SDK unterstützt derzeit die folgenden Szenarien für UWP-Apps. Die API-Referenzdokumentation finden Sie unter [Microsoft Store Services SDK-API-Referenz](https://docs.microsoft.com/uwp/api/overview/engagement).

|  Szenario  |  Beschreibung   |
|------------|----------------|
|  [Durchführen von Experimenten mit A/B-Tests in Ihrer UWP-App](run-app-experiments-with-a-b-testing.md)    |  Führen Sie A/B-Tests in Ihrer App für die universelle Windows-Plattform (UWP) aus, um die Effektivität der Features für einige Kunden zu messen, bevor Sie die Features für alle Benutzer freigeben. Nachdem Sie ein Experiment im Partner Center definiert haben, verwenden Sie die [StoreServicesExperimentVariation](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesexperimentvariation) -Klasse zum Abrufen von Varianten für Ihr Experiment in Ihrer app, verwenden Sie diese Daten zum Ändern des Verhaltens des Features, die Sie testen möchten, und verwenden Sie dann die [LogForVariation ](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicescustomeventlogger.logforvariation)-Methode zum Senden des anzeigeereignisses und der umwandlungsereignisse in das Partner Center. Verwenden Sie zum Schluss Partner Center, um die Ergebnisse anzeigen und Verwalten des Experiments.  |
|  [Starten des Feedback-Hubs über Ihre UWP-App](launch-feedback-hub-from-your-app.md)    |  Verwenden Sie die [StoreServicesFeedbackLauncher](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesfeedbacklauncher)-Klasse in Ihrer UWP-App, um Ihre Windows10-Kunden auf den Feedback-Hub zu verweisen. Dort können Kunden ihre Probleme und Vorschläge übermitteln und das Feedback anderer Benutzer lesen und bewerten. Verwalten Sie anschließend dieses Feedback im [Feedback-Bericht](../publish/feedback-report.md) in Partner Center. |
|  [Konfigurieren Sie Ihre UWP-app zum Empfangen von Partner Center-Pushbenachrichtigungen](configure-your-app-to-receive-dev-center-notifications.md)    |  Verwenden Sie die [StoreServicesEngagementManager](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesengagementmanager) -Klasse in Ihrer UWP-app, registrieren Sie Ihre app für benutzerorientierte Pushbenachrichtigungen empfangen, die Sie für Ihre Kunden mithilfe von Partner Center zu senden.  |
|   [Protokollieren Sie benutzerdefinierte Ereignisse in Ihrer UWP-app für den Bericht "Nutzung" im Partner Center](log-custom-events-for-dev-center.md)   |  Verwenden Sie die [StoreServicesCustomEventLogger](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicescustomeventlogger.log) -Klasse in Ihrer UWP-app, um benutzerdefinierte Ereignisse zu protokollieren, die Ihre app im Partner Center zugeordnet sind. Überprüfen Sie dann alle Instanzen für Ihre benutzerdefinierten Ereignisse im Abschnitt **benutzerdefinierte Ereignisse** im [Bericht "Nutzung"](https://msdn.microsoft.com/windows/uwp/publish/usage-report) im Partner Center.  |

<span id="prerequisites" />

## <a name="prerequisites"></a>Voraussetzungen

Das Microsoft Store Services SDK erfordert:

* Visual Studio2015 oder eine neuere Version.
* Visual Studio-Tools für universelle Windows-Apps, installiert mit Ihrer Version von Visual Studio.

<span id="install" />

## <a name="install-the-sdk"></a>Installieren des SDK

Es gibt zwei Optionen zum Installieren des Microsoft Store Services SDKs auf Ihrem Entwicklungscomputer:

* **MSI-Installer**&nbsp;&nbsp;Sie können das SDK über das [hier](http://aka.ms/store-em-sdk) verfügbare MSI-Installationsprogramm installieren.
* **NuGet-Paket**&nbsp;&nbsp;Sie können das SDK als NuGet-Paket installieren.

Microsoft veröffentlicht in regelmäßigen Abständen neue Versionen des Microsoft Store Services SDKs, die Leistungsverbesserungen und neue Features umfassen. Wenn Sie über vorhandene Projekte verfügen, die das Microsoft Store Services SDK verwenden, und die neueste Version verwenden möchten, laden Sie einfach die neueste Version des SDKs auf Ihren Entwicklungscomputer herunter.

<span id="install-msi" />

### <a name="install-via-msi"></a>Installation über MSI

So installieren Sie das Microsoft Store-Services-SDK über das MSI-Installationsprogramm:

1.  Schließen Sie alle Instanzen von Visual Studio.

2. Wenn Sie zuvor eine frühere Version des Microsoft Store Engagement and Monetization SDK, des Universal Ad Client SDKs oder der Ad Mediator-Erweiterung installiert haben, deinstallieren Sie diese SDKs jetzt. Öffnen Sie optional ein **Eingabeaufforderungsfenster**, und führen Sie diese Befehle aus, um alle älteren SDK-Versionen zu löschen, die möglicherweise mit Visual Studio installiert wurden und die nicht in der Liste der installierten Programme auf Ihrem Computer angezeigt werden:
    ```
    MsiExec.exe /x{5C87A4DB-31C7-465E-9356-71B485B69EC8}
    MsiExec.exe /x{6AB13C21-C3EC-46E1-8009-6FD5EBEE515B}
    MsiExec.exe /x{6AC81125-8485-463D-9352-3F35A2508C11}
    ```

3.  Laden Sie das [Microsoft Store Services SDK](http://aka.ms/store-em-sdk) herunter, und installieren Sie es. Die Installation kann einige Minuten dauern. Warten Sie unbedingt, bis der Vorgang abgeschlossen ist.

4.  Starten Sie Visual Studio neu.

5.  Wenn Sie ein bestehendes Projekt haben, das auf Bibliotheken aus einer früheren Version des Microsoft Store Services SDKs, des Microsoft Advertising-SDKs, des Universal Ad Client SDKs oder des Microsoft Store Engagement and Monetization SDKs verweist, empfehlen wir, Ihr Projekt in Visual Studio zu öffnen, zu bereinigen und neu zu erstellen (klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten, wählen Sie **Bereinigen** aus, klicken Sie dann mit der rechten Maustaste erneut auf den Projektknoten, und wählen Sie **Neu erstellen** aus).

  Wenn Sie das SDK zum ersten Mal in Ihrem Projekt verwenden, sind Sie jetzt bereit, [Ihrem Projekt ein Assemblyverweis hinzuzufügen](#references).

<span id="install-nuget" />

### <a name="install-via-nuget"></a>Installieren über NuGet

So installieren Sie das Microsoft Store Services SDK-Bibliotheken über NuGet:

1.  Schließen Sie alle Instanzen von Visual Studio.

2. Wenn Sie zuvor eine frühere Version des Microsoft Store Engagement and Monetization SDK, des Universal Ad Client SDKs oder der Ad Mediator-Erweiterung installiert haben, deinstallieren Sie diese SDKs jetzt. Öffnen Sie optional ein **Eingabeaufforderungsfenster**, und führen Sie diese Befehle aus, um alle älteren SDK-Versionen zu löschen, die möglicherweise mit Visual Studio installiert wurden und die nicht in der Liste der installierten Programme auf Ihrem Computer angezeigt werden:
    ```
    MsiExec.exe /x{5C87A4DB-31C7-465E-9356-71B485B69EC8}
    MsiExec.exe /x{6AB13C21-C3EC-46E1-8009-6FD5EBEE515B}
    MsiExec.exe /x{6AC81125-8485-463D-9352-3F35A2508C11}
    ```

3.  Starten Sie Visual Studio, und öffnen Sie das Projekt, in dem Sie die Microsoft Store-Services SDK verwenden möchten.
    > [!NOTE]
    > Wenn Ihr Projekt bereits Bibliotheksreferenzen aus einer früheren MSI-Installation des SDKs enthält, entfernen Sie diese Verweise aus Ihrem Projekt. Diese Verweise sind mit Warnsymbolen versehen, da die Bibliotheken, auf die sie verweisen, in den vorherigen Schritten entfernt wurden.

4. Klicken Sie in Visual Studio auf **Projekt** und **NuGet-Pakete verwalten**.

5. Geben Sie im Suchfeld den Text **Microsoft.Services.Store.Engagement** ein, und installieren Sie das Paket Microsoft.Services.Store.Engagement. Wenn das Paket fertig ist installieren, speichern Sie die Projektmappe.
    > [!NOTE]
    > Wenn das **Ausgabe**-Fenster einen *Installationspaket*-Fehler anzeigt, der Ihnen mitteilt, dass der angegebene Pfad zu lang ist, müssen Sie NuGet möglicherweise so konfigurieren, dass es Pakete an einen anderen Speicherort mit einem kürzeren Pfad extrahiert. Fügen Sie hierzu den ```repositoryPath```-Wert einer nuget.config-Datei auf Ihrem Computer hinzu, und weisen Sie ihn einem kurzen Ordnerpfad zu, unter dem die NuGet-Pakete extrahiert werden können. Weitere Informationen finden Sie in [diesem Artikel](http://docs.nuget.org/ndocs/consume-packages/configuring-nuget-behavior) in der NuGet-Dokumentation. Sie können auch versuchen, das Visual Studio-Projekt in einen anderen Ordner mit einem kürzeren Pfad zu verschieben.

6. Schließen Sie die Visual Studio-Lösung mit dem Projekt, und öffnen Sie die Projektmappe erneut.

7.  Wenn Ihr Projekt bereits auf Bibliotheken aus einer früheren Version des Microsoft Store Services SDKs verweist, die über NuGet installiert wurde, und Sie Ihr Projekt auf eine neuere Version des SDKs aktualisiert haben, empfehlen wir, das Projekt zu bereinigen und neu zu erstellen (klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten, wählen Sie **Bereinigen** aus, klicken Sie dann mit der rechten Maustaste erneut auf den Projektknoten, und wählen Sie **Neu erstellen**).

  Wenn Sie das SDK zum ersten Mal in Ihrem Projekt verwenden, sind Sie jetzt bereit, [Ihrem Projekt ein Assemblyverweis hinzuzufügen](#references).

<span id="references" />

## <a name="add-the-assembly-reference-to-your-project"></a>Hinzufügen von Assemblyverweisen zu Ihrem Projekt

Befolgen Sie nach der Installation des Microsoft Store Services SDKs über das MSI-Installationsprogramm oder NuGet diese Instruktionen, um in Ihrem UWP-Projekt auf die SDK-Assemblys zu verweisen.

1. Öffnen Sie das Projekt in Visual Studio.
    > [!NOTE]
    > Wenn Ihr Projekt eine JavaScript-App ist, die auf eine beliebige CPU (**Any CPU**) zielt, aktualisieren Sie es so, dass es eine architekturspezifische Ausgabe verwendet (zum Beispiel **x86**).

2. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Verweise**, und wählen Sie **Verweis hinzufügen...** aus.

3. Erweitern Sie im **Verweis-Manager** die Option **Universelles Windows**, klicken Sie auf **Erweiterungen**, und aktivieren Sie dann das Kontrollkästchen neben **Microsoft Engagement Framework**. Dadurch können Sie die APIs im [Microsoft.Services.Store.Engagement](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement)-Namespace verwenden.

3. Klicken Sie auf **OK**.

> [!NOTE]
> Wenn Sie die SDK-Bibliotheken über NuGet installiert haben, enthält das Projekt enthält eine **Microsoft.Services.Store.Engagement**-Referenz. Die **Microsoft.Services.Store.Engagement**-Referenz repräsentiert das NuGet-Paket (anstelle der Bibliotheken darin) und kann ignoriert werden.

<span id="framework" />

## <a name="understanding-framework-packages-in-the-sdk"></a>Die Frameworkpakete im SDK

Die Bibliothek „Microsoft.Services.Store.Engagement.dll“ im Microsoft Store Services SDK ist als *Frameworkpaket* konfiguriert. Diese Bibliothek enthält die APIs im [Microsoft.Services.Store.Engagement](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement)-Namespace.

Da es sich bei dieser Bibliothek um ein Frameworkpaket handelt, bedeutet dies Folgendes: Nachdem ein Benutzer eine Version Ihrer App installiert hat, die diese Bibliothek verwendet, wird diese Bibliothek automatisch auf dessen Gerät über Windows Update aktualisiert, wenn eine neue Version der Bibliothek mit Fixes und Leistungsverbesserungen veröffentlicht wird. Dadurch wird sichergestellt, dass Ihre Kunden stets die neueste Version der Bibliothek auf ihren Geräten installiert haben.

Wenn wir eine neue Version des SDKs veröffentlichen, in der neue APIs oder Features in dieser Bibliothek eingeführt werden, müssen Sie die neueste Version des SDKs zur Verwendung dieser Features installieren. In diesem Szenario müssen Sie auch die aktualisierte App im Store veröffentlichen.

## <a name="related-topics"></a>Verwandte Themen

* [Microsoft Store Services SDK-API-Referenz](https://docs.microsoft.com/uwp/api/overview/engagement)
* [Ausführen von Experimenten mit A/B-Tests](run-app-experiments-with-a-b-testing.md)
* [Starten des Feedback-Hubs über Ihre App](launch-feedback-hub-from-your-app.md)
* [Konfigurieren Sie Ihre app zum Empfangen von Partner Center-Pushbenachrichtigungen](configure-your-app-to-receive-dev-center-notifications.md)
* [Protokollieren benutzerdefinierter Ereignisse im Partner Center](log-custom-events-for-dev-center.md)
