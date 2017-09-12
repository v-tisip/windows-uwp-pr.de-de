---
author: Jwmsft
Description: "Sie erstellen die Benutzeroberfläche für Ihre App mit Steuerelementen wie Schaltflächen, Textfeldern und Kombinationsfeldern, um Daten anzuzeigen und Benutzereingaben zu erhalten. Hier zeigen wir Ihnen, wie Sie Ihrer App Steuerelemente hinzufügen."
title: "Einführung in Steuerelemente und Muster"
ms.assetid: 64740BF2-CAA1-419E-85D1-42EE7E15F1A5
label: Intro to controls and patterns
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 566f43b83f410ccd690abca95b9de2323fd2631d
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="intro-to-controls-and-patterns"></a><span data-ttu-id="41125-105">Einführung in Steuerelemente und Muster</span><span class="sxs-lookup"><span data-stu-id="41125-105">Intro to controls and patterns</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

<span data-ttu-id="41125-106">In der UWP-App-Entwicklung ist ein *Steuerelement* ein UI-Element, das Inhalte anzeigt oder Interaktionen ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="41125-106">In UWP app development, a *control* is a UI element that displays content or enables interaction.</span></span> <span data-ttu-id="41125-107">Sie erstellen die Benutzeroberfläche für Ihre App mit Steuerelementen wie Schaltflächen, Textfeldern und Kombinationsfeldern, um Daten anzuzeigen und Benutzereingaben zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="41125-107">You create the UI for your app by using controls such as buttons, text boxes, and combo boxes to display data and get user input.</span></span>

> <span data-ttu-id="41125-108">**Wichtige APIs:** [Namespace „Windows.UI.Xaml.Controls“](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.aspx)</span><span class="sxs-lookup"><span data-stu-id="41125-108">**Important APIs**: [Windows.UI.Xaml.Controls namespace](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.aspx)</span></span>

<span data-ttu-id="41125-109">Ein *Muster* ist eine Anleitung zum Ändern eines Steuerelements oder zum Kombinieren verschiedener Steuerelemente, um etwas Neues zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="41125-109">A *pattern* is a recipe for modifying a control or combining several controls to make something new.</span></span> <span data-ttu-id="41125-110">Das [Navigationsbereichsmuster](navigationview.md) ist z.B. eine Möglichkeit, mit der Sie ein [SplitView](split-view.md)-Steuerelement zur App-Navigation verwenden können.</span><span class="sxs-lookup"><span data-stu-id="41125-110">For example, the [Nav pane](navigationview.md) pattern is a way that you can use a [SplitView](split-view.md) control for app navigation.</span></span> <span data-ttu-id="41125-111">Ebenso können Sie die Vorlage eines [Pivot](tabs-pivot.md)-Steuerelements zum Implementieren des Registerkartenmusters anpassen.</span><span class="sxs-lookup"><span data-stu-id="41125-111">Similarly, you can customize the template of a [Pivot](tabs-pivot.md) control to implement the tab pattern.</span></span>

<span data-ttu-id="41125-112">In vielen Fällen können Sie ein Steuerelement unverändert verwenden.</span><span class="sxs-lookup"><span data-stu-id="41125-112">In many cases, you can use a control as-is.</span></span> <span data-ttu-id="41125-113">XAML-Steuerelemente trennen jedoch die Funktion von der Struktur und Darstellung, sodass Sie diese über verschiedene Änderungsebenen an Ihre Bedürfnisse anpassen können.</span><span class="sxs-lookup"><span data-stu-id="41125-113">But XAML controls separate function from structure and appearance, so you can make various levels of modification to make them fit your needs.</span></span> <span data-ttu-id="41125-114">Im Abschnitt [Stil](../style/index.md) erfahren Sie, wie Sie mithilfe von [XAML-Formatvorlagen](xaml-styles.md) und [Steuerelementvorlagen](control-templates.md) Steuerelemente ändern.</span><span class="sxs-lookup"><span data-stu-id="41125-114">In the [Style](../style/index.md) section, you can learn how to use [XAML styles](xaml-styles.md) and [control templates](control-templates.md) to modify a control.</span></span>

