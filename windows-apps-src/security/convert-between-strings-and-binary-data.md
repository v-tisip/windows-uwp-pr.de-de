---
title: Umwandlung zwischen Zeichenfolgen und binären Daten
description: Dieser Beispielcode zeigt, wie Sie zwischen Zeichenfolgen und binären Daten in einer UWP-App (Universelle Windows-Plattform) konvertieren können.
ms.assetid: AED4C74F-E63B-4980-BB4D-28ACCC1AB58B
author: msatranjr
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, Uwp, Sicherheit
ms.localizationpriority: medium
ms.openlocfilehash: 030fe81685fbc6caea0b9847b366384476f6298f
ms.sourcegitcommit: 38f06f1714334273d865935d9afb80efffe97a17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6200978"
---
# <a name="convert-between-strings-and-binary-data"></a><span data-ttu-id="55646-104">Umwandlung zwischen Zeichenfolgen und binären Daten</span><span class="sxs-lookup"><span data-stu-id="55646-104">Convert between strings and binary data</span></span>



<span data-ttu-id="55646-105">Dieser Beispielcode zeigt, wie Sie zwischen Zeichenfolgen und binären Daten in einer UWP-App (Universelle Windows-Plattform) konvertieren können.</span><span class="sxs-lookup"><span data-stu-id="55646-105">This example code shows how to convert between strings and binary data in an Universal Windows Platform (UWP) app.</span></span>

```cs
public void ConvertData()
{
    // Create a string to convert.
    String strIn = "Input String";

    // Convert the string to UTF16BE binary data.
    IBuffer buffUTF16BE = CryptographicBuffer.ConvertStringToBinary(strIn, BinaryStringEncoding.Utf16BE);

    // Convert the string to UTF16LE binary data.
    IBuffer buffUTF16LE = CryptographicBuffer.ConvertStringToBinary(strIn, BinaryStringEncoding.Utf16LE);

    // Convert the string to UTF8 binary data.
    IBuffer buffUTF8 = CryptographicBuffer.ConvertStringToBinary(strIn, BinaryStringEncoding.Utf8);
}
```