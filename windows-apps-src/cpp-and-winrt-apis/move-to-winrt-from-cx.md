---
author: stevewhims
description: In diesem Thema wird gezeigt, wie Sie C++/CX-Code zum entsprechenden Äquivalent in C++/WinRT portieren.
title: Wechsel zu C++/WinRT von C++/CX
ms.author: stwhi
ms.date: 10/18/2018
ms.topic: article
keywords: windows 10, uwp, standard, c++, cpp, winrt, projizierung, portieren, migrieren, C++/CX
ms.localizationpriority: medium
ms.openlocfilehash: 35fe84747624c9a855df5520322546b83772379b
ms.sourcegitcommit: ca96031debe1e76d4501621a7680079244ef1c60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2018
ms.locfileid: "5815375"
---
# <a name="move-to-cwinrt-from-ccx"></a><span data-ttu-id="d5900-104">C++/CX zu C++/WinRT wechseln</span><span class="sxs-lookup"><span data-stu-id="d5900-104">Move to C++/WinRT from C++/CX</span></span>

<span data-ttu-id="d5900-105">Dieses Thema zeigt, wie Sie den Code in Portieren einer [C++ / CX](/cpp/cppcx/visual-c-language-reference-c-cx) Projekt zum entsprechenden Äquivalent in [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).</span><span class="sxs-lookup"><span data-stu-id="d5900-105">This topic shows how to port the code in a [C++/CX](/cpp/cppcx/visual-c-language-reference-c-cx) project to its equivalent in [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).</span></span>

## <a name="porting-strategies"></a><span data-ttu-id="d5900-106">Portieren von Strategien</span><span class="sxs-lookup"><span data-stu-id="d5900-106">Porting strategies</span></span>

<span data-ttu-id="d5900-107">Wenn Sie Ihre C++ schrittweise portieren möchten / CX-Code in C++ / WinRT, können Sie.</span><span class="sxs-lookup"><span data-stu-id="d5900-107">If you want to gradually port your C++/CX code to C++/WinRT, then you can.</span></span> <span data-ttu-id="d5900-108">C++ / CX- und C++ / WinRT-Code kann gleichzeitig im selben Projekt, mit Ausnahme der XAML-Compiler-Unterstützung und Komponenten für Windows-Runtime verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="d5900-108">C++/CX and C++/WinRT code can coexist in the same project, with the exceptions of XAML compiler support and Windows Runtime Components.</span></span> <span data-ttu-id="d5900-109">Für diese zwei Ausnahmen, müssen Sie in der Zielgruppe entweder C++ / CX oder C++ / WinRT im selben Projekt.</span><span class="sxs-lookup"><span data-stu-id="d5900-109">For those two exceptions, you'll need to target either C++/CX or C++/WinRT within the same project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d5900-110">Wenn Ihr Projekt eine XAML-Anwendung erstellt wird, dann einen Workflow, deren empfohlen wird, zunächst ein neues Projekt in Visual Studio mit einer von C++ erstellen / WinRT-Projektvorlagen (siehe [Visual Studio-Unterstützung für C++ / WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix)).</span><span class="sxs-lookup"><span data-stu-id="d5900-110">If your project builds a XAML application, then one workflow that we recommend is to first create a new project in Visual Studio using one of the C++/WinRT project templates (see [Visual Studio support for C++/WinRT, and the VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix)).</span></span> <span data-ttu-id="d5900-111">Starten Sie anschließend auf Kopieren Source Code und Markup über von C++ / CX-Projekt.</span><span class="sxs-lookup"><span data-stu-id="d5900-111">Then, start copying source code and markup over from the C++/CX project.</span></span> <span data-ttu-id="d5900-112">Sie können neue XAML-Seiten mit **Projekt**hinzufügen \> **Neues Element hinzufügen**  \>  **Visual C++** > **leere Seite (C++ / WinRT)**.</span><span class="sxs-lookup"><span data-stu-id="d5900-112">You can add new XAML pages with **Project** \> **Add New Item...** \> **Visual C++** > **Blank Page (C++/WinRT)**.</span></span>
>
> <span data-ttu-id="d5900-113">Alternativ können Sie einer Komponente für Windows-Runtime-Faktor-Code aus dem XAML-C++ / CX projizieren, wie Sie es portieren.</span><span class="sxs-lookup"><span data-stu-id="d5900-113">Alternatively, you can use a Windows Runtime Component to factor code out of the XAML C++/CX project as you port it.</span></span> <span data-ttu-id="d5900-114">Entweder bewegen Sie so viel C++ / CX-code wie möglich in einer Komponente, und ändern Sie dann das XAML-Projekt in C++ / WinRT.</span><span class="sxs-lookup"><span data-stu-id="d5900-114">Either move as much C++/CX code as you can into a component, and then change the XAML project to C++/WinRT.</span></span> <span data-ttu-id="d5900-115">Oder lassen Sie andernfalls das XAML-Projekt als C++ / CX, erstellen Sie eine neue C++ / WinRT-Komponente, und beginnen Sie Portieren von C++ / CX-Code aus dem XAML-Projekt und in der Komponente.</span><span class="sxs-lookup"><span data-stu-id="d5900-115">Or else leave the XAML project as C++/CX, create a new C++/WinRT component, and begin porting C++/CX code out of the XAML project and into the component.</span></span> <span data-ttu-id="d5900-116">Sie haben könnte auch eine C++ / CX-Komponentenprojekt zusammen mit C++ / WinRT-Komponentenprojekt innerhalb der gleichen Projektmappe verweisen auf beide Eigenschaften aus Ihrem Anwendungsprojekt und schrittweise aus einem anderen port.</span><span class="sxs-lookup"><span data-stu-id="d5900-116">You could also have a C++/CX component project alongside a C++/WinRT component project within the same solution, reference both of them from your application project, and gradually port from one to the other.</span></span> <span data-ttu-id="d5900-117">Finden Sie unter [Interoperabilität zwischen C++ / WinRT und C++ / CX](interop-winrt-cx.md) für Weitere Informationen zur Verwendung der beiden sprachprojektionen im selben Projekt.</span><span class="sxs-lookup"><span data-stu-id="d5900-117">See [Interop between C++/WinRT and C++/CX](interop-winrt-cx.md) for more details on using the two language projections in the same project.</span></span>

