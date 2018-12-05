---
title: Einzelhandel (RDX-App) Demo Features Ihrer app hinzufügen
description: Bereiten Sie Ihre app für den Einzelhandel Demo-Modus, helfen, Ihre app auf die Verkaufsversion Vertriebsabteilung zu präsentieren.
ms.assetid: f83f950f-7fdd-4f18-8127-b92a8f400061
ms.date: 10/02/2018
ms.topic: article
keywords: Windows 10, UWP, Demo-App für den Einzelhandel
ms.localizationpriority: medium
ms.openlocfilehash: 9d6baaff5ca2af781e72c9b4643fa1ea0624e0eb
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8729622"
---
# <a name="add-retail-demo-rdx-features-to-your-app"></a><span data-ttu-id="1dd4b-104">Einzelhandel (RDX-App) Demo Features Ihrer app hinzufügen</span><span class="sxs-lookup"><span data-stu-id="1dd4b-104">Add retail demo (RDX) features to your app</span></span>

<span data-ttu-id="1dd4b-105">Fügen Sie einen Retail Demo-Modus in Ihrer Windows-app, damit Kunden, die PCs und Geräte auf die Vertriebsabteilung testen sofort beginnen können.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-105">Include a retail demo mode in your Windows app so customers who try out PCs and devices on the sales floor can jump right in.</span></span>

<span data-ttu-id="1dd4b-106">Wenn Kunden im Einzelhandel befinden, erwarten sie, dass Demos von Computern und Geräten testen können.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-106">When customers are in a retail store, they expect to be able to try out demos of PCs and devices.</span></span> <span data-ttu-id="1dd4b-107">Sie sind häufig einen erheblichen Teil der Zeit mit apps über die [Demo Einzelhandel (RDX-App) auftreten](https://docs.microsoft.com/windows-hardware/customize/desktop/retail-demo-experience).</span><span class="sxs-lookup"><span data-stu-id="1dd4b-107">They often spend a considerable chunk of their time playing around with apps through the [retail demo experience (RDX)](https://docs.microsoft.com/windows-hardware/customize/desktop/retail-demo-experience).</span></span>

<span data-ttu-id="1dd4b-108">Sie können Ihre app einrichten, um unterschiedliche Funktionen im _normalen_ oder _Einzelhandel_ Modi bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-108">You can set up your app to provide different experiences while in _normal_ or _retail_ modes.</span></span> <span data-ttu-id="1dd4b-109">Z. B. Wenn Ihre app mit einem Setupprozess gestartet wird, können Sie im einzelhandelsmodus überspringen und die app mit Einstellungen für die Daten und standardmäßig vorab, damit sie sofort beginnen können.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-109">For example, if your app starts with a setup process, you might skip past it in retail mode, and prepopulate the app with sample data and default settings so they can jump right in.</span></span>

<span data-ttu-id="1dd4b-110">Aus Sicht unserer Kunden besteht nur eine app.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-110">From our customers' perspective, there is only one app.</span></span> <span data-ttu-id="1dd4b-111">Um zwischen den beiden Modi unterscheiden können, empfehlen wir während Ihre app im einzelhandelsmodus ist, das Wort "Einzelhandel" anzeigt hervorgehobener Stelle in der Titelleiste oder an einer geeigneten Stelle.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-111">To help customers distinguish between the two modes, we recommend that while your app is in retail mode, it shows the word "Retail" prominently in the title bar or in a suitable location.</span></span>

<span data-ttu-id="1dd4b-112">Zusätzlich zu den Microsoft Store-Anforderungen für apps müssen RDX-fähige apps auch werden mit dem RDX-Setup, Bereinigung und Update-Prozesse, um sicherzustellen, dass die Kunden ein Geschäft durchgehend positiv Erlebnis Aktualisierungssystem der Vorführgeräte kompatibel.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-112">In addition to the Microsoft Store requirements for apps, RDX-aware apps must also be compatible with the RDX setup, cleanup, and update processes to ensure that customers have a consistently positive experience at the retail store.</span></span>

## <a name="design-principles"></a><span data-ttu-id="1dd4b-113">Designprinzipien</span><span class="sxs-lookup"><span data-stu-id="1dd4b-113">Design principles</span></span>

* <span data-ttu-id="1dd4b-114">**Optimale Präsentation**.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-114">**Show your best**.</span></span> <span data-ttu-id="1dd4b-115">Verwenden Sie die Demo-App, um Showcase großartig von Ihrer app.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-115">Use the retail demo experience to showcase why your app rocks.</span></span> <span data-ttu-id="1dd4b-116">Dies ist wahrscheinlich das erste Mal Ihr Kunde Ihre app so diese besten Seite angezeigt, die angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-116">This is likely the first time your customer will see your app, so show them the best piece!</span></span>

