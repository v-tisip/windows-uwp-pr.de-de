---
author: jnHs
Description: If your developer account has been granted the appropriate permissions, you can generate and download preinstall packages so that an OEM can include your app in their OS image.
title: Generieren von Vorinstallationspaketen für OEMs
ms.assetid: AC3A45E8-7BBD-44E9-B2D3-B74B7C9B2BC9
ms.author: wdg-dev-content
ms.date: 06/19/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 8564d3dc7240bb556f3cb90c51165def9e2d4eba
ms.sourcegitcommit: d0e836dfc937ebf7dfa9c424620f93f3c8e0a7e8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5664996"
---
# <a name="generate-preinstall-packages-for-oems"></a>Generieren von Vorinstallationspaketen für OEMs

Wenn Ihrem Entwicklerkonto die entsprechenden Berechtigungen gewährt wurden, können Sie Vorinstallationspakete generieren und herunterladen, damit das OEM Ihre App in ein OS-Image einschließen kann. Vorinstallationsberechtigungen werden nur für Entwicklerkonten aktiviert, die von OEMs unterstützt werden.


## <a name="important-preinstall-policy--limitations"></a>Wichtige Vorinstallationsrichtlinien und -beschränkungen

Vorinstallations-Apps müssen über das Windows Dev Center zertifiziert sein, um die aktuelle Store-Lizenz zu erhalten. Es ist nicht möglich, eine Verbindung mit dem Store herzustellen und App-Updates herunterzuladen.

Jede vorinstallierte App muss zum aktuellen Zeitpunkt und in Zukunft auf allen Märkten kostenlos angeboten werden.


## <a name="generating-preinstall-packages"></a>Generieren von Vorinstallationspaketen

Nachdem ein Konto mit Vorinstallationsberechtigungen aktiviert wurde, führen Sie die folgenden Schritte aus:

1.  Navigieren Sie in Ihrem Dashboard zur App, die vorinstalliert werden soll.
2.  Erweitern Sie im linken Navigationsmenü **App-Verwaltung**, und wählen Sie **Aktuelle Pakete** aus.
3.  Wählen Sie im Abschnitt **Pakete für die Vorinstallation des Betriebssystems anfordern** **Downloadbare Pakete ermöglichen** aus.
4.  Wählen Sie im Bestätigungsdialogfeld **Aktivieren** aus.
5.  Suchen Sie das Paket, das Sie herunterladen möchten, und wählen Sie den entsprechenden Link **Paket generieren**.

    > [!NOTE]
    > Die Dauer zum Generieren von Vorinstallationspaketen hängt von der Größe des ausgewählten Pakets ab. Sie können diese Seite verlassen und später darauf zurückkehren, oder Sie können die Seite geöffnet lassen, während das Paket generiert wird.

6.  Nachdem das Paket generiert wurde, wird ein Link zu **Paket herunterladen** angezeigt. Wählen Sie das Link aus, um die ZIP-Datei herunterzuladen.

Die ZIP-Datei kann dem OEM zur Verfügung gestellt werden, damit er sie in sein Betriebssystemimage einschließt.


## <a name="support"></a>Support

Wenn Sie weitere Fragen zum Generieren von Vorinstallationspaketen haben, senden Sie eine E-Mail an <partnerops@microsoft.com>.

 

 




