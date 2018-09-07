---
author: PatrickFarley
ms.assetid: 9A0F1852-A76B-4F43-ACFC-2CC56AAD1C03
title: Drucken in Apps
description: Hier erfahren Sie, wie Sie Dokumente in einer Universellen Windows-App drucken. In diesem Thema wird zudem gezeigt, wie bestimmte Seiten gedruckt werden.
ms.author: pafarley
ms.date: 01/29/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, das Drucken
ms.localizationpriority: medium
ms.openlocfilehash: cff96c0b8daf9f3ef32815437b510a5b94641527
ms.sourcegitcommit: 00d27738325d6db5b5e481911ae7fac0711b05eb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2018
ms.locfileid: "3659791"
---
# <a name="print-from-your-app"></a><span data-ttu-id="e92c4-105">Drucken in Apps</span><span class="sxs-lookup"><span data-stu-id="e92c4-105">Print from your app</span></span>



**<span data-ttu-id="e92c4-106">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="e92c4-106">Important APIs</span></span>**

-   [**<span data-ttu-id="e92c4-107">Windows.Graphics.Printing</span><span class="sxs-lookup"><span data-stu-id="e92c4-107">Windows.Graphics.Printing</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR226489)
-   [**<span data-ttu-id="e92c4-108">Windows.UI.Xaml.Printing</span><span class="sxs-lookup"><span data-stu-id="e92c4-108">Windows.UI.Xaml.Printing</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR243325)
-   [**<span data-ttu-id="e92c4-109">PrintDocument</span><span class="sxs-lookup"><span data-stu-id="e92c4-109">PrintDocument</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR243314)

<span data-ttu-id="e92c4-110">Hier erfahren Sie, wie Sie Dokumente in einer universellen Windows-App drucken.</span><span class="sxs-lookup"><span data-stu-id="e92c4-110">Learn how to print documents from a Universal Windows app.</span></span> <span data-ttu-id="e92c4-111">In diesem Thema wird zudem gezeigt, wie bestimmte Seiten gedruckt werden.</span><span class="sxs-lookup"><span data-stu-id="e92c4-111">This topic also shows how to print specific pages.</span></span> <span data-ttu-id="e92c4-112">Informationen zu erweiterten Änderungen an der Benutzeroberfläche für die Druckvorschau finden Sie unter [Anpassen der Benutzeroberfläche für die Druckvorschau](customize-the-print-preview-ui.md).</span><span class="sxs-lookup"><span data-stu-id="e92c4-112">For more advanced changes to the print preview UI, see [Customize the print preview UI](customize-the-print-preview-ui.md).</span></span>

