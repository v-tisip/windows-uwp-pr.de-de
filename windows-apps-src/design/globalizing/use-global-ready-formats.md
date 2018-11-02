---
author: stevewhims
Description: Design your app to be global-ready by appropriately formatting dates, times, numbers, phone numbers, and currencies. You'll then be able later to adapt your app for additional cultures, regions, and languages in the global market.
title: Globalisieren von Datum, Uhrzeit und Zahlenformaten
ms.assetid: 6ECE8BA4-9A7D-49A6-81EE-AB2BE7F0254F
template: detail.hbs
ms.author: stwhi
ms.date: 11/07/2017
ms.topic: article
keywords: Windows 10, UWP, Globalisierung, Lokalisierbarkeit, Lokalisierung
ms.localizationpriority: medium
ms.openlocfilehash: 173198c2c61530704dad02e2e92e6a7e47aae420
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5977527"
---
# <a name="globalize-your-datetimenumber-formats"></a><span data-ttu-id="78f39-103">Globalisieren von Datum, Uhrzeit und Zahlenformaten</span><span class="sxs-lookup"><span data-stu-id="78f39-103">Globalize your date/time/number formats</span></span>

<span data-ttu-id="78f39-104">Gestalten Sie Ihre App so, dass sie global einsetzbar ist, indem Sie Datum, Uhrzeit, Telefonnummern und Währungen entsprechend formatieren.</span><span class="sxs-lookup"><span data-stu-id="78f39-104">Design your app to be global-ready by appropriately formatting dates, times, numbers, phone numbers, and currencies.</span></span> <span data-ttu-id="78f39-105">Dadurch können Sie Ihre App später zur weltweiten Vermarktung für weitere Kulturkreise, Regionen und Sprachen anpassen.</span><span class="sxs-lookup"><span data-stu-id="78f39-105">You'll then be able later to adapt your app for additional cultures, regions, and languages in the global market.</span></span>

## <a name="introduction"></a><span data-ttu-id="78f39-106">Einführung</span><span class="sxs-lookup"><span data-stu-id="78f39-106">Introduction</span></span>

<span data-ttu-id="78f39-107">Wenn Sie bei der Erstellung Ihrer App nicht nur Ihre Sprache und Kultur berücksichtigen, werden nur wenige (oder keine) Probleme auftreten, sobald Sie für Ihre App neue Märkte erschließen.</span><span class="sxs-lookup"><span data-stu-id="78f39-107">When creating your app, if you think more broadly than a single language and culture then you'll have fewer (if any) unexpected issues when your app grows into new markets.</span></span> <span data-ttu-id="78f39-108">Datumsangaben, Uhrzeiten, Zahlen, Kalender, Währungen, Telefonnummern, Maßeinheiten und Papierformate sind Beispiele für Elemente, die in den verschiedenen Kulturen oder Sprachen anders angezeigt werden können.</span><span class="sxs-lookup"><span data-stu-id="78f39-108">For example, dates, times, numbers, calendars, currency, telephone numbers, units of measurement, and paper sizes are all items that can be displayed differently in different cultures or languages.</span></span>

<span data-ttu-id="78f39-109">Verschiedene Regionen und Kulturen verwenden unterschiedliche Formate für Datum und Uhrzeit.</span><span class="sxs-lookup"><span data-stu-id="78f39-109">Different regions and cultures use different date and time formats.</span></span> <span data-ttu-id="78f39-110">Dazu gehören unterschiedliche Konventionen für die Reihenfolge von Tag und Monat im Datum, für die Trennung von Stunden und Minuten und sogar für das zu verwendende Trennzeichen.</span><span class="sxs-lookup"><span data-stu-id="78f39-110">These include conventions for the order of day and month in the date, for the separation of hours and minutes in the time, and even for what punctuation is used as a separator.</span></span> <span data-ttu-id="78f39-111">Zudem kann das Datum in verschiedenen langen Formaten (Mittwoch, 28.März2012) oder kurzen Formaten (28.03.12) angezeigt werden, die je nach Kultur variieren können.</span><span class="sxs-lookup"><span data-stu-id="78f39-111">In addition, dates may be displayed in various long formats ("Wednesday, March 28, 2012") or short formats ("3/28/12"), which vary across cultures.</span></span> <span data-ttu-id="78f39-112">Und natürlich sind die Namen und Kurzformen für die Wochentage und Monate in jeder Sprache unterschiedlich.</span><span class="sxs-lookup"><span data-stu-id="78f39-112">And, of course, the names and abbreviations for the days of the week and months of the year differ between languages.</span></span>

