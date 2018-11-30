---
description: Dient zum eindeutigen Identifizieren von Objektelementen für den Zugriff auf das instanziierte Objekt aus CodeBehind- oder allgemeinem Code.
title: xName-Attribut
ms.assetid: 4FF1F3ED-903A-4305-B2BD-DCD29E0C9E6D
ms.date: 02/08/2017
ms.topic: article
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 6ef1a6047a7c462961f40ae8913881125e2331bb
ms.sourcegitcommit: d2517e522cacc5240f7dffd5bc1eaa278e3f7768
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "8323344"
---
# <a name="xname-attribute"></a>x:Name-Attribut


Dient zum eindeutigen Identifizieren von Objektelementen für den Zugriff auf das instanziierte Objekt aus CodeBehind oder allgemeinem Code. Nach Anwendung auf ein zugrunde liegendes Programmiermodell kann **x:Name** als Äquivalent der Variablen mit einem Objektverweis betrachtet werden (gemäß Rückgabe von einem Konstruktor).

## <a name="xaml-attribute-usage"></a>XAML-Attributsyntax

``` syntax
<object x:Name="XAMLNameValue".../>
```

## <a name="xaml-values"></a>XAML-Werte

| Benennung | Beschreibung |
|------|-------------|
| XAMLNameValue | Eine Zeichenfolge, die den Einschränkungen der XamlName-Grammatik entspricht. |

##  <a name="xamlname-grammar"></a> XamlName-Grammatik

Im Anschluss finden Sie die maßgebende Grammatik für eine Zeichenfolge, die in dieser XAML-Implementierung als Schlüssel verwendet wird:

``` syntax
XamlName ::= NameStartChar (NameChar)*
NameStartChar ::= LetterCharacter | '_'
NameChar ::= NameStartChar | DecimalDigit
LetterCharacter ::= ('a'-'z') | ('A'-'Z')
DecimalDigit ::= '0'-'9'
CombiningCharacter::= none
```

-   Die Zeichen sind auf den unteren ASCII-Bereich beschränkt – genauer: auf Groß- und Kleinbuchstaben des lateinischen Alphabets sowie auf Ziffern und den Unterstrich (\_).
-   Der Unicode-Zeichenbereich wird nicht unterstützt.
-   Ein Name darf nicht mit einer Ziffer beginnen. Einige Toolimplementierungen stellen einer Zeichenfolge einen Unterstrich (\_) voran, wenn der Benutzer als erstes Zeichen eine Ziffer angibt, oder das Tool generiert automatisch **x:Name**-Werte auf Grundlage anderer Werte, die Ziffern enthalten.

## <a name="remarks"></a>Hinweise

Das angegebene **x:Name**-Attribut wird zum Namen eines Felds, das bei der XAML-Verarbeitung im zugrunde liegenden Code erstellt wird. Dieses Feld enthält einen Verweis auf das Objekt. Die Erstellung dieses Felds erfolgt im Rahmen der MSBuild-Zielschritte. Im Rahmen dieser Schritte erfolgt auch der Beitritt zu den partiellen Klassen für eine XAML-Datei und das zugehörige CodeBehind. Dieses Verhalten ist nicht zwingend XAML-bedingt. Ausschlaggebend ist vielmehr die jeweilige Implementierung, die von der UWP-Programmierung (Universelle Windows-Plattform) für XAML angewendet wird, um **x:Name** in den entsprechenden Programmier- und Anwendungsmodellen zu verwenden.

