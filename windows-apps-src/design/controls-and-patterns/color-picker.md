---
Description: A color picker lets a user browse through and select colors.
title: Farbwähler
label: Color Picker
template: detail.hbs
ms.date: 05/19/2017
ms.topic: article
keywords: Windows 10, UWP
pm-contact: kisai
design-contact: ksulliv
dev-contact: llongley
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 1025af31a4827c2369a9555c3bd1a6c4404c5959
ms.sourcegitcommit: a60ab85e9f2f9690e0141050ec3aa51f18ec61ec
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/30/2019
ms.locfileid: "9037212"
---
# <a name="color-picker"></a><span data-ttu-id="1a758-103">Farbwähler</span><span class="sxs-lookup"><span data-stu-id="1a758-103">Color picker</span></span>

<span data-ttu-id="1a758-104">Mithilfe eines Farbwählers können Benutzer Farben suchen und auswählen.</span><span class="sxs-lookup"><span data-stu-id="1a758-104">A color picker is used to browse through and select colors.</span></span> <span data-ttu-id="1a758-105">Standardmäßig können sie durch die Farben eines Farbspektrums navigieren oder eine bestimmte Farbe in einem Textfeld des Typs „Rot-Grün-Blau (RGB)“, „Wert für Farbton/Sättigung“ oder „Hexadezimal“ angeben.</span><span class="sxs-lookup"><span data-stu-id="1a758-105">By default, it lets a user navigate through colors on a color spectrum, or specify a color in either Red-Green-Blue (RGB), Hue-Saturation-Value (HSV), or Hexadecimal textboxes.</span></span>

> <span data-ttu-id="1a758-106">**Wichtige APIs:** [Klasse „ColorPicker“](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.colorpicker), [Eigenschaft „Color“](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.colorpicker.Color), [Ereignis „ColorChanged“](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.colorpicker.ColorChanged)</span><span class="sxs-lookup"><span data-stu-id="1a758-106">**Important APIs**: [ColorPicker class](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.colorpicker), [Color property](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.colorpicker.Color), [ColorChanged event](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.colorpicker.ColorChanged)</span></span>

![Ein Farbwähler in Standardausführung](images/color-picker-default.png)


## <a name="is-this-the-right-control"></a><span data-ttu-id="1a758-108">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="1a758-108">Is this the right control?</span></span>

<span data-ttu-id="1a758-109">Mithilfe eines Farbwählers können Benutzer in Ihrer App Farben auswählen.</span><span class="sxs-lookup"><span data-stu-id="1a758-109">Use the color picker to let a user select colors in your app.</span></span> <span data-ttu-id="1a758-110">Beispielsweise können sie so Farbeinstellungen wie Textfarben, Hintergrundfarben oder App-Farbdesigns ändern.</span><span class="sxs-lookup"><span data-stu-id="1a758-110">For example, use it to change color settings, such as font colors, background, or app theme colors.</span></span>

<span data-ttu-id="1a758-111">Falls Ihre App zum Zeichnen oder für andere stiftbasierte Aufgaben gedacht ist, sollten Sie neben dem Farbwähler auch die Implementierung von [Steuerelementen für Freihandeingaben](inking-controls.md) in Betracht ziehen.</span><span class="sxs-lookup"><span data-stu-id="1a758-111">If your app is for drawing or similar tasks using pen, consider using [Inking controls](inking-controls.md) along with the color picker.</span></span>

## <a name="examples"></a><span data-ttu-id="1a758-112">Beispiele</span><span class="sxs-lookup"><span data-stu-id="1a758-112">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="1a758-113">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="1a758-113">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="1a758-114">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/ColorPicker">die App zu öffnen und ColorPicker in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="1a758-114">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/ColorPicker">open the app and see the ColorPicker in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="1a758-115">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="1a758-115">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Xaml-Controls-Gallery"><span data-ttu-id="1a758-116">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="1a758-116">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="create-a-color-picker"></a><span data-ttu-id="1a758-117">Erstellen eines Farbwählers</span><span class="sxs-lookup"><span data-stu-id="1a758-117">Create a color picker</span></span>

<span data-ttu-id="1a758-118">In diesem Beispiel zeigen wir Ihnen, wie Sie einen Standardfarbwähler in XAML erstellen können.</span><span class="sxs-lookup"><span data-stu-id="1a758-118">This example shows how to create a default color picker in XAML.</span></span>

