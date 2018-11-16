---
author: PatrickFarley
ms.assetid: 70667353-152B-4B18-92C1-0178298052D4
title: Epson ESC/POS mit Formatierung
description: Erfahren Sie, wie Sie die ESC/POS-Befehlssprache zum Formatieren von Text, z. B. in Fett und mit doppelter Größe, für Ihren Point of Service-Drucker verwenden.
ms.author: pafarley
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 3ecc1a61b7db339c7c0c46168255d32bfbc241a1
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6976831"
---
# <a name="epson-escpos-with-formatting"></a><span data-ttu-id="9818d-104">Epson ESC/POS mit Formatierung</span><span class="sxs-lookup"><span data-stu-id="9818d-104">Epson ESC/POS with formatting</span></span>


**<span data-ttu-id="9818d-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="9818d-105">Important APIs</span></span>**

-   [**<span data-ttu-id="9818d-106">PointofService-Drucker</span><span class="sxs-lookup"><span data-stu-id="9818d-106">PointofService Printer</span></span>**](https://msdn.microsoft.com/library/windows/apps/Mt426652)
-   [**<span data-ttu-id="9818d-107">Windows.Devices.PointOfService</span><span class="sxs-lookup"><span data-stu-id="9818d-107">Windows.Devices.PointOfService</span></span>**](https://msdn.microsoft.com/library/windows/apps/Dn298071)

<span data-ttu-id="9818d-108">Erfahren Sie, wie Sie die ESC/POS-Befehlssprache zum Formatieren von Text, z.B. in Fett und mit doppelter Größe, für Ihren Point of Service-Drucker verwenden.</span><span class="sxs-lookup"><span data-stu-id="9818d-108">Learn how to use the ESC/POS command language to format text, such as bold and double size characters, for your Point of Service printer.</span></span>

## <a name="escpos-usage"></a><span data-ttu-id="9818d-109">ESC/POS-Verwendung</span><span class="sxs-lookup"><span data-stu-id="9818d-109">ESC/POS usage</span></span>

<span data-ttu-id="9818d-110">Windows Point of Service ermöglicht die Verwendung einer Vielzahl von Druckern, z.B. mehrerer Drucker der EpsonTM-Reihe. (Eine vollständige Liste der unterstützten Drucker finden Sie auf der Seite [PointofService-Drucker](https://msdn.microsoft.com/library/windows/apps/Mt426652).)</span><span class="sxs-lookup"><span data-stu-id="9818d-110">Windows Point of Service provides use of a variety of printers, including several Epson TM series printers (for a full list of supported printers, see the [PointofService Printer](https://msdn.microsoft.com/library/windows/apps/Mt426652) page).</span></span> <span data-ttu-id="9818d-111">Windows unterstützt das Drucken über die ESC/POS-Druckersteuerungssprache, die über effiziente und funktionale Befehle für die Kommunikation mit dem Drucker verfügt.</span><span class="sxs-lookup"><span data-stu-id="9818d-111">Windows supports printing through the ESC/POS printer control language, which provides efficient and functional commands for communicating with your printer.</span></span>

<span data-ttu-id="9818d-112">ESC/POS ist ein von Epson erstelltes Befehlssystem, das für viele POS-Druckersysteme verwendet wird und mit dem inkompatible Befehlssätze vermieden werden sollen, indem für eine universelle Anwendbarkeit gesorgt wird.</span><span class="sxs-lookup"><span data-stu-id="9818d-112">ESC/POS is a command system created by Epson used across a wide range of POS printer systems, aimed at avoiding incompatible command sets by providing universal applicability.</span></span> <span data-ttu-id="9818d-113">Die meisten modernen Drucker unterstützen ESC/POS.</span><span class="sxs-lookup"><span data-stu-id="9818d-113">Most modern printers support ESC/POS.</span></span>

<span data-ttu-id="9818d-114">Alle Befehle beginnen mit dem ESC-Zeichen (ASCII27, HEX1B) oder GS (ASCII29, HEX1D), gefolgt von einem weiteren Zeichen, das für den Befehl steht.</span><span class="sxs-lookup"><span data-stu-id="9818d-114">All commands start with the ESC character (ASCII 27, HEX 1B) or GS (ASCII 29, HEX 1D), followed by another character that specifies the command.</span></span> <span data-ttu-id="9818d-115">Normaler Text wird – getrennt durch Zeilenumbrüche – einfach an den Drucker gesendet.</span><span class="sxs-lookup"><span data-stu-id="9818d-115">Normal text is simply sent to the printer, separated by line breaks.</span></span>

<span data-ttu-id="9818d-116">Die [**Windows PointOfService API**](https://msdn.microsoft.com/library/windows/apps/Dn298071) stellt einen Großteil der Funktionalität für Sie über die Methoden **Print()** oder **PrintLine()** bereit.</span><span class="sxs-lookup"><span data-stu-id="9818d-116">The [**Windows PointOfService API**](https://msdn.microsoft.com/library/windows/apps/Dn298071) provides much of that functionality for you via the **Print()** or **PrintLine()** methods.</span></span> <span data-ttu-id="9818d-117">Um bestimmte Formatierungen zu erzielen oder spezielle Befehle zu senden, müssen Sie jedoch ESC/POS-Befehle senden, die wie eine Zeichenfolge aufgebaut sind und an den Drucker gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="9818d-117">However, to get certain formatting or to send specific commands, you must use ESC/POS commands, built as a string and sent to the printer.</span></span>

## <a name="example-using-bold-and-double-size-characters"></a><span data-ttu-id="9818d-118">Beispiel für die Verwendung von fetten Zeichen und Zeichen mit doppelter Größe</span><span class="sxs-lookup"><span data-stu-id="9818d-118">Example using bold and double size characters</span></span>

<span data-ttu-id="9818d-119">Im folgenden Beispiel wird die Verwendung von ESC/POS-Befehlen zum Drucken von fetten Zeichen und Zeichen mit doppelter Größe veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="9818d-119">The example below shows how to use ESC/POS commands to print in bold and double sized characters.</span></span> <span data-ttu-id="9818d-120">Beachten Sie, dass jeder Befehl wie eine Zeichenfolge aufgebaut ist und dann in die printJob-Aufrufe eingefügt wird.</span><span class="sxs-lookup"><span data-stu-id="9818d-120">Note that each command is built as a string, then inserted into the printJob calls.</span></span>

```csharp
// … prior plumbing code removed for brevity
// this code assumed you've already created a receipt print job (printJob)
// and also that you've already checked the PosPrinter Capabilities to
// verify that the printer supports Bold and DoubleHighDoubleWide print modes

const string ESC = "\u001B";
const string GS = "\u001D";
const string InitializePrinter = ESC + "@";
const string BoldOn = ESC + "E" + "\u0001";
const string BoldOff = ESC + "E" + "\0";
const string DoubleOn = GS + "!" + "\u0011";  // 2x sized text (double-high + double-wide)
const string DoubleOff = GS + "!" + "\0";

printJob.Print(InitializePrinter);
printJob.PrintLine("Here is some normal text.");
printJob.PrintLine(BoldOn + "Here is some bold text." + BoldOff);
printJob.PrintLine(DoubleOn + "Here is some large text." + DoubleOff);

printJob.ExecuteAsync();
```

<span data-ttu-id="9818d-121">Weitere Informationen zu ESC/POS, darunter zu den verfügbaren Befehlen, finden Sie unter [Epson ESC/POS – FAQ](http://content.epson.de/fileadmin/content/files/RSD/downloads/escpos.pdf).</span><span class="sxs-lookup"><span data-stu-id="9818d-121">For more information on ESC/POS, including available commands, check out the [Epson ESC/POS FAQ](http://content.epson.de/fileadmin/content/files/RSD/downloads/escpos.pdf).</span></span> <span data-ttu-id="9818d-122">Ausführliche Informationen zu [**Windows.Devices.PointOfService**](https://msdn.microsoft.com/library/windows/apps/Dn298071) sowie zu allen verfügbaren Funktionen finden Sie auf der MSDN-Website unter [PointofService Printer](https://msdn.microsoft.com/library/windows/apps/Mt426652).</span><span class="sxs-lookup"><span data-stu-id="9818d-122">For details on [**Windows.Devices.PointOfService**](https://msdn.microsoft.com/library/windows/apps/Dn298071) and all the available functionality, see [PointofService Printer](https://msdn.microsoft.com/library/windows/apps/Mt426652) on MSDN.</span></span>
