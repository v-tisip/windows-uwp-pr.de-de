---
author: normesta
description: Diese Anleitung hilft Ihnen, Fluent-basierte UWP-UIs direkt in einer WPF- oder Windows Forms-Anwendung zu erstellen.
title: Hosten von UWP-Steuerelementen in WPF- und Windows Forms-Anwendungen
ms.author: normesta
ms.date: 05/03/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp, windows forms, wpf
keywords: Windows 10, UWP, Windows Forms, WPF
ms.localizationpriority: medium
ms.openlocfilehash: 4823654bce3373ace5b04ced8ec14c4b6c1b6f1d
ms.sourcegitcommit: 3500825bc2e5698394a8b1d2efece7f071f296c1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2018
ms.locfileid: "1862069"
---
# <a name="host-uwp-controls-in-wpf-and-windows-forms-applications"></a>Hosten von UWP-Steuerelementen in WPF- und Windows Forms-Anwendungen

> [!NOTE]
> Einige Informationen beziehen sich auf die Vorabversion, die vor der kommerziellen Freigabe möglicherweise wesentlichen Änderungen unterliegt. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.

Wir bringen UWP-Steuerelemente auf den Desktop, damit Sie das Aussehen, Verhalten und die Funktionalität Ihrer vorhandenen WPF- oder Windows-Anwendungen mit Fluent Design-Features verbessern können. Dazu gibt es zwei Möglichkeiten.

Zunächst können Sie der Entwurfsoberfläche Ihres WPF- oder Windows Forms-Projekts Steuerelemente direkt hinzufügen und sie dann wie jedes andere Steuerelement im Designer verwenden.  Testen Sie das mit dem neuen **WebView**-Steuerelement. Dieses Steuerelement, das bisher nur für UWP-Anwendungen verfügbar war, verwendet das Renderingmodul aus Microsoft Edge. Sie finden **WebView** im aktuellen [Windows-Community Toolkit](https://docs.microsoft.com/windows/uwpcommunitytoolkit/).

Bald haben Sie auch Zugriff auf andere Fluent Design-Features, denn wir werden ein Steuerelement bereitstellen, mit dem Sie eine Vielzahl von UWP-Steuerelementen hosten können. Sie werden dieses und viele weitere Steuerelemente demnächst im Windows Community Toolkit finden.

Nachfolgend ist dargestellt, wie diese Steuerelemente architektonisch organisiert sind. Die in diesem Diagramm verwendeten Namen werden möglicherweise noch geändert.  

![Hoststeuerelement-Architektur](images/host-controls.png)

Die am Diagrammende aufgeführten APIs sind im Lieferumfang des Windows SDK enthalten.  Die Steuerelemente für den Designer sind als Nuget-Pakete im Windows Community Toolkit geliefert enthalten.

Diese neuen Steuerelemente haben noch Einschränkungen. Bevor Sie die Steuerelemente verwenden, sollten Sie sich einen Moment Zeit nehmen und lesen, was noch nicht unterstützt wird oder nur mit Problemumgehungen funktioniert.

### <a name="whats-supported"></a>Nicht unterstützt

In den meisten Fällen wird nur die Funktionalität nicht unterstützt, die in der folgenden Liste aufgeführt ist.

### <a name="whats-supported-only-with-workarounds"></a>Nur mit Problemumgehungen unterstützt

:heavy_check_mark: Hosting mehrerer Inbox-Steuerelemente innerhalb mehrerer Fenster Sie müssen jedes Fenster in seinem eigenen Thread platzieren.

:heavy_check_mark: Verwendung von ``x:Bind`` mit gehosteten Steuerelementen Sie müssen das Datenmodell in einer .NET Standardbibliothek deklarieren.

:heavy_check_mark: C#-basierte Drittanbieter-Steuerelemente Wenn Sie über den Quellcode eines Drittanbieter-Steuerelements verfügen, können Sie ihn kompilieren.

### <a name="whats-not-yet-supported"></a>Noch nicht unterstützt

:no_entry_sign: Tools mit Bedienungshilfen, die gleichartig für die Anwendung und die gehosteten Steuerelemente funktionieren

:no_entry_sign: Lokalisierter Inhalt in Steuerelementen für Anwendungen, die kein Windows-App-Paket enthalten

:no_entry_sign: Asset-Verweise in XAML innerhalb von Anwendungen, die kein Windows-App-Paket enthalten

:no_entry_sign: Steuerelemente, die korrekt bezüglich Änderungen von DPI und Skalierung reagieren

:no_entry_sign: Hinzufügen eines **WebView**-Steuerelements zu einem benutzerdefinierten Steuerelement (entweder „on-thread”, „off-thread” oder „out of proc”)

:no_entry_sign: Der Fluent-Effekt [Reveal Highlight](https://docs.microsoft.com/windows/uwp/design/style/reveal)

:no_entry_sign: Inline-Freihandeingabe, @Places und @People für Eingabesteuerelemente

:no_entry_sign: Zuweisen von Zugriffstasten

:no_entry_sign: C++-basierte Steuerelemente von Drittanbietern

:no_entry_sign: Hosten benutzerdefinierter Steuerelemente

Die Elemente in dieser Liste werden sich wahrscheinlich ändern, da wir ständig daran arbeiten, Fluent auf dem Desktop zu optimieren.  
