---
author: stevewhims
Description: In diesem Thema werden die formatspezifischen Indexer beschrieben, die das Tool MakePri.exe verwendet, um seinen Ressourcenindex zu generieren.
title: "Formatspezifische Indexer für MakePri.exe"
template: detail.hbs
ms.author: stwhi
ms.date: 10/18/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Ressourcen, Bild, Element, MRT, Qualifizierer
localizationpriority: medium
ms.openlocfilehash: d0ab502a4735ac028a4d2869824378d69314eb72
ms.sourcegitcommit: 44a24b580feea0f188c7eae36e72e4a4f412802b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

# <a name="makepriexe-format-specific-indexers"></a><span data-ttu-id="ff84c-104">Formatspezifische Indexer für MakePri.exe</span><span class="sxs-lookup"><span data-stu-id="ff84c-104">MakePri.exe format-specific indexers</span></span>

<span data-ttu-id="ff84c-105">In diesem Thema werden die formatspezifischen Indexer beschrieben, die das Tool [MakePri.exe](compile-resources-manually-with-makepri.md) verwendet, um seinen Ressourcenindex zu generieren.</span><span class="sxs-lookup"><span data-stu-id="ff84c-105">This topic describes the format-specific indexers used by the [MakePri.exe](compile-resources-manually-with-makepri.md) tool to generate its index of resources.</span></span>

<span data-ttu-id="ff84c-106">MakePri.exe wird in der Regel mit den Befehlen `new`, `versioned` oder `resourcepack` verwendet.</span><span class="sxs-lookup"><span data-stu-id="ff84c-106">MakePri.exe is typically used with the `new`, `versioned`, or `resourcepack` commands.</span></span> <span data-ttu-id="ff84c-107">Siehe [Befehlszeilenoptionen für MakePri.exe](makepri-exe-command-options.md).</span><span class="sxs-lookup"><span data-stu-id="ff84c-107">See [MakePri.exe command-line options](makepri-exe-command-options.md).</span></span> <span data-ttu-id="ff84c-108">In diesen Fällen indiziert das Tool Quelldateien und generiert einen Ressourcenindex.</span><span class="sxs-lookup"><span data-stu-id="ff84c-108">In those cases it indexes source files to generate an index of resources.</span></span> <span data-ttu-id="ff84c-109">MakePri.exe verwendet eine Reihe individueller Indexer, um die verschiedenen Quellressourcendateien oder Ressourcencontainer zu lesen.</span><span class="sxs-lookup"><span data-stu-id="ff84c-109">MakePri.exe uses various individual indexers to read different source resource files or containers for resources.</span></span> <span data-ttu-id="ff84c-110">Der einfachste Indexer ist der Ordnerindexer. Er indiziert den Inhalt eines Ordners, beispielsweise `.jpg`- oder `.png`-Bilder.</span><span class="sxs-lookup"><span data-stu-id="ff84c-110">The simplest indexer is the folder indexer, which indexes the contents of a folder, such as `.jpg` or `.png` images.</span></span>

<span data-ttu-id="ff84c-111">Formatspezifische Indexer werden durch Angabe von `<indexer-config>`-Elementen in einem `<index>`-Element der [MakePri.exe-Konfigurationsdatei](makepri-exe-configuration.md) identifiziert.</span><span class="sxs-lookup"><span data-stu-id="ff84c-111">You identify format-specific indexers by specifying `<indexer-config>` elements within an `<index>` element of the [MakePri.exe configuration file](makepri-exe-configuration.md).</span></span> <span data-ttu-id="ff84c-112">Das Attribut `type` identifiziert den verwendeten formatspezifischen Indexer.</span><span class="sxs-lookup"><span data-stu-id="ff84c-112">The `type` attribute identifies the format-specific indexer that is used.</span></span>

<span data-ttu-id="ff84c-113">Bei Ressourcencontainern, die während der Indizierung vorgefunden werden, wird der Inhalt indiziert. Die Container selbst werden dem Index nicht hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="ff84c-113">Resource containers encountered during indexing usually get their contents indexed rather than being added to the index themselves.</span></span> <span data-ttu-id="ff84c-114">Beispielsweise werden vom Ordnerindexer gefundene `.resjson`-Dateien von einem `.resjson`-Indexer im Detail indiziert. Die `.resjson`-Datei ist in diesem Fall nicht im Index enthalten.</span><span class="sxs-lookup"><span data-stu-id="ff84c-114">For example, `.resjson` files that the folder indexer finds may be further indexed by a `.resjson` indexer, in which case the `.resjson` file itself does not appear in the index.</span></span> <span data-ttu-id="ff84c-115">**Hinweis:** Dazu muss ein `<indexer-config>`-Element für den Indexer, der diesem Container zugeordnet ist, in der Konfigurationsdatei enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="ff84c-115">**Note** an `<indexer-config>` element for the indexer associated with that container must be included in the configuration file for that to happen.</span></span>