* <span data-ttu-id="1dd4b-117">**Zeigen sie schnell**.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-117">**Show it fast**.</span></span> <span data-ttu-id="1dd4b-118">Kunden können ungeduldig sein – je schneller ein Benutzer den Wert ihrer App erfasst, desto besser.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-118">Customers can be impatient - The faster a user can experience the real value of your app, the better.</span></span>

* <span data-ttu-id="1dd4b-119">**Einfache Demonstration**.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-119">**Keep the story simple**.</span></span> <span data-ttu-id="1dd4b-120">Die Demo-App ist ein Elevator Pitch für den Wert Ihrer app.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-120">The retail demo experience is an elevator pitch for your app’s value.</span></span>

* <span data-ttu-id="1dd4b-121">**Fokus auf die Erfahrung**.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-121">**Focus on the experience**.</span></span> <span data-ttu-id="1dd4b-122">Geben Sie den Benutzern die Zeit, um Ihre Inhalte zu verdauen.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-122">Give the user time to digest your content.</span></span> <span data-ttu-id="1dd4b-123">Es ist zwar wichtig, dass die Benutzer schnell zum wichtigsten Teil gelangen, aber nur mithilfe entsprechender Pausen können sie den Wert der App richtig erkennen.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-123">While getting them to the best part fast is important, designing suitable pauses can help them to fully enjoy the experience.</span></span>

## <a name="technical-requirements"></a><span data-ttu-id="1dd4b-124">Technische Anforderungen</span><span class="sxs-lookup"><span data-stu-id="1dd4b-124">Technical requirements</span></span>

<span data-ttu-id="1dd4b-125">Da RDX-fähige apps werden Ihrer App Kunden im Einzelhandel optimal präsentieren sollen, müssen technischen Anforderungen und Datenschutzrichtlinien in Bezug auf, die alle Retail Demo-apps für den Microsoft Store hat.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-125">As RDX-aware apps are meant to showcase the best of your app to retail customers, they must meet technical requirements and adhere to privacy regulations that the Microsoft Store has for all retail demo experience apps.</span></span>

<span data-ttu-id="1dd4b-126">Dies kann als Prüfliste für die sich bei der Prüfung vorzubereiten und Klarheit in den Testprozess verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-126">This can be used as a checklist to help you prepare for the validation process and to provide clarity in the testing process.</span></span> <span data-ttu-id="1dd4b-127">Beachten Sie, dass diese Anforderungen nicht nur für den Prüfprozess, sondern für die gesamte Lebensdauer der Demo-App für den Einzelhandel (d.h. solange Ihre App auf den Vorführgeräten ausgeführt wird) eingehalten werden müssen.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-127">Note that these requirements have to be maintained, not just for the validation process, but for the entire lifetime of the retail demo experience app; as long as your app stays running on the retail demo devices.</span></span>

### <a name="critical-requirements"></a><span data-ttu-id="1dd4b-128">Kritische Anforderungen</span><span class="sxs-lookup"><span data-stu-id="1dd4b-128">Critical requirements</span></span>

<span data-ttu-id="1dd4b-129">RDX-fähige apps, die diese kritischen Anforderungen nicht erfüllen werden so schnell wie möglich aus allen vorführgeräten entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-129">RDX-aware apps that do not meet these critical requirements will be removed from all retail demo devices as soon as possible.</span></span>

* <span data-ttu-id="1dd4b-130">**Fragen Sie nicht nach personenbezogenen Informationen (PII)**.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-130">**Don't ask for personal identifiable information (PII)**.</span></span> <span data-ttu-id="1dd4b-131">Dies umfasst die Anmeldedaten, Microsoft-Kontoinformationen oder Kontakt Details.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-131">This includes login info, Microsoft account info, or contact details.</span></span>

* <span data-ttu-id="1dd4b-132">**Fehlerfreie auftreten**.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-132">**Error-free experience**.</span></span> <span data-ttu-id="1dd4b-133">Ihr App muss fehlerfrei funktionieren.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-133">Your app must run with no errors.</span></span> <span data-ttu-id="1dd4b-134">Außerdem dürfen keine Fehler-Pop-ups oder -Benachrichtigungen angezeigt werden, wenn Kunden die Vorführgeräte verwenden.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-134">Additionally, no error pop ups or notifications should be shown to customers using the retail demo devices.</span></span> <span data-ttu-id="1dd4b-135">Fehler wider negativ auf die app selbst, Ihre Marke, das Gerät Marke, Hersteller des Geräts Marke und Microsoft Marke.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-135">Errors reflect negatively on the app itself, your brand, the device's brand, the device's manufacturer's brand, and Microsoft's brand.</span></span>

