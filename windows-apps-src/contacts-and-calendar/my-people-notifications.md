---
title: "Meine Kontakte – Benachrichtigungen"
description: "Erläutert das Erstellen und Verwenden von Benachrichtigungen für Meine Kontakte, eine neue Art Popups."
author: mukin
ms.author: mukin
ms.date: 06/28/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: b1fbba8b8cea3edd51dc9b60cae1ea3853f39dd1
ms.sourcegitcommit: ec18e10f750f3f59fbca2f6a41bf1892072c3692
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2017
---
# <a name="my-people-notifications"></a><span data-ttu-id="8b9ee-104">Meine Kontakte – Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="8b9ee-104">My People notifications</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8b9ee-105">**VORABVERSION | Erfordert das Fall Creators Update**: Sie müssen als Ziel [Insider SDK 16225](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewSDK) angeben und [Insider-Builds 16226](https://blogs.windows.com/windowsexperience/2017/06/21/announcing-windows-10-insider-preview-build-16226-pc/) oder höher ausführen, um die API „Meine Kontakte” zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-105">**PRERELEASE | Requires Fall Creators Update**: You must target [Insider SDK 16225](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewSDK) and be running [Insider build 16226](https://blogs.windows.com/windowsexperience/2017/06/21/announcing-windows-10-insider-preview-build-16226-pc/) or higher to use the My People APIs.</span></span>

<span data-ttu-id="8b9ee-106">Benachrichtigungen für „Meine Kontakte” sind eine neue Art von Geste, bei denen der Benutzer im Vordergrund steht.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-106">My People notifications are a new kind of gesture that put people first.</span></span> <span data-ttu-id="8b9ee-107">Dies ist eine neue Methode für Benutzer, um Kontakte mit wichtigen Personen dank schneller, leichter deutlicher Gesten herzustellen.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-107">They provide a new way for users to connect with the people they care about through quick, lightweight expressive gestures.</span></span>

![Herz-Emoji-Benachrichtigung](images/heart-emoji-notification-small.gif)

## <a name="requirements"></a><span data-ttu-id="8b9ee-109">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="8b9ee-109">Requirements</span></span>

