---
author: PatrickFarley
ms.assetid: 88132B6F-FB50-4B03-BC21-233988746230
title: Anpassen der Benutzeroberfläche für die Druckvorschau
description: In diesem Abschnitt wird beschrieben, wie die Druckoptionen und -einstellungen in der Benutzeroberfläche für die Druckvorschau angepasst werden.
ms.author: pafarley
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Drucken
ms.localizationpriority: medium
ms.openlocfilehash: fe4086cc87699083304594eb4ccc8e7bb137b19f
ms.sourcegitcommit: c6d6f8b54253e79354f8db14e5cf3b113a3e5014
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "2834022"
---
# <a name="customize-the-print-preview-ui"></a><span data-ttu-id="ea349-104">Anpassen der Benutzeroberfläche für die Druckvorschau</span><span class="sxs-lookup"><span data-stu-id="ea349-104">Customize the print preview UI</span></span>



**<span data-ttu-id="ea349-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="ea349-105">Important APIs</span></span>**

-   [**<span data-ttu-id="ea349-106">Windows.Graphics.Printing</span><span class="sxs-lookup"><span data-stu-id="ea349-106">Windows.Graphics.Printing</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR226489)
-   [**<span data-ttu-id="ea349-107">Windows.UI.Xaml.Printing</span><span class="sxs-lookup"><span data-stu-id="ea349-107">Windows.UI.Xaml.Printing</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR243325)
-   [**<span data-ttu-id="ea349-108">PrintManager</span><span class="sxs-lookup"><span data-stu-id="ea349-108">PrintManager</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR226426)

<span data-ttu-id="ea349-109">In diesem Abschnitt wird beschrieben, wie die Druckoptionen und -einstellungen in der Benutzeroberfläche für die Druckvorschau angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="ea349-109">This section describes how to customize the print options and settings in the print preview UI.</span></span> <span data-ttu-id="ea349-110">Weitere Informationen zur Druckfunktion finden Sie unter [Drucken in Apps](print-from-your-app.md).</span><span class="sxs-lookup"><span data-stu-id="ea349-110">For more info about printing, see [Print from your app](print-from-your-app.md).</span></span>

