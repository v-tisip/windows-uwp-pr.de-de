---
ms.assetid: DC235C16-8DAF-4078-9365-6612A10F3EC3
title: Erstellen Sie eine Hello World-app in C++ / CX (Windows 10)
description: Mit Microsoft Visual Studio2017, können Sie C++ / CX eine app entwickeln, die auf Windows 10, sowie auf Smartphones mit Windows 10 ausgeführt wird. Die Benutzeroberfläche dieser Apps ist in XAML (Extensible Application Markup Language) definiert.
ms.date: 06/11/2018
ms.topic: article
keywords: windows 10, uwp
ms.localizationpriority: medium
ms.openlocfilehash: 6954f935440f75a728c3f3601ade884bbee7b6bc
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8919041"
---
# <a name="create-a-hello-world-app-in-ccx"></a>Erstellen der app "Hello World" in C++ / CX

> [!IMPORTANT]
> In diesem Lernprogramm verwendet C++ / CX. Microsoft stellt C++ / WinRT: eine vollständig standardisierte moderne C ++ 17-Programmiersprache für Windows-Runtime-APIs (WinRT). Weitere Informationen zu dieser Sprache, finden Sie unter [C++ / WinRT](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/). 

Mit Microsoft Visual Studio2017, können Sie C++ / CX eine app entwickeln, die auf Windows 10 mit einer Benutzeroberfläche ausgeführt wird, die in Extensible Application Markup Language (XAML) definiert ist.

> [!NOTE]
> In diesem Lernprogramm wird Visual Studio Community 2017 verwendet. Wenn Sie eine andere Version von Visual Studio verwenden, kann das Programm für Sie etwas anders aussehen.

## <a name="before-you-start"></a>Vorbereitung

