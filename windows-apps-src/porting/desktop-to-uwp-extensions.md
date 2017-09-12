---
author: normesta
Description: "Sie können Erweiterungen verwenden, um Ihre verpackte Desktop-App in Windows10 auf vordefinierter Weise zu integrieren."
Search.Product: eADQiWindows 10XVcnh
title: "Integrieren Sie Ihre App in Windows10 (Desktop-Brücke)"
ms.author: normesta
ms.date: 05/25/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.assetid: 0a8cedac-172a-4efd-8b6b-67fd3667df34
ms.openlocfilehash: 0c3427a7b49b17fda9a3ba0680e59b134732e9fa
ms.sourcegitcommit: 38ef208ef457ce1857038c9cde3658c884d29b75
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/13/2017
---
# <a name="integrate-your-app-with-windows-10-desktop-bridge"></a>Integrieren Sie Ihre App in Windows10 (Desktop-Brücke)

Verwenden Sie Erweiterungen, um Ihre App in Windows10 auf vordefinierter Weise zu integrieren.

Verwenden Sie z.B. eine Erweiterung, um eine Firewallausnahme festzulegen, machen Sie Ihre App die Standard-App für einen Dateityp oder verweisen Sie mit Startkacheln auf die verpackte Version Ihrer App. Um eine Erweiterung zu verwenden, fügen Sie einfach XML-Codes zur Paketmanifestdatei Ihrer App hinzu. Es ist kein Code erforderlich.

In diesem Thema werden diese Erweiterungen und die Aufgaben beschrieben, die Sie anhand dieser Erweiterungen ausführen können.

## <a name="transition-users-to-your-app"></a>Den Übergang Ihrer Benutzer auf Ihre App bereitstellen

Helfen Sie Ihren Benutzern, auf Ihre verpackte App umzustellen.

