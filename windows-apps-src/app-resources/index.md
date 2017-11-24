---
author: stevewhims
Description: In diesem Abschnitt erfahren Sie, wie Sie Zeichenketten-, Bild- und Dateiressourcen Ihrer App erstellen, verpacken und verwenden.
title: App-Ressourcen und das Ressourcenverwaltungssystem
label: Intro
template: detail.hbs
ms.author: stwhi
ms.date: 10/20/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, uwp, Ressourcen, Bild, Element, MRT, Qualifizierer
localizationpriority: medium
ms.openlocfilehash: 38a131704bacbffdf89636aa70b405aa30861d27
ms.sourcegitcommit: d0c93d734639bd31f264424ae5b6fead903a951d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2017
---
# <a name="app-resources-and-the-resource-management-system"></a>App-Ressourcen und das Ressourcenverwaltungssystem
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

In diesem Abschnitt erfahren Sie, wie Sie Zeichenketten-, Bild- und Dateiressourcen Ihrer App erstellen, verpacken und verwenden. Zum Beispiel könnten Sie eine Datei zusammen mit Ihrem Lieblingsspiel verpacken, die eine Definition der Spielebenen enthält, und die Datei zur Laufzeit laden. Außerdem zeigen wir Ihnen, wie Sie Ihre Ressourcen unabhängig von der Logik der App verwalten können. Dadurch wird es einfacher, die App für verschiedene Gebietsschemata, Geräteanzeigen, Eingabehilfeneinstellungen und andere Benutzer- und Maschinenkontexte zu lokalisieren und anzupassen. Ressourcen wie Zeichenketten und Bilder müssen in der Regel in mehreren Sprachen, Skalierungen und Kontrastvarianten vorhanden sein. Bei der Handhabung solcher Ressourcen unterstützt Sie das [Ressourcenverwaltungssystem](resource-management-system.md).

Es gibt zwei Arten von App-Ressourcen:
- Eine Dateiressource ist eine Ressource, die als Datei auf einem Datenträger gespeichert ist. Bei einer Dateiressource kann es sich um ein Bitmap-Bild, XAML, XML, HTML oder beliebige andere Daten handeln.
- Eine eingebettete Ressource ist eine Ressource, die in eine Ressourcendatei eingebettet ist. Das häufigste Beispiel ist eine Zeichenfolgenressource, die in eine Ressourcendatei (.resw oder .resjson) eingebettet ist.

Weitere Informationen zum Wertversprechen durch Lokalisierung Ihrer App finden Sie unter [Globalisierung und Lokalisierung](../globalizing/globalizing-portal.md).

