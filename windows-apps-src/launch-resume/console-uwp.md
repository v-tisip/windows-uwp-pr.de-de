---
author: TylerMSFT
title: Erstellen einer universellen Windows-Plattform-Konsolen-App
description: In diesem Thema erfahren Sie, wie Sie eine UWP-App erstellen, die in einem Konsolenfenster ausgeführt wird.
keywords: console uwp
ms.author: twhitney
ms.date: 08/02/2018
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 7e5923176f5f9fff1a6e4f30a7ba2419e99c074b
ms.sourcegitcommit: ca96031debe1e76d4501621a7680079244ef1c60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "5819075"
---
# <a name="create-a-universal-windows-platform-console-app"></a><span data-ttu-id="87b8f-104">Erstellen einer universellen Windows-Plattform-Konsolen-App</span><span class="sxs-lookup"><span data-stu-id="87b8f-104">Create a Universal Windows Platform console app</span></span>

<span data-ttu-id="87b8f-105">Dieses Thema enthält Informationen zum Erstellen einer [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) oder C++ / CX universelle Windows-Plattform (UWP)-Konsolen-app.</span><span class="sxs-lookup"><span data-stu-id="87b8f-105">This topic describes how to create a [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) or C++/CX Universal Windows Platform (UWP) console app.</span></span>

<span data-ttu-id="87b8f-106">Ab Windows 10, Version 1803, können Sie schreiben C++ / WinRT oder C++ / CX UWP Konsolen-apps, die in einem Konsolenfenster wie z. B. einem DOS oder PowerShell-Konsolenfenster ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="87b8f-106">Starting with Windows 10, version 1803, you can write C++/WinRT or C++/CX UWP console apps that run in a console window, such as a DOS or PowerShell console window.</span></span> <span data-ttu-id="87b8f-107">Konsolen-apps verwenden das Konsolenfenster für die Eingabe und Ausgabe und [Universelle C++-Runtime-](/cpp/c-runtime-library/reference/crt-alphabetical-function-reference) Funktionen wie z. B. **Printf** und **Getchar**verwenden.</span><span class="sxs-lookup"><span data-stu-id="87b8f-107">Console apps use the console window for input and output, and can use [Universal C Runtime](/cpp/c-runtime-library/reference/crt-alphabetical-function-reference) functions such as **printf** and **getchar**.</span></span> <span data-ttu-id="87b8f-108">UWP-Konsolen-Apps können im Microsoft Store veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="87b8f-108">UWP console apps can be published to the Microsoft Store.</span></span> <span data-ttu-id="87b8f-109">Sie haben einen Eintrag in der App-Liste und eine primäre Kachel, die an das Startmenü angeheftet werden kann.</span><span class="sxs-lookup"><span data-stu-id="87b8f-109">They have an entry in the app list, and a primary tile that can be pinned to the Start menu.</span></span> <span data-ttu-id="87b8f-110">UWP-Konsolen-apps können aus dem Menü "Start" gestartet werden, obwohl Sie in der Regel über die Befehlszeile gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="87b8f-110">UWP console apps can be launched from the Start menu, though you will typically launch them from the command-line.</span></span>

<span data-ttu-id="87b8f-111">Hier sehen Sie ein Video über das Erstellen einer UWP-Konsolen-App, um eine in Aktion anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="87b8f-111">To see one in action, here's a video about Creating a UWP Console App.</span></span>

