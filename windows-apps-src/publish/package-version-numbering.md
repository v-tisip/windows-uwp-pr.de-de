---
author: jnHs
Description: The Microsoft Store enforces certain rules related to version numbers, which work somewhat differently in different OS versions.
title: Paketversionsnummern
ms.assetid: DD7BAE5F-C2EE-44EE-8796-055D4BCB3152
ms.author: wdg-dev-content
ms.date: 10/02/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 7cf93cf06b273605b91c31da5b6a6b8cef8dae39
ms.sourcegitcommit: 9354909f9351b9635bee9bb2dc62db60d2d70107
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2018
ms.locfileid: "4679827"
---
# <a name="package-version-numbering"></a>Paketversionsnummern

Jedes von Ihnen bereitgestellte Paket muss eine Versionsnummer aufweisen (als Wert im **Version** -Attribut des **Package/Identity**-Elements im App-Manifest). Der Microsoft Store erzwingt bestimmte Regeln, die im Zusammenhang mit Versionsnummern auftreten, die in verschiedenen Betriebssystemversionen unterschiedlich funktionieren.

> [!NOTE]
> In diesem Thema bezieht sich auf "Pakete", aber nicht anders angegeben, gelten die gleichen Regeln für Versionsnummern für.msix/.appx und.msixbundle/.appxbundle-Dateien.


## <a name="version-numbering-for-windows-10-packages"></a>Versionsnummern für Windows 10-Pakete

> [!IMPORTANT]
> Für Pakete, Windows 10 (UWP) der letzte (vierte) Abschnitt der Versionsnummer ist für die Verwendung des Store reserviert und muss 0 bleiben, wenn Sie Ihr Paket (der Store den Wert in diesem Abschnitt erstellen kann jedoch ändern).

Wenn eine UWP-Paket aus der veröffentlichten Übermittlung auswählen, verwendet den Microsoft Store immer das Paket mit der höchsten Versionsnummer, der für Windows 10 das Kundengerät gilt. Dadurch sind Sie flexibler und haben die Kontrolle darüber, welche Pakete Kunden auf bestimmten Gerätetypen bereitgestellt werden. Außerdem können Sie diese Pakete in beliebiger Reihenfolge übermitteln; Sie sind nicht darauf beschränkt, bei nachfolgenden Übermittlungen Pakete mit höheren Versionsnummern bereitzustellen.

Sie können mehrere UWP-Pakete mit der gleichen Versionsnummer bereitstellen. Pakete mit der gleichen Versionsnummer können jedoch nicht dieselbe Architektur aufweisen, da die vollständige Identität eindeutig sein muss, die der Store für die einzelnen Pakete verwendet. Weitere Informationen finden Sie unter [**Identity**](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-identity).

Wenn Sie mehrere UWP-Pakete, die die gleichen Versionsnummer verwenden bereitstellen, wird die Architektur (in der Reihenfolge X64, x 86, ARM, Neutral) verwendet werden, um zu entscheiden, welche höheren Rang besitzt (wenn der Store für auf dem Gerät eines Kunden bereitzustellenden Pakete bestimmt). Beim Bewerten von App-Bündeln mit gleicher Versionsnummer gilt der höchste Architekturrang im Bündel: ein App-Bündel, das ein x64-Paket enthält, besitzt einen höheren Rang als ein App-Bündel, das lediglich ein x86-Paket enthält.

Dies bietet Ihnen ein hohes Maß an Flexibilität, um Ihre App im Laufe der Zeit weiterzuentwickeln. Sie können hochladen und übermitteln neue Pakete, die niedrigere Versionsnummern zu verwenden, um Unterstützung für Windows 10-Geräte hinzuzufügen, die Sie zuvor nicht unterstützt haben, können Sie höheren Versionsnummern Pakete, die strengeren Abhängigkeiten von Hardware- oder Betriebssystem-Features nutzen hinzufügen kann Pakete höheren Versionsnummern hinzufügen, die für einige oder alle Ihrer vorhandenen Kunden als Aktualisierungen dienen.

