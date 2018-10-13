---
author: stevewhims
description: Dieses Thema zeigt, wie man Event-Handling-Delegaten mit C++/WinRT registriert und widerruft.
title: Verarbeiten von Ereignissen über Delegaten in C++/WinRT
ms.author: stwhi
ms.date: 05/07/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projiziert, projizierung, varbeiten, ereignis, delegat
ms.localizationpriority: medium
ms.openlocfilehash: c64b4a23e3b63c939d192e828e890a9ceb92e5ab
ms.sourcegitcommit: d10fb9eb5f75f2d10e1c543a177402b50fe4019e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "4575179"
---
# <a name="handle-events-by-using-delegates-in-cwinrt"></a><span data-ttu-id="5286c-104">Verarbeiten von Ereignissen über Delegaten in C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="5286c-104">Handle events by using delegates in C++/WinRT</span></span>

<span data-ttu-id="5286c-105">Dieses Thema zeigt, wie Sie registriert und widerruft Event-Handling-Delegaten mit [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).</span><span class="sxs-lookup"><span data-stu-id="5286c-105">This topic shows how to register and revoke event-handling delegates using [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).</span></span> <span data-ttu-id="5286c-106">Sie können ein Ereignis mit jedem Objekt verarbeiten, das einer normalen C++ Funktion entspricht.</span><span class="sxs-lookup"><span data-stu-id="5286c-106">You can handle an event using any standard C++ function-like object.</span></span>

> [!NOTE]
> <span data-ttu-id="5286c-107">Informationen zur Installation und Verwendung der C++/WinRT Visual Studio Extension (VSIX) (die Projektvorlagenunterstützung sowie C++/WinRT MSBuild-Eigenschaften und -Ziele bietet) finden Sie unter [Visual Studio-Unterstützung für C++/WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).</span><span class="sxs-lookup"><span data-stu-id="5286c-107">For info about installing and using the C++/WinRT Visual Studio Extension (VSIX) (which provides project template support, as well as C++/WinRT MSBuild properties and targets) see [Visual Studio support for C++/WinRT, and the VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).</span></span>

## <a name="register-a-delegate-to-handle-an-event"></a><span data-ttu-id="5286c-108">Einen Delegaten für die Verarbeitung eines Ereignisses registrieren</span><span class="sxs-lookup"><span data-stu-id="5286c-108">Register a delegate to handle an event</span></span>

<span data-ttu-id="5286c-109">Ein einfaches Beispiel ist die Verarbeitung des Klickereignisses einer Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="5286c-109">A simple example is handling a button's click event.</span></span> <span data-ttu-id="5286c-110">Es ist typisch, XAML-Markup zu verwenden, um eine Member-Funktion zu registrieren, um das Ereignis wie folgt zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="5286c-110">It's typical to use XAML markup to register a member function to handle the event, like this.</span></span>

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

<span data-ttu-id="5286c-111">Anstatt dies im Markup zu deklarieren, können Sie explizit eine Member-Funktion registrieren, um ein Ereignis zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="5286c-111">Instead of doing it declaratively in markup, you can imperatively register a member function to handle an event.</span></span> <span data-ttu-id="5286c-112">Es mag nicht offensichtlich sein, aber das Argument für den [**ButtonBase::Click**](/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.click)-Aufruf ist eine Instanz des [**RoutedEventHandler**](/uwp/api/windows.ui.xaml.routedeventhandler)-Delegaten.</span><span class="sxs-lookup"><span data-stu-id="5286c-112">It may not be obvious from the code example below, but the argument to the [**ButtonBase::Click**](/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.click) call is an instance of the [**RoutedEventHandler**](/uwp/api/windows.ui.xaml.routedeventhandler) delegate.</span></span> <span data-ttu-id="5286c-113">In diesem Fall verwenden wir die Überladung des **RoutedEventHandler**-Konstruktors, die ein Objekt und eine Pointer-to-Member-Funktion benötigt.</span><span class="sxs-lookup"><span data-stu-id="5286c-113">In this case, we're using the **RoutedEventHandler** constructor overload that takes an object and a pointer-to-member-function.</span></span>

```cppwinrt
// MainPage.cpp
MainPage::MainPage()
{
    InitializeComponent();

    Button().Click({ this, &MainPage::ClickHandler });
}
```

