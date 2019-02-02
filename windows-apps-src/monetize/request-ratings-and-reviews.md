---
Description: Learn about several ways you can programmatically enable customers to rate and review your app.
title: Anfordern von Bewertungen und Prüfungen für Ihre App
ms.date: 01/22/2019
ms.topic: article
keywords: Windows10, UWP, Bewertungen, Rezensionen
ms.localizationpriority: medium
ms.openlocfilehash: b167f4cc40ee72e6405436bacee28f2f20b4623c
ms.sourcegitcommit: 7a1899358cd5ce9d2f9fa1bd174a123740f98e7a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2019
ms.locfileid: "9042636"
---
# <a name="request-ratings-and-reviews-for-your-app"></a>Anfordern von Bewertungen und Prüfungen für Ihre App

Sie können Code zu Ihrer Universellen Windows-Plattform (UWP)-App hinzufügen, um Ihre Kunden programmgesteuert aufzufordern, Ihre App zu bewerten oder zu rezensieren. Hierfür stehen Ihnen mehrere Möglichkeiten zur Verfügung:
* Sie können ein Bewertungs- und Rezensionsdialogfeld direkt im Kontext Ihrer App anzeigen.
* Sie können programmgesteuert die Bewertungs- und Rezensionsseite für Ihre App im Microsoft Store öffnen.

Wenn Sie Ihre bewertungs- und rezensionsdaten analysieren möchten, können die Daten im Partner Center anzeigen oder der Microsoft Store-Analyse-API zum programmgesteuerten Abrufen dieser Daten verwenden.