Das folgende Beispiel veranschaulicht, wie Versionsnummern verwaltet werden können, um Ihren Kunden über mehrere Übermittlungen die beabsichtigten Pakete bereitzustellen.

### <a name="example-moving-to-a-single-package-over-multiple-submissions"></a>Beispiel: Wechsel zu einem einzelnen Paket über mehrere Übermittlungen

Mit Windows 10 können Sie eine einzelne Codebasis schreiben, die überall ausgeführt werden kann. Dadurch wird das Starten eines neuen plattformübergreifenden Projekts sehr viel einfacher. Wegen einer Reihe von Gründen möchten Sie jedoch vielleicht die vorhandene Codebasis nicht zusammenführen, um direkt ein einzelnes Projekt zu erstellen.

Sie können die Paket-Versionsnummernregeln verwenden, um den Wechsel Ihrer Kunden nach und nach auf ein einzelnes Paket für die universellen Gerätefamilie vorzunehmen. Dabei werden eine Reihe von vorläufigen Aktualisierungen für bestimmte Gerätefamilien (einschließlich derjenigen, die die Windows 10-APIs nutzen) bereitgestellt. Im folgenden Beispiel wird veranschaulicht, wie die gleichen Regeln über eine Reihe von Übermittlungen für dieselbe app konsistent angewendet werden.

| Übermittlung | Inhalt                                                  | Benutzerfreundlichkeit                                                                                                                                                                             |
|------------|-----------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1          | -   Paketversion: 1.1.10.0 <br> -   Gerätefamilie: Windows.Desktop, minVersion 10.0.10240.0 <br> <br> -   Paketversion: 1.1.0.0 <br> -   Gerätefamilie: Windows.Mobile, minVersion 10.0.10240.0     | -   Geräte unter Windows 10 Desktop Build 10.0.10240.0 und höher erhalten Versionsnummer 1.1.10.0 <br> -   Geräte unter Windows 10 Mobile Build 10.0.10240.0 und höher erhalten Versionsnummer 1.1.0.0 <br> -   Für andere Gerätefamilien kann die App nicht erworben und installiert werden. |
| 2          | -   Paketversion: 1.1.10.0 <br> -   Gerätefamilie: Windows.Desktop, minVersion 10.0.10240.0 <br> <br> -   Paketversion: 1.1.0.0 <br> -   Gerätefamilie: Windows.Mobile, minVersion 10.0.10240.0 <br> <br> -   Paketversion: 1.0.0.0 <br> -   Gerätefamilie: Windows.Universal, minVersion 10.0.10240.0    | -   Geräte unter Windows 10 Desktop Build 10.0.10240.0 und höher erhalten Versionsnummer 1.1.10.0 <br> -   Geräte unter Windows 10 Mobile Build 10.0.10240.0 und höher erhalten Versionsnummer 1.1.0.0 <br> -   Andere (nicht-Desktop, nicht mobile) Gerätefamilien, erhalten nach Einführung Versionsnummer 1.0.0.0 <br> -   Bei Desktop- und mobilen Geräten, auf denen die App bereits installiert ist, wird kein Updates angezeigt (da diese bereits die beste verfügbare Version besitzen – 1.1.10.0 und 1.1.0.0 sind beide höher als 1.0.0.0) |
| 3          | -   Paketversion: 1.1.10.0 <br> -   Gerätefamilie: Windows.Desktop, minVersion 10.0.10240.0 <br> <br> -   Paketversion: 1.1.5.0 <br> -   Gerätefamilie: Windows.Universal, minVersion 10.0.10250.0 <br> <br> -   Paketversion: 1.0.0.0 <br> -   Gerätefamilie: Windows.Universal, minVersion 10.0.10240.0    | -   Geräte unter Windows 10 Desktop Build 10.0.10240.0 und höher erhalten Versionsnummer 1.1.10.0 <br> -   Geräte unter Windows 10 Mobile Build 10.0.10250.0 und höher erhalten Versionsnummer 1.1.5.0 <br> -   Geräte unter Windows 10 Mobile Build >= 10.0.10240.0 und < 10.010250.0 erhalten Versionsnummer 1.1.0.0 
| 4          | -   Paketversion: 2.0.0.0 <br> -   Gerätefamilie: Windows.Universal, minVersion 10.0.10240.0   | -   Alle Kunden mit allen Gerätefamilien unter Windows 10 Build v10.0.10240.0 und höher erhalten Paket 2.0.0.0 | 

