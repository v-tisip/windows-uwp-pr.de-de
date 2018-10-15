---
author: Jwmsft
Description: You create the UI for your app by using controls such as buttons, text boxes, and combo boxes to display data and get user input. Here, we show you how to add controls to your app.
title: Einführung in Steuerelemente und Muster
ms.assetid: 64740BF2-CAA1-419E-85D1-42EE7E15F1A5
label: Intro to controls and patterns
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 6f8f86a6988e68e3ff8d2dfef32512633b3761fd
ms.sourcegitcommit: 106aec1e59ba41aae2ac00f909b81bf7121a6ef1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2018
ms.locfileid: "4613068"
---
# <a name="intro-to-controls-and-patterns"></a><span data-ttu-id="89dbe-103">Einführung in Steuerelemente und Muster</span><span class="sxs-lookup"><span data-stu-id="89dbe-103">Intro to controls and patterns</span></span>

<span data-ttu-id="89dbe-104">In der UWP-App-Entwicklung ist ein *Steuerelement* ein UI-Element, das Inhalte anzeigt oder Interaktionen ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="89dbe-104">In UWP app development, a *control* is a UI element that displays content or enables interaction.</span></span> <span data-ttu-id="89dbe-105">Sie erstellen die Benutzeroberfläche für Ihre App mit Steuerelementen wie Schaltflächen, Textfeldern und Kombinationsfeldern, um Daten anzuzeigen und Benutzereingaben zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="89dbe-105">You create the UI for your app by using controls such as buttons, text boxes, and combo boxes to display data and get user input.</span></span>

> <span data-ttu-id="89dbe-106">**Wichtige APIs:** [Namespace „Windows.UI.Xaml.Controls“](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.aspx)</span><span class="sxs-lookup"><span data-stu-id="89dbe-106">**Important APIs**: [Windows.UI.Xaml.Controls namespace](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.aspx)</span></span>

<span data-ttu-id="89dbe-107">Ein *Muster* ist eine Anleitung zum Ändern eines Steuerelements oder zum Kombinieren verschiedener Steuerelemente, um etwas Neues zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="89dbe-107">A *pattern* is a recipe for modifying a control or combining several controls to make something new.</span></span> <span data-ttu-id="89dbe-108">Das [Master/Details](master-details.md) -Musters ist z. B. eine Möglichkeit, dass Sie ein [SplitView](split-view.md) -Steuerelement für app-Navigation verwenden können.</span><span class="sxs-lookup"><span data-stu-id="89dbe-108">For example, the [master/details](master-details.md) pattern is a way that you can use a [SplitView](split-view.md) control for app navigation.</span></span> <span data-ttu-id="89dbe-109">Auf ähnliche Weise können Sie die Vorlage eines Steuerelements [NavigationView](navigationview.md) zum Implementieren des registerkartenmusters anpassen.</span><span class="sxs-lookup"><span data-stu-id="89dbe-109">Similarly, you can customize the template of a [NavigationView](navigationview.md) control to implement the tab pattern.</span></span>

<span data-ttu-id="89dbe-110">In vielen Fällen können Sie ein Steuerelement unverändert verwenden.</span><span class="sxs-lookup"><span data-stu-id="89dbe-110">In many cases, you can use a control as-is.</span></span> <span data-ttu-id="89dbe-111">XAML-Steuerelemente trennen jedoch die Funktion von der Struktur und Darstellung, sodass Sie diese über verschiedene Änderungsebenen an Ihre Bedürfnisse anpassen können.</span><span class="sxs-lookup"><span data-stu-id="89dbe-111">But XAML controls separate function from structure and appearance, so you can make various levels of modification to make them fit your needs.</span></span> <span data-ttu-id="89dbe-112">Im Abschnitt [Stil](../style/index.md) erfahren Sie, wie Sie mithilfe von [XAML-Formatvorlagen](xaml-styles.md) und [Steuerelementvorlagen](control-templates.md) Steuerelemente ändern.</span><span class="sxs-lookup"><span data-stu-id="89dbe-112">In the [Style](../style/index.md) section, you can learn how to use [XAML styles](xaml-styles.md) and [control templates](control-templates.md) to modify a control.</span></span>