> [!IMPORTANT]
> <span data-ttu-id="5286c-114">Wenn der Delegat registriert, übergibt im obigen Codebeispiel unformatierte *dieses* -Zeiger (zeigen Sie auf das aktuelle Objekt).</span><span class="sxs-lookup"><span data-stu-id="5286c-114">When registered the delegate, the code example above passes a raw *this* pointer (pointing to the current object).</span></span> <span data-ttu-id="5286c-115">Zum Erstellen eine starke oder schwache Referenz auf das aktuelle Objekt finden Sie unter der **bei der Verwendung einer Member-Funktion als Delegaten** Unterabschnitt im Abschnitt zur [sicheren Zugriff auf das *diesem* Zeiger mit einen Delegaten für die Ereignisbehandlung](weak-references.md#safely-accessing-the-this-pointer-with-an-event-handling-delegate).</span><span class="sxs-lookup"><span data-stu-id="5286c-115">To learn how to establish a strong or a weak reference to the current object, see the **If you use a member function as a delegate** sub-section in the section [Safely accessing the *this* pointer with an event-handling delegate](weak-references.md#safely-accessing-the-this-pointer-with-an-event-handling-delegate).</span></span>

<span data-ttu-id="5286c-116">Es gibt andere Möglichkeiten, ein **RoutedEventHandler** zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="5286c-116">There are other ways to construct a **RoutedEventHandler**.</span></span> <span data-ttu-id="5286c-117">Unten finden Sie den Syntaxblock aus dem Dokumentationsthema für [**RoutedEventHandler**](/uwp/api/windows.ui.xaml.routedeventhandler) (wählen Sie *C++/WinRT* im Dropdown-Menü **Sprache** auf der Seite aus).</span><span class="sxs-lookup"><span data-stu-id="5286c-117">Below is the syntax block taken from the documentation topic for [**RoutedEventHandler**](/uwp/api/windows.ui.xaml.routedeventhandler) (choose *C++/WinRT* from the **Language** drop-down on the page).</span></span> <span data-ttu-id="5286c-118">Beachten Sie die verschiedenen Konstruktoren: Einer nimmt ein Lambda entgegen (ein anderer eine freie Funktion) und ein weiterer (der oben verwendete) nimmt ein Objekt und eine Pointer-to-Member-Funktion entgegen.</span><span class="sxs-lookup"><span data-stu-id="5286c-118">Notice the various constructors: one takes a lambda; another a free function; and another (the one we used above) takes an object and a pointer-to-member-function.</span></span>

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

<span data-ttu-id="5286c-119">Die Syntax des Funktionsaufrufoperators ist ebenfalls hilfreich.</span><span class="sxs-lookup"><span data-stu-id="5286c-119">The syntax of the function call operator is also helpful to see.</span></span> <span data-ttu-id="5286c-120">Sie sagt Ihnen, welche Parameter Ihr Delegat haben muss.</span><span class="sxs-lookup"><span data-stu-id="5286c-120">It tells you what your delegate's parameters need to be.</span></span> <span data-ttu-id="5286c-121">Wie Sie sehen, entspricht in diesem Fall die Syntax des Funktionsaufrufoperators den Parametern unseres **MainPage::ClickHandler**.</span><span class="sxs-lookup"><span data-stu-id="5286c-121">As you can see, in this case the function call operator syntax matches the parameters of our **MainPage::ClickHandler**.</span></span>

<span data-ttu-id="5286c-122">Wenn Sie nicht viel in Ihrem Ereignis-Handler erledigen, dann können Sie eine Lambda-Funktion anstelle einer Mitgliedsfunktion verwenden.</span><span class="sxs-lookup"><span data-stu-id="5286c-122">If you're not doing much work in your event handler, then you can use a lambda function instead of a member function.</span></span> <span data-ttu-id="5286c-123">Auch hier ist es vielleicht nicht offensichtlich, aber ein **RoutedEventHandler**-Delegat wird aus einer Lambda-Funktion erstellt, die wiederum der Syntax des Funktionsaufrufoperators entsprechen muss.</span><span class="sxs-lookup"><span data-stu-id="5286c-123">Again, it may not be obvious from the code example below, but a **RoutedEventHandler** delegate is being constructed from a lambda function which, again, needs to match the syntax of the function call operator.</span></span>

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

<span data-ttu-id="5286c-124">Sie können sich dafür entscheiden, etwas konkreter zu werden, wenn Sie Ihren Delegaten konstruieren.</span><span class="sxs-lookup"><span data-stu-id="5286c-124">You can choose to be a little more explicit when you construct your delegate.</span></span> <span data-ttu-id="5286c-125">Beispielsweise bei der Weitergabe oder der mehrfachen Verwendung.</span><span class="sxs-lookup"><span data-stu-id="5286c-125">For example, if you want to pass it around, or use it more than once.</span></span>

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

## <a name="revoke-a-registered-delegate"></a><span data-ttu-id="5286c-126">Einen registrierten Delgaten widerrufen</span><span class="sxs-lookup"><span data-stu-id="5286c-126">Revoke a registered delegate</span></span>

<span data-ttu-id="5286c-127">Wenn Sie einen Deleganten registrieren, wird Ihnen in der Regel ein Token zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="5286c-127">When you register a delegate, typically a token is returned to you.</span></span> <span data-ttu-id="5286c-128">Mit diesem Token können Sie anschließend Ihren Delegaten widerrufen, d. h. die Registrierung des Delegaten für das Ereignis wird aufgehoben. Er wird nicht mehr aufgerufen, wenn das Ereignis erneut ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="5286c-128">You can subsequently use that token to revoke your delegate; meaning that the delegate is unregistered from the event, and won't be called should the event be raised again.</span></span> <span data-ttu-id="5286c-129">Der Einfachheit halber hat keines der obigen Codebeispiele gezeigt, wie das geht.</span><span class="sxs-lookup"><span data-stu-id="5286c-129">For the sake of simplicity, none of the code examples above showed how to do that.</span></span> <span data-ttu-id="5286c-130">Das nächste Codebeispiel speichert das Token jedoch im privaten Datenelement der Struktur und widerruft seinen Handler im Destruktor.</span><span class="sxs-lookup"><span data-stu-id="5286c-130">But this next code example stores the token in the struct's private data member, and revokes its handler in the destructor.</span></span>

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

<span data-ttu-id="5286c-131">Anstatt eines starken Verweises wie im obigen Beispiel können Sie einen schwachen Verweis auf die Schaltfläche Speichern (siehe [starke und schwache Referenzen in C++ / WinRT](weak-references.md)).</span><span class="sxs-lookup"><span data-stu-id="5286c-131">Instead of a strong reference, as in the example above, you can store a weak reference to the button (see [Strong and weak references in C++/WinRT](weak-references.md)).</span></span>

<span data-ttu-id="5286c-132">Auch wenn Sie einen deleganten registrieren, können Sie angeben **WinRT:: auto_revoke** (das den Wert Typ [**WinRT:: auto_revoke_t**](/uwp/cpp-ref-for-winrt/auto-revoke-t)) um einen Event-Revoker (vom Typ [**event_revoker**](/uwp/cpp-ref-for-winrt/event-revoker)) anzufordern.</span><span class="sxs-lookup"><span data-stu-id="5286c-132">Alternatively, when you register a delegate, you can specify **winrt::auto_revoke** (which is a value of type [**winrt::auto_revoke_t**](/uwp/cpp-ref-for-winrt/auto-revoke-t)) to request an event revoker (of type [**winrt::event_revoker**](/uwp/cpp-ref-for-winrt/event-revoker)).</span></span> <span data-ttu-id="5286c-133">Der Event-Revoker enthält einen schwachen Verweis auf die Ereignisquelle (das Objekt, das das Ereignis auslöst) für Sie.</span><span class="sxs-lookup"><span data-stu-id="5286c-133">The event revoker holds a weak reference to the event source (the object that raises the event) for you.</span></span> <span data-ttu-id="5286c-134">Sie können manuell widerrufen, indem Sie die Mitgliedsfunktion **event_revoker::revoke** aufrufen; der Event-Revoker ruft diese Funktion aber selbst automatisch auf, wenn sie ihren Gültigkeitsbereich verlässt.</span><span class="sxs-lookup"><span data-stu-id="5286c-134">You can manually revoke by calling the **event_revoker::revoke** member function; but the event revoker calls that function itself automatically when it goes out of scope.</span></span> <span data-ttu-id="5286c-135">Die **revoke**-Funktion überprüft, ob die Ereignisquelle noch vorhanden ist, und widerruft in diesem Fall den Delegaten.</span><span class="sxs-lookup"><span data-stu-id="5286c-135">The **revoke** function checks whether the event source still exists and, if so, revokes your delegate.</span></span> <span data-ttu-id="5286c-136">In diesem Beispiel gibt es keine Notwendigkeit, die Ereignisquelle zu speichern, und daher auch keinen Bedarf für einen Destruktor.</span><span class="sxs-lookup"><span data-stu-id="5286c-136">In this example, there's no need to store the event source, and no need for a destructor.</span></span>

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
    winrt::event_revoker<winrt::Windows::UI::Xaml::Controls::Primitives::IButtonBase> m_event_revoker;
};
```

<span data-ttu-id="5286c-137">Unten ist der Syntaxblock aus dem Dokumentationsthema für das [**ButtonBase::Click**](/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.click)-Ereignis zu sehen.</span><span class="sxs-lookup"><span data-stu-id="5286c-137">Below is the syntax block taken from the documentation topic for the [**ButtonBase::Click**](/uwp/api/windows.ui.xaml.controls.primitives.buttonbase.click) event.</span></span> <span data-ttu-id="5286c-138">Es zeigt die drei verschiedenen Registrierungs- und Widerrufsfunktionen.</span><span class="sxs-lookup"><span data-stu-id="5286c-138">It shows the three different registration and revoking functions.</span></span> <span data-ttu-id="5286c-139">Sie können genau sehen, welche Art von Event-Revoker Sie für die dritten Überladung deklarieren müssen.</span><span class="sxs-lookup"><span data-stu-id="5286c-139">You can see exactly what type of event revoker you need to declare from the third overload.</span></span>

```cppwinrt
// Register
winrt::event_token Click(winrt::Windows::UI::Xaml::RoutedEventHandler const& handler) const;

