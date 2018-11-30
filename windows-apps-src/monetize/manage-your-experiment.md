---
Description: After you define your experiment in Partner Center and code your experiment in your app, you are ready to active your experiment and use Partner Center to review the results of your experiment.
title: Verwalten eines Experiments im Partner Center
ms.assetid: D48EE0B4-47F2-455C-8FB9-630769AC5ACE
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Microsoft Store Services SDK, A/B-Tests, Experimente
ms.localizationpriority: medium
ms.openlocfilehash: 6e5c0d0ca1b1d771df2b224cc41ec5a37e267bc9
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8207008"
---
# <a name="manage-your-experiment-in-partner-center"></a>Verwalten eines Experiments im Partner Center

Nachdem Sie [Ihr Experiment im Partner Center definiert](define-your-experiment-in-the-dev-center-dashboard.md) und [Ihrer App programmiert haben](code-your-experiment-in-your-app.md)können Sie Ihr Experiment aktivieren und Partner Center zum Prüfen der Ergebnisse Ihres Experiments verwenden. Nach Abrufen aller benötigten Daten können Sie das Experiment beenden und festlegen, ob die Variablenwerte in der Steuerungsvariation für alle Apps weiter verwendet werden sollen oder die Variablenwerte einer anderen Variation verwendet werden sollen.

> [!NOTE]
> Wenn Sie ein Experiment aktivieren, beginnt Partner Center umgehend mit der Erfassung von Daten aus allen apps, die zum Protokollieren von Daten für Ihr Experiment instrumentiert sind. Es kann jedoch mehrere Stunden experimentdaten im Partner Center dauern.

Eine exemplarische Vorgehensweise, die den gesamten Erstellungs- und Ausführungsprozess für ein Experiment veranschaulicht, finden Sie unter [Erstellen und Durchführen eines ersten Experiments mit A/B-Tests](create-and-run-your-first-experiment-with-a-b-testing.md).

## <a name="activate-your-experiment"></a>Aktivieren Ihres Experiments

Wenn Sie mit den Parametern für Ihr Experiment im Partner Center zufrieden sind und Ihr app-Code aktualisiert haben, können Sie Ihr Experiment aktivieren, damit Sie mit der Erfassung der experimentdaten aus Ihrer app beginnen können. Wenn das Experiment aktiv ist, kann Ihre app variationswerte abrufen und Anzeige-und umwandlungsereignisse an das Partner Center melden.

1. Melden Sie sich im [Partner Center](https://partner.microsoft.com/dashboard) an.
2. Wählen Sie unter **Ihre Apps** die App mit dem Experiment, das Sie aktivieren möchten.
3. Wählen Sie im Navigationsbereich **Dienste** und dann **Experimentation** aus.
4. Erweitern Sie in der Tabelle der Projekte im Abschnitt **Projekte** das Projekt, das Ihr Experiment enthält, und führen Sie dann eine der folgenden Aufgaben aus:
  * Klicken Sie auf den Link **Aktivieren** für Ihr Experiment. Ihr Experiment wird dem Abschnitt **Aktive Experimente** im oberen Bereich der Seite hinzugefügt.
  * Klicken Sie auf den Namen des Experiments, führen Sie auf der Seite für Experimente einen Bildlauf nach unten aus, und klicken Sie auf **Aktivieren**.

> [!IMPORTANT]
> Nach dem Aktivieren eines Experiments können Sie die Experimentparameter nicht mehr ändern, wenn Sie beim Erstellen des Experiments nicht auf das Kontrollkästchen **Editable experiment** geklickt haben. Es wird empfohlen, das Experiment vor der Aktivierung in der App zu codieren.

## <a name="review-the-results-of-your-experiment"></a>Prüfen der Experimentergebnisse

1. Im Partner Center zur Seite zurückkehren Sie, **Experimente** für Ihre app.
2. Klicken Sie im Abschnitt **Aktive Experimente** auf den Namen des aktiven Experiments, um zur Experimentseite zu wechseln.
3. Bei aktiven oder beendeten Experimenten enthalten die ersten zwei Abschnitte auf dieser Seite die Ergebnisse Ihres Experiments:
  * Der Abschnitt **Ergebniszusammenfassung** enthält die Experimentziele und die Umwandlungsquote für jede Variation.
  * Der Abschnitt **Ergebnisdetails** enthält ausführlichere Informationen zu den einzelnen Varianten all der Ziele im Experiment, einschließlich Ansichten, Konvertierungen, eindeutiger Benutzer, Umwandlungsquote, Delta in %, Konfidenz und Signifikanz. Die *Konfidenz* ist ein statistisches Maß zum Angeben der Zuverlässigkeit einer Schätzung, mit dem die Fehlerspanne ermittelt wird. Die *Signifikanz* ist ein statistisches Maß, mit dem basierend auf einer Stichprobe die Wahrscheinlichkeit dafür bestimmt wird, dass ein Ergebnis nicht zufällig ist, sondern auf eine bestimmte Ursache zurückzuführen ist.

> [!NOTE]
> Partner Center meldet nur das erste umwandlungsereignis für jeden Benutzer innerhalb eines Zeitraums von 24 Stunden. Wenn ein Benutzer innerhalb von 24 Stunden mehrere Umwandlungsereignisse in Ihrer App auslöst, wird nur das erste Umwandlungsereignis gemeldet. So soll verhindert werden, dass die Experimentergebnisse für eine Stichprobengruppe von Benutzern durch einen einzelnen Benutzer mit mehreren Umwandlungsereignissen verfälscht wird.


## <a name="complete-your-experiment"></a>Beenden Ihres Experiments

1. Im Partner Center kehren Sie zur experimentseite zurück. Einzelheiten dazu finden Sie im vorherigen Abschnitt.
2. Führen Sie im Abschnitt **Ergebniszusammenfassung** eine der folgenden Aktionen durch:
  * Klicken Sie zum Beenden des Experiments und zum weiteren Verwenden der Variablenwerte der Steuerungsvariation für Ihre App auf **Beibehalten**.
  * Klicken Sie zum Beenden des Experiments und zum Verwenden der Variablenwerte einer anderen Variation für Ihre App unter der Variation, zu der Sie wechseln möchten, auf **Wechseln**.
3. Klicken Sie auf **OK**, um zu bestätigen, dass Sie das Experiment beenden möchten.


## <a name="related-topics"></a>Verwandte Themen

* [Erstellen eines Projekts und Festlegen von remotevariablen im Partner Center](create-a-project-and-define-remote-variables-in-the-dev-center-dashboard.md)
* [Codieren einer App für Experimente](code-your-experiment-in-your-app.md)
* [Definieren eines Experiments im Partner Center](define-your-experiment-in-the-dev-center-dashboard.md)
* [Erstellen und Ausführen eines ersten Experiments mit A/B-Tests](create-and-run-your-first-experiment-with-a-b-testing.md)
* [Ausführen von App-Experimenten mit A/B-Tests](run-app-experiments-with-a-b-testing.md)