<span data-ttu-id="41125-115">In diesem Abschnitt erhalten Sie Anleitungen zu jedem XAML-Steuerelement, das Sie zum Erstellen Ihrer App-UI verwenden können.</span><span class="sxs-lookup"><span data-stu-id="41125-115">In this section, we provide guidance for each of the XAML controls you can use to build your app UI.</span></span> <span data-ttu-id="41125-116">Zu Beginn wird in diesem Artikel beschrieben, wie Sie der App Steuerelemente hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="41125-116">To start, this article shows you how to add controls to your app.</span></span> <span data-ttu-id="41125-117">Es gibt drei wichtige Schritte zum Hinzufügen von Steuerelementen zur App:</span><span class="sxs-lookup"><span data-stu-id="41125-117">There are 3 key steps to using controls to your app:</span></span> 

- <span data-ttu-id="41125-118">Fügen Sie Ihrer App-UI ein Steuerelement hinzu.</span><span class="sxs-lookup"><span data-stu-id="41125-118">Add a control to your app UI.</span></span> 
- <span data-ttu-id="41125-119">Legen Sie Eigenschaften für das Steuerelement fest, z.B. Breite, Höhe und Vordergrundfarbe.</span><span class="sxs-lookup"><span data-stu-id="41125-119">Set properties on the control, such as width, height, or foreground color.</span></span> 
- <span data-ttu-id="41125-120">Fügen Sie den Ereignishandlern des Steuerelements Code hinzu, damit sie eine Funktion haben.</span><span class="sxs-lookup"><span data-stu-id="41125-120">Add code to the control's event handlers so that it does something.</span></span> 

## <a name="add-a-control"></a><span data-ttu-id="41125-121">Hinzufügen eines Steuerelements</span><span class="sxs-lookup"><span data-stu-id="41125-121">Add a control</span></span>
<span data-ttu-id="41125-122">Es gibt mehrere Möglichkeiten, einer App ein Steuerelement hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="41125-122">You can add a control to an app in several ways:</span></span>
 
- <span data-ttu-id="41125-123">Verwenden Sie ein Entwicklungstool wie Blend für Visual Studio oder Microsoft Visual Studio Extensible Application Markup Language (XAML)-Designer.</span><span class="sxs-lookup"><span data-stu-id="41125-123">Use a design tool like Blend for Visual Studio or the Microsoft Visual Studio Extensible Application Markup Language (XAML) designer.</span></span> 
- <span data-ttu-id="41125-124">Fügen Sie das Steuerelement dem XAML-Markup im XAML-Editor in Visual Studio hinzu.</span><span class="sxs-lookup"><span data-stu-id="41125-124">Add the control to the XAML markup in the Visual Studio XAML editor.</span></span> 
- <span data-ttu-id="41125-125">Fügen Sie das Steuerelement im Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="41125-125">Add the control in code.</span></span> <span data-ttu-id="41125-126">Im Code hinzugefügte Steuerelemente sind bei der Ausführung der App, jedoch nicht im Visual Studio-XAML-Designer sichtbar.</span><span class="sxs-lookup"><span data-stu-id="41125-126">Controls that you add in code are visible when the app runs, but are not visible in the Visual Studio XAML designer.</span></span>

<span data-ttu-id="41125-127">Wenn Sie in Visual Studio Steuerelemente in Ihrer App hinzufügen und bearbeiten, können Sie viele Features des Programms wie die Toolbox, den XAML-Designer, den XAML-Editor und das Eigenschaftenfenster nutzen.</span><span class="sxs-lookup"><span data-stu-id="41125-127">In Visual Studio, when you add and manipulate controls in your app, you can use many of the program's features, including the Toolbox, XAML designer, XAML editor, and the Properties window.</span></span> 

