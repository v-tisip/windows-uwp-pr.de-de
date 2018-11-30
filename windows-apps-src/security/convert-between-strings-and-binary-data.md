---
title: Umwandlung zwischen Zeichenfolgen und binären Daten
description: Dieser Beispielcode zeigt, wie Sie zwischen Zeichenfolgen und binären Daten in einer UWP-App (Universelle Windows-Plattform) konvertieren können.
ms.assetid: AED4C74F-E63B-4980-BB4D-28ACCC1AB58B
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, Uwp, Sicherheit
ms.localizationpriority: medium
ms.openlocfilehash: ae2de8f009da1873c9aebf4f60ef315b36c7d744
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8215902"
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