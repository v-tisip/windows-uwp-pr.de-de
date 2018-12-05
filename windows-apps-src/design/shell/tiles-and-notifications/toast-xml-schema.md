---
Description: The following article describes all of the properties and elements within the toast content XML payload.
title: XML-Schema des Popupinhalts
ms.assetid: AF49EFAC-447E-44C3-93C3-CCBEDCF07D22
label: Toast content XML schema
template: detail.hbs
ms.date: 05/19/2017
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 6b9535cd8c2dd82b0c209919080df9a88bb80ccc
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8714000"
---
# <a name="toast-content-xml-schema"></a><span data-ttu-id="33830-103">XML-Schema des Popupinhalts</span><span class="sxs-lookup"><span data-stu-id="33830-103">Toast content XML schema</span></span>

 

<span data-ttu-id="33830-104">Im Folgenden werden alle Eigenschaften und Elemente in der XML-Nutzlast des Popupinhalts beschrieben.</span><span class="sxs-lookup"><span data-stu-id="33830-104">The following describes all of the properties and elements within the toast content XML payload.</span></span>

<span data-ttu-id="33830-105">In den folgenden XML-Schemas bedeutet das Suffix „?“, dass ein Attribut optional ist.</span><span class="sxs-lookup"><span data-stu-id="33830-105">In the following XML schemas, a "?" suffix means that an attribute is optional.</span></span>

## <a name="ltvisualgt-and-ltaudiogt"></a><span data-ttu-id="33830-106">&lt;Visual&gt; und &lt;Audio&gt;</span><span class="sxs-lookup"><span data-stu-id="33830-106">&lt;visual&gt; and &lt;audio&gt;</span></span>

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

**<span data-ttu-id="33830-107">Attribut in &lt;Popup&gt;</span><span class="sxs-lookup"><span data-stu-id="33830-107">Attributes in &lt;toast&gt;</span></span>**

<span data-ttu-id="33830-108">launch?</span><span class="sxs-lookup"><span data-stu-id="33830-108">launch?</span></span>

-   <span data-ttu-id="33830-109">launch?</span><span class="sxs-lookup"><span data-stu-id="33830-109">launch?</span></span> <span data-ttu-id="33830-110">= string</span><span class="sxs-lookup"><span data-stu-id="33830-110">= string</span></span>
-   <span data-ttu-id="33830-111">Dies ist ein optionales Attribut.</span><span class="sxs-lookup"><span data-stu-id="33830-111">This is an optional attribute.</span></span>
-   <span data-ttu-id="33830-112">Eine Zeichenfolge wird an die Anwendung übergeben, wenn sie durch das Popup aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="33830-112">A string that is passed to the application when it is activated by the toast.</span></span>
-   <span data-ttu-id="33830-113">Abhängig vom Wert für „activationType“ kann dieser Wert von der App im Vordergrund, innerhalb der Hintergrundaufgabe oder von einer anderen App empfangen werden, die per Protokollstart über die ursprüngliche App gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="33830-113">Depending on the value of activationType, this value can be received by the app in the foreground, inside the background task, or by another app that's protocol launched from the original app.</span></span>
-   <span data-ttu-id="33830-114">Das Format und der Inhalt dieser Zeichenfolge werden von der App für eigene Zwecke definiert.</span><span class="sxs-lookup"><span data-stu-id="33830-114">The format and contents of this string are defined by the app for its own use.</span></span>
-   <span data-ttu-id="33830-115">Wenn der Benutzer zum Starten der zugeordneten App auf das Popup tippt oder klickt, stellt die Startzeichenfolge der App den Kontext bereit, um dem Benutzer eine Ansicht passend zum Popupinhalt zu ermöglichen, anstatt sie in der Standardgröße starten.</span><span class="sxs-lookup"><span data-stu-id="33830-115">When the user taps or clicks the toast to launch its associated app, the launch string provides the context to the app that allows it to show the user a view relevant to the toast content, rather than launching in its default way.</span></span>
-   <span data-ttu-id="33830-116">Ist die Aktivierung erfolgt, weil der Benutzer auf eine Aktion statt auf den Popuptext geklickt hat, erhält der Entwickler die vordefinierten „Argumente“ in diesem &lt;action&gt;-Tag zurück, statt des vordefinierten „launch“ im &lt;toast&gt;-Tag.</span><span class="sxs-lookup"><span data-stu-id="33830-116">If the activation is happened because user clicked on an action, instead of the body of the toast, the developer retrieves back the "arguments" pre-defined in that &lt;action&gt; tag, instead of "launch" pre-defined in the &lt;toast&gt; tag.</span></span>

<span data-ttu-id="33830-117">duration?</span><span class="sxs-lookup"><span data-stu-id="33830-117">duration?</span></span>

