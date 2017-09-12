---
author: mijacobs
Description: "Mit adaptiven und interaktiven Popupbenachrichtigungen können Sie flexible Popupbenachrichtigungen mit mehr Inhalt, optionalen Inlinebildern und optionaler Benutzerinteraktion erstellen."
title: Adaptive und interaktive Popupbenachrichtigungen
ms.assetid: 1FCE66AF-34B4-436A-9FC9-D0CF4BDA5A01
label: Adaptive and interactive toast notifications
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.openlocfilehash: c8e77773b9118c3177dc958ddc7b51d32a452fa5
ms.sourcegitcommit: 9d1ca16a7edcbbcae03fad50a4a10183a319c63a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2017
---
# <a name="adaptive-and-interactive-toast-notifications"></a><span data-ttu-id="75634-104">Adaptive und interaktive Popupbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="75634-104">Adaptive and interactive toast notifications</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

<span data-ttu-id="75634-105">Mit adaptiven und interaktiven Popupbenachrichtigungen können Sie flexible Benachrichtigungen mit Text, Bildern und Schaltflächen/Eingaben erstellen.</span><span class="sxs-lookup"><span data-stu-id="75634-105">Adaptive and interactive toast notifications let you create flexible notifications with text, images, and buttons/inputs.</span></span>

> <span data-ttu-id="75634-106">**Wichtige APIs**: [UWP Community Toolkit Notifications-NuGet-Paket](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/)</span><span class="sxs-lookup"><span data-stu-id="75634-106">**Important APIs**: [UWP Community Toolkit Notifications nuget package](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/)</span></span>

