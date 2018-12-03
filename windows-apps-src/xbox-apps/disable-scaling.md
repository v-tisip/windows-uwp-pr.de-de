---
title: So deaktivieren Sie die Skalierung
description: Anleitung zum Deaktivieren des Standard-Skalierungsfaktors.
ms.date: 02/08/2017
ms.topic: article
keywords: windows 10, uwp
ms.assetid: 6e68c1fc-a407-4c0b-b0f4-e445ccb72ff3
ms.localizationpriority: medium
ms.openlocfilehash: 44688ff40792ba2ee72cbd1d96bae1ac59834efa
ms.sourcegitcommit: b4c502d69a13340f6e3c887aa3c26ef2aeee9cee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "8464757"
---
# <a name="how-to-turn-off-scaling"></a>So deaktivieren Sie die Skalierung   
Standardmäßig werden Anwendungen für XAML-Apps auf 200Prozent und für HTML-Apps auf 150Prozent skaliert. Der Standardskalierungsfaktor kann deaktiviert werden. Infolgedessen verwendet die Anwendung die tatsächlichen Pixelabmessungen des Geräts (1910 x 1080Pixel).   
   
## <a name="html"></a>HTML   
Sie können den Skalierungsfaktor deaktivieren, indem Sie den folgenden Codeausschnitt verwenden: 
   
```
var result = Windows.UI.ViewManagement.ApplicationViewScaling.trySetDisableLayoutScaling(true);
```

Oder Sie können eine für das Web geeignete Methode verwenden:   

```   
@media (max-height: 1080px) {   
    @-ms-viewport {   
        height: 1080px;   
    }   
}   
```

## <a name="xaml"></a>XAML
Sie können den Skalierungsfaktor deaktivieren, indem Sie den folgenden Codeausschnitt verwenden:   
   
```
bool result = Windows.UI.ViewManagement.ApplicationViewScaling.TrySetDisableLayoutScaling(true);
```
   
## <a name="directxc"></a>DirectX/C++   
DirectX-/C++-Anwendungen werden nicht skaliert. Die automatische Skalierung gilt nur für HTML- und XAML-Anwendungen.  

## <a name="see-also"></a>Weitere Informationen
- [Bewährte Methoden für Xbox](tailoring-for-xbox.md)
- [UWP auf XboxOne](index.md)
