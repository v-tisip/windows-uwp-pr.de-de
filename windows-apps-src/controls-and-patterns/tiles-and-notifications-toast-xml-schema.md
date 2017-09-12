---
author: lex
Description: Im folgenden Artikel werden alle Eigenschaften und Elemente in der XML-Nutzlast des Popupinhalts beschrieben.
title: XML-Schema des Popupinhalts
ms.assetid: AF49EFAC-447E-44C3-93C3-CCBEDCF07D22
label: Toast content XML schema
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.openlocfilehash: ae140ebde954726d0ecf16d731010149aea2fbe5
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="toast-content-xml-schema"></a><span data-ttu-id="74bd9-104">XML-Schema des Popupinhalts</span><span class="sxs-lookup"><span data-stu-id="74bd9-104">Toast content XML schema</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

<span data-ttu-id="74bd9-105">Im Folgenden werden alle Eigenschaften und Elemente in der XML-Nutzlast des Popupinhalts beschrieben.</span><span class="sxs-lookup"><span data-stu-id="74bd9-105">The following describes all of the properties and elements within the toast content XML payload.</span></span>

<span data-ttu-id="74bd9-106">In den folgenden XML-Schemas bedeutet das Suffix „?“, dass ein Attribut optional ist.</span><span class="sxs-lookup"><span data-stu-id="74bd9-106">In the following XML schemas, a "?" suffix means that an attribute is optional.</span></span>

## <a name="ltvisualgt-and-ltaudiogt"></a>&lt;<span data-ttu-id="74bd9-107">Visual&gt; und &lt;Audio</span><span class="sxs-lookup"><span data-stu-id="74bd9-107">visual&gt; and &lt;audio</span></span>&gt;

```
<toast launch? duration? activationType? scenario? >
  <visual lang? baseUri? addImageQuery? >
    <binding template? lang? baseUri? addImageQuery? >
      <text lang? hint-maxLines? >content</text>
      <image src placement? alt? addImageQuery? hint-crop? />
      <group>
        <subgroup hint-weight? hint-textStacking? >
          <text />
          <image />
        </subgroup>
      </group>
    </binding>
  </visual>
  <audio src? loop? silent? />
</toast>
```

**<span data-ttu-id="74bd9-108">Attribute in &lt;Popup</span><span class="sxs-lookup"><span data-stu-id="74bd9-108">Attributes in &lt;toast</span></span>&gt;**

<span data-ttu-id="74bd9-109">launch?</span><span class="sxs-lookup"><span data-stu-id="74bd9-109">launch?</span></span>

-   <span data-ttu-id="74bd9-110">launch?</span><span class="sxs-lookup"><span data-stu-id="74bd9-110">launch?</span></span> <span data-ttu-id="74bd9-111">= string</span><span class="sxs-lookup"><span data-stu-id="74bd9-111">= string</span></span>
-   <span data-ttu-id="74bd9-112">Dies ist ein optionales Attribut.</span><span class="sxs-lookup"><span data-stu-id="74bd9-112">This is an optional attribute.</span></span>
-   <span data-ttu-id="74bd9-113">Eine Zeichenfolge wird an die Anwendung übergeben, wenn sie durch das Popup aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="74bd9-113">A string that is passed to the application when it is activated by the toast.</span></span>
-   <span data-ttu-id="74bd9-114">Abhängig vom Wert für „activationType“ kann dieser Wert von der App im Vordergrund, innerhalb der Hintergrundaufgabe oder von einer anderen App empfangen werden, die per Protokollstart über die ursprüngliche App gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="74bd9-114">Depending on the value of activationType, this value can be received by the app in the foreground, inside the background task, or by another app that's protocol launched from the original app.</span></span>
-   <span data-ttu-id="74bd9-115">Das Format und der Inhalt dieser Zeichenfolge werden von der App für eigene Zwecke definiert.</span><span class="sxs-lookup"><span data-stu-id="74bd9-115">The format and contents of this string are defined by the app for its own use.</span></span>
-   <span data-ttu-id="74bd9-116">Wenn der Benutzer zum Starten der zugeordneten App auf das Popup tippt oder klickt, stellt die Startzeichenfolge der App den Kontext bereit, um dem Benutzer eine Ansicht passend zum Popupinhalt zu ermöglichen, anstatt sie in der Standardgröße starten.</span><span class="sxs-lookup"><span data-stu-id="74bd9-116">When the user taps or clicks the toast to launch its associated app, the launch string provides the context to the app that allows it to show the user a view relevant to the toast content, rather than launching in its default way.</span></span>
-   <span data-ttu-id="74bd9-117">Ist die Aktivierung erfolgt, weil der Benutzer auf eine Aktion statt auf den Popuptext geklickt hat, erhält der Entwickler die vordefinierten „Argumente“ in diesem &lt;action&gt;-Tag zurück, statt des vordefinierten „launch“ im &lt;toast&gt;-Tag.</span><span class="sxs-lookup"><span data-stu-id="74bd9-117">If the activation is happened because user clicked on an action, instead of the body of the toast, the developer retrieves back the "arguments" pre-defined in that &lt;action&gt; tag, instead of "launch" pre-defined in the &lt;toast&gt; tag.</span></span>

