---
description: Dieses Thema zeigt, wie man Event-Handling-Delegaten mit C++/WinRT registriert und widerruft.
title: Verarbeiten von Ereignissen über Delegaten in C++/WinRT
ms.date: 05/07/2018
ms.topic: article
keywords: windows 10, uwp, standard, c++, cpp, winrt, projiziert, projizierung, varbeiten, ereignis, delegat
ms.localizationpriority: medium
ms.openlocfilehash: f30ff39b0dcb54cd50808381bcb30e58e7dfe07d
ms.sourcegitcommit: b4c502d69a13340f6e3c887aa3c26ef2aeee9cee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "8484337"
---
# <a name="handle-events-by-using-delegates-in-cwinrt"></a>Verarbeiten von Ereignissen über Delegaten in C++/WinRT

Dieses Thema zeigt, wie Sie registriert und widerruft Event-Handling-Delegaten mit [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt). Sie können ein Ereignis mit jedem Objekt verarbeiten, das einer normalen C++ Funktion entspricht.

> [!NOTE]
> Informationen zur Installation und Verwendung der C++/WinRT Visual Studio Extension (VSIX) (die Projektvorlagenunterstützung sowie C++/WinRT MSBuild-Eigenschaften und -Ziele bietet) finden Sie unter [Visual Studio-Unterstützung für C++/WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).

## <a name="register-a-delegate-to-handle-an-event"></a>Einen Delegaten für die Verarbeitung eines Ereignisses registrieren

Ein einfaches Beispiel ist die Verarbeitung des Klickereignisses einer Schaltfläche. Es ist typisch, XAML-Markup zu verwenden, um eine Member-Funktion zu registrieren, um das Ereignis wie folgt zu verarbeiten.

```xaml
// MainPage.xaml
<Button x:Name="Button" Click="ClickHandler">Click Me</Button>
```

```cppwinrt
// MainPage.cpp
void MainPage::ClickHandler(IInspectable const& /* sender */, RoutedEventArgs const& /* args */)
{
    Button().Content(box_value(L"Clicked"));
}
```

Anstatt dies im Markup zu deklarieren, können Sie explizit eine Member-Funktion registrieren, um ein Ereignis zu verarbeiten. Es mag nicht offensichtlich sein, aber das Argument für den [**ButtonBase::Click**](/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.click)-Aufruf ist eine Instanz des [**RoutedEventHandler**](/uwp/api/windows.ui.xaml.routedeventhandler)-Delegaten. In diesem Fall verwenden wir die Überladung des **RoutedEventHandler**-Konstruktors, die ein Objekt und eine Pointer-to-Member-Funktion benötigt.

```cppwinrt
// MainPage.cpp
MainPage::MainPage()
{
    InitializeComponent();

    Button().Click({ this, &MainPage::ClickHandler });
}
```

