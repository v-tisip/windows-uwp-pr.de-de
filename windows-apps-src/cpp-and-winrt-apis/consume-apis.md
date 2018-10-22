---
author: stevewhims
description: Dieses Thema zeigt, wie man selbst implementierte oder von Windows oder von Drittanbietern implementierte C++/WinRT-APIs verwendet.
title: Verwenden von APIs mit C++/WinRT
ms.author: stwhi
ms.date: 05/08/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp, standard, c++, cpp, winrt, projiziert, projektion, implementierung, laufzeitklasse, aktivierung
ms.localizationpriority: medium
ms.openlocfilehash: dbd657c966cac2310a1078c889ff31b8147c3a59
ms.sourcegitcommit: c4d3115348c8b54fcc92aae8e18fdabc3deb301d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2018
ms.locfileid: "5397848"
---
# <a name="consume-apis-with-cwinrt"></a><span data-ttu-id="e869d-104">Verwenden von APIs mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="e869d-104">Consume APIs with C++/WinRT</span></span>

<span data-ttu-id="e869d-105">Dieses Thema zeigt, wie Sie nutzen [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) APIs, egal ob sie Teil von Windows, stehen von einem Drittanbieter-Komponentenanbieter implementiert oder durch selbst implementiert.</span><span class="sxs-lookup"><span data-stu-id="e869d-105">This topic shows how to consume [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) APIs, whether they're part of Windows, implemented by a third-party component vendor, or implemented by yourself.</span></span>

## <a name="if-the-api-is-in-a-windows-namespace"></a><span data-ttu-id="e869d-106">Wenn sich die API in einem Windows-Namespace befindet</span><span class="sxs-lookup"><span data-stu-id="e869d-106">If the API is in a Windows namespace</span></span>
<span data-ttu-id="e869d-107">Dies ist der häufigste Fall, bei dem Sie eine Windows-Runtime-API verwenden.</span><span class="sxs-lookup"><span data-stu-id="e869d-107">This is the most common case in which you'll consume a Windows Runtime API.</span></span> <span data-ttu-id="e869d-108">Für jeden Typ in einem Windows-Namespace, der in den Metadaten festgelegt ist, definiert C++/WinRT ein C++-freundliches Äquivalent (den *projizierten Typ*).</span><span class="sxs-lookup"><span data-stu-id="e869d-108">For every type in a Windows namespace defined in metadata, C++/WinRT defines a C++-friendly equivalent (called the *projected type*).</span></span> <span data-ttu-id="e869d-109">Ein projizierter Typ verfügt über den gleichen vollqualifizierten Namen wie der Windows-Typ, wird unter Verwendung der C++-Syntax jedoch im C++-**winrt**-Namespace abgelegt.</span><span class="sxs-lookup"><span data-stu-id="e869d-109">A projected type has the same fully-qualified name as the Windows type, but it's placed in the C++ **winrt** namespace using C++ syntax.</span></span> <span data-ttu-id="e869d-110">Beispielsweise wird [**Windows::Foundation::Uri**](/uwp/api/windows.foundation.uri) in C++/WinRT als **winrt::Windows::Foundation::Uri** projiziert.</span><span class="sxs-lookup"><span data-stu-id="e869d-110">For example, [**Windows::Foundation::Uri**](/uwp/api/windows.foundation.uri) is projected into C++/WinRT as **winrt::Windows::Foundation::Uri**.</span></span>

<span data-ttu-id="e869d-111">Es folgt ein einfaches Codebeispiel.</span><span class="sxs-lookup"><span data-stu-id="e869d-111">Here's a simple code example.</span></span>

```cppwinrt
#include <winrt/Windows.Foundation.h>

using namespace winrt;
using namespace Windows::Foundation;

int main()
{
    winrt::init_apartment();
    Uri contosoUri{ L"http://www.contoso.com" };
    Uri combinedUri = contosoUri.CombineUri(L"products");
}
```