<span data-ttu-id="89dbe-113">In diesem Abschnitt erhalten Sie Anleitungen zu jedem XAML-Steuerelement, das Sie zum Erstellen Ihrer App-UI verwenden können.</span><span class="sxs-lookup"><span data-stu-id="89dbe-113">In this section, we provide guidance for each of the XAML controls you can use to build your app UI.</span></span> <span data-ttu-id="89dbe-114">Zu Beginn wird in diesem Artikel beschrieben, wie Sie der App Steuerelemente hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="89dbe-114">To start, this article shows you how to add controls to your app.</span></span> <span data-ttu-id="89dbe-115">Es gibt drei wichtige Schritte zum Hinzufügen von Steuerelementen zur App:</span><span class="sxs-lookup"><span data-stu-id="89dbe-115">There are 3 key steps to using controls to your app:</span></span>

- <span data-ttu-id="89dbe-116">Fügen Sie Ihrer App-UI ein Steuerelement hinzu.</span><span class="sxs-lookup"><span data-stu-id="89dbe-116">Add a control to your app UI.</span></span>
- <span data-ttu-id="89dbe-117">Legen Sie Eigenschaften für das Steuerelement fest, z.B. Breite, Höhe und Vordergrundfarbe.</span><span class="sxs-lookup"><span data-stu-id="89dbe-117">Set properties on the control, such as width, height, or foreground color.</span></span>
- <span data-ttu-id="89dbe-118">Fügen Sie den Ereignishandlern des Steuerelements Code hinzu, damit sie eine Funktion haben.</span><span class="sxs-lookup"><span data-stu-id="89dbe-118">Add code to the control's event handlers so that it does something.</span></span> 

## <a name="add-a-control"></a><span data-ttu-id="89dbe-119">Hinzufügen eines Steuerelements</span><span class="sxs-lookup"><span data-stu-id="89dbe-119">Add a control</span></span>
<span data-ttu-id="89dbe-120">Es gibt mehrere Möglichkeiten, einer App ein Steuerelement hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="89dbe-120">You can add a control to an app in several ways:</span></span>
 
- <span data-ttu-id="89dbe-121">Verwenden Sie ein Entwicklungstool wie Blend für Visual Studio oder Microsoft Visual Studio Extensible Application Markup Language (XAML)-Designer.</span><span class="sxs-lookup"><span data-stu-id="89dbe-121">Use a design tool like Blend for Visual Studio or the Microsoft Visual Studio Extensible Application Markup Language (XAML) designer.</span></span> 
- <span data-ttu-id="89dbe-122">Fügen Sie das Steuerelement dem XAML-Markup im XAML-Editor in Visual Studio hinzu.</span><span class="sxs-lookup"><span data-stu-id="89dbe-122">Add the control to the XAML markup in the Visual Studio XAML editor.</span></span> 
- <span data-ttu-id="89dbe-123">Fügen Sie das Steuerelement im Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="89dbe-123">Add the control in code.</span></span> <span data-ttu-id="89dbe-124">Im Code hinzugefügte Steuerelemente sind bei der Ausführung der App, jedoch nicht im Visual Studio-XAML-Designer sichtbar.</span><span class="sxs-lookup"><span data-stu-id="89dbe-124">Controls that you add in code are visible when the app runs, but are not visible in the Visual Studio XAML designer.</span></span>

<span data-ttu-id="89dbe-125">Wenn Sie in Visual Studio Steuerelemente in Ihrer App hinzufügen und bearbeiten, können Sie viele Features des Programms wie die Toolbox, den XAML-Designer, den XAML-Editor und das Eigenschaftenfenster nutzen.</span><span class="sxs-lookup"><span data-stu-id="89dbe-125">In Visual Studio, when you add and manipulate controls in your app, you can use many of the program's features, including the Toolbox, XAML designer, XAML editor, and the Properties window.</span></span> 

