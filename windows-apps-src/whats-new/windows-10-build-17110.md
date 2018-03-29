---
author: QuinnRadich
title: Neues in Windows10 für Entwickler, Werkzeuge und Features
description: Windows10, Build17110, und neue Entwicklertools stellen Werkzeuge, Features und Umgebungen zur Verfügung, die durch die neue universelle Windows-Plattform unterstützt werden.
keywords: Neuigkeiten, was neu ist, Aktualisierung, Updates, Features, neu, Windows 10, Neuigkeiten, Entwickler, 17110, Vorschau
ms.author: quradic
ms.date: 3/07/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: high
ms.openlocfilehash: 5d416ad13c2e689c5265164c0269244a387a6c7f
ms.sourcegitcommit: ef5a1e1807313a2caa9c9b35ea20b129ff7155d0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2018
---
# <a name="whats-new-in-windows-10-for-developers-sdk-preview-build-17110"></a>Neuigkeiten für Entwickler in Windows10, SDK-Vorabversion Build 17110

Die Windows10 SDK Vorabversion 17110 bietet in Kombination mit Visual Studio2017 und dem aktualisierten SDK die Tools, Features und Umgebungen, um eine eindrucksvolle universelle Windows-Plattform-Apps zu entwickeln. Nach der [Installation der Tools und des SDKs](http://go.microsoft.com/fwlink/?LinkId=821431) unter Windows10 können Sie entweder [eine neue universelle Windows-App erstellen](../get-started/create-uwp-apps.md) oder sich mit der Verwendung von [vorhandenem App-Code unter Windows](../porting/index.md) vertraut machen.

Dies ist eine Sammlung von neuen und verbesserten Features und Richtlinien, die in dieser SDK-Vorabversion für Windows-Entwickler interessant sind. Im Moment sind diese Features für Mitglieder des [Windows-Insider-Programms](https://insider.windows.com/en-us/) erhältlich. Diese werden im nächsten wichtigen Update von Windows10 öffentlich verfügbar gemacht werden. Eine vollständige Liste der neuen Namespaces, die dem Windows SDK hinzugefügt werden, finden Sie unter der [Windows 10 Build 17110 API-Änderungen](windows-10-build-17110-api-diff.md). Weitere Informationen zu den Highlights von Windows10 finden Sie unter [Die Highlights in Windows10](http://go.microsoft.com/fwlink/?LinkId=823181). Darüber hinaus finden Sie unter [Windows Developer Platform-Features](https://developer.microsoft.com/windows/platform/features) eine grobe Übersicht über die früheren und zukünftigen neuen Features der Windows-Plattform.

## <a name="design--ui"></a>Design und UI

Feature | Beschreibung
 :------ | :------
Adaptive und interaktive Popupbenachrichtigungen | Optimieren Sie Ihre App mit adaptiven und interaktiven Benachrichtigungen. Entdecken Sie die [aktualisierte Anleitung für Popupbenachrichtigungen](../design/shell/tiles-and-notifications/adaptive-interactive-toasts.md) und die Informationen über Größenbeschränkung von Bildern, Statusleisten und das Hinzufügen von Eingabeoptionen.
Links zu Inhalten | Das neue Steuerelement [Links zu Inhalten](../design/controls-and-patterns/content-links.md) bietet eine Möglichkeit, umfangreiche Daten in Textsteuerelemente einzubetten, wodurch Benutzer weitere Informationen zu einer Person oder einem Ort finden und verwenden können, ohne den Kontext Ihrer App verlassen zu müssen.
Entwurfsbeispiele | Das Beispiel „BuildCast” wurde auf der Seite [Design-Toolkits und Beispiele](../design/downloads/index.md) hinzugefügt. BuildCast ist ein End-to-End-Beispiel und basiert auf dem Fluent Design-System sowie auf andere Funktionen der universellen Windows-Plattform.
Eingebettete Handschrift | Den [Textsteuerelementen](../design/controls-and-patterns/text-controls.md) wurde die Stifteingabefunktion hinzugefügt, damit Benutzer mit Windows Ink direkt in die Textfelder schreiben können. Während der Benutzer schreibt, wird der Text in ein Skript konvertiert, das das Verhalten der natürlichen Schreibweise beibehält.
Fluent Design Update | Wir haben viele unserer Fluent Design-Seiten mit neuen Informationen und Anleitungen aktualisiert: </br> * Die [Fluent Design-Übersicht](../design/fluent-design-system/index.md) wurde aktualisiert, um die neuesten Fluent Design-Features widerzuspiegeln. </br> * [Reveal-highlight](../design/style/reveal.md) enthält neue Anleitungen über Designs und benutzerdefinierte Steuerelemente. </br> * [Navigationsverlauf und Rückwärtsnavigation](../design/basics/navigation-history-and-backwards-navigation.md) wurden überarbeitet und mit detaillierten Beispielen, Leitfäden zur Optimierung der Geräte und Richtlinien für das benutzerdefinierte Verhalten aktualisiert.
Seitenlayouts | Wir haben unsere [XAML-Seitenlayout](../design/layout/layouts-with-xaml.md)-Dokumentation mit neuen Informationen zu dynamischen Layouts und visuellen Zuständen aktualisiert. Diese Features ermöglichen eine bessere Kontrolle darüber, wie die Position der Elemente Ihrer App reagieren und sich an den verfügbaren visuellen Platz anpasst.
Aktualisierung durch Ziehen | Dank des Steuerelements [Aktualisieren durch Ziehen](../design/controls-and-patterns/pull-to-refresh.md) können Benutzer aktuelle Daten in einer Liste durch das Ausführen einer Ziehbewegung von oben nach unten auf der Liste abrufen. Es wird häufig auf Geräten mit Touchscreen verwendet.
Navigationsansicht | Das [Navigationsansicht](../design/controls-and-patterns/navigationview.md)-Steuerelement bietet über ein reduzierbares Navigationsmenü ein allgemeines vertikales Layout für App-Bereiche auf oberster Ebene. Dieses Steuerelement dient der Implementierung des Navigationsbereichsmusters oder Hamburger-Menü-Musters, wobei die Anordnung automatisch an verschiedene Fenstergrößen des Bereichs angepasst wird.
Einblendungen mit Fokus | Die neuen [Einblendungen mit Fokus](../design/style/reveal-focus.md)-Effekte bieten Lichtelemente für Erfahrungen wie z.B. Xbox One- und Fernsehbildschirme. Sie animieren den Rahmen des fokussierbaren Elementes wie beispielsweise Schaltflächen, wenn der Benutzer den Fokus des Gamepad oder der Tastatur darauf lenken.
Sound | XAML unterstützt jetzt 3D Audio mit der Eigenschaft **SpatialAudioMode**. Weitere Informationen zur Konfiguration finden Sie unter [Sound](../design/style/sound.md).
Strukturansicht | Das Steuerelement [Strukturansicht](../design/controls-and-patterns/tree-view.md) ermöglicht eine Hierarchieauflistung mit Knoten, die das Aus- und Einblenden von geschachtelten Elementen erlauben. Es kann verwendet werden, um eine Ordnerstruktur oder geschachtelte Beziehungen zwischen Elementen in der Benutzeroberfläche zu veranschaulichen.
Schreibstil | Wir haben unseren Artikel über Ausdrucksweise und Tonfall aktualisiert und erweitert und diesen in eine [Schreibstilanleitung](../design/style/writing-style.md) umgewandelt. Diese neue Information enthält Prinzipien zur Erstellung von effektivem Text in Ihrer App sowie bewährte Methoden für das Schreiben von Steuerelementen wie z.B. Fehlermeldungen oder Dialogfelder.

## <a name="gaming"></a>Spiele
Feature | Beschreibung
 :------ | :------
Erste Schritte bei der Spiele-Entwicklung | Möchten Sie Spiele für Windows10 entwickeln? Die neue Seite [Erste Schritte bei der Spiele-Entwicklung](../gaming/getting-started.md) ermöglicht einen vollständigen Überblick darüber, wie Sie sich vorbereiten, registriert und Ihre Apps und Spiele übermitteln.
Grafikadapter | Wir haben die folgenden DXGI-APIs hinzugefügt, die sich auf die Vorteile und das Entfernen von Grafikadaptern beziehen: </br> * Der [IDXGIFactory6](https://msdn.microsoft.com/library/windows/desktop/mt814823)-Schnittstelle bietet eine einzelne Methode, die Grafikkarten, basierend auf einer bestimmten GPU-Einstellung, auflistet. </br> * Die [DXGIDeclareAdapterRemovalSupport](https://msdn.microsoft.com/library/windows/desktop/mt814821)-Funktion ermöglicht einem Prozess anzugeben, dass er in Bezug auf das Entfernen der Grafikgeräte flexibel reagiert. </br> * Die [DXGI_GPU_PREFERENCE](https://msdn.microsoft.com/library/windows/desktop/mt814822)-Auflistung beschreibt die Einstellung der GPU, auf der für die App ausgeführt wird.


## <a name="develop-windows-apps"></a>Entwickeln von Windows-Apps

Feature | Beschreibung
 :------ | :------
Adaptive Karten | [Adaptive Karten](https://docs.microsoft.com/adaptive-cards/) sind eine offenes Kartenaustauschformat, mit dem Entwickler UI-Inhalte auf einheitliche und konsistente Weise austauschen können. Deren Inhalte werden JSON-Objekt beschrieben, das gerendert werden kann, um das Aussehen und Verhalten der Host-Anwendung automatisch anzupassen.
App-Ressourcengruppe | Die [AppResourceGroupInfo](https://docs.microsoft.com/uwp/api/windows.system.appresourcegroupinfo)-Klasse verfügt über neue Methoden, die Sie verwenden können, um den Übergang für den Status „angehalten”, „aktiv” (zurückgeholt) und „beendet” zu initiieren.
Zugriff auf das allgemeine Dateisystem | Die Funktion **broadFileSystemAccess** ermöglicht Apps den gleichen Zugriff auf das Dateisystem wie der Benutzer, der aktuell die App ohne Dateiauswahlaufforderungen ausführt. Weitere Informationen finden Sie unter [Berechtigungen für den Dateizugriff](../files/file-access-permissions.md) und den Eintrag **broadFileSystemAccess** unter [Deklarationen von App-Funktionen](../packaging/app-capability-declarations.md).
UWP-Apps auf Konsolen | Sie können jetzt C++/WinRT oder /CX UWP Konsolen-Apps erstellen, die in einem Konsolenfenster wie z.B. einem DOS oder PowerShell-Konsolenfenster ausgeführt werden. Konsolen-Apps verwenden das Konsolenfenster für die Eingabe und Ausgabe. UWP-Konsolen-Apps können im Microsoft Store veröffentlicht werden, haben einen Eintrag in der App-Liste und eine primäre Kachel, die an das Startmenü angeheftet werden kann. Weitere Informationen finden Sie unter [Erstellen einer universellen Windows-Plattform-Konsolen-App](../launch-resume/console-uwp.md)
Unterstützte Orientierungspunkte und Überschriften für die barrierefreie Technologie (AT) | „Unterstützte Orientierungspunkte und Überschriften” definieren Bereiche einer Benutzeroberfläche, die Benutzer bei der effizienten Navigation von Hilfstechnologien wie Bildschirmleseprogrammen unterstützen. Weitere Informationen finden Sie unter [Unterstützte Orientierungspunkte und Überschriften](../design/accessibility/landmarks-and-headings.md).
Machine Learning | Mit Windows Machine Learning können Sie Apps erstellen, die bereits geschulte Machine Learning-Modelle lokal auf Ihrem Windows10-Geräten bewerten. Weitere Informationen zur Plattform finden Sie unter [Windows Machine Learning](../machine-learning/index.md). </br> Der [MachineLearning](https://docs.microsoft.com/uwp/api/windows.ai.machinelearning.preview)-Namespace enthält Klassen, mit denen Apps Machine Learning-Modelle hochladen, Daten als Eingaben binden und Ergebnisse auswerten können.
Kartensteuerelemente | Die [MapControl](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapcontrol)-Klasse verfügt über eine neue Eigenschaft namens **Region**, die Sie zum Anzeigen von Inhalt in einem Kartensteuerelement verwenden können, das auf der Sprache einer bestimmten Region (z.B. dem Bundesland) basiert.
Elemente zuordnen | Die [MapElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapelement)-Klasse verfügt über eine neue Eigenschaft namens **IsEnabled**, mit der Sie angeben können, ob Benutzer mit [MapElement](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.maps.mapelement) interagieren können.
Ortsinformationen zuordnen | Die [PlaceInfo](https://docs.microsoft.com/uwp/api/windows.services.maps.placeinfo) -Klasse enthält eine neue Methode **CreateFromAddress**, mit dem Sie zum Erstellen einer [PlaceInfo](https://docs.microsoft.com/uwp/api/windows.services.maps.placeinfo) mithilfe einer Adresse und -Namen.
Kartendienste | Die [MapRouteDrivingOptions](https://docs.microsoft.com/uwp/api/windows.services.maps.maproutedrivingoptions)-Klasse enthält eine neue Eigenschaft namens **DepartureTime**, die Sie verwenden können, um eine Route mit den Verkehrsverhältnissen zu berechnen, die für den angegebene Tag und die Uhrzeit typisch sind.
UWP-Apps mit mehreren Instanzen | Eine UWP-App kann abonniert werden, um mehrere Instanzen zu unterstützen. Wenn eine Instanz einer UWP-App mit mehreren Instanzen ausgeführt wird und eine nachfolgende Aktivierungsanforderung eingeht, wird die vorhandene Instanz von der Plattform nicht aktiviert. Stattdessen wird eine neue Instanz erstellt, die in einem separaten Prozess ausgeführt wird. Weitere Informationen finden Sie unter [Create a multi-instance Universal Windows App](../launch-resume/multi-instance-uwp.md).
PlayReady | Microsoft PlayReady umfasst eine Reihe von Technologien zum Schutz digitaler Inhalte vor unbefugtem Zugriff. PlayReady kann auf verschiedenen Geräten und Apps und auf allen Betriebssystemen ausgeführt werden. [Erfahren Sie, wie Sie PlayReady in Ihre App integrieren.](https://docs.microsoft.com/playready/)
Bildschirmaufnahme | Der [Windows.Graphics.Capture-Namespace](https://docs.microsoft.com/uwp/api/windows.graphics.capture) enthält APIs zum Abrufen von Frames aus einer Anzeige oder einem Anwendungsfenster, um Videostreams zu erstellen oder gemeinsame und interaktive Benutzeroberflächen zu erstellen. Weitere Informationen finden Sie unter [Bildschirmaufnahme](../audio-video-camera/screen-capture.md).
Systemtrigger | Mit dem [CustomSystemEventTrigger](https://docs.microsoft.com/uwp/api/windows.applicationmodel.background.customsystemeventtrigger) können Sie einen Systemtrigger definieren, wenn das Betriebssystem keinen Systemtrigger zur Verfügung steht, den Sie benötigen. Wenn beispielsweise der Hardwaretreiber und die UWP-App beide von Drittanbietern stammen und der Hardwaretreiber ein benutzerdefiniertes Ereignis auslösen soll, das die App behandeln muss. Zum Beispiel eine Soundkarte, die Benutzer darüber benachrichtigt, wenn eine Audiobuchse angeschlossen wird.
Benutzeraktivitäten | Die **UserActivitySessionHistoryItem**-Klasse verfügt über neue Methoden, um Aktivitäten des aktuellen Benutzers abzurufen. Weitere Informationen dazu und über eine Überlastung finden Sie unter [GetRecentUserActivitiesAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivitychannel#Windows_ApplicationModel_UserActivities_UserActivityChannel_GetRecentUserActivitiesAsync_System_Int32_).
Windows Mixed Reality | Um die wachsende Windows Mixed Reality-Plattform zu unterstützen, wurden neue APIs zu den [Windows.Graphic.Holographic](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic) und [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/Windows.UI.Input.Spatial)-Namespaces hinzugefügt.

## <a name="publish--monetize-windows-apps"></a>Veröffentlichen und Monetarisieren von Windows-Apps

Feature | Beschreibung
 :------ | :------
Angeben formfreier Preise in der lokalen Währung für einen bestimmten Markt | Wenn Sie den Grundpreis Ihrer App für einen bestimmten Markt überschreiben, sind Sie nicht mehr auf das Standardpreisniveaus beschränkt. Sie haben nun die Möglichkeit, einen formfreien Preis in der lokalen Währung des Markts einzugeben. Weitere Informationen finden Sie unter [Festlegen und Planen von App-Preisen](../publish/set-and-schedule-app-pricing.md). **Diese Funktion steht allen Windows-Entwicklern zur Verfügung und die aktualisierte SDK ist nicht erforderlich.**
Inhalt des Stores | Die [StoreContext](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext)-Klasse wurde durch eine Auswahl neuer Methoden aktualisiert. Diese Methoden verwalten das Herunterladen und Installieren von Paketupdates und Add-Ons für eine App.
Abonnement-Add-Ons sind jetzt für alle Entwickler verfügbar | Erstellen und veröffentlichen Sie Abonnement-Add-Ons, um digitale Produkte in Ihrer App und Ihren Spielen zu verkaufen (z.B. App-Features oder digitale Inhalte), die mit einer automatisierten wiederkehrenden Abrechnung arbeiten. Weitere Details finden Sie unter [Abonnement-Add-Ons für Ihre App aktivieren](../monetize/enable-subscription-add-ons-for-your-app.md). **Diese Funktion steht allen Windows-Entwicklern zur Verfügung und die aktualisierte SDK ist nicht erforderlich.**

## <a name="videos"></a>Videos

Folgende Videos wurden seit dem Fall Creators Update veröffentlicht. Diese heben neue und verbesserte Features in Windows10 für Entwickler hervor.

### <a name="package-a-net-app-in-visual-studio"></a>Packen einer .NET-App in Visual Studio

Es ist einfacher denn je, eine Desktop-App auf die Universelle Windows-Plattform zu übertragen. [Sehen Sie sich das Video](https://www.youtube.com/watch?v=fJkbYPyd08w) an und erfahren Sie, wie Sie Ihre .NET-App für die Verteilung verpacken und wechseln Sie auf [diese Seite](../porting/desktop-to-uwp-packaging-dot-net.md) für weitere Informationen.

### <a name="xbox-live-creators-program"></a>Xbox Live Creators-Programm

Mit dem Xbox Live Creators-Programm können Entwickler schnell ihre UWP-Spiele auf Xbox One und Windows10 veröffentlichen. [Sehen Sie sich das Video](https://www.youtube.com/watch?v=zpFfHHBkVq4) für weitere Informationen zu dem Programm an, und gehen Sie zu [dieser Seite](https://www.xbox.com/developers/creators-program), um zu beginnen.

### <a name="creating-3d-app-launchers-for-windows-mixed-reality"></a>Erstellen von 3D-Anwendungsstartern für Windows Mixed Reality

3D-Startprogramme bieten eine eindeutige Möglichkeit für Benutzer, eine volumetrische Darstellung Ihrer App auf der Mixed Reality-Heimumgebungen darzustellen. [Video ansehen](https://www.youtube.com/watch?v=TxIslHsEXno) – hier finden Sie Informationen zum Vorbereiten Ihres 3D-Modells und um es als Startprogramm für Ihre App zu verwenden. [Lesen Sie die Entwicklerdokumente](https://developer.microsoft.com/windows/mixed-reality/implementing_3d_app_launchers) und [sehen Sie sich unsere Designrichtlinien](https://developer.microsoft.com/windows/mixed-reality/3d_app_launcher_design_guidance) für weitere Informationen an.

### <a name="motion-controller-tracking"></a>Motion-Controller nachverfolgen

Motion Controller stellen die Hände des Benutzers in Windows Mixed Reality dar. [Sehen Sie sich das Video](https://www.youtube.com/watch?v=rkDpRllbLII) und erfahren Sie, wie Motion Controller funktionieren, wenn sie in und aus dem Sichtfeld des Mixed Reality-Kopfhörers sind und [lesen Sie hier weitere Informationen über das Nachverfolgen des Controllers.](https://developer.microsoft.com/windows/mixed-reality/motion_controllers#controller_tracking_state%E2%80%9D)

### <a name="accessibility-tools-for-windows-developers"></a>Tools für die Barrierefreiheit für Windows-Entwickler

Windows 10 SDK enthält verschiedene Tools, die Bedienungshilfen Ihrer App zu testen und zu verbessern. Die Tools „Inspect” und „AccEvent” helfen Ihnen, Ihre Apps für alle Anwender verfügbar zu machen. Sie können das [Video ansehen](https://www.youtube.com/watch?v=ce0hKQfY9B8&list=PLWs4_NfqMtoycBFndriDmkQlMLwflyoFF&t=0s&index=1), um weitere Informationen zu diesen Tools zu erhalten und [weitere Informationen zu Barrierefreiheitstests lesen](../design/accessibility/accessibility-testing.md).