<span data-ttu-id="e869d-112">Der enthaltene Header `winrt/Windows.Foundation.h` ist Teil des SDKs und befindet sich im Ordner `%WindowsSdkDir%Include<WindowsTargetPlatformVersion>\cppwinrt\winrt\`.</span><span class="sxs-lookup"><span data-stu-id="e869d-112">The included header `winrt/Windows.Foundation.h` is part of the SDK, found inside the folder `%WindowsSdkDir%Include<WindowsTargetPlatformVersion>\cppwinrt\winrt\`.</span></span> <span data-ttu-id="e869d-113">Die Header in diesem Ordner enthalten Windows-Namespace-Typen, die in C++/WinRT projiziert werden.</span><span class="sxs-lookup"><span data-stu-id="e869d-113">The headers in that folder contain Windows namespace types projected into C++/WinRT.</span></span> <span data-ttu-id="e869d-114">In diesem Beispiel enthält `winrt/Windows.Foundation.h` den Typ **winrt::Windows::Foundation::Uri**, der der projizierte Typ für die Laufzeitklasse [**Windows::Foundation::Uri**](/uwp/api/windows.foundation.uri) ist.</span><span class="sxs-lookup"><span data-stu-id="e869d-114">In this example, `winrt/Windows.Foundation.h` contains **winrt::Windows::Foundation::Uri**, which is the projected type for the runtime class [**Windows::Foundation::Uri**](/uwp/api/windows.foundation.uri).</span></span>

> [!TIP]
> <span data-ttu-id="e869d-115">Wenn Sie einen Typ aus einem Windows-Namespace verwenden möchten, fügen Sie den C++/WinRT-Header ein, der diesem Namespace entspricht.</span><span class="sxs-lookup"><span data-stu-id="e869d-115">Whenever you want to use a type from a Windows namespace, include the C++/WinRT header corresponding to that namespace.</span></span> <span data-ttu-id="e869d-116">Die `using namespace`-Direktiven sind optional, aber praktisch.</span><span class="sxs-lookup"><span data-stu-id="e869d-116">The `using namespace` directives are optional, but convenient.</span></span>

<span data-ttu-id="e869d-117">Im obigen Codebeispiel wird nach der Initialisierung von C++/WinRT ein Wert des projizierten Typs **winrt::Windows::Foundation::Uri** mit Stapelzuordnung über einen seiner öffentlich dokumentierten Konstruktoren (in diesem Beispiel [**Uri(String)**](/uwp/api/windows.foundation.uri#Windows_Foundation_Uri__ctor_System_String_)) zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="e869d-117">In the code example above, after initializing C++/WinRT, we stack-allocate a value of the **winrt::Windows::Foundation::Uri** projected type via one of its publicly documented constructors ([**Uri(String)**](/uwp/api/windows.foundation.uri#Windows_Foundation_Uri__ctor_System_String_), in this example).</span></span> <span data-ttu-id="e869d-118">Für diesen häufigsten Anwendungsfall müssen Sie in der Regel nichts weiter tun.</span><span class="sxs-lookup"><span data-stu-id="e869d-118">For this, the most common use case, that's typically all you have to do.</span></span> <span data-ttu-id="e869d-119">Wenn Sie einen projizierten C++/WinRT-Typwert haben, können Sie diesen behandeln, als wäre er eine Instanz des tatsächlichen Windows-Runtime-Typs, da er über die gleichen Mitglieder verfügt.</span><span class="sxs-lookup"><span data-stu-id="e869d-119">Once you have a C++/WinRT projected type value, you can treat it as if it were an instance of the actual Windows Runtime type, since it has all the same members.</span></span>

<span data-ttu-id="e869d-120">Tatsächlich ist dieser projizierte Wert ein Proxy; im Grunde ist er nur ein intelligenter Zeiger auf ein zugrunde liegendes Objekt.</span><span class="sxs-lookup"><span data-stu-id="e869d-120">In fact, that projected value is a proxy; it's essentially just a smart pointer to a backing object.</span></span> <span data-ttu-id="e869d-121">Die Konstruktoren des projizierten Werts rufen [**RoActivateInstance**](https://msdn.microsoft.com/library/br224646) auf, um eine Instanz der zugrunde liegenden Windows-Runtime-Klasse (in diesem Fall **Windows.Foundation.Uri**) zu erstellen und die Standardschnittstelle dieses Objekts im neuen projizierten Wert zu speichern.</span><span class="sxs-lookup"><span data-stu-id="e869d-121">The projected value's constructor(s) call [**RoActivateInstance**](https://msdn.microsoft.com/library/br224646) to create an instance of the backing Windows Runtime class (**Windows.Foundation.Uri**, in this case), and store that object's default interface inside the new projected value.</span></span> <span data-ttu-id="e869d-122">Wie unten dargestellt, delegieren die Aufrufe von Mitglieder des projizierten Werts tatsächlich über den intelligenten Zeiger an das zugrunde liegende Objekt; Dies ist, in denen Zustandsänderungen auftreten.</span><span class="sxs-lookup"><span data-stu-id="e869d-122">As illustrated below, your calls to the projected value's members actually delegate, via the smart pointer, to the backing object; which is where state changes occur.</span></span>

![Der projizierte Windows::Foundation::Uri-Typ](images/uri.png)

<span data-ttu-id="e869d-124">Wenn der `contosoUri`-Wert außerhalb des Bereichs liegt, wird er zerstört und gibt seinen Verweis zur Standardschnittstelle frei.</span><span class="sxs-lookup"><span data-stu-id="e869d-124">When the `contosoUri` value falls out of scope, it destructs, and releases its reference to the default interface.</span></span> <span data-ttu-id="e869d-125">Wenn dieser Verweis der letzte Verweis auf das zugrunde liegende Windows-Runtime-Objekt **Windows.Foundation.Uri** ist, wird auch das zugrunde liegende Objekt zerstört.</span><span class="sxs-lookup"><span data-stu-id="e869d-125">If that reference is the last reference to the backing Windows Runtime **Windows.Foundation.Uri** object, the backing object destructs as well.</span></span>

> [!TIP]
> <span data-ttu-id="e869d-126">Ein *projizierter Typ* ist ein Wrapper für eine Laufzeitklasse, um deren APIs zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="e869d-126">A *projected type* is a wrapper over a runtime class for purposes of consuming its APIs.</span></span> <span data-ttu-id="e869d-127">Eine *projizierte Schnittstelle* ist ein Wrapper für eine Windows-Runtime-Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="e869d-127">A *projected interface* is a wrapper over a Windows Runtime interface.</span></span>

## <a name="cwinrt-projection-headers"></a><span data-ttu-id="e869d-128">C++/WinRT-Projektionsheader</span><span class="sxs-lookup"><span data-stu-id="e869d-128">C++/WinRT projection headers</span></span>
<span data-ttu-id="e869d-129">Um Windows-Namespace-APIs von C++/WinRT zu verwenden, schließen Sie Header aus dem Ordner `%WindowsSdkDir%Include<WindowsTargetPlatformVersion>\cppwinrt\winrt` ein.</span><span class="sxs-lookup"><span data-stu-id="e869d-129">To consume Windows namespace APIs from C++/WinRT, you include headers from the `%WindowsSdkDir%Include<WindowsTargetPlatformVersion>\cppwinrt\winrt` folder.</span></span> <span data-ttu-id="e869d-130">Üblicherweise verweist ein Typ in einem untergeordneten Namespace auf Typen in seinem unmittelbar übergeordneten Namespace.</span><span class="sxs-lookup"><span data-stu-id="e869d-130">It's common for a type in a subordinate namespace to reference types in its immediate parent namespace.</span></span> <span data-ttu-id="e869d-131">Folglich schließt jeder C++/WinRT-Projektionsheader automatisch seine übergeordnete Namespace-Headerdatei ein, sodass Sie sie nicht explizit einschließen *müssen*.</span><span class="sxs-lookup"><span data-stu-id="e869d-131">Consequently, each C++/WinRT projection header automatically includes its parent namespace header file; so you don't *need* to explicitly include it.</span></span> <span data-ttu-id="e869d-132">Aber auch wenn Sie dies tun, tritt kein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="e869d-132">Although, if you do, there will be no error.</span></span>

<span data-ttu-id="e869d-133">Beispielsweise befinden sich für den Namespace [**Windows::Security::Cryptography::Certificates**](/uwp/api/windows.security.cryptography.certificates) die entsprechenden C++/WinRT-Typdefinitionen in `winrt/Windows.Security.Cryptography.Certificates.h`.</span><span class="sxs-lookup"><span data-stu-id="e869d-133">For example, for the [**Windows::Security::Cryptography::Certificates**](/uwp/api/windows.security.cryptography.certificates) namespace, the equivalent C++/WinRT type definitions reside in `winrt/Windows.Security.Cryptography.Certificates.h`.</span></span> <span data-ttu-id="e869d-134">Die Typen in **Windows::Security::Cryptography::Certificates** erfordern Typen im übergeordneten Namespace **Windows::Security::Cryptography**, und die Typen in diesem Namespace könnten Typen in ihrem eigenen übergeordneten Namespace **Windows::Security** benötigen.</span><span class="sxs-lookup"><span data-stu-id="e869d-134">Types in **Windows::Security::Cryptography::Certificates** require types in the parent **Windows::Security::Cryptography** namespace; and types in that namespace could require types in its own parent, **Windows::Security**.</span></span>

<span data-ttu-id="e869d-135">Wenn Sie also `winrt/Windows.Security.Cryptography.Certificates.h` einschließen, enthält diese Datei wiederum `winrt/Windows.Security.Cryptography.h` und `winrt/Windows.Security.Cryptography.h` enthält `winrt/Windows.Security.h`.</span><span class="sxs-lookup"><span data-stu-id="e869d-135">So, when you include `winrt/Windows.Security.Cryptography.Certificates.h`, that file in turn includes `winrt/Windows.Security.Cryptography.h`; and `winrt/Windows.Security.Cryptography.h` includes `winrt/Windows.Security.h`.</span></span> <span data-ttu-id="e869d-136">Hier ist der Trail dann beendet, da es kein `winrt/Windows.h` gibt.</span><span class="sxs-lookup"><span data-stu-id="e869d-136">That's where the trail stops, since there is no `winrt/Windows.h`.</span></span> <span data-ttu-id="e869d-137">Dieses transitive Einschlussverfahren endet beim Namespace auf zweiter Ebene.</span><span class="sxs-lookup"><span data-stu-id="e869d-137">This transitive inclusion process stops at the second-level namespace.</span></span>

<span data-ttu-id="e869d-138">Das Verfahren schließt transitiv die Headerdateien ein, die die erforderlichen *Deklarationen* und *Implementierungen* für die Klassen bereitstellen, die in übergeordneten Namespaces definiert sind.</span><span class="sxs-lookup"><span data-stu-id="e869d-138">This process transitively includes the header files that provide the necessary *declarations* and *implementations* for the classes defined in parent namespaces.</span></span>

<span data-ttu-id="e869d-139">Ein Mitglied eines Typs in einem Namespace kann auf einen oder mehrere Typen in anderen nicht verbundenen Namespaces verweisen.</span><span class="sxs-lookup"><span data-stu-id="e869d-139">A member of a type in one namespace can reference one or more types in other, unrelated, namespaces.</span></span> <span data-ttu-id="e869d-140">Damit der Compiler diese Mitglieddefinitionen erfolgreich kompilieren kann, muss der Compiler die Typdeklarationen für das Schließen aller dieser Typen anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="e869d-140">In order for the compiler to compile these member definitions successfully, the compiler needs to see the type declarations for the closure of all these types.</span></span> <span data-ttu-id="e869d-141">Folglich umfasst jeder C++/WinRT-Projektionsheader die Namespace-Header, die er braucht, um alle abhängigen Typen zu *deklarieren*.</span><span class="sxs-lookup"><span data-stu-id="e869d-141">Consequently, each C++/WinRT projection header includes the namespace headers it needs to *declare* any dependent types.</span></span> <span data-ttu-id="e869d-142">Im Gegensatz zu übergeordneten Namespaces werden bei diesem Verfahren *die Implementierungen* für die referenzierten Typen *nicht* im Pull-Verfahren abgerufen.</span><span class="sxs-lookup"><span data-stu-id="e869d-142">Unlike for parent namespaces, this process does *not* pull in the *implementations* for referenced types.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e869d-143">Möchten Sie tatsächlich einen Typ *verwenden* (Instanziieren, Aufrufen von Methoden usw.), der in einem nicht verbundenen Namespace deklariert ist, müssen Sie die entsprechende Namespace-Headerdatei für diesen Typ einschließen.</span><span class="sxs-lookup"><span data-stu-id="e869d-143">When you want to actually *use* a type (instantiate, call methods, etc.) declared in an unrelated namespace, you must include the appropriate namespace header file for that type.</span></span> <span data-ttu-id="e869d-144">Nur *Deklarationen*, nicht *Implementierungen*, sind automatisch eingeschlossen.</span><span class="sxs-lookup"><span data-stu-id="e869d-144">Only *declarations*, not *implementations*, are automatically included.</span></span>

<span data-ttu-id="e869d-145">Wenn Sie beispielsweise nur `winrt/Windows.Security.Cryptography.Certificates.h` einschließen, führt dies dazu, dass die Deklarationen von diesen Namespaces (und so weiter, transitiv) abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="e869d-145">For example, if you only include `winrt/Windows.Security.Cryptography.Certificates.h`, then that causes declarations to be pulled in from these namespaces (and so on, transitively).</span></span>

- <span data-ttu-id="e869d-146">Windows.Foundation</span><span class="sxs-lookup"><span data-stu-id="e869d-146">Windows.Foundation</span></span>
- <span data-ttu-id="e869d-147">Windows.Foundation.Collections</span><span class="sxs-lookup"><span data-stu-id="e869d-147">Windows.Foundation.Collections</span></span>
- <span data-ttu-id="e869d-148">Windows.Networking</span><span class="sxs-lookup"><span data-stu-id="e869d-148">Windows.Networking</span></span>
- <span data-ttu-id="e869d-149">Windows.Storage.Streams</span><span class="sxs-lookup"><span data-stu-id="e869d-149">Windows.Storage.Streams</span></span>
- <span data-ttu-id="e869d-150">Windows.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="e869d-150">Windows.Security.Cryptography</span></span>

<span data-ttu-id="e869d-151">Anders ausgedrückt: Einige APIs sind in einem Header forward-deklariert, den Sie eingeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="e869d-151">In other words, some APIs are forward-declared in a header that you've included.</span></span> <span data-ttu-id="e869d-152">Ihre Definitionen befinden sich aber in einem Header, den Sie noch nicht eingeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="e869d-152">But their definitions are in a header that you haven't yet included.</span></span> <span data-ttu-id="e869d-153">Wenn Sie also dann [**Windows::Foundation::Uri::RawUri**](/uwp/api/windows.foundation.uri.rawuri) aufrufen, erhalten Sie eine Linker-Fehlermeldung, die darauf hinweist, dass das Mitglied nicht definiert ist.</span><span class="sxs-lookup"><span data-stu-id="e869d-153">So, if you then call [**Windows::Foundation::Uri::RawUri**](/uwp/api/windows.foundation.uri.rawuri), then you'll receive a linker error indicating that the member is undefined.</span></span> <span data-ttu-id="e869d-154">Die Lösung besteht in einem expliziten `#include <winrt/Windows.Foundation.h>`.</span><span class="sxs-lookup"><span data-stu-id="e869d-154">The solution is to explicitly `#include <winrt/Windows.Foundation.h>`.</span></span> <span data-ttu-id="e869d-155">Wenn Sie einen Linkerfehler wie diesen sehen, schließen Sie den Header ein, der für den API-Namespace benannt ist, und wiederholen Sie die Erstellung.</span><span class="sxs-lookup"><span data-stu-id="e869d-155">In general, when you see a linker error such as this, include the header named for the API's namespace, and rebuild.</span></span>

