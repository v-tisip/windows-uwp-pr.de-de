---
author: TylerMSFT
title: Erstellen einer universellen Windows-Plattform-Konsolen-App
description: In diesem Thema erfahren Sie, wie Sie eine UWP-App erstellen, die in einem Konsolenfenster ausgeführt wird.
keywords: console uwp
ms.author: twhitney
ms.date: 08/02/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: medium
ms.openlocfilehash: e4c1b1df8ad29635f38ae5b373685d3504a4eb60
ms.sourcegitcommit: 933e71a31989f8063b020746fdd16e9da94a44c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2018
ms.locfileid: "4530002"
---
# <a name="create-a-universal-windows-platform-console-app"></a>Erstellen einer universellen Windows-Plattform-Konsolen-App

Dieses Thema enthält Informationen zum Erstellen einer [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt) oder C++ / CX universelle Windows-Plattform (UWP)-Konsolen-app.

Ab Windows 10, Version 1803, können Sie schreiben C++ / WinRT oder C++ / CX UWP Konsolen-apps, die in einem Konsolenfenster wie z. B. einem DOS oder PowerShell-Konsolenfenster ausgeführt. Konsolen-apps verwenden das Konsolenfenster für die Eingabe und Ausgabe und können [Universelle C++-Runtime](/cpp/c-runtime-library/reference/crt-alphabetical-function-reference) -Funktionen wie z. B. **Printf** und **Getchar**verwenden. UWP-Konsolen-Apps können im Microsoft Store veröffentlicht werden. Sie haben einen Eintrag in der App-Liste und eine primäre Kachel, die an das Startmenü angeheftet werden kann. UWP-Konsolen-apps können über das Startmenü gestartet werden, obwohl Sie in der Regel über die Befehlszeile gestartet werden.

Hier sehen Sie ein Video über das Erstellen einer UWP-Konsolen-App, um eine Aktion anzuzeigen.

