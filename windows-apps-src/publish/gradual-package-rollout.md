---
author: JnHs
Description: When you publish an update to a submission, you can choose to gradually roll out the updated packages to a percentage of your app’s customers on Windows 10.
title: Schrittweiser Paketrollout
ms.author: wdg-dev-content
ms.date: 12/05/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.assetid: 65d578a6-4e26-484c-90af-b2cd916f3634
ms.localizationpriority: medium
ms.openlocfilehash: 407ffb5fdebdc90a63ed7f65b4e97f8358dc58c8
ms.sourcegitcommit: 1c6325aa572868b789fcdd2efc9203f67a83872a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2018
ms.locfileid: "4741017"
---
# <a name="gradual-package-rollout"></a>Schrittweiser Paketrollout

Wenn Sie ein Update für eine Übermittlung veröffentlichen möchten, können Sie auswählen, schrittweise an die aktualisierten Pakete für einen bestimmten Prozentsatz der Kunden Ihrer app unter Windows 10 (einschließlich Xbox) bereitstellen. So können Sie Feedback und Analysedaten für die jeweiligen Pakete überwachen und vor einem umfassenden Rollout sicherstellen, dass das Update ordnungemäß funktioniert. Sie können den Prozentsatz jederzeit erhöhen (oder das Update stoppen), ohne eine neue Übermittlung zu erstellen. 

> [!IMPORTANT]
> Ihre Rolloutauswahl gilt für alle Pakete, wird jedoch nur bei Kunden mit Betriebssystemversionen mit Unterstützung für Flight-Pakete (Windows.Desktop Build 10586 oder höher, Windows.Mobile Build 10586.63 oder höher und Xbox) übernommen, einschließlich bei Kunden, die Ihre App über [Vom Store verwaltete (Online-)Lizenzierung](organizational-licensing.md) aus dem [Microsoft Store for Business](https://businessstore.microsoft.com/store) oder [Microsoft Store für Bildungseinrichtungen](https://educationstore.microsoft.com/store) beziehen. Beim schrittweisen Paketrollout erhalten Kunden mit älteren Betriebssystemversionen keine Pakete aus der aktuellen Übermittlung, bis Sie das Paketrollout wie nachfolgend beschrieben abschließen.

Beachten Sie, dass alle Ihre Kunden den mit Ihrer letzten Übermittlung eingegebenen Store-Eintrag anzeigen können. Die Rollout-Einstellungen gelten nur für die Pakete, die Kunden erhalten (Neukunden und Updates für vorhandene Kunden).

> [!TIP]
> Beim Paketrollout werden Pakete an eine zufällige Auswahl von Kunden in Höhe des von Ihnen angegebenen Prozentsatzes verteilt. Um bestimmte Pakete an von Ihnen ausgewählte Kunden zu verteilen, können Sie Flight-Pakete verwenden. Sie können das Rollout auch mit Ihren Flight-Paketen kombinieren, wenn Sie ein Update schrittweise auf eine Ihrer Test-Flight-Gruppen verteilen möchten.


## <a name="setting-the-rollout-percentage"></a>Festlegen eines Rollout-Prozentsatzes

Sie können das Rollout eines Updates auf der Seite **Pakete** einer aktualisierten Einreichung auswählen. Aktivieren Sie hierfür das Kontrollkästchen **Update-Rollout schrittweise nach Veröffentlichung dieser Übermittlung (nur für Windows10-Kunden)**. Geben Sie den Prozentsatz an Kunden an, die das Update bei erster Veröffentlichung der Übermittlung erhalten sollen. Geben Sie z.B. 5 ein, wenn Sie das Update zunächst nur für einen kleinen Teil Ihrer App-Kunden veröffentlichen möchten.

Klicken Sie auf **Update**, um Ihre Auswahl zu speichern. Nachdem Ihre App den Zertifizierungsprozess abgeschlossen hat, werden die Pakete an Kunden gemäß dem von Ihnen angegebenen Prozentsatz verteilt (dies gilt für Neukunden und Updates für vorhandene Kunden).


## <a name="adjusting-the-rollout-after-the-submission-is-published"></a>Anpassen des Rollouts, nachdem die Übermittlung veröffentlicht wurde

Sie können das Rollout, nachdem die Übermittlung veröffentlicht wurde, in der App-Übersicht anpassen. Sie können den Prozentsatz der Kunden, die das Paket Ihrer aktuellen Übermittlung erhalten, über den Schieberegler ändern. Klicken Sie auf **Update**, um Ihre Auswahl zu speichern. Die Pakete werden gemäß dem von Ihnen angegebenen Prozentsatz an Kunden verteilt (dies gilt für Neukunden und Updates für vorhandene Kunden).


## <a name="completing-the-rollout"></a>Abschließen des Rollouts

Bevor Sie eine neue Übermittlung erstellen können, müssen Sie das Paketrollout abschließen. Sie können das Rollout **abschließen** und die aktuellen Pakete an alle Ihre Kunden verteilen, oder das Rollout **anhalten**, um die Verteilung der aktuellen Pakete zu stoppen.

Wenn Sie das Update für zuverlässig halten und dieses all Ihren Kunden verfügbar machen möchten, klicken Sie auf **Paketrollout abschließen**. Dann werden die neuesten Pakete an alle Kunden verteilt.

> [!TIP]
> Wenn Sie den Prozentsatz für das Rollout auf 100% festlegen, wird dadurch nicht sichergestellt, dass alle Ihre Kunden die Pakete von der aktuellen Übermittlung erhalten, da einige Kunden möglicherweise Betriebssystemversionen verwenden, die ein Rollout nicht unterstützen. Sie müssen das Rollout abschließen, um die Verteilung von älteren Pakete zu beenden, und allen vorhandenen Kunden das Update bereitstellen.

Wenn Sie feststellen, dass ein Problem mit dem Update besteht, und Sie dieses nicht mehr verbreiten möchten, klicken Sie auf **Paketrollout anhalten**, um die Verteilung von Paketen der letzten Übermittlung zu beenden. Wenn Sie ein Paketrollout anhalten, werden diese Pakete nicht mehr an Kunden verteilt. Nur die Pakete aus der vorherigen Übermittlung werden an neue oder vorhandene Kunden verteilt. Alle Kunden, die bereits über die neueren Pakete verfügen, behalten diese Pakete auch. Ein Rollback auf die vorherige Version wird nicht ausgeführt. Um diesen Kunden ein Update bereitzustellen, müssen Sie eine neue Übermittlung mit den Paketen erstellen, die Sie bereitstellen möchten. Beachten Sie, dass bei einem schrittweisen Rollout bei der nächsten Übermittlung Kunden mit Paketen, die Sie angehalten haben, neue Updates in der gleichen Reihenfolge angeboten werden wie bei der ursprünglichen Verteilung. Das neue Rollout liegt zwischen der letzten abgeschlossenen Übermittlung und Ihrer aktuellen Übermittlung. Nachdem Sie einen Paketrollout anhalten, werden diese Pakete nicht mehr an Kunden verteilt.
