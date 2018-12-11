---
title: Neuigkeiten für UWP auf Xbox One
description: Vorstellung neuer Features für UWP-Apps auf Xbox One.
ms.date: 03/29/2017
ms.topic: article
keywords: Windows10, UWP
ms.assetid: fe63c527-8f06-43a5-868f-de909f5664b3
ms.localizationpriority: medium
ms.openlocfilehash: aff65e5f1b4771cbb33bc8b8219224042b7bf7e2
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8922704"
---
# <a name="whats-new-for-developers-in-the-latest-update-of-uwp-on-xbox-one"></a>Neuigkeiten für Entwickler in der neuesten Aktualisierung von UWP auf Xbox One

Das neueste Update für universelle Windows-Plattform (UWP) auf Xbox One enthält die folgenden neuen Features, Updates für vorhandene Features und Fehlerbehebungen.

## <a name="x86-apps-and-games-are-no-longer-supported-on-xbox"></a>X86 apps und Spiele werden nicht mehr unterstützt, auf Xbox  
Xbox unterstützt die Entwicklung von x86 Apps oder deren Übermittlung an den Store nicht mehr.

## <a name="apps-can-now-support-navigating-back-to-the-previous-app"></a>Apps unterstützen jetzt das Navigieren zurück zum vorherigen app 
UWP auf Xbox One-apps unterstützen jetzt das Navigieren zurück zum vorherigen app. Zu diesem Zweck das [**Windows.UI.Core.SystemNavigationManager.BackRequested**](https://msdn.microsoft.com/library/windows/apps/dn893595) -Ereignis abonnieren Sie, und legen Sie die **Handled** -Eigenschaft auf **"false"** im Ereignishandler.

> [!NOTE]
> Aus Gründen der Kompatibilität ist diese Funktionalität nur für apps, die mit der neuesten Version der UWP auf Xbox One integriert sind verfügbar. 

## <a name="dev-home-is-now-the-default-home-experience-on-development-consoles"></a>Dev Home ist jetzt die Standard-startoberfläche auf Entwicklungskonsolen
-Entwicklungskonsolen starten Sie Dev Home jetzt als der Standard-startoberfläche. Auf diese Weise können Sie richtig funktionieren ohne aus dem Einzelhandel-Startbildschirm durch klicken. Dev Home enthält jetzt eine schnelle Aktion dem Einzelhandel-Startbildschirm starten. Darüber hinaus kann eine neue Einstellung Sie standardmäßig retail Home. 

## <a name="new-dev-home-user-interface"></a>Neue Dev Home-Benutzeroberfläche
Die Dev Home-Benutzeroberfläche enthält jetzt die folgenden erweiterten Funktionen:
 - Wichtige Daten wie IP-Adresse und Recovery-Version wird nun am oberen Rand des Bildschirms für Sichtbarkeit angezeigt. 
 - Dev Home verfügt nun über eine Benutzeroberfläche mit Registerkarten, die Tools in logischen Sätze gruppiert ermöglicht die schnelle Navigation.
 - Schnelle Aktion Schaltflächen auf der ersten Registerkarte der Dev Home können schnellen Zugriff auf die am häufigsten verwendeten Aktionen. 

## <a name="wdp-for-xbox-enhancements"></a>WDP für Xbox-Erweiterungen
Die Windows-Geräteportal (WDP) enthält jetzt zusätzlichen Unterstützung für die Einstellungen der Konsole. 

## <a name="you-can-now-switch-the-type-of-your-uwp-title-between-app-and-game"></a>Sie können jetzt den Typ der UWP Titel zwischen "App" und "Game" wechseln.
Die Art von Ihrer UWP-Titel zwischen "App" und "Spiel" wechseln, können Sie spielszenarien ohne Veröffentlichung an den Store zu testen. Wählen Sie in Dev Home die app im Bereich **Spiele und Apps** , drücken Sie die Ansicht-Taste auf dem Controller, wählen Sie die **App-Details** , und ändern Sie den Typ "App" oder "Spiel".

## <a name="see-also"></a>Weitere Informationen:
- [Bekannte Probleme](known-issues.md)
- [UWP auf XboxOne](index.md)
 - Sie können jetzt einen Screenshot der Konsole erstellen. Weitere Informationen zum Erstellen eines Screenshots finden Sie im Referenzthema [/ext/screenshot](wdp-media-capture-api.md).
 - Das Tool kann einen losen Dateibuild Ihrer App bereitstellen. Weitere Informationen zu losen Dateibuilds finden Sie im Referenzthema [/api/app/packagemanager/register](wdp-loose-folder-register-api.md).
 - Sie können auf Entwicklerdateien auf der Konsole über einen Datei-Explorer auf Ihrem Entwicklungscomputer zugreifen. Weitere Informationen zum Zugreifen auf Dateien über einen Datei-Explorer finden Sie im Referenzthema [/ext/smb/developerfolder](wdp-smb-api.md).

## <a name="see-also"></a>Weitere Informationen
- [Bekannte Probleme](known-issues.md)
- [UWP auf XboxOne](index.md)
