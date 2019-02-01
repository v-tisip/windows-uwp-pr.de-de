---
description: Neuigkeiten und Änderungen zu C++ / WinRT.
title: Neuigkeiten in C++ / WinRT
ms.date: 01/29/2019
ms.topic: article
keywords: Windows 10, Uwp, Standard, c++, Cpp, Winrt, Projektion, Neuigkeiten, was die neue
ms.localizationpriority: medium
ms.custom: RS5
ms.openlocfilehash: cb624a93a010dfe9784cf8c26beed12c6cf2f77d
ms.sourcegitcommit: 2d2483819957619b6de21b678caf887f3b1342af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2019
ms.locfileid: "9042432"
---
# <a name="whats-new-in-cwinrt"></a>Neuigkeiten in C++ / WinRT

Die folgende Tabelle enthält News und Änderungen an [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) in die neuesten in der Regel verfügbare Version des Windows SDKS, ist die 10.0.17763.0 (Windows 10, Version 1809). Diese Änderungen möglicherweise auch in neueren SDK Insider Preview-Versionen vorhanden.

## <a name="news-and-changes-in-windows-sdk-version-100177630-windows-10-version-1809"></a>Neuigkeiten und Änderungen in Windows SDK-Version 10.0.17763.0 (Windows 10, Version 1809)

