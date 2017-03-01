---
author: mcleanbyron
Description: "Zum Ausführen eines Experiments in Ihrer universellen Windows-Plattform (UWP)-App mit einem A/B-Test müssen Sie das Experiment in der App codieren."
title: "Codieren Ihrer App für das Experiment"
ms.assetid: 6A5063E1-28CD-4087-A4FA-FBB511E9CED5
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP, Microsoft Store Services SDK, A / B-Tests, Experimente"
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: d5c46c896aad3dfbc0f6f9bdb010652507654cb0
ms.lasthandoff: 02/07/2017

---

# <a name="code-your-app-for-experimentation"></a>Codieren Ihrer App für das Experiment

Nach dem [Erstellen eines Projekts und Festlegen von Remotevariablen im Dev Center-Dashboard](create-a-project-and-define-remote-variables-in-the-dev-center-dashboard.md) können Sie den Code in Ihrer App für die Universelle Windows-Plattform (UWP) aktualisieren, um:
* Werte von Remotevariablen von Windows Dev Center zu erhalten
* Remotevariablen zum Konfigurieren von App-Funktionen für die Benutzer zu verwenden
* Ereignisse in Dev Center zu protokollieren, die angeben, wann Benutzer Ihr Experiment angezeigt und eine gewünschte Aktion ausgeführt haben (auch als *Umwandlung* bezeichnet).

Um der App dieses Verhalten hinzuzufügen, verwenden Sie die vom Microsoft Store Services SDK bereitgestellten APIs.

In den folgenden Abschnitten erfahren Sie ganz allgemein, wie Sie Abweichungen für Ihr Experiment erhalten und Ereignisse in Dev Center protokollieren. Nachdem Sie die App für Experimente programmiert haben, können Sie [ein Experiment im Dev Center-Dashboard definieren](define-your-experiment-in-the-dev-center-dashboard.md). Eine exemplarische Vorgehensweise, die den gesamten Erstellungs- und Ausführungsprozess für ein Experiment veranschaulicht, finden Sie unter [Erstellen und Ausführen eines ersten Experiments mit A/B-Tests](create-and-run-your-first-experiment-with-a-b-testing.md).

>**Hinweis:**&nbsp;&nbsp;Einige der zum Experimentieren verfügbaren APIs im Windows Store Services SDK nutzen das [asynchrone Muster](../threading-async/asynchronous-programming-universal-windows-platform-apps.md) zum Abrufen von Daten aus Dev Center. Dies bedeutet, dass ein Teil der Methodenausführung nach dem Aufrufen der Methoden stattfinden kann. Auf diese Weise bleibt die Benutzeroberfläche Ihrer App weiter reaktionsfähig, während die Vorgänge abgeschlossen werden. Für das asynchrone Muster muss die App beim Aufrufen der APIs das **async**-Schlüsselwort und den **await**-Operator verwenden, wie aus den Codebeispielen in diesem Artikel ersichtlich. Asynchrone Methoden enden üblicherweise mit **Async**.

## <a name="configure-your-project"></a>Konfigurieren des Projekts

Installieren Sie zunächst das Microsoft Store Services SDK auf dem Entwicklungscomputer, und fügen Sie dem Projekt die erforderlichen Verweise hinzu.

