---
author: jwmsft
description: Die xBind-Markuperweiterung mit der Funktionen im Markup verwendet werden.
title: Funktionen in x:Bind
ms.author: jimwalk
ms.date: 04/26/2018
ms.topic: article
keywords: Windows 10, Uwp, xBind
ms.localizationpriority: medium
ms.openlocfilehash: 7e00762f389791fb3972b6f224759d35bf547e38
ms.sourcegitcommit: 38f06f1714334273d865935d9afb80efffe97a17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6192708"
---
# <a name="functions-in-xbind"></a><span data-ttu-id="85d96-104">Funktionen in x:Bind</span><span class="sxs-lookup"><span data-stu-id="85d96-104">Functions in x:Bind</span></span>

<span data-ttu-id="85d96-105">**Hinweis:** allgemeine Informationen zur Verwendung von Daten Bindung in Ihrer app mit **{X: Bind}** (und für einen vollständigen Vergleich zwischen **{X: Bind}** und **{Binding}**) finden Sie unter [Datenbindung im Detail](https://msdn.microsoft.com/library/windows/apps/mt210946).</span><span class="sxs-lookup"><span data-stu-id="85d96-105">**Note**For general info about using data binding in your app with **{x:Bind}** (and for an all-up comparison between **{x:Bind}** and **{Binding}**), see [Data binding in depth](https://msdn.microsoft.com/library/windows/apps/mt210946).</span></span>

<span data-ttu-id="85d96-106">Ab Windows10, Version 1607, unterstützt **{x: Bind}** die Verwendung einer Funktion als blattbildenden Schrittdes Bindungspfades.</span><span class="sxs-lookup"><span data-stu-id="85d96-106">Starting in Windows 10, version 1607, **{x:Bind}** supports using a function as the leaf step of the binding path.</span></span> <span data-ttu-id="85d96-107">Dadurch wird Folgendes ermöglicht:</span><span class="sxs-lookup"><span data-stu-id="85d96-107">This enables:</span></span>

- <span data-ttu-id="85d96-108">Eine einfachere Möglichkeit der Konvertierung von Werten</span><span class="sxs-lookup"><span data-stu-id="85d96-108">A simpler way to achieve value conversion</span></span>
- <span data-ttu-id="85d96-109">Eine Möglichkeit, Bindungen von mehr als einem Parameter abhängig zu machen</span><span class="sxs-lookup"><span data-stu-id="85d96-109">A way for bindings to depend on more than one parameter</span></span>

> [!NOTE]
> <span data-ttu-id="85d96-110">Wenn Sie Funktionen für **{x: Bind}** verwenden möchten, muss die Ziel-SDK-Version 14393 oder höher sein.</span><span class="sxs-lookup"><span data-stu-id="85d96-110">To use functions with **{x:Bind}**, your app's minimum target SDK version must be 14393 or later.</span></span> <span data-ttu-id="85d96-111">Sie können keine Funktionen verwenden, wenn Ihre App für frühere Versionen von Windows10 bestimmt ist.</span><span class="sxs-lookup"><span data-stu-id="85d96-111">You can't use functions when your app targets earlier versions of Windows 10.</span></span> <span data-ttu-id="85d96-112">Weitere Informationen zu Zielversionen finden Sie unter [Versionsadaptiver Code](https://msdn.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code).</span><span class="sxs-lookup"><span data-stu-id="85d96-112">For more info about target versions, see [Version adaptive code](https://msdn.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code).</span></span>

<span data-ttu-id="85d96-113">Im folgenden Beispiel werden Hintergrund und Vordergrund des Elements an Funktionen gebunden, um eine Konvertierung basierend auf dem Farbparameter durchzuführen</span><span class="sxs-lookup"><span data-stu-id="85d96-113">In the following example, the background and foreground of the item are bound to functions to do conversion based on the color parameter</span></span>

```xaml
<DataTemplate x:DataType="local:ColorEntry">
    <Grid Background="{x:Bind local:ColorEntry.Brushify(Color), Mode=OneWay}" Width="240">
        <TextBlock Text="{x:Bind ColorName}" Foreground="{x:Bind TextColor(Color)}" Margin="10,5" />
    </Grid>
</DataTemplate>
```

```csharp
class ColorEntry
{
    public string ColorName { get; set; }
    public Color Color { get; set; }

    public static SolidColorBrush Brushify(Color c)
    {
        return new SolidColorBrush(c);
    }

    public SolidColorBrush TextColor(Color c)
    {
        return new SolidColorBrush(((c.R * 0.299 + c.G * 0.587 + c.B * 0.114) > 150) ? Colors.Black : Colors.White);
    }
}
```

## <a name="xaml-attribute-usage"></a><span data-ttu-id="85d96-114">XAML-Attributsyntax</span><span class="sxs-lookup"><span data-stu-id="85d96-114">XAML attribute usage</span></span>

``` syntax
<object property="{x:Bind pathToFunction.FunctionName(functionParameter1, functionParameter2, ...), bindingProperties}" ... />
```

## <a name="path-to-the-function"></a><span data-ttu-id="85d96-115">Pfad der Funktion</span><span class="sxs-lookup"><span data-stu-id="85d96-115">Path to the function</span></span>

<span data-ttu-id="85d96-116">Der Pfad der Funktion wird wie jeder andere Eigenschaftspfad angegeben. Er kann Punkte (.), Indexer oder Umwandlungen für die Suche nach der Funktion enthalten.</span><span class="sxs-lookup"><span data-stu-id="85d96-116">The path to the function is specified like other property paths and can include dots (.), indexers or casts to locate the function.</span></span>

<span data-ttu-id="85d96-117">Statische Funktionen können mithilfe der XMLNamespace:ClassName.MethodName-Syntax angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="85d96-117">Static functions can be specified using XMLNamespace:ClassName.MethodName syntax.</span></span> <span data-ttu-id="85d96-118">Verwenden Sie z. B. die unten Syntax für die Bindung an statische Funktionen im CodeBehind.</span><span class="sxs-lookup"><span data-stu-id="85d96-118">For example, use the below syntax for binding to static functions in code-behind.</span></span>

```xaml
<Page 
     xmlns:local="using:MyPage">
     ...
     <Grid x:Name="myGrid" Background="Black" >
        <TextBlock Foreground="{x:Bind local:GenerateAppropriateForeground(myGrid.Background)}" Text="Hello World!" />
    </Grid>
</Page>
```
```csharp
public class MyPage : Page
{
    public static GenerateAppropriateForeground(SolidColorBrush background)
    {
        //Implement static function
        ...
    }
}
```

<span data-ttu-id="85d96-119">Sie können auch Systemfunktionen direkt im Markup verwenden, um einfache Szenarien wie das Datum formatieren, Formatieren von Text, Text Konkatinierungen usw., z. B. auszuführen:</span><span class="sxs-lookup"><span data-stu-id="85d96-119">You can also use system functions directly in markup to accomplish simple scenarios like date formatting, text formatting, text concatenations, etc., For example:</span></span>
```xaml
<Page 
     xmlns:sys="using:System"
     xmlns:local="using:MyPage">
     ...
     <CalendarDatePicker Date="{x:Bind sys:DateTime.Parse(TextBlock1.Text)}" />
     <TextBlock Text="{x:Bind sys:String.Format('{0} is now available in {1}', local:MyPage.personName, local:MyPage.location)}" />
</Page>
```

<span data-ttu-id="85d96-120">Ist der Modus OneWay/TwoWay, wird auf den Pfad der Funktion eine Änderungserkennung angewendet, und die Bindung wird neu ausgewertet, wenn diese Objekte geändert wurden.</span><span class="sxs-lookup"><span data-stu-id="85d96-120">If the mode is OneWay/TwoWay, then the function path will have change detection performed on it, and the binding will be re-evaluated if there are changes to those objects.</span></span>

<span data-ttu-id="85d96-121">Für die zu bindende Funktion müssen folgende Voraussetzungen gelten:</span><span class="sxs-lookup"><span data-stu-id="85d96-121">The function being bound to needs to:</span></span>

- <span data-ttu-id="85d96-122">Code und die Metadaten müssen auf sie zugreifen können, d.h. interne/private Aktionen in C#, aber für C++/CX werden öffentliche WinRT-Methoden benötigt</span><span class="sxs-lookup"><span data-stu-id="85d96-122">Be accessible to the code and metadata – so internal / private work in C#, but C++/CX will need methods to be public WinRT methods</span></span>
- <span data-ttu-id="85d96-123">Überladung basiert auf der Anzahl der Argumente, nicht auf ihrem Typ, und es wird die erste Übereinstimmung mit dieser Anzahl von Argumenten gesucht</span><span class="sxs-lookup"><span data-stu-id="85d96-123">Overloading is based on the number of arguments, not type, and it will try to match to the first overload with that many arguments</span></span>
- <span data-ttu-id="85d96-124">Die Argumenttypen müssen den übergebenen Daten entsprechen. Es werden keine einschränkenden Konvertierungen durchgeführt</span><span class="sxs-lookup"><span data-stu-id="85d96-124">The argument types need to match the data being passed in – we don’t do narrowing conversions</span></span>
- <span data-ttu-id="85d96-125">Der Rückgabetyp der Funktion muss mit dem Typ der Eigenschaft übereinstimmen, für die die Bindung verwendet wird</span><span class="sxs-lookup"><span data-stu-id="85d96-125">The return type of the function needs to match the type of the property that is using the binding</span></span>

<span data-ttu-id="85d96-126">Beginnen mit dem nächsten wichtigen Update für Windows 10, wird das Bindungsmodul Benachrichtigungen über eigenschaftsänderungen ausgelöst, mit dem Funktionsnamen reagieren und Bindungen nach Bedarf neu ausgewertet.</span><span class="sxs-lookup"><span data-stu-id="85d96-126">Starting with the next major update to Windows 10, the binding engine will react to property change notifications fired with the function name and re-evaluate bindings as necessary.</span></span> <span data-ttu-id="85d96-127">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="85d96-127">For example:</span></span> 

```XAML
<DataTemplate x:DataType="local:Person">
   <StackPanel>
      <TextBlock Text="{x:Bind FullName}" />
      <Image Source="{x:Bind IconToBitmap(Icon, CancellationToken), Mode=OneWay}" />
   </StackPanel>
</DataTemplate>
```
```csharp
public class Person:INotifyPropertyChanged
{
    //Implementation for an Icon property and a CancellationToken property with PropertyChanged notifications
    ...

    //IconToBitmap function is essentially a multi binding converter between several options.
    public Uri IconToBitmap (Uri icon, Uri cancellationToken)
    {
        Uri foo = new Uri(...);        
        if (isCancelled)
        {
            foo = cancellationToken;
        }
        else 
        {
            if (this.fullName.Contains("Sr"))
            {
               //pass a different Uri back
               foo = new Uri(...);
            }
            else
            {
                foo = icon;
            }
        }
        return foo;
    }

    //Ensure FullName property handles change notification on itself as well as IconToBitmap since the function uses it
    public string FullName
    {
        get { return this.fullName; }
        set 
        {
            this.fullName = value;
            this.OnPropertyChanged ();
            this.OnPropertyChanged ("IconToBitmap"); 
            //this ensures Image.Source binding re-evaluates when FullName changes in addition to Icon and CancellationToken
        }
    }
}
```

> [!TIP]
> <span data-ttu-id="85d96-128">Sie können Funktionen in X: Bind verwenden, erreichen Sie die gleichen Szenarien wie was über Konverter und MultiBinding in WPF unterstützt wurde.</span><span class="sxs-lookup"><span data-stu-id="85d96-128">You can use functions in x:Bind to achieve the same scenarios as what was supported through Converters and MultiBinding in WPF.</span></span>

## <a name="function-arguments"></a><span data-ttu-id="85d96-129">Funktionsargumente</span><span class="sxs-lookup"><span data-stu-id="85d96-129">Function arguments</span></span>

<span data-ttu-id="85d96-130">Mehrere Argumente können durch Komma (,) voneinander getrennt angegeben werden</span><span class="sxs-lookup"><span data-stu-id="85d96-130">Multiple function arguments can be specified, separated by comma's (,)</span></span>

- <span data-ttu-id="85d96-131">Bindungspfad – dieselbe Syntax wie bei einer direkten Bindung an das Objekt.</span><span class="sxs-lookup"><span data-stu-id="85d96-131">Binding Path – Same syntax as if you were binding directly to that object.</span></span>
  - <span data-ttu-id="85d96-132">Ist der Modus OneWay/TwoWay, wird eine Änderungserkennung angewendet, und die Bindung wird neu ausgewertet, wenn diese Objekte geändert wurden.</span><span class="sxs-lookup"><span data-stu-id="85d96-132">If the mode is OneWay/TwoWay then change detection will be performed and the binding re-evaluated upon object changes</span></span>
- <span data-ttu-id="85d96-133">Konstante Zeichenfolge in Anführungszeichen – Anführungszeichen müssen gesetzt werden, um Zeichenfolgen kenntlich zu machen</span><span class="sxs-lookup"><span data-stu-id="85d96-133">Constant string enclosed in quotes – quotes are needed to designate it as a string.</span></span> <span data-ttu-id="85d96-134">Das Caret-Symbol (^) kann als Escapezeichen für Anführungszeichen innerhalb von Zeichenfolgen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="85d96-134">Hat (^) can be used to escape quotes in strings</span></span>
- <span data-ttu-id="85d96-135">Konstante Zahl – z. B. -123.456</span><span class="sxs-lookup"><span data-stu-id="85d96-135">Constant Number - for example -123.456</span></span>
- <span data-ttu-id="85d96-136">Boolean – als "x: True" oder "x: False" angeben</span><span class="sxs-lookup"><span data-stu-id="85d96-136">Boolean – specified as "x:True" or "x:False"</span></span>

### <a name="two-way-function-bindings"></a><span data-ttu-id="85d96-137">Bidirektionale Funktionsbindung</span><span class="sxs-lookup"><span data-stu-id="85d96-137">Two way function bindings</span></span>

<span data-ttu-id="85d96-138">In einem Szenario mit bidirektionaler Bindung muss eine zweite Funktion für die umgekehrte Bindungsrichtung angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="85d96-138">In a two-way binding scenario, a second function must be specified for the reverse direction of the binding.</span></span> <span data-ttu-id="85d96-139">Dies erfolgt mithilfe der **BindBack** Binding-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="85d96-139">This is done using the **BindBack** binding property.</span></span> <span data-ttu-id="85d96-140">In dem folgenden Beispiel wird die Funktion zu ergreifende Maßnahme ein Argument, das dem Wert entspricht, die das Modell übernommen werden muss.</span><span class="sxs-lookup"><span data-stu-id="85d96-140">In the below example, the function should take one argument which is the value that needs to be pushed back to the model.</span></span>
```xaml
<TextBlock Text="{x:Bind a.MyFunc(b), BindBack=a.MyFunc2, Mode=TwoWay}" />
```
