---
author: jwmsft
description: Erläutert, wie eine angefügte XAML-Eigenschaft als Abhängigkeitseigenschaft implementiert und die Accessorkonvention definiert wird, die erforderlich ist, damit die angefügte Eigenschaft in XAML verwendet werden kann.
title: Benutzerdefinierte angefügte Eigenschaften
ms.assetid: E9C0C57E-6098-4875-AA3E-9D7B36E160E0
ms.author: jimwalk
ms.date: 07/18/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
dev_langs:
- csharp
- vb
- cppwinrt
- cpp
ms.openlocfilehash: ce26242f1f5093afcbfb652a7d1736897975cb3a
ms.sourcegitcommit: 194ab5aa395226580753869c6b66fce88be83522
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2018
ms.locfileid: "4152789"
---
# <a name="custom-attached-properties"></a><span data-ttu-id="59277-104">Benutzerdefinierte angefügte Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="59277-104">Custom attached properties</span></span>

<span data-ttu-id="59277-105">Eine *angefügte Eigenschaft* ist ein XAML-Konzept.</span><span class="sxs-lookup"><span data-stu-id="59277-105">An *attached property* is a XAML concept.</span></span> <span data-ttu-id="59277-106">Angefügte Eigenschaften werden in der Regel als eine spezialisierte Form der Abhängigkeitseigenschaft definiert.</span><span class="sxs-lookup"><span data-stu-id="59277-106">Attached properties are typically defined as a specialized form of dependency property.</span></span> <span data-ttu-id="59277-107">In diesem Thema wird erläutert, wie eine angefügte Eigenschaft als Abhängigkeitseigenschaft implementiert und die Accessorkonvention definiert wird, die erforderlich ist, damit die angefügte Eigenschaft in XAML verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="59277-107">This topic explains how to implement an attached property as a dependency property and how to define the accessor convention that is necessary for your attached property to be usable in XAML.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="59277-108">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="59277-108">Prerequisites</span></span>

<span data-ttu-id="59277-109">Wir gehen davon aus, dass Sie die Abhängigkeitseigenschaften aus der Perspektive eines Consumers vorhandener Abhängigkeitseigenschaften sehen und dass Sie die [Übersicht über Abhängigkeitseigenschaften](dependency-properties-overview.md) gelesen haben.</span><span class="sxs-lookup"><span data-stu-id="59277-109">We assume that you understand dependency properties from the perspective of a consumer of existing dependency properties, and that you have read the [Dependency properties overview](dependency-properties-overview.md).</span></span> <span data-ttu-id="59277-110">Sie sollten auch die [Übersicht über angefügte Eigenschaften](attached-properties-overview.md) gelesen haben.</span><span class="sxs-lookup"><span data-stu-id="59277-110">You should also have read [Attached properties overview](attached-properties-overview.md).</span></span> <span data-ttu-id="59277-111">Für ein besseres Verständnis der in diesem Thema aufgeführten Beispiele sollten Sie XAML verstehen und wissen, wie eine einfache Windows-Runtime-App mit C++, C# oder Visual Basic geschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="59277-111">To follow the examples in this topic, you should also understand XAML and know how to write a basic Windows Runtime app using C++, C#, or Visual Basic.</span></span>

## <a name="scenarios-for-attached-properties"></a><span data-ttu-id="59277-112">Szenarien für angefügte Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="59277-112">Scenarios for attached properties</span></span>