<span data-ttu-id="41125-128">In der Toolbox von Visual Studio werden viele Steuerelemente angezeigt, die Sie in Ihrer App verwenden können.</span><span class="sxs-lookup"><span data-stu-id="41125-128">The Visual Studio Toolbox displays many of the controls that you can use in your app.</span></span> <span data-ttu-id="41125-129">Wenn Sie der App ein Steuerelement hinzufügen möchten, doppelklicken Sie in der Toolbox auf das gewünschte Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="41125-129">To add a control to your app, double-click it in the Toolbox.</span></span> <span data-ttu-id="41125-130">Wenn Sie beispielsweise auf das „TextBox“-Steuerelement doppelklicken, wird der XAML-Ansicht folgender XAML-Code hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="41125-130">For example, when you double-click the TextBox control, this XAML is added to the XAML view.</span></span> 

```xaml
<TextBox HorizontalAlignment="Left" Text="TextBox" VerticalAlignment="Top"/>
```

<span data-ttu-id="41125-131">Sie können das Steuerelement auch aus der Toolbox in den XAML-Designer ziehen.</span><span class="sxs-lookup"><span data-stu-id="41125-131">You can also drag the control from the Toolbox to the XAML designer.</span></span>

## <a name="set-the-name-of-a-control"></a><span data-ttu-id="41125-132">Festlegen des Namens eines Steuerelements</span><span class="sxs-lookup"><span data-stu-id="41125-132">Set the name of a control</span></span> 

<span data-ttu-id="41125-133">Wenn Sie mit einem Steuerelement im Code arbeiten möchten, legen Sie das Attribut [x:Name](../xaml-platform/x-name-attribute.md) fest und verweisen im Code anhand des Namens darauf.</span><span class="sxs-lookup"><span data-stu-id="41125-133">To work with a control in code, you set its [x:Name](../xaml-platform/x-name-attribute.md) attribute and reference it by name in your code.</span></span> <span data-ttu-id="41125-134">Sie können den Namen im Eigenschaftenfenster von Visual Studio oder in XAML festlegen.</span><span class="sxs-lookup"><span data-stu-id="41125-134">You can set the name in the Visual Studio Properties window or in XAML.</span></span> <span data-ttu-id="41125-135">Hier wird veranschaulicht, wie Sie den Namen des derzeit ausgewählten Steuerelements über das Textfeld Name am oberen Rand des Eigenschaftenfensters festlegen.</span><span class="sxs-lookup"><span data-stu-id="41125-135">Here's how to set the name of the currently selected control by using the Name text box at the top of the Properties window.</span></span> 

<span data-ttu-id="41125-136">So benennen Sie ein Steuerelement</span><span class="sxs-lookup"><span data-stu-id="41125-136">To name a control</span></span>
1. <span data-ttu-id="41125-137">Wählen Sie das zu benennende Element aus.</span><span class="sxs-lookup"><span data-stu-id="41125-137">Select the element to name.</span></span>
2. <span data-ttu-id="41125-138">Geben Sie im Eigenschaftenpanel einen Namen in das Textfeld Name ein.</span><span class="sxs-lookup"><span data-stu-id="41125-138">In the Properties panel, type a name into the Name text box.</span></span>
3. <span data-ttu-id="41125-139">Drücken Sie die EINGABETASTE, um den Namen zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="41125-139">Press Enter to commit the name.</span></span>

![Name-Eigenschaft im Visual Studio-Designer](images/add-controls-control-name-designer.png)

<span data-ttu-id="41125-141">Hier wird erläutert, wie Sie den Namen eines Steuerelements im XAML-Editor festlegen, indem Sie das x:Name-Attribut hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="41125-141">Here's how to set the name of a control in the XAML editor by adding the x:Name attribute.</span></span>

```xaml
<Button x:Name="Button1" Content="Button"/>
```

## <a name="set-the-control-properties"></a><span data-ttu-id="41125-142">Festlegen von Steuerelementeigenschaften</span><span class="sxs-lookup"><span data-stu-id="41125-142">Set the control properties</span></span> 

