---
author: TylerMSFT
title: Automatischer Start mit automatischer Wiedergabe
description: "Sie können die automatische Wiedergabe verwenden, um Ihre App als Option bereitzustellen, wenn ein Benutzer ein Gerät an seinen PC anschließt. Hierzu zählen Nicht-Volumegeräte wie Kameras oder Media Player und Volumegeräte wie USB-Sticks, SD-Karten oder DVDs."
ms.assetid: AD4439EA-00B0-4543-887F-2C1D47408EA7
ms.author: twhitney
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 92d8ed53f39f750755bc4fc2d23d4ca365718696
ms.sourcegitcommit: ba0d20f6fad75ce98c25ceead78aab6661250571
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2017
---
# <a name="span-iddevlaunchresumeauto-launchingwithautoplayspanauto-launching-with-autoplay"></a><span data-ttu-id="a3445-105"><span id="dev_launch_resume.auto-launching_with_autoplay"></span>Automatisches Starten mit automatischer Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="a3445-105"><span id="dev_launch_resume.auto-launching_with_autoplay"></span>Auto-launching with AutoPlay</span></span>


<span data-ttu-id="a3445-106">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="a3445-106">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="a3445-107">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132). \]</span><span class="sxs-lookup"><span data-stu-id="a3445-107">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>


<span data-ttu-id="a3445-108">Sie können die **automatische Wiedergabe** verwenden, um Ihre App als Option bereitzustellen, wenn ein Benutzer ein Gerät an seinen PC anschließt.</span><span class="sxs-lookup"><span data-stu-id="a3445-108">You can use **AutoPlay** to provide your app as an option when a user connects a device to their PC.</span></span> <span data-ttu-id="a3445-109">Hierzu zählen Nicht-Volumegeräte wie Kameras oder Media Player und Volumegeräte wie USB-Sticks, SD-Karten oder DVDs.</span><span class="sxs-lookup"><span data-stu-id="a3445-109">This includes non-volume devices such as a camera or media player, or volume devices such as a USB thumb drive, SD card, or DVD.</span></span> <span data-ttu-id="a3445-110">Die **automatische Wiedergabe** bietet Ihnen auch die Möglichkeit, Ihre App als Option anzubieten, wenn Benutzer mithilfe von Näherung (Kopplung) Dateien zwischen zwei PCs freigeben.</span><span class="sxs-lookup"><span data-stu-id="a3445-110">You can also use **AutoPlay** to offer your app as an option when users share files between two PCs by using proximity (tapping).</span></span>