-   Für dieses Lernprogramm, müssen Sie Visual StudioCommunity 2017 oder eine der anderen Versionen von Visual Studio2017 auf einem Computer verwenden, auf denen Windows 10 ausgeführt wird. Informationen zum Herunterladen finden Sie unter [Herunterladen der Tools](http://go.microsoft.com/fwlink/p/?LinkId=532666).
-   Angenommen, Sie haben ein grundlegendes Verständnis der C++ / CX-, XAML, und die Konzepte im [XAML-Übersicht](https://msdn.microsoft.com/library/windows/apps/Mt185595).
-   Wir gehen davon aus, dass Sie das Standardfensterlayout in Visual Studio verwenden. Um das Layout auf das Standardlayout zurückzusetzen, klicken Sie in der Menüleiste auf **Fenster** > **Fensterlayout zurücksetzen**.

## <a name="comparing-c-desktop-apps-to-windows-apps"></a>Vergleich zwischen C++-Desktop-Apps und Windows-Apps

Wenn Sie bereits Windows-Desktop-Apps mit C++ programmiert haben, werden Ihnen einige Aspekte der Programmierung von UWP-Apps bekannt sein, einige aber auch nicht.

### <a name="whats-the-same"></a>Gemeinsamkeiten

-   Sie können die STL-, CRT-(mit einigen Ausnahmen) und andere C++-Bibliothek verwenden, solange ruft der Code nur Windows-Funktionen, die in der Windows-Runtime-Umgebung zugegriffen werden kann.

-   Wenn Sie es gewohnt sind, visuelle Designer zu verwenden, können Sie immer noch den in Microsoft Visual Studio integrierten Designer verwenden, oder Sie können das Tool Blend für Visual Studio nutzen, das einen umfassenderen Umfang an Features bietet. Wenn Sie es gewohnt sind, UI manuell zu codieren, können Sie Ihren XAML-Code manuell programmieren.

-   Sie erstellen wie gehabt Apps, die Windows-Betriebssystemtypen und Ihre eigenen benutzerdefinierten Typen verwenden.

-   Sie verwenden weiterhin Debugger, Profiler und andere Entwicklungstools von Visual Studio.

-   Sie erstellen weiterhin Apps, die mit dem Visual C++-Compiler in systemeigenem Computercode kompiliert werden. UWP-apps in C++ / CX in einer verwalteten Laufzeitumgebung nicht ausgeführt werden kann.

### <a name="whats-new"></a>Das ist neu:

-   Die Designprinzipien für UWP- und UniverselleWindows-Apps unterscheiden sich erheblich von denen für Desktop-Apps. Der Schwerpunkt liegt nicht mehr auf Fensterrahmen, Bezeichnungen, Dialogfeldern usw. Der Inhalt steht im Vordergrund. Eindrucksvolle universelleWindows-Apps folgen diesen Prinzipien schon mit Beginn der Planungsphase.

-   Die gesamte UI wird in XAML definiert. Die Trennung zwischen UI und Kernprogrammlogik ist bei UniversalWindows-Apps viel eindeutiger als bei einer MFC- oder Win32-App. Designer können in der XAML-Datei am Erscheinungsbild der UI feilen, während Sie sich mit dem Verhalten in der Codedatei beschäftigen.

-   Sie programmieren in erster Linie für die Windows-Runtime – eine neue, navigationsfreundliche, objektorientierte API. Auf Windows-Geräten ist für einige Funktionen aber auch weiterhin Win32 verfügbar.

-   Sie verwenden C++/CX zum Verwenden oder Erstellen von Windows-Runtime-Objekten. C++/CX ermöglicht die Behandlung von C++-Ausnahmen, die Verwendung von Delegaten und Ereignissen sowie die automatische Verweiszählung dynamisch erstellter Objekte. Bei Verwendung von C++/CX bleibt die zugrunde liegende COM- und Windows-Architektur vor dem Code der App verborgen. Weitere Informationen finden Sie in der [Programmiersprachenreferenz für C++/CX](https://msdn.microsoft.com/library/windows/apps/hh699871.aspx).

-   Ihre App wird zu einem Paket kompiliert, das auch Metadaten zu den in der App enthaltenen Typen, den verwendeten Ressourcen und den benötigten Funktionen (Datei-, Internet- und Kamerazugriff usw.) enthält.

-   Im Microsoft Store und dem WindowsPhone Store wird die Sicherheit Ihrer App anhand eines Zertifizierungsprozesses geprüft, und die App kann von Millionen potenzieller Kunden entdeckt werden.

## <a name="hello-world-store-app-in-ccx"></a>Hello World-Store-app in C++ / CX

Unsere erste App ist „Hello World“. Sie veranschaulicht einige grundlegende Interaktivitätsfunktionen, Layouts und Stile. Wir erstellen eine App auf der Grundlage der Projektvorlage für universelleWindows-Apps. Wenn Sie apps für Windows8.1 und Windows Phone 8.1 vor entwickelt haben, können Sie denken Sie daran, dass Sie drei Projekte in Visual Studio, eins für die Windows-app, eins für die Phone-app, und ein weiteres mit gemeinsam genutztem Code vorhanden sind. Die Windows 10 universelle Windows-Plattform (UWP) ist es möglich sein, nur ein Projekt, das auf allen Geräten, einschließlich Desktop- und Laptop-Computern Windows 10, Geräten wie Tablets, Smartphones, VR-Geräte und so weiter ausgeführt werden kann.

Wir beginnen mit den Grundlagen:

-   So erstellen Sie eine universelle Windows-Projekt in Visual Studio2017.

-   Kennenlernen der erstellten Projekte und Dateien

-   Kennenlernen der Erweiterungen in für VisualC++-komponentenerweiterungen (C++ / CX), und deren Verwendung.

**Erstellen einer Lösung in Visual Studio**

1.  Wählen Sie in der Menüleiste von Visual Studio **Datei** > **Neu** > **Projekt**.

2.  Erweitern Sie im Dialogfeld **Neues Projekt** im linken Bereich **Installiert** > **Visual C++** > **Windows Universal**.

> [!NOTE]
> Sie werden möglicherweise aufgefordert, die universellen Windows-Tools für die C++-Entwicklung zu installieren.

3.  Wählen Sie im mittleren Bereich **Leere App (universelle Windows-App)** aus.

   (Sollten diese Optionen nicht angezeigt werden, vergewissern Sie sich, dass die Entwicklungstools für universelle Windows-Apps installiert sind. Weitere Informationen finden Sie unter [Vorbereiten](get-set-up.md).)

4.  Geben Sie einen Namen für das Projekt ein. Wir nennen unser Projekt „HelloWorld“.

 ![C++ / CX-Projektvorlagen im Dialogfeld "Neues Projekt" ](images/vs2017-uwp-01.png)

5.  Klicken Sie auf die Schaltfläche **OK**.

> [!NOTE]
> Wenn Sie Visual Studio zum ersten Mal verwenden, wird möglicherweise das Dialogfeld „Einstellungen“ angezeigt, in dem Sie aufgefordert werden, **Entwicklermodus** zu aktivieren. Der Entwicklermodus ist eine spezielle Einstellung, die bestimmte Features ermöglicht, z.B. die Berechtigung zum Ausführen von Apps, direkt und nicht nur aus dem Store. Weitere Informationen finden Sie in [Aktivieren Ihres Geräts für die Entwicklung](enable-your-device-for-development.md). Wählen Sie **Entwicklermodus** aus, klicken Sie auf **Ja**, und schließen Sie das Dialogfeld, um mit dem Lernprogramm fortzufahren.

   Ihre Projektdateien werden erstellt.

Werfen wir einen Blick darauf, was sich in der Lösung befindet, bevor wir fortfahren.

![Projektmappe der universellen App mit reduzierten Knoten](images/vs2017-uwp-02.png)

### <a name="about-the-project-files"></a>Informationen zu Projektdateien

Jede XAML-Datei in einem Projektordner verfügt über eine zugehörige XAML.H- und eine XAML.CPP-Datei im selben Ordner und eine G- und eine G.HPP-Datei im Ordner „Generierte Dateien“, der auf dem Datenträger vorhanden ist, jedoch nicht zum Projekt gehört. Sie können die XAML-Dateien modifizieren, um Benutzeroberflächenelemente zu erstellen und sie mit Datenquellen zu verbinden (DataBinding). Sie können die „.h“- und „.cpp“-Dateien modifizieren, um benutzerdefinierte Logik für Ereignishandler hinzuzufügen. Die automatisch erstellten Dateien stellen die Umwandlung von XAML-Markup in C++ / CX. Verändern Sie diese Dateien nicht, sehen Sie sich die Dateien jedoch genauer an, um den CodeBehind besser zu verstehen. Im Grunde genommen enthält die generierte Datei eine partielle Klassendefinition für ein XAML-Stammelement. Diese Klasse ist die gleiche Klasse, die Sie in den XAML.H- und CPP-Dateien bearbeiten. Die generierten Dateien deklarieren die untergeordneten XAML-UI-Elemente als Klassenmember, sodass Sie in Ihrem Code auf sie verweisen können. Beim Erstellen des Builds werden der generierte Code und Ihr Code zu einer vollständigen Klassendefinition zusammengeführt und anschließend kompiliert.

Befassen wir uns zuerst mit den Projektdateien.

-   **App.xaml, App.xaml.h, App.xaml.cpp:** Stellen das Application-Objekt dar, das als Einstiegspunkt einer App fungiert. „App.xaml“ enthält kein seitenspezifisches UI-Markup, Sie können jedoch UI-Formate und andere Elemente hinzufügen, die auf allen Seiten verfügbar sein sollen. Die CodeBehind-Dateien enthalten Handler für die Ereignisse **OnLaunched** und **OnSuspending**. In der Regel können Sie hier benutzerdefinierten Code hinzufügen, um Ihre App zu initialisieren, wenn sie gestartet wird, und eine Bereinigung durchzuführen, wenn sie unterbrochen oder beendet wird.
-   **MainPage.xaml, MainPage.xaml.h, MainPage.xaml.cpp:** Enthalten das XAML-Markup und den CodeBehind für die standardmäßige Startseite in einer App. Sie bietet keine Unterstützung für Navigation oder integrierte Steuerelemente.
-   **pch.h, pch.cpp:** Eine vorkompilierte Headerdatei und die Datei, die sie in Ihr Projekt einfügt. In „pch.h“ können Sie alle Header einfügen, die sich nur selten ändern und sich in anderen Dateien in der Lösung befinden.
-   **Package.appxmanifest:** Eine XML-Datei, in der die von Ihrer App benötigten Gerätefunktionen sowie die App-Versionsinformationen und andere Metadaten beschrieben werden. Doppelklicken Sie auf die Datei, um sie im **Manifest-Designer** zu öffnen.
-   **HelloWorld\_TemporaryKey.pfx:** Ein Schlüssel von Visual Studio, der die Bereitstellung der App auf diesem Gerät ermöglicht.

## <a name="a-first-look-at-the-code"></a>Ein erster Blick auf den Code

Wenn Sie den Code in den Dateien „App.Xaml.h“ und „App.Xaml.cpp“ im freigegebenen Projekt untersuchen, werden Sie feststellen, dass es sich meistens um C++-Code handelt. Einige Syntaxelemente kennen Sie jedoch möglicherweise nicht, wenn Sie noch nicht mit Windows-Runtime-Apps vertraut sind oder wenn Sie mit C++/CLI gearbeitet haben. Die häufigsten nicht standardmäßigen Syntaxelemente, die in C++/CX auftauchen, sind die folgenden:

**Referenzklassen**

Nahezu alle Windows-Runtime-Klassen, zu denen alle Typen in der Windows-API zählen (XAML-Steuerelemente, die Seiten in Ihrer App, die App-Klasse selbst, alle Geräte- und Netzwerkobjekte sowie alle Containertypen), werden als **ref class** deklariert. (Einige Windows-Typen werden als **value class** oder **value struct** deklariert.) Eine Referenzklasse (ref class) kann von beliebigen Programmiersprachen verwendet werden. In C++ / CX die Lebensdauer dieser Typen unterliegt automatische verweiszählung einführt (nicht der Garbagecollection), damit Sie diese Objekte nie explizit löschen. Sie können auch Ihre eigenen Referenzklassen erstellen.

```cpp
namespace HelloWorld
{
   /// <summary>
   /// An empty page that can be used on its own or navigated to within a Frame.
   /// </summary>
   public ref class MainPage sealed
   {
      public:
      MainPage();
   };
}
```    

Alle Windows-Runtime-Typen müssen innerhalb eines Namespace deklariert sein, und anders als bei ISOC++ haben die Typen selbst einen Zugriffsmodifikator. Der Modifikator **public** macht die Klasse für Komponenten für Windows-Runtime außerhalb des Namespace sichtbar. Das Schlüsselwort **sealed** bedeutet, dass die Klasse nicht als Basisklasse dienen kann. Nahezu alle Referenzklassen sind „sealed“. Klassenvererbung wird häufig nicht verwendet, da JavaScript sie nicht versteht.

**ref new** und **^ (Hütchen)**

Sie können eine Variable einer Referenzklasse deklarieren, indem Sie den Operator ^ (Hütchen) verwenden, und Sie können das Objekt mit dem Schlüsselwort „ref new“ instanziieren. Danach greifen Sie auf die Instanzmethoden des Objekts mit dem Operator -> zu, wie bei einem C++-Zeiger. Auf statische Methoden kann mit dem Operator :: zugegriffen werden, genau wie in ISO C++.

Im folgenden Code verwenden wir den vollständig qualifizierten Namen, um ein Objekt zu instanziieren, und verwenden den Operator -> zum Aufrufen einer Instanzmethode.

```cpp
Windows::UI::Xaml::Media::Imaging::BitmapImage^ bitmapImage =
     ref new Windows::UI::Xaml::Media::Imaging::BitmapImage();
      
bitmapImage->SetSource(fileStream);
```

In einer CPP-Datei würden wir in der Regel eine `using namespace  Windows::UI::Xaml::Media::Imaging`-Direktive und das automatische Schlüsselwort hinzufügen, sodass derselbe Code wie folgt aussieht:

```cpp
auto bitmapImage = ref new BitmapImage();
bitmapImage->SetSource(fileStream);
```

**Eigenschaften**

Eine Referenzklasse kann Eigenschaften haben, die, ebenso wie bei verwalteten Sprachen, spezielle Memberfunktionen darstellen, die für verwendenden Code als Felder erscheinen.

```cpp
public ref class SaveStateEventArgs sealed
{
   public:
   // Declare the property
   property Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^>^ PageState
   {
      Windows::Foundation::Collections::IMap<Platform::String^, Platform::Object^>^ get();
   }
   ...
};

   ...
   // consume the property like a public field
   void PhotoPage::SaveState(Object^ sender, Common::SaveStateEventArgs^ e)
   {    
      if (mruToken != nullptr && !mruToken->IsEmpty())
   {
      e->PageState->Insert("mruToken", mruToken);
   }
}
```

**Delegaten**

Ebenso wie bei verwalteten Sprachen stellt ein Delegat einen Referenztyp dar, der eine Funktion mit einer bestimmten Signatur umschließt. Sie kommen meistens mit Ereignissen und Ereignishandlern zum Einsatz.

```cpp
// Delegate declaration (within namespace scope)
public delegate void LoadStateEventHandler(Platform::Object^ sender, LoadStateEventArgs^ e);

// Event declaration (class scope)
public ref class NavigationHelper sealed
{
   public:
   event LoadStateEventHandler^ LoadState;
};

// Create the event handler in consuming class
MainPage::MainPage()
{
   auto navigationHelper = ref new Common::NavigationHelper(this);
   navigationHelper->LoadState += ref new Common::LoadStateEventHandler(this, &MainPage::LoadState);
}
```

## <a name="adding-content-to-the-app"></a>Hinzufügen von Inhalt zur App

Lassen Sie uns der App einige Inhalte hinzufügen.

**Schritt1: Anpassen der Startseite**

1.  Öffnen Sie im **Projektmappen-Explorer** die Datei „MainPage.xaml.cs“.
2.  Erstellen Sie Steuerelemente für die Benutzeroberfläche, indem Sie den folgenden XAML-Code direkt vor dem schließenden Tag zum [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704)-Stammelement hinzufügen. Er enthält ein [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/BR209635) mit einem [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652), in dem der Benutzer zur Eingabe seines Namens aufgefordert wird, ein [**TextBox**](https://msdn.microsoft.com/library/windows/apps/BR209683)-Element, in das der Name eingegeben wird, sowie ein [**Button**](https://msdn.microsoft.com/library/windows/apps/BR209265)- und ein weiteres **TextBlock**-Element.

    ```xaml
    <StackPanel x:Name="contentPanel" Margin="120,30,0,0">
        <TextBlock HorizontalAlignment="Left" Text="Hello World" FontSize="36"/>
        <TextBlock Text="What's your name?"/>
        <StackPanel x:Name="inputPanel" Orientation="Horizontal" Margin="0,20,0,20">
            <TextBox x:Name="nameInput" Width="300" HorizontalAlignment="Left"/>
            <Button x:Name="inputButton" Content="Say &quot;Hello&quot;"/>
        </StackPanel>
        <TextBlock x:Name="greetingOutput"/>
    </StackPanel>
    ```

3.  Sie haben nun eine sehr einfache universelle Windows-App erstellt. Falls Sie wissen möchten, wie die UWP-App aussieht, drücken Sie F5, um die App zu erstellen, bereitzustellen und im Debugmodus auszuführen.

Zunächst erscheint der standardmäßige Begrüßungsbildschirm. Er setzt sich aus einem Bild (Assets\\SplashScreen.scale-100.png) und einer Hintergrundfarbe zusammen, die in der Manifestdatei der App angegeben sind. Weitere Informationen zur Anpassung des Begrüßungsbildschirms finden Sie unter [Hinzufügen eines Begrüßungsbildschirms](https://msdn.microsoft.com/library/windows/apps/Hh465332).

Wenn der Begrüßungsbildschirm verschwindet, wird Ihre App angezeigt. Die Hauptseite der App wird angezeigt.

![UWP-App-Bildschirm mit Steuerelementen](images/xaml-hw-app2.png)

Viel zu bieten hat sie zwar noch nicht, aber trotzdem: Herzlichen Glückwunsch! Sie haben Ihre erste App für die Universelle Windows-Plattform erstellt!

Kehren Sie zu Visual Studio zurück, und drücken Sie Umschalt+F5, um den Debugmodus zu beenden und die App zu schließen.

Weitere Informationen finden Sie unter [Ausführen einer Store-App über Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=619619).

In der App können Sie etwas in das [**TextBox**](https://msdn.microsoft.com/library/windows/apps/BR209683)-Element eingeben, das Klicken auf [**Button**](https://msdn.microsoft.com/library/windows/apps/BR209265) hat jedoch keinerlei Auswirkung. In späteren Schritten erstellen wir daher einen Ereignishandler für das [**Click**](https://msdn.microsoft.com/library/windows/apps/BR227737)-Ereignis der Schaltfläche, um eine personalisierte Begrüßung einzublenden.

## <a name="step-2-create-an-event-handler"></a>Schritt2: Erstellen eines Ereignishandlers

1.  Wählen Sie in „MainPage.xaml“ entweder in der XAML- oder in der Entwurfsansicht das [**Button**](https://msdn.microsoft.com/library/windows/apps/BR209265)-Element „Say Hello“ aus dem zuvor hinzugefügten [**StackPanel**](https://msdn.microsoft.com/library/windows/apps/BR209635)-Element aus.
2.  Öffnen Sie durch Drücken von F4 das **Eigenschaftenfenster**, und wählen Sie anschließend die Ereignisschaltfläche (![Ereignisschaltfläche](images/eventsbutton.png)) aus.
3.  Suchen Sie das [**Click**](https://msdn.microsoft.com/library/windows/apps/BR227737)-Ereignis. Geben Sie im Textfeld den Namen der Funktion ein, die das **Click**-Ereignis behandelt. Geben Sie für dieses Beispiel „Button\_Click“ ein.

    ![Eigenschaftenfenster, Ereignisansicht](images/xaml-hw-event.png)

4.  Drücken Sie die EINGABETASTE. Die Ereignishandlermethode wird in „MainPage.xaml.cpp“ erstellt und im Code-Editor geöffnet, sodass Sie den Code hinzufügen können, der beim Auftreten des Ereignisses ausgeführt werden soll.

   Gleichzeitig wird in „MainPage.xaml“ der XAML-Code für das [**Button**](https://msdn.microsoft.com/library/windows/apps/BR209265)-Element aktualisiert, um den [**Click**](https://msdn.microsoft.com/library/windows/apps/BR227737)-Ereignishandler wie folgt zu deklarieren:

    ```xaml
    <Button Content="Say &quot;Hello&quot;" Click="Button_Click"/>
    ```

   Sie können dies auch einfach manuell zum XAML-Code hinzufügen, was vor allem dann hilfreich ist, wenn der Designer nicht geladen wird. Wenn Sie dies manuell eingeben, geben Sie „Click“ ein, und warten Sie, bis IntelliSense die Option zum Hinzufügen eines neuen Ereignishandlers anzeigt. Auf diese Weise erstellt Visual Studio die erforderliche Methodendeklaration und den erforderlichen Stub.

   Im Designer tritt ein Fehler beim Laden auf, wenn eine unbehandelte Ausnahme während des Renderns auftritt. Für das Rendern im Designer muss eine Entwurfszeitversion der Seite ausgeführt werden. Es ist möglicherweise hilfreich, den ausgeführten Benutzercode zu deaktivieren. Ändern Sie dazu die Einstellung im Dialogfeld **Tools, Optionen**. Deaktivieren Sie unter **XAML-Designer** die Option **Projektcode im XAML-Designer ausführen (falls unterstützt)**.

5.  Fügen Sie dem gerade erstellten **Button\_Click**-Ereignishandler in „MainPage.xaml.cpp“ den folgenden Code hinzu. Dieser Code ruft den Namen des Benutzers aus dem [**TextBox**](https://msdn.microsoft.com/library/windows/apps/BR209683)-Steuerelement `nameInput` ab und erstellt damit eine Begrüßung. Das [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652)-Element `greetingOutput` zeigt das Ergebnis an.

    ```cpp
    void HelloWorld::MainPage::Button_Click(Platform::Object^ sender, Windows::UI::Xaml::RoutedEventArgs^ e)
    {
        greetingOutput->Text = "Hello, " + nameInput->Text + "!";
    }
    ```

6.  Legen Sie das Projekt als Startprojekt fest, und drücken Sie anschließend F5, um die App zu erstellen und auszuführen. Wenn Sie einen Namen in das Textfeld eingeben und anschließend auf die Schaltfläche klicken, zeigt die App eine personalisierte Begrüßung an.

![App-Bildschirm mit angezeigter Meldung](images/xaml-hw-app4.png)

## <a name="step-3-style-the-start-page"></a>Schritt3: Gestalten der Startseite

### <a name="choosing-a-theme"></a>Auswählen eines Designs

Das Erscheinungsbild Ihrer App lässt sich ganz einfach anpassen. Standardmäßig verwendet die App Ressourcen mit hellem Design. Die Systemressourcen enthalten auch ein helles Design. Probieren wir doch einmal aus, wie das aussieht.

**So wechseln Sie zum dunklen Design**

1.  Öffnen Sie „App.xaml“.
2.  Bearbeiten Sie im öffnenden [**Application**](https://msdn.microsoft.com/library/windows/apps/BR242324)-Tag die [**RequestedTheme**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.application.requestedtheme)-Eigenschaft, und legen Sie ihren Wert auf **Dark** fest:

    ```xaml
    RequestedTheme="Dark"
    ```

    Hier sehen Sie das gesamte [**Application**](https://msdn.microsoft.com/library/windows/apps/BR242324)-Tag mit dunklem Design:

    ```xaml 
        <Application
        x:Class="HelloWorld.App"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:HelloWorld"
        RequestedTheme="Dark">
    ```

3.  Drücken Sie F5, um die App zu erstellen und auszuführen. Wie Sie sehen, wird nun das dunkle Design verwendet.

![App-Bildschirm mit dunklem Design](images/xaml-hw-app3.png)

Welches Design sollten Sie verwenden? Das bleibt ganz Ihnen überlassen. Bei Apps, die hauptsächlich Bilder oder Videos anzeigen, sollten Sie das dunkle Design verwenden, während sich bei Apps mit viel Text die Verwendung des hellen Designs empfiehlt. Falls Sie ein benutzerdefiniertes Farbschema verwenden, wählen Sie das Design, das am besten zum Erscheinungsbild Ihrer App passt. Im verbleibenden Teil dieses Lernprogramms verwenden wir in Screenshots das helle Design.

**Hinweis:** das Design wird angewendet, wenn die app gestartet wird, und kann nicht geändert werden, während die app ausgeführt wird.

### <a name="using-system-styles"></a>Verwenden von Systemstilen

Momentan ist der Text in der Windows-App ziemlich klein und nur schwer lesbar. Lassen Sie uns dies ändern, indem wir einen Systemstil anwenden.

**So ändern Sie den Stil eines Elements**

1.  Öffnen Sie „MainPage.xaml“ im Windows-Projekt.
2.  Wählen Sie in der XAML- oder Entwurfsansicht das von Ihnen hinzugefügte [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652)-Element „What’s your name?“ aus.
3.  Wählen Sie im Dialogfeld **Eigenschaften** (**F4**) rechts oben die Schaltfläche „Eigenschaften“ (![Schaltfläche „Eigenschaften“](images/propertiesbutton.png)) aus.
4.  Erweitern Sie die Gruppe **Text** , und legen Sie den Schriftgrad auf „18px“ fest.
5.  Erweitern Sie die Gruppe **Sonstiges**, und suchen Sie dort nach der Eigenschaft **Style**.
6.  Klicken Sie auf den Eigenschaftenmarker (das grüne Feld rechts neben der Eigenschaft **Style**), und wählen Sie anschließend **Systemressource** > **BaseTextBlockStyle** im Menü aus.

     **BaseTextBlockStyle** ist eine Ressource, die im [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/BR208794) unter „<root>\\Programme\\Windows Kits\\10\\Include\\winrt\\xaml\\design\\generic.xaml“ definiert ist.

    ![Eigenschaftenfenster, Eigenschaftenansicht](images/xaml-hw-style-cpp.png)

     Auf der XAML-Entwurfsoberfläche ändert sich die Textdarstellung. Im XAML-Editor wird der XAML-Code für [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652) aktualisiert:

    ```xaml
    <TextBlock Text="What's your name?" Style="{ThemeResource BaseTextBlockStyle}"/>
    ```

7.  Wiederholen Sie den Vorgang, um den Schriftgrad festzulegen und **BaseTextBlockStyle** dem [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/BR209652)-Element `greetingOutput` zuzuweisen.

    **Tipp:** es gibt, zwar kein Text in diesem [**TextBlock-Element**](https://msdn.microsoft.com/library/windows/apps/BR209652), wenn Sie den Mauszeiger über die XAML-Entwurfsoberfläche bewegen eine blaue Umrandung seine Position zeigt, in denen es ist, damit Sie ihn auswählen können.  

    Ihr XAML-Code sieht nun so aus:

    ```xaml
    <StackPanel x:Name="contentPanel" Margin="120,30,0,0">
        <TextBlock Style="{ThemeResource BaseTextBlockStyle}" FontSize="18" Text="What's your name?"/>
        <StackPanel x:Name="inputPanel" Orientation="Horizontal" Margin="0,20,0,20">
            <TextBox x:Name="nameInput" Width="300" HorizontalAlignment="Left"/>
            <Button x:Name="inputButton" Content="Say &quot;Hello&quot;" Click="Button_Click"/>
        </StackPanel>
        <TextBlock Style="{ThemeResource BaseTextBlockStyle}" FontSize="18" x:Name="greetingOutput"/>
    </StackPanel>
    ```

8.  Drücken Sie F5, um die App zu erstellen und auszuführen. Sie sieht jetzt so aus:

![App-Bildschirm mit größerem Text](images/xaml-hw-app5.png)

### <a name="step-4-adapt-the-ui-to-different-window-sizes"></a>Schritt4: Anpassen der UI an verschiedene Fenstergrößen

Als Nächstes sorgen wir dafür, dass sich die UI verschiedenen Bildschirmgrößen anpasst, damit sie auch auf mobilen Geräten gut aussieht. Dazu fügen Sie ein [**VisualStateManager**](https://msdn.microsoft.com/library/windows/apps/BR209021)-Element hinzu und legen Eigenschaften fest, die für die unterschiedlichen Ansichtszustände angewendet werden.

**So passen Sie das UI-Layout an**

1.  Fügen Sie im XAML-Editor nach dem Starttag des [**Grid**](https://msdn.microsoft.com/library/windows/apps/BR242704)-Stammelements den folgenden XAML-Block hinzu:

    ```xaml
    <VisualStateManager.VisualStateGroups>
        <VisualStateGroup>
            <VisualState x:Name="wideState">
                <VisualState.StateTriggers>
                    <AdaptiveTrigger MinWindowWidth="641" />
                </VisualState.StateTriggers>
            </VisualState>
            <VisualState x:Name="narrowState">
                <VisualState.StateTriggers>
                    <AdaptiveTrigger MinWindowWidth="0" />
                </VisualState.StateTriggers>
                <VisualState.Setters>
                    <Setter Target="contentPanel.Margin" Value="20,30,0,0"/>
                    <Setter Target="inputPanel.Orientation" Value="Vertical"/>
                    <Setter Target="inputButton.Margin" Value="0,4,0,0"/>
                </VisualState.Setters>
            </VisualState>
        </VisualStateGroup>
    </VisualStateManager.VisualStateGroups>
    ```

2.  Debuggen Sie die App auf dem lokalen Computer. Sie sehen, dass die UI genauso aussieht wie vorher, es sei denn, die Fensterbreite beträgt weniger als 641DIP (geräteunabhängige Pixel).
3.  Debuggen Sie die App auf dem Emulator für mobile Geräte. Beachten Sie, dass für die UI die Eigenschaften verwendet werden, die Sie unter `narrowState` definiert haben, und dass die Benutzeroberfläche auf dem kleinen Bildschirm korrekt angezeigt wird.

![Bildschirm der mobilen App mit Textdesign](images/hw10-screen2-mob.png)

Wenn Sie bereits in früheren Versionen von XAML ein [**VisualStateManager**](https://msdn.microsoft.com/library/windows/apps/BR209021)-Element genutzt haben, fällt Ihnen vielleicht auf, dass hier für den XAML-Code eine vereinfachte Syntax verwendet wird.

Das [**VisualState**](https://msdn.microsoft.com/library/windows/apps/BR209007)-Element mit dem Namen `wideState` verfügt über ein [**AdaptiveTrigger**](https://msdn.microsoft.com/library/windows/apps/Dn890382)-Element, für das die [**MinWindowWidth**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.adaptivetrigger.minwindowwidth)-Eigenschaft auf den Wert641 festgelegt ist. Das bedeutet, dass der Zustand nur angewendet wird, wenn die Fensterbreite nicht geringer als die Mindestgröße von 641DIP ist. Da Sie keine [**Setter**](https://msdn.microsoft.com/library/windows/apps/BR208817)-Objekte für diesen Zustand definieren, werden die Layouteigenschaften verwendet, die Sie im XAML-Code für den Seiteninhalt festgelegt haben.

Das zweite [**VisualState**](https://msdn.microsoft.com/library/windows/apps/BR209007)-Element `narrowState` verfügt über ein [**AdaptiveTrigger**](https://msdn.microsoft.com/library/windows/apps/Dn890382)-Element, für das die [**MinWindowWidth**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.adaptivetrigger.minwindowwidth)-Eigenschaft auf0 festgelegt ist. Dieser Zustand wird angewendet, wenn die Fensterbreite größer0, aber kleiner als 641DIP ist. (Bei 641DIP wird `wideState` angewendet.) In diesem Zustand definieren Sie einige [**Setter**](https://msdn.microsoft.com/library/windows/apps/BR208817)-Objekte, um die Layouteigenschaften der Steuerelemente in der UI zu ändern:

-   Verringern Sie den linken Rand des `contentPanel`-Elements von120 auf20.
-   Ändern Sie das [**Orientation**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.stackpanel.orientation)-Element des `inputPanel`-Elements von **Horizontal** in **Vertical**.
-   Fügen Sie dem `inputButton`-Element einen oberen Rand mit einer Breite von 4DIP hinzu.

### <a name="summary"></a>Zusammenfassung

Herzlichen Glückwunsch! Sie haben das erste Lernprogramm abgeschlossen. Darin haben Sie gelernt, wie Sie Inhalte zu universellen Windows-Apps hinzufügen, wie Sie sie interaktiv machen und wie Sie ihr Erscheinungsbild ändern.

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie ein universelle Windows-app-Projekt, das Windows8.1 und/oder Windows Phone 8.1 ausgerichtet ist verfügen, können Sie es zu Windows 10 portieren. Es gibt keinen automatischen Prozess dafür, Sie können das Projekt jedoch manuell portieren. Beginnen Sie mit einem neuen universellen Windows-Projekt, um die aktuelle Projektsystemstruktur und Manifestdateien abzurufen. Kopieren Sie dann die Codedateien in die Verzeichnisstruktur des Projekts, fügen Sie Ihrem Projekt Elemente hinzu, und schreiben Sie Ihren XAML-Code mithilfe von [**VisualStateManager**](https://msdn.microsoft.com/library/windows/apps/BR209021) gemäß den Anweisungen in diesem Thema um. Weitere Informationen finden Sie unter [Portieren eines Windows-Runtime 8-Projekts zu einem UWP-Projekt (Universelle Windows-Plattform)](https://msdn.microsoft.com/library/windows/apps/Mt188203) sowie unter [Portieren zur Universellen Windows-Plattform (C++)](http://go.microsoft.com/fwlink/p/?LinkId=619525).

Wenn Sie über C++-Code verfügen, den Sie mit einer UWP-App integrieren möchten, um beispielsweise eine neue UWP-Benutzeroberfläche für eine vorhandene Anwendung zu erstellen, finden Sie unter [Gewusst wie: Verwenden von vorhandenem C++-Code in einem universellen Windows-Projekt](http://go.microsoft.com/fwlink/p/?LinkId=619623) entsprechende Anweisungen dazu.

