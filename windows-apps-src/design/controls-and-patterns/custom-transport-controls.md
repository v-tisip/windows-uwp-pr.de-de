---
Description: The media player has customizable XAML transport controls to manage control of audio and video content.
title: Erstellen benutzerdefinierter Medientransportsteuerelemente
ms.assetid: 6643A108-A6EB-42BC-B800-22EABD7B731B
label: Create custom media transport controls
template: detail.hbs
ms.date: 05/19/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 4960f6eb18fe4cffe34b8167a328521e9038c684
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8930731"
---
# <a name="create-custom-transport-controls"></a><span data-ttu-id="a5e4c-103">Erstellen benutzerdefinierter Transportsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="a5e4c-103">Create custom transport controls</span></span>



<span data-ttu-id="a5e4c-104">MediaPlayerElement verfügt über anpassbare XAML-Transportsteuerelemente, um die Steuerung von Audio-und Videoinhalten innerhalb einer universellen Windows-Platform (UWP)-App zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-104">MediaPlayerElement has customizable XAML transport controls to manage control of audio and video content within a Universal Windows Platform (UWP) app.</span></span> <span data-ttu-id="a5e4c-105">Hier wird gezeigt, wie Sie die MediaTransportControls-Vorlage anpassen.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-105">Here, we demonstrate how to customize the MediaTransportControls template.</span></span> <span data-ttu-id="a5e4c-106">Wir zeigen Ihnen, wie Sie das Überlaufmenü verwenden, eine benutzerdefinierte Schaltfläche hinzufügen und den Schieberegler bearbeiten können.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-106">We’ll show you how to work with the overflow menu, add a custom button and modify the slider.</span></span>

