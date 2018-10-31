---
author: TylerMSFT
title: Starten der Standard-App für eine Datei
description: Erfahren Sie, wie Sie die Standard-App für eine Datei starten.
ms.assetid: BB45FCAF-DF93-4C99-A8B5-59B799C7BD98
ms.author: twhitney
ms.date: 07/05/2018
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 736018fbf966b547c3dd41e245149d498c1231e3
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5866762"
---
# <a name="launch-the-default-app-for-a-file"></a><span data-ttu-id="77380-104">Starten der Standard-App für eine Datei</span><span class="sxs-lookup"><span data-stu-id="77380-104">Launch the default app for a file</span></span>

**<span data-ttu-id="77380-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="77380-105">Important APIs</span></span>**

-   [**<span data-ttu-id="77380-106">Windows.System.Launcher.LaunchFileAsync</span><span class="sxs-lookup"><span data-stu-id="77380-106">Windows.System.Launcher.LaunchFileAsync</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh701461)

<span data-ttu-id="77380-107">Hier erfahren Sie, wie Sie die Standard-App für eine Datei starten.</span><span class="sxs-lookup"><span data-stu-id="77380-107">Learn how to launch the default app for a file.</span></span> <span data-ttu-id="77380-108">Viele Apps müssen mit Dateien arbeiten, die sie nicht selbst behandeln können.</span><span class="sxs-lookup"><span data-stu-id="77380-108">Many apps need to work with files that they can't handle themselves.</span></span> <span data-ttu-id="77380-109">E-Mail-Apps erhalten beispielsweise eine Vielzahl von Dateitypen und müssen über eine Möglichkeit verfügen, diese Dateien mit ihren Standardhandlern zu starten.</span><span class="sxs-lookup"><span data-stu-id="77380-109">For example, e-mail apps receive a variety of file types and need a way to launch these files in their default handlers.</span></span> <span data-ttu-id="77380-110">In den folgenden Schritten erfahren Sie, wie Sie den Standardhandler für eine Datei, die Ihre App nicht selbst behandeln kann, mithilfe der [**Windows.System.Launcher**](https://msdn.microsoft.com/library/windows/apps/br241801)-API starten.</span><span class="sxs-lookup"><span data-stu-id="77380-110">These steps show how to use the [**Windows.System.Launcher**](https://msdn.microsoft.com/library/windows/apps/br241801) API to launch the default handler for a file that your app can't handle itself.</span></span>

## <a name="get-the-file-object"></a><span data-ttu-id="77380-111">Abrufen des Dateiobjekts</span><span class="sxs-lookup"><span data-stu-id="77380-111">Get the file object</span></span>

<span data-ttu-id="77380-112">Rufen Sie zunächst ein [**Windows.Storage.StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171)-Objekt für die Datei ab.</span><span class="sxs-lookup"><span data-stu-id="77380-112">First, get a [**Windows.Storage.StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) object for the file.</span></span>

