---
author: TylerMSFT
title: Erstellen und Verwenden einer App-Erweiterung
description: "Schreiben und Hosten Sie die App-Erweiterungen der universellen Windows-Plattform (UWP), mit denen Sie Ihre App über Pakete erweitern können, die Benutzer aus dem Microsoft Store installieren können."
keywords: App-Erweiterung, App-Dienst, Hintergrund
ms.author: twhitney
ms.date: 10/05/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
localizationpriority: medium
ms.openlocfilehash: 2391b8efa3d57adcaeec55623bbaceb579add6b8
ms.sourcegitcommit: 44a24b580feea0f188c7eae36e72e4a4f412802b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="create-and-host-an-app-extension"></a><span data-ttu-id="b91e1-104">Erstellen und Hosten einer App-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b91e1-104">Create and host an app extension</span></span>

<span data-ttu-id="b91e1-105">In diesem Artikel wird erläutert, wie Sie eine UWP-App-Erweiterung erstellen und in einer UWP-App hosten.</span><span class="sxs-lookup"><span data-stu-id="b91e1-105">This article shows you how to create a UWP app extension and host it in a UWP app.</span></span>

<span data-ttu-id="b91e1-106">Dieser Artikel wird zusammen mit einem Codebeispiel angezeigt:</span><span class="sxs-lookup"><span data-stu-id="b91e1-106">This article is accompanied by a code sample:</span></span>
- <span data-ttu-id="b91e1-107">Laden Sie [Math Extension-Codebeispiel](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/MathExtensionSample.zip)herunter und entzippen Sie die Dateien.</span><span class="sxs-lookup"><span data-stu-id="b91e1-107">Download and unzip [Math Extension code sample](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/MathExtensionSample.zip).</span></span>
- <span data-ttu-id="b91e1-108">Öffnen Sie in Visual Studio 2017 MathExtensionSample.sln.</span><span class="sxs-lookup"><span data-stu-id="b91e1-108">In Visual Studio 2017, open MathExtensionSample.sln.</span></span> <span data-ttu-id="b91e1-109">Legen Sie den Buildtyp auf x86 fest (**Build** > **Konfigurationsmanager**, ändern Sie dann **Plattform** auf **x86** für beide Projekte).</span><span class="sxs-lookup"><span data-stu-id="b91e1-109">Set the build type to x86 (**Build** > **Configuration Manager**, then change **Platform** to **x86** for both projects).</span></span>
- <span data-ttu-id="b91e1-110">Stellen Sie die Lösung bereit: **Build** > **Lösung bereitstellen**.</span><span class="sxs-lookup"><span data-stu-id="b91e1-110">Deploy the solution: **Build** > **Deploy Solution**.</span></span>

## <a name="introduction-to-app-extensions"></a><span data-ttu-id="b91e1-111">Einführung in App-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="b91e1-111">Introduction to app extensions</span></span>

<span data-ttu-id="b91e1-112">Plug-Ins, Add-Ins und Add-Ons sind unterschiedliche Namen, die Sie möglicherweise für die so genannten App-Erweiterungen in der universellen Windows-Plattform (UWP) gehört haben.</span><span class="sxs-lookup"><span data-stu-id="b91e1-112">Plugins, add-ins, and add-ons are different names you may be familiar with for what we call app extensions in the Universal Windows Platform (UWP).</span></span> <span data-ttu-id="b91e1-113">Microsoft Edge-Erweiterungen UWP-App-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="b91e1-113">Microsoft Edge extensions are UWP app extensions.</span></span> <span data-ttu-id="b91e1-114">UWP-App-Erweiterungen wurden in der Windows10 Anniversary-Edition (Version 1607, Build 10.0.14393) eingeführt.</span><span class="sxs-lookup"><span data-stu-id="b91e1-114">UWP app extensions were introduced in the Windows 10 Anniversary edition (version 1607, build 10.0.14393).</span></span>

<span data-ttu-id="b91e1-115">UWP-App-Erweiterungen sind UWP-Apps mit einer Erweiterungsdeklaration, die ihnen ermöglicht, Inhalte und Bereitstellungsereignisse mit einer Host-App zu teilen.</span><span class="sxs-lookup"><span data-stu-id="b91e1-115">UWP app extensions are UWP apps that have an extension declaration that allows them to share content and deployment events with a host app.</span></span> <span data-ttu-id="b91e1-116">Eine App-Erweiterung stellt mehrere Erweiterungen bereit.</span><span class="sxs-lookup"><span data-stu-id="b91e1-116">An extension app can provide multiple extensions.</span></span>

<span data-ttu-id="b91e1-117">Da App-Erweiterungen UWP-Apps sind, sind sie auch voll funktionsfähige Apps, Host-Erweiterungen und bieten Erweiterungen für andere Apps an – ohne dabei separate App-Pakete zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="b91e1-117">Because app extensions are just UWP apps, they can also be fully functional apps, host extensions, and provide extensions to other apps--all without creating separate app packages.</span></span>

<span data-ttu-id="b91e1-118">Wenn Sie einen App-Erweiterungshost erstellen, bieten Sie die Möglichkeit, ein Ökosystem in Ihrer App zu entwickeln, in dem anderen Entwickler Ihre App auf für Sie möglicherweise unerwartet Weise oder mit unerwarteten Ressourcen verbessern können.</span><span class="sxs-lookup"><span data-stu-id="b91e1-118">When you create an app extension host, you create an opportunity to develop an ecosystem around your app in which other developers can enhance your app in ways that you may not have expected or had the resources for.</span></span> <span data-ttu-id="b91e1-119">Denken Sie an Erweiterungen für Microsoft Office, Visual Studio oder für Browser. Diese erstellen attraktivere Umgebungen für Apps, die die Funktionen übersteigen, die ursprünglich im Lieferumfang enthalten waren.</span><span class="sxs-lookup"><span data-stu-id="b91e1-119">Consider Microsoft Office extensions, Visual Studio extensions, browser extensions, etc. These create richer experiences for those apps that go beyond the functionality they shipped with.</span></span> <span data-ttu-id="b91e1-120">Erweiterungen können der App mehr Wert und eine längere Lebensdauer bieten.</span><span class="sxs-lookup"><span data-stu-id="b91e1-120">Extensions can add value and longevity to your app.</span></span>

**<span data-ttu-id="b91e1-121">Übersicht</span><span class="sxs-lookup"><span data-stu-id="b91e1-121">Overview</span></span>**

<span data-ttu-id="b91e1-122">Allgemein gesagt, muss zum Einrichten einer App-Erweiterungsbeziehung folgendes ausgeführt werden:</span><span class="sxs-lookup"><span data-stu-id="b91e1-122">At a high level, to set up an app extension relationship, we need to:</span></span>

1. <span data-ttu-id="b91e1-123">Die App wird als Erweiterungshost deklariert.</span><span class="sxs-lookup"><span data-stu-id="b91e1-123">Declare an app to be an extension host.</span></span>
2. <span data-ttu-id="b91e1-124">Die App wird als Erweiterung deklariert.</span><span class="sxs-lookup"><span data-stu-id="b91e1-124">Declare an app to be an extension.</span></span>
3. <span data-ttu-id="b91e1-125">Es wird entschieden, ob die Erweiterung als App-Dienst, Hintergrundaufgabe oder anderweitig implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="b91e1-125">Decide whether to implement the extension as an app service, background task, or some other way.</span></span>
4. <span data-ttu-id="b91e1-126">Es wird festgelegt, wie die Hosts und die Erweiterungen kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="b91e1-126">Define how the hosts and its extensions will communicate.</span></span>
5. <span data-ttu-id="b91e1-127">Verwenden Sie die [Windows.ApplicationModel.AppExtensions](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.AppExtensions)-API in der Host-App, um auf die Erweiterungen zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="b91e1-127">Use the [Windows.ApplicationModel.AppExtensions](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.AppExtensions) API in the host app to access the extensions.</span></span>

<span data-ttu-id="b91e1-128">Sehen wir uns diese Vorgehensweise durch Untersuchen des [Math Extension-Codebeispiels](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/MathExtensionSample.zip) an, das einen hypothetischen Rechner implementiert, für den Sie mithilfe der Erweiterungen neue Funktionen hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="b91e1-128">Let's see how this is done by examining the [Math Extension code sample](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/MathExtensionSample.zip) which implements a hypothetical calculator that you can add new functions to by using extensions.</span></span> <span data-ttu-id="b91e1-129">Laden Sie in Microsoft Visual Studio2017 **MathExtensionSample.sln** aus dem Codebeispiel.</span><span class="sxs-lookup"><span data-stu-id="b91e1-129">In Microsoft Visual Studio 2017, load **MathExtensionSample.sln** from the code sample.</span></span>

![Math Extension-Codebeispiel](images/mathextensionhost-calctab.png)

## <a name="declare-an-app-to-be-an-extension-host"></a><span data-ttu-id="b91e1-131">Deklarieren einer App als Erweiterungshost</span><span class="sxs-lookup"><span data-stu-id="b91e1-131">Declare an app to be an extension host</span></span>

<span data-ttu-id="b91e1-132">Eine App identifiziert sich selbst durch das Deklarieren des `<AppExtensionHost>`-Elements in der Datei "Package.appxmanifest" als App-Erweiterungshost.</span><span class="sxs-lookup"><span data-stu-id="b91e1-132">An app identifies itself as an app extension host by declaring the `<AppExtensionHost>` element in its Package.appxmanifest file.</span></span> <span data-ttu-id="b91e1-133">Weitere Informationen finden Sie in der **Package.appxmanifest**-Datei im **MathExtensionHost**-Projekts, um zu sehen wie es funktioniert.</span><span class="sxs-lookup"><span data-stu-id="b91e1-133">See the **Package.appxmanifest** file in the **MathExtensionHost** project to see how this is done.</span></span>

