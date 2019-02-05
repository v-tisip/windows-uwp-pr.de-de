---
Description: Use the Windows.Globalization.DateTimeFormatting API with custom templates and patterns to display dates and times in exactly the format you wish.
title: Verwenden von Mustern zum Formatieren von Datums- und Uhrzeitwerten
ms.assetid: 012028B3-9DA2-4E72-8C0E-3E06BEC3B3FE
label: Use patterns to format dates and times
template: detail.hbs
ms.date: 11/09/2017
ms.topic: article
keywords: Windows 10, UWP, Globalisierung, Lokalisierbarkeit, Lokalisierung
ms.localizationpriority: medium
ms.openlocfilehash: 3849ccf0f129b65dc44f549a37859fe38ac71562
ms.sourcegitcommit: bf600a1fb5f7799961914f638061986d55f6ab12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2019
ms.locfileid: "9048687"
---
# <a name="use-templates-and-patterns-to-format-dates-and-times"></a><span data-ttu-id="3837c-103">Verwenden von Mustern zum Formatieren von Datums- und Uhrzeitwerten</span><span class="sxs-lookup"><span data-stu-id="3837c-103">Use templates and patterns to format dates and times</span></span>

<span data-ttu-id="3837c-104">Verwenden Sie Klassen im Namespace [**Windows.Globalization.DateTimeFormatting**](/uwp/api/windows.globalization.datetimeformatting?branch=live) mit benutzerdefinierten Vorlagen und Mustern, um Daten und Zeiten im gewünschten Format anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="3837c-104">Use classes in the [**Windows.Globalization.DateTimeFormatting**](/uwp/api/windows.globalization.datetimeformatting?branch=live) namespace with custom templates and patterns to display dates and times in exactly the format you wish.</span></span>

## <a name="introduction"></a><span data-ttu-id="3837c-105">Einführung</span><span class="sxs-lookup"><span data-stu-id="3837c-105">Introduction</span></span>

<span data-ttu-id="3837c-106">Die Klasse [**DateTimeFormatter**](/uwp/api/windows.globalization.datetimeformatting?branch=live) bietet vielfältige Möglichkeiten, um Daten und Uhrzeiten für Sprachen und Regionen rund um die Welt ordnungsgemäß zu formatieren.</span><span class="sxs-lookup"><span data-stu-id="3837c-106">The [**DateTimeFormatter**](/uwp/api/windows.globalization.datetimeformatting?branch=live) class provides various ways to properly format dates and times for languages and regions around the world.</span></span> <span data-ttu-id="3837c-107">In den meisten Fällen können Sie Standardformate für Jahr, Monat, Tag usw. verwenden.</span><span class="sxs-lookup"><span data-stu-id="3837c-107">You can use standard formats for year, month, day, and so on.</span></span> <span data-ttu-id="3837c-108">Oder Sie können eine Formatvorlage an das *FormatTemplate*-Argument des **DateTimeFormatter**-Konstruktors übergeben, beispielsweise „longdate” oder „month day”.</span><span class="sxs-lookup"><span data-stu-id="3837c-108">Or you can pass a format template to the *formatTemplate* argument of the **DateTimeFormatter** constructor, such as "longdate" or "month day".</span></span>

<span data-ttu-id="3837c-109">Wenn Sie allerdings noch mehr Kontrolle über Reihenfolge und Format der Komponenten des anzuzeigenden [**DateTime**](/uwp/api/windows.foundation.datetime?branch=live) -Objekts haben möchten, können Sie ein Formatmuster an das *formatTemplate*-Argument des Konstruktors übergeben.</span><span class="sxs-lookup"><span data-stu-id="3837c-109">But when you want even more control over the order and format of the components of the [**DateTime**](/uwp/api/windows.foundation.datetime?branch=live) object you wish to display, you can pass a format pattern to the *formatTemplate* argument of the constructor.</span></span> <span data-ttu-id="3837c-110">Ein Formatmuster verwendet eine spezielle Syntax, mit der Sie einzelne Komponenten eines **DateTime**-Objekts (beispielsweise nur den Monatsnamen oder nur den Jahreswert) abrufen können, um sie in einem bestimmten benutzerdefinierten Format anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="3837c-110">A format pattern uses a special syntax, which allows you to obtain individual components of a **DateTime** object&mdash;just the month name, or just the year value, for example&mdash;in order to display them in whatever custom format you choose.</span></span> <span data-ttu-id="3837c-111">Darüber hinaus kann das Muster mittels Lokalisierung für andere Sprachen und Regionen angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="3837c-111">Furthermore, the pattern can be localized to adapt to other languages and regions.</span></span>

