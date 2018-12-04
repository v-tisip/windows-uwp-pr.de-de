---
Description: Hyperlinks navigate the user to another part of the app, to another app, or launch a specific uniform resource identifier (URI) using a separate browser app.
title: Hyperlinks
ms.assetid: 74302FF0-65FC-4820-B59A-718A765EF7F0
label: Hyperlinks
template: detail.hbs
ms.date: 05/19/2017
ms.topic: article
keywords: Windows10, UWP
pm-contact: kisai
design-contact: kimsea
dev-contact: stpete
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 6d2a4ae2449fcfcccee792f70bb4d90f7b745047
ms.sourcegitcommit: b4c502d69a13340f6e3c887aa3c26ef2aeee9cee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "8484251"
---
# <a name="hyperlinks"></a><span data-ttu-id="52e0a-103">Links</span><span class="sxs-lookup"><span data-stu-id="52e0a-103">Hyperlinks</span></span>

 

<span data-ttu-id="52e0a-104">Über Hyperlinks können Benutzer zu einem anderen Teil der App oder zu einer anderen App navigieren oder mit einer separaten Browser-App einen bestimmten URI (Uniform Resource Identifier) starten.</span><span class="sxs-lookup"><span data-stu-id="52e0a-104">Hyperlinks navigate the user to another part of the app, to another app, or launch a specific uniform resource identifier (URI) using a separate browser app.</span></span> <span data-ttu-id="52e0a-105">Sie haben zwei Möglichkeiten, einer XAML-App einen Link hinzuzufügen: über das **Link**textelement oder das **HyperlinkButton**-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="52e0a-105">There are two ways that you can add a hyperlink to a XAML app: the **Hyperlink** text element and **HyperlinkButton** control.</span></span>