<span data-ttu-id="74bd9-118">duration?</span><span class="sxs-lookup"><span data-stu-id="74bd9-118">duration?</span></span>

-   <span data-ttu-id="74bd9-119">duration?</span><span class="sxs-lookup"><span data-stu-id="74bd9-119">duration?</span></span> <span data-ttu-id="74bd9-120">= "short|long"</span><span class="sxs-lookup"><span data-stu-id="74bd9-120">= "short|long"</span></span>
-   <span data-ttu-id="74bd9-121">Dies ist ein optionales Attribut.</span><span class="sxs-lookup"><span data-stu-id="74bd9-121">This is an optional attribute.</span></span> <span data-ttu-id="74bd9-122">Der Standardwert lautet „kurz“.</span><span class="sxs-lookup"><span data-stu-id="74bd9-122">Default value is "short".</span></span>
-   <span data-ttu-id="74bd9-123">Es dient nur für bestimmte Szenarien und appCompat.</span><span class="sxs-lookup"><span data-stu-id="74bd9-123">This is only here for specific scenarios and appCompat.</span></span> <span data-ttu-id="74bd9-124">Im Alarmszenario wird es nicht mehr benötigt.</span><span class="sxs-lookup"><span data-stu-id="74bd9-124">You don't need this for the alarm scenario anymore.</span></span>
-   <span data-ttu-id="74bd9-125">Die Verwendung dieser Eigenschaft wird nicht empfohlen.</span><span class="sxs-lookup"><span data-stu-id="74bd9-125">We don't recommend using this property.</span></span>

<span data-ttu-id="74bd9-126">activationType?</span><span class="sxs-lookup"><span data-stu-id="74bd9-126">activationType?</span></span>

-   <span data-ttu-id="74bd9-127">activationType?</span><span class="sxs-lookup"><span data-stu-id="74bd9-127">activationType?</span></span> <span data-ttu-id="74bd9-128">= "foreground | background | protocol | system"</span><span class="sxs-lookup"><span data-stu-id="74bd9-128">= "foreground | background | protocol | system"</span></span>
-   <span data-ttu-id="74bd9-129">Dies ist ein optionales Attribut.</span><span class="sxs-lookup"><span data-stu-id="74bd9-129">This is an optional attribute.</span></span>
-   <span data-ttu-id="74bd9-130">Der Standardwert lautet „foreground“</span><span class="sxs-lookup"><span data-stu-id="74bd9-130">The default value is "foreground".</span></span>

<span data-ttu-id="74bd9-131">scenario?</span><span class="sxs-lookup"><span data-stu-id="74bd9-131">scenario?</span></span>

-   <span data-ttu-id="74bd9-132">scenario?</span><span class="sxs-lookup"><span data-stu-id="74bd9-132">scenario?</span></span> <span data-ttu-id="74bd9-133">= "default | alarm | reminder | incomingCall"</span><span class="sxs-lookup"><span data-stu-id="74bd9-133">= "default | alarm | reminder | incomingCall"</span></span>
-   <span data-ttu-id="74bd9-134">Dies ist ein optionales Attribut, der Standardwert lautet „default“.</span><span class="sxs-lookup"><span data-stu-id="74bd9-134">This is an optional attribute, default value is "default".</span></span>
-   <span data-ttu-id="74bd9-135">Sie benötigen es nur, wenn es sich bei Ihrem Szenario um einen Alarm, eine Erinnerung oder einen eingehenden Anruf handelt.</span><span class="sxs-lookup"><span data-stu-id="74bd9-135">You do not need this unless your scenario is to pop an alarm, reminder, or incoming call.</span></span>
-   <span data-ttu-id="74bd9-136">Verwenden Sie es nicht, um die Benachrichtigung dauerhaft auf dem Bildschirm anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="74bd9-136">Do not use this just for keeping your notification persistent on screen.</span></span>

**<span data-ttu-id="74bd9-137">Attribute in &lt;visual</span><span class="sxs-lookup"><span data-stu-id="74bd9-137">Attributes in &lt;visual</span></span>&gt;**

<span data-ttu-id="74bd9-138">lang?</span><span class="sxs-lookup"><span data-stu-id="74bd9-138">lang?</span></span>

