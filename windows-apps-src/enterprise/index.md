---
ms.assetid: 4b0c86d3-f05b-450b-bf9c-6ab4d3f07d31
description: Diese Roadmap enthält eine Übersicht über wichtige Unternehmensfeatures für Windows 10 und universelle Windows-Plattform (UWP)-apps.
title: Enterprise
ms.date: 08/30/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 6cce98591cdaa78a887d7a5fb495e999a4ffc453
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8945376"
---
# <a name="enterprise"></a>Enterprise

Dieser Artikel enthält eine Übersicht über wichtige Unternehmensfeatures, indem Sie die universelle Windows-Plattform (UWP) für Windows 10-apps bereitgestellt.

## <a name="whats-new-and-recent-for-enterprise-applications"></a>Was ist neu und aktuellen für unternehmensanwendungen

> [!div class="checklist"]
> * [Windows Template Studio](#template-studio)
> * [Erstellen von Benutzeroberflächen, die Desktop-Stil-Steuerelemente](#desktop-style-UI)
> * [Steuerelemente zur Unterstützung von Enterprise-Szenarien](#enterprise)
> * [Windows-UI-Bibliothek](#UI-library)
> * [UWP-Steuerelemente in Desktopanwendungen](#xaml-islands)
> * [.NET Standard 2.0](#standard)
> * [SQL Server-Konnektivität](#sql-server)
> * [MSIX-Bereitstellung](#MSIX)

Ein Video, das einige dieser Features ausführlich veranschaulicht, finden Sie [Schnell erstellen LOB-Apps mit UWP und Visual Studio](https://channel9.msdn.com/Events/Build/2018/BRK3502).

<a id="template-studio" />

### <a name="windows-template-studio"></a>Windows Template Studio

Windows Template Studio ist eine Visual Studio-2017-Erweiterung, die die Erstellung des neuen universellen Windows-Plattform (UWP)-apps, die mit einer Umgebung beschleunigt. Das resultierende UWP-Projekt ist wohlgeformte, lesbar Code, der die neuesten Windows 10-Features mit bewährten Muster und bewährten Methoden implementieren.

![Windows Template Studio](images/windows-template-studio.png)

Finden Sie unter [Windows Template Studio](https://marketplace.visualstudio.com/items?itemName=WASTeamAccount.WindowsTemplateStudio)

<a id="desktop-style-UI" />

### <a name="controls-to-create-desktop-style-uis"></a>Erstellen von Benutzeroberflächen, die Desktop-Stil-Steuerelemente

Wir haben neue UWP-XAML-Steuerelemente zur Verfügung, die die Lücke zwischen einer herkömmlichen Desktopanwendung UI und eine UWP-UI.

Z. B. die neuen [Menüleiste](https://review.docs.microsoft.com/en-us/windows/uwp/design/controls-and-patterns/menus?branch=jimwalk%2Frs5-menu-bar), [DropDownButton](https://docs.microsoft.com/en-us/windows/uwp/design/controls-and-patterns/buttons#create-a-drop-down-button), [SplitButton](https://docs.microsoft.com/en-us/windows/uwp/design/controls-and-patterns/buttons#create-a-split-button)und [CommandBarFlyout](https://review.docs.microsoft.com/en-us/windows/uwp/design/controls-and-patterns/command-bar-flyout?branch=jimwalk%2Frs5-command-bar-flyout) Steuerelemente bieten Ihnen die flexiblere Methoden, die Befehle verfügbar zu machen, und lassen Sie uns der Benutzer eingeben der [EditableComboBox](https://review.docs.microsoft.com/en-us/windows/uwp/design/controls-and-patterns/combo-box?branch=rs5#make-a-combo-box-editable) Werte, die nicht genannt sind in einer vordefinierten Liste von Optionen.

![Menüleiste](images/menu-bar.png)

<a id="enterprise" />

### <a name="controls-to-support-enterprise-scenarios"></a>Steuerelemente zur Unterstützung von Enterprise-Szenarien

[DataGridView](https://docs.microsoft.com/en-us/windows/communitytoolkit/controls/datagrid) bietet eine flexible Möglichkeit zum Anzeigen einer Sammlungs von Daten in Zeilen und Spalten.

Die [TreeView](https://docs.microsoft.com/windows/uwp/design/controls-and-patterns/tree-view) ermöglicht eine hierarchieauflistung mit Knoten, die geschachtelten Elementen erlauben aus- und einblenden. Es kann verwendet werden, um eine Ordnerstruktur oder geschachtelte Beziehungen zwischen Elementen in der Benutzeroberfläche zu veranschaulichen.

![DataGrid-Steuerelement](images/DataGrid.gif)


### <a name="windows-ui-library"></a>Windows-UI-Bibliothek

Der Windows-UI-Bibliothek ist eine Reihe von NuGet-Pakete, die Steuerelemente und andere Elemente der Benutzeroberfläche für UWP-apps bereitstellen. Darüber hinaus ermöglicht Sie kompatible Kompatibilität mit früheren Versionen von Windows 10, damit Ihre app funktioniert, auch wenn der Benutzer nicht über das neueste Betriebssystem verfügen.

![Windows-UI-Bibliothek](images/win-ui.png)

Finden Sie unter [Windows-UI-Bibliothek (Preview-Version)](https://docs.microsoft.com/en-us/uwp/toolkits/winui/).

<a id="xaml-islands" />

### <a name="uwp-controls-in-desktop-applications"></a>UWP-Steuerelemente in Desktopanwendungen

Windows 10 können jetzt Sie UWP-Steuerelemente in WPF-, Windows Forms und C++ Win32-desktop-Apps zu verwenden. Dies bedeutet, dass Sie das Erscheinungsbild und Funktionalität Ihrer vorhandenen desktop-Anwendungen mit den neuesten Windows 10-UI-Funktionen, die nur zur Verfügung, über UWP-Steuerelemente, z. B. Windows Ink und Steuerelemente, die das Fluent Design System unterstützen verbessern können. Dieses Feature ist XAML-Inseln bezeichnet.

Finden Sie in [UWP-Steuerelemente in desktop-Apps](https://docs.microsoft.com/windows/uwp/xaml-platform/xaml-host-controls).

<a id="standard" />

### <a name="net-standard-20"></a>.NET Standard 2.0

.NET Standard enthält über 20.000 weitere APIs als .NET Standard 1.x. Dadurch sehr viel einfacher zu migrieren von vorhandenen .NET Framework-Bibliotheken und anschließend für verschiedene .NET-Apps, einschließlich Ihrer UWP-Anwendung zu verwenden.

![NET-standard](images/dot-net-standard-project-template.png)

[Freigeben von Code zwischen einer desktop-app und einer UWP-app](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-migrate)wird angezeigt.

<a id="sql-server" />

### <a name="sql-server-connectivity"></a>SQL Server-Konnektivität

Ihre App kann sich direkt mit einer SQL Server-Datenbank verbinden und dann Daten über Klassen im Namespace [System.Data.SqlClient](https://docs.microsoft.com/dotnet/api/system.data.sqlclient?redirectedfrom=MSDN&view=netframework-4.7.2) speichern und abrufen.

Mehr unter [Verwenden einer SQL Server-Datenbank in einer UWP-App](https://docs.microsoft.com/en-us/windows/uwp/data-access/sql-server-databases).

<a id="MSIX" />

### <a name="msix-deployment"></a>MSIX-Bereitstellung

MSIX ist das Windows-app-Paket-Format, das bietet eine moderne Packaging-Erfahrung für alle Windows-apps. Das MSIX-Paketformat behält die Funktionalität der vorhandenen app-Pakete und Dateien zusätzlich zum Aktivieren von neuen, modernen paketerstellungs und -Features für Win32, WPF und Windows Forms-apps installieren.

MSIX ist eine Paketformat erstellt, um sicher, sicher und zuverlässig, basierend auf einer Kombination von MSI, AppX, App-V und ClickOnce Installation Technologien.

![MSIX-Symbol](images/MSIX-App-Package.ico)

Finden Sie unter [MSIX-Dokumentation](https://docs.microsoft.com/windows/msix/).

<a id="distribution" />

## <a name="security"></a>Sicherheit

Windows 10 bietet eine Suite von Sicherheitsfeatures für app-Entwickler zum Schutz der Identität der Benutzer, die Sicherheit von Unternehmensnetzwerken und auf Geräten gespeicherten Unternehmensdaten. Neue für Windows 10 ist Microsoft Passport, eine zwei-Faktor-Kennwort bereitstellen Alternative, auf die zugegriffen werden über eine PIN oder Windows Hello, die Sicherheit im Unternehmen und unterstützt Fingerabdrücken, gesichtserkennung, und-basierte iriserkennung.

| Thema | Beschreibung |
|-------|-------------|
| [Einführung in die Entwicklung sicherer Windows-Apps](https://msdn.microsoft.com/library/windows/apps/mt622741) | Dieser einführende Artikel erläutert verschiedene Windows-Sicherheitsfeatures, die auf verschiedenen Stufen verfügbar sind, d.h. Authentifizierung, In-Flight-Daten und At-Rest-Daten. Außerdem wird hier beschrieben, wie Sie diese Stufen in Ihren Apps integrieren können. Er umfasst eine Vielzahl an Themen und enthält in erster Linie weitere Informationen für App-Architekten zu den Windows-Features, die die Entwicklung von Universellen Windows-Plattform-Apps beschleunigen. |
| [Authentifizierung und Benutzeridentität](https://msdn.microsoft.com/library/windows/apps/mt270184) | UWP-Apps verfügen über verschiedene Optionen zur Benutzerauthentifizierung, die in diesem Artikel beschrieben werden. Für Unternehmen wird dringend das neue Microsoft Passport-Feature empfohlen. MicrosoftPassport ersetzt Kennwörter mit der sicheren zweistufigen Authentifizierung (Two-Factor Authentication, 2FA), indem vorhandene Anmeldeinformationen überprüft und gerätespezifische Anmeldeinformationen erstellt werden, die eine Benutzergeste (entweder Biometrie- oder PIN-basiert) schützen, und schafft so eine bequeme und sichere Umgebung. |
| [Kryptografie](https://msdn.microsoft.com/library/windows/apps/mt270191) | Der Abschnitt „Kryptografie“ bietet eine Übersicht über die für UWP-Apps verfügbaren Kryptografie-Features. Die Artikel reichen von einführenden exemplarischen Vorgehensweisen zum einfachen Verschlüsseln sensibler Daten bis hin zu erweiterten Themen, z.B. Bearbeiten von kryptografischen Schlüsseln und Arbeiten mit MACs, Hashes und Signaturen. |
| [Windows Information Protection (WIP)](wip-hub.md) | Dies ist ein Übersichtsthema mit umfassenden Informationen für Entwickler zum Zusammenhang zwischen der Windows Information Protection (WIP) und Dateien, Puffern, der Zwischenablage, dem Netzwerk, Hintergrundaufgaben und dem Schutz von Daten bei Sperre. |

## <a name="data-binding-and-databases"></a>Datenbindung und Datenbanken

Die Datenbindung ist eine Methode, mit der die Benutzeroberfläche Ihrer App Daten aus externen Quellen wie Datenbanken anzeigen und diese Daten optional synchronisieren kann. Mit der Datenbindung können Sie Datenaspekte von Benutzeroberflächenaspekten trennen, was zu einem einfacheren konzeptionellen Modell und besserer Lesbarkeit, Testbarkeit und Wartung Ihrer App führt.

| Thema | Beschreibung |
|-------|-------------|
| [Übersicht über Datenbindung](https://msdn.microsoft.com/library/windows/apps/mt269383) | In diesem Thema erfahren Sie, wie Sie in einer UWP-App (Universelle Windows-Plattform) ein Steuerelement (oder ein anderes Benutzeroberflächenelement) an ein einzelnes Element oder ein Elementsteuerelement an eine Sammlung von Elementen binden. Darüber hinaus wird erläutert, wie Sie die Anzeige von Elementen steuern, eine Detailansicht auf Grundlage einer Auswahl implementieren und Daten für die Anzeige umwandeln. |
| [Entity Framework 7 für UWP](https://msdn.microsoft.com/library/windows/apps/mt592863) | Das Durchführen komplexer Abfragen für große Datensätze ist mit Entity Framework 7, mit Unterstützung für UWP, wesentlich einfacher. In dieser exemplarischen Vorgehensweise wird eine UWP-App erstellt, die auf grundlegende Daten der lokalen SQLite-Datenbank mithilfe von Entity Framework zugreift. |
| [Lokale SQLite-Datenbank](https://channel9.msdn.com/Series/A-Developers-Guide-to-Windows-10/10) | Dieses Video enthält ein umfassendes Entwicklerhandbuch zur Verwendung von SQLite, der empfohlenen Lösung für lokale App-Datenbanken. Laden Sie die neueste Version für UWP unter [SQLite](https://www.sqlite.org/download.html) herunter oder verwenden Sie die Version, die im Lieferumfang des Windows 10 SDK enthalten ist. |

## <a name="networking-and-data-serialization"></a>Netzwerke und Datenserialisierung

Branchenspezifische Apps müssen häufig mit Daten auf einer Vielzahl von anderen Systemen kommunizieren oder diese speichern. Dies erfolgt i. d. R. durch Herstellen einer Verbindung mit einem Netzwerkdienst (mithilfe von Protokollen wie REST oder SOAP) und durch anschließendes Serialisieren bzw. Deserialisieren von Daten in ein gemeinsames Format. Die Arbeit mit Netzwerken und die Datenserialisierung in UWP-Apps sind mit WPF-, WinForms- und ASP.NET-Anwendungen vergleichbar. Weitere Informationen finden Sie in den folgenden Artikeln.

| Thema | Beschreibung |
|-------|-------------|
| [Grundlagen zum Netzwerk](https://msdn.microsoft.com/library/windows/apps/mt280233) | In dieser exemplarischen Vorgehensweise werden grundlegende, für alle UWP-Apps relevante Netzwerkkonzepte erläutert, unabhängig von den verwendeten Kommunikationsprotokollen.  |
| [Welche Netzwerktechnologie?](https://msdn.microsoft.com/library/windows/apps/mt280235) | Eine kurze Übersicht über die Netzwerktechnologien, die für UWP-Apps zur Verfügung stehen, mit Vorschlägen zum Auswählen der Technologien, die für Ihre App am besten geeignet sind. |
| [XML- und SOAP-Serialisierung](https://msdn.microsoft.com/library/90c86ass.aspx) | Bei der XML-Serialisierung werden Objekte in einen XML-Datenstrom konvertiert, der einer bestimmten Sprache der XML-Schemadefinition (XSD) entspricht. Sie können zum Konvertieren zwischen XML und einer stark typisierten Klasse die systemeigene [XDocument](https://msdn.microsoft.com/library/system.xml.linq.xdocument.aspx)-Klasse oder eine externe Bibliothek verwenden. |
| [JSON-Serialisierung](https://msdn.microsoft.com/library/windows/apps/br240639) | Die JSON-Serialisierung (JavaScript Object Notation) ist ein gängiges Format für die Kommunikation mit REST-APIs. [JSON.NET von Newtonsoft](http://www.newtonsoft.com/json) wird vollständig für UWP-Apps unterstützt. |

## <a name="devices"></a>Geräte

Für die Integration in branchenspezifischen Tools, z. B. Drucker, Strichcodescanner oder Smartcardleser, ist es möglicherweise erforderlich, externe Geräte oder Sensoren in Ihrer App zu integrieren. Hier folgen einige Beispiele zu Features, die Sie mithilfe der in diesem Abschnitt beschriebenen Technologie zur App hinzufügen können.

| Thema  | Beschreibung |
|--------|-------------|
| [Auflisten von Geräten](https://msdn.microsoft.com/library/windows/apps/mt187355) | In diesem Artikel wird erläutert, wie mit dem [Windows.Devices.Enumeration](https://msdn.microsoft.com/library/windows/apps/br225459)-Namespace nach Geräten gesucht werden kann, die intern mit dem System verbunden, extern verbunden oder über Drahtlos- oder Netzwerkprotokolle entdeckt werden können. Beginnen Sie mit diesem Artikel, wenn Sie eine App erstellen, die mit Geräten arbeitet. |
| [Drucken und Scannen](https://msdn.microsoft.com/library/windows/apps/mt204544) | Beschreibt das Drucken und Scannen von Ihrer App aus, z. B. Herstellen einer Verbindung und Arbeiten mit Unternehmensgeräten wie POS-Systemen (Point-of-Sale), Belegdruckern und Einzugsscannern mit hoher Kapazität. |
| [Bluetooth](https://msdn.microsoft.com/library/windows/apps/mt270288) | Neben herkömmlichen Bluetooth-Verbindungen zum Senden und Empfangen von Daten oder Steuern von Geräten kann unter Windows 10 Bluetooth Low Energy (BTLE) zum Senden oder Empfangen von Beacons im Hintergrund verwendet werden. Verwenden Sie diese zum Anzeigen von Benachrichtigungen oder Aktivieren von Funktionen, wenn sich ein Benutzer in der Nähe eines bestimmten Orts befindet oder diesen verlässt. |
| [Im Unternehmen freigegebener Speicher](enterprise-shared-storage.md) | Erfahren Sie, wie Daten in Gerätesperrszenarien innerhalb derselben App zwischen App-Instanzen oder zwischen Apps freigegeben werden können. |

## <a name="device-targeting"></a>Ausrichten an Geräte

Viele Benutzer bringen in der heutigen Zeit ihre eigenen Telefone oder Tablets zur Arbeit mit, die unterschiedliche Formfaktoren und Bildschirmgrößen aufweisen. Mit der Universellen Windows-Plattform (UWP) können Sie branchenspezifische Apps entwickeln, die problemlos auf allen Arten von Geräten ausgeführt werden können, u.a. Desktop-PCs und PPI-Displays, und können so die Reichweite Ihrer Apps und die Effizienz des Codes maximieren.

| Thema | Beschreibung |
|-------|-------------|
| [Anleitung für UWP-Apps](https://msdn.microsoft.com/library/windows/apps/dn894631) | In dieser Anleitung können Sie sich mit der UWP-Plattform unter Windows10 vertraut machen. Sie erhalten u. a. Informationen dazu, was eine Gerätefamilie ist, wie Sie entscheiden, auf welche Ihre Apps abzielen sollen, Informationen zu neuen UI-Steuerelementen und Bereichen, mit denen Sie Ihre Benutzeroberfläche für verschiedene Geräte-Formfaktoren anpassen können, sowie zur für Ihre App verfügbaren API-Oberfläche und wie Sie diese steuern können. |
| [Adaptives XAML-UI-Codebeispiel](http://go.microsoft.com/fwlink/p/?LinkId=619992) | Dieses Codebeispiel zeigt die möglichen Layoutoptionen und Steuerelemente für Ihre App, unabhängig von der Art des Geräts, und veranschaulicht eine Interaktion mit den Bereichen, um das gewünschte Layout zu erzielen. Neben der Reaktion der Steuerelemente und der App selbst auf verschiedene Formfaktoren, werden die verschiedenen Methoden zum Erzielen einer adaptiven Benutzeroberfläche aufgezeigt. |
| [Xamarin-Thema]() | Xamarin für die Auswahl der phone |

## <a name="deployment"></a>Bereitstellung

Es stehen verschiedene Optionen für die Verteilung von Apps für die Benutzer in Ihrer Organisation zur Verfügung. Sie können Microsoft Store für Unternehmen, die vorhandene mobile geräteverwaltung oder können Sie apps auf Geräte querladen. Sie können auch Ihre apps auf der allgemeinen öffentlichen durch die Veröffentlichung im Microsoft Store zur Verfügung.

| Thema | Beschreibung |
|-------|-------------|
| [Verteilen von branchenspezifischen Apps an Unternehmen](https://msdn.microsoft.com/library/windows/apps/mt608995) | Sie können Branchen-apps direkt für Unternehmen Volumenlizenzen über den Microsoft Store für Unternehmen veröffentlichen, ohne die apps Allgemein zur Verfügung für der Öffentlichkeit. |
| [Querladen von Apps](https://technet.microsoft.com/library/mt269549) | Wenn Sie eine App querladen, stellen Sie ein signiertes App-Paket auf einem Gerät bereit. Das Signieren, Hosten und Bereitstellen dieser Apps wird beibehalten. Der Prozess zum Querladen von Apps ist für Windows 10 optimiert.             |
| [Veröffentlichen von apps im Microsoft Store](https://dev.windows.com/publish) | Einheitliche Microsoft Store können Sie alle Ihre Apps für alle Windows-Geräte verwalten und veröffentlichen. Passen Sie die Verfügbarkeit Ihrer App mit marktspezifischen Preisen, Steuerelementen für Verteilung und Sichtbarkeit und weiteren Optionen an. |

## <a name="enterprise-uwp-samples"></a>Enterprise-UWP-Beispiele

| Thema |  Beschreibung |
|------ |--------------|
| [VanArsdel Inventar-Beispiel](https://github.com/Microsoft/InventorySample) | Eine UWP-Beispiel-app, die Line-of-Business-Szenarien werden. Das Beispiel rund erstellen und Verwalten von Kunden, Aufträge und Produkte für die fiktive Firma VanArsdel. |
| [Beispieldatenbank Kundenbestellung](https://github.com/Microsoft/Windows-appsample-customers-orders-database) | Eine UWP-Beispiel-app, die an, wie die Azure Active Directory (AAD)-Authentifizierung, UI-Steuerelemente (inklusive des Datenrasters), Sqlite und Azure SQL-Datenbank-Integration, Entity Framework und API-Clouddienste nützliche Funktionen werden. Das Beispiel rund erstellen und Verwalten von Kundenkonten, Aufträge und Produkte für die fiktive Unternehmen Contoso. |

## <a name="patterns-and-practices"></a>Muster und Methoden

Eine Codebasis für umfangreiche Apps im Unternehmen kann schwer zu handhaben sein. Prism ist ein Framework zum Erstellen von lose gekoppelter, verwaltbaren und getestet werden XAML-Anwendungen in WPF, Windows 10 UWP und in Xamarin Forms. Prism stellt eine Implementierung einer Sammlung von Entwurfsmustern bereit, die beim Schreiben von gut strukturierten und verwaltbaren XAML-Anwendungen hilfreich sind, u.a. MVVM, Einfügen von Abhängigkeiten, Befehle und EventAggregator.

Weitere Informationen zu Prism finden Sie im [GitHub-Repository](https://github.com/PrismLibrary/Prism).

 

 