> [!NOTE]
> <span data-ttu-id="75634-107">Die Legacyvorlagen von Windows8.1 und Windows Phone8.1 finden Sie im [Legacy-Popupvorlagenkatalog](https://msdn.microsoft.com/library/windows/apps/hh761494).</span><span class="sxs-lookup"><span data-stu-id="75634-107">To see the legacy templates from Windows 8.1 and Windows Phone 8.1, see the [legacy toast template catalog](https://msdn.microsoft.com/library/windows/apps/hh761494).</span></span>


## <a name="getting-started"></a><span data-ttu-id="75634-108">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="75634-108">Getting started</span></span>

**<span data-ttu-id="75634-109">Installieren Sie die Benachrichtigungsbibliothek.</span><span class="sxs-lookup"><span data-stu-id="75634-109">Install Notifications library.</span></span>** <span data-ttu-id="75634-110">Wenn Sie C# anstelle von XML verwenden möchten, um Benachrichtigungen zu generieren, installieren Sie das NuGet-Paket mit dem Namen [Microsoft.Toolkit.Uwp.Notifications](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/). (Suchen Sie nach „Benachrichtigungen UWP“.)</span><span class="sxs-lookup"><span data-stu-id="75634-110">If you'd like to use C# instead of XML to generate notifications, install the NuGet package named [Microsoft.Toolkit.Uwp.Notifications](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) (search for "notifications uwp").</span></span> <span data-ttu-id="75634-111">Die in diesem Artikel bereitgestellten C#-Beispiele verwenden Version 1.0.0 des NuGet-Pakets.</span><span class="sxs-lookup"><span data-stu-id="75634-111">The C# samples provided in this article use version 1.0.0 of the NuGet package.</span></span>

**<span data-ttu-id="75634-112">Installieren Sie den Notifications Visualizer.</span><span class="sxs-lookup"><span data-stu-id="75634-112">Install Notifications Visualizer.</span></span>** <span data-ttu-id="75634-113">Diese kostenlose UWP-App hilft Ihnen, interaktive Popupbenachrichtigungen zu entwerfen, indem sie während der Bearbeitung des Popups sofort eine Vorschau des Popups bereitstellen, ähnlich dem XAML-Editor/der Entwurfsansicht von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="75634-113">This free UWP app helps you design interactive toast notifications by providing an instant visual preview of your toast as you edit it, similar to Visual Studio's XAML editor/design view.</span></span> <span data-ttu-id="75634-114">Weitere Informationen finden Sie in [diesem Blogbeitrag](http://blogs.msdn.com/b/tiles_and_toasts/archive/2015/09/22/introducing-notifications-visualizer-for-windows-10.aspx). Der Download von Notifications Visualizer steht [hier](https://www.microsoft.com/store/apps/notifications-visualizer/9nblggh5xsl1) bereit.</span><span class="sxs-lookup"><span data-stu-id="75634-114">You can read [this blog post](http://blogs.msdn.com/b/tiles_and_toasts/archive/2015/09/22/introducing-notifications-visualizer-for-windows-10.aspx) for more information, and you can download Notifications Visualizer [here](https://www.microsoft.com/store/apps/notifications-visualizer/9nblggh5xsl1).</span></span>


## <a name="sending-a-toast-notification"></a><span data-ttu-id="75634-115">Senden einer Popupbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="75634-115">Sending a toast notification</span></span>

<span data-ttu-id="75634-116">Weitere Informationen zum Senden einer Benachrichtigung finden Sie unter [Senden einer lokalen Popupbenachrichtigung](tiles-and-notifications-send-local-toast.md).</span><span class="sxs-lookup"><span data-stu-id="75634-116">To learn how to send a notification, see [Send local toast](tiles-and-notifications-send-local-toast.md).</span></span> <span data-ttu-id="75634-117">In dieser Dokumentation wird nur die Erstellung des Popupinhalts behandelt.</span><span class="sxs-lookup"><span data-stu-id="75634-117">This documentation only covers creating the toast content.</span></span>


## <a name="toast-notification-structure"></a><span data-ttu-id="75634-118">Struktur der Popupbenachrichtigung</span><span class="sxs-lookup"><span data-stu-id="75634-118">Toast notification structure</span></span>

<span data-ttu-id="75634-119">Popupbenachrichtigungen sind eine Kombination aus einigen Dateneigenschaften wie Tag/Group (mit denen Sie die Benachrichtigung identifizieren können) und dem *Popupinhalt*.</span><span class="sxs-lookup"><span data-stu-id="75634-119">Toast notifications are a combination of some data properties like Tag/Group (which let you identify the notification) and the *toast content*.</span></span>

<span data-ttu-id="75634-120">Die Kernkomponenten des Popupinhalts sind...</span><span class="sxs-lookup"><span data-stu-id="75634-120">The core components of toast content are...</span></span>
* <span data-ttu-id="75634-121">**launch**: Hiermit wird definiert, welche Argumente wieder an Ihre App übergeben werden, wenn der Benutzer auf Ihr Popup klickt, sodass Sie einen Deep-Link zum richtigen Inhalt bereitstellen können, der im Popup angezeigt wurde.</span><span class="sxs-lookup"><span data-stu-id="75634-121">**launch**: This defines what arguments will be passed back to your app when the user clicks your toast, allowing you to deep link into the correct content that the toast was displaying.</span></span> <span data-ttu-id="75634-122">Weitere Informationen hierzu finden Sie unter [Senden einer lokalen Popupbenachrichtigung](tiles-and-notifications-send-local-toast.md).</span><span class="sxs-lookup"><span data-stu-id="75634-122">To learn more, see [Send local toast](tiles-and-notifications-send-local-toast.md).</span></span>
* <span data-ttu-id="75634-123">**visual**: der visuelle Teil des Popups, einschließlich der generischen Bindung, die Text, Bilder und App-Logos enthält</span><span class="sxs-lookup"><span data-stu-id="75634-123">**visual**: The visual portion of the toast, including the generic binding that contains text, images, and app logos.</span></span>
* <span data-ttu-id="75634-124">**actions**: der interaktive Teil des Popups, einschließlich Eingaben und Aktionen</span><span class="sxs-lookup"><span data-stu-id="75634-124">**actions**: The interactive portion of the toast, including inputs and actions.</span></span>
* <span data-ttu-id="75634-125">**audio**: steuert die Tonwiedergabe, während dem Benutzer das Popup angezeigt wird</span><span class="sxs-lookup"><span data-stu-id="75634-125">**audio**: Controls the audio played when the toast is shown to the user.</span></span>

<span data-ttu-id="75634-126">Der Popupinhalt ist in XML-Rohdaten definiert, aber Sie können unsere [NuGet-Bibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) verwenden, um ein C# (oder C++)-Objektmodell für die Erstellung des Popupinhalts zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="75634-126">The toast content is defined in raw XML, but you can use our [NuGet library](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) to get a C# (or C++) object model for constructing the toast content.</span></span> <span data-ttu-id="75634-127">In diesem Artikel werden alle Elemente des Popupinhalts dokumentiert.</span><span class="sxs-lookup"><span data-stu-id="75634-127">This article documents everything that goes within the toast content.</span></span>

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

<span data-ttu-id="75634-128">Hier sehen Sie eine visuelle Darstellung des Inhalts des Popups:</span><span class="sxs-lookup"><span data-stu-id="75634-128">Here is a visual representation of the toast's content:</span></span>

![Aufbau einer Popupbenachrichtigung](images/adaptivetoasts-structure.jpg)


## <a name="visual"></a><span data-ttu-id="75634-130">Visuelles Element</span><span class="sxs-lookup"><span data-stu-id="75634-130">Visual</span></span>

<span data-ttu-id="75634-131">Jedes Popup muss ein visuelles Element angeben, in dem Sie eine generische Popupbindung angeben müssen, die Text, Bilder, Logos und vieles mehr enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="75634-131">Each toast must specify a visual, where you must provide a generic toast binding, which can contain text, images, logos, and more.</span></span> <span data-ttu-id="75634-132">Diese Elemente werden auf verschiedenen Windows-Geräten wie Desktops, Smartphones, Tablets und Xbox wiedergegeben.</span><span class="sxs-lookup"><span data-stu-id="75634-132">These elements will be rendered on various Windows devices, including desktop, phones, tablets, and Xbox.</span></span>

<span data-ttu-id="75634-133">Alle Attribute, die im Abschnitt „Visuelle Elemente“ unterstützt werden, sowie die untergeordneten Elemente [finden Sie in der Schemadokumentation](tiles-and-notifications-toast-schema.md#toastvisual).</span><span class="sxs-lookup"><span data-stu-id="75634-133">For all attributes supported in the visual section and its child elements, [see the schema documentation](tiles-and-notifications-toast-schema.md#toastvisual).</span></span>

<span data-ttu-id="75634-134">Die Identität Ihrer App in der Popupbenachrichtigung wird über Ihr App-Symbol angegeben.</span><span class="sxs-lookup"><span data-stu-id="75634-134">Your app's identity on the toast notification is conveyed via your app icon.</span></span> <span data-ttu-id="75634-135">Wenn Sie jedoch die App-Logo-Überschreibung verwenden, wird der Name Ihrer App unterhalb der Textzeilen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="75634-135">However, if you use the app logo override, we will display your app name beneath your lines of text.</span></span>

| <span data-ttu-id="75634-136">Normales Popupfenster</span><span class="sxs-lookup"><span data-stu-id="75634-136">Normal toast</span></span>                                                                              | <span data-ttu-id="75634-137">Popupfenster mit appLogoOverride</span><span class="sxs-lookup"><span data-stu-id="75634-137">Toast with appLogoOverride</span></span>                                                          |
| ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| ![Benachrichtigung ohne appLogoOverride](images/adaptivetoasts-withoutapplogooverride.jpg) | ![Benachrichtigung mit appLogoOverride](images/adaptivetoasts-withapplogooverride.jpg) |


## <a name="text-elements"></a><span data-ttu-id="75634-140">Textelemente</span><span class="sxs-lookup"><span data-stu-id="75634-140">Text elements</span></span>

<span data-ttu-id="75634-141">Jedes Popup muss mindestens ein Textelement enthalten und kann zwei zusätzliche Textelemente enthalten, wobei alle den Typ [AdaptiveText](tiles-and-notifications-toast-schema.md#adaptivetext) aufweisen müssen.</span><span class="sxs-lookup"><span data-stu-id="75634-141">Each toast must have at least one text element, and can contain two additional text elements, all of type [AdaptiveText](tiles-and-notifications-toast-schema.md#adaptivetext).</span></span>

![Popup mit Titel und Beschreibung](images/toast-title-and-description.jpg)

<span data-ttu-id="75634-143">Seit dem Anniversary Update können Sie mithilfe der **HintMaxLines**-Eigenschaft für den Text steuern, wie viele Zeilen Text angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="75634-143">Since the Anniversary Update, you can control how many lines of text are displayed by using the **HintMaxLines** property on the text.</span></span> <span data-ttu-id="75634-144">In der Standardeinstellung werden im Titel zeigt bis zu 2 Textzeilen angezeigt. Die Beschreibungszeilen zeigen jeweils bis zu 4 Textzeilen an.</span><span class="sxs-lookup"><span data-stu-id="75634-144">By default, the title displays up to 2 lines of text, and the description lines each display up to 4 lines of text.</span></span>

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


## <a name="app-logo-override"></a><span data-ttu-id="75634-145">Überschreibung des App-Logos</span><span class="sxs-lookup"><span data-stu-id="75634-145">App logo override</span></span>

<span data-ttu-id="75634-146">Standardmäßig zeigt das Popup Ihr App-Logo an.</span><span class="sxs-lookup"><span data-stu-id="75634-146">By default, your toast will display your app's logo.</span></span> <span data-ttu-id="75634-147">Allerdings können Sie dieses Logo mit Ihrem eigenen [ToastGenericAppLogo](tiles-and-notifications-toast-schema.md#toastgenericapplogo)-Bild überschreiben.</span><span class="sxs-lookup"><span data-stu-id="75634-147">However, you can override this logo with your own [ToastGenericAppLogo](tiles-and-notifications-toast-schema.md#toastgenericapplogo) image.</span></span> <span data-ttu-id="75634-148">Wenn es sich beispielsweise um eine Benachrichtigung von einer Person handelt, empfehlen wir, das App-Logo mit einem Bild der betreffenden Person zu überschreiben.</span><span class="sxs-lookup"><span data-stu-id="75634-148">For example, if this is a notification from a person, we recommend overriding the app logo with a picture of that person.</span></span>

![Popup mit App-Logo-Überschreibung](images/toast-applogooverride.jpg)

<span data-ttu-id="75634-150">Sie können die **HintCrop**-Eigenschaft verwenden, um den Zuschnitt des Bilds zu ändern.</span><span class="sxs-lookup"><span data-stu-id="75634-150">You can use the **HintCrop** property to change the cropping of the image.</span></span> <span data-ttu-id="75634-151">So ergibt *Kreis* z. B. ein kreisförmig zugeschnittenes Bild.</span><span class="sxs-lookup"><span data-stu-id="75634-151">For example, *circle* results in a circle-cropped image.</span></span> <span data-ttu-id="75634-152">Andernfalls ist das Bild quadratisch.</span><span class="sxs-lookup"><span data-stu-id="75634-152">Otherwise, the image is square.</span></span> <span data-ttu-id="75634-153">Bildabmessungen sind 64x64Pixel bei einer Skalierung von 100%.</span><span class="sxs-lookup"><span data-stu-id="75634-153">Image dimensions are 64x64 pixels at 100% scaling.</span></span>

```csharp
new ToastBindingGeneric()
{
    ...

    AppLogoOverride = new ToastGenericAppLogo()
    {
        Source = "https://unsplash.it/64?image=883",
        HintCrop = ToastGenericAppLogoCrop.Circle
    }
}
```

```xml
<binding template="ToastGeneric">
    ...
    <image placement="appLogoOverride" hint-crop="circle" src="https://unsplash.it/64?image=883"/>
</binding>
```


## <a name="hero-image"></a><span data-ttu-id="75634-154">Favoritenbild</span><span class="sxs-lookup"><span data-stu-id="75634-154">Hero image</span></span>

<span data-ttu-id="75634-155">**Neu im Anniversary Update**: Popups können ein Favoritenbild anzeigen. Dabei handelt es sich um ein ausgewähltes [ToastGenericHeroImage](tiles-and-notifications-toast-schema.md#toastgenericheroimage), das an hervorgehobener Stelle innerhalb des Popup-Banners und im Info-Center angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="75634-155">**New in Anniversary Update**: Toasts can display a hero image, which is a featured [ToastGenericHeroImage](tiles-and-notifications-toast-schema.md#toastgenericheroimage) displayed prominently within the toast banner and while inside Action Center.</span></span> <span data-ttu-id="75634-156">Bildabmessungen sind 360x180Pixel bei einer Skalierung von 100%.</span><span class="sxs-lookup"><span data-stu-id="75634-156">Image dimensions are 360x180 pixels at 100% scaling.</span></span>

![Popup mit Favoritenbild](images/toast-heroimage.jpg)

```csharp
new ToastBindingGeneric()
{
    ...

    HeroImage = new ToastHeroImage()
    {
        Source = "https://unsplash.it/360/180?image=1043"
    }
}
```

```xml
<binding template="ToastGeneric">
    ...
    <image placement="hero" src="https://unsplash.it/360/180?image=1043"/>
</binding>
```


## <a name="inline-image"></a><span data-ttu-id="75634-158">Inline-Bild</span><span class="sxs-lookup"><span data-stu-id="75634-158">Inline image</span></span>

<span data-ttu-id="75634-159">Sie können ein Inline-Bild in voller Breite bereitstellen, das angezeigt wird, wenn das Popup erweitert wird.</span><span class="sxs-lookup"><span data-stu-id="75634-159">You can provide a full-width inline-image that appears when you expand the toast.</span></span>

![Popup mit zusätzlichem Bild](images/toast-additionalimage.jpg)

```csharp
new ToastBindingGeneric()
{
    Children =
    {
        ...

        new AdaptiveImage()
        {
            Source = "https://unsplash.it/360/180?image=1043"
        }
    }
}
```

```xml
<binding template="ToastGeneric">
    ...
    <image src="https://unsplash.it/360/180?image=1043" />
</binding>
```


## <a name="attribution-text"></a><span data-ttu-id="75634-161">Zuschreibungstext</span><span class="sxs-lookup"><span data-stu-id="75634-161">Attribution text</span></span>

<span data-ttu-id="75634-162">**Neu im Anniversary Update**: Wenn Sie die Quelle des Inhalts angeben müssen, können Sie Zuschreibungstext verwenden.</span><span class="sxs-lookup"><span data-stu-id="75634-162">**New in Anniversary Update**: If you need to reference the source of your content, you can use attribution text.</span></span> <span data-ttu-id="75634-163">Dieser Text wird zusammen mit der Identität Ihrer App oder dem Zeitstempel der Benachrichtigung immer am unteren Rand der Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="75634-163">This text is always displayed at the bottom of your notification, along with your app's identity or the notification's timestamp.</span></span>

<span data-ttu-id="75634-164">Für ältere Versionen von Windows, die Zuschreibungstext nicht unterstützen, wird der Text einfach als weiteres Textelement angezeigt (sofern Sie nicht bereits die maximalen drei Textelemente verwenden).</span><span class="sxs-lookup"><span data-stu-id="75634-164">On older versions of Windows that don't support attribution text, the text will simply be displayed as another text element (assuming you don't already have the maximum of three text elements).</span></span>

![Popup mit Zuschreibungstext](images/toast-attributiontext.jpg)

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


## <a name="custom-timestamp"></a><span data-ttu-id="75634-166">Benutzerdefinierter Zeitstempel</span><span class="sxs-lookup"><span data-stu-id="75634-166">Custom timestamp</span></span>

<span data-ttu-id="75634-167">**Neu im Creators Update**: Sie können jetzt den vom System bereitgestellten Zeitstempel mit Ihrem eigenen Zeitstempel überschreiben, der genau angibt, wann die Nachricht/die Informationen/der Inhalt erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="75634-167">**New in Creators Update**: You can now override the system-provided timestamp with your own timestamp that accurately represents when the message/information/content was generated.</span></span> <span data-ttu-id="75634-168">Dieser Zeitstempel wird im Info-Center angezeigt.</span><span class="sxs-lookup"><span data-stu-id="75634-168">This timestamp is visible within Action Center.</span></span>

![Popup mit benutzerdefiniertem Zeitstempel](images/toast-customtimestamp.jpg)

<span data-ttu-id="75634-170">Weitere Informationen zum Verwenden eines benutzerdefinierten Zeitstempels [finden Sie in diesem Blogbeitrag](https://blogs.msdn.microsoft.com/tiles_and_toasts/2017/01/09/custom-timestamp-on-toast-notifications-windows-10-creators-update/).</span><span class="sxs-lookup"><span data-stu-id="75634-170">To learn more about using a custom timestamp, please [see this blog post](https://blogs.msdn.microsoft.com/tiles_and_toasts/2017/01/09/custom-timestamp-on-toast-notifications-windows-10-creators-update/).</span></span>

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


## <a name="adaptive-content"></a><span data-ttu-id="75634-171">Adaptiver Inhalt</span><span class="sxs-lookup"><span data-stu-id="75634-171">Adaptive content</span></span>

<span data-ttu-id="75634-172">**Neu im Anniversary Update**: Zusätzlich zu dem oben angegebenen Inhalt können Sie auch zusätzlichen adaptiven Inhalt anzeigen, der sichtbar ist, wenn das Popup erweitert wird.</span><span class="sxs-lookup"><span data-stu-id="75634-172">**New in Anniversary Update**: In addition to the content specified above, you can also display additional adaptive content that is visible when the toast is expanded.</span></span>

<span data-ttu-id="75634-173">Dieser zusätzliche Inhalt wird mit Adaptive angegeben. Mehr zu diesem Thema erfahren Sie in der [Dokumentation zu adaptiven Kacheln](tiles-and-notifications-create-adaptive-tiles.md).</span><span class="sxs-lookup"><span data-stu-id="75634-173">This additional content is specified using Adaptive, which you can learn more about by reading the [Adaptive Tiles documentation](tiles-and-notifications-create-adaptive-tiles.md).</span></span>

<span data-ttu-id="75634-174">Beachten Sie, dass jeglicher adaptiver Inhalt in einer AdaptiveGroup enthalten sein müssen.</span><span class="sxs-lookup"><span data-stu-id="75634-174">Note that any adaptive content must be contained within an AdaptiveGroup.</span></span> <span data-ttu-id="75634-175">Andernfalls wird der nicht mit Adaptive gerendert.</span><span class="sxs-lookup"><span data-stu-id="75634-175">Otherwise it will not be rendered using adaptive.</span></span>


### <a name="columns-and-text-elements"></a><span data-ttu-id="75634-176">Spalten und Textelemente</span><span class="sxs-lookup"><span data-stu-id="75634-176">Columns and text elements</span></span>

<span data-ttu-id="75634-177">Hier ist ein Beispiel, in dem Spalten und einige erweiterte adaptive Textelemente verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="75634-177">Here's an example where columns and some advanced adaptive text elements are used.</span></span> <span data-ttu-id="75634-178">Da die Textelemente in einer AdaptiveGroup enthalten sind, unterstützen sie alle erweiterten adaptiven Stileigenschaften.</span><span class="sxs-lookup"><span data-stu-id="75634-178">Since the text elements are within an AdaptiveGroup, they support all the rich adaptive styling properties.</span></span>

![Popup mit zusätzlichem Text](images/toast-additionaltext.jpg)

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


## <a name="inputs-and-buttons"></a><span data-ttu-id="75634-180">Eingaben und Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="75634-180">Inputs and buttons</span></span>

<span data-ttu-id="75634-181">Eingaben und Schaltflächen werden innerhalb des Bereichs „Aktionen“ der Popupregion des Popups angegeben. Das bedeutet, dass sie nur angezeigt werden, wenn das Popup erweitert wird.</span><span class="sxs-lookup"><span data-stu-id="75634-181">Inputs and buttons are specified within the Actions region of the toast region of the toast, meaning they are only visible when the toast is expanded.</span></span>


### <a name="quick-reply-text-box"></a><span data-ttu-id="75634-182">Textfeld für schnelle Antworten</span><span class="sxs-lookup"><span data-stu-id="75634-182">Quick reply text box</span></span>

<span data-ttu-id="75634-183">Um ein Textfeld für schnelle Antworten– etwa für ein Nachrichten-Szenario – zu aktivieren, fügen Sie eine Texteingabe und eine Schaltfläche hinzu, und verweisen Sie auf die ID der Texteingabe, damit die Schaltfläche neben der Eingabe angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="75634-183">To enable a quick reply text box, like for a messaging scenario, add a text input and a button, and reference the text input's id so that the button is displayed adjacent to the input.</span></span>

![Benachrichtigung mit Texteingabe und Aktionen](images/adaptivetoasts-xmlsample05.jpg)

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

        <input id="textBox" type="text" placeholderContent="Type a reply"/>

        <action
            content="Send",
            arguments="action=reply&amp;convId=9318"
            activationType="background"
            hint-inputId="textBox"
            imageUri="Assets/Reply.png"/>

    </actions>

</toast>
```


### <a name="inputs-with-buttons-bar"></a><span data-ttu-id="75634-185">Eingaben mit Schaltflächenleiste</span><span class="sxs-lookup"><span data-stu-id="75634-185">Inputs with buttons bar</span></span>

<span data-ttu-id="75634-186">Es können auch eine oder mehrere Eingaben mit normalen Schaltflächen unterhalb der Eingaben angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="75634-186">You also can have one (or many) inputs with normal buttons displayed below the inputs.</span></span>

![Benachrichtigung mit Text und Eingabeaktionen](images/adaptivetoasts-xmlsample04.jpg)

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

        <input id="textBox" type="text" placeholderContent="Type a reply"/>

        <action
            content="Reply",
            arguments="action=reply&amp;threadId=9218"
            activationType="background"/>

        <action
            content="Video call",
            arguments="action=videocall&amp;threadId=9218"
            activationType="foreground"/>

    </actions>

</toast>
```


### <a name="selection-input"></a><span data-ttu-id="75634-188">Auswahleingabe</span><span class="sxs-lookup"><span data-stu-id="75634-188">Selection input</span></span>

<span data-ttu-id="75634-189">Zusätzlich zu Textfeldern können Sie auch ein Auswahlmenü verwenden.</span><span class="sxs-lookup"><span data-stu-id="75634-189">In addition to text boxes, you can also use a selection menu.</span></span>

![Benachrichtigung mit Auswahleingabe und Aktionen](images/adaptivetoasts-xmlsample06.jpg)

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


## <a name="buttons"></a><span data-ttu-id="75634-191">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="75634-191">Buttons</span></span>

<span data-ttu-id="75634-192">Schaltflächen machen Ihr Popup interaktiv. Sie erlauben dem Benutzer, in Ihrer Popupbenachrichtigung schnelle Aktionen auszuführen, ohne den aktuellen Workflow zu unterbrechen.</span><span class="sxs-lookup"><span data-stu-id="75634-192">Buttons make your toast interactive, letting the user take quick actions on your toast notification without interrupting their current workflow.</span></span> <span data-ttu-id="75634-193">Benutzer können z.B. eine Nachricht direkt in einem Popup beantworten oder eine E-Mail löschen, ohne die E-Mail-App überhaupt zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="75634-193">For example, users can reply to a message directly from within a toast, or delete an email without even opening the email app.</span></span>

<span data-ttu-id="75634-194">Schaltflächen können die folgenden verschiedenen Aktionen ausführen...</span><span class="sxs-lookup"><span data-stu-id="75634-194">Buttons can perform the following different actions...</span></span>

-   <span data-ttu-id="75634-195">Aktivieren der App im Vordergrund mit einem Argument, das zum Navigieren zu einer bestimmten Seite bzw. einem bestimmten Kontext verwendet werden kann</span><span class="sxs-lookup"><span data-stu-id="75634-195">Activating the app in the foreground, with an argument that can be used to navigate to a specific page/context.</span></span>
-   <span data-ttu-id="75634-196">Aktivieren der Hintergrundaufgabe der App für eine schnelle Antwort oder ein ähnliches Szenario</span><span class="sxs-lookup"><span data-stu-id="75634-196">Activating the app's background task, for a quick-reply or similar scenario.</span></span>
-   <span data-ttu-id="75634-197">Aktivieren einer anderen App per Protokollstart</span><span class="sxs-lookup"><span data-stu-id="75634-197">Activating another app via protocol launch.</span></span>
-   <span data-ttu-id="75634-198">Durchführen einer Systemaktion, z.B. erneute Erinnerung oder Schließen der Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="75634-198">Performing a system action, like snoozing or dismissing the notification.</span></span>

<span data-ttu-id="75634-199">Beachten Sie, dass Sie nur bis zu 5 Schaltflächen haben können (einschließlich Elementen des Kontextmenüs, die später erläutert werden).</span><span class="sxs-lookup"><span data-stu-id="75634-199">Note that you can only have up to 5 buttons (including context menu items which we discuss later).</span></span>

![Benachrichtigung mit Aktionen, Beispiel1](images/adaptivetoasts-xmlsample02.jpg)

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
            content="See more details",
            arguments="action=viewdetails&amp;contentId=351"
            activationType="foreground"/>

        <action
            content="Remind me later",
            arguments="action=remindlater&amp;contentId=351"
            activationType="background"/>

    </actions>

</toast>
```


### <a name="snoozedismiss-buttons"></a><span data-ttu-id="75634-201">Schaltflächen für erneutes Erinnern/Schließen</span><span class="sxs-lookup"><span data-stu-id="75634-201">Snooze/dismiss buttons</span></span>

<span data-ttu-id="75634-202">Mithilfe eines Auswahlmenüs und zwei Schaltflächen können wir eine Erinnerungsbenachrichtigung erstellen, welche die Systemaktionen zum erneuten Erinnern und Schließen verwendet.</span><span class="sxs-lookup"><span data-stu-id="75634-202">Using a selection menu and two buttons, we can create a reminder notification that utilizes the system snooze and dismiss actions.</span></span> <span data-ttu-id="75634-203">Legen Sie unbedingt das Szenario für die Benachrichtigung auf „Erinnerung“ fest, damit sie sich wie eine Erinnerung verhält.</span><span class="sxs-lookup"><span data-stu-id="75634-203">Make sure to set the scenario to Reminder for the notification to behave like a reminder.</span></span>

![Erinnerungsbenachrichtigung](images/adaptivetoasts-xmlsample07.jpg)

<span data-ttu-id="75634-205">Wir verknüpfen die Schaltfläche „Erneut erinnern“ mithilfe der *SepectionBoxId*-Eigenschaft der Popupschaltfläche mit der Auswahlmenüeingabe.</span><span class="sxs-lookup"><span data-stu-id="75634-205">We link the Snooze button to the selection menu input using the *SepectionBoxId* property on the toast button.</span></span>

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

<span data-ttu-id="75634-206">Gehen Sie wie folgt vor, um die Systemaktionen zum erneuten Erinnern und Schließen zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="75634-206">To use the system snooze and dismiss actions, do the following:</span></span>

-   <span data-ttu-id="75634-207">Angeben eines ToastButtonSnooze oder ToastButtonDismiss</span><span class="sxs-lookup"><span data-stu-id="75634-207">Specify a ToastButtonSnooze or ToastButtonDismiss</span></span>
-   <span data-ttu-id="75634-208">Geben Sie optional eine benutzerdefinierte Inhaltszeichenfolge an:</span><span class="sxs-lookup"><span data-stu-id="75634-208">Optionally specify a custom content string:</span></span>
    -   <span data-ttu-id="75634-209">Wenn Sie keine Zeichenfolge bereitstellen, verwenden wir für „Erneut erinnern“ und „Schließen“ automatisch lokalisierte Zeichenfolgen.</span><span class="sxs-lookup"><span data-stu-id="75634-209">If you don't provide a string, we'll automatically use localized strings for "Snooze" and "Dismiss".</span></span>
-   <span data-ttu-id="75634-210">Geben Sie optional die *SelectionBoxId* an:</span><span class="sxs-lookup"><span data-stu-id="75634-210">Optionally specify the *SelectionBoxId*:</span></span>
    -   <span data-ttu-id="75634-211">Wenn Sie nicht möchten, dass der Benutzer ein Intervall für das erneute Erinnern auswählen kann, sondern das erneute Erinnern an die Benachrichtigung nur einmal in einem vom System definierten (in allen Betriebssystemen einheitlichen) Zeitintervall erfolgt, legen Sie keinen Wert für &lt;input&gt; fest.</span><span class="sxs-lookup"><span data-stu-id="75634-211">If you don't want the user to select a snooze interval and instead just want your notification to snooze only once for a system-defined time interval (that is consistent across the OS), then don't construct any &lt;input&gt; at all.</span></span>
    -   <span data-ttu-id="75634-212">Wenn Sie Intervalle für das erneute Erinnern angeben möchten:</span><span class="sxs-lookup"><span data-stu-id="75634-212">If you want to provide snooze interval selections:</span></span>
        -   <span data-ttu-id="75634-213">Geben Sie *SelectionBoxId* in der Aktion für das erneute Erinnern an</span><span class="sxs-lookup"><span data-stu-id="75634-213">Specify *SelectionBoxId* in the snooze action</span></span>
        -   <span data-ttu-id="75634-214">Stimmen Sie die ID der Eingabe auf den Wert für *SelectionBoxId* der Aktion für das erneute Erinnern ab</span><span class="sxs-lookup"><span data-stu-id="75634-214">Match the id of the input with the *SelectionBoxId* of the snooze action</span></span>
        -   <span data-ttu-id="75634-215">Legen Sie für den Wert von *ToastSelectionBoxItem* eine positive ganze Zahl (nonNegativeInteger) fest, die dem Intervall für das erneute Erinnern in Minuten entspricht.</span><span class="sxs-lookup"><span data-stu-id="75634-215">Specify *ToastSelectionBoxItem*'s value to be a nonNegativeInteger which represents snooze interval in minutes.</span></span>



## <a name="audio"></a><span data-ttu-id="75634-216">Audio</span><span class="sxs-lookup"><span data-stu-id="75634-216">Audio</span></span>

<span data-ttu-id="75634-217">Benutzerdefinierte Audioeffekte wurden schon immer von Mobile unterstützt und wird in der Desktop-Version 1511 (Build 10586) oder einer neueren Version unterstützt.</span><span class="sxs-lookup"><span data-stu-id="75634-217">Custom audio has always been supported by Mobile, and is supported in Desktop Version 1511 (build 10586) or newer.</span></span> <span data-ttu-id="75634-218">Benutzerdefinierte Audioeffekte können über die folgenden Pfade verwiesen werden:</span><span class="sxs-lookup"><span data-stu-id="75634-218">Custom audio can be referenced via the following paths:</span></span>

-   <span data-ttu-id="75634-219">ms-appx:///</span><span class="sxs-lookup"><span data-stu-id="75634-219">ms-appx:///</span></span>
-   <span data-ttu-id="75634-220">ms-appdata:///</span><span class="sxs-lookup"><span data-stu-id="75634-220">ms-appdata:///</span></span>

<span data-ttu-id="75634-221">Sie können alternativ aus der [Liste "ms-winsoundevents"](https://msdn.microsoft.com/library/windows/apps/br230842) auswählen, welche bisher immer auf beiden Plattformen unterstützt wurden.</span><span class="sxs-lookup"><span data-stu-id="75634-221">Alternatively, you can pick from the [list of ms-winsoundevents](https://msdn.microsoft.com/library/windows/apps/br230842), which have always been supported on both platforms.</span></span>

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

<span data-ttu-id="75634-222">Erhalten Sie unter der [Seite](https://msdn.microsoft.com/library/windows/apps/br230842) Informationen zu Töne für Popupbenachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="75634-222">See the [audio schema page](https://msdn.microsoft.com/library/windows/apps/br230842) for information on audio in toast notifications.</span></span> <span data-ttu-id="75634-223">Informationen für das Senden einer Popupbenachrichtigung mit benutzerdefinierten Audioeffekten [finden Sie unter folgenden Blogbeitrag](https://blogs.msdn.microsoft.com/tiles_and_toasts/2016/06/18/quickstart-sending-a-toast-notification-with-custom-audio/).</span><span class="sxs-lookup"><span data-stu-id="75634-223">To learn how to send a toast using custom audio, [see this blog post](https://blogs.msdn.microsoft.com/tiles_and_toasts/2016/06/18/quickstart-sending-a-toast-notification-with-custom-audio/).</span></span>


## <a name="alarms-reminders-and-incoming-calls"></a><span data-ttu-id="75634-224">Alarme, Erinnerungen und eingehende Anrufe</span><span class="sxs-lookup"><span data-stu-id="75634-224">Alarms, reminders, and incoming calls</span></span>

<span data-ttu-id="75634-225">Um Alarme, Erinnerungen und Benachrichtigungen über eingehende Anrufe zu erstellen, verwenden Sie einfach eine normale Popupbenachrichtigung mit einem zugewiesenen Szenariowert.</span><span class="sxs-lookup"><span data-stu-id="75634-225">To create alarms, reminders, and incoming call notifications, you simply use a normal toast notification with a scenario value assigned to it.</span></span> <span data-ttu-id="75634-226">Das Szenario umfasst einige Verhaltensweisen, um eine konsistente und einheitliche Benutzererfahrung zu schaffen.</span><span class="sxs-lookup"><span data-stu-id="75634-226">The scenario adusts a few behaviors to create a consistent and unified user experience.</span></span>

* <span data-ttu-id="75634-227">**Erinnerung**: Die Benachrichtigung bleibt auf dem Bildschirm, bis der Benutzer sie schließt oder eine Aktion ausführt.</span><span class="sxs-lookup"><span data-stu-id="75634-227">**Reminder**: The notification will stay on screen until the user dismisses it or takes action.</span></span> <span data-ttu-id="75634-228">Unter Windows Mobile wird das Popup auch vorab vergrößert angezeigt.</span><span class="sxs-lookup"><span data-stu-id="75634-228">On Windows Mobile, the toast will also show pre-expanded.</span></span> <span data-ttu-id="75634-229">Ein Erinnerungston wird wiedergegeben.</span><span class="sxs-lookup"><span data-stu-id="75634-229">A reminder sound will be played.</span></span>
* <span data-ttu-id="75634-230">**Alarm**: Zusätzlich zu den Erinnerungsverhaltensweisen wird bei Alarmen zusätzlich eine Audioschleife mit einem standardmäßigen Alarmton wiedergegeben.</span><span class="sxs-lookup"><span data-stu-id="75634-230">**Alarm**: In addition to the reminder behaviors, alarms will additionally loop audio with a default alarm sound.</span></span>
* <span data-ttu-id="75634-231">**IncomingCall**: Benachrichtigungen über eingehende Anrufe werden auf Windows Mobile-Geräten im Vollbildmodus angezeigt.</span><span class="sxs-lookup"><span data-stu-id="75634-231">**IncomingCall**: Incoming call notifications are displayed full screen on Windows Mobile devices.</span></span> <span data-ttu-id="75634-232">Andernfalls weisen sie die gleichen Verhaltensweisen wie Alarme auf, außer dass sie einen Klingelton verwenden.</span><span class="sxs-lookup"><span data-stu-id="75634-232">Otherwise, they have the same behaviors as alarms except they use ringtone audio.</span></span>

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


## <a name="handling-activation"></a><span data-ttu-id="75634-233">Behandeln der Aktivierung</span><span class="sxs-lookup"><span data-stu-id="75634-233">Handling activation</span></span>
<span data-ttu-id="75634-234">Informationen dazu, wie Sie Popupaktivierungen behandeln (der Benutzer klickt auf Ihr Popup oder auf Schaltflächen im Popup), finden Sie unter [Senden einer lokalen Popupbenachrichtigung](tiles-and-notifications-send-local-toast.md).</span><span class="sxs-lookup"><span data-stu-id="75634-234">To learn how to handle toast activations (the user clicking your toast or buttons on the toast), see [Send local toast](tiles-and-notifications-send-local-toast.md).</span></span>


 
## <a name="related-topics"></a><span data-ttu-id="75634-235">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="75634-235">Related topics</span></span>

* [<span data-ttu-id="75634-236">Senden einer lokalen Popupbenachrichtigung und Behandeln der Aktivierung</span><span class="sxs-lookup"><span data-stu-id="75634-236">Send a local toast and handle activation</span></span>](tiles-and-notifications-send-local-toast.md)
* [<span data-ttu-id="75634-237">Benachrichtigungsbibliothek auf GitHub</span><span class="sxs-lookup"><span data-stu-id="75634-237">Notifications library on GitHub</span></span>](https://github.com/Microsoft/UWPCommunityToolkit/tree/dev/Notifications)