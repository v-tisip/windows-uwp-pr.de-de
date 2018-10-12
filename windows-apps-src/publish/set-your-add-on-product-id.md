---
author: jnHs
Description: When you create a new add-on in the Windows Dev Center dashboard, you need to specify a product type and assign it a product ID.
title: Festlegen von Produkt-ID und Produkttyp für das Add-On
ms.assetid: 59497B0F-82F0-4CEE-B628-040EF9ED8D3D
ms.author: wdg-dev-content
ms.date: 01/12/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Add-Ons, IAP, dauerhaft, konsumbierbar, Abonnement, Produkt, Typ, Produkt-ID, In-App-Kauf, In-App-Produkt
ms.localizationpriority: medium
ms.openlocfilehash: 0673048fc9a1ed8fb7c439607ebc4197039699e9
ms.sourcegitcommit: 933e71a31989f8063b020746fdd16e9da94a44c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2018
ms.locfileid: "4538148"
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

Wenn das Add-On erworben werden kann, verwendet (verbraucht) und dann erneut gekauft wird, sollten Sie einen der **konsumierbaren** Typen wählen. Konsumierbare Add-Ons bzw. Endverbraucher-Add-Ons werden häufig für Dinge wie spielinterne Währungen (Gold, Münzen usw.) verwendet, die in bestimmten Mengen erworben und vom Kunden aufgebraucht werden. Weitere Informationen finden Sie unter [Unterstützen von Käufen konsumierbarer Add-Ons](../monetize/enable-consumable-add-on-purchases.md).

Es gibt zwei Arten konsumierbarer Add-Ons:
- **Von Entwicklern verwaltetes Endverbraucher-Add-On**: Saldo und Erfüllung müssen in der App verwaltet werden. Wird auf allen Betriebssystemen unterstützt.
- **Vom Store verwaltetes Endverbraucher-Add-On:** Der Saldo wird von Microsoft für alle Geräte des Kunden verfolgt, auf denen Windows10 (Version 1607 oder höher) ausgeführt wird; nicht unterstützt unter früheren Betriebssystemversionen. Um diese Option zu verwenden, muss das übergeordnete Produkt mit Windows10 SDK Version14393 oder höher kompiliert werden. Beachten Sie außerdem, dass Sie erst dann vom Store verwaltete Endverbraucher-Add-Ons zum Store übermitteln können, wenn das übergeordnete Produkt veröffentlicht wurde (es ist jedoch möglich, jederzeit die Übermittlung in Ihrem Dashboard zu erstellen und damit bereits zu arbeiten). Sie müssen die Menge für Ihr vom Store verwaltetes Endverbraucher-Add-on im Schritt **Eigenschaften** der Übermittlung eingeben.

<span id="subscription" />

### <a name="subscription"></a>Abonnement

Wenn Sie Ihre Kunden in regelmäßigen Abständen für Ihre Add-On in Rechnung stellen möchten, wählen Sie **Abonnement** aus.

Nachdem ein abonniertes Add-On von einem Kunden erworben wurde, kann er auch weiterhin in regelmäßigen Abständen in Rechnung gestellt werden, um das Add-On weiter verwenden zu können. Der Kunde kann das Abonnement jederzeit kündigen, um weitere Gebühren zu vermeiden. Sie müssen im Schritt **Eigenschaften** der Übermittlung den Abonnementzeitraum festlegen und ob Sie eine kostenlose Testversion anbieten oder nicht.

Abonnierte Add-Ons werden nur für Kunden mit Windows10, Version 1607 oder höher unterstützt. Um diese Option zu verwenden, muss das übergeordnete Produkt mit Windows10 SDK Version14393 oder höher kompiliert werden. Zudem muss statt der API im **Windows.ApplicationModel.Store**-Namespace die im **Windows.Services.Store**-Namespace verwendete In-App-Kauf-API verwendet werden. Weitere Informationen finden Sie unter [Abonnement-Add-Ons für Ihre App aktivieren](../monetize/enable-subscription-add-ons-for-your-app.md).

Sie müssen das übergeordnete Produkt übermitteln, bevor Sie abonnierte Add-Ons im Store veröffentlichen können (es ist jedoch möglich, jederzeit die Übermittlung in Ihrem Dashboard zu erstellen und damit bereits zu arbeiten).

## <a name="product-id"></a>Produkt-ID

Unabhängig vom Produkt, das Sie auswählen, müssen Sie eine eindeutige Produkt-ID für Ihr Add-On angeben. Dieser Name wird verwendet, um das Add-On im Dashboard zu identifizieren, und Sie können diese ID verwenden, [um sich auf das Add-On in Ihrem Code zu beziehen](../monetize/in-app-purchases-and-trials.md#how-to-use-product-ids-for-add-ons-in-your-code).

Folgende Dinge sollten bei der Wahl einer Produkt-ID beachtet werden:

-   Die Produkt-ID ist für Kunden nicht sichtbar. (Sie können später [einen Titel und eine Beschreibung](create-add-on-descriptions.md) eingeben, die für Kunden sichtbar sind.)
-   Sie können die Produkt-ID eines Add-Ons nach der Veröffentlichung nicht ändern oder löschen.
-   Eine Produkt-ID darf maximal 100 Zeichen umfassen.
-   Folgende Zeichen dürfen nicht in der Produkt-ID enthalten sein: **&lt; &gt; \* % & : \\ ? + ,**
-   Um das Add-On unter allen Betriebssystemversionen anzubieten, dürfen nur alphanumerische Zeichen, Punkte und/oder Unterstriche verwendet werden. Bei Verwendung anderer Zeichen kann das Add-On von Kunden mit Windows Phone8.1 oder früheren Versionen nicht erworben werden.
-   Eine Produkt-ID muss zwar nicht im Microsoft Store, aber für Ihr Entwicklerkonto eindeutig sein.
 
