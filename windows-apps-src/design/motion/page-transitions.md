---
author: QuinnRadich
Description: Learn how to use page transitions in your UWP apps.
title: Seitenübergänge in UWP-Apps
template: detail.hbs
ms.author: quradic
ms.date: 04/08/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
pm-contact: stmoy
ms.localizationpriority: medium
ms.openlocfilehash: 0afc2c55ab0d0bdd2bee0206f986b2724d331eaf
ms.sourcegitcommit: 194ab5aa395226580753869c6b66fce88be83522
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2018
ms.locfileid: "4152649"
---
# <a name="page-transitions"></a><span data-ttu-id="00d96-103">Seitenübergänge</span><span class="sxs-lookup"><span data-stu-id="00d96-103">Page transitions</span></span>

<span data-ttu-id="00d96-104">Seitenübergänge sind Animationen, die abgespielt werden, wenn Benutzer zwischen Seiten in einer App navigieren und Feedback als Beziehung zwischen Seiten liefern.</span><span class="sxs-lookup"><span data-stu-id="00d96-104">Page transitions navigate users between pages in an app, providing feedback as the relationship between pages.</span></span> <span data-ttu-id="00d96-105">Seitenübergänge zeigen dem Benutzer, ob er an der Spitze einer Navigationshierarchie steht, zwischen Geschwisterseiten wechselt oder tiefer in die Seitenhierarchie navigiert.</span><span class="sxs-lookup"><span data-stu-id="00d96-105">Page transitions help users understand if they are at the top of a navigation hierarchy, moving between sibling pages, or navigating deeper into the page hierarchy.</span></span>

<span data-ttu-id="00d96-106">Für die Navigation zwischen Seiten in einer App stehen zwei verschiedene Animationen zur Verfügung: *Seitenaktualisierung* und *Drill*. Sie werden durch Unterklassen von [**NavigationTransitionInfo**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.animation.navigationtransitioninfo) dargestellt.</span><span class="sxs-lookup"><span data-stu-id="00d96-106">Two different animations are provided for navigation between pages in an app, *Page refresh* and *Drill*, and are represented by subclasses of [**NavigationTransitionInfo**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.animation.navigationtransitioninfo).</span></span>

## <a name="page-refresh"></a><span data-ttu-id="00d96-107">Seite aktualisieren</span><span class="sxs-lookup"><span data-stu-id="00d96-107">Page refresh</span></span>

<span data-ttu-id="00d96-108">Seitenaktualisierung ist eine Kombination aus einer Slide-Up-Animation und einer Einblendungsanimation für den eingehenden Inhalt.</span><span class="sxs-lookup"><span data-stu-id="00d96-108">Page refresh is a combination of a slide up animation and a fade in animation for the incoming content.</span></span> <span data-ttu-id="00d96-109">Verwenden Sie die Seitenaktualisierung, wenn der Benutzer an den Anfang eines Navigationsstapels gebracht wird, z. B. beim Navigieren zwischen Registerkarten oder Navigationselementen auf der linken Navigationsleiste.</span><span class="sxs-lookup"><span data-stu-id="00d96-109">Use page refresh when the user is taken to the top of a navigational stack, such as navigating between tabs or left-nav items.</span></span>

<span data-ttu-id="00d96-110">Der gewünschte Effekt ist ein Neubeginn für den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="00d96-110">The desired feeling is that the user has started over.</span></span>

![Seitenaktualisierungsanimation](images/page-refresh.gif)

<span data-ttu-id="00d96-112">Die Seitenaktualisierungsanimation wird durch die Klasse [**EntranceNavigationTransitionInfo**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.animation.entrancenavigationtransitioninfo) dargestellt.</span><span class="sxs-lookup"><span data-stu-id="00d96-112">The page refresh animation is represented by the [**EntranceNavigationTransitionInfoClass**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.animation.entrancenavigationtransitioninfo).</span></span>

```csharp
// Explicitly play the page refresh animation
myFrame.Navigate(typeof(Page2), null, new EntranceNavigationTransitionInfo());

```

<span data-ttu-id="00d96-113">**Hinweis:**: Ein [**Frame**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.frame) verwendet automatisch [**NavigationThemeTransition**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.animation.navigationthemetransition) zur Animation der Navigation zwischen zwei Seiten.</span><span class="sxs-lookup"><span data-stu-id="00d96-113">**Note**: A [**Frame**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.frame) automatically uses [**NavigationThemeTransition**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.animation.navigationthemetransition) to animate navigation between two pages.</span></span> <span data-ttu-id="00d96-114">Standardmäßig ist die Animation eine Seitenaktualisierung.</span><span class="sxs-lookup"><span data-stu-id="00d96-114">By default, the animation is page refresh.</span></span>

