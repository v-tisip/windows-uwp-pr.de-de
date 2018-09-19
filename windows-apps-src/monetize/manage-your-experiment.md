---
author: mcleanbyron
Description: After you define your experiment in the Dev Center dashboard and code your experiment in your app, you are ready to active your experiment and use the Dev Center dashboard to review the results of your experiment.
title: Verwalten Ihres Experiments im Dashboard
ms.assetid: D48EE0B4-47F2-455C-8FB9-630769AC5ACE
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Microsoft Store Services SDK, A/B-Tests, Experimente
ms.localizationpriority: medium
ms.openlocfilehash: 073d5ec67bb012cbfe21c279ee97ec3c50b8458f
ms.sourcegitcommit: 68fcac3288d5698a13dbcbd57f51b30592f24860
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2018
ms.locfileid: "4057172"
---
# <a name="manage-your-experiment-in-the-dashboard"></a>Verwalten Ihres Experiments im Dashboard

Nachdem Sie [Ihr Experiment im Dev Center-Dashboard definiert](define-your-experiment-in-the-dev-center-dashboard.md) und [in Ihrer App programmiert haben](code-your-experiment-in-your-app.md), können Sie das Experiment aktivieren und das Dev Center-Dashboard zum Prüfen der Ergebnisse Ihres Experiments verwenden. Nach Abrufen aller benötigten Daten können Sie das Experiment beenden und festlegen, ob die Variablenwerte in der Steuerungsvariation für alle Apps weiter verwendet werden sollen oder die Variablenwerte einer anderen Variation verwendet werden sollen.

> [!NOTE]
> Wenn Sie ein Experiment aktivieren, beginnt Dev Center umgehend mit der Erfassung von Daten aus allen Apps, die zum Protokollieren von Daten für Ihr Experiment instrumentiert sind. Bis zur Anzeige von Experimentdaten im Dashboard können jedoch mehrere Stunden vergehen.

Eine exemplarische Vorgehensweise, die den gesamten Erstellungs- und Ausführungsprozess für ein Experiment veranschaulicht, finden Sie unter [Erstellen und Durchführen eines ersten Experiments mit A/B-Tests](create-and-run-your-first-experiment-with-a-b-testing.md).

## <a name="activate-your-experiment"></a>Aktivieren Ihres Experiments

Wenn Sie mit den Parametern für Ihr Experiment im Dashboard zufrieden sind und den App-Code aktualisiert haben, können Sie Ihr Experiment aktivieren, damit mit der Erfassung der Experimentdaten aus Ihrer App begonnen wird. Wenn das Experiment aktiv ist, kann Ihre App Variationswerte abrufen und Anzeige- und Umwandlungsereignisse im Dev Center melden.

1. Melden Sie sich beim [Dev Center-Dashboard](https://dev.windows.com/overview) an.
2. Wählen Sie unter **Ihre Apps** die App mit dem Experiment, das Sie aktivieren möchten.
3. Wählen Sie im Navigationsbereich **Dienste** und dann **Experimentation** aus.
4. Erweitern Sie in der Tabelle der Projekte im Abschnitt **Projekte** das Projekt, das Ihr Experiment enthält, und führen Sie dann eine der folgenden Aufgaben aus:
  * Klicken Sie auf den Link **Aktivieren** für Ihr Experiment. Ihr Experiment wird dem Abschnitt **Aktive Experimente** im oberen Bereich der Seite hinzugefügt.
  * Klicken Sie auf den Namen des Experiments, führen Sie auf der Seite für Experimente einen Bildlauf nach unten aus, und klicken Sie auf **Aktivieren**.

> [!IMPORTANT]
> Nach dem Aktivieren eines Experiments können Sie die Experimentparameter nicht mehr ändern, wenn Sie beim Erstellen des Experiments nicht auf das Kontrollkästchen **Editable experiment** geklickt haben. Es wird empfohlen, das Experiment vor der Aktivierung in der App zu codieren.

## <a name="review-the-results-of-your-experiment"></a>Prüfen der Experimentergebnisse

1. Kehren Sie in Dev Center zur Seite **Experimentation** für Ihre App zurück.
2. Klicken Sie im Abschnitt **Aktive Experimente** auf den Namen des aktiven Experiments, um zur Experimentseite zu wechseln.
3. Bei aktiven oder beendeten Experimenten enthalten die ersten zwei Abschnitte auf dieser Seite die Ergebnisse Ihres Experiments:
  * Der Abschnitt **Ergebniszusammenfassung** enthält die Experimentziele und die Umwandlungsquote für jede Variation.
  * Der Abschnitt **Ergebnisdetails** enthält ausführlichere Informationen zu den einzelnen Varianten all der Ziele im Experiment, einschließlich Ansichten, Konvertierungen, eindeutiger Benutzer, Umwandlungsquote, Delta in %, Konfidenz und Signifikanz. Die *Konfidenz* ist ein statistisches Maß zum Angeben der Zuverlässigkeit einer Schätzung, mit dem die Fehlerspanne ermittelt wird. Die *Signifikanz* ist ein statistisches Maß, mit dem basierend auf einer Stichprobe die Wahrscheinlichkeit dafür bestimmt wird, dass ein Ergebnis nicht zufällig ist, sondern auf eine bestimmte Ursache zurückzuführen ist.

> [!NOTE]
> Dev Center meldet nur das erste Umwandlungsereignis für jeden Benutzer innerhalb eines Zeitraums von 24 Stunden. Wenn ein Benutzer innerhalb von 24 Stunden mehrere Umwandlungsereignisse in Ihrer App auslöst, wird nur das erste Umwandlungsereignis gemeldet. So soll verhindert werden, dass die Experimentergebnisse für eine Stichprobengruppe von Benutzern durch einen einzelnen Benutzer mit mehreren Umwandlungsereignissen verfälscht wird.


## <a name="complete-your-experiment"></a>Beenden Ihres Experiments

1. Kehren Sie Im Dashboard zur Experimentseite zurück. Einzelheiten dazu finden Sie im vorherigen Abschnitt.
2. Führen Sie im Abschnitt **Ergebniszusammenfassung** eine der folgenden Aktionen durch:
  * Klicken Sie zum Beenden des Experiments und zum weiteren Verwenden der Variablenwerte der Steuerungsvariation für Ihre App auf **Beibehalten**.
  * Klicken Sie zum Beenden des Experiments und zum Verwenden der Variablenwerte einer anderen Variation für Ihre App unter der Variation, zu der Sie wechseln möchten, auf **Wechseln**.
3. Klicken Sie auf **OK**, um zu bestätigen, dass Sie das Experiment beenden möchten.


## <a name="related-topics"></a>Verwandte Themen

* [Erstellen eines Projekts und Festlegen von Remotevariablen im Dev Center-Dashboard](create-a-project-and-define-remote-variables-in-the-dev-center-dashboard.md)
* [Programmieren Ihrer App für Experimente](code-your-experiment-in-your-app.md)
* [Definieren Ihres Experiments im Dev Center-Dashboard](define-your-experiment-in-the-dev-center-dashboard.md)
* [Erstellen und Ausführen Ihres ersten Experiments mit A/B-Tests](create-and-run-your-first-experiment-with-a-b-testing.md)
* [Ausführen von App-Experimenten mit A/B-Tests](run-app-experiments-with-a-b-testing.md)
