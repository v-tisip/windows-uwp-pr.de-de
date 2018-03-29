---
author: jnHs
Description: The App properties page of the app submission process lets you define your app's category and indicate hardware preferences or other declarations.
title: Eingeben von App-Eigenschaften
ms.assetid: CDE4AF96-95A0-4635-9D07-A27B810CAE26
ms.author: wdg-dev-content
ms.date: 01/24/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Spieleinstellungen, Anzeigemodus, Systemanforderungen, Hardwareanforderungen, Mindestanforderungen an die Hardware, empfohlene Hardware
ms.localizationpriority: high
ms.openlocfilehash: 8ecdeb0dd4ebba83a387666ab87067ff419a9303
ms.sourcegitcommit: 8d9d4f17e272b78e38b346f846b96260c922bbb2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2018
---
# <a name="enter-app-properties"></a>Eingeben von App-Eigenschaften

Auf der Seite **Eigenschaften** des [App-Übermittlungsprozesses](app-submissions.md) können Sie die Kategorie Ihrer App festlegen sowie andere Informationen und weitere Deklarationen angeben. Achten Sie darauf, dass Sie auf dieser Seite vollständige und genaue Details zu Ihrer App angeben.


## <a name="category-and-subcategory"></a>Kategorie und Unterkategorie

Geben Sie hier die Kategorie (und ggf. eine Unterkategorie/Genre) an, die im Store zur Kategorisierung der App verwendet werden soll. Die Angabe einer Kategorie ist für die Einreichung Ihrer App erforderlich.

Weitere Informationen finden Sie unter [Kategorie- und Unterkategorietabelle](category-and-subcategory-table.md).


## <a name="game-settings"></a>Einstellungen für Spiele

Dieser Abschnittwird nur angezeigt, wenn Sie als Kategorie des Produkts **Spiele** ausgewählt haben. Hier können Sie angeben, welche Features von Ihrem Spiel unterstützt werden. Alle Informationen, die Sie in diesem Abschnitt angeben, werden im Store-Eintrag des Produkts angezeigt.

Wenn Ihr Spiel eine Multiplayer-Option unterstützt, müssen Sie die minimale und maximale Anzahl der Spieler für eine Sitzung angeben. Sie können nicht mehr als 1.000 minimale oder maximale Spieler eingeben.

Die **Plattformübergreifende Multiplayer-Option** bedeutet, dass das Spiel Multiplayer-Sitzungen zwischen Spielern auf Windows10-PCs und Xbox unterstützt.


## <a name="display-mode"></a>Anzeigemodus

