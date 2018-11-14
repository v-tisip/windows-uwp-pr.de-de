---
author: stevewhims
description: Wenn Sie Entwickler mit einer WindowsPhone-Silverlight-app sind, und klicken Sie dann Ihre und Fähigkeiten zurückgreifen und Ihren Quellcode beim Wechsel zu Windows 10 nutzen können.
title: Wechsel von WindowsPhone Silverlight zu UWP
ms.assetid: 9E0C0315-6097-488B-A3AF-7120CCED651A
ms.author: stwhi
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: eb2617fc3fbd14d17635435c8bfd6d58817a7a1b
ms.sourcegitcommit: 38f06f1714334273d865935d9afb80efffe97a17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6191958"
---
#  <a name="move-from-windowsphone-silverlight-to-uwp"></a>Wechsel von WindowsPhone Silverlight zu UWP


Wenn Sie Entwickler mit einer WindowsPhone-Silverlight-app sind, und klicken Sie dann Ihre und Fähigkeiten zurückgreifen und Ihren Quellcode beim Wechsel zu Windows 10 nutzen können. Mit Windows 10 können Sie eine app (universelle Windows Plattform) erstellen, also ein einzelnes app-Paket, das Ihre Kunden auf jeder Art von Gerät installieren können. Weitere Hintergrundinformationen zu Windows 10 UWP-apps und den Konzepten von adaptivem Code und adaptiver UI, die wir in diesem Handbuch für das Portieren, erörtern werden finden Sie unter der [Anleitung für universelle Windows-Plattform (UWP) apps](https://msdn.microsoft.com/library/windows/apps/dn894631).

Wenn Sie Ihre WindowsPhone-Silverlight-app zu einer Windows 10-app portieren, müssen Sie möglicherweise mithalten auf mobilen Features, die [in Windows Phone 8.1 eingeführt](https://msdn.microsoft.com/library/windows/apps/dn632424)wurden, und gehen weit darüber hinaus die universelle Windows-Plattform (UWP), deren app-Modell und Benutzeroberflächenframework verwenden universell auf allen Windows 10-Geräten gelten. Dies ermöglicht die Unterstützung von PCs, Tablets, Telefonen und einer großen Zahl von anderen Gerätearten – mit einer Codebasis und einem App-Paket. Zudem vervielfacht sich die potenzielle Zielgruppe Ihrer App, und Sie erhalten neue Möglichkeiten durch freigegebene Daten, gekaufte Consumables usw. [Was ist neu für Entwickler in Windows 10](https://dev.windows.com/getstarted/whats-new-windows-10)finden Sie weitere Informationen zu den neuen Features.

Bei Bedarf, können die WindowsPhone Silverlight-Version Ihrer App und die Windows 10-Version sowohl für Kunden zur gleichen Zeit verfügbar.

**Hinweis:** dieses Handbuchs soll Sie manuellen Portieren Ihrer WindowsPhone Silverlight-app für Windows 10 helfen. Zum Portieren Ihrer App können Sie neben den Informationen in diesem Leitfaden auch die Developer Preview der **Silverlight-Brücke von Mobilize.Net** ausprobieren, um den Portierungsprozess zu automatisieren. Dieses Tool analysiert Quellcode Ihrer app und konvertiert Verweise auf WindowsPhone Silverlight-Steuerelemente und-APIs in ihre UWP-Entsprechungen. Da dieses Tool noch die Developer Preview-Version aufweist, unterstützt es noch nicht alle Konvertierungsszenarien. Die meisten Entwickler sollten mit dem Einstieg in dieses Tool jedoch Zeit und Mühe sparen. Besuchen Sie die [Website von Mobilize.NET](http://go.microsoft.com/fwlink/p/?LinkId=624546), um die Developer Preview zu testen.

## <a name="xaml-and-net-or-html"></a>XAML und .NET oder HTML?

WindowsPhone Silverlight verfügt über ein XAML-UI-Framework, das auf Silverlight 4.0 basiert, und Sie Programmieren mit einer Version von .NET Framework sowie einer kleinen Teilmenge von UWP-APIs. Da Sie Extensible Application Markup Language (XAML) in Ihrer WindowsPhone Silverlight-app verwendet haben, ist es wahrscheinlich, dass XAML Ihrer Wahl für Ihre Windows 10-Version werden, da die meisten Ihrer Kenntnisse und Erfahrungen übertragen werden, wie viel von Ihrem Quellcode wird, und die Softwaremuster, die Sie verwenden. Auch Ihr UI-Markup und -Design lassen sich mühelos portieren. Ihnen werden die verwalteten APIs, das XAML-Markup, das Benutzeroberflächenframework und die Tools angenehm vertraut vorkommen, und Sie können C++, C# oder Visual Basic zusammen mit XAML in einer UWP-App verwenden. Obwohl es die eine oder andere Herausforderung zu meistern gilt, werden Sie vielleicht überrascht sein, wie einfach der Prozess letztlich ist.

Siehe [Roadmap für Universal Windows Platform (UWP)-Apps mit C# oder Visual Basic](https://msdn.microsoft.com/library/windows/apps/br229583).

**Hinweis:** Windows 10 unterstützt einen deutlich größeren von .NET Framework als Windows Phone Store-Apps. Windows 10 verfügt beispielsweise über mehrere System.ServiceModel.\* Namespaces als auch System.Net, System.Net.NetworkInformation und System.Net.Sockets. Daher ist jetzt ein idealer Zeitpunkt für das Portieren von WindowsPhone Silverlight und Ihre .NET Code nur zu kompilieren und auf der neuen Plattform funktionieren. Weitere Informationen finden Sie unter [Namespace- und Klassenzuordnungen](wpsl-to-uwp-namespace-and-class-mappings.md).
Ein weiterer guter Grund zum Neukompilieren von Ihrer vorhandenen .NET-Quellcodes in eine Windows 10-app besteht darin, dass Sie von .NET Native profitieren die eine ahead-des-kompilierungstechnologie, mit der MSIL nativ-Computercode konvertiert. .NET Native-Apps starten schneller, verbrauchen weniger Arbeitsspeicher und benötigen weniger Akkuenergie als ihre MSIL-Gegenstücke.

In diesem Portierungshandbuch geht es vorrangig um XAML. Alternativ können Sie mit JavaScript, Cascading Stylesheets (CSS) und HTML5 sowie der Windows-Bibliothek für JavaScript eine funktional vergleichbare App erstellen– viele der verwendeten UWP-APIs sind in diesem Fall identisch. Obwohl sich die Windows-Runtime-Benutzeroberflächenframeworks von XAML und HTML unterscheiden, funktionieren beide für sämtliche Windows-Geräte.

## <a name="targeting-the-universal-or-the-mobile-device-family"></a>Universelle Geräte oder Mobilgeräte

Eine Option ist das Portieren Ihrer App zu einer App für universelle Geräte. In diesem Fall besteht für die Installation der App der größte Spielraum. Wenn Ihre App die APIs aufruft, die nur in Mobilgeräten implementiert sind, können Sie diese Aufrufe mit adaptivem Code schützen. Alternativ dazu können Sie Ihre App auch zu einer App für Mobilgeräte portieren. In diesem Fall müssen Sie keinen adaptiven Code schreiben.

## <a name="adapting-your-app-to-multiple-form-factors"></a>Anpassen der App an mehrere Formfaktoren

Die im vorherigen Abschnitt gewählte Option bestimmt die Palette an Geräten, auf denen Ihre App oder Apps ausgeführt werden, und dabei kann es sich um eine sehr breite Palette von Geräten handeln. Selbst wenn Sie Ihre App auf Mobilgeräte beschränken, müssen Sie dennoch ein breites Spektrum an Bildschirmgrößen unterstützen. Wenn Ihre App also auf verschiedenen Formfaktoren ausgeführt wird, die vorher nicht unterstützt wurden, sollten Sie Ihre Benutzeroberfläche auf diesen Formfaktoren testen und ggf. Änderungen vornehmen, damit sich die UI auf jedem Gerät entsprechend anpasst. Stellen Sie sich dies als eine Aufgabe nach der Portierung oder eine erweiterte Zielvorgabe für das Portieren vor. Die Fallstudie [Bookstore2](wpsl-to-uwp-case-study-bookstore2.md) enthält hierzu ein Praxisbeispiel.

## <a name="approaching-porting-layer-by-layer"></a>Portieren der einzelnen Ebenen

-   **Ansicht**. Die Ansicht und das Ansichtsmodell bilden die UI Ihrer App. Im Idealfall besteht die Ansicht aus Markup, das an feststellbare Eigenschaften eines Ansichtsmodells gebunden ist. Ein weiteres gängiges, aber nur auf kurze Sicht zweckmäßiges Muster ist das direkte Ändern von UI-Elementen mit imperativem Code in einer CodeBehind-Datei. In beiden Fällen kann ein Großteil des UI-Markups und -Designs–und sogar imperativer Code zum Ändern von UI-Elementen–einfach portiert werden.
-   **Ansichtsmodelle und Datenmodelle**. Auch wenn Sie Muster zur Trennung der Zuständigkeiten (z.B. MVVM) nicht ausdrücklich anwenden, gibt es in Ihrer App zwangsläufig Code, der die Funktion des Ansichts- und Datenmodells übernimmt. Code für das Ansichtsmodell nutzt Typen in den Namespaces des Benutzeroberflächenframeworks. Sowohl der Code für das Ansichtsmodell als auch der Code für das Datenmodell nutzen zudem nicht visuelle Betriebssystem- und .NET-APIs (darunter APIs für den Datenzugriff). Und die meisten dieser APIs sind [für UWP-Apps verfügbar](https://msdn.microsoft.com/library/windows/apps/br211369). Sie können daher davon ausgehen, dass sich ein Großteil dieses Codes ohne Änderungen portieren lässt. Bedenken Sie aber, dass ein Ansichtsmodell ein Modell oder eine *Abstraktion* einer Ansicht ist. Ein Ansichtsmodell stellt den Zustand und das Verhalten der UI bereit, während die Ansicht selbst die visuellen Elemente bereitstellt. Aus diesem Grund sind wahrscheinlich für jede UI, die Sie an die verschiedenen, von der UWP unterstützten Formfaktoren anpassen, entsprechende Änderungen des Ansichtsmodells erforderlich. Für Netzwerke und das Aufrufen von Clouddiensten können Sie normalerweise zwischen .NET und UWP-APIs wählen. Informationen zu den Faktoren, die diese Entscheidung beeinflussen, finden Sie unter [Clouddienste, Netzwerk und Datenbanken](wpsl-to-uwp-business-and-data.md).
-   **Clouddienste**. Höchstwahrscheinlich werden einige (oder sogar die meisten) Teile Ihrer App in Form von Diensten in der Cloud ausgeführt. Der auf dem Clientgerät ausgeführte Teil der App stellt eine Verbindung mit diesen Diensten her. Dies ist der Teil einer verteilten App, bei dem es am wahrscheinlichsten ist, dass er beim Portieren des Clientteils unverändert bleibt. Falls Sie noch keine Clouddienste nutzen, sind [Microsoft Azure Mobile Services](http://azure.microsoft.com/services/mobile-services/) eine gute Wahl für Ihre UWP-App. Sie bieten leistungsstarke Back-End-Komponenten, die universelle Windows-Apps für verschiedenste Dienste aufrufen können– angefangen bei einfachen Benachrichtigungen für Live-Kachelaktualisierungen bis hin zur komplexen Skalierbarkeit, die eine Serverfarm bereitstellen kann.

Überlegen Sie vor oder während der Portierung, ob Ihre App dadurch verbessert werden könnte, wenn Sie sie umgestalten und Code mit einem ähnlichen Zweck in Ebenen zusammenfassen, anstatt ihn willkürlich zu verteilen. Die Aufteilung Ihrer UWP-App in die oben beschriebenen Ebenen erleichtert Ihnen das Ausschließen von Fehlern, das Testen sowie das spätere Lesen und Warten Ihrer App. Sie können die Wiederverwendbarkeit von Funktionen verbessern– und Probleme mit Unterschieden in den UI-APIs vermeiden–, indem Sie das Model-View-ViewModel-Muster ([MVVM](http://msdn.microsoft.com/magazine/dd419663.aspx)) anwenden. Dieses Muster trennt die Daten-, Geschäfts- und UI-Teile der App voneinander. Auch innerhalb der UI kann das Muster Zustand und Verhalten von den visuellen Elementen getrennt halten, sodass diese separat getestet werden können. Das MVVM-Muster bietet Ihnen die Möglichkeit, Ihre Daten und Geschäftslogik einmal zu schreiben und auf allen Geräten, unabhängig von der UI, zu verwenden. Es ist wahrscheinlich, dass Sie auch einen Großteil des Ansichtsmodells und der Ansichtselemente auf verschiedenen Geräten wiederverwenden können.

## <a name="one-or-two-exceptions-to-the-rule"></a>Ein oder zwei Ausnahmen von der Regel

Beim Lesen dieses Portierungshandbuchs können Sie auch die Informationen unter [Namespace- und Klassenzuordnungen](wpsl-to-uwp-namespace-and-class-mappings.md) nutzen. Im Allgemeinen wird eine einfache Zuordnung verwendet, und in der Tabelle mit den Namespace- und Klassenzuordnungen werden etwaige Ausnahmen beschrieben.

Die gute Nachricht ist, dass auf der Featureebene nur sehr wenig nicht in der UWP unterstützt wird. Wenn Sie den Rest dieses Handbuchs für das Portieren lesen, werden Sie feststellen, dass sich die meisten Ihrer Kenntnisse und der Großteil Ihres Quellcodes sehr gut auf UWP-Apps übertragen lassen. Hier sind jedoch einige WindowsPhone Silverlight Features, die Sie verwendet haben und vielleicht für die es kein UWP-äquivalent.

| Feature, für das es kein UWP-Äquivalent gibt | WindowsPhone Silverlight-Dokumentation für das feature |
|----------------------------------------------|---------------------------------------------------------|
| Microsoft XNA. Im Allgemeinen wird als Ersatz [Microsoft DirectX](https://msdn.microsoft.com/library/windows/desktop/ee663274) mit C++ verwendet. Siehe [Entwickeln von Spielen](https://msdn.microsoft.com/library/windows/apps/hh452744) und [Interoperabilität von DirectX und XAML](https://msdn.microsoft.com/library/windows/apps/hh825871). | [XNA-Framework-Klassenbibliothek](http://msdn.microsoft.com/library/bb203940.aspx) | 
|Foto-Apps | [Foto-Apps für Windows Phone8](http://msdn.microsoft.com/library/windows/apps/jj206990.aspx) |

&nbsp;

| Thema| Beschreibung|
|------|------------| 
| [Namespace- und Klassenzuordnungen](wpsl-to-uwp-namespace-and-class-mappings.md) | Dieses Thema enthält eine umfassende Zuordnung der WindowsPhone Silverlight-APIs zu ihren UWP-äquivalenten. |
| [Portieren des Projekts](wpsl-to-uwp-porting-to-a-uwp-project.md) | Sie beginnen den portierungsprozess durch Erstellen eines neuen Windows 10-Projekts in Visual Studio, und kopieren die Dateien hinein. |
| [Fehlerbehebung](wpsl-to-uwp-troubleshooting.md) | Wir empfehlen dringend, dieses Handbuch für das Portieren vollständig zu lesen. Wir wissen aber auch, dass Sie möglichst schnell die Phase erreichen möchten, in der Ihr Projekt erstellt und ausgeführt wird. Zu diesem Zweck können Sie einen temporären Fortschritt erzielen, indem Sie allen nicht unbedingt erforderlichen Code auskommentieren und anschließend zurückkehren, um die Schulden später zu bezahlen. Die Tabelle mit Symptomen und Möglichkeiten zur Problembehandlung in diesem Thema kann in dieser Phase hilfreich für Sie sein, ersetzt jedoch nicht das Lesen der nächsten Themen. Sie können die Tabelle jederzeit zu Rate ziehen, während Sie die weiteren Themen lesen. |
| [Portieren von XAML und UI](wpsl-to-uwp-porting-xaml-and-ui.md) | Die Vorgehensweise zum Definieren einer Benutzeroberfläche in Form von deklarativem XAML-Markup lässt sich sehr gut von WindowsPhone Silverlight zu UWP-apps. Sie werden feststellen, dass große Abschnitte Ihres Markups kompatibel sind, sobald Sie Verweise auf Systemressourcenschlüssel aktualisiert, einige Namen von Elementtypen geändert und „clr-namespace“ in „using“ geändert haben. |
| [Portieren: E/A, Gerät und App-Modell](wpsl-to-uwp-input-and-sensors.md) | Code, der in das Gerät selbst integriert und auf dessen Sensoren abgestimmt ist, umfasst auch Eingaben vom und Ausgaben an den Benutzer. Auch die Datenverarbeitung kann einbezogen werden. Aber dieser Code wird in der Regel nicht als UI-Ebene oder Datenebene betrachtet. Dieser Code enthält die Integration in Vibrationscontroller, Beschleunigungsmesser, Gyroskop, Mikrofon und Lautsprecher (überschneiden sich mit Spracherkennung und Sprachsynthese), (geografischen) Standort und Eingabemodalitäten, z.B. Touch, Maus, Tastatur und Stift. |
| [Portieren der Geschäfts- und Datenebene](wpsl-to-uwp-business-and-data.md) | Im Hintergrund Ihrer UI befinden sich Ihre Geschäfts- und Datenebenen. Der Code auf diesen Ebenen ruft Betriebssystem- und .NET Framework-APIs auf (z. B. Hintergrundverarbeitung, Position, Kamera, Dateisystem, Netzwerk und andere Datenzugriffsfunktionen). Die meisten dieser APIs sind [für UWP-Apps verfügbar](https://msdn.microsoft.com/library/windows/apps/br211369). Sie können daher davon ausgehen, dass sich ein Großteil dieses Codes ohne Änderungen portieren lässt. |
| [Portieren für Formfaktor und Benutzerfreundlichkeit](wpsl-to-uwp-form-factors-and-ux.md) | Windows-Apps weisen auf PCs, Mobilgeräten und vielen anderen Arten von Geräten ein einheitliches Erscheinungsbild auf. Die Benutzeroberfläche, Eingabe und Interaktionsmuster sind fast identisch, und Benutzer profitieren von einer einheitlichen Umgebung auf allen Geräten.|
|[Fallstudie: Bookstore1](wpsl-to-uwp-case-study-bookstore1.md) | Dieses Thema enthält eine Fallstudie für das Portieren einer sehr einfachen WindowsPhone Silverlight-app zu einer Windows10UWP-app. Mit Windows 10, können Sie ein einzelnes app-Paket erstellen, die Ihre Kunden auf einer Vielzahl von Geräten installieren können und was wir in dieser Fallstudie tun. |
| [Fallstudie: Bookstore2](wpsl-to-uwp-case-study-bookstore2.md) | Diese Fallstudie – baut auf den Informationen in [Bookstore1](wpsl-to-uwp-case-study-bookstore1.md)– beginnt mit einer WindowsPhone Silverlight-app, die gruppierte Daten in einem **LongListSelector**. Im Ansichtsmodell stellt jede Instanz der **Author**-Klasse die Gruppe der vom betreffenden Autor verfassten Titel dar. In **LongList Selector** können wir dann entweder die Bücherliste nach Autoren gruppiert anzeigen oder die Liste verkleinern, um eine Sprungliste der Autoren zu erhalten. |

## <a name="related-topics"></a>Verwandte Themen

**Dokumentation**
* [Neuigkeiten für Entwickler in Windows 10](https://dev.windows.com/getstarted/whats-new-windows-10)
* [Anleitung für Universelle Windows-Plattform-Apps (UWP)](https://msdn.microsoft.com/library/windows/apps/dn894631)
* [Roadmap für Universal Windows Platform (UWP)-Apps mit C# oder Visual Basic](https://msdn.microsoft.com/library/windows/apps/br229583)
* [Nächste Schritte für Windows Phone8-Entwickler](https://msdn.microsoft.com/library/windows/apps/xaml/dn655121.aspx)

**Artikel in Magazinen**
* [Visual Studio Magazine: Windows Phone8.1: Ein Riesenschritt für die Konvergenz](http://go.microsoft.com/fwlink/p/?LinkID=398541)

**Präsentationen**
* [Die Story of Bringing Bereitstellung Nokia Music von Windows Phone zu Windows8](http://go.microsoft.com/fwlink/p/?LinkId=321521)
 

