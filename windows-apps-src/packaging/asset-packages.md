---
author: laurenhughes
title: Einführung zu Bestandspaketen
description: Asset-Pakete sind ein Pakettyp, der als zentraler Speicherort für die gemeinsamen Dateien einer Anwendung fungiert. Dadurch wird die Notwendigkeit doppelter Dateien in allen Architekturpaketen effektiv eliminiert.
ms.author: lahugh
ms.date: 09/30/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, verpackung, paketlayout, bestandspaket
ms.localizationpriority: medium
ms.openlocfilehash: 8aafac1c1217ce082cd9d6176c530967f32e4cdd
ms.sourcegitcommit: fbdc9372dea898a01c7686be54bea47125bab6c0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/08/2018
ms.locfileid: "4428275"
---
# <a name="introduction-to-asset-packages"></a><span data-ttu-id="d2ce5-104">Einführung zu Bestandspaketen</span><span class="sxs-lookup"><span data-stu-id="d2ce5-104">Introduction to asset packages</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d2ce5-105">Wenn Sie Ihre App an den Store übermitteln möchten, müssen Sie sich an den [Windows-Support für Entwickler](https://developer.microsoft.com/windows/support) wenden und eine Genehmigung für die Verwendung von Bestandspaketen erhalten.</span><span class="sxs-lookup"><span data-stu-id="d2ce5-105">If you intend to submit your app to the Store, you need to contact [Windows developer support](https://developer.microsoft.com/windows/support) and get approval to use asset packages.</span></span>

<span data-ttu-id="d2ce5-106">Asset-Pakete sind ein Pakettyp, der als zentraler Speicherort für die gemeinsamen Dateien einer Anwendung fungiert. Dadurch wird die Notwendigkeit doppelter Dateien in allen Architekturpaketen effektiv eliminiert.</span><span class="sxs-lookup"><span data-stu-id="d2ce5-106">Asset packages are a type of package that act as a centralized location for an application’s common files – effectively eliminating the necessity for duplicated files throughout its architecture packages.</span></span> <span data-ttu-id="d2ce5-107">Bestandspakete ähneln den Ressourcenpaketen insofern, als beide statischen Inhalt enthalten, der für die Ausführung Ihrer App erforderlich ist. Sie unterscheiden sich jedoch dadurch, dass alle Bestandspakete immer heruntergeladen werden, unabhängig von der Systemarchitektur, Sprache oder Anzeigeskalierung des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="d2ce5-107">Asset packages are similar to resource packages in that they are both designed to contain static content needed for your app to run, but different in that all asset packages are always downloaded, regardless of the user’s system architecture, language, or display scale.</span></span>

![Bestandspaket-Bundle-Diagramm](images/primary-bundle.png)

<span data-ttu-id="d2ce5-109">Da Bestandspakete sämtliche architektur-, sprach- und skalierungsunabhängigen Dateien enthalten, führt ihre Nutzung zu einer verringerten Gesamtgröße der verpackten Apps (da diese Dateien nicht mehr dupliziert werden) und hilft Ihnen bei der Verwaltung des lokalen Speicherplatzes für große Apps sowie bei der Verwaltung der Pakete Ihrer App im Allgemeinen.</span><span class="sxs-lookup"><span data-stu-id="d2ce5-109">Because asset packages contain all the architecture, language, and scale agnostic files, leveraging asset packages results in a reduced overall packaged app size (since these files are no longer duplicated), helping you manage local development disk space usage for large apps and manage your app’s packages in general.</span></span> 

### <a name="how-do-asset-packages-affect-publishing"></a><span data-ttu-id="d2ce5-110">Wie wirken sich Bestandspakete auf die Veröffentlichung aus?</span><span class="sxs-lookup"><span data-stu-id="d2ce5-110">How do asset packages affect publishing?</span></span>
<span data-ttu-id="d2ce5-111">Der offensichtlichste Vorteil von Bestandspaketen ist die reduzierte Größe von verpackten Apps.</span><span class="sxs-lookup"><span data-stu-id="d2ce5-111">The most obvious benefit of asset packages is the reduced size of packaged apps.</span></span> <span data-ttu-id="d2ce5-112">Kleinere App-Pakete beschleunigen den Veröffentlichungsprozess der App, indem der Store weniger Dateien verarbeitet. Dies ist jedoch nicht der wichtigste Vorteil von Bestandspaketen.</span><span class="sxs-lookup"><span data-stu-id="d2ce5-112">Smaller app packages speed up the app’s publishing process by letting the Store process less files; however this is not the most important benefit of asset packages.</span></span>

