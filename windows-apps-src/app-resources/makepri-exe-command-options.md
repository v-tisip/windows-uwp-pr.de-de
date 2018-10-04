---
author: stevewhims
Description: MakePri.exe has the set of commands createconfig, dump, new, resourcepack, and versioned. This topic details their use.
title: Befehlszeilenoptionen für MakePri.exe
template: detail.hbs
ms.author: stwhi
ms.date: 04/10/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Ressourcen, Bild, Element, MRT, Qualifizierer
ms.localizationpriority: medium
ms.openlocfilehash: c0a3892348baff56bbef8d40dd9aade4e612c50d
ms.sourcegitcommit: 5c9a47b135c5f587214675e39c1ac058c0380f4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2018
ms.locfileid: "4357904"
---
# <a name="makepriexe-command-line-options"></a><span data-ttu-id="a389b-103">Befehlszeilenoptionen für MakePRI.exe</span><span class="sxs-lookup"><span data-stu-id="a389b-103">MakePri.exe command-line options</span></span>

<span data-ttu-id="a389b-104">[MakePri.exe](compile-resources-manually-with-makepri.md) akzeptiert die Befehle `createconfig`, `dump`, `new`, `resourcepack` und `versioned`.</span><span class="sxs-lookup"><span data-stu-id="a389b-104">[MakePri.exe](compile-resources-manually-with-makepri.md) has the set of commands `createconfig`, `dump`, `new`, `resourcepack`, and `versioned`.</span></span> <span data-ttu-id="a389b-105">In diesem Thema werden die Befehlszeilenoptionen für diese Befehle erläutert.</span><span class="sxs-lookup"><span data-stu-id="a389b-105">This topic details the command-line options for their use.</span></span>

> [!NOTE]
> <span data-ttu-id="a389b-106">MakePri.exe wird installiert, wenn Sie im **Windows SDK für UWP-Apps verwaltet** Option während der Installation im Windows Software Development Kit aktivieren.</span><span class="sxs-lookup"><span data-stu-id="a389b-106">MakePri.exe is installed when you check the **Windows SDK for UWP Managed Apps** option while installing the Windows Software Development Kit.</span></span> <span data-ttu-id="a389b-107">Es installiert ist, um den Pfad `%WindowsSdkDir%bin\<WindowsTargetPlatformVersion>\x64\makepri.exe` (ebenso wie in den Ordnern für die anderen Architekturen).</span><span class="sxs-lookup"><span data-stu-id="a389b-107">It is installed to the path `%WindowsSdkDir%bin\<WindowsTargetPlatformVersion>\x64\makepri.exe` (as well as in folders named for the other architectures).</span></span> <span data-ttu-id="a389b-108">Beispiel: `C:\Program Files (x86)\Windows Kits\10\bin\10.0.17713.0\x64\makepri.exe`.</span><span class="sxs-lookup"><span data-stu-id="a389b-108">For example, `C:\Program Files (x86)\Windows Kits\10\bin\10.0.17713.0\x64\makepri.exe`.</span></span>

## <a name="makepri-commands"></a><span data-ttu-id="a389b-109">MakePri-Befehle</span><span class="sxs-lookup"><span data-stu-id="a389b-109">MakePri commands</span></span>

<span data-ttu-id="a389b-110">Führen Sie `MakePri.exe help` aus, um die Befehle anzuzeigen, die Sie mit MakePri.exe verwenden können.</span><span class="sxs-lookup"><span data-stu-id="a389b-110">Run `MakePri.exe help` to see the commands that you can use with MakePri.exe.</span></span>

```
C:\>makepri help

Usage:
------
    MakePri.exe <command> [options]

Example:
--------
    MakePri.exe new /cf C:\MyApp\priconfig.xml /pr C:\MyApp\src\ /in PackageName

Description:
------------
    Creates, dumps, and performs utility functions on a PRI file. A PRI file is 
    an index of application resources, such as strings and image files.

Command Options:
----------------
    MakePri.exe createconfig   Creates a PRI config file for use with other
                               commands
    MakePri.exe dump           Dumps the contents of a PRI file
    MakePri.exe new            Creates a new PRI file from scratch
    MakePri.exe resourcepack   Creates a PRI file that contains additional
                               resource variants for a base PRI file
    MakePri.exe versioned      Creates a PRI file based on a previous version

Help:
-----
    MakePri.exe help           Show this help page
    MakePri.exe <command> /?   Shows detailed help for <command>

    For example,
    MakePri.exe createconfig /?
```

## <a name="createconfig-command"></a><span data-ttu-id="a389b-111">Createconfig-Befehl</span><span class="sxs-lookup"><span data-stu-id="a389b-111">Createconfig command</span></span>

