---
description: Tools und Verfahren zum Debuggen und Testen der Kompatibilität Ihrer App mit der Prozesslebensdauer-Verwaltung.
title: Test- und Debugtools für die Prozesslebensdauer-Verwaltung (PLM)
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.assetid: 8ac6d127-3475-4512-896d-80d1e1d66ccd
ms.localizationpriority: medium
ms.openlocfilehash: 8b3e37d4de3a346e0f29909727a46d3b31f9d59d
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7854069"
---
# <a name="testing-and-debugging-tools-for-process-lifetime-management-plm"></a><span data-ttu-id="10545-104">Test- und Debugtools für die Prozesslebensdauer-Verwaltung (PLM)</span><span class="sxs-lookup"><span data-stu-id="10545-104">Testing and debugging tools for Process Lifetime Management (PLM)</span></span>

<span data-ttu-id="10545-105">Einer der Hauptunterschiede zwischen UWP-Apps und traditionellen Desktopanwendungen besteht darin, dass UWP-Titel in einem App-Container enthalten sind, der der Prozesslebensdauer-Verwaltung (Process Lifecycle Management, PLM) unterliegt.</span><span class="sxs-lookup"><span data-stu-id="10545-105">One of the key differences between UWP apps and traditional desktop applications is that UWP titles reside in an app container subject to Process Lifecycle Management (PLM).</span></span> <span data-ttu-id="10545-106">UWP-Apps können plattformübergreifend durch den Runtime Broker-Dienst angehalten, fortgesetzt oder beendet werden. Um diese Übergänge beim Testen oder Debuggen des Codes, durch den sie behandelt werden, zu erzwingen, stehen Ihnen spezielle Tools zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="10545-106">UWP apps can be suspended, resumed, or terminated across all platforms by the Runtime Broker service, and there are dedicated tools for you to use to force those transitions when you are testing or debugging the code that handles them.</span></span>

## <a name="features-in-visual-studio-2015"></a><span data-ttu-id="10545-107">Features in Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="10545-107">Features in Visual Studio 2015</span></span>

<span data-ttu-id="10545-108">Der integrierte Debugger in Visual Studio 2015 kann Sie bei der Untersuchung potenzieller Probleme unterstützen, die bei Verwendung reiner UWP-Features auftreten können.</span><span class="sxs-lookup"><span data-stu-id="10545-108">The built-in debugger in Visual Studio 2015 can help you investigate potential issues when using UWP-exclusive features.</span></span> <span data-ttu-id="10545-109">Mithilfe der Symbolleiste **Ereignisse des Lebenszyklus**, die beim Ausführen und Debuggen Ihres Titels sichtbar wird, können Sie für die Anwendung unterschiedliche PLM-Zustände erzwingen.</span><span class="sxs-lookup"><span data-stu-id="10545-109">You can force your application into different PLM states by using the **Lifecycle Events** toolbar, which becomes visible when you run and debug your title.</span></span>

![Symbolleiste „Ereignisse des Lebenszyklus“](images/gs-debug-uwp-apps-001.png)

## <a name="the-plmdebug-tool"></a><span data-ttu-id="10545-111">Tool PLMDebug</span><span class="sxs-lookup"><span data-stu-id="10545-111">The PLMDebug tool</span></span>

<span data-ttu-id="10545-112">Das Befehlszeilentool „PLMDebug.exe“ ist Bestandteil des Windows SDKs und ermöglicht es Ihnen, den PLM-Zustand eines Anwendungspakets zu steuern.</span><span class="sxs-lookup"><span data-stu-id="10545-112">PLMDebug.exe is a command-line tool that allows you to control the PLM state of an application package, and is shipped as part of the Windows SDK.</span></span> <span data-ttu-id="10545-113">Nach der Installation finden Sie das Tool standardmäßig unter *C:\Programme (x86)\Windows Kits\10\Debuggers\x64*.</span><span class="sxs-lookup"><span data-stu-id="10545-113">After it is installed, the tool resides in *C:\Program Files (x86)\Windows Kits\10\Debuggers\x64* by default.</span></span> 

<span data-ttu-id="10545-114">Mithilfe von PLMDebug können Sie außerdem PLM für beliebige installierte App-Pakete deaktivieren, was für einige Debugger erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="10545-114">PLMDebug also allows you to disable PLM for any installed app package, which is necessary for some debuggers.</span></span> <span data-ttu-id="10545-115">Durch das Deaktivieren von PLM wird verhindert, dass der Runtime Broker-Dienst Ihre App beendet, bevor Sie sie debuggen können.</span><span class="sxs-lookup"><span data-stu-id="10545-115">Disabling PLM prevents the Runtime Broker service from terminating your app before you have a chance to debug.</span></span> <span data-ttu-id="10545-116">Verwenden Sie zum Deaktivieren von PLM die Option **/enableDebug** gefolgt vom *vollständigen Paketnamen* Ihrer UWP-App (der Kurzname, der Paketfamilienname oder die AUMID eines Pakets funktioniert nicht):</span><span class="sxs-lookup"><span data-stu-id="10545-116">To disable PLM, use the **/enableDebug** switch, followed by the *full package name* of your UWP app (the short name, package family name, or AUMID of a package will not work):</span></span>

```
plmdebug /enableDebug [PackageFullName]
```

<span data-ttu-id="10545-117">Nachdem Sie Ihre UWP-App aus Visual Studio bereitgestellt haben, wird im Ausgabefenster der vollständige Paketname angezeigt.</span><span class="sxs-lookup"><span data-stu-id="10545-117">After deploying your UWP app from Visual Studio, the full package name is displayed in the output window.</span></span> <span data-ttu-id="10545-118">Alternativ können Sie den vollständigen Paketnamen abrufen, indem Sie **Get-AppxPackage** in einer PowerShell-Konsole ausführen.</span><span class="sxs-lookup"><span data-stu-id="10545-118">Alternatively, you can also retrieve the full package name by running **Get-AppxPackage** in a PowerShell console.</span></span>

