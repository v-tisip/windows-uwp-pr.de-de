---
author: laurenhughes
title: Paketerstellung mit dem Verpackungslayout
description: Das Verpackungslayout ist ein Dokument, das die Verpackungsstruktur der App beschreibt. Es gibt die Bündel einer App („primär” und „optional”), die Pakete in den Bündeln sowie die Dateien in den Paketen an.
ms.author: lahugh
ms.date: 04/30/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, verpackung, paketlayout, bestandspaket
ms.localizationpriority: medium
ms.openlocfilehash: 3f8cbb3989b58b726336b4bd757902bd9ea3f8c0
ms.sourcegitcommit: d10fb9eb5f75f2d10e1c543a177402b50fe4019e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "4574332"
---
# <a name="package-creation-with-the-packaging-layout"></a><span data-ttu-id="17ced-105">Paketerstellung mit dem Verpackungslayout</span><span class="sxs-lookup"><span data-stu-id="17ced-105">Package creation with the packaging layout</span></span>  

<span data-ttu-id="17ced-106">Mit der Einführung von Bestandspaketen stehen Entwicklern nun die Tools zur Verfügung, um mehr Pakete zusätzlich zu mehr Pakettypen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="17ced-106">With the introduction of asset packages, developers now have the tools to build more packages in addition to more package types.</span></span> <span data-ttu-id="17ced-107">Wenn eine App größer und komplexer wird, besteht sie oft aus mehreren Paketen, und es wird immer schwieriger, diese Pakete zu verwalten (besonders wenn Sie außerhalb von Visual Studio arbeiten und Mapping-Dateien verwenden).</span><span class="sxs-lookup"><span data-stu-id="17ced-107">As an app gets larger and more complex, it will often be comprised of more packages, and the difficulty of managing these packages will increase (especially if you are building outside of Visual Studio and using mapping files).</span></span> <span data-ttu-id="17ced-108">Zur Vereinfachung der Verwaltung der Verpackungsstruktur einer App können Sie das von MakeAppx.exe unterstützte Verpackungslayout verwenden.</span><span class="sxs-lookup"><span data-stu-id="17ced-108">To simplify the management of an app’s packaging structure, you can use the packaging layout supported by MakeAppx.exe.</span></span> 

<span data-ttu-id="17ced-109">Das Verpackungslayout ist ein XML-Dokument, das die Verpackungsstruktur der App beschreibt.</span><span class="sxs-lookup"><span data-stu-id="17ced-109">The packaging layout is a single XML document that describes packaging structure of the app.</span></span> <span data-ttu-id="17ced-110">Es gibt die Bündel einer App („primär” und „optional”), die Pakete in den Bündeln sowie die Dateien in den Paketen an.</span><span class="sxs-lookup"><span data-stu-id="17ced-110">It specifies the bundles of an app (primary and optional), the packages in the bundles, and the files in the packages.</span></span> <span data-ttu-id="17ced-111">Dateien können aus verschiedenen Ordnern, Laufwerken und Netzwerkadressen ausgewählt werden.</span><span class="sxs-lookup"><span data-stu-id="17ced-111">Files can be selected from different folders, drives, and network locations.</span></span> <span data-ttu-id="17ced-112">Platzhalter können zum Auswählen oder Ausschließen von Dateien verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="17ced-112">Wildcards can be used to select or exclude files.</span></span>

<span data-ttu-id="17ced-113">Nachdem das Verpackungslayout für eine App eingerichtet wurde, wird es zusammen mit MakeAppx.exe verwendet, um alle Pakete für eine App in einem einzigen Befehlszeilenaufruf zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="17ced-113">After the packaging layout for an app has been set up, it's used with MakeAppx.exe to create all of the packages for an app in a single command line call.</span></span> <span data-ttu-id="17ced-114">Das Verpackungslayout kann bearbeitet werden, um die Paketstruktur entsprechend Ihren Bereitstellungsanforderungen anzupassen.</span><span class="sxs-lookup"><span data-stu-id="17ced-114">The packaging layout can be edited to alter the package structure to fit your deployment needs.</span></span> 