<span data-ttu-id="a389b-112">Der Befehl `createconfig` erstellt eine neue, initialisierte PRI-Konfigurationsdatei, in der die Standardwerte für die von Ihnen angegebenen Qualifizierer enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="a389b-112">The `createconfig` command creates a new, initialized PRI config file defining the qualifier defaults that you specify.</span></span> <span data-ttu-id="a389b-113">Führen Sie `MakePri.exe createconfig /?` aus, um detaillierte Hilfe für diesen Befehl anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a389b-113">Run `MakePri.exe createconfig /?` to see detailed help for this command.</span></span>

```
C:\>makepri createconfig /?

Usage:
------
    MakePri.exe createconfig /cf <config file destination> /dq
    <default qualifiers> [options]

Example:
--------
    MakePri.exe createconfig /cf C:\MyApp\priconfig.xml /dq lang-en-US /o /pv 10.0.0

Description:
------------
    Creates a PRI configuration file at <config file destination> with default 
    qualifiers specified by <default qualifiers>. Multiple qualifiers are separated 
    by underscores (_)

Required Parameters:
--------------------
    /ConfigXml(cf)    : <FILEPATH> Configuration file output location
    /Default(dq)      : <QUALIFIERS> The default qualifiers to set in the
                        configuration file. A language qualifier is required

Options:
--------
    /ExtensionDll(ex) : <FILEPATH> Location of the Resource Management System
                        environment extension DLL. This DLL must be signed by
                        a Microsoft-issued certificate. Default is an empty path
                        (no DLL will be used)
    /Overwrite(o)     : Overwrite an existing output file of the same name
                        without prompting
    /Platform(pv)     : <VERSION> Platform version to use for generated
                        configuration file

    FILEPATH          - a path to a file, either relative to the current
                        directory or absolute
    QUALIFIERS        - a valid qualifier token
                        (for example, lang-en-US_scale-100_contrast-high)

Help:
-----
    /Help(h, ?)       : Display the usage help text
```

## <a name="dump-command"></a><span data-ttu-id="a389b-114">Dump-Befehl</span><span class="sxs-lookup"><span data-stu-id="a389b-114">Dump command</span></span>

<span data-ttu-id="a389b-115">Der Befehl `dump` gibt den Dump einer XML-Datei aus, die eine Liste aller Ressourcen in einer angegebenen PRI-Datei enthält.</span><span class="sxs-lookup"><span data-stu-id="a389b-115">The `dump` command outputs a dumped xml file containing a list of all resources in a specified PRI file.</span></span> <span data-ttu-id="a389b-116">Führen Sie `MakePri.exe dump /?` aus, um detaillierte Hilfe für diesen Befehl anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a389b-116">Run `MakePri.exe dump /?` to see detailed help for this command.</span></span>

> [!NOTE]
> <span data-ttu-id="a389b-117">Ein schemafreies Ressourcenpaket ist ein Ressourcenpaket, das mit dem Schalter *omitSchemaFromResourcePacks* in der PRI-Konfigurationsdatei erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="a389b-117">A schema-free resource pack is one that was created with the *omitSchemaFromResourcePacks* switch in the PRI config file.</span></span> <span data-ttu-id="a389b-118">Um ein schemafreies Ressourcenpaket zu sichern, verwenden Sie den Schalter `/es <main_package_PRI_file>`.</span><span class="sxs-lookup"><span data-stu-id="a389b-118">To dump a schema-free resource pack, use the switch `/es <main_package_PRI_file>`.</span></span> <span data-ttu-id="a389b-119">Wenn Sie die Hauptdatei nicht angeben, wird eine Fehlermeldung angezeigt, die in etwa wie folgt lautet: „*Die resources.pri im Paket wurde beschädigt, sodass die Verschlüsselung fehlgeschlagen ist (Fehler PRI222: 0xdef0000f - Unbestimmter Fehler aufgetreten)*“.</span><span class="sxs-lookup"><span data-stu-id="a389b-119">If you don't specify the main file then you'll see the error message "*The resources.pri in the package was corrupted so encryption failed (error PRI222: 0xdef0000f - Unspecified error occurred)*".</span></span>