<span data-ttu-id="89dbe-126">In der Toolbox von Visual Studio werden viele Steuerelemente angezeigt, die Sie in Ihrer App verwenden können.</span><span class="sxs-lookup"><span data-stu-id="89dbe-126">The Visual Studio Toolbox displays many of the controls that you can use in your app.</span></span> <span data-ttu-id="89dbe-127">Wenn Sie der App ein Steuerelement hinzufügen möchten, doppelklicken Sie in der Toolbox auf das gewünschte Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="89dbe-127">To add a control to your app, double-click it in the Toolbox.</span></span> <span data-ttu-id="89dbe-128">Wenn Sie beispielsweise auf das „TextBox“-Steuerelement doppelklicken, wird der XAML-Ansicht folgender XAML-Code hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="89dbe-128">For example, when you double-click the TextBox control, this XAML is added to the XAML view.</span></span> 

```xaml
<TextBox HorizontalAlignment="Left" Text="TextBox" VerticalAlignment="Top"/>
```

<span data-ttu-id="89dbe-129">Sie können das Steuerelement auch aus der Toolbox in den XAML-Designer ziehen.</span><span class="sxs-lookup"><span data-stu-id="89dbe-129">You can also drag the control from the Toolbox to the XAML designer.</span></span>

## <a name="set-the-name-of-a-control"></a><span data-ttu-id="89dbe-130">Festlegen des Namens eines Steuerelements</span><span class="sxs-lookup"><span data-stu-id="89dbe-130">Set the name of a control</span></span>

<span data-ttu-id="89dbe-131">Wenn Sie mit einem Steuerelement im Code arbeiten möchten, legen Sie das Attribut [x:Name](../../xaml-platform/x-name-attribute.md) fest und verweisen im Code anhand des Namens darauf.</span><span class="sxs-lookup"><span data-stu-id="89dbe-131">To work with a control in code, you set its [x:Name](../../xaml-platform/x-name-attribute.md) attribute and reference it by name in your code.</span></span> <span data-ttu-id="89dbe-132">Sie können den Namen im Eigenschaftenfenster von Visual Studio oder in XAML festlegen.</span><span class="sxs-lookup"><span data-stu-id="89dbe-132">You can set the name in the Visual Studio Properties window or in XAML.</span></span> <span data-ttu-id="89dbe-133">Hier wird veranschaulicht, wie Sie den Namen des derzeit ausgewählten Steuerelements über das Textfeld Name am oberen Rand des Eigenschaftenfensters festlegen.</span><span class="sxs-lookup"><span data-stu-id="89dbe-133">Here's how to set the name of the currently selected control by using the Name text box at the top of the Properties window.</span></span>

<span data-ttu-id="89dbe-134">So benennen Sie ein Steuerelement</span><span class="sxs-lookup"><span data-stu-id="89dbe-134">To name a control</span></span>
1. <span data-ttu-id="89dbe-135">Wählen Sie das zu benennende Element aus.</span><span class="sxs-lookup"><span data-stu-id="89dbe-135">Select the element to name.</span></span>
2. <span data-ttu-id="89dbe-136">Geben Sie im Eigenschaftenpanel einen Namen in das Textfeld Name ein.</span><span class="sxs-lookup"><span data-stu-id="89dbe-136">In the Properties panel, type a name into the Name text box.</span></span>
3. <span data-ttu-id="89dbe-137">Drücken Sie die EINGABETASTE, um den Namen zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="89dbe-137">Press Enter to commit the name.</span></span>

![Name-Eigenschaft im Visual Studio-Designer](images/add-controls-control-name-designer.png)

<span data-ttu-id="89dbe-139">Hier wird erläutert, wie Sie den Namen eines Steuerelements im XAML-Editor festlegen, indem Sie das x:Name-Attribut hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="89dbe-139">Here's how to set the name of a control in the XAML editor by adding the x:Name attribute.</span></span>

```xaml
<Button x:Name="Button1" Content="Button"/>
```

## <a name="set-the-control-properties"></a><span data-ttu-id="89dbe-140">Festlegen von Steuerelementeigenschaften</span><span class="sxs-lookup"><span data-stu-id="89dbe-140">Set the control properties</span></span> 