<span data-ttu-id="78f39-113">Sie können eine Vorschau der für verschiedene Sprachen verwendeten Formate anzeigen.</span><span class="sxs-lookup"><span data-stu-id="78f39-113">You can preview the formats used for different languages.</span></span> <span data-ttu-id="78f39-114">Wählen Sie **Einstellungen** > **Zeit und Sprache** > **Region und Sprache**, und klicken Sie auf **Zusätzliche Datums-, Uhrzeit- und Ländereinstellungen** > **Datums-, Uhrzeit- oder Zahlenformat ändern**.</span><span class="sxs-lookup"><span data-stu-id="78f39-114">Go to **Settings** > **Time & Language** > **Region & language**, and click **Additional date, time, & regional settings** > **Change date, time, or number formats**.</span></span> <span data-ttu-id="78f39-115">Auf der Registerkarte **Formate** wählen Sie eine Sprache aus der Dropdownliste **Format** und erhalten eine Vorschau der Formate in **Beispiele**.</span><span class="sxs-lookup"><span data-stu-id="78f39-115">On the **Formats** tab, select a language from the **Format** drop-down and preview the formats in **Examples**.</span></span>

<span data-ttu-id="78f39-116">In diesem Thema werden die Begriffe „Benutzerprofil-Sprachenliste”, „App-Manifest-Sprachenliste” und „App-Laufzeit-Sprachenliste” verwendet.</span><span class="sxs-lookup"><span data-stu-id="78f39-116">This topic uses the terms "user profile language list", "app manifest language list", and "app runtime language list".</span></span> <span data-ttu-id="78f39-117">Einzelheiten dazu, was genau diese Begriffe bedeuten und wie sie auf ihre Werte zugreifen können, finden Sie unter [Benutzerprofilsprachen und App-Manifest-Sprachen verstehen](manage-language-and-region.md).</span><span class="sxs-lookup"><span data-stu-id="78f39-117">For details on exactly what those terms mean and how to access their values, see [Understand user profile languages and app manifest languages](manage-language-and-region.md).</span></span>

## <a name="format-dates-and-times-for-the-app-runtime-language-list"></a><span data-ttu-id="78f39-118">Formatieren von Datumsangaben und Uhrzeiten für die App-Laufzeit-Sprachenliste</span><span class="sxs-lookup"><span data-stu-id="78f39-118">Format dates and times for the app runtime language list</span></span>

<span data-ttu-id="78f39-119">Wenn Sie Benutzern erlauben möchten, ein Datum oder eine Uhrzeit auszuwählen, sollten Sie die Standardsteuerelemente für [Kalender, Datum und Uhrzeit](../controls-and-patterns/date-and-time.md) verwenden.</span><span class="sxs-lookup"><span data-stu-id="78f39-119">If you need to allow users to choose a date, or to select a time, then use the standard [calendar, date, and time controls](../controls-and-patterns/date-and-time.md).</span></span> <span data-ttu-id="78f39-120">Diese verwenden automatisch das beste Datums- und Zeitformat für die App-Laufzeit-Sprachenliste.</span><span class="sxs-lookup"><span data-stu-id="78f39-120">These automatically use the best date and time format for the app runtime language list.</span></span>

