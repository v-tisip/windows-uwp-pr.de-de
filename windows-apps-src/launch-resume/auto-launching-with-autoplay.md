---
author: TylerMSFT
title: Automatischer Start mit automatischer Wiedergabe
description: Sie können die automatische Wiedergabe verwenden, um Ihre App als Option bereitzustellen, wenn ein Benutzer ein Gerät an seinen PC anschließt. Hierzu zählen Nicht-Volumegeräte wie Kameras oder Media Player und Volumegeräte wie USB-Sticks, SD-Karten oder DVDs.
ms.assetid: AD4439EA-00B0-4543-887F-2C1D47408EA7
ms.author: twhitney
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 98c537ef3b2a5d002644cc554eae72b89a1799b0
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5558868"
---
# <a name="span-iddevlaunchresumeauto-launchingwithautoplayspanauto-launching-with-autoplay"></a><span data-ttu-id="18ff4-105"><span id="dev_launch_resume.auto-launching_with_autoplay"></span>Automatisches Starten mit automatischer Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="18ff4-105"><span id="dev_launch_resume.auto-launching_with_autoplay"></span>Auto-launching with AutoPlay</span></span>

<span data-ttu-id="18ff4-106">Sie können die **automatische Wiedergabe** verwenden, um Ihre App als Option bereitzustellen, wenn ein Benutzer ein Gerät an seinen PC anschließt.</span><span class="sxs-lookup"><span data-stu-id="18ff4-106">You can use **AutoPlay** to provide your app as an option when a user connects a device to their PC.</span></span> <span data-ttu-id="18ff4-107">Hierzu zählen Nicht-Volumegeräte wie Kameras oder Media Player und Volumegeräte wie USB-Sticks, SD-Karten oder DVDs.</span><span class="sxs-lookup"><span data-stu-id="18ff4-107">This includes non-volume devices such as a camera or media player, or volume devices such as a USB thumb drive, SD card, or DVD.</span></span> <span data-ttu-id="18ff4-108">Die **automatische Wiedergabe** bietet Ihnen auch die Möglichkeit, Ihre App als Option anzubieten, wenn Benutzer mithilfe von Näherung (Kopplung) Dateien zwischen zwei PCs freigeben.</span><span class="sxs-lookup"><span data-stu-id="18ff4-108">You can also use **AutoPlay** to offer your app as an option when users share files between two PCs by using proximity (tapping).</span></span>