<span data-ttu-id="89dbe-141">Mithilfe von Eigenschaften geben Sie das Erscheinungsbild, den Inhalt sowie weitere Attribute von Steuerelementen an.</span><span class="sxs-lookup"><span data-stu-id="89dbe-141">You use properties to specify the appearance, content, and other attributes of controls.</span></span> <span data-ttu-id="89dbe-142">Wenn Sie ein Steuerelement mit einem Entwicklungstool hinzufügen, werden manche Eigenschaften, die Größe, Position und Inhalt steuern, möglicherweise von Visual Studio für Sie festgelegt.</span><span class="sxs-lookup"><span data-stu-id="89dbe-142">When you add a control using a design tool, some properties that control size, position, and content might be set for you by Visual Studio.</span></span> <span data-ttu-id="89dbe-143">Sie können einige Eigenschaften wie etwa die Breite, die Höhe oder den Rand ändern, indem Sie das Steuerelement in der Entwurfsansicht auswählen und bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="89dbe-143">You can change some properties, such as Width, Height or Margin, by selecting and manipulating the control in the Design view.</span></span> <span data-ttu-id="89dbe-144">In der Abbildung werden einige der in der Entwurfsansicht verfügbaren Größenanpassungstools veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="89dbe-144">This illustration shows some of the resizing tools available in Design view.</span></span> 

![Größenanpassungstools im Visual Studio-Designer](images/add-controls-resizing-designer.png)

<span data-ttu-id="89dbe-146">Sie können die Größe und die Position des Steuerelements auch automatisch festlegen lassen.</span><span class="sxs-lookup"><span data-stu-id="89dbe-146">You might want to let the control be sized and positioned automatically.</span></span> <span data-ttu-id="89dbe-147">In diesem Fall können Sie die von Visual Studio festgelegten Eigenschaften für Größe und Position zurücksetzen.</span><span class="sxs-lookup"><span data-stu-id="89dbe-147">In this case, you can reset the size and position properties that Visual Studio set for you.</span></span>

<span data-ttu-id="89dbe-148">Zurücksetzen einer Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="89dbe-148">To reset a property</span></span>
1. <span data-ttu-id="89dbe-149">Klicken Sie im Bereich Eigenschaften auf den Eigenschaftsmarker neben dem Eigenschaftswert.</span><span class="sxs-lookup"><span data-stu-id="89dbe-149">In the Properties panel, click the property marker next to the property value.</span></span> <span data-ttu-id="89dbe-150">Das Eigenschaftsmenü wird geöffnet.</span><span class="sxs-lookup"><span data-stu-id="89dbe-150">The property menu opens.</span></span>
2. <span data-ttu-id="89dbe-151">Klicken Sie im Eigenschaftsmenü auf „Zurücksetzen“.</span><span class="sxs-lookup"><span data-stu-id="89dbe-151">In the property menu, click Reset.</span></span>

![Option „Zurücksetzen“ im Visual Studio-Menü „Eigenschaften“](images/add-controls-property-reset.png)

<span data-ttu-id="89dbe-153">Sie können Steuerelementeigenschaften im Eigenschaftenfenster, in XAML oder im Code festlegen.</span><span class="sxs-lookup"><span data-stu-id="89dbe-153">You can set control properties in the Properties window, in XAML, or in code.</span></span> <span data-ttu-id="89dbe-154">Wenn Sie beispielsweise die Vordergrundfarbe einer Schaltfläche ändern möchten, legen Sie die „Foreground“-Eigenschaft des Steuerelements fest.</span><span class="sxs-lookup"><span data-stu-id="89dbe-154">For example, to change the foreground color for a Button, you set the control's Foreground property.</span></span> <span data-ttu-id="89dbe-155">In dieser Abbildung wird veranschaulicht, wie die „Foreground“-Eigenschaft mit dem Farbwähler im Eigenschaftenfenster festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="89dbe-155">This illustration shows how to set the Foreground property by using the color picker in the Properties window.</span></span> 

![Farbwähler im Visual Studio-Designer](images/add-controls-foreground-designer.png)

