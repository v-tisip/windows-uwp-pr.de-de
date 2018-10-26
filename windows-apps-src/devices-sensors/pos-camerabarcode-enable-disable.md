---
author: TerryWarwick
title: Kamera-Strichcodescannerkonfiguration
description: Aktivieren oder Deaktivieren des Kamera-Strichcodescanners
ms.author: jken
ms.date: 05/1/2018
ms.topic: article
keywords: Windows 10, UWP, Point Of Service, POS
ms.localizationpriority: medium
ms.openlocfilehash: 35666f64c88ad56b8f5bd3052ebbee069ccaecfc
ms.sourcegitcommit: d0e836dfc937ebf7dfa9c424620f93f3c8e0a7e8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5666446"
---
# <a name="enable-or-disable-the-software-decoder-that-ships-with-windows"></a><span data-ttu-id="b46e5-104">Enthält Informationen zum aktivieren oder deaktivieren der Standard-Software-Decoder, der mit im Lieferumfang von Windows enthalten ist</span><span class="sxs-lookup"><span data-stu-id="b46e5-104">Enable or disable the software decoder that ships with Windows</span></span>
<span data-ttu-id="b46e5-105">In Windows10, Version 1803, ist der Software-Decoder installiert und standardmäßig aktiviert.</span><span class="sxs-lookup"><span data-stu-id="b46e5-105">In Windows 10, version 1803, the software decoder is installed and enabled by default.</span></span>  <span data-ttu-id="b46e5-106">Sie können den im Lieferumfang von Windows enthaltenen Software-Decoder deaktivieren, wenn Sie den Kamera-Strichcodescanner nicht wünschen oder einen Decoder von einem Drittanbieter haben, der mit Windows.Devices.PointOfService.BarcodeScanner-APIs verwendet werden kann und nicht beide verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="b46e5-106">You can disable the software decoder that ships with Windows if you do not want to use Camera Barcode Scanner or if you have acquired a 3rd party decoder that works with Windows.Devices.PointOfService.BarcodeScanner APIs and do not want to use both.</span></span>

## <a name="enable-or-disable-using-the-system-registry"></a><span data-ttu-id="b46e5-107">Aktivieren Sie oder deaktivieren Sie die Verwendung der Registrierung</span><span class="sxs-lookup"><span data-stu-id="b46e5-107">Enable or disable using the system registry</span></span>
<span data-ttu-id="b46e5-108">Der Softwaredecoder, der im Lieferumfang von Windows enthalten ist, kann über die Registrierung durch Hinzufügen des Registrierungsschlüssels *InboxDecoder* unter *HKLM\Software\ Microsoft \PointOfService\ BarcodeScanner* aktiviert oder deaktiviert werden, indem Sie den Wert *Aktivieren* wie folgt festlegen.</span><span class="sxs-lookup"><span data-stu-id="b46e5-108">The software decoder that ships with Windows can be enabled or disabled via the system registry by adding the registry key *InboxDecoder* under *HKLM\Software\Microsoft\PointOfService\BarcodeScanner* and setting the *Enable* value as described below.</span></span>

