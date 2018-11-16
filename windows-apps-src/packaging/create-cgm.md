---
author: laurenhughes
ms.assetid: ff2523cb-8109-42be-9dfc-cb5d09002574
title: Erstellen und konvertieren Sie eine Quellinhalt-Gruppenzuordnung.
description: Um Ihre Universelle Windows-Plattform (UWP)-App für die UWP-App-Streaming-Installation vorzubereiten, müssen Sie eine Inhalts-Gruppenzuordnung erstellen. Dieser Artikel hilft Ihnen mit den Einzelheiten für das Erstellen und Konvertieren einer Inhalts-Gruppenzuordnung und bietet gleichzeitig einige Tipps und Tricks.
ms.author: lahugh
ms.date: 9/30/2018
ms.topic: article
keywords: Windows10, Uwp, Inhalt-Gruppenzuordnung, Streaming-Installation, Uwp-App-Streaming-Installation, Quellinhalt-Gruppenzuordnung
ms.localizationpriority: medium
ms.openlocfilehash: 6a2922d6d3f54d693a9fe9c0982ea06cc5f2caae
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6975773"
---
# <a name="create-and-convert-a-source-content-group-map"></a><span data-ttu-id="612bc-105">Erstellen und konvertieren Sie eine Quellinhalt-Gruppenzuordnung.</span><span class="sxs-lookup"><span data-stu-id="612bc-105">Create and convert a source content group map</span></span>

<span data-ttu-id="612bc-106">Um Ihre Universelle Windows-Plattform (UWP)-App für die UWP-App-Streaming-Installation vorzubereiten, müssen Sie eine Inhalts-Gruppenzuordnung erstellen.</span><span class="sxs-lookup"><span data-stu-id="612bc-106">To get your Universal Windows Platform (UWP) app ready for UWP App Streaming Install, you'll need to create a content group map.</span></span> <span data-ttu-id="612bc-107">Dieser Artikel hilft Ihnen mit den Einzelheiten für das Erstellen und Konvertieren einer Inhalts-Gruppenzuordnung und bietet gleichzeitig einige Tipps und Tricks.</span><span class="sxs-lookup"><span data-stu-id="612bc-107">This article will help you with the specifics of creating and converting a content group map while providing some tips and tricks along the way.</span></span>

## <a name="creating-the-source-content-group-map"></a><span data-ttu-id="612bc-108">Erstellen der Quellinhalt-Gruppenzuordnung</span><span class="sxs-lookup"><span data-stu-id="612bc-108">Creating the source content group map</span></span>

<span data-ttu-id="612bc-109">Sie müssen eine `SourceAppxContentGroupMap.xml`-Datei erstellen, und entweder Visual Studio oder das **MakeAppx.exe**-Tool verwenden, um diese Datei auf die endgültige Version zu konvertieren: `AppxContentGroupMap.xml`.</span><span class="sxs-lookup"><span data-stu-id="612bc-109">You'll need to create a `SourceAppxContentGroupMap.xml` file, and then either use Visual Studio or the **MakeAppx.exe** tool to convert this file to the final version: `AppxContentGroupMap.xml`.</span></span> <span data-ttu-id="612bc-110">Ist es möglich, einen Schrittzu überspringen, indem Sie den `AppxContentGroupMap.xml` von Grund auf neu erstellen. Es wird jedoch empfohlen (und es ist in der Regel einfacher), den `SourceAppxContentGroupMap.xml` zu erstellen und ihn zu konvertieren, da Platzhalter in der `AppxContentGroupMap.xml` nicht zulässig sind (und sie sind sehr nützlich).</span><span class="sxs-lookup"><span data-stu-id="612bc-110">It's possible to skip a step by creating the `AppxContentGroupMap.xml` from scratch, but it's recommended (and generally easier) to create the `SourceAppxContentGroupMap.xml` and convert it, since wildcards are not allowed in the `AppxContentGroupMap.xml` (and they're really helpful).</span></span> 

<span data-ttu-id="612bc-111">Betrachten wir ein einfaches Szenario, in dem eine UWP-App-Streaming-Installation von Vorteil ist.</span><span class="sxs-lookup"><span data-stu-id="612bc-111">Let's walk through a simple scenario where UWP App Streaming Install is beneficial.</span></span> 