<span data-ttu-id="89dbe-157">Hier wird beschrieben, wie Sie die „Foreground“-Eigenschaft im XAML-Editor festlegen.</span><span class="sxs-lookup"><span data-stu-id="89dbe-157">Here's how to set the Foreground property in the XAML editor.</span></span> <span data-ttu-id="89dbe-158">Beachten Sie das Visual Studio IntelliSense-Fenster, in dem hilfreiche Informationen zur Syntax angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="89dbe-158">Notice the Visual Studio IntelliSense window that opens to help you with the syntax.</span></span> 

![IntelliSense in XAML Teil1](images/add-controls-foreground-xaml.png)

![IntelliSense in XAML Teil2](images/add-controls-foreground-xaml-2.png)

<span data-ttu-id="89dbe-161">Im Folgenden finden Sie den XAML-Code, der nach dem Festlegen der „Foreground“-Eigenschaft vorliegt.</span><span class="sxs-lookup"><span data-stu-id="89dbe-161">Here's the resulting XAML after you set the Foreground property.</span></span> 

```xaml
<Button x:Name="Button1" Content="Button" 
        HorizontalAlignment="Left" VerticalAlignment="Top"
        Foreground="Beige"/>
```

<span data-ttu-id="89dbe-162">An dieser Stelle wird beschrieben, wie die „Foreground“-Eigenschaft im Code festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="89dbe-162">Here's how to set the Foreground property in code.</span></span> 

```csharp
Button1.Foreground = new SolidColorBrush(Windows.UI.Colors.Beige);
```

## <a name="create-an-event-handler"></a><span data-ttu-id="89dbe-163">Erstellen eines Ereignishandlers</span><span class="sxs-lookup"><span data-stu-id="89dbe-163">Create an event handler</span></span> 

<span data-ttu-id="89dbe-164">Jedes Steuerelement verfügt über Ereignisse, mit denen Sie auf Aktionen seitens des Benutzers oder sonstige Änderungen in der App reagieren können.</span><span class="sxs-lookup"><span data-stu-id="89dbe-164">Each control has events that enable you to respond to actions from your user or other changes in your app.</span></span> <span data-ttu-id="89dbe-165">Das „Button“-Steuerelement stellt beispielsweise ein Click-Ereignis bereit, das ausgelöst wird, wenn ein Benutzer auf die Schaltfläche klickt.</span><span class="sxs-lookup"><span data-stu-id="89dbe-165">For example, a Button control has a Click event that is raised when a user clicks the Button.</span></span> <span data-ttu-id="89dbe-166">Sie erstellen eine als Ereignishandler bezeichnete Methode, mit der das Ereignis behandelt wird.</span><span class="sxs-lookup"><span data-stu-id="89dbe-166">You create a method, called an event handler, to handle the event.</span></span> <span data-ttu-id="89dbe-167">Sie können das Ereignis eines Steuerelements einer Ereignishandlermethode im Eigenschaftenfenster, in XAML oder im Code zuordnen.</span><span class="sxs-lookup"><span data-stu-id="89dbe-167">You can associate a control's event with an event handler method in the Properties window, in XAML, or in code.</span></span> <span data-ttu-id="89dbe-168">Weitere Informationen zu Ereignissen finden Sie unter [Übersicht über Ereignisse und Routingereignisse](../../xaml-platform/events-and-routed-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="89dbe-168">For more info about events, see [Events and routed events overview](../../xaml-platform/events-and-routed-events-overview.md).</span></span>

<span data-ttu-id="89dbe-169">Wählen Sie zum Erstellen eines Ereignishandlers das Steuerelement aus, und klicken Sie oben im Eigenschaftenfenster auf die Registerkarte „Ereignisse“.</span><span class="sxs-lookup"><span data-stu-id="89dbe-169">To create an event handler, select the control and then click the Events tab at the top of the Properties window.</span></span> <span data-ttu-id="89dbe-170">Im Eigenschaftenfenster werden alle für das betreffende Steuerelement verfügbaren Ereignisse aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="89dbe-170">The Properties window lists all of the events available for that control.</span></span> <span data-ttu-id="89dbe-171">Im Folgenden werden einige Ereignisse für eine Schaltfläche aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="89dbe-171">Here are some of the events for a Button.</span></span>

