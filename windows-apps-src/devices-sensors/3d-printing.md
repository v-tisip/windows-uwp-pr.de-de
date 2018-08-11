---
author: PatrickFarley
ms.assetid: 551d4e70-312d-4b40-8d3e-336ce934e0ad
title: 3D-Druck
description: Dieser Abschnitt beschreibt die Verwendung der 3D-Druckfunktionen in Ihrer Universellen Windows-App.
ms.author: pafarley
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: af636e445d2cad70922b8f846140e0886cf7ef28
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: MT
ms.contentlocale: de-DE
ms.locfileid: "233715"
---
# <a name="3d-printing"></a><span data-ttu-id="6e517-104">3D-Druck</span><span class="sxs-lookup"><span data-stu-id="6e517-104">3D Printing</span></span>

<span data-ttu-id="6e517-105">\[ Aktualisiert für UWP-Apps unter Windows 10.</span><span class="sxs-lookup"><span data-stu-id="6e517-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="6e517-106">Artikel zu Windows 8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \].</span><span class="sxs-lookup"><span data-stu-id="6e517-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="6e517-107">In diesem Abschnitt wird beschrieben, wie Sie die [3D-Druck-API](https://msdn.microsoft.com/library/windows/apps/windows.graphics.printing3d.aspx) zum Hinzufügen von Funktionen für den 3D-Druck der universellen Windows-App verwenden.</span><span class="sxs-lookup"><span data-stu-id="6e517-107">This section describes how to utilize the [3D print API](https://msdn.microsoft.com/library/windows/apps/windows.graphics.printing3d.aspx) to add 3D printing functionality to your Universal Windows app.</span></span>  

<!-- ![the 3D printing from Unity sample uses Windows 3D print APIs to facilitate the printing of a textured model asset from Unity software](images/unity-app-screenshot-002.png) -->

<span data-ttu-id="6e517-108">Weitere Informationen zum 3D-Druck mit Windows10, z.B. Ressourcen für Hardwarepartner, Community-Diskussionsforen und allgemeine Hinweise zu Funktionen für den 3D-Druck finden Sie auf der Hardware Dev Center-Website unter [3D-Druck mit Windows10](https://developer.microsoft.com/windows/hardware/3d-print-support-windows-10).</span><span class="sxs-lookup"><span data-stu-id="6e517-108">For more information on 3D printing with Windows 10, including resources for hardware partners, community discussion forums, and general info on 3D print capabilities, see the [3D printing with Windows 10](https://developer.microsoft.com/windows/hardware/3d-print-support-windows-10) site on the Hardware Dev Center.</span></span>

| <span data-ttu-id="6e517-109">Thema</span><span class="sxs-lookup"><span data-stu-id="6e517-109">Topic</span></span> | <span data-ttu-id="6e517-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6e517-110">Description</span></span> |
|-------|-------------|
| [<span data-ttu-id="6e517-111">3D-Druck aus der App</span><span class="sxs-lookup"><span data-stu-id="6e517-111">3D print from your app</span></span>](3d-print-from-app.md) | <span data-ttu-id="6e517-112">Erfahren Sie, wie Sie Ihrer universellen Windows-App 3D-Druckfunktionen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="6e517-112">Learn how to add 3D printing functionality to your Universal Windows app.</span></span> <span data-ttu-id="6e517-113">In diesem Thema wird erläutert, wie das 3D-Drucken-Dialogfeld aufgerufen wird, nachdem Sie sich vergewissert haben, dass das 3D-Modell gedruckt werden kann und im richtigen Format vorliegt.</span><span class="sxs-lookup"><span data-stu-id="6e517-113">This topic covers how to launch the 3D print dialog after ensuring your 3D model is printable and in the correct format.</span></span> |
| [<span data-ttu-id="6e517-114">Generieren eines 3MF-Pakets</span><span class="sxs-lookup"><span data-stu-id="6e517-114">Generate a 3MF package</span></span>](generate-3mf.md) | <span data-ttu-id="6e517-115">Beschreibt die Struktur des 3D Manufacturing Format-Dateityps und dessen Erstellung und Bearbeitung mit der Windows.Graphics.Printing3D-API.</span><span class="sxs-lookup"><span data-stu-id="6e517-115">Describes the structure of the 3D Manufacturing Format file type and how it can be created and manipulated with the Windows.Graphics.Printing3D API.</span></span> |

## <a name="related-topics"></a><span data-ttu-id="6e517-116">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="6e517-116">Related topics</span></span>

* [<span data-ttu-id="6e517-117">3D-Druck mit Windows10 (Hardware Dev Center)</span><span class="sxs-lookup"><span data-stu-id="6e517-117">3D printing with Windows 10 (Hardware Dev Center)</span></span>](https://developer.microsoft.com/windows/hardware/3d-print-support-windows-10)
* [<span data-ttu-id="6e517-118">UWP 3D-Druckbeispiel</span><span class="sxs-lookup"><span data-stu-id="6e517-118">UWP 3D print sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/3DPrinting)
* [<span data-ttu-id="6e517-119">UWP 3D-Druck mit Unity-Beispiel</span><span class="sxs-lookup"><span data-stu-id="6e517-119">UWP 3D printing from Unity sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/3DPrintingFromUnity)

 
