---
author: QuinnRadich
description: Ermöglicht Benutzern das Anzeigen und Festlegen von Bewertungen, die Zufriedenheit mit Inhalten und Diensten widerspiegeln.
title: Bewertungssteuerelement
template: detail.hbs
ms.author: quradic
ms.date: 10/25/2017
ms.topic: article
keywords: Windows10, UWP
pm-contact: abarlow
design-contact: kimsea
dev-contact: mitra
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 45cea3986f149714b1f0f14743bdecd83f8b6782
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2018
ms.locfileid: "5996208"
---
# <a name="rating-control"></a><span data-ttu-id="494a5-104">Bewertungssteuerelement</span><span class="sxs-lookup"><span data-stu-id="494a5-104">Rating control</span></span>

<span data-ttu-id="494a5-105">Das Bewertungssteuerelement ermöglicht Benutzern das Anzeigen und Festlegen von Bewertungen, die den Grad der Zufriedenheit mit Inhalten und Diensten widerspiegeln.</span><span class="sxs-lookup"><span data-stu-id="494a5-105">The rating control allows users to view and set ratings that reflect degrees of satisfaction with content and services.</span></span> <span data-ttu-id="494a5-106">Benutzer können per Toucheingabe, Stift, Maus, Gamepad und Tastatur mit dem Bewertungssteuerelement interagieren.</span><span class="sxs-lookup"><span data-stu-id="494a5-106">Users can interact with the rating control with touch, pen, mouse, gamepad or keyboard.</span></span> <span data-ttu-id="494a5-107">Die Anleitungen zeigen, wie die Funktionen des Bewertungssteuerelements verwendet werden, um Flexibilität und Anpassung bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="494a5-107">The follow guidance shows how to use the rating control's features to provide flexibility and customization.</span></span>

> <span data-ttu-id="494a5-108">**Wichtige APIs**: [RatingControl-Klasse](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.ratingcontrol)</span><span class="sxs-lookup"><span data-stu-id="494a5-108">**Important APIs**: [RatingControl class](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.ratingcontrol)</span></span>

![Beispiel für Bewertungssteuerelement](images/rating_rs2_doc_ratings_intro.png)

## <a name="examples"></a><span data-ttu-id="494a5-110">Beispiele</span><span class="sxs-lookup"><span data-stu-id="494a5-110">Examples</span></span>

<table>
<th align="left"><span data-ttu-id="494a5-111">XAML-Steuerelementekatalog</span><span class="sxs-lookup"><span data-stu-id="494a5-111">XAML Controls Gallery</span></span><th>
<tr>
<td><img src="images/xaml-controls-gallery-sm.png" alt="XAML controls gallery"></img></td>
<td>
    <p><span data-ttu-id="494a5-112">Wenn Sie die App <strong style="font-weight: semi-bold">XAML-Steuerelementekatalog</strong> installiert haben, klicken Sie hier, um <a href="xamlcontrolsgallery:/item/RatingControl">die App zu öffnen und RatingControl in Aktion zu sehen</a>.</span><span class="sxs-lookup"><span data-stu-id="494a5-112">If you have the <strong style="font-weight: semi-bold">XAML Controls Gallery</strong> app installed, click here to <a href="xamlcontrolsgallery:/item/RatingControl">open the app and see the RatingControl in action</a>.</span></span></p>
    <ul>
    <li><a href="https://www.microsoft.com/store/productId/9MSVH128X2ZT"><span data-ttu-id="494a5-113">Erwerben Sie die XAML-Steuerelementekatalog-App (Microsoft Store)</span><span class="sxs-lookup"><span data-stu-id="494a5-113">Get the XAML Controls Gallery app (Microsoft Store)</span></span></a></li>
    <li><a href="https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics"><span data-ttu-id="494a5-114">Erwerben Sie den Quellcode (GitHub)</span><span class="sxs-lookup"><span data-stu-id="494a5-114">Get the source code (GitHub)</span></span></a></li>
    </ul>
</td>
</tr>
</table>

### <a name="editable-rating-with-placeholder-value"></a><span data-ttu-id="494a5-115">Bearbeitbare Bewertung mit Platzhalterwert</span><span class="sxs-lookup"><span data-stu-id="494a5-115">Editable rating with placeholder value</span></span>

<span data-ttu-id="494a5-116">Das Bewertungssteuerelement wird wahrscheinlich am häufigsten eingesetzt, um eine durchschnittliche Bewertung anzuzeigen, wobei dem Benutzer dennoch erlaubt wird, seine eigene Bewertung einzugeben.</span><span class="sxs-lookup"><span data-stu-id="494a5-116">Perhaps the most common way to use the rating control is to display an average rating while still allowing the user to enter their own rating value.</span></span> <span data-ttu-id="494a5-117">In diesem Szenario wird das Bewertungssteuerelement anfänglich so festgelegt, dass es die durchschnittliche Zufriedenheitsbewertung aller Benutzer eines bestimmten Dienstes oder einer Art von Inhalt (z.B. Musik, Videos, Bücher usw.) widerspiegelt.</span><span class="sxs-lookup"><span data-stu-id="494a5-117">In this scenario, the rating control is initially set to reflect the average satisfaction rating of all users of a particular service or type of content (such as a music, videos, books, etc.).</span></span> <span data-ttu-id="494a5-118">Es bleibt in diesem Zustand, bis ein Benutzer mit dem Steuerelement mit dem Ziel interagiert, ein Element persönlich zu bewerten.</span><span class="sxs-lookup"><span data-stu-id="494a5-118">It remains in this state until a user interacts with the control with the goal of individually rating an item.</span></span> <span data-ttu-id="494a5-119">Durch diese Interaktion wird der Zustand des Bewertungssteuerelements entsprechend der persönlichen Zufriedenheitsbewertung des Benutzers geändert.</span><span class="sxs-lookup"><span data-stu-id="494a5-119">This interaction changes the state of the ratings control to reflect the user's personal satisfaction rating.</span></span>

