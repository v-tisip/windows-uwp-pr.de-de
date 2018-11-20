---
author: joannaleecy
title: Einzelhandel (RDX) Demo Features Ihrer app hinzufügen
description: Bereiten Sie Ihre app für den Einzelhandel Demo-Modus, der versehentlichen präsentieren Ihrer app auf die Einzelhandels-Vertriebsabteilung.
ms.assetid: f83f950f-7fdd-4f18-8127-b92a8f400061
ms.author: joanlee
ms.date: 10/02/2018
ms.topic: article
keywords: Windows 10, UWP, Demo-App für den Einzelhandel
ms.localizationpriority: medium
ms.openlocfilehash: ee0344d521b4c31449a2291517b20a09280818fc
ms.sourcegitcommit: cbe7cf620622a5e4df7414f9e38dfecec1cfca99
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "7420804"
---
# <a name="add-retail-demo-rdx-features-to-your-app"></a>Einzelhandel (RDX) Demo Features Ihrer app hinzufügen

Fügen Sie einen Retail Demo-Modus in Ihrer Windows-app, damit Kunden, die PCs und Geräte auf die Vertriebsabteilung testen sofort beginnen können.

Wenn Kunden im Einzelhandel sind, erwarten sie, dass Demos von Computern und Geräten testen können. Sie sind häufig einen erheblichen Teil der Zeit mit apps über den [Einzelhandel Demo auftreten (RDX-App)](https://docs.microsoft.com/windows-hardware/customize/desktop/retail-demo-experience).

Sie können Ihre app einrichten, unterschiedliche Funktionen bereitstellen, während Sie sich im _normalen_ oder _Einzelhandel_ Modi müssen. Z. B. Wenn Ihre app mit einem Setupprozess gestartet wird, können Sie im einzelhandelsmodus überspringen und die app mit Einstellungen für die Daten und standardmäßig vorab, damit sie sofort beginnen können.

Aus Sicht unserer Kunden gibt es nur eine app. Um zwischen den beiden Modi unterscheiden können, empfehlen wir, während Ihre app im einzelhandelsmodus ist, das Wort "Einzelhandel" anzeigt hervorgehobener Stelle in der Titelleiste oder an einer geeigneten Stelle.

Zusätzlich zu den Microsoft Store-Anforderungen für apps müssen RDX-fähige apps auch sein kompatibel mit der RDX-Setup, Bereinigung und Update-Prozesse, um sicherzustellen, dass Kunden ein Geschäft durchgehend positiv Erlebnis bei Geschäft haben.

## <a name="design-principles"></a>Designprinzipien

* **Optimale Präsentation**. Verwenden Sie die Demo-App, um Showcase Ihrer app großartig. Dies ist wahrscheinlich das erste Mal Ihr Kunde Ihre app so diese besten Seite angezeigt, die angezeigt wird.

* **Es schnell anzuzeigen**. Kunden können ungeduldig sein – je schneller ein Benutzer den Wert ihrer App erfasst, desto besser.

* **Einfache Demonstration**. Die Demo-App ist ein Elevator Pitch für den Wert Ihrer app.

* **Fokus auf die Erfahrung**. Geben Sie den Benutzern die Zeit, um Ihre Inhalte zu verdauen. Es ist zwar wichtig, dass die Benutzer schnell zum wichtigsten Teil gelangen, aber nur mithilfe entsprechender Pausen können sie den Wert der App richtig erkennen.

## <a name="technical-requirements"></a>Technische Anforderungen

Da RDX-fähige apps werden Ihrer App Kunden im Einzelhandel optimal präsentieren sollen, müssen technischen Anforderungen und Datenschutzrichtlinien in Bezug auf, die alle Retail Demo-apps für den Microsoft Store hat.

Dies kann als Prüfliste für die sich bei der Prüfung vorzubereiten und Klarheit in den Testprozess verwendet werden. Beachten Sie, dass diese Anforderungen nicht nur für den Prüfprozess, sondern für die gesamte Lebensdauer der Demo-App für den Einzelhandel (d.h. solange Ihre App auf den Vorführgeräten ausgeführt wird) eingehalten werden müssen.

### <a name="critical-requirements"></a>Kritische Anforderungen

RDX-fähige apps, die diese kritischen Anforderungen nicht erfüllen, werden so bald wie möglich von allen vorführgeräten entfernt werden.

* **Fragen Sie nicht nach personenbezogenen Informationen (PII)**. Dazu gehören Anmeldeinformationen oder Microsoft-Kontoinformationen, Kontakt Details.

* **Fehlerfrei auftreten**. Ihr App muss fehlerfrei funktionieren. Außerdem dürfen keine Fehler-Pop-ups oder -Benachrichtigungen angezeigt werden, wenn Kunden die Vorführgeräte verwenden. Fehler wider negativ auf die app selbst, Ihre Marke, des Geräts Marke, Hersteller des Geräts Marke und Microsoft Marke.

* **Kostenpflichtige apps müssen über einen Testmodus verfügen**. Ihre app muss entweder einen [Testmodus](https://msdn.microsoft.com/windows/uwp/monetize/exclude-or-limit-features-in-a-trial-version-of-your-app)einbeziehen oder ein kostenloses werden. Kunden, die sich in einem Laden etwas ansehen, möchten dafür nicht zahlen.

### <a name="high-priority-requirements"></a>Anforderungen mit hoher Priorität

RDX-fähige apps, die diese Anforderungen mit hoher Priorität nicht erfüllen müssen für ein Update sofort untersucht werden. Wenn eine umgehende Problembehebung nicht möglich ist, kann diese App von allen Vorführgeräten entfernt werden.

* **Memorable offline auftreten**. Ihre app muss eine tolle offline-Erfahrung zu bieten, da etwa 50 % der Geräte an einzelhandelsstandorten offline sind. Dadurch wird sichergestellt, dass das Erlebnis für die Kunden auch dann positiv ist, wenn sie offline mit Ihrer App interagieren.

* **Aktualisierte Content-Erfahrung**. Ihre app sollte nie für wird aktualisiert, sobald Sie online sein. Wenn Updates erforderlich sind, sollten sie im Hintergrund ausgeführt werden.

* **Keine anonyme Kommunikation**. Da ein Kunde ein Vorführgerät nutzen, anonyme Benutzer ist, sollte er nicht Nachricht oder Inhalte Freigeben des Geräts können.

* **Konsistentes Erlebnis mit den Bereinigungsprozess zu übermitteln**. Die Verwendung eines Vorführgeräts sollte für alle Kunden gleich sein. Ihre app sollte [Bereinigungsprozess](#clean-up-process) verwenden, um nach jeder Verwendung zum gleichen Standardzustand zurückkehrt wird. Wir möchten wir nicht den nächsten Kunden um festzustellen, welche die letzte Kunden. Dies umfasst z.B. Punktestände, Erfolge und aufgehobene Sperren.

* **Altersgerechte Inhalte**. Alle app-Inhalt muss Altersklasse oder eine jüngere zugewiesen. Weitere Informationen finden Sie unter [abrufen, die die app durch die IARC bewertet](https://www.globalratings.com/for-developers.aspx) und [ESRB-Bewertung](https://www.esrb.org/ratings/ratings_guide.aspx).

### <a name="medium-priority-requirements"></a>Anforderungen mit mittlerer Priorität

Das Windows-Team für den Einzelhandel setzt sich unter Umständen direkt mit Entwicklern in Verbindung, um mit ihnen zu besprechen, wie diese Probleme behoben werden können.

* **Möglichkeit, nicht erfolgreich über eine Vielzahl von Geräten ausgeführt werden**. Apps müssen auf allen Geräten, einschließlich Geräten mit Low-End-Spezifikationen ausgeführt werden. Wenn die app auf Geräten, die die Mindestanforderungen nicht erfüllt installiert ist, muss die app den Benutzer dazu deutlich zu informieren. Die Mindestgeräteanforderungen müssen bekanntgegeben werden, damit die App immer mit höchster Leistung ausgeführt werden kann.

* **Erfüllen der größenanforderungen für Einzelhandel**. Die App darf eine Größe von 800MB nicht übersteigen. Wenden Sie sich an das Windows-Einzelhandel-Team direkt weiteren Erläuterung Wenn RDX-fähige app die größenanforderungen nicht entspricht.

## <a name="retailinfo-api-preparing-your-code-for-demo-mode"></a>RetailInfo API: Vorbereiten von Ihrem Code für Demo-Modus

### <a name="isdemomodeenabled"></a>IsDemoModeEnabled
Die Eigenschaft [**IsDemoModeEnabled**](https://docs.microsoft.com/uwp/api/windows.system.profile.retailinfo.isdemomodeenabled) in die [**RetailInfo**](https://docs.microsoft.com/uwp/api/Windows.System.Profile.RetailInfo) Utility-Klasse, die Teil des [Windows.System.Profile](https://docs.microsoft.com/uwp/api/windows.system.profile) Namespaces in Windows 10 SDK ist, wird als einen booleschen Indikator verwendet, um die angeben, welcher Codepfad Ihrer app ausgeführt wird – die normale _ _oder den _Einzelhandel_ Modus.

``` csharp
using Windows.Storage;

StorageFolder folder = ApplicationData.Current.LocalFolder;

if (Windows.System.Profile.RetailInfo.IsDemoModeEnabled) 
{
    // Use the demo specific directory
    folder = await folder.GetFolderAsync(“demo”);
}

StorageFile file = await folder.GetFileAsync(“hello.txt”);
// Now read from file
```

``` cpp
using namespace Windows::Storage;

StorageFolder^ localFolder = ApplicationData::Current->LocalFolder;

if (Windows::System::Profile::RetailInfo::IsDemoModeEnabled) 
{
    // Use the demo specific directory
    create_task(localFolder->GetFolderAsync(“demo”).then([this](StorageFolder^ demoFolder)
    {
        return demoFolder->GetFileAsync(“hello.txt”);
    }).then([this](task<StorageFile^> fileTask)
    {
        StorageFile^ file = fileTask.get();
    });
    // Do something with file
}
else
{
    create_task(localFolder->GetFileAsync(“hello.txt”).then([this](StorageFile^ file)
    {
        // Do something with file
    });
}
```

``` javascript
if (Windows.System.Profile.retailInfo.isDemoModeEnabled) {
    console.log(“Retail mode is enabled.”);
} else {
    Console.log(“Retail mode is not enabled.”);
}
```

### <a name="retailinfoproperties"></a>RetailInfo.Properties

Wenn [**IsDemoModeEnabled**](https://docs.microsoft.com/uwp/api/windows.system.profile.retailinfo.isdemomodeenabled) „true“ zurückgibt, können Sie mithilfe von [**RetailInfo.Properties**](https://docs.microsoft.com/uwp/api/windows.system.profile.retailinfo.properties) einen Satz von Eigenschaften zum Gerät abfragen, um eine besser angepasste Verwendung der Demo-App zu ermöglichen. Diese Eigenschaften umfassen [**ManufacturerName**](https://docs.microsoft.com/uwp/api/windows.system.profile.knownretailinfoproperties.manufacturername), [**Screensize**](https://docs.microsoft.com/uwp/api/windows.system.profile.knownretailinfoproperties.screensize), [**Memory**](https://docs.microsoft.com/uwp/api/windows.system.profile.knownretailinfoproperties.memory) usw.

```csharp
using Windows.UI.Xaml.Controls;
using Windows.System.Profile

TextBlock priceText = new TextBlock();
priceText.Text = RetailInfo.Properties[KnownRetailInfo.Price];
// Assume infoPanel is a StackPanel declared in XAML
this.infoPanel.Children.Add(priceText);
```

```cpp
using namespace Windows::UI::Xaml::Controls;
using namespace Windows::System::Profile;

TextBlock ^manufacturerText = ref new TextBlock();
manufacturerText.set_Text(RetailInfo::Properties[KnownRetailInfoProperties::Price]);
// Assume infoPanel is a StackPanel declared in XAML
this->infoPanel->Children->Add(manufacturerText);
```

```javascript
var pro = Windows.System.Profile;
console.log(pro.retailInfo.properties[pro.KnownRetailInfoProperties.price);
```

#### <a name="idl"></a>IDL

```
//  Copyright (c) Microsoft Corporation. All rights reserved.
//
//  WindowsRuntimeAPISet

import "oaidl.idl";
import "inspectable.idl";
import "Windows.Foundation.idl";
#include <sdkddkver.h>

namespace Windows.System.Profile
{
    runtimeclass RetailInfo;
    runtimeclass KnownRetailInfoProperties;

    [version(NTDDI_WINTHRESHOLD), uuid(0712C6B8-8B92-4F2A-8499-031F1798D6EF), exclusiveto(RetailInfo)]
    [version(NTDDI_WINTHRESHOLD, Platform.WindowsPhone)]
    interface IRetailInfoStatics : IInspectable
    {
        [propget] HRESULT IsDemoModeEnabled([out, retval] boolean *value);
        [propget] HRESULT Properties([out, retval, hasvariant] Windows.Foundation.Collections.IMapView<HSTRING, IInspectable *> **value);
    }

    [version(NTDDI_WINTHRESHOLD), uuid(50BA207B-33C4-4A5C-AD8A-CD39F0A9C2E9), exclusiveto(KnownRetailInfoProperties)]
    [version(NTDDI_WINTHRESHOLD, Platform.WindowsPhone)]
    interface IKnownRetailInfoPropertiesStatics : IInspectable
    {
        [propget] HRESULT RetailAccessCode([out, retval] HSTRING *value);
        [propget] HRESULT ManufacturerName([out, retval] HSTRING *value);
        [propget] HRESULT ModelName([out, retval] HSTRING *value);
        [propget] HRESULT DisplayModelName([out, retval] HSTRING *value);
        [propget] HRESULT Price([out, retval] HSTRING *value);
        [propget] HRESULT IsFeatured([out, retval] HSTRING *value);
        [propget] HRESULT FormFactor([out, retval] HSTRING *value);
        [propget] HRESULT ScreenSize([out, retval] HSTRING *value);
        [propget] HRESULT Weight([out, retval] HSTRING *value);
        [propget] HRESULT DisplayDescription([out, retval] HSTRING *value);
        [propget] HRESULT BatteryLifeDescription([out, retval] HSTRING *value);
        [propget] HRESULT ProcessorDescription([out, retval] HSTRING *value);
        [propget] HRESULT Memory([out, retval] HSTRING *value);
        [propget] HRESULT StorageDescription([out, retval] HSTRING *value);
        [propget] HRESULT GraphicsDescription([out, retval] HSTRING *value);
        [propget] HRESULT FrontCameraDescription([out, retval] HSTRING *value);
        [propget] HRESULT RearCameraDescription([out, retval] HSTRING *value);
        [propget] HRESULT HasNfc([out, retval] HSTRING *value);
        [propget] HRESULT HasSdSlot([out, retval] HSTRING *value);
        [propget] HRESULT HasOpticalDrive([out, retval] HSTRING *value);
        [propget] HRESULT IsOfficeInstalled([out, retval] HSTRING *value);
        [propget] HRESULT WindowsVersion([out, retval] HSTRING *value);
    }

    [version(NTDDI_WINTHRESHOLD), static(IRetailInfoStatics, NTDDI_WINTHRESHOLD)]
    [version(NTDDI_WINTHRESHOLD, Platform.WindowsPhone), static(IRetailInfoStatics, NTDDI_WINTHRESHOLD, Platform.WindowsPhone)]
    [threading(both)]
    [marshaling_behavior(agile)]
    runtimeclass RetailInfo
    {
    }

    [version(NTDDI_WINTHRESHOLD), static(IKnownRetailInfoPropertiesStatics, NTDDI_WINTHRESHOLD)]
    [version(NTDDI_WINTHRESHOLD, Platform.WindowsPhone), static(IKnownRetailInfoPropertiesStatics, NTDDI_WINTHRESHOLD, Platform.WindowsPhone)]
    [threading(both)]
    [marshaling_behavior(agile)]
    runtimeclass KnownRetailInfoProperties
    {
    }
}
```

## <a name="cleanup-process"></a>Bereinigungsprozess

Bereinigung beginnt mit zwei Minuten nach dem ein Käufer beendet wird, interagiert mit dem Gerät. Die Retail Demo wiedergegeben wird, und Windows beginnt das Zurücksetzen Beispieldaten in die Kontakte, Fotos und anderen apps. Je nach Gerät kann dies zwischen 1 bis 5 Minuten vollständig alles wieder auf die normale zurücksetzen dauern. Dadurch wird sichergestellt, dass jeder Kunde im Geschäft kann auf einem Gerät gleich und die gleiche Erfahrung bei der Interaktion mit dem Gerät.

Schritt 1: Bereinigen
* Alle Win32- und Store-Apps werden geschlossen.
* Alle Dateien in bekannten Ordnern wie __Bilder__, __Videos__, __Musik__, __Dokumente__, __SavedPictures__, __CameraRoll__, __Desktop__ und __Downloads__ Ordner werden gelöscht.
* Unstrukturierte und strukturierte Roamingzustände werden gelöscht.
* Strukturierte lokale Zustände werden gelöscht.

Schritt 2: Einrichten
* Offlinegeräte: Ordner bleiben leer
* Onlinegeräte: Demoressourcen für den Einzelhandel können vom Microsoft Store per Push an das Gerät übertragen werden.

### <a name="store-data-across-user-sessions"></a>Speichern von Daten auf benutzersitzungen

Zum Speichern von Daten sitzungsübergreifend Benutzer können Sie Informationen in __ApplicationData.Current.TemporaryFolder__ speichern, wie Daten in diesem Ordner mit der Standard-Cleanup-Prozess nicht automatisch gelöscht. Beachten Sie, dass mit *LocalState* gespeicherten Informationen während der Bereinigungsprozess gelöscht wird.

### <a name="customize-the-cleanup-process"></a>Den Bereinigungsprozess anpassen

Um den Bereinigungsprozess anzupassen, Implementieren der `Microsoft-RetailDemo-Cleanup` app-Dienst in Ihrer app.

Szenarien, in denen eine benutzerdefinierte Bereinigungslogik erforderlich ist, umfassen das Ausführen einer umfassenden Einrichtung, das Herunterladen und Zwischenspeichern von Daten oder nicht *LocalState* Daten gelöscht werden sollen.

Schritt 1: Deklarieren Sie die _Microsoft-RetailDemo-Cleanup_ -Dienst im app-Manifest.
``` CSharp
  <Applications>
      <Extensions>
        <uap:Extension Category="windows.appService" EntryPoint="MyCompany.MyApp.RDXCustomCleanupTask">
          <uap:AppService Name="Microsoft-RetailDemo-Cleanup" />
        </uap:Extension>
      </Extensions>
   </Application>
  </Applications>

```

Schritt 2: Implementieren der benutzerdefinierten Bereinigungslogik unter der _AppdataCleanup_ -Funktion mithilfe der folgenden Beispielvorlage.
``` CSharp
using System;
using System.IO;
using System.Runtime.Serialization.Json;
using System.Threading;
using System.Threading.Tasks;
using Windows.ApplicationModel.AppService;
using Windows.ApplicationModel.Background;
using Windows.Foundation.Collections;
using Windows.Storage;

namespace MyCompany.MyApp
{
    public sealed class RDXCustomCleanupTask : IBackgroundTask
    {
        BackgroundTaskCancellationReason _cancelReason = BackgroundTaskCancellationReason.Abort;
        BackgroundTaskDeferral _deferral = null;
        IBackgroundTaskInstance _taskInstance = null;
        AppServiceConnection _appServiceConnection = null;

        const string MessageCommand = "Command";

        public void Run(IBackgroundTaskInstance taskInstance)
        {
            // Get the deferral object from the task instance, and take a reference to the taskInstance;
            _deferral = taskInstance.GetDeferral();
            _taskInstance = taskInstance;
            _taskInstance.Canceled += new BackgroundTaskCanceledEventHandler(OnCanceled);

            AppServiceTriggerDetails appService = _taskInstance.TriggerDetails as AppServiceTriggerDetails;
            if ((appService != null) && (appService.Name == "Microsoft-RetailDemo-Cleanup"))
            {
                _appServiceConnection = appService.AppServiceConnection;
                _appServiceConnection.RequestReceived += _appServiceConnection_RequestReceived;
                _appServiceConnection.ServiceClosed += _appServiceConnection_ServiceClosed;
            }
            else
            {
                _deferral.Complete();
            }
        }

        void _appServiceConnection_ServiceClosed(AppServiceConnection sender, AppServiceClosedEventArgs args)
        {
        }

        async void _appServiceConnection_RequestReceived(AppServiceConnection sender, AppServiceRequestReceivedEventArgs args)
        {
            //Get a deferral because we will be calling async code
            AppServiceDeferral requestDeferral = args.GetDeferral();
            string command = null;
            var returnData = new ValueSet();

            try
            {
                ValueSet message = args.Request.Message;
                if (message.ContainsKey(MessageCommand))
                {
                    command = message[MessageCommand] as string;
                }

                if (command != null)
                {
                    switch (command)
                    {
                        case "AppdataCleanup":
                            {
                                // Do custom clean up logic here
                                break;
                            }
                    }
                }
            }
            catch (Exception e)
            {
            }
            finally
            {
                requestDeferral.Complete();
                // Also release the task deferral since we only process one request per instance.
                _deferral.Complete();
            }
        }

        private void OnCanceled(IBackgroundTaskInstance sender, BackgroundTaskCancellationReason reason)
        {
            _cancelReason = reason;
        }
    }
}
```

## <a name="related-links"></a>Verwandte Links

* [Speichern und Abrufen von App-Daten](https://msdn.microsoft.com/windows/uwp/app-settings/store-and-retrieve-app-data)
* [Erstellen und Nutzen eines App-Diensts](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)
* [Lokalisieren von App-Inhalten](https://msdn.microsoft.com/windows/uwp/globalizing/globalizing-portal)
* [Demo-App (RDX-App)](https://docs.microsoft.com/windows-hardware/customize/desktop/retail-demo-experience)