> [!VIDEO https://www.youtube.com/embed/bwvfrguY20s]

## <a name="use-a-uwp-console-app-template"></a><span data-ttu-id="87b8f-112">Verwenden einer UWP-Konsolen-App-Vorlage</span><span class="sxs-lookup"><span data-stu-id="87b8f-112">Use a UWP Console app template</span></span> 

<span data-ttu-id="87b8f-113">Um eine UWP-Konsolen-App zu erstellen, installieren Sie zuerst die **Konsolen-App (Universal)-Projektvorlagen**, die Sie im [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=AndrewWhitechapelMSFT.ConsoleAppUniversal) erhalten.</span><span class="sxs-lookup"><span data-stu-id="87b8f-113">To create a UWP console app, first install the **Console App (Universal) Project Templates**, available from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=AndrewWhitechapelMSFT.ConsoleAppUniversal).</span></span> <span data-ttu-id="87b8f-114">Die installierten Vorlagen stehen dann unter **Neues Projekt** > **installiert** > **Andere Sprachen** > **Visual C++** > **Windows Universal** als \*\*Console App c++ / WinRT (Universal Windows) \*\*und **Console App C++ / CX (Universal Windows)**.</span><span class="sxs-lookup"><span data-stu-id="87b8f-114">The installed templates are then available under **New Project** > **Installed** > **Other Languages** > **Visual C++** > **Windows Universal** as **Console App C++/WinRT (Universal Windows)** and **Console App C++/CX (Universal Windows)**.</span></span>

## <a name="add-your-code-to-main"></a><span data-ttu-id="87b8f-115">Ihren Code „main()” hinzufügen</span><span class="sxs-lookup"><span data-stu-id="87b8f-115">Add your code to main()</span></span>

<span data-ttu-id="87b8f-116">Die Vorlagen fügen **Program.cpp** hinzu, die die `main()`-Funktion enthält.</span><span class="sxs-lookup"><span data-stu-id="87b8f-116">The templates add **Program.cpp**, which contains the `main()` function.</span></span> <span data-ttu-id="87b8f-117">Hier beginnt die Ausführung in einer UWP-App-Konsole.</span><span class="sxs-lookup"><span data-stu-id="87b8f-117">This is where execution begins in a UWP console app.</span></span> <span data-ttu-id="87b8f-118">Greifen Sie mit den Parametern `__argc` und `__argv` auf die Befehlszeilenargumente zu.</span><span class="sxs-lookup"><span data-stu-id="87b8f-118">Access the command-line arguments with the `__argc` and `__argv` parameters.</span></span> <span data-ttu-id="87b8f-119">Die UWP-Konsolen-App wird beendet, wenn die Steuerung von `main()` zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="87b8f-119">The UWP console app exits when control returns from `main()`.</span></span>

<span data-ttu-id="87b8f-120">Das folgende Beispiel von **Program.cpp** wird hinzugefügt, indem die **Console App c++ / WinRT** Vorlage:</span><span class="sxs-lookup"><span data-stu-id="87b8f-120">The following example of **Program.cpp** is added by the **Console App C++/WinRT** template:</span></span>

```cppwinrt
#include "pch.h"

using namespace winrt;

// This example code shows how you could implement the required main function
// for a Console UWP Application. You can replace all the code inside main
// with your own custom code.

int __cdecl main()
{
    // You can get parsed command-line arguments from the CRT globals.
    wprintf(L"Parsed command-line arguments:\n");
    for (int i = 0; i < __argc; i++)
    {
        wprintf(L"__argv[%d] = %S\n", i, __argv[i]);
    }

    // Keep the console window alive in case you want to see console output when running from within Visual Studio
      wprintf(L"Press 'Enter' to continue: ");
    getchar();
}
```

## <a name="uwp-console-app-behavior"></a><span data-ttu-id="87b8f-121">Verhalten der UWP-Konsolen-App</span><span class="sxs-lookup"><span data-stu-id="87b8f-121">UWP Console app behavior</span></span>

