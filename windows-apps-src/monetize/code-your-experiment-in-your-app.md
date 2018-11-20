---
author: Xansky
Description: To run an experiment in your Universal Windows Platform (UWP) app with A/B testing, you must code the experiment in your app.
title: Codieren einer App für Experimente
ms.assetid: 6A5063E1-28CD-4087-A4FA-FBB511E9CED5
ms.author: mhopkins
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Microsoft Store Services SDK, A/B-Tests, Experimente
ms.localizationpriority: medium
ms.openlocfilehash: c9212f3a120e03bd436b77e0dd66be4367ded8e1
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7297111"
---
# <a name="code-your-app-for-experimentation"></a>Codieren einer App für Experimente

Nachdem Sie [das Erstellen eines Projekts und Festlegen von remotevariablen im Partner Center](create-a-project-and-define-remote-variables-in-the-dev-center-dashboard.md)können Sie den Code in Ihrer app (universelle Windows Plattform) zu aktualisieren:
* Erhalten Sie Werte von remotevariablen von Partner Center.
* Remotevariablen zum Konfigurieren von App-Funktionen für die Benutzer zu verwenden
* Protokollieren von Ereignissen in das Partner Center, die angeben, wann Benutzer Ihr Experiment angezeigt haben, und eine gewünschte Aktion (auch als eine *Konvertierung*bezeichnet) ausgeführt.

Um der App dieses Verhalten hinzuzufügen, verwenden Sie die vom Microsoft Store Services SDK bereitgestellten APIs.

In den folgenden Abschnitten wird beschrieben, den allgemeinen Prozess der Varianten für Ihr Experiment erhalten und Ereignisse in Partner Center protokollieren. Nachdem Sie Ihrer app für Experimente programmiert haben, können Sie [ein Experiment im Partner Center zu definieren](define-your-experiment-in-the-dev-center-dashboard.md). Eine exemplarische Vorgehensweise, die den gesamten Erstellungs- und Ausführungsprozess für ein Experiment veranschaulicht, finden Sie unter [Erstellen und Durchführen eines ersten Experiments mit A/B-Tests](create-and-run-your-first-experiment-with-a-b-testing.md).

> [!NOTE]
> Einige der zum Experimentieren verfügbaren APIs im Microsoft Store Services SDK verwenden das [asynchrone Muster](../threading-async/asynchronous-programming-universal-windows-platform-apps.md) zum Abrufen von Daten aus dem Partner Center. Dies bedeutet, dass ein Teil der Methodenausführung nach dem Aufrufen der Methoden stattfinden kann. Auf diese Weise bleibt die Benutzeroberfläche Ihrer App weiter reaktionsfähig, während die Vorgänge abgeschlossen werden. Für das asynchrone Muster muss die App beim Aufrufen der APIs das **async**-Schlüsselwort und den **await**-Operator verwenden, wie aus den Codebeispielen in diesem Artikel ersichtlich. Asynchrone Methoden enden üblicherweise mit **Async**.

## <a name="configure-your-project"></a>Konfigurieren des Projekts

Installieren Sie zunächst das Microsoft Store Services SDK auf dem Entwicklungscomputer, und fügen Sie dem Projekt die erforderlichen Verweise hinzu.