```xaml
<ColorPicker x:Name="myColorPicker"/>
```

<span data-ttu-id="1a758-119">Der Farbwähler zeigt standardmäßig eine Vorschau der ausgewählten Farbe in dem rechteckigen Balken neben dem Farbspektrum an.</span><span class="sxs-lookup"><span data-stu-id="1a758-119">By default, the color picker shows a preview of the chosen color on the rectangular bar beside the color spectrum.</span></span> <span data-ttu-id="1a758-120">Um auf die ausgewählte Farbe zuzugreifen und sie in Ihrer App zu verwenden, können Sie entweder das Ereignis [ColorChanged](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.colorpicker.ColorChanged) oder die Eigenschaft [Color](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.colorpicker.Color) verwenden.</span><span class="sxs-lookup"><span data-stu-id="1a758-120">You can use either the [ColorChanged](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.colorpicker.ColorChanged) event or the [Color](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.colorpicker.Color) property to access the selected color and use it in your app.</span></span> <span data-ttu-id="1a758-121">Detaillierten Code finden Sie in den nachfolgenden Beispielen.</span><span class="sxs-lookup"><span data-stu-id="1a758-121">See the following examples for detailed code.</span></span>

### <a name="bind-to-the-chosen-color"></a><span data-ttu-id="1a758-122">Binden an die ausgewählte Farbe</span><span class="sxs-lookup"><span data-stu-id="1a758-122">Bind to the chosen color</span></span>

<span data-ttu-id="1a758-123">Soll die Farbauswahl sofort wirksam werden, können Sie sie entweder per Datenbindung an die Eigenschaft „Color“ binden oder über das Ereignis „ColorChanged“ in Ihrem Code auf die ausgewählte Farbe zugreifen.</span><span class="sxs-lookup"><span data-stu-id="1a758-123">When the color selection should take effect immediately, you can either use databinding to bind to the Color property, or handle the ColorChanged event to access the selected color in your code.</span></span>

<span data-ttu-id="1a758-124">In diesem Beispiel binden Sie die Eigenschaft „Color“ einer als Füllung für ein Rechteck verwendeten Klasse „SolidColorBrush“ direkt an die im Farbwähler ausgewählte Farbe.</span><span class="sxs-lookup"><span data-stu-id="1a758-124">In this example, you bind the Color property of a SolidColorBrush that’s used as the Fill for a Rectangle directly to the color picker’s selected color.</span></span> <span data-ttu-id="1a758-125">Jede Änderung am Farbwähler zieht eine Liveänderung an der gebundenen Eigenschaft nach sich.</span><span class="sxs-lookup"><span data-stu-id="1a758-125">Any change to the color picker results in a live change to the bound property.</span></span>

```xaml
<ColorPicker x:Name="myColorPicker"
             ColorSpectrumShape=”Ring”
             IsColorPreviewVisible="False"
             IsColorChannelTextInputVisible="False"
             IsHexInputVisible="False"/>

<Rectangle Height="50" Width="50">
    <Rectangle.Fill>
        <SolidColorBrush Color="{x:Bind myColorPicker.Color, Mode=OneWay}"/>
    </Rectangle.Fill>
</Rectangle>
```

<span data-ttu-id="1a758-126">In diesem Beispiel wird ein vereinfachter Farbwähler verwendet, der nur aus einem kreisförmigen Spektrum und einem Schieberegler besteht. Dies ist eine gängige unkomplizierte Ausführung eines Farbwählers.</span><span class="sxs-lookup"><span data-stu-id="1a758-126">This example uses a simplified color picker with just the circle and the slider, which is a common "casual" color picking experience.</span></span> <span data-ttu-id="1a758-127">Lässt sich die Farbänderung in Echtzeit an dem jeweils betroffenen Objekt nachvollziehen, muss kein Farbvorschaubalken angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="1a758-127">When the color change can be seen and happens in real-time on the affected object, you don't need to show the color preview bar.</span></span> <span data-ttu-id="1a758-128">Weitere Informationen finden Sie im Abschnitt *Anpassen des Farbwählers*.</span><span class="sxs-lookup"><span data-stu-id="1a758-128">See the *Customize the color picker* section for more info.</span></span>

### <a name="save-the-chosen-color"></a><span data-ttu-id="1a758-129">Speichern der ausgewählten Farbe</span><span class="sxs-lookup"><span data-stu-id="1a758-129">Save the chosen color</span></span>

