---
author: mcleblanc
ms.assetid: B48E21AB-0EA5-444B-8333-393DD8D1B76D
title: Im Unternehmen freigegebener Speicher
description: Im Unternehmen freigegebener Speicher definiert lokale Datenspeicherorte für Branchenanwendungen zum Freigeben von Daten.
ms.author: markl
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 5236767d4c02d873106c7b1799c8428d84cccd53
ms.sourcegitcommit: 4d88adfaf544a3dab05f4660e2f59bbe60311c00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6463216"
---
# <a name="enterprise-shared-storage"></a><span data-ttu-id="30fc9-104">Im Unternehmen freigegebener Speicher</span><span class="sxs-lookup"><span data-stu-id="30fc9-104">Enterprise Shared Storage</span></span>

<span data-ttu-id="30fc9-105">Der freigegebene Speicher besteht aus zwei Speicherorten, auf die Apps mit der eingeschränkten Funktionalität **enterpriseDeviceLockdown** und einem Unternehmenszertifikat vollständigen Lese- und Schreibzugriff haben.</span><span class="sxs-lookup"><span data-stu-id="30fc9-105">The shared storage consists of two locations, where apps with the restricted capability  **enterpriseDeviceLockdown** and an Enterprise certificate have full read and write access.</span></span> <span data-ttu-id="30fc9-106">Die **enterpriseDeviceLockdown**-Funktion ermöglicht Apps die Verwendung der API zur Gerätesperrung und den Zugriff auf im Unternehmen freigegebene Speicherordner.</span><span class="sxs-lookup"><span data-stu-id="30fc9-106">Note that the **enterpriseDeviceLockdown** capability allows apps to use the device lock down API and access the enterprise shared storage folders.</span></span> <span data-ttu-id="30fc9-107">Weitere Informationen zur API finden Sie unter dem [**Windows.Embedded.DeviceLockdown**](http://go.microsoft.com/fwlink/?LinkId=699331)-Namespace.</span><span class="sxs-lookup"><span data-stu-id="30fc9-107">For more information about the API, see [**Windows.Embedded.DeviceLockdown**](http://go.microsoft.com/fwlink/?LinkId=699331) namespace.</span></span>  

<span data-ttu-id="30fc9-108">Diese Speicherorte werden auf dem lokalen Laufwerk festgelegt:</span><span class="sxs-lookup"><span data-stu-id="30fc9-108">These locations are set on the local drive:</span></span>
- <span data-ttu-id="30fc9-109">\Data\SharedData\Enterprise\Persistent</span><span class="sxs-lookup"><span data-stu-id="30fc9-109">\Data\SharedData\Enterprise\Persistent</span></span>
- <span data-ttu-id="30fc9-110">\Data\SharedData\Enterprise\Non-Persistent</span><span class="sxs-lookup"><span data-stu-id="30fc9-110">\Data\SharedData\Enterprise\Non-Persistent</span></span>

## <a name="scenarios"></a><span data-ttu-id="30fc9-111">Szenarien</span><span class="sxs-lookup"><span data-stu-id="30fc9-111">Scenarios</span></span>

<span data-ttu-id="30fc9-112">Im Unternehmen freigegebener Speicher unterstützt die folgenden Szenarien.</span><span class="sxs-lookup"><span data-stu-id="30fc9-112">Enterprise shared storage provides support for the following scenarios.</span></span>

- <span data-ttu-id="30fc9-113">Sie können Daten in einer Instanz einer App, zwischen Instanzen derselben App oder zwischen verschiedenen Apps freigeben, wenn beide über die entsprechenden Funktionen und Zertifikate verfügen.</span><span class="sxs-lookup"><span data-stu-id="30fc9-113">You can share data within an instance of an app, between instances of the same app, or even between apps assuming they both have the appropriate capability and certificate.</span></span>
- <span data-ttu-id="30fc9-114">Sie können Daten auf der lokalen Festplatte im Ordner „\Data\SharedData\Enterprise\Persistent“ speichern, und die Daten bleiben auch nach dem Zurücksetzen des Geräts erhalten.</span><span class="sxs-lookup"><span data-stu-id="30fc9-114">You can store data on the local hard drive in the \Data\SharedData\Enterprise\Persistent folder and it persists even after the device has been reset.</span></span>
- <span data-ttu-id="30fc9-115">Sie können Dateien über die mobile Geräteverwaltung (Mobile Device Management, MDM) auf einem Gerät bearbeiten (u. a. lesen, schreiben und löschen).</span><span class="sxs-lookup"><span data-stu-id="30fc9-115">Manipulate files, including read, write, and delete of files on a device via Mobile Device Management (MDM) service.</span></span> <span data-ttu-id="30fc9-116">Weitere Informationen zur Verwendung von im Unternehmen freigegebenem Speichern mit dem MDM-Dienst finden Sie unter [EnterpriseExtFileSystem-CSP](http://go.microsoft.com/fwlink/?LinkId=699333).</span><span class="sxs-lookup"><span data-stu-id="30fc9-116">For more information on how to use enterprise shared storage through the MDM service, see [EnterpriseExtFileSystem CSP](http://go.microsoft.com/fwlink/?LinkId=699333).</span></span>

## <a name="access-enterprise-shared-storage"></a><span data-ttu-id="30fc9-117">Zugriff auf im Unternehmen freigegebenen Speicher</span><span class="sxs-lookup"><span data-stu-id="30fc9-117">Access enterprise shared storage</span></span>

<span data-ttu-id="30fc9-118">Das folgende Beispiel zeigt, wie Sie die Funktion für den Zugriff auf im Unternehmen freigegebenen Speicher im Paketmanifest deklarieren und mit der Windows.Storage.StorageFolder-Klasse auf die Ordner für den freigegebenen Speicher zugreifen.</span><span class="sxs-lookup"><span data-stu-id="30fc9-118">The following example shows how to declare the capability to access enterprise shared storage in the package manifest, and how to access the shared storage folders by using the Windows.Storage.StorageFolder class.</span></span>

<span data-ttu-id="30fc9-119">Schließen Sie in das App-Paketmanifest die folgende Funktion ein:</span><span class="sxs-lookup"><span data-stu-id="30fc9-119">In your app package manifest, include the following capability:</span></span>

```xml
<Package
  xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
  xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:rescap="http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities"
  IgnorableNamespaces="uap mp rescap">

…

<Capabilities>
    <rescap:Capability Name="enterpriseDeviceLockdown"/>
</Capabilities>
```

<span data-ttu-id="30fc9-120">Für den Zugriff auf den freigegebenen Datenspeicherort verwendet die App den folgenden Code.</span><span class="sxs-lookup"><span data-stu-id="30fc9-120">To access the shared data location, your app would use the following code.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using Windows.Storage;

…

// Get the Enterprise Shared Storage folder.
var enterprisePersistentFolderRoot = @"C:\Data\SharedData\Enterprise\Persistent";

StorageFolder folder =
    await StorageFolder.GetFolderFromPathAsync(enterprisePersistentFolderRoot);

// Get the files in the folder.
IReadOnlyList<StorageFile> sortedItems =
    await folder.GetFilesAsync();

// Iterate over the results and print the list of files
// to the Visual Studio Output window.
foreach (StorageFile file in sortedItems)
    Debug.WriteLine(file.Name + ", " + file.DateCreated);
```

