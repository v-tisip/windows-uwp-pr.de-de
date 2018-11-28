---
ms.assetid: c43d4af3-9a1a-4eae-a137-1267c293c1b5
description: Dieser Artikel beschreibt, wie Sie spezielle Kamera-UI-Features nutzen, die nur auf mobilen Geräten vorhanden sind.
title: Kamera-UI-Features für mobile Geräte
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 1bf27de9c9b1bce2b35918b2a9d1357d2f3ba20b
ms.sourcegitcommit: b5c9c18e70625ab770946b8243f3465ee1013184
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "7967074"
---
#<a name="camera-ui-features-for-mobile-devices"></a><span data-ttu-id="5590c-104">Kamera-UI-Features für mobile Geräte</span><span class="sxs-lookup"><span data-stu-id="5590c-104">Camera UI features for mobile devices</span></span>

<span data-ttu-id="5590c-105">Dieser Artikel beschreibt, wie Sie spezielle Kamera-UI-Features nutzen, die nur auf mobilen Geräten vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="5590c-105">This article show you how to take advantage of special camera UI features that are only present on mobile devices.</span></span> 

## <a name="add-the-mobile-extension-to-your-project"></a><span data-ttu-id="5590c-106">Hinzufügen der mobilen Erweiterung zu Ihrem Projekt</span><span class="sxs-lookup"><span data-stu-id="5590c-106">Add the mobile extension to your project</span></span> 

<span data-ttu-id="5590c-107">Um diese Features zu verwenden, müssen Sie einen Verweis auf das Microsoft Mobile Extension SDK für die Universelle App-Plattform zu Ihrem Projekt hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="5590c-107">To use these features, you must add a reference to the Microsoft Mobile Extension SDK for Universal App Platform to your project.</span></span>

**<span data-ttu-id="5590c-108">So fügen Sie einen Verweis auf das mobile Erweiterungs-SDK für die Unterstützung einer Hardwaretaste an der Kamera hinzu</span><span class="sxs-lookup"><span data-stu-id="5590c-108">To add a reference to the mobile extension SDK for hardware camera button support</span></span>**

1.  <span data-ttu-id="5590c-109">Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Verweise**, und wählen Sie **Verweis hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="5590c-109">In **Solution Explorer**, right-click **References** and select **Add Reference**.</span></span>

2.  <span data-ttu-id="5590c-110">Erweitern Sie den Knoten für die **universelle Windows-App**, und wählen Sie **Erweiterungen** aus.</span><span class="sxs-lookup"><span data-stu-id="5590c-110">Expand the **Windows Universal** node and select **Extensions**.</span></span>

3.  <span data-ttu-id="5590c-111">Aktivieren Sie das Kontrollkästchen **Microsoft Mobile Extension SDK für Universelle App-Plattform**.</span><span class="sxs-lookup"><span data-stu-id="5590c-111">Select the **Microsoft Mobile Extension SDK for Universal App Platform** check box.</span></span>

## <a name="hide-the-status-bar"></a><span data-ttu-id="5590c-112">Ausblenden der Statusleiste</span><span class="sxs-lookup"><span data-stu-id="5590c-112">Hide the status bar</span></span>