> [!NOTE]
>  In allen Fällen erhalten Kundengeräte das Paket mit der höchsten Versionsnummer, für die sie sich qualifizieren. In der dritten Übermittlung oben erhalten beispielsweise alle Desktopgeräte v1.1.10.0, auch wenn sie die Betriebssystemversion 10.0.10250.0 oder höher haben und somit auch mit v1.1.5.0 kompatibel wären. Da 1.1.10.0 für sie die höchsten Versionsnummer ist, erhalten sie dieses Paket.

### <a name="using-version-numbering-to-roll-back-to-a-previously-shipped-package-for-new-acquisitions"></a>Verwenden der Versionsnummern zum Durchführen eines Rollbacks auf ein vorheriges Paket für Neuanschaffungen

Wenn Sie Kopien Ihrer Pakete beibehalten, müssen Sie die Option zum Zurücksetzen von Ihrer app-Paket im Store auf ein früheres Windows 10-Paket, wenn Sie Probleme mit einer Version haben soll. Dies ist eine temporäre Möglichkeit, um die Unterbrechung für Ihre Kunden zu begrenzen, während Sie Zeit für das Problem zu beheben.

Zu diesem Zweck erstellen Sie eine neue [Übermittlung](app-submissions.md). Entfernen Sie das problematische Paket und laden Sie das alte Paket hoch, das Sie im Store bereitstellen möchten. Kunden, die bereits das Paket erhalten haben, für das Sie einen Rollback durchführen, weisen immer noch das problematische Paket auf (da das ältere Paket eine frühere Versionsnummer besitzt). Dadurch wird verhindert, dass jemand das problematische Paket erhält, und die App ist im Store weiterhin verfügbar.

Um das Problem für den Kunden zu beheben, die das problematische Paket bereits erhalten haben, können Sie ein neues Windows 10-Paket übermitteln, das eine höhere Versionsnummer aufweist als die fehlerhafte Paket verfügt, so früh wie möglich. Danach durchläuft die Übermittlung den Zertifizierungsprozess, und alle Kunden werden auf das neue Paket aktualisiert, da es eine höhere Versionsnummer aufweist.


## <a name="version-numbering-for-windows-81-and-earlier-and-windows-phone-81-packages"></a>Versionsnummern für Windows 8.1 (und früher) und Windows Phone 8.1-Pakete

Bei APPX-Paketen für Windows Phone 8.1-Pakete muss die Versionsnummer des Pakets in einer neuen Übermittlung immer höher sein als die des in der letzten Übermittlung (oder vorherigen Übermittlung) enthaltenen Pakets.

Bei APPX-Paketen für Windows 8 und Windows 8.1 gilt die gleiche Regel pro Architektur: die Versionsnummer des Pakets in einer neuen Übermittlung muss immer höher sein als die des zuletzt im Store veröffentlichten Pakets für dieselbe Architektur.

Außerdem muss die Versionsnummer von Windows 8.1-Paketen stets höher sein als die Versionsnummern aller Windows 8-Pakete für dieselbe App. Mit anderen Worten: Die Versionsnummer eines von Ihnen übermittelten Windows 8-Pakets muss niedriger sein als die Versionsnummer eines Windows 8.1-Paket, das Sie für dieselbe App übermittelt haben.