<span data-ttu-id="1a758-130">In einigen Fällen soll die Farbänderung nicht direkt angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="1a758-130">In some cases, you don't want to apply the color change immediately.</span></span> <span data-ttu-id="1a758-131">Wenn Sie den Farbwähler beispielsweise in einem Flyout hosten, sollten Sie die ausgewählte Farbe erst anwenden, nachdem der Benutzer die Auswahl bestätigt oder das Flyout geschlossen hat.</span><span class="sxs-lookup"><span data-stu-id="1a758-131">For example, when you host a color picker in a flyout, we recomend that you apply the selected color only after the user confirms the selection or closes the flyout.</span></span> <span data-ttu-id="1a758-132">Der ausgewählte Farbwert lässt sich auch zur späteren Verwendung speichern.</span><span class="sxs-lookup"><span data-stu-id="1a758-132">You can also save the selected color value to use later.</span></span>

<span data-ttu-id="1a758-133">In diesem Beispiel wird ein Farbwähler in einem Flyout mit „Bestätigen“-Schaltfläche und „Abbrechen“-Schaltfläche gehostet.</span><span class="sxs-lookup"><span data-stu-id="1a758-133">In this example, you host a color picker in a Flyout with Confirm and Cancel buttons.</span></span> <span data-ttu-id="1a758-134">Sobald der Benutzer seine Farbauswahl bestätigt, wird die ausgewählte Farbe gespeichert und kann später in der App verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1a758-134">When the user confirms their color choice, you save the selected color to use later in your app.</span></span>

```xaml
<Page.Resources>
    <Flyout x:Key="myColorPickerFlyout">
        <RelativePanel>
            <ColorPicker x:Name="myColorPicker"
                         IsColorChannelTextInputVisible="False"
                         IsHexInputVisible="False"/>

            <Grid RelativePanel.Below="myColorPicker"
                  RelativePanel.AlignLeftWithPanel="True"
                  RelativePanel.AlignRightWithPanel="True">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition/>
                    <ColumnDefinition/>
                </Grid.ColumnDefinitions>
                <Button Content="OK" Click="confirmColor_Click"
                        Margin="0,12,2,0" HorizontalAlignment="Stretch"/>
                <Button Content="Cancel" Click="cancelColor_Click"
                        Margin="2,12,0,0" HorizontalAlignment="Stretch"
                        Grid.Column="1"/>
            </Grid>
        </RelativePanel>
    </Flyout>
</Page.Resources>

<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Button x:Name="colorPickerButton"
            Content="Pick a color"
            Flyout="{StaticResource myColorPickerFlyout}"/>
</Grid>
```

```csharp
private Color mycolor;

private void confirmColor_Click(object sender, RoutedEventArgs e)
{
    // Assign the selected color to a variable to use outside the popup.
    myColor = myColorPicker.Color;

    // Close the Flyout.
    colorPickerButton.Flyout.Hide();
}

private void cancelColor_Click(object sender, RoutedEventArgs e)
{
    // Close the Flyout.
    colorPickerButton.Flyout.Hide();
}
```

### <a name="configure-the-color-picker"></a><span data-ttu-id="1a758-135">Konfigurieren des Farbwählers</span><span class="sxs-lookup"><span data-stu-id="1a758-135">Configure the color picker</span></span>

<span data-ttu-id="1a758-136">Zur Farbauswahl sind nicht alle Felder notwendig, daher ist der Farbwähler flexibel.</span><span class="sxs-lookup"><span data-stu-id="1a758-136">Not all fields are necessary to let a user pick a color, so the color picker is flexible.</span></span> <span data-ttu-id="1a758-137">Sie haben eine Vielzahl von Optionen zur Verfügung, über die Sie dieses Steuerelement an Ihre Anforderungen anpassen können.</span><span class="sxs-lookup"><span data-stu-id="1a758-137">It provides a variety of options that let you configure the control to fit your needs.</span></span>

<span data-ttu-id="1a758-138">Benötigt der Benutzer keine präzise Kontrolle, beispielsweise bei der Auswahl der Textmarkerfarbe in einer Notizen-App, können Sie eine vereinfachte Benutzeroberfläche verwenden.</span><span class="sxs-lookup"><span data-stu-id="1a758-138">For example, when the user doesn't need precise control, like picking a highlighter color in a note taking app, you can use a simplified UI.</span></span> <span data-ttu-id="1a758-139">Sie können die Texteingabefelder ausblenden und das Farbspektrum als Kreis darstellen.</span><span class="sxs-lookup"><span data-stu-id="1a758-139">You can hide the text entry fields and change the color spectrum to a circle.</span></span>