| Artikel | Beschreibung |
|---------|-------------|
| [Ressourcenverwaltungssystem](resource-management-system.md) | Zum Buildzeitpunkt erstellt das Ressourcenverwaltungssystem einen Index aller verschiedenen Varianten der Ressourcen, die mit Ihrer App gepackt sind. Zur Laufzeit erkennt das System die momentan geltenden Benutzer- und Computereinstellungen und lädt die Ressourcen, die für diese Einstellungen am besten geeignet sind. |
| [Wie das Ressourcenverwaltungssystem Ressourcen zuordnet und auswählt](how-rms-matches-and-chooses-resources.md) | Wenn eine Ressource angefordert wird, kann es mehrere Kandidaten geben, für die sich in einem gewissen Maße eine Übereinstimmung mit dem aktuellen Ressourcenkontext ergibt. Vom Ressourcenverwaltungssystem werden alle Kandidaten analysiert, und der beste Kandidat für die Rückgabe wird ermittelt. In diesem Thema wird dieser Prozess ausführlich und anhand von Beispielen beschrieben. |
| [Wie das Ressourcenverwaltungssystem Sprachtags zuordnet](how-rms-matches-lang-tags.md) | Im vorherigen Thema ([Wie das Ressourcenverwaltungssystem Ressourcen zuordnet und auswählt](how-rms-matches-and-chooses-resources.md)) wird die Zuordnung von Qualifizierern im Allgemeinen behandelt. Dieses Thema konzentriert sich ausführlicher auf den Vergleich von Sprachtags. |
| [Anpassen von Ressourcen mit Qualifizierern für Sprache, Skalierung, hohen Kontrast und anderen Qualifizierern](tailor-resources-lang-scale-contrast.md) | In diesem Thema werden das allgemeine Konzept der Ressourcenqualifizierer, ihre Verwendung und der Zweck jedes Qualifizierernamens erläutert. |
| [Lokalisieren von Zeichenfolgen in Benutzeroberfläche und App-Paketmanifest](localize-strings-ui-manifest.md) | Wenn Sie möchten, dass Ihre App verschiedene Anzeigesprachen unterstützt und Ihr Code oder XAML-Markup- oder App-Paketmanifest Zeichenfolgenliterale enthält, verschieben Sie diese Zeichenfolgen in eine Ressourcendatei (.resw). Sie können dann eine übersetzte Kopie dieser Ressourcendatei für jede Sprache erstellen, die Ihre App unterstützt. |
| [Laden von Bilder und Ressourcen mit Anpassung an Skalierung, Design, hohen Kontrast und anders](images-tailored-for-scale-theme-contrast.md) | Ihre App kann Bildressourcendateien laden, die Bilder enthalten, die auf den Skalierungsfaktor des Bildschirms, das Design, einen hohen Kontrast und andere Laufzeitkontexte zugeschnitten sind. |
| [Kachel- und Toast-Mitteilungsunterstützung für Sprache, Skalierung und hohen Kontrast](tile-toast-language-scale-contrast.md) | Ihre Kacheln und Toasts können Zeichenfolgen und Bilder laden, die auf die
Anzeigesprache, den Skalierungsfaktor des Bildschirms, einen hohen Kontrast und andere Laufzeitkontexte zugeschnitten sind. |
| [URI-Schemas](uri-schemes.md) | Sie können mehrere Uniform Resource Identifier (URI)-Schemas verwenden, um auf Dateien im App-Paket, in Datenordnern der App oder in der Cloud zu verweisen. Sie können ebenfalls ein URI-Schema verwenden, um auf Zeichenfolgen zu verweisen, die aus den Ressourcendateien (.resw) der App geladen werden. |
| [Manuelles Kompilieren von Ressourcen mit MakePri.exe](compile-resources-manually-with-makepri.md) | MakePri.exe ist ein Befehlszeilentool, mit dem Sie PRI-Dateien erstellen und dumpen können Es ist über MSBuild in Microsoft Visual Studio integriert, kann aber auch für Entwickler von Nutzen sein, die Pakete manuell oder mithilfe benutzerdefinierter Buildsysteme erstellen. |
| [Befehlszeilenoptionen für MakePRI.exe](makepri-exe-command-options.md) | MakePri.exe akzeptiert die Befehle `createconfig`, `dump`, `new`, `resourcepack`, und `versioned`. In diesem Thema werden die Befehlszeilenoptionen für deren Verwendung erläutert. |
| [Konfigurationsdatei für MakePRI.exe](makepri-exe-configuration.md) | In diesem Thema wird das Schema der XML-Konfigurationsdatei für MakePri.exe beschrieben. |
| [Formatspezifische Indexer für MakePri.exe](makepri-exe-format-specific-indexers.md) | In diesem Thema werden die formatspezifischen Indexer beschrieben, die das Tool MakePri.exe verwendet, um seinen Ressourcenindex zu generieren. |
| [Verwenden des Ressourcenverwaltungssystem für Windows 10 in älteren Apps oder Spielen](using-mrt-for-converted-desktop-apps-and-games.md) | Indem Sie Ihre .NET- oder Win32-App oder Ihr Spiel als AppX-Paket verpacken, können Sie das Ressourcenverwaltungssystem nutzen, um App-Ressourcen zu laden, die auf den Laufzeitkontext zugeschnitten sind. In diesem Thema werden die erforderlichen Techniken detailliert beschrieben. |

Weitere Informationen finden Sie in der ursprünglich für Windows8.x erstellten Dokumentation, die auch für Universelle Windows-Plattform (UWP)-Apps und Windows10 gilt.

-   [App-Ressourcen und Lokalisierung](https://msdn.microsoft.com/library/windows/apps/xaml/hh710212.aspx)