> [!TIP]
> <span data-ttu-id="e92c4-113">Die meisten Beispiele in diesem Thema basieren auf dem Druckbeispiel.</span><span class="sxs-lookup"><span data-stu-id="e92c4-113">Most of the examples in this topic are based on the print sample.</span></span> <span data-ttu-id="e92c4-114">Laden Sie das [Druckbeispiel für die universelle Windows-Plattform (UWP)](http://go.microsoft.com/fwlink/p/?LinkId=619984) aus dem Repository [Beispiele für Universelle Windows-Plattform](http://go.microsoft.com/fwlink/p/?LinkId=619979) auf GitHub herunter, um den vollständigen Code anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="e92c4-114">To see the full code, download the [Universal Windows Platform (UWP) print sample](http://go.microsoft.com/fwlink/p/?LinkId=619984) from the [Windows-universal-samples repo](http://go.microsoft.com/fwlink/p/?LinkId=619979) on GitHub.</span></span>

## <a name="register-for-printing"></a><span data-ttu-id="e92c4-115">Registrieren für Druckfunktionen</span><span class="sxs-lookup"><span data-stu-id="e92c4-115">Register for printing</span></span>

<span data-ttu-id="e92c4-116">Um Ihrer App Druckfunktionen hinzuzufügen, müssen Sie sie als Erstes für den Vertrag für "Drucken" registrieren.</span><span class="sxs-lookup"><span data-stu-id="e92c4-116">The first step to add printing to your app is to register for the Print contract.</span></span> <span data-ttu-id="e92c4-117">Die Registrierung ist für jeden Bildschirm erforderlich, auf dem der Benutzer drucken können soll.</span><span class="sxs-lookup"><span data-stu-id="e92c4-117">Your app must do this on every screen from which you want your user to be able to print.</span></span> <span data-ttu-id="e92c4-118">Es kann jeweils nur der Bildschirm, der gerade angezeigt wird, für das Drucken registriert werden.</span><span class="sxs-lookup"><span data-stu-id="e92c4-118">Only the screen that is displayed to the user can be registered for printing.</span></span> <span data-ttu-id="e92c4-119">Wenn ein Bildschirm Ihrer App für das Drucken registriert wurde, muss die Registrierung beim Schließen des Bildschirms aufgehoben werden.</span><span class="sxs-lookup"><span data-stu-id="e92c4-119">If one screen of your app has registered for printing, it must unregister for printing when it exits.</span></span> <span data-ttu-id="e92c4-120">Wird an seiner Stelle ein anderer Bildschirm angezeigt, muss dieser nächste Bildschirm beim Öffnen für einen neuen Vertrag für "Drucken" registriert werden.</span><span class="sxs-lookup"><span data-stu-id="e92c4-120">If it is replaced by another screen, the next screen must register for a new Print contract when it opens.</span></span>

> [!TIP]
> <span data-ttu-id="e92c4-121">Falls das Drucken mehrerer Seiten in Ihrer App unterstützt werden soll, können Sie diesen Druckcode in eine allgemeine Hilfsprogrammklasse einfügen und von den App-Seiten wiederverwenden lassen.</span><span class="sxs-lookup"><span data-stu-id="e92c4-121">If you need to support printing from more than one page in your app, you can put this print code in a common helper class and have your app pages reuse it.</span></span> <span data-ttu-id="e92c4-122">Ein entsprechendes Beispiel finden Sie in der `PrintHelper`-Klasse im [UWP-Druckbeispiel](http://go.microsoft.com/fwlink/p/?LinkId=619984).</span><span class="sxs-lookup"><span data-stu-id="e92c4-122">For an example of how to do this, see the `PrintHelper` class in the [UWP print sample](http://go.microsoft.com/fwlink/p/?LinkId=619984).</span></span>

<span data-ttu-id="e92c4-123">Geben Sie zuerst die Klassen [**PrintManager**](https://msdn.microsoft.com/library/windows/apps/BR226426) und [**PrintDocument**](https://msdn.microsoft.com/library/windows/apps/BR243314) an.</span><span class="sxs-lookup"><span data-stu-id="e92c4-123">First, declare the [**PrintManager**](https://msdn.microsoft.com/library/windows/apps/BR226426) and [**PrintDocument**](https://msdn.microsoft.com/library/windows/apps/BR243314).</span></span> <span data-ttu-id="e92c4-124">Der **PrintManager**-Typ und Typen zur Unterstützung anderer Windows-Druckfunktionen befinden sich im [**Windows.Graphics.Printing**](https://msdn.microsoft.com/library/windows/apps/BR226489)-Namespace.</span><span class="sxs-lookup"><span data-stu-id="e92c4-124">The **PrintManager** type is in the [**Windows.Graphics.Printing**](https://msdn.microsoft.com/library/windows/apps/BR226489) namespace along with types to support other Windows printing functionality.</span></span> <span data-ttu-id="e92c4-125">Der **PrintDocument**-Typ und andere Typen zur Unterstützung der Vorbereitung von XAML-Inhalten für das Drucken sind im [**Windows.UI.Xaml.Printing**](https://msdn.microsoft.com/library/windows/apps/BR243325)-Namespace enthalten.</span><span class="sxs-lookup"><span data-stu-id="e92c4-125">The **PrintDocument** type is in the [**Windows.UI.Xaml.Printing**](https://msdn.microsoft.com/library/windows/apps/BR243325) namespace along with other types that support preparing XAML content for printing.</span></span> <span data-ttu-id="e92c4-126">Sie können das Schreiben eines eigenen Druckcodes vereinfachen, indem Sie der Seite die folgenden **using**- oder **Imports**-Anweisungen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e92c4-126">You can make it easier to write your printing code by adding the following **using** or **Imports** statements to your page.</span></span>

```csharp
using Windows.UI.Xaml;
using Windows.UI.Xaml.Controls;
```

<span data-ttu-id="e92c4-127">Die [**PrintDocument**](https://msdn.microsoft.com/library/windows/apps/BR243314)-Klasse wird verwendet, um den Großteil der Interaktion zwischen der App und dem [**PrintManager**](https://msdn.microsoft.com/library/windows/apps/BR226426) zu behandeln. Sie macht jedoch auch verschiedene eigene Rückrufe verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e92c4-127">The [**PrintDocument**](https://msdn.microsoft.com/library/windows/apps/BR243314) class is used to handle much of the interaction between the app and the [**PrintManager**](https://msdn.microsoft.com/library/windows/apps/BR226426), but it exposes several callbacks of its own.</span></span> <span data-ttu-id="e92c4-128">Erstellen Sie während der Registrierung Instanzen der Klassen **PrintManager** und **PrintDocument**, und registrieren Sie Handler für deren Druckereignisse.</span><span class="sxs-lookup"><span data-stu-id="e92c4-128">During registration, create instances of **PrintManager** and **PrintDocument** and register handlers for their printing events.</span></span>

<span data-ttu-id="e92c4-129">Im [UWP-Druckbeispiel](http://go.microsoft.com/fwlink/p/?LinkId=619984) wird die Registrierung von der `RegisterForPrinting`-Methode durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="e92c4-129">In the [UWP print sample](http://go.microsoft.com/fwlink/p/?LinkId=619984), registration is performed by the `RegisterForPrinting` method.</span></span>

```csharp
public virtual void RegisterForPrinting()
{
   printDocument = new PrintDocument();
   printDocumentSource = printDocument.DocumentSource;
   printDocument.Paginate += CreatePrintPreviewPages;
   printDocument.GetPreviewPage += GetPrintPreviewPage;
   printDocument.AddPages += AddPrintPages;

   PrintManager printMan = PrintManager.GetForCurrentView();
   printMan.PrintTaskRequested += PrintTaskRequested;
}
```

<span data-ttu-id="e92c4-130">Wenn der Benutzer zu einer Seite wechselt, die das Drucken unterstützt, wird die Registrierung innerhalb der `OnNavigatedTo`-Methode initiiert.</span><span class="sxs-lookup"><span data-stu-id="e92c4-130">When the user goes to a page that supports printing, it initiates the registration within the `OnNavigatedTo` method.</span></span>

```csharp
protected override void OnNavigatedTo(NavigationEventArgs e)
{
   // Initialize common helper class and register for printing
   printHelper = new PrintHelper(this);
   printHelper.RegisterForPrinting();

   // Initialize print content for this scenario
   printHelper.PreparePrintContent(new PageToPrint());

   // Tell the user how to print
   MainPage.Current.NotifyUser("Print contract registered with customization, use the Print button to print.", NotifyType.StatusMessage);
}
```

<span data-ttu-id="e92c4-131">Wenn der Benutzer die Seite verlässt, trennen Sie die Verbindung mit den Druckereignishandlern.</span><span class="sxs-lookup"><span data-stu-id="e92c4-131">When the user leaves the page, disconnect the printing event handlers.</span></span> <span data-ttu-id="e92c4-132">Falls Sie bei einer App mit mehreren Seiten die Verbindung nicht trennen, wird eine Ausnahme ausgelöst, wenn der Benutzer die Seite verlässt und sie dann erneut aufruft.</span><span class="sxs-lookup"><span data-stu-id="e92c4-132">If you have a multiple-page app and don't disconnect printing, an exception is thrown when the user leaves the page and then comes back to it.</span></span>

```csharp
protected override void OnNavigatedFrom(NavigationEventArgs e)
{
   if (printHelper != null)
   {
         printHelper.UnregisterForPrinting();
   }
}
```
## <a name="create-a-print-button"></a><span data-ttu-id="e92c4-133">Erstellen einer Druckschaltfläche</span><span class="sxs-lookup"><span data-stu-id="e92c4-133">Create a print button</span></span>

<span data-ttu-id="e92c4-134">Fügen Sie eine Druckschaltfläche an der gewünschten Stelle auf dem App-Bildschirm hinzu.</span><span class="sxs-lookup"><span data-stu-id="e92c4-134">Add a print button to your app's screen where you'd like it to appear.</span></span> <span data-ttu-id="e92c4-135">Stellen Sie sicher, dass sie den zu druckenden Inhalt nicht verdeckt oder anderweitig stört.</span><span class="sxs-lookup"><span data-stu-id="e92c4-135">Make sure that it doesn't interfere with the content that you want to print.</span></span>

```xml
<Button x:Name="InvokePrintingButton" Content="Print" Click="OnPrintButtonClick"/>
```

<span data-ttu-id="e92c4-136">Als Nächstes fügen Sie einen Ereignishandler zum Behandeln des Click-Ereignisses zum Code Ihrer App hinzu.</span><span class="sxs-lookup"><span data-stu-id="e92c4-136">Next, add an event handler to your app's code to handle the click event.</span></span> <span data-ttu-id="e92c4-137">Verwenden Sie die [**ShowPrintUIAsync**](https://msdn.microsoft.com/library/windows/apps/windows.graphics.printing.printmanager.showprintuiasync)-Methode, um das Drucken über Ihre App zu starten.</span><span class="sxs-lookup"><span data-stu-id="e92c4-137">Use the [**ShowPrintUIAsync**](https://msdn.microsoft.com/library/windows/apps/windows.graphics.printing.printmanager.showprintuiasync) method to start printing from your app.</span></span> <span data-ttu-id="e92c4-138">**ShowPrintUIAsync** ist eine asynchrone Methode, die das entsprechende Druckfenster anzeigt.</span><span class="sxs-lookup"><span data-stu-id="e92c4-138">**ShowPrintUIAsync** is an asynchronous method that displays the appropriate printing window.</span></span> <span data-ttu-id="e92c4-139">Wir empfehlen zunächst den Aufruf der [ **IsSupported** ](https://msdn.microsoft.com/library/windows/apps/Windows.Graphics.Printing.PrintManager.IsSupported)-Methode, um zu prüfen, ob die App auf einem gerät ausgeführt wird, das den Druck unterstützt (und den Fall behandelt, wenn dies nicht der Fall ist).</span><span class="sxs-lookup"><span data-stu-id="e92c4-139">We recommend calling the [**IsSupported**](https://msdn.microsoft.com/library/windows/apps/Windows.Graphics.Printing.PrintManager.IsSupported) method first in order to check that the app is being run on a device that supports printing (and handle the case in which it is not).</span></span> <span data-ttu-id="e92c4-140">Wenn das Drucken zu diesem Zeitpunkt aus einem anderen Grund nicht ausgeführt werden kann, gibt**ShowPrintUIAsync** eine Ausnahme aus.</span><span class="sxs-lookup"><span data-stu-id="e92c4-140">If printing can't be performed at that time for any other reason, **ShowPrintUIAsync** will throw an exception.</span></span> <span data-ttu-id="e92c4-141">Es wird empfohlen, die Ausnahmen abzufangen und dem Benutzer mitzuteilen, wenn der Druckvorgang nicht fortgesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="e92c4-141">We recommend catching these exceptions and letting the user know when printing can't proceed.</span></span>

```csharp
async private void OnPrintButtonClick(object sender, RoutedEventArgs e)
{
    if (Windows.Graphics.Printing.PrintManager.IsSupported())
    {
        try
        {
            // Show print UI
            await Windows.Graphics.Printing.PrintManager.ShowPrintUIAsync();

        }
        catch
        {
            // Printing cannot proceed at this time
            ContentDialog noPrintingDialog = new ContentDialog()
            {
                Title = "Printing error",
                Content = "\nSorry, printing can' t proceed at this time.", PrimaryButtonText = "OK"
            };
            await noPrintingDialog.ShowAsync();
        }
    }
    else
    {
        // Printing is not supported on this device
        ContentDialog noPrintingDialog = new ContentDialog()
        {
            Title = "Printing not supported",
            Content = "\nSorry, printing is not supported on this device.",PrimaryButtonText = "OK"
        };
        await noPrintingDialog.ShowAsync();
    }
}
```

<span data-ttu-id="e92c4-142">In diesem Beispiel wird ein Druckfenster im Ereignishandler für das Klicken auf eine Schaltfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e92c4-142">In this example, a print window is displayed in the event handler for a button click.</span></span> <span data-ttu-id="e92c4-143">Wenn die Methode eine Ausnahme auslöst (da das Drucken zu diesem Zeitpunkt nicht möglich ist), informiert ein [**ContentDialog**](https://msdn.microsoft.com/library/windows/apps/Dn633972)-Steuerelement den Benutzer über die Situation.</span><span class="sxs-lookup"><span data-stu-id="e92c4-143">If the method throws an exception (because printing can't be performed at that time), a [**ContentDialog**](https://msdn.microsoft.com/library/windows/apps/Dn633972) control informs the user of the situation.</span></span>

## <a name="format-your-apps-content"></a><span data-ttu-id="e92c4-144">Formatieren der App-Inhalte</span><span class="sxs-lookup"><span data-stu-id="e92c4-144">Format your app's content</span></span>

<span data-ttu-id="e92c4-145">Wenn **ShowPrintUIAsync** aufgerufen wird, wird das [**PrintTaskRequested**](https://msdn.microsoft.com/library/windows/apps/br206597)-Ereignis ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="e92c4-145">When **ShowPrintUIAsync** is called, the [**PrintTaskRequested**](https://msdn.microsoft.com/library/windows/apps/br206597) event is raised.</span></span> <span data-ttu-id="e92c4-146">Der in diesem Schritt gezeigte **PrintTaskRequested**-Ereignishandler erstellt eine [**PrintTask**](https://msdn.microsoft.com/library/windows/apps/BR226436)-Klasse, indem er die [**PrintTaskRequest.CreatePrintTask**](https://msdn.microsoft.com/library/windows/apps/windows.graphics.printing.printtaskrequest.createprinttask.aspx)-Methode aufruft und den Titel für die zu druckende Seite sowie den Namen eines [**PrintTaskSourceRequestedHandler**](https://msdn.microsoft.com/library/windows/apps/windows.graphics.printing.printtask.source) -Delegaten übergibt.</span><span class="sxs-lookup"><span data-stu-id="e92c4-146">The **PrintTaskRequested** event handler shown in this step creates a [**PrintTask**](https://msdn.microsoft.com/library/windows/apps/BR226436) by calling the [**PrintTaskRequest.CreatePrintTask**](https://msdn.microsoft.com/library/windows/apps/windows.graphics.printing.printtaskrequest.createprinttask.aspx) method and passes the title for the print page and the name of a [**PrintTaskSourceRequestedHandler**](https://msdn.microsoft.com/library/windows/apps/windows.graphics.printing.printtask.source) delegate.</span></span> <span data-ttu-id="e92c4-147">Beachten Sie, dass **PrintTaskSourceRequestedHandler** in diesem Beispiel inline definiert wird.</span><span class="sxs-lookup"><span data-stu-id="e92c4-147">Notice that in this example, the **PrintTaskSourceRequestedHandler** is defined inline.</span></span> <span data-ttu-id="e92c4-148">**PrintTaskSourceRequestedHandler** stellt den formatierten Inhalt für das Drucken bereit und wird an späterer Stelle beschrieben.</span><span class="sxs-lookup"><span data-stu-id="e92c4-148">The **PrintTaskSourceRequestedHandler** provides the formatted content for printing and is described later.</span></span>

<span data-ttu-id="e92c4-149">In diesem Beispiel wurde außerdem ein Abschlusshandler definiert, um Fehler aufzufangen.</span><span class="sxs-lookup"><span data-stu-id="e92c4-149">In this example, a completion handler is also defined to catch errors.</span></span> <span data-ttu-id="e92c4-150">Es empfiehlt sich, Abschlussereignisse zu behandeln, da die App den Benutzer dann über aufgetretene Fehler und mögliche Lösungen informieren kann.</span><span class="sxs-lookup"><span data-stu-id="e92c4-150">It's a good idea to handle completion events because then your app can let the user know if an error occurred and provide possible solutions.</span></span> <span data-ttu-id="e92c4-151">Die App kann das Abschlussereignis auch verwenden, um nachfolgende Schritte anzugeben, die der Benutzer nach einem erfolgreichen Druckauftrag ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="e92c4-151">Likewise, your app could use the completion event to indicate subsequent steps for the user to take after the print job is successful.</span></span>

```csharp
protected virtual void PrintTaskRequested(PrintManager sender, PrintTaskRequestedEventArgs e)
{
   PrintTask printTask = null;
   printTask = e.Request.CreatePrintTask("C# Printing SDK Sample", sourceRequested =>
   {
         // Print Task event handler is invoked when the print job is completed.
         printTask.Completed += async (s, args) =>
         {
            // Notify the user when the print operation fails.
            if (args.Completion == PrintTaskCompletion.Failed)
            {
               await scenarioPage.Dispatcher.RunAsync(Windows.UI.Core.CoreDispatcherPriority.Normal, () =>
               {
                     MainPage.Current.NotifyUser("Failed to print.", NotifyType.ErrorMessage);
               });
            }
         };

         sourceRequested.SetSource(printDocumentSource);
   });
}
```

<span data-ttu-id="e92c4-152">Nachdem die Druckaufgabe erstellt wurde, löst der [**PrintManager**](https://msdn.microsoft.com/library/windows/apps/BR226426) das [**Paginate**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.printing.printdocument.paginate)-Ereignis aus, um eine Sammlung zu druckender Seiten anzufordern, die auf der Druckvorschau-Benutzeroberfläche angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e92c4-152">After the print task is created, the [**PrintManager**](https://msdn.microsoft.com/library/windows/apps/BR226426) requests a collection of print pages to show in the print preview UI by raising the [**Paginate**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.printing.printdocument.paginate) event.</span></span> <span data-ttu-id="e92c4-153">Dies entspricht der **Paginate**-Methode der **IPrintPreviewPageCollection**-Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="e92c4-153">This corresponds with the **Paginate** method of the **IPrintPreviewPageCollection** interface.</span></span> <span data-ttu-id="e92c4-154">Der Ereignishandler, den Sie bei der Registrierung erstellt haben, wird zu diesem Zeitpunkt aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="e92c4-154">The event handler you created during registration will be called at this time.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e92c4-155">Wenn der Benutzer die Druckeinstellungen ändert, wird der Ereignishandler für die Aufteilung auf Seiten erneut aufgerufen, damit Sie den Inhalt umbrechen können.</span><span class="sxs-lookup"><span data-stu-id="e92c4-155">If the user changes print settings, the paginate event handler will be called again to allow you to reflow the content.</span></span> <span data-ttu-id="e92c4-156">Für die bestmögliche Benutzerfreundlichkeit wird empfohlen, die Einstellungen zu überprüfen, bevor Sie den Inhalt umbrechen und die erneute Initialisierung der auf Seiten aufgeteilten Inhalte vermeiden, wenn dies nicht erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="e92c4-156">For the best user experience, we recommend checking the settings before you reflow the content and avoid reinitializing the paginated content when it's not necessary.</span></span>

<span data-ttu-id="e92c4-157">Im [**Paginate**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.printing.printdocument.paginate)-Ereignishandler (der `CreatePrintPreviewPages`-Methode im [UWP-Druckbeispiel](http://go.microsoft.com/fwlink/p/?LinkId=619984)) erstellen Sie die Seiten, die auf der Druckvorschau-Benutzeroberfläche angezeigt und an den Drucker gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="e92c4-157">In the [**Paginate**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.printing.printdocument.paginate) event handler (the `CreatePrintPreviewPages` method in the [UWP print sample](http://go.microsoft.com/fwlink/p/?LinkId=619984)), create the pages to show in the print preview UI and to send to the printer.</span></span> <span data-ttu-id="e92c4-158">Der Code zum Vorbereiten der App-Inhalte für den Druck muss speziell an Ihre App und die gedruckten Inhalte angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="e92c4-158">The code you use to prepare your app's content for printing is specific to your app and the content you print.</span></span> <span data-ttu-id="e92c4-159">Im Quellcode für das [UWP-Druckbeispiel](http://go.microsoft.com/fwlink/p/?LinkId=619984) können Sie sehen, wie der Inhalt für das Drucken formatiert wird.</span><span class="sxs-lookup"><span data-stu-id="e92c4-159">Refer to the [UWP print sample](http://go.microsoft.com/fwlink/p/?LinkId=619984) source code to see how it formats its content for printing.</span></span>

```csharp
protected virtual void CreatePrintPreviewPages(object sender, PaginateEventArgs e)
{
   // Clear the cache of preview pages
   printPreviewPages.Clear();

   // Clear the print canvas of preview pages
   PrintCanvas.Children.Clear();

   // This variable keeps track of the last RichTextBlockOverflow element that was added to a page which will be printed
   RichTextBlockOverflow lastRTBOOnPage;

   // Get the PrintTaskOptions
   PrintTaskOptions printingOptions = ((PrintTaskOptions)e.PrintTaskOptions);

   // Get the page description to deterimine how big the page is
   PrintPageDescription pageDescription = printingOptions.GetPageDescription(0);

   // We know there is at least one page to be printed. passing null as the first parameter to
   // AddOnePrintPreviewPage tells the function to add the first page.
   lastRTBOOnPage = AddOnePrintPreviewPage(null, pageDescription);

   // We know there are more pages to be added as long as the last RichTextBoxOverflow added to a print preview
   // page has extra content
   while (lastRTBOOnPage.HasOverflowContent && lastRTBOOnPage.Visibility == Windows.UI.Xaml.Visibility.Visible)
   {
         lastRTBOOnPage = AddOnePrintPreviewPage(lastRTBOOnPage, pageDescription);
   }

   if (PreviewPagesCreated != null)
   {
         PreviewPagesCreated.Invoke(printPreviewPages, null);
   }

   PrintDocument printDoc = (PrintDocument)sender;

   // Report the number of preview pages created
   printDoc.SetPreviewPageCount(printPreviewPages.Count, PreviewPageCountType.Intermediate);
}
```

<span data-ttu-id="e92c4-160">Wenn eine bestimmte Seite in der Druckvorschau angezeigt werden soll, löst [**PrintManager**](https://msdn.microsoft.com/library/windows/apps/BR226426) das [**GetPreviewPage**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.printing.printdocument.getpreviewpage)-Ereignis aus.</span><span class="sxs-lookup"><span data-stu-id="e92c4-160">When a particular page is to be shown in the print preview window, the [**PrintManager**](https://msdn.microsoft.com/library/windows/apps/BR226426) raises the [**GetPreviewPage**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.printing.printdocument.getpreviewpage) event.</span></span> <span data-ttu-id="e92c4-161">Dies entspricht der **MakePage**-Methode der **IPrintPreviewPageCollection**-Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="e92c4-161">This corresponds with the **MakePage** method of the **IPrintPreviewPageCollection** interface.</span></span> <span data-ttu-id="e92c4-162">Der Ereignishandler, den Sie bei der Registrierung erstellt haben, wird zu diesem Zeitpunkt aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="e92c4-162">The event handler you created during registration will be called at this time.</span></span>

<span data-ttu-id="e92c4-163">Legen Sie im [**GetPreviewPage**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.printing.printdocument.getpreviewpage)-Ereignishandler (der `GetPrintPreviewPage`-Methode im [UWP-Druckbeispiel](http://go.microsoft.com/fwlink/p/?LinkId=619984)) die entsprechende Seite des Druckdokuments fest.</span><span class="sxs-lookup"><span data-stu-id="e92c4-163">In the [**GetPreviewPage**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.printing.printdocument.getpreviewpage) event handler (the `GetPrintPreviewPage` method in the [UWP print sample](http://go.microsoft.com/fwlink/p/?LinkId=619984)), set the appropriate page on the print document.</span></span>

```csharp
protected virtual void GetPrintPreviewPage(object sender, GetPreviewPageEventArgs e)
{
   PrintDocument printDoc = (PrintDocument)sender;
   printDoc.SetPreviewPage(e.PageNumber, printPreviewPages[e.PageNumber - 1]);
}
```

<span data-ttu-id="e92c4-164">Nachdem der Benutzer auf die Druckschaltfläche geklickt hat, fordert [**PrintManager**](https://msdn.microsoft.com/library/windows/apps/BR226426) die abschließende Sammlung der an den Drucker zu sendenden Seiten an, indem die **MakeDocument**-Methode der **IDocumentPageSource**-Schnittstelle aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="e92c4-164">Finally, once the user clicks the print button, the [**PrintManager**](https://msdn.microsoft.com/library/windows/apps/BR226426) requests the final collection of pages to send to the printer by calling the **MakeDocument** method of the **IDocumentPageSource** interface.</span></span> <span data-ttu-id="e92c4-165">In XAML löst dies das [**AddPages**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.printing.printdocument.addpages)-Ereignis aus.</span><span class="sxs-lookup"><span data-stu-id="e92c4-165">In XAML, this raises the [**AddPages**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.printing.printdocument.addpages) event.</span></span> <span data-ttu-id="e92c4-166">Der Ereignishandler, den Sie bei der Registrierung erstellt haben, wird zu diesem Zeitpunkt aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="e92c4-166">The event handler you created during registration will be called at this time.</span></span>

<span data-ttu-id="e92c4-167">Im [**AddPages**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.printing.printdocument.addpages)-Ereignishandler (der `AddPrintPages`-Methode im [UWP-Druckbeispiel](http://go.microsoft.com/fwlink/p/?LinkId=619984)) fügen Sie dem [**PrintDocument**](https://msdn.microsoft.com/library/windows/apps/BR243314)-Objekt, das an den Drucker gesendet werden soll, Seiten aus der Seitensammlung hinzu.</span><span class="sxs-lookup"><span data-stu-id="e92c4-167">In the [**AddPages**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.printing.printdocument.addpages) event handler (the `AddPrintPages` method in the [UWP print sample](http://go.microsoft.com/fwlink/p/?LinkId=619984)), add pages from the page collection to the [**PrintDocument**](https://msdn.microsoft.com/library/windows/apps/BR243314) object to be sent to the printer.</span></span> <span data-ttu-id="e92c4-168">Wenn ein Benutzer bestimmte Seiten oder einen Seitenbereich zum Drucken angibt, verwenden Sie diese Informationen, um nur die Seiten hinzuzufügen, die tatsächlich an den Drucker gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="e92c4-168">If a user specifies particular pages or a range of pages to print, you use that information here to add only the pages that will actually be sent to the printer.</span></span>

```csharp
protected virtual void AddPrintPages(object sender, AddPagesEventArgs e)
{
   // Loop over all of the preview pages and add each one to  add each page to be printied
   for (int i = 0; i < printPreviewPages.Count; i++)
   {
         // We should have all pages ready at this point...
         printDocument.AddPage(printPreviewPages[i]);
   }

   PrintDocument printDoc = (PrintDocument)sender;

   // Indicate that all of the print pages have been provided
   printDoc.AddPagesComplete();
}
```

## <a name="prepare-print-options"></a><span data-ttu-id="e92c4-169">Vorbereiten von Druckoptionen</span><span class="sxs-lookup"><span data-stu-id="e92c4-169">Prepare print options</span></span>

<span data-ttu-id="e92c4-170">Als Nächstes bereiten Sie Druckoptionen vor.</span><span class="sxs-lookup"><span data-stu-id="e92c4-170">Next prepare print options.</span></span> <span data-ttu-id="e92c4-171">Dieser Abschnitt beschreibt als Beispiel, wie die Seitenbereichsoption festgelegt wird, um das Drucken bestimmter Seiten zu gestatten.</span><span class="sxs-lookup"><span data-stu-id="e92c4-171">As an example, this section will describe how to set the page range option to allow printing of specific pages.</span></span> <span data-ttu-id="e92c4-172">Weitere Optionen finden Sie unter [Anpassen der Benutzeroberfläche für die Druckvorschau](customize-the-print-preview-ui.md).</span><span class="sxs-lookup"><span data-stu-id="e92c4-172">For more advanced options, see [Customize the print preview UI](customize-the-print-preview-ui.md).</span></span>

<span data-ttu-id="e92c4-173">In diesem Schritt wird eine neue Druckoption erstellt und eine Liste von Werten definiert, die die Option unterstützt. Dann wird die Option der Druckvorschau-UI hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="e92c4-173">This step creates a new print option, defines a list of values that the option supports, and then adds the option to the print preview UI.</span></span> <span data-ttu-id="e92c4-174">Die Seitenbereichsoption hat folgende Einstellungen:</span><span class="sxs-lookup"><span data-stu-id="e92c4-174">The page range option has these settings:</span></span>

| <span data-ttu-id="e92c4-175">Optionsname</span><span class="sxs-lookup"><span data-stu-id="e92c4-175">Option name</span></span>          | <span data-ttu-id="e92c4-176">Aktion</span><span class="sxs-lookup"><span data-stu-id="e92c4-176">Action</span></span> |
|----------------------|--------|
| **<span data-ttu-id="e92c4-177">Print all</span><span class="sxs-lookup"><span data-stu-id="e92c4-177">Print all</span></span>**        | <span data-ttu-id="e92c4-178">Druckt alle Seiten im Dokument.</span><span class="sxs-lookup"><span data-stu-id="e92c4-178">Print all pages in the document.</span></span>|
| **<span data-ttu-id="e92c4-179">Print Selection</span><span class="sxs-lookup"><span data-stu-id="e92c4-179">Print Selection</span></span>**  | <span data-ttu-id="e92c4-180">Druckt nur den vom Benutzer ausgewählten Inhalt.</span><span class="sxs-lookup"><span data-stu-id="e92c4-180">Print only the content the user selected.</span></span>|
| **<span data-ttu-id="e92c4-181">Print Range</span><span class="sxs-lookup"><span data-stu-id="e92c4-181">Print Range</span></span>**      | <span data-ttu-id="e92c4-182">Zeigt ein Bearbeitungssteuerelement an, in das der Benutzer die zu druckenden Seiten eingeben kann.</span><span class="sxs-lookup"><span data-stu-id="e92c4-182">Display an edit control into which the user can enter the pages to print.</span></span>|

<span data-ttu-id="e92c4-183">Ändern Sie zunächst den [**PrintTaskRequested**](https://msdn.microsoft.com/library/windows/apps/br206597)-Ereignishandler, um den Code zum Abrufen eines [**PrintTaskOptionDetails**](https://msdn.microsoft.com/library/windows/apps/Hh701256)-Objekts hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="e92c4-183">First, modify the [**PrintTaskRequested**](https://msdn.microsoft.com/library/windows/apps/br206597) event handler to add the code to get a [**PrintTaskOptionDetails**](https://msdn.microsoft.com/library/windows/apps/Hh701256) object.</span></span>

```csharp
PrintTaskOptionDetails printDetailedOptions = PrintTaskOptionDetails.GetFromPrintTaskOptions(printTask.Options);
```

<span data-ttu-id="e92c4-184">Löschen Sie die Liste der Optionen, die in der Druckvorschau-Benutzeroberfläche angezeigt werden, und fügen Sie die Optionen hinzu, die angezeigt werden sollen, wenn der Benutzer in der App druckt.</span><span class="sxs-lookup"><span data-stu-id="e92c4-184">Clear the list of options that are shown in the print preview UI and add the options that you want to display when the user wants to print from the app.</span></span>

> [!NOTE]
> <span data-ttu-id="e92c4-185">Die Optionen werden in der Druckvorschau-Benutzeroberfläche in der Reihenfolge angezeigt, in der sie hinzugefügt werden, wobei die erste Option oben im Fenster erscheint.</span><span class="sxs-lookup"><span data-stu-id="e92c4-185">The options appear in the print preview UI in the same order they are appended, with the first option shown at the top of the window.</span></span>

```csharp
IList<string> displayedOptions = printDetailedOptions.DisplayedOptions;

displayedOptions.Clear();
displayedOptions.Add(Windows.Graphics.Printing.StandardPrintTaskOptions.Copies);
displayedOptions.Add(Windows.Graphics.Printing.StandardPrintTaskOptions.Orientation);
displayedOptions.Add(Windows.Graphics.Printing.StandardPrintTaskOptions.ColorMode);
```

<span data-ttu-id="e92c4-186">Erstellen Sie die neue Druckoption, und initialisieren Sie die Liste der Optionswerte.</span><span class="sxs-lookup"><span data-stu-id="e92c4-186">Create the new print option and initialize the list of option values.</span></span>

```csharp
// Create a new list option
PrintCustomItemListOptionDetails pageFormat = printDetailedOptions.CreateItemListOption("PageRange", "Page Range");
pageFormat.AddItem("PrintAll", "Print all");
pageFormat.AddItem("PrintSelection", "Print Selection");
pageFormat.AddItem("PrintRange", "Print Range");
```

<span data-ttu-id="e92c4-187">Fügen Sie Ihre benutzerdefinierte Druckoption hinzu, und weisen Sie den Ereignishandler zu.</span><span class="sxs-lookup"><span data-stu-id="e92c4-187">Add your custom print option and assign the event handler.</span></span> <span data-ttu-id="e92c4-188">Die benutzerdefinierte Option wird als Letztes hinzugefügt, sodass sie am Ende der Optionsliste erscheint.</span><span class="sxs-lookup"><span data-stu-id="e92c4-188">The custom option is appended last so that it appears at the bottom of the list of options.</span></span> <span data-ttu-id="e92c4-189">Sie können sie aber an einer beliebigen Stelle der Liste platzieren. Benutzerdefinierte Druckoptionen müssen nicht zuletzt hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="e92c4-189">But you can put it anywhere in the list, custom print options don't need to be added last.</span></span>

```csharp
// Add the custom option to the option list
displayedOptions.Add("PageRange");

// Create new edit option
PrintCustomTextOptionDetails pageRangeEdit = printDetailedOptions.CreateTextOption("PageRangeEdit", "Range");

// Register the handler for the option change event
printDetailedOptions.OptionChanged += printDetailedOptions_OptionChanged;
```

<span data-ttu-id="e92c4-190">Die [**CreateTextOption**](https://msdn.microsoft.com/library/windows/apps/windows.graphics.printing.optiondetails.printtaskoptiondetails.createtextoption)-Methode erstellt das Textfeld **Bereich**.</span><span class="sxs-lookup"><span data-stu-id="e92c4-190">The [**CreateTextOption**](https://msdn.microsoft.com/library/windows/apps/windows.graphics.printing.optiondetails.printtaskoptiondetails.createtextoption) method creates the **Range** text box.</span></span> <span data-ttu-id="e92c4-191">Hier gibt der Benutzer die zu druckenden Seiten ein, wenn die Option **Druckbereich** ausgewählt wurde.</span><span class="sxs-lookup"><span data-stu-id="e92c4-191">This is where the user enters the specific pages they want to print when they select the **Print Range** option.</span></span>

## <a name="handle-print-option-changes"></a><span data-ttu-id="e92c4-192">Behandeln von Druckoptionsänderungen</span><span class="sxs-lookup"><span data-stu-id="e92c4-192">Handle print option changes</span></span>

<span data-ttu-id="e92c4-193">Der **OptionChanged**-Ereignishandler ist im Wesentlichen für zwei Dinge zuständig.</span><span class="sxs-lookup"><span data-stu-id="e92c4-193">The **OptionChanged** event handler does two things.</span></span> <span data-ttu-id="e92c4-194">Erstens blendet er das Texteingabefeld für den Seitenbereich je nach der vom Benutzer ausgewählten Seitenbereichsoption ein und aus.</span><span class="sxs-lookup"><span data-stu-id="e92c4-194">First, it shows and hides the text edit field for the page range depending on the page range option that the user selected.</span></span> <span data-ttu-id="e92c4-195">Zweitens testet er den Text, den der Benutzer in das Seitenbereich-Textfeld eingibt, um sicherzustellen, dass es sich um einen gültigen Seitenbereich für das Dokument handelt.</span><span class="sxs-lookup"><span data-stu-id="e92c4-195">Second, it tests the text entered into the page range text box to make sure that it represents a valid page range for the document.</span></span>

<span data-ttu-id="e92c4-196">Dieses Beispiel zeigt, wie das [UWP-Druckbeispiel](http://go.microsoft.com/fwlink/p/?LinkId=619984) Änderungsereignisse behandelt.</span><span class="sxs-lookup"><span data-stu-id="e92c4-196">This example shows how the [UWP print sample](http://go.microsoft.com/fwlink/p/?LinkId=619984) handles change events.</span></span>

```csharp
async void printDetailedOptions_OptionChanged(PrintTaskOptionDetails sender, PrintTaskOptionChangedEventArgs args)
{
   if (args.OptionId == null)
   {
         return;
   }

   string optionId = args.OptionId.ToString();

   // Handle change in Page Range Option
   if (optionId == "PageRange")
   {
         IPrintOptionDetails pageRange = sender.Options[optionId];
         string pageRangeValue = pageRange.Value.ToString();

         selectionMode = false;

         switch (pageRangeValue)
         {
            case "PrintRange":
               // Add PageRangeEdit custom option to the option list
               sender.DisplayedOptions.Add("PageRangeEdit");
               pageRangeEditVisible = true;
               await scenarioPage.Dispatcher.RunAsync(Windows.UI.Core.CoreDispatcherPriority.Normal, () =>
               {
                     ShowContent(null);
               });
               break;
            case "PrintSelection":
               await scenarioPage.Dispatcher.RunAsync(Windows.UI.Core.CoreDispatcherPriority.Normal, () =>
               {
                     Scenario4PageRange page = (Scenario4PageRange)scenarioPage;
                     PageToPrint pageContent = (PageToPrint)page.PrintFrame.Content;
                     ShowContent(pageContent.TextContentBlock.SelectedText);
               });
               RemovePageRangeEdit(sender);
               break;
            default:
               await scenarioPage.Dispatcher.RunAsync(Windows.UI.Core.CoreDispatcherPriority.Normal, () =>
               {
                     ShowContent(null);
               });
               RemovePageRangeEdit(sender);
               break;
         }

         Refresh();
   }
   else if (optionId == "PageRangeEdit")
   {
         IPrintOptionDetails pageRange = sender.Options[optionId];
         // Expected range format (p1,p2...)*, (p3-p9)* ...
         if (!Regex.IsMatch(pageRange.Value.ToString(), @"^\s*\d+\s*(\-\s*\d+\s*)?(\,\s*\d+\s*(\-\s*\d+\s*)?)*$"))
         {
            pageRange.ErrorText = "Invalid Page Range (eg: 1-3, 5)";
         }
         else
         {
            pageRange.ErrorText = string.Empty;
            try
            {
               GetPagesInRange(pageRange.Value.ToString());
               Refresh();
            }
            catch (InvalidPageException ipex)
            {
               pageRange.ErrorText = ipex.Message;
            }
         }
   }
}
```

> [!TIP]
> <span data-ttu-id="e92c4-197">Weitere Informationen zum Analysieren des vom Benutzer in das Textfeld für den Bereich eingegebenen Seitenbereichs finden Sie in der `GetPagesInRange`-Methode im [UWP-Druckbeispiel](http://go.microsoft.com/fwlink/p/?LinkId=619984).</span><span class="sxs-lookup"><span data-stu-id="e92c4-197">See the `GetPagesInRange` method in the [UWP print sample](http://go.microsoft.com/fwlink/p/?LinkId=619984) for details on how to parse the page range the user enters in the Range text box.</span></span>

## <a name="preview-selected-pages"></a><span data-ttu-id="e92c4-198">Vorschau auf ausgewählte Seiten</span><span class="sxs-lookup"><span data-stu-id="e92c4-198">Preview selected pages</span></span>

<span data-ttu-id="e92c4-199">Die Formatierung des Inhalts Ihrer App zum Drucken hängt von der Art der App und deren Inhalt ab.</span><span class="sxs-lookup"><span data-stu-id="e92c4-199">How you format your app's content for printing depends on the nature of your app and its content.</span></span> <span data-ttu-id="e92c4-200">Das [UWP-Druckbeispiel](http://go.microsoft.com/fwlink/p/?LinkId=619984) verwendet eine Druckhilfsprogrammklasse, um seinen Inhalt für den Druckvorgang zu formatieren.</span><span class="sxs-lookup"><span data-stu-id="e92c4-200">The [UWP print sample](http://go.microsoft.com/fwlink/p/?LinkId=619984) uses a print helper class to format its content for printing.</span></span>

<span data-ttu-id="e92c4-201">Wenn nur ein Teil der Seiten gedruckt wird, gibt es mehrere Möglichkeiten, den Inhalt in der Druckvorschau anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="e92c4-201">When printing a subset of the pages, there are several ways to show the content in the print preview.</span></span> <span data-ttu-id="e92c4-202">Unabhängig davon, welche Methode Sie zum Anzeigen des Seitenbereichs in der Druckvorschau ausgewählt haben, darf der Ausdruck nur die ausgewählten Seiten enthalten.</span><span class="sxs-lookup"><span data-stu-id="e92c4-202">Regardless of the method you chose to show the page range in the print preview, the printed output must contain only the selected pages.</span></span>

-   <span data-ttu-id="e92c4-203">Alle Seiten in der Druckvorschau anzeigen, unabhängig davon, ob ein Seitenbereich festgelegt wurde. Der Benutzer muss selbst wissen, welche Seiten ausgedruckt werden.</span><span class="sxs-lookup"><span data-stu-id="e92c4-203">Show all the pages in the print preview whether a page range is specified or not, leaving the user to know which pages will actually be printed.</span></span>
-   <span data-ttu-id="e92c4-204">Nur den vom Benutzer ausgewählten Seitenbereich in der Druckvorschau anzeigen und die Anzeige aktualisieren, wenn der Benutzer den Seitenbereich ändert.</span><span class="sxs-lookup"><span data-stu-id="e92c4-204">Show only the pages selected by the user's page range in the print preview, updating the display whenever the user changes the page range.</span></span>
-   <span data-ttu-id="e92c4-205">Alle Seiten in der Druckvorschau anzeigen, dabei aber alle Seiten ausgrauen, die nicht in dem vom Benutzer ausgewählten Seitenbereich liegen.</span><span class="sxs-lookup"><span data-stu-id="e92c4-205">Show all the pages in print preview, but grey out the pages that are not in page range selected by the user.</span></span>

## <a name="related-topics"></a><span data-ttu-id="e92c4-206">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="e92c4-206">Related topics</span></span>

* [<span data-ttu-id="e92c4-207">Gestaltungsrichtlinien für Druckvorgänge</span><span class="sxs-lookup"><span data-stu-id="e92c4-207">Design guidelines for printing</span></span>](https://msdn.microsoft.com/library/windows/apps/Hh868178)
* [<span data-ttu-id="e92c4-208">//Build 2015-Video: Entwickeln von druckfähigen Apps in Windows 10</span><span class="sxs-lookup"><span data-stu-id="e92c4-208">//Build 2015 video: Developing apps that print in Windows 10</span></span>](https://channel9.msdn.com/Events/Build/2015/2-94)
* [<span data-ttu-id="e92c4-209">UWP-Druckbeispiel</span><span class="sxs-lookup"><span data-stu-id="e92c4-209">UWP print sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619984)
