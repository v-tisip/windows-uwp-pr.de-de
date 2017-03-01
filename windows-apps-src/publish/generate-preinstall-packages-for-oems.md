---
author: jnHs
Description: "Wenn Ihrem Entwicklerkonto die entsprechenden Berechtigungen gewährt wurden, können Sie Vorinstallationspakete generieren und herunterladen, die von einem OEM verwendet werden können, um Ihre App in ein Image einzuschließen."
title: "Generieren von Vorinstallationspaketen für OEMs"
ms.assetid: AC3A45E8-7BBD-44E9-B2D3-B74B7C9B2BC9
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP"
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 962b6b7361da8b88d13b37219fab538e1510c961
ms.lasthandoff: 02/07/2017

---

# <a name="generate-preinstall-packages-for-oems"></a>Generieren von Vorinstallationspaketen für OEMs


Wenn Ihrem Entwicklerkonto die entsprechenden Berechtigungen gewährt wurden, können Sie Vorinstallationspakete generieren und herunterladen, die von einem OEM verwendet werden können, um Ihre App in ein Image einzuschließen. Vorinstallationsberechtigungen werden nur für Entwicklerkonten aktiviert, die von OEMs unterstützt werden.

## <a name="important-preinstall-policy--limitations"></a>Wichtige Vorinstallationsrichtlinien und -beschränkungen


Vorinstallations-Apps müssen über das Windows Dev Center zertifiziert sein, um die aktuelle Store-Lizenz zu erhalten. Es ist nicht möglich, eine Verbindung mit dem Store herzustellen und App-Updates herunterzuladen.

Jede bereits vorinstallierte App muss zum aktuellen Zeitpunkt und in Zukunft auf allen Märkten kostenlos angeboten werden.

## <a name="generating-preinstall-packages"></a>Generieren von Vorinstallationspaketen


Nachdem ein Konto mit Vorinstallationsberechtigungen aktiviert wurde, führen Sie die folgenden Schritte aus:

1.  Navigieren Sie in Ihrem Dashboard zur App, die vorinstalliert werden soll.
2.  Erweitern Sie im linken Navigationsmenü **App-Verwaltung**, und klicken Sie dann auf **Aktuelle Pakete**.
3.  Klicken Sie im Abschnitt **Pakete für die Vorinstallation des Betriebssystems anfordern** auf **Downloadbare Pakete ermöglichen**.
4.  Es wird ein Bestätigungsdialogfeld mit dem Hinweis angezeigt, dass Apps, die auf Betriebssystemen vor Windows 10 vorinstalliert sind, kostenlos sein müssen. Wählen Sie **Aktivieren** aus.
5.  Suchen Sie das Paket, das Sie herunterladen möchten, und klicken Sie auf den entsprechenden Link **Paket generieren**.
    > **Hinweis**  Die für das Generieren von Vorinstallationspaketen benötigte Zeit ist von der Größe des ausgewählten Pakets abhängig. Sie können diese Seite verlassen und später zurückkehren oder die Seite geöffnet lassen.
6.  Nachdem das Paket generiert wurde, wird ein Link zu **Paket herunterladen** angezeigt. Klicken Sie auf diesen Link, um die ZIP-Datei herunterzuladen.

Die ZIP-Datei kann dem OEM zur Verfügung gestellt werden, damit er sie in sein Betriebssystemimage einschließt.

## <a name="support"></a>Support


Falls Sie weitere Fragen zum Generieren von Vorinstallationspaketen haben, senden Sie eine E-Mail an <partnerops@microsoft.com>.

 

 