<span data-ttu-id="41125-143">Mithilfe von Eigenschaften geben Sie das Erscheinungsbild, den Inhalt sowie weitere Attribute von Steuerelementen an.</span><span class="sxs-lookup"><span data-stu-id="41125-143">You use properties to specify the appearance, content, and other attributes of controls.</span></span> <span data-ttu-id="41125-144">Wenn Sie ein Steuerelement mit einem Entwicklungstool hinzufügen, werden manche Eigenschaften, die Größe, Position und Inhalt steuern, möglicherweise von Visual Studio für Sie festgelegt.</span><span class="sxs-lookup"><span data-stu-id="41125-144">When you add a control using a design tool, some properties that control size, position, and content might be set for you by Visual Studio.</span></span> <span data-ttu-id="41125-145">Sie können einige Eigenschaften wie etwa die Breite, die Höhe oder den Rand ändern, indem Sie das Steuerelement in der Entwurfsansicht auswählen und bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="41125-145">You can change some properties, such as Width, Height or Margin, by selecting and manipulating the control in the Design view.</span></span> <span data-ttu-id="41125-146">In der Abbildung werden einige der in der Entwurfsansicht verfügbaren Größenanpassungstools veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="41125-146">This illustration shows some of the resizing tools available in Design view.</span></span> 

![Größenanpassungstools im Visual Studio-Designer](images/add-controls-resizing-designer.png)

<span data-ttu-id="41125-148">Sie können die Größe und die Position des Steuerelements auch automatisch festlegen lassen.</span><span class="sxs-lookup"><span data-stu-id="41125-148">You might want to let the control be sized and positioned automatically.</span></span> <span data-ttu-id="41125-149">In diesem Fall können Sie die von Visual Studio festgelegten Eigenschaften für Größe und Position zurücksetzen.</span><span class="sxs-lookup"><span data-stu-id="41125-149">In this case, you can reset the size and position properties that Visual Studio set for you.</span></span>

<span data-ttu-id="41125-150">Zurücksetzen einer Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="41125-150">To reset a property</span></span>
1. <span data-ttu-id="41125-151">Klicken Sie im Bereich Eigenschaften auf den Eigenschaftsmarker neben dem Eigenschaftswert.</span><span class="sxs-lookup"><span data-stu-id="41125-151">In the Properties panel, click the property marker next to the property value.</span></span> <span data-ttu-id="41125-152">Das Eigenschaftsmenü wird geöffnet.</span><span class="sxs-lookup"><span data-stu-id="41125-152">The property menu opens.</span></span>
2. <span data-ttu-id="41125-153">Klicken Sie im Eigenschaftsmenü auf „Zurücksetzen“.</span><span class="sxs-lookup"><span data-stu-id="41125-153">In the property menu, click Reset.</span></span>

![Option „Zurücksetzen“ im Visual Studio-Menü „Eigenschaften“](images/add-controls-property-reset.png)

<span data-ttu-id="41125-155">Sie können Steuerelementeigenschaften im Eigenschaftenfenster, in XAML oder im Code festlegen.</span><span class="sxs-lookup"><span data-stu-id="41125-155">You can set control properties in the Properties window, in XAML, or in code.</span></span> <span data-ttu-id="41125-156">Wenn Sie beispielsweise die Vordergrundfarbe einer Schaltfläche ändern möchten, legen Sie die „Foreground“-Eigenschaft des Steuerelements fest.</span><span class="sxs-lookup"><span data-stu-id="41125-156">For example, to change the foreground color for a Button, you set the control's Foreground property.</span></span> <span data-ttu-id="41125-157">In dieser Abbildung wird veranschaulicht, wie die „Foreground“-Eigenschaft über die Farbauswahl im Eigenschaftenfenster festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="41125-157">This illustration shows how to set the Foreground property by using the color picker in the Properties window.</span></span> 

