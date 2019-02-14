---
title: Machen Sie Ihre Anwendung startklar für den Wechsel der japanischen Ära
description: 'Hier erhalten Sie Informationen zum im Mai 2019 anstehenden Wechsel der japanischen Ära, und wie Sie Ihre Anwendung darauf entsprechend vorbereiten können.'
ms.assetid: 5A945F9A-8632-4038-ADD6-C0568091EF27
ms.date: 11/29/2018
ms.topic: article
keywords: 'Windows 10, UWP, Lokalisierbarkeit, Lokalisierung, japanisch, Ära'
ms.localizationpriority: high
---

# Machen Sie Ihre Anwendung startklar für den Wechsel der japanischen Ära

Der japanische Kalender ist in Ären unterteilt, und für den Großteil des modernen Computerzeitalters haben wir uns in der Heisei-Ära befunden. Am 1. Mai 2019 beginnt jedoch eine neue Ära. Da dies das erste Mal seit Jahrzehnten ist, dass ein Wechsel der Ären stattfindet, muss Software, die den japanischen Kalender unterstützt, getestet werden, um sicherzustellen, dass sie zu Beginn der neuen Ära ordnungsgemäß funktioniert.

In den folgenden Abschnitten erfahren Sie, was Sie tun können, um Ihre Anwendung auf die neue Ära vorzubereiten und zu testen.

> [!NOTE]
> Wir empfehlen, hierfür eine Testmaschine zu verwenden, da die von Ihnen vorgenommenen Änderungen das Verhalten des gesamten Computers beeinflussen.

## Hinzufügen eines Registrierungsschlüssels für die neue Ära

Es ist wichtig, auf Kompatibilitätsprobleme hin zu testen, bevor der Epochenwechsel stattgefunden hat. Dies können Sie nun mithilfe eines Platzhalternamens vornehmen. Fügen Sie dazu mithilfe des **Registrierungs-Editors** einen Registrierungsschlüssel für die neue Ära hinzu:

1. Navigieren Sie zu **Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\Calendars\Japanese\Eras**.
2. Wählen Sie **Bearbeiten > Neu > Zeichenfolge** aus, und weisen Sie ihr den Namen **2019 05 01** zu.
3. Klicken Sie mit der rechten Maustaste auf den Schlüssel, und wählen Sie **Ändern** aus.
4. Geben Sie im Feld **Wert** **？？\_？\_??????\_?** ein (Sie können den Wert der Einfachheit halber von hier kopieren und einfügen).