| <span data-ttu-id="b46e5-109">Wertname</span><span class="sxs-lookup"><span data-stu-id="b46e5-109">Value name</span></span>  | <span data-ttu-id="b46e5-110">Werttyp</span><span class="sxs-lookup"><span data-stu-id="b46e5-110">Value Type</span></span> | <span data-ttu-id="b46e5-111">Wert</span><span class="sxs-lookup"><span data-stu-id="b46e5-111">Value</span></span> | <span data-ttu-id="b46e5-112">Status</span><span class="sxs-lookup"><span data-stu-id="b46e5-112">Status</span></span> |
| ----------- | --------- | -------|--------|
| <span data-ttu-id="b46e5-113">Aktivieren</span><span class="sxs-lookup"><span data-stu-id="b46e5-113">Enable</span></span>      | <span data-ttu-id="b46e5-114">DWORD</span><span class="sxs-lookup"><span data-stu-id="b46e5-114">DWORD</span></span>     | <span data-ttu-id="b46e5-115">1 (Standard)</span><span class="sxs-lookup"><span data-stu-id="b46e5-115">1 (default)</span></span><br/><span data-ttu-id="b46e5-116">0</span><span class="sxs-lookup"><span data-stu-id="b46e5-116">0</span></span> |  <span data-ttu-id="b46e5-117">Enthält Informationen zum aktivieren des Standard-Software-Decoders, der im Lieferumfang von Windows enthalten ist</span><span class="sxs-lookup"><span data-stu-id="b46e5-117">Enables the software decoder that ships with Windows</span></span> <br/> <span data-ttu-id="b46e5-118">Enthält Informationen zum deaktivieren des Standard-Software-Decoders, der im Lieferumfang von Windows enthalten ist</span><span class="sxs-lookup"><span data-stu-id="b46e5-118">Disables the software decoder that ships with Windows</span></span> |


<span data-ttu-id="b46e5-119">Hier ist eine Beispiel-Registrierungsdatei, die Sie zum **deaktivieren** des Softwaredecoders verwenden können, der im Lieferumfang von Windows enthalten ist:</span><span class="sxs-lookup"><span data-stu-id="b46e5-119">Here is an example registry file that you can use to **disable** the software decoder that ships with Windows:</span></span>

```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PointOfService\BarcodeScanner\InboxDecoder]
"Enable"=dword:0000000


```  
    
<span data-ttu-id="b46e5-120">Verwenden Sie die Beispiel-Registrierungsdatei zum **aktivieren** des Softwaredecoders, der im Lieferumfang von Windows enthalten ist:</span><span class="sxs-lookup"><span data-stu-id="b46e5-120">Use this example registry file to **enable** the software decoder that ships with Windows:</span></span>

```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PointOfService\BarcodeScanner\InboxDecoder]
"Enable"=dword:0000001


```  

> [!Warning] 
> <span data-ttu-id="b46e5-121">Wird die Registrierung falsch angepasst, können schwerwiegende Probleme auftreten.</span><span class="sxs-lookup"><span data-stu-id="b46e5-121">Serious problems might occur if you modify the registry incorrectly.</span></span>  <span data-ttu-id="b46e5-122">Für den zusätzlichen Schutz, sichern Sie die Registrierung, bevor Sie diese ändern.</span><span class="sxs-lookup"><span data-stu-id="b46e5-122">For added protection, back up the registry before you modify it.</span></span>  <span data-ttu-id="b46e5-123">Sie können dann die Registrierung wiederherstellen, falls ein Problem auftritt.</span><span class="sxs-lookup"><span data-stu-id="b46e5-123">Then, you can restore the registry if a problem occurs.</span></span>  <span data-ttu-id="b46e5-124">Weitere Informationen zur Sicherung und zum Wiederherstellen der Registrierung erhalten Sie in der nachstehende Artikelnummer des MicrosoftKnowledgeBase-Artikels:</span><span class="sxs-lookup"><span data-stu-id="b46e5-124">For more information about how to back up and restore the registry, click the following article number to view the article in the Microsoft Knowledge Base:</span></span> <br/><br/> <span data-ttu-id="b46e5-125">[322756](http://support.microsoft.com/kb/322756) Sichern und Wiederherstellen der Registrierung in Windows.</span><span class="sxs-lookup"><span data-stu-id="b46e5-125">[322756](http://support.microsoft.com/kb/322756) How to back up and restore the registry in Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="b46e5-126">Der in Windows10 integrierte Softwaredecoder stammt von [**Digimarc Corporation**](https://www.digimarc.com/).</span><span class="sxs-lookup"><span data-stu-id="b46e5-126">The software decoder built into Windows 10 is provided courtesy of  [**Digimarc Corporation**](https://www.digimarc.com/).</span></span>