_<span data-ttu-id="b91e1-134">"Package.appxmanifest" im „MathExtensionHost”-Projekt</span><span class="sxs-lookup"><span data-stu-id="b91e1-134">Package.appxmanifest in the MathExtensionHost project</span></span>_
```xml
<Package
  ...
  xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"
  IgnorableNamespaces="uap uap3 mp">
  ...
    <Applications>
      <Application Id="App" ... >
        ...
        <Extensions>
            <uap3:Extension Category="windows.appExtensionHost">
                <uap3:AppExtensionHost>
                  <uap3:Name>microsoft.com.MathExt</uap3:Name>
                </uap3:AppExtensionHost>
          </uap3:Extension>
        </Extensions>
      </Application>
    </Applications>
    ...
</Package>
```

<span data-ttu-id="b91e1-135">Beachten Sie `xmlns:uap3="http://..."` und `uap3` in `IgnorableNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="b91e1-135">Notice the `xmlns:uap3="http://..."` and the presence of `uap3` in `IgnorableNamespaces`.</span></span> <span data-ttu-id="b91e1-136">Diese sind erforderlich, da wir den uap3-Namespace verwenden.</span><span class="sxs-lookup"><span data-stu-id="b91e1-136">These are necessary because we are using the uap3 namespace.</span></span>

`<uap3:Extension Category="windows.appExtensionHost">` <span data-ttu-id="b91e1-137">identifiziert diese App als Erweiterungshost.</span><span class="sxs-lookup"><span data-stu-id="b91e1-137">identifies this app as an extension host.</span></span>

<span data-ttu-id="b91e1-138">Das Element **Name** im `<uap3:AppExtensionHost>` ist der _Erweiterungsvertrags_name.</span><span class="sxs-lookup"><span data-stu-id="b91e1-138">The **Name** element in `<uap3:AppExtensionHost>` is the _extension contract_ name.</span></span> <span data-ttu-id="b91e1-139">Wenn eine Erweiterung den gleichen Erweiterungsvertragsnamen angibt, kann der Host diese finden.</span><span class="sxs-lookup"><span data-stu-id="b91e1-139">When an extension specifies the same extension contract name, the host will be able to find it.</span></span> <span data-ttu-id="b91e1-140">Üblicherweise empfehlen wir, den Namen der App oder den Namen des Herausgebers als Erweiterungsvertragsnamen zu verwenden, um potenzielle Konflikte mit anderen Erweiterungsvertragsnamen zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="b91e1-140">By convention, we recommend building the extension contract name using your app or publisher name to avoid potential collisions with other extension contract names.</span></span>

<span data-ttu-id="b91e1-141">Sie können mehrere Hosts und mehrere Erweiterungen in derselben App definieren.</span><span class="sxs-lookup"><span data-stu-id="b91e1-141">You can define multiple hosts and multiple extensions in the same app.</span></span> <span data-ttu-id="b91e1-142">In diesem Beispiel deklarieren wir einen Host.</span><span class="sxs-lookup"><span data-stu-id="b91e1-142">In this example, we declare one host.</span></span> <span data-ttu-id="b91e1-143">Die Erweiterung wird in einer anderen App definiert.</span><span class="sxs-lookup"><span data-stu-id="b91e1-143">The extension is defined in another app.</span></span>

## <a name="declare-an-app-to-be-an-extension"></a><span data-ttu-id="b91e1-144">Deklarieren einer App als Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b91e1-144">Declare an app to be an extension</span></span>

<span data-ttu-id="b91e1-145">Eine App identifiziert sich selbst durch das Deklarieren des `<uap3:AppExtension>`-Elements in der Datei **Package.appxmanifest** als App-Erweiterung.</span><span class="sxs-lookup"><span data-stu-id="b91e1-145">An app identifies itself as an app extension by declaring the `<uap3:AppExtension>` element in its **Package.appxmanifest** file.</span></span> <span data-ttu-id="b91e1-146">Öffnen Sie die **Package.appxmanifest**-Datei im **MathExtension**-Projekt, um zu sehen wie es funktioniert.</span><span class="sxs-lookup"><span data-stu-id="b91e1-146">Open the **Package.appxmanifest** file in the **MathExtension** project to see how this is done.</span></span>

_<span data-ttu-id="b91e1-147">"Package.appxmanifest" im „MathExtension”-Projekt:</span><span class="sxs-lookup"><span data-stu-id="b91e1-147">Package.appxmanifest in the MathExtension project:</span></span>_
```xml
<Package
  ...
  xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"
  IgnorableNamespaces="uap uap3 mp">
  ...
    <Applications>
      <Application Id="App" ... >
        ...
        <Extensions>
          ...
          <uap3:Extension Category="windows.appExtension">
            <uap3:AppExtension Name="Microsoft.com.MathExt"
                               Id="power"
                               DisplayName="x^y"
                               Description="Exponent"
                               PublicFolder="Public">
              <uap3:Properties>
                <Service>com.microsoft.powservice</Service>
              </uap3:Properties>
              </uap3:AppExtension>
          </uap3:Extension>
        </Extensions>
      </Application>
    </Applications>
    ...
</Package>
```

<span data-ttu-id="b91e1-148">Beachten Sie erneut die Zeile `xmlns:uap3="http://..."` und `uap3` in `IgnorableNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="b91e1-148">Again, notice the `xmlns:uap3="http://..."` line, and the presence of `uap3` in `IgnorableNamespaces`.</span></span> <span data-ttu-id="b91e1-149">Diese sind erforderlich, da wir den uap3-Namespace verwenden.</span><span class="sxs-lookup"><span data-stu-id="b91e1-149">These are necessary because we are using the uap3 namespace.</span></span>

`<uap3:Extension Category="windows.appExtension">` <span data-ttu-id="b91e1-150">identifiziert diese App als Erweiterung.</span><span class="sxs-lookup"><span data-stu-id="b91e1-150">identifies this app as an extension.</span></span>

<span data-ttu-id="b91e1-151">Die `<uap3:AppExtension>`-Attribute haben folgende Bedeutungen:</span><span class="sxs-lookup"><span data-stu-id="b91e1-151">The meaning of the `<uap3:AppExtension>` attributes are as follows:</span></span>