> <span data-ttu-id="a3445-111">**Hinweis**  Wenn Sie ein Gerätehersteller sind und Ihrem Gerät eine bestimmte [WindowsStore-Geräte-App](http://go.microsoft.com/fwlink/p/?LinkID=301381) als Handler für die **automatische Wiedergabe** zuordnen möchten, können Sie diese App in den Gerätemetadaten angeben.</span><span class="sxs-lookup"><span data-stu-id="a3445-111">**Note**  If you are a device manufacturer and you want to associate your [Windows Store device app](http://go.microsoft.com/fwlink/p/?LinkID=301381) as an **AutoPlay** handler for your device, you can identify that app in the device metadata.</span></span> <span data-ttu-id="a3445-112">Weitere Informationen finden Sie im Thema [Automatische Wiedergabe für WindowsStore-Geräte-Apps](http://go.microsoft.com/fwlink/p/?LinkId=306684).</span><span class="sxs-lookup"><span data-stu-id="a3445-112">For more info, see [AutoPlay for Windows Store device apps](http://go.microsoft.com/fwlink/p/?LinkId=306684).</span></span>

## <a name="register-for-autoplay-content"></a><span data-ttu-id="a3445-113">Registrieren für Inhalt für die automatische Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="a3445-113">Register for AutoPlay content</span></span>

<span data-ttu-id="a3445-114">Sie können Apps als Optionen für Inhaltsereignisse für die **automatische Wiedergabe** registrieren.</span><span class="sxs-lookup"><span data-stu-id="a3445-114">You can register apps as options for **AutoPlay** content events.</span></span> <span data-ttu-id="a3445-115">Inhaltsereignisse der **automatischen Wiedergabe** werden ausgelöst, wenn ein Volumegerät wie etwa die Speicherkarte einer Kamera, eine DVD oder ein USB-Stick in den PC eingelegt bzw. daran angeschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="a3445-115">**AutoPlay** content events are raised when a volume device such as a camera memory card, thumb drive, or DVD is inserted into the PC.</span></span> <span data-ttu-id="a3445-116">Dieses Beispiel zeigt, wie Sie eine App als Option für die **automatische Wiedergabe** identifizieren, wenn ein Volumegerät einer Kamera angeschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="a3445-116">Here we show how to identify your app as an **AutoPlay** option when a volume device from a camera is inserted.</span></span>

<span data-ttu-id="a3445-117">In diesem Lernprogramm haben Sie eine App erstellt, die Bilddateien anzeigt oder in „Bilder“ kopiert.</span><span class="sxs-lookup"><span data-stu-id="a3445-117">In this tutorial, you created an app that displays image files or copies them to Pictures.</span></span> <span data-ttu-id="a3445-118">Sie haben die App für das Inhaltsereignis **ShowPicturesOnArrival** der automatischen Wiedergabe registriert.</span><span class="sxs-lookup"><span data-stu-id="a3445-118">You registered the app for the AutoPlay **ShowPicturesOnArrival** content event.</span></span>

<span data-ttu-id="a3445-119">Die automatische Wiedergabe löst außerdem Inhaltsereignisse für Inhalte aus, die mittels Näherung (Koppeln) zwischen PCs freigegeben werden.</span><span class="sxs-lookup"><span data-stu-id="a3445-119">AutoPlay also raises content events for content shared between PCs using proximity (tapping).</span></span> <span data-ttu-id="a3445-120">Sie können die Schritte und den Code aus diesem Abschnitt auch für Dateien verwenden, die mittels Näherung zwischen PCs freigegeben werden.</span><span class="sxs-lookup"><span data-stu-id="a3445-120">You can use the steps and code in this section to handle files that are shared between PCs that use proximity.</span></span> <span data-ttu-id="a3445-121">Die folgende Tabelle enthält die Inhaltsereignisse für die automatische Wiedergabe, die Sie verwenden können, um Inhalte mithilfe der Näherungsfunktion zu teilen.</span><span class="sxs-lookup"><span data-stu-id="a3445-121">The following table lists the AutoPlay content events that are available for sharing content by using proximity.</span></span>

| <span data-ttu-id="a3445-122">Aktion</span><span class="sxs-lookup"><span data-stu-id="a3445-122">Action</span></span>         | <span data-ttu-id="a3445-123">Inhaltsereignis für die automatische Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="a3445-123">AutoPlay content event</span></span>  |
|----------------|-------------------------|
| <span data-ttu-id="a3445-124">Teilen von Musik</span><span class="sxs-lookup"><span data-stu-id="a3445-124">Sharing music</span></span>  | <span data-ttu-id="a3445-125">PlayMusicFilesOnArrival</span><span class="sxs-lookup"><span data-stu-id="a3445-125">PlayMusicFilesOnArrival</span></span> |
| <span data-ttu-id="a3445-126">Teilen von Videos</span><span class="sxs-lookup"><span data-stu-id="a3445-126">Sharing videos</span></span> | <span data-ttu-id="a3445-127">PlayVideoFilesOnArrival</span><span class="sxs-lookup"><span data-stu-id="a3445-127">PlayVideoFilesOnArrival</span></span> |

 
<span data-ttu-id="a3445-128">Wenn Dateien mithilfe der Näherungsfunktion freigegeben werden, enthält die **Files**-Eigenschaft des **FileActivatedEventArgs**-Objekts einen Verweis auf einen Stammordner mit allen freigegebenen Dateien.</span><span class="sxs-lookup"><span data-stu-id="a3445-128">When files are shared by using proximity, the **Files** property of the **FileActivatedEventArgs** object contains a reference to a root folder that contains all of the shared files.</span></span>

### <a name="step-1-create-a-new-project-and-add-autoplay-declarations"></a><span data-ttu-id="a3445-129">Schritt 1: Erstellen eines neuen Projekts und Hinzufügen von Deklarationen für die automatische Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="a3445-129">Step 1: Create a new project and add AutoPlay declarations</span></span>

1.  <span data-ttu-id="a3445-130">Öffnen Sie Microsoft Visual Studio, und wählen Sie **Neues Projekt** im Menü **Datei** aus.</span><span class="sxs-lookup"><span data-stu-id="a3445-130">Open Microsoft Visual Studio and select **New Project** from the **File** menu.</span></span> <span data-ttu-id="a3445-131">Wählen Sie im Abschnitt **VisualC#** unter **Windows** die Option **Leere App (Universelle Windows-App)** aus.</span><span class="sxs-lookup"><span data-stu-id="a3445-131">In the **Visual C#** section, under **Windows**, select **Blank App (Universal Windows)**.</span></span> <span data-ttu-id="a3445-132">Nennen Sie die App **AutoPlayDisplayOrCopyImages**, und klicken Sie auf **OK.**</span><span class="sxs-lookup"><span data-stu-id="a3445-132">Name the app **AutoPlayDisplayOrCopyImages** and click **OK.**</span></span>
2.  <span data-ttu-id="a3445-133">Öffnen Sie die Datei „Package.appxmanifest“, und wählen Sie die Registerkarte **Funktionen** aus.</span><span class="sxs-lookup"><span data-stu-id="a3445-133">Open the Package.appxmanifest file and select the **Capabilities** tab.</span></span> <span data-ttu-id="a3445-134">Wählen Sie die Funktionen **Wechselmedien** und **Bildbibliothek** aus.</span><span class="sxs-lookup"><span data-stu-id="a3445-134">Select the **Removable Storage** and **Pictures Library** capabilities.</span></span> <span data-ttu-id="a3445-135">Dadurch erhält die App Zugriff auf Wechselmedien für Kameraspeicher und lokale Bilder.</span><span class="sxs-lookup"><span data-stu-id="a3445-135">This gives the app access to removable storage devices for camera memory, and access to local pictures.</span></span>
3.  <span data-ttu-id="a3445-136">Klicken Sie in der Manifestdatei auf die Registerkarte **Deklarationen**.</span><span class="sxs-lookup"><span data-stu-id="a3445-136">In the manifest file, select the **Declarations** tab.</span></span> <span data-ttu-id="a3445-137">Wählen Sie in der Dropdownliste **Verfügbare Deklarationen** die Option **Inhalt automatisch wiedergeben** aus, und klicken Sie anschließend auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="a3445-137">In the **Available Declarations** drop-down list, select **AutoPlay Content** and click **Add**.</span></span> <span data-ttu-id="a3445-138">Wählen Sie das neue Element vom Typ **Inhalt automatisch wiedergeben** aus, das der Liste **Unterstützte Deklarationen** hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="a3445-138">Select the new **AutoPlay Content** item that was added to the **Supported Declarations** list.</span></span>
4.  <span data-ttu-id="a3445-139">Eine Deklaration vom Typ **Inhalt automatisch wiedergeben** identifiziert Ihre App als Option, wenn die automatische Wiedergabe ein Inhaltsereignis auslöst.</span><span class="sxs-lookup"><span data-stu-id="a3445-139">An **AutoPlay Content** declaration identifies your app as an option when AutoPlay raises a content event.</span></span> <span data-ttu-id="a3445-140">Das Ereignis basiert auf dem Inhalt eines Volumegeräts (beispielsweise eine DVD oder ein Speicherstick).</span><span class="sxs-lookup"><span data-stu-id="a3445-140">The event is based on the content of a volume device such as a DVD or a thumb drive.</span></span> <span data-ttu-id="a3445-141">Für die automatische Wiedergabe wird der Inhalt des Volumegeräts ermittelt und festgelegt, welches Inhaltsereignis ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="a3445-141">AutoPlay examines the content of the volume device and determines which content event to raise.</span></span> <span data-ttu-id="a3445-142">Die automatische Wiedergabe löst das **ShowPicturesOnArrival**-Ereignis aus, wenn das Stammverzeichnis des Volumes den Ordner „DCIM“, „AVCHD“ oder „PRIVATE\\ACHD“ enthält oder wenn der Benutzer in der Systemsteuerung unter „Automatische Wiedergabe“ die Option **Gewünschte Aktion für jeden Medientyp auswählen** aktiviert hat und Bilder im Stammverzeichnis des Volumes gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="a3445-142">If the root of the volume contains a DCIM, AVCHD, or PRIVATE\\ACHD folder, or if a user has enabled **Choose what to do with each type of media** in the AutoPlay Control Panel and pictures are found in the root of the volume, then AutoPlay raises the **ShowPicturesOnArrival** event.</span></span> <span data-ttu-id="a3445-143">Geben Sie im Abschnitt **Startaktionen** die Werte aus der nachfolgenden Tabelle1 für die Aktion beim ersten Start an.</span><span class="sxs-lookup"><span data-stu-id="a3445-143">In the **Launch Actions** section, enter the values from Table 1 below for the first launch action.</span></span>
5.  <span data-ttu-id="a3445-144">Klicken Sie im Abschnitt **Startaktionen** für das Element vom Typ **Inhalt automatisch wiedergeben** auf **Neu hinzufügen**, um eine zweite Startaktion hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="a3445-144">In the **Launch Actions** section for the **AutoPlay Content** item, click **Add New** to add a second launch action.</span></span> <span data-ttu-id="a3445-145">Geben Sie die Werte aus der nachfolgenden Tabelle2 für die Aktion beim zweiten Start an:</span><span class="sxs-lookup"><span data-stu-id="a3445-145">Enter the values in Table 2 below for the second launch action.</span></span>
6.  <span data-ttu-id="a3445-146">Wählen Sie in der Dropdownliste **Verfügbare Deklarationen** die Option **Dateitypzuordnungen** aus, und klicken Sie anschließend auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="a3445-146">In the **Available Declarations** drop-down list, select **File Type Associations** and click **Add**.</span></span> <span data-ttu-id="a3445-147">Setzen Sie in den Eigenschaften der neuen Deklaration vom Typ **Dateitypzuordnungen** das Feld **Anzeigename** auf **AutoPlay Copy or Show Images** und das Feld **Name** auf **image\_association1**.</span><span class="sxs-lookup"><span data-stu-id="a3445-147">In the Properties of the new **File Type Associations** declaration, set the **Display Name** field to **AutoPlay Copy or Show Images** and the **Name** field to **image\_association1**.</span></span> <span data-ttu-id="a3445-148">Klicken Sie im Abschnitt **Unterstützte Dateitypen** auf **Neu hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="a3445-148">In the **Supported File Types** section, click **Add New**.</span></span> <span data-ttu-id="a3445-149">Legen Sie im Feld **Dateityp** die Option **.jpg** fest.</span><span class="sxs-lookup"><span data-stu-id="a3445-149">Set the **File Type** field to **.jpg**.</span></span> <span data-ttu-id="a3445-150">Legen Sie im Abschnitt **Unterstützte Dateitypen** das Feld **Dateityp** der neuen Dateizuordnung auf **.png** fest.</span><span class="sxs-lookup"><span data-stu-id="a3445-150">In the **Supported File Types** section, set the **File Type** field of the new file association to **.png**.</span></span> <span data-ttu-id="a3445-151">Für Inhaltsereignisse filtert die automatische Wiedergabe alle Dateitypen heraus, die nicht explizit Ihrer App zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="a3445-151">For content events, AutoPlay filters out any file types that are not explicitly associated with your app.</span></span>
7.  <span data-ttu-id="a3445-152">Speichern und schließen Sie die Manifestdatei.</span><span class="sxs-lookup"><span data-stu-id="a3445-152">Save and close the manifest file.</span></span>


**<span data-ttu-id="a3445-153">Tabelle1</span><span class="sxs-lookup"><span data-stu-id="a3445-153">Table 1</span></span>**

| <span data-ttu-id="a3445-154">Einstellung</span><span class="sxs-lookup"><span data-stu-id="a3445-154">Setting</span></span>             | <span data-ttu-id="a3445-155">Wert</span><span class="sxs-lookup"><span data-stu-id="a3445-155">Value</span></span>                 |
|---------------------|-----------------------|
| <span data-ttu-id="a3445-156">Verb</span><span class="sxs-lookup"><span data-stu-id="a3445-156">Verb</span></span>                | <span data-ttu-id="a3445-157">show</span><span class="sxs-lookup"><span data-stu-id="a3445-157">show</span></span>                  |
| <span data-ttu-id="a3445-158">Aktionsanzeigename</span><span class="sxs-lookup"><span data-stu-id="a3445-158">Action Display Name</span></span> | <span data-ttu-id="a3445-159">Bilder anzeigen</span><span class="sxs-lookup"><span data-stu-id="a3445-159">Show Pictures</span></span>         |
| <span data-ttu-id="a3445-160">Inhaltsereignis</span><span class="sxs-lookup"><span data-stu-id="a3445-160">Content Event</span></span>       | <span data-ttu-id="a3445-161">ShowPicturesOnArrival</span><span class="sxs-lookup"><span data-stu-id="a3445-161">ShowPicturesOnArrival</span></span> |

<span data-ttu-id="a3445-162">Die Einstellung **Aktionsanzeigename** gibt die Zeichenfolge an, die bei der automatischen Wiedergabe für Ihre App angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a3445-162">The **Action Display Name** setting identifies the string that AutoPlay displays for your app.</span></span> <span data-ttu-id="a3445-163">Die Einstellung **Verb** dient zum Angeben eines Werts, der für die ausgewählte Option an Ihre App übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="a3445-163">The **Verb** setting identifies a value that is passed to your app for the selected option.</span></span> <span data-ttu-id="a3445-164">Sie können mehrere Startaktionen für Ereignisse der automatischen Wiedergabe angeben und mit der Einstellung **Verb** ermitteln, welche Option ein Benutzer für Ihre App ausgewählt hat.</span><span class="sxs-lookup"><span data-stu-id="a3445-164">You can specify multiple launch actions for an AutoPlay event and use the **Verb** setting to determine which option a user has selected for your app.</span></span> <span data-ttu-id="a3445-165">Für welche Option sich der Benutzer entschieden hat, erfahren Sie durch Überprüfen der **verb**-Eigenschaft der an die App übergebenen Startereignisargumente.</span><span class="sxs-lookup"><span data-stu-id="a3445-165">You can tell which option the user selected by checking the **verb** property of the startup event arguments passed to your app.</span></span> <span data-ttu-id="a3445-166">Für die Einstellung **Verb** können Sie einen beliebigen Wert verwenden. Einzige Ausnahme ist **open**: Dieser Wert ist reserviert.</span><span class="sxs-lookup"><span data-stu-id="a3445-166">You can use any value for the **Verb** setting except, **open**, which is reserved.</span></span>

**<span data-ttu-id="a3445-167">Tabelle2</span><span class="sxs-lookup"><span data-stu-id="a3445-167">Table 2</span></span>**  

| <span data-ttu-id="a3445-168">Einstellung</span><span class="sxs-lookup"><span data-stu-id="a3445-168">Setting</span></span>             | <span data-ttu-id="a3445-169">Wert</span><span class="sxs-lookup"><span data-stu-id="a3445-169">Value</span></span>                      |
|---------------------|----------------------------|
| <span data-ttu-id="a3445-170">Verb</span><span class="sxs-lookup"><span data-stu-id="a3445-170">Verb</span></span>                | <span data-ttu-id="a3445-171">copy</span><span class="sxs-lookup"><span data-stu-id="a3445-171">copy</span></span>                       |
| <span data-ttu-id="a3445-172">Aktionsanzeigename</span><span class="sxs-lookup"><span data-stu-id="a3445-172">Action Display Name</span></span> | <span data-ttu-id="a3445-173">Bilder in die Bibliothek kopieren</span><span class="sxs-lookup"><span data-stu-id="a3445-173">Copy Pictures Into Library</span></span> |
| <span data-ttu-id="a3445-174">Inhaltsereignis</span><span class="sxs-lookup"><span data-stu-id="a3445-174">Content Event</span></span>       | <span data-ttu-id="a3445-175">ShowPicturesOnArrival</span><span class="sxs-lookup"><span data-stu-id="a3445-175">ShowPicturesOnArrival</span></span>      |

### <a name="step-2-add-xaml-ui"></a><span data-ttu-id="a3445-176">Schritt 2: Hinzufügen von XAML-UI</span><span class="sxs-lookup"><span data-stu-id="a3445-176">Step 2: Add XAML UI</span></span>

<span data-ttu-id="a3445-177">Öffnen Sie die Datei „MainPage.xaml“, und fügen Sie dem Standardabschnitt &lt;Grid&gt; folgenden XAML-Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="a3445-177">Open the MainPage.xaml file and add the following XAML to the default &lt;Grid&gt; section.</span></span>

```xml
<TextBlock FontSize="18">File List</TextBlock>
<TextBlock x:Name="FilesBlock" HorizontalAlignment="Left" TextWrapping="Wrap"
           VerticalAlignment="Top" Margin="0,20,0,0" Height="280" Width="240" />
<Canvas x:Name="FilesCanvas" HorizontalAlignment="Left" VerticalAlignment="Top"
        Margin="260,20,0,0" Height="280" Width="100"/>
```

### <a name="step-3-add-initialization-code"></a><span data-ttu-id="a3445-178">Schritt 3: Hinzufügen von Initialisierungscode</span><span class="sxs-lookup"><span data-stu-id="a3445-178">Step 3: Add initialization code</span></span>

<span data-ttu-id="a3445-179">Der Code in diesem Schritt überprüft den Verb-Wert in der **Verb**-Eigenschaft. Dabei handelt es sich um eines der Startargumente, die beim **OnFileActivated**-Ereignis an die App übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="a3445-179">The code in this step checks the verb value in the **Verb** property, which is one of the startup arguments passed to the app during the **OnFileActivated** event.</span></span> <span data-ttu-id="a3445-180">Anschließend ruft der Code entsprechend der vom Benutzer ausgewählten Option eine Methode auf.</span><span class="sxs-lookup"><span data-stu-id="a3445-180">The code then calls a method related to the option that the user selected.</span></span> <span data-ttu-id="a3445-181">Beim Kameraspeicherereignis wird bei der automatischen Wiedergabe der Stammordner des Kameraspeichers an die App übergeben.</span><span class="sxs-lookup"><span data-stu-id="a3445-181">For the camera memory event, AutoPlay passes the root folder of the camera storage to the app.</span></span> <span data-ttu-id="a3445-182">Sie können diesen Ordner aus dem ersten Element der **Files**-Eigenschaft abrufen.</span><span class="sxs-lookup"><span data-stu-id="a3445-182">You can retrieve this folder from the first element of the **Files** property.</span></span>

<span data-ttu-id="a3445-183">Öffnen Sie die Datei „App.xaml.cs“, und fügen Sie der **App**-Klasse den folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="a3445-183">Open the App.xaml.cs file and add the following code to the **App** class.</span></span>

```cs
protected override void OnFileActivated(FileActivatedEventArgs args)
{
    if (args.Verb == "show")
    {
        Frame rootFrame = (Frame)Window.Current.Content;
        MainPage page = (MainPage)rootFrame.Content;

        // Call DisplayImages with root folder from camera storage.
        page.DisplayImages((Windows.Storage.StorageFolder)args.Files[0]);
    }

    if (args.Verb == "copy")
    {
        Frame rootFrame = (Frame)Window.Current.Content;
        MainPage page = (MainPage)rootFrame.Content;

        // Call CopyImages with root folder from camera storage.
        page.CopyImages((Windows.Storage.StorageFolder)args.Files[0]);
    }

    base.OnFileActivated(args);
}
```

> <span data-ttu-id="a3445-184">**Hinweis**  Die Methoden `DisplayImages` und `CopyImages` werden in den nächsten Schritten hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a3445-184">**Note**  The `DisplayImages` and `CopyImages` methods are added in the following steps.</span></span>

### <a name="step-4-add-code-to-display-images"></a><span data-ttu-id="a3445-185">Schritt 4: Hinzufügen von Code zum Anzeigen von Bildern</span><span class="sxs-lookup"><span data-stu-id="a3445-185">Step 4: Add code to display images</span></span>

<span data-ttu-id="a3445-186">Fügen Sie in der Datei „MainPage.xaml.cs“ der **MainPage**-Klasse folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="a3445-186">In the MainPage.xaml.cs file add the following code to the **MainPage** class.</span></span>

```cs
async internal void DisplayImages(Windows.Storage.StorageFolder rootFolder)
{
    // Display images from first folder in root\DCIM.
    var dcimFolder = await rootFolder.GetFolderAsync("DCIM");
    var folderList = await dcimFolder.GetFoldersAsync();
    var cameraFolder = folderList[0];
    var fileList = await cameraFolder.GetFilesAsync();
    for (int i = 0; i < fileList.Count; i++)
    {
        var file = (Windows.Storage.StorageFile)fileList[i];
        WriteMessageText(file.Name + "\n");
        DisplayImage(file, i);
    }
}

async private void DisplayImage(Windows.Storage.IStorageItem file, int index)
{
    try
    {
        var sFile = (Windows.Storage.StorageFile)file;
        Windows.Storage.Streams.IRandomAccessStream imageStream =
            await sFile.OpenAsync(Windows.Storage.FileAccessMode.Read);
        Windows.UI.Xaml.Media.Imaging.BitmapImage imageBitmap =
            new Windows.UI.Xaml.Media.Imaging.BitmapImage();
        imageBitmap.SetSource(imageStream);
        var element = new Image();
        element.Source = imageBitmap;
        element.Height = 100;
        Thickness margin = new Thickness();
        margin.Top = index * 100;
        element.Margin = margin;
        FilesCanvas.Children.Add(element);
    }
    catch (Exception e)
    {
       WriteMessageText(e.Message + "\n");
    }
}

// Write a message to MessageBlock on the UI thread.
private Windows.UI.Core.CoreDispatcher messageDispatcher = Window.Current.CoreWindow.Dispatcher;

private async void WriteMessageText(string message, bool overwrite = false)
{
    await messageDispatcher.RunAsync(Windows.UI.Core.CoreDispatcherPriority.Normal,
        () =>
        {
            if (overwrite)
                FilesBlock.Text = message;
            else
                FilesBlock.Text += message;
        });
}
```

### <a name="step-5-add-code-to-copy-images"></a><span data-ttu-id="a3445-187">Schritt 5: Hinzufügen von Code zum Kopieren von Bildern</span><span class="sxs-lookup"><span data-stu-id="a3445-187">Step 5: Add code to copy images</span></span>

<span data-ttu-id="a3445-188">Fügen Sie in der Datei „MainPage.xaml.cs“ der **MainPage**-Klasse folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="a3445-188">In the MainPage.xaml.cs file add the following code to the **MainPage** class.</span></span>

```cs
async internal void CopyImages(Windows.Storage.StorageFolder rootFolder)
{
    // Copy images from first folder in root\DCIM.
    var dcimFolder = await rootFolder.GetFolderAsync("DCIM");
    var folderList = await dcimFolder.GetFoldersAsync();
    var cameraFolder = folderList[0];
    var fileList = await cameraFolder.GetFilesAsync();

    try
    {
        var folderName = "Images " + DateTime.Now.ToString("yyyy-MM-dd HHmmss");
        Windows.Storage.StorageFolder imageFolder = await
            Windows.Storage.KnownFolders.PicturesLibrary.CreateFolderAsync(folderName);

        foreach (Windows.Storage.IStorageItem file in fileList)
        {
            CopyImage(file, imageFolder);
        }
    }
    catch (Exception e)
    {
        WriteMessageText("Failed to copy images.\n" + e.Message + "\n");
    }
}

async internal void CopyImage(Windows.Storage.IStorageItem file,
                              Windows.Storage.StorageFolder imageFolder)
{
    try
    {
        Windows.Storage.StorageFile sFile = (Windows.Storage.StorageFile)file;
        await sFile.CopyAsync(imageFolder, sFile.Name);
        WriteMessageText(sFile.Name + " copied.\n");
    }
    catch (Exception e)
    {
        WriteMessageText("Failed to copy file.\n" + e.Message + "\n");
    }
}
```

### <a name="step-6-build-and-run-the-app"></a><span data-ttu-id="a3445-189">Schritt 6: Erstellen und Ausführen der App</span><span class="sxs-lookup"><span data-stu-id="a3445-189">Step 6: Build and run the app</span></span>

1.  <span data-ttu-id="a3445-190">Drücken SieF5, um die App zu erstellen und bereitzustellen (im Debugmodus).</span><span class="sxs-lookup"><span data-stu-id="a3445-190">Press F5 to build and deploy the app (in debug mode).</span></span>
2.  <span data-ttu-id="a3445-191">Legen Sie eine Kameraspeicherkarte oder ein anderes Speichergerät einer Kamera in Ihren PC ein, um die App auszuführen.</span><span class="sxs-lookup"><span data-stu-id="a3445-191">To run your app, insert a camera memory card or another storage device from a camera into your PC.</span></span> <span data-ttu-id="a3445-192">Wählen Sie dann in der Liste mit den Optionen für die automatische Wiedergabe eine der Inhaltsereignisoptionen aus, die Sie in der Datei „package.appxmanifest“ angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="a3445-192">Then, select one of the content event options that you specified in your package.appxmanifest file from the AutoPlay list of options.</span></span> <span data-ttu-id="a3445-193">Dieser Beispielcode blendet Bilder im DCIM-Ordner auf der Speicherkarte einer Kamera nur ein oder kopiert diese.</span><span class="sxs-lookup"><span data-stu-id="a3445-193">This sample code only displays or copies pictures in the DCIM folder of a camera memory card.</span></span> <span data-ttu-id="a3445-194">Wenn die Speicherkarte Ihrer Kamera Bilder in „AVCHD“ oder „PRIVATE\\ACHD“ speichert, müssen Sie den Code entsprechend ändern.</span><span class="sxs-lookup"><span data-stu-id="a3445-194">If your camera memory card stores pictures in an AVCHD or PRIVATE\\ACHD folder, you will need to update the code accordingly.</span></span>
    <span data-ttu-id="a3445-195">**Hinweis**  Falls Sie keine Kameraspeicherkarte haben, können Sie einen USB-Stick verwenden, sofern dieser im Stammverzeichnis einen Ordner mit dem Namen **DCIM** und dieser wiederum den Ordner „DCIM“ als Unterordner mit Bildern enthält.</span><span class="sxs-lookup"><span data-stu-id="a3445-195">**Note**  If you don't have a camera memory card, you can use a flash drive if it has a folder named **DCIM** in the root and if the DCIM folder has a subfolder that contains images.</span></span>

## <a name="register-for-an-autoplay-device"></a><span data-ttu-id="a3445-196">Registrieren für ein Gerät mit automatischer Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="a3445-196">Register for an AutoPlay device</span></span>


<span data-ttu-id="a3445-197">Sie können Apps als Optionen für Geräteereignisse der **automatischen Wiedergabe** registrieren.</span><span class="sxs-lookup"><span data-stu-id="a3445-197">You can register apps as options for **AutoPlay** device events.</span></span> <span data-ttu-id="a3445-198">Geräteereignisse zur **automatischen Wiedergabe** werden ausgelöst, wenn ein Gerät an einen PC angeschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="a3445-198">**AutoPlay** device events are raised when a device is connected to a PC.</span></span>

<span data-ttu-id="a3445-199">Hier wird gezeigt, wie Sie eine App als Option für die **automatische Wiedergabe** identifizieren, wenn eine Kamera an einen PC angeschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="a3445-199">Here we show how to identify your app as an **AutoPlay** option when a camera is connected to a PC.</span></span> <span data-ttu-id="a3445-200">Die App wird als Handler für das **WPD\\ImageSourceAutoPlay**-Ereignis registriert.</span><span class="sxs-lookup"><span data-stu-id="a3445-200">The app registers as a handler for the **WPD\\ImageSourceAutoPlay** event.</span></span> <span data-ttu-id="a3445-201">Dabei handelt es sich um ein häufiges Ereignis, das vom WPD-System (Windows Portable Device) ausgelöst wird, wenn es von Kameras und anderen Bildverarbeitungsgeräten benachrichtigt wird, dass es sich dabei um eine ImageSource mit MTP handelt.</span><span class="sxs-lookup"><span data-stu-id="a3445-201">This is a common event that the Windows Portable Device (WPD) system raises when cameras and other imaging devices notify it that they are an ImageSource using MTP.</span></span> <span data-ttu-id="a3445-202">Weitere Informationen finden Sie unter [Tragbare Windows-Geräte](https://msdn.microsoft.com/library/windows/hardware/ff597729).</span><span class="sxs-lookup"><span data-stu-id="a3445-202">For more info, see [Windows Portable Devices](https://msdn.microsoft.com/library/windows/hardware/ff597729).</span></span>

<span data-ttu-id="a3445-203">**Wichtig**  Die [**Windows.Devices.Portable.StorageDevice**](https://msdn.microsoft.com/library/windows/apps/br225654)-APIs sind Teil der [Desktopgerätefamilie](https://msdn.microsoft.com/library/windows/apps/dn894631).</span><span class="sxs-lookup"><span data-stu-id="a3445-203">**Important**  The [**Windows.Devices.Portable.StorageDevice**](https://msdn.microsoft.com/library/windows/apps/br225654) APIs are part of the [desktop device family](https://msdn.microsoft.com/library/windows/apps/dn894631).</span></span> <span data-ttu-id="a3445-204">Apps können diese APIs nur auf Windows10-Geräten der Desktopgerätefamilie (z.B. PCs) verwenden.</span><span class="sxs-lookup"><span data-stu-id="a3445-204">Apps can use these APIs only on Windows 10 devices in the desktop device family, such as PCs.</span></span>

 

### <a name="step-1-create-a-new-project-and-add-autoplay-declarations"></a><span data-ttu-id="a3445-205">Schritt 1: Erstellen eines neuen Projekts und Hinzufügen von Deklarationen für die automatische Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="a3445-205">Step 1: Create a new project and add AutoPlay declarations</span></span>

1.  <span data-ttu-id="a3445-206">Öffnen Sie Visual Studio, und wählen Sie im Menü **Datei** die Option **Neues Projekt** aus.</span><span class="sxs-lookup"><span data-stu-id="a3445-206">Open Visual Studio and select **New Project** from the **File** menu.</span></span> <span data-ttu-id="a3445-207">Wählen Sie im Abschnitt **VisualC#** unter **Windows** die Option **Leere App (Universelle Windows-App)** aus.</span><span class="sxs-lookup"><span data-stu-id="a3445-207">In the **Visual C#** section, under **Windows**, select **Blank App (Universal Windows)**.</span></span> <span data-ttu-id="a3445-208">Nennen Sie die App **AutoPlayDevice\_Camera**, und klicken Sie auf **OK.**</span><span class="sxs-lookup"><span data-stu-id="a3445-208">Name the app **AutoPlayDevice\_Camera** and click **OK.**</span></span>
2.  <span data-ttu-id="a3445-209">Öffnen Sie die Datei „Package.appxmanifest“, und wählen Sie die Registerkarte **Funktionen** aus.</span><span class="sxs-lookup"><span data-stu-id="a3445-209">Open the Package.appxmanifest file and select the **Capabilities** tab.</span></span> <span data-ttu-id="a3445-210">Wählen Sie die Funktion **Wechselmedien** aus.</span><span class="sxs-lookup"><span data-stu-id="a3445-210">Select the **Removable Storage** capability.</span></span> <span data-ttu-id="a3445-211">Damit geben Sie der App Zugriff auf die Daten auf der Kamera als Wechselmedien-Volumegerät.</span><span class="sxs-lookup"><span data-stu-id="a3445-211">This gives the app access to the data on the camera as a removable storage volume device.</span></span>
3.  <span data-ttu-id="a3445-212">Klicken Sie in der Manifestdatei auf die Registerkarte **Deklarationen**.</span><span class="sxs-lookup"><span data-stu-id="a3445-212">In the manifest file, select the **Declarations** tab.</span></span> <span data-ttu-id="a3445-213">Wählen Sie in der Dropdownliste **Verfügbare Deklarationen** die Option **Gerät automatisch wiedergeben** aus, und klicken Sie anschließend auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="a3445-213">In the **Available Declarations** drop-down list, select **AutoPlay Device** and click **Add**.</span></span> <span data-ttu-id="a3445-214">Wählen Sie das neue Element vom Typ **Gerät automatisch wiedergeben** aus, das der Liste **Unterstützte Deklarationen** hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="a3445-214">Select the new **AutoPlay Device** item that was added to the **Supported Declarations** list.</span></span>
4.  <span data-ttu-id="a3445-215">Die Deklaration **Gerät automatisch wiedergeben** erkennt Ihre App als Option, wenn von der automatischen Wiedergabe ein Geräteereignis ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="a3445-215">An **AutoPlay Device** declaration identifies your app as an option when AutoPlay raises a device event for known events.</span></span> <span data-ttu-id="a3445-216">Geben Sie im Abschnitt **Startaktionen** die Werte aus der nachfolgenden Tabelle für die Aktion beim ersten Start an.</span><span class="sxs-lookup"><span data-stu-id="a3445-216">In the **Launch Actions** section, enter the values in the table below for the first launch action.</span></span>
5.  <span data-ttu-id="a3445-217">Wählen Sie in der Dropdownliste **Verfügbare Deklarationen** die Option **Dateitypzuordnungen** aus, und klicken Sie anschließend auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="a3445-217">In the **Available Declarations** drop-down list, select **File Type Associations** and click **Add**.</span></span> <span data-ttu-id="a3445-218">Setzen Sie in den Eigenschaften der neuen Deklaration vom Typ **Dateitypzuordnungen** das Feld **Anzeigename** auf **Show Images from Camera** und das Feld **Name** auf **image\_association1**.</span><span class="sxs-lookup"><span data-stu-id="a3445-218">In the Properties of the new **File Type Associations** declaration, set the **Display Name** field to **Show Images from Camera** and the **Name** field to **camera\_association1**.</span></span> <span data-ttu-id="a3445-219">Klicken Sie im Abschnitt **Unterstützte Dateitypen** auf **Neu hinzufügen** (falls erforderlich).</span><span class="sxs-lookup"><span data-stu-id="a3445-219">In the **Supported File Types** section, click **Add New** (if needed).</span></span> <span data-ttu-id="a3445-220">Legen Sie im Feld **Dateityp** die Option **.jpg** fest.</span><span class="sxs-lookup"><span data-stu-id="a3445-220">Set the **File Type** field to **.jpg**.</span></span> <span data-ttu-id="a3445-221">Klicken Sie im Abschnitt **Unterstützte Dateitypen** erneut auf **Neu hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="a3445-221">In the **Supported File Types** section, click **Add New** again.</span></span> <span data-ttu-id="a3445-222">Legen Sie das Feld **Dateityp** der neuen Dateizuordnung auf **.png** fest.</span><span class="sxs-lookup"><span data-stu-id="a3445-222">Set the **File Type** field of the new file association to **.png**.</span></span> <span data-ttu-id="a3445-223">Für Inhaltsereignisse filtert die automatische Wiedergabe alle Dateitypen heraus, die nicht explizit Ihrer App zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="a3445-223">For content events, AutoPlay filters out any file types that are not explicitly associated with your app.</span></span>
6.  <span data-ttu-id="a3445-224">Speichern und schließen Sie die Manifestdatei.</span><span class="sxs-lookup"><span data-stu-id="a3445-224">Save and close the manifest file.</span></span>

| <span data-ttu-id="a3445-225">Einstellung</span><span class="sxs-lookup"><span data-stu-id="a3445-225">Setting</span></span>             | <span data-ttu-id="a3445-226">Wert</span><span class="sxs-lookup"><span data-stu-id="a3445-226">Value</span></span>            |
|---------------------|------------------|
| <span data-ttu-id="a3445-227">Verb</span><span class="sxs-lookup"><span data-stu-id="a3445-227">Verb</span></span>                | <span data-ttu-id="a3445-228">show</span><span class="sxs-lookup"><span data-stu-id="a3445-228">show</span></span>             |
| <span data-ttu-id="a3445-229">Aktionsanzeigename</span><span class="sxs-lookup"><span data-stu-id="a3445-229">Action Display Name</span></span> | <span data-ttu-id="a3445-230">Bilder anzeigen</span><span class="sxs-lookup"><span data-stu-id="a3445-230">Show Pictures</span></span>    |
| <span data-ttu-id="a3445-231">Inhaltsereignis</span><span class="sxs-lookup"><span data-stu-id="a3445-231">Content Event</span></span>       | <span data-ttu-id="a3445-232">WPD\\ImageSource</span><span class="sxs-lookup"><span data-stu-id="a3445-232">WPD\\ImageSource</span></span> |

<span data-ttu-id="a3445-233">Die Einstellung **Aktionsanzeigename** gibt die Zeichenfolge an, die bei der automatischen Wiedergabe für Ihre App angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a3445-233">The **Action Display Name** setting identifies the string that AutoPlay displays for your app.</span></span> <span data-ttu-id="a3445-234">Die Einstellung **Verb** dient zum Angeben eines Werts, der für die ausgewählte Option an Ihre App übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="a3445-234">The **Verb** setting identifies a value that is passed to your app for the selected option.</span></span> <span data-ttu-id="a3445-235">Sie können mehrere Startaktionen für Ereignisse der automatischen Wiedergabe angeben und mit der Einstellung **Verb** ermitteln, welche Option ein Benutzer für Ihre App ausgewählt hat.</span><span class="sxs-lookup"><span data-stu-id="a3445-235">You can specify multiple launch actions for an AutoPlay event and use the **Verb** setting to determine which option a user has selected for your app.</span></span> <span data-ttu-id="a3445-236">Für welche Option sich der Benutzer entschieden hat, erfahren Sie durch Überprüfen der **verb**-Eigenschaft der an die App übergebenen Startereignisargumente.</span><span class="sxs-lookup"><span data-stu-id="a3445-236">You can tell which option the user selected by checking the **verb** property of the startup event arguments passed to your app.</span></span> <span data-ttu-id="a3445-237">Für die Einstellung **Verb** können Sie einen beliebigen Wert verwenden. Einzige Ausnahme ist **open**: Dieser Wert ist reserviert.</span><span class="sxs-lookup"><span data-stu-id="a3445-237">You can use any value for the **Verb** setting except, **open**, which is reserved.</span></span> <span data-ttu-id="a3445-238">Ein Beispiel zur Verwendung mehrerer Verben in einer einzelnen App finden Sie unter [Registrieren für Inhalt für die automatische Wiedergabe](#register-for-autoplay-content).</span><span class="sxs-lookup"><span data-stu-id="a3445-238">For an example of using multiple verbs in a single app, see [Register for AutoPlay content](#register-for-autoplay-content).</span></span>

### <a name="step-2-add-assembly-reference-for-the-desktop-extensions"></a><span data-ttu-id="a3445-239">Schritt 2: Hinzufügen von Assemblyverweisen für die Desktoperweiterungen</span><span class="sxs-lookup"><span data-stu-id="a3445-239">Step 2: Add assembly reference for the desktop extensions</span></span>

<span data-ttu-id="a3445-240">Die APIs, die für den Speicherzugriff auf einem tragbaren Windows-Gerät erforderlich sind ([**Windows.Devices.Portable.StorageDevice**](https://msdn.microsoft.com/library/windows/apps/br225654)), sind Teil der [Desktopgerätefamilie](https://msdn.microsoft.com/library/windows/apps/dn894631).</span><span class="sxs-lookup"><span data-stu-id="a3445-240">The APIs required to access storage on a Windows Portable Device, [**Windows.Devices.Portable.StorageDevice**](https://msdn.microsoft.com/library/windows/apps/br225654), are part of the desktop [desktop device family](https://msdn.microsoft.com/library/windows/apps/dn894631).</span></span> <span data-ttu-id="a3445-241">Dies bedeutet, dass eine spezielle Assembly erforderlich ist, um die APIs zu verwenden, und dass diese Aufrufe nur auf einem Gerät der Desktopgerätefamilie (z.B. einem PC) funktionieren.</span><span class="sxs-lookup"><span data-stu-id="a3445-241">This means a special assembly is required to use the APIs and those calls will only work on a device in the desktop device family (such as a PC).</span></span>

1.  <span data-ttu-id="a3445-242">Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Verweise**, und wählen Sie dann **Verweis hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="a3445-242">In **Solution Explorer**, right click on **References** and then **Add Reference...**.</span></span>
2.  <span data-ttu-id="a3445-243">Erweitern Sie die Option **Universal Windows**, und klicken Sie auf **Erweiterungen**.</span><span class="sxs-lookup"><span data-stu-id="a3445-243">Expand **Universal Windows** and click **Extensions**.</span></span>
3.  <span data-ttu-id="a3445-244">Wählen Sie dann **Windows Desktop Extensions for the UWP** aus, und klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="a3445-244">Then select **Windows Desktop Extensions for the UWP** and click **OK**.</span></span>

### <a name="step-3-add-xaml-ui"></a><span data-ttu-id="a3445-245">Schritt 3: Hinzufügen von XAML-UI</span><span class="sxs-lookup"><span data-stu-id="a3445-245">Step 3: Add XAML UI</span></span>

<span data-ttu-id="a3445-246">Öffnen Sie die Datei „MainPage.xaml“, und fügen Sie dem Standardabschnitt &lt;Grid&gt; folgenden XAML-Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="a3445-246">Open the MainPage.xaml file and add the following XAML to the default &lt;Grid&gt; section.</span></span>

```xml
<StackPanel Orientation="Vertical" Margin="10,0,-10,0">
    <TextBlock FontSize="24">Device Information</TextBlock>
    <StackPanel Orientation="Horizontal">
        <TextBlock x:Name="DeviceInfoTextBlock" FontSize="18" Height="400" Width="400" VerticalAlignment="Top" />
        <ListView x:Name="ImagesList" HorizontalAlignment="Left" Height="400" VerticalAlignment="Top" Width="400">
            <ListView.ItemTemplate>
                <DataTemplate>
                    <StackPanel Orientation="Vertical">
                        <Image Source="{Binding Path=Source}" />
                        <TextBlock Text="{Binding Path=Name}" />
                    </StackPanel>
                </DataTemplate>
            </ListView.ItemTemplate>
            <ListView.ItemsPanel>
                <ItemsPanelTemplate>
                    <WrapGrid Orientation="Horizontal" ItemHeight="100" ItemWidth="120"></WrapGrid>
                </ItemsPanelTemplate>
            </ListView.ItemsPanel>
        </ListView>
    </StackPanel>
</StackPanel>
```

### <a name="step-4-add-activation-code"></a><span data-ttu-id="a3445-247">Schritt 4: Hinzufügen von Aktivierungscode</span><span class="sxs-lookup"><span data-stu-id="a3445-247">Step 4: Add activation code</span></span>

<span data-ttu-id="a3445-248">Der Code in diesem Schritts verweist auf die Kamera als [**StorageDevice**](https://msdn.microsoft.com/library/windows/apps/br225654), indem er die Geräteinformations-ID der Kamera an die [**FromId**](https://msdn.microsoft.com/library/windows/apps/br225655)-Methode übergibt.</span><span class="sxs-lookup"><span data-stu-id="a3445-248">The code in this step references the camera as a [**StorageDevice**](https://msdn.microsoft.com/library/windows/apps/br225654) by passing the device information Id of the camera to the [**FromId**](https://msdn.microsoft.com/library/windows/apps/br225655) method.</span></span> <span data-ttu-id="a3445-249">Die Geräteinformations-ID der Kamera wird ermittelt, indem die Ereignisargumente zunächst in [**DeviceActivatedEventArgs**](https://msdn.microsoft.com/library/windows/apps/br224710) umgewandelt werden und anschließend der Wert von der [**DeviceInformationId**](https://msdn.microsoft.com/library/windows/apps/br224711)-Eigenschaft abgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="a3445-249">The device information Id of the camera is obtained by first casting the event arguments as [**DeviceActivatedEventArgs**](https://msdn.microsoft.com/library/windows/apps/br224710), and then getting the value from the [**DeviceInformationId**](https://msdn.microsoft.com/library/windows/apps/br224711) property.</span></span>

<span data-ttu-id="a3445-250">Öffnen Sie die Datei „App.xaml.cs“, und fügen Sie der **App**-Klasse den folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="a3445-250">Open the App.xaml.cs file and add the following code to the **App** class.</span></span>

```cs
protected override void OnActivated(IActivatedEventArgs args)
{
   if (args.Kind == ActivationKind.Device)
   {
      Frame rootFrame = null;
      // Ensure that the current page exists and is activated
      if (Window.Current.Content == null)
      {
         rootFrame = new Frame();
         rootFrame.Navigate(typeof(MainPage));
         Window.Current.Content = rootFrame;
      }
      else
      {
         rootFrame = Window.Current.Content as Frame;
      }
      Window.Current.Activate();

      // Make sure the necessary APIs are present on the device
      bool storageDeviceAPIPresent =
      Windows.Foundation.Metadata.ApiInformation.IsTypePresent("Windows.Devices.Portable.StorageDevice");

      if (storageDeviceAPIPresent)
      {
         // Reference the current page as type MainPage
         var mPage = rootFrame.Content as MainPage;

         // Cast the activated event args as DeviceActivatedEventArgs and show images
         var deviceArgs = args as DeviceActivatedEventArgs;
         if (deviceArgs != null)
         {
            mPage.ShowImages(Windows.Devices.Portable.StorageDevice.FromId(deviceArgs.DeviceInformationId));
         }
      }
      else
      {
         // Handle case where APIs are not present (when the device is not part of the desktop device family)
      }

   }

   base.OnActivated(args);
}
```

> <span data-ttu-id="a3445-251">**Hinweis**  Die `ShowImages`-Methode wird im nächsten Schritt hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a3445-251">**Note**  The `ShowImages` method is added in the following step.</span></span>

### <a name="step-5-add-code-to-display-device-information"></a><span data-ttu-id="a3445-252">Schritt 5: Hinzufügen von Code zum Anzeigen von Geräteinformationen</span><span class="sxs-lookup"><span data-stu-id="a3445-252">Step 5: Add code to display device information</span></span>

<span data-ttu-id="a3445-253">Informationen zur Kamera erhalten Sie über die Eigenschaften der [**StorageDevice**](https://msdn.microsoft.com/library/windows/apps/br225654)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="a3445-253">You can obtain information about the camera from the properties of the [**StorageDevice**](https://msdn.microsoft.com/library/windows/apps/br225654) class.</span></span> <span data-ttu-id="a3445-254">Der Code in diesem Schritt zeigt bei der Ausführung der App den Gerätenamen und andere Informationen für den Benutzer an.</span><span class="sxs-lookup"><span data-stu-id="a3445-254">The code in this step displays the device name and other info to the user when the app runs.</span></span> <span data-ttu-id="a3445-255">Anschließend ruft der Code die Methoden GetImageList und GetThumbnail auf, die Sie im nächsten Schritt hinzufügen, um Miniaturansichten der auf der Kamera gespeicherten Bilder anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a3445-255">The code then calls the GetImageList and GetThumbnail methods, which you will add in the next step, to display thumbnails of the images stored on the camera</span></span>

<span data-ttu-id="a3445-256">Fügen Sie in der Datei „MainPage.xaml.cs“ der **MainPage**-Klasse folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="a3445-256">In the MainPage.xaml.cs file, add the following code to the **MainPage** class.</span></span>

```cs
private Windows.Storage.StorageFolder rootFolder;

internal async void ShowImages(Windows.Storage.StorageFolder folder)
{
    DeviceInfoTextBlock.Text = "Display Name = " + folder.DisplayName + "\n";
    DeviceInfoTextBlock.Text += "Display Type =  " + folder.DisplayType + "\n";
    DeviceInfoTextBlock.Text += "FolderRelativeId = " + folder.FolderRelativeId + "\n";

    // Reference first folder of the device as the root
    rootFolder = (await folder.GetFoldersAsync())[0];
    var imageList = await GetImageList(rootFolder);

    foreach (Windows.Storage.StorageFile img in imageList)
    {
        ImagesList.Items.Add(await GetThumbnail(img));
    }
}
```

> <span data-ttu-id="a3445-257">**Hinweis**  Die Methoden `GetImageList` und `GetThumbnail` werden im nächsten Schritt hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a3445-257">**Note**  The `GetImageList` and `GetThumbnail` methods are added in the following step.</span></span>

 

### <a name="step-6-add-code-to-display-images"></a><span data-ttu-id="a3445-258">Schritt 6: Hinzufügen von Code zum Anzeigen von Bildern</span><span class="sxs-lookup"><span data-stu-id="a3445-258">Step 6: Add code to display images</span></span>

<span data-ttu-id="a3445-259">Der Code in diesem Schritt zeigt Miniaturansichten der Bilder an, die auf der Kamera gespeichert sind.</span><span class="sxs-lookup"><span data-stu-id="a3445-259">The code in this step displays thumbnails of the images stored on the camera.</span></span> <span data-ttu-id="a3445-260">Der Code ruft die Miniaturansicht mit asynchronen Aufrufen an die Kamera ab.</span><span class="sxs-lookup"><span data-stu-id="a3445-260">The code makes asynchronous calls to the camera to get the thumbnail image.</span></span> <span data-ttu-id="a3445-261">Der nächste asynchrone Aufruf erfolgt aber nicht, bis der vorherige asynchrone Aufruf abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="a3445-261">However, the next asynchronous call doesn't occur until the previous asynchronous call completes.</span></span> <span data-ttu-id="a3445-262">Auf diese Weise wird sichergestellt, dass nur jeweils ein Aufruf an die Kamera gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="a3445-262">This ensures that only one request is made to the camera at a time.</span></span>

<span data-ttu-id="a3445-263">Fügen Sie in der Datei „MainPage.xaml.cs“ der **MainPage**-Klasse folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="a3445-263">In the MainPage.xaml.cs file, add the following code to the **MainPage** class.</span></span>

```cs
async private System.Threading.Tasks.Task<List<Windows.Storage.StorageFile>> GetImageList(Windows.Storage.StorageFolder folder)
{
    var result = await folder.GetFilesAsync();
    var subFolders = await folder.GetFoldersAsync();
    foreach (Windows.Storage.StorageFolder f in subFolders)
        result = result.Union(await GetImageList(f)).ToList();

    return (from f in result orderby f.Name select f).ToList();
}

async private System.Threading.Tasks.Task<Image> GetThumbnail(Windows.Storage.StorageFile img)
{
    // Get the thumbnail to display
    var thumbnail = await img.GetThumbnailAsync(Windows.Storage.FileProperties.ThumbnailMode.SingleItem,
                                                100,
                                                Windows.Storage.FileProperties.ThumbnailOptions.UseCurrentScale);

    // Create a XAML Image object bind to on the display page
    var result = new Image();
    result.Height = thumbnail.OriginalHeight;
    result.Width = thumbnail.OriginalWidth;
    result.Name = img.Name;
    var imageBitmap = new Windows.UI.Xaml.Media.Imaging.BitmapImage();
    imageBitmap.SetSource(thumbnail);
    result.Source = imageBitmap;

    return result;
}
```

### <a name="step-7-build-and-run-the-app"></a><span data-ttu-id="a3445-264">Schritt 7: Erstellen und Ausführen der App</span><span class="sxs-lookup"><span data-stu-id="a3445-264">Step 7: Build and run the app</span></span>

1.  <span data-ttu-id="a3445-265">Drücken SieF5, um die App zu erstellen und bereitzustellen (im Debugmodus).</span><span class="sxs-lookup"><span data-stu-id="a3445-265">Press F5 to build and deploy the app (in debug mode).</span></span>
2.  <span data-ttu-id="a3445-266">Führen Sie Ihre App aus, indem Sie eine Kamera an Ihren Computer anschließen.</span><span class="sxs-lookup"><span data-stu-id="a3445-266">To run your app, connect a camera to your machine.</span></span> <span data-ttu-id="a3445-267">Wählen Sie die App anschließend in der Liste mit Optionen für die automatische Wiedergabe aus.</span><span class="sxs-lookup"><span data-stu-id="a3445-267">Then select the app from the AutoPlay list of options.</span></span>
    <span data-ttu-id="a3445-268">**Hinweis**  Nicht alle Kameras zeigen das **WPD\\ImageSource**-Geräteereignis für die automatische Wiedergabe an.</span><span class="sxs-lookup"><span data-stu-id="a3445-268">**Note**  Not all cameras advertise for the **WPD\\ImageSource** AutoPlay device event.</span></span>

     

## <a name="configure-removable-storage"></a><span data-ttu-id="a3445-269">Konfigurieren von Wechselmedien</span><span class="sxs-lookup"><span data-stu-id="a3445-269">Configure removable storage</span></span>


<span data-ttu-id="a3445-270">Sie können ein Volumegerät wie eine Speicherkarte oder einen USB-Stick als Gerät für die **automatische Wiedergabe** identifizieren, wenn das Volumegerät an einen PC angeschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="a3445-270">You can identify a volume device such as a memory card or thumb drive as an **AutoPlay** device when the volume device is connected to a PC.</span></span> <span data-ttu-id="a3445-271">Das ist vor allem dann sehr nützlich, wenn Sie möchten, dass dem Benutzer bei der **automatischen Wiedergabe** eine bestimmte App für Ihr Volumegerät angeboten wird.</span><span class="sxs-lookup"><span data-stu-id="a3445-271">This is especially useful when you want to associate a specific app for **AutoPlay** to present to the user for your volume device.</span></span>

<span data-ttu-id="a3445-272">Im Folgenden zeigen wir, wie Sie Ihr Volumegerät als Gerät zur **automatischen Wiedergabe** identifizieren.</span><span class="sxs-lookup"><span data-stu-id="a3445-272">Here we show how to identify your volume device as an **AutoPlay** device.</span></span>

<span data-ttu-id="a3445-273">Identifizieren Sie Ihr Volumegerät als Gerät für die **automatische Wiedergabe**, indem Sie dem Stammverzeichnis des Geräts die Datei „autorun.inf“ hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="a3445-273">To identify your volume device as an **AutoPlay** device, add an autorun.inf file to the root drive of your device.</span></span> <span data-ttu-id="a3445-274">Fügen Sie in der Datei „autorun.inf“ im **AutoRun**-Abschnitt einen **CustomEvent**-Schlüssel hinzu.</span><span class="sxs-lookup"><span data-stu-id="a3445-274">In the autorun.inf file, add a **CustomEvent** key to the **AutoRun** section.</span></span> <span data-ttu-id="a3445-275">Wenn Ihr Volumegerät an einen PC angeschlossen wird, findet die **automatische Wiedergabe** die Datei „autorun.inf“ und behandelt Ihr Volume als ein Gerät.</span><span class="sxs-lookup"><span data-stu-id="a3445-275">When your volume device connects to a PC, **AutoPlay** will find the autorun.inf file and treat your volume as a device.</span></span> <span data-ttu-id="a3445-276">Die **automatische Wiedergabe** erstellt anhand des Namens, den Sie für den **CustomEvent**-Schlüssel angegeben haben, ein Ereignis zur **automatischen Wiedergabe**.</span><span class="sxs-lookup"><span data-stu-id="a3445-276">**AutoPlay** will create an **AutoPlay** event by using the name that you supplied for the **CustomEvent** key.</span></span> <span data-ttu-id="a3445-277">Sie können eine App erstellen und sie dann als Handler für dieses Ereignis zur **automatischen Wiedergabe** registrieren.</span><span class="sxs-lookup"><span data-stu-id="a3445-277">You can then create an app and register the app as a handler for that **AutoPlay** event.</span></span> <span data-ttu-id="a3445-278">Wenn das Gerät an den PC angeschlossen wird, bietet die **automatische Wiedergabe** Ihre App als Handler für Ihr Volumegerät an.</span><span class="sxs-lookup"><span data-stu-id="a3445-278">When the device is connected to the PC, **AutoPlay** will show your app as a handler for your volume device.</span></span> <span data-ttu-id="a3445-279">Weitere Informationen zu Dateien vom Typ „autorun.inf“ finden Sie unter [Autorun.inf-Einträge](https://msdn.microsoft.com/library/windows/desktop/cc144200).</span><span class="sxs-lookup"><span data-stu-id="a3445-279">For more info on autorun.inf files, see [autorun.inf entries](https://msdn.microsoft.com/library/windows/desktop/cc144200).</span></span>

### <a name="step-1-create-an-autoruninf-file"></a><span data-ttu-id="a3445-280">Schritt 1: Erstellen der Datei „autorun.inf“</span><span class="sxs-lookup"><span data-stu-id="a3445-280">Step 1: Create an autorun.inf file</span></span>

<span data-ttu-id="a3445-281">Fügen Sie im Stammverzeichnis Ihres Volumegeräts eine Datei namens „autorun.inf“ hinzu.</span><span class="sxs-lookup"><span data-stu-id="a3445-281">In the root drive of your volume device, add a file named autorun.inf.</span></span> <span data-ttu-id="a3445-282">Öffnen Sie die Datei „autorun.inf“, und fügen Sie den folgenden Text hinzu.</span><span class="sxs-lookup"><span data-stu-id="a3445-282">Open the autorun.inf file and add the following text.</span></span>

``` syntax
[AutoRun]
CustomEvent=AutoPlayCustomEventQuickstart
```

### <a name="step-2-create-a-new-project-and-add-autoplay-declarations"></a><span data-ttu-id="a3445-283">Schritt 2: Erstellen eines neuen Projekts und Hinzufügen von Deklarationen für die automatische Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="a3445-283">Step 2: Create a new project and add AutoPlay declarations</span></span>

1.  <span data-ttu-id="a3445-284">Öffnen Sie Visual Studio, und wählen Sie im Menü **Datei** die Option **Neues Projekt** aus.</span><span class="sxs-lookup"><span data-stu-id="a3445-284">Open Visual Studio and select **New Project** from the **File** menu.</span></span> <span data-ttu-id="a3445-285">Wählen Sie im Abschnitt **VisualC#** unter **Windows** die Option **Leere App (Universelle Windows-App)** aus.</span><span class="sxs-lookup"><span data-stu-id="a3445-285">In the **Visual C#** section, under **Windows**, select **Blank App (Universal Windows)**.</span></span> <span data-ttu-id="a3445-286">Nennen Sie die Anwendung **AutoPlayCustomEvent**, und klicken Sie auf **OK.**</span><span class="sxs-lookup"><span data-stu-id="a3445-286">Name the application **AutoPlayCustomEvent** and click **OK.**</span></span>
2.  <span data-ttu-id="a3445-287">Öffnen Sie die Datei „Package.appxmanifest“, und wählen Sie die Registerkarte **Funktionen** aus.</span><span class="sxs-lookup"><span data-stu-id="a3445-287">Open the Package.appxmanifest file and select the **Capabilities** tab.</span></span> <span data-ttu-id="a3445-288">Wählen Sie die Funktion **Wechselmedien** aus.</span><span class="sxs-lookup"><span data-stu-id="a3445-288">Select the **Removable Storage** capability.</span></span> <span data-ttu-id="a3445-289">Damit erhält Ihre App Zugriff auf die Dateien und Ordner auf dem Wechselmediengerät.</span><span class="sxs-lookup"><span data-stu-id="a3445-289">This gives the app access to the files and folders on removable storage devices.</span></span>
3.  <span data-ttu-id="a3445-290">Klicken Sie in der Manifestdatei auf die Registerkarte **Deklarationen**.</span><span class="sxs-lookup"><span data-stu-id="a3445-290">In the manifest file, select the **Declarations** tab.</span></span> <span data-ttu-id="a3445-291">Wählen Sie in der Dropdownliste **Verfügbare Deklarationen** die Option **Inhalt automatisch wiedergeben** aus, und klicken Sie anschließend auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="a3445-291">In the **Available Declarations** drop-down list, select **AutoPlay Content** and click **Add**.</span></span> <span data-ttu-id="a3445-292">Wählen Sie das neue Element vom Typ **Inhalt automatisch wiedergeben** aus, das der Liste **Unterstützte Deklarationen** hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="a3445-292">Select the new **AutoPlay Content** item that was added to the **Supported Declarations** list.</span></span>

    <span data-ttu-id="a3445-293">**Hinweis**  Alternativ können Sie auch die Deklaration **Gerät automatisch wiedergeben** für Ihr benutzerdefiniertes Ereignis zur automatischen Wiedergabe hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="a3445-293">**Note**  Alternatively, you can also choose to add an **AutoPlay Device** declaration for your custom AutoPlay event.</span></span>
    
4.  <span data-ttu-id="a3445-294">Geben Sie im Abschnitt **Startaktionen** der Ereignisdeklaration **Inhalt automatisch Wiedergeben** für die Aktion beim ersten Start die Werte in der folgenden Tabelle ein.</span><span class="sxs-lookup"><span data-stu-id="a3445-294">In the **Launch Actions** section for your **AutoPlay Content** event declaration, enter the values in the table below for the first launch action.</span></span>
5.  <span data-ttu-id="a3445-295">Wählen Sie in der Dropdownliste **Verfügbare Deklarationen** die Option **Dateitypzuordnungen** aus, und klicken Sie anschließend auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="a3445-295">In the **Available Declarations** drop-down list, select **File Type Associations** and click **Add**.</span></span> <span data-ttu-id="a3445-296">Setzen Sie in den Eigenschaften der neuen Deklaration vom Typ **Dateitypzuordnungen** das Feld **Anzeigename** auf **Show .ms Files** und das Feld **Name** auf **ms\_association**.</span><span class="sxs-lookup"><span data-stu-id="a3445-296">In the Properties of the new **File Type Associations** declaration, set the **Display Name** field to **Show .ms Files** and the **Name** field to **ms\_association**.</span></span> <span data-ttu-id="a3445-297">Klicken Sie im Abschnitt **Unterstützte Dateitypen** auf **Neu hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="a3445-297">In the **Supported File Types** section, click **Add New**.</span></span> <span data-ttu-id="a3445-298">Legen Sie im Feld **Dateityp** die Option **.ms** fest.</span><span class="sxs-lookup"><span data-stu-id="a3445-298">Set the **File Type** field to **.ms**.</span></span> <span data-ttu-id="a3445-299">Für Inhaltsereignisse filtert die automatische Wiedergabe alle Dateitypen heraus, die nicht explizit Ihrer App zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="a3445-299">For content events, AutoPlay filters out any file types that aren't explicitly associated with your app.</span></span>
6.  <span data-ttu-id="a3445-300">Speichern und schließen Sie die Manifestdatei.</span><span class="sxs-lookup"><span data-stu-id="a3445-300">Save and close the manifest file.</span></span>

| <span data-ttu-id="a3445-301">Einstellung</span><span class="sxs-lookup"><span data-stu-id="a3445-301">Setting</span></span>             | <span data-ttu-id="a3445-302">Wert</span><span class="sxs-lookup"><span data-stu-id="a3445-302">Value</span></span>                         |
|---------------------|-------------------------------|
| <span data-ttu-id="a3445-303">Verb</span><span class="sxs-lookup"><span data-stu-id="a3445-303">Verb</span></span>                | <span data-ttu-id="a3445-304">show</span><span class="sxs-lookup"><span data-stu-id="a3445-304">show</span></span>                          |
| <span data-ttu-id="a3445-305">Aktionsanzeigename</span><span class="sxs-lookup"><span data-stu-id="a3445-305">Action Display Name</span></span> | <span data-ttu-id="a3445-306">Dateien anzeigen</span><span class="sxs-lookup"><span data-stu-id="a3445-306">Show Files</span></span>                    |
| <span data-ttu-id="a3445-307">Inhaltsereignis</span><span class="sxs-lookup"><span data-stu-id="a3445-307">Content Event</span></span>       | <span data-ttu-id="a3445-308">AutoPlayCustomEventQuickstart</span><span class="sxs-lookup"><span data-stu-id="a3445-308">AutoPlayCustomEventQuickstart</span></span> |

<span data-ttu-id="a3445-309">Der Wert für **Inhaltsereignis** ist der Text, den Sie für den **CustomEvent**-Schlüssel in der Datei „autorun.inf“ angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="a3445-309">The **Content Event** value is the text that you supplied for the **CustomEvent** key in your autorun.inf file.</span></span> <span data-ttu-id="a3445-310">Die Einstellung **Aktionsanzeigename** gibt die Zeichenfolge an, die bei der automatischen Wiedergabe für Ihre App angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a3445-310">The **Action Display Name** setting identifies the string that AutoPlay displays for your app.</span></span> <span data-ttu-id="a3445-311">Die Einstellung **Verb** dient zum Angeben eines Werts, der für die ausgewählte Option an Ihre App übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="a3445-311">The **Verb** setting identifies a value that is passed to your app for the selected option.</span></span> <span data-ttu-id="a3445-312">Sie können mehrere Startaktionen für Ereignisse der automatischen Wiedergabe angeben und mit der Einstellung **Verb** ermitteln, welche Option ein Benutzer für Ihre App ausgewählt hat.</span><span class="sxs-lookup"><span data-stu-id="a3445-312">You can specify multiple launch actions for an AutoPlay event and use the **Verb** setting to determine which option a user has selected for your app.</span></span> <span data-ttu-id="a3445-313">Für welche Option sich der Benutzer entschieden hat, erfahren Sie durch Überprüfen der **verb**-Eigenschaft der an die App übergebenen Startereignisargumente.</span><span class="sxs-lookup"><span data-stu-id="a3445-313">You can tell which option the user selected by checking the **verb** property of the startup event arguments passed to your app.</span></span> <span data-ttu-id="a3445-314">Für die Einstellung **Verb** können Sie einen beliebigen Wert verwenden. Einzige Ausnahme ist **open**: Dieser Wert ist reserviert.</span><span class="sxs-lookup"><span data-stu-id="a3445-314">You can use any value for the **Verb** setting except, **open**, which is reserved.</span></span>

### <a name="step-3-add-xaml-ui"></a><span data-ttu-id="a3445-315">Schritt 3: Hinzufügen von XAML-UI</span><span class="sxs-lookup"><span data-stu-id="a3445-315">Step 3: Add XAML UI</span></span>

<span data-ttu-id="a3445-316">Öffnen Sie die Datei „MainPage.xaml“, und fügen Sie dem Standardabschnitt &lt;Grid&gt; folgenden XAML-Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="a3445-316">Open the MainPage.xaml file and add the following XAML to the default &lt;Grid&gt; section.</span></span>

```xml
<StackPanel Orientation="Vertical">
    <TextBlock FontSize="28" Margin="10,0,800,0">Files</TextBlock>
    <TextBlock x:Name="FilesBlock" FontSize="22" Height="600" Margin="10,0,800,0" />
</StackPanel>
```

### <a name="step-4-add-activation-code"></a><span data-ttu-id="a3445-317">Schritt 4: Hinzufügen von Aktivierungscode</span><span class="sxs-lookup"><span data-stu-id="a3445-317">Step 4: Add activation code</span></span>

<span data-ttu-id="a3445-318">Der Code in diesem Schritt ruft eine Methode zum Anzeigen der Ordner im Stammlaufwerk Ihres Volumegeräts auf.</span><span class="sxs-lookup"><span data-stu-id="a3445-318">The code in this step calls a method to display the folders in the root drive of your volume device.</span></span> <span data-ttu-id="a3445-319">Für das Inhaltsereignis zur automatischen Wiedergabe übergibt die automatische Wiedergabe den Stammordner des Speichergeräts in den Startargumenten, die der Anwendung während des **OnFileActivated**-Ereignisses übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="a3445-319">For the AutoPlay content events, AutoPlay passes the root folder of the storage device in the startup arguments passed to the application during the **OnFileActivated** event.</span></span> <span data-ttu-id="a3445-320">Sie können diesen Ordner aus dem ersten Element der **Files**-Eigenschaft abrufen.</span><span class="sxs-lookup"><span data-stu-id="a3445-320">You can retrieve this folder from the first element of the **Files** property.</span></span>

<span data-ttu-id="a3445-321">Öffnen Sie die Datei „App.xaml.cs“, und fügen Sie der **App**-Klasse den folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="a3445-321">Open the App.xaml.cs file and add the following code to the **App** class.</span></span>

```cs
protected override void OnFileActivated(FileActivatedEventArgs args)
{
    var rootFrame = Window.Current.Content as Frame;
    var page = rootFrame.Content as MainPage;

    // Call ShowFolders with root folder from device storage.
    page.DisplayFiles(args.Files[0] as Windows.Storage.StorageFolder);

    base.OnFileActivated(args);
}
```

> <span data-ttu-id="a3445-322">**Hinweis**  Die `DisplayFiles`-Methode wird im nächsten Schritt hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a3445-322">**Note**  The `DisplayFiles` method is added in the following step.</span></span>

 

### <a name="step-5-add-code-to-display-folders"></a><span data-ttu-id="a3445-323">Schritt 5: Hinzufügen von Code zum Anzeigen von Ordnern</span><span class="sxs-lookup"><span data-stu-id="a3445-323">Step 5: Add code to display folders</span></span>

<span data-ttu-id="a3445-324">Fügen Sie in der Datei „MainPage.xaml.cs“ der **MainPage**-Klasse folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="a3445-324">In the MainPage.xaml.cs file add the following code to the **MainPage** class.</span></span>

```cs
internal async void DisplayFiles(Windows.Storage.StorageFolder folder)
{
    foreach (Windows.Storage.StorageFile f in await ReadFiles(folder, ".ms"))
    {
        FilesBlock.Text += "  " + f.Name + "\n";
    }
}

internal async System.Threading.Tasks.Task<IReadOnlyList<Windows.Storage.StorageFile>>
    ReadFiles(Windows.Storage.StorageFolder folder, string fileExtension)
{
    var options = new Windows.Storage.Search.QueryOptions();
    options.FileTypeFilter.Add(fileExtension);
    var query = folder.CreateFileQueryWithOptions(options);
    var files = await query.GetFilesAsync();

    return files;
}
```

### <a name="step-6-build-and-run-the-qpp"></a><span data-ttu-id="a3445-325">Schritt 6: Erstellen und Ausführen der App</span><span class="sxs-lookup"><span data-stu-id="a3445-325">Step 6: Build and run the qpp</span></span>

1.  <span data-ttu-id="a3445-326">Drücken SieF5, um die App zu erstellen und bereitzustellen (im Debugmodus).</span><span class="sxs-lookup"><span data-stu-id="a3445-326">Press F5 to build and deploy the app (in debug mode).</span></span>
2.  <span data-ttu-id="a3445-327">Legen Sie eine Speicherkarte oder ein anderes Speichergerät in Ihren PC ein, um Ihre App auszuführen.</span><span class="sxs-lookup"><span data-stu-id="a3445-327">To run your app, insert a memory card or another storage device into your PC.</span></span> <span data-ttu-id="a3445-328">Wählen Sie die App anschließend in der Liste mit den Handleroptionen für die automatische Wiedergabe aus.</span><span class="sxs-lookup"><span data-stu-id="a3445-328">Then select your app from the list of AutoPlay handler options.</span></span>

## <a name="autoplay-event-reference"></a><span data-ttu-id="a3445-329">Referenz für Ereignisse der automatischen Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="a3445-329">AutoPlay event reference</span></span>


<span data-ttu-id="a3445-330">Das **automatische Wiedergabesystem** ermöglicht es, Apps für eine Vielzahl von Arrival-Ereignissen für Geräte und Volumes (Datenträger) zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="a3445-330">The **AutoPlay** system allows apps to register for a variety of device and volume (disk) arrival events.</span></span> <span data-ttu-id="a3445-331">Wenn Sie die App für Inhaltsereignisse für die **automatische Wiedergabe** registrieren möchten, müssen Sie die Funktion **Wechselmedien** im Paketmanifest aktivieren.</span><span class="sxs-lookup"><span data-stu-id="a3445-331">To register for **AutoPlay** content events, you must enable the **Removable Storage** capability in your package manifest.</span></span> <span data-ttu-id="a3445-332">In der folgenden Tabelle sind die Ereignisse aufgeführt, die Sie für die automatische Wiedergabe registrieren können, wenn sie ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="a3445-332">This table shows the events that you can register for and when they are raised.</span></span>

| <span data-ttu-id="a3445-333">Szenario</span><span class="sxs-lookup"><span data-stu-id="a3445-333">Scenario</span></span>                                                           | <span data-ttu-id="a3445-334">Ereignis</span><span class="sxs-lookup"><span data-stu-id="a3445-334">Event</span></span>                              | <span data-ttu-id="a3445-335">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a3445-335">Description</span></span>   |
|--------------------------------------------------------------------|------------------------------------|---------------|
| <span data-ttu-id="a3445-336">Anzeigen von Fotos auf einer Kamera</span><span class="sxs-lookup"><span data-stu-id="a3445-336">Using photos on a Camera</span></span>                                           | **<span data-ttu-id="a3445-337">WPD\ImageSource</span><span class="sxs-lookup"><span data-stu-id="a3445-337">WPD\ImageSource</span></span>**                | <span data-ttu-id="a3445-338">Ausgelöst für Kameras, die als tragbare Windows-Geräte mit ImageSource-Funktion erkannt wurden.</span><span class="sxs-lookup"><span data-stu-id="a3445-338">Raised for cameras that are identified as Windows Portable Devices and offer the ImageSource capability.</span></span> |
| <span data-ttu-id="a3445-339">Abspielen von Musik auf einem Audioplayer</span><span class="sxs-lookup"><span data-stu-id="a3445-339">Using music on an audio player</span></span>                                     | **<span data-ttu-id="a3445-340">WPD\AudioSource</span><span class="sxs-lookup"><span data-stu-id="a3445-340">WPD\AudioSource</span></span>**                | <span data-ttu-id="a3445-341">Ausgelöst für Mediaplayer, die als tragbare Windows-Geräte mit AudioSource-Funktion erkannt wurden.</span><span class="sxs-lookup"><span data-stu-id="a3445-341">Raised for media players that are identified as Windows Portable Devices and offer the AudioSource capability.</span></span> |
| <span data-ttu-id="a3445-342">Abspielen von Videos auf einer Videokamera</span><span class="sxs-lookup"><span data-stu-id="a3445-342">Using videos on a video camera</span></span>                                     | **<span data-ttu-id="a3445-343">WPD\VideoSource</span><span class="sxs-lookup"><span data-stu-id="a3445-343">WPD\VideoSource</span></span>**                | <span data-ttu-id="a3445-344">Ausgelöst für Videokameras, die als tragbare Windows-Geräte mit VideoSource-Funktion erkannt wurden.</span><span class="sxs-lookup"><span data-stu-id="a3445-344">Raised for video cameras that are identified as Windows Portable Devices and offer the VideoSource capability.</span></span> |
| <span data-ttu-id="a3445-345">Zugriff auf ein verbundenes Flash-Laufwerk oder auf eine externe Festplatte</span><span class="sxs-lookup"><span data-stu-id="a3445-345">Access a connected flash drive or external hard drive</span></span>              | **<span data-ttu-id="a3445-346">StorageOnArrival</span><span class="sxs-lookup"><span data-stu-id="a3445-346">StorageOnArrival</span></span>**               | <span data-ttu-id="a3445-347">Ausgelöst, wenn ein Laufwerk oder ein Volume an den PC angeschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="a3445-347">Raised when a drive or volume is connected to the PC.</span></span>   <span data-ttu-id="a3445-348">Wenn das Laufwerk oder Volume den Ordner „DCIM“, „AVCHD“ oder „PRIVATE\ACHD“ im Stammverzeichnis des Datenträgers enthält, wird stattdessen das **ShowPicturesOnArrival**-Ereignis ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="a3445-348">If the drive or volume contains a DCIM, AVCHD, or PRIVATE\ACHD folder in the root of the disk, the **ShowPicturesOnArrival** event is raised instead.</span></span> |
| <span data-ttu-id="a3445-349">Anzeigen von Fotos auf einem Massenspeicher (Legacy)</span><span class="sxs-lookup"><span data-stu-id="a3445-349">Using photos from mass storage (legacy)</span></span>                            | **<span data-ttu-id="a3445-350">ShowPicturesOnArrival</span><span class="sxs-lookup"><span data-stu-id="a3445-350">ShowPicturesOnArrival</span></span>**          | <span data-ttu-id="a3445-351">Dieses Ereignis wird ausgelöst, wenn das Laufwerk oder das Volume den Ordner „DCIM“, „AVCHD“ oder „PRIVATE\ACHD“ im Stammverzeichnis der Platte enthält.</span><span class="sxs-lookup"><span data-stu-id="a3445-351">Raised when a drive or volume contains a DCIM, AVCHD, or PRIVATE\ACHD folder in the root of the disk.</span></span> <span data-ttu-id="a3445-352">Wenn der Benutzer in der Systemsteuerung unter „Automatische Wiedergabe“ die Option **Gewünschte Aktion für jeden Medientyp auswählen** aktiviert hat, überprüft die automatische Wiedergabe das am PC angeschlossene Volume, um den Inhaltstyp auf dem Datenträger zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="a3445-352">IIf a user  has enabled **Choose what to do with each type of media** in the AutoPlay Control Panel, AutoPlay will examine a volume connected to the PC to determine the type of content on the disk.</span></span> <span data-ttu-id="a3445-353">Wenn Bilder gefunden werden, wird **ShowPicturesOnArrival** ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="a3445-353">When pictures are found, **ShowPicturesOnArrival** is raised.</span></span> |
| <span data-ttu-id="a3445-354">Empfangen von Fotos mit Näherungsfreigabe (Koppeln und Senden)</span><span class="sxs-lookup"><span data-stu-id="a3445-354">Receiving photos with Proximity Sharing (tap and send)</span></span>             | **<span data-ttu-id="a3445-355">ShowPicturesOnArrival</span><span class="sxs-lookup"><span data-stu-id="a3445-355">ShowPicturesOnArrival</span></span>**          | <span data-ttu-id="a3445-356">Wenn Benutzer Inhalt mit Näherung (Koppeln und Senden) senden, prüft die automatische Wiedergabe die freigegebenen Dateien auf den Inhaltstyp.</span><span class="sxs-lookup"><span data-stu-id="a3445-356">When users send content with using proximity (tap and send), AutoPlay will examine the shared files to determine the type of content.</span></span> <span data-ttu-id="a3445-357">Wenn Bilder gefunden werden, wird **ShowPicturesOnArrival** ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="a3445-357">If pictures are found, **ShowPicturesOnArrival** is raised.</span></span> |
| <span data-ttu-id="a3445-358">Abspielen von Musik von einem Massenspeicher (Legacy)</span><span class="sxs-lookup"><span data-stu-id="a3445-358">Using music from mass storage (legacy)</span></span>                             | **<span data-ttu-id="a3445-359">PlayMusicFilesOnArrival</span><span class="sxs-lookup"><span data-stu-id="a3445-359">PlayMusicFilesOnArrival</span></span>**        | <span data-ttu-id="a3445-360">Wenn der Benutzer in der Systemsteuerung unter „Automatische Wiedergabe“ die Option **Gewünschte Aktion für jeden Medientyp auswählen** aktiviert hat, überprüft die automatische Wiedergabe das am PC angeschlossene Volume, um den Inhaltstyp auf dem Datenträger zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="a3445-360">If a user has enabled **Choose what to do with each type of media** in the AutoPlay Control Panel, AutoPlay will examine a volume connected to the PC to determine the type of content on the disk.</span></span>  <span data-ttu-id="a3445-361">Wenn Musikdateien gefunden werden, wird **PlayMusicFilesOnArrival** ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="a3445-361">When music files are found, **PlayMusicFilesOnArrival** is raised.</span></span> |
| <span data-ttu-id="a3445-362">Empfangen von Musik mit Näherungsfreigabe (Koppeln und Senden)</span><span class="sxs-lookup"><span data-stu-id="a3445-362">Receiving music with Proximity Sharing (tap and send)</span></span>              | **<span data-ttu-id="a3445-363">PlayMusicFilesOnArrival</span><span class="sxs-lookup"><span data-stu-id="a3445-363">PlayMusicFilesOnArrival</span></span>**        | <span data-ttu-id="a3445-364">Wenn Benutzer Inhalt mit Näherung (Koppeln und Senden) senden, prüft die automatische Wiedergabe die freigegebenen Dateien auf den Inhaltstyp.</span><span class="sxs-lookup"><span data-stu-id="a3445-364">When users send content with using proximity (tap and send), AutoPlay will examine the shared files to determine the type of content.</span></span> <span data-ttu-id="a3445-365">Wenn Musikdateien gefunden werden, wird **PlayMusicFilesOnArrival** ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="a3445-365">If music files are found, **PlayMusicFilesOnArrival** is raised.</span></span> |
| <span data-ttu-id="a3445-366">Abspielen von Videos von einem Massenspeicher (Legacy)</span><span class="sxs-lookup"><span data-stu-id="a3445-366">Using videos from mass storage (legacy)</span></span>                            | **<span data-ttu-id="a3445-367">PlayVideoFilesOnArrival</span><span class="sxs-lookup"><span data-stu-id="a3445-367">PlayVideoFilesOnArrival</span></span>**        | <span data-ttu-id="a3445-368">Wenn der Benutzer in der Systemsteuerung unter „Automatische Wiedergabe“ die Option **Gewünschte Aktion für jeden Medientyp auswählen** aktiviert hat, überprüft die automatische Wiedergabe das am PC angeschlossene Volume, um den Inhaltstyp auf dem Datenträger zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="a3445-368">If a user has enabled **Choose what to do with each type of media** in the AutoPlay Control Panel, AutoPlay will examine a volume connected to the PC to determine the type of content on the disk.</span></span> <span data-ttu-id="a3445-369">Wenn Videodateien gefunden werden, wird **PlayVideoFilesOnArrival** ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="a3445-369">When video files are found, **PlayVideoFilesOnArrival** is raised.</span></span> |
| <span data-ttu-id="a3445-370">Empfangen von Videos mit Näherungsfreigabe (Koppeln und Senden)</span><span class="sxs-lookup"><span data-stu-id="a3445-370">Receiving videos with Proximity Sharing (tap and send)</span></span>             | **<span data-ttu-id="a3445-371">PlayVideoFilesOnArrival</span><span class="sxs-lookup"><span data-stu-id="a3445-371">PlayVideoFilesOnArrival</span></span>**        | <span data-ttu-id="a3445-372">Wenn Benutzer Inhalt mit Näherung (Koppeln und Senden) senden, prüft die automatische Wiedergabe die freigegebenen Dateien auf den Inhaltstyp.</span><span class="sxs-lookup"><span data-stu-id="a3445-372">When users send content with using proximity (tap and send), AutoPlay will examine the shared files to determine the type of content.</span></span> <span data-ttu-id="a3445-373">Wenn Videodateien gefunden werden, wird **PlayVideoFilesOnArrival** ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="a3445-373">If video files are found, **PlayVideoFilesOnArrival** is raised.</span></span> |
| <span data-ttu-id="a3445-374">Verarbeitung von gemischten Dateigruppen von einem verbundenen Gerät aus</span><span class="sxs-lookup"><span data-stu-id="a3445-374">Handling mixed sets of files from a connected device</span></span>               | **<span data-ttu-id="a3445-375">MixedContentOnArrival</span><span class="sxs-lookup"><span data-stu-id="a3445-375">MixedContentOnArrival</span></span>**          | <span data-ttu-id="a3445-376">Wenn der Benutzer in der Systemsteuerung unter „Automatische Wiedergabe“ die Option **Gewünschte Aktion für jeden Medientyp auswählen** aktiviert hat, überprüft die automatische Wiedergabe das am PC angeschlossene Volume, um den Inhaltstyp auf dem Datenträger zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="a3445-376">If a user has enabled **Choose what to do with each type of media** in the AutoPlay Control Panel, AutoPlay will examine a volume connected to the PC to determine the type of content on the disk.</span></span> <span data-ttu-id="a3445-377">Wenn kein bestimmter Inhaltstyp gefunden wird (z. B. Bilder), wird **MixedContentOnArrival** ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="a3445-377">If no specific content type is found (for example, pictures), **MixedContentOnArrival** is raised.</span></span> |
| <span data-ttu-id="a3445-378">Verarbeitung von gemischten Dateigruppen mit Näherungsfreigabe (Koppeln und Senden)</span><span class="sxs-lookup"><span data-stu-id="a3445-378">Handling mixed sets of files with Proximity Sharing (tap and send)</span></span> | **<span data-ttu-id="a3445-379">MixedContentOnArrival</span><span class="sxs-lookup"><span data-stu-id="a3445-379">MixedContentOnArrival</span></span>**          | <span data-ttu-id="a3445-380">Wenn Benutzer Inhalt mit Näherung (Koppeln und Senden) senden, prüft die automatische Wiedergabe die freigegebenen Dateien auf den Inhaltstyp.</span><span class="sxs-lookup"><span data-stu-id="a3445-380">When users send content with using proximity (tap and send), AutoPlay will examine the shared files to determine the type of content.</span></span> <span data-ttu-id="a3445-381">Wenn kein bestimmter Inhaltstyp gefunden wird (z. B. Bilder), wird **MixedContentOnArrival** ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="a3445-381">If no specific content type is found (for example, pictures), **MixedContentOnArrival** is raised.</span></span> |
| <span data-ttu-id="a3445-382">Verarbeitung von Videos von optischen Medien</span><span class="sxs-lookup"><span data-stu-id="a3445-382">Handle video from optical media</span></span>                                    | **<span data-ttu-id="a3445-383">PlayDVDMovieOnArrival</span><span class="sxs-lookup"><span data-stu-id="a3445-383">PlayDVDMovieOnArrival</span></span>**<br />**<span data-ttu-id="a3445-384">PlayBluRayOnArrival</span><span class="sxs-lookup"><span data-stu-id="a3445-384">PlayBluRayOnArrival</span></span>**<br />**<span data-ttu-id="a3445-385">PlayVideoCDMovieOnArrival</span><span class="sxs-lookup"><span data-stu-id="a3445-385">PlayVideoCDMovieOnArrival</span></span>**<br />**<span data-ttu-id="a3445-386">PlaySuperVideoCDMovieOnArrival</span><span class="sxs-lookup"><span data-stu-id="a3445-386">PlaySuperVideoCDMovieOnArrival</span></span>** | <span data-ttu-id="a3445-387">Wenn ein Datenträger in das optische Laufwerk eingelegt wird, prüft die automatische Wiedergabe die Dateien, um den Inhaltstyp zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="a3445-387">When a disk is inserted into the optical drive, AutoPlay will examine the files to determine the type of content.</span></span> <span data-ttu-id="a3445-388">Wenn eine Videodateien gefunden wurde, wird das Ereignis entsprechend dem Typ des optischen Datenträgers ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="a3445-388">When video files are found, the event corresponding to the type of optical disk is raised.</span></span> |
| <span data-ttu-id="a3445-389">Verarbeitung von Musik von optischen Medien</span><span class="sxs-lookup"><span data-stu-id="a3445-389">Handle music from optical media</span></span>                                    | **<span data-ttu-id="a3445-390">PlayCDAudioOnArrival</span><span class="sxs-lookup"><span data-stu-id="a3445-390">PlayCDAudioOnArrival</span></span>**<br />**<span data-ttu-id="a3445-391">PlayDVDAudioOnArrival</span><span class="sxs-lookup"><span data-stu-id="a3445-391">PlayDVDAudioOnArrival</span></span>** | <span data-ttu-id="a3445-392">Wenn ein Datenträger in das optische Laufwerk eingelegt wird, prüft die automatische Wiedergabe die Dateien, um den Inhaltstyp zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="a3445-392">When a disk is inserted into the optical drive, AutoPlay will examine the files to determine the type of content.</span></span> <span data-ttu-id="a3445-393">Wenn eine Musikdateien gefunden wurde, wird das Ereignis entsprechend dem Typ des optischen Datenträgers ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="a3445-393">When music files are found, the event corresponding to the type of optical disk is raised.</span></span> |
| <span data-ttu-id="a3445-394">Abspielen erweiterter Datenträger</span><span class="sxs-lookup"><span data-stu-id="a3445-394">Play enhanced disks</span></span>                                                | **<span data-ttu-id="a3445-395">PlayEnhancedCDOnArrival</span><span class="sxs-lookup"><span data-stu-id="a3445-395">PlayEnhancedCDOnArrival</span></span>**<br />**<span data-ttu-id="a3445-396">PlayEnhancedDVDOnArrival</span><span class="sxs-lookup"><span data-stu-id="a3445-396">PlayEnhancedDVDOnArrival</span></span>** | <span data-ttu-id="a3445-397">Wenn ein Datenträger in das optische Laufwerk eingelegt wird, prüft die automatische Wiedergabe die Dateien, um den Inhaltstyp zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="a3445-397">When a disk is inserted into the optical drive, AutoPlay will examine the files to determine the type of content.</span></span> <span data-ttu-id="a3445-398">Wenn ein erweiterter Datenträger gefunden wurde, wird das Ereignis entsprechend dem Typ des optischen Datenträgers ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="a3445-398">When an enhanced disk is found, the event corresponding to the type of optical disk is raised.</span></span> |
| <span data-ttu-id="a3445-399">Verarbeitung von beschreibbaren optischen Datenträgern</span><span class="sxs-lookup"><span data-stu-id="a3445-399">Handle writeable optical disks</span></span>                                     | **<span data-ttu-id="a3445-400">HandleCDBurningOnArrival</span><span class="sxs-lookup"><span data-stu-id="a3445-400">HandleCDBurningOnArrival</span></span>** <br />**<span data-ttu-id="a3445-401">HandleDVDBurningOnArrival</span><span class="sxs-lookup"><span data-stu-id="a3445-401">HandleDVDBurningOnArrival</span></span>** <br />**<span data-ttu-id="a3445-402">HandleBDBurningOnArrival</span><span class="sxs-lookup"><span data-stu-id="a3445-402">HandleBDBurningOnArrival</span></span>** | <span data-ttu-id="a3445-403">Wenn ein Datenträger in das optische Laufwerk eingelegt wird, prüft die automatische Wiedergabe die Dateien, um den Inhaltstyp zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="a3445-403">When a disk is inserted into the optical drive, AutoPlay will examine the files to determine the type of content.</span></span> <span data-ttu-id="a3445-404">Wenn ein Datenträger mit Schreibzugriff gefunden wurde, wird das Ereignis entsprechend dem Typ des optischen Datenträgers ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="a3445-404">When a writable disk is found, the event corresponding to the type of optical disk is raised.</span></span> |
| <span data-ttu-id="a3445-405">Verarbeitung von anderen Geräte- oder Volumeverbindungen</span><span class="sxs-lookup"><span data-stu-id="a3445-405">Handle any other device or volume connection</span></span>                       | **<span data-ttu-id="a3445-406">UnknownContentOnArrival</span><span class="sxs-lookup"><span data-stu-id="a3445-406">UnknownContentOnArrival</span></span>**        | <span data-ttu-id="a3445-407">Ausgelöst für alle Ereignisse, wenn Inhalt gefunden wurde, der mit einem der Inhaltsereignisse für die automatische Wiedergabe übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="a3445-407">Raised for all events in case content is found that does not match any of the AutoPlay content events.</span></span> <span data-ttu-id="a3445-408">Es wird nicht empfohlen, dieses Ereignis zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="a3445-408">Use of this event is not recommended.</span></span> <span data-ttu-id="a3445-409">Sie sollten Ihre Anwendung nur für bestimmte Ereignisse für die automatische Wiedergabe registrieren, die sie auch verarbeiten kann.</span><span class="sxs-lookup"><span data-stu-id="a3445-409">You should only register your application for the specific AutoPlay events that it can handle.</span></span> |

<span data-ttu-id="a3445-410">Mit dem Eintrag **CustomEvent** in der Datei „autorun.inf“ können Sie angeben, dass von der automatischen Wiedergabe ein benutzerdefiniertes Inhaltsereignis für die automatische Wiedergabe ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="a3445-410">You can specify that AutoPlay raise a custom AutoPlay Content event using the **CustomEvent** entry in the autorun.inf file for a volume.</span></span> <span data-ttu-id="a3445-411">Weitere Informationen finden Sie unter [Autorun.inf-Einträge](https://msdn.microsoft.com/library/windows/desktop/cc144200).</span><span class="sxs-lookup"><span data-stu-id="a3445-411">For more info, see [Autorun.inf entries](https://msdn.microsoft.com/library/windows/desktop/cc144200).</span></span>

<span data-ttu-id="a3445-412">Sie können Ihre App als Ereignishandler für Inhalte oder Geräte zur automatischen Wiedergabe registrieren, indem Sie der Datei „package.appxmanifest“ eine Erweiterung für die App hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="a3445-412">You can register your app as an AutoPlay Content or AutoPlay Device event handler by adding an extension to the package.appxmanifest file for your app.</span></span> <span data-ttu-id="a3445-413">Wenn Sie Visual Studio verwenden, können Sie auf der Registerkarte **Deklarationen** eine Deklaration vom Typ **Inhalt automatisch wiedergeben** oder **Gerät automatisch wiedergeben** hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="a3445-413">If you are using Visual Studio, you can add an **AutoPlay Content** or **AutoPlay Device** declaration in the **Declarations** tab.</span></span> <span data-ttu-id="a3445-414">Wenn Sie die Datei „package.appxmanifest“ für die App direkt bearbeiten, fügen Sie dem Paketmanifest ein [**Extension**](https://msdn.microsoft.com/library/windows/apps/br211400)-Element hinzu, das als **Category** entweder **windows.autoPlayContent** oder **windows.autoPlayDevice** festlegt.</span><span class="sxs-lookup"><span data-stu-id="a3445-414">If you are editing the package.appxmanifest file for your app directly, add an [**Extension**](https://msdn.microsoft.com/library/windows/apps/br211400) element to your package manifest that specifies either **windows.autoPlayContent** or **windows.autoPlayDevice** as the **Category**.</span></span> <span data-ttu-id="a3445-415">So wird beispielsweise durch den folgenden Eintrag im Paketmanifest eine Erweiterung für **Inhalt automatisch wiedergeben** hinzugefügt, um die App als Handler für das **ShowPicturesOnArrival**-Ereignis zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="a3445-415">For example, the following entry in the package manifest adds an **AutoPlay Content** extension to register the app as a handler for the **ShowPicturesOnArrival** event.</span></span>

```xml
  <Applications>
    <Application Id="AutoPlayHandlerSample.App">
      <Extensions>
        <Extension Category="windows.autoPlayContent">
          <AutoPlayContent>
            <LaunchAction Verb="show" ActionDisplayName="Show Pictures"
                          ContentEvent="ShowPicturesOnArrival" />
          </AutoPlayContent>
        </Extension>
      </Extensions>
    </Application>
  </Applications>
```

 

 
