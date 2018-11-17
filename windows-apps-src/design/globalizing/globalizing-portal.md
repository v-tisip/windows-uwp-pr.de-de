---
author: stevewhims
Description: Learn about the benefits of globalizing and localizing your app, and exactly what these terms mean.
Search.SourceType: Video
title: Globalisierung und Lokalisierung
ms.assetid: c0791eec-5bb8-4a13-8977-61d7d98e35ce
label: Intro
template: detail.hbs
ms.author: stwhi
ms.date: 10/18/2017
ms.topic: article
keywords: Windows 10, UWP, Globalisierung, Lokalisierbarkeit, Lokalisierung
ms.localizationpriority: medium
ms.openlocfilehash: b437055704c307dc3e3fa506a9885ff892585503
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "7147823"
---
# <a name="globalization-and-localization"></a>Globalisierung und Lokalisierung

Windows wird auf der ganzen Welt in verschiedenen Märkten und von Anwendern unterschiedlicher Kulturen, Herkunft und Sprachen verwendet. Ihre Benutzer sprechen eine Vielzahl verschiedener Sprachen in vielen verschiedenen Ländern und Regionen. Einige Benutzer sprechen mehr als eine Sprache. Ihre App wird also auf Konfigurationen ausgeführt, die viele Systemeinstellungen für Sprache, Region und Kultur beinhalten. Sie können die Marktchancen Ihrer App erweitern, indem Sie mithilfe von *Globalisierung* und *Lokalisierung* eine variable App entwickeln.

