---
author: TylerMSFT
title: Bauen Sie Ihre App mit Diensten, Erweiterungen und Paketen aus
description: Hier erfahren Sie, wie Sie eine Hintergrundaufgabe erstellen, die ausgeführt wird, wenn die Store-App Ihrer Universellen Windows-Plattform (UWP) aktualisiert wird.
ms.author: twhitney
ms.date: 05/21/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, erweitern, aufschlüsseln, App-Dienst, Paket, Erweiterung
ms.localizationpriority: medium
ms.openlocfilehash: 2721f9d8f768cabb0e07c0cd2cfcfcbf9255cd70
ms.sourcegitcommit: 6618517dc0a4e4100af06e6d27fac133d317e545
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
ms.locfileid: "1689616"
---
# <a name="extend-your-app-with-services-extensions-and-packages"></a>Bauen Sie Ihre App mit Diensten, Erweiterungen und Paketen aus

In Windows 10 stehen Ihnen verschiedene Technologien zur Verfügung, um Ihre App zu erweitern und aufzuschlüsseln. Anhand der nachfolgenden Tabelle können Sie ermitteln, welche Technologie für Ihr Szenario die richtige ist. Anschließend finden Sie eine kurze Beschreibung der jeweiligen Szenarien und Technologien.


| Szenario                           | Ressourcenpaket | Optionales Paket | App-Erweiterung    | App-Dienst      | Streaming installieren |
|------------------------------------|:----------------:|:----------------:|:----------------:|:----------------:|:-----------------:|
| Drittanbieter Code-Plugins            |                  |                  | :heavy_check_mark: |                  |                   |
| In-Process Code-Plugins              |                  | :heavy_check_mark: |                  |                  |                   |
| UX-Ressourcen (Zeichenfolgen/Images)         | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                  | :heavy_check_mark: |
| On-Demand Inhalte <br/> (z. B. zusätzliche Spielstufen) |    | :heavy_check_mark: | :heavy_check_mark: |                  | :heavy_check_mark: |
| Separate Lizenzierung und Erwerb |                  | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                   |
| In-App-Erwerb                 |                  | :heavy_check_mark: | :heavy_check_mark: |                  |                   |
| Optimierung der Installationszeit              | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |                  | :heavy_check_mark: |

## <a name="scenario-descriptions-rows-in-the-table"></a>Beschreibungen der Szenarien (Zeilen der Tabelle)

**Drittanbieter-Plugins**  

Code, der im Store zum Herunterladen bereitsteht und den Sie über Ihre App ausführen können. Beispielsweise Erweiterungen für den Microsoft Edge-Browser.

**In-Process Code-Plugins**  

Code, der In-Process von Ihrer App ausgeführt wird. Nur C++ wird unterstützt. Kann auch Inhalte enthalten. Da der Code In-Process ausgeführt wird, wird von einem höheren Maß an Vertrauen ausgegangen. Es ist ratsam, diese Art der Erweiterbarkeit nicht auf Drittanbieter anzuwenden.

**UX-Ressourcen (Zeichenfolgen/Bilder)**  

Ressourcen der Benutzeroberfläche wie lokalisierte Zeichenfolgen, Bilder sowie jegliche andere UI-Inhalte, die Sie aufgrund der Sprachumgebung oder anderen Gründen einbeziehen möchten.

**On-Demand Inhalte**  

Inhalte, die Sie zu einem späteren Zeitpunkt herunterladen möchten. Beispielsweise In-App-Einkäufe, die Ihnen ermöglichen, neue Spielstufen, Designs oder Funktionen herunterzuladen.

**Separate Lizenzierung und Erwerb**  

Die Fähigkeit den Inhalt unabhängig von der App zu lizenzieren und zu erwerben.

**In-App-Erwerb**  

Gibt an, ob eine Unterstützung seitens des Programms vorhanden ist, die Inhalte App-intern zu erwerben.

**Optimierung der Installationszeit**

Stellt Funktionen zur Verfügung, die die benötigte Zeit verringern, um die App aus dem Store herunterzuladen und diese zu starten.

## <a name="technology-descriptions-columns-in-the-table"></a>Beschreibung der Technologien (Spalten der Tabelle)

**Ressourcenpaket**

Bei Ressourcenpaketen handelt es sich um an die Ressource gebundene Pakete, die Ihrer App eine Anpassung an zahlreiche Bildschirmgrößen und Systemsprachen ermöglichen. Das Ressourcenpaket zielt auf die Benutzersprache, die Systemskalierung sowie die DirectX-Funktionen ab und erlaubt der App dadurch eine Anpassung an zahlreiche Nutzerszenarien. Obwohl ein App-Paket mehrere Ressourcen enthalten kann, wird das Betriebssystem nur die für das Gerät des Benutzers notwendigen Ressourcen herunterladen. Dies spart Bandbreite und Festplattenspeicher.