<span data-ttu-id="612bc-112">Angenommen Sie haben ein UWP-Spiel erstellt, aber die Größe der endgültigen App ist mehr als 100GB.</span><span class="sxs-lookup"><span data-stu-id="612bc-112">Say you've created a UWP game, but the size of your final app is over 100 GB.</span></span> <span data-ttu-id="612bc-113">Die wird nicht lange dauern zum Herunterladen von aus dem Microsoft Store, was sehr umständlich sein kann.</span><span class="sxs-lookup"><span data-stu-id="612bc-113">That's going to take a long time to download from the Microsoft Store, which can be inconvenient.</span></span> <span data-ttu-id="612bc-114">Wenn Sie sich für die UWP-App-Streaming-Installation entscheiden, können Sie die Reihenfolge angeben, in der die Dateien der App heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="612bc-114">If you choose to use UWP App Streaming Install, you can specify the order in which your app's files are downloaded.</span></span> <span data-ttu-id="612bc-115">Indem der Benutzer dem Store anordnet, dass zunächst essenzielle Dateien heruntergeladen werden sollen, wird er Ihre App schneller ausprobieren können, während andere nicht unbedingt erforderlichen Dateien im Hintergrund heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="612bc-115">By telling the Store to download essential files first, the user will be able to engage with your app sooner while other non-essential files are downloaded in the background.</span></span>

> [!NOTE]
> <span data-ttu-id="612bc-116">Die Verwendung der UWP-App-Streaming-Installation hängt stark von der Dateiorganisation Ihrer App ab.</span><span class="sxs-lookup"><span data-stu-id="612bc-116">Using UWP App Streaming Install heavily relies on your app's file organization.</span></span> <span data-ttu-id="612bc-117">Es wird empfohlen, dass Sie sich so früh wie möglich Gedanken zum Layout des Inhalts in Bezug auf die UWP-App-Streaming-Installation machen, um das Segmentieren Ihrer App-Dateien zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="612bc-117">It's recommended that you think about your app's content layout with respect to UWP App Streaming Install as soon as possible to make segmenting your app's files simpler.</span></span>

<span data-ttu-id="612bc-118">Zunächst erstellen wir eine `SourceAppxContentGroupMap.xml`-Datei.</span><span class="sxs-lookup"><span data-stu-id="612bc-118">First, we'll create a `SourceAppxContentGroupMap.xml` file.</span></span>

<span data-ttu-id="612bc-119">Bevor wir auf die Details eingehen ist hier ein Beispiel für eine einfache, vollständige `SourceAppxContentGroupMap.xml`-Datei:</span><span class="sxs-lookup"><span data-stu-id="612bc-119">Before we get in to the details, here's an example of a simple, complete `SourceAppxContentGroupMap.xml` file:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>  
<ContentGroupMap xmlns="http://schemas.microsoft.com/appx/2016/sourcecontentgroupmap" 
                 xmlns:s="http://schemas.microsoft.com/appx/2016/sourcecontentgroupmap"> 
    <Required>
        <ContentGroup Name="Required">
            <File Name="StreamingTestApp.exe"/>
        </ContentGroup>
    </Required>
    <Automatic>
        <ContentGroup Name="Level2">
            <File Name="Assets\Level2\*"/>
        </ContentGroup>
        <ContentGroup Name="Level3">
            <File Name="Assets\Level3\*"/>
        </ContentGroup>
    </Automatic>
