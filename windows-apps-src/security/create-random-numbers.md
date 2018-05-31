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
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: da60dd982ab378bc71ecbc1f485ca3127cefc9dd
ms.sourcegitcommit: 6618517dc0a4e4100af06e6d27fac133d317e545
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
ms.locfileid: "1689226"
---
# <a name="create-random-numbers"></a><span data-ttu-id="a72fd-104">Erstellen zufälliger Zahlen</span><span class="sxs-lookup"><span data-stu-id="a72fd-104">Create random numbers</span></span>



<span data-ttu-id="a72fd-105">Dieser Beispielcode zeigt, wie Sie zufällige Zahlen oder Puffer für die Verwendung bei der Kryptografie in einer UWP (Universelle Windows-Plattform)-App erstellen.</span><span class="sxs-lookup"><span data-stu-id="a72fd-105">This example code shows how to create a random number or buffer for use in cryptography in an Universal Windows Platform (UWP) app.</span></span>

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