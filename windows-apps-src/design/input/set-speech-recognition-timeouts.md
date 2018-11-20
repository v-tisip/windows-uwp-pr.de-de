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
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7290792"
---
# <a name="set-speech-recognition-timeouts"></a>Festlegen von Timeouts für die Spracherkennung


Legen Sie fest, wie lange eine Spracherkennung Stille oder nicht erkennbare Geräusche (Störgeräusche) ignoriert und weiterhin auf Spracheingabe wartet.

> **Wichtige APIs**: [**Timeouts**](https://msdn.microsoft.com/library/windows/apps/dn653253), [**SpeechRecognizerTimeouts**](https://msdn.microsoft.com/library/windows/apps/dn653230)

## <a name="set-a-timeout"></a>Festlegen eines Timeouts


Hier geben wir verschiedene [**Timeouts**](https://msdn.microsoft.com/library/windows/apps/dn653253)-Werte an:

-   InitialSilenceTimeout – Die Zeitspanne, für die ein Spracherkennungsmodul Stille erkennt (vor Generierung etwaiger Erkennungsergebnisse) und davon ausgeht, dass keine Spracheingabe erfolgen wird.
-   BabbleTimeout – Die Zeitspanne, für die ein Spracherkennungsmodul weiterhin auf erkennbare Geräusche (Störgeräusche) wartet, bevor davon ausgegangen wird, dass die Spracheingabe beendet ist, und der Erkennungsvorgangs beendet wird.
-   EndSilenceTimeout – Die Zeitspanne, für die das Spracherkennungsmodul Stille erkennt (nach Generierung von Erkennungsergebnissen) und davon ausgeht, dass die Spracheingabe beendet ist.

**Hinweis:** Timeouts können auf einer pro Erkennungsmodul festgelegt werden.

 

```CSharp
// Set timeout settings.
recognizer.Timeouts.InitialSilenceTimeout = TimeSpan.FromSeconds(6.0);
recognizer.Timeouts.BabbleTimeout = TimeSpan.FromSeconds(4.0);
recognizer.Timeouts.EndSilenceTimeout = TimeSpan.FromSeconds(1.2);
```

## <a name="related-articles"></a>Verwandte Artikel


* [Interaktionen mit der Spracherkennung](speech-interactions.md)
**Beispiele**
* [Beispiel zu Spracherkennung und Sprachsynthese](http://go.microsoft.com/fwlink/p/?LinkID=619897)
 

 




