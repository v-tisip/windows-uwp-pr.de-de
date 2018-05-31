---
title: Codieren und Decodieren von Daten
description: Dieser Beispielcode zeigt, wie Sie base64- und Hexadezimaldaten in einer App für die universelle Windows-Plattform (UWP) codieren und decodieren.
ms.assetid: 2CC23863-E840-48F4-B087-0479045743AC
author: msatranjr
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
ms.localizationpriority: medium
ms.openlocfilehash: 5c826edcd8f7ce625f3cb42df69136f500e93f4e
ms.sourcegitcommit: 6618517dc0a4e4100af06e6d27fac133d317e545
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
ms.locfileid: "1690356"
---
# <a name="encode-and-decode-data"></a><span data-ttu-id="320fa-104">Codieren und Decodieren von Daten</span><span class="sxs-lookup"><span data-stu-id="320fa-104">Encode and decode data</span></span>



<span data-ttu-id="320fa-105">Dieser Beispielcode zeigt, wie Sie base64- und Hexadezimaldaten in einer App für die universelle Windows-Plattform (UWP) codieren und decodieren.</span><span class="sxs-lookup"><span data-stu-id="320fa-105">This example code shows how to encode and decode base64 and hexadecimal data in an Universal Windows Platform (UWP) app.</span></span>

```cs
public void EncodeDecodeBase64()
{
    // Define a Base64 encoded string.
    String strBase64 = "uiwyeroiugfyqcajkds897945234==";

    // Decoded the string from Base64 to binary.
    IBuffer buffer = CryptographicBuffer.DecodeFromBase64String(strBase64);

    // Encode the buffer back into a Base64 string.
    String strBase64New = CryptographicBuffer.EncodeToBase64String(buffer);
}

public void EncodeDecodeHex()
{
    // Define a hexadecimal string.
    String strHex = "30310AFF";

    // Decode a hexadecimal string to binary.
    IBuffer buffer = CryptographicBuffer.DecodeFromHexString(strHex);

    // Encode the buffer back into a hexadecimal string.
    String strHexNew = CryptographicBuffer.EncodeToHexString(buffer);
}
```