<span data-ttu-id="5590c-113">Mobile Geräte verfügen über ein [**StatusBar**](https://msdn.microsoft.com/library/windows/apps/dn633864)-Steuerelement, das dem Benutzer Statusinformationen zum Gerät liefert.</span><span class="sxs-lookup"><span data-stu-id="5590c-113">Mobile devices have a [**StatusBar**](https://msdn.microsoft.com/library/windows/apps/dn633864) control that provides the user with status information about the device.</span></span> <span data-ttu-id="5590c-114">Dieses Steuerelement benötigt Speicherplatz auf dem Bildschirm, der die Medienaufnahme-UI beeinträchtigen kann.</span><span class="sxs-lookup"><span data-stu-id="5590c-114">This control takes up space on the screen that can interfere with the media capture UI.</span></span> <span data-ttu-id="5590c-115">Sie können die Statusleiste ausblenden, indem Sie [**HideAsync**](https://msdn.microsoft.com/library/windows/apps/dn610339) aufrufen. Dieser Aufruf muss jedoch innerhalb eines Bedingungsblocks ausgeführt werden, in dem Sie die [**ApiInformation.IsTypePresent**](https://msdn.microsoft.com/library/windows/apps/dn949016)-Methode verwenden, um festzustellen, ob die API verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="5590c-115">You can hide the status bar by calling [**HideAsync**](https://msdn.microsoft.com/library/windows/apps/dn610339), but you must make this call from within a conditional block where you use the [**ApiInformation.IsTypePresent**](https://msdn.microsoft.com/library/windows/apps/dn949016) method to determine if the API is available.</span></span> <span data-ttu-id="5590c-116">Diese Methode gibt nur „true“ auf mobilen Geräten zurück, die die Statusleiste unterstützen.</span><span class="sxs-lookup"><span data-stu-id="5590c-116">This method will only return true on mobile devices that support the status bar.</span></span> <span data-ttu-id="5590c-117">Sie sollten die Statusleiste ausblenden, wenn die App gestartet wird oder wenn Sie die Vorschau von der Kamera beginnen.</span><span class="sxs-lookup"><span data-stu-id="5590c-117">You should hide the status bar when your app launches or when you begin previewing from the camera.</span></span>

[!code-cs[HideStatusBar](./code/BasicMediaCaptureWin10/cs/MainPage.xaml.cs#SnippetHideStatusBar)]

<span data-ttu-id="5590c-118">Wenn die App beendet wird oder der Benutzer die Medienaufnahmeseite der App verlässt, können Sie das Steuerelement wieder einblenden.</span><span class="sxs-lookup"><span data-stu-id="5590c-118">When your app is shutting down or when the user navigates away from the media capture page of your app, you can make the control visible again.</span></span>

[!code-cs[ShowStatusBar](./code/BasicMediaCaptureWin10/cs/MainPage.xaml.cs#SnippetShowStatusBar)]

## <a name="use-the-hardware-camera-button"></a><span data-ttu-id="5590c-119">Verwenden der Kamera-Hardwaretaste</span><span class="sxs-lookup"><span data-stu-id="5590c-119">Use the hardware camera button</span></span>

<span data-ttu-id="5590c-120">Einige mobile Geräte verfügen über eine dedizierte Kamera-Hardwaretaste, die einige Benutzer einem Steuerelement auf dem Bildschirm vorziehen.</span><span class="sxs-lookup"><span data-stu-id="5590c-120">Some mobile devices have a dedicated hardware camera button that some users prefer over an on-screen control.</span></span> <span data-ttu-id="5590c-121">Um benachrichtigt zu werden, wenn die Hardwaretaste für die Kamera gedrückt wird, registrieren Sie einen Handler für das [**HardwareButtons.CameraPressed**](https://msdn.microsoft.com/library/windows/apps/dn653805)-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="5590c-121">To be notified when the hardware camera button is pressed, register a handler for the [**HardwareButtons.CameraPressed**](https://msdn.microsoft.com/library/windows/apps/dn653805) event.</span></span> <span data-ttu-id="5590c-122">Da diese API nur auf mobilen Geräten verfügbar ist, müssen Sie erneut **IsTypePresent** verwenden, um sicherzustellen, dass die API auf dem aktuellen Gerät unterstützt wird, bevor Sie versuchen, darauf zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="5590c-122">Because this API is available on mobile devices only, you must again use the **IsTypePresent** to make sure the API is supported on the current device before attempting to access it.</span></span>

[!code-cs[PhoneUsing](./code/BasicMediaCaptureWin10/cs/MainPage.xaml.cs#SnippetPhoneUsing)]

[!code-cs[RegisterCameraButtonHandler](./code/BasicMediaCaptureWin10/cs/MainPage.xaml.cs#SnippetRegisterCameraButtonHandler)]

<span data-ttu-id="5590c-123">Im Handler für das **CameraPressed**-Ereignis können Sie die Aufnahme eines Fotos initiieren.</span><span class="sxs-lookup"><span data-stu-id="5590c-123">In the handler for the **CameraPressed** event, you can initiate a photo capture.</span></span>

[!code-cs[CameraPressed](./code/BasicMediaCaptureWin10/cs/MainPage.xaml.cs#SnippetCameraPressed)]

<span data-ttu-id="5590c-124">Wenn die App heruntergefahren wird oder der Benutzer die Medienaufnahmeseite der App verlässt, heben Sie die Registrierung des Hardwaretastenhandlers auf.</span><span class="sxs-lookup"><span data-stu-id="5590c-124">When your app is shutting down or the user moves away from the media capture page of your app, unregister the hardware button handler.</span></span>

[!code-cs[UnregisterCameraButtonHandler](./code/BasicMediaCaptureWin10/cs/MainPage.xaml.cs#SnippetUnregisterCameraButtonHandler)]

## <a name="related-topics"></a><span data-ttu-id="5590c-125">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="5590c-125">Related topics</span></span>

* [<span data-ttu-id="5590c-126">Kamera</span><span class="sxs-lookup"><span data-stu-id="5590c-126">Camera</span></span>](camera.md)
* [<span data-ttu-id="5590c-127">Allgemeine Foto-, Video- und Audioaufnahme mit „MediaCapture“</span><span class="sxs-lookup"><span data-stu-id="5590c-127">Basic photo, video, and audio capture with MediaCapture</span></span>](basic-photo-video-and-audio-capture-with-MediaCapture.md)





