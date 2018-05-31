---
author: serenaz
Description: Learn how to use page transitions in your UWP apps.
title: Seitenübergänge in UWP-Apps
template: detail.hbs
ms.author: sezhen
ms.date: 04/08/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
pm-contact: stmoy
ms.localizationpriority: medium
ms.openlocfilehash: dc42199eba00071f5dbabd83a4ae524298a619ee
ms.sourcegitcommit: 91511d2d1dc8ab74b566aaeab3ef2139e7ed4945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2018
ms.locfileid: "1818358"
---
# <a name="page-transitions"></a><span data-ttu-id="81c7c-103">Seitenübergang</span><span class="sxs-lookup"><span data-stu-id="81c7c-103">Page transitions</span></span>

<span data-ttu-id="81c7c-104">Seitenübergänge sind Animationen, die abgespielt werden, wenn Benutzer zwischen Seiten in einer App navigieren und Feedback als Beziehung zwischen Seiten liefern.</span><span class="sxs-lookup"><span data-stu-id="81c7c-104">Page transitions are animations that play when users navigate between pages in an app, providing feedback as the relationship between pages.</span></span> <span data-ttu-id="81c7c-105">Seitenübergänge zeigen dem Benutzer, ob er an der Spitze einer Navigationshierarchie steht, zwischen Geschwisterseiten wechselt oder tiefer in die Seitenhierarchie navigiert.</span><span class="sxs-lookup"><span data-stu-id="81c7c-105">Page transitions help users understand if they are at the top of a navigation hierarchy, moving between sibling pages, or navigating deeper into the page hierarchy.</span></span>

<span data-ttu-id="81c7c-106">Zwei verschiedene Animationen stehen für die Navigation zwischen den Seiten in einer App zur Verfügung: *Seitenaktualisierung* und *Drill*. Sie werden durch Unterklassen von [NavigationTransitionInfo](/uwp/api/windows.ui.xaml.media.animation.navigationtransitioninfo) dargestellt.</span><span class="sxs-lookup"><span data-stu-id="81c7c-106">Two different animations are provided for navigation between pages in an app, *page refresh* and *drill*, and are represented by subclasses of [NavigationTransitionInfo](/uwp/api/windows.ui.xaml.media.animation.navigationtransitioninfo).</span></span>

## <a name="page-refresh"></a><span data-ttu-id="81c7c-107">Seite aktualisieren</span><span class="sxs-lookup"><span data-stu-id="81c7c-107">Page refresh</span></span>

<span data-ttu-id="81c7c-108">Die Seitenaktualisierung ist eine Kombination aus einer Folie Animation und eine Überblendung in die Animation für den eingehenden Inhalt.</span><span class="sxs-lookup"><span data-stu-id="81c7c-108">Page refresh is a combination of a slide up animation and a fade in animation for the incoming content.</span></span> <span data-ttu-id="81c7c-109">Der gewünschte Effekt ist ein Neubeginn für den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="81c7c-109">The desired feeling is that the user has started over.</span></span>

<span data-ttu-id="81c7c-110">Verwenden Sie die Seitenaktualisierung, wenn der Benutzer an den Anfang eines Navigationsstapels gebracht wird, z. B. beim Navigieren zwischen [tab](../controls-and-patterns/tabs-pivot.md) oder [left-nav](../controls-and-patterns/navigationview.md)-Navigationselementen.</span><span class="sxs-lookup"><span data-stu-id="81c7c-110">Use page refresh when the user is taken to the top of a navigational stack, such as navigating between [tabs](../controls-and-patterns/tabs-pivot.md) or [left-nav](../controls-and-patterns/navigationview.md) items.</span></span> <span data-ttu-id="81c7c-111">[Frame.Navigate()](/uwp/api/windows.ui.xaml.controls.frame.navigate) verwendet standardmäßig die Seitenaktualisierung.</span><span class="sxs-lookup"><span data-stu-id="81c7c-111">By default, [Frame.Navigate()](/uwp/api/windows.ui.xaml.controls.frame.navigate) uses page refresh.</span></span>

![Seitenaktualisierungsanimation](images/page-refresh.gif)

<span data-ttu-id="81c7c-113">Die Animation zur Seitenaktualisierung wird durch [EntranceNavigationTransitionInfoClass](/uwp/api/windows.ui.xaml.media.animation.entrancenavigationtransitioninfo) dargestellt.</span><span class="sxs-lookup"><span data-stu-id="81c7c-113">The page refresh animation is represented by the [EntranceNavigationTransitionInfoClass](/uwp/api/windows.ui.xaml.media.animation.entrancenavigationtransitioninfo).</span></span>

```csharp
// Explicitly play the page refresh animation
myFrame.Navigate(typeof(Page2), null, new EntranceNavigationTransitionInfo());
```

## <a name="drill"></a><span data-ttu-id="81c7c-114">Drill</span><span class="sxs-lookup"><span data-stu-id="81c7c-114">Drill</span></span>

<span data-ttu-id="81c7c-115">Verwenden Sie Drill, wenn Benutzer tiefer in eine Anwendung navigieren, z. B. um nach der Auswahl eines Elements weitere Informationen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="81c7c-115">Use drill when users navigate deeper into an app, such as displaying more information after selecting an item.</span></span>

