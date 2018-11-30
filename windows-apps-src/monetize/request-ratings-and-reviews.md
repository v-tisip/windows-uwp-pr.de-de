---
Description: Learn about several ways you can programmatically enable customers to rate and review your app.
title: Anfordern von Bewertungen und Prüfungen für Ihre App
ms.date: 06/15/2018
ms.topic: article
keywords: Windows10, UWP, Bewertungen, Rezensionen
ms.localizationpriority: medium
ms.openlocfilehash: 377b71dba2fb62dfc562b56d40e65e43b0bd49c9
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8216504"
---
# <a name="request-ratings-and-reviews-for-your-app"></a>Anfordern von Bewertungen und Prüfungen für Ihre App

Sie können Code zu Ihrer Universellen Windows-Plattform (UWP)-App hinzufügen, um Ihre Kunden programmgesteuert aufzufordern, Ihre App zu bewerten oder zu rezensieren. Hierfür stehen Ihnen mehrere Möglichkeiten zur Verfügung:
* Sie können ein Bewertungs- und Rezensionsdialogfeld direkt im Kontext Ihrer App anzeigen.
* Sie können programmgesteuert die Bewertungs- und Rezensionsseite für Ihre App im Microsoft Store öffnen.

Wenn Sie Ihre bewertungs- und rezensionsdaten analysieren möchten, können Sie die Daten im Partner Center anzeigen oder der Microsoft Store-Analyse-API zum programmgesteuerten Abrufen dieser Daten verwenden.

