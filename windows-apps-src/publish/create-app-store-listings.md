---
author: jnHs
Description: "Im Abschnitt „Store-Einträge“ des App-Übermittlungsprozesses stellen Sie den Text und die Bilder bereit, die den Kunden im Store-Eintrag Ihrer App angezeigt werden."
title: "Erstellen von Store-Einträgen für Apps"
ms.assetid: 50D67219-B6C6-4EF0-B76A-926A5F24997D
ms.author: wdg-dev-content
ms.date: 08/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 004169178c906ac892865569fd2ed483bd2471fa
ms.sourcegitcommit: 6c6f3c265498d7651fcc4081c04c41fafcbaa5e7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2017
---
# <a name="create-app-store-listings"></a>Erstellen von Store-Einträgen für Apps


Im Abschnitt **Store-Einträge** des [App-Übermittlungsprozesses](app-submissions.md) stellen Sie den Text und die [Bilder](app-screenshots-and-images.md) bereit, die den Kunden im Store-Eintrag Ihrer App angezeigt werden.

> [!NOTE]
> Wir haben vor kurzem die Optionen auf dieser Seite aktualisiert. Wenn Sie eine laufende Übermittlung hatten, bevor die neueren Optionen verfügbar waren, zeigt diese Übermittlung immer noch die älteren Optionen an. Sie können diese Übermittlung löschen und dann eine neue erstellen, wenn Sie die neuen Optionen für diese App verwenden möchten. Andernfalls werden die neueren Optionen mit dem nächsten Update nach der Veröffentlichung der laufenden Übermittlung verfügbar.

