---
author: msatranjr
title: Erstellen von Komponenten für Windows-Runtime in C++
description: Dieses Thema zeigt, wie Sie C++ / CX nach einer Windows-Runtime-Komponente erstellen, also eine Komponente, die von einer universellen Windows-app mit c#, Visual Basic, C++ oder Javascript erstellt aufgerufen werden kann.
ms.assetid: F7E06AA2-DCEC-427E-BD5D-9CA2A0ED2612
ms.author: misatran
ms.date: 05/14/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: b5515d0ed5dc6e200c7c4fc9a7785c993d4cab59
ms.sourcegitcommit: 72835733ec429a5deb6a11da4112336746e5e9cf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2018
ms.locfileid: "5168655"
---
# <a name="creating-windows-runtime-components-in-ccx"></a><span data-ttu-id="78a96-104">Erstellen von Komponenten für Windows-Runtime in C++/CX</span><span class="sxs-lookup"><span data-stu-id="78a96-104">Creating Windows Runtime Components in C++/CX</span></span>
> [!NOTE]
> <span data-ttu-id="78a96-105">In diesem Thema erhalten Sie Unterstützung bei der Verwaltung Ihrer C++/CX-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="78a96-105">This topic exists to help you maintain your C++/CX application.</span></span> <span data-ttu-id="78a96-106">Es wird jedoch empfohlen, dass Sie [C++/WinRT](../cpp-and-winrt-apis/intro-to-using-cpp-with-winrt.md) für neue Anwendungen nutzen.</span><span class="sxs-lookup"><span data-stu-id="78a96-106">But we recommend that you use [C++/WinRT](../cpp-and-winrt-apis/intro-to-using-cpp-with-winrt.md) for new applications.</span></span> <span data-ttu-id="78a96-107">C++/WinRT ist eine vollständig standardisierte, moderne C++17 Sprachprojektion für Windows-Runtime-(WinRT)-APIs, die als headerdateibasierte Bibliothek implementiert ist und Ihnen einen erstklassigen Zugriff auf die moderne Windows-API bietet.</span><span class="sxs-lookup"><span data-stu-id="78a96-107">C++/WinRT is an entirely standard modern C++17 language projection for Windows Runtime (WinRT) APIs, implemented as a header-file-based library, and designed to provide you with first-class access to the modern Windows API.</span></span> <span data-ttu-id="78a96-108">Informationen zum Erstellen einer Komponente für Windows-Runtime mit C++ / WinRT, finden Sie unter [Erstellen von Ereignissen in C++ / WinRT](../cpp-and-winrt-apis/author-events.md).</span><span class="sxs-lookup"><span data-stu-id="78a96-108">To learn how to create a Windows Runtime Component using C++/WinRT, see [Author events in C++/WinRT](../cpp-and-winrt-apis/author-events.md).</span></span>

<span data-ttu-id="78a96-109">Dieses Thema zeigt, wie Sie C++ / CX nach einer Windows-Runtime-Komponente erstellen, also eine Komponente, die von einer universellen Windows-app mit c#, Visual Basic, C++ oder Javascript erstellt aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="78a96-109">This topic shows how to use C++/CX to create a Windows Runtime component, which is a component that's callable from a Universal Windows app built using C#, Visual Basic, C++, or Javascript.</span></span>

<span data-ttu-id="78a96-110">Es gibt verschiedene Gründe für die Erstellung einer Komponente für Windows-Runtime.</span><span class="sxs-lookup"><span data-stu-id="78a96-110">There are several reasons for building a Windows Runtime component.</span></span>
- <span data-ttu-id="78a96-111">Um die Leistungsvorteile von C++ für komplexe oder rechenintensive Vorgänge zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="78a96-111">To get the performance advantage of C++ in complex or computationally intensive operations.</span></span>
- <span data-ttu-id="78a96-112">Um Code wiederzuverwenden, der bereits geschrieben und getestet wurde.</span><span class="sxs-lookup"><span data-stu-id="78a96-112">To reuse code that's already written and tested.</span></span>