<span data-ttu-id="78f39-121">Zur Anzeige von Datumsangaben oder Uhrzeiten können Sie die Klasse [**DateTimeFormatter**](/uwp/api/windows.globalization.datetimeformatting?branch=live) verwenden.</span><span class="sxs-lookup"><span data-stu-id="78f39-121">If you need to display dates or times yourself then you can use the [**DateTimeFormatter**](/uwp/api/windows.globalization.datetimeformatting?branch=live) class.</span></span> <span data-ttu-id="78f39-122">Standardmäßig verwendet **DateTimeFormatter** automatisch das beste Datums- und Zeitformat für die App-Laufzeit-Sprachenliste.</span><span class="sxs-lookup"><span data-stu-id="78f39-122">By default, **DateTimeFormatter** automatically uses the best date and time format for the app runtime language list.</span></span> <span data-ttu-id="78f39-123">Der folgende Code formatiert also einen gegebenen **DateTime**-Wert optimal für diese Liste.</span><span class="sxs-lookup"><span data-stu-id="78f39-123">So, the code below formats a given **DateTime** in the best way for that list.</span></span> <span data-ttu-id="78f39-124">Nehmen wir zum Beispiel an, dass die App-Manifest-Sprachenliste Englisch (USA) als Standardsprache und zudem Deutsch (Deutschland) enthält.</span><span class="sxs-lookup"><span data-stu-id="78f39-124">As an example, assume that your app manifest language list includes English (United States), which is also your default, and German (Germany).</span></span> <span data-ttu-id="78f39-125">Wenn das aktuelle Datum „Nov 6 2017” ist und die Benutzerprofil-Sprachenliste Deutsch (Deutschland) als erste Sprache enthält, gibt der Formatierer „06.11.2017” zurück..</span><span class="sxs-lookup"><span data-stu-id="78f39-125">If the current date is Nov 6 2017 and the user profile language list contains German (Germany) first, then the formatter gives "06.11.2017".</span></span> <span data-ttu-id="78f39-126">Wenn die Benutzerprofil-Sprachenliste zuerst Englisch (USA) enthält (oder wenn sie weder Englisch noch Deutsch enthält), gibt der Formatierer „11/6/2017” zurück (da „en-US” übereinstimmt oder als Standard verwendet wird) ).</span><span class="sxs-lookup"><span data-stu-id="78f39-126">If the user profile language list contains English (United States) first (or if it contains neither English nor German), then the formatter gives "11/6/2017" (since "en-US" matches, or is used as the default).</span></span>

```csharp
    // Use the DateTimeFormatter class to display dates and times using basic formatters.

    var shortDateFormatter = new Windows.Globalization.DateTimeFormatting.DateTimeFormatter("shortdate");
    var shortTimeFormatter = new Windows.Globalization.DateTimeFormatting.DateTimeFormatter("shorttime");

    var dateTimeToFormat = DateTime.Now;

    var shortDate = shortDateFormatter.Format(dateTimeToFormat);
    var shortTime = shortTimeFormatter.Format(dateTimeToFormat);

    var results = "Short Date: " + shortDate + "\n" +
                  "Short Time: " + shortTime;
```

<span data-ttu-id="78f39-127">Sie können den Code oben auf Ihrem eigenen PC wie folgt testen.</span><span class="sxs-lookup"><span data-stu-id="78f39-127">You can test the code above on your own PC like this.</span></span>

- <span data-ttu-id="78f39-128">Stellen Sie sicher, dass die Ressourcendateien in Ihrem Projekt sowohl für „en-US”" als auch für „de-DE” qualifiziert sind (siehe [Anpassen von Ressourcen mit Qualifizierern für Sprache, Skalierung, hohen Kontrast und andere Eigenschaften](../../app-resources/tailor-resources-lang-scale-contrast.md)).</span><span class="sxs-lookup"><span data-stu-id="78f39-128">Make sure that you have resource files in your project qualified for both "en-US" and "de-DE" (see [Tailor your resources for language, scale, high contrast, and other qualifiers](../../app-resources/tailor-resources-lang-scale-contrast.md)).</span></span>
- <span data-ttu-id="78f39-129">Ändern Sie die Benutzerprofil-Sprachenliste unter **Einstellungen** > **Zeit und Sprache** > **Region und Sprache** > **Sprachen**.</span><span class="sxs-lookup"><span data-stu-id="78f39-129">Change your user profile language list in **Settings** > **Time & Language** > **Region & language** > **Languages**.</span></span> <span data-ttu-id="78f39-130">Fügen Sie Deutsch (Deutschland) als Standardsprache hinzu, und führen Sie den Code erneut aus.</span><span class="sxs-lookup"><span data-stu-id="78f39-130">Add German (Germany), make it the default, and run the code again.</span></span>

## <a name="format-dates-and-times-for-the-user-profile-language-list"></a><span data-ttu-id="78f39-131">Formatieren von Datumsangaben und Uhrzeiten für die Benutzerprofil-Sprachenliste</span><span class="sxs-lookup"><span data-stu-id="78f39-131">Format dates and times for the user profile language list</span></span>

