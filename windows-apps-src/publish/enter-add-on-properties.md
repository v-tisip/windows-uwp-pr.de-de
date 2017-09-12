---
author: jnHs
Description: "Beim Übermitteln eines Add-Ons sind die Optionen auf der Seite „Eigenschaften“ hilfreich, um das Verhalten Ihres Add-Ons festzulegen, wenn es Kunden angeboten wird."
title: Eingeben von Add-On-Eigenschaften
ms.assetid: 26D2139F-66FD-479E-940B-7491238ADCAE
ms.author: wdg-dev-content
ms.date: 06/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
ms.openlocfilehash: 253e008d3622094dcfe765531d71e5f37b7777b0
ms.sourcegitcommit: de6bc8acec2cd5ebc36bb21b2ce1a9980c3e78b2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
---
# <a name="enter-add-on-properties"></a>Eingeben von Add-On-Eigenschaften


Beim Übermitteln eines Add-Ons sind die Optionen auf der Seite **Eigenschaften** hilfreich, um das Verhalten Ihres Add-Ons festzulegen, wenn es Kunden angeboten wird.

## <a name="product-type"></a>Produkttyp

Beim ersten [Erstellen des Add-Ons](set-your-add-on-product-id.md) wird der Produkttyp ausgewählt. Der ausgewählte Produkttyp wird hier angezeigt, Sie können ihn jedoch nicht ändern.

> [!TIP]
> Hinweis Wenn Sie das Add-On nicht veröffentlicht haben, können Sie die Übermittlung löschen und von vorne beginnen, falls Sie einen anderen Produkttyp auswählen möchten.

Die Felder, die Sie auf dieser Seite sehen, variieren je nach den Produkttyp Ihres Add-Ons.

## <a name="product-lifetime"></a>Produktlebensdauer


Wenn Sie als Produkttyp **Gebrauchsgut** ausgewählt haben, wird hier die **Produktlebenszeit** angezeigt. Die standardmäßige **Produktlebenszeit** dauerhafter Add-Ons ist **Unbegrenzt**. Das Add-On läuft also niemals ab. Sie können die **Produktlebenszeit** auch festlegen, sodass das Add-On nach einem festgelegten Zeitraum abläuft (mögliche Optionen: 1 bis 365Tage).

## <a name="quantity"></a>Menge


Wenn Sie den Produkttyp **Vom Store verwalteter Verbrauchsartikel** ausgewählt haben, wird hier die **Menge** angezeigt. Sie müssen eine Zahl zwischen 1 und 1000000 eingeben. Diese Menge wird Kunden gewährt, wenn sie Ihr Add-On erwerben, und vom Store wird der Betrag nachverfolgt, wenn die App die Nutzung des Add-Ons durch Kunden meldet.


## <a name="subscription-period"></a>Abonnementdauer

Wenn Sie als Produkttyp **Abonnement** ausgewählt haben, wird hier die **Abonnementdauer** angezeigt. Müssen Sie eine der verfügbaren Optionen auswählen (**Monatlich**, **3 Monate**, **6 Monate**, **Jährlich**, oder **24 Monate**), um anzugeben, wie häufig ein Kunde für das Abonnement in Rechnung gestellt wird. Beachten Sie, dass Sie nach der Veröffentlichung Ihres Add-Ons Ihre **Abonnementdauer** auswählen können.

> [!NOTE]
> Die Fähigkeit zum Erstellen von Abonnement-Add-Ons ist derzeit nur für eine Gruppe von Entwicklerkonten verfügbar, die am frühen Adoption-Programm teilnehmen. Wir stellen Abonnement-Add-Ons für alle Entwicklerkonten in Zukunft zur Verfügung und wir stellen Ihnen diese vorläufige Dokumentation jetzt zur Verfügung, um Entwicklern eine Vorschau dieser Funktion zu ermöglichen. Weitere Informationen finden Sie unter [Abonnement-Add-Ons für Ihre App aktivieren](../monetize/enable-subscription-add-ons-for-your-app.md).


## <a name="free-trial"></a>Kostenlose Testversion

Für die Abonnement-Add-Ons wird hier ebenfalls eine **kostenlose Testversion** angezeigt. Sie müssen auswählen, ob Kunden das Add-On für einen festgelegten Zeitraum kostenlos verwenden können (entweder **1 Woche** oder **1 Monat**), oder ob Sie **keine kostenlose Testversion** anbieten. Beachten Sie, dass Sie nach der Veröffentlichung Ihres Add-Ons Ihre **Kostenlose Testversion** auswählen können.


## <a name="content-type"></a>Inhaltstyp