> [!IMPORTANT]
> Wenn Sie eine Bewertung-Funktion in Ihrer app hinzufügen, müssen alle Rezensionen der Benutzer auf den Store Bewertung Mechanismen, unabhängig von der Bewertung ausgewählte Star senden. Wenn Sie Feedback oder Kommentare von Benutzern erfassen, muss es deutlich gemacht werden, dass er bezieht sich nicht auf die app-Bewertung oder Rezensionen im Store jedoch direkt an die app-Entwickler gesendet. Finden Sie unter den Entwickler Verhaltensregeln für Weitere Informationen im Zusammenhang mit [Fraudulent oder unehrlichen Aktivitäten](https://docs.microsoft.com/legal/windows/agreements/store-developer-code-of-conduct#3-fraudulent-or-dishonest-activities).

## <a name="show-a-rating-and-review-dialog-in-your-app"></a>Ein Bewertungs- und Rezensionsdialogfeld in Ihrer App anzeigen

Wenn Sie programmgesteuert ein Dialogfeld von Ihrer app anzeigen möchten, die Ihre Kunden auffordert zu Ihrer app zu bewerten und eine Rezension zu senden, rufen Sie die [RequestRateAndReviewAppAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.requestrateandreviewappasync) -Methode im [Windows.Services.Store](https://docs.microsoft.com/uwp/api/windows.services.store) -Namespace. 

> [!IMPORTANT]
> Die Anforderung zum Anzeigen des Bewertungs- und Rezensionsdialogfelds muss im UI-Thread in Ihrer App aufgerufen werden.

```csharp
using Windows.ApplicationModel.Store;

private StoreContext _storeContext;

public async Task Initialize()
{
    if (App.IsMultiUserApp) // pseudo-code
    {
        IReadOnlyList<User> users = await User.FindAllAsync();
        User firstUser = users[0];
        _storeContext = StoreContext.GetForUser(firstUser);
    }
    else
    {
        _storeContext = StoreContext.GetDefault();
    }
}

private async Task PromptUserToRateApp()
{
    // Check if we’ve recently prompted user to review, we don’t want to bother user too often and only between version changes
    if (HaveWePromptedUserInPastThreeMonths())  // pseudo-code
    {
        return;
    }

    StoreRateAndReviewResult result = await 
        _storeContext.RequestRateAndReviewAppAsync();

    // Check status
    switch (result.Status)
    { 
        case StoreRateAndReviewStatus.Succeeded:
            // Was this an updated review or a new review, if Updated is false it means it was a users first time reviewing
            if (result.UpdatedExistingRatingOrReview)
            {
                // This was an updated review thank user
                ThankUserForReview(); // pseudo-code
            }
            else
            {
                // This was a new review, thank user for reviewing and give some free in app tokens
                ThankUserForReviewAndGrantTokens(); // pseudo-code
            }
            // Keep track that we prompted user and don’t do it again for a while
            SetUserHasBeenPrompted(); // pseudo-code
            break;

        case StoreRateAndReviewStatus.CanceledByUser:
            // Keep track that we prompted user and don’t prompt again for a while
            SetUserHasBeenPrompted(); // pseudo-code

            break;

        case StoreRateAndReviewStatus.NetworkError:
            // User is probably not connected, so we’ll try again, but keep track so we don’t try too often
            SetUserHasBeenPromptedButHadNetworkError(); // pseudo-code

            break;

        // Something else went wrong
        case StoreRateAndReviewStatus.OtherError:
        default:
            // Log error, passing in ExtendedJsonData however it will be empty for now
            LogError(result.ExtendedError, result.ExtendedJsonData); // pseudo-code
            break;
    }
}
```

Die **RequestRateAndReviewAppAsync** -Methode wurde in Windows 10, Version 1809, eingeführt und kann nur in Projekten für die **Windows 10 October 2018 verwendet werden Update (10.0; Build 17763)** oder einer neueren Version in Visual Studio.

### <a name="response-data-for-the-rating-and-review-request"></a>Antwortdaten für die Bewertungs- und Rezensionsanforderung

Nach Übermittlung die Anforderung zum Anzeigen eines bewertungs- und rezensionsdialogfeldes, enthält die [ExtendedJsonData](https://docs.microsoft.com/uwp/api/windows.services.store.storerateandreviewresult.extendedjsondata) -Eigenschaft der [StoreRateAndReviewResult](https://docs.microsoft.com/uwp/api/windows.services.store.storerateandreviewresult) -Klasse eine JSON-formatierte Zeichenfolge, die angibt, ob die Anforderung erfolgreich war.

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

| Feld          | Beschreibung                                                                                                                                   |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| *status*       | Eine Zeichenfolge, die angibt, ob der Kunde eine Bewertung oder Rezension erfolgreich gesendet hat. Die unterstützten Werte sind **success** und **aborted**. |
| *data*         | Ein Objekt, das nur einen booleschen Wert mit dem Namen *aktualisiert* enthält. Dieser Wert gibt an, ob der Kunde eine vorhandene Bewertung oder Rezension aktualisiert hat. Das *data*-Objekt ist nur in den Erfolgsantworten enthalten. |
| *errorDetails* | Eine Zeichenfolge, die Fehlerdetails für die Anforderung enthält.                                                                                     |

## <a name="launch-the-rating-and-review-page-for-your-app-in-the-store"></a>Die Bewertungs- und Rezensionsseite für Ihre App im Store starten

Wenn Sie programmgesteuert eine Bewertungs- und Rezensionsseite für Ihre App im Store öffnen möchten, können Sie die [LaunchUriAsync](https://docs.microsoft.com/uwp/api/windows.system.launcher.launchuriasync)-Methode mit dem ```ms-windows-store://review```-URI-Schema verwenden, wie in diesem Codebeispiel gezeigt wird.

```csharp
bool result = await Windows.System.Launcher.LaunchUriAsync(new Uri("ms-windows-store://review/?ProductId=9WZDNCRFHVJL"));
```

Weitere Informationen finden Sie unter [Die Microsoft Store App starten](../launch-resume/launch-store-app.md).

## <a name="analyze-your-ratings-and-reviews-data"></a>Ihre Bewertungs- und Rezensionsdaten analysieren

Sie haben mehrere Optionen, um die Bewertungs- und Rezensionsdaten von Ihren Kunden zu analysieren:
* Sie können den Bericht ["Rezensionen"](../publish/reviews-report.md) im Partner Center verwenden, um die Bewertungen und Prüfungen von Ihren Kunden anzuzeigen. Sie können diesen Bericht auch herunterladen, um ihn offline zu sehen.
* Sie können die [Abrufen von App-Bewertungen](get-app-ratings.md)- und [Abrufen von App-Rezensionen](get-app-reviews.md)-Methoden in der Store-Analyse-API zum programmgesteuerten Abrufen der Bewertungen und Prüfungen von Ihren Kunden im JSON-Format verwenden.

## <a name="related-topics"></a>Verwandte Themen

* [Senden von Anfragen an den Store](send-requests-to-the-store.md)
* [Starten der Microsoft Store-App](../launch-resume/launch-store-app.md)
* [Rezensionsbericht](../publish/reviews-report.md)
