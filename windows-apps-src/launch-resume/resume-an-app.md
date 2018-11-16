---
author: TylerMSFT
title: Behandeln der App-Fortsetzung
description: Erfahren Sie, wie Sie den angezeigten Inhalt aktualisieren, wenn das System die App fortsetzt.
ms.assetid: DACCC556-B814-4600-A10A-90B82664EA15
ms.author: twhitney
ms.date: 07/06/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
dev_langs:
- csharp
- vb
- cppwinrt
- cpp
ms.openlocfilehash: 717c819aaa732cf8d29e0a701a1fec81485f48ac
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6976100"
---
# <a name="handle-app-resume"></a><span data-ttu-id="2f27e-104">Behandeln der App-Fortsetzung</span><span class="sxs-lookup"><span data-stu-id="2f27e-104">Handle app resume</span></span>

**<span data-ttu-id="2f27e-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="2f27e-105">Important APIs</span></span>**

- [**<span data-ttu-id="2f27e-106">Fortsetzen</span><span class="sxs-lookup"><span data-stu-id="2f27e-106">Resuming</span></span>**](https://msdn.microsoft.com/library/windows/apps/br242339)

<span data-ttu-id="2f27e-107">Erfahren Sie, wo Sie Ihre Benutzeroberfläche aktualisieren, wenn das System die App fortsetzt.</span><span class="sxs-lookup"><span data-stu-id="2f27e-107">Learn where to refresh your UI when the system resumes your app.</span></span> <span data-ttu-id="2f27e-108">Im Beispiel in diesem Thema wird ein Ereignishandler für das [**Resuming**](https://msdn.microsoft.com/library/windows/apps/br242339)-Ereignis registriert.</span><span class="sxs-lookup"><span data-stu-id="2f27e-108">The example in this topic registers an event handler for the [**Resuming**](https://msdn.microsoft.com/library/windows/apps/br242339) event.</span></span>

## <a name="register-the-resuming-event-handler"></a><span data-ttu-id="2f27e-109">Registrieren des „resuming“-Ereignishandlers</span><span class="sxs-lookup"><span data-stu-id="2f27e-109">Register the resuming event handler</span></span>

<span data-ttu-id="2f27e-110">Registrieren Sie die Behandlung des [**Resuming**](https://msdn.microsoft.com/library/windows/apps/br242339)-Ereignisses, mit dem angegeben wird, dass der Benutzer aus der App und wieder zurück gewechselt hat.</span><span class="sxs-lookup"><span data-stu-id="2f27e-110">Register to handle the [**Resuming**](https://msdn.microsoft.com/library/windows/apps/br242339) event, which indicates that the user switched away from your app and then back to it.</span></span>

```csharp
partial class MainPage
{
   public MainPage()
   {
      InitializeComponent();
      Application.Current.Resuming += new EventHandler<Object>(App_Resuming);
   }
}
```

```vb
Public NonInheritable Class MainPage

   Public Sub New()
      InitializeComponent()
      AddHandler Application.Current.Resuming, AddressOf App_Resuming
   End Sub

End Class
```

```cppwinrt
MainPage::MainPage()
{
    InitializeComponent();
    Windows::UI::Xaml::Application::Current().Resuming({ this, &MainPage::App_Resuming });
}
```

```cpp
MainPage::MainPage()
{
    InitializeComponent();
    Application::Current->Resuming +=
        ref new EventHandler<Platform::Object^>(this, &MainPage::App_Resuming);
}
```

## <a name="refresh-displayed-content-and-reacquire-resources"></a><span data-ttu-id="2f27e-111">Aktualisieren des angezeigten Inhalts und erneutes Abrufen von Ressourcen</span><span class="sxs-lookup"><span data-stu-id="2f27e-111">Refresh displayed content and reacquire resources</span></span>

<span data-ttu-id="2f27e-112">Das System hält Ihre App ein paar Sekunden an, nachdem der Benutzer zu einer anderen App oder zum Desktop wechselt.</span><span class="sxs-lookup"><span data-stu-id="2f27e-112">The system suspends your app a few seconds after the user switches to another app or to the desktop.</span></span> <span data-ttu-id="2f27e-113">Wenn der Benutzer wieder zu Ihrer App wechselt, wird diese vom System fortgesetzt.</span><span class="sxs-lookup"><span data-stu-id="2f27e-113">The system resumes your app when the user switches back to it.</span></span> <span data-ttu-id="2f27e-114">Beim Fortsetzen der App haben die Variablen und Datenstrukturen den gleichen Inhalt wie vor der Unterbrechung.</span><span class="sxs-lookup"><span data-stu-id="2f27e-114">When the system resumes your app, the content of your variables and data structures are the same as they were before the system suspended the app.</span></span> <span data-ttu-id="2f27e-115">Das System stellt die App an der Stelle wieder her.</span><span class="sxs-lookup"><span data-stu-id="2f27e-115">The system restores the app where it left off.</span></span> <span data-ttu-id="2f27e-116">Für den Benutzer sieht es so aus, als ob die App im Hintergrund ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="2f27e-116">To the user, it appears as if the app has been running in the background.</span></span>

<span data-ttu-id="2f27e-117">Wenn Ihre App das [**Resuming** ](https://msdn.microsoft.com/library/windows/apps/br242339)-Ereignis handhabt, wird sie möglicherweise für Stunden oder Tage angehalten.</span><span class="sxs-lookup"><span data-stu-id="2f27e-117">When your app handles the [**Resuming**](https://msdn.microsoft.com/library/windows/apps/br242339) event, your app may be been suspended for hours or days.</span></span> <span data-ttu-id="2f27e-118">Sie sollte alle Inhalte aktualisieren, die während des Anhaltens der App ggf. veraltet sind, z.B. Newsfeeds oder der Standort des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="2f27e-118">It should refresh any content that might have become stale while the app was suspended, such as news feeds or the user's location.</span></span>

<span data-ttu-id="2f27e-119">Dies ist auch ein guter Zeitpunkt, um alle exklusiven Ressourcen wiederzuherstellen, die Sie freigegeben haben, als Ihre App angehalten wurde, z.B. Dateihandles, Kameras, E/A-Geräte, externe Geräte und Netzwerkressourcen.</span><span class="sxs-lookup"><span data-stu-id="2f27e-119">This is also a good time to restore any exclusive resources that you released when your app was suspended such as file handles, cameras, I/O devices, external devices, and network resources.</span></span>

```csharp
partial class MainPage
{
    private void App_Resuming(Object sender, Object e)
    {
        // TODO: Refresh network data, perform UI updates, and reacquire resources like cameras, I/O devices, etc.
    }
}
```

```vb
Public NonInheritable Class MainPage

    Private Sub App_Resuming(sender As Object, e As Object)
 
        ' TODO: Refresh network data, perform UI updates, and reacquire resources like cameras, I/O devices, etc.

    End Sub
>
End Class
```

```cppwinrt
void MainPage::App_Resuming(
    Windows::Foundation::IInspectable const& /* sender */,
    Windows::Foundation::IInspectable const& /* e */)
{
    // TODO: Refresh network data, perform UI updates, and reacquire resources like cameras, I/O devices, etc.
}
```

```cpp
void MainPage::App_Resuming(Object^ sender, Object^ e)
{
    // TODO: Refresh network data, perform UI updates, and reacquire resources like cameras, I/O devices, etc.
}
```

> [!NOTE]
> <span data-ttu-id="2f27e-120">Da das [**Resuming**](https://msdn.microsoft.com/library/windows/apps/br242339) -Ereignis nicht vom UI-Thread ausgelöst wird, muss ein Dispatcher in Ihrem Handler verwendet werden, um Aufrufe für Ihre UI zu verteilen.</span><span class="sxs-lookup"><span data-stu-id="2f27e-120">Because the [**Resuming**](https://msdn.microsoft.com/library/windows/apps/br242339) event is not raised from the UI thread, a dispatcher must be used in your handler to dispatch any calls to your UI.</span></span>

## <a name="remarks"></a><span data-ttu-id="2f27e-121">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="2f27e-121">Remarks</span></span>

<span data-ttu-id="2f27e-122">Wenn Ihre App an den Visual Studio-Debugger gebunden ist, wird sie nicht angehalten.</span><span class="sxs-lookup"><span data-stu-id="2f27e-122">When your app is attached to the Visual Studio debugger, it will not be suspended.</span></span> <span data-ttu-id="2f27e-123">Sie können sie aber vom Debugger anhalten und dann ein **Resume**-Ereignis senden, damit Sie den Code debuggen können.</span><span class="sxs-lookup"><span data-stu-id="2f27e-123">You can suspend it from the debugger, however, and then send it a **Resume** event so that you can debug your code.</span></span> <span data-ttu-id="2f27e-124">Sorgen Sie dafür, dass die Symbolleiste **Debugspeicherort** angezeigt wird, und klicken Sie auf das Dropdownelement neben dem Symbol **Anhalten**.</span><span class="sxs-lookup"><span data-stu-id="2f27e-124">Make sure the **Debug Location toolbar** is visible and click the drop-down next to the **Suspend** icon.</span></span> <span data-ttu-id="2f27e-125">Wählen Sie dann **Fortsetzen** aus.</span><span class="sxs-lookup"><span data-stu-id="2f27e-125">Then choose **Resume**.</span></span>

<span data-ttu-id="2f27e-126">Für Windows Phone Store-Apps folgt auf das [**Resuming**](https://msdn.microsoft.com/library/windows/apps/br242339)-Ereignis immer [**OnLaunched**](https://msdn.microsoft.com/library/windows/apps/br242335), auch wenn Ihre App derzeit angehalten ist und der Benutzer Ihre App über eine primäre Kachel oder die App-Liste neu startet.</span><span class="sxs-lookup"><span data-stu-id="2f27e-126">For Windows Phone Store apps, the [**Resuming**](https://msdn.microsoft.com/library/windows/apps/br242339) event is always followed by [**OnLaunched**](https://msdn.microsoft.com/library/windows/apps/br242335), even when your app is currently suspended and the user re-launches your app from a primary tile or app list.</span></span> <span data-ttu-id="2f27e-127">Apps können die Initialisierung überspringen, wenn für das aktuelle Fenster bereits Inhalte festgelegt wurden.</span><span class="sxs-lookup"><span data-stu-id="2f27e-127">Apps can skip initialization if there is already content set on the current window.</span></span> <span data-ttu-id="2f27e-128">Überprüfen Sie die [**LaunchActivatedEventArgs.TileId**](https://msdn.microsoft.com/library/windows/apps/br224736)-Eigenschaft, um zu ermitteln, ob die App über eine primäre oder sekundäre Kachel gestartet wurde. Entscheiden Sie basierend auf dieser Information, ob die App neu gestartet oder fortgesetzt werden soll.</span><span class="sxs-lookup"><span data-stu-id="2f27e-128">You can check the [**LaunchActivatedEventArgs.TileId**](https://msdn.microsoft.com/library/windows/apps/br224736) property to determine if the app was launched from a primary or a secondary tile and, based on that information, decide whether you should present a fresh or resume app experience.</span></span>

## <a name="related-topics"></a><span data-ttu-id="2f27e-129">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="2f27e-129">Related topics</span></span>

* [<span data-ttu-id="2f27e-130">App-Lebenszyklus</span><span class="sxs-lookup"><span data-stu-id="2f27e-130">App lifecycle</span></span>](app-lifecycle.md)
* [<span data-ttu-id="2f27e-131">Behandeln der App-Aktivierung</span><span class="sxs-lookup"><span data-stu-id="2f27e-131">Handle app activation</span></span>](activate-an-app.md)
* [<span data-ttu-id="2f27e-132">Behandeln des Anhaltens von Apps</span><span class="sxs-lookup"><span data-stu-id="2f27e-132">Handle app suspend</span></span>](suspend-an-app.md)
