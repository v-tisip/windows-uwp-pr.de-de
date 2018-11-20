---
author: jnHs
Description: You can select the screenshots, logos, and other art assets (such as trailers and promotional images) to include in your app's Store listing.
title: App-Screenshots, -Bilder und -Trailer
ms.assetid: D216DD2B-F43D-4D26-82EE-0CD34DB929D8
ms.author: wdg-dev-content
ms.date: 10/31/2018
ms.topic: article
keywords: Windows10, UWP, Trailer, Video, Screenshot, Bild, Symbol, Store-Eintrag, Store-Eintragsbilder
ms.localizationpriority: medium
ms.openlocfilehash: 4899e117096cf6d03c497fec79038e6d96aca3fd
ms.sourcegitcommit: ed0304b8a214c03b8aab74b8ef12c9f82b8e3c5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2018
ms.locfileid: "7305558"
---
# <a name="app-screenshots-images-and-trailers"></a>App-Screenshots, -Bilder und -Trailer

Durch aussagekräftige Bilder kann die Aufmerksamkeit potentieller Kunden im Store auf Ihre App gelenkt werden.

Sie können die [Bildschirmfotos](#screenshots), [Logos](#store-logos), [Trailer](#trailers)und andere Grafikobjekte im Store-Eintrag Ihrer app enthalten sein bereitstellen. Einige dieser Elemente sind erforderlich, während andere optional sind, (auch wenn einige der optionalen Bilder wichtig für die beste Anzeige im Store sind).

Während der [App-Übermittlung](app-submissions.md) geben Sie diese Grafikobjekte im Schritt [Store-Einträge](create-app-store-listings.md) an. Beachten Sie, dass es vom Betriebssystem des Kunden und weiteren Faktoren abhängt, wie Bilder im Store angezeigt werden.

Im Store können auch dem Symbol Ihrer app und andere Bilder, die Sie in Ihrer app-Paket einschließen. Führen Sie das [Zertifizierungskit für Windows-Apps](../debug-test-perf/windows-app-certification-kit.md) aus, um zu ermitteln, ob erforderliche Bilder fehlen, bevor Sie Ihre App übermitteln. Richtlinien und Empfehlungen zu diesen Bildern finden Sie in [App-Symbole und Logos](../design/style/app-icons-and-logos.md).

## <a name="screenshots"></a>Screenshots

Screenshots sind die Bilder Ihrer App, die Ihren Kunden im Store-Eintrag der App angezeigt werden.

Sie haben die Möglichkeit zum Bereitstellen von Bildschirmfotos für andere Gerätefamilien, die Ihre App unterstützt, damit die entsprechenden Bildschirmfotos angezeigt werden, wenn ein Kunde den Store-Eintrag Ihrer App auf diesem Gerätetyp anzeigt. 

Für die Übermittlung ist nur ein Screenshot (für jede Gerätefamilie) erforderlich. Sie können jedoch bis zu neun Desktop-Screenshots und bis zu acht Screenshots für die anderen Gerätefamilien bereitstellen. Wir empfehlen, mindestens 4 Screenshots für jede Gerätefamilie hinzuzufügen, die von Ihrer App unterstützt werden, damit Benutzer sehen, wie die App auf ihrem Gerätetyp aussieht. (Verwenden Sie keine Screenshots für Gerätefamilien, die Ihre App nicht unterstützt.) Beachten Sie, dass **Desktop**-Screenshots auch für Kunden auf Surface Hub-Geräten angezeigt werden.

> [!NOTE]
> Microsoft Visual Studio enthält ein [Tool zum Erstellen von Screenshots](https://docs.microsoft.com/visualstudio/debugger/run-windows-store-apps-in-the-simulator#BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store).

Jeder Screenshot muss einer PNG-Datei im Quer- oder Hochformat entsprechen, und die Datei darf nicht größer als 50 MB sein.

Die Größenanforderungen hängen von der Gerätefamilie ab:
- Desktopgerät: 1366x768 Pixel oder größer. Unterstützt 4K-Bilder (3840x2160). (Wird ebenfalls den Kunden auf Surface Hub-Geräten angezeigt.)
- Mobilgeräte: Bilder müssen folgende Größe haben: 1080x1920, 1920x1080, 768x1280, 1280x768, 720x1280 und 1280x720, 800x480 oder 480x800 Pixel.
- Xbox: 3480 x 2160 Pixel oder kleiner. Unterstützt 4K-Bilder (3840x2160).
- Geräte für Hologramme: 1268x720 Pixel oder größer. Unterstützt 4K-Bilder (3840x2160).

Beachten Sie für die optimale Anzeige die folgenden Richtlinien beim Erstellen Ihrer Bildschirmfotos:
- Platzieren Sie wichtige visuelle Elemente und Text in den oberen drei Vierteln des Bilds. Textüberlagerungen können im unteren Viertel angezeigt werden. 
- Fügen Sie Ihren Screenshots keine zusätzlichen Logos, Symbole oder Marketingnachrichten hinzu.
- Verwenden Sie nicht sehr helle oder dunkle Farben oder Streifen mit starkem Kontrast, die die Lesbarkeit von Textüberlagerungen beeinträchtigen können.

Sie können auch eine Kurzbeschreibung von maximal 200Zeichen für die einzelnen Screenshots angeben.

> [!TIP]
> Bildschirmfotos werden in Ihrem Eintrag der Reihenfolge nach angezeigt. Nachdem Sie Ihre Bildschirmfotos hochgeladen haben, können Sie sie ziehen und ablegen, um sie neu anzuordnen. 

Hinweis: Wenn Sie Store-Einträge für [mehrere Sprachen](supported-languages.md) erstellen, erhalten Sie für jede Sprache eine Seite vom Typ **Store-Eintrag**. Sie müssen Bilder für jede Sprache separat hochladen (auch wenn Sie dieselben Bilder verwenden), einschließlich Beschriftungen, die für die einzelnen Sprachen verwendet werden. (Wenn Sie Store-Einträge in vielen Sprachen verfügen, können Sie diese aktualisieren, indem [Daten des Eintrags exportieren und offline-](import-and-export-store-listings.md)einfacher.)


## <a name="store-logos"></a>Store-Logos

Sie können Store-Logos hochladen, um eine angepasstere Darstellung im Store zu erstellen. Es wird empfohlen, dass Sie diese Bilder für eine optimale Anzeige im Store-Eintrag für alle Geräte und Betriebssystemversionen bereitstellen, die Ihre App unterstützt. Wenn Ihre App für Kunden auf Xbox verfügbar ist, sind einige dieser Bilder erforderlich.

Sie können diese Bilder als PNG-Dateien (maximal 50MB) in drei Größen bereitstellen, die jeweils den folgenden Richtlinien entsprechen sollten.

### <a name="916-poster-art-720-x-1080-or-1440-x-2160-pixels"></a>9:16 – Plakate (720x1080 oder 1440x2160 Pixel)

Diese Größe wird als Logo in Store-Einträgen für Kunden unter Windows10 und auf Xbox-Geräten verwendet, daher wird **dringend empfohlen**, dieses Bild für die ordnungsgemäße Anzeige bereitzustellen. Ihr Angebot sieht möglicherweise nicht gut, wenn Sie nicht werden eingeschlossen, und nicht mit anderen angeboten, die Kunden beim Browsen im Store angezeigt werden. Dieses Bild kann ebenfalls in den Suchergebnissen oder in speziell zusammengestellten Sammlungen verwendet werden.

Dieses Bild sollte den Namen Ihrer App enthalten, und Text auf dem Bild sollte die Lesbarkeitsanforderungen (Kontrastverhältnis von 4,5:1) erfüllen. Beachten Sie, dass auf dem unteren Viertel des Bilds Textüberlagerungen angezeigt werden. Stellen Sie sicher, dass Sie dort keinen Text oder das Hauptbild einfügen.

> [!NOTE]
> Wenn Ihre App für Kunden auf Xbox verfügbar ist, ist dieses Bild **erforderlich** und muss den Produkttitel enthalten. Der Titel muss im oberen Dreiviertel des Bilds angezeigt werden, da Textüberlagerungen auf den unteren Viertel des Bilds angezeigt werden.

### <a name="11-box-art-1080-x-1080-or-2160-x-2160-pixels"></a>1:1 – Verpackungsillustration (1080 x 1080 or 2160 x 2160 Pixel)

Dieses Bild kann auf verschiedenen Store-Seiten für Windows10 angezeigt werden (einschließlich Xbox), und wenn Sie keine **9:16 Illustrationen** angeben, wird dieses als zentrales Logo verwendet. Dieses Bild muss auch den Namen Ihrer App enthalten. Beachten Sie, dass auf dem unteren Viertel des Bilds Textüberlagerungen angezeigt werden und fügen Sie dort keinen Text oder das Hauptbild ein. Stellen Sie sicher, dass Sie den Namen Ihrer App im Bild einfügen. 

> [!NOTE]
> Wenn Ihre App für Kunden auf Xbox verfügbar ist, ist dieses Bild **erforderlich** und muss den Produkttitel enthalten. Der Titel muss im oberen Dreiviertel des Bilds angezeigt werden, da Textüberlagerungen auf den unteren Viertel des Bilds angezeigt werden.

### <a name="11-app-tile-icon-300-x-300-pixels"></a>1:1 Symbol für App-Kachel (300 x 300 Pixel)

Dieses Bild ist für die ordnungsgemäße Anzeige auf Windows Phone8.1 und früheren Versionen erforderlich. Wenn Ihre app zuvor veröffentlichten Windows Phone 8.1 oder frühere Versionen unterstützt, und Sie dieses Bild nicht bereitstellen, sehen Kunden für den Eintrag Ihrer app ein leeres Symbol. (Dies gilt auch für Kunden unter Windows 10 hat Ihre app nur Pakete für Windows Phone 8.1 oder früher.)

Wenn Ihre Übermittlung *nur* UWP-Pakete enthält, müssen Sie dieses Bild bereitstellen (es sei denn, Sie das Kontrollkästchen **für Kunden unter Windows 10 und Xbox anzeigen uploaded Logo Images INSTEAD die Bilder aus meiner Paketen**überprüfen gemäß den nächsten Abschnitt).

### <a name="display-only-uploaded-logo-images-in-the-store"></a>Anzeige nur hochgeladen Logo Bilder im Store.

Sie haben die Möglichkeit zum verhindern, dass des Stores die Logobilder in den Paketen Ihrer app, wenn Ihr Angebot für Kunden unter Windows 10 (einschließlich Xbox) angezeigt, und stattdessen der Store muss nur Bilder verwenden, die Sie hochladen. Dies bietet Ihnen mehr Kontrolle über die Darstellung Ihrer App in verschiedenen Anzeigen im Store für Kunden auf Windows 10 (einschließlich Xbox). (Wenn Ihre app zuvor veröffentlichten frühere Betriebssystemversionen unterstützt, können diese Kunden weiterhin Bilder aus Ihrer Pakete angezeigt.)

In der Store verwendet nur die Bilder, die Sie hochladen, (für Kunden unter Windows 10, einschließlich Xbox), und keine Bilder von Ihren Paketen verwenden, aktivieren Sie das Kontrollkästchen mit der Bezeichnung **für Kunden unter Windows 10 und Xbox muss, zeigen Sie hochgeladen Logo Images INSTEAD die Bilder aus meiner Paketen **.

Wenn Sie dieses Kontrollkästchen aktivieren, wird ein neuer Abschnitt namens **Store Bilder anzuzeigen** . Hier können Sie 3 Bilder, u. a. die **1:1-app-Kachel Symbol (300 x 300 Pixel)** (Wenn Sie das Kontrollkästchen, das Feld zum Bereitstellen, dass das Bild in diesem Abschnitt verschoben) hochladen. Es wird empfohlen, alle drei Bildgrößen bereitzustellen, wenn Sie diese Option verwenden: 300 x 300, 150 x 150 und 71 x 71 Pixel. Es ist jedoch nur die Größe 300 x 300 erforderlich.


<span id="promotional-images" />

## <a name="trailers-and-additional-assets"></a>Trailer und weitere Ressourcen

In diesem Abschnitt können Sie Grafiken bereitstellen, damit Sie Ihr Produkt im Store effektiver präsentieren können. Wir empfehlen die Bereitstellung dieser Bilder, um einen einladenden Store-Eintrag zu erstellen.

> [!TIP]
> Das Bild [16:9 besonderes Favoritenbild](#windows-10-and-xbox-image-169-super-hero-art) wird vor allem empfohlen, wenn Sie beabsichtigen [Videotrailer](#trailers) in Ihrem Store-Eintrag; Wenn Sie es nicht einfügen, nicht Ihre Trailer am Anfang Ihrer Eintrag angezeigt.


### <a name="trailers"></a>Trailer

Trailer sind kurzen Videos, die Kunden die Anzeige Ihres Produkts in Aktion ermöglichen, damit sie seine Funktionen besser nachvollziehen können. Sie werden am oberen Rand der Store-Eintrag Ihrer app (solange Sie ein [16:9 besonderes Favoritenbild](#windows-10-and-xbox-image-169-super-hero-art) Image enthalten) angezeigt. 

Trailer sind mit [Smooth Streaming](http://www.iis.net/downloads/microsoft/smooth-streaming) codiert. Dabei wird die Qualität eines für Kunden angezeigten Videostreams in Echtzeit basierend auf der verfügbaren Bandbreite und CPU-Ressourcen angepasst.

> [!NOTE]
> Trailer werden nur für Kunden unter Windows10, Version 1607 oder höher (einschließlich Xbox), angezeigt.

### <a name="upload-trailers"></a>Trailer hochladen

Sie können bis zu 15 Trailer zu Ihrem Store-Eintrag hinzufügen. Achten Sie darauf, dass sie alle unten aufgeführten [Anforderungen](#trailer-requirements) erfüllen.

Sie müssen eine Videodatei (MP4 oder MOV), eine Miniaturansicht und einen Titel für jeden bereitgestellten Trailer hochladen.

> [!IMPORTANT]
> Wenn Sie Trailer verwenden zu können, müssen Sie auch einen Abschnitt [16:9 besonderes Favoritenbild](#windows-10-and-xbox-image-169-super-hero-art) Image, damit Ihre Trailer am Anfang der Store-Eintrag angezeigt werden bereitstellen. Dieses Bild wird angezeigt, wenn Ihre Trailer beendet sind.

Befolgen Sie folgende Empfehlungen, damit Ihre Trailer effektiv sind:
- Trailer sollten eine gute Qualität und eine minimale Länge aufweisen (60 Sekunden oder weniger als 2GB wird empfohlen). 
- Verwenden Sie eine andere Miniaturansicht für jeden Trailer, sodass Kunden wissen, dass sie eindeutig sind.
- Da bei einigen Store-Layouts der obere und untere Rand der Trailer leicht abgeschnitten sein kann, stellen Sie sicher, dass wichtige Informationen in der Mitte des Bildschirms angezeigt werden.
- Bildfrequenz und Auflösung sollten dem Quellmaterial entsprechen. Beispielsweise sollten mit 720p60 aufgenommene Inhalte codiert und mit 720p60 hochgeladen werden. 

Sie müssen auch die unten genannten Anforderungen erfüllen.

**So fügen Sie Trailer zu Ihrem Eintrag hinzu:**
1. Laden Sie die **Videodatei** Ihres Trailers im angegebenen Feld hoch. Ein Dropdownfeld wird auch angezeigt für den Fall, dass Sie einen Trailer wiederverwenden möchten, den Sie bereits hochgeladen haben (z.B. für einen Store-Eintrag in einer anderen Sprache).
2. Nachdem Sie den Trailer hochgeladen haben, müssen Sie ein **Miniaturbild** dafür hochladen. Dies muss eine PNG-Datei mit 1920 x 1080 Pixeln sein. In der Regel handelt es sich um ein Standbild aus dem Trailer.
3. Klicken Sie auf das Stiftsymbol, um einen **Titel** für Ihren Trailer hinzuzufügen (maximal 255Zeichen).
4. Wenn Sie weitere Trailer zum Eintrag hinzufügen möchten, klicken Sie auf **Add trailer**, und wiederholen Sie die oben aufgeführten Schritte.

> [!TIP]
> Wenn Sie Store-Einträge in mehreren Sprachen erstellt haben, können Sie **Aus vorhandenem Trailer auswählen** auswählen, um den Trailer wiederzuverwenden, den Sie bereits hochgeladen haben. Sie müssen diese nicht einzeln für jede Sprache hochladen.

Um einen Trailer aus einem Eintrag zu entfernen, klicken Sie auf das **X** neben dem Dateinamen. Sie können auswählen, ob Sie es aus nur den aktuellen Store-Eintrag entfernen, in dem Sie arbeiten, oder es aus allen Store-Einträge für Ihr Produkt (in jeder Sprache) zu entfernen.


### <a name="trailer-requirements"></a>Traileranforderungen

Wenn Sie Ihre Trailer bereitstellen, müssen Sie die folgenden Anforderungen erfüllen:

- Das Videoformat muss MOV oder MP4 sein. 
- Die Videodauer sollte nicht 60Sekunden überschreiten.
- Die Dateigröße des Trailers sollte 2GB nicht überschreiten. 
- Die Videoauflösung muss 1920 x 1080 Pixel oder 3840 x 2160 Pixel sein.
- Die Miniaturansicht muss eine PNG-Datei mit einer Auflösung von entweder 1920 x 1080 Pixeln oder 3840 x 2160 Pixeln sein.
- Der Titel darf 255Zeichen nicht überschreiten. 
- Schließen Sie keine Altersfreigaben in Ihrem Trailer ein.

Wie die anderen Felder auf der Seite des Store-Eintrags müssen Trailer die Zertifizierung bestehen, bevor Sie sie im Microsoft Store veröffentlichen können. Achten Sie darauf, dass Ihre Trailer die [Microsoft Store-Richtlinien](https://docs.microsoft.com/legal/windows/agreements/store-policies) einhalten.

Es gibt weitere Anforderungen je nach Typ der Datei.

#### <a name="mov"></a>MOV

<table>
<tr>
<td>

**Video:**

<ul>
<li>1080p ProRes (bei Bedarf HQ)</li>
<li>Native Bildfrequenz; 29,97 BpS bevorzugt</li>
</ul>
</td>
<td>

**Audio:**

<ul>
<li>Stereo erforderlich</li>
<li>Empfohlener Audiopegel: -16 LKFS/LUFS</li>
</ul> 
</td>
</tr>
</table>

#### <a name="mp4"></a>MP4

<table>
<tr>
<td>

**Video:**

<ul>
<li>Codec: H.264</li>
<li>Progressiver Scan (kein Interlacing)</li>
<li>High Profile</li>
<li>2 aufeinanderfolgende B-Frames</li>
<li>Geschlossene GOP. GOP der Hälfte der Bildfrequenz</li>
<li>CABAC</li>
<li>50 MB/s </li>
<li>Farbraum: 4.2.0</li>
</ul>
</td>
<td>

**Audio:**

<ul>
<li>Codec: AAC-LC</li>
<li>Kanäle: Stereo oder Surround-Sound</li>
<li>Samplingrate: 48KHz</li>
<li>Audiobitrate: 384 KB/s für Stereo, 512 KB/s für Surround-Sound</li>
</ul>
</td>
</tr>
</table>

Für H.264-Mezzanine-Dateien wird Folgendes empfohlen:
- Container: MP4
- Keine Bearbeitungslisten (oder AV-Synchronisierung geht womöglich verloren)
- moov atom am Anfang der Datei (schneller Start)

### <a name="windows-10-and-xbox-image-169-super-hero-art"></a>Windows10 und Xbox-Bild (16:9 Besonderes Favoritenbild)

Unter **Windows 10 und Xbox-Bild** wird das Bild **16:9 besonderes Favoritenbild (1920 x 1080 oder 3840 x 2160 Pixel)** in verschiedenen Layouts im Microsoft Store auf allen Windows 10-Gerätetypen (einschließlich Xbox) verwendet. Es wird empfohlen, dieses Image bereitzustellen, unabhängig davon, auf welche Betriebssystemversionen oder Gerättypen die App ausgerichtet ist.

Dieses Bild ist *erforderlich* für die ordnungsgemäße Anzeige, wenn Ihr Eintrag [Videotrailer](#trailers) enthält. Für Kunden mit Windows10, Version 1607 oder höher (einschließlich Xbox), wird es als Hauptbild auf Ihrem Store-Eintrag verwendet (oder es wird angezeigt, nachdem alle Trailer beendet sind). Es kann auch verwendet werden, um Ihre App in Werbelayouts im Store zu präsentieren. Beachten Sie, dass dieses Bild weder den Produkttitel noch anderen Text enthalten darf.

Im Folgenden finden Sie einige Tipps, die Sie beim Entwerfen Ihres Bilds beachten sollten:

- Das Bild muss eine PNG-Datei mit 1920 x 1080 Pixel oder 3840 x 2160 Pixel sein.
- Wählen Sie ein dynamisches Bild aus, das mit der App zusammenhängt, um den Wiedererkennungswert sowie die Differenzierung zu fördern. Vermeiden Sie Stockfotografien oder generische visuelle Elemente.
- Fügen Sie keinen Text in das Bild ein.
- Platzieren Sie keine wichtigen visuellen Elemente in das untere Drittel des Bilds (da in einigen Layouts ein Farbverlauf über diesen Bereich angewendet wird).
- Platzieren Sie die wichtigsten Details in die Mitte des Bilds (da in einigen Layouts das Bild zugeschnitten wird).
- Minimieren Sie den leeren Bereich.
- Vermeiden Sie das Anzeigen der Benutzeroberfläche Ihrer App, und verwenden Sie keine Bilder für bestimmte Geräte.
- Vermeiden Sie politische und nationale Designs, Flaggen oder religiöse Symbole.
- Fügen Sie keine Bilder von taktlosen Gesten, Nacktheit, Glücksspiel, Währung, Drogen, Tabakprodukte oder Alkohol hinzu.
- Verwenden Sie keine Bilder mit Waffen, die auf den Benutzer gerichtet sind, oder übermäßige Gewalt und Blut.

Durch das Bereitstellen des Bilds können wir es für Vermarktungsmöglichkeiten in Betracht ziehen. Dies garantiert nicht, dass die App präsentiert wird. Weitere Informationen finden Sie unter [Einfaches Bewerben Ihrer App](make-your-app-easier-to-promote.md).


### <a name="xbox-images"></a>Xbox-Bilder

Diese Bilder werden für die ordnungsgemäße Anzeige empfohlen, wenn Sie Ihre App auf Xbox veröffentlichen. 

Es gibt 3 verschiedene Größen, die Sie hochladen können:
- **Grafik mit Branding, 584 x 800 Pixel**: Muss den Titel des Produkts enthalten. Für dieses Image ist eine Brandlingleiste erforderlich. Der Titel und alle Hauptbilder müssen im oberen Dreiviertel des Bilds angezeigt werden, da die Textüberlagerung auf dem unteren Viertel angezeigt werden.
- **Favoritenbild mit Titel, 1920 x 1080 Pixel**: Muss den Titel des Produkts enthalten. Der Titel und alle Hauptbilder müssen im oberen Dreiviertel des Bilds angezeigt werden, da die Textüberlagerung auf dem unteren Viertel angezeigt werden.
- **Ausgewähltes quadratisches Werbebild, 1080 x 1080 Pixel**: Muss *nicht* den Produkttitel enthalten.

> [!NOTE]
> Sie müssen ebenfalls für die besten Anzeige auf Xbox ein **9:16 (720 x 1080 oder 1440 x 2160 Pixel)** Bild im Abschnitt [Store-Logos](#store-logos) angeben.


### <a name="holographic-image"></a>Hologrammbild

Die Bildgröße **2:1 (2400 x 1200)** wird nur verwendet, wenn Ihre App die Hologramm-Gerätefamilie unterstützt. Wenn dies der Fall ist, wird empfohlen, dieses Bild zu verwenden.


<span id="optional-promotional-images" />

### <a name="images-only-for-windows-8x-andor-windows-phone-8x"></a>Bilder für Windows8.x bzw. Windows Phone8.x 

Wenn Ihre app zuvor übermittelt frühere Betriebssystemversionen unterstützt (Windows 8.x und/oder Windows Phone 8.x), müssen diese Bilder bereitgestellt werden, in der Reihenfolge für uns, damit Ihre app in werbelayouts (Dies garantiert nicht, dass die app präsentiert wird). Wenn Ihre app diese älteren Betriebssystemversionen nicht unterstützt, überspringen Sie diesen Abschnitt. (Dieser Abschnitt hieß früher **Optionale Werbebilder**.)

**Für Windows Phone8.1 und frühere Versionen** können zwei Bildgrößen in Werbelayouts verwendet werden: **1000 x 800 Pixel (5:4)** und **358 x 358 Pixel (1:1)**. Wenn Ihre app unter Windows Phone 8.1 oder früheren Versionen ausgeführt wird, empfehlen wir die Bereitstellung von Bildern in diesen beiden Größen.  

> [!TIP]
> Stellen Sie ein 300 x 300 großes App-Kachelsymbol im Abschnitt [Store-Logos](#store-logos) für alle Übermittlungen bereit, die Windows Phone 8.1 oder früher unterstützen. Dadurch wird sichergestellt, dass Ihre App im Store nicht mit einem leeren Symbol angezeigt wird.  

**Für Windows 8.1 und frühere Versionen** verwenden manche Werbelayouts unter Umständen ein Bild der Größe **414 x 180** Pixel. Wenn Ihre app unter Windows 8.1 oder früheren Versionen ausgeführt wird, wird empfohlen, ein Bild in diesem Sizen bereitstellen.




