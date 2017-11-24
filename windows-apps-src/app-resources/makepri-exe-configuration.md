---
author: stevewhims
Description: "In diesem Thema wird das Schema der XML-Konfigurationsdatei für MakePri.exe beschrieben."
title: "Konfigurationsdatei für MakePRI.exe"
template: detail.hbs
ms.author: stwhi
ms.date: 10/18/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Ressourcen, Bild, Element, MRT, Qualifizierer
localizationpriority: medium
ms.openlocfilehash: 7d19d1d778b434abd25d0d087159ea79521642e8
ms.sourcegitcommit: 44a24b580feea0f188c7eae36e72e4a4f412802b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

# <a name="makepriexe-configuration-file"></a><span data-ttu-id="d4b35-104">Konfigurationsdatei für MakePRI.exe</span><span class="sxs-lookup"><span data-stu-id="d4b35-104">MakePri.exe configuration file</span></span>

<span data-ttu-id="d4b35-105">In diesem Thema wird das Schema der XML-Konfigurationsdatei (auch PRI-Konfigurationsdatei genannt) für [MakePri.exe](compile-resources-manually-with-makepri.md) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="d4b35-105">This topic describes the schema of the [MakePri.exe](compile-resources-manually-with-makepri.md) XML configuration file; also known as a PRI config file.</span></span> <span data-ttu-id="d4b35-106">Das Tool MakePri.exe verfügt über den Befehl [createconfig](makepri-exe-command-options.md#createconfig-command), der eine neue, initialisierte PRI-Konfigurationsdatei erstellt.</span><span class="sxs-lookup"><span data-stu-id="d4b35-106">The MakePri.exe tool has a [createconfig command](makepri-exe-command-options.md#createconfig-command) that you can use to create a new, initialized PRI config file.</span></span>

<span data-ttu-id="d4b35-107">Die PRI-Konfigurationsdatei steuert, welche Ressourcen wie indiziert werden.</span><span class="sxs-lookup"><span data-stu-id="d4b35-107">The PRI config file controls what resources are indexed, and how.</span></span> <span data-ttu-id="d4b35-108">Die XML-Konfigurationsdatei muss folgendem Schema entsprechen:</span><span class="sxs-lookup"><span data-stu-id="d4b35-108">The configuration XML must conform to the following schema.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="resources">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="packaging" maxOccurs="1" minOccurs="0">
          <xs:complexType>
            <xs:sequence>
              <xs:element name="autoResourcePackage" maxOccurs="unbounded" minOccurs="0">
                <xs:complexType>
                  <xs:attribute name="qualifier" type="xs:string" use="required" />
                </xs:complexType>
              </xs:element>
              <xs:element name="resourcePackage" maxOccurs="unbounded" minOccurs="0">
                <xs:complexType>
                  <xs:sequence>
                    <xs:element name="qualifierSet" maxOccurs="unbounded" minOccurs="0">
                      <xs:complexType>
                        <xs:attribute name="definition" type="xs:string" use="required" />
                      </xs:complexType>
                    </xs:element>
                  </xs:sequence>
                  <xs:attribute name="name" type="xs:string" use="required" />
                </xs:complexType>
              </xs:element>
            </xs:sequence>
          </xs:complexType>
        </xs:element>
        <xs:element maxOccurs="unbounded" name="index">
          <xs:complexType>
            <xs:sequence>
              <xs:element name="qualifiers" minOccurs="0" maxOccurs="unbounded">
                <xs:complexType>
                  <xs:sequence>
                    <xs:element minOccurs="1" maxOccurs="unbounded" name="qualifier">
                      <xs:complexType>
                        <xs:attribute name="name" type="xs:string" use="required" />
                        <xs:attribute name="value" type="xs:string" use="required" />
                      </xs:complexType>
                    </xs:element>
                  </xs:sequence>
                </xs:complexType>
              </xs:element>
              <xs:element name="default" minOccurs="0" maxOccurs="unbounded">
                <xs:complexType>
                  <xs:sequence>
                    <xs:element minOccurs="1" maxOccurs="unbounded" name="qualifier">
                      <xs:complexType>
                        <xs:attribute name="name" type="xs:string" use="required" />
                        <xs:attribute name="value" type="xs:string" use="required" />
                      </xs:complexType>
                    </xs:element>
                  </xs:sequence>
                </xs:complexType>
              </xs:element>
              <xs:element name="indexer-config" minOccurs="0" maxOccurs="unbounded">
                <xs:complexType>
                  <xs:sequence>
                    <xs:any minOccurs="0" maxOccurs="unbounded" processContents="skip"/>
                  </xs:sequence>
                  <xs:attribute name="type" type="xs:string" use="required" />
                  <xs:anyAttribute processContents="skip"/>
                </xs:complexType>
              </xs:element>
            </xs:sequence>
            <xs:attribute name="root" type="xs:string" use="required" />
            <xs:attribute name="startIndexAt" type="xs:string" use="required" />
          </xs:complexType>
        </xs:element>
      </xs:sequence>
      <xs:attribute name="isDeploymentMergeable" type="xs:boolean" use="optional" />
      <xs:attribute name="majorVersion" type="xs:positiveInteger" use="optional" />
      <xs:attribute name="targetOsVersion" type="xs:string" use="optional" />
    </xs:complexType>
  </xs:element>
</xs:schema>
```

- <span data-ttu-id="d4b35-109">Das Element `default` gibt den Kontext (Sprache, Skalierung, Kontrast usw.) an, der zur Auflösung der Ressourcen verwendet werden soll, wenn keine passenden Kandidaten als Ressourcen für den Laufzeitkontext vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="d4b35-109">The `default` element specifies the context (language, scale, contrast, etc.) that should be used to resolve resources when the runtime context does not match any resource candidates.</span></span> <span data-ttu-id="d4b35-110">Da dieser Kontext zur Erstellungszeit angegeben wird und sich nicht ändert, werden die Ressourcen für diesen Kontext aufgelöst, sobald Qualifizierer erstellt worden sind.</span><span class="sxs-lookup"><span data-stu-id="d4b35-110">Because this context is specified at build time and does not change, resources are resolved to this context as qualifiers are created.</span></span> <span data-ttu-id="d4b35-111">Die passende Bewertung wird zur Erstellungszeit gespeichert.</span><span class="sxs-lookup"><span data-stu-id="d4b35-111">The matched score is stored at build time.</span></span> <span data-ttu-id="d4b35-112">Für jeden Qualifizierer muss ein Wert angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="d4b35-112">Every qualifier must have some value specified.</span></span> <span data-ttu-id="d4b35-113">Weitere Informationen zur Ressourcenauswahl finden Sie unter [ResourceContext](resource-management-system.md#resourcecontext).</span><span class="sxs-lookup"><span data-stu-id="d4b35-113">See [ResourceContext](resource-management-system.md#resourcecontext) for details on how resources are chosen.</span></span>
- <span data-ttu-id="d4b35-114">Das Element `index` definiert separate Indizierungsdurchläufe, die für die Ressourcen durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="d4b35-114">The `index` element defines discrete indexing passes that are done over the assets.</span></span> <span data-ttu-id="d4b35-115">Jeder Indizierungsdurchlauf bestimmt die zu verwendenden [formatspezifischen Indexer](makepri-exe-format-specific-indexers.md) und die zu indizierenden Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="d4b35-115">Each indexing pass determines the [format-specific indexers](makepri-exe-format-specific-indexers.md) to use, and which resources to index.</span></span>
- <span data-ttu-id="d4b35-116">Das Element `qualifiers` legt die anfänglichen Qualifizierer für die erste Datei bzw. für den ersten Ordner fest, die andere Ressourcen erben.</span><span class="sxs-lookup"><span data-stu-id="d4b35-116">The `qualifiers` element sets the initial qualifiers for the first file or folder that other resources inherit.</span></span> <span data-ttu-id="d4b35-117">Jedes Qualifiziererelement muss einen gültigen Namen und einen gültigen Wert besitzen (siehe [Anpassen von Ressourcen mit Qualifizierern für Sprache, Skalierung, hohen Kontrast und andere Eigenschaften](tailor-resources-lang-scale-contrast.md)).</span><span class="sxs-lookup"><span data-stu-id="d4b35-117">Each qualifier element must have a valid name and value (see [Tailor your resources for language, scale, high contrast, and other qualifiers](tailor-resources-lang-scale-contrast.md)).</span></span>
- <span data-ttu-id="d4b35-118">Das Attribut `root` ist der Stamm des Dateipfads der physischen Datei für den Indizierungsdurchlauf.</span><span class="sxs-lookup"><span data-stu-id="d4b35-118">The `root` attribute is the path root of the physical file for the index pass.</span></span> <span data-ttu-id="d4b35-119">Er kann relativ oder absolut sein.</span><span class="sxs-lookup"><span data-stu-id="d4b35-119">It can be relative or absolute.</span></span> <span data-ttu-id="d4b35-120">Wenn er relativ ist, wird er an den Projektstamm angehängt, den Sie an der Befehlszeile angeben.</span><span class="sxs-lookup"><span data-stu-id="d4b35-120">If relative, it is appended to the project root that you provide in the command line.</span></span> <span data-ttu-id="d4b35-121">Wenn er absolut ist, wird er direkt als Stamm für den Indizierungsdurchlauf verwendet.</span><span class="sxs-lookup"><span data-stu-id="d4b35-121">If absolute, it is directly used as the index pass root.</span></span> <span data-ttu-id="d4b35-122">Es können sowohl Schrägstriche als auch umgekehrte Schrägstriche verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="d4b35-122">Back or forward slashes are acceptable.</span></span> <span data-ttu-id="d4b35-123">Nachgestellte Leerzeichen werden entfernt.</span><span class="sxs-lookup"><span data-stu-id="d4b35-123">Trailing slashes are trimmed.</span></span> <span data-ttu-id="d4b35-124">Der Stamm des Indizierungsdurchlaufs bestimmt den Ordner, zu dem alle Ressourcen als relativ betrachtet werden.</span><span class="sxs-lookup"><span data-stu-id="d4b35-124">The root of the index pass determines the folder to which all resources are considered relative.</span></span>
- <span data-ttu-id="d4b35-125">Das `startIndexAt`-Attribut bezeichnet die Ausgangsdatei oder den Ausgangsordner, der bei der Indizierung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d4b35-125">The `startIndexAt` attribute is the initial seed file or folder used in indexing.</span></span> <span data-ttu-id="d4b35-126">Es ist relativ zum Stamm des Indizierungsdurchlaufs.</span><span class="sxs-lookup"><span data-stu-id="d4b35-126">It is relative to the index pass root.</span></span> <span data-ttu-id="d4b35-127">Bei einem leeren Wert wird vom Stammordner des Indizierungsdurchlaufs ausgegangen.</span><span class="sxs-lookup"><span data-stu-id="d4b35-127">An empty value assumes the index pass root folder.</span></span>

## <a name="default-pri-config-file"></a><span data-ttu-id="d4b35-128">Standard-PRI-Konfigurationsdatei</span><span class="sxs-lookup"><span data-stu-id="d4b35-128">Default PRI config file</span></span>

<span data-ttu-id="d4b35-129">MakePri.exe generiert diese neue, initialisiert PRI-Konfigurationsdatei, wenn der Befehl [createconfig](makepri-exe-command-options.md#createconfig-command) aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="d4b35-129">MakePri.exe generates this new, initialized PRI config file when the [createconfig command](makepri-exe-command-options.md#createconfig-command) is issued.</span></span>

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<resources targetOsVersion="10.0.0" majorVersion="1">
  <packaging>
    <autoResourcePackage qualifier="Language"/>
    <autoResourcePackage qualifier="Scale"/>
    <autoResourcePackage qualifier="DXFeatureLevel"/>
  </packaging>
  <index root="\" startIndexAt="\">
    <default>
      <qualifier name="Language" value="en-US"/>
      <qualifier name="Contrast" value="standard"/>
      <qualifier name="Scale" value="100"/>
      <qualifier name="HomeRegion" value="001"/>
      <qualifier name="TargetSize" value="256"/>
      <qualifier name="LayoutDirection" value="LTR"/>
      <qualifier name="Theme" value="dark"/>
      <qualifier name="AlternateForm" value=""/>
      <qualifier name="DXFeatureLevel" value="DX9"/>
      <qualifier name="Configuration" value=""/>
      <qualifier name="DeviceFamily" value="Universal"/>
      <qualifier name="Custom" value=""/>
    </default>
    <indexer-config type="folder" foldernameAsQualifier="true" filenameAsQualifier="true" qualifierDelimiter="."/>
    <indexer-config type="resw" convertDotsToSlashes="true" initialPath=""/>
    <indexer-config type="resjson" initialPath=""/>
    <indexer-config type="PRI"/>
  </index>
  <!--<index startIndexAt="Start Index Here" root="Root Here">-->
  <!--        <indexer-config type="resfiles" qualifierDelimiter="."/>-->
  <!--        <indexer-config type="priinfo" emitStrings="true" emitPaths="true" emitEmbeddedData="true"/>-->
  <!--</index>-->
</resources>
```

## <a name="packaging-element"></a><span data-ttu-id="d4b35-130">Packaging-Element</span><span class="sxs-lookup"><span data-stu-id="d4b35-130">Packaging element</span></span>

<span data-ttu-id="d4b35-131">Die Element `packaging` definiert PRI-Aufteilungsinformationen.</span><span class="sxs-lookup"><span data-stu-id="d4b35-131">The `packaging` element defines PRI split information.</span></span> <span data-ttu-id="d4b35-132">Das Schema für das Element `packaging` kann sowohl für automatische Konfiguration (Unterstützung für `autoResourcePackage` für eine spezifische Dimension) als auch für manuelle Konfiguration definiert werden.</span><span class="sxs-lookup"><span data-stu-id="d4b35-132">The schema for the `packaging` element is defined for both automatic (support for `autoResourcePackage` along a specific dimension), and manual configuration.</span></span>

<span data-ttu-id="d4b35-133">Dieses Beispiel zeigt die Verwendung von `autoResourcePackage` für eine spezifische Dimension:</span><span class="sxs-lookup"><span data-stu-id="d4b35-133">This example shows how to use `autoResourcePackage` along a specific dimension.</span></span>

```xml
    <packaging>
        <autoResourcePackage qualifier="Language"/>
        <autoResourcePackage qualifier="Scale"/>
        <autoResourcePackage qualifier="DXFeatureLevel"/>
    </packaging>
```

<span data-ttu-id="d4b35-134">Dieses Beispiel zeigt die manuelle Anwendung von `resourcePackage`:</span><span class="sxs-lookup"><span data-stu-id="d4b35-134">This example shows how to use manual `resourcePackage`.</span></span>

```xml
  <packaging>
    <resourcePackage name="Germany">
      <qualifierSet definition="lang-de-de"/>
      <qualifierSet definition="lang-es-es"/>
    </resourcePackage>  
    <resourcePackage name="France">
      <qualifierSet definition="lang-fr-fr"/>
    </resourcePackage>  
    <resourcePackage name="HighRes1">
      <qualifierSet definition="scale-200"/>
    </resourcePackage>
    <resourcePackage name="HighRes2">
      <qualifierSet definition="scale-400"/>
    </resourcePackage>
  </packaging>
```

<span data-ttu-id="d4b35-135">Die Erzeugung von PRI-Ressourcendateien für eine spezifische Dimension wird von MakePri.exe nicht explizit blockiert.</span><span class="sxs-lookup"><span data-stu-id="d4b35-135">MakePri.exe doesn't explicitly block generation of resource PRI files along any specific dimension.</span></span> <span data-ttu-id="d4b35-136">Einschränkungen für eine bestimmte Gruppe von Dimensionen werden extern mithilfe von MakeAppx.exe oder anderen Tools der Pipeline definiert und implementiert.</span><span class="sxs-lookup"><span data-stu-id="d4b35-136">Restrictions along a certain set of dimensions are defined and implemented externally by either MakeAppx.exe or other tools in the pipeline.</span></span>

<span data-ttu-id="d4b35-137">MakePri.exe analysiert das Element `packaging` nach allen Knoten `index`-Knoten, um alle Standardqualifizierer aufzufüllen.</span><span class="sxs-lookup"><span data-stu-id="d4b35-137">MakePri.exe parses the `packaging` element after all the `index` nodes to populate all the default qualifiers.</span></span> <span data-ttu-id="d4b35-138">MakePri.exe sammelt die gewonnenen Informationen in diesen Datenstrukturen:</span><span class="sxs-lookup"><span data-stu-id="d4b35-138">MakePri.exe collects parsed info in these data structures.</span></span>

**<span data-ttu-id="d4b35-139">C#</span><span class="sxs-lookup"><span data-stu-id="d4b35-139">C#</span></span>**
```csharp
enum ResourcePackageMode
{
    None,
    AutoPackQualifier,
    ManualPack
}

ResourcePackageMode eResourcePackageMode;
list<string> RPQualifierList; // To store AutoResourcePackage Qualifiers
map<string, list<string>> RPNameToQSIMap; // To store ResourcePackage name to QualifierSet list mapping.
```

## <a name="resourcesisdeploymentmergeable-attribute"></a><span data-ttu-id="d4b35-140">resources@isDeploymentMergeable-Attribut</span><span class="sxs-lookup"><span data-stu-id="d4b35-140">resources@isDeploymentMergeable attribute</span></span>

<span data-ttu-id="d4b35-141">Dieses Attribut setzt ein Flag in der PRI-Datei, das Folgendes bewirkt:</span><span class="sxs-lookup"><span data-stu-id="d4b35-141">This attribute sets a flag in the PRI file that causes</span></span>

- <span data-ttu-id="d4b35-142">Bereitstellungszusammenführung, um zu identifizieren, ob diese PRI-Datei für die Zusammenführung geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="d4b35-142">Deployment merge to identify that this PRI file can merge.</span></span>
- <span data-ttu-id="d4b35-143">Von GetFullyQualifiedReference wird ein Fehler zurückgegeben, falls dieses Kennzeichen festgelegt und der Ressourcen-Manager mit einer Datei initialisiert wurde.</span><span class="sxs-lookup"><span data-stu-id="d4b35-143">GetFullyQualifiedReference to return an error in case this flag is set and the resource manager has been initialized with a file.</span></span>

<span data-ttu-id="d4b35-144">Der Standardwert dieses Attributs ist `true`.</span><span class="sxs-lookup"><span data-stu-id="d4b35-144">The default value of this attribute is `true`.</span></span> <span data-ttu-id="d4b35-145">MakePri.exe setzt das Flag in PRI nur im Zusammenhang mit Windows 10.</span><span class="sxs-lookup"><span data-stu-id="d4b35-145">MakePri.exe only sets the flag in PRI if you target Windows 10.</span></span>

<span data-ttu-id="d4b35-146">Wir empfehlen, das Flag `isDeploymentMergeable` bei der Erstellung von Ressourcenpaketen für Windows 10 nicht zu verwenden (oder es explizit auf `true` zu setzen).</span><span class="sxs-lookup"><span data-stu-id="d4b35-146">We recommend that you omit `isDeploymentMergeable` (or set it explicitly to `true`) for resource pack creation if you target Windows 10.</span></span>

<span data-ttu-id="d4b35-147">MakePri.exe fügt den Wert von `isDeploymentMergeable` der Dumpdatei hinzu, wenn `makepri dump` mit der Option `/dt detailed` ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="d4b35-147">MakePri.exe adds the value of `isDeploymentMergeable` to the dump file if `makepri dump` is run with the `/dt detailed` option.</span></span>

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<PriInfo>
    <PriHeader>
        ...
        <IsDeploymentMergeable>true</IsDeploymentMergeable>
        ...
    </PriHeader>
  ...
</PriInfo>
```

## <a name="resourcesmajorversion-attribute"></a><span data-ttu-id="d4b35-148">resources@majorVersion-Attribut</span><span class="sxs-lookup"><span data-stu-id="d4b35-148">resources@majorVersion attribute</span></span>

<span data-ttu-id="d4b35-149">Der Standardwert für dieses Attribut ist 1.</span><span class="sxs-lookup"><span data-stu-id="d4b35-149">The default value for this attribute is 1.</span></span> <span data-ttu-id="d4b35-150">Wenn Sie einen expliziten Wert angeben und auch die veraltete Befehlszeilenoption `/VersionMajor(vma)` für das MakePri.exe-Tool verwenden, hat der Wert in der Konfigurationsdatei Vorrang.</span><span class="sxs-lookup"><span data-stu-id="d4b35-150">If you provide an explicit value, and you also use the deprecated `/VersionMajor(vma)` command-line option for the MakePri.exe tool, then the value in the config file takes precedence.</span></span>

<span data-ttu-id="d4b35-151">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="d4b35-151">Here's an example.</span></span>

```xml
<resources majorVersion="2">
  <packaging ... />
  <index root="\" startIndexAt="\">
    ...
  </index>
</resources>
```

## <a name="resourcestargetosversion-attribute"></a><span data-ttu-id="d4b35-152">resources@targetOsVersion-Attribut</span><span class="sxs-lookup"><span data-stu-id="d4b35-152">resources@targetOsVersion attribute</span></span>

<span data-ttu-id="d4b35-153">Gibt die Zielbetriebssystemversion an.</span><span class="sxs-lookup"><span data-stu-id="d4b35-153">Indicates the target operating system version.</span></span> <span data-ttu-id="d4b35-154">Die folgenden Tabelle enthält die unterstützten Werte. Der Standardwert ist 6.3.0.</span><span class="sxs-lookup"><span data-stu-id="d4b35-154">The table below shows the values that are supported; the default value is 6.3.0.</span></span>

| <span data-ttu-id="d4b35-155">Wert</span><span class="sxs-lookup"><span data-stu-id="d4b35-155">Value</span></span> | <span data-ttu-id="d4b35-156">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="d4b35-156">Meaning</span></span> |
| ----- | ------- |
| <span data-ttu-id="d4b35-157">10.0.0</span><span class="sxs-lookup"><span data-stu-id="d4b35-157">10.0.0</span></span> | <span data-ttu-id="d4b35-158">Windows 10</span><span class="sxs-lookup"><span data-stu-id="d4b35-158">Windows 10</span></span> |
| <span data-ttu-id="d4b35-159">6.3.0 (Standard)</span><span class="sxs-lookup"><span data-stu-id="d4b35-159">6.3.0 (default)</span></span> | <span data-ttu-id="d4b35-160">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="d4b35-160">Windows 8.1</span></span> |
| <span data-ttu-id="d4b35-161">6.2.1</span><span class="sxs-lookup"><span data-stu-id="d4b35-161">6.2.1</span></span> | <span data-ttu-id="d4b35-162">Windows 8</span><span class="sxs-lookup"><span data-stu-id="d4b35-162">Windows 8</span></span> |

<span data-ttu-id="d4b35-163">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="d4b35-163">Here's an example.</span></span>

```xml
<resources targetOsVersion="10.0.0">
  <packaging ... />
  <index root="\" startIndexAt="\">
    ...
  </index>
</resources>
```

<span data-ttu-id="d4b35-164">**Hinweis:** Windows ist in Bezug auf die PRI-Dateien abwärtskompatibel, aber nicht immer aufwärtskompatibel.</span><span class="sxs-lookup"><span data-stu-id="d4b35-164">**Note** Windows is backward compatible with respect to PRI files; but not always forward compatible.</span></span>

<span data-ttu-id="d4b35-165">MakePri.exe fügt den Wert von `targetOsVersion` der Dumpdatei hinzu, wenn `makepri dump` mit der Option `/dt detailed` ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="d4b35-165">MakePri.exe adds the value of `targetOsVersion` to the dump file if `makepri dump` is run with the `/dt detailed` option.</span></span>

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<PriInfo>
    <PriHeader>
        ...
        <TargetOS version="10.0.0"/>
        ...
    </PriHeader>
  ...
</PriInfo>
```

## <a name="validation-error-messages"></a><span data-ttu-id="d4b35-166">Fehlermeldungen bei der Überprüfung</span><span class="sxs-lookup"><span data-stu-id="d4b35-166">Validation error messages</span></span>

<span data-ttu-id="d4b35-167">Hier einige Beispiele für Fehlerbedingungen und die entsprechenden Fehlermeldungen:</span><span class="sxs-lookup"><span data-stu-id="d4b35-167">Here are some example error conditions, and the corresponding error message.</span></span>

| <span data-ttu-id="d4b35-168">Bedingung</span><span class="sxs-lookup"><span data-stu-id="d4b35-168">Condition</span></span> | <span data-ttu-id="d4b35-169">Schweregrad</span><span class="sxs-lookup"><span data-stu-id="d4b35-169">Severity</span></span> | <span data-ttu-id="d4b35-170">Meldung</span><span class="sxs-lookup"><span data-stu-id="d4b35-170">Message</span></span> |
| --------- | -------- | ------- |
| <span data-ttu-id="d4b35-171">Für targetOsVersion ist keiner der unterstützten Werte angegeben.</span><span class="sxs-lookup"><span data-stu-id="d4b35-171">A targetOsVersion other than one of the supported values is specified.</span></span> | <span data-ttu-id="d4b35-172">Fehler</span><span class="sxs-lookup"><span data-stu-id="d4b35-172">Error</span></span> | <span data-ttu-id="d4b35-173">Ungültige Konfiguration: Die Angabe für targetOsVersion ist ungültig.</span><span class="sxs-lookup"><span data-stu-id="d4b35-173">Invalid Configuration: Invalid targetOsVersion specified.</span></span> |
| <span data-ttu-id="d4b35-174">Für targetOsVersion wurde der Wert „6.2.1 ”angegeben, und es ist ein `packaging`-Element vorhanden.</span><span class="sxs-lookup"><span data-stu-id="d4b35-174">A targetOsVersion of "6.2.1" is specified and a `packaging` element is present.</span></span> | <span data-ttu-id="d4b35-175">Fehler</span><span class="sxs-lookup"><span data-stu-id="d4b35-175">Error</span></span> | <span data-ttu-id="d4b35-176">Ungültige Konfiguration: Knoten „Packaging” wird von dieser targetOsVersion nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d4b35-176">Invalid Configuration: 'Packaging' node is not supported with this targetOsVersion.</span></span> |
| <span data-ttu-id="d4b35-177">In der Konfiguration wurde mehr als ein Modus gefunden.</span><span class="sxs-lookup"><span data-stu-id="d4b35-177">More than one mode found in the configuration.</span></span> <span data-ttu-id="d4b35-178">Beispielsweise wurde "Manual" und "AutoResourcePackage" angegeben.</span><span class="sxs-lookup"><span data-stu-id="d4b35-178">For example, Manual and AutoResourcePackage specified.</span></span> | <span data-ttu-id="d4b35-179">Fehler</span><span class="sxs-lookup"><span data-stu-id="d4b35-179">Error</span></span> | <span data-ttu-id="d4b35-180">Ungültige Konfiguration: Knoten „Packaging” unterstützt nur einen Betriebsmodus.</span><span class="sxs-lookup"><span data-stu-id="d4b35-180">Invalid Configuration: 'packaging' node cannot have more than one mode of operation.</span></span> |
| <span data-ttu-id="d4b35-181">Für das Ressourcenpaket ist ein Standardqualifizierer angegeben.</span><span class="sxs-lookup"><span data-stu-id="d4b35-181">A default qualifier is listed under resource package.</span></span> | <span data-ttu-id="d4b35-182">Fehler</span><span class="sxs-lookup"><span data-stu-id="d4b35-182">Error</span></span> | <span data-ttu-id="d4b35-183">Ungültige Konfiguration: <Qualifiername>=<QualifierValue> ist ein Standardqualifizierer, und seine Kandidaten können nicht zu einem Ressourcenpaket hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="d4b35-183">Invalid Configuration: <Qualifiername>=<QualifierValue> is a default qualifier and its candidates cannot be added to a resource package.</span></span> |
| <span data-ttu-id="d4b35-184">Der Qualifizierer AutoResourcePackage enthält mehrere Qualifizierer.</span><span class="sxs-lookup"><span data-stu-id="d4b35-184">AutoResourcePackage qualifier contains multiple qualifiers.</span></span> <span data-ttu-id="d4b35-185">Beispiel: language_scale.</span><span class="sxs-lookup"><span data-stu-id="d4b35-185">For example, language_scale.</span></span> | <span data-ttu-id="d4b35-186">Fehler</span><span class="sxs-lookup"><span data-stu-id="d4b35-186">Error</span></span> | <span data-ttu-id="d4b35-187">Invalid Configuration: AutoResourcePackage with multiple qualifiers is not supported.</span><span class="sxs-lookup"><span data-stu-id="d4b35-187">Invalid Configuration : AutoResourcePackage with multiple qualifiers is not supported.</span></span> |
| <span data-ttu-id="d4b35-188">ResourcePackage QualifierSet enthält mehrere Qualifizierer.</span><span class="sxs-lookup"><span data-stu-id="d4b35-188">ResourcePackage QualifierSet contains multiple qualifiers.</span></span> <span data-ttu-id="d4b35-189">Beispiel: language-en-us_scale-100.</span><span class="sxs-lookup"><span data-stu-id="d4b35-189">For example, language-en-us_scale-100</span></span> | <span data-ttu-id="d4b35-190">Fehler</span><span class="sxs-lookup"><span data-stu-id="d4b35-190">Error</span></span> | <span data-ttu-id="d4b35-191">Invalid Configuration: QualifierSet with multiple qualifiers is not supported.</span><span class="sxs-lookup"><span data-stu-id="d4b35-191">Invalid Configuration : QualifierSet with multiple qualifiers is not supported.</span></span> |
| <span data-ttu-id="d4b35-192">Es wurde ein doppelter Ressourcenpaketname gefunden.</span><span class="sxs-lookup"><span data-stu-id="d4b35-192">Duplicate resourcepack name found.</span></span> | <span data-ttu-id="d4b35-193">Fehler</span><span class="sxs-lookup"><span data-stu-id="d4b35-193">Error</span></span> | <span data-ttu-id="d4b35-194">Ungültige Konfiguration: Doppelter Ressourcenpaketname <rpname>.</span><span class="sxs-lookup"><span data-stu-id="d4b35-194">Invalid Configuration : Duplicate resource pack name <rpname>.</span></span> |
| <span data-ttu-id="d4b35-195">In zwei Ressourcenpaketen wurde der gleiche Satz von Qualifizierern definiert.</span><span class="sxs-lookup"><span data-stu-id="d4b35-195">Same qualifier set defined in two resource packages.</span></span> | <span data-ttu-id="d4b35-196">Fehler</span><span class="sxs-lookup"><span data-stu-id="d4b35-196">Error</span></span> | <span data-ttu-id="d4b35-197">Ungültige Konfiguration: Es wurden mehrere QualifierSet-Instanzen von „<qualifier tags>” gefunden.</span><span class="sxs-lookup"><span data-stu-id="d4b35-197">Invalid Configuration: Multiple instances of QualifierSet "<qualifier tags>" found.</span></span> |
| <span data-ttu-id="d4b35-198">Für das für den Knoten "ResourcePackage" aufgelistete QualifierSet-Element wurden keine Kandidaten gefunden.</span><span class="sxs-lookup"><span data-stu-id="d4b35-198">No candidates are found for the QualifierSet listed for 'ResourcePackage' node.</span></span> | <span data-ttu-id="d4b35-199">Warnung</span><span class="sxs-lookup"><span data-stu-id="d4b35-199">Warning</span></span> | <span data-ttu-id="d4b35-200">Ungültige Konfiguration: Für <Resource Package Name> wurden keine Kandidaten gefunden.</span><span class="sxs-lookup"><span data-stu-id="d4b35-200">Invalid Configuration: No candidates found for <Resource Package Name>.</span></span> |
| <span data-ttu-id="d4b35-201">Für den unter dem Knoten "AutoResourcePackage" aufgeführten Qualifizierer wurden keine Kandidaten gefunden.</span><span class="sxs-lookup"><span data-stu-id="d4b35-201">No candidates found for qualifier listed under ‘AutoResourcePackage’ node.</span></span> | <span data-ttu-id="d4b35-202">Warnung</span><span class="sxs-lookup"><span data-stu-id="d4b35-202">Warning</span></span> | <span data-ttu-id="d4b35-203">Ungültige Konfiguration: Für den Qualifizierer <qualifier name> wurden keine Kandidaten gefunden.</span><span class="sxs-lookup"><span data-stu-id="d4b35-203">Invalid Configuration: No candidates found for qualifier <qualifier name>.</span></span> <span data-ttu-id="d4b35-204">Das Ressourcenpaket wurde nicht generiert</span><span class="sxs-lookup"><span data-stu-id="d4b35-204">Resource Package not generated.</span></span> |
| <span data-ttu-id="d4b35-205">Es wurde kein Modus gefunden.</span><span class="sxs-lookup"><span data-stu-id="d4b35-205">None of the modes are found.</span></span> <span data-ttu-id="d4b35-206">Es wurde also ein leerer Knoten "packaging" gefunden.</span><span class="sxs-lookup"><span data-stu-id="d4b35-206">That is, empty 'packaging' node found.</span></span> | <span data-ttu-id="d4b35-207">Warnung</span><span class="sxs-lookup"><span data-stu-id="d4b35-207">Warning</span></span> | <span data-ttu-id="d4b35-208">Ungültige Konfiguration: Kein Verpackungsmodus angegeben.</span><span class="sxs-lookup"><span data-stu-id="d4b35-208">Invalid Configuration: No packaging mode specified.</span></span> |

## <a name="related-topics"></a><span data-ttu-id="d4b35-209">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="d4b35-209">Related topics</span></span>

* [<span data-ttu-id="d4b35-210">Manuelles Kompilieren von Ressourcen mit MakePri.exe</span><span class="sxs-lookup"><span data-stu-id="d4b35-210">Compile resources manually with MakePri.exe</span></span>](compile-resources-manually-with-makepri.md)
* [<span data-ttu-id="d4b35-211">Befehlszeilenoptionen von MakePri.exe&mdash;createconfig-Befehl</span><span class="sxs-lookup"><span data-stu-id="d4b35-211">MakePri.exe command-line options&mdash;createconfig command</span></span>](makepri-exe-command-options.md#createconfig-command)
* [<span data-ttu-id="d4b35-212">Anpassen von Ressourcen mit Qualifizierern für Sprache, Skalierung, hohen Kontrast und anderen Qualifizierern</span><span class="sxs-lookup"><span data-stu-id="d4b35-212">Tailor your resources for language, scale, high contrast, and other qualifiers</span></span>](tailor-resources-lang-scale-contrast.md)
* [<span data-ttu-id="d4b35-213">Ressourcenverwaltungssystem&mdash;ResourceContext</span><span class="sxs-lookup"><span data-stu-id="d4b35-213">Resource Management System&mdash;ResourceContext</span></span>](resource-management-system.md#resourcecontext)