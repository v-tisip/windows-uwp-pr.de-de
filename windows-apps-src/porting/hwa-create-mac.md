---
author: seksenov
title: "Gehostete Web Apps – Konvertieren Ihrer Webanwendung in eine Windows-App mithilfe eines Mac-Computers"
description: "Verwenden Sie einen Mac-Computer, um Ihre Website in eine Universelle Windows-Plattform (UWP)-App für Windows 10 zu konvertieren."
kw: Hosted Web Apps with a Mac, Porting to Windows 10 with a Mac, Convert website to Windows with Mac, Packaging web application with ManfoldJS for Windows Store, Add website to Windows Store with App Studio
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Gehostete Web-Apps mit einem Mac, Portieren zu Windows 10 mit einem Mac, Website in Windows umwandeln mit Mac, Website für Windows Store, Manifold JS für Web-Apps, App Studio für Web-Apps"
ms.assetid: a4cea1e8-4417-4488-b0e7-45c704dc53e9
translationtype: Human Translation
ms.sourcegitcommit: 5645eee3dc2ef67b5263b08800b0f96eb8a0a7da
ms.openlocfilehash: 464097cc3f90c2e84e03e936fb354f4220aff91d
ms.lasthandoff: 02/08/2017

---

# <a name="create-your-hosted-web-app-using-a-mac"></a>Erstellen einer gehosteten Web-App mithilfe eines Mac-Computers

Erstellen Sie einfach aus einer Website-URL eine Windows 10-App für die Universelle Windows-Plattform. 

> [!NOTE]
> Die folgenden Anweisungen gelten für die Verwendung mit einer Mac-Entwicklungsplattform. Windows-Benutzer sollten sich in den [Anweisungen zur Verwendung einer Windows-Entwicklungsplattform](./hwa-create-windows.md) informieren.

## <a name="what-you-need-to-develop-on-mac"></a>Voraussetzungen für die Entwicklung auf einem Mac-Computer

- Ein Webbrowser.
- Eine Eingabeaufforderung.

## <a name="option-1-manifoldjs"></a>Option 1: ManifoldJS

[ManifoldJS](http://manifoldjs.com/) ist eine Node.js-App, die problemlos über NPM installiert werden kann. Sie verwendet die Metadaten über Ihre Website und generiert systemeigene gehostete Apps für Android, iOS und Windows. Wenn Ihre Website kein [Web-App-Manifest](https://www.w3.org/TR/appmanifest/) besitzt, wird ein Manifest automatisch für Sie generiert.

1. Installieren Sie [NodeJS](https://nodejs.org/), das NPM (Node Package Manager) enthält. <br>

2. Öffnen Sie eine Eingabeaufforderung, und die NPM-Installation von ManifoldJS:
```
npm install -g manifoldjs
```

3. Führen Sie den Befehl `manifoldjs` auf Ihrer Website-URL aus:
```
manifoldjs http://codepen.io/seksenov/pen/wBbVyb/?editors=101
```

4. Befolgen Sie die im Video unten angezeigten Schritte aus, um die Verpackung durchzuführen und Ihre gehostete Web-App im Windows Store zu veröffentlichen.

[![Veröffentlichen einer UWP-Web-App auf einem Mac-Computer mit ManifoldJS](images/hwa-to-uwp/mac_manifoldjs_video.png)](https://sec.ch9.ms/ch9/0a67/9b06e5c7-d7aa-478d-b30d-f99e145a0a67/ManifoldJS_high.mp4 "Veröffentlichen einer UWP-Web-App auf einem Mac-Computer mit ManifoldJS")

## <a name="option-2-app-studio"></a>Option 2: App Studio

[App Studio](http://appstudio.windows.com/) ist ein kostenloses Onlinetool, mit dem Sie Windows 10-Apps rasch erstellen können.

1. Öffnen Sie [App Studio](http://appstudio.windows.com/) in Ihrem Webbrowser.

2. Klicken Sie auf **Start now!** (Jetzt starten).

3. Klicken Sie in **Web app templates** (Vorlagen für Web-Apps) auf **Hosted Web App** (Gehostete Web App).

4. Befolgen Sie die Anweisungen auf dem Bildschirm, um ein Paket zu generieren, das Sie im Windows Store veröffentlichen können.

## <a name="related-topics"></a>Verwandte Themen

- [Optimieren Ihrer Web-App durch den Zugriff auf Features für die Universelle Windows-Plattform (UWP)](./hwa-access-features.md)
- [Anleitung für Apps für die Universelle Windows-Plattform (UWP)](http://go.microsoft.com/fwlink/p/?LinkID=397871)
- [Herunterladen von Designressourcen für Windows Store-Apps](https://msdn.microsoft.com/library/windows/apps/xaml/bg125377.aspx)