Das folgende Video enthält eine kurze Einführung dazu, wie Sie Ihre App für die weltweite Verbreitung vorbereiten: [Einführung in die Globalisierung und Lokalisierung](https://channel9.msdn.com/Blogs/One-Dev-Minute/Introduction-to-globalization-and-localization).

**Globalisierung** ist der Vorgang, bei dem Sie Ihre App so entwerfen und entwickeln, dass sie auf verschiedenen globalen Märkten (auf Systemen mit unterschiedlichen Sprach- und Kulturkonfigurationen) angemessen funktioniert, ohne dass kulturspezifische Änderungen oder Anpassungen erforderlich sind.

- Berücksichtigen Sie beim Bearbeiten von Zeichenfolgen die Kultur. Ändern Sie beispielsweise den Fall von Zeichenfolgen nicht, ohne sie zu vergleichen.
- Verwenden Sie Kalender, die für die aktuelle Kultur geeignet sind.
- Verwenden Sie die Globalisierungs-APIs zum Anzeigen von Daten, die für das Land oder die Region entsprechend formatiert sind, z. B. Zahlen, Datumsangaben, Uhrzeiten und Währungen.
- Berücksichtigen Sie, dass in verschiedenen Kulturen unterschiedliche Regeln für die Sortierung von Text und anderen Daten gelten.

Ihr Code muss in allen Kulturen, für die Sie Ihre App vorgesehen haben, gleich gut funktionieren. Im Idealfall funktioniert Ihr Code im Kontext *jeder* Sprache, Region oder Kultur gleich gut. Der effizienteste Weg, um die Funktionen Ihrer App zu globalisieren, ist die Verwendung des Konzepts der Kulturen/Gebietsschemas. Eine Gebietsschema ist ein Satz von Regeln und ein Satz von Daten, die für eine bestimmte Sprache und Region spezifisch sind. Diese Regeln und Daten enthalten Informationen über Folgendes:

- Zeichenklassifizierung
- Schreibsystem
- Datums- und Zeitformatierung
- Konventionen über Zahlen, Währung, Gewicht und Maße
- Sortierregeln

**Lokalisierbarkeit** ist das Ergebnis des Prozess der Vorbereitung der Lokalisierung einer globalisierten App und/oder der Überprüfung, ob die App für die Lokalisierung bereit ist. Die korrekte Herstellung der Lokalisierbarkeit einer App bedeutet, dass der spätere Lokalisierungsprozess keine funktionalen Mängel in der App aufdeckt. Die wichtigste Eigenschaft einer lokalisierbaren App ist, dass ihr ausführbarer Code sauber von den lokalisierbaren Ressourcen der App getrennt ist.

- Die Längen von Zeichenfolgen, die in andere Sprachen übersetzt sind, können stark variieren. Entwerfen Sie Ihre Benutzeroberfläche so, dass verschiedenen Textlängen und Schriftgrößen für Beschriftungen und Texteingabesteuerelemente möglich sind.
- Versuchen Sie, Text und kulturell sensibles Material in Bildern zu vermeiden.
- Verwenden Sie weder hartcodierte Zeichenfolgen noch kulturabhängige Bilder in Code und Markup Ihrer App. Speichern Sie diese stattdessen als Zeichenfolgen- und Bildressourcen, damit sie unabhängig von den von Ihrer App erstellten Binärdateien an verschiedene lokale Märkte angepasst werden können.
- Nehmen Sie ein Pseudolokalisierung Ihrer App vor, um alle Lokalisierungsprobleme zu erkennen.

**Lokalisierung** ist der Prozess der Anpassung oder Übersetzung der lokalisierbaren Ressourcen Ihrer App, um die sprachlichen, kulturellen und politischen Anforderungen der spezifischen lokalen Märkte für die App zu erfüllen. Wenn Ihre App lokalisierbar ist und Sie die Stufe der Lokalisierung erreicht haben, müssen Sie während dieses Vorgangs keine Logik ändern.

- Übersetzen Sie die Zeichenfolgenressourcen und andere Ressourcen der App für den neuen Markt.
- Ändern Sie kulturspezifische Bilder nach Bedarf.
- Dateien können auch unabhängig von der Sprache je nach Region des Benutzers variieren. Eine Datei kann beispielsweise abhängig vom Benutzerstandort unterschiedliche Rahmen haben. Die Bezeichnungen sollten aber in der bevorzugten Sprache des Benutzers angezeigt werden.

Die meisten Lokalisierungsteams verwenden spezielle Tools, um den Prozess zu unterstützen. Beispielsweise durch das Kopieren der Übersetzungen von wiederkehrendem Text.

| Artikel | Beschreibung |
|---------|-------------|
| [Richtlinien für Globalisierung](guidelines-and-checklist-for-globalizing-your-app.md) | Entwerfen und entwickeln Sie Ihre App so, dass sie auf Systemen mit unterschiedlichen Sprach- und Kulturkonfigurationen ordnungsgemäß funktioniert. |
| [Benutzerprofilsprachen und App-Manifest-Sprachen verstehen](manage-language-and-region.md) | In diesem Thema werden die Begriffe „Benutzerprofil-Sprachenliste”, „App-Manifest-Sprachenliste” und „App-Laufzeit-Sprachenliste” definiert. Wir verwenden diese Begriffe in diesem Thema und in anderen Themen in diesem Featurebereich. Daher ist es wichtig zu wissen, was sie bedeuten. |
| [Globalisieren von Datum, Uhrzeit und Zahlenformaten](use-global-ready-formats.md) | Gestalten Sie Ihre App so, dass sie global einsetzbar ist, indem Sie Datum, Uhrzeit, Telefonnummern und Währungen entsprechend formatieren. Dadurch können Sie Ihre App später zur weltweiten Vermarktung für weitere Kulturkreise, Regionen und Sprachen anpassen. |
| [Muster zum Formatieren von Datum und Uhrzeit verwenden](use-patterns-to-format-dates-and-times.md) | Verwenden Sie Klassen im Namespace [**Windows.Globalization.DateTimeFormatting**](/uwp/api/windows.globalization.datetimeformatting?branch=live)mit benutzerdefinierten Vorlagen und Mustern, um Daten und Zeiten im gewünschten Format anzuzeigen. |
| [Layout und Schriften anpassen und RTL unterstützen](adjust-layout-and-fonts--and-support-rtl.md) | Entwerfen Sie Ihre App so, dass die Layouts und Schriften mehrerer Sprachen unterstützen – beispielsweise auch den Textfluss von rechts nach links (right-to-left, RTL). |
| [NumeralSystem-Werte](glob-numeralsystem-values.md) | In diesem Thema werden die für die **NumeralSystem**-Eigenschaft von verschiedenen Klassen im [**Windows.Globalization**](/uwp/api/windows.globalization?branch=live)-Namespace verfügbaren Werte aufgeführt. |
| [App lokalisierbar machen](prepare-your-app-for-localization.md) | Eine lokalisierte App kann in anderen Märkten, Sprachen oder Regionen lokalisiert werden, ohne dass funktionale Mängel in der App auftreten. Die wichtigste Eigenschaft einer lokalisierbaren App ist, dass ihr ausführbarer Code sauber von den lokalisierbaren Ressourcen der App getrennt ist. |
| [Internationale Schriften](loc-international-fonts.md) | Dieses Thema enthält eine Liste der für UWP-Apps verfügbaren Schriften, die in andere Sprachen als Englisch (USA) lokalisiert sind. |
| [App für bidirektionalen Text entwerfen](design-for-bidi-text.md) | Entwerfen Sie Ihre App so, dass bidirektionale Textunterstützung (BiDi) bereitgestellt wird, sodass Sie Texte aus links und rechtsbündigen Schreibsystemen kombinieren können. |
| [Verwenden des Multilingual App Toolkit 4.0](use-mat.md) | Das Multilingual App Toolkit (MAT) 4.0 integriert sich in Microsoft Visual Studio 2017, um Übersetzungsunterstützung, Übersetzungsdateiverwaltung und Editortools für UWP-Apps bereitzustellen. |
| [Multilingual App Toolkit 4.0 – Fragen und Antworten sowie Problembehandlung](mat-faq-troubleshooting.md) | Dieses Thema enthält Antworten auf häufig gestellte Fragen und Probleme in Bezug auf das Multilingual App Toolkit (MAT) 4.0. |