<span data-ttu-id="87b8f-122">Eine UWP-Konsolen-App kann sowohl aus dem Verzeichnis auf das Dateisystem zugreifen, aus dem sie ausgeführt wird, sowie aus Unterverzeichnissen dessen.</span><span class="sxs-lookup"><span data-stu-id="87b8f-122">A UWP Console app can access the file-system from the directory it is run from, and below.</span></span> <span data-ttu-id="87b8f-123">Dies ist möglich, da die Vorlage der Datei „Package.appxmanifest” der App die [AppExecutionAlias](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap5-appexecutionalias)-Erweiterung hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="87b8f-123">This is possible because the template adds the [AppExecutionAlias](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap5-appexecutionalias) extension to your app's Package.appxmanifest file.</span></span> <span data-ttu-id="87b8f-124">Diese Erweiterung ermöglicht auch, dass der Benutzer den Alias in einem Konsolenfenster eingeben kann, um die App zu starten.</span><span class="sxs-lookup"><span data-stu-id="87b8f-124">This extension also enables the user to type the alias from a console window to launch the app.</span></span> <span data-ttu-id="87b8f-125">Die App muss sich für den Start nicht im Systempfad befinden.</span><span class="sxs-lookup"><span data-stu-id="87b8f-125">The app does not need to be in the system path to launch.</span></span>