> [!NOTE]
> <span data-ttu-id="d5900-118">Sowohl [C++/CX ](/cpp/cppcx/visual-c-language-reference-c-cx) als auch das Windows SDK deklarieren Typen im Root-Namespace **Windows**.</span><span class="sxs-lookup"><span data-stu-id="d5900-118">Both [C++/CX](/cpp/cppcx/visual-c-language-reference-c-cx) and the Windows SDK declare types in the root namespace **Windows**.</span></span> <span data-ttu-id="d5900-119">Ein Windows-Typ, der in C++/WinRT projiziert wird, verfügt über den gleichen vollqualifizierten Namen wie der Windows-Typ, befindet sich aber im C++/**winrt**-Namespace.</span><span class="sxs-lookup"><span data-stu-id="d5900-119">A Windows type projected into C++/WinRT has the same fully-qualified name as the Windows type, but it's placed in the C++ **winrt** namespace.</span></span> <span data-ttu-id="d5900-120">Diese unterschiedlichen Namespaces ermöglichen die Portierung von C++/CX nach C++/WinRT in Ihrem eigenen Tempo.</span><span class="sxs-lookup"><span data-stu-id="d5900-120">These distinct namespaces let you port from C++/CX to C++/WinRT at your own pace.</span></span>

<span data-ttu-id="d5900-121">Unter Berücksichtigung der oben genannten Ausnahmen, das erste Schritt beim Portieren eine C++ / CX-Projekts zu C++ / WinRT ist C++ manuell hinzufügen / WinRT-Unterstützung es (finden Sie unter [Visual Studio-Unterstützung für C++ / WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix)).</span><span class="sxs-lookup"><span data-stu-id="d5900-121">Bearing in mind the exceptions mentioned above, the first step in porting a C++/CX project to C++/WinRT is to manually add C++/WinRT support to it (see [Visual Studio support for C++/WinRT, and the VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix)).</span></span> <span data-ttu-id="d5900-122">Bearbeiten Sie dazu Ihre `.vcxproj`-Datei, suchen Sie nach `<PropertyGroup Label="Globals">`, und definieren Sie innerhalb dieser Eigenschaftengruppe die Eigenschaft `<CppWinRTEnabled>true</CppWinRTEnabled>`.</span><span class="sxs-lookup"><span data-stu-id="d5900-122">To do that, edit your `.vcxproj` file, find `<PropertyGroup Label="Globals">` and, inside that property group, set the property `<CppWinRTEnabled>true</CppWinRTEnabled>`.</span></span> <span data-ttu-id="d5900-123">Eine Auswirkung dieser Änderung ist, dass die Unterstützung für C++/CX im Projekt deaktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="d5900-123">One effect of that change is that support for C++/CX is turned off in the project.</span></span> <span data-ttu-id="d5900-124">Es ist sinnvoll, lassen Sie Unterstützung deaktiviert, so dass Build Nachrichten Sie suchen (und Port) unterstützen alle Ihre Abhängigkeiten auf C++ / CX, oder Sie können Unterstützung wieder aktivieren (in den Projekteigenschaften, **C/C++-** \> **Allgemeine** \> **verbrauchen Windows-Runtime Erweiterung** \> **Ja (/ Zw)**), und nach und nach portieren.</span><span class="sxs-lookup"><span data-stu-id="d5900-124">It's a good idea to leave support turned off so that build messages help you find (and port) all of your dependencies on C++/CX, or you can turn support back on (in project properties, **C/C++** \> **General** \> **Consume Windows Runtime Extension** \> **Yes (/ZW)**), and port gradually.</span></span>

<span data-ttu-id="d5900-125">Stellen Sie sicher, **Allgemeine**Projekteigenschaft \> **Zielplattformversion** mit 10.0.17134.0 (Windows 10, Version 1803) festgelegt ist oder größer.</span><span class="sxs-lookup"><span data-stu-id="d5900-125">Ensure that project property **General** \> **Target Platform Version** is set to 10.0.17134.0 (Windows 10, version 1803) or greater.</span></span>

<span data-ttu-id="d5900-126">Fügen Sie Ihrer vorkompilierten Headerdatei (in der Regel `pch.h`) `winrt/base.h` hinzu.</span><span class="sxs-lookup"><span data-stu-id="d5900-126">In your precompiled header file (usually `pch.h`), include `winrt/base.h`.</span></span>

```cppwinrt
#include <winrt/base.h>
```

<span data-ttu-id="d5900-127">Wenn Sie alle C++/WinRT-projizierten Windows-API-Header hinzufügen (z.B. `winrt/Windows.Foundation.h`), müssen Sie so nicht explizit `winrt/base.h` einschließen, da dies automatisch erfolgt.</span><span class="sxs-lookup"><span data-stu-id="d5900-127">If you include any C++/WinRT projected Windows API headers (for example, `winrt/Windows.Foundation.h`), then you don't need to explicitly include `winrt/base.h` like this because it will be included automatically for you.</span></span>

<span data-ttu-id="d5900-128">Wenn Ihr Projekt zudem Typen der [C++-Vorlagenbibliothek für Windows-Runtime (WRL)](/cpp/windows/windows-runtime-cpp-template-library-wrl) verwendet, lesen Sie bitte [Wechsel zu C++/WinRT von WRL](move-to-winrt-from-wrl.md).</span><span class="sxs-lookup"><span data-stu-id="d5900-128">If your project is also using [Windows Runtime C++ Template Library (WRL)](/cpp/windows/windows-runtime-cpp-template-library-wrl) types, then see [Move to C++/WinRT from WRL](move-to-winrt-from-wrl.md).</span></span>

## <a name="parameter-passing"></a><span data-ttu-id="d5900-129">Parameterübergabe</span><span class="sxs-lookup"><span data-stu-id="d5900-129">Parameter-passing</span></span>
<span data-ttu-id="d5900-130">Beim Schreiben von C++/CX-Quellcode übergeben Sie C++/CX-Typen als Funktionsparameter wie Hütchenverweise (\^).</span><span class="sxs-lookup"><span data-stu-id="d5900-130">When writing C++/CX source code, you pass C++/CX types as function parameters as hat (\^) references.</span></span>

```cpp
void LogPresenceRecord(PresenceRecord^ record);
```

<span data-ttu-id="d5900-131">In C++/WinRT sollten Sie für synchrone Funktionen standardmäßig `const&`-Parameter verwenden.</span><span class="sxs-lookup"><span data-stu-id="d5900-131">In C++/WinRT, for synchronous functions, you should use `const&` parameters by default.</span></span> <span data-ttu-id="d5900-132">Dadurch werden Kopien und unnötiger Zusatzaufwand vermieden.</span><span class="sxs-lookup"><span data-stu-id="d5900-132">That will avoid copies and interlocked overhead.</span></span> <span data-ttu-id="d5900-133">Ihre Coroutinen sollten aber Pass-by-Value verwenden, um sicherzustellen, dass sie nach Wert erfassen, und um Probleme mit der Lebensdauer zu vermeiden (weitere Informationen finden Sie unter [Parallelität und asynchrone Vorgänge mit C++/WinRT](concurrency.md)).</span><span class="sxs-lookup"><span data-stu-id="d5900-133">But your coroutines should use pass-by-value to ensure that they capture by value and avoid lifetime issues (for more details, see [Concurrency and asynchronous operations with C++/WinRT](concurrency.md)).</span></span>

```cppwinrt
void LogPresenceRecord(PresenceRecord const& record);
IASyncAction LogPresenceRecordAsync(PresenceRecord const record);
```

<span data-ttu-id="d5900-134">Ein C++/WinRT-Objekt ist im Grunde genommen ein Wert, der einen Schnittstellenzeiger zum zugrunde liegenden Windows-Runtime-Objekt enthält.</span><span class="sxs-lookup"><span data-stu-id="d5900-134">A C++/WinRT object is fundamentally a value that holds an interface pointer to the backing Windows Runtime object.</span></span> <span data-ttu-id="d5900-135">Beim Kopieren eines C++/WinRT-Objekts kopiert der Compiler den gekapselten Schnittstellenzeiger, wodurch sich sein Verweiszähler erhöht.</span><span class="sxs-lookup"><span data-stu-id="d5900-135">When you copy a C++/WinRT object, the compiler copies the encapsulated interface pointer, incrementing its reference count.</span></span> <span data-ttu-id="d5900-136">Eine Zerstörung der Kopie beinhaltet, dass der Verweiszähler verringert wird.</span><span class="sxs-lookup"><span data-stu-id="d5900-136">Eventual destruction of the copy involves decrementing the reference count.</span></span> <span data-ttu-id="d5900-137">Daher wird Aufwand einer Kopie nur bei Bedarf verursacht.</span><span class="sxs-lookup"><span data-stu-id="d5900-137">So, only incur the overhead of a copy when necessary.</span></span>

## <a name="variable-and-field-references"></a><span data-ttu-id="d5900-138">Variablen und Feldverweise</span><span class="sxs-lookup"><span data-stu-id="d5900-138">Variable and field references</span></span>
<span data-ttu-id="d5900-139">Beim Schreiben von C++/CX-Quellcode verwenden Sie Hütchenvariablen (\^) zum Verweisen auf Windows-Runtime-Objekte sowie den Pfeiloperator (-&gt;), um den Verweis einer Hütchenvariable aufzuheben.</span><span class="sxs-lookup"><span data-stu-id="d5900-139">When writing C++/CX source code, you use hat (\^) variables to reference Windows Runtime objects, and the arrow (-&gt;) operator to dereference a hat variable.</span></span>

```cpp
IVectorView<User^>^ userList = User::Users;

if (userList != nullptr)
{
    for (UINT32 iUser = 0; iUser < userList->Size; ++iUser)
    ...
```

<span data-ttu-id="d5900-140">Beim Portieren in den entsprechenden C++ / WinRT-Code Sie die hütchen entfernt und ändern Sie den Pfeiloperator (-&gt;) in den Punktoperator (.), da C++ / WinRT-projizierte Typen Werte und keine Zeiger sind.</span><span class="sxs-lookup"><span data-stu-id="d5900-140">When porting to the equivalent C++/WinRT code, you basically remove the hats and change the arrow operator (-&gt;) to the dot operator (.), because C++/WinRT projected types are values, and not pointers.</span></span>

```cppwinrt
IVectorView<User> userList = User::Users();

if (userList != nullptr)
{
    for (UINT32 iUser = 0; iUser < userList.Size(); ++iUser)
    ...
```

## <a name="properties"></a><span data-ttu-id="d5900-141">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="d5900-141">Properties</span></span>
<span data-ttu-id="d5900-142">Die C++/CX-Spracherweiterungen beinhalten das Konzept von Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="d5900-142">The C++/CX language extensions include the concept of properties.</span></span> <span data-ttu-id="d5900-143">Beim Schreiben von C++/CX-Quellcode können Sie auf eine Eigenschaft zugreifen, als wäre sie ein Feld.</span><span class="sxs-lookup"><span data-stu-id="d5900-143">When writing C++/CX source code, you can access a property as if it were a field.</span></span> <span data-ttu-id="d5900-144">Der C++-Standardcode verfügt nicht über das Konzept einer Eigenschaft, folglich rufen Sie in C++/WinRT Get- und Set-Funktionen auf.</span><span class="sxs-lookup"><span data-stu-id="d5900-144">Standard C++ does not have the concept of a property so, in C++/WinRT, you call get and set functions.</span></span>

<span data-ttu-id="d5900-145">In den folgenden Beispielen sind **XboxUserId**, **UserState**, **PresenceDeviceRecords** und **Größe** alles Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="d5900-145">In the examples that follow, **XboxUserId**, **UserState**, **PresenceDeviceRecords**, and **Size** are all properties.</span></span>

### <a name="retrieving-a-value-from-a-property"></a><span data-ttu-id="d5900-146">Abrufen eines Werts aus einer Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="d5900-146">Retrieving a value from a property</span></span>
<span data-ttu-id="d5900-147">So erhalten Sie einen Eigenschaftswert in C++/CX.</span><span class="sxs-lookup"><span data-stu-id="d5900-147">Here's how you get a property value in C++/CX.</span></span>

```cpp
void Sample::LogPresenceRecord(PresenceRecord^ record)
{
    auto id = record->XboxUserId;
    auto state = record->UserState;
    auto size = record->PresenceDeviceRecords->Size;
}
```

<span data-ttu-id="d5900-148">Der entsprechende C++/WinRT-Quellcode ruft eine Funktion mit dem gleichen Namen wie die Eigenschaft auf, jedoch ohne Parameter.</span><span class="sxs-lookup"><span data-stu-id="d5900-148">The equivalent C++/WinRT source code calls a function with the same name as the property, but with no parameters.</span></span>

```cppwinrt
void Sample::LogPresenceRecord(PresenceRecord const& record)
{
    auto id = record.XboxUserId();
    auto state = record.UserState();
    auto size = record.PresenceDeviceRecords().Size();
}
```

<span data-ttu-id="d5900-149">Beachten Sie, dass die Funktion **PresenceDeviceRecords** ein Windows-Runtime-Objekt zurückgibt, das über eine **Size**-Funktion verfügt.</span><span class="sxs-lookup"><span data-stu-id="d5900-149">Note that the **PresenceDeviceRecords** function returns a Windows Runtime object that itself has a **Size** function.</span></span> <span data-ttu-id="d5900-150">Da es sich beim zurückgegebenen Objekt ebenfalls um einen C++/WinRT-projizierten Typ handelt, dereferenzieren wir, indem wir den Punktoperator zum Aufrufen von **Size** verwenden.</span><span class="sxs-lookup"><span data-stu-id="d5900-150">As the returned object is also a C++/WinRT projected type, we dereference using the dot operator to call **Size**.</span></span>

### <a name="setting-a-property-to-a-new-value"></a><span data-ttu-id="d5900-151">Festlegen einer Eigenschaft auf einen neuen Wert</span><span class="sxs-lookup"><span data-stu-id="d5900-151">Setting a property to a new value</span></span>
<span data-ttu-id="d5900-152">Beim Festlegen einer Eigenschaft auf einen neuen Wert wird ein ähnliches Muster angewandt.</span><span class="sxs-lookup"><span data-stu-id="d5900-152">Setting a property to a new value follows a similar pattern.</span></span> <span data-ttu-id="d5900-153">Zuerst in C++/CX.</span><span class="sxs-lookup"><span data-stu-id="d5900-153">First, in C++/CX.</span></span>

```cpp
record->UserState = newValue;
```

<span data-ttu-id="d5900-154">Um das Äquivalent in C++/WinRT zu tun, rufen Sie eine Funktion mit dem gleichen Namen wie die Eigenschaft auf und übergeben ein Argument.</span><span class="sxs-lookup"><span data-stu-id="d5900-154">To do the equivalent in C++/WinRT, you call a function with the same name as the property, and pass an argument.</span></span>

```cppwinrt
record.UserState(newValue);
```

## <a name="creating-an-instance-of-a-class"></a><span data-ttu-id="d5900-155">Erstellen einer Instanz einer Klasse</span><span class="sxs-lookup"><span data-stu-id="d5900-155">Creating an instance of a class</span></span>
<span data-ttu-id="d5900-156">Sie arbeiten mit einem C++/ CX-Objekt über einen Handle dafür (Hütchenverweis (\^)).</span><span class="sxs-lookup"><span data-stu-id="d5900-156">You work with a C++/CX object via a handle to it, commonly known as a hat (\^) reference.</span></span> <span data-ttu-id="d5900-157">Sie erstellen ein neues Objekt über das Schlüsselwort `ref new`, das wiederum [**RoActivateInstance**](https://msdn.microsoft.com/library/br224646) aufruft, um eine neue Instanz der Laufzeitklasse zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="d5900-157">You create a new object via the `ref new` keyword, which in turn calls [**RoActivateInstance**](https://msdn.microsoft.com/library/br224646) to activate a new instance of the runtime class.</span></span>

```cpp
using namespace Windows::Storage::Streams;

class Sample
{
private:
    Buffer^ m_gamerPicBuffer = ref new Buffer(MAX_IMAGE_SIZE);
};
```

<span data-ttu-id="d5900-158">Ein C++/WinRT-Objekt ist ein Wert. Folglich können Sie es auf dem Stapel oder als ein Feld eines Objekts zuweisen.</span><span class="sxs-lookup"><span data-stu-id="d5900-158">A C++/WinRT object is a value; so you can allocate it on the stack, or as a field of an object.</span></span> <span data-ttu-id="d5900-159">*Niemals* können Sie `ref new` (oder `new`) verwenden, um ein C++/WinRT-Objekt zuzuordnen.</span><span class="sxs-lookup"><span data-stu-id="d5900-159">You *never* use `ref new` (nor `new`) to allocate a C++/WinRT object.</span></span> <span data-ttu-id="d5900-160">Im Hintergrund wird dennoch **RoActivateInstance** aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="d5900-160">Behind the scenes, **RoActivateInstance** is still being called.</span></span>

```cppwinrt
using namespace winrt::Windows::Storage::Streams;

struct Sample
{
private:
    Buffer m_gamerPicBuffer{ MAX_IMAGE_SIZE };
};
```

<span data-ttu-id="d5900-161">Wenn eine Ressource aufwendig zu initialisieren ist, ist es üblich, deren Initialisierung zu verzögern, bis sie tatsächlich benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="d5900-161">If a resource is expensive to initialize, then it's common to delay initialization of it until it's actually needed.</span></span>

```cpp
using namespace Windows::Storage::Streams;

class Sample
{
public:
    void DelayedInit()
    {
        // Allocate the actual buffer.
        m_gamerPicBuffer = ref new Buffer(MAX_IMAGE_SIZE);
    }

private:
    Buffer^ m_gamerPicBuffer;
};
```

<span data-ttu-id="d5900-162">Der gleiche Code wird zu C++/WinRT portiert.</span><span class="sxs-lookup"><span data-stu-id="d5900-162">The same code ported to C++/WinRT.</span></span> <span data-ttu-id="d5900-163">Beachten Sie die Verwendung des Konstruktors `nullptr`.</span><span class="sxs-lookup"><span data-stu-id="d5900-163">Note the use of the `nullptr` constructor.</span></span> <span data-ttu-id="d5900-164">Weitere Informationen zu diesem Konstruktor finden Sie unter [Nutzen von APIs mit C++/WinRT](consume-apis.md).</span><span class="sxs-lookup"><span data-stu-id="d5900-164">For more info about that constructor, see [Consume APIs with C++/WinRT](consume-apis.md).</span></span>

```cppwinrt
using namespace winrt::Windows::Storage::Streams;

struct Sample
{
    void DelayedInit()
    {
        // Allocate the actual buffer.
        m_gamerPicBuffer = Buffer(MAX_IMAGE_SIZE);
    }

private:
    Buffer m_gamerPicBuffer{ nullptr };
};
```

## <a name="converting-from-a-base-runtime-class-to-a-derived-one"></a><span data-ttu-id="d5900-165">Konvertieren von einer Basisklasse Laufzeitklasse in eine abgeleitete</span><span class="sxs-lookup"><span data-stu-id="d5900-165">Converting from a base runtime class to a derived one</span></span>
<span data-ttu-id="d5900-166">Es ist üblich, eine Verweis auf Basis verfügen, die Sie wissen, dass auf ein Objekt eines abgeleiteten Typs verweist.</span><span class="sxs-lookup"><span data-stu-id="d5900-166">It's common to have a reference-to-base that you know refers to an object of a derived type.</span></span> <span data-ttu-id="d5900-167">In C++ / CX verwenden Sie `dynamic_cast` zu *wandeln* der Referenz-Basis in einer Referenz-zu-abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="d5900-167">In C++/CX, you use `dynamic_cast` to *cast* the reference-to-base into a reference-to-derived.</span></span> <span data-ttu-id="d5900-168">Die `dynamic_cast` ist eigentlich nur ein versteckten Aufruf von [**QueryInterface**](https://msdn.microsoft.com/library/windows/desktop/ms682521).</span><span class="sxs-lookup"><span data-stu-id="d5900-168">The `dynamic_cast` is really just a hidden call to [**QueryInterface**](https://msdn.microsoft.com/library/windows/desktop/ms682521).</span></span> <span data-ttu-id="d5900-169">Hier ist ein typisches Beispiel&mdash;können Sie eine Abhängigkeit geänderter Eigenschaft-Ereignis behandeln und von **DependencyObject** zurück in den tatsächlichen Typ umgewandelt, die die Abhängigkeitseigenschaft besitzt werden soll.</span><span class="sxs-lookup"><span data-stu-id="d5900-169">Here's a typical example&mdash;you're handling a dependency property changed event, and you want to cast from **DependencyObject** back to the actual type that owns the dependency property.</span></span>

```cpp
void BgLabelControl::OnLabelChanged(Windows::UI::Xaml::DependencyObject^ d, Windows::UI::Xaml::DependencyPropertyChangedEventArgs^ e)
{
    BgLabelControl^ theControl{ dynamic_cast<BgLabelControl^>(d) };

    if (theControl != nullptr)
    {
        // succeeded ...
    }
}
```

<span data-ttu-id="d5900-170">Die entsprechende C++ / WinRT-Code ersetzt die `dynamic_cast` mit einem Aufruf an die [**IUnknown:: Try_as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknowntryas-function) Funktion, die **QueryInterface**kapselt.</span><span class="sxs-lookup"><span data-stu-id="d5900-170">The equivalent C++/WinRT code replaces the `dynamic_cast` with a call to the [**IUnknown::try_as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknowntryas-function) function, which encapsulates **QueryInterface**.</span></span> <span data-ttu-id="d5900-171">Sie haben auch die Möglichkeit, rufen Sie stattdessen [**IUnknown:: As**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknownas-function), die eine Ausnahme auslöst, wenn für die erforderliche Schnittstelle (die Standardschnittstelle des Typs, die Sie anfordern) Abfragen nicht zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="d5900-171">You also have the option to call [**IUnknown::as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknownas-function), instead, which throws an exception if querying for the required interface (the default interface of the type you're requesting) is not returned.</span></span> <span data-ttu-id="d5900-172">Hier sehen Sie eine C++ / WinRT-Codebeispiel.</span><span class="sxs-lookup"><span data-stu-id="d5900-172">Here's a C++/WinRT code example.</span></span>

```cppwinrt
void BgLabelControl::OnLabelChanged(Windows::UI::Xaml::DependencyObject const& d, Windows::UI::Xaml::DependencyPropertyChangedEventArgs const& e)
{
    if (BgLabelControlApp::BgLabelControl theControl{ d.try_as<BgLabelControlApp::BgLabelControl>() })
    {
        // succeeded ...
    }

    try
    {
        BgLabelControlApp::BgLabelControl theControl{ d.as<BgLabelControlApp::BgLabelControl>() };
        // succeeded ...
    }
    catch (winrt::hresult_no_interface const&)
    {
        // failed ...
    }
}
```

## <a name="event-handling-with-a-delegate"></a><span data-ttu-id="d5900-173">Ereignisbehandlung mit einem Delegaten</span><span class="sxs-lookup"><span data-stu-id="d5900-173">Event-handling with a delegate</span></span>
<span data-ttu-id="d5900-174">Hier ist ein typisches Beispiel für die Behandlung eines Ereignisses in C++/CX unter Verwendung einer Lambda-Funktion als Delegaten.</span><span class="sxs-lookup"><span data-stu-id="d5900-174">Here's a typical example of handling an event in C++/CX, using a lambda function as a delegate in this case.</span></span>

```cpp
auto token = myButton->Click += ref new RoutedEventHandler([&](Platform::Object^ sender, RoutedEventArgs^ args)
{
    // Handle the event.
});
```

<span data-ttu-id="d5900-175">Dies ist das Äquivalent in C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="d5900-175">This is the equivalent in C++/WinRT.</span></span>

```cppwinrt
auto token = myButton().Click([&](IInspectable const& sender, RoutedEventArgs const& args)
{
    // Handle the event.
});
```

<span data-ttu-id="d5900-176">Anstelle einer Lambda-Funktion können Sie den Delegaten als eine freie Funktion oder als Pointer-to-Member-Funktion implementieren.</span><span class="sxs-lookup"><span data-stu-id="d5900-176">Instead of a lambda function, you can choose to implement your delegate as a free function, or as a pointer-to-member-function.</span></span> <span data-ttu-id="d5900-177">Weitere Informationen finden Sie unter [Verarbeiten von Ereignissen über Delegaten in C++/WinRT](handle-events.md).</span><span class="sxs-lookup"><span data-stu-id="d5900-177">For more info, see [Handle events by using delegates in C++/WinRT](handle-events.md).</span></span>

<span data-ttu-id="d5900-178">Wenn Sie von einer C++/CX-Codebasis portieren, wo Ereignisse und Delegate intern verwendet werden (nicht über Binärdateien), hilft Ihnen [**winrt::delegate**](/uwp/cpp-ref-for-winrt/delegate) beim Replizieren dieses Musters in C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="d5900-178">If you're porting from a C++/CX codebase where events and delegates are used internally (not across binaries), then [**winrt::delegate**](/uwp/cpp-ref-for-winrt/delegate) will help you to replicate that pattern in C++/WinRT.</span></span> <span data-ttu-id="d5900-179">Siehe auch [parametrisiert Delegaten, einfachen Signale und Rückrufe innerhalb eines Projekts](author-events.md#parameterized-delegates-simple-signals-and-callbacks-within-a-project).</span><span class="sxs-lookup"><span data-stu-id="d5900-179">Also see [Parameterized delegates, simple signals, and callbacks within a project](author-events.md#parameterized-delegates-simple-signals-and-callbacks-within-a-project).</span></span>

## <a name="revoking-a-delegate"></a><span data-ttu-id="d5900-180">Widerrufen eines Delegaten</span><span class="sxs-lookup"><span data-stu-id="d5900-180">Revoking a delegate</span></span>
<span data-ttu-id="d5900-181">In C++/CX verwenden Sie den `-=`-Operator, um eine frühere Ereignisregistrierung zu widerrufen.</span><span class="sxs-lookup"><span data-stu-id="d5900-181">In C++/CX you use the `-=` operator to revoke a prior event registration.</span></span>

```cpp
myButton->Click -= token;
```

<span data-ttu-id="d5900-182">Dies ist das Äquivalent in C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="d5900-182">This is the equivalent in C++/WinRT.</span></span>

```cppwinrt
myButton().Click(token);
```

<span data-ttu-id="d5900-183">Weitere Informationen und Optionen finden Sie unter [Einen registrierten Delegaten widerrufen](handle-events.md#revoke-a-registered-delegate).</span><span class="sxs-lookup"><span data-stu-id="d5900-183">For more info and options, see [Revoke a registered delegate](handle-events.md#revoke-a-registered-delegate).</span></span>

## <a name="mapping-ccx-platform-types-to-cwinrt-types"></a><span data-ttu-id="d5900-184">Zuordnen von C++/CX-**Platform**-Typen zu C++/WinRT-Typen</span><span class="sxs-lookup"><span data-stu-id="d5900-184">Mapping C++/CX **Platform** types to C++/WinRT types</span></span>
<span data-ttu-id="d5900-185">C++/CX bietet verschiedene Datentypen im **Platform**-Namespace.</span><span class="sxs-lookup"><span data-stu-id="d5900-185">C++/CX provides several data types in the **Platform** namespace.</span></span> <span data-ttu-id="d5900-186">Diese Typen gehören nicht zum C++-Standard, daher können Sie sie nur verwenden, wenn Sie die Windows-Runtime-Spracherweiterungen aktivieren (Visual Studio-Projekteigenschaft **C/C++** > **Allgemein** > **Windows-Runtime-Erweiterung verwenden** > **Ja (/ZW)**).</span><span class="sxs-lookup"><span data-stu-id="d5900-186">These types are not standard C++, so you can only use them when you enable Windows Runtime language extensions (Visual Studio project property **C/C++** > **General** > **Consume Windows Runtime Extension** > **Yes (/ZW)**).</span></span> <span data-ttu-id="d5900-187">In der Tabelle unten finden Sie Informationen zum Portieren von **Platform**-Typen in ihre Entsprechungen in C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="d5900-187">The table below helps you port from **Platform** types to their equivalents in C++/WinRT.</span></span> <span data-ttu-id="d5900-188">Nachdem Sie dies erledigt haben, können Sie, da C++/WinRT zum C++-Standard gehört, die Option `/ZW` deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="d5900-188">Once you've done that, since C++/WinRT is standard C++, you can turn off the `/ZW` option.</span></span>

| <span data-ttu-id="d5900-189">C++/CX</span><span class="sxs-lookup"><span data-stu-id="d5900-189">C++/CX</span></span> | <span data-ttu-id="d5900-190">C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="d5900-190">C++/WinRT</span></span> |
| ---- | ---- |
| **<span data-ttu-id="d5900-191">Platform:: Agile\ ^</span><span class="sxs-lookup"><span data-stu-id="d5900-191">Platform::Agile\^</span></span>** | [**<span data-ttu-id="d5900-192">WinRT:: agile_ref</span><span class="sxs-lookup"><span data-stu-id="d5900-192">winrt::agile_ref</span></span>**](/uwp/cpp-ref-for-winrt/agile-ref) |
| **<span data-ttu-id="d5900-193">Platform::Exception\^</span><span class="sxs-lookup"><span data-stu-id="d5900-193">Platform::Exception\^</span></span>** | [**<span data-ttu-id="d5900-194">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="d5900-194">winrt::hresult_error</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error) |
| **<span data-ttu-id="d5900-195">Platform::InvalidArgumentException\^</span><span class="sxs-lookup"><span data-stu-id="d5900-195">Platform::InvalidArgumentException\^</span></span>** | [**<span data-ttu-id="d5900-196">winrt::hresult_invalid_argument</span><span class="sxs-lookup"><span data-stu-id="d5900-196">winrt::hresult_invalid_argument</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-invalid-argument) |
| **<span data-ttu-id="d5900-197">Platform::Object\^</span><span class="sxs-lookup"><span data-stu-id="d5900-197">Platform::Object\^</span></span>** | **<span data-ttu-id="d5900-198">winrt::Windows::Foundation::IInspectable</span><span class="sxs-lookup"><span data-stu-id="d5900-198">winrt::Windows::Foundation::IInspectable</span></span>** |
| **<span data-ttu-id="d5900-199">Platform::String\^</span><span class="sxs-lookup"><span data-stu-id="d5900-199">Platform::String\^</span></span>** | [**<span data-ttu-id="d5900-200">winrt::hstring</span><span class="sxs-lookup"><span data-stu-id="d5900-200">winrt::hstring</span></span>**](/uwp/cpp-ref-for-winrt/hstring) |

### <a name="port-platformagile-to-winrtagileref"></a><span data-ttu-id="d5900-201">Port **Platform:: Agile\ ^** zu **WinRT:: agile_ref**</span><span class="sxs-lookup"><span data-stu-id="d5900-201">Port **Platform::Agile\^** to **winrt::agile_ref**</span></span>
<span data-ttu-id="d5900-202">Die **Platform:: Agile\ ^** Typ in C++ / CX steht für eine Windows-Runtime-Klasse, die von jedem Thread aus zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="d5900-202">The **Platform::Agile\^** type in C++/CX represents a Windows Runtime class that can be accessed from any thread.</span></span> <span data-ttu-id="d5900-203">C++ / WinRT-äquivalent ist [**WinRT:: agile_ref**](/uwp/cpp-ref-for-winrt/agile-ref).</span><span class="sxs-lookup"><span data-stu-id="d5900-203">The C++/WinRT equivalent is [**winrt::agile_ref**](/uwp/cpp-ref-for-winrt/agile-ref).</span></span>

<span data-ttu-id="d5900-204">In C++/CX.</span><span class="sxs-lookup"><span data-stu-id="d5900-204">In C++/CX.</span></span>

```cpp
Platform::Agile<Windows::UI::Core::CoreWindow> m_window;
```

<span data-ttu-id="d5900-205">In C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="d5900-205">In C++/WinRT.</span></span>

```cppwinrt
winrt::agile_ref<Windows::UI::Core::CoreWindow> m_window;
```

### <a name="port-platformexception-to-winrthresulterror"></a><span data-ttu-id="d5900-206">Portieren von **Platform::Exception\^** nach **winrt::hresult_error**</span><span class="sxs-lookup"><span data-stu-id="d5900-206">Port **Platform::Exception\^** to **winrt::hresult_error**</span></span>
<span data-ttu-id="d5900-207">Der Typ **Platform::Exception\^** wird in C++/CX erzeugt, wenn eine Windows-Runtime-API ein Nicht-S\_OK HRESULT zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="d5900-207">The **Platform::Exception\^** type is produced in C++/CX when a Windows Runtime API returns a non S\_OK HRESULT.</span></span> <span data-ttu-id="d5900-208">Für C++/WinRT ist die Entsprechung [**winrt::hresult_error**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error).</span><span class="sxs-lookup"><span data-stu-id="d5900-208">The C++/WinRT equivalent is [**winrt::hresult_error**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error).</span></span>

<span data-ttu-id="d5900-209">Zum Portieren nach C++/WinRT ändern Sie jeglichen Code, der **Platform::Exception\^** verwendet, um stattdessen **winrt::hresult_error** zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="d5900-209">To port to C++/WinRT, change all code that uses **Platform::Exception\^** to use **winrt::hresult_error**.</span></span>

<span data-ttu-id="d5900-210">In C++/CX.</span><span class="sxs-lookup"><span data-stu-id="d5900-210">In C++/CX.</span></span>

```cpp
catch (Platform::Exception^ ex)
```

<span data-ttu-id="d5900-211">In C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="d5900-211">In C++/WinRT.</span></span>

```cppwinrt
catch (winrt::hresult_error const& ex)
```

<span data-ttu-id="d5900-212">C++/WinRT stellt diese Ausnahmeklassen bereit.</span><span class="sxs-lookup"><span data-stu-id="d5900-212">C++/WinRT provides these exception classes.</span></span>

| <span data-ttu-id="d5900-213">Ausnahmentyp</span><span class="sxs-lookup"><span data-stu-id="d5900-213">Exception type</span></span> | <span data-ttu-id="d5900-214">Basisklasse</span><span class="sxs-lookup"><span data-stu-id="d5900-214">Base class</span></span> | <span data-ttu-id="d5900-215">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d5900-215">HRESULT</span></span> |
| ---- | ---- | ---- |
| [**<span data-ttu-id="d5900-216">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="d5900-216">winrt::hresult_error</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error) | | <span data-ttu-id="d5900-217">Aufrufen von [**hresult_error::to_abi**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error#hresulterrortoabi-function)</span><span class="sxs-lookup"><span data-stu-id="d5900-217">call [**hresult_error::to_abi**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error#hresulterrortoabi-function)</span></span> |
| [**<span data-ttu-id="d5900-218">winrt::hresult_access_denied</span><span class="sxs-lookup"><span data-stu-id="d5900-218">winrt::hresult_access_denied</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-access-denied) | **<span data-ttu-id="d5900-219">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="d5900-219">winrt::hresult_error</span></span>** | <span data-ttu-id="d5900-220">E_ACCESSDENIED</span><span class="sxs-lookup"><span data-stu-id="d5900-220">E_ACCESSDENIED</span></span> |
| [**<span data-ttu-id="d5900-221">winrt::hresult_canceled</span><span class="sxs-lookup"><span data-stu-id="d5900-221">winrt::hresult_canceled</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-canceled) | **<span data-ttu-id="d5900-222">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="d5900-222">winrt::hresult_error</span></span>** | <span data-ttu-id="d5900-223">ERROR_CANCELLED</span><span class="sxs-lookup"><span data-stu-id="d5900-223">ERROR_CANCELLED</span></span> |
| [**<span data-ttu-id="d5900-224">winrt::hresult_changed_state</span><span class="sxs-lookup"><span data-stu-id="d5900-224">winrt::hresult_changed_state</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-changed-state) | **<span data-ttu-id="d5900-225">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="d5900-225">winrt::hresult_error</span></span>** | <span data-ttu-id="d5900-226">E_CHANGED_STATE</span><span class="sxs-lookup"><span data-stu-id="d5900-226">E_CHANGED_STATE</span></span> |
| [**<span data-ttu-id="d5900-227">winrt::hresult_class_not_available</span><span class="sxs-lookup"><span data-stu-id="d5900-227">winrt::hresult_class_not_available</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-class-not-available) | **<span data-ttu-id="d5900-228">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="d5900-228">winrt::hresult_error</span></span>** | <span data-ttu-id="d5900-229">CLASS_E_CLASSNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d5900-229">CLASS_E_CLASSNOTAVAILABLE</span></span> |
| [**<span data-ttu-id="d5900-230">winrt::hresult_illegal_delegate_assignment</span><span class="sxs-lookup"><span data-stu-id="d5900-230">winrt::hresult_illegal_delegate_assignment</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-illegal-delegate-assignment) | **<span data-ttu-id="d5900-231">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="d5900-231">winrt::hresult_error</span></span>** | <span data-ttu-id="d5900-232">E_ILLEGAL_DELEGATE_ASSIGNMENT</span><span class="sxs-lookup"><span data-stu-id="d5900-232">E_ILLEGAL_DELEGATE_ASSIGNMENT</span></span> |
| [**<span data-ttu-id="d5900-233">winrt::hresult_illegal_method_call</span><span class="sxs-lookup"><span data-stu-id="d5900-233">winrt::hresult_illegal_method_call</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-illegal-method-call) | **<span data-ttu-id="d5900-234">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="d5900-234">winrt::hresult_error</span></span>** | <span data-ttu-id="d5900-235">E_ILLEGAL_METHOD_CALL</span><span class="sxs-lookup"><span data-stu-id="d5900-235">E_ILLEGAL_METHOD_CALL</span></span> |
| [**<span data-ttu-id="d5900-236">winrt::hresult_illegal_state_change</span><span class="sxs-lookup"><span data-stu-id="d5900-236">winrt::hresult_illegal_state_change</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-illegal-state-change) | **<span data-ttu-id="d5900-237">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="d5900-237">winrt::hresult_error</span></span>** | <span data-ttu-id="d5900-238">E_ILLEGAL_STATE_CHANGE</span><span class="sxs-lookup"><span data-stu-id="d5900-238">E_ILLEGAL_STATE_CHANGE</span></span> |
| [**<span data-ttu-id="d5900-239">winrt::hresult_invalid_argument</span><span class="sxs-lookup"><span data-stu-id="d5900-239">winrt::hresult_invalid_argument</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-invalid-argument) | **<span data-ttu-id="d5900-240">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="d5900-240">winrt::hresult_error</span></span>** | <span data-ttu-id="d5900-241">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d5900-241">E_INVALIDARG</span></span> |
| [**<span data-ttu-id="d5900-242">winrt::hresult_no_interface</span><span class="sxs-lookup"><span data-stu-id="d5900-242">winrt::hresult_no_interface</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-no-interface) | **<span data-ttu-id="d5900-243">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="d5900-243">winrt::hresult_error</span></span>** | <span data-ttu-id="d5900-244">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="d5900-244">E_NOINTERFACE</span></span> |
| [**<span data-ttu-id="d5900-245">winrt::hresult_not_implemented</span><span class="sxs-lookup"><span data-stu-id="d5900-245">winrt::hresult_not_implemented</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-not-implemented) | **<span data-ttu-id="d5900-246">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="d5900-246">winrt::hresult_error</span></span>** | <span data-ttu-id="d5900-247">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="d5900-247">E_NOTIMPL</span></span> |
| [**<span data-ttu-id="d5900-248">winrt::hresult_out_of_bounds</span><span class="sxs-lookup"><span data-stu-id="d5900-248">winrt::hresult_out_of_bounds</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-out-of-bounds) | **<span data-ttu-id="d5900-249">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="d5900-249">winrt::hresult_error</span></span>** | <span data-ttu-id="d5900-250">E_BOUNDS</span><span class="sxs-lookup"><span data-stu-id="d5900-250">E_BOUNDS</span></span> |
| [**<span data-ttu-id="d5900-251">winrt::hresult_wrong_thread</span><span class="sxs-lookup"><span data-stu-id="d5900-251">winrt::hresult_wrong_thread</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-wrong-thread) | **<span data-ttu-id="d5900-252">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="d5900-252">winrt::hresult_error</span></span>** | <span data-ttu-id="d5900-253">RPC_E_WRONG_THREAD</span><span class="sxs-lookup"><span data-stu-id="d5900-253">RPC_E_WRONG_THREAD</span></span> |

<span data-ttu-id="d5900-254">Beachten Sie, dass jede Klasse (über die **hresult_error** -Basisklasse) eine [**to_abi**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error#hresulterrortoabi-function)-Funktion bereitstellt, die das HRESULT für den Fehler zurückgibt, sowie eine [**message**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error#hresulterrormessage-function)-Funktion, die die Darstellung der Zeichenfolge dieses HRESULT zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="d5900-254">Note that each class (via the **hresult_error** base class) provides a [**to_abi**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error#hresulterrortoabi-function) function, which returns the HRESULT of the error, and a [**message**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error#hresulterrormessage-function) function, which returns the string representation of that HRESULT.</span></span>

<span data-ttu-id="d5900-255">Hier ist ein Beispiel für das Auslösen einer Ausnahme in C++/CX.</span><span class="sxs-lookup"><span data-stu-id="d5900-255">Here's an example of throwing an exception in C++/CX.</span></span>

```cpp
throw ref new Platform::InvalidArgumentException(L"A valid User is required");
```

<span data-ttu-id="d5900-256">Und das Äquivalent in C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="d5900-256">And the equivalent in C++/WinRT.</span></span>

```cppwinrt
throw winrt::hresult_invalid_argument{ L"A valid User is required" };
```

### <a name="port-platformobject-to-winrtwindowsfoundationiinspectable"></a><span data-ttu-id="d5900-257">Portieren von **Platform::Object\^** nach **winrt::Windows::Foundation::IInspectable**</span><span class="sxs-lookup"><span data-stu-id="d5900-257">Port **Platform::Object\^** to **winrt::Windows::Foundation::IInspectable**</span></span>
<span data-ttu-id="d5900-258">Wie alle C++/WinRT-Typen ist **winrt::Windows::Foundation::IInspectable** ein Werttyp.</span><span class="sxs-lookup"><span data-stu-id="d5900-258">Like all C++/WinRT types, **winrt::Windows::Foundation::IInspectable** is a value type.</span></span> <span data-ttu-id="d5900-259">Hier erfahren Sie, wie Sie eine Variable dieses Typs auf null initialisieren.</span><span class="sxs-lookup"><span data-stu-id="d5900-259">Here's how you initialize a variable of that type to null.</span></span>

```cppwinrt
winrt::Windows::Foundation::IInspectable var{ nullptr };
```

### <a name="port-platformstring-to-winrthstring"></a><span data-ttu-id="d5900-260">Portieren von **Platform::String\^** nach **winrt::hstring**</span><span class="sxs-lookup"><span data-stu-id="d5900-260">Port **Platform::String\^** to **winrt::hstring**</span></span>
<span data-ttu-id="d5900-261">**Platform::String\^** ist das Äquivalent zum Windows-Runtime-HSTRING-ABI-Typ.</span><span class="sxs-lookup"><span data-stu-id="d5900-261">**Platform::String\^** is equivalent to the Windows Runtime HSTRING ABI type.</span></span> <span data-ttu-id="d5900-262">Für C++/WinRT ist die Entsprechung [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring).</span><span class="sxs-lookup"><span data-stu-id="d5900-262">For C++/WinRT, the equivalent is [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring).</span></span> <span data-ttu-id="d5900-263">Mit C++/WinRT können Sie aber Windows-Runtime-APIs mit Standard-C++ Wide-String-Typen wie **std::wstring** aufrufen und/oder Wide-String-Literale.</span><span class="sxs-lookup"><span data-stu-id="d5900-263">But with C++/WinRT, you can call Windows Runtime APIs using C++ Standard Library wide string types such as **std::wstring**, and/or wide string literals.</span></span> <span data-ttu-id="d5900-264">Weitere Informationen und Codebeispiele finden Sie unter [String-Verarbeitung in C++/WinRT](strings.md).</span><span class="sxs-lookup"><span data-stu-id="d5900-264">For more details, and code examples, see [String handling in C++/WinRT](strings.md).</span></span>

<span data-ttu-id="d5900-265">Mit C++/CX können Sie auf die Eigenschaft [**Platform::String::Data**](https://docs.microsoft.com/en-us/cpp/cppcx/platform-string-class#data) zugreifen, um die Zeichenfolge als **const wchar_t\***-Array im C-Stil abzurufen (z.B. zur Übergabe an **std::wcout**).</span><span class="sxs-lookup"><span data-stu-id="d5900-265">With C++/CX, you can access the [**Platform::String::Data**](https://docs.microsoft.com/en-us/cpp/cppcx/platform-string-class#data) property to retrieve the string as a C-style **const wchar_t\*** array (for example, to pass it to **std::wcout**).</span></span>

```C++
auto var = titleRecord->TitleName->Data();
```

<span data-ttu-id="d5900-266">Um das Gleiche mit C++ / WinRT zu tun, können Sie die Funktion [**hstring::c_str**](/uwp/api/windows.foundation.uri#hstringcstr-function) verwenden, um eine auf null beendete Zeichenfolgenversion im C-Stil abzurufen (wie von **std::wstring**).</span><span class="sxs-lookup"><span data-stu-id="d5900-266">To do the same with C++/WinRT, you can use the [**hstring::c_str**](/uwp/api/windows.foundation.uri#hstringcstr-function) function to get a null-terminated C-style string version, just as you can from **std::wstring**.</span></span>

```C++
auto var = titleRecord.TitleName().c_str();
```

<span data-ttu-id="d5900-267">Bei der Implementierung von APIs, die Zeichenfolgen übernehmen oder zurückgeben, ändern Sie in der Regel jeglichen C++/CX-Code, der **Platform::String\^** verwendet, um stattdessen **winrt::hstring** zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="d5900-267">When it comes to implementing APIs that take or return strings, you typically change any C++/CX code that uses **Platform::String\^** to use **winrt::hstring** instead.</span></span>

<span data-ttu-id="d5900-268">Hier ist ein Beispiel für eine C++/CX-API, die eine Zeichenfolge übernimmt.</span><span class="sxs-lookup"><span data-stu-id="d5900-268">Here's an example of a C++/CX API that takes a string.</span></span>

```cpp
void LogWrapLine(Platform::String^ str);
```

<span data-ttu-id="d5900-269">Für C++/WinRT könnten Sie diese API in [MIDL 3.0](/uwp/midl-3) wie folgt deklarieren.</span><span class="sxs-lookup"><span data-stu-id="d5900-269">For C++/WinRT you could declare that API in [MIDL 3.0](/uwp/midl-3) like this.</span></span>

```idl
// LogType.idl
void LogWrapLine(String str);
```

<span data-ttu-id="d5900-270">Die C++/WinRT-Toolkette generiert dann Quellcode für Sie, der wie folgt aussieht.</span><span class="sxs-lookup"><span data-stu-id="d5900-270">The C++/WinRT toolchain will then generate source code for you that looks like this.</span></span>

```cppwinrt
void LogWrapLine(winrt::hstring const& str);
```

## <a name="important-apis"></a><span data-ttu-id="d5900-271">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="d5900-271">Important APIs</span></span>
* [<span data-ttu-id="d5900-272">winrt::delegate-Strukturvorlage</span><span class="sxs-lookup"><span data-stu-id="d5900-272">winrt::delegate struct template</span></span>](/uwp/cpp-ref-for-winrt/delegate)
* [<span data-ttu-id="d5900-273">winrt::hresult_error-Struktur</span><span class="sxs-lookup"><span data-stu-id="d5900-273">winrt::hresult_error struct</span></span>](/uwp/cpp-ref-for-winrt/error-handling/hresult-error)
* [<span data-ttu-id="d5900-274">winrt::hstring-Struktur</span><span class="sxs-lookup"><span data-stu-id="d5900-274">winrt::hstring struct</span></span>](/uwp/cpp-ref-for-winrt/hstring)
* [<span data-ttu-id="d5900-275">winrt-Namespace</span><span class="sxs-lookup"><span data-stu-id="d5900-275">winrt namespace</span></span>](/uwp/cpp-ref-for-winrt/winrt)

## <a name="related-topics"></a><span data-ttu-id="d5900-276">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="d5900-276">Related topics</span></span>
* [<span data-ttu-id="d5900-277">C++/CX</span><span class="sxs-lookup"><span data-stu-id="d5900-277">C++/CX</span></span>](/cpp/cppcx/visual-c-language-reference-c-cx)
* [<span data-ttu-id="d5900-278">Erstellen von Ereignissen mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="d5900-278">Author events in C++/WinRT</span></span>](author-events.md)
* [<span data-ttu-id="d5900-279">Parallelität und asynchrone Vorgänge mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="d5900-279">Concurrency and asynchronous operations with C++/WinRT</span></span>](concurrency.md)
* [<span data-ttu-id="d5900-280">Verwenden von APIs mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="d5900-280">Consume APIs with C++/WinRT</span></span>](consume-apis.md)
* [<span data-ttu-id="d5900-281">Verarbeiten von Ereignissen über Delegaten in C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="d5900-281">Handle events by using delegates in C++/WinRT</span></span>](handle-events.md)
* [<span data-ttu-id="d5900-282">Interoperabilität zwischen C++/WinRT und C++/CX</span><span class="sxs-lookup"><span data-stu-id="d5900-282">Interop between C++/WinRT and C++/CX</span></span>](interop-winrt-cx.md)
* [<span data-ttu-id="d5900-283">Microsoft Interface Definition Language3.0– Referenz</span><span class="sxs-lookup"><span data-stu-id="d5900-283">Microsoft Interface Definition Language 3.0 reference</span></span>](/uwp/midl-3)
* [<span data-ttu-id="d5900-284">Wechsel zu C++/WinRT von WRL</span><span class="sxs-lookup"><span data-stu-id="d5900-284">Move to C++/WinRT from WRL</span></span>](move-to-winrt-from-wrl.md)
* [<span data-ttu-id="d5900-285">String-Verarbeitung in C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="d5900-285">String handling in C++/WinRT</span></span>](strings.md)
