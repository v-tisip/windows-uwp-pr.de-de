---
Description: This guide helps you enlighten your app to handle enterprise data managed by Windows Information Protection (WIP) policy as well as personal data.
MSHAttr: PreferredLib:/library/windows/apps
Search.Product: eADQiWindows 10XVcnh
title: Entwicklerhandbuch für Windows Information Protection (WIP)
ms.date: 06/21/2017
ms.topic: article
keywords: Windows10, UWP, WIP, Windows Information Protection, Unternehmensdaten, Unternehmensdatenschutz, edp, optimierte Apps
ms.assetid: 913ac957-ea49-43b0-91b3-e0f6ca01ef2c
ms.localizationpriority: medium
ms.openlocfilehash: 229d97c137344de26be0168be437825bea8e9700
ms.sourcegitcommit: 231065c899d0de285584d41e6335251e0c2c4048
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "8827125"
---
# <a name="windows-information-protection-wip-developer-guide"></a><span data-ttu-id="21565-103">Entwicklerhandbuch für Windows Information Protection (WIP)</span><span class="sxs-lookup"><span data-stu-id="21565-103">Windows Information Protection (WIP) developer guide</span></span>

<span data-ttu-id="21565-104">Eine *optimierte* App unterscheidet zwischen Firmen- oder persönlichen Daten und weiß, welche sie schützen soll, basierend auf Windows Information Protection (WIP)-Richtlinien, die vom Administrator definiert werden.</span><span class="sxs-lookup"><span data-stu-id="21565-104">An *enlightened* app differentiates between corporate and personal data and knows which to protect based on Windows Information Protection (WIP) policies defined by the administrator.</span></span>

<span data-ttu-id="21565-105">In diesem Handbuch zeigen wir Ihnen, wie eine erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="21565-105">In this guide, we'll show you how to build one.</span></span> <span data-ttu-id="21565-106">Wenn Sie fertig sind, werden Richtlinienadministratoren Ihrer App vertrauen, Daten für ihre Organisation zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="21565-106">When you're done, policy administrators will be able to trust your app to consume their organization's data.</span></span> <span data-ttu-id="21565-107">Und Mitarbeiter schätzen es, dass ihre persönlichen Daten auf den Geräten unangetastet bleiben, auch wenn sie die Registrierung des Geräts in der mobilen Geräteverwaltung (Mobile Device Management, MDM) aufheben oder das Unternehmen ganz verlassen.</span><span class="sxs-lookup"><span data-stu-id="21565-107">And employees will love that you've kept their personal data intact on their device even if they un-enroll from the organization's mobile device management (MDM) or leave the organization entirely.</span></span>

