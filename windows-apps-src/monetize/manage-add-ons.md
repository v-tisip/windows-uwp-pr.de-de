---
author: mcleanbyron
ms.assetid: 4F9657E5-1AF8-45E0-9617-45AF64E144FC
description: "Verwenden Sie diese Methoden in der Windows Store-Übermittlungs-API, um Add-Ons für Apps zu verwalten, die in Ihrem Windows Dev Center-Konto registriert wurden."
title: "Verwalten von Add-Ons mithilfe der Windows Store-Übermittlungs-API"
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP, Windows Store-Übermittlung API, Add-Ons, In-App-Produkt, IAP"
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 55a6b548246e801c9fcc0392265263123f24de00
ms.lasthandoff: 02/07/2017

---

# <a name="manage-add-ons-using-the-windows-store-submission-api"></a>Verwalten von Add-Ons mithilfe der Windows Store-Übermittlungs-API

Verwenden Sie die folgenden Methoden in der Windows Store-Übermittlungs-API, um Add-Ons zu verwalten (die auch als In-App-Produkt bzw. IAP bezeichnet werden). Eine Einführung in die Windows Store-Übermittlungs-API einschließlich der Voraussetzungen für die Verwendung der API finden Sie unter [Erstellen und Verwalten von Übermittlungen mit Windows Store-Diensten](create-and-manage-submissions-using-windows-store-services.md).

>**Hinweis**&nbsp;&nbsp;Diese Methoden können nur für Windows Dev Center-Konten verwendet werden, die zur Verwendung der Windows Store-Übermittlungs-API berechtigt sind. Diese Berechtigung wird für Entwicklerkonten phasenweise aktiviert, und die Berechtigung ist zu diesem Zeitpunkt nicht für alle Konten aktiviert. Um früheren Zugriff anfordern, melden Sie sich beim Dev Center-Dashboard an, klicken Sie am unteren Rand des Dashboards auf **Feedback**, wählen Sie **Übermittlungs-API** für den Feedback-Bereich, und übermitteln Sie Ihre Anforderung. Sie erhalten eine E-Mail, wenn diese Berechtigung für Ihr Konto aktiviert ist.

Diese Methoden können nur verwendet werden, um Add-Ons abzurufen, zu erstellen oder zu löschen. Um Übermittlungen für Add-Ons zu erstellen, verwenden Sie die Methoden in [Verwalten von Add-On-Übermittlungen](manage-add-on-submissions.md).

<table>
<colgroup>
<col width="10%" />
<col width="30%" />
<col width="60%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Methode</th>
<th align="left">URI</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr>
<td align="left">GET</td>
<td align="left">```https://manage.devcenter.microsoft.com/v1.0/my/inappproducts```</td>
<td align="left">[Abrufen aller Add-Ons für Ihre Apps](get-all-add-ons.md)</td>
</tr>
<tr>
<td align="left">GET</td>
<td align="left">```https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/{inAppProductId}```</td>
<td align="left">[Abrufen eines bestimmten Add-Ons](get-an-add-on.md)</td>
</tr>
<tr>
<td align="left">POST</td>
<td align="left">```https://manage.devcenter.microsoft.com/v1.0/my/inappproducts```</td>
<td align="left">[Erstellen eines Add-Ons](create-an-add-on.md)</td>
</tr>
<tr>
<td align="left">DELETE</td>
<td align="left">```https://manage.devcenter.microsoft.com/v1.0/my/inappproducts/{inAppProductId}```</td>
<td align="left">[Löschen eines Add-Ons](delete-an-add-on.md)</td>
</tr>
</tbody>
</table>

## <a name="prerequisites"></a>Voraussetzungen

Falls noch nicht geschehen, sorgen Sie vor der Verwendung dieser Methoden dafür, dass alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Windows Store-Übermittlungs-API erfüllt sind.

## <a name="data-resources"></a>Datenressourcen

Die Methoden der Windows Store-Übermittlungs-API für das Verwalten von Add-Ons verwenden die folgenden JSON-Datenressourcen.

<span id="add-on-object" />
### <a name="add-on-resource"></a>Add-On-Ressource

Diese Ressource beschreibt ein Add-On.