<span data-ttu-id="ff84c-116">Die für eine Containerentität wie einen Ordner oder eine &mdash;-Datei gefundenen Qualifizierer werden normalerweise auf alle enthaltenen Ressourcen angewendet, also beispielsweise auf die Dateien im Ordner oder die Zeichenfolgen in der `.resw`-Datei.</span><span class="sxs-lookup"><span data-stu-id="ff84c-116">Typically, qualifiers found on a containing entity&mdash;such as a folder or a `.resw` file&mdash;are applied to all resources within it, such as the files within the folder, or the strings within the `.resw` file.</span></span>

## <a name="folder"></a><span data-ttu-id="ff84c-117">Ordner</span><span class="sxs-lookup"><span data-stu-id="ff84c-117">Folder</span></span>

<span data-ttu-id="ff84c-118">Der Ordnerindexer wird mit dem `type`-Attribut FOLDER angegeben.</span><span class="sxs-lookup"><span data-stu-id="ff84c-118">The folder indexer is identified by a `type` attribute of FOLDER.</span></span> <span data-ttu-id="ff84c-119">Er indiziert den Inhalt eines Ordners und bestimmt Ressourcenbezeichner anhand der Ordner- und Dateinamen.</span><span class="sxs-lookup"><span data-stu-id="ff84c-119">It indexes the contents of a folder, and determines resource qualifiers from the folder and filenames.</span></span> <span data-ttu-id="ff84c-120">Das zugehörige Konfigurationselement entspricht dem folgenden Schema.</span><span class="sxs-lookup"><span data-stu-id="ff84c-120">Its configuration element conforms to the following schema.</span></span>

```xml
<xs:schema attributeFormDefault=\"unqualified\" elementFormDefault=\"qualified\" xmlns:xs=\"http://www.w3.org/2001/XMLSchema\">\
    <xs:simpleType name=\"ExclusionTypeList\">\
        <xs:restriction base=\"xs:string\">\
            <xs:enumeration value=\"path\"/>\
            <xs:enumeration value=\"extension\"/>\
            <xs:enumeration value=\"name\"/>\
            <xs:enumeration value=\"tree\"/>\
        </xs:restriction>\
    </xs:simpleType>\
    <xs:complexType name=\"FolderExclusionType\">\
        <xs:attribute name=\"type\" type=\"ExclusionTypeList\" use=\"required\"/>\
        <xs:attribute name=\"value\" type=\"xs:string\" use=\"required\"/>\
        <xs:attribute name=\"doNotTraverse\" type=\"xs:boolean\" use=\"required\"/>\
        <xs:attribute name=\"doNotIndex\" type=\"xs:boolean\" use=\"required\"/>\
    </xs:complexType>\
    <xs:simpleType name=\"IndexerConfigFolderType\">\
        <xs:restriction base=\"xs:string\">\
            <xs:pattern value=\"((f|F)(o|O)(l|L)(d|D)(e|E)(r|R))\"/>\
        </xs:restriction>\
    </xs:simpleType>\
    <xs:element name=\"indexer-config\">\
        <xs:complexType>\
            <xs:sequence>\
                <xs:element name=\"exclude\" type=\"FolderExclusionType\" minOccurs=\"0\" maxOccurs=\"unbounded\"/>\
            </xs:sequence>\
            <xs:attribute name=\"type\" type=\"IndexerConfigFolderType\" use=\"required\"/>\
            <xs:attribute name=\"foldernameAsQualifier\" type=\"xs:boolean\" use=\"required\"/>\
            <xs:attribute name=\"filenameAsQualifier\" type=\"xs:boolean\" use=\"required\"/>\
            <xs:attribute name=\"qualifierDelimiter\" type=\"xs:string\" use=\"required\"/>\
        </xs:complexType>\
    </xs:element>\
</xs:schema>
```

<span data-ttu-id="ff84c-121">Das Attribut `qualifierDelimiter` bestimmt das Zeichen, nach dem Qualifizierer in einem Dateinamen angegeben werden (die Dateinamenerweiterung wird ignoriert).</span><span class="sxs-lookup"><span data-stu-id="ff84c-121">The `qualifierDelimiter` attribute specifies the character after which qualifiers are specified in a filename, ignoring the extension.</span></span> <span data-ttu-id="ff84c-122">Der Standardwert ist ".".</span><span class="sxs-lookup"><span data-stu-id="ff84c-122">The default is ".".</span></span>

## <a name="pri"></a><span data-ttu-id="ff84c-123">PRI</span><span class="sxs-lookup"><span data-stu-id="ff84c-123">PRI</span></span>

