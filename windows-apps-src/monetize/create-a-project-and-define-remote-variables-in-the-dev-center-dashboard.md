---
author: Xansky
Description: Before you can run an experiment in your Universal Windows Platform (UWP) app with A/B testing, you must create a project and define your remote variables in Partner Center.
title: Erstellen eines experimentprojekts im Partner Center
ms.assetid: C3809FF1-0A6A-4715-B989-BE9D0E8C9013
ms.author: mhopkins
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Microsoft Store Services SDK, A/B-Tests, Experimente
ms.localizationpriority: medium
ms.openlocfilehash: 19a59110fa094aeae3d40dca1372fde9889c108e
ms.sourcegitcommit: e814a13978f33654d8e995584f4b047cb53e0aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "6047801"
---
# <a name="create-an-experiment-project-in-partner-center"></a>Erstellen eines experimentprojekts im Partner Center

Erste Schritte mit experimentieren, erstellen Sie ein Experiment- [Projekt](run-app-experiments-with-a-b-testing.md#terms) für Ihre app im Partner Center und definieren Sie die remotevariablen, die Ihre app zugreifen kann.

Die folgenden Anweisungen beschreiben die wichtigsten Schritte für die Erstellung eines Projekts. Eine ausführliche Erläuterung, die den gesamten Erstellungs- und Ausführungsprozess für ein Projekt und die Durchführung eines Experiments veranschaulicht, finden Sie unter [Erstellen und Durchführen eines ersten Experiments mit A/B-Tests](create-and-run-your-first-experiment-with-a-b-testing.md).

## <a name="instructions"></a>Anweisungen

1. Melden Sie sich im [Partner Center](https://partner.microsoft.com/dashboard) an.
2. Wählen Sie unter **Ihre Apps** die App aus, für die Sie ein Experiment erstellen möchten.
3. Wählen Sie im Navigationsbereich **Dienste** und dann **Experimente**.
4. Klicken Sie auf der Seite **Experimente** im Abschnitt **Projekte** auf die Schaltfläche **Neues Projekt**. Wenn Sie bereits ein oder mehrere Projekte erstellt haben, werden diese Projekte im Abschnitt **Projekte** aufgeführt.
5. Geben Sie auf der Seite **Neues Projekt** einen Namen für das neue Projekt ein.
6. Fügen Sie im Abschnitt **Remotevariablen** die [Variablen](run-app-experiments-with-a-b-testing.md#terms) hinzu, die für alle Experimente in diesem Projekt verfügbar sein sollen, und definieren Sie die Standardwerte für jede Variable. Die hier festgelegten Standardwerte werden für die Steuerelementgruppe der Experimente verwendet, sowie für alle Benutzer, die an dem Experiment nicht teilnehmen.
  1. Falls der Abschnitt **Remotevariablen** reduziert ist, klicken Sie in der Abschnittsüberschrift auf **Anzeigen**.
  2. Klicken Sie auf **Variable hinzufügen**, um jede neue Variable zu erstellen, die für jedes Experiment in diesem Projekt verfügbar sein soll, und geben Sie den Variablennamen und den Standardwert der Variablen ein.
  3. Wenn Sie das Hinzufügen von Variablen beendet haben, klicken Sie auf **Speichern**.
3. Notieren Sie im Abschnitt **SDK-Integration** den Wert der [Projekt-ID](run-app-experiments-with-a-b-testing.md#terms). Wenn müssen Sie [Ihrer App programmiert haben](code-your-experiment-in-your-app.md), Sie verweisen diese Projekt-ID in Ihrem Code damit Sie Variantendaten empfangen sowie Anzeige-und umwandlungsereignisse an Partner Center melden können.

> [!NOTE]
> Sie können keine Remotevariablen bearbeiten, hinzufügen oder entfernen, während ein Experiment im Projekt aktiv ist. Diese Einschränkung hilft, die Integrität der Daten der Steuerelementgruppe für das aktive Experiment zu schützen.


## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie ein Projekt erstellt haben, können Sie mit dem [Codieren der App für das Experiment](code-your-experiment-in-your-app.md) beginnen, indem Sie Werte von Remotevariablen in Ihrer App abrufen, und Sie können [ein Experiment im Projekt erstellen](define-your-experiment-in-the-dev-center-dashboard.md).

## <a name="related-topics"></a>Verwandte Themen

* [Codieren der App für das Experiment](code-your-experiment-in-your-app.md)
* [Definieren Sie Ihres Experiments im Partner Center](define-your-experiment-in-the-dev-center-dashboard.md)
* [Verwalten des Experiments im Partner Center](manage-your-experiment.md)
* [Erstellen und Ausführen eines ersten Experiments mit A/B-Tests](create-and-run-your-first-experiment-with-a-b-testing.md)
* [Ausführen von App-Experimenten mit A/B-Tests](run-app-experiments-with-a-b-testing.md)