<span data-ttu-id="78f39-132">Denken Sie daran, dass **DateTimeFormatter** standardmäßig die App-Runtime-Sprachenliste übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="78f39-132">Remember that, by default, **DateTimeFormatter** matches the app runtime language list.</span></span> <span data-ttu-id="78f39-133">Daher wird bei der Anzeige einer Zeichenfolge wie „Das Datum ist der &lt;date&gt;” die Sprache dem Datumsformat entsprechen.</span><span class="sxs-lookup"><span data-stu-id="78f39-133">That way, if you display strings such as "The date is &lt;date&gt;", then the language will match the date format.</span></span>

<span data-ttu-id="78f39-134">Wenn Sie Daten und/oder Uhrzeiten aus irgendeinem Grund nur gemäß der Benutzerprofil-Sprachenliste formatieren möchten, können Sie dies mithilfe von Code wie im folgenden Beispiel tun.</span><span class="sxs-lookup"><span data-stu-id="78f39-134">If for whatever reason you want to format dates and/or times only according to the user profile language list, then you can do that using code like the example below.</span></span> <span data-ttu-id="78f39-135">Aber in diesem Fall können Sie nicht ausschließen, dass der Benutzer eine Sprache wählt, für die Ihre App keine Zeichenfolgen übersetzt hat.</span><span class="sxs-lookup"><span data-stu-id="78f39-135">But if you do so then understand that the user can choose a language for which your app doesn't have translated strings.</span></span> <span data-ttu-id="78f39-136">Wenn Ihre App beispielsweise nicht in Deutsch (Deutschland) lokalisiert ist, aber der Benutzer diese Sprache als bevorzugte Sprache auswählt, kann dies zur Anzeige einer Zeichenfolgen wie „Das Datum ist der 06.11.2017” führen.</span><span class="sxs-lookup"><span data-stu-id="78f39-136">For example, if your app is not localized into German (Germany), but the user chooses that as their preferred language, then that could result in the display of arguably odd-looking strings such as "The date is 06.11.2017".</span></span>

```csharp
    // Use the DateTimeFormatter class to display dates and times using basic formatters.

    var userLanguages = Windows.System.UserProfile.GlobalizationPreferences.Languages;

    var shortDateFormatter = new Windows.Globalization.DateTimeFormatting.DateTimeFormatter("shortdate", userLanguages);

    var results = "Short Date: " + shortDateFormatter.Format(DateTime.Now);
```

## <a name="format-numbers-and-currencies-appropriately"></a><span data-ttu-id="78f39-137">Formatieren Sie Zahlen und Währungen entsprechend</span><span class="sxs-lookup"><span data-stu-id="78f39-137">Format numbers and currencies appropriately</span></span>

<span data-ttu-id="78f39-138">In verschiedenen Kulturen werden Zahlen unterschiedlich formatiert.</span><span class="sxs-lookup"><span data-stu-id="78f39-138">Different cultures format numbers differently.</span></span> <span data-ttu-id="78f39-139">Formatunterschiede können sich auf Folgendes beziehen: wie viele Dezimalziffern angezeigt werden, welche Zeichen als Dezimaltrennzeichen verwendet werden und welches Währungssymbol verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="78f39-139">Format differences may include how many decimal digits to display, what characters to use as decimal separators, and what currency symbol to use.</span></span> <span data-ttu-id="78f39-140">Verwenden Sie Klassen aus dem Namespace [**NumberFormatting**](/uwp/api/windows.globalization.numberformatting?branch=live), um Dezimal-, Prozent- oder Promillezahlen und Währungen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="78f39-140">Use classes in the [**NumberFormatting**](/uwp/api/windows.globalization.numberformatting?branch=live) namespace to display decimal, percent, or permille numbers, and currencies.</span></span> <span data-ttu-id="78f39-141">In den meisten Fällen wird es Ihre Absicht sein, dass diese Formatierungsklassen das beste Format für das Benutzerprofil verwenden.</span><span class="sxs-lookup"><span data-stu-id="78f39-141">Most of the time, you will want these formatter classes to use the best format for the user profile.</span></span> <span data-ttu-id="78f39-142">Sie können die Formatierer aber auch verwenden, um eine Währung für eine beliebige Region oder ein beliebiges Format anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="78f39-142">But you may use the formatters to display a currency for any region or format.</span></span>

