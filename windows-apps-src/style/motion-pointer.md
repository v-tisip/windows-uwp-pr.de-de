---
author: mijacobs
Description: Verwenden Sie Zeigeranimationen, um Benutzern visuelles Feedback zu liefern, wenn diese auf ein Element tippen.
title: "Animationen für Zeigerklicks in UWP-Apps"
ms.assetid: EEB10A2C-629A-4705-8468-4D019D74DDFF
label: Motion--Pointer animations
template: detail.hbs
translationtype: Human Translation
ms.sourcegitcommit: a3924fef520d7ba70873d6838f8e194e5fc96c62
ms.openlocfilehash: c208b67829e2053302ec0cc7c6da013b89cee8b3

---

# <a name="pointer-click-animations"></a>Animationen für Zeigerklicks

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

Verwenden Sie Zeigeranimationen, um Benutzern visuelles Feedback zu liefern, wenn diese auf ein Element tippen. Bei der Animation für „Zeiger nach unten“ wird das gedrückte Element leicht verkleinert und geneigt. Sie wird wiedergegeben, wenn erstmalig auf ein Element getippt wird. Die Animation für „Zeiger nach oben“, mit der der ursprüngliche Zustand des Elements wiederhergestellt wird, wird beim Loslassen des Zeigers wiedergegeben.


<div class="important-apis" >
<b>Wichtige APIs</b><br/>
<ul>
<li>[**PointerUpThemeAnimation-Klasse**](https://msdn.microsoft.com/library/windows/apps/hh969168)</li>
<li>[**PointerDownThemeAnimation-Klasse**](https://msdn.microsoft.com/library/windows/apps/hh969164)</li>
</ul>
</div>


## <a name="dos-and-donts"></a>Empfohlene und nicht empfohlene Vorgehensweisen

-   Wenn Sie eine Animation für „Zeiger hoch“ verwenden, sollte die Animation ausgelöst werden, nachdem der Benutzer den Zeiger losgelassen hat. Auf diese Weise erhalten Benutzer umgehend Feedback, dass ihre Aktion erkannt wurde. Dies gilt auch, wenn die durch das Tippen ausgelöste Aktion (beispielsweise das Navigieren zu einer neuen Seite) langsamer reagiert.

## <a name="related-articles"></a>Verwandte Artikel

* [Übersicht über Animationen](https://msdn.microsoft.com/library/windows/apps/mt187350)
* [Animieren von Zeigerklicks](https://msdn.microsoft.com/library/windows/apps/xaml/jj649432)
* [Schnellstart: Animieren der Benutzeroberfläche mithilfe von Bibliotheksanimationen](https://msdn.microsoft.com/library/windows/apps/xaml/hh452703)
* [**PointerUpThemeAnimation-Klasse**](https://msdn.microsoft.com/library/windows/apps/hh969168)
* [**PointerDownThemeAnimation-Klasse**](https://msdn.microsoft.com/library/windows/apps/hh969164)

 

 







<!--HONumber=Dec16_HO2-->


