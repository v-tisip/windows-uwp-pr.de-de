---
author: stevewhims
description: In diesem Thema wird gezeigt, wie Sie C++/CX-Code zum entsprechenden Äquivalent in C++/WinRT portieren.
title: Wechsel zu C++/WinRT von C++/CX
ms.author: stwhi
ms.date: 05/30/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projizierung, portieren, migrieren, C++/CX
ms.localizationpriority: medium
ms.openlocfilehash: da6226158056cbbf0b51b46be0b17fe7e478dd01
ms.sourcegitcommit: 929fa4b3273862dcdc76b083bf6c3b2c872dd590
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2018
ms.locfileid: "1935748"
---
# <a name="move-to-cwinrtwindowsuwpcpp-and-winrt-apisintro-to-using-cpp-with-winrt-from-ccx"></a><span data-ttu-id="afd98-104">Wechsel zu [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) von C++/CX</span><span class="sxs-lookup"><span data-stu-id="afd98-104">Move to [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) from C++/CX</span></span>
<span data-ttu-id="afd98-105">In diesem Thema wird gezeigt, wie Sie [C++/CX](/cpp/cppcx/visual-c-language-reference-c-cx)-Code zum entsprechenden Äquivalent in C++/WinRT portieren.</span><span class="sxs-lookup"><span data-stu-id="afd98-105">This topic shows how to port [C++/CX](/cpp/cppcx/visual-c-language-reference-c-cx) code to its equivalent in C++/WinRT.</span></span>