```
C:\>makepri dump /?

Usage:
------
    MakePri.exe dump [options]

Example:
--------
    MakePri.exe dump /if C:\MyApp\resources.pri /of C:\resources.pri.xml

Description:
------------
    Outputs a dumped xml file at <output file> containing a list of all 
    resources in <index file>.

Options:
--------
    /DumpType(dt)       : <STRING> Format of the dumped file, default is
                          Basic
    /ExtensionDll(ex)   : <FILEPATH> Location of the Resource Management System
                          environment extension DLL. This DLL must be signed by a
                          Microsoft-issued certificate. Default is an empty path
                          (no DLL will be used)
    /ExternalSchema(es) : <FILEPATH> Location of the external schema file
    /IndexFile(if)      : <FILEPATH> Location of the PRI file to dump from.
                          Default is .\resources.pri
    /OutputFile(of)     : <FILEPATH> Output location of the dump file, default
                          is .\[indexfile].xml
    /OutputOptions(oo)  : <OPTIONS> Options to provide detailed control over
                          contents of XML output files.
    /Overwrite(o)       : Overwrite an existing output file of the same name
                          without prompting
    /Verbose(v)         : Causes verbose messages to be output to the console

    Dump Type:
        Either 'Basic', 'Detailed', 'Schema', or 'Summary'

    FILEPATH            - a path to a file, either relative to the current
                          directory or absolute
Help:
-----
    /Help(h, ?)         : Display the usage help text
```

## <a name="new-command"></a><span data-ttu-id="a389b-120">New-Befehl</span><span class="sxs-lookup"><span data-stu-id="a389b-120">New command</span></span>

<span data-ttu-id="a389b-121">Der Befehl `new` erstellt eine neue PRI-Datei, indem er die Dateien in Ihrem Projekt gemäß Ihrer Konfigurationsdatei indiziert.</span><span class="sxs-lookup"><span data-stu-id="a389b-121">The `new` command creates a new PRI file by indexing the files in your project as directed by your configuration file.</span></span> <span data-ttu-id="a389b-122">Führen Sie `MakePri.exe new /?` aus, um detaillierte Hilfe für diesen Befehl anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a389b-122">Run `MakePri.exe new /?` to see detailed help for this command.</span></span>

```
C:\>makepri new /?

Usage:
------
    MakePri.exe new /cf <config file> /pr <project root> [options]

Example:
--------
    MakePri.exe new /cf C:\MyApp\priconfig.xml /pr C:\MyApp\src\ 
    /mn C:\MyApp\AppXManifest.xml /o /of C:\MyApp\src\resources.pri

Description:
------------
    Creates a PRI file at <output file> by indexing all files in
    <project root> and its subdirectories as directed by <config file>. The
    index will be assigned <index name> to reference resources in the app

Required Parameters:
--------------------
    /ConfigXml(cf)    : <FILEPATH> Configuration file location. Use the
                        'Makepri.exe createconfig' command to generate one
    /ProjectRoot(pr)  : <FOLDERPATH> Root location of project files

Options:
--------
    /AutoMerge(am)    : This flag is not recommended for normal use with AppX
                        packages. It causes Makepri.exe to set the auto
                        merge flag within the PRI file. Default is not set.
    /ExtensionDll(ex) : <FILEPATH> Location of the Resource Management System
                        environment extension DLL. This DLL must be signed by
                        a Microsoft-issued certificate. Default is an empty path
                        (no DLL will be used)
    /IndexLog(il)     : <FILEPATH> XML Log of indexed resources, no file
                        generated by default
    /IndexName(in)    : <STRING> Name for the generated index of resources.
                        Typically matches the AppX package name, class library
                        simple name, etc. May be supplied via the
                        [manifest] parameter.
    /IndexOptions(io) : <OPTIONS> Options to provide detailed control over
                        behavior of resource indexers.
    /Manifest(mn)     : <FILEPATH> Location of the application or component's
                        manifest. This parameter is ignored if [indexname]
                        is given. Default is [projectroot]\AppXManifest.xml
    /MappingFile(mf)  : <MAPPINGFILETYPE> Generate a mapping file in the given
                        file format.
    /OutputFile(of)   : <FILEPATH> Output location of PRI file, default is
                        .\resources.pri
    /Overwrite(o)     : Overwrite an existing output file of the same name
                        without prompting
    /ReverseMap(rm)   : Generate a reverse mapping section in the PRI file
                        which can be used for debugging purposes.
    /SchemaFile(sf)   : <FILEPATH> Output location of XML resource schema
                        description.
    /Verbose(v)       : Causes verbose messages to be output to the console
    /VersionMajor(vma): <INTEGER> [Deprecated] Major version number for
                        index, default is 1

    FOLDERPATH        - a path to a folder
    FILEPATH          - a path to a file, either relative to the current
                        directory or absolute
    MAPPINGFILETYPE   - Supported File type(s): 'AppX'

Help:
-----
    /Help(h, ?)        : Display the usage help text
```

