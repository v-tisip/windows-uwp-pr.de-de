---
author: stevewhims
description: Aufbau von Visual Studio
title: Aufbau von Visual Studio
ms.assetid: 7FBB50A2-6D22-4082-B333-5153DADDDE9A
ms.author: stwhi
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 8219f1600297dfa60345fe8130e8954558b8ac61
ms.sourcegitcommit: 086001cffaf436e6e4324761d59bcc5e598c15ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2018
ms.locfileid: "5689988"
---
# <a name="getting-started-getting-around-in-visual-studio"></a><span data-ttu-id="1f187-104">Erste Schritte: Aufbau von Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1f187-104">Getting started: Getting around in Visual Studio</span></span>


## <a name="getting-around-in-microsoft-visual-studio"></a><span data-ttu-id="1f187-105">Aufbau von Microsoft Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1f187-105">Getting around in Microsoft Visual Studio</span></span>

<span data-ttu-id="1f187-106">Kehren wir nun zum Projekt zurück, das wir zuvor erstellt haben. Dabei soll der Aufbau der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) von Microsoft Visual Studio veranschaulicht werden.</span><span class="sxs-lookup"><span data-stu-id="1f187-106">Let's now get back to the project that we created earlier, and look at how you might find your way around the Microsoft Visual Studio integrated development environment (IDE).</span></span>

<span data-ttu-id="1f187-107">Xcode-Entwickler sollten die im Folgenden dargestellte Standardansicht kennen. Dabei befinden sich die Quelldateien im linken Bereich und der Editor (für Benutzeroberfläche oder Quellcode) ist in der Mitte angeordnet. Im Bereich auf der rechten Seite sind die Steuerelemente und die zugehörigen Eigenschaften angeordnet.</span><span class="sxs-lookup"><span data-stu-id="1f187-107">If you are an Xcode developer, the default view below should be familiar, with source files in the left pane, the editor (either the UI or source code) in the center pane, and controls and their properties in the right pane.</span></span>

![Xcode-Entwicklungsumgebung](images/ios-to-uwp/xcode-ide.png)

<span data-ttu-id="1f187-109">Microsoft Visual Studio ist ähnlich aufgebaut, obwohl sich die Steuerelemente in der Standardansicht auf der linken Seite in der **Toolbox** befinden.</span><span class="sxs-lookup"><span data-stu-id="1f187-109">Microsoft Visual Studio looks very similar, although the default view has the controls on the left side in the **Toolbox**.</span></span> <span data-ttu-id="1f187-110">Die Quelldateien befinden sich im **Projektmappen-Explorer** auf der rechten Seite, und die Eigenschaften werden unter **Eigenschaften** im Bereich **Projektmappen-Explorer** wie folgt aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="1f187-110">The source files are in the **Solution Explorer** on the right side, and properties are in **Properties** under the **Solution Explorer** pane, like this:</span></span>

![Visual Studio-Entwicklungsumgebung](images/ios-to-uwp/vs-ide.png)

<span data-ttu-id="1f187-112">Wenn dies etwas ungewohnt für Sie ist, können Sie die Bereiche in Visual Studio neu anordnen und die Quelldateien im linken Bereich des Bildschirms und die Toolbox auf der rechten Seite platzieren.</span><span class="sxs-lookup"><span data-stu-id="1f187-112">If this feels a little alien to you, you'll be pleased to know you can rearrange the panes in Visual Studio to place the source files on the left of the screen and the toolbox on the right.</span></span> <span data-ttu-id="1f187-113">Sie können auf die Titelleiste eines beliebigen Bereichs klicken und diese ziehen, um sie neu anzuordnen. In Visual Studio wird anhand eines schattierten Felds angezeigt, an welcher Stelle sie nach Veröffentlichung angedockt wird.</span><span class="sxs-lookup"><span data-stu-id="1f187-113">In fact, you can click and drag the title bar of any pane to reposition it, and Visual Studio will display a shaded box telling you where it will be docked once you release it.</span></span> <span data-ttu-id="1f187-114">Viele Bereiche können auch ein kleines Reißzweckensymbol in der Titelleiste aufweisen.</span><span class="sxs-lookup"><span data-stu-id="1f187-114">Many panes also have a small drawing pin icon in their title bar.</span></span> <span data-ttu-id="1f187-115">Damit können Sie den Bereich anheften und an dieser Stelle sperren.</span><span class="sxs-lookup"><span data-stu-id="1f187-115">This allows you to pin the panel as-is, locking it in place.</span></span> <span data-ttu-id="1f187-116">Beim lösen des Bereichs kann dieser ausgeblendet werden, um Platz zu sparen. Dies ist nützlich, wenn sich der Bildschirm auf der schmalen Seite befindet.</span><span class="sxs-lookup"><span data-stu-id="1f187-116">Unpin the pane, and it can be collapsed to save space: useful if your monitor is on the smaller side.</span></span> <span data-ttu-id="1f187-117">Wählen Sie, wenn Sie sich vertan haben, **Fensterlayout zurücksetzen** im Menü **Fenster** aus, um die Reihenfolge wiederherzustellen.</span><span class="sxs-lookup"><span data-stu-id="1f187-117">If you mess things up (don't worry, we've all done it), select **Reset Window Layout** from the **Window** menu to restore order.</span></span>