1. [Installieren Sie das Microsoft Store Services SDK](microsoft-store-services-sdk.md#install-the-sdk).
2. Öffnen Sie das Projekt in Visual Studio.
3. Erweitern Sie im Projektmappen-Explorer den Projektknoten, klicken Sie mit der rechten Maustaste auf **Verweise**, und klicken Sie auf **Verweis hinzufügen**.
3. Erweitern Sie im **Verweis-Manager** die Option **Universelle Windows-App**, und klicken Sie auf **Erweiterungen**.
4. Aktivieren Sie in der Liste mit den SDKs das Kontrollkästchen neben **Microsoft Engagement Framework**, und klicken Sie anschließend auf **OK**.

> [!NOTE]
> Die Codebeispiele in diesem Artikel wird davon ausgegangen, dass Ihre **mithilfe von** Anweisungen für die Namespaces **System.Threading.Tasks** und **Microsoft.Services.Store.Engagement Codedatei** .

## <a name="get-variation-data-and-log-the-view-event-for-your-experiment"></a>Abrufen von Abweichungsdaten und protokollieren des Anzeigeereignisses für Ihr Experiment

Suchen Sie im Projekt nach dem Code für das Feature, das Sie in Ihrem Experiment ändern möchten. Fügen Sie Code, der Daten für eine Variante abruft, verwenden Sie diese Daten, um das Verhalten des Features ändern Sie testen und melden Sie sich dann das anzeigeereignis für Ihr Experiment im A / B-Testdienst in Partner Center.

Der jeweils benötigte Code richtet sich nach Ihrer App, im folgenden Beispiel wird jedoch die grundlegende Vorgehensweise veranschaulicht. Ein vollständiges Codebeispiel finden Sie unter [Erstellen und Ausführen eines ersten Experiments mit A/B-Tests](create-and-run-your-first-experiment-with-a-b-testing.md).

[!code-cs[ExperimentExamples](./code/StoreSDKSamples/cs/ExperimentExamples.cs#ExperimentCodeSample)]

In den folgenden Schritten werden die wichtigen Schritte dieses Verfahrens ausführlich beschrieben.

1. Deklarieren Sie ein [StoreServicesExperimentVariation](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesexperimentvariation) -Objekt, das die aktuelle abweichungszuweisung darstellt, und ein [StoreServicesCustomEventLogger](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicescustomeventlogger) -Objekt, das Sie zum Protokollieren von Anzeige- und umwandlungsereignisse in Partner Center verwenden.

    [!code-cs[ExperimentExamples](./code/StoreSDKSamples/cs/ExperimentExamples.cs#Snippet1)]

2. Deklarieren Sie eine Zeichenfolgenvariable, die der [Projekt-ID](run-app-experiments-with-a-b-testing.md#terms) für das Experiment zugewiesen wird, das Sie abrufen möchten.
    > [!NOTE]
    > Sie erhalten eine Projekt ID, wenn Sie [ein Projekt im Partner Center erstellen](create-a-project-and-define-remote-variables-in-the-dev-center-dashboard.md). Der hier gezeigte Projekt-ID dient nur als Beispiel.

    [!code-cs[ExperimentExamples](./code/StoreSDKSamples/cs/ExperimentExamples.cs#Snippet2)]

3. Rufen Sie die statische [GetCachedVariationAsync](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesexperimentvariation.getcachedvariationasync)-Methode auf, um die aktuelle zwischengespeicherte Abweichungszuweisung für Ihr Experiment abzurufen, und übergeben Sie die Projekt-ID für das Experiment an die Methode. Diese Methode gibt ein [StoreServicesExperimentVariationResult](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesexperimentvariationresult)-Objekt zurück, das den Zugriff auf die Abweichungszuweisung (über die [ExperimentVariation](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesexperimentvariationresult.experimentvariation)-Eigenschaft) ermöglicht.

    [!code-cs[ExperimentExamples](./code/StoreSDKSamples/cs/ExperimentExamples.cs#Snippet3)]

4. Überprüfen Sie anhand der [IsStale](htthttps://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesexperimentvariation.isstale)-Eigenschaft, ob die zwischengespeicherte Abweichungszuweisung mit einer Remoteabweichungszuweisung vom Server aktualisiert werden muss. Wenn ja, rufen Sie die statische [GetRefreshedVariationAsync](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesexperimentvariation.getrefreshedvariationasync)-Methode auf, um auf dem Server nach einer aktualisierten Abweichungszuweisung zu suchen und die lokale zwischengespeicherte Abweichung zu aktualisieren.

    [!code-cs[ExperimentExamples](./code/StoreSDKSamples/cs/ExperimentExamples.cs#Snippet4)]

5. Verwenden Sie die [GetBoolean](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesexperimentvariation.getboolean)-, [GetDouble](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesexperimentvariation.getdouble)-, [GetInt32](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesexperimentvariation.getint32) oder [GetString](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesexperimentvariation.getstring)-Methode des [StoreServicesExperimentVariation](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesexperimentvariation)-Objekts, um die Werte für die Abweichungszuweisung abzurufen. Jede Methode der erste Parameter ist der Name der Abweichung, die Sie abrufen möchten (Dies ist der gleiche Name der eine Variante, die Sie im Partner Center eingeben). Der zweite Parameter ist der Standardwert, den die Methode zurückgeben soll, wenn sie nicht den angegebenen Wert aus dem Partner Center (z. B., wenn keine Netzwerkkonnektivität besteht) abrufen können, und eine zwischengespeicherte Version der Abweichung ist nicht verfügbar.

    Im folgenden Beispiel werden mithilfe von [GetString](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesexperimentvariation.getstring) eine Variable namens *buttonText* abgerufen und der Standardvariablenwert **Grey Button** angegeben.

    [!code-cs[ExperimentExamples](./code/StoreSDKSamples/cs/ExperimentExamples.cs#Snippet5)]

6. Verwenden Sie die Variablenwerte im Code, um das Verhalten des getesteten Features zu ändern. Der folgende Code weist beispielsweise den *buttonText*-Wert dem Inhalt einer Schaltfläche in Ihrer App zu. In diesem Beispiel wird davon ausgegangen, dass Sie diese Schaltfläche bereits an einer anderen Stelle in Ihrem Projekt definiert haben.

    [!code-cs[ExperimentExamples](./code/StoreSDKSamples/cs/ExperimentExamples.cs#Snippet6)]

7. Protokollieren Sie zuletzt das [anzeigeereignis](run-app-experiments-with-a-b-testing.md#terms) für Ihr Experiment im a / B-Testdienst in Partner Center. Initialisieren Sie das ```logger```-Feld in ein [StoreServicesCustomEventLogger](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicescustomeventlogger)-Objekt, und rufen Sie die [LogForVariation](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicescustomeventlogger.logforvariation)-Methode auf. Übergeben Sie das [StoreServicesExperimentVariation](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesexperimentvariation) -Objekt, das die aktuelle abweichungszuweisung darstellt (dieses Objekt liefert den Ereigniskontext für Partner Center) und den Namen des anzeigeereignisses für Ihr Experiment. Dieser muss dem Namen des anzeigeereignisses entsprechen, den Sie im Partner Center für Ihr Experiment eingeben. Vom Code sollte das Anzeigeereignis protokolliert werden, wenn der Benutzer mit dem Anzeigen einer Abweichung beginnt, die Teil des Experiments ist.

    Das folgende Beispiel veranschaulicht, wie ein Anzeigeereignis namens **userViewedButton** protokolliert wird. Das Ziel des Experiments in diesem Beispiel besteht darin, dass der Benutzer auf eine Schaltfläche in der App klickt, damit das Anzeigeereignis protokolliert wird, nachdem die App die Abweichungsdaten (in diesem Fall den Schaltflächentext) abgerufen und dem Inhalt der Schaltfläche zugewiesen hat.

    [!code-cs[ExperimentExamples](./code/StoreSDKSamples/cs/ExperimentExamples.cs#Snippet7)]

## <a name="log-conversion-events-to-partner-center"></a>Protokollieren von umwandlungsereignissen in das Partner Center

Als Nächstes fügen Sie Code, der meldet sich [umwandlungsereignisse](run-app-experiments-with-a-b-testing.md#terms) im a / B-Testdienst in Partner Center. Vom Code sollte ein Umwandlungsereignis protokolliert werden, wenn der Benutzer ein für Ihr Experiment gesetztes Ziel erreicht. Welchen Code Sie genau benötigen, hängt von Ihrer App ab. Hier werden daher nur die allgemeinen Schritte angegeben. Ein umfassendes Codebeispiel finden Sie unter [Erstellen und Ausführen eines ersten Experiments mit A/B-Tests](create-and-run-your-first-experiment-with-a-b-testing.md).

1. Rufen Sie in dem Code, der ausgeführt wird, wenn der Benutzer eines der Ziele für das Experiment erreicht, erneut die [LogForVariation](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicescustomeventlogger.logforvariation)-Methode auf, und übergeben Sie das [StoreServicesExperimentVariation](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicesexperimentvariation)-Objekt und den Namen eines Umwandlungsereignisses für Ihr Experiment. Dieser muss einem der umwandlungsereignisnamen entsprechen, die Sie im Partner Center für Ihr Experiment eingeben.

    Im folgenden Beispiel wird ein Umwandlungsereignis namens **userClickedButton** aus dem **Click**-Ereignishandler für eine Schaltfläche protokolliert. In diesem Beispiel besteht das Ziel des Experiments darin, dass der Benutzer auf die Schaltfläche klickt.

    [!code-cs[ExperimentExamples](./code/StoreSDKSamples/cs/ExperimentExamples.cs#Snippet8)]

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie das Experiment in Ihrer App programmiert haben, sind Sie bereit für die folgenden Schritte:
1. [Definieren Ihres Experiments im Partner Center](define-your-experiment-in-the-dev-center-dashboard.md). Erstellen Sie ein Experiment, das die Anzeigeereignisse, Umwandlungsereignisse und eindeutigen Abweichungen für den A/B-Test festlegt.
2. [Ausführen und Verwalten des Experiments im Partner Center](manage-your-experiment.md).


## <a name="related-topics"></a>Verwandte Themen

* [Erstellen eines Projekts und Festlegen von remotevariablen im Partner Center](create-a-project-and-define-remote-variables-in-the-dev-center-dashboard.md)
* [Definieren eines Experiments im Partner Center](define-your-experiment-in-the-dev-center-dashboard.md)
* [Verwalten eines Experiments im Partner Center](manage-your-experiment.md)
* [Erstellen und Ausführen eines ersten Experiments mit A/B-Tests](create-and-run-your-first-experiment-with-a-b-testing.md)
* [Ausführen von App-Experimenten mit A/B-Tests](run-app-experiments-with-a-b-testing.md)