## <a name="drill"></a><span data-ttu-id="00d96-115">Drill</span><span class="sxs-lookup"><span data-stu-id="00d96-115">Drill</span></span>

<span data-ttu-id="00d96-116">Verwenden Sie Drill, wenn Benutzer tiefer in eine Anwendung navigieren, z. B. um nach der Auswahl eines Elements weitere Informationen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="00d96-116">Use drill when users navigate deeper into an app, such as displaying more information after selecting an item.</span></span>

<span data-ttu-id="00d96-117">Der gewünschte Effekt ist, dass der Benutzer tiefer in die App vorgedrungen ist.</span><span class="sxs-lookup"><span data-stu-id="00d96-117">The desired feeling is that the user has gone deeper into the app.</span></span>

![Drill-Animation](images/drill.gif)

<span data-ttu-id="00d96-119">Die Drill-Animation wird durch die Klasse [**DrillInNavigationTransitionInfo**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.animation.drillinnavigationtransitioninfo) dargestellt.</span><span class="sxs-lookup"><span data-stu-id="00d96-119">The drill animation is represented by the [**DrillInNavigationTransitionInfo**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.animation.drillinnavigationtransitioninfo) class.</span></span>

```csharp
// Play the drill in animation
myFrame.Navigate(typeof(Page2), null, new DrillInNavigationTransitionInfo());
```

## <a name="suppress"></a><span data-ttu-id="00d96-120">Unterdrückung</span><span class="sxs-lookup"><span data-stu-id="00d96-120">Suppress</span></span>

<span data-ttu-id="00d96-121">Um die Wiedergabe von Animationen während der Navigation zu vermeiden, verwenden Sie [**SuppressNavigationTransitionInfo**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.animation.suppressnavigationtransitioninfo) anstelle anderer **NavigationTransitionInfo**-Subtypen.</span><span class="sxs-lookup"><span data-stu-id="00d96-121">To avoid playing any animation during navigation, use [**SuppressNavigationTransitionInfo**](https://docs.microsoft.com/uwp/api/windows.ui.xaml.media.animation.suppressnavigationtransitioninfo) in the place of other **NavigationTransitionInfo** subtypes.</span></span>

```csharp
// Suppress the default animation
myFrame.Navigate(typeof(Page2), null, new SuppressNavigationTransitionInfo());
```

<span data-ttu-id="00d96-122">Das Unterdrücken der Animation ist hilfreich, wenn Sie Ihre eigenen Übergang mit [verbundenen Animationen](connected-animation.md) erstellen oder das implizite Einblenden/Ausblenden von Animationen nutzen.</span><span class="sxs-lookup"><span data-stu-id="00d96-122">Suppressing the animation is useful if you are building your own transition using [Connected Animations](connected-animation.md) or implicit show/hide animations.</span></span>

## <a name="backwards-navigation"></a><span data-ttu-id="00d96-123">Rückwärtsnavigation</span><span class="sxs-lookup"><span data-stu-id="00d96-123">Backwards navigation</span></span>

<span data-ttu-id="00d96-124">Um einen bestimmten Übergang bei der Rückwärtsnavigation darzustellen, verwenden Sie `Frame.GoBack(NavigationTransitionInfo)`.</span><span class="sxs-lookup"><span data-stu-id="00d96-124">You can use `Frame.GoBack(NavigationTransitionInfo)` to play a specific transition when navigating backwards.</span></span>

<span data-ttu-id="00d96-125">Dies kann nützlich sein, wenn Sie das Navigationsverhalten dynamisch an die Bildschirmgröße anpassen – z. B. in einem dynamischen Master/Detail-Szenario.</span><span class="sxs-lookup"><span data-stu-id="00d96-125">This can be useful when you modify navigation behavior dynamically based on screen size; for example, in a responsive master/detail scenario.</span></span>

## <a name="related-topics"></a><span data-ttu-id="00d96-126">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="00d96-126">Related topics</span></span>

- [<span data-ttu-id="00d96-127">Navigieren zwischen zwei Seiten</span><span class="sxs-lookup"><span data-stu-id="00d96-127">Navigate between two pages</span></span>](../basics/navigate-between-two-pages.md)
- [<span data-ttu-id="00d96-128">Bewegung in UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="00d96-128">Motion in UWP apps</span></span>](index.md)
