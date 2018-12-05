---
title: Erste Schritte mit Animationen
ms.assetid: C1C3F5EA-B775-4700-9C45-695E78C16205
description: In diesem Projekt verschieben wir ein Rechteck, wenden einen Ausblendeeffekt an und blenden das Rechteck wieder ein
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: dc5e107fd343798698f5957c26d87a0d3ffe6625
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8694631"
---
# <a name="getting-started-animation"></a><span data-ttu-id="a20e2-104">Erste Schritte: Animationen</span><span class="sxs-lookup"><span data-stu-id="a20e2-104">Getting started: Animation</span></span>


## <a name="adding-animations"></a><span data-ttu-id="a20e2-105">Hinzufügen von Animationen</span><span class="sxs-lookup"><span data-stu-id="a20e2-105">Adding animations</span></span>

<span data-ttu-id="a20e2-106">In iOS werden Animationseffekte meist programmgesteuert erstellt.</span><span class="sxs-lookup"><span data-stu-id="a20e2-106">In iOS, you most often create animation effects programmatically.</span></span> <span data-ttu-id="a20e2-107">Sie könnten beispielsweise Animationen verwenden, die von den blockbasierten **animateWithDuration**-Methoden der **UIView**-Klasse oder den älteren, nicht blockbasierten Methoden bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="a20e2-107">For example, you might use animations provided by the block-based **UIView** class's **animateWithDuration** methods, or the older non-block based methods.</span></span> <span data-ttu-id="a20e2-108">Sie können auch explizit die **CALayer**-Klasse verwenden, um Ebenen zu animieren.</span><span class="sxs-lookup"><span data-stu-id="a20e2-108">Or, you might explicitly use the **CALayer** class to animate layers.</span></span> <span data-ttu-id="a20e2-109">Animationen in Windows-Apps können programmgesteuert erstellt werden. Sie können jedoch auch deklarativ mittels der Extensible Application Markup Language (XAML) definiert werden.</span><span class="sxs-lookup"><span data-stu-id="a20e2-109">Animations in Windows apps can be created programmatically, but they can also be defined declaratively with Extensible Application Markup Language (XAML).</span></span> <span data-ttu-id="a20e2-110">Sie können Microsoft Visual Studio zum direkten Bearbeiten von XAML-Code verwenden oder auch das Visual Studio-Tool **Blend**, das XAML-Code beim Arbeiten mit Animationen in einem Designer erstellt.</span><span class="sxs-lookup"><span data-stu-id="a20e2-110">You can use Microsoft Visual Studio to edit XAML code directly, but Visual Studio also comes with a tool called **Blend**, which creates XAML code for you as you work with animations in a designer.</span></span> <span data-ttu-id="a20e2-111">Mit Blend können Sie komplette VisualStudio-Projekte öffnen, entwerfen, erstellen und ausführen.</span><span class="sxs-lookup"><span data-stu-id="a20e2-111">In fact, Blend allows you to open, design, build, and run complete Visual Studio projects, graphically.</span></span> <span data-ttu-id="a20e2-112">In der folgenden exemplarischen Vorgehensweise können Sie diese Methode testen.</span><span class="sxs-lookup"><span data-stu-id="a20e2-112">The following walkthrough lets you try this out.</span></span>

<span data-ttu-id="a20e2-113">Erstellen Sie eine neue Universal Windows Platform (UWP)-App, und nennen Sie sie z.B. „SimpleAnimation“.</span><span class="sxs-lookup"><span data-stu-id="a20e2-113">Create a new Universal Windows Platform (UWP) app and name it something like "SimpleAnimation".</span></span> <span data-ttu-id="a20e2-114">In diesem Projekt verschieben wir ein Rechteck, wenden einen Ausblendeeffekt an und blenden es wieder ein</span><span class="sxs-lookup"><span data-stu-id="a20e2-114">In this project, we're going to move a rectangle, apply a fade effect, and then bring it back into view.</span></span> <span data-ttu-id="a20e2-115">In XAML basieren Animationen auf dem Konzept von *Storyboards* (nicht mit iOS-Storyboards zu verwechseln).</span><span class="sxs-lookup"><span data-stu-id="a20e2-115">Animations in XAML are based on the concept of *storyboards* (not to be confused with iOS storyboards).</span></span> <span data-ttu-id="a20e2-116">Bei Storyboards werden Änderungen von Eigenschaften mithilfe von *Keyframes* animiert.</span><span class="sxs-lookup"><span data-stu-id="a20e2-116">Storyboards use *keyframes* to animate property changes.</span></span>