<span data-ttu-id="ea349-111">**Tipp** Die Mehrzahl der Beispiele in diesem Thema basiert auf dem Druckbeispiel.</span><span class="sxs-lookup"><span data-stu-id="ea349-111">**Tip**  Most of the examples in this topic are based on the print sample.</span></span> <span data-ttu-id="ea349-112">Laden Sie das [Druckbeispiel für die universelle Windows-Plattform (UWP)](http://go.microsoft.com/fwlink/p/?LinkId=619984) aus dem Repository [Beispiele für Universelle Windows-Plattform](http://go.microsoft.com/fwlink/p/?LinkId=619979) auf GitHub herunter, um den vollständigen Code anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="ea349-112">To see the full code, download the [Universal Windows Platform (UWP) print sample](http://go.microsoft.com/fwlink/p/?LinkId=619984) from the [Windows-universal-samples repo](http://go.microsoft.com/fwlink/p/?LinkId=619979) on GitHub.</span></span>

 

## <a name="customize-print-options"></a><span data-ttu-id="ea349-113">Anpassen der Druckoptionen</span><span class="sxs-lookup"><span data-stu-id="ea349-113">Customize print options</span></span>

<span data-ttu-id="ea349-114">Standardmäßig werden in der Benutzeroberfläche für die Druckvorschau die Druckoptionen [**ColorMode**](https://msdn.microsoft.com/library/windows/apps/BR226478), [**Copies**](https://msdn.microsoft.com/library/windows/apps/BR226479) und [**Orientation**](https://msdn.microsoft.com/library/windows/apps/BR226486) angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ea349-114">By default, the print preview UI shows the [**ColorMode**](https://msdn.microsoft.com/library/windows/apps/BR226478), [**Copies**](https://msdn.microsoft.com/library/windows/apps/BR226479), and [**Orientation**](https://msdn.microsoft.com/library/windows/apps/BR226486) print options.</span></span> <span data-ttu-id="ea349-115">Neben diesen Optionen sind weitere allgemeine Druckeroptionen verfügbar, die Sie der Benutzeroberfläche für die Druckvorschau hinzufügen können:</span><span class="sxs-lookup"><span data-stu-id="ea349-115">In addition to those, there are several other common printer options that you can add to the print preview UI:</span></span>

-   [**<span data-ttu-id="ea349-116">Binding</span><span class="sxs-lookup"><span data-stu-id="ea349-116">Binding</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR226476)
-   [**<span data-ttu-id="ea349-117">Collation</span><span class="sxs-lookup"><span data-stu-id="ea349-117">Collation</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR226477)
-   [**<span data-ttu-id="ea349-118">Duplex</span><span class="sxs-lookup"><span data-stu-id="ea349-118">Duplex</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR226480)
-   [**<span data-ttu-id="ea349-119">HolePunch</span><span class="sxs-lookup"><span data-stu-id="ea349-119">HolePunch</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR226481)
-   [**<span data-ttu-id="ea349-120">InputBin</span><span class="sxs-lookup"><span data-stu-id="ea349-120">InputBin</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR226482)
-   [**<span data-ttu-id="ea349-121">MediaSize</span><span class="sxs-lookup"><span data-stu-id="ea349-121">MediaSize</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR226483)
-   [**<span data-ttu-id="ea349-122">MediaType</span><span class="sxs-lookup"><span data-stu-id="ea349-122">MediaType</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR226484)
-   [**<span data-ttu-id="ea349-123">NUp</span><span class="sxs-lookup"><span data-stu-id="ea349-123">NUp</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR226485)
-   [**<span data-ttu-id="ea349-124">PrintQuality</span><span class="sxs-lookup"><span data-stu-id="ea349-124">PrintQuality</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR226487)
-   [**<span data-ttu-id="ea349-125">Staple</span><span class="sxs-lookup"><span data-stu-id="ea349-125">Staple</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR226488)

<span data-ttu-id="ea349-126">Diese Optionen werden in der [**StandardPrintTaskOptions**](https://msdn.microsoft.com/library/windows/apps/BR226475)-Klasse definiert.</span><span class="sxs-lookup"><span data-stu-id="ea349-126">These options are defined in the [**StandardPrintTaskOptions**](https://msdn.microsoft.com/library/windows/apps/BR226475) class.</span></span> <span data-ttu-id="ea349-127">Sie können in der Optionsliste, die in der Druckvorschau-Benutzeroberfläche angezeigt wird, Optionen hinzufügen oder entfernen.</span><span class="sxs-lookup"><span data-stu-id="ea349-127">You can add to or remove options from the list of options displayed in the print preview UI.</span></span> <span data-ttu-id="ea349-128">Sie können auch die Reihenfolge, in der die Optionen angezeigt werden, und die für den Benutzer angezeigten Standardeinstellungen ändern.</span><span class="sxs-lookup"><span data-stu-id="ea349-128">You can also change the order in which they appear, and set the default settings that are shown to the user.</span></span>

<span data-ttu-id="ea349-129">Die Änderungen, die Sie auf diese Weise vornehmen, betreffen allerdings nur die Druckvorschau-Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="ea349-129">However, the modifications that you make by using this method affect only the print preview UI.</span></span> <span data-ttu-id="ea349-130">Der Benutzer kann stets auf alle vom Drucker unterstützten Optionen zugreifen, indem er in der Druckvorschau-Benutzeroberfläche auf **Weitere Einstellungen** tippt.</span><span class="sxs-lookup"><span data-stu-id="ea349-130">The user can always access all of the options that the printer supports by tapping **More settings** in the print preview UI.</span></span>

<span data-ttu-id="ea349-131">**Hinweis** Obwohl Ihre App jede beliebige Druckoption zur Anzeige angeben kann, werden in der Benutzeroberfläche für die Druckvorschau nur die vom ausgewählten Drucker unterstützten Optionen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ea349-131">**Note**  Although your app can specify any print options to be displayed, only those that are supported by the selected printer are shown in the print preview UI.</span></span> <span data-ttu-id="ea349-132">In der Druckbenutzeroberfläche werden keine Optionen angezeigt, die der ausgewählte Drucker nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ea349-132">The print UI won't show options that the selected printer doesn't support.</span></span>

 

### <a name="define-the-options-to-display"></a><span data-ttu-id="ea349-133">Definieren der anzuzeigenden Optionen</span><span class="sxs-lookup"><span data-stu-id="ea349-133">Define the options to display</span></span>

<span data-ttu-id="ea349-134">Wenn der Bildschirm der App geladen wird, wird die App für den Vertrag für „Drucken“ registriert.</span><span class="sxs-lookup"><span data-stu-id="ea349-134">When the app's screen is loaded, it registers for the Print contract.</span></span> <span data-ttu-id="ea349-135">Im Rahmen dieser Registrierung wird der [**PrintTaskRequested**](https://msdn.microsoft.com/library/windows/apps/br206597)-Ereignishandler definiert.</span><span class="sxs-lookup"><span data-stu-id="ea349-135">Part of that registration includes defining the [**PrintTaskRequested**](https://msdn.microsoft.com/library/windows/apps/br206597) event handler.</span></span> <span data-ttu-id="ea349-136">Der Code zum Anpassen der in der Druckvorschau-Benutzeroberfläche angezeigten Optionen wird dem **PrintTaskRequested**-Ereignishandler hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="ea349-136">The code to customize the options displayed in the print preview UI is added to the **PrintTaskRequested** event handler.</span></span>

<span data-ttu-id="ea349-137">Ändern Sie den [**PrintTaskRequested**](https://msdn.microsoft.com/library/windows/apps/br206597)-Ereignishandler, um die [**printTask.options**](https://msdn.microsoft.com/library/windows/apps/BR226469)-Anweisungen einzubeziehen, mit denen die Druckeinstellungen konfiguriert werden, die Sie auf der Benutzeroberfläche für die Druckvorschau anzeigen möchten. Überschreiben Sie für den Bildschirm Ihrer App, in dem Sie eine benutzerdefinierte Liste von Druckoptionen anzeigen möchten, den **PrintTaskRequested**-Ereignishandler in der Basisklasse, um Code hinzuzufügen, der die Optionen angibt, die bei der Ausgabe des Bildschirms angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="ea349-137">Modify the [**PrintTaskRequested**](https://msdn.microsoft.com/library/windows/apps/br206597) event handler to include the [**printTask.options**](https://msdn.microsoft.com/library/windows/apps/BR226469) instructions that configure the print settings that you want to display in the print preview UI.For the screen in your app for which you want to show a customized list of print options, override the **PrintTaskRequested** event handler in the helper class to include code that specifies the options to display when the screen is printed.</span></span>

``` csharp
protected override void PrintTaskRequested(PrintManager sender, PrintTaskRequestedEventArgs e)
{
   PrintTask printTask = null;
   printTask = e.Request.CreatePrintTask("C# Printing SDK Sample", sourceRequestedArgs =>
   {
         IList<string> displayedOptions = printTask.Options.DisplayedOptions;

         // Choose the printer options to be shown.
         // The order in which the options are appended determines the order in which they appear in the UI
         displayedOptions.Clear();
         displayedOptions.Add(Windows.Graphics.Printing.StandardPrintTaskOptions.Copies);
         displayedOptions.Add(Windows.Graphics.Printing.StandardPrintTaskOptions.Orientation);
         displayedOptions.Add(Windows.Graphics.Printing.StandardPrintTaskOptions.MediaSize);
         displayedOptions.Add(Windows.Graphics.Printing.StandardPrintTaskOptions.Collation);
         displayedOptions.Add(Windows.Graphics.Printing.StandardPrintTaskOptions.Duplex);

         // Preset the default value of the printer option
         printTask.Options.MediaSize = PrintMediaSize.NorthAmericaLegal;

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

         sourceRequestedArgs.SetSource(printDocumentSource);
   });
}
```

<span data-ttu-id="ea349-138">**Wichtig** Durch das Aufrufen von [**displayedOptions.clear**](https://msdn.microsoft.com/library/windows/apps/BR226453)() werden alle Druckoptionen aus der Druckvorschau-Benutzeroberfläche entfernt, einschließlich des Links **Weitere Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="ea349-138">**Important**  Calling [**displayedOptions.clear**](https://msdn.microsoft.com/library/windows/apps/BR226453)() removes all of the print options from the print preview UI, including the **More settings** link.</span></span> <span data-ttu-id="ea349-139">Fügen Sie alle Optionen an, die in der Druckvorschau-Benutzeroberfläche angezeigt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="ea349-139">Be sure to append the options that you want to show on the print preview UI.</span></span>

### <a name="specify-default-options"></a><span data-ttu-id="ea349-140">Festlegen der Standardoptionen</span><span class="sxs-lookup"><span data-stu-id="ea349-140">Specify default options</span></span>

<span data-ttu-id="ea349-141">Sie können auch die Standardwerte der Optionen in der Druckvorschau-Benutzeroberfläche festlegen.</span><span class="sxs-lookup"><span data-stu-id="ea349-141">You can also set the default values of the options in the print preview UI.</span></span> <span data-ttu-id="ea349-142">Die folgende Codezeile aus dem letzten Beispiel legt den Standardwert der Option [**MediaSize**](https://msdn.microsoft.com/library/windows/apps/BR226483) fest.</span><span class="sxs-lookup"><span data-stu-id="ea349-142">The following line of code, from the last example, sets the default value of the [**MediaSize**](https://msdn.microsoft.com/library/windows/apps/BR226483) option.</span></span>

``` csharp
         // Preset the default value of the printer option
         printTask.Options.MediaSize = PrintMediaSize.NorthAmericaLegal;
```         

## <a name="add-new-print-options"></a><span data-ttu-id="ea349-143">Hinzufügen neuer Druckoptionen</span><span class="sxs-lookup"><span data-stu-id="ea349-143">Add new print options</span></span>

<span data-ttu-id="ea349-144">In diesem Abschnitt werden die Erstellung einer neuen Druckoption, die Definition einer Liste von Werten, die von dieser Option unterstützt werden, und das Hinzufügen der Option zur Druckvorschau gezeigt.</span><span class="sxs-lookup"><span data-stu-id="ea349-144">This section shows how to create a new print option, define a list of values that the option supports, and then add the option to the print preview.</span></span> <span data-ttu-id="ea349-145">Fügen Sie die Druckoption wie im vorherigen Abschnitt gezeigt im [**PrintTaskRequested**](https://msdn.microsoft.com/library/windows/apps/br206597)-Ereignishandler hinzu.</span><span class="sxs-lookup"><span data-stu-id="ea349-145">As in the previous section, add the new print option in the [**PrintTaskRequested**](https://msdn.microsoft.com/library/windows/apps/br206597) event handler.</span></span>

<span data-ttu-id="ea349-146">Rufen Sie zunächst ein [**PrintTaskOptionDetails**](https://msdn.microsoft.com/library/windows/apps/Hh701256)-Objekt ab.</span><span class="sxs-lookup"><span data-stu-id="ea349-146">First, get a [**PrintTaskOptionDetails**](https://msdn.microsoft.com/library/windows/apps/Hh701256) object.</span></span> <span data-ttu-id="ea349-147">Dies wird verwendet, um die neue Druckoption zur Benutzeroberfläche für die Druckvorschau hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="ea349-147">This is used to add the new print option to the print preview UI.</span></span> <span data-ttu-id="ea349-148">Löschen Sie dann die Liste der Optionen, die in der Druckvorschau-Benutzeroberfläche angezeigt werden, und fügen Sie die Optionen hinzu, die angezeigt werden sollen, wenn der Benutzer in der App druckt.</span><span class="sxs-lookup"><span data-stu-id="ea349-148">Then clear the list of options that are shown in the print preview UI and add the options that you want to display when the user wants to print from the app.</span></span> <span data-ttu-id="ea349-149">Anschließend erstellen Sie die neue Druckoption und initialisieren die Liste der Optionswerte.</span><span class="sxs-lookup"><span data-stu-id="ea349-149">After that, create the new print option and initialize the list of option values.</span></span> <span data-ttu-id="ea349-150">Abschließend fügen Sie die neue Option hinzu und weisen dem **OptionChanged**-Ereignis einen Handler zu.</span><span class="sxs-lookup"><span data-stu-id="ea349-150">Finally, add the new option and assign a handler for the **OptionChanged** event.</span></span>

``` csharp
protected override void PrintTaskRequested(PrintManager sender, PrintTaskRequestedEventArgs e)
{
   PrintTask printTask = null;
   printTask = e.Request.CreatePrintTask("C# Printing SDK Sample", sourceRequestedArgs =>
   {
         PrintTaskOptionDetails printDetailedOptions = PrintTaskOptionDetails.GetFromPrintTaskOptions(printTask.Options);
         IList<string> displayedOptions = printDetailedOptions.DisplayedOptions;

         // Choose the printer options to be shown.
         // The order in which the options are appended determines the order in which they appear in the UI
         displayedOptions.Clear();

         displayedOptions.Add(Windows.Graphics.Printing.StandardPrintTaskOptions.Copies);
         displayedOptions.Add(Windows.Graphics.Printing.StandardPrintTaskOptions.Orientation);
         displayedOptions.Add(Windows.Graphics.Printing.StandardPrintTaskOptions.ColorMode);

         // Create a new list option
         PrintCustomItemListOptionDetails pageFormat = printDetailedOptions.CreateItemListOption("PageContent", "Pictures");
         pageFormat.AddItem("PicturesText", "Pictures and text");
         pageFormat.AddItem("PicturesOnly", "Pictures only");
         pageFormat.AddItem("TextOnly", "Text only");

         // Add the custom option to the option list
         displayedOptions.Add("PageContent");

         printDetailedOptions.OptionChanged += printDetailedOptions_OptionChanged;

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

         sourceRequestedArgs.SetSource(printDocumentSource);
   });
}
```

<span data-ttu-id="ea349-151">Die Optionen werden in der Druckvorschau-Benutzeroberfläche in der Reihenfolge angezeigt, in der sie hinzugefügt werden, wobei die erste Option oben im Fenster erscheint.</span><span class="sxs-lookup"><span data-stu-id="ea349-151">The options appear in the print preview UI in the same order they are appended, with the first option shown at the top of the window.</span></span> <span data-ttu-id="ea349-152">In diesem Beispiel wird die benutzerdefinierte Option als Letztes hinzugefügt, sodass sie am Ende der Optionsliste erscheint.</span><span class="sxs-lookup"><span data-stu-id="ea349-152">In this example, the custom option is appended last so that it appears at the bottom of the list of options.</span></span> <span data-ttu-id="ea349-153">Sie könnten sie jedoch an einer beliebigen Stelle der Liste platzieren. Benutzerdefinierte Druckoptionen müssen nicht zuletzt hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="ea349-153">However, you could put it anywhere in the list; custom print options don't need to be added last.</span></span>

<span data-ttu-id="ea349-154">Wenn der Benutzer die ausgewählte Option in Ihrer benutzerdefinierten Druckoption ändert, aktualisieren Sie das Druckvorschaubild.</span><span class="sxs-lookup"><span data-stu-id="ea349-154">When the user changes the selected option in your custom option, update the print preview image.</span></span> <span data-ttu-id="ea349-155">Rufen Sie die [**InvalidatePreview**](https://msdn.microsoft.com/library/windows/apps/Hh702146)-Methode auf, um das Bild in der Druckvorschau-Benutzeroberfläche neu zu zeichnen, wie unten gezeigt.</span><span class="sxs-lookup"><span data-stu-id="ea349-155">Call the [**InvalidatePreview**](https://msdn.microsoft.com/library/windows/apps/Hh702146) method to redraw the image in the print preview UI, as shown below.</span></span>

``` csharp
async void printDetailedOptions_OptionChanged(PrintTaskOptionDetails sender, PrintTaskOptionChangedEventArgs args)
{
   // Listen for PageContent changes
   string optionId = args.OptionId as string;
   if (string.IsNullOrEmpty(optionId))
   {
         return;
   }

   if (optionId == "PageContent")
   {
         await scenarioPage.Dispatcher.RunAsync(Windows.UI.Core.CoreDispatcherPriority.Normal, () =>
         {
            printDocument.InvalidatePreview();
         });
   }
}
```

## <a name="related-topics"></a><span data-ttu-id="ea349-156">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="ea349-156">Related topics</span></span>

* [<span data-ttu-id="ea349-157">Gestaltungsrichtlinien für Druckvorgänge</span><span class="sxs-lookup"><span data-stu-id="ea349-157">Design guidelines for printing</span></span>](https://msdn.microsoft.com/library/windows/apps/Hh868178)
* [<span data-ttu-id="ea349-158">//Build 2015-Video: Entwickeln von druckfähigen Apps in Windows 10</span><span class="sxs-lookup"><span data-stu-id="ea349-158">//Build 2015 video: Developing apps that print in Windows 10</span></span>](https://channel9.msdn.com/Events/Build/2015/2-94)
* [<span data-ttu-id="ea349-159">UWP-Druckbeispiel</span><span class="sxs-lookup"><span data-stu-id="ea349-159">UWP print sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619984)
