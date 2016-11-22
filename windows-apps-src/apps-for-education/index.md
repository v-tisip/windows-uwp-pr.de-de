---
author: TylerMSFT
title: "Entwickeln Sie Apps für das Bildungswesen."
description: "In diesem Abschnitt werden die Ressourcen für universelle Windows-Apps beschrieben, die Ihnen zum Erstellen von Bildungs-Apps für die Windows10-Plattform zur Verfügung stehen."
translationtype: Human Translation
ms.sourcegitcommit: 48fcfe2b033614b445a1be6d757a8d208c7b1292
ms.openlocfilehash: bb401b73432c072d551814dec9504a7d1742b7d4

---
# Entwickeln von universellen Windows-Apps für das Bildungswesen
Die folgenden Ressourcen unterstützen Sie beim Erstellen universeller Windows-Apps für das Bildungswesen.

### Bedienungshilfen
Bildungs-Apps müssen barrierefrei sein. Weitere Informationen finden Sie unter [Entwickeln von Apps für Barrierefreiheit](https://developer.microsoft.com/windows/accessible-apps).


### Sichere Bewertungen
Apps für Bewertungen oder Tests müssen oft eine *gesperrte* Umgebung bereitstellen, um zu verhindern, dass die Lernenden während eines Tests andere Computer oder Internetressourcen verwenden. Diese Funktion wird über die [Prüfungs-API](take-a-test-api.md) bereitgestellt. Ein Beispiel einer Prüfungsumgebung mit gesperrtem Onlinezugriff für ernsthafte Prüfungen finden Sie in der Web-App [Prüfung](https://technet.microsoft.com/edu/windows/take-tests-in-windows-10) im Windows IT Center.

### Benutzereingabe
Benutzereingaben sind ein wichtiger Bestandteil von Apps für Bildungszwecke. Die Steuerelemente auf der Benutzeroberfläche müssen gut reagieren und intuitiv bedienbar sein, damit die Aufmerksamkeit der Benutzer für die Inhalte nicht gestört wird. Eine allgemeine Übersicht der in einer universellen Windows-App verfügbaren Eingabeoptionen finden Sie unter [Einführung in Eingaben](https://msdn.microsoft.com/windows/uwp/input-and-devices/input-primer) und in den nachfolgenden Themen im Abschnitt „Design und UI“. Dazu zeigen die folgenden Beispiel-Apps den grundlegenden Umgang mit der Benutzeroberfläche in der universellen Windows-Plattform.
- Das [einfache Eingabebeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicInput) veranschaulicht die Behandlung von Eingaben in universellen Windows-Apps.
- Das [Beispiel für den Benutzerinteraktionsmodus](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/UserInteractionMode) zeigt, wie Sie den Benutzerinteraktionsmodus erkennen und auf ihn reagieren.
- Das [Beispiel für visuelle Fokuselemente](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlFocusVisuals) zeigt, wie Sie die neuen visuellen Systemfokuselemente nutzen oder eigene visuelle Fokuselemente erstellen, wenn sich die vom System bereitgestellten Elemente nicht für Ihre Anforderungen eignen.

Die Windows Ink-Plattform kann Apps für Bildungszwecke unterstützen, indem diese an ein Eingabeverfahren angepasst werden, mit dem die Lernenden gut vertraut sind. Eine umfassende Anleitung zur Implementierung von Windows Ink in Ihrer App finden Sie unter [Zeichenstiftinteraktionen und Windows Ink](https://msdn.microsoft.com/windows/uwp/input-and-devices/pen-and-stylus-interactions) und den darauf folgenden Themen. Die folgenden Beispiel-Apps illustrieren diese API.
- [Freihandbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Ink) demonstriert die Verwendung der Freihandfunktion (Erfassung, Manipulation und Interpretation von Freihandstrichen) in universellen Windows-Apps mit JavaScript.
- Das [einfache Freihandbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SimpleInk) veranschaulicht die Verwendung der Freihandfunktion (beispielsweise das Erfassen von Freihandeingaben des Benutzers und Durchführen der Schrifterkennung für Freihandstriche) in universellen Windows-Apps mit C#.
- Das [komplexe Freihandbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/ComplexInk) veranschaulicht die Verwendung der erweiterten InkPresenter-Funktion zum Überlappen von Freihandeingaben mit anderen Objekten, Auswählen der Freihandeingabe, Kopieren/Einfügen und Behandeln von Ereignissen. Es basiert auf der universellen Windows-Plattform in C++ und kann auf Windows10-SKUs für Desktops und mobile Geräte ausgeführt werden.


### Windows Store
Apps für Bildungszwecke werden oft unter speziellen Umständen für eine bestimmte Organisation veröffentlicht. Informationen dazu finden Sie unter [Verteilen von branchenspezifischen Apps an Unternehmen](https://msdn.microsoft.com/windows/uwp/publish/distribute-lob-apps-to-enterprises).

## Verwandte Themen
- [Windows 10 for Education](https://technet.microsoft.com/edu/windows/index) im Windows-IT Center



<!--HONumber=Nov16_HO1-->


