---
author: TylerMSFT
title: "Entwickeln Sie Apps für das Bildungswesen."
description: "In diesem Abschnitt werden die für Sie verfügbaren App-Ressourcen der Universellen Windows-Plattform beschrieben, die Sie zum Schreiben von Bildungs-Apps für die Plattform Windows 10 verwenden können."
ms.author: twhitney
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.assetid: 2431f253-efe3-4895-b131-34653b61f13c
ms.openlocfilehash: 1750a75657affc0d7557afe393084f88630a7366
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="develop-universal-windows-apps-for-education"></a>Entwickeln von Bildungs-Apps für die Universelle Windows-Plattform
![Screenshot, Prüfungs-App](images/take-a-test-screen-small.png)

Die folgenden Ressourcen unterstützen Sie beim Schreiben einer Bildungs-App für die Universelle Windows-Plattform.

### <a name="accessibility"></a>Bedienungshilfen
Bildungs-Apps müssen barrierefrei sein. Weitere Informationen finden Sie unter [Entwickeln von Apps für Barrierefreiheit](https://developer.microsoft.com/windows/accessible-apps).


### <a name="secure-assessments"></a>Sichere Bewertungen
Apps für Bewertungen oder Tests müssen oft eine *gesperrte* Umgebung bereitstellen, um zu verhindern, dass die Lernenden während eines Tests andere Computer oder Internetressourcen verwenden. Diese Funktion wird über die [Prüfungs-API](take-a-test-api.md) bereitgestellt. Ein Beispiel einer Prüfungsumgebung mit gesperrtem Onlinezugriff für ernsthafte Prüfungen finden Sie in der Web-App [Prüfung](https://technet.microsoft.com/edu/windows/take-tests-in-windows-10) im Windows IT Center.

### <a name="user-input"></a>Benutzereingabe
Benutzereingaben sind ein wichtiger Bestandteil von Apps für Bildungszwecke. Die Steuerelemente auf der Benutzeroberfläche müssen gut reagieren und intuitiv bedienbar sein, damit die Aufmerksamkeit der Benutzer für die Inhalte nicht gestört wird. Eine allgemeine Übersicht der in einer universellen Windows-App verfügbaren Eingabeoptionen finden Sie unter [Einführung in Eingaben](https://msdn.microsoft.com/windows/uwp/input-and-devices/input-primer) und in den nachfolgenden Themen im Abschnitt „Design und UI“. Dazu zeigen die folgenden Beispiel-Apps den grundlegenden Umgang mit der Benutzeroberfläche in der universellen Windows-Plattform.
- Das [einfache Eingabebeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicInput) veranschaulicht die Behandlung von Eingaben in universellen Windows-Apps.
- Das [Beispiel für den Benutzerinteraktionsmodus](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/UserInteractionMode) zeigt, wie Sie den Benutzerinteraktionsmodus erkennen und auf ihn reagieren.
- Das [Beispiel für visuelle Fokuselemente](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlFocusVisuals) zeigt, wie Sie die neuen visuellen Systemfokuselemente nutzen oder eigene visuelle Fokuselemente erstellen, wenn sich die vom System bereitgestellten Elemente nicht für Ihre Anforderungen eignen.

Die Windows Ink-Plattform kann Apps für Bildungszwecke unterstützen, indem diese an ein Eingabeverfahren angepasst werden, mit dem die Lernenden gut vertraut sind. Eine umfassende Anleitung zur Implementierung von Windows Ink in Ihrer App finden Sie unter [Zeichenstiftinteraktionen und Windows Ink](https://msdn.microsoft.com/windows/uwp/input-and-devices/pen-and-stylus-interactions) und den darauf folgenden Themen. Die folgenden Beispiel-Apps illustrieren diese API.
- [Freihandbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Ink) demonstriert die Verwendung der Freihandfunktion (Erfassung, Manipulation und Interpretation von Freihandstrichen) in universellen Windows-Apps mit JavaScript.
- Das [einfache Freihandbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SimpleInk) veranschaulicht die Verwendung der Freihandfunktion (beispielsweise das Erfassen von Freihandeingaben des Benutzers und Durchführen der Schrifterkennung für Freihandstriche) in universellen Windows-Apps mit C#.
- Das [komplexe Freihandbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ComplexInk) veranschaulicht die Verwendung der erweiterten InkPresenter-Funktion zum Überlappen von Freihandeingaben mit anderen Objekten, Auswählen der Freihandeingabe, Kopieren/Einfügen und Behandeln von Ereignissen. Es basiert auf der universellen Windows-Plattform in C++ und kann auf Windows10-SKUs für Desktops und mobile Geräte ausgeführt werden.


### <a name="windows-store"></a>Windows Store
Apps für Bildungszwecke werden oft unter speziellen Umständen für eine bestimmte Organisation veröffentlicht. Informationen dazu finden Sie unter [Verteilen von branchenspezifischen Apps an Unternehmen](https://msdn.microsoft.com/windows/uwp/publish/distribute-lob-apps-to-enterprises).

## <a name="related-topics"></a>Verwandte Themen
- [Windows 10 for Education](https://technet.microsoft.com/edu/windows/index) im Windows-IT Center
