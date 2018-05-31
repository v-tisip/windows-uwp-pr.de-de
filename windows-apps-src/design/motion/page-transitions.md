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
# <a name="page-transitions"></a>Seitenübergang

Seitenübergänge sind Animationen, die abgespielt werden, wenn Benutzer zwischen Seiten in einer App navigieren und Feedback als Beziehung zwischen Seiten liefern. Seitenübergänge zeigen dem Benutzer, ob er an der Spitze einer Navigationshierarchie steht, zwischen Geschwisterseiten wechselt oder tiefer in die Seitenhierarchie navigiert.

Zwei verschiedene Animationen stehen für die Navigation zwischen den Seiten in einer App zur Verfügung: *Seitenaktualisierung* und *Drill*. Sie werden durch Unterklassen von [NavigationTransitionInfo](/uwp/api/windows.ui.xaml.media.animation.navigationtransitioninfo) dargestellt.

## <a name="page-refresh"></a>Seite aktualisieren

Die Seitenaktualisierung ist eine Kombination aus einer Folie Animation und eine Überblendung in die Animation für den eingehenden Inhalt. Der gewünschte Effekt ist ein Neubeginn für den Benutzer.

Verwenden Sie die Seitenaktualisierung, wenn der Benutzer an den Anfang eines Navigationsstapels gebracht wird, z. B. beim Navigieren zwischen [tab](../controls-and-patterns/tabs-pivot.md) oder [left-nav](../controls-and-patterns/navigationview.md)-Navigationselementen. [Frame.Navigate()](/uwp/api/windows.ui.xaml.controls.frame.navigate) verwendet standardmäßig die Seitenaktualisierung.

![Seitenaktualisierungsanimation](images/page-refresh.gif)

Die Animation zur Seitenaktualisierung wird durch [EntranceNavigationTransitionInfoClass](/uwp/api/windows.ui.xaml.media.animation.entrancenavigationtransitioninfo) dargestellt.

```csharp
// Explicitly play the page refresh animation
myFrame.Navigate(typeof(Page2), null, new EntranceNavigationTransitionInfo());
```

## <a name="drill"></a>Drill

Verwenden Sie Drill, wenn Benutzer tiefer in eine Anwendung navigieren, z. B. um nach der Auswahl eines Elements weitere Informationen anzuzeigen.

Der gewünschte Effekt ist, dass der Benutzer tiefer in die App vorgedrungen ist.

![Drill-Animation](images/drill.gif)

Die Drill-Animation wird durch die Klasse [DrillInNavigationTransitionInfo](/uwp/api/windows.ui.xaml.media.animation.drillinnavigationtransitioninfo) repräsentiert.

```csharp
// Play the drill in animation
myFrame.Navigate(typeof(Page2), null, new DrillInNavigationTransitionInfo());
```

## <a name="suppress"></a>Unterdrückung

Das Unterdrücken der Animation ist hilfreich, wenn Sie Ihre eigenen Übergang mit [verbundenen Animationen](connected-animation.md) erstellen oder das implizite Einblenden/Ausblenden von Animationen nutzen.

Um das Abspielen von Animationen während der Navigation zu vermeiden, verwenden Sie [SuppressNavigationTransitionInfo](/uwp/api/windows.ui.xaml.media.animation.suppressnavigationtransitioninfo) anstelle anderer [NavigationTransitionInfo](/uwp/api/windows.ui.xaml.media.animation.navigationtransitioninfo)-Subtypen.

```csharp
// Suppress the default animation
myFrame.Navigate(typeof(Page2), null, new SuppressNavigationTransitionInfo());
```

## <a name="backwards-navigation"></a>Rückwärtsnavigation

Standardmäßig spielt [Frame.GoBack()](/uwp/api/windows.ui.xaml.controls.frame.goback) die entsprechende „go back”-Animation auf Basis der abgespielten Animation ab, um zur Seite zu navigieren. Beispielsweise wird eine App, die Drill-In zur Navigation auf eine Seite verendet, einen Drill-Out bei der Rückwärtsnavigation verwenden.

Um einen bestimmten Übergang bei der Rückwärtsnavigation abzuspielen, verwenden Sie `Frame.GoBack(NavigationTransitionInfo)`. Dies kann nützlich sein, wenn Sie das Navigationsverhalten dynamisch an die Bildschirmgröße anpassen – z. B. in einem dynamischen Master/Detail-Szenario.

## <a name="related-topics"></a>Verwandte Themen

- [Navigieren zwischen zwei Seiten](../basics/navigate-between-two-pages.md)
- [Bewegung in UWP-Apps](index.md)