## <a name="resourcepack-command"></a><span data-ttu-id="a389b-123">ResourcePack-Befehl</span><span class="sxs-lookup"><span data-stu-id="a389b-123">ResourcePack command</span></span>

<span data-ttu-id="a389b-124">Der Befehl `resourcepack` erstellt eine neue PRI-Datei, indem er die Dateien in Ihrem Projekt gemäß Ihrer Konfigurationsdatei indiziert.</span><span class="sxs-lookup"><span data-stu-id="a389b-124">The `resourcepack` command creates a new PRI file by indexing the files in your project as directed by your configuration file.</span></span> <span data-ttu-id="a389b-125">Eine Ressourcenpaket-PRI-Datei enthält nur zusätzliche Varianten von Ressourcen, die bereits in einer vorhandenen PRI-Datei angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="a389b-125">A resource pack PRI file contains only additional variants of resources already specified in an existing PRI file.</span></span> <span data-ttu-id="a389b-126">Führen Sie `MakePri.exe resourcepack /?` aus, um detaillierte Hilfe für diesen Befehl anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a389b-126">Run `MakePri.exe resourcepack /?` to see detailed help for this command.</span></span>

```
C:\>makepri resourcepack /?

Usage:
------
    MakePri.exe resourcepack /pr <project root> /cf <config file> [options]

Example:
--------
    MakePri.exe resourcepack /cf C:\MyAppEs\priconfig.xml /pr C:\MyAppEs\src\ 
    /if C:\MyApp\1.2\resources.pri /o /of C:\MyAppEs\resources.pri

Description:
------------
    Creates a PRI file at <output file> by indexing all files in 
    <project root> and its subdirectories as directed by <config file>. A 
    resource pack PRI file contains only additional variants of resources 
    already specified in <index file>.

Required Parameters:
--------------------
    /ConfigXml(cf)    : <FILEPATH> Configuration file location. Use
                        'Makepri.exe createconfig' command to generate one
    /ProjectRoot(pr)  : <FOLDERPATH> Root location of project files

Options:
--------
    /AutoMerge(am)    : This flag is not recommended for normal use with AppX
                        packages. It causes Makepri.exe to set the auto
                        merge flag within the PRI file. By default it is set
                        to same as the base PRI file.
    /ExtensionDll(ex) : <FILEPATH> Location of the Resource Management System
                        environment extension DLL. This DLL must be signed by
                        a Microsoft-issued certificate. Default is an empty path
                        (no DLL will be used)
    /IndexFile(if)    : <FILEPATH> Location of the base PRI or XML schema file.
                        Default is <ProjectRoot>\resources.pri
    /IndexLog(il)     : <FILEPATH> XML Log of indexed resources, no file
                        generated by default
    /IndexOptions(io) : <OPTIONS> Options to provide detailed control over
                        behavior of resource indexers.
    /MappingFile(mf)  : <MAPPINGFILETYPE> Generate a mapping file in the given
                        file format.
    /OutputFile(of)   : <FILEPATH> Output location of PRI file, default is
                        .\resources.pri
    /Overwrite(o)     : Overwrite an existing output file of the same name
                        without prompting
    /ReverseMap(rm)   : Generate a reverse mapping section in the PRI file
                        which can be used for debugging purposes.
    /SchemaFile(sf)   : <FILEPATH> Output location of XML resource schema
                        description.
    /Verbose(v)       : Causes verbose messages to be output to the console

    FOLDERPATH        - a path to a folder
    FILEPATH          - a path to a file, either relative to the current
                        directory or absolute
    MAPPINGFILETYPE   - Supported File type(s): 'AppX'

Help:
-----
    /Help(h, ?)        : Display the usage help text
```

## <a name="versioned-command"></a><span data-ttu-id="a389b-127">Versioned-Befehl</span><span class="sxs-lookup"><span data-stu-id="a389b-127">Versioned command</span></span>

<span data-ttu-id="a389b-128">Der Befehl `versioned` erstellt eine neue versionsverwaltete PRI-Datei, indem er die Dateien in Ihrem Projekt gemäß Ihrer Konfigurationsdatei indiziert.</span><span class="sxs-lookup"><span data-stu-id="a389b-128">The `versioned` command creates a versioned PRI file by indexing the files in your project as directed by your configuration file.</span></span> <span data-ttu-id="a389b-129">Führen Sie `MakePri.exe versioned /?` aus, um detaillierte Hilfe für diesen Befehl anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a389b-129">Run `MakePri.exe versioned /?` to see detailed help for this command.</span></span>