<span data-ttu-id="ff84c-124">Der PRI-Indexer wird mit dem `type`-Attribut PRI angegeben.</span><span class="sxs-lookup"><span data-stu-id="ff84c-124">The PRI indexer is identified by a `type` attribute of PRI.</span></span> <span data-ttu-id="ff84c-125">Er indiziert die Inhalte von PRI-Dateien.</span><span class="sxs-lookup"><span data-stu-id="ff84c-125">It indexes the contents of a PRI file.</span></span> <span data-ttu-id="ff84c-126">Normalerweise werden damit Ressourcen in anderen Assemblys, DLLs, SDKs oder in Klassenbibliotheken in der PRI-Datei der App indiziert.</span><span class="sxs-lookup"><span data-stu-id="ff84c-126">You typically use it when indexing the resource contained within another assembly, DLL, SDK, or class library into the app's PRI.</span></span>

<span data-ttu-id="ff84c-127">Alle Ressourcennamen, Qualifizierer und Werte in der PRI-Datei werden direkt in der neuen PRI-Datei beibehalten.</span><span class="sxs-lookup"><span data-stu-id="ff84c-127">All resource names, qualifiers and values contained in the PRI file are directly maintained in the new PRI file.</span></span> <span data-ttu-id="ff84c-128">Die Ressourcenzuordnung der obersten Ebene wird jedoch nicht in der abschließenden PRI-Datei beibehalten.</span><span class="sxs-lookup"><span data-stu-id="ff84c-128">The top level resource map, however is not maintained in the final PRI.</span></span> <span data-ttu-id="ff84c-129">Ressourcenzuordnungen werden zusammengeführt.</span><span class="sxs-lookup"><span data-stu-id="ff84c-129">Resource Maps are merged.</span></span>

```xml
<xs:schema id=\"prifile\" xmlns:xs=\"http://www.w3.org/2001/XMLSchema\" elementFormDefault=\"qualified\">\
    <xs:simpleType name=\"IndexerConfigPriType\">\
        <xs:restriction base=\"xs:string\">\
            <xs:pattern value=\"((p|P)(r|R)(i|I))\"/>\
        </xs:restriction>\
    </xs:simpleType>\
    <xs:element name=\"indexer-config\">\
        <xs:complexType>\
            <xs:attribute name=\"type\" type=\"IndexerConfigPriType\" use=\"required\"/>\
        </xs:complexType>\
    </xs:element>\
</xs:schema>\
```

## <a name="priinfo"></a><span data-ttu-id="ff84c-130">PriInfo</span><span class="sxs-lookup"><span data-stu-id="ff84c-130">PriInfo</span></span>

<span data-ttu-id="ff84c-131">Der PriInfo-Indexer wird mit dem `type`-Attribut PRIINFO angegeben.</span><span class="sxs-lookup"><span data-stu-id="ff84c-131">The PriInfo indexer is identified by a `type` attribute of PRIINFO.</span></span> <span data-ttu-id="ff84c-132">Er indiziert den Inhalt einer ausführlichen Dumpdatei.</span><span class="sxs-lookup"><span data-stu-id="ff84c-132">It indexes the contents of a detailed dump file.</span></span> <span data-ttu-id="ff84c-133">Durch den Aufruf von `makepri dump` mit der Option `/dt detailed` wird eine detaillierte Dumpdatei erstellt.</span><span class="sxs-lookup"><span data-stu-id="ff84c-133">You produce a detailed dump file by running `makepri dump` with the `/dt detailed` option.</span></span> <span data-ttu-id="ff84c-134">Der Konfigurationselement für den Indexer entspricht dem folgenden Schema.</span><span class="sxs-lookup"><span data-stu-id="ff84c-134">The configuration element for the indexer conforms to the following schema.</span></span>

