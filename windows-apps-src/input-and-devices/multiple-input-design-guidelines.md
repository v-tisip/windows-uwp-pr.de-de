---
author: Karl-Bridge-Microsoft
Description: Ebenso wie Menschen untereinander mit einer Mischung aus Sprache und Gesten kommunizieren, kann sich auch bei der Interaktion mit einer App die Verwendung mehrerer Eingabearten und -modi als hilfreich erweisen.
title: "Entwurfsrichtlinien für mehrere Eingaben"
ms.assetid: 03EB5388-080F-467C-B272-C92BE00F2C69
label: Multiple inputs
template: detail.hbs
ms.author: kbridge
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: e3da62c83012d2a854e53c0e7082ecacec8df766
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="multiple-inputs"></a>Mehrere Eingaben
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

Ebenso wie Menschen untereinander mit einer Mischung aus Sprache und Gesten kommunizieren, kann sich auch bei der Interaktion mit einer App die Verwendung mehrerer Eingabearten und -modi als hilfreich erweisen.


Um eine möglichst große Zahl von Benutzern und Geräten zu unterstützen, empfehlen wir, Ihre App für die Kompatibilität mit so vielen Eingabearten wie möglich zu entwickeln(Gesten, Spracherkennung, Toucheingabe, Touchpad, Maus und Tastatur). Dadurch werden Flexibilität, Benutzerfreundlichkeit und Barrierefreiheit optimiert.

Um zu beginnen, sollten Sie die verschiedenen Szenarien berücksichtigen, in denen Ihre App Eingaben verarbeitet. Versuchen Sie, in der gesamten App konsistent zu sein, und denken Sie daran, dass die Steuerelemente der Plattform integrierte Unterstützung für mehrere Eingabetypen bereitstellen.

-   Können Benutzer über mehrere Eingabegeräte mit der Anwendung interagieren?
-   Werden alle Eingabemethoden jederzeit unterstützt? Mit bestimmten Steuerelementen? Zu bestimmten Zeiten oder Umständen?
-   Hat eine Eingabemethode Priorität?

## <a name="single-or-exclusive-mode-interactions"></a>Einzel- (oder Exklusiv)-Modusinteraktionen


Mit Einzelmodusinteraktionen werden mehrere Eingabetypen unterstützt, es kann jedoch nur einer pro Aktion verwendet werden. Z. B. Spracherkennung für Befehle und Gesten für die Navigation; oder die Texteingabe per Touch oder Gesten, je nach Näherung.

## <a name="multimodal-interactions"></a>Kombinierte Interaktionen


Mit kombinierten Interaktionen werden nacheinander mehrere Eingabemethoden verwendet, um eine einzelne Aktion auszuführen.

Spracherkennung + Geste  
Der Benutzer zeigt auf ein Produkt, und sagt dann „Dem Einkaufswagen hinzufügen“.

Spracherkennung + Toucheingabe  
Der Benutzer wählt ein Foto, indem er dieses gedrückt hält, und sagt dann „Foto senden“.