<span data-ttu-id="77380-113">Wenn die Datei im Paket für die App enthalten ist, können Sie die [**Package.InstalledLocation**](https://msdn.microsoft.com/library/windows/apps/br224681)-Eigenschaft verwenden, um ein [**Windows.Storage.StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230)-Objekt abzurufen, und die [**Windows.Storage.StorageFolder.GetFileAsync**](https://msdn.microsoft.com/library/windows/apps/br227272)-Methode, um das [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171)-Objekt abzurufen.</span><span class="sxs-lookup"><span data-stu-id="77380-113">If the file is included in the package for your app, you can use the [**Package.InstalledLocation**](https://msdn.microsoft.com/library/windows/apps/br224681) property to get a [**Windows.Storage.StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230) object and the [**Windows.Storage.StorageFolder.GetFileAsync**](https://msdn.microsoft.com/library/windows/apps/br227272) method to get the [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) object.</span></span>

<span data-ttu-id="77380-114">Falls sich die Datei in einem bekannten Ordner befindet, können Sie die Eigenschaften der [**Windows.Storage.KnownFolders**](https://msdn.microsoft.com/library/windows/apps/br227151)-Klasse verwenden, um ein [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230)-Objekt abzurufen, und die [**GetFileAsync**](https://msdn.microsoft.com/library/windows/apps/br227272)-Methode, um das [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171)-Objekt abzurufen.</span><span class="sxs-lookup"><span data-stu-id="77380-114">If the file is in a known folder, you can use the properties of the [**Windows.Storage.KnownFolders**](https://msdn.microsoft.com/library/windows/apps/br227151) class to get a [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230) and the [**GetFileAsync**](https://msdn.microsoft.com/library/windows/apps/br227272) method to get the [**StorageFile**](https://msdn.microsoft.com/library/windows/apps/br227171) object.</span></span>

## <a name="launch-the-file"></a><span data-ttu-id="77380-115">Starten der Datei</span><span class="sxs-lookup"><span data-stu-id="77380-115">Launch the file</span></span>

<span data-ttu-id="77380-116">Windows stellt mehrere verschiedene Optionen zum Starten des Standardhandlers für eine Datei bereit.</span><span class="sxs-lookup"><span data-stu-id="77380-116">Windows provides several different options for launching the default handler for a file.</span></span> <span data-ttu-id="77380-117">Diese Optionen werden in diesem Diagramm und den anschließenden Abschnitten ausführlich beschrieben.</span><span class="sxs-lookup"><span data-stu-id="77380-117">These options are described in this chart and in the sections that follow.</span></span>

| <span data-ttu-id="77380-118">Option</span><span class="sxs-lookup"><span data-stu-id="77380-118">Option</span></span> | <span data-ttu-id="77380-119">Methode</span><span class="sxs-lookup"><span data-stu-id="77380-119">Method</span></span> | <span data-ttu-id="77380-120">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="77380-120">Description</span></span> |
|--------|--------|-------------|
| <span data-ttu-id="77380-121">Standardstart</span><span class="sxs-lookup"><span data-stu-id="77380-121">Default launch</span></span> | [**<span data-ttu-id="77380-122">LaunchFileAsync(IStorageFile)</span><span class="sxs-lookup"><span data-stu-id="77380-122">LaunchFileAsync(IStorageFile)</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh701471) | <span data-ttu-id="77380-123">Starten Sie die angegebene Datei mit dem Standardhandler.</span><span class="sxs-lookup"><span data-stu-id="77380-123">Launch the specified file with the default handler.</span></span> |
| <span data-ttu-id="77380-124">Starten über „Öffnen mit“</span><span class="sxs-lookup"><span data-stu-id="77380-124">Open With launch</span></span> | [**<span data-ttu-id="77380-125">LaunchFileAsync(IStorageFile, LauncherOptions)</span><span class="sxs-lookup"><span data-stu-id="77380-125">LaunchFileAsync(IStorageFile, LauncherOptions)</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh701465) | <span data-ttu-id="77380-126">Starten Sie die angegebene Datei und lassen Sie den Benutzer den Handler über das Dialogfeld „Öffnen mit“ auswählen.</span><span class="sxs-lookup"><span data-stu-id="77380-126">Launch the specified file letting the user pick the handler through the Open With dialog.</span></span> |
| <span data-ttu-id="77380-127">Start mit einem empfohlenen App-Fallback</span><span class="sxs-lookup"><span data-stu-id="77380-127">Launch with a recommended app fallback</span></span> | [**<span data-ttu-id="77380-128">LaunchFileAsync(IStorageFile, LauncherOptions)</span><span class="sxs-lookup"><span data-stu-id="77380-128">LaunchFileAsync(IStorageFile, LauncherOptions)</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh701465) | <span data-ttu-id="77380-129">Starten Sie die angegebene Datei mit dem Standardhandler.</span><span class="sxs-lookup"><span data-stu-id="77380-129">Launch the specified file with the default handler.</span></span> <span data-ttu-id="77380-130">Wenn kein Handler im System installiert ist, empfehlen Sie dem Benutzer eine App im Store.</span><span class="sxs-lookup"><span data-stu-id="77380-130">If no handler is installed on the system, recommend an app in the store to the user.</span></span> |
| <span data-ttu-id="77380-131">Starten mit einer gewünschten verbleibenden Ansicht</span><span class="sxs-lookup"><span data-stu-id="77380-131">Launch with a desired remaining view</span></span> | <span data-ttu-id="77380-132">[**LaunchFileAsync(IStorageFile, LauncherOptions)**](https://msdn.microsoft.com/library/windows/apps/hh701465) (nur Windows)</span><span class="sxs-lookup"><span data-stu-id="77380-132">[**LaunchFileAsync(IStorageFile, LauncherOptions)**](https://msdn.microsoft.com/library/windows/apps/hh701465) (Windows-only)</span></span> | <span data-ttu-id="77380-133">Starten Sie die angegebene Datei mit dem Standardhandler.</span><span class="sxs-lookup"><span data-stu-id="77380-133">Launch the specified file with the default handler.</span></span> <span data-ttu-id="77380-134">Geben Sie an, wie lange die App nach dem Start auf dem Bildschirm verbleiben soll. Fordern Sie zudem eine bestimmte Fenstergröße an.</span><span class="sxs-lookup"><span data-stu-id="77380-134">Specify a preference to stay on screen after the launch and request a specific window size.</span></span> <span data-ttu-id="77380-135">[**LauncherOptions.DesiredRemainingView**](https://msdn.microsoft.com/library/windows/apps/dn298314) wird für die Mobilgerätefamilie nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="77380-135">[**LauncherOptions.DesiredRemainingView**](https://msdn.microsoft.com/library/windows/apps/dn298314) isn't supported on the mobile device family.</span></span> |

### <a name="default-launch"></a><span data-ttu-id="77380-136">Standardstart</span><span class="sxs-lookup"><span data-stu-id="77380-136">Default launch</span></span>

<span data-ttu-id="77380-137">Rufen Sie die [**Windows.System.Launcher.LaunchFileAsync(IStorageFile)**](https://msdn.microsoft.com/library/windows/apps/hh701471)-Methode auf, um die Standard-App zu starten.</span><span class="sxs-lookup"><span data-stu-id="77380-137">Call the [**Windows.System.Launcher.LaunchFileAsync(IStorageFile)**](https://msdn.microsoft.com/library/windows/apps/hh701471) method to launch the default app.</span></span> <span data-ttu-id="77380-138">In diesem Beispiel wird die [**Windows.Storage.StorageFolder.GetFileAsync**](https://msdn.microsoft.com/library/windows/apps/br227272)-Methode verwendet, um eine im App-Paket enthaltene Bilddatei zu starten.</span><span class="sxs-lookup"><span data-stu-id="77380-138">This example uses the [**Windows.Storage.StorageFolder.GetFileAsync**](https://msdn.microsoft.com/library/windows/apps/br227272) method to launch an image file, test.png, that is included in the app package.</span></span>

```csharp
async void DefaultLaunch()
{
   // Path to the file in the app package to launch
   string imageFile = @"images\test.png";
   
   var file = await Windows.ApplicationModel.Package.Current.InstalledLocation.GetFileAsync(imageFile);
   
   if (file != null)
   {
      // Launch the retrieved file
      var success = await Windows.System.Launcher.LaunchFileAsync(file);

      if (success)
      {
         // File launched
      }
      else
      {
         // File launch failed
      }
   }
   else
   {
      // Could not find file
   }
}
```

```vb
async Sub DefaultLaunch()
   ' Path to the file in the app package to launch
   Dim imageFile = "images\test.png"
   Dim file = await Windows.ApplicationModel.Package.Current.InstalledLocation.GetFileAsync(imageFile)
   
   If file IsNot Nothing Then
      ' Launch the retrieved file
      Dim success = await Windows.System.Launcher.LaunchFileAsync(file)

      If success Then
         ' File launched
      Else
         ' File launch failed
      End If
   Else
      ' Could not find file
   End If
End Sub
```

```cppwinrt
Windows::Foundation::IAsyncAction MainPage::DefaultLaunch()
{
    auto installFolder{ Windows::ApplicationModel::Package::Current().InstalledLocation() };

    Windows::Storage::StorageFile file{ co_await installFolder.GetFileAsync(L"images\\test.png") };

    if (file)
    {
        // Launch the retrieved file
        bool success = co_await Windows::System::Launcher::LaunchFileAsync(file);
        if (success)
        {
            // File launched
        }
        else
        {
            // File launch failed
        }
    }
    else
    {
        // Could not find file
    }
}
```

```cpp
void MainPage::DefaultLaunch()
{
   auto installFolder = Windows::ApplicationModel::Package::Current->InstalledLocation;

   concurrency::task<Windows::Storage::StorageFile^getFileOperation(installFolder->GetFileAsync("images\\test.png"));
   getFileOperation.then([](Windows::Storage::StorageFile^ file)
   {
      if (file != nullptr)
      {
         // Launch the retrieved file
         concurrency::task<bool> launchFileOperation(Windows::System::Launcher::LaunchFileAsync(file));
         launchFileOperation.then([](bool success)
         {
            if (success)
            {
               // File launched
            }
            else
            {
               // File launch failed
            }
         });
      }
      else
      {
         // Could not find file
      }
   });
}
```

### <a name="open-with-launch"></a><span data-ttu-id="77380-139">Starten über „Öffnen mit“</span><span class="sxs-lookup"><span data-stu-id="77380-139">Open With launch</span></span>

<span data-ttu-id="77380-140">Rufen Sie die [**Windows.System.Launcher.LaunchFileAsync(IStorageFile, LauncherOptions)**](https://msdn.microsoft.com/library/windows/apps/hh701465)-Methode mit dem [**LauncherOptions.DisplayApplicationPicker**](https://msdn.microsoft.com/library/windows/apps/hh701438)-Wert **true** auf, um die App zu starten, die der Benutzer im Dialogfeld **Öffnen mit** auswählt.</span><span class="sxs-lookup"><span data-stu-id="77380-140">Call the [**Windows.System.Launcher.LaunchFileAsync(IStorageFile, LauncherOptions)**](https://msdn.microsoft.com/library/windows/apps/hh701465) method with [**LauncherOptions.DisplayApplicationPicker**](https://msdn.microsoft.com/library/windows/apps/hh701438) set to **true** to launch the app that the user selects from the **Open With** dialog box.</span></span>

<span data-ttu-id="77380-141">Mit dem Dialogfeld **Öffnen mit** können Sie dem Benutzer das Auswählen einer anderen App als der Standard-App für einen bestimmten Dateityp ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="77380-141">We recommend that you use the **Open With** dialog box when the user may want to select an app other than the default for a particular file.</span></span> <span data-ttu-id="77380-142">Angenommen, Ihre App ermöglicht dem Benutzer das Aufrufen einer Bilddatei. In diesem Fall ist der Standardhandler wahrscheinlich eine Anzeige-App.</span><span class="sxs-lookup"><span data-stu-id="77380-142">For example, if your app allows the user to launch an image file, the default handler will likely be a viewer app.</span></span> <span data-ttu-id="77380-143">Nun kann es jedoch sein, dass der Benutzer die Datei nicht nur anzeigen, sondern auch bearbeiten möchte.</span><span class="sxs-lookup"><span data-stu-id="77380-143">In some cases, the user may want to edit the image instead of viewing it.</span></span> <span data-ttu-id="77380-144">Mit der Option **Öffnen mit** und einem alternativen Befehl in der **AppBar** oder in einem Kontextmenü können Sie dem Benutzer das Aufrufen des Dialogfelds **Öffnen mit** und das Auswählen einer entsprechenden Editor-App ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="77380-144">Use the **Open With** option along with an alternative command in the **AppBar** or in a context menu to let the user bring up the **Open With** dialog and select the editor app in these types of scenarios.</span></span>

![Das Dialogfeld „Öffnen mit“ für den Start einer PNG-Datei.](images/checkboxopenwithdialog.png)

```csharp
async void DefaultLaunch()
{
   // Path to the file in the app package to launch
      string imageFile = @"images\test.png";
      
   var file = await Windows.ApplicationModel.Package.Current.InstalledLocation.GetFileAsync(imageFile);

   if (file != null)
   {
      // Set the option to show the picker
      var options = new Windows.System.LauncherOptions();
      options.DisplayApplicationPicker = true;

      // Launch the retrieved file
      bool success = await Windows.System.Launcher.LaunchFileAsync(file, options);
      if (success)
      {
         // File launched
      }
      else
      {
         // File launch failed
      }
   }
   else
   {
      // Could not find file
   }
}
```

```vb
async Sub DefaultLaunch()

   ' Path to the file in the app package to launch
   Dim imageFile = "images\test.png"

   Dim file = await Windows.ApplicationModel.Package.Current.InstalledLocation.GetFileAsync(imageFile)

   If file IsNot Nothing Then
      ' Set the option to show the picker
      Dim options = Windows.System.LauncherOptions()
      options.DisplayApplicationPicker = True

      ' Launch the retrieved file
      Dim success = await Windows.System.Launcher.LaunchFileAsync(file)

      If success Then
         ' File launched
      Else
         ' File launch failed
      End If
   Else
      ' Could not find file
   End If
End Sub
```

```cppwinrt
Windows::Foundation::IAsyncAction MainPage::DefaultLaunch()
{
    auto installFolder{ Windows::ApplicationModel::Package::Current().InstalledLocation() };

    Windows::Storage::StorageFile file{ co_await installFolder.GetFileAsync(L"images\\test.png") };

    if (file)
    {
        // Set the option to show the picker
        Windows::System::LauncherOptions launchOptions;
        launchOptions.DisplayApplicationPicker(true);

        // Launch the retrieved file
        bool success = co_await Windows::System::Launcher::LaunchFileAsync(file, launchOptions);
        if (success)
        {
            // File launched
        }
        else
        {
            // File launch failed
        }
    }
    else
    {
        // Could not find file
    }
}
```

```cpp
void MainPage::DefaultLaunch()
{
   auto installFolder = Windows::ApplicationModel::Package::Current->InstalledLocation;

   concurrency::task<Windows::Storage::StorageFile^> getFileOperation(installFolder->GetFileAsync("images\\test.png"));
   getFileOperation.then([](Windows::Storage::StorageFile^ file)
   {
      if (file != nullptr)
      {
         // Set the option to show the picker
         auto launchOptions = ref new Windows::System::LauncherOptions();
         launchOptions->DisplayApplicationPicker = true;

         // Launch the retrieved file
         concurrency::task<bool> launchFileOperation(Windows::System::Launcher::LaunchFileAsync(file, launchOptions));
         launchFileOperation.then([](bool success)
         {
            if (success)
            {
               // File launched
            }
            else
            {
               // File launch failed
            }
         });
      }
      else
      {
         // Could not find file
      }
   });
}
```

**<span data-ttu-id="77380-148">Start mit einem empfohlenen App-Fallback</span><span class="sxs-lookup"><span data-stu-id="77380-148">Launch with a recommended app fallback</span></span>**

<span data-ttu-id="77380-149">Es kann jedoch sein, dass der Benutzer nicht über die erforderliche App zum Bearbeiten des aufgerufenen Dateityps verfügt.</span><span class="sxs-lookup"><span data-stu-id="77380-149">In some cases the user may not have an app installed to handle the file that you are launching.</span></span> <span data-ttu-id="77380-150">In diesen Fällen bietet Windows standardmäßig einen Link an, mit dessen Hilfe Benutzer im Store nach einer geeigneten App suchen können.</span><span class="sxs-lookup"><span data-stu-id="77380-150">By default, Windows will handle these cases by providing the user with a link to search for an appropriate app on the store.</span></span> <span data-ttu-id="77380-151">Wenn Sie dem Benutzer eine bestimmte App für dieses spezifische Szenario empfehlen möchten, können Sie die Empfehlung zusammen mit der Datei weitergeben, die gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="77380-151">If you would like to give the user a specific recommendation for which app to acquire in this scenario, you may do so by passing that recommendation along with the file that you are launching.</span></span> <span data-ttu-id="77380-152">Rufen Sie dazu die [**Windows.System.Launcher.launchFileAsync(IStorageFile, LauncherOptions)**](https://msdn.microsoft.com/library/windows/apps/hh701465)-Methode mit [**LauncherOptions.PreferredApplicationPackageFamilyName**](https://msdn.microsoft.com/library/windows/apps/hh965482) (festgelegt auf den Paketfamiliennamen der empfohlenen App im Store) auf.</span><span class="sxs-lookup"><span data-stu-id="77380-152">To do this, call the [**Windows.System.Launcher.launchFileAsync(IStorageFile, LauncherOptions)**](https://msdn.microsoft.com/library/windows/apps/hh701465) method with [**LauncherOptions.PreferredApplicationPackageFamilyName**](https://msdn.microsoft.com/library/windows/apps/hh965482) set to the package family name of the app in the Store that you want to recommend.</span></span> <span data-ttu-id="77380-153">Legen Sie anschließend [**LauncherOptions.PreferredApplicationDisplayName**](https://msdn.microsoft.com/library/windows/apps/hh965481) auf den Namen dieser App fest.</span><span class="sxs-lookup"><span data-stu-id="77380-153">Then, set the [**LauncherOptions.PreferredApplicationDisplayName**](https://msdn.microsoft.com/library/windows/apps/hh965481) to the name of that app.</span></span> <span data-ttu-id="77380-154">Diese Informationen werden von Windows verwendet, um die allgemeine Option zum Suchen einer App im Store durch die spezifische Option zum Verwenden der empfohlenen App im Store zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="77380-154">Windows will use this information to replace the general option to search for an app in the store with a specific option to acquire the recommended app from the Store.</span></span>

> [!NOTE]
> <span data-ttu-id="77380-155">Wenn Sie eine App empfehlen möchten, müssen Sie beide Optionen festlegen.</span><span class="sxs-lookup"><span data-stu-id="77380-155">You must set both of these options to recommend an app.</span></span> <span data-ttu-id="77380-156">Eine Festlegung der einen ohne die andere führt zu einem Fehler.</span><span class="sxs-lookup"><span data-stu-id="77380-156">Setting one without the other will result in a failure.</span></span>

![Das Dialogfeld „Öffnen mit“ für den Start einer „.contoso“-Datei.](images/howdoyouwanttoopen.png)

```csharp
async void DefaultLaunch()
{
   // Path to the file in the app package to launch
   string imageFile = @"images\test.contoso";

   // Get the image file from the package's image directory
   var file = await Windows.ApplicationModel.Package.Current.InstalledLocation.GetFileAsync(imageFile);

   if (file != null)
   {
      // Set the recommended app
      var options = new Windows.System.LauncherOptions();
      options.PreferredApplicationPackageFamilyName = "Contoso.FileApp_8wknc82po1e";
      options.PreferredApplicationDisplayName = "Contoso File App";

      // Launch the retrieved file pass in the recommended app
      // in case the user has no apps installed to handle the file
      bool success = await Windows.System.Launcher.LaunchFileAsync(file, options);
      if (success)
      {
         // File launched
      }
      else
      {
         // File launch failed
      }
   }
   else
   {
      // Could not find file
   }
}
```

```vb
async Sub DefaultLaunch()

   ' Path to the file in the app package to launch
   Dim imageFile = "images\test.contoso"

   ' Get the image file from the package's image directory
   Dim file = await Windows.ApplicationModel.Package.Current.InstalledLocation.GetFileAsync(imageFile)

   If file IsNot Nothing Then
      ' Set the recommended app
      Dim options = Windows.System.LauncherOptions()
      options.PreferredApplicationPackageFamilyName = "Contoso.FileApp_8wknc82po1e";
      options.PreferredApplicationDisplayName = "Contoso File App";

      ' Launch the retrieved file pass in the recommended app
      ' in case the user has no apps installed to handle the file
      Dim success = await Windows.System.Launcher.LaunchFileAsync(file)

      If success Then
         ' File launched
      Else
         ' File launch failed
      End If
   Else
      ' Could not find file
   End If
End Sub
```

```cppwinrt
Windows::Foundation::IAsyncAction MainPage::DefaultLaunch()
{
    auto installFolder{ Windows::ApplicationModel::Package::Current().InstalledLocation() };

    Windows::Storage::StorageFile file{ co_await installFolder.GetFileAsync(L"images\\test.png") };

    if (file)
    {
        // Set the recommended app
        Windows::System::LauncherOptions launchOptions;
        launchOptions.PreferredApplicationPackageFamilyName(L"Contoso.FileApp_8wknc82po1e");
        launchOptions.PreferredApplicationDisplayName(L"Contoso File App");

        // Launch the retrieved file, and pass in the recommended app
        // in case the user has no apps installed to handle the file.
        bool success = co_await Windows::System::Launcher::LaunchFileAsync(file, launchOptions);
        if (success)
        {
            // File launched
        }
        else
        {
            // File launch failed
        }
    }
    else
    {
        // Could not find file
    }
}
```

```cpp
void MainPage::DefaultLaunch()
{
   auto installFolder = Windows::ApplicationModel::Package::Current->InstalledLocation;

   concurrency::task<Windows::Storage::StorageFile^> getFileOperation(installFolder->GetFileAsync("images\\test.contoso"));
   getFileOperation.then([](Windows::Storage::StorageFile^ file)
   {
      if (file != nullptr)
      {
         // Set the recommended app
         auto launchOptions = ref new Windows::System::LauncherOptions();
         launchOptions->PreferredApplicationPackageFamilyName = "Contoso.FileApp_8wknc82po1e";
         launchOptions->PreferredApplicationDisplayName = "Contoso File App";
         
         // Launch the retrieved file pass, and in the recommended app
         // in case the user has no apps installed to handle the file.
         concurrency::task<bool> launchFileOperation(Windows::System::Launcher::LaunchFileAsync(file, launchOptions));
         launchFileOperation.then([](bool success)
         {
            if (success)
            {
               // File launched
            }
            else
            {
               // File launch failed
            }
         });
      }
      else
      {
         // Could not find file
      }
   });
}
```

### <a name="launch-with-a-desired-remaining-view-windows-only"></a><span data-ttu-id="77380-160">Starten mit einer gewünschten verbleibenden Ansicht (nur Windows)</span><span class="sxs-lookup"><span data-stu-id="77380-160">Launch with a Desired Remaining View (Windows-only)</span></span>

<span data-ttu-id="77380-161">Quell-Apps, die [**LaunchFileAsync**](https://msdn.microsoft.com/library/windows/apps/hh701461) aufrufen, können anfordern, nach dem Start einer Datei auf dem Bildschirm zu verbleiben.</span><span class="sxs-lookup"><span data-stu-id="77380-161">Source apps that call [**LaunchFileAsync**](https://msdn.microsoft.com/library/windows/apps/hh701461) can request that they remain on screen after a file launch.</span></span> <span data-ttu-id="77380-162">Standardmäßig wird von Windows versucht, den gesamten verfügbaren Speicher gleichmäßig zwischen der Quell- und der Ziel-App aufzuteilen, die die Datei verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="77380-162">By default, Windows attempts to share all available space equally between the source app and the target app that handles the file.</span></span> <span data-ttu-id="77380-163">Quell-Apps können die Eigenschaft [**DesiredRemainingView**](https://msdn.microsoft.com/library/windows/apps/dn298314) verwenden. Hiermit geben sie dem Betriebssystem an, mehr oder weniger des verfügbaren Speicherplatzes für ihr App-Fenster zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="77380-163">Source apps can use the [**DesiredRemainingView**](https://msdn.microsoft.com/library/windows/apps/dn298314) property to indicate to the operating system that they prefer their app window to take up more or less of the available space.</span></span> <span data-ttu-id="77380-164">**DesiredRemainingView** kann auch verwendet werden, um anzugeben, dass die Quell-App nach dem Start der Datei nicht auf dem Bildschirm verbleiben muss und vollständig durch die Ziel-App ersetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="77380-164">**DesiredRemainingView** can also be used to indicate that the source app does not need to remain on screen after the file launch and can be completely replaced by the target app.</span></span> <span data-ttu-id="77380-165">Mit dieser Eigenschaft wird nur die bevorzugte Fenstergröße der aufrufenden App angegeben.</span><span class="sxs-lookup"><span data-stu-id="77380-165">This property only specifies the preferred window size of the calling app.</span></span> <span data-ttu-id="77380-166">Es wird nicht das Verhalten anderer Apps angegeben, die ggf. zur gleichen Zeit auf dem Bildschirm angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="77380-166">It doesn't specify the behavior of other apps that may happen to also be on screen at the same time.</span></span>

> [!NOTE]
> <span data-ttu-id="77380-167">Von Windows werden mehrere unterschiedliche Faktoren in Betracht gezogen, wenn die endgültige Fenstergröße der Quell-App bestimmt wird. Dazu zählen beispielsweise die Einstellung der Quell-App, die Anzahl der Apps auf dem Bildschirm und die Bildschirmausrichtung.</span><span class="sxs-lookup"><span data-stu-id="77380-167">Windows takes into account multiple different factors when it determines the source app's final window size, for example, the preference of the source app, the number of apps on screen, the screen orientation, and so on.</span></span> <span data-ttu-id="77380-168">Das Festlegen von [**DesiredRemainingView**](https://msdn.microsoft.com/library/windows/apps/dn298314) garantiert kein bestimmtes Fensterverhalten für die Quell-App.</span><span class="sxs-lookup"><span data-stu-id="77380-168">By setting [**DesiredRemainingView**](https://msdn.microsoft.com/library/windows/apps/dn298314), you aren't guaranteed a specific windowing behavior for the source app.</span></span>

<span data-ttu-id="77380-169">**Familie der Mobilgeräte:** [**LauncherOptions.DesiredRemainingView**](https://msdn.microsoft.com/library/windows/apps/dn298314) wird auf der mobilgerätefamilie nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="77380-169">**Mobile device family:**[**LauncherOptions.DesiredRemainingView**](https://msdn.microsoft.com/library/windows/apps/dn298314) isn't supported on the mobile device family.</span></span>

```csharp
async void DefaultLaunch()
{
   // Path to the file in the app package to launch
   string imageFile = @"images\test.png";
   
   var file = await Windows.ApplicationModel.Package.Current.InstalledLocation.GetFileAsync(imageFile);

   if (file != null)
   {
      // Set the desired remaining view
      var options = new Windows.System.LauncherOptions();
      options.DesiredRemainingView = Windows.UI.ViewManagement.ViewSizePreference.UseLess;

      // Launch the retrieved file
      bool success = await Windows.System.Launcher.LaunchFileAsync(file, options);
      if (success)
      {
         // File launched
      }
      else
      {
         // File launch failed
      }
   }
   else
   {
      // Could not find file
   }
}
```

```cppwinrt
Windows::Foundation::IAsyncAction MainPage::DefaultLaunch()
{
    auto installFolder{ Windows::ApplicationModel::Package::Current().InstalledLocation() };

    Windows::Storage::StorageFile file{ co_await installFolder.GetFileAsync(L"images\\test.png") };

    if (file)
    {
        // Set the desired remaining view.
        Windows::System::LauncherOptions launchOptions;
        launchOptions.DesiredRemainingView(Windows::UI::ViewManagement::ViewSizePreference::UseLess);

        // Launch the retrieved file.
        bool success = co_await Windows::System::Launcher::LaunchFileAsync(file, launchOptions);
        if (success)
        {
            // File launched
        }
        else
        {
            // File launch failed
        }
    }
    else
    {
        // Could not find file
    }
}
```

```cpp
void MainPage::DefaultLaunch()
{
   auto installFolder = Windows::ApplicationModel::Package::Current->InstalledLocation;

   concurrency::task<Windows::Storage::StorageFile^> getFileOperation(installFolder->GetFileAsync("images\\test.png"));
   getFileOperation.then([](Windows::Storage::StorageFile^ file)
   {
      if (file != nullptr)
      {
         // Set the desired remaining view.
         auto launchOptions = ref new Windows::System::LauncherOptions();
         launchOptions->DesiredRemainingView = Windows::UI::ViewManagement::ViewSizePreference::UseLess;

         // Launch the retrieved file.
         concurrency::task<bool> launchFileOperation(Windows::System::Launcher::LaunchFileAsync(file, launchOptions));
         launchFileOperation.then([](bool success)
         {
            if (success)
            {
               // File launched
            }
            else
            {
               // File launch failed
            }
         });
      }
      else
      {
         // Could not find file
      }
   });
}
```

## <a name="remarks"></a><span data-ttu-id="77380-170">Hinweise</span><span class="sxs-lookup"><span data-stu-id="77380-170">Remarks</span></span>

<span data-ttu-id="77380-171">Die gestartete App kann nicht von Ihrer App ausgewählt werden.</span><span class="sxs-lookup"><span data-stu-id="77380-171">Your app can't select the app that is launched.</span></span> <span data-ttu-id="77380-172">Der Benutzer entscheidet, welche App gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="77380-172">The user determines which app is launched.</span></span> <span data-ttu-id="77380-173">Der Benutzer kann eine App für die UWP (Universelle Windows-Plattform) oder eine Windows-Desktop-App auswählen.</span><span class="sxs-lookup"><span data-stu-id="77380-173">The user can select either a Universal Windows Platform (UWP) app or a Windows desktop app.</span></span>

<span data-ttu-id="77380-174">Beim Starten einer Datei muss Ihre App im Vordergrund ausgeführt werden, d.h. sie muss für den Benutzer sichtbar sein.</span><span class="sxs-lookup"><span data-stu-id="77380-174">When launching a file, your app must be the foreground app, that is, it must be visible to the user.</span></span> <span data-ttu-id="77380-175">Durch diese Anforderung wird sichergestellt, dass der Benutzer zu jedem Zeitpunkt die Kontrolle behält.</span><span class="sxs-lookup"><span data-stu-id="77380-175">This requirement helps ensure that the user remains in control.</span></span> <span data-ttu-id="77380-176">Verknüpfen Sie alle Dateistartvorgänge direkt mit der Benutzeroberfläche Ihrer App, um sicherzustellen, dass diese Anforderung erfüllt wird.</span><span class="sxs-lookup"><span data-stu-id="77380-176">To meet this requirement, make sure that you tie all file launches directly to the UI of your app.</span></span> <span data-ttu-id="77380-177">Benutzer müssen wahrscheinlich immer eine Aktion ausführen, bevor eine Datei gestartet werden kann.</span><span class="sxs-lookup"><span data-stu-id="77380-177">Most likely, the user must always take some action to initiate a file launch.</span></span>

<span data-ttu-id="77380-178">Dateitypen mit Code oder Skripts, die automatisch vom Betriebssystem ausgeführt werden (z.B. EXE-, MSI- oder JS-Dateien), können nicht gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="77380-178">You can't launch file types that contain code or script if they are executed automatically by the operating system, such as, .exe, .msi, and .js files.</span></span> <span data-ttu-id="77380-179">Diese Einschränkung schützt Benutzer vor der Ausführung von schädlichen Dateien, durch die das Betriebssystem verändert werden könnte.</span><span class="sxs-lookup"><span data-stu-id="77380-179">This restriction protects users from potentially malicious files that could modify the operating system.</span></span> <span data-ttu-id="77380-180">Mit dieser Methode können Sie Dateitypen mit Skripts starten, wenn das Skript dabei von der ausgeführten App isoliert wird, z.B. DOCX-Dateien.</span><span class="sxs-lookup"><span data-stu-id="77380-180">You can use this method to launch file types that can contain script if they are executed by an app that isolates the script, such as, .docx files.</span></span> <span data-ttu-id="77380-181">Apps wie Microsoft Word verhindern, dass das Betriebssystem durch DOCX-Dateien modifiziert wird.</span><span class="sxs-lookup"><span data-stu-id="77380-181">Apps like Microsoft Word keep the script in .docx files from modifying the operating system.</span></span>

<span data-ttu-id="77380-182">Wenn Sie versuchen, einen eingeschränkten Dateityp zu starten, schlägt der Start fehl, und Ihr Fehlerrückruf wird aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="77380-182">If you try to launch a restricted file type, the launch will fail and your error callback will be invoked.</span></span> <span data-ttu-id="77380-183">Wenn Ihre App viele verschiedene Dateitypen behandelt und Sie erwarten, dass dieser Fehler auftritt, sollten Sie Benutzern eine Fallbackoption zur Verfügung stellen.</span><span class="sxs-lookup"><span data-stu-id="77380-183">If your app handles many different types of files and you expect that you will hit this error, we recommend that you provide a fallback experience to your user.</span></span> <span data-ttu-id="77380-184">Bieten Sie Benutzern z.B. die Möglichkeit, die Datei auf dem Desktop zu speichern und zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="77380-184">For example, you could give the user an option to save the file to the desktop, and they could open it there.</span></span>

## <a name="related-topics"></a><span data-ttu-id="77380-185">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="77380-185">Related topics</span></span>

### <a name="tasks"></a><span data-ttu-id="77380-186">Aufgaben</span><span class="sxs-lookup"><span data-stu-id="77380-186">Tasks</span></span>

* [<span data-ttu-id="77380-187">Starten der Standard-App für einen URI</span><span class="sxs-lookup"><span data-stu-id="77380-187">Launch the default app for a URI</span></span>](launch-default-app.md)
* [<span data-ttu-id="77380-188">Behandeln der Dateiaktivierung</span><span class="sxs-lookup"><span data-stu-id="77380-188">Handle file activation</span></span>](handle-file-activation.md)

### <a name="guidelines"></a><span data-ttu-id="77380-189">Richtlinien</span><span class="sxs-lookup"><span data-stu-id="77380-189">Guidelines</span></span>

* [<span data-ttu-id="77380-190">Richtlinien für Dateitypen und URIs</span><span class="sxs-lookup"><span data-stu-id="77380-190">Guidelines for file types and URIs</span></span>](https://msdn.microsoft.com/library/windows/apps/hh700321)

### <a name="reference"></a><span data-ttu-id="77380-191">Referenz</span><span class="sxs-lookup"><span data-stu-id="77380-191">Reference</span></span>

* [**<span data-ttu-id="77380-192">Windows.Storage.StorageFile</span><span class="sxs-lookup"><span data-stu-id="77380-192">Windows.Storage.StorageFile</span></span>**](https://msdn.microsoft.com/library/windows/apps/br227171)
* [**<span data-ttu-id="77380-193">Windows.System.Launcher.LaunchFileAsync</span><span class="sxs-lookup"><span data-stu-id="77380-193">Windows.System.Launcher.LaunchFileAsync</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh701461)