```xml
<xs:schema id="priinfo" xmlns:xs="http://www.w3.org/2001/XMLSchema" elementFormDefault="qualified">
  <xs:simpleType name="IndexerConfigPriInfoType">
    <xs:restriction base="xs:string">
      <xs:pattern value="((p|P)(r|R)(i|I)(i|I)(n|N)(f|F)(o|O))"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:element name="indexer-config">
    <xs:complexType>
      <xs:attribute name="type" type="IndexerConfigPriInfoType" use="required"/>
      <xs:attribute name="emitStrings" type="xs:boolean" use="optional"/>
      <xs:attribute name="emitPaths" type="xs:boolean" use="optional"/>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

<span data-ttu-id="ff84c-135">Dieses Konfigurationselement ermöglicht die Verwendung optionaler Attribute, um das Verhalten des PriInfo-Indexers zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="ff84c-135">This configuration element allows for optional attributes to configure the behavior of the PriInfo indexer.</span></span> <span data-ttu-id="ff84c-136">Der Standardwert für `emitStrings` und `emitPaths` ist `true`.</span><span class="sxs-lookup"><span data-stu-id="ff84c-136">The default value of `emitStrings` and `emitPaths` is `true`.</span></span> <span data-ttu-id="ff84c-137">Wenn `emitStrings` den Wert `true` besitzt, werden Ressourcenkandidaten mit dem `type`-Attribut „String” in den Index aufgenommen. Andernfalls werden sie ausgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="ff84c-137">If `emitStrings` is `true` then resource candidates with the `type` attribute set to "String" are be included in the index, otherwise they are excluded.</span></span> <span data-ttu-id="ff84c-138">Wenn „emitPaths” den Wert `true` besitzt, werden Ressourcenkandidaten mit dem `type`-Attribut „Path” in den Index aufgenommen. Andernfalls werden sie ausgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="ff84c-138">If 'emitPaths' is `true` then resource candidates with the `type` attribute set to "Path" are included in the index, otherwise they are excluded.</span></span>

<span data-ttu-id="ff84c-139">Im folgenden Konfigurationsbeispiel werden String-Ressourcentypen aufgenommen und Path-Ressourcentypen übersprungen.</span><span class="sxs-lookup"><span data-stu-id="ff84c-139">Here is an example configuration that includes String resource types but skips Path resource types.</span></span>

```xml
<indexer-config type="priinfo" emitStrings="true" emitPaths="false" />
```

<span data-ttu-id="ff84c-140">Voraussetzung für die Indizierung einer Dumpdatei ist, dass sie über die Erweiterung `.pri.xml` verfügt und dem folgenden Schema entspricht.</span><span class="sxs-lookup"><span data-stu-id="ff84c-140">To be indexed, a dump file must end with the extension `.pri.xml`, and must conform to the following schema.</span></span>

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" elementFormDefault="qualified" >\
  <xs:simpleType name="candidateType">\
    <xs:restriction base="xs:string">\
      <xs:pattern value="Path|String"/>\
    </xs:restriction>\
  </xs:simpleType>\
  <xs:complexType name="scopeType">\
    <xs:sequence>\
      <xs:element name="ResourceMapSubtree" type="scopeType" minOccurs="0" maxOccurs="unbounded"/>\
      <xs:element name="NamedResource" minOccurs="0" maxOccurs="unbounded">\
        <xs:complexType>\
          <xs:sequence>\
            <xs:element name="Decision" minOccurs="0" maxOccurs="unbounded">\
              <xs:complexType>\
                <xs:sequence>\
                  <xs:any processContents="skip" minOccurs="0" maxOccurs="unbounded"/>\
                </xs:sequence>\
                <xs:anyAttribute processContents="skip" />\
              </xs:complexType>\
            </xs:element>\
            <xs:element name="Candidate" minOccurs="0" maxOccurs="unbounded">\
              <xs:complexType>\
                <xs:sequence>\
                  <xs:element name="QualifierSet" minOccurs="0" maxOccurs="unbounded">\
                    <xs:complexType>\
                      <xs:sequence>\
                        <xs:element name="Qualifier" minOccurs="0" maxOccurs="unbounded">\
                          <xs:complexType>\
                            <xs:attribute name="name" type="xs:string" use="required" />\
                            <xs:attribute name="value" type="xs:string" use="required" />\
                            <xs:attribute name="priority" type="xs:integer" use="required" />\
                            <xs:attribute name="scoreAsDefault" type="xs:decimal" use="required" />\
                            <xs:attribute name="index" type="xs:integer" use="required" />\
                          </xs:complexType>\
                        </xs:element>\
                      </xs:sequence>\
                      <xs:anyAttribute processContents="skip" />\
                    </xs:complexType>\
                  </xs:element>\
                  <xs:element name="Value" type="xs:string"  minOccurs="0" maxOccurs="unbounded"/>\
                </xs:sequence>\
                <xs:attribute name="type" type="candidateType" use="required" />\
              </xs:complexType>\
            </xs:element>\
          </xs:sequence>\
          <xs:attribute name="name" use="required" type="xs:string" />\
          <xs:anyAttribute processContents="skip" />\
        </xs:complexType>\
      </xs:element>\
    </xs:sequence>\
    <xs:attribute name="name" use="required" type="xs:string" />\
    <xs:anyAttribute processContents="skip" />\
  </xs:complexType>\
  <xs:element name="PriInfo">\
    <xs:complexType>\
      <xs:sequence>\
        <xs:element name="PriHeader" >\
          <xs:complexType>\
            <xs:sequence>\
              <xs:any minOccurs ="0" maxOccurs="unbounded" processContents="skip" />\
            </xs:sequence>\
            <xs:anyAttribute processContents="skip" />\
          </xs:complexType>\
        </xs:element>\
        <xs:element name="QualifierInfo">\
          <xs:complexType>\
            <xs:sequence>\
              <xs:any minOccurs="0" maxOccurs="unbounded" processContents="skip" />\
            </xs:sequence>\
          </xs:complexType>\
        </xs:element>\
        <xs:element name="ResourceMap">\
          <xs:complexType>\
            <xs:sequence>\
              <xs:element name="VersionInfo">\
                <xs:complexType>\
                  <xs:anyAttribute processContents="skip" />\
                </xs:complexType>\
              </xs:element>\
              <xs:element minOccurs="0" maxOccurs="unbounded" name="ResourceMapSubtree" type="scopeType" />\
            </xs:sequence>\
            <xs:attribute name="name" type="xs:string" use="required" />\
            <xs:anyAttribute processContents="skip" />\
          </xs:complexType>\
        </xs:element>\
      </xs:sequence>\
    </xs:complexType>\
  </xs:element>\
</xs:schema>
```

