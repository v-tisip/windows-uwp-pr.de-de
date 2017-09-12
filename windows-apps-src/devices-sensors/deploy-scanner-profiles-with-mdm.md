---
title: Bereitstellen von Strichcodescanner-Profilen mit MDM
author: PatrickFarley
description: "Strichcodescanner-Profile können mit einem MDM-Server bereitgestellt werden."
ms.assetid: 99ED3BD8-022C-40C2-9C65-F599186548FE
ms.openlocfilehash: a63a09e64b6e2b935963a3f49ed7cbc6b82bdcef
ms.sourcegitcommit: d2ec178103f49b198da2ee486f1681e38dcc8e7b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/28/2017
---
# <a name="deploy-barcode-scanner-profiles-with-mdm"></a><span data-ttu-id="725dc-103">Bereitstellen von Strichcodescanner-Profilen mit MDM</span><span class="sxs-lookup"><span data-stu-id="725dc-103">Deploy barcode scanner profiles with MDM</span></span>

<span data-ttu-id="725dc-104">**Hinweis:** Dieses Feature erfordert Windows10 Mobile oder höher.</span><span class="sxs-lookup"><span data-stu-id="725dc-104">**Note**  This feature requires Windows 10 Mobile or later.</span></span>

<span data-ttu-id="725dc-105">Strichcodescanner-Profile können mit einem MDM-Server bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="725dc-105">Barcode scanner profiles can be deployed with an MDM server.</span></span> <span data-ttu-id="725dc-106">Verwenden Sie *OemProfile* in [EnterpriseExtFileSystem CSP](https://msdn.microsoft.com/library/windows/hardware/mt157025), um die Profile bereitzustellen und im Ordner „\\Data\\SharedData\\OEM\\Public\\Profile“ abzulegen.</span><span class="sxs-lookup"><span data-stu-id="725dc-106">To deploy the profiles, use *OemProfile* in the [EnterpriseExtFileSystem CSP](https://msdn.microsoft.com/library/windows/hardware/mt157025) to place them into the \\Data\\SharedData\\OEM\\Public\\Profile folder.</span></span> <span data-ttu-id="725dc-107">Diese Scannerprofile können dann durch Treiberhersteller verwendet werden, um Einstellungen zu konfigurieren, die nicht auf der API-Oberfläche verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="725dc-107">These scanner profiles can then be used by driver manufacturers to configure settings that are not exposed through the API surface.</span></span>

<span data-ttu-id="725dc-108">Microsoft definiert die Einzelheiten eines Scannerprofils und seine Implementierung nicht.</span><span class="sxs-lookup"><span data-stu-id="725dc-108">Microsoft does not define the specifics of a scanner profile or how to implement them.</span></span>

## <a name="related-topics"></a><span data-ttu-id="725dc-109">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="725dc-109">Related topics</span></span>
[<span data-ttu-id="725dc-110">Strichcodescanner</span><span class="sxs-lookup"><span data-stu-id="725dc-110">Barcode Scanner</span></span>](barcode-scanner.md)

[<span data-ttu-id="725dc-111">EnterpriseExtFileSystem CSP</span><span class="sxs-lookup"><span data-stu-id="725dc-111">EnterpriseExtFileSystem CSP</span></span>](https://msdn.microsoft.com/library/windows/hardware/mt157025)