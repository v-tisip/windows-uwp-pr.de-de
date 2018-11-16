---
author: Xansky
Description: You can use Partner Center to run experiments for your Universal Windows Platform (UWP) apps with A/B testing.
title: Ausführen von App-Experimenten mit A/B-Tests
ms.assetid: 790B4B37-C72D-4CEA-97AF-D226B2216DCC
ms.author: mhopkins
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP, Microsoft Store Services SDK, A/B-Tests, Experimente
ms.localizationpriority: medium
ms.openlocfilehash: 6697d522ee14a00bb8cb9c0c2c367f01d6e50ef4
ms.sourcegitcommit: e38b334edb82bf2b1474ba686990f4299b8f59c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6854738"
---
# <a name="run-app-experiments-with-ab-testing"></a>Ausführen von App-Experimenten mit A/B-Tests

Sie können Partner Center verwenden, um remote-Variablen definieren, die Sie zur Laufzeit aus Ihrer universellen Windows-Plattform (UWP) apps abrufen können, und Sie können Varianten dieser Werte testen, mit Ihren Benutzern die effektivsten Werte für die gewünschte Benutzerverhalten zu identifizieren. Ihre App kann Remotevariablen verwenden, um App-Funktionen zu konfigurieren, z. B. In-App-Käufe, Anmeldungsfluss, Überschriften und Platzierung von Werbung.

Ziel des A/B-Tests sollte sein, eine Variante Ihrer Remotevariablenwerte zu identifizieren, die Ihnen wahrscheinlich bessere Konversionsraten einbringt (z.B. mehr In-App-Käufe), da eine interessantere App-Erfahrung bereitgestellt wird. Nachdem Sie eine erfolgreiche Variante identifiziert haben, können Sie sofort Beenden des Experiments und diese Variante für die gesamte Zielgruppe aus dem Partner Center, ohne die app erneut veröffentlichen aktivieren.

## <a name="create-and-run-an-ab-test"></a>Erstellen und Ausführen eines A/B-Tests

Führen Sie zum Erstellen und Ausführen eines A/B-Tests die folgenden Schritte aus:

1. [Erstellen eines Projekts und Festlegen von remotevariablen im Partner Center](create-a-project-and-define-remote-variables-in-the-dev-center-dashboard.md). Dieses Projekt enthält die Variablen und Standardvariablenwerte für Ihre Experimente.  
2. [Codieren der App für das Experiment](code-your-experiment-in-your-app.md). Verwenden Sie eine API zum Abrufen von remotevariablenwerte aus dem Projekt, das Sie im Partner Center erstellt haben, verwenden Sie diese Daten zum Ändern des Verhaltens des Features, die Sie testen möchten, und senden anzeigeereignis und umwandlungsereignisse an Partner Center im Microsoft Store Services SDK.
3. [Definieren Ihres Experiments im Partner Center ](define-your-experiment-in-the-dev-center-dashboard.md). Erstellen Sie ein Experiment in Ihrem Projekt, das die eindeutigen Ziele und Varianten für Ihren A/B-Test definiert.
4. [Ausführen und Verwalten des Experiments im Partner Center ashboardseite](manage-your-experiment.md). Aktivieren Sie Ihr Experiment, und verwenden Sie Partner Center zum Überprüfen der Ergebnisse des Experiments und das Experiment abzuschließen.

Eine exemplarische Vorgehensweise, in der der Prozess vollständig dargestellt wird, finden Sie unter [Create and run your first experiment with A/B testing](create-and-run-your-first-experiment-with-a-b-testing.md) (Erstellen und Ausführen eines ersten Experiments mit A/B-Tests).

## <a name="requirements"></a>Anforderungen

A / B-Tests im Partner Center wird nur für UWP-apps unterstützt.

Damit Sie Experimente mit A/B-Tests ausführen können, müssen Sie den Entwicklungscomputer einrichten:

* Führen Sie [diese Anweisungen](../get-started/get-set-up.md) aus, um den Entwicklungscomputer für die UWP-Entwicklung einzurichten.
* [Installieren Sie das Microsoft Store Services SDK](microsoft-store-services-sdk.md#install-the-sdk). Zusätzlich zur API für Experimente bietet dieses SDK auch APIs für weitere Features wie z.B. das Anzeigen von Werbung und das Weiterleiten von Kunden zum Feedback-Hub, um Feedback zur App zu erfassen.

## <a name="best-practices"></a>Bewährte Verfahren

Um möglichst aussagekräftige Ergebnisse zu erzielen, sollten Sie beim Durchführen von Experimenten mit A/B-Tests diese Empfehlungen berücksichtigen:

* Führen Sie Experimente mit nur zwei Varianten mit einer zufälligen 50/50-Aufteilung für Variantenzuweisungen durch.
* Führen Sie die Experimente mindestens 2 bis 4Wochen lang durch, um ausreichend Daten zu erfassen, die statistisch signifikant und aussagekräftig sind.

<span id="terms" />

## <a name="related-terms"></a>Verwandte Begriffe

|  Begriff  |  Definition  |
|--------|--------------|
| Projekt    |   Eine Auflistung von Remotevariablen mit Standardwerten, auf die Ihre App mithilfe des Microsoft Store Services SDK zugreifen kann. Ein Projekt kann optional auch ein oder mehrere Experimente enthalten, die die gleichen Remotevariablen nutzen.  |
| Experiment    |   Ein Satz von Parametern, die einen A/B-Test definieren, den Ihre Benutzer erhalten. Experimente sind im Umfang eines Projekts definiert. Jedes Experiment besteht aus folgenden Elementen: <p></p><ul><li>Ein *Anzeigeereignis*, das angibt, wann der Benutzer mit dem Anzeigen einer Variante beginnt, die Teil des Experiments ist.</li><li>Eines oder mehrere Ziele mit *Umwandlungsereignissen*, um anzugeben, wann ein Ziel erreicht wurde.</li><li>Eine oder mehrere *Varianten*, die die im Experiment verwendeten Variablendaten definieren. Die *Steuerelement*-Variante verwendet die Standardvariablenwerte, die im Projekt für das Experiment definiert sind. Zusätzlich zu der Steuerungsvariation verfügen Experimente in der Regel über mindestens eine zusätzliche Variante mit Variablenwerten, die speziell für das Experiment gelten. </li></ul>          |
| Projekt-ID    |   Eine eindeutige ID, die Ihre app mit einem Projekt in Ihrem Partner Center-Konto verknüpft. Sie müssen diese ID verwenden, für die Verbindung mit dem A / B-Testdienst in Ihrer app-Code, um Variantendaten empfangen sowie Anzeige-und umwandlungsereignisse an das Partner Center melden. Weitere Informationen finden Sie unter [Programmieren Ihrer App für Experimente](code-your-experiment-in-your-app.md).<p></p><p>Jedes Projekt und alle Experimente im Projekt sind genau einer Projekt-ID zugeordnet. Sie können Projekt-IDs verwenden, um zwischen verschiedenen Gruppen von Experimenten zu unterscheiden. Beispielsweise haben Sie möglicherweise einen Satz von Experimenten, den Sie für Tester in Ihrer Organisation freigeben, und einen anderen Satz von Experimenten, den Sie nur für externe Benutzer Ihrer App freigeben.  Eine App kann auf mehrere Projekt-IDs verweisen, wenn sie mehrere Experimente implementiert.</p>         |
| Variante    |   Eine Sammlung von einer oder mehreren Variablen, die Sie in Ihrem Experiment testen. Jedes Experiment muss mindestens eine Variable und zwei Varianten umfassen (einschließlich des Steuerelements). Ein Experiment kann bis zu fünf Varianten aufweisen.           |
| Variable    |  Ein Wert, den Ihre App verwendet, um eine Eigenschaft oder einen anderen Wert in Ihrer App zu initialisieren. Während eines Experiments ändert sich der Wert der Variable von Variante zu Variante. Nachdem Sie das Experiment beendet haben, wird die Variable dem Wert der Variante zugewiesen, die Sie für die Freigabe für alle Benutzer Ihrer App auswählen. Variablen können die folgenden Typen aufweisen: eine Zeichenfolge, Boolean, Double und ganze Zahl.
| Anzeigeereignis    |  Eine beliebige Zeichenfolge, die eine Aktivität darstellt, wenn der Benutzer beginnt, eine Variante anzuzeigen, die Teil Ihres Experiments ist. In der Regel ist dies der Name eines Ereignisses in Ihrem Code. App-Code sendet Zeichenfolge des anzeigeereignisses für das Partner Center, wenn der Benutzer beginnt, eine Variante. Weitere Informationen finden Sie unter [Programmieren Ihrer App für Experimente](code-your-experiment-in-your-app.md).
| Umwandlungsereignis    |  Eine beliebige Zeichenfolge, die eine Zielsetzung für das Ziel eines Experiments darstellt. In der Regel ist dies der Name eines Ereignisses in Ihrem Code. App-Code sendet diese umwandlungsereignis-Zeichenfolge in das Partner Center, wenn der Benutzer ein Ziel erreicht. Weitere Informationen finden Sie unter [Programmieren Ihrer App für Experimente](code-your-experiment-in-your-app.md).  

## <a name="related-topics"></a>Verwandte Themen

* [Erstellen eines Projekts und Festlegen von remotevariablen im Partner Center](create-a-project-and-define-remote-variables-in-the-dev-center-dashboard.md)
* [Codieren der App für Tests](code-your-experiment-in-your-app.md)
* [Definieren Sie Ihres Experiments im Partner Center](define-your-experiment-in-the-dev-center-dashboard.md)
* [Verwalten des Experiments im Partner Center](manage-your-experiment.md)
* [Erstellen und Ausführen Ihres ersten Experiments mit A/B-Tests](create-and-run-your-first-experiment-with-a-b-testing.md)