## <a name="simple-packaging-layout-example"></a><span data-ttu-id="17ced-115">Beispiel für ein einfaches Verpackungslayout</span><span class="sxs-lookup"><span data-stu-id="17ced-115">Simple packaging layout example</span></span>

<span data-ttu-id="17ced-116">Hier sehen Sie ein Beispiel für ein einfaches Verpackungslayout:</span><span class="sxs-lookup"><span data-stu-id="17ced-116">Here's an example of what a simple packaging layout looks like:</span></span>

```xml
<PackagingLayout xmlns="http://schemas.microsoft.com/appx/makeappx/2017">
  <PackageFamily ID="MyGame" FlatBundle="true" ManifestPath="C:\mygame\appxmanifest.xml" ResourceManager="false">
    
    <!-- x64 code package-->
    <Package ID="x64" ProcessorArchitecture="x64">
      <Files>
        <File DestinationPath="*" SourcePath="C:\mygame\*"/>
        <File ExcludePath="*C:\mygame\*.txt"/>
      </Files>
    </Package>
    
    <!-- Media asset package -->
    <AssetPackage ID="Media" AllowExecution="false">
      <Files>
        <File DestinationPath="Media\**" SourcePath="C:\mygame\media\**"/>
      </Files>
    </AssetPackage>

  </PackageFamily>
</PackagingLayout>
```

<span data-ttu-id="17ced-117">Analysieren wir dieses Beispiel, um zu verstehen, wie es funktioniert.</span><span class="sxs-lookup"><span data-stu-id="17ced-117">Let's break this example down to understand how it works.</span></span>

### <a name="packagefamily"></a><span data-ttu-id="17ced-118">PackageFamily</span><span class="sxs-lookup"><span data-stu-id="17ced-118">PackageFamily</span></span>
<span data-ttu-id="17ced-119">Dieses verpackungslayout erstellt eine einzelne flache app-Bündel-Datei mit einer X64 architekturpaket und einem Bestandspaket namens "Medien".</span><span class="sxs-lookup"><span data-stu-id="17ced-119">This packaging layout will create a single flat app bundle file with an x64 architecture package and a “Media” asset package.</span></span> 

<span data-ttu-id="17ced-120">Das **PackageFamily**-Element wird verwendet, um ein App-Bündel zu definieren.</span><span class="sxs-lookup"><span data-stu-id="17ced-120">The **PackageFamily** element is used to define an app bundle.</span></span> <span data-ttu-id="17ced-121">Sie müssen das **ManifestPath**-Attribut verwenden, um für das Bündel eine **AppxManifest**-Datei bereitzustellen, wobei diese **AppxManifest**-Datei der **AppxManifest**-Datei für das Architekturpaket des Bündels entsprechen sollte.</span><span class="sxs-lookup"><span data-stu-id="17ced-121">You must use the **ManifestPath** attribute to provide an **AppxManifest** for the bundle, the **AppxManifest** should correspond to the **AppxManifest** for the architecture package of the bundle.</span></span> <span data-ttu-id="17ced-122">Das **ID**-Attribut muss ebenfalls angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="17ced-122">The **ID** attribute must also be provided.</span></span> <span data-ttu-id="17ced-123">Dies wird während der Erstellung des Pakets zusammen mit MakeAppx.exe verwendet, damit Sie nur dieses Paket erstellen können, wenn Sie möchten, und das ist der Dateiname des resultierenden Pakets.</span><span class="sxs-lookup"><span data-stu-id="17ced-123">This is used with MakeAppx.exe during package creation so that you can create just this package if you want to, and this will be the file name of the resulting package.</span></span> <span data-ttu-id="17ced-124">Das **FlatBundle**-Attribut wird verwendet, um zu beschreiben, welche Art von Bündel Sie erstellen möchten, wobei **true** für ein flaches Bündel (über das Sie hier mehr lesen können), und **false** für ein klassisches Bündel steht.</span><span class="sxs-lookup"><span data-stu-id="17ced-124">The **FlatBundle** attribute is used to describe what type of bundle you want to create, **true** for a flat bundle (which you can read more about here), and **false** for a classic bundle.</span></span> <span data-ttu-id="17ced-125">Das **ResourceManager**-Attribut wird verwendet, um anzugeben, ob die Ressourcenpakete innerhalb dieses Bündels MRT verwenden, um auf die Dateien zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="17ced-125">The **ResourceManager** attribute is used to specify if the resource packages within this bundle will use MRT in order to access the files.</span></span> <span data-ttu-id="17ced-126">Dies ist standardmäßig **true**, ab Windows10, Version 1803, ist es jedoch noch nicht fertig, daher muss dieses Attribut auf **false** gesetzt werden.</span><span class="sxs-lookup"><span data-stu-id="17ced-126">This is by default **true**, but as of Windows 10, version 1803, this is not yet ready, so this attribute must be set to **false**.</span></span>