> [!NOTE]
> <span data-ttu-id="afd98-106">Sowohl [C++/CX ](/cpp/cppcx/visual-c-language-reference-c-cx) als auch das Windows SDK deklarieren Typen im Root-Namespace **Windows**.</span><span class="sxs-lookup"><span data-stu-id="afd98-106">Both [C++/CX](/cpp/cppcx/visual-c-language-reference-c-cx) and the Windows SDK declare types in the root namespace **Windows**.</span></span> <span data-ttu-id="afd98-107">Ein Windows-Typ, der in C++/WinRT projiziert wird, verfügt über den gleichen vollqualifizierten Namen wie der Windows-Typ, befindet sich aber im C++/**winrt**-Namespace.</span><span class="sxs-lookup"><span data-stu-id="afd98-107">A Windows type projected into C++/WinRT has the same fully-qualified name as the Windows type, but it's placed in the C++ **winrt** namespace.</span></span> <span data-ttu-id="afd98-108">Diese unterschiedlichen Namespaces ermöglichen die Portierung von C++/CX nach C++/WinRT in Ihrem eigenen Tempo.</span><span class="sxs-lookup"><span data-stu-id="afd98-108">These distinct namespaces let you port from C++/CX to C++/WinRT at your own pace.</span></span>

<span data-ttu-id="afd98-109">Der erste Schritt beim Portieren zu C++/WinRT besteht darin, C++/WinRT-Unterstützung manuell Ihrem Projekt hinzuzufügen (siehe [Visual Studio-Unterstützung für C++/WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix)).</span><span class="sxs-lookup"><span data-stu-id="afd98-109">The first step in porting to C++/WinRT is to manually add C++/WinRT support to your project (see [Visual Studio support for C++/WinRT, and the VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix)).</span></span> <span data-ttu-id="afd98-110">Bearbeiten Sie dazu Ihre `.vcxproj`-Datei, suchen Sie nach `<PropertyGroup Label="Globals">`, und definieren Sie innerhalb dieser Eigenschaftengruppe die Eigenschaft `<CppWinRTEnabled>true</CppWinRTEnabled>`.</span><span class="sxs-lookup"><span data-stu-id="afd98-110">To do that, edit your `.vcxproj` file, find `<PropertyGroup Label="Globals">` and, inside that property group, set the property `<CppWinRTEnabled>true</CppWinRTEnabled>`.</span></span> <span data-ttu-id="afd98-111">Eine Auswirkung dieser Änderung ist, dass die Unterstützung für C++/CX im Projekt deaktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="afd98-111">One effect of that change is that support for C++/CX is turned off in the project.</span></span> <span data-ttu-id="afd98-112">Es empfiehlt sich, die Unterstützung deaktiviert zu lassen, damit Sie alle Ihre Abhängigkeiten von C++/CX finden und portieren können. Sie können die Unterstützung auch wieder aktivieren (in den Projekteigenschaften, **C/C++** \> **Allgemein** \> **Windows-Runtime-Erweiterung verwenden** \> **Ja (/ZW)**) und nach und nach portieren.</span><span class="sxs-lookup"><span data-stu-id="afd98-112">It's a good idea to leave support turned off so that you can find and port all of your dependencies on C++/CX, or you can turn support back on (in project properties, **C/C++** \> **General** \> **Consume Windows Runtime Extension** \> **Yes (/ZW)**), and port gradually.</span></span>

<span data-ttu-id="afd98-113">Definieren Sie die Projekteigenschaft **Allgemein** \> **Zielplattformversion** mit 10.0.17134.0 (Windows 10, Version 1803) oder höher.</span><span class="sxs-lookup"><span data-stu-id="afd98-113">Set project property **General** \> **Target Platform Version** to 10.0.17134.0 (Windows 10, version 1803) or greater.</span></span>

<span data-ttu-id="afd98-114">Fügen Sie Ihrer vorkompilierten Headerdatei (in der Regel `pch.h`) `winrt/base.h` hinzu.</span><span class="sxs-lookup"><span data-stu-id="afd98-114">In your precompiled header file (usually `pch.h`), include `winrt/base.h`.</span></span>

```cppwinrt
#include <winrt/base.h>
```

<span data-ttu-id="afd98-115">Wenn Sie alle C++/WinRT-projizierten Windows-API-Header hinzufügen (z.B. `winrt/Windows.Foundation.h`), müssen Sie so nicht explizit `winrt/base.h` einschließen, da dies automatisch erfolgt.</span><span class="sxs-lookup"><span data-stu-id="afd98-115">If you include any C++/WinRT projected Windows API headers (for example, `winrt/Windows.Foundation.h`), then you don't need to explicitly include `winrt/base.h` like this because it will be included automatically for you.</span></span>

<span data-ttu-id="afd98-116">Wenn Ihr Projekt zudem Typen der [C++-Vorlagenbibliothek für Windows-Runtime (WRL)](/cpp/windows/windows-runtime-cpp-template-library-wrl) verwendet, lesen Sie bitte [Wechsel zu C++/WinRT von WRL](move-to-winrt-from-wrl.md).</span><span class="sxs-lookup"><span data-stu-id="afd98-116">If your project is also using [Windows Runtime C++ Template Library (WRL)](/cpp/windows/windows-runtime-cpp-template-library-wrl) types, then see [Move to C++/WinRT from WRL](move-to-winrt-from-wrl.md).</span></span>

## <a name="parameter-passing"></a><span data-ttu-id="afd98-117">Parameterübergabe</span><span class="sxs-lookup"><span data-stu-id="afd98-117">Parameter-passing</span></span>
<span data-ttu-id="afd98-118">Beim Schreiben von C++/CX-Quellcode übergeben Sie C++/CX-Typen als Funktionsparameter wie Hütchenverweise (\^).</span><span class="sxs-lookup"><span data-stu-id="afd98-118">When writing C++/CX source code, you pass C++/CX types as function parameters as hat (\^) references.</span></span>

```cpp
void LogPresenceRecord(PresenceRecord^ record);
```

<span data-ttu-id="afd98-119">In C++/WinRT sollten Sie für synchrone Funktionen standardmäßig `const&`-Parameter verwenden.</span><span class="sxs-lookup"><span data-stu-id="afd98-119">In C++/WinRT, for synchronous functions, you should use `const&` parameters by default.</span></span> <span data-ttu-id="afd98-120">Dadurch werden Kopien und unnötiger Zusatzaufwand vermieden.</span><span class="sxs-lookup"><span data-stu-id="afd98-120">That will avoid copies and interlocked overhead.</span></span> <span data-ttu-id="afd98-121">Ihre Coroutinen sollten aber Pass-by-Value verwenden, um sicherzustellen, dass sie nach Wert erfassen, und um Probleme mit der Lebensdauer zu vermeiden (weitere Informationen finden Sie unter [Parallelität und asynchrone Vorgänge mit C++/WinRT](concurrency.md)).</span><span class="sxs-lookup"><span data-stu-id="afd98-121">But your coroutines should use pass-by-value to ensure that they capture by value and avoid lifetime issues (for more details, see [Concurrency and asynchronous operations with C++/WinRT](concurrency.md)).</span></span>

```cppwinrt
void LogPresenceRecord(PresenceRecord const& record);
IASyncAction LogPresenceRecordAsync(PresenceRecord const record);
```

<span data-ttu-id="afd98-122">Ein C++/WinRT-Objekt ist im Grunde genommen ein Wert, der einen Schnittstellenzeiger zum zugrunde liegenden Windows-Runtime-Objekt enthält.</span><span class="sxs-lookup"><span data-stu-id="afd98-122">A C++/WinRT object is fundamentally a value that holds an interface pointer to the backing Windows Runtime object.</span></span> <span data-ttu-id="afd98-123">Beim Kopieren eines C++/WinRT-Objekts kopiert der Compiler den gekapselten Schnittstellenzeiger, wodurch sich sein Verweiszähler erhöht.</span><span class="sxs-lookup"><span data-stu-id="afd98-123">When you copy a C++/WinRT object, the compiler copies the encapsulated interface pointer, incrementing its reference count.</span></span> <span data-ttu-id="afd98-124">Eine Zerstörung der Kopie beinhaltet, dass der Verweiszähler verringert wird.</span><span class="sxs-lookup"><span data-stu-id="afd98-124">Eventual destruction of the copy involves decrementing the reference count.</span></span> <span data-ttu-id="afd98-125">Daher wird Aufwand einer Kopie nur bei Bedarf verursacht.</span><span class="sxs-lookup"><span data-stu-id="afd98-125">So, only incur the overhead of a copy when necessary.</span></span>

## <a name="variable-and-field-references"></a><span data-ttu-id="afd98-126">Variablen und Feldverweise</span><span class="sxs-lookup"><span data-stu-id="afd98-126">Variable and field references</span></span>
<span data-ttu-id="afd98-127">Beim Schreiben von C++/CX-Quellcode verwenden Sie Hütchenvariablen (\^) zum Verweisen auf Windows-Runtime-Objekte sowie den Pfeiloperator (-&gt;), um den Verweis einer Hütchenvariable aufzuheben.</span><span class="sxs-lookup"><span data-stu-id="afd98-127">When writing C++/CX source code, you use hat (\^) variables to reference Windows Runtime objects, and the arrow (-&gt;) operator to dereference a hat variable.</span></span>

```cpp
IVectorView<User^>^ userList = User::Users;

if (userList != nullptr)
{
    for (UINT32 iUser = 0; iUser < userList->Size; ++iUser)
    ...
```

<span data-ttu-id="afd98-128">Beim Konvertieren in den entsprechenden C++/WinRT-Code werden die Hütchen entfernt und der Pfeiloperator (-&gt;) in den Punktoperator (.) geändert, da C++/WinRT-projizierte Typen Werte und keine Zeiger sind.</span><span class="sxs-lookup"><span data-stu-id="afd98-128">When converting to the equivalent C++/WinRT code, you basically remove the hats and change the arrow operator (-&gt;) to the dot operator (.), because C++/WinRT projected types are values, and not pointers.</span></span>

```cppwinrt
IVectorView<User> userList = User::Users();

if (userList != nullptr)
{
    for (UINT32 iUser = 0; iUser < userList.Size(); ++iUser)
    ...
```

## <a name="properties"></a><span data-ttu-id="afd98-129">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="afd98-129">Properties</span></span>
<span data-ttu-id="afd98-130">Die C++/CX-Spracherweiterungen beinhalten das Konzept von Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="afd98-130">The C++/CX language extensions include the concept of properties.</span></span> <span data-ttu-id="afd98-131">Beim Schreiben von C++/CX-Quellcode können Sie auf eine Eigenschaft zugreifen, als wäre sie ein Feld.</span><span class="sxs-lookup"><span data-stu-id="afd98-131">When writing C++/CX source code, you can access a property as if it were a field.</span></span> <span data-ttu-id="afd98-132">Der C++-Standardcode verfügt nicht über das Konzept einer Eigenschaft, folglich rufen Sie in C++/WinRT Get- und Set-Funktionen auf.</span><span class="sxs-lookup"><span data-stu-id="afd98-132">Standard C++ does not have the concept of a property so, in C++/WinRT, you call get and set functions.</span></span>

<span data-ttu-id="afd98-133">In den folgenden Beispielen sind **XboxUserId**, **UserState**, **PresenceDeviceRecords** und **Größe** alles Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="afd98-133">In the examples that follow, **XboxUserId**, **UserState**, **PresenceDeviceRecords**, and **Size** are all properties.</span></span>

### <a name="retrieving-a-value-from-a-property"></a><span data-ttu-id="afd98-134">Abrufen eines Werts aus einer Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="afd98-134">Retrieving a value from a property</span></span>
<span data-ttu-id="afd98-135">So erhalten Sie einen Eigenschaftswert in C++/CX.</span><span class="sxs-lookup"><span data-stu-id="afd98-135">Here's how you get a property value in C++/CX.</span></span>

```cpp
void Sample::LogPresenceRecord(PresenceRecord^ record)
{
    auto id = record->XboxUserId;
    auto state = record->UserState;
    auto size = record->PresenceDeviceRecords->Size;
}
```

<span data-ttu-id="afd98-136">Der entsprechende C++/WinRT-Quellcode ruft eine Funktion mit dem gleichen Namen wie die Eigenschaft auf, jedoch ohne Parameter.</span><span class="sxs-lookup"><span data-stu-id="afd98-136">The equivalent C++/WinRT source code calls a function with the same name as the property, but with no parameters.</span></span>

```cppwinrt
void Sample::LogPresenceRecord(PresenceRecord const& record)
{
    auto id = record.XboxUserId();
    auto state = record.UserState();
    auto size = record.PresenceDeviceRecords().Size();
}
```

<span data-ttu-id="afd98-137">Beachten Sie, dass die Funktion **PresenceDeviceRecords** ein Windows-Runtime-Objekt zurückgibt, das über eine **Size**-Funktion verfügt.</span><span class="sxs-lookup"><span data-stu-id="afd98-137">Note that the **PresenceDeviceRecords** function returns a Windows Runtime object that itself has a **Size** function.</span></span> <span data-ttu-id="afd98-138">Da es sich beim zurückgegebenen Objekt ebenfalls um einen C++/WinRT-projizierten Typ handelt, dereferenzieren wir, indem wir den Punktoperator zum Aufrufen von **Size** verwenden.</span><span class="sxs-lookup"><span data-stu-id="afd98-138">As the returned object is also a C++/WinRT projected type, we dereference using the dot operator to call **Size**.</span></span>

### <a name="setting-a-property-to-a-new-value"></a><span data-ttu-id="afd98-139">Festlegen einer Eigenschaft auf einen neuen Wert</span><span class="sxs-lookup"><span data-stu-id="afd98-139">Setting a property to a new value</span></span>
<span data-ttu-id="afd98-140">Beim Festlegen einer Eigenschaft auf einen neuen Wert wird ein ähnliches Muster angewandt.</span><span class="sxs-lookup"><span data-stu-id="afd98-140">Setting a property to a new value follows a similar pattern.</span></span> <span data-ttu-id="afd98-141">Zuerst in C++/CX.</span><span class="sxs-lookup"><span data-stu-id="afd98-141">First, in C++/CX.</span></span>

```cpp
record->UserState = newValue;
```

<span data-ttu-id="afd98-142">Um das Äquivalent in C++/WinRT zu tun, rufen Sie eine Funktion mit dem gleichen Namen wie die Eigenschaft auf und übergeben ein Argument.</span><span class="sxs-lookup"><span data-stu-id="afd98-142">To do the equivalent in C++/WinRT, you call a function with the same name as the property, and pass an argument.</span></span>

```cppwinrt
record.UserState(newValue);
```

## <a name="creating-an-instance-of-a-class"></a><span data-ttu-id="afd98-143">Erstellen einer Instanz einer Klasse</span><span class="sxs-lookup"><span data-stu-id="afd98-143">Creating an instance of a class</span></span>
<span data-ttu-id="afd98-144">Sie arbeiten mit einem C++/ CX-Objekt über einen Handle dafür (Hütchenverweis (\^)).</span><span class="sxs-lookup"><span data-stu-id="afd98-144">You work with a C++/CX object via a handle to it, commonly known as a hat (\^) reference.</span></span> <span data-ttu-id="afd98-145">Sie erstellen ein neues Objekt über das Schlüsselwort `ref new`, das wiederum [**RoActivateInstance**](https://msdn.microsoft.com/library/br224646) aufruft, um eine neue Instanz der Laufzeitklasse zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="afd98-145">You create a new object via the `ref new` keyword, which in turn calls [**RoActivateInstance**](https://msdn.microsoft.com/library/br224646) to activate a new instance of the runtime class.</span></span>

```cpp
using namespace Windows::Storage::Streams;

class Sample
{
private:
    Buffer^ m_gamerPicBuffer = ref new Buffer(MAX_IMAGE_SIZE);
};
```

<span data-ttu-id="afd98-146">Ein C++/WinRT-Objekt ist ein Wert. Folglich können Sie es auf dem Stapel oder als ein Feld eines Objekts zuweisen.</span><span class="sxs-lookup"><span data-stu-id="afd98-146">A C++/WinRT object is a value; so you can allocate it on the stack, or as a field of an object.</span></span> <span data-ttu-id="afd98-147">*Niemals* können Sie `ref new` (oder `new`) verwenden, um ein C++/WinRT-Objekt zuzuordnen.</span><span class="sxs-lookup"><span data-stu-id="afd98-147">You *never* use `ref new` (nor `new`) to allocate a C++/WinRT object.</span></span> <span data-ttu-id="afd98-148">Im Hintergrund wird dennoch **RoActivateInstance** aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="afd98-148">Behind the scenes, **RoActivateInstance** is still being called.</span></span>

```cppwinrt
using namespace winrt::Windows::Storage::Streams;

struct Sample
{
private:
    Buffer m_gamerPicBuffer{ MAX_IMAGE_SIZE };
};
```

<span data-ttu-id="afd98-149">Wenn eine Ressource aufwendig zu initialisieren ist, ist es üblich, deren Initialisierung zu verzögern, bis sie tatsächlich benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="afd98-149">If a resource is expensive to initialize, then it's common to delay initialization of it until it's actually needed.</span></span>

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

<span data-ttu-id="afd98-150">Der gleiche Code wird zu C++/WinRT portiert.</span><span class="sxs-lookup"><span data-stu-id="afd98-150">The same code ported to C++/WinRT.</span></span> <span data-ttu-id="afd98-151">Beachten Sie die Verwendung des Konstruktors `nullptr`.</span><span class="sxs-lookup"><span data-stu-id="afd98-151">Note the use of the `nullptr` constructor.</span></span> <span data-ttu-id="afd98-152">Weitere Informationen zu diesem Konstruktor finden Sie unter [Nutzen von APIs mit C++/WinRT](consume-apis.md).</span><span class="sxs-lookup"><span data-stu-id="afd98-152">For more info about that constructor, see [Consume APIs with C++/WinRT](consume-apis.md).</span></span>

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

## <a name="event-handling-with-a-delegate"></a><span data-ttu-id="afd98-153">Ereignisbehandlung mit einem Delegaten</span><span class="sxs-lookup"><span data-stu-id="afd98-153">Event-handling with a delegate</span></span>
<span data-ttu-id="afd98-154">Hier ist ein typisches Beispiel für die Behandlung eines Ereignisses in C++/CX unter Verwendung einer Lambda-Funktion als Delegaten.</span><span class="sxs-lookup"><span data-stu-id="afd98-154">Here's a typical example of handling an event in C++/CX, using a lambda function as a delegate in this case.</span></span>

```cpp
auto token = myButton->Click += ref new RoutedEventHandler([&](Platform::Object^ sender, RoutedEventArgs^ args)
{
    // Handle the event.
});
```

<span data-ttu-id="afd98-155">Dies ist das Äquivalent in C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="afd98-155">This is the equivalent in C++/WinRT.</span></span>

```cppwinrt
auto token = myButton().Click([&](IInspectable const& sender, RoutedEventArgs const& args)
{
    // Handle the event.
});
```

<span data-ttu-id="afd98-156">Anstelle einer Lambda-Funktion können Sie den Delegaten als eine freie Funktion oder als Pointer-to-Member-Funktion implementieren.</span><span class="sxs-lookup"><span data-stu-id="afd98-156">Instead of a lambda function, you can choose to implement your delegate as a free function, or as a pointer-to-member-function.</span></span> <span data-ttu-id="afd98-157">Weitere Informationen finden Sie unter [Verarbeiten von Ereignissen über Delegaten in C++/WinRT](handle-events.md).</span><span class="sxs-lookup"><span data-stu-id="afd98-157">For more info, see [Handle events by using delegates in C++/WinRT](handle-events.md).</span></span>

<span data-ttu-id="afd98-158">Wenn Sie von einer C++/CX-Codebasis portieren, wo Ereignisse und Delegate intern verwendet werden (nicht über Binärdateien), hilft Ihnen [**winrt::delegate**](/uwp/cpp-ref-for-winrt/delegate) beim Replizieren dieses Musters in C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="afd98-158">If you're porting from a C++/CX codebase where events and delegates are used internally (not across binaries), then [**winrt::delegate**](/uwp/cpp-ref-for-winrt/delegate) will help you to replicate that pattern in C++/WinRT.</span></span> <span data-ttu-id="afd98-159">Siehe auch [winrt::delegate&lt;... T&gt;](author-events.md#winrtdelegate-t).</span><span class="sxs-lookup"><span data-stu-id="afd98-159">Also see [winrt::delegate&lt;... T&gt;](author-events.md#winrtdelegate-t).</span></span>

## <a name="revoking-a-delegate"></a><span data-ttu-id="afd98-160">Widerrufen eines Delegaten</span><span class="sxs-lookup"><span data-stu-id="afd98-160">Revoking a delegate</span></span>
<span data-ttu-id="afd98-161">In C++/CX verwenden Sie den `-=`-Operator, um eine frühere Ereignisregistrierung zu widerrufen.</span><span class="sxs-lookup"><span data-stu-id="afd98-161">In C++/CX you use the `-=` operator to revoke a prior event registration.</span></span>

```cpp
myButton->Click -= token;
```

<span data-ttu-id="afd98-162">Dies ist das Äquivalent in C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="afd98-162">This is the equivalent in C++/WinRT.</span></span>

```cppwinrt
myButton().Click(token);
```

<span data-ttu-id="afd98-163">Weitere Informationen und Optionen finden Sie unter [Einen registrierten Delegaten widerrufen](handle-events.md#revoke-a-registered-delegate).</span><span class="sxs-lookup"><span data-stu-id="afd98-163">For more info and options, see [Revoke a registered delegate](handle-events.md#revoke-a-registered-delegate).</span></span>

## <a name="mapping-ccx-platform-types-to-cwinrt-types"></a><span data-ttu-id="afd98-164">Zuordnen von C++/CX-**Platform**-Typen zu C++/WinRT-Typen</span><span class="sxs-lookup"><span data-stu-id="afd98-164">Mapping C++/CX **Platform** types to C++/WinRT types</span></span>
<span data-ttu-id="afd98-165">C++/CX bietet verschiedene Datentypen im **Platform**-Namespace.</span><span class="sxs-lookup"><span data-stu-id="afd98-165">C++/CX provides several data types in the **Platform** namespace.</span></span> <span data-ttu-id="afd98-166">Diese Typen gehören nicht zum C++-Standard, daher können Sie sie nur verwenden, wenn Sie die Windows-Runtime-Spracherweiterungen aktivieren (Visual Studio-Projekteigenschaft **C/C++** > **Allgemein** > **Windows-Runtime-Erweiterung verwenden** > **Ja (/ZW)**).</span><span class="sxs-lookup"><span data-stu-id="afd98-166">These types are not standard C++, so you can only use them when you enable Windows Runtime language extensions (Visual Studio project property **C/C++** > **General** > **Consume Windows Runtime Extension** > **Yes (/ZW)**).</span></span> <span data-ttu-id="afd98-167">In der Tabelle unten finden Sie Informationen zum Portieren von **Platform**-Typen in ihre Entsprechungen in C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="afd98-167">The table below helps you port from **Platform** types to their equivalents in C++/WinRT.</span></span> <span data-ttu-id="afd98-168">Nachdem Sie dies erledigt haben, können Sie, da C++/WinRT zum C++-Standard gehört, die Option `/ZW` deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="afd98-168">Once you've done that, since C++/WinRT is standard C++, you can turn off the `/ZW` option.</span></span>

| <span data-ttu-id="afd98-169">C++/CX</span><span class="sxs-lookup"><span data-stu-id="afd98-169">C++/CX</span></span> | <span data-ttu-id="afd98-170">C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="afd98-170">C++/WinRT</span></span> |
| ---- | ---- |
| **<span data-ttu-id="afd98-171">Platform::Object\^</span><span class="sxs-lookup"><span data-stu-id="afd98-171">Platform::Object\^</span></span>** | **<span data-ttu-id="afd98-172">winrt::Windows::Foundation::IInspectable</span><span class="sxs-lookup"><span data-stu-id="afd98-172">winrt::Windows::Foundation::IInspectable</span></span>** |
| **<span data-ttu-id="afd98-173">Platform::String\^</span><span class="sxs-lookup"><span data-stu-id="afd98-173">Platform::String\^</span></span>** | [**<span data-ttu-id="afd98-174">winrt::hstring</span><span class="sxs-lookup"><span data-stu-id="afd98-174">winrt::hstring</span></span>**](/uwp/cpp-ref-for-winrt/hstring) |
| **<span data-ttu-id="afd98-175">Platform::Exception\^</span><span class="sxs-lookup"><span data-stu-id="afd98-175">Platform::Exception\^</span></span>** | [**<span data-ttu-id="afd98-176">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="afd98-176">winrt::hresult_error</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error) |
| **<span data-ttu-id="afd98-177">Platform::InvalidArgumentException\^</span><span class="sxs-lookup"><span data-stu-id="afd98-177">Platform::InvalidArgumentException\^</span></span>** | [**<span data-ttu-id="afd98-178">winrt::hresult_invalid_argument</span><span class="sxs-lookup"><span data-stu-id="afd98-178">winrt::hresult_invalid_argument</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-invalid-argument) |

### <a name="port-platformobject-to-winrtwindowsfoundationiinspectable"></a><span data-ttu-id="afd98-179">Portieren von **Platform::Object\^** nach **winrt::Windows::Foundation::IInspectable**</span><span class="sxs-lookup"><span data-stu-id="afd98-179">Port **Platform::Object\^** to **winrt::Windows::Foundation::IInspectable**</span></span>
<span data-ttu-id="afd98-180">Wie alle C++/WinRT-Typen ist **winrt::Windows::Foundation::IInspectable** ein Werttyp.</span><span class="sxs-lookup"><span data-stu-id="afd98-180">Like all C++/WinRT types, **winrt::Windows::Foundation::IInspectable** is a value type.</span></span> <span data-ttu-id="afd98-181">Hier erfahren Sie, wie Sie eine Variable dieses Typs auf null initialisieren.</span><span class="sxs-lookup"><span data-stu-id="afd98-181">Here's how you initialize a variable of that type to null.</span></span>

```cppwinrt
winrt::Windows::Foundation::IInspectable var{ nullptr };
```

### <a name="port-platformstring-to-winrthstring"></a><span data-ttu-id="afd98-182">Portieren von **Platform::String\^** nach **winrt::hstring**</span><span class="sxs-lookup"><span data-stu-id="afd98-182">Port **Platform::String\^** to **winrt::hstring**</span></span>
<span data-ttu-id="afd98-183">**Platform::String\^** ist das Äquivalent zum Windows-Runtime-HSTRING-ABI-Typ.</span><span class="sxs-lookup"><span data-stu-id="afd98-183">**Platform::String\^** is equivalent to the Windows Runtime HSTRING ABI type.</span></span> <span data-ttu-id="afd98-184">Für C++/WinRT ist die Entsprechung [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring).</span><span class="sxs-lookup"><span data-stu-id="afd98-184">For C++/WinRT, the equivalent is [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring).</span></span> <span data-ttu-id="afd98-185">Mit C++/WinRT können Sie aber Windows-Runtime-APIs mit Standard-C++ Wide-String-Typen wie **std::wstring** aufrufen und/oder Wide-String-Literale.</span><span class="sxs-lookup"><span data-stu-id="afd98-185">But with C++/WinRT, you can call Windows Runtime APIs using C++ Standard Library wide string types such as **std::wstring**, and/or wide string literals.</span></span> <span data-ttu-id="afd98-186">Weitere Informationen und Codebeispiele finden Sie unter [String-Verarbeitung in C++/WinRT](strings.md).</span><span class="sxs-lookup"><span data-stu-id="afd98-186">For more details, and code examples, see [String handling in C++/WinRT](strings.md).</span></span>

<span data-ttu-id="afd98-187">Mit C++/CX können Sie auf die Eigenschaft [**Platform::String::Data**](https://docs.microsoft.com/en-us/cpp/cppcx/platform-string-class#data) zugreifen, um die Zeichenfolge als **const wchar_t\***-Array im C-Stil abzurufen (z.B. zur Übergabe an **std::wcout**).</span><span class="sxs-lookup"><span data-stu-id="afd98-187">With C++/CX, you can access the [**Platform::String::Data**](https://docs.microsoft.com/en-us/cpp/cppcx/platform-string-class#data) property to retrieve the string as a C-style **const wchar_t\*** array (for example, to pass it to **std::wcout**).</span></span>

```C++
auto var = titleRecord->TitleName->Data();
```

<span data-ttu-id="afd98-188">Um das Gleiche mit C++ / WinRT zu tun, können Sie die Funktion [**hstring::c_str**](/uwp/api/windows.foundation.uri#hstringcstr-function) verwenden, um eine auf null beendete Zeichenfolgenversion im C-Stil abzurufen (wie von **std::wstring**).</span><span class="sxs-lookup"><span data-stu-id="afd98-188">To do the same with C++/WinRT, you can use the [**hstring::c_str**](/uwp/api/windows.foundation.uri#hstringcstr-function) function to get a null-terminated C-style string version, just as you can from **std::wstring**.</span></span>

```C++
auto var = titleRecord.TitleName().c_str();
```

<span data-ttu-id="afd98-189">Bei der Implementierung von APIs, die Zeichenfolgen übernehmen oder zurückgeben, ändern Sie in der Regel jeglichen C++/CX-Code, der **Platform::String\^** verwendet, um stattdessen **winrt::hstring** zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="afd98-189">When it comes to implementing APIs that take or return strings, you typically change any C++/CX code that uses **Platform::String\^** to use **winrt::hstring** instead.</span></span>

<span data-ttu-id="afd98-190">Hier ist ein Beispiel für eine C++/CX-API, die eine Zeichenfolge übernimmt.</span><span class="sxs-lookup"><span data-stu-id="afd98-190">Here's an example of a C++/CX API that takes a string.</span></span>

```cpp
void LogWrapLine(Platform::String^ str);
```

<span data-ttu-id="afd98-191">Für C++/WinRT könnten Sie diese API in [MIDL 3.0](/uwp/midl-3) wie folgt deklarieren.</span><span class="sxs-lookup"><span data-stu-id="afd98-191">For C++/WinRT you could declare that API in [MIDL 3.0](/uwp/midl-3) like this.</span></span>

```idl
// LogType.idl
void LogWrapLine(String str);
```

<span data-ttu-id="afd98-192">Die C++/WinRT-Toolkette generiert dann Quellcode für Sie, der wie folgt aussieht.</span><span class="sxs-lookup"><span data-stu-id="afd98-192">The C++/WinRT toolchain will then generate source code for you that looks like this.</span></span>

```cppwinrt
void LogWrapLine(winrt::hstring const& str);
```

### <a name="port-platformexception-to-winrthresulterror"></a><span data-ttu-id="afd98-193">Portieren von **Platform::Exception\^** nach **winrt::hresult_error**</span><span class="sxs-lookup"><span data-stu-id="afd98-193">Port **Platform::Exception\^** to **winrt::hresult_error**</span></span>
<span data-ttu-id="afd98-194">Der Typ **Platform::Exception\^** wird in C++/CX erzeugt, wenn eine Windows-Runtime-API ein Nicht-S\_OK HRESULT zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="afd98-194">The **Platform::Exception\^** type is produced in C++/CX when a Windows Runtime API returns a non S\_OK HRESULT.</span></span> <span data-ttu-id="afd98-195">Für C++/WinRT ist die Entsprechung [**winrt::hresult_error**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error).</span><span class="sxs-lookup"><span data-stu-id="afd98-195">The C++/WinRT equivalent is [**winrt::hresult_error**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error).</span></span>

<span data-ttu-id="afd98-196">Zum Portieren nach C++/WinRT ändern Sie jeglichen Code, der **Platform::Exception\^** verwendet, um stattdessen **winrt::hresult_error** zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="afd98-196">To port to C++/WinRT, change all code that uses **Platform::Exception\^** to use **winrt::hresult_error**.</span></span>

<span data-ttu-id="afd98-197">In C++/CX.</span><span class="sxs-lookup"><span data-stu-id="afd98-197">In C++/CX.</span></span>

```cpp
catch (Platform::Exception^ ex)
```

<span data-ttu-id="afd98-198">In C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="afd98-198">In C++/WinRT.</span></span>

```cppwinrt
catch (winrt::hresult_error const& ex)
```

<span data-ttu-id="afd98-199">C++/WinRT stellt diese Ausnahmeklassen bereit.</span><span class="sxs-lookup"><span data-stu-id="afd98-199">C++/WinRT provides these exception classes.</span></span>

| <span data-ttu-id="afd98-200">Ausnahmentyp</span><span class="sxs-lookup"><span data-stu-id="afd98-200">Exception type</span></span> | <span data-ttu-id="afd98-201">Basisklasse</span><span class="sxs-lookup"><span data-stu-id="afd98-201">Base class</span></span> | <span data-ttu-id="afd98-202">HRESULT</span><span class="sxs-lookup"><span data-stu-id="afd98-202">HRESULT</span></span> |
| ---- | ---- | ---- |
| [**<span data-ttu-id="afd98-203">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="afd98-203">winrt::hresult_error</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error) | | <span data-ttu-id="afd98-204">Aufrufen von [**hresult_error::to_abi**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error#hresulterrortoabi-function)</span><span class="sxs-lookup"><span data-stu-id="afd98-204">call [**hresult_error::to_abi**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error#hresulterrortoabi-function)</span></span> |
| [**<span data-ttu-id="afd98-205">winrt::hresult_access_denied</span><span class="sxs-lookup"><span data-stu-id="afd98-205">winrt::hresult_access_denied</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-access-denied) | **<span data-ttu-id="afd98-206">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="afd98-206">winrt::hresult_error</span></span>** | <span data-ttu-id="afd98-207">E_ACCESSDENIED</span><span class="sxs-lookup"><span data-stu-id="afd98-207">E_ACCESSDENIED</span></span> |
| [**<span data-ttu-id="afd98-208">winrt::hresult_canceled</span><span class="sxs-lookup"><span data-stu-id="afd98-208">winrt::hresult_canceled</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-canceled) | **<span data-ttu-id="afd98-209">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="afd98-209">winrt::hresult_error</span></span>** | <span data-ttu-id="afd98-210">ERROR_CANCELLED</span><span class="sxs-lookup"><span data-stu-id="afd98-210">ERROR_CANCELLED</span></span> |
| [**<span data-ttu-id="afd98-211">winrt::hresult_changed_state</span><span class="sxs-lookup"><span data-stu-id="afd98-211">winrt::hresult_changed_state</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-changed-state) | **<span data-ttu-id="afd98-212">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="afd98-212">winrt::hresult_error</span></span>** | <span data-ttu-id="afd98-213">E_CHANGED_STATE</span><span class="sxs-lookup"><span data-stu-id="afd98-213">E_CHANGED_STATE</span></span> |
| [**<span data-ttu-id="afd98-214">winrt::hresult_class_not_available</span><span class="sxs-lookup"><span data-stu-id="afd98-214">winrt::hresult_class_not_available</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-class-not-available) | **<span data-ttu-id="afd98-215">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="afd98-215">winrt::hresult_error</span></span>** | <span data-ttu-id="afd98-216">CLASS_E_CLASSNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="afd98-216">CLASS_E_CLASSNOTAVAILABLE</span></span> |
| [**<span data-ttu-id="afd98-217">winrt::hresult_illegal_delegate_assignment</span><span class="sxs-lookup"><span data-stu-id="afd98-217">winrt::hresult_illegal_delegate_assignment</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-illegal-delegate-assignment) | **<span data-ttu-id="afd98-218">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="afd98-218">winrt::hresult_error</span></span>** | <span data-ttu-id="afd98-219">E_ILLEGAL_DELEGATE_ASSIGNMENT</span><span class="sxs-lookup"><span data-stu-id="afd98-219">E_ILLEGAL_DELEGATE_ASSIGNMENT</span></span> |
| [**<span data-ttu-id="afd98-220">winrt::hresult_illegal_method_call</span><span class="sxs-lookup"><span data-stu-id="afd98-220">winrt::hresult_illegal_method_call</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-illegal-method-call) | **<span data-ttu-id="afd98-221">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="afd98-221">winrt::hresult_error</span></span>** | <span data-ttu-id="afd98-222">E_ILLEGAL_METHOD_CALL</span><span class="sxs-lookup"><span data-stu-id="afd98-222">E_ILLEGAL_METHOD_CALL</span></span> |
| [**<span data-ttu-id="afd98-223">winrt::hresult_illegal_state_change</span><span class="sxs-lookup"><span data-stu-id="afd98-223">winrt::hresult_illegal_state_change</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-illegal-state-change) | **<span data-ttu-id="afd98-224">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="afd98-224">winrt::hresult_error</span></span>** | <span data-ttu-id="afd98-225">E_ILLEGAL_STATE_CHANGE</span><span class="sxs-lookup"><span data-stu-id="afd98-225">E_ILLEGAL_STATE_CHANGE</span></span> |
| [**<span data-ttu-id="afd98-226">winrt::hresult_invalid_argument</span><span class="sxs-lookup"><span data-stu-id="afd98-226">winrt::hresult_invalid_argument</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-invalid-argument) | **<span data-ttu-id="afd98-227">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="afd98-227">winrt::hresult_error</span></span>** | <span data-ttu-id="afd98-228">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="afd98-228">E_INVALIDARG</span></span> |
| [**<span data-ttu-id="afd98-229">winrt::hresult_no_interface</span><span class="sxs-lookup"><span data-stu-id="afd98-229">winrt::hresult_no_interface</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-no-interface) | **<span data-ttu-id="afd98-230">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="afd98-230">winrt::hresult_error</span></span>** | <span data-ttu-id="afd98-231">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="afd98-231">E_NOINTERFACE</span></span> |
| [**<span data-ttu-id="afd98-232">winrt::hresult_not_implemented</span><span class="sxs-lookup"><span data-stu-id="afd98-232">winrt::hresult_not_implemented</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-not-implemented) | **<span data-ttu-id="afd98-233">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="afd98-233">winrt::hresult_error</span></span>** | <span data-ttu-id="afd98-234">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="afd98-234">E_NOTIMPL</span></span> |
| [**<span data-ttu-id="afd98-235">winrt::hresult_out_of_bounds</span><span class="sxs-lookup"><span data-stu-id="afd98-235">winrt::hresult_out_of_bounds</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-out-of-bounds) | **<span data-ttu-id="afd98-236">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="afd98-236">winrt::hresult_error</span></span>** | <span data-ttu-id="afd98-237">E_BOUNDS</span><span class="sxs-lookup"><span data-stu-id="afd98-237">E_BOUNDS</span></span> |
| [**<span data-ttu-id="afd98-238">winrt::hresult_wrong_thread</span><span class="sxs-lookup"><span data-stu-id="afd98-238">winrt::hresult_wrong_thread</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-wrong-thread) | **<span data-ttu-id="afd98-239">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="afd98-239">winrt::hresult_error</span></span>** | <span data-ttu-id="afd98-240">RPC_E_WRONG_THREAD</span><span class="sxs-lookup"><span data-stu-id="afd98-240">RPC_E_WRONG_THREAD</span></span> |

<span data-ttu-id="afd98-241">Beachten Sie, dass jede Klasse (über die **hresult_error** -Basisklasse) eine [**to_abi**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error#hresulterrortoabi-function)-Funktion bereitstellt, die das HRESULT für den Fehler zurückgibt, sowie eine [**message**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error#hresulterrormessage-function)-Funktion, die die Darstellung der Zeichenfolge dieses HRESULT zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="afd98-241">Note that each class (via the **hresult_error** base class) provides a [**to_abi**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error#hresulterrortoabi-function) function, which returns the HRESULT of the error, and a [**message**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error#hresulterrormessage-function) function, which returns the string representation of that HRESULT.</span></span>

<span data-ttu-id="afd98-242">Hier ist ein Beispiel für das Auslösen einer Ausnahme in C++/CX.</span><span class="sxs-lookup"><span data-stu-id="afd98-242">Here's an example of throwing an exception in C++/CX.</span></span>

```cpp
throw ref new Platform::InvalidArgumentException(L"A valid User is required");
```

<span data-ttu-id="afd98-243">Und das Äquivalent in C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="afd98-243">And the equivalent in C++/WinRT.</span></span>

```cppwinrt
throw winrt::hresult_invalid_argument{ L"A valid User is required" };
```

## <a name="important-apis"></a><span data-ttu-id="afd98-244">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="afd98-244">Important APIs</span></span>
* [<span data-ttu-id="afd98-245">winrt::delegate-Strukturvorlage</span><span class="sxs-lookup"><span data-stu-id="afd98-245">winrt::delegate struct template</span></span>](/uwp/cpp-ref-for-winrt/delegate)
* [<span data-ttu-id="afd98-246">winrt::hresult_error-Struktur</span><span class="sxs-lookup"><span data-stu-id="afd98-246">winrt::hresult_error struct</span></span>](/uwp/cpp-ref-for-winrt/error-handling/hresult-error)
* [<span data-ttu-id="afd98-247">winrt::hstring-Struktur</span><span class="sxs-lookup"><span data-stu-id="afd98-247">winrt::hstring struct</span></span>](/uwp/cpp-ref-for-winrt/hstring)
* [<span data-ttu-id="afd98-248">winrt-Namespace</span><span class="sxs-lookup"><span data-stu-id="afd98-248">winrt namespace</span></span>](/uwp/cpp-ref-for-winrt/winrt)

## <a name="related-topics"></a><span data-ttu-id="afd98-249">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="afd98-249">Related topics</span></span>
* [<span data-ttu-id="afd98-250">C++/CX</span><span class="sxs-lookup"><span data-stu-id="afd98-250">C++/CX</span></span>](/cpp/cppcx/visual-c-language-reference-c-cx)
* [<span data-ttu-id="afd98-251">Erstellen von Ereignissen mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="afd98-251">Author events in C++/WinRT</span></span>](author-events.md)
* [<span data-ttu-id="afd98-252">Parallelität und asynchrone Vorgänge mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="afd98-252">Concurrency and asynchronous operations with C++/WinRT</span></span>](concurrency.md)
* [<span data-ttu-id="afd98-253">Verwenden von APIs mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="afd98-253">Consume APIs with C++/WinRT</span></span>](consume-apis.md)
* [<span data-ttu-id="afd98-254">Verarbeiten von Ereignissen über Delegaten in C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="afd98-254">Handle events by using delegates in C++/WinRT</span></span>](handle-events.md)
* [<span data-ttu-id="afd98-255">Microsoft Interface Definition Language3.0– Referenz</span><span class="sxs-lookup"><span data-stu-id="afd98-255">Microsoft Interface Definition Language 3.0 reference</span></span>](/uwp/midl-3)
* [<span data-ttu-id="afd98-256">Wechsel zu C++/WinRT von WRL</span><span class="sxs-lookup"><span data-stu-id="afd98-256">Move to C++/WinRT from WRL</span></span>](move-to-winrt-from-wrl.md)
* [<span data-ttu-id="afd98-257">String-Verarbeitung in C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="afd98-257">String handling in C++/WinRT</span></span>](strings.md)