## <a name="accessing-members-via-the-object-via-an-interface-or-via-the-abi"></a><span data-ttu-id="e869d-156">Zugreifen auf Mitglieder über das Objekt, eine Schnittstelle oder die ABI</span><span class="sxs-lookup"><span data-stu-id="e869d-156">Accessing members via the object, via an interface, or via the ABI</span></span>
<span data-ttu-id="e869d-157">Mit der C++/WinRT-Projektion ist die Laufzeitdarstellung einer Windows-Runtime-Klasse nicht mehr als die zugrunde liegenden ABI-Schnittstellen.</span><span class="sxs-lookup"><span data-stu-id="e869d-157">With the C++/WinRT projection, the runtime representation of a Windows Runtime class is no more than the underlying ABI interfaces.</span></span> <span data-ttu-id="e869d-158">Der Einfachheit halber können Sie Code für die Klassen aber auf eine Weise ausführen, die der jeweilige Autor beabsichtigte.</span><span class="sxs-lookup"><span data-stu-id="e869d-158">But, for your convenience, you can code against classes in the way that their author intended.</span></span> <span data-ttu-id="e869d-159">Rufen Sie z.B. die **ToString**-Methode eines [**Uri**](/uwp/api/windows.foundation.uri) auf, als handelte es sich um eine Methode der Klasse (tatsächlich ist es eine Methode auf der separaten **IStringable**-Schnittstelle).</span><span class="sxs-lookup"><span data-stu-id="e869d-159">For example, you can call the **ToString** method of a [**Uri**](/uwp/api/windows.foundation.uri) as if that were a method of the class (in fact, under the covers, it's a method on the separate **IStringable** interface).</span></span>

```cppwinrt
Uri contosoUri{ L"http://www.contoso.com" };
WINRT_ASSERT(contosoUri.ToString() == L"http://www.contoso.com/"); // QueryInterface is called at this point.
```

<span data-ttu-id="e869d-160">Sie erreichen dies über eine Abfrage für die entsprechende Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="e869d-160">This convenience is achieved via a query for the appropriate interface.</span></span> <span data-ttu-id="e869d-161">Sie haben aber immer die Kontrolle.</span><span class="sxs-lookup"><span data-stu-id="e869d-161">But you're always in control.</span></span> <span data-ttu-id="e869d-162">Sie können ein wenig Komfort gegen etwas mehr Leistung eintauschen– indem Sie die IStringable-Schnittstelle selbst abrufen und direkt verwenden.</span><span class="sxs-lookup"><span data-stu-id="e869d-162">You can opt to give away a little of that convenience for a little performance by retrieving the IStringable interface yourself and using it directly.</span></span> <span data-ttu-id="e869d-163">Im folgenden Codebeispiel erhalten Sie einen tatsächlichen IStringable-Schnittstellenzeiger zur Laufzeit (über eine einmalige Abfrage).</span><span class="sxs-lookup"><span data-stu-id="e869d-163">In the code example below, you obtain an actual IStringable interface pointer at run time (via a one-time query).</span></span> <span data-ttu-id="e869d-164">Danach ist Ihr Aufruf von **ToString** direkter Art und verhindert alle weiteren Aufrufe an **QueryInterface**.</span><span class="sxs-lookup"><span data-stu-id="e869d-164">After that, your call to **ToString** is direct, and avoids any further call to **QueryInterface**.</span></span>

```cppwinrt
IStringable stringable = contosoUri; // One-off QueryInterface.
WINRT_ASSERT(stringable.ToString() == L"http://www.contoso.com/");
```

<span data-ttu-id="e869d-165">Sie können diese Technik wählen, wenn Sie wissen, dass Sie mehrere Methoden auf der gleichen Schnittstelle aufrufen.</span><span class="sxs-lookup"><span data-stu-id="e869d-165">You might choose this technique if you know you'll be calling several methods on the same interface.</span></span>

<span data-ttu-id="e869d-166">Wenn Sie im Übrigen nicht auf die Mitglieder auf ABI-Ebene zugreifen möchten, ist dies möglich.</span><span class="sxs-lookup"><span data-stu-id="e869d-166">Incidentally, if you do want to access members at the ABI level then you can.</span></span> <span data-ttu-id="e869d-167">Im Codebeispiel unten sehen Sie, wie das geht. Sie finden weitere Informationen und Codebeispiele unter [Interoperabilität zwischen C++/WinRT und der ABI](interop-winrt-abi.md).</span><span class="sxs-lookup"><span data-stu-id="e869d-167">The code example below shows how, and there are more details and code examples in [Interop between C++/WinRT and the ABI](interop-winrt-abi.md).</span></span>

```cppwinrt
int port = contosoUri.Port(); // Access the Port "property" accessor via C++/WinRT.

winrt::com_ptr<ABI::Windows::Foundation::IUriRuntimeClass> abiUri = contosoUri.as<ABI::Windows::Foundation::IUriRuntimeClass>();
HRESULT hr = abiUri->get_Port(&port); // Access the get_Port ABI function.
```

## <a name="delayed-initialization"></a><span data-ttu-id="e869d-168">Verzögerte Initialisierung</span><span class="sxs-lookup"><span data-stu-id="e869d-168">Delayed initialization</span></span>
<span data-ttu-id="e869d-169">Selbst der Standardkonstruktor eines projizierten Typs bewirkt, dass ein zugrunde liegendes Windows-Runtime-Objekt erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="e869d-169">Even the default constructor of a projected type causes a backing Windows Runtime object to be created.</span></span> <span data-ttu-id="e869d-170">Wenn Sie eine Variable eines projizierten Typs erstellen möchten, ohne dass es wiederum ein Windows-Runtime-Objekt erstellt (sodass Sie diese Arbeit auf einen späteren Zeitpunkt verschieben können), so können Sie das tun.</span><span class="sxs-lookup"><span data-stu-id="e869d-170">If you want to construct a variable of a projected type without it in turn constructing a Windows Runtime object (so that you can delay that work until later), then you can.</span></span> <span data-ttu-id="e869d-171">Deklarieren Sie die Variable oder das Feld mit dem speziellen C++/WinRT-Konstruktor `nullptr_t` des projizierten Typs.</span><span class="sxs-lookup"><span data-stu-id="e869d-171">Declare your variable or field using the projected type's special C++/WinRT `nullptr_t` constructor.</span></span>

```cppwinrt
#include <winrt/Windows.Storage.Streams.h>
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

<span data-ttu-id="e869d-172">Alle Konstruktoren des projizierten Typs, *ausgenommen* der Konstruktor `nullptr_t`, bewirken, dass ein zugrunde liegendes Windows-Runtime-Objekt erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="e869d-172">All constructors on the projected type *except* the `nullptr_t` constructor cause a backing Windows Runtime object to be created.</span></span> <span data-ttu-id="e869d-173">Dem Konstruktor `nullptr_t` ist im Wesentlichen keine Aktion zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="e869d-173">The `nullptr_t` constructor is essentially a no-op.</span></span> <span data-ttu-id="e869d-174">Er erwartet, dass das projizierte Objekt zu einem späteren Zeitpunkt initialisiert wird.</span><span class="sxs-lookup"><span data-stu-id="e869d-174">It expects the projected object to be initialized at a subsequent time.</span></span> <span data-ttu-id="e869d-175">Ob eine Laufzeitklasse also über einen Standardkonstruktor verfügt oder nicht, Sie können dieses Verfahren für eine effiziente verzögerte Initialisierung verwenden.</span><span class="sxs-lookup"><span data-stu-id="e869d-175">So, whether a runtime class has a default constructor or not, you can use this technique for efficient delayed initialization.</span></span>

## <a name="if-the-api-is-implemented-in-a-windows-runtime-component"></a><span data-ttu-id="e869d-176">Wenn die API in einer Komponente für Windows-Runtime implementiert ist</span><span class="sxs-lookup"><span data-stu-id="e869d-176">If the API is implemented in a Windows Runtime component</span></span>
<span data-ttu-id="e869d-177">Dieser Abschnitt gilt unabhängig davon, ob Sie die Komponente selbst erstellt haben oder ob sie von einem Anbieter stammt.</span><span class="sxs-lookup"><span data-stu-id="e869d-177">This section applies whether you authored the component yourself, or it came from a vendor.</span></span>

> [!NOTE]
> <span data-ttu-id="e869d-178">Informationen zur Installation und Verwendung der C++/WinRT Visual Studio Extension (VSIX) (die Projektvorlagenunterstützung sowie C++/WinRT MSBuild-Eigenschaften und -Ziele bietet) finden Sie unter [Visual Studio-Unterstützung für C++/WinRT und VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).</span><span class="sxs-lookup"><span data-stu-id="e869d-178">For info about installing and using the C++/WinRT Visual Studio Extension (VSIX) (which provides project template support, as well as C++/WinRT MSBuild properties and targets) see [Visual Studio support for C++/WinRT, and the VSIX](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix).</span></span>

<span data-ttu-id="e869d-179">Verweisen Sie in Ihrem Anwendungsprojekt auf die Windows-Runtime-Metadaten-Datei (`.winmd`) der Komponente für Windows-Runtime und erstellen Sie diese.</span><span class="sxs-lookup"><span data-stu-id="e869d-179">In your application project, reference the Windows Runtime component's Windows Runtime metadata (`.winmd`) file, and build.</span></span> <span data-ttu-id="e869d-180">Während des Builds erzeugt das `cppwinrt.exe`-Tool eine Standard-C++ Bibliothek, die die API-Oberfläche der Komponente vollständig beschreibt (bzw. *projiziert*).</span><span class="sxs-lookup"><span data-stu-id="e869d-180">During the build, the `cppwinrt.exe` tool generates a standard C++ library that fully describes&mdash;or *projects*&mdash;the API surface for the component.</span></span> <span data-ttu-id="e869d-181">Mit anderen Worten, die generierte Bibliothek enthält die projizierten Typen für die Komponente.</span><span class="sxs-lookup"><span data-stu-id="e869d-181">In other words, the generated library contains the projected types for the component.</span></span>

<span data-ttu-id="e869d-182">Dann fügen Sie wie bei einem Windows-Namespace-Typ einen Header ein und konstruieren den projizierten Typ über einen seiner Konstruktoren.</span><span class="sxs-lookup"><span data-stu-id="e869d-182">Then, just as for a Windows namespace type, you include a header and construct the projected type via one of its constructors.</span></span> <span data-ttu-id="e869d-183">Der Startcode Ihres Anwendungsprojekts registriert die Laufzeitklasse, und der Konstruktor des projizierten Typs ruft [**RoActivateInstance**](https://msdn.microsoft.com/library/br224646) auf, um die Laufzeitklasse der referenzierten Komponente zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="e869d-183">Your application project's startup code registers the runtime class, and the projected type's constructor calls [**RoActivateInstance**](https://msdn.microsoft.com/library/br224646) to activate the runtime class from the referenced component.</span></span>

```cppwinrt
#include <winrt/BankAccountWRC.h>

struct App : implements<App, IFrameworkViewSource, IFrameworkView>
{
    BankAccountWRC::BankAccount bankAccount;
    ...
};
```

<span data-ttu-id="e869d-184">Weitere Details, Code und eine exemplarische Vorgehensweise bei der Verwendung von APIs, die in einer Komponente für Windows-Runtime implementiert sind, finden Sie unter [Erstellen von Ereignissen in C++/WinRT](author-events.md#create-a-core-app-bankaccountcoreapp-to-test-the-windows-runtime-component).</span><span class="sxs-lookup"><span data-stu-id="e869d-184">For more details, code, and a walkthrough of consuming APIs implemented in a Windows Runtime component, see [Author events in C++/WinRT](author-events.md#create-a-core-app-bankaccountcoreapp-to-test-the-windows-runtime-component).</span></span>

## <a name="if-the-api-is-implemented-in-the-consuming-project"></a><span data-ttu-id="e869d-185">Wenn die API im verwendenden Projekt implementiert ist</span><span class="sxs-lookup"><span data-stu-id="e869d-185">If the API is implemented in the consuming project</span></span>
<span data-ttu-id="e869d-186">Ein Typ, der vom XAML-UI verwendet wird, muss eine Laufzeitklasse sein (auch, wenn er sich im selben Projekt wie das XAML-UI befindet).</span><span class="sxs-lookup"><span data-stu-id="e869d-186">A type that's consumed from XAML UI must be a runtime class, even if it's in the same project as the XAML.</span></span>

<span data-ttu-id="e869d-187">Für dieses Szenario generieren Sie einen projizierten Typ aus den Windows-Runtime-Metadaten der Laufzeitklasse (`.winmd`).</span><span class="sxs-lookup"><span data-stu-id="e869d-187">For this scenario, you generate a projected type from the runtime class's Windows Runtime metadata (`.winmd`).</span></span> <span data-ttu-id="e869d-188">Auch hier fügen Sie einen Header ein. Aber diesmal konstruieren Sie den projizierten Typ über seinen `nullptr`-Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="e869d-188">Again, you include a header, but this time you construct the projected type via its `nullptr` constructor.</span></span> <span data-ttu-id="e869d-189">Dieser Konstruktor führt keine Initialisierung durch. Daher müssen Sie der Instanz über die [**winrt::make**](/uwp/cpp-ref-for-winrt/make)-Helper-Funktion einen Wert zuweisen und alle notwendigen Konstruktorargumente übergeben.</span><span class="sxs-lookup"><span data-stu-id="e869d-189">That constructor doesn't perform any initialization, so you must next assign a value to the instance via the [**winrt::make**](/uwp/cpp-ref-for-winrt/make) helper function, passing any necessary constructor arguments.</span></span> <span data-ttu-id="e869d-190">Eine Laufzeitklasse, die im selben Projekt wie der verwendende Code implementiert ist, muss weder registriert noch über die Windows-Runtime/COM-Aktivierung instanziiert werden.</span><span class="sxs-lookup"><span data-stu-id="e869d-190">A runtime class implemented in the same project as the consuming code doesn't need to be registered, nor instantiated via Windows Runtime/COM activation.</span></span>

```cppwinrt
// MainPage.h
...
struct MainPage : MainPageT<MainPage>
{
    ...
    private:
        Bookstore::BookstoreViewModel m_mainViewModel{ nullptr };
        ...
    };
}
...
// MainPage.cpp
...
#include "BookstoreViewModel.h"