|<span data-ttu-id="b91e1-152">Attribut</span><span class="sxs-lookup"><span data-stu-id="b91e1-152">Attribute</span></span>|<span data-ttu-id="b91e1-153">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b91e1-153">Description</span></span>|<span data-ttu-id="b91e1-154">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="b91e1-154">Required</span></span>|
|---------|-----------|:------:|
|**<span data-ttu-id="b91e1-155">Name</span><span class="sxs-lookup"><span data-stu-id="b91e1-155">Name</span></span>**|<span data-ttu-id="b91e1-156">Dies ist der Erweiterungsvertragsname.</span><span class="sxs-lookup"><span data-stu-id="b91e1-156">This is the extension contract name.</span></span> <span data-ttu-id="b91e1-157">Wenn sie dem auf einem Host deklarierten **Namen** entspricht, kann dieser Host diese Erweiterung finden.</span><span class="sxs-lookup"><span data-stu-id="b91e1-157">When it matches the **Name** declared in a host, that host will be able to find this extension.</span></span>|<span data-ttu-id="b91e1-158">:heavy_check_mark:</span><span class="sxs-lookup"><span data-stu-id="b91e1-158">:heavy_check_mark:</span></span>|
|**<span data-ttu-id="b91e1-159">ID</span><span class="sxs-lookup"><span data-stu-id="b91e1-159">ID</span></span>**| <span data-ttu-id="b91e1-160">Identifiziert diese Erweiterung eindeutig.</span><span class="sxs-lookup"><span data-stu-id="b91e1-160">Uniquely identifies this extension.</span></span> <span data-ttu-id="b91e1-161">Da es möglicherweise mehrere Erweiterungen mit dem gleichen Erweiterungsvertragsnamen gibt (wie eine Paint-App, die mehrere Erweiterungen unterstützt), können Sie die ID verwenden, um sie auseinanderzuhalten.</span><span class="sxs-lookup"><span data-stu-id="b91e1-161">Because there can be multiple extensions that use the same extension contract name (imagine a paint app that supports several extensions), you can use the ID to tell them apart.</span></span> <span data-ttu-id="b91e1-162">App-Erweiterungshosts können die ID verwenden, um den Typ der Erweiterung zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="b91e1-162">App extension hosts can use the ID to infer something about the type of extension.</span></span> <span data-ttu-id="b91e1-163">Beispielsweise können Sie eine Erweiterung für den Desktop und eine weitere für Mobilgeräte haben, wobei die ID das Unterscheidungsmerkmal ist.</span><span class="sxs-lookup"><span data-stu-id="b91e1-163">For example, you could have one Extension designed for desktop and another for mobile, with the ID being the differentiator.</span></span> <span data-ttu-id="b91e1-164">Sie können ebenfalls dafür das Element **Eigenschaften** verwenden.</span><span class="sxs-lookup"><span data-stu-id="b91e1-164">You could also use the **Properties** element, discussed below, for that.</span></span>|<span data-ttu-id="b91e1-165">:heavy_check_mark:</span><span class="sxs-lookup"><span data-stu-id="b91e1-165">:heavy_check_mark:</span></span>|
|**<span data-ttu-id="b91e1-166">DisplayName</span><span class="sxs-lookup"><span data-stu-id="b91e1-166">DisplayName</span></span>**| <span data-ttu-id="b91e1-167">Kann von der Host-App verwendet werden, um die Erweiterung für den Benutzer zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="b91e1-167">Can be used from your host app to identify the extension to the user.</span></span> <span data-ttu-id="b91e1-168">Ist abfragbar vom und verwendet das [Neue Ressourcenverwaltungssystem](https://docs.microsoft.com/windows/uwp/app-resources/using-mrt-for-converted-desktop-apps-and-games) (`ms-resource:TokenName`) für die Lokalisierung.</span><span class="sxs-lookup"><span data-stu-id="b91e1-168">It is queryable from, and can use, the [new resource management system](https://docs.microsoft.com/windows/uwp/app-resources/using-mrt-for-converted-desktop-apps-and-games) (`ms-resource:TokenName`) for localization.</span></span> <span data-ttu-id="b91e1-169">Der lokalisierte Inhalt wird vom App-Erweiterungspaket und nicht von der Host-App geladen.</span><span class="sxs-lookup"><span data-stu-id="b91e1-169">The localized content is loaded from the app extension package, not the host app.</span></span> | |
|**<span data-ttu-id="b91e1-170">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b91e1-170">Description</span></span>** | <span data-ttu-id="b91e1-171">Kann von der Host-App verwendet werden, um die Erweiterung für den Benutzer zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="b91e1-171">Can be used from your host app to describe the extension to the user.</span></span> <span data-ttu-id="b91e1-172">Ist abfragbar vom und verwendet das [Neue Ressourcenverwaltungssystem](https://docs.microsoft.com/windows/uwp/app-resources/using-mrt-for-converted-desktop-apps-and-games) (`ms-resource:TokenName`) für die Lokalisierung.</span><span class="sxs-lookup"><span data-stu-id="b91e1-172">It is queryable from, and can use, the [new resource management system](https://docs.microsoft.com/windows/uwp/app-resources/using-mrt-for-converted-desktop-apps-and-games) (`ms-resource:TokenName`) for localization.</span></span> <span data-ttu-id="b91e1-173">Der lokalisierte Inhalt wird vom App-Erweiterungspaket und nicht von der Host-App geladen.</span><span class="sxs-lookup"><span data-stu-id="b91e1-173">The localized content is loaded from the app extension package, not the host app.</span></span> | |
|**<span data-ttu-id="b91e1-174">PublicFolder</span><span class="sxs-lookup"><span data-stu-id="b91e1-174">PublicFolder</span></span>**|<span data-ttu-id="b91e1-175">Der Name eines Ordners, relativ zum Stammverzeichnis des Pakets, in dem Sie Inhalte mit dem Erweiterungshost teilen können.</span><span class="sxs-lookup"><span data-stu-id="b91e1-175">The name of a folder, relative to the package root, where you can share content with the extension host.</span></span> <span data-ttu-id="b91e1-176">Üblicherweise ist der Name "Public", Sie können allerdings einen beliebigen Namen verwenden, der einem Ordner in der Erweiterung entspricht.</span><span class="sxs-lookup"><span data-stu-id="b91e1-176">By convention the name is "Public", but you can use any name that matches a folder in your extension.</span></span>|<span data-ttu-id="b91e1-177">:heavy_check_mark:</span><span class="sxs-lookup"><span data-stu-id="b91e1-177">:heavy_check_mark:</span></span>|
`<uap3:Properties>` <span data-ttu-id="b91e1-178">ist ein optionales Element, das benutzerdefinierte Metadaten enthält, die Hosts zur Laufzeit lesen können.</span><span class="sxs-lookup"><span data-stu-id="b91e1-178">is an optional element that contains custom metadata that hosts can read at runtime.</span></span> <span data-ttu-id="b91e1-179">Im Codebeispiel ist die Erweiterung als App-Dienst implementiert, damit der Host den Namen des App-Diensts abrufen kann und ihn damit aufrufen kann.</span><span class="sxs-lookup"><span data-stu-id="b91e1-179">In the code sample, the extension is implemented as an app service so host needs a way to get the name of that app service so it can call it.</span></span> <span data-ttu-id="b91e1-180">Der Name des App-Diensts ist im <Service>-Element definiert, das wir definiert haben (der Name spielt dabei keine Rolle).</span><span class="sxs-lookup"><span data-stu-id="b91e1-180">The name of the app service is defined in the <Service> element, which we defined (we could have called it anything we wanted).</span></span> <span data-ttu-id="b91e1-181">Der Host im Codebeispiel sucht zur Laufzeit nach dieser Eigenschaft, um den Namen des App-Diensts zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="b91e1-181">The host in the code sample looks for this property at runtime to learn the name of the app service.</span></span>

## <a name="decide-how-you-will-implement-the-extension"></a><span data-ttu-id="b91e1-182">Entscheiden Sie, wie Sie die Erweiterung implementiert möchten.</span><span class="sxs-lookup"><span data-stu-id="b91e1-182">Decide how you will implement the extension.</span></span>

<span data-ttu-id="b91e1-183">In [Build 2016-Sitzung zu App-Erweiterungen](https://channel9.msdn.com/Events/Build/2016/B808) wird veranschaulicht, wie der öffentliche Ordner verwendet wird, der zwischen dem Host und den Erweiterungen freigegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="b91e1-183">The [Build 2016 session about app extensions](https://channel9.msdn.com/Events/Build/2016/B808) demonstrates how to use the public folder that is shared between the host and the extensions.</span></span> <span data-ttu-id="b91e1-184">In diesem Beispiel wird die Erweiterung von einer Javascript-Datei implementiert, die im öffentlichen Ordner gespeichert ist, der vom Host aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="b91e1-184">In that example, the extension is implemented by a Javascript file that is stored in the public folder, which the host invokes.</span></span> <span data-ttu-id="b91e1-185">Diese Methode hat den Vorteil, leichter zu sein und erfordert keine Kompilierung. Sie unterstützt eventuell das Erstellen der Standardstartseite, die Anweisungen für die Erweiterung und einen Link zur Microsoft Store-Seite der Host-App bietet.</span><span class="sxs-lookup"><span data-stu-id="b91e1-185">That approach has the advantage of being lightweight, does not require compilation, and can support making the default landing page that provides instructions for the extension and a link to the host app's Microsoft Store page.</span></span> <span data-ttu-id="b91e1-186">Weitere Details finden Sie im [Build 2016-App-Erweiterung – Codebeispiel](https://github.com/Microsoft/App-Extensibility-Sample).</span><span class="sxs-lookup"><span data-stu-id="b91e1-186">See the [Build 2016 app extension code sample](https://github.com/Microsoft/App-Extensibility-Sample) for details.</span></span> <span data-ttu-id="b91e1-187">Genauer gesagt finden Sie die Informationen im **InvertImageExtension**-Projekt und `InvokeLoad()` in ExtensionManager.cs im **ExtensibilitySample**-Projekt.</span><span class="sxs-lookup"><span data-stu-id="b91e1-187">Specifically, see the **InvertImageExtension** project and `InvokeLoad()` in ExtensionManager.cs in the **ExtensibilitySample** project.</span></span>

<span data-ttu-id="b91e1-188">In diesem Beispiel wird ein App-Dienst verwendet, um die Erweiterung zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="b91e1-188">In this example, we'll use an app service to implement the extension.</span></span> <span data-ttu-id="b91e1-189">App-Dienste bieten folgende Vorteile:</span><span class="sxs-lookup"><span data-stu-id="b91e1-189">App services have the following advantages:</span></span>

- <span data-ttu-id="b91e1-190">Wenn die Erweiterung abstürzt, wirkt sich dies nicht auf die Host-App aus, da die Host-App in einem eigenen Prozess ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b91e1-190">If the extension crashes, it won't take down the host app because the host app runs in its own process.</span></span>
- <span data-ttu-id="b91e1-191">Sie können die Sprache Ihrer Wahl verwenden, um den Dienst zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="b91e1-191">You can use the language of your choice to implement the service.</span></span> <span data-ttu-id="b91e1-192">Es muss nicht die gleiche Sprache sein, die zum Implementieren der Host-App verwendet wurde.</span><span class="sxs-lookup"><span data-stu-id="b91e1-192">It doesn't have to match language used to implement the host app.</span></span>
- <span data-ttu-id="b91e1-193">Der App-Dienst hat Zugriff auf seinen eigenen App-Container – der unterschiedliche Funktionen als der Host haben kann.</span><span class="sxs-lookup"><span data-stu-id="b91e1-193">The app service has access to its own app container--which may have different capabilities than the host has.</span></span>
- <span data-ttu-id="b91e1-194">Zwischen den Daten im Dienst und der Host-App besteht eine Isolierung.</span><span class="sxs-lookup"><span data-stu-id="b91e1-194">There is isolation between data in service and the host app.</span></span>

### <a name="host-app-service-code"></a><span data-ttu-id="b91e1-195">Host-App-Dienstcode</span><span class="sxs-lookup"><span data-stu-id="b91e1-195">Host app service code</span></span>

<span data-ttu-id="b91e1-196">Hier ist der Hostcode, der den App-Dienst der Erweiterung aufruft:</span><span class="sxs-lookup"><span data-stu-id="b91e1-196">Here is the host code that invokes the extension's app service:</span></span>

_<span data-ttu-id="b91e1-197">ExtensionManager.cs im MathExtensionHost-Projekt</span><span class="sxs-lookup"><span data-stu-id="b91e1-197">ExtensionManager.cs in the MathExtensionHost project</span></span>_
```cs
public async Task<double> Invoke(ValueSet message)
{
    if (Loaded)
    {
        try
        {
            // make the app service call
            using (var connection = new AppServiceConnection())
            {
                // service name is defined in appxmanifest properties
                connection.AppServiceName = _serviceName;
                // package Family Name is provided by the extension
                connection.PackageFamilyName = AppExtension.Package.Id.FamilyName;

                // open the app service connection
                AppServiceConnectionStatus status = await connection.OpenAsync();
                if (status != AppServiceConnectionStatus.Success)
                {
                    Debug.WriteLine("Failed App Service Connection");
                }
                else
                {
                    // Call the app service
                    AppServiceResponse response = await connection.SendMessageAsync(message);
                    if (response.Status == AppServiceResponseStatus.Success)
                    {
                        ValueSet answer = response.Message as ValueSet;
                        if (answer.ContainsKey("Result")) // When our app service returns "Result", it means it succeeded
                        {
                            return (double)answer["Result"];
                        }
                    }
                }
            }
        }
        catch (Exception)
        {
             Debug.WriteLine("Calling the App Service failed");
        }
    }
    return double.NaN; // indicates an error from the app service
}
```

<span data-ttu-id="b91e1-198">Dies ist der übliche Code zum Aufrufen eines App-Diensts.</span><span class="sxs-lookup"><span data-stu-id="b91e1-198">This is typical code for invoking an app service.</span></span> <span data-ttu-id="b91e1-199">Weitere Informationen zum Implementieren und Aufrufen eines App-Diensts finden Sie unter [Erstellen und Nutzen eines App-Diensts](how-to-create-and-consume-an-app-service.md).</span><span class="sxs-lookup"><span data-stu-id="b91e1-199">For details on how to implement and call an app service, see [How to create and consume an app service](how-to-create-and-consume-an-app-service.md).</span></span>

<span data-ttu-id="b91e1-200">Beachten Sie, wie der Name des aufzurufenden App-Diensts bestimmt wird.</span><span class="sxs-lookup"><span data-stu-id="b91e1-200">One thing to note is how the name of the app service to call is determined.</span></span> <span data-ttu-id="b91e1-201">Da der Host keine Informationen über die Implementierung der Erweiterung besitzt, muss die Erweiterung den Namen des App-Diensts angeben.</span><span class="sxs-lookup"><span data-stu-id="b91e1-201">Because the host doesn't have information about the implementation of the extension, the extension needs to provide the name of its app service.</span></span> <span data-ttu-id="b91e1-202">Im Codebeispiel deklariert die Erweiterung den Namen des App-Diensts in ihrer Datei im `<uap3:Properties>`-Element:</span><span class="sxs-lookup"><span data-stu-id="b91e1-202">In the code sample, the extension declares the name of the app service in its  file in the `<uap3:Properties>` element:</span></span>

_<span data-ttu-id="b91e1-203">"Package.appxmanifest" im „MathExtension”-Projekt</span><span class="sxs-lookup"><span data-stu-id="b91e1-203">Package.appxmanifest in the MathExtension project</span></span>_
```xml
    ...
    <uap3:Extension Category="windows.appExtension">
      <uap3:AppExtension ...>
        <uap3:Properties>
          <Service>com.microsoft.powservice</Service>
        </uap3:Properties>
        </uap3:AppExtension>
    </uap3:Extension>
```

<span data-ttu-id="b91e1-204">Definieren Sie Ihren eigenen XML-Code im `<uap3:Properties>`-Element.</span><span class="sxs-lookup"><span data-stu-id="b91e1-204">You can define your own XML in the `<uap3:Properties>` element.</span></span> <span data-ttu-id="b91e1-205">In diesem Fall definieren wir den Namen des App-Diensts, damit der Host diesen beim Aufruf der Erweiterung verwendet.</span><span class="sxs-lookup"><span data-stu-id="b91e1-205">In this case, we define the name of the app service so that the host can it when it invokes the extension.</span></span>

<span data-ttu-id="b91e1-206">Wenn der Host eine Erweiterung lädt, extrahiert ein solcher Code den Namen des Diensts aus den Eigenschaften, die in der Erweiterung "Package.appxmanifest" definiert wurden:</span><span class="sxs-lookup"><span data-stu-id="b91e1-206">When the host loads an extension, code like this extracts the name of the service from the properties defined in the extension's Package.appxmanifest:</span></span>

_`Update()` <span data-ttu-id="b91e1-207">in ExtensionManager.cs im MathExtensionHost-Projekt</span><span class="sxs-lookup"><span data-stu-id="b91e1-207">in ExtensionManager.cs, in the MathExtensionHost project</span></span>_
```cs
...
var properties = await ext.GetExtensionPropertiesAsync() as PropertySet;

...
#region Update Properties
// update app service information
_serviceName = null;
if (_properties != null)
{
   if (_properties.ContainsKey("Service"))
   {
       PropertySet serviceProperty = _properties["Service"] as PropertySet;
       this._serviceName = serviceProperty["#text"].ToString();
   }
}
#endregion
```

<span data-ttu-id="b91e1-208">Dank dem Namen des App-Diensts, der in `_serviceName` gespeichert ist, kann der Host diesen zum Aufrufen des App-Diensts verwenden.</span><span class="sxs-lookup"><span data-stu-id="b91e1-208">With the name of the app service stored in `_serviceName`, the host is able to use it to invoke the app service.</span></span>

<span data-ttu-id="b91e1-209">Das Aufrufen von App-Diensten erfordert auch den Familiennamen des Pakets, das den App-Dienst enthält.</span><span class="sxs-lookup"><span data-stu-id="b91e1-209">Calling an app service also requires the family name of the package that contains the app service.</span></span> <span data-ttu-id="b91e1-210">Glücklicherweise liefert die API der App-Erweiterung diese Informationen, die in folgender Zeile abgerufen wird:</span><span class="sxs-lookup"><span data-stu-id="b91e1-210">Fortunately, the app extension API provides this information which is obtained in the line:</span></span> `connection.PackageFamilyName = AppExtension.Package.Id.FamilyName;`

### <a name="define-how-the-host-and-the-extension-will-communicate"></a><span data-ttu-id="b91e1-211">Festlegen, wie der Host und die Erweiterung kommunizieren</span><span class="sxs-lookup"><span data-stu-id="b91e1-211">Define how the host and the extension will communicate</span></span>

<span data-ttu-id="b91e1-212">App-Dienste verwenden [ValueSet](https://docs.microsoft.com/uwp/api/windows.foundation.collections.valueset) zum Austauschen von Informationen.</span><span class="sxs-lookup"><span data-stu-id="b91e1-212">App services use a [ValueSet](https://docs.microsoft.com/uwp/api/windows.foundation.collections.valueset) to exchange information.</span></span> <span data-ttu-id="b91e1-213">Als Autor des Hosts müssen Sie ein Protokoll für die Kommunikation mit Erweiterungen anbieten, das flexibel ist.</span><span class="sxs-lookup"><span data-stu-id="b91e1-213">As the author of the host, you need to come up with a protocol for communicating with extensions that is flexible.</span></span> <span data-ttu-id="b91e1-214">Im Codebeispiel bedeutet dies, Erweiterungen zu berücksichtigen, die in Zukunft 1, 2 oder mehr Argumente annehmen können.</span><span class="sxs-lookup"><span data-stu-id="b91e1-214">In the code sample, that means accounting for extensions that may take 1, 2, or more arguments in the future.</span></span>

<span data-ttu-id="b91e1-215">In diesem Beispiel ist das Protokoll für die Argumente ein **ValueSet**, das die Schlüssel-Wert-Paare mit dem Namen "Argument" und der Anzahl der Argumente enthält, z.B. `Arg1` und `Arg2`.</span><span class="sxs-lookup"><span data-stu-id="b91e1-215">For this example, the protocol for the arguments is a **ValueSet** containing the key value pairs named 'Arg' + the argument number, e.g. `Arg1` and `Arg2`.</span></span> <span data-ttu-id="b91e1-216">Der Host übergibt alle Argumente im **ValueSet**, und die Erweiterung verwendet diejenigen, die es benötigt.</span><span class="sxs-lookup"><span data-stu-id="b91e1-216">The host passes all of the arguments in the **ValueSet**, and the extension makes use of the ones that it needs.</span></span> <span data-ttu-id="b91e1-217">Wenn die Erweiterung das Ergebnis berechnen kann, erwarte der Host, dass das on der Erweiterung zurückgegebene **ValueSet** einen Schlüssel namens `Result` mit dem Wert der Berechnung enthält.</span><span class="sxs-lookup"><span data-stu-id="b91e1-217">If the extension is able to calculate a result, then the host expects the **ValueSet** returned from the extension to have a key named `Result` that contains the value of the calculation.</span></span> <span data-ttu-id="b91e1-218">Wenn dieser Schlüssel nicht vorhanden ist, geht der Host davon aus, dass die Erweiterung die Berechnung nicht abschließen konnte.</span><span class="sxs-lookup"><span data-stu-id="b91e1-218">If that key is not present, the host assumes that the extension couldn't complete the calculation.</span></span>

### <a name="extension-app-service-code"></a><span data-ttu-id="b91e1-219">App-Dienstcode der Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b91e1-219">Extension app service code</span></span>

<span data-ttu-id="b91e1-220">Im Codebeispiel wird der App-Dienst der Erweiterung nicht als Hintergrundaufgabe implementiert.</span><span class="sxs-lookup"><span data-stu-id="b91e1-220">In the code sample, the extension's app service is not implemented as a background task.</span></span> <span data-ttu-id="b91e1-221">Stattdessen wird das einzelne Proc App-Service-Modell verwendet, in dem der App-Dienst im gleichen Prozess wie die Erweiterungs-App ausgeführt wird, die ihn hostet.</span><span class="sxs-lookup"><span data-stu-id="b91e1-221">Instead, it uses the single proc app service model in which the app service runs in the same process as the extension app that hosts it.</span></span> <span data-ttu-id="b91e1-222">Dieser Prozess unterscheidet sich immer noch von der Host-App und bietet die Vorteile einer Trennung der Prozesse, während durch das Vermeiden prozessübergreifender Kommunikation zwischen dem Erweiterungs- und dem Hintergrundprozess, der den App-Dienst implementiert, Leistungsvorteile entstehen.</span><span class="sxs-lookup"><span data-stu-id="b91e1-222">This is still a different process from the host app, providing the benefits of process separation, while gaining some performance benefits by avoiding cross-process communication between the extension process and the background process that implements the app service.</span></span> <span data-ttu-id="b91e1-223">Unter [Umwandeln eines App-Diensts für die Ausführung im gleichen Prozess wie die Host-App](convert-app-service-in-process.md) sehen Sie den Unterschied zwischen einem App-Dienst, der als Hintergrundaufgabe anstatt in demselben Prozess ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b91e1-223">See [Convert an app service to run in the same process as its host app](convert-app-service-in-process.md) to see the difference between an app service that runs as a background task versus in the same process.</span></span>

<span data-ttu-id="b91e1-224">Das System stellt `OnBackgroundActivate()` bereit, wenn der App-Dienst aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="b91e1-224">The system makes to `OnBackgroundActivate()` when the app service is activated.</span></span> <span data-ttu-id="b91e1-225">Dieser Code übernimmt die Ereignishandler zum Behandeln des eigentlichen App-Dienstaufrufs, wenn dieser eingeht (`OnAppServiceRequestReceived()`), und geht mit Wartungsaufgaben-Ereignissen um, wie mit Verzögerungsobjekten für das Behandeln oder Schließen eines Ereignisses.</span><span class="sxs-lookup"><span data-stu-id="b91e1-225">That code sets up event handlers to handle the actual app service call when it comes (`OnAppServiceRequestReceived()`) as well as deal with housekeeping events such as getting a deferral object handling a cancel or closed event.</span></span>

_<span data-ttu-id="b91e1-226">App.xaml.cs im MathExtension-Projekt.</span><span class="sxs-lookup"><span data-stu-id="b91e1-226">App.xaml.cs in the MathExtension project.</span></span>_
```cs
protected override void OnBackgroundActivated(BackgroundActivatedEventArgs args)
{
    base.OnBackgroundActivated(args);

    if ( _appServiceInitialized == false ) // Only need to setup the handlers once
    {
        _appServiceInitialized = true;

        IBackgroundTaskInstance taskInstance = args.TaskInstance;
        taskInstance.Canceled += OnAppServicesCanceled;

        AppServiceTriggerDetails appService = taskInstance.TriggerDetails as AppServiceTriggerDetails;
        _appServiceDeferral = taskInstance.GetDeferral();
        _appServiceConnection = appService.AppServiceConnection;
        _appServiceConnection.RequestReceived += OnAppServiceRequestReceived;
        _appServiceConnection.ServiceClosed += AppServiceConnection_ServiceClosed;
    }
}
```

<span data-ttu-id="b91e1-227">Der Code, der die Arbeit der Erweiterung durchführt befindet sich in `OnAppServiceRequestReceived()`.</span><span class="sxs-lookup"><span data-stu-id="b91e1-227">The code that does the work of the extension is in `OnAppServiceRequestReceived()`.</span></span> <span data-ttu-id="b91e1-228">Diese Funktion wird aufgerufen, wenn der App-Dienst zum Durchführen einer Berechnung aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="b91e1-228">This function is called when the app service is invoked to perform a calculation.</span></span> <span data-ttu-id="b91e1-229">Sie extrahiert die erforderlichen Werte aus dem **ValueSet**.</span><span class="sxs-lookup"><span data-stu-id="b91e1-229">It extracts the values it needs from the **ValueSet**.</span></span> <span data-ttu-id="b91e1-230">Wenn die Berechnung durchgeführt werden kann, wird das Ergebnis unter einem Schlüssel mit dem Namen **Ergebnis**im **ValueSet** an den Host zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="b91e1-230">If it can do the calculation, it puts the result, under a key named **Result**, in the **ValueSet** that is returned to the host.</span></span> <span data-ttu-id="b91e1-231">Denken Sie daran, dass entsprechend der im Protokoll definierten Kommunikation zwischen diesem Host und seinen Erweiterungen das Vorhandensein eines **Ergebnis**-Schlüssels den Erfolg oder Misserfolg angibt.</span><span class="sxs-lookup"><span data-stu-id="b91e1-231">Recall that according to the protocol defined for how this host and its extensions will communicate, the presence of a **Result** key will indicate success; otherwise failure.</span></span>

_<span data-ttu-id="b91e1-232">App.xaml.cs im MathExtension-Projekt</span><span class="sxs-lookup"><span data-stu-id="b91e1-232">App.xaml.cs in the MathExtension project.</span></span>_
```cs
private async void OnAppServiceRequestReceived(AppServiceConnection sender, AppServiceRequestReceivedEventArgs args)
{
    // Get a deferral because we use an awaitable API below (SendResponseAsync()) to respond to the message
    // and we don't want this call to get cancelled while we are waiting.
    AppServiceDeferral messageDeferral = args.GetDeferral();
    ValueSet message = args.Request.Message;
    ValueSet returnMessage = new ValueSet();

    double? arg1 = Convert.ToDouble(message["arg1"]);
    double? arg2 = Convert.ToDouble(message["arg2"]);
    if (arg1.HasValue && arg2.HasValue)
    {
        returnMessage.Add("Result", Math.Pow(arg1.Value, arg2.Value)); // For this sample, the presence of a "Result" key will mean the call succeeded
    }

    await args.Request.SendResponseAsync(returnMessage);
    messageDeferral.Complete();
}
```

## <a name="manage-extensions"></a><span data-ttu-id="b91e1-233">Verwalten von Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="b91e1-233">Manage extensions</span></span>

<span data-ttu-id="b91e1-234">Nachdem wir nun gesehen haben, wie die Beziehung zwischen einem Host und den dazugehörigen Erweiterungen implementier wird, wird als Nächstes beschrieben, wie der Host auf dem System installierte Erweiterungen findet, darauf reagiert und wie Pakete mit Erweiterungen entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="b91e1-234">Now that we've seen how to implement the relationship between a host and its extensions, let's see how a host finds  extensions installed on the system and reacts to the addition and removal of packages containing extensions.</span></span>

<span data-ttu-id="b91e1-235">Im Microsoft Store werden Erweiterungen als Pakete angeboten.</span><span class="sxs-lookup"><span data-stu-id="b91e1-235">The Microsoft Store delivers extensions as packages.</span></span> <span data-ttu-id="b91e1-236">Der [AppExtensionCatalog](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appextensions.appextensioncatalog) sucht nach installierten Paketen, deren Erweiterungen dem Erweiterungsvertragsnamen des Hosts entsprechen und bietet Ereignisse, die ausgelöst werden, wenn ein relevantes App-Erweiterungspaket für den Host installiert oder entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="b91e1-236">The [AppExtensionCatalog](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appextensions.appextensioncatalog) finds installed packages that contain extensions matching the host's extension contract name, and supplies events that fire when an app extension package relevant to the host is installed or removed.</span></span>

<span data-ttu-id="b91e1-237">Im Codebeispiel umschließt die `ExtensionManager`-Klasse (unter **ExtensionManager.cs** im **MathExtensionHost**-Projekt definiert) die Logik des Ladens von Erweiterungen und der Reaktion auf die Installation und Deinstallation von Erweiterungspaketen.</span><span class="sxs-lookup"><span data-stu-id="b91e1-237">In the code sample, the `ExtensionManager` class (defined in **ExtensionManager.cs** in the **MathExtensionHost** project) wraps the logic for loading extensions and responding to extension package installs and uninstalls.</span></span>

<span data-ttu-id="b91e1-238">Der `ExtensionManager`-Konstruktor nutzt die `AppExtensionCatalog`, um die App-Erweiterungen auf dem System zu suchen, die den gleichen Erweiterungsvertragsnamen wie der Host haben:</span><span class="sxs-lookup"><span data-stu-id="b91e1-238">The `ExtensionManager` constructor uses the `AppExtensionCatalog` to find the app extensions on the system that have the same extension contract name as the host:</span></span>

_<span data-ttu-id="b91e1-239">ExtensionManager.cs im MathExtensionHost-Projekt.</span><span class="sxs-lookup"><span data-stu-id="b91e1-239">ExtensionManager.cs in the MathExtensionHost project.</span></span>_
```cs
public ExtensionManager(string extensionContractName)
{
   // catalog & contract
   ExtensionContractName = extensionContractName;
   _catalog = AppExtensionCatalog.Open(ExtensionContractName);
   ...
}
```

<span data-ttu-id="b91e1-240">Wenn ein Erweiterungspaket installiert ist, sammelt der `ExtensionManager` Informationen über die Erweiterungen im Paket, die den gleichen Erweiterungsvertragsnamen wie der Host haben.</span><span class="sxs-lookup"><span data-stu-id="b91e1-240">When an extension package is installed, the `ExtensionManager` gathers information about the extensions in the package that have the same extension contract name as the host.</span></span> <span data-ttu-id="b91e1-241">Eine Installation kann ein Update sein, wodurch möglicherweise die betroffenen Erweiterungsinformationen aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="b91e1-241">An install may represent an update in which case the affected extension's information is updated.</span></span> <span data-ttu-id="b91e1-242">Bei der Deinstallation eines Erweiterungspakets entfernt der `ExtensionManager` Informationen zu den betroffenen Erweiterungen, damit der Benutzer weiß, welche Erweiterungen nicht mehr verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="b91e1-242">When an extension package is uninstalled, the `ExtensionManager` removes information about the affected extensions so that the user knows which extensions are no longer available.</span></span>

<span data-ttu-id="b91e1-243">Die `Extension`-Klasse (im **ExtensionManager.cs** des **MathExtensionHost**-Projekts definiert) wurde für das Codebeispiel erstellt, um die ID, Beschreibung, das Logo und die App-spezifischen Informationen der Erweiterung zu beschreiben wie z.B., ob der Benutzer die Erweiterung aktiviert hat.</span><span class="sxs-lookup"><span data-stu-id="b91e1-243">The `Extension` class (defined in **ExtensionManager.cs** in the **MathExtensionHost** project) was created for the code sample to access an extension's ID, description, logo, and app specific information such as whether the user has enabled the extension.</span></span>

<span data-ttu-id="b91e1-244">Wenn die Erweiterung geladen wird (siehe `Load()` im **ExtensionManager.cs**), bedeutet dies, dass der Paketstatus in Ordnung ist und die ID, das Logo, die Beschreibung und öffentlichen Ordner erhalten wurden (die wir nicht in diesem Beispiel verwenden, hier wird nur gezeigt nur, wie Sie diese Informationen erhalten).</span><span class="sxs-lookup"><span data-stu-id="b91e1-244">To say that the extension is loaded (see `Load()` in **ExtensionManager.cs**) means that the package status is fine and that we've obtained its ID, logo, description, and public folder (which we don't use in this sample-its just to show how you get it).</span></span> <span data-ttu-id="b91e1-245">Das Erweiterungspaket selbst wird nicht geladen.</span><span class="sxs-lookup"><span data-stu-id="b91e1-245">The extension package itself isn't being loaded.</span></span>

<span data-ttu-id="b91e1-246">Das Konzept des Entladens dient dazu, die Erweiterungen zu überprüfen, die für den Benutzer nicht mehr angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b91e1-246">The concept of unloading is used for keeping track of which extensions should no longer be presented to the user.</span></span>

<span data-ttu-id="b91e1-247">Der `ExtensionManager` bietet eine Sammlung von `Extension`-Instanzen, damit die Erweiterungen, deren Namen, Beschreibungen und Logos Datenbindungen zur Benutzeroberfläche enthält.</span><span class="sxs-lookup"><span data-stu-id="b91e1-247">The `ExtensionManager` provides a collection `Extension` instances so that the extensions, their names, descriptions, and logos can be data bound to UI.</span></span> <span data-ttu-id="b91e1-248">Die Seite **ExtensionsTab** ist an diese Sammlung gebunden und bietet eine Benutzeroberfläche zum Aktivieren/Deaktivieren und Entfernen von Erweiterungen.</span><span class="sxs-lookup"><span data-stu-id="b91e1-248">The **ExtensionsTab** page binds to this collection and provides UI for enabling/disabling extensions as well as removing them.</span></span>

![Beispiel der Registerkarte "Erweiterungen" für eine Benutzeroberfläche](images/mathextensionhost-extensiontab.png)

 <span data-ttu-id="b91e1-250">Wenn eine Erweiterung entfernt wird, fordert das System den Benutzer auf, zu überprüfen, ob das Paket deinstalliert werden soll, das die Erweiterung enthält (und möglicherweise andere Erweiterungen).</span><span class="sxs-lookup"><span data-stu-id="b91e1-250">When an extension is removed, the system prompts the user to verify that they want to uninstall the package that contains the extension (and possibly contains other extensions).</span></span> <span data-ttu-id="b91e1-251">Wenn der Benutzer dies bestätigt, wird das Paket deinstalliert und der `ExtensionManager` entfernt die Erweiterungen aus dem deinstallierten Paket aus der Liste der Erweiterungen, die in der Host-App zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="b91e1-251">If the user agrees, the package is uninstalled and the `ExtensionManager` removes the extensions in the uninstalled package from the list of extensions available to the host app.</span></span>

 ![Deinstallieren der Benutzeroberfläche](images/mathextensionhost-uninstall.png)

## <a name="debugging-app-extensions-and-hosts"></a><span data-ttu-id="b91e1-253">Debuggen von App-Erweiterungen und Hosts</span><span class="sxs-lookup"><span data-stu-id="b91e1-253">Debugging app extensions and hosts</span></span>

<span data-ttu-id="b91e1-254">Oftmals sind der Erweiterungshost und die Erweiterung nicht Teil der gleichen Lösung.</span><span class="sxs-lookup"><span data-stu-id="b91e1-254">Often, the extension host and extension are not part of the same solution.</span></span> <span data-ttu-id="b91e1-255">In diesem Fall können Sie den Host und die Erweiterung folgendermaßen debuggen:</span><span class="sxs-lookup"><span data-stu-id="b91e1-255">In that case, to debug the host and the extension:</span></span>

1. <span data-ttu-id="b91e1-256">Laden Sie Ihr Hostprojekt in eine Instanz von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b91e1-256">Load your host project in one instance of Visual Studio.</span></span>
2. <span data-ttu-id="b91e1-257">Laden Sie die Erweiterung in eine andere Instanz von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b91e1-257">Load your extension in another instance of Visual Studio.</span></span>
3. <span data-ttu-id="b91e1-258">Starten Sie die Host-App im Debugger.</span><span class="sxs-lookup"><span data-stu-id="b91e1-258">Launch your host app in the debugger.</span></span>
4. <span data-ttu-id="b91e1-259">Starten Sie die Erweiterungs-App im Debugger.</span><span class="sxs-lookup"><span data-stu-id="b91e1-259">Launch the extension app in the debugger.</span></span> <span data-ttu-id="b91e1-260">(Wenn Sie die Erweiterung bereitstellen möchten anstatt sie zu debuggen, gehen Sie folgendermaßen vor, um das Installationsereignis des Host-Pakets zu testen: **Build &gt; Lösung bereitstellen**).</span><span class="sxs-lookup"><span data-stu-id="b91e1-260">(If you want to deploy the extension, rather than debug it, to test the host's package install event, do **Build &gt; Deploy Solution**, instead).</span></span>

<span data-ttu-id="b91e1-261">Sie können jetzt Haltepunkte auf dem Host und in der Erweiterung treffen.</span><span class="sxs-lookup"><span data-stu-id="b91e1-261">Now you will be able to hit breakpoints in the host and the extension.</span></span>
<span data-ttu-id="b91e1-262">Wenn Sie die Erweiterungs-App selbst debuggen, wird ein leeres Fenster für die App angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b91e1-262">If you start debugging the extension app itself, you will see a blank window for the app.</span></span> <span data-ttu-id="b91e1-263">Wenn kein leeres Fenster angezeigt werden sollen, können Sie die Debugeinstellungen für das Erweiterungsprojekt ändern, um die App nicht zu starten, sondern sie stattdessen beim Start zu debuggen (klicken Sie mit der rechten Maustaste auf das Erweiterungsprojekt **Eigenschaften** > **Debuggen** > wählen Sie **Eigenen Code zunächst nicht starten, sondern debuggen**). Sie müssen das Erweiterungsprojekt trotzdem debuggen (**F5**). Dies wartet allerdings so lange, bis der Host die Erweiterung aktiviert. Danach wird der Haltepunkt getroffen.</span><span class="sxs-lookup"><span data-stu-id="b91e1-263">If you don't want to see the blank window, you can change the debugging settings for the extension project to not launch the app but instead debug it when it starts (right-click the extension project, **Properties** > **Debug** > select **Do not launch, but debug my code when it starts**)  You'll still need to start debugging (**F5**) the extension project, but it will  wait until the host activates the extension and then your breakpoints in the extension will be hit.</span></span>

**<span data-ttu-id="b91e1-264">Debuggen des Codebeispiels</span><span class="sxs-lookup"><span data-stu-id="b91e1-264">Debug the code sample</span></span>**

<span data-ttu-id="b91e1-265">Im Codebeispiel befinden sich der Host und die Erweiterung in der gleichen Lösung.</span><span class="sxs-lookup"><span data-stu-id="b91e1-265">In the code sample, the host and the extension are in the same solution.</span></span> <span data-ttu-id="b91e1-266">So gehen Sie zum Debuggen vor:</span><span class="sxs-lookup"><span data-stu-id="b91e1-266">Do the following to debug:</span></span>

1. <span data-ttu-id="b91e1-267">Stellen Sie sicher, dass **MathExtensionHost** das Startprojekt ist (klicken Sie mit der rechten Maustaste auf das **MathExtensionHost**-Projekt und dann auf **Als Startprojekt festlegen**).</span><span class="sxs-lookup"><span data-stu-id="b91e1-267">Ensure that **MathExtensionHost** is the startup project (right-click the **MathExtensionHost** project, click **Set as StartUp project**).</span></span>
2. <span data-ttu-id="b91e1-268">Setzen Sie einen Haltepunkt auf `Invoke` im ExtensionManager.cs im **MathExtensionHost**-Projekt.</span><span class="sxs-lookup"><span data-stu-id="b91e1-268">Put a breakpoint on `Invoke` in ExtensionManager.cs, in the **MathExtensionHost** project.</span></span>
3. <span data-ttu-id="b91e1-269">Drücken Sie **F5**, um das **MathExtensionHost**-Projekt auszuführen.</span><span class="sxs-lookup"><span data-stu-id="b91e1-269">**F5** to run the **MathExtensionHost** project.</span></span>
4. <span data-ttu-id="b91e1-270">Setzen Sie einen Haltepunkt auf `OnAppServiceRequestReceived` in App.xaml.cs im **MathExtension**-Projekt.</span><span class="sxs-lookup"><span data-stu-id="b91e1-270">Put a breakpoint on `OnAppServiceRequestReceived` in App.xaml.cs in the **MathExtension** project.</span></span>
5. <span data-ttu-id="b91e1-271">Starten Sie mit dem Debuggen des **MathExtension**-Projekts (klicken Sie mit der rechten Maustaste auf das **MathExtension**-Projekt **Debuggen > Neue Instanz starten**). Dadurch wird es bereitgestellt und das Installationsereignis des Pakets auf dem Host ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="b91e1-271">Start debugging the **MathExtension** project (right-click the **MathExtension** project, **Debug > Start new instance**) which will deploy it and trigger the package install event in the host.</span></span>
6. <span data-ttu-id="b91e1-272">In der **MathExtensionHost**-App, wechseln Sie zur Seite **Berechnung**, und klicken Sie auf **x^y**, um die Erweiterung zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="b91e1-272">In the **MathExtensionHost** app, navigate to the **Calculation** page, and click **x^y** to activate the extension.</span></span> <span data-ttu-id="b91e1-273">Der `Invoke()`-Haltepunkt wird zuerst getroffen und Sie sehen, dass der App-Dienstaufruf der Erweiterungen durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b91e1-273">The `Invoke()` breakpoint is hit first and you can see the extensions app service call being made.</span></span> <span data-ttu-id="b91e1-274">Danach wird die `OnAppServiceRequestReceived()`-Methode in der Erweiterung erreicht, und Sie sehen, wie der App-Diensts das Ergebnis berechnet und zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="b91e1-274">Then the `OnAppServiceRequestReceived()` method in the extension is hit, and you can see the app service calculate the result and return it.</span></span>

**<span data-ttu-id="b91e1-275">Problembehandlung bei Erweiterungen, die als App-Dienst implementiert wurden</span><span class="sxs-lookup"><span data-stu-id="b91e1-275">Troubleshooting extensions implemented as an app service</span></span>**

<span data-ttu-id="b91e1-276">Wenn Ihre Erweiterungshost Probleme beim Herstellen einer Verbindung mit dem App-Dienst für die Erweiterung hat, stellen Sie sicher, dass das `<uap:AppService Name="...">`-Attribut Ihrer Eingabe des `<Service>`-Elements entspricht.</span><span class="sxs-lookup"><span data-stu-id="b91e1-276">If your extension host has trouble connecting to the app service for your extension, ensure that the `<uap:AppService Name="...">` attribute matches what you put in your `<Service>` element.</span></span> <span data-ttu-id="b91e1-277">Wenn diese nicht übereinstimmen, wird der Dienstname, den Ihre Erweiterung an den Host bereitgestellt nicht mit dem implementierten Namen des App-Dienstnamens übereinstimmen, und der Hosts kann Ihre Erweiterung nicht aktivieren.</span><span class="sxs-lookup"><span data-stu-id="b91e1-277">If they don't match, the service name that your extension provides the host won't match the app service name you implemented, and the host won't be able to activate your extension.</span></span>

_<span data-ttu-id="b91e1-278">Package.appxmanifest im MathExtension-Projekt:</span><span class="sxs-lookup"><span data-stu-id="b91e1-278">Package.appxmanifest in the MathExtension project:</span></span>_
```xml
<Extensions>
   <uap:Extension Category="windows.appService">
     <uap:AppService Name="com.microsoft.sqrtservice" />      <!-- This must match the contents of <Service>...</Service> -->
   </uap:Extension>
   <uap3:Extension Category="windows.appExtension">
     <uap3:AppExtension Name="Microsoft.com.MathExt" Id="sqrt" DisplayName="Sqrt(x)" Description="Square root" PublicFolder="Public">
       <uap3:Properties>
         <Service>com.microsoft.powservice</Service>   <!-- this must match <uap:AppService Name=...> -->
       </uap3:Properties>
     </uap3:AppExtension>
   </uap3:Extension>
</Extensions>   
```

## <a name="a-checklist-of-basic-scenarios-to-test"></a><span data-ttu-id="b91e1-279">Hier ist eine Prüfliste, um einfache Szenarien zu testen</span><span class="sxs-lookup"><span data-stu-id="b91e1-279">A checklist of basic scenarios to test</span></span>

<span data-ttu-id="b91e1-280">Wenn Sie nach der Entwicklung eines Erweiterungshosts diesen testen möchten, um zu sehen, wie gut die Erweiterungen unterstützt werden, finden Sie hier einige grundlegende Testszenarien:</span><span class="sxs-lookup"><span data-stu-id="b91e1-280">When you build an extension host and are ready to test how well it supports extensions, here are some basic scenarios to try:</span></span>

- <span data-ttu-id="b91e1-281">Führen Sie den Host aus, und stellen Sie dann eine Erweiterungs-App bereit</span><span class="sxs-lookup"><span data-stu-id="b91e1-281">Run the host and then deploy an extension app</span></span>  
    - <span data-ttu-id="b91e1-282">Übernimmt der Host neue Erweiterungen, die während der Ausführung auftreten?</span><span class="sxs-lookup"><span data-stu-id="b91e1-282">Does the host pick up new extensions that come along while its running?</span></span>  
- <span data-ttu-id="b91e1-283">Stellen Sie die Erweiterungs-App bereit und stellen Sie anschließend den Host bereit und führen Sie ihn aus</span><span class="sxs-lookup"><span data-stu-id="b91e1-283">Deploy the extension app and then deploy and run the host.</span></span>
    - <span data-ttu-id="b91e1-284">Übernimmt der Host bereits vorhandene Erweiterungen?</span><span class="sxs-lookup"><span data-stu-id="b91e1-284">Does the host pick up previously-existing extensions?</span></span>  
- <span data-ttu-id="b91e1-285">Führen Sie den Host aus, und entfernen Sie dann die Erweiterungs-App.</span><span class="sxs-lookup"><span data-stu-id="b91e1-285">Run the host and then remove extension app.</span></span>
    - <span data-ttu-id="b91e1-286">Erkennt der Host die Entfernung ordnungsgemäß?</span><span class="sxs-lookup"><span data-stu-id="b91e1-286">Does the host detect the removal correctly?</span></span>
- <span data-ttu-id="b91e1-287">Führen Sie den Host aus, und ersetzen Sie die Erweiterungs-App anschließend durch eine neuere Version.</span><span class="sxs-lookup"><span data-stu-id="b91e1-287">Run the host and then update the extension app to a newer version.</span></span>
    - <span data-ttu-id="b91e1-288">Übernimmt der Host die Änderung und entlädt die alten Versionen der Erweiterung ordnungsgemäß?</span><span class="sxs-lookup"><span data-stu-id="b91e1-288">Does the host pick up the change and unload the old versions of the extension properly?</span></span>  

**<span data-ttu-id="b91e1-289">Erweiterte Testszenarien:</span><span class="sxs-lookup"><span data-stu-id="b91e1-289">Advanced scenarios to test:</span></span>**

- <span data-ttu-id="b91e1-290">Führen Sie den Host aus, verschieben Sie die Erweiterungs-App auf Wechselmedien, entfernen Sie das Medium</span><span class="sxs-lookup"><span data-stu-id="b91e1-290">Run the host, move the extension app to removable media, remove the media</span></span>
    - <span data-ttu-id="b91e1-291">Erkennt der Host die Änderung des Paketstatus und deaktiviert die Erweiterungen?</span><span class="sxs-lookup"><span data-stu-id="b91e1-291">Does the host detect the change in package status and disable the extension?</span></span>
- <span data-ttu-id="b91e1-292">Führen Sie den Host aus, beschädigen Sie die Erweiterungs-App (machen Sie diese ungültig, ändern Sie die Signatur usw.)</span><span class="sxs-lookup"><span data-stu-id="b91e1-292">Run the host, then corrupt the extension app (make it invalid, signed differently, etc.)</span></span>
    - <span data-ttu-id="b91e1-293">Erkennt der Host die manipulierte Erweiterung und behandelt sie ordnungsgemäß?</span><span class="sxs-lookup"><span data-stu-id="b91e1-293">Does the host detect the tampered extension and handle it correctly?</span></span>
- <span data-ttu-id="b91e1-294">Führen Sie den Host aus, und stellen Sie dann eine Erweiterungs-App bereit, die ungültige Inhalte oder Eigenschaften hat</span><span class="sxs-lookup"><span data-stu-id="b91e1-294">Run the host, then deploy an extension app that has invalid content or properties</span></span>
    - <span data-ttu-id="b91e1-295">Erkennt der Host den ungültigen Inhalt und behandelt ihn ordnungsgemäß?</span><span class="sxs-lookup"><span data-stu-id="b91e1-295">Does the host detect invalid content and handle it correctly?</span></span>

## <a name="design-considerations"></a><span data-ttu-id="b91e1-296">Überlegungen zum Entwurf</span><span class="sxs-lookup"><span data-stu-id="b91e1-296">Design considerations</span></span>

- <span data-ttu-id="b91e1-297">Stellen Sie Benutzeroberflächen bereit, die dem Benutzer anzeigen, welche Erweiterungen zur Verfügung stehen, und ermöglichen Sie ihnen, diese zu aktivieren oder zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="b91e1-297">Provide UI that shows the user which extensions are available and allows them to enable/disable them.</span></span> <span data-ttu-id="b91e1-298">Sie können außerdem Glyphen für Erweiterungen hinzufügen, die nicht mehr verfügbar sind, wenn das Paket offline geschaltet wurde usw. hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b91e1-298">You might also consider adding glyphs for extensions that become unavailable because a package goes offline, etc.</span></span>
- <span data-ttu-id="b91e1-299">Geben Sie dem Benutzer an, wo die Erweiterungen erhalten werden können.</span><span class="sxs-lookup"><span data-stu-id="b91e1-299">Direct the user to where they can get extensions.</span></span> <span data-ttu-id="b91e1-300">Ihre Seite der Erweiterung kann möglicherweise eine Suchabfrage des Microsoft Store bereitstellen, die eine Liste der Erweiterungen anbietet, die mit Ihrer App verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="b91e1-300">Perhaps your extension page can provide a Microsoft Store search query that brings up a list of extensions that can be used with your app.</span></span>
- <span data-ttu-id="b91e1-301">Überlegen Sie, wie Sie den Benutzer über das Hinzufügen und Entfernen von Erweiterungen benachrichtigen.</span><span class="sxs-lookup"><span data-stu-id="b91e1-301">Consider how to notify the user of the addition and removal of extensions.</span></span> <span data-ttu-id="b91e1-302">Erstellen Sie eine Benachrichtigung, wenn eine neue Erweiterung installiert wird und fordern Sie den Benutzer auf, diese zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="b91e1-302">You might create a notification for when a new extension is installed and invite the user to enable it.</span></span> <span data-ttu-id="b91e1-303">Erweiterungen sollte standardmäßig deaktiviert werden, damit Benutzer die Kontrolle haben.</span><span class="sxs-lookup"><span data-stu-id="b91e1-303">Extensions should be disabled by default so that users are in control.</span></span>

## <a name="how-app-extensions-differ-from-optional-packages"></a><span data-ttu-id="b91e1-304">So unterscheiden sich App-Erweiterungen von optionalen Paketen</span><span class="sxs-lookup"><span data-stu-id="b91e1-304">How app extensions differ from optional packages</span></span>

<span data-ttu-id="b91e1-305">Der Hauptunterschied zwischen [optionalen Paketen](https://docs.microsoft.com/windows/uwp/packaging/optional-packages) und App-Erweiterungen ist ein offenes Ökosystem im Vergleich zu einem geschlossenen Ökosystem und abhängige Pakete im Vergleich zu unabhängigen Paketen.</span><span class="sxs-lookup"><span data-stu-id="b91e1-305">The key differentiator between [optional packages](https://docs.microsoft.com/windows/uwp/packaging/optional-packages) and app extensions are open ecosystem versus closed ecosystem, and dependent package versus independent package.</span></span>

<span data-ttu-id="b91e1-306">App-Erweiterungen sind Teil eines offenen Ökosystems.</span><span class="sxs-lookup"><span data-stu-id="b91e1-306">App extensions participate in an open ecosystem.</span></span> <span data-ttu-id="b91e1-307">Wenn Ihre App-Erweiterungen hosten kann, kann jeder Benutzer eine Erweiterung für den Host schreiben, solange er die Methode des Übergebens und Empfangens von Informationen aus der Erweiterung verwendet.</span><span class="sxs-lookup"><span data-stu-id="b91e1-307">If your app can host app extensions, anyone can write an extension for your host as long as they comply with your method of passing/receiving information from the extension.</span></span> <span data-ttu-id="b91e1-308">Dies unterscheidet sich von optionalen Paketen, die Teil eines geschlossenen Ökosystem sind. Dort entscheidet der Herausgeber, wer ein optionales Paket erstellen darf, das mit der App verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="b91e1-308">This differs from optional packages which participate in a closed ecosystem where the publisher decides who is allowed to make an optional package that can be used with the app.</span></span>

<span data-ttu-id="b91e1-309">App-Erweiterungen sind unabhängige Pakete und eigenständige Apps.</span><span class="sxs-lookup"><span data-stu-id="b91e1-309">App extensions are independent packages and can be standalone apps.</span></span> <span data-ttu-id="b91e1-310">Sie dürfen keine Abhängigkeit in puncto Bereitstellung auf einer anderen App besitzen.</span><span class="sxs-lookup"><span data-stu-id="b91e1-310">They cannot have a deployment dependency on another app.</span></span> <span data-ttu-id="b91e1-311">Bei optionalen Paketen ist das primäre Pakets erforderlich und diese können nicht ohne ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="b91e1-311">Optional packages require the primary package and cannot run without it.</span></span>

<span data-ttu-id="b91e1-312">Ein Erweiterungspaket für ein Spiel wäre ein guter Kandidat für ein optionales Paket, da es eng mit dem Spiel verbunden ist und nicht unabhängig auf dem Spiel ausgeführt werden kann. Erweiterungspakete sollten nicht von beliebigen Entwickler im Ökosystem erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="b91e1-312">An expansion pack for a game would be a good candidate for an optional package because it's tightly bound to the game, it can't run independently of the game, and you may not want expansion packs to be created by just any developer in the ecosystem.</span></span>

<span data-ttu-id="b91e1-313">Hätte das gleiche Spiel anpassbare UI-Add-Ons oder Designs, wäre eine App-Erweiterung eine gute Wahl, da die App, die die Erweiterung anbietet, eigenständig ausgeführt werden kann und alle Drittanbieter diese erstellen kann.</span><span class="sxs-lookup"><span data-stu-id="b91e1-313">If that same game had customizable UI add-ons or theming, then an app extension could be a good choice because the app providing the extension could run on its own, and any 3rd party could make them.</span></span>

## <a name="remarks"></a><span data-ttu-id="b91e1-314">Hinweise</span><span class="sxs-lookup"><span data-stu-id="b91e1-314">Remarks</span></span>

<span data-ttu-id="b91e1-315">Dieses Thema stellt eine Einführung zur App-Erweiterungen bereit.</span><span class="sxs-lookup"><span data-stu-id="b91e1-315">This topic provides an introduction to app extensions.</span></span> <span data-ttu-id="b91e1-316">Die wichtigsten Punkte sind die Erstellung des Hosts und das Markieren in der Datei "Package.appxmanifest", das Erstellen der Erweiterung und das Markieren als solche in der Datei "Package.appxmanifest", festzulegen, wie die Erweiterung implementiert wird (z.B. als App-Dienst, als Hintergrundaufgaben oder anderweitig), zu definieren, wie der Host mit den Erweiterungen kommunizieren soll, und das Verwenden der [AppExtensions API](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appextensions) für den Zugriff und das Verwalten der Erweiterungen.</span><span class="sxs-lookup"><span data-stu-id="b91e1-316">The key things to note are the creation of the host and marking it as such in its Package.appxmanifest file, creating the extension and marking it as such in its Package.appxmanifest file, determining how to implement the extension (such as an app service, background task, or other means), defining how the host will communicate with extensions, and using the [AppExtensions API](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appextensions) to access and manage extensions.</span></span>

## <a name="related-topics"></a><span data-ttu-id="b91e1-317">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="b91e1-317">Related topics</span></span>

* [<span data-ttu-id="b91e1-318">Build 2016-Sitzung zu App-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="b91e1-318">Build 2016 session about app extensions</span></span>](https://channel9.msdn.com/Events/Build/2016/B808)
* [<span data-ttu-id="b91e1-319">Build 2016 App-Erweiterung – Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="b91e1-319">Build 2016 app extension code sample</span></span>](https://github.com/Microsoft/App-Extensibility-Sample)
* [<span data-ttu-id="b91e1-320">Unterstützen Ihrer App mit Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="b91e1-320">Support your app with background tasks</span></span>](support-your-app-with-background-tasks.md)
* <span data-ttu-id="b91e1-321">[Erstellen und Nutzen eines App-Diensts](how-to-create-and-consume-an-app-service.md).</span><span class="sxs-lookup"><span data-stu-id="b91e1-321">[How to create and consume an app service](how-to-create-and-consume-an-app-service.md).</span></span>
* [<span data-ttu-id="b91e1-322">AppExtensions-Namespace</span><span class="sxs-lookup"><span data-stu-id="b91e1-322">AppExtensions namespace</span></span>](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appextensions)
* [<span data-ttu-id="b91e1-323">Bauen Sie Ihre App mit Diensten, Erweiterungen und Paketen aus</span><span class="sxs-lookup"><span data-stu-id="b91e1-323">Extend your app with services, extensions, and packages</span></span>](https://docs.microsoft.com/windows/uwp/launch-resume/extend-your-app-with-services-extensions-packages)