1. [Installieren Sie das Microsoft Store Services SDK](microsoft-store-services-sdk.md#install-the-sdk).
2. Öffnen Sie das Projekt in Visual Studio.
3. Erweitern Sie im Projektmappen-Explorer den Projektknoten, klicken Sie mit der rechten Maustaste auf **Verweise**, und klicken Sie auf **Verweis hinzufügen**.
3. Erweitern Sie im **Verweis-Manager** die Option **Universelle Windows-App**, und klicken Sie auf **Erweiterungen**.
4. Aktivieren Sie in der Liste mit den SDKs das Kontrollkästchen neben **Microsoft Engagement Framework**, und klicken Sie anschließend auf **OK**.

>**Hinweis**&nbsp;&nbsp;Bei den Codebeispielen in diesem Artikel wird davon ausgegangen, dass Ihre Codedatei **using**-Anweisungen für **System.Threading.Tasks** und **Microsoft.Services.Store.Engagement**-Namespaces enthält.

## <a name="get-variation-data-and-log-the-view-event-for-your-experiment"></a>Abrufen von Abweichungsdaten und protokollieren des Anzeigeereignisses für Ihr Experiment

Suchen Sie im Projekt nach dem Code für das Feature, das Sie in Ihrem Experiment ändern möchten. Fügen Sie Code hinzu, mit dem Daten für eine Abweichung abgerufen werden, verwenden Sie diese Daten, um das Verhalten des zu testenden Features zu ändern, und protokollieren Sie dann das Anzeigeereignis für Ihr Experiment im A/B-Testdienst in Dev Center.

Der jeweils benötigte Code richtet sich nach Ihrer App, im folgenden Beispiel wird jedoch die grundlegende Vorgehensweise veranschaulicht. Ein vollständiges Codebeispiel finden Sie unter [Erstellen und Ausführen eines ersten Experiments mit A/B-Tests](create-and-run-your-first-experiment-with-a-b-testing.md).

> [!div class="tabbedCodeSnippets"]
[!code-cs[ExperimentExamples](./code/StoreSDKSamples/cs/ExperimentExamples.cs#ExperimentCodeSample)]

In den folgenden Schritten werden die wichtigen Schritte dieses Verfahrens ausführlich beschrieben.

1. Deklarieren Sie ein [StoreServicesExperimentVariation](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesexperimentvariation.aspx)-Objekt, das die aktuelle Abweichungszuweisung darstellt, und ein [StoreServicesCustomEventLogger](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicescustomeventlogger.aspx)-Objekt zum Protokollieren von Anzeige- und Umwandlungsereignissen in Dev Center.

  > [!div class="tabbedCodeSnippets"]
  [!code-cs[ExperimentExamples](./code/StoreSDKSamples/cs/ExperimentExamples.cs#Snippet1)]

1. Deklarieren Sie eine Zeichenfolgenvariable, die der [Projekt-ID](run-app-experiments-with-a-b-testing.md#terms) für das Experiment zugewiesen wird, das Sie abrufen möchten.
  >**Hinweis**&nbsp;&nbsp;Sie erhalten eine Projekt-ID, wenn Sie [ein Projekt im Dev Center-Dashboard erstellen](create-a-project-and-define-remote-variables-in-the-dev-center-dashboard.md). Der hier gezeigte Projekt-ID dient nur als Beispiel.

  > [!div class="tabbedCodeSnippets"]
  [!code-cs[ExperimentExamples](./code/StoreSDKSamples/cs/ExperimentExamples.cs#Snippet2)]

2. Rufen Sie die statische [GetCachedVariationAsync](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesexperimentvariation.getcachedvariationasync.aspx)-Methode auf, um die aktuelle zwischengespeicherte Abweichungszuweisung für Ihr Experiment abzurufen, und übergeben Sie die Projekt-ID für das Experiment an die Methode. Diese Methode gibt ein [StoreServicesExperimentVariationResult](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesexperimentvariationresult.aspx)-Objekt zurück, das den Zugriff auf die Abweichungszuweisung (über die [ExperimentVariation](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesexperimentvariationresult.experimentvariation.aspx)-Eigenschaft) ermöglicht.

  > [!div class="tabbedCodeSnippets"]
  [!code-cs[ExperimentExamples](./code/StoreSDKSamples/cs/ExperimentExamples.cs#Snippet3)]

4. Überprüfen Sie anhand der [IsStale](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesexperimentvariation.isstale.aspx)-Eigenschaft, ob die zwischengespeicherte Abweichungszuweisung mit einer Remoteabweichungszuweisung vom Server aktualisiert werden muss. Wenn ja, rufen Sie die statische [GetRefreshedVariationAsync](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesexperimentvariation.getrefreshedvariationasync.aspx)-Methode auf, um auf dem Server nach einer aktualisierten Abweichungszuweisung zu suchen und die lokale zwischengespeicherte Abweichung zu aktualisieren.

  > [!div class="tabbedCodeSnippets"]
  [!code-cs[ExperimentExamples](./code/StoreSDKSamples/cs/ExperimentExamples.cs#Snippet4)]

5. Verwenden Sie die [GetBoolean](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesexperimentvariation.getboolean.aspx)-, [GetDouble](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesexperimentvariation.getdouble.aspx)-, [GetInt32](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesexperimentvariation.getint32.aspx) oder [GetString](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesexperimentvariation.getstring.aspx)-Methode des [StoreServicesExperimentVariation](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesexperimentvariation.aspx)-Objekts, um die Werte für die Abweichungszuweisung abzurufen. Der erste Parameter in den Methoden ist jeweils der Name der Abweichung, die Sie abrufen möchten (gemäß Eingabe im Dev Center-Dashboard). Der zweite Parameter ist der Standardwert, den die Methode zurückgeben soll, falls der angegebene Wert nicht aus dem Dev Center abgerufen werden kann (etwa, weil keine Netzwerkverbindung besteht) und keine zwischengespeicherte Version der Abweichung verfügbar ist.

  Im folgenden Beispiel werden mithilfe von [GetString](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesexperimentvariation.getstring.aspx) eine Variable namens *buttonText* abgerufen und der Standardvariablenwert **Grey Button** angegeben.

  > [!div class="tabbedCodeSnippets"]
  [!code-cs[ExperimentExamples](./code/StoreSDKSamples/cs/ExperimentExamples.cs#Snippet5)]

4. Verwenden Sie die Variablenwerte im Code, um das Verhalten des getesteten Features zu ändern. Der folgende Code weist beispielsweise den *buttonText*-Wert dem Inhalt einer Schaltfläche in Ihrer App zu. In diesem Beispiel wird davon ausgegangen, dass Sie diese Schaltfläche bereits an einer anderen Stelle in Ihrem Projekt definiert haben.

  > [!div class="tabbedCodeSnippets"]
  [!code-cs[ExperimentExamples](./code/StoreSDKSamples/cs/ExperimentExamples.cs#Snippet6)]

5. Protokollieren Sie zuletzt das [Anzeigeereignis](run-app-experiments-with-a-b-testing.md#terms) für Ihr Experiment im A/B-Testdienst in Dev Center. Initialisieren Sie das ```logger```-Feld in ein [StoreServicesCustomEventLogger](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicescustomeventlogger.aspx)-Objekt, und rufen Sie die [LogForVariation](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicescustomeventlogger.logforvariation.aspx)-Methode auf. Übergeben Sie das [StoreServicesExperimentVariation](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesexperimentvariation.aspx)-Objekt, das die aktuelle Abweichungszuweisung darstellt (dieses Objekt liefert den Ereigniskontext für Dev Center), und den Namen des Anzeigeereignisses für Ihr Experiment. Dieser muss dem Namen des Anzeigeereignisses entsprechen, den Sie für Ihr Experiment im Dev Center-Dashboard eingeben. Vom Code sollte das Anzeigeereignis protokolliert werden, wenn der Benutzer mit dem Anzeigen einer Abweichung beginnt, die Teil des Experiments ist.

  Das folgende Beispiel veranschaulicht, wie ein Anzeigeereignis namens **userViewedButton** protokolliert wird. Das Ziel des Experiments in diesem Beispiel besteht darin, dass der Benutzer auf eine Schaltfläche in der App klickt, damit das Anzeigeereignis protokolliert wird, nachdem die App die Abweichungsdaten (in diesem Fall den Schaltflächentext) abgerufen und dem Inhalt der Schaltfläche zugewiesen hat.

  > [!div class="tabbedCodeSnippets"]
  [!code-cs[ExperimentExamples](./code/StoreSDKSamples/cs/ExperimentExamples.cs#Snippet7)]

## <a name="log-conversion-events-to-dev-center"></a>Protokollieren von Umwandlungsereignissen in Dev Center

Fügen Sie als Nächstes Code hinzu, mit dem [Umwandlungsereignisse](run-app-experiments-with-a-b-testing.md#terms) im A/B-Testdienst in Dev Center protokolliert werden. Vom Code sollte ein Umwandlungsereignis protokolliert werden, wenn der Benutzer ein für Ihr Experiment gesetztes Ziel erreicht. Welchen Code Sie genau benötigen, hängt von Ihrer App ab. Hier werden daher nur die allgemeinen Schritte angegeben. Ein umfassendes Codebeispiel finden Sie unter [Erstellen und Ausführen eines ersten Experiments mit A/B-Tests](create-and-run-your-first-experiment-with-a-b-testing.md).

1. Rufen Sie in dem Code, der ausgeführt wird, wenn der Benutzer eines der Ziele für das Experiment erreicht, erneut die [LogForVariation](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicescustomeventlogger.logforvariation.aspx)-Methode auf, und übergeben Sie das [StoreServicesExperimentVariation](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicesexperimentvariation.aspx)-Objekt und den Namen eines Umwandlungsereignisses für Ihr Experiment. Dieser muss einem der Umwandlungsereignisnamen entsprechen, die Sie im Dev Center-Dashboard für Ihr Experiment eingeben.

  Im folgenden Beispiel wird ein Umwandlungsereignis namens **userClickedButton** aus dem **Click**-Ereignishandler für eine Schaltfläche protokolliert. In diesem Beispiel besteht das Ziel des Experiments darin, dass der Benutzer auf die Schaltfläche klickt.

  > [!div class="tabbedCodeSnippets"]
  [!code-cs[ExperimentExamples](./code/StoreSDKSamples/cs/ExperimentExamples.cs#Snippet8)]

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie das Experiment in Ihrer App programmiert haben, sind Sie bereit für die folgenden Schritte:
1. [Definieren Sie das Experiment im Dev Center-Dashboard](define-your-experiment-in-the-dev-center-dashboard.md). Erstellen Sie ein Experiment, das die Anzeigeereignisse, Umwandlungsereignisse und eindeutigen Abweichungen für den A/B-Test festlegt.
2. [Führen Sie das Experiment im Dev Center-Dashboard aus, und verwalten Sie es](manage-your-experiment.md).


## <a name="related-topics"></a>Verwandte Themen

* [Erstellen eines Projekts und Festlegen von Remotevariablen im Dev Center-Dashboard](create-a-project-and-define-remote-variables-in-the-dev-center-dashboard.md)
* [Definieren des Experiments im Dev Center-Dashboard](define-your-experiment-in-the-dev-center-dashboard.md)
* [Verwalten des Experiments im Dev Center-Dashboard](manage-your-experiment.md)
* [Erstellen und Ausführen eines ersten Experiments mit A/B-Tests](create-and-run-your-first-experiment-with-a-b-testing.md)
* [Ausführen von App-Experimenten mit A/B-Tests](run-app-experiments-with-a-b-testing.md)

