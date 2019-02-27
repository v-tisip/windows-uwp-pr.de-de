---
title: Bewährte Methoden für das Schreiben von Dateien
description: Hier erfahren Sie bewährte Methoden für die Verwendung von verschiedenen Datei Schreiben von Methoden der Klassen FileIO und PathIO.
ms.date: 02/06/2019
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: f8bed97e060015f92ff95c9f7d797bbcb83db431
ms.sourcegitcommit: 079801609165bc7eb69670d771a05bffe236d483
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/27/2019
ms.locfileid: "9115707"
---
# <a name="best-practices-for-writing-to-files"></a>Bewährte Methoden für das Schreiben von Dateien

**Wichtige APIs**

* [**FileIO-Klasse**](https://docs.microsoft.com/uwp/api/Windows.Storage.FileIO)
* [**PathIO-Klasse**](https://docs.microsoft.com/uwp/api/windows.storage.pathio)

Entwickler treten eine Reihe von allgemeinen Problemen in einigen Fällen aus, wenn die Methoden **Schreiben** , der Klassen [**FileIO**](https://docs.microsoft.com/uwp/api/Windows.Storage.FileIO) und [**PathIO**](https://docs.microsoft.com/uwp/api/windows.storage.pathio) zum System e/a-Dateivorgänge durchführen. Beispielsweise enthalten häufige Probleme:

• Die app eine Ausnahme empfängt, wenn eine der Methoden aufrufen wird teilweise • eine Datei geschrieben. • Die Vorgänge bleiben. TMP-Dateien mit dem Namen den Namen der Zieldatei ähnelt.

Die Methoden **Schreiben** , der Klassen [**FileIO**](https://docs.microsoft.com/uwp/api/Windows.Storage.FileIO) und [**PathIO**](https://docs.microsoft.com/uwp/api/windows.storage.pathio) umfassen Folgendes:

* **WriteBufferAsync**
* **WriteBytesAsync**
* **WriteLinesAsync**
* **WriteTextAsync**

 Dieser Artikel enthält Informationen zur Funktionsweise dieser Methoden strukturiert besser wann und deren Verwendung verstehen. Dieser Artikel enthält Richtlinien und versucht nicht, eine Lösung für alle möglichen Datei-e/a-Probleme bereitzustellen. 

> [!NOTE]
> Dieser Artikel befasst sich der Methoden der **FileIO** Beispiele und Diskussionen. Allerdings die **PathIO** Methoden folgen einem ähnlichen Muster und die meisten der in diesem Artikel gilt für diese Methoden zu. 

## <a name="conveience-vs-control"></a>Conveience im Vergleich zu Steuerelement

Ein [**StorageFile**](https://docs.microsoft.com/uwp/api/windows.storage.storagefile) -Objekt ist keine Datei-Handle, wie das systemeigene Win32-Programmiermodell. Stattdessen wird ein [**StorageFile**](https://docs.microsoft.com/uwp/api/windows.storage.storagefile) eine Darstellung einer Datei mit Methoden auf, um den Inhalt zu bearbeiten.

Grundlegendes zu diesem Konzept ist nützlich, wenn e/a mit einer **StorageFile**durchführen. Im Abschnitt [Schreiben einer Datei](quickstart-reading-and-writing-files.md#writing-to-a-file) enthält z. B. drei Methoden zum Schreiben in eine Datei:

* Verwenden die [**FileIO.WriteTextAsync**](https://docs.microsoft.com/uwp/api/windows.storage.fileio.writetextasync) -Methode.
* Durch Erstellen eines Puffers aus, und anschließend die [**FileIO.WriteBufferAsync**](https://docs.microsoft.com/en-us/uwp/api/windows.storage.fileio.writebufferasync) -Methode aufrufen.
* Die vier Schritten-Modell mit einem Stream:
  1. [Öffnen](https://docs.microsoft.com/uwp/api/windows.storage.storagefile.openasync) der Datei in einen Datenstrom abzurufen.
  2. [Erhalten](https://docs.microsoft.com/uwp/api/windows.storage.streams.irandomaccessstream.getoutputstreamat) Sie einen Ausgabedatenstrom.
  3. Erstellen Sie ein [**DataWriter**](https://docs.microsoft.com/uwp/api/windows.storage.streams.datawriter) -Objekt, und rufen Sie die entsprechende Methode **Schreiben** .
  4. [Übernehmen](https://docs.microsoft.com/uwp/api/windows.storage.streams.datawriter.storeasync) der Daten in den Daten Writer und den Ausgabedatenstrom zu [leeren](https://docs.microsoft.com/uwp/api/windows.storage.streams.ioutputstream.flushasync) .

Die ersten beiden Szenarien werden am häufigsten von apps verwendet. Schreiben in die Datei in einem einzigen Vorgang ist einfacher, code und verwalten, und die Verantwortung der app auch aus Umgang mit vielen der die Komplexität der e/a-Datei entfernt. Jedoch erreichen Ihren Preis: den Verlust der Kontrolle über den gesamten Vorgang und die Möglichkeit zum Abfangen von Fehlern an bestimmten Punkten.

## <a name="the-transactional-model"></a>Das Transaktions-Modell

Die Methoden **Schreiben** , der Klassen [**FileIO**](https://docs.microsoft.com/uwp/api/Windows.Storage.FileIO) und [**PathIO**](https://docs.microsoft.com/uwp/api/windows.storage.pathio) umschließen Sie die Schritte im dritten Schreib-Modell mit eine zusätzliche Sicherheitsschicht oben beschrieben. Diese Ebene ist in einer Transaktion Speicher eingekapselt.

Um die Integrität der ursprünglichen Datei für den Fall, dass ein Fehler auftritt, während die Daten zu schützen, verwenden die **Schreiben** ein Transaktions-Modell durch Öffnen der Datei mit [**OpenTransactedWriteAsync**](https://docs.microsoft.com/uwp/api/windows.storage.storagefile.opentransactedwriteasync). Dieser Prozess erstellt ein [**StorageStreamTransaction**](https://docs.microsoft.com/uwp/api/windows.storage.storagestreamtransaction) -Objekt. Nachdem dieses Transaktionsobjekt erstellt wurde, Schreiben Sie die APIs die Daten, ähnlich wie im Beispiel [Für den Zugriff auf](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/FileAccess) oder im Codebeispiel wird im Artikel [**StorageStreamTransaction**](https://docs.microsoft.com/uwp/api/windows.storage.storagestreamtransaction) .

Das folgende Diagramm zeigt die zugrunde liegenden Aufgaben durch die die **WriteTextAsync** -Methode in einem erfolgreichen Schreibvorgang. Diese Abbildung zeigt eine vereinfachte Ansicht des Vorgangs. Beispielsweise überspringt Schritte, z. B. Text-Codierung und asynchronen Abschluss in verschiedenen Threads.

![UWP-API-Aufruf Sequenzdiagramm zum Schreiben in eine Datei](images/file-write-call-sequence.svg)

Die Vorteile der Verwendung von Methoden **Schreiben** der Klassen [**FileIO**](https://docs.microsoft.com/uwp/api/Windows.Storage.FileIO) und [**PathIO**](https://docs.microsoft.com/uwp/api/windows.storage.pathio) anstelle des komplexeren vier Schritten Modells mit einem Stream sind:

* Ein API-Aufruf, alle temporären Schritte, einschließlich Fehlern zu behandeln.
* Die ursprüngliche Datei wird beibehalten, wenn ein Fehler auftritt.
* Der Systemstatus versucht, möglichst sauber gehalten werden.

Mit so vielen möglichen intermediate Fehlerquellen gibt es jedoch eine höhere Wahrscheinlichkeit des Fehlers. Wenn ein Fehler auftritt, kann es schwierig sein zu verstehen, wo der Prozess fehlgeschlagen ist. Den folgenden Abschnitten werden einige der der Fehler, die Sie möglicherweise auftreten, wenn die Methoden **Schreiben** verwenden und mögliche Lösungen.

## <a name="common-error-codes-for-write-methods-of-the-fileio-and-pathio-classes"></a>Allgemeine Fehlercodes für Methoden zum Schreiben der FileIO und PathIO

In dieser Tabelle sind allgemeine Fehlercodes, die app-Entwickler auftreten, wenn Sie die Methoden **Schreiben** zu verwenden. Die Schritte in der Tabelle zu den Schritten im vorherigen Diagramm entsprechen.

|  Fehler Name (Wert)  |  Schritte  |  Ursachen  |  Lösungen  |
|----------------------|---------|----------|-------------|
|  ERROR_ACCESS_DENIED (0 X 80070005)  |  5  |  Die ursprüngliche Datei möglicherweise zum Löschen, möglicherweise aus einer vorherigen Vorgangs gekennzeichnet.  |  Sie wiederholt den Vorgang.</br>Stellen Sie sicher, Zugriff auf die Datei synchronisiert wird.  |
|  ERROR_SHARING_VIOLATION (0 X 80070020)  |  5  |  Die ursprüngliche Datei wird durch ein weiteres exklusive Schreiben geöffnet.   |  Sie wiederholt den Vorgang.</br>Stellen Sie sicher, Zugriff auf die Datei synchronisiert wird.  |
|  ERROR_UNABLE_TO_REMOVE_REPLACED (0X80070497)  |  19-20  |  Die ursprüngliche Datei (file.txt) konnte nicht ersetzt werden, da es verwendet wird. Einen anderen Prozess oder Vorgang befragt Zugriff auf die Datei, bevor sie ersetzt werden konnte.  |  Sie wiederholt den Vorgang.</br>Stellen Sie sicher, Zugriff auf die Datei synchronisiert wird.  |
|  ERROR_DISK_FULL (0X80070070)  |  7, 14, 16, 20  |  Das durchgeführte Modell wird eine zusätzliche Datei erstellt, und diese zusätzlichen Speicher verbraucht.  |    |
|  ERROR_OUTOFMEMORY (0X8007000E)  |  14, 16  |  Dies kann passieren, aufgrund von mehreren ausstehenden e/a-Vorgänge oder große Dateien.  |  Eine präzisere Vorgehensweise, indem Sie den Datenstrom steuern möglicherweise den Fehler beheben.  |
|  E_FAIL (0 X 80004005) |  Any  |  Verschiedenes  |  Sie wiederholt den Vorgang. Wenn weiterhin ein Fehler auftritt, es ist möglicherweise ein Plattform-Fehler, und die app sollte beendet werden, da es in einen inkonsistenten Zustand ist. |

## <a name="other-considerations-for-file-states-that-might-lead-to-errors"></a>Weitere Aspekte für Datei Zustände, die zu Fehlern führen kann

Abgesehen vom Fehler zurückgegebene **Schreiben** müssen Sie hier einige Richtlinien auf, was eine app beim Schreiben in eine Datei erwarten kann sind.

### <a name="data-was-written-to-the-file-if-and-only-if-operation-completed"></a>Daten wurde in die Datei geschrieben, wenn es sich bei Vorgang abgeschlossen

Ihre app sollte keine Annahme über Daten in der Datei erstellen, während ein Schreibvorgang ausgeführt wird. Versuchen, auf die Datei zuzugreifen, bevor ein Vorgang abgeschlossen ist, kann zu Datenverlust führen. Ihre app sollte der laufenden ausstehenden e/as verantwortlich.

### <a name="readers"></a>Leser

Wenn die Datei geschrieben wird auch von einem polite Reader verwendet wird (d. h. mit [**FileAccessMode.Read**](https://docs.microsoft.com/uwp/api/Windows.Storage.FileAccessMode)geöffnet, nachfolgende Lesevorgänge tritt ein Fehler ERROR_OPLOCK_HANDLE_CLOSED (0x80070323). In einigen Fällen wiederholen Sie apps Öffnen der Datei zum Lesen erneut während des Vorgangs **Schreiben** ausgeführt wird. Dies kann eine Racebedingung führen auf dem **Schreiben** letztendlich schlägt fehl, bei dem Versuch, die ursprüngliche Datei überschrieben werden, da es nicht ersetzt werden kann.

### <a name="files-from-knownfolders"></a>Dateien aus KnownFolders

Ihre app möglicherweise nicht die einzige app, die versucht, auf eine Datei auf eines der [**KnownFolders**](https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders)zuzugreifen. Es ist nicht garantiert werden, wenn der Vorgang erfolgreich ist, den Inhalt, die eine app in die Datei schreibt konstant bleiben werden, das nächste Mal versucht wird, die Datei zu lesen. Freigabe oder Zugriff verweigert auch, Fehler, die immer häufiger unter diesem Szenario.

### <a name="conflicting-io"></a>In Konflikt stehenden e/a

Die Wahrscheinlichkeit, dass Parallelitätsfehler können gesenkt werden, wenn die app die Methoden **Schreiben** für Dateien in der lokalen Daten verwendet, aber Vorsicht jedoch weiterhin erforderlich ist. Wenn mehrere **Schreiben** Vorgänge gleichzeitig auf die Datei gesendet werden, besteht keine Garantie, über welche Daten in der Datei endet. Um dies zu verringern, wird empfohlen, dass Ihre app **Schreiben** Vorgänge in die Datei serialisiert.

### <a name="tmp-files"></a>~ TMP-Dateien

Es kann vorkommen, wenn Erzwingen der Vorgang abgebrochen wird (z. B., wenn die app wurde angehalten oder beendet, durch das Betriebssystem wurde), die Transaktion nicht übernommen oder entsprechend geschlossen. Diese lassen sich hinter Dateien mit einer (. ~ TMP) Erweiterung. Sollten Sie diese temporären Dateien löschen, (Wenn sie in der app lokale Daten vorhanden sind) bei der Behandlung von der app-Aktivierungs.

## <a name="considerations-based-on-file-types"></a>Basierend auf Dateitypen Aspekte

Einige Fehler können je nach Art der Dateien, die Häufigkeit, die auf der auf sie zugegriffen werden und die Dateigröße häufiger werden. Es gibt in der Regel drei Kategorien von Dateien, die Ihre app zugreifen kann:

* Dateien erstellt und in den Ordner Ihrer Anwendung lokale Daten vom Benutzer bearbeitet. Diese erstellt und nur bei der Verwendung von Ihrer app bearbeitet werden, und sie nur innerhalb der app vorhanden sind.
* App-Metadaten. Ihre app verwendet diese Dateien, um den eigenen Zustand nachzuverfolgen.
* Andere Dateien an Speicherorten des Dateisystems, in denen Ihre app Funktionen zum Zugreifen auf deklariert hat. Diese befinden sich am häufigsten in eines der [**KnownFolders**](https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders).

Ihrer app hat Vollzugriff auf den ersten zwei Kategorien von Dateien, da sie Teil Ihrer app-Paket-Dateien sind und ausschließlich von der app zugegriffen werden. Für Dateien in der letzten Kategorie muss Ihre app achten, dass die anderen apps und Diensten Betriebssystem die Dateien gleichzeitig möglicherweise auf zugreifen.

Abhängig von der app kann den Zugriff auf die Dateien auf Häufigkeit variieren:

* Sehr gering. Hierbei handelt es sich in der Regel um Dateien, die geöffnet werden, nachdem die app-Starts und werden beim Speichern, wenn die app angehalten wird.
* Niedrig. Hierbei handelt es sich um Dateien, die der Benutzer ausdrücklich eine Aktion (z. behandelt wird b. speichern oder laden).
* Mittel "oder" Hoch ". Hierbei handelt es sich um Dateien, in denen die app ständig Daten (z. B. Automatisches Speichern Features oder Konstante Metadaten tracking) aktualisieren muss.

Sollten Sie für die Dateigröße die Performance-Daten in der folgenden Tabelle für die **WriteBytesAsync** -Methode. In diesem Diagramm werden die Zeit für einen Vorgang Vs-Dateigröße, über eine durchschnittliche Leistung der 10000 Vorgänge pro Dateigröße in einer kontrollierten Umgebung verglichen.

![WriteBytesAsync-Leistung](images/writebytesasync-performance.png)

Die Zeitwerte auf der y-Achse werden von diesem Diagramm absichtlich ausgelassen, da andere Hardware und Konfigurationen unterschiedliche absoluten Zeitwerte ergibt. Allerdings haben wir haben diese Trends bei unseren Tests konsistent beobachtet:

* Für sehr kleine Dateien (< = 1 MB): die Zeit bis zum Abschluss des Vorgangs beendet ist konsistent schnell.
* Für größere Dateien (> 1 MB): die Zeit bis zum Abschluss des Vorgangs beendet wird gestartet, um exponentiell zu erhöhen.

## <a name="io-during-app-suspension"></a>E/a, während des Anhaltens von Apps

Ihre app muss entwickelt, um anhalten zu behandeln, wenn Sie die Reaktionsfähigkeit Zustandsinformationen oder Metadaten für den Einsatz in späteren Sitzungen möchten. Hintergrundinformationen zum Anhalten der app finden Sie in der [App-Lebenszyklus](../launch-resume/app-lifecycle.md) und [in diesem Blogbeitrag](https://blogs.windows.com/buildingapps/2016/04/28/the-lifecycle-of-a-uwp-app/#qLwdmV5zfkAPMEco.97).

Es sei denn, das Betriebssystem erweiterten Ausführung Ihrer App gewährt, wenn Ihre app angehalten wird, hat es 5 Sekunden, um alle seine Ressourcen freizugeben, und speichern die Daten. Treten Sie für die besten Zuverlässigkeit und Benutzer auf, immer davon ausgehen Sie, dass die Zeit zum Anhalten Aufgaben begrenzt ist. Bedenken Sie die folgenden Richtlinien während der 5-Sekunden-Zeitraum für die Behandlung von anhalten Aufgaben:

* Versuchen Sie, halten e/a auf ein Minimum zu leeren und Version Vorgänge zurückzuführen Racebedingungen zu vermeiden.
* Vermeiden Sie das Schreiben von Dateien, die Hunderte von Millisekunden oder mehr schreiben erfordern.
* Wenn Ihre app die Methoden **Schreiben** , Bedenken Sie alle intermediate Schritte, die diese Methoden erfordern.

Wenn Ihre app auf eine kleine Menge an Zustandsdaten während der Unterbrechung ausgeführt wird, in den meisten Fällen können die Methoden **Schreiben** Sie um die Daten zu leeren. Wenn Ihre app eine große Menge an Zustandsdaten verwendet, sollten Sie jedoch Streams, dass Ihre Daten direkt gespeichert. Dies kann helfen, die Verzögerung vom Transaktions-Modell der Methoden **Schreiben** , die zu reduzieren. 

Ein Beispiel finden Sie unter der [BasicSuspension](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BasicSuspension) .

## <a name="other-examples-and-resources"></a>Andere Beispiele und Ressourcen

Hier sind einige Beispiele und weitere Ressourcen für bestimmte Szenarien.

### <a name="code-example-for-retrying-file-io-example"></a>Codebeispiel für die Wiederholung der Datei-e/a-Beispiel

Nachfolgend finden Sie eine Pseudocode Beispiel zum Wiederholen eines Schreibvorgangs (c#), vorausgesetzt, dass der Schreibvorgang durchgeführt werden, nachdem der Benutzer eine Datei für die Speicherung auswählt ist:

```csharp
Windows.Storage.Pickers.FileSavePicker savePicker = new Windows.Storage.Pickers.FileSavePicker();
savePicker.FileTypeChoices.Add("Plain Text", new List<string>() { ".txt" });
Windows.Storage.StorageFile file = await savePicker.PickSaveFileAsync();

Int32 retryAttempts = 5;

const Int32 ERROR_ACCESS_DENIED = unchecked((Int32)0x80070005);
const Int32 ERROR_SHARING_VIOLATION = unchecked((Int32)0x80070020);

if (file != null)
{
    // Application now has read/write access to the picked file.
    while (retryAttempts > 0)
    {
        try
        {
            retryAttempts--;
            await Windows.Storage.FileIO.WriteTextAsync(file, "Text to write to file");
            break;
        }
        catch (Exception ex) when ((ex.HResult == ERROR_ACCESS_DENIED) ||
                                   (ex.HResult == ERROR_SHARING_VIOLATION))
        {
            // This might be recovered by retrying, otherwise let the exception be raised.
            // The app can decide to wait before retrying.
        }
    }
}
else
{
    // The operation was cancelled in the picker dialog.
}
```

### <a name="synchronize-access-to-the-file"></a>Synchronisierung des Zugriffs auf die Datei

Die [Parallele Programmierung mit .NET Blog](https://blogs.msdn.microsoft.com/pfxteam/) ist eine hervorragende Ressource für Leitfaden für die parallele Programmierung. Insbesondere beschreibt die [post über AsyncReaderWriterLock](https://blogs.msdn.microsoft.com/pfxteam/2012/02/12/building-async-coordination-primitives-part-7-asyncreaderwriterlock/) exklusiven Zugriff auf eine Datei für Schreibvorgänge, während weiterhin eine gleichzeitige Lesezugriff zu verwalten. Denken Sie daran, die e/a auswirkt, serialisieren Leistung.

## <a name="see-also"></a>Weitere Informationen:

* [Erstellen, Schreiben und Lesen einer Datei](quickstart-reading-and-writing-files.md)
