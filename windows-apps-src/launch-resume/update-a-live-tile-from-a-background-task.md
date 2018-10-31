---
author: TylerMSFT
title: Aktualisieren einer Live-Kachel über eine Hintergrundaufgabe
description: Verwenden Sie eine Hintergrundaufgabe, um die Live-Kachel Ihrer App mit neuen Inhalten zu aktualisieren.
Search.SourceType: Video
ms.assetid: 9237A5BD-F9DE-4B8C-B689-601201BA8B9A
ms.author: twhitney
ms.date: 01/11/2018
ms.topic: article
keywords: Windows 10, Uwp, Hintergrundaufgabe, für die
ms.localizationpriority: medium
ms.openlocfilehash: 3c379097efaef65357bc1c6b036695ef84671ea6
ms.sourcegitcommit: ca96031debe1e76d4501621a7680079244ef1c60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "5825983"
---
# <a name="update-a-live-tile-from-a-background-task"></a><span data-ttu-id="92dc5-104">Aktualisieren einer Live-Kachel über eine Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="92dc5-104">Update a live tile from a background task</span></span>

**<span data-ttu-id="92dc5-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="92dc5-105">Important APIs</span></span>**

-   [**<span data-ttu-id="92dc5-106">IBackgroundTask</span><span class="sxs-lookup"><span data-stu-id="92dc5-106">IBackgroundTask</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224794)
-   [**<span data-ttu-id="92dc5-107">BackgroundTaskBuilder</span><span class="sxs-lookup"><span data-stu-id="92dc5-107">BackgroundTaskBuilder</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224768)

<span data-ttu-id="92dc5-108">Verwenden Sie eine Hintergrundaufgabe, um die Live-Kachel Ihrer App mit neuen Inhalten zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="92dc5-108">Use a background task to update your app's live tile with fresh content.</span></span>

<span data-ttu-id="92dc5-109">Das folgende Video zeigt, wie Sie Ihren Apps Live-Kacheln hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="92dc5-109">Here's a video that shows how to add live tiles to your apps.</span></span>

<iframe src="https://channel9.msdn.com/Blogs/One-Dev-Minute/Updating-a-live-tile-from-a-background-task/player" width="720" height="405" allowFullScreen="true" frameBorder="0"></iframe>

## <a name="create-the-background-task-project"></a><span data-ttu-id="92dc5-110">Erstellen des Hintergrundaufgabenprojekts</span><span class="sxs-lookup"><span data-stu-id="92dc5-110">Create the background task project</span></span>  

<span data-ttu-id="92dc5-111">Fügen Sie der Projektmappe zum Aktivieren einer Live-Kachel für Ihre App ein neues Projekt mit Komponenten für Windows-Runtime hinzu.</span><span class="sxs-lookup"><span data-stu-id="92dc5-111">To enable a live tile for your app, add a new Windows Runtime Component project to your solution.</span></span> <span data-ttu-id="92dc5-112">Dies ist eine separate Assembly, die vom BS im Hintergrund geladen und ausgeführt wird, wenn Benutzer die App installieren.</span><span class="sxs-lookup"><span data-stu-id="92dc5-112">This is a separate assembly that the OS loads and runs in the background when a user installs your app.</span></span>

1.  <span data-ttu-id="92dc5-113">Klicken Sie im Projektmappen-Explorer auf die Projektmappe, klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Projekt**.</span><span class="sxs-lookup"><span data-stu-id="92dc5-113">In Solution Explorer, right-click the solution, click **Add**, and then click **New Project**.</span></span>
2.  <span data-ttu-id="92dc5-114">Wählen Sie im Dialogfeld **Neues Projekt hinzufügen** im Abschnitt **Installiert &gt; Andere Sprachen &gt; Visual C# &gt; Windows Universal** die Vorlage **Komponente für Windows-Runtime** aus.</span><span class="sxs-lookup"><span data-stu-id="92dc5-114">In the **Add New Project** dialog, select the **Windows Runtime Component** template in the **Installed &gt; Other Languages &gt; Visual C# &gt; Windows Universal** section.</span></span>
3.  <span data-ttu-id="92dc5-115">Geben Sie dem Projekt den Namen „BackgroundTasks“, und klicken oder tippen Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="92dc5-115">Name the project BackgroundTasks and click or tap **OK**.</span></span> <span data-ttu-id="92dc5-116">In Microsoft Visual Studio wird das neue Projekt der Projektmappe hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="92dc5-116">Microsoft Visual Studio adds the new project to the solution.</span></span>
4.  <span data-ttu-id="92dc5-117">Fügen Sie im Hauptprojekt einen Verweis auf das Projekt „BackgroundTasks“ hinzu.</span><span class="sxs-lookup"><span data-stu-id="92dc5-117">In the main project, add a reference to the BackgroundTasks project.</span></span>

