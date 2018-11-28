---
title: Bereitstellen von Strichcodescanner-Profilen mit MDM
description: Strichcodescanner-Profile können mit einem MDM-Server bereitgestellt werden.
ms.assetid: 99ED3BD8-022C-40C2-9C65-F599186548FE
ms.date: 09/26/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: dbcaa683e2c7a2bb18d88fcba03e10fa951d4459
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7832345"
---
# <a name="deploy-barcode-scanner-profiles-with-mdm"></a>Bereitstellen von Strichcodescanner-Profilen mit MDM

**Hinweis:** dieses Feature erfordert Windows 10 Mobile oder höher.

Strichcodescanner-Profile können mit einem MDM-Server bereitgestellt werden. Verwenden Sie *OemProfile* in [EnterpriseExtFileSystem CSP](https://msdn.microsoft.com/library/windows/hardware/mt157025), um die Profile bereitzustellen und im Ordner „\\Data\\SharedData\\OEM\\Public\\Profile“ abzulegen. Diese Scannerprofile können dann durch Treiberhersteller verwendet werden, um Einstellungen zu konfigurieren, die nicht auf der API-Oberfläche verfügbar sind.

Microsoft definiert die Einzelheiten eines Scannerprofils und seine Implementierung nicht.

## <a name="related-topics"></a>Verwandte Themen
- [EnterpriseExtFileSystem-Konfigurationsdienstanbieter](https://msdn.microsoft.com/library/windows/hardware/mt157025)
- [Unterstützung für Barcode-Scanner-Geräte](https://docs.microsoft.com/en-us/windows/uwp/devices-sensors/pos-device-support#barcode-scanner)