MainPage::MainPage()
{
    m_mainViewModel = winrt::make<Bookstore::implementation::BookstoreViewModel>();
    ...
}
```

<span data-ttu-id="e869d-191">Weitere Details, Code und eine exemplarische Vorgehensweise für die Nutzung einer im verwendenden Projekt implementierten Laufzeitklasse finden Sie unter [XAML-Steuerelemente; Binden an eine C++/WinRT-Eigenschaft](binding-property.md#add-a-property-of-type-bookstoreviewmodel-to-mainpage).</span><span class="sxs-lookup"><span data-stu-id="e869d-191">For more details, code, and a walkthrough of consuming a runtime class implemented in the consuming project, see [XAML controls; bind to a C++/WinRT property](binding-property.md#add-a-property-of-type-bookstoreviewmodel-to-mainpage).</span></span>

## <a name="instantiating-and-returning-projected-types-and-interfaces"></a><span data-ttu-id="e869d-192">Instanziierung und Rückgabe von projizierten Typen und Schnittstellen</span><span class="sxs-lookup"><span data-stu-id="e869d-192">Instantiating and returning projected types and interfaces</span></span>
<span data-ttu-id="e869d-193">Hier ist ein Beispiel dafür, wie projizierte Typen und Schnittstellen in Ihrem Projekt aussehen könnten.</span><span class="sxs-lookup"><span data-stu-id="e869d-193">Here's an example of what projected types and interfaces might look like in your consuming project.</span></span> <span data-ttu-id="e869d-194">Denken Sie daran, dass ein Projizierter Typ (wie in diesem Beispiel), Tool generiert wird, und nicht etwas, würde sich selbst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="e869d-194">Remember that a projected type (such as the one in this example), is tool-generated, and is not something that you'd author yourself.</span></span>

```cppwinrt
struct MyRuntimeClass : MyProject::IMyRuntimeClass, impl::require<MyRuntimeClass,
    Windows::Foundation::IStringable, Windows::Foundation::IClosable>
