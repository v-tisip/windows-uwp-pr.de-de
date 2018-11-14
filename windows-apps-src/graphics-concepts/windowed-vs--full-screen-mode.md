---
title: Vergleich von Vollbild- und Fenstermodus
description: Direct3D-Anwendungen können jeweils entweder im Fenstermodus oder im Vollbildmodus ausgeführt werden.
ms.assetid: EE8B9F87-822B-4576-A446-CA603E786862
keywords:
- Vergleich von Vollbild- und Fenstermodus
author: michaelfromredmond
ms.author: mithom
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: b2f8c52835801f6cabccad3419bef9ef510522dc
ms.sourcegitcommit: f2c9a050a9137a473f28b613968d5782866142c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2018
ms.locfileid: "6264794"
---
# <a name="span-iddirect3dconceptswindowedvsfull-screenmodespanwindowed-vs-full-screen-mode"></a><span data-ttu-id="fc46d-104"><span id="direct3dconcepts.windowed_vs__full-screen_mode"></span>Vergleich von Vollbild- und Fenstermodus</span><span class="sxs-lookup"><span data-stu-id="fc46d-104"><span id="direct3dconcepts.windowed_vs__full-screen_mode"></span>Windowed vs. full-screen mode</span></span>


<span data-ttu-id="fc46d-105">Direct3D-Anwendungen können jeweils entweder im Fenstermodus oder im Vollbildmodus ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="fc46d-105">Direct3D applications can run in either of two modes: windowed or full-screen.</span></span> <span data-ttu-id="fc46d-106">Im *Fenstermodus* teilt sich die Anwendung die verfügbare Bildschirmfläche auf dem Desktop mit allen anderen ausgeführten Programmen.</span><span class="sxs-lookup"><span data-stu-id="fc46d-106">In *windowed mode*, the application shares the available desktop screen space with all running applications.</span></span> <span data-ttu-id="fc46d-107">Im *Vollbildmodus* bedeckt das Fenster der Anwendung den gesamten Desktop, alle anderen ausgeführten Programme (einschließlich der Entwicklungsumgebung) werden ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="fc46d-107">In *full-screen mode*, the window that the application runs in covers the entire desktop, hiding all running applications (including your development environment).</span></span> <span data-ttu-id="fc46d-108">Normalerweise werden beispielsweise Spiele standardmäßig im Vollbildmodus ausgeführt, damit der Benutzer ganz in das Spiel eintauchen kann, ohne durch die anderen Anwendungen abgelenkt zu werden.</span><span class="sxs-lookup"><span data-stu-id="fc46d-108">Games typically default to full-screen mode to fully immerse the user in the game by hiding all running applications.</span></span>

<span data-ttu-id="fc46d-109">Die Codeunterschiede zwischen Vollbildmodus und Fenstermodus sind äußert gering.</span><span class="sxs-lookup"><span data-stu-id="fc46d-109">Code differences between full-screen mode and windowed mode are very small.</span></span>

<span data-ttu-id="fc46d-110">Da eine Anwendung, die im Vollbildmodus ausgeführt wird, den gesamten Bildschirm ausfüllt, wird für das Debuggen der Anwendung entweder ein zweiter Bildschirm benötigt oder ein Remotedebugger.</span><span class="sxs-lookup"><span data-stu-id="fc46d-110">Because an application running in full-screen mode takes over the screen, debugging the application requires either a separate monitor or the use of a remote debugger.</span></span> <span data-ttu-id="fc46d-111">Ein Vorteil von Anwendungen im Fenstermodus ist, dass Sie den Code in einem Debugger schrittweise ausführen lassen können, ohne einen zweiten Bildschirm oder einen Remotedebugger verwenden zu müssen.</span><span class="sxs-lookup"><span data-stu-id="fc46d-111">One advantage of a windowed-mode application is that you can step through the code in a debugger without multiple monitors or a remote debugger.</span></span>

## <a name="span-idrelated-topicsspanrelated-topics"></a><span data-ttu-id="fc46d-112"><span id="related-topics"></span>Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="fc46d-112"><span id="related-topics"></span>Related topics</span></span>


[<span data-ttu-id="fc46d-113">Geräte</span><span class="sxs-lookup"><span data-stu-id="fc46d-113">Devices</span></span>](devices.md)

 

 