### <a name="package-and-assetpackage"></a><span data-ttu-id="17ced-127">Package und AssetPackage</span><span class="sxs-lookup"><span data-stu-id="17ced-127">Package and AssetPackage</span></span>
<span data-ttu-id="17ced-128">Innerhalb der **PackageFamily** sind die Pakete, die ein App-Bündel enthält bzw. Verweise definiert.</span><span class="sxs-lookup"><span data-stu-id="17ced-128">Within the **PackageFamily**, the packages that the app bundle contains or references are defined.</span></span> <span data-ttu-id="17ced-129">Hier wird das Architekturpaket (auch als Hauptpaket bezeichnet) mit dem **Package**-Element, und das Bestandspaket mit dem **AssetPackage**-Element definiert.</span><span class="sxs-lookup"><span data-stu-id="17ced-129">Here, the architecture package (also called the main package) is defined with the **Package** element, and the asset package is defined with the **AssetPackage** element.</span></span> <span data-ttu-id="17ced-130">Das Architekturpaket muss angeben, für welche Architektur das Paket vorgesehen ist, entweder „x64”, „x86”, „arm” oder „neutral”.</span><span class="sxs-lookup"><span data-stu-id="17ced-130">The architecture package must specify which architecture the package is for, either “x64”, “x86”, “arm”, or “neutral”.</span></span> <span data-ttu-id="17ced-131">Sie können (optional) auch direkt eine **AppxManifest**-Datei speziell für dieses Paket bereitstellen, indem Sie das **ManifestPath**-Attribut erneut verwenden.</span><span class="sxs-lookup"><span data-stu-id="17ced-131">You can also (optionally) directly provide an **AppxManifest** specifically for this package by using the **ManifestPath** attribute again.</span></span> <span data-ttu-id="17ced-132">Wenn keine **AppxManifest**-Datei bereitgestellt wird, wird eine aus der für die **PackageFamily** bereitgestellten **AppxManifest**-Datei automatisch generiert.</span><span class="sxs-lookup"><span data-stu-id="17ced-132">If an **AppxManifest** is not provided, one will be automatically generated from the **AppxManifest** provided for the **PackageFamily**.</span></span> 

<span data-ttu-id="17ced-133">Standardmäßig wird für jedes Paket im Bündel eine **AppxManifest**-Datei generiert.</span><span class="sxs-lookup"><span data-stu-id="17ced-133">By default and **AppxManifest** will be generated for every package within the bundle.</span></span> <span data-ttu-id="17ced-134">Für das Bestandspaket können Sie auch das **AllowExecution**-Attribut festlegen.</span><span class="sxs-lookup"><span data-stu-id="17ced-134">For the asset package, you can also set the **AllowExecution** attribute.</span></span> <span data-ttu-id="17ced-135">Dieses Attribut auf **false** (den Standardwert) festzulegen hilft, die Veröffentlichungszeit Ihrer App zu verkürzen, da die Virenprüfung bei Paketen, die nicht ausgeführt werden müssen, den Veröffentlichungsprozess nicht blockiert (weitere Informationen hierzu finden Sie unter [Einführung zu Bestandspaketen](asset-packages.md)).</span><span class="sxs-lookup"><span data-stu-id="17ced-135">Setting this to **false** (the default), will help decrease the publishing time for your app since packages that don’t need to execute won’t have their virus scan block the publishing process (you can learn more about this at [Introduction to asset packages](asset-packages.md)).</span></span> 