<span data-ttu-id="a20e2-117">Klicken Sie mit der rechten Maustaste im **Projektmappen-Explorer** auf den Namen des Projekts, während das Projekt geöffnet ist, und wählen Sie **In Blend öffnen** oder **In Blend entwerfen** aus wie in der folgenden Abbildung gezeigt.</span><span class="sxs-lookup"><span data-stu-id="a20e2-117">With your project open, in **Solution Explorer**, right-click the project's name and then select **Open in Blend** or **Design in Blend**, as shown in the following figure.</span></span> <span data-ttu-id="a20e2-118">Die Ausführung von Visual Studio wird im Hintergrund fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="a20e2-118">Visual Studio continues to run in the background.</span></span>

![Menübefehl „In Blend öffnen“](images/ios-to-uwp/vs-open-in-blend.png)

<span data-ttu-id="a20e2-120">Nachdem Blend gestartet wurde, sollte die Anzeige der folgenden Abbildung ähnlich sein.</span><span class="sxs-lookup"><span data-stu-id="a20e2-120">After Blend starts, you should see something similar to the following figure.</span></span>

![Blend-Entwicklungsumgebung](images/ios-to-uwp/blend-1.png)

<span data-ttu-id="a20e2-122">Doppelklicken Sie auf der linken Seite auf **MainPage.xaml** im **Projektmappen-Explorer**.</span><span class="sxs-lookup"><span data-stu-id="a20e2-122">Double-click on **MainPage.xaml** in the **Solution Explorer** on the left hand side.</span></span> <span data-ttu-id="a20e2-123">Wählen Sie als Nächstes auf der vertikalen Toolleiste am Rand der zentralen **Entwurfsansicht** das Tool **Rechteck** aus, und zeichnen Sie ein Rechteck in der **Entwurfsansicht** wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="a20e2-123">Next, from the vertical strip of tools on the edge of the central **Design View**, select the **Rectangle** tool, and then draw a rectangle in **Design View**, as shown in the following figure.</span></span>

![Hinzufügen eines Rechtecks zur Entwurfsansicht](images/ios-to-uwp/blend-2.png)

<span data-ttu-id="a20e2-125">Wenn Sie das Rechteck grün zeichnen möchten, klicken Sie im Fenster **Eigenschaften** im Bereich **Pinsel** auf die Schaltfläche **Pinsel mit Volltonfarbe**. Klicken Sie dann auf das Symbol **Farbformatpipette**.</span><span class="sxs-lookup"><span data-stu-id="a20e2-125">To make the rectangle green, look in the **Properties** window, and in the **Brush** area, click on the **Solid color brush** button, and then click the **Color eyedropper** icon.</span></span> <span data-ttu-id="a20e2-126">Klicken Sie auf eine beliebige Stelle im grünen Farbtonband.</span><span class="sxs-lookup"><span data-stu-id="a20e2-126">Click somewhere in the green band of hues.</span></span>

<span data-ttu-id="a20e2-127">Tippen Sie im Fenster **Objekte und Zeitachsen** auf das Plussymbol (**Neu**) und dann auf **OK**, um mit der Animation des Rechtecks zu beginnen, wie in der folgenden Abbildung gezeigt.</span><span class="sxs-lookup"><span data-stu-id="a20e2-127">To begin animating the rectangle, in the **Objects and Timeline** window, tap the plus symbol (**New**) button as shown in the following figure, and then tap **OK**.</span></span>

![Hinzufügen eines Storyboards](images/ios-to-uwp/blend-3.png)

