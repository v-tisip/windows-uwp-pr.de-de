---
description: In diesem Thema wird gezeigt, wie Sie C++/CX-Code zum entsprechenden Äquivalent in C++/WinRT portieren.
title: Wechsel zu C++/WinRT von C++/CX
ms.date: 01/17/2019
ms.topic: article
keywords: windows 10, uwp, standard, c++, cpp, winrt, projizierung, portieren, migrieren, C++/CX
ms.localizationpriority: medium
ms.openlocfilehash: 39f60576962d9e69d8ec7ba80918fdbdfe96f070
ms.sourcegitcommit: 9b0f9c8854277d2e786e9294af3a2b559aa457a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/23/2019
ms.locfileid: "9099317"
---
# <a name="move-to-cwinrt-from-ccx"></a><span data-ttu-id="11e37-104">C++/CX zu C++/WinRT wechseln</span><span class="sxs-lookup"><span data-stu-id="11e37-104">Move to C++/WinRT from C++/CX</span></span>

<span data-ttu-id="11e37-105">Dieses Thema zeigt, wie Sie den Code im Anschluss eine [C++ / CX](/cpp/cppcx/visual-c-language-reference-c-cx) Projekt zum entsprechenden Äquivalent in [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).</span><span class="sxs-lookup"><span data-stu-id="11e37-105">This topic shows how to port the code in a [C++/CX](/cpp/cppcx/visual-c-language-reference-c-cx) project to its equivalent in [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).</span></span>

## <a name="porting-strategies"></a><span data-ttu-id="11e37-106">Portieren von Strategien</span><span class="sxs-lookup"><span data-stu-id="11e37-106">Porting strategies</span></span>

<span data-ttu-id="11e37-107">Wenn Sie Ihre C++ nach und nach portieren möchten / CX-Code in C++ / WinRT, können Sie.</span><span class="sxs-lookup"><span data-stu-id="11e37-107">If you want to gradually port your C++/CX code to C++/WinRT, then you can.</span></span> <span data-ttu-id="11e37-108">C++ / CX- und C++ / WinRT-Code kann im selben Projekt, mit Ausnahme der XAML-Compiler-Unterstützung und der Windows-Runtime-Komponenten vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="11e37-108">C++/CX and C++/WinRT code can coexist in the same project, with the exceptions of XAML compiler support and Windows Runtime Components.</span></span> <span data-ttu-id="11e37-109">Für diese zwei Ausnahmen, müssen Sie in der Zielgruppe entweder C++ / CX oder C++ / WinRT im selben Projekt.</span><span class="sxs-lookup"><span data-stu-id="11e37-109">For those two exceptions, you'll need to target either C++/CX or C++/WinRT within the same project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="11e37-110">Wenn Ihr Projekt eine XAML-Anwendung erstellt wird, dann einen Workflow, die wir empfehlen wird zuerst ein neues Projekt in Visual Studio mithilfe eines C++ erstellen / WinRT-Projektvorlagen (finden Sie unter [Visual Studio-Unterstützung für C++ / WinRT](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-xaml-the-vsix-extension-and-the-nuget-package)).</span><span class="sxs-lookup"><span data-stu-id="11e37-110">If your project builds a XAML application, then one workflow that we recommend is to first create a new project in Visual Studio using one of the C++/WinRT project templates (see [Visual Studio support for C++/WinRT](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-xaml-the-vsix-extension-and-the-nuget-package)).</span></span> <span data-ttu-id="11e37-111">Starten Sie anschließend das Kopieren Source Code und Markup über von C++ / CX-Projekt.</span><span class="sxs-lookup"><span data-stu-id="11e37-111">Then, start copying source code and markup over from the C++/CX project.</span></span> <span data-ttu-id="11e37-112">Sie können neue XAML-Seiten mit **Projekt**hinzufügen \> **Neues Element hinzufügen**  \>  **Visual C++** > **leere Seite (C++ / WinRT)**.</span><span class="sxs-lookup"><span data-stu-id="11e37-112">You can add new XAML pages with **Project** \> **Add New Item...** \> **Visual C++** > **Blank Page (C++/WinRT)**.</span></span>
>
> <span data-ttu-id="11e37-113">Alternativ können Sie eine Komponente für Windows-Runtime-Faktor-Code aus dem XAML-C++ / CX projizieren, wie Sie es portieren.</span><span class="sxs-lookup"><span data-stu-id="11e37-113">Alternatively, you can use a Windows Runtime Component to factor code out of the XAML C++/CX project as you port it.</span></span> <span data-ttu-id="11e37-114">Entweder bewegen Sie so viele C++ / CX-code können Sie in einer Komponente, und klicken Sie dann das XAML-Projekt in C++ / WinRT.</span><span class="sxs-lookup"><span data-stu-id="11e37-114">Either move as much C++/CX code as you can into a component, and then change the XAML project to C++/WinRT.</span></span> <span data-ttu-id="11e37-115">Oder lassen Sie andernfalls das XAML-Projekt als C++ / CX, erstellen Sie eine neue C++ / WinRT-Komponente, und beginnen Sie Portieren von C++ / CX-Code aus dem XAML-Projekt und in der Komponente.</span><span class="sxs-lookup"><span data-stu-id="11e37-115">Or else leave the XAML project as C++/CX, create a new C++/WinRT component, and begin porting C++/CX code out of the XAML project and into the component.</span></span> <span data-ttu-id="11e37-116">Sie haben können auch eine C++ / CX-Komponentenprojekt zusammen mit C++ / WinRT-Komponentenprojekt in der gleichen Projektmappe, verweisen auf beide aus Ihrem Anwendungsprojekt und nach und nach auf einem anderen port.</span><span class="sxs-lookup"><span data-stu-id="11e37-116">You could also have a C++/CX component project alongside a C++/WinRT component project within the same solution, reference both of them from your application project, and gradually port from one to the other.</span></span> <span data-ttu-id="11e37-117">Finden Sie unter [Interoperabilität zwischen C++ / WinRT und C++ / CX](interop-winrt-cx.md) für Weitere Informationen zur Verwendung die beiden sprachprojektionen im selben Projekt.</span><span class="sxs-lookup"><span data-stu-id="11e37-117">See [Interop between C++/WinRT and C++/CX](interop-winrt-cx.md) for more details on using the two language projections in the same project.</span></span>

