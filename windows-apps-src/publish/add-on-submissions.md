---
author: jnHs
Description: "Add-Ons werden über das Windows Dev Center-Dashboard veröffentlicht."
title: "Add-On-Übermittlungen"
ms.assetid: E175AF9E-A1D4-45DF-B353-5E24E573AE67
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP"
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: e7d13a55ba545758e01452103c3380ac67ad6610
ms.lasthandoff: 02/07/2017

---

# <a name="add-on-submissions"></a>Add-On-Übermittlungen

Add-Ons (auch als In-App-Produkte bezeichnet) sind ergänzende Elemente für Ihre App, die von Kunden erworben werden können. Ein Add-On kann ein lustiges neues Add-On-Feature, ein neues Gamelevel oder etwas anderes sein, von dem Sie denken, dass Benutzer Spaß daran haben. Add-Ons sind nicht nur eine gute Möglichkeit, um Geld zu verdienen, sondern fördern zudem die Kundeninteraktion und -bindung.

Add-Ons werden über das Windows Dev Center-Dashboard veröffentlicht. Sie müssen die [Add-Ons außerdem im Code Ihrer App aktivieren](../monetize/in-app-purchases-and-trials.md).

Der erste Schritt bei der Add-On-Übermittlung besteht darin, das Add-On im Dashboard zu erstellen, indem Sie den [Produkt-Typ und die Produkt-ID definieren](set-your-add-on-product-id.md). Danach können Sie eine Übermittlung erstellen, damit Ihr Add-On über den Windows Store erworben werden kann. Sie können ein Add-On gleichzeitig mit [Ihrer App einreichen](app-submissions.md) oder unabhängig vorgehen. Außerdem können Sie [Updates](#updating-an-add-on-after-submission) für Add-Ons ausführen, nachdem die App im Store eingetragen wurde, ohne dass die App erneut übermittelt werden muss.

> **Hinweis**&nbsp;&nbsp;In diesem Abschnitt der Dokumentation wird das Übermitteln von Add-Ons im Dev Center-Dashboard beschrieben. Alternativ dazu können Sie auch die [Windows Store-Übermittlungs-API](../monetize/create-and-manage-submissions-using-windows-store-services.md) verwenden, um Add-On-Übermittlungen zu automatisieren.

## <a name="checklist-for-submitting-an-add-on"></a>Prüfliste für die Übermittlung eines Add-Ons

Hier finden Sie eine Liste mit den Informationen, die Sie beim Erstellen Ihrer Add-On-Übermittlung angeben können. Die erforderlichen Elemente sind im Folgenden aufgeführt. Einige Elemente sind optional oder verfügen bereits über Standardwerte, die Sie nach Bedarf ändern können.

### <a name="create-a-new-add-on-page"></a>Erstellen einer neuen Add-On-Seite
| Feldname                    | Hinweise                            |
|-------------------------------|----------------------------------|
| [**Produkttyp**](set-your-add-on-product-id.md#product-type)      | Erforderlich. Bei **Gebrauchsgut** muss **Produktlebenszeit** angegeben werden. |  
| [**Produkt-ID**](set-your-add-on-product-id.md#product-id)          | Erforderlich |        

<span/>

### <a name="properties-page"></a>Seite „Eigenschaften“
| Feldname                    | Hinweise                              |   
|-------------------------------|------------------------------------|
| [**Produktlebensdauer**](enter-add-on-properties.md#product-lifetime)  | Erforderlich, wenn der Produkttyp **Gebrauchsgut** lautet. Gilt nicht für andere Produkttypen. |
| [**Menge**](enter-add-on-properties.md#quantity)  | Erforderlich, wenn der Produkttyp **Vom Store verwalteter Verbrauchsartikel** lautet. Gilt nicht für andere Produkttypen.
| [**Inhaltstyp**](enter-add-on-properties.md#content-type)          | Erforderlich       |               
| [**Schlüsselwörter**](enter-add-on-properties.md#keywords)                  | Optional (bis zu zehn Schlüsselwörter mit jeweils maximal 30 Zeichen) |
| [**Benutzerdefinierte Entwicklerdaten**](enter-add-on-properties.md#custom-developer-data)                               | Optional (maximal 3.000 Zeichen)             |

<span/>

### <a name="pricing-and-availability-page"></a>Seite „Preise und Verfügbarkeit“
| Feldname                    | Hinweise                                       |
|-------------------------------|---------------------------------------------|
| [**Grundpreis**](set-add-on-pricing-and-availability.md#base-price)                | Erforderlich                                    |
| [**Märkte und angepasste Preise**](set-add-on-pricing-and-availability.md#markets-and-custom-prices)  | Standard: in allen möglichen Märkten verfügbar |
| [**Sonderangebotsverkaufspreise**](put-apps-and-add-ons-on-sale.md)               | Optional                             |
| [**Verteilung und Sichtbarkeit**](set-add-on-pricing-and-availability.md#distribution-and-visibility)   | Standard: Das Add-On kann von Kunden beim Browsen oder Suchen im Store gefunden werden. |
| [**Veröffentlichungsdatum**](set-add-on-pricing-and-availability.md#publish-date)                | Standard: Das Add-On wird direkt nach der Zertifizierung veröffentlicht. |

<span/>

### <a name="store-listings"></a>Store-Einträge
Ein Store-Eintrag ist erforderlich. Es wird empfohlen, für jede von der App unterstützte [Sprache](create-add-on-store-listings.md#languages) Store-Einträge anzugeben.

| Feldname                    | Hinweise                                       |
|-------------------------------|---------------------------------------------|
| [**Titel**](create-add-on-store-listings.md#title)                    | Erforderlich (max. 100 Zeichen)              |
| [**Beschreibung**](create-add-on-store-listings.md#description)       | Optional (max. 200 Zeichen)              |
| [**Symbol**](create-add-on-store-listings.md#icon)                    | Optional (PNG, 300x300 Pixel)             |

<span/>

Nachdem Sie diese Informationen eingegeben haben, klicken Sie auf **An Store einreichen**. In den meisten Fällen dauert der Zertifizierungsprozess etwa eine Stunde. Danach wird Ihr Add-On im Store veröffentlicht und steht für Kunden zum Kauf bereit.

>**Hinweis**&nbsp;&nbsp;Das Add-On muss außerdem im Code Ihrer App implementiert werden. Weitere Informationen finden Sie unter [In-App-Käufe und Testversionen](../monetize/in-app-purchases-and-trials.md).


## <a name="updating-an-add-on-after-publication"></a>Aktualisieren eines Add-Ons nach der Veröffentlichung

Sie können ein veröffentlichtes Add-On jederzeit ändern. Add-On-Änderungen werden unabhängig von Ihrer App eingereicht und veröffentlicht. Sie müssen daher in der Regel nicht die gesamte App aktualisieren, um Änderungen an einem Add-On vorzunehmen, z. B. das Aktualisieren des Preises oder der Beschreibung.

> **Wichtig**&nbsp;&nbsp;Wenn die App für Kunden unter Windows 8.x verfügbar ist, müssen Sie eine neue App-Übermittlung erstellen und veröffentlichen, um die Add-On-Updates für diese Kunden sichtbar zu machen. Auch wenn Sie neue Add-Ons einer App für Windows 8.x hinzufügen, nachdem die App veröffentlicht wurde, müssen Sie den App-Code aktualisieren, um auf diese Add-Ons zu verweisen, und die App dann erneut übermitteln. Andernfalls sind die neuen Add-Ons nicht für Kunden unter Windows 8.x sichtbar.

Wechseln Sie zum Übermitteln von Updates im Dashboard zur Seite des Add-Ons, und klicken Sie auf **Aktualisieren**. Dadurch wird eine neue Übermittlung für das Add-On erstellt, wobei die Informationen aus der vorherigen Übermittlung als Ausgangspunkt verwendet werden. Ändern Sie die gewünschten Informationen, und klicken Sie dann auf **An Store übermitteln**.

Wenn Sie ein zuvor angebotenes Add-On entfernen möchten, können Sie dies tun, indem Sie eine neue Übermittlung erstellen und die Option [Verteilung und Sichtbarkeit](set-add-on-pricing-and-availability.md) in **Nicht mehr zum Kauf erhältlich. Wird nicht im App-Eintrag angezeigt.** ändern. Achten Sie darauf, den App-Code entsprechend zu aktualisieren, um auch Verweise auf das Add-On zu entfernen.