<span data-ttu-id="a20e2-129">Ein Storyboard wird im Fenster **Objekte und Zeitachsen** angezeigt (möglicherweise müssen Sie die Größe der Ansicht anpassen, damit es ordnungsgemäß angezeigt wird).</span><span class="sxs-lookup"><span data-stu-id="a20e2-129">A storyboard appears in the **Objects and Timeline** window (you may need to resize the view to see it properly).</span></span> <span data-ttu-id="a20e2-130">Die Anzeige der **Designansicht** ändert sich, um anzuzeigen, dass die Zeitachsenaufzeichnung für Storyboard1 aktiviert ist\*\*\*\*.</span><span class="sxs-lookup"><span data-stu-id="a20e2-130">The **Design View** display changes to show that **Storyboard1 timeline recording is on**.</span></span> <span data-ttu-id="a20e2-131">Tippen Sie im Fenster **Objekte und Zeitachsen** über dem gelben Pfeil auf die Schaltfläche **Keyframe aufzeichnen**, um den aktuellen Status des Rechtecks zu erfassen, wie in der folgenden Abbildung gezeigt.</span><span class="sxs-lookup"><span data-stu-id="a20e2-131">To capture the current state of the rectangle, in the **Objects and Timeline** window, tap the **Record Keyframe** button just above the yellow arrow, as shown in the following figure.</span></span>

![Aufzeichnen eines Keyframes](images/ios-to-uwp/blend-4.png)

<span data-ttu-id="a20e2-133">Lassen Sie uns das Rechteck nun verschieben und ausblenden.</span><span class="sxs-lookup"><span data-stu-id="a20e2-133">Now, let's move the rectangle and fade it away.</span></span> <span data-ttu-id="a20e2-134">Ziehen Sie dazu den orangefarbenen/gelben Pfeil auf die 2-Sekunden-Position, und verschieben Sie dann das Rechteck leicht nach rechts.</span><span class="sxs-lookup"><span data-stu-id="a20e2-134">To do this, drag the orange/yellow arrow to the 2-second position, and then move your green rectangle slightly to the right.</span></span> <span data-ttu-id="a20e2-135">Ändern Sie dann wie in der folgenden Abbildung gezeigt im Fenster **Eigenschaften** im Bereich **Darstellung** die Eigenschaft **Undurchsichtigkeit** in den Wert **0**.</span><span class="sxs-lookup"><span data-stu-id="a20e2-135">Then, in the **Properties** window, in the **Appearance** area, change the **Opacity** property to **0**, as shown in the following figure.</span></span> <span data-ttu-id="a20e2-136">Tippen Sie auf die Schaltfläche **Wiedergeben** im Storyboard-Bereich, um eine Vorschau der Animation anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a20e2-136">To preview the animation, tap the **Play** button in the Storyboard panel.</span></span>

![Fenster „Eigenschaften“ und Schaltfläche „Wiedergeben“](images/ios-to-uwp/blend-5.png)

<span data-ttu-id="a20e2-138">Als Nächstes möchten wir das Rechteck wieder einblenden.</span><span class="sxs-lookup"><span data-stu-id="a20e2-138">Next, let's bring the rectangle back into view.</span></span> <span data-ttu-id="a20e2-139">Doppelklicken Sie im Fenster **Objekte und Zeitachsen** auf **Storyboard1**.</span><span class="sxs-lookup"><span data-stu-id="a20e2-139">In the **Objects and Timeline** window, double-click **Storyboard1**.</span></span> <span data-ttu-id="a20e2-140">Wählen Sie dann wie in der folgenden Abbildung gezeigt im Fenster **Eigenschaften** im Bereich **Allgemein** **AutoReverse** aus.</span><span class="sxs-lookup"><span data-stu-id="a20e2-140">Then, in the **Properties** window, in the **Common** area, select **AutoReverse**, as shown in the following figure.</span></span>

![Auswählen eines Storyboards](images/ios-to-uwp/blend-6.png)

<span data-ttu-id="a20e2-142">Klicken Sie schließlich auf die Schaltfläche **Wiedergeben**, um das Ergebnis zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="a20e2-142">Finally, click on the **Play** button to see what happens.</span></span>