</ContentGroupMap>
```

<span data-ttu-id="612bc-120">Es gibt zwei Hauptkomponenten in einer Inhalts-Gruppenzuordnung: der **erforderliche** Abschnitt, der die erforderliche Inhaltsgruppe beinhaltet und der **automatische** Abschnitt, der mehrere automatische Inhaltsgruppen enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="612bc-120">There are two main components to a content group map: the **required** section, which contains the required content group, and the **automatic** section, which can contain multiple automatic content groups.</span></span>

### <a name="required-content-group"></a><span data-ttu-id="612bc-121">Erforderliche Inhaltsgruppe</span><span class="sxs-lookup"><span data-stu-id="612bc-121">Required content group</span></span>

<span data-ttu-id="612bc-122">Die erforderliche Inhaltsgruppe ist eine einzelne Inhaltsgruppe innerhalb des `<Required>`-Elements von der `SourceAppxContentGroupMap.xml`.</span><span class="sxs-lookup"><span data-stu-id="612bc-122">The required content group is a single content group within the `<Required>` element of the `SourceAppxContentGroupMap.xml`.</span></span> <span data-ttu-id="612bc-123">Eine erforderliche Inhaltsgruppe sollte alle wichtigen Dateien zum Starten der App mit minimaler Benutzererfahrung enthalten.</span><span class="sxs-lookup"><span data-stu-id="612bc-123">A required content group should contain all of the essential files necessary to launch the app with the minimal user experience.</span></span> <span data-ttu-id="612bc-124">Aufgrund der .NET Native-Kompilierung muss der gesamte Code (ausführbare Anwendung) Teil der erforderlichen Gruppe sein. Ressourcen und andere Dateien werden den automatischen Gruppen überlassen.</span><span class="sxs-lookup"><span data-stu-id="612bc-124">Due to .NET Native compilation, all code (the application executable) must be part of the required group, leaving assets and other files for the automatic groups.</span></span>

<span data-ttu-id="612bc-125">Wenn Ihre App beispielsweise ein Spiel ist, kann die erforderliche Gruppe z.B. Dateien umfassen, die im Hauptmenü oder auf der Startseite des Spiels verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="612bc-125">For example, if your app is a game, the required group may include files used in the main menu or game home screen.</span></span>

<span data-ttu-id="612bc-126">Hier ist der Ausschnitt aus der ursprünglichen `SourceAppxContentGroupMap.xml`-Beispieldatei:</span><span class="sxs-lookup"><span data-stu-id="612bc-126">Here's the snippet from our original `SourceAppxContentGroupMap.xml` example file:</span></span> 
```xml
<Required>
    <ContentGroup Name="Required">
        <File Name="StreamingTestApp.exe"/>
    </ContentGroup>
