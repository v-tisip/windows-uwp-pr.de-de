---
author: jnHs
Description: Add-ons are published through the Windows Dev Center dashboard.
title: Add-On-Übermittlungen
ms.assetid: E175AF9E-A1D4-45DF-B353-5E24E573AE67
ms.author: wdg-dev-content
ms.date: 05/09/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, IAP, In-App-Kauf, In-App-Produkt, IAP-Übermittlung
ms.localizationpriority: medium
ms.openlocfilehash: 37d05722578ed945fbf75040f96360bb569c6d06
ms.sourcegitcommit: 72835733ec429a5deb6a11da4112336746e5e9cf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "5161480"
---
# <a name="add-on-submissions"></a>Add-On-Übermittlungen

Add-Ons (auch als In-App-Produkte bezeichnet) sind ergänzende Elemente für Ihre App, die von Kunden erworben werden können. Ein Add-on kann ein lustiges sein, die neue Funktion, eine neue gamelevel oder etwas anderes Meinung Benutzer Spaß daran haben. Add-Ons sind nicht nur eine gute Möglichkeit, um Geld zu verdienen, sondern fördern zudem die Kundeninteraktion und -bindung.

Add-Ons werden über das Windows Dev Center-Dashboard veröffentlicht. Sie müssen die [Add-Ons außerdem im Code Ihrer App aktivieren](../monetize/in-app-purchases-and-trials.md).

