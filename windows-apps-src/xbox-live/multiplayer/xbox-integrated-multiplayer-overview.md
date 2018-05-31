---
title: Xbox Integrated Multiplayer (Übersicht)
author: KevinAsgari
description: Erfahren Sie mehr über Xbox Integrated Multiplayer (XIM), eine All-in-One-Lösung für Multiplayer/Netzwerk/Chats für Xbox Live-Spiele.
ms.assetid: edbb28e6-1b6c-4f12-a9c6-fa8961de99a8
ms.author: kevinasg
ms.date: 04/04/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Xbox Live, Xbox, Spiele, UWP, Windows10, Xbox One
ms.localizationpriority: medium
ms.openlocfilehash: 5af9a5c386dc620c19183747750081ea1bd5a66d
ms.sourcegitcommit: db09dcb08da5995c46c2729896e56be3774ee5ba
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2018
ms.locfileid: "1563394"
---
# <a name="xbox-integrated-multiplayer-overview"></a>Xbox Integrated Multiplayer (Übersicht)

 Xbox Integrated Multiplayer (XIM) ist eine eigenständige Schnittstelle zum einfachen Hinzufügen von Echtzeitfunktionen für Multiplayernetzwerke und Chatkommunikation zu Ihrem Spiel, die auf den leistungsstarken Xbox Live-Diensten aufbaut. Die Schnittstelle basiert auf einigen wichtigen Schlüsselkonzepten:

 - **XIM-Netzwerk** – Eine logische Darstellung einer Reihe verbundener Benutzer, die an einer bestimmten Multiplayererfahrung teilnehmen, sowie ein grundlegender Zustand, der diese Ansammlung beschreibt. Die Teilnehmer können sich jeweils nur in einem XIM-Netzwerk befinden, Sie können jedoch problemlos von einem konzeptionellen XIM-Netzwerk in ein anderes wechseln.
 - `xim_player` – Ein Objekt, das einen einzelnen menschlichen Benutzer repräsentiert, der auf einem lokalen oder Remotegerät angemeldet ist und an einem XIM-Netzwerk teilnimmt. Ein einzelner physischer Benutzer, der dem gleichen XIM-Netzwerk beitritt, es verlässt und wieder beitritt wird als zwei separate Spielerinstanzen angesehen.
 - `xim_authority` – Ein Objekt, das eine einzelne Einheit mit der Berechtigung und der Verantwortung zur Verwaltung einer konsistenten Ansicht eines spielspezifischen Zustands in einem XIM-Netzwerk repräsentiert. Die Verwendung dieses Objekts ist optional. Die Funktionalität steht auch derzeit in dieser Version nicht zur Verfügung.
 - `xim_state_change` – Eine Struktur, die eine Benachrichtigung auf dem lokalen Gerät in Bezug auf eine asynchrone Änderung einiger Aspekte des XIM-Netzwerk repräsentiert.
 - `xim::start/finish_processing_state_changes` – Das Methodenpaar, das bei jedem UI-Frame von der App aufgerufen wird, um asynchrone Vorgänge auszuführen, um die Ergebnisse in Form von `xim_state_change`-Strukturen abzurufen und um die verbundenen Ressourcen nach Abschluss wieder freizugeben.
 - **Spielersuche** – Optionaler Prozess zum Ermitteln weiterer Remotespieler mit ähnlichen Interessen oder Fertigkeitsstufen zur Teilnahme an einem XIM-Netzwerk, ohne dass dafür eine soziale Beziehung vorhanden sein muss.

Auf sehr hoher Ebene verwendet die App die Bibliothek, um Sie eine Reihe von Benutzern auf dem lokalen Gerät zu konfigurieren, die als neue Spieler in einer XIM-Netzwerk verschoben werden. Da App-Instanzen auf Remotegeräten dasselbe mit ihren eigenen Benutzern ausführen und jeder kontinuierliche Start+Abschluss-Verarbeitungszustand jedes UI-Frame ändert, erhält jede teilnehmende Instanz `xim_state_change`-Updates, die die lokalen und Remote-`xim_player` beschreiben, die dem-XIM Netzwerk beitreten.

