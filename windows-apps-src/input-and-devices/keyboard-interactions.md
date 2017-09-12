---
author: Karl-Bridge-Microsoft
Description: "Erfahren Sie, wie Sie Ihre UWP-Apps entwerfen und optimieren, sodass sie die bestmögliche Umgebung für erfahrene Tastaturbenutzer und Personen mit Einschränkungen und anderen Anforderungen an Barrierefreiheit bieten."
title: Tastaturinteraktionen
ms.assetid: FF819BAC-67C0-4EC9-8921-F087BE188138
label: Keyboard interactions
template: detail.hbs
keywords: Tastatur, Barrierefreiheit, Navigation, Fokus, Text, Eingabe, Benutzerinteraktionen, Gamepad, Fernbedienung
ms.author: kbridge
ms.date: 03/29/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
pm-contact: chigy
design-contact: kimsea
dev-contact: niallm
doc-status: Published
ms.openlocfilehash: 22a95cfb77740d7521c62f0b7153130ccdc1b552
ms.sourcegitcommit: ba0d20f6fad75ce98c25ceead78aab6661250571
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2017
---
# <a name="keyboard-interactions"></a>Tastaturinteraktionen
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

![Tastaturfavoritenbild](images/keyboard/keyboard-hero.jpg)

Erfahren Sie, wie Sie Ihre UWP-Apps entwerfen und optimieren, sodass sie die bestmögliche Umgebung für erfahrene Tastaturbenutzer und Personen mit Einschränkungen und anderen Anforderungen an Barrierefreiheit bieten.

Auf verschiedenen Geräten ist die Tastatureingabe ein wichtiger Teil der Gesamtinteraktion mit der Universellen Windows-Plattform (UWP). Eine gut durchdachte Tastatur ermöglicht Benutzern die effiziente UI-Navigation in Ihrer App und Zugriff auf die gesamte Funktionalität, ohne die Hände von der Tastatur zu nehmen.

![Bild von Tastatur und Gamepad](images/keyboard/keyboard-gamepad.jpg)

***Allgemeine Interaktionsmuster sind bei Tastatur und Gamepad gleich.***

