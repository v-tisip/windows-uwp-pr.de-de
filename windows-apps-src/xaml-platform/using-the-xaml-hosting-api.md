---
author: mcleans
description: Dieser Artikel beschreibt, wie UWP-XAML-Benutzeroberfläche in Ihrer desktop-Anwendung gehostet wird.
title: Unter Verwendung des UWP-XAML hosting-API in einer desktop-Anwendung
ms.author: mcleans
ms.date: 09/21/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp, windows forms, wpf
keywords: Windows 10, Uwp, Windows Forms, Wpf, win32
ms.localizationpriority: medium
ms.openlocfilehash: 860e515d013046ef77d0aee38eb5d42c9c3e2dc9
ms.sourcegitcommit: e6daa7ff878f2f0c7015aca9787e7f2730abcfbf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2018
ms.locfileid: "4311008"
---
# <a name="using-the-uwp-xaml-hosting-api-in-a-desktop-application"></a>Unter Verwendung des UWP-XAML hosting-API in einer desktop-Anwendung

> [!NOTE]
> Die UWP-XAML hosting-API ist zurzeit als Entwicklervorschau verfügbar. Obwohl wir Sie diese API in Ihrem eigenen Code Prototyp jetzt testen dazu ermutigen, empfehlen wir nicht, mit denen Sie in Produktionscode zu diesem Zeitpunkt. Diese API weiterhin breiter und Stabilisierung in zukünftigen Windows-Versionen. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.

Windows 10 Insider Preview SDK ab build 17709, nicht-UWP-desktop-Apps (einschließlich WPF, Windows Forms und C++ Win32-Anwendungen) können Sie das *UWP-XAML hosting-API* zum Hosten von UWP-Steuerelementen in jedes UI-Element, das ein Fenster-Handle (zugeordnet ist HWND). Mit dieser API können nicht-UWP-desktopanwendungen mit den neuesten Windows 10-UI-Features, die nur über UWP-Steuerelemente verfügbar sind. Beispielsweise können nicht-UWP-desktopanwendungen diese API zum Hosten von UWP-Steuerelementen, die das [Fluent Design-Systems](../design/fluent-design-system/index.md) und [Windows Ink](../design/input/pen-and-stylus-interactions.md)unterstützen.

Die UWP-XAML hosting-API bildet die Grundlage für eine breitere Gruppe von Steuerelementen, die wir zum Aktivieren der Entwickler Fluent-Benutzeroberfläche in nicht-UWP-desktopanwendungen bringen bereitstellen. In diesem Szenario wird mitunter als *XAML-Inseln*bezeichnet. Weitere Informationen zu diesem Szenario Entwickler finden Sie in [UWP-Steuerelemente in desktop-Apps](xaml-host-controls.md).

## <a name="is-the-uwp-xaml-hosting-api-right-for-your-desktop-application"></a>Ist der UWP-XAML-API-Rechte für Ihre desktop-Anwendung hosten?

Die UWP-XAML hosting-API bietet die Low-Level-Infrastruktur für das Hosten von UWP-Steuerelemente in desktop-Apps. Einige Arten von desktop-Apps haben die Möglichkeit der Verwendung von alternativen und einfacher APIs um dies zu erreichen.  

* Wenn Sie eine C++ Win32-desktop-Anwendung und Host-UWP-Steuerelemente in Ihrer Anwendung möchten, müssen Sie die UWP-XAML hosting-API verwenden. Es gibt keine alternativen für diese Arten von Anwendungen.

