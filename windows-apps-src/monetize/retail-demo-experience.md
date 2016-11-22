---
author: joannaleecy
title: "Erstellen einer Demo-App für den Einzelhandel"
description: "Erstellen Sie eine Demo-App für den Einzelhandel (RDX, Retail Demo Experience). Dies ist eine App, die sowohl im Einzelhandels-Demomodus als auch im Normalmodus gestartet werden kann."
ms.assetid: f83f950f-7fdd-4f18-8127-b92a8f400061
translationtype: Human Translation
ms.sourcegitcommit: 0110cec1857aac519f8e7c1490e5b3a0d8be9ea2
ms.openlocfilehash: 7a5367ae13be60be6e5b0ee4f62190f8b3330c59

---
#  Erstellen einer Demo-App für den Einzelhandel (RDX-App)

Wenn Kunden einen Laden betreten, erwarten sie, dass sie dort die neuesten PCs und Mobiltelefone vorfinden. Diese Geräte sind speziell für die Vorführung im Einzelhandel bestimmt. Solche Vorführgeräte und die darauf installierten Inhalte sind zu großen Teilen für das Kundenerlebnis im Geschäft verantwortlich, da Kunden häufig viel Zeit damit verbringen, diese Geräte auszuprobieren.

Auf diesen PCs und Mobiltelefonen in den Einzelhandelsgeschäften muss eine Demo-App für den Einzelhandel (RDX-App) installiert sein. In diesem Artikel finden Sie Informationen zum Entwickeln und Gestalten einer Einzelhandels-Demoversion Ihrer App, die auf PCs und mobilen Demogeräten im Einzelhandel installiert wird.

Eine Demo-App für den Einzelhandel umfasst einen einzelnen Build, der in zwei verschiedenen Modi gestartet werden kann: im _Normalmodus_ oder im _Einzelhandelsmodus_. Aus Sicht unserer Kunden gibt es nur eine App. Damit sie zwischen den beiden Versionen unterscheiden können, empfiehlt es sich, dass die im Einzelhandelsmodus ausgeführte App in der Titelleiste oder an einer anderen entsprechenden Stelle gut sichtbar das Wort „Einzelhandel“ anzeigt.

Zusätzlich zu den Store-Anforderungen für Apps müssen RDX-Apps auch vollständig mit dem Einrichtungs-, Bereinigungs- und Aktualisierungssystem der Vorführgeräte kompatibel sein, damit die Erfahrung der Kunden im Geschäft durchgehend positiv ist.

## Designprinzipien

### Optimale Präsentation

Verwenden Sie die Demo-App, um zu zeigen, was an Ihrer Anwendung so großartig ist.  Wahrscheinlich ist dies das erste Mal, dass die Kunden Ihre Anwendung sehen, präsentieren Sie sie also von ihrer besten Seite.
    
### Schnelle Vorführung

Kunden können ungeduldig sein – je schneller ein Benutzer den Wert ihrer App erfasst, desto besser. 
    
### Einfache Demonstration
    
Die Demo-App ist ein Elevator Pitch für den Wert Ihrer App.
    
### Das Erlebnis in den Mittelpunkt stellen

Geben Sie den Benutzern die Zeit, um Ihre Inhalte zu verdauen.  Es ist zwar wichtig, dass die Benutzer schnell zum wichtigsten Teil gelangen, aber nur mithilfe entsprechender Pausen können sie den Wert der App richtig erkennen.

## Technische Anforderungen

Da Demo-Apps den Kunden im Einzelhandel Ihre App optimal präsentieren sollen, ist es wichtig, dass die technischen Anforderungen und Datenschutzrichtlinien des Stores in Bezug auf Demo-Apps für den Einzelhandel eingehalten werden.
Dies kann auch als Checkliste in Vorbereitung auf den Prüfprozess verwendet werden und für Klarheit beim Testen sorgen. Beachten Sie, dass diese Anforderungen nicht nur für den Prüfprozess, sondern für die gesamte Lebensdauer der Demo-App für den Einzelhandel (d.h. solange Ihre App auf den Vorführgeräten ausgeführt wird) eingehalten werden müssen.

### Kritische Anforderungen
   
RDX-Apps, die diese kritischen Anforderungen nicht erfüllen, werden umgehend von allen Vorführgeräten entfernt.

* Kein Anfordern personenbezogener Informationen

    Die App darf Kunden nicht nach personenbezogenen Informationen fragen.  Dies umfasst Microsoft-Kontoinformationen, Kontaktdetails usw.
    
* Fehlerfreie Ausführung

    Ihr App muss fehlerfrei funktionieren. Außerdem dürfen keine Fehler-Pop-ups oder -Benachrichtigungen angezeigt werden, wenn Kunden die Vorführgeräte verwenden. Dies ist wichtig, da wir uns den Kunden von unserer besten Seite zeigen möchten – und diese muss fehlerfrei sein. 
    Zudem werfen Fehler ein schlechtes Licht auf die App, Ihr Unternehmen, das Gerät, auf dem die App ausgeführt wird, den Gerätehersteller und Microsoft selbst.
    