> [!VIDEO https://www.youtube.com/embed/bwvfrguY20s]

## <a name="use-a-uwp-console-app-template"></a>Verwenden einer UWP-Konsolen-App-Vorlage 

Um eine UWP-Konsolen-App zu erstellen, installieren Sie zuerst die **Konsolen-App (Universal)-Projektvorlagen**, die Sie im [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=AndrewWhitechapelMSFT.ConsoleAppUniversal) erhalten. Die installierten Vorlagen sind Rahmen des **Neuen Projekts** > **installierte** > **Andere Sprachen** > **Visual C++** > **Windows Universal** als **Console App c++ / WinRT (Universal Windows) **und **Console App C++ / CX (Universal Windows)**.

## <a name="add-your-code-to-main"></a>Ihren Code „main()” hinzufügen

Die Vorlagen fügen **Program.cpp** hinzu, die die `main()`-Funktion enthält. Hier beginnt die Ausführung in einer UWP-App-Konsole. Greifen Sie mit den Parametern `__argc` und `__argv` auf die Befehlszeilenargumente zu. Die UWP-Konsolen-App wird beendet, wenn die Steuerung von `main()` zurückgegeben wird.

Im folgende Beispiel **Program.cpp** wird hinzugefügt, indem die **Console App c++ / WinRT** Vorlage:

```cppwinrt
#include "pch.h"

using namespace winrt;

// This example code shows how you could implement the required main function
// for a Console UWP Application. You can replace all the code inside main
// with your own custom code.

int __cdecl main()
{
    // You can get parsed command-line arguments from the CRT globals.
    wprintf(L"Parsed command-line arguments:\n");
    for (int i = 0; i < __argc; i++)
    {
        wprintf(L"__argv[%d] = %S\n", i, __argv[i]);
    }

    // Keep the console window alive in case you want to see console output when running from within Visual Studio
      wprintf(L"Press 'Enter' to continue: ");
    getchar();
}
```

## <a name="uwp-console-app-behavior"></a>Verhalten der UWP-Konsolen-App

Eine UWP-Konsolen-App kann sowohl aus dem Verzeichnis auf das Dateisystem zugreifen, aus dem sie ausgeführt wird, sowie aus Unterverzeichnissen dessen. Dies ist möglich, da die Vorlage der Datei „Package.appxmanifest” der App die [AppExecutionAlias](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap5-appexecutionalias)-Erweiterung hinzufügt. Diese Erweiterung ermöglicht auch, dass der Benutzer den Alias in einem Konsolenfenster eingeben kann, um die App zu starten. Die App muss sich für den Start nicht im Systempfad befinden.

Darüber hinaus können Sie Ihrer UWP-Konsolen-App umfassenden Zugriff auf das Dateisystem erteilen, indem Sie die eingeschränkte Funktion `broadFileSystemAccess`, wie in [Berechtigungen für den Dateizugriff](https://docs.microsoft.com/windows/uwp/files/file-access-permissions) beschrieben, hinzufügen. Diese Funktion funktioniert mit APIs im [**Windows.Storage**](https://msdn.microsoft.com/library/windows/apps/BR227346)-Namespace.

Zu jedem beliebigen Zeitpunkt kann mehr als eine Instanz einer UWP-Konsolen-App ausgeführt werden, da die Vorlage der Datei „Package.appxmanifest” Ihrer App die [SupportsMultipleInstances](multi-instance-uwp.md)-Funktion hinzufügt.

Außerdem fügt die Vorlage der Datei „Package.appxmanifest” die `Subsystem="console"`-Funktion hinzu, die angibt, dass es sich bei dieser UWP-App um eine Konsolen-App handelt. Beachten Sie die Präfixe `desktop4` und iot2 `namespace`. UWP-Konsolen-Apps werden nur für Desktop- und Internet der Dinge (IoT)-Projekte unterstützt.

```xml
<Package
  ...
  xmlns:desktop4="http://schemas.microsoft.com/appx/manifest/desktop/windows10/4" 
  xmlns:iot2="http://schemas.microsoft.com/appx/manifest/iot/windows10/2" 
  IgnorableNamespaces="uap mp uap5 desktop4 iot2">
  ...
  <Applications>
    <Application Id="App"
      ...
      desktop4:Subsystem="console" 
      desktop4:SupportsMultipleInstances="true" 
      iot2:Subsystem="console" 
      iot2:SupportsMultipleInstances="true"  >
      ...
      <Extensions>
          <uap5:Extension 
            Category="windows.appExecutionAlias" 
            Executable="YourApp.exe" 
            EntryPoint="YourApp.App">
            <uap5:AppExecutionAlias desktop4:Subsystem="console">
              <uap5:ExecutionAlias Alias="YourApp.exe" />
            </uap5:AppExecutionAlias>
          </uap5:Extension>
      </Extensions>
    </Application>
  </Applications>
    ...
</Package>
```

## <a name="additional-considerations-for-uwp-console-apps"></a>Weitere Überlegungen zu UWP-Konsolen-Apps

- Nur C++ / WinRT und C++ / CX-UWP-apps können Konsolen-apps sein.
- UWP-Konsolen-Apps müssen auf den Projekttyp Desktop oder IoT ausgerichtet sein.
- UWP-Konsolen-apps dürfen kein Fenster erstellen. Sie können keine MessageBox(), oder Location() und alle anderen APIs, die ein Fenster aus irgendeinem Grund erstellen kann verwenden, z. B. Zustimmung aufgefordert werden.
- UWP-Konsolen-Apps darf nicht Hintergrundaufgaben nutzen oder als Hintergrundaufgabe dienen.
- Mit Ausnahme der [Befehlszeilenaktivierung](https://blogs.windows.com/buildingapps/2017/07/05/command-line-activation-universal-windows-apps/#5YJUzjBoXCL4MhAe.97) unterstützen UWP-Konsolen-Apps keine Support-Aktivierungsverträge, einschließlich Dateizuordnung, Protokollzuordnung usw.
- Obwohl UWP-Konsolen-Apps die Multiinstanzerstellung unterstützen, bieten Sie keine Unterstützung für die [Umleitung bei der Multiinstanzerstellung](multi-instance-uwp.md)
- Eine Liste von Win32-APIs, die für UWP-Apps verfügbar sind, finden Sie unter [Win32- und COM-APIs für UWP-Apps](https://docs.microsoft.com/uwp/win32-and-com/win32-and-com-for-uwp-apps)