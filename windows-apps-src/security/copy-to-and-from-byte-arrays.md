---
title: Kopieren in und aus Bytearrays
description: Dieser Beispielcode zeigt, wie Sie in und aus Bytearrays in einer UWP (Universelle Windows-Plattform)-App kopieren können.
ms.assetid: C343B08C-1FA1-40FD-8CA5-7FC9B707C5E3
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, Uwp, Sicherheit
ms.localizationpriority: medium
ms.openlocfilehash: b3ce63ca1780f9ed1ecd32f3ab1c029a1a92e1b5
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7693840"
---
# <a name="copy-to-and-from-byte-arrays"></a><span data-ttu-id="ad1a4-104">Kopieren in und aus Bytearrays</span><span class="sxs-lookup"><span data-stu-id="ad1a4-104">Copy to and from byte arrays</span></span>



<span data-ttu-id="ad1a4-105">Dieser Beispielcode zeigt, wie Sie in und aus Bytearrays in einer UWP (Universelle Windows-Plattform)-App kopieren können.</span><span class="sxs-lookup"><span data-stu-id="ad1a4-105">This example code shows how to copy to and from byte arrays in an Universal Windows Platform (UWP) app.</span></span>

```cs
public void ByteArrayCopy()
{
    // Initialize a byte array.
    byte[] bytes = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

    // Create a buffer from the byte array.
    IBuffer buffer = CryptographicBuffer.CreateFromByteArray(bytes);

    // Encode the buffer into a hexadecimal string (for display);
    string hex = CryptographicBuffer.EncodeToHexString(buffer);

    // Copy the buffer back into a new byte array.
    byte[] newByteArray;
    CryptographicBuffer.CopyToByteArray(buffer, out newByteArray);
}
```