* [Verweisen Sie mit vorhandenen Startkacheln Taskleistenschaltflächen auf die verpackte App.](#point)
* [Stellen Sie ein, dass die verpackte App und nicht Ihre Desktop-App Dateien öffnet.](#make)
* [Ihre verpackte App einer Gruppe von Dateitypen zuordnen.](#associate)
* [Fügen Sie den Kontextmenüs der Dateien, die einen bestimmten Dateityp haben, Optionen hinzu.](#add)
* [Öffnen Sie bestimmte Dateitypen direkt anhand einer URL](#open)

<span id="point" />
### <a name="point-existing-start-tiles-and-taskbar-buttons-to-your-packaged-app"></a>Verweisen Sie mit vorhandenen Startkacheln Taskleistenschaltflächen auf die verpackte App.

Ihre Benutzer haben möglicherweise Ihre Desktop-Anwendung an die Taskleiste oder das Startmenü angeheftet. Sie mit diesen Verknüpfungen auf Ihre neu verpackte App verweisen.

#### <a name="xml-namespace"></a>XML-Namespace

http://schemas.microsoft.com/appx/Manifest/foundation/windows10/restrictedcapabilities/3

#### <a name="elements-and-attributes-of-this-extension"></a>Elemente und Attribute dieser Erweiterung

```XML
<Extension Category="windows.desktopAppMigration">
    <DesktopAppMigration>
        <DesktopApp AumId="[your_app_aumid]" />
        <DesktopApp ShortcutPath="[path]" />
    </DesktopAppMigration>
</Extension>

```

Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-rescap3-desktopappmigration).

|Name | Beschreibung |
|-------|-------------|
|Category |Immer ``windows.desktopAppMigration``.
|AumID |Die Anwendungsbenutzermodell-ID der verpackten App. |
|Verknüpfungspfad |Der Pfad zu den Ink-Dateien, die die Desktop-Version Ihrer App starten. |

#### <a name="example"></a>Beispiel

```XML
<Package
  xmlns:rescap3="http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities/3"
  IgnorableNamespaces="rescap3">
  <Applications>
    <Application>
      <Extensions>
        <rescap3:Extension Category="windows.desktopAppMigration">
          <rescap3:DesktopAppMigration>
            <rescap3:DesktopApp AumId="[your_app_aumid]" />
            <rescap3:DesktopApp ShortcutPath="%USERPROFILE%\Desktop\[my_app].lnk" />
            <rescap3:DesktopApp ShortcutPath="%APPDATA%\Microsoft\Windows\Start Menu\Programs\[my_app].lnk" />
            <rescap3:DesktopApp ShortcutPath="%PROGRAMDATA%\Microsoft\Windows\Start Menu\Programs\[my_app_folder]\[my_app].lnk"/>
         </rescap3:DesktopAppMigration>
        </rescap3:Extension>
      </Extensions>
    </Application>
  </Applications>
</Package>
```
#### <a name="related-sample"></a>Verwandte Beispiele

[WPF-Bildanzeige mit Übergang/Migration/Deinstallation](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/DesktopAppTransition)

<span id="make" />
### <a name="make-your-packaged-app-open-files-instead-of-your-desktop-app"></a>Stellen Sie ein, dass die verpackte App und nicht Ihre Desktop-App Dateien öffnet.

Sie können sicherstellen, dass Benutzer standardmäßig Ihre neu verpackte Version statt die Desktop-Version Ihrer App für bestimmte Dateitypen öffnen.

Dazu müssen Sie den [programmgesteuerten Bezeichner (Programm-ID)](https://msdn.microsoft.com/library/windows/desktop/cc144152.aspx) jeder Anwendung angeben, aus der Sie Dateizuordnungen übernehmen möchten.

#### <a name="xml-namespaces"></a>XML-Namespaces

* http://schemas.microsoft.com/appx/Manifest/uap/windows10/3
* http://schemas.microsoft.com/appx/Manifest/foundation/windows10/restrictedcapabilities/3

#### <a name="elements-and-attributes-of-this-extension"></a>Elemente und Attribute dieser Erweiterung

```XML
<Extension Category="windows.fileTypeAssociation">
<FileTypeAssociation Name="[AppID]">
         <MigrationProgIds>
            <MigrationProgId>"[ProgID]"</MigrationProgId>
        </MigrationProgIds>
    </FileTypeAssociation>
</Extension>
```

Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).

|Name |Beschreibung |
|-------|-------------|
|Kategorie |Immer ``windows.fileTypeAssociation``.
|Name |Eine eindeutige ID für Ihre App. Diese ID wird intern verwendet, um einen [programmgesteuerte Bezeichner (Programm-ID)](https://msdn.microsoft.com/library/windows/desktop/cc144152.aspx) mit Hash zu generieren, die mit Ihrer Dateitypzuordnung verknüpft ist. Mithilfe dieser ID können Sie Änderungen in zukünftigen Versionen Ihrer App verwalten. |
|MigrationProgId |Der [programmgesteuerte Bezeichner (Programm-ID)](https://msdn.microsoft.com/library/windows/desktop/cc144152.aspx), der die Anwendung, die Komponente und die Version der Desktop-App beschreibt, aus der die Dateizuordnungen übernommen werden sollen.|

#### <a name="example"></a>Beispiel

```XML
<Package
  xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"
  xmlns:rescap3="http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities/3"
  IgnorableNamespaces="uap3, rescap3">
  <Applications>
    <Application>
      <Extensions>
        <uap:Extension Category="windows.fileTypeAssociation">
          <uap3:FileTypeAssociation Name="Contoso">
            <rescap3:MigrationProgIds>
              <rescap3:MigrationProgId>Foo.Bar.1</rescap3:MigrationProgId>
              <rescap3:MigrationProgId>Foo.Bar.2</rescap3:MigrationProgId>
            </rescap3:MigrationProgIds>
          </uap3:FileTypeAssociation>
        </uap:Extension>
      </Extensions>
    </Application>
  </Applications>
</Package>
```
#### <a name="related-sample"></a>Verwandte Beispiele

[WPF-Bildanzeige mit Übergang/Migration/Deinstallation](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/DesktopAppTransition)

<span id="associate" />
### <a name="associate-your-packaged-app-with-a-set-of-file-types"></a>Ihre verpackte App einer Gruppe von Dateitypen zuordnen.

Sie können Ihre verpackte App mit Dateityperweiterungen zuordnen. Wenn ein Benutzer mit der rechten Maustaste auf eine Datei klickt und **Öffnen mit** auswählt, wird Ihre App in der Vorschlagsliste angezeigt.

#### <a name="xml-namespace"></a>XML-Namespace

* http://schemas.microsoft.com/appx/manifest/uap/windows10
* http://schemas.microsoft.com/appx/manifest/uap/windows10/3

#### <a name="elements-and-attributes-of-this-extension"></a>Elemente und Attribute dieser Erweiterung

```XML
<Extension Category="windows.fileTypeAssociation">
    <FileTypeAssociation Name="[AppID]">
        <SupportedFileTypes>
            <FileType>"[file extension]"</FileType>
        </SupportedFileTypes>
    </FileTypeAssociation>
</Extension>
```

Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).

|Name |Beschreibung |
|-------|-------------|
|Kategorie |Immer ``windows.fileTypeAssociation``.
|Name |Eine eindeutige ID für Ihre App. Diese ID wird intern verwendet, um einen [programmgesteuerte Bezeichner (Programm-ID)](https://msdn.microsoft.com/library/windows/desktop/cc144152.aspx) mit Hash zu generieren, die mit Ihrer Dateitypzuordnung verknüpft ist. Mithilfe dieser ID können Sie Änderungen in zukünftigen Versionen Ihrer App verwalten.   |
|FileType |Die Erweiterung, die von Ihrer App unterstützt wird. |

#### <a name="example"></a>Beispiel

```XML
<Package
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"
  IgnorableNamespaces="uap, uap3">
  <Applications>
    <Application>
      <Extensions>
        <uap:Extension Category="windows.fileTypeAssociation">
          <uap3:FileTypeAssociation Name="Contoso">
            <uap:SupportedFileTypes>
              <uap:FileType>.txt</uap:FileType>
              <uap:FileType>.avi</uap:FileType>
            </uap:SupportedFileTypes>
          </uap3:FileTypeAssociation>
        </uap:Extension>
      </Extensions>
    </Application>
  </Applications>
</Package>
```

#### <a name="related-sample"></a>Verwandte Beispiele

[WPF-Bildanzeige mit Übergang/Migration/Deinstallation](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/DesktopAppTransition)

<span id="add" />
### <a name="add-options-to-the-context-menus-of-files-that-have-a-certain-file-type"></a>Fügen Sie den Kontextmenüs der Dateien, die einen bestimmten Dateityp haben, Optionen hinzu.

In den meisten Fällen klicken Benutzer doppelt auf Dateien, um sie zu öffnen. Wenn Benutzer mit der rechten Maustaste auf eine Datei klicken, werden verschiedene Optionen angezeigt.

Sie können diesem Menü Optionen hinzufügen. Diese Optionen geben Benutzern weitere Möglichkeiten zur Interaktion mit der Datei, wie etwa Drucken, Bearbeiten oder das Anzeigen einer Vorschau.

#### <a name="xml-namespaces"></a>XML-Namespaces

* http://schemas.microsoft.com/appx/manifest/uap/windows10
* http://schemas.microsoft.com/appx/manifest/uap/windows10/2
* http://schemas.microsoft.com/appx/manifest/uap/windows10/3


#### <a name="elements-and-attributes-of-this-extension"></a>Elemente und Attribute dieser Erweiterung

```XML
<Extension Category="windows.fileTypeAssociation">
    <FileTypeAssociation Name="[AppID]">
        <SupportedVerbs>
              <Verb Id="[ID]" Extended="[Extended]" Parameters="[parameters]">"[verb label]"</Verb>
        </SupportedVerbs>
    </FileTypeAssociation>
</Extension>
```

Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).

|Name |Description |
|-------|-------------|
|Category | Immer ``windows.fileTypeAssociation``.
|Name |Eine eindeutige ID für Ihre App. |
|Verb |Der Name, der im Kontextmenü des Datei-Explorers angezeigt wird. Diese Zeichenfolge kann mithilfe von ```ms-resource``` lokalisiert werden.|
|ID |Die eindeutige ID des Verbs. Bei UWP-Apps wird sie im Rahmen der Aktivierungsereignisargumente übergeben, um eine entsprechende Behandlung der Benutzerauswahl zu ermöglichen. Bei vertrauenswürdig verpackten Apps werden dagegen Parameter übergeben (siehe nächster Aufzählungspunkt). |
|Parameter |Die Liste mit Argumentparametern und -werten für das Verb. Wenn Ihre App eine vertrauenswürdig verpackte App ist, werden diese Parameter bei der Aktivierung der App als Ereignisargumente an die App übergeben. Sie können das Verhalten Ihrer App auf Basis anderer Aktivierungsverben anpassen. Wenn eine Variable einen Dateipfad enthalten kann, schließen Sie den Parameterwert in Anführungszeichen. Dadurch werden jegliche Probleme vermieden, die in Fällen auftreten, bei denen der Pfad Leerzeichen enthält. Wenn Ihre App eine UWP-App ist, können Sie keine Parameter übergeben. Die App empfängt stattdessen die ID (siehe das vorherige Aufzählungszeichen).|
|Erweitert |Gibt an, dass das Verb nur angezeigt werden soll, wenn der Benutzer zum Anzeigen des Kontextmenüs **UMSCHALT** gedrückt hält, bevor er mit der rechten Maustaste auf die Datei klickt. Dieses Attribut ist optional und standardmäßig auf den Wert von **False** (Verb soll immer angezeigt werden) festgelegt. Dieses Verhalten muss für jedes Verb einzeln angegeben werden – mit Ausnahme von „Öffnen“: Bei diesem Verb ist der Wert immer **False**.|

#### <a name="example"></a>Beispiel

```XML
<Package
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
  xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"

  IgnorableNamespaces="uap, uap2, uap3">
  <Applications>
    <Application>
      <Extensions>
        <uap:Extension Category="windows.fileTypeAssociation">
          <uap3:FileTypeAssociation Name="Contoso">
            <uap2:SupportedVerbs>
              <uap3:Verb Id="Edit" Parameters="/e &quot;%1&quot;">Edit</uap3:Verb>
              <uap3:Verb Id="Print" Extended="true" Parameters="/p &quot;%1&quot;">Print</uap3:Verb>
            </uap2:SupportedVerbs>
          </uap3:FileTypeAssociation>
        </uap:Extension>
      </Extensions>
    </Application>
  </Applications>
</Package>
```
#### <a name="related-sample"></a>Verwandte Beispiele

[WPF-Bildanzeige mit Übergang/Migration/Deinstallation](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/DesktopAppTransition)

<span id="open" />
### <a name="open-certain-types-of-files-directly-by-using-a-url"></a>Öffnen Sie bestimmte Dateitypen direkt anhand einer URL

Sie können sicherstellen, dass Benutzer standardmäßig Ihre neu verpackte Version statt die Desktop-Version Ihrer App für bestimmte Dateitypen öffnen.

#### <a name="xml-namespaces"></a>XML-Namespaces

* http://schemas.microsoft.com/appx/manifest/uap/windows10
* http://schemas.microsoft.com/appx/manifest/uap/windows10/3"

#### <a name="elements-and-attributes-of-this-extension"></a>Elemente und Attribute dieser Erweiterung

```XML
<Extension Category="windows.fileTypeAssociation">
    <FileTypeAssociation Name="[AppID]" UseUrl="true" Parameters="%1">
        <SupportedFileTypes>
            <FileType>"[FileExtension]"</FileType>
        </SupportedFileTypes> 
    </FileTypeAssociation>
</Extension>
```

Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).

|Name |Description |
|-------|-------------|
|Category |Immer ``windows.fileTypeAssociation``.
|Name |Eine eindeutige ID für Ihre App. |
|UseUrl |Gibt an, ob Dateien direkt über eine URL-Ziel geöffnet werden sollen. Wenn Sie diesen Wert nicht festlegen, wird das System die Datei zunächst lokal herunterladen, wenn Ihre App versucht, die Datei durch eine URL zu öffnen. |
|Parameter |Optionale Parameter. |
|FileType |Die relevanten Dateierweiterungen. |

#### <a name="example"></a>Beispiel

```XML
<Package
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"
  IgnorableNamespaces="uap, uap3">
  <Applications>
      <Application>
        <Extensions>
          <uap:Extension Category="windows.fileTypeAssociation">
            <uap3:FileTypeAssociation Name="documenttypes" UseUrl="true" Parameters="%1">
              <uap:SupportedFileTypes>
                <uap:FileType>.txt</uap:FileType>
                <uap:FileType>.doc</uap:FileType>
              </uap:SupportedFileTypes> 
            </uap3:FileTypeAssociation>
          </uap:Extension>
        </Extensions>
      </Application>
    </Applications>
</Package>
```

## <a name="perform-setup-tasks"></a>Setup-Aufgaben ausführen

* [Erstellen von Firewallausnahmen für Ihre App](#rules)

<span id="rules" />
### <a name="create-firewall-exception-for-your-app"></a>Erstellen von Firewallausnahmen für Ihre App

Wenn bei Ihrer App eine Kommunikation über einen Anschluss erforderlich ist, können Sie Ihre App zur Liste der Firewallausnahmen hinzufügen.

#### <a name="xml-namespace"></a>XML-Namespace

http://schemas.microsoft.com/appx/manifest/desktop/windows10/2

#### <a name="elements-and-attributes-of-this-extension"></a>Elemente und Attribute dieser Erweiterung

```XML
<Extension Category="windows.firewallRules">  
  <FirewallRules Executable="[executable file name]">  
    <Rule
      Direction="[Direction]"
      IPProtocol="[Protocol]"
      LocalPortMin="[LocalPortMin]"
      LocalPortMax="LocalPortMax"
      RemotePortMin="RemotePortMin"
      RemotePortMax="RemotePortMax"
      Profile="[Profile]"/>  
  </FirewallRules>  
</Extension>
```
Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-desktop2-firewallrules).

|Name |Description |
|-------|-------------|
|Category |Immer ``windows.firewallRules``|
|Ausführbare Datei |Der Name der ausführbaren Datei, die Sie der Liste der Firewallausnahmen hinzufügen möchten. |
|Richtung |Gibt an, ob die Regel eine ein- oder ausgehende Regel ist. |
|IPProtocol |Das Kommunikationsprotokoll |
|LocalPortMin |Die untere Portnummer in einer Auswahl von lokalen Portnummern. |
|LocalPortMax |Die höchste Portnummer in einer Auswahl von lokalen Portnummern. |
|RemotePortMax |Die niedrigere Portnummer in einer Auswahl von Remoteportnummern. |
|RemotePortMax |Die höchste Portnummer in einer Auswahl Remoteportnummern. |
|Profil |Der Netzwerktyp |



#### <a name="example"></a>Beispiel

```XML
<Package
  xmlns:desktop2="http://schemas.microsoft.com/appx/manifest/desktop/windows10/2"
  IgnorableNamespaces="desktop2">
  <Extensions>
    <desktop2:Extension Category="windows.firewallRules">  
      <desktop2:FirewallRules Executable="Contoso.exe">  
          <desktop2:Rule Direction="in" IPProtocol="TCP" Profile="all"/>  
          <desktop2:Rule Direction="in" IPProtocol="UDP" LocalPortMin="1337" LocalPortMax="1338" Profile="domain"/>  
          <desktop2:Rule Direction="in" IPProtocol="UDP" LocalPortMin="1337" LocalPortMax="1338" Profile="public"/>  
          <desktop2:Rule Direction="out" IPProtocol="UDP" LocalPortMin="1339" LocalPortMax="1340" RemotePortMin="15"
                         RemotePortMax="19" Profile="domainAndPrivate"/>  
          <desktop2:Rule Direction="out" IPProtocol="GRE" Profile="private"/>  
      </desktop2:FirewallRules>  
  </desktop2:Extension>
</Extensions>
</Package>
```

## <a name="integrate-with-file-explorer"></a>Integration mit dem Datei-Explorer

Helfen Sie Benutzern beim Organisieren von Dateien und interagieren Sie mit Ihnen auf vertrauter Weise.

* [Definieren Sie, wie sich Ihre App verhält, wenn Benutzer mehrere Dateien gleichzeitig auswählen und öffnen.](#define)
* [Zeigen Sie Dateiinhalte in einem Miniaturbild im Datei-Explorer an.](#show)
* [Zeigen Sie Dateiinhalte in einer Vorschau des Datei-Explorers an.](#preview)
* [Ermöglichen Sie es Benutzern, Dateien mithilfe der Spalte „Art” im Datei-Explorer zu gruppieren.](#enable)
* [Stellen Sie den Bereichen Suchen, Index, Eigenschaftendialogfelder und Details Dateieigenschaften zur Verfügung.](#make-file-properties)

<span id="define" />
### <a name="define-how-your-app-behaves-when-users-select-and-open-multiple-files-at-the-same-time"></a>Definieren Sie, wie sich Ihre App verhält, wenn Benutzer mehrere Dateien gleichzeitig auswählen und öffnen.

Geben Sie an, wie sich die App verhält, wenn ein Benutzer mehrere Dateien gleichzeitig öffnet.

#### <a name="xml-namespaces"></a>XML-Namespaces

* http://schemas.microsoft.com/appx/manifest/uap/windows10
* http://schemas.microsoft.com/appx/manifest/uap/windows10/2
* http://schemas.microsoft.com/appx/manifest/uap/windows10/3

#### <a name="elements-and-attributes-of-this-extension"></a>Elemente und Attribute dieser Erweiterung

```XML
<Extension Category="windows.fileTypeAssociation">
    <FileTypeAssociation Name="[AppID]" MultiSelectModel="[SelectionModel]">
        <SupportedVerbs>
            <Verb Id="Edit" MultiSelectModel="[SelectionModel]">Edit</Verb>
        </SupportedVerbs>
          <SupportedFileTypes>
                <FileType>"[FileExtension]"</FileType>
        </SupportedFileTypes>
</Extension>
```
Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).

|Name |Beschreibung |
|-------|-------------|
|Kategorie |Immer ``windows.fileTypeAssociation``.
|Name |Eine eindeutige ID für Ihre App. |
|MultiSelectModel |Weitere Informationen finden Sie unter unten. |
|FileType |Die relevanten Dateierweiterungen. |

**MultSelectModel**

Bei verpackten Desktop-Apps stehen die gleichen drei Optionen zur Verfügung wie bei regulären Desktop-Apps.

 * ``Player``: Ihre App wird ein Mal aktiviert. Alle der ausgewählten Dateien werden an Ihre App als Argument-Parameter übergeben.
 * ``Single``: Ihre App wird einmal für die erste markierte Datei aktiviert. Andere Dateien werden ignoriert.
 * ``Document``: Für die markierten Dateien wird jeweils eine neue (eigene) Instanz Ihrer App aktiviert.

 Für unterschiedliche Dateitypen und Aktionen können unterschiedliche Einstellungen festgelegt werden. So können beispielsweise *Dokumente* im Modus *Document* und *Bilder* im Modus *Player* geöffnet werden.

#### <a name="example"></a>Beispiel

```XML
<Package
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
  xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"
  IgnorableNamespaces="uap, uap2, uap3">
  <Applications>
    <Application>
      <Extensions>
        <uap:Extension Category="windows.fileTypeAssociation">
          <uap3:FileTypeAssociation Name="myapp" MultiSelectModel="Document">
            <uap2:SupportedVerbs>
              <uap3:Verb Id="Edit" MultiSelectModel="Player">Edit</uap3:Verb>
              <uap3:Verb Id="Preview" MultiSelectModel="Document">Preview</uap3:Verb>
            </uap2:SupportedVerbs>
            <uap:SupportedFileTypes>
                <uap:FileType>.txt</uap:FileType>
            </uap:SupportedFileTypes>
        </uap:Extension>
      </Extensions>
    </Application>
  </Applications>
</Package>
```

Wenn der Benutzer 15 oder weniger Dateien öffnet, ist die Standardauswahl des **MultiSelectModel**-Attributs *Player*. Andernfalls ist die Standardauswahl *Document*. UWP-Apps werden immer als *Player* gestartet.

<span id="show" />
### <a name="show-file-contents-in-a-thumbnail-image-within-file-explorer"></a>Zeigen Sie Dateiinhalte in einem Miniaturbild im Datei-Explorer an.

Ermöglichen Sie es Benutzern, eine Miniaturansicht des Dateiinhalts anzuzeigen, wenn das Symbol der Datei in den Größen Mittel, Groß, oder extra Groß angezeigt wird.

#### <a name="xml-namespace"></a>XML-Namespace

* http://schemas.microsoft.com/appx/manifest/uap/windows10
* http://schemas.microsoft.com/appx/manifest/uap/windows10/2
* http://schemas.microsoft.com/appx/manifest/uap/windows10/3
* http://schemas.microsoft.com/appx/manifest/desktop/windows10/2

#### <a name="elements-and-attributes-of-this-extension"></a>Elemente und Attribute dieser Erweiterung

```XML
<Extension Category="windows.fileTypeAssociation">
    <FileTypeAssociation Name="[AppID]">
        <SupportedFileTypes>
            <FileType>"[FileExtension]"</FileType>
        </SupportedFileTypes>
        <ThumbnailHandler
            Clsid  ="[Clsid  ]"
            Cutoff="[Cutoff]"
            Treatment="[Treatment]" />
    </FileTypeAssociation>
</Extension>
```

Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).

|Name |Beschreibung |
|-------|-------------|
|Kategorie |Immer ``windows.fileTypeAssociation``.
|Name |Eine eindeutige ID für Ihre App. |
|FileType |Die relevanten Dateierweiterungen. |
|Clsid   |Die Klassen-ID Ihrer App. |
|Trennungswert |Die Größe, unter der eine Miniaturansicht nicht verwendet wird. Weitere Informationen finden Sie unter [Miniaturansichtscache und Anpassung](https://msdn.microsoft.com/library/windows/desktop/cc144118.aspx#cache) |
|Behandlung |Das [Miniaturansicht-Zusatzelement](https://msdn.microsoft.com/library/windows/desktop/cc144118.aspx#adornments), das das Erscheinungsbild des Miniaturansichtsymbols definiert. |

#### <a name="example"></a>Beispiel

```XML
<Package
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
  xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"
  xmlns:desktop2="http://schemas.microsoft.com/appx/manifest/desktop/windows10/2"
  IgnorableNamespaces="uap, uap2, uap3, desktop2">
  <Applications>
    <Application>
      <Extensions>
        <uap:Extension Category="windows.fileTypeAssociation">
          <uap3:FileTypeAssociation Name="Contoso">
            <uap2:SupportedFileTypes>
              <uap:FileType>.bar</uap:FileType>
            </uap2:SupportedFileTypes>
            <desktop2:ThumbnailHandler
              Clsid  ="20000000-0000-0000-0000-000000000001"
              Cutoff="20x20"
              Treatment="Video Sprockets" />
            </uap3:FileTypeAssociation>
         </uap::Extension>
      </Extensions>
    </Application>
  </Applications>
</Package>
```

<span id="preview" />
### <a name="show-file-contents-in-the-preview-pane-of-file-explorer"></a>Zeigen Sie Dateiinhalte in der Vorschau des Datei-Explorers an.

Ermöglichen Sie es Benutzern, den Inhalt einer Datei in Vorschaubereich des Datei-Explorers anzuzeigen.

#### <a name="xml-namespace"></a>XML-Namespace

* http://schemas.microsoft.com/appx/manifest/uap/windows10
* http://schemas.microsoft.com/appx/manifest/uap/windows10/2
* http://schemas.microsoft.com/appx/manifest/uap/windows10/3
* http://schemas.microsoft.com/appx/manifest/desktop/windows10/2

#### <a name="elements-and-attributes-of-this-extension"></a>Elemente und Attribute dieser Erweiterung

```XML
<Extension Category="windows.fileTypeAssociation">
    <FileTypeAssociation Name="[AppID]">
        <SupportedFileTypes>
            <FileType>"[FileExtension]"</FileType>
        </SupportedFileTypes>
        <DesktopPreviewHandler Clsid  ="[Clsid  ]" />
    </FileTypeAssociation>
</Extension>
```

Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).

|Name |Beschreibung |
|-------|-------------|
|Kategorie |Immer ``windows.fileTypeAssociation``.
|Name |Eine eindeutige ID für Ihre App. |
|FileType |Die relevanten Dateierweiterungen. |
|Clsid   |Die Klassen-ID Ihrer App. |

#### <a name="example"></a>Beispiel

```XML
<Package
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
  xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"
  xmlns:desktop2="http://schemas.microsoft.com/appx/manifest/desktop/windows10/2"
  IgnorableNamespaces="uap, uap2, uap3, desktop2">
  <Applications>
    <Application>
      <Extensions>
        <uap:Extension Category="windows.fileTypeAssociation">
          <uap3:FileTypeAssociation Name="Contoso">
            <uap2SupportedFileTypes>
              <uap:FileType>.bar</uap:FileType>
                </uap2SupportedFileTypes>
              <desktop2:DesktopPreviewHandler Clsid ="20000000-0000-0000-0000-000000000001" />
           </uap3:FileTypeAssociation>
        </uap:Extension>
      </Extensions>
    </Application>
  </Applications>
</Package>
```

<span id="enable" />
### <a name="enable-users-to-group-files-by-using-the-kind-column-in-file-explorer"></a>Ermöglichen Sie es Benutzern, Dateien mithilfe der Spalte „Art” im Datei-Explorer zu gruppieren.

Sie können einen oder mehrere vordefinierte Werte für die Dateitypen mit dem **Art**-Feld zuordnen.

Im Datei-Explorer können Benutzer diese Dateien mithilfe dieses Felds gruppieren. Systemkomponenten verwenden auch dieses Feld für verschiedene Zwecke, wie etwa für die Indizierung.

Für weitere Informationen zum **Art**-Feld und die Werte, die Sie für dieses Feld verwenden können, finden Sie unter [Art Namen verwenden](https://msdn.microsoft.com/library/windows/desktop/cc144136.aspx).

#### <a name="xml-namespaces"></a>XML-Namespaces

* http://schemas.microsoft.com/appx/manifest/uap/windows10
* http://schemas.microsoft.com/appx/Manifest/foundation/windows10/restrictedcapabilities/3

#### <a name="elements-and-attributes-of-this-extension"></a>Elemente und Attribute dieser Erweiterung

```XML
<Extension Category="windows.fileTypeAssociation">
    <FileTypeAssociation Name="[AppID]">
        <SupportedFileTypes>
            <FileType>"[FileExtension]"</FileType>
        </SupportedFileTypes>
        <KindMap>
            <Kind value="[KindValue]">
        </KindMap>
    </FileTypeAssociation>
</Extension>
```
Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).

|Name |Beschreibung |
|-------|-------------|
|Kategorie |Immer ``windows.fileTypeAssociation``.
|Name |Eine eindeutige ID für Ihre App. |
|FileType |Die relevanten Dateierweiterungen. |
|Wert |Ein gültiger [Art-Wert](https://msdn.microsoft.com/en-us/library/windows/desktop/cc144136.aspx#kind_hierarchy) |

#### <a name="example"></a>Beispiel

```XML
<Package
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:rescap="http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities/3"
  IgnorableNamespaces="uap, rescap">
  <Applications>
    <Application>
      <Extensions>
        <uap:Extension Category="windows.fileTypeAssociation">
           <uap:FileTypeAssociation Name="Contoso">
             <uap:SupportedFileTypes>
               <uap:FileType>.m4a</uap:FileType>
               <uap:FileType>.mta</uap:FileType>
             </uap:SupportedFileTypes>
             <rescap:KindMap>
               <rescap:Kind value="Item">
               <rescap:Kind value="Communications">
               <rescap:Kind value="Task">
             </rescap:KindMap>
          </uap:FileTypeAssociation>
      </uap:Extension>
      </Extensions>
    </Application>
  </Applications>
</Package>
```
<span id="make-file-properties" />
### <a name="make-file-properties-available-to-search-index-property-dialogs-and-the-details-pane"></a>Stellen Sie den Bereichen Suchen, Index, Eigenschaftendialogfelder und Details Dateieigenschaften zur Verfügung.

#### <a name="xml-namespace"></a>XML-Namespace

* http://schemas.microsoft.com/appx/manifest/uap/windows10
* http://schemas.microsoft.com/appx/manifest/uap/windows10/3
* http://schemas.microsoft.com/appx/manifest/desktop/windows10/2

#### <a name="elements-and-attributes-of-this-extension"></a>Elemente und Attribute dieser Erweiterung

```XML
<uap:Extension Category="windows.fileTypeAssociation">
    <uap:FileTypeAssociation Name="[AppID]">
        <SupportedFileTypes>
            <FileType>.bar</FileType>
        </SupportedFileTypes>
        <DesktopPropertyHandler Clsid ="[Clsid ]"/>
    </uap:FileTypeAssociation>
</uap:Extension>
```
**Wichtige Element- und Attributbeschreibungen**

Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).

|Name |Beschreibung |
|-------|-------------|
|Kategorie |Immer ``windows.fileTypeAssociation``.
|Name |Eine eindeutige ID für Ihre App. |
|FileType |Die relevanten Dateierweiterungen. |
|Clsid  |Die Klassen-ID Ihrer App. |

#### <a name="example"></a>Beispiel

```XML
<Package
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"
  xmlns:desktop2="http://schemas.microsoft.com/appx/manifest/desktop/windows10/2"
  IgnorableNamespaces="uap, uap3, desktop2">
  <Applications>
    <Application>
      <Extensions>
        <uap:Extension Category="windows.fileTypeAssociation">
          <uap3:FileTypeAssociation Name="Contoso">
            <uap:SupportedFileTypes>
              <uap:FileType>.bar</uap:FileType>
            </uap:SupportedFileTypes>
            <desktop2:DesktopPropertyHandler Clsid ="20000000-0000-0000-0000-000000000001"/>
          </uap3:FileTypeAssociation>
        </uap:Extension>
      </Extensions>
    </Application>
  </Applications>
</Package>
```

<span id="start" />
## <a name="start-your-app-in-different-ways"></a>Starten Sie Ihre App auf unterschiedlicher Weise.

* [Starten Sie die App über ein Protokoll.](#protocol)
* [Starten Sie Ihre App unter Verwendung eines Alias.](#alias)
* [Starten Sie eine ausführbare Datei, wenn Benutzer sich bei Windows anmelden.](#executable)
* [Nach dem Empfang einer Aktualisierung aus dem Windows Store starten Sie automatisch neu](#updates)

<span id="protocol" />
### <a name="start-your-app-by-using-a-protocol"></a>Starten Sie die App über ein Protokoll.

Protokollzuordnungen ermöglichen es anderen Programmen und Systemkomponenten, mit ihrer verpackten App zu interagieren. Wenn Ihre verpackte App anhand eines Protokolls gestartet wird, können Sie bestimmte Parameter angeben, die an die Aktivierungsereignisargumente übergeben werden sollen, um ein entsprechendes Verhalten zu erreichen. Parameter werden nur für verpackte, vertrauenswürdige Apps unterstützt. UWP-Apps können die Parameter nicht verwenden.  

#### <a name="xml-namespace"></a>XML-Namespace

http://schemas.microsoft.com/appx/manifest/uap/windows10/3


#### <a name="elements-and-attributes-of-this-extension"></a>Elemente und Attribute dieser Erweiterung

```XML
<Extension
    Category="windows.protocol">
    <Protocol
      Name="[Protocol name]"
      Parameters="[Parameters]" />
</Extension>
```

Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-protocol).

|Name |Beschreibung |
|-------|-------------|
|Kategorie |Immer ``windows.protocol``.
|Name |Der Name des Protokolls. |
|Parameter |Die Liste der Parameter und Werte, die bei der Aktivierung Ihrer App als Ereignisargumente an Ihre App übergeben werden sollen. Wenn eine Variable einen Dateipfad enthalten kann, schließen Sie den Parameterwert in Anführungszeichen. Dadurch werden jegliche Probleme vermieden, die in Fällen auftreten, bei denen der Pfad Leerzeichen enthält. |

### <a name="example"></a>Beispiel

```XML
<Package
  xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"
  IgnorableNamespaces="uap3">
  <Applications>
    <Application>
      <Extensions>
        <uap3:Extension
          Category="windows.protocol">
        <uap3:Protocol
          Name="myapp-cmd"
          Parameters="/p &quot;%1&quot;" />
        </uap3:Extension>
      </Extensions>
    </Application>
  </Applications>
</Package>
```
<span id="alias" />
### <a name="start-your-app-by-using-an-alias"></a>Starten Sie Ihre App unter Verwendung eines Alias.

Benutzer und andere Prozesse können einen Alias verwenden, um Ihre App zu starten, ohne den vollständigen Pfad zu Ihrer App angeben zu müssen. Sie können diesen Aliasnamen angeben.

#### <a name="xml-namespaces"></a>XML-Namespaces

* http://schemas.microsoft.com/appx/manifest/uap/windows10/3
* http://schemas.microsoft.com/appx/manifest/desktop/windows10


#### <a name="elements-and-attributes-of-this-extension"></a>Elemente und Attribute dieser Erweiterung

```XML
<Extension
    Category="windows.appExecutionAlias"
    Executable="[ExecutableName]"
    EntryPoint="Windows.FullTrustApplication">
    <AppExecutionAlias>
            <desktop:ExecutionAlias Alias="[AliasName]" />
      </AppExecutionAlias>
</Extension>
```

|Name |Beschreibung |
|-------|-------------|
|Kategorie |Immer ``windows.appExecutionAlias``.
|Ausführbare Datei |Der relative Pfad zur ausführbaren Datei, die beim Aufrufen des Alias gestartet wird. |
|Alias |Der kurze Name für Ihre App. Er muss immer mit der Erweiterung „.exe“ enden. Für die einzelnen Anwendungen im Paket kann immer nur einzelner App-Ausführungsalias angegeben werden. Wenn sich mehrere Apps mit dem gleichen Alias registrieren, ruft das System die zuletzt registrierte App auf. Wählen Sie daher einen eindeutigen Alias, um die Wahrscheinlichkeit einer Überschreibung durch andere Apps möglichst gering zu halten.
|

#### <a name="example"></a>Beispiel

```XML
<Package
  xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"
  xmlns:desktop="http://schemas.microsoft.com/appx/manifest/desktop/windows10"
  IgnorableNamespaces="uap3, desktop">
  ...
  <uap3:Extension
        Category="windows.appExecutionAlias"
        Executable="exes\launcher.exe"
        EntryPoint="Windows.FullTrustApplication">
        <uap3:AppExecutionAlias>
            <desktop:ExecutionAlias Alias="Contoso.exe" />
        </uap3:AppExecutionAlias>
  </uap3:Extension>
...
</Package>
```

Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).

|Name |Beschreibung |
|-------|-------------|
|Kategorie |Immer ``windows.fileTypeAssociation``.
|Name |Eine eindeutige ID für Ihre App. Diese ID wird intern verwendet, um einen [programmgesteuerte Bezeichner (Programm-ID)](https://msdn.microsoft.com/library/windows/desktop/cc144152.aspx) mit Hash zu generieren, die mit Ihrer Dateitypzuordnung verknüpft ist. Mithilfe dieser ID können Sie Änderungen in zukünftigen Versionen Ihrer App verwalten.   |
|FileType |Die Erweiterung, die von Ihrer App unterstützt wird. |

<span id="executable" />
### <a name="start-an-executable-file-when-users-log-into-windows"></a>Starten Sie eine ausführbare Datei, wenn Benutzer sich bei Windows anmelden.

Startaufgaben ermöglichen der App das automatische Ausführen einer ausführbaren Datei, wenn sich ein Benutzer anmeldet.

> [!NOTE]
> Der Benutzer muss Ihre App mindestens ein Mal starten, um diese Startaufgabe registrieren.

Ihre App kann mehrere Startaufgaben deklarieren. Die Aufgaben beginnen unabhängig voneinander. Alle Startaufgaben werden im Task-Manager auf der Registerkarte **Autostart** mit dem Namen aus Ihrem App-Manifest und dem Symbol Ihrer App angezeigt. Der Task-Manager analysiert automatisch die Startauswirkungen Ihrer Aufgaben.

Benutzer können die Startaufgabe Ihrer App manuell mithilfe des Task-Managers deaktivieren. Wenn ein Benutzer eine Aufgabe deaktiviert, können Sie sie nicht erneut programmgesteuert aktivieren.

#### <a name="xml-namespace"></a>XML-Namespace

http://schemas.microsoft.com/appx/manifest/desktop/windows10

#### <a name="elements-and-attributes-of-this-extension"></a>Elemente und Attribute dieser Erweiterung

```XML
<Extension
    Category="windows.startupTask"
    Executable="[ExecutableName]"
    EntryPoint="Windows.FullTrustApplication">
    <StartupTask
      TaskId="[TaskID]"
      Enabled="true"
      DisplayName="[DisplayName]" />
</Extension>
```

|Name |Beschreibung |
|-------|-------------|
|Kategorie |Immer ``windows.startupTask``.|
|Ausführbare Datei |Der relative Pfad der ausführbaren Datei, die gestartet werden soll. |
|TaskId |Ein eindeutiger Bezeichner Ihrer Aufgabe. Mit diesem Bezeichner kann Ihre App die APIs in der [Windows.ApplicationModel.StartupTask](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.StartupTask)-Klasse aufrufen, um eine Startaufgabe programmgesteuert zu aktivieren oder zu deaktivieren. |
|Enabled |Gibt an, ob die Aufgabe erst aktiviert oder deaktiviert gestartet wird. Aktivierte Aufgaben werden bei der nächsten Anmeldung des Benutzers ausgeführt (es sei denn, der Benutzer deaktiviert sie). |
|DisplayName |Der Name der Aufgabe, die im Task-Manager angezeigt wird. Sie können diese Zeichenfolge mit ```ms-resource``` lokalisieren. |

#### <a name="example"></a>Beispiel

```XML
<Package
  xmlns:desktop="http://schemas.microsoft.com/appx/manifest/desktop/windows10"
  IgnorableNamespaces="desktop">
  <Applications>
    <Application>
      <Extensions>
        <desktop:Extension
          Category="windows.startupTask"
          Executable="bin\MyStartupTask.exe"
          EntryPoint="Windows.FullTrustApplication">
          <desktop:StartupTask
          TaskId="MyStartupTask"
          Enabled="true"
          DisplayName="My App Service" />
        </desktop:Extension>
      </Extensions>
    </Application>
  </Applications>
 </Package>
```

<span id="updates" />
### <a name="restart-automatically-after-receiving-an-update-from-the-windows-store"></a>Nach dem Empfang einer Aktualisierung aus dem Windows Store starten Sie automatisch neu

Wenn Ihre App geöffnet ist, wenn Benutzer ein Update installieren, wird die App geschlossen.

Wenn Sie möchten, dass die App neu startet, nachdem das Update abgeschlossen ist, rufen Sie die [RegisterApplicationRestart ist](https://msdn.microsoft.com/library/windows/desktop/aa373347.aspx) Funktion in jedem neu zu startenden Prozess auf.

Jedes aktiven Fenster in Ihrer App erhält eine [WM_QUERYENDSESSION](https://msdn.microsoft.com/library/windows/desktop/aa376890.aspx) Nachricht. An diesem Punkt kann Ihre App die [RegisterApplicationRestart ist](https://msdn.microsoft.com/library/windows/desktop/aa373347.aspx) Funktion erneut aufrufen, um die Befehlszeile bei Bedarf zu aktualisieren.

Wenn jedes aktiven Fenster in Ihre App die [WM_ENDSESSION](https://msdn.microsoft.com/library/windows/desktop/aa376889.aspx)-Nachricht erhält, sollte die App die Daten speichern und herunterfahren.

>[!NOTE]
Die aktiven Fenster erhalte ebenfalls die [WM_CLOSE](https://msdn.microsoft.com/library/windows/desktop/ms632617.aspx)-Nachricht falls die App nicht die [WM_ENDSESSION](https://msdn.microsoft.com/library/windows/desktop/aa376889.aspx)-Nachricht behandelt.

Zu diesem Zeitpunkt hat Ihre App 30Sekunden, um ihre eigenen Prozesse zu schließen (oder die Plattform beendet diese).

Nachdem das Update abgeschlossen ist, startet Ihre App neu.

## <a name="work-with-other-applications"></a>Zusammenarbeit mit anderen Anwendungen

Mit anderen Apps integrieren, andere Prozesse starten oder Informationen freigeben.

* [Legen Sie Ihre App als Druckerziel in Anwendungen fest, die das Drucken unterstützen.](#printing)
* [Freigeben von Schriftarten für andere Windows-Anwendungen](#fonts)
* [Starten Sie einen Win32-Prozess aus einer Universellen Windows-Plattform-App (UWP-App).](#win32-process)

<span id="printing" />
### <a name="make-your-app-appear-as-the-print-target-in-applications-that-support-printing"></a>Legen Sie Ihre App als Druckerziel in Anwendungen fest, die das Drucken unterstützen.

Wenn Benutzer Benutzer Daten aus einer anderen App wie z.B. Editor drucken möchten, können Sie Ihre App als Druckerziel in der App-Liste der verfügbaren Druckerziele anzeigen lassen.

Sie müssen Ihre App so einrichten, dass sie Daten im XML Paper Specification-Format (XPS-Format) empfängt.

#### <a name="xml-namespaces"></a>XML-Namespaces

http://schemas.microsoft.com/appx/manifest/desktop/windows10/2

#### <a name="elements-and-attributes-of-this-extension"></a>Elemente und Attribute dieser Erweiterung

```XML
<Extension Category="windows.appPrinter">
    <AppPrinter
        DisplayName="[DisplayName]"
        Parameters="[Parameters]" />
</Extension>
```

Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-desktop2-appprinter).

|Name |Beschreibung |
|-------|-------------|
|Kategorie |Immer ``windows.appPrinter``.
|DisplayName |Der Name, der in der Liste der Druckerziele für eine App angezeigt werden soll. |
|Parameter |Parameter, die Ihre App benötigt, um die Anforderung ordnungsgemäß zu behandeln. |

#### <a name="example"></a>Beispiel

```XML
<Package
  xmlns:desktop2="http://schemas.microsoft.com/appx/manifest/desktop/windows10/2"
  IgnorableNamespaces="desktop2">
  <Applications>
  <Application>
    <Extensions>
      <desktop2:Extension Category="windows.appPrinter">
        <desktop2:AppPrinter
          DisplayName="Send to Contoso"
          Parameters="/insertdoc %1" />
      </desktop2:Extension>
    </Extensions>
  </Application>
</Applications>
</Package>
```
Suchen Sie [hier](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/PrintToPDF) ein Beispiel, in dem diese Erweiterung verwendet wird.

<span id="fonts" />
### <a name="share-fonts-with-other-windows-applications"></a>Freigeben von Schriftarten für andere Windows-Anwendungen

Teilen Sie Ihre benutzerdefinierten Schriftarten mit einer anderen Windows-Anwendungen.

#### <a name="xml-namespaces"></a>XML-Namespaces

http://schemas.microsoft.com/appx/manifest/desktop/windows10/2

#### <a name="elements-and-attributes-of-this-extension"></a>Elemente und Attribute dieser Erweiterung

```XML
<Extension Category="windows.sharedFonts">
    <SharedFonts>
      <Font File="[FontFile]" />
    </SharedFonts>
  </Extension>
```

Die vollständige Schemareferenz finden Sie [hier](https://review.docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap4-sharedfonts).


|Name |Beschreibung |
|-------|-------------|
|Kategorie |Immer ``windows.sharedFonts``.
|Datei |Die Datei mit der Schriftart, die Sie teilen möchten. |

#### <a name="example"></a>Beispiel

```XML
<Package
  xmlns:uap4="http://schemas.microsoft.com/appx/manifest/uap/windows10/4"
  IgnorableNamespaces="uap4">
  <Applications>
    <Application>
      <Extensions>
        <uap4:Extension Category="windows.sharedFonts">
          <uap4:SharedFonts>
            <uap4:Font File="Fonts\JustRealize.ttf" />
            <uap4:Font File="Fonts\JustRealizeBold.ttf" />
          </uap4:SharedFonts>
        </uap4:Extension>
      </Extensions>
    </Application>
  </Applications>
</Package>
```
<span id="win32-process" />
### <a name="start-a-win32-process-from-a-universal-windows-platform-uwp-app"></a>Starten Sie einen Win32-Prozess aus einer Universellen Windows-Plattform-App (UWP-App).

Starten Sie einen vertrauenswürdigen Win32-Prozess.

#### <a name="xml-namespaces"></a>XML-Namespaces

http://schemas.microsoft.com/appx/manifest/desktop/windows10

#### <a name="elements-and-attributes-of-this-extension"></a>Elemente und Attribute dieser Erweiterung

```XML
<xtension Category="windows.fullTrustProcess" Executable="[executable file]">
  <FullTrustProcess>
    <ParameterGroup GroupId="[GroupID]" Parameters="[Parameters]"/>
  </FullTrustProcess>
</Extension>
```

|Name |Beschreibung |
|-------|-------------|
|Kategorie |Immer ``windows.fullTrustProcess``.
|Gruppen-ID |Eine Zeichenfolge, die eine Reihe von Parametern identifiziert, die an die ausführbare Datei übergeben werden sollen. |
|Parameter |Parameter, die an die ausführbare Datei übergeben werden sollen. |

#### <a name="example"></a>Beispiel

```XML
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
         xmlns:rescap=
"http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities"
         xmlns:desktop="http://schemas.microsoft.com/appx/manifest/desktop/windows10">
  ...
  <Capabilities>
      <rescap:Capability Name="runFullTrust"/>
  </Capabilities>
  <Applications>
    <Application>
      <Extensions>
          <desktop:Extension Category="windows.fullTrustProcess" Executable="fulltrustprocess.exe">
              <desktop:FullTrustProcess>
                  <desktop:ParameterGroup GroupId="SyncGroup" Parameters="/Sync"/>
                  <desktop:ParameterGroup GroupId="OtherGroup" Parameters="/Other"/>
              </desktop:FullTrustProcess>
           </desktop:Extension>
      </Extensions>
    </Application>
  </Applications>
</Package>
```
Diese Erweiterung kann hilfreich sein, wenn Sie eine Universelle Windows-Plattform-Benutzeroberfläche erstellen möchten, die auf allen Geräten ausgeführt werden soll. Dabei sollen aber auch die Komponenten der Win32-App weiterhin in voller Vertrauenswürdigkeit ausgeführt werden.

Erstellen Sie einfach ein Desktop-Brücke-Paket für die Win32-App. Fügen Sie dann der Paketdatei Ihrer UWP-App diese Erweiterung hinzu. Diese Erweiterungen gibt an, dass Sie eine ausführbare Datei im Desktop-Brücke-Paket starten möchten.  Wenn Sie zwischen Ihrer UWP-App und Ihrer Win32-App kommunizieren möchten, können Sie einen oder mehrere [App-Dienste](../launch-resume/app-services.md) dafür festlegen. Weitere Informationen zu diesem Szenario finden Sie [hier](https://blogs.msdn.microsoft.com/appconsult/2016/12/19/desktop-bridge-the-migrate-phase-invoking-a-win32-process-from-a-uwp-app/).

## <a name="next-steps"></a>Nächste Schritte

**Antworten auf bestimmte Fragen finden**

Unser Team überwacht diese [StackOverflow-Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).

**Geben Sie Feedback zu diesem Artikel**

Verwenden Sie den Kommentarabschnitt weiter unten.