* Testmodus für kostenpflichtige Apps

    Damit Apps auf Vorführgeräten installiert werden können, müssen sie entweder kostenlos sein oder über einen Testmodus verfügen.  Kunden, die sich in einem Laden etwas ansehen, möchten dafür nicht zahlen. Weitere Informationen finden Sie unter [Ausschließen oder Einschränken von Features in einer Testversion](https://msdn.microsoft.com/windows/uwp/monetize/exclude-or-limit-features-in-a-trial-version-of-your-app).

### Anforderungen mit hoher Priorität
    
Bei RDX-Apps, die diese Anforderungen mit hoher Priorität nicht erfüllen, muss sofort untersucht werden, wie das Problem behoben werden kann. Wenn eine umgehende Problembehebung nicht möglich ist, kann diese App von allen Vorführgeräten entfernt werden.

* Einprägsame Offline-Erfahrung

    Ihre Demo-App für den Einzelhandel muss eine tolle Offline-Erfahrung bieten, da etwa 50% der Geräte an Einzelhandelsstandorten offline sind. Dadurch wird sichergestellt, dass das Erlebnis für die Kunden auch dann positiv ist, wenn sie offline mit Ihrer App interagieren.
    
* Aktualisierte Content-Erfahrung

    Damit die Kunden einen guten Eindruck von Ihrer App erhalten, muss diese immer aktuell sein, und Kunden sollten nicht aufgefordert werden, Aktualisierungen durchzuführen, wenn die App online ist.
        
* Keine anonyme Kommunikation

    Da Kunden, die ein Vorführgerät nutzen, anonyme Benutzer sind, dürfen sie über das Gerät keine Nachrichten versenden oder Inhalte freigeben.
    
* Bereitstellen einer einheitlichen Benutzererfahrung mithilfe des Bereinigungsprozesses

    Die Verwendung eines Vorführgeräts sollte für alle Kunden gleich sein. Verwenden Sie daher den [Bereinigungsprozess](#clean-up-process) für Ihre App, damit diese nach jeder Verwendung zum gleichen Standardzustand zurückkehrt. So wird Kunden nicht angezeigt, was die vorherigen Kunden ausgeführt haben.  Dies umfasst z.B. Punktestände, Erfolge und aufgehobene Sperren.
    
* Altersgerechte Inhalte

    Alle Inhalte von Demo-Apps für den Einzelhandel müssen für Jugendliche oder eine jüngere Altersklasse freigegeben sein. Weitere Informationen finden Sie unter [Einstufung Ihrer App durch die IARC](https://www.globalratings.com/for-developers.aspx) und [ESRB-Bewertung](https://www.esrb.org/ratings/ratings_guide.aspx).
    
### Anforderungen mit mittlerer Priorität

Das Windows-Team für den Einzelhandel setzt sich unter Umständen direkt mit Entwicklern in Verbindung, um mit ihnen zu besprechen, wie diese Probleme behoben werden können.

* Möglichkeit zur Ausführung auf verschiedenen Geräten

    Demo-Apps für den Einzelhandel müssen auf allen Geräten (einschließlich leistungsschwächeren Geräten) problemlos ausgeführt werden können. Wenn die Demo-App für den Einzelhandel auf Geräten installiert wird, die die Mindestspezifikationen zum Ausführen der App nicht erfüllt, müssen die Benutzer klar darauf hingewiesen werden. Die Mindestgeräteanforderungen müssen bekanntgegeben werden, damit die App immer mit höchster Leistung ausgeführt werden kann.
     
* Erfüllen der Größenanforderungen für Vorführgeräte
    
    Die App darf eine Größe von 800MB nicht übersteigen. Wenden Sie sich direkt an das Windows-Team für den Einzelhandel, wenn Ihre Demo-App für den Einzelhandel den Größenanforderungen nicht entspricht.

## Vorbereiten der Codebasis für den Demomodus für den Einzelhandel

Die Eigenschaft [**IsDemoModeEnabled**](https://msdn.microsoft.com/library/windows/apps/windows.system.profile.retailinfo.isdemomodeenabled.aspx) in der Hilfsklasse [**RetailInfo**](https://msdn.microsoft.com/library/windows/apps/windows.system.profile.retailinfo.aspx), die dem Namespace [Windows.System.Profile](https://msdn.microsoft.com/library/windows/apps/windows.system.profile.aspx) im Windows 10 SDK angehört, ist ein Boolescher Wert, der angibt, welcher Codepfad Ihrer Anwendung im _Normalmodus_ oder im _Einzelhandelsmodus_ ausgeführt wird. 

Wenn [**RetailInfo.IsDemoModeEnabled**](https://msdn.microsoft.com/library/windows/apps/windows.system.profile.retailinfo.isdemomodeenabled.aspx) „true“ zurückgibt, können Sie mithilfe von [**RetailInfo.Properties**](https://msdn.microsoft.com/library/windows/apps/windows.system.profile.retailinfo.properties.aspx) einen Satz von Eigenschaften zum Gerät abfragen, um eine besser angepasste Verwendung der Demo-App zu ermöglichen. Diese Eigenschaften umfassen [**ManufacturerName**](https://msdn.microsoft.com/library/windows/apps/windows.system.profile.knownretailinfoproperties.manufacturername.aspx), [**Screensize**](https://msdn.microsoft.com/library/windows/apps/windows.system.profile.knownretailinfoproperties.screensize.aspx), [**Memory**](https://msdn.microsoft.com/library/windows/apps/windows.system.profile.knownretailinfoproperties.memory.aspx) usw. 


## Bereinigungsprozess

Mit dem Bereinigungsprozess werden Vorführgeräte automatisch auf die ursprünglichen Standardeinstellungen zurückgesetzt, wenn für einen bestimmten Zeitraum keine Interaktion mit dem Gerät stattfindet. Dadurch wird sichergestellt, dass sich die Interaktion mit dem Gerät für alle Benutzer im Geschäft gleich gestaltet. Beim Entwickeln einer Demo-App für den Einzelhandel sind Kenntnisse darüber wichtig, wann und wie der Bereinigungsprozess ausgelöst wird, was bei der Standardbereinigung ausgeführt wird und wie dies angepasst werden kann, damit der Prozess der beabsichtigten Vorführanwendung entspricht.

### Wann beginnt die Bereinigung?

Die Bereinigung startet nach einer bestimmten Leerlaufzeit. Die Leerlaufzeit beginnt, wenn auf dem keine Touch-, Maus- oder Tastatureingabe mehr erfolgt.

#### Desktop/PC

Nach 120 Sekunden Leerlaufzeit wird auf dem Gerät das Leerlaufvideo wiedergegeben. 5Sekunden später startet der Bereinigungsprozess.

#### Telefon

Nach 60Sekunden Leerlaufzeit wird auf dem Gerät das Leerlaufvideo wiedergegeben, und der Bereinigungsprozess startet sofort.

### Was geschieht bei einem Standardbereinigungsprozess?

#### Schritt1: Bereinigen
* Alle Win32- und Store-Apps werden geschlossen.
* Alle Dateien in bekannten Ordnern wie __Bilder__, __Videos__, __Musik__, __Dokumente__, __SavedPictures__, __CameraRoll__, __Desktop__ und __Downloads__ Ordner werden gelöscht.
* Unstrukturierte und strukturierte Roamingzustände werden gelöscht.
* Strukturierte lokale Zustände werden gelöscht.

#### Schritt2: Einrichten 
* Offlinegeräte: Ordner bleiben leer
* Onlinegeräte: Demoressourcen für den Einzelhandel können vom Windows Store per Push an das Gerät übertragen werden.

### Wie kann ich Daten sitzungsübergreifend speichern?

Wenn Sie Daten sitzungsübergreifend speichern möchten, können Sie die Informationen in __ApplicationData.Current.TemporaryFolder__ speichern, da der Standardbereinigungsprozess die Daten in diesem Ordner nicht automatisch löscht. Die mithilfe von *LocalState* gespeicherten Informationen werden bei der Bereinigung gelöscht. 

### Wie kann ich den Bereinigungsprozess anpassen?

Wenn Sie den Bereinigungsprozess anpassen möchten, müssen Sie den `Microsoft-RetailDemo-Cleanup`-App-Dienst in Ihrer App implementieren. 

Szenarien, bei denen eine benutzerdefinierte Bereinigungslogik erforderlich ist, umfassen das Ausführen einer umfassenden Einrichtung, das Herunterladen und Zwischenspeichern von Daten oder das Beibehalten der *LocalState*-Daten.

Schritt1: Deklarieren des _Microsoft-RetailDemo-Cleanup_-Diensts in Ihrem Anwendungsmanifest
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

Schritt2: Implementieren der benutzerdefinierten Bereinigungslogik unter der _AppdataCleanup_-Funktion mithilfe der folgenden Beispielvorlage.
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

## Verwandte Links

* [Speichern und Abrufen von App-Daten](https://msdn.microsoft.com/windows/uwp/app-settings/store-and-retrieve-app-data)
* [Erstellen und Nutzen eines App-Diensts](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)
* [Lokalisieren von App-Inhalten](https://msdn.microsoft.com/windows/uwp/globalizing/globalizing-portal)


 

 



<!--HONumber=Nov16_HO1-->