> [!NOTE]
> Wenn Ihre app auch Windows 10-Pakete enthält, muss die Versionsnummer des Windows 10-Pakete höher sein als die für Windows 8, Windows 8.1 und/oder Windows Phone 8.1-Pakete werden. Weitere Informationen finden Sie unter [Hinzufügen von Paketen für Windows 10 zu einer zuvor veröffentlichten App](guidance-for-app-package-management.md#adding-packages-for-windows-10-to-a-previously-published-app).

Hier sind einige Beispiele für abweichende Nummer Update für Pakete, die für Windows 8 und Windows 8.1 Aktualisierungsszenarios.

| Version der App im Store  | Hochgeladene Version | Nachdem die neue Version in den Store hochgeladen wurde, wird sie als Neukauf installiert. | Nachdem die neue Version in den Store hochgeladen wurde, wird sie aktualisiert, wenn der Kunde die App bereits besitzt. |
|---------------------------------------------|-----------------------------|--------------------------------------------------------------------------------------------|----------|
| Nichts                                     | x86, v1.0.0.0               | x86, v1.0.0.0 auf x86- und x64-PCs                                                | Nichts. |
| x86, v1.0.0.0                               | x64, v1.0.0.0               | v1.0.0.0 für die Architektur des Kunden                                                   | Nichts. Die Versionsnummern sind identisch. |
| x86, v1.0.0.0 <br> x64, v1.0.0.0            | x64, v1.0.0.1               | v1.0.0.0 für Kunden mit einem x86-PC <br> v1.0.0.1 für Kunden mit einem x64-PC                 | Nichts für Kunden, die die App auf einem x86-PC ausführen. <br> v1.0.0.0 wird für Kunden, die die App auf einem x64-PC ausführen, auf v1.0.0.1 aktualisiert. <br> **Hinweis**  Wenn die x86-Version der App auf einem x64-Computer ausgeführt wird, wird die App erst auf die x64-Version aktualisiert, wenn der Kunde die App deinstalliert und wieder neu installiert. |
| Nichts                                     | Neutral, v1.0.0.1           | Neutral, v1.0.0.1 auf allen PCs                                                         | Nichts. |
| Neutral, v1.0.0.1                           | x86, v1.0.0.0 <br> x64, v1.0.0.0 <br> ARM, v1.0.0.0 | v1.0.0.0 für die Architektur des PC des Kunden.          | Nichts. Kunden mit der neutralen Version v1.0.0.1 verwenden weiter diese Version der App. |
| Neutral, v1.0.0.1 <br> x86, v1.0.0.0 <br> x64, v1.0.0.0 <br> ARM, v1.0.0.0 | x86, v1.0.0.1 <br> x64, v1.0.0.1 <br> ARM, v1.0.0.1 | v1.0.0.1 für die Architektur des PC des Kunden. | Nichts für Kunden mit der neutralen Version v1.0.0.1. <br> v1.0.0.0 wird für Kunden, die die Version v1.0.0.0 der App für die spezifische Architektur ihres PC verwenden, auf v1.0.0.1 aktualisiert. |
| x86, v1.0.0.1 <br> x64, v1.0.0.1 <br> ARM, v1.0.0.1 | x86, v1.0.0.2 <br> x64, v1.0.0.2 <br> ARM, v1.0.0.2 | v1.0.0.2 für die Architektur des PC des Kunden.  | v1.0.0.1 wird für Kunden, die die Version v1.0.0.1 der App für die spezifische Architektur ihres PC verwenden, auf v1.0.0.2 aktualisiert. |

> [!NOTE]
> Im Gegensatz zu APPX-Paketen werden die Versionsnummern in allen XAP-Paketen beim Ermitteln der für einen gegebenen Kunden bereitzustellenden Pakete ignoriert. Um ein Kunde von einem XAP-Paket auf ein neueres zu aktualisieren, stellen Sie sicher, dass die ältere XAP-Datei in der neuen Übermittlung entfernt wird.
