---
title: Erstellen zufälliger Zahlen
description: Dieser Beispielcode zeigt, wie Sie zufällige Zahlen oder Puffer für die Verwendung bei der Kryptografie in einer UWP (Universelle Windows-Plattform)-App erstellen.
ms.assetid: 15746824-F93A-4DC7-836E-EBA916D2CFD3
author: msatranjr
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Sicherheit
ms.localizationpriority: medium
ms.openlocfilehash: 595b4ab47e3c6c833a4b8f2e692a0cc0c8ffcaa4
ms.sourcegitcommit: e4f3e1b2d08a02b9920e78e802234e5b674e7223
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2018
ms.locfileid: "4206212"
---
# <a name="create-random-numbers"></a><span data-ttu-id="ad0e1-104">Erstellen zufälliger Zahlen</span><span class="sxs-lookup"><span data-stu-id="ad0e1-104">Create random numbers</span></span>



<span data-ttu-id="ad0e1-105">Dieser Beispielcode zeigt, wie Sie zufällige Zahlen oder Puffer für die Verwendung bei der Kryptografie in einer UWP (Universelle Windows-Plattform)-App erstellen.</span><span class="sxs-lookup"><span data-stu-id="ad0e1-105">This example code shows how to create a random number or buffer for use in cryptography in an Universal Windows Platform (UWP) app.</span></span>

```cs
public string GenerateRandomData()
{
    // Define the length, in bytes, of the buffer.
    uint length = 32;

    // Generate random data and copy it to a buffer.
    IBuffer buffer = CryptographicBuffer.GenerateRandom(length);

    // Encode the buffer to a hexadecimal string (for display).
    string randomHex = CryptographicBuffer.EncodeToHexString(buffer);

    return randomHex;
}

public uint GenerateRandomNumber()
{
    // Generate a random number.
    uint random = CryptographicBuffer.GenerateRandomNumber();
    return random;
}
```