Innerhalb des XIM-Netzwerks kann die App eigene spielspezifische Datennachrichten senden, z.B. Avatar-Bewegungsupdates. Diese können an andere Spieler oder eine `xim_authority` gerichtet sein, die automatisch für eines der beteiligten Geräte ausgewählt wurde (basierend auf der besten Netzwerkqualität, Stabilität, Reputation des Spielers und anderen Faktoren), sodass die App auf diesem `xim_authority`-Gerät Nachrichten an Spieler senden kann, die in der Regel für die Netzwerkeffizienz und Konfliktvermeidung gebündelt werden. Alle empfangenen Nachrichten werden an die App als ein `xim_state_change` übermittelt, der die gewünschte Quelle und die lokalen Ziele anzeigt.

Sprach- und Text-Chat-Kommunikation wird automatisch auch für alle Spieler bereitgestellt, sofern die Einstellungen für Datenschutz und die App-Konfiguration dies zulassen. Für Spieler, bei denen Sprache-zu-Text- oder Text-zu-Sprache-Konvertierung aktiviert ist, führt XIM diese Übersetzung transparent aus, sodass Chat-Textnachrichten gesendet werden, die die eingehenden Sprachaudio-Nachrichten darstellen, sowie Sprachsynthese-Audio für ausgehende Chat-Textnachrichten.

Wenn ein Spieler seine Teilnahme am XIM-Netzwerk beendet (selbst ausgelöst oder aufgrund von Netzwerkverbindungsproblemen), werden `xim_state_change`-Updates an alle App-Instanzen bereitgestellt, dass der `xim_player` das Netzwerk verlassen hat. Wenn das als `xim_authority` ausgewählte Gerät das Netzwerk verlässt, werden die App-Instanzen auf ähnliche Weise darüber informiert, dass die Autorität sich wegbewegt hat, und eine „Abstimmung“ zu allen spielspezifischen Zuständen wird gestartet, indem ein optionaler Datenpuffer für die Ersatz- `xim_authority` bereitgestellt wird, sodass eine Neusynchronisierung stattfinden kann. Die neue Autorität kann diese Abstimmungsdaten aller Spieler nach Bedarf auswerten und wiederum einen „abgestimmten“ Datenpuffer wieder an alle Spieler zurücksenden, um die Autoritätsbewegung und die erneute Synchronisierung abzuschließen. Dasselbe grundlegende Abstimmungsverfahren wird auch neu teilnehmenden Geräten angeboten, sodass die Autorität auf einfache Weise den aktuellen Spielstatus der Autorisierung bereitstellen kann, wenn die Spieler das XIM-Netzwerk betreten, ohne dass dafür zusätzlicher Code erforderlich ist. Beachten Sie, dass Zustandsänderungen der Autorität in dieser Softwareversion derzeit nicht bereitgestellt werden.

Eine App kann auf verschiedene Weisen das XIM-Netzwerk erkennen, an dem teilgenommen werden soll. Häufig starten die Apps, indem sie lokale Benutzer in ein neues Netzwerk automatisch verschieben, das den Freunden des Benutzers zur Verfügung steht, wobei die lokalen Benutzer Einladungen senden können oder das XIM-Netzwerk als Teilnahmeaktivität anzeigen lassen können (z. B. über Spielerkarten). Nachdem diese über Social Media ermittelten Benutzer bereit sind, kann die App den „Spielersuche“-Prozess von Xbox Live initiieren und alle Spieler in ein neues XIM-Netzwerk verschieben, das auch zusätzliche „abgestimmte“ Remotespieler für Teams und nach Bedarf Gegnerteams enthält. Nach Abschluss dieses Multiplayererlebnisses können die App-Instanzen ihre lokalen Spieler – und optional auch die ursprünglichen Remotespieler vor der Spielersuche – in ein neues privates XIM-Netzwerk oder in ein anderes zufällig über die Spielersuche gefundenes XIM-Netzwerk verschieben. Sprach- und Text-Chat bleiben die ganze Zeit verfügbar. Dieses einfache Verschieben von Spielern zwischen XIM-Netzwerken ist ein zentraler Bestandteil der API und reflektiert die heutigen Erwartungen an gute und hochentwickelte SocialGaming-Erfahrungen.

