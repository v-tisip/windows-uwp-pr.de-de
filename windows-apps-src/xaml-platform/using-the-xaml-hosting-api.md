---
author: mcleanbyron
description: Dieser Artikel beschreibt die UWP XAML-Benutzeroberfläche in desktop-Anwendung hosten.
title: Mithilfe von UWP XAML hosting-API in einer desktop-Anwendung
ms.author: mcleans
ms.date: 09/21/2018
ms.topic: article
keywords: Windows 10 Uwp Windows Forms, Wpf, win32
ms.localizationpriority: medium
ms.openlocfilehash: 2ba64e32a25feaee9245bbfe2b598c756b29df98
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "5919698"
---
# <a name="using-the-uwp-xaml-hosting-api-in-a-desktop-application"></a>Mithilfe von UWP XAML hosting-API in einer desktop-Anwendung

> [!NOTE]
> UWP XAML hosting-API ist derzeit als Entwicklervorschau. Zwar wir Ihnen empfehlen, diese API in Ihrem eigenen Code Prototyp jetzt ausprobieren, empfohlen nicht, im Produktionscode zu diesem Zeitpunkt verwenden. Diese API wird fortgesetzt und Stabilisierung in zukünftigen Windows-Versionen. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.

Windows 10 Insider Vorschau SDK ab build 17709, nicht UWP desktop Applications (einschließlich WPF und Windows Forms mit C++ Win32-Anwendung) können *UWP XAML-hosting-API* , UWP-Hoststeuerelemente in jedes Benutzeroberflächenelement einen Fenster-Handle (zugeordnet ist HWND). Diese API ermöglicht nicht UWP desktop-Anwendung die neuesten Windows 10 UI-Funktionen verwenden, die nur über UWP-Steuerelemente verfügbar sind. Beispielsweise können nicht UWP desktop-Anwendung diese API UWP Hoststeuerelemente, die [Fließend Design System](../design/fluent-design-system/index.md) und [Windows Freihandeingaben](../design/input/pen-and-stylus-interactions.md)unterstützen.

UWP XAML hosting-API bildet die Grundlage für einer größeren Gruppe von Steuerelementen, die wir bereitstellen, um Entwickler zu Fluent-Benutzeroberfläche nicht UWP desktop-Anwendung. Dieses Szenario wird *XAML-Inseln*bezeichnet. Weitere Informationen zu diesem Szenario Developer finden Sie unter [UWP Steuerelemente in desktop-Anwendung](xaml-host-controls.md).

## <a name="is-the-uwp-xaml-hosting-api-right-for-your-desktop-application"></a>Ist das XAML UWP API für desktop-Anwendung hosten?

UWP XAML hosting-API bietet einfache Infrastruktur für UWP Steuerelemente in desktop-Anwendung hosten. Einige desktop Anwendungstypen können mit alternativen einfacher APIs zum Erreichen dieses Ziels.  

* Wenn Sie eine C++ Win32-desktop-Anwendung und UWP Steuerelemente in Ihrer Anwendung wollen, müssen Sie UWP XAML hosting-API verwenden. Es gibt keine alternativen für diese Anwendungstypen.