## <a name="implement-the-background-task"></a><span data-ttu-id="92dc5-118">Implementieren der Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="92dc5-118">Implement the background task</span></span>


<span data-ttu-id="92dc5-119">Implementieren Sie die [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794)-Schnittstelle, um eine Klasse zu erstellen, mit der die Live-Kachel Ihrer App aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="92dc5-119">Implement the [**IBackgroundTask**](https://msdn.microsoft.com/library/windows/apps/br224794) interface to create a class that updates your app's live tile.</span></span> <span data-ttu-id="92dc5-120">Ihre Hintergrundarbeit bezieht sich auf die Run-Methode.</span><span class="sxs-lookup"><span data-stu-id="92dc5-120">Your background work goes in the Run method.</span></span> <span data-ttu-id="92dc5-121">In diesem Fall erhält die Aufgabe einen Veröffentlichungsfeed für die MSDN-Blogs.</span><span class="sxs-lookup"><span data-stu-id="92dc5-121">In this case, the task gets a syndication feed for the MSDN blogs.</span></span> <span data-ttu-id="92dc5-122">Richten Sie eine Verzögerung ein, um das zu frühe Schließen der Aufgabe zu verhindern, während noch asynchroner Code ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="92dc5-122">To prevent the task from closing prematurely while asynchronous code is still running, get a deferral.</span></span>

1.  <span data-ttu-id="92dc5-123">Benennen Sie im Projektmappen-Explorer die automatisch generierte Datei „Class1.cs“ in „BlogFeedBackgroundTask.cs“ um.</span><span class="sxs-lookup"><span data-stu-id="92dc5-123">In Solution Explorer, rename the automatically generated file, Class1.cs, to BlogFeedBackgroundTask.cs.</span></span>
2.  <span data-ttu-id="92dc5-124">Ersetzen Sie in „BlogFeedBackgroundTask.cs“ den automatisch generierten Code durch den Stub-Code für die **BlogFeedBackgroundTask**-Klasse.</span><span class="sxs-lookup"><span data-stu-id="92dc5-124">In BlogFeedBackgroundTask.cs, replace the automatically generated code with the stub code for the **BlogFeedBackgroundTask** class.</span></span>
3.  <span data-ttu-id="92dc5-125">Fügen Sie in der Implementierung der Run-Methode Code für die Methoden **GetMSDNBlogFeed** und **UpdateTile** hinzu.</span><span class="sxs-lookup"><span data-stu-id="92dc5-125">In the Run method implementation, add code for the **GetMSDNBlogFeed** and **UpdateTile** methods.</span></span>

```cs
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

// Added during quickstart
using Windows.ApplicationModel.Background;
using Windows.Data.Xml.Dom;
using Windows.UI.Notifications;
using Windows.Web.Syndication;

namespace BackgroundTasks
{
    public sealed class BlogFeedBackgroundTask  : IBackgroundTask
    {
        public async void Run( IBackgroundTaskInstance taskInstance )
        {
            // Get a deferral, to prevent the task from closing prematurely
            // while asynchronous code is still running.
            BackgroundTaskDeferral deferral = taskInstance.GetDeferral();

            // Download the feed.
            var feed = await GetMSDNBlogFeed();

            // Update the live tile with the feed items.
            UpdateTile( feed );

            // Inform the system that the task is finished.
            deferral.Complete();
        }

        private static async Task<SyndicationFeed> GetMSDNBlogFeed()
        {
            SyndicationFeed feed = null;

            try
            {
                // Create a syndication client that downloads the feed.  
                SyndicationClient client = new SyndicationClient();
                client.BypassCacheOnRetrieve = true;
                client.SetRequestHeader( customHeaderName, customHeaderValue );

                // Download the feed.
                feed = await client.RetrieveFeedAsync( new Uri( feedUrl ) );
            }
            catch( Exception ex )
            {
                Debug.WriteLine( ex.ToString() );
            }

            return feed;
        }

        private static void UpdateTile( SyndicationFeed feed )
        {
            // Create a tile update manager for the specified syndication feed.
            var updater = TileUpdateManager.CreateTileUpdaterForApplication();
            updater.EnableNotificationQueue( true );
            updater.Clear();

            // Keep track of the number feed items that get tile notifications.
            int itemCount = 0;

            // Create a tile notification for each feed item.
            foreach( var item in feed.Items )
            {
                XmlDocument tileXml = TileUpdateManager.GetTemplateContent( TileTemplateType.TileWideText03 );

                var title = item.Title;
                string titleText = title.Text == null ? String.Empty : title.Text;
                tileXml.GetElementsByTagName( textElementName )[0].InnerText = titleText;

                // Create a new tile notification.
                updater.Update( new TileNotification( tileXml ) );

                // Don't create more than 5 notifications.
                if( itemCount++ > 5 ) break;
            }
        }

        // Although most HTTP servers do not require User-Agent header, others will reject the request or return
        // a different response if this header is missing. Use SetRequestHeader() to add custom headers.
        static string customHeaderName = "User-Agent";
        static string customHeaderValue = "Mozilla/5.0 (compatible; MSIE 10.0; Windows NT 6.2; WOW64; Trident/6.0)";

        static string textElementName = "text";
        static string feedUrl = @"http://blogs.msdn.com/b/MainFeed.aspx?Type=BlogsOnly";
    }
}
```

## <a name="set-up-the-package-manifest"></a><span data-ttu-id="92dc5-126">Einrichten des Paketmanifests</span><span class="sxs-lookup"><span data-stu-id="92dc5-126">Set up the package manifest</span></span>


<span data-ttu-id="92dc5-127">Öffnen Sie das Paketmanifest, um es einzurichten, und fügen Sie eine Deklaration einer neuen Hintergrundaufgabe hinzu.</span><span class="sxs-lookup"><span data-stu-id="92dc5-127">To set up the package manifest, open it and add a new background task declaration.</span></span> <span data-ttu-id="92dc5-128">Legen Sie den Einstiegspunkt für die Aufgabe auf den Klassennamen fest, und fügen Sie auch den Namespace ein.</span><span class="sxs-lookup"><span data-stu-id="92dc5-128">Set the entry point for the task to the class name, including its namespace.</span></span>

1.  <span data-ttu-id="92dc5-129">Öffnen Sie im Projektmappen-Explorer die Datei „Package.appxmanifest“.</span><span class="sxs-lookup"><span data-stu-id="92dc5-129">In Solution Explorer, open Package.appxmanifest.</span></span>
2.  <span data-ttu-id="92dc5-130">Klicken oder tippen Sie auf die Registerkarte **Deklarationen**.</span><span class="sxs-lookup"><span data-stu-id="92dc5-130">Click or tap the **Declarations** tab.</span></span>
3.  <span data-ttu-id="92dc5-131">Wählen Sie unter **Verfügbare Deklarationen**die Option **BackgroundTasks** aus, und klicken Sie auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="92dc5-131">Under **Available Declarations**, select **BackgroundTasks** and click **Add**.</span></span> <span data-ttu-id="92dc5-132">In Visual Studio wird **BackgroundTasks** unter **Unterstützte Deklarationen** hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="92dc5-132">Visual Studio adds **BackgroundTasks** under **Supported Declarations**.</span></span>
4.  <span data-ttu-id="92dc5-133">Stellen Sie unter **Unterstützte Aufgabentypen** sicher, dass **Timer** aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="92dc5-133">Under **Supported task types**, ensure that **Timer** is checked.</span></span>
5.  <span data-ttu-id="92dc5-134">Legen Sie unter **App-Einstellungen** den Einstiegspunkt auf **BackgroundTasks.BlogFeedBackgroundTask** fest.</span><span class="sxs-lookup"><span data-stu-id="92dc5-134">Under **App settings**, set the entry point to **BackgroundTasks.BlogFeedBackgroundTask**.</span></span>
6.  <span data-ttu-id="92dc5-135">Klicken oder tippen Sie auf die Registerkarte **Anwendungsbenutzeroberfläche**.</span><span class="sxs-lookup"><span data-stu-id="92dc5-135">Click or tap the **Application UI** tab.</span></span>
7.  <span data-ttu-id="92dc5-136">Legen Sie die Option **Benachrichtigungen bei gesperrtem Bildschirm** auf **Text für Infoanzeiger und Kachel**fest.</span><span class="sxs-lookup"><span data-stu-id="92dc5-136">Set **Lock screen notifications** to **Badge and Tile Text**.</span></span>
8.  <span data-ttu-id="92dc5-137">Legen Sie im Feld **Infoanzeigerlogo** einen Pfad zu einem Symbol mit einer Größe von 24x24Pixel fest.</span><span class="sxs-lookup"><span data-stu-id="92dc5-137">Set a path to a 24x24 pixel icon in the **Badge logo** field.</span></span>
    <span data-ttu-id="92dc5-138">**Wichtige**dieses Symbol muss nur einfarbige und transparente Pixel verwenden.</span><span class="sxs-lookup"><span data-stu-id="92dc5-138">**Important**This icon must use monochrome and transparent pixels only.</span></span>
9.  <span data-ttu-id="92dc5-139">Legen Sie im Feld **Kleines Logo** einen Pfad zu einem Symbol der Größe 30x30 Pixel fest.</span><span class="sxs-lookup"><span data-stu-id="92dc5-139">In the **Small logo** field, set a path to a 30x30 pixel icon.</span></span>
10. <span data-ttu-id="92dc5-140">Legen Sie im Feld **Breites Logo** einen Pfad zu einem Symbol mit einer Größe von 310x150Pixel fest.</span><span class="sxs-lookup"><span data-stu-id="92dc5-140">In the **Wide logo** field, set a path to a 310x150 pixel icon.</span></span>

## <a name="register-the-background-task"></a><span data-ttu-id="92dc5-141">Registrieren der Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="92dc5-141">Register the background task</span></span>


<span data-ttu-id="92dc5-142">Erstellen Sie zum Registrieren Ihrer Aufgabe ein [**BackgroundTaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="92dc5-142">Create a [**BackgroundTaskBuilder**](https://msdn.microsoft.com/library/windows/apps/br224768) to register your task.</span></span>

> <span data-ttu-id="92dc5-143">**Hinweis:** Windows8.1 ab, werden Parameter für die Registrierung von Hintergrundaufgaben zum Zeitpunkt der Registrierung überprüft.</span><span class="sxs-lookup"><span data-stu-id="92dc5-143">**Note**Starting in Windows8.1, background task registration parameters are validated at the time of registration.</span></span> <span data-ttu-id="92dc5-144">Bei ungültigen Registrierungsparametern wird ein Fehler zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="92dc5-144">An error is returned if any of the registration parameters are invalid.</span></span> <span data-ttu-id="92dc5-145">Ihre App muss Szenarien mit nicht erfolgreicher Registrierung von Hintergrundaufgaben problemlos verarbeiten können. Verwenden Sie beispielsweise eine Bedingungsanweisung, um die App auf Registrierungsfehler zu prüfen, und wiederholen Sie die nicht erfolgreiche Registrierung mit anderen Parameterwerten.</span><span class="sxs-lookup"><span data-stu-id="92dc5-145">Your app must be able to handle scenarios where background task registration fails - for example, use a conditional statement to check for registration errors and then retry failed registration using different parameter values.</span></span>
 

<span data-ttu-id="92dc5-146">Fügen Sie auf der Hauptseite der App die **RegisterBackgroundTask**-Methode hinzu, und rufen Sie sie im **OnNavigatedTo**-Ereignishandler auf.</span><span class="sxs-lookup"><span data-stu-id="92dc5-146">In your app's main page, add the **RegisterBackgroundTask** method and call it in the **OnNavigatedTo** event handler.</span></span>

```cs
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Threading.Tasks;
using Windows.ApplicationModel.Background;
using Windows.Data.Xml.Dom;
using Windows.Foundation;
using Windows.Foundation.Collections;
using Windows.UI.Xaml;
using Windows.UI.Xaml.Controls;
using Windows.UI.Xaml.Controls.Primitives;
using Windows.UI.Xaml.Data;
using Windows.UI.Xaml.Input;
using Windows.UI.Xaml.Media;
using Windows.UI.Xaml.Navigation;
using Windows.Web.Syndication;

// The Blank Page item template is documented at http://go.microsoft.com/fwlink/p/?LinkID=234238

namespace ContosoApp
{
    /// <summary>
    /// An empty page that can be used on its own or navigated to within a Frame.
    /// </summary>
    public sealed partial class MainPage : Page
    {
        public MainPage()
        {
            this.InitializeComponent();
        }

        /// <summary>
        /// Invoked when this page is about to be displayed in a Frame.
        /// </summary>
        /// <param name="e">Event data that describes how this page was reached.  The Parameter
        /// property is typically used to configure the page.</param>
        protected override void OnNavigatedTo( NavigationEventArgs e )
        {
            this.RegisterBackgroundTask();
        }


        private async void RegisterBackgroundTask()
        {
            var backgroundAccessStatus = await BackgroundExecutionManager.RequestAccessAsync();
            if( backgroundAccessStatus == BackgroundAccessStatus.AllowedMayUseActiveRealTimeConnectivity ||
                backgroundAccessStatus == BackgroundAccessStatus.AllowedWithAlwaysOnRealTimeConnectivity )
            {
                foreach( var task in BackgroundTaskRegistration.AllTasks )
                {
                    if( task.Value.Name == taskName )
                    {
                        task.Value.Unregister( true );
                    }
                }

                BackgroundTaskBuilder taskBuilder = new BackgroundTaskBuilder();
                taskBuilder.Name = taskName;
                taskBuilder.TaskEntryPoint = taskEntryPoint;
                taskBuilder.SetTrigger( new TimeTrigger( 15, false ) );
                var registration = taskBuilder.Register();
            }
        }

        private const string taskName = "BlogFeedBackgroundTask";
        private const string taskEntryPoint = "BackgroundTasks.BlogFeedBackgroundTask";
    }
}
```

## <a name="debug-the-background-task"></a><span data-ttu-id="92dc5-147">Debuggen der Hintergrundaufgabe</span><span class="sxs-lookup"><span data-stu-id="92dc5-147">Debug the background task</span></span>


<span data-ttu-id="92dc5-148">Legen Sie zum Debuggen der Hintergrundaufgabe in der Run-Methode der Aufgabe einen Haltepunkt fest.</span><span class="sxs-lookup"><span data-stu-id="92dc5-148">To debug the background task, set a breakpoint in the task’s Run method.</span></span> <span data-ttu-id="92dc5-149">Wählen Sie die Hintergrundaufgabe auf der Symbolleiste **Debugspeicherort** aus.</span><span class="sxs-lookup"><span data-stu-id="92dc5-149">In the **Debug Location** toolbar, select your background task.</span></span> <span data-ttu-id="92dc5-150">Das System ruft dann sofort die Run-Methode auf.</span><span class="sxs-lookup"><span data-stu-id="92dc5-150">This causes the system to call the Run method immediately.</span></span>

1.  <span data-ttu-id="92dc5-151">Legen Sie in der Run-Methode der Aufgabe einen Haltepunkt fest.</span><span class="sxs-lookup"><span data-stu-id="92dc5-151">Set a breakpoint in the task’s Run method.</span></span>
2.  <span data-ttu-id="92dc5-152">Drücken Sie F5 oder tippen Sie auf **Debuggen &gt; Debugging starten**, um die App bereitzustellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="92dc5-152">Press F5 or tap **Debug &gt; Start Debugging** to deploy and run the app.</span></span>
3.  <span data-ttu-id="92dc5-153">Wechseln Sie nach dem Start der App zurück zu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="92dc5-153">After the app launches, switch back to Visual Studio.</span></span>
4.  <span data-ttu-id="92dc5-154">Stellen Sie sicher, dass die Symbolleiste **Debugspeicherort** sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="92dc5-154">Ensure that the **Debug Location** toolbar is visible.</span></span> <span data-ttu-id="92dc5-155">Sie befindet sich im Menü **Ansicht &gt; Symbolleisten**.</span><span class="sxs-lookup"><span data-stu-id="92dc5-155">It's on the **View &gt; Toolbars** menu.</span></span>
5.  <span data-ttu-id="92dc5-156">Klicken Sie in der Symbolleiste **Debugspeicherort** auf die Dropdownliste **Anhalten**, und wählen Sie **BlogFeedBackgroundTask**aus.</span><span class="sxs-lookup"><span data-stu-id="92dc5-156">On the **Debug Location** toolbar, click the **Suspend** dropdown and select **BlogFeedBackgroundTask**.</span></span>
6.  <span data-ttu-id="92dc5-157">Visual Studio hält die Ausführung am Haltepunkt an.</span><span class="sxs-lookup"><span data-stu-id="92dc5-157">Visual Studio suspends execution at the breakpoint.</span></span>
7.  <span data-ttu-id="92dc5-158">Drücken Sie F5 oder tippen Sie auf **Debuggen &gt; Fortsetzen**, um die Ausführung der App fortzusetzen.</span><span class="sxs-lookup"><span data-stu-id="92dc5-158">Press F5 or tap **Debug &gt; Continue** to continue running the app.</span></span>
8.  <span data-ttu-id="92dc5-159">Drücken Sie UMSCHALT+F5 oder tippen Sie auf **Debuggen &gt; Debugging** beenden, um das Debuggen zu beenden.</span><span class="sxs-lookup"><span data-stu-id="92dc5-159">Press Shift+F5 or tap **Debug &gt; Stop Debugging** to stop debugging.</span></span>
9.  <span data-ttu-id="92dc5-160">Kehren Sie zur Kachel der App auf dem Startbildschirm zurück.</span><span class="sxs-lookup"><span data-stu-id="92dc5-160">Return to the app's tile on the Start screen.</span></span> <span data-ttu-id="92dc5-161">Nach einigen Sekunden werden in der Kachel der App Kachelbenachrichtigungen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="92dc5-161">After a few seconds, tile notifications appear on your app's tile.</span></span>

## <a name="related-topics"></a><span data-ttu-id="92dc5-162">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="92dc5-162">Related topics</span></span>


* [**<span data-ttu-id="92dc5-163">BackgroundTaskBuilder</span><span class="sxs-lookup"><span data-stu-id="92dc5-163">BackgroundTaskBuilder</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224768)
* [**<span data-ttu-id="92dc5-164">TileUpdateManager</span><span class="sxs-lookup"><span data-stu-id="92dc5-164">TileUpdateManager</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208622)
* [**<span data-ttu-id="92dc5-165">TileNotification</span><span class="sxs-lookup"><span data-stu-id="92dc5-165">TileNotification</span></span>**](https://msdn.microsoft.com/library/windows/apps/br208616)
* [<span data-ttu-id="92dc5-166">Unterstützen Ihrer App mit Hintergrundaufgaben</span><span class="sxs-lookup"><span data-stu-id="92dc5-166">Support your app with background tasks</span></span>](support-your-app-with-background-tasks.md)
* [<span data-ttu-id="92dc5-167">Richtlinien und Prüfliste für Kacheln und Signale</span><span class="sxs-lookup"><span data-stu-id="92dc5-167">Guidelines and checklist for tiles and badges</span></span>](https://msdn.microsoft.com/library/windows/apps/hh465403)

 

 