#### <a name="initial-average-rating-state"></a><span data-ttu-id="494a5-120">Anfänglicher durchschnittlicher Bewertungszustand</span><span class="sxs-lookup"><span data-stu-id="494a5-120">Initial average rating state</span></span>
![Anfänglicher durchschnittlicher Bewertungszustand](images/rating_rs2_doc_movie_aggregate.png)

#### <a name="representation-of-user-rating-once-set"></a><span data-ttu-id="494a5-122">Darstellung der Benutzerbewertung, sobald sie festgelegt wurde</span><span class="sxs-lookup"><span data-stu-id="494a5-122">Representation of user rating once set</span></span>

![Darstellung der Benutzerbewertung, sobald sie festgelegt wurde](images/rating_rs2_doc_movie_user.png)

```XAML
<RatingControl x:Name="MyRating" ValueChanged="RatingChanged"/>
```

```csharp
private void RatingChanged(RatingControl sender, object args)
{
    if (sender.Value == null)
    {
        MyRating.Caption = "(" + SomeWebService.HowManyPreviousRatings() + ")";
    }

    else
    {
        MyRating.Caption = "Your rating";
    }
}
```

### <a name="read-only-rating-mode"></a><span data-ttu-id="494a5-124">Schreibgeschützter Bewertungsmodus</span><span class="sxs-lookup"><span data-stu-id="494a5-124">Read-only rating mode</span></span>

<span data-ttu-id="494a5-125">Manchmal müssen Sie Bewertungen von sekundärem Inhalt anzeigen, z.B. Bewertungen, die in empfohlenem Inhalt angezeigt werden, oder wenn eine Liste von Kommentaren und die entsprechenden Bewertungen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="494a5-125">Sometimes you need to show ratings of secondary content, such as that displayed in recommended content or when displaying a list of comments and their corresponding ratings.</span></span> <span data-ttu-id="494a5-126">In diesem Fall sollte der Benutzer die Bewertung nicht bearbeiten können. Daher können Sie für das Steuerelement den schreibgeschützten Modus festlegen.</span><span class="sxs-lookup"><span data-stu-id="494a5-126">In this case, the user shouldn’t be able to edit the rating, so you can make the control read-only.</span></span>
<span data-ttu-id="494a5-127">Das Bewertungssteuerelement sollte auch dann im schreibgeschützten Modus verwendet werden, wenn es in sehr großen virtualisierten Listen mit Inhalt, für UI-Design und aus Leistungsgründen, eingesetzt wird.</span><span class="sxs-lookup"><span data-stu-id="494a5-127">The read only mode is also the recommended way of using the rating control when it is used in very large virtualized lists of content, for both UI design and performance reasons.</span></span>

![Schreibgeschützte lange Liste](images/rating_rs2_doc_reviews.png)

<span data-ttu-id="494a5-129">Dazu würden Sie die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="494a5-129">To do this you would do the following:</span></span>

```XAML
<RatingControl IsReadOnly="True"/>
```

## <a name="additional-functionality"></a><span data-ttu-id="494a5-130">Zusätzliche Funktionalität</span><span class="sxs-lookup"><span data-stu-id="494a5-130">Additional functionality</span></span>

<span data-ttu-id="494a5-131">Das Bewertungssteuerelement verfügt über viele zusätzliche Funktionen, die verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="494a5-131">The rating control has many additional features which can be used.</span></span> <span data-ttu-id="494a5-132">Details zur Verwendung dieser Funktionen finden Sie in unserer MSDN-Referenzdokumentation.</span><span class="sxs-lookup"><span data-stu-id="494a5-132">Details for using these features can be found in our MSDN reference documentation.</span></span>
<span data-ttu-id="494a5-133">Hier finden Sie eine Auflistung einiger zusätzlicher Funktionen:</span><span class="sxs-lookup"><span data-stu-id="494a5-133">Here is a non-comprehensive list of additional functionality:</span></span>
-   <span data-ttu-id="494a5-134">Sehr gute Leistung bei langen Listen</span><span class="sxs-lookup"><span data-stu-id="494a5-134">Great long list performance</span></span>
-   <span data-ttu-id="494a5-135">Kompakte Größe für UI-Szenarien mit wenig Platz</span><span class="sxs-lookup"><span data-stu-id="494a5-135">Compact sizing for tight UI scenarios</span></span>
-   <span data-ttu-id="494a5-136">Kontinuierliche Wertfüllung und Bewertung</span><span class="sxs-lookup"><span data-stu-id="494a5-136">Continuous value fill and rating</span></span>
-   <span data-ttu-id="494a5-137">Abstandsanpassung</span><span class="sxs-lookup"><span data-stu-id="494a5-137">Spacing customization</span></span>
-   <span data-ttu-id="494a5-138">Deaktivieren von Wachstumsanimationen</span><span class="sxs-lookup"><span data-stu-id="494a5-138">Disable growth animations</span></span>
-   <span data-ttu-id="494a5-139">Anpassung der Anzahl von Sternen</span><span class="sxs-lookup"><span data-stu-id="494a5-139">Customization of the number of stars</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="494a5-140">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="494a5-140">Get the sample code</span></span>

- <span data-ttu-id="494a5-141">[Beispiel eines XAML-Steuerelementekatalogs](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) – Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.</span><span class="sxs-lookup"><span data-stu-id="494a5-141">[XAML Controls Gallery sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlUIBasics) - See all the XAML controls in an interactive format.</span></span>