> <span data-ttu-id="52e0a-106">**Wichtige APIs**: [Linktextelement](https://msdn.microsoft.com/library/windows/apps/dn279356), [HyperlinkButton-Steuerelement](https://msdn.microsoft.com/library/windows/apps/br242739)</span><span class="sxs-lookup"><span data-stu-id="52e0a-106">**Important APIs**: [Hyperlink text element](https://msdn.microsoft.com/library/windows/apps/dn279356), [HyperlinkButton control](https://msdn.microsoft.com/library/windows/apps/br242739)</span></span>

![Eine Linkschaltfläche](images/controls/hyperlink-button.png)


## <a name="is-this-the-right-control"></a><span data-ttu-id="52e0a-108">Ist dies das richtige Steuerelement?</span><span class="sxs-lookup"><span data-stu-id="52e0a-108">Is this the right control?</span></span>

<span data-ttu-id="52e0a-109">Verwenden Sie einen Link, wenn Text erforderlich ist, der bei Auswahl reagiert und der weitere Informationen zum ausgewählten Text aufruft.</span><span class="sxs-lookup"><span data-stu-id="52e0a-109">Use a hyperlink when you need text that responds when selected and navigates the user to more information about the text that was selected.</span></span>

<span data-ttu-id="52e0a-110">Wählen Sie den richtigen Linktyp basierend auf Ihren Anforderungen:</span><span class="sxs-lookup"><span data-stu-id="52e0a-110">Choose the right type of hyperlink based on your needs:</span></span>

-   <span data-ttu-id="52e0a-111">Verwenden Sie innerhalb eines Textsteuerelements ein Inline-**Link**textelement.</span><span class="sxs-lookup"><span data-stu-id="52e0a-111">Use an inline **Hyperlink** text element inside of a text control.</span></span> <span data-ttu-id="52e0a-112">Ein Linkelement wird mit anderen Textelementen umgebrochen, und Sie können es in einem beliebigen InlineCollection-Element verwenden.</span><span class="sxs-lookup"><span data-stu-id="52e0a-112">A Hyperlink element flows with other text elements and you can use it in any InlineCollection.</span></span> <span data-ttu-id="52e0a-113">Verwenden Sie einen Textlink, wenn Sie automatischen Textumbruch nutzen möchten und nicht unbedingt ein großes Tippziel benötigen.</span><span class="sxs-lookup"><span data-stu-id="52e0a-113">Use a text hyperlink if you want automatic text wrapping and don't necessarily need a large hit target.</span></span> <span data-ttu-id="52e0a-114">Der Linktext kann klein sein und sich nur schwer auswählen lassen, insbesondere bei der Toucheingabe.</span><span class="sxs-lookup"><span data-stu-id="52e0a-114">Hyperlink text can be small and difficult to target, especially for touch.</span></span>
-   <span data-ttu-id="52e0a-115">Verwenden Sie ein **HyperlinkButton**-Element für eigenständige Links.</span><span class="sxs-lookup"><span data-stu-id="52e0a-115">Use a **HyperlinkButton** for stand-alone hyperlinks.</span></span> <span data-ttu-id="52e0a-116">Ein HyperlinkButton-Element ist ein spezielles Schaltflächen-Steuerelement, das Sie überall dort verwenden können, wo Sie eine Schaltfläche verwenden würden.</span><span class="sxs-lookup"><span data-stu-id="52e0a-116">A HyperlinkButton is a specialized Button control that you can use anywhere that you would use a Button.</span></span>
-   <span data-ttu-id="52e0a-117">Verwenden Sie ein **HyperlinkButton**-Element mit einem [Bild](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.aspx)als Inhalt, um ein klickbares Bild zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="52e0a-117">Use a **HyperlinkButton** with an [Image](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.aspx) as its content to make a clickable image.</span></span>

## <a name="examples"></a><span data-ttu-id="52e0a-118">Beispiele</span><span class="sxs-lookup"><span data-stu-id="52e0a-118">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="52e0a-119">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="52e0a-119">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="52e0a-120">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/HyperlinkButton">die App zu öffnen und HyperlinkButton in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="52e0a-120">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/HyperlinkButton">open the app and see the HyperlinkButton in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="52e0a-121">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="52e0a-121">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="52e0a-122">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="52e0a-122">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

## <a name="create-a-hyperlink-text-element"></a><span data-ttu-id="52e0a-123">Erstellen eines Linktextelements</span><span class="sxs-lookup"><span data-stu-id="52e0a-123">Create a Hyperlink text element</span></span>

<span data-ttu-id="52e0a-124">In diesem Beispiel wird veranschaulicht, wie Sie ein Linktextelement in einem [TextBlock](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) verwenden.</span><span class="sxs-lookup"><span data-stu-id="52e0a-124">This example shows how to use a Hyperlink text element inside of a [TextBlock](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx).</span></span>

```xml
<StackPanel Width="200">
    <TextBlock Text="Privacy" Style="{StaticResource SubheaderTextBlockStyle}"/>
    <TextBlock TextWrapping="WrapWholeWords">
        <Span xml:space="preserve"><Run>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Read the </Run><Hyperlink NavigateUri="http://www.contoso.com">Contoso Privacy Statement</Hyperlink><Run> in your browser.</Run> Donec pharetra, enim sit amet mattis tincidunt, felis nisi semper lectus, vel porta diam nisi in augue.</Span>
    </TextBlock>
</StackPanel>

```
<span data-ttu-id="52e0a-125">Der Link wird inline angezeigt und mit dem umgebenden Text umbrochen:</span><span class="sxs-lookup"><span data-stu-id="52e0a-125">The hyperlink appears inline and flows with the surrounding text:</span></span>

![Beispiel für einen Link als Textelement](images/controls_hyperlink-element.png) 

> <span data-ttu-id="52e0a-127">**Tipp:**&nbsp;&nbsp;Wenn Sie einen Link in einem Textsteuerelement mit anderen Textelementen in XAML verwenden, platzieren Sie den Inhalt in einem [Span](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.documents.span.aspx)-Container und wenden das Attribut `xml:space="preserve"` auf den Span-Container an, um die Leerstelle zwischen dem Link und anderen Elementen beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="52e0a-127">**Tip**&nbsp;&nbsp;When you use a Hyperlink in a text control with other text elements in XAML, place the content in a [Span](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.documents.span.aspx) container and apply the `xml:space="preserve"` attribute to the Span to keep the white space between the Hyperlink and other elements.</span></span>

## <a name="create-a-hyperlinkbutton"></a><span data-ttu-id="52e0a-128">Erstellen eines HyperlinkButton-Elements</span><span class="sxs-lookup"><span data-stu-id="52e0a-128">Create a HyperlinkButton</span></span>

<span data-ttu-id="52e0a-129">Hier sehen Sie, wie Sie ein HyperlinkButton-Element sowohl mit Text als auch mit Bild verwenden.</span><span class="sxs-lookup"><span data-stu-id="52e0a-129">Here's how to use a HyperlinkButton, both with text and with an image.</span></span>

```xml
<StackPanel>
    <TextBlock Text="About" Style="{StaticResource TitleTextBlockStyle}"/>
    <HyperlinkButton NavigateUri="http://www.contoso.com">
        <Image Source="Assets/ContosoLogo.png"/>
    </HyperlinkButton>
    <TextBlock Text="Version: 1.0.0001" Style="{StaticResource CaptionTextBlockStyle}"/>
    <HyperlinkButton Content="Contoso.com" NavigateUri="http://www.contoso.com"/>
    <HyperlinkButton Content="Acknowledgments" NavigateUri="http://www.contoso.com"/>
    <HyperlinkButton Content="Help" NavigateUri="http://www.contoso.com"/>
</StackPanel>

```

<span data-ttu-id="52e0a-130">Die Linkschaltflächen mit Textinhalt werden als markierter Text angezeigt.</span><span class="sxs-lookup"><span data-stu-id="52e0a-130">The hyperlink buttons with text content appear as marked-up text.</span></span> <span data-ttu-id="52e0a-131">Das Contoso-Logobild ist ebenfalls ein klickbarer Link:</span><span class="sxs-lookup"><span data-stu-id="52e0a-131">The Contoso logo image is also a clickable hyperlink:</span></span>

![Beispiel für einen Link als Schaltflächensteuerelement](images/controls_hyperlink-button-image.png)

<span data-ttu-id="52e0a-133">Dieses Beispiel zeigt, wie Sie ein einfaches HyperlinkButton-Element in Code erstellen.</span><span class="sxs-lookup"><span data-stu-id="52e0a-133">This example shows how to create a HyperlinkButton in code.</span></span>

```csharp
var helpLinkButton = new HyperlinkButton();
helpLinkButton.Content = "Help";
helpLinkButton.NavigateUri = new Uri("http://www.contoso.com");
```

## <a name="handle-navigation"></a><span data-ttu-id="52e0a-134">Handhaben der Navigation</span><span class="sxs-lookup"><span data-stu-id="52e0a-134">Handle navigation</span></span>

<span data-ttu-id="52e0a-135">Die Navigation wird bei beiden Linktypen gleich gehandhabt. Sie können die Eigenschaft **NavigateUri** festlegen oder das **Click**-Ereignis behandeln.</span><span class="sxs-lookup"><span data-stu-id="52e0a-135">For both kinds of hyperlinks, you handle navigation the same way; you can set the **NavigateUri** property, or handle the **Click** event.</span></span>

**<span data-ttu-id="52e0a-136">Navigieren zu einem URI</span><span class="sxs-lookup"><span data-stu-id="52e0a-136">Navigate to a URI</span></span>**

<span data-ttu-id="52e0a-137">Wenn Sie mit dem Link zu einem URI navigieren möchten, legen Sie die NavigateUri-Eigenschaft fest.</span><span class="sxs-lookup"><span data-stu-id="52e0a-137">To use the hyperlink to navigate to a URI, set the NavigateUri property.</span></span> <span data-ttu-id="52e0a-138">Wenn ein Benutzer auf den Link klickt oder tippt, wird der angegebene URI im Standardbrowser geöffnet.</span><span class="sxs-lookup"><span data-stu-id="52e0a-138">When a user clicks or taps the hyperlink, the specified URI opens in the default browser.</span></span> <span data-ttu-id="52e0a-139">Der Standardbrowser wird in einem separaten Prozess von Ihrer App ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="52e0a-139">The default browser runs in a separate process from your app.</span></span>

> [!NOTE]
> <span data-ttu-id="52e0a-140">Ein URI wird durch die [Windows.Foundation.Uri](/uwp/api/windows.foundation.uri)-Klasse dargestellt.</span><span class="sxs-lookup"><span data-stu-id="52e0a-140">A URI is represented by the [Windows.Foundation.Uri](/uwp/api/windows.foundation.uri) class.</span></span> <span data-ttu-id="52e0a-141">Bei der Programmierung mit .NET wird diese Klasse ausgeblendet und sollte die [System.Uri](https://docs.microsoft.com/dotnet/api/system.uri)-Klasse verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="52e0a-141">When programming with .NET, this class is hidden and you should use the [System.Uri](https://docs.microsoft.com/dotnet/api/system.uri) class.</span></span> <span data-ttu-id="52e0a-142">Weitere Informationen finden Sie auf den Referenzseiten für diese Klassen.</span><span class="sxs-lookup"><span data-stu-id="52e0a-142">For more info, see the reference pages for these classes.</span></span>

<span data-ttu-id="52e0a-143">Sie müssen keine Schemas wie **http:** oder **https:** verwenden.</span><span class="sxs-lookup"><span data-stu-id="52e0a-143">You don't have to use **http:** or **https:** schemes.</span></span> <span data-ttu-id="52e0a-144">Sie können Schemas wie **ms-appx:**, **ms-appdata:** oder **ms-resources:** verwenden, falls dort Ressourceninhalte vorhanden sind, die in einem Browser geladen werden können.</span><span class="sxs-lookup"><span data-stu-id="52e0a-144">You can use schemes such as **ms-appx:**, **ms-appdata:**, or **ms-resources:**, if there's resource content at these locations that's appropriate to load in a browser.</span></span> <span data-ttu-id="52e0a-145">Das Schema **file:** ist ausdrücklich blockiert.</span><span class="sxs-lookup"><span data-stu-id="52e0a-145">However, the **file:** scheme is specifically blocked.</span></span> <span data-ttu-id="52e0a-146">Weitere Informationen finden Sie unter [URI-Schemas](https://msdn.microsoft.com/library/windows/apps/jj655406.aspx).</span><span class="sxs-lookup"><span data-stu-id="52e0a-146">For more info, see [URI schemes](https://msdn.microsoft.com/library/windows/apps/jj655406.aspx).</span></span>

<span data-ttu-id="52e0a-147">Wenn ein Benutzer auf den Link klickt, wird der Wert der NavigateUri-Eigenschaft an einen Systemhandler für URI-Typen und -Schemas übergeben.</span><span class="sxs-lookup"><span data-stu-id="52e0a-147">When a user clicks the hyperlink, the value of the NavigateUri property is passed to a system handler for URI types and schemes.</span></span> <span data-ttu-id="52e0a-148">Das System startet dann die App, die für das Schema des URIs registriert ist, der für „NavigateUri“ angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="52e0a-148">The system then launches the app that is registered for the scheme of the URI provided for NavigateUri.</span></span>

<span data-ttu-id="52e0a-149">Wenn der Link keine Inhalte in einem Standardwebbrowser laden soll (und kein Browser angezeigt werden soll), legen Sie keinen Wert für „NavigateUri“ fest.</span><span class="sxs-lookup"><span data-stu-id="52e0a-149">If you don't want the hyperlink to load content in a default Web browser (and don't want a browser to appear), then don't set a value for NavigateUri.</span></span> <span data-ttu-id="52e0a-150">Behandeln Sie stattdessen das Click-Ereignis, und schreiben Sie Code, der die gewünschte Aktion ausführt.</span><span class="sxs-lookup"><span data-stu-id="52e0a-150">Instead, handle the Click event, and write code that does what you want.</span></span>


**<span data-ttu-id="52e0a-151">Behandeln des Click-Ereignisses</span><span class="sxs-lookup"><span data-stu-id="52e0a-151">Handle the Click event</span></span>**

<span data-ttu-id="52e0a-152">Verwenden Sie das Click-Ereignis für alle Aktionen außer für das Starten eines URIs in einem Browser (also beispielsweise für die Navigation innerhalb der App).</span><span class="sxs-lookup"><span data-stu-id="52e0a-152">Use the Click event for actions other than launching a URI in a browser, such as navigation within the app.</span></span> <span data-ttu-id="52e0a-153">Wenn Sie beispielsweise keinen Broswer öffnen, sondern eine neue App-Seite laden möchten, rufen Sie eine [Frame.Navigate](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.frame.navigate.aspx)-Methode in Ihrem Click-Ereignishandler auf, um zur neuen App-Seite zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="52e0a-153">For example, if you want to load a new app page rather than opening a browser, call a [Frame.Navigate](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.frame.navigate.aspx) method within your Click event handler to navigate to the new app page.</span></span> <span data-ttu-id="52e0a-154">Wenn ein externer, absoluter URI in einem [WebView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.webview.aspx)-Steuerelement geladen werden soll, das auch in Ihrer App vorhanden ist, rufen Sie [WebView.Navigate](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.webview.navigate.aspx) als Teil Ihrer Klickhandlerlogik auf.</span><span class="sxs-lookup"><span data-stu-id="52e0a-154">If you want an external, absolute URI to load within a [WebView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.webview.aspx) control that also exists in your app, call [WebView.Navigate](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.webview.navigate.aspx) as part of your Click handler logic.</span></span>

<span data-ttu-id="52e0a-155">In der Regel behandeln Sie nicht das Click-Ereignis und legen gleichzeitig einen NavigateUri-Wert fest, da dies zwei verschiedene Methoden zur Verwendung des Linkelements darstellen.</span><span class="sxs-lookup"><span data-stu-id="52e0a-155">You don't typically handle the Click event as well as specifying a NavigateUri value, as these represent two different ways of using the hyperlink element.</span></span> <span data-ttu-id="52e0a-156">Wenn Sie den URI im Standardbrowser öffnen möchten und einen Wert für „NavigateUri“ angegeben haben, behandeln Sie das Click-Ereignis nicht.</span><span class="sxs-lookup"><span data-stu-id="52e0a-156">If your intent is to open the URI in the default browser, and you have specified a value for NavigateUri, don't handle the Click event.</span></span> <span data-ttu-id="52e0a-157">Im umgekehrten Fall geben Sie kein NavigateUri-Element an, wenn Sie das Click-Ereignis behandeln.</span><span class="sxs-lookup"><span data-stu-id="52e0a-157">Conversely, if you handle the Click event, don't specify a NavigateUri.</span></span>

<span data-ttu-id="52e0a-158">Sie können im Click-Ereignishandler nicht verhindern, dass der Standardbrowser ein für „NavigateUri“ angegebenes gültiges Ziel lädt. Die Aktion wird automatisch (asynchron) ausgeführt, wenn der Link aktiviert wird und kann nicht im Click-Ereignishandler abgebrochen werden.</span><span class="sxs-lookup"><span data-stu-id="52e0a-158">There's nothing you can do within the Click event handler to prevent the default browser from loading any valid target specified for NavigateUri; that action takes place automatically (asynchronously) when the hyperlink is activated and can't be canceled from within the Click event handler.</span></span> 

## <a name="hyperlink-underlines"></a><span data-ttu-id="52e0a-159">Unterstreichung von Links</span><span class="sxs-lookup"><span data-stu-id="52e0a-159">Hyperlink underlines</span></span>
<span data-ttu-id="52e0a-160">Links sind standardmäßig unterstrichen.</span><span class="sxs-lookup"><span data-stu-id="52e0a-160">By default, hyperlinks are underlined.</span></span> <span data-ttu-id="52e0a-161">Diese Unterstreichung ist wichtig, da dadurch Anforderungen für Barrierefreiheit erfüllt werden.</span><span class="sxs-lookup"><span data-stu-id="52e0a-161">This underline is important because it helps meet accessibility requirements.</span></span> <span data-ttu-id="52e0a-162">Farbenblinde Benutzer können anhand der Unterstreichung zwischen Links und anderem Text unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="52e0a-162">Color-blind users use the underline to distinguish between hyperlinks and other text.</span></span> <span data-ttu-id="52e0a-163">Wenn Sie die Unterstreichung deaktivieren, sollten Sie eine andere Art der Formatierung in Betracht ziehen (z.B. „FontWeight“ oder „FontStyle“), um Links von anderem Text abzuheben.</span><span class="sxs-lookup"><span data-stu-id="52e0a-163">If you disable underlines, you should consider adding some other type of formatting difference to distinguish hyperlinks from other text, such as FontWeight or FontStyle.</span></span>

**<span data-ttu-id="52e0a-164">Linktextelemente</span><span class="sxs-lookup"><span data-stu-id="52e0a-164">Hyperlink text elements</span></span>**

<span data-ttu-id="52e0a-165">Sie können die [UnderlineStyle](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.documents.hyperlink.underlinestyle.aspx)-Eigenschaft festlegen, um die Unterstreichung zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="52e0a-165">You can set the [UnderlineStyle](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.documents.hyperlink.underlinestyle.aspx) property to disable the underline.</span></span> <span data-ttu-id="52e0a-166">Ziehen Sie in diesem Fall die Verwendung von [FontWeight](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.documents.textelement.fontweight.aspx) oder [FontStyle](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.documents.textelement.fontstyle.aspx) in Betracht, um Ihren Linktext zu differenzieren.</span><span class="sxs-lookup"><span data-stu-id="52e0a-166">If you do, consider using [FontWeight](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.documents.textelement.fontweight.aspx) or [FontStyle](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.documents.textelement.fontstyle.aspx) to differentiate your link text.</span></span>

**<span data-ttu-id="52e0a-167">HyperlinkButton</span><span class="sxs-lookup"><span data-stu-id="52e0a-167">HyperlinkButton</span></span>** 

<span data-ttu-id="52e0a-168">„HyperlinkButton“ wird standardmäßig als unterstrichener Text angezeigt, wenn Sie eine Zeichenfolge als Wert für die [Content](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.contentcontrol.content.aspx)-Eigenschaft festlegen.</span><span class="sxs-lookup"><span data-stu-id="52e0a-168">By default, the HyperlinkButton appears as underlined text when you set a string as the value for the [Content](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.contentcontrol.content.aspx) property.</span></span>

<span data-ttu-id="52e0a-169">Der Text wird in den folgenden Fällen nicht unterstrichen angezeigt:</span><span class="sxs-lookup"><span data-stu-id="52e0a-169">The text does not appear underlined in the following cases:</span></span>
- <span data-ttu-id="52e0a-170">Sie legen [TextBlock](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) als Wert für die Content-Eigenschaft und die [Text](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.text.aspx)-Eigenschaft für „TextBlock“ fest.</span><span class="sxs-lookup"><span data-stu-id="52e0a-170">You set a [TextBlock](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) as the value for the Content property, and set the [Text](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.text.aspx) property on the TextBlock.</span></span>
- <span data-ttu-id="52e0a-171">Sie passen die Vorlage für „HyperlinkButton“ an und ändern den Namen des [ContentPresenter](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.contentpresenter.aspx)-Vorlagenteils.</span><span class="sxs-lookup"><span data-stu-id="52e0a-171">You re-template the HyperlinkButton and change the name of the [ContentPresenter](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.contentpresenter.aspx) template part.</span></span>

<span data-ttu-id="52e0a-172">Wenn Sie eine Schaltfläche benötigen, die als nicht unterstrichener Text angezeigt wird, können Sie ein Standard-Schaltflächen-Steuerelement verwenden und die integrierte Systemressource `TextBlockButtonStyle` auf die Style-Eigenschaft anwenden.</span><span class="sxs-lookup"><span data-stu-id="52e0a-172">If you need a button that appears as non-underlined text, consider using a standard Button control and applying the built-in `TextBlockButtonStyle` system resource to its Style property.</span></span>

## <a name="notes-for-hyperlink-text-element"></a><span data-ttu-id="52e0a-173">Hinweise zum Linktextelement</span><span class="sxs-lookup"><span data-stu-id="52e0a-173">Notes for Hyperlink text element</span></span>

<span data-ttu-id="52e0a-174">Dieser Abschnitt gilt nur für das Linktextelement, nicht das HyperlinkButton-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="52e0a-174">This section applies only to the Hyperlink text element, not to the HyperlinkButton control.</span></span>

**<span data-ttu-id="52e0a-175">Eingabeereignisse</span><span class="sxs-lookup"><span data-stu-id="52e0a-175">Input events</span></span>**

<span data-ttu-id="52e0a-176">Da es sich bei einem Link nicht um ein [UIElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.aspx) handelt, enthält er nicht den Satz von Eingabeereignissen für UI-Elemente wie „Tapped“, „PointerPressed“ usw.</span><span class="sxs-lookup"><span data-stu-id="52e0a-176">Because a Hyperlink is not a [UIElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.aspx), it does not have the set of UI element input events such as Tapped, PointerPressed, and so on.</span></span> <span data-ttu-id="52e0a-177">Stattdessen enthält ein Link ein eigenes Click-Ereignis sowie das implizite Verhalten des Systems, das jeden als „NavigateUri“ angegebenen URI lädt.</span><span class="sxs-lookup"><span data-stu-id="52e0a-177">Instead, a Hyperlink has its own Click event, plus the implicit behavior of the system loading any URI specified as the NavigateUri.</span></span> <span data-ttu-id="52e0a-178">Das System verarbeitet alle Eingabeaktionen, die die Linkaktionen aufrufen sollten, und löst als Reaktion das Click-Ereignis aus.</span><span class="sxs-lookup"><span data-stu-id="52e0a-178">The system handles all input actions that should invoke the Hyperlink actions and raises the Click event in response.</span></span>

**<span data-ttu-id="52e0a-179">Inhalt</span><span class="sxs-lookup"><span data-stu-id="52e0a-179">Content</span></span>**

<span data-ttu-id="52e0a-180">Für den Link liegen Einschränkungen in Bezug auf den Inhalt vor, der in der [Inlines](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.documents.span.inlines.aspx)-Sammlung enthalten sein darf.</span><span class="sxs-lookup"><span data-stu-id="52e0a-180">Hyperlink has restrictions on the content that can exist in its [Inlines](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.documents.span.inlines.aspx) collection.</span></span> <span data-ttu-id="52e0a-181">Genauer gesagt: Ein Link lässt nur [Run](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.documents.run.aspx)- und andere [Span]()-Typen zu, die keinen anderen Link darstellen.</span><span class="sxs-lookup"><span data-stu-id="52e0a-181">Specifically, a Hyperlink only permits [Run](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.documents.run.aspx) and other [Span]() types that aren't another Hyperlink.</span></span> <span data-ttu-id="52e0a-182">[InlineUIContainer](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.documents.inlineuicontainer.aspx) darf nicht in der Inlines-Sammlung eines Links enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="52e0a-182">[InlineUIContainer](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.documents.inlineuicontainer.aspx) can't be in the Inlines collection of a Hyperlink.</span></span> <span data-ttu-id="52e0a-183">Beim Versuch, eingeschränkte Inhalte hinzuzufügen, wird eine Ausnahme für ein ungültiges Argument oder eine XAML-Analyseausnahme ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="52e0a-183">Attempting to add restricted content throws an invalid argument exception or XAML parse exception.</span></span>

**<span data-ttu-id="52e0a-184">Links und Design-/Formatvorlagenverhalten</span><span class="sxs-lookup"><span data-stu-id="52e0a-184">Hyperlink and theme/style behavior</span></span>**

<span data-ttu-id="52e0a-185">Links erben nicht von [Control](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.control.aspx). Daher enthalten sie keine [Style](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.style.aspx)- oder [Template](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.control.template.aspx)-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="52e0a-185">Hyperlink doesn't inherit from [Control](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.control.aspx), so it doesn't have a [Style](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.style.aspx) property or a [Template](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.control.template.aspx).</span></span> <span data-ttu-id="52e0a-186">Sie können die von [TextElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.documents.textelement.aspx) geerbten Eigenschaften wie „Foreground“ oder „FontFamily“ bearbeiten, um das Erscheinungsbild eines Links zu ändern. Sie können jedoch keinen allgemeinen Stil bzw. keine allgemeine Vorlage zum Anwenden von Änderungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="52e0a-186">You can edit the properties that are inherited from [TextElement](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.documents.textelement.aspx), such as Foreground or FontFamily, to change the appearance of a Hyperlink, but you can't use a common style or template to apply changes.</span></span> <span data-ttu-id="52e0a-187">Verwenden Sie anstelle einer Vorlage allgemeine Ressourcen für Werte der Linkeigenschaften, um die Konsistenz zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="52e0a-187">Instead of using a template, consider using common resources for values of Hyperlink properties to provide consistency.</span></span> <span data-ttu-id="52e0a-188">Einige Linkeigenschaften verwenden Standardwerte aus einem vom System bereitgestellten {ThemeResource}-Markuperweiterungswert.</span><span class="sxs-lookup"><span data-stu-id="52e0a-188">Some properties of Hyperlink use defaults from a {ThemeResource} markup extension value provided by the system.</span></span> <span data-ttu-id="52e0a-189">Dadurch kann die Linkdarstellung entsprechend angepasst werden, wenn der Benutzer das Systemdesign während der Laufzeit ändert.</span><span class="sxs-lookup"><span data-stu-id="52e0a-189">This enables the Hyperlink appearance to switch in appropriate ways when the user changes the system theme at run-time.</span></span>

<span data-ttu-id="52e0a-190">Die Standardfarbe des Links ist die Akzentfarbe des Systems.</span><span class="sxs-lookup"><span data-stu-id="52e0a-190">The default color of the hyperlink is the accent color of the system.</span></span> <span data-ttu-id="52e0a-191">Dieses Verhalten können Sie mit der [Foreground](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.documents.textelement.foreground.aspx)-Eigenschaft außer Kraft setzen.</span><span class="sxs-lookup"><span data-stu-id="52e0a-191">You can set the [Foreground](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.documents.textelement.foreground.aspx) property to override this.</span></span>

## <a name="recommendations"></a><span data-ttu-id="52e0a-192">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="52e0a-192">Recommendations</span></span>

-   <span data-ttu-id="52e0a-193">Verwenden Sie Links nur für die Navigation. Verwenden Sie sie nicht für andere Aktionen.</span><span class="sxs-lookup"><span data-stu-id="52e0a-193">Only use hyperlinks for navigation; don't use them for other actions.</span></span>
-   <span data-ttu-id="52e0a-194">Verwenden Sie den Textstil aus dem Typenverlauf für textbasierte Links.</span><span class="sxs-lookup"><span data-stu-id="52e0a-194">Use the Body style from the type ramp for text-based hyperlinks.</span></span> <span data-ttu-id="52e0a-195">Informieren Sie sich über [Schriftarten und den Windows 10-Typenverlauf](../style/typography.md).</span><span class="sxs-lookup"><span data-stu-id="52e0a-195">Read about [fonts and the Windows 10 type ramp](../style/typography.md).</span></span>
-   <span data-ttu-id="52e0a-196">Separate Links sollten weit genug voneinander platziert werden, damit der Benutzer zwischen ihnen unterscheiden kann und sie mühelos einzeln auswählen kann.</span><span class="sxs-lookup"><span data-stu-id="52e0a-196">Keep discrete hyperlinks far enough apart so that the user can differentiate between them and has an easy time selecting each one.</span></span>
-   <span data-ttu-id="52e0a-197">Fügen Sie Hyperlinks QuickInfos hinzu, die dem Benutzer anzeigen, wohin er umgeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="52e0a-197">Add tooltips to hyperlinks that indicate to where the user will be directed.</span></span> <span data-ttu-id="52e0a-198">Wenn der Benutzer zu einer externen Website weitergeleitet werden soll, schließen Sie den Namen der Domäne der obersten Ebene in die QuickInfo ein und formatieren den Text mit einer zweiten Schriftfarbe.</span><span class="sxs-lookup"><span data-stu-id="52e0a-198">If the user will be directed to an external site, include the top-level domain name inside the tooltip, and style the text with a secondary font color.</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="52e0a-199">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="52e0a-199">Get the sample code</span></span>

- <span data-ttu-id="52e0a-200">[Beispiel eines XAML-Steuerelementkatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="52e0a-200">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>

## <a name="related-articles"></a><span data-ttu-id="52e0a-201">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="52e0a-201">Related articles</span></span>

- [<span data-ttu-id="52e0a-202">Textsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="52e0a-202">Text controls</span></span>](text-controls.md)
- [<span data-ttu-id="52e0a-203">Richtlinien für QuickInfos</span><span class="sxs-lookup"><span data-stu-id="52e0a-203">Guidelines for tooltips</span></span>](tooltips.md)

**<span data-ttu-id="52e0a-204">Für Entwickler (XAML)</span><span class="sxs-lookup"><span data-stu-id="52e0a-204">For developers (XAML)</span></span>**
- [<span data-ttu-id="52e0a-205">Windows.UI.Xaml.Documents.Hyperlink-Klasse</span><span class="sxs-lookup"><span data-stu-id="52e0a-205">Windows.UI.Xaml.Documents.Hyperlink class</span></span>](https://msdn.microsoft.com/library/windows/apps/dn279356)
- [<span data-ttu-id="52e0a-206">Windows.UI.Xaml.Controls.HyperlinkButton-Klasse</span><span class="sxs-lookup"><span data-stu-id="52e0a-206">Windows.UI.Xaml.Controls.HyperlinkButton class</span></span>](https://msdn.microsoft.com/library/windows/apps/br242739)
