---
title: Kopieren in und aus Bytearrays
description: "Dieser Beispielcode zeigt, wie Sie in einer App für die Universelle Windows-Plattform (UWP) in und aus Bytearrays kopieren."
ms.assetid: C343B08C-1FA1-40FD-8CA5-7FC9B707C5E3
author: awkoren
ms.author: alkoren
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 6eee2c509956dcc38907334000a35fd9c9344a52
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: HT
ms.contentlocale: de-DE
---
# <a name="copy-to-and-from-byte-arrays"></a><span data-ttu-id="1569a-104">Kopieren in und aus Bytearrays</span><span class="sxs-lookup"><span data-stu-id="1569a-104">Copy to and from byte arrays</span></span>


<span data-ttu-id="1569a-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="1569a-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="1569a-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="1569a-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="1569a-107">Dieser Beispielcode zeigt, wie Sie in einer UWP (Universelle Windows-Plattform)-App in und aus Bytearrays kopieren können.</span><span class="sxs-lookup"><span data-stu-id="1569a-107">This example code shows how to copy to and from byte arrays in an Universal Windows Platform (UWP) app.</span></span>

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