### <a name="files"></a><span data-ttu-id="17ced-136">Dateien</span><span class="sxs-lookup"><span data-stu-id="17ced-136">Files</span></span>
<span data-ttu-id="17ced-137">Innerhalb jeder Paketdefinition können Sie das **Datei**-Element verwenden, um Dateien auszuwählen, die in diesem Paket enthalten sein sollen.</span><span class="sxs-lookup"><span data-stu-id="17ced-137">Within each package definition, you can use the **File** element to select files to be included in this package.</span></span> <span data-ttu-id="17ced-138">Das **SourcePath**-Attribut gibt an, wo sich die Dateien lokal befinden.</span><span class="sxs-lookup"><span data-stu-id="17ced-138">The **SourcePath** attribute is where the files are locally.</span></span> <span data-ttu-id="17ced-139">Sie können Dateien aus verschiedenen Ordnern (durch Angabe von relativen Pfaden), verschiedenen Laufwerken (durch Angabe von absoluten Pfaden) oder sogar Netzwerkfreigaben auswählen (beispielsweise durch Angabe von `\\myshare\myapp\*`).</span><span class="sxs-lookup"><span data-stu-id="17ced-139">You can select files from different folders (by providing relative paths), different drives (by providing absolute paths), or even network shares (by providing something like `\\myshare\myapp\*`).</span></span> <span data-ttu-id="17ced-140">**DestinationPath** gibt an, wo die Dateien innerhalb des Pakets, relativ zum Paketstammverzeichnis, gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="17ced-140">The **DestinationPath** is where the files will end up within the package, relative to the package root.</span></span> <span data-ttu-id="17ced-141">**ExcludePath** kann verwendet werden (anstelle der beiden anderen Attribute), um Dateien von denen auszuschließen, die von den **SourcePath**-Attributen anderer **File**-Elemente innerhalb des gleichen Pakets ausgewählt wurden.</span><span class="sxs-lookup"><span data-stu-id="17ced-141">**ExcludePath** can be used (instead of the other two attributes) to select files to be excluded from the ones selected by other **File** elements’ **SourcePath** attributes within the same package.</span></span>