<span data-ttu-id="59277-113">Möglicherweise möchten Sie eine angefügte Eigenschaft erstellen, wenn es einen Grund für das Vorhandensein eines Mechanismus zum Festlegen von Eigenschaften für Klassen außer der definierenden Klasse gibt.</span><span class="sxs-lookup"><span data-stu-id="59277-113">You might create an attached property when there is a reason to have a property-setting mechanism available for classes other than the defining class.</span></span> <span data-ttu-id="59277-114">Die häufigsten Szenarien dafür sind Layout- und Dienstunterstützung.</span><span class="sxs-lookup"><span data-stu-id="59277-114">The most common scenarios for this are layout and services support.</span></span> <span data-ttu-id="59277-115">Beispiele für vorhandene Layouteigenschaften sind [**Canvas.ZIndex**](https://msdn.microsoft.com/library/windows/apps/hh759773) und [**Canvas.Top**](https://msdn.microsoft.com/library/windows/apps/hh759772).</span><span class="sxs-lookup"><span data-stu-id="59277-115">Examples of existing layout properties are [**Canvas.ZIndex**](https://msdn.microsoft.com/library/windows/apps/hh759773) and [**Canvas.Top**](https://msdn.microsoft.com/library/windows/apps/hh759772).</span></span> <span data-ttu-id="59277-116">In einem Layoutszenario können Elemente, die als untergeordnete Elemente für layoutsteuernde Elemente fungieren, einzeln Layoutanforderungen gegenüber ihren übergeordneten Elementen ausdrücken. Dabei legt jedes Element einen Eigenschaftswert fest, den das übergeordnete Element als eine angefügte Eigenschaft definiert.</span><span class="sxs-lookup"><span data-stu-id="59277-116">In a layout scenario, elements that exist as child elements to layout-controlling elements can express layout requirements to their parent elements individually, each setting a property value that the parent defines as an attached property.</span></span> <span data-ttu-id="59277-117">Ein Beispiel für das Dienstunterstützungsszenario in der Windows-Runtime-API ist das Festlegen der angefügten Eigenschaften von [**ScrollViewer**](https://msdn.microsoft.com/library/windows/apps/br209527), z.B. [**ScrollViewer.IsZoomChainingEnabled**](https://msdn.microsoft.com/library/windows/apps/br209561).</span><span class="sxs-lookup"><span data-stu-id="59277-117">An example of the services-support scenario in the Windows Runtime API is set of the attached properties of [**ScrollViewer**](https://msdn.microsoft.com/library/windows/apps/br209527), such as [**ScrollViewer.IsZoomChainingEnabled**](https://msdn.microsoft.com/library/windows/apps/br209561).</span></span>

> [!WARNING]
> <span data-ttu-id="59277-118">Eine Beschränkung der XAML-Implementierung der Windows Runtime: Sie können keine benutzerdefinierten angefügten Eigenschaften animieren.</span><span class="sxs-lookup"><span data-stu-id="59277-118">An existing limitation of the Windows Runtime XAML implementation is that you cannot animate your custom attached property.</span></span>

## <a name="registering-a-custom-attached-property"></a><span data-ttu-id="59277-119">Registrieren einer benutzerdefinierten angefügten Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="59277-119">Registering a custom attached property</span></span>

<span data-ttu-id="59277-120">Wenn Sie die angefügte Eigenschaft immer für die Verwendung mit anderen Typen definieren, muss die Klasse, in der die Eigenschaft registriert ist, nicht aus [**DependencyObject**](https://msdn.microsoft.com/library/windows/apps/br242356) abgeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="59277-120">If you are defining the attached property strictly for use on other types, the class where the property is registered does not have to derive from [**DependencyObject**](https://msdn.microsoft.com/library/windows/apps/br242356).</span></span> <span data-ttu-id="59277-121">Die Zielparameter für Accessoren müssen jedoch **DependencyObject** verwenden, wenn Sie das typische Modell befolgen, bei dem Ihre angefügte Eigenschaft auch eine Abhängigkeitseigenschaft sein kann, sodass Sie den Sicherungseigenschaftsspeicher verwenden können.</span><span class="sxs-lookup"><span data-stu-id="59277-121">But you do need to have the target parameter for accessors use **DependencyObject** if you follow the typical model of having your attached property also be a dependency property, so that you can use the backing property store.</span></span>

<span data-ttu-id="59277-122">Sie definieren Ihre angefügte Eigenschaft als Abhängigkeitseigenschaft, indem Sie eine **public** **static** **readonly**-Eigenschaft des Typs [**DependencyProperty**](https://msdn.microsoft.com/library/windows/apps/br242362) deklarieren.</span><span class="sxs-lookup"><span data-stu-id="59277-122">Define your attached property as a dependency property by declaring a **public** **static** **readonly** property of type [**DependencyProperty**](https://msdn.microsoft.com/library/windows/apps/br242362).</span></span> <span data-ttu-id="59277-123">Sie definieren diese Eigenschaft mithilfe des Rückgabewerts der [**RegisterAttached**](https://msdn.microsoft.com/library/windows/apps/hh701833)-Methode.</span><span class="sxs-lookup"><span data-stu-id="59277-123">You define this property by using the return value of the [**RegisterAttached**](https://msdn.microsoft.com/library/windows/apps/hh701833) method.</span></span> <span data-ttu-id="59277-124">Der Eigenschaftenname muss mit dem Namen der angefügten Eigenschaft übereinstimmen, die Sie als **RegisterAttached** *name*-Parameter angeben. Am Ende muss die Zeichenfolge „Property“ hinzugefügt sein.</span><span class="sxs-lookup"><span data-stu-id="59277-124">The property name must match the attached property name you specify as the **RegisterAttached** *name* parameter, with the string "Property" added to the end.</span></span> <span data-ttu-id="59277-125">Dies ist die bestehende Konvention zum Benennen der Bezeichner von Abhängigkeitseigenschaften im Verhältnis mit den Eigenschaften, die sie darstellen.</span><span class="sxs-lookup"><span data-stu-id="59277-125">This is the established convention for naming the identifiers of dependency properties in relation to the properties that they represent.</span></span>

<span data-ttu-id="59277-126">Der Hauptunterschied beim Definieren einer benutzerdefinierten Eigenschaft und beim Definieren einer benutzerdefinierten Abhängigkeitseigenschaft besteht darin, wie Sie die Accessoren oder Wrapper definieren.</span><span class="sxs-lookup"><span data-stu-id="59277-126">The main area where defining a custom attached property differs from a custom dependency property is in how you define the accessors or wrappers.</span></span> <span data-ttu-id="59277-127">Anstelle der wrappertechnik in [benutzerdefinierte Abhängigkeitseigenschaften](custom-dependency-properties.md)beschrieben, müssen Sie auch statische bereitstellen \**erhalten \*\*\* PropertyName* und \**festlegen \*\*\* PropertyName* -Methoden als Accessoren für die angefügte Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="59277-127">Instead of the using the wrapper technique described in [Custom dependency properties](custom-dependency-properties.md), you must also provide static \**Get\*\*\*PropertyName* and \**Set\*\*\*PropertyName* methods as accessors for the attached property.</span></span> <span data-ttu-id="59277-128">Die Accessoren werden hauptsächlich vom XAML-Parser verwendet, obwohl sie auch von anderen aufrufenden Elementen verwendet werden können, um Werte in Nicht-XAML-Szenarien festzulegen.</span><span class="sxs-lookup"><span data-stu-id="59277-128">The accessors are used mostly by the XAML parser, although any other caller can also use them to set values in non-XAML scenarios.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="59277-129">Wenn Sie die Accessoren nicht ordnungsgemäß definieren, kann der XAML-Prozessor nicht auf Ihre angefügte Eigenschaft zugreifen, und Benutzer, die sie verwenden möchten, erhalten möglicherweise einen XAML-Parserfehler.</span><span class="sxs-lookup"><span data-stu-id="59277-129">If you don't define the accessors correctly, the XAML processor can't access your attached property and anyone who tries to use it will probably get a XAML parser error.</span></span> <span data-ttu-id="59277-130">Außerdem erfordern Entwurfs- und Codiertools häufig die "\*Property"-Konventionen zum Benennen von Bezeichnern, wenn sie eine benutzerdefinierte Abhängigkeitseigenschaft in einer referenzierten Assembly feststellen.</span><span class="sxs-lookup"><span data-stu-id="59277-130">Also, design and coding tools often rely on the "\*Property" conventions for naming identifiers when they encounter a custom dependency property in a referenced assembly.</span></span>

## <a name="accessors"></a><span data-ttu-id="59277-131">Accessoren</span><span class="sxs-lookup"><span data-stu-id="59277-131">Accessors</span></span>

<span data-ttu-id="59277-132">Die Signatur für den **Get**_PropertyName_-Accessor lautet folgendermaßen.</span><span class="sxs-lookup"><span data-stu-id="59277-132">The signature for the **Get**_PropertyName_ accessor must be this.</span></span>

`public static` <span data-ttu-id="59277-133">_valueType_ **Get**_PropertyName_</span><span class="sxs-lookup"><span data-stu-id="59277-133">_valueType_ **Get**_PropertyName_</span></span> `(DependencyObject target)`

<span data-ttu-id="59277-134">Bei Microsoft Visual Basic lautet sie folgendermaßen.</span><span class="sxs-lookup"><span data-stu-id="59277-134">For Microsoft Visual Basic, it is this.</span></span>

`Public Shared Function Get`<span data-ttu-id="59277-135">_PropertyName_`(ByVal target As DependencyObject) As `_valueType_</span><span class="sxs-lookup"><span data-stu-id="59277-135">_PropertyName_`(ByVal target As DependencyObject) As `_valueType_</span></span>`)`

<span data-ttu-id="59277-136">Das *target*-Objekt kann in Ihrer Implementierung einen spezielleren Typ aufweisen, muss jedoch von [**DependencyObject**](https://msdn.microsoft.com/library/windows/apps/br242356) abgeleitet sein.</span><span class="sxs-lookup"><span data-stu-id="59277-136">The *target* object can be of a more specific type in your implementation, but must derive from [**DependencyObject**](https://msdn.microsoft.com/library/windows/apps/br242356).</span></span> <span data-ttu-id="59277-137">Der *valueType*-Rückgabewert kann in Ihrer Implementierung auch einen spezielleren Typ aufweisen.</span><span class="sxs-lookup"><span data-stu-id="59277-137">The *valueType* return value can also be of a more specific type in your implementation.</span></span> <span data-ttu-id="59277-138">Der grundlegende **Object**-Typ wird akzeptiert. Häufig soll jedoch Ihre angefügte Eigenschaft Typsicherheit erzwingen.</span><span class="sxs-lookup"><span data-stu-id="59277-138">The basic **Object** type is acceptable, but often you'll want your attached property to enforce type safety.</span></span> <span data-ttu-id="59277-139">Die Verwendung der Typisierung in den Getter- und Setter-Signaturen ist eine empfohlene Typsicherheitstechnik.</span><span class="sxs-lookup"><span data-stu-id="59277-139">The use of typing in the getter and setter signatures is a recommended type-safety technique.</span></span>

<span data-ttu-id="59277-140">Die Signatur für den \**festlegen \*\*\* PropertyName* Accessor lautet folgendermaßen.</span><span class="sxs-lookup"><span data-stu-id="59277-140">The signature for the \**Set\*\*\*PropertyName* accessor must be this.</span></span>

`public static void Set`<span data-ttu-id="59277-141">_PropertyName_` (DependencyObject target , `_valueType_</span><span class="sxs-lookup"><span data-stu-id="59277-141">_PropertyName_` (DependencyObject target , `_valueType_</span></span>` value)`

<span data-ttu-id="59277-142">Bei Microsoft Visual Basic lautet sie folgendermaßen.</span><span class="sxs-lookup"><span data-stu-id="59277-142">For Visual Basic, it is this.</span></span>

`Public Shared Sub Set`<span data-ttu-id="59277-143">_PropertyName_` (ByVal target As DependencyObject, ByVal value As `_valueType_</span><span class="sxs-lookup"><span data-stu-id="59277-143">_PropertyName_` (ByVal target As DependencyObject, ByVal value As `_valueType_</span></span>`)`

<span data-ttu-id="59277-144">Das *target*-Objekt kann in Ihrer Implementierung einen spezielleren Typ aufweisen, muss jedoch von [**DependencyObject**](https://msdn.microsoft.com/library/windows/apps/br242356) abgeleitet sein.</span><span class="sxs-lookup"><span data-stu-id="59277-144">The *target* object can be of a more specific type in your implementation, but must derive from [**DependencyObject**](https://msdn.microsoft.com/library/windows/apps/br242356).</span></span> <span data-ttu-id="59277-145">Das *value*-Objekt und dessen *valueType* können in Ihrer Implementierung einen spezielleren Typ aufweisen.</span><span class="sxs-lookup"><span data-stu-id="59277-145">The *value* object and its *valueType* can be of a more specific type in your implementation.</span></span> <span data-ttu-id="59277-146">Beachten Sie, dass der Wert für diese Methode die Eingabe ist, die vom XAML-Prozessor stammt, wenn er Ihre angefügte Eigenschaft im Markup feststellt.</span><span class="sxs-lookup"><span data-stu-id="59277-146">Remember that the value for this method is the input that comes from the XAML processor when it encounters your attached property in markup.</span></span> <span data-ttu-id="59277-147">Die Typkonvertierung oder vorhandene Markuperweiterung muss für den von Ihnen verwendeten Typ unterstützt werden, damit der entsprechende Typ auf der Grundlage eines Attributwerts (der letztlich nur eine Zeichenfolge ist) erstellt werden kann.</span><span class="sxs-lookup"><span data-stu-id="59277-147">There must be type conversion or existing markup extension support for the type you use, so that the appropriate type can be created from an attribute value (which is ultimately just a string).</span></span> <span data-ttu-id="59277-148">Der grundlegende **Object**-Typ ist akzeptabel. Häufig möchten Sie jedoch zusätzliche Typsicherheit erreichen.</span><span class="sxs-lookup"><span data-stu-id="59277-148">The basic **Object** type is acceptable, but often you'll want further type safety.</span></span> <span data-ttu-id="59277-149">Versehen Sie hierzu die Accessoren mit einer Typerzwingung.</span><span class="sxs-lookup"><span data-stu-id="59277-149">To accomplish that, put type enforcement in the accessors.</span></span>

> [!NOTE]
> <span data-ttu-id="59277-150">Es ist auch möglich, über die Eigenschaftselementsyntax eine angefügte Eigenschaft zu definieren, die den beabsichtigten Zweck angibt.</span><span class="sxs-lookup"><span data-stu-id="59277-150">It's also possible to define an attached property where the intended usage is through property element syntax.</span></span> <span data-ttu-id="59277-151">In diesem Fall benötigen Sie keine Typkonvertierung für die Werte. Sie müssen allerdings sicherstellen, dass die beabsichtigten Werte in XAML konstruierbar sind.</span><span class="sxs-lookup"><span data-stu-id="59277-151">In that case you don't need type conversion for the values, but you do need to assure that the values you intend can be constructed in XAML.</span></span> <span data-ttu-id="59277-152">[**VisualStateManager.VisualStateGroups**](https://msdn.microsoft.com/library/windows/apps/hh738505) ist ein Beispiel für eine vorhandene angefügte Eigenschaft, die nur die Eigenschaftselementverwendung unterstützt.</span><span class="sxs-lookup"><span data-stu-id="59277-152">[**VisualStateManager.VisualStateGroups**](https://msdn.microsoft.com/library/windows/apps/hh738505) is an example of an existing attached property that only supports property element usage.</span></span>

## <a name="code-example"></a><span data-ttu-id="59277-153">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="59277-153">Code example</span></span>

<span data-ttu-id="59277-154">In diesem Beispiel werden die Abhängigkeitseigenschaftsregistrierung (mithilfe der [**RegisterAttached**](https://msdn.microsoft.com/library/windows/apps/hh701833)-Methode) sowie die Accessoren **Get** und **Set** für eine benutzerdefinierte angefügte Eigenschaft dargestellt.</span><span class="sxs-lookup"><span data-stu-id="59277-154">This example shows the dependency property registration (using the [**RegisterAttached**](https://msdn.microsoft.com/library/windows/apps/hh701833) method), as well as the **Get** and **Set** accessors, for a custom attached property.</span></span> <span data-ttu-id="59277-155">Im Beispiel lautet der Name der angefügten Eigenschaft `IsMovable`.</span><span class="sxs-lookup"><span data-stu-id="59277-155">In the example, the attached property name is `IsMovable`.</span></span> <span data-ttu-id="59277-156">Daher müssen die Accessoren die Namen `GetIsMovable` und `SetIsMovable` aufweisen.</span><span class="sxs-lookup"><span data-stu-id="59277-156">Therefore, the accessors must be named `GetIsMovable` and `SetIsMovable`.</span></span> <span data-ttu-id="59277-157">Der Besitzer der angefügten Eigenschaft ist eine Dienstklasse mit dem Namen `GameService`, die nicht über eine eigene Benutzeroberfläche verfügt. Sie dient lediglich zur Bereitstellung der Dienste der angefügten Eigenschaft, wenn die angefügte Eigenschaft **GameService.IsMovable** verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="59277-157">The owner of the attached property is a service class named `GameService` that doesn't have a UI of its own; its purpose is only to provide the attached property services when the **GameService.IsMovable** attached property is used.</span></span>

<span data-ttu-id="59277-158">Definieren der angefügten Eigenschaft in C++ / CX ist etwas komplexer.</span><span class="sxs-lookup"><span data-stu-id="59277-158">Defining the attached property in C++/CX is a bit more complex.</span></span> <span data-ttu-id="59277-159">Sie müssen entscheiden, wie die Faktorverteilung zwischen der Header- und Codedatei lauten soll.</span><span class="sxs-lookup"><span data-stu-id="59277-159">You have to decide how to factor between the header and code file.</span></span> <span data-ttu-id="59277-160">Außerdem sollten Sie den Bezeichner als Eigenschaft mit nur einem **get**-Accessor verfügbar machen. Die Gründe hierfür werden unter [Benutzerdefinierte Abhängigkeitseigenschaften](custom-dependency-properties.md) erläutert.</span><span class="sxs-lookup"><span data-stu-id="59277-160">Also, you should expose the identifier as a property with only a **get** accessor, for reasons discussed in [Custom dependency properties](custom-dependency-properties.md).</span></span> <span data-ttu-id="59277-161">In C++ / CX müssen Sie definieren diese Eigenschaft-Feld-Beziehung explizit anstatt auf .NET **Readonly** -Schlüsselwörter und implizite Sicherung einfacher Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="59277-161">In C++/CX you must define this property-field relationship explicitly rather than relying on .NET **readonly** keywording and implicit backing of simple properties.</span></span> <span data-ttu-id="59277-162">Sie müssen auch die Registrierung der angefügten Eigenschaft innerhalb einer Hilfsfunktion durchführen, die nur einmal ausgeführt wird; dies erfolgt beim ersten Start der App, jedoch bevor XAML-Seiten geladen werden, die die angefügte Eigenschaft benötigen.</span><span class="sxs-lookup"><span data-stu-id="59277-162">You also need to perform the registration of the attached property within a helper function that only gets run once, when the app first starts but before any XAML pages that need the attached property are loaded.</span></span> <span data-ttu-id="59277-163">Normalerweise werden Ihre Hilfsfunktionen für die Registrierung von Eigenschaften für alle Abhängigkeits- oder angefügten Eigenschaften innerhalb des Konstruktors **App** / [**Application**](https://msdn.microsoft.com/library/windows/apps/br242325) im Code für Ihre app.xml-Datei aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="59277-163">The typical place to call your property registration helper functions for any and all dependency or attached properties is from within the **App** / [**Application**](https://msdn.microsoft.com/library/windows/apps/br242325) constructor in the code for your app.xaml file.</span></span>

```csharp
public class GameService : DependencyObject
{
    public static readonly DependencyProperty IsMovableProperty = 
    DependencyProperty.RegisterAttached(
      "IsMovable",
      typeof(Boolean),
      typeof(GameService),
      new PropertyMetadata(false)
    );
    public static void SetIsMovable(UIElement element, Boolean value)
    {
        element.SetValue(IsMovableProperty, value);
    }
    public static Boolean GetIsMovable(UIElement element)
    {
        return (Boolean)element.GetValue(IsMovableProperty);
    }
}
```

```vb
Public Class GameService
    Inherits DependencyObject

    Public Shared ReadOnly IsMovableProperty As DependencyProperty = 
        DependencyProperty.RegisterAttached("IsMovable",  
        GetType(Boolean), 
        GetType(GameService), 
        New PropertyMetadata(False))

    Public Shared Sub SetIsMovable(ByRef element As UIElement, value As Boolean)
        element.SetValue(IsMovableProperty, value)
    End Sub

    Public Shared Function GetIsMovable(ByRef element As UIElement) As Boolean
        GetIsMovable = CBool(element.GetValue(IsMovableProperty))
    End Function
End Class
```

```cppwinrt
// GameService.idl
namespace UserAndCustomControls
{
    runtimeclass GameService : Windows.UI.Xaml.DependencyObject
    {
        GameService();
        static Windows.UI.Xaml.DependencyProperty IsMovableProperty{ get; };
        Boolean IsMovable;
    }
}

// GameService.h
...
    bool IsMovable(){ return winrt::unbox_value<bool>(GetValue(m_IsMovableProperty)); }
    void IsMovable(bool value){ SetValue(m_IsMovableProperty, winrt::box_value(value)); }
    Windows::UI::Xaml::DependencyProperty IsMovableProperty(){ return m_IsMovableProperty; }

private:
    static Windows::UI::Xaml::DependencyProperty m_IsMovableProperty;
...

// GameService.cpp
...
Windows::UI::Xaml::DependencyProperty GameService::m_IsMovableProperty =
    Windows::UI::Xaml::DependencyProperty::RegisterAttached(
        L"IsMovable",
        winrt::xaml_typename<bool>(),
        winrt::xaml_typename<UserAndCustomControls::GameService>(),
        Windows::UI::Xaml::PropertyMetadata{ winrt::box_value(false) }
);
...
```

```cpp
// GameService.h
#pragma once

#include "pch.h"
//namespace WUX = Windows::UI::Xaml;

namespace UserAndCustomControls {
    public ref class GameService sealed : public WUX::DependencyObject {
    private:
        static WUX::DependencyProperty^ _IsMovableProperty;
    public:
        GameService::GameService();
        void GameService::RegisterDependencyProperties();
        static property WUX::DependencyProperty^ IsMovableProperty
        {
            WUX::DependencyProperty^ get() {
                return _IsMovableProperty;
            }
        };
        static bool GameService::GetIsMovable(WUX::UIElement^ element) {
            return (bool)element->GetValue(_IsMovableProperty);
        };
        static void GameService::SetIsMovable(WUX::UIElement^ element, bool value) {
            element->SetValue(_IsMovableProperty,value);
        }
    };
}

// GameService.cpp
#include "pch.h"
#include "GameService.h"

using namespace UserAndCustomControls;

using namespace Platform;
using namespace Windows::Foundation;
using namespace Windows::Foundation::Collections;
using namespace Windows::UI::Xaml;
using namespace Windows::UI::Xaml::Controls;
using namespace Windows::UI::Xaml::Data;
using namespace Windows::UI::Xaml::Documents;
using namespace Windows::UI::Xaml::Input;
using namespace Windows::UI::Xaml::Interop;
using namespace Windows::UI::Xaml::Media;

GameService::GameService() {};

GameService::RegisterDependencyProperties() {
    DependencyProperty^ GameService::_IsMovableProperty = DependencyProperty::RegisterAttached(
         "IsMovable", Platform::Boolean::typeid, GameService::typeid, ref new PropertyMetadata(false));
}
```

## <a name="using-your-custom-attached-property-in-xaml"></a><span data-ttu-id="59277-164">Verwenden der angefügten Eigenschaft in XAML</span><span class="sxs-lookup"><span data-stu-id="59277-164">Using your custom attached property in XAML</span></span>

<span data-ttu-id="59277-165">Nachdem Sie die angefügte Eigenschaft definiert und ihre unterstützenden Elemente als Teil des benutzerdefinierten Typs eingefügt haben, müssen Sie die Definitionen anschließend für die Verwendung von XAML verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="59277-165">After you have defined your attached property and included its support members as part of a custom type, you must then make the definitions available for XAML usage.</span></span> <span data-ttu-id="59277-166">Dazu müssen Sie einen XAML-Namespace zuordnen, der auf den Codenamespace mit der relevanten Klasse verweist.</span><span class="sxs-lookup"><span data-stu-id="59277-166">To do this, you must map a XAML namespace that will reference the code namespace that contains the relevant class.</span></span> <span data-ttu-id="59277-167">In Fällen, in denen Sie die angefügte Eigenschaft als Teil einer Bibliothek definiert haben, müssen Sie diese Bibliothek als Teil des App-Pakets für die App einfügen.</span><span class="sxs-lookup"><span data-stu-id="59277-167">In cases where you have defined the attached property as part of a library, you must include that library as part of the app package for the app.</span></span>

<span data-ttu-id="59277-168">Eine XML-Namespacezuordnung wird in der Regel im Stammelement einer XAML-Seite platziert.</span><span class="sxs-lookup"><span data-stu-id="59277-168">An XML namespace mapping for XAML is typically placed in the root element of a XAML page.</span></span> <span data-ttu-id="59277-169">Für die Klasse mit dem Namen `GameService` im Namespace `UserAndCustomControls`, der die in den vorherigen Ausschnitten dargestellten Definitionen der angefügten Eigenschaften enthält, sieht die Zuordnung z.B. folgendermaßen aus.</span><span class="sxs-lookup"><span data-stu-id="59277-169">For example, for the class named `GameService` in the namespace `UserAndCustomControls` that contains the attached property definitions shown in preceding snippets, the mapping might look like this.</span></span>

```xaml
<UserControl
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:uc="using:UserAndCustomControls"
  ... >
```

<span data-ttu-id="59277-170">Mithilfe der Zuordnung können Sie die angefügte `GameService.IsMovable` -Eigenschaft für beliebige Elemente festlegen, die Ihrer Zieldefinition entsprechen. Dies schließt auch einen vorhandenen von Windows-Runtime definierten Typ mit ein.</span><span class="sxs-lookup"><span data-stu-id="59277-170">Using the mapping, you can set your `GameService.IsMovable` attached property on any element that matches your target definition, including an existing type that Windows Runtime defines.</span></span>

```xaml
<Image uc:GameService.IsMovable="True" .../>
```

<span data-ttu-id="59277-171">Wenn Sie die Eigenschaft für ein Element festlegen, das sich auch im selben zugeordneten XML-Namespace befindet, müssen Sie das Präfix dennoch in den Namen der angefügten Eigenschaft einfügen.</span><span class="sxs-lookup"><span data-stu-id="59277-171">If you are setting the property on an element that is also within the same mapped XML namespace, you still must include the prefix on the attached property name.</span></span> <span data-ttu-id="59277-172">Das liegt daran, dass das Präfix den Besitzertyp qualifiziert.</span><span class="sxs-lookup"><span data-stu-id="59277-172">This is because the prefix qualifies the owner type.</span></span> <span data-ttu-id="59277-173">Es kann nicht angenommen werden, dass sich das Attribut der angefügten Eigenschaft innerhalb desselben XML-Namespace wie das Element befindet, in dem das Attribut enthalten ist, auch wenn Attribute gemäß normalen XML-Regeln Namespaces von Elementen erben können.</span><span class="sxs-lookup"><span data-stu-id="59277-173">The attached property's attribute cannot be assumed to be within the same XML namespace as the element where the attribute is included, even though, by normal XML rules, attributes can inherit namespace from elements.</span></span> <span data-ttu-id="59277-174">Wenn Sie beispielsweise `GameService.IsMovable` für einen benutzerdefinierten Typ von `ImageWithLabelControl` (Definition nicht dargestellt) festlegen, sieht das XAML-Element nach wie vor folgendermaßen aus, auch wenn beide im selben Codenamespace definiert und demselben Präfix zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="59277-174">For example, if you are setting `GameService.IsMovable` on a custom type of `ImageWithLabelControl` (definition not shown), and even if both were defined in the same code namespace mapped to same prefix, the XAML would still be this.</span></span>

```xaml
<uc:ImageWithLabelControl uc:GameService.IsMovable="True" .../>
```

> [!NOTE]
> <span data-ttu-id="59277-175">Wenn Sie eine XAML-Benutzeroberfläche mit C++ schreiben, müssen Sie den Header für den benutzerdefinierten Typ, der die angefügte Eigenschaft definiert, jedes Mal einfügen, sobald eine XAML-Seite diesen Typ verwendet.</span><span class="sxs-lookup"><span data-stu-id="59277-175">If you are writing a XAML UI with C++, you must include the header for the custom type that defines the attached property, any time that a XAML page uses that type.</span></span> <span data-ttu-id="59277-176">Jede XAML-Seite hat einen zugeordneten .xaml.h-CodeBehind-Header.</span><span class="sxs-lookup"><span data-stu-id="59277-176">Each XAML page has an associated .xaml.h code-behind header.</span></span> <span data-ttu-id="59277-177">Dort sollten Sie (mithilfe von **\#include**) den Header für die Definition des Besitzertyps der angefügten Eigenschaft einfügen.</span><span class="sxs-lookup"><span data-stu-id="59277-177">This is where you should include (using **\#include**) the header for the definition of the attached property's owner type.</span></span>

## <a name="value-type-of-a-custom-attached-property"></a><span data-ttu-id="59277-178">Werttyp einer benutzerdefinierten angefügten Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="59277-178">Value type of a custom attached property</span></span>

<span data-ttu-id="59277-179">Der Typ, der als Werttyp einer benutzerdefinierten angefügten Eigenschaft verwendet wird, wirkt sich auf die Nutzung, die Definition oder auf beides aus.</span><span class="sxs-lookup"><span data-stu-id="59277-179">The type that is used as the value type of a custom attached property affects the usage, the definition, or both the usage and definition.</span></span> <span data-ttu-id="59277-180">Der Werttyp der angefügten Eigenschaft wird an verschiedenen Stellen deklariert: in den Signaturen der **Get**- und **Set**-Accessormethoden und im *propertyType*-Parameter des [**RegisterAttached**](https://msdn.microsoft.com/library/windows/apps/hh701833)-Aufrufs.</span><span class="sxs-lookup"><span data-stu-id="59277-180">The attached property's value type is declared in several places: in the signatures of both the **Get** and **Set** accessor methods, and also as the *propertyType* parameter of the [**RegisterAttached**](https://msdn.microsoft.com/library/windows/apps/hh701833) call.</span></span>

<span data-ttu-id="59277-181">Der häufigste Werttyp für angefügte Eigenschaften (benutzerdefinierte oder andere) ist eine einfache Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="59277-181">The most common value type for attached properties (custom or otherwise) is a simple string.</span></span> <span data-ttu-id="59277-182">Das liegt daran, dass angefügte Eigenschaften in der Regel für die Nutzung mit XAML-Attributen vorgesehen sind, und durch die Verwendung einer Zeichenfolge als Werttyp bleiben die Eigenschaften einfach.</span><span class="sxs-lookup"><span data-stu-id="59277-182">This is because attached properties are generally intended for XAML attribute usage, and using a string as the value type keeps the properties lightweight.</span></span> <span data-ttu-id="59277-183">Andere Grundtypen, die über eine systemeigene Konvertierung in Zeichenfolgenmethoden verfügen (z. B. eine ganze Zahl, ein Double oder ein Enumerationswert), werden ebenfalls häufig als Werttypen für angefügte Eigenschaften verwendet.</span><span class="sxs-lookup"><span data-stu-id="59277-183">Other primitives that have native conversion to string methods, such as integer, double, or an enumeration value, are also common as value types for attached properties.</span></span> <span data-ttu-id="59277-184">Sie können andere Werttypen – die die systemeigene Zeichenfolgekonvertierung nicht unterstützen – als Wert der angefügten Eigenschaft verwenden.</span><span class="sxs-lookup"><span data-stu-id="59277-184">You can use other value types—ones that don't support native string conversion—as the attached property value.</span></span> <span data-ttu-id="59277-185">Dies hat jedoch zur Folge, dass eine Auswahl in Bezug auf die Nutzung oder Implementierung getroffen werden muss:</span><span class="sxs-lookup"><span data-stu-id="59277-185">However, this entails making a choice about either the usage or the implementation:</span></span>

- <span data-ttu-id="59277-186">Sie können die angefügte Eigenschaft so belassen, wie sie ist. Dann kann die angefügte Eigenschaft die Nutzung nur unterstützen, wenn die angefügte Eigenschaft ein Eigenschaftselement darstellt und der Wert als Objektelement deklariert wurde.</span><span class="sxs-lookup"><span data-stu-id="59277-186">You can leave the attached property as it is, but the attached property can support usage only where the attached property is a property element, and the value is declared as an object element.</span></span> <span data-ttu-id="59277-187">In diesem Fall muss der Eigenschaftstyp die XAML-Nutzung als Objektelement unterstützen.</span><span class="sxs-lookup"><span data-stu-id="59277-187">In this case, the property type does have to support XAML usage as an object element.</span></span> <span data-ttu-id="59277-188">Überprüfen Sie bei vorhandenen Windows-Runtime-Referenzklassen die XAML-Syntax, um sicherzustellen, dass der Typ die XAML-Objektelementnutzung unterstützt.</span><span class="sxs-lookup"><span data-stu-id="59277-188">For existing Windows Runtime reference classes, check the XAML syntax to make sure that the type supports XAML object element usage.</span></span>
- <span data-ttu-id="59277-189">Sie können die angefügte Eigenschaft so belassen, wie sie ist. Dann können Sie diese jedoch nur in einer Attributnutzung über eine XAML-Referenztechnik wie **Binding** oder **StaticResource** verwenden, die als Zeichenfolge ausgedrückt werden kann.</span><span class="sxs-lookup"><span data-stu-id="59277-189">You can leave the attached property as it is, but use it only in an attribute usage through a XAML reference technique such as a **Binding** or **StaticResource** that can be expressed as a string.</span></span>

## <a name="more-about-the-canvasleft-example"></a><span data-ttu-id="59277-190">Weitere Informationen zum **Canvas.Left**-Beispiel</span><span class="sxs-lookup"><span data-stu-id="59277-190">More about the **Canvas.Left** example</span></span>

<span data-ttu-id="59277-191">In vorherigen Beispielen für die Nutzung angefügter Eigenschaften wurden verschiedene Methoden zum Festlegen der angefügten Eigenschaft [**Canvas.Left**](https://msdn.microsoft.com/library/windows/apps/hh759771) gezeigt.</span><span class="sxs-lookup"><span data-stu-id="59277-191">In earlier examples of attached property usages we showed different ways to set the [**Canvas.Left**](https://msdn.microsoft.com/library/windows/apps/hh759771) attached property.</span></span> <span data-ttu-id="59277-192">Doch wie wirkt sich dies auf die Interaktionen einer [**Canvas**](https://msdn.microsoft.com/library/windows/apps/br209267) mit Ihrem Objekt aus, und wann tritt dies auf?</span><span class="sxs-lookup"><span data-stu-id="59277-192">But what does that change about how a [**Canvas**](https://msdn.microsoft.com/library/windows/apps/br209267) interacts with your object, and when does that happen?</span></span> <span data-ttu-id="59277-193">Wir schauen uns dieses bestimmte Beispiel genauer an. Es ist beim Implementieren einer angefügten Eigenschaft interessant zu wissen, wozu eine typische Besitzerklasse der angefügten Eigenschaft die Werte der angefügten Eigenschaft außerdem verwendet, wenn sie diese in anderen Objekten findet.</span><span class="sxs-lookup"><span data-stu-id="59277-193">We'll examine this particular example further, because if you implement an attached property, it's interesting to see what else a typical attached property owner class intends to do with its attached property values if it finds them on other objects.</span></span>

<span data-ttu-id="59277-194">Eine [**Canvas**](https://msdn.microsoft.com/library/windows/apps/br209267) dient hauptsächlich dazu, einen Layoutcontainer mit absoluter Position auf der UI darzustellen.</span><span class="sxs-lookup"><span data-stu-id="59277-194">The main function of a [**Canvas**](https://msdn.microsoft.com/library/windows/apps/br209267) is to be an absolute-positioned layout container in UI.</span></span> <span data-ttu-id="59277-195">Die untergeordneten Elemente einer **Canvas** werden in der definierten Basisklasseneigenschaft [**Children**](https://msdn.microsoft.com/library/windows/apps/br227514) gespeichert.</span><span class="sxs-lookup"><span data-stu-id="59277-195">The children of a **Canvas** are stored in a base-class defined property [**Children**](https://msdn.microsoft.com/library/windows/apps/br227514).</span></span> <span data-ttu-id="59277-196">**Canvas** verwendet als einziges Panel eine absolute Positionierung.</span><span class="sxs-lookup"><span data-stu-id="59277-196">Of all the panels **Canvas** is the only one that uses absolute positioning.</span></span> <span data-ttu-id="59277-197">Das Objektmodell des allgemeinen [**UIElement**](https://msdn.microsoft.com/library/windows/apps/br208911)-Typs würde übermäßig aufgebläht werden, wenn Eigenschaften hinzugefügt werden, die nur für **Canvas** und die speziellen **UIElement**-Fälle wichtig wären, in denen diese untergeordnete Elemente eines **UIElement** sind.</span><span class="sxs-lookup"><span data-stu-id="59277-197">It would've bloated the object model of the common [**UIElement**](https://msdn.microsoft.com/library/windows/apps/br208911) type to add properties that might only be of concern to **Canvas** and those particular **UIElement** cases where they are child elements of a **UIElement**.</span></span> <span data-ttu-id="59277-198">Wenn Sie die Eigenschaften von Layoutsteuerelementen einer **Canvas** als angefügte Eigenschaften definieren, die von allen **UIElement**-Elementen verwendet werden können, ist das Objektmodell übersichtlicher.</span><span class="sxs-lookup"><span data-stu-id="59277-198">Defining the layout control properties of a **Canvas** to be attached properties that any **UIElement** can use keeps the object model cleaner.</span></span>

<span data-ttu-id="59277-199">Um als Panel praktikabel zu sein, besitzt [**Canvas**](https://msdn.microsoft.com/library/windows/apps/br209267) Verhaltensweisen, die die Frameworkmethoden [**Measure**](https://msdn.microsoft.com/library/windows/apps/br208952) und [**Arrange**](https://msdn.microsoft.com/library/windows/apps/br208914) überschreiben.</span><span class="sxs-lookup"><span data-stu-id="59277-199">In order to be a practical panel, [**Canvas**](https://msdn.microsoft.com/library/windows/apps/br209267) has behavior that overrides the framework-level [**Measure**](https://msdn.microsoft.com/library/windows/apps/br208952) and [**Arrange**](https://msdn.microsoft.com/library/windows/apps/br208914) methods.</span></span> <span data-ttu-id="59277-200">Hier wird von **Canvas** nach Werten der angefügten Eigenschaftswerte für ihre untergeordneten Elemente gesucht.</span><span class="sxs-lookup"><span data-stu-id="59277-200">This is where **Canvas** actually checks for attached property values on its children.</span></span> <span data-ttu-id="59277-201">Ein Teil der Muster **Measure** und **Arrange** ist eine Schleife, die alle Inhalte durchläuft. Ein Panel besitzt die Eigenschaft [**Children**](https://msdn.microsoft.com/library/windows/apps/br227514), die explizit angibt, was als untergeordnetes Element eines Panels gelten soll.</span><span class="sxs-lookup"><span data-stu-id="59277-201">Part of both the **Measure** and **Arrange** patterns is a loop that iterates over any content, and a panel has the [**Children**](https://msdn.microsoft.com/library/windows/apps/br227514) property that makes it explicit what's supposed to be considered the child of a panel.</span></span> <span data-ttu-id="59277-202">Das **Canvas**-Layoutverhalten durchläuft diese untergeordneten Elemente und führt statische [**Canvas.GetLeft**](https://msdn.microsoft.com/library/windows/apps/br209269)- und [**Canvas.GetTop**](https://msdn.microsoft.com/library/windows/apps/br209270)-Aufrufe für alle untergeordneten Elemente aus, um zu ermitteln, ob diese angefügten Eigenschaften einen nicht standardmäßigen Wert enthalten (der standardmäßige Wert ist 0).</span><span class="sxs-lookup"><span data-stu-id="59277-202">So the **Canvas** layout behavior iterates through these children, and makes static [**Canvas.GetLeft**](https://msdn.microsoft.com/library/windows/apps/br209269) and [**Canvas.GetTop**](https://msdn.microsoft.com/library/windows/apps/br209270) calls on each child to see whether those attached properties contain a non-default value (default is 0).</span></span> <span data-ttu-id="59277-203">Mithilfe dieser Werte werden die untergeordneten Elemente auf der verfügbaren **Canvas**-Layoutfläche gemäß den von den einzelnen untergeordneten Elementen bereitgestellten spezifischen Werten absolut positioniert. Anschließend wird mithilfe von **Arrange** ein Commit für sie ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="59277-203">These values are then used to absolutely position each child in the **Canvas** available layout space according to the specific values provided by each child, and committed using **Arrange**.</span></span>

<span data-ttu-id="59277-204">Der Code sieht ähnlich dem folgenden Pseudocode.</span><span class="sxs-lookup"><span data-stu-id="59277-204">The code looks something like this pseudocode.</span></span>

```syntax
protected override Size ArrangeOverride(Size finalSize)
{
    foreach (UIElement child in Children)
    {
        double x = (double) Canvas.GetLeft(child);
        double y = (double) Canvas.GetTop(child);
        child.Arrange(new Rect(new Point(x, y), child.DesiredSize));
    }
    return base.ArrangeOverride(finalSize); 
    // real Canvas has more sophisticated sizing
}
```

> [!NOTE]
> <span data-ttu-id="59277-205">Weitere Informationen zur Funktionsweise von Panels finden Sie in der [XAML-Übersicht über benutzerdefinierte Panels](https://msdn.microsoft.com/library/windows/apps/mt228351).</span><span class="sxs-lookup"><span data-stu-id="59277-205">For more info on how panels work, see [XAML custom panels overview](https://msdn.microsoft.com/library/windows/apps/mt228351).</span></span>

## <a name="related-topics"></a><span data-ttu-id="59277-206">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="59277-206">Related topics</span></span>

* [**<span data-ttu-id="59277-207">RegisterAttached</span><span class="sxs-lookup"><span data-stu-id="59277-207">RegisterAttached</span></span>**](https://msdn.microsoft.com/library/windows/apps/hh701833)
* [<span data-ttu-id="59277-208">Übersicht über angefügte Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="59277-208">Attached properties overview</span></span>](attached-properties-overview.md)
* [<span data-ttu-id="59277-209">Benutzerdefinierte Abhängigkeitseigenschaften</span><span class="sxs-lookup"><span data-stu-id="59277-209">Custom dependency properties</span></span>](custom-dependency-properties.md)
* [<span data-ttu-id="59277-210">Übersicht über XAML</span><span class="sxs-lookup"><span data-stu-id="59277-210">XAML overview</span></span>](xaml-overview.md)
