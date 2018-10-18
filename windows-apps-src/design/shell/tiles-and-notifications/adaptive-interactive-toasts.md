---
author: andrewleader
Description: Adaptive and interactive toast notifications let you create flexible pop-up notifications with more content, optional inline images, and optional user interaction.
title: Popupinhalt
ms.assetid: 1FCE66AF-34B4-436A-9FC9-D0CF4BDA5A01
label: Toast content
template: detail.hbs
ms.author: mijacobs
ms.date: 11/20/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Popupbenachrichtigungen, interaktive Popups, adaptive Popups, Popup-Inhalt, Nutzlast des Popups
ms.localizationpriority: medium
ms.openlocfilehash: de999528d07e6bd7d243e53708e9afc465004af7
ms.sourcegitcommit: 1c6325aa572868b789fcdd2efc9203f67a83872a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2018
ms.locfileid: "4754335"
---
# <a name="toast-content"></a><span data-ttu-id="04e96-103">Popupinhalt</span><span class="sxs-lookup"><span data-stu-id="04e96-103">Toast content</span></span>

<span data-ttu-id="04e96-104">Mit adaptiven und interaktiven Popupbenachrichtigungen können Sie flexible Benachrichtigungen mit Text, Bildern und Schaltflächen/Eingaben erstellen.</span><span class="sxs-lookup"><span data-stu-id="04e96-104">Adaptive and interactive toast notifications let you create flexible notifications with text, images, and buttons/inputs.</span></span>

> <span data-ttu-id="04e96-105">**Wichtige APIs**: [UWP Community Toolkit Notifications-NuGet-Paket](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/)</span><span class="sxs-lookup"><span data-stu-id="04e96-105">**Important APIs**: [UWP Community Toolkit Notifications nuget package](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/)</span></span>

