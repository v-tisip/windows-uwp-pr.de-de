---
title: Erstellen von Komponenten für Windows-Runtime in C# und Visual Basic
description: Ab .NET Framework4.5 können Sie mit verwaltetem Code eigene Windows-Runtime-Typen erstellen, die in einer Komponente für Windows-Runtime gepackt sind.
ms.assetid: A5672966-74DF-40AB-B01E-01E3FCD0AD7A
ms.date: 12/04/2018
ms.topic: article
dev_langs:
- csharp
- vb
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: b4f5a2de5c3fa5564b4e4389cfc0806fd5d2844f
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "8878261"
---
# <a name="creating-windows-runtime-components-in-c-and-visual-basic"></a>Erstellen von Komponenten für Windows-Runtime in C# und Visual Basic
Ab .NET Framework 4.5, können Sie verwalteten Code verwenden, um Ihre eigenen Windows-Runtime-Typen zu erstellen und diese in einer Komponente für Windows-Runtime-verpacken. Sie können Ihre Komponente in universelle Windows-Plattform (UWP)-apps verwenden, die in C++, JavaScript, Visual Basic oder c# geschrieben werden. In diesem Thema wird beschrieben, die Regeln zum Erstellen einer Komponente, und beschreibt einige Aspekte der .NET Framework-Unterstützung für die Windows-Runtime. Im Allgemeinen ist diese Unterstützung allen .NET Framework-Programmierern klar. Wenn Sie aber eine Komponente erstellen, die mit JavaScript oder C++ verwendet werden soll, müssen Sie auf die Unterschiede bei der Unterstützung der Windows-Runtime durch diese Sprachen achten.

Wenn Sie erstellen eine Komponente nur in UWP-apps, die in Visual Basic oder c# geschrieben werden, und die Komponente enthält keine UWP-Steuerelemente, klicken Sie dann mit der **Klassenbibliotheksvorlage** und anstelle von der **Komponente für Windows-Runtime** -Projektvorlage onsider in Microsoft Visual Studio. Eine einfache Klassenbibliothek weist weniger Einschränkungen auf.

## <a name="declaring-types-in-windows-runtime-components"></a>Deklarieren von Typen in Komponenten für Windows-Runtime