> <span data-ttu-id="a5e4c-107">**Wichtige APIs:** [MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx), [MediaPlayerElement.AreTransportControlsEnabled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aretransportcontrolsenabled.aspx), [MediaTransportControls](https://msdn.microsoft.com/library/windows/apps/dn278677)</span><span class="sxs-lookup"><span data-stu-id="a5e4c-107">**Important APIs**: [MediaPlayerElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx), [MediaPlayerElement.AreTransportControlsEnabled](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aretransportcontrolsenabled.aspx), [MediaTransportControls](https://msdn.microsoft.com/library/windows/apps/dn278677)</span></span>

<span data-ttu-id="a5e4c-108">Bevor Sie beginnen, sollten Sie mit den Klassen „MediaPlayerElement“ und „MediaTransportControls“ vertraut sein.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-108">Before starting, you should be familiar with the MediaPlayerElement and the MediaTransportControls classes.</span></span> <span data-ttu-id="a5e4c-109">Weitere Informationen finden Sie im Leitfaden für das MediaPlayerElement-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-109">For more info, see the MediaPlayerElement control guide.</span></span>

> [!TIP]
> <span data-ttu-id="a5e4c-110">Die Beispiele in diesem Thema basieren auf dem [Beispiel für die Steuerelemente für den Medientransport](http://go.microsoft.com/fwlink/p/?LinkId=620023).</span><span class="sxs-lookup"><span data-stu-id="a5e4c-110">The examples in this topic are based on the [Media Transport Controls sample](http://go.microsoft.com/fwlink/p/?LinkId=620023).</span></span> <span data-ttu-id="a5e4c-111">Sie können das Beispiel herunterladen, um den fertigen Code anzuzeigen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-111">You can download the sample to view and run the completed code.</span></span>

> [!NOTE]
> <span data-ttu-id="a5e4c-112">**MediaPlayerElement** steht erst ab Windows10 Version1607 zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-112">**MediaPlayerElement** is only available in Windows 10, version 1607 and up.</span></span> <span data-ttu-id="a5e4c-113">Für das Entwickeln von Apps für niedrigere Windows10-Versionen muss stattdessen [**MediaElement**](https://msdn.microsoft.com/library/windows/apps/br242926) verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-113">If you are developing an app for an earlier version of Windows 10 you will need to use [**MediaElement**](https://msdn.microsoft.com/library/windows/apps/br242926) instead.</span></span> <span data-ttu-id="a5e4c-114">Alle Beispiele auf dieser Seite funktionieren auch mit **MediaElement**.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-114">All of the examples on this page work with **MediaElement** as well.</span></span>

## <a name="when-should-you-customize-the-template"></a><span data-ttu-id="a5e4c-115">Wann sollte die Vorlage angepasst werden?</span><span class="sxs-lookup"><span data-stu-id="a5e4c-115">When should you customize the template?</span></span>

<span data-ttu-id="a5e4c-116">**MediaPlayerElement** verfügt über integrierte Transportsteuerelemente, die so konzipiert sind, dass sie standardmäßig mit den meisten Apps für die Video- und Audiowiedergabe verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-116">**MediaPlayerElement** has built-in transport controls that are designed to work well without modification in most video and audio playback apps.</span></span> <span data-ttu-id="a5e4c-117">Sie werden von der [**MediaTransportControls**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.mediatransportcontrols.aspx)-Klasse bereitgestellt und enthalten Schaltflächen zum Wiedergeben und Beenden von sowie zum Navigieren in Medien, zum Einstellen der Lautstärke, zum Aktivieren/Deaktivieren des Vollbildmodus, zum Übertragen auf ein Zweitgerät, zum Aktivieren von Untertiteln, zum Wechseln von Audiospuren und zum Anpassen der Wiedergaberate.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-117">They’re provided by the [**MediaTransportControls**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.mediatransportcontrols.aspx) class and include buttons to play, stop, and navigate media, adjust volume, toggle full screen, cast to a second device, enable captions, switch audio tracks, and adjust the playback rate.</span></span> <span data-ttu-id="a5e4c-118">MediaTransportControls verfügt über Eigenschaften, mit denen Sie steuern können, ob die einzelnen Schaltflächen angezeigt und aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-118">MediaTransportControls has properties that let you control whether each button is shown and enabled.</span></span> <span data-ttu-id="a5e4c-119">Sie können auch die [**IsCompact**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.mediatransportcontrols.iscompact.aspx)-Eigenschaft festlegen, um anzugeben, ob die Steuerelemente in einer Zeile oder in zwei Zeilen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-119">You can also set the [**IsCompact**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.mediatransportcontrols.iscompact.aspx) property to specify whether the controls are shown in one row or two.</span></span>

<span data-ttu-id="a5e4c-120">Allerdings gibt es möglicherweise Szenarien, in denen Sie das Erscheinungsbild des Steuerelements weiter anpassen oder sein Verhalten ändern müssen.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-120">However, there may be scenarios where you need to further customize the look of the control or change its behavior.</span></span> <span data-ttu-id="a5e4c-121">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="a5e4c-121">Here are some examples:</span></span>
- <span data-ttu-id="a5e4c-122">Ändern Sie die Symbole, das Schiebereglerverhalten und die Farben.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-122">Change the icons, slider behavior, and colors.</span></span>
- <span data-ttu-id="a5e4c-123">Verschieben Sie weniger häufig verwendete Befehlsschaltflächen in ein Überlaufmenü.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-123">Move less commonly used command buttons into an overflow menu.</span></span>
- <span data-ttu-id="a5e4c-124">Ändern Sie die Reihenfolge, in der Befehle wegfallen, wenn die Größe des Steuerelements geändert wird.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-124">Change the order in which commands drop out when the control is resized.</span></span>
- <span data-ttu-id="a5e4c-125">Stellen Sie eine Befehlsschaltfläche bereit, die nicht im Standardsatz enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-125">Provide a command button that’s not in the default set.</span></span>

> [!NOTE]
> <span data-ttu-id="a5e4c-126">Wenn auf dem Bildschirm nicht genügend Platz vorhanden ist, fallen die angezeigten Schaltflächen in einer vordefinierten Reihenfolge aus den integrierten Transportsteuerelementen weg.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-126">The buttons visible on screen will drop out of the built-in transport controls in a predefined order if there is not enough room on screen.</span></span> <span data-ttu-id="a5e4c-127">Um diese Reihenfolge zu ändern, oder um Befehle zu platzieren, die nicht in ein Überlaufmenü passen, müssen Sie die Steuerelemente anpassen.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-127">To change this ordering or put commands that don't fit into an overflow menu, you will need to customize the controls.</span></span>

<span data-ttu-id="a5e4c-128">Sie können die Darstellung des Steuerelements durch Ändern der Standardvorlage anpassen.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-128">You can customize the appearance of the control by modifying the default template.</span></span> <span data-ttu-id="a5e4c-129">Wenn Sie das Verhalten des Steuerelements ändern oder neue Befehle hinzufügen möchten, können Sie ein benutzerdefiniertes Steuerelement erstellen, das von MediaTransportControls abgeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-129">To modify the control's behavior or add new commands, you can create a custom control that's derived from MediaTransportControls.</span></span>

> [!TIP]
> <span data-ttu-id="a5e4c-130">Anpassbare Steuerelementvorlagen sind ein leistungsfähiges Feature der XAML-Plattform, aber bei ihrer Nutzung ergeben sich auch Konsequenzen, die Sie berücksichtigen sollten.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-130">Customizable control templates are a powerful feature of the XAML platform, but there are also consequences that you should take into consideration.</span></span> <span data-ttu-id="a5e4c-131">Wenn Sie eine Vorlage anpassen, wird sie zu einem statischen Teil Ihrer App und erhält daher keine Plattformupdates, die von Microsoft für die Vorlage durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-131">When you customize a template, it becomes a static part of your app and therefore will not receive any platform updates that are made to the template by Microsoft.</span></span> <span data-ttu-id="a5e4c-132">Wenn von Microsoft Vorlagenupdates herausgegeben werden, sollten Sie die neue Vorlage nutzen und erneut anpassen, um von den Vorteilen der aktualisierten Vorlage zu profitieren.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-132">If template updates are made by Microsoft, you should take the new template and re-modify it in order to get the benefits of the updated template.</span></span>

## <a name="template-structure"></a><span data-ttu-id="a5e4c-133">Vorlagenstruktur</span><span class="sxs-lookup"><span data-stu-id="a5e4c-133">Template structure</span></span>

<span data-ttu-id="a5e4c-134">Das [**ControlTemplate**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.controltemplate.aspx)-Element ist im Standardstil enthalten.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-134">The [**ControlTemplate**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.controltemplate.aspx) is part of the default style.</span></span> <span data-ttu-id="a5e4c-135">Der Standardstil des Transportsteuerelements wird in der [**MediaTransportControls**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.mediatransportcontrols.aspx)-Klassenreferenzseite angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-135">The transport control's default style is shown in the [**MediaTransportControls**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.mediatransportcontrols.aspx) class reference page.</span></span> <span data-ttu-id="a5e4c-136">Sie können diesen Standardstil in Ihr Projekt kopieren, um ihn zu ändern.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-136">You can copy this default style into your project to modify it.</span></span> <span data-ttu-id="a5e4c-137">Das ControlTemplate-Element ist in Abschnitte unterteilt, ähnlich wie andere XAML-Steuerelementvorlagen.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-137">The ControlTemplate is divided into sections similar to other XAML control templates.</span></span>
- <span data-ttu-id="a5e4c-138">Der erste Abschnitt der Vorlage enthält die [**Style**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.style.aspx)-Definitionen für die verschiedenen Komponenten von MediaTransportControls.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-138">The first section of the template contains the [**Style**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.style.aspx) definitions for the various components of the MediaTransportControls.</span></span>
- <span data-ttu-id="a5e4c-139">Im zweiten Abschnitt werden die verschiedenen visuellen Zustände definiert, die von MediaTransportControls verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-139">The second section defines the various visual states that are used by the MediaTransportControls.</span></span>
- <span data-ttu-id="a5e4c-140">Der dritte Abschnitt enthält das [**Grid**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.grid.aspx)-Element, in dem die verschiedenen MediaTransportControls-Elemente zusammengeführt werden und mit dem das Layout der Komponenten definiert wird.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-140">The third section contains the [**Grid**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.grid.aspx) that holds that various MediaTransportControls elements together and defines how the components are laid out.</span></span>

> [!NOTE]
> <span data-ttu-id="a5e4c-141">Weitere Informationen zum Ändern von Vorlagen finden Sie unter [Steuerelementvorlagen]().</span><span class="sxs-lookup"><span data-stu-id="a5e4c-141">For more info about modifying templates, see [Control templates]().</span></span> <span data-ttu-id="a5e4c-142">Sie können einen Text-Editor oder vergleichbare Editoren in Ihrer IDE verwenden, um die XAML-Dateien in \(*Programmdateien*)\Windows Kits\10\DesignTime\CommonConfiguration\Neutral\UAP\\(*SDK-Version*)\Generic zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-142">You can use a text editor or similar editors in your IDE to open the XAML files in \(*Program Files*)\Windows Kits\10\DesignTime\CommonConfiguration\Neutral\UAP\\(*SDK version*)\Generic.</span></span> <span data-ttu-id="a5e4c-143">Das Standardformat und die Vorlage für jedes Steuerelement werden in der Datei **generic.xaml** definiert.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-143">The default style and template for each control is defined in the **generic.xaml** file.</span></span> <span data-ttu-id="a5e4c-144">Sie finden die MediaTransportControls-Vorlage in generic.xaml, indem Sie nach „MediaTransportControls“ suchen.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-144">You can find the MediaTransportControls template in generic.xaml by searching for "MediaTransportControls".</span></span>

<span data-ttu-id="a5e4c-145">In den folgenden Abschnitten erfahren Sie, wie Sie einige der wichtigsten Elemente der Transportsteuerelemente anpassen:</span><span class="sxs-lookup"><span data-stu-id="a5e4c-145">In the following sections, you learn how to customize several of the main elements of the transport controls:</span></span>
- <span data-ttu-id="a5e4c-146">[**Slider**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.slider.aspx): ermöglicht Benutzern das Scrubbing durch ihre Medien und zeigt darüber hinaus den Fortschritt an.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-146">[**Slider**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.slider.aspx): allows a user to scrub through their media and also displays progress</span></span>
- <span data-ttu-id="a5e4c-147">[**CommandBar**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.commandbar.aspx): enthält alle Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-147">[**CommandBar**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.commandbar.aspx): contains all of the buttons.</span></span>
<span data-ttu-id="a5e4c-148">Weitere Informationen finden Sie im Abschnitt zum Aufbau des MediaTransportControls-Referenzthemas.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-148">For more info, see the Anatomy section of the MediaTransportControls reference topic.</span></span>

## <a name="customize-the-transport-controls"></a><span data-ttu-id="a5e4c-149">Anpassen der Transportsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="a5e4c-149">Customize the transport controls</span></span>

<span data-ttu-id="a5e4c-150">Wenn Sie nur die Darstellung von MediaTransportControls ändern möchten, können Sie einfach eine Kopie des standardmäßigen Steuerelementstils und der Vorlage erstellen und diese ändern.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-150">If you want to modify only the appearance of the MediaTransportControls, you can create a copy of the default control style and template, and modify that.</span></span> <span data-ttu-id="a5e4c-151">Wenn Sie jedoch auch die Funktionalität des Steuerelements erweitern oder ändern möchten, müssen Sie eine neue von MediaTransportControls abgeleitete Klasse erstellen.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-151">However, if you also want to add to or modify the functionality of the control, you need to create a new class that derives from MediaTransportControls.</span></span>

### <a name="re-template-the-control"></a><span data-ttu-id="a5e4c-152">Anpassen der Vorlage eines Steuerelements</span><span class="sxs-lookup"><span data-stu-id="a5e4c-152">Re-template the control</span></span>

**<span data-ttu-id="a5e4c-153">So passen Sie den MediaTransportControls-Standardstil und die Standardvorlage an</span><span class="sxs-lookup"><span data-stu-id="a5e4c-153">To customize the MediaTransportControls default style and template</span></span>**
1. <span data-ttu-id="a5e4c-154">Kopieren Sie den Standardstil aus den MediaTransportControls-Stilen und-Vorlagen in ein ResourceDictionary in Ihrem Projekt.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-154">Copy the default style from MediaTransportControls styles and templates into a ResourceDictionary in your project.</span></span>
2. <span data-ttu-id="a5e4c-155">Weisen Sie dem Style einen x:Key-Wert zu, um ihn zu identifizieren, wie hier gezeigt.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-155">Give the Style an x:Key value to identify it, like this.</span></span>

```xaml
<Style TargetType="MediaTransportControls" x:Key="myTransportControlsStyle">
    <!-- Style content ... -->
</Style>
```

3. <span data-ttu-id="a5e4c-156">Fügen Sie Ihrer Benutzeroberfläche ein MediaPlayerElement mit MediaTransportControls hinzu.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-156">Add a MediaPlayerElement with MediaTransportControls to your UI.</span></span>
4. <span data-ttu-id="a5e4c-157">Legen Sie die Style-Eigenschaft des MediaTransportControls-Element auf Ihre benutzerdefinierte Style-Ressource fest, wie hier gezeigt.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-157">Set the Style property of the MediaTransportControls element to your custom Style resource, as shown here.</span></span>

```xaml
<MediaPlayerElement AreTransportControlsEnabled="True">
    <MediaPlayerElement.TransportControls>
        <MediaTransportControls Style="{StaticResource myTransportControlsStyle}"/>
    </MediaPlayerElement.TransportControls>
</MediaPlayerElement>
```

<span data-ttu-id="a5e4c-158">Weitere Informationen zum Ändern von Stilen und Vorlagen finden Sie unter [Formatieren von Steuerelementen]() und [Steuerelementvorlagen]().</span><span class="sxs-lookup"><span data-stu-id="a5e4c-158">For more info about modifying styles and templates, see [Styling controls]() and [Control templates]().</span></span>

### <a name="create-a-derived-control"></a><span data-ttu-id="a5e4c-159">Erstellen eines abgeleiteten Steuerelements</span><span class="sxs-lookup"><span data-stu-id="a5e4c-159">Create a derived control</span></span>

<span data-ttu-id="a5e4c-160">Wenn Sie die Funktionalität der Transportsteuerelemente erweitern oder ändern möchten, müssen Sie eine neue von MediaTransportControls abgeleitete Klasse erstellen.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-160">To add to or modify the functionality of the transport controls, you must create a new class that's derived from MediaTransportControls.</span></span> <span data-ttu-id="a5e4c-161">Eine abgeleitete Klasse namens `CustomMediaTransportControls` wird im [Beispiel für die Steuerelemente für den Medientransport](http://go.microsoft.com/fwlink/p/?LinkId=620023) und den übrigen Beispielen auf dieser Seite gezeigt.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-161">A derived class called `CustomMediaTransportControls` is shown in the [Media Transport Controls sample](http://go.microsoft.com/fwlink/p/?LinkId=620023) and the remaining examples on this page.</span></span>

**<span data-ttu-id="a5e4c-162">So erstellen Sie eine neue Klasse, die von MediaTransportControls abgeleitet ist</span><span class="sxs-lookup"><span data-stu-id="a5e4c-162">To create a new class derived from MediaTransportControls</span></span>**
1. <span data-ttu-id="a5e4c-163">Fügen Sie Ihrem Projekt eine neue Klassendatei hinzu.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-163">Add a new class file to your project.</span></span>
    - <span data-ttu-id="a5e4c-164">Wählen Sie in Visual Studio Projekt > Klasse hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-164">In Visual Studio, select Project > Add Class.</span></span> <span data-ttu-id="a5e4c-165">Das Dialogfeld Neues Element hinzufügen wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-165">The Add New Item dialog opens.</span></span>
    - <span data-ttu-id="a5e4c-166">Geben Sie im Dialogfeld „Neues Element hinzufügen“ einen Namen für die Klassendatei ein, und klicken Sie dann auf „Hinzufügen“.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-166">In the Add New Item dialog, enter a name for the class file, then click Add.</span></span> <span data-ttu-id="a5e4c-167">(Im Beispiel für die Medientransportsteuerelemente hat die Klasse den Namen `CustomMediaTransportControls`.)</span><span class="sxs-lookup"><span data-stu-id="a5e4c-167">(In the Media Transport Controls sample, the class is named `CustomMediaTransportControls`.)</span></span>
2. <span data-ttu-id="a5e4c-168">Ändern Sie den Klassencode, um die Ableitung von der MediaTransportControls-Klasse auszuführen.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-168">Modify the class code to derive from the MediaTransportControls class.</span></span>

```csharp
public sealed class CustomMediaTransportControls : MediaTransportControls
{
}
```

3. <span data-ttu-id="a5e4c-169">Kopieren Sie den Standardstil für [**MediaTransportControls**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.mediatransportcontrols.aspx) in einen [ResourceDictionary](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.resourcedictionary.aspx) in Ihrem Projekt.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-169">Copy the default style for [**MediaTransportControls**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.mediatransportcontrols.aspx) into a [ResourceDictionary](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.resourcedictionary.aspx) in your project.</span></span> <span data-ttu-id="a5e4c-170">Dies sind der Stil und die Vorlage, die Sie ändern.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-170">This is the style and template you modify.</span></span>
<span data-ttu-id="a5e4c-171">(Im Beispiel für die Medientransportsteuerelemente wird ein neuer Ordner mit dem Namen „Themes“ erstellt, dem eine ResourceDictionary-Datei mit dem Namen generic.xaml hinzugefügt wird.)</span><span class="sxs-lookup"><span data-stu-id="a5e4c-171">(In the Media Transport Controls sample, a new folder called "Themes" is created, and a ResourceDictionary file called generic.xaml is added to it.)</span></span>
4. <span data-ttu-id="a5e4c-172">Ändern Sie den [**TargetType**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.style.targettype.aspx) des Stils in den Typ des neuen benutzerdefinierten Steuerelements.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-172">Change the [**TargetType**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.style.targettype.aspx) of the style to the new custom control type.</span></span> <span data-ttu-id="a5e4c-173">(Im Beispiel wird der TargetType in `local:CustomMediaTransportControls`geändert.)</span><span class="sxs-lookup"><span data-stu-id="a5e4c-173">(In the sample, the TargetType is changed to `local:CustomMediaTransportControls`.)</span></span>

```xaml
xmlns:local="using:CustomMediaTransportControls">
...
<Style TargetType="local:CustomMediaTransportControls">
```

5. <span data-ttu-id="a5e4c-174">Legen Sie den [**DefaultStyleKey**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.control.defaultstylekey.aspx) Ihrer benutzerdefinierten Klasse fest.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-174">Set the [**DefaultStyleKey**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.control.defaultstylekey.aspx) of your custom class.</span></span> <span data-ttu-id="a5e4c-175">Dies weist die benutzerdefinierte Klasse an, einen Style mit dem TargetType `local:CustomMediaTransportControls` zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-175">This tells your custom class to use a Style with a TargetType of `local:CustomMediaTransportControls`.</span></span>

```csharp
public sealed class CustomMediaTransportControls : MediaTransportControls
{
    public CustomMediaTransportControls()
    {
        this.DefaultStyleKey = typeof(CustomMediaTransportControls);
    }
}
```

6. <span data-ttu-id="a5e4c-176">Fügen Sie dem XAML-Markup ein [**MediaPlayerElement**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx) hinzu, und fügen Sie diesem die benutzerdefinierten Transportsteuerelemente hinzu.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-176">Add a [**MediaPlayerElement**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx) to your XAML markup and add the custom transport controls to it.</span></span> <span data-ttu-id="a5e4c-177">Beachten Sie, dass die APIs zum Ausblenden, Anzeigen, Deaktivieren und Aktivieren der Standardschaltflächen mit einer angepassten Vorlage weiterhin funktionieren.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-177">One thing to note is that the APIs to hide, show, disable, and enable the default buttons still work with a customized template.</span></span>

```xaml
<MediaPlayerElement Name="MediaPlayerElement1" AreTransportControlsEnabled="True" Source="video.mp4">
    <MediaPlayerElement.TransportControls>
        <local:CustomMediaTransportControls x:Name="customMTC"
                                            IsFastForwardButtonVisible="True"
                                            IsFastForwardEnabled="True"
                                            IsFastRewindButtonVisible="True"
                                            IsFastRewindEnabled="True"
                                            IsPlaybackRateButtonVisible="True"
                                            IsPlaybackRateEnabled="True"
                                            IsCompact="False">
        </local:CustomMediaTransportControls>
    </MediaPlayerElement.TransportControls>
</MediaPlayerElement>
```

<span data-ttu-id="a5e4c-178">Sie können nun den Steuerelementstil und die -vorlage ändern, um das Erscheinungsbild des benutzerdefiniertes Steuerelements zu aktualisieren, und den Steuerelementcodes ändern, um das Verhalten zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-178">You can now modify the control style and template to update the look of your custom control, and the control code to update its behavior.</span></span>

### <a name="working-with-the-overflow-menu"></a><span data-ttu-id="a5e4c-179">Verwenden des Überlaufmenüs</span><span class="sxs-lookup"><span data-stu-id="a5e4c-179">Working with the overflow menu</span></span>

<span data-ttu-id="a5e4c-180">Sie können MediaTransportControls-Befehlsschaltflächen in ein Überlaufmenü verschieben, sodass weniger häufig verwendete Befehle ausgeblendet werden, bis der Benutzer diese benötigt.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-180">You can move MediaTransportControls command buttons into an overflow menu, so that less commonly used commands are hidden until the user needs them.</span></span>

<span data-ttu-id="a5e4c-181">In der MediaTransportControls-Vorlage sind die Befehlsschaltflächen in einem [**CommandBar**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.commandbar.aspx)-Element enthalten.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-181">In the MediaTransportControls template, the command buttons are contained in a [**CommandBar**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.commandbar.aspx) element.</span></span> <span data-ttu-id="a5e4c-182">Das Konzept der Befehlsleiste basiert auf primären und sekundären Befehlen.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-182">The command bar has the concept of primary and secondary commands.</span></span> <span data-ttu-id="a5e4c-183">Die primären Befehle sind die Schaltflächen, die standardmäßig im Steuerelement angezeigt werden und stets sichtbar sind (es sei denn, Sie deaktivieren die Schaltfläche oder blenden sie aus, oder es ist nicht ausreichend Platz vorhanden).</span><span class="sxs-lookup"><span data-stu-id="a5e4c-183">The primary commands are the buttons that appear in the control by default and are always visible (unless you disable the button, hide the button or there is not enough room).</span></span> <span data-ttu-id="a5e4c-184">Die sekundären Befehle sind in einem Überlaufmenü enthalten, das angezeigt wird, wenn ein Benutzer auf die Schaltfläche mit den Auslassungspunkten (...) klickt.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-184">The secondary commands are shown in an overflow menu that appears when a user clicks the ellipsis (…) button.</span></span> <span data-ttu-id="a5e4c-185">Weitere Informationen finden Sie im Artikel [App-Leisten und Befehlsleisten](app-bars.md).</span><span class="sxs-lookup"><span data-stu-id="a5e4c-185">For more info, see the [App bars and command bars](app-bars.md) article.</span></span>

<span data-ttu-id="a5e4c-186">Um ein Element aus den primären Befehlsleistenbefehlen in das Überlaufmenü zu verschieben, müssen Sie die XAML-Steuerelementvorlage bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-186">To move an element from the command bar primary commands to the overflow menu, you need to edit the XAML control template.</span></span>

**<span data-ttu-id="a5e4c-187">So verschieben Sie einen Befehl in das Überlaufmenü</span><span class="sxs-lookup"><span data-stu-id="a5e4c-187">To move a command to the overflow menu:</span></span>**
1. <span data-ttu-id="a5e4c-188">Suchen Sie in der Steuerelementvorlage das CommandBar-Element namens `MediaControlsCommandBar`.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-188">In the control template, find the CommandBar element named `MediaControlsCommandBar`.</span></span>
2. <span data-ttu-id="a5e4c-189">Fügen Sie dem XAML-Code für CommandBar einen [**SecondaryCommands**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.commandbar.secondarycommands.aspx)-Abschnitt hinzu.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-189">Add a [**SecondaryCommands**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.commandbar.secondarycommands.aspx) section to the XAML for the CommandBar.</span></span> <span data-ttu-id="a5e4c-190">Platzieren Sie diesen nach dem schließenden Tag für das [**PrimaryCommands**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.commandbar.primarycommands.aspx)-Element.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-190">Put it after the closing tag for the [**PrimaryCommands**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.commandbar.primarycommands.aspx).</span></span>

```xaml
<CommandBar x:Name="MediaControlsCommandBar" ... >  
  <CommandBar.PrimaryCommands>
...
    <AppBarButton x:Name='PlaybackRateButton'
                    Style='{StaticResource AppBarButtonStyle}'
                    MediaTransportControlsHelper.DropoutOrder='4'
                    Visibility='Collapsed'>
      <AppBarButton.Icon>
        <FontIcon Glyph="&#xEC57;"/>
      </AppBarButton.Icon>
    </AppBarButton>
...
  </CommandBar.PrimaryCommands>
<!-- Add secondary commands (overflow menu) here -->
  <CommandBar.SecondaryCommands>
    ...
  </CommandBar.SecondaryCommands>
</CommandBar>
```

3. <span data-ttu-id="a5e4c-191">Um das Menü mit Befehlen zu füllen, schneiden Sie den XAML-Code für die gewünschten [**AppBarButton**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarbutton.aspx)-Objekte aus dem PrimaryCommands-Element aus, und fügen Sie ihn in das SecondaryCommands-Element ein.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-191">To populate the menu with commands, cut and paste the XAML for the desired [**AppBarButton**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarbutton.aspx) objects from the PrimaryCommands to the SecondaryCommands.</span></span> <span data-ttu-id="a5e4c-192">In diesem Beispiel wird das `PlaybackRateButton`-Element in das Überlaufmenü verschoben.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-192">In this example, we move the `PlaybackRateButton` to the overflow menu.</span></span>

4. <span data-ttu-id="a5e4c-193">Fügen Sie der Schaltfläche eine Beschriftung hinzu, und entfernen Sie die Formatierungsinformationen, wie hier gezeigt.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-193">Add a label to the button and remove the styling information, as shown here.</span></span>
<span data-ttu-id="a5e4c-194">Da das Überlaufmenü aus Textschaltflächen besteht, müssen Sie der Schaltfläche eine Textbeschriftung hinzufügen und außerdem den Stil entfernen, der die Höhe und Breite der Schaltfläche festgelegt.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-194">Because the overflow menu is comprised of text buttons, you must add a text label to the button and also remove the style that sets the height and width of the button.</span></span> <span data-ttu-id="a5e4c-195">Andernfalls wird sie nicht richtig im Überlaufmenü angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-195">Otherwise, it won't appear correctly in the overflow menu.</span></span>

```xaml
<CommandBar.SecondaryCommands>
    <AppBarButton x:Name='PlaybackRateButton'
                  Label='Playback Rate'>
    </AppBarButton>
</CommandBar.SecondaryCommands>
```

> [!IMPORTANT]
> <span data-ttu-id="a5e4c-196">Außerdem müssen Sie die Schaltfläche sichtbar machen und aktivieren, damit sie im Überlaufmenü verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-196">You must still make the button visible and enable it in order to use it in the overflow menu.</span></span> <span data-ttu-id="a5e4c-197">In diesem Beispiel ist das PlaybackRateButton-Element nicht im Überlaufmenü sichtbar, es sei denn, die IsPlaybackRateButtonVisible-Eigenschaft ist auf „true“ festgelegt.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-197">In this example, the PlaybackRateButton element isn't visible in the overflow menu unless the IsPlaybackRateButtonVisible property is true.</span></span> <span data-ttu-id="a5e4c-198">Es ist nicht aktiviert, es sei denn, die IsPlaybackRateEnabled-Eigenschaft ist auf „true“ festgelegt.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-198">It's not enabled unless the IsPlaybackRateEnabled property is true.</span></span> <span data-ttu-id="a5e4c-199">Das Festlegen dieser Eigenschaften wird im vorherigen Abschnitt erläutert.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-199">Setting these properties is shown in the previous section.</span></span>

### <a name="adding-a-custom-button"></a><span data-ttu-id="a5e4c-200">Hinzufügen einer benutzerdefinierten Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="a5e4c-200">Adding a custom button</span></span>

<span data-ttu-id="a5e4c-201">Das Anpassen von MediaTransportControls kann beispielsweise erforderlich sein, wenn Sie dem Steuerelement einen benutzerdefinierten Befehl hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-201">One reason you might want to customize MediaTransportControls is to add a custom command to the control.</span></span> <span data-ttu-id="a5e4c-202">Unabhängig davon, ob Sie ihn als primären oder sekundären Befehl hinzufügen, sind die Verfahren zum Erstellen der Befehlsschaltfläche und zum Ändern des Verhaltens gleich.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-202">Whether you add it as a primary command or a secondary command, the procedure for creating the command button and modifying its behavior is the same.</span></span> <span data-ttu-id="a5e4c-203">Im [Beispiel für die Medientransportsteuerelemente](http://go.microsoft.com/fwlink/p/?LinkId=620023) wird den primären Befehlen eine Bewertungsschaltfläche hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-203">In the [Media Transport Controls sample](http://go.microsoft.com/fwlink/p/?LinkId=620023), a "rating" button is added to the primary commands.</span></span>

**<span data-ttu-id="a5e4c-204">So fügen Sie eine benutzerdefinierte Befehlsschaltfläche hinzu</span><span class="sxs-lookup"><span data-stu-id="a5e4c-204">To add a custom command button</span></span>**
1. <span data-ttu-id="a5e4c-205">Erstellen Sie ein AppBarButton-Objekt, und fügen Sie es dem CommandBar-Element in der Steuerelementvorlage hinzu.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-205">Create an AppBarButton object and add it to the CommandBar in the control template.</span></span>

```xaml
<AppBarButton x:Name="LikeButton"
              Icon="Like"
              Style="{StaticResource AppBarButtonStyle}"
              MediaTransportControlsHelper.DropoutOrder="3"
              VerticalAlignment="Center" />
```

    You must add it to the CommandBar in the appropriate location. (For more info, see the Working with the overflow menu section.) How it's positioned in the UI is determined by where the button is in the markup. For example, if you want this button to appear as the last element in the primary commands, add it at the very end of the primary commands list.

    You can also customize the icon for the button. For more info, see the [**AppBarButton**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.appbarbutton.aspx) reference.

2. <span data-ttu-id="a5e4c-206">Rufen Sie in der [**OnApplyTemplate**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.frameworkelement.onapplytemplate.aspx)-Überschreibung die Schaltfläche aus der Vorlage ab, und registrieren Sie einen Handler für das dazugehörige [**Click**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.primitives.buttonbase.click.aspx)-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-206">In the [**OnApplyTemplate**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.frameworkelement.onapplytemplate.aspx) override, get the button from the template and register a handler for its [**Click**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.primitives.buttonbase.click.aspx) event.</span></span> <span data-ttu-id="a5e4c-207">Dieser Code wird in die `CustomMediaTransportControls`-Klasse eingefügt.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-207">This code goes in the `CustomMediaTransportControls` class.</span></span>

```csharp
public sealed class CustomMediaTransportControls :  MediaTransportControls
{
    // ...

    protected override void OnApplyTemplate()
    {
        // Find the custom button and create an event handler for its Click event.
        var likeButton = GetTemplateChild("LikeButton") as Button;
        likeButton.Click += LikeButton_Click;
        base.OnApplyTemplate();
    }

    //...
}
```

3. <span data-ttu-id="a5e4c-208">Fügen Sie dem Click-Ereignishandler Code hinzu, um die Aktion auszuführen, die beim Klicken auf die Schaltfläche ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-208">Add code to the Click event handler to perform the action that occurs when the button is clicked.</span></span>
<span data-ttu-id="a5e4c-209">Dies ist der vollständige Code für die Klasse.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-209">Here's the complete code for the class.</span></span>

```csharp
public sealed class CustomMediaTransportControls : MediaTransportControls
{
    public event EventHandler< EventArgs> Liked;

    public CustomMediaTransportControls()
    {
        this.DefaultStyleKey = typeof(CustomMediaTransportControls);
    }

    protected override void OnApplyTemplate()
    {
        // Find the custom button and create an event handler for its Click event.
        var likeButton = GetTemplateChild("LikeButton") as Button;
        likeButton.Click += LikeButton_Click;
        base.OnApplyTemplate();
    }

    private void LikeButton_Click(object sender, RoutedEventArgs e)
    {
        // Raise an event on the custom control when 'like' is clicked.
        var handler = Liked;
        if (handler != null)
        {
            handler(this, EventArgs.Empty);
        }
    }
}
```

<span data-ttu-id="a5e4c-210">**Benutzerdefinierte Medientransport-Steuerelemente mit hinzugefügter „Gefällt mir“-Schaltfläche**
![Benutzerdefiniertes Medientransport-Steuerelement mit zusätzlicher „Gefällt mir“-Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="a5e4c-210">**Custom media transport controls with a "Like" button added**
![Custom media transport control with additional like button</span></span>](images/controls/mtc_double_custom_inprod.png)

### <a name="modifying-the-slider"></a><span data-ttu-id="a5e4c-211">Ändern des Schiebereglers</span><span class="sxs-lookup"><span data-stu-id="a5e4c-211">Modifying the slider</span></span>

<span data-ttu-id="a5e4c-212">Das „seek“-Steuerelement von MediaTransportControls wird durch ein [**Slider**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.slider.aspx)-Element bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-212">The "seek" control of the MediaTransportControls is provided by a [**Slider**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.slider.aspx) element.</span></span> <span data-ttu-id="a5e4c-213">Eine Möglichkeit zum Anpassen besteht darin, die Granularität des Suchverhaltens zu ändern.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-213">One way you can customize it is to change the granularity of the seek behavior.</span></span>

<span data-ttu-id="a5e4c-214">Der standardmäßige Suchschieberegler ist in 100Segmente unterteilt, sodass das Suchverhalten auf diese Anzahl von Abschnitten begrenzt ist.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-214">The default seek slider is divided into 100 parts, so the seek behavior is limited to that many sections.</span></span> <span data-ttu-id="a5e4c-215">Sie können die Granularität des Suchschiebereglers ändern, indem Sie das Slider-Element aus der visuellen XAML-Struktur in Ihrem [**MediaOpened**](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplayer.mediaopened.aspx)-Ereignishandler für [**MediaPlayerElement.MediaPlayer**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx) abrufen.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-215">You can change the granularity of the seek slider by getting the Slider from the XAML visual tree in your [**MediaOpened**](https://msdn.microsoft.com/library/windows/apps/windows.media.playback.mediaplayer.mediaopened.aspx) event handler on [**MediaPlayerElement.MediaPlayer**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.mediaplayerelement.aspx).</span></span> <span data-ttu-id="a5e4c-216">In diesem Beispiel wird gezeigt, wie Sie mithilfe von [**VisualTreeHelper**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.media.visualtreehelper.aspx) einen Verweis auf das Slider-Element abrufen, dann das Standardschrittintervall des Schiebereglers von 1% in 0,1% (1.000Schritte) ändern, wenn das Medium länger als 120Minuten ist.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-216">This example shows how to use [**VisualTreeHelper**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.media.visualtreehelper.aspx) to get a reference to the Slider, then change the default step frequency of the slider from 1% to 0.1% (1000 steps) if the media is longer than 120 minutes.</span></span> <span data-ttu-id="a5e4c-217">Das MediaPlayerElement hat den Namen `MediaPlayerElement1`.</span><span class="sxs-lookup"><span data-stu-id="a5e4c-217">The MediaPlayerElement is named `MediaPlayerElement1`.</span></span>

```csharp
protected override void OnNavigatedTo(NavigationEventArgs e)
{
  MediaPlayerElement1.MediaPlayer.MediaOpened += MediaPlayerElement_MediaPlayer_MediaOpened;
  base.OnNavigatedTo(e);
}

private void MediaPlayerElement_MediaPlayer_MediaOpened(object sender, RoutedEventArgs e)
{
  FrameworkElement transportControlsTemplateRoot = (FrameworkElement)VisualTreeHelper.GetChild(MediaPlayerElement1.TransportControls, 0);
  Slider sliderControl = (Slider)transportControlsTemplateRoot.FindName("ProgressSlider");
  if (sliderControl != null && MediaPlayerElement1.NaturalDuration.TimeSpan.TotalMinutes > 120)
  {
    // Default is 1%. Change to 0.1% for more granular seeking.
    sliderControl.StepFrequency = 0.1;
  }
}
```
## <a name="related-articles"></a><span data-ttu-id="a5e4c-218">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="a5e4c-218">Related articles</span></span>

- [<span data-ttu-id="a5e4c-219">Medienwiedergabe</span><span class="sxs-lookup"><span data-stu-id="a5e4c-219">Media playback</span></span>](media-playback.md)