<span data-ttu-id="ff84c-141">MakePri unterstützt die Dumptypen „Basic”, „Detailed”, „Schema” und „Summary”.</span><span class="sxs-lookup"><span data-stu-id="ff84c-141">MakePri.exe supports dump types 'Basic', 'Detailed', 'Schema', and 'Summary'.</span></span> <span data-ttu-id="ff84c-142">Damit MakePri.exe einen Dumptyp ausgibt, den der PriInfo-Indexer lesen kann, müssen Sie die Zeichenfolge „/DumpType Detailed” in den `dump`-Befehl aufnehmen.</span><span class="sxs-lookup"><span data-stu-id="ff84c-142">To configure MakePri.exe to emit the dump type that the PriInfo indexer can read, include "/DumpType Detailed" when using the `dump` command.</span></span>

<span data-ttu-id="ff84c-143">Mehrere Elemente der `.pri.xml`-Datei werden von MakePri.exe übersprungen.</span><span class="sxs-lookup"><span data-stu-id="ff84c-143">Several elements of the `.pri.xml` file are skipped by MakePri.exe.</span></span> <span data-ttu-id="ff84c-144">Diese Elemente werden entweder bei der Indizierung erstellt oder sind in der MakePri.exe-Konfigurationsdatei angegeben.</span><span class="sxs-lookup"><span data-stu-id="ff84c-144">These elements are either computed during indexing, or are specified in the MakePri.exe configuration file.</span></span> <span data-ttu-id="ff84c-145">Ressourcennamen, Qualifizierer und Werte in der Dumpdatei werden direkt in der neuen PRI-Datei beibehalten.</span><span class="sxs-lookup"><span data-stu-id="ff84c-145">Resource names, qualifiers, and values that are contained within the dump file are directly maintained in the new PRI file.</span></span> <span data-ttu-id="ff84c-146">Die Ressourcenzuordnung der obersten Ebene wird jedoch nicht in der abschließenden PRI-Datei verwaltet.</span><span class="sxs-lookup"><span data-stu-id="ff84c-146">The top-level resource map, however, is not maintained in the final PRI.</span></span> <span data-ttu-id="ff84c-147">Ressourcenzuordnungen werden bei der Indizierung zusammengeführt.</span><span class="sxs-lookup"><span data-stu-id="ff84c-147">Resource Maps are merged as part of the indexing.</span></span>

<span data-ttu-id="ff84c-148">Hier ein Beispiel für eine gültige Ressource vom Typ „String” aus einer Dumpdatei:</span><span class="sxs-lookup"><span data-stu-id="ff84c-148">This is an example of a valid String type resource from a dump file.</span></span>

```xml
<NamedResource name="SampleString " index="96" uri="ms-resource://SampleApp/resources/SampleString ">
  <Decision index="2">
    <QualifierSet index="1">
      <Qualifier name="Language" value="EN-US" priority="900" scoreAsDefault="1.0" index="1"/>
    </QualifierSet>
  </Decision>
  <Candidate type="String">
    <QualifierSet index="1">
      <Qualifier name="Language" value="EN-US" priority="900" scoreAsDefault="1.0" index="1"/>
    </QualifierSet>
    <Value>A Sample String Value</Value>
  </Candidate>
</NamedResource>
```

<span data-ttu-id="ff84c-149">Hier ein Beispiel für eine gültige Ressource vom Typ „Path” aus einer Dumpdatei:</span><span class="sxs-lookup"><span data-stu-id="ff84c-149">This is an example of a valid Path type resource with two candidates from a dump file.</span></span>

```xml
<NamedResource name="Sample.png" index="77" uri="ms-resource://SampleApp/Files/Images/Sample.png">
  <Decision index="2">
    <QualifierSet index="1">
      <Qualifier name="Scale" value="180" priority="500" scoreAsDefault="1.0" index="1"/>
    </QualifierSet>
    <QualifierSet index="2">
      <Qualifier name="Scale" value="140" priority="500" scoreAsDefault="0.7" index="2"/>
    </QualifierSet>
  </Decision>
  <Candidate type="Path">
    <QualifierSet index="1">
      <Qualifier name="Scale" value="180" priority="500" scoreAsDefault="1.0" index="1"/>
    </QualifierSet>
    <Value>Images\Sample.scale-180.png</Value>
  </Candidate>
  <Candidate type="Path">
    <QualifierSet index="2">
      <Qualifier name="Scale" value="140" priority="500" scoreAsDefault="1.0" index="1"/>
    </QualifierSet>
    <Value>Images\Sample.scale-140.png</Value>
  </Candidate>
</NamedResource>
```

