---
author: Jwmsft
Description: Use a label to indicate to the user what they should enter into an adjacent control. You can also label a group of related controls, or display instructional text near a group of related controls.
title: Label
ms.assetid: CFACCCD4-749F-43FB-947E-2591AE673804
label: Labels
template: detail.hbs
ms.author: jimwalk
ms.date: 05/19/2017
ms.topic: article
keywords: Windows 10, UWP
pm-contact: miguelrb
design-contact: ksulliv
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: c17b2a539a01572bed984b86f72f5439896fac87
ms.sourcegitcommit: 086001cffaf436e6e4324761d59bcc5e598c15ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2018
ms.locfileid: "5704451"
---
# <a name="labels"></a>Label

 

Ein Label ist der Name bzw. Titel eines Steuerelements oder einer Gruppe verwandter Steuerelemente.

> **Wichtige APIs**: Header-Eigenschaft, [TextBlock-Klasse](https://msdn.microsoft.com/library/windows/apps/br209652)

In XAML verfügen zahlreiche Steuerelemente über eine integrierte Header-Eigenschaft, die Sie zum Anzeigen der Beschriftung verwenden. Für Steuerelemente ohne Header-Eigenschaft oder zum Beschriften von Steuerelementgruppen können Sie stattdessen ein [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652)-Element verwenden.

![Bildschirmfoto mit einem standardmäßigen Beschriftungssteuerelement](images/label-standard.png)

## <a name="recommendations"></a>Empfehlungen


-   Verwenden Sie eine Beschriftung, um den Benutzer darauf hinzuweisen, was er in ein benachbartes Steuerelement eingeben soll. Sie können auch eine Gruppe verwandter Steuerelemente beschriften oder in der Nähe davon Anweisungstexte anzeigen.
-   Wenn Sie Steuerelemente beschriften, formulieren Sie die Beschriftung als Substantiv oder als präzisen substantivierten Ausdruck und nicht als Satz oder Anweisungstext. Vermeiden Sie die Verwendung von Doppelpunkten oder anderen Satzzeichen.
-   Wenn Sie in einer Bezeichnung Anweisungstext nutzen, können Sie bei der Länge von Textzeichenfolgen großzügiger sein und auch Satzzeichen verwenden.


## <a name="get-the-sample-code"></a>Beispielcode herunterladen
* [Beispiel für XAML-UI-Grundlagen](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/XamlUIBasics)

## <a name="related-topics"></a>Verwandte Themen
* [Textsteuerelemente](text-controls.md)
* [TextBox.Header-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/dn252861)
* [Eigenschaft „PasswordBox.Header“](https://msdn.microsoft.com/library/windows/apps/dn299051)
* [Eigenschaft „ToggleSwitch.Header“](https://msdn.microsoft.com/library/windows/apps/br209713)
* [Eigenschaft „DatePicker.Header“](https://msdn.microsoft.com/library/windows/apps/dn279460)
* [Eigenschaft „TimePicker.Header“](https://msdn.microsoft.com/library/windows/apps/dn299286)
* [Eigenschaft „Slider.Header“](https://msdn.microsoft.com/library/windows/apps/dn252829)
* [Eigenschaft „ComboBox.Header“](https://msdn.microsoft.com/library/windows/apps/dn279416)
* [Eigenschaft „RichEditBox.Header“](https://msdn.microsoft.com/library/windows/apps/dn252726)
* [Klasse „TextBlock“](https://msdn.microsoft.com/library/windows/apps/br209652)

 

 