In diesem Abschnitt können Sie angeben, ob Ihr Produkt in einer immersiven Ansicht (nicht nur 2D) für [Windows Mixed Reality](https://developer.microsoft.com/windows/mixed-reality) auf PC bzw. HoloLens-Geräten geeignet ist. Wenn Sie dies bestätigen, müssen Sie ebenfalls folgendes angeben:
- Wählen Sie entweder **Mindesthardwareanforderungen** oder **Empfohlene Hardware** für **immersives Windows Mixed Reality-Headset** unter [Systemanforderungen](#system-requirements) auf dem unten angezeigten Abschnitt der Seite **Eigenschaften** aus.
- Geben Sie **Boundary setup** an (wenn ein PC ausgewählt wurde), damit Benutzer wissen, ob es nur einer sitzenden oder stehenden Position verwendet werden soll, oder ob der Benutzer sich bei der Verwendung bewegen kann. 

Wenn Sie **Spiele** als Kategorie des Produkts ausgewählt haben, werden zusätzliche Optionen in der Auswahl des **Anzeigemodus** angezeigt, mit denen Sie angeben können, ob Ihr Produkt eine 4K-Auflösung der Videoausgabe, High Dynamic Range (HDR) oder die variable Aktualisierungsratenanzeige unterstützt.

Wenn Ihr Produkt keine dieser Anzeigemodioptionen unterstützt, lassen Sie alle Kontrollkästchen leer.


## <a name="product-declarations"></a>Produktdeklarationen

Über die Kontrollkästchen in diesem Abschnitt geben Sie an, ob Deklarationen auf Ihre App zutreffen. Dies kann sich darauf auswirken, wie Ihre App angezeigt wird, ob sie bestimmten Kunden angeboten wird und wie sie von Kunden genutzt werden kann.

Weitere Informationen finden Sie unter [Produktdeklarationen](app-declarations.md).

## <a name="system-requirements"></a>Systemanforderungen

In diesem Abschnitt können Sie angeben, ob bestimmte Hardwarefeatures erforderlich sind oder empfohlen werden, um Ihre App ordnungsgemäß auszuführen und zu verwenden. Sie können das Kontrollkästchen für jedes Hardwareelement aktivieren (oder die entsprechende Option angeben), für das Sie **Mindesthardwareanforderungen** und/oder **Empfohlene Hardware** festlegen möchten.

Wenn Sie eine Auswahl für **Empfohlene Hardware** festlegen, werden diese Elemente Kunden unter Windows10, Version 1607 oder höher, in Ihrem Store-Eintrag für das Produkt als empfohlene Hardware angezeigt. Kunden mit älteren Betriebssystemversionen werden diese Informationen nicht angezeigt.

Wenn Sie eine Auswahl für **Mindesthardwareanforderungen** treffen, werden diese Elemente Kunden unter Windows10, Version 1607 oder höher, in Ihrem Store-Eintrag für das Produkt als erforderliche Hardware angezeigt. Kunden mit älteren Betriebssystemversionen werden diese Informationen nicht angezeigt. Im Store wird mit dem Eintrag Ihrer App möglicherweise auch eine Warnung für Kunden angezeigt, deren Gerät die Hardwareanforderungen nicht erfüllt. Dies hindert Kunden nicht daran, Ihre App auf Geräte ohne geeignete Hardware herunterzuladen. Allerdings können sie Ihre App auf diesen Geräten nicht bewerten oder eine Rezension für diese verfassen. 

Das Verhalten für Kunden variiert abhängig von den spezifischen Anforderungen und der Windows-Version des Kunden:

- **Für Kunden mit Windows10, Version 1607 oder höher:**
     - Alle Mindest- und empfohlenen Anforderungen werden im Store-Eintrag angezeigt.
     - Der Store überprüft alle Mindestanforderungen und zeigt eine Warnung für Kunden an, deren Gerät die Anforderungen nicht erfüllt.
- **Für Kunden mit früheren Versionen von Windows10:**
     - Für die meisten Kunden werden alle Mindest- und empfohlenen Hardwareanforderungen im Store-Eintrag angezeigt (Kunden mit älteren Versionen des Store-Clients werden jedoch nur die Mindesthardwareanforderungen angezeigt).
     - Der Store versucht, Elemente zu überprüfen, die Sie als **Mindesthardwareanforderungen** kennzeichnen, mit Ausnahme von **Speicher**, **DirectX**, **Videospeicher**, **Grafiken** und **Prozessor**. Diese Optionen werden nicht überprüft, und Kunden mit Geräten, die diese Anforderungen nicht erfüllen, wird keine Warnung angezeigt. 
- **Für Kunden mit Windows8.x bzw. Windows Phone8.x und früheren Versionen:**
     - Wenn Sie das Feld **Mindesthardwareanforderungen** für **Touchscreen** aktivieren, wird diese Anforderung im Store-Eintrag Ihrer App angezeigt und Kunden auf Geräten ohne Touchscreen wird eine Warnung angezeigt, wenn sie versuchen, die App herunterladen. Es werden keine weiteren Anforderungen überprüft oder in Ihrem Store-Eintrag angezeigt.

Zusätzlich wird empfohlen, der App Laufzeitprüfungen für die angegebene Hardware hinzuzufügen, da vom Store nicht immer erkannt werden kann, ob ein Kundengerät über das ausgewählte Feature verfügt, sodass Kunden die App trotz der Warnung herunterladen können. Wenn Sie verhindern möchten, dass Ihre UWP-App auf ein Gerät heruntergeladen wird, das die Mindestanforderungen für die Arbeitsspeicherkapazität oder DirectX-Ebene nicht erfüllt, können Sie die Mindestanforderungen in der [Datei StoreManifest XML](https://docs.microsoft.com/uwp/schemas/storemanifest/storemanifestschema2015/schema-root).

> [!TIP]
> Wenn für Ihr Produkt zusätzliche Elemente erforderlich sind, die nicht in diesem Abschnitt aufgeführt sind, damit es ordnungsgemäß ausgeführt werden kann wie z.B. 3D-Drucker oder USB-Geräte, können Sie ebenfalls [Weitere Systemanforderungen](create-app-store-listings.md#additional-system-requirements) bei der Erstellung Ihrer Store-Eintrags angeben.





