---
author: stevewhims
Description: "MakePri.exe ist ein Befehlszeilentool, mit dem Sie PRI-Dateien erstellen und dumpen können Es ist über MSBuild in Microsoft Visual Studio integriert, kann aber auch für Entwickler von Nutzen sein, die Pakete manuell oder mithilfe benutzerdefinierter Buildsysteme erstellen."
title: Manuelles Kompilieren von Ressourcen mit MakePri.exe
template: detail.hbs
ms.author: stwhi
ms.date: 10/23/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, uwp, Ressourcen, Bild, Element, MRT, Qualifizierer
localizationpriority: medium
ms.openlocfilehash: 16d2a270a69497bc66f7b17109bc28b062f14b5e
ms.sourcegitcommit: d0c93d734639bd31f264424ae5b6fead903a951d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2017
---
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

# <a name="compile-resources-manually-with-makepriexe"></a>Manuelles Kompilieren von Ressourcen mit MakePri.exe

MakePri.exe ist ein Befehlszeilentool, mit dem Sie PRI-Dateien erstellen und dumpen können Es ist über MSBuild in Microsoft Visual Studio integriert, kann aber auch für Entwickler von Nutzen sein, die Pakete manuell oder mithilfe benutzerdefinierter Buildsysteme erstellen.

## <a name="makepriexe-command-line-options"></a>Befehlszeilenoptionen für MakePRI.exe

MakePri.exe akzeptiert die Befehle `createconfig`, `dump`, `new`, `resourcepack`, und `versioned`. Details zur Verwendung dieser Befehle finden Sie unter [Befehlszeilenoptionen für MakePRI.exe](makepri-exe-command-options.md).

## <a name="makepriexe-configuration"></a>Konfigurieren von MakePRI.exe

Die PRI-XML-Konfigurationsdatei legt fest, welche Ressourcen indiziert werden und auf welche Weise die Indexerstellung erfolgt. Das Schema der Konfigurations-XML wird unter [Konfigurieren von MakePRI.exe](makepri-exe-configuration.md) beschrieben.

## <a name="format-specific-indexers"></a>Formatspezifische Indexer

MakePri.exe wird in der Regel mit den Optionen `new`, `versioned`, und `resourcepack` verwendet. In diesem Fall werden zwecks Generierung eines Ressourcenindexes Quelldateien indiziert. MakePri.exe verwendet eine Reihe individueller Indexer, um die verschiedenen Quellressourcendateien oder Ressourcencontainer zu lesen. Der einfachste Indexer ist der Ordnerindexer. Er indiziert den Inhalt eines Ordners, beispielsweise Ressourcen wie `.jpg`- oder `.png`-Bilder. Weitere Informationen finden Sie unter [Formatspezifische Indexer für MakePri.exe](makepri-exe-format-specific-indexers.md).

## <a name="makepriexe-warnings-and-error-messages"></a>Warnungen und Fehlermeldungen von MakePri.exe

```
Resources found for language(s) '<language(s)>' but no resources found for default language(s): '<language(s)>'. Change the default language or qualify resources with the default language.
```

Die obige Warnung wird angezeigt, wenn MakePri.exe oder MSBuild Dateien oder Zeichenfolgenressourcen für eine bestimmte benannte Ressource erkennt, die scheinbar mit Sprachqualifizierern gekennzeichnet sind, für eine Standardsprache jedoch kein Kandidat gefunden wird. Die Verwendung von Qualifizierern in Datei- und Ordnernamen wird beschrieben in [Anpassen von Ressourcen mit Qualifizierern für Sprache, Skalierung und anderen](tailor-resources-lang-scale-contrast.md). Dateien und Ordner können Namen von Sprachen enthalten, obwohl keine Ressourcen erkannt werden, die genau für die Standardsprache qualifiziert sind. Die Warnung wird beispielsweise angezeigt, wenn für ein Projekt „en-US” als Standardsprache verwendet wird und eine Datei mit dem Namen „de/logo.png” vorhanden ist, aber keine Dateien vorliegen, die mit der Standardsprache „en-US” markiert sind. Um die Warnung zu entfernen, müssen entweder eine oder mehrere Dateien oder eine oder mehrere Zeichenfolgenressourcen mit der Standardsprache qualifiziert werden, oder die Standardsprache muss geändert werden. Zum Ändern der Standardsprache öffnen Sie Ihre Projektmappe in Visual Studio und dann `Package.appxmanifest`. Vergewissern Sie sich auf der Registerkarte „Anwendung”, dass die Standardsprache passend festgelegt ist (z.B. auf „En” oder „en-US”).

