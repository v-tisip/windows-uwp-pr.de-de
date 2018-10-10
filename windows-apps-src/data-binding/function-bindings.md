---
author: jwmsft
description: Die xBind-Markuperweiterung mit der Funktionen im Markup verwendet werden.
title: 'X: Bind-Funktionen'
ms.author: jimwalk
ms.date: 04/26/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, xBind
ms.localizationpriority: medium
ms.openlocfilehash: b160b1e711f6e56b14f0d6e0e83e9f9150be5e90
ms.sourcegitcommit: 49aab071aa2bd88f1c165438ee7e5c854b3e4f61
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2018
ms.locfileid: "4472573"
---
# <a name="functions-in-xbind"></a>X: Bind-Funktionen

**Hinweis**  Allgemeine Informationen zur Verwendung der Datenbindung in Ihrer App mit **{x:Bind}** (sowie einen Gesamtvergleich von **{x:Bind}** und **{Binding}**) finden Sie unter [Datenbindung im Detail](https://msdn.microsoft.com/library/windows/apps/mt210946).

Ab Windows10, Version 1607, unterstützt **{x: Bind}** die Verwendung einer Funktion als blattbildenden Schrittdes Bindungspfades. Dadurch wird Folgendes ermöglicht:

- Eine einfachere Möglichkeit der Konvertierung von Werten
- Eine Möglichkeit, Bindungen von mehr als einem Parameter abhängig zu machen

> [!NOTE]
> Wenn Sie Funktionen für **{x: Bind}** verwenden möchten, muss die Ziel-SDK-Version 14393 oder höher sein. Sie können keine Funktionen verwenden, wenn Ihre App für frühere Versionen von Windows10 bestimmt ist. Weitere Informationen zu Zielversionen finden Sie unter [Versionsadaptiver Code](https://msdn.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code).

Im folgenden Beispiel werden Hintergrund und Vordergrund des Elements an Funktionen gebunden, um eine Konvertierung basierend auf dem Farbparameter durchzuführen

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

## <a name="xaml-attribute-usage"></a>XAML-Attributsyntax

``` syntax
<object property="{x:Bind pathToFunction.FunctionName(functionParameter1, functionParameter2, ...), bindingProperties}" ... />
```

## <a name="path-to-the-function"></a>Pfad der Funktion

Der Pfad der Funktion wird wie jeder andere Eigenschaftspfad angegeben. Er kann Punkte (.), Indexer oder Umwandlungen für die Suche nach der Funktion enthalten.

Statische Funktionen können mithilfe der XMLNamespace:ClassName.MethodName-Syntax angegeben werden. Verwenden Sie z. B. die unten Syntax für die Bindung an statische Funktionen im CodeBehind.

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

Sie können auch Systemfunktionen direkt im Markup verwenden, um einfache Szenarien wie das Datum formatieren, Formatieren von Text, Text Konkatinierungen usw., z. B. auszuführen:
```xaml
<Page 
     xmlns:sys="using:System"
     xmlns:local="using:MyPage">
     ...
     <CalendarDatePicker Date="{x:Bind sys:DateTime.Parse(TextBlock1.Text)}" />
     <TextBlock Text="{x:Bind sys:String.Format('{0} is now available in {1}', local:MyPage.personName, local:MyPage.location)}" />
</Page>
```

Ist der Modus OneWay/TwoWay, wird auf den Pfad der Funktion eine Änderungserkennung angewendet, und die Bindung wird neu ausgewertet, wenn diese Objekte geändert wurden.

Für die zu bindende Funktion müssen folgende Voraussetzungen gelten:

- Code und die Metadaten müssen auf sie zugreifen können, d.h. interne/private Aktionen in C#, aber für C++/CX werden öffentliche WinRT-Methoden benötigt
- Überladung basiert auf der Anzahl der Argumente, nicht auf ihrem Typ, und es wird die erste Übereinstimmung mit dieser Anzahl von Argumenten gesucht
- Die Argumenttypen müssen den übergebenen Daten entsprechen. Es werden keine einschränkenden Konvertierungen durchgeführt
- Der Rückgabetyp der Funktion muss mit dem Typ der Eigenschaft übereinstimmen, für die die Bindung verwendet wird

Beginnen mit dem nächsten wichtigen Update für Windows 10, wird das Bindungsmodul Benachrichtigungen über eigenschaftsänderungen mit den Namen der Funktion ausgelöst reagieren und Bindungen nach Bedarf neu ausgewertet. Beispiel: 

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
> Sie können Funktionen in X: Bind um zu erreichen die gleichen Szenarien wie was über Konverter und MultiBinding in WPF unterstützt wurde.

## <a name="function-arguments"></a>Funktionsargumente

Mehrere Argumente können durch Komma (,) voneinander getrennt angegeben werden

- Bindungspfad – dieselbe Syntax wie bei einer direkten Bindung an das Objekt.
  - Ist der Modus OneWay/TwoWay, wird eine Änderungserkennung angewendet, und die Bindung wird neu ausgewertet, wenn diese Objekte geändert wurden.
- Konstante Zeichenfolge in Anführungszeichen – Anführungszeichen müssen gesetzt werden, um Zeichenfolgen kenntlich zu machen Das Caret-Symbol (^) kann als Escapezeichen für Anführungszeichen innerhalb von Zeichenfolgen verwendet werden.
- Konstante Zahl – z. B. -123.456
- Boolean – als "x: True" oder "x: False" angeben

### <a name="two-way-function-bindings"></a>Bidirektionale Funktionsbindung

In einem Szenario mit bidirektionaler Bindung muss eine zweite Funktion für die umgekehrte Bindungsrichtung angegeben werden. Dies erfolgt mithilfe der **BindBack** Binding-Eigenschaft. In dem Beispiel unten haben die Funktion zu ergreifende Maßnahme ein Argument, das dem Wert entspricht, die das Modell übernommen werden muss.
```xaml
<TextBlock Text="{x:Bind a.MyFunc(b), BindBack=a.MyFunc2, Mode=TwoWay}" />
```
