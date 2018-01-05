---
title: "Umwandlung zwischen Zeichenfolgen und binären Daten"
description: "Dieser Beispielcode zeigt, wie Sie in einer App für die Universelle Windows-Plattform (UWP) eine Konvertierung zwischen Zeichenfolgen und binären Daten durchführen."
ms.assetid: AED4C74F-E63B-4980-BB4D-28ACCC1AB58B
author: awkoren
ms.author: alkoren
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 3317c1c05c8a9a51f0a4d3c363db9c92809c1919
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: HT
ms.contentlocale: de-DE
---
# <a name="convert-between-strings-and-binary-data"></a><span data-ttu-id="06807-104">Umwandlung zwischen Zeichenfolgen und binären Daten</span><span class="sxs-lookup"><span data-stu-id="06807-104">Convert between strings and binary data</span></span>


<span data-ttu-id="06807-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="06807-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="06807-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="06807-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="06807-107">Dieser Beispielcode zeigt, wie Sie in einer UWP-App (Universelle Windows-Plattform) zwischen Zeichenfolgen und binären Daten konvertieren können.</span><span class="sxs-lookup"><span data-stu-id="06807-107">This example code shows how to convert between strings and binary data in an Universal Windows Platform (UWP) app.</span></span>

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