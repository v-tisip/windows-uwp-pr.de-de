---
author: stevewhims
Description: This topic describes the schema of the MakePri.exe XML configuration file.
title: Konfigurationsdatei für MakePri.exe
template: detail.hbs
ms.author: stwhi
ms.date: 10/18/2017
ms.topic: article
keywords: Windows10, UWP, Ressourcen, Bild, Element, MRT, Qualifizierer
ms.localizationpriority: medium
ms.openlocfilehash: 3becb43fb1f173926ce4873aa61368f095bef5d4
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2018
ms.locfileid: "7162582"
---
# <a name="makepriexe-configuration-file"></a>Konfigurationsdatei für MakePRI.exe

In diesem Thema wird das Schema der XML-Konfigurationsdatei (auch PRI-Konfigurationsdatei genannt) für [MakePri.exe](compile-resources-manually-with-makepri.md) beschrieben. Das Tool MakePri.exe verfügt über den Befehl [createconfig](makepri-exe-command-options.md#createconfig-command), der eine neue, initialisierte PRI-Konfigurationsdatei erstellt.

> [!NOTE]
> MakePri.exe wird installiert, wenn Sie im **Windows SDK für UWP-Apps verwaltet** Option während der Installation im Windows Software Development Kit aktivieren. Es installiert ist, um den Pfad `%WindowsSdkDir%bin\<WindowsTargetPlatformVersion>\x64\makepri.exe` (ebenso wie in den Ordnern für die anderen Architekturen). Beispiel: `C:\Program Files (x86)\Windows Kits\10\bin\10.0.17713.0\x64\makepri.exe`.

Die PRI-Konfigurationsdatei steuert, welche Ressourcen wie indiziert werden. Die XML-Konfigurationsdatei muss folgendem Schema entsprechen:

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

- Das Element `default` gibt den Kontext (Sprache, Skalierung, Kontrast usw.) an, der zur Auflösung der Ressourcen verwendet werden soll, wenn keine passenden Kandidaten als Ressourcen für den Laufzeitkontext vorhanden sind. Da dieser Kontext zur Erstellungszeit angegeben wird und sich nicht ändert, werden die Ressourcen für diesen Kontext aufgelöst, sobald Qualifizierer erstellt worden sind. Die passende Bewertung wird zur Erstellungszeit gespeichert. Für jeden Qualifizierer muss ein Wert angegeben werden. Weitere Informationen zur Ressourcenauswahl finden Sie unter [ResourceContext](resource-management-system.md#resourcecontext).
- Das Element `index` definiert separate Indizierungsdurchläufe, die für die Ressourcen durchgeführt werden. Jeder Indizierungsdurchlauf bestimmt die zu verwendenden [formatspezifischen Indexer](makepri-exe-format-specific-indexers.md) und die zu indizierenden Ressourcen.
- Das Element `qualifiers` legt die anfänglichen Qualifizierer für die erste Datei bzw. für den ersten Ordner fest, die andere Ressourcen erben. Jedes Qualifiziererelement muss einen gültigen Namen und einen gültigen Wert besitzen (siehe [Anpassen von Ressourcen mit Qualifizierern für Sprache, Skalierung, hohen Kontrast und andere Eigenschaften](tailor-resources-lang-scale-contrast.md)).
- Das Attribut `root` ist der Stamm des Dateipfads der physischen Datei für den Indizierungsdurchlauf. Er kann relativ oder absolut sein. Wenn er relativ ist, wird er an den Projektstamm angehängt, den Sie an der Befehlszeile angeben. Wenn er absolut ist, wird er direkt als Stamm für den Indizierungsdurchlauf verwendet. Es können sowohl Schrägstriche als auch umgekehrte Schrägstriche verwendet werden. Nachgestellte Leerzeichen werden entfernt. Der Stamm des Indizierungsdurchlaufs bestimmt den Ordner, zu dem alle Ressourcen als relativ betrachtet werden.
- Das `startIndexAt`-Attribut bezeichnet die Ausgangsdatei oder den Ausgangsordner, der bei der Indizierung verwendet wird. Es ist relativ zum Stamm des Indizierungsdurchlaufs. Bei einem leeren Wert wird vom Stammordner des Indizierungsdurchlaufs ausgegangen.

## <a name="default-pri-config-file"></a>Standard-PRI-Konfigurationsdatei

MakePri.exe generiert diese neue, initialisiert PRI-Konfigurationsdatei, wenn der Befehl [createconfig](makepri-exe-command-options.md#createconfig-command) aufgerufen wird.

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

## <a name="packaging-element"></a>Packaging-Element

Die Element `packaging` definiert PRI-Aufteilungsinformationen. Das Schema für das Element `packaging` kann sowohl für automatische Konfiguration (Unterstützung für `autoResourcePackage` für eine spezifische Dimension) als auch für manuelle Konfiguration definiert werden.

Dieses Beispiel zeigt die Verwendung von `autoResourcePackage` für eine spezifische Dimension:

```xml
    <packaging>
        <autoResourcePackage qualifier="Language"/>
        <autoResourcePackage qualifier="Scale"/>
        <autoResourcePackage qualifier="DXFeatureLevel"/>
    </packaging>
```

Dieses Beispiel zeigt die manuelle Anwendung von `resourcePackage`:

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

Die Erzeugung von PRI-Ressourcendateien für eine spezifische Dimension wird von MakePri.exe nicht explizit blockiert. Einschränkungen für eine bestimmte Gruppe von Dimensionen werden extern mithilfe von MakeAppx.exe oder anderen Tools der Pipeline definiert und implementiert.

MakePri.exe analysiert das Element `packaging` nach allen Knoten `index`-Knoten, um alle Standardqualifizierer aufzufüllen. MakePri.exe sammelt die gewonnenen Informationen in diesen Datenstrukturen:

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

## <a name="resourcesisdeploymentmergeable-attribute"></a>resources@isDeploymentMergeable-Attribut

Dieses Attribut setzt ein Flag in der PRI-Datei, das Folgendes bewirkt:

- Bereitstellungszusammenführung, um zu identifizieren, ob diese PRI-Datei für die Zusammenführung geeignet ist.
- Von GetFullyQualifiedReference wird ein Fehler zurückgegeben, falls dieses Kennzeichen festgelegt und der Ressourcen-Manager mit einer Datei initialisiert wurde.

Der Standardwert dieses Attributs ist `true`. MakePri.exe setzt das Flag in PRI nur im Zusammenhang mit Windows 10.

Wir empfehlen, das Flag `isDeploymentMergeable` bei der Erstellung von Ressourcenpaketen für Windows 10 nicht zu verwenden (oder es explizit auf `true` zu setzen).

MakePri.exe fügt den Wert von `isDeploymentMergeable` der Dumpdatei hinzu, wenn `makepri dump` mit der Option `/dt detailed` ausgeführt wird.

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

## <a name="resourcesmajorversion-attribute"></a>resources@majorVersion-Attribut

Der Standardwert für dieses Attribut ist 1. Wenn Sie einen expliziten Wert angeben und auch die veraltete Befehlszeilenoption `/VersionMajor(vma)` für das MakePri.exe-Tool verwenden, hat der Wert in der Konfigurationsdatei Vorrang.

Beispiel:

```xml
<resources majorVersion="2">
  <packaging ... />
  <index root="\" startIndexAt="\">
    ...
  </index>
</resources>
```

## <a name="resourcestargetosversion-attribute"></a>resources@targetOsVersion-Attribut

Gibt die Zielbetriebssystemversion an. Die folgenden Tabelle enthält die unterstützten Werte. Der Standardwert ist 6.3.0.

| Wert | Bedeutung |
| ----- | ------- |
| 10.0.0 | Windows 10 |
| 6.3.0 (Standard) | Windows 8.1 |
| 6.2.1 | Windows 8 |

Beispiel:

```xml
<resources targetOsVersion="10.0.0">
  <packaging ... />
  <index root="\" startIndexAt="\">
    ...
  </index>
</resources>
```

**Hinweis:** Windows ist in Bezug auf die PRI-Dateien abwärtskompatibel, aber nicht immer aufwärtskompatibel.

MakePri.exe fügt den Wert von `targetOsVersion` der Dumpdatei hinzu, wenn `makepri dump` mit der Option `/dt detailed` ausgeführt wird.

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

## <a name="validation-error-messages"></a>Fehlermeldungen bei der Überprüfung

Hier einige Beispiele für Fehlerbedingungen und die entsprechenden Fehlermeldungen:

| Bedingung | Schweregrad | Meldung |
| --------- | -------- | ------- |
| Für targetOsVersion ist keiner der unterstützten Werte angegeben. | Fehler | Ungültige Konfiguration: Die Angabe für targetOsVersion ist ungültig. |
| Für targetOsVersion wurde der Wert „6.2.1 ”angegeben, und es ist ein `packaging`-Element vorhanden. | Fehler | Ungültige Konfiguration: Knoten „Packaging” wird von dieser targetOsVersion nicht unterstützt. |
| In der Konfiguration wurde mehr als ein Modus gefunden. Beispielsweise wurde "Manual" und "AutoResourcePackage" angegeben. | Fehler | Ungültige Konfiguration: Knoten „Packaging” unterstützt nur einen Betriebsmodus. |
| Für das Ressourcenpaket ist ein Standardqualifizierer angegeben. | Fehler | Ungültige Konfiguration: <Qualifiername>=<QualifierValue> ist ein Standardqualifizierer, und seine Kandidaten können nicht zu einem Ressourcenpaket hinzugefügt werden. |
| Der Qualifizierer AutoResourcePackage enthält mehrere Qualifizierer. Beispiel: language_scale. | Fehler | Invalid Configuration: AutoResourcePackage with multiple qualifiers is not supported. |
| ResourcePackage QualifierSet enthält mehrere Qualifizierer. Beispiel: language-en-us_scale-100. | Fehler | Invalid Configuration: QualifierSet with multiple qualifiers is not supported. |
| Es wurde ein doppelter Ressourcenpaketname gefunden. | Fehler | Ungültige Konfiguration: Doppelter Ressourcenpaketname <rpname>. |
| In zwei Ressourcenpaketen wurde der gleiche Satz von Qualifizierern definiert. | Fehler | Ungültige Konfiguration: Es wurden mehrere QualifierSet-Instanzen von „<qualifier tags>” gefunden. |
| Für das für den Knoten "ResourcePackage" aufgelistete QualifierSet-Element wurden keine Kandidaten gefunden. | Warnung | Ungültige Konfiguration: Für <Resource Package Name> wurden keine Kandidaten gefunden. |
| Für den unter dem Knoten "AutoResourcePackage" aufgeführten Qualifizierer wurden keine Kandidaten gefunden. | Warnung | Ungültige Konfiguration: Für den Qualifizierer <qualifier name> wurden keine Kandidaten gefunden. Das Ressourcenpaket wurde nicht generiert |
| Es wurde kein Modus gefunden. Es wurde also ein leerer Knoten "packaging" gefunden. | Warnung | Ungültige Konfiguration: Kein Verpackungsmodus angegeben. |

## <a name="related-topics"></a>Verwandte Themen

* [Manuelles Kompilieren von Ressourcen mit MakePri.exe](compile-resources-manually-with-makepri.md)
* [Befehlszeilenoptionen von MakePri.exe&mdash;createconfig-Befehl](makepri-exe-command-options.md#createconfig-command)
* [Anpassen von Ressourcen mit Qualifizierern für Sprache, Skalierung, hohen Kontrast und anderen Qualifizierern](tailor-resources-lang-scale-contrast.md)
* [Ressourcenverwaltungssystem&mdash;ResourceContext](resource-management-system.md#resourcecontext)