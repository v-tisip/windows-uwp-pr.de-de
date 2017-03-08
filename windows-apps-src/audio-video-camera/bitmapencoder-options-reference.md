---
author: laurenhughes
ms.assetid: 98BD79B3-F420-43C5-98D3-52EBDDB479A0
description: "In diesem Artikel sind die Codierungsoptionen aufgeführt, die mit BitmapEncoder verwendet werden können."
title: Referenz zu BitmapEncoder-Optionen
ms.author: lahugh
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP"
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: c29c05e7397e87851ebb0fa5fa29df3b9b58907b
ms.lasthandoff: 02/07/2017

---

# <a name="bitmapencoder-options-reference"></a>Referenz zu BitmapEncoder-Optionen

\[ Aktualisiert für UWP-Apps unter Windows 10. Artikel zu Windows 8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132). \]

In diesem Artikel sind die Codierungsoptionen aufgeführt, die mit [**BitmapEncoder**](https://msdn.microsoft.com/library/windows/apps/br226206) verwendet werden können. Eine Codierungsoption wird durch ihren Namen (eine Zeichenfolge) und einen Wert mit einem bestimmten Datentyp definiert ([**Windows.Foundation.PropertyType**](https://msdn.microsoft.com/library/windows/apps/br225871)). Weitere Informationen zur Verwendung von Bildern finden Sie unter [Erstellen, Bearbeiten und Speichern von Bitmapbildern](imaging.md).

| Name                    | PropertyType | Verwendungshinweise                                                                                        | Gültige Formate |
|-------------------------|--------------|----------------------------------------------------------------------------------------------------|---------------|
| ImageQuality            | single       | Gültige Werte von 0 bis 1,0 Höhere Werte bedeuten höhere Qualität                                 | JPEG, JPEG-XR |
| CompressionQuality      | single       | Gültige Werte von 0 bis 1,0 Höhere Werte bedeuten ein effizienteres und langsameres Komprimierungsverfahren | TIFF          |
| Lossless                | boolean      | Wenn dieser Wert auf „true“ festgelegt ist, wird die Option „ImageQuality“ ignoriert.                                        | JPEG-XR       |
| InterlaceOption         | boolean      | Gibt an, ob der Interlacemodus für das Bild verwendet wird                                                                    | PNG           |
| FilterOption            | uint8        | Verwenden Sie die [**PngFilterMode**](https://msdn.microsoft.com/library/windows/apps/br226389)-Enumeration.                                | PNG           |
| TiffCompressionMethod   | uint8        | Verwenden Sie die [**TiffCompressionMode**](https://msdn.microsoft.com/library/windows/apps/br226399)-Enumeration.                    | TIFF          |
| Luminance               | uint32Array  | Ein Array mit 64 Elementen, das die Quantifizierungskonstanten für die Leuchtdichte enthält                               | JPEG          |
| Chrominance             | uint32Array  | Ein Array mit 64 Elementen, das die Quantifizierungskonstanten für die Chrominanz enthält                             | JPEG          |
| JpegYCrCbSubsampling    | uint8        | Verwenden Sie die [**JpegSubsamplingMode**](https://msdn.microsoft.com/library/windows/apps/br226386)-Enumeration                    | JPEG          |
| SuppressApp0            | boolean      | Gibt an, ob die Erstellung eines App0-Metadatenblocks unterdrückt wird                                        | JPEG          |
| EnableV5Header32bppBGRA | boolean      | Gibt an, ob die Codierung als Version 5 des BMP-Formats erfolgen soll, die Alphawerte unterstützt.                                         | BMP           |

 

## <a name="related-topics"></a>Verwandte Themen

* [Erstellen, Bearbeiten und Speichern von Bitmapbildern](imaging.md)
* [Unterstützte Codecs](supported-codecs.md)

 





