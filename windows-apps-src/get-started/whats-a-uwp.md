---
author: GrantMeStrength
ms.assetid: C9787269-B54F-4FFA-A884-D4A3BF28F80D
title: Was ist eine Universelle Windows-Plattform (UWP)-App?
description: "Hier erfahren Sie mehr über die verschiedenen Arten von universellen Windows-Apps – Windows Store-Apps, Windows Phone Store -Apps und Windows-Runtime-Apps."
ms.author: susanw
ms.date: 03/22/2017
ms.topic: article
pms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 2afb5cbc74b381e85fa861562e7de57d877b0c7f
ms.sourcegitcommit: 253ed634522773e15199084a6f74a3a465c2b218
translationtype: HT
---
# <a name="whats-a-universal-windows-platform-uwp-app"></a>Was ist eine Universelle Windows-Plattform (UWP)-App?

Die Universelle Windows-Plattform (UWP) ist die App-Plattform für Windows10. Sie können mit nur einem API-Satz, einem App-Paket und einem Store Apps für UWP entwickeln, um alle Windows10-Geräte zu erreichen – PCs, Tablets, Telefone, Xbox, HoloLens, Surface Hub und mehr. Es ist einfacher, eine Reihe von Bildschirmgrößen und eine Vielzahl von Interaktionsmodellen zu unterstützen, sei es Touch, Maus und Tastatur, einen Gamecontroller oder einen Stift. Die Idee der UWP-Apps besteht im Prinzip darin, dass Benutzer ihre *Erfahrungen* auf ALLEN Geräten nutzen und jeweils das Gerät verwenden möchten, das für die entsprechende Aufgabe am einfachsten oder produktivsten einzusetzen ist.

UWP ist auch flexibel: Sie müssen C# und XAML nicht verwenden, wenn Sie nicht möchten. Entwickeln Sie gerne in Unity oder MonoGame? Bevorzugen Sie JavaScript? Kein Problem; Sie können beliebige Programmiersprachen verwenden. Sie haben eine mit C++ entwickelte Desktop-App, die Sie mit UWP-Features erweitern und im Store verkaufen möchten? Das ist auch möglich. 

Fazit: Sie können mit vertrauten Programmiersprachen, Frameworks und APIs in einem einzigen Projekt arbeiten und denselben Code auf dem breiten Spektrum der heute verfügbaren Windows-Hardware ausführen lassen. Nachdem Sie Ihre UWP-App entwickelt haben, können Sie sie im Store veröffentlichen und damit der ganzen Welt präsentieren.

![Windows-Geräte](images/1894834-hig-device-primer-01-500.png)
 
##<a name="so-what-exactly-is-a-uwp-app"></a>Was also ist eine UWP-App *genau*?

Was ist das Besondere an einer UWP-App? Dies sind einige der Merkmale, die UWP-Apps unter Windows 10 von anderen Apps unterscheiden.

-   **Es gibt eine gemeinsame API-Oberfläche für alle Geräte.**

    Die zentralen APIs für die Universelle Windows-Plattform (UWP) sind für alle Arten von Windows-Geräten dieselben. Wenn Ihre App nur die zentralen APIs verwendet, wird sie auf jedem Windows10-Gerät ausgeführt, unabhängig davon, ob Sie sie für einen Desktop-PC, eine Xbox oder einen Mixed Reality-Headset entwickeln.

-   **Mithilfe von Erweiterungs-SDKs kann Ihre App auf bestimmten Gerätetypen interessante Aktionen ausführen.**

    Erweiterungs-SDKs fügen jeder Geräteklasse spezielle APIs hinzu. Wenn Ihre UWP-App beispielsweise auf HoloLens ausgerichtet ist, können Sie zusätzlich zu den normalen UWP-Kern-APIs HoloLens-Features hinzufügen.
    Wenn Sie die universellen APIs verwenden, kann Ihr App-Paket auf allen Geräten ausgeführt werden, die Windows10 ausführen. Wenn Ihre UWP-App jedoch gerätespezifische APIs verwenden soll, wenn es auf Geräten einer bestimmten Klasse ausgeführt wird, können Sie zur Laufzeit überprüfen lassen, ob eine API vorhanden ist, bevor sie aufgerufen wird. 

-   **Apps werden im AppX-Paketformat verpackt und über den Store verteilt.**

    Alle UWP-Apps werden als AppX-Paket verteilt. Dies stellt einen vertrauenswürdigen Installationsmechanismus bereit und stellt sicher, dass Ihre Apps problemlos bereitgestellt und aktualisiert werden können.

-   **Es gibt einen Store für alle Geräte.**

    Nach der Registrierung als App-Entwickler können Sie Ihre App an den Store übermitteln und auf für Geräte aller Art oder nur für bestimmte Geräte zur Verfügung stellen. Sie übermitteln und verwalten alle Ihre Apps für Windows-Geräte an einem zentralen Ort.

