---
title: Grundlagen am Beispiel von Marble Maze
description: Dieses Dokument beschreibt die fundamentalen Eigenschaften des Marble Maze-Projekt. beispielsweise wie Visual C++ in der Windows-Runtime-Umgebung verwendet wird, wie es erstellt und strukturiert ist und wie es aufgebaut ist.
ms.assetid: 73329b29-62e3-1b36-01db-b7744ee5b4c3
ms.date: 08/22/2017
ms.topic: article
keywords: Windows10, Uwp, Spiele, Beispiel, Directx, Grundlagen
ms.localizationpriority: medium
ms.openlocfilehash: d41a9fe2363e5d5c462fb0646fbcc2479c756119
ms.sourcegitcommit: bf600a1fb5f7799961914f638061986d55f6ab12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2019
ms.locfileid: "9049387"
---
# <a name="marble-maze-sample-fundamentals"></a>Grundlagen am Beispiel von Marble Maze




In diesem Thema werden die fundamentalen Eigenschaften des Marble Maze-Projekt&mdash;s beschrieben, beispielsweise wie Visual C++ in der Windows Runtime-Umgebung verwendet wird, wie es erstellt und strukturiert wird und wie es aufgebaut ist. Das Thema enthält auch eine Beschreibung verschiedener Konventionen, die im Code verwendet werden.

