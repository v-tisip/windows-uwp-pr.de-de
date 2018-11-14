---
author: KarlErickson
ms.assetid: F46306EC-DFF3-4FF0-91A8-826C1F8C4A52
title: Datenbindungen und MVVM
description: Die Datenbindung ist das Herzstück des architektonischen Entwurfsmusters Model-View-ViewModel (MVVM)-UI, und ermöglicht die Kopplung zwischen UI und nicht-UI-Code.
ms.author: karler
ms.date: 10/02/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 8a70603c26c7123af50fc920d327ccef332b7ed6
ms.sourcegitcommit: f2c9a050a9137a473f28b613968d5782866142c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6282902"
---
# <a name="data-binding-and-mvvm"></a>Datenbindungen und MVVM

Model-View-ViewModel (MVVM) ist ein UI-Architektur-Muster für die Benutzeroberfläche und nicht-UI-Code entkoppeln. MVVM deklarativ definieren die Benutzeroberfläche in XAML und Verwenden von Daten bindungsmarkup so verknüpfen Sie es mit anderen Ebenen, Daten und Befehle enthält. Die Datenbindung Infrastruktur bietet eine lose Kopplung, die die Benutzeroberfläche hält und die verknüpften Daten synchronisiert und leitet Benutzereingaben an die entsprechenden Befehle weiter. 

Da es Kopplung bereitstellt, wird die Verwendung der Datenbindung schwer Abhängigkeiten zwischen verschiedenen Arten von Code verringert. Dies erleichtert die einzelnen Code-Einheiten (Methoden, Klassen, Steuerelemente usw.) ändern, ohne unerwünschte Nebenwirkungen in anderen Einheiten. Dieser Entkopplung ist ein Beispiel für die *Trennung von Bereichen*, was ein wichtiges Konzept in vielen Entwurfsmuster. 

## <a name="benefits-of-mvvm"></a>Vorteile von MVVM

Entkoppeln Ihren Code hat viele Vorteile, darunter:

* Aktivieren eine iterative, explorativen Codierungsstil. Änderung, die isoliert ist weniger fehleranfällig und leichter zu experimentieren.
* Vereinfachung Komponententests. Code-Einheiten, die voneinander isoliert sind können einzeln und außerhalb produktionsumgebungen getestet werden.
* Unterstützung der Teamzusammenarbeit. Getrennt Code, die gut durchdachte Schnittstellen entspricht, kann durch separate Personen oder Teams entwickelt und später integriert werden.
* Verbesserung der Wartungsfreundlichkeit. Beheben von Fehlern im Code getrennt wahrscheinlich weniger Funktionalität in anderen Code verursachen.

Im Gegensatz zu MVVM eine app mit mehr herkömmlichen "CodeBehind" Struktur in der Regel für die Anzeige nur Daten binden von Daten verwendet, und reagiert auf Benutzereingaben durch direkt behandeln von Ereignissen, die von Steuerelementen verfügbar gemacht werden. Die Ereignishandler im Code-Behind-Dateien (z. B. "MainPage.Xaml.cs") implementiert sind, und werden häufig eng an die Steuerelemente, die in der Regel mit Code, der die Benutzeroberfläche direkt bearbeitet. Dadurch wird es schwierig oder sogar unmöglich, um ein Steuerelement zu ersetzen, ohne den Ereignisbehandlungscode zu aktualisieren. Mit dieser Architektur wiederholenden CodeBehind-Dateien häufig Code, der sich direkt auf die Benutzeroberfläche, z. B. Datenbankzugriffs Code mit ist nicht der Clientmethode dupliziert und für die Verwendung mit anderen Seiten geändert wird.

## <a name="app-layers"></a>App-Schichten

Bei Verwendung des MVVM-Musters ist eine app in den folgenden Ebenen unterteilt:

* Die **Modell** -Ebene definiert die Typen, die Ihre Geschäftsdaten darstellen. Dies enthält alles, was erforderlich, um die Core app Domäne Modell und umfasst häufig zentralen app-Logik. Diese Ebene ist vollständig unabhängig von der Ansicht und der Ansichtsmodell Ebene und befindet sich häufig teilweise in der Cloud. Eine vollständig implementierten Modellebene können Sie mehrere verschiedene Client apps erstellen, wenn Sie also, z. B. UWP und Web-apps auswählen, die mit den gleichen Daten funktionieren.
* Die **Ansicht** -Ebene definiert die Benutzeroberfläche mit XAML-Markup. Das Markup enthält Datenbindungsausdrücke (z. B. [X: Bind](https://docs.microsoft.com/windows/uwp/xaml-platform/x-bind-markup-extension)), die die Verbindung zwischen bestimmten UI-Komponenten und verschiedenen Ansichtsmodell und die Modellnummer Member zu definieren. Code-Behind-Dateien werden manchmal als Teil der Ansicht Ebene verwendet, enthalten Sie zusätzlichen Code erforderlich, anpassen oder die Benutzeroberfläche bearbeiten oder Extrahieren von Daten aus den Ereignisargumenten Handler vor dem Aufrufen einer Ansicht und Modell-Methode, die die Arbeit ausführt. 
* Die **Ansichtsmodell** -Ebene bereitstellt Bindungsziele Daten für die Ansicht. In vielen Fällen das Ansichtsmodell verfügbar macht das Modell direkt oder enthält Member für die spezifische Modell Mitglieder umschließen. Das Ansichtsmodell kann Mitglieder Verfolgen von Daten, die relevant ist auch definieren der Benutzeroberfläche, nicht aber das Modell, z. B. die Anzeigereihenfolge der eine Liste von Elementen. Das Ansichtsmodell dient auch als Point Integration mit anderen Diensten wie z. B. Datenbankzugriffs Code. Bei einfachen Projekten benötigen Sie möglicherweise keine separate Modellebene, aber nur ein Ansichtsmodell, das alle Daten kapselt, die Sie benötigen. 

## <a name="basic-and-advanced-mvvm"></a>Grundlegenden und erweiterten MVVM

Wie bei allen Entwurfsmuster, es ist mehr als eine Möglichkeit zum Implementieren von MVVM und viele verschiedene Techniken, die als Teil des MVVM. Aus diesem Grund stehen mehrere verschiedene Drittanbieter-MVVM-Frameworks unterstützen die verschiedenen XAML-basierte Plattformen, einschließlich UWP. Diese Frameworks umfassen jedoch in der Regel mehrere Dienste für die Implementierung von getrennt Architektur, die genaue Definition des MVVM nicht eindeutig machen. 

Zwar komplexen MVVM-Frameworks sehr nützlich sein können, insbesondere bei einer Skalierung von Enterprise-Projekten ist in der Regel zugeordnet, übernehmen alle bestimmtes Muster oder Technik Kosten und Vorteile sind nicht immer klar, je nach der Skalierung und die Größe des Ihr Projekt. Glücklicherweise können Sie übernehmen nur diese Techniken, die einen klar und konkreten Vorteil bereitstellen und andere ignorieren, bis Sie sie benötigen. 

Insbesondere erhalten Sie einen Großteil der Vorteil, indem Sie einfach Verständnis und die leistungsstarken Daten binden und die Aufteilung Ihrer app-Logik in der weiter oben beschriebenen Ebenen anwenden. Dies kann mit nur die Funktionen von Windows SDK, und ohne jede externe Frameworks erzielt werden. Insbesondere die [Markuperweiterung {X: Bind}](https://docs.microsoft.com/windows/uwp/xaml-platform/x-bind-markup-extension) erleichtert die Datenbindung und leistungsfähigere als in vorherigen XAML-Plattformen, einen Großteil der Standardcode überflüssig früheren Versionen erforderlich.

Weitere Informationen zur Verwendung von einfachen, Out-of-the-Box MVVM sehen Sie sich das [Kundenauftragsdatenbank-Beispiel](https://github.com/Microsoft/Windows-appsample-customers-orders-database) auf GitHub. Viele der anderen [UWP: Beispiele](https://github.com/Microsoft?q=windows-appsample
) verwenden auch eine grundlegende MVVM-Architektur und [Datenverkehr App-Beispiel](https://github.com/Microsoft/Windows-appsample-trafficapp) enthält sowohl Code-Behind-MVVM-Versionen mit Notizen, beschreibt die [Konvertierung von MVVM](https://github.com/Microsoft/Windows-appsample-trafficapp/blob/MVVM/MVVM.md). 

## <a name="see-also"></a>Weitere Informationen:

### <a name="topics"></a>Themen

[Datenbindung im Detail](https://docs.microsoft.com/windows/uwp/data-binding/data-binding-in-depth)  
[{x:Bind}-Markuperweiterung](https://docs.microsoft.com/windows/uwp/xaml-platform/x-bind-markup-extension)  

### <a name="samples"></a>Beispiele

[Beispiel für Kunden-Datenbank für Kundenaufträge](https://github.com/Microsoft/Windows-appsample-customers-orders-database)  
[VanArsdel Inventar-Beispiel](https://github.com/Microsoft/InventorySample)  
[Datenverkehr-App-Beispiel](https://github.com/Microsoft/Windows-appsample-trafficapp)  