<span data-ttu-id="78f39-143">Dieses Beispiel zeigt, wie Währungen sowohl für das Benutzerprofil als auch für ein bestimmtes Währungssystem angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="78f39-143">This example shows how to display currencies both per the user profile, and for a specific given currency system.</span></span>

```csharp
    // This scenario uses the CurrencyFormatter class to format a number as a currency.

    var userCurrency = Windows.System.UserProfile.GlobalizationPreferences.Currencies[0];

    var valueToBeFormatted = 12345.67;

    var userCurrencyFormatter = new Windows.Globalization.NumberFormatting.CurrencyFormatter(userCurrency);
    var userCurrencyValue = userCurrencyFormatter.Format(valueToBeFormatted);

    // Create a formatter initialized to a specific currency,
    // in this case US Dollar (specified as an ISO 4217 code) 
    // but with the default number formatting for the current user.
    var currencyFormatUSD = new Windows.Globalization.NumberFormatting.CurrencyFormatter("USD");
    var currencyValueUSD = currencyFormatUSD.Format(valueToBeFormatted);

    // Create a formatter initialized to a specific currency.
    // In this case it's the Euro with the default number formatting for France.
    var currencyFormatEuroFR = new Windows.Globalization.NumberFormatting.CurrencyFormatter("EUR", new[] { "fr-FR" }, "FR");
    var currencyValueEuroFR = currencyFormatEuroFR.Format(valueToBeFormatted);

    // Results for display.
    var results = "Fixed number (" + valueToBeFormatted + ")\n" +
                    "With user's default currency: " + userCurrencyValue + "\n" +
                    "Formatted US Dollar: " + currencyValueUSD + "\n" +
                    "Formatted Euro (fr-FR defaults): " + currencyValueEuroFR;
```

<span data-ttu-id="78f39-144">Sie können den nachstehenden Code auf Ihrem PC testen. Ändern Sie dazu Land oder Region unter **Einstellungen** > **Zeit und Sprache** > **Region und Sprache** > **Land oder Region**.</span><span class="sxs-lookup"><span data-stu-id="78f39-144">You can test the code above on your own PC by changing the country or region in **Settings** > **Time & Language** > **Region & language** > **Country or region**.</span></span> <span data-ttu-id="78f39-145">Wählen Sie ein Land oder eine Region (z.B. Island), und führen Sie den Code erneut aus.</span><span class="sxs-lookup"><span data-stu-id="78f39-145">Choose a country or region (perhaps Iceland), and run the code again.</span></span>

## <a name="use-a-culturally-appropriate-calendar"></a><span data-ttu-id="78f39-146">Verwenden Sie einen kulturspezifischen Kalender</span><span class="sxs-lookup"><span data-stu-id="78f39-146">Use a culturally appropriate calendar</span></span>

<span data-ttu-id="78f39-147">Der Kalender ist für verschiedene Regionen und Sprachen unterschiedlich.</span><span class="sxs-lookup"><span data-stu-id="78f39-147">The calendar differs across regions and languages.</span></span> <span data-ttu-id="78f39-148">Der gregorianische Kalender ist nicht der Standardkalender für alle Regionen.</span><span class="sxs-lookup"><span data-stu-id="78f39-148">The Gregorian calendar is not the default for every region.</span></span> <span data-ttu-id="78f39-149">In einigen Regionen wählen Benutzer möglicherweise alternative Kalender aus, z.B. den japanischen Era-Kalender oder den arabischen Mondkalender.</span><span class="sxs-lookup"><span data-stu-id="78f39-149">Users in some regions may choose alternate calendars, such as the Japanese era calendar, or Arabic lunar calendars.</span></span> <span data-ttu-id="78f39-150">In Datumsangaben und Uhrzeiten im Kalender werden auch verschiedene Zeitzonen und Sommerzeiten berücksichtigt.</span><span class="sxs-lookup"><span data-stu-id="78f39-150">Dates and times on the calendar are also sensitive to different time zones and daylight-saving time.</span></span>