> [!NOTE]
> Den Beispielcode für dieses Dokument finden Sie im [DirectX-Beispielspiel Marble Maze](https://go.microsoft.com/fwlink/?LinkId=624011).

Es folgen einige wichtige Punkte, die in diesem Dokument erläutert werden und die beim Planen und Entwickeln Ihres UWP-Spiels relevant sind.

-   Verwenden Sie die Visual C++ Vorlage **DirectX 11-App (Universelle Windows-App)** in Visual Studio, um das DirectX-UWP-Spiel zu erstellen.
-   Windows-Runtime stellt Klassen und Schnittstellen bereit, sodass Sie UWP-Apps auf moderne, objektorientierte Art und Weise entwickeln können.
-   Verwenden Sie Objektreferenzen mit Hütchensymbol (^), um die Lebensdauer von Windows-Runtime-Variablen zu verwalten, [Microsoft::WRL::ComPtr](https://docs.microsoft.com/cpp/windows/comptr-class) zum Verwalten der Lebensdauer von COM-Objekten und [std::shared\_ptr](https://docs.microsoft.com/cpp/standard-library/shared-ptr-class) oder [std::unique\_ptr](https://docs.microsoft.com/cpp/standard-library/unique-ptr-class) zum Verwalten der Lebensdauer aller anderen, vom Heap zugewiesenen C++-Objekte.
-   In den meisten Fällen verwenden Sie für die Behandlung unerwarteter Fehler die Ausnahmebehandlung anstelle von Ergebniscodes.
-   Verwenden Sie [SAL-Anmerkungen](https://docs.microsoft.com/visualstudio/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects) Kombination mit Codeanalysetools, um Fehler in Ihrer app zu finden.

## <a name="creating-the-visual-studio-project"></a>Erstellen des Visual Studio-Projekts


Wenn Sie heruntergeladen und extrahiert haben das Beispiel, Sie können die **MarbleMaze_VS2017.sln** -Datei (in der **C++** -Ordner) in Visual Studio öffnen, und Sie müssen den Code vor Ihnen.

Beim Erstellen des Visual Studio-Projekts für Marble Maze haben wir mit einem bereits vorhandenen Projekt begonnen. Wenn Sie jedoch noch kein vorhandenes Projekt haben, das die grundlegende, für Ihr DirectX-UWP-Spiel erforderliche Funktionalität bereitstellt, wird empfohlen, ein Projekt basierend auf der Visual Studio-Vorlage **DirectX 11-App (Universelle Windows-App)** zu erstellen, da sie eine grundlegende, funktionierende 3D-Anwendung enthält. Gehen Sie hierzu folgendermaßen vor:

1. Wählen Sie in Visual Studio 2017 **Datei > neue > Projekt**

2. Wählen Sie im Fenster **Neues Projekt** in der linken Randleiste **installiert > Vorlagen > Visual C++**.

3. Wählen Sie in der Liste mittleren **DirectX 11-App (Universal Windows)**. Wenn Sie diese Option nicht angezeigt wird, Sie haben keine die erforderlichen Komponenten installiert&mdash;finden Sie Informationen dazu, wie Sie zusätzliche Komponenten installieren [Ändern Visual Studio 2017 hinzufügen oder Entfernen von Workloads und Komponenten](https://docs.microsoft.com/visualstudio/install/modify-visual-studio) .

4. Verleihen Sie Ihrem Projekt einen **Namen**, einen **Speicherort** für die Dateien gespeichert werden und einen **Namen Projektmappe**, und klicken Sie auf **OK**.

![Neues Projekt](images/marble-maze-sample-fundamentals-1.png)

Eine wichtige Projekteinstellung in der Voralge **DirectX 11-App (Universelle Windows-App)** ist die Option **/ZW**. Diese Option ermöglicht dem Programm die Verwendung der Windows-Runtime-Spracherweiterungen. Sie ist standardmäßig aktiviert, wenn Sie die Visual Studio-Vorlage verwenden. Weitere Informationen zur Vorgehensweise beim Festlegen von Compiler-Optionen in Visual Studio finden Sie unter [Compileroptionen festlegen](https://docs.microsoft.com/cpp/build/reference/setting-compiler-options).

> **Achtung**  die **Option/Zw** ist nicht kompatibel mit Optionen wie z. **B./CLR**. Im Fall von **/clr** können Sie demnach über ein und dasselbe Visual C++-Projekt nicht das .NET Framework und die Windows-Runtime erreichen.

 

Jede UWP-app, die Sie aus dem Microsoft Store erwerben wird in Form von einem app-Paket bereitgestellt. Ein App-Paket enthält ein App-Manifest, das wiederum Informationen zur App beinhaltet. Sie können beispielsweise die Funktionen (d.h. den erforderlichen Zugriff auf geschützte Systemressourcen oder Benutzerdaten) Ihrer App angeben. Wenn Sie festlegen, dass für Ihre App bestimmte Funktionen erforderlich sind, verwenden Sie das Paketmanifest, um die erforderlichen Funktionen zu deklarieren. Das Manifest ermöglicht Ihnen auch die Angabe von Projekteigenschaften wie der Rotation unterstützter Geräte, Kachelbildern und Begrüßungsbildschirm. Sie können das Manifest bearbeiten, indem Sie **Package.appxmanifest** in Ihrem Projekt öffnen. Weitere Informationen zu App-Paketen finden Sie unter [Verpacken von Apps](https://msdn.microsoft.com/library/windows/apps/mt270969).

##  <a name="building-deploying-and-running-the-game"></a>Erstellen, Bereitstellen und Ausführen des Spiels

Wählen Sie in den Dropdownmenüs oben in Visual Studio links neben der grünen Schaltfläche "Wiedergabe" die Konfiguration Ihrer Bereitstellung aus. Wir empfehlen die Einstellung als **Debuggen** und die Architektur Ihres Geräts auf (**x86** für 32-Bit, **x64** für 64-Bit) und auf **Lokaler Computer** festzulegen. Sie können ebenfalls einen **Remotecomputer** oder ein **Gerät** testen, das über USB verbunden ist. Klicken Sie dann auf die grüne Wiedergabeschaltfläche zum Erstellen und Bereitstellen auf Ihrem Gerät.

![Debuggen; X64; Lokaler Computer](images/marble-maze-sample-fundamentals-2.png)

###  <a name="controlling-the-game"></a>Steuern des Spiels

Sie können die Fingereingabe, den Beschleunigungsmesser, Xbox One-Controller oder die Maus-Steuerung von Marble Maze verwenden.

-   Mithilfe des Steuerkreuzes am Controller können Sie das aktive Menüelement ändern.
-   Verwenden Sie Toucheingabe, die ein oder Start Taste am Controller oder die Maus, um ein Menüelement auszuwählen.
-   Über die Fingereingabe, den Beschleunigungsmesser, den linken Ministick oder die Maus können Sie das Labyrinth neigen.
-   Verwenden Sie Toucheingabe, die ein oder Start Taste am Controller oder die Maus zum Schließen von Menüs wie der Highscore-Tabelle.
-   Verwenden Sie die Schaltfläche "Start" am Controller oder der P-Taste auf der Tastatur, um das Spiel anzuhalten oder fortzusetzen.
-   Zum Neustarten des Spiels können Sie die Zurück-Taste am Controller oder die Pos1-Taste auf der Tastatur verwenden.
-   Wenn die Highscore Tabelle angezeigt wird, verwenden Sie die zurück-Taste am Controller oder die POS1-Taste auf der Tastatur, um alle punktergebnisse löschen.

##  <a name="code-conventions"></a>Codekonventionen


Die Windows-Runtime ist eine Programmierschnittstelle, die Sie zum Erstellen von UWP-Apps verwenden können, die nur in einer speziellen Anwendungsumgebung ausgeführt werden. Solche apps verwenden autorisierte Funktionen, Datentypen und Geräte, und werden aus dem Microsoft Store verteilt. Die Windows-Runtime besteht auf der untersten Ebene aus einer binären Anwendungsschnittstelle (Application Binary Interface, ABI). Die ABI ist ein binärer Vertrag auf unterer Ebene, der Windows-Runtime-APIs für mehrere Programmiersprachen zur Verfügung stellt, beispielsweise für JavaScript, die .NET-Sprachen und Visual C++.

Diese Sprachen erfordern für den Aufruf von Windows-Runtime-APIs aus JavaScript und .NET Projektionen, die für die jeweilige Sprachumgebung spezifisch sind. Wenn Sie eine Windows-Runtime-API aus JavaScript oder .NET aufrufen, rufen Sie die Projektion auf, die wiederum die zugrunde liegende ABI-Funktion aufruft. Sie können zwar die ABI-Funktionen direkt aus Standard-C++ aufrufen, jedoch stellt Microsoft auch Projektionen für C++ bereit, da diese die Verwendung der Windows-Runtime-APIs stark vereinfachen und dennoch eine hohe Leistung aufrecht erhalten. Microsoft stellt außerdem Spracherweiterungen für Visual C++ bereit, die spezielle Unterstützung für die Windows-Runtime-Projektionen bieten. Viele dieser Spracherweiterungen ähneln der Syntax für die Sprache C++/CLI. Anstelle einer Zielgruppenadressierung für die Common Language Runtime (CLR) durchzuführen, verwenden systemeigene Apps diese Syntax zum Erreichen der Windows-Runtime. Der Modifizierer in Form einer Objektreferenz, bzw. des Hütchensymbols (^), ist ein wichtiger Teil dieser neuen Syntax, da er die automatische Löschung von Runtime-Objekten anhand einer Referenzzählung ermöglicht. Anstatt Methoden wie [AddRef](https://msdn.microsoft.com/library/windows/desktop/ms691379) und [Release](https://msdn.microsoft.com/library/windows/desktop/ms682317) zum Verwalten der Lebensdauer eines Windows-Runtime-Objekts aufzurufen, löscht die Runtime das Objekt, wenn keine andere Komponente darauf verweist. Dies ist beispielsweise der Fall, wenn es den Bereich verlässt oder wenn Sie alle Verweise auf **nullptr** festlegen. Ein weiterer wichtiger Aspekt beim Erstellen von UWP-Apps ist das **ref new**-Schlüsselwort. Verwenden Sie **ref new** anstelle von **new**, um Windows-Runtime-Objekte mit Verweiszählung zu erstellen. Weitere Informationen finden Sie unter [Typsystem (C++/CX)](https://msdn.microsoft.com/library/windows/apps/hh755822).

> [!IMPORTANT]
> Wenn Sie Windows-Runtime-Objekte oder Komponenten für die Windows-Runtime erstellen, müssen Sie nur **^** und **ref new** verwenden. Sie können die C++-Standardsyntax verwenden, wenn Sie Kernanwendungscode schreiben, in dem die Windows-Runtime nicht genutzt wird.

In Marble Maze werden mit **^** und **Microsoft::WRL::ComPtr** vom Heap zugewiesene Objekte verwaltet und Arbeitsspeicherverluste minimiert. Wir empfehlen die Verwendung ^ die Lebensdauer von Windows-Runtime-Variablen zu **ComPtr** zum Verwalten der Lebensdauer von COM-Variables (z. B. bei Verwendung von DirectX), "und" **Std:: shared\_ptr** "oder" **Std:: unique\_ptr** zum Verwalten der Lebensdauer des alle anderen zu verwalten Heap zugewiesenen C++-Objekte.

 

Weitere Informationen zu den Spracherweiterungen, die für eine C++-UWP-App verfügbar sind, finden Sie unter [Sprachreferenz zu Visual C++ (C++/CX)](https://msdn.microsoft.com/library/windows/apps/hh699871).

###  <a name="error-handling"></a>Fehlerbehandlung

In Marble Maze werden unerwartete Fehler in erster Linie mithilfe der Ausnahmebehandlung verarbeitet. Obwohl für Spielecode zur Angabe von Fehlern traditionell die Protokollierung oder Fehlercodes verwendet werden, beispielsweise **HRESULT**-Werte, bietet die Ausnahmebehandlung zwei wesentliche Vorteile. Zunächst kann sie das Lesen und Verwalten von Code erleichtern. Aus Codeperspektive stellt die Ausnahmebehandlung ein effizienteres Verfahren dar, um einen Fehler an eine Routine weiterzugeben, die den Fehler behandeln kann. Bei der Verwendung von Fehlercodes muss i.d.R. jede Funktion explizit Fehler weitergeben. Ein zweiter Vorteil besteht darin, dass Sie den Visual Studio-Debugger so konfigurieren können, dass er beim Auftreten einer Ausnahme unterbrochen wird, damit die Ausführung unmittelbar an der Position und im Kontext des Fehlers angehalten wird. Die Windows-Runtime macht ebenfalls extensiven Gebrauch von der Ausnahmebehandlung. Deshalb können Sie durch die Verwendung von Ausnahmebehandlung im Code die gesamte Fehlerbehandlung in einem einzigen Modell zusammenfassen.

Es wird empfohlen, in Ihrem Fehlerbehandlungsmodell die folgenden Konventionen zu verwenden:

-   Kommunizieren Sie unerwartete Fehler anhand von Ausnahmen.
-   Verwenden Sie Ausnahmen nicht zum Steuern des Codeflusses.
-   Fangen Sie nur die Ausnahmen ab, die Sie auf jeden Fall behandeln und beheben können. Fangen Sie andernfalls die Ausnahme nicht ab, und ermöglichen Sie das Beenden der App.
-   Wenn Sie eine DirectX-Routine aufrufen, die **HRESULT** zurückgibt, verwenden Sie die **DX::ThrowIfFailed**-Funktion. Diese Funktion wird in ["directxhelper.h"](https://github.com/Microsoft/Windows-appsample-marble-maze/blob/master/C%2B%2B/Shared/DirectXHelper.h)definiert. **ThrowIfFailed** löst eine Ausnahme aus, wenn das bereitgestellte **HRESULT** ein Fehlercode ist. **E\_POINTER** bewirkt beispielsweise, dass **ThrowIfFailed** [Platform::NullReferenceException](https://msdn.microsoft.com/library/windows/apps/hh755823.aspx) auslöst.

    Wenn Sie **ThrowIfFailed** verwenden, platzieren Sie den DirectX-Aufruf in einer separaten Zeile, um die Lesbarkeit des Codes zu verbessern. Dies wird im folgenden Beispiel veranschaulicht.

    ```cpp
    // Identify the physical adapter (GPU or card) this device is running on.
    ComPtr<IDXGIAdapter> dxgiAdapter;
    DX::ThrowIfFailed(
        dxgiDevice->GetAdapter(&dxgiAdapter)
        );
    ```

-   Es wird jedoch empfohlen, dass Sie die Verwendung von **HRESULT** für unerwartete Fehler vermeiden, ist es wichtiger, auf die Verwendung der Ausnahmebehandlung zur Steuerung des Code zu vermeiden. Demzufolge wird bevorzugt, bei Bedarf einen **HRESULT**-Rückgabewert zu verwenden, um den Codefluss zu steuern.

###  <a name="sal-annotations"></a>SAL-Anmerkungen

Verwenden Sie SAL-Anmerkungen in Kombination mit Codeanalysetools, um Fehler in der App zu finden.

Mithilfe der Microsoft-Quellcodeanmerkungssprache (Source Code Annotation Language, SAL) können Sie anmerken bzw. beschreiben, wie eine Funktion die zugehörigen Parameter verwendet. SAL-Anmerkungen werden auch zum Beschreiben von Rückgabewerten verwendet. SAL-Anmerkungen können mit dem C/C++-Codeanalysetool verwendet werden, um mögliche Fehler im C- und C++-Quellcode zu finden. Häufige Codierungsfehler, die vom Tool gemeldet werden, beinhalten Pufferüberläufe, nicht initialisierte Speicher, Nullzeiger-Dereferenzierungen und Speicher- und Ressourcenverluste.

Berücksichtigen Sie die **basicloader:: Loadmesh** -Methode, die in [BasicLoader.h](https://github.com/Microsoft/Windows-appsample-marble-maze/blob/e62d68a85499e208d591d2caefbd9df62af86809/C%2B%2B/Shared/BasicLoader.h)deklariert wird. Diese Methode verwendet `_In_` an der *Dateiname* ist ein Eingabeparameter (und daher wird nur gelesen werden, aus), `_Out_` angeben, dass *VertexBuffer* und *IndexBuffer* Ausgabeparameter sind (und daher nur geschrieben wird) und `_Out_opt_` angeben, dass *VertexCount* und *IndexCount* optional sind Ausgabeparameter (und möglicherweise in geschrieben werden). Da *vertexCount* und *indexCount* optionale Ausgabeparameter sind, dürfen sie **nullptr** sein. Das C/C++-Codeanalysetool untersucht Aufrufe dieser Methode, um sicherzustellen, dass die von ihr übergebenen Parameter diese Kriterien erfüllen.

```cpp
void LoadMesh(
    _In_ Platform::String^ filename,
    _Out_ ID3D11Buffer** vertexBuffer,
    _Out_ ID3D11Buffer** indexBuffer,
    _Out_opt_ uint32* vertexCount,
    _Out_opt_ uint32* indexCount
    );
```

Wählen Sie zum Ausführen der Codeanalyse für Ihre app, auf der Menüleiste **Build > Codeanalyse für Lösung ausführen**. Weitere Informationen zur Codeanalyse finden Sie unter [Analysieren der C/C++-Codequalität mithilfe der Codeanalyse](https://docs.microsoft.com/visualstudio/code-quality/analyzing-c-cpp-code-quality-by-using-code-analysis).

Die vollständige Liste der verfügbaren Anmerkungen wird in sal.h definiert. Weitere Informationen finden Sie unter [SAL-Anmerkungen](https://docs.microsoft.com/cpp/c-runtime-library/sal-annotations).

## <a name="next-steps"></a>Nächste Schritte


Lesen Sie die Informationen unter [Marble Maze-Anwendungsstruktur](marble-maze-application-structure.md), um zu erfahren, wie der Marble Maze-Anwendungscode strukturiert ist und wodurch sich die Struktur einer DirectX-UWP-App von der einer herkömmlichen Desktopanwendung unterscheidet.

## <a name="related-topics"></a>Verwandte Themen


* [Marble Maze-Anwendungsstruktur](marble-maze-application-structure.md)
* [Entwickeln von Marble Maze, einem UWP-Spiel in C++ und DirectX](developing-marble-maze-a-windows-store-game-in-cpp-and-directx.md)

 

 