-   <span data-ttu-id="74bd9-139">In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230847) finden Sie ausführliche Informationen zu diesem optionalen Attribut.</span><span class="sxs-lookup"><span data-stu-id="74bd9-139">See [this element schema article](https://msdn.microsoft.com/library/windows/apps/br230847) for details on this optional attribute.</span></span>

<span data-ttu-id="74bd9-140">baseUri?</span><span class="sxs-lookup"><span data-stu-id="74bd9-140">baseUri?</span></span>

-   <span data-ttu-id="74bd9-141">In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230847) finden Sie ausführliche Informationen zu diesem optionalen Attribut.</span><span class="sxs-lookup"><span data-stu-id="74bd9-141">See [this element schema article](https://msdn.microsoft.com/library/windows/apps/br230847) for details on this optional attribute.</span></span>

<span data-ttu-id="74bd9-142">addImageQuery?</span><span class="sxs-lookup"><span data-stu-id="74bd9-142">addImageQuery?</span></span>

-   <span data-ttu-id="74bd9-143">In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230847) finden Sie ausführliche Informationen zu diesem optionalen Attribut.</span><span class="sxs-lookup"><span data-stu-id="74bd9-143">See [this element schema article](https://msdn.microsoft.com/library/windows/apps/br230847) for details on this optional attribute.</span></span>

**<span data-ttu-id="74bd9-144">Attribute in &lt;binding</span><span class="sxs-lookup"><span data-stu-id="74bd9-144">Attributes in &lt;binding</span></span>&gt;**

<span data-ttu-id="74bd9-145">template?</span><span class="sxs-lookup"><span data-stu-id="74bd9-145">template?</span></span>

-   <span data-ttu-id="74bd9-146">\[Important\] template?</span><span class="sxs-lookup"><span data-stu-id="74bd9-146">\[Important\] template?</span></span> <span data-ttu-id="74bd9-147">= "ToastGeneric"</span><span class="sxs-lookup"><span data-stu-id="74bd9-147">= "ToastGeneric"</span></span>
-   <span data-ttu-id="74bd9-148">Wenn Sie eines der neuen Features für adaptive und interaktive Benachrichtigungen verwenden, stellen Sie sicher, dass Sie mit der Vorlage „ToastGeneric“ statt mit der Legacyvorlage beginnen.</span><span class="sxs-lookup"><span data-stu-id="74bd9-148">If you are using any of the new adaptive and interactive notification features, please make sure you start using "ToastGeneric" template instead of the legacy template.</span></span>
-   <span data-ttu-id="74bd9-149">Möglicherweise können Sie die Legacyvorlagen mit den neuen Aktionen verwenden, aber da dies nicht der gewünschte Anwendungsfall ist, können wir keinen Erfolg garantieren.</span><span class="sxs-lookup"><span data-stu-id="74bd9-149">Using the legacy templates with the new actions might work now, but that is not the intended use case, and we cannot guarantee that will continue working.</span></span>

<span data-ttu-id="74bd9-150">lang?</span><span class="sxs-lookup"><span data-stu-id="74bd9-150">lang?</span></span>

-   <span data-ttu-id="74bd9-151">In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230847) finden Sie ausführliche Informationen zu diesem optionalen Attribut.</span><span class="sxs-lookup"><span data-stu-id="74bd9-151">See [this element schema article](https://msdn.microsoft.com/library/windows/apps/br230847) for details on this optional attribute.</span></span>

<span data-ttu-id="74bd9-152">baseUri?</span><span class="sxs-lookup"><span data-stu-id="74bd9-152">baseUri?</span></span>

-   <span data-ttu-id="74bd9-153">In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230847) finden Sie ausführliche Informationen zu diesem optionalen Attribut.</span><span class="sxs-lookup"><span data-stu-id="74bd9-153">See [this element schema article](https://msdn.microsoft.com/library/windows/apps/br230847) for details on this optional attribute.</span></span>

<span data-ttu-id="74bd9-154">addImageQuery?</span><span class="sxs-lookup"><span data-stu-id="74bd9-154">addImageQuery?</span></span>

-   <span data-ttu-id="74bd9-155">In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230847) finden Sie ausführliche Informationen zu diesem optionalen Attribut.</span><span class="sxs-lookup"><span data-stu-id="74bd9-155">See [this element schema article](https://msdn.microsoft.com/library/windows/apps/br230847) for details on this optional attribute.</span></span>

**<span data-ttu-id="74bd9-156">Attribute in &lt;text</span><span class="sxs-lookup"><span data-stu-id="74bd9-156">Attributes in &lt;text</span></span>&gt;**

<span data-ttu-id="74bd9-157">lang?</span><span class="sxs-lookup"><span data-stu-id="74bd9-157">lang?</span></span>

-   <span data-ttu-id="74bd9-158">In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230847) finden Sie ausführliche Informationen zu diesem optionalen Attribut.</span><span class="sxs-lookup"><span data-stu-id="74bd9-158">See [this element schema article](https://msdn.microsoft.com/library/windows/apps/br230847) for details on this optional attribute.</span></span>

**<span data-ttu-id="74bd9-159">Attribute in &lt;image</span><span class="sxs-lookup"><span data-stu-id="74bd9-159">Attributes in &lt;image</span></span>&gt;**

<span data-ttu-id="74bd9-160">src</span><span class="sxs-lookup"><span data-stu-id="74bd9-160">src</span></span>

-   <span data-ttu-id="74bd9-161">In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230844) finden Sie ausführliche Informationen zu diesem erforderlichen Attribut.</span><span class="sxs-lookup"><span data-stu-id="74bd9-161">See [this element schema article](https://msdn.microsoft.com/library/windows/apps/br230844) for details on this required attribute.</span></span>

<span data-ttu-id="74bd9-162">placement?</span><span class="sxs-lookup"><span data-stu-id="74bd9-162">placement?</span></span>

-   <span data-ttu-id="74bd9-163">placement?</span><span class="sxs-lookup"><span data-stu-id="74bd9-163">placement?</span></span> <span data-ttu-id="74bd9-164">= "inline" | "appLogoOverride"</span><span class="sxs-lookup"><span data-stu-id="74bd9-164">= "inline" | "appLogoOverride"</span></span>
-   <span data-ttu-id="74bd9-165">Dieses Attribut ist optional.</span><span class="sxs-lookup"><span data-stu-id="74bd9-165">This attribute is optional.</span></span>
-   <span data-ttu-id="74bd9-166">Es bestimmt, wo dieses Bild angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="74bd9-166">This specifies where this image will be displayed.</span></span>
-   <span data-ttu-id="74bd9-167">„inline“ bedeutet innerhalb des Popuptextes, unter dem Text; „appLogoOverride“ steht für das Ersetzen des Anwendungssymbols (das in der oberen linken Ecke des Popups angezeigt wird).</span><span class="sxs-lookup"><span data-stu-id="74bd9-167">"inline" means inside the toast body, below the text; "appLogoOverride" means replace the application icon (that shows up on the top left corner of the toast).</span></span>
-   <span data-ttu-id="74bd9-168">Für jeden Platzierungswert ist maximal ein Bild möglich.</span><span class="sxs-lookup"><span data-stu-id="74bd9-168">You can have up to one image for each placement value.</span></span>

<span data-ttu-id="74bd9-169">alt?</span><span class="sxs-lookup"><span data-stu-id="74bd9-169">alt?</span></span>

-   <span data-ttu-id="74bd9-170">In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230844) finden Sie ausführliche Informationen zu diesem optionalen Attribut.</span><span class="sxs-lookup"><span data-stu-id="74bd9-170">See [this element schema article](https://msdn.microsoft.com/library/windows/apps/br230844) for details on this optional attribute.</span></span>

<span data-ttu-id="74bd9-171">addImageQuery?</span><span class="sxs-lookup"><span data-stu-id="74bd9-171">addImageQuery?</span></span>

-   <span data-ttu-id="74bd9-172">In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230844) finden Sie ausführliche Informationen zu diesem optionalen Attribut.</span><span class="sxs-lookup"><span data-stu-id="74bd9-172">See [this element schema article](https://msdn.microsoft.com/library/windows/apps/br230844) for details on this optional attribute.</span></span>

<span data-ttu-id="74bd9-173">hint-crop?</span><span class="sxs-lookup"><span data-stu-id="74bd9-173">hint-crop?</span></span>

-   <span data-ttu-id="74bd9-174">hint-crop?</span><span class="sxs-lookup"><span data-stu-id="74bd9-174">hint-crop?</span></span> <span data-ttu-id="74bd9-175">= "none" | "circle"</span><span class="sxs-lookup"><span data-stu-id="74bd9-175">= "none" | "circle"</span></span>
-   <span data-ttu-id="74bd9-176">Dieses Attribut ist optional.</span><span class="sxs-lookup"><span data-stu-id="74bd9-176">This attribute is optional.</span></span>
-   <span data-ttu-id="74bd9-177">„none“ ist der Standardwert, sodass kein Zuschneiden möglich ist.</span><span class="sxs-lookup"><span data-stu-id="74bd9-177">"none" is the default value which means no cropping.</span></span>
-   <span data-ttu-id="74bd9-178">„circle“ schneidet das Bild in Kreisform.</span><span class="sxs-lookup"><span data-stu-id="74bd9-178">"circle" crops the image to a circular shape.</span></span> <span data-ttu-id="74bd9-179">Verwenden Sie diese Option für Profilbilder eines Kontakts, Bilder einer Person usw.</span><span class="sxs-lookup"><span data-stu-id="74bd9-179">Use this for profile images of a contact, images of a person, and so on.</span></span>

**<span data-ttu-id="74bd9-180">Attribute in &lt;audio</span><span class="sxs-lookup"><span data-stu-id="74bd9-180">Attributes in &lt;audio</span></span>&gt;**

<span data-ttu-id="74bd9-181">src?</span><span class="sxs-lookup"><span data-stu-id="74bd9-181">src?</span></span>

-   <span data-ttu-id="74bd9-182">In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230842) finden Sie ausführliche Informationen zu diesem optionalen Attribut.</span><span class="sxs-lookup"><span data-stu-id="74bd9-182">See [this element schema article](https://msdn.microsoft.com/library/windows/apps/br230842) for details on this optional attribute.</span></span>

<span data-ttu-id="74bd9-183">loop?</span><span class="sxs-lookup"><span data-stu-id="74bd9-183">loop?</span></span>

-   <span data-ttu-id="74bd9-184">In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230842) finden Sie ausführliche Informationen zu diesem optionalen Attribut.</span><span class="sxs-lookup"><span data-stu-id="74bd9-184">See [this element schema article](https://msdn.microsoft.com/library/windows/apps/br230842) for details on this optional attribute.</span></span>

<span data-ttu-id="74bd9-185">silent?</span><span class="sxs-lookup"><span data-stu-id="74bd9-185">silent?</span></span>

-   <span data-ttu-id="74bd9-186">In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230842) finden Sie ausführliche Informationen zu diesem optionalen Attribut.</span><span class="sxs-lookup"><span data-stu-id="74bd9-186">See [this element schema article](https://msdn.microsoft.com/library/windows/apps/br230842) for details on this optional attribute.</span></span>

## <a name="schemas-ltactiongt"></a><span data-ttu-id="74bd9-187">Schemas: &lt;action</span><span class="sxs-lookup"><span data-stu-id="74bd9-187">Schemas: &lt;action</span></span>&gt;


<span data-ttu-id="74bd9-188">In den folgenden XML-Schemas bedeutet das Suffix „?“, dass ein Attribut optional ist.</span><span class="sxs-lookup"><span data-stu-id="74bd9-188">In the following XML schemas, a "?" suffix means that an attribute is optional.</span></span>

```
<toast>
  <visual>
  </visual>
  <audio />
  <actions>
    <input id type title? placeHolderContent? defaultInput? >
      <selection id content />
    </input>
    <action content arguments activationType? imageUri? hint-inputId />
  </actions>
</toast>
```

**<span data-ttu-id="74bd9-189">Attribute in &lt;input</span><span class="sxs-lookup"><span data-stu-id="74bd9-189">Attributes in &lt;input</span></span>&gt;**

<span data-ttu-id="74bd9-190">id</span><span class="sxs-lookup"><span data-stu-id="74bd9-190">id</span></span>

-   <span data-ttu-id="74bd9-191">id = string</span><span class="sxs-lookup"><span data-stu-id="74bd9-191">id = string</span></span>
-   <span data-ttu-id="74bd9-192">Dieses Attribut ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="74bd9-192">This attribute is required.</span></span>
-   <span data-ttu-id="74bd9-193">Das id-Attribut ist erforderlich und wird von Entwicklern verwendet, um Eingaben des Benutzers abzurufen, sobald die App (im Vordergrund oder im Hintergrund) aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="74bd9-193">The id attribute is required and is used by developers to retrieve user inputs once the app is activated (in the foreground or background).</span></span>

<span data-ttu-id="74bd9-194">type</span><span class="sxs-lookup"><span data-stu-id="74bd9-194">type</span></span>

-   <span data-ttu-id="74bd9-195">type = "text | selection"</span><span class="sxs-lookup"><span data-stu-id="74bd9-195">type = "text | selection"</span></span>
-   <span data-ttu-id="74bd9-196">Dieses Attribut ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="74bd9-196">This attribute is required.</span></span>
-   <span data-ttu-id="74bd9-197">Damit wird eine Texteingabe oder Eingabe aus einer Liste von vordefinierten Optionen angegeben.</span><span class="sxs-lookup"><span data-stu-id="74bd9-197">It is used to specify a text input or input from a list of pre-defined selections.</span></span>
-   <span data-ttu-id="74bd9-198">Auf Mobilgeräten und Desktops wird damit angegeben, ob eine Eingabe per Textfeld oder per Listenfeld erfolgen soll.</span><span class="sxs-lookup"><span data-stu-id="74bd9-198">On mobile and desktop, this is to specify whether you want a textbox input or a listbox input.</span></span>

<span data-ttu-id="74bd9-199">title?</span><span class="sxs-lookup"><span data-stu-id="74bd9-199">title?</span></span>

-   <span data-ttu-id="74bd9-200">title?</span><span class="sxs-lookup"><span data-stu-id="74bd9-200">title?</span></span> <span data-ttu-id="74bd9-201">= string</span><span class="sxs-lookup"><span data-stu-id="74bd9-201">= string</span></span>
-   <span data-ttu-id="74bd9-202">Das Title-Attribut ist optional. Entwickler können damit einen Titel für die Eingabe festlegen, damit Shells gerendert werden können.</span><span class="sxs-lookup"><span data-stu-id="74bd9-202">The title attribute is optional and is for developers to specify a title for the input for shells to render when there is affordance.</span></span>
-   <span data-ttu-id="74bd9-203">Auf Mobilgeräten und Desktops wird dieser Titel über der Eingabe angezeigt.</span><span class="sxs-lookup"><span data-stu-id="74bd9-203">For mobile and desktop, this title will be displayed above the input.</span></span>

<span data-ttu-id="74bd9-204">placeHolderContent?</span><span class="sxs-lookup"><span data-stu-id="74bd9-204">placeHolderContent?</span></span>

-   <span data-ttu-id="74bd9-205">placeHolderContent?</span><span class="sxs-lookup"><span data-stu-id="74bd9-205">placeHolderContent?</span></span> <span data-ttu-id="74bd9-206">= string</span><span class="sxs-lookup"><span data-stu-id="74bd9-206">= string</span></span>
-   <span data-ttu-id="74bd9-207">Das Attribut „placeHolderContent“ ist optional und der ausgegraute Hinweistext für den Texteingabetyp.</span><span class="sxs-lookup"><span data-stu-id="74bd9-207">The placeHolderContent attribute is optional and is the grey-out hint text for text input type.</span></span> <span data-ttu-id="74bd9-208">Dieses Attribut wird ignoriert, wenn der Eingabetyp nicht „text“ lautet.</span><span class="sxs-lookup"><span data-stu-id="74bd9-208">This attribute is ignored when the input type is not "text".</span></span>

<span data-ttu-id="74bd9-209">defaultInput?</span><span class="sxs-lookup"><span data-stu-id="74bd9-209">defaultInput?</span></span>

-   <span data-ttu-id="74bd9-210">defaultInput?</span><span class="sxs-lookup"><span data-stu-id="74bd9-210">defaultInput?</span></span> <span data-ttu-id="74bd9-211">= string</span><span class="sxs-lookup"><span data-stu-id="74bd9-211">= string</span></span>
-   <span data-ttu-id="74bd9-212">Das Attribut „defaultInput“ ist optional und wird verwendet, um einen Standardeingabewert bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="74bd9-212">The defaultInput attribute is optional and is used to provide a default input value.</span></span>
-   <span data-ttu-id="74bd9-213">Beim Eingabetyp „text“ wird dieser als Zeichenfolgeneingabe behandelt.</span><span class="sxs-lookup"><span data-stu-id="74bd9-213">If the input type is "text", this will be treated as a string input.</span></span>
-   <span data-ttu-id="74bd9-214">Lautet der Eingabetyp „selection“, wird angenommen, dass dieser die ID einer der verfügbaren Auswahl in diesen Eingabeelementen ist.</span><span class="sxs-lookup"><span data-stu-id="74bd9-214">If the input type is "selection", this is expected to be the id of one of the available selections inside this input's elements.</span></span>

**<span data-ttu-id="74bd9-215">Attribute in &lt;selection</span><span class="sxs-lookup"><span data-stu-id="74bd9-215">Attributes in &lt;selection</span></span>&gt;**

<span data-ttu-id="74bd9-216">id</span><span class="sxs-lookup"><span data-stu-id="74bd9-216">id</span></span>

-   <span data-ttu-id="74bd9-217">Dieses Attribut ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="74bd9-217">This attribute is required.</span></span> <span data-ttu-id="74bd9-218">Hiermit wird die Auswahl des Benutzers ermittelt.</span><span class="sxs-lookup"><span data-stu-id="74bd9-218">It's used to identify user selections.</span></span> <span data-ttu-id="74bd9-219">Die ID wird an Ihre App zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="74bd9-219">The id is returned to your app.</span></span>

<span data-ttu-id="74bd9-220">content</span><span class="sxs-lookup"><span data-stu-id="74bd9-220">content</span></span>

-   <span data-ttu-id="74bd9-221">Dieses Attribut ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="74bd9-221">This attribute is required.</span></span> <span data-ttu-id="74bd9-222">Es enthält die Zeichenfolge, die für dieses Auswahlelement angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="74bd9-222">It provides the string to display for this selection element.</span></span>

**<span data-ttu-id="74bd9-223">Attribute in &lt;action</span><span class="sxs-lookup"><span data-stu-id="74bd9-223">Attributes in &lt;action</span></span>&gt;**

<span data-ttu-id="74bd9-224">content</span><span class="sxs-lookup"><span data-stu-id="74bd9-224">content</span></span>

-   <span data-ttu-id="74bd9-225">content = string</span><span class="sxs-lookup"><span data-stu-id="74bd9-225">content = string</span></span>
-   <span data-ttu-id="74bd9-226">Das Inhaltsattribut ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="74bd9-226">The content attribute is required.</span></span> <span data-ttu-id="74bd9-227">Es enthält die Textzeichenfolge, die auf der Schaltfläche angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="74bd9-227">It provides the text string displayed on the button.</span></span>

<span data-ttu-id="74bd9-228">arguments</span><span class="sxs-lookup"><span data-stu-id="74bd9-228">arguments</span></span>

-   <span data-ttu-id="74bd9-229">arguments = string</span><span class="sxs-lookup"><span data-stu-id="74bd9-229">arguments = string</span></span>
-   <span data-ttu-id="74bd9-230">Die Argument-Attribut ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="74bd9-230">The arguments attribute it required.</span></span> <span data-ttu-id="74bd9-231">Es beschreibt die von der App definierten Daten, die die App später abrufen kann, nachdem sie vom Benutzer durch diese Aktion aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="74bd9-231">It describes the app-defined data that the app can later retrieve once it is activated from user taking this action.</span></span>

<span data-ttu-id="74bd9-232">activationType?</span><span class="sxs-lookup"><span data-stu-id="74bd9-232">activationType?</span></span>

-   <span data-ttu-id="74bd9-233">activationType?</span><span class="sxs-lookup"><span data-stu-id="74bd9-233">activationType?</span></span> <span data-ttu-id="74bd9-234">= "foreground | background | protocol | system"</span><span class="sxs-lookup"><span data-stu-id="74bd9-234">= "foreground | background | protocol | system"</span></span>
-   <span data-ttu-id="74bd9-235">Das Attribut „activationType“ ist optional und der Standardwert lautet „foreground“.</span><span class="sxs-lookup"><span data-stu-id="74bd9-235">The activationType attribute is optional and its default value is "foreground".</span></span>
-   <span data-ttu-id="74bd9-236">Es beschreibt die Art der Aktivierung, die diese Aktion auslöst: im Vordergrund, im Hintergrund, Starten einer anderen App über Protokollstart oder Aufrufen einer Systemaktion.</span><span class="sxs-lookup"><span data-stu-id="74bd9-236">It describes the kind of activation this action will cause: foreground, background, or launching another app via protocol launch, or invoking a system action.</span></span>

<span data-ttu-id="74bd9-237">imageUri?</span><span class="sxs-lookup"><span data-stu-id="74bd9-237">imageUri?</span></span>

-   <span data-ttu-id="74bd9-238">imageUri?</span><span class="sxs-lookup"><span data-stu-id="74bd9-238">imageUri?</span></span> <span data-ttu-id="74bd9-239">= string</span><span class="sxs-lookup"><span data-stu-id="74bd9-239">= string</span></span>
-   <span data-ttu-id="74bd9-240">ImageUri ist optional und wird verwendet, um ein Bildsymbol für diese Aktion bereitzustellen, welches auf der Schaltfläche im Textkontext angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="74bd9-240">imageUri is optional and is used to provide an image icon for this action to display inside the button alone with the text content.</span></span>

<span data-ttu-id="74bd9-241">hint-inputId</span><span class="sxs-lookup"><span data-stu-id="74bd9-241">hint-inputId</span></span>

-   <span data-ttu-id="74bd9-242">hint-inputId = string</span><span class="sxs-lookup"><span data-stu-id="74bd9-242">hint-inputId = string</span></span>
-   <span data-ttu-id="74bd9-243">Das hint-inpudId-Attribut ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="74bd9-243">The hint-inpudId attribute is required.</span></span> <span data-ttu-id="74bd9-244">Es wird speziell für das schnelle Beantworten einer Nachricht verwendet.</span><span class="sxs-lookup"><span data-stu-id="74bd9-244">It's specifically used for the quick reply scenario.</span></span>
-   <span data-ttu-id="74bd9-245">Der Wert muss der ID entsprechen, die dem Eingabeelement zugeordnet werden soll.</span><span class="sxs-lookup"><span data-stu-id="74bd9-245">The value needs to be the id of the input element desired to be associated with.</span></span>
-   <span data-ttu-id="74bd9-246">Auf Mobilgeräten und Desktops wird die Schaltfläche rechts neben dem Eingabefeld platziert.</span><span class="sxs-lookup"><span data-stu-id="74bd9-246">In mobile and desktop, this will put the button right next to the input box.</span></span>

## <a name="attributes-for-system-handled-actions"></a><span data-ttu-id="74bd9-247">Attribute für systemgesteuerte Aktionen</span><span class="sxs-lookup"><span data-stu-id="74bd9-247">Attributes for system-handled actions</span></span>


<span data-ttu-id="74bd9-248">Das System kann Aktionen für die Funktionen zum erneuen Erinnern und zum Schließen von Benachrichtigungen auslösen, wenn Sie nicht wünschen, dass Ihre App das erneute Erinnern/Neuplanen von Benachrichtigungen im Hintergrund ausführt.</span><span class="sxs-lookup"><span data-stu-id="74bd9-248">The system can handle actions for snoozing and dismissing notifications if you don't want your app to handle the snoozing/rescheduling of notifications as a background task.</span></span> <span data-ttu-id="74bd9-249">Systemgesteuerte Aktionen können kombiniert (oder einzeln festgelegt) werden. Wir raten jedoch davon ab, eine erneute Erinnerung ohne Möglichkeit zum Schließen zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="74bd9-249">System-handled actions can be combined (or individually specified), but we don't recommend implementing a snooze action without a dismiss action.</span></span>

<span data-ttu-id="74bd9-250">Kombinationsfeld für Systembefehle: SnoozeAndDismiss</span><span class="sxs-lookup"><span data-stu-id="74bd9-250">System commands combo: SnoozeAndDismiss</span></span>

```
<toast>
  <visual>
  </visual>
  <actions hint-systemCommands="SnoozeAndDismiss" />
</toast>
```

<span data-ttu-id="74bd9-251">Einzelne systemgesteuerte Aktionen</span><span class="sxs-lookup"><span data-stu-id="74bd9-251">Individual system-handled actions</span></span>

```
<toast>
  <visual>
  </visual>
  <actions>
  <input id="snoozeTime" type="selection" defaultInput="10">
    <selection id="5" content="5 minutes" />
    <selection id="10" content="10 minutes" />
    <selection id="20" content="20 minutes" />
    <selection id="30" content="30 minutes" />
    <selection id="60" content="1 hour" />
  </input>
  <action activationType="system" arguments="snooze" hint-inputId="snoozeTime" content=""/>
  <action activationType="system" arguments="dismiss" content=""/>
  </actions>
</toast>
```

<span data-ttu-id="74bd9-252">Gehen Sie wie folgt vor, um individuelle Aktionen zum erneuten Erinnern und Schließen zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="74bd9-252">To construct individual snooze and dismiss actions, do the following:</span></span>

-   <span data-ttu-id="74bd9-253">Legen Sie Folgendes fest: activationType = "system"</span><span class="sxs-lookup"><span data-stu-id="74bd9-253">Specify activationType = "system"</span></span>
-   <span data-ttu-id="74bd9-254">Legen Sie Argumente fest = "snooze" | "dismiss"</span><span class="sxs-lookup"><span data-stu-id="74bd9-254">Specify arguments = "snooze" | "dismiss"</span></span>
-   <span data-ttu-id="74bd9-255">Legen Sie Inhalt fest:</span><span class="sxs-lookup"><span data-stu-id="74bd9-255">Specify content:</span></span>
    -   <span data-ttu-id="74bd9-256">Wenn Sie wünschen, dass lokalisierte Zeichenfolgen für „snooze“ und „dismiss“ in den Aktionen angezeigt werden, legen Sie den Inhalt als leere Zeichenfolge fest: &lt;action content = ""/</span><span class="sxs-lookup"><span data-stu-id="74bd9-256">If you want localized strings of "snooze" and "dismiss" to be displayed on the actions, specify content to be an empty string: &lt;action content = ""/</span></span>&gt;
    -   <span data-ttu-id="74bd9-257">Wenn Sie eine benutzerdefinierte Zeichenfolge wünschen, geben Sie seinen Wert an: &lt;action content="Erinnere mich später" /</span><span class="sxs-lookup"><span data-stu-id="74bd9-257">If you want a customized string, just provide its value: &lt;action content="Remind me later" /</span></span>&gt;
-   <span data-ttu-id="74bd9-258">Legen Sie Eingaben fest:</span><span class="sxs-lookup"><span data-stu-id="74bd9-258">Specify input:</span></span>
    -   <span data-ttu-id="74bd9-259">Wenn Sie nicht möchten, dass der Benutzer ein Intervall für das erneute Erinnern auswählen kann, sondern das erneute Erinnern an die Benachrichtigung nur einmal in einem vom System definierten (in allen Betriebssystemen einheitlichen) Zeitintervall erfolgt, legen Sie keinen Wert für &lt;input&gt; fest.</span><span class="sxs-lookup"><span data-stu-id="74bd9-259">If you don't want the user to select a snooze interval and instead just want your notification to snooze only once for a system-defined time interval (that is consistent across the OS), then don't construct any &lt;input&gt; at all.</span></span>
    -   <span data-ttu-id="74bd9-260">Wenn Sie mögliche Intervalle für das erneute Erinnern bereitstellen möchten:</span><span class="sxs-lookup"><span data-stu-id="74bd9-260">If you want to provide snooze interval selections:</span></span>
        -   <span data-ttu-id="74bd9-261">Gegen Sie „hint-inputId“ in der Aktion für das erneute Erinnerung an.</span><span class="sxs-lookup"><span data-stu-id="74bd9-261">Specify hint-inputId in the snooze action</span></span>
        -   <span data-ttu-id="74bd9-262">Stimmen Sie die ID der Eingabe auf den Wert für „hint-inputId“ der Aktion für das erneute Erinnern ab: &lt;input id="snoozeTime"&gt;&lt;/input&gt;&lt;action hint-inputId="snoozeTime"/</span><span class="sxs-lookup"><span data-stu-id="74bd9-262">Match the id of the input with the hint-inputId of the snooze action: &lt;input id="snoozeTime"&gt;&lt;/input&gt;&lt;action hint-inputId="snoozeTime"/</span></span>&gt;
        -   <span data-ttu-id="74bd9-263">Legen Sie für die Auswahl-ID eine positive ganze Zahl (nonNegativeInteger) fest, die dem Intervall für das erneute Erinnern in Minuten entspricht: &lt;selection id="240" /&gt; bedeutet, dass die erneute Erinnerung in vier Stunden erfolgt.</span><span class="sxs-lookup"><span data-stu-id="74bd9-263">Specify selection id to be a nonNegativeInteger which represents snooze interval in minutes: &lt;selection id="240" /&gt; means snoozing for 4 hours</span></span>
        -   <span data-ttu-id="74bd9-264">Stellen Sie sicher, dass der Wert für „defaultInput“ in &lt;input&gt; einer der IDs der untergeordneten &lt;selection&gt; -Elemente entspricht.</span><span class="sxs-lookup"><span data-stu-id="74bd9-264">Make sure that the value of defaultInput in &lt;input&gt; matches with one of the ids of the &lt;selection&gt; children elements</span></span>
        -   <span data-ttu-id="74bd9-265">Sie können bis zu (aber nicht mehr als) 5 &lt;selection&gt;-Werte bereitstellen</span><span class="sxs-lookup"><span data-stu-id="74bd9-265">Provide up to (but no more than) 5 &lt;selection&gt; values</span></span>