## <a name="resfiles"></a><span data-ttu-id="ff84c-150">ResFiles</span><span class="sxs-lookup"><span data-stu-id="ff84c-150">ResFiles</span></span>

<span data-ttu-id="ff84c-151">Der ResFiles-Indexer wird mit dem `type`-Attribut RESFILES angegeben.</span><span class="sxs-lookup"><span data-stu-id="ff84c-151">The ResFiles indexer is identified by a `type` attribute of RESFILES.</span></span> <span data-ttu-id="ff84c-152">Er indiziert die Inhalte einer `.resfiles`-Datei.</span><span class="sxs-lookup"><span data-stu-id="ff84c-152">It indexes the contents of a `.resfiles` file.</span></span> <span data-ttu-id="ff84c-153">Der zugehörige Konfigurationselement entspricht dem folgenden Schema.</span><span class="sxs-lookup"><span data-stu-id="ff84c-153">Its configuration element conforms to the following schema.</span></span>

```xml
<xs:schema id=\"resx\" xmlns:xs=\"http://www.w3.org/2001/XMLSchema\" elementFormDefault=\"qualified\">\
    <xs:simpleType name=\"IndexerConfigResFilesType\">\
        <xs:restriction base=\"xs:string\">\
            <xs:pattern value=\"((r|R)(e|E)(s|S)(f|F)(i|I)(l|L)(e|E)(s|S))\"/>\
        </xs:restriction>\
    </xs:simpleType>\
    <xs:element name=\"indexer-config\">\
        <xs:complexType>\
            <xs:attribute name=\"type\" type=\"IndexerConfigResFilesType\" use=\"required\"/>\
            <xs:attribute name=\"qualifierDelimiter\" type=\"xs:string\" use=\"required\"/>\
        </xs:complexType>\
    </xs:element>\
</xs:schema>\
```

<span data-ttu-id="ff84c-154">Die `.resfiles`-Datei ist eine Textdatei mit einer flachen Liste von Dateipfaden.</span><span class="sxs-lookup"><span data-stu-id="ff84c-154">A `.resfiles` file is a text file containing a flat list of file paths.</span></span> <span data-ttu-id="ff84c-155">Eine `.resfiles`-Datei kann Kommentare mit Schrägstrichen ("//") enthalten.</span><span class="sxs-lookup"><span data-stu-id="ff84c-155">A `.resfiles` file can contain "//" comments.</span></span> <span data-ttu-id="ff84c-156">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="ff84c-156">Here's an example.</span></span>

```
Strings\component1\fr\elements.resjson
Images\logo.scale-100.png
Images\logo.scale-140.png
Images\logo.scale-180.png
```

## <a name="resjson"></a><span data-ttu-id="ff84c-157">ResJSON</span><span class="sxs-lookup"><span data-stu-id="ff84c-157">ResJSON</span></span>

<span data-ttu-id="ff84c-158">Der ResJSON-Indexer wird mit dem `type`-Attribut RESJSON angegeben.</span><span class="sxs-lookup"><span data-stu-id="ff84c-158">The ResJSON indexer is identified by a `type` attribute of RESJSON.</span></span> <span data-ttu-id="ff84c-159">Er indiziert die Inhalte einer `.resjson`-Datei, bei der es sich um eine Zeichenfolgen-Ressourcendatei handelt.</span><span class="sxs-lookup"><span data-stu-id="ff84c-159">It indexes the contents of a `.resjson` file, which is a string resource file.</span></span> <span data-ttu-id="ff84c-160">Der zugehörige Konfigurationselement entspricht dem folgenden Schema.</span><span class="sxs-lookup"><span data-stu-id="ff84c-160">Its configuration element conforms to the following schema.</span></span>

```xml
<xs:schema id=\"resjson\" xmlns:xs=\"http://www.w3.org/2001/XMLSchema\" elementFormDefault=\"qualified\">\
    <xs:simpleType name=\"IndexerConfigResJsonType\">\
        <xs:restriction base=\"xs:string\">\
            <xs:pattern value=\"((r|R)(e|E)(s|S)(j|J)(s|S)(o|O)(n|N))\"/>\
        </xs:restriction>\
    </xs:simpleType>\
    <xs:element name=\"indexer-config\">\
        <xs:complexType>\
            <xs:attribute name=\"type\" type=\"IndexerConfigResJsonType\" use=\"required\"/>\
            <xs:attribute name=\"initialPath\" type=\"xs:string\" use=\"optional\"/>\
        </xs:complexType>\
    </xs:element>\
</xs:schema>\
```

