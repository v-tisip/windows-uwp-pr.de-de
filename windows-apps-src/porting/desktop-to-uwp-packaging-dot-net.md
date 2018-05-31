---
author: normesta
Description: This guide explains how to configure your Visual Studio Solution to edit, debug, and package desktop app for the Desktop Bridge.
Search.Product: eADQiWindows 10XVcnh
title: Verpacken einer App mit Visual Studio (Desktop-Brücke)
ms.author: normesta
ms.date: 08/30/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.assetid: 807a99a7-d285-46e7-af6a-7214da908907
ms.localizationpriority: medium
ms.openlocfilehash: d7ae77c499cb8398aa5557f0d422899fbe8b252d
ms.sourcegitcommit: 91511d2d1dc8ab74b566aaeab3ef2139e7ed4945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2018
ms.locfileid: "1816255"
---
# <a name="package-an-app-by-using-visual-studio-desktop-bridge"></a>Verpacken einer App mit Visual Studio (Desktop-Brücke)

Sie können Visual Studio verwenden, um ein Paket für Ihre Desktop-App zu generieren. Anschließend können Sie das Paket im Windows Store veröffentlichen oder es auf einem oder mehreren PCs querladen.

Die aktuelle Version von Visual Studio bietet ein neue Version des Paketprojekts, um manuelle Schritte zu eliminieren, die beim Verpacken Ihrer App erforderlich sind. Sie müssen nur Ihr Paketprojekt hinzufügen, auf das Desktopprojekt verweisen und F5 drücken, um Ihre App zu debuggen. Es sind keine manuellen Optimierungsmethoden mehr erforderlich. Das neue optimierte Design ist eine enorme Verbesserung über die Benutzeroberfläche, die in der vorherigen Version von Visual Studio verfügbar war.

>[!IMPORTANT]
>Der Desktop-Brücke wurde in Windows10, Version 1607, eingeführt und kann nur in Projekten für das Windows10 Anniversary Update (10.0; Build 14393) oder einer neueren Version in Visual Studio verwendet werden.

## <a name="first-consider-how-youll-distribute-your-app"></a>Überlegen Sie zunächst, wie Sie Ihre App verteilen möchten.

Wenn Sie Ihre App im [Microsoft Store](https://www.microsoft.com/store/apps) veröffentlichen möchten, beginnen Sie mit dem Ausfüllen [dieses Formulars](https://developer.microsoft.com/windows/projects/campaigns/desktop-bridge). Microsoft nimmt mit Ihnen Kontakt auf und beginnt den Onboardingprozess. Im Rahmen dieses Prozesses reservieren Sie einen Namen im Store und erhalten Informationen, die Sie benötigen, um Ihre App zu verpacken.

Lesen Sie außerdem unbedingt dieses Handbuch lesen, bevor Sie mit der Paketerstellung für Ihre Anwendung beginnen: [Vorbereiten der Verpackung einer App (Desktop-Brücke)](desktop-to-uwp-prepare.md).

<a id="new-packaging-project"/>

## <a name="create-a-package"></a>Erstellen eines Pakets

1. Öffnen Sie in Visual Studio die Lösung mit Ihrem Desktopanwendungsprojekt.

2. Fügen Sie der Projektmappe ein Projekt **Paketerstellungsprojekt für Windows-Anwendungen** hinzu.

   Sie müssen keinen Code hinzufügen. Es dient nur, um ein Paket zu generieren. Wir nennen das Projekt „Paketprojekt“.

   ![Paketprojekt](images/desktop-to-uwp/packaging-project.png)

   >[!NOTE]
   >Dieses Projekt wird nur in Visual Studio2017 ab Version 15.5 oder höher angezeigt.

3. Legen Sie die **Zielversion** des Projekts auf eine beliebige Version fest, stellen Sie jedoch sicher, dass die **Mindestens erforderliche Version** auf **Windows10 Anniversary Update** eingestellt ist.

   ![Das Dialogfeld zur Auswahl der Paketversion](images/desktop-to-uwp/packaging-version.png)

4. Klicken sie im Paketprojekt mit der rechten Maustaste auf den Ordner **Anwendungen**, und wählen Sie dann **Verweis hinzufügen** aus.

   ![Hinzufügen des Projektverweises](images/desktop-to-uwp/add-project-reference.png)

5. Wählen Sie Ihr Desktopanwendungsprojekt aus, und klicken Sie dann auf die Schaltfläche **OK**.

   ![Desktopprojekt](images/desktop-to-uwp/reference-project.png)

   Sie können mehrere Desktopanwendungen im Paket miteinbeziehen, aber nur eines kann gestartet werden, wenn Benutzer Ihre App-Kachel auswählen. Klicken Sie mit der rechten Maustaste im Knoten **Anwendungen** auf die Anwendung, die die Benutzer starten sollen, wenn sie die App-Kachel auswählen, und wählen Sie dann **Als Einstiegspunkt festlegen** aus.

   ![Als Einstiegspunkt festlegen](images/desktop-to-uwp/entry-point-set.png)

6. Erstellen Sie das Paketprojekt, um sicherzustellen, dass keine Fehler angezeigt werden.

7. Verwenden Sie den Assistenten [App-Pakete erstellen](../packaging/packaging-uwp-apps.md), um eine appxupload-Datei zu erstellen.

   Sie können diese Datei direkt in den Store hochladen.

**Video**

<iframe src="https://www.youtube.com/embed/fJkbYPyd08w" width="636" height="480" allowFullScreen frameBorder="0"></iframe>

## <a name="next-steps"></a>Nächste Schritte

**Finden Sie Antworten auf Ihre Fragen**

Haben Sie Fragen? Fragen Sie uns auf Stack Overflow. Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge). Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).

**Geben Sie Feedback oder Verbesserungsvorschläge**

Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).

**Ausführen, Debuggen oder Testen der App**

Siehe [Ausführen, Debuggen und Testen eine verpackten Desktop-App (Desktop-Brücke)](desktop-to-uwp-debug.md)

**Verbessern Sie Ihre Desktop-App durch Hinzufügen von UWP-APIs**

Siehe [Verbessern Sie Ihre Desktopanwendung für Windows10](desktop-to-uwp-enhance.md)

**Erweitern der Desktop-App durch Hinzufügen von UWP-Projekten und Komponenten für Windows-Runtime**

Weitere Informationen finden Sie unter [Erweitern Ihrer Desktopanwendung mit modernen UWP-Komponenten](desktop-to-uwp-extend.md).

**Verteilen Ihrer App**

Weitere Informationen finden Sie in [Verteilen einer verpackten Desktop-App (Desktop-Brücke)](desktop-to-uwp-distribute.md)