![Ausführen von Get-AppxPackage](images/gs-debug-uwp-apps-003.png)

<span data-ttu-id="10545-120">Optional können Sie einen absoluten Pfad zu einem Debugger angeben, der beim Aktivieren des App-Pakets automatisch gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="10545-120">Optionally, you can specify an absolute path to a debugger that will automatically launch when your app package is activated.</span></span> <span data-ttu-id="10545-121">Wenn Sie zu diesem Zweck Visual Studio verwenden möchten, müssen Sie „VSJITDebugger.exe“ als Debugger angeben.</span><span class="sxs-lookup"><span data-stu-id="10545-121">If you wish to do this using Visual Studio, you’ll need to specify VSJITDebugger.exe as the debugger.</span></span> <span data-ttu-id="10545-122">„VSJITDebugger.exe“ erfordert jedoch, dass Sie zusätzlich zur Prozess-ID (PID) der UWP-App die Option „-p“ angeben.</span><span class="sxs-lookup"><span data-stu-id="10545-122">However, VSJITDebugger.exe requires that you specify the “-p” switch, along with the process ID (PID) of the UWP app.</span></span> <span data-ttu-id="10545-123">Da Sie die PID Ihrer UWP-App im Voraus nicht kennen können, ist dieses Szenario nicht ohne weitere Vorbereitung möglich.</span><span class="sxs-lookup"><span data-stu-id="10545-123">Because it’s not possible to know the PID of your UWP app beforehand, this scenario is not possible out of the box.</span></span>

<span data-ttu-id="10545-124">Sie können diese Einschränkung umgehen, indem Sie ein Skript oder Tool schreiben, mit dem der Prozess Ihres Spiels identifiziert wird. Anschließend führt die Shell „VSJITDebugger.exe“ aus und übergibt die PID Ihrer UWP-App.</span><span class="sxs-lookup"><span data-stu-id="10545-124">You can work around this limitation by writing a script or tool that identifies your game’s process, and then the shell runs VSJITDebugger.exe, passing in the PID of your UWP app.</span></span> <span data-ttu-id="10545-125">Das folgende C#-Codebeispiel veranschaulicht einen direkten Ansatz für dieses Verfahren.</span><span class="sxs-lookup"><span data-stu-id="10545-125">The following C# code sample illustrates a straightforward approach to accomplish this.</span></span>

```
using System.Diagnostics;

namespace VSJITLauncher
{
    class Program
    {
        static void Main(string[] args)
        {
            // Name of UWP process, which can be retrieved via Task Manager.
            Process[] processes = Process.GetProcessesByName(args[0]);

            // Get PID of most recent instance
            // Note the highest PID is arbitrary. Windows may recycle or wrap the PID at any time.
            int highestId = 0;
            foreach (Process detectedProcess in processes)
            {
                if (detectedProcess.Id > highestId)
                    highestId = detectedProcess.Id;
            }

            // Launch VSJITDebugger.exe, which resides in C:\Windows\System32
            ProcessStartInfo startInfo = new ProcessStartInfo("vsjitdebugger.exe", "-p " + highestId);
            startInfo.UseShellExecute = true;

            Process process = new Process();
            process.StartInfo = startInfo;
            process.Start();
        }
    }
}
```

<span data-ttu-id="10545-126">Verwendungsbeispiel für dieses Verfahren in Verbindung mit PLMDebug:</span><span class="sxs-lookup"><span data-stu-id="10545-126">Example usage of this in conjunction with PLMDebug:</span></span>

```
plmdebug /enableDebug 279f7062-ce35-40e8-a69f-cc22c08e0bb8_1.0.0.0_x86__c6sq6kwgxxfcg "\"C:\VSJITLauncher.exe\" Game"
```
<span data-ttu-id="10545-127">`Game` entspricht dabei dem Prozessnamen und `279f7062-ce35-40e8-a69f-cc22c08e0bb8_1.0.0.0_x86__c6sq6kwgxxfcg` dem vollständigen Paketnamen des UWP-App-Pakets im Beispiel.</span><span class="sxs-lookup"><span data-stu-id="10545-127">where `Game` is the process name, and `279f7062-ce35-40e8-a69f-cc22c08e0bb8_1.0.0.0_x86__c6sq6kwgxxfcg` is the full package name of the example UWP app package.</span></span>

<span data-ttu-id="10545-128">Beachten Sie, dass jeder **/enableDebug**-Aufruf später mit der Option **/disableDebug** an einen weiteren PLMDebug-Aufruf gekoppelt werden muss.</span><span class="sxs-lookup"><span data-stu-id="10545-128">Note that every call to **/enableDebug** must be later coupled to another PLMDebug call with the **/disableDebug** switch.</span></span> <span data-ttu-id="10545-129">Darüber hinaus muss der Pfad zu einem Debugger absolut sein (relative Pfade werden nicht unterstützt).</span><span class="sxs-lookup"><span data-stu-id="10545-129">Furthermore, the path to a debugger must be absolute (relative paths are not supported).</span></span>

## <a name="related-topics"></a><span data-ttu-id="10545-130">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="10545-130">Related topics</span></span>
- [<span data-ttu-id="10545-131">Bereitstellen und Debuggen von UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="10545-131">Deploying and debugging UWP apps</span></span>](deploying-and-debugging-uwp-apps.md)
- [<span data-ttu-id="10545-132">Debugging, Tests und Leistung</span><span class="sxs-lookup"><span data-stu-id="10545-132">Debugging, testing, and performance</span></span>](index.md)