<span data-ttu-id="3837c-112">**Hinweis:** Dies ist nur eine Übersicht über Formatmuster.</span><span class="sxs-lookup"><span data-stu-id="3837c-112">**Note**This is only an overview of format patterns.</span></span> <span data-ttu-id="3837c-113">Eine ausführlichere Besprechung der Formatvorlagen und Formatmuster finden Sie in der Dokumentation zur [**DateTimeFormatter**](/uwp/api/windows.globalization.datetimeformatting?branch=live)-Klasse im Abschnitt „Anmerkungen“.</span><span class="sxs-lookup"><span data-stu-id="3837c-113">For a more complete discussion of format templates and format patterns see the Remarks section of the [**DateTimeFormatter**](/uwp/api/windows.globalization.datetimeformatting?branch=live) class.</span></span>

## <a name="the-difference-between-format-templates-and-format-patterns"></a><span data-ttu-id="3837c-114">Der Unterschied zwischen Formatvorlagen und Formatmustern</span><span class="sxs-lookup"><span data-stu-id="3837c-114">The difference between format templates and format patterns</span></span>

<span data-ttu-id="3837c-115">Eine Formatvorlage ist eine kulturunabhängige Formatzeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="3837c-115">A format template is a culture-agnostic format string.</span></span> <span data-ttu-id="3837c-116">Wenn Sie also einen **DateTimeFormatter** mithilfe einer Formatvorlage erstellen, zeigt der Formatierer Ihre Formatkomponenten in der richtigen Reihenfolge für die aktuelle Sprache an.</span><span class="sxs-lookup"><span data-stu-id="3837c-116">So, if you construct a **DateTimeFormatter** using a format template, then the formatter displays your format components in the right order for the current language.</span></span> <span data-ttu-id="3837c-117">Im Gegensatz dazu ist ein Formatmuster kulturspezifisch.</span><span class="sxs-lookup"><span data-stu-id="3837c-117">Conversely, a format pattern is culture-specific.</span></span> <span data-ttu-id="3837c-118">Wenn Sie einen **DateTimeFormatter** mithilfe eines Formatmusters erstellen, verwendet der Formatierer genau das vorgegebene Muster.</span><span class="sxs-lookup"><span data-stu-id="3837c-118">If you construct a **DateTimeFormatter** using a format pattern, then the formatter will use the pattern exactly as given.</span></span> <span data-ttu-id="3837c-119">Somit ist ein Muster nicht unbedingt für verschiedenen Kulturen anwendbar.</span><span class="sxs-lookup"><span data-stu-id="3837c-119">Consequently, a pattern isn't necesssarily valid across cultures.</span></span>

<span data-ttu-id="3837c-120">Betrachten Sie den Unterschied anhand des folgenden Beispiels.</span><span class="sxs-lookup"><span data-stu-id="3837c-120">Let's illustrate this distinction with an example.</span></span> <span data-ttu-id="3837c-121">Wir übergeben eine einfache Formatvorlage (kein Muster) an den **DateTimeFormatter**-Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="3837c-121">We'll pass a simple format template (not a pattern) to the **DateTimeFormatter** constructor.</span></span> <span data-ttu-id="3837c-122">Dies ist die Formatvorlage „month day”.</span><span class="sxs-lookup"><span data-stu-id="3837c-122">This is the format template "month day".</span></span>

```csharp
var dateFormatter = new Windows.Globalization.DateTimeFormatting.DateTimeFormatter("month day");
```

