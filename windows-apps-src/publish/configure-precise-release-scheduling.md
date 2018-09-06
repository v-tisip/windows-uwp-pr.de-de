---
author: jnHs
Description: You can set the precise date and time that your app should become available in the Store, giving you greater flexibility and the ability to customize dates for different markets.
title: Konfigurieren des genauen Veröffentlichungszeitplans
ms.author: wdg-dev-content
ms.date: 05/02/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Zeitplan, Veröffentlichung, Datum, starten
ms.localizationpriority: medium
ms.openlocfilehash: 84466f907bad7e38506e1bf81b89eb631675093c
ms.sourcegitcommit: 914b38559852aaefe7e9468f6f53a7465bf36e30
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "3402162"
---
# <a name="configure-precise-release-scheduling"></a>Konfigurieren des genauen Veröffentlichungszeitplans

Im Abschnitt **Zeitplan** auf der Seite [Preise und Verfügbarkeit](set-app-pricing-and-availability.md) können Sie das genaue Datum und die genaue Uhrzeit festlegen, an dem bzw. zu der Ihre App im Store verfügbar gemacht werden soll, was Ihnen mehr Flexibilität und das Anpassen des Datums für verschiedene Märkte ermöglicht.

> [!NOTE]
> Obwohl dieses Thema auf Apps verweist, verwendet der Veröffentlichungszeitplan für die Add-On-Übermittlungen das gleiche Verfahren.

Sie können darüber hinaus ein Datum festlegen, ab dem das Produkt nicht mehr im Store verfügbar sein soll. Beachten Sie, dass dies bedeutet, dass das Produkt nicht mehr im Store durch Suchen oder beim Surfen gefunden werden kann. Aber alle Kunden mit einem direkten Link können den Store-Eintrag des Produkts anzeigen. Sie können es nur herunterladen, wenn sie das Produkt bereits besitzen oder einen [Werbecode](generate-promotional-codes.md) haben und ein Windows10-Gerät verwenden.