<span data-ttu-id="1a758-140">Benötigt der Benutzer präzise Kontrolle, beispielsweise in einer Grafikdesign-App, können Sie sowohl Schieberegler als auch Texteingabefelder für jeden Aspekt der Farbe anzeigen.</span><span class="sxs-lookup"><span data-stu-id="1a758-140">When the user does need precise control, like in a graphic design app, you can show both sliders and text entry fields for each aspect of the color.</span></span>

#### <a name="show-the-circle-spectrum"></a><span data-ttu-id="1a758-141">Anzeigen eines kreisförmigen Spektrums</span><span class="sxs-lookup"><span data-stu-id="1a758-141">Show the circle spectrum</span></span>

<span data-ttu-id="1a758-142">In diesem Beispiel wird demonstriert, wie Sie den Farbwähler mithilfe der Eigenschaft [ColorSpectrumShape](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.colorpicker.ColorSpectrumShape) so konfigurieren können, dass statt des standardmäßigen quadratischen Farbspektrums ein kreisförmiges Farbspektrum angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="1a758-142">This example shows how to use the [ColorSpectrumShape](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.colorpicker.ColorSpectrumShape) property to configure the color picker to use a circular spectrum instead of the default square.</span></span>

```xaml
<ColorPicker x:Name="myColorPicker"
             ColorSpectrumShape="Ring"/>
```

![Farbwähler mit kreisförmigem Spektrum](images/color-picker-ring.png)

<span data-ttu-id="1a758-144">Bei der Entscheidung zwischen einem quadratischen und einem kreisförmigen Farbspektrum ist das Hauptkriterium die Genauigkeit.</span><span class="sxs-lookup"><span data-stu-id="1a758-144">When you must choose between the square and circle color spectrum, a primary consideration is accuracy.</span></span> <span data-ttu-id="1a758-145">In einem quadratischen Farbspektrum hat der Benutzer mehr Kontrolle über die Farbauswahl, da ein größerer Teil des Farbraums angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="1a758-145">A user has more control when they select a specific color using a square because more of the color gamut is shown.</span></span> <span data-ttu-id="1a758-146">Ein kreisförmiges Spektrum ist eher für eine schnelle, unkomplizierte Farbauswahl gedacht.</span><span class="sxs-lookup"><span data-stu-id="1a758-146">You should consider the circle spectrum as more of the "casual" color choosing experience.</span></span>

#### <a name="show-the-alpha-channel"></a><span data-ttu-id="1a758-147">Anzeigen des Alphakanals</span><span class="sxs-lookup"><span data-stu-id="1a758-147">Show the alpha channel</span></span>

<span data-ttu-id="1a758-148">In diesem Beispiel implementieren Sie im Farbwähler einen Schieberegler und ein Textfeld für die Deckkraft.</span><span class="sxs-lookup"><span data-stu-id="1a758-148">In this example, you enable an opacity slider and textbox on the color picker.</span></span>

```xaml
<ColorPicker x:Name="myColorPicker"
             IsAlphaEnabled="True"/>
```

![Farbwähler mit „IsAlphaEnabled“ auf „true“](images/color-picker-alpha.png)

#### <a name="show-a-simple-picker"></a><span data-ttu-id="1a758-150">Anzeigen eines einfachen Wählers</span><span class="sxs-lookup"><span data-stu-id="1a758-150">Show a simple picker</span></span>

<span data-ttu-id="1a758-151">In diesem Beispiel wird demonstriert, wie Sie den Farbwähler mit einer einfachen Benutzeroberfläche für die schnelle und unkomplizierte Verwendung konfigurieren können.</span><span class="sxs-lookup"><span data-stu-id="1a758-151">This example shows how to configure the color picker with a simple UI for "casual" use.</span></span> <span data-ttu-id="1a758-152">Sie implementieren das kreisförmige Spektrum und blenden die standardmäßigen Texteingabefelder aus.</span><span class="sxs-lookup"><span data-stu-id="1a758-152">You show the circular spectrum and hide the default text input boxes.</span></span> <span data-ttu-id="1a758-153">Lässt sich die Farbänderung in Echtzeit an dem jeweils betroffenen Objekt nachvollziehen, muss kein Farbvorschaubalken angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="1a758-153">When the color change can be seen and happens in real-time on the affected object, you don't need to show the color preview bar.</span></span> <span data-ttu-id="1a758-154">Andernfalls sollte die Farbvorschau sichtbar sein.</span><span class="sxs-lookup"><span data-stu-id="1a758-154">Otherwise, you should leave the color preview visible.</span></span>