```
C:\>makepri versioned /?

Usage:
------
    MakePri.exe versioned /cf <config file> /pr <project root> [options]

Example:
--------
    MakePri.exe versioned /cf C:\MyApp\priconfig.xml /pr C:\MyApp\src 
    /if C:\MyApp\1.2\resources.pri /o /of C:\MyApp\src\resources.pri /o

Description:
------------
    Creates a versioned PRI file at <output file> by indexing all files in 
    <project root> and its subdirectories as directed by <config file>.

Required Parameters:
--------------------
    /ConfigXml(cf)    : <FILEPATH> Configuration file location. Use
                        'Makepri.exe createconfig' command to generate one
    /ProjectRoot(pr)  : <FOLDERPATH> Root location of project files

Options:
--------
    /AutoMerge(am)    : This flag is not recommended for normal use with AppX
                        packages. It causes Makepri.exe to set the auto
                        merge flag within the PRI file. By default it is set
                        to same as the base PRI file.
    /ExtensionDll(ex) : <FILEPATH> Location of the Resource Management System
                        environment extension DLL. This DLL must be signed by
                        a Microsoft-issued certificate. Default is an empty path
                        (no DLL will be used)
    /IndexFile(if)    : <FILEPATH> Location of the base PRI or XML schema file
                        to version from. Default is <ProjectRoot>\resources.pri
    /IndexLog(il)     : <FILEPATH> XML Log of indexed resources, no file
                        generated by default
    /IndexOptions(io) : <OPTIONS> Options to provide detailed control over
                        behavior of resource indexers.
    /MappingFile(mf)  : <MAPPINGFILETYPE> Generate a mapping file in the given
                        file format.
    /OutputFile(of)   : <FILEPATH> Output location of PRI file, default is
                        [current directory]\resources.pri
    /Overwrite(o)     : Overwrite an existing output file of the same name
                        without prompting
    /ReverseMap(rm)   : Generate a reverse mapping section in the PRI file
                        which can be used for debugging purposes.
    /SchemaFile(sf)   : <FILEPATH> Output location of XML resource schema
                        description.
    /Verbose(v)       : Causes verbose messages to be output to the console

    FOLDERPATH        - a path to a folder
    FILEPATH          - a path to a file, either relative to the current
                        directory or absolute
    MAPPINGFILETYPE   - Supported File type(s): 'AppX'

Help:
-----
    /Help(h, ?)        : Display the usage help text
```

## <a name="47extensiondllex"></a><span data-ttu-id="a389b-130">&#47;ExtensionDll(ex)</span><span class="sxs-lookup"><span data-stu-id="a389b-130">&#47;ExtensionDll(ex)</span></span>

<span data-ttu-id="a389b-131">Verwenden Sie die Erweiterungs-DLL-Option (/ex) mit `createconfig`, `dump`, `new`, `resourcepack` und `versioned`, um den Speicherort der Umgebungserweiterungs-DLL für das Ressourcenverwaltungssystem festzulegen.</span><span class="sxs-lookup"><span data-stu-id="a389b-131">You use the extension DLL option (/ex) with `createconfig`, `dump`, `new`, `resourcepack`, and `versioned` to specify the location of the Resource Management System environment extension DLL.</span></span>

## <a name="logging47metadata-file"></a><span data-ttu-id="a389b-132">Logging&#47;Metadatendatei</span><span class="sxs-lookup"><span data-stu-id="a389b-132">Logging&#47;metadata file</span></span>

<span data-ttu-id="a389b-133">MakePri kann Informationen zu einem Ressourcenpaket in die Indexer-Metadatendatei einfügen.</span><span class="sxs-lookup"><span data-stu-id="a389b-133">MakePri can include info specific to a resource pack in the indexer metadata file.</span></span> <span data-ttu-id="a389b-134">Hier ein Beispiel einer Protokolldatei für `resources.pri` mit den PRI-Ressourcendateien `german.pri` und `highresolution.pri`:</span><span class="sxs-lookup"><span data-stu-id="a389b-134">Here is an example of a log file for `resources.pri` with resource PRI files `german.pri` and `highresolution.pri`.</span></span>

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<root>
  <package filename="resources.pri">
    <instance itemname="Files\logo.jpg" qualifiers="Scale-100" src="" type="Path">
      <value>logo.scale-100.jpg</value>
    </instance>
    <instance itemname="resources\string2" qualifiers="Language-en-us" src="C:\Users\alias\Desktop\repro\app4\project\en-us\resources.resw" type="String">
      <value>value2</value>
    </instance>
    <instance itemname="resources\string1" qualifiers="Language-en-us" src="C:\Users\alias\Desktop\repro\app4\project\en-us\resources.resw" type="String">
      <value>value1</value>
    </instance>
  </package>
  <package filename="german.pri">
    <instance itemname="resources\string2" qualifiers="Language-de-de" src="C:\Users\alias\Desktop\repro\app4\project\de-de\resources.resw" type="String">
      <value>value2</value>
    </instance>
    <instance itemname="resources\string1" qualifiers="Language-de-de" src="C:\Users\alias\Desktop\repro\app4\project\de-de\resources.resw" type="String">
      <value>value1</value>
    </instance>
  </package>
  <package filename="highresolution.pri">
    <instance itemname="Files\logo.jpg" qualifiers="Scale-200" src="" type="Path">
      <value>logo.scale-200.jpg</value>
    </instance>
  </package>