-   **Apps unterstützen adaptive Steuerelemente und Eingaben**

    Benutzeroberflächenelemente verwenden *effektive Pixel* (siehe [Reaktionsfähiges Design 101 für UWP-Apps](https://msdn.microsoft.com/library/windows/apps/Dn958435)), sodass sie ein Layout zurückgeben können, das auf der Basis der auf dem Gerät verfügbaren Bildschirmpixel funktioniert. Sie funktionieren außerdem mit mehreren Arten von Eingaben, z.B. Tastatur, Maus, Touch, Stift und Xbox One-Controller. Wenn Sie die Benutzeroberfläche auf eine bestimmte Bildschirmgröße oder ein bestimmtes Gerät anpassen müssen, helfen Ihnen neue Layoutbereiche und Tools dabei, die Benutzeroberfläche auf die Geräte anzupassen, auf denen Ihre App möglicherweise ausgeführt wird.



## <a name="use-a-language-you-already-know"></a>Verwenden einer vertrauten Sprache


UWP-Apps verwenden die Windows-Runtime. Dies ist eine native, in das Betriebssystem integrierte API. Diese API ist in C++ implementiert und wird in C#, Visual Basic, C++ und JavaScript unterstützt. Einige Optionen für das Schreiben von Apps in UWP sind:
-   XAML-UI und ein in C#, VB oder C++ geschriebenes Back-End
-   DirectX UI und ein in C++ geschriebenes Back-End
-   JavaScript und HTML

Microsoft Visual Studio 2017 stellt eine Vorlage für UWP-Apps für jede Sprache bereit. Damit können Sie ein einziges Projekt für alle Geräte erstellen. Nachdem Sie Ihre Arbeit abgeschlossen haben, können Sie ein App-Paket erstellen und aus Visual Studio heraus an den Windows Store senden, um die App für Kunden mit beliebigen Windows 10-Geräten bereitzustellen.

## <a name="uwp-apps-come-to-life-on-windows"></a>UWP-Apps entfalten unter Windows ihre Vielseitigkeit


Unter Windows kann Ihre App relevante Infos in Echtzeit für Benutzer bereitstellen, damit sie immer wieder auf die App zugreifen. In der modernen App-Welt mit vielen Konkurrenzprodukten muss Ihre App so attraktiv sein, dass sie von Benutzern gern und häufig genutzt wird. Windows bietet Ihnen viele Ressourcen, mit deren Hilfe Sie erreichen können, dass Benutzer Ihre App immer wieder nutzen:

-   Auf Live-Kacheln und dem Sperrbildschirm werden kontextbezogene, relevante und aktuelle Informationen auf einen Blick sichtbar angezeigt.

-   Pushbenachrichtigungen informieren Benutzer in Echtzeit über wichtige Ereignisse, sobald diese verfügbar sind.

-   Benachrichtigungen und Inhalte, auf die Benutzer reagieren müssen, können Sie im neuen Info-Center organisieren und anzeigen.

-   Hintergrundausführung und Auslöser erwecken Ihre App zum Leben, wenn der Benutzer sie benötigt.

-   Ihre App kann Sprache und Bluetooth LE-Geräte verwenden, um Benutzer bei der Interaktion mit der Welt um sie herum zu unterstützen.

-   Unterstützung für funktionsreiche, digitale Freihandeingaben und das innovative Dial.

-   Cortana fügt Ihrer Software persönliche Züge hinzu.

-   XAML stellt Ihnen die nötigen Tools bereit, um störungsfreie, animierte Benutzeroberflächen zu erstellen.

Schließlich können Sie auch Roamingdaten und das Windows-Schließfach für Anmeldeinformationen nutzen, um auf allen Windows-Bildschirmen, auf denen Benutzer Ihre App ausführen, für eine einheitliche Roamingumgebung zu sorgen. Roamingdaten sind eine einfache Möglichkeit zum Speichern der Präferenzen und Einstellungen von Benutzern in der Cloud, ohne Ihre eigene Infrastruktur für die Synchronisierung erstellen zu müssen. Darüber hinaus können Sie die Anmeldeinformationen von Benutzern im Schließfach für Anmeldeinformationen speichern, wo Sicherheit und Zuverlässigkeit oberste Priorität haben.

##  <a name="monetize-your-app"></a>Monetisieren Ihrer App


Unter Windows können Sie Ihre App nach eigenen Vorstellungen zu Geld machen – für Telefone, Tablets, PCs und andere Geräte. Wir bieten Ihnen verschiedene Möglichkeiten, wie Sie Ihre App und die zugehörigen Dienste zu Geld machen können. Sie müssen nur die für Sie am besten geeignete Methode auswählen:

-   Ein bezahlter Download ist die einfachste Möglichkeit. Geben Sie einfach nur Ihren Preis an.
-   Dank Testversionen können Benutzern Ihre App vor dem Kauf testen. Im Vergleich zu den herkömmlicheren „Freemium“-Optionen kann sie leichter gefunden werden, und die Zahl der Konversionen ist höher.
-   Verwenden Sie Verkaufspreise für Apps und Add-Ons.
-   In-App-Käufe und -Anzeigen sind ebenfalls verfügbar.

## <a name="lets-get-started"></a>Machen Sie die ersten Schritte


Eine ausführlichere Beschreibung der UWP finden Sie unter [Anleitung für Apps für die universelle Windows-Plattform (UWP)](universal-application-platform-guide.md). Navigieren Sie anschließend zu [Vorbereiten](get-set-up.md), um die Tools herunterzuladen, die Sie benötigen, um mit dem Erstellen von Apps zu beginnen, und schreiben Sie [Ihre erste App](your-first-app.md)!


## <a name="more-advanced-topics"></a>Fortgeschrittenere Themen

* [.NET Native - Bedeutung für UWP-Entwickler (Universelle Windows-Plattform)](https://blogs.windows.com/buildingapps/2015/08/20/net-native-what-it-means-for-universal-windows-platform-uwp-developers/#TYsD3tJuBJpK3Hc7.97)
* [Universelle Windows-Apps in .NET](https://blogs.msdn.microsoft.com/dotnet/2015/07/30/universal-windows-apps-in-net)
* [.NET für UWP-Apps](https://msdn.microsoft.com/en-us/library/mt185501.aspx)
