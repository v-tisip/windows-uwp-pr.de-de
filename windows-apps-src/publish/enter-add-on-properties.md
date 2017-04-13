---
author: jnHs
Description: "Beim Übermitteln eines Add-Ons sind die Optionen auf der Seite „Eigenschaften“ hilfreich, um das Verhalten Ihres Add-Ons festzulegen, wenn es Kunden angeboten wird."
title: Eingeben von Add-On-Eigenschaften
ms.assetid: 26D2139F-66FD-479E-940B-7491238ADCAE
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
ms.openlocfilehash: 186088f249c2e6fe116c970bd1969fcb59863ba6
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="enter-add-on-properties"></a>Eingeben von Add-On-Eigenschaften


Beim Übermitteln eines Add-Ons sind die Optionen auf der Seite **Eigenschaften** hilfreich, um das Verhalten Ihres Add-Ons festzulegen, wenn es Kunden angeboten wird.

## <a name="product-type"></a>Produkttyp

Beim ersten [Erstellen des Add-Ons](set-your-add-on-product-id.md) wird der Produkttyp ausgewählt. Der ausgewählte Produkttyp wird hier angezeigt, Sie können ihn jedoch nicht ändern.

> **Hinweis**  Wenn Sie das Add-On noch nicht veröffentlicht haben können Sie die Übermittlung löschen und erneut starten, falls Sie einen anderen Produkttyp auswählen müssen. 

Je nach ausgewähltem Produkttyp wird eins der folgenden Felder angezeigt:

### <a name="product-lifetime"></a>Produktlebensdauer
Wenn Sie als Produkttyp **Gebrauchsgut** ausgewählt haben, wird hier die **Produktlebenszeit** angezeigt. Die standardmäßige **Produktlebenszeit** eines solchen Add-Ons ist **Unbegrenzt**, d.h. das Add-On läuft niemals ab. Sie können die **Produktlebenszeit** auch festlegen, sodass das Add-On nach einem festgelegten Zeitraum abläuft (mögliche Optionen: 1 bis 365Tage). 

### <a name="quantity"></a>Menge
Wenn Sie den Produkttyp **Vom Store verwalteter Verbrauchsartikel** ausgewählt haben, wird hier die **Menge** angezeigt. Sie müssen eine Zahl zwischen 1 und 1000000 eingeben. Diese Menge wird Kunden gewährt, wenn sie Ihr Add-On erwerben, und vom Store wird der Betrag nachverfolgt, wenn die App die Nutzung des Add-Ons durch Kunden meldet.

## <a name="content-type"></a>Inhaltstyp

Unabhängig vom Produkttyp Ihres Add-Ons müssen Sie auch die Art der Inhalte angeben, die Sie anbieten. Für die meisten Add-Ons sollte der Inhaltstyp **Download elektronischer Software** lauten. Wenn eine andere Option aus der Liste Ihr Add-On besser beschreibt (wenn Sie z.B. einen Musikdownload oder ein E-Book anbieten), wählen Sie stattdessen diese Option. 

Mögliche Optionen für den Inhaltstyp eines Add-Ons:

-   Download elektronischer Software
-   Elektronische Bücher
-   Einzelausgabe einer elektronischen Zeitschrift
-   Einzelausgabe einer elektronischen Zeitung
-   Musikdownload
-   Musikstreaming
-   Onlinedatenspeicher/-dienste
-   Videodownload
-   Videostreaming
-   Software as a Service

## <a name="keywords"></a>Schlüsselwörter

Sie können für jedes eingereichte Add-On bis zu zehn Schlüsselwörter von jeweils bis zu 30 Zeichen bereitstellen. Danach kann Ihre App nach Add-Ons suchen, die diesen Schlüsselwörtern entsprechen. Durch dieses Feature können Sie Bildschirme in Ihrer App erstellen, die Add-Ons laden können, ohne dass Sie die Produkt-ID im App-Code direkt angeben müssen. Sie können die Schlüsselwörter des Add-Ons später jederzeit ändern, ohne Codeänderungen an der App vorzunehmen oder die App erneut einzureichen.

> **Hinweis**  Schlüsselwörter stehen für Pakete, die für Windows8 und Windows8.1 entwickelt wurden, nicht zur Verfügung.

## <a name="custom-developer-data"></a>Benutzerdefinierte Entwicklerdaten

Sie können im Feld **Benutzerdefinierte Entwicklerdaten** (früher **Tag**) bis zu 3.000 Zeichen eingeben, um zusätzlichen Kontext für das In-App-Produkt bereitzustellen. Meistens handelt es sich um eine XML-Zeichenfolge. Sie können aber beliebige Inhalte eingeben.

Verwenden Sie zur Abfrage des Felds die Eigenschaft [StoreSku.CustomDeveloperData](https://msdn.microsoft.com/en-us/library/windows/apps/windows.services.store.storesku.customdeveloperdata.aspx) in [Windows.Services.Store namespace](https://msdn.microsoft.com/en-us/library/windows/apps/windows.services.store.aspx). (Wenn Sie [Windows.ApplicationModel.Store-Namespace](https://msdn.microsoft.com/en-us/library/windows/apps/windows.applicationmodel.store.aspx) verwenden, nutzen Sie die Eigenschaft [ProductListing.Tag](https://msdn.microsoft.com/en-us/library/windows/apps/windows.applicationmodel.store.productlisting.tag.aspx).)

Nehmen wir beispielsweise an, dass Sie ein Spiel anbieten und einen Beutel Goldmünzen als Add-On verkaufen. Über das Feld **Benutzerdefinierte Entwicklerdaten** kann die App nach diesem Beutel Gold fragen. Sie können den Wert (in diesem Fall die Anzahl der Münzen im Beutel) jederzeit anpassen, indem Sie die Informationen im Feld **Benutzerdefinierte Entwicklerdaten** des Add-Ons aktualisieren. Dazu müssen Sie keine Codeänderungen in der App vornehmen und die App nicht erneut übermitteln.

> **Hinweis**  Das Feld **Benutzerdefinierte Entwicklerdaten** ist nicht in Paketen verfügbar, die für Windows8 und Windows8.1 entwickelt wurden.

 

 

 