Informationen zu den ersten Schritten finden Sie unter [Verwenden von XIM](xbox-integrated-multiplayer/using-xim.md).

## <a name="xims-relationship-to-other-modules"></a>Beziehungen von XIM zu anderen Modulen

XIM dient zur Bereitstellung einer komfortablen All-in-One-Schnittstelle für Spiele mit grundlegenden Multiplayeranforderungen. XIM kapselt die Funktionalität mehrerer Module – insbesondere des `multiplayer_manager`-Moduls der Xbox Services API (XSAPI), der `Microsoft::Xbox::GameChat` -Bibliothek und der sicheren Multiplayer-Netzwerke von `Windows::Networking::XboxLive` – in einer einzelnen optimierten API. Dadurch wird die typische Menge an Code, Aufgaben und Konzepten beim Erstellen von Multiplayerspielen reduziert, bei denen nicht absolut maximale Flexibilität oder Kontrolle erforderlich ist. Apps, deren Anforderungen nicht mit den vereinfachenden Annahmen der XIMs übereinstimmen, sollten diese Komponenten stattdessen jedoch direkt verwenden.

Auch wenn XIM dazu gedacht ist, den Verwaltungsbedarf für Elemente wie Multiplayer Session Directory (MPSD)-Sitzungsdokumente oder den Netzwerktransport über die zugrunde liegenden Komponenten zu vermeiden, schließt dies nicht die gleichzeitige oder Side-by-Side-Nutzung als Teil einer separaten Spielergruppe oder eines Kommunikationsnetzwerks aus. In diesem Fall liegt es in der Verantwortung der App, eine kooperative Netzwerkressourcenauslastung zwischen XIM und den eigenen Mechanismen sicherzustellen. XIM unterstützt derzeit „Out-of-Band-Reservierungen“, um die Verwendung als dedizierte Chat-Lösung zu erleichtern, deren Benutzerliste ausschließlich durch externe Eingabe gesteuert wird.

Xbox Live bietet viele weitere Features, die nützlich für Multiplayerspiele, jedoch weniger direkt an der Einrichtung von Multiplayerchat und Netzwerkkommunikation beteiligt sind, und die daher nicht in diesem Modul einbezogen werden. Apps sollten in der Xbox Services API (XSAPI) nach Spielerfeedback, Erfolgen, Ranglisten, Speicher und mehr suchen.


## <a name="using-xim-as-a-dedicated-chat-solution-via-out-of-band-reservations"></a>Verwenden von XIM als dedizierte Chatlösung über Out-of-Band-Reservierungen

Die meisten Apps verwenden XIM, um jeden Aspekt der Zusammenführung der Spieler zu verarbeiten. Bei „Xbox Integrated Multiplayer“ liegt der Schwerpunkt nicht zuletzt auf der Unterstützung allgemeiner End-to-End-Multiplayerszenarien. Einige Apps, die ihre eigenen dedizierten Netzwerklösungen mit Internetservern implementieren, profitieren jedoch auch von den Vorteilen der Zuverlässigkeit und der geringen Latenz der kostengünstige Peer-to-Peer-Chatkommunikation. XIM erkennt dies unterstützt derzeit einen Erweiterungsmodus, durch den vereinfachte Peerkommunikation zur Verbesserung der externen Spielerverwaltung außerhalb der XIM-API genutzt wird.

> Eine ausführliche Dokumentation zur Verwendung von XIM über Out-of-Band-Reservierungen finden Sie unter [XIM-Reservierungen](xbox-integrated-multiplayer/xim-reservations.md).
