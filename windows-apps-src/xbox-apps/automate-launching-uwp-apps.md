---
title: Automatisieren des Starts für Apps der universellen Windows Plattform (UWP) in Windows10
description: Mit der Protokoll- und Startaktivierung können Entwickler ihre UWP-Apps oder Spiele für automatisierte Tests automatisch starten.
ms.topic: article
ms.localizationpriority: medium
ms.date: 02/08/2017
ms.openlocfilehash: fb68b4bbd1b751591e9f336efe5dad3c22b3bf92
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8937199"
---
# <a name="automate-launching-windows-10-uwp-apps"></a><span data-ttu-id="31592-103">Automatisieren des Starts von UWP-Apps unter Windows 10</span><span class="sxs-lookup"><span data-stu-id="31592-103">Automate launching Windows 10 UWP apps</span></span>

## <a name="introduction"></a><span data-ttu-id="31592-104">Einführung</span><span class="sxs-lookup"><span data-stu-id="31592-104">Introduction</span></span>

<span data-ttu-id="31592-105">Entwickler haben mehrere Möglichkeiten, einen automatisierten Start von UWP-Apps zu realisieren.</span><span class="sxs-lookup"><span data-stu-id="31592-105">Developers have several options for achieving automated launching of Universal Windows Platform (UWP) apps.</span></span> <span data-ttu-id="31592-106">Dieses Dokument beschreibt Methoden zum Starten einer App über die Protokoll- und Startaktivierung.</span><span class="sxs-lookup"><span data-stu-id="31592-106">In this paper we will explore methods of launching an app by using protocol activation and launch activation.</span></span>

<span data-ttu-id="31592-107">Die *Protokollaktivierung* ermöglicht der App eine Registrierung als Handler für ein bestimmtes Protokoll.</span><span class="sxs-lookup"><span data-stu-id="31592-107">*Protocol activation* allows an app to register itself as a handler for a given protocol.</span></span> 

<span data-ttu-id="31592-108">Die *Startaktivierung* stellt den normalen Start einer App dar, beispielsweise das Starten über eine App-Kachel.</span><span class="sxs-lookup"><span data-stu-id="31592-108">*Launch activation* is the normal launching of an app, such as launching from the app tile.</span></span>

<span data-ttu-id="31592-109">Bei jeder Aktivierungsmethode können Sie entweder die Befehlszeile oder eine Startanwendung nutzen.</span><span class="sxs-lookup"><span data-stu-id="31592-109">With each activation method, you have the option of using the command line or a launcher application.</span></span> <span data-ttu-id="31592-110">Wird die App gerade ausgeführt, wird sie bei allen Aktivierungsmethoden in den Vordergrund geschaltet, wodurch sie erneut aktiviert wird. Dabei werden die neuen Aktivierungsargumente bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="31592-110">For all activation methods, if the app is currently running, the activation will bring the app to the foreground (which reactivates it) and provide the new activation arguments.</span></span> <span data-ttu-id="31592-111">Somit besteht die Möglichkeit, Aktivierungsbefehle zu verwenden, um neue Nachrichten für die App bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="31592-111">This allows flexibility to use activation commands to provide new messages to the app.</span></span> <span data-ttu-id="31592-112">Beachten Sie unbedingt, dass das Projekt kompiliert und für die Aktivierungsmethode bereitgestellt werden muss, damit die aktualisierte App ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="31592-112">It is important to note that the project needs to be compiled and deployed for the activation method to run the newly updated app.</span></span> 

## <a name="protocol-activation"></a><span data-ttu-id="31592-113">Protokollaktivierung</span><span class="sxs-lookup"><span data-stu-id="31592-113">Protocol activation</span></span>

<span data-ttu-id="31592-114">Führen Sie diese Schritte zum Einrichten der Protokollaktivierung für Apps aus:</span><span class="sxs-lookup"><span data-stu-id="31592-114">Follow these steps to set up protocol activation for apps:</span></span> 

1. <span data-ttu-id="31592-115">Öffnen Sie die Datei **Package.appxmanifest** in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="31592-115">Open the **Package.appxmanifest** file in Visual Studio.</span></span>
2. <span data-ttu-id="31592-116">Klicken Sie auf die Registerkarte **Deklarationen**.</span><span class="sxs-lookup"><span data-stu-id="31592-116">Select the **Declarations** tab.</span></span>
3. <span data-ttu-id="31592-117">Wählen Sie unter **Verfügbare Deklarationen** die Option **Protokoll** und anschließend **Hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="31592-117">Under the **Available Declarations** drop-down, select **Protocol**, and then select **Add**.</span></span>
4. <span data-ttu-id="31592-118">Geben Sie unter **Eigenschaften** im Feld **Name** einen eindeutigen Namen zum Starten der App ein.</span><span class="sxs-lookup"><span data-stu-id="31592-118">Under **Properties**, in the **Name** field, enter a unique name to launch the app.</span></span> 

    ![Protokollaktivierung](images/automate-uwp-apps-1.png)

