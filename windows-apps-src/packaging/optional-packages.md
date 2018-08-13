---
author: laurenhughes
ms.assetid: 3a59ff5e-f491-491c-81b1-6aff15886aad
title: Optionale Pakete und die Erstellung zugehöriger Sets
description: Optionale Pakete enthalten Inhalte, die in ein Hauptpaket integriert werden können. Diese sind nützlich für herunterladbare Inhalte (DLC), da große Apps so im Hinblick auf Größenbeschränkungen geteilt werden, oder auch, um zusätzliche Inhalte getrennt von der ursprünglichen App zu liefern.
ms.author: lahugh
ms.date: 04/05/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, optional Pakete, ähnliche, Paket-Erweiterung, visual studio
ms.localizationpriority: medium
ms.openlocfilehash: d66a511211396190393e31bfd553149a1e89fad0
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "406083"
---
# <a name="optional-packages-and-related-set-authoring"></a>Optionale Pakete und die Erstellung zugehöriger Sets
Optionale Pakete enthalten Inhalte, die in ein Hauptpaket integriert werden können. Diese eignen sich für eine große-app für Größe Beschränkungen, Division Bücher (DLC), oder für den Versand alle zusätzlichen Inhalte aus Ihrer ursprünglichen app zu trennen.

Verwandte sind eine Erweiterung der optionale Pakete – können Sie strenge Versionen für Haupt- und optional Pakete zu erzwingen. Außerdem können Sie auch systemeigenen Code (C++) aus optionale Pakete zu laden. 

## <a name="prerequisites"></a>Voraussetzungen

- Visual Studio 2017, Version 15.1.
- Windows10, Version1703
- Windows-10, Version 1703 SDK (engl.)