Jedes definierte **x:Name**-Attribut muss innerhalb eines XAML-Namescopes eindeutig sein. Im Allgemeinen wird ein XAML-Namescope auf der Stammelementebene einer geladenen Seite definiert und enthält alle Elemente unter diesem Element auf einer einzelnen XAML-Seite. Zusätzliche XAML-Namescopes werden von beliebigen, ebenfalls auf dieser Seite definierten Steuerelement- oder Datenvorlagen definiert. Zur Laufzeit wird ein weiterer XAML-Namescope für den Stamm der aus einer angewendeten Steuerelementvorlage erstellten Objektstruktur und auch von Objektstrukturen, die aus einem Aufruf von [**XamlReader.Load**](https://msdn.microsoft.com/library/windows/apps/br228048) erstellt werden, definiert. Weitere Informationen finden Sie unter [XAML-Namescopes](xaml-namescopes.md).

Entwurfstools erzeugen oft automatisch **x:Name**-Werte für Elemente, wenn diese auf der Entwurfsoberfläche eingeführt werden. Welches Schema für die automatische Generierung verwendet wird, hängt zwar davon ab, welchen Designer Sie verwenden, ein häufig verwendetes Schema ist jedoch die Generierung einer Zeichenfolge, die mit dem zugrunde liegenden Klassennamen des Elements beginnt und im Anschluss daran mit einer laufenden ganzen Zahl versehen wird. Wenn Sie also beispielsweise das erste [**Button**](https://msdn.microsoft.com/library/windows/apps/br209265)-Element im Designer einführen, besitzt dieses Element in XAML unter Umständen für das **x:Name**-Attribut den Wert „Button1“.

**x:Name** kann nicht in der XAML-Eigenschaftselementsyntax oder in Code mit [**SetValue**](https://msdn.microsoft.com/library/windows/apps/br242361) festgelegt werden. **x:Name** kann nur über die XAML-Attributsyntax für Elemente festgelegt werden.

**Hinweis:** speziell bei C++ / CX-apps kein Sicherungsfeld für einen Verweis **X: Name** wird für das Stammelement einer XAML-Datei oder-Seite nicht erstellt. Wenn Sie in C++-CodeBehind auf das Stammobjekt verweisen müssen, verwenden Sie andere APIs oder eine Strukturtraversierung. Sie können beispielsweise erst [**FindName**](https://msdn.microsoft.com/library/windows/apps/br208715) für ein bekanntes benanntes Unterelement und anschließend [**Parent**](https://msdn.microsoft.com/library/windows/apps/br208739) aufrufen.

### <a name="xname-and-other-name-properties"></a>x:Name und andere Name-Eigenschaften

Einige in UWP-XAML verwendete Typen verfügen auch über die Eigenschaft **Name**. Beispiele: [**FrameworkElement.Name**](https://msdn.microsoft.com/library/windows/apps/br208735) und [**TextElement.Name**](https://msdn.microsoft.com/library/windows/apps/hh702125).

Falls **Name** als einstellbare Eigenschaft für ein Element verfügbar ist, können **Name** und **x:Name** in XAML synonym verwendet werden. Werden allerdings beide Attribute für das gleiche Element angegeben, tritt ein Fehler auf. In einigen Fällen ist zwar eine **Name**-Eigenschaft vorhanden, diese ist jedoch schreibgeschützt (z.B. [**VisualState.Name**](https://msdn.microsoft.com/library/windows/apps/br209031)). In diesem Fällen verwenden Sie immer **Name** zum Benennen dieses Elements im XAML, und die schreibgeschützte **Name** ist für seltener verwendete Codeszenarien vorhanden.

**Hinweis:** [**FrameworkElement.Name**](https://msdn.microsoft.com/library/windows/apps/br208735) sollte als eine Möglichkeit, ursprünglich durch **X: Name**, festgelegten Werte ändern, es gibt jedoch einige Szenarien, die Ausnahmen von dieser Regel sind in der Regel nicht verwendet werden. In typischen Szenarien handelt es sich bei der Erstellung und Definition von XAML-Namescopes um Vorgänge des XAML-Prozessors. Das Ändern von **FrameworkElement.Name** zur Laufzeit kann einen inkonsistenten XAML-Namescope bzw. eine inkonsistente Benennungsausrichtung privater Felder zur Folge haben, was im CodeBehind nur schwer nachvollziehbar ist.

### <a name="xname-and-xkey"></a>x:Name und x:Key

**x:Name** kann als Attribut auf Elemente innerhalb von [**ResourceDictionary**](https://msdn.microsoft.com/library/windows/apps/br208794) angewendet werden, um als Ersatz für das [x:Key-Attribut](x-key-attribute.md) zu dienen. (Es gilt die Regel, dass alle Elemente in einem **ResourceDictionary** ein x:Key- oder x:Name-Attribut besitzen müssen.) Bei [Storyboardanimationen](https://msdn.microsoft.com/library/windows/apps/mt187354) ist dies häufig der Fall. Weitere Informationen finden Sie im entsprechenden Abschnitt unter [ResourceDictionary- und XAML-Ressourcenverweise](https://msdn.microsoft.com/library/windows/apps/mt187273).

