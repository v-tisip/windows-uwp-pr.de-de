---
Description: Set how long a speech recognizer ignores silence or unrecognizable sounds (babble) and continues listening for speech input.
title: Festlegen von Timeouts für die Spracherkennung
ms.assetid: 58F446AC-4A56-454D-8125-62A2C4DBFCC8
label: Speech recognition timeouts
template: detail.hbs
keywords: Sprache, Stimme, Spracherkennung, natürliche Sprache, diktieren, Eingabe, Benutzerinteraktion
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 679c2632fd5793ae083b2a79e29de3a3e9da04cf
ms.sourcegitcommit: bf600a1fb5f7799961914f638061986d55f6ab12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/04/2019
ms.locfileid: "9044923"
---
# <a name="set-speech-recognition-timeouts"></a><span data-ttu-id="41a29-103">Festlegen von Timeouts für die Spracherkennung</span><span class="sxs-lookup"><span data-stu-id="41a29-103">Set speech recognition timeouts</span></span>


<span data-ttu-id="41a29-104">Legen Sie fest, wie lange eine Spracherkennung Stille oder nicht erkennbare Geräusche (Störgeräusche) ignoriert und weiterhin auf Spracheingabe wartet.</span><span class="sxs-lookup"><span data-stu-id="41a29-104">Set how long a speech recognizer ignores silence or unrecognizable sounds (babble) and continues listening for speech input.</span></span>

> <span data-ttu-id="41a29-105">**Wichtige APIs**: [**Timeouts**](https://msdn.microsoft.com/library/windows/apps/dn653253), [**SpeechRecognizerTimeouts**](https://msdn.microsoft.com/library/windows/apps/dn653230)</span><span class="sxs-lookup"><span data-stu-id="41a29-105">**Important APIs**: [**Timeouts**](https://msdn.microsoft.com/library/windows/apps/dn653253), [**SpeechRecognizerTimeouts**](https://msdn.microsoft.com/library/windows/apps/dn653230)</span></span>

## <a name="set-a-timeout"></a><span data-ttu-id="41a29-106">Festlegen eines Timeouts</span><span class="sxs-lookup"><span data-stu-id="41a29-106">Set a timeout</span></span>


<span data-ttu-id="41a29-107">Hier geben wir verschiedene [**Timeouts**](https://msdn.microsoft.com/library/windows/apps/dn653253)-Werte an:</span><span class="sxs-lookup"><span data-stu-id="41a29-107">Here, we specify various [**Timeouts**](https://msdn.microsoft.com/library/windows/apps/dn653253) values:</span></span>

-   <span data-ttu-id="41a29-108">InitialSilenceTimeout – Die Zeitspanne, für die ein Spracherkennungsmodul Stille erkennt (vor Generierung etwaiger Erkennungsergebnisse) und davon ausgeht, dass keine Spracheingabe erfolgen wird.</span><span class="sxs-lookup"><span data-stu-id="41a29-108">InitialSilenceTimeout - The length of time that a SpeechRecognizer detects silence (before any recognition results have been generated) and assumes speech input is not forthcoming.</span></span>
-   <span data-ttu-id="41a29-109">BabbleTimeout – Die Zeitspanne, für die ein Spracherkennungsmodul weiterhin auf erkennbare Geräusche (Störgeräusche) wartet, bevor davon ausgegangen wird, dass die Spracheingabe beendet ist, und der Erkennungsvorgangs beendet wird.</span><span class="sxs-lookup"><span data-stu-id="41a29-109">BabbleTimeout - The length of time that a SpeechRecognizer continues to listen to unrecognizable sounds (babble) before it assumes speech input has ended and finalizes the recognition operation.</span></span>
-   <span data-ttu-id="41a29-110">EndSilenceTimeout – Die Zeitspanne, für die das Spracherkennungsmodul Stille erkennt (nach Generierung von Erkennungsergebnissen) und davon ausgeht, dass die Spracheingabe beendet ist.</span><span class="sxs-lookup"><span data-stu-id="41a29-110">EndSilenceTimeout - The length of time that a SpeechRecognizer detects silence (after recognition results have been generated) and assumes speech input has ended.</span></span>

<span data-ttu-id="41a29-111">**Hinweis:**: Timeouts können auf einer pro Erkennungsmodul festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="41a29-111">**Note**Timeouts can be set on a per-recognizer basis.</span></span>

 

```CSharp
// Set timeout settings.
recognizer.Timeouts.InitialSilenceTimeout = TimeSpan.FromSeconds(6.0);
recognizer.Timeouts.BabbleTimeout = TimeSpan.FromSeconds(4.0);
recognizer.Timeouts.EndSilenceTimeout = TimeSpan.FromSeconds(1.2);
```

## <a name="related-articles"></a><span data-ttu-id="41a29-112">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="41a29-112">Related articles</span></span>


* <span data-ttu-id="41a29-113">[Interaktionen mit der Spracherkennung](speech-interactions.md)
**Beispiele**</span><span class="sxs-lookup"><span data-stu-id="41a29-113">[Speech interactions](speech-interactions.md)
**Samples**</span></span>
* [<span data-ttu-id="41a29-114">Beispiel zu Spracherkennung und Sprachsynthese</span><span class="sxs-lookup"><span data-stu-id="41a29-114">Speech recognition and speech synthesis sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=619897)
 

 




