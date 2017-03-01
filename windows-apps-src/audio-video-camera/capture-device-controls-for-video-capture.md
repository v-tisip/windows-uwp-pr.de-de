---
author: drewbatgit
ms.assetid: 708170E1-777A-4E4A-9F77-5AB28B88B107
description: "In diesem Artikel wird beschrieben, wie Sie manuelle Gerätesteuerelemente verwenden, um erweiterte Videoaufnahmeszenarien, z. B. HDR-Video und Belichtungspriorität, zu ermöglichen."
title: "Manuelle Kamerasteuerelemente für die Videoaufnahme"
ms.author: drewbat
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP"
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: cd6326ebad94c33fd03bf39f2dfd11f1c27e9b37
ms.lasthandoff: 02/07/2017

---

# <a name="manual-camera-controls-for-video-capture"></a>Manuelle Kamerasteuerelemente für die Videoaufnahme

\[ Aktualisiert für UWP-Apps unter Windows 10. Artikel zu Windows 8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \].


In diesem Artikel wird beschrieben, wie Sie manuelle Gerätesteuerelemente verwenden, um erweiterte Videoaufnahmeszenarien, z. B. HDR-Video und Belichtungspriorität, zu ermöglichen.

Die in diesem Artikel beschriebenen Steuerelemente des Videoaufnahmegeräts werden Ihrer App alle mithilfe desselben Musters hinzugefügt. Überprüfen Sie zunächst, ob das Steuerelement auf dem aktuellen Gerät unterstützt wird, auf dem Ihre App ausgeführt wird. Wenn das Steuerelement unterstützt wird, legen Sie den gewünschten Modus für das Steuerelement fest. Wenn ein bestimmtes Steuerelement auf dem aktuellen Gerät nicht unterstützt wird, sollten Sie das UI-Element, über das der Benutzer das Feature aktivieren kann, deaktivieren oder ausblenden.

Alle in diesem Artikel beschriebenen Gerätesteuerelement-APIs gehören dem [**Windows.Media.Devices**](https://msdn.microsoft.com/library/windows/apps/br206902)-Namespace an.

[!code-cs[VideoControllersUsing](./code/BasicMediaCaptureWin10/cs/MainPage.xaml.cs#SnippetVideoControllersUsing)]

> [!NOTE] 
> Dieser Artikel baut auf Konzepten und Codebeispielen auf, die unter [Allgemeine Foto-, Video- und Audioaufnahme mit „MediaCapture“](basic-photo-video-and-audio-capture-with-MediaCapture.md) erläutert werden. Dort werden die Schritte für die Implementierung einer grundlegenden Foto- und Videoaufnahme beschrieben. Wir empfehlen Ihnen, sich mit dem grundlegenden Medienaufnahmemuster in diesem Artikel vertraut zu machen, bevor Sie sich komplexeren Aufnahmeszenarien zuwenden. Bei dem Code in diesem Artikel wird davon ausgegangen, dass Ihre App bereits eine Instanz von MediaCapture aufweist, die ordnungsgemäß initialisiert wurde.

## <a name="hdr-video"></a>HDR-Video

Die Videofunktion „High Dynamic Range“ (HDR) bezieht sich auf die HDR-Verarbeitung des Videostreams des Aufnahmegeräts. Ermitteln Sie, ob HDR-Video unterstützt wird, indem Sie die [**HdrVideoControl.Supported**](https://msdn.microsoft.com/library/windows/apps/dn926682)-Eigenschaft auswählen.

Das HDR-Videosteuerelement unterstützt drei Modi: ein, aus und automatisch. Dies bedeutet, dass das Gerät dynamisch ermittelt, ob die Medienaufnahme durch die HDR-Videoverarbeitung verbessert wird, und HDR-Video aktiviert, wenn dies der Fall ist. Um festzustellen, ob ein bestimmter Modus auf dem aktuellen Gerät unterstützt wird, überprüfen Sie, ob die [**HdrVideoControl.SupportedModes**](https://msdn.microsoft.com/library/windows/apps/dn926683)-Auflistung den gewünschten Modus enthält.

Aktivieren oder deaktivieren Sie die HDR-Videoverarbeitung, in dem Sie [**HdrVideoControl.Mode**](https://msdn.microsoft.com/library/windows/apps/dn926681) auf den gewünschten Modus festlegen.

[!code-cs[SetHdrVideoMode](./code/BasicMediaCaptureWin10/cs/MainPage.xaml.cs#SnippetSetHdrVideoMode)]

## <a name="exposure-priority"></a>Belichtungspriorität

Wenn [**ExposurePriorityVideoControl**](https://msdn.microsoft.com/library/windows/apps/dn926644) aktiviert ist, werden die Videoframes des Aufnahmegeräts ausgewertet, um zu bestimmen, ob in dem Video ein Motiv unter schlechten Lichtverhältnissen aufgenommen wird. Wenn dies der Fall ist, verringert das Steuerelement die Bildfrequenz des aufgenommenen Videos, um die Belichtungszeit für jeden Frame zu erhöhen und die visuelle Qualität des aufgenommenen Videos zu verbessern.

Ermitteln Sie, ob das Steuerelement für die Belichtungspriorität auf dem aktuellen Gerät unterstützt wird, indem Sie die [**ExposurePriorityVideoControl.Supported**](https://msdn.microsoft.com/library/windows/apps/dn926647)-Eigenschaft überprüfen.

Aktivieren oder deaktivieren Sie das Steuerelement für die Belichtungspriorität, indem Sie [**ExposurePriorityVideoControl.Enabled**](https://msdn.microsoft.com/library/windows/apps/dn926646) auf den gewünschten Modus festlegen.

[!code-cs[EnableExposurePriority](./code/BasicMediaCaptureWin10/cs/MainPage.xaml.cs#SnippetEnableExposurePriority)]

## <a name="related-topics"></a>Verwandte Themen

* [Kamera](camera.md)
* [Allgemeine Foto-, Video- und Audioaufnahme mit „MediaCapture“](basic-photo-video-and-audio-capture-with-MediaCapture.md)
 

 





