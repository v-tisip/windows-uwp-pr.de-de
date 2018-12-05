---
title: Meine Kontakte – Benachrichtigungen
description: Erläutert das Erstellen und Verwenden von Benachrichtigungen für Meine Kontakte, eine neue Art Popups.
ms.date: 10/25/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: db25954b7fc6541ac5f5900236e61cb8da488be6
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8686343"
---
# <a name="my-people-notifications"></a><span data-ttu-id="f0ecb-104">Meine Kontakte – Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="f0ecb-104">My People notifications</span></span>

<span data-ttu-id="f0ecb-105">„Meine Kontakte”-Benachrichtigungen bieten Benutzern eine neue Möglichkeit, sich mit den Menschen, die ihnen wichtig sind, durch schnelle, ausdrucksstarke Gesten zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-105">My People notifications provide a new way for users to connect with the people they care about, through quick expressive gestures.</span></span> <span data-ttu-id="f0ecb-106">Dieser Artikel zeigt, wie Sie Meine Kontakte-Benachrichtigungen in Ihrer Anwendung entwerfen und implementieren.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-106">This article shows how to design and implement My People notifications in your application.</span></span> <span data-ttu-id="f0ecb-107">Vollständige Implementierungen finden Sie unter [Beispiel für „Meine Kontakte”.](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/MyPeopleNotifications)</span><span class="sxs-lookup"><span data-stu-id="f0ecb-107">For complete implementations, see the [My People Notifications Sample.](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/MyPeopleNotifications)</span></span>

![Herz-Emoji-Benachrichtigung](images/heart-emoji-notification-small.gif)

## <a name="requirements"></a><span data-ttu-id="f0ecb-109">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="f0ecb-109">Requirements</span></span>