Viele der Felder in einem **Store-Eintrag** sind optional. Es wird jedoch empfohlen, mehrere Bilder und so viele Infos wie möglich bereitzustellen, damit Ihr Eintrag auffällt. Im Schritt **Store-Eintrag** sollten Sie mindestens eine Textbeschreibung und mindestens einen [Screenshot](app-screenshots-and-images.md#screenshots) angeben.

> [!TIP]
> Sie können ebenfalls [Store-Einträge importieren oder exportieren](import-and-export-store-listings.md), wenn Sie Ihre Eintragsinformationen offline in eine CSV-Datei eingeben möchten, anstatt diese Informationen direkt im Dashboard anzugeben. Dies kann besonders dann hilfreich sein, wenn Sie Einträge in vielen Sprachen haben.

Standardmäßig verwenden wir denselben Store-Eintrag (pro Sprache) für alle Ihre Zielbetriebssysteme. Wenn Sie einen benutzerdefinierten Store-Eintrag für ein bestimmtes Betriebssystem verwenden möchten, können Sie [plattformspezifische Store-Einträge erstellen](create-platform-specific-store-listings.md). Ihr Standardeintrag wird für Kunden unter Windows10 immer angezeigt.

## <a name="store-listing-languages"></a>Sprachen für Store-Einträge

Sie müssen die Seite **Store-Eintrag** für mindestens eine Sprache ausfüllen. Es wird empfohlen, einen Store-Eintrag in jeder Sprache bereitzustellen, die Ihre Pakete unterstützen. Sie haben jedoch die Möglichkeit, Sprachen zu entfernen, für die Sie keinen Store-Eintrag bereitstellen möchten. Sie können auch Store-Einträge in zusätzlichen Sprachen bereitstellen, die von Ihren Paketen nicht unterstützt werden.

> [!NOTE]
> Wenn Ihre Übermittlung bereits Pakete enthält, werden die in Ihren Paketen unterstützten [Sprachen](supported-languages.md) in der Übermittlungsübersicht angezeigt (es sei denn, Sie diese entfernen welche).

Klicken Sie zum Hinzufügen oder Entfernen von Sprachen für Ihre Store-Einträge in der Übermittlungsübersicht auf **Add/remove languages**. Wenn Sie bereits Pakete hochgeladen haben, sind die Sprachen dafür im Abschnitt **Languages supported by your packages** aufgeführt. Klicken Sie zum Entfernen einer oder mehrerer dieser Sprachen auf **Entfernen**. Wenn Sie später eine Sprache angeben möchten, die Sie zuvor aus diesem Abschnittentfernt haben, können Sie auf **Hinzufügen** klicken.

Im Abschnitt **Additional Store listing languages** können Sie auf **Manage additional languages** klicken, um Sprachen hinzuzufügen oder zu entfernen, die  *nicht* in Ihren Paketen enthalten sind. Aktivieren Sie die Kontrollkästchen für die Sprachen, die Sie hinzufügen möchten, und klicken Sie dann auf **Aktualisieren**. Die ausgewählten Sprachen werden im Abschnitt **Additional Store listing languages** angezeigt. Klicken Sie zum Entfernen einer oder mehrerer dieser Sprachen auf **Entfernen** (oder klicken Sie auf **Manage additional languages**, und deaktivieren Sie die Kontrollkästchen für die Sprachen, die Sie entfernen möchten).

Wenn Sie Ihre Auswahl getroffen haben, klicken Sie auf **Speichern**, um zur Übermittlungsübersicht zurückzukehren.

> [!NOTE]
> Wenn Sie einen Store-Eintrag in einer Sprache erstellen, die von Ihren Paketen nicht unterstützt wird, müssen Sie angeben, welcher Ihrer reservierten App-Namen in diesem Store-Eintrag angezeigt werden soll, da für diese Sprache kein verknüpftes Paket vorliegt, von dem der Name abgerufen werden könnte. Der Name, den Sie hier wählen, gilt nur für den Store-Eintrag für diese Sprache und wirkt sich nicht auf den Namen aus, der angezeigt wird, wenn ein Kunde die App installiert.

Klicken Sie zum Bearbeiten eines Store-Eintrags in der Übermittlungsübersicht auf den Namen der Sprache.

Oben auf der Seite **Store-Eintrag** sehen Sie die Felder, die dem standardmäßigen Store-Eintrag für die ausgewählte Sprache zugeordnet sind. Diese Felder sind für alle Kunden sichtbar, sofern keine Pakete für frühere Betriebssystemversionen (Windows8.x oder früher, Windows Phone8.x oder früher) vorhanden sind und Sie keine plattformspezifischen Store-Einträge mit verschiedenen Screenshots oder Informationen erstellt haben, die Kunden unter den angegebenen Betriebssystemversionen angezeigt werden. Weitere Informationen finden Sie unter [Erstellen plattformspezifischer Store-Einträge](create-platform-specific-store-listings.md).

## <a name="description"></a>Beschreibung

Über das Beschreibungsfeld können Sie Ihren Kunden den Zweck der App mitteilen. Dieses Feld ist erforderlich und kann bis zu 10.000 Zeichen reinen Text enthalten.

Tipps zum Erstellen einer aussagekräftigen Beschreibung finden Sie unter [Erstellen einer interessanten App-Beschreibung](write-a-great-app-description.md).

## <a name="release-notes"></a>Versionshinweise

Wenn Sie Ihre App erstmalig einrichten, werden Sie dieses Feld wahrscheinlich leer lassen. Bei Updates einer vorhandenen App teilen Sie dem Kunden hier mit, was sich in der aktuellen Version geändert hat. Dieses Feld ist auf 1.500 Zeichen beschränkt.

## <a name="screenshots"></a>Screenshots

Ein Bildschirmfoto ist erforderlich, um Ihre App zu übermitteln. Wir empfehlen die Bereitstellung von mindestens einem Bildschirmfoto für jeden Gerätetyp, den Ihre App unterstützt.

Weitere Informationen finden Sie unter [App-Screenshots und -Bilder](app-screenshots-and-images.md#screenshots).

## <a name="store-logos"></a>Store-Logos 

Store-Logos sind optionale Bilder, die Sie hochladen können, um die Art und Weise zu verbessern, auf die Ihre App für Kunden angezeigt wird. Sie können optional auch angeben, dass nur hier hochgeladene Bilder im Store-Eintrag der App für Windows10-Kunden verwendet werden sollen, statt dem Store die Verwendung von Logobildern aus den Paketen Ihrer App zu erlauben.

> [!IMPORTANT]
> Wenn Ihre App Xbox unterstützt oder wenn Windows Phone8.1 oder frühere Versionen unterstützt werden, müssen Sie hier bestimmte Bilder bereitstellen, damit der Eintrag im Store korrekt angezeigt wird. 

Weitere Informationen finden Sie unter [Store-Logos](app-screenshots-and-images.md#store-logos).

## <a name="additional-art-assets"></a>Zusätzliche Grafikobjekte

Sie können zusätzliche Ressourcen für das Produkt übermitteln, einschließlich Trailer und Werbebilder. Diese sind optional, aber es empfiehlt sich, so viele wie möglich hochzuladen. Diese Bilder können Kunden eine bessere Vorstellung davon bieten, worum es sich bei Ihrem Produkt handelt, und den Eintrag ansprechender gestalten.

Weitere Informationen finden Sie unter [Zusätzliche Grafikobjekte](app-screenshots-and-images.md#additional-art-assets).

## <a name="additional-information"></a>Weitere Informationen

Die Felder in diesem Abschnittsind alle optional, können jedoch verwendet werden, um Kunden mehr Informationen zur Funktionsweise Ihrer App und zu den Voraussetzungen für eine optimale Nutzung anzuzeigen. Wir empfehlen die Überprüfung der unten beschriebenen Optionen und die Bereitstellung aller Informationen, die Kunden über Ihre App vielleicht wissen müssen oder die Kunden zum Herunterladen bewegen können.

### <a name="app-features"></a>App-Features

Hierbei handelt es sich um kurze Zusammenfassungen der wichtigsten App-Features. Diese werden dem Kunden neben der Beschreibung als Aufzählung im Store-Eintrag Ihrer App angezeigt. Die Beschreibung sollte pro Feature nur wenige Wörter (und nicht mehr als 200Zeichen) enthalten. Sie können bis zu 20Features hinzufügen.

> [!NOTE]
> Ihre App-Features werden im Store-Eintrag mit Aufzählungszeichen versehen. Fügen Sie daher keine eigenen Aufzählungszeichen hinzu.

### <a name="additional-system-requirements"></a>Weitere Systemanforderungen

Bei Bedarf können Sie die Hardwarekonfigurationen beschreiben, die für die ordnungsgemäße Funktionsweise der App erforderlich sind, über die Informationen hinaus, die Sie im Abschnitt **Systemanforderungen** unter [App-Eigenschaften](enter-app-properties.md#system-requirements) angegeben haben. Dies ist besonders wichtig, wenn Ihre App Hardware benötigt, die u.U. nicht auf jedem Computer vorhanden ist.

Sie können bis zu 11Elemente sowohl für **Mindesthardwareanforderungen** als auch für **Empfohlene Hardware** eingeben.  Diese werden dem Kunden im App-Eintrag als Aufzählung angezeigt. Die Beschreibung sollte pro Element nur wenige Wörter (und nicht mehr als 200Zeichen) enthalten.

Die Informationen, die Sie hier eingeben, werden Kunden im Store-Eintrag Ihrer App unter Windows10, Version 1607 oder höher, zusammen mit den auf der Eigenschaftenseite des Produkts angegebenen Anforderungen angezeigt.

> [!NOTE]
> Die zusätzlichen Systemanforderungen werden im Store-Eintrag mit Aufzählungszeichen versehen. Fügen Sie daher keine eigenen Aufzählungszeichen hinzu.

### <a name="developed-by"></a>Entwickelt von

Geben Sie hier Text ein, wenn Sie das Feld **Entwickelt von** im Store-Eintrag Ihrer App anzeigen möchten. (Das Feld **Veröffentlicht von** zeigt den mit Ihrem Konto verknüpften Anzeigename des Herausgebers an, wenn Sie einen Wert für das Feld **Veröffentlicht von** angeben.)

Dieses Feld ist auf 255 Zeichen beschränkt.


## <a name="shared-fields"></a>Freigegebene Felder

Mit den unten beschriebenen Elementen können Kunden Ihr Produkt finden und verstehen. Die hier eingegebenen Informationen gelten für alle Store-Einträge einer bestimmten Sprache, auch wenn Sie [plattformspezifische Store-Einträge erstellen](create-platform-specific-store-listings.md).

### <a name="search-terms"></a>Suchbegriffe

Suchbegriffe (früher als Schlüsselwörter bezeichnet) sind einzelne Wörter oder kurze Ausdrücke, die für Kunden nicht angezeigt werden, jedoch dazu beitragen, dass Ihre App in Suchergebnissen für den Begriff erscheint. Sie können bis zu 7 Suchbegriffe mit jeweils maximal 30 Zeichen aufnehmen und nicht mehr als 21 separate Wörter für alle Suchbegriffe verwenden.

Beim Hinzufügen von Suchbegriffen sollten Sie überlegen, mit welchen Begriffen Kunden nach Ihrer App suchen würden, insbesondere, wenn sie nicht im App-Namen vorkommen. Verwenden Sie nur Suchbegriffe, die wirklich für Ihre App relevant sind.


### <a name="privacy-policy"></a>Datenschutzrichtlinie

Wenn Ihre App über eine Datenschutzrichtlinie verfügt, geben Sie die URL hier ein. Sie müssen sicherstellen, dass die geltenden Datenschutzgesetze eingehalten werden und müssen bei Bedarf eine Datenschutzrichtlinie bereitstellen.

> [!IMPORTANT]
> Microsoft stellt keine standardmäßigen Datenschutzrichtlinien für Ihre App bereit. Außerdem ist Ihre App nicht durch Datenschutzrichtlinien von Microsoft abgedeckt. Um festzustellen, ob Ihre App eine Datenschutzrichtlinie benötigt, lesen Sie die [Vereinbarung für App-Entwickler](https://msdn.microsoft.com/library/windows/apps/hh694058) und die [Windows Store-Richtlinien](https://msdn.microsoft.com/library/windows/apps/dn764944.aspx#pol_10_5_1).

### <a name="copyright-and-trademark-info"></a>Urheberrecht- und Markeninformationen

Zusätzliche Urheberrecht- und Markeninformationen können Sie bei Bedarf hier eingeben. Dieses Feld ist auf 200 Zeichen beschränkt.

### <a name="additional-license-terms"></a>Zusätzliche Lizenzbedingungen

Lassen Sie dieses Feld leer, wenn Sie möchten, dass Ihre App für Kunden gemäß den **Standardbedingungen für anwendungsbezogene Lizenzen** (am Ende der [Vereinbarung für App-Entwickler](https://msdn.microsoft.com/library/windows/apps/hh694058)) lizenziert wird.

Wenn sich Ihre Lizenzbedingungen von den **Standardbedingungen für anwendungsbezogene Lizenzen** unterscheiden, geben Sie sie hier ein.

Wenn Sie einen einzelnen URL in dieses Feld eingeben, wird dieser für Kunden als Link angezeigt, auf den sie klicken können, um Ihre zusätzlichen Lizenzbedingungen zu lesen. Dies ist hilfreich, wenn Ihre zusätzlichen Lizenzbedingungen sehr lang sind, oder wenn Sie Links oder Formatierungen in die zusätzlichen Lizenzbedingungen einschließen möchten, auf die geklickt werden kann.

Sie können auch bis zu 10.000 Zeichen Texts in dieses Feld eingeben. Wenn Sie dies tun, werden Kunden die zusätzlichen Lizenzbedingungen als reiner Text angezeigt.

### <a name="website"></a>Website

Geben Sie die URL der Webseite für Ihre App ein. Diese URL muss auf eine Seite Ihrer eigenen Website verweisen, nicht auf den Webeintrag Ihrer App im Store.

### <a name="support-contact-info"></a>Support – Kontaktinfos

Geben Sie die URL der Webseite ein, auf der Ihre Kunden Support für die App erhalten, oder eine E-Mail-Adresse, unter der Kunden den Support erreichen können.

> [!IMPORTANT]
> Microsoft bietet keinen App-Support für Ihre Kunden.