</Required>
```

<span data-ttu-id="612bc-127">Es müssen einige wichtige Dinge erwähnt werden:</span><span class="sxs-lookup"><span data-stu-id="612bc-127">There are a few important things to notice here:</span></span>

- <span data-ttu-id="612bc-128">Die `<ContentGroup>` innerhalb des `<Required>`-Elements **muss** „Erforderlich” genannt werden.</span><span class="sxs-lookup"><span data-stu-id="612bc-128">The `<ContentGroup>` within the `<Required>` element **must** be named "Required."</span></span> <span data-ttu-id="612bc-129">Dieser Name ist nur für die erforderliche Inhaltsgruppe reserviert und kann nicht mit einer anderen `<ContentGroup>` in der endgültigen Inhaltsgruppen-Zuordnung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="612bc-129">This name is reserved for the required content group only, and cannot be used with any other `<ContentGroup>` in the final content group map.</span></span>
- <span data-ttu-id="612bc-130">Es gibt nur ein `<ContentGroup>`.</span><span class="sxs-lookup"><span data-stu-id="612bc-130">There's only one `<ContentGroup>`.</span></span> <span data-ttu-id="612bc-131">Dies ist beabsichtigt, da nur eine Gruppe von wichtigen Dateien werden soll.</span><span class="sxs-lookup"><span data-stu-id="612bc-131">This is intentional, since there should be only one group of essential files.</span></span>
- <span data-ttu-id="612bc-132">Die Datei in diesem Beispiel ist eine einzelne `.exe`-Datei.</span><span class="sxs-lookup"><span data-stu-id="612bc-132">The file in this example is a single `.exe` file.</span></span> <span data-ttu-id="612bc-133">Eine erforderliche Inhaltsgruppe ist nicht auf eine Datei beschränkt, es kann mehrere geben.</span><span class="sxs-lookup"><span data-stu-id="612bc-133">A required content group isn't restricted to one file, there can be several.</span></span> 

<span data-ttu-id="612bc-134">Für die ersten Schritte beim Schreiben dieser Datei wird empfohlen, eine neue Seite in Ihrem bevorzugten Text-Editor zu öffnen, mit Drücken auf „Speichern unter” die Datei in dem App-Projektordner zu speichern, und die neu erstellte Datei folgendermaßen zu nennen: `SourceAppxContentGroupMap.xml`.</span><span class="sxs-lookup"><span data-stu-id="612bc-134">An easy way to get started writing this file is to open up a new page in your favorite text editor, do a quick "Save As" of your file to your app's project folder, and name your newly created file: `SourceAppxContentGroupMap.xml`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="612bc-135">Wenn Sie eine C++-UWP-App entwickeln, müssen Sie die Dateieigenschaften Ihrer `SourceAppxContentGroupMap.xml` anpassen.</span><span class="sxs-lookup"><span data-stu-id="612bc-135">If you are developing a C++ UWP app, you will need to adjust the file properties of your `SourceAppxContentGroupMap.xml`.</span></span> <span data-ttu-id="612bc-136">Setzen Sie die `Content`-Eigenschaft auf **true** und die `File Type`-Eigenschaft auf **XML-Datei**.</span><span class="sxs-lookup"><span data-stu-id="612bc-136">Set the `Content` property to **true** and the `File Type` property to **XML File**.</span></span> 

<span data-ttu-id="612bc-137">Wenn Sie die `SourceAppxContentGroupMap.xml`erstellen, es ist es bei der Benennung von Dateinamen nützlich, Platzhalter zu verwenden. Weitere Informationen finden Sie unter dem Abschnitt [Tipps und Tricks für die Verwendung von Platzhaltern](#wildcards).</span><span class="sxs-lookup"><span data-stu-id="612bc-137">When you're creating the `SourceAppxContentGroupMap.xml`, it's helpful to take advantage of using wildcards in file names, for more info, see the [Tips and tricks for using wildcards](#wildcards) section.</span></span>

<span data-ttu-id="612bc-138">Wenn Sie Ihre App mit Visual Studio entwickelt haben, empfiehlt es sich, dass Sie Folgendes hinsichtlich der erforderlichen Inhaltsgruppe berücksichtigen:</span><span class="sxs-lookup"><span data-stu-id="612bc-138">If you developed your app using Visual Studio, it's recommended that you include this in your required content group:</span></span>

```xml
<File Name="*"/>
<File Name="WinMetadata\*"/>
<File Name="Properties\*"/>
<File Name="Assets\*Logo*"/>
<File Name="Assets\*SplashScreen*"/>
```

<span data-ttu-id="612bc-139">Die einzelnen hinzugefügten Platzhalter-Dateinamen werden Datei umfassen, die dem Projektverzeichnis aus Visual Studio hinzugefügt wurden, wie z.B. die ausführbare App oder DLL-Dateien.</span><span class="sxs-lookup"><span data-stu-id="612bc-139">Adding the single wildcard file name will include files added to the project directory from Visual Studio, such as the app executable or DLLs.</span></span> <span data-ttu-id="612bc-140">Die WinMetadata- und Eigenschaften-Ordner müssen die anderen Ordner enthalten, die Visual Studio generiert.</span><span class="sxs-lookup"><span data-stu-id="612bc-140">The WinMetadata and Properties folders are to include the other folders Visual Studio generates.</span></span> <span data-ttu-id="612bc-141">Die Platzhalterressourcen müssen die Logo- und SplashScreen-Bilder wählen, die für die Installation der App erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="612bc-141">The Assets wildcards are to select the Logo and SplashScreen images that are necessary for the app to be installed.</span></span>

<span data-ttu-id="612bc-142">Beachten Sie, dass Sie das doppelte Platzhalterzeichen nicht, "\*\*", im Stamm der Dateistruktur verwenden können, um alle Dateien im Projekt einzuschließen, da dies bei der Konvertierung der `SourceAppxContentGroupMap.xml` auf das endgültige `AppxContentGroupMap.xml` fehlschlagen wird.</span><span class="sxs-lookup"><span data-stu-id="612bc-142">Note that you cannot use the double wild card, "\*\*", at the root of the file structure to include every file in the project since this will fail when attempting to convert `SourceAppxContentGroupMap.xml` to the final `AppxContentGroupMap.xml`.</span></span>

<span data-ttu-id="612bc-143">Es sollte auch beachtet werden, dass Fußabdruckdateien (AppxManifest.xml, Appxsignature.p7x, resources.pri usw.) nicht in der Inhalts-Gruppenzuordnung vorhanden sein sollten.</span><span class="sxs-lookup"><span data-stu-id="612bc-143">It's also important to note that footprint files (AppxManifest.xml, AppxSignature.p7x, resources.pri, etc.) should not be included in the content group map.</span></span> <span data-ttu-id="612bc-144">Wenn sich Fußabdruckdateien in einer der von Ihnen angegebenen Platzhalter-Dateinamen befinden, werden sie ignoriert.</span><span class="sxs-lookup"><span data-stu-id="612bc-144">If footprint files are included within one of the wildcard file names you specify, they will be ignored.</span></span>

### <a name="automatic-content-groups"></a><span data-ttu-id="612bc-145">Automatische Inhaltsgruppen</span><span class="sxs-lookup"><span data-stu-id="612bc-145">Automatic content groups</span></span>

<span data-ttu-id="612bc-146">Automatische Inhaltsgruppen sind die Ressourcen, die im Hintergrund heruntergeladen werden, während der Benutzer mit den bereits heruntergeladenen Inhaltsgruppen interagiert.</span><span class="sxs-lookup"><span data-stu-id="612bc-146">Automatic content groups are the assets that are downloaded in the background while the user is interacting with the already downloaded content groups.</span></span> <span data-ttu-id="612bc-147">Diese enthalten alle zusätzlichen Dateien, die nicht für das Starten der App erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="612bc-147">These contain any additional files that are not essential to launching the app.</span></span> <span data-ttu-id="612bc-148">Sie können beispielsweise automatische Inhaltsgruppen in verschiedene Ebenen aufteilen und jede Ebene als separate Inhaltsgruppen definieren.</span><span class="sxs-lookup"><span data-stu-id="612bc-148">For example, you could break up automatic content groups in to different levels, defining each level as a separate content group.</span></span> <span data-ttu-id="612bc-149">Wie bereits im Abschnitt zur erforderlichen Inhaltsgruppe erwähnt: aufgrund der .NET Native-Kompilierung, muss der gesamte (für die Anwendung ausführbare) Code Teil der erforderlichen Gruppe sein, und die Ressourcen und anderen Dateien müssen der automatischen Gruppen überlassen werden.</span><span class="sxs-lookup"><span data-stu-id="612bc-149">As noted in the required content group section: due to .NET Native compilation, all code (the application executable) must be part of the required group, leaving assets and other files for the automatic groups.</span></span>

<span data-ttu-id="612bc-150">Schauen wir uns die automatische Inhaltsgruppe aus unserem `SourceAppxContentGroupMap.xml`-Beispiel etwas genauer an:</span><span class="sxs-lookup"><span data-stu-id="612bc-150">Let's take a closer look at the automatic content group from our `SourceAppxContentGroupMap.xml` example:</span></span>
```xml
<Automatic>
    <ContentGroup Name="Level2">
        <File Name="Assets\Level2\*"/>
    </ContentGroup>
    <ContentGroup Name="Level3">
        <File Name="Assets\Level3\*"/>
    </ContentGroup>
