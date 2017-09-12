---
author: drewbatgit
ms.assetid: a128edc8-8a80-4645-ac29-908ede2d1c72
description: "In diesem Artikel wird beschrieben, wie Sie mit „MediaFrameReader“ und „MediaCapture“ Medienframes aus einer oder mehreren verfügbaren Quellen abrufen. Hierzu zählen Farb-, Tiefen- und Infrarotkameras sowie Audiogeräte und sogar benutzerdefinierte Framequellen (etwa für Skeletal-Tracking-Frames)."
title: "Verarbeiten von Medienframes mit „MediaFrameReader“"
ms.author: drewbat
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: bc0cfc468613429d7989c9c0d93bd98246c0195b
ms.sourcegitcommit: 7540962003b38811e6336451bb03d46538b35671
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/26/2017
---
# <a name="process-media-frames-with-mediaframereader"></a>Verarbeiten von Medienframes mit „MediaFrameReader“

In diesem Artikel wird beschrieben, wie Sie mit [**MediaFrameReader**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameReader) und [**MediaCapture**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.MediaCapture) Medienframes aus einer oder mehreren verfügbaren Quellen abrufen. Hierzu zählen Farb-, Tiefen- und Infrarotkameras sowie Audiogeräte und sogar benutzerdefinierte Framequellen (etwa für Skeletal-Tracking-Frames). Dieses Feature wurde für die Verwendung von Apps entworfen, die Medienframes in Echtzeit verarbeiten, wie beispielsweise Augmented-Reality- und Tiefenkamera-Apps.

Wenn Sie normale Videos oder Fotos aufnehmen möchten, wie mit einer typischen Foto-App, sollten Sie möglicherweise eine der anderen Aufnahmemethoden verwenden, die von [**MediaCapture**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.MediaCapture) unterstützt werden. Eine Liste der verfügbaren Methoden zur Medienaufnahme und Artikel zu ihrer Verwendung finden Sie unter [**Kamera**](camera.md).

> [!NOTE] 
> Die in diesem Artikel besprochenen Features sind erst ab Windows10, Version1607, verfügbar.