Intern können die Windows-Runtime-Typen in Ihrer Komponente alle .NET Framework-Funktionen verwenden, die in einer UWP-app zulässig ist. Weitere Informationen finden Sie unter [.NET für UWP-apps](https://msdn.microsoft.com/library/windows/apps/mt185501).

Extern können die Member Ihrer Typen nur Windows-Runtime-Typen für ihre Parameter und Rückgabewerte verfügbar machen. In der folgende Liste sind die Einschränkungen für .NET Framework-Typen, die aus einer Komponente für Windows-Runtime verfügbar gemacht werden.

- Die Felder, Parameter und Rückgabewerte aller öffentlichen Typen und Member in der Komponente müssen Windows-Runtime-Typen sein. Diese Einschränkung betrifft die Windows-Runtime-Typen, die sowie Typen zu erstellen, die von der Windows-Runtime bereitgestellt werden. Außerdem trifft sie auf einige .NET Framework-Typen zu. Die Aufnahme dieser Typen ist Teil der Unterstützung von .NET Framework bietet, um die natürliche Verwendung der Windows-Runtime in verwaltetem Code zu ermöglichen&mdash;Code bekannte .NET Framework-Typen anstelle der zugrunde liegenden Windows-Runtime-Typen verwenden angezeigt wird. Beispielsweise können Sie primitive .NET Framework-Typen wie **Int32** und **Double**, bestimmte grundlegenden Typen wie **DateTimeOffset** und **Uri**, und einige häufig verwendete generische Schnittstellentypen wie IEnumerable- **&lt;T &gt; ** (IEnumerable (Of T) in Visual Basic) und **IDictionary&lt;TKey, TValue&gt;**. Beachten Sie, dass die Typargumente dieser generischen Typen Windows-Runtime-Typen sein müssen. Dies wird in den Abschnitten [übergeben von Windows-Runtime-Typen an verwalteten Code](#passing-windows-runtime-types-to-managed-code) und [übergeben von verwalteten Typen an die Windows-Runtime](#passing-managed-types-to-the-windows-runtime), später in diesem Thema erläutert.

- Öffentliche Klassen und Schnittstellen können Methoden, Eigenschaften und Ereignisse enthalten. Sie können Delegaten für Ereignisse deklarieren oder verwenden Sie die **EventHandler&lt;T&gt; ** delegieren. Eine öffentliche Klasse oder Schnittstelle kann nicht:
    - generisch sein.
    - Eine Schnittstelle implementieren, die keine Windows-Runtime-Schnittstelle ist (Sie können eigene Windows-Runtime-Schnittstellen erstellen und implementieren sie).
    - Von Typen, die nicht in der Windows-Runtime, wie **System.Exception** und **System.EventArgs**abgeleitet.

- Alle öffentliche Typen müssen über einen Stammnamespace verfügen, der mit dem Assemblynamen übereinstimmt, und der Assemblyname darf nicht mit „Windows” beginnen.

    > **Tipp**. Standardmäßig entsprechen die Namespacenamen in Visual Studio-Projekten den Assemblynamen. In Visual Basic wird die Namespace-Anweisung für diesen Standardnamespace nicht im Code angezeigt.

- Öffentliche Strukturen können nur öffentliche Felder als Member enthalten, und diese Felder müssen Werttypen oder Zeichenfolgen sein.
- Öffentliche Klassen müssen **versiegelt** (**NotInheritable** in Visual Basic) sein. Wenn das Programmiermodell Polymorphie erfordert, können Sie eine öffentliche Schnittstelle erstellen und implementieren Sie diese Schnittstelle für die Klassen, die polymorph sein müssen.

## <a name="debugging-your-component"></a>Debuggen der Komponente

Wenn Ihre UWP-app und Ihre Komponente mit verwaltetem Code erstellt wurden, können Sie beide gleichzeitig Debuggen.

Wenn Sie Ihre Komponente als Teil einer UWP-app mit C++ testen, können Sie verwalteten und systemeigenen Code gleichzeitig Debuggen. Die Vorgabe ist nur systemeigener Code.

## <a name="to-debug-both-native-c-code-and-managed-code"></a>So debuggen Sie systemeigenen C++-Code und verwalteten Code
1.  Öffnen Sie das Kontextmenü für das Visual C++-Projekt, und wählen Sie **Eigenschaften** aus.
2.  Wählen Sie auf den Eigenschaftenseiten unter **Konfigurationseigenschaften** die Option **Debuggen** aus.
3.  Wählen Sie **Debuggertyp** aus, und ändern Sie dann in der Dropdownliste **Nur systemeigen** in **Gemischt (verwaltet und systemeigen)**. Klicken Sie auf **OK**.
4.  Legen Sie Haltepunkte im systemeigenen und verwalteten Code fest.

Wenn Sie Ihre Komponente als Teil einer UWP-app mit JavaScript testen, ist die Projektmappe standardmäßig im JavaScript-Debugmodus. In Visual Studio ist das gleichzeitige Debuggen von JavaScript und verwaltetem Code nicht möglich.

## <a name="to-debug-managed-code-instead-of-javascript"></a>So debuggen Sie verwalteten Code anstelle von JavaScript
1.  Öffnen Sie das Kontextmenü für das JavaScript-Projekt, und wählen Sie **Eigenschaften** aus.
2.  Wählen Sie auf den Eigenschaftenseiten unter **Konfigurationseigenschaften** die Option **Debuggen** aus.
3.  Wählen Sie **Debuggertyp** aus, und ändern Sie in der Dropdownliste **Nur Skript** in **Nur verwaltet**. Klicken Sie auf **OK**.
4.  Legen Sie Haltepunkte im verwaltetem Code fest, und debuggen Sie wie gewohnt.

## <a name="passing-windows-runtime-types-to-managed-code"></a>Übergeben von Windows-Runtime Typen an verwalteten Code
Wie bereits im Abschnitt [Deklarieren von Typen in Komponenten für Windows-Runtime-](#declaring-types-in-windows-runtime-components)erwähnt, können bestimmte .NET Framework-Typen in den Signaturen von Membern öffentlicher Klassen erscheinen. Dies ist Teil der Unterstützung, die .NET Framework bietet, um die natürliche Verwendung der Windows-Runtime in verwaltetem Code zu ermöglichen. Darin sind primitive Typen und einige Klassen und Schnittstellen enthalten. Wenn die Komponente über JavaScript oder C++-Code verwendet wird, ist es wichtig zu wissen, wie die .NET Framework-Typen an den Aufrufer angezeigt werden. Beispiele mit JavaScript finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer einfachen Komponente in C# oder Visual Basic und Aufrufen dieser Komponente über JavaScript](walkthrough-creating-a-simple-windows-runtime-component-and-calling-it-from-javascript.md). In diesem Abschnitt werden häufig verwendete Typen beschrieben.

In .NET Framework haben primitive Typen wie **Int32** -Struktur viele nützliche Eigenschaften und Methoden, z. B. die **TryParse** -Methode. Im Gegensatz dazu haben primitive Typen und Strukturen in der Windows-Runtime nur Felder. Wenn Sie diese Typen an verwalteten Code übergeben, verhalten sie sich wie .NET Framework-Typen, und Sie können die Eigenschaften und Methoden der .NET Framework-Typen wie gewohnt verwenden. Die folgende Liste fasst die Ersetzungen zusammen, die automatisch in der IDE vorgenommen werden:

-   Für die primitiven Windows-Runtime **Int32** **Int64**, **Single**, **Double**, **Boolean**, **String** (eine unveränderliche Sammlung von Unicode-Zeichen), **Enum**, **UInt32**, **UInt64**und **Guid **, verwenden Sie den Typ mit dem gleichen Namen im System-Namespace.
-   Verwenden Sie für **UInt8** **den Typ System.Byte**.
-   Verwenden Sie für **Char16** **den Typ System.Char**.
-   Verwenden Sie für die **IInspectable** -Schnittstelle **System.Object**.

Wenn c# oder Visual Basic ein Schlüsselwort für einen dieser Typen bereitstellt, können Sie stattdessen das Schlüsselwort verwenden.

Zusätzlich zu primitiven Typen erscheinen einige grundlegende, häufig verwendete Windows-Runtime-Typen in verwaltetem Code als ihre .NET Framework-Entsprechung. Nehmen wir beispielsweise an Ihren JavaScript-Code verwendet die **Windows.Foundation.Uri** -Klasse, und es auf ein C#- oder Visual Basic-Methode übergeben werden sollen. Entspricht der Typ im verwalteten Code ist die .NET Framework- **System.Uri** -Klasse, und das ist der Typ, der für den Methodenparameter verwendet. Sie können feststellen, wann ein Windows-Runtime-Typ als .NET Framework-Typ erscheint, da IntelliSense in Visual Studio den Windows-Runtime-Typ ausblendet, wenn Sie verwalteten Code schreiben und den entsprechenden .NET Framework-Typ anzeigt. (In der Regel haben beiden Typen den gleichen Namen. Beachten Sie jedoch, dass die **Windows.Foundation.DateTime** -Struktur in verwaltetem Code als **System.DateTimeOffset** und nicht als **System.DateTime**angezeigt wird.)

Für einige häufig verwendete Sammlungstypen erfolgt die Zuordnung zwischen den Schnittstellen, die von einem Windows-Runtime-Typ implementiert werden, und den Schnittstellen, die vom entsprechenden .NET Framework-Typ implementiert werden. Wie bei den bereits erwähnten Typen deklarieren Sie Parametertypen, indem Sie den .NET Framework-Typ verwenden. Dadurch werden bestimmte Unterschiede zwischen den Typen ausgeblendet, und das Schreiben von .NET Framework-Code wirkt natürlicher.

In der folgenden Tabelle sind die häufigsten dieser generischen Schnittstellentypen zusammen mit anderen allgemeinen Klassen- und Schnittstellenzuordnungen aufgeführt. Eine vollständige Liste der Windows-Runtime-Typen, die das .NET Framework zuordnet, finden Sie unter [.NET Framework-Zuordnungen von Windows-Runtime-Typen](net-framework-mappings-of-windows-runtime-types.md).

| Windows-Runtime                                  | .NET Framework                                    |
|-|-|
| IIterable&lt;T&gt;                               | IEnumerable&lt;T&gt;                              |
| IVector&lt;T&gt;                                 | IList&lt;T&gt;                                    |
| IVectorView&lt;T&gt;                             | IReadOnlyList&lt;T&gt;                            |
| IMap&lt;K, V&gt;                                 | IDictionary&lt;TKey, TValue&gt;                   |
| IMapView&lt;K, V&gt;                             | IReadOnlyDictionary&lt;TKey, TValue&gt;           |
| IKeyValuePair&lt;K, V&gt;                        | KeyValuePair&lt;TKey, TValue&gt;                  |
| IBindableIterable                                | IEnumerable                                       |
| IBindableVecinr                                  | IList                                             |
| Windows.UI.Xaml.Data.INotifyPropertyChanged      | System.ComponentModel.INotifyPropertyChanged      |
| Windows.UI.Xaml.Data.PropertyChangedEventHandler | System.ComponentModel.PropertyChangedEventHandler |
| Windows.UI.Xaml.Data.PropertyChangedEventArgs    | System.ComponentModel.PropertyChangedEventArgs    |

Wenn ein Typ mehrere Schnittstellen implementiert, können Sie jede Schnittstelle verwenden, die als Parametertyp oder Rückgabetyp eines Members implementiert wird. Angenommen, Sie übergeben oder zurückgeben können eine **Wörterbuch&lt;Int, String&gt; ** (**Dictionary (Of Integer, String)** in Visual Basic) als **IDictionary&lt;Int, String&gt;**, **IReadOnlyDictionary&lt;Int, String &gt; **, oder **IEnumerable&lt;System.Collections.Generic.KeyValuePair&lt;TKey, TValue&gt;**.

> [!IMPORTANT]
> JavaScript verwendet die Schnittstelle, die zuerst in der Liste der Schnittstellen angezeigt wird, die ein verwalteter Typ implementiert. Wenn Sie zurückkehren, z. B. **Wörterbuch&lt;Int, String&gt; ** an JavaScript-Code, sie wird als **IDictionary&lt;Int, String&gt; ** unabhängig davon, welche Schnittstelle Sie als Rückgabetyp angeben. Das bedeutet, dass die erste Schnittstelle Member enthalten muss, die in den nächsten Schnittstellen erscheinen, damit diese Member für JavaScript sichtbar sind.

In der Windows-Runtime **IMap&lt;K, V&gt; ** und **IMapView&lt;K, V&gt; ** werden mit IKeyValuePair durchlaufen. Wenn Sie diese an verwalteten Code übergeben, werden sie als **IDictionary&lt;TKey, TValue&gt; ** und **IReadOnlyDictionary&lt;TKey, TValue&gt;**, natürlich verwenden Sie **System.Collections.Generic.KeyValuePair&lt;TKey, TValue&gt; ** auflisten.

Die Darstellungsweise von Schnittstellen in verwaltetem Code wirkt sich auf die Darstellungsweise der Typen aus, die diese Schnittstellen implementieren. Die **PropertySet** -Klasse implementiert z. B. **IMap&lt;K, V&gt;**, die angezeigt wird, in verwaltetem Code als **IDictionary&lt;TKey, TValue&gt;**. **PropertySet** wird angezeigt, als ob sie implementiert **IDictionary&lt;TKey, TValue&gt; ** anstelle von **IMap&lt;K, V&gt;** in verwaltetem Code scheinbar eine **Add** -Methode vorhanden, die verhält, wie die **Add** -Methode in .NET Framework-Wörterbüchern. Es wird nicht angezeigt, haben Sie eine **Insert** -Methode. Sie finden dieses Beispiel im Thema [Exemplarische Vorgehensweise: Erstellen einer einfachen Komponente in c# oder Visual Basic und Aufrufen der Komponente über JavaScript](walkthrough-creating-a-simple-windows-runtime-component-and-calling-it-from-javascript.md).

## <a name="passing-managed-types-to-the-windows-runtime"></a>Übergeben von verwalteten Typen an die Windows-Runtime

Wie bereits im vorherigen Abschnitt erwähnt, können einige Windows-Runtime-Typen als .NET Framework-Typen in den Signaturen von Komponentenmembern oder in den Signaturen von Windows-Runtime-Membern erscheinen, wenn Sie sie in der IDE verwenden. Wenn Sie .NET Framework-Typen an diese Member übergeben oder als Rückgabewerte von Komponentenmembern verwenden, werden sie dem Code auf der anderen Seite als der entsprechende Windows-Runtime-Typ dargestellt. Sie finden einige Beispiele für die Auswirkungen beim Aufruf Ihrer Komponente in JavaScript im Abschnitt „Zurückgeben verwalteter Typen aus der Komponente” unter [Exemplarische Vorgehensweise: Erstellen einer einfachen Komponente in C# oder Visual Basic und Aufrufen dieser Komponente über JavaScript](walkthrough-creating-a-simple-windows-runtime-component-and-calling-it-from-javascript.md).

## <a name="overloaded-methods"></a>Überladene Methoden

In der Windows-Runtime können Methoden überladen werden. Wenn Sie mehrere Überladungen mit der gleichen Anzahl von Parametern deklarieren, müssen Sie das Attribut [**Windows.Foundation.Metadata.defaultoverloadattribute versehen wird**](/uwp/api/windows.foundation.metadata.defaultoverloadattribute) nur auf eine dieser Überladungen anwenden. Nur diese Überladung kann aus JavaScript aufgerufen werden. Im folgenden Code ist beispielsweise die Überladung, die **int** übernimmt (**Integer** in Visual Basic), die Standardüberladung.

```csharp
public string OverloadExample(string s)
{
    return s;
}

[Windows.Foundation.Metadata.DefaultOverload()]
public int OverloadExample(int x)
{
    return x;
}
```

```vb
Public Function OverloadExample(ByVal s As String) As String
    Return s
End Function

<Windows.Foundation.Metadata.DefaultOverload> _
Public Function OverloadExample(ByVal x As Integer) As Integer
    Return x
End Function
```

> [WICHTIGE] JavaScript können Sie einen beliebigen Wert zu **OverloadExample**übergeben und wandelt den Wert in den Typ, der durch den Parameter erforderlich ist. Sie können **OverloadExample** mit "Zweiundvierzig", "42" oder "42,3" aufrufen, aber alle diese Werte werden an die standardüberladung übergeben. Die standardüberladung im vorherigen Beispiel gibt 0, 42 bzw. 42 zurück.

Sie können keine Konstruktoren das **DefaultOverloadAttribut**-e-Mail-Attribut zuweisen. Alle Konstruktoren in einer Klasse müssen eine unterschiedliche Anzahl von Parametern aufweisen.

## <a name="implementing-istringable"></a>Implementieren von IStringable

Ab Windows 8.1 enthält die Windows-Runtime eine **IStringable** -Schnittstelle, deren einzige Methode, **IStringable.ToString**, grundlegende formatierungsunterstützung mit **Object.ToString**enthält. Wenn Sie **IStringable** in einem öffentlichen, verwalteten Typ implementieren möchten, die in einer Komponente für Windows-Runtime exportiert wird, gelten folgenden Einschränkungen:

-   Sie können die **IStringable** -Schnittstelle nur in einer "Klasse implementiert", z. B. den folgenden Code in c# definieren:

    ```cs
    public class NewClass : IStringable
    ```

    Oder in Visual Basic-Code:

    ```vb
    Public Class NewClass : Implements IStringable
    ```

-   Sie können keine **IStringable** in einer Schnittstelle implementieren.
-   Sie können einen Parameter vom Typ **IStringable**nicht deklarieren.
-   **IStringable** kann nicht der Rückgabetyp einer Methode, eine Eigenschaft oder ein Feld sein.
-   Sie können die **IStringable** -Implementierung von Basisklassen verbergen, indem Sie eine Methodendefinition wie folgt:

    ```cs
    public class NewClass : IStringable
    {
       public new string ToString()
       {
          return "New ToString in NewClass";
       }
    }
    ```

    Stattdessen muss die **IStringable.ToString** -Implementierung immer die Implementierung der Basisklasse überschreiben. Sie können eine **ToString** -Implementierung ausblenden, nur, indem sie für eine stark typisierte Klasseninstanz aufrufen.

> [!NOTE]
> Unter verschiedenen Bedingungen können Aufrufe von systemeigenem Code auf einen verwalteten Typ, der **IStringable** implementiert oder seine **ToString** -Implementierung verbirgt unerwartetem Verhalten führen.

## <a name="asynchronous-operations"></a>Asynchrone Vorgänge

Um eine asynchrone Methode in Ihrer Komponente zu implementieren, fügen Sie am Ende des Methodennamens "Async", und Zurückgeben eines Windows-Runtime-Schnittstellen, die asynchrone Aktionen oder Vorgänge repräsentieren: **IAsyncAction**, IAsyncActionWithProgress- **&lt; TProgress&gt;**, **IAsyncOperation&lt;TResult&gt;**, oder **IAsyncOperationWithProgress&lt;TResult, TProgress&gt;**.

Sie können die .NET Framework-Aufgaben (der [**Task**](/dotnet/api/system.threading.tasks.task) -Klasse und die generische [**Aufgabe&lt;TResult&gt; **](/dotnet/api/system.threading.tasks.task-1) Klasse) eine asynchrone Methode implementieren. Sie müssen eine Aufgabe zurückgeben, die einen laufenden Vorgang darstellt, z. B. eine Aufgabe, die von einer asynchronen Methode in c# oder Visual Basic geschrieben zurückgegeben wird, oder eine Aufgabe, die von der [**Task.Run**](/dotnet/api/system.threading.tasks.task.run) -Methode zurückgegeben wird. Wenn Sie für die Aufgabenerstellung einen Konstruktor verwenden, müssen Sie seine [Task.Start](/dotnet/api/system.threading.tasks.task.start)-Methode vor der Rückgabe aufrufen.

Eine Methode, die verwendet `await` (`Await` in Visual Basic) erfordert die `async` Schlüsselwort (`Async` in Visual Basic). Wenn Sie eine solche Methode aus einer Komponente für Windows-Runtime verfügbar machen, die `async` Schlüsselwort für den Delegaten, die an die **Run** -Methode übergeben.

Für asynchrone Aktionen und Vorgänge, die weder die Abbruch- noch die Fortschrittsberichterstattung unterstützen, können Sie mit der Erweiterungsmethode [WindowsRuntimeSystemExtensions.AsAsyncAction](https://msdn.microsoft.com/library/system.windowsruntimesystemextensions.asasyncaction.aspx) oder [AsAsyncOperation&lt;TResult&gt;](https://msdn.microsoft.com/library/hh779745.aspx) die Aufgabe in die entsprechende Schnittstelle umschließen. Der folgende Code implementiert z. B. eine asynchrone Methode, mit der **Task.Run&lt;TResult&gt; ** Methode, um eine Aufgabe zu starten. Die **AsAsyncOperation&lt;TResult&gt; ** Erweiterungsmethode gibt die Aufgabe als asynchronen Windows-Runtime-Vorgang zurück.

```csharp
public static IAsyncOperation<IList<string>> DownloadAsStringsAsync(string id)
{
    return Task.Run<IList<string>>(async () =>
    {
        var data = await DownloadDataAsync(id);
        return ExtractStrings(data);
    }).AsAsyncOperation();
}
```

```vb
Public Shared Function DownloadAsStringsAsync(ByVal id As String) _
     As IAsyncOperation(Of IList(Of String))

    Return Task.Run(Of IList(Of String))(
        Async Function()
            Dim data = Await DownloadDataAsync(id)
            Return ExtractStrings(data)
        End Function).AsAsyncOperation()
End Function
```

Der folgende JavaScript-Code zeigt, wie die Methode aufgerufen werden kann, mit einem [**WinJS.Promise**](https://msdn.microsoft.com/library/windows/apps/br211867.aspx) -Objekt. Die an die then-Methode übergebene Funktion wird ausgeführt, wenn der asynchrone Aufruf abgeschlossen ist. Der StringList-Parameter enthält die Liste der Zeichenfolgen, die von der **DownloadAsStringAsync** -Methode zurückgegeben wird, und die Funktion übernimmt Verarbeitung erforderlich ist.

```javascript
function asyncExample(id) {

    var result = SampleComponent.Example.downloadAsStringAsync(id).then(
        function (stringList) {
            // Place code that uses the returned list of strings here.
        });
}
```

Verwenden Sie für asynchrone Aktionen und Vorgänge, die Abbruch- oder Fortschrittsberichterstattung unterstützen, [**AsyncInfo**](/dotnet/api/system.runtime.interopservices.windowsruntime) -Klasse, um eine gestartete Aufgabe zu generieren und die Abbruch-und fortschrittsberichterstattungsfunktionen der Aufgabe mit den Abbruch- und Status zu verknüpfen Funktionen zur Erstellung der entsprechenden Windows-Runtime-Schnittstelle. Ein Beispiel, das sowohl die Abbruch- als auch die Fortschrittsberichterstattung unterstützt, finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer einfachen Komponente in C# oder Visual Basic und Aufrufen dieser Komponente über JavaScript](walkthrough-creating-a-simple-windows-runtime-component-and-calling-it-from-javascript.md).

Beachten Sie, dass Sie die Methoden der **AsyncInfo** -Klasse verwenden können, auch wenn die asynchrone Methode nicht Abbruch oder Fortschrittsberichterstattung unterstützt. Wenn Sie eine Visual Basic-Lambda-Funktion oder eine anonyme C#-Methode verwenden, geben Sie keine Parameter für das Token und [**IProgress&lt;T&gt; **](https://msdn.microsoft.com/library/hh138298.aspx) Schnittstelle. Wenn Sie eine C#-Lambda-Funktion verwenden, geben Sie einen Tokenparameter an, aber ignorieren Sie ihn. Die vorherigen Beispiel, in dem die asasyncoperation&lt;TResult&gt; Methode sieht wie folgt aus, bei der Verwendung der [**AsyncInfo.Run&lt;TResult&gt;(Func&lt;CancellationToken, Task&lt;TResult&gt;**](https://msdn.microsoft.com/library/hh779740.aspx))-Methode stattdessen die Überladung.

```csharp
public static IAsyncOperation<IList<string>> DownloadAsStringsAsync(string id)
{
    return AsyncInfo.Run<IList<string>>(async (token) =>
    {
        var data = await DownloadDataAsync(id);
        return ExtractStrings(data);
    });
}
```

```vb
Public Shared Function DownloadAsStringsAsync(ByVal id As String) _
    As IAsyncOperation(Of IList(Of String))

    Return AsyncInfo.Run(Of IList(Of String))(
        Async Function()
            Dim data = Await DownloadDataAsync(id)
            Return ExtractStrings(data)
        End Function)
End Function
```

Wenn Sie eine asynchrone Methode, die optional die Abbruch- oder Fortschrittsberichterstattung unterstützt erstellen, sollten Sie die Überladung, die Parameter für ein Abbruchtoken hinzufügen oder die **IProgress&lt;T&gt; ** Schnittstelle.

## <a name="throwing-exceptions"></a>Auslösen von Ausnahmen

Sie können jeden Ausnahmetyp auslösen, der in .NET für Windows-Apps enthalten ist. Sie können keine eigenen öffentlichen Ausnahmetypen in einer Komponente für Windows-Runtime deklarieren, aber Sie können nicht öffentliche Typen deklarieren und auslösen.

Wenn die Komponente die Ausnahme nicht behandelt, wird eine entsprechende Ausnahme im Code ausgelöst, der die Komponente aufgerufen hat. Die Unterstützung der Windows-Runtime durch die aufrufende Sprache bestimmt, wie die Ausnahme dem Aufrufer dargestellt wird.

-   In JavaScript erscheint die Ausnahme als Objekt, in dem die Ausnahmemeldung durch eine Stapelüberwachung ersetzt ist. Wenn Sie Ihre App in Visual Studio debuggen, wird der Originaltext der Meldung im Ausnahmedialogfeld des Debuggers unter „WinRT Information" angezeigt. Sie können mit JavaScript-Code nicht auf den Originaltext der Meldung zugreifen.

    > **Tipp**.Momentan enthält die Stapelüberwachung zwar den verwalteten Ausnahmetyp, aber es ist nicht empfehlenswert, diese zu untersuchen, um den Ausnahmetyp zu ermitteln. Verwenden Sie stattdessen einen HRESULT-Wert, wie weiter unten in diesem Abschnitt beschrieben.

-   In C++ erscheint die Ausnahme als Plattformausnahme. Wenn der verwalteten Ausnahme HResult-Eigenschaft auf das Ergebnis der einer bestimmten plattformausnahme zugeordnet werden kann, wird die jeweiligen Ausnahme verwendet. Andernfalls wird eine [**Platform:: COMException**](https://msdn.microsoft.com/library/windows/apps/xaml/hh710414.aspx) -Ausnahme ausgelöst. Der Meldungstext der verwalteten Ausnahme ist für C++-Code nicht verfügbar. Wenn eine bestimmte Plattformausnahme ausgelöst wurde, erscheint der Meldungstext für diesen Ausnahmetyp. Andernfalls wird kein Meldungstext ausgegeben. Siehe [Ausnahmen (C++/CX)](https://msdn.microsoft.com/library/windows/apps/xaml/hh699896.aspx).
-   In C# oder Visual Basic ist die Ausnahme eine normale verwaltete Ausnahme.

Wenn Sie in Ihrer Komponente eine Ausnahme auslösen, sollten Sie einen nicht öffentlichen Ausnahmetyp verwenden, dessen HResult-Eigenschaftswert speziell für Ihre Komponente gilt, damit die Ausnahme leichter von einem JavaScript- oder C++-Aufrufer verwaltet werden kann. Das Ergebnis ist für einen JavaScript-Aufrufer über die Eigenschaft des Ausnahmeobjekts Anzahl, und ein C++-Aufrufer über die Eigenschaft [**COMException**](https://msdn.microsoft.com/library/windows/apps/xaml/hh710415.aspx) verfügbar.

> [!NOTE]
> Verwenden Sie einen negativen Wert für HRESULT. Ein positiver Wert wird als Erfolg interpretiert und im JavaScript- oder C++-Aufrufer wird keine Ausnahme ausgelöst.

## <a name="declaring-and-raising-events"></a>Deklarieren und Auslösen von Ereignissen

Wenn Sie einen Typ deklarieren, um die Daten für das Ereignis aufzunehmen, leiten Sie diesen von „Object“ und nicht von „EventArgs“ ab, da „EventArgs“ kein Windows-Runtime-Typ ist. Verwenden Sie [**EventHandler&lt;TEventArgs&gt; **](https://msdn.microsoft.com/library/db0etb8x.aspx) als Typ des Ereignisses, und verwenden Sie den Ereignisargumenttyp als generisches Typargument. Lösen Sie das Ereignis genauso wie in einer .NET Framework-Anwendung aus.

Wenn Ihre Komponente für Windows-Runtime von JavaScript oder C++ verwendet wird, folgt das Ereignis dem Windows-Runtime-Ereignismuster, das diese Sprachen erwarten. Wenn Sie die Komponente in C# oder Visual Basic verwenden, erscheint das Ereignis als normales .NET Framework-Ereignis. Ein Beispiel finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer einfachen Komponente in C# oder Visual Basic und Aufrufen dieser Komponente über JavaScript]().

Wenn Sie benutzerdefinierte Ereignisaccessoren implementieren (in Visual Basic ein Ereignis mit dem Schlüsselwort **Custom** deklarieren), müssen Sie in der Implementierung das Windows-Runtime-Ereignismuster verwenden. Siehe [Benutzerdefinierte Ereignisse und Ereignisaccessoren in Komponenten für Windows-Runtime](custom-events-and-event-accessors-in-windows-runtime-components.md). Beachten Sie, dass das Ereignis auch dann als einfaches .NET Framework-Ereignis erscheint, wenn Sie C#- oder Visual Basic-Code verwenden.

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie eine Komponente für Windows-Runtime für eigene Zwecke erstellt haben, stellen Sie möglicherweise fest, dass die Funktionen, die diese kapselt, für andere Entwickler nützlich sind. Sie haben zwei Optionen, um eine Komponente für die Verteilung an andere Entwickler zu packen. Siehe [Verteilen einer verwalteten Komponente für Windows-Runtime](https://msdn.microsoft.com/library/jj614475.aspx).

Weitere Informationen zu Visual Basic- und C#-Sprachfunktionen und zur .NET Framework-Unterstützung für die Windows-Runtime finden Sie unter [Visual Basic- und C#-Programmiersprachenreferenz](https://msdn.microsoft.com/library/windows/apps/xaml/br212458.aspx).

## <a name="related-topics"></a>Verwandte Themen
* [.NET für UWP-Apps](https://msdn.microsoft.com/library/windows/apps/mt185501)
* [Exemplarische Vorgehensweise: Erstellen einer einfachen Komponente für Windows-Runtime und Aufrufen der Komponente über JavaScript](walkthrough-creating-a-simple-windows-runtime-component-and-calling-it-from-javascript.md)