> [!IMPORTANT]
> Wenn Sie eine Bewertung-Funktion innerhalb Ihrer app hinzufügen, müssen alle Rezensionen der Benutzer auf den Store Bewertung Mechanismen, unabhängig von der Bewertung ausgewählte Star senden. Wenn Sie Feedback oder Kommentare von Benutzern erfassen, muss es deutlich gemacht werden, dass er wird nicht im Zusammenhang mit der app-Bewertung oder Rezensionen im Store jedoch direkt an die app-Entwickler gesendet. Finden Sie unter den Entwickler Verhaltensregeln für Weitere Informationen im Zusammenhang mit [Fraudulent oder unehrlichen Aktivitäten](https://docs.microsoft.com/legal/windows/agreements/store-developer-code-of-conduct#3-fraudulent-or-dishonest-activities).

## <a name="show-a-rating-and-review-dialog-in-your-app"></a>Ein Bewertungs- und Rezensionsdialogfeld in Ihrer App anzeigen

Wenn Sie programmgesteuert ein Dialogfeld von Ihrer App aus anzeigen möchten, das Ihre Kunden auffordert, die App zu bewerten und eine Rezension zu senden, rufen Sie die [SendRequestAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storerequesthelper.sendrequestasync)-Methode im [Windows.Services.Store](https://docs.microsoft.com/uwp/api/windows.services.store)-Namespace auf. Übergeben Sie die ganze Zahl 16 an den *requestKind*-Parameter und eine leere Zeichenfolge an den *parametersAsJson*-Parameter wie in diesem Codebeispiel dargestellt. Dieses Beispiel erfordert die [Json.NET](http://www.newtonsoft.com/json)-Bibliothek von Newtonsoft sowie die Verwendung von using-Anweisungen für die **Windows.Services.Store**-, **System.Threading.Tasks**- und **Newtonsoft.Json.Linq **-Namespaces.

> [!IMPORTANT]
> Die Anforderung zum Anzeigen des Bewertungs- und Rezensionsdialogfelds muss im UI-Thread in Ihrer App aufgerufen werden.

```csharp
public async Task<bool> ShowRatingReviewDialog()
{
    StoreSendRequestResult result = await StoreRequestHelper.SendRequestAsync(
        StoreContext.GetDefault(), 16, String.Empty);

    if (result.ExtendedError == null)
    {
        JObject jsonObject = JObject.Parse(result.Response);
        if (jsonObject.SelectToken("status").ToString() == "success")
        {
            // The customer rated or reviewed the app.
            return true;
        }
    }

    // There was an error with the request, or the customer chose not to
    // rate or review the app.
    return false;
}
```

Die **SendRequestAsync**-Methode verwendet ein einfaches ganzzahlig-basiertes Anforderungssystem und JSON-basierte-Datenparameter, um verschiedene Store-Vorgänge den Apps zur Verfügung zu stellen. Wenn Sie die ganze Zahl 16 an den *requestKind*-Parameter übergeben, stellen Sie eine Anforderung zum Anzeigen des Bewertungs- und Rezensionsdialogfeldes aus und senden die zugehörigen Daten an den Store. Diese Methode wurde in Windows10, Version 1607, eingeführt und kann nur in Projekten für die **Windows 10 Anniversary Edition (10.0; Build 14393)** oder einer neueren Version in Visual Studio verwendet werden. Eine allgemeine Übersicht über diese Methode finden Sie unter [Anforderungen an den Store senden](send-requests-to-the-store.md).

### <a name="response-data-for-the-rating-and-review-request"></a>Antwortdaten für die Bewertungs- und Rezensionsanforderung

Nach Übermittlung der Anforderung zum Anzeigen eines Bewertungs- und Rezensionsdialogfeldes gibt die [Response](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult.Response)-Eigenschaft des [StoreSendRequestResult](https://docs.microsoft.com/uwp/api/windows.services.store.storesendrequestresult)-Rückgabewerts eine Zeichenfolge im JSON-Format zurück, die anzeigt, ob die Anforderung erfolgreich war.

Das folgende Beispiel veranschaulicht den Rückgabewert für diese Anforderung, nachdem der Kunde erfolgreich eine Bewertung oder Rezension übermittelt hat.

```json
{ 
  "status": "success", 
  "data": {
    "updated": false
  },
  "errorDetails": "Success"
}
```

Das folgende Beispiel veranschaulicht den Rückgabewert für diese Anforderung, nachdem der Kunde gewählt hat, keine Bewertung oder Rezension zu übermitteln.

```json
{ 
  "status": "aborted", 
  "errorDetails": "Navigation was unsuccessful"
}
```

In der folgenden Tabelle werden die Felder in der Zeichenfolge im JSON-Format erläutert.

|  Feld  |  Beschreibung  |
|----------------------|---------------|
|  *status*                   |  Eine Zeichenfolge, die angibt, ob der Kunde eine Bewertung oder Rezension erfolgreich gesendet hat. Die unterstützten Werte sind **success** und **aborted**.   |
|  *data*                   |  Ein Objekt, das nur einen booleschen Wert mit dem Namen *aktualisiert* enthält. Dieser Wert gibt an, ob der Kunde eine vorhandene Bewertung oder Rezension aktualisiert hat. Das *data*-Objekt ist nur in den Erfolgsantworten enthalten.   |
|  *errorDetails*                   |  Eine Zeichenfolge, die Fehlerdetails für die Anforderung enthält. |

## <a name="launch-the-rating-and-review-page-for-your-app-in-the-store"></a>Die Bewertungs- und Rezensionsseite für Ihre App im Store starten

Wenn Sie programmgesteuert eine Bewertungs- und Rezensionsseite für Ihre App im Store öffnen möchten, können Sie die [LaunchUriAsync](https://docs.microsoft.com/uwp/api/windows.system.launcher.launchuriasync)-Methode mit dem ```ms-windows-store://review```-URI-Schema verwenden, wie in diesem Codebeispiel gezeigt wird.

```csharp
bool result = await Windows.System.Launcher.LaunchUriAsync(new Uri("ms-windows-store://review/?ProductId=9WZDNCRFHVJL"));
```

Weitere Informationen finden Sie unter [Die Microsoft Store App starten](../launch-resume/launch-store-app.md).

## <a name="analyze-your-ratings-and-reviews-data"></a>Ihre Bewertungs- und Rezensionsdaten analysieren

Sie haben mehrere Optionen, um die Bewertungs- und Rezensionsdaten von Ihren Kunden zu analysieren:
* Den Bericht ["Rezensionen"](../publish/reviews-report.md) können im Partner Center Sie um die Bewertungen und Prüfungen von Ihren Kunden zu sehen. Sie können diesen Bericht auch herunterladen, um ihn offline zu sehen.
* Sie können die [Abrufen von App-Bewertungen](get-app-ratings.md)- und [Abrufen von App-Rezensionen](get-app-reviews.md)-Methoden in der Store-Analyse-API zum programmgesteuerten Abrufen der Bewertungen und Prüfungen von Ihren Kunden im JSON-Format verwenden.

## <a name="related-topics"></a>Verwandte Themen

* [Senden von Anfragen an den Store](send-requests-to-the-store.md)
* [Starten der Microsoft Store-App](../launch-resume/launch-store-app.md)
* [Rezensionsbericht](../publish/reviews-report.md)
