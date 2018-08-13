---
author: payzer
title: Deaktivieren des Mausmodus
description: Anleitungen zum Deaktivieren des Standardmausmodus
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.assetid: e57ee4e6-7807-4943-a933-c2b4dc80fc01
ms.openlocfilehash: 980779b110523ceecf608b5077cb8446fb9a1e2b
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: MT
ms.contentlocale: de-DE
ms.locfileid: "234945"
---
# <a name="how-to-disable-mouse-mode"></a>Deaktivieren des Mausmodus
Der Mausmodus ist standardmäßig für alle Anwendungen aktiviert. Das bedeutet, dass alle Anwendungen, für die die Option nicht deaktiviert wurde, einen Mauszeiger erhalten (ähnlich dem Zeiger im Edge-Browser auf der Konsole). Es wird nachdrücklich empfohlen, diese Option zu deaktivieren und die direktionale Navigation über den Controller zu optimieren.   
   
## <a name="html"></a>HTML   
Um die direktionale Navigation über den Controller in einer JavaScript-UWP-App (Universelle Windows-Plattform) zu aktivieren, verwenden Sie die JavaScript-Bibliothek [TVHelpers für die direktionale Navigation](https://github.com/Microsoft/TVHelpers/wiki/Using-DirectionalNavigation). Fügen Sie die JavaScript-Datei für die direktionale Navigation in Ihr App-Paket ein, und fügen Sie einen Verweis auf diese in allen HTML-Seiten ein, die eine direktionale Navigation über den Controller erfordern:

```code
<script src="directionalnavigation-1.0.0.0.js"></script>
```
Weitere Informationen finden Sie im [Wiki für direktionale Navigation](https://github.com/Microsoft/TVHelpers/wiki/Using-DirectionalNavigation).

Wenn Sie stattdessen den Mausmodus deaktivieren und die DOM- oder WinRT-Gamepad-APIs direkt verwenden möchten, führen Sie folgende Schritte für jede Seite aus, für die dies erforderlich ist: 
   
```code
navigator.gamepadInputEmulation = "gamepad";
```   

   Diese Eigenschaft ist standardmäßig auf `mouse` festgelegt, wodurch der Mausmodus aktiviert wird. Wenn Sie diese auf `keyboard` festlegen, wird der Mausmodus deaktiviert, und Gamepad-Eingaben generieren DOM-Tastaturereignisse. Wenn Sie diese auf `gamepad` festlegen, wird der Mausmodus deaktiviert, und es werden keine DOM-Tastaturereignisse generiert. Auf diese Weise können Sie nur die DOM- oder WinRT-Gamepad-APIs verwenden.

## <a name="xaml"></a>XAML    
Um den Mausmodus zu deaktivieren, fügen Sie dem Konstruktor für Ihre App Folgendes hinzu:   
   
```code
public App() {
        this.InitializeComponent();
        this.RequiresPointerMode = Windows.UI.Xaml.ApplicationRequiresPointerMode.WhenRequested;
        this.Suspending += OnSuspending;
}
```

## <a name="cdirectx"></a>C++/DirectX   
Wenn Sie eine C++-/DirectX-App schreiben, müssen Sie keine Schritte ausführen. Der Mausmodus gilt nur für HTML- und XAML-Anwendungen.

## <a name="see-also"></a>Weitere Informationen
- [Bewährte Methoden für Xbox](tailoring-for-xbox.md)
- [UWP auf XboxOne](index.md)