<span data-ttu-id="17ced-142">Jedes **File**-Element kann zum Auswählen mehrerer Dateien mithilfe von Platzhaltern verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="17ced-142">Each **File** element can be used to select multiple files by using wildcards.</span></span> <span data-ttu-id="17ced-143">Im Allgemeinen können einzelne Platzhalter (`*`) innerhalb des Pfades überall und beliebig oft verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="17ced-143">In general, single wildcard (`*`) can be used anywhere within the path any number of times.</span></span> <span data-ttu-id="17ced-144">Ein Platzhalter entspricht jedoch nur den Dateien in einem Ordner und nicht in Unterordnern.</span><span class="sxs-lookup"><span data-stu-id="17ced-144">However, a single wildcard will only match the files within a folder and not any subfolders.</span></span> <span data-ttu-id="17ced-145">Beispielsweise kann `C:\MyGame\*\*` in **SourcePath** zum Auswählen der Dateien `C:\MyGame\Audios\UI.mp3` und `C:\MyGame\Videos\intro.mp4` verwendet werden, es kann jedoch nicht `C:\MyGame\Audios\Level1\warp.mp3` auswählen.</span><span class="sxs-lookup"><span data-stu-id="17ced-145">For example, `C:\MyGame\*\*` can be used in the **SourcePath** to select the files `C:\MyGame\Audios\UI.mp3` and `C:\MyGame\Videos\intro.mp4`, but it cannot select `C:\MyGame\Audios\Level1\warp.mp3`.</span></span> <span data-ttu-id="17ced-146">Der doppelte Platzhalter (`**`) kann auch anstelle von Ordner- oder Dateinamen verwendet werden, um beliebige Zeichenfolgen rekursiv zu ersetzen (jedoch nicht neben Teilnamen).</span><span class="sxs-lookup"><span data-stu-id="17ced-146">The double wildcard (`**`) can also be used in place of folder or file names to match anything recursively (but it cannot be next to partial names).</span></span> <span data-ttu-id="17ced-147">Beispielsweise kann `C:\MyGame\**\Level1\**` `C:\MyGame\Audios\Level1\warp.mp3` und `C:\MyGame\Videos\Bonus\Level1\DLC1\intro.mp4` auswählen.</span><span class="sxs-lookup"><span data-stu-id="17ced-147">For example, `C:\MyGame\**\Level1\**` can select `C:\MyGame\Audios\Level1\warp.mp3` and `C:\MyGame\Videos\Bonus\Level1\DLC1\intro.mp4`.</span></span> <span data-ttu-id="17ced-148">Platzhalter können auch verwendet werden, um Dateinamen im Rahmen des Verpackungsprozesses direkt zu ändern, wenn die Platzhalter an verschiedenen Stellen zwischen Quelle und Ziel verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="17ced-148">Wildcards can also be used to directly change file names as part of the packaging process if the wildcards are used in different places between the source and destination.</span></span> <span data-ttu-id="17ced-149">Wenn zum Beispiel `C:\MyGame\Audios\*` für **SourcePath** und `Sound\copy_*` für **DestinationPath** steht, kann `C:\MyGame\Audios\UI.mp3` ausgewählt werden und wird im Paket als `Sound\copy_UI.mp3` angezeigt.</span><span class="sxs-lookup"><span data-stu-id="17ced-149">For example, having `C:\MyGame\Audios\*` for **SourcePath** and `Sound\copy_*` for **DestinationPath** can select `C:\MyGame\Audios\UI.mp3` and have it appear in the package as `Sound\copy_UI.mp3`.</span></span> <span data-ttu-id="17ced-150">Im Allgemeinen muss die Anzahl der einfachen Platzhalter und doppelten Platzhalter für **SourcePath** und **DestinationPath** eines einzelnen **File**-Elements identisch sein.</span><span class="sxs-lookup"><span data-stu-id="17ced-150">In general, the number of single wildcards and double wildcards must be the same for the **SourcePath** and **DestinationPath** of a single **File** element.</span></span>


## <a name="advanced-packaging-layout-example"></a><span data-ttu-id="17ced-151">Beispiel für ein erweitertes Verpackungslayout</span><span class="sxs-lookup"><span data-stu-id="17ced-151">Advanced packaging layout example</span></span>

<span data-ttu-id="17ced-152">Hier sehen Sie ein Beispiel für ein komplizierteres Verpackungslayout:</span><span class="sxs-lookup"><span data-stu-id="17ced-152">Here's an example of a more complicated packaging layout:</span></span>

```xml
<PackagingLayout xmlns="http://schemas.microsoft.com/appx/makeappx/2017">
  <!-- Main game -->
  <PackageFamily ID="MyGame" FlatBundle="true" ManifestPath="C:\mygame\appxmanifest.xml" ResourceManager="false">
    
    <!-- x64 code package-->
    <Package ID="x64" ProcessorArchitecture="x64">
      <Files>
        <File DestinationPath="*" SourcePath="C:\mygame\*"/>
        <File ExcludePath="*C:\mygame\*.txt"/>
      </Files>
    </Package>

    <!-- Media asset package -->
    <AssetPackage ID="Media" AllowExecution="false">
      <Files>
        <File DestinationPath="Media\**" SourcePath="C:\mygame\media\**"/>
      </Files>
    </AssetPackage>
    
    <!-- English resource package -->
    <ResourcePackage ID="en">
      <Files>
        <File DestinationPath="english\**" SourcePath="C:\mygame\english\**"/>
      </Files>
      <Resources Default="true">
        <Resource Language="en"/>
      </Resources>
    </ResourcePackage>

    <!-- French resource package -->
    <ResourcePackage ID="fr">
      <Files>
        <File DestinationPath="french\**" SourcePath="C:\mygame\french\**"/>
      </Files>
      <Resources>
        <Resource Language="fr"/>
      </Resources>
    </ResourcePackage>
  </PackageFamily>

  <!-- DLC in the related set -->
  <PackageFamily ID="DLC" Optional="true" ManifestPath="C:\DLC\appxmanifest.xml">
    <Package ID="DLC.x86" Architecture="x86">
      <Files>
        <File DestinationPath="**" SourcePath="C:\DLC\**"/>
      </Files>
    </Package>
  </PackageFamily>

  <!-- DLC not part of the related set -->
  <PackageFamily ID="Themes" Optional="true" RelatedSet="false" ManifestPath="C:\themes\appxmanifest.xml">
    <Package ID="Themes.main" Architecture="neutral">
      <Files>
        <File DestinationPath="**" SourcePath="C:\themes\**"/>
      </Files>
    </Package>
  </PackageFamily>

  <!-- Existing packages that need to be included/referenced in the bundle -->
  <PrebuiltPackage Path="C:\prebuilt\DLC2.appxbundle" />

</PackagingLayout>
```

