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
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "5572509"
---
# <a name="convert-between-strings-and-binary-data"></a>Umwandlung zwischen Zeichenfolgen und binären Daten



Dieser Beispielcode zeigt, wie Sie zwischen Zeichenfolgen und binären Daten in einer UWP-App (Universelle Windows-Plattform) konvertieren können.

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