---
title: Was ist neu in Windows-Dokumentation im August 2018 – Entwicklung von UWP-apps
description: Neue Features, Videos, Beispiele und entwicklerleitfäden wurden in der Windows 10-Entwicklerdokumentation für August 2018 hinzugefügt.
keywords: Neues in, Update, Features, Anleitungen für Entwickler, Windows 10, august
ms.date: 08/14/2018
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: da8bc3b441a1b619e086934f277cb14be6bcc37a
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8788460"
---
# <a name="whats-new-in-the-windows-developer-docs-in-august-2018"></a>Neuigkeiten in der Windows-Entwicklerdokumentation im August 2018

Die Entwicklerdokumentation für die Windows-Plattform wird ständig mit Informationen über neue Features für Entwickler aktualisiert. Die folgenden Featureübersichten, entwicklerleitfäden und Videos wurden im Monat August zur Verfügung gestellt wurden.

Nach der [Installation der Tools und des SDKs](http://go.microsoft.com/fwlink/?LinkId=821431) unter Windows10 können Sie entweder [eine neue universelle Windows-App erstellen](../get-started/create-uwp-apps.md) oder sich mit der Verwendung von [vorhandenem App-Code unter Windows](../porting/index.md) vertraut machen.

## <a name="features"></a>Features

### <a name="design"></a>Entwerfen

Die folgenden Features wurden auf die Windows Insider Preview-Builds, über das [Windows-Insider-](https://insider.windows.com/) Programm verfügbar hinzugefügt.

* Der [Windows-UI-Bibliothek](https://aka.ms/winui-docs) ist eine Reihe von NuGet-Pakete, die Steuerelemente und andere Elemente interfact für UWP-apps bereitstellen. Diese Pakete sind auch kompatibel mit früheren Versionen von Windows 10, damit Ihre app funktioniert, auch wenn der Benutzer die aktuelle Version des Betriebssystems besitzen.

* [DropDownButton](../design/controls-and-patterns/buttons.md#create-a-drop-down-button), [SplitButton](../design/controls-and-patterns/buttons.md#create-a-split-button)und [ToggleSplitButton](../design/controls-and-patterns/buttons.md#create-a-toggle-split-button) bieten die Steuerelemente mit speziellen Features zur Verbesserung der Benutzeroberfläche Ihrer app.

![Eine geteilte Schaltfläche für die Vordergrundfarbe auswählen](../design/controls-and-patterns/images/split-button-rtb.png)

* NavigationView unterstützt jetzt in der [oberen Navigationsleiste](../design/controls-and-patterns/navigationview.md)für Fälle, in dem Ihre app verfügt über weniger Navigationsoptionen und mehr Platz für den Inhalt Ihrer app erforderlich.

* Strukturansicht wurde zur Unterstützung von erweitert [die Datenbindung, Elementvorlagen, und Drag & Drop.](../design/controls-and-patterns/tree-view.md)

### <a name="package-support-framework"></a>Paket-Support-Framework

Das Paket-Unterstützung ist ein Open-Source-Kit, mit dem Sie das Anwenden von Updates für Ihre win32-Anwendung, wenn Sie keinen Zugriff auf den Quellcode, haben, damit sie in einem MSIX-Container ausgeführt werden kann.

Weitere Informationen finden Sie in der [Übernehmen Runtime behebt ein MSIX-Paket mit dem Paket-Support-Framework](../porting/package-support-framework.md).

## <a name="developer-guidance"></a>Anleitungen für Entwickler

### <a name="web-api-extensions"></a>Web-API-Erweiterungen

Eine Liste der [Erweiterungen für ältere Microsoft-API](https://developer.mozilla.org/docs/Web/API/Microsoft_API_extensions) wurde in der Dokumentation Mozilla Developer Network browserübergreifende Webentwicklung hinzugefügt. Diese API-Erweiterungen sind spezifisch für Internet Explorer oder Microsoft Edge, und ergänzen vorhandene Informationen zur Kompatibilität und Browser-Unterstützung in der MDN Web-Dokumentation. Ältere Microsoft [CSS-Erweiterungen](https://developer.mozilla.org/docs/Web/CSS/Microsoft_Extensions) und [JavaScript-Erweiterungen](https://developer.mozilla.org/docs/Web/JavaScript/Microsoft_JavaScript_extensions) sind auch verfügbar, und finden Sie umfassende Web-API-Informationen von MDN Warnungen direkt in [Visual Studio Code.](https://code.visualstudio.com/updates/v1_25#_new-css-pseudo-selectors-and-pseudo-elements-from-mdn)

### <a name="cwinrt-code-examples"></a>C++ / WinRT-Code-Beispiele

Wir haben 250 hinzugefügt [C++ / WinRT](../cpp-and-winrt-apis/index.md) Einträge zu Themen in unserer Dokumentation, begleitende vorhandenen C++-code / CX-Code-Beispiele.

### <a name="project-rome"></a>Project Rome

Die Website [Project Rome Dokumente](https://docs.microsoft.com/windows/project-rome/) wurde in einen Ansatz Feature ausgelegt neu organisiert. Dies sollte einfacher für Entwickler zu finden, was sie suchen und Features ihrer Wahl für mehrere Plattformen zu implementieren.

## <a name="videos"></a>Videos

### <a name="xbox-live-unity-plugin"></a>Xbox Live Unity-Plug-in

Die Xbox Live-Plug-In für Unity enthält Unterstützung für das Hinzufügen von Xbox Live zu signieren, Statistiken, Freunde-Listen, Cloud-Speicher und Bestenlisten um Ihrem Titel. [Das Video ansehen](https://youtu.be/fVQZ-YgwNpY) , um mehr zu erfahren, und klicken Sie dann [GitHub-Paket herunterzuladen](https://aka.ms/UnityPlugin) , um zu beginnen.

### <a name="one-dev-question"></a>One Dev Frage

In der eine Dev Frage Videoserie behandelt seit Microsoft-Entwicklern eine Reihe von Fragen zur Windows-Entwicklung, Teamkultur, und zum Verlauf. Hier ist die neueste Fragen, die wir beantwortet haben!

Raymond Chen:

* [Woher weiß der Kernel bei Videotreibers neu gestartet?](https://youtu.be/3SNAdyO1l5c)

Larry Osterman:

* [Was ist die Story hinter dem Burgermaster-Objekt in Windows?](https://youtu.be/0TDSbyAIvX0)