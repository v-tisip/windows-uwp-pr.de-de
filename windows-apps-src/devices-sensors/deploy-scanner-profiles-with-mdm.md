---
title: Bereitstellen von Strichcodescanner-Profilen mit MDM
description: Strichcodescanner-Profile können mit einem MDM-Server bereitgestellt werden.
ms.assetid: 99ED3BD8-022C-40C2-9C65-F599186548FE
ms.date: 09/26/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: dbcaa683e2c7a2bb18d88fcba03e10fa951d4459
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8893659"
---
# <a name="deploy-barcode-scanner-profiles-with-mdm"></a><span data-ttu-id="99485-104">Bereitstellen von Strichcodescanner-Profilen mit MDM</span><span class="sxs-lookup"><span data-stu-id="99485-104">Deploy barcode scanner profiles with MDM</span></span>

<span data-ttu-id="99485-105">**Hinweis:** dieses Feature erfordert Windows 10 Mobile oder höher.</span><span class="sxs-lookup"><span data-stu-id="99485-105">**Note**This feature requires Windows10 Mobile or later.</span></span>

<span data-ttu-id="99485-106">Strichcodescanner-Profile können mit einem MDM-Server bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="99485-106">Barcode scanner profiles can be deployed with an MDM server.</span></span> <span data-ttu-id="99485-107">Verwenden Sie *OemProfile* in [EnterpriseExtFileSystem CSP](https://msdn.microsoft.com/library/windows/hardware/mt157025), um die Profile bereitzustellen und im Ordner „\\Data\\SharedData\\OEM\\Public\\Profile“ abzulegen.</span><span class="sxs-lookup"><span data-stu-id="99485-107">To deploy the profiles, use *OemProfile* in the [EnterpriseExtFileSystem CSP](https://msdn.microsoft.com/library/windows/hardware/mt157025) to place them into the \\Data\\SharedData\\OEM\\Public\\Profile folder.</span></span> <span data-ttu-id="99485-108">Diese Scannerprofile können dann durch Treiberhersteller verwendet werden, um Einstellungen zu konfigurieren, die nicht auf der API-Oberfläche verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="99485-108">These scanner profiles can then be used by driver manufacturers to configure settings that are not exposed through the API surface.</span></span>

<span data-ttu-id="99485-109">Microsoft definiert die Einzelheiten eines Scannerprofils und seine Implementierung nicht.</span><span class="sxs-lookup"><span data-stu-id="99485-109">Microsoft does not define the specifics of a scanner profile or how to implement them.</span></span>

## <a name="related-topics"></a><span data-ttu-id="99485-110">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="99485-110">Related topics</span></span>
- [<span data-ttu-id="99485-111">EnterpriseExtFileSystem-Konfigurationsdienstanbieter</span><span class="sxs-lookup"><span data-stu-id="99485-111">EnterpriseExtFileSystem CSP</span></span>](https://msdn.microsoft.com/library/windows/hardware/mt157025)
- [<span data-ttu-id="99485-112">Unterstützung für Barcode-Scanner-Geräte</span><span class="sxs-lookup"><span data-stu-id="99485-112">Barcode scanner device support</span></span>](https://docs.microsoft.com/en-us/windows/uwp/devices-sensors/pos-device-support#barcode-scanner)