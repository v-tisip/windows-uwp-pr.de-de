---
author: normesta
Description: Enhance your desktop application for Windows 10 users by using Universal Windows Platform (UWP) APIs.
Search.Product: eADQiWindows 10XVcnh
title: Verbessern Ihrer Desktopanwendung für Windows10
ms.author: normesta
ms.date: 08/12/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 392f8166e16c028a57bc9e27039a9884f1d9714a
ms.sourcegitcommit: e16c9845b52d5bd43fc02bbe92296a9682d96926
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "4948719"
---
# <a name="enhance-your-desktop-application-for-windows-10"></a>Verbessern Sie Ihre Desktopanwendung für Windows10

Sie können UWP-APIs verwenden, um moderner Funktionen für Windows10-Benutzer hinzuzufügen.

Richten Sie zuerst Ihr Projekt ein. Dann fügen Sie Windows10-Funktionen hinzu. Sie können separate Builds für Windows10-Benutzer erstellen oder die gleichen Binärdateien für alle Benutzer verteilen – unabhängig davon, welche Version von Windows sie ausführen.

## <a name="first-set-up-your-project"></a>Einrichten Ihres Projekts

Sie müssen einige Änderungen am Projekt vornehmen, um UWP-APIs zu verwenden.

### <a name="modify-a-net-project-to-use-uwp-apis"></a>Ändern eines .NET-Projekts für UWP-APIs

Öffnen Sie das **Verweis-Manager**-Dialogfeld, wählen Sie die **Durchsuchen**-Schaltfläche, und wählen Sie dann **Alle Dateien** aus.

![Dialogfeld „Verweis hinzufügen“](images/desktop-to-uwp/browse-references.png)

Fügen Sie dann einen Verweis auf diese Dateien hinzu.

|Datei|Speicherort|
|--|--|
|System.Runtime.WindowsRuntime|C:\Program Files (x86)\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5|
|System.Runtime.WindowsRuntime.UI.Xaml|C:\Program Files (x86)\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5|
|System.Runtime.InteropServices.WindowsRuntime|C:\Program Files (x86)\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5|
|Windows.winmd|C:\Program Files (x86)\Windows Kits\10\UnionMetadata\Facade|
|Windows.Foundation.UniversalApiContract.winmd|C:\Program Files (x86)\Windows Kits\10\References\<*sdk version*>\Windows.Foundation.UniversalApiContract\<*version*>|
|Windows.Foundation.FoundationContract.winmd|C:\Program Files (x86)\Windows Kits\10\References\<*sdk version*>\Windows.Foundation.FoundationContract\<*version*>|

Legen Sie im Dialogfeld **Eigenschaften** die **lokale Kopie** jeder *winmd*-Datei auf **Falsch** fest.

![„Lokal kopieren“-Feld](images/desktop-to-uwp/copy-local-field.png)

### <a name="modify-a-c-project-to-use-uwp-apis"></a>Ändern eines C++ Projekts für UWP-APIs

Öffnen Sie die Eigenschaftenseiten des Projekts.

Legen Sie in den **Allgemeinen** Einstellungen der **C/C++** Einstellungsgruppe das Feld **Windows-Runtime-Erweiterung verwenden** auf **Ja(/ZW)** fest.

   ![Windows-Runtime-Erweiterung verwenden](images/desktop-to-uwp/consume-runtime-extensions.png)

Öffnen Sie das Dialogfeld **Zusätzliche #using-Verzeichnisse**, und fügen Sie diese Verzeichnisse hinzu.

* %VSInstallDir%\Common7\IDE\VC\vcpackages
* C:\Programme (x86)\Windows Kits\10\UnionMetadata
* C:\Program Files (x86)\Windows Kits\10\References\Windows.Foundation.UniversalApiContract\<*latest version*>
* C:\Program Files (x86)\Windows Kits\10\References\Windows.Foundation.FoundationContract\<*latest version*>

Öffnen Sie das Dialogfeld **Additional Include Directories**, und fügen Sie dieses Verzeichnis hinzu: C:\Program Files (x86)\Windows Kits\10\Include\<*latest version*>\um

![Zusätzliche Include-Verzeichnisse](images/desktop-to-uwp/additional-include.png)

In den **Codegenerierung**-Einstellungen der **C/C++** Einstellungsgruppe legen die **Minimales Neuerstellen aktivieren** auf **Nein(/GM)** fest.

![Minimales Neuerstellen aktivieren](images/desktop-to-uwp/disable-min-build.png)


## <a name="add-windows-10-experiences"></a>Windows10-Funktionen hinzufügen

Jetzt können Sie moderner Funktionen für Benutzer der Anwendung unter Windows10 Hinzufügen. Verwenden Sie diesen Designfluss.

:white_check_mark: **Entscheiden Sie zunächst, welche Funktionen Sie hinzufügen möchten**

Es gibt viele zur Auswahl. Beispielsweise können Sie Ihre Bestellung Reihenfolge Fluss mithilfe von monetisierungs-APIs oder mehr Aufmerksamkeit für Ihre Anwendung bei interessante, z. B. ein neues Bild mit Teilen kaufablauf vereinfachen.