![Farbauswahl im Visual Studio-Designer](images/add-controls-foreground-designer.png)

<span data-ttu-id="41125-159">Hier wird beschrieben, wie Sie die „Foreground“-Eigenschaft im XAML-Editor festlegen.</span><span class="sxs-lookup"><span data-stu-id="41125-159">Here's how to set the Foreground property in the XAML editor.</span></span> <span data-ttu-id="41125-160">Beachten Sie das Visual Studio IntelliSense-Fenster, in dem hilfreiche Informationen zur Syntax angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="41125-160">Notice the Visual Studio IntelliSense window that opens to help you with the syntax.</span></span> 

![IntelliSense in XAML Teil1](images/add-controls-foreground-xaml.png)

![IntelliSense in XAML Teil2](images/add-controls-foreground-xaml-2.png)

<span data-ttu-id="41125-163">Im Folgenden finden Sie den XAML-Code, der nach dem Festlegen der „Foreground“-Eigenschaft vorliegt.</span><span class="sxs-lookup"><span data-stu-id="41125-163">Here's the resulting XAML after you set the Foreground property.</span></span> 

```xaml
<Button x:Name="Button1" Content="Button" 
        HorizontalAlignment="Left" VerticalAlignment="Top"
        Foreground="Beige"/>
```

<span data-ttu-id="41125-164">An dieser Stelle wird beschrieben, wie die „Foreground“-Eigenschaft im Code festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="41125-164">Here's how to set the Foreground property in code.</span></span> 

```csharp
Button1.Foreground = new SolidColorBrush(Windows.UI.Colors.Beige);
```

## <a name="create-an-event-handler"></a><span data-ttu-id="41125-165">Erstellen eines Ereignishandlers</span><span class="sxs-lookup"><span data-stu-id="41125-165">Create an event handler</span></span> 

<span data-ttu-id="41125-166">Jedes Steuerelement verfügt über Ereignisse, mit denen Sie auf Aktionen seitens des Benutzers oder sonstige Änderungen in der App reagieren können.</span><span class="sxs-lookup"><span data-stu-id="41125-166">Each control has events that enable you to respond to actions from your user or other changes in your app.</span></span> <span data-ttu-id="41125-167">Das „Button“-Steuerelement stellt beispielsweise ein Click-Ereignis bereit, das ausgelöst wird, wenn ein Benutzer auf die Schaltfläche klickt.</span><span class="sxs-lookup"><span data-stu-id="41125-167">For example, a Button control has a Click event that is raised when a user clicks the Button.</span></span> <span data-ttu-id="41125-168">Sie erstellen eine als Ereignishandler bezeichnete Methode, mit der das Ereignis behandelt wird.</span><span class="sxs-lookup"><span data-stu-id="41125-168">You create a method, called an event handler, to handle the event.</span></span> <span data-ttu-id="41125-169">Sie können das Ereignis eines Steuerelements einer Ereignishandlermethode im Eigenschaftenfenster, in XAML oder im Code zuordnen.</span><span class="sxs-lookup"><span data-stu-id="41125-169">You can associate a control's event with an event handler method in the Properties window, in XAML, or in code.</span></span> <span data-ttu-id="41125-170">Weitere Informationen zu Ereignissen finden Sie unter [Übersicht über Ereignisse und Routingereignisse](../xaml-platform/events-and-routed-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="41125-170">For more info about events, see [Events and routed events overview](../xaml-platform/events-and-routed-events-overview.md).</span></span>

<span data-ttu-id="41125-171">Wählen Sie zum Erstellen eines Ereignishandlers das Steuerelement aus, und klicken Sie oben im Eigenschaftenfenster auf die Registerkarte „Ereignisse“.</span><span class="sxs-lookup"><span data-stu-id="41125-171">To create an event handler, select the control and then click the Events tab at the top of the Properties window.</span></span> <span data-ttu-id="41125-172">Im Eigenschaftenfenster werden alle für das betreffende Steuerelement verfügbaren Ereignisse aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="41125-172">The Properties window lists all of the events available for that control.</span></span> <span data-ttu-id="41125-173">Im Folgenden werden einige Ereignisse für eine Schaltfläche aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="41125-173">Here are some of the events for a Button.</span></span>