In diesem Thema konzentrieren wir uns speziell auf das UWP-App-Design für die Tastatureingabe auf PCs. Eine gut durchdachte Tastatur ist jedoch wichtig für die Unterstützung von Eingabehilfen (z.B. die Windows-Sprachausgabe), die Verwendung von Softwaretastaturen (z.B. die [Touch-Tastatur](#touch-keyboard) und die [Bildschirmtastatur](#osk)) und andere Gerätetypen, z.B. Xbox-Gamepad und -Fernbedienung.

Viele der hier erwähnten Richtlinien und Empfehlungen, einschließlich [visueller Fokuselemente](#focus-visual), [Zugriffstasten](#access-keys), und [UI-Navigation](#navigation), gelten auch für diese anderen Szenarien.

**HINWEIS** Während Hardware- und Softwaretastaturen für die Texteingabe verwendet werden, liegt der Fokus dieses Themas auf Navigation und Interaktion.

## <a name="built-in-support"></a>Integrierte Unterstützung

Zusammen mit der Maus ist die Tastatur das am häufigsten verwendete Peripheriegerät für PCs und daher ein wesentlicher Bestandteil des PC-Erlebnisses. PC-Benutzer erwarten ein umfassendes und konsistentes Erlebnis bei Tastatureingaben in System-Apps und individuellen Apps.

Alle UWP-Steuerelemente enthalten integrierte Unterstützung für umfangreiche Tastaturfunktionen und Benutzerinteraktionen, während die Plattform selbst eine umfassende Grundlage für das Erstellen von Tastaturfunktionen bietet, die Ihrer Meinung nach am besten für Ihre benutzerdefinierten Steuerelemente und Apps geeignet sind.

![Bild von Tastatur mit Telefon](images/keyboard/keyboard-phone.jpg)

***UWP unterstützt Tastatur auf allen Geräten***

## <a name="basic-experiences"></a>Grundlegende Funktionen
![Fokusbasierte Geräte](images/keyboard/focus-based-devices.jpg)

Wie bereits erwähnt, ist die Tastatureingabe für Navigation und Befehle von Eingabegeräten wie Xbox-Gamepad und -Fernbedienung und Eingabehilfen wie der Sprachausgabe zum Großteil gleich. Die Einheitlichkeit in Bezug auf Eingabetypen und Tools minimiert zusätzliche Aufgaben und trägt zur Erreichung des Ziels der Universellen Windows-Plattform bei: einmal erstellen, überall ausführen.

Bei Bedarf identifizieren wir wichtige Unterschiede, die Sie kennen sollten, und beschreiben Maßnahmen, die Sie berücksichtigen sollten.

Hier sind die Geräte und die Tools, die in diesem Thema erläutert werden:

| Gerät/Tool                       | Beschreibung     |
|-----------------------------------|-----------------|
|Tastatur (Hardware und Software)   |Neben der standardmäßigen Hardwaretastatur unterstützen UWP-Apps zwei Softwaretastaturen: [Touch-Tastatur (oder Softwaretastatur)](#touch-keyboard) und [Bildschirmtastatur](#osk).|
|Gamepad und Fernbedienung         |Xbox-Gamepad und -Fernbedienung sind grundlegende Eingabegeräte im [10-Fuß-Bereich](designing-for-tv.md).
Ausführliche Informationen zur UWP-Unterstützung für Gamepad und Fernbedienung finden Sie unter [Interaktionen mit Gamepad und Fernbedienung](gamepad-and-remote-interactions.md).|
|Bildschirmleseprogramme (Sprachausgabe)          |Die Sprachausgabe ist ein integriertes Bildschirmleseprogramm für Windows, das eindeutige Interaktion und Funktionalität bietet, aber dennoch auf der einfachen Tastaturnavigation und -eingabe basiert.
Weitere Informationen zur Sprachausgabe finden Sie unter [Erste Schritte mit Sprachausgabe](https://support.microsoft.com/help/22798/windows-10-narrator-get-started).|

## <a name="custom-experiences-and-efficient-keyboarding"></a>Benutzerdefinierte Erfahrungen und effiziente Tastaturfunktionen
Wie bereits erwähnt, ist Die Tastaturunterstützung ist ein wesentlicher Bestandteil dafür, dass Ihre Anwendungen optimal für Benutzer mit unterschiedlichen Kenntnissen, Fähigkeiten und Erwartungen funktionieren. Wir empfehlen Ihnen, folgendes zu priorisieren.
- Unterstützung der Tastaturnavigation und Interaktion
    - Stellen Sie sicher, dass ausführbare Elemente als Tabstopps gekennzeichnet sind (und nicht bedienbare Elemente andersartig gekennzeichnet sind), und die Reihenfolge für die Seitennavigation logisch und vorhersehbar ist (weiter Informationen finden Sie unter [Tabstopps](#tab-stops))
    - Legen Sie den anfänglichen Fokus auf das logischste Element fest (weitere Informationen finden Sie unter [Anfänglicher Fokus](#initial-focus))
    - Bieten Sie eine Navigation mittels Pfeiltasten für "innere Navigationsvorgänge" an (siehe [Navigation](#navigation))
- Unterstützen Sie Tastenkombinationen
    - Stellen Sie Zugriffstasten für schnelle Aktionen bereit (siehe [Schnellinfos](#accelerators))
    - Bereitstellen von Zugriffstasten, um die Benutzeroberfläche Ihrer App zu navigieren (siehe [Zugriffstasten](access-keys.md))

### <a name="focus-visuals-a-namefocus-visual"></a>Visuelle Fokuselemente <a name="focus-visual">

Die UWP unterstützt ein einzelnes Design für visuelle Fokuselemente, das gut für alle Eingabearten und -funktionen funktioniert.
![Visuelles Fokuselement](images/keyboard/focus-visual.png)

Ein visuelles Fokuselement:
-   wird angezeigt, wenn ein UI-Element über eine Tastatur und/oder ein Gamepad/eine Fernbedienung den Fokus erhält
-   wird als hervorgehobener Rahmen um das UI-Element wiedergegeben, um anzugeben, dass eine Aktion ausgeführt werden kann
-   unterstützt einen Benutzer dabei, in einer App-UI zu navigieren, ohne die Orientierung zu verlieren
-   kann für Ihre App angepasst werden (siehe [Visuelle Fokuselemente mit hoher Sichtbarkeit](guidelines-for-visualfeedback.md#high-visibility-focus-visuals))

**HINWEIS** Das visuelle UWP-Fokuselement entspricht nicht dem Fokusrechteck der Sprachausgabe.

### <a name="tab-stops-a-nametab-stops"></a>Tabstopps <a name="tab-stops">

Damit ein Steuerelement (einschließlich der Navigationselemente) über die Tastatur verwendet werden kann, muss auf dem Steuerelement der Fokus liegen. Eine Möglichkeit für ein Steuerelement, den Tastaturfokus zu erhalten, ist, es über TAB-Navigation zugänglich zu machen, indem es als Tabstopp in der Aktivierreihenfolge Ihrer App identifiziert wird.

Damit ein Steuerelement in der Aktivierreihenfolge enthalten ist, muss die [**IsEnabled**](https://msdn.microsoft.com/library/windows/apps/br209419)-Eigenschaft auf **true** und die [**IsTabStop**](https://msdn.microsoft.com/library/windows/apps/br209422)-Eigenschaft auf **true** festgelegt werden.

Um ein Steuerelement explizit aus der Aktivierreihenfolge auszuschließen, legen Sie die [**IsTabStop**](https://msdn.microsoft.com/library/windows/apps/br209422)-Eigenschaft auf **false** fest.

Standardmäßig entspricht die Aktivierreihenfolge der Reihenfolge, in der UI-Elemente erstellt werden. Wenn beispielsweise ein `StackPanel` die Elemente `Button`, `Checkbox` und `TextBox` enthält, ist die Aktivierreihenfolge `Button`, `Checkbox` und`TextBox`.

Sie können die Standardaktivierreihenfolge überschreiben, indem Sie die [**TabIndex**](https://msdn.microsoft.com/library/windows/apps/br209461)-Eigenschaft festlegen.

#### <a name="tab-order-should-be-logical-and-predictable"></a>Aktivierreihenfolge sollte logisch und vorhersehbar sein

Ein gut durchdachtes Tastatur-Navigationsmodell, das eine logische und vorhersehbare Aktivierreihenfolge verwendet, macht Ihre App intuitiver und unterstützt Benutzer dabei, Funktionen effizienter und effektiver zu erkunden, zu identifizieren und auf sie zuzugreifen.

Alle interaktiven Steuerelemente (die nicht in einer [Gruppe](#control-group) enthalten sind) sollten über Tabstopps verfügen, nicht interaktive Steuerelemente, z. B. `labels`, dagegen nicht.

Vermeiden Sie eine Aktivierreihenfolge, durch die der Fokus in Ihrer Anwendung wechselt. Beispielsweise sollte eine Liste mit Steuerelementen in einer formularähnlichen UI eine Aktivierreihenfolge aufweisen, die von oben nach unten und von links nach rechts verläuft.

Auf der Seite [Barrierefreiheit der Tastaturnavigation](../accessibility/keyboard-accessibility.md) finden Sie weitere Details zum Anpassen von Tabstopps.

#### <a name="try-to-coordinate-tab-order-and-visual-order"></a>Koordinieren von Aktivierreihenfolge und visueller Reihenfolge

Die Koordinierung der Aktivierreihenfolge und visuellen Reihenfolge (auch Lesereihenfolge oder Anzeigereihenfolge) vereinfacht die Benutzernavigation in der App-UI.

Versuchen Sie, die wichtigsten Befehle, Steuerelemente und Inhalte zuerst in der Aktivierreihenfolge und der visuellen Reihenfolge einzustufen und darzustellen. Die tatsächliche Anzeigeposition kann jedoch vom übergeordneten Layoutcontainer und bestimmten Eigenschaften der untergeordneten Elemente abhängen, die das Layout beeinflussen. Insbesondere kann sich die visuelle Reihenfolge von Layouts mit einer Raster- oder Tabellenmetapher erheblich von der Aktivierreihenfolge unterscheiden.

**HINWEIS** Die visuelle Reihenfolge ist auch von Gebietsschema und Sprache abhängig.

### <a name="initial-focus-a-nameinitial-focus"></a>Anfänglicher Fokus <a name="initial-focus">

Der anfängliche Fokus gibt das UI-Element an, das den Fokus erhält, wenn eine Anwendung oder eine Seite zum ersten Mal gestartet oder aktiviert wird. Wenn Sie eine Tastatur verwenden, beginnt ein Benutzer von diesem Element die Interaktion mit der App-UI.

Für UWP-Apps wird der anfängliche Fokus auf das Element mit dem höchsten [**TabIndex**](https://msdn.microsoft.com/library/windows/apps/br209461) festgelegt, der den Fokus erhalten kann. Untergeordnete Elemente von Container-Steuerelementen werden ignoriert. Bei einer Verknüpfung erhält das erste Element in der visuellen Struktur den Fokus.

#### <a name="set-initial-focus-on-the-most-logical-element"></a>Festlegen des anfänglichen Fokus auf das logischste Element

Legen Sie den anfänglichen Fokus auf das UI-Element für die erste, oder primäre, Aktion, die Benutzer mit der größten Wahrscheinlichkeit durchführen, wenn Sie Ihre App starten oder zu einer Seite navigieren. Beispiele:
-   Eine Foto-App, wobei der Fokus auf dem ersten Element in einer Galerie liegt
-   Eine Musik-App, wobei der Fokus auf der Wiedergabe-Taste liegt

#### <a name="dont-set-initial-focus-on-an-element-that-exposes-a-potentially-negative-or-even-disastrous-outcome"></a>Kein anfänglicher Fokus auf ein Element mit potenziell negativen oder verhängnisvollen Ergebnissen

Dieser Funktionsumfang sollte vom Benutzer festgelegt werden. Das Festlegen des anfänglichen Fokus auf ein Element mit einem signifikanten Ergebnis resultiert möglicherweise in unerwünschtem Datenverlust oder Systemzugriff. Legen Sie beispielsweise nicht den Fokus auf die Schaltfläche "Löschen" beim Navigieren zu einer E-Mail-Nachricht.

Auf der Seite [Barrierefreiheit der Tastaturnavigation](../accessibility/keyboard-accessibility.md) finden Sie weitere Informationen zum Überschreiben der Aktivierreihenfolge.

### <a name="navigation-a-namenavigation"></a>Navigation <a name="navigation">

Die Tastaturnavigation wird in der Regel durch die TAB-Tasten und die Pfeiltasten unterstützt.

![TAB-Tasten und Pfeiltasten](images/keyboard/tab-and-arrow.png)

Standardmäßig weisen UWP-Steuerelemente dieses grundlegende Tastaturverhalten auf:
-   **TAB-Tasten** dienen der Navigation zwischen ausführbaren/aktiven Steuerelementen in der Aktivierreihenfolge.
-   **UMSCHALT + TAB** dient der Navigation zwischen Steuerelementen in umgekehrter Aktivierreihenfolge. Wenn der Benutzer mit der Pfeiltaste in das Steuerelement navigiert ist, liegt der Fokus auf dem letzten bekannten Wert im Steuerelement.
-   **Pfeiltasten** ermöglichen die steuerelementspezifische „interne Navigation“, wenn der Benutzer zur „internen Navigation“ wechselt. Pfeiltasten dienen nicht der Navigation außerhalb des Steuerelements. Beispiele:
    -   Nach-oben-/Nach-unten-Pfeiltaste verschiebt Fokus in `ListView` und `MenuFlyout`
    -   Ändern der derzeit ausgewählten Werte für `Slider` und `RatingsControl`
    -   Internes Verschieben des Textcursors `TextBox`
    -   Internes Erweitern/Reduzieren von Elementen `TreeView`

Verwenden Sie dieses Standardverhalten, um die Tastaturnavigation Ihrer App zu optimieren.

#### <a name="use-inner-navigation-with-sets-of-related-controls"></a>Verwenden Sie die „interne Navigation“ mit Gruppen verwandter Steuerelemente.

Durch Bereitstellen der Pfeiltastennavigation für eine Gruppe verwandter Steuerelemente wird ihre Beziehung innerhalb der gesamten Organisation der App-UI verstärkt.

Das hier gezeigte Steuerelement `ContentDialog` ermöglicht beispielsweise standardmäßig die interne Navigation für eine horizontale Reihe von Tasten. (Informationen zu benutzerdefinierten Steuerelementen finden Sie im Abschnitt [Steuerelementgruppe](#control-group)).

![Dialogfeldbeispiel](images/keyboard/dialog.png)

***Interaktion mit einer Sammlung verwandter Tasten durch Pfeiltastennavigation vereinfacht***

Wenn Elemente in einer einzelnen Spalte angezeigt werden, erfolgt die Elementnavigation mit der Nach-oben-/Nach-unten-Pfeiltaste. Wenn Elemente in einer einzelnen Zeile angezeigt werden, erfolgt die Elementnavigation mit der Rechts-/Links-Pfeiltaste. Wenn sich die Elemente in mehreren Spalten befinden, erfolgt die Navigation über alle 4 Pfeiltasten.

#### <a name="make-a-set-of-related-controls-a-single-tab-stop"></a>Konvertieren einer Gruppe verwandter Steuerelemente in einen einzelnen Tabstopp

Durch Konvertieren einer Gruppe verwandter oder komplementärer Steuerelemente in einen einzelnen Tabstopp können Sie die Anzahl der Tabstopps in Ihrer App minimieren.

Die folgenden Abbildungen zeigen beispielsweise zwei gestapelte `ListView`-Steuerelemente. Die Abbildung auf der linken Seite zeigt die Pfeiltastennavigation zwischen `ListView`-Steuerelementen für einen Tabstopp. Die Abbildung auf der rechten Seite zeigt, wie die Navigation zwischen untergeordneten Elementen einfacher und effizienter gestaltet werden kann, da die Navigation in übergeordneten Steuerelementen nicht mit einer TAB-Taste erfolgt.


<table>
  <td>![Pfeil und TAB](images/keyboard/arrow-and-tab.png)</td>
  <td>![Nur Pfeil](images/keyboard/arrow-only.png)</td>
</table>

***Die Interaktion mit zwei gestapelten ListView-Steuerelementen kann durch Eliminierung von Tabstopps und Navigation mit den Pfeiltasten einfacher und effizienter gestaltet werden.***

Im Abschnitt [Steuerelementgruppe](#control-group) erfahren Sie, wie Sie die Optimierungsbeispiele auf Ihre Anwendungs-UI anwenden.

### <a name="interaction-and-commanding"></a>Interaktion und Befehle

Wenn ein Steuerelement den Fokus hat, kann ein Benutzer mit ihm interagieren und zugehörige Funktionalität über spezielle Tastatureingaben aufrufen.

#### <a name="text-entry"></a>Texteingabe

Für Steuerelemente, die speziell der Texteingabe dienen (wie `TextBox` und `RichEditBox`), werden alle Tastatureingaben zur Eingabe von Text oder Navigation in Text verwendet, was Priorität gegenüber anderen Tastaturbefehlen hat. Beispielsweise erkennt das Dropdownmenü für ein `AutoSuggestBox`-Steuerelement nicht die **Leertaste** als Auswahlbefehl.

![Texteingabe](images/keyboard/text-entry.png)

#### <a name="space-key"></a>Leertaste

Wenn Sie sich nicht im Texteingabemodus befinden, ruft die **Leertaste** die Aktion oder den Befehl auf, der mit dem fokussierten Steuerelement verknüpft ist (vergleichbar mit dem Tippen oder dem Klicken mit einer Maus).

![LEERTASTE](images/keyboard/space-key.png)

#### <a name="enter-key"></a>EINGABETASTE

Die **EINGABETASTE** ermöglicht eine Vielzahl an gängigen Benutzerinteraktionen, abhängig vom fokussierten Steuerelement:
-   Aktiviert Befehlssteuerelemente wie `Button` oder `Hyperlink`. Für mehr Benutzerfreundlichkeit aktiviert die **EINGABETASTE** auch Steuerelemente, die Befehlssteuerelementen ähneln, wie `ToggleButton` oder `AppBarToggleButton`.
-   Zeigt die Auswahl-UI für Steuerelemente an, z.B. `ComboBox` und `DatePicker`. Die **EINGABETASTE** bestätigt und schließt auch die Auswahl-UI.
-   Aktiviert Listensteuerelemente wie `ListView`, `GridView` und `ComboBox`.
    -   Die **EINGABETASTE** führt die Auswahlaktion als **LEERTASTE** für Listen- und Rasterelemente durch, es sei denn, es ist eine zusätzliche Aktion für diese Elemente vorhanden (wodurch ein neues Fenster geöffnet wird).
    -   Wenn eine weitere Aktion mit dem Steuerelement verknüpft ist, führt die **EINGABETASTE** die zusätzliche Aktion und die **LEERTASTE** die Auswahlaktion durch.

**HINWEIS** Die **EINGABETASTE** und die **LEERTASTE** führen nicht immer dieselbe Aktion aus, aber oft.

![EINGABETASTE](images/keyboard/enter-key.png)

Die ESC-TASTE ermöglicht Benutzern das Abbrechen einer Übergangs-UI (sowie aller laufenden Aktionen in dieser UI).

Beispiele umfassen:
-   Benutzer öffnet eine `ComboBox` mit einem ausgewählten Wert und verwendet die Pfeiltasten zum Verschieben der Fokusauswahl auf einen neuen Wert. Durch Drücken der ESC-TASTE wird die `ComboBox` geschlossen und der ausgewählte Wert auf den ursprünglichen Wert zurückgesetzt.
-   Der Benutzer ruft eine Aktion zum dauerhaften Löschen für eine E-Mail auf und wird mit einem `ContentDialog` aufgefordert, die Aktion zu bestätigen. Der Benutzer entscheidet, dass dies nicht die gewünschte Aktion ist, und drückt die **ESC-TASTE**, um das Dialogfeld zu schließen. Da die **ESC-TASTE** mit der Schaltfläche **Abbrechen** verknüpft ist, wird das Dialogfeld geschlossen und die Aktion abgebrochen. Die **ESC-TASTE** wirkt sich nur auf die Übergangs-UI aus. Die App-UI wird nicht geschlossen, und es wird auch nicht durch sie zurücknavigiert.

![ESC-TASTE](images/keyboard/esc-key.png)

#### <a name="home-and-end-keys"></a>POS1-TASTE und ENDE-TASTE

Die Tasten **POS1** und **ENDE** ermöglichen Benutzern, einen Bildlauf zum Anfang oder Ende eines UI-Bereichs durchzuführen.

Beispiele umfassen:
-   Für die Steuerelemente `ListView` und `GridView` verlagert die Taste **POS1** den Fokus auf das erste Element und führt einen Bildlauf in die Ansicht durch. Die Taste **ENDE** verlagert den Fokus auf das letzte Element und führt einen Bildlauf in die Ansicht durch.
-   Für das Steuerelement `ScrollView` führt die Taste **POS1** einen Bildlauf zum Anfang des Bereichs durch. Die Taste **ENDE** führt einen Bildlauf zum Ende des Bereichs durch (Fokus wird nicht geändert).

![POS1-TASTE und ENDE-TASTE](images/keyboard/home-and-end.png)

#### <a name="page-up-and-page-down-keys"></a>BILD-AUF-TASTE und BILD-AB-TASTE

Die **BILD-TASTEN** ermöglichen Benutzern das Durchführen eines Bildlaufs in einem UI-Bereich in einzelnen Inkrementen.

Für die Steuerelemente `ListView` und `GridView` führt die **BILD-AUF-TASTE** einen Bildlauf nach oben im Bereich um ein „Bild“ (in der Regel die Viewporthöhe) durch und verlagert den Fokus nach oben im Bereich. Alternativ führt die **BILD-AB-TASTE** einen Bildlauf nach unten im Bereich um ein Bild durch und verlagert den Fokus nach unten im Bereich.

![BILD-AUF-TASTE und BILD-AB-TASTE](images/keyboard/page-up-and-down.png)

### <a name="keyboard-shortcuts"></a>Tastenkombinationen

Tastenkombinationen können Ihre App einfacher und effizienter machen.

Zusätzlich zur Navigation und Aktivierung über die Tastatur empfiehlt es sich, Tastenkombinationen für die Funktionen Ihrer App zu implementieren. Die TAB-Navigation ist eine gute, einfache Form der Tastaturunterstützung. Bei komplexeren Formularen kann es aber sinnvoll sein, auch Unterstützung für Tastenkombinationen hinzuzufügen. Hierdurch kann Ihre App effizienter genutzt werden – auch von Menschen, die sowohl Tastatur als auch Zeigegeräte nutzen.

Tastenkombinationen sind eine effiziente Methode für den Zugriff auf App-Funktionen und verbessern daher die Produktivität der Benutzer. Es gibt zwei Arten von Tastenkombinationen:
-   [Tastenkombinationen mit der STRG-Taste](#accelerators) ermöglichen den schnellen Zugriff auf App-Befehle. Ihr App kann UI-Elemente aufweisen, die exakt dem Befehl entsprechen. Hierbei handelt es sich um eine Kombination aus der STRG-TASTE und einer Buchstabentaste.
-   [Tastenkombinationen mit der ALT-TASTE](#access-keys) ermöglichen den schnellen Zugriff auf UI-Elemente Ihrer App. Hierbei handelt es sich um eine Kombination aus der ALT-TASTE und einer Buchstabentaste.

Besuchen Sie diese Seite, um eine umfassende Liste mit [Tastenkombinationen für Windows](https://support.microsoft.com/help/12445/windows-keyboard-shortcuts) sowie [anwendungsspezifischen Tastenkombinationen](https://support.microsoft.com/help/13805/windows-keyboard-shortcuts-in-apps) zu erhalten, die in von Microsoft entwickelten Anwendungen verwendet werden können.

#### <a name="accelerators-a-nameaccelerators"></a>Tastenkombinationen mit der STRG-Taste <a name="accelerators">

Tastenkombinationen mit der STRG-Taste ermöglichen es Benutzern, häufige Aktionen in Anwendungen schnell auszuführen. Das Bereitstellen konsistenter Tastenkombinationen mit der STRG-Taste, die Benutzer sich leicht merken und in Anwendungen mit ähnlichen Aufgaben verwenden können, ist sehr wichtig, damit diese Tastenkombinationen hilfreich und effizient sind.

Beispiele für Tastenkombinationen mit der STRG-Taste:
-   Durch Drücken von STRG + N in der Mail-App wird ein neues E-Mail-Element gestartet.
-   Durch Drücken von STRG + E in der Edge- und Store-App können Benutzer schnell Text im Suchfeld eingeben.

Tastenkombinationen mit der STRG-Taste weisen die folgenden Merkmale auf:
-   Sie verwenden primär die STRG- und Funktionstastensequenzen (Windows-Systemtastenkombinationen verwenden ebenfalls ALT in Verbindung mit nicht alphanumerischen Tasten und der Windows-Logo-Taste).
-   Sie dienen in erster Linie erweiterten Benutzer hinsichtlich Effizienz.
-   Sie werden nur den am häufigsten verwendeten Befehlen zugewiesen.
-   Ihre Speicherung ist vorgesehen, und sie werden nur in Menüs, QuickInfos und in der Hilfe dokumentiert.
-   Sie wirken sich auf das gesamte Programm aus, sie haben jedoch keine Auswirkung, wenn sie nicht angewendet werden.
-   Sie müssen konsistent zugewiesen werden, da sie gespeichert und nicht direkt dokumentiert werden.

#### <a name="access-keys-a-nameaccess-keys"></a>Tastenkombinationen mit der STRG-Taste <a name="access-keys">

Tastenkombinationen mit der STRG-Taste bieten Benutzern mit Anforderungen für Barrierefreiheit und erfahrenen Tastaturbenutzern eine effiziente und effektive Möglichkeit, in der App-UI zu navigieren.

Auf der Seite [Tastenkombinationen mit der STRG-Taste](access-keys.md) finden Sie umfassendere Informationen zur Unterstützung von Tastenkombinationen mit der STRG-Taste mit UWP.

Tastenkombinationen mit der STRG-Taste ermöglichen es Benutzern mit motorischen Einschränkungen, jeweils eine Taste zu drücken, um eine Aktion für ein bestimmtes Element in der UI durchzuführen. Darüber hinaus können Tastenkombinationen mit der STRG-Taste verwendet werden, um zusätzliche Tastenkombinationen zu kommunizieren, damit erfahrene Benutzer schnell Aktionen durchführen können.

Tastenkombinationen mit der STRG-Taste weisen die folgenden Merkmale auf:
-   Sie verwenden ALT und eine alphanumerische Taste.
-   Sie dienen in erster Linie der Barrierefreiheit.
-   Sie sind direkt in der UI neben dem Steuerelement mit [Zugriffstasteninfos](access-keys.md) dokumentiert.
-   Sie wirken sich nur auf das aktuelle Fenster aus und navigieren zum entsprechenden Menü- oder Steuerelement.
-   Sie werden nicht konsistent zugewiesen, da dies nicht immer möglich ist. Zugriffstasten sollten jedoch für die am häufigsten verwendeten Befehle, insbesondere für Schaltflächen für den Commit, konsistent zugewiesen werden.
-   Sie sind lokalisiert.

#### <a name="common-keyboard-shortcuts"></a>Häufig verwendete Tastenkombinationen

Die folgende Tabelle enthält einige Beispiele für häufig verwendete Tastaturbefehle. Eine vollständige Liste der Tastaturbefehle erhalten Sie unter [Tastenkombinationen in Windows](https://support.microsoft.com/kb/126449).

| Aktion                               | Tastenkombination                                      |
|--------------------------------------|--------------------------------------------------|
| Alle auswählen                           | STRG+A                                           |
| Fortlaufend auswählen                  | UMSCHALT+Pfeiltaste                                  |
| Speichern                                 | STRG+S                                           |
| Suchen                                 | STRG+F                                           |
| Drucken                                | STRG+P                                           |
| Kopieren                                 | STRG+C                                           |
| Ausschneiden                                  | STRG+X                                           |
| Einfügen                                | STRG+V                                           |
| Rückgängig machen                                 | STRG+Z                                           |
| Nächste Registerkarte                             | STRG+TAB                                         |
| Registerkarte schließen                            | STRG+F4 oder STRG+W                                |
| Semantischer Zoom                        | STRG+PLUS-TASTE oder STRG+MINUS-TASTE                                 |

## <a name="advanced-experiences"></a>Erweiterte Funktionen

In diesem Abschnitterläutern wir einige der komplexeren Tastaturinteraktionen, die durch UWP-Apps unterstützt werden, sowie einige der Verhaltensweisen, die Sie bei Verwendung Ihrer App auf verschiedenen Geräten und mit verschiedenen Tools berücksichtigen sollten.

### <a name="control-group-a-namecontrol-group"></a>Steuerelementgruppe <a name="control-group">

Sie können eine Gruppe verwandter oder komplementärer Steuerelemente in einer „Steuerelementgruppe“ (oder einem direktionalen Bereich) gruppieren, was die „interne Navigation“ mit den Pfeiltasten aktiviert. Die Steuerelementgruppe kann ein einzelner Tabstopp sein, oder Sie können mehrere Tabstopps innerhalb der Steuerelementgruppe angeben.

#### <a name="arrow-key-navigation"></a>Pfeiltastennavigation

Benutzer erwarten Unterstützung für die Pfeiltastennavigation, wenn eine Gruppe ähnlicher, verwandter Steuerelemente in einem UI-Bereich vorhanden ist:
-   `AppBarButtons` in `CommandBar`
-   `ListItems` oder `GridItems` in `ListView` oder `GridView`
-   `Buttons` in `ContentDialog`

UWP-Steuerelemente unterstützen die Pfeiltastennavigation standardmäßig. Verwenden Sie für benutzerdefinierte Layouts und Steuerelementgruppen `XYFocusKeyboardNavigation="Enabled"`, um ein ähnliches Verhalten zu erzeugen.

Ziehen Sie in Betracht, die Pfeiltastennavigation für folgende Steuerelemente zu unterstützen:

<table>
  <tr>
    <td>
      <p>![Dialogfeld](images/keyboard/dialog.png)</p>
      <p>**Schaltflächen**</p>
      <p>![Optionsschaltfläche](images/keyboard/radiobutton.png)</p>
      <p>**Optionsschaltflächen**</p>     
    </td>
    <td>
      <p>![App-Leiste](images/keyboard/appbar.png)</p>
      <p>**Schaltflächen auf App-Leiste**</p>
      <p>![Listen- und Rasterelemente](images/keyboard/list-and-grid-items.png)</p>
      <p>**Listenelemente und Rasterelemente**</p>
    </td>    
  </tr>
</table>

#### <a name="tab-stops"></a>Tabstopps

Anhängig von Funktionalität und Layout Ihrer App ist die beste Navigationsoption für eine Steuerelementgruppe evtl. ein einzelner Tabstopp mit Pfeilnavigation zu untergeordneten Elementen, mehrere Tabstopps oder eine Kombination.

##### <a name="use-multiple-tab-stops-and-arrow-keys-for-buttons"></a>Verwenden mehrerer Tabstopps und Pfeiltasten für Schaltflächen

Benutzer, für die Barrierefreiheit wichtig ist, benötigen gut etablierte Tastaturnavigationsregeln, bei denen nicht typischerweise Pfeiltasten zum Navigieren in verschiedenen Schaltflächen verwendet werden. Allerdings empfinden Benutzer ohne Sehschwäche das Verhalten evtl. als natürlich.

Ein Beispiel des UWP-Standardverhaltens ist in diesem Fall das `ContentDialog`. Während Pfeiltasten zum Navigieren zwischen Schaltflächen verwendet werden können, ist jede Schaltfläche auch ein Tabstopp.

##### <a name="assign-single-tab-stop-to-familiar-ui-patterns"></a>Zuweisen einzelner Tabstopps zu vertrauten UI-Mustern

In Fällen, in denen das Layout einem bekannten UI-Muster für Steuerelementgruppen folgt, kann das Zuweisen eines einzelnen Tabstopps zur Gruppe die Navigationseffizienz für Benutzer verbessern.

Dazu gehören:
-   `RadioButtons`
-   Mehrere `ListViews`, die wie eine einzelne aussehen und sich entsprechend verhalten `ListView`
-   Jede UI, die wie ein Kachelraster aussehen und sich entsprechend verhalten soll (z.B. Kacheln im Startmenü)

#### <a name="specifying-control-group-behavior"></a>Angeben von Steuerelementgruppenverhalten

Verwenden Sie die folgenden APIs, um benutzerdefiniertes Steuerelementgruppenverhalten zu unterstützen (alle werden später in diesem Thema ausführlich erläutert):

-   [XYFocusKeyboardNavigation](custom-keyboard-interactions.md#xyfocuskeyboardnavigation) ermöglicht die Pfeiltastennavigation zwischen Steuerelementen
-   [TabFocusNavigation](custom-keyboard-interactions.md#tab-navigation) gibt an, ob mehrere Tabstopps vorhanden sind oder ein einzelner Tabstopp vorhanden ist
-   [FindFirstFocusableElement und FindLastFocusableElement](managing-focus-navigation.md#findfirstfocusableelement) legen den Fokus auf das erste Element mit der Taste **POS1** und das letzte Element mit der Taste **ENDE**

Die folgende Abbildungzeigt ein intuitives Tastaturnavigationsverhalten für eine Steuerelementgruppe mit zugeordneten Optionsfeldern. In diesem Fall wird Folgendes empfohlen: ein einzelner Tabstopp für die Steuerelementgruppe, interne Navigation zwischen den Optionsfeldern mit den Pfeiltasten, Taste **POS1** verknüpft mit dem ersten Optionsfeld und Taste **ENDE** verknüpft mit dem letzten Optionsfeld.

![Kombination](images/keyboard/putting-it-all-together.png)

### <a name="keyboard-and-narrator"></a>Tastatur und Sprachausgabe

Die Sprachausgabe ist eine UI-Eingabehilfe für Tastaturbenutzer. (Weitere Eingabetypen werden ebenfalls unterstützt.) Allerdings geht die Sprachausgabefunktionalität über die Tastaturinteraktionen hinaus, die von den UWP-Apps unterstützt werden, und beim Entwerfen der UWP-App für die Sprachausgabe ist besondere Sorgfalt erforderlich. (Die [Seite mit den Grundlagen der Sprachausgabe](https://support.microsoft.com/help/22808/windows-10-narrator-learning-basics) leitet Sie durch die Sprachausgabe.)

Einige der Unterschiede zwischen dem UWP-Tastaturverhalten und der Sprachausgabe umfassen:
-   Zusätzliche Tastenkombinationen für die Navigation zu UI-Elementen, die nicht über die Standardtastaturnavigation verfügbar sind, z.B. FESTSTELLTASTE + Pfeiltasten zum Lesen von Steuerelementbeschriftungen.
-   Navigation zu deaktivierten Elementen. Standardmäßig werden deaktivierte Elemente nicht über die Standardtastaturnavigation verfügbar gemacht.
    -   Steuerelementansichten für schnellere Navigation basierend auf UI-Granularität. Benutzer können zu Elementen, Zeichen, Wörtern, Zeilen, Absätzen, Links, Überschriften, Tabellen, Landmarks und Vorschlägen navigieren. Die Standardtastaturnavigation macht diese Objekte als einfache Liste verfügbar, was die Navigation unter Umständen verkompliziert, es sein denn, Sie stellen Tastenkombinationen bereit.

#### <a name="case-study--autosuggestbox-control"></a>Fallstudie – AutoSuggestBox-Steuerelement

Die Suchschaltfläche für `AutoSuggestBox` ist nicht bei der standardmäßigen Tastaturnavigation mit der TAB-Taste und den Pfeiltasten zugänglich, da der Benutzer die **EINGABETASTE** drücken kann, um die Suchabfrage zu senden. Sie ist jedoch über die Sprachausgabe zugänglich, wenn der Benutzer FESTSTELLTASTE + eine Pfeiltaste drückt.

![Automatische Vorschläge für Tastaturfokus](images/keyboard/auto-suggest-keyboard.png)

***Über die Tastatur*** *verwenden Benutzer* die ***EINGABETASTE***, * um eine Suchabfrage zu senden.*

<table>
  <tr>
    <td>
      <p>![Automatische Vorschläge für Sprachausgabefokus](images/keyboard/auto-suggest-narrator-1.png)</p>
      <p>**Mit der Sprachausgabe** *können Benutzer über die EINGABETASTE eine Suchabfrage übermitteln.*</P>
    </td>
    <td>
      <p>![Automatische Vorschläge für Sprachausgabefokus bei Suche](images/keyboard/auto-suggest-narrator-2.png)</p>
      <p>*Der Benutzer kann auch mit FESTSTELLTASTE + NACH-RECHTS-TASTE + LEERTASTE auf die Suchschaltfläche zugreifen.*</p>
    </td>
  </tr>
</table>

### <a name="keyboard-and-the-xbox-gamepad-and-remote-control"></a>Tastatur und Xbox-Gamepad und -Fernbedienung

Xbox-Gamepads und -Fernbedienungen unterstützen das Verhalten und die Funktionen der UWP-Tastatur größtenteils. Da jedoch verschiedene Tastenoptionen einer Tastatur fehlen, stehen bei Gamepad und Fernbedienung viele Tastaturoptimierungen nicht zur Verfügung (Fernbedienung noch eingeschränkter als Gamepad).

Unter [Entwerfen für Xbox und Fernsehgeräte](designing-for-tv.md#gamepad-and-remote-control) finden Sie weitere Informationen zur UWP-Unterstützung für die Eingabe per Gamepad und Fernbedienung.

Im Folgenden finden Sie einige wichtige Zuordnungen zwischen Tastatur, Gamepad und Fernbedienung.

| **Tastatur**  | **Gamepad**                         | **Fernbedienung**  |
|---------------|-------------------------------------|---------------------|
| LEERTASTE         | A-TASTE                            | Auswahltaste       |
| EINGABETASTE         | A-TASTE                            | Auswahltaste       |
| ESCAPE-TASTE        | B-TASTE                            | Zurücktaste         |
| POS1/ENDE      | n.a.                                 | n.a.                 |
| Bild AUF/BILD AB  | Auslösertaste für vertikalen Bildlauf, Bumper-Taste für horizontalen Bildlauf   | n.a.                 |

Einige der wichtigsten Unterschiede, die Sie beim Entwerfen Ihrer UWP-App für die Verwendung mit Gamepad und Fernbedienung beachten sollten, sind:
-   Die Texteingabe erfordert, dass der Benutzer A drückt, um ein Textsteuerelement zu aktivieren.
-   Die Fokusnavigation ist nicht auf Steuerelementgruppen beschränkt, Benutzer können frei zu beliebigen fokussierbaren UI-Elementen in der App navigieren.

    **HINWEIS** Der Fokus kann auf jedes beliebige fokussierbare UI-Element in Tastendruckrichtung verlagert werden, es sei denn, es handelt sich um eine Overlay-UI, oder [Fokusaktivierung](designing-for-tv.md#focus-engagement) ist angegeben. Dies verhindert, dass der Fokus in einen/aus einem Bereich wechselt, bis er durch die A-Taste belegt/nicht belegt ist. Weitere Informationen finden Sie im Abschnitt zur [direktionalen Navigation](#directional-navigation).
-   Das Steuerkreuz und der linke Stick werden zum Verlagern des Fokus zwischen Steuerelementen und für die interne Navigation verwendet.

    **HINWEIS** Gamepad und Fernbedienung navigieren nur zu Elementen in derselben visuellen Reihenfolge wie die gedrückte Richtungstaste. Die Navigation in diese Richtung wird deaktiviert, wenn es kein nachfolgendes Element gibt, das den Fokus erhalten kann. Abhängig von der Situation gilt diese Einschränkung für Tastaturbenutzer nicht immer. Im Abschnitt [Integrierte Tastaturoptimierung](#built-in-keyboard-optimization) erhalten Sie weitere Infos.

#### <a name="directional-navigation-a-namedirectional-navigation"></a>Direktionale Navigation <a name="directional-navigation">

Die direktionale Navigation wird über die UWP-Hilfsklasse [Focus Manager](https://docs.microsoft.com/uwp/api/Windows.UI.Xaml.Input.FocusManager) verwaltet, die die gedrückte Richtungstaste (Pfeiltaste, Steuerkreuz) verwendet und versucht, den Fokus in die entsprechende visuelle Richtung zu verlagern.

Wenn eine App nicht mehr den [Mausmodus](designing-for-tv.md#mouse-mode) verwendet, wird die direktionale Navigation anders als bei der Tastatur auf die gesamte Anwendung für Gamepad und Fernbedienung angewendet. Gehen Sie zum [Artikel zur XY-Fokusnavigation und -interaktion](designing-for-tv.md#xy-focus-navigation-and-interaction), um weitere Informationen zu direktionalen Navigationsoptimierungen für Gamepad und Fernbedienung zu erhalten.

**HINWEIS** Die Navigation mithilfe der TAB-TASTE der Tastatur wird nicht als direktionale Navigation betrachtet. Weitere Informationen finden Sie im Abschnitt [Tabstopps](#tab-stops).

<table>
  <tr>
    <td>
      <p>![direktionale Navigation](images/keyboard/directional-navigation.png)</p>
      <p>***Direktionale Navigation unterstützt*** </br>*Durch das Verwenden von Richtungstasten (Tastaturpfeile, Gamepad und Steuerkreuz der Fernbedienung) können Benutzer zwischen verschiedenen Steuerelementen navigieren.*</p>
    </td>
    <td>
      <p>![keine direktionale Navigation](images/keyboard/no-directional-navigation.png)</p>
      <p>***Direktionale Navigation nicht unterstützt*** </br>*Der Benutzer kann nicht zwischen verschiedenen Steuerelementen mit Richtungstasten navigieren. Andere Methoden zum Navigieren zwischen Steuerelementen (TAB-TASTE) sind nicht betroffen.*</p>
    </td>
  </tr>
</table>

### <a name="built-in-keyboard-optimization-a-namebuilt-in-keyboard-optimization"></a>Integrierte Tastaturoptimierung <a name="built-in-keyboard-optimization">

Je nach Layout und Steuerelementen können UWP-Apps speziell für die Tastatureingabe optimiert werden.

Das folgende Beispiel zeigt eine Gruppe von Listenelementen, Rasterelementen und Menüelementen, die zu einem einzelnen Tabstopp zugewiesen wurden (siehe Abschnitt [Tabstopps](#tab-stops)). Wenn die Gruppe im Fokus steht, wird die interne Navigation mit den Richtungspfeiltasten in der entsprechenden visuellen Reihenfolge ausgeführt (siehe Abschnitt [Navigation](#navigation)).

![Pfeiltastennavigation in einzelner Spalte](images/keyboard/single-column-arrow.png)

***Pfeiltastennavigation in einzelner Spalte***

![Pfeiltastennavigation in einzelner Zeile](images/keyboard/single-row-arrow.png)

***Pfeiltastennavigation in einzelner Zeile***

![Pfeiltastennavigation in mehreren Spalten und Zeilen](images/keyboard/multiple-column-and-row-navigation.png)

***Pfeiltastennavigation in mehreren Spalten und Zeilen***

#### <a name="wrapping-homogeneous-list-and-grid-view-items"></a>Umschließen homogener Listen- und Rasteransichtselemente

Die direktionale Navigation ist nicht immer die effizienteste Möglichkeit, durch mehrere Zeilen und Spalten der Listen- und Rasteransichtselemente zu navigieren.

**HINWEIS** Menüelemente sind in der Regel Listen mit einer Spalte, aber in einigen Fällen können spezielle Fokusregeln gelten (siehe [Popup-UI](#popup-ui)).

Listen- und Rasterobjekte können mit mehreren Zeilen und Spalten erstellt werden. Diese befinden sich in der Regel in einer zeilenweise absteigenden (Ausfüllen einer kompletten Zeile vor dem Ausfüllen der nächsten Zeile) oder spaltenweise absteigenden (Ausfüllen einer kompletten Spalte vor dem Ausfüllen der nächsten Spalte) Reihenfolge. Die zeilenweise oder spaltenweise absteigende Reihenfolge hängt von der Bildlaufrichtung ab, und Sie sollten sicherstellen, dass es keinen Konflikt mit der Elementreihenfolge gibt.

Wenn bei zeilenweise absteigender Reihenfolge (Eingabe der Elemente von links nach rechts und von oben nach unten) der Fokus auf dem letzten Element in einer Zeile liegt und die NACH-RECHTS-TASTE gedrückt wird, wird der Fokus zum ersten Element in der nächsten Zeile verlagert. Dieses Verhalten tritt auch umgekehrt auf: Wenn der Fokus auf dem ersten Element in einer Zeile liegt und die NACH-LINKS-TASTE gedrückt wird, wird der Fokus auf das letzte Element in der vorherigen Zeile verlagert.

Wenn bei spaltenweise absteigender Reihenfolge (Eingabe der Elemente von oben nach unten und von links nach rechts) der Fokus auf dem letzten Element in einer Spalte liegt und die NACH-UNTEN-TASTE gedrückt wird, wird der Fokus zum ersten Element in der nächsten Spalte verlagert. Dieses Verhalten tritt auch umgekehrt auf: Wenn der Fokus auf dem ersten Element in einer Spalte liegt und die NACH-OBEN-TASTE gedrückt wird, wird der Fokus auf das letzte Element in der vorherigen Spalte verlagert.

<table>
  <tr>
    <td>
      <p>![zeilenweise absteigende Tastaturnavigation](images/keyboard/row-major-keyboard.png)</p>
      <p>***Zeilenweise absteigende Tastaturnavigation***</p>
    </td>
    <td>
      <p>![spaltenweise absteigende Tastaturnavigation](images/keyboard/column-major-keyboard.png)</p>
      <p>***Spaltenweise absteigende Tastaturnavigation***</p>
    </td>
  </tr>
</table>

#### <a name="popup-ui-a-namepopup-ui"></a>Popup-UI <a name="popup-ui">

Wie bereits erwähnt, sollten Sie versuchen, sicherzustellen, dass die direktionale Navigation der visuellen Reihenfolge der Steuerelemente in der UI Ihrer App entspricht.

Einige Steuerelemente, z.B. `ContextMenu`, `AppBarOverflowMenu` und `AutoSuggest`, enthalten Popupmenüs, die an einer Position und in einer Richtung relativ zum primären Steuerelement angezeigt werden (auf Grundlage der verfügbaren Bildschirmfläche). Wenn beispielsweise nicht genügend Platz vorhanden ist, um das Menü nach unten (Standardrichtung) zu öffnen, wird es nach oben geöffnet. Es kann nicht garantiert werden, dass das Menü jedes Mal in dieselbe Richtung geöffnet wird.

<table>
  <td>![Befehlsleiste wird mit NACH-UNTEN-TASTE nach unten geöffnet](images/keyboard/command-bar-open-down.png)</td>
  <td>![Befehlsleiste wird mit NACH-OBEN-TASTE nach oben geöffnet](images/keyboard/command-bar-open-up.png)</td>
</table>

Wenn das Menü zum ersten Mal geöffnet wird (und vom Benutzer kein Element ausgewählt wurde), legt die NACH-UNTEN-TASTE den Fokus für diese Steuerelemente immer auf das erste Element im Menü. Die NACH-OBEN-TASTE legt den Fokus für diese Steuerelemente immer auf das letzte Element im Menü. Wenn das letzte Element ausgewählt und die NACH-UNTEN-TASTE gedrückt wird, wird der Fokus gleichermaßen auf das erste Element im Menü verlagert. Wenn das erste Element ausgewählt und die NACH-OBEN-TASTE gedrückt wird, wird der Fokus gleichermaßen auf das letzte Element im Menü verlagert

Sie sollten versuchen, diese Verhaltensweisen für Ihre benutzerdefinierten Steuerelemente zu emulieren. Ein Codebeispiel zum Implementieren dieses Verhaltens finden Sie in der Dokumentation zum [Verwalten der Fokusnavigation](managing-focus-navigation.md#popup-ui-code-sample) .

## <a name="test-your-app"></a>Testen der App

Testen Sie Ihre App mit allen unterstützten Eingabegeräten, um sicherzustellen, dass eine einheitliche und intuitive Navigation zu UI-Elementen möglich ist und keine unerwarteten Elemente die gewünschte Aktivierreihenfolge beeinträchtigen.

## <a name="related-articles"></a>Verwandte Artikel
* [Tastaturereignisse](keyboard-events.md)
* [Identifizieren von Eingabegeräten](identify-input-devices.md)
* [Reagieren auf das Vorhandensein der Bildschirmtastatur](respond-to-the-presence-of-the-touch-keyboard.md)
* [Beispiel für visuelle Fokuselemente](http://go.microsoft.com/fwlink/p/?LinkID=619895)

## <a name="appendix"></a>Anhang

### <a name="software-keyboard-a-nametouch-keyboard"></a>Softwaretastatur <a name="touch-keyboard">

Bei der Softwaretastatur handelt es sich um eine Tastatur auf dem Bildschirm, die der Benutzer anstelle der physischen Tastatur zum Eingeben von Daten per Touch, Maus, Zeichen-/Eingabestift oder mit einem anderen Zeigegerät verwenden kann. Ein Touchscreen ist nicht erforderlich. Auf einem Touchscreen kann diese Tastatur auch direkt zum Eingeben von Text verwendet werden. Auf Xbox One-Geräten müssen einzelne Tasten ausgewählt werden, indem Sie visuelle Fokuselemente verschieben oder Tastenkombinationen mit dem Gamepad oder der Fernbedienung verwenden.

![Windows10-Bildschirmtastatur](images/keyboard/kbdpcdefault.png)

***Windows10-Bildschirmtastatur***

![Windows 10 Phone-Bildschirmtastatur](images/keyboard/kbdwpdefault.png)

***Windows Phone 10-Bildschirmtastatur***

![Xbox one-Bildschirmtastatur](images/keyboard/xbox-onscreen-keyboard.png)

***Xbox One-Bildschirmtastatur***

Abhängig vom Gerät wird die Softwaretastatur angezeigt, wenn ein Textfeld oder ein anderes bearbeitbares Textsteuerelement im Fokus steht, oder wenn der Benutzer sie über das **Benachrichtigungs-Center**manuell aktiviert.

![Symbol der Bildschirmtastatur im Benachrichtigungs-Center](images/keyboard/touch-keyboard-notificationcenter.png)

Wenn Ihre App den Fokus programmgesteuert auf ein Texteingabesteuerelement festlegt, wird die Bildschirmtastatur nicht aufgerufen. Dadurch wird unerwartetes, nicht direkt vom Benutzer ausgelöstes Verhalten verhindert. Allerdings wird die Tastatur automatisch ausgeblendet, wenn der Fokus programmgesteuert auf ein nicht textuelles Eingabesteuerelement bewegt wird.

Die Bildschirmtastatur bleibt in der Regel sichtbar, während der Benutzer zwischen Steuerelementen in einem Formular navigiert. Dieses Verhalten kann je nach den anderen Steuerelementtypen innerhalb des Formulars variieren.

Im Folgenden finden Sie eine Liste der nicht bearbeitbaren Steuerelemente, die in einer Texteingabesitzung mit der Bildschirmtastatur den Fokus erhalten können, ohne dass die Tastatur ausgeblendet wird. Statt die Benutzeroberfläche unnötigerweise zu ändern und den Benutzer möglicherweise zu verwirren, bleibt die Bildschirmtastatur angezeigt, da der Benutzer wahrscheinlich zwischen diesen Steuerelementen und der Texteingabe über die Bildschirmtastatur hin und her wechselt.

-   Kontrollkästchen
-   Kombinationsfeld
-   Optionsfeld
-   Bildlaufleiste
-   Struktur
-   Strukturelement
-   Menü
-   Menüleiste
-   Menüelement
-   Symbolleiste
-   Liste
-   Listenelement

Hier finden Sie einige Beispiele für verschiedene Modi der Touch-Bildschirmtastatur. Das erste Bild zeigt das Standardlayout, das zweite das Daumenlayout. (Letzteres ist unter Umständen nicht in allen Sprachen verfügbar.)

![Bildschirmtastatur mit Standardlayout](images/keyboard/touchkeyboard-standard.png)

***Bildschirmtastatur mit Standardlayout***

![Bildschirmtastatur mit erweitertem Layout](images/keyboard/touchkeyboard-expanded.png)

***Bildschirmtastatur mit erweitertem Layout***

![Bildschirmtastatur mit Daumenlayout](images/keyboard/touchkeyboard-thumb.png)

***Bildschirmtastatur mit standardmäßigem Daumenlayout***

![Bildschirmtastatur mit numerischem Daumenlayout](images/keyboard/touchkeyboard-numeric-thumb.png)

***Bildschirmtastatur mit numerischem Daumenlayout***

Erfolgreiche Tastaturinteraktionen ermöglichen es Benutzern, einfache App-Szenarien nur über die Tastatur auszuführen; Benutzer können demnach über die Tastatur alle interaktiven Elemente erreichen und Standardfunktionen aktivieren. Eine Reihe von Faktoren kann den Erfolg beeinflussen, z. B. Tastaturnavigation, Tastenkombinationen für die Barrierefreiheit sowie Tastenkombinationen für erfahrene Benutzer.

**HINWEIS** Die Bildschirmtastatur unterstützt weder die Umschaltung noch die meisten Systembefehle.

#### <a name="on-screen-keyboard-a-nameosk"></a>Bildschirmtastatur <a name="osk">
Wie bei der Softwaretastatur handelt es sich bei der Bildschirmtastatur um eine visuelle Softwaretastatur, die Sie anstelle der physischen Tastatur zum Eingeben von Daten per Touch, Maus, Zeichen-/Eingabestift oder mit einem anderen Zeigegerät verwenden können. Ein Touchscreen ist nicht erforderlich. Die Bildschirmtastatur ist für Systeme ohne physische Tastatur oder für Benutzer vorgesehen, deren Mobilitätseinschränkungen die Verwendung herkömmlicher physischer Eingabegeräte verhindern. Die Bildschirmtastatur emuliert nahezu alle Funktionen der Hardwaretastatur.

Die Bildschirmtastatur kann auf der Seite „Tastatur“ unter „Einstellungen &gt; Erleichterte Bedienung“ aktiviert werden.

**HINWEIS** Die Bildschirmtastatur hat Priorität gegenüber der Touch-Tastatur. Diese wird nicht angezeigt, wenn die Bildschirmtastatur angezeigt wird.

![Bildschirmtastatur](images/keyboard/osk.png)

***Bildschirmtastatur***

Gehen Sie zur [Seite „Bildschirmtastatur“](https://support.microsoft.com/help/10762/windows-use-on-screen-keyboard), um weitere Informationen zur Bildschirmtastatur zu erhalten.