> [!NOTE] 
> Es gibt ein Beispiel für universelle Windows-Apps, in dem die Verwendung von **MediaFrameReader** zum Anzeigen von Frames aus unterschiedlichen Framequellen demonstriert wird, unter anderem Farb-, Tiefen- und Infrarotkameras. Weitere Informationen finden Sie unter [Beispiel für Kameraframes](http://go.microsoft.com/fwlink/?LinkId=823230).

## <a name="setting-up-your-project"></a>Einrichten Ihres Projekts
Wie bei allen Apps, die **MediaCapture** verwenden, müssen Sie deklarieren, dass Ihre App die *Webcam*-Funktion verwendet. Erst dann können Sie auf Kamerageräte zugreifen. Wenn Ihre App von einem Audiogerät aufzeichnet, müssen Sie auch die *microphone*-Gerätefunktion deklarieren. 

**Hinzufügen von Funktionen zum App-Manifest**

1.  Öffnen Sie in MicrosoftVisual Studio im **Projektmappen-Explorer** den Designer für das Anwendungsmanifest, indem Sie auf das Element **package.appxmanifest** doppelklicken.
2.  Wählen Sie die Registerkarte **Funktionen** aus.
3.  Aktivieren Sie die Kontrollkästchen für **Webcam** und **Mikrofon**.
4.  Für den Zugriff auf die Bibliothek „Bilder und Videos“ aktivieren Sie die Kontrollkästchen für **Bildbibliothek** und **Videobibliothek**.

Im Beispielcode in diesem Artikel werden neben den in der Standard-Projektvorlage enthaltenen APIs auch APIs aus den folgenden Namespaces verwendet.

[!code-cs[FramesUsing](./code/Frames_Win10/Frames_Win10/MainPage.xaml.cs#SnippetFramesUsing)]

## <a name="select-frame-sources-and-frame-source-groups"></a>Auswählen von Framequellen und Framequellgruppen
Viele Apps, die Medienframes verarbeiten, müssen Frames aus mehreren Quellen gleichzeitig abrufen, z.B. die Farb- und Tiefenkameras eines Geräts. Das [**MediaFrameSourceGroup**] (https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameSourceGroup)-Objekt stellt einen Satz von Medienframequellen dar, die gleichzeitig verwendet werden können. Rufen Sie die statische Methode [**MediaFrameSourceGroup.FindAllAsync**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameSourceGroup.FindAllAsync) auf, um eine Liste aller vom aktuellen Gerät unterstützten Gruppen von Framequellen abzurufen.

[!code-cs[FindAllAsync](./code/Frames_Win10/Frames_Win10/MainPage.xaml.cs#SnippetFindAllAsync)]

Sie können auch einen [**DeviceWatcher**](https://msdn.microsoft.com/library/windows/apps/Windows.Devices.Enumeration.DeviceWatcher) erstellen, indem Sie mit [**DeviceInformation.CreateWatcher**](https://msdn.microsoft.com/library/windows/apps/br225427) und dem vom [**MediaFrameSourceGroup.GetDeviceSelector**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameSourceGroup.GetDeviceSelector) zurückgegebenen Wert Benachrichtigungen empfangen, wenn sich die verfügbaren Framequellgruppen für das Gerät ändern, z.B. bei Anschließen einer externen Kamera. Weitere Informationen finden Sie unter [**Auflisten von Geräten**](https://msdn.microsoft.com/windows/uwp/devices-sensors/enumerate-devices).

Eine [**MediaFrameSourceGroup**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameSourceGroup) verfügt über eine Sammlung von [**MediaFrameSourceInfo**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameSourceInfo)-Objekten, die in der Gruppe enthaltene Framequellen beschreiben. Nach dem Abrufen der auf dem Gerät verfügbaren Framequellgruppen können Sie die Gruppe auswählen, die die für Sie relevanten Framequellen verfügbar macht.

Das folgende Beispiel zeigt die einfachste Möglichkeit zum Auswählen einer Framequellgruppe. Vom Code werden dann einfach Schleifen durch alle verfügbaren Gruppen und anschließend durch die einzelnen Elemente in der [**SourceInfos**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameSourceGroup.SourceInfos)-Sammlung durchgeführt. Für jede **MediaFrameSourceInfo** wird geprüft, ob sie die gewünschten Funktionen unterstützt. In diesem Fall wird die [**MediaStreamType**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameSourceInfo.MediaStreamType)-Eigenschaft auf den Wert [**VideoPreview**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.MediaStreamType) überprüft. D.h. das Gerät stellt einen Videovorschau-Stream bereit, und die [**SourceKind**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameSourceInfo.SourceKind)-Eigenschaft wird auf den Wert [**Farbe**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameSourceKind) überprüft, um anzuzeigen, dass die Quelle Farbframes bereitstellt.

[!code-cs[SimpleSelect](./code/Frames_Win10/Frames_Win10/MainPage.xaml.cs#SnippetSimpleSelect)]

Diese Methode zur Identifizierung der gewünschten Framequellgruppe und Framequellen ist für einfache Fälle geeignet. Wenn Sie jedoch anhand komplexerer Kriterien Framequellen auswählen möchten, wird dieses Verfahren unpraktisch. Eine weitere Methode ist die Auswahl mithilfe von Linq-Syntax und anonymen Objekten. Im folgenden Beispiel wird die Erweiterungsmethode **Select** verwendet, um die **MediaFrameSourceGroup**-Objekte in der *FrameSourceGroups*-Liste in ein anonymes Objekt mit zwei Feldern umzuwandeln:*sourceGroup*, welches die Gruppe selbst darstellt, und *colorSourceInfo*, welches die Farbframequelle in der Gruppe repräsentiert. Für das Feld *colorSourceInfo* wird das Ergebnis der **FirstOrDefault**-Methode festgelegt, die das erste Objekt auswählt, für dessen bereitgestelltes Prädikat die Auflösung „true“ ist. In diesem Fall ist das Prädikat „true“, wenn der Datenstromtyp **VideoPreview** und die Art der Quelle **Color** ist und sich die Kamera an der Vorderseite des Geräts befindet.

Aus der Liste der von der oben beschriebenen Abfrage zurückgegebenen anonymen Objekte werden mit der **Where**-Erweiterungsmethode nur die Objekte ausgewählt, in denen das Feld *colorSourceInfo* nicht NULL ist. Schließlich wird **FirstOrDefault** aufgerufen, um das erste Element in der Liste auszuwählen.

Nun können Sie mithilfe der Felder des ausgewählten Objekts die Verweise auf das ausgewählte **MediaFrameSourceGroup**- und das **MediaFrameSourceInfo**-Objekt abrufen, die die Farbkamera darstellen. Diese werden später verwendet, um das **MediaCapture**-Objekt zu initialisieren und einen **MediaFrameReader** für die ausgewählte Quelle zu erstellen. Abschließend sollten Sie testen, ob Quellgruppe NULL ist. Dies würde bedeuten, dass das aktuelle Gerät nicht über Ihre angeforderten Aufnahmequellen verfügt.

[!code-cs[SelectColor](./code/Frames_Win10/Frames_Win10/MainPage.xaml.cs#SnippetSelectColor)]

Im folgenden Beispiel wird mit einer ähnlichen Methode wie der oben beschriebenen eine Quellgruppe mit Farb-, Tiefen- und Infrarotkameras ausgewählt.

[!code-cs[ColorInfraredDepth](./code/Frames_Win10/Frames_Win10/MainPage.xaml.cs#SnippetColorInfraredDepth)]

## <a name="initialize-the-mediacapture-object-to-use-the-selected-frame-source-group"></a>Initialisieren des MediaCapture-Objekts zum Verwenden der ausgewählten Framequellgruppe
Im nächsten Schritt wird das **MediaCapture**-Objekt initialisiert, um die im vorherigen Schritt ausgewählte Framequellgruppe zu verwenden.

Das **MediaCapture**-Objekt wird üblicherweise an mehreren Stellen in Ihrer App verwendet. Sie sollten daher eine Klassenmembervariable deklarieren, um es aufzunehmen.

[!code-cs[DeclareMediaCapture](./code/Frames_Win10/Frames_Win10/MainPage.xaml.cs#SnippetDeclareMediaCapture)]

Erstellen Sie eine Instanz des **MediaCapture**-Objekts, indem Sie den Konstruktor aufrufen. Erstellen Sie als Nächstes ein [**MediaCaptureSettings**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.MediaCaptureSettings)-Objekt, das zum Initialisieren des **MediaCapture**-Objekts verwendet wird. In diesem Beispiel werden die folgenden Einstellungen verwendet:

* [**SourceGroup**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.MediaCaptureInitializationSettings.SourceGroup) – Damit wird dem System mitgeteilt, welche Quellgruppe zum Abrufen von Frames verwendet wird. Bedenken Sie, dass die Quellgruppe einen Satz von Medienframequellen definiert, die gleichzeitig verwendet werden können.
* [**SharingMode**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.MediaCaptureInitializationSettings.SharingMode) – Damit wird dem System mitgeteilt, ob exklusive Steuerung der Aufnahmequellgeräte erforderlich ist. Bei Festlegung auf [**ExclusiveControl**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.MediaCaptureSharingMode) können Sie die Einstellungen für das Aufnahmegerät, z.B. das Format der von ihm erzeugten Frames, ändern. Wenn jedoch eine andere App bereits über die exklusive Steuerung verfügt, wird der Versuch Ihrer App, das Medienaufnahmegerät zu initialisieren, fehlschlagen. Bei Festlegung auf [**SharedReadOnly**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.MediaCaptureSharingMode) können Sie Frames von den Framequellen empfangen, auch wenn diese gerade von einer anderen App verwendet werden. Sie können jedoch nicht die Einstellungen der Geräte ändern.
* [**MemoryPreference**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.MediaCaptureInitializationSettings.MemoryPreference) – Wenn Sie [**CPU**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.MediaCaptureMemoryPreference) angeben, verwendet das Gerät den CPU-Speicher. Damit wird garantiert, dass eintreffende Frames als [**SoftwareBitmap**](https://msdn.microsoft.com/library/windows/apps/Windows.Graphics.Imaging.SoftwareBitmap)-Objekte verfügbar sind. Wenn Sie [**Auto**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.MediaCaptureMemoryPreference) angeben, wählt das System dynamisch den optimalen Speicherort zum Speichern der Frames aus. Wenn das System die Verwendung des GPU-Speichers auswählt, werden die Medienframes als [**IDirect3DSurface**](https://msdn.microsoft.com/library/windows/apps/Windows.Graphics.DirectX.Direct3D11.IDirect3DSurface)-Objekt und nicht als **SoftwareBitmap**-Objekt übermittelt.
* [**StreamingCaptureMode**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.MediaCaptureInitializationSettings.StreamingCaptureMode) – Legen Sie [**Video**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.StreamingCaptureMode) fest, um anzugeben, dass das Streamen von Audio nicht erforderlich ist.

Rufen Sie [**InitializeAsync**](https://msdn.microsoft.com/library/windows/apps/br226598) auf, um **MediaCapture** mit ihren gewünschten Einstellungen zu initialisieren. Achten Sie darauf, den Aufruf in einem *Try*-Block auszuführen, falls die Initialisierung fehlschlägt.

[!code-cs[InitMediaCapture](./code/Frames_Win10/Frames_Win10/MainPage.xaml.cs#SnippetInitMediaCapture)]

## <a name="set-the-preferred-format-for-the-frame-source"></a>Festlegen des bevorzugten Formats für die Framequelle
Zum Einstellen des bevorzugten Formats einer Framequelle benötigen Sie ein [**MediaFrameSource**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameSource)-Objekt, das die Quelle darstellt. Sie erhalten dieses Objekt, indem Sie auf das [**Frames**](https://msdn.microsoft.com/library/windows/apps/Windows.Phone.Media.Capture.CameraCaptureSequence.Frames)-Verzeichnis des initialisierten **MediaCapture** -Objekts zugreifen und dabei den Bezeichner der gewünschten Framequelle angeben. Aus diesem Grund wurde das [**MediaFrameSourceInfo**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameSourceInfo)-Objekt bei der Auswahl einer Framequellgruppe gespeichert.

Die [**MediaFrameSource.SupportedFormats**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameSource.SupportedFormats)-Eigenschaft enthält eine Liste von [**MediaFrameFormat**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameFormat)-Objekten, die die unterstützten Formate der Framequelle beschreiben. Verwenden Sie die Linq-Erweiterungsmethode **Where**, um basierend auf den gewünschten Eigenschaften ein Format auszuwählen. In diesem Beispiel wird ein Format mit einer Breite von 1.080Pixeln ausgewählt, welches Frames im 32-Bit-RGB-Format bereitstellen kann. Die **FirstOrDefault**-Erweiterungsmethode wählt den ersten Eintrag in der Liste aus. Ist das ausgewählte Format NULL, wird das angeforderte Format nicht von der Framequelle unterstützt. Wenn das Format unterstützt wird, können Sie [**SetFormatAsync**](https://msdn.microsoft.com/library/windows/apps/) aufrufen, um die Verwendung dieses Formats durch die Quelle anzufordern.

[!code-cs[GetPreferredFormat](./code/Frames_Win10/Frames_Win10/MainPage.xaml.cs#SnippetGetPreferredFormat)]

## <a name="create-a-frame-reader-for-the-frame-source"></a>Erstellen eines Frame-Readers für die Framequelle
Verwenden Sie zum Empfangen von Frames für die Medienframequelle einen [**MediaFrameReader**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameReader).

[!code-cs[DeclareMediaFrameReader](./code/Frames_Win10/Frames_Win10/MainPage.xaml.cs#SnippetDeclareMediaFrameReader)]

Instanziieren Sie den Frame-Reader, indem Sie auf Ihrem initialisierten **MediaCapture**-Objekt [**CreateFrameReaderAsync**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.MediaCapture.CreateFrameReaderAsync) aufrufen. Das erste Argument dieser Methode ist die Framequelle, von der Frames empfangen werden sollen. Sie können für jede gewünschte Framequelle einen separaten Frame-Reader erstellen. Das zweite Argument gibt dem System das Ausgabeformat vor, in dem die Frames übermittelt werden sollen. So entfällt das Konvertieren der übermittelten Frames. Beachten Sie, dass eine Ausnahme ausgelöst wird, wenn Sie ein von der Framequelle nicht unterstütztes Format festlegen. Stellen Sie daher sicher, dass dieser Wert in der [**SupportedFormats**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameSource.SupportedFormats)-Sammlung enthalten ist.  

Registrieren Sie nach dem Erstellen des Frame-Readers einen Handler für das [**FrameArrived**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameReader.FrameArrived)-Ereignis, das immer dann ausgelöst wird, wenn ein neuer Frame von der Quelle verfügbar ist.

Rufen Sie [**StartAsync**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameReader.StartAsync) auf, um dem System zu befehlen, mit dem Lesen von Frames aus der Quelle zu beginnen.

[!code-cs[CreateFrameReader](./code/Frames_Win10/Frames_Win10/MainPage.xaml.cs#SnippetCreateFrameReader)]

## <a name="handle-the-frame-arrived-event"></a>Behandeln des „FrameArrived“-Ereignisses
Das [**MediaFrameReader.FrameArrived**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameReader.FrameArrived)-Ereignis wird ausgelöst, wenn ein neuer Frame verfügbar ist. Sie können entweder jeden empfangenen Frame verarbeiten oder Frames nur bei Bedarf verwenden. Der Frame-Reader löst das Ereignis in seinem eigenen Thread aus. Daher müssen Sie möglicherweise Synchronisierungslogik implementieren, damit Sie nicht aus mehreren Threads auf dieselben Daten zugreifen. In diesem Abschnitt wird das Synchronisieren von Zeichenfarbframes zu einem Image-Steuerelement in einer XAML-Seite veranschaulicht. Dieses Szenario behandelt die zusätzliche Synchronisierungseinschränkung, die erfordert, dass alle Updates für XAML-Steuerelemente im UI-Thread ausgeführt werden.

Als erster Schritt beim Anzeigen von Frames in XAML wird ein Bild-Steuerelement erstellt. 

[!code-xml[ImageElementXAML](./code/Frames_Win10/Frames_Win10/MainPage.xaml#SnippetImageElementXAML)]

Deklarieren Sie auf der CodeBehind-Seite eine Klassenmembervariable vom Typ **SoftwareBitmap**. Diese wird als Hintergrundpuffer verwendet, in den alle eingehenden Bilder kopiert werden. Beachten Sie, dass nicht die Bilddaten selbst kopiert werden, sondern nur die Objektverweise. Deklarieren Sie außerdem einen booleschen Wert, um nachzuverfolgen, ob der UI-Vorgang aktuell ausgeführt wird.

[!code-cs[DeclareBackBuffer](./code/Frames_Win10/Frames_Win10/MainPage.xaml.cs#SnippetDeclareBackBuffer)]

Da Frames als **SoftwareBitmap**-Objekte übermittelt werden, müssen Sie ein [**SoftwareBitmapSource**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Media.Imaging.SoftwareBitmapSource)-Objekt erstellen, mit dem Sie eine **SoftwareBitmap** als Quelle für ein XAML-**Steuerelement** verwenden können. Sie sollten die Bildquelle in Ihrem Code festlegen, bevor Sie den Frame-Reader starten.

[!code-cs[ImageElementSource](./code/Frames_Win10/Frames_Win10/MainPage.xaml.cs#SnippetImageElementSource)]

Nun wird der **FrameArrived**-Ereignishandler implementiert. Wenn der Handler aufgerufen wird, enthält der *sender*-Parameter einen Verweis auf das **MediaFrameReader**-Objekt, welches das Ereignis ausgelöst hat. Rufen Sie [**TryAcquireLatestFrame**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameReader.TryAcquireLatestFrame) für dieses Objekt auf, um zu versuchen, den aktuellen Frame abzurufen. Wie der Name schon sagt, schlägt das Zurückgeben eines Frames über **TryAcquireLatestFrame** möglicherweise fehl. Testen Sie daher beim Zugreifen auf die VideoMediaFrame- und die SoftwareBitmap-Eigenschaften, ob diese auf NULL festgelegt sind. In diesem Beispiel wird der Operator mit NULL-Bedingung ? verwendet, um auf die **SoftwareBitmap** zurückzugreifen. Anschließend wird geprüft, ob das abgerufene Objekt auf NULL festgelegt ist.

Das **Image**-Steuerelement kann nur Bilder in BRGA8 Format anzeigen, die entweder vormultipliziert sind oder kein Alpha aufweisen. Weist der eingehende Frame nicht dieses Format auf, wird mit der statischen Methode [**Convert**](https://msdn.microsoft.com/library/windows/apps/Windows.Graphics.Imaging.SoftwareBitmap.Covert) die Software-Bitmap in das richtige Format konvertiert.

Als Nächstes wird mit der [**Interlocked.Exchange**](https://msdn.microsoft.com/library/bb337971)-Methode der Verweis auf die eingehende Bitmap mit der Hintergrundpuffer-Bitmap ausgetauscht. Bei dieser Methode werden die Verweise in einer threadsicheren atomischen Operation ausgetauscht. Nach dem Austausch wird das alte Hintergrundpufferbild – jetzt in der *softwareBitmap*-Variablen – gelöscht, um seine Ressourcen zu bereinigen.

Als Nächstes wird mit dem mit dem **Image**-Element verknüpften [**CoreDispatcher**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Core.CoreDispatcher) eine Aufgabe erstellt, die durch Aufrufen von [**RunAsync**](https://msdn.microsoft.com/library/windows/apps/hh750317) im UI-Thread ausgeführt wird. Da die asynchronen Aufgaben in dieser Aufgabe ausgeführt werden, wird der an **RunAsync** weitergegebene Lambda-Ausdruck mit dem *async*- Schlagwort deklariert.

Innerhalb der Aufgabe wird die *_taskRunning*-Variable überprüft, um sicherzustellen, dass zu jedem Zeitpunkt nur eine Instanz der Aufgabe ausgeführt wird. Wird die Aufgabe nicht bereits ausgeführt, wird *_taskRunning* auf „true“ festgelegt, um zu verhindern, dass die Aufgabe erneut ausgeführt wird. **Interlocked.Exchange** wird zum Kopieren aus dem Hintergrundpuffer in eine temporäre **SoftwareBitmap** in einer *while*-Schleife aufgerufen, bis das Hintergrundpufferbild NULL ist. Bei jedem Auffüllen der temporären Bitmap wird die **Source**-Eigenschaft des **Bildes** in eine **SoftwareBitmapSource** umgewandelt. Anschließend wird [**SetBitmapAsync**](https://msdn.microsoft.com/library/windows/apps/dn997856) aufgerufen, um die Bildquelle festzulegen.

Schließlich wird die *_taskRunning*-Variable wieder auf „false“ festgelegt, damit die Aufgabe beim nächsten Aufrufen des Handlers erneut ausgeführt werden kann.

> [!NOTE] 
> Wenn Sie auf das [**SoftwareBitmap**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.VideoMediaFrame.SoftwareBitmap)- oder [**Direct3DSurface**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.VideoMediaFrame.Direct3DSurface)-Objekt zugreifen, das von der [**VideoMediaFrame**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameReference.VideoMediaFrame)-Eigenschaft eines [**MediaFrameReference**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameReference) bereitgestellt wird, erstellt das System einen starken Verweis auf dieses Objekt. Das bedeutet, dass sie nicht entfernt werden, wenn Sie [**Dispose**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameReference.Close) auf dem **MediaFrameReference** aufrufen, der das Objekt enthält. Sie müssen die **Dispose**-Methode von **SoftwareBitmap** oder **Direct3DSurface** explizit direkt aufrufen, damit die Objekte sofort entfernt werden. Andernfalls wird der Garbage Collector den Speicher für diese Objekte schließlich freigeben. Sie wissen jedoch nicht, wann dies sein wird. Wenn die Anzahl der zugeteilten Bitmaps oder Oberflächen die maximale, vom System zugelassene Menge überschreitet, wird der Fluss neuer Frames beendet.


[!code-cs[FrameArrived](./code/Frames_Win10/Frames_Win10/MainPage.xaml.cs#SnippetFrameArrived)]

## <a name="cleanup-resources"></a>Bereinigen von Ressourcen
Achten Sie darauf, nach dem Lesen der Frames den Medienframe-Reader zu beenden, indem Sie [**StopAsync**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameReader.StopAsync) aufrufen, die Registrierung des **FrameArrived**-Handlers aufheben und das **MediaCapture**-Objekt löschen.

[!code-cs[Bereinigen](./code/Frames_Win10/Frames_Win10/MainPage.xaml.cs#SnippetCleanup)]

Weitere Informationen zum Bereinigen von Medienaufnahmeobjekten bei angehaltener Anwendung finden Sie unter [**Anzeigen der Kameravorschau**](simple-camera-preview-access.md).

## <a name="the-framerenderer-helper-class"></a>Die FrameRenderer-Hilfsprogrammklasse
Das Universal Windows-[Beispiel für Kameraframes](http://go.microsoft.com/fwlink/?LinkId=823230) stellt eine Hilfsprogrammklasse zum einfachen Anzeigen der Frames aus Farb-, Infrarot- und Tiefenquellen in Ihrer App bereit. In der Regel sollen Tiefen- und Infrarotdaten nicht nur auf dem Bildschirm angezeigt werden. Dennoch ist diese Hilfsprogrammklasse ein hilfreiches Tool zum Veranschaulichen der Frame-Reader-Funktion und zum Debuggen Ihrer eigenen Frame-Reader-Implementierung.

Die **FrameRenderer**-Hilfsprogrammklasse implementiert die folgenden Methoden.

* **FrameRenderer**-Konstruktor – Der Konstruktor initialisiert die Verwendung des übergebenen XAML-[**Bild**](https://msdn.microsoft.com/library/windows/apps/Windows.UI.Xaml.Controls.Image)-Elements durch die Hilfsprogrammklasse zum Anzeigen von Medienframes.
* **ProcessFrame** – Bei dieser Methode wird ein durch eine [**MediaFrameReference**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameReference) repräsentierter Medienframe in dem in den Konstruktor eingereichten **Bild**-Element angezeigt. Üblicherweise sollten Sie diese Methode aus Ihrem [**FrameArrived**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameReader.FrameArrived)-Ereignishandler aufrufen, wenn der von [**TryAcquireLatestFrame**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameReader.TryAcquireLatestFrame) zurückgegebene Frame übergeben wird.
* **ConvertToDisplayableImage** – Bei dieser Methode wird das Format des Medienframes überprüft und ggf. in ein anzeigbares Format umgewandelt. Bei Farbbildern wird also überprüft, ob als Farbformat BGRA8 festgelegt ist und der Bitmap-Alphamodus prämultipliziert wird. Bei Tiefen- oder Infrarotframes wird jede Scanzeile verarbeitet, um die Tiefen- oder Infrarotwerte mithilfe der ebenfalls im Beispiel enthaltenen und unten aufgeführten **PsuedoColorHelper**-Klasse in einen Pseudo-Farbgradienten umzuwandeln

> [!NOTE] 
> Zum Ändern von Pixeln in **SoftwareBitmap**-Bildern müssen Sie auf einen nativen Speicherpuffer zugreifen. Zu diesem Zweck müssen Sie die in der untenstehenden Codeauflistung enthaltene IMemoryBufferByteAccess COM-Schnittstelle verwenden und die Projekteigenschaften aktualisieren, um die Kompilierung von unsicherem Code zuzulassen. Weitere Informationen finden Sie unter [Erstellen, Bearbeiten und Speichern von Bitmapbildern](imaging.md).

[!code-cs[FrameArrived](./code/Frames_Win10/Frames_Win10/FrameRenderer.cs#SnippetFrameRenderer)]

## <a name="use-multisourcemediaframereader-to-get-time-corellated-frames-from-multiple-sources"></a>Verwenden von MultiSourceMediaFrameReader zum Abrufen zeitkorrelierter Frames aus mehreren Quellen
Ab Windows10, Version 1607, können Sie mit [**MultiSourceMediaFrameReader**](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.multisourcemediaframereader) zeitkorrelierte Frames aus mehreren Quellen empfangen. Diese API vereinfacht im Vergleich mit der [**DepthCorrelatedCoordinateMapper**](https://docs.microsoft.com/en-us/uwp/api/windows.media.devices.core.depthcorrelatedcoordinatemapper)-Klasse die Verarbeitung von Frames aus mehreren Quellen, die zeitlich eng aufeinanderfolgend erfasst wurden. Eine Einschränkung bei der Verwendung dieser neuen Methode ist, das Ereignisse, die eine Frameankunft signalisieren, nur mit der Geschwindigkeit der langsamsten Erfassungsquelle ausgelöst werden. Zusätzliche Frames aus schneller Quellen werden gelöscht. Und da das System erwartet, dass Frames aus verschiedenen Quellen unterschiedlich schnell eintreffen, kann es nicht automatisch erkennen, wenn eine Quelle das Generieren von Frames endgültig beendet hat. Der Beispielcode in diesem Abschnitt zeigt, wie Sie mit einem Ereignis Ihre eigene Timeoutlogik erstellen. Der Aufruf erfolgt, wenn korrelierte Frames nicht in einem von der App festgelegten Zeitlimit eintreffen.

Die Schrittefür die Verwendung von [**MultiSourceMediaFrameReader**](https://docs.microsoft.com/en-us/uwp/api/windows.media.capture.frames.multisourcemediaframereader) ähneln den Schrittenfür die zuvor in diesem Artikel beschriebene Verwendung von [**MediaFrameReader**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameReader). In diesem Beispiel wird eine Farbquelle und eine Tiefenquelle verwendet. Deklarieren Sie einige Zeichenfolgenvariablen, um die Frame-IDs der Medienquelle zu speichern, die verwendet werden, um Frames aus jeder Quelle auswählen. Deklarieren Sie dann ein [**ManualResetEventSlim**](https://docs.microsoft.com/dotnet/api/system.threading.manualreseteventslim?view=netframework-4.7), eine [**CancellationTokenSource**](https://msdn.microsoft.com/library/system.threading.cancellationtokensource.aspx) sowie einen [**EventHandler**](https://msdn.microsoft.com/library/system.eventhandler.aspx), der zur Implementierung von Timeoutlogik für das Beispiel verwendet wird. 

[!code-cs[MultiFrameDeclarations](./code/Frames_Win10/Frames_Win10/MainPage.xaml.cs#SnippetMultiFrameDeclarations)]

Ermitteln Sie mithilfe der in diesem Artikel beschriebenen Techniken eine [**MediaFrameSourceGroup**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameSourceGroup), welche die Farb- und Tiefenquellen enthält, die für dieses Beispielszenario erforderlich sind. Nach Auswahl der gewünschten Framequellengruppe rufen Sie die [**MediaFrameSourceInfo**](https://msdn.microsoft.com/library/windows/apps/Windows.Media.Capture.Frames.MediaFrameSourceInfo) für jede Framequelle ab.

[!code-cs[SelectColorAndDepth](./code/Frames_Win10/Frames_Win10/MainPage.xaml.cs#SnippetSelectColorAndDepth)]

Erstellen und Initialisieren Sie ein **MediaCapture**-Objekt, und übergeben Sie die gewählte Framequellengruppe in den Initialisierungseinstellungen.

[!code-cs[MultiFrameInitMediaCapture](./code/Frames_Win10/Frames_Win10/MainPage.xaml.cs#SnippetMultiFrameInitMediaCapture)]

Nach der Initialisierung des **MediaCapture**-Objekts rufen Sie die [**MediaFrameSource**](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.Frames.MediaFrameSource)-Objekte für die Farb- und Tiefenkameras ab. Speichern Sie die ID für jede Quelle, sodass Sie den eingehenden Frame für die entsprechende Quelle auswählen können.

[!code-cs[GetColorAndDepthSource](./code/Frames_Win10/Frames_Win10/MainPage.xaml.cs#SnippetGetColorAndDepthSource)]

Erstellen und initialisieren Sie den **MultiSourceMediaFrameReader** durch Aufrufen von [**CreateMultiSourceFrameReaderAsync**](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture#Windows_Media_Capture_MediaCapture_CreateMultiSourceFrameReaderAsync_Windows_Foundation_Collections_IIterable_Windows_Media_Capture_Frames_MediaFrameSource__). Übergeben Sie dabei ein Array mit Framequellen für den Reader. Registrieren Sie einen Ereignishandler für das Ereignis [**FrameArrived**](https://docs.microsoft.com/uwp/api/windows.media.capture.frames.multisourcemediaframereader#Windows_Media_Capture_Frames_MultiSourceMediaFrameReader_FrameArrived). Dieses Beispiel erstellt eine Instanz der zuvor in diesem Artikel beschriebenen **FrameRenderer**-Hilfsklasse, die zum Rendern von Frames für ein **Image**-Steuerelement dient. Starten Sie die den Framereader durch Aufrufen von [**StartAsync**](https://docs.microsoft.com/uwp/api/windows.media.capture.frames.multisourcemediaframereader#Windows_Media_Capture_Frames_MultiSourceMediaFrameReader_StartAsync).

Registrieren Sie einen Ereignishandler für das zuvor in diesem Beispiel deklarierte Ereignis **CorellationFailed**. Dieses Ereignis signalisiert, wenn eine der verwendeten Medienframequellen die Produktion von Frames beendet. Rufen Sie schließlich mit [**Task.Run**](https://msdn.microsoft.com/en-us/library/hh195051.aspx) die Timeout-Hilfsmethode **NotifyAboutCorrelationFailure** in einem separaten Thread auf. Die Implementierung dieser Methode wird später in diesem Artikel gezeigt.

[!code-cs[InitMultiFrameReader](./code/Frames_Win10/Frames_Win10/MainPage.xaml.cs#SnippetInitMultiFrameReader)]

Das Ereignis **FrameArrived** wird jedes Mal ausgelöst, wenn ein neuer Frame von einer der Medienframequellen verfügbar ist, die vom **MultiSourceMediaFrameReader** verwaltet werden. Dies bedeutet, dass das Ereignis mit der Geschwindigkeit der langsamsten Medienquelle ausgelöst wird. Wenn eine Quelle mehrere Frames in der Zeit produziert, in der eine langsamere Quelle einen Frame fertigstellt, werden die zusätzlichen Frames aus der schnellen Quelle gelöscht. 

Rufen Sie die dem Ereignis zugeordnete [**MultiSourceMediaFrameReference**](https://docs.microsoft.com/uwp/api/windows.media.capture.frames.multisourcemediaframereference) durch Aufrufen von [**TryAcquireLatestFrame**](https://docs.microsoft.com/uwp/api/windows.media.capture.frames.multisourcemediaframereader#Windows_Media_Capture_Frames_MultiSourceMediaFrameReader_TryAcquireLatestFrame) ab. Rufen Sie die jeder Medienframequelle zugeordnete **MediaFrameReference** durch Aufrufen von [**TryGetFrameReferenceBySourceId**](https://docs.microsoft.com/uwp/api/windows.media.capture.frames.multisourcemediaframereference#Windows_Media_Capture_Frames_MultiSourceMediaFrameReference_TryGetFrameReferenceBySourceId_System_String_) ab. Übergeben Sie dabei die ID-Zeichenfolgen, die Sie gespeichert haben, als der Framereader initialisiert wurde.

Rufen Sie die [**Set**](https://msdn.microsoft.com/library/system.threading.manualreseteventslim.set.aspx)-Methode des **ManualResetEventSlim**-Objekts auf, um zu signalisieren, dass Frames angekommen sind. Dieses Ereignis wird in der **NotifyCorrelationFailure**-Methode überprüft, die in einem separaten Thread ausgeführt wird. 

Schließlich verarbeiten Sie die zeitkorrelierten Medienframes. Dieses Beispiel zeigt einfach den Frame aus der Tiefenquelle an.

[!code-cs[MultiFrameArrived](./code/Frames_Win10/Frames_Win10/MainPage.xaml.cs#SnippetMultiFrameArrived)]

Die Hilfsmethode **NotifyCorrelationFailure** wurde nach dem Start des Framereaders in einem separaten Thread ausgeführt. Überprüfen Sie in dieser Methode, ob das Ereignis des Frameempfangs signalisiert wurde. Beachten Sie, dass dieses Ereignis im **FrameArrived**-Handler ausgelöst wird, sobald ein Satz korrelierter Frames ankommt. Wenn das Ereignis nicht innerhalb einer von der App definierten Zeit ausgelöst wurde (5Sekunden sind ein angemessener Wert), und der Task nicht mit der **CancellationToken**-Methode abgebrochen wurde, hat wahrscheinlich eine der Medienframequellen das Lesen von Frames beendet. In diesem Fall sollten Sie in der Regel den Framereader schließen, indem Sie das **CorrelationFailed**-Ereignis auslösen. Im Handler für dieses Ereignis können Sie den Framereader beenden und die zugeordnet Ressourcen bereinigen (wie zuvor in diesem Artikel gezeigt).

[!code-cs[NotifyCorrelationFailure](./code/Frames_Win10/Frames_Win10/MainPage.xaml.cs#SnippetNotifyCorrelationFailure)]

[!code-cs[CorrelationFailure](./code/Frames_Win10/Frames_Win10/MainPage.xaml.cs#SnippetCorrelationFailure)]

## <a name="related-topics"></a>Verwandte Themen

* [Kamera](camera.md)
* [Allgemeine Foto-, Video- und Audioaufnahme mit „MediaCapture“](basic-photo-video-and-audio-capture-with-MediaCapture.md)
* [Beispiel für Kameraframes](http://go.microsoft.com/fwlink/?LinkId=823230)
 

 