<span data-ttu-id="78f39-151">Um sicherzustellen, dass das bevorzugte Kalenderformat verwendet wird, können Sie die standardmäßigen [Steuerelemente für Kalender, Datum und Uhrzeit](../controls-and-patterns/date-and-time.md) verwenden.</span><span class="sxs-lookup"><span data-stu-id="78f39-151">To ensure that the preferred calendar format is used, you can use the standard [calendar, date, and time controls](../controls-and-patterns/date-and-time.md).</span></span> <span data-ttu-id="78f39-152">Für komplexere Szenarien, in denen direkt mit Vorgängen in Bezug auf das Kalenderdatum gearbeitet werden muss, stellt **Windows.Globalization** eine [**Calendar**](/uwp/api/windows.globalization.calendar?branch=live)-Klasse bereit, die eine passende Kalenderdarstellung für die jeweilige Kultur, Region und den Kalendertyp ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="78f39-152">For more complex scenarios, where working directly with operations on calendar dates may be required, **Windows.Globalization** provides a [**Calendar**](/uwp/api/windows.globalization.calendar?branch=live) class that gives an appropriate calendar representation for the given culture, region, and calendar type.</span></span>

## <a name="format-phone-numbers-appropriately"></a><span data-ttu-id="78f39-153">Formatieren Sie Telefonnummern entsprechend</span><span class="sxs-lookup"><span data-stu-id="78f39-153">Format phone numbers appropriately</span></span>

<span data-ttu-id="78f39-154">Telefonnummern werden in verschiedenen Regionen unterschiedlich formatiert.</span><span class="sxs-lookup"><span data-stu-id="78f39-154">Phone numbers are formatted differently across regions.</span></span> <span data-ttu-id="78f39-155">Die Anzahl der Stellen, die Gruppierung der Ziffern und die Bedeutung bestimmter Teile der Telefonnummer variieren zwischen verschiedenen Ländern.</span><span class="sxs-lookup"><span data-stu-id="78f39-155">The number of digits, how the digits are grouped, and the significance of certain parts of the phone number vary between countries.</span></span> <span data-ttu-id="78f39-156">Ab Windows 10, Version 1607, können Sie Klassen aus dem Namespace [**PhoneNumberFormatting**](/uwp/api/windows.globalization.phonenumberformatting?branch=live) verwenden, um Telefonnummern gemäß der aktuellen Region zu formatieren.</span><span class="sxs-lookup"><span data-stu-id="78f39-156">Starting in Windows 10, version 1607, you can use classes in the [**PhoneNumberFormatting**](/uwp/api/windows.globalization.phonenumberformatting?branch=live) namespace to format phone numbers appropriately for the current region.</span></span>

<span data-ttu-id="78f39-157">[**PhoneNumberInfo**](/uwp/api/windows.globalization.phonenumberformatting.phonenumberinfo?branch=live) analysiert eine Ziffernfolge und bestimmt, ob die Ziffern eine gültige Telefonnummer für diese Region bilden, vergleicht zwei Nummern auf Gleichheit und extrahiert die verschiedenen Funktionsteile einer Telefonnummer, z.B. den Ländercode oder den Code für die geographische Region.</span><span class="sxs-lookup"><span data-stu-id="78f39-157">[**PhoneNumberInfo**](/uwp/api/windows.globalization.phonenumberformatting.phonenumberinfo?branch=live) parses a string of digits and allows you to: determine whether the digits are a valid phone number in the current region; compare two numbers for equality; and to extract the different functional parts of the phone number, such as country code or geographical area code.</span></span>

<span data-ttu-id="78f39-158">[**PhoneNumberFormatter**](/uwp/api/windows.globalization.phonenumberformatting.phonenumberformatter?branch=live) formatiert eine Ziffernfolge oder ein **PhoneNumberInfo** für die Anzeige, auch wenn die Ziffernfolge nur den Teil einer Telefonnummer darstellt.</span><span class="sxs-lookup"><span data-stu-id="78f39-158">[**PhoneNumberFormatter**](/uwp/api/windows.globalization.phonenumberformatting.phonenumberformatter?branch=live) formats a string of digits or a **PhoneNumberInfo** for display, even when the string of digits represents a partial phone number.</span></span> <span data-ttu-id="78f39-159">Sie können diese partielle Nummernformatierung verwenden, um eine Zahl zu formatieren, die gerade von einem Benutzer eingegeben wird.</span><span class="sxs-lookup"><span data-stu-id="78f39-159">You can use this partial number formatting to format a number as a user is entering the number.</span></span>