<span data-ttu-id="17ced-153">Dieses Beispiel unterscheidet sich vom einfachen Beispiel durch das Hinzufügen der Elemente **ResourcePackage** und **Optional**.</span><span class="sxs-lookup"><span data-stu-id="17ced-153">This example differs from the simple example with the addition of **ResourcePackage** and **Optional** elements.</span></span>

<span data-ttu-id="17ced-154">Ressourcenpakete können mit dem **ResourcePackage**-Element angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="17ced-154">Resource packages can be specified with the **ResourcePackage** element.</span></span> <span data-ttu-id="17ced-155">Innerhalb von **ResourcePackage** muss das **Resources**-Element für die Angabe der Ressourcenbezeichner des Ressourcenpakets verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="17ced-155">Within the **ResourcePackage**, the **Resources** element must be used to specify the resource qualifiers of the resource pack.</span></span> <span data-ttu-id="17ced-156">Die Ressourcenbezeichner sind die Ressourcen, die vom Ressourcenpaket unterstützt werden. Hier sehen wir, dass zwei Ressourcenpakete definiert sind, die jeweils die sprachspezifischen Dateien für Englisch und Französisch enthalten.</span><span class="sxs-lookup"><span data-stu-id="17ced-156">The resource qualifiers are the resources that are supported by the resource pack, here, we can see that there are two resource packs defined and they each contain the English and French specific files.</span></span> <span data-ttu-id="17ced-157">Ein Ressourcenpaket kann mehrere Bezeichner haben. Fügen Sie hierzu ein weiteres **Resource**-Element in **Resources** hinzu.</span><span class="sxs-lookup"><span data-stu-id="17ced-157">A resource pack can have more than one qualifier, this can be done by adding another **Resource** element within **Resources**.</span></span> <span data-ttu-id="17ced-158">Außerdem muss eine Standardressource für die Ressourcendimension angegeben werden, wenn die Dimension (Sprache, Skalierung und dxfl) vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="17ced-158">A default resource for the resource dimension must also be specified if the dimension exists (dimensions being language, scale, dxfl).</span></span> <span data-ttu-id="17ced-159">Hier sehen wir, dass Englisch die Standardsprache ist, was für Benutzer, die Französisch nicht als Systemsprache festgelegt haben, bedeutet, dass sie das englische Ressourcenpaket herunterladen und zur Anzeige in Englisch wechseln müssen.</span><span class="sxs-lookup"><span data-stu-id="17ced-159">Here, we can see that English is the default language, meaning that for users that does not have a system language of French set, they will fallback to downloading the English resource pack and display in English.</span></span>