| Neue oder geänderte feature | Weitere Informationen |
| - | - |
| **Bedeutende Änderung**. Damit es zu kompilieren, C++ / WinRT ist nicht davon abhängig Header aus dem Windows SDK. | Nachfolgend finden Sie in der [Isolierung von Windows SDK-Header-Dateien](#isolation-from-windows-sdk-header-files). |
| Das Visual Studio-Projekt System-Format wurde geändert. | Finden Sie unter [wie neu zuweisen, Ihre C++ / WinRT-Projekt auf eine neuere Version des Windows SDK](#how-to-retarget-your-cwinrt-project-to-a-later-version-of-the-windows-sdk)unten. |
| Es gibt neue Funktionen und Basisklassen, mit denen Sie ein Objekt Sammlung an eine Windows-Runtime-Funktion übergeben können oder Ihre eigenen Sammlungseigenschaften und Sammlungstypen implementieren. | Finden Sie unter [Sammlungen mit C++ / WinRT](collections.md). |
| Sie können die Markuperweiterung [{Binding}](/windows/uwp/xaml-platform/binding-markup-extension) verwenden, mit der C++ / WinRT-Runtime-Klassen. | Weitere Informationen und Codebeispiele finden Sie unter [Übersicht über Datenbindung](/windows/uwp/data-binding/data-binding-quickstart). |
| Unterstützung für den Abbruch einer Coroutine können Sie zum Registrieren eines Rückrufs Abbruch. | Weitere Informationen und Codebeispiele finden Sie [Abbrechen eines Vorgangs asychrone und Abbruch Rückrufe](concurrency.md#canceling-an-asychronous-operation-and-cancellation-callbacks). |
| Wenn Sie einen Delegaten, der auf eine Member-Funktion zu erstellen, können Sie festlegen, eine starke oder schwache Referenz auf das aktuelle Objekt (anstelle von unformatierten *dieser* -Zeiger) an der Stelle, wo der Handler registriert ist. | Weitere Informationen und Codebeispiele finden Sie **bei Verwendung von eine Member-Funktion als Delegaten** untergeordnete Abschnitt im Abschnitt [problemlos den Zugriff auf die *dieser* Zeiger mit einem Delegaten für die Ereignisbehandlung](weak-references.md#safely-accessing-the-this-pointer-with-an-event-handling-delegate). |
| Fehler behoben, die von Visual Studio verbesserte Konformität mit der C++-standard aufgedeckt wurden. Die toolkette LLVM und Clang wird auch besser genutzt, zum Überprüfen von C++ / WinRT-Standardkonformität. | Wird nicht mehr auftreten des Problems wird nicht in [beschrieben warum mein neues Projekt kompilieren? Ich verwende Visual Studio 2017 (Version 15.8.0 oder höher), und SDK-Version 17134](faq.md#why-wont-my-new-project-compile-im-using-visual-studio-2017-version-1580-or-higher-and-sdk-version-17134) |

Andere Änderungen.

- **Bedeutende Änderung**. [**WinRT::get_abi(WinRT::hstring const&)**](/uwp/cpp-ref-for-winrt/get-abi) jetzt gibt `void*` anstelle von `HSTRING`. Sie können `static_cast<HSTRING>(get_abi(my_hstring));` um ein HSTRING zu erhalten.
- **Bedeutende Änderung**. [**WinRT::put_abi(WinRT::hstring&)**](/uwp/cpp-ref-for-winrt/put-abi) jetzt gibt `void**` anstelle von `HSTRING*`. Sie können `reinterpret_cast<HSTRING*>(put_abi(my_hstring));` um ein HSTRING * zu erhalten.
- **Bedeutende Änderung**. HRESULT wird jetzt als **WinRT:: HRESULT**projiziert. Wenn Sie benötigen ein HRESULT (bei der Eingabe überprüfen oder Typ Traits unterstützen), können Sie `static_cast` ein **WinRT:: HRESULT**. Andernfalls **WinRT:: HRESULT** in konvertiert HRESULT, solange Sie enthalten `unknwn.h` bevor Sie alle C++ aufnehmen / WinRT-Header.
- **Bedeutende Änderung**. GUID wird jetzt als **winrt::guid**projiziert. APIs, die Sie implementieren, müssen Sie **winrt::guid** für GUID-Parameter verwenden. Andernfalls **WinRT:: HRESULT** in konvertiert GUID, solange Sie enthalten `unknwn.h` bevor Sie alle C++ aufnehmen / WinRT-Header.
- **Bedeutende Änderung**. Der [**Konstruktor winrt::handle_type**](/uwp/cpp-ref-for-winrt/handle-type#handletypehandletype-constructor) wurde durch es explizites (es ist jetzt schwieriger, um falsch Code mit ihm zu schreiben) abgesichert. Wenn Sie einen unformatierten Handlewert zuweisen möchten, rufen Sie stattdessen die [**handle_type::attach-Funktion**](/uwp/cpp-ref-for-winrt/handle-type#handletypeattach-function) .
- **Bedeutende Änderung**. Die Signaturen von **WINRT_CanUnloadNow** und **WINRT_GetActivationFactory** wurden geändert. Diese Funktionen darf nicht gar nicht deklariert werden. Fügen Sie stattdessen `winrt/base.h` (der automatisch enthalten ist, wenn Sie alle C++ / WinRT-Windows-Namespace-Header-Dateien) enthalten die Deklarationen dieser Funktionen.
- Für die [**winrt::clock-Struktur**](/uwp/cpp-ref-for-winrt/clock)sind **From_FILETIME/To_FILETIME** zugunsten von **From_file_time/To_file_time**.
- APIs, die davon ausgehen, **IBuffer** Parameter dass werden vereinfacht. Obwohl die meisten APIs Sammlungen oder Arrays bevorzugen, per genügend APIs **IBuffer** , die es einfacher, verwenden Sie diese APIs von C++ erforderlich. Dieses Update bietet direkten Zugriff auf die Daten hinter einer **IBuffer** Implementierung mit der gleichen Daten Benennungskonvention, die von den C++-Standardbibliothek-Containern verwendet. Dadurch wird verhindert, und Aktivitäts-Metadaten-Namen, die im herkömmlichen Sinn mit einem Großbuchstaben beginnen.
- Verbesserte-Zeitcode-Generierung: verschiedene Verbesserungen für Code, verkleinern Inlinefunktion und Optimierung der optimieren Factory Zwischenspeichern.
- Entfernt unnötige Rekursion. Wenn die Befehlszeile bezieht sich auf einen Ordner, anstatt auf einen bestimmten `.winmd`, die `cppwinrt.exe` Tool sucht nicht mehr rekursiv nach `.winmd` Dateien. Die `cppwinrt.exe` Tool jetzt auch behandelt Duplikate intelligenter, macht es stabiler Benutzer Fehler und zu schlecht gebildet `.winmd` Dateien.
- Gesicherte intelligenten Zeigern. Früher zugewiesene verschieben das Ereignis der zugeordneten Rücknahmeschlüssel konnte nicht widerrufen, wenn einen neuen Wert. Auf diese Weise konnten, ein Problem aufdecken, in denen intelligenten Zeiger Klassen Self Zuweisung zuverlässig handhaben waren nicht; als Stamm gebunden, in der [**WinRT:: com_ptr strukturvorlage**](/uwp/cpp-ref-for-winrt/com-ptr). **WinRT:: com_ptr** behoben wurde, und das Ereignis der zugeordneten Rücknahmeschlüssel behoben, behandeln verschieben Semantik korrekt, so dass sie nach Zuweisung widerrufen.

> [!IMPORTANT]
> Wichtige Änderungen vorgenommen wurden, damit die [C++ / WinRT Visual Studio Extension (VSIX)](https://aka.ms/cppwinrt/vsix), sowohl in Version 1.0.181002.2, und klicken Sie dann weiter unten in Version 1.0.190128.4. Weitere Informationen über diese Änderungen und Einfluss auf vorhandene Projekte, [Visual Studio-Unterstützung für C++ / WinRT](intro-to-using-cpp-with-winrt.md#visual-studio-support-for-cwinrt-xaml-the-vsix-extension-and-the-nuget-package) und [früheren Versionen der VSIX-Erweiterung](intro-to-using-cpp-with-winrt.md#earlier-versions-of-the-vsix-extension).

## <a name="isolation-from-windows-sdk-header-files"></a>Isolierung von Windows SDK-Header-Dateien

Dies ist möglicherweise eine bedeutende Änderung für Ihren Code.

Damit es zu kompilieren, C++ / WinRT nicht mehr hängt von Header-Dateien aus dem Windows SDK. Header-Dateien in der C++-Laufzeitbibliothek (CRT) und der C++ Standard Template Library (STL-) einfügen nicht auch alle Windows SDK-Header. Und verbessert die Einhaltung von Standards, um eine unbeabsichtigte Abhängigkeiten und erheblich reduziert die Anzahl der Makros, die Sie zum Schutz gegen.

Diese Unabhängigkeit bedeutet, dass das C++ / WinRT jetzt besser portierbar und Standards kompatibel ist und es die Möglichkeit, dass sie immer eine Bibliothek-Cross-Compiler und plattformübergreifenden optimiert. Außerdem bedeutet das, dass die C++ / WinRT-Header werden die betroffenen Makros nicht.

Wenn zuvor zu C++ links / WinRT, um alle Windows-Header in Ihrem Projekt einfügen, müssen Sie jetzt selbst einschließen. Es ist in jedem Fall immer empfiehlt es sich um explizit die Header enthalten, denen Sie abhängig sind, und lassen Sie es nicht in eine andere Bibliothek zum Einschließen für Sie.

Derzeit sind die einzigen Ausnahmen zu Windows SDK-Header-Datei Isolation für systeminternen Funktionen und numerische Werte. Es gibt keine bekannten Probleme für diese letzten verbleibenden Abhängigkeiten.

In Ihrem Projekt können Sie Interoperabilität mit den Windows SDK-Headern erneut aktivieren, wenn notwendig. Möglicherweise möchten Sie z. B. eine COM-Schnittstelle (als Stamm [**IUnknown**](https://msdn.microsoft.com/library/windows/desktop/ms680509)) zu implementieren. Für dieses Beispiel enthalten `unknwn.h` bevor Sie alle C++ aufnehmen / WinRT-Header. Dadurch C++ / WinRT-Basisbibliothek verschiedene Hooks zur Unterstützung von klassischer COM-Schnittstellen zu aktivieren. Ein Codebeispiel finden Sie unter ["author" COM-Komponenten mit C++ / WinRT](author-coclasses.md). Auf ähnliche Weise enthalten Sie explizit alle anderen Windows SDK-Header, die Deklarieren von Typen und/oder Funktionen, die Sie aufrufen möchten.

## <a name="how-to-retarget-your-cwinrt-project-to-a-later-version-of-the-windows-sdk"></a>Wie neu zuweisen, Ihre C++ / WinRT-Projekt auf eine neuere Version des Windows SDK

Die Methode zum Auswählen einer neuen Zielversion des Projekts, die wahrscheinlich das geringste Compiler und Linker Problem kommen ist auch der am häufigsten aufwändig. Diese Methode umfasst das Erstellen eines neuen Projekts (für die Windows SDK-Version Ihrer Wahl) und dann Kopieren von Dateien über in das neue Projekt auf Ihrem alten. Es werden die alte Abschnitte `.vcxproj` und `.vcxproj.filters` über Kopieren von Dateien, die Sie gerade können Sie das Hinzufügen von Dateien in Visual Studio zu speichern.

Es gibt jedoch zwei weitere Arten, Ihr Projekt in Visual Studio neu zuweisen.

- Wechseln Sie zum Projekt-Eigenschaft, die **Allgemeine** \> **Windows SDK-Version**, und wählen Sie **Alle Konfigurationen** und **Alle Plattformen**. Legen Sie **Windows SDK-Version** auf die Version, die Sie ansprechen möchten.
- Im **Projektmappen-Explorer**mit der rechten Maustaste in des Projektknoten, klicken Sie auf **Projekte neu zuweisen**, wählen Sie die Versionen, die Sie als Ziel möchten und klicken Sie dann auf **OK**.

Wenn Sie alle Compiler und Linkerfehler auftritt, nachdem Sie mithilfe der folgenden zwei Methoden, können Sie versuchen, die Projektmappe bereinigen (**Build** > **Projektmappe bereinigen** und/oder manuell löschen Sie alle temporären Ordner und Dateien) bevor Sie versuchen, erneut zu erstellen.

Wenn der C++ Compiler erzeugt "*Fehler C2039: 'IUnknown': ist kein Mitglied des" \'global Namespace''*", fügen Sie dann `#include <unknwn.h>` an den Anfang Ihrer `pch.h` Datei (bevor Sie alle C++ aufnehmen / WinRT-Header).

Sie müssen möglicherweise auch hinzufügen `#include <hstring.h>` danach.

Wenn der C++ Linker erzeugt "*Fehler LNK2019: nicht aufgelöstes externes Symbol _WINRT_CanUnloadNow@0 verwiesen in Funktion _VSDesignerCanUnloadNow@0 *", und klicken Sie dann, die durch Hinzufügen zu beheben `#define _VSDESIGNER_DONT_LOAD_AS_DLL` auf Ihre `pch.h` Datei.
