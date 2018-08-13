---
author: v-angraf
title: Neuigkeiten für UWP auf Xbox One
description: Vorstellung neuer Features für UWP-Apps auf Xbox One.
ms.author: v-angraf
ms.date: 03/29/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.assetid: fe63c527-8f06-43a5-868f-de909f5664b3
ms.localizationpriority: medium
ms.openlocfilehash: cbabe9d31b5b9762320df8e4a92d19ae4e33497d
ms.sourcegitcommit: 897a111e8fc5d38d483800288ad01c523e924ef4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "301460"
---
# <a name="whats-new-for-developers-in-the-latest-update-of-uwp-on-xbox-one"></a>Neuigkeiten für Entwickler in der neuesten Aktualisierung von UWP auf Xbox One

Das neueste Update von universellen Windows Plattform (UWP) auf einem Xbox enthält die folgenden neuen Features auf vorhandenen Features und Fehlerbehebungen Updates.

## <a name="x86-apps-and-games-are-no-longer-supported-on-xbox"></a>X86 apps und Spiele werden auf der Xbox nicht mehr unterstützt  
Xbox unterstützt die Entwicklung von x86 Apps oder deren Übermittlung an den Store nicht mehr.

## <a name="apps-can-now-support-navigating-back-to-the-previous-app"></a>Apps unterstützen nun wieder zur vorherigen app navigieren 
UWP auf eine Xbox apps unterstützen jetzt wieder auf den vorherigen app navigieren. Zu diesem Zweck abonnieren Sie das [**Windows.UI.Core.SystemNavigationManager.BackRequested**](https://msdn.microsoft.com/library/windows/apps/dn893595) -Ereignis, und legen Sie die **bearbeitete** -Eigenschaft auf **false** im Ereignishandler.

> [!NOTE]
> Diese Funktion ist aus Gründen der Kompatibilität nur für apps, die mit der neuesten Version von UWP auf Xbox One integriert sind verfügbar. 

## <a name="dev-home-is-now-the-default-home-experience-on-development-consoles"></a>Dev Home ist jetzt standardmäßig die private auf Entwicklung Konsolen
Entwicklung Konsolen starten Dev Home jetzt als die standardmäßige home Erfahrung. Auf diese Weise können Sie rechts, ohne die Notwendigkeit, die im Einzelhandel Startbildschirm durch Klicken arbeiten möchten. Dev Home enthält nun eine schnelle Aktion um im Einzelhandel Startbildschirm zu starten. Darüber hinaus kann eine neue Einstellung Sie standardmäßig Einzelhandel (privat). 

## <a name="new-dev-home-user-interface"></a>Neue Dev Home-Benutzeroberfläche
Die Benutzeroberfläche Dev Home enthält nun die folgenden erweiterten Funktionen:
 - Wichtige Daten wie IP-Adresse und Recovery Version nun am oberen Rand des Bildschirms für Sichtbarkeit angezeigt wird. 
 - Dev zu Hause bereits jetzt eine Benutzeroberfläche mit Registerkarten, die Tools in logischen Gruppen gruppiert Navigation über den zulassen.
 - Quick-Aktionsschaltflächen auf der ersten Registerkarte Dev Home ermöglichen schnellen Zugriff auf die am häufigsten verwendeten Aktionen. 

## <a name="wdp-for-xbox-enhancements"></a>WDP für Xbox Verbesserungen
Windows Gerät Portal (WDP) enthält nun zusätzliche Unterstützung für die Konsole-Einstellungen. 

## <a name="you-can-now-switch-the-type-of-your-uwp-title-between-app-and-game"></a>Sie können nun den Typ des Ihr Titel UWP zwischen "App" und "Spiel" wechseln.
Wechseln den Typ des Ihr Titel UWP zwischen "App" und "Gamecontroller" können Sie Spiel Szenarios ohne Veröffentlichung im Speicher zu testen. Wählen Sie in Dev Ihnen zu Hause die app im Bereich **Spiele & Apps** , drücken Sie die Schaltfläche Ansicht auf dem Domänencontroller, wählen Sie **App-Details** aus, und ändern Sie den Typ "App" oder "Spiel".

## <a name="see-also"></a>Weitere Informationen
- [Bekannte Probleme](known-issues.md)
- [UWP auf XboxOne](index.md)
 - Sie können jetzt einen Screenshot der Konsole erstellen. Weitere Informationen zum Erstellen eines Screenshots finden Sie im Referenzthema [/ext/screenshot](wdp-media-capture-api.md).
 - Das Tool kann einen losen Dateibuild Ihrer App bereitstellen. Weitere Informationen zu losen Dateibuilds finden Sie im Referenzthema [/api/app/packagemanager/register](wdp-loose-folder-register-api.md).
 - Sie können auf Entwicklerdateien auf der Konsole über einen Datei-Explorer auf Ihrem Entwicklungscomputer zugreifen. Weitere Informationen zum Zugreifen auf Dateien über einen Datei-Explorer finden Sie im Referenzthema [/ext/smb/developerfolder](wdp-smb-api.md).

## <a name="see-also"></a>Weitere Informationen
- [Bekannte Probleme](known-issues.md)
- [UWP auf XboxOne](index.md)