<span data-ttu-id="17ced-160">Optionale Pakete besitzen jeweils ihre eigenen, eindeutigen Paketfamiliennamen und müssen mit **PackageFamily**-Elementen definiert werden, wenn das **Optional**-Attribut als **true** angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="17ced-160">Optional packages each have their own distinct package family names and must be defined with **PackageFamily** elements, while specifying the **Optional** attribute to be **true**.</span></span> <span data-ttu-id="17ced-161">Das **RelatedSet**-Attribut wird verwendet, um anzugeben, ob sich das optionale Paket innerhalb des zugehörigen Sets befindet (standardmäßig ist dieser Wert „true”), und ob das optionale Paket mit dem primären Paket aktualisiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="17ced-161">The **RelatedSet** attribute is used to specify whether the optional package is within the related set (by default this is true) – whether the optional package should be updated with the primary package.</span></span>

<span data-ttu-id="17ced-162">Das Element **PrebuiltPackage** wird verwendet, um Pakete hinzufügen, die nicht im verpackungslayout, enthalten oder referenziert in den app-Bundle-Dateien zu erstellenden definiert sind.</span><span class="sxs-lookup"><span data-stu-id="17ced-162">The **PrebuiltPackage** element is used to add packages that are not defined in the packaging layout to be included or referenced in the app bundle file(s) to be built.</span></span> <span data-ttu-id="17ced-163">In diesem Fall wird ein anderes optionales DLC-Paket enthalten wird, damit die primäre app-Bundle-Datei kann darauf verweisen und es Teil des zugehörigen Sets werden kann.</span><span class="sxs-lookup"><span data-stu-id="17ced-163">In this case, another DLC optional package is being included here so that the primary app bundle file can reference it and have it be part of the related set.</span></span>


## <a name="build-app-packages-with-a-packaging-layout-and-makeappxexe"></a><span data-ttu-id="17ced-164">Erstellen von App-Paketen mit einem Verpackungslayout und MakeAppx.exe</span><span class="sxs-lookup"><span data-stu-id="17ced-164">Build app packages with a packaging layout and MakeAppx.exe</span></span>
<span data-ttu-id="17ced-165">Sobald Sie das Verpackungslayout für Ihre App haben, können Sie MakeAppx.exe verwenden, um die Pakete Ihrer App zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="17ced-165">Once you have the packaging layout for your app, you can start using MakeAppx.exe to build the packages of your app.</span></span> <span data-ttu-id="17ced-166">Verwenden Sie den folgenden Befehl, um alle im Verpackungslayout definierten Pakete zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="17ced-166">To build all of the packages defined in the packaging layout, use the command:</span></span>

``` example 
MakeAppx.exe build /f PackagingLayout.xml /op OutputPackages\
```

<span data-ttu-id="17ced-167">Wenn Sie jedoch Ihre App aktualisieren, und einige Pakete keine geänderten Dateien enthalten, können Sie nur die Pakete erstellen, die geändert wurden.</span><span class="sxs-lookup"><span data-stu-id="17ced-167">But, if you are updating your app and some packages don't contain any changed files, you can build only the packages that have changed.</span></span> <span data-ttu-id="17ced-168">Bei Verwendung des einfachen Beispiels für ein Verpackungslayout auf dieser Seite und beim Erstellen des x64-Architekturpakets würde der Befehl folgendermaßen aussehen:</span><span class="sxs-lookup"><span data-stu-id="17ced-168">Using the simple packaging layout example on this page and building the x64 architecture package, this is what our command would look like:</span></span>

``` example 
MakeAppx.exe build /f PackagingLayout.xml /id "x64" /ip PreviousVersion\ /op OutputPackages\ /iv
```