## <a name="adding-controls-setting-their-properties-and-responding-to-events"></a><span data-ttu-id="1f187-118">Hinzufügen von Steuerelementen, Festlegen der zugehörigen Eigenschaften und Reagieren auf Ereignisse</span><span class="sxs-lookup"><span data-stu-id="1f187-118">Adding controls, setting their properties, and responding to events</span></span>

<span data-ttu-id="1f187-119">Lassen Sie uns dem Projekt nun einige Steuerelemente hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="1f187-119">Let's now add some controls to your project.</span></span> <span data-ttu-id="1f187-120">Anschließend ändern wir einige der Steuerelementeigenschaften und schreiben Code, um auf eines der Steuerelementereignisse zu reagieren.</span><span class="sxs-lookup"><span data-stu-id="1f187-120">We'll then change some of their properties, and write some code to respond to one of the control's events.</span></span>

<span data-ttu-id="1f187-121">Zum Hinzufügen von Steuerelementen in Xcode öffnen Sie die gewünschte XIB-Datei oder das Storyboard, und fügen Sie dann per Drag & Drop wie im Folgenden dargestellt Steuerelemente hinzu, beispielsweise eine **rechteckige Schaltfläche mit abgerundeten Ecken** und eine **Bezeichnung**.</span><span class="sxs-lookup"><span data-stu-id="1f187-121">To add controls in Xcode, you open up the desired .xib file or the Storyboard and then drag and drop controls, such as a**Round Rect Button** or a **Label**, as shown below:</span></span>

![Entwerfen der Benutzeroberfläche in Xcode](images/ios-to-uwp/xcode-add-button-label.png)

<span data-ttu-id="1f187-123">Lassen Sie uns nun einen ähnlichen Vorgang in Visual Studio ausführen.</span><span class="sxs-lookup"><span data-stu-id="1f187-123">Let's do something similar in Visual Studio.</span></span> <span data-ttu-id="1f187-124">Ziehen Sie in der **Toolbox** das **Schaltflächen**-Steuerelement und legen Sie es auf der Entwurfsoberfläche der Datei „MainPage.xaml“ ab.</span><span class="sxs-lookup"><span data-stu-id="1f187-124">From the **Toolbox**, drag the **Button** control, and then drop it onto the MainPage.xaml file's design surface.</span></span>

<span data-ttu-id="1f187-125">Wiederholen Sie den Vorgang für das **TextBlock**-Steuerelement, sodass es wie folgt aussieht:</span><span class="sxs-lookup"><span data-stu-id="1f187-125">Do the same with the **TextBlock** control, so it looks like this:</span></span>

![Entwerfen der Benutzeroberfläche in Visual Studio](images/ios-to-uwp/vs-add-button-label.png)