<span data-ttu-id="a20e2-143">Sie können das Projekt erstellen und ausführen, indem Sie auf die grüne Schaltfläche „Ausführen“ am oberen Rand des Fensters klicken (oder F5 drücken).</span><span class="sxs-lookup"><span data-stu-id="a20e2-143">You can build and run the project by clicking on the green run button at the top of the window (or just press F5).</span></span> <span data-ttu-id="a20e2-144">Wenn Sie dies tun, wird das Projekt tatsächlich erstellt und ausgeführt, das grüne Rechteck ist jedoch weiterhin vorhanden.</span><span class="sxs-lookup"><span data-stu-id="a20e2-144">If you do this, you'll see your project will indeed build and run, but the green rectangle will stubbornly sit perfectly still, like a toddler denied candy in a supermarket aisle.</span></span> <span data-ttu-id="a20e2-145">Zum Starten der Animation müssen Sie dem Projekt eine Zeile mit Code hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="a20e2-145">To start the animation, you'll need to add a line of code to the project.</span></span> <span data-ttu-id="a20e2-146">Gehen Sie dazu wie folgt vor.</span><span class="sxs-lookup"><span data-stu-id="a20e2-146">Here's how.</span></span>

<span data-ttu-id="a20e2-147">Speichern Sie das Projekt, indem Sie das Menü **Datei** Menü öffnen und **MainPage.xaml speichern** wählen.</span><span class="sxs-lookup"><span data-stu-id="a20e2-147">Save the project, by opening the **File** menu, and selecting **Save MainPage.xaml**.</span></span> <span data-ttu-id="a20e2-148">Kehren Sie zu Visual Studio zurück.</span><span class="sxs-lookup"><span data-stu-id="a20e2-148">Return to Visual Studio.</span></span> <span data-ttu-id="a20e2-149">Wenn in Visual Studio ein Dialogfeld mit der Frage angezeigt wird, ob Sie die geänderte Datei erneut laden möchten, wählen Sie **Ja**.</span><span class="sxs-lookup"><span data-stu-id="a20e2-149">If Visual Studio displays a dialog box asking whether you want to reload the modified file, select **Yes**.</span></span> <span data-ttu-id="a20e2-150">Doppelklicken Sie zum Öffnen auf die Datei **MainPage.xaml.cs** unter **MainPage.xaml**, und fügen Sie folgenden Code direkt über der public MainPage()-Methode hinzu:</span><span class="sxs-lookup"><span data-stu-id="a20e2-150">Double-click the **MainPage.xaml.cs** file, which is hidden under **MainPage.xaml**, to open it, and add the following code just above the public MainPage() method:</span></span>

```csharp
protected override void OnNavigatedTo(NavigationEventArgs e)
{
    // Add the following line of code.
    Storyboard1.Begin();
}
```

<span data-ttu-id="a20e2-151">Führen Sie das Projekt erneut aus, und sehen Sie sich die Animation des Rechtecks an.</span><span class="sxs-lookup"><span data-stu-id="a20e2-151">Run the project again, and watch the rectangle animate.</span></span> <span data-ttu-id="a20e2-152">Fertig!</span><span class="sxs-lookup"><span data-stu-id="a20e2-152">Hurrah!</span></span>

<span data-ttu-id="a20e2-153">Wenn Sie die Datei MainPage.xaml in der **XAML**-Ansicht öffnen, können Sie den XAML-Code sehen, den Blend für Sie hinzugefügt hat, während Sie im Designer gearbeitet haben.</span><span class="sxs-lookup"><span data-stu-id="a20e2-153">If you open the MainPage.xaml file, in **XAML** view, you'll see the XAML code that Blend added for you as you worked in the designer.</span></span> <span data-ttu-id="a20e2-154">Sehen Sie sich insbesondere den Code in den `<Storyboard>`- und `<Rectangle>`-Elementen an.</span><span class="sxs-lookup"><span data-stu-id="a20e2-154">In particular, look at the code in the `<Storyboard>` and `<Rectangle>` elements.</span></span> <span data-ttu-id="a20e2-155">Der folgende Code zeigt ein Beispiel.</span><span class="sxs-lookup"><span data-stu-id="a20e2-155">The following code shows an example.</span></span> <span data-ttu-id="a20e2-156">Auslassungspunkte stellen Code ohne Bezug dar, der aus Platzgründen ausgelassen wird. Zur besseren Lesbarkeit des Codes wurden Zeilenumbrüche hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a20e2-156">Ellipses indicate unrelated code omitted for brevity, and line breaks have been added for code readability.)</span></span>

