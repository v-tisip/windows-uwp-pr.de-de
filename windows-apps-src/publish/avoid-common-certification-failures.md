---
author: jnHs
Description: Review this list to help avoid issues that frequently prevent apps from getting certified, or that might be identified during a spot check after the app is published.
title: Vermeiden allgemeiner Zertifizierungsfehler
ms.assetid: 9E9E3841-2F9B-42D4-B5F8-4C7C31E42E3D
ms.author: wdg-dev-content
ms.date: 10/31/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 7f37412ac88b001f412a1495f2b4efa029cf4d3a
ms.sourcegitcommit: f2c9a050a9137a473f28b613968d5782866142c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6252345"
---
# <a name="avoid-common-certification-failures"></a>Vermeiden allgemeiner Zertifizierungsfehler


Lesen Sie diese Liste, und vermeiden Sie dadurch Probleme, die häufig die Zertifizierung von Apps verhindern oder nach der Veröffentlichung der App bei einer Stichprobenkontrolle auftreten können.

> [!NOTE]
> Achten Sie darauf, überprüfen Sie die [Microsoft Store-Richtlinien](https://docs.microsoft.com/legal/windows/agreements/store-policies) , um sicherzustellen, dass Ihre app alle darin aufgeführten Anforderungen erfüllt.

-   Reichen Sie die App erst ein, wenn sie fertig ist. Sie können die Beschreibung Ihrer App gern nutzen, um auf geplante Features hinzuweisen. Achten Sie jedoch darauf, dass Ihre App keine unvollständigen Abschnitte, Links zu unfertigen Webseiten oder andere Elemente enthält, die Kunden darauf schließen lassen, dass sich die App in einem unvollständigen Zustand befindet.

-   [Testen Sie die App vor dem Einreichen mit dem Zertifizierungskit für Windows-Apps](../debug-test-perf/windows-app-certification-kit.md).

-   Testen Sie die App unter verschiedenen Konfigurationen, um größtmögliche Stabilität sicherzustellen.

-   Vergewissern Sie sich, dass die App nicht abstürzt, wenn keine Netzwerkkonnektivität besteht! Auch wenn für die eigentliche Verwendung der App eine Verbindung erforderlich ist, muss sie richtig ausgeführt werden, wenn keine Verbindung besteht.

-   [Stellen Sie die erforderlichen Infos](notes-for-certification.md) zum Verwenden der App bereit, z.B. Benutzername und Kennwort für ein Testkonto, wenn sich Benutzer bei einem Dienst anmelden müssen, oder geben Sie die erforderlichen Schritte zum Zugreifen auf versteckte oder gesperrte Features an.

-   Fügen Sie eine [URL zur Datenschutzrichtlinie](enter-app-properties.md#privacy-policy-url) , wenn Ihre app eine benötigt; z. B. wenn die app greift auf jeder Art von persönlichen Informationen auf irgendeine Weise oder dies anderweitig gesetzlich vorgeschrieben. Um zu ermitteln, ob Ihre app eine Datenschutzrichtlinie benötigt, überprüfen Sie die [Vereinbarung für App-Entwickler](https://docs.microsoft.com/legal/windows/agreements/app-developer-agreement) und die [Microsoft Store-Richtlinien](https://docs.microsoft.com/legal/windows/agreements/store-policies).

-   Formulieren Sie die Beschreibung der App so, dass sie den Funktionsumfang der App genau darstellt. Unterstützung erhalten Sie in den Richtlinien zum [Verfassen einer ansprechenden App-Beschreibung](write-a-great-app-description.md).

-   Beantworten Sie alle Fragen im Bereich [Altersfreigaben](age-ratings.md) vollständig und richtig.

-   [Deklarieren Sie die App nur dann als barrierefrei](app-declarations.md#this-app-has-been-tested-to-meet-accessibility-guidelines), wenn Sie sie ausdrücklich für Barrierefreiheitsszenarien entwickelt und getestet haben.

-   Wenn die App die E-Commerce-APIs für den Windows Store aus dem [**Windows.ApplicationModel.Store**](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Store)-Namespace verwendet, müssen Sie die App testen und sich vergewissern, dass sie typische Ausnahmen behandelt. Stellen Sie außerdem sicher, dass die App die [**CurrentApp**](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Store.CurrentApp)-Klasse verwendet und nicht die [**CurrentAppSimulator**](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Store.CurrentAppSimulator)-Klasse, die nur zu Testzwecken gedacht ist. (Wenn Ihre App auf Windows10, Version1607 oder höher ausgerichtet ist, wird empfohlen, Mitglieder des [Windows.Services.Store](https://docs.microsoft.com/uwp/api/windows.services.store)-Namespace statt des Windows.ApplicationModel.Store-Namespace zu verwenden).


 

 




