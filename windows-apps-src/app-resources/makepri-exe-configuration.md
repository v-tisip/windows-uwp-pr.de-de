---
author: stevewhims
Description: This topic describes the schema of the MakePri.exe XML configuration file.
title: Konfigurationsdatei für MakePri.exe
template: detail.hbs
ms.author: stwhi
ms.date: 10/18/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Ressourcen, Bild, Element, MRT, Qualifizierer
ms.localizationpriority: medium
ms.openlocfilehash: 24ba76549053ef0f88612249eb903278d8554167
ms.sourcegitcommit: f9a4854b6aecfda472fb3f8b4a2d3b271b327800
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2017
ms.locfileid: "1393519"
---
# <a name="makepriexe-configuration-file"></a><span data-ttu-id="ed684-103">Konfigurationsdatei für MakePRI.exe</span><span class="sxs-lookup"><span data-stu-id="ed684-103">MakePri.exe configuration file</span></span>

<span data-ttu-id="ed684-104">In diesem Thema wird das Schema der XML-Konfigurationsdatei (auch PRI-Konfigurationsdatei genannt) für [MakePri.exe](compile-resources-manually-with-makepri.md) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="ed684-104">This topic describes the schema of the [MakePri.exe](compile-resources-manually-with-makepri.md) XML configuration file; also known as a PRI config file.</span></span> <span data-ttu-id="ed684-105">Das Tool MakePri.exe verfügt über den Befehl [createconfig](makepri-exe-command-options.md#createconfig-command), der eine neue, initialisierte PRI-Konfigurationsdatei erstellt.</span><span class="sxs-lookup"><span data-stu-id="ed684-105">The MakePri.exe tool has a [createconfig command](makepri-exe-command-options.md#createconfig-command) that you can use to create a new, initialized PRI config file.</span></span>

<span data-ttu-id="ed684-106">Die PRI-Konfigurationsdatei steuert, welche Ressourcen wie indiziert werden.</span><span class="sxs-lookup"><span data-stu-id="ed684-106">The PRI config file controls what resources are indexed, and how.</span></span> <span data-ttu-id="ed684-107">Die XML-Konfigurationsdatei muss folgendem Schema entsprechen:</span><span class="sxs-lookup"><span data-stu-id="ed684-107">The configuration XML must conform to the following schema.</span></span>

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

- <span data-ttu-id="ed684-108">Das Element `default` gibt den Kontext (Sprache, Skalierung, Kontrast usw.) an, der zur Auflösung der Ressourcen verwendet werden soll, wenn keine passenden Kandidaten als Ressourcen für den Laufzeitkontext vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="ed684-108">The `default` element specifies the context (language, scale, contrast, etc.) that should be used to resolve resources when the runtime context does not match any resource candidates.</span></span> <span data-ttu-id="ed684-109">Da dieser Kontext zur Erstellungszeit angegeben wird und sich nicht ändert, werden die Ressourcen für diesen Kontext aufgelöst, sobald Qualifizierer erstellt worden sind.</span><span class="sxs-lookup"><span data-stu-id="ed684-109">Because this context is specified at build time and does not change, resources are resolved to this context as qualifiers are created.</span></span> <span data-ttu-id="ed684-110">Die passende Bewertung wird zur Erstellungszeit gespeichert.</span><span class="sxs-lookup"><span data-stu-id="ed684-110">The matched score is stored at build time.</span></span> <span data-ttu-id="ed684-111">Für jeden Qualifizierer muss ein Wert angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="ed684-111">Every qualifier must have some value specified.</span></span> <span data-ttu-id="ed684-112">Weitere Informationen zur Ressourcenauswahl finden Sie unter [ResourceContext](resource-management-system.md#resourcecontext).</span><span class="sxs-lookup"><span data-stu-id="ed684-112">See [ResourceContext](resource-management-system.md#resourcecontext) for details on how resources are chosen.</span></span>
- <span data-ttu-id="ed684-113">Das Element `index` definiert separate Indizierungsdurchläufe, die für die Ressourcen durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="ed684-113">The `index` element defines discrete indexing passes that are done over the assets.</span></span> <span data-ttu-id="ed684-114">Jeder Indizierungsdurchlauf bestimmt die zu verwendenden [formatspezifischen Indexer](makepri-exe-format-specific-indexers.md) und die zu indizierenden Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="ed684-114">Each indexing pass determines the [format-specific indexers](makepri-exe-format-specific-indexers.md) to use, and which resources to index.</span></span>
- <span data-ttu-id="ed684-115">Das Element `qualifiers` legt die anfänglichen Qualifizierer für die erste Datei bzw. für den ersten Ordner fest, die andere Ressourcen erben.</span><span class="sxs-lookup"><span data-stu-id="ed684-115">The `qualifiers` element sets the initial qualifiers for the first file or folder that other resources inherit.</span></span> <span data-ttu-id="ed684-116">Jedes Qualifiziererelement muss einen gültigen Namen und einen gültigen Wert besitzen (siehe [Anpassen von Ressourcen mit Qualifizierern für Sprache, Skalierung, hohen Kontrast und andere Eigenschaften](tailor-resources-lang-scale-contrast.md)).</span><span class="sxs-lookup"><span data-stu-id="ed684-116">Each qualifier element must have a valid name and value (see [Tailor your resources for language, scale, high contrast, and other qualifiers](tailor-resources-lang-scale-contrast.md)).</span></span>
- <span data-ttu-id="ed684-117">Das Attribut `root` ist der Stamm des Dateipfads der physischen Datei für den Indizierungsdurchlauf.</span><span class="sxs-lookup"><span data-stu-id="ed684-117">The `root` attribute is the path root of the physical file for the index pass.</span></span> <span data-ttu-id="ed684-118">Er kann relativ oder absolut sein.</span><span class="sxs-lookup"><span data-stu-id="ed684-118">It can be relative or absolute.</span></span> <span data-ttu-id="ed684-119">Wenn er relativ ist, wird er an den Projektstamm angehängt, den Sie an der Befehlszeile angeben.</span><span class="sxs-lookup"><span data-stu-id="ed684-119">If relative, it is appended to the project root that you provide in the command line.</span></span> <span data-ttu-id="ed684-120">Wenn er absolut ist, wird er direkt als Stamm für den Indizierungsdurchlauf verwendet.</span><span class="sxs-lookup"><span data-stu-id="ed684-120">If absolute, it is directly used as the index pass root.</span></span> <span data-ttu-id="ed684-121">Es können sowohl Schrägstriche als auch umgekehrte Schrägstriche verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ed684-121">Back or forward slashes are acceptable.</span></span> <span data-ttu-id="ed684-122">Nachgestellte Leerzeichen werden entfernt.</span><span class="sxs-lookup"><span data-stu-id="ed684-122">Trailing slashes are trimmed.</span></span> <span data-ttu-id="ed684-123">Der Stamm des Indizierungsdurchlaufs bestimmt den Ordner, zu dem alle Ressourcen als relativ betrachtet werden.</span><span class="sxs-lookup"><span data-stu-id="ed684-123">The root of the index pass determines the folder to which all resources are considered relative.</span></span>
- <span data-ttu-id="ed684-124">Das `startIndexAt`-Attribut bezeichnet die Ausgangsdatei oder den Ausgangsordner, der bei der Indizierung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ed684-124">The `startIndexAt` attribute is the initial seed file or folder used in indexing.</span></span> <span data-ttu-id="ed684-125">Es ist relativ zum Stamm des Indizierungsdurchlaufs.</span><span class="sxs-lookup"><span data-stu-id="ed684-125">It is relative to the index pass root.</span></span> <span data-ttu-id="ed684-126">Bei einem leeren Wert wird vom Stammordner des Indizierungsdurchlaufs ausgegangen.</span><span class="sxs-lookup"><span data-stu-id="ed684-126">An empty value assumes the index pass root folder.</span></span>

## <a name="default-pri-config-file"></a><span data-ttu-id="ed684-127">Standard-PRI-Konfigurationsdatei</span><span class="sxs-lookup"><span data-stu-id="ed684-127">Default PRI config file</span></span>

<span data-ttu-id="ed684-128">MakePri.exe generiert diese neue, initialisiert PRI-Konfigurationsdatei, wenn der Befehl [createconfig](makepri-exe-command-options.md#createconfig-command) aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="ed684-128">MakePri.exe generates this new, initialized PRI config file when the [createconfig command](makepri-exe-command-options.md#createconfig-command) is issued.</span></span>

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

## <a name="packaging-element"></a><span data-ttu-id="ed684-129">Packaging-Element</span><span class="sxs-lookup"><span data-stu-id="ed684-129">Packaging element</span></span>

<span data-ttu-id="ed684-130">Die Element `packaging` definiert PRI-Aufteilungsinformationen.</span><span class="sxs-lookup"><span data-stu-id="ed684-130">The `packaging` element defines PRI split information.</span></span> <span data-ttu-id="ed684-131">Das Schema für das Element `packaging` kann sowohl für automatische Konfiguration (Unterstützung für `autoResourcePackage` für eine spezifische Dimension) als auch für manuelle Konfiguration definiert werden.</span><span class="sxs-lookup"><span data-stu-id="ed684-131">The schema for the `packaging` element is defined for both automatic (support for `autoResourcePackage` along a specific dimension), and manual configuration.</span></span>

<span data-ttu-id="ed684-132">Dieses Beispiel zeigt die Verwendung von `autoResourcePackage` für eine spezifische Dimension:</span><span class="sxs-lookup"><span data-stu-id="ed684-132">This example shows how to use `autoResourcePackage` along a specific dimension.</span></span>

```xml
    <packaging>
        <autoResourcePackage qualifier="Language"/>
        <autoResourcePackage qualifier="Scale"/>
        <autoResourcePackage qualifier="DXFeatureLevel"/>
    </packaging>
```

<span data-ttu-id="ed684-133">Dieses Beispiel zeigt die manuelle Anwendung von `resourcePackage`:</span><span class="sxs-lookup"><span data-stu-id="ed684-133">This example shows how to use manual `resourcePackage`.</span></span>

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

<span data-ttu-id="ed684-134">Die Erzeugung von PRI-Ressourcendateien für eine spezifische Dimension wird von MakePri.exe nicht explizit blockiert.</span><span class="sxs-lookup"><span data-stu-id="ed684-134">MakePri.exe doesn't explicitly block generation of resource PRI files along any specific dimension.</span></span> <span data-ttu-id="ed684-135">Einschränkungen für eine bestimmte Gruppe von Dimensionen werden extern mithilfe von MakeAppx.exe oder anderen Tools der Pipeline definiert und implementiert.</span><span class="sxs-lookup"><span data-stu-id="ed684-135">Restrictions along a certain set of dimensions are defined and implemented externally by either MakeAppx.exe or other tools in the pipeline.</span></span>

<span data-ttu-id="ed684-136">MakePri.exe analysiert das Element `packaging` nach allen Knoten `index`-Knoten, um alle Standardqualifizierer aufzufüllen.</span><span class="sxs-lookup"><span data-stu-id="ed684-136">MakePri.exe parses the `packaging` element after all the `index` nodes to populate all the default qualifiers.</span></span> <span data-ttu-id="ed684-137">MakePri.exe sammelt die gewonnenen Informationen in diesen Datenstrukturen:</span><span class="sxs-lookup"><span data-stu-id="ed684-137">MakePri.exe collects parsed info in these data structures.</span></span>

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

## <a name="resourcesisdeploymentmergeable-attribute"></a><span data-ttu-id="ed684-138">resources@isDeploymentMergeable-Attribut</span><span class="sxs-lookup"><span data-stu-id="ed684-138">resources@isDeploymentMergeable attribute</span></span>

<span data-ttu-id="ed684-139">Dieses Attribut setzt ein Flag in der PRI-Datei, das Folgendes bewirkt:</span><span class="sxs-lookup"><span data-stu-id="ed684-139">This attribute sets a flag in the PRI file that causes</span></span>

- <span data-ttu-id="ed684-140">Bereitstellungszusammenführung, um zu identifizieren, ob diese PRI-Datei für die Zusammenführung geeignet ist.</span><span class="sxs-lookup"><span data-stu-id="ed684-140">Deployment merge to identify that this PRI file can merge.</span></span>
- <span data-ttu-id="ed684-141">Von GetFullyQualifiedReference wird ein Fehler zurückgegeben, falls dieses Kennzeichen festgelegt und der Ressourcen-Manager mit einer Datei initialisiert wurde.</span><span class="sxs-lookup"><span data-stu-id="ed684-141">GetFullyQualifiedReference to return an error in case this flag is set and the resource manager has been initialized with a file.</span></span>

<span data-ttu-id="ed684-142">Der Standardwert dieses Attributs ist `true`.</span><span class="sxs-lookup"><span data-stu-id="ed684-142">The default value of this attribute is `true`.</span></span> <span data-ttu-id="ed684-143">MakePri.exe setzt das Flag in PRI nur im Zusammenhang mit Windows 10.</span><span class="sxs-lookup"><span data-stu-id="ed684-143">MakePri.exe only sets the flag in PRI if you target Windows 10.</span></span>

<span data-ttu-id="ed684-144">Wir empfehlen, das Flag `isDeploymentMergeable` bei der Erstellung von Ressourcenpaketen für Windows 10 nicht zu verwenden (oder es explizit auf `true` zu setzen).</span><span class="sxs-lookup"><span data-stu-id="ed684-144">We recommend that you omit `isDeploymentMergeable` (or set it explicitly to `true`) for resource pack creation if you target Windows 10.</span></span>

<span data-ttu-id="ed684-145">MakePri.exe fügt den Wert von `isDeploymentMergeable` der Dumpdatei hinzu, wenn `makepri dump` mit der Option `/dt detailed` ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="ed684-145">MakePri.exe adds the value of `isDeploymentMergeable` to the dump file if `makepri dump` is run with the `/dt detailed` option.</span></span>

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

## <a name="resourcesmajorversion-attribute"></a><span data-ttu-id="ed684-146">resources@majorVersion-Attribut</span><span class="sxs-lookup"><span data-stu-id="ed684-146">resources@majorVersion attribute</span></span>

<span data-ttu-id="ed684-147">Der Standardwert für dieses Attribut ist 1.</span><span class="sxs-lookup"><span data-stu-id="ed684-147">The default value for this attribute is 1.</span></span> <span data-ttu-id="ed684-148">Wenn Sie einen expliziten Wert angeben und auch die veraltete Befehlszeilenoption `/VersionMajor(vma)` für das MakePri.exe-Tool verwenden, hat der Wert in der Konfigurationsdatei Vorrang.</span><span class="sxs-lookup"><span data-stu-id="ed684-148">If you provide an explicit value, and you also use the deprecated `/VersionMajor(vma)` command-line option for the MakePri.exe tool, then the value in the config file takes precedence.</span></span>

<span data-ttu-id="ed684-149">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="ed684-149">Here's an example.</span></span>

```xml
<resources majorVersion="2">
  <packaging ... />
  <index root="\" startIndexAt="\">
    ...
  </index>
</resources>
```

## <a name="resourcestargetosversion-attribute"></a><span data-ttu-id="ed684-150">resources@targetOsVersion-Attribut</span><span class="sxs-lookup"><span data-stu-id="ed684-150">resources@targetOsVersion attribute</span></span>

<span data-ttu-id="ed684-151">Gibt die Zielbetriebssystemversion an.</span><span class="sxs-lookup"><span data-stu-id="ed684-151">Indicates the target operating system version.</span></span> <span data-ttu-id="ed684-152">Die folgenden Tabelle enthält die unterstützten Werte. Der Standardwert ist 6.3.0.</span><span class="sxs-lookup"><span data-stu-id="ed684-152">The table below shows the values that are supported; the default value is 6.3.0.</span></span>

| <span data-ttu-id="ed684-153">Wert</span><span class="sxs-lookup"><span data-stu-id="ed684-153">Value</span></span> | <span data-ttu-id="ed684-154">Bedeutung</span><span class="sxs-lookup"><span data-stu-id="ed684-154">Meaning</span></span> |
| ----- | ------- |
| <span data-ttu-id="ed684-155">10.0.0</span><span class="sxs-lookup"><span data-stu-id="ed684-155">10.0.0</span></span> | <span data-ttu-id="ed684-156">Windows 10</span><span class="sxs-lookup"><span data-stu-id="ed684-156">Windows 10</span></span> |
| <span data-ttu-id="ed684-157">6.3.0 (Standard)</span><span class="sxs-lookup"><span data-stu-id="ed684-157">6.3.0 (default)</span></span> | <span data-ttu-id="ed684-158">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="ed684-158">Windows 8.1</span></span> |
| <span data-ttu-id="ed684-159">6.2.1</span><span class="sxs-lookup"><span data-stu-id="ed684-159">6.2.1</span></span> | <span data-ttu-id="ed684-160">Windows 8</span><span class="sxs-lookup"><span data-stu-id="ed684-160">Windows 8</span></span> |

<span data-ttu-id="ed684-161">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="ed684-161">Here's an example.</span></span>

```xml
<resources targetOsVersion="10.0.0">
  <packaging ... />
  <index root="\" startIndexAt="\">
    ...
  </index>
</resources>
```

<span data-ttu-id="ed684-162">**Hinweis:** Windows ist in Bezug auf die PRI-Dateien abwärtskompatibel, aber nicht immer aufwärtskompatibel.</span><span class="sxs-lookup"><span data-stu-id="ed684-162">**Note** Windows is backward compatible with respect to PRI files; but not always forward compatible.</span></span>

<span data-ttu-id="ed684-163">MakePri.exe fügt den Wert von `targetOsVersion` der Dumpdatei hinzu, wenn `makepri dump` mit der Option `/dt detailed` ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="ed684-163">MakePri.exe adds the value of `targetOsVersion` to the dump file if `makepri dump` is run with the `/dt detailed` option.</span></span>

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

## <a name="validation-error-messages"></a><span data-ttu-id="ed684-164">Fehlermeldungen bei der Überprüfung</span><span class="sxs-lookup"><span data-stu-id="ed684-164">Validation error messages</span></span>

<span data-ttu-id="ed684-165">Hier einige Beispiele für Fehlerbedingungen und die entsprechenden Fehlermeldungen:</span><span class="sxs-lookup"><span data-stu-id="ed684-165">Here are some example error conditions, and the corresponding error message.</span></span>

| <span data-ttu-id="ed684-166">Bedingung</span><span class="sxs-lookup"><span data-stu-id="ed684-166">Condition</span></span> | <span data-ttu-id="ed684-167">Schweregrad</span><span class="sxs-lookup"><span data-stu-id="ed684-167">Severity</span></span> | <span data-ttu-id="ed684-168">Meldung</span><span class="sxs-lookup"><span data-stu-id="ed684-168">Message</span></span> |
| --------- | -------- | ------- |
| <span data-ttu-id="ed684-169">Für targetOsVersion ist keiner der unterstützten Werte angegeben.</span><span class="sxs-lookup"><span data-stu-id="ed684-169">A targetOsVersion other than one of the supported values is specified.</span></span> | <span data-ttu-id="ed684-170">Fehler</span><span class="sxs-lookup"><span data-stu-id="ed684-170">Error</span></span> | <span data-ttu-id="ed684-171">Ungültige Konfiguration: Die Angabe für targetOsVersion ist ungültig.</span><span class="sxs-lookup"><span data-stu-id="ed684-171">Invalid Configuration: Invalid targetOsVersion specified.</span></span> |
| <span data-ttu-id="ed684-172">Für targetOsVersion wurde der Wert „6.2.1 ”angegeben, und es ist ein `packaging`-Element vorhanden.</span><span class="sxs-lookup"><span data-stu-id="ed684-172">A targetOsVersion of "6.2.1" is specified and a `packaging` element is present.</span></span> | <span data-ttu-id="ed684-173">Fehler</span><span class="sxs-lookup"><span data-stu-id="ed684-173">Error</span></span> | <span data-ttu-id="ed684-174">Ungültige Konfiguration: Knoten „Packaging” wird von dieser targetOsVersion nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ed684-174">Invalid Configuration: 'Packaging' node is not supported with this targetOsVersion.</span></span> |
| <span data-ttu-id="ed684-175">In der Konfiguration wurde mehr als ein Modus gefunden.</span><span class="sxs-lookup"><span data-stu-id="ed684-175">More than one mode found in the configuration.</span></span> <span data-ttu-id="ed684-176">Beispielsweise wurde "Manual" und "AutoResourcePackage" angegeben.</span><span class="sxs-lookup"><span data-stu-id="ed684-176">For example, Manual and AutoResourcePackage specified.</span></span> | <span data-ttu-id="ed684-177">Fehler</span><span class="sxs-lookup"><span data-stu-id="ed684-177">Error</span></span> | <span data-ttu-id="ed684-178">Ungültige Konfiguration: Knoten „Packaging” unterstützt nur einen Betriebsmodus.</span><span class="sxs-lookup"><span data-stu-id="ed684-178">Invalid Configuration: 'packaging' node cannot have more than one mode of operation.</span></span> |
| <span data-ttu-id="ed684-179">Für das Ressourcenpaket ist ein Standardqualifizierer angegeben.</span><span class="sxs-lookup"><span data-stu-id="ed684-179">A default qualifier is listed under resource package.</span></span> | <span data-ttu-id="ed684-180">Fehler</span><span class="sxs-lookup"><span data-stu-id="ed684-180">Error</span></span> | <span data-ttu-id="ed684-181">Ungültige Konfiguration: <Qualifiername>=<QualifierValue> ist ein Standardqualifizierer, und seine Kandidaten können nicht zu einem Ressourcenpaket hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="ed684-181">Invalid Configuration: <Qualifiername>=<QualifierValue> is a default qualifier and its candidates cannot be added to a resource package.</span></span> |
| <span data-ttu-id="ed684-182">Der Qualifizierer AutoResourcePackage enthält mehrere Qualifizierer.</span><span class="sxs-lookup"><span data-stu-id="ed684-182">AutoResourcePackage qualifier contains multiple qualifiers.</span></span> <span data-ttu-id="ed684-183">Beispiel: language_scale.</span><span class="sxs-lookup"><span data-stu-id="ed684-183">For example, language_scale.</span></span> | <span data-ttu-id="ed684-184">Fehler</span><span class="sxs-lookup"><span data-stu-id="ed684-184">Error</span></span> | <span data-ttu-id="ed684-185">Invalid Configuration: AutoResourcePackage with multiple qualifiers is not supported.</span><span class="sxs-lookup"><span data-stu-id="ed684-185">Invalid Configuration : AutoResourcePackage with multiple qualifiers is not supported.</span></span> |
| <span data-ttu-id="ed684-186">ResourcePackage QualifierSet enthält mehrere Qualifizierer.</span><span class="sxs-lookup"><span data-stu-id="ed684-186">ResourcePackage QualifierSet contains multiple qualifiers.</span></span> <span data-ttu-id="ed684-187">Beispiel: language-en-us_scale-100.</span><span class="sxs-lookup"><span data-stu-id="ed684-187">For example, language-en-us_scale-100</span></span> | <span data-ttu-id="ed684-188">Fehler</span><span class="sxs-lookup"><span data-stu-id="ed684-188">Error</span></span> | <span data-ttu-id="ed684-189">Invalid Configuration: QualifierSet with multiple qualifiers is not supported.</span><span class="sxs-lookup"><span data-stu-id="ed684-189">Invalid Configuration : QualifierSet with multiple qualifiers is not supported.</span></span> |
| <span data-ttu-id="ed684-190">Es wurde ein doppelter Ressourcenpaketname gefunden.</span><span class="sxs-lookup"><span data-stu-id="ed684-190">Duplicate resourcepack name found.</span></span> | <span data-ttu-id="ed684-191">Fehler</span><span class="sxs-lookup"><span data-stu-id="ed684-191">Error</span></span> | <span data-ttu-id="ed684-192">Ungültige Konfiguration: Doppelter Ressourcenpaketname <rpname>.</span><span class="sxs-lookup"><span data-stu-id="ed684-192">Invalid Configuration : Duplicate resource pack name <rpname>.</span></span> |
| <span data-ttu-id="ed684-193">In zwei Ressourcenpaketen wurde der gleiche Satz von Qualifizierern definiert.</span><span class="sxs-lookup"><span data-stu-id="ed684-193">Same qualifier set defined in two resource packages.</span></span> | <span data-ttu-id="ed684-194">Fehler</span><span class="sxs-lookup"><span data-stu-id="ed684-194">Error</span></span> | <span data-ttu-id="ed684-195">Ungültige Konfiguration: Es wurden mehrere QualifierSet-Instanzen von „<qualifier tags>” gefunden.</span><span class="sxs-lookup"><span data-stu-id="ed684-195">Invalid Configuration: Multiple instances of QualifierSet "<qualifier tags>" found.</span></span> |
| <span data-ttu-id="ed684-196">Für das für den Knoten "ResourcePackage" aufgelistete QualifierSet-Element wurden keine Kandidaten gefunden.</span><span class="sxs-lookup"><span data-stu-id="ed684-196">No candidates are found for the QualifierSet listed for 'ResourcePackage' node.</span></span> | <span data-ttu-id="ed684-197">Warnung</span><span class="sxs-lookup"><span data-stu-id="ed684-197">Warning</span></span> | <span data-ttu-id="ed684-198">Ungültige Konfiguration: Für <Resource Package Name> wurden keine Kandidaten gefunden.</span><span class="sxs-lookup"><span data-stu-id="ed684-198">Invalid Configuration: No candidates found for <Resource Package Name>.</span></span> |
| <span data-ttu-id="ed684-199">Für den unter dem Knoten "AutoResourcePackage" aufgeführten Qualifizierer wurden keine Kandidaten gefunden.</span><span class="sxs-lookup"><span data-stu-id="ed684-199">No candidates found for qualifier listed under ‘AutoResourcePackage’ node.</span></span> | <span data-ttu-id="ed684-200">Warnung</span><span class="sxs-lookup"><span data-stu-id="ed684-200">Warning</span></span> | <span data-ttu-id="ed684-201">Ungültige Konfiguration: Für den Qualifizierer <qualifier name> wurden keine Kandidaten gefunden.</span><span class="sxs-lookup"><span data-stu-id="ed684-201">Invalid Configuration: No candidates found for qualifier <qualifier name>.</span></span> <span data-ttu-id="ed684-202">Das Ressourcenpaket wurde nicht generiert</span><span class="sxs-lookup"><span data-stu-id="ed684-202">Resource Package not generated.</span></span> |
| <span data-ttu-id="ed684-203">Es wurde kein Modus gefunden.</span><span class="sxs-lookup"><span data-stu-id="ed684-203">None of the modes are found.</span></span> <span data-ttu-id="ed684-204">Es wurde also ein leerer Knoten "packaging" gefunden.</span><span class="sxs-lookup"><span data-stu-id="ed684-204">That is, empty 'packaging' node found.</span></span> | <span data-ttu-id="ed684-205">Warnung</span><span class="sxs-lookup"><span data-stu-id="ed684-205">Warning</span></span> | <span data-ttu-id="ed684-206">Ungültige Konfiguration: Kein Verpackungsmodus angegeben.</span><span class="sxs-lookup"><span data-stu-id="ed684-206">Invalid Configuration: No packaging mode specified.</span></span> |

## <a name="related-topics"></a><span data-ttu-id="ed684-207">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="ed684-207">Related topics</span></span>

* [<span data-ttu-id="ed684-208">Manuelles Kompilieren von Ressourcen mit MakePri.exe</span><span class="sxs-lookup"><span data-stu-id="ed684-208">Compile resources manually with MakePri.exe</span></span>](compile-resources-manually-with-makepri.md)
* [<span data-ttu-id="ed684-209">Befehlszeilenoptionen von MakePri.exe&mdash;createconfig-Befehl</span><span class="sxs-lookup"><span data-stu-id="ed684-209">MakePri.exe command-line options&mdash;createconfig command</span></span>](makepri-exe-command-options.md#createconfig-command)
* [<span data-ttu-id="ed684-210">Anpassen von Ressourcen mit Qualifizierern für Sprache, Skalierung, hohen Kontrast und anderen Qualifizierern</span><span class="sxs-lookup"><span data-stu-id="ed684-210">Tailor your resources for language, scale, high contrast, and other qualifiers</span></span>](tailor-resources-lang-scale-contrast.md)
* [<span data-ttu-id="ed684-211">Ressourcenverwaltungssystem&mdash;ResourceContext</span><span class="sxs-lookup"><span data-stu-id="ed684-211">Resource Management System&mdash;ResourceContext</span></span>](resource-management-system.md#resourcecontext)