> [!IMPORTANT]
> Wenn der Delegat registriert, übergibt im obigen Codebeispiel wird einen unformatierte *diesem* Zeiger (zeigen Sie auf das aktuelle Objekt). Um zu erfahren, wie Sie eine starke oder schwache Referenz auf das aktuelle Objekt herzustellen, finden Sie **bei Verwendung von eine Member-Funktion als Delegaten** untergeordnete im Abschnitt Abschnitt [problemlos den Zugriff auf die *dieser* Zeiger mit einem Delegaten für die Ereignisbehandlung](weak-references.md#safely-accessing-the-this-pointer-with-an-event-handling-delegate).

Es gibt andere Möglichkeiten, ein **RoutedEventHandler** zu erstellen. Unten finden Sie den Syntaxblock aus dem Dokumentationsthema für [**RoutedEventHandler**](/uwp/api/windows.ui.xaml.routedeventhandler) (wählen Sie *C++/WinRT* im Dropdown-Menü **Sprache** auf der Seite aus). Beachten Sie die verschiedenen Konstruktoren: Einer nimmt ein Lambda entgegen (ein anderer eine freie Funktion) und ein weiterer (der oben verwendete) nimmt ein Objekt und eine Pointer-to-Member-Funktion entgegen.

```cppwinrt
struct RoutedEventHandler : winrt::Windows::Foundation::IUnknown
{
    RoutedEventHandler(std::nullptr_t = nullptr) noexcept;
    template <typename L> RoutedEventHandler(L lambda);
    template <typename F> RoutedEventHandler(F* function);
    template <typename O, typename M> RoutedEventHandler(O* object, M method);
    void operator()(winrt::Windows::Foundation::IInspectable const& sender,
        winrt::Windows::UI::Xaml::RoutedEventArgs const& e) const;
};
```

Die Syntax des Funktionsaufrufoperators ist ebenfalls hilfreich. Sie sagt Ihnen, welche Parameter Ihr Delegat haben muss. Wie Sie sehen, entspricht in diesem Fall die Syntax des Funktionsaufrufoperators den Parametern unseres **MainPage::ClickHandler**.

Wenn Sie nicht viel in Ihrem Ereignis-Handler erledigen, dann können Sie eine Lambda-Funktion anstelle einer Mitgliedsfunktion verwenden. Auch hier ist es vielleicht nicht offensichtlich, aber ein **RoutedEventHandler**-Delegat wird aus einer Lambda-Funktion erstellt, die wiederum der Syntax des Funktionsaufrufoperators entsprechen muss.

```cppwinrt
MainPage::MainPage()
{
    InitializeComponent();

    Button().Click([this](IInspectable const& /* sender */, RoutedEventArgs const& /* args */)
    {
        Button().Content(box_value(L"Clicked"));
    });
}
```

Sie können sich dafür entscheiden, etwas konkreter zu werden, wenn Sie Ihren Delegaten konstruieren. Beispielsweise bei der Weitergabe oder der mehrfachen Verwendung.

```cppwinrt
MainPage::MainPage()
{
    InitializeComponent();

    auto click_handler = [](IInspectable const& sender, RoutedEventArgs const& /* args */)
    {
        sender.as<winrt::Windows::UI::Xaml::Controls::Button>().Content(box_value(L"Clicked"));
    };
    Button().Click(click_handler);
    AnotherButton().Click(click_handler);
}
```

## <a name="revoke-a-registered-delegate"></a>Einen registrierten Delgaten widerrufen

Wenn Sie einen Deleganten registrieren, wird Ihnen in der Regel ein Token zurückgegeben. Mit diesem Token können Sie anschließend Ihren Delegaten widerrufen, d. h. die Registrierung des Delegaten für das Ereignis wird aufgehoben. Er wird nicht mehr aufgerufen, wenn das Ereignis erneut ausgelöst wird. Der Einfachheit halber hat keines der obigen Codebeispiele gezeigt, wie das geht. Das nächste Codebeispiel speichert das Token jedoch im privaten Datenelement der Struktur und widerruft seinen Handler im Destruktor.

```cppwinrt
struct Example : ExampleT<Example>
{
    Example(winrt::Windows::UI::Xaml::Controls::Button const& button) : m_button(button)
    {
        m_token = m_button.Click([this](IInspectable const&, RoutedEventArgs const&)
        {
            // ...
        });
    }
    ~Example()
    {
        m_button.Click(m_token);
    }

private:
    winrt::Windows::UI::Xaml::Controls::Button m_button;
    winrt::event_token m_token;
};
```

Anstatt eines starken Verweises wie im obigen Beispiel können Sie einen schwachen Verweis auf die Schaltfläche Speichern (siehe [starke und schwache Referenzen in C++ / WinRT](weak-references.md)).

Wenn Sie einen deleganten registrieren, können Sie auch angeben **WinRT:: auto_revoke** (den Typ [**WinRT:: auto_revoke_t**](/uwp/cpp-ref-for-winrt/auto-revoke-t)Wert) um einen Event-Revoker (vom Typ [**event_revoker**](/uwp/cpp-ref-for-winrt/event-revoker)) anzufordern. Der Event-Revoker enthält einen schwachen Verweis auf die Ereignisquelle (das Objekt, das das Ereignis auslöst) für Sie. Sie können manuell widerrufen, indem Sie die Mitgliedsfunktion **event_revoker::revoke** aufrufen; der Event-Revoker ruft diese Funktion aber selbst automatisch auf, wenn sie ihren Gültigkeitsbereich verlässt. Die **revoke**-Funktion überprüft, ob die Ereignisquelle noch vorhanden ist, und widerruft in diesem Fall den Delegaten. In diesem Beispiel gibt es keine Notwendigkeit, die Ereignisquelle zu speichern, und daher auch keinen Bedarf für einen Destruktor.

```cppwinrt
struct Example : ExampleT<Example>
{
    Example(winrt::Windows::UI::Xaml::Controls::Button button)
    {
        m_event_revoker = button.Click(winrt::auto_revoke, [this](IInspectable const& /* sender */, RoutedEventArgs const& /* args */)
        {
            // ...
        });
    }

private:
    winrt::Windows::UI::Xaml::Controls::Button::Click_revoker m_event_revoker;
};
```

Unten ist der Syntaxblock aus dem Dokumentationsthema für das [**ButtonBase::Click**](/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.click)-Ereignis zu sehen. Es zeigt die drei verschiedenen Registrierungs- und Widerrufsfunktionen. Sie können genau sehen, welche Art von Event-Revoker Sie für die dritten Überladung deklarieren müssen.

```cppwinrt
// Register
winrt::event_token Click(winrt::Windows::UI::Xaml::RoutedEventHandler const& handler) const;

// Revoke with event_token
void Click(winrt::event_token const& token) const;

// Revoke with event_revoker
Button::Click_revoker Click(winrt::auto_revoke_t,
    winrt::Windows::UI::Xaml::RoutedEventHandler const& handler) const;
```

> [!NOTE]
> Im obigen Codebeispiel `Button::Click_revoker` ist ein Typalias für `winrt::event_revoker<winrt::Windows::UI::Xaml::Controls::Primitives::IButtonBase>`. Ein ähnliches Muster gilt für alle C++/WinRT-Ereignisse. Jedes Windows-Runtime-Ereignis verfügt über eine Überladung der Revoke-Funktion, die einen Event-Revoker zurückgibt, und Revoker Typ ist ein Mitglied der Ereignisquelle. Um ein weiteres Beispiel zu nutzen, hat das [**corewindow:: SizeChanged**](/uwp/api/windows.ui.core.corewindow.sizechanged) -Ereignis also eine Überladung der Registrierung-Funktion, die einen Wert vom Typ **CoreWindow::SizeChanged_revoker**zurückgibt.


In einem Seitennavigationsszenario kann es sinnvoll sein, Handler zu widerrufen. Wenn Sie wiederholt auf eine Seite navigieren und diese dann wieder verlassen, können Sie alle Handler widerrufen, wenn Sie von der Seite weg navigieren. Wenn Sie dieselbe Seiteninstanz wiederverwenden, dann überprüfen Sie alternativ den Wert Ihres Tokens und registrieren Sie sich nur, wenn er noch nicht festgelegt ist (`if (!m_token){ ... }`). Eine dritte Möglichkeit besteht darin, einen Event-Revoker als Datenelement der Seite zu speichern. Und eine vierte Möglichkeit (wird später in diesem Thema beschrieben) besteht darin, eine starke oder schwache Referenz auf das *this*-Objekt in Ihrer Lambda-Funktion zu verwenden.

## <a name="delegate-types-for-asynchronous-actions-and-operations"></a>Delegattypen für asynchrone Aktionen und Vorgänge

Die obigen Beispiele verwenden den Delegattyp **RoutedEventHandler**, aber es gibt natürlich auch viele andere Delegattypen. Beispielsweise haben asynchrone Aktionen und Vorgänge (mit und ohne Fortschritt) Completed- und/oder Progress-Ereignisse, die Delegaten des entsprechenden Typs erwarten. Beispielsweise erfordert das Progress-Ereignis eines asynchronen Vorgangs mit Fortschritt (betrifft alles, das [**IAsyncOperationWithProgress**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_) implementiert) einen Delegaten vom Typ [**AsyncOperationProgressHandler**](/uwp/api/windows.foundation.asyncoperationprogresshandler). Hier ist ein Codebeispiel für die Erstellung eines solchen Delegaten mit einer Lambda-Funktion. Das Beispiel zeigt auch, wie man einen [**AsyncOperationWithProgressCompletedHandler**](/uwp/api/windows.foundation.asyncoperationwithprogresscompletedhandler)-Delegaten erstellt.

```cppwinrt
using namespace winrt;
using namespace Windows::Foundation;
using namespace Windows::Web::Syndication;

void ProcessFeedAsync()
{
    Uri rssFeedUri{ L"https://blogs.windows.com/feed" };
    SyndicationClient syndicationClient;

    auto async_op_with_progress = syndicationClient.RetrieveFeedAsync(rssFeedUri);

    async_op_with_progress.Progress(
        [](IAsyncOperationWithProgress<SyndicationFeed, RetrievalProgress> const& /* sender */, RetrievalProgress const& args)
    {
        uint32_t bytes_retrieved = args.BytesRetrieved;
        // use bytes_retrieved;
    });

    async_op_with_progress.Completed(
        [](IAsyncOperationWithProgress<SyndicationFeed, RetrievalProgress> const& sender, AsyncStatus const /* asyncStatus */)
    {
        SyndicationFeed syndicationFeed = sender.GetResults();
        // use syndicationFeed;
    });
    
    // or (but this function must then be a coroutine, and return IAsyncAction)
    // SyndicationFeed syndicationFeed{ co_await async_op_with_progress };
}
```

Wie aus dem obigen „coroutine“-Kommentar hervorgeht, werden Sie es wahrscheinlich natürlicher finden, Coroutinen zu verwenden, anstatt einen Delegaten für die Completed-Ereignisse asynchroner Aktionen und Vorgänge zu verwenden. Details und Codebeispiele finden Sie unter [Parallelität und asynchrone Vorgänge mit C++/WinRT](concurrency.md).

> [!NOTE]
> Es ist nicht korrekt auf mehr als ein *Abschlusshandler* für eine asynchrone Aktion oder Operation implementieren. Sie können entweder einen einzelnen Delegaten für das abgeschlossene Ereignis haben, oder Sie können `co_await` es. Wenn Sie beide haben, wird die zweite fehl.

Wenn Sie an Delegaten anstelle einer Coroutine, können Sie für eine einfachere Syntax ablehnen.

```cppwinrt
async_op_with_progress.Completed(
    [](auto&& /*sender*/, AsyncStatus const /* args */)
{
    // ...
});
```

## <a name="delegate-types-that-return-a-value"></a>Delegattypen, die einen Wert zurückgeben

Einige Delegattypen müssen selbst einen Wert zurückgeben. Ein Beispiel ist [**ListViewItemToKeyHandler**](/uwp/api/windows.ui.xaml.controls.listviewitemtokeyhandler), der einen String zurückgibt. Hier ist ein Beispiel für die Erstellung eines solchen Delegaten (beachten Sie, dass die Lambda-Funktion einen Wert zurückgibt).

```cppwinrt
using namespace winrt::Windows::UI::Xaml::Controls;

winrt::hstring f(ListView listview)
{
    return ListViewPersistenceHelper::GetRelativeScrollPosition(listview, [](IInspectable const& item)
    {
        return L"key for item goes here";
    });
}
```

## <a name="safely-accessing-the-this-pointer-with-an-event-handling-delegate"></a>Problemlos den Zugriff auf die *dieser* Zeiger mit einem Delegaten für die Ereignisbehandlung

Wenn Sie ein Ereignis mit Mitgliedsfunktion eines Objekts verarbeiten oder von innerhalb einer Lambda-Funktion innerhalb eines Objekts Member-Funktion, Sie über die relative Lebensdauer des Ereignisempfängers (das Objekt, das das Ereignis behandelt) und die Ereignisquelle (das Objekt vorstellen müssen das Ereignis auslöst). Weitere Informationen und Codebeispiele finden Sie unter [starke und schwache Referenzen in C++ / WinRT](weak-references.md#safely-accessing-the-this-pointer-with-an-event-handling-delegate).

## <a name="important-apis"></a>Wichtige APIs
* [WinRT:: auto_revoke_t markerstruktur](/uwp/cpp-ref-for-winrt/auto-revoke-t)
* [winrt::implements::get_weak-Funktion](/uwp/cpp-ref-for-winrt/implements#implementsgetweak-function)
* [winrt::implements::get_strong-Funktion](/uwp/cpp-ref-for-winrt/implements#implementsgetstrong-function)

## <a name="related-topics"></a>Verwandte Themen
* [Erstellen von Ereignissen mit C++/WinRT](author-events.md)
* [Parallelität und asynchrone Vorgänge mit C++/WinRT](concurrency.md)
* [Starke und schwache Referenzen in C++ / WinRT](weak-references.md)
