---
author: mcleanbyron
Description: "Der Microsoft Store Services SDK bietet Bibliotheken und Tools zum Hinzufügen von Features zu Ihren Apps, mit denen Sie mehr Geld verdienen und Kunden gewinnen können."
title: Microsoft Store Services SDK
ms.assetid: 518516DB-70A7-49C4-B3B6-CD8A98320B9C
translationtype: Human Translation
ms.sourcegitcommit: 011b370b7bd7ad7c7d8f60281261b6da954e2256
ms.openlocfilehash: 840a5e76d409f547d55e558262af09c8fa36a544

---

# Microsoft Store Services SDK

Das Microsoft Store Services SDK bietet Features, mit denen Sie in Ihren Apps für die universelle Windows-Plattform (UWP) mehr Geld verdienen und besser mit Kunden interagieren können. Mit diesen können Sie z.B. Anzeigen in Ihren Apps einblenden und Experimente mit A/B-Tests in Ihren Apps durchführen. Dieses SDK ist eine Erweiterung für Visual Studio2015 und neuere Versionen von Visual Studio.

## Vom SDK unterstützte Szenarien

Das SDK unterstützt derzeit die folgenden Szenarien für UWP-Apps. Das SDK wird ständig weiterentwickelt, um neue Szenarien für die Vernetzung und die gewinnbringende Nutzung zu unterstützen. Die Referenzdokumentation zu den APIs im SDK finden Sie unter [Microsoft Store Services SDK-API-Referenz](https://msdn.microsoft.com/library/windows/apps/mt691886.aspx).

|  Szenario  |  Beschreibung   |
|------------|----------------|
|  [Durchführen von Experimenten mit A/B-Tests in Ihrer UWP-App](run-app-experiments-with-a-b-testing.md)    |  Führen Sie A/B-Tests in Ihrer App für die universelle Windows-Plattform (UWP) aus, um die Effektivität der Features für einige Kunden zu messen, bevor Sie die Features für alle Benutzer freigeben. Verwenden Sie nach der Definition eines Experiments im Dev Center-Dashboard die [StoreServicesExperimentVariation](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesexperimentvariation.aspx)-Klasse zum Abrufen von Varianten für Ihr Experiment in der App, verwenden Sie diese Daten zum Ändern des Verhaltens des Features, das Sie testen, und verwenden Sie dann die [LogForVariation](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicescustomeventlogger.logforvariation.aspx)-Methode zum Senden des Anzeigeereignisses und der Umwandlungsereignisse an Dev Center. Verwenden Sie dann das Dashboard zum Anzeigen der Ergebnisse und zum Verwalten des Experiments.  |
|  [Starten des Feedback-Hubs über Ihre UWP-App](launch-feedback-hub-from-your-app.md)    |  Verwenden Sie die [StoreServicesFeedbackLauncher](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesfeedbacklauncher.aspx)-Klasse in Ihrer UWP-App, um Ihre Windows10-Kunden auf den Feedback-Hub zu verweisen. Dort können Kunden ihre Probleme und Vorschläge übermitteln und das Feedback anderer Benutzer lesen und bewerten. Verwalten Sie anschließend dieses Feedback im [Feedbackbericht](../publish/feedback-report.md) im Dev Center-Dashboard. |
|  [Konfigurieren Sie Ihre UWP-App zum Empfangen von Dev Center-Pushbenachrichtigungen](configure-your-app-to-receive-dev-center-notifications.md)    |  Verwenden Sie die [StoreServicesEngagementManager](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesengagementmanager.aspx)-Klasse in Ihrer UWP-App zum Registrieren Ihrer App für den Empfang benutzerorientierter Pushbenachrichtigungen, die Sie Ihren Kunden mithilfe des Windows Dev Center-Dashboards senden.  |
|   [Protokollieren Sie benutzerdefinierte Ereignisse in Ihrer UWP-App für den Nutzungsbericht in Dev Center](log-custom-events-for-dev-center.md)   |  Verwenden Sie die [StoreServicesCustomEventLogger](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicescustomeventlogger.log.aspx)-Klasse in Ihrer UWP-App, um benutzerdefinierte Ereignisse zu protokollieren, die Ihrer App im Dev Center zugeordnet sind. Überprüfen Sie dann alle Instanzen für Ihre benutzerdefinierten Ereignisse im Abschnitt **Benutzerdefinierte Ereignisse** des [Nutzungsberichts](https://msdn.microsoft.com/windows/uwp/publish/usage-report) im Dev Center-Dashboard.  |
|  [Anzeigen von Werbung in Ihrer UWP-App](display-ads-in-your-app.md)    |  Verwenden Sie das Steuerelement [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx) oder [InterstitialAd](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.interstitialad.aspx) in Ihrer UWP-App, um Ihre Umsätze durch die Anzeige von Banner-Anzeigen oder Interstitialanzeigen zu steigern.<br/><br/>**Hinweis**&nbsp;&nbsp;Das Microsoft Store Services SDK unterstützt nur UWP-Apps für Windows10. Um Anzeigen in Windows8.1 und Windows Phone8.x-Apps anzuzeigen, verwenden Sie das [Microsoft Advertising SDK for Windows and Windows Phone 8.x](http://aka.ms/store-8-sdk).  |

<span id="prerequisites" />
## Voraussetzungen

Das Microsoft Store Services SDK erfordert:

* Visual Studio2015 oder eine neuere Version.
* Visual Studio-Tools für universelle Windows-Apps, installiert mit Ihrer Version von Visual Studio.

>**Hinweis**&nbsp;&nbsp; Um das Microsoft Store Services SDK mit Visual Studio2015 zu installieren, muss Version1.1 oder höher der Visual Studio-Tools für universelle Windows-Apps installiert sein. Weitere Informationen zu diesem Update der Visual Studio-Tools für universelle Windows-Apps finden Sie in den [Versionshinweisen](http://go.microsoft.com/fwlink/?LinkID=624516).

<span id="install" />
## Installieren des SDK

Es gibt zwei Optionen für die Installation des Microsoft Store-Services-SDKs für die Verwendung mit Visual Studio2015 (oder einer neueren Version) auf dem Entwicklungscomputer:

* **MSI-Installer**&nbsp;&nbsp;Sie können das SDK über das [hier](http://aka.ms/store-em-sdk) verfügbare MSI-Installationsprogramm installieren. Bei dieser Option werden die SDK-Bibliotheken an einem freigegebenen Speicherort auf dem Entwicklungscomputer installiert, damit alle UWP-Projekte in Visual Studio darauf verweisen können.
* **NuGet-Paket**&nbsp;&nbsp;Sie können die SDK-Bibliotheken für ein bestimmtes UWP-Projekt in Visual Studio mithilfe von NuGet installieren. Bei dieser Option werden die SDK-Bibliotheken nur für das Projekt installiert, in dem Sie das NuGet-Paket installiert haben.

Microsoft veröffentlicht in regelmäßigen Abständen neue Versionen des Microsoft Store Services SDKs, die Leistungsverbesserungen und neue Features umfassen. Wenn Sie über vorhandene Projekte verfügen, die das Microsoft Store Services SDK verwenden, und die neueste Version verwenden möchten, laden Sie einfach die neueste Version des SDKs auf Ihren Entwicklungscomputer herunter.

>**Hinweis**&nbsp;&nbsp;Um das Microsoft Store Services SDK mit Visual Studio2015 zu installieren, muss Version1.1 oder höher der Visual Studio-Tools für universelle Windows-Apps installiert sein. Weitere Informationen zu diesem Update der Visual Studio-Tools für universelle Windows-Apps finden Sie in den [Versionshinweisen](http://go.microsoft.com/fwlink/?LinkID=624516).

<span id="install-msi" />
### Installation über MSI

So installieren Sie das Microsoft Store-Services-SDK über das MSI-Installationsprogramm:

1.  Schließen Sie alle Instanzen von Visual Studio2015 (oder einer neueren Version). Wenn Sie zuvor eine frühere Version des Microsoft Advertising SDKs, des Universal Ad Client SDKs, der Ad Mediator-Erweiterung oder des Microsoft Store Engagement and Monetization SDKs installiert haben, deinstallieren Sie diese SDK-Versionen jetzt.

2.  Öffnen Sie ein **Eingabeaufforderungsfenster**, und führen Sie diese Befehle aus, um alle älteren Advertising SDK-Versionen zu löschen, die möglicherweise mit Visual Studio installiert wurden und die nicht in der Liste der installierten Programme auf Ihrem Computer angezeigt werden:
  ```
  MsiExec.exe /x{5C87A4DB-31C7-465E-9356-71B485B69EC8}
  MsiExec.exe /x{6AB13C21-C3EC-46E1-8009-6FD5EBEE515B}
  MsiExec.exe /x{6AC81125-8485-463D-9352-3F35A2508C11}
  ```

3.  Laden Sie das [Microsoft Store Services SDK](http://aka.ms/store-em-sdk) herunter, und installieren Sie es. Die Installation kann einige Minuten dauern. Warten Sie unbedingt, bis der Vorgang abgeschlossen ist.

4.  Starten Sie Visual Studio neu.

5.  Wenn Sie ein bestehendes Projekt haben, das auf Bibliotheken aus einer früheren Version des Microsoft Store Services SDKs, des Microsoft Advertising SDKs, des Universal Ad Client SDKs oder des Microsoft Store Engagement and Monetization SDKs verweist, empfehlen wir, Ihr Projekt in Visual Studio zu öffnen, zu bereinigen und neu zu erstellen (klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten, wählen Sie **Bereinigen** aus, klicken Sie dann mit der rechten Maustaste erneut auf den Projektknoten, und wählen Sie **Neu erstellen** aus).

  Wenn Sie das SDK zum ersten Mal in Ihrem Projekt verwenden, sind Sie jetzt bereit, [Ihrem Projekt die entsprechenden Microsoft Store-Services-SDK-Bibliotheksreferenzen hinzuzufügen](#references).

<span id="install-nuget" />
### Installieren über NuGet

So installieren Sie die Microsoft Store-Services-SDK-Bibliotheken für ein bestimmtes Projekt über NuGet

1.  Schließen Sie alle Instanzen von Visual Studio2015 (oder einer neueren Version). Wenn Sie zuvor eine frühere Version des Microsoft Advertising SDKs, des Universal Ad Client SDKs, der Ad Mediator-Erweiterung oder des Microsoft Store Engagement and Monetization SDKs installiert haben, deinstallieren Sie diese SDK-Versionen jetzt.

2.  Öffnen Sie ein **Eingabeaufforderungsfenster**, und führen Sie diese Befehle aus, um alle älteren Advertising SDK-Versionen zu löschen, die möglicherweise mit Visual Studio installiert wurden und die nicht in der Liste der installierten Programme auf Ihrem Computer angezeigt werden:
  ```
  MsiExec.exe /x{5C87A4DB-31C7-465E-9356-71B485B69EC8}
  MsiExec.exe /x{6AB13C21-C3EC-46E1-8009-6FD5EBEE515B}
  MsiExec.exe /x{6AC81125-8485-463D-9352-3F35A2508C11}
  ```

3.  Starten Sie Visual Studio, und öffnen Sie das Projekt, in dem Sie die Microsoft Store-Services-SDK-Bibliotheken verwenden möchten.

  >**Hinweis:**&nbsp;&nbsp;Wenn Ihr Projekt bereits Bibliotheksreferenzen aus einer früheren MSI-Installation des SDKs enthält, entfernen Sie diese Verweise aus Ihrem Projekt. Diese Verweise sind mit Warnsymbolen versehen, da die Bibliotheken, auf die sie verweisen, in den vorherigen Schritten entfernt wurden.

4. Klicken Sie in Visual Studio auf **Projekt** und **NuGet-Pakete verwalten**.

5. Geben Sie im Suchfeld den Text **Microsoft.Services.Store.SDK** ein, und installieren Sie das Paket Microsoft.Services.Store.SDK.

  >**Hinweis:**&nbsp;&nbsp;Wenn das **Ausgabe**-Fenster einen *Installationspaket*-Fehler anzeigt, der Ihnen mitteilt, dass der angegebene Pfad zu lang ist, müssen Sie NuGet möglicherweise so konfigurieren, dass es Pakete an einen anderen Speicherort mit einem kürzeren Pfad extrahiert. Fügen Sie hierzu den ```repositoryPath```-Wert einer nuget.config-Datei auf Ihrem Computer hinzu, und weisen Sie ihn einem kurzen Ordnerpfad zu, unter dem die NuGet-Pakete extrahiert werden können. Weitere Informationen finden Sie in [diesem Artikel](http://docs.nuget.org/ndocs/consume-packages/configuring-nuget-behavior) in der NuGet-Dokumentation. Sie können auch versuchen, das Visual Studio-Projekt in einen anderen Ordner mit einem kürzeren Pfad zu verschieben.

6. Schließen Sie das Projekt, und öffnen Sie es erneut.

7.  Wenn Ihr Projekt bereits auf Bibliotheken aus einer früheren Version des Microsoft Store Services SDKs verweist, die über NuGet installiert wurde, und Sie Ihr Projekt auf eine neuere Version des SDKs aktualisiert haben, empfehlen wir, das Projekt zu bereinigen und neu zu erstellen (klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf den Projektknoten, wählen Sie **Bereinigen** aus, klicken Sie dann mit der rechten Maustaste erneut auf den Projektknoten, und wählen Sie **Neu erstellen**).

  Wenn Sie das SDK zum ersten Mal in Ihrem Projekt verwenden, sind Sie jetzt bereit, [Ihrem Projekt die entsprechenden Microsoft Store-Services-SDK-Bibliotheksreferenzen hinzuzufügen](#references).

<span id="references" />
## Hinzufügen von SDK-Bibliotheksverweisen zu dem Projekt

Befolgen Sie nach der Installation des Microsoft Store Services SDKs über das MSI-Installationsprogramm oder NuGet diese Instruktionen, um in Ihrem UWP-Projekt auf die SDK-Bibliotheken zu verweisen.

1. Öffnen Sie das Projekt in Visual Studio.

  >**Hinweis**&nbsp;&nbsp;Wenn Ihr Projekt eine JavaScript-App ist, die auf **irgendeinen Prozessor** zielt, aktualisieren Sie es so, dass es eine architekturspezifische Ausgabe verwendet (zum Beispiel **x86**).

2. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Verweise**, und wählen Sie **Verweis hinzufügen...** aus.

3. Erweitern Sie im **Verweis-Manager** die Option **Universal Windows**, klicken Sie auf **Erweiterungen**, und aktivieren Sie dann das Kontrollkästchen neben einem der folgenden Elemente.

  * Aktivieren Sie zur Verwendung der APIs im [Microsoft.Services.Store.Engagement](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.aspx)-Namespace für Kundeninteraktionsszenarien das Kontrollkästchen neben **Microsoft Engagement Framework**. Wählen Sie diese Option, wenn Sie [A/B-Experimente durchführen](run-app-experiments-with-a-b-testing.md), [den Feedback-Hub starten](launch-feedback-hub-from-your-app.md), [benutzerorientierte Pushbenachrichtigungen von Dev Center erhalten](configure-your-app-to-receive-dev-center-notifications.md) oder [benutzerdefinierte Ereignisse im Dev Center](log-custom-events-for-dev-center.md) protokollieren möchten.

  * Aktivieren Sie zur Verwendung der APIs für die [Anzeige von Banner-Anzeigen oder Interstitialanzeigen in Ihrer App](display-ads-in-your-app.md) das Kontrollkästchen neben **Microsoft Advertising SDK für XAML** oder **Microsoft Advertising SDK für JavaScript**, je nach Art des Projekts.

3. Klicken Sie auf **OK**.

>**Hinweis**&nbsp;&nbsp;Wenn Sie die SDK-Bibliotheken über NuGet installiert haben, enthält Ihr Projekt eine **Microsoft.Services.Store.SDK**-Referenz, zusätzlich zu **Microsoft Advertising SDK für XAML** oder **Microsoft Advertising SDK für JavaScript**. Die **Microsoft.Services.Store.SDK**-Referenz repräsentiert das NuGet-Paket (anstelle der Bibliotheken darin) und kann ignoriert werden.

<span id="framework" />
## Die Frameworkpakete in dem SDK

Die folgenden Bibliotheken im Microsoft Store Services SDK werden als *Frameworkpakete* konfiguriert:

* Microsoft.Advertising.dll. Diese Bibliothek enthält die Werbe-APIs in den [Microsoft.Advertising](https://msdn.microsoft.com/en-us/library/windows/apps/mt313187.aspx)- und [Microsoft.Advertising.WinRT.UI](https://msdn.microsoft.com/en-us/library/windows/apps/microsoft.advertising.winrt.ui.aspx)-Namespaces.
* Microsoft.Services.Store.Engagement.dll. Diese Bibliothek enthält die APIs im [Microsoft.Services.Store.Engagement](https://msdn.microsoft.com/en-us/library/windows/apps/microsoft.services.store.engagement.aspx)-Namespace.

Dies bedeutet: Nachdem ein Benutzer eine Version Ihrer App installiert hat, die diese Bibliotheken verwendet, werden diese Bibliotheken automatisch auf dessen Gerät über Windows Update aktualisiert, wenn neue Versionen der Bibliotheken mit Fixes und Leistungsverbesserungen veröffentlicht werden. Dadurch wird sichergestellt, dass Ihre Kunden stets die neueste Version der Bibliotheken auf ihren Geräten installiert haben.

Wenn wir eine neue Version des SDKs veröffentlichen, in der neue APIs oder Features in diesen Bibliotheken eingeführt werden, müssen Sie die neueste Version des SDKs zur Verwendung dieser Features installieren. In diesem Szenario müssen Sie auch die aktualisierte App im Store veröffentlichen.

## Verwandte Themen

* [Microsoft Store Services SDK-API-Referenz](https://msdn.microsoft.com/library/windows/apps/mt691886.aspx)
* [Ausführen von Experimenten mit A/B-Tests](run-app-experiments-with-a-b-testing.md)
* [Starten des Feedback-Hubs über Ihre App](launch-feedback-hub-from-your-app.md)
* [Konfigurieren Ihrer App zum Empfangen von Dev Center-Pushbenachrichtigungen](configure-your-app-to-receive-dev-center-notifications.md)
* [Protokollieren benutzerdefinierter Ereignisse für Dev Center](log-custom-events-for-dev-center.md)
* [Anzeigen von Werbung in Ihrer App](display-ads-in-your-app.md)



<!--HONumber=Nov16_HO1-->


