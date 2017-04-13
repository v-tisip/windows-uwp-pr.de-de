---
title: Bereitstellen von Strichcodescanner-Profilen mit MDM
author: mukin
description: "Strichcodescanner-Profile können mit einem MDM-Server bereitgestellt werden."
ms.assetid: 99ED3BD8-022C-40C2-9C65-F599186548FE
ms.openlocfilehash: 51d3b90dd7f202fd86285bb3f95c78ded4a8b6d8
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="deploy-barcode-scanner-profiles-with-mdm"></a>Bereitstellen von Strichcodescanner-Profilen mit MDM

**Hinweis:** Dieses Feature erfordert Windows10 Mobile oder höher.

Strichcodescanner-Profile können mit einem MDM-Server bereitgestellt werden. Verwenden Sie *OemProfile* in [EnterpriseExtFileSystem CSP](https://msdn.microsoft.com/library/windows/hardware/mt157025), um die Profile bereitzustellen und im Ordner „\\Data\\SharedData\\OEM\\Public\\Profile“ abzulegen. Diese Scannerprofile können dann durch Treiberhersteller verwendet werden, um Einstellungen zu konfigurieren, die nicht auf der API-Oberfläche verfügbar sind.

Microsoft definiert die Einzelheiten eines Scannerprofils und seine Implementierung nicht.

## <a name="related-topics"></a>Verwandte Themen
[Strichcodescanner](barcode-scanner.md)

[EnterpriseExtFileSystem CSP](https://msdn.microsoft.com/library/windows/hardware/mt157025)