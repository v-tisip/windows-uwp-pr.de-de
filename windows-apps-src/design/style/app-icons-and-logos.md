---
author: mijacobs
Description: How to create app icons/logos that represent your app in the Start menu, app tiles, the taskbar, the Microsoft Store, and more.
title: App-Symbole und Logos
template: detail.hbs
ms.author: mijacobs
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP
design-contact: Judysa
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: 6c389aa207b0756a222c1c82ea99ea007b451b1e
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5989068"
---
# <a name="app-icons-and-logos"></a>App-Symbole und Logos 

Jede app verfügt über ein Symbol/Logo, das es darstellt, und das Symbol an mehreren Standorten in der Windows-Shell angezeigt: 

:::row:::
    :::column:::
        * Der Titelleiste Ihrer app-Fenster
        * App-Liste im Menü "Start"
        * Die Taskleiste und Task-manager
        * Die app Kacheln
        * Begrüßungsbildschirm der app
        * Im Microsoft Store
    :::column-end:::
    :::column:::
        ![windows 10 start and tiles](images/assetguidance01.jpg)
    :::column-end:::
:::row-end:::

In diesem Artikel werden die Grundlagen der Erstellung von app-Symbole, wie Sie Visual Studio verwaltet werden, und wie diese manuell verwalten müssen Sie verwenden.
 
(In diesem Artikel ist insbesondere für Symbole, die die app selbst darstellen, allgemeine Symbol-Anleitung finden Sie im Artikel [Symbole](icons.md) .)

## <a name="icon-types-locations-and-scale-factors"></a>Symbol Kontotypen, Standorte und Skalierungsfaktoren

Standardmäßig speichert Visual Studio die Symbolressourcen in ein Unterverzeichnis Ressourcen. Hier ist eine Liste der verschiedenen Arten von Symbolen, wo sie angezeigt werden, und wie sie benannt sind. 

| Symbol ein | Erscheint in | Asset-Dateiname |
| ---      | ---        | --- |
| Kleine Kachel | Startmenü |  SmallTile.png  |
| Mittelgroße Kachel |Menü "Start", Microsoft Store Listing\ *  |  Square150x150Logo.PNG |
| Breite Kachel  | Startmenü   | Wide310x150Logo.PNG |
| Große Kachel   | Menü "Start", Microsoft Store Listing\ * |  LargeTile.png  |
| App-Symbol | App-Liste im Menü "Start", Taskleiste, Task-manager | Square44x44Logo.PNG |
| Begrüßungsbildschirm | Begrüßungsbildschirm der app | SplashScreen.png  |
| Signallogo | Die app Kacheln | BadgeLogo.png  |
| Paket-Logo-Speicher-logo | App-Installer, Dev Center die Option "Melden eine app" im Speicher, die Option "Einen Prüfbericht schreiben" im Store | StoreLogo.png  |

