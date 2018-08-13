---
title: Bereitstellen von Strichcodescanner-Profilen mit MDM
author: PatrickFarley
description: Strichcodescanner-Profile können mit einem MDM-Server bereitgestellt werden.
ms.assetid: 99ED3BD8-022C-40C2-9C65-F599186548FE
ms.author: pafarley
ms.date: 09/26/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: ef7f1029573d2ff98e744ceb44b108a67a7c0d0b
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "1018083"
---
# <a name="deploy-barcode-scanner-profiles-with-mdm"></a><span data-ttu-id="8b94a-104">Bereitstellen von Strichcodescanner-Profilen mit MDM</span><span class="sxs-lookup"><span data-stu-id="8b94a-104">Deploy barcode scanner profiles with MDM</span></span>

<span data-ttu-id="8b94a-105">**Hinweis:** Dieses Feature erfordert Windows10 Mobile oder höher.</span><span class="sxs-lookup"><span data-stu-id="8b94a-105">**Note**  This feature requires Windows 10 Mobile or later.</span></span>

<span data-ttu-id="8b94a-106">Strichcodescanner-Profile können mit einem MDM-Server bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="8b94a-106">Barcode scanner profiles can be deployed with an MDM server.</span></span> <span data-ttu-id="8b94a-107">Verwenden Sie *OemProfile* in [EnterpriseExtFileSystem CSP](https://msdn.microsoft.com/library/windows/hardware/mt157025), um die Profile bereitzustellen und im Ordner „\\Data\\SharedData\\OEM\\Public\\Profile“ abzulegen.</span><span class="sxs-lookup"><span data-stu-id="8b94a-107">To deploy the profiles, use *OemProfile* in the [EnterpriseExtFileSystem CSP](https://msdn.microsoft.com/library/windows/hardware/mt157025) to place them into the \\Data\\SharedData\\OEM\\Public\\Profile folder.</span></span> <span data-ttu-id="8b94a-108">Diese Scannerprofile können dann durch Treiberhersteller verwendet werden, um Einstellungen zu konfigurieren, die nicht auf der API-Oberfläche verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="8b94a-108">These scanner profiles can then be used by driver manufacturers to configure settings that are not exposed through the API surface.</span></span>

<span data-ttu-id="8b94a-109">Microsoft definiert die Einzelheiten eines Scannerprofils und seine Implementierung nicht.</span><span class="sxs-lookup"><span data-stu-id="8b94a-109">Microsoft does not define the specifics of a scanner profile or how to implement them.</span></span>

## <a name="related-topics"></a><span data-ttu-id="8b94a-110">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="8b94a-110">Related topics</span></span>
- [<span data-ttu-id="8b94a-111">EnterpriseExtFileSystem CSP</span><span class="sxs-lookup"><span data-stu-id="8b94a-111">EnterpriseExtFileSystem CSP</span></span>](https://msdn.microsoft.com/library/windows/hardware/mt157025)
- [<span data-ttu-id="8b94a-112">Unterstützung von Barcodes Scanner Geräte</span><span class="sxs-lookup"><span data-stu-id="8b94a-112">Barcode scanner device support</span></span>](https://docs.microsoft.com/en-us/windows/uwp/devices-sensors/pos-device-support#barcode-scanner)