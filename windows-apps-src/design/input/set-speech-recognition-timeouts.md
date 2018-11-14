---
author: Karl-Bridge-Microsoft
Description: Set how long a speech recognizer ignores silence or unrecognizable sounds (babble) and continues listening for speech input.
title: Festlegen von Timeouts für die Spracherkennung
ms.assetid: 58F446AC-4A56-454D-8125-62A2C4DBFCC8
label: Speech recognition timeouts
template: detail.hbs
keywords: Sprache, Stimme, Spracherkennung, natürliche Sprache, diktieren, Eingabe, Benutzerinteraktion
ms.author: kbridge
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 00923b4448d96943cf00eade46c39c42e87c4f96
ms.sourcegitcommit: 4d88adfaf544a3dab05f4660e2f59bbe60311c00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2018
ms.locfileid: "6471395"
---
# <a name="set-speech-recognition-timeouts"></a><span data-ttu-id="c8aaf-103">Festlegen von Timeouts für die Spracherkennung</span><span class="sxs-lookup"><span data-stu-id="c8aaf-103">Set speech recognition timeouts</span></span>


<span data-ttu-id="c8aaf-104">Legen Sie fest, wie lange eine Spracherkennung Stille oder nicht erkennbare Geräusche (Störgeräusche) ignoriert und weiterhin auf Spracheingabe wartet.</span><span class="sxs-lookup"><span data-stu-id="c8aaf-104">Set how long a speech recognizer ignores silence or unrecognizable sounds (babble) and continues listening for speech input.</span></span>

> <span data-ttu-id="c8aaf-105">**Wichtige APIs**: [**Timeouts**](https://msdn.microsoft.com/library/windows/apps/dn653253), [**SpeechRecognizerTimeouts**](https://msdn.microsoft.com/library/windows/apps/dn653230)</span><span class="sxs-lookup"><span data-stu-id="c8aaf-105">**Important APIs**: [**Timeouts**](https://msdn.microsoft.com/library/windows/apps/dn653253), [**SpeechRecognizerTimeouts**](https://msdn.microsoft.com/library/windows/apps/dn653230)</span></span>

## <a name="set-a-timeout"></a><span data-ttu-id="c8aaf-106">Festlegen eines Timeouts</span><span class="sxs-lookup"><span data-stu-id="c8aaf-106">Set a timeout</span></span>


<span data-ttu-id="c8aaf-107">Hier geben wir verschiedene [**Timeouts**](https://msdn.microsoft.com/library/windows/apps/dn653253)-Werte an:</span><span class="sxs-lookup"><span data-stu-id="c8aaf-107">Here, we specify various [**Timeouts**](https://msdn.microsoft.com/library/windows/apps/dn653253) values:</span></span>

-   <span data-ttu-id="c8aaf-108">InitialSilenceTimeout – Die Zeitspanne, für die ein Spracherkennungsmodul Stille erkennt (vor Generierung etwaiger Erkennungsergebnisse) und davon ausgeht, dass keine Spracheingabe erfolgen wird.</span><span class="sxs-lookup"><span data-stu-id="c8aaf-108">InitialSilenceTimeout - The length of time that a SpeechRecognizer detects silence (before any recognition results have been generated) and assumes speech input is not forthcoming.</span></span>
-   <span data-ttu-id="c8aaf-109">BabbleTimeout – Die Zeitspanne, für die ein Spracherkennungsmodul weiterhin auf erkennbare Geräusche (Störgeräusche) wartet, bevor davon ausgegangen wird, dass die Spracheingabe beendet ist, und der Erkennungsvorgangs beendet wird.</span><span class="sxs-lookup"><span data-stu-id="c8aaf-109">BabbleTimeout - The length of time that a SpeechRecognizer continues to listen to unrecognizable sounds (babble) before it assumes speech input has ended and finalizes the recognition operation.</span></span>
-   <span data-ttu-id="c8aaf-110">EndSilenceTimeout – Die Zeitspanne, für die das Spracherkennungsmodul Stille erkennt (nach Generierung von Erkennungsergebnissen) und davon ausgeht, dass die Spracheingabe beendet ist.</span><span class="sxs-lookup"><span data-stu-id="c8aaf-110">EndSilenceTimeout - The length of time that a SpeechRecognizer detects silence (after recognition results have been generated) and assumes speech input has ended.</span></span>

<span data-ttu-id="c8aaf-111">**Hinweis:** Timeouts können auf einer pro Erkennungsmodul festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="c8aaf-111">**Note**Timeouts can be set on a per-recognizer basis.</span></span>

 

```CSharp
// Set timeout settings.
recognizer.Timeouts.InitialSilenceTimeout = TimeSpan.FromSeconds(6.0);
recognizer.Timeouts.BabbleTimeout = TimeSpan.FromSeconds(4.0);
recognizer.Timeouts.EndSilenceTimeout = TimeSpan.FromSeconds(1.2);
```

## <a name="related-articles"></a><span data-ttu-id="c8aaf-112">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="c8aaf-112">Related articles</span></span>


* <span data-ttu-id="c8aaf-113">[Interaktionen mit der Spracherkennung](speech-interactions.md)
**Beispiele**</span><span class="sxs-lookup"><span data-stu-id="c8aaf-113">[Speech interactions](speech-interactions.md)
**Samples**</span></span>
* [<span data-ttu-id="c8aaf-114">Beispiel zu Spracherkennung und Sprachsynthese</span><span class="sxs-lookup"><span data-stu-id="c8aaf-114">Speech recognition and speech synthesis sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619897)
 

 




