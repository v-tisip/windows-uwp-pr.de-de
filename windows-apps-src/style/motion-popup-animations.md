---
author: mijacobs
Description: "Verwenden Sie Popupanimationen, um Popup-UI-Elemente für Flyouts oder benutzerdefinierte Popup-UI-Elemente anzuzeigen und auszublenden. Popupelemente sind Container, die über dem Inhalt der App angezeigt werden und ausgeblendet werden, wenn Benutzer außerhalb des Popupelements tippen oder klicken."
title: "Animationen für Popupbenutzeroberflächen in UWP-Apps"
ms.assetid: 4E9025CE-FC90-4d4c-9DE6-EC6B6F2AD9DF
label: Motion--Pop-up animations
template: detail.hbs
translationtype: Human Translation
ms.sourcegitcommit: a3924fef520d7ba70873d6838f8e194e5fc96c62
ms.openlocfilehash: cb5d70784e758b4e18092b75df9e0d77243af7fc

---

# <a name="pop-up-ui-animations"></a>Animationen für Popupbenutzeroberflächen

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

Verwenden Sie Popupanimationen, um Popup-UI-Elemente für Flyouts oder benutzerdefinierte Popup-UI-Elemente anzuzeigen und auszublenden. Popupelemente sind Container, die über dem Inhalt der App angezeigt werden und ausgeblendet werden, wenn Benutzer außerhalb des Popupelements tippen oder klicken.

<div class="important-apis" >
<b>Wichtige APIs</b><br/>
<ul>
<li>[**PopInThemeAnimation-Klasse**](https://msdn.microsoft.com/library/windows/apps/br210383)</li>
<li>[**PopupThemeTransition-Klasse**](https://msdn.microsoft.com/library/windows/apps/hh969172)</li>
</ul>
</div>


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

 

 







<!--HONumber=Dec16_HO2-->