![Popup](images/desktop-to-uwp/toast.png)

Auch dann, wenn Benutzer Ihre Nachricht ignorieren oder schließen, können sie diese im Info-Center anzeigen und dann auf die Nachricht klicken, um Ihre App zu öffnen. Dies erhöht die Interaktion mit Ihrer Anwendung und hat den zusätzlichen Vorteil, Ihre Anwendung tief in das Betriebssystem integrieren. Wir zeigen Ihnen den Code für diese Funktion weiter unten.

Besuchen Sie unsere [Developer Center](https://developer.microsoft.com/windows) mit weiteren Ideen.

:white_check_mark: **Entscheiden Sie, ob Sie die App verbessern oder erweitern möchten**

Wir verwenden häufig die Begriffe „verbessern“ und „Erweitern“. Daher möchten wir erklären, was diese Begriffe bedeuten.

Wir verwenden den Begriff „Verbessern“ für UWP-APIs, die Sie direkt aus Ihrer Desktopanwendung aufrufen können. Wenn Sie eine Windows10-Funktion ausgewählt haben, identifizieren Sie die APIs, die Sie benötigen, um sie zu erstellen. Überprüfen Sie dann, ob die API in dieser [Liste](desktop-to-uwp-supported-api.md) aufgeführt wird. Hierbei handelt es sich um eine Liste der APIs, die Sie direkt aus Ihrer Desktopanwendung aufrufen können. Wenn Ihre API nicht in dieser Liste angezeigt wird, kann die Funktionalität der zugeordneten API nur in einem UWP-Prozess ausgeführt werden. Häufig sind dies APIs, die moderne Benutzeroberflächenelemente wie z.B. ein UWP-Karten-Steuerelement oder ein Windows Hello-Anmeldung nutzen.

Dies bedeutet, wenn Sie diese Funktionen in der Anwendung nutzen möchten, „erweitern“ sie einfach die Anwendung, indem Sie ein UWP-Projekt zur Projektmappe hinzufügen. Das Desktop-Projekt ist immer noch den Einstiegspunkt der Anwendung, aber das UWP-Projekt ermöglicht den Zugriff auf alle APIs, die nicht in dieser [Liste](desktop-to-uwp-supported-api.md) aufgeführt sind. Der Desktopanwendung kann mithilfe eines App-Dienstes mit dem UWP-Prozess kommunizieren. Wir stellen zahlreiche Anleitungen zum Einrichten dieser Kommunikation bereit. Wenn Sie eine Umgebung hinzufügen möchten, die ein UWP-Projekt erfordert finden Sie unter [Erweitern mit UWP](desktop-to-uwp-extend.md) weitere Informationen.

:white_check_mark: **Referenz-API-Verträge**

Wenn Sie die API direkt aus Ihrer Desktopanwendung aufrufen können, öffnen Sie einen Browser und suchen Sie nach dem Referenzthema für diese API.
Unterhalb der Zusammenfassung der API finden Sie eine Tabelle, die die API-Vertrag für diese API beschreibt. Dies ist ein Beispiel.

![API-Vertrag-Tabelle](images/desktop-to-uwp/contract-table.png)

Wenn Sie eine .NET-basierte Desktop-App haben, fügen Sie einen Verweis auf den API-Vertrag hinzu und legen Sie die **Lokale Kopie** Eigenschaft dieser Datei auf **Falsch** fest. Wenn Sie ein C++-basiertes Projekt haben, fügen Sie **Zusätzliche Include-Verzeichnisse** einen Pfad zu dem Ordner hinzu, der diesen Vertrag enthält.

:white_check_mark: **Aufrufen der APIs, um die Funktion hinzuzufügen**

Dies ist der Code, den Sie verwenden würden, um dem Benachrichtigungsfenster anzuzeigen, dass wir weiter oben behandelt haben. Diese APIs werden in dieser [Liste](desktop-to-uwp-supported-api.md) aufgeführt. Sie können diesen Code sofort in Ihrer Desktopanwendung nutzen.

```csharp
using Windows.Foundation;
using Windows.System;
using Windows.UI.Notifications;
using Windows.Data.Xml.Dom;
...

private void ShowToast()
{
    string title = "featured picture of the day";
    string content = "beautiful scenery";
    string image = "https://picsum.photos/360/180?image=104";
    string logo = "https://picsum.photos/64?image=883";

    string xmlString =
    $@"<toast><visual>
       <binding template='ToastGeneric'>
       <text>{title}</text>
       <text>{content}</text>
       <image src='{image}'/>
       <image src='{logo}' placement='appLogoOverride' hint-crop='circle'/>
       </binding>
      </visual></toast>";

    XmlDocument toastXml = new XmlDocument();
    toastXml.LoadXml(xmlString);

    ToastNotification toast = new ToastNotification(toastXml);

    ToastNotificationManager.CreateToastNotifier().Show(toast);
}
```

```C++
using namespace Windows::Foundation;
using namespace Windows::System;
using namespace Windows::UI::Notifications;
using namespace Windows::Data::Xml::Dom;

void UWP::ShowToast()
{
    Platform::String ^title = "featured picture of the day";
    Platform::String ^content = "beautiful scenery";
    Platform::String ^image = "https://picsum.photos/360/180?image=104";
    Platform::String ^logo = "https://picsum.photos/64?image=883";

    Platform::String ^xmlString =
        L"<toast><visual><binding template='ToastGeneric'>" +
        L"<text>" + title + "</text>" +
        L"<text>"+ content + "</text>" +
        L"<image src='" + image + "'/>" +
        L"<image src='" + logo + "'" +
        L" placement='appLogoOverride' hint-crop='circle'/>" +
        L"</binding></visual></toast>";

    XmlDocument ^toastXml = ref new XmlDocument();

    toastXml->LoadXml(xmlString);

    ToastNotificationManager::CreateToastNotifier()->Show(ref new ToastNotification(toastXml));
}
```
Weitere Informationen zu Benachrichtigungen finden Sie unter [Adaptive und interaktive Popupbenachrichtigungen](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/adaptive-interactive-toasts).

## <a name="support-windows-xp-windows-vista-and-windows-78-install-bases"></a>Unterstützung der Windows XP-, Windows Vista- und Windows7/8-Installationsbasis

Sie können Ihre Anwendung für Windows 10 modernisieren, ohne dass eine neue Verzweigung zu erstellen und eine separate Codebasis verwalten zu müssen.

Wenn Sie separate Binärdateien für Windows10-Benutzer erstellen möchten, verwenden Sie die bedingten Kompilierung. Wenn Sie einen Satz von Binärdateien für alle Windows-Benutzer erstellen möchten, verwenden Sie Laufzeitprüfungen.

Schauen wir uns die Optionen an.

### <a name="conditional-compilation"></a>Bedingte Kompilierung

Sie können eine Codebasis beibehalten und einen Satz Binärdateien nur für Windows10-Benutzer kompilieren.

Fügen Sie Ihrem Projekt zuerst eine neue Buildkonfiguration hinzu.

![Buildkonfiguration](images/desktop-to-uwp/build-config.png)

Erstellen Sie für diese Buildkonfiguration eine Konstante, um den Code zu identifizieren, der UWP-APIs aufruft.  

Für .NET-basierte Projekte heißt die Konstante **Bedingte Kompilierungskonstante**.

![Preprozessor](images/desktop-to-uwp/compilation-constants.png)

Für C++ basierte Projekte heißt die Konstante **Preprozessordefinition**.

![Preprozessor](images/desktop-to-uwp/pre-processor.png)

Fügen Sie die Konstanten vor jedem UWP-Codeblock hinzu.

```csharp

[System.Diagnostics.Conditional("_UWP")]
private void ShowToast()
{
 ...
}

```

```C++

#if _UWP
void UWP::ShowToast()
{
 ...
}
#endif

```

Der Compiler erstellt den Code nur dann, wenn die Konstante in der aktiven Buildkonfiguration definiert ist.

### <a name="runtime-checks"></a>Laufzeitprüfungen

Sie können einen Satz von Binärdateien für alle Windows-Benutzer kompilieren, unabhängig davon, welche Version von Windows sie ausführen. Ihre Anwendung ruft UWP-APIs nur dann, wenn der Benutzer Ihre Anwendung als verpackten Anwendung für Windows 10 ausgeführt.

Die einfachste Methode zum Hinzufügen von Laufzeitprüfungen zum Code ist die Installation des Nuget-Pakets [Desktop Bridge Helpers](https://www.nuget.org/packages/DesktopBridge.Helpers/) und die Verwendung der ``IsRunningAsUWP()``-Methode, um den ganzen UWP-Code abzugrenzen. Weitere Detail finden Sie in diesem Blogbeitrag: [Desktop-Brücke - Identifizieren des Anwendungskontexts](https://blogs.msdn.microsoft.com/appconsult/2016/11/03/desktop-bridge-identify-the-applications-context/).

## <a name="related-video"></a>Verwandte Videos

<iframe src="https://mva.microsoft.com/en-US/training-courses-embed/developers-guide-to-the-desktop-bridge-17373/Demo-Use-UWP-APIs-in-Your-Code-3d78c6WhD_9506218965" width="636" height="480" allowFullScreen frameBorder="0"></iframe>

## <a name="related-samples"></a>Verwandte Beispiele

* [„Hello world“-Beispiel](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/HelloWorldSample)
* [Sekundäre Kachel](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/SecondaryTileSample)
* [Store-API-Beispiel](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/StoreSample)
* [WinForms-Anwendung, die eine UWP-UpdateTask implementiert.](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/WinFormsUpdateTaskSample)
* [Beispiele für Desktop-App-Brücke zu UWP](https://github.com/Microsoft/DesktopBridgeToUWP-Samples)


## <a name="support-and-feedback"></a>Support und Feedback

**Finden Sie Antworten auf Ihre Fragen**

Haben Sie Fragen? Fragen Sie uns auf Stack Overflow. Unser Team überwacht diese [Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge). Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).

**Geben Sie Feedback oder Verbesserungsvorschläge**

Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).