<span data-ttu-id="d2ce5-113">Wenn ein Bestandspaket erstellt wird, können Sie angeben, ob das Ausführen des Pakets zugelassen werden soll.</span><span class="sxs-lookup"><span data-stu-id="d2ce5-113">When an asset package is created, you can specify whether the package should be allowed to execute.</span></span> <span data-ttu-id="d2ce5-114">Da Bestandspakete nur architekturunabhängige Dateien enthalten sollten, enthalten sie in der Regel keine .dll oder .exe-Dateien, sodass Bestandspakete in der Regel nicht ausgeführt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="d2ce5-114">Since asset packages should contain only architecture agnostic files, they generally don't contain any .dll or .exe files, so for asset packages typically don't need to execute.</span></span> <span data-ttu-id="d2ce5-115">Die Bedeutung dieser Unterscheidung besteht darin, dass während des Veröffentlichungsprozesses alle ausführbaren Pakete gescannt werden müssen, um sicherzustellen, dass sie keine Malware enthalten. Dieser Scanvorgang dauert bei größeren Paketen länger.</span><span class="sxs-lookup"><span data-stu-id="d2ce5-115">The importance of this distinction is that during the publishing process, all executable packages must be scanned to ensure that they do not contain malware, and this scanning process takes longer for larger packages.</span></span> <span data-ttu-id="d2ce5-116">Wenn ein Paket jedoch als nicht ausführbar gekennzeichnet ist, stellt die Installation der App sicher, dass die in diesem Paket enthaltenen Dateien nicht ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="d2ce5-116">However, if a package is designated as non-executable, the installation of the app will ensure that files contained in this package cannot be executed.</span></span> <span data-ttu-id="d2ce5-117">Mit dieser Garantie entfällt während der Veröffentlichung der App (und auch der Updates) die Notwendigkeit für eine vollständige Paketprüfung, und die Scanzeit für Malware wird erheblich reduziert. Dadurch wird die Veröffentlichung für Apps, die Bestandspakete verwenden, deutlich beschleunigt.</span><span class="sxs-lookup"><span data-stu-id="d2ce5-117">This guarantee eliminates the need for a complete package scan and will greatly reduce the malware scan time during the publication of the app (and for updates too) - thus making publishing significantly faster for apps that use asset packages.</span></span> <span data-ttu-id="d2ce5-118">Beachten Sie, dass die [flat-Bundle-app-Pakete](flat-bundles.md) auch verwendet werden muss, um diesen veröffentlichungsvorteil zu erhalten, da dies dem Store ist, jede .appx oder .msix-Paketdatei parallel zu verarbeiten ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="d2ce5-118">Note that [flat bundle app packages](flat-bundles.md) must also be used to get this publishing benefit since this is what allows the Store to process each .appx or .msix package file in parallel.</span></span> 


### <a name="should-i-use-asset-packages"></a><span data-ttu-id="d2ce5-119">Sollte ich Bestandspakete verwenden?</span><span class="sxs-lookup"><span data-stu-id="d2ce5-119">Should I use asset packages?</span></span>
<span data-ttu-id="d2ce5-120">Wenn Sie die Dateistruktur Ihrer App aktualisieren, um Bestandspakete zu nutzen, können Sie fassbare Vorteile erzielen, wie etwa reduzierte Paketgröße und schlankere Entwicklungsiterationen.</span><span class="sxs-lookup"><span data-stu-id="d2ce5-120">Updating the file structure of your app to leverage the use of asset packages can yield tangible benefits: reduced package size and leaner development iterations.</span></span> <span data-ttu-id="d2ce5-121">Wenn all Ihre Architekturpakete eine erhebliche Anzahl gemeinsam genutzter Dateien enthalten oder wenn der Großteil Ihrer App aus nicht ausführbaren Dateien besteht, wird dringend empfohlen, den Mehraufwand zu investieren, um auf die Verwendung von Bestandspaketen umzusteigen.</span><span class="sxs-lookup"><span data-stu-id="d2ce5-121">If your architecture packages all contain significant amount of files in common or if the bulk of your app is made up of non-executing files, it is highly recommended that you invest the extra time to convert to using asset packages.</span></span>

<span data-ttu-id="d2ce5-122">Es sollte jedoch darauf hingewiesen werden, dass Bestandspakete kein Mittel zum Erreichen der Optionalität von App-Inhalten sind.</span><span class="sxs-lookup"><span data-stu-id="d2ce5-122">However, it should be cautioned that asset packages are not a means to achieve app content optionality.</span></span> <span data-ttu-id="d2ce5-123">Bestandspaketdateien sind nicht optional und werden **immer** heruntergeladen, unabhängig von der Architektur, Sprache oder Skalierung des Zielgeräts. Optionale Inhalte, die Ihre App unterstützen soll, sollten mit [optionalen Paketen](optional-packages.md) implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="d2ce5-123">Asset package files are non-optional and will **always** be downloaded regardless of the target device’s architecture, language, or scale - any optional content that you want your app to support should be implemented using [optional packages](optional-packages.md).</span></span> 


