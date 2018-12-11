---
title: Codieren und Decodieren von Daten
description: Dieser Beispielcode zeigt, wie Sie base64- und Hexadezimaldaten in einer App für die universelle Windows-Plattform (UWP) codieren und decodieren.
ms.assetid: 2CC23863-E840-48F4-B087-0479045743AC
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, Uwp, Sicherheit
ms.localizationpriority: medium
ms.openlocfilehash: 3c4e694dca3c84c7e94e513d8bb10a3f405bbc86
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "8875459"
---
# <a name="encode-and-decode-data"></a><span data-ttu-id="38b7f-104">Codieren und Decodieren von Daten</span><span class="sxs-lookup"><span data-stu-id="38b7f-104">Encode and decode data</span></span>



<span data-ttu-id="38b7f-105">Dieser Beispielcode zeigt, wie Sie base64- und Hexadezimaldaten in einer App für die universelle Windows-Plattform (UWP) codieren und decodieren.</span><span class="sxs-lookup"><span data-stu-id="38b7f-105">This example code shows how to encode and decode base64 and hexadecimal data in an Universal Windows Platform (UWP) app.</span></span>

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