<span data-ttu-id="87b8f-126">Darüber hinaus können Sie Ihrer UWP-Konsolen-App umfassenden Zugriff auf das Dateisystem erteilen, indem Sie die eingeschränkte Funktion `broadFileSystemAccess`, wie in [Berechtigungen für den Dateizugriff](https://docs.microsoft.com/windows/uwp/files/file-access-permissions) beschrieben, hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="87b8f-126">You can additionally give broad access to the file system to your UWP console app by adding the restricted capability `broadFileSystemAccess` as described in [File access permissions](https://docs.microsoft.com/windows/uwp/files/file-access-permissions).</span></span> <span data-ttu-id="87b8f-127">Diese Funktion funktioniert mit APIs im [**Windows.Storage**](https://msdn.microsoft.com/library/windows/apps/BR227346)-Namespace.</span><span class="sxs-lookup"><span data-stu-id="87b8f-127">This capability works with APIs in the [**Windows.Storage**](https://msdn.microsoft.com/library/windows/apps/BR227346) namespace.</span></span>

<span data-ttu-id="87b8f-128">Zu jedem beliebigen Zeitpunkt kann mehr als eine Instanz einer UWP-Konsolen-App ausgeführt werden, da die Vorlage der Datei „Package.appxmanifest” Ihrer App die [SupportsMultipleInstances](multi-instance-uwp.md)-Funktion hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="87b8f-128">More than one instance of a UWP Console app can run at a time because the template adds the [SupportsMultipleInstances](multi-instance-uwp.md) capability to your app's Package.appxmanifest file.</span></span>

<span data-ttu-id="87b8f-129">Außerdem fügt die Vorlage der Datei „Package.appxmanifest” die `Subsystem="console"`-Funktion hinzu, die angibt, dass es sich bei dieser UWP-App um eine Konsolen-App handelt.</span><span class="sxs-lookup"><span data-stu-id="87b8f-129">The template also adds the `Subsystem="console"` capability to the Package.appxmanifest file, which denotes that this UWP app is a console app.</span></span> <span data-ttu-id="87b8f-130">Beachten Sie die Präfixe `desktop4` und iot2 `namespace`.</span><span class="sxs-lookup"><span data-stu-id="87b8f-130">Note the `desktop4` and iot2 `namespace` prefixes.</span></span> <span data-ttu-id="87b8f-131">UWP-Konsolen-Apps werden nur für Desktop- und Internet der Dinge (IoT)-Projekte unterstützt.</span><span class="sxs-lookup"><span data-stu-id="87b8f-131">UWP Console apps are only supported on desktop and Internet of Things (IoT) projects.</span></span>

```xml
<Package
  ...
  xmlns:desktop4="http://schemas.microsoft.com/appx/manifest/desktop/windows10/4" 
  xmlns:iot2="http://schemas.microsoft.com/appx/manifest/iot/windows10/2" 
  IgnorableNamespaces="uap mp uap5 desktop4 iot2">
  ...
  <Applications>
    <Application Id="App"
      ...
      desktop4:Subsystem="console" 
      desktop4:SupportsMultipleInstances="true" 
      iot2:Subsystem="console" 
      iot2:SupportsMultipleInstances="true"  >
      ...
      <Extensions>
          <uap5:Extension 
            Category="windows.appExecutionAlias" 
            Executable="YourApp.exe" 
            EntryPoint="YourApp.App">
            <uap5:AppExecutionAlias desktop4:Subsystem="console">
              <uap5:ExecutionAlias Alias="YourApp.exe" />
            </uap5:AppExecutionAlias>
          </uap5:Extension>
      </Extensions>
    </Application>
  </Applications>
    ...
</Package>
```

## <a name="additional-considerations-for-uwp-console-apps"></a><span data-ttu-id="87b8f-132">Weitere Überlegungen zu UWP-Konsolen-Apps</span><span class="sxs-lookup"><span data-stu-id="87b8f-132">Additional considerations for UWP console apps</span></span>

- <span data-ttu-id="87b8f-133">Nur C++ / WinRT und C++ / CX-UWP-apps können Konsolen-apps sein.</span><span class="sxs-lookup"><span data-stu-id="87b8f-133">Only C++/WinRT and C++/CX UWP apps may be console apps.</span></span>
- <span data-ttu-id="87b8f-134">UWP-Konsolen-Apps müssen auf den Projekttyp Desktop oder IoT ausgerichtet sein.</span><span class="sxs-lookup"><span data-stu-id="87b8f-134">UWP Console apps must target the Desktop, or IoT project type.</span></span>
- <span data-ttu-id="87b8f-135">UWP-Konsolen-apps dürfen kein Fenster erstellen.</span><span class="sxs-lookup"><span data-stu-id="87b8f-135">UWP console apps may not create a window.</span></span> <span data-ttu-id="87b8f-136">Sie können nicht MessageBox(), oder Location() oder jeder anderen API, die aus irgendeinem Grund wird ein Fenster erstellt möglicherweise verwenden, z. B. Zustimmung aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="87b8f-136">They cannot use MessageBox(), or Location(), or any other API that may create a window for any reason, such as user consent prompts.</span></span>
- <span data-ttu-id="87b8f-137">UWP-Konsolen-Apps darf nicht Hintergrundaufgaben nutzen oder als Hintergrundaufgabe dienen.</span><span class="sxs-lookup"><span data-stu-id="87b8f-137">UWP console apps may not consume background tasks nor serve as a background task.</span></span>
- <span data-ttu-id="87b8f-138">Mit Ausnahme der [Befehlszeilenaktivierung](https://blogs.windows.com/buildingapps/2017/07/05/command-line-activation-universal-windows-apps/#5YJUzjBoXCL4MhAe.97) unterstützen UWP-Konsolen-Apps keine Support-Aktivierungsverträge, einschließlich Dateizuordnung, Protokollzuordnung usw.</span><span class="sxs-lookup"><span data-stu-id="87b8f-138">With the exception of [Command-Line activation](https://blogs.windows.com/buildingapps/2017/07/05/command-line-activation-universal-windows-apps/#5YJUzjBoXCL4MhAe.97), UWP console apps do not support activation contracts, including file association, protocol association, etc.</span></span>
- <span data-ttu-id="87b8f-139">Obwohl UWP-Konsolen-Apps die Multiinstanzerstellung unterstützen, bieten Sie keine Unterstützung für die [Umleitung bei der Multiinstanzerstellung](multi-instance-uwp.md)</span><span class="sxs-lookup"><span data-stu-id="87b8f-139">Although UWP console apps support multi-instancing, they do not support [Multi-instancing redirection](multi-instance-uwp.md)</span></span>
- <span data-ttu-id="87b8f-140">Eine Liste von Win32-APIs, die für UWP-Apps verfügbar sind, finden Sie unter [Win32- und COM-APIs für UWP-Apps](https://docs.microsoft.com/uwp/win32-and-com/win32-and-com-for-uwp-apps)</span><span class="sxs-lookup"><span data-stu-id="87b8f-140">For a list of Win32 APIs that are available to UWP apps, see [Win32 and COM APIs for UWP apps](https://docs.microsoft.com/uwp/win32-and-com/win32-and-com-for-uwp-apps)</span></span>