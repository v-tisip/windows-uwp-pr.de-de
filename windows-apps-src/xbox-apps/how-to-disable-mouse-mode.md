---
title: Deaktivieren des Mausmodus
description: Anleitungen zum Deaktivieren des Standardmausmodus
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.assetid: e57ee4e6-7807-4943-a933-c2b4dc80fc01
ms.localizationpriority: medium
ms.openlocfilehash: 1e4b8868f416494daf978d65d4a4ccde02d6ccf5
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7830460"
---
# <a name="how-to-disable-mouse-mode"></a><span data-ttu-id="12bbc-104">Deaktivieren des Mausmodus</span><span class="sxs-lookup"><span data-stu-id="12bbc-104">How to disable mouse mode</span></span>
<span data-ttu-id="12bbc-105">Der Mausmodus ist standardmäßig für alle Anwendungen aktiviert. Das bedeutet, dass alle Anwendungen, für die die Option nicht deaktiviert wurde, einen Mauszeiger erhalten (ähnlich dem Zeiger im Edge-Browser auf der Konsole).</span><span class="sxs-lookup"><span data-stu-id="12bbc-105">Mouse mode is on by default for all applications, which means that all applications that have not opted out will receive a mouse pointer (similar to the one in the Edge browser on the console).</span></span> <span data-ttu-id="12bbc-106">Es wird nachdrücklich empfohlen, diese Option zu deaktivieren und die direktionale Navigation über den Controller zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="12bbc-106">We strongly recommend that you turn this off and optimize for directional controller navigation.</span></span>   
   
## <a name="html"></a><span data-ttu-id="12bbc-107">HTML</span><span class="sxs-lookup"><span data-stu-id="12bbc-107">HTML</span></span>   
<span data-ttu-id="12bbc-108">Um die direktionale Navigation über den Controller in einer JavaScript-UWP-App (Universelle Windows-Plattform) zu aktivieren, verwenden Sie die JavaScript-Bibliothek [TVHelpers für die direktionale Navigation](https://github.com/Microsoft/TVHelpers/wiki/Using-DirectionalNavigation).</span><span class="sxs-lookup"><span data-stu-id="12bbc-108">To turn on directional controller navigation in a JavaScript Universal Windows Platform (UWP) app, use the [TVHelpers directional navigation](https://github.com/Microsoft/TVHelpers/wiki/Using-DirectionalNavigation) JavaScript library.</span></span> <span data-ttu-id="12bbc-109">Fügen Sie die JavaScript-Datei für die direktionale Navigation in Ihr App-Paket ein, und fügen Sie einen Verweis auf diese in allen HTML-Seiten ein, die eine direktionale Navigation über den Controller erfordern:</span><span class="sxs-lookup"><span data-stu-id="12bbc-109">Include the directional navigation JavaScript file in your app package, and add a reference to it in all of the HTML pages that require directional controller navigation:</span></span>

```code
<script src="directionalnavigation-1.0.0.0.js"></script>
```
<span data-ttu-id="12bbc-110">Weitere Informationen finden Sie im [Wiki für direktionale Navigation](https://github.com/Microsoft/TVHelpers/wiki/Using-DirectionalNavigation).</span><span class="sxs-lookup"><span data-stu-id="12bbc-110">For more details, see the [directional navigation wiki](https://github.com/Microsoft/TVHelpers/wiki/Using-DirectionalNavigation).</span></span>

<span data-ttu-id="12bbc-111">Wenn Sie stattdessen den Mausmodus deaktivieren und die DOM- oder WinRT-Gamepad-APIs direkt verwenden möchten, führen Sie folgende Schritte für jede Seite aus, für die dies erforderlich ist:</span><span class="sxs-lookup"><span data-stu-id="12bbc-111">If you instead want to turn off mouse mode and use the DOM or WinRT gamepad APIs directly, run the following for every page that requires it:</span></span> 
   
```code
navigator.gamepadInputEmulation = "gamepad";
```   

   <span data-ttu-id="12bbc-112">Diese Eigenschaft ist standardmäßig auf `mouse` festgelegt, wodurch der Mausmodus aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="12bbc-112">This property defaults to `mouse`, which enables mouse mode.</span></span> <span data-ttu-id="12bbc-113">Wenn Sie diese auf `keyboard` festlegen, wird der Mausmodus deaktiviert, und Gamepad-Eingaben generieren DOM-Tastaturereignisse.</span><span class="sxs-lookup"><span data-stu-id="12bbc-113">Setting it to `keyboard` turns off mouse mode, and instead gamepad input generates DOM keyboard events.</span></span> <span data-ttu-id="12bbc-114">Wenn Sie diese auf `gamepad` festlegen, wird der Mausmodus deaktiviert, und es werden keine DOM-Tastaturereignisse generiert. Auf diese Weise können Sie nur die DOM- oder WinRT-Gamepad-APIs verwenden.</span><span class="sxs-lookup"><span data-stu-id="12bbc-114">Setting it to `gamepad` turns off mouse mode and does not generate DOM keyboard events, and allows you to just use the DOM or WinRT gamepad APIs.</span></span>

## <a name="xaml"></a><span data-ttu-id="12bbc-115">XAML</span><span class="sxs-lookup"><span data-stu-id="12bbc-115">XAML</span></span>    
<span data-ttu-id="12bbc-116">Um den Mausmodus zu deaktivieren, fügen Sie dem Konstruktor für Ihre App Folgendes hinzu:</span><span class="sxs-lookup"><span data-stu-id="12bbc-116">To turn off mouse mode, add the following to the constructor for your app:</span></span>   
   
```code
public App() {
        this.InitializeComponent();
        this.RequiresPointerMode = Windows.UI.Xaml.ApplicationRequiresPointerMode.WhenRequested;
        this.Suspending += OnSuspending;
}
```

## <a name="cdirectx"></a><span data-ttu-id="12bbc-117">C++/DirectX</span><span class="sxs-lookup"><span data-stu-id="12bbc-117">C++/DirectX</span></span>   
<span data-ttu-id="12bbc-118">Wenn Sie eine C++-/DirectX-App schreiben, müssen Sie keine Schritte ausführen.</span><span class="sxs-lookup"><span data-stu-id="12bbc-118">If you are writing a C++/DirectX app, there's nothing to do.</span></span> <span data-ttu-id="12bbc-119">Der Mausmodus gilt nur für HTML- und XAML-Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="12bbc-119">Mouse mode only applies to HTML and XAML applications.</span></span>

## <a name="see-also"></a><span data-ttu-id="12bbc-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="12bbc-120">See also</span></span>
- [<span data-ttu-id="12bbc-121">Bewährte Methoden für Xbox</span><span class="sxs-lookup"><span data-stu-id="12bbc-121">Best practices for Xbox</span></span>](tailoring-for-xbox.md)
- [<span data-ttu-id="12bbc-122">UWP auf XboxOne</span><span class="sxs-lookup"><span data-stu-id="12bbc-122">UWP on Xbox One</span></span>](index.md)

