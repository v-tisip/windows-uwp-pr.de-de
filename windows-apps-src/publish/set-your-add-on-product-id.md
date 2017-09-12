---
author: jnHs
Description: "Beim Erstellen eines neuen Add-Ons im WindowsDevCenter-Dashboard müssen Sie einen Produkttyp angeben und eine Produkt-ID zuweisen."
title: "Festlegen von Produkt-ID und Produkttyp für das Add-On"
ms.assetid: 59497B0F-82F0-4CEE-B628-040EF9ED8D3D
ms.author: wdg-dev-content
ms.date: 06/28/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.openlocfilehash: 136077edcf4704f3ea71416719e7c37db43dafda
ms.sourcegitcommit: 6c6f3c265498d7651fcc4081c04c41fafcbaa5e7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2017
---
# <a name="set-your-add-on-product-type-and-product-id"></a>Festlegen von Produkt-ID und Produkttyp für das Add-On

Ein Add-On muss einer App zugeordnet sein, die bereits im Dashboard erstellt (aber noch nicht unbedingt übermittelt) wurde. Die Schaltfläche zum **Erstellen eines neuen Add-Ons** finden Sie entweder auf der App-Seite **Übersicht** oder unter **Add-Ons**.

Nachdem Sie **Ein neues Add-On erstellen** ausgewählt haben, werden Sie aufgefordert, einen Produkttyp anzugeben und eine Produkt-ID für Ihr Add-On zuzuweisen.

## <a name="product-type"></a>Produkttyp

Zunächst müssen Sie angeben, welche Art von Add-On Sie anbieten. Diese Auswahloption bezieht sich darauf, wie das Add-On vom Kunden genutzt werden kann.

> [!NOTE]
> Nachdem Sie diese Seite gespeichert haben, um das Add-On zu erstellen, kann der Produkttyp nicht mehr geändert werden. Sollten Sie den falschen Produkttyp ausgewählt haben, können Sie die in Bearbeitung befindliche Add-On-Übermittlung jederzeit löschen und ein neues Add-On erstellen.

<span id="durable" />
### <a name="durable"></a>Gebrauchsgut

Wählen Sie **Dauerhaft** als Produkttyp Ihres Add-Ons aus, wenn es in der Regel nur einmal erworben wird. Diese dauerhaften Add-Ons werden häufig verwendet, um zusätzliche Funktionen in einer App freizuschalten.

Die standardmäßige **Produktlebenszeit** dauerhafter Add-Ons ist **Unbegrenzt**. Das Add-On läuft also niemals ab. Sie können die Option **Produktlebensdauer** im Schritt [Einstellungen](enter-add-on-properties.md) des Add-On-Übermittlungsprozesses auf eine andere Zeitdauer festlegen. Wenn Sie dies tun, läuft das Add-On nach der angegebenen Dauer ab (mögliche Optionen sind 1 bis 365Tage). Der Kunde kann es dann erneut kaufen, nachdem es abgelaufen ist.

<span id="consumable" />
### <a name="consumable"></a>Verbrauchsprodukte

Wenn das Add-On erworben werden kann, verwendet (verbraucht) und dann erneut gekauft wird, sollten Sie einen der **konsumierbaren** Typen wählen. Konsumierbare Add-Ons bzw. Endverbraucher-Add-Ons werden häufig für Dinge wie spielinterne Währungen (Gold, Münzen usw.) verwendet, die in bestimmten Mengen erworben und vom Kunden aufgebraucht werden. Weitere Informationen zum Hinzufügen von konsumierbaren Add-Ons in Ihrer App finden Sie unter [Unterstützen von Endverbraucher-Add-On-Käufen](../monetize/enable-consumable-add-on-purchases.md).

Es gibt zwei Arten konsumierbarer Add-Ons:
- **Von Entwicklern verwaltetes Endverbraucher-Add-On**: Saldo und Erfüllung müssen in der App verwaltet werden. Wird auf allen Betriebssystemen unterstützt.
- **Vom Store verwaltetes Endverbraucher-Add-On:** Der Saldo wird von Microsoft für alle Geräte des Kunden verfolgt, auf denen Windows10 (Version 1607 oder höher) ausgeführt wird; nicht unterstützt unter früheren Betriebssystemversionen. Um diese Option zu verwenden, muss das übergeordnete Produkt mit Windows10 SDK Version14393 oder höher kompiliert werden. Beachten Sie außerdem, dass Sie erst dann vom Store verwaltete Endverbraucher-Add-Ons zum Store übermitteln können, wenn das übergeordnete Produkt veröffentlicht wurde (es ist jedoch möglich, jederzeit die Übermittlung in Ihrem Dashboard zu erstellen und damit bereits zu arbeiten). Sie müssen die Menge für Ihr vom Store verwaltetes Endverbraucher-Add-on im Schritt **Eigenschaften** der Übermittlung eingeben.

