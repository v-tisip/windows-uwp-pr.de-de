---
author: QuinnRadich
title: Was ist neu in Windows-Dokumentation im August 2018 – Entwicklung von UWP-apps
description: Neue Features, Videos, Beispiele und entwicklerleitfäden wurden in der Windows 10-Entwicklerdokumentation für August 2018 hinzugefügt.
keywords: Neues in, Update, Features, Anleitungen für Entwickler, Windows 10, august
ms.author: quradic
ms.date: 08/14/2018
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 76de6c5c1e8925dd8b166a8d99c39116bf66141d
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5870726"
---
# <a name="whats-new-in-the-windows-developer-docs-in-august-2018"></a>Was ist neu in der Windows-Entwicklerdokumentation im August 2018

Die Entwicklerdokumentation für die Windows-Plattform wird ständig mit Informationen über neue Features für Entwickler aktualisiert. Die folgenden Featureübersichten, entwicklerleitfäden und Videos wurden im Monat August zur Verfügung gestellt.

Nach der [Installation der Tools und des SDKs](http://go.microsoft.com/fwlink/?LinkId=821431) unter Windows10 können Sie entweder [eine neue universelle Windows-App erstellen](../get-started/create-uwp-apps.md) oder sich mit der Verwendung von [vorhandenem App-Code unter Windows](../porting/index.md) vertraut machen.

## <a name="features"></a>Features

### <a name="design"></a>Entwerfen

Die folgenden Features wurden die Windows Insider Preview-Builds, über das [Windows-Insider-](https://insider.windows.com/) Programm verfügbar hinzugefügt.

* Der [Windows-UI-Bibliothek](https://aka.ms/winui-docs) ist ein Satz von NuGet-Pakete, die Steuerelemente und andere Elemente einer interfact für UWP-apps bereitstellen. Diese Pakete sind auch kompatibel mit früheren Versionen von Windows 10, damit Ihre app funktioniert, auch wenn Ihre Benutzer die neueste Version des Betriebssystems besitzen.

* [DropDownButton](../design/controls-and-patterns/buttons.md#create-a-drop-down-button), [SplitButton](../design/controls-and-patterns/buttons.md#create-a-split-button)und [ToggleSplitButton](../design/controls-and-patterns/buttons.md#create-a-toggle-split-button) bieten Schaltflächensteuerelementen mit speziellen Features zur Verbesserung der Benutzeroberfläche Ihrer app.

![Eine geteilte Schaltfläche zum Auswählen von Vordergrundfarbe](../design/controls-and-patterns/images/split-button-rtb.png)

* NavigationView unterstützt jetzt in der [oberen Navigationsleiste](../design/controls-and-patterns/navigationview.md)für Fälle, in dem Ihre app verfügt über eine kleinere Anzahl Navigationsoptionen und mehr Platz für den Inhalt Ihrer app erforderlich.

* TreeView wurde zur Unterstützung von erweitert [Daten binden, Elementvorlagen, und Drag & drop.](../design/controls-and-patterns/tree-view.md)

### <a name="package-support-framework"></a>Paket-Unterstützung Framework

Das Paket Support-Framework ist ein Open-Source-Kit, das hilft Ihnen das Anwenden von Updates für Ihre Win32-Anwendung, wenn Sie keinen Zugriff auf den Quellcode haben, damit sie in einem MSIX-Container ausgeführt werden kann.

Um mehr zu erfahren, finden Sie unter [Übernehmen Runtime auf ein MSIX-Paket mit dem Paket Support-Framework behebt](../porting/package-support-framework.md).

## <a name="developer-guidance"></a>Anleitungen für Entwickler

### <a name="web-api-extensions"></a>Web-API-Erweiterungen

Eine Liste der [Erweiterungen für ältere Microsoft-API](https://developer.mozilla.org/docs/Web/API/Microsoft_API_extensions) wurde in der Dokumentation Mozilla Developer Network browserübergreifende Webentwicklung hinzugefügt. Diese API-Erweiterungen sind spezifisch für Internet Explorer oder Microsoft Edge, und ergänzen vorhandene Informationen zur Kompatibilität und Browser-Unterstützung in der MDN Web-Dokumentation. Ältere Microsoft [CSS-Erweiterungen](https://developer.mozilla.org/docs/Web/CSS/Microsoft_Extensions) und [JavaScript-Erweiterungen](https://developer.mozilla.org/docs/Web/JavaScript/Microsoft_JavaScript_extensions) sind auch verfügbar, und finden Sie umfassende Web-API-Informationen aus MDN ermittlungsfunktionen direkt in [Visual Studio Code.](https://code.visualstudio.com/updates/v1_25#_new-css-pseudo-selectors-and-pseudo-elements-from-mdn)

### <a name="cwinrt-code-examples"></a>C++ / WinRT-Codebeispiele

Wir haben 250 hinzugefügt [C++ / WinRT](../cpp-and-winrt-apis/index.md) Einträge zu Themen in unserer Dokumentation, begleitende vorhandenen C++-code / CX-Code-Beispiele.

### <a name="project-rome"></a>Projekt Rome

Die Website [Projekt "ROME" Dokumente](https://docs.microsoft.com/windows/project-rome/) wurde in einen Ansatz Feature ausgelegt neu organisiert. Dies sollte einfacher für Entwickler zu finden, was sie suchen und Funktionen ihrer Wahl für mehrere Plattformen zu implementieren.

## <a name="videos"></a>Videos

### <a name="xbox-live-unity-plugin"></a>Xbox Live Unity-Plug-in

Die Xbox Live-Plug-In für Unity enthält Unterstützung für das Hinzufügen von Xbox Live Signieren, Statistiken, Freunde-Listen, Cloud-Speicher und Bestenlisten um Ihrem Titel. [Das Video ansehen](https://youtu.be/fVQZ-YgwNpY) , um mehr zu erfahren, und [das GitHub-Paket herunterzuladen](https://aka.ms/UnityPlugin) , für den Einstieg.

### <a name="one-dev-question"></a>One Dev Frage

In der One Dev Frage Videoserie behandelt seit Microsoft-Entwicklern eine Reihe von Fragen zur Windows-Entwicklung, Teamkultur und Verlauf. Hier ist die neueste Fragen, die wir beantwortet haben!

Raymond Chen:

* [Woher weiß der Kernel wann Videotreibers neu gestartet?](https://youtu.be/3SNAdyO1l5c)

Larry Osterman:

* [Was ist die Story hinter dem Burgermaster Objekt in Windows?](https://youtu.be/0TDSbyAIvX0)