Der erste Schritt bei der Add-On-Übermittlung besteht darin, das Add-On im Dashboard zu erstellen, indem Sie den [Produkt-Typ und die Produkt-ID definieren](set-your-add-on-product-id.md). Danach müssen Sie eine Übermittlung erstellen, damit Ihr Add-on über den Microsoft Store erworben werden kann. Sie können ein Add-On gleichzeitig mit [Ihrer App einreichen](app-submissions.md) oder unabhängig vorgehen. Außerdem können Sie [Updates](#updating-an-add-on-after-publication) für Add-Ons ausführen, nachdem die App im Store eingetragen wurde, ohne dass die App erneut übermittelt werden muss.

> [!NOTE]
> In diesem Abschnitt der Dokumentation wird das Übermitteln von Add-Ons im Dev Center-Dashboard beschrieben. Alternativ dazu können Sie auch die [Microsoft Store-Übermittlungs-API](../monetize/create-and-manage-submissions-using-windows-store-services.md) verwenden, um Add-On-Übermittlungen zu automatisieren.


## <a name="checklist-for-submitting-an-add-on"></a>Prüfliste für die Übermittlung eines Add-Ons

Hier finden Sie eine Liste mit den Informationen, die Sie beim Erstellen Ihrer Add-On-Übermittlung angeben können. Die erforderlichen Elemente sind im Folgenden aufgeführt. Einige Elemente sind optional oder verfügen bereits über Standardwerte, die Sie nach Bedarf ändern können.


### <a name="create-a-new-add-on-page"></a>Erstellen einer neuen Add-On-Seite

| Feldname                    | Hinweise                            |
|-------------------------------|----------------------------------|
| [**Produkttyp**](set-your-add-on-product-id.md#product-type)      | Nötig |  
| [**Produkt-ID**](set-your-add-on-product-id.md#product-id)          | Erforderlich |        


### <a name="properties-page"></a>Seite „Eigenschaften“

| Feldname                    | Hinweise                              |   
|-------------------------------|------------------------------------|
| [**Produktlebensdauer**](enter-add-on-properties.md#product-lifetime)  | Erforderlich, wenn der Produkttyp **Gebrauchsgut** lautet. Gilt nicht für andere Produkttypen. |
| [**Menge**](enter-add-on-properties.md#quantity)  | Erforderlich, wenn der Produkttyp **Vom Store verwalteter Verbrauchsartikel** lautet. Gilt nicht für andere Produkttypen. |
| [**Abonnementdauer**](enter-add-on-properties.md#subscription-period)          | Erforderlich, wenn der Produkttyp **Dauerauftrag** lautet. Gilt nicht für andere Produkttypen.       |  
| [**Kostenlose Testversion**](enter-add-on-properties.md#free-trial)          | Erforderlich, wenn der Produkttyp **Dauerauftrag** lautet. Gilt nicht für andere Produkttypen.       |
| [**Inhaltstyp**](enter-add-on-properties.md#content-type)          | Erforderlich    |               
| [**Schlüsselwörter**](enter-add-on-properties.md#keywords)                  | Optional (bis zu zehnSchlüsselwörter mit jeweils maximal 30Zeichen) |
| [**Benutzerdefinierte Entwicklerdaten**](enter-add-on-properties.md#custom-developer-data)   | Optional (maximal 3.000Zeichen)            |


### <a name="pricing-and-availability-page"></a>Seite „Preise und Verfügbarkeit“

| Feldname                    | Hinweise                                       |
|-------------------------------|---------------------------------------------|
| [**Märkte**](set-add-on-pricing-and-availability.md#markets)  | Standard: alle möglichen Märkte |
| [**Sichtbarkeit**](set-add-on-pricing-and-availability.md#visibility)   | Standard: Zum Kauf erhältlich. Kann im App-Eintrag angezeigt werden |
| [**Zeitplan**](set-add-on-pricing-and-availability.md#schedule)    | Standard: so schnell wie möglich veröffentlichen
| [**Preise**](set-add-on-pricing-and-availability.md#pricing)                | Nötig                                    |
| [**Sonderpreise**](put-apps-and-add-ons-on-sale.md)               | Optional                    |


### <a name="store-listings"></a>Store-Einträge

Ein Store-Eintrag ist erforderlich. Es wird empfohlen, für jede von der App unterstützte [Sprache](create-add-on-store-listings.md#store-listing-languages) Store-Einträge anzugeben.

| Feldname                    | Hinweise                                       |
|-------------------------------|---------------------------------------------|
| [**Titel**](create-add-on-store-listings.md#title)                    | Erforderlich (max. 100 Zeichen)           |
| [**Beschreibung**](create-add-on-store-listings.md#description)       | Optional (max. 200 Zeichen)            |
| [**Symbol**](create-add-on-store-listings.md#icon)                    | Optional (PNG, 300x300 Pixel)            |


Nachdem Sie diese Informationen eingegeben haben, klicken Sie auf **An Store einreichen**. In den meisten Fällen dauert der Zertifizierungsprozess etwa eine Stunde. Danach wird Ihr Add-On im Store veröffentlicht und steht für Kunden zum Kauf bereit.

> [!NOTE]
> Das Add-On muss außerdem im Code Ihrer App implementiert werden. Weitere Informationen finden Sie unter [In-App-Käufe und Testversionen](../monetize/in-app-purchases-and-trials.md).


## <a name="updating-an-add-on-after-publication"></a>Aktualisieren eines Add-Ons nach der Veröffentlichung

Sie können ein veröffentlichtes Add-On jederzeit ändern. Add-On-Änderungen werden eingereicht und unabhängig von Ihrer app veröffentlicht werden, damit Sie in der Regel nicht die gesamte app aktualisieren, um ein Add-on z. B. zum Aktualisieren des Preises oder der Beschreibung ändern müssen.

> [!IMPORTANT]
> Wenn die App für Kunden unter Windows8.x verfügbar ist, müssen Sie eine neue App-Übermittlung erstellen und veröffentlichen, um die Add-On-Updates für diese Kunden sichtbar zu machen. Auch wenn Sie neue Add-Ons einer App für Windows 8.x hinzufügen, nachdem die App veröffentlicht wurde, müssen Sie den App-Code aktualisieren, um auf diese Add-Ons zu verweisen, und die App dann erneut übermitteln. Andernfalls sind die neuen Add-Ons nicht für Kunden unter Windows 8.x sichtbar.

Wechseln Sie zum Übermitteln von Updates im Dashboard zur Seite des Add-Ons, und klicken Sie auf **Aktualisieren**. Dadurch entsteht eine neue Übermittlung für das Add-on, wobei die Informationen aus der vorherigen Übermittlung als Ausgangspunkt. Ändern Sie wie folgt, und klicken Sie dann auf **an den Store übermitteln**.

Wenn Sie ein zuvor angebotenes Add-On entfernen möchten, können Sie dies tun, indem Sie eine neue Übermittlung erstellen und die Option [Verteilung und Sichtbarkeit](set-add-on-pricing-and-availability.md) unter **Im Store ausgeblendet** in **Beenden des Erwerbs**. Achten Sie darauf, den App-Code entsprechend zu aktualisieren, um auch Verweise auf das Add-On zu entfernen (wenn Ihre App frühere Versionen von Windows8.1 unterstützt, gilt diese Sichtbarkeitseinstellung nicht für diese Kunden).
