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
ms.sourcegitcommit: f5cf806a595969ecbb018c3f7eea86c7a34940f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "3820714"
---
# <a name="create-random-numbers"></a><span data-ttu-id="7e480-104">Erstellen zufälliger Zahlen</span><span class="sxs-lookup"><span data-stu-id="7e480-104">Create random numbers</span></span>



<span data-ttu-id="7e480-105">Dieser Beispielcode zeigt, wie Sie zufällige Zahlen oder Puffer für die Verwendung bei der Kryptografie in einer UWP (Universelle Windows-Plattform)-App erstellen.</span><span class="sxs-lookup"><span data-stu-id="7e480-105">This example code shows how to create a random number or buffer for use in cryptography in an Universal Windows Platform (UWP) app.</span></span>

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