// Revoke with event_token
void Click(winrt::event_token const& token) const;

// Revoke with event_revoker
winrt::event_revoker<winrt::Windows::UI::Xaml::Controls::Primitives::IButtonBase> Click(winrt::auto_revoke_t,
    winrt::Windows::UI::Xaml::RoutedEventHandler const& handler) const;
```

<span data-ttu-id="5286c-140">Ein ähnliches Muster gilt für alle C++/WinRT-Ereignisse.</span><span class="sxs-lookup"><span data-stu-id="5286c-140">A similar pattern applies to all C++/WinRT events.</span></span>

<span data-ttu-id="5286c-141">In einem Seitennavigationsszenario kann es sinnvoll sein, Handler zu widerrufen.</span><span class="sxs-lookup"><span data-stu-id="5286c-141">You might consider revoking handlers in a page-navigation scenario.</span></span> <span data-ttu-id="5286c-142">Wenn Sie wiederholt auf eine Seite navigieren und diese dann wieder verlassen, können Sie alle Handler widerrufen, wenn Sie von der Seite weg navigieren.</span><span class="sxs-lookup"><span data-stu-id="5286c-142">If you're repeatedly navigating into a page and then back out, then you could revoke any handlers when you navigate away from the page.</span></span> <span data-ttu-id="5286c-143">Wenn Sie dieselbe Seiteninstanz wiederverwenden, dann überprüfen Sie alternativ den Wert Ihres Tokens und registrieren Sie sich nur, wenn er noch nicht festgelegt ist (`if (!m_token){ ... }`).</span><span class="sxs-lookup"><span data-stu-id="5286c-143">Alternatively, if you're re-using the same page instance, then check the value of your token and only register if it's not yet been set (`if (!m_token){ ... }`).</span></span> <span data-ttu-id="5286c-144">Eine dritte Möglichkeit besteht darin, einen Event-Revoker als Datenelement der Seite zu speichern.</span><span class="sxs-lookup"><span data-stu-id="5286c-144">A third option is to store an event revoker in the page as a data member.</span></span> <span data-ttu-id="5286c-145">Und eine vierte Möglichkeit (wird später in diesem Thema beschrieben) besteht darin, eine starke oder schwache Referenz auf das *this*-Objekt in Ihrer Lambda-Funktion zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="5286c-145">And a fourth option, as described later in this topic, is to capture a strong or a weak reference to the *this* object in your lambda function.</span></span>

## <a name="delegate-types-for-asynchronous-actions-and-operations"></a><span data-ttu-id="5286c-146">Delegattypen für asynchrone Aktionen und Vorgänge</span><span class="sxs-lookup"><span data-stu-id="5286c-146">Delegate types for asynchronous actions and operations</span></span>

<span data-ttu-id="5286c-147">Die obigen Beispiele verwenden den Delegattyp **RoutedEventHandler**, aber es gibt natürlich auch viele andere Delegattypen.</span><span class="sxs-lookup"><span data-stu-id="5286c-147">The examples above use the **RoutedEventHandler** delegate type, but there are of course many other delegate types.</span></span> <span data-ttu-id="5286c-148">Beispielsweise haben asynchrone Aktionen und Vorgänge (mit und ohne Fortschritt) Completed- und/oder Progress-Ereignisse, die Delegaten des entsprechenden Typs erwarten.</span><span class="sxs-lookup"><span data-stu-id="5286c-148">For example, asynchronous actions and operations (with and without progress) have completed and/or progress events that expect delegates of the corresponding type.</span></span> <span data-ttu-id="5286c-149">Beispielsweise erfordert das Progress-Ereignis eines asynchronen Vorgangs mit Fortschritt (betrifft alles, das [**IAsyncOperationWithProgress**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_) implementiert) einen Delegaten vom Typ [**AsyncOperationProgressHandler**](/uwp/api/windows.foundation.asyncoperationprogresshandler).</span><span class="sxs-lookup"><span data-stu-id="5286c-149">For example, the progress event of an asynchronous operation with progress (which is anything that implements [**IAsyncOperationWithProgress**](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_)) requires a delegate of type [**AsyncOperationProgressHandler**](/uwp/api/windows.foundation.asyncoperationprogresshandler).</span></span> <span data-ttu-id="5286c-150">Hier ist ein Codebeispiel für die Erstellung eines solchen Delegaten mit einer Lambda-Funktion.</span><span class="sxs-lookup"><span data-stu-id="5286c-150">Here's a code example of authoring a delegate of that type using a lambda function.</span></span> <span data-ttu-id="5286c-151">Das Beispiel zeigt auch, wie man einen [**AsyncOperationWithProgressCompletedHandler**](/uwp/api/windows.foundation.asyncoperationwithprogresscompletedhandler)-Delegaten erstellt.</span><span class="sxs-lookup"><span data-stu-id="5286c-151">The example also shows how to author an [**AsyncOperationWithProgressCompletedHandler**](/uwp/api/windows.foundation.asyncoperationwithprogresscompletedhandler) delegate.</span></span>

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

<span data-ttu-id="5286c-152">Wie aus dem obigen „coroutine“-Kommentar hervorgeht, werden Sie es wahrscheinlich natürlicher finden, Coroutinen zu verwenden, anstatt einen Delegaten für die Completed-Ereignisse asynchroner Aktionen und Vorgänge zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="5286c-152">As the "coroutine" comment above suggests, instead of using a delegate with the completed events of asynchronous actions and operations, you'll probably find it more natural to use coroutines.</span></span> <span data-ttu-id="5286c-153">Details und Codebeispiele finden Sie unter [Parallelität und asynchrone Vorgänge mit C++/WinRT](concurrency.md).</span><span class="sxs-lookup"><span data-stu-id="5286c-153">For details, and code examples, see [Concurrency and asynchronous operations with C++/WinRT](concurrency.md).</span></span>

> [!NOTE]
> <span data-ttu-id="5286c-154">Es ist nicht korrekt mehrere *Abschlusshandler* für eine asynchrone Aktion oder eines Vorgangs zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="5286c-154">It's not correct to implement more than one *completion handler* for an asynchronous action or operation.</span></span> <span data-ttu-id="5286c-155">Sie können entweder einen einzelnen Delegaten für das abgeschlossene Ereignis haben, oder Sie können `co_await` es.</span><span class="sxs-lookup"><span data-stu-id="5286c-155">You can have either a single delegate for its completed event, or you can `co_await` it.</span></span> <span data-ttu-id="5286c-156">Wenn Sie beide haben, wird die zweite fehl.</span><span class="sxs-lookup"><span data-stu-id="5286c-156">If you have both, then the second will fail.</span></span>

<span data-ttu-id="5286c-157">Wenn Sie an Delegaten anstelle einer Coroutine, können Sie für eine einfachere Syntax ablehnen.</span><span class="sxs-lookup"><span data-stu-id="5286c-157">If you stick with delegates instead of a coroutine, then you can opt for a simpler syntax.</span></span>

```cppwinrt
async_op_with_progress.Completed(
    [](auto&& /*sender*/, AsyncStatus const /* args */)
{
    // ...
});
```

## <a name="delegate-types-that-return-a-value"></a><span data-ttu-id="5286c-158">Delegattypen, die einen Wert zurückgeben</span><span class="sxs-lookup"><span data-stu-id="5286c-158">Delegate types that return a value</span></span>

<span data-ttu-id="5286c-159">Einige Delegattypen müssen selbst einen Wert zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="5286c-159">Some delegate types must themselves return a value.</span></span> <span data-ttu-id="5286c-160">Ein Beispiel ist [**ListViewItemToKeyHandler**](/uwp/api/windows.ui.xaml.controls.listviewitemtokeyhandler), der einen String zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="5286c-160">An example is [**ListViewItemToKeyHandler**](/uwp/api/windows.ui.xaml.controls.listviewitemtokeyhandler), which returns a string.</span></span> <span data-ttu-id="5286c-161">Hier ist ein Beispiel für die Erstellung eines solchen Delegaten (beachten Sie, dass die Lambda-Funktion einen Wert zurückgibt).</span><span class="sxs-lookup"><span data-stu-id="5286c-161">Here's an example of authoring a delegate of that type (note that the lambda function returns a value).</span></span>

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

## <a name="safely-accessing-the-this-pointer-with-an-event-handling-delegate"></a><span data-ttu-id="5286c-162">Sicheren Zugriff auf das *diesem* Zeiger mit einen Delegaten für die Ereignisbehandlung</span><span class="sxs-lookup"><span data-stu-id="5286c-162">Safely accessing the *this* pointer with an event-handling delegate</span></span>

<span data-ttu-id="5286c-163">Wenn Sie ein Ereignis mit Mitgliedsfunktion eines Objekts verarbeiten, oder von innerhalb einer Lambda-Funktion innerhalb eines Objekts Member-Funktion, Sie über die relative Lebensdauer des Ereignisempfängers (das Objekt, das das Ereignis behandelt) und die Ereignisquelle (das Objekt vorstellen müssen das Ereignis auslöst).</span><span class="sxs-lookup"><span data-stu-id="5286c-163">If you handle an event with an object's member function, or from within a lambda function inside an object's member function, then you need to think about the relative lifetimes of the event recipient (the object handling the event) and the event source (the object raising the event).</span></span> <span data-ttu-id="5286c-164">Weitere Informationen und Codebeispiele finden Sie unter [starke und schwache Referenzen in C++ / WinRT](weak-references.md#safely-accessing-the-this-pointer-with-an-event-handling-delegate).</span><span class="sxs-lookup"><span data-stu-id="5286c-164">For more info, and code examples, see [Strong and weak references in C++/WinRT](weak-references.md#safely-accessing-the-this-pointer-with-an-event-handling-delegate).</span></span>

## <a name="important-apis"></a><span data-ttu-id="5286c-165">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="5286c-165">Important APIs</span></span>
* [<span data-ttu-id="5286c-166">WinRT:: auto_revoke_t markerstruktur</span><span class="sxs-lookup"><span data-stu-id="5286c-166">winrt::auto_revoke_t marker struct</span></span>](/uwp/cpp-ref-for-winrt/auto-revoke-t)
* [<span data-ttu-id="5286c-167">winrt::implements::get_weak-Funktion</span><span class="sxs-lookup"><span data-stu-id="5286c-167">winrt::implements::get_weak function</span></span>](/uwp/cpp-ref-for-winrt/implements#implementsgetweak-function)
* [<span data-ttu-id="5286c-168">winrt::implements::get_strong-Funktion</span><span class="sxs-lookup"><span data-stu-id="5286c-168">winrt::implements::get_strong function</span></span>](/uwp/cpp-ref-for-winrt/implements#implementsgetstrong-function)

## <a name="related-topics"></a><span data-ttu-id="5286c-169">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="5286c-169">Related topics</span></span>
* [<span data-ttu-id="5286c-170">Erstellen von Ereignissen mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="5286c-170">Author events in C++/WinRT</span></span>](author-events.md)
* [<span data-ttu-id="5286c-171">Parallelität und asynchrone Vorgänge mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="5286c-171">Concurrency and asynchronous operations with C++/WinRT</span></span>](concurrency.md)
* [<span data-ttu-id="5286c-172">Starke und schwache Referenzen in C++ / WinRT</span><span class="sxs-lookup"><span data-stu-id="5286c-172">Strong and weak references in C++/WinRT</span></span>](weak-references.md)