* Für WPF und Windows Forms empfiehlt [umschlossenen Steuerelemente](xaml-host-controls.md#wrapped-controls) und [Hoststeuerelemente](xaml-host-controls.md#host-controls) in den Windows Community statt UWP XAML verwenden hosting-API. Diese Steuerelemente verwenden UWP XAML intern hosting-API und eine einfachere Entwicklung. Sie können jedoch UWP XAML-hosting-API direkt in diese Anwendungstypen Wunsch.

## <a name="related-samples"></a>Verwandte Beispiele

UWP XAML hosting-API im Code verwendet hängt von Ihrem Anwendungstyp, den Entwurf der Anwendung und anderen Faktoren ab. Zur Veranschaulichung der Verwendung dieser API im Kontext eines vollständigen Antrags bezieht sich dieser Artikel Code in den folgenden Beispielen.

### <a name="c-win32"></a>C++ Win32

Es gibt mehrere Beispiele auf GitHub wie die hosting-API in C++ Win32-Anwendung UWP XAML verwendet werden:

  * [XamlHostingSample](https://github.com/Microsoft/Windows-appsample-Xaml-Hosting). Dieses Beispiel veranschaulicht, wie ein C++ Win32-Anwendung UWP [InkCanvas](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas), [InkToolbar](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar)und [MediaPlayerElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.mediaplayerelement) -Steuerelemente hinzu.
  * [XamlIslands32](https://github.com/clarkezone/cppwinrt/tree/master/Desktop/XamlIslandsWin32). Dieses Beispiel veranschaulicht, wie ein C++ Win32-Anwendung mehrere grundlegende UWP Steuerelemente hinzufügen und DPI ändern.

### <a name="wpf-and-windows-forms"></a>WPF und Windows Forms

[WindowsXamlHost](https://docs.microsoft.com/windows/communitytoolkit/controls/wpf-winforms/windowsxamlhost) -Steuerelement in den Windows Community fungiert als einer Referenzprobe Dank UWP hosting-API in WPF und Windows Forms. Der Quellcode ist an folgenden Orten verfügbar:

  * Die WPF-Version des Steuerelements [hier](https://github.com/Microsoft/WindowsCommunityToolkit/tree/master/Microsoft.Toolkit.Win32/Microsoft.Toolkit.Wpf.UI.XamlHost). Die WPF-Version von [**System.Windows.Interop.HwndHost**](https://docs.microsoft.com/dotnet/api/system.windows.interop.hwndhost)abgeleitet.
  * Für die Windows Forms-Version des Steuerelements [hier](https://github.com/Microsoft/WindowsCommunityToolkit/tree/master/Microsoft.Toolkit.Win32/Microsoft.Toolkit.Forms.UI.XamlHost). Windows Forms-Version von [**System.Windows.Forms.Control**](https://docs.microsoft.com/dotnet/api/system.windows.forms.control)abgeleitet ist.

## <a name="prerequisites"></a>Voraussetzungen

UWP XAML hosting-API hat diese erforderlichen Komponenten.

* Windows 10 Insider Preview build 17709 (oder einen späteren Build) und die entsprechenden Insider Vorabversion des Windows SDK. Dies ist eine weiterentwickelte Funktion empfiehlt für optimale Ergebnisse des neuesten Builds.

* Um die hosting-API in der Desktop-Anwendung UWP XAML zu verwenden, müssen Sie das Projekt so konfigurieren Sie UWP APIs aufrufen können:

    * **C++ Win32:** Wir empfehlen Konfigurieren des Projekts verwenden [C + / WinRT](../cpp-and-winrt-apis/index.md). Herunterladen und Installieren der [C + / WinRT Visual Studio-Erweiterung (VSIX)](https://aka.ms/cppwinrt/vsix) von Visual Studio Marketplace und fügen die ```<CppWinRTEnabled>true</CppWinRTEnabled>``` -Eigenschaft als Beschreibung [hier](../cpp-and-winrt-apis/intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix)die VCXPROJ-Datei.

    * **Windows Forms und WPF:** [Gehen Sie wie folgt vor.](../porting/desktop-to-uwp-enhance.md)

## <a name="architecture-of-xaml-islands"></a>Architektur der XAML-Inseln

UWP XAML hosting-API umfasst [**DesktopWindowXamlSource**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting.desktopwindowxamlsource), [**WindowsXamlManager**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting.windowsxamlmanager)und andere verwandten Arten im [**Windows.UI.Xaml.Hosting**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting) -Namespace. Desktop-Anwendung können diese API UWP Steuerelemente und Tastatur Fokusnavigation in und aus dem Elemente weiterleiten. Desktop-Applikationen können auch Größe und position die UWP-Kontrollen.

Beim Erstellen einer XAML-Insel mit XAML hosting-API in einer desktop-Anwendung müssen Sie die folgende Hierarchie von Objekten:

* Auf der Basisebene ist das Element der Benutzeroberfläche der Anwendung XAML-Insel gehostet werden soll. Dieses Benutzeroberflächenelement müssen ein Fensterhandle (HWND). Benutzeroberflächenelemente in denen XAML-Insel hosten kann zählen [**System.Windows.Interop.HwndHost**](https://docs.microsoft.com/dotnet/api/system.windows.interop.hwndhost) für WPF Applications [**System.Windows.Forms.Control**](https://docs.microsoft.com/dotnet/api/system.windows.forms.control) für Windows Forms-Anwendung und ein [Fenster](https://docs.microsoft.com/windows/desktop/winmsg/about-windows) für C++ Win32-Anwendung.

* Die nächste ist Ebene ein **DesktopWindowXamlSource** -Objekt. Dieses Objekt stellt die Infrastruktur zum Hosten von XAML-Insel bereit. Der Code ist für dieses Objekt erstellen und Anfügen an das übergeordnete Element der Benutzeroberfläche verantwortlich.

* Beim Erstellen einer **DesktopWindowXamlSource**erstellt dieses Objekt automatisch eine systemeigene untergeordnete zum Hosten des Steuerelements UWP. Systemeigene untergeordneten Fensters wird hauptsächlich vom Code abstrahiert, jedoch das Handle (HWND) ggf. auf.

* Auf der obersten Ebene ist das UWP-Steuerelement in der Desktop-Anwendung hosten möchten. Dies ist ein UWP-Objekt, das aus [**Windows.UI.Xaml.UIElement**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement), einschließlich jedes UWP-Steuerelement von Windows SDK als auch benutzerdefinierte Steuerelemente bereitgestellt.

Die folgende Abbildung zeigt die Hierarchie der Objekte in einer XAML-Insel.

![DesktopWindowXamlSource-Architektur](images/xaml-hosting-api-rev2.png)

## <a name="how-to-host-uwp-xaml-controls"></a>UWP XAML-Steuerelemente hosten.

Hier werden die wichtigsten Schritte für die Verwendung von UWP XAML hosting-API ein UWP Steuerelement in Ihrer Anwendung gehostet.

1. UWP XAML-Framework für den aktuellen Thread zu initialisieren, bevor die Anwendung erstellt die [**Windows.UI.Xaml.UIElement**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement) -Objekte, die sie hosten in [**DesktopWindowXamlSource**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting.desktopwindowxamlsource).

    * Wenn die Anwendung das **DesktopWindowXamlSource** -Objekt erstellt, bevor sie **Windows.UI.Xaml.UIElement** Objekte erstellt, wird diesem Sie Initialisiert beim Instanziieren des **DesktopWindowXamlSource** -Objekts . In diesem Szenario müssen Sie eigenen Rahmen initialisieren Code hinzufügen.

    * Wenn die Anwendung Objekte **Windows.UI.Xaml.UIElement** erstellt, bevor das **DesktopWindowXamlSource** -Objekt erstellt, das sie hosten, muss die Anwendung die statische [**aufrufen WindowsXamlManager.InitializeForCurrentThread**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting.windowsxamlmanager.initializeforcurrentthread) Methode explizit UWP XAML-Framework initialisieren, bevor die **Windows.UI.Xaml.UIElement** Objekte instanziiert werden. Die Anwendung sollte in der Regel diese Methode aufrufen, bei der Instanziierung des übergeordneten UI-Elements, das die **DesktopWindowXamlSource** hostet.

    ```cppwinrt
    Windows::UI::Xaml::Hosting::WindowsXamlManager windowsXamlManager =
        Windows::UI::Xaml::Hosting::WindowsXamlManager::InitializeForCurrentThread();
    ```

    ```csharp
    global::Windows.UI.Xaml.Hosting.WindowsXamlManager windowsXamlManager =
        global::Windows.UI.Xaml.Hosting.WindowsXamlManager.InitializeForCurrentThread();
    ```

    > [!NOTE]
    > Diese Methode gibt ein [**WindowsXamlManager**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting.windowsxamlmanager) -Objekt, das einen Verweis auf die UWP XAML-Framework enthält. Sie können für einen bestimmten Thread soll **WindowsXamlManager** Objekte erstellen. Aber da jedes Objekt einen Verweis auf die UWP XAML-Framework enthält, sollten Sie freigeben Objekte um sicherzustellen, dass XAML-Ressourcen schließlich freigegeben werden.

2. Erstellen Sie ein [**DesktopWindowXamlSource**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting.desktopwindowxamlsource) -Objekt und an einen übergeordneten UI-Element in der Anwendung ein Fensterhandle zugeordnet ist.

    Dazu müssen Sie die folgenden Schritte:

    1. Ein **DesktopWindowXamlSource** -Objekt erstellen und in die **IDesktopWindowXamlSourceNative** COM-Schnittstelle umgewandelt. Diese Schnittstelle deklariert die ```windows.ui.xaml.hosting.desktopwindowxamlsource.h``` Headerdatei im Windows SDK. In C++ Win32-Projekt können Sie diese Header-Datei direkt verweisen. In einem WPF- oder Windows Forms-Projekt müssen Sie diese Schnittstelle im Anwendungscode mit dem [**ComImport**](https://docs.microsoft.com/dotnet/api/system.runtime.interopservices.comimportattribute) -Attribut deklarieren. Sicherstellen, dass die Schnittstellendeklaration exakt die Schnittstellendeklaration in ```windows.ui.xaml.hosting.desktopwindowxamlsource.h```.

    2. Rufen Sie die **AttachToWindow** -Methode der **IDesktopWindowXamlSourceNative** -Schnittstelle, und übergeben Sie das Fensterhandle des übergeordneten UI-Element in der Anwendung.

    3. Legen Sie die Anfangsgröße des internen untergeordneten Fensters in **DesktopWindowXamlSource**enthalten. Standardmäßig wird dieses internen untergeordneten Fensters auf eine Breite und Höhe von 0 festgelegt. Wenn Sie die Größe des Fensters festlegen, werden alle UWP-Steuerelemente hinzu **DesktopWindowXamlSource** nicht angezeigt. Verwenden Sie für den Zugriff auf das interne untergeordnete Fenster in **DesktopWindowXamlSource** **WindowHandle** -Eigenschaft der **IDesktopWindowXamlSourceNative** -Schnittstelle. Die folgenden Beispiele verwenden die Funktion [SetWindowPos](https://docs.microsoft.com/windows/desktop/api/winuser/nf-winuser-setwindowpos) der Größe des Fensters.

    Hier sind einige Codebeispiele, in denen dieser Prozess veranschaulicht wird.

    ```cppwinrt
    // This example assumes you already have an HWND variable named 'parentHwnd' that
    // contains the handle of the parent window.
    Windows::UI::Xaml::Hosting::DesktopWindowXamlSource desktopWindowXamlSource;
    auto interop = desktopWindowXamlSource.as<IDesktopWindowXamlSourceNative>();
    check_hresult(interop->AttachToWindow(parentHwnd));

    HWND childInteropHwnd = nullptr;
    interop->get_WindowHandle(&childInteropHwnd);

    SetWindowPos(childInteropHwnd, 0, 0, 0, 300, 300, SWP_SHOWWINDOW);
    ```

    ```csharp
    // This WPF example assumes you already have an HwndHost named 'parentHwndHost'
    // that will act as the parent UI elemnt for your XAML island. It also assumes
    // you have used the DllImport attribute to import SetWindowPos from user32.dll
    // as a static method into a class named NativeMethods.
    Windows.UI.Xaml.Hosting.DesktopWindowXamlSource desktopWindowXamlSource =
        new Windows.UI.Xaml.Hosting.DesktopWindowXamlSource();

    IntPtr iUnknownPtr = System.Runtime.InteropServices.Marshal.GetIUnknownForObject(
        desktopWindowXamlSource);
    IDesktopWindowXamlSourceNative desktopWindowXamlSourceNative =
        System.Runtime.InteropServices.Marshal.Marshal.GetTypedObjectForIUnknown(
            iUnknownPtr, typeof(IDesktopWindowXamlSourceNative))
            as IDesktopWindowXamlSourceNative;

    desktopWindowXamlSourceNative.AttachToWindow(parentHwndHost.Handle);

    var childInteropHwnd = desktopWindowXamlSourceNative.WindowHandle;
    NativeMethods.SetWindowPos(childInteropHwnd, HWND_TOP, 0, 0, 300, 300, SWP_SHOWWINDOW);
    ```

3. Legen Sie die **Windows.UI.Xaml.UIElement** zu hosten, die [**Content**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting.desktopwindowxamlsource.content) -Eigenschaft des **DesktopWindowXamlSource** -Objekts. Im folgenden Beispiel wird ein [**Windows.UI.Xaml.Controls.Grid**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.grid) mit dem Namen ```myGrid``` , die **Content** -Eigenschaft.

   ```cppwinrt
   desktopWindowXamlSource.Content(myGrid);
   ```

   ```csharp
   desktopWindowXamlSource.Content = myGrid;
   ```

Vollständige Beispiele für die diese Vorgänge im Kontext einer Beispiel-Anwendung arbeiten, finden Sie die folgenden Dateien:

  * **C++ Win32:** Finden Sie in der Datei ["Main.cpp"](https://github.com/Microsoft/Windows-appsample-Xaml-Hosting/blob/master/XamlHostingSample/Main.cpp) im Beispiel [XamlHostingSample](https://github.com/Microsoft/Windows-appsample-Xaml-Hosting) oder [Desktop.cpp](https://github.com/clarkezone/cppwinrt/blob/master/Desktop/XamlIslandsWin32/Desktop.cpp) -Datei im Beispiel [XamlIslands32](https://github.com/clarkezone/cppwinrt/tree/master/Desktop/XamlIslandsWin32) .
  * **WPF:** Die Dateien [WindowsXamlHostBase.cs](https://github.com/Microsoft/WindowsCommunityToolkit/blob/master/Microsoft.Toolkit.Win32/Microsoft.Toolkit.Wpf.UI.XamlHost/WindowsXamlHostBase.cs) und [WindowsXamlHost.cs](https://github.com/Microsoft/WindowsCommunityToolkit/blob/master/Microsoft.Toolkit.Win32/Microsoft.Toolkit.Wpf.UI.XamlHost/WindowsXamlHost.cs) in den Windows Community anzeigen  
  * **Windows Forms:** Die Dateien [WindowsXamlHostBase.cs](https://github.com/Microsoft/WindowsCommunityToolkit/blob/master/Microsoft.Toolkit.Win32/Microsoft.Toolkit.Forms.UI.XamlHost/WindowsXamlHostBase.cs) und [WindowsXamlHost.cs](https://github.com/Microsoft/WindowsCommunityToolkit/blob/master/Microsoft.Toolkit.Win32/Microsoft.Toolkit.Forms.UI.XamlHost/WindowsXamlHost.cs) in den Windows Community anzeigen


## <a name="how-to-host-custom-uwp-xaml-controls"></a>Wie Host benutzerdefinierte XAML UWP Steuerelemente

> [!IMPORTANT]
> Benutzerdefinierte Steuerelemente UWP XAML 3. Parteien sind derzeit nur in C# WPF und Windows Forms unterstützt. Benötigen Sie den Quellcode für die Steuerelemente so gegen Ihre Anwendung kompilieren können.

Wenn Sie ein benutzerdefiniertes UWP XAML-Steuerelement (ein Steuerelement, das Sie selbst definieren oder eine Kontrolle durch ein 3rd party) hosten möchten, führen Sie die folgenden zusätzlichen Aufgaben neben der im [vorherigen Abschnitt](#how-to-host-uwp-xaml-controls)beschrieben.

1. Definieren Sie einen benutzerdefinierten Typ, der von [**Windows.UI.Xaml.Application**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application) abgeleitet und setzt [**IXamlMetadataProvider**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.markup.ixamlmetadataprovider). Dieser Typ dient als einen Stamm Metadatenanbieter Metadaten für benutzerdefinierte UWP XAML-Typen in Assemblys im aktuellen Verzeichnis der Anwendung geladen.

    Ein Beispiel, das veranschaulicht, finden Sie in der Codedatei [XamlApplication.cs](https://github.com/Microsoft/WindowsCommunityToolkit/tree/master/Microsoft.Toolkit.Win32/Microsoft.Windows.Interop.WindowsXamlHost.Shared/XamlApplication.cs) in die Windows-Community-Toolkit. Diese Datei ist Teil der gemeinsamen Implementierung der **WindowsXamlHost** Klassen für WPF und Windows Forms, die verdeutlichen, wie die hosting-API in diesen Anwendungstypen UWP XAML.

2. Aufrufen die [**GetXamlType**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.markup.ixamlmetadataprovider.getxamltype) -Methode des Anbieters Metadaten Stamm bei der Typnamen UWP XAML-Steuerelement zugeordnet ist (Dies könnte Code zur Laufzeit zugewiesen werden oder können dies im Eigenschaftenfenster von Visual Studio zugewiesen werden).

    Ein Beispiel, das veranschaulicht, finden Sie in der Codedatei [UWPTypeFactory.cs](https://github.com/Microsoft/WindowsCommunityToolkit/tree/master/Microsoft.Toolkit.Win32/Microsoft.Windows.Interop.WindowsXamlHost.Shared/UWPTypeFactory.cs) in die Windows-Community-Toolkit. Diese Datei ist Teil der gemeinsamen Implementierung der **WindowsXamlHost** Klassen für WPF und Windows Forms.

3. Den Quellcode für das benutzerdefinierte Steuerelement UWP XAML in Ihre Anwendung Host Integration, erstellen Sie das benutzerdefinierte Steuerelement und folgenden [lernen](https://docs.microsoft.com/windows/communitytoolkit/controls/wpf-winforms/windowsxamlhost#add-a-custom-uwp-control)in der Anwendung verwenden.

## <a name="how-to-handle-keyboard-focus-navigation"></a>Umgang mit den Tastaturfokus

Wenn der Benutzer über die UI-Elemente in der Anwendung mithilfe der Tastatur (z. B. durch Drücken von **Tab** oder Pfeil Richtung), müssen Sie programmgesteuert Fokus in und aus dem **DesktopWindowXamlSource** -Objekt verschieben. Erreicht der Benutzer Tastaturnavigation der **DesktopWindowXamlSource**, verschieben den Fokus in das erste [**Windows.UI.Xaml.UIElement**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement) -Objekt in der Navigation die Benutzeroberfläche weiterhin Fokus auf folgende ** Windows.UI.Xaml.UIElement** Objekte wie Benutzer, durchläuft die Elemente und verschieben den Fokus aus der **DesktopWindowXamlSource** und das übergeordnete Element der Benutzeroberfläche.  

UWP XAML hosting-API bietet verschiedene Typen und Member dieser Aufgaben helfen.

1. Die Tastaturnavigation Ihre **DesktopWindowXamlSource**ein, das [**GotFocus**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting.desktopwindowxamlsource.gotfocus) -Ereignis ausgelöst. Behandeln Sie dieses Ereignis und programmgesteuert verschieben Sie des Fokus auf die erste gehostete **Windows.UI.Xaml.UIElement** mithilfe der [**NavigateFocus**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting.desktopwindowxamlsource.navigatefocus) -Methode.

2. Wenn der Benutzer auf das letzte fokussierbare Element in der **DesktopWindowXamlSource** und die **Tab** -Taste oder eine Pfeiltaste drückt, wird das [**TakeFocusRequested**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting.desktopwindowxamlsource.takefocusrequested) -Ereignis ausgelöst. Behandeln Sie dieses Ereignis und verschieben Sie den Fokus auf das nächste fokussierbare Element in der hostanwendung programmgesteuert. Beispielsweise in einer WPF-Anwendung, die **DesktopWindowXamlSource** in einem [**System.Windows.Interop.HwndHost**](https://docs.microsoft.com/dotnet/api/system.windows.interop.hwndhost)gehostet wird, können die [**MoveFocus**](https://docs.microsoft.com/dotnet/api/system.windows.frameworkelement.movefocus) -Methode Sie den Fokus auf das nächste fokussierbare Element in der hostanwendung übertragen.

Beispiele für die Verwendung im Kontext einer Beispiel-Anwendung arbeiten, finden Sie in den folgenden Dateien:
  * **WPF:** Finden Sie in den Windows Community [WindowsXamlHostBase.Focus.cs](https://github.com/Microsoft/WindowsCommunityToolkit/blob/master/Microsoft.Toolkit.Win32/Microsoft.Toolkit.Wpf.UI.XamlHost/WindowsXamlHostBase.Focus.cs) .  
  * **Windows Forms:** Finden Sie in den Windows Community [WindowsXamlHostBase.KeyboardFocus.cs](https://github.com/Microsoft/WindowsCommunityToolkit/blob/master/Microsoft.Toolkit.Win32/Microsoft.Toolkit.Forms.UI.XamlHost/WindowsXamlHostBase.KeyboardFocus.cs) .

## <a name="how-to-handle-layout-changes"></a>Layout Änderungen

Wenn der Benutzer die Größe des übergeordneten UI-Element ändert, müssen Sie behandeln layoutänderungen erforderlichen zu UWP Steuerelemente wie erwartet angezeigt. Hier sind einige wichtige Szenarios zu berücksichtigen.

1. Wenn das übergeordnete Element der Benutzeroberfläche muss die Größe eines rechteckigen Bereichs an auf **DesktopWindowXamlSource hosten** **Windows.UI.Xaml.UIElement** erforderlich, rufen Sie die [**Measure**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.measure) -Methode **Windows.UI.Xaml.UIElement **. Beispiel:
    * In einer WPF-Anwendung können Sie die [**MeasureOverride**](https://docs.microsoft.com/dotnet/api/system.windows.frameworkelement.measureoverride) -Methode [**HwndHost**](https://docs.microsoft.com/dotnet/api/system.windows.interop.hwndhost) dazu, die **DesktopWindowXamlSource**hostet.
    * In einer Windows Forms-Anwendung können Sie [**GetPreferredSize**](https://docs.microsoft.com/dotnet/api/system.windows.forms.control.getpreferredsize) -Methode des [**Steuerelements**](https://docs.microsoft.com/dotnet/api/system.windows.forms.control) dazu, die **DesktopWindowXamlSource**hostet.

2. Wenn die Größe des übergeordneten-Element ändert sich Aufrufen [**Arrange**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.arrange) -Methode des eigentlichen **Windows.UI.Xaml.UIElement** , hosten Sie auf **DesktopWindowXamlSource**. Beispiel:
    * In einer WPF-Anwendung können Sie die [**ArrangeOverride**](https://docs.microsoft.com/dotnet/api/system.windows.frameworkelement.arrangeoverride) -Methode des Objekts [**HwndHost**](https://docs.microsoft.com/dotnet/api/system.windows.interop.hwndhost) dazu, die **DesktopWindowXamlSource**hostet.
    * In einer Windows Forms-Anwendung können Sie Handler für das [**SizeChanged**](https://docs.microsoft.com/dotnet/api/system.windows.forms.control.sizechanged) -Ereignis des [**Steuerelements**](https://docs.microsoft.com/dotnet/api/system.windows.forms.control) hostet **DesktopWindowXamlSource**dazu.

Beispiele für die Verwendung im Kontext einer Beispiel-Anwendung arbeiten, finden Sie in den folgenden Dateien:
  * **WPF:** Finden Sie in den Windows Community [WindowsXamlHost.Layout.cs](https://github.com/Microsoft/WindowsCommunityToolkit/blob/master/Microsoft.Toolkit.Win32/Microsoft.Toolkit.Wpf.UI.XamlHost/WindowsXamlHostBase.Layout.cs) .  
  * **Windows Forms:** Finden Sie in den Windows Community [WindowsXamlHost.Layout.cs](https://github.com/Microsoft/WindowsCommunityToolkit/blob/master/Microsoft.Toolkit.Win32/Microsoft.Toolkit.Forms.UI.XamlHost/WindowsXamlHostBase.Layout.cs) .

## <a name="how-to-handle-dpi-changes"></a>DPI Änderungen

Wenn DPI ändert sich im Fenster hostet die UWP steuern (z. B. wenn der Benutzer das Fenster zwischen den Monitoren mit unterschiedlichen DPI zieht) behandelt werden soll, müssen Sie, konfigurieren Sie das UWP-Steuerelement mit einer Rendertransformation DPI Änderung Ihrer app überwachen , und aktualisiert die Position des Fensters und Transformation des Steuerelements UWP DPI Änderungen rendern.

Die folgenden Schritte veranschaulichen eine Möglichkeit, diesen Prozess im Kontext einer C++ Win32-Anwendung. Ein vollständiges Beispiel finden Sie in den Dateien [Desktop.cpp](https://github.com/clarkezone/cppwinrt/blob/master/Desktop/XamlIslandsWin32/Desktop.cpp) und [Desktop.h](https://github.com/clarkezone/cppwinrt/blob/master/Desktop/XamlIslandsWin32/Desktop.h) in die [XamlIslands32](https://github.com/clarkezone/cppwinrt/tree/master/Desktop/XamlIslandsWin32) Probe auf GitHub.

1. [**ScaleTransform**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.scaletransform) -Objekt in Ihrer Anwendung verwalten und [**RenderTransform**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.rendertransform) -Methode des Steuerelements UWP zuweisen. Im folgende Beispiel wird für ein [**Windows.UI.Xaml.Controls.Grid**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.grid) -Steuerelement in ein C++ Win32-Anwendung.

    ```cppwinrt
    // Private fields maintained by your app, such as in a window class you have defined.
    Windows::UI::Xaml::Media::ScaleTransform m_scale;
    Windows::UI::Xaml::Controls::Grid m_rootGrid;

    // Code that runs during initialization, such as the constructor for a window class you have defined.
    m_rootGrid.RenderTransform(m_scale);
    ```

2. Hören Sie die [**WindowProc**](https://msdn.microsoft.com/library/windows/desktop/ms633573.aspx) -Funktion für die [**WM_DPICHANGED**](https://docs.microsoft.com/windows/desktop/hidpi/wm-dpichanged) -Nachricht. Antwort auf diese Nachricht:
    * Funktion [**SetWindowPos**](https://docs.microsoft.com/windows/desktop/api/winuser/nf-winuser-setwindowpos) die Fenstergröße, die die UWP die Meldung übergebene Rechteck enthält.
    * Aktualisieren der x- und y-Achse Skalierungsfaktoren **ScaleTransform** -Objekt entsprechend der DPI-Wert.
    * Transaktionsattribute, die Darstellung und das Layout des Steuerelements UWP. Im folgenden Codebeispiel passt den [**Abstand**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.grid.padding) des gehosteten Steuerelements **Windows.UI.Xaml.Controls.Grid** DPI Änderungen.

    ```cppwinrt
    LRESULT HandleDpiChange(HWND hWnd, WPARAM wParam, LPARAM lParam)
    {
        HWND hWndStatic = GetWindow(hWnd, GW_CHILD);
        if (hWndStatic != nullptr)
        {
            UINT uDpi = HIWORD(wParam);

            // Resize the window
            auto lprcNewScale = reinterpret_cast<RECT*>(lParam);

            SetWindowPos(hWnd, nullptr, lprcNewScale->left, lprcNewScale->top,
                lprcNewScale->right - lprcNewScale->left, lprcNewScale->bottom - lprcNewScale->top,
                SWP_NOZORDER | SWP_NOACTIVATE);

            NewScale(uDpi);
          }
          return 0;
    }

    void NewScale(UINT dpi) {

        auto scaleFactor = (float)dpi / 100;

        if (m_scale != nullptr) {
            m_scale.ScaleX(scaleFactor);
            m_scale.ScaleY(scaleFactor);
        }

        ApplyCorrection(scaleFactor);
    }

    void ApplyCorrection(float scaleFactor) {
        float rightCorrection = (m_rootGrid.Width() * scaleFactor - m_rootGrid.Width()) / scaleFactor;
        float bottomCorrection = (m_rootGrid.Height() * scaleFactor - m_rootGrid.Height()) / scaleFactor;

        m_rootGrid.Padding(Windows::UI::Xaml::ThicknessHelper::FromLengths(0, 0, rightCorrection, bottomCorrection));
    }
    ```

2. Konfigurieren Sie Ihre Anwendung zu DPI pro Monitor eine [nebeneinander Assemblymanifest](https://docs.microsoft.com/windows/desktop/SbsCs/application-manifests) zur Projekt und ```<dpiAwareness>``` Element ```PerMonitorV2```. Weitere Informationen zu diesem Wert finden Sie unter der Beschreibung für [**DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2**](https://docs.microsoft.com/windows/desktop/hidpi/dpi-awareness-context).

    ```xml
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
        <application xmlns="urn:schemas-microsoft-com:asm.v3">
            <windowsSettings>
                <dpiAwareness xmlns="http://schemas.microsoft.com/SMI/2016/WindowsSettings">PerMonitorV2</dpiAwareness>
            </windowsSettings>
        </application>
    </assembly>
    ```

    Ein vollständiges Beispiel Side-by-Side Assemblymanifest finden Sie in der Datei [XamlIslandsWin32.exe.manifest](https://github.com/clarkezone/cppwinrt/blob/master/Desktop/XamlIslandsWin32/XamlIslandsWin32.exe.manifest) in die [XamlIslands32](https://github.com/clarkezone/cppwinrt/tree/master/Desktop/XamlIslandsWin32) Probe auf GitHub.

## <a name="limitations"></a>Einschränkungen

Die hosting-API XAML teilt die gleichen Grenzen als andere Typen von XAML-Steuerelemente für Windows 10. Eine detaillierte Liste finden Sie unter [XAML-Host Control eingeschränkt](xaml-host-controls.md#limitations).

## <a name="troubleshooting"></a>Fehlerbehebung

### <a name="error-using-uwp-xaml-hosting-api-in-a-uwp-app"></a>Fehler mit UWP XAML-hosting-API in einer Anwendung UWP

| Problem | Auflösung |
|-------|------------|
| Ihre Anwendung empfängt einen **COMException** mit der folgenden Meldung: "DesktopWindowXamlSource kann nicht aktiviert werden. Dieser Typ kann in einer UWP-app verwendet werden." oder "WindowsXamlManager kann nicht aktiviert werden. Dieser Typ kann in einer UWP-app verwendet werden." | Dieser Fehler gibt UWP XAML hosting-API verwenden möchten (insbesondere soll Instanziieren der Typen [**DesktopWindowXamlSource**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting.desktopwindowxamlsource) oder [**WindowsXamlManager**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting.windowsxamlmanager) ) in UWP app. UWP XAML hosting-API soll nur in Desktop-apps nicht UWP wie WPF und Windows Forms mit C++ Win32-Anwendung verwendet werden. |

### <a name="error-attaching-to-a-window-on-a-different-thread"></a>Fehler beim Anhängen an ein Fenster in einem anderen thread

| Problem | Auflösung |
|-------|------------|
| Ihre Anwendung empfängt einen **COMException** mit der folgenden Meldung: "AttachToWindow Methode fehlgeschlagen angegebene HWND in einem anderen Thread erstellt wurde." | Dieser Fehler weist darauf hin, dass die Anwendung die **IDesktopWindowXamlSourceNative.AttachToWindow** -Methode aufgerufen und übergeben HWND des Fensters, das in einem anderen Thread erstellt wurde. Sie müssen diese Methode das HWND des Fensters übergeben, die im gleichen Thread wie der Code erstellt wurde, aus dem Sie die Methode aufrufen. |

### <a name="error-attaching-to-a-window-on-a-different-top-level-window"></a>Fehler beim Anhängen an ein Fenster auf ein anderes Fenster der obersten Ebene

| Problem | Auflösung |
|-------|------------|
| Ihre Anwendung empfängt einen **COMException** mit der folgenden Meldung: "AttachToWindow Methode fehlgeschlagen angegebene HWND aus einem anderen Fenster der obersten Ebene als HWND steigt, die zuvor auf dem gleichen Thread an AttachToWindow übergeben wurde." | Dieser Fehler gibt an, dass die Anwendung die **IDesktopWindowXamlSourceNative.AttachToWindow** -Methode aufgerufen und HWND des Fensters, der aus einem anderen Fenster der obersten Ebene Fenster in einem vorherigen Aufruf dieser Methode angegebene übergeben auf dem gleichen Thread.</p></p>Nachdem die Anwendung **IDesktopWindowXamlSourceNative.AttachToWindow** für einen bestimmten Thread aufruft, können andere [**DesktopWindowXamlSource**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting.desktopwindowxamlsource) Objekte auf dem gleichen Thread nur Windows zuordnen, die Nachfolger von demselben Fenster auf oberster Ebene im ersten Aufruf an **IDesktopWindowXamlSourceNative.AttachToWindow**übergebene. Wenn die **DesktopWindowXamlSource** -Objekte für einen bestimmten Thread geschlossen sind, kann der nächste **DesktopWindowXamlSource** alle Fenster wieder an.</p></p>Schließen Sie zum Beheben dieses Problems entweder alle **DesktopWindowXamlSource** Objekte, die werden andere Fenster der obersten Ebene in diesem Thread gebunden oder erstellen einen neuen Thread für diesen **DesktopWindowXamlSource**. |

## <a name="related-topics"></a>Verwandte Themen

* [UWP-Steuerelemente in Desktopanwendungen](xaml-host-controls.md)
