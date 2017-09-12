---
author: jnHs
Description: "Auf der Seite App-Eigenschaften des App-Übermittlungsprozesses können Sie die Kategorie Ihrer App festlegen sowie Hardwareeinstellungen und weitere Deklarationen angeben."
title: Eingeben von App-Eigenschaften
ms.assetid: CDE4AF96-95A0-4635-9D07-A27B810CAE26
ms.author: wdg-dev-content
ms.date: 08/03/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: e4d391d551cf4e41853a1aac0e4b5be8bf0b0c3f
ms.sourcegitcommit: 968187e803a866b60cda0528718a3d31f07dc54c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2017
---
# <a name="enter-app-properties"></a>Eingeben von App-Eigenschaften

Auf der Seite **Eigenschaften** des [App-Übermittlungsprozesses](app-submissions.md) können Sie die Kategorie Ihrer App festlegen sowie Hardwareeinstellungen und weitere Deklarationen angeben. Wir stellen Ihnen hier die auf dieser Seite verfügbaren Optionen vor und informieren Sie darüber, was Sie bei der Eingabe dieser Informationen beachten sollten.

## <a name="category-and-subcategory"></a>Kategorie und Unterkategorie

In diesem Abschnitt geben Sie die Kategorie (und ggf. eine Unterkategorie) an, die im Store zur Kategorisierung der App verwendet werden soll. Die Angabe einer Kategorie ist für die Einreichung Ihrer App erforderlich.

Weitere Informationen finden Sie unter [Kategorie- und Unterkategorietabelle](category-and-subcategory-table.md).

## <a name="game-settings"></a>Einstellungen für Spiele

Dieser Abschnittwird nur angezeigt, wenn Sie als Kategorie des Produkts **Spiele** ausgewählt haben. Hier können Sie angeben, welche Features von Ihrem Spiel unterstützt werden. Alle Informationen, die Sie in diesem Abschnitt angeben, werden im Store-Eintrag des Produkts angezeigt.

Wenn Ihr Spiel eine Multiplayer-Option unterstützt, müssen Sie die minimale und maximale Anzahl der Spieler für eine Sitzung angeben. Sie können nicht mehr als 1.000 minimale oder maximale Spieler eingeben.

Die **Plattformübergreifende Multiplayer-Option** bedeutet, dass das Spiel Multiplayer-Sitzungen zwischen Spielern auf Windows10-PCs und Xbox unterstützt.


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

Zusätzlich wird empfohlen, der App Laufzeitprüfungen für die angegebene Hardware hinzuzufügen, da vom Store nicht immer erkannt werden kann, ob ein Kundengerät über das ausgewählte Feature verfügt, sodass Kunden die App trotz der Warnung herunterladen können.

> [!TIP]
> Wenn Sie verhindern möchten, dass Ihre UWP-App auf ein Gerät heruntergeladen wird, das die Mindestanforderungen für die Arbeitsspeicherkapazität oder DirectX-Ebene nicht erfüllt, können Sie die Mindestanforderungen in der Datei „StoreManifest.xml“ festlegen. Weitere Informationen finden Sie unter [StoreManifest-Schema (Windows 10)](https://msdn.microsoft.com/library/windows/apps/mt617335).