![Ereignisliste in Visual Studio](images/add-controls-add-event-designer.png)

<span data-ttu-id="89dbe-173">Wenn Sie einen Ereignishandler mit dem Standardnamen erstellen möchten, doppelklicken Sie im Eigenschaftenfenster auf das Textfeld neben dem Ereignisnamen.</span><span class="sxs-lookup"><span data-stu-id="89dbe-173">To create an event handler with the default name, double-click the text box next to the event name in the Properties window.</span></span> <span data-ttu-id="89dbe-174">Wenn Sie einen Ereignishandler mit einem benutzerdefinierten Namen erstellen möchten, geben Sie im Textfeld den gewünschten Namen ein, und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="89dbe-174">To create an event handler with a custom name, type the name of your choice into the text box and press enter.</span></span> <span data-ttu-id="89dbe-175">Der Ereignishandler wird erstellt, und die CodeBehind-Datei wird im Code-Editor geöffnet.</span><span class="sxs-lookup"><span data-stu-id="89dbe-175">The event handler is created and the code-behind file is opened in the code editor.</span></span> <span data-ttu-id="89dbe-176">Die Ereignishandlermethode enthält zweiParameter.</span><span class="sxs-lookup"><span data-stu-id="89dbe-176">The event handler method has 2 parameters.</span></span> <span data-ttu-id="89dbe-177">Der erste Parameter ist `sender`. Dabei handelt es sich um einen Verweis auf das Objekt, dem der Handler angefügt ist.</span><span class="sxs-lookup"><span data-stu-id="89dbe-177">The first is `sender`, which is a reference to the object where the handler is attached.</span></span> <span data-ttu-id="89dbe-178">Der `sender`-Parameter ist ein **Object**-Typ.</span><span class="sxs-lookup"><span data-stu-id="89dbe-178">The `sender` parameter is an **Object** type.</span></span> <span data-ttu-id="89dbe-179">In der Regel wandeln Sie `sender` in einen genaueren Typ um, wenn Sie den Zustand direkt für das `sender`-Objekt überprüfen oder ändern möchten.</span><span class="sxs-lookup"><span data-stu-id="89dbe-179">You typically cast `sender` to a more precise type if you expect to check or change the state on the `sender` object itself.</span></span> <span data-ttu-id="89dbe-180">Abhängig davon, wo der Handler angefügt wird, handelt es sich dabei basierend auf Ihrem eigenen App-Design voraussichtlich um einen Typ, in den `sender` sicher umgewandelt werden kann.</span><span class="sxs-lookup"><span data-stu-id="89dbe-180">Based on your own app design, you expect a type that is safe to cast the `sender` to, based on where the handler is attached.</span></span> <span data-ttu-id="89dbe-181">Den zweiten Wert stellen Ereignisdaten dar. In der Regel sind diese in Signaturen als `e`- oder `args`-Parameter enthalten.</span><span class="sxs-lookup"><span data-stu-id="89dbe-181">The second value is event data, which generally appears in signatures as the `e` or `args` parameter.</span></span>

<span data-ttu-id="89dbe-182">Hier finden Sie den Code, der das Click-Ereignis einer Schaltfläche namens `Button1` behandelt.</span><span class="sxs-lookup"><span data-stu-id="89dbe-182">Here's code that handles the Click event of a Button named `Button1`.</span></span> <span data-ttu-id="89dbe-183">Wenn Sie auf die Schaltfläche klicken, wird die „Foreground“-Eigenschaft der Schaltfläche auf Blau gesetzt.</span><span class="sxs-lookup"><span data-stu-id="89dbe-183">When you click the button, the Foreground property of the Button you clicked is set to blue.</span></span> 

```csharp
private void Button_Click(object sender, RoutedEventArgs e)
{
    Button b = (Button)sender;
    b.Foreground = new SolidColorBrush(Windows.UI.Colors.Blue);
}
```