### <a name="how-to-create-an-asset-package"></a><span data-ttu-id="d2ce5-124">So erstellen Sie ein Bestandpaket</span><span class="sxs-lookup"><span data-stu-id="d2ce5-124">How to create an asset package</span></span>
<span data-ttu-id="d2ce5-125">Der einfachste Weg zum Erstellen von Bestandspaketen ist die Verwendung des Verpackungslayouts.</span><span class="sxs-lookup"><span data-stu-id="d2ce5-125">The easiest way to create asset packages is using the packaging layout.</span></span> <span data-ttu-id="d2ce5-126">Allerdings können Bestandspakete auch mithilfe von MakeAppx.exe manuell erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="d2ce5-126">However, asset packages can also be created manually using MakeAppx.exe.</span></span> <span data-ttu-id="d2ce5-127">Um anzugeben, welche Dateien in das Bestandspaket aufgenommen werden sollen, müssen Sie eine „Zuordnungsdatei” erstellen.</span><span class="sxs-lookup"><span data-stu-id="d2ce5-127">To specify which files to include in the asset package, you will need to create a “mapping file”.</span></span> <span data-ttu-id="d2ce5-128">In diesem Beispiel ist „Video.mp4” die einzige Datei im Bestandspaket, es sollten hier jedoch alle Dateien des Bestandspakets aufgelistet sein.</span><span class="sxs-lookup"><span data-stu-id="d2ce5-128">In this example, the only file in the asset package is "Video.mp4”, but all the asset package’s files should be listed here.</span></span> <span data-ttu-id="d2ce5-129">Beachten Sie, dass der Bezeichner **ResourceDimensions** in **ResourceMetadata** für Bestandspakete (im Vergleich zu einer Zuordnungsdatei für Ressourcenpakete) weggelassen wird.</span><span class="sxs-lookup"><span data-stu-id="d2ce5-129">Note that the **ResourceDimensions** specifier in **ResourceMetadata** is omitted for asset packages (as compared to a mapping file for resource packages).</span></span>

```example 
[ResourceMetadata]
"ResourceId"        "Videos"

[Files]
"Video.mp4"         "Video.mp4"
```

<span data-ttu-id="d2ce5-130">Verwenden Sie diesen Befehl, um das Bestandspaket mit MakeAppx.exe zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="d2ce5-130">Use this command to create the asset package using MakeAppx.exe:</span></span> 

```syntax 
MakeAppx.exe pack /r /m AppxManifest.xml /f MappingFile.txt /p Videos.appx

...

MakeAppx.exe pack /r /m AppxManifest.xml /f MappingFile.txt /p Videos.msix

```
<span data-ttu-id="d2ce5-131">Es sollte hier angemerkt werden, dass alle im AppxManifest referenzierten Dateien (die Logodateien) nicht in Bestandspakete verschoben werden können; diese Dateien müssen über Architekturpakete hinweg dupliziert werden.</span><span class="sxs-lookup"><span data-stu-id="d2ce5-131">It should be noted here that all of the files referenced in the AppxManifest (the logo files) cannot be moved into asset packages – these files must be duplicated across architecture packages.</span></span> <span data-ttu-id="d2ce5-132">Bestandspakete sollten auch kein resources.pri enthalten. MRT kann nicht verwendet werden, um auf Bestandspaketdateien zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="d2ce5-132">Asset packages should also not contain a resources.pri; MRT cannot be used to access asset package files.</span></span> <span data-ttu-id="d2ce5-133">Weitere Informationen zum Zugriff auf Bestandspaketdateien und dazu, warum Bestandspakete die Installation Ihrer App auf einem NTFS-Laufwerk erfordern, finden Sie unter [Entwickeln mit Bestandspaketen und Paketfaltung](Package-Folding.md).</span><span class="sxs-lookup"><span data-stu-id="d2ce5-133">To learn more about how to access asset package files and why asset packages require your app to be installed to an NTFS drive, see [Developing with asset packages and package folding](Package-Folding.md).</span></span>

<span data-ttu-id="d2ce5-134">Um festzulegen, ob das Ausführen eines Bestandspakets zugelassen ist oder nicht, können Sie **[uap6:AllowExecution](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap6-allowexecution)** im **Eigenschaften**-Element des AppxManifest verwenden. Zudem müssen Sie dem übergeordneten **Paket**-Element **uap6** hinzufügen, damit es sich wie folgt ändert:</span><span class="sxs-lookup"><span data-stu-id="d2ce5-134">To control whether an asset package is allowed to execute or not, you can use **[uap6:AllowExecution](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap6-allowexecution)** in the **Properties** element of the AppxManifest You must also add **uap6** to the top level **Package** element to become the following:</span></span> 

```XML
<Package IgnorableNamespaces="uap uap6" 
xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6" 
xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

 <span data-ttu-id="d2ce5-135">Wenn nicht angegeben, ist der Standardwert für **AllowExecution** **true**. Setzen Sie ihn auf **false** für Bestandspakete ohne ausführbare Dateien, um die Veröffentlichung zu beschleunigen.</span><span class="sxs-lookup"><span data-stu-id="d2ce5-135">If not specified, the default value for **AllowExecution** is **true** – set it to **false** for asset packages with no executables to make publishing faster.</span></span>  



