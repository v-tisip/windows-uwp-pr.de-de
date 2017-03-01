---
author: Mtoepke
title: Deaktivierung des Xbox One-Entwicklermodus
description: In diesem Artikel wird das Deaktivieren des Entwicklermodus beschrieben.
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
ms.assetid: 244124dd-d80a-4a72-91db-1c9c2fbc7c3c
translationtype: Human Translation
ms.sourcegitcommit: 5645eee3dc2ef67b5263b08800b0f96eb8a0a7da
ms.openlocfilehash: 857b1529a933f416a1c61f3afd844f6cb820f3f3
ms.lasthandoff: 02/08/2017

---

# <a name="xbox-one-developer-mode-deactivation"></a>Deaktivierung des Xbox One-Entwicklermodus

* [Wechseln zum Retailmodus](#switch-to-retail-mode)
* [Deaktivieren der Konsole mit der DevMode-Aktivierungsapp](#deactivate-your-console-using-the-dev-mode-activation-app)  
* [Zurücksetzen der Konsole](#reset-your-console)
* [Deaktivieren der Konsole mit Windows Dev Center](#deactivate-your-console-using-windows-dev-center)

Wenn Sie die Konsole nicht mehr für die Entwicklung verwenden möchten, führen Sie die folgenden Schritte aus, um den Entwicklermodus zu deaktivieren.

## <a name="switch-to-retail-mode"></a>Wechseln zum Einzelhandelsmodus
Setzen Sie zunächst die Xbox One-Konsole in den Einzelhandelsmodus zurück.

1. Öffnen Sie **Dev Home**.
2. Klicken Sie auf **Entwicklermodus beenden**.  Die Konsole wird im Einzelhandelsmodus neu gestartet.  

   ![Beenden des Entwicklermodus](images/deactivation-leave-dev-mode.png)

Deaktivieren Sie jetzt die Konsole mithilfe einer der folgenden Methoden.

## <a name="deactivate-your-console-using-the-dev-mode-activation-app"></a>Deaktivieren der Konsole mit der DevMode-Aktivierungsapp

Die bevorzugte Methode zum Deaktivieren des Entwicklermodus ist die Verwendung der DevMode-Aktivierungs-App. 

1. Navigieren Sie zu **My games & apps** > **Apps**.
  
   ![Aktivierungsschritt 3](images/activation-step-3.png)    
   
2.  Öffnen Sie die Devmode-Aktivierungs-App.    
3.  Klicken Sie auf **Deaktivieren**.
  
![Deaktivieren der Konsole](images/deactivation-app.png)

## <a name="reset-your-console"></a>Zurücksetzen der Konsole

Sie können den Entwicklermodus auch deaktivieren, indem Sie die Konsole zurücksetzen.  

> [!NOTE]
> Wenn Sie die Konsole zurücksetzen, gehen alle lokal gespeicherten Spieldaten verloren.

Führen Sie zum Zurücksetzen der Konsole die folgenden Schritte aus:

1.  Wechseln Sie zu **My games & apps**.  
2.  Wählen Sie **Apps** und dann **Einstellungen**.  
3.  Wechseln Sie im rechten Bereich zu **System**, und wählen Sie dann im linken Bereich **Console info & updates** aus.  
4.  Wechseln Sie zu **Console info & updates**.  
   
    ![Console info and updates](images/deactivation-console-info-updates.png)  
    
5.  Klicken Sie auf **Reset console**.
    
    ![Reset console](images/deactivation-reset-console.png)
    
6.  Klicken Sie anschließend auf **Reset and remove everything**. Mit dieser Option wird die Konsole in den ursprünglichen Einzelhandelszustand zurückgesetzt.  Alle Apps, Spiele und lokal gespeicherten Daten werden gelöscht. Beachten Sie, dass die Konsole nicht aus dem Entwicklerprogramm gelöscht wird, wenn Sie die andere Option, **Reset and keep my games & apps**, auswählen.  
   
    ![Reset and remove everything](images/deactivation-reset-remove.png)

## <a name="deactivate-your-console-using-windows-dev-center"></a>Deaktivieren der Konsole mit Windows Dev Center

Wenn Sie aus irgendeinem Grund keinen Zugriff auf die Konsole haben, können Sie auch mit Windows Dev Center den Entwicklermodus auf der Konsole deaktivieren.

1. Rufen Sie [developer.microsoft.com/xboxdevices](https://developer.microsoft.com/xboxdevices) auf.    
2. Melden Sie sich mit Ihrem Dev Center-Konto beim Dev Center an.    
3. Suchen Sie in der Liste der Konsolen die Konsole, die Sie deaktivieren möchten, anhand der Seriennummer, Konsolen-ID oder Geräte-ID.  
4. Klicken Sie auf **Deaktivieren**.  
  
![Deaktivieren mit Dev Center](images/deactivation-devcenter.png)

Wenn Sie die Xbox One-Konsole noch nicht in den Einzelhandelsmodus zurückgesetzt haben, holen Sie dies jetzt nach.

1. Starten Sie **Dev Home**.
2. Klicken Sie auf **Leave developer mode**.  Die Konsole wird im Einzelhandelsmodus neu gestartet.

![Aktivierungsschritt 13](images/deactivation-leave-dev-mode.png)

## <a name="see-also"></a>Weitere Informationen
- [Aktivierung des Xbox One-Entwicklermodus](devkit-activation.md)
- [UWP auf Xbox One](index.md)