</root>
```

## <a name="47indexfileif-option"></a><span data-ttu-id="a389b-135">&#47;IndexFile(if) Option</span><span class="sxs-lookup"><span data-stu-id="a389b-135">&#47;IndexFile(if) option</span></span>

<span data-ttu-id="a389b-136">Verwenden Sie die Indexdateioption (/if) mit `dump`, `resourcepack` und `versioned`, um eine PRI-Eingabedatei anzugeben.</span><span class="sxs-lookup"><span data-stu-id="a389b-136">You use the index file option (/if) with `dump`, `resourcepack`, and `versioned` to specify an input PRI file.</span></span>

<span data-ttu-id="a389b-137">Für `resourcepack` und `versioned` können Sie eine Schemadatei bereitstellen, statt eine PRI-Datei als Eingabeparameter für /IndexFile(if) anzugeben.</span><span class="sxs-lookup"><span data-stu-id="a389b-137">For `resourcepack` and `versioned`, instead of providing a PRI file as the input parameter for /IndexFile(if), you can instead provide a schema file.</span></span>

```
/IndexFile(if) <FILEPATH>
```

<span data-ttu-id="a389b-138">**FILEPATH** ist ein Token, das den Speicherort der PRI-Eingabedatei oder PRI-Schemadatei angibt</span><span class="sxs-lookup"><span data-stu-id="a389b-138">**FILEPATH** is a token that that specifies the location of the input PRI file or PRI schema file.</span></span>

## <a name="47mappingfilemf-option"></a><span data-ttu-id="a389b-139">&#47;MappingFile(mf) Option</span><span class="sxs-lookup"><span data-stu-id="a389b-139">&#47;MappingFile(mf) option</span></span>

<span data-ttu-id="a389b-140">Verwenden Sie die Zuordnungsoption (/mf) mit `new`, `resourcepack` und `versioned`, um eine Zuordnungsdatei zu generieren.</span><span class="sxs-lookup"><span data-stu-id="a389b-140">You use the mapping file option (/mf) with `new`, `resourcepack`, and `versioned` to generate a mapping file.</span></span> <span data-ttu-id="a389b-141">[MakeAppx.exe](../packaging/create-app-package-with-makeappx-tool.md) verwendet die Zuordnungsdatei zum Erzeugen von App-Paketen.</span><span class="sxs-lookup"><span data-stu-id="a389b-141">[MakeAppx.exe](../packaging/create-app-package-with-makeappx-tool.md) uses the mapping file to generate app packages.</span></span>

```
/MappingFile(mf) <MAPPINGFILETYPE>
```

<span data-ttu-id="a389b-142">**MAPPINGFILETYPE** ist ein Token, mit dem das Format der Zuordnungsdatei angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="a389b-142">**MAPPINGFILETYPE** is a token that specifies the format of the mapping file.</span></span> <span data-ttu-id="a389b-143">Es wird nur das Format `appx` unterstützt.</span><span class="sxs-lookup"><span data-stu-id="a389b-143">The only valid supported format is `appx`.</span></span>

```
/mf appx
```

<span data-ttu-id="a389b-144">Hier ein Beispiel für Inhalte einer Hauptzuordnungsdatei:</span><span class="sxs-lookup"><span data-stu-id="a389b-144">This is an example contents of a main mapping file.</span></span>

```
"ResourceDimensions"                   "language-de-de"
```

<span data-ttu-id="a389b-145">Und hier ein Beispiel für Inhalte einer Zuordnungsdatei für ein Ressourcenpaket:</span><span class="sxs-lookup"><span data-stu-id="a389b-145">And this is an example contents of a resource pack mapping file.</span></span>

```
"ResourceId"                           "Resources184.la5decaf08"
"ResourceDimensions"                   "language-de-de"
```

## <a name="output-summary"></a><span data-ttu-id="a389b-146">Ausgabezusammenfassung</span><span class="sxs-lookup"><span data-stu-id="a389b-146">Output summary</span></span>

<span data-ttu-id="a389b-147">Wenn Ressourcenpakete erstellt werden, ist die Ausgabezusammenfassung von MakePRI.exe ausführlicher.</span><span class="sxs-lookup"><span data-stu-id="a389b-147">If resource packs are created, the output summary from MakePRI.exe is of more verbose form.</span></span> <span data-ttu-id="a389b-148">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="a389b-148">Here's an example.</span></span>

```
Index Pass Completed: ResourcePackTests\TestApp_ResourcePack
Language Qualifiers: fr-FR, de-DE