> [!NOTE]
> <span data-ttu-id="11e37-118">Sowohl [C++/CX ](/cpp/cppcx/visual-c-language-reference-c-cx) als auch das Windows SDK deklarieren Typen im Root-Namespace **Windows**.</span><span class="sxs-lookup"><span data-stu-id="11e37-118">Both [C++/CX](/cpp/cppcx/visual-c-language-reference-c-cx) and the Windows SDK declare types in the root namespace **Windows**.</span></span> <span data-ttu-id="11e37-119">Ein Windows-Typ, der in C++/WinRT projiziert wird, verfügt über den gleichen vollqualifizierten Namen wie der Windows-Typ, befindet sich aber im C++/**winrt**-Namespace.</span><span class="sxs-lookup"><span data-stu-id="11e37-119">A Windows type projected into C++/WinRT has the same fully-qualified name as the Windows type, but it's placed in the C++ **winrt** namespace.</span></span> <span data-ttu-id="11e37-120">Diese unterschiedlichen Namespaces ermöglichen die Portierung von C++/CX nach C++/WinRT in Ihrem eigenen Tempo.</span><span class="sxs-lookup"><span data-stu-id="11e37-120">These distinct namespaces let you port from C++/CX to C++/WinRT at your own pace.</span></span>

<span data-ttu-id="11e37-121">Angesichts der oben genannten Ausnahmen, das erste Schritt beim Portieren eine C++ / CX-Projekts zu C++ / WinRT ist C++ manuell hinzufügen / WinRT-Unterstützung es (finden Sie unter [Visual Studio-Unterstützung für C++ / WinRT](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-xaml-the-vsix-extension-and-the-nuget-package)).</span><span class="sxs-lookup"><span data-stu-id="11e37-121">Bearing in mind the exceptions mentioned above, the first step in porting a C++/CX project to C++/WinRT is to manually add C++/WinRT support to it (see [Visual Studio support for C++/WinRT](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-xaml-the-vsix-extension-and-the-nuget-package)).</span></span> <span data-ttu-id="11e37-122">Installieren Sie dazu das [Microsoft.Windows.CppWinRT NuGet-Paket](https://www.nuget.org/packages/Microsoft.Windows.CppWinRT/) in Ihr Projekt ein.</span><span class="sxs-lookup"><span data-stu-id="11e37-122">To do that, install the [Microsoft.Windows.CppWinRT NuGet package](https://www.nuget.org/packages/Microsoft.Windows.CppWinRT/) into your project.</span></span> <span data-ttu-id="11e37-123">Öffnen des Projekts in Visual Studio, klicken Sie auf **Projekt** \> **NuGet-Pakete verwalten...**  \>  **Durchsuchen**, geben Sie oder fügen Sie **Microsoft.Windows.CppWinRT** in das Suchfeld ein, wählen Sie das Element in den Suchergebnissen übergehen, und dann auf **Installieren** , um das Paket für das Projekt zu installieren.</span><span class="sxs-lookup"><span data-stu-id="11e37-123">Open the project in Visual Studio, click **Project** \> **Manage NuGet Packages...** \> **Browse**, type or paste **Microsoft.Windows.CppWinRT** in the search box, select the item in search results, and then click **Install** to install the package for that project.</span></span> <span data-ttu-id="11e37-124">Eine Auswirkung dieser Änderung ist, dass die Unterstützung für C++/CX im Projekt deaktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="11e37-124">One effect of that change is that support for C++/CX is turned off in the project.</span></span> <span data-ttu-id="11e37-125">Es ist sinnvoll, lassen Sie Unterstützung deaktiviert, so dass Build Nachrichten Sie suchen (und Port) unterstützen alle Ihre Abhängigkeiten von C++ / CX, oder Sie können Unterstützung wieder aktivieren (in den Projekteigenschaften, **C/C++-** \> **Allgemeine** \> **verbrauchen Windows-Runtime Erweiterung** \> **Ja (/ Zw)**), und nach und nach portieren.</span><span class="sxs-lookup"><span data-stu-id="11e37-125">It's a good idea to leave support turned off so that build messages help you find (and port) all of your dependencies on C++/CX, or you can turn support back on (in project properties, **C/C++** \> **General** \> **Consume Windows Runtime Extension** \> **Yes (/ZW)**), and port gradually.</span></span>

<span data-ttu-id="11e37-126">Stellen Sie sicher, **Allgemeine**Projekteigenschaft \> **Zielplattformversion** mit 10.0.17134.0 (Windows 10, Version 1803) festgelegt ist oder größer.</span><span class="sxs-lookup"><span data-stu-id="11e37-126">Ensure that project property **General** \> **Target Platform Version** is set to 10.0.17134.0 (Windows 10, version 1803) or greater.</span></span>

<span data-ttu-id="11e37-127">Fügen Sie Ihrer vorkompilierten Headerdatei (in der Regel `pch.h`) `winrt/base.h` hinzu.</span><span class="sxs-lookup"><span data-stu-id="11e37-127">In your precompiled header file (usually `pch.h`), include `winrt/base.h`.</span></span>

```cppwinrt
#include <winrt/base.h>
```

<span data-ttu-id="11e37-128">Wenn Sie alle C++/WinRT-projizierten Windows-API-Header hinzufügen (z.B. `winrt/Windows.Foundation.h`), müssen Sie so nicht explizit `winrt/base.h` einschließen, da dies automatisch erfolgt.</span><span class="sxs-lookup"><span data-stu-id="11e37-128">If you include any C++/WinRT projected Windows API headers (for example, `winrt/Windows.Foundation.h`), then you don't need to explicitly include `winrt/base.h` like this because it will be included automatically for you.</span></span>

<span data-ttu-id="11e37-129">Wenn Ihr Projekt zudem Typen der [C++-Vorlagenbibliothek für Windows-Runtime (WRL)](/cpp/windows/windows-runtime-cpp-template-library-wrl) verwendet, lesen Sie bitte [Wechsel zu C++/WinRT von WRL](move-to-winrt-from-wrl.md).</span><span class="sxs-lookup"><span data-stu-id="11e37-129">If your project is also using [Windows Runtime C++ Template Library (WRL)](/cpp/windows/windows-runtime-cpp-template-library-wrl) types, then see [Move to C++/WinRT from WRL](move-to-winrt-from-wrl.md).</span></span>

## <a name="parameter-passing"></a><span data-ttu-id="11e37-130">Parameterübergabe</span><span class="sxs-lookup"><span data-stu-id="11e37-130">Parameter-passing</span></span>
<span data-ttu-id="11e37-131">Beim Schreiben von C++/CX-Quellcode übergeben Sie C++/CX-Typen als Funktionsparameter wie Hütchenverweise (\^).</span><span class="sxs-lookup"><span data-stu-id="11e37-131">When writing C++/CX source code, you pass C++/CX types as function parameters as hat (\^) references.</span></span>

```cppcx
void LogPresenceRecord(PresenceRecord^ record);
```

<span data-ttu-id="11e37-132">In C++/WinRT sollten Sie für synchrone Funktionen standardmäßig `const&`-Parameter verwenden.</span><span class="sxs-lookup"><span data-stu-id="11e37-132">In C++/WinRT, for synchronous functions, you should use `const&` parameters by default.</span></span> <span data-ttu-id="11e37-133">Dadurch werden Kopien und unnötiger Zusatzaufwand vermieden.</span><span class="sxs-lookup"><span data-stu-id="11e37-133">That will avoid copies and interlocked overhead.</span></span> <span data-ttu-id="11e37-134">Ihre Coroutinen sollten aber Pass-by-Value verwenden, um sicherzustellen, dass sie nach Wert erfassen, und um Probleme mit der Lebensdauer zu vermeiden (weitere Informationen finden Sie unter [Parallelität und asynchrone Vorgänge mit C++/WinRT](concurrency.md)).</span><span class="sxs-lookup"><span data-stu-id="11e37-134">But your coroutines should use pass-by-value to ensure that they capture by value and avoid lifetime issues (for more details, see [Concurrency and asynchronous operations with C++/WinRT](concurrency.md)).</span></span>

```cppwinrt
void LogPresenceRecord(PresenceRecord const& record);
IASyncAction LogPresenceRecordAsync(PresenceRecord const record);
```

<span data-ttu-id="11e37-135">Ein C++/WinRT-Objekt ist im Grunde genommen ein Wert, der einen Schnittstellenzeiger zum zugrunde liegenden Windows-Runtime-Objekt enthält.</span><span class="sxs-lookup"><span data-stu-id="11e37-135">A C++/WinRT object is fundamentally a value that holds an interface pointer to the backing Windows Runtime object.</span></span> <span data-ttu-id="11e37-136">Beim Kopieren eines C++/WinRT-Objekts kopiert der Compiler den gekapselten Schnittstellenzeiger, wodurch sich sein Verweiszähler erhöht.</span><span class="sxs-lookup"><span data-stu-id="11e37-136">When you copy a C++/WinRT object, the compiler copies the encapsulated interface pointer, incrementing its reference count.</span></span> <span data-ttu-id="11e37-137">Eine Zerstörung der Kopie beinhaltet, dass der Verweiszähler verringert wird.</span><span class="sxs-lookup"><span data-stu-id="11e37-137">Eventual destruction of the copy involves decrementing the reference count.</span></span> <span data-ttu-id="11e37-138">Daher wird Aufwand einer Kopie nur bei Bedarf verursacht.</span><span class="sxs-lookup"><span data-stu-id="11e37-138">So, only incur the overhead of a copy when necessary.</span></span>

## <a name="variable-and-field-references"></a><span data-ttu-id="11e37-139">Variablen und Feldverweise</span><span class="sxs-lookup"><span data-stu-id="11e37-139">Variable and field references</span></span>
<span data-ttu-id="11e37-140">Beim Schreiben von C++/CX-Quellcode verwenden Sie Hütchenvariablen (\^) zum Verweisen auf Windows-Runtime-Objekte sowie den Pfeiloperator (-&gt;), um den Verweis einer Hütchenvariable aufzuheben.</span><span class="sxs-lookup"><span data-stu-id="11e37-140">When writing C++/CX source code, you use hat (\^) variables to reference Windows Runtime objects, and the arrow (-&gt;) operator to dereference a hat variable.</span></span>

```cppcx
IVectorView<User^>^ userList = User::Users;

if (userList != nullptr)
{
    for (UINT32 iUser = 0; iUser < userList->Size; ++iUser)
    ...
```

<span data-ttu-id="11e37-141">Beim Portieren in den entsprechenden C++ / WinRT-Code können Sie enorm abrufen, indem die hütchen entfernt, und ändern den Pfeiloperator (-&gt;) in den Punktoperator (.).</span><span class="sxs-lookup"><span data-stu-id="11e37-141">When porting to the equivalent C++/WinRT code, you can get a long way by removing the hats, and changing the arrow operator (-&gt;) to the dot operator (.).</span></span> <span data-ttu-id="11e37-142">C++ / WinRT-projizierte Typen Werte und keine Zeiger sind.</span><span class="sxs-lookup"><span data-stu-id="11e37-142">C++/WinRT projected types are values, and not pointers.</span></span>

```cppwinrt
IVectorView<User> userList = User::Users();

if (userList != nullptr)
{
    for (UINT32 iUser = 0; iUser < userList.Size(); ++iUser)
    ...
```

<span data-ttu-id="11e37-143">Der Standardkonstruktor für eine C++ / CX Hat Zeiger auf null initialisiert.</span><span class="sxs-lookup"><span data-stu-id="11e37-143">The default constructor for a C++/CX hat pointer initializes it to null.</span></span> <span data-ttu-id="11e37-144">Nachfolgend finden Sie eine C++ / CX-Codebeispiel in der erstellen wir eine Variable oder ein Feld den richtigen Typ, sondern eines, das nicht initialisiert wurde.</span><span class="sxs-lookup"><span data-stu-id="11e37-144">Here's a C++/CX code example in which we create a variable/field of the correct type, but one that's uninitialized.</span></span> <span data-ttu-id="11e37-145">Anders ausgedrückt, bezieht es zunächst einen **TextBlock**sich nicht auf; Wir beabsichtigen, einen Verweis später zuweisen.</span><span class="sxs-lookup"><span data-stu-id="11e37-145">In other words, it doesn't initially refer to a **TextBlock**; we intend to assign a reference later.</span></span>

```cppcx
TextBlock^ textBlock;

class MyClass
{
    TextBlock^ textBlock;
};
```

<span data-ttu-id="11e37-146">Für das Äquivalent in C++ / WinRT, siehe [verzögerte Initialisierung](consume-apis.md#delayed-initialization).</span><span class="sxs-lookup"><span data-stu-id="11e37-146">For the equivalent in C++/WinRT, see [Delayed initialization](consume-apis.md#delayed-initialization).</span></span>

## <a name="properties"></a><span data-ttu-id="11e37-147">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="11e37-147">Properties</span></span>
<span data-ttu-id="11e37-148">Die C++/CX-Spracherweiterungen beinhalten das Konzept von Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="11e37-148">The C++/CX language extensions include the concept of properties.</span></span> <span data-ttu-id="11e37-149">Beim Schreiben von C++/CX-Quellcode können Sie auf eine Eigenschaft zugreifen, als wäre sie ein Feld.</span><span class="sxs-lookup"><span data-stu-id="11e37-149">When writing C++/CX source code, you can access a property as if it were a field.</span></span> <span data-ttu-id="11e37-150">Der C++-Standardcode verfügt nicht über das Konzept einer Eigenschaft, folglich rufen Sie in C++/WinRT Get- und Set-Funktionen auf.</span><span class="sxs-lookup"><span data-stu-id="11e37-150">Standard C++ does not have the concept of a property so, in C++/WinRT, you call get and set functions.</span></span>

<span data-ttu-id="11e37-151">In den folgenden Beispielen sind **XboxUserId**, **UserState**, **PresenceDeviceRecords** und **Größe** alles Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="11e37-151">In the examples that follow, **XboxUserId**, **UserState**, **PresenceDeviceRecords**, and **Size** are all properties.</span></span>

### <a name="retrieving-a-value-from-a-property"></a><span data-ttu-id="11e37-152">Abrufen eines Werts aus einer Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="11e37-152">Retrieving a value from a property</span></span>
<span data-ttu-id="11e37-153">So erhalten Sie einen Eigenschaftswert in C++/CX.</span><span class="sxs-lookup"><span data-stu-id="11e37-153">Here's how you get a property value in C++/CX.</span></span>

```cppcx
void Sample::LogPresenceRecord(PresenceRecord^ record)
{
    auto id = record->XboxUserId;
    auto state = record->UserState;
    auto size = record->PresenceDeviceRecords->Size;
}
```

<span data-ttu-id="11e37-154">Der entsprechende C++/WinRT-Quellcode ruft eine Funktion mit dem gleichen Namen wie die Eigenschaft auf, jedoch ohne Parameter.</span><span class="sxs-lookup"><span data-stu-id="11e37-154">The equivalent C++/WinRT source code calls a function with the same name as the property, but with no parameters.</span></span>

```cppwinrt
void Sample::LogPresenceRecord(PresenceRecord const& record)
{
    auto id = record.XboxUserId();
    auto state = record.UserState();
    auto size = record.PresenceDeviceRecords().Size();
}
```

<span data-ttu-id="11e37-155">Beachten Sie, dass die Funktion **PresenceDeviceRecords** ein Windows-Runtime-Objekt zurückgibt, das über eine **Size**-Funktion verfügt.</span><span class="sxs-lookup"><span data-stu-id="11e37-155">Note that the **PresenceDeviceRecords** function returns a Windows Runtime object that itself has a **Size** function.</span></span> <span data-ttu-id="11e37-156">Da es sich beim zurückgegebenen Objekt ebenfalls um einen C++/WinRT-projizierten Typ handelt, dereferenzieren wir, indem wir den Punktoperator zum Aufrufen von **Size** verwenden.</span><span class="sxs-lookup"><span data-stu-id="11e37-156">As the returned object is also a C++/WinRT projected type, we dereference using the dot operator to call **Size**.</span></span>

### <a name="setting-a-property-to-a-new-value"></a><span data-ttu-id="11e37-157">Festlegen einer Eigenschaft auf einen neuen Wert</span><span class="sxs-lookup"><span data-stu-id="11e37-157">Setting a property to a new value</span></span>
<span data-ttu-id="11e37-158">Beim Festlegen einer Eigenschaft auf einen neuen Wert wird ein ähnliches Muster angewandt.</span><span class="sxs-lookup"><span data-stu-id="11e37-158">Setting a property to a new value follows a similar pattern.</span></span> <span data-ttu-id="11e37-159">Zuerst in C++/CX.</span><span class="sxs-lookup"><span data-stu-id="11e37-159">First, in C++/CX.</span></span>

```cppcx
record->UserState = newValue;
```

<span data-ttu-id="11e37-160">Um das Äquivalent in C++/WinRT zu tun, rufen Sie eine Funktion mit dem gleichen Namen wie die Eigenschaft auf und übergeben ein Argument.</span><span class="sxs-lookup"><span data-stu-id="11e37-160">To do the equivalent in C++/WinRT, you call a function with the same name as the property, and pass an argument.</span></span>

```cppwinrt
record.UserState(newValue);
```

## <a name="creating-an-instance-of-a-class"></a><span data-ttu-id="11e37-161">Erstellen einer Instanz einer Klasse</span><span class="sxs-lookup"><span data-stu-id="11e37-161">Creating an instance of a class</span></span>
<span data-ttu-id="11e37-162">Sie arbeiten mit einem C++/ CX-Objekt über einen Handle dafür (Hütchenverweis (\^)).</span><span class="sxs-lookup"><span data-stu-id="11e37-162">You work with a C++/CX object via a handle to it, commonly known as a hat (\^) reference.</span></span> <span data-ttu-id="11e37-163">Sie erstellen ein neues Objekt über das Schlüsselwort `ref new`, das wiederum [**RoActivateInstance**](https://msdn.microsoft.com/library/br224646) aufruft, um eine neue Instanz der Laufzeitklasse zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="11e37-163">You create a new object via the `ref new` keyword, which in turn calls [**RoActivateInstance**](https://msdn.microsoft.com/library/br224646) to activate a new instance of the runtime class.</span></span>

```cppcx
using namespace Windows::Storage::Streams;

class Sample
{
private:
    Buffer^ m_gamerPicBuffer = ref new Buffer(MAX_IMAGE_SIZE);
};
```

<span data-ttu-id="11e37-164">Ein C++/WinRT-Objekt ist ein Wert. Folglich können Sie es auf dem Stapel oder als ein Feld eines Objekts zuweisen.</span><span class="sxs-lookup"><span data-stu-id="11e37-164">A C++/WinRT object is a value; so you can allocate it on the stack, or as a field of an object.</span></span> <span data-ttu-id="11e37-165">*Niemals* können Sie `ref new` (oder `new`) verwenden, um ein C++/WinRT-Objekt zuzuordnen.</span><span class="sxs-lookup"><span data-stu-id="11e37-165">You *never* use `ref new` (nor `new`) to allocate a C++/WinRT object.</span></span> <span data-ttu-id="11e37-166">Im Hintergrund wird dennoch **RoActivateInstance** aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="11e37-166">Behind the scenes, **RoActivateInstance** is still being called.</span></span>

```cppwinrt
using namespace winrt::Windows::Storage::Streams;

struct Sample
{
private:
    Buffer m_gamerPicBuffer{ MAX_IMAGE_SIZE };
};
```

<span data-ttu-id="11e37-167">Wenn eine Ressource aufwendig zu initialisieren ist, ist es üblich, deren Initialisierung zu verzögern, bis sie tatsächlich benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="11e37-167">If a resource is expensive to initialize, then it's common to delay initialization of it until it's actually needed.</span></span>

```cppcx
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

<span data-ttu-id="11e37-168">Der gleiche Code wird zu C++/WinRT portiert.</span><span class="sxs-lookup"><span data-stu-id="11e37-168">The same code ported to C++/WinRT.</span></span> <span data-ttu-id="11e37-169">Beachten Sie die Verwendung des Konstruktors `nullptr`.</span><span class="sxs-lookup"><span data-stu-id="11e37-169">Note the use of the `nullptr` constructor.</span></span> <span data-ttu-id="11e37-170">Weitere Informationen zu diesem Konstruktor finden Sie unter [Nutzen von APIs mit C++/WinRT](consume-apis.md).</span><span class="sxs-lookup"><span data-stu-id="11e37-170">For more info about that constructor, see [Consume APIs with C++/WinRT](consume-apis.md).</span></span>

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

## <a name="converting-from-a-base-runtime-class-to-a-derived-one"></a><span data-ttu-id="11e37-171">Konvertieren von einer Basisklasse Laufzeitklasse in einen abgeleiteten</span><span class="sxs-lookup"><span data-stu-id="11e37-171">Converting from a base runtime class to a derived one</span></span>
<span data-ttu-id="11e37-172">Es ist üblich, eine Referenz-zu-Base verfügen, die Sie wissen, dass auf ein Objekt eines abgeleiteten Typs verweist.</span><span class="sxs-lookup"><span data-stu-id="11e37-172">It's common to have a reference-to-base that you know refers to an object of a derived type.</span></span> <span data-ttu-id="11e37-173">In C++ / CX verwenden Sie `dynamic_cast` auf eine *Umwandlung* der Referenz-Basis in eine Referenz--abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="11e37-173">In C++/CX, you use `dynamic_cast` to *cast* the reference-to-base into a reference-to-derived.</span></span> <span data-ttu-id="11e37-174">Die `dynamic_cast` ist wirklich nur ein ausgeblendeter Aufruf von [**QueryInterface**](https://msdn.microsoft.com/library/windows/desktop/ms682521).</span><span class="sxs-lookup"><span data-stu-id="11e37-174">The `dynamic_cast` is really just a hidden call to [**QueryInterface**](https://msdn.microsoft.com/library/windows/desktop/ms682521).</span></span> <span data-ttu-id="11e37-175">Hier ist ein typisches Beispiel&mdash;Sie ein Abhängigkeit geänderter Eigenschaft-Ereignis behandelt, und Sie **DependencyObject** zurück in den tatsächlichen Typ umgewandelt werden, die die Abhängigkeitseigenschaft besitzt möchten.</span><span class="sxs-lookup"><span data-stu-id="11e37-175">Here's a typical example&mdash;you're handling a dependency property changed event, and you want to cast from **DependencyObject** back to the actual type that owns the dependency property.</span></span>

```cppcx
void BgLabelControl::OnLabelChanged(Windows::UI::Xaml::DependencyObject^ d, Windows::UI::Xaml::DependencyPropertyChangedEventArgs^ e)
{
    BgLabelControl^ theControl{ dynamic_cast<BgLabelControl^>(d) };

    if (theControl != nullptr)
    {
        // succeeded ...
    }
}
```

<span data-ttu-id="11e37-176">Die entsprechende C++ / WinRT-Code ersetzt die `dynamic_cast` mit einem Aufruf an die [**IUnknown:: Try_as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknowntryas-function) Funktion, die **QueryInterface**kapselt.</span><span class="sxs-lookup"><span data-stu-id="11e37-176">The equivalent C++/WinRT code replaces the `dynamic_cast` with a call to the [**IUnknown::try_as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknowntryas-function) function, which encapsulates **QueryInterface**.</span></span> <span data-ttu-id="11e37-177">Sie haben auch die Möglichkeit, rufen Sie stattdessen [**IUnknown:: As**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknownas-function), die eine Ausnahme auslöst, wenn für die erforderliche Schnittstelle (die Standardschnittstelle des Typs, die Sie anfordern) Abfragen nicht zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="11e37-177">You also have the option to call [**IUnknown::as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknownas-function), instead, which throws an exception if querying for the required interface (the default interface of the type you're requesting) is not returned.</span></span> <span data-ttu-id="11e37-178">Nachfolgend finden Sie eine C++ / WinRT-Codebeispiel.</span><span class="sxs-lookup"><span data-stu-id="11e37-178">Here's a C++/WinRT code example.</span></span>

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

## <a name="event-handling-with-a-delegate"></a><span data-ttu-id="11e37-179">Ereignisbehandlung mit einem Delegaten</span><span class="sxs-lookup"><span data-stu-id="11e37-179">Event-handling with a delegate</span></span>
<span data-ttu-id="11e37-180">Hier ist ein typisches Beispiel für die Behandlung eines Ereignisses in C++/CX unter Verwendung einer Lambda-Funktion als Delegaten.</span><span class="sxs-lookup"><span data-stu-id="11e37-180">Here's a typical example of handling an event in C++/CX, using a lambda function as a delegate in this case.</span></span>

```cppcx
auto token = myButton->Click += ref new RoutedEventHandler([=](Platform::Object^ sender, RoutedEventArgs^ args)
{
    // Handle the event.
    // Note: locals are captured by value, not reference, since this handler is delayed.
});
```

<span data-ttu-id="11e37-181">Dies ist das Äquivalent in C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="11e37-181">This is the equivalent in C++/WinRT.</span></span>

```cppwinrt
auto token = myButton().Click([=](IInspectable const& sender, RoutedEventArgs const& args)
{
    // Handle the event.
    // Note: locals are captured by value, not reference, since this handler is delayed.
});
```

<span data-ttu-id="11e37-182">Anstelle einer Lambda-Funktion können Sie den Delegaten als eine freie Funktion oder als Pointer-to-Member-Funktion implementieren.</span><span class="sxs-lookup"><span data-stu-id="11e37-182">Instead of a lambda function, you can choose to implement your delegate as a free function, or as a pointer-to-member-function.</span></span> <span data-ttu-id="11e37-183">Weitere Informationen finden Sie unter [Verarbeiten von Ereignissen über Delegaten in C++/WinRT](handle-events.md).</span><span class="sxs-lookup"><span data-stu-id="11e37-183">For more info, see [Handle events by using delegates in C++/WinRT](handle-events.md).</span></span>

<span data-ttu-id="11e37-184">Wenn Sie von einer C++/CX-Codebasis portieren, wo Ereignisse und Delegate intern verwendet werden (nicht über Binärdateien), hilft Ihnen [**winrt::delegate**](/uwp/cpp-ref-for-winrt/delegate) beim Replizieren dieses Musters in C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="11e37-184">If you're porting from a C++/CX codebase where events and delegates are used internally (not across binaries), then [**winrt::delegate**](/uwp/cpp-ref-for-winrt/delegate) will help you to replicate that pattern in C++/WinRT.</span></span> <span data-ttu-id="11e37-185">Siehe auch [parametrisiert Delegaten, einfachen Signale und Rückrufe innerhalb eines Projekts](author-events.md#parameterized-delegates-simple-signals-and-callbacks-within-a-project).</span><span class="sxs-lookup"><span data-stu-id="11e37-185">Also see [Parameterized delegates, simple signals, and callbacks within a project](author-events.md#parameterized-delegates-simple-signals-and-callbacks-within-a-project).</span></span>

## <a name="revoking-a-delegate"></a><span data-ttu-id="11e37-186">Widerrufen eines Delegaten</span><span class="sxs-lookup"><span data-stu-id="11e37-186">Revoking a delegate</span></span>
<span data-ttu-id="11e37-187">In C++/CX verwenden Sie den `-=`-Operator, um eine frühere Ereignisregistrierung zu widerrufen.</span><span class="sxs-lookup"><span data-stu-id="11e37-187">In C++/CX you use the `-=` operator to revoke a prior event registration.</span></span>

```cppcx
myButton->Click -= token;
```

<span data-ttu-id="11e37-188">Dies ist das Äquivalent in C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="11e37-188">This is the equivalent in C++/WinRT.</span></span>

```cppwinrt
myButton().Click(token);
```

<span data-ttu-id="11e37-189">Weitere Informationen und Optionen finden Sie unter [Einen registrierten Delegaten widerrufen](handle-events.md#revoke-a-registered-delegate).</span><span class="sxs-lookup"><span data-stu-id="11e37-189">For more info and options, see [Revoke a registered delegate](handle-events.md#revoke-a-registered-delegate).</span></span>

## <a name="mapping-ccx-platform-types-to-cwinrt-types"></a><span data-ttu-id="11e37-190">Zuordnen von C++/CX-**Platform**-Typen zu C++/WinRT-Typen</span><span class="sxs-lookup"><span data-stu-id="11e37-190">Mapping C++/CX **Platform** types to C++/WinRT types</span></span>
<span data-ttu-id="11e37-191">C++/CX bietet verschiedene Datentypen im **Platform**-Namespace.</span><span class="sxs-lookup"><span data-stu-id="11e37-191">C++/CX provides several data types in the **Platform** namespace.</span></span> <span data-ttu-id="11e37-192">Diese Typen gehören nicht zum C++-Standard, daher können Sie sie nur verwenden, wenn Sie die Windows-Runtime-Spracherweiterungen aktivieren (Visual Studio-Projekteigenschaft **C/C++** > **Allgemein** > **Windows-Runtime-Erweiterung verwenden** > **Ja (/ZW)**).</span><span class="sxs-lookup"><span data-stu-id="11e37-192">These types are not standard C++, so you can only use them when you enable Windows Runtime language extensions (Visual Studio project property **C/C++** > **General** > **Consume Windows Runtime Extension** > **Yes (/ZW)**).</span></span> <span data-ttu-id="11e37-193">In der Tabelle unten finden Sie Informationen zum Portieren von **Platform**-Typen in ihre Entsprechungen in C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="11e37-193">The table below helps you port from **Platform** types to their equivalents in C++/WinRT.</span></span> <span data-ttu-id="11e37-194">Nachdem Sie dies erledigt haben, können Sie, da C++/WinRT zum C++-Standard gehört, die Option `/ZW` deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="11e37-194">Once you've done that, since C++/WinRT is standard C++, you can turn off the `/ZW` option.</span></span>

| <span data-ttu-id="11e37-195">C++/CX</span><span class="sxs-lookup"><span data-stu-id="11e37-195">C++/CX</span></span> | <span data-ttu-id="11e37-196">C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="11e37-196">C++/WinRT</span></span> |
| ---- | ---- |
| **<span data-ttu-id="11e37-197">Platform:: Agile\ ^</span><span class="sxs-lookup"><span data-stu-id="11e37-197">Platform::Agile\^</span></span>** | [**<span data-ttu-id="11e37-198">WinRT:: agile_ref</span><span class="sxs-lookup"><span data-stu-id="11e37-198">winrt::agile_ref</span></span>**](/uwp/cpp-ref-for-winrt/agile-ref) |
| **<span data-ttu-id="11e37-199">Platform:: Array\ ^</span><span class="sxs-lookup"><span data-stu-id="11e37-199">Platform::Array\^</span></span>** | <span data-ttu-id="11e37-200">Finden Sie unter [Port **Platform:: Array\ ^** ](#port-platformarray)</span><span class="sxs-lookup"><span data-stu-id="11e37-200">See [Port **Platform::Array\^**](#port-platformarray)</span></span> |
| **<span data-ttu-id="11e37-201">Platform::Exception\^</span><span class="sxs-lookup"><span data-stu-id="11e37-201">Platform::Exception\^</span></span>** | [**<span data-ttu-id="11e37-202">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="11e37-202">winrt::hresult_error</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error) |
| **<span data-ttu-id="11e37-203">Platform::InvalidArgumentException\^</span><span class="sxs-lookup"><span data-stu-id="11e37-203">Platform::InvalidArgumentException\^</span></span>** | [**<span data-ttu-id="11e37-204">winrt::hresult_invalid_argument</span><span class="sxs-lookup"><span data-stu-id="11e37-204">winrt::hresult_invalid_argument</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-invalid-argument) |
| **<span data-ttu-id="11e37-205">Platform::Object\^</span><span class="sxs-lookup"><span data-stu-id="11e37-205">Platform::Object\^</span></span>** | **<span data-ttu-id="11e37-206">winrt::Windows::Foundation::IInspectable</span><span class="sxs-lookup"><span data-stu-id="11e37-206">winrt::Windows::Foundation::IInspectable</span></span>** |
| **<span data-ttu-id="11e37-207">Platform::String\^</span><span class="sxs-lookup"><span data-stu-id="11e37-207">Platform::String\^</span></span>** | [**<span data-ttu-id="11e37-208">winrt::hstring</span><span class="sxs-lookup"><span data-stu-id="11e37-208">winrt::hstring</span></span>**](/uwp/cpp-ref-for-winrt/hstring) |

### <a name="port-platformagile-to-winrtagileref"></a><span data-ttu-id="11e37-209">Port **Platform:: Agile\ ^** zu **WinRT:: agile_ref**</span><span class="sxs-lookup"><span data-stu-id="11e37-209">Port **Platform::Agile\^** to **winrt::agile_ref**</span></span>
<span data-ttu-id="11e37-210">Die **Platform:: Agile\ ^** Typ in C++ / CX steht für eine Windows-Runtime-Klasse, die von jedem Thread aus zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="11e37-210">The **Platform::Agile\^** type in C++/CX represents a Windows Runtime class that can be accessed from any thread.</span></span> <span data-ttu-id="11e37-211">C++ / WinRT-äquivalent ist [**WinRT:: agile_ref**](/uwp/cpp-ref-for-winrt/agile-ref).</span><span class="sxs-lookup"><span data-stu-id="11e37-211">The C++/WinRT equivalent is [**winrt::agile_ref**](/uwp/cpp-ref-for-winrt/agile-ref).</span></span>

<span data-ttu-id="11e37-212">In C++/CX.</span><span class="sxs-lookup"><span data-stu-id="11e37-212">In C++/CX.</span></span>

```cppcx
Platform::Agile<Windows::UI::Core::CoreWindow> m_window;
```

<span data-ttu-id="11e37-213">In C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="11e37-213">In C++/WinRT.</span></span>

```cppwinrt
winrt::agile_ref<Windows::UI::Core::CoreWindow> m_window;
```

### <a name="port-platformarray"></a><span data-ttu-id="11e37-214">Port **Platform:: Array\ ^**</span><span class="sxs-lookup"><span data-stu-id="11e37-214">Port **Platform::Array\^**</span></span>
<span data-ttu-id="11e37-215">Ihre Optionen umfassen mit einer Initialisierungsliste, eine **Std:: Array**oder eine **Std:: Vector**.</span><span class="sxs-lookup"><span data-stu-id="11e37-215">Your options include using an initializer list, a **std::array**, or a **std::vector**.</span></span> <span data-ttu-id="11e37-216">Weitere Informationen und Codebeispiele finden Sie unter [aufgeführt, welche standardmäßigen Initialisierung](/windows/uwp/cpp-and-winrt-apis/std-cpp-data-types#standard-initializer-lists) und [Standard-Arrays und-Vektoren](/windows/uwp/cpp-and-winrt-apis/std-cpp-data-types#standard-arrays-and-vectors).</span><span class="sxs-lookup"><span data-stu-id="11e37-216">For more info, and code examples, see [Standard initializer lists](/windows/uwp/cpp-and-winrt-apis/std-cpp-data-types#standard-initializer-lists) and [Standard arrays and vectors](/windows/uwp/cpp-and-winrt-apis/std-cpp-data-types#standard-arrays-and-vectors).</span></span>

### <a name="port-platformexception-to-winrthresulterror"></a><span data-ttu-id="11e37-217">Portieren von **Platform::Exception\^** nach **winrt::hresult_error**</span><span class="sxs-lookup"><span data-stu-id="11e37-217">Port **Platform::Exception\^** to **winrt::hresult_error**</span></span>
<span data-ttu-id="11e37-218">Der Typ **Platform::Exception\^** wird in C++/CX erzeugt, wenn eine Windows-Runtime-API ein Nicht-S\_OK HRESULT zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="11e37-218">The **Platform::Exception\^** type is produced in C++/CX when a Windows Runtime API returns a non S\_OK HRESULT.</span></span> <span data-ttu-id="11e37-219">Für C++/WinRT ist die Entsprechung [**winrt::hresult_error**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error).</span><span class="sxs-lookup"><span data-stu-id="11e37-219">The C++/WinRT equivalent is [**winrt::hresult_error**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error).</span></span>

<span data-ttu-id="11e37-220">Zum Portieren nach C++/WinRT ändern Sie jeglichen Code, der **Platform::Exception\^** verwendet, um stattdessen **winrt::hresult_error** zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="11e37-220">To port to C++/WinRT, change all code that uses **Platform::Exception\^** to use **winrt::hresult_error**.</span></span>

<span data-ttu-id="11e37-221">In C++/CX.</span><span class="sxs-lookup"><span data-stu-id="11e37-221">In C++/CX.</span></span>

```cppcx
catch (Platform::Exception^ ex)
```

<span data-ttu-id="11e37-222">In C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="11e37-222">In C++/WinRT.</span></span>

```cppwinrt
catch (winrt::hresult_error const& ex)
```

<span data-ttu-id="11e37-223">C++/WinRT stellt diese Ausnahmeklassen bereit.</span><span class="sxs-lookup"><span data-stu-id="11e37-223">C++/WinRT provides these exception classes.</span></span>

| <span data-ttu-id="11e37-224">Ausnahmentyp</span><span class="sxs-lookup"><span data-stu-id="11e37-224">Exception type</span></span> | <span data-ttu-id="11e37-225">Basisklasse</span><span class="sxs-lookup"><span data-stu-id="11e37-225">Base class</span></span> | <span data-ttu-id="11e37-226">HRESULT</span><span class="sxs-lookup"><span data-stu-id="11e37-226">HRESULT</span></span> |
| ---- | ---- | ---- |
| [**<span data-ttu-id="11e37-227">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="11e37-227">winrt::hresult_error</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error) | | <span data-ttu-id="11e37-228">Aufrufen von [**hresult_error::to_abi**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error#hresulterrortoabi-function)</span><span class="sxs-lookup"><span data-stu-id="11e37-228">call [**hresult_error::to_abi**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error#hresulterrortoabi-function)</span></span> |
| [**<span data-ttu-id="11e37-229">winrt::hresult_access_denied</span><span class="sxs-lookup"><span data-stu-id="11e37-229">winrt::hresult_access_denied</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-access-denied) | **<span data-ttu-id="11e37-230">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="11e37-230">winrt::hresult_error</span></span>** | <span data-ttu-id="11e37-231">E_ACCESSDENIED</span><span class="sxs-lookup"><span data-stu-id="11e37-231">E_ACCESSDENIED</span></span> |
| [**<span data-ttu-id="11e37-232">winrt::hresult_canceled</span><span class="sxs-lookup"><span data-stu-id="11e37-232">winrt::hresult_canceled</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-canceled) | **<span data-ttu-id="11e37-233">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="11e37-233">winrt::hresult_error</span></span>** | <span data-ttu-id="11e37-234">ERROR_CANCELLED</span><span class="sxs-lookup"><span data-stu-id="11e37-234">ERROR_CANCELLED</span></span> |
| [**<span data-ttu-id="11e37-235">winrt::hresult_changed_state</span><span class="sxs-lookup"><span data-stu-id="11e37-235">winrt::hresult_changed_state</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-changed-state) | **<span data-ttu-id="11e37-236">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="11e37-236">winrt::hresult_error</span></span>** | <span data-ttu-id="11e37-237">E_CHANGED_STATE</span><span class="sxs-lookup"><span data-stu-id="11e37-237">E_CHANGED_STATE</span></span> |
| [**<span data-ttu-id="11e37-238">winrt::hresult_class_not_available</span><span class="sxs-lookup"><span data-stu-id="11e37-238">winrt::hresult_class_not_available</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-class-not-available) | **<span data-ttu-id="11e37-239">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="11e37-239">winrt::hresult_error</span></span>** | <span data-ttu-id="11e37-240">CLASS_E_CLASSNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="11e37-240">CLASS_E_CLASSNOTAVAILABLE</span></span> |
| [**<span data-ttu-id="11e37-241">winrt::hresult_illegal_delegate_assignment</span><span class="sxs-lookup"><span data-stu-id="11e37-241">winrt::hresult_illegal_delegate_assignment</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-illegal-delegate-assignment) | **<span data-ttu-id="11e37-242">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="11e37-242">winrt::hresult_error</span></span>** | <span data-ttu-id="11e37-243">E_ILLEGAL_DELEGATE_ASSIGNMENT</span><span class="sxs-lookup"><span data-stu-id="11e37-243">E_ILLEGAL_DELEGATE_ASSIGNMENT</span></span> |
| [**<span data-ttu-id="11e37-244">winrt::hresult_illegal_method_call</span><span class="sxs-lookup"><span data-stu-id="11e37-244">winrt::hresult_illegal_method_call</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-illegal-method-call) | **<span data-ttu-id="11e37-245">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="11e37-245">winrt::hresult_error</span></span>** | <span data-ttu-id="11e37-246">E_ILLEGAL_METHOD_CALL</span><span class="sxs-lookup"><span data-stu-id="11e37-246">E_ILLEGAL_METHOD_CALL</span></span> |
| [**<span data-ttu-id="11e37-247">winrt::hresult_illegal_state_change</span><span class="sxs-lookup"><span data-stu-id="11e37-247">winrt::hresult_illegal_state_change</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-illegal-state-change) | **<span data-ttu-id="11e37-248">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="11e37-248">winrt::hresult_error</span></span>** | <span data-ttu-id="11e37-249">E_ILLEGAL_STATE_CHANGE</span><span class="sxs-lookup"><span data-stu-id="11e37-249">E_ILLEGAL_STATE_CHANGE</span></span> |
| [**<span data-ttu-id="11e37-250">winrt::hresult_invalid_argument</span><span class="sxs-lookup"><span data-stu-id="11e37-250">winrt::hresult_invalid_argument</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-invalid-argument) | **<span data-ttu-id="11e37-251">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="11e37-251">winrt::hresult_error</span></span>** | <span data-ttu-id="11e37-252">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="11e37-252">E_INVALIDARG</span></span> |
| [**<span data-ttu-id="11e37-253">winrt::hresult_no_interface</span><span class="sxs-lookup"><span data-stu-id="11e37-253">winrt::hresult_no_interface</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-no-interface) | **<span data-ttu-id="11e37-254">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="11e37-254">winrt::hresult_error</span></span>** | <span data-ttu-id="11e37-255">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="11e37-255">E_NOINTERFACE</span></span> |
| [**<span data-ttu-id="11e37-256">winrt::hresult_not_implemented</span><span class="sxs-lookup"><span data-stu-id="11e37-256">winrt::hresult_not_implemented</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-not-implemented) | **<span data-ttu-id="11e37-257">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="11e37-257">winrt::hresult_error</span></span>** | <span data-ttu-id="11e37-258">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="11e37-258">E_NOTIMPL</span></span> |
| [**<span data-ttu-id="11e37-259">winrt::hresult_out_of_bounds</span><span class="sxs-lookup"><span data-stu-id="11e37-259">winrt::hresult_out_of_bounds</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-out-of-bounds) | **<span data-ttu-id="11e37-260">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="11e37-260">winrt::hresult_error</span></span>** | <span data-ttu-id="11e37-261">E_BOUNDS</span><span class="sxs-lookup"><span data-stu-id="11e37-261">E_BOUNDS</span></span> |
| [**<span data-ttu-id="11e37-262">winrt::hresult_wrong_thread</span><span class="sxs-lookup"><span data-stu-id="11e37-262">winrt::hresult_wrong_thread</span></span>**](/uwp/cpp-ref-for-winrt/error-handling/hresult-wrong-thread) | **<span data-ttu-id="11e37-263">winrt::hresult_error</span><span class="sxs-lookup"><span data-stu-id="11e37-263">winrt::hresult_error</span></span>** | <span data-ttu-id="11e37-264">RPC_E_WRONG_THREAD</span><span class="sxs-lookup"><span data-stu-id="11e37-264">RPC_E_WRONG_THREAD</span></span> |

<span data-ttu-id="11e37-265">Beachten Sie, dass jede Klasse (über die **hresult_error** -Basisklasse) eine [**to_abi**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error#hresulterrortoabi-function)-Funktion bereitstellt, die das HRESULT für den Fehler zurückgibt, sowie eine [**message**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error#hresulterrormessage-function)-Funktion, die die Darstellung der Zeichenfolge dieses HRESULT zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="11e37-265">Note that each class (via the **hresult_error** base class) provides a [**to_abi**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error#hresulterrortoabi-function) function, which returns the HRESULT of the error, and a [**message**](/uwp/cpp-ref-for-winrt/error-handling/hresult-error#hresulterrormessage-function) function, which returns the string representation of that HRESULT.</span></span>

<span data-ttu-id="11e37-266">Hier ist ein Beispiel für das Auslösen einer Ausnahme in C++/CX.</span><span class="sxs-lookup"><span data-stu-id="11e37-266">Here's an example of throwing an exception in C++/CX.</span></span>

```cppcx
throw ref new Platform::InvalidArgumentException(L"A valid User is required");
```

<span data-ttu-id="11e37-267">Und das Äquivalent in C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="11e37-267">And the equivalent in C++/WinRT.</span></span>

```cppwinrt
throw winrt::hresult_invalid_argument{ L"A valid User is required" };
```

### <a name="port-platformobject-to-winrtwindowsfoundationiinspectable"></a><span data-ttu-id="11e37-268">Portieren von **Platform::Object\^** nach **winrt::Windows::Foundation::IInspectable**</span><span class="sxs-lookup"><span data-stu-id="11e37-268">Port **Platform::Object\^** to **winrt::Windows::Foundation::IInspectable**</span></span>
<span data-ttu-id="11e37-269">Wie alle C++/WinRT-Typen ist **winrt::Windows::Foundation::IInspectable** ein Werttyp.</span><span class="sxs-lookup"><span data-stu-id="11e37-269">Like all C++/WinRT types, **winrt::Windows::Foundation::IInspectable** is a value type.</span></span> <span data-ttu-id="11e37-270">Hier erfahren Sie, wie Sie eine Variable dieses Typs auf null initialisieren.</span><span class="sxs-lookup"><span data-stu-id="11e37-270">Here's how you initialize a variable of that type to null.</span></span>

```cppwinrt
winrt::Windows::Foundation::IInspectable var{ nullptr };
```

### <a name="port-platformstring-to-winrthstring"></a><span data-ttu-id="11e37-271">Portieren von **Platform::String\^** nach **winrt::hstring**</span><span class="sxs-lookup"><span data-stu-id="11e37-271">Port **Platform::String\^** to **winrt::hstring**</span></span>
<span data-ttu-id="11e37-272">**Platform::String\^** ist das Äquivalent zum Windows-Runtime-HSTRING-ABI-Typ.</span><span class="sxs-lookup"><span data-stu-id="11e37-272">**Platform::String\^** is equivalent to the Windows Runtime HSTRING ABI type.</span></span> <span data-ttu-id="11e37-273">Für C++/WinRT ist die Entsprechung [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring).</span><span class="sxs-lookup"><span data-stu-id="11e37-273">For C++/WinRT, the equivalent is [**winrt::hstring**](/uwp/cpp-ref-for-winrt/hstring).</span></span> <span data-ttu-id="11e37-274">Mit C++/WinRT können Sie aber Windows-Runtime-APIs mit Standard-C++ Wide-String-Typen wie **std::wstring** aufrufen und/oder Wide-String-Literale.</span><span class="sxs-lookup"><span data-stu-id="11e37-274">But with C++/WinRT, you can call Windows Runtime APIs using C++ Standard Library wide string types such as **std::wstring**, and/or wide string literals.</span></span> <span data-ttu-id="11e37-275">Weitere Informationen und Codebeispiele finden Sie unter [String-Verarbeitung in C++/WinRT](strings.md).</span><span class="sxs-lookup"><span data-stu-id="11e37-275">For more details, and code examples, see [String handling in C++/WinRT](strings.md).</span></span>

<span data-ttu-id="11e37-276">Mit C++/CX können Sie auf die Eigenschaft [**Platform::String::Data**](https://docs.microsoft.com/en-us/cpp/cppcx/platform-string-class#data) zugreifen, um die Zeichenfolge als **const wchar_t\***-Array im C-Stil abzurufen (z.B. zur Übergabe an **std::wcout**).</span><span class="sxs-lookup"><span data-stu-id="11e37-276">With C++/CX, you can access the [**Platform::String::Data**](https://docs.microsoft.com/en-us/cpp/cppcx/platform-string-class#data) property to retrieve the string as a C-style **const wchar_t\*** array (for example, to pass it to **std::wcout**).</span></span>

```cppcx
auto var{ titleRecord->TitleName->Data() };
```

<span data-ttu-id="11e37-277">Um das Gleiche mit C++ / WinRT zu tun, können Sie die Funktion [**hstring::c_str**](/uwp/api/windows.foundation.uri#hstringcstr-function) verwenden, um eine auf null beendete Zeichenfolgenversion im C-Stil abzurufen (wie von **std::wstring**).</span><span class="sxs-lookup"><span data-stu-id="11e37-277">To do the same with C++/WinRT, you can use the [**hstring::c_str**](/uwp/api/windows.foundation.uri#hstringcstr-function) function to get a null-terminated C-style string version, just as you can from **std::wstring**.</span></span>

```cppwinrt
auto var{ titleRecord.TitleName().c_str() };
```

<span data-ttu-id="11e37-278">Bei der Implementierung von APIs, die Zeichenfolgen übernehmen oder zurückgeben, ändern Sie in der Regel jeglichen C++/CX-Code, der **Platform::String\^** verwendet, um stattdessen **winrt::hstring** zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="11e37-278">When it comes to implementing APIs that take or return strings, you typically change any C++/CX code that uses **Platform::String\^** to use **winrt::hstring** instead.</span></span>

<span data-ttu-id="11e37-279">Hier ist ein Beispiel für eine C++/CX-API, die eine Zeichenfolge übernimmt.</span><span class="sxs-lookup"><span data-stu-id="11e37-279">Here's an example of a C++/CX API that takes a string.</span></span>

```cppcx
void LogWrapLine(Platform::String^ str);
```

<span data-ttu-id="11e37-280">Für C++/WinRT könnten Sie diese API in [MIDL 3.0](/uwp/midl-3) wie folgt deklarieren.</span><span class="sxs-lookup"><span data-stu-id="11e37-280">For C++/WinRT you could declare that API in [MIDL 3.0](/uwp/midl-3) like this.</span></span>

```idl
// LogType.idl
void LogWrapLine(String str);
```

<span data-ttu-id="11e37-281">Die C++/WinRT-Toolkette generiert dann Quellcode für Sie, der wie folgt aussieht.</span><span class="sxs-lookup"><span data-stu-id="11e37-281">The C++/WinRT toolchain will then generate source code for you that looks like this.</span></span>

```cppwinrt
void LogWrapLine(winrt::hstring const& str);
```

#### <a name="tostring"></a><span data-ttu-id="11e37-282">ToString()</span><span class="sxs-lookup"><span data-stu-id="11e37-282">ToString()</span></span>

<span data-ttu-id="11e37-283">C++ / CX bietet die [Object::ToString](/cpp/cppcx/platform-object-class?view=vs-2017#tostring) -Methode.</span><span class="sxs-lookup"><span data-stu-id="11e37-283">C++/CX provides the [Object::ToString](/cpp/cppcx/platform-object-class?view=vs-2017#tostring) method.</span></span>

```cppcx
int i{ 2 };
auto s{ i.ToString() }; // s is a Platform::String^ with value L"2".
```

<span data-ttu-id="11e37-284">C++ / WinRT nicht direkt zur Verfügung, diese Funktion, aber Sie können zu alternativen aktivieren.</span><span class="sxs-lookup"><span data-stu-id="11e37-284">C++/WinRT doesn't directly provide this facility, but you can turn to alternatives.</span></span>

```cppwinrt
int i{ 2 };
auto s{ std::to_wstring(i) }; // s is a std::wstring with value L"2".
```

## <a name="important-apis"></a><span data-ttu-id="11e37-285">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="11e37-285">Important APIs</span></span>
* [<span data-ttu-id="11e37-286">winrt::delegate-Strukturvorlage</span><span class="sxs-lookup"><span data-stu-id="11e37-286">winrt::delegate struct template</span></span>](/uwp/cpp-ref-for-winrt/delegate)
* [<span data-ttu-id="11e37-287">winrt::hresult_error-Struktur</span><span class="sxs-lookup"><span data-stu-id="11e37-287">winrt::hresult_error struct</span></span>](/uwp/cpp-ref-for-winrt/error-handling/hresult-error)
* [<span data-ttu-id="11e37-288">winrt::hstring-Struktur</span><span class="sxs-lookup"><span data-stu-id="11e37-288">winrt::hstring struct</span></span>](/uwp/cpp-ref-for-winrt/hstring)
* [<span data-ttu-id="11e37-289">winrt-Namespace</span><span class="sxs-lookup"><span data-stu-id="11e37-289">winrt namespace</span></span>](/uwp/cpp-ref-for-winrt/winrt)

## <a name="related-topics"></a><span data-ttu-id="11e37-290">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="11e37-290">Related topics</span></span>
* [<span data-ttu-id="11e37-291">C++/CX</span><span class="sxs-lookup"><span data-stu-id="11e37-291">C++/CX</span></span>](/cpp/cppcx/visual-c-language-reference-c-cx)
* [<span data-ttu-id="11e37-292">Erstellen von Ereignissen mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="11e37-292">Author events in C++/WinRT</span></span>](author-events.md)
* [<span data-ttu-id="11e37-293">Parallelität und asynchrone Vorgänge mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="11e37-293">Concurrency and asynchronous operations with C++/WinRT</span></span>](concurrency.md)
* [<span data-ttu-id="11e37-294">Verwenden von APIs mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="11e37-294">Consume APIs with C++/WinRT</span></span>](consume-apis.md)
* [<span data-ttu-id="11e37-295">Verarbeiten von Ereignissen über Delegaten in C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="11e37-295">Handle events by using delegates in C++/WinRT</span></span>](handle-events.md)
* [<span data-ttu-id="11e37-296">Interoperabilität zwischen C++/WinRT und C++/CX</span><span class="sxs-lookup"><span data-stu-id="11e37-296">Interop between C++/WinRT and C++/CX</span></span>](interop-winrt-cx.md)
* [<span data-ttu-id="11e37-297">Microsoft Interface Definition Language3.0– Referenz</span><span class="sxs-lookup"><span data-stu-id="11e37-297">Microsoft Interface Definition Language 3.0 reference</span></span>](/uwp/midl-3)
* [<span data-ttu-id="11e37-298">Wechsel zu C++/WinRT von WRL</span><span class="sxs-lookup"><span data-stu-id="11e37-298">Move to C++/WinRT from WRL</span></span>](move-to-winrt-from-wrl.md)
* [<span data-ttu-id="11e37-299">String-Verarbeitung in C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="11e37-299">String handling in C++/WinRT</span></span>](strings.md)
