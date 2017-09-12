---
author: mijacobs
Description: "Die Navigation in UWP-Apps (Apps für die Universelle Windows-Plattform) basiert auf einem flexiblen Modell aus Navigationsstrukturen, Navigationselementen und Funktionen auf Systemebene."
title: "Navigationsverlauf und Rückwärtsnavigation (Windows-Apps)"
ms.assetid: e9876b4c-242d-402d-a8ef-3487398ed9b3
isNew: True
label: History and backwards navigation
template: detail.hbs
op-migration-status: ready
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: cd3184ebe5e94c410d55a725129a38907aa6a01e
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
#  <a name="navigation-history-and-backwards-navigation-for-uwp-apps"></a>Navigationsverlauf und Rückwärtsnavigation für UWP-Apps

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

Im Internet stellen die einzelnen Websites eigene Navigationssysteme bereit, beispielsweise Inhaltsverzeichnis, Schaltflächen, Menüs, einfache Listen mit Links usw. Die Navigationsfunktionalität kann je nach Website stark variieren. Es gibt jedoch eine konsistente Navigationsfunktion: Zurück. Die meisten Browser bieten eine Zurück-Schaltfläche, die unabhängig von der Website das gleiche Verhalten aufweist.

> **Wichtige APIs**: [SystemNavigationManager-Klasse](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Core.SystemNavigationManager), [BackRequested-Ereignis](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Core.SystemNavigationManager#Windows_UI_Core_SystemNavigationManager_BackRequested), [OnNavigatedTo](https://msdn.microsoft.com/library/windows/apps/br227508)

Ähnlichen Gründen enthält die universelle Windows-Plattform (UWP) ein einheitliches System zur Rückwärtsnavigation, mit dem der Navigationsverlauf des Benutzers innerhalb einer App und je nach Gerät von App zu App durchlaufen werden kann.

Die Benutzeroberfläche für die Systemschaltfläche "Zurück" ist für jeden Formfaktor und Eingabegerätetyp optimiert. Die Navigationsfunktionalität hingegen ist auf allen Geräten und UWP-Apps global und einheitlich gültig.

Im Folgenden sind die primären Formfaktoren für die Zurück-Schaltfläche der Benutzeroberfläche aufgeführt:


<table>
    <tr>
        <td colspan="2">Geräte</td>
        <td style="vertical-align:top;">Verhalten der Zurück-Schaltfläche</td>
     </tr>
    <tr>
        <td style="vertical-align:top;">Telefon</td>
        <td style="vertical-align:top;">![Zurück-Funktion des Systems auf einem Smartphone](images/back-systemback-phone.png)</td>
        <td style="vertical-align:top;">
        <ul>
<li>Immer vorhanden.</li>
<li>Eine Software- oder Hardwareschaltfläche am unteren Rand des Geräts.</li>
<li>Globale Rückwärtsnavigation innerhalb der App und zwischen Apps.</li>
</ul>
</td>
     </tr>
     <tr>
        <td style="vertical-align:top;">Tablet</td>
        <td style="vertical-align:top;">![Zurück-Funktion des Systems auf einem Tablet (im Tablet-Modus)](images/back-systemback-tablet.png)</td>
        <td style="vertical-align:top;">
<ul>
<li>Im Tablet-Modus immer vorhanden. In Desktopmodus nicht verfügbar. Stattdessen kann die Zurück-Schaltfläche in der Titelleiste aktiviert werden. Weitere Infos finden Sie unter [PC, Laptop, Tablet](#PC).
Benutzer können zwischen dem Tablet- und dem Desktopmodus wechseln, indem sie unter **Einstellungen &gt; System &gt; Tablet-Modus** die Option **Durch die Verwendung des Geräts als Tablet wird die Toucheingabe in Windows verbessert** aktivieren.</li>
<li> Eine Softwareschaltfläche in der Navigationsleiste am unteren Rand des Geräts.</li>
<li>Globale Rückwärtsnavigation innerhalb der App und zwischen Apps.</li></ul>        
        </td>
     </tr>
    <tr>
        <td style="vertical-align:top;">PC, Laptop, Tablet</td>
        <td style="vertical-align:top;">![Zurück-Funktion des Systems auf einem PC oder Laptop](images/back-systemback-pc.png)</td>
        <td style="vertical-align:top;">
<ul>
<li>Optional im Desktopmodus. Im Tablet-Modus nicht verfügbar. Weitere Infos finden Sie unter [Tablet](#Tablet). Standardmäßig deaktiviert. Muss zur Verwendung aktiviert werden.
Benutzer können zwischen dem Tablet- und dem Desktopmodus wechseln, indem sie unter **Einstellungen &gt; System &gt; Tablet-Modus** die Option **Durch die Verwendung des Geräts als Tablet wird die Toucheingabe in Windows verbessert** aktivieren.</li>
<li>Eine Softwareschaltfläche in der Titelleiste der App.</li>
<li>Ermöglicht die Rückwärtsnavigation nur innerhalb der App. Unterstützt keine App-zu-App-Navigation.</li></ul>        
        </td>
     </tr>
    <tr>
        <td style="vertical-align:top;">Surface Hub</td>
        <td style="vertical-align:top;">![Zurück-Funktion des Systems auf einem Surface Hub](images/nav/nav-back-surfacehub.png)</td>
        <td style="vertical-align:top;">
<ul>
<li>Optional.</li>
<li>Standardmäßig deaktiviert. Muss zur Verwendung aktiviert werden.</li>
<li>Eine Softwareschaltfläche in der Titelleiste der App.</li>
<li>Ermöglicht die Rückwärtsnavigation nur innerhalb der App. Unterstützt keine App-zu-App-Navigation.</li></ul>        
        </td>
     </tr>     
<table>


Hier sind einige alternative Eingabetypen, die keine Zurück-Schaltfläche auf der Benutzeroberfläche erfordern, aber dieselbe Funktionalität bieten.


<table>
<tr><td colspan="3">Eingabegeräte</td></tr>
<tr><td style="vertical-align:top;">Tastatur</td><td style="vertical-align:top;">![Tastatur](images/keyboard-wireframe.png)</td><td style="vertical-align:top;">Windows-Taste + RÜCKTASTE</td></tr>
<tr><td style="vertical-align:top;">Cortana</td><td style="vertical-align:top;">![Spracherkennung](images/speech-wireframe.png)</td><td style="vertical-align:top;">Sagen Sie „Hey Cortana, zurück.“</td></tr>
</table>
 

Wenn Ihre App auf einem Smartphone, Tablet, oder einem PC bzw. Laptop mit aktivierter Zurück-Funktion des Systems ausgeführt wird, informiert das System Ihre App darüber, wenn die Zurück-Schaltfläche gedrückt wird. Der Benutzer erwartet, dass durch Drücken der Zurück-Schaltfläche die vorherige Seite im Navigationsverlauf der App aufgerufen wird. Sie können entscheiden, welche Navigationsaktionen dem Navigationsverlauf hinzugefügt werden sollen und wie auf das Drücken der Zurück-Schaltfläche reagiert werden soll.


## <a name="how-to-enable-system-back-navigation-support"></a>Aktivieren der Unterstützung für die System-Rückwärtsnavigation


Apps müssen die Rückwärtsnavigation für alle Hardware- und Software-Zurück-Systemschaltflächen aktivieren. Dazu registrieren Sie einen Listener für das [**BackRequested**](https://msdn.microsoft.com/library/windows/apps/dn893596)-Ereignis und definieren einen entsprechenden Handler.

Hier registrieren wir einen globalen Listener für das [**BackRequested**](https://msdn.microsoft.com/library/windows/apps/dn893596)-Ereignis in der CodeBehind-Datei für App.xaml. Sie können sich für dieses Ereignis auf jeder Seite registrieren, wenn Sie bestimmte Seiten aus der Rückwärtsnavigation ausschließen oder vor dem Anzeigen der Seite Seitenebenencode ausführen möchten.

> [!div class="tabbedCodeSnippets"]
```csharp
Windows.UI.Core.SystemNavigationManager.GetForCurrentView().BackRequested += 
    App_BackRequested;
```
```cpp
Windows::UI::Core::SystemNavigationManager::GetForCurrentView()->
    BackRequested += ref new Windows::Foundation::EventHandler<
    Windows::UI::Core::BackRequestedEventArgs^>(
        this, &App::App_BackRequested);
```

Das ist der entsprechende [**BackRequested**](https://msdn.microsoft.com/library/windows/apps/dn893596)-Ereignishandler, der [**GoBack**](https://msdn.microsoft.com/library/windows/apps/dn996568) im Stammframe der App aufruft.

Dieser Handler wird für ein globales Zurück-Ereignis aufgerufen. Wenn der In-App-Zurück-Stapel leer ist, navigiert das System ggf. zur vorherigen App im App-Stapel oder zum Startbildschirm zurück. Im Desktopmodus gibt es keinen App-Zurück-Stapel, und der Benutzer bleibt selbst dann in der App, wenn der In-App-Zurück-Stapel leer ist.

> [!div class="tabbedCodeSnippets"]
```csharp
>private void App_BackRequested(object sender, 
>    Windows.UI.Core.BackRequestedEventArgs e)
>{
>    Frame rootFrame = Window.Current.Content as Frame;
>    if (rootFrame == null)
>        return;
>
>    // Navigate back if possible, and if the event has not 
>    // already been handled .
>    if (rootFrame.CanGoBack && e.Handled == false)
>    {
>        e.Handled = true;
>        rootFrame.GoBack();
>    }
>}
```
```cpp
>void App::App_BackRequested(
>    Platform::Object^ sender, 
>    Windows::UI::Core::BackRequestedEventArgs^ e)
>{
>    Frame^ rootFrame = dynamic_cast<Frame^>(Window::Current->Content);
>    if (rootFrame == nullptr)
>        return;
>
>    // Navigate back if possible, and if the event has not
>    // already been handled.
>    if (rootFrame->CanGoBack && e->Handled == false)
>    {
>        e->Handled = true;
>        rootFrame->GoBack();
>    }
>}
```

## <a name="how-to-enable-the-title-bar-back-button"></a>Aktivieren der Schaltfläche „Zurück“ auf der Titelleiste


Geräte, die den Desktopmodus unterstützen (in der Regel PCs und Laptops, aber auch einige Tablets) und auf denen die Einstellung (**Einstellungen &gt; System &gt; Tablet-Modus**) aktiviert ist, bieten keine globale Navigationsleiste mit der Systemschaltfläche „Zurück“.

Im Desktopmodus wird jede App in einem Fenster mit Titelleiste ausgeführt. Sie können eine alternative Zurück-Schaltfläche für Ihre App bereitstellen, die in dieser Titelleiste angezeigt wird.

Die Titelleisten-Zurück-Schaltfläche ist nur in Apps verfügbar, die auf Geräten im Desktop-Modus ausgeführt werden. Sie unterstützt nur den In-App-Navigationsverlauf. Der App-zu-App-Navigationsverlauf wird nicht unterstützt.

**Wichtig**  Die Schaltfläche „Zurück“ der Titelleiste wird standardmäßig nicht angezeigt. Sie müssen sie aktivieren.

 

|                                                             |                                                        |
|-------------------------------------------------------------|--------------------------------------------------------|
| ![Keine Zurück-Systemschaltfläche im Desktopmodus](images/nav-noback-pc.png) | ![Zurück-Systemschaltfläche im Desktopmodus](images/nav-back-pc.png) |
| Desktopmodus, keine Rückwärtsnavigation.                           | Desktopmodus, Rückwärtsnavigation aktiviert.                 |

 

Überschreiben Sie das [**OnNavigatedTo**](https://msdn.microsoft.com/library/windows/apps/br227508)-Ereignis, und legen Sie [**AppViewBackButtonVisibility**](https://msdn.microsoft.com/library/windows/apps/dn986448) in der CodeBehind-Datei für jede Seite in Ihrer App auf [**Visible**](https://msdn.microsoft.com/library/windows/apps/dn986276) fest, für die Sie die Titelleisten-Zurück-Schaltfläche aktivieren möchten.

Für dieses Beispiel wird jede Seite im Zurück-Stapel aufgelistet und die Zurück-Schaltfläche aktiviert, wenn die [**CanGoBack**](https://msdn.microsoft.com/library/windows/apps/br242685)-Eigenschaft des Frames den Wert **true** aufweist.

> [!div class="tabbedCodeSnippets"]
>```csharp
>protected override void OnNavigatedTo(NavigationEventArgs e)
>{
>    Frame rootFrame = Window.Current.Content as Frame;
>
>    string myPages = "";
>    foreach (PageStackEntry page in rootFrame.BackStack)
>    {
>        myPages += page.SourcePageType.ToString() + "\n";
>    }
>    stackCount.Text = myPages;
>
>    if (rootFrame.CanGoBack)
>    {
>        // Show UI in title bar if opted-in and in-app backstack is not empty.
>        SystemNavigationManager.GetForCurrentView().AppViewBackButtonVisibility = 
>            AppViewBackButtonVisibility.Visible;
>    }
>    else
>    {
>        // Remove the UI from the title bar if in-app back stack is empty.
>        SystemNavigationManager.GetForCurrentView().AppViewBackButtonVisibility = 
>            AppViewBackButtonVisibility.Collapsed;
>    }
>}
>```
>```cpp
>void StartPage::OnNavigatedTo(NavigationEventArgs^ e)
>{
>    auto rootFrame = dynamic_cast<Windows::UI::Xaml::Controls::Frame^>(Window::Current->Content);
>
>    Platform::String^ myPages = "";
>
>    if (rootFrame == nullptr)
>        return;
>
>    for each (PageStackEntry^ page in rootFrame->BackStack)
>    {
>        myPages += page->SourcePageType.ToString() + "\n";
>    }
>    stackCount->Text = myPages;
>
>    if (rootFrame->CanGoBack)
>    {
>        // If we have pages in our in-app backstack and have opted in to showing back, do so
>        Windows::UI::Core::SystemNavigationManager::GetForCurrentView()->AppViewBackButtonVisibility =
>            Windows::UI::Core::AppViewBackButtonVisibility::Visible;
>    }
>    else
>    {
>        // Remove the UI from the title bar if there are no pages in our in-app back stack
>        Windows::UI::Core::SystemNavigationManager::GetForCurrentView()->AppViewBackButtonVisibility =
>            Windows::UI::Core::AppViewBackButtonVisibility::Collapsed;
>    }
>}
>```


### <a name="guidelines-for-custom-back-navigation-behavior"></a>Richtlinien für das benutzerdefinierte Verhalten der Rückwärtsnavigation

Wenn Sie Ihre eigene Zurück-Stapelnavigation bereitstellen möchten, sollte die Benutzeroberfläche mit anderen Apps konsistent sein. Wir empfehlen, die folgenden Muster für Navigationsaktionen zu verwenden:

<table>
<thead>
<tr class="header">
<th align="left">Navigationsaktion</th>
<th align="left">Zum Navigationsverlauf hinzufügen?</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="vertical-align:top;"><strong>Seite zu Seite, verschiedene Peer-Gruppen</strong></td>
<td style="vertical-align:top;"><strong>Ja</strong>
<p>In der folgenden Abbildung navigiert der Benutzer von Ebene 1 der App zu Ebene 2. Dabei werden Peer-Gruppen durchlaufen, sodass die Navigation dem Navigationsverlauf hinzugefügt wird.</p>
<p><img src="images/nav/nav-pagetopage-diffpeers-imageonly1.png" alt="Navigation across peer groups" /></p>
<p>In der nächsten Abbildung navigiert der Benutzer zwischen zwei Peer-Gruppen derselben Ebene. Er durchläuft erneut Peer-Gruppen, sodass die Navigation dem Navigationsverlauf hinzugefügt wird.</p>
<p><img src="images/nav/nav-pagetopage-diffpeers-imageonly2.png" alt="Navigation across peer groups" /></p></td>
</tr>
<tr class="even">
<td style="vertical-align:top;"><strong>Seite zu Seite, gleiche Peer-Gruppe, kein Bildschirmnavigationselement</strong>
<p>Der Benutzer navigiert von einer Seite zu einer anderen mit derselben Peer-Gruppe. Es gibt kein Navigationselement, das immer vorhanden ist (wie Registerkarten/Pivots oder ein angedockter Navigationsbereich) und das eine direkte Navigation zu beiden Seiten ermöglicht.</p></td>
<td style="vertical-align:top;"><strong>Ja</strong>
<p>In der folgenden Abbildung navigiert der Benutzer zwischen zwei Seiten in derselben Peer-Gruppe. Die Seiten verwenden keine Registerkarten oder angedockten Navigationsbereich, sodass die Navigation dem Navigationsverlauf hinzugefügt wird.</p>
<p><img src="images/nav/nav-pagetopage-samepeer-noosnavelement.png" alt="Navigation within a peer group" /></p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top;"><strong>Seite zu Seite, gleiche Peer-Gruppe, mit einem Bildschirmnavigationselement</strong>
<p>Der Benutzer navigiert von einer Seite zu einer anderen in derselben Peer-Gruppe. Beide Seiten werden im gleichen Navigationselement angezeigt. Beide Seiten verwenden beispielsweise das gleiche Registerkarten/Pivots-Element, oder beide Seiten werden in einem angedockten Navigationsbereich angezeigt.</p></td>
<td style="vertical-align:top;"><strong>Nein</strong>
<p>Wenn der Benutzer die Zurück-Schaltfläche drückt, wird wieder die letzte Seite aufgerufen, die geöffnet war, bevor der Benutzer zur aktuellen Peer-Gruppe navigierte.</p>
<p><img src="images/nav/nav-pagetopage-samepeer-yesosnavelement.png" alt="Navigation across peer groups when a navigation element is present" /></p></td>
</tr>
<tr class="even">
<td style="vertical-align:top;"><strong>Anzeigen einer vorübergehenden Benutzeroberfläche</strong>
<p>Die App zeigt ein Popupfenster oder ein untergeordnetes Fenster an, z. B. ein Dialogfeld, einen Begrüßungsbildschirm oder eine Bildschirmtastatur. Anderenfalls wechselt die App in einen speziellen Modus, z. B. den Mehrfachauswahlmodus.</p></td>
<td style="vertical-align:top;"><strong>Nein</strong>
<p>Wenn der Benutzer die Zurück-Schaltfläche drückt, sollte die vorübergehende Benutzeroberfläche geschlossen werden (durch Ausblenden der Bildschirmtastatur, Abbrechen des Dialogfelds usw.) und zur Seite zurückgekehrt werden, die die vorübergehende Benutzeroberfläche aufgerufen hat.</p>
<p><img src="images/back-transui.png" alt="Showing a transient UI" /></p></td>
</tr>
<tr class="odd">
<td style="vertical-align:top;"><strong>Aufzählen von Elementen</strong>
<p>Die App zeigt die Inhalte für ein Bildschirmelement an, z. B. die Details für das ausgewählte Element in der Master/Details-Liste.</p></td>
<td style="vertical-align:top;"><strong>Nein</strong>
<p>Das Aufzählen von Elementen ist mit der Navigation innerhalb einer Peer-Gruppe vergleichbar. Wenn der Benutzer die Zurück-Schaltfläche drückt, sollte zu der Seite navigiert werden, die vor der aktuellen Seite angezeigt wurde, die die Elementenaufzählung enthält.</p>
<img src="images/nav/nav-enumerate.png" alt="Iterm enumeration" /></td>
</tr>
</tbody>
</table>


### <a name="resuming"></a>Fortsetzen

Wenn der Benutzer zu einer anderen App wechselt und zu Ihrer App zurückkehrt, wird empfohlen, zur letzten Seite im Navigationsverlauf zurückzukehren.


## <a name="get-the-samples"></a>Beispiele herunterladen
*   [Beispiel für die Zurück-Schaltfläche](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/BackButton)<br/>
    Zeigt, wie Sie einen Ereignishandler für das Ereignis Zurück-Schaltfläche einrichten und die Titelleisten-Zurück-Schaltfläche aktivieren, wenn sich die App im Fensterdesktopmodus befindet.

## <a name="related-articles"></a>Verwandte Artikel
* [Navigationsgrundlagen](navigation-basics.md)

 