<span data-ttu-id="81c7c-116">Der gewünschte Effekt ist, dass der Benutzer tiefer in die App vorgedrungen ist.</span><span class="sxs-lookup"><span data-stu-id="81c7c-116">The desired feeling is that the user has gone deeper into the app.</span></span>

![Drill-Animation](images/drill.gif)

<span data-ttu-id="81c7c-118">Die Drill-Animation wird durch die Klasse [DrillInNavigationTransitionInfo](/uwp/api/windows.ui.xaml.media.animation.drillinnavigationtransitioninfo) repräsentiert.</span><span class="sxs-lookup"><span data-stu-id="81c7c-118">The drill animation is represented by the [DrillInNavigationTransitionInfo](/uwp/api/windows.ui.xaml.media.animation.drillinnavigationtransitioninfo) class.</span></span>

```csharp
// Play the drill in animation
myFrame.Navigate(typeof(Page2), null, new DrillInNavigationTransitionInfo());
```

## <a name="suppress"></a><span data-ttu-id="81c7c-119">Unterdrückung</span><span class="sxs-lookup"><span data-stu-id="81c7c-119">Suppress</span></span>

<span data-ttu-id="81c7c-120">Das Unterdrücken der Animation ist hilfreich, wenn Sie Ihre eigenen Übergang mit [verbundenen Animationen](connected-animation.md) erstellen oder das implizite Einblenden/Ausblenden von Animationen nutzen.</span><span class="sxs-lookup"><span data-stu-id="81c7c-120">Suppressing the animation is useful if you are building your own transition using [Connected Animations](connected-animation.md) or implicit show/hide animations.</span></span>

<span data-ttu-id="81c7c-121">Um das Abspielen von Animationen während der Navigation zu vermeiden, verwenden Sie [SuppressNavigationTransitionInfo](/uwp/api/windows.ui.xaml.media.animation.suppressnavigationtransitioninfo) anstelle anderer [NavigationTransitionInfo](/uwp/api/windows.ui.xaml.media.animation.navigationtransitioninfo)-Subtypen.</span><span class="sxs-lookup"><span data-stu-id="81c7c-121">To avoid playing any animation during navigation, use [SuppressNavigationTransitionInfo](/uwp/api/windows.ui.xaml.media.animation.suppressnavigationtransitioninfo) in the place of other [NavigationTransitionInfo](/uwp/api/windows.ui.xaml.media.animation.navigationtransitioninfo) subtypes.</span></span>

```csharp
// Suppress the default animation
myFrame.Navigate(typeof(Page2), null, new SuppressNavigationTransitionInfo());
```

## <a name="backwards-navigation"></a><span data-ttu-id="81c7c-122">Rückwärtsnavigation</span><span class="sxs-lookup"><span data-stu-id="81c7c-122">Backwards navigation</span></span>

<span data-ttu-id="81c7c-123">Standardmäßig spielt [Frame.GoBack()](/uwp/api/windows.ui.xaml.controls.frame.goback) die entsprechende „go back”-Animation auf Basis der abgespielten Animation ab, um zur Seite zu navigieren.</span><span class="sxs-lookup"><span data-stu-id="81c7c-123">By default, [Frame.GoBack()](/uwp/api/windows.ui.xaml.controls.frame.goback) plays the corresponding "go back" animation based on the animation played to navigate to the page.</span></span> <span data-ttu-id="81c7c-124">Beispielsweise wird eine App, die Drill-In zur Navigation auf eine Seite verendet, einen Drill-Out bei der Rückwärtsnavigation verwenden.</span><span class="sxs-lookup"><span data-stu-id="81c7c-124">For example, an app that uses drill in to navigate into a page will see a drill out when users navigate backwards.</span></span>

<span data-ttu-id="81c7c-125">Um einen bestimmten Übergang bei der Rückwärtsnavigation abzuspielen, verwenden Sie `Frame.GoBack(NavigationTransitionInfo)`.</span><span class="sxs-lookup"><span data-stu-id="81c7c-125">To play a specific transition when navigating backwards, use `Frame.GoBack(NavigationTransitionInfo)`.</span></span> <span data-ttu-id="81c7c-126">Dies kann nützlich sein, wenn Sie das Navigationsverhalten dynamisch an die Bildschirmgröße anpassen – z. B. in einem dynamischen Master/Detail-Szenario.</span><span class="sxs-lookup"><span data-stu-id="81c7c-126">This can be useful when you modify navigation behavior dynamically based on screen size, for example, in a responsive master/detail scenario.</span></span>

## <a name="related-topics"></a><span data-ttu-id="81c7c-127">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="81c7c-127">Related topics</span></span>

- [<span data-ttu-id="81c7c-128">Navigieren zwischen zwei Seiten</span><span class="sxs-lookup"><span data-stu-id="81c7c-128">Navigate between two pages</span></span>](../basics/navigate-between-two-pages.md)
- [<span data-ttu-id="81c7c-129">Bewegung in UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="81c7c-129">Motion in UWP apps</span></span>](index.md)
