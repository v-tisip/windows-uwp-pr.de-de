---
author: laurenhughes
ms.assetid: 3a59ff5e-f491-491c-81b1-6aff15886aad
title: Optionale Pakete und die Erstellung zugehöriger Sets
description: Optionale Pakete enthalten Inhalte, die in ein Hauptpaket integriert werden können. Diese sind nützlich für herunterladbare Inhalte (DLC), da große Apps so im Hinblick auf Größenbeschränkungen geteilt werden, oder auch, um zusätzliche Inhalte getrennt von der ursprünglichen App zu liefern.
ms.author: lahugh
ms.date: 09/30/2018
ms.topic: article
keywords: Windows 10, Uwp, optionale Pakete, zusammengehörig, Paket-Erweiterung, visual studio
ms.localizationpriority: medium
ms.openlocfilehash: 8a782ba90fbf350d9a18098d342c05c75dca6ceb
ms.sourcegitcommit: 753e0a7160a88830d9908b446ef0907cc71c64e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "5761092"
---
# <a name="optional-packages-and-related-set-authoring"></a>Optionale Pakete und die Erstellung zugehöriger Sets
Optionale Pakete enthalten Inhalte, die in ein Hauptpaket integriert werden können. Diese sind nützlich für herunterladbare Inhalte (DLC), da große Apps so im Hinblick auf größenbeschränkungen, oder auch zusätzliche Inhalte getrennt von der ursprünglichen app.

Zugehörige Gruppen sind eine Erweiterung der optionalen Pakete – sie zulassen, dass Sie strenger Versionen über Haupt- und optionale Pakete zu erzwingen. Außerdem können Sie auch systemeigenen Code (C++) von optionalen Paketen laden. 

## <a name="prerequisites"></a>Voraussetzungen

- Visual Studio 2017 Version 15.1
- Windows10, Version1703
- Windows 10, Version 1703 SDK