```
No default or neutral resource given for '<resource identifier>'. The application may throw an exception for certain user configurations when retrieving the resources.
```

Die obige Warnung wird angezeigt, wenn MakePri.exe oder MSBuild Dateien oder Ressourcen erkennt, die offenbar mit Sprachkennzeichnern markiert sind, deren Ressourcenzuordnungen unklar sind. Das heißt, dass Qualifizierer vorhanden sind, es aber nicht sicher ist, dass zur Laufzeit eine bestimmte infrage kommende Ressource für den betreffenden Ressourcenbezeichner zurückgegeben werden kann. Die Warnung wird angezeigt, wenn keine infrage kommende Ressource für die betreffende Sprache oder Wohnorteinstellung oder einen anderen Qualifizierer gefunden wird, bei dem es sich um einen Standard handelt oder der in jedem Fall mit dem Benutzerkontext übereinstimmt. Zur Laufzeit wird für bestimmte Benutzerkonfigurationen, z.B. die Sprachpräferenzen oder den Wohnort eines Benutzers (**Einstellungen** > **Zeit und Sprache** > **Region und Sprache**), von den zum Abrufen der Ressourcen verwendeten APIs möglicherweise eine unerwartete Ausnahme ausgelöst. Um die Warnung zu entfernen, müssen Standardressourcen bereitgestellt werden, beispielsweise eine Ressource mit der Standardsprache des Projekts oder dem globalen Wohnort (homeregion-001).

## <a name="using-makepriexe-in-a-build-system"></a>Verwenden von MakePri.exe in einem Buildsystem

Buildsysteme müssen je nach Art des zu erstellenden Projekts den MakePri.exe-Befehl `new`, `versioned` oder `resourcepack` verwenden. Buildsysteme, die eine neue PRI-Datei erstellen, müssen den Befehl `new` verwenden. Buildsysteme, welche die Kompatibilität interner Offsets durch Iterationen gewährleisten müssen, können den Befehl `versioned` verwenden. Buildsysteme, die eine PRI-Datei erstellen müssen, die zusätzliche Ressourcenvarianten mit einer Prüfung zur Sicherstellung enthält, dass der Variante keinen neuen Ressourcen hinzugefügt werden, müssen den Befehl `resourcepack` verwenden.

Für Buildsysteme, die eine explizite Kontrolle der indizierten Quelldateien erfordern, kann der ResFiles-Indexer zur Ordnerindexerstellung verwendet werden. Buildsysteme können außerdem mehrere Indexdurchläufe mit verschiedenen [formatspezifischen Indexern](makepri-exe-format-specific-indexers.md) verwenden, um eine einzelne PRI-Datei zu erstellen.

Buildsysteme können außerdem den formatspezifischen PRI-Indexer verwenden, um dem PRI für das Paket vorbereitete PRI-Dateien aus anderen Komponenten wie Klassenbibliotheken, Assemblys, SDKs und DLLs hinzuzufügen.

Beim Erstellen von PRI-Dateien für andere Komponenten, Klassenbibliotheken, Assemblys, DLLs und SDKs muss die **initialPath** -Konfiguration verwendet werden, damit für die Komponentenressourcen eigene untergeordnete Ressourcenzuordnungen vorhanden sind, die nicht mit der sie enthaltenden App in Konflikt geraten.

## <a name="related-topics"></a>Verwandte Themen

* [Befehlszeilenoptionen für MakePRI.exe](makepri-exe-command-options.md)
* [Konfigurieren von MakePRI.exe](makepri-exe-configuration.md)
* [Formatspezifische Indexer für MakePri.exe](makepri-exe-format-specific-indexers.md)
* [Anpassen von Ressourcen mit Qualifizierern für Sprache, Skalierung und andere Eigenschaften](tailor-resources-lang-scale-contrast.md)