-   <span data-ttu-id="33830-118">duration?</span><span class="sxs-lookup"><span data-stu-id="33830-118">duration?</span></span> <span data-ttu-id="33830-119">= "short|long"</span><span class="sxs-lookup"><span data-stu-id="33830-119">= "short|long"</span></span>
-   <span data-ttu-id="33830-120">Dies ist ein optionales Attribut.</span><span class="sxs-lookup"><span data-stu-id="33830-120">This is an optional attribute.</span></span> <span data-ttu-id="33830-121">Der Standardwert lautet „kurz“.</span><span class="sxs-lookup"><span data-stu-id="33830-121">Default value is "short".</span></span>
-   <span data-ttu-id="33830-122">Es dient nur für bestimmte Szenarien und appCompat.</span><span class="sxs-lookup"><span data-stu-id="33830-122">This is only here for specific scenarios and appCompat.</span></span> <span data-ttu-id="33830-123">Im Alarmszenario wird es nicht mehr benötigt.</span><span class="sxs-lookup"><span data-stu-id="33830-123">You don't need this for the alarm scenario anymore.</span></span>
-   <span data-ttu-id="33830-124">Die Verwendung dieser Eigenschaft wird nicht empfohlen.</span><span class="sxs-lookup"><span data-stu-id="33830-124">We don't recommend using this property.</span></span>

<span data-ttu-id="33830-125">activationType?</span><span class="sxs-lookup"><span data-stu-id="33830-125">activationType?</span></span>

-   <span data-ttu-id="33830-126">activationType?</span><span class="sxs-lookup"><span data-stu-id="33830-126">activationType?</span></span> <span data-ttu-id="33830-127">= "foreground | background | protocol | system"</span><span class="sxs-lookup"><span data-stu-id="33830-127">= "foreground | background | protocol | system"</span></span>
-   <span data-ttu-id="33830-128">Dies ist ein optionales Attribut.</span><span class="sxs-lookup"><span data-stu-id="33830-128">This is an optional attribute.</span></span>
-   <span data-ttu-id="33830-129">Der Standardwert lautet „foreground“</span><span class="sxs-lookup"><span data-stu-id="33830-129">The default value is "foreground".</span></span>

<span data-ttu-id="33830-130">scenario?</span><span class="sxs-lookup"><span data-stu-id="33830-130">scenario?</span></span>

-   <span data-ttu-id="33830-131">scenario?</span><span class="sxs-lookup"><span data-stu-id="33830-131">scenario?</span></span> <span data-ttu-id="33830-132">= "default | alarm | reminder | incomingCall"</span><span class="sxs-lookup"><span data-stu-id="33830-132">= "default | alarm | reminder | incomingCall"</span></span>
-   <span data-ttu-id="33830-133">Dies ist ein optionales Attribut, der Standardwert lautet „default“.</span><span class="sxs-lookup"><span data-stu-id="33830-133">This is an optional attribute, default value is "default".</span></span>
-   <span data-ttu-id="33830-134">Sie benötigen es nur, wenn es sich bei Ihrem Szenario um einen Alarm, eine Erinnerung oder einen eingehenden Anruf handelt.</span><span class="sxs-lookup"><span data-stu-id="33830-134">You do not need this unless your scenario is to pop an alarm, reminder, or incoming call.</span></span>
-   <span data-ttu-id="33830-135">Verwenden Sie es nicht, um die Benachrichtigung dauerhaft auf dem Bildschirm anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="33830-135">Do not use this just for keeping your notification persistent on screen.</span></span>

**<span data-ttu-id="33830-136">Attribut in &lt;Visual&gt;</span><span class="sxs-lookup"><span data-stu-id="33830-136">Attributes in &lt;visual&gt;</span></span>**

<span data-ttu-id="33830-137">lang?</span><span class="sxs-lookup"><span data-stu-id="33830-137">lang?</span></span>

