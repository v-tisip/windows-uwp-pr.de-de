---
Description: In this scenario, we'll make a new app to represent our custom build system. We'll create a resource indexer and add strings and other kinds of resources to it. Then we'll generate and dump a PRI file.
title: 'Szenario 1: Generieren einer PRI-Datei aus Zeichenfolgenressourcen und Ressourcendateien'
template: detail.hbs
ms.date: 05/07/2018
ms.topic: article
keywords: Windows10, UWP, Ressourcen, Bild, Element, MRT, Qualifizierer
ms.localizationpriority: medium
ms.openlocfilehash: 9b14e413a5629dfb5447750e32c42c4efafef8fa
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8931447"
---
# <a name="scenario-1-generate-a-pri-file-from-string-resources-and-asset-files"></a><span data-ttu-id="a9ff9-103">Szenario 1: Generieren einer PRI-Datei aus Zeichenfolgenressourcen und Ressourcendateien</span><span class="sxs-lookup"><span data-stu-id="a9ff9-103">Scenario 1: Generate a PRI file from string resources and asset files</span></span>
<span data-ttu-id="a9ff9-104">In diesem Szenario verwenden wir die [APIs zur Paketressourcenindizierung (PRI)](https://msdn.microsoft.com/library/windows/desktop/mt845690), um eine neue App zur Darstellung unseres benutzerdefinierten Buildsystems zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-104">In this scenario, we'll use the [package resource indexing (PRI) APIs](https://msdn.microsoft.com/library/windows/desktop/mt845690) to make a new app to represent our custom build system.</span></span> <span data-ttu-id="a9ff9-105">Denken Sie daran: Der Zweck dieses benutzerdefinierten Buildsystems besteht darin, PRI-Dateien für eine Ziel-UWP-App zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-105">The purpose of this custom build system, remember, is to create PRI files for a target UWP app.</span></span> <span data-ttu-id="a9ff9-106">Im Rahmen dieser exemplarischen Vorgehensweise erstellen wir also einige Beispielressourcendateien (mit Zeichenfolgen und anderen Arten von Ressourcen), um die Ressourcen dieser Ziel-UWP-App abzubilden.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-106">So, as part of this walkthrough, we'll create some sample resource files (containing strings, and other kinds of resources) to represent that target UWP app's resources.</span></span>

## <a name="new-project"></a><span data-ttu-id="a9ff9-107">Neues Projekt</span><span class="sxs-lookup"><span data-stu-id="a9ff9-107">New project</span></span>
<span data-ttu-id="a9ff9-108">Erstellen Sie zunächst ein neues Projekt in Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-108">Begin by creating a new project in Microsoft Visual Studio.</span></span> <span data-ttu-id="a9ff9-109">Erstellen Sie ein Anwendungsprojekt der **Visual C++-Windows-Konsole**, und nennen Sie es *CBSConsoleApp*.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-109">Create a **Visual C++ Windows Console Application** project, and name it *CBSConsoleApp* (for "custom build system console app").</span></span>

<span data-ttu-id="a9ff9-110">Wählen Sie *x64* aus der Dropdownliste **Lösungsplattformen**.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-110">Choose *x64* from the **Solution Platforms** drop-down.</span></span>

## <a name="headers-static-library-and-dll"></a><span data-ttu-id="a9ff9-111">Header, statische Bibliothek und DLL</span><span class="sxs-lookup"><span data-stu-id="a9ff9-111">Headers, static library, and dll</span></span>
<span data-ttu-id="a9ff9-112">Die PRI-APIs werden in der Headerdatei „MrmResourceIndexer.h“ deklariert (diese wird unter `%ProgramFiles(x86)%\Windows Kits\10\Include\<WindowsTargetPlatformVersion>\um\` installiert).</span><span class="sxs-lookup"><span data-stu-id="a9ff9-112">The PRI APIs are declared in the MrmResourceIndexer.h header file (which is installed to `%ProgramFiles(x86)%\Windows Kits\10\Include\<WindowsTargetPlatformVersion>\um\`).</span></span> <span data-ttu-id="a9ff9-113">Öffnen Sie die Datei `CBSConsoleApp.cpp`, und fügen Sie den Header sowie einige andere Header hinzu, die Sie benötigen.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-113">Open the file `CBSConsoleApp.cpp` and include the header along with some other headers that you'll need.</span></span>

```cppwinrt
#include <string>
#include <windows.h>
#include <MrmResourceIndexer.h>
```

<span data-ttu-id="a9ff9-114">Die APIs sind in „MrmSupport.dll“ implementiert. Diese rufen Sie über die Verknüpfung zur statischen Bibliothek „MrmSupport.lib“ auf.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-114">The APIs are implemented in MrmSupport.dll, which you access by linking to the static library MrmSupport.lib.</span></span> <span data-ttu-id="a9ff9-115">Öffnen Sie die **Eigenschaften** des Projekts, klicken Sie auf **Linker** > **Eingabe**, bearbeiten Sie **Zusätzliche Abhängigkeiten**, und fügen Sie `MrmSupport.lib` hinzu.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-115">Open your project's **Properties**, click **Linker** > **Input**, edit **AdditionalDependencies** and add `MrmSupport.lib`.</span></span>

<span data-ttu-id="a9ff9-116">Erstellen Sie die Projektmappe, und kopieren Sie `MrmSupport.dll` von `C:\Program Files (x86)\Windows Kits\10\bin\<WindowsTargetPlatformVersion>\x64\` in den Build-Ausgabeordner (wahrscheinlich `C:\Users\%USERNAME%\source\repos\CBSConsoleApp\x64\Debug\`).</span><span class="sxs-lookup"><span data-stu-id="a9ff9-116">Build the Solution, and then copy `MrmSupport.dll` from `C:\Program Files (x86)\Windows Kits\10\bin\<WindowsTargetPlatformVersion>\x64\` to your build output folder (probably `C:\Users\%USERNAME%\source\repos\CBSConsoleApp\x64\Debug\`).</span></span>

<span data-ttu-id="a9ff9-117">Fügen Sie die folgende Hilfsfunktion `CBSConsoleApp.cpp` hinzu, da wir diese benötigen.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-117">Add the following helper function to `CBSConsoleApp.cpp`, since we'll be needing it.</span></span>

```cppwinrt
inline void ThrowIfFailed(HRESULT hr)
{
    if (FAILED(hr))
    {
        // Set a breakpoint on this line to catch Win32 API errors.
        throw new std::exception();
    }
}
```

<span data-ttu-id="a9ff9-118">Fügen Sie in der `main()`-Funktion Aufrufe zur Initialisierung und Aufhebung der Initialisierung von COM hinzu.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-118">In the `main()` function, add calls to initialize and uninitialize COM.</span></span>

```cppwinrt
int main()
{
    ::ThrowIfFailed(::CoInitializeEx(nullptr, COINIT_MULTITHREADED));
    
    // More code will go here.
    
    ::CoUninitialize();
}
```

## <a name="resource-files-belonging-to-the-target-uwp-app"></a><span data-ttu-id="a9ff9-119">Ressourcendateien, die zur Ziel-UWP-App gehören</span><span class="sxs-lookup"><span data-stu-id="a9ff9-119">Resource files belonging to the target UWP app</span></span>
<span data-ttu-id="a9ff9-120">Wir benötigen nun einige Beispielressourcendateien (mit Zeichenfolgen und anderen Arten von Ressourcen), um die Ressourcen dieser Ziel-UWP-App abzubilden.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-120">Now we'll need some sample resource files (containing strings, and other kinds of resources) to represent the target UWP app's resources.</span></span> <span data-ttu-id="a9ff9-121">Diese können sich natürlich an einem beliebigen Ort im Dateisystem befinden.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-121">These, of course, can be located anywhere on your file system.</span></span> <span data-ttu-id="a9ff9-122">Für diese exemplarische Vorgehensweise empfiehlt es sich jedoch, sie im Projektordner von CBSConsoleApp zu platzieren, damit alles an einem zentralen Ort abgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-122">But for this walkthrough it'll be convenient to put them in the project folder of CBSConsoleApp so that everything is in one place.</span></span> <span data-ttu-id="a9ff9-123">Sie müssen diese Ressourcendateien nur dem Dateisystem hinzuzufügen. Fügen Sie sie nicht dem Projekt „CBSConsoleApp“ hinzu.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-123">You only need to add these resource files to the file system; don't add them to the CBSConsoleApp project.</span></span>

<span data-ttu-id="a9ff9-124">Fügen Sie im gleichen Ordner, der `CBSConsoleApp.vcxproj` enthält, einen neuen Unterordner namens `UWPAppProjectRootFolder` hinzu.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-124">Inside the same folder that contains `CBSConsoleApp.vcxproj`, add a new subfolder named `UWPAppProjectRootFolder`.</span></span> <span data-ttu-id="a9ff9-125">Erstellen Sie in diesem neuen Unterordner diese Beispielressourcendateien.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-125">Inside that new subfolder, create these sample resource files.</span></span>

### <a name="uwpappprojectrootfoldersample-imagepng"></a><span data-ttu-id="a9ff9-126">\UWPAppProjectRootFolder\sample-image.png</span><span class="sxs-lookup"><span data-stu-id="a9ff9-126">\UWPAppProjectRootFolder\sample-image.png</span></span>
<span data-ttu-id="a9ff9-127">Diese Datei kann ein beliebiges PNG-Bild enthalten.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-127">This file can contain any PNG image.</span></span>

### <a name="uwpappprojectrootfolderresourcesresw"></a><span data-ttu-id="a9ff9-128">\UWPAppProjectRootFolder\resources.resw</span><span class="sxs-lookup"><span data-stu-id="a9ff9-128">\UWPAppProjectRootFolder\resources.resw</span></span>
```xml
<?xml version="1.0"?>
<root>
    <data name="LocalizedString1">
        <value>LocalizedString1-neutral</value>
    </data>
    <data name="LocalizedString2">
        <value>LocalizedString2-neutral</value>
    </data>
    <data name="NeutralOnlyString">
        <value>NeutralOnlyString-neutral</value>
    </data>
</root>
```

### <a name="uwpappprojectrootfolderde-deresourcesresw"></a><span data-ttu-id="a9ff9-129">\UWPAppProjectRootFolder\de-DE\resources.resw</span><span class="sxs-lookup"><span data-stu-id="a9ff9-129">\UWPAppProjectRootFolder\de-DE\resources.resw</span></span>
```xml
<?xml version="1.0"?>
<root>
    <data name="LocalizedString2">
        <value>LocalizedString2-de-DE</value>
    </data>
</root>
```

### <a name="uwpappprojectrootfolderen-usresourcesresw"></a><span data-ttu-id="a9ff9-130">\UWPAppProjectRootFolder\en-US\resources.resw</span><span class="sxs-lookup"><span data-stu-id="a9ff9-130">\UWPAppProjectRootFolder\en-US\resources.resw</span></span>
```xml
<?xml version="1.0"?>
<root>
    <data name="LocalizedString1">
        <value>LocalizedString1-en-US</value>
    </data>
    <data name="EnOnlyString">
        <value>EnOnlyString-en-US</value>
    </data>
</root>
```

## <a name="index-the-resources-and-create-a-pri-file"></a><span data-ttu-id="a9ff9-131">Indizieren der Ressourcen und Erstellen einer PRI-Datei</span><span class="sxs-lookup"><span data-stu-id="a9ff9-131">Index the resources, and create a PRI file</span></span>
<span data-ttu-id="a9ff9-132">Deklarieren Sie in der `main()`-Funktion vor dem Aufruf zur COM-Initialisierung einige Zeichenfolgen, die wir benötigen, und erstellen Sie auch den Ausgabeordner, in dem wir die PRI-Datei generieren.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-132">In the `main()` function, before the call to initialize COM, declare some strings that we'll need, and also create the output folder in which we'll be generating our PRI file.</span></span>

```cppwinrt
std::wstring projectRootFolderUWPApp{ L"UWPAppProjectRootFolder" };
std::wstring generatedPRIsFolder{ projectRootFolderUWPApp + L"\\Generated PRIs" };
std::wstring filePathPRI{ generatedPRIsFolder + L"\\resources.pri" };
std::wstring filePathPRIDumpBasic{ generatedPRIsFolder + L"\\resources-pri-dump-basic.xml" };

::CreateDirectory(generatedPRIsFolder.c_str(), nullptr);
```

<span data-ttu-id="a9ff9-133">Deklarieren Sie unmittelbar nach dem Aufruf zur COM-Initialisierung einen Ressourcenindexer-Handle, und rufen Sie dann [**MrmCreateResourceIndexer**]() auf, um einen Ressourcenindexer zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-133">Immediately after the call to Initialize COM, declare a resource indexer handle and then call [**MrmCreateResourceIndexer**]() to create a resource indexer.</span></span>

```cppwinrt
MrmResourceIndexerHandle indexer;
::ThrowIfFailed(::MrmCreateResourceIndexer(
    L"OurUWPApp",
    projectRootFolderUWPApp.c_str(),
    MrmPlatformVersion::MrmPlatformVersion_Windows10_0_0_0,
    L"language-en_scale-100_contrast-standard",
    &indexer));
```

<span data-ttu-id="a9ff9-134">Hier werden die Argumente erläutert, die an **MrmCreateResourceIndexer** übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-134">Here's an explanation of the arguments being passed to **MrmCreateResourceIndexer**.</span></span>

- <span data-ttu-id="a9ff9-135">Der Paketfamilienname der Ziel-UWP-App, der als Name der Ressourcenzuordnung verwendet wird, wenn wir später eine PRI-Datei aus diesem Ressourcenindexer generieren.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-135">The package family name of our target UWP app, which will be used as the resource map name when we later generate a PRI file from this resource indexer.</span></span>
- <span data-ttu-id="a9ff9-136">Der Projektstamm der Ziel-UWP-App.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-136">The project root of our target UWP app.</span></span> <span data-ttu-id="a9ff9-137">Mit anderen Worten: der Pfad zu unserer Ressourcendateien.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-137">In other words, the path to our resource files.</span></span> <span data-ttu-id="a9ff9-138">Wir geben diesen an, damit wir dann Pfade relativ zu diesem Stamm in nachfolgenden API-Aufrufe an den gleichen Ressourcenindexer angeben können.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-138">We specify this so that we can then specify paths relative to that root in subsequent API calls to the same resource indexer.</span></span>
- <span data-ttu-id="a9ff9-139">Die Version von Windows, die wir anvisieren.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-139">The version of Windows that we want to target.</span></span>
- <span data-ttu-id="a9ff9-140">Eine Liste der Standardressourcenqualifizierer.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-140">A list of default resource qualifiers.</span></span>
- <span data-ttu-id="a9ff9-141">Ein Zeiger auf unseren Ressourcenindexer-Handle, sodass die Funktion diesen festlegen kann.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-141">A pointer to our resource indexer handle so that the function can set it.</span></span>

<span data-ttu-id="a9ff9-142">Im nächsten Schritt fügen wir unsere Ressourcen dem Ressourcenindexer hinzu, den wir gerade erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-142">The next step is to add our resources to the resource indexer that we just created.</span></span> `resources.resw` <span data-ttu-id="a9ff9-143">ist eine Ressourcendatei (.resw), die die neutralen Zeichenfolgen für die Ziel-UWP-App enthält.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-143">is a Resources File (.resw) that contains the neutral strings for our target UWP app.</span></span> <span data-ttu-id="a9ff9-144">Führen Sie (in diesem Thema) einen Bildlauf nach oben durch, wenn Sie den Inhalt dieser Datei anzeigen möchten.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-144">Scroll up (in this topic) if you want to see its contents.</span></span> `de-DE\resources.resw` <span data-ttu-id="a9ff9-145">enthält unsere deutschen Zeichenfolgen und `en-US\resources.resw` enthält unsere englischen Zeichenfolgen.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-145">contains our German strings, and `en-US\resources.resw` our English strings.</span></span> <span data-ttu-id="a9ff9-146">Zum Hinzufügen der Zeichenfolgenressourcen innerhalb einer Ressourcendatei zu einem Ressourcenindexer rufen Sie [**MrmIndexResourceContainerAutoQualifiers**]() auf.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-146">To add the string resources inside a Resources File to a resource indexer, you call [**MrmIndexResourceContainerAutoQualifiers**]().</span></span> <span data-ttu-id="a9ff9-147">Als Drittes rufen wir die [**MrmIndexFile**]()-Funktion zu einer Datei auf, die eine neutrale Bildressource für den Ressourcenindexer enthält.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-147">Thirdly, we call the [**MrmIndexFile**]() function to a file containing a neutral image resource to the resource indexer.</span></span>

```cppwinrt
::ThrowIfFailed(::MrmIndexResourceContainerAutoQualifiers(indexer, L"resources.resw"));
::ThrowIfFailed(::MrmIndexResourceContainerAutoQualifiers(indexer, L"de-DE\\resources.resw"));
::ThrowIfFailed(::MrmIndexResourceContainerAutoQualifiers(indexer, L"en-US\\resources.resw"));
::ThrowIfFailed(::MrmIndexFile(indexer, L"ms-resource:///Files/sample-image.png", L"sample-image.png", L""));
```

<span data-ttu-id="a9ff9-148">Im Aufruf an **MrmIndexFile** ist der Wert „ms-resource:///Files/sample-image.png“ der Ressourcen-URI.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-148">In the call to **MrmIndexFile**, the value L"ms-resource:///Files/sample-image.png" is the resource uri.</span></span> <span data-ttu-id="a9ff9-149">Das erste Pfadsegment ist „Dateien“. Dieses wird als Name der Ressourcenzuordnung-Unterstruktur verwendet, wenn wir später eine PRI-Datei aus diesem Ressourcenindexer generieren.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-149">The first path segment is "Files", and that's what will be used as the resource map subtree name when we later generate a PRI file from this resource indexer.</span></span>

<span data-ttu-id="a9ff9-150">Nachdem wir den Ressourcenindexer über unsere Ressourcendateien informiert haben, ist es an der Zeit, dass dieser uns eine PRI-Datei auf dem Datenträger generiert, und zwar durch Aufrufen der [**MrmCreateResourceFile**]()-Funktion.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-150">Having briefed the resource indexer about our resource files, it's time to have it generate us a PRI file on disk by calling the [**MrmCreateResourceFile**]() function.</span></span>

```cppwinrt
::ThrowIfFailed(::MrmCreateResourceFile(indexer, MrmPackagingModeStandaloneFile, MrmPackagingOptionsNone, generatedPRIsFolder.c_str()));
```

<span data-ttu-id="a9ff9-151">Zu diesem Zeitpunkt wurde eine PRI-Datei mit dem Namen `resources.pri` in einem Ordner namens `Generated PRIs` erstellt.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-151">At this point, a PRI file named `resources.pri` has been created inside a folder named `Generated PRIs`.</span></span> <span data-ttu-id="a9ff9-152">Nun, da wir mit dem Ressourcenindexer fertig sind, rufen wir [**MrmDestroyIndexerAndMessages**]() auf, um den Handle zu löschen und alle ihm zugewiesenen Computerressourcen freizugeben.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-152">Now that we're done with the resource indexer, we call [**MrmDestroyIndexerAndMessages**]() to destroy its handle and release any machine resources that it allocated.</span></span>

```cppwinrt
::ThrowIfFailed(::MrmDestroyIndexerAndMessages(indexer));
```

<span data-ttu-id="a9ff9-153">Da eine PRI-Datei ein binäres Format hat, können wir das soeben Generierte leichter anzeigen, wenn wir die binäre PRI-Datei in ihr XML-Äquivalent sichern.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-153">Since a PRI file is binary, it's going to be easier to view what we've just generated if we dump the binary PRI file to its XML equivalent.</span></span> <span data-ttu-id="a9ff9-154">Dies erreichen wir durch Aufrufen von [**MrmDumpPriFile**]().</span><span class="sxs-lookup"><span data-stu-id="a9ff9-154">A call to [**MrmDumpPriFile**]()does just that.</span></span>

```cppwinrt
::ThrowIfFailed(::MrmDumpPriFile(filePathPRI.c_str(), nullptr, MrmDumpType::MrmDumpType_Basic, filePathPRIDumpBasic.c_str()));
```

<span data-ttu-id="a9ff9-155">Hier werden die Argumente erläutert, die an **MrmDumpPriFile** übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-155">Here's an explanation of the arguments being passed to **MrmDumpPriFile**.</span></span>

- <span data-ttu-id="a9ff9-156">Der Pfad zur PRI-Datei, die gesichert werden soll.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-156">The path to the PRI file to dump.</span></span> <span data-ttu-id="a9ff9-157">In diesem Aufruf verwenden wir nicht den Ressourcenindexer (wir haben diesen gerade gelöscht). Folglich müssen wir einen vollständigen Dateipfad angeben.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-157">We're not using the resource indexer in this call (we just destroyed it), so we need to specify a full file path.</span></span>
- <span data-ttu-id="a9ff9-158">Keine Schemadatei.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-158">No schema file.</span></span> <span data-ttu-id="a9ff9-159">Was ein Schema ist, wird weiter unten im Thema erläutert.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-159">We'll discuss what a schema is later in the topic.</span></span>
- <span data-ttu-id="a9ff9-160">Nur die grundlegenden Informationen.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-160">Just the basic info.</span></span>
- <span data-ttu-id="a9ff9-161">Der Pfad einer zu erstellenden XML-Datei.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-161">The path of an XML file to create.</span></span>

<span data-ttu-id="a9ff9-162">Dies enthält die PRI-Datei, hier in XML gesichert.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-162">This is what the PRI file, dumped to XML here, contains.</span></span>

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<PriInfo>
    <ResourceMap name="OurUWPApp" version="1.0" primary="true">
        <Qualifiers>
            <Language>en-US,de-DE</Language>
        </Qualifiers>
        <ResourceMapSubtree name="Files">
            <NamedResource name="sample-image.png" uri="ms-resource://OurUWPApp/Files/sample-image.png">
                <Candidate type="Path">
                    <Value>sample-image.png</Value>
                </Candidate>
            </NamedResource>
        </ResourceMapSubtree>
        <ResourceMapSubtree name="resources">
            <NamedResource name="EnOnlyString" uri="ms-resource://OurUWPApp/resources/EnOnlyString">
                <Candidate qualifiers="Language-en-US" isDefault="true" type="String">
                    <Value>EnOnlyString-en-US</Value>
                </Candidate>
            </NamedResource>
            <NamedResource name="LocalizedString1" uri="ms-resource://OurUWPApp/resources/LocalizedString1">
                <Candidate qualifiers="Language-en-US" isDefault="true" type="String">
                    <Value>LocalizedString1-en-US</Value>
                </Candidate>
                <Candidate type="String">
                    <Value>LocalizedString1-neutral</Value>
                </Candidate>
            </NamedResource>
            <NamedResource name="LocalizedString2" uri="ms-resource://OurUWPApp/resources/LocalizedString2">
                <Candidate qualifiers="Language-de-DE" type="String">
                    <Value>LocalizedString2-de-DE</Value>
                </Candidate>
                <Candidate type="String">
                    <Value>LocalizedString2-neutral</Value>
                </Candidate>
            </NamedResource>
            <NamedResource name="NeutralOnlyString" uri="ms-resource://OurUWPApp/resources/NeutralOnlyString">
                <Candidate type="String">
                    <Value>NeutralOnlyString-neutral</Value>
                </Candidate>
            </NamedResource>
        </ResourceMapSubtree>
    </ResourceMap>
</PriInfo>
```

<span data-ttu-id="a9ff9-163">Die Informationen beginnen mit einer Ressourcenzuordnung, deren Namen dem Paketfamiliennamen unserer Ziel-UWP-App entspricht.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-163">The info begins with a resource map, which is named with the package family name of our target UWP app.</span></span> <span data-ttu-id="a9ff9-164">Von der Ressourcenzuordnung eingeschlossen sind zwei Ressourcenzuordnungsteilstrukturen: eine für die Dateiressourcen, die wir indiziert haben, und eine andere für unsere Zeichenfolgenressourcen.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-164">Enclosed by the resource map are two resource map subtrees: one for the file resources that we indexed, and another for our string resources.</span></span> <span data-ttu-id="a9ff9-165">Beachten Sie, wie der Paketfamilienname in alle Ressourcen-URIs eingefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-165">Notice how the package family name has been inserted into all of the resource URIs.</span></span>

<span data-ttu-id="a9ff9-166">Die erste Zeichenfolgenressource lautet *EnOnlyString* aus `en-US\resources.resw`. Dieser umfasst nur einen Kandidaten (der dem Qualifizierer *language-en-US* entspricht).</span><span class="sxs-lookup"><span data-stu-id="a9ff9-166">The first string resource is *EnOnlyString* from `en-US\resources.resw`, and it has just one candidate (which matches the *language-en-US* qualifier).</span></span> <span data-ttu-id="a9ff9-167">Anschließend folgt *LocalizedString1* sowohl aus `resources.resw` als auch aus `en-US\resources.resw`.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-167">Next comes *LocalizedString1* from both `resources.resw` and `en-US\resources.resw`.</span></span> <span data-ttu-id="a9ff9-168">Folglich gibt es zwei Kandidaten: einen übereinstimmenden *language-en-US* und einen neutralen Fallback-Kandidaten, der mit einem beliebigen Kontext übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-168">Consequently, it has two candidates: one matching *language-en-US*, and a fallback neutral candidate that matches any context.</span></span> <span data-ttu-id="a9ff9-169">Analog dazu verfügt *LocalizedString2* über zwei Kandidaten: *language-de-DE* und neutral.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-169">Similarly, *LocalizedString2* has two candidates: *language-de-DE*, and neutral.</span></span> <span data-ttu-id="a9ff9-170">Und schließlich ist *NeutralOnlyString* nur in neutraler Form vorhanden.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-170">And, finally, *NeutralOnlyString* only exists in neutral form.</span></span> <span data-ttu-id="a9ff9-171">Dieser Name soll deutlich machen, dass er nicht lokalisiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-171">I gave it that name to make it clear that it's not meant to be localized.</span></span>

## <a name="summary"></a><span data-ttu-id="a9ff9-172">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="a9ff9-172">Summary</span></span>
<span data-ttu-id="a9ff9-173">In diesem Szenario haben wir gezeigt, wie Sie die [APIs zur Paketressourcenindizierung (PRI](https://msdn.microsoft.com/library/windows/desktop/mt845690) verwenden, um einen Ressourcenindexer zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-173">In this scenario, we showed how to use the [package resource indexing (PRI) APIs](https://msdn.microsoft.com/library/windows/desktop/mt845690) to create a resource indexer.</span></span> <span data-ttu-id="a9ff9-174">Wir haben dem Ressourcenindexer Zeichenfolgenressourcen und Ressourcendateien hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-174">We added string resources and asset files to the resource indexer.</span></span> <span data-ttu-id="a9ff9-175">Anschließend haben wir mit dem Ressourcenindexer eine binäre PRI-Datei generiert.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-175">Then, we used the resource indexer to generated a binary PRI file.</span></span> <span data-ttu-id="a9ff9-176">Und schließlich haben wir die binäre PRI-Datei im XML-Format gesichert, sodass wir überprüfen konnten, dass sie die erwarteten Informationen enthält.</span><span class="sxs-lookup"><span data-stu-id="a9ff9-176">And finally we dumped the binary PRI file in the form of XML so that we could confirm that it contains the info we expected.</span></span>

## <a name="important-apis"></a><span data-ttu-id="a9ff9-177">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="a9ff9-177">Important APIs</span></span>
* [<span data-ttu-id="a9ff9-178">Referenz für die Paketressourcenindizierung (PRI)</span><span class="sxs-lookup"><span data-stu-id="a9ff9-178">Package resource indexing (PRI) reference</span></span>](https://msdn.microsoft.com/library/windows/desktop/mt845690)

## <a name="related-topics"></a><span data-ttu-id="a9ff9-179">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="a9ff9-179">Related topics</span></span>
* [<span data-ttu-id="a9ff9-180">APIs zur Paketressourcenindizierung (PRI) und benutzerdefinierte Buildsysteme</span><span class="sxs-lookup"><span data-stu-id="a9ff9-180">Package resource indexing (PRI) APIs and custom build systems</span></span>](pri-apis-custom-build-systems.md)