Standardmäßig (es sei denn, Sie haben eine der Optionen für **Make this app available but not discoverable in the Store** im Abschnitt [Sichtbarkeit](choose-visibility-options.md#discoverability) ausgewählt) wird Ihre App für Kunden zur Verfügung gestellt, sobald sie die Zertifizierung bestanden und den Veröffentlichungsprozess abgeschlossen hat. Um ein anderes Datum auszuwählen, wählen Sie **Optionen anzeigen**, um diesen Abschnittzu erweitern.

Beachten Sie, dass Sie Datumsangaben im Abschnitt **Zeitplan** nicht konfigurieren können, wenn Sie eine der Optionen für **Make this app available but not discoverable in the Store** im Abschnitt [Sichtbarkeit](choose-visibility-options.md#discoverability) ausgewählt haben, da ihre App nicht für Kunden veröffentlicht wird. Daher muss kein Veröffentlichungsdatum konfiguriert werden.

> [!IMPORTANT]
> Das im Abschnitt "Zeitplan" angegebene Datum gilt nur für Kunden unter Windows10.
>
>Wenn Ihre App frühere Betriebssystemversionen unterstützt, sehen Kunden unter diesen Betriebssystemversionen den Eintrag Ihrer App, sobald sie die Zertifizierung bestanden und den Veröffentlichungsprozess abgeschlossen hat, auch wenn Sie ein späteres Veröffentlichungsdatum ausgewählt haben. Ein für **Stop acquisition** ausgewähltes Datum gilt nicht für diese Kunden. Sie können die App weiterhin erwerben (sofern Sie nicht ein Update mit einer neuen Auswahl im Abschnitt [Sichtbarkeit](choose-visibility-options.md#discoverability) übermitteln, oder wenn Sie **Make app unavailable** auf der Seite **App-Übersicht** auswählen).


## <a name="base-schedule"></a>Basiszeitplan

Die für den Basiszeitplan getroffene Auswahl gilt für alle Märkte, in denen Ihre App verfügbar ist, es sei denn, Sie fügen später ein Datum für bestimmte Märkte (oder Marktgruppen) durch die Auswahl von [Customize for specific markets](#customize-the-schedule-for-specific-markets) hinzu.

Sie sehen hier zwei Optionen: **Release** und **Stop acquisition**. 

## <a name="release"></a>Release

In der Dropdownliste **Release** können Sie festlegen, wann Ihre App im Store verfügbar sein soll. Dies bedeutet, dass die App im Store durch Suchen oder beim Surfen gefunden werden kann und dass Kunden den Store-Eintrag anzeigen und die App erwerben können.

>[!NOTE]
> Nachdem Ihre App veröffentlicht und im Store verfügbar gemacht wurde, können Sie kein Datum für **Release** mehr auswählen (da die App bereits veröffentlicht worden ist).

Hier sind die Optionen, die Sie für den **Releasezeitplan** eines Produkts konfigurieren können:
- **so bald wie möglich**: Das Produkt wird sofort nach der Zertifizierung und Veröffentlichung verfügbar gemacht. Dies ist die Standardoption.
- **at**: Das Produkt wird am ausgewählten Datum und zur ausgewählten Uhrzeit verfügbar gemacht. Ihnen stehen zwei zusätzliche Optionen zur Auswahl:
   - **UTC**: Die ausgewählte Zeit ist UTC-Zeit (Universal Coordinated Time, Koordinierte Weltzeit), damit die App überall zur gleichen Zeit verfügbar gemacht wird.
   - **Lokal**: Die ausgewählte Zeit ist die in jeder Zeitzone für einen Markt verwendete Uhrzeit. (Beachten Sie, dass für Märkte, die mehr als eine Zeitzone umfassen, nur eine Zeitzone in diesem Markt verwendet wird. Für die USA wird die Eastern Time verwendet.)
- **nicht geplant**: Die App wird nicht im Store verfügbar sein. Wenn Sie diese Option auswählen, können Sie die App im Store später zur Verfügung stellen, indem Sie eine neue Übermittlung erstellen und eine der anderen Optionen auswählen.


## <a name="stop-acquisition"></a>Beenden des Erwerbs

Im Dropdownmenü **Stop acquisition** können Sie ein Datum und eine Uhrzeit festlegen, an dem bzw. zu der neue Kunden die App nicht mehr im Store erwerben oder ihren Eintrag anzeigen dürfen. Dies kann nützlich sein, wenn Sie präzise steuern möchten, wann eine App neuen Kunden nicht mehr angeboten wird, z.B. wenn Sie die Verfügbarkeit zwischen mehr als einer Ihrer Apps koordinieren.

Die Standardeinstellung für **Stop acquisition** ist "Never". Wählen Sie zum Ändern in der Dropdownliste **at** aus, und geben Sie wie oben beschrieben Datum und Uhrzeit ein. Am ausgewählten Datum und zur ausgewählten Uhrzeit können Kunden die App nicht mehr erwerben.

Es ist wichtig zu verstehen, dass diese Option dieselbe Auswirkung hat wie die Auswahl von **Make this app discoverable but not available** im Abschnitt [Sichtbarkeit](choose-visibility-options.md#discoverability) und **Stop acquisition: Any customer with a direct link can see the product’s Store listing, but they can only download it if they owned the product before or have a promotional code and are using a Windows 10 device.** Wenn Sie eine App überhaupt nicht mehr für Kunden anbieten möchten, klicken Sie in der App-Übersicht auf **Make app unavailable**. Weitere Informationen finden Sie unter [Entfernen einer App aus dem Store](guidance-for-app-package-management.md#removing-an-app-from-the-store).

> [!TIP]
> Wenn Sie ein Datum auswählen, um **den Erwerb zu beenden**, und später feststellen, dass Sie die App wieder verfügbar machen möchten, können Sie eine neue Übermittlung erstellen und für **Stop acquisition** wieder **Never** festlegen. Die App wird wieder verfügbar, nachdem Ihre aktualisierte Übermittlung veröffentlicht wurde.

## <a name="customize-the-schedule-for-specific-markets"></a>Anpassen des Zeitplans für bestimmte Märkte 

Die oben ausgewählten Optionen gelten standardmäßig für alle Märkte, in denen Ihre App angeboten wird. Wenn Sie den Preis für die einzelnen Märkte anpassen möchten, klicken Sie auf **Customize for specific markets**. Das Popupfenster **Market selection** wird mit allen Märkten angezeigt, in denen Sie Ihre App verfügbar machen möchten. Wenn Sie Märkte im Abschnitt [Märkte](define-pricing-and-market-selection.md) ausgeschlossen haben, werden diese Märkte hier nicht angezeigt. 

Um einen Zeitplan für einen Markt hinzuzufügen, wählen Sie ihn aus, und klicken Sie auf **Speichern**. Sie sehen dann die gleichen Optionen **Release** und **Stop acquisition** wie oben beschrieben, aber die getroffene Auswahl wird nur auf diesen Markt angewendet.

Um einen Zeitplan hinzuzufügen, der für mehrere Märkte gilt, erstellen Sie eine *Marktgruppe*. Dazu wählen Sie die Märkte aus, die Sie aufnehmen möchten, und geben einen Namen für die Gruppe ein. (Dieser Name dient nur zu Referenzzwecken und ist nicht für alle Kunden sichtbar.) Beispiel: Wenn Sie eine Marktgruppe für Nordamerika erstellen möchten, können Sie **Kanada**, **Mexiko** und **USA** auswählen und sie **Nordamerika** nennen oder einen anderen Namen auswählen. Wenn Sie Ihre Marktgruppe erstellt haben, klicken Sie auf **Speichern**. Sie sehen dann die gleichen Optionen **Release** und **Stop acquisition** wie oben beschrieben, aber die getroffene Auswahl wird nur auf diese Marktgruppe angewendet.

Um einen benutzerdefinierten Zeitplan für einen zusätzlichen Markt oder eine weitere Marktgruppe hinzuzufügen, klicken Sie einfach erneut auf **Customize for specific markets**, und wiederholen Sie diese Schritte. Wählen Sie zum Ändern der in einer Marktgruppe enthaltenen Märkte den Namen aus. Um den benutzerdefinierten Zeitplan für eine Marktgruppe (oder einen einzelnen Markt) zu entfernen, klicken Sie auf **Entfernen**.

> [!NOTE]
> Ein Markt kann nicht zu mehr als einer der Marktgruppen gehören, die Sie im Abschnitt **Zeitplan** verwenden. 