<span data-ttu-id="21565-108">__Hinweis:__ Dieses Handbuch hilft Ihnen beim Optimieren einer UWP-App.</span><span class="sxs-lookup"><span data-stu-id="21565-108">__Note__ This guide helps you enlighten a UWP app.</span></span> <span data-ttu-id="21565-109">Wenn Sie eine C++-Windows-Desktop-App optimieren möchten, lesen Sie die Informationen unter [Entwicklerhandbuch für Windows Information Protection (WIP) (C++)](http://go.microsoft.com/fwlink/?LinkId=822192).</span><span class="sxs-lookup"><span data-stu-id="21565-109">If you want to enlighten a C++ Windows desktop app, see [Windows Information Protection (WIP) developer guide (C++)](http://go.microsoft.com/fwlink/?LinkId=822192).</span></span>

<span data-ttu-id="21565-110">Weitere Informationen zu WIP und optimierten Apps hier: [Windows Information Protection (WIP)](wip-hub.md).</span><span class="sxs-lookup"><span data-stu-id="21565-110">You can read more about WIP and enlightened apps here: [Windows Information Protection (WIP)](wip-hub.md).</span></span>

<span data-ttu-id="21565-111">Ein vollständiges Beispiel finden Sie [hier](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/EnterpriseDataProtection).</span><span class="sxs-lookup"><span data-stu-id="21565-111">You can find a complete sample [here](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/EnterpriseDataProtection).</span></span>

<span data-ttu-id="21565-112">Wenn Sie bereit sind, die einzelnen Aufgaben durchzugehen, lassen Sie uns starten.</span><span class="sxs-lookup"><span data-stu-id="21565-112">If you're ready to go through each task, let's start.</span></span>

## <a name="first-gather-what-you-need"></a><span data-ttu-id="21565-113">Sammeln Sie zuerst die gewünschten Informationen.</span><span class="sxs-lookup"><span data-stu-id="21565-113">First, gather what you need</span></span>

<span data-ttu-id="21565-114">Sie benötigen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="21565-114">You'll need these:</span></span>

* <span data-ttu-id="21565-115">Einen virtuellen Testcomputer mit Windows 10, Version 1607, oder höher.</span><span class="sxs-lookup"><span data-stu-id="21565-115">A test Virtual Machine (VM) that runs Windows 10, version 1607 or higher.</span></span> <span data-ttu-id="21565-116">Sie debuggen Ihre App unter Verwendung dieses virtuellen Testcomputers.</span><span class="sxs-lookup"><span data-stu-id="21565-116">You'll debug your app against this test VM.</span></span>

* <span data-ttu-id="21565-117">Einen Entwicklungscomputer mit Windows 10, Version 1607, oder höher.</span><span class="sxs-lookup"><span data-stu-id="21565-117">A development computer that runs Windows 10, version 1607 or higher.</span></span> <span data-ttu-id="21565-118">Dies kann Ihr virtueller Testcomputer sein, wenn Visual Studio darauf installiert ist.</span><span class="sxs-lookup"><span data-stu-id="21565-118">This could be your test VM if you have Visual Studio installed on it.</span></span>

## <a name="setup-your-development-environment"></a><span data-ttu-id="21565-119">Richten Sie Ihre Entwicklungsumgebung ein.</span><span class="sxs-lookup"><span data-stu-id="21565-119">Setup your development environment</span></span>

<span data-ttu-id="21565-120">Sie führen folgende Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="21565-120">You'll do these things:</span></span>

* [<span data-ttu-id="21565-121">Installieren Sie den WIP Setup Developer Assistant auf dem virtuellen Testcomputer.</span><span class="sxs-lookup"><span data-stu-id="21565-121">Install the WIP Setup Developer Assistant onto your test VM</span></span>](#install-assistant)

* [<span data-ttu-id="21565-122">Erstellen Sie eine Schutzrichtlinie mit dem WIP Setup Developer Assistant.</span><span class="sxs-lookup"><span data-stu-id="21565-122">Create a protection policy by using the WIP Setup Developer Assistant</span></span>](#create-protection-policy)

* [<span data-ttu-id="21565-123">Richten Sie ein Visual Studio-Projekt ein.</span><span class="sxs-lookup"><span data-stu-id="21565-123">Setup a Visual Studio project</span></span>](#setup-vs-project)

* [<span data-ttu-id="21565-124">Richten Sie das Remotedebuggen ein.</span><span class="sxs-lookup"><span data-stu-id="21565-124">Setup remote debugging</span></span>](#setup-remote-debugging)

* [<span data-ttu-id="21565-125">Fügen Sie die Namespaces zu Ihren Codedateien hinzu.</span><span class="sxs-lookup"><span data-stu-id="21565-125">Add namespaces to your code files</span></span>](#add-namespaces)

<a id="install-assistant" />

### <a name="install-the-wip-setup-developer-assistant-onto-your-test-vm"></a><span data-ttu-id="21565-126">Installieren Sie den WIP Setup Developer Assistant auf dem virtuellen Testcomputer.</span><span class="sxs-lookup"><span data-stu-id="21565-126">Install the WIP Setup Developer Assistant onto your test VM</span></span>

 <span data-ttu-id="21565-127">Verwenden Sie dieses Tool, um eine Windows Information Protection-Richtlinie auf Ihrem virtuellen Testcomputer einzurichten.</span><span class="sxs-lookup"><span data-stu-id="21565-127">Use this tool to setup a Windows Information Protection policy on your test VM.</span></span>

 <span data-ttu-id="21565-128">Laden Sie das Tool hier herunter: [WIP Setup Developer Assistant](https://www.microsoft.com/store/p/wip-setup-developer-assistant/9nblggh526jf).</span><span class="sxs-lookup"><span data-stu-id="21565-128">Download the tool here: [WIP Setup Developer Assistant](https://www.microsoft.com/store/p/wip-setup-developer-assistant/9nblggh526jf).</span></span>

<a id="create-protection-policy" />

### <a name="create-a-protection-policy"></a><span data-ttu-id="21565-129">Erstellen Sie eine Schutzrichtlinie.</span><span class="sxs-lookup"><span data-stu-id="21565-129">Create a protection policy</span></span>

<span data-ttu-id="21565-130">Definieren Sie die Richtlinie, indem Sie in jedem Abschnitt des WIP Setup Developer Assistant Informationen eingeben.</span><span class="sxs-lookup"><span data-stu-id="21565-130">Define your policy by adding information to each section in the WIP setup developer assistant.</span></span> <span data-ttu-id="21565-131">Um mehr über die Verwendung der einzelnen Einstellungen zu erfahren, wählen Sie das daneben angezeigte Hilfesymbol aus.</span><span class="sxs-lookup"><span data-stu-id="21565-131">Choose the help icon next to any setting to learn more about how to use it.</span></span>

<span data-ttu-id="21565-132">Allgemeine Informationen zur Verwendung dieses Tools finden Sie im Abschnitt „Versionshinweise“ auf der Downloadseite der App.</span><span class="sxs-lookup"><span data-stu-id="21565-132">For more general guidance about how to use this tool, see the Version notes section on the app download page.</span></span>

<a id="setup-vs-project" />

### <a name="setup-a-visual-studio-project"></a><span data-ttu-id="21565-133">Richten Sie ein Visual Studio-Projekt ein.</span><span class="sxs-lookup"><span data-stu-id="21565-133">Setup a Visual Studio project</span></span>

1. <span data-ttu-id="21565-134">Öffnen Sie das Projekt auf Ihrem Entwicklungscomputer.</span><span class="sxs-lookup"><span data-stu-id="21565-134">On your development computer, open your project.</span></span>

2. <span data-ttu-id="21565-135">Fügen Sie einen Verweis auf die Desktop- und Mobilerweiterungen für die Universelle Windows-Plattform (UWP) hinzu.</span><span class="sxs-lookup"><span data-stu-id="21565-135">Add a reference to the desktop and mobile extensions for Universal Windows Platform (UWP).</span></span>

    ![UWP-Erweiterungen hinzufügen](images/extensions.png)

3. <span data-ttu-id="21565-137">Fügen Sie diese Funktion der Paketmanifestdatei hinzu:</span><span class="sxs-lookup"><span data-stu-id="21565-137">Add this capability to your package manifest file:</span></span>

    ```xml
       <rescap:Capability Name="enterpriseDataPolicy"/>
    ```
   ><span data-ttu-id="21565-138">*Optionale Info*: Das Präfix „Rescap“ bedeutet *eingeschränkte Funktion*.</span><span class="sxs-lookup"><span data-stu-id="21565-138">*Optional Reading*: The "rescap" prefix means *Restricted Capability*.</span></span> <span data-ttu-id="21565-139">Siehe [Spezielle und eingeschränkte Funktionen](https://msdn.microsoft.com/windows/uwp/packaging/app-capability-declarations).</span><span class="sxs-lookup"><span data-stu-id="21565-139">See [Special and restricted capabilities](https://msdn.microsoft.com/windows/uwp/packaging/app-capability-declarations).</span></span>

4. <span data-ttu-id="21565-140">Fügen Sie diesen Namespace der Paketmanifestdatei hinzu:</span><span class="sxs-lookup"><span data-stu-id="21565-140">Add this namespace to your package manifest file:</span></span>

    ```xml
      xmlns:rescap="http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities"
    ```
5. <span data-ttu-id="21565-141">Fügen Sie das Namespacepräfix dem ``<ignorableNamespaces>``-Element der Paketmanifestdatei hinzu.</span><span class="sxs-lookup"><span data-stu-id="21565-141">Add the namespace prefix to the ``<ignorableNamespaces>`` element of your package manifest file.</span></span>

    ```xml
        <IgnorableNamespaces="uap mp rescap">
    ```

    <span data-ttu-id="21565-142">Auf diese Weise ignoriert Windows die ``enterpriseDataPolicy``-Funktion, wenn Ihre App auf einer Version des Windows-Betriebssystems ausgeführt wird, die eingeschränkte Funktionen nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="21565-142">This way, if your app runs on a version of the Windows operating system that doesn't support restricted capabilities, Windows will ignore the ``enterpriseDataPolicy`` capability.</span></span>

<a id="setup-remote-debugging" />

### <a name="setup-remote-debugging"></a><span data-ttu-id="21565-143">Richten Sie das Remotedebuggen ein.</span><span class="sxs-lookup"><span data-stu-id="21565-143">Setup remote debugging</span></span>

<span data-ttu-id="21565-144">Installieren Sie Visual Studio-Remotetools auf Ihrem virtuellen Testcomputer nur dann, wenn Sie Ihre App auf einem anderem Computer als einem virtuellen Computer entwickeln.</span><span class="sxs-lookup"><span data-stu-id="21565-144">Install Visual Studio Remote Tools on your test VM only if you are developing your app on a computer other than your VM.</span></span> <span data-ttu-id="21565-145">Starten Sie den Remotedebugger auf dem Entwicklungscomputer, und überprüfen Sie, ob Ihre App auf dem virtuellen Testcomputer ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="21565-145">Then, on your development computer start the remote debugger and see if your app runs on the test VM.</span></span>

<span data-ttu-id="21565-146">Siehe [Anweisungen zu Remote-PCs](https://msdn.microsoft.com/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#remote-pc-instructions).</span><span class="sxs-lookup"><span data-stu-id="21565-146">See [Remote PC instructions](https://msdn.microsoft.com/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#remote-pc-instructions).</span></span>

<a id="add-namespaces" />

### <a name="add-these-namespaces-to-your-code-files"></a><span data-ttu-id="21565-147">Fügen Sie diese Namespaces zu Ihren Codedateien hinzu.</span><span class="sxs-lookup"><span data-stu-id="21565-147">Add these namespaces to your code files</span></span>

<span data-ttu-id="21565-148">Fügen Sie diese using-Anweisungen am Anfang Ihrer Codedateien ein (Verwenden Sie Codeausschnitte aus diesem Handbuch):</span><span class="sxs-lookup"><span data-stu-id="21565-148">Add these using statements to the top of your code files(The snippets in this guide use them):</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Windows.Security.EnterpriseData;
using Windows.Web.Http;
using Windows.Storage.Streams;
using Windows.ApplicationModel.DataTransfer;
using Windows.UI.Xaml.Controls;
using Windows.UI.Xaml;
using Windows.ApplicationModel.Activation;
using Windows.Web.Http.Filters;
using Windows.Storage;
using Windows.Data.Xml.Dom;
using Windows.Foundation.Metadata;
using Windows.Web.Http.Headers;
```

## <a name="determine-whether-to-use-wip-apis-in-your-app"></a><span data-ttu-id="21565-149">Bestimmen Sie, ob WIP-APIs in Ihrer App verwendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="21565-149">Determine whether to use WIP APIs in your app</span></span>

<span data-ttu-id="21565-150">Stellen Sie sicher, dass das Betriebssystem, das Ihre App ausführt, WIP unterstützt und WIP auf dem Gerät aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="21565-150">Ensure that the operating system that runs your app supports WIP and that WIP is enabled on the device.</span></span>

```csharp
bool use_WIP_APIs = false;

if ((ApiInformation.IsApiContractPresent
    ("Windows.Security.EnterpriseData.EnterpriseDataContract", 3)
    && ProtectionPolicyManager.IsProtectionEnabled))
{
    use_WIP_APIs = true;
}
else
{
    use_WIP_APIs = false;
}
```
<span data-ttu-id="21565-151">Rufen Sie keine WIP-APIs auf, wenn das Betriebssystem WIP nicht unterstützt oder WIP nicht auf dem Gerät aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="21565-151">Don't call WIP APIs if the operating system doesn't support WIP or WIP is not enabled on the device.</span></span>

## <a name="read-enterprise-data"></a><span data-ttu-id="21565-152">Lesen von Unternehmensdaten</span><span class="sxs-lookup"><span data-stu-id="21565-152">Read enterprise data</span></span>

<span data-ttu-id="21565-153">Ihre App muss Zugriff anfordern, um geschützte Dateien, Netzwerkendpunkte, Daten aus der Zwischenablage und Daten zu lesen, die Sie von einem Freigabe-Vertrag akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="21565-153">To read protected files, network endpoints, clipboard data and data that you accept from a Share contract, your app will have to request access.</span></span>

<span data-ttu-id="21565-154">Windows Information Protection erteilt Ihrer App die Berechtigung, wenn Ihre App in der Liste der zugelassenen Apps der Schutzrichtlinie enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="21565-154">Windows Information Protection gives your app permission if your app is on the protection policy's allowed list.</span></span>

**<span data-ttu-id="21565-155">In diesem Abschnitt:</span><span class="sxs-lookup"><span data-stu-id="21565-155">In this section:</span></span>**

* [<span data-ttu-id="21565-156">Lesen von Daten aus einer Datei</span><span class="sxs-lookup"><span data-stu-id="21565-156">Read data from a file</span></span>](#read-file)
* [<span data-ttu-id="21565-157">Lesen Sie Daten von einem Netzwerkendpunkt aus</span><span class="sxs-lookup"><span data-stu-id="21565-157">Read data from a network endpoint</span></span>](#read-network)
* [<span data-ttu-id="21565-158">Daten aus der Zwischenablage lesen</span><span class="sxs-lookup"><span data-stu-id="21565-158">Read data from the clipboard</span></span>](#read-clipboard)
* [<span data-ttu-id="21565-159">Lesen von Daten aus einem Freigabe-Vertrag</span><span class="sxs-lookup"><span data-stu-id="21565-159">Read data from a Share contract</span></span>](#read-share)

<a id="read-file" />

### <a name="read-data-from-a-file"></a><span data-ttu-id="21565-160">Lesen von Daten aus einer Datei</span><span class="sxs-lookup"><span data-stu-id="21565-160">Read data from a file</span></span>

**<span data-ttu-id="21565-161">Schritt 1: Dateihandle herunterladen</span><span class="sxs-lookup"><span data-stu-id="21565-161">Step 1: Get the file handle</span></span>**

```csharp
    Windows.Storage.StorageFolder storageFolder =
        Windows.Storage.ApplicationData.Current.LocalFolder;

    Windows.Storage.StorageFile file =
        await storageFolder.GetFileAsync(fileName);
```

**<span data-ttu-id="21565-162">Schritt 2: Stellen Sie fest, ob Ihre App die Datei öffnen kann</span><span class="sxs-lookup"><span data-stu-id="21565-162">Step 2: Determine whether your app can open the file</span></span>**

<span data-ttu-id="21565-163">Rufen Sie [FileProtectionManager.GetProtectionInfoAsync](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.fileprotectionmanager.getprotectioninfoasync.aspx) auf, um festzustellen, ob Ihre App die Datei öffnen kann.</span><span class="sxs-lookup"><span data-stu-id="21565-163">Call [FileProtectionManager.GetProtectionInfoAsync](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.fileprotectionmanager.getprotectioninfoasync.aspx) to determine whether your app can open the file.</span></span>

```csharp
FileProtectionInfo protectionInfo = await FileProtectionManager.GetProtectionInfoAsync(file);

if ((protectionInfo.Status != FileProtectionStatus.Protected &&
    protectionInfo.Status != FileProtectionStatus.Unprotected))
{
    return false;
}
else if (protectionInfo.Status == FileProtectionStatus.Revoked)
{
    // Code goes here to handle this situation. Perhaps, show UI
    // saying that the user's data has been revoked.
}
```

<span data-ttu-id="21565-164">Ein [FileProtectionStatus](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.fileprotectionstatus.aspx)-Wert von **Geschützt** bedeutet, dass die Datei geschützt ist und Ihre App sie öffnen kann, da Ihre App in der Liste der zugelassenen Apps der Richtlinie enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="21565-164">A [FileProtectionStatus](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.fileprotectionstatus.aspx) value of **Protected** means that the file is protected and your app can open it because your app is on the policy's allowed list.</span></span>

<span data-ttu-id="21565-165">Ein [FileProtectionStatus](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.fileprotectionstatus.aspx)-Wert von **Ungeschützt** bedeutet, dass die Datei nicht geschützt ist, und Ihre App die Datei sogar öffnen kann, wenn Sie nicht in der Liste der zugelassenen Apps der Richtlinie enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="21565-165">A [FileProtectionStatus](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.fileprotectionstatus.aspx) value of **UnProtected** means that the file is not protected and your app can open the file even your app is not on the policy's allowed list.</span></span>

> **<span data-ttu-id="21565-166">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-166">APIs</span></span>** <br>
[<span data-ttu-id="21565-167">FileProtectionManager.GetProtectionInfoAsync</span><span class="sxs-lookup"><span data-stu-id="21565-167">FileProtectionManager.GetProtectionInfoAsync</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.fileprotectionmanager.getprotectioninfoasync.aspx)<br>
[<span data-ttu-id="21565-168">FileProtectionInfo</span><span class="sxs-lookup"><span data-stu-id="21565-168">FileProtectionInfo</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.fileprotectioninfo.aspx)<br>
[<span data-ttu-id="21565-169">FileProtectionStatus</span><span class="sxs-lookup"><span data-stu-id="21565-169">FileProtectionStatus</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.fileprotectionstatus.aspx)<br>
[<span data-ttu-id="21565-170">ProtectionPolicyManager.IsIdentityManaged</span><span class="sxs-lookup"><span data-stu-id="21565-170">ProtectionPolicyManager.IsIdentityManaged</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.isidentitymanaged.aspx)

**<span data-ttu-id="21565-171">Schritt 3: Lesen Sie die Datei in einen Datenstrom oder Puffer ein</span><span class="sxs-lookup"><span data-stu-id="21565-171">Step 3: Read the file into a stream or buffer</span></span>**

*<span data-ttu-id="21565-172">Lesen Sie die Datei in einen Datenstrom</span><span class="sxs-lookup"><span data-stu-id="21565-172">Read the file into a stream</span></span>*

```csharp
var stream = await file.OpenAsync(Windows.Storage.FileAccessMode.ReadWrite);
```

*<span data-ttu-id="21565-173">Lesen Sie die Datei in einen Puffer</span><span class="sxs-lookup"><span data-stu-id="21565-173">Read the file into a buffer</span></span>*

```csharp
var buffer = await Windows.Storage.FileIO.ReadBufferAsync(file);
```
<a id="read-network" />

### <a name="read-data-from-a-network-endpoint"></a><span data-ttu-id="21565-174">Lesen Sie Daten von einem Netzwerkendpunkt aus</span><span class="sxs-lookup"><span data-stu-id="21565-174">Read data from a network endpoint</span></span>

<span data-ttu-id="21565-175">Erstellen Sie einen geschützten Threadkontext zum Lesen aus einem Unternehmens-Endpunkt.</span><span class="sxs-lookup"><span data-stu-id="21565-175">Create a protected thread context to read from an enterprise endpoint.</span></span>

**<span data-ttu-id="21565-176">Schritt 1: Abrufen der Identität des Netzwerkendpunktes</span><span class="sxs-lookup"><span data-stu-id="21565-176">Step 1: Get the identity of the network endpoint</span></span>**

```csharp
Uri resourceURI = new Uri("http://contoso.com/stockData.xml");

Windows.Networking.HostName hostName =
    new Windows.Networking.HostName(resourceURI.Host);

string identity = await ProtectionPolicyManager.
    GetPrimaryManagedIdentityForNetworkEndpointAsync(hostName);
```

<span data-ttu-id="21565-177">Wenn der Endpunkt nicht mithilfe der Gruppenrichtlinie verwaltet wird, erhalten Sie einen leeren String zurück.</span><span class="sxs-lookup"><span data-stu-id="21565-177">If the endpoint isn't managed by policy, you'll get back an empty string.</span></span>

> **<span data-ttu-id="21565-178">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-178">APIs</span></span>** <br>
[<span data-ttu-id="21565-179">ProtectionPolicyManager.GetPrimaryManagedIdentityForNetworkEndpointAsync</span><span class="sxs-lookup"><span data-stu-id="21565-179">ProtectionPolicyManager.GetPrimaryManagedIdentityForNetworkEndpointAsync</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.getprimarymanagedidentityfornetworkendpointasync.aspx)


**<span data-ttu-id="21565-180">Schritt 2: Erstellen eines geschützten Threadkontexts</span><span class="sxs-lookup"><span data-stu-id="21565-180">Step 2: Create a protected thread context</span></span>**

<span data-ttu-id="21565-181">Wenn der Endpunkt durch die Richtlinie verwaltet wird, erstellen Sie einen geschützten Threadkontext.</span><span class="sxs-lookup"><span data-stu-id="21565-181">If the endpoint is managed by policy, create a protected thread context.</span></span> <span data-ttu-id="21565-182">Dadurch werden alle Netzwerkverbindungen markiert, die mit dieser Identität auf demselben Thread hergestellt werden.</span><span class="sxs-lookup"><span data-stu-id="21565-182">This tags any network connections that you make on the same thread to the identity.</span></span>

<span data-ttu-id="21565-183">Sie erhalten auch Zugriff auf Unternehmensnetzwerkressourcen, die von dieser Richtlinie verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="21565-183">It also gives you access to enterprise network resources that are managed by that policy.</span></span>

```csharp
if (!string.IsNullOrEmpty(identity))
{
    using (ThreadNetworkContext threadNetworkContext =
            ProtectionPolicyManager.CreateCurrentThreadNetworkContext(identity))
    {
        return await GetDataFromNetworkRedirectHelperMethod(resourceURI);
    }
}
else
{
    return await GetDataFromNetworkRedirectHelperMethod(resourceURI);
}
```
<span data-ttu-id="21565-184">Dieses Beispiel umschließt Socket-Aufrufe in einem ``using``-Block.</span><span class="sxs-lookup"><span data-stu-id="21565-184">This example encloses socket calls in a ``using`` block.</span></span> <span data-ttu-id="21565-185">Wenn Sie dies nicht tun, stellen Sie sicher, dass Sie den Threadkontext schließen, nachdem Sie die Ressource abgerufen haben.</span><span class="sxs-lookup"><span data-stu-id="21565-185">If you don't do this, make sure that you close the thread context after you've retrieved your resource.</span></span> <span data-ttu-id="21565-186">Siehe [ThreadNetworkContext.Close](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.threadnetworkcontext.close.aspx).</span><span class="sxs-lookup"><span data-stu-id="21565-186">See [ThreadNetworkContext.Close](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.threadnetworkcontext.close.aspx).</span></span>

<span data-ttu-id="21565-187">Erstellen Sie keine persönlichen Dateien auf geschützten Threads, da diese Dateien automatisch verschlüsselt werden.</span><span class="sxs-lookup"><span data-stu-id="21565-187">Don't create any personal files on that protected thread because those files will be automatically encrypted.</span></span>

<span data-ttu-id="21565-188">Die [**ProtectionPolicyManager.CreateCurrentThreadNetworkContext**](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.createcurrentthreadnetworkcontext.aspx)-Methode gibt ein [**ThreadNetworkContext**](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.threadnetworkcontext.aspx)-Objekt zurück, unabhängig davon, ob der Endpunkt durch die Richtlinie verwaltet wird.</span><span class="sxs-lookup"><span data-stu-id="21565-188">The [**ProtectionPolicyManager.CreateCurrentThreadNetworkContext**](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.createcurrentthreadnetworkcontext.aspx) method returns a [**ThreadNetworkContext**](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.threadnetworkcontext.aspx) object whether or not the endpoint is being managed by policy.</span></span> <span data-ttu-id="21565-189">Wenn Ihre App persönliche und Unternehmensressourcen behandelt, rufen Sie [**ProtectionPolicyManager.CreateCurrentThreadNetworkContext**](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.createcurrentthreadnetworkcontext.aspx) für alle Identitäten auf.</span><span class="sxs-lookup"><span data-stu-id="21565-189">If your app handles both personal and enterprise resources, call [**ProtectionPolicyManager.CreateCurrentThreadNetworkContext**](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.createcurrentthreadnetworkcontext.aspx) for all identities.</span></span>  <span data-ttu-id="21565-190">Nachdem Sie die Ressource erhalten haben, geben Sie den ThreadNetworkContext frei, um jedes Identitätstag des aktuellen Threads zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="21565-190">After you get the resource, dispose the ThreadNetworkContext to clear any identity tag from the current thread.</span></span>

> **<span data-ttu-id="21565-191">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-191">APIs</span></span>** <br>
[<span data-ttu-id="21565-192">ProtectionPolicyManager.GetForCurrentView</span><span class="sxs-lookup"><span data-stu-id="21565-192">ProtectionPolicyManager.GetForCurrentView</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.getforcurrentview.aspx)<br>
[<span data-ttu-id="21565-193">ProtectionPolicyManager.Identity</span><span class="sxs-lookup"><span data-stu-id="21565-193">ProtectionPolicyManager.Identity</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.aspx)<br>
[<span data-ttu-id="21565-194">ProtectionPolicyManager.CreateCurrentThreadNetworkContext</span><span class="sxs-lookup"><span data-stu-id="21565-194">ProtectionPolicyManager.CreateCurrentThreadNetworkContext</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.createcurrentthreadnetworkcontext.aspx)

**<span data-ttu-id="21565-195">Schritt 3: Lesen Sie die Ressource in einen Puffer</span><span class="sxs-lookup"><span data-stu-id="21565-195">Step 3: Read the resource into a buffer</span></span>**

```csharp
private static async Task<IBuffer> GetDataFromNetworkHelperMethod(Uri resourceURI)
{
    HttpClient client;

    client = new HttpClient();

    try { return await client.GetBufferAsync(resourceURI); }

    catch (Exception) { return null; }
}
```

**<span data-ttu-id="21565-196">(Optional) Verwenden eines Headertokens anstatt der Erstellung eines geschützten Threadkontexts</span><span class="sxs-lookup"><span data-stu-id="21565-196">(Optional) Use a header token instead of creating a protected thread context</span></span>**

```csharp
public static async Task<IBuffer> GetDataFromNetworkbyUsingHeader(Uri resourceURI)
{
    HttpClient client;

    Windows.Networking.HostName hostName =
        new Windows.Networking.HostName(resourceURI.Host);

    string identity = await ProtectionPolicyManager.
        GetPrimaryManagedIdentityForNetworkEndpointAsync(hostName);

    if (!string.IsNullOrEmpty(identity))
    {
        client = new HttpClient();

        HttpRequestHeaderCollection headerCollection = client.DefaultRequestHeaders;

        headerCollection.Add("X-MS-Windows-HttpClient-EnterpriseId", identity);

        return await GetDataFromNetworkbyUsingHeaderHelperMethod(client, resourceURI);
    }
    else
    {
        client = new HttpClient();
        return await GetDataFromNetworkbyUsingHeaderHelperMethod(client, resourceURI);
    }

}

private static async Task<IBuffer> GetDataFromNetworkbyUsingHeaderHelperMethod(HttpClient client, Uri resourceURI)
{

    try { return await client.GetBufferAsync(resourceURI); }

    catch (Exception) { return null; }
}
```

**<span data-ttu-id="21565-197">Handle-Seite leitet weiter</span><span class="sxs-lookup"><span data-stu-id="21565-197">Handle page redirects</span></span>**

<span data-ttu-id="21565-198">In einigen Fällen leitet ein Webserver Datenverkehr auf eine aktuellere Version einer Ressource weiter.</span><span class="sxs-lookup"><span data-stu-id="21565-198">Sometimes a web server will redirect traffic to a more current version of a resource.</span></span>

<span data-ttu-id="21565-199">Um damit umzugehen, stellen Sie Anfragen, bis der Antwortstatus Ihrer Anfrage den Wert **OK** hat.</span><span class="sxs-lookup"><span data-stu-id="21565-199">To handle this, make requests until the response status of your request has a value of **OK**.</span></span>

<span data-ttu-id="21565-200">Verwenden Sie dann den URI der Antwort, um die Identität des Endpunkts abzurufen.</span><span class="sxs-lookup"><span data-stu-id="21565-200">Then use the URI of that response to get the identity of the endpoint.</span></span> <span data-ttu-id="21565-201">Hier ist eine Möglichkeit, dies zu tun:</span><span class="sxs-lookup"><span data-stu-id="21565-201">Here's one way to do this:</span></span>

```csharp
private static async Task<IBuffer> GetDataFromNetworkRedirectHelperMethod(Uri resourceURI)
{
    HttpClient client = null;

    HttpBaseProtocolFilter filter = new HttpBaseProtocolFilter();
    filter.AllowAutoRedirect = false;

    client = new HttpClient(filter);

    HttpResponseMessage response = null;

        HttpRequestMessage message = new HttpRequestMessage(HttpMethod.Get, resourceURI);
        response = await client.SendRequestAsync(message);

    if (response.StatusCode == HttpStatusCode.MultipleChoices ||
        response.StatusCode == HttpStatusCode.MovedPermanently ||
        response.StatusCode == HttpStatusCode.Found ||
        response.StatusCode == HttpStatusCode.SeeOther ||
        response.StatusCode == HttpStatusCode.NotModified ||
        response.StatusCode == HttpStatusCode.UseProxy ||
        response.StatusCode == HttpStatusCode.TemporaryRedirect ||
        response.StatusCode == HttpStatusCode.PermanentRedirect)
    {
        message = new HttpRequestMessage(HttpMethod.Get, message.RequestUri);
        response = await client.SendRequestAsync(message);

        try { return await response.Content.ReadAsBufferAsync(); }

        catch (Exception) { return null; }
    }
    else
    {
        try { return await response.Content.ReadAsBufferAsync(); }

        catch (Exception) { return null; }
    }
}

```

> **<span data-ttu-id="21565-202">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-202">APIs</span></span>** <br>
[<span data-ttu-id="21565-203">ProtectionPolicyManager.GetPrimaryManagedIdentityForNetworkEndpointAsync</span><span class="sxs-lookup"><span data-stu-id="21565-203">ProtectionPolicyManager.GetPrimaryManagedIdentityForNetworkEndpointAsync</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.getprimarymanagedidentityfornetworkendpointasync.aspx)<br>
[<span data-ttu-id="21565-204">ProtectionPolicyManager.CreateCurrentThreadNetworkContext</span><span class="sxs-lookup"><span data-stu-id="21565-204">ProtectionPolicyManager.CreateCurrentThreadNetworkContext</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.createcurrentthreadnetworkcontext.aspx)<br>
[<span data-ttu-id="21565-205">ProtectionPolicyManager.GetForCurrentView</span><span class="sxs-lookup"><span data-stu-id="21565-205">ProtectionPolicyManager.GetForCurrentView</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.getforcurrentview.aspx)<br>
[<span data-ttu-id="21565-206">ProtectionPolicyManager.Identity</span><span class="sxs-lookup"><span data-stu-id="21565-206">ProtectionPolicyManager.Identity</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.aspx)

<a id="read-clipboard" />

### <a name="read-data-from-the-clipboard"></a><span data-ttu-id="21565-207">Daten aus der Zwischenablage lesen</span><span class="sxs-lookup"><span data-stu-id="21565-207">Read data from the clipboard</span></span>

**<span data-ttu-id="21565-208">Erhalten Sie die Berechtigung zum Verwenden von Daten aus der Zwischenablage</span><span class="sxs-lookup"><span data-stu-id="21565-208">Get permission to use data from the clipboard</span></span>**

<span data-ttu-id="21565-209">Zum Abrufen von Daten aus der Zwischenablage bitten Sie Windows um Erlaubnis.</span><span class="sxs-lookup"><span data-stu-id="21565-209">To get data from the clipboard, ask Windows for permission.</span></span> <span data-ttu-id="21565-210">Verwenden Sie dazu [**DataPackageView.RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/dn706645.aspx) .</span><span class="sxs-lookup"><span data-stu-id="21565-210">Use [**DataPackageView.RequestAccessAsync**](https://msdn.microsoft.com/library/windows/apps/dn706645.aspx) to do that.</span></span>

```csharp
public static async Task PasteText(TextBox textBox)
{
    DataPackageView dataPackageView = Clipboard.GetContent();

    if (dataPackageView.Contains(StandardDataFormats.Text))
    {
        ProtectionPolicyEvaluationResult result = await dataPackageView.RequestAccessAsync();

        if (result == ProtectionPolicyEvaluationResult..Allowed)
        {
            string contentsOfClipboard = await dataPackageView.GetTextAsync();
            textBox.Text = contentsOfClipboard;
        }
    }
}
```

> **<span data-ttu-id="21565-211">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-211">APIs</span></span>** <br>
[<span data-ttu-id="21565-212">DataPackageView.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="21565-212">DataPackageView.RequestAccessAsync</span></span>](https://msdn.microsoft.com/library/windows/apps/dn706645.aspx)

**<span data-ttu-id="21565-213">Ausblenden oder Deaktivieren von Features, die Daten aus der Zwischenablage verwenden</span><span class="sxs-lookup"><span data-stu-id="21565-213">Hide or disable features that use clipboard data</span></span>**

<span data-ttu-id="21565-214">Ermitteln Sie, ob die aktuelle Ansicht über die Berechtigung zum Abrufen von Daten, die sich in der Zwischenablage befinden, verfügt.</span><span class="sxs-lookup"><span data-stu-id="21565-214">Determine whether current view has permission to get data that is on the clipboard.</span></span>

<span data-ttu-id="21565-215">Wenn dies nicht der Fall ist, können Sie Steuerelemente, mit denen Benutzer Informationen aus der Zwischenablage einsetzen oder den Inhalt in der Vorschau anzeigen, deaktivieren oder ausblenden.</span><span class="sxs-lookup"><span data-stu-id="21565-215">If it doesn't, you can disable or hide controls that let users paste information from the clipboard or preview its contents.</span></span>

```csharp
private bool IsClipboardAllowedAsync()
{
    ProtectionPolicyEvaluationResult protectionPolicyEvaluationResult = ProtectionPolicyEvaluationResult.Blocked;

    DataPackageView dataPackageView = Clipboard.GetContent();

    if (dataPackageView.Contains(StandardDataFormats.Text))

        protectionPolicyEvaluationResult =
            ProtectionPolicyManager.CheckAccess(dataPackageView.Properties.EnterpriseId,
                ProtectionPolicyManager.GetForCurrentView().Identity);

    return (protectionPolicyEvaluationResult == ProtectionPolicyEvaluationResult.Allowed |
        protectionPolicyEvaluationResult == ProtectionPolicyEvaluationResult.ConsentRequired);
}
```

> **<span data-ttu-id="21565-216">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-216">APIs</span></span>** <br>
[<span data-ttu-id="21565-217">ProtectionPolicyEvaluationResult</span><span class="sxs-lookup"><span data-stu-id="21565-217">ProtectionPolicyEvaluationResult</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicyevaluationresult.aspx)<br>
[<span data-ttu-id="21565-218">ProtectionPolicyManager.GetForCurrentView</span><span class="sxs-lookup"><span data-stu-id="21565-218">ProtectionPolicyManager.GetForCurrentView</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.getforcurrentview.aspx)<br>
[<span data-ttu-id="21565-219">ProtectionPolicyManager.Identity</span><span class="sxs-lookup"><span data-stu-id="21565-219">ProtectionPolicyManager.Identity</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.aspx)

**<span data-ttu-id="21565-220">Verhindern Sie, dass Benutzer mit einem Dialogfeld zur Zustimmung aufgefordert werden</span><span class="sxs-lookup"><span data-stu-id="21565-220">Prevent users from being prompted with a consent dialog box</span></span>**

<span data-ttu-id="21565-221">Ein neues Dokument ist nicht *persönlich* oder *Unternehmen*.</span><span class="sxs-lookup"><span data-stu-id="21565-221">A new document isn't *personal* or *enterprise*.</span></span> <span data-ttu-id="21565-222">Es ist einfach neu.</span><span class="sxs-lookup"><span data-stu-id="21565-222">It's just new.</span></span> <span data-ttu-id="21565-223">Wenn ein Benutzer Unternehmensdaten in die Datei einsetzt, setzt Windows Richtlinien durch und der Benutzer wird aufgefordert, einem Dialogfeld zuzustimmen.</span><span class="sxs-lookup"><span data-stu-id="21565-223">If a user pastes enterprise data into it, Windows enforces policy and the user is prompted with a consent dialog.</span></span> <span data-ttu-id="21565-224">Dieser Code verhindert, dass dies geschieht.</span><span class="sxs-lookup"><span data-stu-id="21565-224">This code prevents that from happening.</span></span> <span data-ttu-id="21565-225">Es geht bei dieser Aufgabe nicht darum, Daten zu schützen.</span><span class="sxs-lookup"><span data-stu-id="21565-225">This task is not about helping to protect data.</span></span> <span data-ttu-id="21565-226">Es geht mehr darum, Benutzer davon abzuhalten, Dialogfelder zur Zustimmung zu sehen – in Fällen, in denen Ihre App ein völlig neues Element erstellt hat.</span><span class="sxs-lookup"><span data-stu-id="21565-226">It's more about keeping users from receiving the consent dialog box in cases where your app creates a brand new item.</span></span>

```csharp
private async void PasteText(bool isNewEmptyDocument)
{
    DataPackageView dataPackageView = Clipboard.GetContent();

    if (dataPackageView.Contains(StandardDataFormats.Text))
    {
        if (!string.IsNullOrEmpty(dataPackageView.Properties.EnterpriseId))
        {
            if (isNewEmptyDocument)
            {
                ProtectionPolicyManager.TryApplyProcessUIPolicy(dataPackageView.Properties.EnterpriseId);
                string contentsOfClipboard = contentsOfClipboard = await dataPackageView.GetTextAsync();
                // add this string to the new item or document here.          

            }
            else
            {
                ProtectionPolicyEvaluationResult result = await dataPackageView.RequestAccessAsync();

                if (result == ProtectionPolicyEvaluationResult.Allowed)
                {
                    string contentsOfClipboard = contentsOfClipboard = await dataPackageView.GetTextAsync();
                    // add this string to the new item or document here.
                }
            }
        }
    }
}
```

> **<span data-ttu-id="21565-227">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-227">APIs</span></span>** <br>
[<span data-ttu-id="21565-228">DataPackageView.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="21565-228">DataPackageView.RequestAccessAsync</span></span>](https://msdn.microsoft.com/library/windows/apps/dn706645.aspx)<br>
[<span data-ttu-id="21565-229">ProtectionPolicyEvaluationResult</span><span class="sxs-lookup"><span data-stu-id="21565-229">ProtectionPolicyEvaluationResult</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicyevaluationresult.aspx)<br>
[<span data-ttu-id="21565-230">ProtectionPolicyManager.TryApplyProcessUIPolicy</span><span class="sxs-lookup"><span data-stu-id="21565-230">ProtectionPolicyManager.TryApplyProcessUIPolicy</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.tryapplyprocessuipolicy.aspx)

<a id="read-share" />

### <a name="read-data-from-a-share-contract"></a><span data-ttu-id="21565-231">Lesen von Daten aus einem Freigabe-Vertrag</span><span class="sxs-lookup"><span data-stu-id="21565-231">Read data from a Share contract</span></span>

<span data-ttu-id="21565-232">Wenn Mitarbeiter zur Freigabe ihrer Informationen Ihre App auswählen, öffnet Ihre App ein neues Element, das diese Inhalte enthält.</span><span class="sxs-lookup"><span data-stu-id="21565-232">When employees choose your app to share their information, your app will open a new item that contains that content.</span></span>

<span data-ttu-id="21565-233">Wie bereits erwähnt, wird ein neues Element nicht *persönlich* oder *Unternehmen*.</span><span class="sxs-lookup"><span data-stu-id="21565-233">As we mentioned earlier, a new item isn't *personal* or *enterprise*.</span></span> <span data-ttu-id="21565-234">Es ist einfach neu.</span><span class="sxs-lookup"><span data-stu-id="21565-234">It's just new.</span></span> <span data-ttu-id="21565-235">Wenn Ihr Code Unternehmensinhalt zu dem Element hinzufügt, setzt Windows Richtlinien durch und der Benutzer wird mit einem Zustimmungsdialogfeld aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="21565-235">If your code adds enterprise content to the item, Windows enforces policy and the user is prompted with a consent dialog.</span></span> <span data-ttu-id="21565-236">Dieser Code verhindert, dass dies geschieht.</span><span class="sxs-lookup"><span data-stu-id="21565-236">This code prevents that from happening.</span></span>

```csharp
protected override async void OnShareTargetActivated(ShareTargetActivatedEventArgs args)
{
    bool isNewEmptyDocument = true;
    string identity = "corp.microsoft.com";

    ShareOperation shareOperation = args.ShareOperation;
    if (shareOperation.Data.Contains(StandardDataFormats.Text))
    {
        if (!string.IsNullOrEmpty(shareOperation.Data.Properties.EnterpriseId))
        {
            if (isNewEmptyDocument)
                // If this is a new and empty document, and we're allowed to access
                // the data, then we can avoid popping the consent dialog
                ProtectionPolicyManager.TryApplyProcessUIPolicy(shareOperation.Data.Properties.EnterpriseId);
            else
            {
                // In this case, we can't optimize the workflow, so we just
                // request consent from the user in this case.

                ProtectionPolicyEvaluationResult protectionPolicyEvaluationResult = await shareOperation.Data.RequestAccessAsync();

                if (protectionPolicyEvaluationResult == ProtectionPolicyEvaluationResult.Allowed)
                {
                    string text = await shareOperation.Data.GetTextAsync();

                    // Do something with that text.
                }
            }
        }
        else
        {
            // If the data has no enterprise identity, then we already have access.
            string text = await shareOperation.Data.GetTextAsync();

            // Do something with that text.
        }

    }

}
```

> **<span data-ttu-id="21565-237">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-237">APIs</span></span>** <br>
[<span data-ttu-id="21565-238">ProtectionPolicyManager.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="21565-238">ProtectionPolicyManager.RequestAccessAsync</span></span>](https://msdn.microsoft.com/library/windows/apps/dn705789.aspx)<br>
[<span data-ttu-id="21565-239">ProtectionPolicyEvaluationResult</span><span class="sxs-lookup"><span data-stu-id="21565-239">ProtectionPolicyEvaluationResult</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicyevaluationresult.aspx)<br>
[<span data-ttu-id="21565-240">ProtectionPolicyManager.TryApplyProcessUIPolicy</span><span class="sxs-lookup"><span data-stu-id="21565-240">ProtectionPolicyManager.TryApplyProcessUIPolicy</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.tryapplyprocessuipolicy.aspx)

## <a name="protect-enterprise-data"></a><span data-ttu-id="21565-241">Unternehmensdaten schützen</span><span class="sxs-lookup"><span data-stu-id="21565-241">Protect enterprise data</span></span>

<span data-ttu-id="21565-242">Schützen Sie Unternehmensdaten, die Ihre App verlassen.</span><span class="sxs-lookup"><span data-stu-id="21565-242">Protect enterprise data that leaves your app.</span></span> <span data-ttu-id="21565-243">Daten verlassen Ihre App, wenn Sie diese auf einer Seite zeigen. Sichern Sie sie in einer Datei oder einem Netzwerkendpunkt oder über einen Freigabe-Vertrag.</span><span class="sxs-lookup"><span data-stu-id="21565-243">Data leaves your app when you show it in a page, save it to a file or network endpoint, or through a share contract.</span></span>

**<span data-ttu-id="21565-244">In diesem Abschnitt:</span><span class="sxs-lookup"><span data-stu-id="21565-244">In this section:</span></span>**

* [<span data-ttu-id="21565-245">Schützen Sie Daten, die auf Seiten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="21565-245">Protect data that appears in pages</span></span>](#protect-pages)
* [<span data-ttu-id="21565-246">Schützen von Daten in einer Datei als Hintergrundprozess</span><span class="sxs-lookup"><span data-stu-id="21565-246">Protect data to a file as a background process</span></span>](#protect-background)
* [<span data-ttu-id="21565-247">Einen Teil einer Datei schützen</span><span class="sxs-lookup"><span data-stu-id="21565-247">Protect part of a file</span></span>](#protect-part-file)
* [<span data-ttu-id="21565-248">Lesen Sie den geschützten Teil einer Datei.</span><span class="sxs-lookup"><span data-stu-id="21565-248">Read the protected part of a file</span></span>](#read-protected)
* [<span data-ttu-id="21565-249">Schützen Sie Daten in einem Ordner.</span><span class="sxs-lookup"><span data-stu-id="21565-249">Protect data to a folder</span></span>](#protect-folder)
* [<span data-ttu-id="21565-250">Schützen Sie Daten in einem Netzwerkendpunkt.</span><span class="sxs-lookup"><span data-stu-id="21565-250">Protect data to a network end point</span></span>](#protect-network)
* [<span data-ttu-id="21565-251">Schützen Sie Daten, die Ihre App über einen Freigabe-Vertrag teilt.</span><span class="sxs-lookup"><span data-stu-id="21565-251">Protect data that your app shares through a share contract</span></span>](#protect-share)
* [<span data-ttu-id="21565-252">Schützen von Dateien, die Sie an einen anderen Speicherort kopieren</span><span class="sxs-lookup"><span data-stu-id="21565-252">Protect files that you copy to another location</span></span>](#protect-other-location)
* [<span data-ttu-id="21565-253">Unternehmensdaten schützen, wenn der Bildschirm des Geräts gesperrt ist</span><span class="sxs-lookup"><span data-stu-id="21565-253">Protect enterprise data when the screen of the device is locked</span></span>](#protect-locked)

<a id="protect-pages" />

### <a name="protect-data-that-appears-in-pages"></a><span data-ttu-id="21565-254">Schützen Sie Daten, die auf Seiten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="21565-254">Protect data that appears in pages</span></span>

<span data-ttu-id="21565-255">Wenn Sie Daten auf einer Seite anzeigen, können Sie Windows mitteilen, um welche Art von Daten es sich handelt (persönlich oder Unternehmen).</span><span class="sxs-lookup"><span data-stu-id="21565-255">When you show data in a page, let Windows know what type of data it is (personal or enterprise).</span></span> <span data-ttu-id="21565-256">Zu diesem Zweck *markieren Sie* die aktuelle App-Ansicht, oder markieren Sie den gesamten App-Prozess.</span><span class="sxs-lookup"><span data-stu-id="21565-256">To do that, *tag* the current app view or tag the entire app process.</span></span>

<span data-ttu-id="21565-257">Wenn Sie die Ansicht oder den Prozess markieren, setzt Windows die Richtlinie durch.</span><span class="sxs-lookup"><span data-stu-id="21565-257">When you tag the view or the process, Windows enforces policy on it.</span></span> <span data-ttu-id="21565-258">Dadurch werden Datenlecks verhindert, die aus Aktionen, die Ihre App nicht steuert, entstehen.</span><span class="sxs-lookup"><span data-stu-id="21565-258">This helps prevent data leaks that result from actions that your app doesn't control.</span></span> <span data-ttu-id="21565-259">Beispielsweise auf einem Computer könnten ein Benutzer mit STRG+V Unternehmensinformationen aus einer Ansicht kopieren und diese Informationen in einer anderen App einsetzen.</span><span class="sxs-lookup"><span data-stu-id="21565-259">For example, on a computer, a user could use CTRL-V to copy enterprise information from a view and then paste that information to another app.</span></span> <span data-ttu-id="21565-260">Windows schützt davor.</span><span class="sxs-lookup"><span data-stu-id="21565-260">Windows protects against that.</span></span> <span data-ttu-id="21565-261">Windows hilft auch, die Freigabe-Verträge durchzusetzen.</span><span class="sxs-lookup"><span data-stu-id="21565-261">Windows also helps to enforce share contracts.</span></span>

**<span data-ttu-id="21565-262">Markieren der aktuellen App-Ansicht</span><span class="sxs-lookup"><span data-stu-id="21565-262">Tag the current app view</span></span>**

<span data-ttu-id="21565-263">Vorgehensweise, wenn Ihre App mehrere Ansichten hat, in denen einige Ansichten Unternehmensdaten und einige persönliche Daten nutzen.</span><span class="sxs-lookup"><span data-stu-id="21565-263">Do this if your app has multiple views where some views consume enterprise data and some consume personal data.</span></span>

```csharp

// tag as enterprise data. "identity" the string that contains the enterprise ID.
// You'd get that from a file, network endpoint, or clipboard data package.
ProtectionPolicyManager.GetForCurrentView().Identity = identity;

// tag as personal data.
ProtectionPolicyManager.GetForCurrentView().Identity = String.Empty;
```

> **<span data-ttu-id="21565-264">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-264">APIs</span></span>** <br>
[<span data-ttu-id="21565-265">ProtectionPolicyManager.GetForCurrentView</span><span class="sxs-lookup"><span data-stu-id="21565-265">ProtectionPolicyManager.GetForCurrentView</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.getforcurrentview.aspx)<br>
[<span data-ttu-id="21565-266">ProtectionPolicyManager.Identity</span><span class="sxs-lookup"><span data-stu-id="21565-266">ProtectionPolicyManager.Identity</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.aspx)

**<span data-ttu-id="21565-267">Markieren des Prozesses</span><span class="sxs-lookup"><span data-stu-id="21565-267">Tag the process</span></span>**

<span data-ttu-id="21565-268">Vorgehensweise, wenn alle Ansichten in der App mit nur einem Typ von Daten (persönlich oder Unternehmen) verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="21565-268">Do this if all views in your app will work with only one type of data (personal or enterprise).</span></span>

<span data-ttu-id="21565-269">Dadurch müssen Sie nicht unabhängig voneinander markierte Ansichten verwalten.</span><span class="sxs-lookup"><span data-stu-id="21565-269">This prevents you from having to manage independently tagged views.</span></span>

```csharp


// tag as enterprise data. "identity" the string that contains the enterprise ID.
// You'd get that from a file, network endpoint, or clipboard data package.
bool result =
            ProtectionPolicyManager.TryApplyProcessUIPolicy(identity);

// tag as personal data.
ProtectionPolicyManager.ClearProcessUIPolicy();
```

> **<span data-ttu-id="21565-270">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-270">APIs</span></span>** <br>
[<span data-ttu-id="21565-271">ProtectionPolicyManager.TryApplyProcessUIPolicy</span><span class="sxs-lookup"><span data-stu-id="21565-271">ProtectionPolicyManager.TryApplyProcessUIPolicy</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.tryapplyprocessuipolicy.aspx)

<a id="protect-file" />

### <a name="protect-data-to-a-file"></a><span data-ttu-id="21565-272">Daten in einer Datei schützen</span><span class="sxs-lookup"><span data-stu-id="21565-272">Protect data to a file</span></span>

<span data-ttu-id="21565-273">Erstellen Sie eine geschützte Datei, und schreiben Sie dann hinein.</span><span class="sxs-lookup"><span data-stu-id="21565-273">Create a protected file and then write to it.</span></span>

**<span data-ttu-id="21565-274">Schritt 1: Ermitteln Sie, ob Ihre App eine Unternehmensdatei erstellen kann</span><span class="sxs-lookup"><span data-stu-id="21565-274">Step 1: Determine if your app can create an enterprise file</span></span>**

<span data-ttu-id="21565-275">Ihre App kann eine Unternehmensdatei erstellen, wenn der Identitätsstring durch die Richtlinie verwaltet wird und Ihre App sich auf der Liste der zulässigen Apps von dieser Richtlinie befindet.</span><span class="sxs-lookup"><span data-stu-id="21565-275">Your app can create an enterprise file if the identity string is managed by policy and your app is on the Allowed list of that policy.</span></span>

```csharp
  if (!ProtectionPolicyManager.IsIdentityManaged(identity)) return false;
```

> **<span data-ttu-id="21565-276">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-276">APIs</span></span>** <br>
[<span data-ttu-id="21565-277">ProtectionPolicyManager.IsIdentityManaged</span><span class="sxs-lookup"><span data-stu-id="21565-277">ProtectionPolicyManager.IsIdentityManaged</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.isidentitymanaged.aspx)


**<span data-ttu-id="21565-278">Schritt 2: Erstellen Sie die Datei, und schützen Sie die Identität</span><span class="sxs-lookup"><span data-stu-id="21565-278">Step 2: Create the file and protect it to the identity</span></span>**

```csharp
StorageFolder storageFolder = ApplicationData.Current.LocalFolder;
StorageFile storageFile = await storageFolder.CreateFileAsync("sample.txt",
    CreationCollisionOption.ReplaceExisting);

FileProtectionInfo fileProtectionInfo =
    await FileProtectionManager.ProtectAsync(storageFile, identity);
```

> **<span data-ttu-id="21565-279">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-279">APIs</span></span>** <br>
[<span data-ttu-id="21565-280">FileProtectionManager.ProtectAsync</span><span class="sxs-lookup"><span data-stu-id="21565-280">FileProtectionManager.ProtectAsync</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.fileprotectionmanager.protectasync.aspx)

**<span data-ttu-id="21565-281">Schritt 3: Schreiben Sie die Datenströme oder Puffer in die Datei</span><span class="sxs-lookup"><span data-stu-id="21565-281">Step 3: Write that stream or buffer to the file</span></span>**

*<span data-ttu-id="21565-282">Schreiben Sie einen Datenstrom</span><span class="sxs-lookup"><span data-stu-id="21565-282">Write a stream</span></span>*

```csharp
    if (fileProtectionInfo.Status == FileProtectionStatus.Protected)
    {
        var stream = await storageFile.OpenAsync(FileAccessMode.ReadWrite);

        using (var outputStream = stream.GetOutputStreamAt(0))
        {
            using (var dataWriter = new DataWriter(outputStream))
            {
                dataWriter.WriteString(enterpriseData);
            }
        }

    }
```

*<span data-ttu-id="21565-283">Schreiben eines Puffers</span><span class="sxs-lookup"><span data-stu-id="21565-283">Write a buffer</span></span>*

```csharp
     if (fileProtectionInfo.Status == FileProtectionStatus.Protected)
     {
         var buffer = Windows.Security.Cryptography.CryptographicBuffer.ConvertStringToBinary(
             enterpriseData, Windows.Security.Cryptography.BinaryStringEncoding.Utf8);

         await FileIO.WriteBufferAsync(storageFile, buffer);

      }
```

> **<span data-ttu-id="21565-284">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-284">APIs</span></span>** <br>
[<span data-ttu-id="21565-285">FileProtectionInfo</span><span class="sxs-lookup"><span data-stu-id="21565-285">FileProtectionInfo</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.fileprotectioninfo.aspx)<br>
[<span data-ttu-id="21565-286">FileProtectionStatus</span><span class="sxs-lookup"><span data-stu-id="21565-286">FileProtectionStatus</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.fileprotectionstatus.aspx)<br>

<a id="protect-background" />

### <a name="protect-data-to-a-file-as-a-background-process"></a><span data-ttu-id="21565-287">Schützen von Daten in einer Datei als Hintergrundprozess</span><span class="sxs-lookup"><span data-stu-id="21565-287">Protect data to a file as a background process</span></span>

<span data-ttu-id="21565-288">Während der Bildschirm des Geräts gesperrt ist, kann dieser Code ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="21565-288">This code can run while the screen of the device is locked.</span></span> <span data-ttu-id="21565-289">Wenn der Administrator eine sichere "Schutz von Daten bei Sperre" (Data Protection Under Lock, DPL) Richtlinie konfiguriert, entfernt Windows die Verschlüsselungsschlüssel, die erforderlich sind, um Zugriff auf geschützte Ressourcen aus dem Arbeitsspeicher des Geräts zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="21565-289">If the administrator configured a secure "Data protection under lock" (DPL) policy, Windows removes the encryption keys required to access protected resources from device memory.</span></span> <span data-ttu-id="21565-290">Dies beugt Datenverlusten vor, wenn das Gerät verloren geht.</span><span class="sxs-lookup"><span data-stu-id="21565-290">This prevents data leaks if the device is lost.</span></span> <span data-ttu-id="21565-291">Das gleiche Feature entfernt auch Schlüssel, die mit geschützten Dateien heruntergeladen wurden, wenn deren Handles geschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="21565-291">This same feature also removes keys associated with protected files when their handles are closed.</span></span>

<span data-ttu-id="21565-292">Sie müssen einen Ansatz verwenden, der das Datei-Handle geöffnet hält, wenn Sie eine Datei erstellen.</span><span class="sxs-lookup"><span data-stu-id="21565-292">You'll have to use an approach that keeps the file handle open when you create a file.</span></span>  

**<span data-ttu-id="21565-293">Schritt 1: Ermitteln Sie, ob Sie eine Unternehmensdatei erstellen können</span><span class="sxs-lookup"><span data-stu-id="21565-293">Step 1: Determine if you can create an enterprise file</span></span>**

<span data-ttu-id="21565-294">Sie können eine Unternehmensdatei erstellen, wenn die Identität, die Sie verwenden, durch die Richtlinie verwaltet wird und Ihre App sich auf der Liste der zulässigen Apps dieser Richtlinie befindet.</span><span class="sxs-lookup"><span data-stu-id="21565-294">You can create an enterprise file if the identity that you're using is managed by policy and your app is on the allowed list of that policy.</span></span>

```csharp
if (!ProtectionPolicyManager.IsIdentityManaged(identity)) return false;
```

> **<span data-ttu-id="21565-295">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-295">APIs</span></span>** <br>
[<span data-ttu-id="21565-296">ProtectionPolicyManager.IsIdentityManaged</span><span class="sxs-lookup"><span data-stu-id="21565-296">ProtectionPolicyManager.IsIdentityManaged</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.isidentitymanaged.aspx)

**<span data-ttu-id="21565-297">Schritt 2: Erstellen Sie eine Datei, und schützen Sie die Identität</span><span class="sxs-lookup"><span data-stu-id="21565-297">Step 2: Create a file and protect it to the identity</span></span>**

<span data-ttu-id="21565-298">Der [**FileProtectionManager.CreateProtectedAndOpenAsync**](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.fileprotectionmanager.createprotectedandopenasync.aspx) erstellt eine geschützte Datei und hält das Datei-Handle geöffnet, während Sie einen Schreibvorgang ausführen.</span><span class="sxs-lookup"><span data-stu-id="21565-298">The [**FileProtectionManager.CreateProtectedAndOpenAsync**](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.fileprotectionmanager.createprotectedandopenasync.aspx) creates a protected file and keeps the file handle open while you write to it.</span></span>

```csharp
StorageFolder storageFolder = ApplicationData.Current.LocalFolder;

ProtectedFileCreateResult protectedFileCreateResult =
    await FileProtectionManager.CreateProtectedAndOpenAsync(storageFolder,
        "sample.txt", identity, CreationCollisionOption.ReplaceExisting);
```

> **<span data-ttu-id="21565-299">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-299">APIs</span></span>** <br>
[<span data-ttu-id="21565-300">FileProtectionManager.CreateProtectedAndOpenAsync</span><span class="sxs-lookup"><span data-stu-id="21565-300">FileProtectionManager.CreateProtectedAndOpenAsync</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.fileprotectionmanager.createprotectedandopenasync.aspx)

**<span data-ttu-id="21565-301">Schritt 3: Schreiben Sie Datenströme oder Puffer in die Datei</span><span class="sxs-lookup"><span data-stu-id="21565-301">Step 3: Write a stream or buffer to the file</span></span>**

<span data-ttu-id="21565-302">Dieses Beispiel schreibt einen Datenstrom in eine Datei.</span><span class="sxs-lookup"><span data-stu-id="21565-302">This example writes a stream to a file.</span></span>

```csharp
if (protectedFileCreateResult.ProtectionInfo.Status == FileProtectionStatus.Protected)
{
    IOutputStream outputStream =
        protectedFileCreateResult.Stream.GetOutputStreamAt(0);

    using (DataWriter writer = new DataWriter(outputStream))
    {
        writer.WriteString(enterpriseData);
        await writer.StoreAsync();
        await writer.FlushAsync();
    }

    outputStream.Dispose();
}
else if (protectedFileCreateResult.ProtectionInfo.Status == FileProtectionStatus.AccessSuspended)
{
    // Perform any special processing for the access suspended case.
}

```

> **<span data-ttu-id="21565-303">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-303">APIs</span></span>** <br>
[<span data-ttu-id="21565-304">ProtectedFileCreateResult.ProtectionInfo</span><span class="sxs-lookup"><span data-stu-id="21565-304">ProtectedFileCreateResult.ProtectionInfo</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectedfilecreateresult.protectioninfo.aspx)<br>
[<span data-ttu-id="21565-305">FileProtectionStatus</span><span class="sxs-lookup"><span data-stu-id="21565-305">FileProtectionStatus</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.fileprotectionstatus.aspx)<br>
[<span data-ttu-id="21565-306">ProtectedFileCreateResult.Datenstrom</span><span class="sxs-lookup"><span data-stu-id="21565-306">ProtectedFileCreateResult.Stream</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectedfilecreateresult.stream.aspx)<br>

<a id="protect-part-file" />

### <a name="protect-part-of-a-file"></a><span data-ttu-id="21565-307">Einen Teil einer Datei schützen</span><span class="sxs-lookup"><span data-stu-id="21565-307">Protect part of a file</span></span>

<span data-ttu-id="21565-308">In den meisten Fällen ist es sauberer, Unternehmens- und persönliche Daten separat zu speichern, jedoch können Sie sie in derselben Datei speichern, wenn Sie möchten.</span><span class="sxs-lookup"><span data-stu-id="21565-308">In most cases, it's cleaner to store enterprise and personal data separately but you can store them to the same file if you want.</span></span> <span data-ttu-id="21565-309">Beispielsweise kann Microsoft Outlook Unternehmens-E-Mails zusammen mit den persönlichen E-Mails in einer einzigen Archivdatei speichern.</span><span class="sxs-lookup"><span data-stu-id="21565-309">For example, Microsoft Outlook can store enterprise mails alongside of personal mails in a single archive file.</span></span>

<span data-ttu-id="21565-310">Verschlüsseln Sie die Unternehmensdaten, jedoch nicht die gesamte Datei.</span><span class="sxs-lookup"><span data-stu-id="21565-310">Encrypt the enterprise data but not the entire file.</span></span> <span data-ttu-id="21565-311">Auf diese Weise können Benutzer weiterhin mit der Datei arbeiten, selbst wenn sie von MDM aufgehoben werden oder ihre Unternehmensdatenzugriffsrechte widerrufen werden.</span><span class="sxs-lookup"><span data-stu-id="21565-311">That way, users can continue using that file even if they un-enroll from MDM or their enterprise data access rights are revoked.</span></span> <span data-ttu-id="21565-312">Darüber hinaus sollte Ihre App den Überblick behalten, welche Daten sie verschlüsselt, damit bekannt ist, welche Daten zu schützen sind, wenn sie die Datei zurück in den Arbeitsspeicher liest.</span><span class="sxs-lookup"><span data-stu-id="21565-312">Also, your app should keep track of what data it encrypts so that it knows what data to protect when it reads the file back into memory.</span></span>

**<span data-ttu-id="21565-313">Schritt 1: Hinzufügen von Unternehmensdaten zu einem verschlüsselten Datenstrom oder Puffer</span><span class="sxs-lookup"><span data-stu-id="21565-313">Step 1: Add enterprise data to an encrypted stream or buffer</span></span>**

```csharp
string enterpriseDataString = "<employees><employee><name>Bill</name><social>xxx-xxx-xxxx</social></employee></employees>";

var enterpriseData= Windows.Security.Cryptography.CryptographicBuffer.ConvertStringToBinary(
        enterpriseDataString, Windows.Security.Cryptography.BinaryStringEncoding.Utf8);

BufferProtectUnprotectResult result =
   await DataProtectionManager.ProtectAsync(enterpriseData, identity);

enterpriseData= result.Buffer;
```

> **<span data-ttu-id="21565-314">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-314">APIs</span></span>** <br>
[<span data-ttu-id="21565-315">DataProtectionManager.ProtectAsync</span><span class="sxs-lookup"><span data-stu-id="21565-315">DataProtectionManager.ProtectAsync</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.dataprotectionmanager.protectasync.aspx)<br>
[<span data-ttu-id="21565-316">BufferProtectUnprotectResult.Puffer</span><span class="sxs-lookup"><span data-stu-id="21565-316">BufferProtectUnprotectResult.buffer</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.bufferprotectunprotectresult.buffer.aspx)


**<span data-ttu-id="21565-317">Schritt 2: Hinzufügen von persönlichen Daten zu einem unverschlüsselten Datenstrom oder Puffer</span><span class="sxs-lookup"><span data-stu-id="21565-317">Step 2: Add personal data to an unencrypted stream or buffer</span></span>**

```csharp
string personalDataString = "<recipies><recipe><name>BillsCupCakes</name><cooktime>30</cooktime></recipe></recipies>";

var personalData = Windows.Security.Cryptography.CryptographicBuffer.ConvertStringToBinary(
    personalDataString, Windows.Security.Cryptography.BinaryStringEncoding.Utf8);
```

**<span data-ttu-id="21565-318">Schritt 3: Schreiben Sie Datenströme oder Puffer in eine Datei</span><span class="sxs-lookup"><span data-stu-id="21565-318">Step 3: Write both streams or buffers to a file</span></span>**

```csharp
StorageFolder storageFolder = ApplicationData.Current.LocalFolder;

StorageFile storageFile = await storageFolder.CreateFileAsync("data.xml",
    CreationCollisionOption.ReplaceExisting);

 // Write both buffers to the file and save the file.

var stream = await storageFile.OpenAsync(FileAccessMode.ReadWrite);

using (var outputStream = stream.GetOutputStreamAt(0))
{
    using (var dataWriter = new DataWriter(outputStream))
    {
        dataWriter.WriteBuffer(enterpriseData);
        dataWriter.WriteBuffer(personalData);

        await dataWriter.StoreAsync();
        await outputStream.FlushAsync();
    }
}
```

**<span data-ttu-id="21565-319">Schritt 4: Behalten Sie den Überblick über den Speicherort Ihrer Unternehmensdaten in der Datei</span><span class="sxs-lookup"><span data-stu-id="21565-319">Step 4: Keep track of the location of your enterprise data in the file</span></span>**

<span data-ttu-id="21565-320">Ihre App ist dafür verantwortlich, die zum Unternehmen gehörigen Daten in der Datei im Blick zu behalten.</span><span class="sxs-lookup"><span data-stu-id="21565-320">It's the responsibility of your app to keep track of the data in that file that is enterprise owned.</span></span>

<span data-ttu-id="21565-321">Sie können diese Informationen in der Datei-Eigenschaft, einer Datenbank oder in einem Kopfzeilentext in der Datei speichern.</span><span class="sxs-lookup"><span data-stu-id="21565-321">You can store that information in a property associated with the file, in a database, or in some header text in the file.</span></span>

<span data-ttu-id="21565-322">Dieses Beispiel sichert die Informationen in eine separate XML-Datei.</span><span class="sxs-lookup"><span data-stu-id="21565-322">This example, saves that information to a separate XML file.</span></span>

```csharp
StorageFile metaDataFile = await storageFolder.CreateFileAsync("metadata.xml",
   CreationCollisionOption.ReplaceExisting);

await Windows.Storage.FileIO.WriteTextAsync
    (metaDataFile, "<EnterpriseDataMarker start='0' end='" + enterpriseData.Length.ToString() +
    "'></EnterpriseDataMarker>");
```
<a id="read-protected" />

### <a name="read-the-protected-part-of-a-file"></a><span data-ttu-id="21565-323">Lesen Sie den geschützten Teil einer Datei</span><span class="sxs-lookup"><span data-stu-id="21565-323">Read the protected part of a file</span></span>

<span data-ttu-id="21565-324">Hier wird beschrieben, wie die Unternehmensdaten aus der Datei gelesen werden würde.</span><span class="sxs-lookup"><span data-stu-id="21565-324">Here's how you'd read the enterprise data out of that file.</span></span>

**<span data-ttu-id="21565-325">Schritt 1: Abrufen der Position Ihrer Unternehmensdaten in der Datei</span><span class="sxs-lookup"><span data-stu-id="21565-325">Step 1: Get the position of your enterprise data in the file</span></span>**

```csharp
Windows.Storage.StorageFolder storageFolder =
    Windows.Storage.ApplicationData.Current.LocalFolder;

 Windows.Storage.StorageFile metaDataFile =
   await storageFolder.GetFileAsync("metadata.xml");

string metaData = await Windows.Storage.FileIO.ReadTextAsync(metaDataFile);

XmlDocument doc = new XmlDocument();

doc.LoadXml(metaData);

uint startPosition =
    Convert.ToUInt16((doc.FirstChild.Attributes.GetNamedItem("start")).InnerText);

uint endPosition =
    Convert.ToUInt16((doc.FirstChild.Attributes.GetNamedItem("end")).InnerText);
```

**<span data-ttu-id="21565-326">Schritt 2: Öffnen Sie die Datei, und stellen Sie sicher, dass sie nicht geschützt ist</span><span class="sxs-lookup"><span data-stu-id="21565-326">Step 2: Open the data file and make sure that it's not protected</span></span>**

```csharp
Windows.Storage.StorageFile dataFile =
    await storageFolder.GetFileAsync("data.xml");

FileProtectionInfo protectionInfo =
    await FileProtectionManager.GetProtectionInfoAsync(dataFile);

if (protectionInfo.Status == FileProtectionStatus.Protected)
    return false;
```

> **<span data-ttu-id="21565-327">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-327">APIs</span></span>** <br>
[<span data-ttu-id="21565-328">FileProtectionManager.GetProtectionInfoAsync</span><span class="sxs-lookup"><span data-stu-id="21565-328">FileProtectionManager.GetProtectionInfoAsync</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.fileprotectionmanager.getprotectioninfoasync.aspx)<br>
[<span data-ttu-id="21565-329">FileProtectionInfo</span><span class="sxs-lookup"><span data-stu-id="21565-329">FileProtectionInfo</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.fileprotectioninfo.aspx)<br>
[<span data-ttu-id="21565-330">FileProtectionStatus</span><span class="sxs-lookup"><span data-stu-id="21565-330">FileProtectionStatus</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.fileprotectionstatus.aspx)<br>

**<span data-ttu-id="21565-331">Schritt 3: Lesen Sie in den Unternehmensdaten aus der Datei.</span><span class="sxs-lookup"><span data-stu-id="21565-331">Step 3: Read the enterprise data from the file</span></span>**

```csharp
var stream = await dataFile.OpenAsync(Windows.Storage.FileAccessMode.ReadWrite);

stream.Seek(startPosition);

Windows.Storage.Streams.Buffer tempBuffer = new Windows.Storage.Streams.Buffer(50000);

IBuffer enterpriseData = await stream.ReadAsync(tempBuffer, endPosition, InputStreamOptions.None);
```

**<span data-ttu-id="21565-332">Schritt 4: Entschlüsseln Sie den Puffer, der Unternehmensdaten enthält</span><span class="sxs-lookup"><span data-stu-id="21565-332">Step 4: Decrypt the buffer that contains enterprise data</span></span>**

```csharp
DataProtectionInfo dataProtectionInfo =
   await DataProtectionManager.GetProtectionInfoAsync(enterpriseData);

if (dataProtectionInfo.Status == DataProtectionStatus.Protected)
{
    BufferProtectUnprotectResult result = await DataProtectionManager.UnprotectAsync(enterpriseData);
    enterpriseData = result.Buffer;
}
else if (dataProtectionInfo.Status == DataProtectionStatus.Revoked)
{
    // Code goes here to handle this situation. Perhaps, show UI
    // saying that the user's data has been revoked.
}

```

> **<span data-ttu-id="21565-333">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-333">APIs</span></span>** <br>
[<span data-ttu-id="21565-334">DataProtectionInfo</span><span class="sxs-lookup"><span data-stu-id="21565-334">DataProtectionInfo</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.dataprotectioninfo.aspx)<br>
[<span data-ttu-id="21565-335">DataProtectionManager.GetProtectionInfoAsync</span><span class="sxs-lookup"><span data-stu-id="21565-335">DataProtectionManager.GetProtectionInfoAsync</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.dataprotectionmanager.getstreamprotectioninfoasync.aspx)<br>

<a id="protect-folder" />

### <a name="protect-data-to-a-folder"></a><span data-ttu-id="21565-336">Schützen Sie Daten in einem Ordner</span><span class="sxs-lookup"><span data-stu-id="21565-336">Protect data to a folder</span></span>

<span data-ttu-id="21565-337">Sie können einen Ordner erstellen und diesen schützen.</span><span class="sxs-lookup"><span data-stu-id="21565-337">You can create a folder and protect it.</span></span> <span data-ttu-id="21565-338">Auf diese Weise sind alle Elemente, die Sie zu diesem Ordner hinzufügen, automatisch geschützt.</span><span class="sxs-lookup"><span data-stu-id="21565-338">That way any items that you add to that folder are automatically protected.</span></span>

```csharp
private async Task<bool> CreateANewFolderAndProtectItAsync(string folderName, string identity)
{
    if (!ProtectionPolicyManager.IsIdentityManaged(identity)) return false;

    StorageFolder storageFolder = ApplicationData.Current.LocalFolder;
    StorageFolder newStorageFolder =
        await storageFolder.CreateFolderAsync(folderName);

    FileProtectionInfo fileProtectionInfo =
        await FileProtectionManager.ProtectAsync(newStorageFolder, identity);

    if (fileProtectionInfo.Status != FileProtectionStatus.Protected)
    {
        // Protection failed.
        return false;
    }
    return true;
}
```

<span data-ttu-id="21565-339">Stellen Sie sicher, dass der Ordner leer ist, bevor Sie ihn schützen.</span><span class="sxs-lookup"><span data-stu-id="21565-339">Make sure that the folder is empty before you protect it.</span></span> <span data-ttu-id="21565-340">Es ist nicht möglich, einen Ordner zu schützen, der bereits Elemente enthält.</span><span class="sxs-lookup"><span data-stu-id="21565-340">You can't protect a folder that already contains items.</span></span>

> **<span data-ttu-id="21565-341">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-341">APIs</span></span>** <br>
[<span data-ttu-id="21565-342">ProtectionPolicyManager.IsIdentityManaged</span><span class="sxs-lookup"><span data-stu-id="21565-342">ProtectionPolicyManager.IsIdentityManaged</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.isidentitymanaged.aspx)<br>
[<span data-ttu-id="21565-343">FileProtectionManager.ProtectAsync</span><span class="sxs-lookup"><span data-stu-id="21565-343">FileProtectionManager.ProtectAsync</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.fileprotectionmanager.protectasync.aspx)<br>
[<span data-ttu-id="21565-344">FileProtectionInfo.Identity</span><span class="sxs-lookup"><span data-stu-id="21565-344">FileProtectionInfo.Identity</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.fileprotectioninfo.identity.aspx)<br>
[<span data-ttu-id="21565-345">FileProtectionInfo.Status</span><span class="sxs-lookup"><span data-stu-id="21565-345">FileProtectionInfo.Status</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.fileprotectioninfo.status.aspx)

<a id="protect-network" />

### <a name="protect-data-to-a-network-end-point"></a><span data-ttu-id="21565-346">Schützen Sie Daten in einem Netzwerkendpunkt</span><span class="sxs-lookup"><span data-stu-id="21565-346">Protect data to a network end point</span></span>

<span data-ttu-id="21565-347">Erstellen Sie einen geschützten Threadkontext zum Senden von Daten an einen Unternehmensendpunkt.</span><span class="sxs-lookup"><span data-stu-id="21565-347">Create a protected thread context to send that data to an enterprise endpoint.</span></span>  

**<span data-ttu-id="21565-348">Schritt 1: Abrufen der Identität des Netzwerkendpunktes</span><span class="sxs-lookup"><span data-stu-id="21565-348">Step 1: Get the identity of the network endpoint</span></span>**

```csharp
Windows.Networking.HostName hostName =
    new Windows.Networking.HostName(resourceURI.Host);

string identity = await ProtectionPolicyManager.
    GetPrimaryManagedIdentityForNetworkEndpointAsync(hostName);
```

> **<span data-ttu-id="21565-349">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-349">APIs</span></span>** <br>
[<span data-ttu-id="21565-350">ProtectionPolicyManager.GetPrimaryManagedIdentityForNetworkEndpointAsync</span><span class="sxs-lookup"><span data-stu-id="21565-350">ProtectionPolicyManager.GetPrimaryManagedIdentityForNetworkEndpointAsync</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.getprimarymanagedidentityfornetworkendpointasync.aspx)

**<span data-ttu-id="21565-351">Schritt 2: Erstellen eines geschützten Threadkontexts und Senden von Daten an den Netzwerkendpunkt</span><span class="sxs-lookup"><span data-stu-id="21565-351">Step 2: Create a protected thread context and send data to the network endpoint</span></span>**

```csharp
HttpClient client = null;

if (!string.IsNullOrEmpty(m_EnterpriseId))
{
    ProtectionPolicyManager.GetForCurrentView().Identity = identity;

    using (ThreadNetworkContext threadNetworkContext =
            ProtectionPolicyManager.CreateCurrentThreadNetworkContext(identity))
    {
        client = new HttpClient();
        HttpRequestMessage message = new HttpRequestMessage(HttpMethod.Put, resourceURI);
        message.Content = new HttpStreamContent(dataToWrite);

        HttpResponseMessage response = await client.SendRequestAsync(message);

        if (response.StatusCode == HttpStatusCode.Ok)
            return true;
        else
            return false;
    }
}
else
{
    return false;
}
```

> **<span data-ttu-id="21565-352">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-352">APIs</span></span>** <br>
[<span data-ttu-id="21565-353">ProtectionPolicyManager.GetForCurrentView</span><span class="sxs-lookup"><span data-stu-id="21565-353">ProtectionPolicyManager.GetForCurrentView</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.getforcurrentview.aspx)<br>
[<span data-ttu-id="21565-354">ProtectionPolicyManager.Identity</span><span class="sxs-lookup"><span data-stu-id="21565-354">ProtectionPolicyManager.Identity</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.aspx)<br>
[<span data-ttu-id="21565-355">ProtectionPolicyManager.CreateCurrentThreadNetworkContext</span><span class="sxs-lookup"><span data-stu-id="21565-355">ProtectionPolicyManager.CreateCurrentThreadNetworkContext</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.createcurrentthreadnetworkcontext.aspx)

<a id="protect-share" />

### <a name="protect-data-that-your-app-shares-through-a-share-contract"></a><span data-ttu-id="21565-356">Schützen Sie Daten, die Ihre App über einen Freigabe-Vertrag teilt</span><span class="sxs-lookup"><span data-stu-id="21565-356">Protect data that your app shares through a share contract</span></span>

<span data-ttu-id="21565-357">Wenn Benutzer Inhalt aus Ihrer App freigeben sollen, müssen Sie einen Freigabe-Vertrag implementieren und das Ereignis [**DataTransferManager.DataRequested**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datatransfermanager.datarequested) behandeln.</span><span class="sxs-lookup"><span data-stu-id="21565-357">If you want users to share content from your app, you'll have to implement a share contract and handle the [**DataTransferManager.DataRequested**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.datatransfer.datatransfermanager.datarequested) event.</span></span>

<span data-ttu-id="21565-358">Legen Sie in Ihrem Ereignishandler den Unternehmensidentitätskontext im Datenpaket fest.</span><span class="sxs-lookup"><span data-stu-id="21565-358">In your event handler, set the enterprise identity context in the data package.</span></span>

```csharp
private void OnShareSourceOperation(object sender, RoutedEventArgs e)
{
    // Register the current page as a share source (or you could do this earlier in your app).
    DataTransferManager.GetForCurrentView().DataRequested += OnDataRequested;
    DataTransferManager.ShowShareUI();
}

private void OnDataRequested(DataTransferManager sender, DataRequestedEventArgs args)
{
    if (!string.IsNullOrEmpty(this.shareSourceContent))
    {
        var protectionPolicyManager = ProtectionPolicyManager.GetForCurrentView();
        DataPackage requestData = args.Request.Data;
        requestData.Properties.Title = this.shareSourceTitle;
        requestData.Properties.EnterpriseId = protectionPolicyManager.Identity;
        requestData.SetText(this.shareSourceContent);
    }
}
```

> **<span data-ttu-id="21565-359">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-359">APIs</span></span>** <br>
[<span data-ttu-id="21565-360">ProtectionPolicyManager.GetForCurrentView</span><span class="sxs-lookup"><span data-stu-id="21565-360">ProtectionPolicyManager.GetForCurrentView</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.getforcurrentview.aspx)<br>
[<span data-ttu-id="21565-361">ProtectionPolicyManager.Identity</span><span class="sxs-lookup"><span data-stu-id="21565-361">ProtectionPolicyManager.Identity</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.aspx)

<a id="protect-other-location" />

### <a name="protect-files-that-you-copy-to-another-location"></a><span data-ttu-id="21565-362">Schützen von Dateien, die Sie an einen anderen Speicherort kopieren</span><span class="sxs-lookup"><span data-stu-id="21565-362">Protect files that you copy to another location</span></span>

```csharp
private async void CopyProtectionFromOneFileToAnother
    (StorageFile sourceStorageFile, StorageFile targetStorageFile)
{
    bool copyResult = await
        FileProtectionManager.CopyProtectionAsync(sourceStorageFile, targetStorageFile);

    if (!copyResult)
    {
        // Copying failed. To diagnose, you could check the file's status.
        // (call FileProtectionManager.GetProtectionInfoAsync and
        // check FileProtectionInfo.Status).
    }
}
```

> **<span data-ttu-id="21565-363">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-363">APIs</span></span>** <br>
[<span data-ttu-id="21565-364">FileProtectionManager.CopyProtectionAsync</span><span class="sxs-lookup"><span data-stu-id="21565-364">FileProtectionManager.CopyProtectionAsync</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.fileprotectionmanager.copyprotectionasync.aspx)<br>

<a id="protect-locked" />

### <a name="protect-enterprise-data-when-the-screen-of-the-device-is-locked"></a><span data-ttu-id="21565-365">Unternehmensdaten schützen, wenn der Bildschirm des Geräts gesperrt ist</span><span class="sxs-lookup"><span data-stu-id="21565-365">Protect enterprise data when the screen of the device is locked</span></span>

<span data-ttu-id="21565-366">Entfernen Sie alle sensible Daten im Arbeitsspeicher, wenn das Gerät gesperrt wird.</span><span class="sxs-lookup"><span data-stu-id="21565-366">Remove all sensitive data in memory when the device is locked.</span></span> <span data-ttu-id="21565-367">Wenn der Benutzer das Gerät entsperrt, kann Ihre App diese Daten wieder sicher hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="21565-367">When the user unlocks the device, your app can safely add that data back.</span></span>

<span data-ttu-id="21565-368">Behandeln des [**ProtectionPolicyManager.ProtectedAccessSuspending**](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.protectedaccesssuspending.aspx) Ereignis, damit Ihre App weiß, wann der Bildschirm gesperrt ist.</span><span class="sxs-lookup"><span data-stu-id="21565-368">Handle the [**ProtectionPolicyManager.ProtectedAccessSuspending**](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.protectedaccesssuspending.aspx) event so that your app knows when the screen is locked.</span></span> <span data-ttu-id="21565-369">Dieses Ereignis wird nur ausgelöst, wenn der Administrator einen sicheren Datenschutz bei Sperre in den Richtlinien konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="21565-369">This event is raised only if the administrator configures a secure data protection under lock policy.</span></span> <span data-ttu-id="21565-370">Windows entfernt vorübergehend die Datenschutzschlüssel, welche auf dem Gerät bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="21565-370">Windows temporarily removes the data protection keys that are provisioned on the device.</span></span> <span data-ttu-id="21565-371">Windows entfernt diese Schlüssel, um sicherzustellen, dass es keine nicht autorisierten Zugriffe auf verschlüsselte Daten gibt, wenn das Gerät gesperrt und möglicherweise nicht im Besitz des Besitzers ist.</span><span class="sxs-lookup"><span data-stu-id="21565-371">Windows removes these keys to ensure that there is no unauthorized access to encrypted data while the device is locked and possibly not in possession of its owner.</span></span>  

<span data-ttu-id="21565-372">Behandeln des [**ProtectionPolicyManager.ProtectedAccessResumed**](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.protectedaccessresumed.aspx) Ereignis, damit Ihre App weiß, wann der Bildschirm entsperrt ist.</span><span class="sxs-lookup"><span data-stu-id="21565-372">Handle the [**ProtectionPolicyManager.ProtectedAccessResumed**](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.protectedaccessresumed.aspx) event so that your app knows when the screen is unlocked.</span></span> <span data-ttu-id="21565-373">Dieses Ereignis wird ausgelöst, unabhängig davon, ob der Administrator einen sicheren Datenschutz bei Sperre in den Richtlinien konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="21565-373">This event is raised regardless of whether the administrator configures a secure data protection under lock policy.</span></span>

#### <a name="remove-sensitive-data-in-memory-when-the-screen-is-locked"></a><span data-ttu-id="21565-374">Entfernen Sie sensible Daten im Arbeitsspeicher, wenn der Bildschirm gesperrt wird</span><span class="sxs-lookup"><span data-stu-id="21565-374">Remove sensitive data in memory when the screen is locked</span></span>

<span data-ttu-id="21565-375">Schützen Sie sensible Daten, und schließen Sie alle Datenströme, die Ihre App auf geschützten Dateien geöffnet hat, um sicherzustellen, dass das System keine sensiblen Daten im Speicher zwischenspeichert.</span><span class="sxs-lookup"><span data-stu-id="21565-375">Protect sensitive data, and close any file streams that your app has opened on protected files to help ensure that the system doesn't cache any sensitive data in memory.</span></span>

<span data-ttu-id="21565-376">Dieses Beispiel sichert Inhalte aus einem TextBlock-Steuerelement in einem verschlüsselten Puffer und entfernt die Inhalte von diesem TextBlock-Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="21565-376">This example saves content from a textblock to an encrypted buffer and removes the content from that textblock.</span></span>

```csharp
private async void ProtectionPolicyManager_ProtectedAccessSuspending(object sender, ProtectedAccessSuspendingEventArgs e)
{
    Deferral deferral = e.GetDeferral();

    if (ProtectionPolicyManager.GetForCurrentView().Identity != String.Empty)
    {
        IBuffer documentBodyBuffer = CryptographicBuffer.ConvertStringToBinary
           (documentTextBlock.Text, BinaryStringEncoding.Utf8);

        BufferProtectUnprotectResult result = await DataProtectionManager.ProtectAsync
            (documentBodyBuffer, ProtectionPolicyManager.GetForCurrentView().Identity);

        if (result.ProtectionInfo.Status == DataProtectionStatus.Protected)
        {
            this.protectedDocumentBuffer = result.Buffer;
            documentTextBlock.Text = null;
        }
    }

    // Close any open streams that you are actively working with
    // to make sure that we have no unprotected content in memory.

    // Optionally, code goes here to use e.Deadline to determine whether we have more
    // than 15 seconds left before the suspension deadline. If we do then process any
    // messages queued up for sending while we are still able to access them.

    deferral.Complete();
}
```

> **<span data-ttu-id="21565-377">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-377">APIs</span></span>** <br>
[<span data-ttu-id="21565-378">ProtectionPolicyManager.ProtectedAccessSuspending</span><span class="sxs-lookup"><span data-stu-id="21565-378">ProtectionPolicyManager.ProtectedAccessSuspending</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.protectedaccesssuspending.aspx)<br>
[<span data-ttu-id="21565-379">ProtectionPolicyManager.GetForCurrentView</span><span class="sxs-lookup"><span data-stu-id="21565-379">ProtectionPolicyManager.GetForCurrentView</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.getforcurrentview.aspx)<br>
[<span data-ttu-id="21565-380">ProtectionPolicyManager.Identity</span><span class="sxs-lookup"><span data-stu-id="21565-380">ProtectionPolicyManager.Identity</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.aspx)</br>
[<span data-ttu-id="21565-381">DataProtectionManager.ProtectAsync</span><span class="sxs-lookup"><span data-stu-id="21565-381">DataProtectionManager.ProtectAsync</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.dataprotectionmanager.protectasync.aspx)<br>
[<span data-ttu-id="21565-382">BufferProtectUnprotectResult.Puffer</span><span class="sxs-lookup"><span data-stu-id="21565-382">BufferProtectUnprotectResult.buffer</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.bufferprotectunprotectresult.buffer.aspx)<br>
[<span data-ttu-id="21565-383">ProtectedAccessSuspendingEventArgs.GetDeferral</span><span class="sxs-lookup"><span data-stu-id="21565-383">ProtectedAccessSuspendingEventArgs.GetDeferral</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectedaccesssuspendingeventargs.getdeferral.aspx)<br>
[<span data-ttu-id="21565-384">Deferral.Complete</span><span class="sxs-lookup"><span data-stu-id="21565-384">Deferral.Complete</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.foundation.deferral.complete.aspx)<br>

#### <a name="add-back-sensitive-data-when-the-device-is-unlocked"></a><span data-ttu-id="21565-385">Fügen Sie wieder sensible Daten ein, wenn das Gerät entsperrt wurde</span><span class="sxs-lookup"><span data-stu-id="21565-385">Add back sensitive data when the device is unlocked</span></span>

<span data-ttu-id="21565-386">[**ProtectionPolicyManager.ProtectedAccessResumed**](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.protectedaccessresumed.aspx) wird ausgelöst, wenn das Gerät entsperrt ist und die Schlüssel wieder auf dem Geräts verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="21565-386">[**ProtectionPolicyManager.ProtectedAccessResumed**](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.protectedaccessresumed.aspx) is raised when the device is unlocked and the keys are available on the device again.</span></span>

<span data-ttu-id="21565-387">[**ProtectedAccessResumedEventArgs.Identities**](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectedaccessresumedeventargs.identities.aspx) ist eine leere Collection, wenn der Administrator keinen sicheren Datenschutz bei Sperre in den Richtlinien konfiguriert hat.</span><span class="sxs-lookup"><span data-stu-id="21565-387">[**ProtectedAccessResumedEventArgs.Identities**](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectedaccessresumedeventargs.identities.aspx) is an empty collection if the administrator hasn't configured a secure data protection under lock policy.</span></span>

<span data-ttu-id="21565-388">In diesem Beispiel erfolgt das Gegenteil der Aktionen des vorherigen Beispiels.</span><span class="sxs-lookup"><span data-stu-id="21565-388">This example does the reverse of the previous example.</span></span> <span data-ttu-id="21565-389">Es entschlüsselt den Puffer, fügt Informationen dieses Puffers zum Textfeld hinzu und gibt anschließend den Puffer frei.</span><span class="sxs-lookup"><span data-stu-id="21565-389">It decrypts the buffer, adds information from that buffer back to the textbox and then disposes of the buffer.</span></span>

```csharp
private async void ProtectionPolicyManager_ProtectedAccessResumed(object sender, ProtectedAccessResumedEventArgs e)
{
    if (ProtectionPolicyManager.GetForCurrentView().Identity != String.Empty)
    {
        BufferProtectUnprotectResult result = await DataProtectionManager.UnprotectAsync
            (this.protectedDocumentBuffer);

        if (result.ProtectionInfo.Status == DataProtectionStatus.Unprotected)
        {
            // Restore the unprotected version.
            documentTextBlock.Text = CryptographicBuffer.ConvertBinaryToString
                (BinaryStringEncoding.Utf8, result.Buffer);
            this.protectedDocumentBuffer = null;
        }
    }

}
```

> **<span data-ttu-id="21565-390">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-390">APIs</span></span>** <br>
[<span data-ttu-id="21565-391">ProtectionPolicyManager.ProtectedAccessResumed</span><span class="sxs-lookup"><span data-stu-id="21565-391">ProtectionPolicyManager.ProtectedAccessResumed</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.protectedaccessresumed.aspx)<br>
[<span data-ttu-id="21565-392">ProtectionPolicyManager.GetForCurrentView</span><span class="sxs-lookup"><span data-stu-id="21565-392">ProtectionPolicyManager.GetForCurrentView</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.getforcurrentview.aspx)<br>
[<span data-ttu-id="21565-393">ProtectionPolicyManager.Identity</span><span class="sxs-lookup"><span data-stu-id="21565-393">ProtectionPolicyManager.Identity</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.aspx)</br>
[<span data-ttu-id="21565-394">DataProtectionManager.UnprotectAsync</span><span class="sxs-lookup"><span data-stu-id="21565-394">DataProtectionManager.UnprotectAsync</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.dataprotectionmanager.unprotectasync.aspx)<br>
[<span data-ttu-id="21565-395">PufferProtectUnprotectResult.Status</span><span class="sxs-lookup"><span data-stu-id="21565-395">BufferProtectUnprotectResult.Status</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.bufferprotectunprotectresult.aspx)<br>

## <a name="handle-enterprise-data-when-protected-content-is-revoked"></a><span data-ttu-id="21565-396">Behandeln Sie Unternehmensdaten, wenn der geschützte Inhalt verweigert wird</span><span class="sxs-lookup"><span data-stu-id="21565-396">Handle enterprise data when protected content is revoked</span></span>

<span data-ttu-id="21565-397">Wenn Ihre App benachrichtigt werden soll, wenn ein Gerät von MDM aufgehoben ist oder wenn der Richtlinien-Administrator explizit den Zugriff auf Unternehmensdaten widerruft, behandeln Sie das [**ProtectionPolicyManager_ProtectedContentRevoked**](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.protectedcontentrevoked.aspx)-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="21565-397">If you want your app to be notified when the device is un-enrolled from MDM or when the policy administrator explicitly revokes access to enterprise data, handle the [**ProtectionPolicyManager_ProtectedContentRevoked**](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.protectedcontentrevoked.aspx) event.</span></span>

<span data-ttu-id="21565-398">In diesem Beispiel wird bestimmt, ob die Daten in einem Unternehmenspostfach für eine E-Mail-App gesperrt wurden.</span><span class="sxs-lookup"><span data-stu-id="21565-398">This example determines if the data in an enterprise mailbox for an email app has been revoked.</span></span>

```csharp
private string mailIdentity = "contoso.com";

void MailAppSetup()
{
    ProtectionPolicyManager.ProtectedContentRevoked += ProtectionPolicyManager_ProtectedContentRevoked;
    // Code goes here to set up mailbox for 'mailIdentity'.
}

private void ProtectionPolicyManager_ProtectedContentRevoked(object sender, ProtectedContentRevokedEventArgs e)
{
    if (!new System.Collections.Generic.List<string>(e.Identities).Contains
        (this.mailIdentity))
    {
        // This event is not for our identity.
        return;
    }

    // Code goes here to delete any metadata associated with 'mailIdentity'.
}
```

> **<span data-ttu-id="21565-399">APIs</span><span class="sxs-lookup"><span data-stu-id="21565-399">APIs</span></span>** <br>
[<span data-ttu-id="21565-400">ProtectionPolicyManager_ProtectedContentRevoked</span><span class="sxs-lookup"><span data-stu-id="21565-400">ProtectionPolicyManager_ProtectedContentRevoked</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.security.enterprisedata.protectionpolicymanager.protectedcontentrevoked.aspx)<br>

## <a name="related-topics"></a><span data-ttu-id="21565-401">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="21565-401">Related topics</span></span>

[<span data-ttu-id="21565-402">Windows Information Protection (WIP)-Beispiel</span><span class="sxs-lookup"><span data-stu-id="21565-402">Windows Information Protection (WIP) sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=620031&clcid=0x409)