```xaml
<ColorPicker x:Name="myColorPicker"
             ColorSpectrumShape="Ring"
             IsColorPreviewVisible="False"
             IsColorChannelTextInputVisible="False"
             IsHexInputVisible="False"/>
```

![Ein einfacher Farbwähler](images/color-picker-casual.png)

#### <a name="show-or-hide-additional-features"></a><span data-ttu-id="1a758-156">Anzeigen oder Ausblenden von zusätzlichen Funktionen</span><span class="sxs-lookup"><span data-stu-id="1a758-156">Show or hide additional features</span></span>

<span data-ttu-id="1a758-157">In der Tabelle unten sind alle Optionen aufgeführt, die Sie zur Konfiguration des Steuerelements „ColorPicker“ verwenden können.</span><span class="sxs-lookup"><span data-stu-id="1a758-157">This table shows all the options you can use to configure the ColorPicker control.</span></span>

<span data-ttu-id="1a758-158">Funktion</span><span class="sxs-lookup"><span data-stu-id="1a758-158">Feature</span></span> | <span data-ttu-id="1a758-159">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="1a758-159">Properties</span></span>
--------|-----------
<span data-ttu-id="1a758-160">Farbspektrum</span><span class="sxs-lookup"><span data-stu-id="1a758-160">Color spectrum</span></span> | <span data-ttu-id="1a758-161">IsColorSpectrumVisible, ColorSpectrumShape, ColorSpectrumComponents</span><span class="sxs-lookup"><span data-stu-id="1a758-161">IsColorSpectrumVisible, ColorSpectrumShape, ColorSpectrumComponents</span></span>
<span data-ttu-id="1a758-162">Farbvorschau</span><span class="sxs-lookup"><span data-stu-id="1a758-162">Color preview</span></span> | <span data-ttu-id="1a758-163">IsColorPreviewVisible</span><span class="sxs-lookup"><span data-stu-id="1a758-163">IsColorPreviewVisible</span></span>
<span data-ttu-id="1a758-164">Farbwerte</span><span class="sxs-lookup"><span data-stu-id="1a758-164">Color values</span></span>| <span data-ttu-id="1a758-165">IsColorSliderVisible, IsColorChannelTextInputVisible</span><span class="sxs-lookup"><span data-stu-id="1a758-165">IsColorSliderVisible, IsColorChannelTextInputVisible</span></span>
<span data-ttu-id="1a758-166">Deckkraftwerte</span><span class="sxs-lookup"><span data-stu-id="1a758-166">Opacity values</span></span> | <span data-ttu-id="1a758-167">IsAlphaEnabled, IsAlphaSliderVisible, IsAlphaTextInputVisible</span><span class="sxs-lookup"><span data-stu-id="1a758-167">IsAlphaEnabled, IsAlphaSliderVisible, IsAlphaTextInputVisible</span></span>
<span data-ttu-id="1a758-168">Hexwerte</span><span class="sxs-lookup"><span data-stu-id="1a758-168">Hex values</span></span> | <span data-ttu-id="1a758-169">IsHexInputVisible</span><span class="sxs-lookup"><span data-stu-id="1a758-169">IsHexInputVisible</span></span>

> [!NOTE]
> <span data-ttu-id="1a758-170">Das Textfeld und der Schieberegler für die Deckkraft werden nur angezeigt, wenn „AlphaEnabled“ auf **true** gesetzt ist.</span><span class="sxs-lookup"><span data-stu-id="1a758-170">IsAlphaEnabled must be **true** in order to show the opacity textbox and slider.</span></span> <span data-ttu-id="1a758-171">Dann können Sie die Sichtbarkeit der Eingabesteuerelemente mithilfe der Eigenschaften „IsAlphaTextInputVisible“ und „IsAlphaSliderVisible“ anpassen.</span><span class="sxs-lookup"><span data-stu-id="1a758-171">The visibility of the input controls can then be modified using IsAlphaTextInputVisible and IsAlphaSliderVisible properties.</span></span> <span data-ttu-id="1a758-172">Details hierzu finden Sie in der API-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="1a758-172">See the API documentation for details.</span></span>