> [!NOTE]
> <span data-ttu-id="04e96-106">Die Legacyvorlagen von Windows8.1 und Windows Phone8.1 finden Sie im [Legacy-Popupvorlagenkatalog](https://msdn.microsoft.com/library/windows/apps/hh761494).</span><span class="sxs-lookup"><span data-stu-id="04e96-106">To see the legacy templates from Windows 8.1 and Windows Phone 8.1, see the [legacy toast template catalog](https://msdn.microsoft.com/library/windows/apps/hh761494).</span></span>


## <a name="getting-started"></a><span data-ttu-id="04e96-107">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="04e96-107">Getting started</span></span>

**<span data-ttu-id="04e96-108">Installieren Sie die Benachrichtigungsbibliothek.</span><span class="sxs-lookup"><span data-stu-id="04e96-108">Install Notifications library.</span></span>** <span data-ttu-id="04e96-109">Wenn Sie C# anstelle von XML verwenden möchten, um Benachrichtigungen zu generieren, installieren Sie das NuGet-Paket mit dem Namen [Microsoft.Toolkit.Uwp.Notifications](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/). (Suchen Sie nach „Benachrichtigungen UWP“.)</span><span class="sxs-lookup"><span data-stu-id="04e96-109">If you'd like to use C# instead of XML to generate notifications, install the NuGet package named [Microsoft.Toolkit.Uwp.Notifications](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) (search for "notifications uwp").</span></span> <span data-ttu-id="04e96-110">Die in diesem Artikel bereitgestellten C#-Beispiele verwenden Version 1.0.0 des NuGet-Pakets.</span><span class="sxs-lookup"><span data-stu-id="04e96-110">The C# samples provided in this article use version 1.0.0 of the NuGet package.</span></span>

**<span data-ttu-id="04e96-111">Installieren Sie den Notifications Visualizer.</span><span class="sxs-lookup"><span data-stu-id="04e96-111">Install Notifications Visualizer.</span></span>** <span data-ttu-id="04e96-112">Diese kostenlose UWP-App hilft Ihnen, interaktive Popupbenachrichtigungen zu entwerfen, indem sie während der Bearbeitung des Popups sofort eine Vorschau des Popups bereitstellen, ähnlich dem XAML-Editor/der Entwurfsansicht von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="04e96-112">This free UWP app helps you design interactive toast notifications by providing an instant visual preview of your toast as you edit it, similar to Visual Studio's XAML editor/design view.</span></span> <span data-ttu-id="04e96-113">Weitere Informationen finden Sie unter [Notifications Visualizer](notifications-visualizer.md) oder [Notifications Visualizer aus dem Store herunterladen](https://www.microsoft.com/store/apps/notifications-visualizer/9nblggh5xsl1).</span><span class="sxs-lookup"><span data-stu-id="04e96-113">See [Notifications Visualizer](notifications-visualizer.md) for more information, or [download Notifications Visualizer from the Store](https://www.microsoft.com/store/apps/notifications-visualizer/9nblggh5xsl1).</span></span>


## <a name="sending-a-toast-notification"></a><span data-ttu-id="04e96-114">Senden einer Popupbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="04e96-114">Sending a toast notification</span></span>

<span data-ttu-id="04e96-115">Weitere Informationen zum Senden einer Benachrichtigung finden Sie unter [Senden einer lokalen Popupbenachrichtigung](send-local-toast.md).</span><span class="sxs-lookup"><span data-stu-id="04e96-115">To learn how to send a notification, see [Send local toast](send-local-toast.md).</span></span> <span data-ttu-id="04e96-116">In dieser Dokumentation wird nur die Erstellung des Popupinhalts behandelt.</span><span class="sxs-lookup"><span data-stu-id="04e96-116">This documentation only covers creating the toast content.</span></span>


## <a name="toast-notification-structure"></a><span data-ttu-id="04e96-117">Struktur der Popupbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="04e96-117">Toast notification structure</span></span>

<span data-ttu-id="04e96-118">Popupbenachrichtigungen sind eine Kombination aus einigen Dateneigenschaften wie Tag/Group (mit denen Sie die Benachrichtigung identifizieren können) und dem *Popupinhalt*.</span><span class="sxs-lookup"><span data-stu-id="04e96-118">Toast notifications are a combination of some data properties like Tag/Group (which let you identify the notification) and the *toast content*.</span></span>

<span data-ttu-id="04e96-119">Die Kernkomponenten des Popupinhalts sind...</span><span class="sxs-lookup"><span data-stu-id="04e96-119">The core components of toast content are...</span></span>
* <span data-ttu-id="04e96-120">**launch**: Hiermit wird definiert, welche Argumente wieder an Ihre App übergeben werden, wenn der Benutzer auf Ihr Popup klickt, sodass Sie einen Deep-Link zum richtigen Inhalt bereitstellen können, der im Popup angezeigt wurde.</span><span class="sxs-lookup"><span data-stu-id="04e96-120">**launch**: This defines what arguments will be passed back to your app when the user clicks your toast, allowing you to deep link into the correct content that the toast was displaying.</span></span> <span data-ttu-id="04e96-121">Weitere Informationen hierzu finden Sie unter [Senden einer lokalen Popupbenachrichtigung](send-local-toast.md).</span><span class="sxs-lookup"><span data-stu-id="04e96-121">To learn more, see [Send local toast](send-local-toast.md).</span></span>
* <span data-ttu-id="04e96-122">**visual**: der visuelle Teil des Popups, einschließlich der generischen Bindung, die Text und Bilder enthält</span><span class="sxs-lookup"><span data-stu-id="04e96-122">**visual**: The visual portion of the toast, including the generic binding that contains text and images.</span></span>
* <span data-ttu-id="04e96-123">**actions**: der interaktive Teil des Popups, einschließlich Eingaben und Aktionen</span><span class="sxs-lookup"><span data-stu-id="04e96-123">**actions**: The interactive portion of the toast, including inputs and actions.</span></span>
* <span data-ttu-id="04e96-124">**audio**: steuert die Tonwiedergabe, während dem Benutzer das Popup angezeigt wird</span><span class="sxs-lookup"><span data-stu-id="04e96-124">**audio**: Controls the audio played when the toast is shown to the user.</span></span>

<span data-ttu-id="04e96-125">Der Popupinhalt ist in XML-Rohdaten definiert, aber Sie können unsere [NuGet-Bibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) verwenden, um ein C# (oder C++)-Objektmodell für die Erstellung des Popupinhalts zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="04e96-125">The toast content is defined in raw XML, but you can use our [NuGet library](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) to get a C# (or C++) object model for constructing the toast content.</span></span> <span data-ttu-id="04e96-126">In diesem Artikel werden alle Elemente des Popupinhalts dokumentiert.</span><span class="sxs-lookup"><span data-stu-id="04e96-126">This article documents everything that goes within the toast content.</span></span>

```csharp
ToastContent content = new ToastContent()
{
    Launch = "app-defined-string",
 
    Visual = new ToastVisual()
    {
        BindingGeneric = new ToastBindingGeneric() { ... }
    },
 
    Actions = new ToastActionsCustom() { ... },
 
    Audio = new ToastAudio() { ... }
};
```

```xml
<toast launch="app-defined-string">

  <visual>
    <binding template="ToastGeneric">
      ...
    </binding>
  </visual>

  <actions>
    ...
  </actions>

  <audio src="ms-winsoundevent:Notification.Reminder"/>

</toast>
```

<span data-ttu-id="04e96-127">Hier sehen Sie eine visuelle Darstellung des Inhalts des Popups:</span><span class="sxs-lookup"><span data-stu-id="04e96-127">Here is a visual representation of the toast's content:</span></span>

![Aufbau einer Popupbenachrichtigung](images/adaptivetoasts-structure.jpg)


## <a name="visual"></a><span data-ttu-id="04e96-129">Visuelles Element</span><span class="sxs-lookup"><span data-stu-id="04e96-129">Visual</span></span>

<span data-ttu-id="04e96-130">Jedes Popup muss ein visuelles Element angeben, in dem Sie eine generische Popupbindung angeben müssen, die Text, Bilder und vieles mehr enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="04e96-130">Each toast must specify a visual, where you must provide a generic toast binding, which can contain text, images, and more.</span></span> <span data-ttu-id="04e96-131">Diese Elemente werden auf verschiedenen Windows-Geräten wie Desktops, Smartphones, Tablets und Xbox wiedergegeben.</span><span class="sxs-lookup"><span data-stu-id="04e96-131">These elements will be rendered on various Windows devices, including desktop, phones, tablets, and Xbox.</span></span>

<span data-ttu-id="04e96-132">Alle Attribute, die im Abschnitt „Visuelle Elemente“ unterstützt werden, sowie die untergeordneten Elemente [finden Sie in der Schemadokumentation](toast-schema.md#toastvisual).</span><span class="sxs-lookup"><span data-stu-id="04e96-132">For all attributes supported in the visual section and its child elements, [see the schema documentation](toast-schema.md#toastvisual).</span></span>

<span data-ttu-id="04e96-133">Die Identität Ihrer App in der Popupbenachrichtigung wird über Ihr App-Symbol angegeben.</span><span class="sxs-lookup"><span data-stu-id="04e96-133">Your app's identity on the toast notification is conveyed via your app icon.</span></span> <span data-ttu-id="04e96-134">Wenn Sie jedoch die App-Logo-Überschreibung verwenden, wird der Name Ihrer App unterhalb der Textzeilen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="04e96-134">However, if you use the app logo override, we will display your app name beneath your lines of text.</span></span>

| <span data-ttu-id="04e96-135">App-Identität für normale Popups</span><span class="sxs-lookup"><span data-stu-id="04e96-135">App identity for normal toast</span></span> | <span data-ttu-id="04e96-136">App-Identität mit appLogoOverride</span><span class="sxs-lookup"><span data-stu-id="04e96-136">App identity with appLogoOverride</span></span> |
| -- | -- |
| <img src="images/adaptivetoasts-withoutapplogooverride.jpg" alt="notification without appLogoOverride" width="364"/> | <img alt="notification with appLogoOverride" src="images/adaptivetoasts-withapplogooverride.jpg" width="364"/> |


## <a name="text-elements"></a><span data-ttu-id="04e96-137">Textelemente</span><span class="sxs-lookup"><span data-stu-id="04e96-137">Text elements</span></span>

<span data-ttu-id="04e96-138">Jedes Popup muss mindestens ein Textelement enthalten und kann zwei zusätzliche Textelemente enthalten, wobei alle den Typ [**AdaptiveText**](toast-schema.md#adaptivetext) aufweisen müssen.</span><span class="sxs-lookup"><span data-stu-id="04e96-138">Each toast must have at least one text element, and can contain two additional text elements, all of type [**AdaptiveText**](toast-schema.md#adaptivetext).</span></span>

<img alt="Toast with title and description" src="images/toast-title-and-description.jpg" width="364"/>

<span data-ttu-id="04e96-139">Seit dem Windows 10 Anniversary Update können Sie mithilfe der **HintMaxLines**-Eigenschaft für den Text steuern, wie viele Zeilen Text angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="04e96-139">Since the Windows 10 Anniversary Update, you can control how many lines of text are displayed by using the **HintMaxLines** property on the text.</span></span> <span data-ttu-id="04e96-140">Der Standardwert (maximal) ist maximal 2 Zeilen Text für den Titel und maximal 4 Zeilen (kombiniert) für die zwei zusätzlichen Beschreibungselemente (der zweite und dritte **AdaptiveText**).</span><span class="sxs-lookup"><span data-stu-id="04e96-140">The default (and maximum) is up to 2 lines of text for the title, and up to 4 lines (combined) for the two additional description elements (the second and third **AdaptiveText**).</span></span>

```csharp
new ToastBindingGeneric()
{
    Children =
    {
        new AdaptiveText()
        {
            Text = "Adaptive Tiles Meeting",
            HintMaxLines = 1
        },

        new AdaptiveText()
        {
            Text = "Conf Room 2001 / Building 135"
        },

        new AdaptiveText()
        {
            Text = "10:00 AM - 10:30 AM"
        }
    }
}
```

```xml
<binding template="ToastGeneric">
    <text hint-maxLines="1">Adaptive Tiles Meeting</text>
    <text>Conf Room 2001 / Building 135</text>
    <text>10:00 AM - 10:30 AM</text>
</binding>
```


## <a name="app-logo-override"></a><span data-ttu-id="04e96-141">Überschreibung des App-Logos</span><span class="sxs-lookup"><span data-stu-id="04e96-141">App logo override</span></span>

<span data-ttu-id="04e96-142">Standardmäßig zeigt das Popup Ihr App-Logo an.</span><span class="sxs-lookup"><span data-stu-id="04e96-142">By default, your toast will display your app's logo.</span></span> <span data-ttu-id="04e96-143">Allerdings können Sie dieses Logo mit Ihrem eigenen [**ToastGenericAppLogo**](toast-schema.md#toastgenericapplogo)-Bild überschreiben.</span><span class="sxs-lookup"><span data-stu-id="04e96-143">However, you can override this logo with your own [**ToastGenericAppLogo**](toast-schema.md#toastgenericapplogo) image.</span></span> <span data-ttu-id="04e96-144">Wenn es sich beispielsweise um eine Benachrichtigung von einer Person handelt, empfehlen wir, das App-Logo mit einem Bild der betreffenden Person zu überschreiben.</span><span class="sxs-lookup"><span data-stu-id="04e96-144">For example, if this is a notification from a person, we recommend overriding the app logo with a picture of that person.</span></span>

<img alt="Toast with app logo override" src="images/toast-applogooverride.jpg" width="364"/>

<span data-ttu-id="04e96-145">Sie können die **HintCrop**-Eigenschaft verwenden, um den Zuschnitt des Bilds zu ändern.</span><span class="sxs-lookup"><span data-stu-id="04e96-145">You can use the **HintCrop** property to change the cropping of the image.</span></span> <span data-ttu-id="04e96-146">So ergibt **Kreis** z. B. ein kreisförmig zugeschnittenes Bild.</span><span class="sxs-lookup"><span data-stu-id="04e96-146">For example, **Circle** results in a circle-cropped image.</span></span> <span data-ttu-id="04e96-147">Andernfalls ist das Bild quadratisch.</span><span class="sxs-lookup"><span data-stu-id="04e96-147">Otherwise, the image is square.</span></span> <span data-ttu-id="04e96-148">Bildabmessungen sind 48x48Pixel bei einer Skalierung von 100%.</span><span class="sxs-lookup"><span data-stu-id="04e96-148">Image dimensions are 48x48 pixels at 100% scaling.</span></span>

```csharp
new ToastBindingGeneric()
{
    ...

    AppLogoOverride = new ToastGenericAppLogo()
    {
        Source = "https://picsum.photos/48?image=883",
        HintCrop = ToastGenericAppLogoCrop.Circle
    }
}
```

```xml
<binding template="ToastGeneric">
    ...
    <image placement="appLogoOverride" hint-crop="circle" src="https://picsum.photos/48?image=883"/>
</binding>
```


## <a name="hero-image"></a><span data-ttu-id="04e96-149">Favoritenbild</span><span class="sxs-lookup"><span data-stu-id="04e96-149">Hero image</span></span>

<span data-ttu-id="04e96-150">**Neu im Anniversary Update**: Popups können ein Favoritenbild anzeigen. Dabei handelt es sich um ein ausgewähltes [**ToastGenericHeroImage**](toast-schema.md#toastgenericheroimage), das an hervorgehobener Stelle innerhalb des Popup-Banners und im Info-Center angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="04e96-150">**New in Anniversary Update**: Toasts can display a hero image, which is a featured [**ToastGenericHeroImage**](toast-schema.md#toastgenericheroimage) displayed prominently within the toast banner and while inside Action Center.</span></span> <span data-ttu-id="04e96-151">Bildabmessungen sind 364x180Pixel bei einer Skalierung von 100%.</span><span class="sxs-lookup"><span data-stu-id="04e96-151">Image dimensions are 364x180 pixels at 100% scaling.</span></span>

<img alt="Toast with hero image" src="images/toast-heroimage.jpg" width="364"/>

```csharp
new ToastBindingGeneric()
{
    ...

    HeroImage = new ToastGenericHeroImage()
    {
        Source = "https://picsum.photos/364/180?image=1043"
    }
}
```

```xml
<binding template="ToastGeneric">
    ...
    <image placement="hero" src="https://picsum.photos/364/180?image=1043"/>
</binding>
```


## <a name="inline-image"></a><span data-ttu-id="04e96-152">Inline-Bild</span><span class="sxs-lookup"><span data-stu-id="04e96-152">Inline image</span></span>

<span data-ttu-id="04e96-153">Sie können ein Inline-Bild in voller Breite bereitstellen, das angezeigt wird, wenn das Popup erweitert wird.</span><span class="sxs-lookup"><span data-stu-id="04e96-153">You can provide a full-width inline-image that appears when you expand the toast.</span></span>

<img alt="Toast with additional image" src="images/toast-additionalimage.jpg" width="364"/>

```csharp
new ToastBindingGeneric()
{
    Children =
    {
        ...

        new AdaptiveImage()
        {
            Source = "https://picsum.photos/360/202?image=1043"
        }
    }
}
```

```xml
<binding template="ToastGeneric">
    ...
    <image src="https://picsum.photos/360/202?image=1043" />
</binding>
```


## <a name="image-size-restrictions"></a><span data-ttu-id="04e96-154">Größenbeschränkung</span><span class="sxs-lookup"><span data-stu-id="04e96-154">Image size restrictions</span></span>

<span data-ttu-id="04e96-155">Die Bilder, die Sie in Ihre Popupbenachrichtigung verwenden, können von folgenden Quellen kommen...</span><span class="sxs-lookup"><span data-stu-id="04e96-155">The images you use in your toast notification can be sourced from...</span></span>

 - <span data-ttu-id="04e96-156">http://</span><span class="sxs-lookup"><span data-stu-id="04e96-156">http://</span></span>
 - <span data-ttu-id="04e96-157">ms-appx:///</span><span class="sxs-lookup"><span data-stu-id="04e96-157">ms-appx:///</span></span>
 - <span data-ttu-id="04e96-158">ms-appdata:///</span><span class="sxs-lookup"><span data-stu-id="04e96-158">ms-appdata:///</span></span>

<span data-ttu-id="04e96-159">Für http und https/Remotewebbilder gibt es Dateigrößenbeschränkungen für jedes einzelne Bild.</span><span class="sxs-lookup"><span data-stu-id="04e96-159">For http and https remote web images, there are limits on the file size of each individual image.</span></span> <span data-ttu-id="04e96-160">Im Fall Creators Update (16299) erhöhten wir die Beschränkung auf 3MB für normale Verbindungen und 1MB für getaktete Verbindungen.</span><span class="sxs-lookup"><span data-stu-id="04e96-160">In the Fall Creators Update (16299), we increased the limit to be 3 MB on normal connections and 1 MB on metered connections.</span></span> <span data-ttu-id="04e96-161">Davor waren Bilder immer auf 200KB begrenzt.</span><span class="sxs-lookup"><span data-stu-id="04e96-161">Before that, images were always limited to 200 KB.</span></span>

| <span data-ttu-id="04e96-162">Normale Verbindung</span><span class="sxs-lookup"><span data-stu-id="04e96-162">Normal connection</span></span> | <span data-ttu-id="04e96-163">Getaktete Verbindung</span><span class="sxs-lookup"><span data-stu-id="04e96-163">Metered connection</span></span> | <span data-ttu-id="04e96-164">Vor dem Fall Creators Update</span><span class="sxs-lookup"><span data-stu-id="04e96-164">Before Fall Creators Update</span></span> |
| - | - | - |
| <span data-ttu-id="04e96-165">3 MB</span><span class="sxs-lookup"><span data-stu-id="04e96-165">3 MB</span></span> | <span data-ttu-id="04e96-166">1 MB</span><span class="sxs-lookup"><span data-stu-id="04e96-166">1 MB</span></span> | <span data-ttu-id="04e96-167">200 KB</span><span class="sxs-lookup"><span data-stu-id="04e96-167">200 KB</span></span> |

<span data-ttu-id="04e96-168">Wenn ein Bild die Dateigröße überschreitet oder nicht herunterladbar ist oder ein Timeout hervorruft, wird das Bild verworfen, und der Rest der Benachrichtigung wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="04e96-168">If an image exceeds the file size, or fails to download, or times out, the image will be dropped and the rest of the notification will be displayed.</span></span>


## <a name="attribution-text"></a><span data-ttu-id="04e96-169">Zuschreibungstext</span><span class="sxs-lookup"><span data-stu-id="04e96-169">Attribution text</span></span>

<span data-ttu-id="04e96-170">**Neu im Anniversary Update**: Wenn Sie die Quelle des Inhalts angeben müssen, können Sie Zuschreibungstext verwenden.</span><span class="sxs-lookup"><span data-stu-id="04e96-170">**New in Anniversary Update**: If you need to reference the source of your content, you can use attribution text.</span></span> <span data-ttu-id="04e96-171">Dieser Text wird zusammen mit der Identität Ihrer App oder dem Zeitstempel der Benachrichtigung immer am unteren Rand der Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="04e96-171">This text is always displayed at the bottom of your notification, along with your app's identity or the notification's timestamp.</span></span>

<span data-ttu-id="04e96-172">Für ältere Versionen von Windows, die Zuschreibungstext nicht unterstützen, wird der Text einfach als weiteres Textelement angezeigt (sofern Sie nicht bereits die maximalen drei Textelemente verwenden).</span><span class="sxs-lookup"><span data-stu-id="04e96-172">On older versions of Windows that don't support attribution text, the text will simply be displayed as another text element (assuming you don't already have the maximum of three text elements).</span></span>

<img alt="Toast with attribution text" src="images/toast-attributiontext.jpg" width="364"/>

```csharp
new ToastBindingGeneric()
{
    ...

    Attribution = new ToastGenericAttributionText()
    {
        Text = "Via SMS"
    }
}
```

```xml
<binding template="ToastGeneric">
    ...
    <text placement="attribution">Via SMS</text>
</binding>
```


## <a name="custom-timestamp"></a><span data-ttu-id="04e96-173">Benutzerdefinierter Zeitstempel</span><span class="sxs-lookup"><span data-stu-id="04e96-173">Custom timestamp</span></span>

<span data-ttu-id="04e96-174">**Neu im Creators Update**: Sie können jetzt den vom System bereitgestellten Zeitstempel mit Ihrem eigenen Zeitstempel überschreiben, der genau angibt, wann die Nachricht/die Informationen/der Inhalt erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="04e96-174">**New in Creators Update**: You can now override the system-provided timestamp with your own timestamp that accurately represents when the message/information/content was generated.</span></span> <span data-ttu-id="04e96-175">Dieser Zeitstempel wird im Info-Center angezeigt.</span><span class="sxs-lookup"><span data-stu-id="04e96-175">This timestamp is visible within Action Center.</span></span>

<img alt="Toast with custom timestamp" src="images/toast-customtimestamp.jpg" width="396"/>

<span data-ttu-id="04e96-176">Weitere Informationen zum Verwenden eines benutzerdefinierten Zeitstempels [benutzerdefinierten Zeitstempel für Popups](custom-timestamps-on-toasts.md).</span><span class="sxs-lookup"><span data-stu-id="04e96-176">To learn more about using a custom timestamp, please see [custom timestamps on toasts](custom-timestamps-on-toasts.md).</span></span>

```csharp
ToastContent toastContent = new ToastContent()
{
    DisplayTimestamp = new DateTime(2017, 04, 15, 19, 45, 00, DateTimeKind.Utc),
    ...
};
```

```xml
<toast displayTimestamp="2017-04-15T19:45:00Z">
  ...
</toast>
```


## <a name="progress-bar"></a><span data-ttu-id="04e96-177">Statusanzeige</span><span class="sxs-lookup"><span data-stu-id="04e96-177">Progress bar</span></span>

<span data-ttu-id="04e96-178">**Neu im Creators Update**: Sie können eine Statusanzeige für Ihre Popupbenachrichtigung bereitstellen, damit die Benutzer über den Status der Vorgänge, z.B. Downloads und vieles mehr, informiert werden.</span><span class="sxs-lookup"><span data-stu-id="04e96-178">**New in Creators Update**: You can provide a progress bar on your toast notification to keep the user informed of the progress of operations, like downloads and more.</span></span>

<img alt="Toast with progress bar" src="images/toast-progressbar.png" width="364"/>

<span data-ttu-id="04e96-179">Weitere Informationen zur Verwendung einer Statusanzeige finden Sie unter [Popup-Statusanzeige](toast-progress-bar.md).</span><span class="sxs-lookup"><span data-stu-id="04e96-179">To learn more about using a progress bar, please see [Toast progress bar](toast-progress-bar.md).</span></span>


## <a name="headers"></a><span data-ttu-id="04e96-180">Header</span><span class="sxs-lookup"><span data-stu-id="04e96-180">Headers</span></span>

<span data-ttu-id="04e96-181">**Neu im Creators Update**: Sie können Benachrichtigungen unter dem Header im Info-Center gruppieren.</span><span class="sxs-lookup"><span data-stu-id="04e96-181">**New in Creators Update**: You can group notifications under headers within Action Center.</span></span> <span data-ttu-id="04e96-182">Beispielsweise können Sie einen Gruppenchat unter einem Header zusammenfassen, oder einer Gruppenbenachrichtigungen unter einem Header zusammenfassen oder mehr.</span><span class="sxs-lookup"><span data-stu-id="04e96-182">For example, you can group messages from a group chat under a header, or group notifications of a common theme under a header, or more.</span></span>

<img alt="Toasts with header" src="images/toast-headers-action-center.png" width="396"/>

<span data-ttu-id="04e96-183">Weitere Informationen zum Verwenden von Headern finden Sie unter [Toast headers](toast-headers.md).</span><span class="sxs-lookup"><span data-stu-id="04e96-183">To learn more about using headers, please see [Toast headers](toast-headers.md).</span></span>


## <a name="adaptive-content"></a><span data-ttu-id="04e96-184">Adaptiver Inhalt</span><span class="sxs-lookup"><span data-stu-id="04e96-184">Adaptive content</span></span>

<span data-ttu-id="04e96-185">**Neu im Anniversary Update**: Zusätzlich zu dem oben angegebenen Inhalt können Sie auch zusätzlichen adaptiven Inhalt anzeigen, der sichtbar ist, wenn das Popup erweitert wird.</span><span class="sxs-lookup"><span data-stu-id="04e96-185">**New in Anniversary Update**: In addition to the content specified above, you can also display additional adaptive content that is visible when the toast is expanded.</span></span>

<span data-ttu-id="04e96-186">Dieser zusätzliche Inhalt wird mit Adaptive angegeben. Mehr zu diesem Thema erfahren Sie in der [Dokumentation zu adaptiven Kacheln](create-adaptive-tiles.md).</span><span class="sxs-lookup"><span data-stu-id="04e96-186">This additional content is specified using Adaptive, which you can learn more about by reading the [Adaptive Tiles documentation](create-adaptive-tiles.md).</span></span>

<span data-ttu-id="04e96-187">Beachten Sie, dass jeglicher adaptiver Inhalt in einer [**AdaptiveGroup**](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/toast-schema#adaptivegroup) enthalten sein müssen.</span><span class="sxs-lookup"><span data-stu-id="04e96-187">Note that any adaptive content must be contained within an [**AdaptiveGroup**](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/toast-schema#adaptivegroup).</span></span> <span data-ttu-id="04e96-188">Andernfalls wird der nicht mit Adaptive gerendert.</span><span class="sxs-lookup"><span data-stu-id="04e96-188">Otherwise it will not be rendered using adaptive.</span></span>


### <a name="columns-and-text-elements"></a><span data-ttu-id="04e96-189">Spalten und Textelemente</span><span class="sxs-lookup"><span data-stu-id="04e96-189">Columns and text elements</span></span>

<span data-ttu-id="04e96-190">Hier ist ein Beispiel, in dem Spalten und einige erweiterte adaptive Textelemente verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="04e96-190">Here's an example where columns and some advanced adaptive text elements are used.</span></span> <span data-ttu-id="04e96-191">Da die Textelemente in einer **AdaptiveGroup** enthalten sind, unterstützen sie alle erweiterten adaptiven Stileigenschaften.</span><span class="sxs-lookup"><span data-stu-id="04e96-191">Since the text elements are within an **AdaptiveGroup**, they support all the rich adaptive styling properties.</span></span>

<img alt="Toast with additional text" src="images/toast-additionaltext.jpg" width="364"/>

```csharp
new ToastBindingGeneric()
{
    Children =
    {
        ...

        new AdaptiveGroup()
        {
            Children =
            {
                new AdaptiveSubgroup()
                {
                    Children =
                    {
                        new AdaptiveText()
                        {
                            Text = "52 attendees",
                            HintStyle = AdaptiveTextStyle.Base
                        },
                        new AdaptiveText()
                        {
                            Text = "23 minute drive",
                            HintStyle = AdaptiveTextStyle.CaptionSubtle
                        }
                    }
                },
                new AdaptiveSubgroup()
                {
                    Children =
                    {
                        new AdaptiveText()
                        {
                            Text = "1 Microsoft Way",
                            HintStyle = AdaptiveTextStyle.CaptionSubtle,
                            HintAlign = AdaptiveTextAlign.Right
                        },
                        new AdaptiveText()
                        {
                            Text = "Bellevue, WA 98008",
                            HintStyle = AdaptiveTextStyle.CaptionSubtle,
                            HintAlign = AdaptiveTextAlign.Right
                        }
                    }
                }
            }
        }
    }
}
```

```xml
<binding template="ToastGeneric">
    ...
    <group>
        <subgroup>
            <text hint-style="base">52 attendees</text>
            <text hint-style="captionSubtle">23 minute drive</text>
        </subgroup>
        <subgroup>
            <text hint-style="captionSubtle" hint-align="right">1 Microsoft Way</text>
            <text hint-style="captionSubtle" hint-align="right">Bellevue, WA 98008</text>
        </subgroup>
    </group>
</binding>
```


## <a name="buttons"></a><span data-ttu-id="04e96-192">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="04e96-192">Buttons</span></span>

<span data-ttu-id="04e96-193">Schaltflächen machen Ihr Popup interaktiv. Sie erlauben dem Benutzer, in Ihrer Popupbenachrichtigung schnelle Aktionen auszuführen, ohne den aktuellen Workflow zu unterbrechen.</span><span class="sxs-lookup"><span data-stu-id="04e96-193">Buttons make your toast interactive, letting the user take quick actions on your toast notification without interrupting their current workflow.</span></span> <span data-ttu-id="04e96-194">Benutzer können z.B. eine Nachricht direkt in einem Popup beantworten oder eine E-Mail löschen, ohne die E-Mail-App überhaupt zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="04e96-194">For example, users can reply to a message directly from within a toast, or delete an email without even opening the email app.</span></span> <span data-ttu-id="04e96-195">Schaltflächen werden im erweiterten Teil der Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="04e96-195">Buttons appear in the expanded portion of your notification.</span></span>

<span data-ttu-id="04e96-196">Weitere Informationen zur Implementierung von Schaltflächen End-to-End finden Sie unter [Lokale Popups senden](send-local-toast.md).</span><span class="sxs-lookup"><span data-stu-id="04e96-196">To learn more about implementing buttons end-to-end, see [Send local toast](send-local-toast.md).</span></span>

<span data-ttu-id="04e96-197">Schaltflächen können die folgenden verschiedenen Aktionen ausführen...</span><span class="sxs-lookup"><span data-stu-id="04e96-197">Buttons can perform the following different actions...</span></span>

-   <span data-ttu-id="04e96-198">Aktivieren der App im Vordergrund mit einem Argument, das zum Navigieren zu einer bestimmten Seite bzw. einem bestimmten Kontext verwendet werden kann</span><span class="sxs-lookup"><span data-stu-id="04e96-198">Activating the app in the foreground, with an argument that can be used to navigate to a specific page/context.</span></span>
-   <span data-ttu-id="04e96-199">Aktivieren der Hintergrundaufgabe der App für eine schnelle Antwort oder ein ähnliches Szenario</span><span class="sxs-lookup"><span data-stu-id="04e96-199">Activating the app's background task, for a quick-reply or similar scenario.</span></span>
-   <span data-ttu-id="04e96-200">Aktivieren einer anderen App per Protokollstart</span><span class="sxs-lookup"><span data-stu-id="04e96-200">Activating another app via protocol launch.</span></span>
-   <span data-ttu-id="04e96-201">Durchführen einer Systemaktion, z.B. erneute Erinnerung oder Schließen der Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="04e96-201">Performing a system action, like snoozing or dismissing the notification.</span></span>

> [!NOTE]
> <span data-ttu-id="04e96-202">Sie können nur bis zu 5 Schaltflächen haben (einschließlich Elementen des Kontextmenüs, die später erläutert werden).</span><span class="sxs-lookup"><span data-stu-id="04e96-202">You can only have up to 5 buttons (including context menu items which we discuss later).</span></span>

<img alt="notification with actions, example 1" src="images/adaptivetoasts-xmlsample02.jpg" width="364"/>

```csharp
ToastContent content = new ToastContent()
{
    ...
 
    Actions = new ToastActionsCustom()
    {
        Buttons =
        {
            new ToastButton("See more details", "action=viewdetails&contentId=351")
            {
                ActivationType = ToastActivationType.Foreground
            },

            new ToastButton("Remind me later", "action=remindlater&contentId=351")
            {
                ActivationType = ToastActivationType.Background
            }
        }
    }
};
```

```xml
<toast launch="app-defined-string">

    ...

    <actions>

        <action
            content="See more details"
            arguments="action=viewdetails&amp;contentId=351"
            activationType="foreground"/>

        <action
            content="Remind me later"
            arguments="action=remindlater&amp;contentId=351"
            activationType="background"/>

    </actions>

</toast>
```


### <a name="buttons-with-icons"></a><span data-ttu-id="04e96-203">Schaltflächen mit Symbolen</span><span class="sxs-lookup"><span data-stu-id="04e96-203">Buttons with icons</span></span>

<span data-ttu-id="04e96-204">Sie können Ihren Schaltflächen Symbole hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="04e96-204">You can add icons to your buttons.</span></span> <span data-ttu-id="04e96-205">Diese Symbole sind weiße, transparente und 16 x 16 Pixel große Bilder mit einer Skalierung von 100%. Sie sollten keinen Abstand enthalten in dem Bild selbst enthalten.</span><span class="sxs-lookup"><span data-stu-id="04e96-205">These icons are white transparent 16x16 pixel images at 100% scaling, and should have no padding included in the image itself.</span></span> <span data-ttu-id="04e96-206">Wenn Sie Symbole auf eine Popupbenachrichtigung bereitstellen, müssen Sie die Symbole für alle Schaltflächen in der Benachrichtigung bereitstellen, da es den Stil der Schaltflächen in der Symbolschaltflächen umwandelt.</span><span class="sxs-lookup"><span data-stu-id="04e96-206">If you choose to provide icons on a toast notification, you must provide icons for ALL of your buttons in the notification, as it transforms the style of your buttons into icon buttons.</span></span>

> [!NOTE]
> <span data-ttu-id="04e96-207">Fügen Sie für mehr Barrierefreiheit eine Version mit Kontrast (weiß) für das Symbol hinzu (ein schwarzes Symbol auf weißem Hintergrund): Wenn der Benutzer den Modus „Hoher Kontrast (Weiß)“ aktiviert, wird das Symbol angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="04e96-207">For accessibility, be sure to include a contrast-white version of the icon (a black icon for white backgrounds), so that when the user turns on High Contrast White mode, your icon is visible.</span></span> <span data-ttu-id="04e96-208">Erfahren Sie mehr auf der [Seite für Popup-Bedienungshilfen](tile-toast-language-scale-contrast.md).</span><span class="sxs-lookup"><span data-stu-id="04e96-208">Learn more on the [toast accessiblity page](tile-toast-language-scale-contrast.md).</span></span>

<img src="images\adaptivetoasts-buttonswithicons.png" width="364" alt="Toast that has buttons with icons"/>

```csharp
new ToastButton("Dismiss", "dismiss")
{
    ActivationType = ToastActivationType.Background,
    ImageUri = "Assets/ToastButtonIcons/Dismiss.png"
}
```


```xml
<action
    content="Dismiss"
    imageUri="Assets/ToastButtonIcons/Dismiss.png"
    arguments="dismiss"
    activationType="background"/>
```


### <a name="buttons-with-pending-update-activation"></a><span data-ttu-id="04e96-209">Schaltflächen mit ausstehenden Updates in Aktion</span><span class="sxs-lookup"><span data-stu-id="04e96-209">Buttons with pending update activation</span></span>

<span data-ttu-id="04e96-210">**Neu im Fall Creators Update**: Bei Schaltflächen für die Hintergrundaktivierung können Sie nach dem Aktivierungsverhalten **PendingUpdate** mehrere Interaktionsschritte in Popupbenachrichtigungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="04e96-210">**New in Fall Creators Update**: On background activation buttons, you can use an after activation behavior of **PendingUpdate** to create multi-step interactions in your toast notifications.</span></span> <span data-ttu-id="04e96-211">Wenn der Benutzer die Schaltfläche anklickt, wird die Hintergrundaufgabe aktiviert und das Popup wird in den Zustand "ausstehendes Update" versetzt, ein Zustand, in dem es auf dem Bildschirm bleibt, bis die Hintergrundaufgabe das Popup durch eine neue Popupbenachrichtigung ersetzt wird.</span><span class="sxs-lookup"><span data-stu-id="04e96-211">When the user clicks your button, your background task is activated, and the toast gets placed in a "pending update" state, where it stays on screen till your background task replaces the toast with a new toast.</span></span>

<span data-ttu-id="04e96-212">Informationen zur Implementierung finden Sie unter [ausstehende Updates für Popups](toast-pending-update.md).</span><span class="sxs-lookup"><span data-stu-id="04e96-212">To learn how to implement this, see [Toast pending update](toast-pending-update.md).</span></span>

![Popup mit ausstehendem Update](images/toast-pendingupdate.gif)


### <a name="context-menu-actions"></a><span data-ttu-id="04e96-214">Kontextmenüaktionen</span><span class="sxs-lookup"><span data-stu-id="04e96-214">Context menu actions</span></span>

<span data-ttu-id="04e96-215">**Neu im Anniversary Update**: Sie können dem existierenden Kontextmenü zusätzliche Kontextmenüaktionen hinzufügen, die angezeigt werden, wenn der Benutzer mit der rechten Maustaste auf das Popup im Info-Center klickt.</span><span class="sxs-lookup"><span data-stu-id="04e96-215">**New in Anniversary Update**: You can add additional context menu actions to the existing context menu that appears when the user right clicks your toast from within Action Center.</span></span> <span data-ttu-id="04e96-216">Beachten Sie, dass dieses Menü nur angezeigt wird, wenn der Benutzer mit der rechten Maustaste auf das Info-Center klickt.</span><span class="sxs-lookup"><span data-stu-id="04e96-216">Note that this menu only appears when right clicked from Action Center.</span></span> <span data-ttu-id="04e96-217">Es wird nicht angezeigt, wenn der Benutzer mit der rechten Maustaste auf ein Popup-Banner klickt.</span><span class="sxs-lookup"><span data-stu-id="04e96-217">It does not appear when right clicking a toast popup banner.</span></span>

> [!NOTE]
> <span data-ttu-id="04e96-218">Bei älteren Geräten werden diese zusätzlichen Kontextmenüaktionen einfach als normale Schaltflächen im Popup angezeigt.</span><span class="sxs-lookup"><span data-stu-id="04e96-218">On older devices, these additional context menu actions will simply appear as normal buttons on your toast.</span></span>

<span data-ttu-id="04e96-219">Die zusätzlichen Kontextmenüaktionen, die Sie hinzufügen (wie. "Pfad ändern"), werden über die zwei standardmäßigen Systemeinträge angezeigt.</span><span class="sxs-lookup"><span data-stu-id="04e96-219">The additional context menu actions you add (like "Change location") appear above the two default system entries.</span></span>

<img alt="Toast with context menu" src="images/toast-contextmenu.png" width="444"/>

```csharp
ToastContent content = new ToastContent()
{
    ...
 
    Actions = new ToastActionsCustom()
    {
        ContextMenuItems =
        {
            new ToastContextMenuItem("Change location", "action=changeLocation")
        }
    }
};
```

```xml
<toast>

    ...

    <actions>

        <action
            placement="contextMenu"
            content="Change location"
            arguments="action=changeLocation"/>

    </actions>

</toast>
```

> [!NOTE]
> <span data-ttu-id="04e96-220">Zusätzliche Kontextmenüelemente tragen zu dem Gesamtlimit von 5 Schaltflächen für eine Popupbenachrichtigung bei.</span><span class="sxs-lookup"><span data-stu-id="04e96-220">Additional context menu items contribute to the total limit of 5 buttons on a toast.</span></span>

<span data-ttu-id="04e96-221">Die Aktivierung der zusätzlichen Menüelementkontexte ist identisch mit den Schaltflächen für die Popupbenachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="04e96-221">Activation of additional context menu items is handled identical to toast buttons.</span></span>


## <a name="inputs"></a><span data-ttu-id="04e96-222">Eingaben</span><span class="sxs-lookup"><span data-stu-id="04e96-222">Inputs</span></span>

<span data-ttu-id="04e96-223">Eingaben werden innerhalb des Bereichs „Aktionen“ der Popupregion des Popups angegeben. Das bedeutet, dass sie nur angezeigt werden, wenn das Popup erweitert wird.</span><span class="sxs-lookup"><span data-stu-id="04e96-223">Inputs are specified within the Actions region of the toast region of the toast, meaning they are only visible when the toast is expanded.</span></span>


### <a name="quick-reply-text-box"></a><span data-ttu-id="04e96-224">Textfeld für schnelle Antworten</span><span class="sxs-lookup"><span data-stu-id="04e96-224">Quick reply text box</span></span>

<span data-ttu-id="04e96-225">Um ein Textfeld für schnelle Antworten– etwa für ein Nachrichten-Szenario – zu aktivieren, fügen Sie eine Texteingabe und eine Schaltfläche hinzu, und verweisen Sie auf die ID der Texteingabe, damit die Schaltfläche neben der Eingabe angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="04e96-225">To enable a quick reply text box, like for a messaging scenario, add a text input and a button, and reference the text input's id so that the button is displayed adjacent to the input.</span></span>

<img alt="notification with text input and actions" src="images/adaptivetoasts-xmlsample05.jpg" width="364"/>

```csharp
ToastContent content = new ToastContent()
{
    ...
 
    Actions = new ToastActionsCustom()
    {
        Inputs =
        {
            new ToastTextBox("tbReply")
            {
                PlaceholderContent = "Type a reply"
            }
        },

        Buttons =
        {
            new ToastButton("Reply", "action=reply&convId=9318")
            {
                ActivationType = ToastActivationType.Background,

                // To place the button next to the text box,
                // reference the text box's Id and provide an image
                TextBoxId = "tbReply",
                ImageUri = "Assets/Reply.png"
            }
        }
    }
};
```

```xml
<toast launch="app-defined-string">

    ...

    <actions>

        <input id="textBox" type="text" placeHolderContent="Type a reply"/>

        <action
            content="Send"
            arguments="action=reply&amp;convId=9318"
            activationType="background"
            hint-inputId="textBox"
            imageUri="Assets/Reply.png"/>

    </actions>

</toast>
```


### <a name="inputs-with-buttons-bar"></a><span data-ttu-id="04e96-226">Eingaben mit Schaltflächenleiste</span><span class="sxs-lookup"><span data-stu-id="04e96-226">Inputs with buttons bar</span></span>

<span data-ttu-id="04e96-227">Es können auch eine oder mehrere Eingaben mit normalen Schaltflächen unterhalb der Eingaben angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="04e96-227">You also can have one (or many) inputs with normal buttons displayed below the inputs.</span></span>

<img alt="notification with text and input actions" src="images/adaptivetoasts-xmlsample04.jpg" width="364"/>

```csharp
ToastContent content = new ToastContent()
{
    ...
 
    Actions = new ToastActionsCustom()
    {
        Inputs =
        {
            new ToastTextBox("tbReply")
            {
                PlaceholderContent = "Type a reply"
            }
        },

        Buttons =
        {
            new ToastButton("Reply", "action=reply&threadId=9218")
            {
                ActivationType = ToastActivationType.Background
            },

            new ToastButton("Video call", "action=videocall&threadId=9218")
            {
                ActivationType = ToastActivationType.Foreground
            }
        }
    }
};
```

```xml
<toast launch="app-defined-string">

    ...

    <actions>

        <input id="textBox" type="text" placeHolderContent="Type a reply"/>

        <action
            content="Reply"
            arguments="action=reply&amp;threadId=9218"
            activationType="background"/>

        <action
            content="Video call"
            arguments="action=videocall&amp;threadId=9218"
            activationType="foreground"/>

    </actions>

</toast>
```


### <a name="selection-input"></a><span data-ttu-id="04e96-228">Auswahleingabe</span><span class="sxs-lookup"><span data-stu-id="04e96-228">Selection input</span></span>

<span data-ttu-id="04e96-229">Zusätzlich zu Textfeldern können Sie auch ein Auswahlmenü verwenden.</span><span class="sxs-lookup"><span data-stu-id="04e96-229">In addition to text boxes, you can also use a selection menu.</span></span>

<img alt="notification with selection input and actions" src="images/adaptivetoasts-xmlsample06.jpg" width="364"/>

```csharp
ToastContent content = new ToastContent()
{
    ...
 
    Actions = new ToastActionsCustom()
    {
        Inputs =
        {
            new ToastSelectionBox("time")
            {
                DefaultSelectionBoxItemId = "lunch",
                Items =
                {
                    new ToastSelectionBoxItem("breakfast", "Breakfast"),
                    new ToastSelectionBoxItem("lunch", "Lunch"),
                    new ToastSelectionBoxItem("dinner", "Dinner")
                }
            }
        },

        Buttons = { ... }
};
```

```xml
<toast launch="app-defined-string">

    ...

    <actions>

        <input id="time" type="selection" defaultInput="lunch">
            <selection id="breakfast" content="Breakfast" />
            <selection id="lunch" content="Lunch" />
            <selection id="dinner" content="Dinner" />
        </input>

        ...

    </actions>

</toast>
```


### <a name="snoozedismiss"></a><span data-ttu-id="04e96-230">Erneutes Erinnern/Schließen</span><span class="sxs-lookup"><span data-stu-id="04e96-230">Snooze/dismiss</span></span>

<span data-ttu-id="04e96-231">Mithilfe eines Auswahlmenüs und zwei Schaltflächen können wir eine Erinnerungsbenachrichtigung erstellen, welche die Systemaktionen zum erneuten Erinnern und Schließen verwendet.</span><span class="sxs-lookup"><span data-stu-id="04e96-231">Using a selection menu and two buttons, we can create a reminder notification that utilizes the system snooze and dismiss actions.</span></span> <span data-ttu-id="04e96-232">Legen Sie unbedingt das Szenario für die Benachrichtigung auf „Erinnerung“ fest, damit sie sich wie eine Erinnerung verhält.</span><span class="sxs-lookup"><span data-stu-id="04e96-232">Make sure to set the scenario to Reminder for the notification to behave like a reminder.</span></span>

<img alt="reminder notification" src="images/adaptivetoasts-xmlsample07.jpg" width="364"/>

<span data-ttu-id="04e96-233">Wir verknüpfen die Schaltfläche „Erneut erinnern“ mithilfe der **SelectionBoxId**-Eigenschaft der Popupschaltfläche mit der Auswahlmenüeingabe.</span><span class="sxs-lookup"><span data-stu-id="04e96-233">We link the Snooze button to the selection menu input using the **SelectionBoxId** property on the toast button.</span></span>

```csharp
ToastContent content = new ToastContent()
{
    Scenario = ToastScenario.Reminder,

    ...
 
    Actions = new ToastActionsCustom()
    {
        Inputs =
        {
            new ToastSelectionBox("snoozeTime")
            {
                DefaultSelectionBoxItemId = "15",
                Items =
                {
                    new ToastSelectionBoxItem("5", "5 minutes"),
                    new ToastSelectionBoxItem("15", "15 minutes"),
                    new ToastSelectionBoxItem("60", "1 hour"),
                    new ToastSelectionBoxItem("240", "4 hours"),
                    new ToastSelectionBoxItem("1440", "1 day")
                }
            }
        },

        Buttons =
        {
            new ToastButtonSnooze()
            {
                SelectionBoxId = "snoozeTime"
            },
 
            new ToastButtonDismiss()
        }
    }
};
```

```xml
<toast scenario="reminder" launch="action=viewEvent&amp;eventId=1983">
   
  ...
 
  <actions>
     
    <input id="snoozeTime" type="selection" defaultInput="15">
      <selection id="1" content="1 minute"/>
      <selection id="15" content="15 minutes"/>
      <selection id="60" content="1 hour"/>
      <selection id="240" content="4 hours"/>
      <selection id="1440" content="1 day"/>
    </input>
 
    <action activationType="system" arguments="snooze" hint-inputId="snoozeTime" content="" />
 
    <action activationType="system" arguments="dismiss" content=""/>
     
  </actions>
   
</toast>
```

<span data-ttu-id="04e96-234">Gehen Sie wie folgt vor, um die Systemaktionen zum erneuten Erinnern und Schließen zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="04e96-234">To use the system snooze and dismiss actions:</span></span>

-   <span data-ttu-id="04e96-235">Angeben eines **ToastButtonSnooze** oder **ToastButtonDismiss**</span><span class="sxs-lookup"><span data-stu-id="04e96-235">Specify a **ToastButtonSnooze** or **ToastButtonDismiss**</span></span>
-   <span data-ttu-id="04e96-236">Geben Sie optional eine benutzerdefinierte Inhaltszeichenfolge an:</span><span class="sxs-lookup"><span data-stu-id="04e96-236">Optionally specify a custom content string:</span></span>
    -   <span data-ttu-id="04e96-237">Wenn Sie keine Zeichenfolge bereitstellen, verwenden wir für „Erneut erinnern“ und „Schließen“ automatisch lokalisierte Zeichenfolgen.</span><span class="sxs-lookup"><span data-stu-id="04e96-237">If you don't provide a string, we'll automatically use localized strings for "Snooze" and "Dismiss".</span></span>
-   <span data-ttu-id="04e96-238">Geben Sie optional die **SelectionBoxId** an:</span><span class="sxs-lookup"><span data-stu-id="04e96-238">Optionally specify the **SelectionBoxId**:</span></span>
    -   <span data-ttu-id="04e96-239">Wenn Sie nicht möchten, dass der Benutzer ein Intervall für das erneute Erinnern auswählen kann, sondern das erneute Erinnern an die Benachrichtigung nur einmal in einem vom System definierten (in allen Betriebssystemen einheitlichen) Zeitintervall erfolgt, legen Sie keinen Wert für &lt;input&gt; fest.</span><span class="sxs-lookup"><span data-stu-id="04e96-239">If you don't want the user to select a snooze interval and instead just want your notification to snooze only once for a system-defined time interval (that is consistent across the OS), then don't construct any &lt;input&gt; at all.</span></span>
    -   <span data-ttu-id="04e96-240">Wenn Sie Intervalle für das erneute Erinnern angeben möchten:</span><span class="sxs-lookup"><span data-stu-id="04e96-240">If you want to provide snooze interval selections:</span></span>
        -   <span data-ttu-id="04e96-241">Geben Sie **SelectionBoxId** in der Aktion für das erneute Erinnern an</span><span class="sxs-lookup"><span data-stu-id="04e96-241">Specify **SelectionBoxId** in the snooze action</span></span>
        -   <span data-ttu-id="04e96-242">Stimmen Sie die ID der Eingabe auf den Wert für **SelectionBoxId** der Aktion für das erneute Erinnern ab</span><span class="sxs-lookup"><span data-stu-id="04e96-242">Match the id of the input with the **SelectionBoxId** of the snooze action</span></span>
        -   <span data-ttu-id="04e96-243">Legen Sie für den Wert von **ToastSelectionBoxItem** eine positive ganze Zahl (nonNegativeInteger) fest, die dem Intervall für das erneute Erinnern in Minuten entspricht.</span><span class="sxs-lookup"><span data-stu-id="04e96-243">Specify **ToastSelectionBoxItem**'s value to be a nonNegativeInteger which represents snooze interval in minutes.</span></span>



## <a name="audio"></a><span data-ttu-id="04e96-244">Audio</span><span class="sxs-lookup"><span data-stu-id="04e96-244">Audio</span></span>

<span data-ttu-id="04e96-245">Benutzerdefinierte Audioeffekte wurden schon immer von Mobile unterstützt und wird in der Desktop-Version 1511 (Build 10586) oder einer neueren Version unterstützt.</span><span class="sxs-lookup"><span data-stu-id="04e96-245">Custom audio has always been supported by Mobile, and is supported in Desktop Version 1511 (build 10586) or newer.</span></span> <span data-ttu-id="04e96-246">Benutzerdefinierte Audioeffekte können über die folgenden Pfade verwiesen werden:</span><span class="sxs-lookup"><span data-stu-id="04e96-246">Custom audio can be referenced via the following paths:</span></span>

-   <span data-ttu-id="04e96-247">ms-appx:///</span><span class="sxs-lookup"><span data-stu-id="04e96-247">ms-appx:///</span></span>
-   <span data-ttu-id="04e96-248">ms-appdata:///</span><span class="sxs-lookup"><span data-stu-id="04e96-248">ms-appdata:///</span></span>

<span data-ttu-id="04e96-249">Sie können alternativ aus der [Liste "ms-winsoundevents"](/uwp/schemas/tiles/toastschema/element-audio#attributes-and-elements) auswählen, welche bisher immer auf beiden Plattformen unterstützt wurden.</span><span class="sxs-lookup"><span data-stu-id="04e96-249">Alternatively, you can pick from the [list of ms-winsoundevents](/uwp/schemas/tiles/toastschema/element-audio#attributes-and-elements), which have always been supported on both platforms.</span></span>

```csharp
ToastContent content = new ToastContent()
{
    ...

    Audio = new ToastAudio()
    {
        Src = new Uri("ms-appx:///Assets/NewMessage.mp3")
    }
}
```

```xml
<toast launch="app-defined-string">

    ...

    <audio src="ms-appx:///Assets/NewMessage.mp3"/>

</toast>
```

<span data-ttu-id="04e96-250">Erhalten Sie unter der [Seite](/uwp/schemas/tiles/toastschema/element-audio) Informationen zu Töne für Popupbenachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="04e96-250">See the [audio schema page](/uwp/schemas/tiles/toastschema/element-audio) for information on audio in toast notifications.</span></span> <span data-ttu-id="04e96-251">Informationen für das Senden einer Popupbenachrichtigung mit benutzerdefinierten Audioeffekten finden Sie unter [benutzerdefiniertes Audio auf Popups](custom-audio-on-toasts.md).</span><span class="sxs-lookup"><span data-stu-id="04e96-251">To learn how to send a toast using custom audio, see [custom audio on toasts](custom-audio-on-toasts.md).</span></span>


## <a name="alarms-reminders-and-incoming-calls"></a><span data-ttu-id="04e96-252">Alarme, Erinnerungen und eingehende Anrufe</span><span class="sxs-lookup"><span data-stu-id="04e96-252">Alarms, reminders, and incoming calls</span></span>

<span data-ttu-id="04e96-253">Um Alarme, Erinnerungen und Benachrichtigungen über eingehende Anrufe zu erstellen, verwenden Sie einfach eine normale Popupbenachrichtigung mit einem zugewiesenen Szenariowert.</span><span class="sxs-lookup"><span data-stu-id="04e96-253">To create alarms, reminders, and incoming call notifications, you simply use a normal toast notification with a scenario value assigned to it.</span></span> <span data-ttu-id="04e96-254">Das Szenario umfasst einige Verhaltensweisen, um eine konsistente und einheitliche Benutzererfahrung zu schaffen.</span><span class="sxs-lookup"><span data-stu-id="04e96-254">The scenario adusts a few behaviors to create a consistent and unified user experience.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="04e96-255">Wenn Sie Alarme oder Erinnerungen verwenden, müssen Sie mindestens eine Schaltfläche auf Ihrer Popupbenachrichtigung angeben.</span><span class="sxs-lookup"><span data-stu-id="04e96-255">When using Reminder or Alarm, you must provide at least one button on your toast notification.</span></span> <span data-ttu-id="04e96-256">Andernfalls wird das Popup als ein normales Popup behandelt.</span><span class="sxs-lookup"><span data-stu-id="04e96-256">Otherwise, the toast will be treated as a normal toast.</span></span>

* <span data-ttu-id="04e96-257">**Erinnerung**: Die Benachrichtigung bleibt auf dem Bildschirm, bis der Benutzer sie schließt oder eine Aktion ausführt.</span><span class="sxs-lookup"><span data-stu-id="04e96-257">**Reminder**: The notification will stay on screen until the user dismisses it or takes action.</span></span> <span data-ttu-id="04e96-258">Unter Windows Mobile wird das Popup auch vorab vergrößert angezeigt.</span><span class="sxs-lookup"><span data-stu-id="04e96-258">On Windows Mobile, the toast will also show pre-expanded.</span></span> <span data-ttu-id="04e96-259">Ein Erinnerungston wird wiedergegeben.</span><span class="sxs-lookup"><span data-stu-id="04e96-259">A reminder sound will be played.</span></span>
* <span data-ttu-id="04e96-260">**Alarm**: Zusätzlich zu den Erinnerungsverhaltensweisen wird bei Alarmen zusätzlich eine Audioschleife mit einem standardmäßigen Alarmton wiedergegeben.</span><span class="sxs-lookup"><span data-stu-id="04e96-260">**Alarm**: In addition to the reminder behaviors, alarms will additionally loop audio with a default alarm sound.</span></span>
* <span data-ttu-id="04e96-261">**IncomingCall**: Benachrichtigungen über eingehende Anrufe werden auf Windows Mobile-Geräten im Vollbildmodus angezeigt.</span><span class="sxs-lookup"><span data-stu-id="04e96-261">**IncomingCall**: Incoming call notifications are displayed full screen on Windows Mobile devices.</span></span> <span data-ttu-id="04e96-262">Andernfalls weisen sie die gleichen Verhaltensweisen wie Alarme auf, außer dass sie einen Klingelton verwenden und die Schaltflächen anders aussehen.</span><span class="sxs-lookup"><span data-stu-id="04e96-262">Otherwise, they have the same behaviors as alarms except they use ringtone audio and their buttons are styled differently.</span></span>

```csharp
ToastContent content = new ToastContent()
{
    Scenario = ToastScenario.Reminder,

    ...
}
```

```xml
<toast scenario="reminder" launch="app-defined-string">

    ...

</toast>
```


## <a name="localization-and-accessibility"></a><span data-ttu-id="04e96-263">Lokalisierung und Bedienungshilfen</span><span class="sxs-lookup"><span data-stu-id="04e96-263">Localization and accessibility</span></span>

<span data-ttu-id="04e96-264">Ihre Kacheln und Popups können Zeichenfolgen und Bilder laden, die speziell auf die Sprache, den Skalierungsfaktor für die Anzeige, das Design, den hohen Kontrast und anderen Laufzeitkontexte angepasst wurden.</span><span class="sxs-lookup"><span data-stu-id="04e96-264">Your tiles and toasts can load strings and images tailored for display language, display scale factor, high contrast, and other runtime contexts.</span></span> <span data-ttu-id="04e96-265">Weitere Informationen finden Sie unter [Unterstützte Kachel- und Popupbenachrichtigungen für Sprache, Skalierungsfaktor und hohen Kontrast](tile-toast-language-scale-contrast.md)</span><span class="sxs-lookup"><span data-stu-id="04e96-265">For more info, see [Tile and toast notification support for language, scale, and high contrast](tile-toast-language-scale-contrast.md).</span></span>


## <a name="handling-activation"></a><span data-ttu-id="04e96-266">Behandeln der Aktivierung</span><span class="sxs-lookup"><span data-stu-id="04e96-266">Handling activation</span></span>
<span data-ttu-id="04e96-267">Informationen dazu, wie Sie Popupaktivierungen behandeln (der Benutzer klickt auf Ihr Popup oder auf Schaltflächen im Popup), finden Sie unter [Senden einer lokalen Popupbenachrichtigung](send-local-toast.md).</span><span class="sxs-lookup"><span data-stu-id="04e96-267">To learn how to handle toast activations (the user clicking your toast or buttons on the toast), see [Send local toast](send-local-toast.md).</span></span>
 
## <a name="related-topics"></a><span data-ttu-id="04e96-268">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="04e96-268">Related topics</span></span>

* [<span data-ttu-id="04e96-269">Senden einer lokalen Popupbenachrichtigung und Behandeln der Aktivierung</span><span class="sxs-lookup"><span data-stu-id="04e96-269">Send a local toast and handle activation</span></span>](send-local-toast.md)
* [<span data-ttu-id="04e96-270">Benachrichtigungsbibliothek auf GitHub (Teil des UWP Community-Toolkit)</span><span class="sxs-lookup"><span data-stu-id="04e96-270">Notifications library on GitHub (part of the UWP Community Toolkit)</span></span>](https://github.com/Microsoft/UWPCommunityToolkit/tree/master/Microsoft.Toolkit.Uwp.Notifications)
* [<span data-ttu-id="04e96-271">Unterstützte Kachel- und Popupbenachrichtigungen für Sprache, Skalierungsfaktor und hohen Kontrast</span><span class="sxs-lookup"><span data-stu-id="04e96-271">Tile and toast notification support for language, scale, and high contrast</span></span>](tile-toast-language-scale-contrast.md)