5. <span data-ttu-id="31592-120">Speichern Sie die Datei, und stellen Sie das Projekt bereit.</span><span class="sxs-lookup"><span data-stu-id="31592-120">Save the file and deploy the project.</span></span> 
6. <span data-ttu-id="31592-121">Nach der Bereitstellung des Projekts sollte die Protokollaktivierung festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="31592-121">After the project has been deployed, the protocol activation should be set.</span></span> 
7. <span data-ttu-id="31592-122">Wechseln Sie zu **Systemsteuerung\Alle Systemsteuerungselemente\Standardprogramme**, und wählen Sie **Dateityp oder Protokoll einem Programm zuordnen** aus.</span><span class="sxs-lookup"><span data-stu-id="31592-122">Go to **Control Panel\All Control Panel Items\Default Programs** and select **Associate a file type or protocol with a specific program**.</span></span> <span data-ttu-id="31592-123">Führen Sie einen Bildlauf zum Abschnitt **Protokolle** aus, um festzustellen, ob das Protokoll aufgeführt ist.</span><span class="sxs-lookup"><span data-stu-id="31592-123">Scroll to the **Protocols** section to see if the protocol is listed.</span></span> 

<span data-ttu-id="31592-124">Nach der Einrichtung der Protokollaktivierung haben Sie zwei Möglichkeiten (Befehlszeile oder Startanwendung), die App über das Protokoll zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="31592-124">Now that protocol activation is set up, you have two options (the command line or launcher application) for activating the app by using the protocol.</span></span> 

### <a name="command-line"></a><span data-ttu-id="31592-125">Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="31592-125">Command line</span></span>

<span data-ttu-id="31592-126">Die App wird per Protokoll aktiviert, indem Sie die Befehlszeile mit dem Startbefehl gefolgt vom vorher festgelegten Protokoll, einem Doppelpunkt („:“) und beliebigen Parametern verwenden.</span><span class="sxs-lookup"><span data-stu-id="31592-126">The app can be protocol-activated by using the command line with the command start followed by the protocol name set previously, a colon (“:”), and any parameters.</span></span> <span data-ttu-id="31592-127">Die Parameter können eine beliebige Zeichenfolge sein. Um aber die Vorteile der Uniform Resource Identifier (URI)-Funktionen nutzen zu können, sollten Sie das standardmäßige URI-Format verwenden:</span><span class="sxs-lookup"><span data-stu-id="31592-127">The parameters can be any arbitrary string; however, to take advantage of the Uniform Resource Identifier (URI) capabilities, it is advisable to follow the standard URI format:</span></span> 

  ```
  scheme://username:password@host:port/path.extension?query#fragment
  ```