<span data-ttu-id="1f187-127">Im Gegensatz zu Xcode, wo Layout- und Bindungsinformationen in einer XIB- oder einer Storyboard-Datei gespeichert sind, wird in Visual Studio empfohlen, die zum Speichern dieser Details verwendeten XAML-Dateien in einer umfangreichen, bearbeitbaren, deklarativen XML-ähnlichen Sprache zu bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="1f187-127">Unlike Xcode, which hides the layout and binding information inside a .xib or Storyboard file, Visual Studio encourages you to edit the XAML files used to store these details it its rich, editable, declarative, XML-like language.</span></span> <span data-ttu-id="1f187-128">Weitere Informationen zu Extensible Application Markup Language (XAML) finden Sie in der [XAML-Übersicht](https://msdn.microsoft.com/library/windows/apps/mt185595).</span><span class="sxs-lookup"><span data-stu-id="1f187-128">For more info about Extensible Application Markup Language (XAML), see [XAML overview](https://msdn.microsoft.com/library/windows/apps/mt185595).</span></span> <span data-ttu-id="1f187-129">Alle derzeit im Bereich **Entwurf** angezeigten Inhalte werden im **XAML**-Bereich definiert.</span><span class="sxs-lookup"><span data-stu-id="1f187-129">For now, know that everything displayed in the **Design** pane is defined in the **XAML** pane.</span></span> <span data-ttu-id="1f187-130">Der **XAML**-Bereich ermöglicht bei Bedarf eine genaue Steuerung, und sobald Sie sich eingearbeitet haben, kommen Sie mit dem manuellen Schreiben von Benutzeroberflächencode schnell voran.</span><span class="sxs-lookup"><span data-stu-id="1f187-130">The **XAML** pane allows for fine control where necessary, and as you learn more about it, you can quickly develop user interface code manually.</span></span> <span data-ttu-id="1f187-131">An dieser Stelle konzentrieren wir uns jedoch ausschließlich auf die Bereiche **Entwurf** und **Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="1f187-131">For now, however, let's focus on just the **Design** and **Properties** panes.</span></span>

<span data-ttu-id="1f187-132">Ändern wir nun die Schaltflächendetails.</span><span class="sxs-lookup"><span data-stu-id="1f187-132">Let's change the button's details.</span></span> <span data-ttu-id="1f187-133">Wie Sie nachvollziehen können, muss zum Ändern des Namens der Schaltfläche in Xcode der Wert des Felds **Titel** im Eigenschaftenpanel geändert werden.</span><span class="sxs-lookup"><span data-stu-id="1f187-133">As you will know, to change the button's name in Xcode, you would change the value of the **Title** field in its properties panel.</span></span>

<span data-ttu-id="1f187-134">Bei Verwendung von Visual Studio gehen Sie ähnlich vor.</span><span class="sxs-lookup"><span data-stu-id="1f187-134">When using Visual Studio you do something very similar.</span></span> <span data-ttu-id="1f187-135">Tippen Sie im Bereich **Entwurf** auf die Schaltfläche, damit sie den Fokus erhält.</span><span class="sxs-lookup"><span data-stu-id="1f187-135">In the **Design** pane, tap the button to give it focus.</span></span> <span data-ttu-id="1f187-136">Ändern Sie dann im Bereich **Eigenschaften** den Wert des Felds **Inhalt** von „Button“ in „Press Me“.</span><span class="sxs-lookup"><span data-stu-id="1f187-136">Then in the **Properties** pane, alter the **Content** value from "Button" to "Press Me".</span></span> <span data-ttu-id="1f187-137">Aktualisieren Sie als Nächstes den Namen des Schaltflächen-Steuerelements, indem Sie den **Name**-Wert von "&lt;No Name&gt;" in "myButton" ändern, wie hier gezeigt:</span><span class="sxs-lookup"><span data-stu-id="1f187-137">Next, update the name of the button control, by changing the **Name** value from "&lt;No Name&gt;" to "myButton", as shown here:</span></span>

![Fenster "Schaltflächeneigenschaften" in Visual Studio](images/ios-to-uwp/vs-button-properties.png)

<span data-ttu-id="1f187-139">Lassen Sie uns nun Code zum Ändern der Inhalte des **TextBlock**-Steuerelements in „Hello, World!“ schreiben, sodass dieser Text angezeigt wird,</span><span class="sxs-lookup"><span data-stu-id="1f187-139">Now, let's write some code to change the **TextBlock** control's contents to "Hello, World!"</span></span> <span data-ttu-id="1f187-140">nachdem der Benutzer auf die Schaltfläche getippt hat.</span><span class="sxs-lookup"><span data-stu-id="1f187-140">after the user taps the button.</span></span>

<span data-ttu-id="1f187-141">In Xcode würden Sie ein Ereignis zu einem Steuerelement zuordnen, indem Sie Code schreiben und diesen Code dann dem Steuerelement zuordnen. Dies geschieht häufig durch gesteuertes Ziehen der Schaltfläche in den Quellcode, wie im Folgenden dargestellt:</span><span class="sxs-lookup"><span data-stu-id="1f187-141">In Xcode, you would associate an event with a control by writing code and then associating that code with the control, often by control-dragging the button into the source code, like this:</span></span>

![Verknüpfen einer Schaltfläche mit einem Ereignis in Xcode](images/ios-to-uwp/xcode-add-button-event.png)

```swift
// Swift implementation.

@IBAction func buttonPressed(sender: UIButton) {
    
}
```

<span data-ttu-id="1f187-143">Visual Studio ist ähnlich aufgebaut.</span><span class="sxs-lookup"><span data-stu-id="1f187-143">Visual Studio is similar.</span></span> <span data-ttu-id="1f187-144">Rechts über den **Eigenschaften** befindet sich eine Schaltfläche mit einem Gewitterblitz.</span><span class="sxs-lookup"><span data-stu-id="1f187-144">At the top right of **Properties** is a lightning bolt button.</span></span> <span data-ttu-id="1f187-145">Hier werden dem ausgewählten Steuerelement zugeordnete mögliche Ereignisse wie folgt aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="1f187-145">This is where the possible events associated with the selected control are listed, like this:</span></span>

![Schaltflächenereignisliste in Visual Studio](images/ios-to-uwp/vs-button-event.png)

<span data-ttu-id="1f187-147">Um Code für das Click-Ereignis der Schaltfläche hinzuzufügen, wählen Sie im Bereich **Entwurf** zunächst die Schaltfläche aus.</span><span class="sxs-lookup"><span data-stu-id="1f187-147">To add code for the button's click event, first select the button in the **Design** pane.</span></span> <span data-ttu-id="1f187-148">Klicken Sie als Nächstes auf die Schaltfläche mit dem Gewitterblitz, und doppelklicken Sie auf das leere Feld neben **Click**.</span><span class="sxs-lookup"><span data-stu-id="1f187-148">Next, click the lightning bolt button, and double-click the empty box next to the name **Click**.</span></span> <span data-ttu-id="1f187-149">Visual Studio fügt dann das Ereignis „myButton\_Click“ dem Feld **Click** hinzu. Anschließend wird der entsprechende Ereignishandler zur Datei „MainPage.xaml.cs“ hinzugefügt und angezeigt, wie im Folgenden dargestellt.</span><span class="sxs-lookup"><span data-stu-id="1f187-149">Visual Studio then adds the event "myButton\_Click" to the **Click** box, and then adds and displays the corresponding event handler in the MainPage.xaml.cs file, like this.</span></span>

```csharp
private void myButton_Click(object sender, RoutedEventArgs e)
{

}
```

<span data-ttu-id="1f187-150">Jetzt verbinden wir das **TextBlock**-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="1f187-150">Let's now hook-up the **TextBlock** control.</span></span> <span data-ttu-id="1f187-151">In Xcode würden Sie die Schaltfläche bei gedrückter STRG-Taste in den Quellcode ziehen, um dem Steuerelement seine Definition zuzuordnen, wie hier gezeigt.</span><span class="sxs-lookup"><span data-stu-id="1f187-151">In Xcode, you would control-drag the button to the source code file to associate the control with its definition, like this.</span></span>

![Verknüpfen einer Bezeichnung mit der zugehörigen Definition in Xcode](images/ios-to-uwp/xcode-add-button-reference.png)

```swift
// Swift implentation.

@IBOutlet weak var myLabel : UILabel
```

<span data-ttu-id="1f187-153">In Visual Studio müssen Sie das Steuerelement nicht zuordnen, da dies immer automatisch erfolgt.</span><span class="sxs-lookup"><span data-stu-id="1f187-153">In Visual Studio, you don't need associated the control as this is always done for you.</span></span> <span data-ttu-id="1f187-154">Nun werden jedoch einige der Eigenschaften geändert:</span><span class="sxs-lookup"><span data-stu-id="1f187-154">Let's change some of the properties though:</span></span>

1.  <span data-ttu-id="1f187-155">Tippen Sie auf die Registerkarte der Datei „MainPage.xaml“.</span><span class="sxs-lookup"><span data-stu-id="1f187-155">Tap the MainPage.xaml file tab.</span></span>
2.  <span data-ttu-id="1f187-156">Tippen Sie im Bereich **Entwurf** auf das **TextBlock**-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="1f187-156">In the **Design** pane, tap the **TextBlock** control.</span></span>
3.  <span data-ttu-id="1f187-157">Tippen Sie im Bereich **Eigenschaften** auf die Schaltfläche mit dem Schraubenschlüssel, um die zugehörigen Eigenschaften anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="1f187-157">In the **Properties** pane, tap the wrench button to display its properties.</span></span>
4.  <span data-ttu-id="1f187-158">Ändern Sie im Feld **Name** den Eintrag "&lt;No Name&gt;" in "myLabel".</span><span class="sxs-lookup"><span data-stu-id="1f187-158">In the **Name** box, change "&lt;No Name&gt;" to "myLabel".</span></span>

![Fenster "Bezeichnungseigenschaften" in Visual Studio](images/ios-to-uwp/vs-label-properties.png)

<span data-ttu-id="1f187-160">Lassen Sie uns nun dem Click-Ereignis der Schaltfläche Code hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="1f187-160">Let's now add some code to the button's click event.</span></span> <span data-ttu-id="1f187-161">Tippen Sie dazu auf die Datei „MainPage.xaml.cs“, und fügen Sie dem myButton\_Click-Ereignishandler den folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="1f187-161">To do this, tap the MainPage.xaml.cs file, and add the following code to the myButton\_Click event handler.</span></span>

```csharp
private void myButton_Click(object sender, RoutedEventArgs e)
{
    // Add the following line of code.    
    myLabel.Text = "Hello, World!";
}
```

<span data-ttu-id="1f187-162">Dieser ist mit dem Code vergleichbar, den Sie in Swift schreiben:</span><span class="sxs-lookup"><span data-stu-id="1f187-162">This is similar to what you would write in Swift:</span></span>

```swift
@IBAction func buttonPressed(sender: UIButton) {
    myLabel.text = "Hello, World!"
}
```

<span data-ttu-id="1f187-163">Wählen Sie schließlich zum Ausführen der App das Menü **Debuggen** aus, und wählen Sie dann **Debuggen starten** (oder drücken Sie F5).</span><span class="sxs-lookup"><span data-stu-id="1f187-163">Finally, to run the app, select the **Debug** menu, and then select **Start Debugging** (or just press F5).</span></span> <span data-ttu-id="1f187-164">Nachdem die App gestartet wurde, klicken Sie auf die Schaltfläche „Press Me“. Sie werden feststellen, dass der Inhalt der Bezeichnung von „TextBlock“ in „Hello, World!“ geändert wurde, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="1f187-164">After the app starts, click the "Press Me" button, and see the label's contents change from "TextBlock" to "Hello, World!", as shown in the following figure.</span></span>

![Ausführungsergebnisse der ersten exemplarischen Vorgehensweise: Hello, World!](images/ios-to-uwp/vs-hello-world.png)

<span data-ttu-id="1f187-166">Wenn Sie die App beenden möchten, tippen Sie in Visual Studio auf das Menü **Debuggen**, und tippen Sie dann auf **Debuggen beenden** (oder drücken Sie einfach UMSCHALT+F5).</span><span class="sxs-lookup"><span data-stu-id="1f187-166">To quit the app, return to Visual Studio, tap the **Debug** menu, and then tap **Stop Debugging** (or just press SHIFT + F5).</span></span> <span data-ttu-id="1f187-167">Beachten Sie, dass Sie in Visual Studio die App auf vielen unterschiedlichen Geräten testen können.</span><span class="sxs-lookup"><span data-stu-id="1f187-167">Notice that Visual Studio lets you try the app in many different devices, to check how it will perform in each.</span></span>

## <a name="next-step"></a><span data-ttu-id="1f187-168">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="1f187-168">Next step</span></span>

[<span data-ttu-id="1f187-169">Erste Schritte: Allgemeine Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="1f187-169">Getting started: Common Controls</span></span>](getting-started-common-controls.md)