![Ereignisliste in Visual Studio](images/add-controls-add-event-designer.png)

<span data-ttu-id="41125-175">Wenn Sie einen Ereignishandler mit dem Standardnamen erstellen möchten, doppelklicken Sie im Eigenschaftenfenster auf das Textfeld neben dem Ereignisnamen.</span><span class="sxs-lookup"><span data-stu-id="41125-175">To create an event handler with the default name, double-click the text box next to the event name in the Properties window.</span></span> <span data-ttu-id="41125-176">Wenn Sie einen Ereignishandler mit einem benutzerdefinierten Namen erstellen möchten, geben Sie im Textfeld den gewünschten Namen ein, und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="41125-176">To create an event handler with a custom name, type the name of your choice into the text box and press enter.</span></span> <span data-ttu-id="41125-177">Der Ereignishandler wird erstellt, und die CodeBehind-Datei wird im Code-Editor geöffnet.</span><span class="sxs-lookup"><span data-stu-id="41125-177">The event handler is created and the code-behind file is opened in the code editor.</span></span> <span data-ttu-id="41125-178">Die Ereignishandlermethode enthält zweiParameter.</span><span class="sxs-lookup"><span data-stu-id="41125-178">The event handler method has 2 parameters.</span></span> <span data-ttu-id="41125-179">Der erste Parameter ist `sender`. Dabei handelt es sich um einen Verweis auf das Objekt, dem der Handler angefügt ist.</span><span class="sxs-lookup"><span data-stu-id="41125-179">The first is `sender`, which is a reference to the object where the handler is attached.</span></span> <span data-ttu-id="41125-180">Der `sender`-Parameter ist ein **Object**-Typ.</span><span class="sxs-lookup"><span data-stu-id="41125-180">The `sender` parameter is an **Object** type.</span></span> <span data-ttu-id="41125-181">In der Regel wandeln Sie `sender` in einen genaueren Typ um, wenn Sie den Zustand direkt für das `sender`-Objekt überprüfen oder ändern möchten.</span><span class="sxs-lookup"><span data-stu-id="41125-181">You typically cast `sender` to a more precise type if you expect to check or change the state on the `sender` object itself.</span></span> <span data-ttu-id="41125-182">Abhängig davon, wo der Handler angefügt wird, handelt es sich dabei basierend auf Ihrem eigenen App-Design voraussichtlich um einen Typ, in den `sender` sicher umgewandelt werden kann.</span><span class="sxs-lookup"><span data-stu-id="41125-182">Based on your own app design, you expect a type that is safe to cast the `sender` to, based on where the handler is attached.</span></span> <span data-ttu-id="41125-183">Den zweiten Wert stellen Ereignisdaten dar. In der Regel sind diese in Signaturen als `e`- oder `args`-Parameter enthalten.</span><span class="sxs-lookup"><span data-stu-id="41125-183">The second value is event data, which generally appears in signatures as the `e` or `args` parameter.</span></span>

<span data-ttu-id="41125-184">Hier finden Sie den Code, der das Click-Ereignis einer Schaltfläche namens `Button1` behandelt.</span><span class="sxs-lookup"><span data-stu-id="41125-184">Here's code that handles the Click event of a Button named `Button1`.</span></span> <span data-ttu-id="41125-185">Wenn Sie auf die Schaltfläche klicken, wird die „Foreground“-Eigenschaft der Schaltfläche auf Blau gesetzt.</span><span class="sxs-lookup"><span data-stu-id="41125-185">When you click the button, the Foreground property of the Button you clicked is set to blue.</span></span> 

```csharp
private void Button_Click(object sender, RoutedEventArgs e)
{
    Button b = (Button)sender;
    b.Foreground = new SolidColorBrush(Windows.UI.Colors.Blue);
}
```