\ * Verwendet, es sei denn, Sie für die [Anzeige nur Bilder im Store hochgeladen](/windows/uwp/publish/app-screenshots-and-images#display-only-uploaded-logo-images-in-the-store)auswählen. 

Um sicherzustellen, dass diese Symbole für jeden Bildschirm scharf aussehen, können Sie mehrere Versionen des gleichen Schildsymbols für unterschiedliche Skalierungsfaktoren erstellen. 

Der Skalierungsfaktor bestimmt die Größe des UI-Elemente, z. B. Text. Skalierung von Faktoren reichen von 100 % und 400 %. Mit höheren Werten erstellen größer UI-Elemente, und daher leichter auf hohe DPI-Displays finden Sie unter. 

:::row:::
    :::column:::
        Windows automatically sets the scale factor for each display based on its DPI (dots-per-inch) and the viewing distance of the device. 

        (Users can override the default value by going to the **Settings &gt; Display &gt; Scale and layout** page.)
    :::column-end:::
    :::column:::
        ![](images/icons/display-settings-screen.png)
    :::column-end:::
:::row-end:::  


Da Ressourcen für app-Symbole Bitmaps sind und Bitmaps nicht gut skalieren, es wird empfohlen, einer Version jede Ressource Symbol für jedes Skalierungsfaktor: 100 %, 125 %, 150 %, 200 % und 400 %. Das ist eine Menge von Symbolen! Fortunatly, Visual Studio bietet ein Tool, das zum Erstellen und aktualisieren diese Symbole erleichtert. 

## <a name="microsoft-store-listing-image"></a>Microsoft Store-Eintrag image

"Wie kann ich Bilder für meine app Eintrag im Microsoft Store an?"

Standardmäßig verwenden wir einige der Bilder von Ihren Paketen im Store wie in der Tabelle am Anfang dieser Seite (sowie andere [Bilder, die Sie während der Übermittlung bereitstellen](https://docs.microsoft.com/en-us/windows/uwp/publish/app-screenshots-and-images)) beschrieben. Allerdings haben Sie die Möglichkeit zu verhindern, dass den Store Logo Bilder in den Paketen Ihrer app zu verwenden, wenn Ihr Angebot für Kunden unter Windows 10 (einschließlich Xbox) angezeigt, und muss stattdessen nur Bilder verwenden, die Sie hochladen Store. Dies bietet Ihnen mehr Kontrolle über die Darstellung Ihrer app in verschiedenen anzeigen im Store. (Beachten Sie, dass wenn Ihr Produkt für frühere Betriebssystemversionen unterstützt, die Kunden weiterhin Bilder aus Ihren Paketen angezeigt werden, auch wenn Sie diese Option verwenden.) Dies ist im **Store-Logos** Abschnitt des **Store-Eintrag** Schritts im Übermittlungsprozess möglich.

![Festlegen von Store-Logos während der app-Übermittlungsprozesses](images/app-icons/storelogodisplay.png)

Wenn Sie dieses Kontrollkästchen aktivieren, wird ein neuer Abschnitt namens **Store Bilder anzuzeigen** . Sie können hier hochladen 3 Bildgrößen, die der Store "anstelle von" logobildern aus den Paketen Ihrer app verwenden: 300 x 300, 150 x 150 und 71 x 71 Pixel. Nur die Größe 300 x 300 ist erforderlich, obwohl es wird empfohlen, alle 3 Größen.

Weitere Informationen finden Sie in der [Anzeige nur Bilder im Store Logo hochgeladen](/windows/uwp/publish/app-screenshots-and-images#display-only-uploaded-logo-images-in-the-store).

<!-- ### Fallback images for the Store

The simplest way to control the Store listing image is to specify it during the app submission process. If you don't provide these images during the app submission process, the Store will use a tile image:

1. Large tile
2. Medium tile

If these images aren't provided, the Store will search all matching images of the same image type with a square aspect ratio, preferable with a height greated than the scaled requested height (scaled height is the machine's resolution scale factor * display height). If none of the images meet this criteria, the Store will ignore the scale factor and select an image based on height.  -->

<!-- You can provide screenshots, logos, and other art assets (such as trailers and promotional images to include in your app's Microsoft Store listing. Some of these are required, and some are optional (although some of the optional images are important to include for the best Store display).

The Store may also use your app's tile and other images that you include in your app's package. 

For more information, see [App screenshots, images, and trailers in the Microsoft Store](/windows/uwp/publish/app-screenshots-and-images). -->


## <a name="managing-app-icons-with-the-visual-studio-manifest-designer"></a>Verwalten von app-Symbole mit dem Visual Studio-Manifest-Designer

Visual Studio bietet ein sehr nützliches Tool für die Verwaltung von Ihrer app-Symbole im **Manifest-Designer**aufgerufen. 

> Wenn Sie Visual Studio 2017 noch nicht, sind verschiedene Versionen verfügbar, z. B. eine kostenlose Version (Visual Studio 2017 Community Edition), und die anderen Versionen bieten kostenlose Testversionen. Sie können sie hier herunterladen:[https://developer.microsoft.com/windows/downloads](https://developer.microsoft.com/windows/downloads)


So starten Sie den Manifest-Designer
<!-- 1. Use Visual Studio to open a UWP project.
2. In the **Solution Explorer**, double-click the package.appmanifest file. 

    ![The Visual Studio 2017 Solution Explorer](images/icons/vs-solution-explorer.png)

    Visual Studio displays the manifest designer.

    ![The Visual Studio 2017 manifest designer](images/icons/vs-manfiest-designer.png)
3. Click the **Visual Assets** tab.

    ![The Visual Assets tab](images/icons/vs-manfiest-designer-visual-assets.png) -->


:::row:::
    :::column:::
        1. Verwenden Sie Visual Studio, um ein UWP-Projekt öffnen.
    :::column-end:::
    :::column:::
        
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        2. Doppelklicken Sie im **Projektmappen-Explorer**auf die Datei Package.appmxanifest.
    :::column-end:::
    :::column:::
        ![The Visual Studio 2017 Manifest Designer](images/icons/vs-solution-explorer.png)
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
            Visual Studio displays the Manifest Designer.
    :::column-end:::
    :::column:::
            ![The Visual Assets tab](images/icons/vs-manfiest-designer.png)
    :::column-end:::
:::row-end:::    
:::row:::
    :::column:::
        3. Klicken Sie auf der Registerkarte " **Visuelle Anlagen** ".
    :::column-end:::
    :::column:::
        ![The Visual Assets tab](images/icons/vs-manfiest-designer-visual-assets.png)
    :::column-end:::
:::row-end:::        

## <a name="generating-all-assets-at-once"></a>Alle Objekte auf einmal generieren

Das erste Menüelement in der Registerkarte " **Visuelle Anlagen** ", **Alle visuellen Ressourcen**, ist genau das, was der Name schon sagt: jede visuelle Ressource, die Ihre app mit dem Drücken der Taste a muss generiert.

![Generieren von alle visuellen Ressourcen in Visual Studio](images/app-icons/all-visual-assets.png)

Alles, was Sie tun müssen ist ein einzelnes Bild bereitstellen, und Visual Studio generiert die kleine Kachel, mittelgroßen Kachel, große Kachel, Breite Kachel, große Kachel, app-Symbol, Begrüßungsbildschirm, und Logo Ressourcen für jedes Skalierungsfaktor zu verpacken.

Um alle Ressourcen auf einmal zu generieren:
1. Klicken Sie auf die **** neben dem Feld **Quelle** , und wählen Sie das Bild, das Sie verwenden möchten. Wenn Sie ein Bitmap-Bild verwenden, stellen Sie sicher, dass sie mindestens 400 um 400 Pixel ist, damit Sie scharfe Ergebnisse erhalten. Vektorbasierte Bilder funktionieren am besten; Visual Studio können Sie AI (Adobe Illustrator) und PDF-Dateien verwenden. 
2. (Optional). Konfigurieren Sie im Abschnitt **Anzeigeeinstellungen** folgende Optionen:

    a.  **Kurzname**: Geben Sie einen kurzen Namen für Ihre app.

    b.  **Namen anzeigen**: angeben, ob der Kurzname für Mittel, breit, oder große Kacheln angezeigt werden sollen. 

    c. **Hintergrund-Kachel**: Geben Sie den Hexadezimalwert oder einen Farbnamen für die Hintergrundfarbe der Kachel. Beispiel: `#464646`. Der Standardwert lautet `transparent`.

    d. **Hintergrund: Splash**: Geben Sie die hex-Wert oder Farbe für den Hintergrund des: Splash. 

3. Klicken Sie auf **generieren**. 

Visual Studio generiert Bilddateien und Projekt hinzugefügt. Wenn Sie Ihre Ressourcen ändern möchten, wiederholen Sie einfach den Vorgang. 

Skalierte Symbolressourcen führen Sie diese Datei Namenskonvention:

*Filename*- Scale -*Skalierungsfaktor*PNG

Beispiel:

Square150x150Logo-Scale-100.png, Square150x150Logo-Scale-200.png, Square150x150Logo-Scale-400.png

Beachten Sie, dass ein signallogo standardmäßig von Visual Studio generiert nicht. Ist, dass Ihre signallogo ist eindeutig und wahrscheinlich mit Ihrer app-Symbole sollten nicht übereinstimmen. Weitere Informationen finden Sie unter der [signalbenachrichtigungen für UWP-apps Artikel](/windows/uwp/design/shell/tiles-and-notifications/badges). 


## <a name="more-about-app-icon-assets"></a>Weitere Informationen zu Ressourcen für app-Symbole
Visual Studio generiert alle app Symbolressourcen für das Projekt erforderlich, aber wenn Sie diese anpassen möchten, hilft es um zu verstehen, wie sie sich von anderen app-Ressourcen sind. 

Die app-Symbol-Ressource wird in vielen Stellen angezeigt: der Windows-Taskleiste, der Aufgabenansicht, ALT + TAB und der unteren rechten Ecke von startkacheln. Da die app-Symbol Ressource an vielen Orten angezeigt wird, verfügt über einige zusätzliche größenanpassung und Optionen, die die andere Ressourcen verfügen nicht über plating: "Target-Size" Bestand und "unbeschichtete" Ressourcen. 

### <a name="target-size-app-icon-assets"></a>Zielgröße-app Symbolressourcen
Zusätzlich zu den standardmäßigen Skalierungsfaktor Größen ("Square44x44Logo.scale-400.png") empfehlen wir auch "Target-Size" Ressourcen erstellen. Wir bezeichnen diese Ressourcen Zielgröße, da sie bestimmte Größen, z. B. bestimmte Skalierungsfaktoren, z. B. 400, anstatt 16 Pixel abzielen. Zielgröße-Ressourcen sind für Oberflächen, die Skalierung Plateau System nicht:

* Starten der Sprungliste (Desktop)
* Starten der unteren Ecke der Kachel (Desktop)
* Tastenkombinationen (Desktop)
* Systemsteuerung (Desktop)

Hier ist die Liste der Zielgröße-Ressourcen:


| Ressourcengröße | Dateinamenbeispiel                  |
|------------|------------------------------------|
| 16 x 16\*    | Square44x44Logo.targetsize-16.png  |
| 24 x 24\*    | Square44x44Logo.targetsize-24.png  |
| 32 x 32\*    | Square44x44Logo.targetsize-32.png  |
| 48 x 48\*    | Square44x44Logo.targetsize-48.png  |
| 256 x 256\*  | Square44x44Logo.targetsize-256.png |
| 20 x 20      | Square44x44Logo.targetsize-20.png  |
| 30x30      | Square44x44Logo.targetsize-30.png  |
| 36 x 36      | Square44x44Logo.targetsize-36.png  |
| 40 x 40      | Square44x44Logo.targetsize-40.png  |
| 60 x 60      | Square44x44Logo.targetsize-60.png  |
| 64 x 64      | Square44x44Logo.targetsize-64.png  |
| 72 x 72      | Square44x44Logo.targetsize-72.png  |
| 80 x 80      | Square44x44Logo.targetsize-80.png  |
| 96 x 96      | Square44x44Logo.targetsize-96.png  |

\ * Mindestens, es wird empfohlen, diese Größen. 

Sie müssen für diese Ressourcen keine Abstände hinzufügen, diese werden bei Bedarf von Windows hinzugefügt. Bei diesen Ressourcen sollte eine minimale Fläche von 16Pixeln vorgesehen werden. 

Unten sehen Sie ein Beispiel dafür, wie diese Ressourcen als Symbole in der Windows-Taskleiste angezeigt werden:

![Ressourcen in Windows-Taskleiste](images/assetguidance21.png)

### <a name="unplated-assets"></a>Unbeschichtete Ressourcen
Standardmäßig verwendet Windows eine zielbasierte Ressource neben einer farbigen Rückwand standardmäßig. Wenn Sie möchten, können Sie eine zielbasierte zielbasierte Ressource bereitstellen. "Unbeschichtete" bedeutet, dass die Ressource auf einen transparenten Hintergrund angezeigt wird. Denken Sie daran, die diese Ressourcen über eine Vielzahl von Hintergrundfarben angezeigt wird. 

![Ressourcen mit und ohne Anpassung](images/assetguidance22.png)

Hier sind die Oberflächen, die Symbolressourcen unbeschichtete app verwenden:
* Taskleiste und Miniaturansicht der Taskleiste (Desktop)
* Taskleisten-Sprungliste
* Aufgabenansicht
* ALT + TAB


### <a name="target-and-unplated-sizing"></a>Ziel und zielbasierte anpassen

Hier sind die empfohlenen Größe für zielbasierte Ressourcen bei einer Skalierung von 100 %:

![Zielbasierte Ressourcengröße bei einer Skalierung von 100%](images/assetguidance23.png)


## <a name="more-about-splash-screen-assets"></a>Weitere Informationen zu Ressourcen für den Begrüßungsbildschirm
Weitere Informationen zu Begrüßungsbildschirme finden Sie im [UWP Begrüßungsbildschirm Bildschirme Artikel](/windows/uwp/launch-resume/splash-screens).

## <a name="more-about-badge-logo-assets"></a>Weitere Informationen zur Badge-Logo-Ressourcen

Wenn Sie den Asset-Generator verwenden, um alle Ressourcen zu generieren, Sie müssen, es gibt ein Grund, warum es Signal Logos standardmäßig generiert nicht: sie sind unterscheidet sich von anderen app-Ressourcen. Das signallogo ist ein Status-Bild, das in Benachrichtigungen und auf die app-Kacheln angezeigt wird. 

Weitere Informationen finden Sie unter der [signalbenachrichtigungen für UWP-apps Artikel](/windows/uwp/design/shell/tiles-and-notifications/badges).


## <a name="customizing-asset-padding"></a>Anpassen der Ressource "Padding"

Standardmäßig gilt Asset-Generator von Visual Studio empfohlene "Padding" für alle Bilder. Wenn Ihre Bilder "Padding" bereits enthalten, oder Sie randlose Bilder, die am Ende der Kachel erweitern möchten, können Sie dieses Feature deaktivieren directly das Kontrollkästchen **"Padding" empfohlen anwenden** . 

### <a name="tile-padding-recommendations"></a>Kachel "Padding" Empfehlungen
Wenn Sie Ihre eigene Padding bereitstellen möchten, folgen Sie unsere Empfehlungen für die Kacheln. 

Es gibt 4 kachelgrößen: klein (71 x 71), Mittel (150 x 150), Wide (310 x 150) und große (310 x 310). 

Jede Kachelressource hat die gleiche Größe wie die Kachel, auf der sie sich befindet.

![Randlose Kachel](images/app-icons/tile-assets1.png)

Wenn Sie nicht, dass Ihr Symbol an den Rand der Kachel erweitern möchten, können Sie transparente Pixel in Ihrem Bestand verwenden, um "Padding" zu erstellen. 

![Kachel und Rückwand](images/assetguidance05.png)

Beschränken Sie bei kleinen Kacheln die Breite und Höhe auf 66% der Kachelgröße:

![Verhältnisse bei kleinen Kachelgrößen](images/assetguidance09.png)

Beschränken Sie bei mittelgroßen Kacheln die Symbolbreite auf 66% und die Höhe auf 50% der Kachelgröße. Dadurch wird verhindert, dass Elemente in der Brandingleiste überlappen:

![Verhältnisse bei mittelgroßen Kacheln](images/assetguidance10.png)

Beschränken Sie bei breiten Kacheln die Symbolbreite auf 66% und die Höhe auf 50% der Kachelgröße. Dadurch wird verhindert, dass Elemente in der Brandingleiste überlappen:

![Verhältnisse bei breiten Kacheln](images/assetguidance11.png)

Beschränken Sie bei großen Kacheln die Symbolbreite auf 66% und die Höhe auf 50% der Kachelgröße:

![Verhältnisse bei großen Kacheln](images/assetguidance12.png)

Einige Symbole sind so konzipiert, dass sie horizontal oder vertikal ausgerichtet sind, andere Symbole hingegen weisen komplexere Formen auf, wodurch verhindert wird, dass sie direkt in die Zielabmessungen passen. Symbole, die zentriert erscheinen, können auf eine Seite geneigt sein. In diesem Fall können Teile eines Symbols aus der empfohlenen Fläche heraushängen, vorausgesetzt, das Symbol belegt dasselbe visuelle Gewicht wie ein genau passendes Symbol:

![Drei zentrierte Symbole](images/assetguidance13.png)

Berücksichtigen Sie bei randlosen Ressourcen Elemente, die innerhalb der Ränder und Kanten der Kacheln interagieren. Behalten Sie Ränder von mindestens 16 % der Höhe oder Breite der Kachel bei. Dieser Prozentsatz stellt die doppelte Breite der Ränder bei den kleinsten Kachelgrößen dar:

![Randlose Kachel mit Rändern](images/assetguidance14.png)

In diesem Beispiel sind die Ränder zu eng:

![Randlose Kachel mit zu engen Rändern](images/assetguidance15.png)