<span id="subscription" />
### <a name="subscription"></a>Abonnement

Wenn Sie Ihre Kunden in regelmäßigen Abständen für Ihre Add-On in Rechnung stellen möchten, wählen Sie **Abonnement** aus.

> [!NOTE]
> Die Fähigkeit zum Erstellen von Abonnement-Add-Ons ist derzeit nur für eine Gruppe von Entwicklerkonten verfügbar, die am frühen Adoption-Programm teilnehmen. Wir stellen Abonnement-Add-Ons für alle Entwicklerkonten in Zukunft zur Verfügung und wir stellen Ihnen diese vorläufige Dokumentation jetzt zur Verfügung, um Entwicklern eine Vorschau dieser Funktion zu ermöglichen. Weitere Informationen finden Sie unter [Abonnement-Add-Ons für Ihre App aktivieren](../monetize/enable-subscription-add-ons-for-your-app.md).

Nachdem ein abonniertes Add-On von einem Kunden erworben wurde, kann er auch weiterhin in regelmäßigen Abständen in Rechnung gestellt werden, um das Add-On weiter verwenden zu können. Der Kunde kann das Abonnement jederzeit kündigen, um weitere Gebühren zu vermeiden. Sie müssen im Schritt **Eigenschaften** der Übermittlung den Abonnementzeitraum festlegen und ob Sie eine kostenlose Testversion anbieten oder nicht.

Abonnierte Add-Ons werden nur für Kunden mit Windows10, Version 1607 oder höher unterstützt. Um diese Option zu verwenden, muss das übergeordnete Produkt mit Windows10 SDK Version14393 oder höher kompiliert werden. Zudem muss statt der API im **Windows.ApplicationModel.Store**-Namespace die im **Windows.Services.Store**-Namespace verwendete In-App-Kauf-API verwendet werden. Weitere Informationen zu den Unterschieden zwischen diesen Namespaces finden Sie unter [In-App-Käufe und Testversionen](../monetize/in-app-purchases-and-trials.md).

Sie müssen das übergeordnete Produkt übermitteln, bevor Sie das abonnierte Add-Ons im Store veröffentlichen können (es ist jedoch möglich, jederzeit die Übermittlung in Ihrem Dashboard zu erstellen und damit bereits zu arbeiten).

## <a name="product-id"></a>Produkt-ID

Unabhängig vom Produkt, das Sie auswählen, müssen Sie eine eindeutige Produkt-ID für Ihr Add-On angeben. Dieser Name wird verwendet, um das Add-On im Dashboard zu identifizieren, und Sie können diese ID verwenden, [um sich auf das Add-On in Ihrem Code zu beziehen](../monetize/in-app-purchases-and-trials.md#how-to-use-product-ids-for-add-ons-in-your-code).

Folgende Dinge sollten bei der Wahl einer Produkt-ID beachtet werden:

-   Die Produkt-ID ist für Kunden nicht sichtbar. (Sie können später [einen Titel und eine Beschreibung](create-add-on-descriptions.md) eingeben, die für Kunden sichtbar sind.)
-   Sie können die Produkt-ID eines Add-Ons nach der Veröffentlichung nicht ändern oder löschen.
-   Eine Produkt-ID darf maximal 100 Zeichen umfassen.
-   Folgende Zeichen dürfen nicht in der Produkt-ID enthalten sein: **&lt; &gt; \* % & : \\ ? + ,**
-   Um das Add-On unter allen Betriebssystemversionen anzubieten, dürfen nur alphanumerische Zeichen, Punkte und/oder Unterstriche verwendet werden. Bei Verwendung anderer Zeichen kann das Add-On von Kunden mit Windows Phone8.1 oder früheren Versionen nicht erworben werden.
-   Eine Produkt-ID muss zwar nicht im Windows Store, aber für Ihr Entwicklerkonto eindeutig sein.
 