Finished building
Version: 1.0
Resource Map Name: AppTest
Named Resources: 11

Resource PRI: fr-FR.pri
Version: 1.0
Resource Candidates: 4
Language: fr-FR

Resource PRI: de-DE.pri
Version: 1.0
Resource Candidates: 4
Language: de-DE

Output File(s) at TempTestResults
Successfully Completed
```

## <a name="47overwriteo-option"></a><span data-ttu-id="a389b-149">&#47;Overwrite(o) Option</span><span class="sxs-lookup"><span data-stu-id="a389b-149">&#47;Overwrite(o) option</span></span>

<span data-ttu-id="a389b-150">Wenn die Option zum Überschreiben (/o) fehlt und die angegebenen Ausgabedateien bereits vorhanden sind, benötigt MakePri.exe zum Überschreiben eine Bestätigung.</span><span class="sxs-lookup"><span data-stu-id="a389b-150">If the over-write option (/o) is not provided, and the specified output file(s) already exist(s), then MakePri.exe requires a confirmation before overwriting.</span></span>

```
Following file(s) already exist at output location:
<file(s)>
Overwrite these file(s)? [Y]es (any other key to cancel):
```

## <a name="47outputfileof-option"></a><span data-ttu-id="a389b-151">&#47;OutputFile(of) Option</span><span class="sxs-lookup"><span data-stu-id="a389b-151">&#47;OutputFile(of) option</span></span>

<span data-ttu-id="a389b-152">Verwenden Sie die Ausgabedateioption (/of) mit `dump`, `new`, `resourcepack` und `versioned`, um den Ausgabespeicherort und den Namen der zu generierenden PRI-Datei anzugeben.</span><span class="sxs-lookup"><span data-stu-id="a389b-152">You use the output file option (/of) with `dump`, `new`, `resourcepack`, and `versioned` to specify the output location and name of the PRI file to be generated.</span></span> <span data-ttu-id="a389b-153">Sollte MakePri.exe mehrere PRI-Ressourcendateien generieren, werden diese im übergeordneten Ordner der Zieldatei abgelegt.</span><span class="sxs-lookup"><span data-stu-id="a389b-153">If MakePri.exe generates more than one resource PRI file, it places them in the parent folder of the target file.</span></span> <span data-ttu-id="a389b-154">Wenn Sie beispielsweise `/of MyParentFolder\TargetFile.pri` angeben, generiert MakePri.exe `TargetFile.language-en.pri` und `TargetFile.scale-100.pri` zusammen mit `TargetFile.pri` unter `ParentFolder`.</span><span class="sxs-lookup"><span data-stu-id="a389b-154">For example, if you specify `/of MyParentFolder\TargetFile.pri` then MakePri.exe generates `TargetFile.language-en.pri` and `TargetFile.scale-100.pri` alongside `TargetFile.pri` under `ParentFolder`.</span></span>

<span data-ttu-id="a389b-155">Hier ein Beispiel für eine Fehlerbedingung und die entsprechende Fehlermeldung:</span><span class="sxs-lookup"><span data-stu-id="a389b-155">Here is an example error condition and the corresponding error message.</span></span>

| <span data-ttu-id="a389b-156">Fehlerbedingung</span><span class="sxs-lookup"><span data-stu-id="a389b-156">Error condition</span></span> | <span data-ttu-id="a389b-157">Fehlermeldung</span><span class="sxs-lookup"><span data-stu-id="a389b-157">Error message</span></span> |
| --------------- | ------------- |
| <span data-ttu-id="a389b-158">Der Name der Ausgabedatei entspricht einem der Ressourcenpaketnamen in der Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a389b-158">The output file name is the same as one of the resource pack names in the configuration.</span></span> | <span data-ttu-id="a389b-159">Ungültige Konfiguration: Der Ressourcenpaketname <resource pack name> darf nicht mit dem Namen der Ausgabedatei <outputfilename.pri> übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="a389b-159">Invalid Configuration: Resource Pack name <resource pack name> cannot be the same as the output file <outputfilename.pri>.</span></span> |

## <a name="reversemaprm-option"></a><span data-ttu-id="a389b-160">/ReverseMap(rm) Option</span><span class="sxs-lookup"><span data-stu-id="a389b-160">/ReverseMap(rm) option</span></span>

<span data-ttu-id="a389b-161">Sie können die Option zum Umkehren der Zuordnung (/rm) mit `new`, `resourcepack` und `versioned` verwenden, um in der PRI-Datei einen Abschnitt mit umgekehrter Zuordnung zu generieren, der zum Debuggen verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="a389b-161">You use the reverse map option (/rm) with `new`, `resourcepack`, and `versioned` to generate a reverse-mapping section in the PRI file, which can be used for debugging.</span></span>

## <a name="47schemafilesf-option"></a><span data-ttu-id="a389b-162">&#47;SchemaFile(sf) Option</span><span class="sxs-lookup"><span data-stu-id="a389b-162">&#47;SchemaFile(sf) option</span></span>

<span data-ttu-id="a389b-163">Verwenden Sie die Schemadateioption (/sf) mit `new`, `resourcepack` und `versioned`, um eine Schemadatei am angegebenen Speicherort zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="a389b-163">You use the schema file option (/sf) with `new`, `resourcepack`, and `versioned` to write a schema file at the specified location.</span></span>

<span data-ttu-id="a389b-164">Für `resourcepack` und `versioned` können Sie eine Schemadatei bereitstellen, statt eine PRI-Datei als Eingabeparameter für /IndexFile(if) anzugeben.</span><span class="sxs-lookup"><span data-stu-id="a389b-164">For `resourcepack` and `versioned`, instead of providing a PRI file as the input parameter for /IndexFile(if), you can instead provide a schema file.</span></span>

```
/SchemaFile(sf) <FILEPATH>
```

<span data-ttu-id="a389b-165">**FILEPATH** ist ein Token, das angibt, an welchem Speicherort die Schemadatei geschrieben werden soll.</span><span class="sxs-lookup"><span data-stu-id="a389b-165">**FILEPATH** is a token that that specifies where to write the schema file.</span></span>

<span data-ttu-id="a389b-166">Hier ein Beispiel für eine Datendatei:</span><span class="sxs-lookup"><span data-stu-id="a389b-166">This is an example of a schema file.</span></span>

```xml
<PriInfo>
    <ResourceMap name="IndexName" resourceVersion="1.0"> 
        <ResourceMapSubtree name="Resources" index="1">
            <NamedResource name="String1" index="1"/>
            <NamedResource name="String2" index="1"/>
        </ResourceMapSubtree>
        <ResourceMapSubtree name="Files" index="2">
            <NamedResource name="logo.png" index="2"/>
            <ResourceMapSubtree name="images" index="3">
                <NamedResource name="success.png" index="3"/>
                <NamedResource name="error.png" index="3"/>
            </ResourceMapSubtree>
        </ResourceMapSubtree>
    </ResourceMap>