<span data-ttu-id="3837c-123">Hierdurch wird ein Formatierer erstellt, der auf dem Sprach- und Regionswert des aktuellen Kontexts basiert.</span><span class="sxs-lookup"><span data-stu-id="3837c-123">This creates a formatter based on the language and region value of the current context.</span></span> <span data-ttu-id="3837c-124">Die Reihenfolge der Komponenten in einer Formatvorlage spielt keine Rolle. Der Formatierer zeigt sie in der richtigen Reihenfolge für die aktuelle Sprache.</span><span class="sxs-lookup"><span data-stu-id="3837c-124">The order of the components in a format template doesn't matter; the formatter displays them in the right order for the current language.</span></span> <span data-ttu-id="3837c-125">Er zeigt also „January 1” für Englisch (USA), „1 janvier“ für Französisch (Frankreich) und „1月1日“ für Japanisch an.</span><span class="sxs-lookup"><span data-stu-id="3837c-125">So, it displays "January 1" for English (United States), "1 janvier" for French (France), and "1月1日" for Japanese.</span></span>

<span data-ttu-id="3837c-126">Dagegen ist ein Formatmuster kulturspezifisch.</span><span class="sxs-lookup"><span data-stu-id="3837c-126">On the other hand, a format pattern is culture-specific.</span></span> <span data-ttu-id="3837c-127">Lassen Sie uns auf das Formatmuster für unsere Formatvorlage zugreifen.</span><span class="sxs-lookup"><span data-stu-id="3837c-127">Let's access the format pattern for our format template.</span></span>

```csharp
IReadOnlyList<string> monthDayPatterns = dateFormatter.Patterns;
```

<span data-ttu-id="3837c-128">Wir erhalten unterschiedliche Ergebnisse, je nach Laufzeitsprache und Region.</span><span class="sxs-lookup"><span data-stu-id="3837c-128">This yields different results depending on the runtime language and region.</span></span> <span data-ttu-id="3837c-129">Unterschiedliche Regionen können unterschiedliche Komponenten in unterschiedlicher Reihenfolge und mit oder ohne zusätzliche Zeichen und Leerzeichen verwenden.</span><span class="sxs-lookup"><span data-stu-id="3837c-129">Different regions might use different components, in different orders, with or without additional characters and spacing.</span></span>

```syntax
En-US: "{month.full} {day.integer}"
Fr-FR: "{day.integer} {month.full}"
Ja-JP: "{month.integer}月{day.integer}日"
```

<span data-ttu-id="3837c-130">Im obigen Beispiel haben wir eine kulturunabhängige Formatzeichenfolge eingegeben und eine kulturspezifische Formatzeichenfolge erhalten (die eine Funktion der Sprache und Region war, die beim Aufruf von `dateFormatter.Patterns` gültig waren).</span><span class="sxs-lookup"><span data-stu-id="3837c-130">In the example above, we inputted a culture-agnostic format string, and we got back a culture-specific format string (which was a function of the language and region that happened to be in effect when we called `dateFormatter.Patterns`).</span></span> <span data-ttu-id="3837c-131">Wenn Sie also einen **DateTimeFormatter** aus einem kulturspezifischen Formatmuster erstellen, ist er nur für bestimmte Sprachen/Regionen gültig.</span><span class="sxs-lookup"><span data-stu-id="3837c-131">It follows therefore that if you construct a **DateTimeFormatter** from a culture-specific format pattern, then it will only be valid for specific languages/regions.</span></span>

```csharp
var dateFormatter = new Windows.Globalization.DateTimeFormatting.DateTimeFormatter("{month.full} {day.integer}");
```

<span data-ttu-id="3837c-132">Der obige Formatierer gibt kulturspezifische Werte für die einzelnen Komponenten innerhalb der Klammern {}.</span><span class="sxs-lookup"><span data-stu-id="3837c-132">The formatter above returns culture-specific values for the individual components inside the brackets {}.</span></span> <span data-ttu-id="3837c-133">Aber die Reihenfolge der Komponenten in einem Formatmuster ist unveränderlich.</span><span class="sxs-lookup"><span data-stu-id="3837c-133">But the order of components in a format pattern is invariant.</span></span> <span data-ttu-id="3837c-134">Sie erhalten also stets genau das, was Sie anfordern, und das ist unter Umständen nicht immer für die jeweilige Kultur geeignet.</span><span class="sxs-lookup"><span data-stu-id="3837c-134">You get precisely what you ask for, which may or may not be culturally appropriate.</span></span> <span data-ttu-id="3837c-135">Diese Formatierer gilt für Englisch (USA), aber nicht für Französisch (Frankreich) oder Japanisch.</span><span class="sxs-lookup"><span data-stu-id="3837c-135">This formatter is valid for English (United States), but not for French (France) nor for Japanese.</span></span>