Alle von der aktuellen Entwicklungstools finden Sie [Downloads und Tools für Windows 10](https://developer.microsoft.com/windows/downloads).

> [!NOTE]
> Um eine app übermitteln, die an den Microsoft Store optionale Pakete und/oder zugehörige Gruppen verwendet, benötigen Sie eine Berechtigung. Optionale Pakete und zugehörige Gruppen können ohne Dev Center-Berechtigung für branchenspezifische oder Unternehmens-Apps verwendet werden, wenn sie nicht an den Store übermittelt werden. Informationen zum Erhalt einer Berechtigung, eine App zu übermitteln, die optionale Pakete und zugehörige Gruppen verwendet, finden Sie unter [Windows-Support für Entwickler](https://developer.microsoft.com/windows/support).

### <a name="code-sample"></a>Codebeispiel
Während Sie in diesem Artikel lesen, wird empfohlen, dass Sie folgen Sie das [optionale Paket-Codebeispiel](https://github.com/AppInstaller/OptionalPackageSample) auf GitHub eine praktische zu verstehen und wie optionalen Paketen und Gruppen Arbeit in Visual Studio verwandten.

## <a name="optional-packages"></a>Optionale Pakete
Um ein optionales Paket in Visual Studio erstellen, müssen Sie:
1. Stellen Sie sicher, dass Ihre app **Zielplattformversion Min** auf festgelegt ist: 10.0.15063.0.
2. Öffnen Sie in Ihrem Projekt **Hauptpaket** der `Package.appxmanifest` Datei. Navigieren Sie zur Registerkarte "Verpacken", und notieren Sie Ihren **paketfamilienname**, das ist alles, was vor dem Zeichen "_".
3. Aus Ihrem Projekt **optionales Paket** Rechtsklick die `Package.appxmanifest` , und wählen Sie **mit öffnen > XML (Text) Editor**.
4. Suchen Sie nach dem `<Dependencies>` Element in der Datei. Fügen Sie Folgendes hinzu:

```XML
<uap3:MainPackageDependency Name="[MainPackageDependency]"/>
```

Ersetzen Sie `[MainPackageDependency]` mit der **paketfamilienname** aus Schritt2. Dies legt fest, dass das **optionale Paket** das **Hauptpaket**abhängig ist.

Wenn Sie Ihr Paket-Abhängigkeiten von Schritte 1 bis 4, einrichten haben, können Sie entwickeln wie gewohnt weiter. Wenn Sie Code aus optionalen Pakets in das Hauptpaket laden möchten, müssen Sie eine verwandte Gruppe erstellen. Finden Sie im Abschnitt [verknüpft legt](#related_sets) für weitere Details.

Visual Studio kann konfiguriert werden, um Ihrem Hauptpaket jedes Mal erneut bereitstellen Sie ein optionales Paket bereitstellen. Um die Buildabhängigkeit in Visual Studio festlegen, sollten Sie folgende Aktionen ausführen:

- Klicken Sie mit der rechten Maustaste auf das Projekt optionales Paket, und wählen Sie **Abhängigkeiten Build > Projekt Abhängigkeiten...**
- Überprüfen Sie das Hauptpaket-Projekt, und klicken Sie auf "OK". 

Nun, jedes Mal, wenn Sie F5 eingeben oder ein optionales Paket-Projekt erstellen, wird Visual Studio das Hauptpaket Projekt erstellen zuerst. Dadurch wird sichergestellt, dass Ihre Hauptprojekt und optionale Projekte synchronisiert sind.

## Zugehörige Gruppen<a name="related_sets"></a>

Wenn Sie Code über ein optionales Paket in das Hauptpaket laden möchten, müssen Sie eine verwandte Gruppe erstellen. Um eine verwandte Gruppe zu erstellen, müssen Ihre Hauptpaket und optionalen Pakets eng gekoppelt werden. Die Metadaten für zugehörige Gruppen wird in der Datei .appxbundle oder .msixbundle des Hauptpakets angegeben. Visual Studio können Sie die richtige Metadaten in Ihren Dateien abgerufen. Gehen Sie folgendermaßen vor, um Ihre app-Lösung für die zugehörige Gruppen zu konfigurieren:

1. Klicken Sie mit der rechten Maustaste auf das Hauptpaket-Projekt, wählen Sie **Hinzufügen > Neues Element**
2. Klicken Sie im Fenster Suchen Sie die installierten Vorlagen für "txt", und fügen Sie eine neue Textdatei.
> [!IMPORTANT]
> Die neue Textdatei muss den Namen: `Bundle.Mapping.txt`.
3. In der `Bundle.Mapping.txt` Datei, die Sie geben relative Pfade für alle optionalen Pakets Projekte oder externe Pakete. Ein Beispiel für `Bundle.Mapping.txt` Datei sollte etwa wie folgt aussehen:

```syntax
[OptionalProjects]
"..\ActivatableOptionalPackage1\ActivatableOptionalPackage1.vcxproj"
"..\ActivatableOptionalPackage2\ActivatableOptionalPackage2.vcxproj"

[ExternalPackages]
"..\ActivatableOptionalPackage1\x86\Release\ActivatableOptionalPackage3_1.1.1.0\ ActivatableOptionalPackage3_1.1.1.0.appx"
```

Wenn Ihre Lösung auf diese Weise konfiguriert ist, erstellt Visual Studio ein bündelmanifest für das Hauptpaket mit alle erforderlichen Metadaten für zugehörige Gruppen. 

Beachten Sie, die optionale Pakete wie ein `Bundle.Mapping.txt` -Datei für Dateisätze funktioniert nur unter Windows 10, Version 1703. Darüber hinaus sollte Ihre app Min Zielplattformversion auf 10.0.15063.0 festgelegt werden.

## Bekannte Probleme<a name="known_issues"></a>

Debuggen eines optionalen zusammengehörig-Projekts ist derzeit in Visual Studio nicht unterstützt. Um dieses Problem zu umgehen, können Sie bereitstellen und starten die Aktivierung (STRG + F5) und manuell den Debugger an einen Prozess anhängen. Um den Debugger anzufügen, wechseln Sie in Visual Studio im Menü "Debug", wählen Sie "Anhängen zum Prozess...", und hängen Sie den Debugger an der **Haupt-app-Prozess**.