* Für WPF und Windows Forms-Anwendungen empfehlen wir die Verwendung von [umschlossenen Steuerelemente](xaml-host-controls.md#wrapped-controls) und der [Host-Steuerelemente](xaml-host-controls.md#host-controls) in der Windows-Community-Toolkit anstelle der UWP-XAML hosting-API werden. Diese Steuerelemente verwenden, die UWP-XAML intern hosting-API und ein einfacher Development-Erlebnis zu bieten. Allerdings können Sie die UWP-XAML-API direkt in diese Arten von Anwendungen hosten, wenn Sie auswählen.

## <a name="related-samples"></a>Verwandte Beispiele

Wie Sie die UWP-XAML hosting-API in Ihrem Code verwenden, hängt von Ihrem Anwendungstyp, das Design der Anwendung und anderen Faktoren ab. Zum verdeutlichen, wie Sie diese API im Kontext einer vollständigen Anwendung verwenden, bezieht sich in diesem Artikel auf Code aus den folgenden Beispielen.

### <a name="c-win32"></a>C++ Win32

Es gibt mehrere Beispiele auf GitHub, die zeigen, wie Sie die UWP-XAML hosting-API in einer C++ Win32-Anwendung:

  * [XamlHostingSample](https://github.com/Microsoft/Windows-appsample-Xaml-Hosting). In diesem Beispiel wird veranschaulicht, wie die UWP [InkCanvas](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inkcanvas), [InkToolbar](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.inktoolbar)und [MediaPlayerElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.mediaplayerelement) -Steuerelemente an eine C++ Win32-Anwendung hinzufügen.
  * [XamlIslands32](https://github.com/clarkezone/cppwinrt/tree/master/Desktop/XamlIslandsWin32). In diesem Beispiel wird veranschaulicht, wie eine C++ Win32-Anwendung mehrere grundlegende UWP-Steuerelemente hinzu und DPI-Änderungen zu behandeln.

### <a name="wpf-and-windows-forms"></a>WPF und Windows Forms

Das [WindowsXamlHost](https://docs.microsoft.com/windows/communitytoolkit/controls/wpf-winforms/windowsxamlhost) -Steuerelement in der Windows-Community-Toolkit fungiert als eine referenzbeispiel für die Verwendung der UWP hosting-API in WPF- oder Windows Forms-Anwendung. Der Quellcode ist an folgenden Orten verfügbar:

  * Für die WPF-Version des Steuerelements, [hier](https://github.com/Microsoft/WindowsCommunityToolkit/tree/master/Microsoft.Toolkit.Win32/Microsoft.Toolkit.Wpf.UI.XamlHost). Die WPF-Version wird von [**System.Windows.Interop.HwndHost**](https://docs.microsoft.com/dotnet/api/system.windows.interop.hwndhost)abgeleitet.
  * Für die Windows Forms-Version des Steuerelements, [hier](https://github.com/Microsoft/WindowsCommunityToolkit/tree/master/Microsoft.Toolkit.Win32/Microsoft.Toolkit.Forms.UI.XamlHost). Windows Forms-Version von [**System.Windows.Forms.Control**](https://docs.microsoft.com/dotnet/api/system.windows.forms.control)abgeleitet ist.

## <a name="prerequisites"></a>Voraussetzungen

Die UWP-XAML hosting-API hat diese erforderlichen Komponenten.

* Windows 10 Insider Preview build 17709 (oder einen späteren Build) und den entsprechenden Insider Preview-Build des Windows SDKS. Da dies ein entwickelnden Feature ist, wird empfohlen für eine optimale Verwendung des neuesten Builds.

* Um die UWP-XAML hosting-API in Ihrer Desktopanwendung zu verwenden, müssen Sie Ihr Projekt konfigurieren, sodass Sie UWP-APIs aufrufen können:

    * **C++ Win32-:** Es wird empfohlen, dass Sie das Projekt zur Verwendung konfigurieren [C++ / WinRT](../cpp-and-winrt-apis/index.md). Herunterladen und Installieren der [C++ / WinRT Visual Studio Extension (VSIX)](https://aka.ms/cppwinrt/vsix) aus dem Visual Studio Marketplace und fügen Sie dann die ```<CppWinRTEnabled>true</CppWinRTEnabled>``` -Eigenschaft verwenden, um Ihre VCXPROJ-Datei als beschrieben [hier](../cpp-and-winrt-apis/intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).

    * **Windows Forms und WPF:** [Gehen Sie wie folgt vor.](../porting/desktop-to-uwp-enhance.md#modify-a-net-project-to-use-uwp-apis)

## <a name="architecture-of-xaml-islands"></a>Architektur der XAML-Inseln

Die UWP-XAML hosting-API umfasst [**DesktopWindowXamlSource**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting.desktopwindowxamlsource), [**WindowsXamlManager**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting.windowsxamlmanager)und andere verwandten Typen im Namespace [**Windows.UI.Xaml.Hosting**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting) . Desktop-Apps können diese API zum Rendern von UWP-Steuerelemente und Fokus-Navigation per Tastatur in und aus den Elementen weitergeleitet. Desktop-Apps können auch Größe und position der UWP-Steuerelemente nach Bedarf.

Wenn Sie eine XAML-Insel unter Verwendung des XAML hosting-API in einer desktop-Anwendung erstellen, müssen Sie die folgende Hierarchie der Objekte:

* Auf der Basisebene ist das UI-Element in der Anwendung in der XAML-Insel hosten soll. Dieses UI-Element muss einen Fensterhandle (HWND) verfügen. Beispiele für UI-Elemente, die in denen Sie eine XAML-Insel hosten können sind [**System.Windows.Interop.HwndHost**](https://docs.microsoft.com/dotnet/api/system.windows.interop.hwndhost) für WPF-Anwendung [**System.Windows.Forms.Control**](https://docs.microsoft.com/dotnet/api/system.windows.forms.control) für Windows Forms-Anwendung und ein [Fenster](https://docs.microsoft.com/windows/desktop/winmsg/about-windows) für C++ Win32-Anwendungen.

* Auf der nächsten ist Ebene ein **DesktopWindowXamlSource** -Objekt. Dieses Objekt stellt die Infrastruktur für die XAML-Insel hosten. Der Code ist verantwortlich für das Erstellen dieses Objekts und diese an das übergeordnete UI-Element.

* Wenn Sie eine **DesktopWindowXamlSource**erstellen, erstellt dieses Objekt automatisch native untergeordnetes Fenster um Ihre UWP-Steuerelement zu hosten. Diese systemeigenen untergeordnetes Fenster wird hauptsächlich herausgenommen Code, aber Sie können das Handle (HWND) bei Bedarf zugreifen.

* Schließlich ist auf der obersten Ebene das UWP-Steuerelement, das Sie in Ihrer desktop-Anwendung hosten möchten. Dies kann ein UWP-Objekt sein, die von [**Windows.UI.Xaml.UIElement**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement), einschließlich alle UWP-Steuerelemente, die von der Windows SDK sowie benutzerdefinierte Steuerelemente bereitgestellten abgeleitet wird.

Das folgende Diagramm zeigt die Hierarchie der Objekte in einer XAML-Insel.

![DesktopWindowXamlSource-Architektur](images/xaml-hosting-api-rev2.png)

## <a name="how-to-host-uwp-xaml-controls"></a>Informationen zum Hosten von UWP-XAML-Steuerelementen

Hier sind die wichtigsten Schritte für die Verwendung der UWP-XAML hosting-API zum ein UWP-Steuerelement in Ihrer Anwendung hosten.

1. Initialisieren Sie das UWP-XAML-Framework für den aktuellen Thread, bevor die Anwendung die [**Windows.UI.Xaml.UIElement**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement) -Objekte, die sie hostet in der [**DesktopWindowXamlSource**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting.desktopwindowxamlsource)erstellt.

    * Wenn die Anwendung das **DesktopWindowXamlSource** -Objekt erstellt, bevor sie die Objekte **Windows.UI.Xaml.UIElement** erstellt, wird dieses Framework für Sie initialisiert werden, wenn Sie das **DesktopWindowXamlSource** -Objekt zu instanziieren . In diesem Szenario müssen Sie eigene, initialisieren Sie das Framework Code hinzufügen.

    * Wenn jedoch die Anwendung die **Windows.UI.Xaml.UIElement** Objekte erstellt, bevor sie das **DesktopWindowXamlSource** -Objekt erstellt, das sie hostet, muss Ihre Anwendung die statische [**aufrufen WindowsXamlManager.InitializeForCurrentThread**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting.windowsxamlmanager.initializeforcurrentthread) Methode, um die UWP-XAML-Framework explizit zu initialisieren, bevor die **Windows.UI.Xaml.UIElement** Objekte instanziiert werden. Ihre Anwendung sollte in der Regel diese Methode aufrufen sollten, wenn das übergeordnete UI-Element, das die **DesktopWindowXamlSource** hostet instanziiert wird.

    ```cppwinrt
    Windows::UI::Xaml::Hosting::WindowsXamlManager windowsXamlManager =
        Windows::UI::Xaml::Hosting::WindowsXamlManager::InitializeForCurrentThread();
    ```

    ```csharp
    global::Windows.UI.Xaml.Hosting.WindowsXamlManager windowsXamlManager =
        global::Windows.UI.Xaml.Hosting.WindowsXamlManager.InitializeForCurrentThread();
    ```

    > [!NOTE]
    > Diese Methode gibt ein [**WindowsXamlManager**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting.windowsxamlmanager) -Objekt, das einen Verweis auf das UWP-XAML-Framework enthält. Sie können beliebig viele **WindowsXamlManager** Objekte in einem bestimmten Thread soll erstellen. Jedoch, da jedes Objekt einen Verweis auf das UWP-XAML-Framework enthält, sollten Sie freigeben der Objekte, um sicherzustellen, dass XAML-Ressourcen schließlich freigegeben werden.

2. Erstellen Sie ein [**DesktopWindowXamlSource**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting.desktopwindowxamlsource) -Objekt, und ordnen Sie es einem übergeordneten UI-Element in Ihrer Anwendung, die ein Fensterhandle zugeordnet ist.

    Zu diesem Zweck müssen Sie die folgenden Schritte:

    1. Erstellen Sie ein **DesktopWindowXamlSource** -Objekt, und wandeln sie in der **IDesktopWindowXamlSourceNative** COM-Schnittstelle. Diese Schnittstelle wird deklariert, der ```windows.ui.xaml.hosting.desktopwindowxamlsource.h``` Header-Datei im Windows SDK. In C++ Win32-Projekt können Sie diese Headerdatei direkt verweisen. In einem WPF- oder Windows Forms-Projekt müssen Sie diese Schnittstelle im Code Ihrer Anwendung mit dem [**ComImport**](https://docs.microsoft.com/dotnet/api/system.runtime.interopservices.comimportattribute) -Attribut zu deklarieren. Stellen Sie sicher, Ihre Interface-Deklaration genau entspricht die Schnittstellendeklaration im ```windows.ui.xaml.hosting.desktopwindowxamlsource.h```.

    2. Rufen Sie die Methode **AttachToWindow** der **IDesktopWindowXamlSourceNative** -Schnittstelle, und übergeben Sie das Fenster-Handle für das übergeordnete UI-Element in der Anwendung.

    3. Legen Sie die ursprüngliche Größe des Fensters interne untergeordnetes Element in der **DesktopWindowXamlSource**enthalten sind. Standardmäßig wird diese interne untergeordnetes Fenster auf eine Breite und Höhe von 0 festgelegt. Wenn Sie die Größe des Fensters nicht festlegen, werden alle UWP-Steuerelemente, die Sie der **DesktopWindowXamlSource** hinzufügen nicht angezeigt. Um das interne untergeordnete Fenster in der **DesktopWindowXamlSource**zuzugreifen, verwenden Sie die **WindowHandle** -Eigenschaft der **IDesktopWindowXamlSourceNative** -Schnittstelle. Die folgenden Beispiele verwenden die [SetWindowPos](https://docs.microsoft.com/windows/desktop/api/winuser/nf-winuser-setwindowpos) -Funktion, um die Größe des Fensters festzulegen.

    Hier sind einige Codebeispiele, die diesen Prozess zu veranschaulichen.

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

3. Legen Sie die **Windows.UI.Xaml.UIElement** , die Sie für die [**Content**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting.desktopwindowxamlsource.content) -Eigenschaft des Objekts **DesktopWindowXamlSource** hosten möchten. Im folgenden Beispiel wird ein [**Windows.UI.Xaml.Controls.Grid**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.grid) mit dem Namen ```myGrid``` um die **Content** -Eigenschaft.

   ```cppwinrt
   desktopWindowXamlSource.Content(myGrid);
   ```

   ```csharp
   desktopWindowXamlSource.Content = myGrid;
   ```

Vollständige Beispiele, die veranschaulichen diese Aufgaben im Kontext einer beispielanwendung arbeiten, finden Sie unter den folgenden Codedateien:

  * **C++ Win32-:** Finden Sie in der Datei ["Main.cpp"](https://github.com/Microsoft/Windows-appsample-Xaml-Hosting/blob/master/XamlHostingSample/Main.cpp) im Beispiel [XamlHostingSample](https://github.com/Microsoft/Windows-appsample-Xaml-Hosting) oder [Desktop.cpp](https://github.com/clarkezone/cppwinrt/blob/master/Desktop/XamlIslandsWin32/Desktop.cpp) -Datei im Beispiel [XamlIslands32](https://github.com/clarkezone/cppwinrt/tree/master/Desktop/XamlIslandsWin32) .
  * **WPF:** Finden Sie die Dateien [WindowsXamlHostBase.cs](https://github.com/Microsoft/WindowsCommunityToolkit/blob/master/Microsoft.Toolkit.Win32/Microsoft.Toolkit.Wpf.UI.XamlHost/WindowsXamlHostBase.cs) und [WindowsXamlHost.cs](https://github.com/Microsoft/WindowsCommunityToolkit/blob/master/Microsoft.Toolkit.Win32/Microsoft.Toolkit.Wpf.UI.XamlHost/WindowsXamlHost.cs) im Windows Community Toolkit.  
  * **Windows Forms:** Finden Sie die Dateien [WindowsXamlHostBase.cs](https://github.com/Microsoft/WindowsCommunityToolkit/blob/master/Microsoft.Toolkit.Win32/Microsoft.Toolkit.Forms.UI.XamlHost/WindowsXamlHostBase.cs) und [WindowsXamlHost.cs](https://github.com/Microsoft/WindowsCommunityToolkit/blob/master/Microsoft.Toolkit.Win32/Microsoft.Toolkit.Forms.UI.XamlHost/WindowsXamlHost.cs) im Windows Community Toolkit.


## <a name="how-to-host-custom-uwp-xaml-controls"></a>Wie mit benutzerdefinierten Host UWP XAML-Steuerelemente

> [!IMPORTANT]
> Benutzerdefinierte UWP-XAML-Steuerelemente von 3. Parteien werden derzeit nur in C#-WPF- oder Windows Forms-Anwendung unterstützt. Sie müssen den Quellcode für die Steuerelemente verfügen, damit Sie ihn in Ihrer Anwendung kompilieren können.

Wenn Sie ein benutzerdefiniertes UWP-XAML-Steuerelement (ein Steuerelement, das Sie selbst definieren oder ein Steuerelement von bereitgestellt, die eine 3rd party) hosten möchten, müssen Sie die folgenden zusätzlichen Aufgaben zusätzlich zu den im [vorherigen Abschnitt](#how-to-host-uwp-xaml-controls)beschriebene Verfahren ausführen.

1. Definieren Sie einen benutzerdefinierten Typ, die auch implementiert [**IXamlMetadataProvider**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.markup.ixamlmetadataprovider) [**Windows.UI.Xaml.Application**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.application) abgeleitet. Diese Art fungiert als Stamm Metadatenanbieter zum Laden von Metadaten für benutzerdefinierte UWP-XAML-Typen in Assemblys im aktuellen Verzeichnis der Anwendung.

    Ein Beispiel, das veranschaulicht, wie Sie dies tun, finden Sie in der Codedatei [XamlApplication.cs](https://github.com/Microsoft/WindowsCommunityToolkit/tree/master/Microsoft.Toolkit.Win32/Microsoft.Windows.Interop.WindowsXamlHost.Shared/XamlApplication.cs) in der Windows-Community-Toolkit. Diese Datei ist Teil der gemeinsam genutzte Implementierung der **WindowsXamlHost** Klassen für WPF und Windows Forms, das verdeutlichen, wie Sie die UWP-XAML hosting-API in diese Arten von apps verwenden.

2. Rufen Sie die [**GetXamlType**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.markup.ixamlmetadataprovider.getxamltype) -Methode des Anbieters Metadaten Stamm, wenn der Typname des UWP-XAML-Steuerelements zugeordnet ist (Dies kann im Code zur Laufzeit zugewiesen werden oder Sie können dies im Eigenschaftenfenster von Visual Studio zugewiesen werden).

    Ein Beispiel, das veranschaulicht, wie Sie dies tun, finden Sie in der Codedatei [UWPTypeFactory.cs](https://github.com/Microsoft/WindowsCommunityToolkit/tree/master/Microsoft.Toolkit.Win32/Microsoft.Windows.Interop.WindowsXamlHost.Shared/UWPTypeFactory.cs) in der Windows-Community-Toolkit. Diese Datei ist Teil der gemeinsam genutzte Implementierung der **WindowsXamlHost** Klassen für WPF und Windows Forms.

3. Integrieren Sie den Quellcode für das benutzerdefinierte UWP-XAML-Steuerelement in der Host-Anwendung-Lösung, erstellen Sie das benutzerdefinierte Steuerelement, und verwenden Sie es in Ihrer Anwendung, indem Sie folgenden [diese Anweisungen](https://docs.microsoft.com/windows/communitytoolkit/controls/wpf-winforms/windowsxamlhost#add-a-custom-uwp-control).

## <a name="how-to-handle-keyboard-focus-navigation"></a>Wie Sie den Tastaturfokus behandeln

Wenn der Benutzer über die UI-Elemente in Ihrer Anwendung über die Tastatur (z. B. durch Drücken der **Tab** -Taste oder Richtung-Taste Schlüssel) navigiert, müssen Sie programmgesteuert verlagern des Fokus in und aus dem **DesktopWindowXamlSource** -Objekt. Navigation mithilfe der Tastatur des Benutzers erreicht die **DesktopWindowXamlSource**, verschieben den Fokus an das erste [**Windows.UI.Xaml.UIElement**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement) -Objekt in der Reihenfolge für die Seitennavigation für Ihre Benutzeroberfläche, weiterhin Fokus auf die folgenden ** Windows.UI.Xaml.UIElement** Objekte als der Benutzer durchläuft die Elemente, und verschieben den Fokus zurück aus der **DesktopWindowXamlSource** und in der übergeordneten UI-Element.  

Die UWP-XAML hosting-API bietet verschiedene Typen und Member damit Sie diese Aufgaben ausführen können.

1. Wenn die Tastaturnavigation Ihre **DesktopWindowXamlSource**eingibt, wird das [**GotFocus**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting.desktopwindowxamlsource.gotfocus) -Ereignis ausgelöst. Behandeln Sie dieses Ereignis und programmgesteuert verlagern Sie des Fokus auf das erste gehosteten **Windows.UI.Xaml.UIElement** mithilfe der [**NavigateFocus**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting.desktopwindowxamlsource.navigatefocus) -Methode.

2. Wenn der Benutzer auf das letzte fokussierbare Element in der **DesktopWindowXamlSource** ist und die **Tab** -Taste oder eine Pfeiltaste drückt, wird das [**TakeFocusRequested**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting.desktopwindowxamlsource.takefocusrequested) -Ereignis ausgelöst. Behandeln Sie dieses Ereignis und verlagern Sie des Fokus programmgesteuert auf das nächste fokussierbare Element in der Host-Anwendung. In einer WPF-Anwendung, die **DesktopWindowXamlSource** in einem [**System.Windows.Interop.HwndHost**](https://docs.microsoft.com/dotnet/api/system.windows.interop.hwndhost)gehostet wird, können Sie z. B. die [**MoveFocus**](https://docs.microsoft.com/dotnet/api/system.windows.frameworkelement.movefocus) -Methode verwenden, übertragen Sie den Fokus auf das nächste fokussierbare Element in der Host-Anwendung.

Beispiele für die Vorgehensweise im Kontext des eine funktionierende-beispielanwendung finden Sie die folgenden Codedateien:
  * **WPF:** Finden Sie im Windows Community Toolkit [WindowsXamlHostBase.Focus.cs](https://github.com/Microsoft/WindowsCommunityToolkit/blob/master/Microsoft.Toolkit.Win32/Microsoft.Toolkit.Wpf.UI.XamlHost/WindowsXamlHostBase.Focus.cs) .  
  * **Windows Forms:** Finden Sie im Windows Community Toolkit [WindowsXamlHostBase.KeyboardFocus.cs](https://github.com/Microsoft/WindowsCommunityToolkit/blob/master/Microsoft.Toolkit.Win32/Microsoft.Toolkit.Forms.UI.XamlHost/WindowsXamlHostBase.KeyboardFocus.cs) .

## <a name="how-to-handle-layout-changes"></a>Zum Behandeln von Layout zu ändern

Wenn der Benutzer die Größe des übergeordneten UI-Elements ändert, müssen Sie zum Behandeln von layoutänderungen erforderlich, um sicherzustellen, Ihre UWP-Steuerelemente, die zeigen, wie erwartet. Hier sind einige wichtigen Szenarien zu berücksichtigen.

1. Wenn das übergeordnete Element der Benutzeroberfläche muss die Größe der rechteckigen Bereich benötigt, um die **Windows.UI.Xaml.UIElement** passen, die Sie auf die **DesktopWindowXamlSource**hosten, rufen Sie die [**Measure**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.measure) -Methode für die **Windows.UI.Xaml.UIElement **. Beispiel:
    * In einer WPF-Anwendung können Sie die [**MeasureOverride**](https://docs.microsoft.com/dotnet/api/system.windows.frameworkelement.measureoverride) -Methode des der [**HwndHost**](https://docs.microsoft.com/dotnet/api/system.windows.interop.hwndhost) dazu, die die **DesktopWindowXamlSource**hostet.
    * In einer Windows Forms-Anwendung können Sie die [**GetPreferredSize**](https://docs.microsoft.com/dotnet/api/system.windows.forms.control.getpreferredsize) -Methode des [**Steuerelements**](https://docs.microsoft.com/dotnet/api/system.windows.forms.control) dazu, die die **DesktopWindowXamlSource**hostet.

2. Wenn die Größe des übergeordneten UI-Element wird, rufen Sie die Methode [**Anordnen**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.arrange) der Stamm- **Windows.UI.Xaml.UIElement** , die hosten Sie auf die **DesktopWindowXamlSource**. Beispiel:
    * In einer WPF-Anwendung können Sie die [**ArrangeOverride**](https://docs.microsoft.com/dotnet/api/system.windows.frameworkelement.arrangeoverride) -Methode des Objekts [**HwndHost**](https://docs.microsoft.com/dotnet/api/system.windows.interop.hwndhost) dazu, die die **DesktopWindowXamlSource**hostet.
    * In einer Windows Forms-Anwendung können Sie den Handler für das [**SizeChanged**](https://docs.microsoft.com/dotnet/api/system.windows.forms.control.sizechanged) -Ereignis des [**Steuerelements**](https://docs.microsoft.com/dotnet/api/system.windows.forms.control) , hostet die **DesktopWindowXamlSource**dazu.

Beispiele für die Vorgehensweise im Kontext des eine funktionierende-beispielanwendung finden Sie die folgenden Codedateien:
  * **WPF:** Finden Sie im Windows Community Toolkit [WindowsXamlHost.Layout.cs](https://github.com/Microsoft/WindowsCommunityToolkit/blob/master/Microsoft.Toolkit.Win32/Microsoft.Toolkit.Wpf.UI.XamlHost/WindowsXamlHostBase.Layout.cs) .  
  * **Windows Forms:** Finden Sie im Windows Community Toolkit [WindowsXamlHost.Layout.cs](https://github.com/Microsoft/WindowsCommunityToolkit/blob/master/Microsoft.Toolkit.Win32/Microsoft.Toolkit.Forms.UI.XamlHost/WindowsXamlHostBase.Layout.cs) .

## <a name="how-to-handle-dpi-changes"></a>Zum Behandeln von DPI-Änderungen

Wenn Sie DPI-Änderungen im Fenster behandeln, hostet, Ihre UWP (z. B., wenn der Benutzer das Fenster zwischen Bildschirmen mit unterschiedlichen Energiezustände DPI-Wert zieht) steuern, möchten, müssen Sie zum Konfigurieren von UWP-Steuerelement mit einem Rendertransformation, Lauschen DPI-Änderungen in Ihrer app , und aktualisieren Sie die Position des Fensters und Transformation des UWP-Steuerelements in Reaktion auf die DPI-Änderungen zu rendern.

Die folgenden Schritte veranschaulichen eine Möglichkeit zur Behandlung von dieser Vorgang im Kontext des eine C++ Win32-Anwendung. Ein vollständiges Beispiel finden Sie in Codedateien [Desktop.cpp](https://github.com/clarkezone/cppwinrt/blob/master/Desktop/XamlIslandsWin32/Desktop.cpp) und [Desktop.h](https://github.com/clarkezone/cppwinrt/blob/master/Desktop/XamlIslandsWin32/Desktop.h) in das [XamlIslands32](https://github.com/clarkezone/cppwinrt/tree/master/Desktop/XamlIslandsWin32) -Beispiel auf GitHub.

1. Verwalten Sie ein [**ScaleTransform**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.scaletransform) -Objekt in Ihrer app, und weisen Sie sie an die Methode [**RenderTransform**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.rendertransform) von Ihrer UWP-Steuerelement. Im folgende Beispiel wird für ein Steuerelement [**Windows.UI.Xaml.Controls.Grid**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.grid) in einer C++ Win32-Anwendung.

    ```cppwinrt
    // Private fields maintained by your app, such as in a window class you have defined.
    Windows::UI::Xaml::Media::ScaleTransform m_scale;
    Windows::UI::Xaml::Controls::Grid m_rootGrid;

    // Code that runs during initialization, such as the constructor for a window class you have defined.
    m_rootGrid.RenderTransform(m_scale);
    ```

2. Hören Sie in Ihrer [**WindowProc**](https://msdn.microsoft.com/library/windows/desktop/ms633573.aspx) -Funktion für die [**WM_DPICHANGED**](https://docs.microsoft.com/windows/desktop/hidpi/wm-dpichanged) -Nachricht. In Reaktion auf diese Meldung:
    * Verwenden Sie die Funktion [**SetWindowPos**](https://docs.microsoft.com/windows/desktop/api/winuser/nf-winuser-setwindowpos) , Größe des Fensters, das das UWP-Steuerelement an das Rechteck an Sie übergebenen enthält.
    * Aktualisieren Sie die Skalierungsfaktoren x- und y-Achse des Objekts **ScaleTransform** gemäß der neue DPI-Wert.
    * Nehmen Sie alle erforderlichen Anpassungen vor, um die Darstellung und das Layout von Ihrer UWP-Steuerelement. Im folgenden Codebeispiel wird passt [**Padding**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.grid.padding) des gehosteten **Windows.UI.Xaml.Controls.Grid** Steuerelements in Reaktion auf Änderungen der DPI-Wert.

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

2. Zum Konfigurieren Ihrer Anwendung, darauf zu achten pro-Monitor-DPI-Wert zu Ihrem Projekt hinzufügen einer [parallelen Assembly-manifest](https://docs.microsoft.com/windows/desktop/SbsCs/application-manifests) , und legen Sie ```<dpiAwareness>``` Element ```PerMonitorV2```. Weitere Informationen zu diesen Wert finden Sie in der Beschreibung für [**DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2**](https://docs.microsoft.com/windows/desktop/hidpi/dpi-awareness-context).

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

    Ein vollständiges Beispiel Side-by-Side-Assembly-Manifest finden Sie unter der [XamlIslandsWin32.exe.manifest](https://github.com/clarkezone/cppwinrt/blob/master/Desktop/XamlIslandsWin32/XamlIslandsWin32.exe.manifest) -Datei in das [XamlIslands32](https://github.com/clarkezone/cppwinrt/tree/master/Desktop/XamlIslandsWin32) -Beispiel auf GitHub.

## <a name="limitations"></a>Einschränkungen

Der XAML-Code hosting-API teilt dieselben Einschränkungen wie alle anderen Typen von XAML-Steuerelemente für Windows 10. Eine detaillierte Liste finden Sie in [XAML-Host Steuerelement Einschränkungen](xaml-host-controls.md#limitations).

## <a name="troubleshooting"></a>Problembehandlung

### <a name="error-using-uwp-xaml-hosting-api-in-a-uwp-app"></a>Fehler bei der Verwendung von UWP-XAML hosting-API in einer UWP-app

| Problem | Auflösung |
|-------|------------|
| Ihre app erhält eine **COMException** mit folgender Meldung: "DesktopWindowXamlSource kann nicht aktiviert werden. Dieser Typ kann in einer UWP-app verwendet werden." oder "WindowsXamlManager kann nicht aktiviert werden. Dieser Typ kann in einer UWP-app verwendet werden." | Dieser Fehler weist darauf hin, Sie versuchen, die UWP-XAML hosting-API verwenden (genauer gesagt: Sie möchten die Typen [**DesktopWindowXamlSource**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting.desktopwindowxamlsource) oder [**WindowsXamlManager**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting.windowsxamlmanager) instanziieren) in einer UWP-app. Die UWP-XAML hosting-API ist lediglich in nicht-UWP-desktop-apps, z. B. WPF, Windows Forms und C++ Win32-Anwendungen verwendet werden. |

### <a name="error-attaching-to-a-window-on-a-different-thread"></a>Fehler beim Anhängen an ein Fenster in einem anderen thread

| Problem | Auflösung |
|-------|------------|
| Ihre app erhält eine **COMException** mit folgender Meldung: "AttachToWindow Methode ist fehlgeschlagen, da das angegebene HWND auf einem anderen Thread erstellt wurde." | Dieser Fehler weist darauf hin, dass Ihre Anwendung die **IDesktopWindowXamlSourceNative.AttachToWindow** -Methode aufgerufen, und übergeben es HWND eines Fensters, die in einem anderen Thread erstellt wurde. Sie müssen diese Methode das HWND eines Fensters übergeben, die auf demselben Thread wie der Code erstellt wurde, aus denen Sie die Methode aufrufen. |

### <a name="error-attaching-to-a-window-on-a-different-top-level-window"></a>Fehler beim Anhängen an ein Fenster auf ein anderes auf oberster Ebene Fenster

| Problem | Auflösung |
|-------|------------|
| Ihre app erhält eine **COMException** mit folgender Meldung: "AttachToWindow Methode fehlgeschlagen, da das angegebene HWND aus einer anderen auf oberster Ebene als HWND wird, die zuvor auf demselben Thread AttachToWindow übergeben wurde." | Dieser Fehler weist darauf hin, dass Ihre Anwendung die **IDesktopWindowXamlSourceNative.AttachToWindow** -Methode aufgerufen, und übergeben es HWND eines Fensters, die aus einer anderen auf oberster Ebene als ein Fenster wird, das Sie in einem vorherigen Aufruf dieser Methode angegeben auf dem gleichen Thread.</p></p>Nachdem Ihre Anwendung **IDesktopWindowXamlSourceNative.AttachToWindow** für einen bestimmten Thread aufgerufen hat, können alle anderen [**DesktopWindowXamlSource**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.hosting.desktopwindowxamlsource) Objekte, die auf demselben Thread nur Windows zuordnen, die untergeordneten Elemente der obersten Ebene Fensteransicht werden in dem ersten Aufruf von **IDesktopWindowXamlSourceNative.AttachToWindow**übergeben wurde. Wenn alle **DesktopWindowXamlSource** Objekte, die für einen bestimmten Thread geschlossen werden, kann der nächsten **DesktopWindowXamlSource** dann jedes Fenster erneut an.</p></p>Um dieses Problem zu beheben, entweder alle **DesktopWindowXamlSource** -Objekte, die an andere Fenster der obersten Ebene für diesen Thread gebunden sind, oder erstellen einen neuen Thread für diese **DesktopWindowXamlSource**schließen. |

## <a name="related-topics"></a>Verwandte Themen

* [UWP-Steuerelemente in desktop-Apps](xaml-host-controls.md)