``` syntax
En-US: January 1
Fr-FR: janvier 1 (inappropriate for France; non-standard order)
Ja-JP: 1月1 (inappropriate for Japan; the day symbol 日 is missing)
```

<span data-ttu-id="3837c-136">Zudem kann ein Muster, das heute korrekt ist, in Zukunft falsch sein.</span><span class="sxs-lookup"><span data-stu-id="3837c-136">Furthermore, a pattern that's correct today might not be correct in the future.</span></span> <span data-ttu-id="3837c-137">Länder und Regionen können Änderungen an ihren Kalendersystemen vornehmen, die eine Anpassung einer Formatvorlage erfordern.</span><span class="sxs-lookup"><span data-stu-id="3837c-137">Countries or regions might change their calendar systems, which alters a format template.</span></span> <span data-ttu-id="3837c-138">Windows aktualisiert die Ausgabe von Formatierern basierend auf Formatvorlagen, um solchen Änderungen Rechnung zu tragen</span><span class="sxs-lookup"><span data-stu-id="3837c-138">Windows updates the output of formatters based on format templates to accommodate such changes.</span></span> <span data-ttu-id="3837c-139">Daher sollten Sie die Mustersyntax nur unter einer oder mehreren dieser Bedingungen verwenden:</span><span class="sxs-lookup"><span data-stu-id="3837c-139">Therefore, you should only use the pattern syntax under one or more of these conditions.</span></span>

-   <span data-ttu-id="3837c-140">Sie benötigen keine bestimmte Ausgabe für ein Format.</span><span class="sxs-lookup"><span data-stu-id="3837c-140">You are not dependent on a particular output for a format.</span></span>
-   <span data-ttu-id="3837c-141">Das Format muss keinen bestimmten kulturspezifischen Standard erfüllen.</span><span class="sxs-lookup"><span data-stu-id="3837c-141">You do not need the format to follow some culture-specific standard.</span></span>
-   <span data-ttu-id="3837c-142">Das Muster soll bewusst für alle Kulturen unveränderlich sein.</span><span class="sxs-lookup"><span data-stu-id="3837c-142">You specifically intend the pattern to be invariant across cultures.</span></span>
-   <span data-ttu-id="3837c-143">Sie beabsichtigen, die Musterformat-Zeichenfolge selbst zu lokalisieren.</span><span class="sxs-lookup"><span data-stu-id="3837c-143">You intend to localize the actual format pattern string itself.</span></span>

<span data-ttu-id="3837c-144">Hier eine Zusammenfassung der Unterschiede zwischen Formatvorlagen und Formatmustern:</span><span class="sxs-lookup"><span data-stu-id="3837c-144">Here's a summary of the distinction between format templates and format patterns.</span></span>

**<span data-ttu-id="3837c-145">Formatvorlagen wie „month day“</span><span class="sxs-lookup"><span data-stu-id="3837c-145">Format templates, such as "month day"</span></span>**

-   <span data-ttu-id="3837c-146">Eine abstrahierte Darstellung des [DateTime](/uwp/api/windows.foundation.datetime?branch=live)-Formats, die Werte für Tag , Monat usw. in einer bestimmten Reihenfolge enthält.</span><span class="sxs-lookup"><span data-stu-id="3837c-146">Abstracted representation of a [DateTime](/uwp/api/windows.foundation.datetime?branch=live) format that includes values for the month, day, etc., in any order.</span></span>
-   <span data-ttu-id="3837c-147">Gibt für alle von Windows unterstützten Sprach- und Regionswerte stets ein gültiges Standardformat zurück.</span><span class="sxs-lookup"><span data-stu-id="3837c-147">Guaranteed to return a valid standard format across all language-region values supported by Windows.</span></span>
-   <span data-ttu-id="3837c-148">Liefert stets eine entsprechend der Kultur formatierte Zeichenfolge für die angegebene Sprache und Region.</span><span class="sxs-lookup"><span data-stu-id="3837c-148">Guaranteed to give you a culturally-appropriate formatted string for the given language-region.</span></span>
-   <span data-ttu-id="3837c-149">Nicht alle Kombinationen der Komponenten sind gültig.</span><span class="sxs-lookup"><span data-stu-id="3837c-149">Not all combinations of components are valid.</span></span> <span data-ttu-id="3837c-150">Beispielsweise ist „dayofweek day ” ungültig.</span><span class="sxs-lookup"><span data-stu-id="3837c-150">For example, "dayofweek day" is not valid.</span></span>