<span data-ttu-id="78a96-113">Wenn Sie eine Projektmappe erstellen, die ein JavaScript- oder .NET-Projekt und ein Komponentenprojekt für Windows-Runtime enthält, werden die JavaScript-Projektdateien und die kompilierte DLL in ein Paket zusammengeführt, das Sie lokal im Simulator oder remote auf einem verbundenen Gerät debuggen können.</span><span class="sxs-lookup"><span data-stu-id="78a96-113">When you build a solution that contains a JavaScript or .NET project, and a Windows Runtime component project, the JavaScript project files and the compiled DLL are merged into one package, which you can debug locally in the simulator or remotely on a tethered device.</span></span> <span data-ttu-id="78a96-114">Sie können auch nur das Komponentenprojekt als Erweiterungs-SDK verteilen.</span><span class="sxs-lookup"><span data-stu-id="78a96-114">You can also distribute just the component project as an Extension SDK.</span></span> <span data-ttu-id="78a96-115">Weitere Informationen finden Sie unter [Erstellen eines Software Development Kit](https://msdn.microsoft.com/library/hh768146.aspx).</span><span class="sxs-lookup"><span data-stu-id="78a96-115">For more information, see [Creating a Software Development Kit](https://msdn.microsoft.com/library/hh768146.aspx).</span></span>

<span data-ttu-id="78a96-116">In der Regel, wenn Sie code Ihrer C++ / CX-Komponente, verwenden Sie die reguläre C++-Bibliothek und integrierte Typen außer an der Grenze abstrakte binäre Schnittstelle (ABI), in denen Sie Daten in und aus Code in einem anderen winmd-Paket übergeben.</span><span class="sxs-lookup"><span data-stu-id="78a96-116">In general, when you code your C++/CX component, use the regular C++ library and built-in types, except at the abstract binary interface (ABI) boundary where you are passing data to and from code in another .winmd package.</span></span> <span data-ttu-id="78a96-117">Verwenden Sie Windows-Runtime-Typen und die spezielle Syntax, C++ / CX zum Erstellen und Bearbeiten dieser Typen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="78a96-117">There, use Windows Runtime types and the special syntax that C++/CX supports for creating and manipulating those types.</span></span> <span data-ttu-id="78a96-118">Darüber hinaus in Ihrer C++ / CX programmiert haben, Typen wie Delegaten und implementieren Sie in JavaScript, Visual Basic, C++ oder C#-Ereignisse, die von der Komponente ausgelöst und verarbeitet werden können.</span><span class="sxs-lookup"><span data-stu-id="78a96-118">In addition, in your C++/CX code, use types such as delegate and event to implement events that can be raised from your component and handled in JavaScript, Visual Basic, C++, or C#.</span></span> <span data-ttu-id="78a96-119">Weitere Informationen zu C++ / CX-Syntax finden Sie unter [Visual C++-Programmiersprachenreferenz (C++ / CX)](https://msdn.microsoft.com/library/windows/apps/xaml/hh699871.aspx).</span><span class="sxs-lookup"><span data-stu-id="78a96-119">For more information about the C++/CX syntax, see [Visual C++ Language Reference (C++/CX)](https://msdn.microsoft.com/library/windows/apps/xaml/hh699871.aspx).</span></span>

## <a name="casing-and-naming-rules"></a><span data-ttu-id="78a96-120">Regeln für die Groß-/Kleinschreibung und die Benennung</span><span class="sxs-lookup"><span data-stu-id="78a96-120">Casing and naming rules</span></span>

### <a name="javascript"></a><span data-ttu-id="78a96-121">JavaScript</span><span class="sxs-lookup"><span data-stu-id="78a96-121">JavaScript</span></span>
<span data-ttu-id="78a96-122">In JavaScript muss die Groß-/Kleinschreibung beachtet werden.</span><span class="sxs-lookup"><span data-stu-id="78a96-122">JavaScript is case-sensitive.</span></span> <span data-ttu-id="78a96-123">Daher müssen Sie die folgenden Konventionen zur Groß-/Kleinschreibung einhalten:</span><span class="sxs-lookup"><span data-stu-id="78a96-123">Therefore, you must follow these casing conventions:</span></span>

-   <span data-ttu-id="78a96-124">Verwenden Sie die C++-Schreibweise, wenn Sie auf C++-Namespaces und -Klassen verweisen.</span><span class="sxs-lookup"><span data-stu-id="78a96-124">When you reference C++ namespaces and classes, use the same casing that's used on the C++ side.</span></span>
-   <span data-ttu-id="78a96-125">Verwenden Sie beim Aufrufen von Methoden die Kamelschreibweise, auch wenn der Methodenname in C++ großgeschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="78a96-125">When you call methods, use camel casing even if the method name is capitalized on the C++ side.</span></span> <span data-ttu-id="78a96-126">Beispielsweise muss die C++-Methode „GetDate()” aus JavaScript mit „getDate()” aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="78a96-126">For example, a C++ method GetDate() must be called from JavaScript as getDate().</span></span>
-   <span data-ttu-id="78a96-127">Ein aktivierbarer Klassenname und Namespacename darf keine UNICODE-Zeichen enthalten.</span><span class="sxs-lookup"><span data-stu-id="78a96-127">An activatable class name and namespace name can't contain UNICODE characters.</span></span>

### <a name="net"></a><span data-ttu-id="78a96-128">.NET</span><span class="sxs-lookup"><span data-stu-id="78a96-128">.NET</span></span>
<span data-ttu-id="78a96-129">Die .NET-Sprachen folgen ihren üblichen Regeln für die Groß-und Kleinschreibung.</span><span class="sxs-lookup"><span data-stu-id="78a96-129">The .NET languages follow their normal casing rules.</span></span>

## <a name="instantiating-the-object"></a><span data-ttu-id="78a96-130">Instanziieren des Objekts</span><span class="sxs-lookup"><span data-stu-id="78a96-130">Instantiating the object</span></span>
<span data-ttu-id="78a96-131">Nur Windows-Runtime-Typen können über die ABI-Grenze hinweg übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="78a96-131">Only Windows Runtime types can be passed across the ABI boundary.</span></span> <span data-ttu-id="78a96-132">Der Compiler löst einen Fehler aus, wenn die Komponente über einen Typ wie „std::wstring” als Rückgabetyp oder Parameter in einer öffentlichen Methode verfügt.</span><span class="sxs-lookup"><span data-stu-id="78a96-132">The compiler will raise an error if the component has a type like std::wstring as a return type or parameter in a public method.</span></span> <span data-ttu-id="78a96-133">Die Visual C++-komponentenerweiterungen (C++ / CX) integrierte Typen enthalten die üblichen skalare, wie Int und Double sowie deren Typedef-Entsprechungen int32, float64, und so weiter.</span><span class="sxs-lookup"><span data-stu-id="78a96-133">The Visual C++ component extensions (C++/CX) built-in types include the usual scalars such as int and double, and also their typedef equivalents int32, float64, and so on.</span></span> <span data-ttu-id="78a96-134">Weitere Informationen finden Sie unter [Typsystem (C++/CX)](https://msdn.microsoft.com/library/windows/apps/hh755822.aspx).</span><span class="sxs-lookup"><span data-stu-id="78a96-134">For more information, see [Type System (C++/CX)](https://msdn.microsoft.com/library/windows/apps/hh755822.aspx).</span></span>

```cpp
// ref class definition in C++
public ref class SampleRefClass sealed
{
    // Class members...

    // #include <valarray>
public:
    double LogCalc(double input)
    {
        // Use C++ standard library as usual.
        return std::log(input);
    }

};
```

```javascript
//Instantiation in JavaScript (requires "Add reference > Project reference")
var nativeObject = new CppComponent.SampleRefClass();
```

```csharp
//Call a method and display result in a XAML TextBlock
var num = nativeObject.LogCalc(21.5);
ResultText.Text = num.ToString();
```

## <a name="ccx-built-in-types-library-types-and-windows-runtime-types"></a><span data-ttu-id="78a96-135">C++ / CX integrierte Typen, Bibliothekstypen und Windows-Runtime-Typen</span><span class="sxs-lookup"><span data-stu-id="78a96-135">C++/CX built-in types, library types, and Windows Runtime types</span></span>
<span data-ttu-id="78a96-136">Eine aktivierbare Klassen (auch als Verweisklasse bezeichnet) kann in einer anderen Sprache, wie z.B. JavaScript, C# oder Visual Basic, instanziiert werden.</span><span class="sxs-lookup"><span data-stu-id="78a96-136">An activatable class (also known as a ref class) is one that can be instantiated from another language such as JavaScript, C# or Visual Basic.</span></span> <span data-ttu-id="78a96-137">Um von einer anderen Sprache verwendet werden zu können, muss eine Komponente mindestens eine aktivierbare Klasse enthalten.</span><span class="sxs-lookup"><span data-stu-id="78a96-137">To be consumable from another language, a component must contain at least one activatable class.</span></span>

<span data-ttu-id="78a96-138">Eine Komponente für Windows-Runtime kann mehrere öffentliche aktivierbare Klassen sowie zusätzliche Klassen enthalten, die der Komponente nur intern bekannt sind.</span><span class="sxs-lookup"><span data-stu-id="78a96-138">A Windows Runtime component can contain multiple public activatable classes as well as additional classes that are known only internally to the component.</span></span> <span data-ttu-id="78a96-139">Wenden Sie das Attribut [WebHostHidden](https://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.webhosthiddenattribute.aspx) zu C++ / CX-Typen, die nicht für JavaScript sichtbar sein sollen.</span><span class="sxs-lookup"><span data-stu-id="78a96-139">Apply the [WebHostHidden](https://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.webhosthiddenattribute.aspx) attribute to C++/CX types that are not intended to be visible to JavaScript.</span></span>

<span data-ttu-id="78a96-140">Alle öffentliche Klassen müssen sich im selben Stammnamespace befinden, der denselben Namen wie die Metadatendatei der Komponente hat.</span><span class="sxs-lookup"><span data-stu-id="78a96-140">All public classes must reside in the same root namespace which has the same name as the component metadata file.</span></span> <span data-ttu-id="78a96-141">Zum Beispiel kann eine Klasse mit dem Namen A.B.C.MyClass nur instanziiert werden, wenn sie in einer Metadatendatei mit dem Namen A.winmd oder A.B.winmd oder A.B.C.winmd definiert ist.</span><span class="sxs-lookup"><span data-stu-id="78a96-141">For example, a class that's named A.B.C.MyClass can be instantiated only if it's defined in a metadata file that's named A.winmd or A.B.winmd or A.B.C.winmd.</span></span> <span data-ttu-id="78a96-142">Der Name der DLL muss nicht mit dem Namen der WINMD-Datei übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="78a96-142">The name of the DLL is not required to match the .winmd file name.</span></span>

<span data-ttu-id="78a96-143">Clientcode erstellt eine Instanz der Komponente mit dem Schlüsselwort **new** (**New** in Visual Basic) so wie für jede andere Klasse auch.</span><span class="sxs-lookup"><span data-stu-id="78a96-143">Client code creates an instance of the component by using the **new** (**New** in Visual Basic) keyword just as for any class.</span></span>

<span data-ttu-id="78a96-144">Eine aktivierbare Klasse muss als **public ref class sealed** deklariert werden.</span><span class="sxs-lookup"><span data-stu-id="78a96-144">An activatable class must be declared as **public ref class sealed**.</span></span> <span data-ttu-id="78a96-145">Das Schlüsselwort **ref class** teilt dem Compiler mit, die Klasse als einen mit der Windows-Runtime kompatiblen Typ zu erstellen, und das Schlüsselwort „sealed” gibt an, dass die Klasse nicht vererbt werden kann.</span><span class="sxs-lookup"><span data-stu-id="78a96-145">The **ref class** keyword tells the compiler to create the class as a Windows Runtime compatible type, and the sealed keyword specifies that the class cannot be inherited.</span></span> <span data-ttu-id="78a96-146">Die Windows-Runtime unterstützt derzeit kein generalisiertes Vererbungsmodell; ein beschränktes Vererbungsmodell unterstützt die Erstellung von benutzerdefinierten XAML-Steuerelementen.</span><span class="sxs-lookup"><span data-stu-id="78a96-146">The Windows Runtime does not currently support a generalized inheritance model; a limited inheritance model supports creation of custom XAML controls.</span></span> <span data-ttu-id="78a96-147">Weitere Informationen finden Sie unter [Verweisklassen und Strukturen (C++/CX)](https://msdn.microsoft.com/library/windows/apps/xaml/hh699870.aspx).</span><span class="sxs-lookup"><span data-stu-id="78a96-147">For more information, see [Ref classes and structs (C++/CX)](https://msdn.microsoft.com/library/windows/apps/xaml/hh699870.aspx).</span></span>

<span data-ttu-id="78a96-148">Für C++ / CX, alle numerischen Grundtypen im Standardnamespace definiert sind.</span><span class="sxs-lookup"><span data-stu-id="78a96-148">For C++/CX, all the numeric primitives are defined in the default namespace.</span></span> <span data-ttu-id="78a96-149">Die [Plattform](https://msdn.microsoft.com/library/windows/apps/xaml/hh710417.aspx) -Namespace enthält C++ / CX-Klassen, die speziell für die Windows-Runtime-Typsystem.</span><span class="sxs-lookup"><span data-stu-id="78a96-149">The [Platform](https://msdn.microsoft.com/library/windows/apps/xaml/hh710417.aspx) namespace contains C++/CX classes that are specific to the Windows Runtime type system.</span></span> <span data-ttu-id="78a96-150">Dazu gehören die Klassen [Platform:: String](https://msdn.microsoft.com/library/windows/apps/xaml/hh755812.aspx) und [Platform::Object](https://msdn.microsoft.com/library/windows/apps/xaml/hh748265.aspx).</span><span class="sxs-lookup"><span data-stu-id="78a96-150">These include [Platform::String](https://msdn.microsoft.com/library/windows/apps/xaml/hh755812.aspx) class and [Platform::Object](https://msdn.microsoft.com/library/windows/apps/xaml/hh748265.aspx) class.</span></span> <span data-ttu-id="78a96-151">Die konkreten Sammlungstypen, wie die Klassen [Platform::Collections::Map](https://msdn.microsoft.com/library/windows/apps/xaml/hh441508.aspx) und [Platform::Collections::Vector](https://msdn.microsoft.com/library/windows/apps/xaml/hh441570.aspx), sind im Namespace [Platform::Collections](https://msdn.microsoft.com/library/windows/apps/xaml/hh710418.aspx) definiert.</span><span class="sxs-lookup"><span data-stu-id="78a96-151">The concrete collection types such as [Platform::Collections::Map](https://msdn.microsoft.com/library/windows/apps/xaml/hh441508.aspx) class and [Platform::Collections::Vector](https://msdn.microsoft.com/library/windows/apps/xaml/hh441570.aspx) class are defined in the [Platform::Collections](https://msdn.microsoft.com/library/windows/apps/xaml/hh710418.aspx) namespace.</span></span> <span data-ttu-id="78a96-152">Die öffentlichen Schnittstellen, die diese Typen implementieren, sind im [Windows::Foundation::Collections-Namespace (C++/CX)](https://msdn.microsoft.com/library/windows/apps/xaml/hh441496.aspx) definiert.</span><span class="sxs-lookup"><span data-stu-id="78a96-152">The public interfaces that these types implement are defined in [Windows::Foundation::Collections Namespace (C++/CX)](https://msdn.microsoft.com/library/windows/apps/xaml/hh441496.aspx).</span></span> <span data-ttu-id="78a96-153">Diese Schnittstellentypen werden von JavaScript, C# und Visual Basic verwendet.</span><span class="sxs-lookup"><span data-stu-id="78a96-153">It is these interface types that are consumed by JavaScript, C# and Visual Basic.</span></span> <span data-ttu-id="78a96-154">Weitere Informationen finden Sie unter [Typsystem (C++/CX)](https://msdn.microsoft.com/library/windows/apps/hh755822.aspx).</span><span class="sxs-lookup"><span data-stu-id="78a96-154">For more information, see [Type System (C++/CX)](https://msdn.microsoft.com/library/windows/apps/hh755822.aspx).</span></span>

## <a name="method-that-returns-a-value-of-built-in-type"></a><span data-ttu-id="78a96-155">Methode, die einen Wert mit einem integrierten Typ zurückgibt</span><span class="sxs-lookup"><span data-stu-id="78a96-155">Method that returns a value of built-in type</span></span>
```cpp
    // #include <valarray>
public:
    double LogCalc(double input)
    {
        // Use C++ standard library as usual.
        return std::log(input);
    }
```

```javascript
//Call a method
var nativeObject = new CppComponent.SampleRefClass;
var num = nativeObject.logCalc(21.5);
document.getElementById('P2').innerHTML = num;
```

## <a name="method-that-returns-a-custom-value-struct"></a><span data-ttu-id="78a96-156">Methode, die eine benutzerdefinierte Wertstruktur zurückgibt</span><span class="sxs-lookup"><span data-stu-id="78a96-156">Method that returns a custom value struct</span></span>
```cpp
namespace CppComponent
{
    // Custom struct
    public value struct PlayerData
    {
        Platform::String^ Name;
        int Number;
        double ScoringAverage;
    };

    public ref class Player sealed
    {
    private:
        PlayerData m_player;
    public:
        property PlayerData PlayerStats
        {
            PlayerData get(){ return m_player; }
            void set(PlayerData data) {m_player = data;}
        }
    };
}
```

<span data-ttu-id="78a96-157">Um benutzerdefinierte wertstrukturen über die ABI zu übergeben, definieren Sie ein JavaScript-Objekt, das die gleichen Member wie die wertstruktur verfügt, die in C++ definiert ist / CX.</span><span class="sxs-lookup"><span data-stu-id="78a96-157">To pass user-defined value structs across the ABI, define a JavaScript object that has the same members as the value struct that's defined in C++/CX.</span></span> <span data-ttu-id="78a96-158">Sie können dieses Objekt dann als Argument übergeben, an eine C++ / CX-Methode, damit das Objekt implizit in C++ konvertiert wird / CX-Typ.</span><span class="sxs-lookup"><span data-stu-id="78a96-158">You can then pass that object as an argument to a C++/CX method so that the object is implicitly converted to the C++/CX type.</span></span>

```javascript
// Get and set the value struct
function GetAndSetPlayerData() {
    // Create an object to pass to C++
    var myData =
        { name: "Bob Homer", number: 12, scoringAverage: .357 };
    var nativeObject = new CppComponent.Player();
    nativeObject.playerStats = myData;

    // Retrieve C++ value struct into new JavaScript object
    var myData2 = nativeObject.playerStats;
    document.getElementById('P3').innerHTML = myData.name + " , " + myData.number + " , " + myData.scoringAverage.toPrecision(3);
}
```

<span data-ttu-id="78a96-159">Ein anderer Ansatz besteht darin, eine Klasse zu definieren, die „IPropertySet” implementiert (nicht dargestellt).</span><span class="sxs-lookup"><span data-stu-id="78a96-159">Another approach is to define a class that implements IPropertySet (not shown).</span></span>

<span data-ttu-id="78a96-160">In den .NET-Sprachen erstellen Sie einfach eine Variable des Typs, die in C++ definiert / CX-Komponente.</span><span class="sxs-lookup"><span data-stu-id="78a96-160">In the .NET languages, you just create a variable of the type that's defined in the C++/CX component.</span></span>

```csharp
private void GetAndSetPlayerData()
{
    // Create a ref class
    var player = new CppComponent.Player();

    // Create a variable of a value struct
    // type that is defined in C++
    CppComponent.PlayerData myPlayer;
    myPlayer.Name = "Babe Ruth";
    myPlayer.Number = 12;
    myPlayer.ScoringAverage = .398;

    // Set the property
    player.PlayerStats = myPlayer;

    // Get the property and store it in a new variable
    CppComponent.PlayerData myPlayer2 = player.PlayerStats;
    ResultText.Text += myPlayer.Name + " , " + myPlayer.Number.ToString() +
        " , " + myPlayer.ScoringAverage.ToString();
}
```

## <a name="overloaded-methods"></a><span data-ttu-id="78a96-161">Überladene Methoden</span><span class="sxs-lookup"><span data-stu-id="78a96-161">Overloaded Methods</span></span>
<span data-ttu-id="78a96-162">Eine C++ / CX öffentliche Verweisklasse kann überladene Methoden enthalten, aber JavaScript verfügt nur über begrenzte Möglichkeiten zur Unterscheidung überladener Methoden.</span><span class="sxs-lookup"><span data-stu-id="78a96-162">A C++/CX public ref class can contain overloaded methods, but JavaScript has limited ability to differentiate overloaded methods.</span></span> <span data-ttu-id="78a96-163">Beispielsweise kann JavaScript den Unterschied zwischen diesen Signaturen erkennen:</span><span class="sxs-lookup"><span data-stu-id="78a96-163">For example, it can tell the difference between these signatures:</span></span>

```cpp
public ref class NumberClass sealed
{
public:
    int GetNumber(int i);
    int GetNumber(int i, Platform::String^ str);
    double GetNumber(int i, MyData^ d);
};
```

<span data-ttu-id="78a96-164">Aber den Unterschied zwischen diesen nicht:</span><span class="sxs-lookup"><span data-stu-id="78a96-164">But it can’t tell the difference between these:</span></span>

```cpp
int GetNumber(int i);
double GetNumber(double d);
```

<span data-ttu-id="78a96-165">In mehrdeutigen Fällen können Sie sicherstellen, dass JavaScript immer eine bestimmte Überladung aufruft, indem Sie der Methodensignatur in der Headerdatei das [Windows::Foundation::Metadata::DefaultOverload](https://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.defaultoverloadattribute.aspx)-Attribut hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="78a96-165">In ambiguous cases, you can ensure that JavaScript always calls a specific overload by applying the [Windows::Foundation::Metadata::DefaultOverload](https://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.defaultoverloadattribute.aspx) attribute to the method signature in the header file.</span></span>

<span data-ttu-id="78a96-166">Dieser JavaScript-Code ruft immer die attributierte Überladung auf:</span><span class="sxs-lookup"><span data-stu-id="78a96-166">This JavaScript always calls the attributed overload:</span></span>

```javascript
var nativeObject = new CppComponent.NumberClass();
var num = nativeObject.getNumber(9);
document.getElementById('P4').innerHTML = num;
```

## <a name="net"></a><span data-ttu-id="78a96-167">.NET</span><span class="sxs-lookup"><span data-stu-id="78a96-167">.NET</span></span>
<span data-ttu-id="78a96-168">Die .NET-Sprachen erkennen Überladungen in einer C++ / CX-Verweisklasse ebenso wie in jeder .NET Framework-Klasse.</span><span class="sxs-lookup"><span data-stu-id="78a96-168">The .NET languages recognize overloads in a C++/CX ref class just as in any .NET Framework class.</span></span>

## <a name="datetime"></a><span data-ttu-id="78a96-169">DateTime</span><span class="sxs-lookup"><span data-stu-id="78a96-169">DateTime</span></span>
<span data-ttu-id="78a96-170">In der Windows-Runtime ist ein [Windows::Foundation::DateTime](https://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx)-Objekt einfach eine 64-Bit-Ganzzahl mit Vorzeichen, die die Anzahl der 100-Nanosekunden-Intervalle vor oder nach dem 1.Januar 1601 darstellt.</span><span class="sxs-lookup"><span data-stu-id="78a96-170">In the Windows Runtime, a [Windows::Foundation::DateTime](https://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx) object is just a 64-bit signed integer that represents the number of 100-nanosecond intervals either before or after January 1, 1601.</span></span> <span data-ttu-id="78a96-171">Es gibt keine Methoden für ein Windows:Foundation::DateTime-Objekt.</span><span class="sxs-lookup"><span data-stu-id="78a96-171">There are no methods on a Windows:Foundation::DateTime object.</span></span> <span data-ttu-id="78a96-172">Jede Sprache stellt stattdessen DateTime in einer für diese Sprache systemeigenen Weise dar: als Date-Objekt in JavaScript und als System.DateTime- und System.DateTimeOffset-Typen in .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="78a96-172">Instead, each language projects the DateTime in the way that is native to that language: the Date object in JavaScript and the System.DateTime and System.DateTimeOffset types in the .NET Framework.</span></span>

```cpp
public  ref class MyDateClass sealed
{
public:
    property Windows::Foundation::DateTime TimeStamp;
    void SetTime(Windows::Foundation::DateTime dt)
    {
        auto cal = ref new Windows::Globalization::Calendar();
        cal->SetDateTime(dt);
        TimeStamp = cal->GetDateTime(); // or TimeStamp = dt;
    }
};
```

<span data-ttu-id="78a96-173">Wenn Sie einen DateTime-Wert übergeben, von C++ / CX an JavaScript, JavaScript als Date-Objekt akzeptiert und wird standardmäßig als Datumszeichenfolge Langform angezeigt.</span><span class="sxs-lookup"><span data-stu-id="78a96-173">When you pass a DateTime value from C++/CX to JavaScript, JavaScript accepts it as a Date object and displays it by default as a long-form date string.</span></span>

```javascript
function SetAndGetDate() {
    var nativeObject = new CppComponent.MyDateClass();

    var myDate = new Date(1956, 4, 21);
    nativeObject.setTime(myDate);

    var myDate2 = nativeObject.timeStamp;

    //prints long form date string
    document.getElementById('P5').innerHTML = myDate2;

}
```

<span data-ttu-id="78a96-174">Wenn eine .NET-Sprache einen System.DateTime-Wert übergibt, an eine C++ / CX-Komponente, die Methode akzeptiert ihn als ein Windows::Foundation::DateTime.</span><span class="sxs-lookup"><span data-stu-id="78a96-174">When a .NET language passes a System.DateTime to a C++/CX component, the method accepts it as a Windows::Foundation::DateTime.</span></span> <span data-ttu-id="78a96-175">Wenn die Komponente einen Windows::Foundation::DateTime-Wert an eine .NET Framework-Methode übergibt, akzeptiert die Framework-Methode ihn als DateTimeOffset.</span><span class="sxs-lookup"><span data-stu-id="78a96-175">When the component passes a Windows::Foundation::DateTime to a .NET Framework method, the Framework method accepts it as a DateTimeOffset.</span></span>

```csharp
private void DateTimeExample()
{
    // Pass a System.DateTime to a C++ method
    // that takes a Windows::Foundation::DateTime
    DateTime dt = DateTime.Now;
    var nativeObject = new CppComponent.MyDateClass();
    nativeObject.SetTime(dt);

    // Retrieve a Windows::Foundation::DateTime as a
    // System.DateTimeOffset
    DateTimeOffset myDate = nativeObject.TimeStamp;

    // Print the long-form date string
    ResultText.Text += myDate.ToString();
}
```

## <a name="collections-and-arrays"></a><span data-ttu-id="78a96-176">Sammlungen und Arrays</span><span class="sxs-lookup"><span data-stu-id="78a96-176">Collections and arrays</span></span>
<span data-ttu-id="78a96-177">Sammlungen werden immer über die ABI-Grenze hinweg als Handles an Windows-Runtime-Typen wie z.B. Windows::Foundation::Collections::IVector^ und Windows::Foundation::Collections::IMap^ übergeben.</span><span class="sxs-lookup"><span data-stu-id="78a96-177">Collections are always passed across the ABI boundary as handles to Windows Runtime types such as Windows::Foundation::Collections::IVector^ and Windows::Foundation::Collections::IMap^.</span></span> <span data-ttu-id="78a96-178">Wenn Sie beispielsweise ein Handle für Platform::Collections::Map zurückzugeben, wird er implizit in Windows::Foundation::Collections::IMap^ konvertiert.</span><span class="sxs-lookup"><span data-stu-id="78a96-178">For example, if you return a handle to a Platform::Collections::Map, it implicitly converts to a Windows::Foundation::Collections::IMap^.</span></span> <span data-ttu-id="78a96-179">Die Sammlungsschnittstellen werden in einem Namespace, der vom C + getrennt ist definiert / CX-Klassen, die die konkrete Implementierung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="78a96-179">The collection interfaces are defined in a namespace that's separate from the C++/CX classes that provide the concrete implementations.</span></span> <span data-ttu-id="78a96-180">JavaScript und .NET-Sprachen nutzen die Schnittstellen.</span><span class="sxs-lookup"><span data-stu-id="78a96-180">JavaScript and .NET languages consume the interfaces.</span></span> <span data-ttu-id="78a96-181">Weitere Informationen finden Sie unter [Sammlungen (C++/CX)](https://msdn.microsoft.com//library/windows/apps/hh700103.aspx) und [Array und WriteOnlyArray (C++/CX)](https://msdn.microsoft.com/library/windows/apps/hh700131.aspx).</span><span class="sxs-lookup"><span data-stu-id="78a96-181">For more information, see [Collections (C++/CX)](https://msdn.microsoft.com//library/windows/apps/hh700103.aspx) and [Array and WriteOnlyArray (C++/CX)](https://msdn.microsoft.com/library/windows/apps/hh700131.aspx).</span></span>

## <a name="passing-ivector"></a><span data-ttu-id="78a96-182">Übergeben von „IVector“</span><span class="sxs-lookup"><span data-stu-id="78a96-182">Passing IVector</span></span>
```cpp
// Windows::Foundation::Collections::IVector across the ABI.
//#include <algorithm>
//#include <collection.h>
Windows::Foundation::Collections::IVector<int>^ SortVector(Windows::Foundation::Collections::IVector<int>^ vec)
{
    std::sort(begin(vec), end(vec));
    return vec;
}
```

```javascript
var nativeObject = new CppComponent.CollectionExample();
// Call the method to sort an integer array
var inVector = [14, 12, 45, 89, 23];
var outVector = nativeObject.sortVector(inVector);
var result = "Sorted vector to array:";
for (var i = 0; i < outVector.length; i++)
{
    outVector[i];
    result += outVector[i].toString() + ",";
}
document.getElementById('P6').innerHTML = result;
```

<span data-ttu-id="78a96-183">In den .NET-Sprachen wird „IVector&lt;T&gt; ” als „IList&lt;T&gt;” betrachtet.</span><span class="sxs-lookup"><span data-stu-id="78a96-183">The .NET languages see IVector&lt;T&gt; as IList&lt;T&gt;.</span></span>

```csharp
private void SortListItems()
{
    IList<int> myList = new List<int>();
    myList.Add(5);
    myList.Add(9);
    myList.Add(17);
    myList.Add(2);

    var nativeObject = new CppComponent.CollectionExample();
    IList<int> mySortedList = nativeObject.SortVector(myList);

    foreach (var item in mySortedList)
    {
        ResultText.Text += " " + item.ToString();
    }
}
```

## <a name="passing-imap"></a><span data-ttu-id="78a96-184">Übergeben von „IMap“</span><span class="sxs-lookup"><span data-stu-id="78a96-184">Passing IMap</span></span>
```cpp
// #include <map>
//#include <collection.h>
Windows::Foundation::Collections::IMap<int, Platform::String^> ^GetMap(void)
{    
    Windows::Foundation::Collections::IMap<int, Platform::String^> ^ret =
        ref new Platform::Collections::Map<int, Platform::String^>;
    ret->Insert(1, "One ");
    ret->Insert(2, "Two ");
    ret->Insert(3, "Three ");
    ret->Insert(4, "Four ");
    ret->Insert(5, "Five ");
    return ret;
}
```

```javascript
// Call the method to get the map
var outputMap = nativeObject.getMap();
var mStr = "Map result:" + outputMap.lookup(1) + outputMap.lookup(2)
    + outputMap.lookup(3) + outputMap.lookup(4) + outputMap.lookup(5);
document.getElementById('P7').innerHTML = mStr;
```

<span data-ttu-id="78a96-185">In den .NET-Sprachen wird „IMap” als „IDictionary&lt;K, V&gt;” betrachtet.</span><span class="sxs-lookup"><span data-stu-id="78a96-185">The .NET languages see IMap and IDictionary&lt;K, V&gt;.</span></span>

```csharp
private void GetDictionary()
{
    var nativeObject = new CppComponent.CollectionExample();
    IDictionary<int, string> d = nativeObject.GetMap();
    ResultText.Text += d[2].ToString();
}
```

## <a name="properties"></a><span data-ttu-id="78a96-186">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="78a96-186">Properties</span></span>
<span data-ttu-id="78a96-187">Eine öffentliche Verweisklasse in C++ / CX-komponentenerweiterungen macht öffentliche Datenmember als Eigenschaften verfügbar, mit der Schlüsselworts "Property".</span><span class="sxs-lookup"><span data-stu-id="78a96-187">A public ref class in C++/CX component extensions exposes public data members as properties, by using the property keyword.</span></span> <span data-ttu-id="78a96-188">Das Konzept ist identisch mit .NET Framework-Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="78a96-188">The concept is identical to .NET Framework properties.</span></span> <span data-ttu-id="78a96-189">Eine triviale Eigenschaft ähnelt einem Datenmember, da ihre Funktionalität implizit ist.</span><span class="sxs-lookup"><span data-stu-id="78a96-189">A trivial property resembles a data member because its functionality is implicit.</span></span> <span data-ttu-id="78a96-190">Eine nicht triviale Eigenschaft verfügt über explizite Get- und Set-Accessoren und über eine benannte private Variable, die der „Sicherungsspeicher" für den Wert ist.</span><span class="sxs-lookup"><span data-stu-id="78a96-190">A non-trivial property has explicit get and set accessors and a named private variable that's the "backing store" for the value.</span></span> <span data-ttu-id="78a96-191">In diesem Beispiel ist die private Membervariable „\_propertyAValue” der Sicherungsspeicher für „PropertyA“.</span><span class="sxs-lookup"><span data-stu-id="78a96-191">In this example, the private member variable \_propertyAValue is the backing store for PropertyA.</span></span> <span data-ttu-id="78a96-192">Eine Eigenschaft kann ein Ereignis auslösen, wenn sich ihr Wert ändert, und eine Client-App kann sich für den Empfang dieses Ereignisses registrieren.</span><span class="sxs-lookup"><span data-stu-id="78a96-192">A property can fire an event when its value changes, and a client app can register to receive that event.</span></span>

```cpp
//Properties
public delegate void PropertyChangedHandler(Platform::Object^ sender, int arg);
public ref class PropertyExample  sealed
{
public:
    PropertyExample(){}

    // Event that is fired when PropertyA changes
    event PropertyChangedHandler^ PropertyChangedEvent;

    // Property that has custom setter/getter
    property int PropertyA
    {
        int get() { return m_propertyAValue; }
        void set(int propertyAValue)
        {
            if (propertyAValue != m_propertyAValue)
            {
                m_propertyAValue = propertyAValue;
                // Fire event. (See event example below.)
                PropertyChangedEvent(this, propertyAValue);
            }
        }
    }

    // Trivial get/set property that has a compiler-generated backing store.
    property Platform::String^ PropertyB;

private:
    // Backing store for propertyA.
    int m_propertyAValue;
};
```

```javascript
var nativeObject = new CppComponent.PropertyExample();
var propValue = nativeObject.propertyA;
document.getElementById('P8').innerHTML = propValue;

//Set the string property
nativeObject.propertyB = "What is the meaning of the universe?";
document.getElementById('P9').innerHTML += nativeObject.propertyB;
```

<span data-ttu-id="78a96-193">Die .NET-Sprachen greifen auf Eigenschaften für einen systemeigenen C++ / CX-Objekt nur genau so wie in einer .NET Framework-Objekt.</span><span class="sxs-lookup"><span data-stu-id="78a96-193">The .NET languages access properties on a native C++/CX object just as they would on a .NET Framework object.</span></span>

```csharp
private void GetAProperty()
{
    // Get the value of the integer property
    // Instantiate the C++ object
    var obj = new CppComponent.PropertyExample();

    // Get an integer property
    var propValue = obj.PropertyA;
    ResultText.Text += propValue.ToString();

    // Set a string property
    obj.PropertyB = " What is the meaning of the universe?";
    ResultText.Text += obj.PropertyB;

}
```

## <a name="delegates-and-events"></a><span data-ttu-id="78a96-194">Delegaten und Ereignisse</span><span class="sxs-lookup"><span data-stu-id="78a96-194">Delegates and events</span></span>
<span data-ttu-id="78a96-195">Ein Delegat ist ein Windows-Runtime-Typ, der ein Funktionsobjekt darstellt.</span><span class="sxs-lookup"><span data-stu-id="78a96-195">A delegate is a Windows Runtime type that represents a function object.</span></span> <span data-ttu-id="78a96-196">Sie können mit Delegaten in Verbindung mit Ereignissen, Rückrufen und asynchronen Methodenaufrufen eine Aktion festlegen, die zu einem späteren Zeitpunkt ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="78a96-196">You can use delegates in connection with events, callbacks, and asynchronous method calls to specify an action to be performed later.</span></span> <span data-ttu-id="78a96-197">Wie ein Funktionsobjekt bietet der Delegat Typsicherheit, indem dem Compiler ermöglicht wird, den Rückgabetyp und die Parametertypen der Funktion zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="78a96-197">Like a function object, the delegate provides type-safety by enabling the compiler to verify the return type and parameter types of the function.</span></span> <span data-ttu-id="78a96-198">Die Deklaration eines Delegaten ähnelt einer Funktionssignatur, die Implementierung ähnelt einer Klassendefinition und der Aufruf ähnelt einen Funktionsaufruf.</span><span class="sxs-lookup"><span data-stu-id="78a96-198">The declaration of a delegate resembles a function signature, the implementation resembles a class definition, and the invocation resembles a function invocation.</span></span>

## <a name="adding-an-event-listener"></a><span data-ttu-id="78a96-199">Hinzufügen eines Ereignislisteners</span><span class="sxs-lookup"><span data-stu-id="78a96-199">Adding an event listener</span></span>
<span data-ttu-id="78a96-200">Mit dem Schlüsselwort „event” können Sie einen öffentlichen Member eines bestimmten Delegattyps deklarieren.</span><span class="sxs-lookup"><span data-stu-id="78a96-200">You can use the event keyword to declare a public member of a specified delegate type.</span></span> <span data-ttu-id="78a96-201">Clientcode abonniert das Ereignis anhand der Standardmechanismen, die die jeweilige Sprache bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="78a96-201">Client code subscribes to the event by using the standard mechanisms that are provided in the particular language.</span></span>

```cpp
public:
    event SomeHandler^ someEvent;
```

<span data-ttu-id="78a96-202">In diesem Beispiel wird der gleiche C++-Code verwendet, wie im vorherigen Abschnitt „Eigenschaften".</span><span class="sxs-lookup"><span data-stu-id="78a96-202">This example uses the same C++ code as for the previous properties section.</span></span>

```javascript
function Button_Click() {
    var nativeObj = new CppComponent.PropertyExample();
    // Define an event handler method
    var singlecasthandler = function (ev) {
        document.getElementById('P10').innerHTML = "The button was clicked and the value is " + ev;
    };

    // Subscribe to the event
    nativeObj.onpropertychangedevent = singlecasthandler;

    // Set the value of the property and fire the event
    var propValue = 21;
    nativeObj.propertyA = 2 * propValue;

}
```

<span data-ttu-id="78a96-203">In den .NET-Sprachen entspricht das Abonnieren eines Ereignisses in einer C++-Komponente dem Abonnieren eines Ereignisses in einer .NET Framework-Klasse:</span><span class="sxs-lookup"><span data-stu-id="78a96-203">In the .NET languages, subscribing to an event in a C++ component is the same as subscribing to an event in a .NET Framework class:</span></span>

```csharp
//Subscribe to event and call method that causes it to be fired.
private void TestMethod()
{
    var objWithEvent = new CppComponent.PropertyExample();
    objWithEvent.PropertyChangedEvent += objWithEvent_PropertyChangedEvent;

    objWithEvent.PropertyA = 42;
}

//Event handler method
private void objWithEvent_PropertyChangedEvent(object __param0, int __param1)
{
    ResultText.Text = "the event was fired and the result is " +
         __param1.ToString();
}
```

## <a name="adding-multiple-event-listeners-for-one-event"></a><span data-ttu-id="78a96-204">Hinzufügen mehrere Ereignislistener für ein Ereignis</span><span class="sxs-lookup"><span data-stu-id="78a96-204">Adding multiple event listeners for one event</span></span>
<span data-ttu-id="78a96-205">JavaScript verfügt über eine addEventListener-Methode, mit der mehrere Handler ein einzelnes Ereignis abonnieren können.</span><span class="sxs-lookup"><span data-stu-id="78a96-205">JavaScript has an addEventListener method that enables multiple handlers to subscribe to a single event.</span></span>

```cpp
public delegate void SomeHandler(Platform::String^ str);

public ref class LangSample sealed
{
public:
    event SomeHandler^ someEvent;
    property Platform::String^ PropertyA;

    // Method that fires an event
    void FireEvent(Platform::String^ str)
    {
        someEvent(Platform::String::Concat(str, PropertyA->ToString()));
    }
    //...
};
```

```javascript
// Add two event handlers
var multicast1 = function (ev) {
    document.getElementById('P11').innerHTML = "Handler 1: " + ev.target;
};
var multicast2 = function (ev) {
    document.getElementById('P12').innerHTML = "Handler 2: " + ev.target;
};

var nativeObject = new CppComponent.LangSample();
//Subscribe to the same event
nativeObject.addEventListener("someevent", multicast1);
nativeObject.addEventListener("someevent", multicast2);

nativeObject.propertyA = "42";

// This method should fire an event
nativeObject.fireEvent("The answer is ");
```

<span data-ttu-id="78a96-206">In C# kann eine beliebige Anzahl von Ereignishandlern mit dem Operator += das Ereignis abonnieren, wie im vorherigen Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="78a96-206">In C#, any number of event handlers can subscribe to the event by using the += operator as shown in the previous example.</span></span>

## <a name="enums"></a><span data-ttu-id="78a96-207">Enumerationen</span><span class="sxs-lookup"><span data-stu-id="78a96-207">Enums</span></span>
<span data-ttu-id="78a96-208">Eine Windows-Runtime-Enumeration in C++ / CX wird deklariert, mit "öffentliche Klasse Enum"; Sie ähnelt eine Bereichsbezogene Enumeration in Standard-c++.</span><span class="sxs-lookup"><span data-stu-id="78a96-208">A Windows Runtime enum in C++/CX is declared by using public class enum; it resembles a scoped enum in standard C++.</span></span>

```cpp
public enum class Direction {North, South, East, West};

public ref class EnumExampleClass sealed
{
public:
    property Direction CurrentDirection
    {
        Direction  get(){return m_direction; }
    }

private:
    Direction m_direction;
};
```

<span data-ttu-id="78a96-209">Enumerationswerte werden übergeben zwischen C++ / CX und JavaScript als ganze Zahlen.</span><span class="sxs-lookup"><span data-stu-id="78a96-209">Enum values are passed between C++/CX and JavaScript as integers.</span></span> <span data-ttu-id="78a96-210">Sie können optional ein JavaScript-Objekt, das dieselben benannten Werte wie C++ enthält, deklarieren / CX-Enumeration und verwenden sie als folgt.</span><span class="sxs-lookup"><span data-stu-id="78a96-210">You can optionally declare a JavaScript object that contains the same named values as the C++/CX enum and use it as follows.</span></span>

```javascript
var Direction = { 0: "North", 1: "South", 2: "East", 3: "West" };
//. . .

var nativeObject = new CppComponent.EnumExampleClass();
var curDirection = nativeObject.currentDirection;
document.getElementById('P13').innerHTML =
Direction[curDirection];
```

<span data-ttu-id="78a96-211">C# und Visual Basic bieten Sprachunterstützung für Enumerationen.</span><span class="sxs-lookup"><span data-stu-id="78a96-211">Both C# and Visual Basic have language support for enums.</span></span> <span data-ttu-id="78a96-212">In diesen Sprachen wird eine öffentliche C++-Enumerationsklasse wie eine .NET Framework-Enumeration betrachtet.</span><span class="sxs-lookup"><span data-stu-id="78a96-212">These languages see a C++ public enum class just as they would see a .NET Framework enum.</span></span>

## <a name="asynchronous-methods"></a><span data-ttu-id="78a96-213">Asynchrone Methoden</span><span class="sxs-lookup"><span data-stu-id="78a96-213">Asynchronous methods</span></span>
<span data-ttu-id="78a96-214">Verwenden Sie die [task-Klasse (Concurrency Runtime)](https://msdn.microsoft.com/library/hh750113.aspx), um asynchrone Methoden zu nutzen, die von anderen Windows-Runtime-Objekten verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="78a96-214">To consume asynchronous methods that are exposed by other Windows Runtime objects, use the [task Class (Concurrency Runtime)](https://msdn.microsoft.com/library/hh750113.aspx).</span></span> <span data-ttu-id="78a96-215">Weitere Informationen finden Sie unter [Aufgabenparallelität (Concurrency Runtime)](https://msdn.microsoft.com/library/dd492427.aspx).</span><span class="sxs-lookup"><span data-stu-id="78a96-215">For more information, see and [Task Parallelism (Concurrency Runtime)](https://msdn.microsoft.com/library/dd492427.aspx).</span></span>

<span data-ttu-id="78a96-216">Zum Implementieren von asynchroner Methoden in C++ / CX verwenden Sie die [Create\_async](https://msdn.microsoft.com/library/hh750102.aspx) -Funktion, die in "ppltasks.h" definiert ist.</span><span class="sxs-lookup"><span data-stu-id="78a96-216">To implement asynchronous methods in C++/CX, use the [create\_async](https://msdn.microsoft.com/library/hh750102.aspx) function that's defined in ppltasks.h.</span></span> <span data-ttu-id="78a96-217">Weitere Informationen finden Sie unter [Erstellen asynchroner Vorgänge in C++ / CX für UWP-apps](https://msdn.microsoft.com/library/vstudio/hh750082.aspx).</span><span class="sxs-lookup"><span data-stu-id="78a96-217">For more information, see [Creating Asynchronous Operations in C++/CX for UWP apps](https://msdn.microsoft.com/library/vstudio/hh750082.aspx).</span></span> <span data-ttu-id="78a96-218">Ein Beispiel finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer einfachen Komponente für Windows-Runtime in C++ / CX und Aufrufen der Komponente über JavaScript oder C#-](walkthrough-creating-a-basic-windows-runtime-component-in-cpp-and-calling-it-from-javascript-or-csharp.md).</span><span class="sxs-lookup"><span data-stu-id="78a96-218">For an example, see [Walkthrough: Creating a basic Windows Runtime component in C++/CX and calling it from JavaScript or C#](walkthrough-creating-a-basic-windows-runtime-component-in-cpp-and-calling-it-from-javascript-or-csharp.md).</span></span> <span data-ttu-id="78a96-219">Die .NET-Sprachen verwenden C++ / CX asynchronen Methoden nur, wie eine asynchrone Methode, die in .NET Framework definiert ist.</span><span class="sxs-lookup"><span data-stu-id="78a96-219">The .NET languages consume C++/CX asynchronous methods just as they would any asynchronous method that's defined in the .NET Framework.</span></span>

## <a name="exceptions"></a><span data-ttu-id="78a96-220">Ausnahmen</span><span class="sxs-lookup"><span data-stu-id="78a96-220">Exceptions</span></span>
<span data-ttu-id="78a96-221">Sie können jeden Ausnahmetyp auslösen, der von der Windows-Runtime definiert ist.</span><span class="sxs-lookup"><span data-stu-id="78a96-221">You can throw any exception type that's defined by the Windows Runtime.</span></span> <span data-ttu-id="78a96-222">Sie können keine benutzerdefinierten Typen von einem Windows-Runtime-Ausnahmetyp ableiten.</span><span class="sxs-lookup"><span data-stu-id="78a96-222">You cannot derive custom types from any Windows Runtime exception type.</span></span> <span data-ttu-id="78a96-223">Allerdings können Sie eine COMException auslösen und ein benutzerdefiniertes HRESULT bereitstellen, auf das der Code, der die Ausnahme abfängt, zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="78a96-223">However, you can throw COMException and provide a custom HRESULT that can be accessed by the code that catches the exception.</span></span> <span data-ttu-id="78a96-224">Es gibt keine Möglichkeit, eine benutzerdefinierte Meldung in einer COMException anzugeben.</span><span class="sxs-lookup"><span data-stu-id="78a96-224">There's no way to specify a custom Message in a COMException.</span></span>

## <a name="debugging-tips"></a><span data-ttu-id="78a96-225">Tipps zum Debuggen</span><span class="sxs-lookup"><span data-stu-id="78a96-225">Debugging tips</span></span>
<span data-ttu-id="78a96-226">Beim Debuggen einer JavaScript-Lösung mit einer Komponenten-DLL können Sie den Debugger so einstellen, dass er das schrittweise Ausführen von Skripts oder das schrittweise Ausführen von systemeigenem Code in der Komponente, aber nicht beides gleichzeitig ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="78a96-226">When you debug a JavaScript solution that has a component DLL, you can set the debugger to enable either stepping through script, or stepping through native code in the component, but not both at the same time.</span></span> <span data-ttu-id="78a96-227">Um die Einstellung zu ändern, wählen Sie im Projektmappen-Explorer den JavaScript-Projektknoten aus und dann „Eigenschaften”, „Debuggen”, „Debuggertyp”.</span><span class="sxs-lookup"><span data-stu-id="78a96-227">To change the setting, select the JavaScript project node in Solution Explorer and then choose Properties, Debugging, Debugger Type.</span></span>

<span data-ttu-id="78a96-228">Achten Sie darauf, entsprechende Funktionen im Paket-Designer auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="78a96-228">Be sure to select appropriate capabilities in the package designer.</span></span> <span data-ttu-id="78a96-229">Wenn Sie zum Beispiel eine Bilddatei in der Bildbibliothek des Benutzers mit den Windows-Runtime-APIs öffnen möchten, müssen Sie das Kontrollkästchen „Bildbibliothek” im Bereich „Funktionen” des Manifest-Designers aktivieren.</span><span class="sxs-lookup"><span data-stu-id="78a96-229">For example, if you are attempting to open an image file in the user's Pictures library by using the Windows Runtime APIs, be sure to select the Pictures Library check box in the Capabilities pane of the manifest designer.</span></span>

<span data-ttu-id="78a96-230">Wenn der JavaScript-Code die öffentlichen Eigenschaften oder Methoden in der Komponente nicht zu erkennen scheint, stellen Sie sicher, dass Sie in JavaScript die Kamelschreibweise verwenden.</span><span class="sxs-lookup"><span data-stu-id="78a96-230">If your JavaScript code doesn't seem to be recognizing the public properties or methods in the component, make sure that in JavaScript you are using camel casing.</span></span> <span data-ttu-id="78a96-231">Beispielsweise wird die LogCalc c++ / CX-Methode muss als LogCalc in JavaScript darauf verwiesen werden.</span><span class="sxs-lookup"><span data-stu-id="78a96-231">For example, the LogCalc C++/CX method must be referenced as logCalc in JavaScript.</span></span>

<span data-ttu-id="78a96-232">Wenn Sie eine C++ entfernen / CX-Windows-Runtime-Komponentenprojekt aus einer Projektmappe entfernen, müssen Sie auch manuell den Projektverweis aus dem JavaScript-Projekt.</span><span class="sxs-lookup"><span data-stu-id="78a96-232">If you remove a C++/CX Windows Runtime component project from a solution, you must also manually remove the project reference from the JavaScript project.</span></span> <span data-ttu-id="78a96-233">Andernfalls werden nachfolgende Debug- oder Buildvorgänge verhindert.</span><span class="sxs-lookup"><span data-stu-id="78a96-233">Failure to do so prevents subsequent debug or build operations.</span></span> <span data-ttu-id="78a96-234">Bei Bedarf können Sie dann einen Assemblyverweis zur DLL-Datei hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="78a96-234">If necessary, you can then add an assembly reference to the DLL.</span></span>

## <a name="related-topics"></a><span data-ttu-id="78a96-235">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="78a96-235">Related topics</span></span>
* [<span data-ttu-id="78a96-236">Exemplarische Vorgehensweise: Erstellen einer einfachen Komponente für Windows-Runtime in C++ / CX und Aufrufen der Komponente über JavaScript oder C#</span><span class="sxs-lookup"><span data-stu-id="78a96-236">Walkthrough: Creating a basic Windows Runtime component in C++/CX and calling it from JavaScript or C#</span></span>](walkthrough-creating-a-basic-windows-runtime-component-in-cpp-and-calling-it-from-javascript-or-csharp.md)
