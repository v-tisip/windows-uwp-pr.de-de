---
description: Code, der in das Gerät selbst integriert und auf dessen Sensoren abgestimmt ist, umfasst auch Eingaben vom und Ausgaben an den Benutzer.
title: Portieren von WindowsPhone Silverlight zu UWP für e/a, Gerät und app-Modell "
ms.assetid: bf9f2c03-12c1-49e4-934b-e3fa98919c53
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 6ef1814443b3831e514eafb3f5a0c58b7703126b
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8730981"
---
#  <a name="porting-windowsphone-silverlight-to-uwp-for-io-device-and-app-model"></a>Portieren von WindowsPhone Silverlight zu UWP für e/a, Gerät und app-Modell


Im vorherigen Thema ging es um das [Portieren von XAML und UI](wpsl-to-uwp-porting-xaml-and-ui.md).

Code, der in das Gerät selbst integriert und auf dessen Sensoren abgestimmt ist, umfasst auch Eingaben vom und Ausgaben an den Benutzer. Auch die Datenverarbeitung kann einbezogen werden. Aber dieser Code wird in der Regel nicht als UI-Ebene oder Datenebene betrachtet. Dieser Code enthält die Integration in Vibrationscontroller, Beschleunigungsmesser, Gyroskop, Mikrofon und Lautsprecher (überschneiden sich mit Spracherkennung und Sprachsynthese), (geografischen) Standort und Eingabemodalitäten, z.B. Touch, Maus, Tastatur und Stift.

## <a name="application-lifecycle-process-lifetime-management"></a>App-Lebenszyklus (Prozesslebensdauer-Verwaltung)

Ihre WindowsPhone Silverlight-app enthält Code zum Speichern und Wiederherstellen des App-Zustands und Anzeigemodus, um die Markierung als veraltet und anschließende erneute Aktivierung zu unterstützen. App-Lebenszyklus von universellen Windows-Plattform (UWP) apps weist starke parallelen mit der WindowsPhone Silverlight-apps, da beide mit dem gleichen Ziel zur Maximierung der verfügbaren Ressourcen entworfen werden unabhängig vom gewählten App der Benutzer ausgewählt hat, dass in der Vordergrund zu jedem Zeitpunkt. Sie werden feststellen, dass Ihr Code sich dem neuen System recht problemlos anpasst.

**Hinweis:**  eine WindowsPhone Silverlight-app durch Drücken der **zurück** -Hardwaretaste automatisch beendet. Eine UWP-App wird durch Drücken der Hardwaretaste **Zurück** auf einem Mobilgerät dagegen *nicht* automatisch beendet. Stattdessen wird sie erst angehalten und dann ggf. beendet. Diese Details sind für eine App, die entsprechend auf App-Lebenszyklusereignisse reagiert, jedoch transparent.

Ein so genanntes „Entprellfenster“ ist der Zeitraum von der Deaktivierung der App bis zum Auslösen des Anhalteereignisses durch das System. Für eine UWP-App gibt es kein Entprellfenster. Das Anhalteereignis wird ausgelöst, sobald eine App inaktiv wird.