<span data-ttu-id="17ced-169">Mit dem `/id`-Kennzeichen können die zu erstellenden Pakete aus dem Verpackungslayout entsprechend dem **ID**-Attribut im Layout ausgewählt werden.</span><span class="sxs-lookup"><span data-stu-id="17ced-169">The `/id` flag can be used to select the packages to be built from the packaging layout, corresponding to the **ID** attribute in the layout.</span></span> <span data-ttu-id="17ced-170">`/ip` wird verwendet, um anzugeben, wo sich in diesem Fall die früheren Versionen der Pakete befinden.</span><span class="sxs-lookup"><span data-stu-id="17ced-170">The `/ip` is used to indicate where the previous version of the packages are in this case.</span></span> <span data-ttu-id="17ced-171">Die frühere Version muss bereitgestellt werden, da die app-Bundle-Datei weiterhin auf die vorherige Version des **Media** -Pakets verweisen muss.</span><span class="sxs-lookup"><span data-stu-id="17ced-171">The previous version must be provided because the app bundle file still needs to reference the previous version of the **Media** package.</span></span> <span data-ttu-id="17ced-172">Mit dem `/iv`-Kennzeichen wird die Version der zu erstellenden Pakete automatisch erhöht (anstatt die Version in der **AppxManifest**-Datei zu ändern).</span><span class="sxs-lookup"><span data-stu-id="17ced-172">The `/iv` flag is used to automatically increment the version of the packages being built (instead of changing the version in the **AppxManifest**).</span></span> <span data-ttu-id="17ced-173">Sie können auch die Switches `/pv` und `/bv` verwenden, um eine Paketversion (für alle zu erstellenden Pakete) bzw. eine Bündelversion (für alle zu erstellenden Bündel), direkt bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="17ced-173">Alternatively, the switches `/pv` and `/bv` can be used to directly provide a package version (for all packages to be created) and a bundle version (for all bundles to be created), respectively.</span></span>
<span data-ttu-id="17ced-174">Verwenden Sie diesen Befehl, wenn Sie mithilfe des erweiterten Verpackungslayoutbeispiels auf dieser Seite nur das optionale Bündel **Designs** und das App-Paket **Themes.main**, auf das es verweist, erstellen möchten:</span><span class="sxs-lookup"><span data-stu-id="17ced-174">Using the advanced packaging layout example on this page, if you want to only build the **Themes** optional bundle and the **Themes.main** app package that it references, you would use this command:</span></span>

``` example 
MakeAppx.exe build /f PackagingLayout.xml /id "Themes" /op OutputPackages\ /bc /nbp
```

<span data-ttu-id="17ced-175">Das `/bc`-Kennzeichen wird verwendet, um anzugeben, dass die untergeordneten Elemente des **Designs**-Bündels ebenfalls erstellt werden sollen (in diesem Fall wird **Themes.main** erstellt).</span><span class="sxs-lookup"><span data-stu-id="17ced-175">The `/bc` flag is used to denote that the children of the **Themes** bundle should also be built (in this case **Themes.main** will be built).</span></span> <span data-ttu-id="17ced-176">Das `/nbp`-Kennzeichen gibt an, dass das übergeordnete Element des **Designs**-Bündels nicht erstellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="17ced-176">The `/nbp` flag is used to denote that the parent of the **Themes** bundle should not be built.</span></span> <span data-ttu-id="17ced-177">Das übergeordnete Element von **Designs**, bei dem es sich um ein optionales App-Bündel handelt, ist das primäre App-Bündel: **MyGame**.</span><span class="sxs-lookup"><span data-stu-id="17ced-177">The parent of **Themes**, which is an optional app bundle, is the primary app bundle: **MyGame**.</span></span> <span data-ttu-id="17ced-178">In der Regel muss für ein optionales Paket in einem zugehörigen Set auch das primäre App-Bündel erstellt werden, damit das optionale Paket installiert werden kann, da auf das optionale Paket auch im primären App-Bündel verwiesen wird, wenn es sich in einem zugehörigen Set befindet (um die Versionierung zwischen primärem und optionalem Paket zu gewährleisten).</span><span class="sxs-lookup"><span data-stu-id="17ced-178">Usually for an optional package in a related set, the primary app bundle must also be built for the optional package to be installable, since the optional package is also referenced in the primary app bundle when it is in a related set (to guarantee versioning between the primary and the optional packages).</span></span> <span data-ttu-id="17ced-179">Das folgende Diagramm veranschaulicht die über- und untergeordnete Beziehung zwischen Paketen.</span><span class="sxs-lookup"><span data-stu-id="17ced-179">The parent child relationship between packages is illustrated in the following diagram:</span></span>

![Verpackungslayout-Diagramm](images/packaging-layout.png)
