---
author: normesta
Description: This guide explains how to configure your Visual Studio Solution to edit, debug, and package desktop application.
Search.Product: eADQiWindows 10XVcnh
title: Verpacken Sie eine desktop-Anwendung mit Visual Studio
ms.author: normesta
ms.date: 08/30/2017
ms.topic: article
keywords: windows10, UWP
ms.assetid: 807a99a7-d285-46e7-af6a-7214da908907
ms.localizationpriority: medium
ms.openlocfilehash: cc71a58594c8794369bedd7f415518100892ff67
ms.sourcegitcommit: e38b334edb82bf2b1474ba686990f4299b8f59c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6855203"
---
# <a name="package-a-desktop-application-by-using-visual-studio"></a>Verpacken Sie eine desktop-Anwendung mit Visual Studio

Sie können Visual Studio verwenden, um ein Paket für Ihre Desktop-App zu generieren. Anschließend können Sie veröffentlichen, die auf den Microsoft Store oder querladen es auf einem oder mehreren PCs verpacken.

Die aktuelle Version von Visual Studio bietet ein neue Version des Paketprojekts, um manuelle Schritte zu eliminieren, die beim Verpacken Ihrer App erforderlich sind. Sie müssen nur Ihr Paketprojekt hinzufügen, auf das Desktopprojekt verweisen und F5 drücken, um Ihre App zu debuggen. Es sind keine manuellen Optimierungsmethoden mehr erforderlich. Das neue optimierte Design ist eine enorme Verbesserung über die Benutzeroberfläche, die in der vorherigen Version von Visual Studio verfügbar war.

>[!IMPORTANT]
>Die Fähigkeit zum Erstellen eines Windows-app-Pakets für Ihre desktop-Anwendung (auch bekannt als der Desktop-Brücke) wurde in Windows 10, Version 1607, eingeführt und kann nur in Projekten für die Windows 10 Anniversary Update (10.0; verwendet werden Build 14393) oder einer neueren Version in Visual Studio.

## <a name="first-prepare-your-application"></a>Vorbereiten Ihrer Anwendung

Lesen Sie dieses Handbuch, bevor Sie mit der paketerstellung für Ihre Anwendung beginnen: [Vorbereiten eine desktop-Anwendung zu verpacken](desktop-to-uwp-prepare.md).

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

6. Erstellen Sie das Paketprojekt, um sicherzustellen, dass keine Fehler angezeigt werden.  Wenn Sie Fehler zu erhalten, öffnen Sie den **Konfigurations-Manager** , und stellen, dass sicher Plattform Ihre Projekte dieselbe.

   ![Konfigurations-manager](images/desktop-to-uwp/config-manager.png)

7. Verwenden Sie den Assistenten [App-Pakete erstellen](../packaging/packaging-uwp-apps.md), um eine appxupload-Datei zu erstellen.

   Sie können diese Datei direkt an den Store hochladen.

**Video**

&nbsp;
> [!VIDEO https://www.youtube.com/embed/fJkbYPyd08w]

## <a name="next-steps"></a>Nächste Schritte

**Finden Sie Antworten auf Ihre Fragen**

Haben Sie Fragen? Fragen Sie uns auf Stack Overflow. Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge). Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).

**Geben Sie Feedback oder Verbesserungsvorschläge**

Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).

**Führen Sie aus, Debuggen Sie oder testen Sie Ihre desktop-Anwendung**

Finden Sie unter [ausführen, Debuggen und testen eine verpackte desktop-Anwendung](desktop-to-uwp-debug.md)

**Verbessern Sie Ihre desktop-Anwendung durch Hinzufügen von UWP-APIs**

Siehe [Verbessern Sie Ihre Desktopanwendung für Windows10](desktop-to-uwp-enhance.md)

**Erweitern Sie Ihre desktop-Anwendung durch Hinzufügen von UWP-Projekten und Komponenten für Windows-Runtime**

Weitere Informationen finden Sie unter [Erweitern Ihrer Desktopanwendung mit modernen UWP-Komponenten](desktop-to-uwp-extend.md).

**Verteilen Ihrer App**

Finden Sie unter [Verteilen einer verpackten desktop-Anwendung](desktop-to-uwp-distribute.md)