**<span data-ttu-id="3837c-151">Formmuster wie „{month.full} {day.integer}“</span><span class="sxs-lookup"><span data-stu-id="3837c-151">Format patterns, such as "{month.full} {day.integer}"</span></span>**

-   <span data-ttu-id="3837c-152">Eine Zeichenfolge mit explizit festgelegter Reihenfolge, die den vollständigen Monatsnamen, gefolgt von einem Leerzeichen, gefolgt von einer ganze Zahl (für den Tag) angibt, und zwar in dieser Reihenfolge oder gemäß dem angegebenen spezifischen Formatmuster.</span><span class="sxs-lookup"><span data-stu-id="3837c-152">Explicitly ordered string that expresses the full month name, followed by a space, followed by the day integer, in that order, or whatever specific format pattern you specify.</span></span>
-   <span data-ttu-id="3837c-153">Entspricht möglicherweise nicht dem gültigen Standardformat für jedes Sprache-Region-Paar.</span><span class="sxs-lookup"><span data-stu-id="3837c-153">May not correspond to a valid standard format for any language-region pair.</span></span>
-   <span data-ttu-id="3837c-154">Ist nicht unbedingt der Kultur angemessen.</span><span class="sxs-lookup"><span data-stu-id="3837c-154">Not guaranteed to be culturally appropriate.</span></span>
-   <span data-ttu-id="3837c-155">Es kann eine beliebige Kombination von Komponenten in einer beliebigen Reihenfolge angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="3837c-155">Any combination of components may be specified, in any order.</span></span>

## <a name="examples"></a><span data-ttu-id="3837c-156">Beispiele</span><span class="sxs-lookup"><span data-stu-id="3837c-156">Examples</span></span>

<span data-ttu-id="3837c-157">Angenommen, Sie möchten den aktuellen Monat und den aktuellen Tag zusammen mit der aktuellen Uhrzeit in einen bestimmten Format anzeigen.</span><span class="sxs-lookup"><span data-stu-id="3837c-157">Suppose you wish to display the current month and day together with the current time, in a specific format.</span></span> <span data-ttu-id="3837c-158">Sie möchten also z.B., dass für US-Benutzer Folgendes angezeigt wird:</span><span class="sxs-lookup"><span data-stu-id="3837c-158">For example, you would like US English users to see something like this:</span></span>

``` syntax
June 25 | 1:38 PM
```

<span data-ttu-id="3837c-159">Die Datumskomponente entspricht der Formatvorlage „month day“, die Uhrzeitkomponente der Formatvorlage „hour minute“.</span><span class="sxs-lookup"><span data-stu-id="3837c-159">The date part corresponds to the "month day" format template, and the time part corresponds to the "hour minute" format template.</span></span> <span data-ttu-id="3837c-160">Sie können also einen Formatierer der relevanten Datum und Uhrzeit Formatvorlagen erstellen und dann ihre Ausgabe zusammen mit einer lokalisierbaren Formatzeichenfolge verketten.</span><span class="sxs-lookup"><span data-stu-id="3837c-160">So, you can construct formatters for the relevant date and time format templates, and then concatenate their output together using a localizable format string.</span></span>

```csharp
var dateToFormat = System.DateTime.Now;
var resourceLoader = Windows.ApplicationModel.Resources.ResourceLoader.GetForCurrentView();

var dateFormatter = new Windows.Globalization.DateTimeFormatting.DateTimeFormatter("month day");
var timeFormatter = new Windows.Globalization.DateTimeFormatting.DateTimeFormatter("hour minute");

var date = dateFormatter.Format(dateToFormat);
var time = timeFormatter.Format(dateToFormat);

string output = string.Format(resourceLoader.GetString("CustomDateTimeFormatString"), date, time);
```

