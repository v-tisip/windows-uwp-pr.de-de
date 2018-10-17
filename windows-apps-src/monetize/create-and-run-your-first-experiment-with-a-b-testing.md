---
author: Xansky
Description: In this walkthrough, you will create, run, and manage your first experiment with A/B testing.
title: Erstellen und Ausführen des ersten Experiments
ms.assetid: 16A2B129-14E1-4C68-86E8-52F1BE58F256
ms.author: mhopkins
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Microsoft Store Services SDK, A/B-Tests, Experimente
ms.localizationpriority: medium
ms.openlocfilehash: ac97b8d34ec0f5dbfc42022fc54911f04f09ba3b
ms.sourcegitcommit: 1c6325aa572868b789fcdd2efc9203f67a83872a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2018
ms.locfileid: "4743092"
---
# <a name="create-and-run-your-first-experiment"></a>Erstellen und Ausführen des ersten Experiments

In dieser exemplarischen Vorgehensweise führen Sie folgende Aktionen aus:
* Erstellen eines [Projekts](run-app-experiments-with-a-b-testing.md#terms) für das Experiment im Dev Center-Dashboard, das verschiedene Remotevariablen festlegt, die den Text und die Farbe einer App-Schaltfläche darstellen
* Erstellen einer App mit Code, die die Werte von Remotevariablen abruft, anhand dieser Daten die Hintergrundfarbe einer Schaltfläche ändert und Anzeige- sowie Umwandlungsereignisdaten wieder in Dev Center protokolliert
* Erstellen eines Experiments im Projekt, um zu testen, ob die Anzahl von Klicks auf eine App-Schaltfläche durch das Ändern der Hintergrundfarbe der Schaltfläche erfolgreich erhöht werden kann
* Ausführen der App, um Experimentdaten zu sammeln
* Überprüfen der Experimentergebnisse im Dev Center-Dashboard, Auswählen einer Variante zur Aktivierung für alle Benutzer der App und Abschließen des Experiments

Eine Übersicht über A/B-Tests mit Dev Center finden Sie unter [Ausführen von App-Experimenten mit A/B-Tests](run-app-experiments-with-a-b-testing.md).

## <a name="prerequisites"></a>Voraussetzungen

Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie ein Windows Dev Center-Konto und müssen Ihren Entwicklungscomputer gemäß der Beschreibung in [Ausführen von App-Experimenten mit A/B-Tests](run-app-experiments-with-a-b-testing.md) konfigurieren.

## <a name="create-a-project-with-remote-variables-in-windows-dev-center"></a>Erstellen eines Projekts mit Remotevariablen in Windows Dev Center

1. Melden Sie sich beim [Dev Center-Dashboard](https://dev.windows.com/overview) an.
2. Wenn Sie eine bereits in Dev Center vorhandene App zu Erstellen eines Experiments verwenden möchten, wählen Sie diese App im Dashboard aus. Wenn Ihr Dashboard noch keine App enthält, [erstellen Sie eine neue App durch Reservierung eines Namens](../publish/create-your-app-by-reserving-a-name.md) und wählen diese App dann im Dashboard aus.
3. Klicken Sie im Navigationsbereich auf **Dienste** und dann auf **Experimentation**.
4. Klicken Sie auf der nächsten Seite im Abschnitt **Projekte** auf die Schaltfläche **Neues Projekt**.
5. Geben Sie auf der Seite **Neues Projekt** den Namen **Button Click Experiments** für das neue Projekt ein.
6. Erweitern Sie den Abschnitt **Remotevariablen**, und klicken Sie viermal auf **Variable hinzufügen**. Sie sollten jetzt über vier leere Variablenzeilen verfügen.
  * Geben Sie in der ersten Zeile **buttonText** als Variablennamen und **Graue Schaltfläche** in der Spalte **Standardwert** ein.
  * Geben Sie in der zweiten Zeile **r** als Variablennamen und **128** in der Spalte **Standardwert** ein.
  * Geben Sie in der dritten Zeile **g** als Variablennamen und **128** in der Spalte **Standardwert** ein.
  * Geben Sie in der vierten Zeile **b** als Variablennamen und **128** in der Spalte **Standardwert** ein.
7. Klicken Sie auf **Speichern**, und notieren Sie den Wert der [Projekt-ID](run-app-experiments-with-a-b-testing.md#terms) im Abschnitt **SDK-Integration**. Im nächsten Abschnitt aktualisieren Sie den App-Code und verweisen im Code auf diesen Wert.

## <a name="code-the-experiment-in-your-app"></a>Codieren des Experiments in der App

1. Erstellen Sie in Visual Studio ein neues universelle Windows-Plattform-Projekt mit Visual c#. Geben Sie dem Projekt den Namen **SampleExperiment**.
2. Erweitern Sie im Projektmappen-Explorer den Projektknoten, klicken Sie mit der rechten Maustaste auf **Verweise**, und klicken Sie auf **Verweis hinzufügen**.
3. Erweitern Sie im **Verweis-Manager** die Option **Universelle Windows-App**, und klicken Sie auf **Erweiterungen**.
4. Aktivieren Sie in der Liste mit den SDKs das Kontrollkästchen neben **Microsoft Engagement Framework**, und klicken Sie anschließend auf **OK**.
5. Doppelklicken Sie im **Projektmappen-Explorer** auf „MainPage.xaml“, um den Designer für die Hauptseite in der App zu öffnen.
6. Ziehen Sie eine **Schaltfläche** aus der **Toolbox** auf die Seite.
7. Doppelklicken Sie im Designer auf die Schaltfläche, um die Codedatei zu öffnen, und fügen Sie einen Ereignishandler für das **Click**-Ereignis hinzu.  
8. Ersetzen Sie den gesamten Inhalt der Codedatei mit folgendem Code. Weisen Sie die ```projectId```-Variable dem Wert der [Projekt-ID](run-app-experiments-with-a-b-testing.md#terms) zu, den Sie im vorhergehenden Abschnitt aus dem Dev Center-Dashboard abgerufen haben.
    [!code-cs[SampleExperiment](./code/StoreSDKSamples/cs/ExperimentPage.xaml.cs#SampleExperiment)]

9. Speichern Sie die Codedatei, und erstellen Sie das Projekt.

## <a name="create-the-experiment-in-windows-dev-center"></a>Erstellen des Experiments in Windows Dev Center

1. Kehren Sie zur Projektseite **Button Click Experiments** im Windows Dev Center-Dashboard zurück.
2. Klicken Sie im Abschnitt **Experimente** auf die Schaltfläche **Neues Experiment**.
3. Geben Sie im Abschnitt **Experiment details** den Namen **Optimize Button Clicks** im Feld **Experiment name** ein.
4. Geben Sie im Abschnitt **View event** den Namen **userViewedButton** im Feld **Anzeige Ereignisname** ein. Dieser Name entspricht der Anzeigeereigniszeichenfolge, die Sie im Code protokolliert haben, der im vorherigen Abschnitt hinzugefügt wurde.
5. Geben Sie im Abschnitt **Goals and conversion events** die folgenden Werte ein:
  * Geben Sie im Feld **Goal name** **Increase Button Clicks** ein.
  * Geben Sie im Feld **Umwandlungsereignisname** den Namen **userClickedButton** ein. Dieser Name entspricht der Umwandlungsereigniszeichenfolge, die Sie im Code protokolliert haben, der im vorherigen Abschnitt hinzugefügt wurde.
  * Wählen Sie im Feld **Ziel** die Option **Maximieren**.
6. Stellen Sie im Abschnitt **Remote variables and variations** sicher, dass das Kontrollkästchen **Gleichmäßig verteilen** aktiviert ist, damit die Varianten gleichmäßig über Ihre App verteilt werden.
7. Fügen Sie dem Experiment Variablen hinzu:
    1. Klicken Sie auf das Dropdownsteuerelement, wählen Sie **buttonText** aus, und klicken Sie auf **Variable hinzufügen**. Die Zeichenfolge **Graue Schaltfläche** sollte automatisch in der Spalte **Variation A** angezeigt werden (dieser Wert wird von den Projekteinstellungen abgeleitet). Geben Sie in der Spalte **Variation B** den Text **Blaue Schaltfläche** ein.
    2. Klicken Sie erneut auf das Dropdownsteuerelement, wählen Sie **r** aus, und klicken Sie auf **Variable hinzufügen**. Die Zeichenfolge **128** sollte automatisch in der Spalte **Variation A** angezeigt werden. Geben Sie in der Spalte **Variation B** die Zahl **1** ein.
    3. Klicken Sie erneut auf das Dropdownsteuerelement, wählen Sie **g** aus, und klicken Sie auf **Variable hinzufügen**. Die Zeichenfolge **128** sollte automatisch in der Spalte **Variation A** angezeigt werden. Geben Sie in der Spalte **Variation B** die Zahl **1** ein.  
    4. Klicken Sie erneut auf das Dropdownsteuerelement, wählen Sie **b** aus, und klicken Sie auf **Variable hinzufügen**. Die Zeichenfolge **128** sollte automatisch in der Spalte **Variation A** angezeigt werden. Geben Sie in der Spalte **Variation B** die Zahl **255** ein.  
8. Klicken Sie auf **Speichern** und dann auf **Aktivieren**.

> [!IMPORTANT]
> Nach dem Aktivieren eines Experiments können Sie die Experimentparameter nicht mehr ändern, wenn Sie beim Erstellen des Experiments nicht auf das Kontrollkästchen **Editable experiment** geklickt haben. In der Regel wird empfohlen, das Experiment vor der Aktivierung in der App zu codieren.

## <a name="run-the-app-to-gather-experiment-data"></a>Ausführen der App, um Experimentdaten zu sammeln

1. Führen Sie die App **SampleExperiment** aus, die Sie zuvor erstellt haben.
2. Stellen Sie sicher, dass entweder eine graue oder eine blaue Schaltfläche angezeigt wird. Klicken Sie auf die Schaltfläche, und schließen Sie dann die App.
3. Wiederholen Sie die obigen Schritte auf demselben Computer mehrmals, um zu bestätigen, dass in Ihrer App die gleiche Schaltflächenfarbe angezeigt wird.

## <a name="review-the-results-and-complete-the-experiment"></a>Überprüfen der Ergebnisse Abschließen des Experiments

Warten Sie nach Abschluss des vorherigen Abschnitts mindestens ein paar Stunden, und führen Sie dann diese Schritte aus, um die Ergebnisse Ihres Experiments zu überprüfen und das Experiment abzuschließen.

> [!NOTE]
> Wenn Sie ein Experiment aktivieren, beginnt Dev Center umgehend mit der Erfassung von Daten aus allen Apps, die zum Protokollieren von Daten für Ihr Experiment instrumentiert sind. Bis zur Anzeige von Experimentdaten im Dashboard können jedoch mehrere Stunden vergehen.

1. Kehren Sie in Dev Center zur Seite **Experimentation** für Ihre App zurück.
2. Klicken Sie im Abschnitt **Active experiments** auf **Optimize Button Clicks**, um zur Seite für dieses Experiment zu wechseln.
3. Vergewissern Sie sich, dass die Ergebnisse in den Abschnitten **Results summary** und **Results details** Ihren Erwartungen entsprechen. Ausführlichere Informationen zu diesen Abschnitten finden Sie unter [Verwalten des Experiments im Dev Center-Dashboard](manage-your-experiment.md#review-the-results-of-your-experiment).
    > [!NOTE]
    > Dev Center meldet nur das erste Umwandlungsereignis für jeden Benutzer innerhalb eines Zeitraums von 24 Stunden. Wenn ein Benutzer innerhalb von 24 Stunden mehrere Umwandlungsereignisse in Ihrer App auslöst, wird nur das erste Umwandlungsereignis gemeldet. So soll verhindert werden, dass die Experimentergebnisse für eine Stichprobengruppe von Benutzern durch einen einzelnen Benutzer mit mehreren Umwandlungsereignissen verfälscht wird.

4. Jetzt sind Sie bereit, das Experiment zu beenden. Klicken Sie im Abschnitt **Results summary** in der Spalte **Variation B** auf **Wechseln**. Dadurch wird für alle Benutzer Ihrer App zur blauen Schaltfläche gewechselt.
5. Klicken Sie auf **OK**, um zu bestätigen, dass Sie das Experiment beenden möchten.
6. Führen Sie die App **SampleExperiment** aus, die Sie im vorhergehenden Abschnitt erstellt haben.
7. Vergewissern Sie sich, dass eine blaue Schaltfläche angezeigt wird. Beachten Sie, dass es bis zu zweiMinuten dauern kann, bis Ihre App eine aktualisierte Variantenzuweisung erhält.

## <a name="related-topics"></a>Verwandte Themen

* [Erstellen eines Projekts und Festlegen von Remotevariablen im Dev Center-Dashboard](create-a-project-and-define-remote-variables-in-the-dev-center-dashboard.md)
* [Programmieren Ihrer App für Experimente](code-your-experiment-in-your-app.md)
* [Definieren des Experiments im Dev Center-Dashboard](define-your-experiment-in-the-dev-center-dashboard.md)
* [Verwalten des Experiments im Dev Center-Dashboard](manage-your-experiment.md)
* [Ausführen von App-Experimenten mit A/B-Tests](run-app-experiments-with-a-b-testing.md)