+ <span data-ttu-id="f0ecb-110">Windows10 und Microsoft Visual Studio2017</span><span class="sxs-lookup"><span data-stu-id="f0ecb-110">Windows 10 and Microsoft Visual Studio 2017.</span></span> <span data-ttu-id="f0ecb-111">Ausführliche Informationen zur Installation finden Sie unter [Visual Studio einrichten](https://docs.microsoft.com/en-us/windows/uwp/get-started/get-set-up).</span><span class="sxs-lookup"><span data-stu-id="f0ecb-111">For installation details, see [Get set up with Visual Studio](https://docs.microsoft.com/en-us/windows/uwp/get-started/get-set-up).</span></span>
+ <span data-ttu-id="f0ecb-112">Sie sollten über Grundkenntnisse in C# oder einer ähnlichen objektorientierten Programmiersprache verfügen.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-112">Basic knowledge of C# or a similar object-oriented programming language.</span></span> <span data-ttu-id="f0ecb-113">Die ersten Schritte mit C# finden Sie unter [Erstellen der App „Hello, world“ (C++)](https://docs.microsoft.com/en-us/windows/uwp/get-started/create-a-hello-world-app-xaml-universal).</span><span class="sxs-lookup"><span data-stu-id="f0ecb-113">To get started with C#, see [Create a "Hello, world" app](https://docs.microsoft.com/en-us/windows/uwp/get-started/create-a-hello-world-app-xaml-universal).</span></span>

## <a name="how-it-works"></a><span data-ttu-id="f0ecb-114">Funktionsweise</span><span class="sxs-lookup"><span data-stu-id="f0ecb-114">How it works</span></span>

<span data-ttu-id="f0ecb-115">Als Alternative zur generischen Popupbenachrichtigungen können Sie jetzt Benachrichtigungen über das Feature „Meine Kontakte” senden, um eine persönlichere Erfahrung für Benutzer bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-115">As an alternative to generic toast notifications, you can now send notifications through the My People feature to provide a more personal experience to users.</span></span> <span data-ttu-id="f0ecb-116">Dies ist eine neue Art von Popup, das von einem Kontakt gesendet wird, der mit der Funktion „Meine Kontakte” auf der Taskleiste des Benutzers angeheftet ist.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-116">This is a new kind of toast, sent from a contact pinned on the user's taskbar with the My People feature.</span></span> <span data-ttu-id="f0ecb-117">Wenn die Benachrichtigung empfangen wird, wird das Bild des Kontakts auf der Taskleiste animiert und ein Sound wird abgespielt, was signalisiert, dass eine Benachrichtigung gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-117">When the notification is received, the sender’s contact picture will animate in the taskbar and a sound will play, signaling that the notification is starting.</span></span> <span data-ttu-id="f0ecb-118">Die Animation oder das in der Nutzlast angezeigte Bild werden für 5 Sekunden angezeigt (oder, wenn die Nutzlast eine Animation ist, die kürzer als 5 Sekunden dauert, wird diese wiederholt, bis die 5 Sekunden vorbei sind).</span><span class="sxs-lookup"><span data-stu-id="f0ecb-118">The animation or image specified in the payload will be displayed for 5 seconds (or, if the payload is an animation less than 5 seconds long, it will loop until 5 seconds have passed).</span></span>

## <a name="supported-image-types"></a><span data-ttu-id="f0ecb-119">Unterstützte Abbildtypen</span><span class="sxs-lookup"><span data-stu-id="f0ecb-119">Supported image types</span></span>

+ <span data-ttu-id="f0ecb-120">GIF</span><span class="sxs-lookup"><span data-stu-id="f0ecb-120">GIF</span></span>
+ <span data-ttu-id="f0ecb-121">Statisches Bild (JPEG, PNG)</span><span class="sxs-lookup"><span data-stu-id="f0ecb-121">Static Image (JPEG, PNG)</span></span>
+ <span data-ttu-id="f0ecb-122">Spritesheet (nur vertikal)</span><span class="sxs-lookup"><span data-stu-id="f0ecb-122">Spritesheet (vertical only)</span></span>

> [!NOTE]
> <span data-ttu-id="f0ecb-123">Ein Spritesheet ist eine Animation, die von einem statischen Bild (JPEG- oder PNG) abgeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-123">A spritesheet is an animation derived from a static image (JPEG or PNG).</span></span> <span data-ttu-id="f0ecb-124">Einzelne Frames werden vertikal angeordnet, so dass sich das erste Bild im Vordergrund befindet (Sie können eine andere Startframe in der Nutzlast der Popupbenachrichtigung angeben).</span><span class="sxs-lookup"><span data-stu-id="f0ecb-124">Individual frames are arranged vertically, such that the first frame is on top (though you can specify a different starting frame in the toast payload).</span></span> <span data-ttu-id="f0ecb-125">Jedes Frame muss die gleiche Höhe haben, damit das Programm diese wiederholt, um eine animierte Sequenz zu erstellen (z.B. wie ein Flipbook mit seinen Seiten, die vertikal angeordnet sind).</span><span class="sxs-lookup"><span data-stu-id="f0ecb-125">Each frame must have the same height, which the program loops through to create an animated sequence (like a flipbook with its pages laid out vertically).</span></span> <span data-ttu-id="f0ecb-126">Ein Beispiel für ein Spritesheet wird unten gezeigt.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-126">An example of a spritesheet is shown below.</span></span>

![Spritesheet in Regenbogenfarben](images/shoulder-tap-rainbow-spritesheet.png)

## <a name="notification-parameters"></a><span data-ttu-id="f0ecb-128">Benachrichtigungsparameter</span><span class="sxs-lookup"><span data-stu-id="f0ecb-128">Notification parameters</span></span>
<span data-ttu-id="f0ecb-129">Benachrichtigungen von „Meine Kontakte” verwenden die [Popupbenachrichtigung](../design/shell/tiles-and-notifications/adaptive-interactive-toasts.md)-Framework, aber erfordern einen zusätzlichen Bindungsknoten in der Nutzlast des Popups.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-129">My People notifications use the [toast notification](../design/shell/tiles-and-notifications/adaptive-interactive-toasts.md) framework, but require an additional binding node in the toast payload.</span></span> <span data-ttu-id="f0ecb-130">Die zweite Bindung muss folgende Parameter enthalten:</span><span class="sxs-lookup"><span data-stu-id="f0ecb-130">This second binding must include the following parameter:</span></span>

```xml
experienceType=”shoulderTap”
```

<span data-ttu-id="f0ecb-131">Dies bedeutet, dass das Popup als eine Benachrichtigung für „Meine Kontakte” behandelt werden soll.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-131">This indicates that the toast should be treated as a My People notification.</span></span>

<span data-ttu-id="f0ecb-132">Die Image-Knoten in der Bindung sollten die folgenden Parameter enthalten:</span><span class="sxs-lookup"><span data-stu-id="f0ecb-132">The image node inside the binding should include the following parameters:</span></span>

+ **<span data-ttu-id="f0ecb-133">src</span><span class="sxs-lookup"><span data-stu-id="f0ecb-133">src</span></span>**
    + <span data-ttu-id="f0ecb-134">Die URI des Elements.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-134">The URI of the asset.</span></span> <span data-ttu-id="f0ecb-135">Dies kann sowohl HTTP/HTTPS web URI, eine msappx URI oder ein Pfad zu einer lokalen Datei sein.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-135">This can be either HTTP/HTTPS web URI, an msappx URI, or a path to a local file.</span></span>
+ **<span data-ttu-id="f0ecb-136">spritesheet-src</span><span class="sxs-lookup"><span data-stu-id="f0ecb-136">spritesheet-src</span></span>**
    + <span data-ttu-id="f0ecb-137">Die URI des Elements.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-137">The URI of the asset.</span></span> <span data-ttu-id="f0ecb-138">Dies kann sowohl HTTP/HTTPS web URI, eine msappx URI oder ein Pfad zu einer lokalen Datei sein.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-138">This can be either HTTP/HTTPS web URI, an msappx URI, or a path to a local file.</span></span> <span data-ttu-id="f0ecb-139">Ist nur für Spritesheet-Animationen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-139">Only required for spritesheet animations.</span></span>
+ **<span data-ttu-id="f0ecb-140">spritesheet-height</span><span class="sxs-lookup"><span data-stu-id="f0ecb-140">spritesheet-height</span></span>**
    + <span data-ttu-id="f0ecb-141">Die Framehöhe (in Pixeln).</span><span class="sxs-lookup"><span data-stu-id="f0ecb-141">The frame height (in pixels).</span></span> <span data-ttu-id="f0ecb-142">Ist nur für Spritesheet-Animationen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-142">Only required for spritesheet animations.</span></span>
+ **<span data-ttu-id="f0ecb-143">spritesheet-fps</span><span class="sxs-lookup"><span data-stu-id="f0ecb-143">spritesheet-fps</span></span>**
    + <span data-ttu-id="f0ecb-144">Frames pro Sekunde (FPS).</span><span class="sxs-lookup"><span data-stu-id="f0ecb-144">Frames per second (FPS).</span></span> <span data-ttu-id="f0ecb-145">Ist nur für Spritesheet-Animationen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-145">Only required for spritesheet animations.</span></span> <span data-ttu-id="f0ecb-146">Es werden nur Werte von 1‑120 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-146">Only values 1-120 are supported.</span></span>
+ **<span data-ttu-id="f0ecb-147">spritesheet-startingFrame</span><span class="sxs-lookup"><span data-stu-id="f0ecb-147">spritesheet-startingFrame</span></span>**
    + <span data-ttu-id="f0ecb-148">Die Framenummer, um die Animation zu starten.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-148">The frame number to begin the animation.</span></span> <span data-ttu-id="f0ecb-149">Wird nur für Spritesheet-Animationen verwendet und hat den Standardwert 0, wenn keine Angabe erfolgt.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-149">Only used for spritesheet animations and defaults to 0 if not provided.</span></span>
+ **<span data-ttu-id="f0ecb-150">alt</span><span class="sxs-lookup"><span data-stu-id="f0ecb-150">alt</span></span>**
    + <span data-ttu-id="f0ecb-151">Text-Zeichenfolge, die als Bildschirmsprachausgabe verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-151">Text string used for screen reader narration.</span></span>

> [!NOTE]
> <span data-ttu-id="f0ecb-152">Bei einer animierten Benachrichtigung sollten Sie dennoch ein statisches Bild im Parameter „src” angeben.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-152">When making an animated notification, you should still specify a static image in the "src" parameter.</span></span> <span data-ttu-id="f0ecb-153">Es wird als Fallback verwendet, wenn die Animation nicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-153">It will be used as a fall-back if the animation fails to display.</span></span>

<span data-ttu-id="f0ecb-154">Darüber hinaus muss der Knoten der obersten Ebene Popups **hint-people**-Parameter enthalten, um den Absender-Kontakt anzugeben.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-154">In addition, the top-level toast node must include the **hint-people** parameter to specify the sending contact.</span></span> <span data-ttu-id="f0ecb-155">Dieser Parameter kann folgende Werte haben:</span><span class="sxs-lookup"><span data-stu-id="f0ecb-155">This parameter can have any the following values:</span></span>

+ **<span data-ttu-id="f0ecb-156">E-Mail-Adresse</span><span class="sxs-lookup"><span data-stu-id="f0ecb-156">Email address</span></span>** 
    + <span data-ttu-id="f0ecb-157">z.B.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-157">E.g.</span></span> <span data-ttu-id="f0ecb-158">mailto:johndoe@mydomain.com</span><span class="sxs-lookup"><span data-stu-id="f0ecb-158">mailto:johndoe@mydomain.com</span></span>
+ **<span data-ttu-id="f0ecb-159">Telefonnummer</span><span class="sxs-lookup"><span data-stu-id="f0ecb-159">Telephone number</span></span>** 
    + <span data-ttu-id="f0ecb-160">z.B.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-160">E.g.</span></span> <span data-ttu-id="f0ecb-161">Tel:888-888-8888</span><span class="sxs-lookup"><span data-stu-id="f0ecb-161">tel:888-888-8888</span></span>
+ **<span data-ttu-id="f0ecb-162">Remote-ID</span><span class="sxs-lookup"><span data-stu-id="f0ecb-162">Remote ID</span></span>** 
    + <span data-ttu-id="f0ecb-163">z.B.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-163">E.g.</span></span> <span data-ttu-id="f0ecb-164">remoteid:1234</span><span class="sxs-lookup"><span data-stu-id="f0ecb-164">remoteid:1234</span></span>

> [!NOTE]
> <span data-ttu-id="f0ecb-165">Falls Ihre App die [ContactStore APIs](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.contacts.contactstore) verwendet und auf dem Smartphone gespeicherte Kontakte mithilfe der [StoredContact.RemoteId](https://docs.microsoft.com/en-us/uwp/api/Windows.Phone.PersonalInformation.StoredContact.RemoteId)-Eigenschaft mit remote gespeicherten Kontakten verknüpft, muss der Wert für die RemoteId-Eigenschaft unbedingt stabil und eindeutig sein.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-165">If your app uses the [ContactStore APIs](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.contacts.contactstore) and uses the [StoredContact.RemoteId](https://docs.microsoft.com/en-us/uwp/api/Windows.Phone.PersonalInformation.StoredContact.RemoteId) property to link contacts stored on the PC with contacts stored remotely, it is essential that the value for the RemoteId property is both stable and unique.</span></span> <span data-ttu-id="f0ecb-166">Die Remote-ID muss also durchweg ein einzelnes Benutzerkonto identifizieren und ein eindeutiges Tag enthalten, um zu verhindern, dass sich Konflikte mit den Remote-IDs anderer Kontakte auf dem PC ergeben. Hierzu zählen auch Kontakte von anderen Apps.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-166">This means that the remote ID must consistently identify a single user account, and should contain a unique tag to guarantee that it does not conflict with the remote IDs of other contacts on the PC, including contacts that are owned by other apps.</span></span>
> <span data-ttu-id="f0ecb-167">Falls die Stabilität und Eindeutigkeit der von Ihrer App verwendeten Remote-IDs nicht gewährleistet ist, können Sie allen Ihren [RemoteIdHelper](https://msdn.microsoft.com/en-us/library/windows/apps/jj207024(v=vs.105).aspx#BKMK_UsingtheRemoteIdHelperclass) mithilfe der später in diesem Thema beschriebenen -Klasse ein eindeutiges Tag hinzufügen, bevor Sie die Remote-IDs dem System hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-167">If the remote IDs used by your app are not guaranteed to be stable and unique, you can use the [RemoteIdHelper class](https://msdn.microsoft.com/en-us/library/windows/apps/jj207024(v=vs.105).aspx#BKMK_UsingtheRemoteIdHelperclass) in order to add a unique tag to all of your remote IDs before you add them to the system.</span></span> <span data-ttu-id="f0ecb-168">Alternativ können Sie auch ganz auf die Verwendung der RemoteId-Eigenschaft verzichten und stattdessen eine benutzerdefinierte erweiterte Eigenschaft erstellen, um die Remote-IDs für Ihre Kontakte zu speichern.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-168">Alternatively, you can choose to not use the RemoteId property at all, and instead create a custom extended property in which to store remote IDs for your contacts.</span></span>

<span data-ttu-id="f0ecb-169">Neben der zweiten Bindung und der Nutzlast müssen Sie eine weitere Nutzlast in die erste Bindung für das Fallback-Popup aufnehmen.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-169">In addition to the second binding and payload, you must include another payload in the first binding for the fallback toast.</span></span> <span data-ttu-id="f0ecb-170">Die Benachrichtigung verwendet diese, wenn sie gezwungen ist, zu einem regulären Popup zurückzukehren (wird am [Ende dieses Artikels](https://review.docs.microsoft.com/en-us/windows/uwp/contacts-and-calendar/my-people-notifications#falling-back-to-toast) näher erläutert).</span><span class="sxs-lookup"><span data-stu-id="f0ecb-170">The notification will use this if it is forced to revert to a regular toast (explained further at the [end of this article](https://review.docs.microsoft.com/en-us/windows/uwp/contacts-and-calendar/my-people-notifications#falling-back-to-toast)).</span></span>

## <a name="creating-the-notification"></a><span data-ttu-id="f0ecb-171">Erstellen der Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="f0ecb-171">Creating the notification</span></span>
<span data-ttu-id="f0ecb-172">Sie können eine Benachrichtigungsvorlage für Meine Kontakte genau so erstellen wie eine [Popupbenachrichtigung](../design/shell/tiles-and-notifications/adaptive-interactive-toasts.md).</span><span class="sxs-lookup"><span data-stu-id="f0ecb-172">You can create a My People notification template just like you would a [toast notification](../design/shell/tiles-and-notifications/adaptive-interactive-toasts.md).</span></span>

<span data-ttu-id="f0ecb-173">Hier ist ein Beispiel für das Erstellen einer Benachrichtigung für „Meine Kontakte” mithilfe eines statischen Bilds:</span><span class="sxs-lookup"><span data-stu-id="f0ecb-173">Here's an example of how to create a My People notification with a static image payload:</span></span>

```xml
<toast hint-people="mailto:johndoe@mydomain.com">
    <visual lang="en-US">
        <binding template="ToastGeneric">
            <text hint-style="body">Toast fallback</text>
            <text>Add your fallback toast content here</text>
        </binding>
        <binding template="ToastGeneric" experienceType="shoulderTap">
            <image src="https://docs.microsoft.com/en-us/windows/uwp/contacts-and-calendar/images/shoulder-tap-static-payload.png"/>
        </binding>
    </visual>
</toast>
```

<span data-ttu-id="f0ecb-174">Wenn Sie die Benachrichtigung starten, sollte sie wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="f0ecb-174">When you start the notification, it should look like this:</span></span>

![Benachrichtigung als statisches Bild](images/static-image-notification-small.gif)

<span data-ttu-id="f0ecb-176">Hier ist ein Beispiel, wie man eine „Meine Kontakte”-Benachrichtigung mit einer statischen Bild-Nutzlast erstellt:</span><span class="sxs-lookup"><span data-stu-id="f0ecb-176">Here's an example of how to create a notification with an animated spritesheet payload.</span></span> <span data-ttu-id="f0ecb-177">Dieses Spritesheet hat eine Framehöhe von 80 Pixel, die mit 25 Frames pro Sekunde animiert werden.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-177">This spritesheet has a frame-height of 80 pixels, which we'll animate at 25 frames per second.</span></span> <span data-ttu-id="f0ecb-178">Wir legen Sie den ersten Frame auf 15 fest und geben ihm ein statisches Fallback-Bild mit dem Parameter "Src".</span><span class="sxs-lookup"><span data-stu-id="f0ecb-178">We set the starting frame to 15 and provide it with a static fallback image in the “src” parameter.</span></span> <span data-ttu-id="f0ecb-179">Das Fallback-Bild wird verwendet, wenn die Spritesheet-Animation nicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-179">The fallback image is used if the spritesheet animation fails to display.</span></span>

```xml
<toast hint-people="mailto:johndoe@mydomain.com">
    <visual lang="en-US">
        <binding template="ToastGeneric">
            <text hint-style="body">Toast fallback</text>
            <text>Add your fallback toast content here</text>
        </binding>
        <binding template="ToastGeneric" experienceType="shoulderTap">
            <image src="https://docs.microsoft.com/en-us/windows/uwp/contacts-and-calendar/images/shoulder-tap-pizza-static.png"
                spritesheet-src="https://docs.microsoft.com/en-us/windows/uwp/contacts-and-calendar/images/shoulder-tap-pizza-spritesheet.png"
                spritesheet-height='80' spritesheet-fps='25' spritesheet-startingFrame='15'/>
        </binding>
    </visual>
</toast>
```

<span data-ttu-id="f0ecb-180">Wenn Sie die Benachrichtigung starten, sollte sie wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="f0ecb-180">When you start the notification, it should look like this:</span></span>

![Benachrichtigung als Spritesheet](images/pizza-notification-small.gif)

## <a name="starting-the-notification"></a><span data-ttu-id="f0ecb-182">Starten der Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="f0ecb-182">Starting the notification</span></span>
<span data-ttu-id="f0ecb-183">Um eine Benachrichtigung für „Meine Kontakte” zu starten, müssen wir die Popup-Vorlage in ein [XmlDocument](https://msdn.microsoft.com/en-us/library/windows/apps/windows.data.xml.dom.xmldocument.aspx)-Objekt konvertieren.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-183">To start a My People notification, we need to convert the toast template into an [XmlDocument](https://msdn.microsoft.com/en-us/library/windows/apps/windows.data.xml.dom.xmldocument.aspx) object.</span></span> <span data-ttu-id="f0ecb-184">Falls Sie das Popup in einer XML-Datei (hier „content.xml“ genannt) definiert haben, verwenden Sie diesen Code zum Starten verwenden:</span><span class="sxs-lookup"><span data-stu-id="f0ecb-184">When you have defined the toast in an XML file (here named "content.xml"), you can use this code to start it:</span></span>

```CSharp
string xmlText = File.ReadAllText("content.xml");
XmlDocument xmlContent = new XmlDocument();
xmlContent.LoadXml(xmlText);
```

<span data-ttu-id="f0ecb-185">Sie können diesen Code anschließend verwenden, um das Popupfenster zu erstellen und zu senden.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-185">You can then use this code to create and send the toast:</span></span>

```CSharp
ToastNotification notification = new ToastNotification(xmlContent);
ToastNotificationManager.CreateToastNotifier().Show(notification);
```

## <a name="falling-back-to-toast"></a><span data-ttu-id="f0ecb-186">Zurückgreifen auf Popupbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="f0ecb-186">Falling back to toast</span></span>
<span data-ttu-id="f0ecb-187">Es gibt einige Fälle, wo eine Benachrichtigung über „Meine Kontakte” stattdessen als reguläre Popupbenachrichtigung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-187">There are some cases when a My People notification will instead display as a regular toast notification.</span></span> <span data-ttu-id="f0ecb-188">Eine Benachrichtigung für „Meine Kontakte” greift unter folgenden Umständen auf eine Popupbenachrichtigung zurück:</span><span class="sxs-lookup"><span data-stu-id="f0ecb-188">A My People notification will fall back to toast under the following conditions:</span></span>

+ <span data-ttu-id="f0ecb-189">Die Benachrichtigung wird nicht angezeigt</span><span class="sxs-lookup"><span data-stu-id="f0ecb-189">The notification fails to display</span></span>
+ <span data-ttu-id="f0ecb-190">Benachrichtigungen für „Meine Kontakte” sind nicht vom Empfänger aktiviert</span><span class="sxs-lookup"><span data-stu-id="f0ecb-190">My People notifications are not enabled by the recipient</span></span>
+ <span data-ttu-id="f0ecb-191">Der Kontakt des Absenders ist nicht an die Taskleiste des Empfängers angeheftet</span><span class="sxs-lookup"><span data-stu-id="f0ecb-191">The sender’s contact is not pinned to the receiver’s taskbar</span></span>

<span data-ttu-id="f0ecb-192">Wenn eine Benachrichtigung für „Meine Kontakte” erneut auf eine Popupbenachrichtigung zurückfällt, wird die zweite spezifische Bindung für „Meine Kontakte” ignoriert, und nur die erste Bindung wird verwendet, um das Popup anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-192">If a My People notification falls back to toast, the second My-People-specific binding is ignored, and only the first binding is used to display the toast.</span></span> <span data-ttu-id="f0ecb-193">Deshalb ist es wichtig, eine Fallback-Nutzlast in der ersten Popupbindung bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="f0ecb-193">This is why it is critical to provide a fallback payload in the first toast binding.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0ecb-194">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="f0ecb-194">See also</span></span>
+ [<span data-ttu-id="f0ecb-195">Beispiel zu „Meine Kontakte”-Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="f0ecb-195">My People Notifications Sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/MyPeopleNotifications)
+ [<span data-ttu-id="f0ecb-196">Hinzufügen von Support für „Meine Kontakte”</span><span class="sxs-lookup"><span data-stu-id="f0ecb-196">Adding My People support</span></span>](my-people-support.md)
+ [<span data-ttu-id="f0ecb-197">Adaptive Popupbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="f0ecb-197">Adaptive toast notifications</span></span>](../design/shell/tiles-and-notifications/adaptive-interactive-toasts.md)
+ [<span data-ttu-id="f0ecb-198">ToastNotification-Klasse</span><span class="sxs-lookup"><span data-stu-id="f0ecb-198">ToastNotification Class</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.ui.notifications.toastnotification)