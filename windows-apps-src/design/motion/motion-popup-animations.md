---
author: mijacobs
Description: Use pop-up animations to show and hide pop-up UI for flyouts or custom pop-up UI elements. Pop-up elements are containers that appear over the app's content and are dismissed if the user taps or clicks outside of the pop-up element.
title: Animationen für Popupbenutzeroberflächen in UWP-Apps
ms.assetid: 4E9025CE-FC90-4d4c-9DE6-EC6B6F2AD9DF
label: Motion--Pop-up animations
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 1a304df30986c904f19cc2401c9a1fb468514f6f
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "5883545"
---
# <a name="pop-up-ui-animations"></a>Animationen für Popupbenutzeroberflächen



Verwenden Sie Popupanimationen, um Popup-UI-Elemente für Flyouts oder benutzerdefinierte Popup-UI-Elemente anzuzeigen und auszublenden. Popupelemente sind Container, die über dem Inhalt der App angezeigt werden und ausgeblendet werden, wenn Benutzer außerhalb des Popupelements tippen oder klicken.

> **Wichtige APIs**: [**PopInThemeAnimation class**](https://msdn.microsoft.com/library/windows/apps/br210383), [**PopupThemeTransition class**](https://msdn.microsoft.com/library/windows/apps/hh969172)


## <a name="dos-and-donts"></a>Empfohlene und nicht empfohlene Vorgehensweisen


-   Verwenden Sie Popupanimationen zum Anzeigen oder Ausblenden benutzerdefinierter Popup-UI-Elemente, die nicht Teil der eigentlichen App-Seite sind. In die von Windows bereitgestellten allgemeinen Steuerelemente sind diese Animationen bereits integriert.
-   Verwenden Sie Popupanimationen nicht für QuickInfos oder Dialogfelder.
-   Verwenden Sie Popupanimationen nicht zum Anzeigen oder Ausblenden von Benutzeroberflächen innerhalb des Hauptinhalts der App. Verwenden Sie Popupanimationen nur, um einen Popupcontainer anzuzeigen oder auszublenden, der über dem Hauptinhalt der App angezeigt wird.

## <a name="related-articles"></a>Verwandte Artikel

* [Übersicht über Animationen](https://msdn.microsoft.com/library/windows/apps/mt187350)
* [Animieren von Popupbenutzeroberflächen](https://msdn.microsoft.com/library/windows/apps/xaml/jj649433)
* [Schnellstart: Animieren der Benutzeroberfläche mithilfe von Bibliotheksanimationen](https://msdn.microsoft.com/library/windows/apps/xaml/hh452703)
* [**PopInThemeAnimation-Klasse**](https://msdn.microsoft.com/library/windows/apps/br210383)
* [**PopOutThemeAnimation-Klasse**](https://msdn.microsoft.com/library/windows/apps/br210391)
* [**PopupThemeTransition-Klasse**](https://msdn.microsoft.com/library/windows/apps/hh969172)

 

 




