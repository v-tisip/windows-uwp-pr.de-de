---
title: Umwandlung zwischen Zeichenfolgen und binären Daten
description: Dieser Beispielcode zeigt, wie Sie in einer App für die Universelle Windows-Plattform (UWP) eine Konvertierung zwischen Zeichenfolgen und binären Daten durchführen.
ms.assetid: AED4C74F-E63B-4980-BB4D-28ACCC1AB58B
author: msatranjr
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 84ba6fab0ea58a5598fb60ce99c98e71825705f8
ms.sourcegitcommit: 6618517dc0a4e4100af06e6d27fac133d317e545
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
ms.locfileid: "1689096"
---
# <a name="convert-between-strings-and-binary-data"></a><span data-ttu-id="562d7-104">Umwandlung zwischen Zeichenfolgen und binären Daten</span><span class="sxs-lookup"><span data-stu-id="562d7-104">Convert between strings and binary data</span></span>



<span data-ttu-id="562d7-105">Dieser Beispielcode zeigt, wie Sie zwischen Zeichenfolgen und binären Daten in einer UWP-App (Universelle Windows-Plattform) konvertieren können.</span><span class="sxs-lookup"><span data-stu-id="562d7-105">This example code shows how to convert between strings and binary data in an Universal Windows Platform (UWP) app.</span></span>

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