Unabhängig vom Produkttyp Ihres Add-Ons müssen Sie die Art der Inhalte angeben, die Sie anbieten. Für die meisten Add-Ons sollte der Inhaltstyp **Download elektronischer Software** lauten. Wenn eine andere Option aus der Liste Ihr Add-On besser beschreibt (wenn Sie z.B. einen Musikdownload oder ein E-Book anbieten), wählen Sie stattdessen diese Option.

Mögliche Optionen für den Inhaltstyp eines Add-Ons:

-   Download elektronischer Software
-   Elektronische Bücher
-   Einzelausgabe einer elektronischen Zeitschrift
-   Einzelausgabe einer elektronischen Zeitung
-   Musikdownload
-   Musikstreaming
-   Onlinedatenspeicher/-dienste
-   Software as a Service
-   Videodownload
-   Videostreaming


## <a name="additional-properties"></a>Weitere Eigenschaften

Diese Felder sind optional für alle Arten von Add-Ons.

<span id="keywords" />
### <a name="keywords"></a>Schlüsselwörter

Sie können für jedes eingereichte Add-On bis zu zehn Schlüsselwörter von jeweils bis zu 30 Zeichen bereitstellen. Danach kann Ihre App nach Add-Ons suchen, die diesen Schlüsselwörtern entsprechen. Durch dieses Feature können Sie Bildschirme in Ihrer App erstellen, die Add-Ons laden können, ohne dass Sie die Produkt-ID im App-Code direkt angeben müssen. Sie können die Schlüsselwörter des Add-Ons später jederzeit ändern, ohne Codeänderungen an der App vorzunehmen oder die App erneut einzureichen.

Verwenden Sie zur Abfrage des Felds die Eigenschaft [StoreProduct.Keywords](https://docs.microsoft.com/uwp/api/windows.services.store.storeproduct#Windows_Services_Store_StoreProduct_Keywords) in [Windows.Services.Store namespace](https://msdn.microsoft.com/en-us/library/windows/apps/windows.services.store.aspx). (Wenn Sie [Windows.ApplicationModel.Store-Namespace](https://msdn.microsoft.com/en-us/library/windows/apps/windows.applicationmodel.store.aspx) verwenden, nutzen Sie die Eigenschaft [ProductListing.Keywords](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.productlisting#Windows_ApplicationModel_Store_ProductListing_Keywords).)

> [!NOTE]
> Schlüsselwörter stehen für Pakete, die auf Windows 8 und Windows 8.1 ausgerichtet sind, nicht zur Verfügung.

<span id="custom-developer-data" />
### <a name="custom-developer-data"></a>Benutzerdefinierte Entwicklerdaten

Sie können im Feld **Benutzerdefinierte Entwicklerdaten** (früher **Tag**) bis zu 3.000 Zeichen eingeben, um zusätzlichen Kontext für das In-App-Produkt bereitzustellen. Meistens handelt es sich um eine XML-Zeichenfolge. Sie können aber beliebige Inhalte eingeben. Ihre App kann dann dieses Feld abfragen, um den Inhalt zu lesen (auch wenn die App die Daten nicht bearbeiten kann und die Änderungen zurückgibt.)

Nehmen Sie beispielsweise an, dass Sie ein Spiel anbieten und Add-Ons verkaufen, wodurch Kunden auf zusätzliche Ebenen zugreifen können. Mithilfe des Felds **Benutzerdefinierte Entwicklerdaten** kann die App abfragen, welche Ebenen verfügbar sind, wenn ein Kunde dieses Add-On erwirbt. Sie können den Wert jederzeit anpassen (in diesem Fall die zugefügten Ebenen), ohne den Code der App zu ändern oder die App erneut zu übermitteln, indem Sie die Informationen im Feld **Benutzerdefinierte Entwicklerdaten** aktualisieren und dann eine aktualisierte Übermittlung für das Add-On veröffentlichen.

Verwenden Sie zur Abfrage des Felds die Eigenschaft [StoreSku.CustomDeveloperData](https://msdn.microsoft.com/en-us/library/windows/apps/windows.services.store.storesku.customdeveloperdata.aspx) unter [Windows.Services.Store namespace](https://msdn.microsoft.com/en-us/library/windows/apps/windows.services.store.aspx). (Wenn Sie [Windows.ApplicationModel.Store-Namespace](https://msdn.microsoft.com/en-us/library/windows/apps/windows.applicationmodel.store.aspx) verwenden, nutzen Sie die Eigenschaft [ProductListing.Tag](https://msdn.microsoft.com/en-us/library/windows/apps/windows.applicationmodel.store.productlisting.tag.aspx).)

> [!NOTE]
> Das Feld **Benutzerdefinierte Entwicklerdaten** ist nicht in Paketen verfügbar, die für Windows8 und Windows8.1 entwickelt wurden.

 

 

 