+ <span data-ttu-id="8b9ee-110">Windows10 und Microsoft Visual Studio2017</span><span class="sxs-lookup"><span data-stu-id="8b9ee-110">Windows 10 and Microsoft Visual Studio 2017.</span></span> <span data-ttu-id="8b9ee-111">Ausführliche Informationen zur Installation finden Sie unter [Visual Studio einrichten](https://docs.microsoft.com/en-us/windows/uwp/get-started/get-set-up).</span><span class="sxs-lookup"><span data-stu-id="8b9ee-111">For installation details, see [Get set up with Visual Studio](https://docs.microsoft.com/en-us/windows/uwp/get-started/get-set-up).</span></span>
+ <span data-ttu-id="8b9ee-112">Sie sollten über Grundkenntnisse in C# oder einer ähnlichen objektorientierten Programmiersprache verfügen.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-112">Basic knowledge of C# or a similar object-oriented programming language.</span></span> <span data-ttu-id="8b9ee-113">Die ersten Schritte mit C# finden Sie unter [Erstellen der App „Hello, world“ (C++)](https://docs.microsoft.com/en-us/windows/uwp/get-started/create-a-hello-world-app-xaml-universal).</span><span class="sxs-lookup"><span data-stu-id="8b9ee-113">To get started with C#, see [Create a "Hello, world" app](https://docs.microsoft.com/en-us/windows/uwp/get-started/create-a-hello-world-app-xaml-universal).</span></span>

## <a name="how-it-works"></a><span data-ttu-id="8b9ee-114">Funktionsweise</span><span class="sxs-lookup"><span data-stu-id="8b9ee-114">How it works</span></span>

<span data-ttu-id="8b9ee-115">Als Alternative zur generischen Popupbenachrichtigungen können Entwickler jetzt Benachrichtigungen über das Feature „Meine Kontakte” senden, um eine persönlichere Erfahrung für Benutzer bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-115">As an alternative to generic toast notifications, application developers can now send notifications through the My People feature, to provide a more personal experience to users.</span></span> <span data-ttu-id="8b9ee-116">Dies ist eine neue Art von Popups, die von einem auf der Taskleiste des Benutzers angehefteten Kontakt gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-116">This is a new kind of toast, sent from a contact pinned to the user's taskbar.</span></span> <span data-ttu-id="8b9ee-117">Wenn die Benachrichtigung empfangen wird, wird das Bild des Kontakts auf der Taskleiste animiert und ein Sound wird abgespielt, was signalisiert, dass eine Benachrichtigung von „Meine Kontakte” gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-117">When the notification is received, the sender’s contact picture will animate in the taskbar and a sound will play, signaling that a My People notification is starting.</span></span> <span data-ttu-id="8b9ee-118">Anschließend wird die Animation oder das in der Nutzlast angezeigte Bild für 5 Sekunden angezeigt (wenn die Nutzlast eine Animation ist, die kürzer als 5 Sekunden dauert, wird diese wiederholt, bis die 5 Sekunden vorbei sind).</span><span class="sxs-lookup"><span data-stu-id="8b9ee-118">Then the animation or image specified in the payload will be displayed for 5 seconds (if the payload is an animation that lasts less than 5 seconds, it will loop until 5 seconds have passed).</span></span>

## <a name="supported-image-types"></a><span data-ttu-id="8b9ee-119">Unterstützte Abbildtypen</span><span class="sxs-lookup"><span data-stu-id="8b9ee-119">Supported image types</span></span>

+ <span data-ttu-id="8b9ee-120">GIF</span><span class="sxs-lookup"><span data-stu-id="8b9ee-120">GIF</span></span>
+ <span data-ttu-id="8b9ee-121">Statisches Bild (JPEG, PNG)</span><span class="sxs-lookup"><span data-stu-id="8b9ee-121">Static Image (JPEG, PNG)</span></span>
+ <span data-ttu-id="8b9ee-122">Spritesheet (nur vertikal)</span><span class="sxs-lookup"><span data-stu-id="8b9ee-122">Spritesheet (vertical only)</span></span>

> [!NOTE]
> <span data-ttu-id="8b9ee-123">Ein Spritesheet ist eine Animation, die von einem statischen Bild (JPEG- oder PNG) abgeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-123">A spritesheet is an animation derived from a static image (JPEG or PNG).</span></span> <span data-ttu-id="8b9ee-124">Einzelne Frames werden vertikal angeordnet, so dass sich das erste Bild im Vordergrund befindet (Sie können eine andere Startframe in der Nutzlast der Popupbenachrichtigung angeben).</span><span class="sxs-lookup"><span data-stu-id="8b9ee-124">Individual frames are arranged vertically, such that the first frame is on top (you can specify a different starting frame in the toast payload).</span></span> <span data-ttu-id="8b9ee-125">Jedes Frame muss die gleiche Höhe haben, damit das Programm diese wiederholt, um eine animierte Sequenz zu erstellen (z.B. wie ein Flipbook mit allen Seiten, die vertikal angeordnet sind).</span><span class="sxs-lookup"><span data-stu-id="8b9ee-125">Each frame must have the same height, which the program loops through to create an animated sequence (like a flipbook with all the pages laid out vertically).</span></span> <span data-ttu-id="8b9ee-126">Die folgende Abbildung zeigt ein Beispiel für ein Spritesheet.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-126">Shown below is an example of a spritesheet.</span></span>

![Spritesheet in Regenbogenfarben](images/shoulder-tap-rainbow-spritesheet.png)

## <a name="notification-parameters"></a><span data-ttu-id="8b9ee-128">Benachrichtigungsparameter</span><span class="sxs-lookup"><span data-stu-id="8b9ee-128">Notification parameters</span></span>
<span data-ttu-id="8b9ee-129">Benachrichtigungen von „Meine Kontakte” verwenden die [Popupbenachrichtigung](../controls-and-patterns/tiles-and-notifications-adaptive-interactive-toasts.md)-Framework in Windows10 und erfordern einen zusätzlichen Bindungsknoten in der Nutzlast des Popups.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-129">My People notifications use the [toast notification](../controls-and-patterns/tiles-and-notifications-adaptive-interactive-toasts.md) framework in Windows 10 and require an additional binding node in the toast payload.</span></span> <span data-ttu-id="8b9ee-130">Dies bedeutet, dass Benachrichtigungen über „Meine Kontakte” zwei Bindungen statt einer benötigen.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-130">This means notifications through My People must have two bindings instead of one.</span></span> <span data-ttu-id="8b9ee-131">Die zweite Bindung muss folgende Parameter enthalten:</span><span class="sxs-lookup"><span data-stu-id="8b9ee-131">This second binding must include the following parameter:</span></span>

```xml
experienceType=”shoulderTap”
```

<span data-ttu-id="8b9ee-132">Dies bedeutet, dass das Popup als eine Benachrichtigungen für „Meine Kontakte” behandelt werden soll.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-132">This indicates that the toast should be treated as a My People notifications.</span></span>

<span data-ttu-id="8b9ee-133">Die Image-Knoten in der Bindung sollten die folgenden Parameter enthalten:</span><span class="sxs-lookup"><span data-stu-id="8b9ee-133">The image node inside the binding should include the following parameters:</span></span>

+ **<span data-ttu-id="8b9ee-134">src</span><span class="sxs-lookup"><span data-stu-id="8b9ee-134">src</span></span>**
    + <span data-ttu-id="8b9ee-135">Die URI des Elements.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-135">The URI of the asset.</span></span> <span data-ttu-id="8b9ee-136">Dies kann sowohl HTTP/HTTPS web URI, eine msappx URI oder ein Pfad zu einer lokalen Datei sein.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-136">This can be either HTTP/HTTPS web URI, an msappx URI, or a path to a local file.</span></span>
+ **<span data-ttu-id="8b9ee-137">spritesheet-src</span><span class="sxs-lookup"><span data-stu-id="8b9ee-137">spritesheet-src</span></span>**
    + <span data-ttu-id="8b9ee-138">Die URI des Elements.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-138">The URI of the asset.</span></span> <span data-ttu-id="8b9ee-139">Dies kann sowohl HTTP/HTTPS web URI, eine msappx URI oder ein Pfad zu einer lokalen Datei sein.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-139">This can be either HTTP/HTTPS web URI, an msappx URI, or a path to a local file.</span></span> <span data-ttu-id="8b9ee-140">Ist nur für Spritesheet-Animationen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-140">Only required for spritesheet animations.</span></span>
+ **<span data-ttu-id="8b9ee-141">spritesheet-height</span><span class="sxs-lookup"><span data-stu-id="8b9ee-141">spritesheet-height</span></span>**
    + <span data-ttu-id="8b9ee-142">Die Framehöhe (in Pixeln).</span><span class="sxs-lookup"><span data-stu-id="8b9ee-142">The frame height (in pixels).</span></span> <span data-ttu-id="8b9ee-143">Ist nur für Spritesheet-Animationen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-143">Only required for spritesheet animations.</span></span>
+ **<span data-ttu-id="8b9ee-144">spritesheet-fps</span><span class="sxs-lookup"><span data-stu-id="8b9ee-144">spritesheet-fps</span></span>**
    + <span data-ttu-id="8b9ee-145">Frames pro Sekunde.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-145">Frames per second.</span></span> <span data-ttu-id="8b9ee-146">Ist nur für Spritesheet-Animationen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-146">Only required for spritesheet animations.</span></span>
+ **<span data-ttu-id="8b9ee-147">spritesheet-startingFrame</span><span class="sxs-lookup"><span data-stu-id="8b9ee-147">spritesheet-startingFrame</span></span>**
    + <span data-ttu-id="8b9ee-148">Die Framenummer, um die Animation zu starten.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-148">The frame number to begin the animation.</span></span> <span data-ttu-id="8b9ee-149">Wird nur für Spritesheet-Animationen verwendet und hat den Standardwert 0, wenn keine Angabe erfolgt.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-149">Only used for spritesheet animations and defaults to 0 if not provided.</span></span>
+ **<span data-ttu-id="8b9ee-150">alt</span><span class="sxs-lookup"><span data-stu-id="8b9ee-150">alt</span></span>**
    + <span data-ttu-id="8b9ee-151">Text-Zeichenfolge, die als Bildschirmsprachausgabe verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-151">Text string used for screen reader narration.</span></span>

> [!NOTE]
> <span data-ttu-id="8b9ee-152">Auch wenn Sie ein Spritesheet verwenden, sollten Sie noch ein statisches Bild im Parameter "Src" als Auffanglösung angeben für den Fall, dass die Animation nicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-152">Even if you're using a spritesheet, you should still specify a static image in the "src" parameter as a fall-back in case the animation fails to display.</span></span>

<span data-ttu-id="8b9ee-153">Darüber hinaus muss der Knoten der obersten Ebene Popups **hint-people**-Parameter enthalten, um den Absender-Kontakt anzugeben.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-153">In addition, the top-level toast node must include the **hint-people** parameter to indicate the sending contact.</span></span> <span data-ttu-id="8b9ee-154">Dieser Parameter kann folgende Werte haben:</span><span class="sxs-lookup"><span data-stu-id="8b9ee-154">This parameter can have any the following values:</span></span>

+ **<span data-ttu-id="8b9ee-155">E-Mail-Adresse</span><span class="sxs-lookup"><span data-stu-id="8b9ee-155">Email address</span></span>** 
    + <span data-ttu-id="8b9ee-156">z.B.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-156">E.g.</span></span> <span data-ttu-id="8b9ee-157">mailto:johndoe@mydomain.com</span><span class="sxs-lookup"><span data-stu-id="8b9ee-157">mailto:johndoe@mydomain.com</span></span>
+ **<span data-ttu-id="8b9ee-158">Telefonnummer</span><span class="sxs-lookup"><span data-stu-id="8b9ee-158">Telephone number</span></span>** 
    + <span data-ttu-id="8b9ee-159">z.B.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-159">E.g.</span></span> <span data-ttu-id="8b9ee-160">Tel:888-888-8888</span><span class="sxs-lookup"><span data-stu-id="8b9ee-160">tel:888-888-8888</span></span>
+ **<span data-ttu-id="8b9ee-161">Remote-ID</span><span class="sxs-lookup"><span data-stu-id="8b9ee-161">Remote ID</span></span>** 
    + <span data-ttu-id="8b9ee-162">z.B.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-162">E.g.</span></span> <span data-ttu-id="8b9ee-163">remoteid:1234</span><span class="sxs-lookup"><span data-stu-id="8b9ee-163">remoteid:1234</span></span>

> [!NOTE]
> <span data-ttu-id="8b9ee-164">Falls Ihre App die [ContactStore APIs](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.contacts.contactstore) verwendet und auf dem Smartphone gespeicherte Kontakte mithilfe der [StoredContact.RemoteId](https://docs.microsoft.com/en-us/uwp/api/Windows.Phone.PersonalInformation.StoredContact#Windows_Phone_PersonalInformation_StoredContact_RemoteId)-Eigenschaft mit remote gespeicherten Kontakten verknüpft, muss der Wert für die RemoteId-Eigenschaft unbedingt stabil und eindeutig sein.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-164">If your app uses the [ContactStore APIs](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.contacts.contactstore) and uses the [StoredContact.RemoteId](https://docs.microsoft.com/en-us/uwp/api/Windows.Phone.PersonalInformation.StoredContact#Windows_Phone_PersonalInformation_StoredContact_RemoteId) property to link contacts stored on the PC with contacts stored remotely, it is essential that the value for the RemoteId property is both stable and unique.</span></span> <span data-ttu-id="8b9ee-165">Die Remote-ID muss also durchweg ein einzelnes Benutzerkonto identifizieren und ein eindeutiges Tag enthalten, um zu verhindern, dass sich Konflikte mit den Remote-IDs anderer Kontakte auf dem PC ergeben. Hierzu zählen auch Kontakte von anderen Apps.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-165">This means that the remote ID must consistently identify a single user account and should contain a unique tag to guarantee that it does not conflict with the remote IDs of other contacts on the PC, including contacts that are owned by other apps.</span></span>
> <span data-ttu-id="8b9ee-166">Falls die Stabilität und Eindeutigkeit der von Ihrer App verwendeten Remote-IDs nicht gewährleistet ist, können Sie allen Ihren RemoteIdHelper mithilfe der später in diesem Thema beschriebenen -Klasse ein eindeutiges Tag hinzufügen, bevor Sie die Remote-IDs dem System hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-166">If the remote IDs used by your app are not guaranteed to be stable and unique, you can use the RemoteIdHelper class shown later in this topic in order to add a unique tag to all of your remote IDs before you add them to the system.</span></span> <span data-ttu-id="8b9ee-167">Alternativ können Sie auch ganz auf die Verwendung der RemoteId-Eigenschaft verzichten und stattdessen eine benutzerdefinierte erweiterte Eigenschaft erstellen, um die Remote-IDs für Ihre Kontakte zu speichern.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-167">Or you can choose to not use the RemoteId property at all and instead you create a custom extended property in which to store remote IDs for your contacts.</span></span>

<span data-ttu-id="8b9ee-168">Neben der zweiten Bindung und Nutzlast müssen Sie eine andere Nutzlast in die ersten Bindung der Fallback-Popup einfügen (die die Benachrichtigung verwendet, wenn sie gezwungen ist, auf eine reguläre Popupbenachrichtigungen zurück zu wechseln).</span><span class="sxs-lookup"><span data-stu-id="8b9ee-168">In addition to the second binding and payload, you MUST include another payload in the first binding for the fallback toast (which the notification will use if it is forced to revert to a regular toast).</span></span> <span data-ttu-id="8b9ee-169">Dies wird im letzten Abschnitt ausführlicher erläutert.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-169">This is explained in more detail in the final section.</span></span>

## <a name="creating-the-notification"></a><span data-ttu-id="8b9ee-170">Erstellen der Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="8b9ee-170">Creating the notification</span></span>
<span data-ttu-id="8b9ee-171">Sie können eine Benachrichtigungsvorlage für Meine Kontakte genau so erstellen wie eine [Popupbenachrichtigung](../controls-and-patterns/tiles-and-notifications-adaptive-interactive-toasts.md).</span><span class="sxs-lookup"><span data-stu-id="8b9ee-171">You can create a My People notification template just like you would a [toast notification](../controls-and-patterns/tiles-and-notifications-adaptive-interactive-toasts.md).</span></span>

<span data-ttu-id="8b9ee-172">Hier ist ein Beispiel für das Erstellen einer Benachrichtigung für „Meine Kontakte” mithilfe eines statischen Bilds:</span><span class="sxs-lookup"><span data-stu-id="8b9ee-172">Here's an example of how to create a My People notification using a static image:</span></span>

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

<span data-ttu-id="8b9ee-173">Wenn Sie die Benachrichtigung starten, sollte sie wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="8b9ee-173">If you start the notification, it should look like this:</span></span>

![Benachrichtigung als statisches Bild](images/static-image-notification-small.gif)

<span data-ttu-id="8b9ee-175">Als Nächstes zeigen wir das Erstellen einer Benachrichtigung mithilfe eines animierten Spritesheets.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-175">Next we'll show how to create a notification using an animated spritesheet.</span></span> <span data-ttu-id="8b9ee-176">Dieses Spritesheet hat eine Framehöhe von 80 Pixel, die mit 25 Frames pro Sekunde animiert werden.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-176">This spritesheet has a frame-height of 80 pixels, which we'll animate at 25 frames per second.</span></span> <span data-ttu-id="8b9ee-177">Wir legen Sie den ersten Frame auf 15 fest und geben ihm ein statisches Fallback-Bild mit dem Parameter "Src".</span><span class="sxs-lookup"><span data-stu-id="8b9ee-177">We set the starting frame to 15 and provide it with a static fallback image in the “src” parameter.</span></span> <span data-ttu-id="8b9ee-178">Das Fallback-Bild wird verwendet, wenn die Spritesheet-Animation nicht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-178">The fallback image is used if the spritesheet animation fails to display.</span></span>

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

<span data-ttu-id="8b9ee-179">Wenn Sie die Benachrichtigung starten, sollte sie wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="8b9ee-179">If you start the notification, it should look like this:</span></span>

![Benachrichtigung als Spritesheet](images/pizza-notification-small.gif)

## <a name="starting-the-notification"></a><span data-ttu-id="8b9ee-181">Starten der Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="8b9ee-181">Starting the notification</span></span>
<span data-ttu-id="8b9ee-182">Um eine Benachrichtigung für „Meine Kontakte” zu starten, müssen wir die Popup-Vorlage in ein [XmlDocument](https://msdn.microsoft.com/en-us/library/windows/apps/windows.data.xml.dom.xmldocument.aspx)-Objekt konvertieren.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-182">To start a My People notification, we need to convert the toast template into an [XmlDocument](https://msdn.microsoft.com/en-us/library/windows/apps/windows.data.xml.dom.xmldocument.aspx) object.</span></span> <span data-ttu-id="8b9ee-183">Falls Sie das Popup in einer XML-Datei (hier „content.xml“ genannt) definiert haben, verwenden Sie diesen C#-Code zum Starten verwenden:</span><span class="sxs-lookup"><span data-stu-id="8b9ee-183">Assuming you defined the toast in an XML file (here named "content.xml"), you can use this C# code to start it:</span></span>

```CSharp
string xmlText = File.ReadAllText("content.xml");
XmlDocument xmlContent = new XmlDocument();
xmlContent.LoadXml(xmlText);
```

<span data-ttu-id="8b9ee-184">Sie können diesen Code anschließend verwenden, um das Popupfenster zu erstellen und zu senden.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-184">You can then use this code to create and send the toast:</span></span>

```CSharp
ToastNotification notification = new ToastNotification(xmlContent);
ToastNotificationManager.CreateToastNotifier().Show(notification);
```

## <a name="falling-back-to-toast"></a><span data-ttu-id="8b9ee-185">Zurückgreifen auf Popupbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="8b9ee-185">Falling back to toast</span></span>
<span data-ttu-id="8b9ee-186">Es gibt einige Fälle, wo eine Benachrichtigung, die als Benachrichtigung für „Meine Kontakte” codiert war, stattdessen als reguläre Popupbenachrichtigungen angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-186">There are some cases when a notification coded as a My People notification will instead display as a regular toast.</span></span> <span data-ttu-id="8b9ee-187">Eine Benachrichtigung für „Meine Kontakte” greift unter folgenden Umständen auf eine Popupbenachrichtigung zurück:</span><span class="sxs-lookup"><span data-stu-id="8b9ee-187">A My People notification will fall back to toast under the following conditions:</span></span>

+ <span data-ttu-id="8b9ee-188">Die Benachrichtigung wird nicht angezeigt</span><span class="sxs-lookup"><span data-stu-id="8b9ee-188">The notification fails to display</span></span>
+ <span data-ttu-id="8b9ee-189">Benachrichtigungen für „Meine Kontakte” sind nicht vom Empfänger aktiviert</span><span class="sxs-lookup"><span data-stu-id="8b9ee-189">My People notifications are not enabled by the recipient</span></span>
+ <span data-ttu-id="8b9ee-190">Der Kontakt des Absenders ist nicht an die Taskleiste des Empfängers angeheftet</span><span class="sxs-lookup"><span data-stu-id="8b9ee-190">The sender’s contact is not pinned to the receiver’s taskbar</span></span>

<span data-ttu-id="8b9ee-191">Wenn eine Benachrichtigung für „Meine Kontakte” erneut auf eine Popupbenachrichtigung zurückfällt, wird die zweite spezifische Bindung für „Meine Kontakte” ignoriert, und nur die erste Bindung wird verwendet, um das Popup anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-191">If a My People notification falls back to toast, the second My-People-specific binding is ignored, and only the first binding is used to display the toast.</span></span> <span data-ttu-id="8b9ee-192">Dies bedeutet, dass, wie bereits angesprochen, eine alternative Nutzlast in der ersten Popup-Bindung angegeben werden muss.</span><span class="sxs-lookup"><span data-stu-id="8b9ee-192">This means that, as stated before, a fallback payload must be provided in the first toast binding.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b9ee-193">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="8b9ee-193">See also</span></span>
+ [<span data-ttu-id="8b9ee-194">Hinzufügen von Support für „Meine Kontakte”</span><span class="sxs-lookup"><span data-stu-id="8b9ee-194">Adding My People support</span></span>](my-people-support.md)
+ [<span data-ttu-id="8b9ee-195">Adaptive Popupbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="8b9ee-195">Adaptive toast notifications</span></span>](../controls-and-patterns/tiles-and-notifications-adaptive-interactive-toasts.md)
+ [<span data-ttu-id="8b9ee-196">ToastNotification-Klasse</span><span class="sxs-lookup"><span data-stu-id="8b9ee-196">ToastNotification Class</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.ui.notifications.toastnotification)