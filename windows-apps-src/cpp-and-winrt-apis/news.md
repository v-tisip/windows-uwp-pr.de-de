---
description: Neuigkeiten und Änderungen zu C++ / WinRT.
title: Neuigkeiten in C++ / WinRT
ms.date: 10/03/2018
ms.topic: article
keywords: Windows 10, Uwp, Standard, c++, Cpp, Winrt, Projektion, Neuigkeiten, was die neue
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: 87ab438de08ed5d6165343e7b9c4a559f37b351e
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "8195488"
---
# <a name="whats-new-in-cwinrt"></a>Neuigkeiten in C++ / WinRT

Die folgende Tabelle enthält Neuigkeiten und Änderungen an [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) in die neuesten in der Regel verfügbare Version des Windows SDK, ist die 10.0.17763.0 (Windows 10, Version 1809). Diese Änderungen möglicherweise auch in neueren SDK Insider Preview-Versionen vorhanden.

## <a name="news-and-changes-in-windows-sdk-version-100177630-windows-10-version-1809"></a>Neuigkeiten und Änderungen in Windows SDK-Version 10.0.17763.0 (Windows 10, Version 1809)

| Neue oder geänderte feature | Weitere Informationen |
| - | - |
| **Bedeutende Änderung**. Damit es zu kompilieren, C++ / WinRT ist nicht davon abhängig Header aus dem Windows SDK. | Nachfolgend finden Sie in der [Isolierung von Windows SDK-Header-Dateien](#isolation-from-windows-sdk-header-files), die. |
| Das Visual Studio-Projekt System-Format wurde geändert. | Finden Sie unter [wie neu zuweisen, Ihre C++ / WinRT-Projekt auf eine neuere Version des Windows SDK](#how-to-retarget-your-cwinrt-project-to-a-later-version-of-the-windows-sdk)unten. |
| Es gibt neue Funktionen und Basisklassen, mit denen Sie ein Objekt Sammlung an eine Windows-Runtime-Funktion übergeben können oder Ihre eigenen Sammlungseigenschaften und Sammlungstypen implementieren. | Finden Sie unter [Sammlungen mit C++ / WinRT](collections.md). |
| Sie können die Markuperweiterung [{Binding}](/windows/uwp/xaml-platform/binding-markup-extension) verwenden, mit der C++ / WinRT-Runtime-Klassen. | Weitere Informationen und Codebeispiele finden Sie in der [Übersicht über Datenbindung](/windows/uwp/data-binding/data-binding-quickstart). |
| Unterstützung für die Stornierung einer Coroutine können Sie zum Registrieren eines Rückrufs Abbruch. | Weitere Informationen und Codebeispiele finden Sie unter [Abbrechen eines Vorgangs asychrone und Abbruch Rückrufe](concurrency.md#canceling-an-asychronous-operation-and-cancellation-callbacks). |
| Wenn Sie einen Delegaten, der auf eine Member-Funktion zu erstellen, können Sie festlegen, eine starke oder schwache Referenz auf das aktuelle Objekt (statt eine unformatierte *diesem* Zeiger) an der Stelle, in dem der Handler registriert ist. | Weitere Informationen und Codebeispiele finden Sie unter der **bei der Verwendung einer Member-Funktion als Delegaten** Unterabschnitt im Abschnitt [problemlos den Zugriff auf die *dieser* Zeiger mit einem Delegaten für die Ereignisbehandlung](weak-references.md#safely-accessing-the-this-pointer-with-an-event-handling-delegate). |
| Fehler behoben, die von Visual Studio bessere Übereinstimmung mit der C++-standard aufgedeckt wurden. Die toolkette LLVM und Clang wird auch besser genutzt, zum Überprüfen von C++ / WinRT-Standardkonformität. | Wird nicht mehr auftreten des Problems wird nicht in [beschrieben warum mein neues Projekt kompilieren? Ich verwende Visual Studio 2017 (Version 15.8.0 oder höher), und SDK-Version 17134](faq.md#why-wont-my-new-project-compile-im-using-visual-studio-2017-version-1580-or-higher-and-sdk-version-17134) |

Andere gewünschte Änderungen vornehmen.

- **Bedeutende Änderung**. [**Winrt::get_abi(winrt::hstring const&)**](/uwp/cpp-ref-for-winrt/get-abi) gibt jetzt `void*` anstelle von `HSTRING`. Sie können `static_cast<HSTRING>(get_abi(my_hstring));` um ein HSTRING zu erhalten.
- **Bedeutende Änderung**. [**WinRT::put_abi(WinRT::hstring&)**](/uwp/cpp-ref-for-winrt/put-abi) jetzt gibt `void**` anstelle von `HSTRING*`. Sie können `reinterpret_cast<HSTRING*>(put_abi(my_hstring));` um ein HSTRING * zu erhalten.
- **Bedeutende Änderung**. HRESULT wird jetzt als **WinRT:: HRESULT**projiziert. Wenn Sie benötigen ein HRESULT (bei der Eingabe überprüfen oder Typ Traits unterstützen), können Sie `static_cast` ein **WinRT:: HRESULT**. Andernfalls **WinRT:: HRESULT** in konvertiert HRESULT, solange Sie enthalten `unknwn.h` bevor Sie alle C++ aufnehmen / WinRT-Header.
- **Bedeutende Änderung**. GUID wird jetzt als **winrt::guid**projiziert. APIs, die Sie implementieren, müssen Sie **winrt::guid** für GUID-Parameter verwenden. Andernfalls **WinRT:: HRESULT** in konvertiert GUID, solange Sie enthalten `unknwn.h` bevor Sie alle C++ aufnehmen / WinRT-Header.
- **Bedeutende Änderung**. Der [**Konstruktor winrt::handle_type**](/uwp/cpp-ref-for-winrt/handle-type#handletypehandletype-constructor) wurde durch es explizites (es ist jetzt schwieriger, um falsch Code mit ihm zu schreiben) abgesichert. Wenn Sie einen unformatierten Handlewert zuweisen möchten, rufen Sie stattdessen die [**handle_type::attach-Funktion**](/uwp/cpp-ref-for-winrt/handle-type#handletypeattach-function) .
- **Bedeutende Änderung**. Die Signaturen von **WINRT_CanUnloadNow** und **WINRT_GetActivationFactory** wurden geändert. Diese Funktionen darf nicht auf allen deklariert werden. Fügen Sie stattdessen `winrt/base.h` (der automatisch enthalten ist, wenn Sie alle C++ / WinRT-Windows-Namespace-Header-Dateien) für die Deklarationen für diese Funktionen umfassen.
- Für die [**winrt::clock-Struktur**](/uwp/cpp-ref-for-winrt/clock)sind **From_FILETIME/To_FILETIME** zugunsten von **From_file_time/To_file_time**.
- APIs, die davon ausgehen, **IBuffer** Parameter dass werden vereinfacht. Obwohl die meisten APIs Sammlungen und Arrays bevorzugen, per genügend APIs **IBuffer** , die es einfacher, verwenden Sie diese APIs von C++ erforderlich. Dieses Update bietet direkten Zugriff auf die Daten hinter einer **IBuffer** Implementierung mit der gleichen Daten verwendete Benennungskonvention von der C++ Standard Library-Containern. Dadurch wird verhindert, und Aktivitäts-Metadaten-Namen, die im herkömmlichen Sinn mit einem Großbuchstaben beginnen.
- Verbesserte codegenerierung: verschiedenen Verbesserungen für Code, verkleinern Inlinefunktion und Optimierung der optimieren Factory Zwischenspeichern.
- Unnötige Rekursion entfernt. Wenn die Befehlszeile bezieht sich auf einen Ordner, anstatt auf eine bestimmte `.winmd`, wird die `cppwinrt.exe` Tool sucht nicht mehr rekursiv nach `.winmd` Dateien. Die `cppwinrt.exe` Tool jetzt auch behandelt Duplikate intelligenter, um ihn stabiler Benutzer Fehler und zu schlecht formatiertes `.winmd` Dateien.
- Verstärkten intelligenten Zeigern. Früher zugewiesene verschieben das Ereignis der zugeordneten Rücknahmeschlüssel konnte nicht widerrufen, wenn einen neuen Wert. Auf diese Weise konnten, ein Problem aufdecken, in denen intelligenten Zeiger Klassen Self Zuordnung zuverlässig handhaben waren nicht; als Stamm gebunden, in der [**WinRT:: com_ptr strukturvorlage**](/uwp/cpp-ref-for-winrt/com-ptr). **WinRT:: com_ptr** behoben wurde, und das Ereignis der zugeordneten Rücknahmeschlüssel behoben, behandeln verschieben Semantik korrekt, damit sie nach Zuweisung widerrufen.

> [!NOTE]
> Mit Version 1.0.181002.2 (oder höher) von der [C++ / WinRT Visual Studio Extension (VSIX)](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-and-the-vsix) installiert haben, erstellen eine neue C++ / WinRT-Projekt installiert automatisch das [Microsoft.Windows.CppWinRT NuGet-Paket](https://www.nuget.org/packages/Microsoft.Windows.CppWinRT/) für das Projekt. Das Microsoft.Windows.CppWinRT NuGet-Paket bietet verbesserte C++ / WinRT-Projekt Build Support, indem Ihr Projekt tragbaren zwischen einem Entwicklungscomputer und einen Build-Agent (auf dem die NuGet-Paket und nicht VSIX, installiert ist).
>
> Für ein vorhandenes Projekt&mdash;nach der Installation von Version 1.0.181002.2 (oder höher) des VSIX&mdash;es wird empfohlen, dass Sie das Projekt in Visual Studio öffnen, klicken Sie auf **Projekt** \> **NuGet-Pakete verwalten...**  \>  **Durchsuchen**, geben Sie oder fügen Sie **Microsoft.Windows.CppWinRT** in das Suchfeld ein, wählen Sie das Element in den Suchergebnissen, und dann auf **Installieren** , um das Paket für das Projekt zu installieren.


## <a name="isolation-from-windows-sdk-header-files"></a>Isolation von Windows SDK-Header-Dateien

Dies ist möglicherweise eine bedeutende Änderung für Ihren Code.

Damit es zu kompilieren, C++ / WinRT nicht mehr hängt von Header-Dateien aus dem Windows SDK. Header-Dateien in der C++-Laufzeitbibliothek (CRT) und der C++ Standard Template Library (STL-) einfügen nicht auch alle Windows SDK-Header. Und verbessert die Standards Compliance, um eine unbeabsichtigte Abhängigkeiten und erheblich reduziert die Anzahl der Makros, die Sie zum Schutz gegen.

Diese Unabhängigkeit bedeutet, dass das C++ / WinRT ist jetzt besser portierbar und Standards kompatibel, und sie die Möglichkeit, dass sie immer eine Bibliothek Cross-Compiler und plattformübergreifenden optimiert. Außerdem bedeutet das, dass die C++ / WinRT-Header werden die betroffenen Makros nicht.

Wenn zuvor zu C++ links / WinRT, um alle Windows-Header in Ihrem Projekt einfügen, müssen Sie jetzt selbst einschließen. Es ist in jedem Fall immer empfiehlt es sich um explizit die Header enthalten, denen Sie abhängig sind, und lassen Sie es nicht in eine andere Bibliothek zum Einschließen für Sie.

Derzeit sind die einzigen Ausnahmen zu Windows SDK-Header-Datei Isolation für systeminternen Funktionen und numerische Werte. Es gibt keine bekannten Probleme für diese letzten verbleibenden Abhängigkeiten.

In Ihrem Projekt können Sie Interoperabilität mit den Windows SDK-Headern wieder aktivieren, wenn Sie möchten. Möglicherweise möchten Sie z. B. eine COM-Schnittstelle (als Stamm [**IUnknown**](https://msdn.microsoft.com/library/windows/desktop/ms680509)) zu implementieren. Für dieses Beispiel enthalten `unknwn.h` bevor Sie alle C++ aufnehmen / WinRT-Header. Dadurch C++ / WinRT-Basisbibliothek verschiedene Hooks zur Unterstützung von klassischer COM-Schnittstellen zu aktivieren. Ein Codebeispiel finden Sie unter ["author" COM-Komponenten mit C++ / WinRT](author-coclasses.md). Auf ähnliche Weise enthalten Sie explizit alle anderen Windows SDK-Header, die Deklarieren von Typen und/oder Funktionen, die Sie aufrufen möchten.

## <a name="how-to-retarget-your-cwinrt-project-to-a-later-version-of-the-windows-sdk"></a>Wie neu zuweisen, Ihre C++ / WinRT-Projekt auf eine neuere Version des Windows SDK

Die Methode zum Auswählen einer neuen Zielversion des Projekts, die wahrscheinlich das geringste Compiler und Linker Problem auftreten ist ist auch der am häufigsten aufwändig. Diese Methode umfasst das Erstellen eines neuen Projekts (für die Windows SDK-Version Ihrer Wahl) und dann Kopieren von Dateien über dem neuen Projekt auf Ihrem alten. Es werden Abschnitte der Ihre alten `.vcxproj` und `.vcxproj.filters` über Kopieren von Dateien, die Sie gerade können Sie das Hinzufügen von Dateien in Visual Studio zu speichern.

Es gibt jedoch zwei weitere Arten, Ihr Projekt in Visual Studio neu zuweisen.

- Navigieren Sie zum Projekt-Eigenschaft, die **Allgemeine** \> **Windows SDK-Version**, und wählen Sie **Alle Konfigurationen** und **Alle Plattformen**. Legen Sie **Windows SDK-Version** auf die Version, die Sie ansprechen möchten.
- Im **Projektmappen-Explorer**mit der rechten Maustaste des Projektknoten, klicken Sie auf **Projekte neu zuweisen**, wählen Sie die Versionen, die Sie abzielen möchten und klicken Sie dann auf **OK**.

Wenn Sie alle Compiler und Linkerfehler auftritt, nachdem Sie mithilfe der folgenden zwei Methoden, können Sie versuchen, die Lösung bereinigen (**Build** > **Projektmappe bereinigen** bzw. alle temporären Ordner und Dateien manuell löschen) bevor Sie versuchen, erneut zu erstellen.

Wenn der C++ Compiler erzeugt "*Fehler C2039: 'IUnknown': ist kein Mitglied des" \'global Namespace''*", fügen Sie dann `#include <unknwn.h>` an den Anfang Ihrer `pch.h` Datei (bevor Sie alle C++ aufnehmen / WinRT-Header).

Sie müssen möglicherweise auch hinzufügen `#include <hstring.h>` danach.

Wenn der C++ Linker erzeugt "*Fehler LNK2019: nicht aufgelöstes externes Symbol _WINRT_CanUnloadNow@0 verwiesen in Funktion _VSDesignerCanUnloadNow@0 *", und klicken Sie dann, die durch Hinzufügen zu beheben `#define _VSDESIGNER_DONT_LOAD_AS_DLL` auf Ihre `pch.h` Datei.
