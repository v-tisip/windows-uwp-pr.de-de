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
# <a name="request-ratings-and-reviews-for-your-app"></a><span data-ttu-id="1b185-103">Anfordern von Bewertungen und Prüfungen für Ihre App</span><span class="sxs-lookup"><span data-stu-id="1b185-103">Request ratings and reviews for your app</span></span>

<span data-ttu-id="1b185-104">Sie können Code zu Ihrer Universellen Windows-Plattform (UWP)-App hinzufügen, um Ihre Kunden programmgesteuert aufzufordern, Ihre App zu bewerten oder zu rezensieren.</span><span class="sxs-lookup"><span data-stu-id="1b185-104">You can add code to your Universal Windows Platform (UWP) app to programmatically prompt your customers to rate or review your app.</span></span> <span data-ttu-id="1b185-105">Hierfür stehen Ihnen mehrere Möglichkeiten zur Verfügung:</span><span class="sxs-lookup"><span data-stu-id="1b185-105">There are several ways you can do this:</span></span>
* <span data-ttu-id="1b185-106">Sie können ein Bewertungs- und Rezensionsdialogfeld direkt im Kontext Ihrer App anzeigen.</span><span class="sxs-lookup"><span data-stu-id="1b185-106">You can show a rating and review dialog directly in the context of your app.</span></span>
* <span data-ttu-id="1b185-107">Sie können programmgesteuert die Bewertungs- und Rezensionsseite für Ihre App im Microsoft Store öffnen.</span><span class="sxs-lookup"><span data-stu-id="1b185-107">You can programmatically open the rating and review page for your app in the Microsoft Store.</span></span>

<span data-ttu-id="1b185-108">Wenn Sie Ihre bewertungs- und rezensionsdaten analysieren möchten, können die Daten im Partner Center anzeigen oder der Microsoft Store-Analyse-API zum programmgesteuerten Abrufen dieser Daten verwenden.</span><span class="sxs-lookup"><span data-stu-id="1b185-108">When you are ready to analyze your ratings and reviews data, you can view the data in Partner Center or use the Microsoft Store analytics API to retrieve this data programmatically.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1b185-109">Wenn Sie eine Bewertung-Funktion in Ihrer app hinzufügen, müssen alle Rezensionen der Benutzer auf den Store Bewertung Mechanismen, unabhängig von der Bewertung ausgewählte Star senden.</span><span class="sxs-lookup"><span data-stu-id="1b185-109">When adding a rating function within your app, all reviews must send the user to the Store's rating mechanisms, regardless of star rating chosen.</span></span> <span data-ttu-id="1b185-110">Wenn Sie Feedback oder Kommentare von Benutzern erfassen, muss es deutlich gemacht werden, dass er bezieht sich nicht auf die app-Bewertung oder Rezensionen im Store jedoch direkt an die app-Entwickler gesendet.</span><span class="sxs-lookup"><span data-stu-id="1b185-110">If you collect feedback or comments from users, it must be clear that it is not related to the app rating or reviews in the Store but is sent directly to the app developer.</span></span> <span data-ttu-id="1b185-111">Finden Sie unter den Entwickler Verhaltensregeln für Weitere Informationen im Zusammenhang mit [Fraudulent oder unehrlichen Aktivitäten](https://docs.microsoft.com/legal/windows/agreements/store-developer-code-of-conduct#3-fraudulent-or-dishonest-activities).</span><span class="sxs-lookup"><span data-stu-id="1b185-111">See the Developer Code of Conduct for more information related to [Fraudulent or Dishonest Activities](https://docs.microsoft.com/legal/windows/agreements/store-developer-code-of-conduct#3-fraudulent-or-dishonest-activities).</span></span>

## <a name="show-a-rating-and-review-dialog-in-your-app"></a><span data-ttu-id="1b185-112">Ein Bewertungs- und Rezensionsdialogfeld in Ihrer App anzeigen</span><span class="sxs-lookup"><span data-stu-id="1b185-112">Show a rating and review dialog in your app</span></span>

