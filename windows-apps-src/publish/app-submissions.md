---
Description: Once you've created your app by reserving a name, you can start working on getting it published. The first step is to create a submission.
title: App-Übermittlung
ms.assetid: 363BB9E4-4437-4238-A80F-ABDFC70D96E4
keywords: Prüfliste, Windows, UWP, Übermittlung, übermitteln, Spiel, App, übermitteln
ms.date: 10/31/2018
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 444243bdb1d50146ba54af4f1417103566f97f93
ms.sourcegitcommit: b5c9c18e70625ab770946b8243f3465ee1013184
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "7964499"
---
# <a name="app-submissions"></a>App-Übermittlungen


Nachdem Sie Ihre [App durch die Reservierung eines Namens erstellt haben](create-your-app-by-reserving-a-name.md), können Sie mit der Veröffentlichung beginnen. Der erste Schritt besteht darin, eine ***Übermittlung** zu erstellen.

Sie beginnen mit der Einreichung, sobald Ihre App fertig und bereit für die Veröffentlichung ist. Sie können mit der Eingabe von Infos beginnen, noch bevor Sie eine einzige Codezeile programmiert haben. Updates, die Sie an Ihre Übermittlung werden gespeichert, darauf zurückkehren und darauf zu arbeiten, wenn Sie bereit sind.