```xml
...
<Storyboard 
        x:Name="Storyboard1" 
        AutoReverse="True">
    <DoubleAnimationUsingKeyFrames 
            Storyboard.TargetProperty="(UIElement.RenderTransform).(CompositeTransform.TranslateX)"
            Storyboard.TargetName="rectangle">
        <EasingDoubleKeyFrame 
                KeyTime="0" 
                Value="0"/>
        <EasingDoubleKeyFrame 
                KeyTime="0:0:2" 
                Value="185.075"/>
    </DoubleAnimationUsingKeyFrames>
    <DoubleAnimationUsingKeyFrames 
            Storyboard.TargetProperty="(UIElement.RenderTransform).(CompositeTransform.TranslateY)" 
            Storyboard.TargetName="rectangle">
        <EasingDoubleKeyFrame 
                KeyTime="0" 
                Value="0"/>
        <EasingDoubleKeyFrame 
                KeyTime="0:0:2" 
                Value="2.985"/>
    </DoubleAnimationUsingKeyFrames>
    <DoubleAnimationUsingKeyFrames 
            Storyboard.TargetProperty="(UIElement.Opacity)" 
            Storyboard.TargetName="rectangle">
        <EasingDoubleKeyFrame 
                KeyTime="0" 
                Value="1"/>
        <EasingDoubleKeyFrame 
                KeyTime="0:0:2"
                Value="0"/>
    </DoubleAnimationUsingKeyFrames>
</Storyboard>
...
<Rectangle 
        x:Name="rectangle" 
        Fill="#FF00FF63" 
        HorizontalAlignment="Left" 
        Height="122" 
        Margin="151,312,0,0" 
        Stroke="Black" 
        VerticalAlignment="Top" 
        Width="239" 
        RenderTransformOrigin="0.5,0.5">
    <Rectangle.RenderTransform>
        <CompositeTransform/>
    </Rectangle.RenderTransform>
</Rectangle>
...
```

<span data-ttu-id="a20e2-157">Sie können diesen XAML-Code manuell bearbeiten oder zu Blend zurückkehren, um dort weiter an diesem zu arbeiten.</span><span class="sxs-lookup"><span data-stu-id="a20e2-157">You can edit this XAML manually, or return to Blend to continue working on it there.</span></span> <span data-ttu-id="a20e2-158">Mit Blend können Sie spielerisch interessante Benutzeroberflächen erstellen und sie mit einem Grafiktool animieren, was die Entwicklung erheblich beschleunigt.</span><span class="sxs-lookup"><span data-stu-id="a20e2-158">Blend makes it fun to create interesting user interfaces, and the ability to animate them using a graphical tool can dramatically speed up development time.</span></span> <span data-ttu-id="a20e2-159">Weitere Informationen zu Animationen finden Sie unter [Übersicht über Animationen](https://msdn.microsoft.com/library/windows/apps/mt187350).</span><span class="sxs-lookup"><span data-stu-id="a20e2-159">For more info about animations, see [Animations overview](https://msdn.microsoft.com/library/windows/apps/mt187350).</span></span>

<span data-ttu-id="a20e2-160">**Hinweis:** Informationen zu Animationen für <span class="legacy-term">UWP-apps mit JavaScript und HTML</span>finden Sie unter [Animieren der Benutzeroberfläche (HTML)](https://msdn.microsoft.com/library/windows/apps/hh465165).</span><span class="sxs-lookup"><span data-stu-id="a20e2-160">**Note**For info about animations for <span class="legacy-term">UWP apps using JavaScript and HTML</span>, see [Animating your UI (HTML)](https://msdn.microsoft.com/library/windows/apps/hh465165).</span></span>

### <a name="next-step"></a><span data-ttu-id="a20e2-161">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="a20e2-161">Next step</span></span>

[<span data-ttu-id="a20e2-162">Erste Schritte: Was kommt als Nächstes?</span><span class="sxs-lookup"><span data-stu-id="a20e2-162">Getting started: What next?</span></span>](getting-started-what-next.md)