<span data-ttu-id="78f39-160">Das folgende Beispiel veranschaulicht die Verwendung von **PhoneNumberFormatter** zum Formatieren einer Telefonnummer, die gerade eingegeben wird.</span><span class="sxs-lookup"><span data-stu-id="78f39-160">The example below shows how to use **PhoneNumberFormatter** to format a phone number as it is being entered.</span></span> <span data-ttu-id="78f39-161">Sobald sich der Text in einer **TextBox** mit dem Namen „phoneNumberInputTextBox“ ändert, wird der Inhalt des Textfelds gemäß der aktuellen Standardregion formatiert und in einem **TextBlock** mit dem Namen „phoneNumberOutputTextBlock“ angezeigt.</span><span class="sxs-lookup"><span data-stu-id="78f39-161">Each time text changes in a **TextBox** named phoneNumberInputTextBox, the contents of the text box are formatted using the current default region and displayed in a **TextBlock** named phoneNumberOutputTextBlock.</span></span> <span data-ttu-id="78f39-162">Zu Demonstrationszwecken wird die Zeichenfolge auch für die Region Neuseeland formatiert und in einem TextBlock mit dem Namen phoneNumberOutputTextBlockNZ angezeigt.</span><span class="sxs-lookup"><span data-stu-id="78f39-162">For demonstration purposes, the string is also formatted using the region for New Zealand, and displayed in a TextBlock named phoneNumberOutputTextBlockNZ.</span></span>
  
```csharp
    using Windows.Globalization.PhoneNumberFormatting;

    PhoneNumberFormatter currentFormatter, NZFormatter;

    public MainPage()
    {
        this.InitializeComponent();

        // Use the default formatter for the current region
        this.currentFormatter = new PhoneNumberFormatter();

        // Create an explicit formatter for New Zealand. 
        PhoneNumberFormatter.TryCreate("NZ", out this.NZFormatter);
    }

    private void phoneNumberInputTextBox_TextChanged(object sender, TextChangedEventArgs e)
    {
        // Format for the default region.
        this.phoneNumberOutputTextBlock.Text = currentFormatter.FormatPartialString(this.phoneNumberInputTextBox.Text);

        // If the NZFormatter was created successfully, format the partial string for the NZ TextBlock.
        if(this.NZFormatter != null)
        {
            this.phoneNumberOutputTextBlockNZ.Text = this.NZFormatter.FormatPartialString(this.phoneNumberInputTextBox.Text);
        }
    }
```    

<span data-ttu-id="78f39-163">Sie können den nachstehenden Code auf Ihrem PC testen. Ändern Sie dazu Land oder Region unter **Einstellungen** > **Zeit und Sprache** > **Region und Sprache** > **Land oder Region**.</span><span class="sxs-lookup"><span data-stu-id="78f39-163">You can test the code above on your own PC by changing the country or region in **Settings** > **Time & Language** > **Region & language** > **Country or region**.</span></span> <span data-ttu-id="78f39-164">Wählen Sie ein Land oder eine Region aus (z.B. Neuseeland, um zu prüfen, ob die Formate stimmen), und führen Sie den Code erneut aus.</span><span class="sxs-lookup"><span data-stu-id="78f39-164">Choose a country or region (perhaps New Zealand to confirm that the formats match), and run the code again.</span></span> <span data-ttu-id="78f39-165">Für Testdaten können Sie eine Websuche nach der Telefonnummer eines Unternehmens in Neuseeland durchführen.</span><span class="sxs-lookup"><span data-stu-id="78f39-165">For test data, you can do a web search for the phone number of a business in New Zealand.</span></span>

## <a name="the-users-language-and-cultural-preferences"></a><span data-ttu-id="78f39-166">Sprach- und Kultureinstellungen des Benutzers</span><span class="sxs-lookup"><span data-stu-id="78f39-166">The user's language and cultural preferences</span></span>

