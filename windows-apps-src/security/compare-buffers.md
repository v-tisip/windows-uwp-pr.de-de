---
title: Vergleichen von Puffern
description: "Dieser Beispielcode zeigt, wie Sie Puffer in einer App für die Universelle Windows-Plattform (UWP) vergleichen."
ms.assetid: CB086E51-544A-470D-B7C8-C055271CD615
author: awkoren
ms.author: alkoren
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: d5f84ce00026c9e2381e7b90213b3dcdd8aad9ff
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: HT
ms.contentlocale: de-DE
---
# <a name="compare-buffers"></a><span data-ttu-id="df84d-104">Vergleichen von Puffern</span><span class="sxs-lookup"><span data-stu-id="df84d-104">Compare buffers</span></span>


<span data-ttu-id="df84d-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="df84d-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="df84d-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132). \]</span><span class="sxs-lookup"><span data-stu-id="df84d-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="df84d-107">Dieser Beispielcode zeigt, wie Sie Puffer in einer Universellen Windows-Plattform (UWP)-App vergleichen können.</span><span class="sxs-lookup"><span data-stu-id="df84d-107">This example code shows how to compare buffers in an Universal Windows Platform (UWP) app.</span></span>

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