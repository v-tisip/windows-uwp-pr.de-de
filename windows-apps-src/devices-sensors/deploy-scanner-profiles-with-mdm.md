---
title: Bereitstellen von Strichcodescanner-Profilen mit MDM
author: PatrickFarley
description: Strichcodescanner-Profile können mit einem MDM-Server bereitgestellt werden.
ms.assetid: 99ED3BD8-022C-40C2-9C65-F599186548FE
ms.author: pafarley
ms.date: 09/26/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: cfd9692620273952483ec7da65a69b643cb5bf4f
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7296955"
---
# <a name="deploy-barcode-scanner-profiles-with-mdm"></a>Bereitstellen von Strichcodescanner-Profilen mit MDM

**Hinweis:** dieses Feature erfordert Windows 10 Mobile oder höher.

Strichcodescanner-Profile können mit einem MDM-Server bereitgestellt werden. Verwenden Sie *OemProfile* in [EnterpriseExtFileSystem CSP](https://msdn.microsoft.com/library/windows/hardware/mt157025), um die Profile bereitzustellen und im Ordner „\\Data\\SharedData\\OEM\\Public\\Profile“ abzulegen. Diese Scannerprofile können dann durch Treiberhersteller verwendet werden, um Einstellungen zu konfigurieren, die nicht auf der API-Oberfläche verfügbar sind.

Microsoft definiert die Einzelheiten eines Scannerprofils und seine Implementierung nicht.

## <a name="related-topics"></a>Verwandte Themen
- [EnterpriseExtFileSystem-Konfigurationsdienstanbieter](https://msdn.microsoft.com/library/windows/hardware/mt157025)
- [Unterstützung für Barcode-Scanner-Geräte](https://docs.microsoft.com/en-us/windows/uwp/devices-sensors/pos-device-support#barcode-scanner)