</PriInfo>
```

## <a name="47versionmajorvma-is-deprecated"></a><span data-ttu-id="a389b-167">&#47;VersionMajor(vma) ist veraltet</span><span class="sxs-lookup"><span data-stu-id="a389b-167">&#47;VersionMajor(vma) is deprecated</span></span>

<span data-ttu-id="a389b-168">Die Option für die Hauptversion (/vma) (für den Befehl `new`) ist veraltet, und bei der Verwendung der Option wird folgende Warnmeldung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="a389b-168">The major version (/vma) option (for the `new` command) is deprecated, and using it results in this warning message.</span></span>

```
'VersionMajor (vma)' input parameter has been deprecated. Please specify major version in the configuration file using 'majorVersion' attribute on 'resources' node.
```

<span data-ttu-id="a389b-169">Verwenden Sie stattdessen in Ihrer Konfigurationsdatei das Attribut [resources@majorVersion](makepri-exe-configuration.md), um die Hauptversionsnummer anzugeben.</span><span class="sxs-lookup"><span data-stu-id="a389b-169">To provide the major version number, use the [resources@majorVersion](makepri-exe-configuration.md) attribute in your configuration file.</span></span>

## <a name="related-topics"></a><span data-ttu-id="a389b-170">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="a389b-170">Related topics</span></span>

* [<span data-ttu-id="a389b-171">MakePri.exe</span><span class="sxs-lookup"><span data-stu-id="a389b-171">MakePri.exe</span></span>](compile-resources-manually-with-makepri.md)