<span data-ttu-id="1b185-113">Wenn Sie programmgesteuert ein Dialogfeld von Ihrer app anzeigen möchten, die Ihre Kunden auffordert zu Ihrer app zu bewerten und eine Rezension zu senden, rufen Sie die [RequestRateAndReviewAppAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.requestrateandreviewappasync) -Methode im [Windows.Services.Store](https://docs.microsoft.com/uwp/api/windows.services.store) -Namespace.</span><span class="sxs-lookup"><span data-stu-id="1b185-113">To programmatically show a dialog from your app that asks your customer to rate your app and submit a review, call the [RequestRateAndReviewAppAsync](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext.requestrateandreviewappasync) method in the [Windows.Services.Store](https://docs.microsoft.com/uwp/api/windows.services.store) namespace.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="1b185-114">Die Anforderung zum Anzeigen des Bewertungs- und Rezensionsdialogfelds muss im UI-Thread in Ihrer App aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="1b185-114">The request to show the rating and review dialog must be called on the UI thread in your app.</span></span>

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

<span data-ttu-id="1b185-115">Die **RequestRateAndReviewAppAsync** -Methode wurde in Windows 10, Version 1809, eingeführt und kann nur in Projekten für die **Windows 10 October 2018 verwendet werden Update (10.0; Build 17763)** oder einer neueren Version in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1b185-115">The **RequestRateAndReviewAppAsync** method was introduced in Windows 10, version 1809, and it can only be used in projects that target **Windows 10 October 2018 Update (10.0; Build 17763)** or a later release in Visual Studio.</span></span>

### <a name="response-data-for-the-rating-and-review-request"></a><span data-ttu-id="1b185-116">Antwortdaten für die Bewertungs- und Rezensionsanforderung</span><span class="sxs-lookup"><span data-stu-id="1b185-116">Response data for the rating and review request</span></span>

<span data-ttu-id="1b185-117">Nach Übermittlung die Anforderung zum Anzeigen eines bewertungs- und rezensionsdialogfeldes, enthält die [ExtendedJsonData](https://docs.microsoft.com/uwp/api/windows.services.store.storerateandreviewresult.extendedjsondata) -Eigenschaft der [StoreRateAndReviewResult](https://docs.microsoft.com/uwp/api/windows.services.store.storerateandreviewresult) -Klasse eine JSON-formatierte Zeichenfolge, die angibt, ob die Anforderung erfolgreich war.</span><span class="sxs-lookup"><span data-stu-id="1b185-117">After you submit the request to display the rating and review dialog, the [ExtendedJsonData](https://docs.microsoft.com/uwp/api/windows.services.store.storerateandreviewresult.extendedjsondata) property of the [StoreRateAndReviewResult](https://docs.microsoft.com/uwp/api/windows.services.store.storerateandreviewresult) class contains a JSON-formatted string that indicates whether the request was successful.</span></span>

<span data-ttu-id="1b185-118">Das folgende Beispiel veranschaulicht den Rückgabewert für diese Anforderung, nachdem der Kunde erfolgreich eine Bewertung oder Rezension übermittelt hat.</span><span class="sxs-lookup"><span data-stu-id="1b185-118">The following example demonstrates the return value for this request after the customer successfully submits a rating or review.</span></span>

```json
{ 
  "status": "success", 
  "data": {
    "updated": false
  },
  "errorDetails": "Success"
}
```

<span data-ttu-id="1b185-119">Das folgende Beispiel veranschaulicht den Rückgabewert für diese Anforderung, nachdem der Kunde gewählt hat, keine Bewertung oder Rezension zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="1b185-119">The following example demonstrates the return value for this request after the customer chooses not to submit a rating or review.</span></span>

```json
{ 
  "status": "aborted", 
  "errorDetails": "Navigation was unsuccessful"
}
```

<span data-ttu-id="1b185-120">In der folgenden Tabelle werden die Felder in der Zeichenfolge im JSON-Format erläutert.</span><span class="sxs-lookup"><span data-stu-id="1b185-120">The following table describes the fields in the JSON-formatted data string.</span></span>

| <span data-ttu-id="1b185-121">Feld</span><span class="sxs-lookup"><span data-stu-id="1b185-121">Field</span></span>          | <span data-ttu-id="1b185-122">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="1b185-122">Description</span></span>                                                                                                                                   |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| *<span data-ttu-id="1b185-123">status</span><span class="sxs-lookup"><span data-stu-id="1b185-123">status</span></span>*       | <span data-ttu-id="1b185-124">Eine Zeichenfolge, die angibt, ob der Kunde eine Bewertung oder Rezension erfolgreich gesendet hat.</span><span class="sxs-lookup"><span data-stu-id="1b185-124">A string that indicates whether the customer successfully submitted a rating or review.</span></span> <span data-ttu-id="1b185-125">Die unterstützten Werte sind **success** und **aborted**.</span><span class="sxs-lookup"><span data-stu-id="1b185-125">The supported values are **success** and **aborted**.</span></span> |
| *<span data-ttu-id="1b185-126">data</span><span class="sxs-lookup"><span data-stu-id="1b185-126">data</span></span>*         | <span data-ttu-id="1b185-127">Ein Objekt, das nur einen booleschen Wert mit dem Namen *aktualisiert* enthält.</span><span class="sxs-lookup"><span data-stu-id="1b185-127">An object that contains a single Boolean value named *updated*.</span></span> <span data-ttu-id="1b185-128">Dieser Wert gibt an, ob der Kunde eine vorhandene Bewertung oder Rezension aktualisiert hat.</span><span class="sxs-lookup"><span data-stu-id="1b185-128">This value indicates whether the customer updated an existing rating or review.</span></span> <span data-ttu-id="1b185-129">Das *data*-Objekt ist nur in den Erfolgsantworten enthalten.</span><span class="sxs-lookup"><span data-stu-id="1b185-129">The *data* object is included in success responses only.</span></span> |
| *<span data-ttu-id="1b185-130">errorDetails</span><span class="sxs-lookup"><span data-stu-id="1b185-130">errorDetails</span></span>* | <span data-ttu-id="1b185-131">Eine Zeichenfolge, die Fehlerdetails für die Anforderung enthält.</span><span class="sxs-lookup"><span data-stu-id="1b185-131">A string that contains the error details for the request.</span></span>                                                                                     |

## <a name="launch-the-rating-and-review-page-for-your-app-in-the-store"></a><span data-ttu-id="1b185-132">Die Bewertungs- und Rezensionsseite für Ihre App im Store starten</span><span class="sxs-lookup"><span data-stu-id="1b185-132">Launch the rating and review page for your app in the Store</span></span>

<span data-ttu-id="1b185-133">Wenn Sie programmgesteuert eine Bewertungs- und Rezensionsseite für Ihre App im Store öffnen möchten, können Sie die [LaunchUriAsync](https://docs.microsoft.com/uwp/api/windows.system.launcher.launchuriasync)-Methode mit dem ```ms-windows-store://review```-URI-Schema verwenden, wie in diesem Codebeispiel gezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="1b185-133">If you want to programmatically open the rating and review page for your app in the Store, you can use the [LaunchUriAsync](https://docs.microsoft.com/uwp/api/windows.system.launcher.launchuriasync) method with the ```ms-windows-store://review``` URI scheme as demonstrated in this code example.</span></span>

```csharp
bool result = await Windows.System.Launcher.LaunchUriAsync(new Uri("ms-windows-store://review/?ProductId=9WZDNCRFHVJL"));
```

<span data-ttu-id="1b185-134">Weitere Informationen finden Sie unter [Die Microsoft Store App starten](../launch-resume/launch-store-app.md).</span><span class="sxs-lookup"><span data-stu-id="1b185-134">For more information, see [Launch the Microsoft Store app](../launch-resume/launch-store-app.md).</span></span>

## <a name="analyze-your-ratings-and-reviews-data"></a><span data-ttu-id="1b185-135">Ihre Bewertungs- und Rezensionsdaten analysieren</span><span class="sxs-lookup"><span data-stu-id="1b185-135">Analyze your ratings and reviews data</span></span>

<span data-ttu-id="1b185-136">Sie haben mehrere Optionen, um die Bewertungs- und Rezensionsdaten von Ihren Kunden zu analysieren:</span><span class="sxs-lookup"><span data-stu-id="1b185-136">To analyze the ratings and reviews data from your customers, you have several options:</span></span>
* <span data-ttu-id="1b185-137">Sie können den Bericht ["Rezensionen"](../publish/reviews-report.md) im Partner Center verwenden, um die Bewertungen und Prüfungen von Ihren Kunden anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="1b185-137">You can use the [Reviews](../publish/reviews-report.md) report in Partner Center to see the ratings and reviews from your customers.</span></span> <span data-ttu-id="1b185-138">Sie können diesen Bericht auch herunterladen, um ihn offline zu sehen.</span><span class="sxs-lookup"><span data-stu-id="1b185-138">You can also download this report to view it offline.</span></span>
* <span data-ttu-id="1b185-139">Sie können die [Abrufen von App-Bewertungen](get-app-ratings.md)- und [Abrufen von App-Rezensionen](get-app-reviews.md)-Methoden in der Store-Analyse-API zum programmgesteuerten Abrufen der Bewertungen und Prüfungen von Ihren Kunden im JSON-Format verwenden.</span><span class="sxs-lookup"><span data-stu-id="1b185-139">You can use the [Get app ratings](get-app-ratings.md) and [Get app reviews](get-app-reviews.md) methods in the Store analytics API to programmatically retrieve the ratings and reviews from your customers in JSON format.</span></span>

## <a name="related-topics"></a><span data-ttu-id="1b185-140">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="1b185-140">Related topics</span></span>

* [<span data-ttu-id="1b185-141">Senden von Anfragen an den Store</span><span class="sxs-lookup"><span data-stu-id="1b185-141">Send requests to the Store</span></span>](send-requests-to-the-store.md)
* [<span data-ttu-id="1b185-142">Starten der Microsoft Store-App</span><span class="sxs-lookup"><span data-stu-id="1b185-142">Launch the Microsoft Store app</span></span>](../launch-resume/launch-store-app.md)
* [<span data-ttu-id="1b185-143">Rezensionsbericht</span><span class="sxs-lookup"><span data-stu-id="1b185-143">Reviews report</span></span>](../publish/reviews-report.md)