So rufen Sie alle der neuesten Entwicklungstools, finden Sie unter [Downloads und Tools für Windows 10](https://developer.microsoft.com/windows/downloads).

> [!NOTE]
> Wenn Sie eine app übermitteln, die an den Microsoft-Store optionale Pakete und/oder verwandte verwendet, benötigen Sie die Berechtigung. Optionale Pakete und zugehörige Gruppen können ohne Dev Center-Berechtigung für branchenspezifische oder Unternehmens-Apps verwendet werden, wenn sie nicht an den Store übermittelt werden. Informationen zum Erhalt einer Berechtigung, eine App zu übermitteln, die optionale Pakete und zugehörige Gruppen verwendet, finden Sie unter [Windows-Support für Entwickler](https://developer.microsoft.com/windows/support).

### <a name="code-sample"></a>Codebeispiel
Während Sie in diesem Artikel lesen, wird empfohlen, dass Sie führen Sie eine praktische zu verstehen und wie optionale Pakete auf GitHub sowie die [optionalen Paket Codebeispiel](https://github.com/AppInstaller/OptionalPackageSample) und damit legt Arbeit in Visual Studio verbundene.

## <a name="optional-packages"></a>Optionale Pakete
Um ein optionales Paket in Visual Studio erstellen möchten, benötigen Sie:
1. Stellen Sie sicher, dass Ihre app- **Plattform Min-Zielversion** auf festgelegt ist: 10.0.15063.0.
2. Aus dem Projekt **Hauptfenster Paket** öffnen Sie die `Package.appxmanifest` Datei. Navigieren Sie zur Registerkarte "Packen", und notieren Sie Ihre **Familie Paketname**, ist alles vor dem Zeichen "_".
3. Aus dem Projekt **optionales Paket** rechten Maustaste klicken Sie auf die `Package.appxmanifest` und wählen Sie **mit Open > XML (Text) Editor**.
4. Suchen Sie nach der `<Dependencies>` Element in der Datei. Fügen Sie Folgendes ein:

```XML
<uap3:MainPackageDependency Name="[MainPackageDependency]"/>
```

Ersetzen Sie `[MainPackageDependency]` Ihre **Familie Paketname** aus Schritt2. Dies wird angegeben, dass Ihr **Paket optional** das **Hauptfenster Paket**abhängig ist.

Sobald Sie Paket Abhängigkeiten von Schritte 1 bis 4 eingerichtet haben, können Sie die Entwicklung von weiterhin, wie gewohnt verwenden. Wenn Sie Code in das Hauptfenster Paket aus dem optionalen Paket laden möchten, müssen Sie eine zugehörige Gruppe erstellen. Finden Sie weitere Informationen im Abschnitt [verknüpft wird](#related_sets) .

Visual Studio kann konfiguriert werden, um das Hauptfenster Paket jedes Mal erneut bereitstellen Sie ein optionales Paket bereitstellen. Wenn die Buildabhängigkeit in Visual Studio festlegen möchten, sollten Sie folgende Schritte ausführen:

- Klicken Sie mit der rechten Maustaste auf das Projekt optionales Paket, und wählen Sie **Abhängigkeiten Build > Project Dependencies...**
- Aktivieren Sie das Hauptfenster Paket-Projekt, und wählen Sie "OK". 

Nun, jedes Mal, wenn Sie F5 eingeben oder ein optionales Paket-Projekt erstellen, wird Visual Studio Haupt-Paket zuerst erstellen das Projekt. Dadurch wird sichergestellt, dass Ihre Hauptassembly des Projekts und optional Projekte synchronisiert sind.

## Verwandte<a name="related_sets"></a>

Wenn Sie Code in das Hauptfenster Paket aus einem Paket optional laden möchten, müssen Sie eine zugehörige Gruppe erstellen. Um ähnliche zu erstellen, müssen Ihre wichtigsten Paket und optional Paket eng verknüpft sein. Die Metadaten für verwandte wird angegeben, der `.appxbundle` Datei des Haupt-Pakets. Visual Studio unterstützt Sie bei die richtige Metadaten in den Dateien. Gehen Sie folgendermaßen vor, um Ihre app-Lösung für verwandte zu konfigurieren:

1. Klicken Sie mit der rechten Maustaste auf das Hauptfenster Paket-Projekt, wählen Sie **Hinzufügen > Neues Element...**
2. Klicken Sie im Fenster Suchen Sie die installierte Vorlagen für "txt", und fügen Sie eine neue Textdatei.
> [!IMPORTANT]
> Muss den Namen der neuen Textdatei: `Bundle.Mapping.txt`.
3. In der `Bundle.Mapping.txt` Datei benötigen Sie relative Pfade an einem beliebigen optionales Paket Projekte oder externe Pakete angeben. Ein Beispiel für `Bundle.Mapping.txt` Datei sollte in etwa wie folgt aussehen:

```syntax
[OptionalProjects]
"..\ActivatableOptionalPackage1\ActivatableOptionalPackage1.vcxproj"
"..\ActivatableOptionalPackage2\ActivatableOptionalPackage2.vcxproj"

[ExternalPackages]
"..\ActivatableOptionalPackage1\x86\Release\ActivatableOptionalPackage3_1.1.1.0\ ActivatableOptionalPackage3_1.1.1.0.appx"
```

Wenn Ihre Lösung auf diese Weise konfiguriert ist, erstellt Visual Studio ein Manifest Bundle für das Hauptfenster Paket mit alle erforderlichen Metadaten für verwandte. 

Notiz, die optionale Pakete, wie eine `Bundle.Mapping.txt` -Datei für verwandte funktioniert nur auf Windows-10, Version 1703. Darüber hinaus sollten Ihre app Zielversion Plattform Min auf 10.0.15063.0 festgelegt werden.

## Bekannte Probleme<a name="known_issues"></a>

Debuggen eines optional ähnliche-Projekts wird derzeit in Visual Studio nicht unterstützt. Dieses Problem zu umgehen, können Sie bereitstellen und manuelles Anfügen des Debuggers an einen Prozess und starten Sie die Aktivierung (STRG + F5). Zum Anfügen des Debuggers wechseln Sie in Visual Studio im Menü "Debuggen", wählen Sie "Anfügen an Prozess..." und fügen Sie des Debuggers an den **Prozess Hauptfenster app an**.