<span data-ttu-id="89dbe-184">Sie können einen Ereignishandler auch in XAML zuordnen.</span><span class="sxs-lookup"><span data-stu-id="89dbe-184">You can also associate an event handler in XAML.</span></span> <span data-ttu-id="89dbe-185">Geben Sie im XAML-Editor den Namen des Ereignisses ein, das behandelt werden soll.</span><span class="sxs-lookup"><span data-stu-id="89dbe-185">In the XAML editor, type in the event name that you want to handle.</span></span> <span data-ttu-id="89dbe-186">In Visual Studio wird ein IntelliSense-Fenster geöffnet, sobald Sie mit der Eingabe beginnen.</span><span class="sxs-lookup"><span data-stu-id="89dbe-186">Visual Studio shows an IntelliSense window when you begin typing.</span></span> <span data-ttu-id="89dbe-187">Nach dem Angeben des Ereignisses können Sie im IntelliSense-Fenster auf `<New Event Handler>` doppelklicken, um einen neuen Ereignishandler mit dem Standardnamen zu erstellen oder einen vorhandenen Ereignishandler aus der Liste auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="89dbe-187">After you specify the event, you can double-click `<New Event Handler>` in the IntelliSense window to create a new event handler with the default name, or select an existing event handler from the list.</span></span> 

<span data-ttu-id="89dbe-188">Das folgende IntelliSense-Fenster wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="89dbe-188">Here's the IntelliSense window that appears.</span></span> <span data-ttu-id="89dbe-189">Sie können darin einen neuen Ereignishandler erstellen oder einen vorhandenen Ereignishandler auswählen.</span><span class="sxs-lookup"><span data-stu-id="89dbe-189">It helps you create a new event handler or select an existing event handler.</span></span>

![IntelliSense für das Click-Ereignis](images/add-controls-add-event-xaml.png)

<span data-ttu-id="89dbe-191">In diesem Beispiel wird veranschaulicht, wie in XAML ein Click-Ereignis einem Ereignishandler namens „Button_Click“ zugeordnet wird.</span><span class="sxs-lookup"><span data-stu-id="89dbe-191">This example shows how to associate a Click event with an event handler named Button_Click in XAML.</span></span> 

```xaml
<Button Name="Button1" Content="Button" Click="Button_Click"/>
```

<span data-ttu-id="89dbe-192">Sie können ein Ereignis auch dem zugehörigen Ereignishandler im „CodeBehind“ zuordnen.</span><span class="sxs-lookup"><span data-stu-id="89dbe-192">You can also associate an event with its event handler in the code-behind.</span></span> <span data-ttu-id="89dbe-193">Im Folgenden wird beschrieben, wie ein Ereignishandler im Code zugeordnet wird.</span><span class="sxs-lookup"><span data-stu-id="89dbe-193">Here's how to associate an event handler in code.</span></span>

```csharp
Button1.Click += new RoutedEventHandler(Button_Click);
```

## <a name="related-topics"></a><span data-ttu-id="89dbe-194">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="89dbe-194">Related topics</span></span>

-   [<span data-ttu-id="89dbe-195">Index der Steuerelemente nach Funktion</span><span class="sxs-lookup"><span data-stu-id="89dbe-195">Index of controls by function</span></span>](controls-by-function.md)
-   [<span data-ttu-id="89dbe-196">Windows.UI.Xaml.Controls-Namespace</span><span class="sxs-lookup"><span data-stu-id="89dbe-196">Windows.UI.Xaml.Controls namespace</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.aspx)
-   [<span data-ttu-id="89dbe-197">Layout</span><span class="sxs-lookup"><span data-stu-id="89dbe-197">Layout</span></span>](../layout/index.md)
-   [<span data-ttu-id="89dbe-198">Stil</span><span class="sxs-lookup"><span data-stu-id="89dbe-198">Style</span></span>](../style/index.md)
-   [<span data-ttu-id="89dbe-199">Nutzbarkeit</span><span class="sxs-lookup"><span data-stu-id="89dbe-199">Usability</span></span>](../usability/index.md)