```json
{
  "applications": {
    "value": [
      {
        "id": "9NBLGGH4R315",
        "resourceLocation": "applications/9NBLGGH4R315"
      }
    ],
    "totalCount": 1
  },
  "id": "9NBLGGH4TNMP",
  "productId": "TestAddOn",
  "productType": "Durable",
  "pendingInAppProductSubmission": {
    "id": "1152921504621243619",
    "resourceLocation": "inappproducts/9NBLGGH4TNMP/submissions/1152921504621243619"
  },
  "lastPublishedInAppProductSubmission": {
    "id": "1152921504621243705",
    "resourceLocation": "inappproducts/9NBLGGH4TNMP/submissions/1152921504621243705"
  }
}
```

Die Ressource hat die folgenden Werte.

| Wert      | Typ   | Beschreibung        |
|------------|--------|--------------|
| applications      | array  | Ein Array mit genau einer [Anwendungsressource](#application-object), die die App darstellt, der dieses Add-On zugeordnet ist. In diesem Array wird nur ein Element unterstützt.  |
| id | string  | Die Store-ID des Add-Ons. Dieser Wert wird vom Store bereitgestellt. Beispiel für eine Store-ID: 9NBLGGH4TNMP.  |
| productId | string  | Die Produkt-ID des Add-Ons. Dies ist die ID, die vom Entwickler während der Erstellung des Add-Ons angegeben wurde. Weitere Informationen finden Sie unter [Festlegen von Produkttyp und Produkt-ID für das IAP](https://msdn.microsoft.com/windows/uwp/publish/set-your-iap-product-id). |
| productType | string  | Der Produkttyp des Add-Ons. Die folgenden Werte werden unterstützt: **Durable** und **Consumable**.  |
| lastPublishedInAppProductSubmission       | object | Eine [Übermittlungsressource](#submission-object) mit Informationen über die letzte veröffentlichte Übermittlung für das Add-On.         |
| pendingInAppProductSubmission        | object  |  Eine [Übermittlungsressource](#submission-object) mit Informationen über die aktuelle ausstehende Übermittlung für das Add-On.  |   |

<span id="application-object" />
### <a name="application-resource"></a>Anwendungsressource

Diese Ressource beschreibt die App, der ein Add-On zugeordnet ist. Das folgende Beispiel veranschaulicht das Format der Ressource.

```json
{
  "applications": {
    "value": [
      {
        "id": "9NBLGGH4R315",
        "resourceLocation": "applications/9NBLGGH4R315"
      }
    ],
    "totalCount": 1
  },
}
```

Die Ressource hat die folgenden Werte.

| Wert           | Typ    | Beschreibung        |
|-----------------|---------|-----------|
| value            | object  |  Ein Objekt, das die folgenden Werte enthält: <br/><br/> <ul><li>*id*. Die Store-ID der App. Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).</li><li>*resourceLocation*. Ein relativer Pfad, den Sie an den Basisanforderungs-URI ```https://manage.devcenter.microsoft.com/v1.0/my/``` anfügen können, um die vollständigen Daten für die App abzurufen.</li></ul>   |
| totalCount   | int  | Die Anzahl der App-Objekte im *applications*-Array des Antworttexts.                                                                                                                                                 |

<span id="submission-object" />
### <a name="submission-resource"></a>Übermittlungsressource

Diese Ressource enthält Informationen über eine Übermittlung für ein Add-On. Das folgende Beispiel veranschaulicht das Format der Ressource.

```json
{
  "pendingInAppProductSubmission": {
    "id": "1152921504621243619",
    "resourceLocation": "inappproducts/9NBLGGH4TNMP/submissions/1152921504621243619"
  },
}
```

Die Ressource hat die folgenden Werte.

| Wert           | Typ    | Beschreibung     |
|-----------------|---------|------------------|
| id            | string  | Die ID der Übermittlung.    |
| resourceLocation   | string  | Ein relativer Pfad, den Sie an den Basisanforderungs-URI ```https://manage.devcenter.microsoft.com/v1.0/my/``` anfügen können, um die vollständigen Daten für die Übermittlung abzurufen.     |
 
<span/>
## <a name="related-topics"></a>Verwandte Themen

* [Erstellen und Verwalten von Übermittlungen mit Windows Store-Diensten](create-and-manage-submissions-using-windows-store-services.md)
* [Verwalten von Add-On-Übermittlungen mithilfe der Windows Store-Übermittlungs-API](manage-add-on-submissions.md)
* [Abrufen aller Add-Ons](get-all-add-ons.md)
* [Abrufen eines Add-Ons](get-an-add-on.md)
* [Erstellen eines Add-Ons](create-an-add-on.md)
* [Löschen eines Add-Ons](delete-an-add-on.md)