**Optionales Paket**

Optionale Pakete dienen entweder der Ergänzung oder Erweiterung der Originalfunktionsweise eines App-Pakets. Es ist möglich, eine App zu veröffentlichen und die optionalen Pakete zu einem späteren Zeitpunkt zu veröffentlichen oder sowohl die App als auch die optionalen Pakete gleichzeitig zu veröffentlichen. Die Erweiterung Ihrer App um optionale Pakete hat zum Vorteil, dass Sie Inhalte als separates App-Paket verbreiten und vermarkten können. Optionale Pakete werden in der Regel vom ursprünglichen App-Entwickler entwickelt, da diese über die Identität der Haupt-App (im Gegensatz zu App-Erweiterungen) ausgeführt werden. Je nach Definition Ihres optionalen Pakets können Sie Code, Ressourcen oder Code und Ressourcen Ihres optionalen Pakets in Ihre Haupt-App laden. Wenn Sie Ihre App um Inhalte erweitern möchten, die separat vermarktet, lizenziert und verteilten werden können, sind optionale Pakete unter Umständen die richtige Wahl für Sie. Einzelheiten zur Implementierung, finden Sie unter [Optionale Pakete und die Erstellung zugehöriger Sets](https://docs.microsoft.com/windows/uwp/packaging/optional-packages).

**App-Erweiterung**

Durch [App-Erweiterungen](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appextensions) kann Ihre UWP-App Inhalte hosten, die von anderen UWP-Apps bereitgestellt werden. Sie können auf schreibgeschützte Inhalte dieser Apps zugreifen sowie diese ermitteln und enumerieren.

Wenn eine App Erweiterungen unterstützt, kann jeder beliebige Entwickler Erweiterungen für diese App übermitteln. Daher bedarf es einer soliden Host-App, um Erweiterungen zu laden, die zuvor nicht mit dieser getestet wurde. Erweiterungen sollten als nicht vertrauenswürdig eingestuft werden.

Anwendungen können Code aus Erweiterungen nicht laden. Wenn Sie die Ausführung von Code benötigen, sollten Sie App-Dienste in Erwägung ziehen.

**App-Dienst**

Windows-App-Dienste aktivieren die App-zu-App-Kommunikation, indem sie Ihrer UWP-App erlauben, anderen Universellen Windows-Apps Dienste bereitzustellen. App-Dienste ermöglichen Ihnen, Dienste ohne UI zu erstellen, die von Apps auf demselben Gerät aufgerufen werden können. Ab Windows 10, Version 1607 ist dies auch für Remote-Geräte möglich. Weitere Einzelheiten finden Sie unter [App-Service erstellen und verwenden](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).

App-Dienste sind UWP-Apps, die Dienste für andere UWP-Apps bereitstellen. Sie entsprechen Webdiensten auf einem Gerät. Ein App-Dienst wird als Hintergrundaufgabe in der Host-App ausgeführt und kann seine Dienste auch anderen Apps bereitstellen. Beispielsweise kann der Barcode-Scanner eines App-Dienstes auch anderen Apps nützlich sein. Oder möglicherweise verfügt eine Enterprise-Suite von Apps über einen gemeinschaftlichen App-Dienst für die Rechtschreibprüfung, der auch den anderen Apps in der Suite zur Verfügung steht.

**UWP-App-Streaming installieren**

Die Installierung von Streaming ermöglicht Ihnen die Optimierung der Art und Weise, wie Ihre App Benutzern bereitgestellt wird. Anstatt darauf warten zu müssen, dass die gesamte App heruntergeladen ist, bevor sie verwenden werden kann, können Benutzer bereits mit der App interagieren, sobald ein notwendiger Teil heruntergeladen wurde. Es obliegt Ihnen, als Entwickler, Ihre App entsprechend in einen für die primäre Aktivierung und Initialisierung erforderlichen Bereich sowie einen Bereich für die restlichen Inhalte der App zu gliedern. Weitere Informationen sowie Einzelheiten zur Implementierung finden Sie unter [UWP-App-Streaming installieren](https://docs.microsoft.com/windows/uwp/packaging/streaming-install).

## <a name="see-also"></a>Weitere Informationen

[Erstellen und Verwenden eines App-Dienstes](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)  
[Optionale Pakete und die Erstellung zugehöriger Sets](https://docs.microsoft.com/windows/uwp/packaging/optional-packages)  
[Namensraum von Windows.ApplicationModel.Extensions](https://docs.microsoft.com/uwp/api/windows.applicationmodel.appextensions)  
[UWP-App-Streaming installieren](https://docs.microsoft.com/windows/uwp/packaging/streaming-install)  
[Namensraum von Windows.ApplicationModel.AppService](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.AppService)    