> <span data-ttu-id="18ff4-109">**Hinweis:** Wenn Sie ein Gerätehersteller sind und Sie Ihre [Microsoft Store-Geräte-app](http://go.microsoft.com/fwlink/p/?LinkID=301381) als Handler für das Gerät **automatisch wiedergeben** zuordnen möchten, können Sie diese app in den Gerätemetadaten identifizieren.</span><span class="sxs-lookup"><span data-stu-id="18ff4-109">**Note**If you are a device manufacturer and you want to associate your [Microsoft Store device app](http://go.microsoft.com/fwlink/p/?LinkID=301381) as an **AutoPlay** handler for your device, you can identify that app in the device metadata.</span></span> <span data-ttu-id="18ff4-110">Weitere Informationen finden Sie im Thema [Automatische Wiedergabe für MicrosoftStore-Geräte-Apps](http://go.microsoft.com/fwlink/p/?LinkId=306684).</span><span class="sxs-lookup"><span data-stu-id="18ff4-110">For more info, see [AutoPlay for Microsoft Store device apps](http://go.microsoft.com/fwlink/p/?LinkId=306684).</span></span>

## <a name="register-for-autoplay-content"></a><span data-ttu-id="18ff4-111">Registrieren für Inhalt für die automatische Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="18ff4-111">Register for AutoPlay content</span></span>

<span data-ttu-id="18ff4-112">Sie können Apps als Optionen für Inhaltsereignisse für die **automatische Wiedergabe** registrieren.</span><span class="sxs-lookup"><span data-stu-id="18ff4-112">You can register apps as options for **AutoPlay** content events.</span></span> <span data-ttu-id="18ff4-113">Inhaltsereignisse der **automatischen Wiedergabe** werden ausgelöst, wenn ein Volumegerät wie etwa die Speicherkarte einer Kamera, eine DVD oder ein USB-Stick in den PC eingelegt bzw. daran angeschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="18ff4-113">**AutoPlay** content events are raised when a volume device such as a camera memory card, thumb drive, or DVD is inserted into the PC.</span></span> <span data-ttu-id="18ff4-114">Dieses Beispiel zeigt, wie Sie eine App als Option für die **automatische Wiedergabe** identifizieren, wenn ein Volumegerät einer Kamera angeschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="18ff4-114">Here we show how to identify your app as an **AutoPlay** option when a volume device from a camera is inserted.</span></span>

<span data-ttu-id="18ff4-115">In diesem Lernprogramm haben Sie eine App erstellt, die Bilddateien anzeigt oder in „Bilder“ kopiert.</span><span class="sxs-lookup"><span data-stu-id="18ff4-115">In this tutorial, you created an app that displays image files or copies them to Pictures.</span></span> <span data-ttu-id="18ff4-116">Sie haben die App für das Inhaltsereignis **ShowPicturesOnArrival** der automatischen Wiedergabe registriert.</span><span class="sxs-lookup"><span data-stu-id="18ff4-116">You registered the app for the AutoPlay **ShowPicturesOnArrival** content event.</span></span>

<span data-ttu-id="18ff4-117">Die automatische Wiedergabe löst außerdem Inhaltsereignisse für Inhalte aus, die mittels Näherung (Koppeln) zwischen PCs freigegeben werden.</span><span class="sxs-lookup"><span data-stu-id="18ff4-117">AutoPlay also raises content events for content shared between PCs using proximity (tapping).</span></span> <span data-ttu-id="18ff4-118">Sie können die Schritte und den Code aus diesem Abschnitt auch für Dateien verwenden, die mittels Näherung zwischen PCs freigegeben werden.</span><span class="sxs-lookup"><span data-stu-id="18ff4-118">You can use the steps and code in this section to handle files that are shared between PCs that use proximity.</span></span> <span data-ttu-id="18ff4-119">Die folgende Tabelle enthält die Inhaltsereignisse für die automatische Wiedergabe, die Sie verwenden können, um Inhalte mithilfe der Näherungsfunktion zu teilen.</span><span class="sxs-lookup"><span data-stu-id="18ff4-119">The following table lists the AutoPlay content events that are available for sharing content by using proximity.</span></span>

| <span data-ttu-id="18ff4-120">Aktion</span><span class="sxs-lookup"><span data-stu-id="18ff4-120">Action</span></span>         | <span data-ttu-id="18ff4-121">Inhaltsereignis für die automatische Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="18ff4-121">AutoPlay content event</span></span>  |
|----------------|-------------------------|
| <span data-ttu-id="18ff4-122">Teilen von Musik</span><span class="sxs-lookup"><span data-stu-id="18ff4-122">Sharing music</span></span>  | <span data-ttu-id="18ff4-123">PlayMusicFilesOnArrival</span><span class="sxs-lookup"><span data-stu-id="18ff4-123">PlayMusicFilesOnArrival</span></span> |
| <span data-ttu-id="18ff4-124">Teilen von Videos</span><span class="sxs-lookup"><span data-stu-id="18ff4-124">Sharing videos</span></span> | <span data-ttu-id="18ff4-125">PlayVideoFilesOnArrival</span><span class="sxs-lookup"><span data-stu-id="18ff4-125">PlayVideoFilesOnArrival</span></span> |

 
<span data-ttu-id="18ff4-126">Wenn Dateien mithilfe der Näherungsfunktion freigegeben werden, enthält die **Files**-Eigenschaft des **FileActivatedEventArgs**-Objekts einen Verweis auf einen Stammordner mit allen freigegebenen Dateien.</span><span class="sxs-lookup"><span data-stu-id="18ff4-126">When files are shared by using proximity, the **Files** property of the **FileActivatedEventArgs** object contains a reference to a root folder that contains all of the shared files.</span></span>

### <a name="step-1-create-a-new-project-and-add-autoplay-declarations"></a><span data-ttu-id="18ff4-127">Schritt 1: Erstellen eines neuen Projekts und Hinzufügen von Deklarationen für die automatische Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="18ff4-127">Step 1: Create a new project and add AutoPlay declarations</span></span>

1.  <span data-ttu-id="18ff4-128">Öffnen Sie Microsoft Visual Studio, und wählen Sie **Neues Projekt** im Menü **Datei** aus.</span><span class="sxs-lookup"><span data-stu-id="18ff4-128">Open Microsoft Visual Studio and select **New Project** from the **File** menu.</span></span> <span data-ttu-id="18ff4-129">Wählen Sie im Abschnitt **VisualC#** unter **Windows** die Option **Leere App (Universelle Windows-App)** aus.</span><span class="sxs-lookup"><span data-stu-id="18ff4-129">In the **Visual C#** section, under **Windows**, select **Blank App (Universal Windows)**.</span></span> <span data-ttu-id="18ff4-130">Nennen Sie die App **AutoPlayDisplayOrCopyImages**, und klicken Sie auf **OK.**</span><span class="sxs-lookup"><span data-stu-id="18ff4-130">Name the app **AutoPlayDisplayOrCopyImages** and click **OK.**</span></span>
2.  <span data-ttu-id="18ff4-131">Öffnen Sie die Datei „Package.appxmanifest”, und wählen Sie die Registerkarte **Funktionen** aus. Wählen Sie dann die Funktionen **Wechselmedien** und **Bildbibliothek** aus.</span><span class="sxs-lookup"><span data-stu-id="18ff4-131">Open the Package.appxmanifest file and select the **Capabilities** tab. Select the **Removable Storage** and **Pictures Library** capabilities.</span></span> <span data-ttu-id="18ff4-132">Dadurch erhält die App Zugriff auf Wechselmedien für Kameraspeicher und lokale Bilder.</span><span class="sxs-lookup"><span data-stu-id="18ff4-132">This gives the app access to removable storage devices for camera memory, and access to local pictures.</span></span>
3.  <span data-ttu-id="18ff4-133">Wählen Sie in der Manifestdatei die Registerkarte **Deklarationen** und dann in der Dropdownliste **Verfügbare Deklarationen** die Option **Inhalt automatisch wiedergeben** aus. Klicken Sie dann auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="18ff4-133">In the manifest file, select the **Declarations** tab. In the **Available Declarations** drop-down list, select **AutoPlay Content** and click **Add**.</span></span> <span data-ttu-id="18ff4-134">Wählen Sie das neue Element vom Typ **Inhalt automatisch wiedergeben** aus, das der Liste **Unterstützte Deklarationen** hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="18ff4-134">Select the new **AutoPlay Content** item that was added to the **Supported Declarations** list.</span></span>
4.  <span data-ttu-id="18ff4-135">Eine Deklaration vom Typ **Inhalt automatisch wiedergeben** identifiziert Ihre App als Option, wenn die automatische Wiedergabe ein Inhaltsereignis auslöst.</span><span class="sxs-lookup"><span data-stu-id="18ff4-135">An **AutoPlay Content** declaration identifies your app as an option when AutoPlay raises a content event.</span></span> <span data-ttu-id="18ff4-136">Das Ereignis basiert auf dem Inhalt eines Volumegeräts (beispielsweise eine DVD oder ein Speicherstick).</span><span class="sxs-lookup"><span data-stu-id="18ff4-136">The event is based on the content of a volume device such as a DVD or a thumb drive.</span></span> <span data-ttu-id="18ff4-137">Für die automatische Wiedergabe wird der Inhalt des Volumegeräts ermittelt und festgelegt, welches Inhaltsereignis ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="18ff4-137">AutoPlay examines the content of the volume device and determines which content event to raise.</span></span> <span data-ttu-id="18ff4-138">Die automatische Wiedergabe löst das **ShowPicturesOnArrival**-Ereignis aus, wenn das Stammverzeichnis des Volumes den Ordner „DCIM“, „AVCHD“ oder „PRIVATE\\ACHD“ enthält oder wenn der Benutzer in der Systemsteuerung unter „Automatische Wiedergabe“ die Option **Gewünschte Aktion für jeden Medientyp auswählen** aktiviert hat und Bilder im Stammverzeichnis des Volumes gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="18ff4-138">If the root of the volume contains a DCIM, AVCHD, or PRIVATE\\ACHD folder, or if a user has enabled **Choose what to do with each type of media** in the AutoPlay Control Panel and pictures are found in the root of the volume, then AutoPlay raises the **ShowPicturesOnArrival** event.</span></span> <span data-ttu-id="18ff4-139">Geben Sie im Abschnitt **Startaktionen** die Werte aus der nachfolgenden Tabelle1 für die Aktion beim ersten Start an.</span><span class="sxs-lookup"><span data-stu-id="18ff4-139">In the **Launch Actions** section, enter the values from Table 1 below for the first launch action.</span></span>
5.  <span data-ttu-id="18ff4-140">Klicken Sie im Abschnitt **Startaktionen** für das Element vom Typ **Inhalt automatisch wiedergeben** auf **Neu hinzufügen**, um eine zweite Startaktion hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="18ff4-140">In the **Launch Actions** section for the **AutoPlay Content** item, click **Add New** to add a second launch action.</span></span> <span data-ttu-id="18ff4-141">Geben Sie die Werte aus der nachfolgenden Tabelle2 für die Aktion beim zweiten Start an:</span><span class="sxs-lookup"><span data-stu-id="18ff4-141">Enter the values in Table 2 below for the second launch action.</span></span>
6.  <span data-ttu-id="18ff4-142">Wählen Sie in der Dropdownliste **Verfügbare Deklarationen** die Option **Dateitypzuordnungen** aus, und klicken Sie anschließend auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="18ff4-142">In the **Available Declarations** drop-down list, select **File Type Associations** and click **Add**.</span></span> <span data-ttu-id="18ff4-143">Setzen Sie in den Eigenschaften der neuen Deklaration vom Typ **Dateitypzuordnungen** das Feld **Anzeigename** auf **AutoPlay Copy or Show Images** und das Feld **Name** auf **image\_association1**.</span><span class="sxs-lookup"><span data-stu-id="18ff4-143">In the Properties of the new **File Type Associations** declaration, set the **Display Name** field to **AutoPlay Copy or Show Images** and the **Name** field to **image\_association1**.</span></span> <span data-ttu-id="18ff4-144">Klicken Sie im Abschnitt **Unterstützte Dateitypen** auf **Neu hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="18ff4-144">In the **Supported File Types** section, click **Add New**.</span></span> <span data-ttu-id="18ff4-145">Legen Sie im Feld **Dateityp** die Option **.jpg** fest.</span><span class="sxs-lookup"><span data-stu-id="18ff4-145">Set the **File Type** field to **.jpg**.</span></span> <span data-ttu-id="18ff4-146">Legen Sie im Abschnitt **Unterstützte Dateitypen** das Feld **Dateityp** der neuen Dateizuordnung auf **.png** fest.</span><span class="sxs-lookup"><span data-stu-id="18ff4-146">In the **Supported File Types** section, set the **File Type** field of the new file association to **.png**.</span></span> <span data-ttu-id="18ff4-147">Für Inhaltsereignisse filtert die automatische Wiedergabe alle Dateitypen heraus, die nicht explizit Ihrer App zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="18ff4-147">For content events, AutoPlay filters out any file types that are not explicitly associated with your app.</span></span>
7.  <span data-ttu-id="18ff4-148">Speichern und schließen Sie die Manifestdatei.</span><span class="sxs-lookup"><span data-stu-id="18ff4-148">Save and close the manifest file.</span></span>

**<span data-ttu-id="18ff4-149">Tabelle1</span><span class="sxs-lookup"><span data-stu-id="18ff4-149">Table 1</span></span>**

| <span data-ttu-id="18ff4-150">Einstellung</span><span class="sxs-lookup"><span data-stu-id="18ff4-150">Setting</span></span>             | <span data-ttu-id="18ff4-151">Wert</span><span class="sxs-lookup"><span data-stu-id="18ff4-151">Value</span></span>                 |
|---------------------|-----------------------|
| <span data-ttu-id="18ff4-152">Verb</span><span class="sxs-lookup"><span data-stu-id="18ff4-152">Verb</span></span>                | <span data-ttu-id="18ff4-153">show</span><span class="sxs-lookup"><span data-stu-id="18ff4-153">show</span></span>                  |
| <span data-ttu-id="18ff4-154">Aktionsanzeigename</span><span class="sxs-lookup"><span data-stu-id="18ff4-154">Action Display Name</span></span> | <span data-ttu-id="18ff4-155">Bilder anzeigen</span><span class="sxs-lookup"><span data-stu-id="18ff4-155">Show Pictures</span></span>         |
| <span data-ttu-id="18ff4-156">Inhaltsereignis</span><span class="sxs-lookup"><span data-stu-id="18ff4-156">Content Event</span></span>       | <span data-ttu-id="18ff4-157">ShowPicturesOnArrival</span><span class="sxs-lookup"><span data-stu-id="18ff4-157">ShowPicturesOnArrival</span></span> |

<span data-ttu-id="18ff4-158">Die Einstellung **Aktionsanzeigename** gibt die Zeichenfolge an, die bei der automatischen Wiedergabe für Ihre App angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="18ff4-158">The **Action Display Name** setting identifies the string that AutoPlay displays for your app.</span></span> <span data-ttu-id="18ff4-159">Die Einstellung **Verb** dient zum Angeben eines Werts, der für die ausgewählte Option an Ihre App übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="18ff4-159">The **Verb** setting identifies a value that is passed to your app for the selected option.</span></span> <span data-ttu-id="18ff4-160">Sie können mehrere Startaktionen für Ereignisse der automatischen Wiedergabe angeben und mit der Einstellung **Verb** ermitteln, welche Option ein Benutzer für Ihre App ausgewählt hat.</span><span class="sxs-lookup"><span data-stu-id="18ff4-160">You can specify multiple launch actions for an AutoPlay event and use the **Verb** setting to determine which option a user has selected for your app.</span></span> <span data-ttu-id="18ff4-161">Für welche Option sich der Benutzer entschieden hat, erfahren Sie durch Überprüfen der **verb**-Eigenschaft der an die App übergebenen Startereignisargumente.</span><span class="sxs-lookup"><span data-stu-id="18ff4-161">You can tell which option the user selected by checking the **verb** property of the startup event arguments passed to your app.</span></span> <span data-ttu-id="18ff4-162">Für die Einstellung **Verb** können Sie einen beliebigen Wert verwenden. Einzige Ausnahme ist **open**: Dieser Wert ist reserviert.</span><span class="sxs-lookup"><span data-stu-id="18ff4-162">You can use any value for the **Verb** setting except, **open**, which is reserved.</span></span>

**<span data-ttu-id="18ff4-163">Tabelle2</span><span class="sxs-lookup"><span data-stu-id="18ff4-163">Table 2</span></span>**  

| <span data-ttu-id="18ff4-164">Einstellung</span><span class="sxs-lookup"><span data-stu-id="18ff4-164">Setting</span></span>             | <span data-ttu-id="18ff4-165">Wert</span><span class="sxs-lookup"><span data-stu-id="18ff4-165">Value</span></span>                      |
|--------------------:|----------------------------|
| <span data-ttu-id="18ff4-166">Verb</span><span class="sxs-lookup"><span data-stu-id="18ff4-166">Verb</span></span>                | <span data-ttu-id="18ff4-167">copy</span><span class="sxs-lookup"><span data-stu-id="18ff4-167">copy</span></span>                       |
| <span data-ttu-id="18ff4-168">Aktionsanzeigename</span><span class="sxs-lookup"><span data-stu-id="18ff4-168">Action Display Name</span></span> | <span data-ttu-id="18ff4-169">Bilder in die Bibliothek kopieren</span><span class="sxs-lookup"><span data-stu-id="18ff4-169">Copy Pictures Into Library</span></span> |
| <span data-ttu-id="18ff4-170">Inhaltsereignis</span><span class="sxs-lookup"><span data-stu-id="18ff4-170">Content Event</span></span>       | <span data-ttu-id="18ff4-171">ShowPicturesOnArrival</span><span class="sxs-lookup"><span data-stu-id="18ff4-171">ShowPicturesOnArrival</span></span>      |

### <a name="step-2-add-xaml-ui"></a><span data-ttu-id="18ff4-172">Schritt 2: Hinzufügen von XAML-UI</span><span class="sxs-lookup"><span data-stu-id="18ff4-172">Step 2: Add XAML UI</span></span>

<span data-ttu-id="18ff4-173">Öffnen Sie die Datei „MainPage.xaml“, und fügen Sie dem Standardabschnitt &lt;Grid&gt; folgenden XAML-Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="18ff4-173">Open the MainPage.xaml file and add the following XAML to the default &lt;Grid&gt; section.</span></span>

```xml
<TextBlock FontSize="18">File List</TextBlock>
<TextBlock x:Name="FilesBlock" HorizontalAlignment="Left" TextWrapping="Wrap"
           VerticalAlignment="Top" Margin="0,20,0,0" Height="280" Width="240" />
<Canvas x:Name="FilesCanvas" HorizontalAlignment="Left" VerticalAlignment="Top"
        Margin="260,20,0,0" Height="280" Width="100"/>
```

### <a name="step-3-add-initialization-code"></a><span data-ttu-id="18ff4-174">Schritt 3: Hinzufügen von Initialisierungscode</span><span class="sxs-lookup"><span data-stu-id="18ff4-174">Step 3: Add initialization code</span></span>

<span data-ttu-id="18ff4-175">Der Code in diesem Schritt überprüft den Verb-Wert in der **Verb**-Eigenschaft. Dabei handelt es sich um eines der Startargumente, die beim **OnFileActivated**-Ereignis an die App übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="18ff4-175">The code in this step checks the verb value in the **Verb** property, which is one of the startup arguments passed to the app during the **OnFileActivated** event.</span></span> <span data-ttu-id="18ff4-176">Anschließend ruft der Code entsprechend der vom Benutzer ausgewählten Option eine Methode auf.</span><span class="sxs-lookup"><span data-stu-id="18ff4-176">The code then calls a method related to the option that the user selected.</span></span> <span data-ttu-id="18ff4-177">Beim Kameraspeicherereignis wird bei der automatischen Wiedergabe der Stammordner des Kameraspeichers an die App übergeben.</span><span class="sxs-lookup"><span data-stu-id="18ff4-177">For the camera memory event, AutoPlay passes the root folder of the camera storage to the app.</span></span> <span data-ttu-id="18ff4-178">Sie können diesen Ordner aus dem ersten Element der **Files**-Eigenschaft abrufen.</span><span class="sxs-lookup"><span data-stu-id="18ff4-178">You can retrieve this folder from the first element of the **Files** property.</span></span>

<span data-ttu-id="18ff4-179">Öffnen Sie die Datei „App.xaml.cs“, und fügen Sie der **App**-Klasse den folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="18ff4-179">Open the App.xaml.cs file and add the following code to the **App** class.</span></span>

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

> <span data-ttu-id="18ff4-180">**Hinweis:** der `DisplayImages` und `CopyImages` Methoden werden in den folgenden Schritten hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="18ff4-180">**Note**The `DisplayImages` and `CopyImages` methods are added in the following steps.</span></span>

### <a name="step-4-add-code-to-display-images"></a><span data-ttu-id="18ff4-181">Schritt 4: Hinzufügen von Code zum Anzeigen von Bildern</span><span class="sxs-lookup"><span data-stu-id="18ff4-181">Step 4: Add code to display images</span></span>

<span data-ttu-id="18ff4-182">Fügen Sie in der Datei „MainPage.xaml.cs“ der **MainPage**-Klasse folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="18ff4-182">In the MainPage.xaml.cs file add the following code to the **MainPage** class.</span></span>

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

### <a name="step-5-add-code-to-copy-images"></a><span data-ttu-id="18ff4-183">Schritt 5: Hinzufügen von Code zum Kopieren von Bildern</span><span class="sxs-lookup"><span data-stu-id="18ff4-183">Step 5: Add code to copy images</span></span>

<span data-ttu-id="18ff4-184">Fügen Sie in der Datei „MainPage.xaml.cs“ der **MainPage**-Klasse folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="18ff4-184">In the MainPage.xaml.cs file add the following code to the **MainPage** class.</span></span>

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

### <a name="step-6-build-and-run-the-app"></a><span data-ttu-id="18ff4-185">Schritt 6: Erstellen und Ausführen der App</span><span class="sxs-lookup"><span data-stu-id="18ff4-185">Step 6: Build and run the app</span></span>

1.  <span data-ttu-id="18ff4-186">Drücken SieF5, um die App zu erstellen und bereitzustellen (im Debugmodus).</span><span class="sxs-lookup"><span data-stu-id="18ff4-186">Press F5 to build and deploy the app (in debug mode).</span></span>
2.  <span data-ttu-id="18ff4-187">Legen Sie eine Kameraspeicherkarte oder ein anderes Speichergerät einer Kamera in Ihren PC ein, um die App auszuführen.</span><span class="sxs-lookup"><span data-stu-id="18ff4-187">To run your app, insert a camera memory card or another storage device from a camera into your PC.</span></span> <span data-ttu-id="18ff4-188">Wählen Sie dann in der Liste mit den Optionen für die automatische Wiedergabe eine der Inhaltsereignisoptionen aus, die Sie in der Datei „package.appxmanifest“ angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="18ff4-188">Then, select one of the content event options that you specified in your package.appxmanifest file from the AutoPlay list of options.</span></span> <span data-ttu-id="18ff4-189">Dieser Beispielcode blendet Bilder im DCIM-Ordner auf der Speicherkarte einer Kamera nur ein oder kopiert diese.</span><span class="sxs-lookup"><span data-stu-id="18ff4-189">This sample code only displays or copies pictures in the DCIM folder of a camera memory card.</span></span> <span data-ttu-id="18ff4-190">Wenn die Speicherkarte Ihrer Kamera Bilder in „AVCHD“ oder „PRIVATE\\ACHD“ speichert, müssen Sie den Code entsprechend ändern.</span><span class="sxs-lookup"><span data-stu-id="18ff4-190">If your camera memory card stores pictures in an AVCHD or PRIVATE\\ACHD folder, you will need to update the code accordingly.</span></span>
    <span data-ttu-id="18ff4-191">**Hinweis:** Wenn Sie keine Kameraspeicherkarte haben, können Sie einen USB-Stick verwenden, wenn er verfügt über einen Ordner mit dem Namen **DCIM** im Stammverzeichnis und der Ordner "DCIM" einen Unterordner hat, die Bilder enthält.</span><span class="sxs-lookup"><span data-stu-id="18ff4-191">**Note**If you don't have a camera memory card, you can use a flash drive if it has a folder named **DCIM** in the root and if the DCIM folder has a subfolder that contains images.</span></span>

## <a name="register-for-an-autoplay-device"></a><span data-ttu-id="18ff4-192">Registrieren für ein Gerät mit automatischer Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="18ff4-192">Register for an AutoPlay device</span></span>


<span data-ttu-id="18ff4-193">Sie können Apps als Optionen für Geräteereignisse der **automatischen Wiedergabe** registrieren.</span><span class="sxs-lookup"><span data-stu-id="18ff4-193">You can register apps as options for **AutoPlay** device events.</span></span> <span data-ttu-id="18ff4-194">Geräteereignisse zur **automatischen Wiedergabe** werden ausgelöst, wenn ein Gerät an einen PC angeschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="18ff4-194">**AutoPlay** device events are raised when a device is connected to a PC.</span></span>

<span data-ttu-id="18ff4-195">Hier wird gezeigt, wie Sie eine App als Option für die **automatische Wiedergabe** identifizieren, wenn eine Kamera an einen PC angeschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="18ff4-195">Here we show how to identify your app as an **AutoPlay** option when a camera is connected to a PC.</span></span> <span data-ttu-id="18ff4-196">Die App wird als Handler für das **WPD\\ImageSourceAutoPlay**-Ereignis registriert.</span><span class="sxs-lookup"><span data-stu-id="18ff4-196">The app registers as a handler for the **WPD\\ImageSourceAutoPlay** event.</span></span> <span data-ttu-id="18ff4-197">Dabei handelt es sich um ein häufiges Ereignis, das vom WPD-System (Windows Portable Device) ausgelöst wird, wenn es von Kameras und anderen Bildverarbeitungsgeräten benachrichtigt wird, dass es sich dabei um eine ImageSource mit MTP handelt.</span><span class="sxs-lookup"><span data-stu-id="18ff4-197">This is a common event that the Windows Portable Device (WPD) system raises when cameras and other imaging devices notify it that they are an ImageSource using MTP.</span></span> <span data-ttu-id="18ff4-198">Weitere Informationen finden Sie unter [Tragbare Windows-Geräte](https://msdn.microsoft.com/library/windows/hardware/ff597729).</span><span class="sxs-lookup"><span data-stu-id="18ff4-198">For more info, see [Windows Portable Devices](https://msdn.microsoft.com/library/windows/hardware/ff597729).</span></span>

<span data-ttu-id="18ff4-199">**Wichtige**die [**Windows.Devices.Portable.StorageDevice**](https://msdn.microsoft.com/library/windows/apps/br225654) -APIs sind Teil der [Familie der Desktopgeräte](https://msdn.microsoft.com/library/windows/apps/dn894631).</span><span class="sxs-lookup"><span data-stu-id="18ff4-199">**Important**The [**Windows.Devices.Portable.StorageDevice**](https://msdn.microsoft.com/library/windows/apps/br225654) APIs are part of the [desktop device family](https://msdn.microsoft.com/library/windows/apps/dn894631).</span></span> <span data-ttu-id="18ff4-200">Apps können diese APIs nur auf Windows 10-Geräten in der Familie der Desktopgeräte, z. B. PCs verwenden.</span><span class="sxs-lookup"><span data-stu-id="18ff4-200">Apps can use these APIs only on Windows10 devices in the desktop device family, such as PCs.</span></span>

 

### <a name="step-1-create-a-new-project-and-add-autoplay-declarations"></a><span data-ttu-id="18ff4-201">Schritt 1: Erstellen eines neuen Projekts und Hinzufügen von Deklarationen für die automatische Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="18ff4-201">Step 1: Create a new project and add AutoPlay declarations</span></span>

1.  <span data-ttu-id="18ff4-202">Öffnen Sie Visual Studio, und wählen Sie im Menü **Datei** die Option **Neues Projekt** aus.</span><span class="sxs-lookup"><span data-stu-id="18ff4-202">Open Visual Studio and select **New Project** from the **File** menu.</span></span> <span data-ttu-id="18ff4-203">Wählen Sie im Abschnitt **VisualC#** unter **Windows** die Option **Leere App (Universelle Windows-App)** aus.</span><span class="sxs-lookup"><span data-stu-id="18ff4-203">In the **Visual C#** section, under **Windows**, select **Blank App (Universal Windows)**.</span></span> <span data-ttu-id="18ff4-204">Nennen Sie die App **AutoPlayDevice\_Camera**, und klicken Sie auf **OK.**</span><span class="sxs-lookup"><span data-stu-id="18ff4-204">Name the app **AutoPlayDevice\_Camera** and click **OK.**</span></span>
2.  <span data-ttu-id="18ff4-205">Öffnen Sie die Datei "Package.appxmanifest", und wählen Sie die Registerkarte **Funktionen** aus. Wählen Sie dann die Funktion **Wechselmedien** aus.</span><span class="sxs-lookup"><span data-stu-id="18ff4-205">Open the Package.appxmanifest file and select the **Capabilities** tab. Select the **Removable Storage** capability.</span></span> <span data-ttu-id="18ff4-206">Damit geben Sie der App Zugriff auf die Daten auf der Kamera als Wechselmedien-Volumegerät.</span><span class="sxs-lookup"><span data-stu-id="18ff4-206">This gives the app access to the data on the camera as a removable storage volume device.</span></span>
3.  <span data-ttu-id="18ff4-207">Wählen Sie in der Manifestdatei Sie die Registerkarte **Deklarationen** und dann in der Dropdownliste **Verfügbare Deklarationen** die Option **Gerät automatisch wiedergeben** aus. Klicken Sie dann auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="18ff4-207">In the manifest file, select the **Declarations** tab. In the **Available Declarations** drop-down list, select **AutoPlay Device** and click **Add**.</span></span> <span data-ttu-id="18ff4-208">Wählen Sie das neue Element vom Typ **Gerät automatisch wiedergeben** aus, das der Liste **Unterstützte Deklarationen** hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="18ff4-208">Select the new **AutoPlay Device** item that was added to the **Supported Declarations** list.</span></span>
4.  <span data-ttu-id="18ff4-209">Die Deklaration **Gerät automatisch wiedergeben** erkennt Ihre App als Option, wenn von der automatischen Wiedergabe ein Geräteereignis ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="18ff4-209">An **AutoPlay Device** declaration identifies your app as an option when AutoPlay raises a device event for known events.</span></span> <span data-ttu-id="18ff4-210">Geben Sie im Abschnitt **Startaktionen** die Werte aus der nachfolgenden Tabelle für die Aktion beim ersten Start an.</span><span class="sxs-lookup"><span data-stu-id="18ff4-210">In the **Launch Actions** section, enter the values in the table below for the first launch action.</span></span>
5.  <span data-ttu-id="18ff4-211">Wählen Sie in der Dropdownliste **Verfügbare Deklarationen** die Option **Dateitypzuordnungen** aus, und klicken Sie anschließend auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="18ff4-211">In the **Available Declarations** drop-down list, select **File Type Associations** and click **Add**.</span></span> <span data-ttu-id="18ff4-212">Setzen Sie in den Eigenschaften der neuen Deklaration vom Typ **Dateitypzuordnungen** das Feld **Anzeigename** auf **Show Images from Camera** und das Feld **Name** auf **image\_association1**.</span><span class="sxs-lookup"><span data-stu-id="18ff4-212">In the Properties of the new **File Type Associations** declaration, set the **Display Name** field to **Show Images from Camera** and the **Name** field to **camera\_association1**.</span></span> <span data-ttu-id="18ff4-213">Klicken Sie im Abschnitt **Unterstützte Dateitypen** auf **Neu hinzufügen** (falls erforderlich).</span><span class="sxs-lookup"><span data-stu-id="18ff4-213">In the **Supported File Types** section, click **Add New** (if needed).</span></span> <span data-ttu-id="18ff4-214">Legen Sie im Feld **Dateityp** die Option **.jpg** fest.</span><span class="sxs-lookup"><span data-stu-id="18ff4-214">Set the **File Type** field to **.jpg**.</span></span> <span data-ttu-id="18ff4-215">Klicken Sie im Abschnitt **Unterstützte Dateitypen** erneut auf **Neu hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="18ff4-215">In the **Supported File Types** section, click **Add New** again.</span></span> <span data-ttu-id="18ff4-216">Legen Sie das Feld **Dateityp** der neuen Dateizuordnung auf **.png** fest.</span><span class="sxs-lookup"><span data-stu-id="18ff4-216">Set the **File Type** field of the new file association to **.png**.</span></span> <span data-ttu-id="18ff4-217">Für Inhaltsereignisse filtert die automatische Wiedergabe alle Dateitypen heraus, die nicht explizit Ihrer App zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="18ff4-217">For content events, AutoPlay filters out any file types that are not explicitly associated with your app.</span></span>
6.  <span data-ttu-id="18ff4-218">Speichern und schließen Sie die Manifestdatei.</span><span class="sxs-lookup"><span data-stu-id="18ff4-218">Save and close the manifest file.</span></span>

| <span data-ttu-id="18ff4-219">Einstellung</span><span class="sxs-lookup"><span data-stu-id="18ff4-219">Setting</span></span>             | <span data-ttu-id="18ff4-220">Wert</span><span class="sxs-lookup"><span data-stu-id="18ff4-220">Value</span></span>            |
|---------------------|------------------|
| <span data-ttu-id="18ff4-221">Verb</span><span class="sxs-lookup"><span data-stu-id="18ff4-221">Verb</span></span>                | <span data-ttu-id="18ff4-222">show</span><span class="sxs-lookup"><span data-stu-id="18ff4-222">show</span></span>             |
| <span data-ttu-id="18ff4-223">Aktionsanzeigename</span><span class="sxs-lookup"><span data-stu-id="18ff4-223">Action Display Name</span></span> | <span data-ttu-id="18ff4-224">Bilder anzeigen</span><span class="sxs-lookup"><span data-stu-id="18ff4-224">Show Pictures</span></span>    |
| <span data-ttu-id="18ff4-225">Inhaltsereignis</span><span class="sxs-lookup"><span data-stu-id="18ff4-225">Content Event</span></span>       | <span data-ttu-id="18ff4-226">WPD\\ImageSource</span><span class="sxs-lookup"><span data-stu-id="18ff4-226">WPD\\ImageSource</span></span> |

<span data-ttu-id="18ff4-227">Die Einstellung **Aktionsanzeigename** gibt die Zeichenfolge an, die bei der automatischen Wiedergabe für Ihre App angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="18ff4-227">The **Action Display Name** setting identifies the string that AutoPlay displays for your app.</span></span> <span data-ttu-id="18ff4-228">Die Einstellung **Verb** dient zum Angeben eines Werts, der für die ausgewählte Option an Ihre App übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="18ff4-228">The **Verb** setting identifies a value that is passed to your app for the selected option.</span></span> <span data-ttu-id="18ff4-229">Sie können mehrere Startaktionen für Ereignisse der automatischen Wiedergabe angeben und mit der Einstellung **Verb** ermitteln, welche Option ein Benutzer für Ihre App ausgewählt hat.</span><span class="sxs-lookup"><span data-stu-id="18ff4-229">You can specify multiple launch actions for an AutoPlay event and use the **Verb** setting to determine which option a user has selected for your app.</span></span> <span data-ttu-id="18ff4-230">Für welche Option sich der Benutzer entschieden hat, erfahren Sie durch Überprüfen der **verb**-Eigenschaft der an die App übergebenen Startereignisargumente.</span><span class="sxs-lookup"><span data-stu-id="18ff4-230">You can tell which option the user selected by checking the **verb** property of the startup event arguments passed to your app.</span></span> <span data-ttu-id="18ff4-231">Für die Einstellung **Verb** können Sie einen beliebigen Wert verwenden. Einzige Ausnahme ist **open**: Dieser Wert ist reserviert.</span><span class="sxs-lookup"><span data-stu-id="18ff4-231">You can use any value for the **Verb** setting except, **open**, which is reserved.</span></span> <span data-ttu-id="18ff4-232">Ein Beispiel zur Verwendung mehrerer Verben in einer einzelnen App finden Sie unter [Registrieren für Inhalt für die automatische Wiedergabe](#register-for-autoplay-content).</span><span class="sxs-lookup"><span data-stu-id="18ff4-232">For an example of using multiple verbs in a single app, see [Register for AutoPlay content](#register-for-autoplay-content).</span></span>

### <a name="step-2-add-assembly-reference-for-the-desktop-extensions"></a><span data-ttu-id="18ff4-233">Schritt 2: Hinzufügen von Assemblyverweisen für die Desktoperweiterungen</span><span class="sxs-lookup"><span data-stu-id="18ff4-233">Step 2: Add assembly reference for the desktop extensions</span></span>

<span data-ttu-id="18ff4-234">Die APIs, die für den Speicherzugriff auf einem tragbaren Windows-Gerät erforderlich sind ([**Windows.Devices.Portable.StorageDevice**](https://msdn.microsoft.com/library/windows/apps/br225654)), sind Teil der [Desktopgerätefamilie](https://msdn.microsoft.com/library/windows/apps/dn894631).</span><span class="sxs-lookup"><span data-stu-id="18ff4-234">The APIs required to access storage on a Windows Portable Device, [**Windows.Devices.Portable.StorageDevice**](https://msdn.microsoft.com/library/windows/apps/br225654), are part of the desktop [desktop device family](https://msdn.microsoft.com/library/windows/apps/dn894631).</span></span> <span data-ttu-id="18ff4-235">Dies bedeutet, dass eine spezielle Assembly erforderlich ist, um die APIs zu verwenden, und dass diese Aufrufe nur auf einem Gerät der Desktopgerätefamilie (z.B. einem PC) funktionieren.</span><span class="sxs-lookup"><span data-stu-id="18ff4-235">This means a special assembly is required to use the APIs and those calls will only work on a device in the desktop device family (such as a PC).</span></span>

1.  <span data-ttu-id="18ff4-236">Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Verweise**, und wählen Sie dann **Verweis hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="18ff4-236">In **Solution Explorer**, right click on **References** and then **Add Reference...**.</span></span>
2.  <span data-ttu-id="18ff4-237">Erweitern Sie die Option **Universal Windows**, und klicken Sie auf **Erweiterungen**.</span><span class="sxs-lookup"><span data-stu-id="18ff4-237">Expand **Universal Windows** and click **Extensions**.</span></span>
3.  <span data-ttu-id="18ff4-238">Wählen Sie dann **Windows Desktop Extensions for the UWP** aus, und klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="18ff4-238">Then select **Windows Desktop Extensions for the UWP** and click **OK**.</span></span>

### <a name="step-3-add-xaml-ui"></a><span data-ttu-id="18ff4-239">Schritt 3: Hinzufügen von XAML-UI</span><span class="sxs-lookup"><span data-stu-id="18ff4-239">Step 3: Add XAML UI</span></span>

<span data-ttu-id="18ff4-240">Öffnen Sie die Datei „MainPage.xaml“, und fügen Sie dem Standardabschnitt &lt;Grid&gt; folgenden XAML-Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="18ff4-240">Open the MainPage.xaml file and add the following XAML to the default &lt;Grid&gt; section.</span></span>

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

### <a name="step-4-add-activation-code"></a><span data-ttu-id="18ff4-241">Schritt 4: Hinzufügen von Aktivierungscode</span><span class="sxs-lookup"><span data-stu-id="18ff4-241">Step 4: Add activation code</span></span>

<span data-ttu-id="18ff4-242">Der Code in diesem Schritts verweist auf die Kamera als [**StorageDevice**](https://msdn.microsoft.com/library/windows/apps/br225654), indem er die Geräteinformations-ID der Kamera an die [**FromId**](https://msdn.microsoft.com/library/windows/apps/br225655)-Methode übergibt.</span><span class="sxs-lookup"><span data-stu-id="18ff4-242">The code in this step references the camera as a [**StorageDevice**](https://msdn.microsoft.com/library/windows/apps/br225654) by passing the device information Id of the camera to the [**FromId**](https://msdn.microsoft.com/library/windows/apps/br225655) method.</span></span> <span data-ttu-id="18ff4-243">Die Geräteinformations-ID der Kamera wird ermittelt, indem die Ereignisargumente zunächst in [**DeviceActivatedEventArgs**](https://msdn.microsoft.com/library/windows/apps/br224710) umgewandelt werden und anschließend der Wert von der [**DeviceInformationId**](https://msdn.microsoft.com/library/windows/apps/br224711)-Eigenschaft abgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="18ff4-243">The device information Id of the camera is obtained by first casting the event arguments as [**DeviceActivatedEventArgs**](https://msdn.microsoft.com/library/windows/apps/br224710), and then getting the value from the [**DeviceInformationId**](https://msdn.microsoft.com/library/windows/apps/br224711) property.</span></span>

<span data-ttu-id="18ff4-244">Öffnen Sie die Datei „App.xaml.cs“, und fügen Sie der **App**-Klasse den folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="18ff4-244">Open the App.xaml.cs file and add the following code to the **App** class.</span></span>

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

> <span data-ttu-id="18ff4-245">**Hinweis:** die `ShowImages` -Methode wird im nächsten Schritt hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="18ff4-245">**Note**The `ShowImages` method is added in the following step.</span></span>

### <a name="step-5-add-code-to-display-device-information"></a><span data-ttu-id="18ff4-246">Schritt 5: Hinzufügen von Code zum Anzeigen von Geräteinformationen</span><span class="sxs-lookup"><span data-stu-id="18ff4-246">Step 5: Add code to display device information</span></span>

<span data-ttu-id="18ff4-247">Informationen zur Kamera erhalten Sie über die Eigenschaften der [**StorageDevice**](https://msdn.microsoft.com/library/windows/apps/br225654)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="18ff4-247">You can obtain information about the camera from the properties of the [**StorageDevice**](https://msdn.microsoft.com/library/windows/apps/br225654) class.</span></span> <span data-ttu-id="18ff4-248">Der Code in diesem Schritt zeigt bei der Ausführung der App den Gerätenamen und andere Informationen für den Benutzer an.</span><span class="sxs-lookup"><span data-stu-id="18ff4-248">The code in this step displays the device name and other info to the user when the app runs.</span></span> <span data-ttu-id="18ff4-249">Anschließend ruft der Code die Methoden GetImageList und GetThumbnail auf, die Sie im nächsten Schritt hinzufügen, um Miniaturansichten der auf der Kamera gespeicherten Bilder anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="18ff4-249">The code then calls the GetImageList and GetThumbnail methods, which you will add in the next step, to display thumbnails of the images stored on the camera</span></span>

<span data-ttu-id="18ff4-250">Fügen Sie in der Datei „MainPage.xaml.cs“ der **MainPage**-Klasse folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="18ff4-250">In the MainPage.xaml.cs file, add the following code to the **MainPage** class.</span></span>

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

> <span data-ttu-id="18ff4-251">**Hinweis:** der `GetImageList` und `GetThumbnail` Methoden werden im nächsten Schritt hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="18ff4-251">**Note**The `GetImageList` and `GetThumbnail` methods are added in the following step.</span></span>

### <a name="step-6-add-code-to-display-images"></a><span data-ttu-id="18ff4-252">Schritt 6: Hinzufügen von Code zum Anzeigen von Bildern</span><span class="sxs-lookup"><span data-stu-id="18ff4-252">Step 6: Add code to display images</span></span>

<span data-ttu-id="18ff4-253">Der Code in diesem Schritt zeigt Miniaturansichten der Bilder an, die auf der Kamera gespeichert sind.</span><span class="sxs-lookup"><span data-stu-id="18ff4-253">The code in this step displays thumbnails of the images stored on the camera.</span></span> <span data-ttu-id="18ff4-254">Der Code ruft die Miniaturansicht mit asynchronen Aufrufen an die Kamera ab.</span><span class="sxs-lookup"><span data-stu-id="18ff4-254">The code makes asynchronous calls to the camera to get the thumbnail image.</span></span> <span data-ttu-id="18ff4-255">Der nächste asynchrone Aufruf erfolgt aber nicht, bis der vorherige asynchrone Aufruf abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="18ff4-255">However, the next asynchronous call doesn't occur until the previous asynchronous call completes.</span></span> <span data-ttu-id="18ff4-256">Auf diese Weise wird sichergestellt, dass nur jeweils ein Aufruf an die Kamera gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="18ff4-256">This ensures that only one request is made to the camera at a time.</span></span>

<span data-ttu-id="18ff4-257">Fügen Sie in der Datei „MainPage.xaml.cs“ der **MainPage**-Klasse folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="18ff4-257">In the MainPage.xaml.cs file, add the following code to the **MainPage** class.</span></span>

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

### <a name="step-7-build-and-run-the-app"></a><span data-ttu-id="18ff4-258">Schritt 7: Erstellen und Ausführen der App</span><span class="sxs-lookup"><span data-stu-id="18ff4-258">Step 7: Build and run the app</span></span>

1.  <span data-ttu-id="18ff4-259">Drücken SieF5, um die App zu erstellen und bereitzustellen (im Debugmodus).</span><span class="sxs-lookup"><span data-stu-id="18ff4-259">Press F5 to build and deploy the app (in debug mode).</span></span>
2.  <span data-ttu-id="18ff4-260">Führen Sie Ihre App aus, indem Sie eine Kamera an Ihren Computer anschließen.</span><span class="sxs-lookup"><span data-stu-id="18ff4-260">To run your app, connect a camera to your machine.</span></span> <span data-ttu-id="18ff4-261">Wählen Sie die App anschließend in der Liste mit Optionen für die automatische Wiedergabe aus.</span><span class="sxs-lookup"><span data-stu-id="18ff4-261">Then select the app from the AutoPlay list of options.</span></span>
    <span data-ttu-id="18ff4-262">**Hinweis:** nicht alle Kameras für die **WPD\\ImageSource** Wiedergabe Gerät ankündigen.</span><span class="sxs-lookup"><span data-stu-id="18ff4-262">**Note**Not all cameras advertise for the **WPD\\ImageSource** AutoPlay device event.</span></span>

## <a name="configure-removable-storage"></a><span data-ttu-id="18ff4-263">Konfigurieren von Wechselmedien</span><span class="sxs-lookup"><span data-stu-id="18ff4-263">Configure removable storage</span></span>

<span data-ttu-id="18ff4-264">Sie können ein Volumegerät wie eine Speicherkarte oder einen USB-Stick als Gerät für die **automatische Wiedergabe** identifizieren, wenn das Volumegerät an einen PC angeschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="18ff4-264">You can identify a volume device such as a memory card or thumb drive as an **AutoPlay** device when the volume device is connected to a PC.</span></span> <span data-ttu-id="18ff4-265">Das ist vor allem dann sehr nützlich, wenn Sie möchten, dass dem Benutzer bei der **automatischen Wiedergabe** eine bestimmte App für Ihr Volumegerät angeboten wird.</span><span class="sxs-lookup"><span data-stu-id="18ff4-265">This is especially useful when you want to associate a specific app for **AutoPlay** to present to the user for your volume device.</span></span>

<span data-ttu-id="18ff4-266">Im Folgenden zeigen wir, wie Sie Ihr Volumegerät als Gerät zur **automatischen Wiedergabe** identifizieren.</span><span class="sxs-lookup"><span data-stu-id="18ff4-266">Here we show how to identify your volume device as an **AutoPlay** device.</span></span>

<span data-ttu-id="18ff4-267">Identifizieren Sie Ihr Volumegerät als Gerät für die **automatische Wiedergabe**, indem Sie dem Stammverzeichnis des Geräts die Datei „autorun.inf“ hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="18ff4-267">To identify your volume device as an **AutoPlay** device, add an autorun.inf file to the root drive of your device.</span></span> <span data-ttu-id="18ff4-268">Fügen Sie in der Datei „autorun.inf“ im **AutoRun**-Abschnitt einen **CustomEvent**-Schlüssel hinzu.</span><span class="sxs-lookup"><span data-stu-id="18ff4-268">In the autorun.inf file, add a **CustomEvent** key to the **AutoRun** section.</span></span> <span data-ttu-id="18ff4-269">Wenn Ihr Volumegerät an einen PC angeschlossen wird, findet die **automatische Wiedergabe** die Datei „autorun.inf“ und behandelt Ihr Volume als ein Gerät.</span><span class="sxs-lookup"><span data-stu-id="18ff4-269">When your volume device connects to a PC, **AutoPlay** will find the autorun.inf file and treat your volume as a device.</span></span> <span data-ttu-id="18ff4-270">Die **automatische Wiedergabe** erstellt anhand des Namens, den Sie für den **CustomEvent**-Schlüssel angegeben haben, ein Ereignis zur **automatischen Wiedergabe**.</span><span class="sxs-lookup"><span data-stu-id="18ff4-270">**AutoPlay** will create an **AutoPlay** event by using the name that you supplied for the **CustomEvent** key.</span></span> <span data-ttu-id="18ff4-271">Sie können eine App erstellen und sie dann als Handler für dieses Ereignis zur **automatischen Wiedergabe** registrieren.</span><span class="sxs-lookup"><span data-stu-id="18ff4-271">You can then create an app and register the app as a handler for that **AutoPlay** event.</span></span> <span data-ttu-id="18ff4-272">Wenn das Gerät an den PC angeschlossen wird, bietet die **automatische Wiedergabe** Ihre App als Handler für Ihr Volumegerät an.</span><span class="sxs-lookup"><span data-stu-id="18ff4-272">When the device is connected to the PC, **AutoPlay** will show your app as a handler for your volume device.</span></span> <span data-ttu-id="18ff4-273">Weitere Informationen zu Dateien vom Typ „autorun.inf“ finden Sie unter [Autorun.inf-Einträge](https://msdn.microsoft.com/library/windows/desktop/cc144200).</span><span class="sxs-lookup"><span data-stu-id="18ff4-273">For more info on autorun.inf files, see [autorun.inf entries](https://msdn.microsoft.com/library/windows/desktop/cc144200).</span></span>

### <a name="step-1-create-an-autoruninf-file"></a><span data-ttu-id="18ff4-274">Schritt 1: Erstellen der Datei „autorun.inf“</span><span class="sxs-lookup"><span data-stu-id="18ff4-274">Step 1: Create an autorun.inf file</span></span>

<span data-ttu-id="18ff4-275">Fügen Sie im Stammverzeichnis Ihres Volumegeräts eine Datei namens „autorun.inf“ hinzu.</span><span class="sxs-lookup"><span data-stu-id="18ff4-275">In the root drive of your volume device, add a file named autorun.inf.</span></span> <span data-ttu-id="18ff4-276">Öffnen Sie die Datei „autorun.inf“, und fügen Sie den folgenden Text hinzu.</span><span class="sxs-lookup"><span data-stu-id="18ff4-276">Open the autorun.inf file and add the following text.</span></span>

``` syntax
[AutoRun]
CustomEvent=AutoPlayCustomEventQuickstart
```

### <a name="step-2-create-a-new-project-and-add-autoplay-declarations"></a><span data-ttu-id="18ff4-277">Schritt 2: Erstellen eines neuen Projekts und Hinzufügen von Deklarationen für die automatische Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="18ff4-277">Step 2: Create a new project and add AutoPlay declarations</span></span>

1.  <span data-ttu-id="18ff4-278">Öffnen Sie Visual Studio, und wählen Sie im Menü **Datei** die Option **Neues Projekt** aus.</span><span class="sxs-lookup"><span data-stu-id="18ff4-278">Open Visual Studio and select **New Project** from the **File** menu.</span></span> <span data-ttu-id="18ff4-279">Wählen Sie im Abschnitt **VisualC#** unter **Windows** die Option **Leere App (Universelle Windows-App)** aus.</span><span class="sxs-lookup"><span data-stu-id="18ff4-279">In the **Visual C#** section, under **Windows**, select **Blank App (Universal Windows)**.</span></span> <span data-ttu-id="18ff4-280">Nennen Sie die Anwendung **AutoPlayCustomEvent**, und klicken Sie auf **OK.**</span><span class="sxs-lookup"><span data-stu-id="18ff4-280">Name the application **AutoPlayCustomEvent** and click **OK.**</span></span>
2.  <span data-ttu-id="18ff4-281">Öffnen Sie die Datei "Package.appxmanifest", und wählen Sie die Registerkarte **Funktionen** aus. Wählen Sie dann die Funktion **Wechselmedien** aus.</span><span class="sxs-lookup"><span data-stu-id="18ff4-281">Open the Package.appxmanifest file and select the **Capabilities** tab. Select the **Removable Storage** capability.</span></span> <span data-ttu-id="18ff4-282">Damit erhält Ihre App Zugriff auf die Dateien und Ordner auf dem Wechselmediengerät.</span><span class="sxs-lookup"><span data-stu-id="18ff4-282">This gives the app access to the files and folders on removable storage devices.</span></span>
3.  <span data-ttu-id="18ff4-283">Wählen Sie in der Manifestdatei die Registerkarte **Deklarationen** und dann in der Dropdownliste **Verfügbare Deklarationen** die Option **Inhalt automatisch wiedergeben** aus, und klicken Sie dann auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="18ff4-283">In the manifest file, select the **Declarations** tab. In the **Available Declarations** drop-down list, select **AutoPlay Content** and click **Add**.</span></span> <span data-ttu-id="18ff4-284">Wählen Sie das neue Element vom Typ **Inhalt automatisch wiedergeben** aus, das der Liste **Unterstützte Deklarationen** hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="18ff4-284">Select the new **AutoPlay Content** item that was added to the **Supported Declarations** list.</span></span>

    <span data-ttu-id="18ff4-285">**Hinweis:** Sie können alternativ auch auswählen, eine **Gerät automatisch wiedergeben** Deklaration für Ihr benutzerdefiniertes Ereignis für die automatische Wiedergabe hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="18ff4-285">**Note**Alternatively, you can also choose to add an **AutoPlay Device** declaration for your custom AutoPlay event.</span></span>  
4.  <span data-ttu-id="18ff4-286">Geben Sie im Abschnitt **Startaktionen** der Ereignisdeklaration **Inhalt automatisch Wiedergeben** für die Aktion beim ersten Start die Werte in der folgenden Tabelle ein.</span><span class="sxs-lookup"><span data-stu-id="18ff4-286">In the **Launch Actions** section for your **AutoPlay Content** event declaration, enter the values in the table below for the first launch action.</span></span>
5.  <span data-ttu-id="18ff4-287">Wählen Sie in der Dropdownliste **Verfügbare Deklarationen** die Option **Dateitypzuordnungen** aus, und klicken Sie anschließend auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="18ff4-287">In the **Available Declarations** drop-down list, select **File Type Associations** and click **Add**.</span></span> <span data-ttu-id="18ff4-288">Setzen Sie in den Eigenschaften der neuen Deklaration vom Typ **Dateitypzuordnungen** das Feld **Anzeigename** auf **Show .ms Files** und das Feld **Name** auf **ms\_association**.</span><span class="sxs-lookup"><span data-stu-id="18ff4-288">In the Properties of the new **File Type Associations** declaration, set the **Display Name** field to **Show .ms Files** and the **Name** field to **ms\_association**.</span></span> <span data-ttu-id="18ff4-289">Klicken Sie im Abschnitt **Unterstützte Dateitypen** auf **Neu hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="18ff4-289">In the **Supported File Types** section, click **Add New**.</span></span> <span data-ttu-id="18ff4-290">Legen Sie im Feld **Dateityp** die Option **.ms** fest.</span><span class="sxs-lookup"><span data-stu-id="18ff4-290">Set the **File Type** field to **.ms**.</span></span> <span data-ttu-id="18ff4-291">Für Inhaltsereignisse filtert die automatische Wiedergabe alle Dateitypen heraus, die nicht explizit Ihrer App zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="18ff4-291">For content events, AutoPlay filters out any file types that aren't explicitly associated with your app.</span></span>
6.  <span data-ttu-id="18ff4-292">Speichern und schließen Sie die Manifestdatei.</span><span class="sxs-lookup"><span data-stu-id="18ff4-292">Save and close the manifest file.</span></span>

| <span data-ttu-id="18ff4-293">Einstellung</span><span class="sxs-lookup"><span data-stu-id="18ff4-293">Setting</span></span>             | <span data-ttu-id="18ff4-294">Wert</span><span class="sxs-lookup"><span data-stu-id="18ff4-294">Value</span></span>                         |
|---------------------|-------------------------------|
| <span data-ttu-id="18ff4-295">Verb</span><span class="sxs-lookup"><span data-stu-id="18ff4-295">Verb</span></span>                | <span data-ttu-id="18ff4-296">show</span><span class="sxs-lookup"><span data-stu-id="18ff4-296">show</span></span>                          |
| <span data-ttu-id="18ff4-297">Aktionsanzeigename</span><span class="sxs-lookup"><span data-stu-id="18ff4-297">Action Display Name</span></span> | <span data-ttu-id="18ff4-298">Dateien anzeigen</span><span class="sxs-lookup"><span data-stu-id="18ff4-298">Show Files</span></span>                    |
| <span data-ttu-id="18ff4-299">Inhaltsereignis</span><span class="sxs-lookup"><span data-stu-id="18ff4-299">Content Event</span></span>       | <span data-ttu-id="18ff4-300">AutoPlayCustomEventQuickstart</span><span class="sxs-lookup"><span data-stu-id="18ff4-300">AutoPlayCustomEventQuickstart</span></span> |

<span data-ttu-id="18ff4-301">Der Wert für **Inhaltsereignis** ist der Text, den Sie für den **CustomEvent**-Schlüssel in der Datei „autorun.inf“ angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="18ff4-301">The **Content Event** value is the text that you supplied for the **CustomEvent** key in your autorun.inf file.</span></span> <span data-ttu-id="18ff4-302">Die Einstellung **Aktionsanzeigename** gibt die Zeichenfolge an, die bei der automatischen Wiedergabe für Ihre App angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="18ff4-302">The **Action Display Name** setting identifies the string that AutoPlay displays for your app.</span></span> <span data-ttu-id="18ff4-303">Die Einstellung **Verb** dient zum Angeben eines Werts, der für die ausgewählte Option an Ihre App übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="18ff4-303">The **Verb** setting identifies a value that is passed to your app for the selected option.</span></span> <span data-ttu-id="18ff4-304">Sie können mehrere Startaktionen für Ereignisse der automatischen Wiedergabe angeben und mit der Einstellung **Verb** ermitteln, welche Option ein Benutzer für Ihre App ausgewählt hat.</span><span class="sxs-lookup"><span data-stu-id="18ff4-304">You can specify multiple launch actions for an AutoPlay event and use the **Verb** setting to determine which option a user has selected for your app.</span></span> <span data-ttu-id="18ff4-305">Für welche Option sich der Benutzer entschieden hat, erfahren Sie durch Überprüfen der **verb**-Eigenschaft der an die App übergebenen Startereignisargumente.</span><span class="sxs-lookup"><span data-stu-id="18ff4-305">You can tell which option the user selected by checking the **verb** property of the startup event arguments passed to your app.</span></span> <span data-ttu-id="18ff4-306">Für die Einstellung **Verb** können Sie einen beliebigen Wert verwenden. Einzige Ausnahme ist **open**: Dieser Wert ist reserviert.</span><span class="sxs-lookup"><span data-stu-id="18ff4-306">You can use any value for the **Verb** setting except, **open**, which is reserved.</span></span>

### <a name="step-3-add-xaml-ui"></a><span data-ttu-id="18ff4-307">Schritt 3: Hinzufügen von XAML-UI</span><span class="sxs-lookup"><span data-stu-id="18ff4-307">Step 3: Add XAML UI</span></span>

<span data-ttu-id="18ff4-308">Öffnen Sie die Datei „MainPage.xaml“, und fügen Sie dem Standardabschnitt &lt;Grid&gt; folgenden XAML-Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="18ff4-308">Open the MainPage.xaml file and add the following XAML to the default &lt;Grid&gt; section.</span></span>

```xml
<StackPanel Orientation="Vertical">
    <TextBlock FontSize="28" Margin="10,0,800,0">Files</TextBlock>
    <TextBlock x:Name="FilesBlock" FontSize="22" Height="600" Margin="10,0,800,0" />
</StackPanel>
```

### <a name="step-4-add-activation-code"></a><span data-ttu-id="18ff4-309">Schritt 4: Hinzufügen von Aktivierungscode</span><span class="sxs-lookup"><span data-stu-id="18ff4-309">Step 4: Add activation code</span></span>

<span data-ttu-id="18ff4-310">Der Code in diesem Schritt ruft eine Methode zum Anzeigen der Ordner im Stammlaufwerk Ihres Volumegeräts auf.</span><span class="sxs-lookup"><span data-stu-id="18ff4-310">The code in this step calls a method to display the folders in the root drive of your volume device.</span></span> <span data-ttu-id="18ff4-311">Für das Inhaltsereignis zur automatischen Wiedergabe übergibt die automatische Wiedergabe den Stammordner des Speichergeräts in den Startargumenten, die der Anwendung während des **OnFileActivated**-Ereignisses übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="18ff4-311">For the AutoPlay content events, AutoPlay passes the root folder of the storage device in the startup arguments passed to the application during the **OnFileActivated** event.</span></span> <span data-ttu-id="18ff4-312">Sie können diesen Ordner aus dem ersten Element der **Files**-Eigenschaft abrufen.</span><span class="sxs-lookup"><span data-stu-id="18ff4-312">You can retrieve this folder from the first element of the **Files** property.</span></span>

<span data-ttu-id="18ff4-313">Öffnen Sie die Datei „App.xaml.cs“, und fügen Sie der **App**-Klasse den folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="18ff4-313">Open the App.xaml.cs file and add the following code to the **App** class.</span></span>

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

> <span data-ttu-id="18ff4-314">**Hinweis:** die `DisplayFiles` -Methode wird im nächsten Schritt hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="18ff4-314">**Note**The `DisplayFiles` method is added in the following step.</span></span>

 

### <a name="step-5-add-code-to-display-folders"></a><span data-ttu-id="18ff4-315">Schritt 5: Hinzufügen von Code zum Anzeigen von Ordnern</span><span class="sxs-lookup"><span data-stu-id="18ff4-315">Step 5: Add code to display folders</span></span>

<span data-ttu-id="18ff4-316">Fügen Sie in der Datei „MainPage.xaml.cs“ der **MainPage**-Klasse folgenden Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="18ff4-316">In the MainPage.xaml.cs file add the following code to the **MainPage** class.</span></span>

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

### <a name="step-6-build-and-run-the-qpp"></a><span data-ttu-id="18ff4-317">Schritt 6: Erstellen und Ausführen der App</span><span class="sxs-lookup"><span data-stu-id="18ff4-317">Step 6: Build and run the qpp</span></span>

1.  <span data-ttu-id="18ff4-318">Drücken SieF5, um die App zu erstellen und bereitzustellen (im Debugmodus).</span><span class="sxs-lookup"><span data-stu-id="18ff4-318">Press F5 to build and deploy the app (in debug mode).</span></span>
2.  <span data-ttu-id="18ff4-319">Legen Sie eine Speicherkarte oder ein anderes Speichergerät in Ihren PC ein, um Ihre App auszuführen.</span><span class="sxs-lookup"><span data-stu-id="18ff4-319">To run your app, insert a memory card or another storage device into your PC.</span></span> <span data-ttu-id="18ff4-320">Wählen Sie die App anschließend in der Liste mit den Handleroptionen für die automatische Wiedergabe aus.</span><span class="sxs-lookup"><span data-stu-id="18ff4-320">Then select your app from the list of AutoPlay handler options.</span></span>

## <a name="autoplay-event-reference"></a><span data-ttu-id="18ff4-321">Referenz für Ereignisse der automatischen Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="18ff4-321">AutoPlay event reference</span></span>


<span data-ttu-id="18ff4-322">Das **automatische Wiedergabesystem** ermöglicht es, Apps für eine Vielzahl von Arrival-Ereignissen für Geräte und Volumes (Datenträger) zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="18ff4-322">The **AutoPlay** system allows apps to register for a variety of device and volume (disk) arrival events.</span></span> <span data-ttu-id="18ff4-323">Wenn Sie die App für Inhaltsereignisse für die **automatische Wiedergabe** registrieren möchten, müssen Sie die Funktion **Wechselmedien** im Paketmanifest aktivieren.</span><span class="sxs-lookup"><span data-stu-id="18ff4-323">To register for **AutoPlay** content events, you must enable the **Removable Storage** capability in your package manifest.</span></span> <span data-ttu-id="18ff4-324">In der folgenden Tabelle sind die Ereignisse aufgeführt, die Sie für die automatische Wiedergabe registrieren können, wenn sie ausgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="18ff4-324">This table shows the events that you can register for and when they are raised.</span></span>

| <span data-ttu-id="18ff4-325">Szenario</span><span class="sxs-lookup"><span data-stu-id="18ff4-325">Scenario</span></span>                                                           | <span data-ttu-id="18ff4-326">Ereignis</span><span class="sxs-lookup"><span data-stu-id="18ff4-326">Event</span></span>                              | <span data-ttu-id="18ff4-327">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="18ff4-327">Description</span></span>   |
|--------------------------------------------------------------------|------------------------------------|---------------|
| <span data-ttu-id="18ff4-328">Anzeigen von Fotos auf einer Kamera</span><span class="sxs-lookup"><span data-stu-id="18ff4-328">Using photos on a Camera</span></span>                                           | **<span data-ttu-id="18ff4-329">WPD\ImageSource</span><span class="sxs-lookup"><span data-stu-id="18ff4-329">WPD\ImageSource</span></span>**                | <span data-ttu-id="18ff4-330">Ausgelöst für Kameras, die als tragbare Windows-Geräte mit ImageSource-Funktion erkannt wurden.</span><span class="sxs-lookup"><span data-stu-id="18ff4-330">Raised for cameras that are identified as Windows Portable Devices and offer the ImageSource capability.</span></span> |
| <span data-ttu-id="18ff4-331">Abspielen von Musik auf einem Audioplayer</span><span class="sxs-lookup"><span data-stu-id="18ff4-331">Using music on an audio player</span></span>                                     | **<span data-ttu-id="18ff4-332">WPD\AudioSource</span><span class="sxs-lookup"><span data-stu-id="18ff4-332">WPD\AudioSource</span></span>**                | <span data-ttu-id="18ff4-333">Ausgelöst für Mediaplayer, die als tragbare Windows-Geräte mit AudioSource-Funktion erkannt wurden.</span><span class="sxs-lookup"><span data-stu-id="18ff4-333">Raised for media players that are identified as Windows Portable Devices and offer the AudioSource capability.</span></span> |
| <span data-ttu-id="18ff4-334">Abspielen von Videos auf einer Videokamera</span><span class="sxs-lookup"><span data-stu-id="18ff4-334">Using videos on a video camera</span></span>                                     | **<span data-ttu-id="18ff4-335">WPD\VideoSource</span><span class="sxs-lookup"><span data-stu-id="18ff4-335">WPD\VideoSource</span></span>**                | <span data-ttu-id="18ff4-336">Ausgelöst für Videokameras, die als tragbare Windows-Geräte mit VideoSource-Funktion erkannt wurden.</span><span class="sxs-lookup"><span data-stu-id="18ff4-336">Raised for video cameras that are identified as Windows Portable Devices and offer the VideoSource capability.</span></span> |
| <span data-ttu-id="18ff4-337">Zugriff auf ein verbundenes Flash-Laufwerk oder auf eine externe Festplatte</span><span class="sxs-lookup"><span data-stu-id="18ff4-337">Access a connected flash drive or external hard drive</span></span>              | **<span data-ttu-id="18ff4-338">StorageOnArrival</span><span class="sxs-lookup"><span data-stu-id="18ff4-338">StorageOnArrival</span></span>**               | <span data-ttu-id="18ff4-339">Ausgelöst, wenn ein Laufwerk oder ein Volume an den PC angeschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="18ff4-339">Raised when a drive or volume is connected to the PC.</span></span>   <span data-ttu-id="18ff4-340">Wenn das Laufwerk oder Volume den Ordner „DCIM“, „AVCHD“ oder „PRIVATE\ACHD“ im Stammverzeichnis des Datenträgers enthält, wird stattdessen das **ShowPicturesOnArrival**-Ereignis ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="18ff4-340">If the drive or volume contains a DCIM, AVCHD, or PRIVATE\ACHD folder in the root of the disk, the **ShowPicturesOnArrival** event is raised instead.</span></span> |
| <span data-ttu-id="18ff4-341">Anzeigen von Fotos auf einem Massenspeicher (Legacy)</span><span class="sxs-lookup"><span data-stu-id="18ff4-341">Using photos from mass storage (legacy)</span></span>                            | **<span data-ttu-id="18ff4-342">ShowPicturesOnArrival</span><span class="sxs-lookup"><span data-stu-id="18ff4-342">ShowPicturesOnArrival</span></span>**          | <span data-ttu-id="18ff4-343">Dieses Ereignis wird ausgelöst, wenn das Laufwerk oder das Volume den Ordner „DCIM“, „AVCHD“ oder „PRIVATE\ACHD“ im Stammverzeichnis der Platte enthält.</span><span class="sxs-lookup"><span data-stu-id="18ff4-343">Raised when a drive or volume contains a DCIM, AVCHD, or PRIVATE\ACHD folder in the root of the disk.</span></span> <span data-ttu-id="18ff4-344">Wenn der Benutzer in der Systemsteuerung unter „Automatische Wiedergabe“ die Option **Gewünschte Aktion für jeden Medientyp auswählen** aktiviert hat, überprüft die automatische Wiedergabe das am PC angeschlossene Volume, um den Inhaltstyp auf dem Datenträger zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="18ff4-344">IIf a user  has enabled **Choose what to do with each type of media** in the AutoPlay Control Panel, AutoPlay will examine a volume connected to the PC to determine the type of content on the disk.</span></span> <span data-ttu-id="18ff4-345">Wenn Bilder gefunden werden, wird **ShowPicturesOnArrival** ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="18ff4-345">When pictures are found, **ShowPicturesOnArrival** is raised.</span></span> |
| <span data-ttu-id="18ff4-346">Empfangen von Fotos mit Näherungsfreigabe (Koppeln und Senden)</span><span class="sxs-lookup"><span data-stu-id="18ff4-346">Receiving photos with Proximity Sharing (tap and send)</span></span>             | **<span data-ttu-id="18ff4-347">ShowPicturesOnArrival</span><span class="sxs-lookup"><span data-stu-id="18ff4-347">ShowPicturesOnArrival</span></span>**          | <span data-ttu-id="18ff4-348">Wenn Benutzer Inhalt mit Näherung (Koppeln und Senden) senden, prüft die automatische Wiedergabe die freigegebenen Dateien auf den Inhaltstyp.</span><span class="sxs-lookup"><span data-stu-id="18ff4-348">When users send content with using proximity (tap and send), AutoPlay will examine the shared files to determine the type of content.</span></span> <span data-ttu-id="18ff4-349">Wenn Bilder gefunden werden, wird **ShowPicturesOnArrival** ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="18ff4-349">If pictures are found, **ShowPicturesOnArrival** is raised.</span></span> |
| <span data-ttu-id="18ff4-350">Abspielen von Musik von einem Massenspeicher (Legacy)</span><span class="sxs-lookup"><span data-stu-id="18ff4-350">Using music from mass storage (legacy)</span></span>                             | **<span data-ttu-id="18ff4-351">PlayMusicFilesOnArrival</span><span class="sxs-lookup"><span data-stu-id="18ff4-351">PlayMusicFilesOnArrival</span></span>**        | <span data-ttu-id="18ff4-352">Wenn der Benutzer in der Systemsteuerung unter „Automatische Wiedergabe“ die Option **Gewünschte Aktion für jeden Medientyp auswählen** aktiviert hat, überprüft die automatische Wiedergabe das am PC angeschlossene Volume, um den Inhaltstyp auf dem Datenträger zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="18ff4-352">If a user has enabled **Choose what to do with each type of media** in the AutoPlay Control Panel, AutoPlay will examine a volume connected to the PC to determine the type of content on the disk.</span></span>  <span data-ttu-id="18ff4-353">Wenn Musikdateien gefunden werden, wird **PlayMusicFilesOnArrival** ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="18ff4-353">When music files are found, **PlayMusicFilesOnArrival** is raised.</span></span> |
| <span data-ttu-id="18ff4-354">Empfangen von Musik mit Näherungsfreigabe (Koppeln und Senden)</span><span class="sxs-lookup"><span data-stu-id="18ff4-354">Receiving music with Proximity Sharing (tap and send)</span></span>              | **<span data-ttu-id="18ff4-355">PlayMusicFilesOnArrival</span><span class="sxs-lookup"><span data-stu-id="18ff4-355">PlayMusicFilesOnArrival</span></span>**        | <span data-ttu-id="18ff4-356">Wenn Benutzer Inhalt mit Näherung (Koppeln und Senden) senden, prüft die automatische Wiedergabe die freigegebenen Dateien auf den Inhaltstyp.</span><span class="sxs-lookup"><span data-stu-id="18ff4-356">When users send content with using proximity (tap and send), AutoPlay will examine the shared files to determine the type of content.</span></span> <span data-ttu-id="18ff4-357">Wenn Musikdateien gefunden werden, wird **PlayMusicFilesOnArrival** ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="18ff4-357">If music files are found, **PlayMusicFilesOnArrival** is raised.</span></span> |
| <span data-ttu-id="18ff4-358">Abspielen von Videos von einem Massenspeicher (Legacy)</span><span class="sxs-lookup"><span data-stu-id="18ff4-358">Using videos from mass storage (legacy)</span></span>                            | **<span data-ttu-id="18ff4-359">PlayVideoFilesOnArrival</span><span class="sxs-lookup"><span data-stu-id="18ff4-359">PlayVideoFilesOnArrival</span></span>**        | <span data-ttu-id="18ff4-360">Wenn der Benutzer in der Systemsteuerung unter „Automatische Wiedergabe“ die Option **Gewünschte Aktion für jeden Medientyp auswählen** aktiviert hat, überprüft die automatische Wiedergabe das am PC angeschlossene Volume, um den Inhaltstyp auf dem Datenträger zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="18ff4-360">If a user has enabled **Choose what to do with each type of media** in the AutoPlay Control Panel, AutoPlay will examine a volume connected to the PC to determine the type of content on the disk.</span></span> <span data-ttu-id="18ff4-361">Wenn Videodateien gefunden werden, wird **PlayVideoFilesOnArrival** ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="18ff4-361">When video files are found, **PlayVideoFilesOnArrival** is raised.</span></span> |
| <span data-ttu-id="18ff4-362">Empfangen von Videos mit Näherungsfreigabe (Koppeln und Senden)</span><span class="sxs-lookup"><span data-stu-id="18ff4-362">Receiving videos with Proximity Sharing (tap and send)</span></span>             | **<span data-ttu-id="18ff4-363">PlayVideoFilesOnArrival</span><span class="sxs-lookup"><span data-stu-id="18ff4-363">PlayVideoFilesOnArrival</span></span>**        | <span data-ttu-id="18ff4-364">Wenn Benutzer Inhalt mit Näherung (Koppeln und Senden) senden, prüft die automatische Wiedergabe die freigegebenen Dateien auf den Inhaltstyp.</span><span class="sxs-lookup"><span data-stu-id="18ff4-364">When users send content with using proximity (tap and send), AutoPlay will examine the shared files to determine the type of content.</span></span> <span data-ttu-id="18ff4-365">Wenn Videodateien gefunden werden, wird **PlayVideoFilesOnArrival** ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="18ff4-365">If video files are found, **PlayVideoFilesOnArrival** is raised.</span></span> |
| <span data-ttu-id="18ff4-366">Verarbeitung von gemischten Dateigruppen von einem verbundenen Gerät aus</span><span class="sxs-lookup"><span data-stu-id="18ff4-366">Handling mixed sets of files from a connected device</span></span>               | **<span data-ttu-id="18ff4-367">MixedContentOnArrival</span><span class="sxs-lookup"><span data-stu-id="18ff4-367">MixedContentOnArrival</span></span>**          | <span data-ttu-id="18ff4-368">Wenn der Benutzer in der Systemsteuerung unter „Automatische Wiedergabe“ die Option **Gewünschte Aktion für jeden Medientyp auswählen** aktiviert hat, überprüft die automatische Wiedergabe das am PC angeschlossene Volume, um den Inhaltstyp auf dem Datenträger zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="18ff4-368">If a user has enabled **Choose what to do with each type of media** in the AutoPlay Control Panel, AutoPlay will examine a volume connected to the PC to determine the type of content on the disk.</span></span> <span data-ttu-id="18ff4-369">Wenn kein bestimmter Inhaltstyp gefunden wird (z. B. Bilder), wird **MixedContentOnArrival** ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="18ff4-369">If no specific content type is found (for example, pictures), **MixedContentOnArrival** is raised.</span></span> |
| <span data-ttu-id="18ff4-370">Verarbeitung von gemischten Dateigruppen mit Näherungsfreigabe (Koppeln und Senden)</span><span class="sxs-lookup"><span data-stu-id="18ff4-370">Handling mixed sets of files with Proximity Sharing (tap and send)</span></span> | **<span data-ttu-id="18ff4-371">MixedContentOnArrival</span><span class="sxs-lookup"><span data-stu-id="18ff4-371">MixedContentOnArrival</span></span>**          | <span data-ttu-id="18ff4-372">Wenn Benutzer Inhalt mit Näherung (Koppeln und Senden) senden, prüft die automatische Wiedergabe die freigegebenen Dateien auf den Inhaltstyp.</span><span class="sxs-lookup"><span data-stu-id="18ff4-372">When users send content with using proximity (tap and send), AutoPlay will examine the shared files to determine the type of content.</span></span> <span data-ttu-id="18ff4-373">Wenn kein bestimmter Inhaltstyp gefunden wird (z. B. Bilder), wird **MixedContentOnArrival** ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="18ff4-373">If no specific content type is found (for example, pictures), **MixedContentOnArrival** is raised.</span></span> |
| <span data-ttu-id="18ff4-374">Verarbeitung von Videos von optischen Medien</span><span class="sxs-lookup"><span data-stu-id="18ff4-374">Handle video from optical media</span></span>                                    | **<span data-ttu-id="18ff4-375">PlayDVDMovieOnArrival</span><span class="sxs-lookup"><span data-stu-id="18ff4-375">PlayDVDMovieOnArrival</span></span>**<br />**<span data-ttu-id="18ff4-376">PlayBluRayOnArrival</span><span class="sxs-lookup"><span data-stu-id="18ff4-376">PlayBluRayOnArrival</span></span>**<br />**<span data-ttu-id="18ff4-377">PlayVideoCDMovieOnArrival</span><span class="sxs-lookup"><span data-stu-id="18ff4-377">PlayVideoCDMovieOnArrival</span></span>**<br />**<span data-ttu-id="18ff4-378">PlaySuperVideoCDMovieOnArrival</span><span class="sxs-lookup"><span data-stu-id="18ff4-378">PlaySuperVideoCDMovieOnArrival</span></span>** | <span data-ttu-id="18ff4-379">Wenn ein Datenträger in das optische Laufwerk eingelegt wird, prüft die automatische Wiedergabe die Dateien, um den Inhaltstyp zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="18ff4-379">When a disk is inserted into the optical drive, AutoPlay will examine the files to determine the type of content.</span></span> <span data-ttu-id="18ff4-380">Wenn eine Videodateien gefunden wurde, wird das Ereignis entsprechend dem Typ des optischen Datenträgers ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="18ff4-380">When video files are found, the event corresponding to the type of optical disk is raised.</span></span> |
| <span data-ttu-id="18ff4-381">Verarbeitung von Musik von optischen Medien</span><span class="sxs-lookup"><span data-stu-id="18ff4-381">Handle music from optical media</span></span>                                    | **<span data-ttu-id="18ff4-382">PlayCDAudioOnArrival</span><span class="sxs-lookup"><span data-stu-id="18ff4-382">PlayCDAudioOnArrival</span></span>**<br />**<span data-ttu-id="18ff4-383">PlayDVDAudioOnArrival</span><span class="sxs-lookup"><span data-stu-id="18ff4-383">PlayDVDAudioOnArrival</span></span>** | <span data-ttu-id="18ff4-384">Wenn ein Datenträger in das optische Laufwerk eingelegt wird, prüft die automatische Wiedergabe die Dateien, um den Inhaltstyp zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="18ff4-384">When a disk is inserted into the optical drive, AutoPlay will examine the files to determine the type of content.</span></span> <span data-ttu-id="18ff4-385">Wenn eine Musikdateien gefunden wurde, wird das Ereignis entsprechend dem Typ des optischen Datenträgers ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="18ff4-385">When music files are found, the event corresponding to the type of optical disk is raised.</span></span> |
| <span data-ttu-id="18ff4-386">Abspielen erweiterter Datenträger</span><span class="sxs-lookup"><span data-stu-id="18ff4-386">Play enhanced disks</span></span>                                                | **<span data-ttu-id="18ff4-387">PlayEnhancedCDOnArrival</span><span class="sxs-lookup"><span data-stu-id="18ff4-387">PlayEnhancedCDOnArrival</span></span>**<br />**<span data-ttu-id="18ff4-388">PlayEnhancedDVDOnArrival</span><span class="sxs-lookup"><span data-stu-id="18ff4-388">PlayEnhancedDVDOnArrival</span></span>** | <span data-ttu-id="18ff4-389">Wenn ein Datenträger in das optische Laufwerk eingelegt wird, prüft die automatische Wiedergabe die Dateien, um den Inhaltstyp zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="18ff4-389">When a disk is inserted into the optical drive, AutoPlay will examine the files to determine the type of content.</span></span> <span data-ttu-id="18ff4-390">Wenn ein erweiterter Datenträger gefunden wurde, wird das Ereignis entsprechend dem Typ des optischen Datenträgers ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="18ff4-390">When an enhanced disk is found, the event corresponding to the type of optical disk is raised.</span></span> |
| <span data-ttu-id="18ff4-391">Verarbeitung von beschreibbaren optischen Datenträgern</span><span class="sxs-lookup"><span data-stu-id="18ff4-391">Handle writeable optical disks</span></span>                                     | **<span data-ttu-id="18ff4-392">HandleCDBurningOnArrival</span><span class="sxs-lookup"><span data-stu-id="18ff4-392">HandleCDBurningOnArrival</span></span>** <br />**<span data-ttu-id="18ff4-393">HandleDVDBurningOnArrival</span><span class="sxs-lookup"><span data-stu-id="18ff4-393">HandleDVDBurningOnArrival</span></span>** <br />**<span data-ttu-id="18ff4-394">HandleBDBurningOnArrival</span><span class="sxs-lookup"><span data-stu-id="18ff4-394">HandleBDBurningOnArrival</span></span>** | <span data-ttu-id="18ff4-395">Wenn ein Datenträger in das optische Laufwerk eingelegt wird, prüft die automatische Wiedergabe die Dateien, um den Inhaltstyp zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="18ff4-395">When a disk is inserted into the optical drive, AutoPlay will examine the files to determine the type of content.</span></span> <span data-ttu-id="18ff4-396">Wenn ein Datenträger mit Schreibzugriff gefunden wurde, wird das Ereignis entsprechend dem Typ des optischen Datenträgers ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="18ff4-396">When a writable disk is found, the event corresponding to the type of optical disk is raised.</span></span> |
| <span data-ttu-id="18ff4-397">Verarbeitung von anderen Geräte- oder Volumeverbindungen</span><span class="sxs-lookup"><span data-stu-id="18ff4-397">Handle any other device or volume connection</span></span>                       | **<span data-ttu-id="18ff4-398">UnknownContentOnArrival</span><span class="sxs-lookup"><span data-stu-id="18ff4-398">UnknownContentOnArrival</span></span>**        | <span data-ttu-id="18ff4-399">Ausgelöst für alle Ereignisse, wenn Inhalt gefunden wurde, der mit einem der Inhaltsereignisse für die automatische Wiedergabe übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="18ff4-399">Raised for all events in case content is found that does not match any of the AutoPlay content events.</span></span> <span data-ttu-id="18ff4-400">Es wird nicht empfohlen, dieses Ereignis zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="18ff4-400">Use of this event is not recommended.</span></span> <span data-ttu-id="18ff4-401">Sie sollten Ihre Anwendung nur für bestimmte Ereignisse für die automatische Wiedergabe registrieren, die sie auch verarbeiten kann.</span><span class="sxs-lookup"><span data-stu-id="18ff4-401">You should only register your application for the specific AutoPlay events that it can handle.</span></span> |

<span data-ttu-id="18ff4-402">Mit dem Eintrag **CustomEvent** in der Datei „autorun.inf“ können Sie angeben, dass von der automatischen Wiedergabe ein benutzerdefiniertes Inhaltsereignis für die automatische Wiedergabe ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="18ff4-402">You can specify that AutoPlay raise a custom AutoPlay Content event using the **CustomEvent** entry in the autorun.inf file for a volume.</span></span> <span data-ttu-id="18ff4-403">Weitere Informationen finden Sie unter [Autorun.inf-Einträge](https://msdn.microsoft.com/library/windows/desktop/cc144200).</span><span class="sxs-lookup"><span data-stu-id="18ff4-403">For more info, see [Autorun.inf entries](https://msdn.microsoft.com/library/windows/desktop/cc144200).</span></span>

<span data-ttu-id="18ff4-404">Sie können Ihre App als Ereignishandler für Inhalte oder Geräte zur automatischen Wiedergabe registrieren, indem Sie der Datei „package.appxmanifest“ eine Erweiterung für die App hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="18ff4-404">You can register your app as an AutoPlay Content or AutoPlay Device event handler by adding an extension to the package.appxmanifest file for your app.</span></span> <span data-ttu-id="18ff4-405">Wenn Sie Visual Studio verwenden, können Sie auf der Registerkarte **Deklarationen** die Deklaration **Inhalt automatisch wiedergeben** oder **Gerät automatisch wiedergeben** hinzufügen. Wenn Sie die Datei „Package.appxmanifest” für Ihre App direkt bearbeiten, fügen Sie Ihrem Paketmanifest ein [**Extension**](https://msdn.microsoft.com/library/windows/apps/br211400)-Element hinzu, das entweder **windows.autoPlayContent** oder **windows.autoPlayDevice** als **Kategorie** angibt.</span><span class="sxs-lookup"><span data-stu-id="18ff4-405">If you are using Visual Studio, you can add an **AutoPlay Content** or **AutoPlay Device** declaration in the **Declarations** tab. If you are editing the package.appxmanifest file for your app directly, add an [**Extension**](https://msdn.microsoft.com/library/windows/apps/br211400) element to your package manifest that specifies either **windows.autoPlayContent** or **windows.autoPlayDevice** as the **Category**.</span></span> <span data-ttu-id="18ff4-406">So wird beispielsweise durch den folgenden Eintrag im Paketmanifest eine Erweiterung für **Inhalt automatisch wiedergeben** hinzugefügt, um die App als Handler für das **ShowPicturesOnArrival**-Ereignis zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="18ff4-406">For example, the following entry in the package manifest adds an **AutoPlay Content** extension to register the app as a handler for the **ShowPicturesOnArrival** event.</span></span>

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

 

 
