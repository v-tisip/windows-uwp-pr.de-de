---
title: Vergleichen von Puffern
description: Dieser Beispielcode zeigt, wie Sie Puffer in einer UWP (Universelle Windows-Plattform)-App vergleichen können.
ms.assetid: CB086E51-544A-470D-B7C8-C055271CD615
author: msatranjr
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Sicherheit
ms.localizationpriority: medium
ms.openlocfilehash: 139514166d623dc9a621b533cd3ce4bb7fdea0c5
ms.sourcegitcommit: 1938851dc132c60348f9722daf994b86f2ead09e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2018
ms.locfileid: "4267569"
---
# <a name="compare-buffers"></a><span data-ttu-id="345fd-104">Vergleichen von Puffern</span><span class="sxs-lookup"><span data-stu-id="345fd-104">Compare buffers</span></span>



<span data-ttu-id="345fd-105">Dieser Beispielcode zeigt, wie Sie Puffer in einer UWP (Universelle Windows-Plattform)-App vergleichen können.</span><span class="sxs-lookup"><span data-stu-id="345fd-105">This example code shows how to compare buffers in an Universal Windows Platform (UWP) app.</span></span>

```cs
public void CompareBuffers()
{
    // Create a hexadecimal string.
    String strHex = "30310aff";

    // Create a Base64 string that is equivalent to strHex.
    String strBase64v1 = "MDEK/w==";

    // Create a Base64 string that is not equivalent to strHex.
    String strBase64v2 = "KEDM/w==";

    // Decode strHex to a buffer.
    IBuffer buff1 = CryptographicBuffer.DecodeFromHexString(strHex);

    // Decode strBase64v1 to a buffer.
    IBuffer buff2 = CryptographicBuffer.DecodeFromBase64String(strBase64v1);

    // Decode strBase64v2 to a buffer.
    IBuffer buff3 = CryptographicBuffer.DecodeFromBase64String(strBase64v2);

    // Compare the hexadecimal-decoded buff1 to the Base64-decoded buff2.
    // The code points in the two buffers are equal, and the Boolean value
    // is true.
    Boolean bVal_1 = CryptographicBuffer.Compare(buff1, buff2);

    // Compare the hexadecimal-decoded buff1 to the Base64-decoded buff3.
    // The code points in the two buffers are not equal, and the Boolean value
    // is false.
    Boolean bVal_2 = CryptographicBuffer.Compare(buff1, buff3);
}
```