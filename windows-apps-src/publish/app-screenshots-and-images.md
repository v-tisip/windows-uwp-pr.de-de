---
author: jnHs
Description: "Sie können die Bildschirmfotos, Logos und andere Grafikobjekte (z.B. Trailer und Werbebilder) auswählen, die im Store-Eintrag Ihrer App enthalten sein sollen."
title: App-Screenshots, -Bilder und -Trailer
ms.assetid: D216DD2B-F43D-4D26-82EE-0CD34DB929D8
ms.author: wdg-dev-content
ms.date: 08/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 7d5da868a93f958a9432e7f8360129a8be8ca486
ms.sourcegitcommit: 6c6f3c265498d7651fcc4081c04c41fafcbaa5e7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2017
---
# <a name="app-screenshots-images-and-trailers"></a>App-Screenshots, -Bilder und -Trailer

Durch aussagekräftige Bilder kann die Aufmerksamkeit potentieller Kunden im Store auf Ihre App gelenkt werden.

Sie können [Bildschirmfotos](#screenshots), [Logos](#store-logos) und andere Grafikobjekte (z.B. [Trailer](#trailers) und [Werbebilder](##additional-art-assets)) auswählen, die im Store-Eintrag Ihrer App enthalten sein sollen. Einige dieser Elemente sind erforderlich, während andere optional sind, (auch wenn einige der optionalen Bilder wichtig für die beste Anzeige im Store sind). 

Während der [App-Übermittlung](app-submissions.md) geben Sie diese Grafikobjekte im Schritt [Store-Einträge](create-app-store-listings.md) an. Beachten Sie, dass es vom Betriebssystem des Kunden und weiteren Faktoren abhängt, wie Bilder im Store angezeigt werden.

Der Store verwendet außerdem unter Umständen Ihre App-Kachel und andere Bilder, die Sie in Ihr App-Paket einschließen. Führen Sie das [Zertifizierungskit für Windows-Apps](../debug-test-perf/windows-app-certification-kit.md) aus, um zu ermitteln, ob erforderliche Bilder fehlen, bevor Sie Ihre App übermitteln. Anleitungen und Empfehlungen zu diesen Bildern finden Sie unter [Ressourcen für Kacheln und Symbole](../controls-and-patterns/tiles-and-notifications-app-assets.md).

## <a name="screenshots"></a>Screenshots

Screenshots sind die Bilder Ihrer App, die Ihren Kunden im Store-Eintrag der App angezeigt werden.

Sie haben die Möglichkeit zum Bereitstellen von Bildschirmfotos für andere Gerätefamilien, damit die entsprechenden Bildschirmfotos angezeigt werden, wenn ein Kunde den Store-Eintrag Ihrer App auf diesem Gerätetyp anzeigt. 

Für die Übermittlung ist nur ein Screenshot (für jede Gerätefamilie) erforderlich. Sie können jedoch bis zu neun Desktop-Screenshots und bis zu acht Screenshots für die anderen Gerätefamilien bereitstellen. Wir empfehlen, mindestens 4 Screenshots für jede Gerätefamilie hinzuzufügen, die von Ihrer App unterstützt werden, damit Benutzer sehen, wie die App auf ihrem Gerätetyp aussieht.

> [!NOTE]
> Microsoft Visual Studio enthält ein [Tool zum Erstellen von Screenshots](https://docs.microsoft.com/visualstudio/debugger/run-windows-store-apps-in-the-simulator#BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store).

Jeder Screenshot muss einer PNG-Datei im Quer- oder Hochformat entsprechen, und die Datei darf nicht größer als 5 MB sein.

Die Größenanforderungen hängen von der Gerätefamilie ab:
- Mobile Geräte: 768x1280, 720x1280 oder 480x800 Pixel
- Desktopgerät: 1366x768 Pixel oder größer
- Geräte für Hologramme: 1268x720 Pixel oder größer
- Xbox: 3480 x 2160 Pixel oder kleiner

Beachten Sie für die optimale Anzeige die folgenden Richtlinien beim Erstellen Ihrer Bildschirmfotos:
- Platzieren Sie wichtige visuelle Elemente und Text in den oberen drei Vierteln des Bilds. Textüberlagerungen können im unteren Viertel angezeigt werden. 
- Fügen Sie Ihren Screenshots keine zusätzlichen Logos, Symbole oder Marketingnachrichten hinzu.
- Verwenden Sie nicht sehr helle oder dunkle Farben oder Streifen mit starkem Kontrast, die die Lesbarkeit von Textüberlagerungen beeinträchtigen können.

Sie können auch eine Kurzbeschreibung von maximal 200Zeichen für die einzelnen Screenshots angeben.

> [!TIP]
> Bildschirmfotos werden in Ihrem Eintrag der Reihenfolge nach angezeigt. Nachdem Sie Ihre Bildschirmfotos hochgeladen haben, können Sie sie ziehen und ablegen, um sie neu anzuordnen. 

Hinweis: Wenn Sie Store-Einträge für [mehrere Sprachen](supported-languages.md) erstellen, erhalten Sie für jede Sprache eine Seite vom Typ **Store-Eintrag**. Sie müssen Bilder für jede Sprache separat hochladen (auch wenn Sie dieselben Bilder verwenden), einschließlich Beschriftungen, die für die einzelnen Sprachen verwendet werden.


## <a name="store-logos"></a>Store-Logos

Store-Logos sind optionale Bilder, die Sie für eine angepasstere Darstellung im Store hochladen können. Es wird empfohlen, dass Sie diese Bilder für die beste Anzeige im Store-Eintrag für alle Geräte und Betriebssystemversionen bereitstellen, die Ihre App unterstützt.

Sie können diese Bilder als PNG-Dateien bereitstellen, die den folgenden Richtlinien entsprechen sollten:

- **9:16 (720 x 1080 oder 1440 x 2160 Pixel)**: Dies ist das Hauptbild für Store-Einträge für Kunden mit Windows10- und Xbox-Geräten, daher wird dringend empfohlen, dieses Bild bereitzustellen. Ihr Angebot sieht ohne das Bild nicht gut aus. Das Bild sollte den Namen Ihrer App enthalten, und Text auf dem Bild sollte die Lesbarkeitsanforderungen (Kontrastverhältnis von 4,5:1) erfüllen.  
- **1080 x 1080 oder 2160 x 2160 Pixel (1:1)**: Dieses Bild wird unter Umständen in einigen Layouts angezeigt. Wenn Sie es bereitstellen, achten Sie darauf, dass es den App-Namen enthält.
- **(300 x 300 Pixel) (1:1)**: Dieses Bild (auch als **App-Kachelsymbol** bezeichnet) wird bei der Anzeige des Store-Eintrags Ihrer App für Kunden unter Windows Phone 8.1 und früheren Versionen verwendet. Wenn Sie dieses Bild nicht bereitstellen, sehen Kunden unter Windows Phone8.1 und früheren Versionen im Eintrag für Ihre App ein leeres Symbol. (Dies gilt auch für Kunden unter Windows10, wenn Ihre App nur Pakete für Windows Phone8.1 oder frühere Versionen enthält.) Wenn Ihre Übermittlung *nur* UWP-Pakete enthält, müssen Sie dieses Bild nicht bereitstellen. (Beachten Sie Folgendes: Wenn Ihre Übermittlung sowohl Windows Phone8.x-Pakete als auch UWP-Pakete enthält und Sie dieses Bild bereitstellen, kann es unter Windows10 in bestimmten Store-Layouts verwendet werden. Um dies zu verhindern, können Sie einen [plattformspezifischen Eintrag](create-platform-specific-store-listings.md) für die Windows Phone-Betriebssystemversionen erstellen und nur das Symbol für die App-Kachel aufnehmen.

Außerdem haben die Möglichkeit, zu verhindern, dass der Store Logobilder anzeigt, die in den Paketen Ihrer App verwendet werden, wenn Ihr Angebot für Kunden mit Windows10 angezeigt wird, und der Store muss stattdessen nur Bilder verwenden, die Sie hochladen. Dies bietet Ihnen mehr Kontrolle über die Darstellung Ihrer App in verschiedenen Anzeigen im Store unter Windows 10.

Wenn Sie nur hochgeladene Bilder für die Anzeige im Store auf Windows 10 bereitstellen, aktivieren Sie das Kontrollkästchen mit der Bezeichnung **For Windows 10 customers, display uploaded logo images instead of the images from my packages**.

Durch Aktivieren dieses Kontrollkästchens wird ein neuer Abschnitt namens **Uploaded Store logos** angezeigt. Hier können Sie 3 Bilder, u.a. das 300 x 300 große App-Kachelsymbol, hochladen (Wenn Sie das Kontrollkästchen aktivieren, wird das Feld zum Bereitstellen dieses Bilds in diesen Abschnitt verschoben). Es wird empfohlen, alle drei Bildgrößen bereitzustellen, wenn Sie diese Option verwenden: 300 x 300, 150 x 150 und 71 x 71 Pixel. Es ist jedoch nur die Größe 300 x 300 erforderlich.


## <a name="additional-art-assets"></a>Zusätzliche Grafikobjekte

In diesem Abschnitt können Sie Grafiken bereitstellen, damit Sie Ihr Produkt im Store effektiver präsentieren können: Werbebilder, Xbox-Bilder, optionale Werbebilder und Trailer. Wir empfehlen die Bereitstellung dieser Bilder, um einen einladenden Store-Eintrag zu erstellen. Das **16:9 "Favoritenbild" (1920 x 1080 oder 3840 x 2160 Pixel)** wird vor allem empfohlen, wenn Sie beabsichtigen [Videotrailer](#trailers) im Store-Eintrag anzubieten. Wenn Sie das Bild nicht anbieten, wird Ihre Trailer nicht am Anfang der Liste angezeigt.

Wählen Sie zum Hinzufügen dieser Bilder **Details anzeigen** im Abschnitt **Additional art assets**.


## <a name="promotional-images"></a>Promotional images (Werbebilder)

Die Bilder in diesem Abschnitt können das Aussehen des App-Eintrags verbessern. Ohne das Bild kann die App jedoch nicht für Werbemöglichkeiten in Betracht gezogen werden. Das Bereitstellen von Werbebildern für Ihre App garantiert nicht, dass die App präsentiert wird. Weitere Informationen finden Sie unter [Einfaches Bewerben Ihrer App](make-your-app-easier-to-promote.md).

Im Folgenden finden Sie einige Tipps, die Sie beim Entwerfen Ihrer Werbebilder beachten sollten:

- Bilder müssen im PNG-Format vorliegen.
- Wählen Sie dynamische Bilder, die mit der App zusammenhängen und den Wiedererkennungswert sowie die Differenzierung zu fördern. Vermeiden Sie Stockfotografien oder generische visuelle Elemente.
- Fügen Sie keinen Text hinzu (abgesehen von Ihrem Branding).
- Halten Sie leeren Platz im Bild möglichst gering.
- Vermeiden Sie das Anzeigen der Benutzeroberfläche Ihrer App, und verwenden Sie keine Bilder für bestimmte Geräte.
- Vermeiden Sie politische und nationale Designs, Flaggen oder religiöse Symbole.
- Fügen Sie keine Bilder von taktlosen Gesten, Nacktheit, Glücksspiel, Währung, Drogen, Tabakprodukte oder Alkohol hinzu.
- Verwenden Sie keine Bilder mit Waffen, die auf den Benutzer gerichtet sind, oder übermäßige Gewalt und Blut.

Das **16:9 "Favoritenbild" (1920 x 1080 oder 3840 x 2160 Pixel)** wird in verschiedenen Layouts im Store auf allen Windows10-Geräten verwendet. Es wird empfohlen, dieses Image bereitzustellen, unabhängig davon, auf welche Betriebssystemversionen oder Gerättypen die App ausgerichtet ist. Dieses Bild ist *erforderlich* für die ordnungsgemäße Anzeige, wenn Ihr Eintrag [Videotrailer](#trailers) enthält. Für Kunden mit Windows10, Version 1607 oder höher, wird es als Hauptbild auf Ihrem Store-Eintrag verwendet (oder es wird angezeigt, nachdem alle Trailer beendet sind). 

Die Bildgröße **2:1 (2400 x 1200)** wird nur verwendet, wenn Ihre App die Hologramm-Gerätefamilie unterstützt.

Bedenken Sie beim Entwerfen Ihres Bilds, dass in einigen Layouts im unteren Bilddrittel ein Farbverlauf angewendet wird, damit wir Marketingtext lesbar über dem Bild anzeigen können. Stellen Sie daher sicher, dass Sie im unteren Drittel keinen Text oder wichtige visuelle Elemente verwenden. Außerdem schneiden wir Ihr Bild u.U. zu; platzieren Sie das Branding und die wichtigsten Informationen zu Ihrer App daher in der Bildmitte.  

<!-- update? ![guidelines for spotlight image](images/spotlight1.jpg) 
![well-designed spotlight image](images/spotlight2.jpg)

The image below shows the key proportions to keep in mind. The "safe zone" in the center will be prominent even if we crop the image. The "dynamic text area" is where text and a gradient may appear.  -->

## <a name="xbox-images"></a>Xbox-Bilder

Diese Bilder werden für die ordnungsgemäße Anzeige empfohlen, wenn Sie Ihre App auf Xbox veröffentlichen. 

Es gibt 3 verschiedene Größen, die Sie hochladen können:
- **Grafik mit Branding, 584 x 800 Pixel**: Verwendet im Xbox.com-Store. Muss den Titel des Produkts enthalten. 
- **Herobild mit Titel, 1920 x 1080 Pixel**: Muss den Titel des Produkts enthalten.
- **Empfohlenes Angebot, 1080 x 1080 Pixel**: Verwendet im Xbox Store. Muss den Titel des Produkts enthalten.

> [!NOTE]
> Sie müssen ebenfalls für die besten Anzeige auf Xbox ein **9:16 (720 x 1080 oder 1440 x 2160 Pixel)** Bild im Abschnitt [Store-Logos](#store-logos) angeben.


## <a name="optional-promotional-images"></a>Optionale Werbebilder

Wenn Ihre App frühere Betriebssystemversionen (Windows8.x und/oder Windows Phone8.x) unterstützt, müssen diese Bilder bereitgestellt werden, damit Ihre App in Werbelayouts bereitgestellt werden kann (dies garantiert nicht, dass die App präsentiert wird). Wenn Ihre App diese älteren Betriebssystemversionen nicht unterstützt, können Sie diesen Abschnitt überspringen.

**Für Windows Phone8.1 und frühere Versionen** können zwei Bildgrößen in Werbelayouts verwendet werden: **1000 x 800 Pixel (5:4)** und **358 x 358 Pixel (1:1)**. Wenn Ihre App unter Windows Phone 8.1 oder einer früheren Version ausgeführt wird, wird die Bereitstellung von Bildern in diesen beiden Größen empfohlen, damit sie für Werbung in Frage kommen.  

> [!TIP]
> Stellen Sie ein 300 x 300 großes App-Kachelsymbol im Abschnitt [Store-Logos](#store-logos) für alle Übermittlungen bereit, die Windows Phone 8.1 oder früher unterstützen. Dadurch wird sichergestellt, dass Ihre App im Store nicht mit einem leeren Symbol angezeigt wird.  

**Für Windows 8.1 und frühere Versionen** verwenden manche Werbelayouts unter Umständen ein Bild der Größe **414 x 180** Pixel. Wenn Ihre App unter Windows 8.1 oder früheren Versionen ausgeführt wird, wird das Bereitstellen eines Bilds in dieser Größe empfohlen, damit sie für Werbung in Frage kommt.


## <a name="trailers"></a>Trailer

Trailer sind kurzen Videos, die Kunden die Anzeige Ihres Produkts in Aktion ermöglichen, damit sie seine Funktionen besser nachvollziehen können. Sie werden am oberen Rand des App Store-Eintrags angezeigt (solange Sie ein **1920 x 1080 Pixel großes Bild (16:9)** im Abschnitt [Werbebilder](#promotional-images) enthalten). 

Trailer sind mit [Smooth Streaming](http://www.iis.net/downloads/microsoft/smooth-streaming) codiert. Dabei wird die Qualität eines für Kunden angezeigten Videostreams in Echtzeit basierend auf der verfügbaren Bandbreite und CPU-Ressourcen angepasst.

> [!NOTE]
> Trailer werden nur für Kunden unter Windows10, Version 1607 oder höher, angezeigt.

### <a name="upload-trailers"></a>Trailer hochladen

Sie können bis zu 15 Trailer zu Ihrem Store-Eintrag hinzufügen. Achten Sie darauf, dass sie die für jeden Trailer unten aufgeführten Anforderungen erfüllen.

Sie müssen eine Videodatei (MP4 oder MOV), eine Miniaturansicht und einen Titel für jeden Trailer bereitstellen.

> [!IMPORTANT]
> Wenn Sie Trailer verwenden, müssen Sie auch ein **1920 x 1080 Pixel großes Bild (16:9)** im Abschnitt [Werbebilder](#promotional-images) angeben, damit Ihre Trailer am Anfang unserer Store-Einträge aufgelistet werden. Dieses Bild wird angezeigt, wenn Ihre Trailer beendet sind.

Befolgen Sie folgende Empfehlungen, damit Ihre Trailer effektiv sind:
- Trailer sollten eine gute Qualität und eine minimale Länge aufweisen (2Minuten oder weniger wird empfohlen). 
- Bildfrequenz und Auflösung sollten dem Quellmaterial entsprechen. Beispielsweise sollten mit 720p60 aufgenommene Inhalte codiert und mit 720p60 hochgeladen werden. 
- Verwenden Sie eine andere Miniaturansicht für jeden Trailer, sodass Kunden wissen, dass sie eindeutig sind.
- Da bei einigen Layouts der obere und untere Rand der Trailer leicht abgeschnitten sein kann, stellen Sie sicher, dass wichtige Informationen in der Mitte des Bildschirms angezeigt werden.

Sie müssen auch die unten genannten Anforderungen erfüllen.

**So fügen Sie Trailer zu Ihrem Eintrag hinzu:**
1. Laden Sie die **Videodatei** Ihres Trailers im angegebenen Feld hoch. Ein Dropdownfeld wird auch angezeigt für den Fall, dass Sie einen Trailer wiederverwenden möchten, den Sie bereits hochgeladen haben (z.B. für einen Store-Eintrag in einer anderen Sprache).
2. Nachdem Sie den Trailer hochgeladen haben, müssen Sie ein **Miniaturbild** dafür hochladen. Dies muss eine PNG-Datei mit 1920 x 1080 Pixeln sein. In der Regel handelt es sich um ein Standbild aus dem Trailer.
3. Klicken Sie auf das Stiftsymbol, um einen **Titel** für Ihren Trailer hinzuzufügen (maximal 255Zeichen).
4. Wenn Sie weitere Trailer zum Eintrag hinzufügen möchten, klicken Sie auf **Add trailer**, und wiederholen Sie die oben aufgeführten Schritte.

Um einen Trailer zu entfernen, klicken Sie auf das **X** neben dem Dateinamen. Sie können auswählen, ob er nur aus den aktuellen Store-Einträgen oder aus allen Store-Einträgen für Ihr Produkt entfernt werden soll (d.h. nur für diese Sprache oder für alle Sprachen).

### <a name="trailer-requirements"></a>Traileranforderungen

Wenn Sie Ihre Trailer bereitstellen, müssen Sie die folgenden Anforderungen erfüllen:

- Das Videoformat muss MOV oder MP4 sein. 
- Die Videodauer muss weniger als 30Minuten betragen. 
- Die Dateigröße des Trailers darf 10GB nicht überschreiten. 
- Die Miniaturansicht muss eine PNG-Datei mit einer Auflösung von 1920 x 1080 Pixeln sein. 
- Der Titel darf 255Zeichen nicht überschreiten. 

Wie die anderen Felder auf der Seite des Store-Eintrags müssen Trailer die Zertifizierung bestehen, bevor Sie sie im Store veröffentlichen können. Achten Sie darauf, dass Ihre Trailer die [Windows Store-Richtlinien](https://msdn.microsoft.com/library/windows/apps/dn764944.aspx) einhalten.

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