</Automatic>
```

<span data-ttu-id="612bc-151">Das Layout der automatischen Gruppe ist sehr ähnlich zu der erforderlichen Gruppe, mit wenigen Ausnahmen:</span><span class="sxs-lookup"><span data-stu-id="612bc-151">The layout of the automatic group is pretty similar to the required group, with a few exceptions:</span></span>

- <span data-ttu-id="612bc-152">Es gibt mehrere Inhaltsgruppen.</span><span class="sxs-lookup"><span data-stu-id="612bc-152">There are multiple content groups.</span></span>
- <span data-ttu-id="612bc-153">Automatische Inhaltsgruppen können einzigartige Namen haben, mit Ausnahme von „Erforderlich”, was für die erforderliche Inhaltsgruppe reserviert ist.</span><span class="sxs-lookup"><span data-stu-id="612bc-153">Automatic content groups can have unique names except for the name "Required" which is reserved for the required content group.</span></span>
- <span data-ttu-id="612bc-154">Automatische Inhaltsgruppen dürfen nicht **alle** Dateien aus der Gruppe der erforderlichen Inhaltsgruppe beinhalten.</span><span class="sxs-lookup"><span data-stu-id="612bc-154">Automatic content groups cannot contain **any** files from the required content group.</span></span> 
- <span data-ttu-id="612bc-155">Eine automatische Inhaltsgruppe kann Dateien enthalten, die sich auch in anderen automatischen Inhaltsgruppen befinden.</span><span class="sxs-lookup"><span data-stu-id="612bc-155">An automatic content group can contain files that are also in other automatic content groups.</span></span> <span data-ttu-id="612bc-156">Die Dateien werden nur ein Mal heruntergeladen, und werden mit der ersten automatischen Inhaltsgruppe heruntergeladen, die sie enthält.</span><span class="sxs-lookup"><span data-stu-id="612bc-156">The files will be downloaded only once, and will be downloaded with the first automatic content group that contains them.</span></span>

#### <span data-ttu-id="612bc-157">Tipps und Tricks für die Verwendung von Platzhaltern<a name="wildcards"></a></span><span class="sxs-lookup"><span data-stu-id="612bc-157">Tips and tricks for using wildcards<a name="wildcards"></a></span></span>

<span data-ttu-id="612bc-158">Der Datei-Layout für Inhaltsgruppen-Zuordnungen steht immer im Zusammenhang mit Ihrem Projektstammordner.</span><span class="sxs-lookup"><span data-stu-id="612bc-158">The file layout for content group maps is always relative to your project root folder.</span></span>

<span data-ttu-id="612bc-159">In unserem Beispiel werden Platzhalter in beiden `<ContentGroup>`.Elementen verwendet, um alle Dateien innerhalb einer Dateiebene von „Assets\Level2” oder „Assets\Level3” abzurufen.</span><span class="sxs-lookup"><span data-stu-id="612bc-159">In our example, wildcards are used within both `<ContentGroup>` elements to retrieve all files within one file level of "Assets\Level2" or "Assets\Level3."</span></span> <span data-ttu-id="612bc-160">Wenn Sie eine genauere Ordnerstruktur verwenden, können Sie die doppelten Platzhalter einsetzen:</span><span class="sxs-lookup"><span data-stu-id="612bc-160">If you're using a deeper folder structure, you can use the double wildcard:</span></span>

```xml
<ContentGroup Name="Level2">
    <File Name="Assets\Level2\**"/>
