---
author: QuinnRadich
title: Was ist neu in Windows-Dokumente im August 2018 – Entwickeln von apps UWP
description: Neue Features, Videos, Beispiele und Anleitungen für Entwickler wurden in der Windows-10-Entwicklerdokumentation für August 2018 hinzugefügt.
keywords: Neues in, Update, Features, Developer Leitfaden für die Windows-10, august
ms.author: quradic
ms.date: 08/14/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: c294dedc8e19605bc2cee0308022bed8624df57e
ms.sourcegitcommit: 9a17266f208ec415fc718e5254d5b4c08835150c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2018
ms.locfileid: "2888109"
---
# <a name="whats-new-in-the-windows-developer-docs-in-august-2018"></a>Was ist neu in der Windows-Entwicklerdokumente im August 2018

Die Entwicklerdokumentation für die Windows-Plattform wird ständig mit Informationen über neue Features für Entwickler aktualisiert. Die folgenden Featureübersichten, Developer Anleitungen und Videos sind in den Monat August verfügbar gemacht wurden.

Nach der [Installation der Tools und des SDKs](http://go.microsoft.com/fwlink/?LinkId=821431) unter Windows10 können Sie entweder [eine neue universelle Windows-App erstellen](../get-started/create-uwp-apps.md) oder sich mit der Verwendung von [vorhandenem App-Code unter Windows](../porting/index.md) vertraut machen.

## <a name="features"></a>Features

### <a name="design"></a>Entwerfen

Die folgenden Features wurden an den Windows Insider Preview Builds, über die [Windows-Insider](https://insider.windows.com/) -Anwendung hinzugefügt.

* Die [UI-Bibliothek für Windows](https://aka.ms/winui-docs) ist eine Reihe von NuGet-Pakete, die Steuerelemente und andere interfact Elemente für apps UWP bereitstellen. Diese Pakete sind auch kompatibel mit früheren Versionen von Windows 10, damit Ihre app funktioniert, auch wenn die Benutzer nicht über die neueste Version des Betriebssystems verfügen.

* [DropDownButton](../design/controls-and-patterns/buttons.md#create-a-drop-down-button) [SplitButton](../design/controls-and-patterns/buttons.md#create-a-split-button)und [ToggleSplitButton](../design/controls-and-patterns/buttons.md#create-a-toggle-split-button) bieten Schaltflächensteuerelemente mit speziellen Features Ihrer app-Benutzeroberfläche optimiert.

![Eine Trennschaltfläche für die Auswahl von Vordergrundfarbe](../design/controls-and-patterns/images/split-button-rtb.png)

* NavigationView unterstützt jetzt in der [oberen Navigationsleiste](../design/controls-and-patterns/navigationview.md)für Fälle, in dem Ihre app hat eine geringere Anzahl von Optionen für die Websitenavigation und erfordern mehr Speicherplatz für Ihre app Inhalte.

* "TreeView" wurde verbessert zur Unterstützung der [Daten binden, Vorlagen, Artikel und Drag & drop.](../design/controls-and-patterns/tree-view.md)

### <a name="package-support-framework"></a>Paket-Support-Framework

Das Paket Support-Framework ist ein Open-Source-Kit, die Dank gelten Korrekturen für Ihre Win32-Anwendung, wenn Sie nicht über Zugriff auf den Quellcode verfügen, damit es in einem MSIX-Container ausgeführt werden kann.

Weitere Informationen finden Sie unter [Übernehmen Runtime behebt zu einem Paket MSIX mithilfe des Paket-Support-Frameworks](../porting/package-support-framework.md).

## <a name="developer-guidance"></a>Anleitungen für Entwickler

### <a name="web-api-extensions"></a>Web-API-Erweiterungen

Eine Liste mit [älteren Microsoft-API-Erweiterungen](https://developer.mozilla.org/docs/Web/API/Microsoft_API_extensions) wurde der Mozilla Developer Network-Dokumentation für browserübergreifende Webentwicklung hinzugefügt. Diese API-Erweiterungen stehen nur in Internet Explorer oder Microsoft Edge, und vorhandene Informationen zur Kompatibilität und Browser-Unterstützung in der Webdokumente MDN ergänzen. Ältere Microsoft [CSS-Erweiterungen](https://developer.mozilla.org/docs/Web/CSS/Microsoft_Extensions) und [JavaScript-Erweiterungen](https://developer.mozilla.org/docs/Web/JavaScript/Microsoft_JavaScript_extensions) stehen ebenfalls zur Verfügung, und finden Sie rich-Web-API-Informationen aus MDN verfügbar gemacht, direkt in [Visual Studio-Code.](https://code.visualstudio.com/updates/v1_25#_new-css-pseudo-selectors-and-pseudo-elements-from-mdn)

### <a name="cwinrt-code-examples"></a>C + / WinRT-Codebeispiele

Wir haben 250 hinzugefügt [C + / WinRT](../cpp-and-winrt-apis/index.md) code Auflistungen zu Themen, die in unserer Dokumente, die begleitenden vorhandenen C + / CX-Codebeispiele.

### <a name="project-rome"></a>Projekt Rome

Die [Projekt-ROM-Dokumente](https://docs.microsoft.com/windows/project-rome/) Website wurde in einer Feature-First-Ansatz neu organisiert. Dies sollte erleichtern für Entwickler zu finden, wonach sie suchen und Funktionen ihrer Wahl plattformübergreifend implementieren.

## <a name="videos"></a>Videos

### <a name="xbox-live-unity-plugin"></a>Xbox Live-eins-Plug-in

Die Xbox Live-Plug-Ins für Einheit enthält Unterstützung für das Hinzufügen von Xbox Live Signieren, Stats, Freunde-Listen, Cloud-Speicher und setzen, Ihren Titel. [Video ansehen](https://youtu.be/fVQZ-YgwNpY) , um mehr zu erfahren, und klicken Sie dann auf die ersten Schritte beim [Herunterladen des Pakets GitHub](https://aka.ms/UnityPlugin) .

### <a name="one-dev-question"></a>Eine Dev Frage

In der eine Dev Frage Videoserie behandelt seit Microsoft Entwickler eine Reihe von Fragen zu Windows-Entwicklung, Teamkultur und Verlauf. Nachfolgend finden Sie die neuesten Fragen, die wir angenommen haben!

Raymond Chen:

* [Woher weiß Kernel wann einen Grafiktreiber neu starten?](https://youtu.be/3SNAdyO1l5c)

Larry Osterman:

* [Was ist die Geschichte des Burgermaster-Objekts in Windows?](https://youtu.be/0TDSbyAIvX0)