Weitere Informationen finden Sie unter [Umgang mit Ären im japanischen Kalender](https://docs.microsoft.com/windows/desktop/Intl/era-handling-for-the-japanese-calendar), wo Sie weitere Einzelheiten über das Format für diese Registrierungsschlüssel erhalten können.

Sobald der Name der neuen Ära angekündigt wurde, enthält ein Update mit einem neuen Registrierungsschlüssel für unterstützte Windows-Versionen diesen Namen. Sie können überprüfen, ob Ihre Anwendung damit ordnungsgemäß umgehen kann. Dieses Update wird für unterstützte frühere Versionen von Windows 10 sowie Windows 8 und 7 bereitgestellt.

Nachdem Sie das Testen Ihrer Anwendung abgeschlossen haben, können Sie den Platzhalter-Registrierungsschlüssel löschen. Auf diese Weise wird sichergestellt, dass der neue Registrierungsschlüssel, der bei der Aktualisierung von Windows hinzugefügt wird, nicht beeinträchtigt wird.

## Ändern des Kalenderformats Ihres Geräts

Nachdem Sie den Registrierungsschlüssel für die neue Ära hinzugefügt haben, müssen Sie Ihr Gerät für die Verwendung des japanischen Kalenders konfigurieren. Sie benötigen dazu kein Gerät in japanischer Sprache. Um gründliche Tests durchzuführen, können Sie auch das japanische Sprachpaket installieren; dies ist für die grundlegenden Tests jedoch nicht erforderlich.

So konfigurieren Sie Ihr Gerät für die Verwendung des japanischen Kalenders:

1. Öffnen Sie **intl.cpl** (suchen Sie in der Windows-Suchleiste danach).
2. Wählen Sie in der Dropdown-Liste **Format** **Japanisch (Japan)** aus.
3. Wählen Sie **Zusätzliche Einstellungen** aus.
4. Wählen Sie die Registerkarte **Datum** aus.
5. Wählen Sie in der Dropdown-Liste **Kalendertyp** **和暦** (*Wareki*, den japanischen Kalender) aus. Es sollte die zweite Option sein.
6. Klicken Sie auf **OK**.
7. Klicken Sie im Fenster **Region** auf **OK** .

Ihr Gerät sollte nun für die Verwendung des japanischen Kalenders konfiguriert sein und die in der Registrierung eingetragenen Ären anzeigen. Nachstehend sehen Sie ein Beispiel dafür, was Sie möglicherweise in der rechten unteren Ecke des Bildschirms sehen:

![Datum und Uhrzeit im japanischen Kalenderformat](images/japanese-calendar-format.png)

## Einstellen der Uhr des Geräts

Um zu überprüfen, ob Ihre Anwendung mit den neuen Ära funktioniert, müssen Sie die Uhr Ihres Computers auf den 1. Mai 2019 oder auf ein späteres Datum stellen. Die folgenden Anweisungen gelten für Windows 10, Windows 8 und 7 sollten jedoch ähnlich funktionieren:

1. Klicken Sie mit der rechten Maustaste auf den Datums-/Uhrzeitbereich in der unteren rechten Ecke des Bildschirms.
2. Wählen Sie **Datum/Uhrzeit ändern** aus.
3. Wählen Sie in der Einstellungs-App unter **Datum und Uhrzeit ändern** die Option **Ändern** aus.
4. Ändern Sie das Datum auf den 1. Mai 2019 oder später.

> [!NOTE]
> Möglicherweise können Sie das Datum basierend auf den Organisationseinstellungen nicht ändern. Wenn dies der Fall ist, sprechen Sie mit Ihrem Administrator. Alternativ können Sie Ihren Platzhalter-Registrierungsschlüssel bearbeiten, um ein bereits vergangenes Datum zu erhalten.

## Testen Ihrer Anwendung

Testen Sie nun, wie Ihre Anwendung mit der neuen Ära umgeht. Überprüfen Sie Stellen, an denen das Datum angezeigt wird, z. B. bei Zeitstempeln und in Datumsauswahlfeldern. Stellen Sie sicher, dass die Ära vor dem 1. Mai 2019 (Heisei, 平成) und danach (？？) korrekt ist.

### *Gannen* (元年)

In der Regel ist das Format für den japanischen Kalender **&lt;Name der Ära&gt; &lt;Jahr der Ära&gt;**. Das Jahr 2018 ist z. B. **Heisei 30** (平成30年).  Das erste Jahr einer Ära ist jedoch etwas Besonderes. Anstelle von **&lt;Name der Ära&gt; 1**, hat es das Format **&lt;Name der Ära&gt; 元年** (*Gannen*). Dementsprechend wäre das erste Jahr der Heisei-Ära 平成元年 (*Heisei Gannen*). Vergewissern Sie sich, dass Ihre Anwendung das erste Jahr der neuen Ära richtig verarbeitet und ？？元年 ausgibt.

## Zugehörige APIs

Es gibt mehrere WinRT-, .NET- und Win32-APIs, die aktualisiert werden, um mit dem Wechsel der Ären umgehen zu können. Sie müssen sich daher keine Sorgen machen, sofern Sie diese APIs verwenden. Auch wenn Sie sich vollständig auf diese APIs verlassen, ist es dennoch eine gute Idee, Ihre Anwendung zu testen und sicherzustellen, dass sie sich erwartungsgemäß verhält, insbesondere, wenn Sie sie für etwas Besonderes wie Parsing verwenden.

Aktualisierungen des Betriebssystems und der SDKs finden Sie unter [Updates für den Wechsel der japanischen Ära im Mai 2019](https://support.microsoft.com/help/4470918/updates-for-may-2019-japan-era-change).

Die folgenden APIs werden betroffen sein:

### WinRT

* [Windows.Globalization Namespace](https://docs.microsoft.com/uwp/api/windows.globalization)
    * [Kalenderklasse](https://docs.microsoft.com/uwp/api/windows.globalization.calendar)
        * [Methode „AddDays”](https://docs.microsoft.com/uwp/api/windows.globalization.calendar.adddays)
        * [Methode „AddEras”](https://docs.microsoft.com/uwp/api/windows.globalization.calendar.adderas)
        * [Methode „AddHours”](https://docs.microsoft.com/uwp/api/windows.globalization.calendar.addhours)
        * [Methode „AddMinutes”](https://docs.microsoft.com/uwp/api/windows.globalization.calendar.addminutes)
        * [Methode „AddMonths”](https://docs.microsoft.com/uwp/api/windows.globalization.calendar.addmonths)
        * [Methode „AddNanoseconds”](https://docs.microsoft.com/uwp/api/windows.globalization.calendar.addnanoseconds)
        * [Methode „AddPeriods”](https://docs.microsoft.com/uwp/api/windows.globalization.calendar.addperiods)
        * [Methode „AddSeconds”](https://docs.microsoft.com/uwp/api/windows.globalization.calendar.addseconds)
        * [Methode „AddWeeks”](https://docs.microsoft.com/uwp/api/windows.globalization.calendar.addweeks)
        * [Methode „AddYears”](https://docs.microsoft.com/uwp/api/windows.globalization.calendar.addyears)
        * [Eigenschaft „Era”](https://docs.microsoft.com/uwp/api/windows.globalization.calendar.era)
        * [Methode „EraAsString”](https://docs.microsoft.com/uwp/api/windows.globalization.calendar.eraasstring)
        * [Eigenschaft „FirstYearInThisEra”](https://docs.microsoft.com/uwp/api/windows.globalization.calendar.firstyearinthisera)
        * [Eigenschaft „LastEra”](https://docs.microsoft.com/uwp/api/windows.globalization.calendar.lastera)
        * [Eigenschaft „LastYearInThisEra”](https://docs.microsoft.com/uwp/api/windows.globalization.calendar.lastyearinthisera)
        * [Eigenschaft „NumberOfYearsInThisEra”](https://docs.microsoft.com/uwp/api/windows.globalization.calendar.numberofyearsinthisera)     
* [Namespace „Windows.Globalization.DateTimeFormatting”](https://docs.microsoft.com/uwp/api/windows.globalization.datetimeformatting)
    * [Klasse „DateTimeFormatter”](https://docs.microsoft.com/uwp/api/windows.globalization.datetimeformatting.datetimeformatter)
        * [Methode „Format”](https://docs.microsoft.com/uwp/api/windows.globalization.datetimeformatting.datetimeformatter.format)

### .NET

* [Namespace „System”](https://docs.microsoft.com/dotnet/api/system)
    * [Struktur „DateTime”](https://docs.microsoft.com/dotnet/api/system.datetime)
    * [Struktur „DateTimeOffset”](https://docs.microsoft.com/dotnet/api/system.datetimeoffset)
* [Namespace „System.Globalization”](https://docs.microsoft.com/dotnet/api/system.globalization)
    * [Klasse „Calendar”](https://docs.microsoft.com/dotnet/api/system.globalization.calendar)
    * [Klasse „DateTimeFormatInfo”](https://docs.microsoft.com/dotnet/api/system.globalization.datetimeformatinfo)
    * [Klasse „JapaneseCalendar”](https://docs.microsoft.com/dotnet/api/system.globalization.japanesecalendar)
    * [Klasse „JapaneseLunisolarCalendar”](https://docs.microsoft.com/dotnet/api/system.globalization.japaneselunisolarcalendar)

### Win32

* [Header „datetimeapi.h”](https://docs.microsoft.com/windows/desktop/api/datetimeapi/)
    * [Funktion „GetDateFormatA”](https://docs.microsoft.com/windows/desktop/api/datetimeapi/nf-datetimeapi-getdateformata)
    * [Funktion „GetDateFormatEx”](https://docs.microsoft.com/windows/desktop/api/datetimeapi/nf-datetimeapi-getdateformatex)
    * [Funktion „GetDateFormatW”](https://docs.microsoft.com/windows/desktop/api/datetimeapi/nf-datetimeapi-getdateformatw)
* [Header „winnls.h”](https://docs.microsoft.com/windows/desktop/api/winnls/)
    * [Funktion „EnumDateFormatsA”](https://docs.microsoft.com/windows/desktop/api/winnls/nf-winnls-enumdateformatsa)
    * [Funktion „EnumDateFormatsExA”](https://docs.microsoft.com/windows/desktop/api/winnls/nf-winnls-enumdateformatsexa)
    * [Funktion „EnumDateFormatsExEx”](https://docs.microsoft.com/windows/desktop/api/winnls/nf-winnls-enumdateformatsexex)
    * [Funktion „EnumDateFormatsExW”](https://docs.microsoft.com/windows/desktop/api/winnls/nf-winnls-enumdateformatsexw)
    * [Funktion „EnumDateFormatsW”](https://docs.microsoft.com/windows/desktop/api/winnls/nf-winnls-enumdateformatsw)
    * [Funktion „GetCalendarInfoA”](https://docs.microsoft.com/windows/desktop/api/winnls/nf-winnls-getcalendarinfoa)
    * [Funktion „GetCalendarInfoEx”](https://docs.microsoft.com/windows/desktop/api/winnls/nf-winnls-getcalendarinfoex)
    * [Funktion „GetCalendarInfoW”](https://docs.microsoft.com/windows/desktop/api/winnls/nf-winnls-getcalendarinfow)

## Weitere Informationen:

* [Umgang mit Ären im japanischen Kalender](https://docs.microsoft.com/windows/desktop/Intl/era-handling-for-the-japanese-calendar)
* [Das Y2K-Phänomen im japanischen Kalender](https://blogs.msdn.microsoft.com/shawnste/2018/04/12/the-japanese-calendars-y2k-moment/)
* [Verwenden der Registrierung zum Testen der neuen japanischen Ära unter Windows](https://blogs.msdn.microsoft.com/shawnste/2018/08/07/using-the-registry-to-test-the-new-japanese-era-on-windows/)
* [Gannen vs Ichinen](https://blogs.msdn.microsoft.com/shawnste/2018/11/12/gannen-vs-ichinen/)
* [Updates für den Wechsel der japanischen Ära im Mai 2019](https://support.microsoft.com/help/4470918/updates-for-may-2019-japan-era-change)
* [Umgang mit einer neuen Ära im japanischen Kalender in .NET](https://blogs.msdn.microsoft.com/dotnet/2018/11/14/handling-a-new-era-in-the-japanese-calendar-in-net/)

<!--HONumber=12月18_HO1-->

