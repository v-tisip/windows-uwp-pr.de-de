---
author: TylerMSFT
title: Behandeln der Dateiaktivierung
description: Eine App kann als Standardhandler für einen bestimmten Dateityp registriert werden.
ms.assetid: A0F914C5-62BC-4FF7-9236-E34C5277C363
ms.author: twhitney
ms.date: 07/05/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
dev_langs:
- csharp
- vb
- cppwinrt
- cpp
ms.openlocfilehash: 9f1e41c3e09d9a711ce9174a5a658a55c7c44abd
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "5921012"
---
# <a name="handle-file-activation"></a><span data-ttu-id="3a8ab-104">Behandeln der Dateiaktivierung</span><span class="sxs-lookup"><span data-stu-id="3a8ab-104">Handle file activation</span></span>

**<span data-ttu-id="3a8ab-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="3a8ab-105">Important APIs</span></span>**

-   [**<span data-ttu-id="3a8ab-106">Windows.ApplicationModel.Activation.FileActivatedEventArgs</span><span class="sxs-lookup"><span data-stu-id="3a8ab-106">Windows.ApplicationModel.Activation.FileActivatedEventArgs</span></span>**](https://msdn.microsoft.com/library/windows/apps/br224716)
-   [**<span data-ttu-id="3a8ab-107">Windows.UI.Xaml.Application.OnFileActivated</span><span class="sxs-lookup"><span data-stu-id="3a8ab-107">Windows.UI.Xaml.Application.OnFileActivated</span></span>**](https://msdn.microsoft.com/library/windows/apps/br242331)

<span data-ttu-id="3a8ab-108">Ihre app kann registrieren, damit der Standardhandler für einen bestimmten Dateityp wird.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-108">Your app can register to become the default handler for a certain file type.</span></span> <span data-ttu-id="3a8ab-109">Sowohl Windows-Desktopanwendungen als auch UWP-Apps (Universelle Windows-Plattform) können als Standarddateihandler registriert werden.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-109">Both Windows desktop applications and Universal Windows Platform (UWP) apps can register to be a default file handler.</span></span> <span data-ttu-id="3a8ab-110">Wenn Ihre App vom Benutzer als Standardhandler für einen bestimmten Dateityp ausgewählt wird, wird sie dann aktiviert, wenn der Dateityp gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-110">If the user chooses your app as the default handler for a certain file type, your app will be activated when that type of file is launched.</span></span>

<span data-ttu-id="3a8ab-111">Wir empfehlen, die Registrierung für einen Dateityp nur durchzuführen, wenn davon auszugehen ist, dass alle entsprechenden Vorgänge für einen bestimmten Dateityp verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-111">We recommend that you only register for a file type if you expect to handle all file launches for that type of file.</span></span> <span data-ttu-id="3a8ab-112">Wenn der Dateityp von Ihrer App nur intern verwendet wird, ist die Registrierung eines Standardhandlers nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-112">If your app only needs to use the file type internally, then you don't need to register to be the default handler.</span></span> <span data-ttu-id="3a8ab-113">Wenn Sie sich entscheiden, die Registrierung für eine bestimmten Dateityp durchzuführen, müssen Sie die entsprechenden Funktionen bereitstellen, die vom Benutzer bei der Aktivierung für diesen Dateityp erwartet werden.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-113">If you do choose to register for a file type, you must provide the end user with the functionality that is expected when your app is activated for that file type.</span></span> <span data-ttu-id="3a8ab-114">Beispielsweise kann eine Bildanzeige-App für das Anzeigen des Dateityps JPG registriert werden.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-114">For example, a picture viewer app may register to display a .jpg file.</span></span> <span data-ttu-id="3a8ab-115">Weitere Informationen zu Dateizuordnungen finden Sie unter [Richtlinien für Dateitypen und URIs](https://msdn.microsoft.com/library/windows/apps/hh700321).</span><span class="sxs-lookup"><span data-stu-id="3a8ab-115">For more info on file associations, see [Guidelines for file types and URIs](https://msdn.microsoft.com/library/windows/apps/hh700321).</span></span>

<span data-ttu-id="3a8ab-116">Die folgenden Schritte zeigen, wie Sie den benutzerdefinierten Dateityp „.alsdk“ registrieren und Ihre App aktivieren, wenn der Benutzer eine ALSDK-Datei startet.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-116">These steps show how to register for a custom file type, .alsdk, and how to activate your app when the user launches an .alsdk file.</span></span>

> <span data-ttu-id="3a8ab-117">**Hinweis:** In UWP-apps bestimmte URIs und Dateierweiterungen für die Verwendung durch vorinstallierte apps und das Betriebssystem reserviert sind.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-117">**Note**In UWP apps, certain URIs and file extensions are reserved for use by built-in apps and the operating system.</span></span> <span data-ttu-id="3a8ab-118">Versuche, die App mit einem reservierten URI oder einer reservierten Dateierweiterung zu registrieren, werden ignoriert.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-118">Attempts to register your app with a reserved URI or file extension will be ignored.</span></span> <span data-ttu-id="3a8ab-119">Weitere Informationen finden Sie unter [Reservierte Datei- und URI-Schemanamen](reserved-uri-scheme-names.md).</span><span class="sxs-lookup"><span data-stu-id="3a8ab-119">For more information, see [Reserved file and URI scheme names](reserved-uri-scheme-names.md).</span></span>

## <a name="step-1-specify-the-extension-point-in-the-package-manifest"></a><span data-ttu-id="3a8ab-120">Schritt 1: Angeben des Erweiterungspunkts im Paketmanifest</span><span class="sxs-lookup"><span data-stu-id="3a8ab-120">Step 1: Specify the extension point in the package manifest</span></span>

<span data-ttu-id="3a8ab-121">Die App empfängt nur für die im Paketmanifest angegebenen Dateierweiterungen Aktivierungsereignisse.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-121">The app receives activation events only for the file extensions listed in the package manifest.</span></span> <span data-ttu-id="3a8ab-122">Im Folgenden wird beschrieben, wie Sie festlegen, dass die App Dateien mit der Erweiterung `.alsdk` behandelt.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-122">Here's how you indicate that your app handles the files with the `.alsdk` extension.</span></span>

1.  <span data-ttu-id="3a8ab-123">Doppelklicken Sie im **Projektmappen-Explorer** auf „package.appxmanifest“, um den Manifest-Designer zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-123">In the **Solution Explorer**, double-click package.appxmanifest to open the manifest designer.</span></span> <span data-ttu-id="3a8ab-124">Wählen Sie die Registerkarte **Deklarationen** und dann in der Dropdownliste **Verfügbare Deklarationen** die Option **Dateitypzuordnungen** aus, und klicken Sie dann auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-124">Select the **Declarations** tab and in the **Available Declarations** drop-down, select **File Type Associations** and then click **Add**.</span></span> <span data-ttu-id="3a8ab-125">Ausführliche Informationen zu Bezeichnern, die von Dateizuordnungen verwendet werden, finden Sie unter [ProgIDs](https://msdn.microsoft.com/library/windows/desktop/cc144152).</span><span class="sxs-lookup"><span data-stu-id="3a8ab-125">See [Programmatic Identifiers](https://msdn.microsoft.com/library/windows/desktop/cc144152) for more details of identifiers used by file associations.</span></span>

    <span data-ttu-id="3a8ab-126">Es folgt eine kurze Beschreibung der Felder, die Sie im Manifest-Designer ausfüllen können:</span><span class="sxs-lookup"><span data-stu-id="3a8ab-126">Here is a brief description of each of the fields that you may fill in the manifest designer:</span></span>

| <span data-ttu-id="3a8ab-127">Feld</span><span class="sxs-lookup"><span data-stu-id="3a8ab-127">Field</span></span> | <span data-ttu-id="3a8ab-128">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3a8ab-128">Description</span></span> |
|------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **<span data-ttu-id="3a8ab-129">Anzeigename</span><span class="sxs-lookup"><span data-stu-id="3a8ab-129">Display Name</span></span>** | <span data-ttu-id="3a8ab-130">Geben Sie den Anzeigenamen für eine Gruppe von Dateitypen an.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-130">Specify the display name for a group of file types.</span></span> <span data-ttu-id="3a8ab-131">Anhand des Anzeigenamens wird in der **Systemsteuerung** unter [Standardprogramme festlegen](https://msdn.microsoft.com/library/windows/desktop/cc144154) der Dateityp identifiziert.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-131">The display name is used to identify the file type in the [Set Default Programs](https://msdn.microsoft.com/library/windows/desktop/cc144154) on the **Control Panel**.</span></span> |
| **<span data-ttu-id="3a8ab-132">Logo</span><span class="sxs-lookup"><span data-stu-id="3a8ab-132">Logo</span></span>** | <span data-ttu-id="3a8ab-133">Geben Sie das Logo zur Identifikation des Dateityps auf dem Desktop in der **Systemsteuerung** unter [Standardprogramme festlegen](https://msdn.microsoft.com/library/windows/desktop/cc144154) an.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-133">Specify the logo that is used to identify the file type on the desktop and in the [Set Default Programs](https://msdn.microsoft.com/library/windows/desktop/cc144154) on the **Control Panel**.</span></span> <span data-ttu-id="3a8ab-134">Wenn kein Logo angegeben wird, wird das kleine Logo der Anwendung verwendet.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-134">If no Logo is specified, the application’s small logo is used.</span></span> |
| **<span data-ttu-id="3a8ab-135">Infotipp</span><span class="sxs-lookup"><span data-stu-id="3a8ab-135">Info Tip</span></span>** | <span data-ttu-id="3a8ab-136">Geben Sie den [Infotipp](https://msdn.microsoft.com/library/windows/desktop/cc144152) für eine Gruppe von Dateitypen an.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-136">Specify the [info tip](https://msdn.microsoft.com/library/windows/desktop/cc144152) for a group of file types.</span></span> <span data-ttu-id="3a8ab-137">Diese QuickInfo wird angezeigt, wenn Benutzer mit der Maus auf das Symbol für eine Datei dieses Typs zeigen.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-137">This tool tip text appears when the user hovers on the icon for a file of this type.</span></span> |
| **<span data-ttu-id="3a8ab-138">Name</span><span class="sxs-lookup"><span data-stu-id="3a8ab-138">Name</span></span>** | <span data-ttu-id="3a8ab-139">Wählen Sie einen Namen für eine Gruppe von Dateitypen aus, die identische Anzeigenamen, Logos, Infotipps und Bearbeitungsflags verwenden.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-139">Choose a name for a group of file types that share the same display name, logo, info tip, and edit flags.</span></span> <span data-ttu-id="3a8ab-140">Wählen Sie einen Gruppennamen aus, der auch nach App-Updates unverändert bleiben kann.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-140">Choose a group name that can stay the same across app updates.</span></span> <span data-ttu-id="3a8ab-141">**Hinweis**  Der Name darf nur aus Kleinbuchstaben bestehen.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-141">**Note**  The Name must be in all lower case letters.</span></span> |
| **<span data-ttu-id="3a8ab-142">Inhaltstyp</span><span class="sxs-lookup"><span data-stu-id="3a8ab-142">Content Type</span></span>** | <span data-ttu-id="3a8ab-143">Geben Sie den MIME-Inhaltstyp, z.B. **image/jpeg**, für einen bestimmten Dateityp an.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-143">Specify the MIME content type, such as **image/jpeg**, for a particular file type.</span></span> <span data-ttu-id="3a8ab-144">**Wichtiger Hinweis zu zulässigen Inhaltstypen:** Dies ist eine alphabetische Liste der MIME-Inhaltstypen, die Sie nicht in das Paketmanifest eingeben können, da sie entweder reserviert oder unzulässig sind: **application/force-download**, **application/octet-stream**, **application/unknown**, **application/x-msdownload**.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-144">**Important Note about allowed content types:** Here is an alphabetic list of MIME content types that you cannot enter into the package manifest because they are either reserved or forbidden: **application/force-download**, **application/octet-stream**, **application/unknown**, **application/x-msdownload**.</span></span> |
| **<span data-ttu-id="3a8ab-145">Dateityp</span><span class="sxs-lookup"><span data-stu-id="3a8ab-145">File type</span></span>** | <span data-ttu-id="3a8ab-146">Geben Sie den Dateityp, für den die Registrierung durchgeführt werden soll, mit vorangestelltem Punkt an, z.B. „.jpeg“.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-146">Specify the file type to register for, preceded by a period, for example, “.jpeg”.</span></span> <span data-ttu-id="3a8ab-147">**Reservierte und unzulässige Dateitypen:** Eine alphabetische Liste der Dateitypen für vorinstallierte Apps, die Sie nicht für Ihre UWP-Apps registrieren können, da diese entweder reserviert oder unzulässig sind, finden Sie unter [Reservierte URI-Schemanamen und Dateitypen](reserved-uri-scheme-names.md).</span><span class="sxs-lookup"><span data-stu-id="3a8ab-147">**Reserved and forbidden file types:** See [Reserved URI scheme names and file types](reserved-uri-scheme-names.md) for an alphabetic list of file types for built-in apps that you can't register for your UWP apps because they are either reserved or forbidden.</span></span> |

2.  <span data-ttu-id="3a8ab-148">Geben Sie `alsdk` in das Feld **Name** ein.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-148">Enter `alsdk` as the **Name**.</span></span>
3.  <span data-ttu-id="3a8ab-149">Geben Sie `.alsdk` als **Dateityp** ein.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-149">Enter `.alsdk` as the **File Type**.</span></span>
4.  <span data-ttu-id="3a8ab-150">Geben Sie „images\\Icon.png“ als Logo ein.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-150">Enter “images\\Icon.png” as the Logo.</span></span>
5.  <span data-ttu-id="3a8ab-151">Drücken Sie STRG+S, um die an „package.appxmanifest“ vorgenommenen Änderungen zu speichern.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-151">Press Ctrl+S to save the change to package.appxmanifest.</span></span>

<span data-ttu-id="3a8ab-152">Die obigen Schritte fügen dem Paketmanifest ein [**Extension**](https://msdn.microsoft.com/library/windows/apps/br211400)-Element wie das unten dargestellte hinzu.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-152">The steps above add an [**Extension**](https://msdn.microsoft.com/library/windows/apps/br211400) element like this one to the package manifest.</span></span> <span data-ttu-id="3a8ab-153">Die **windows.fileTypeAssociation**-Kategorie gibt an, dass die App Dateien mit der Erweiterung `.alsdk` behandelt.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-153">The **windows.fileTypeAssociation** category indicates that the app handles files with the `.alsdk` extension.</span></span>

```xml
      <Extensions>
        <uap:Extension Category="windows.fileTypeAssociation">
          <uap:FileTypeAssociation Name="alsdk">
            <uap:Logo>images\icon.png</uap:Logo>
            <uap:SupportedFileTypes>
              <uap:FileType>.alsdk</uap:FileType>
            </uap:SupportedFileTypes>
          </uap:FileTypeAssociation>
        </uap:Extension>
      </Extensions>
```

## <a name="step-2-add-the-proper-icons"></a><span data-ttu-id="3a8ab-154">Schritt 2: Hinzufügen der geeigneten Symbole</span><span class="sxs-lookup"><span data-stu-id="3a8ab-154">Step 2: Add the proper icons</span></span>

<span data-ttu-id="3a8ab-155">Die Symbole von Apps, die für einen Dateityp zum Standard werden, werden an verschiedenen Stellen innerhalb des Systems angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-155">Apps that become the default for a file type have their icons displayed in various places throughout the system.</span></span> <span data-ttu-id="3a8ab-156">Diese Symbole werden z.B. an folgenden Stellen angezeigt:</span><span class="sxs-lookup"><span data-stu-id="3a8ab-156">For example, these icons are shown in:</span></span>

-   <span data-ttu-id="3a8ab-157">Anzeige der Elemente, Kontextmenüs, Menüband in Windows Explorer</span><span class="sxs-lookup"><span data-stu-id="3a8ab-157">Windows Explorer Items View, context menus, and the Ribbon</span></span>
-   <span data-ttu-id="3a8ab-158">Standardprogramme in der Systemsteuerung</span><span class="sxs-lookup"><span data-stu-id="3a8ab-158">Default programs Control Panel</span></span>
-   <span data-ttu-id="3a8ab-159">Dateiauswahl</span><span class="sxs-lookup"><span data-stu-id="3a8ab-159">File picker</span></span>
-   <span data-ttu-id="3a8ab-160">Suchergebnisse auf dem Startbildschirm</span><span class="sxs-lookup"><span data-stu-id="3a8ab-160">Search results on the Start screen</span></span>

<span data-ttu-id="3a8ab-161">Fügen Sie ein 44 x 44-Symbol in das Projekt ein, damit Ihr Logo an diesen Positionen angezeigt werden kann.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-161">Include a 44x44 icon with your project so that your logo can appear in those locations.</span></span> <span data-ttu-id="3a8ab-162">Stimmen Sie das Erscheinungsbild des Logos der App-Kachel ab, und verwenden Sie die Hintergrundfarbe der App, anstatt das Symbol transparent darzustellen.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-162">Match the look of the app tile logo and use your app's background color rather than making the icon transparent.</span></span> <span data-ttu-id="3a8ab-163">Erweitern Sie das Logo bis zum Rand, ohne eine Auffüllung vorzunehmen.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-163">Have the logo extend to the edge without padding it.</span></span> <span data-ttu-id="3a8ab-164">Testen Sie Ihre Symbole auf weißem Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-164">Test your icons on white backgrounds.</span></span> <span data-ttu-id="3a8ab-165">Weitere Einzelheiten zu den Symbolen finden Sie unter [Richtlinien für Kacheln und Symbole](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/app-assets).</span><span class="sxs-lookup"><span data-stu-id="3a8ab-165">See [Guidelines for tile and icon assets](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/app-assets) for more details about icons.</span></span>

## <a name="step-3-handle-the-activated-event"></a><span data-ttu-id="3a8ab-166">Schritt 3: Behandeln des activated-Ereignisses</span><span class="sxs-lookup"><span data-stu-id="3a8ab-166">Step 3: Handle the activated event</span></span>

<span data-ttu-id="3a8ab-167">Der [**OnFileActivated**](https://msdn.microsoft.com/library/windows/apps/br242331)-Ereignishandler empfängt alle Dateiaktivierungsereignisse.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-167">The [**OnFileActivated**](https://msdn.microsoft.com/library/windows/apps/br242331) event handler receives all file activation events.</span></span>

```csharp
protected override void OnFileActivated(FileActivatedEventArgs args)
{
       // TODO: Handle file activation
       // The number of files received is args.Files.Size
       // The name of the first file is args.Files[0].Name
}
```

```vb
Protected Overrides Sub OnFileActivated(ByVal args As Windows.ApplicationModel.Activation.FileActivatedEventArgs)
      ' TODO: Handle file activation
      ' The number of files received is args.Files.Size
      ' The name of the first file is args.Files(0).Name
End Sub
```

```cppwinrt
void App::OnFileActivated(Windows::ApplicationModel::Activation::FileActivatedEventArgs const& args)
{
    // TODO: Handle file activation.
    auto numberOfFilesReceived{ args.Files().Size() };
    auto nameOfTheFirstFile{ args.Files().GetAt(0).Name() };
}
```

```cpp
void App::OnFileActivated(Windows::ApplicationModel::Activation::FileActivatedEventArgs^ args)
{
    // TODO: Handle file activation
    // The number of files received is args->Files->Size
    // The name of the first file is args->Files->GetAt(0)->Name
}
```

> [!NOTE]
> <span data-ttu-id="3a8ab-168">Achten Sie darauf, dass beim Start über einen Dateivertrag der Benutzer über die Zurück-Schaltfläche zu dem Bildschirm zurückkehren muss, von dem aus die App gestartet wurde, und nicht zum vorherigen Inhalt der App.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-168">When launched via File Contract, make sure that Back button takes the user back to the screen that launched the app and not to the app's previous content.</span></span>

<span data-ttu-id="3a8ab-169">Es wird empfohlen, dass Sie einen neuen XAML- **Frame** für jedes Aktivierungsereignis erstellen, die eine neue Seite geöffnet wird.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-169">We recommend that you create a new XAML **Frame** for each activation event that opens a new page.</span></span> <span data-ttu-id="3a8ab-170">Auf diese Weise nicht der navigationsbackstack für den neuen XAML-Frame keinen vorherigen Inhalt enthalten, der die app im aktuellen Fenster beim Anhalten.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-170">That way, the navigation backstack for the new XAML Frame doesn't contain any previous content that the app might have on the current window when suspended.</span></span> <span data-ttu-id="3a8ab-171">Wenn Sie einen einzelnen XAML- **Frame** für den Start und Dateiverträge verwenden möchten, sollten Sie die Seiten im navigationsjournal der **Frame**vor dem Navigieren zu einer neuen Seite löschen.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-171">If you decide to use a single XAML **Frame** for Launch and for File Contracts, then you should clear the pages in the **Frame**'s navigation journal before navigating to a new page.</span></span>

<span data-ttu-id="3a8ab-172">Wenn Ihre app über dateiaktivierung gestartet wird, sollten Sie überlegen, einschließlich Benutzeroberfläche, die der Benutzer zur ersten Seite der app zurückkehren kann.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-172">When your app is launched via File activation, you should consider including UI that allows the user to go back to the top page of the app.</span></span>

## <a name="remarks"></a><span data-ttu-id="3a8ab-173">Anmerkungen</span><span class="sxs-lookup"><span data-stu-id="3a8ab-173">Remarks</span></span>

<span data-ttu-id="3a8ab-174">Die empfangenen Dateien stammen unter Umständen aus einer nicht vertrauenswürdigen Quelle.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-174">The files that you receive could come from an untrusted source.</span></span> <span data-ttu-id="3a8ab-175">Wir empfehlen, den Inhalt einer Datei zu überprüfen, bevor Sie sie weiter verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="3a8ab-175">We recommend that you validate the content of a file before taking action on it.</span></span> <span data-ttu-id="3a8ab-176">Weitere Informationen zur Eingabeüberprüfung finden Sie unter [Schreiben von sicherem Code](http://go.microsoft.com/fwlink/p/?LinkID=142053).</span><span class="sxs-lookup"><span data-stu-id="3a8ab-176">For more info on input validation, see [Writing Secure Code](http://go.microsoft.com/fwlink/p/?LinkID=142053)</span></span>

## <a name="related-topics"></a><span data-ttu-id="3a8ab-177">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="3a8ab-177">Related topics</span></span>

### <a name="complete-example"></a><span data-ttu-id="3a8ab-178">Vollständiges Beispiel</span><span class="sxs-lookup"><span data-stu-id="3a8ab-178">Complete example</span></span>

* [<span data-ttu-id="3a8ab-179">Beispiel für Assoziationsstart</span><span class="sxs-lookup"><span data-stu-id="3a8ab-179">Association launching sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=231484)

### <a name="concepts"></a><span data-ttu-id="3a8ab-180">Konzepte</span><span class="sxs-lookup"><span data-stu-id="3a8ab-180">Concepts</span></span>

* [<span data-ttu-id="3a8ab-181">Standardprogramme</span><span class="sxs-lookup"><span data-stu-id="3a8ab-181">Default Programs</span></span>](https://msdn.microsoft.com/library/windows/desktop/cc144154)
* [<span data-ttu-id="3a8ab-182">Dateityp- und Protokollzuordnungsmodell</span><span class="sxs-lookup"><span data-stu-id="3a8ab-182">File Type and Protocol Associations Model</span></span>](https://msdn.microsoft.com/library/windows/desktop/hh848047)

### <a name="tasks"></a><span data-ttu-id="3a8ab-183">Aufgaben</span><span class="sxs-lookup"><span data-stu-id="3a8ab-183">Tasks</span></span>

* [<span data-ttu-id="3a8ab-184">Starten der Standard-App für eine Datei</span><span class="sxs-lookup"><span data-stu-id="3a8ab-184">Launch the default app for a file</span></span>](launch-the-default-app-for-a-file.md)
* [<span data-ttu-id="3a8ab-185">Behandeln der URI-Aktivierung</span><span class="sxs-lookup"><span data-stu-id="3a8ab-185">Handle URI activation</span></span>](handle-uri-activation.md)

### <a name="guidelines"></a><span data-ttu-id="3a8ab-186">Richtlinien</span><span class="sxs-lookup"><span data-stu-id="3a8ab-186">Guidelines</span></span>

* [<span data-ttu-id="3a8ab-187">Richtlinien für Dateitypen und URIs</span><span class="sxs-lookup"><span data-stu-id="3a8ab-187">Guidelines for file types and URIs</span></span>](https://msdn.microsoft.com/library/windows/apps/hh700321)

### <a name="reference"></a><span data-ttu-id="3a8ab-188">Referenz</span><span class="sxs-lookup"><span data-stu-id="3a8ab-188">Reference</span></span>
* [<span data-ttu-id="3a8ab-189">Windows.ApplicationModel.Activation.FileActivatedEventArgs</span><span class="sxs-lookup"><span data-stu-id="3a8ab-189">Windows.ApplicationModel.Activation.FileActivatedEventArgs</span></span>](https://msdn.microsoft.com/library/windows/apps/br224716)
* [<span data-ttu-id="3a8ab-190">Windows.UI.Xaml.Application.OnFileActivated</span><span class="sxs-lookup"><span data-stu-id="3a8ab-190">Windows.UI.Xaml.Application.OnFileActivated</span></span>](https://msdn.microsoft.com/library/windows/apps/br242331)
