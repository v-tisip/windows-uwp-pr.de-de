---
ms.assetid: A5320094-DF53-42FC-A6BA-A958F8E9210B
title: Testen von Surface Hub-Apps mit Visual Studio
description: Der Visual Studio-Simulator bietet eine Umgebung für das Entwerfen, Entwickeln, Debuggen und Testen von UWP-Apps, einschließlich Apps für Surface Hub.
ms.date: 10/26/2017
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: db481fac1bdcb9e79762f52aee48574e987c4cbb
ms.sourcegitcommit: bf600a1fb5f7799961914f638061986d55f6ab12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2019
ms.locfileid: "9048883"
---
# <a name="test-surface-hub-apps-using-visual-studio"></a>Testen von Surface Hub-Apps mit Visual Studio
Der Visual Studio-Simulator bietet eine Umgebung, in der Sie Universelle Windows-Plattform (UWP)-Apps entwerfen, entwickeln, debuggen und testen können, einschließlich Apps, die Sie für Microsoft Surface Hub entwickelt haben. Der Simulator verwendet nicht dieselbe Benutzeroberfläche wie ein Surface Hub, aber es empfiehlt sich Ihre app aussieht und verhält sich mit den Surface Hub Bildschirmgröße und-Auflösung zu testen.

Weitere Informationen zu den Simulator-Tool im Allgemeinen finden Sie unter [Ausführen von UWP-apps im Simulator](https://docs.microsoft.com/visualstudio/debugger/run-windows-store-apps-in-the-simulator).

## <a name="add-surface-hub-resolutions-to-the-simulator"></a>Hinzufügen von Surface Hub-Auflösungen zum Simulator
So fügen Sie Surface Hub-Auflösungen zum Simulator hinzu:

1. Erstellen Sie eine Konfiguration für die 55" Surface Hub, indem Sie den folgenden XML-Code in eine Datei mit dem Namen *HardwareConfigurations-SurfaceHub55.xml*speichern.  

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <ArrayOfHardwareConfiguration xmlns:xsd="http://www.w3.org/2001/XMLSchema"
                                  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
        <HardwareConfiguration>
            <Name>SurfaceHub55</Name>
            <DisplayName>Surface Hub 55"</DisplayName>
            <Resolution>
                <Height>1080</Height>
                <Width>1920</Width>
            </Resolution>
            <DeviceSize>55</DeviceSize>
            <DeviceScaleFactor>100</DeviceScaleFactor>
        </HardwareConfiguration>
    </ArrayOfHardwareConfiguration>
    ```

2. Erstellen Sie eine Konfiguration für die 84" Surface Hub, indem Sie den folgenden XML-Code in eine Datei mit dem Namen *HardwareConfigurations-SurfaceHub84.xml*speichern.

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <ArrayOfHardwareConfiguration xmlns:xsd="http://www.w3.org/2001/XMLSchema"
                                  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
        <HardwareConfiguration>
            <Name>SurfaceHub84</Name>
            <DisplayName>Surface Hub 84"</DisplayName>
            <Resolution>
                <Height>2160</Height>
                <Width>3840</Width>
            </Resolution>
            <DeviceSize>84</DeviceSize>
            <DeviceScaleFactor>150</DeviceScaleFactor>
        </HardwareConfiguration>
    </ArrayOfHardwareConfiguration>
    ```

3. Kopieren Sie die zwei XML-Dateien in *C:\Programme (x86)\Gemeinsame Dateien\Microsoft Shared\Windows Simulator\\&lt;Versionsnummer&gt;\HardwareConfigurations*.

   > [!NOTE]
   > Zum Speichern der Dateien in diesem Ordner werden Administratorrechte benötigt.

4. Führen Sie Ihre App im Visual Studio-Simulator aus. Klicken Sie in der Palette auf die Schaltfläche **Change Resolution**, und wählen Sie in der Liste eine Surface Hub-Konfiguration aus.

    ![Auflösungen des Visual Studio-Simulators](images/vs-simulator-resolutions.png)

   > [!TIP]
   > [Tablet-Modus aktivieren](https://windows.microsoft.com/windows-10/getstarted-like-a-tablet) , um eine bessere simulieren die Erfahrung von Surface Hub.

## <a name="deploy-apps-to-a-surface-hub-device-from-visual-studio"></a>Bereitstellen von apps auf einem Surface Hub-Gerät aus Visual Studio
Manuelle Bereitstellen einer app für einen Surface Hub ist ein einfacher Vorgang.

### <a name="enable-developer-mode"></a>Aktivieren des Entwicklermodus
Standardmäßig installiert Surface Hub nur apps aus dem Microsoft Store. Um Apps, die von einer anderen Quelle signiert wurden, zu installieren, müssen Sie den Entwicklermodus aktivieren.

> [!NOTE]
> Nachdem der Entwicklermodus aktiviert wurde, müssen Sie den Surface Hub zurücksetzen, wenn Sie wieder zu deaktivieren möchten. Durch das Zurücksetzen des Geräts werden alle lokalen Benutzerdateien und die Konfiguration gelöscht, und anschließend wird Windows neu installiert.

1. Öffnen Sie im **Startmenü** des Surface Hub die Einstellungs-App.

   > [!NOTE]
   > Greifen Sie auf die Einstellungs-app auf Surface Hub sind Administratorrechte erforderlich.

2. Navigieren Sie zu **& Sicherheit \> für Entwickler zu aktualisieren**.

3. Wählen Sie **Entwicklermodus** aus, und akzeptieren Sie die Warnung.

### <a name="deploy-your-app-from-visual-studio"></a>Bereitstellen Ihrer App aus Visual Studio
Weitere Informationen zu den Bereitstellungsprozess im Allgemeinen finden Sie unter [Bereitstellen und Debuggen von UWP-apps](https://msdn.microsoft.com/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps).

   > [!NOTE]
   > Dieses Feature erfordert Visual Studio 2015 Update 1 oder höher, aber es wird empfohlen, dass Sie die neueste aktuelle Version von Visual Studio verwenden. Eine auf dem neuesten Stand Visual Studio-Instanz wird Sie alle neuesten Entwicklungen und Sicherheitsupdates gibe.

1. Zur Auswahl eines Ziels navigieren Sie zur Dropdownliste mit Debugzielen neben der Schaltfläche **Debugging starten** und wählen **Remotecomputer** aus.

    <!--lcap: in your screenshot, you have local machine selected-->

   ![Dropdownliste der Debugziele in Visual Studio](images/vs-debug-target.png)

2. Geben Sie die IP-Adresse des Surface Hub ein. Stellen Sie sicher, dass der Authentifizierungsmodus **Universell** ausgewählt ist.

   > [!TIP] 
   > Nachdem Sie den Entwicklermodus aktiviert haben, finden Sie den Surface Hub IP-Adresse auf der Willkommensseite angezeigt.

3. Wählen Sie zum Bereitstellen und Debuggen Sie Ihre app auf dem Surface Hub **Debugging starten (F5)** , oder drücken Sie STRG + F5, um nur die Bereitstellung Ihrer app auszuführen.

   > [!TIP]
   > Wenn Surface Hub auf die Willkommensseite angezeigt wird, können schließen Sie diesen durch Drücken einer beliebigen Schaltfläche.