Weitere Informationen finden Sie unter [App-Lebenszyklus](https://msdn.microsoft.com/library/windows/apps/mt243287).

## <a name="camera"></a>Kamera

Code WindowsPhone Silverlight-kameraaufnahme wird die Klassen **Microsoft.Devices.Camera**, **Microsoft.Devices.PhotoCamera**oder **Microsoft.Phone.Tasks.CameraCaptureTask** verwendet. Zum Portieren dieses Codes zur universellen Windows-Plattform (UWP) können Sie die [**MediaCapture**](https://msdn.microsoft.com/library/windows/apps/br241124)-Klasse verwenden. Ein Codebeispiel finden Sie im Thema [**CapturePhotoToStorageFileAsync**](https://msdn.microsoft.com/library/windows/apps/hh700836). Diese Methode ermöglicht es Ihnen, ein Foto in einer Speicherdatei aufnehmen und erfordert das **Mikrofon** und **Webcam**[**Gerätefunktionen**](https://msdn.microsoft.com/library/windows/apps/dn934747) in der app-Paketmanifest festgelegt werden.

Eine weitere Möglichkeit ist die [**"cameracaptureui"**](https://msdn.microsoft.com/library/windows/apps/br241030) -Klasse, die auch die **Mikrofon** und **Webcam**[**Gerätefunktionen**](https://msdn.microsoft.com/library/windows/apps/dn934747)erfordert.

Foto-Apps werden für UWP-Apps nicht unterstützt.

## <a name="detecting-the-platform-your-app-is-running-on"></a>Erkennen der Plattform, auf der Ihre App ausgeführt wird

Die Möglichkeit für die Herangehensweise Ausrichtung von Apps ändert sich mit Windows 10. Das neue konzeptionelle Modell besteht darin, dass eine App auf die Universelle Windows-Plattform (UWP) ausgerichtet ist und auf allen Windows-Geräten ausgeführt wird. Dann besteht die Möglichkeit, Funktionen hervorzuheben, die exklusiv für bestimmte Gerätefamilien angeboten werden. Bei Bedarf besteht auch die Möglichkeit, die App auf eine oder mehrere bestimmte Gerätefamilien zu beschränken. Weitere Informationen zu Gerätefamilien – und wie Sie entscheiden, auf welche Sie eine App ausrichten sollten – finden Sie unter [Anleitung für UWP-Apps](https://msdn.microsoft.com/library/windows/apps/dn894631).

**Hinweis:**  empfohlen, dass Sie nicht Betriebssystem oder die Gerätefamilie zum Ermitteln des Vorhandenseins von Features zu. Das Identifizieren des aktuellen Betriebssystems oder der Gerätefamilie ist in der Regel nicht die beste Möglichkeit, um festzustellen, ob ein bestimmtes Feature für das Betriebssystem oder die Gerätefamilie vorhanden ist. Anstatt das Betriebssystem oder die Gerätefamilie (und Versionsnummer) zu ermitteln, sollten Sie das Vorhandensein des Features selbst überprüfen (siehe [Bedingte Kompilierung und adaptiver Code](wpsl-to-uwp-porting-to-a-uwp-project.md)). Wenn ein bestimmtes Betriebssystem oder eine bestimmte Gerätefamilie erforderlich ist, sollten Sie darauf achten, es bzw. sie als unterstützte Mindestversion zu verwenden, anstatt den Test nur für diese Version zu entwerfen.

Zum Anpassen der Benutzeroberfläche Ihrer App für verschiedene Geräte gibt es mehrere empfohlene Möglichkeiten. Verwenden Sie weiterhin Elemente mit automatischer Größenanpassung und dynamische Layoutbereiche. Verwenden Sie in Ihrem XAML-Markup weiterhin Größen in der Einheit „effektive Pixel“ (früher „Anzeigepixel“), damit sich die Benutzeroberfläche an verschiedene Auflösungen und Skalierungsfaktoren anpasst (siehe [Anzeigepixel/Effektive Pixel, Abstand zum Bildschirm und Skalierungsfaktoren](wpsl-to-uwp-porting-xaml-and-ui.md)). Verwenden Sie außerdem die adaptiven Auslöser und Setter des Visual State-Managers zum Anpassen der Benutzeroberfläche an die Fenstergröße (siehe [Anleitung für UWP-Apps](https://msdn.microsoft.com/library/windows/apps/dn894631)).

Bei einem Szenario, in dem das Erkennen der Gerätefamilie unvermeidbar ist, können Sie so vorgehen. In diesem Beispiel verwenden wir die [**AnalyticsVersionInfo**](https://msdn.microsoft.com/library/windows/apps/dn960165)-Klasse, um zu einer für die jeweilige Mobilgerätefamilie angepassten Seite zu navigieren – falls diese vorhanden ist – und wir stellen sicher, dass andernfalls eine Umleitung auf eine Standardseite erfolgt.

```csharp
   if (Windows.System.Profile.AnalyticsInfo.VersionInfo.DeviceFamily == "Windows.Mobile")
        rootFrame.Navigate(typeof(MainPageMobile), e.Arguments);
    else
        rootFrame.Navigate(typeof(MainPage), e.Arguments);
```

Ihre App kann auch anhand der aktiven Ressourcenauswahlfaktoren die Gerätefamilie ermitteln, auf der sie ausgeführt wird. Im folgenden Beispiel wird gezeigt, wie dies imperativ durchgeführt wird, und im Thema [**ResourceContext.QualifierValues**](https://msdn.microsoft.com/library/windows/apps/br206071) wird der gängigere Anwendungsfall für die Klasse beim Laden der gerätefamilienspezifischen Ressourcen basierend auf dem Gerätefamilienfaktor beschrieben.

```csharp
var qualifiers = Windows.ApplicationModel.Resources.Core.ResourceContext.GetForCurrentView().QualifierValues;
string deviceFamilyName;
bool isDeviceFamilyNameKnown = qualifiers.TryGetValue("DeviceFamily", out deviceFamilyName);
```

Siehe auch [Bedingte Kompilierung und adaptiver Code](wpsl-to-uwp-porting-to-a-uwp-project.md).

## <a name="device-status"></a>Gerätestatus

Eine WindowsPhone Silverlight-app können die **Microsoft.Phone.Info.DeviceStatus** -Klasse zum Abrufen von Informationen über das Gerät auf dem die app ausgeführt wird. Es gibt kein direktes UWP-Äquivalent für den **Microsoft.Phone.Info**-Namespace. Sie finden hier aber einige Eigenschaften und Ereignisse, die Sie in einer UWP-App verwenden können, anstatt die Member der **DeviceStatus-Klasse** aufzurufen.

| Windows Phone Silverlight                                                               | UWP                                                                                                                                                                                                                                                                                                                                |
|-----------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **ApplicationCurrentMemoryUsage**-Eigenschaft und **ApplicationCurrentMemoryUsageLimit**-Eigenschaft | [**MemoryManager.AppMemoryUsage**](https://msdn.microsoft.com/library/windows/apps/dn633832)-Eigenschaft und [**AppMemoryUsageLimit**](https://msdn.microsoft.com/library/windows/apps/dn633836)-Eigenschaft                                                                                                                                    |
| **ApplicationPeakMemoryUsage**-Eigenschaft                                                 | Verwenden Sie das Tool zur Erstellung von Arbeitsspeicherprofilen in Visual Studio. Weitere Informationen finden Sie unter [Analysieren der Speicherauslastung](http://msdn.microsoft.com/library/windows/apps/dn645469.aspx).                                                                                                                                                                          |
| **DeviceFirmwareVersion**-Eigenschaft                                                      | [**EasClientDeviceInformation.SystemFirmwareVersion**](https://msdn.microsoft.com/library/windows/apps/dn608144)-Eigenschaft (nur Familie der Desktopgeräte)                                                                                                                                                                             |
| **DeviceHardwareVersion**-Eigenschaft                                                      | [**EasClientDeviceInformation.SystemHardwareVersion**](https://msdn.microsoft.com/library/windows/apps/dn608145)-Eigenschaft (nur Familie der Desktopgeräte)                                                                                                                                                                             |
| **DeviceManufacturer**-Eigenschaft                                                         | [**EasClientDeviceInformation.SystemManufacturer**](https://msdn.microsoft.com/library/windows/apps/hh701398)-Eigenschaft (nur Familie der Desktopgeräte)                                                                                                                                                                                |
| **DeviceName**-Eigenschaft                                                                 | [**EasClientDeviceInformation.SystemProductName**](https://msdn.microsoft.com/library/windows/apps/hh701401)-Eigenschaft (nur Familie der Desktopgeräte)                                                                                                                                                                                 |
| **DeviceTotalMemory**-Eigenschaft                                                          | Kein Äquivalent                                                                                                                                                                                                                                                                                                                      |
| **IsKeyboardDeployed**-Eigenschaft                                                         | Kein Äquivalent. Diese Eigenschaft enthält Infos zu Hardwaretastaturen für Mobilgeräte, die nur selten verwendet werden.                                                                                                                                                                                                        |
| **IsKeyboardPresent**-Eigenschaft                                                          | Kein Äquivalent. Diese Eigenschaft enthält Infos zu Hardwaretastaturen für Mobilgeräte, die nur selten verwendet werden.                                                                                                                                                                                                        |
| **KeyboardDeployedChanged**-Ereignis                                                       | Kein Äquivalent. Diese Eigenschaft enthält Infos zu Hardwaretastaturen für Mobilgeräte, die nur selten verwendet werden.                                                                                                                                                                                                        |
| **PowerSource**-Eigenschaft                                                                | Kein Äquivalent                                                                                                                                                                                                                                                                                                                      |
| **PowerSourceChanged**-Ereignis                                                            | Behandeln Sie das [**RemainingChargePercentChanged**](https://msdn.microsoft.com/library/windows/apps/jj207240)-Ereignis (nur Familie der Mobilgeräte). Das Ereignis wird ausgelöst, wenn der Wert der [**RemainingChargePercent**](https://msdn.microsoft.com/library/windows/apps/jj207239)-Eigenschaft (nur Familie der Mobilgeräte) um 1% verkleinert wird. |

## <a name="location"></a>Position

Wenn eine app, die in der app-Paketmanifest die positionsfunktion deklariert unter Windows 10 ausgeführt wird, fordert das System die Zustimmung des Endbenutzers. Falls in Ihrer App eine eigene benutzerdefinierte Aufforderung zur Zustimmung oder eine Schaltfläche zum Aktivieren/Deaktivieren angezeigt wird, sollten Sie sie entfernen, damit Endbenutzer nur eine Aufforderung erhalten.

## <a name="orientation"></a>Ausrichtung

Die Entsprechung der UWP-App für die Eigenschaften **PhoneApplicationPage.SupportedOrientations** und **Orientation** ist das [**uap:InitialRotationPreference**](https://msdn.microsoft.com/library/windows/apps/dn934798)-Element im App-Paketmanifest. Wählen Sie die Registerkarte **Anwendung** aus, falls sie nicht bereits ausgewählt wurde, und aktivieren Sie unter **Unterstützte Drehungen** ein oder mehrere Kontrollkästchen, um Ihre Präferenzen anzugeben.

Sie können die Benutzeroberfläche Ihrer UWP-App aber beliebig ausrichten, damit sie unabhängig von Geräteausrichtung und Bildschirmgröße gut aussieht. Mehr dazu finden Sie im folgenden Thema [Portieren für Formfaktor und Benutzerfreundlichkeit](wpsl-to-uwp-form-factors-and-ux.md).

Das nächste Thema lautet [Portieren von Unternehmen und Datenebenen](wpsl-to-uwp-business-and-data.md).