> [!NOTE]
> Sie müssen ein aktives [Entwicklerkonto](http://go.microsoft.com/fwlink/p/?LinkId=615100) im [Partner Center](https://partner.microsoft.com/dashboard) haben, um apps im Microsoft Store übermitteln.

Nach der Veröffentlichung Ihrer app können Sie eine aktualisierte Version veröffentlichen, indem Sie eine weitere Einreichung im Partner Center erstellen. Durch die Erstellung einer neuen Einreichung können Sie alle erforderlichen Änderungen vornehmen und veröffentlichen – z. B. neue Pakete hochladen oder Preisdetails oder App-Kategorie ändern. **Um eine neue Übermittlung für eine veröffentlichte app zu erstellen, klicken Sie auf neben der aktuellen Übermittlung, die auf **der Übersichtsseite** angezeigt.** Sie können auch [eine app aus dem Speicher zu entfernen](guidance-for-app-package-management.md#removing-an-app-from-the-store) , wenn Sie müssen dazu (und dann zur Verfügung stellen später erneut, wenn Sie möchten).

> [!NOTE]
> In diesem Abschnitt der Dokumentation wird beschrieben, wie Sie eine app-Übermittlung in Partner Center erstellen. Alternativ dazu können Sie auch die [Microsoft Store-Übermittlungs-API](../monetize/create-and-manage-submissions-using-windows-store-services.md) verwenden, um App-Übermittlungen zu automatisieren.

> [!IMPORTANT]
> Ab dem 31. Oktober 2018 darf keine Produkte neu erstellten Pakete für Windows-8.x/Windows enthalten Phone 8.x oder früher. Weitere Informationen finden Sie in diesem [Blogbeitrag](https://blogs.windows.com/buildingapps/2018/08/20/important-dates-regarding-apps-with-windows-phone-8-x-and-earlier-and-windows-8-8-1-packages-submitted-to-microsoft-store/#SzKghBbqDMlmAO4c.97).

## <a name="app-submission-checklist"></a>Prüfliste für die App-Übermittlung

Hier finden Sie eine Liste mit den Informationen, die Sie beim Erstellen Ihrer App-Übermittlung angeben können, sowie Links zu weiteren Informationen.

Die erforderlichen Elemente sind im Folgenden aufgeführt. Einige Bereiche sind optional oder verfügen über Standardwerte, die Sie nach Bedarf ändern können. Sie müssen nicht auf diesen Abschnitten in der hier angegebenen Reihenfolge funktionieren.

### <a name="pricing-and-availability-page"></a>Seite „Preise und Verfügbarkeit“
| Feldname                    | Hinweise                                       | Weitere Informationen                                                             |
|-------------------------------|---------------------------------------------|---------------------------------------------------------------------------|
| **Märkte**                   | Standard: alle möglichen Märkte  | [Festlegen des Preises und Auswählen der Märkte](define-pricing-and-market-selection.md)         |
| **Zielgruppe**                | Standardwert: Öffentlich | [Zielgruppe](choose-visibility-options.md#audience) |
| **Erkennbarkeit**                | Standard: Diese App im Store verfügbar und sichtbar machen | [Erkennbarkeit](choose-visibility-options.md#discoverability) |
| **Zeitplan**                  | Standard: so schnell wie möglich veröffentlichen        | [Konfigurieren des genauen Veröffentlichungszeitplans](configure-precise-release-scheduling.md) |
| **Grundpreis**                | Erforderlich                                    | [Festlegen und Planen von App-Preisen](set-and-schedule-app-pricing.md)              |
| **Kostenlose Testversion**                | Standard: Keine kostenlose Testversion                      | [Kostenlose Testversion](set-app-pricing-and-availability.md#free-trial)              |
| **Sonderpreise**              | Optional                                    | [Anbieten vergünstigter Apps und Add-Ons](put-apps-and-add-ons-on-sale.md)           |
| **Organisationslizenzierung**    | Standard: Großvolumige Käufe durch Organisationen sind erlaubt. | [Optionen für die Organisationslizenzierung](organizational-licensing.md)        |
      |


### <a name="properties-page"></a>Seite „Eigenschaften“

| Feldname                    | Hinweise                                       | Weitere Informationen                                                             |
|-------------------------------|---------------------------------------------|---------------------------------------------------------------------------|
| **Kategorie und Unterkategorie**  | Erforderlich                                    | [Kategorie- und Unterkategorietabelle](category-and-subcategory-table.md)       |
| **URL zu den Datenschutzrichtlinien**            | Für viele Apps erforderlich. Weitere Informationen finden Sie in der [Vereinbarung für App-Entwickler](https://docs.microsoft.com/legal/windows/agreements/app-developer-agreement) und den [MicrosoftStore-Richtlinien](https://docs.microsoft.com/en-us/legal/windows/agreements/store-policies#105-personal-information). | [URL zu den Datenschutzrichtlinien](enter-app-properties.md#privacy-policy-url)        |
| **Webseite**                   | Optional                                    | [Website](enter-app-properties.md#website)                   |
| **Support – Kontaktinfos**      | Erforderlich, wenn Ihr Produkt auf Xbox verfügbar ist. Andernfalls optional (empfohlen)                                   | [Support – Kontaktinfos](enter-app-properties.md#support-contact-info)              |
| **Einstellungen für Spiele**             | Optional (gilt nur für Spiele)         | [Einstellungen für Spiele](enter-app-properties.md#game-settings) |
| **Anzeigemodus**             | Optional                   | [Anzeigemodus](enter-app-properties.md#display-mode) |
| **Produktdeklarationen**          | Standard: Kunden können diese App auf alternativen Laufwerken oder Wechselmedien installieren. Windows kann die Daten dieser App in automatische Sicherungen auf OneDrive einschließen. | [Produktdeklarationen](app-declarations.md) |
| **Systemanforderungen**      | Optional                                    | [Systemanforderungen](enter-app-properties.md#system-requirements)      |

<span/>

### <a name="age-ratings-page"></a>Seite „Altersfreigaben“

| Feldname                    | Hinweise                                       | Weitere Informationen                          |
|-------------------------------|---------------------------------------------|----------------------------------------|
| **Altersfreigaben**               | Erforderlich                                    | [Altersfreigaben](age-ratings.md)          |

<span/>

### <a name="packages-page"></a>Seite „Pakete“

| Feldname                    | Hinweise                                  | Weitere Informationen                          |
|-------------------------------|----------------------------------------|----------------------------------------|
| **Package upload control (Paketuploadsteuerung)**    | Erforderlich (mindestens ein Paket)        | [Hochladen von App-Paketen](upload-app-packages.md) |
| **Verfügbarkeit von Gerätefamilien** | Standard: basierend auf Ihren Paketen       | [Verfügbarkeit von Gerätefamilien](device-family-availability.md) |
| **Schrittweises Paketrollout**   | Optional (nur für Updates)            | [Schrittweises Paketrollout](gradual-package-rollout.md) |
| **Erforderliches Update**          | Optional (nur für Updates)            | [Erforderliches Update](upload-app-packages.md#mandatory-update)


### <a name="store-listings"></a>Store-Einträge

Sie benötigen alle erforderlichen Informationen für mindestens eine der von Ihrer App unterstützten Sprachen. Wir empfehlen Ihnen, [Store-Einträge](create-app-store-listings.md) in allen Sprachen anzugeben, die von der App unterstützt werden. Außerdem können Sie [Store-Einträge in weiteren Sprachen angeben](create-app-store-listings.md#store-listing-languages). Um die Verwaltung mehrerer Einträge für das gleiche Produkt zu erleichtern, können Sie [Store-Einträge importieren und exportieren](import-and-export-store-listings.md).

| Feldname                    | Hinweise                                       | Weitere Informationen                                                     |
|-------------------------------|---------------------------------------------|-------------------------------------------------------------------|
| **Beschreibung**               | Erforderlich                                    | [Erstellen einer interessanten App-Beschreibung](write-a-great-app-description.md) |
| **Neuigkeiten in dieser Version**   | Optional                                 | [Anmerkungen zu dieser Version](create-app-store-listings.md#whats-new-in-this-version)       |
| **App-Features**              | Optional                                    | [Produktfunktionen](create-app-store-listings.md#product-features)         |
| **Screenshots**               | Erforderlich (mindestens ein Screenshot; es werden vier oder mehr empfohlen)          | [Screenshots](app-screenshots-and-images.md#screenshots)          |
| **Store-Logos**               | Empfohlen. Ist für bestimmte Betriebssystemversionen erforderlich | [Store-Logos](app-screenshots-and-images.md#store-logos)             |
| **Trailer**                  | Optional                                    | [Trailer](app-screenshots-and-images.md#trailers)                | 
| **Windows10 und Xbox-Bild (16:9 Besonderes Favoritenbild)**     | Empfohlen        | [Windows 10 und Xbox-Bild (16:9 besonderes Favoritenbild)
] (app-screenshots-and-images.md#windows-10-and-xbox-image-169-super-hero-art) |
| **Xbox-Bilder**     | Erforderlich für die ordnungsgemäße Anzeige, wenn Sie auf Xbox veröffentlichen        | [Xbox-Bilder
] (app-Screenshots-und-images.md #Xbox-Bilder) |
| **Zusätzliche Felder**  | Optional                                    | [Zusätzliche Felder](create-app-store-listings.md#supplemental-fields) 
| **Suchbegriffe**              | Optional                                    | [Suchbegriffe](create-app-store-listings.md#search-terms)         |
| **Urheberrecht- und Markeninformationen** | Optional                                 | [Urheberrecht- und Markeninformationen](create-app-store-listings.md#copyright-and-trademark-info) |
| **Zusätzliche Lizenzbedingungen**  | Optional                                    | [Zusätzliche Lizenzbedingungen](create-app-store-listings.md#additional-license-terms) |
| **Entwickelt von**              | Optional                                    | [Entwickelt von](create-app-store-listings.md#developed-by)                   |


<span/>

### <a name="submission-options-page"></a>Seite für die Übermittlungsoptionen

| Feldname                    | Hinweise                                       | Weitere Informationen                                                     |
|-------------------------------|---------------------------------------------|-------------------------------------------------------------------|
| **Optionen zum Anhalten der Veröffentlichung**     | Standard: Veröffentlichen Sie diese Übermittlung, sobald die Zertifizierung abgeschlossen ist (oder ab einem im Abschnitt des Zeitplans ausgewählten Datum)      | [Optionen zum Anhalten der Veröffentlichung](manage-submission-options.md#publishing-hold-options)    
| **Hinweise für Zertifizierung**     | Empfohlen          | [Hinweise für Zertifizierung](notes-for-certification.md)             |
| **Eingeschränkte Funktionen**     | Erforderlich, wenn Ihr Produkt alle [eingeschränkten Funktionen](../packaging/app-capability-declarations.md#restricted-capabilities) deklariert    | [Eingeschränkte Funktionen](manage-submission-options.md#publishing-hold-options)       

<span/>

> [!NOTE]
> Informationen zum Veröffentlichen von Branchen-Apps direkt für Unternehmen finden Sie unter [Verteilen von Branchen-Apps an Unternehmen](distribute-lob-apps-to-enterprises.md).
