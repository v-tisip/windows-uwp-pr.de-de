---
author: Xansky
Description: Introduces accessibility concepts that relate to Universal Windows Platform (UWP) apps.
ms.assetid: C89D79C2-B830-493D-B020-F3FF8EB5FFDD
title: Bedienungshilfen
label: Accessibility
template: detail.hbs
ms.author: mhopkins
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 5827bf0c9ddb7f5ebbab3f34e40e08d1620b6e0c
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "5928373"
---
# <a name="accessibility"></a>Eingabehilfen  



Es werden Barrierefreiheitskonzepte für UWP-Apps (Universelle Windows-Plattform) vorgestellt.

Bei der Barrierefreiheit geht es darum, eine Anwendung so zu gestalten, dass sie auch von Menschen verwendet werden kann, bei denen bestimmte Beeinträchtigungen die Nutzung herkömmlicher Benutzeroberflächen verhindern oder erschweren. Für bestimmte Situationen gelten gesetzlich vorgeschriebene Vorgaben im Hinblick auf Barrierefreiheit. Es wird jedoch empfohlen, die Barrierefreiheit unabhängig von gesetzlichen Anforderungen zu berücksichtigen, um sicherzustellen, dass Ihre Apps die größtmögliche Benutzergruppe erreichen. Es ist auch eine Microsoft Store-Deklaration zur Barrierefreiheit der App vorhanden.

> [!NOTE]
> Das Deklarieren der App als barrierefrei ist nur für den Microsoft Store relevant.

| Artikel | Beschreibung |
|---------|-------------|
| [Übersicht über die Barrierefreiheit](accessibility-overview.md) | Dieser Artikel bietet eine Übersicht über die Konzepte und Technologien im Zusammenhang mit Barrierefreiheitsszenarien für UWP-Apps. |
| [Entwerfen von barrierefreier Software](designing-inclusive-software.md) | Erfahren Sie mehr über das Entwerfen inklusiver UWP-Apps für Windows 10.  Entwerfen und erstellen Sie inklusive Software unter Berücksichtigung der Barrierefreiheit. |
| [Entwickeln von inklusiven Windows-Apps](developing-inclusive-windows-apps.md) | Dieser Artikel dient als Orientierungshilfe bei der Entwicklung barrierefreier UWP-Apps. |
| [Barrierefreiheitstests](accessibility-testing.md) | Testverfahren, mit denen Sie sicherstellen können, dass Ihre UWP-App barrierefrei ist. |
| [Barrierefreiheit im Store](accessibility-in-the-store.md) | Hier werden die Anforderungen beschrieben, die Sie erfüllen müssen, wenn Sie Ihre UWP-App im MicrosoftStore als barrierefrei deklarieren möchten. |
| [Prüfliste für die Barrierefreiheit](accessibility-checklist.md) | Enthält eine Prüfliste, mit der Sie sicherstellen können, dass Ihre UWP-App barrierefrei ist. |
| [Verfügbarmachen von grundlegenden Informationen zur Barrierefreiheit](basic-accessibility-information.md) | Grundlegende Informationen zur Barrierefreiheit werden häufig in die Kategorien Name, Rolle und Wert unterteilt. In diesem Thema wird der Code beschrieben, mit dem Ihre App die grundlegenden Informationen verfügbar machen kann, die für Hilfstechnologien erforderlich sind. |
| [Barrierefreiheit der Tastaturnavigation](keyboard-accessibility.md) | Wenn Ihre App keine barrierefreie Bedienung mit der Tastatur ermöglicht, können Benutzer, die blind oder in ihrer Beweglichkeit eingeschränkt sind, Schwierigkeiten bei der Verwendung Ihrer App haben oder Ihre App möglicherweise überhaupt nicht nutzen. |
| [Orientierungspunkte und Überschriften](landmarks-and-headings.md) | „Unterstützte Orientierungspunkte und Überschriften” definieren Bereiche einer Benutzeroberfläche, die Benutzer bei der effizienten Navigation von Hilfstechnologien wie Bildschirmleseprogrammen unterstützen. |
| [Designs mit hohem Kontrast](high-contrast-themes.md) | Beschreibt die Schritte, mit denen Sie die Bedienbarkeit Ihrer UWP-App sicherstellen können, wenn ein Design mit hohem Kontrast aktiviert ist. |
| [Anforderungen für barrierefreien Text](accessible-text-requirements.md) | In diesem Thema werden die bewährten Methoden für barrierefreien Text in Apps beschrieben. Damit stellen Sie sicher, dass der Kontrast zwischen Farben und Hintergründen ausreichend hoch ist. Außerdem werden in diesem Thema die Rollen der Microsoft-Benutzeroberflächenautomatisierung, die für Textelemente in einer UWP-App verwendet werden können, sowie bewährte Methoden für Text in Grafiken erläutert. |
| [Nicht empfehlenswerte Praktiken für die Barrierefreiheit](practices-to-avoid.md) | Es werden die Praktiken aufgeführt, die Sie vermeiden sollten, wenn Sie eine barrierefreie UWP-App erstellen möchten. |
| [Benutzerdefinierte Automatisierungspeers](custom-automation-peers.md) | Beschreibt das Konzept von Automatisierungspeers für die Benutzeroberflächenautomatisierung und erläutert, wie Sie Unterstützung zur Benutzeroberflächenautomatisierung für eigene benutzerdefinierte UI-Klassen bereitstellen können. |
| [Steuerelementmuster und Schnittstellen](control-patterns-and-interfaces.md) | Enthält eine Liste der Steuerelementmuster für die Microsoft-Benutzeroberflächenautomatisierung samt der Klassen, die Clients für den Zugriff verwenden, und der Schnittstellen, die Anbieter zur Implementierung verwenden. |

## <a name="related-topics"></a>Verwandte Themen  
* [**Windows.UI.Xaml.Automation**](https://msdn.microsoft.com/library/windows/apps/BR209179) 
* [Erste Schritte mit der Sprachausgabe](https://support.microsoft.com/en-us/help/22798/windows-10-narrator-get-started)