-   <span data-ttu-id="33830-138">In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230847) finden Sie ausführliche Informationen zu diesem optionalen Attribut.</span><span class="sxs-lookup"><span data-stu-id="33830-138">See [this element schema article](https://msdn.microsoft.com/library/windows/apps/br230847) for details on this optional attribute.</span></span>

<span data-ttu-id="33830-139">baseUri?</span><span class="sxs-lookup"><span data-stu-id="33830-139">baseUri?</span></span>

-   <span data-ttu-id="33830-140">In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230847) finden Sie ausführliche Informationen zu diesem optionalen Attribut.</span><span class="sxs-lookup"><span data-stu-id="33830-140">See [this element schema article](https://msdn.microsoft.com/library/windows/apps/br230847) for details on this optional attribute.</span></span>

<span data-ttu-id="33830-141">addImageQuery?</span><span class="sxs-lookup"><span data-stu-id="33830-141">addImageQuery?</span></span>

-   <span data-ttu-id="33830-142">In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230847) finden Sie ausführliche Informationen zu diesem optionalen Attribut.</span><span class="sxs-lookup"><span data-stu-id="33830-142">See [this element schema article](https://msdn.microsoft.com/library/windows/apps/br230847) for details on this optional attribute.</span></span>

**<span data-ttu-id="33830-143">Attribut in &lt;Bindung&gt;</span><span class="sxs-lookup"><span data-stu-id="33830-143">Attributes in &lt;binding&gt;</span></span>**

<span data-ttu-id="33830-144">template?</span><span class="sxs-lookup"><span data-stu-id="33830-144">template?</span></span>

-   <span data-ttu-id="33830-145">\[Important\] template?</span><span class="sxs-lookup"><span data-stu-id="33830-145">\[Important\] template?</span></span> <span data-ttu-id="33830-146">= "ToastGeneric"</span><span class="sxs-lookup"><span data-stu-id="33830-146">= "ToastGeneric"</span></span>
-   <span data-ttu-id="33830-147">Wenn Sie eines der neuen Features für adaptive und interaktive Benachrichtigungen verwenden, stellen Sie sicher, dass Sie mit der Vorlage „ToastGeneric“ statt mit der Legacyvorlage beginnen.</span><span class="sxs-lookup"><span data-stu-id="33830-147">If you are using any of the new adaptive and interactive notification features, please make sure you start using "ToastGeneric" template instead of the legacy template.</span></span>
-   <span data-ttu-id="33830-148">Möglicherweise können Sie die Legacyvorlagen mit den neuen Aktionen verwenden, aber da dies nicht der gewünschte Anwendungsfall ist, können wir keinen Erfolg garantieren.</span><span class="sxs-lookup"><span data-stu-id="33830-148">Using the legacy templates with the new actions might work now, but that is not the intended use case, and we cannot guarantee that will continue working.</span></span>

<span data-ttu-id="33830-149">lang?</span><span class="sxs-lookup"><span data-stu-id="33830-149">lang?</span></span>

-   <span data-ttu-id="33830-150">In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230847) finden Sie ausführliche Informationen zu diesem optionalen Attribut.</span><span class="sxs-lookup"><span data-stu-id="33830-150">See [this element schema article](https://msdn.microsoft.com/library/windows/apps/br230847) for details on this optional attribute.</span></span>

<span data-ttu-id="33830-151">baseUri?</span><span class="sxs-lookup"><span data-stu-id="33830-151">baseUri?</span></span>

-   <span data-ttu-id="33830-152">In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230847) finden Sie ausführliche Informationen zu diesem optionalen Attribut.</span><span class="sxs-lookup"><span data-stu-id="33830-152">See [this element schema article](https://msdn.microsoft.com/library/windows/apps/br230847) for details on this optional attribute.</span></span>

<span data-ttu-id="33830-153">addImageQuery?</span><span class="sxs-lookup"><span data-stu-id="33830-153">addImageQuery?</span></span>

-   <span data-ttu-id="33830-154">In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230847) finden Sie ausführliche Informationen zu diesem optionalen Attribut.</span><span class="sxs-lookup"><span data-stu-id="33830-154">See [this element schema article](https://msdn.microsoft.com/library/windows/apps/br230847) for details on this optional attribute.</span></span>

**<span data-ttu-id="33830-155">Attribut in &lt;Text&gt;</span><span class="sxs-lookup"><span data-stu-id="33830-155">Attributes in &lt;text&gt;</span></span>**

<span data-ttu-id="33830-156">lang?</span><span class="sxs-lookup"><span data-stu-id="33830-156">lang?</span></span>

-   <span data-ttu-id="33830-157">In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230847) finden Sie ausführliche Informationen zu diesem optionalen Attribut.</span><span class="sxs-lookup"><span data-stu-id="33830-157">See [this element schema article](https://msdn.microsoft.com/library/windows/apps/br230847) for details on this optional attribute.</span></span>

**<span data-ttu-id="33830-158">Attribut in &lt;Bild&gt;</span><span class="sxs-lookup"><span data-stu-id="33830-158">Attributes in &lt;image&gt;</span></span>**

<span data-ttu-id="33830-159">src</span><span class="sxs-lookup"><span data-stu-id="33830-159">src</span></span>

-   <span data-ttu-id="33830-160">In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230844) finden Sie ausführliche Informationen zu diesem erforderlichen Attribut.</span><span class="sxs-lookup"><span data-stu-id="33830-160">See [this element schema article](https://msdn.microsoft.com/library/windows/apps/br230844) for details on this required attribute.</span></span>

<span data-ttu-id="33830-161">placement?</span><span class="sxs-lookup"><span data-stu-id="33830-161">placement?</span></span>

-   <span data-ttu-id="33830-162">placement?</span><span class="sxs-lookup"><span data-stu-id="33830-162">placement?</span></span> <span data-ttu-id="33830-163">= "inline" | "appLogoOverride"</span><span class="sxs-lookup"><span data-stu-id="33830-163">= "inline" | "appLogoOverride"</span></span>
-   <span data-ttu-id="33830-164">Dieses Attribut ist optional.</span><span class="sxs-lookup"><span data-stu-id="33830-164">This attribute is optional.</span></span>
-   <span data-ttu-id="33830-165">Es bestimmt, wo dieses Bild angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="33830-165">This specifies where this image will be displayed.</span></span>
-   <span data-ttu-id="33830-166">„inline“ bedeutet innerhalb des Popuptextes, unter dem Text; „appLogoOverride“ steht für das Ersetzen des Anwendungssymbols (das in der oberen linken Ecke des Popups angezeigt wird).</span><span class="sxs-lookup"><span data-stu-id="33830-166">"inline" means inside the toast body, below the text; "appLogoOverride" means replace the application icon (that shows up on the top left corner of the toast).</span></span>
-   <span data-ttu-id="33830-167">Für jeden Platzierungswert ist maximal ein Bild möglich.</span><span class="sxs-lookup"><span data-stu-id="33830-167">You can have up to one image for each placement value.</span></span>

<span data-ttu-id="33830-168">alt?</span><span class="sxs-lookup"><span data-stu-id="33830-168">alt?</span></span>

-   <span data-ttu-id="33830-169">In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230844) finden Sie ausführliche Informationen zu diesem optionalen Attribut.</span><span class="sxs-lookup"><span data-stu-id="33830-169">See [this element schema article](https://msdn.microsoft.com/library/windows/apps/br230844) for details on this optional attribute.</span></span>

<span data-ttu-id="33830-170">addImageQuery?</span><span class="sxs-lookup"><span data-stu-id="33830-170">addImageQuery?</span></span>

-   <span data-ttu-id="33830-171">In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230844) finden Sie ausführliche Informationen zu diesem optionalen Attribut.</span><span class="sxs-lookup"><span data-stu-id="33830-171">See [this element schema article](https://msdn.microsoft.com/library/windows/apps/br230844) for details on this optional attribute.</span></span>

<span data-ttu-id="33830-172">hint-crop?</span><span class="sxs-lookup"><span data-stu-id="33830-172">hint-crop?</span></span>

-   <span data-ttu-id="33830-173">hint-crop?</span><span class="sxs-lookup"><span data-stu-id="33830-173">hint-crop?</span></span> <span data-ttu-id="33830-174">= "none" | "circle"</span><span class="sxs-lookup"><span data-stu-id="33830-174">= "none" | "circle"</span></span>
-   <span data-ttu-id="33830-175">Dieses Attribut ist optional.</span><span class="sxs-lookup"><span data-stu-id="33830-175">This attribute is optional.</span></span>
-   <span data-ttu-id="33830-176">„none“ ist der Standardwert, sodass kein Zuschneiden möglich ist.</span><span class="sxs-lookup"><span data-stu-id="33830-176">"none" is the default value which means no cropping.</span></span>
-   <span data-ttu-id="33830-177">„circle“ schneidet das Bild in Kreisform.</span><span class="sxs-lookup"><span data-stu-id="33830-177">"circle" crops the image to a circular shape.</span></span> <span data-ttu-id="33830-178">Verwenden Sie diese Option für Profilbilder eines Kontakts, Bilder einer Person usw.</span><span class="sxs-lookup"><span data-stu-id="33830-178">Use this for profile images of a contact, images of a person, and so on.</span></span>

**<span data-ttu-id="33830-179">Attribut in &lt;Audio&gt;</span><span class="sxs-lookup"><span data-stu-id="33830-179">Attributes in &lt;audio&gt;</span></span>**

<span data-ttu-id="33830-180">src?</span><span class="sxs-lookup"><span data-stu-id="33830-180">src?</span></span>

-   <span data-ttu-id="33830-181">In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230842) finden Sie ausführliche Informationen zu diesem optionalen Attribut.</span><span class="sxs-lookup"><span data-stu-id="33830-181">See [this element schema article](https://msdn.microsoft.com/library/windows/apps/br230842) for details on this optional attribute.</span></span>

<span data-ttu-id="33830-182">loop?</span><span class="sxs-lookup"><span data-stu-id="33830-182">loop?</span></span>

-   <span data-ttu-id="33830-183">In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230842) finden Sie ausführliche Informationen zu diesem optionalen Attribut.</span><span class="sxs-lookup"><span data-stu-id="33830-183">See [this element schema article](https://msdn.microsoft.com/library/windows/apps/br230842) for details on this optional attribute.</span></span>

<span data-ttu-id="33830-184">silent?</span><span class="sxs-lookup"><span data-stu-id="33830-184">silent?</span></span>

-   <span data-ttu-id="33830-185">In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230842) finden Sie ausführliche Informationen zu diesem optionalen Attribut.</span><span class="sxs-lookup"><span data-stu-id="33830-185">See [this element schema article](https://msdn.microsoft.com/library/windows/apps/br230842) for details on this optional attribute.</span></span>

## <a name="schemas-ltactiongt"></a><span data-ttu-id="33830-186">Schemata: &lt;Aktion&gt;</span><span class="sxs-lookup"><span data-stu-id="33830-186">Schemas: &lt;action&gt;</span></span>


<span data-ttu-id="33830-187">In den folgenden XML-Schemas bedeutet das Suffix „?“, dass ein Attribut optional ist.</span><span class="sxs-lookup"><span data-stu-id="33830-187">In the following XML schemas, a "?" suffix means that an attribute is optional.</span></span>

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

**<span data-ttu-id="33830-188">Attribut in &lt;Eingabe&gt;</span><span class="sxs-lookup"><span data-stu-id="33830-188">Attributes in &lt;input&gt;</span></span>**

<span data-ttu-id="33830-189">id</span><span class="sxs-lookup"><span data-stu-id="33830-189">id</span></span>

-   <span data-ttu-id="33830-190">id = string</span><span class="sxs-lookup"><span data-stu-id="33830-190">id = string</span></span>
-   <span data-ttu-id="33830-191">Dieses Attribut ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="33830-191">This attribute is required.</span></span>
-   <span data-ttu-id="33830-192">Das id-Attribut ist erforderlich und wird von Entwicklern verwendet, um Eingaben des Benutzers abzurufen, sobald die App (im Vordergrund oder im Hintergrund) aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="33830-192">The id attribute is required and is used by developers to retrieve user inputs once the app is activated (in the foreground or background).</span></span>

<span data-ttu-id="33830-193">type</span><span class="sxs-lookup"><span data-stu-id="33830-193">type</span></span>

-   <span data-ttu-id="33830-194">type = "text | selection"</span><span class="sxs-lookup"><span data-stu-id="33830-194">type = "text | selection"</span></span>
-   <span data-ttu-id="33830-195">Dieses Attribut ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="33830-195">This attribute is required.</span></span>
-   <span data-ttu-id="33830-196">Damit wird eine Texteingabe oder Eingabe aus einer Liste von vordefinierten Optionen angegeben.</span><span class="sxs-lookup"><span data-stu-id="33830-196">It is used to specify a text input or input from a list of pre-defined selections.</span></span>
-   <span data-ttu-id="33830-197">Auf Mobilgeräten und Desktops wird damit angegeben, ob eine Eingabe per Textfeld oder per Listenfeld erfolgen soll.</span><span class="sxs-lookup"><span data-stu-id="33830-197">On mobile and desktop, this is to specify whether you want a textbox input or a listbox input.</span></span>

<span data-ttu-id="33830-198">title?</span><span class="sxs-lookup"><span data-stu-id="33830-198">title?</span></span>

-   <span data-ttu-id="33830-199">title?</span><span class="sxs-lookup"><span data-stu-id="33830-199">title?</span></span> <span data-ttu-id="33830-200">= string</span><span class="sxs-lookup"><span data-stu-id="33830-200">= string</span></span>
-   <span data-ttu-id="33830-201">Das Title-Attribut ist optional. Entwickler können damit einen Titel für die Eingabe festlegen, damit Shells gerendert werden können.</span><span class="sxs-lookup"><span data-stu-id="33830-201">The title attribute is optional and is for developers to specify a title for the input for shells to render when there is affordance.</span></span>
-   <span data-ttu-id="33830-202">Auf Mobilgeräten und Desktops wird dieser Titel über der Eingabe angezeigt.</span><span class="sxs-lookup"><span data-stu-id="33830-202">For mobile and desktop, this title will be displayed above the input.</span></span>

<span data-ttu-id="33830-203">placeHolderContent?</span><span class="sxs-lookup"><span data-stu-id="33830-203">placeHolderContent?</span></span>

-   <span data-ttu-id="33830-204">placeHolderContent?</span><span class="sxs-lookup"><span data-stu-id="33830-204">placeHolderContent?</span></span> <span data-ttu-id="33830-205">= string</span><span class="sxs-lookup"><span data-stu-id="33830-205">= string</span></span>
-   <span data-ttu-id="33830-206">Das Attribut „placeHolderContent“ ist optional und der ausgegraute Hinweistext für den Texteingabetyp.</span><span class="sxs-lookup"><span data-stu-id="33830-206">The placeHolderContent attribute is optional and is the grey-out hint text for text input type.</span></span> <span data-ttu-id="33830-207">Dieses Attribut wird ignoriert, wenn der Eingabetyp nicht „text“ lautet.</span><span class="sxs-lookup"><span data-stu-id="33830-207">This attribute is ignored when the input type is not "text".</span></span>

<span data-ttu-id="33830-208">defaultInput?</span><span class="sxs-lookup"><span data-stu-id="33830-208">defaultInput?</span></span>

-   <span data-ttu-id="33830-209">defaultInput?</span><span class="sxs-lookup"><span data-stu-id="33830-209">defaultInput?</span></span> <span data-ttu-id="33830-210">= string</span><span class="sxs-lookup"><span data-stu-id="33830-210">= string</span></span>
-   <span data-ttu-id="33830-211">Das Attribut „defaultInput“ ist optional und wird verwendet, um einen Standardeingabewert bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="33830-211">The defaultInput attribute is optional and is used to provide a default input value.</span></span>
-   <span data-ttu-id="33830-212">Beim Eingabetyp „text“ wird dieser als Zeichenfolgeneingabe behandelt.</span><span class="sxs-lookup"><span data-stu-id="33830-212">If the input type is "text", this will be treated as a string input.</span></span>
-   <span data-ttu-id="33830-213">Lautet der Eingabetyp „selection“, wird angenommen, dass dieser die ID einer der verfügbaren Auswahl in diesen Eingabeelementen ist.</span><span class="sxs-lookup"><span data-stu-id="33830-213">If the input type is "selection", this is expected to be the id of one of the available selections inside this input's elements.</span></span>

**<span data-ttu-id="33830-214">Attribut in &lt;Auswahl&gt;</span><span class="sxs-lookup"><span data-stu-id="33830-214">Attributes in &lt;selection&gt;</span></span>**

<span data-ttu-id="33830-215">id</span><span class="sxs-lookup"><span data-stu-id="33830-215">id</span></span>

-   <span data-ttu-id="33830-216">Dieses Attribut ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="33830-216">This attribute is required.</span></span> <span data-ttu-id="33830-217">Hiermit wird die Auswahl des Benutzers ermittelt.</span><span class="sxs-lookup"><span data-stu-id="33830-217">It's used to identify user selections.</span></span> <span data-ttu-id="33830-218">Die ID wird an Ihre App zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="33830-218">The id is returned to your app.</span></span>

<span data-ttu-id="33830-219">content</span><span class="sxs-lookup"><span data-stu-id="33830-219">content</span></span>

-   <span data-ttu-id="33830-220">Dieses Attribut ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="33830-220">This attribute is required.</span></span> <span data-ttu-id="33830-221">Es enthält die Zeichenfolge, die für dieses Auswahlelement angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="33830-221">It provides the string to display for this selection element.</span></span>

**<span data-ttu-id="33830-222">Attribut in &lt;Aktion&gt;</span><span class="sxs-lookup"><span data-stu-id="33830-222">Attributes in &lt;action&gt;</span></span>**

<span data-ttu-id="33830-223">content</span><span class="sxs-lookup"><span data-stu-id="33830-223">content</span></span>

-   <span data-ttu-id="33830-224">content = string</span><span class="sxs-lookup"><span data-stu-id="33830-224">content = string</span></span>
-   <span data-ttu-id="33830-225">Das Inhaltsattribut ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="33830-225">The content attribute is required.</span></span> <span data-ttu-id="33830-226">Es enthält die Textzeichenfolge, die auf der Schaltfläche angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="33830-226">It provides the text string displayed on the button.</span></span>

<span data-ttu-id="33830-227">arguments</span><span class="sxs-lookup"><span data-stu-id="33830-227">arguments</span></span>

-   <span data-ttu-id="33830-228">arguments = string</span><span class="sxs-lookup"><span data-stu-id="33830-228">arguments = string</span></span>
-   <span data-ttu-id="33830-229">Die Argument-Attribut ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="33830-229">The arguments attribute it required.</span></span> <span data-ttu-id="33830-230">Es beschreibt die von der App definierten Daten, die die App später abrufen kann, nachdem sie vom Benutzer durch diese Aktion aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="33830-230">It describes the app-defined data that the app can later retrieve once it is activated from user taking this action.</span></span>

<span data-ttu-id="33830-231">activationType?</span><span class="sxs-lookup"><span data-stu-id="33830-231">activationType?</span></span>

-   <span data-ttu-id="33830-232">activationType?</span><span class="sxs-lookup"><span data-stu-id="33830-232">activationType?</span></span> <span data-ttu-id="33830-233">= "foreground | background | protocol | system"</span><span class="sxs-lookup"><span data-stu-id="33830-233">= "foreground | background | protocol | system"</span></span>
-   <span data-ttu-id="33830-234">Das Attribut „activationType“ ist optional und der Standardwert lautet „foreground“.</span><span class="sxs-lookup"><span data-stu-id="33830-234">The activationType attribute is optional and its default value is "foreground".</span></span>
-   <span data-ttu-id="33830-235">Es beschreibt die Art der Aktivierung, die diese Aktion auslöst: im Vordergrund, im Hintergrund, Starten einer anderen App über Protokollstart oder Aufrufen einer Systemaktion.</span><span class="sxs-lookup"><span data-stu-id="33830-235">It describes the kind of activation this action will cause: foreground, background, or launching another app via protocol launch, or invoking a system action.</span></span>

<span data-ttu-id="33830-236">imageUri?</span><span class="sxs-lookup"><span data-stu-id="33830-236">imageUri?</span></span>

-   <span data-ttu-id="33830-237">imageUri?</span><span class="sxs-lookup"><span data-stu-id="33830-237">imageUri?</span></span> <span data-ttu-id="33830-238">= string</span><span class="sxs-lookup"><span data-stu-id="33830-238">= string</span></span>
-   <span data-ttu-id="33830-239">ImageUri ist optional und wird verwendet, um ein Bildsymbol für diese Aktion bereitzustellen, welches auf der Schaltfläche im Textkontext angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="33830-239">imageUri is optional and is used to provide an image icon for this action to display inside the button alone with the text content.</span></span>

<span data-ttu-id="33830-240">hint-inputId</span><span class="sxs-lookup"><span data-stu-id="33830-240">hint-inputId</span></span>

-   <span data-ttu-id="33830-241">hint-inputId = string</span><span class="sxs-lookup"><span data-stu-id="33830-241">hint-inputId = string</span></span>
-   <span data-ttu-id="33830-242">Das hint-inpudId-Attribut ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="33830-242">The hint-inpudId attribute is required.</span></span> <span data-ttu-id="33830-243">Es wird speziell für das schnelle Beantworten einer Nachricht verwendet.</span><span class="sxs-lookup"><span data-stu-id="33830-243">It's specifically used for the quick reply scenario.</span></span>
-   <span data-ttu-id="33830-244">Der Wert muss der ID entsprechen, die dem Eingabeelement zugeordnet werden soll.</span><span class="sxs-lookup"><span data-stu-id="33830-244">The value needs to be the id of the input element desired to be associated with.</span></span>
-   <span data-ttu-id="33830-245">Auf Mobilgeräten und Desktops wird die Schaltfläche rechts neben dem Eingabefeld platziert.</span><span class="sxs-lookup"><span data-stu-id="33830-245">In mobile and desktop, this will put the button right next to the input box.</span></span>

## <a name="attributes-for-system-handled-actions"></a><span data-ttu-id="33830-246">Attribute für systemgesteuerte Aktionen</span><span class="sxs-lookup"><span data-stu-id="33830-246">Attributes for system-handled actions</span></span>


<span data-ttu-id="33830-247">Das System kann Aktionen für die Funktionen zum erneuen Erinnern und zum Schließen von Benachrichtigungen auslösen, wenn Sie nicht wünschen, dass Ihre App das erneute Erinnern/Neuplanen von Benachrichtigungen im Hintergrund ausführt.</span><span class="sxs-lookup"><span data-stu-id="33830-247">The system can handle actions for snoozing and dismissing notifications if you don't want your app to handle the snoozing/rescheduling of notifications as a background task.</span></span> <span data-ttu-id="33830-248">Systemgesteuerte Aktionen können kombiniert (oder einzeln festgelegt) werden. Wir raten jedoch davon ab, eine erneute Erinnerung ohne Möglichkeit zum Schließen zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="33830-248">System-handled actions can be combined (or individually specified), but we don't recommend implementing a snooze action without a dismiss action.</span></span>

<span data-ttu-id="33830-249">Kombinationsfeld für Systembefehle: SnoozeAndDismiss</span><span class="sxs-lookup"><span data-stu-id="33830-249">System commands combo: SnoozeAndDismiss</span></span>

```
<toast>
  <visual>
  </visual>
  <actions hint-systemCommands="SnoozeAndDismiss" />
</toast>
```

<span data-ttu-id="33830-250">Einzelne systemgesteuerte Aktionen</span><span class="sxs-lookup"><span data-stu-id="33830-250">Individual system-handled actions</span></span>

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

<span data-ttu-id="33830-251">Gehen Sie wie folgt vor, um individuelle Aktionen zum erneuten Erinnern und Schließen zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="33830-251">To construct individual snooze and dismiss actions, do the following:</span></span>

-   <span data-ttu-id="33830-252">Legen Sie Folgendes fest: activationType = "system"</span><span class="sxs-lookup"><span data-stu-id="33830-252">Specify activationType = "system"</span></span>
-   <span data-ttu-id="33830-253">Legen Sie Argumente fest = "snooze" | "dismiss"</span><span class="sxs-lookup"><span data-stu-id="33830-253">Specify arguments = "snooze" | "dismiss"</span></span>
-   <span data-ttu-id="33830-254">Legen Sie Inhalt fest:</span><span class="sxs-lookup"><span data-stu-id="33830-254">Specify content:</span></span>
    -   <span data-ttu-id="33830-255">Wenn Sie wünschen, dass lokalisierte Zeichenfolgen für „snooze“ und „dismiss“ in den Aktionen angezeigt werden, legen Sie den Inhalt als leere Zeichenfolge fest: &lt;action content = ""/&gt;</span><span class="sxs-lookup"><span data-stu-id="33830-255">If you want localized strings of "snooze" and "dismiss" to be displayed on the actions, specify content to be an empty string: &lt;action content = ""/&gt;</span></span>
    -   <span data-ttu-id="33830-256">Wenn Sie eine benutzerdefinierte Zeichenfolge wünschen, geben Sie seinen Wert an: &lt;action content="Erinnere mich später" /&gt;</span><span class="sxs-lookup"><span data-stu-id="33830-256">If you want a customized string, just provide its value: &lt;action content="Remind me later" /&gt;</span></span>
-   <span data-ttu-id="33830-257">Legen Sie Eingaben fest:</span><span class="sxs-lookup"><span data-stu-id="33830-257">Specify input:</span></span>
    -   <span data-ttu-id="33830-258">Wenn Sie nicht möchten, dass der Benutzer ein Intervall für das erneute Erinnern auswählen kann, sondern das erneute Erinnern an die Benachrichtigung nur einmal in einem vom System definierten (in allen Betriebssystemen einheitlichen) Zeitintervall erfolgt, legen Sie keinen Wert für &lt;input&gt; fest.</span><span class="sxs-lookup"><span data-stu-id="33830-258">If you don't want the user to select a snooze interval and instead just want your notification to snooze only once for a system-defined time interval (that is consistent across the OS), then don't construct any &lt;input&gt; at all.</span></span>
    -   <span data-ttu-id="33830-259">Wenn Sie mögliche Intervalle für das erneute Erinnern bereitstellen möchten:</span><span class="sxs-lookup"><span data-stu-id="33830-259">If you want to provide snooze interval selections:</span></span>
        -   <span data-ttu-id="33830-260">Gegen Sie „hint-inputId“ in der Aktion für das erneute Erinnerung an.</span><span class="sxs-lookup"><span data-stu-id="33830-260">Specify hint-inputId in the snooze action</span></span>
        -   <span data-ttu-id="33830-261">Stimmen Sie die ID der Eingabe auf den Wert für „hint-inputId“ der Aktion für das erneute Erinnern ab: : &lt;input id="snoozeTime"&gt;&lt;/input&gt;&lt;action hint-inputId="snoozeTime"/&gt;</span><span class="sxs-lookup"><span data-stu-id="33830-261">Match the id of the input with the hint-inputId of the snooze action: &lt;input id="snoozeTime"&gt;&lt;/input&gt;&lt;action hint-inputId="snoozeTime"/&gt;</span></span>
        -   <span data-ttu-id="33830-262">Legen Sie für die Auswahl-ID eine positive ganze Zahl (nonNegativeInteger) fest, die dem Intervall für das erneute Erinnern in Minuten entspricht: &lt;selection id="240" /&gt; bedeutet, dass die erneute Erinnerung in vier Stunden erfolgt.</span><span class="sxs-lookup"><span data-stu-id="33830-262">Specify selection id to be a nonNegativeInteger which represents snooze interval in minutes: &lt;selection id="240" /&gt; means snoozing for 4 hours</span></span>
        -   <span data-ttu-id="33830-263">Stellen Sie sicher, dass der Wert für „defaultInput“ in &lt;input&gt; einer der IDs der untergeordneten &lt;selection&gt; -Elemente entspricht.</span><span class="sxs-lookup"><span data-stu-id="33830-263">Make sure that the value of defaultInput in &lt;input&gt; matches with one of the ids of the &lt;selection&gt; children elements</span></span>
        -   <span data-ttu-id="33830-264">Sie können bis zu (aber nicht mehr als) 5 &lt;selection&gt;-Werte bereitstellen</span><span class="sxs-lookup"><span data-stu-id="33830-264">Provide up to (but no more than) 5 &lt;selection&gt; values</span></span>