<span data-ttu-id="41125-186">Sie können einen Ereignishandler auch in XAML zuordnen.</span><span class="sxs-lookup"><span data-stu-id="41125-186">You can also associate an event handler in XAML.</span></span> <span data-ttu-id="41125-187">Geben Sie im XAML-Editor den Namen des Ereignisses ein, das behandelt werden soll.</span><span class="sxs-lookup"><span data-stu-id="41125-187">In the XAML editor, type in the event name that you want to handle.</span></span> <span data-ttu-id="41125-188">In Visual Studio wird ein IntelliSense-Fenster geöffnet, sobald Sie mit der Eingabe beginnen.</span><span class="sxs-lookup"><span data-stu-id="41125-188">Visual Studio shows an IntelliSense window when you begin typing.</span></span> <span data-ttu-id="41125-189">Nach dem Angeben des Ereignisses können Sie im IntelliSense-Fenster auf `<New Event Handler>` doppelklicken, um einen neuen Ereignishandler mit dem Standardnamen zu erstellen oder einen vorhandenen Ereignishandler aus der Liste auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="41125-189">After you specify the event, you can double-click `<New Event Handler>` in the IntelliSense window to create a new event handler with the default name, or select an existing event handler from the list.</span></span> 

<span data-ttu-id="41125-190">Das folgende IntelliSense-Fenster wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="41125-190">Here's the IntelliSense window that appears.</span></span> <span data-ttu-id="41125-191">Sie können darin einen neuen Ereignishandler erstellen oder einen vorhandenen Ereignishandler auswählen.</span><span class="sxs-lookup"><span data-stu-id="41125-191">It helps you create a new event handler or select an existing event handler.</span></span>

![IntelliSense für das Click-Ereignis](images/add-controls-add-event-xaml.png)

<span data-ttu-id="41125-193">In diesem Beispiel wird veranschaulicht, wie in XAML ein Click-Ereignis einem Ereignishandler namens „Button_Click“ zugeordnet wird.</span><span class="sxs-lookup"><span data-stu-id="41125-193">This example shows how to associate a Click event with an event handler named Button_Click in XAML.</span></span> 

```xaml
<Button Name="Button1" Content="Button" Click="Button_Click"/>
```

<span data-ttu-id="41125-194">Sie können ein Ereignis auch dem zugehörigen Ereignishandler im „CodeBehind“ zuordnen.</span><span class="sxs-lookup"><span data-stu-id="41125-194">You can also associate an event with its event handler in the code-behind.</span></span> <span data-ttu-id="41125-195">Im Folgenden wird beschrieben, wie ein Ereignishandler im Code zugeordnet wird.</span><span class="sxs-lookup"><span data-stu-id="41125-195">Here's how to associate an event handler in code.</span></span>

```csharp
Button1.Click += new RoutedEventHandler(Button_Click);
```

## <a name="related-topics"></a><span data-ttu-id="41125-196">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="41125-196">Related topics</span></span>

-     [<span data-ttu-id="41125-197">Index der Steuerelemente nach Funktion</span><span class="sxs-lookup"><span data-stu-id="41125-197">Index of controls by function</span></span>](controls-by-function.md)
-     [<span data-ttu-id="41125-198">Windows.UI.Xaml.Controls-Namespace</span><span class="sxs-lookup"><span data-stu-id="41125-198">Windows.UI.Xaml.Controls namespace</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.aspx)
-     [<span data-ttu-id="41125-199">Layout</span><span class="sxs-lookup"><span data-stu-id="41125-199">Layout</span></span>](../layout/index.md)
-     [<span data-ttu-id="41125-200">Stil</span><span class="sxs-lookup"><span data-stu-id="41125-200">Style</span></span>](../style/index.md)
-     [<span data-ttu-id="41125-201">Nutzbarkeit</span><span class="sxs-lookup"><span data-stu-id="41125-201">Usability</span></span>](../usability/index.md)