## <a name="dos-and-donts"></a><span data-ttu-id="1a758-173">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="1a758-173">Do's and Don'ts</span></span>

- <span data-ttu-id="1a758-174">Überlegen Sie, welche Art Farbwähler für Ihre App die beste Option ist.</span><span class="sxs-lookup"><span data-stu-id="1a758-174">Do think about what kind of color picking experience is appropriate for your app.</span></span> <span data-ttu-id="1a758-175">Einige Szenarien erfordern keine präzise Farbauswahl; dann ist ein vereinfachter Wähler die bessere Entscheidung.</span><span class="sxs-lookup"><span data-stu-id="1a758-175">Some scenarios may not require granular color picking and would benefit from a simplified picker</span></span>
- <span data-ttu-id="1a758-176">Für maximale Genauigkeit bei der Farbauswahl sollten Sie das quadratische Spektrum verwenden, mit einer Mindestgröße von 256×256px. Alternativ können Sie die Texteingabefelder implementieren, damit der Benutzer seine Wunschfarbe präzise anpassen kann.</span><span class="sxs-lookup"><span data-stu-id="1a758-176">For the most accurate color picking experience, use the square spectrum and ensure it is at least 256x256px, or include the text input fields to let users refine their selected color.</span></span>
- <span data-ttu-id="1a758-177">Wenn Sie den Farbwähler in einem Flyout hosten, sollte die Farbauswahl nicht bereits durch ein simples Tippen in das Spektrum oder eine einfache Justierung des Schiebereglers übernommen werden.</span><span class="sxs-lookup"><span data-stu-id="1a758-177">When used in a flyout, tapping in the spectrum or adjusting the slider alone should not commit the color selection.</span></span> <span data-ttu-id="1a758-178">Regeln Sie die Übernahme der Auswahl wie folgt:</span><span class="sxs-lookup"><span data-stu-id="1a758-178">To commit the selection:</span></span>
  - <span data-ttu-id="1a758-179">Implementieren Sie Schaltflächen zum Übernehmen und Abbrechen, über die der Benutzer seine Auswahl anwenden oder verwerfen kann.</span><span class="sxs-lookup"><span data-stu-id="1a758-179">Provide commit and cancel buttons to apply or cancel the selection.</span></span> <span data-ttu-id="1a758-180">Durch Klicken oder Tippen auf die Zurück-Schaltfläche bzw. auf eine Stelle außerhalb des Flyouts wird das Flyout geschlossen, ohne dass die Auswahl des Benutzers gespeichert wird.</span><span class="sxs-lookup"><span data-stu-id="1a758-180">Hitting the back button or tapping outside of the flyout will dismiss it, and not save the user’s selection.</span></span>
  - <span data-ttu-id="1a758-181">Alternativ kann die Auswahl übernommen werden, sobald der Benutzer das Flyout per Tippen oder Klicken auf eine Stelle außerhalb des Flyouts oder auf die Zurück-Schaltfläche schließt.</span><span class="sxs-lookup"><span data-stu-id="1a758-181">Or, commit the selection upon dismissing the flyout, by either tapping outside of the flyout or hitting the back button.</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="1a758-182">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="1a758-182">Get the sample code</span></span>

- <span data-ttu-id="1a758-183">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Xaml-Controls-Gallery) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="1a758-183">[XAML Controls Gallery sample](https://github.com/Microsoft/Xaml-Controls-Gallery) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="1a758-184">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="1a758-184">Related articles</span></span>

- [<span data-ttu-id="1a758-185">Zeichen- und Eingabestiftinteraktionen in UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="1a758-185">Pen and stylus interactions in UWP apps</span></span>](../input/pen-and-stylus-interactions.md)
- [<span data-ttu-id="1a758-186">Freihandeingaben</span><span class="sxs-lookup"><span data-stu-id="1a758-186">Inking</span></span>](inking-controls.md)

<!--
<div class=”microsoft-internal-note”>
<p>
<p>
Note: For more info, see the [color picker redlines](http://uni/DesignDepot.FrontEnd/#/ProductNav/3666/15/dv/?t=Windows%7CControls&f=RS2) on UNI.
</div>
-->