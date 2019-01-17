---
title: Was ist neu in Windows-Dokumentation im Januar 2019 – Entwicklung von UWP-apps
description: Neue Features, Videos und entwicklerleitfäden wurden in der Windows 10-Entwicklerdokumentation für Januar 2019 hinzugefügt
keywords: Neues in, Update, Features, Anleitungen für Entwickler, Windows 10, Januar
ms.date: 1/17/2019
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 4f224663506cbb60f6c1476caccb5ecffefeaf7b
ms.sourcegitcommit: cfdc854fede8e586202523cdb59d3d0a2f5b4b36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2019
ms.locfileid: "9014406"
---
# <a name="whats-new-in-the-windows-developer-docs-in-january-2019"></a>Was ist neu in der Windows-Entwicklerdokumentation im Januar 2019

Die Entwicklerdokumentation für die Windows-Plattform wird ständig mit Informationen über neue Features für Entwickler aktualisiert. Die folgenden Featureübersichten, entwicklerleitfäden und Videos wurden im Januar zur Verfügung gestellt wurden.

Nach der [Installation der Tools und des SDKs](http://go.microsoft.com/fwlink/?LinkId=821431) unter Windows10 können Sie entweder [eine neue universelle Windows-App erstellen](../get-started/create-uwp-apps.md) oder sich mit der Verwendung von [vorhandenem App-Code unter Windows](../porting/index.md) vertraut machen.

## <a name="features"></a>Features

### <a name="windows-development-on-microsoft-learn"></a>Entwicklung von Windows auf Microsoft Learn

Microsoft Learn bietet neue praktische Learning und Schulung begünstigen für Microsoft-Entwickler. Wenn Sie zum Entwickeln von Windows-apps interessiert sind, sehen Sie sich [unsere neue Lernpfad](https://docs.microsoft.com/learn/paths/develop-windows10-apps/) für eine umfassende Einführung in die Plattform, die Tools und wie Sie Ihre erste einige apps schreiben.

![Bild von der Windows-Entwicklung Lernpfad](images/windows-learn.png)

### <a name="direct-3d-12"></a>Direct3D 12-Beschleunigung

[Direct3D 12 Rendern übergibt](/windows/desktop/direct3d12/direct3d-12-render-passes) können die Leistung des Renderers verbessern, wenn sie auf die Kachel-basierte zurückgestellt Wiedergabe (TBDR), zu anderen Techniken basiert. Die Technik hilft des Renderers zur Verbesserung der GPU-Effizienz durch Aktivieren von Ihrer Anwendung Ressource Rendering Sortierung Anforderungen und Daten Abhängigkeiten leichter zu identifizieren und wodurch Speicher-Datenverkehr in a-Chip-Speicher.

### <a name="msix-modification-packages"></a>MSIX-Änderung Pakete

Windows 10-Version 1809 verbesserte Unterstützung für [MSIX Änderung Pakete](https://docs.microsoft.com/windows/msix/modification-package-1809-update). Änderung Pakete können registrierungsbasierte-Plug-Ins und zugeordneten Anpassung gehören und ermöglicht es einer Anwendung, die über MSIX eine virtuelle Registrierung und wie erwartet ausgeführt bereitgestellt werden.

![MSIX-Änderung die Erstellung des Pakets](images/msix-modification-package.png)

### <a name="open-source-of-wpf-windows-forms-and-winui"></a>Open-Source von WPF, Windows Forms und WinUI

WPF, Windows Forms und WinUI UX-Frameworks sind jetzt für Open-Source-Beiträge auf GitHub verfügbar. Weitere Informationen und Links finden Sie unter der [Windows-apps Blog erstellen](https://blogs.windows.com/buildingapps/2018/12/04/announcing-open-source-of-wpf-windows-forms-and-winui-at-microsoft-connect-2018/#OKZjJs1VVTrMMtkL.97).

### <a name="progressive-web-apps-for-xbox"></a>Progressive Web-Apps für Xbox

[Progressive Web-Apps für Xbox One](https://docs.microsoft.com/microsoft-edge/progressive-web-apps/xbox-considerations)können Sie eine Anwendung erweitern und zur Verfügung stellen als ein Xbox One-app über den Microsoft Store und trotzdem weiterhin auf Ihrer vorhandenen Frameworks, CDN und Server-Back-End verwenden. Sie können in den meisten Fällen Ihre PWA für Xbox One Verpacken, auf die gleiche Weise wie für Windows, es gibt jedoch einige wichtige Unterschiede, die diesem Handbuch Sie durchlaufen werden.

### <a name="windows-machine-learning"></a>Windows Machine learning

Wir haben neu strukturiert [die Startseite für WinML-APIs](https://docs.microsoft.com/windows/ai/api-reference)und neue Dokumentation für benutzerdefinierte Operator WinML und systemeigene APIs hinzugefügt.

[Trainieren Sie ein Modell mit PyTorch](https://docs.microsoft.com/windows/ai/train-model-pytorch) Hinweise zum Trainieren Sie ein Modell mit dem PyTorch-Framework, lokal oder in der Cloud. Sie können dann dieses Modell als ONNX-Datei herunterladen und verwenden es in Ihrer Anwendung WinML.

![WinML-Grafik](images/winml-graphic.png)

## <a name="developer-guidance"></a>Anleitungen für Entwickler

### <a name="choose-your-platform"></a>Wählen Sie Ihre Plattform

Erstellen einer neuen desktop-Anwendung möchten? Sehen Sie sich unsere überarbeitete Seite [Auswählen der Plattform](https://docs.microsoft.com/windows/desktop/choose-your-technology) für ausführliche Beschreibungen und Vergleichen der UWP, WPF und Windows Forms-Plattformen und Weitere Informationen zu der Win32-API.

### <a name="faqs-on-win32-webview"></a>Häufig gestellte Fragen für Win32-WebView

Unsere [häufig gestellte Fragen](https://docs.microsoft.com/windows/communitytoolkit/controls/wpf-winforms/webview#frequently-asked-questions-faqs) enthält Antworten auf häufig gestellte Fragen bei Verwendung der Microsoft Edge WebView in desktop-Apps sowie Links zu Beispiele und weitere Ressourcen.

### <a name="japanese-era-change"></a>Japanischen Era-Änderung

[Vorbereiten Ihrer Anwendung für den japanischen Era ändern](../design/globalizing/japanese-era-change.md) , zeigt, wie um sicherzustellen, dass Ihre Windows-Anwendung bereit ist, für den japanischen Era ändern Satz wird am 1. Mai 2019 platzieren. [Diese Seite ist auch in Japanisch verfügbar](https://docs.microsoft.com/ja-jp/windows/uwp/design/globalizing/japanese-era-change).

## <a name="videos"></a>Videos

### <a name="progressive-web-apps"></a>Progressive Web-Apps

Progressive Web-Apps sind Websites, die in verschiedenen Browsern und eine Vielzahl von Windows 10-Geräte wie native apps funktionieren. [Das Video ansehen](https://youtu.be/ugAewC3308Y) , um mehr zu erfahren, und klicken Sie dann [sehen Sie sich die Dokumentation](http://aka.ms/Windows-PWA) für den Einstieg.

### <a name="vs-code-series"></a>VS-Code-Serie

Sehen Sie sich unsere [neue Videoserie in Visual Studio Code](https://www.youtube.com/playlist?list=PLlrxD0HtieHjQX77y-0sWH9IZBTmv1tTx) Informationen was VSCode ist, wie sie zu verwenden, und wie es erstellt wurde.

### <a name="one-dev-question"></a>One Dev Frage

In der eine Dev Frage Videoserie behandelt seit Microsoft-Entwicklern eine Reihe von Fragen zur Windows-Entwicklung, Teamkultur, und zum Verlauf. Hier ist die neueste Fragen, die wir beantwortet haben!

Raymond Chen:

* [Warum haben Programmdateien und Programmdateien (x86)?](https://youtu.be/N7o9eJpFYco)

Larry Osterman:

* [Warum COM ist so kompliziert?](https://youtu.be/-gkXAV-StVA )
* [Was ist die erste Interview wie für Microsoft?](https://youtu.be/qRb6otsHG5c)