<span data-ttu-id="ff84c-161">Eine `.resjson`-Datei enthält JSON-Text (siehe [Anwendungs-/JSON-Medientyp für JavaScript Object Notation (JSON)](http://www.ietf.org/rfc/rfc4627.txt)).</span><span class="sxs-lookup"><span data-stu-id="ff84c-161">A `.resjson` file contains JSON text (see [The application/json Media Type for JavaScript Object Notation (JSON)](http://www.ietf.org/rfc/rfc4627.txt)).</span></span> <span data-ttu-id="ff84c-162">Die Datei muss ein einzelnes JSON-Objekt mit hierarchischen Eigenschaften enthalten.</span><span class="sxs-lookup"><span data-stu-id="ff84c-162">The file must contain a single JSON object with hierarchical properties.</span></span> <span data-ttu-id="ff84c-163">Jede Eigenschaft muss ein anderes JSON-Objekt oder ein Zeichenfolgenwert sein.</span><span class="sxs-lookup"><span data-stu-id="ff84c-163">Each property must either be another JSON object or a string value.</span></span>

<span data-ttu-id="ff84c-164">JSON-Eigenschaften, deren Name mit einem Unterstrich (_) beginnt, werden nicht in die abschließende PRI-Datei kompiliert, sondern in der Protokolldatei beibehalten.</span><span class="sxs-lookup"><span data-stu-id="ff84c-164">JSON properties with names that begin with an underscore ("_") are not compiled into the final PRI file, but are maintained in the log file.</span></span>

<span data-ttu-id="ff84c-165">Die Datei kann auch „// ”-Kommentare enthalten. Diese werden bei der Analyse ignoriert.</span><span class="sxs-lookup"><span data-stu-id="ff84c-165">The file can also contain "//" comments which are ignored during parsing.</span></span>

<span data-ttu-id="ff84c-166">Das `initialPath`-Attribut platziert alle Ressourcen unter diesem Anfangspfad. Zu diesem Zweck wird das Attribut dem Namen der Ressource vorangestellt.</span><span class="sxs-lookup"><span data-stu-id="ff84c-166">The `initialPath` attribute places all resources under this initial path by prepending it to the name of the resource.</span></span> <span data-ttu-id="ff84c-167">Diese Vorgehensweise findet normalerweise bei der Indizierung der Ressourcen von Klassenbibliotheken Anwendung.</span><span class="sxs-lookup"><span data-stu-id="ff84c-167">You would typically use this when indexing class library resources.</span></span> <span data-ttu-id="ff84c-168">Der Standardwert ist leer.</span><span class="sxs-lookup"><span data-stu-id="ff84c-168">The default is blank.</span></span>

## <a name="resw"></a><span data-ttu-id="ff84c-169">ResW</span><span class="sxs-lookup"><span data-stu-id="ff84c-169">ResW</span></span>

<span data-ttu-id="ff84c-170">Der ResW-Indexer wird mit dem `type`-Aattribut RESW angegeben.</span><span class="sxs-lookup"><span data-stu-id="ff84c-170">The ResW indexer is identified by a `type` attribute of RESW.</span></span> <span data-ttu-id="ff84c-171">Er indiziert die Inhalte einer `.resw`-Datei, bei der es sich um eine Zeichenfolgen-Ressourcendatei handelt.</span><span class="sxs-lookup"><span data-stu-id="ff84c-171">It indexes the contents of a `.resw` file, which is a string resource file.</span></span> <span data-ttu-id="ff84c-172">Der zugehörige Konfigurationselement entspricht dem folgenden Schema.</span><span class="sxs-lookup"><span data-stu-id="ff84c-172">Its configuration element conforms to the following schema.</span></span>

```xml
<xs:schema id=\"resw\" xmlns:xs=\"http://www.w3.org/2001/XMLSchema\" elementFormDefault=\"qualified\">\
    <xs:simpleType name=\"IndexerConfigResxType\">\
        <xs:restriction base=\"xs:string\">\
            <xs:pattern value=\"((r|R)(e|E)(s|S)(w|W))\"/>\
        </xs:restriction>\
    </xs:simpleType>\
    <xs:element name=\"indexer-config\">\
        <xs:complexType>\
            <xs:attribute name=\"type\" type=\"IndexerConfigResxType\" use=\"required\"/>\
            <xs:attribute name=\"convertDotsToSlashes\" type=\"xs:boolean\" use=\"required\"/>\
            <xs:attribute name=\"initialPath\" type=\"xs:string\" use=\"optional\"/>\
        </xs:complexType>\
    </xs:element>\
</xs:schema>\
```

<span data-ttu-id="ff84c-173">Eine `.resw`-Datei ist eine XML-Datei, die dem folgendem Schema entspricht.</span><span class="sxs-lookup"><span data-stu-id="ff84c-173">A `.resw` file is an XML file that conforms to the following schema.</span></span>

```xml
  <xsd:schema id="root" xmlns="" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">
    <xsd:import namespace="http://www.w3.org/XML/1998/namespace" />
    <xsd:element name="root" msdata:IsDataSet="true">
      <xsd:complexType>
        <xsd:choice maxOccurs="unbounded">
          <xsd:element name="metadata">
            <xsd:complexType>
              <xsd:sequence>
                <xsd:element name="value" type="xsd:string" minOccurs="0" />
              </xsd:sequence>
              <xsd:attribute name="name" use="required" type="xsd:string" />
              <xsd:attribute name="type" type="xsd:string" />
              <xsd:attribute name="mimetype" type="xsd:string" />
              <xsd:attribute ref="xml:space" />
            </xsd:complexType>
          </xsd:element>
          <xsd:element name="assembly">
            <xsd:complexType>
              <xsd:attribute name="alias" type="xsd:string" />
              <xsd:attribute name="name" type="xsd:string" />
            </xsd:complexType>
          </xsd:element>
          <xsd:element name="data">
            <xsd:complexType>
              <xsd:sequence>
                <xsd:element name="value" type="xsd:string" minOccurs="0" msdata:Ordinal="1" />
                <xsd:element name="comment" type="xsd:string" minOccurs="0" msdata:Ordinal="2" />
              </xsd:sequence>
              <xsd:attribute name="name" type="xsd:string" use="required" msdata:Ordinal="1" />
              <xsd:attribute name="type" type="xsd:string" msdata:Ordinal="3" />
              <xsd:attribute name="mimetype" type="xsd:string" msdata:Ordinal="4" />
              <xsd:attribute ref="xml:space" />
            </xsd:complexType>
          </xsd:element>
          <xsd:element name="resheader">
            <xsd:complexType>
              <xsd:sequence>
                <xsd:element name="value" type="xsd:string" minOccurs="0" msdata:Ordinal="1" />
              </xsd:sequence>
              <xsd:attribute name="name" type="xsd:string" use="required" />
            </xsd:complexType>
          </xsd:element>
        </xsd:choice>
      </xsd:complexType>
    </xsd:element>
  </xsd:schema>
```

<span data-ttu-id="ff84c-174">Das Attribut `convertDotsToSlashes` bewirkt, dass alle Punkte (.) in Ressourcennamen (Namensattribute von Datenelementen) in einen Schrägstrich (/) konvertiert werden. Dies gilt jedoch nicht für Punkte zwischen eckigen Klammern ([ und ]).</span><span class="sxs-lookup"><span data-stu-id="ff84c-174">The `convertDotsToSlashes` attribute converts all dot (".") characters found in resource names (data element name attributes) to a forward slash "/", except when the dot characters are between a "[" and "]".</span></span>

<span data-ttu-id="ff84c-175">Das `initialPath`-Attribut platziert alle Ressourcen unter diesem Anfangspfad. Zu diesem Zweck wird das Attribut dem Namen der Ressource vorangestellt.</span><span class="sxs-lookup"><span data-stu-id="ff84c-175">The `initialPath` attribute places all resources under this initial path by prepending it to the name of the resource.</span></span> <span data-ttu-id="ff84c-176">Diese Vorgehensweise findet normalerweise bei der Indizierung der Ressourcen von Klassenbibliotheken Anwendung.</span><span class="sxs-lookup"><span data-stu-id="ff84c-176">You typically use this when indexing class library resources.</span></span> <span data-ttu-id="ff84c-177">In der Standardeinstellung ist kein Wert angegeben.</span><span class="sxs-lookup"><span data-stu-id="ff84c-177">The default is blank.</span></span>

## <a name="related-topics"></a><span data-ttu-id="ff84c-178">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="ff84c-178">Related topics</span></span>

* [<span data-ttu-id="ff84c-179">Manuelles Kompilieren von Ressourcen mit MakePri.exe</span><span class="sxs-lookup"><span data-stu-id="ff84c-179">Compile resources manually with MakePri.exe</span></span>](compile-resources-manually-with-makepri.md)
* [<span data-ttu-id="ff84c-180">Befehlszeilenoptionen für MakePri.exe</span><span class="sxs-lookup"><span data-stu-id="ff84c-180">MakePri.exe command-line options</span></span>](makepri-exe-command-options.md)
* [<span data-ttu-id="ff84c-181">Konfigurationsdatei für MakePri.exe</span><span class="sxs-lookup"><span data-stu-id="ff84c-181">MakePri.exe configuration file</span></span>](makepri-exe-configuration.md)
* [<span data-ttu-id="ff84c-182">Anwendungs-/JSON-Medientyp für JavaScript Object Notation (JSON)</span><span class="sxs-lookup"><span data-stu-id="ff84c-182">The application/json Media Type for JavaScript Object Notation (JSON)</span></span>](http://www.ietf.org/rfc/rfc4627.txt)