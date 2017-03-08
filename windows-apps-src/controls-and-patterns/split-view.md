---
author: Jwmsft
title: Geteilte Darstellung
ms.assetid: E9E4537F-1160-4183-9A83-26602FCFDC9A
description: "Ein Steuerelement für die geteilte Ansicht verfügt über einen erweiterbaren/reduzierbaren Bereich und einen Inhaltsbereich."
label: Split view
template: detail.hbs
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: b4f0c84c4fdf273e7ddf2c16e3323ad0c4e52359
ms.lasthandoff: 02/07/2017

---
# <a name="split-view-control"></a>Steuerelement für geteilte Ansicht

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

Ein Steuerelement für die geteilte Ansicht verfügt über einen erweiterbaren/reduzierbaren Bereich und einen Inhaltsbereich.

<div class="important-apis" >
<b>Wichtige APIs</b><br/>
<ul>
<li>[**SplitView-Klasse**](https://msdn.microsoft.com/library/windows/apps/dn864360)</li>
</ul>
</div>

Dies ist ein Beispiel für die Verwendung von SplitView durch die Microsoft Edge-App, um den Hub anzuzeigen.

![Beispiel für die geteilte Ansicht in Microsoft Edge](images/split_view_Edge.png)


 Der Inhaltsbereich einer geteilten Ansicht wird stets angezeigt. Der Bereich kann erweitert und reduziert werden oder geöffnet bleiben. Er kann vom linken oder rechten Rand eines App-Fensters aus eingeblendet werden. Der Bereich verfügt über vier Modi:

-   **Überlagerung**

    Der Bereich ist ausgeblendet, bis er geöffnet wird. Ist der Bereich geöffnet, überlagert er den Inhaltsbereich.

-   **Inline**

    Der Bereich ist immer sichtbar und überlagert den Inhaltsbereich nicht. Der Bereich und der Inhaltsbereich teilen sich die verfügbare Bildschirmfläche.

-   **CompactOverlay**

    Ein kleiner Teil des Bereich – gerade breit genug für die Anzeige von Symbolen – ist in diesem Modus immer sichtbar. Die Standardbreite für den geschlossen Bereich ist 48px und kann mit `CompactPaneLength` geändert werden. Wenn das Fenster geöffnet ist, wird den Inhaltsbereich überlagert werden.

-   **CompactInline**

    Ein kleiner Teil des Bereich – gerade breit genug für die Anzeige von Symbolen – ist in diesem Modus immer sichtbar. Die Standardbreite für den geschlossen Bereich ist 48px und kann mit `CompactPaneLength` geändert werden. Wenn das Fenster geöffnet ist, reduziert es den Platz für Inhalte, die weggeschoben werden.

## <a name="is-this-the-right-control"></a>Ist dies das richtige Steuerelement?

Das Steuerelement für die geteilte Darstellung kann zum Erstellen eines [Navigationsbereichs](nav-pane.md) verwendet werden. Zum Erstellen dieses Musters fügen Sie eine Schaltfläche zum Erweitern/Reduzieren (die „Hamburger“-Schaltfläche) sowie eine Listenansicht mit den Navigationselementen hinzu.

Das Steuerelement für die geteilte Ansicht kann auch für eine Drawer-Ansicht verwendet werden, in der Benutzer den ergänzenden Bereich öffnen und schließen können.

## <a name="create-a-split-view"></a>Erstellen einer geteilten Ansicht

Dies ist ein SplitView-Steuerelement mit einem offenen Bereich, der inline neben dem Inhaltsbereich angezeigt wird.
```xaml
<SplitView IsPaneOpen="True"
           DisplayMode="Inline"
           OpenPaneLength="296">
    <SplitView.Pane>
        <TextBlock Text="Pane"
                   FontSize="24"
                   VerticalAlignment="Center"
                   HorizontalAlignment="Center"/>
    </SplitView.Pane>

    <Grid>
        <TextBlock Text="Content"
                   FontSize="24"
                   VerticalAlignment="Center"
                   HorizontalAlignment="Center"/>
    </Grid>
</SplitView>
```



## <a name="related-topics"></a>Verwandte Themen
* [Navigationsbereichsmuster](nav-pane.md)
* [Listenansicht](lists.md)
 

 