</ContentGroup>
```

<span data-ttu-id="612bc-161">Sie können auch Platzhalter mit Text für Dateinamen verwenden.</span><span class="sxs-lookup"><span data-stu-id="612bc-161">You can also use wildcards with text for file names.</span></span> <span data-ttu-id="612bc-162">Wenn beispielsweise Ihr Ordner „Assets” jede Datei mit dem Namen „Level2” enthalten soll, können Sie etwa Folgendes verwenden:</span><span class="sxs-lookup"><span data-stu-id="612bc-162">For example, if you want to include every file in your "Assets" folder with a file name that contains "Level2" you can use something like this:</span></span>

```xml
<ContentGroup Name="Level2">
    <File Name="Assets\*Level2*"/>
</ContentGroup>
```

## <a name="convert-sourceappxcontentgroupmapxml-to-appxcontentgroupmapxml"></a><span data-ttu-id="612bc-163">Konvertieren von SourceAppxContentGroupMap.xml in AppxContentGroupMap.xml</span><span class="sxs-lookup"><span data-stu-id="612bc-163">Convert SourceAppxContentGroupMap.xml to AppxContentGroupMap.xml</span></span>

<span data-ttu-id="612bc-164">Um die `SourceAppxContentGroupMap.xml` in die endgültige Version `AppxContentGroupMap.xml` zu konvertieren, können Sie Visual Studio2017 oder das **MakeAppx.exe**-Befehlszeilentool verwenden.</span><span class="sxs-lookup"><span data-stu-id="612bc-164">To convert the `SourceAppxContentGroupMap.xml` to the final version, `AppxContentGroupMap.xml`, you can use Visual Studio 2017 or the **MakeAppx.exe** command line tool.</span></span>

<span data-ttu-id="612bc-165">Verwenden von Visual Studio für die Konvertierung Ihrer Inhaltsgruppen-Zuordnung:</span><span class="sxs-lookup"><span data-stu-id="612bc-165">To use Visual Studio to convert your content group map:</span></span>
1. <span data-ttu-id="612bc-166">Fügen Sie die `SourceAppxContentGroupMap.xml` zu Ihrem Projektordner hinzu.</span><span class="sxs-lookup"><span data-stu-id="612bc-166">Add the `SourceAppxContentGroupMap.xml` to your project folder</span></span>
2. <span data-ttu-id="612bc-167">Ändern Sie den Buildvorgang der `SourceAppxContentGroupMap.xml`zu „AppxSourceContentGroupMap” im Eigenschaftenfenster.</span><span class="sxs-lookup"><span data-stu-id="612bc-167">Change the Build Action of the `SourceAppxContentGroupMap.xml`to "AppxSourceContentGroupMap" in the Properties window</span></span>
2. <span data-ttu-id="612bc-168">Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt.</span><span class="sxs-lookup"><span data-stu-id="612bc-168">Right click the project in the solution explorer</span></span>
3. <span data-ttu-id="612bc-169">Navigieren Sie zum Store -> Inhaltsgruppen-Zuordnungsdatei konvertieren</span><span class="sxs-lookup"><span data-stu-id="612bc-169">Navigate to Store -> Convert Content Group Map File</span></span>

<span data-ttu-id="612bc-170">Wenn Sie Ihre App nicht in Visual Studio entwickelt haben, oder wenn Sie einfach nur die Verwendung der Befehlszeile bevorzugen, verwenden Sie das **MakeAppx.exe**-Tool zum Konvertieren Ihrer `SourceAppxContentGroupMap.xml`.</span><span class="sxs-lookup"><span data-stu-id="612bc-170">If you didn't develop your app in Visual Studio, or if you just prefer using the command line, use the **MakeAppx.exe** tool to convert your `SourceAppxContentGroupMap.xml`.</span></span> 

<span data-ttu-id="612bc-171">Ein einfacher **MakeAppx.exe**-Befehl sieht etwa wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="612bc-171">A simple **MakeAppx.exe** command might look something like this:</span></span>
```syntax
MakeAppx convertCGM /s MyApp\SourceAppxContentGroupMap.xml /f MyApp\AppxContentGroupMap.xml /d MyApp\
```

<span data-ttu-id="612bc-172">Die Option /s gibt den Pfad zur `SourceAppxContentGroupMap.xml` an, und /f gibt den Pfad zur `AppxContentGroupMap.xml` an.</span><span class="sxs-lookup"><span data-stu-id="612bc-172">The /s option specifies the path to the `SourceAppxContentGroupMap.xml`, and /f specifies the path to the `AppxContentGroupMap.xml`.</span></span> <span data-ttu-id="612bc-173">Die letzte Option, /d gibt das Verzeichnis für das Erweitern von Dateiplatzhaltern an. In diesem Fall ist es das App-Projekt-Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="612bc-173">The final option, /d, specifies which directory should be used for expanding file name wildcards, in this case, its the app project directory.</span></span>

<span data-ttu-id="612bc-174">Für weitere Informationen zu den Optionen, die Sie mit **MakeAppx.exe** verwenden können, öffnen Sie ein Eingabeaufforderungsfenster, navigieren Sie zu **MakeAppx.exe**, und geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="612bc-174">For more information about options you can use with **MakeAppx.exe**, open a command prompt, navigate to **MakeAppx.exe** and enter:</span></span>

```syntax
MakeAppx convertCGM /?
```

<span data-ttu-id="612bc-175">Das ist alles, was Sie brauchen, um Ihre endgültige `AppxContentGroupMap.xml` für Ihre App vorzubereiten!</span><span class="sxs-lookup"><span data-stu-id="612bc-175">That's all you'll need to get your final `AppxContentGroupMap.xml` ready for your app!</span></span> <span data-ttu-id="612bc-176">Es gibt noch viel zu tun, bevor Ihre app für den Microsoft Store bereit ist.</span><span class="sxs-lookup"><span data-stu-id="612bc-176">There's still more to do before your app is fully ready for the Microsoft Store.</span></span> <span data-ttu-id="612bc-177">Weitere Informationen zum gesamten Prozess für das Hinzufügen der UWP-App-Streaming-Installationsfunktion für Ihre App finden Sie in [diesem Blogbeitrag](https://blogs.msdn.microsoft.com/appinstaller/2017/03/15/uwp-streaming-app-installation/).</span><span class="sxs-lookup"><span data-stu-id="612bc-177">For more information on the complete process of adding UWP App Streaming Install to your app, check out [this blog post](https://blogs.msdn.microsoft.com/appinstaller/2017/03/15/uwp-streaming-app-installation/).</span></span>