* <span data-ttu-id="1dd4b-136">**Kostenpflichtige apps müssen über einen Testmodus verfügen**.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-136">**Paid apps must have a trial mode**.</span></span> <span data-ttu-id="1dd4b-137">Ihre app muss entweder ein kostenloses oder einen [Testmodus](https://msdn.microsoft.com/windows/uwp/monetize/exclude-or-limit-features-in-a-trial-version-of-your-app)enthalten.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-137">Your app either needs to be a free or include a [trial mode](https://msdn.microsoft.com/windows/uwp/monetize/exclude-or-limit-features-in-a-trial-version-of-your-app).</span></span> <span data-ttu-id="1dd4b-138">Kunden, die sich in einem Laden etwas ansehen, möchten dafür nicht zahlen.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-138">Customers aren't looking to pay for an experience in a retail store.</span></span>

### <a name="high-priority-requirements"></a><span data-ttu-id="1dd4b-139">Anforderungen mit hoher Priorität</span><span class="sxs-lookup"><span data-stu-id="1dd4b-139">High-priority requirements</span></span>

<span data-ttu-id="1dd4b-140">RDX-fähige apps, die diese Anforderungen mit hoher Priorität nicht erfüllen müssen für ein Update sofort untersucht werden.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-140">RDX-aware apps that do not meet these high priority requirements need to be investigated for a fix immediately.</span></span> <span data-ttu-id="1dd4b-141">Wenn eine umgehende Problembehebung nicht möglich ist, kann diese App von allen Vorführgeräten entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-141">If no immediate fix is found, this app may be removed from all retail demo devices.</span></span>

* <span data-ttu-id="1dd4b-142">**Memorable offline auftreten**.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-142">**Memorable offline experience**.</span></span> <span data-ttu-id="1dd4b-143">Ihre app muss eine tolle offline-Erfahrung zu bieten, da etwa 50 % der Geräte an einzelhandelsstandorten offline sind.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-143">Your app needs to demonstrate a great offline experience as about 50% of the devices are offline at retail locations.</span></span> <span data-ttu-id="1dd4b-144">Dadurch wird sichergestellt, dass das Erlebnis für die Kunden auch dann positiv ist, wenn sie offline mit Ihrer App interagieren.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-144">This is to ensure that customers interacting with your app offline are still able to have a meaningful and positive experience.</span></span>

* <span data-ttu-id="1dd4b-145">**Aktualisierte Content-Erfahrung**.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-145">**Updated content experience**.</span></span> <span data-ttu-id="1dd4b-146">Ihre app sollte nie für das wird aktualisiert, sobald Sie online sein.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-146">Your app should never be prompt for updates when online.</span></span> <span data-ttu-id="1dd4b-147">Wenn Updates erforderlich sind, sollten sie im Hintergrund ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-147">If updates are needed, they should be performed silently.</span></span>

* <span data-ttu-id="1dd4b-148">**Keine anonyme Kommunikation**.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-148">**No anonymous communication**.</span></span> <span data-ttu-id="1dd4b-149">Da ein Kunde ein Vorführgerät nutzen, anonyme Benutzer ist, sollten sie nicht Nachricht oder Inhalte Freigeben des Geräts können.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-149">Because a customer using a retail demo device is an anonymous user, they should not be able to message or share content from the device.</span></span>

* <span data-ttu-id="1dd4b-150">**Konsistentes Erlebnis mit den Bereinigungsprozess zu übermitteln**.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-150">**Deliver consistent experiences by using the cleanup process**.</span></span> <span data-ttu-id="1dd4b-151">Die Verwendung eines Vorführgeräts sollte für alle Kunden gleich sein.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-151">Every customer should have the same experience when they walk up to a retail demo device.</span></span> <span data-ttu-id="1dd4b-152">Ihre app sollte [Bereinigungsprozess](#clean-up-process) verwenden, um nach jeder Verwendung zum gleichen Standardzustand zurückkehrt wird.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-152">Your app should use [clean up process](#clean-up-process) to return to the same default state after each use.</span></span> <span data-ttu-id="1dd4b-153">Wir möchten wir nicht den nächsten Kunden um festzustellen, welche die letzte Kunden.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-153">We don't want the next customer to see what the last customer left behind.</span></span> <span data-ttu-id="1dd4b-154">Dies umfasst z.B. Punktestände, Erfolge und aufgehobene Sperren.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-154">This includes scoreboards, achievements, and unlocks.</span></span>

* <span data-ttu-id="1dd4b-155">**Altersgerechte Inhalte**.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-155">**Age appropriate content**.</span></span> <span data-ttu-id="1dd4b-156">Alle app-Inhalt muss Altersklasse oder eine jüngere zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-156">All app content needs to be assigned a Teen or lower rating category.</span></span> <span data-ttu-id="1dd4b-157">Weitere Informationen finden Sie unter [abrufen, die die app durch die IARC bewertet](https://www.globalratings.com/for-developers.aspx) und [ESRB-Bewertung](https://www.esrb.org/ratings/ratings_guide.aspx).</span><span class="sxs-lookup"><span data-stu-id="1dd4b-157">To learn more, see [Getting your app rated by IARC](https://www.globalratings.com/for-developers.aspx) and [ESRB ratings](https://www.esrb.org/ratings/ratings_guide.aspx).</span></span>

### <a name="medium-priority-requirements"></a><span data-ttu-id="1dd4b-158">Anforderungen mit mittlerer Priorität</span><span class="sxs-lookup"><span data-stu-id="1dd4b-158">Medium-priority requirements</span></span>

<span data-ttu-id="1dd4b-159">Das Windows-Team für den Einzelhandel setzt sich unter Umständen direkt mit Entwicklern in Verbindung, um mit ihnen zu besprechen, wie diese Probleme behoben werden können.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-159">The Windows Retail Store team may reach out to developers directly to set up a discussion on how to fix these issues.</span></span>

* <span data-ttu-id="1dd4b-160">**Möglichkeit zum Ausführen von erfolgreich über eine Vielzahl von Geräten**.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-160">**Ability to run successfully over a range of devices**.</span></span> <span data-ttu-id="1dd4b-161">Apps müssen auf allen Geräten, einschließlich Geräten mit Low-End-Spezifikationen ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-161">Apps must run well on all devices, including devices with low-end specifications.</span></span> <span data-ttu-id="1dd4b-162">Wenn die app auf Geräten, die nicht die Mindestanforderungen erfüllt installiert ist, muss die app klar den Benutzer darüber zu informieren.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-162">If the app is installed on devices that did not meet the minimum specifications, the app needs to clearly inform the user about this.</span></span> <span data-ttu-id="1dd4b-163">Die Mindestgeräteanforderungen müssen bekanntgegeben werden, damit die App immer mit höchster Leistung ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-163">Minimum device requirements has to be made known so that the app can always run with high performance.</span></span>

* <span data-ttu-id="1dd4b-164">**Erfüllen der größenanforderungen für Einzelhandel**.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-164">**Meet retail store app size requirements**.</span></span> <span data-ttu-id="1dd4b-165">Die App darf eine Größe von 800MB nicht übersteigen.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-165">The app must be smaller than 800MB.</span></span> <span data-ttu-id="1dd4b-166">Wenden Sie sich an das Windows-Einzelhandel-Team direkt Weitere Informationen zu Wenn Ihre RDX-fähige app die größenanforderungen nicht entspricht.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-166">Contact the Windows Retail Store team directly for further discussion if your RDX-aware app does not meet the size requirements.</span></span>

## <a name="retailinfo-api-preparing-your-code-for-demo-mode"></a><span data-ttu-id="1dd4b-167">RetailInfo API: Vorbereiten von Ihrem Code für Demo-Modus</span><span class="sxs-lookup"><span data-stu-id="1dd4b-167">RetailInfo API: Preparing your code for demo mode</span></span>

### <a name="isdemomodeenabled"></a><span data-ttu-id="1dd4b-168">IsDemoModeEnabled</span><span class="sxs-lookup"><span data-stu-id="1dd4b-168">IsDemoModeEnabled</span></span>
<span data-ttu-id="1dd4b-169">Die Eigenschaft [**IsDemoModeEnabled**](https://docs.microsoft.com/uwp/api/windows.system.profile.retailinfo.isdemomodeenabled) [**RetailInfo**](https://docs.microsoft.com/uwp/api/Windows.System.Profile.RetailInfo) -Hilfsklasse, die Teil des [Windows.System.Profile](https://docs.microsoft.com/uwp/api/windows.system.profile) Namespaces in Windows 10 SDK ist, wird als einen booleschen Indikator verwendet, an welcher Codepfad, Ihre app ausgeführt wird – die normale _ _-Modus oder im _einzelhandelsmodus_ aktiviert.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-169">The [**IsDemoModeEnabled**](https://docs.microsoft.com/uwp/api/windows.system.profile.retailinfo.isdemomodeenabled) property in the [**RetailInfo**](https://docs.microsoft.com/uwp/api/Windows.System.Profile.RetailInfo) utility class, which is part of the [Windows.System.Profile](https://docs.microsoft.com/uwp/api/windows.system.profile) namespace in the Windows 10 SDK, is used as a Boolean indicator to specify which code path your app runs on - the _normal_ mode or the _retail_ mode.</span></span>

``` csharp
using Windows.Storage;

StorageFolder folder = ApplicationData.Current.LocalFolder;

if (Windows.System.Profile.RetailInfo.IsDemoModeEnabled) 
{
    // Use the demo specific directory
    folder = await folder.GetFolderAsync(“demo”);
}

StorageFile file = await folder.GetFileAsync(“hello.txt”);
// Now read from file
```

``` cpp
using namespace Windows::Storage;

StorageFolder^ localFolder = ApplicationData::Current->LocalFolder;

if (Windows::System::Profile::RetailInfo::IsDemoModeEnabled) 
{
    // Use the demo specific directory
    create_task(localFolder->GetFolderAsync(“demo”).then([this](StorageFolder^ demoFolder)
    {
        return demoFolder->GetFileAsync(“hello.txt”);
    }).then([this](task<StorageFile^> fileTask)
    {
        StorageFile^ file = fileTask.get();
    });
    // Do something with file
}
else
{
    create_task(localFolder->GetFileAsync(“hello.txt”).then([this](StorageFile^ file)
    {
        // Do something with file
    });
}
```

``` javascript
if (Windows.System.Profile.retailInfo.isDemoModeEnabled) {
    console.log(“Retail mode is enabled.”);
} else {
    Console.log(“Retail mode is not enabled.”);
}
```

### <a name="retailinfoproperties"></a><span data-ttu-id="1dd4b-170">RetailInfo.Properties</span><span class="sxs-lookup"><span data-stu-id="1dd4b-170">RetailInfo.Properties</span></span>

<span data-ttu-id="1dd4b-171">Wenn [**IsDemoModeEnabled**](https://docs.microsoft.com/uwp/api/windows.system.profile.retailinfo.isdemomodeenabled) „true“ zurückgibt, können Sie mithilfe von [**RetailInfo.Properties**](https://docs.microsoft.com/uwp/api/windows.system.profile.retailinfo.properties) einen Satz von Eigenschaften zum Gerät abfragen, um eine besser angepasste Verwendung der Demo-App zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-171">When [**IsDemoModeEnabled**](https://docs.microsoft.com/uwp/api/windows.system.profile.retailinfo.isdemomodeenabled) returns true, you can query for a set of properties about the device using [**RetailInfo.Properties**](https://docs.microsoft.com/uwp/api/windows.system.profile.retailinfo.properties) to build a more customized retail demo experience.</span></span> <span data-ttu-id="1dd4b-172">Diese Eigenschaften umfassen [**ManufacturerName**](https://docs.microsoft.com/uwp/api/windows.system.profile.knownretailinfoproperties.manufacturername), [**Screensize**](https://docs.microsoft.com/uwp/api/windows.system.profile.knownretailinfoproperties.screensize), [**Memory**](https://docs.microsoft.com/uwp/api/windows.system.profile.knownretailinfoproperties.memory) usw.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-172">These properties include [**ManufacturerName**](https://docs.microsoft.com/uwp/api/windows.system.profile.knownretailinfoproperties.manufacturername), [**Screensize**](https://docs.microsoft.com/uwp/api/windows.system.profile.knownretailinfoproperties.screensize), [**Memory**](https://docs.microsoft.com/uwp/api/windows.system.profile.knownretailinfoproperties.memory) and so on.</span></span>

```csharp
using Windows.UI.Xaml.Controls;
using Windows.System.Profile

TextBlock priceText = new TextBlock();
priceText.Text = RetailInfo.Properties[KnownRetailInfo.Price];
// Assume infoPanel is a StackPanel declared in XAML
this.infoPanel.Children.Add(priceText);
```

```cpp
using namespace Windows::UI::Xaml::Controls;
using namespace Windows::System::Profile;

TextBlock ^manufacturerText = ref new TextBlock();
manufacturerText.set_Text(RetailInfo::Properties[KnownRetailInfoProperties::Price]);
// Assume infoPanel is a StackPanel declared in XAML
this->infoPanel->Children->Add(manufacturerText);
```

```javascript
var pro = Windows.System.Profile;
console.log(pro.retailInfo.properties[pro.KnownRetailInfoProperties.price);
```

#### <a name="idl"></a><span data-ttu-id="1dd4b-173">IDL</span><span class="sxs-lookup"><span data-stu-id="1dd4b-173">IDL</span></span>

```
//  Copyright (c) Microsoft Corporation. All rights reserved.
//
//  WindowsRuntimeAPISet

import "oaidl.idl";
import "inspectable.idl";
import "Windows.Foundation.idl";
#include <sdkddkver.h>

namespace Windows.System.Profile
{
    runtimeclass RetailInfo;
    runtimeclass KnownRetailInfoProperties;

    [version(NTDDI_WINTHRESHOLD), uuid(0712C6B8-8B92-4F2A-8499-031F1798D6EF), exclusiveto(RetailInfo)]
    [version(NTDDI_WINTHRESHOLD, Platform.WindowsPhone)]
    interface IRetailInfoStatics : IInspectable
    {
        [propget] HRESULT IsDemoModeEnabled([out, retval] boolean *value);
        [propget] HRESULT Properties([out, retval, hasvariant] Windows.Foundation.Collections.IMapView<HSTRING, IInspectable *> **value);
    }

    [version(NTDDI_WINTHRESHOLD), uuid(50BA207B-33C4-4A5C-AD8A-CD39F0A9C2E9), exclusiveto(KnownRetailInfoProperties)]
    [version(NTDDI_WINTHRESHOLD, Platform.WindowsPhone)]
    interface IKnownRetailInfoPropertiesStatics : IInspectable
    {
        [propget] HRESULT RetailAccessCode([out, retval] HSTRING *value);
        [propget] HRESULT ManufacturerName([out, retval] HSTRING *value);
        [propget] HRESULT ModelName([out, retval] HSTRING *value);
        [propget] HRESULT DisplayModelName([out, retval] HSTRING *value);
        [propget] HRESULT Price([out, retval] HSTRING *value);
        [propget] HRESULT IsFeatured([out, retval] HSTRING *value);
        [propget] HRESULT FormFactor([out, retval] HSTRING *value);
        [propget] HRESULT ScreenSize([out, retval] HSTRING *value);
        [propget] HRESULT Weight([out, retval] HSTRING *value);
        [propget] HRESULT DisplayDescription([out, retval] HSTRING *value);
        [propget] HRESULT BatteryLifeDescription([out, retval] HSTRING *value);
        [propget] HRESULT ProcessorDescription([out, retval] HSTRING *value);
        [propget] HRESULT Memory([out, retval] HSTRING *value);
        [propget] HRESULT StorageDescription([out, retval] HSTRING *value);
        [propget] HRESULT GraphicsDescription([out, retval] HSTRING *value);
        [propget] HRESULT FrontCameraDescription([out, retval] HSTRING *value);
        [propget] HRESULT RearCameraDescription([out, retval] HSTRING *value);
        [propget] HRESULT HasNfc([out, retval] HSTRING *value);
        [propget] HRESULT HasSdSlot([out, retval] HSTRING *value);
        [propget] HRESULT HasOpticalDrive([out, retval] HSTRING *value);
        [propget] HRESULT IsOfficeInstalled([out, retval] HSTRING *value);
        [propget] HRESULT WindowsVersion([out, retval] HSTRING *value);
    }

    [version(NTDDI_WINTHRESHOLD), static(IRetailInfoStatics, NTDDI_WINTHRESHOLD)]
    [version(NTDDI_WINTHRESHOLD, Platform.WindowsPhone), static(IRetailInfoStatics, NTDDI_WINTHRESHOLD, Platform.WindowsPhone)]
    [threading(both)]
    [marshaling_behavior(agile)]
    runtimeclass RetailInfo
    {
    }

    [version(NTDDI_WINTHRESHOLD), static(IKnownRetailInfoPropertiesStatics, NTDDI_WINTHRESHOLD)]
    [version(NTDDI_WINTHRESHOLD, Platform.WindowsPhone), static(IKnownRetailInfoPropertiesStatics, NTDDI_WINTHRESHOLD, Platform.WindowsPhone)]
    [threading(both)]
    [marshaling_behavior(agile)]
    runtimeclass KnownRetailInfoProperties
    {
    }
}
```

## <a name="cleanup-process"></a><span data-ttu-id="1dd4b-174">Bereinigungsprozess</span><span class="sxs-lookup"><span data-stu-id="1dd4b-174">Cleanup process</span></span>

<span data-ttu-id="1dd4b-175">Bereinigung beginnt mit zwei Minuten nach dem ein Käufer beendet interagiert mit dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-175">Cleanup begins two minutes after a shopper stops interacting with the device.</span></span> <span data-ttu-id="1dd4b-176">Die Retail Demo wiedergegeben wird, und Windows beginnt das Zurücksetzen Beispieldaten in die Kontakte, Fotos und anderen apps.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-176">The retail demo plays, and Windows begins resetting any sample data in the contacts, photos, and other apps.</span></span> <span data-ttu-id="1dd4b-177">Je nach Gerät kann dies zwischen 1 bis 5 Minuten vollständig alles wieder zurücksetzen dauern.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-177">Depending on the device, this could take between 1-5 minutes to fully reset everything back to normal.</span></span> <span data-ttu-id="1dd4b-178">Dadurch wird sichergestellt, dass jeder Kunde im Geschäft kann auf einem Gerät problemlos und die gleiche Erfahrung bei der Interaktion mit dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-178">This ensures that every customer in the retail store can walk up to a device and have the same experience when interacting with the device.</span></span>

<span data-ttu-id="1dd4b-179">Schritt 1: Bereinigen</span><span class="sxs-lookup"><span data-stu-id="1dd4b-179">Step 1: Cleanup</span></span>
* <span data-ttu-id="1dd4b-180">Alle Win32- und Store-Apps werden geschlossen.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-180">All Win32 and store apps are closed</span></span>
* <span data-ttu-id="1dd4b-181">Alle Dateien in bekannten Ordnern wie __Bilder__, __Videos__, __Musik__, __Dokumente__, __SavedPictures__, __CameraRoll__, __Desktop__ und __Downloads__ Ordner werden gelöscht.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-181">All files in known folders like __Pictures__, __Videos__, __Music__, __Documents__, __SavedPictures__, __CameraRoll__, __Desktop__ and __Downloads__ folders are deleted</span></span>
* <span data-ttu-id="1dd4b-182">Unstrukturierte und strukturierte Roamingzustände werden gelöscht.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-182">Unstructured and structured roaming states are deleted</span></span>
* <span data-ttu-id="1dd4b-183">Strukturierte lokale Zustände werden gelöscht.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-183">Structured local states are deleted</span></span>

<span data-ttu-id="1dd4b-184">Schritt 2: Einrichten</span><span class="sxs-lookup"><span data-stu-id="1dd4b-184">Step 2:  Setup</span></span>
* <span data-ttu-id="1dd4b-185">Offlinegeräte: Ordner bleiben leer</span><span class="sxs-lookup"><span data-stu-id="1dd4b-185">For offline devices: Folders remain empty</span></span>
* <span data-ttu-id="1dd4b-186">Onlinegeräte: Demoressourcen für den Einzelhandel können vom Microsoft Store per Push an das Gerät übertragen werden.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-186">For online devices: Retail demo assets can be pushed to the device from the Microsoft Store</span></span>

### <a name="store-data-across-user-sessions"></a><span data-ttu-id="1dd4b-187">Speichern von Daten auf benutzersitzungen</span><span class="sxs-lookup"><span data-stu-id="1dd4b-187">Store data across user sessions</span></span>

<span data-ttu-id="1dd4b-188">Zum Speichern von Daten sitzungsübergreifend Benutzer können Sie Informationen in __ApplicationData.Current.TemporaryFolder__ speichern, wie Daten in diesem Ordner mit der Standard-Cleanup-Prozess nicht automatisch gelöscht.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-188">To store data across user sessions, you can store information in __ApplicationData.Current.TemporaryFolder__ as the default cleanup process does not automatically delete data in this folder.</span></span> <span data-ttu-id="1dd4b-189">Beachten Sie, dass mit *LocalState* gespeicherten Informationen während der Bereinigungsprozess gelöscht wird.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-189">Note that information stored using *LocalState* is deleted during the cleanup process.</span></span>

### <a name="customize-the-cleanup-process"></a><span data-ttu-id="1dd4b-190">Den Bereinigungsprozess anpassen</span><span class="sxs-lookup"><span data-stu-id="1dd4b-190">Customize the cleanup process</span></span>

<span data-ttu-id="1dd4b-191">Um den Bereinigungsprozess anpassen, Implementieren der `Microsoft-RetailDemo-Cleanup` app-Dienst in Ihre app.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-191">To customize the cleanup process, implement the `Microsoft-RetailDemo-Cleanup` app service into your app.</span></span>

<span data-ttu-id="1dd4b-192">Szenarien, in denen eine benutzerdefinierte Bereinigungslogik erforderlich ist, umfassen das Ausführen einer umfassenden Einrichtung, das Herunterladen und Zwischenspeichern von Daten oder nicht *LocalState* Daten gelöscht werden sollen.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-192">Scenarios where a custom cleanup logic is needed includes running an extensive setup, downloading and caching data, or not wanting *LocalState* data to be deleted.</span></span>

<span data-ttu-id="1dd4b-193">Schritt 1: Deklarieren Sie den _Microsoft-RetailDemo-Cleanup_ -Dienst in Ihrem app-Manifest.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-193">Step 1: Declare the _Microsoft-RetailDemo-Cleanup_ service in your app manifest.</span></span>
``` CSharp
  <Applications>
      <Extensions>
        <uap:Extension Category="windows.appService" EntryPoint="MyCompany.MyApp.RDXCustomCleanupTask">
          <uap:AppService Name="Microsoft-RetailDemo-Cleanup" />
        </uap:Extension>
      </Extensions>
   </Application>
  </Applications>

```

<span data-ttu-id="1dd4b-194">Schritt 2: Implementieren der benutzerdefinierten Bereinigungslogik unter der _AppdataCleanup_ -Funktion mithilfe der folgenden Beispielvorlage.</span><span class="sxs-lookup"><span data-stu-id="1dd4b-194">Step 2: Implement your custom cleanup logic under the _AppdataCleanup_ case function using the sample template below.</span></span>
``` CSharp
using System;
using System.IO;
using System.Runtime.Serialization.Json;
using System.Threading;
using System.Threading.Tasks;
using Windows.ApplicationModel.AppService;
using Windows.ApplicationModel.Background;
using Windows.Foundation.Collections;
using Windows.Storage;

namespace MyCompany.MyApp
{
    public sealed class RDXCustomCleanupTask : IBackgroundTask
    {
        BackgroundTaskCancellationReason _cancelReason = BackgroundTaskCancellationReason.Abort;
        BackgroundTaskDeferral _deferral = null;
        IBackgroundTaskInstance _taskInstance = null;
        AppServiceConnection _appServiceConnection = null;

        const string MessageCommand = "Command";

        public void Run(IBackgroundTaskInstance taskInstance)
        {
            // Get the deferral object from the task instance, and take a reference to the taskInstance;
            _deferral = taskInstance.GetDeferral();
            _taskInstance = taskInstance;
            _taskInstance.Canceled += new BackgroundTaskCanceledEventHandler(OnCanceled);

            AppServiceTriggerDetails appService = _taskInstance.TriggerDetails as AppServiceTriggerDetails;
            if ((appService != null) && (appService.Name == "Microsoft-RetailDemo-Cleanup"))
            {
                _appServiceConnection = appService.AppServiceConnection;
                _appServiceConnection.RequestReceived += _appServiceConnection_RequestReceived;
                _appServiceConnection.ServiceClosed += _appServiceConnection_ServiceClosed;
            }
            else
            {
                _deferral.Complete();
            }
        }

        void _appServiceConnection_ServiceClosed(AppServiceConnection sender, AppServiceClosedEventArgs args)
        {
        }

        async void _appServiceConnection_RequestReceived(AppServiceConnection sender, AppServiceRequestReceivedEventArgs args)
        {
            //Get a deferral because we will be calling async code
            AppServiceDeferral requestDeferral = args.GetDeferral();
            string command = null;
            var returnData = new ValueSet();

            try
            {
                ValueSet message = args.Request.Message;
                if (message.ContainsKey(MessageCommand))
                {
                    command = message[MessageCommand] as string;
                }

                if (command != null)
                {
                    switch (command)
                    {
                        case "AppdataCleanup":
                            {
                                // Do custom clean up logic here
                                break;
                            }
                    }
                }
            }
            catch (Exception e)
            {
            }
            finally
            {
                requestDeferral.Complete();
                // Also release the task deferral since we only process one request per instance.
                _deferral.Complete();
            }
        }

        private void OnCanceled(IBackgroundTaskInstance sender, BackgroundTaskCancellationReason reason)
        {
            _cancelReason = reason;
        }
    }
}
```

## <a name="related-links"></a><span data-ttu-id="1dd4b-195">Verwandte Links</span><span class="sxs-lookup"><span data-stu-id="1dd4b-195">Related links</span></span>

* [<span data-ttu-id="1dd4b-196">Speichern und Abrufen von App-Daten</span><span class="sxs-lookup"><span data-stu-id="1dd4b-196">Store and retrieve app data</span></span>](https://msdn.microsoft.com/windows/uwp/app-settings/store-and-retrieve-app-data)
* [<span data-ttu-id="1dd4b-197">Erstellen und Nutzen eines App-Diensts</span><span class="sxs-lookup"><span data-stu-id="1dd4b-197">How to create and consume an app service</span></span>](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)
* [<span data-ttu-id="1dd4b-198">Lokalisieren von App-Inhalten</span><span class="sxs-lookup"><span data-stu-id="1dd4b-198">Localizing app contents</span></span>](https://msdn.microsoft.com/windows/uwp/globalizing/globalizing-portal)
* [<span data-ttu-id="1dd4b-199">Demo-App (RDX-App)</span><span class="sxs-lookup"><span data-stu-id="1dd4b-199">Retail demo experience (RDX)</span></span>](https://docs.microsoft.com/windows-hardware/customize/desktop/retail-demo-experience)