`CustomDateTimeFormatString` <span data-ttu-id="3837c-161">ist ein Ressourcenbezeichner, der auf eine lokalisierbare Ressource in einer Ressourcendatei (.resw) verweist.</span><span class="sxs-lookup"><span data-stu-id="3837c-161">is a resource identifier referring to a localizable resource in a Resources File (.resw).</span></span> <span data-ttu-id="3837c-162">Für die Standardsprache Englisch (USA), dieser würde festgelegt werden, auf einen Wert von "{0} | {1}"zusammen mit einem Kommentar, der angibt, dass"{0}"ist das Datum und"{1}"ist die Zeit.</span><span class="sxs-lookup"><span data-stu-id="3837c-162">For a default language of English (United States), this would be set to a value of "{0} | {1}" along with a comment indicating that "{0}" is the date and "{1}" is the time.</span></span> <span data-ttu-id="3837c-163">Somit können Übersetzer die Formatelemente wie gewünscht anpassen.</span><span class="sxs-lookup"><span data-stu-id="3837c-163">That way, translators can adjust the format items as needed.</span></span> <span data-ttu-id="3837c-164">Sie können beispielsweise die Reihenfolge der Komponenten ändern, falls in bestimmten Sprachen oder Regionen die Uhrzeit vor dem Datum stehen soll.</span><span class="sxs-lookup"><span data-stu-id="3837c-164">For example, they can change the order of the items if it seems more natural in some language or region to have the time precede the date.</span></span> <span data-ttu-id="3837c-165">Oder Sie können „|“ durch ein anderes Trennzeichen ersetzen.</span><span class="sxs-lookup"><span data-stu-id="3837c-165">Or, they can replace "|" with some other separator character.</span></span>

<span data-ttu-id="3837c-166">Eine andere Möglichkeit zum Implementieren dieses Beispiels besteht darin, die beiden Formatierer nach ihren Formatmustern abzufragen, diese miteinander zu verketten und dann aus dem resultierenden Formatmuster einen dritten Formatierer zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="3837c-166">Another way to implement this example is to query the two formatters for their format patterns, concatenate those together, and then construct a third formatter from the resultant format pattern.</span></span>

```csharp
var resourceLoader = Windows.ApplicationModel.Resources.ResourceLoader.GetForCurrentView();

var dateFormatter = new Windows.Globalization.DateTimeFormatting.DateTimeFormatter("month day");
var timeFormatter = new Windows.Globalization.DateTimeFormatting.DateTimeFormatter("hour minute");

string dateFormatterPattern = dateFormatter.Patterns[0];
string timeFormatterPattern = timeFormatter.Patterns[0];

string pattern = string.Format(resourceLoader.GetString("CustomDateTimeFormatString"), dateFormatterPattern, timeFormatterPattern);

var patternFormatter = new Windows.Globalization.DateTimeFormatting.DateTimeFormatter(pattern);

string output = patternFormatter.Format(System.DateTime.Now);
```

## <a name="important-apis"></a><span data-ttu-id="3837c-167">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="3837c-167">Important APIs</span></span>

* [<span data-ttu-id="3837c-168">Windows.Globalization.DateTimeFormatting</span><span class="sxs-lookup"><span data-stu-id="3837c-168">Windows.Globalization.DateTimeFormatting</span></span>](/uwp/api/windows.globalization.datetimeformatting?branch=live)
* [<span data-ttu-id="3837c-169">DateTimeFormatter</span><span class="sxs-lookup"><span data-stu-id="3837c-169">DateTimeFormatter</span></span>](/uwp/api/windows.globalization.datetimeformatting?branch=live)
* [<span data-ttu-id="3837c-170">DateTime</span><span class="sxs-lookup"><span data-stu-id="3837c-170">DateTime</span></span>](/uwp/api/windows.foundation.datetime?branch=live)

## <a name="related-topics"></a><span data-ttu-id="3837c-171">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="3837c-171">Related topics</span></span>

* [<span data-ttu-id="3837c-172">Beispiel für Datums- und Uhrzeitformatierung</span><span class="sxs-lookup"><span data-stu-id="3837c-172">Date and time formatting sample</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=231618)