<span data-ttu-id="78f39-167">Für Szenarien, in denen Sie basierend auf den Sprach-, Regions- und Kultureinstellungen des Benutzers unterschiedliche Funktionen bereitstellen möchten, bietet Windows die Möglichkeit, über [**Windows.System.UserProfile.GlobalizationPreferences**](/uwp/api/windows.system.userprofile.globalizationpreferences?branch=live) auf diese Einstellungen zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="78f39-167">For scenarios where you wish to provide different functionality based solely on the user's language, region, or cultural preferences, Windows gives you a way to access those preferences, through [**Windows.System.UserProfile.GlobalizationPreferences**](/uwp/api/windows.system.userprofile.globalizationpreferences?branch=live).</span></span> <span data-ttu-id="78f39-168">Verwenden Sie bei Bedarf die **GlobalizationPreferences**-Klasse, um den Wert der aktuellen Region des Benutzers sowie die bevorzugten Sprachen, Währungen usw. zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="78f39-168">When needed, use the **GlobalizationPreferences** class to get the value of the user's current geographic region, preferred languages, preferred currencies, and so on.</span></span> <span data-ttu-id="78f39-169">Aber vergessen Sie nicht: Wenn die Zeichenfolgen/Bilder Ihrer App nicht für die bevorzugte Sprache des Benutzers lokalisiert sind, werden Datum, Uhrzeit und andere Daten, die für diese bevorzugte Sprache formatiert sind, nicht mit den Zeichenfolgen übereinstimmen, die Sie anzeigen.</span><span class="sxs-lookup"><span data-stu-id="78f39-169">But remember that if your app's strings/images aren't localized for the user's preferred language then dates and times and other data formatted for that preferred language won't match the strings that you display.</span></span>

## <a name="important-apis"></a><span data-ttu-id="78f39-170">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="78f39-170">Important APIs</span></span>

* [<span data-ttu-id="78f39-171">DateTimeFormatter</span><span class="sxs-lookup"><span data-stu-id="78f39-171">DateTimeFormatter</span></span>](/uwp/api/windows.globalization.datetimeformatting?branch=live)
* [<span data-ttu-id="78f39-172">NumberFormatting</span><span class="sxs-lookup"><span data-stu-id="78f39-172">NumberFormatting</span></span>](/uwp/api/windows.globalization.numberformatting?branch=live)
* [<span data-ttu-id="78f39-173">Calendar</span><span class="sxs-lookup"><span data-stu-id="78f39-173">Calendar</span></span>](/uwp/api/windows.globalization.calendar?branch=live)
* [<span data-ttu-id="78f39-174">PhoneNumberFormatting</span><span class="sxs-lookup"><span data-stu-id="78f39-174">PhoneNumberFormatting</span></span>](/uwp/api/windows.globalization.phonenumberformatting?branch=live)
* [<span data-ttu-id="78f39-175">GlobalizationPreferences</span><span class="sxs-lookup"><span data-stu-id="78f39-175">GlobalizationPreferences</span></span>](/uwp/api/windows.system.userprofile.globalizationpreferences?branch=live)

## <a name="related-topics"></a><span data-ttu-id="78f39-176">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="78f39-176">Related topics</span></span>

* [<span data-ttu-id="78f39-177">Kalender-, Datums- und Uhrzeitsteuerelemente</span><span class="sxs-lookup"><span data-stu-id="78f39-177">Calendar, date, and time controls</span></span>](../controls-and-patterns/date-and-time.md)
* [<span data-ttu-id="78f39-178">Benutzerprofilsprachen und App-Manifest-Sprachen verstehen</span><span class="sxs-lookup"><span data-stu-id="78f39-178">Understand user profile languages and app manifest languages</span></span>](manage-language-and-region.md)
* [<span data-ttu-id="78f39-179">Anpassen von Ressourcen mit Qualifizierern für Sprache, Skalierung, hohen Kontrast und andere Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="78f39-179">Tailor your resources for language, scale, high contrast, and other qualifiers</span></span>](../../app-resources/tailor-resources-lang-scale-contrast.md)

## <a name="samples"></a><span data-ttu-id="78f39-180">Beispiele</span><span class="sxs-lookup"><span data-stu-id="78f39-180">Samples</span></span>

* [<span data-ttu-id="78f39-181">Kalenderdetails und Mathematikbeispiel</span><span class="sxs-lookup"><span data-stu-id="78f39-181">Calendar details and math sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231636)
* [<span data-ttu-id="78f39-182">Beispiel für Datums- und Uhrzeitformatierung</span><span class="sxs-lookup"><span data-stu-id="78f39-182">Date and time formatting sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231618)
* [<span data-ttu-id="78f39-183">Beispiel für Globalisierungseinstellungen</span><span class="sxs-lookup"><span data-stu-id="78f39-183">Globalization preferences sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231608)
* [<span data-ttu-id="78f39-184">Beispiel für Zahlenformatierung und Analyse</span><span class="sxs-lookup"><span data-stu-id="78f39-184">Number formatting and parsing sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231620)