```

<span data-ttu-id="e869d-195">**MyRuntimeClass** ist ein projizierter Typ. Projizierte Schnittstellen sind **IMyRuntimeClass**, **IStringable** und **IClosable**.</span><span class="sxs-lookup"><span data-stu-id="e869d-195">**MyRuntimeClass** is a projected type; projected interfaces include **IMyRuntimeClass**, **IStringable**, and **IClosable**.</span></span> <span data-ttu-id="e869d-196">Dieses Thema hat die verschiedenen Möglichkeiten gezeigt, über die Sie einen projizierten Typ instanziieren können.</span><span class="sxs-lookup"><span data-stu-id="e869d-196">This topic has shown the different ways in which you can instantiate a projected type.</span></span> <span data-ttu-id="e869d-197">Hier ist eine Zusammenfassung, die **MyRuntimeClass** als Beispiel verwendet.</span><span class="sxs-lookup"><span data-stu-id="e869d-197">Here's a reminder and summary, using **MyRuntimeClass** as an example.</span></span>

```cppwinrt
// The runtime class is implemented in another compilation unit (it's either a Windows API,
// or it's implemented in a second- or third-party component).
MyProject::MyRuntimeClass myrc1;

// The runtime class is implemented in the same compilation unit.
MyProject::MyRuntimeClass myrc2{ nullptr };
myrc2 = winrt::make<MyProject::implementation::MyRuntimeClass>();
```

- <span data-ttu-id="e869d-198">Sie können auf die Mitglieder aller Schnittstellen eines projizierten Typs zugreifen.</span><span class="sxs-lookup"><span data-stu-id="e869d-198">You can access the members of all of the interfaces of a projected type.</span></span>
- <span data-ttu-id="e869d-199">Sie können einen projizierten Typ an einen Aufrufer zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="e869d-199">You can return a projected type to a caller.</span></span>
- <span data-ttu-id="e869d-200">Projizierte Typen und Schnittstellen sind von [**winrt::Windows::Foundation::IUnknown**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown) abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="e869d-200">Projected types and interfaces derive from [**winrt::Windows::Foundation::IUnknown**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown).</span></span> <span data-ttu-id="e869d-201">Sie können [**IUnknown::as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknownas-function) für einen projizierten Typ oder eine Interface aufrufen, um nach anderen projizierten Schnittstellen zu suchen, die Sie ebenfalls verwenden oder an einen Aufrufer zurückgeben können.</span><span class="sxs-lookup"><span data-stu-id="e869d-201">So, you can call [**IUnknown::as**](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown#iunknownas-function) on a projected type or interface to query for other projected interfaces, which you can also either use or return to a caller.</span></span> <span data-ttu-id="e869d-202">Die Mitgliedsfunktion **as** funktioniert wie [**QueryInterface**](https://msdn.microsoft.com/library/windows/desktop/ms682521).</span><span class="sxs-lookup"><span data-stu-id="e869d-202">The **as** member function works like [**QueryInterface**](https://msdn.microsoft.com/library/windows/desktop/ms682521).</span></span>

```cppwinrt
void f(MyProject::MyRuntimeClass const& myrc)
{
    myrc.ToString();
    myrc.Close();
    IClosable iclosable = myrc.as<IClosable>();
    iclosable.Close();
}
```

## <a name="activation-factories"></a><span data-ttu-id="e869d-203">Aktivierungsfactorys</span><span class="sxs-lookup"><span data-stu-id="e869d-203">Activation factories</span></span>
<span data-ttu-id="e869d-204">Es folgt eine einfache, direkte Methode zur Erstellung eines C++/WinRT-Objekts.</span><span class="sxs-lookup"><span data-stu-id="e869d-204">The convenient, direct way to create a C++/WinRT object is as follows.</span></span>

```cppwinrt
using namespace winrt::Windows::Globalization::NumberFormatting;
...
CurrencyFormatter currency{ L"USD" };
```

<span data-ttu-id="e869d-205">Es kann jedoch Fälle geben, in denen Sie die Aktivierungsfactory selbst erstellen und dann Objekte daraus anlegen möchten.</span><span class="sxs-lookup"><span data-stu-id="e869d-205">But there may be times that you'll want to create the activation factory yourself, and then create objects from it at your convenience.</span></span> <span data-ttu-id="e869d-206">Es folgen einige Beispiele, die Ihnen zeigen, wie dies mit der Funktionsvorlage [**winrt::get_activation_factory**](/uwp/cpp-ref-for-winrt/get-activation-factory) geht.</span><span class="sxs-lookup"><span data-stu-id="e869d-206">Here are some examples showing you how, using the [**winrt::get_activation_factory**](/uwp/cpp-ref-for-winrt/get-activation-factory) function template.</span></span>

```cppwinrt
using namespace winrt::Windows::Globalization::NumberFormatting;
...
auto factory = winrt::get_activation_factory<CurrencyFormatter, ICurrencyFormatterFactory>();
CurrencyFormatter currency = factory.CreateCurrencyFormatterCode(L"USD");
```

```cppwinrt
using namespace winrt::Windows::Foundation;
...
auto factory = winrt::get_activation_factory<Uri, IUriRuntimeClassFactory>();
Uri account = factory.CreateUri(L"http://www.contoso.com");
```

<span data-ttu-id="e869d-207">Die Klassen in den beiden obigen Beispielen sind Typen aus einem Windows-Namespace.</span><span class="sxs-lookup"><span data-stu-id="e869d-207">The classes in the two examples above are types from a Windows namespace.</span></span> <span data-ttu-id="e869d-208">Im nächsten Beispiel ist **BankAccountWRC::BankAccount** ein benutzerdefinierter Typ, der in einer Komponente für Windows-Runtime implementiert ist.</span><span class="sxs-lookup"><span data-stu-id="e869d-208">In this next example, **BankAccountWRC::BankAccount** is a custom type implemented in a Windows Runtime Component.</span></span>

```cppwinrt
auto factory = winrt::get_activation_factory<BankAccountWRC::BankAccount>();
BankAccountWRC::BankAccount account = factory.ActivateInstance<BankAccountWRC::BankAccount>();
```

## <a name="important-apis"></a><span data-ttu-id="e869d-209">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="e869d-209">Important APIs</span></span>
* [<span data-ttu-id="e869d-210">QueryInterface-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="e869d-210">QueryInterface interface</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682521)
* [<span data-ttu-id="e869d-211">RoActivateInstance-Funktion</span><span class="sxs-lookup"><span data-stu-id="e869d-211">RoActivateInstance function</span></span>](https://msdn.microsoft.com/library/br224646)
* [<span data-ttu-id="e869d-212">Foundation-Klasse</span><span class="sxs-lookup"><span data-stu-id="e869d-212">Windows::Foundation::Uri class</span></span>](/uwp/api/windows.foundation.uri)
* [<span data-ttu-id="e869d-213">winrt::get_activation_factory Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="e869d-213">winrt::get_activation_factory function template</span></span>](/uwp/cpp-ref-for-winrt/get-activation-factory)
* [<span data-ttu-id="e869d-214">winrt::make Funktionsvorlage</span><span class="sxs-lookup"><span data-stu-id="e869d-214">winrt::make function template</span></span>](/uwp/cpp-ref-for-winrt/make)
* [<span data-ttu-id="e869d-215">winrt::Windows::Foundation::IUnknown-Struktur</span><span class="sxs-lookup"><span data-stu-id="e869d-215">winrt::Windows::Foundation::IUnknown struct</span></span>](/uwp/cpp-ref-for-winrt/windows-foundation-iunknown)

## <a name="related-topics"></a><span data-ttu-id="e869d-216">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="e869d-216">Related topics</span></span>
* [<span data-ttu-id="e869d-217">Erstellen von Ereignissen mit C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="e869d-217">Author events in C++/WinRT</span></span>](author-events.md#create-a-core-app-bankaccountcoreapp-to-test-the-windows-runtime-component)
* [<span data-ttu-id="e869d-218">Interoperabilität zwischen C++/WinRT und der ABI</span><span class="sxs-lookup"><span data-stu-id="e869d-218">Interop between C++/WinRT and the ABI</span></span>](interop-winrt-abi.md)
* [<span data-ttu-id="e869d-219">Einführung in C++/WinRT</span><span class="sxs-lookup"><span data-stu-id="e869d-219">Introduction to C++/WinRT</span></span>](intro-to-using-cpp-with-winrt.md)
* [<span data-ttu-id="e869d-220">XAML-Steuerelemente; Binden an eine C++/WinRT-Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="e869d-220">XAML controls; bind to a C++/WinRT property</span></span>](binding-property.md#add-a-property-of-type-bookstoreviewmodel-to-mainpage)