<span data-ttu-id="31592-128">Das Uri-Objekt verfügt über Methoden zum Analysieren einer URI-Zeichenfolge in diesem Format.</span><span class="sxs-lookup"><span data-stu-id="31592-128">The Uri object has methods of parsing a URI string in this format.</span></span> <span data-ttu-id="31592-129">Weitere Informationen finden Sie unter [Uri-Klasse (MSDN)](https://msdn.microsoft.com/library/windows/apps/windows.foundation.uri.aspx).</span><span class="sxs-lookup"><span data-stu-id="31592-129">For more information, see [Uri class (MSDN)](https://msdn.microsoft.com/library/windows/apps/windows.foundation.uri.aspx).</span></span> 

<span data-ttu-id="31592-130">Beispiele:</span><span class="sxs-lookup"><span data-stu-id="31592-130">Examples:</span></span>

  ```
  >start bingnews:
  >start myapplication:protocol-parameter
  >start myapplication://single-player/level3?godmode=1&ammo=200
  ```

<span data-ttu-id="31592-131">Die Befehlszeilenaktivierung per Protokoll unterstützt Unicode-Zeichen bis zu maximal 2038 Zeichen auf dem unformatierten URI.</span><span class="sxs-lookup"><span data-stu-id="31592-131">Protocol command-line activation supports Unicode characters up to a 2038-character limit on the raw URI.</span></span> 

### <a name="launcher-application"></a><span data-ttu-id="31592-132">Startanwendung</span><span class="sxs-lookup"><span data-stu-id="31592-132">Launcher application</span></span>

<span data-ttu-id="31592-133">Erstellen Sie zum Starten eine separate Anwendung, die die WinRT-API unterstützt.</span><span class="sxs-lookup"><span data-stu-id="31592-133">For launching, create a separate application that supports the WinRT API.</span></span> <span data-ttu-id="31592-134">Im folgenden Beispiel wird der C++-Code für einen Start per Protokollaktivierung in einem Startprogramm gezeigt. Dabei ist **PackageURI** der URI für die Anwendung mit beliebigen Argumenten, beispielsweise `myapplication:` oder `myapplication:protocol activation arguments`.</span><span class="sxs-lookup"><span data-stu-id="31592-134">The C++ code for launching with protocol activation in a launcher program is shown in the following sample, where **PackageURI** is the URI for the application with any arguments; for example `myapplication:` or `myapplication:protocol activation arguments`.</span></span>

```
bool ProtocolLaunchURI(Platform::String^ URI)
{
       IAsyncOperation<bool>^ protocolLaunchAsyncOp;
       try
       {
              protocolLaunchAsyncOp = Windows::System::Launcher::LaunchUriAsync(ref new 
Uri(URI));
       }
       catch (Platform::Exception^ e)
       {
              Platform::String^ dbgStr = "ProtocolLaunchURI Exception Thrown: " 
+ e->ToString() + "\n";
              OutputDebugString(dbgStr->Data());
              return false;
       }

       concurrency::create_task(protocolLaunchAsyncOp).wait();

       if (protocolLaunchAsyncOp->Status == AsyncStatus::Completed)
       {
              bool LaunchResult = protocolLaunchAsyncOp->GetResults();
              Platform::String^ dbgStr = "ProtocolLaunchURI " + URI 
+ " completed. Launch result " + LaunchResult + "\n";
              OutputDebugString(dbgStr->Data());
              return LaunchResult;
       }
       else
       {
              Platform::String^ dbgStr = "ProtocolLaunchURI " + URI + " failed. Status:" 
+ protocolLaunchAsyncOp->Status.ToString() + " ErrorCode:" 
+ protocolLaunchAsyncOp->ErrorCode.ToString() + "\n";
              OutputDebugString(dbgStr->Data());
              return false;
       }
}
```
<span data-ttu-id="31592-135">Für die Protokollaktivierung mit der Startanwendung gelten dieselben Einschränkungen für Argumente wie für die Protokollaktivierung mit der Befehlszeile.</span><span class="sxs-lookup"><span data-stu-id="31592-135">Protocol activation with the launcher application has the same limitations for arguments as protocol activation with the command line.</span></span> <span data-ttu-id="31592-136">Beide unterstützen Unicode-Zeichen bis maximal 2038Zeichen auf dem unformatierten URI.</span><span class="sxs-lookup"><span data-stu-id="31592-136">Both support Unicode characters up to a 2038-character limit on the raw URI.</span></span> 

## <a name="launch-activation"></a><span data-ttu-id="31592-137">Startaktivierung</span><span class="sxs-lookup"><span data-stu-id="31592-137">Launch activation</span></span>

<span data-ttu-id="31592-138">Sie können die App auch mit der Startaktivierung starten.</span><span class="sxs-lookup"><span data-stu-id="31592-138">You can also launch the app by using launch activation.</span></span> <span data-ttu-id="31592-139">Es ist kein Setup erforderlich, dafür aber die Anwendungsbenutzermodell-ID (Application User Model ID, AUMID) der UWP-App.</span><span class="sxs-lookup"><span data-stu-id="31592-139">No setup is required, but the Application User Model ID (AUMID) of the UWP app is needed.</span></span> <span data-ttu-id="31592-140">Die AUMID ist der Paketfamilienname gefolgt von einem Ausrufezeichen und der Anwendungs-ID.</span><span class="sxs-lookup"><span data-stu-id="31592-140">The AUMID is the package family name followed by an exclamation point and the application ID.</span></span> 

<span data-ttu-id="31592-141">Die beste Möglichkeit zum Abrufen des Paketfamiliennamens besteht in der Durchführung der folgenden Schritte:</span><span class="sxs-lookup"><span data-stu-id="31592-141">The best way to obtain the package family name is to complete these steps:</span></span>

1. <span data-ttu-id="31592-142">Öffnen Sie die Datei **Package.appxmanifest**.</span><span class="sxs-lookup"><span data-stu-id="31592-142">Open the **Package.appxmanifest** file.</span></span>
2. <span data-ttu-id="31592-143">Geben Sie auf der Registerkarte **Verpacken** den **Paketnamen** ein.</span><span class="sxs-lookup"><span data-stu-id="31592-143">On the **Packaging** tab, enter the **Package name**.</span></span>

    ![Startaktivierung](images/automate-uwp-apps-2.png)

3. <span data-ttu-id="31592-145">Wenn der **Paketfamilienname** nicht aufgeführt ist, öffnen Sie PowerShell und führen `>get-appxpackage MyPackageName` aus, um **PackageFamilyName** zu finden.</span><span class="sxs-lookup"><span data-stu-id="31592-145">If the **Package family name** is not listed, open PowerShell and run `>get-appxpackage MyPackageName` to find the **PackageFamilyName**.</span></span>

<span data-ttu-id="31592-146">Sie finden die Anwendungs-ID in der Datei **Package.appxmanifest** (geöffnet in der XML-Ansicht) unter dem `<Applications>`-Element.</span><span class="sxs-lookup"><span data-stu-id="31592-146">The application ID can be found in the **Package.appxmanifest** file (opened in XML view) under the `<Applications>` element.</span></span>

### <a name="command-line"></a><span data-ttu-id="31592-147">Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="31592-147">Command line</span></span>

<span data-ttu-id="31592-148">Ein Tool für die Durchführung einer Startaktivierung einer UWP-App ist im Windows 10-SDK enthalten.</span><span class="sxs-lookup"><span data-stu-id="31592-148">A tool for performing a launch activation of a UWP app is installed with the Windows 10 SDK.</span></span> <span data-ttu-id="31592-149">Es kann über die Befehlszeile ausgeführt werden und benötigt die AUMID der App, damit ein Start als Argument möglich ist.</span><span class="sxs-lookup"><span data-stu-id="31592-149">It can be run from the command line, and it takes the AUMID of the app to be launched as an argument.</span></span>

```
C:\Program Files (x86)\Windows Kits\10\App Certification Kit\microsoft.windows.softwarelogo.appxlauncher.exe <AUMID>
```

<span data-ttu-id="31592-150">Es sieht etwa wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="31592-150">It would look something like this:</span></span>

```
"C:\Program Files (x86)\Windows Kits\10\App Certification Kit\microsoft.windows.softwarelogo.appxlauncher.exe" MyPackageName_ph1m9x8skttmg!AppId
```

<span data-ttu-id="31592-151">Diese Option unterstützt keine Befehlszeilenargumente.</span><span class="sxs-lookup"><span data-stu-id="31592-151">This option does not support command-line arguments.</span></span> 

### <a name="launcher-application"></a><span data-ttu-id="31592-152">Startanwendung</span><span class="sxs-lookup"><span data-stu-id="31592-152">Launcher application</span></span>

<span data-ttu-id="31592-153">Sie können eine separate Anwendung erstellen, die den Einsatz von COM zum Starten unterstützt.</span><span class="sxs-lookup"><span data-stu-id="31592-153">You can create a separate application that supports using COM to use for launching.</span></span> <span data-ttu-id="31592-154">Das folgende Beispiel zeigt den C++-Code für den Start mit Startaktivierung in einem Startprogramm.</span><span class="sxs-lookup"><span data-stu-id="31592-154">The following example shows C++ code for launching with launch activation in a launcher program.</span></span> <span data-ttu-id="31592-155">Mit diesem Code erstellen Sie ein **ApplicationActivationManager**-Objekt und rufen **ActivateApplication** auf, indem Sie die zuvor gefundene AUMID und beliebige Argumente übergeben.</span><span class="sxs-lookup"><span data-stu-id="31592-155">With this code, you can create an **ApplicationActivationManager** object and call **ActivateApplication** passing in the AUMID found previously and any arguments.</span></span> <span data-ttu-id="31592-156">Weitere Informationen zu den anderen Parametern finden Sie unter [IApplicationActivationManager::ActivateApplication-Methode (MSDN)](https://msdn.microsoft.com/library/windows/desktop/hh706903(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="31592-156">For more information about the other parameters, see [IApplicationActivationManager::ActivateApplication method (MSDN)](https://msdn.microsoft.com/library/windows/desktop/hh706903(v=vs.85).aspx).</span></span>

```
#include <ShObjIdl.h>
#include <atlbase.h>

HRESULT LaunchApp(LPCWSTR AUMID)
{
     HRESULT hr = CoInitializeEx(nullptr, COINIT_APARTMENTTHREADED);
     if (FAILED(hr))
     {
            wprintf(L"LaunchApp %s: Failed to init COM. hr = 0x%08lx \n", AUMID, hr);
     }
     {
            CComPtr<IApplicationActivationManager> AppActivationMgr = nullptr;
            if (SUCCEEDED(hr))
            {
                   hr = CoCreateInstance(CLSID_ApplicationActivationManager, nullptr,  
CLSCTX_LOCAL_SERVER, IID_PPV_ARGS(&AppActivationMgr));
                   if (FAILED(hr))
                   {
                         wprintf(L"LaunchApp %s: Failed to create Application Activation 
Manager. hr = 0x%08lx \n", AUMID, hr);
                   }
            }
            if (SUCCEEDED(hr))
            {
                   DWORD pid = 0;
                   hr = AppActivationMgr->ActivateApplication(AUMID, nullptr, AO_NONE, 
&pid);
                   if (FAILED(hr))
                   {
                         wprintf(L"LaunchApp %s: Failed to Activate App. hr = 0x%08lx 
\n", AUMID, hr);
                   }
            }
     }
     CoUninitialize();
     return hr;
}
```

<span data-ttu-id="31592-157">Dabei ist zu beachten, dass diese Methode im Gegensatz zur vorherigen Methode für den Start (also die Befehlszeilenmethode) übergebene Argumente unterstützt.</span><span class="sxs-lookup"><span data-stu-id="31592-157">It is worth noting that this method does support arguments being passed in, unlike the previous method for launching (that is, using the command line).</span></span>

## <a name="accepting-arguments"></a><span data-ttu-id="31592-158">Akzeptieren von Argumenten</span><span class="sxs-lookup"><span data-stu-id="31592-158">Accepting arguments</span></span>

<span data-ttu-id="31592-159">Damit Argumente, die bei der Aktivierung der UWP-App übergeben werden, akzeptiert werden, müssen Sie der App einen Code hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="31592-159">To accept arguments passed in on activation of the UWP app, you must add some code to the app.</span></span> <span data-ttu-id="31592-160">Zur Feststellung, ob eine Protokoll- oder Startaktivierung stattgefunden hat, überschreiben Sie das **OnActivated**-Ereignis, überprüfen den Typ des Arguments und rufen dann die unformatierte Zeichenfolge oder die vorab analysierten Werte des Uri-Objekts ab.</span><span class="sxs-lookup"><span data-stu-id="31592-160">To determine if protocol activation or launch activation occurred, override the **OnActivated** event and check the argument type, and then get the raw string or Uri object’s pre-parsed values.</span></span> 

<span data-ttu-id="31592-161">Dieses Beispiel zeigt, wie Sie die unformatierte Zeichenfolge abrufen.</span><span class="sxs-lookup"><span data-stu-id="31592-161">This example shows how to get the raw string.</span></span>

```
void OnActivated(IActivatedEventArgs^ args)
{
        // Check for launch activation
        if (args->Kind == ActivationKind::Launch)
        {
            auto launchArgs = static_cast<LaunchActivatedEventArgs^>(args); 
            Platform::String^ argval = launchArgs->Arguments;
            // Manipulate arguments …
        }

        // Check for protocol activation
        if (args->Kind == ActivationKind::Protocol)
        {
            auto protocolArgs = static_cast< ProtocolActivatedEventArgs^>(args);
            Platform::String^ argval = protocolArgs->Uri->ToString();
            // Manipulate arguments …
        }
}
```

## <a name="summary"></a><span data-ttu-id="31592-162">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="31592-162">Summary</span></span>
<span data-ttu-id="31592-163">Zusammenfassend lässt sich sagen, dass für den Start der UWP-App verschiedene Methoden zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="31592-163">In summary, you can use various methods to launch the UWP app.</span></span> <span data-ttu-id="31592-164">Je nach Anforderungen und Anwendungsfällen können manche Methoden besser geeignet sein als andere.</span><span class="sxs-lookup"><span data-stu-id="31592-164">Depending on the requirements and use cases, different methods may be better suited than others.</span></span> 

## <a name="see-also"></a><span data-ttu-id="31592-165">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="31592-165">See also</span></span>
- [<span data-ttu-id="31592-166">UWP auf Xbox One</span><span class="sxs-lookup"><span data-stu-id="31592-166">UWP on Xbox One</span></span>](index.md)

