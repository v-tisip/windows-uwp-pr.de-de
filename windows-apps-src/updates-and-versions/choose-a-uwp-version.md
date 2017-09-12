---
author: QuinnRadich
title: "Auswählen einer UWP-Version"
description: "Beim Schreiben einer UWP-App in Microsoft Visual Studio können Sie wählen, für welche Version die App bestimmt ist. Sie erhalten Informationen zum Unterschied zwischen unterschiedlichen UWP-Versionen und zur Konfiguration Ihrer Auswahl in neuen und vorhandenen Projekten."
ms.author: quradic
ms.date: 06/06/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.assetid: a8b7830f-4929-44c6-90be-91f38be5f364
ms.openlocfilehash: 141560d379efab8f0bf8f745ec9e77972d847eec
ms.sourcegitcommit: 9d1ca16a7edcbbcae03fad50a4a10183a319c63a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2017
---
# <a name="choose-a-uwp-version"></a>Auswählen einer UWP-Version

Jede Version von Windows10 hat neue und verbesserte Features für die UWP-Plattform hervorgebracht. Beim Erstellen einer UWP-App in Microsoft Visual Studio können Sie wählen, für welche Version die App bestimmt ist.

In der folgenden Tabelle sind die verfügbaren Versionen von Windows10 beschrieben. Bitte beachten Sie, dass diese Tabelle nur für die Erstellung von UWP-Apps gilt, die nur auf Windows10 unterstützt werden. Sie können keine UWP-Apps für ältere Versionen von Windows entwickeln, und es muss [der entsprechende SDK-Build](http://go.microsoft.com/fwlink/?LinkId=821431) für die jeweilige Version installiert sein. 

| Version | Beschreibung |
| --- | --- |
| Build 15063 (Creators Update) | Dies ist die neueste Version von Windows10, die im März2017 veröffentlicht wurde. **Bitte beachten Sie, dass Sie Visual Studio 2017 verwenden _müssen_, um die Ausrichtung auf diese Windows-Version zu ermöglichen**. Einige Highlights dieser Version sind:  </br> \* **Handschrifterkennung:** Windows Ink kann jetzt Freihandstriche als Schrift oder als Zeichenstriche kategorisieren und Text, Formen und grundlegende Layoutstrukturen erkennen. </br> \* **Windows.Ui.Composition-APIs:** Kombinieren und verwenden Sie Animationen ganz einfach in der gesamten App. </br> \* **Livebearbeitung:** Bearbeiten Sie XAML, während Ihre App ausgeführt wird, und zeigen Sie die Änderungen in Echtzeit an. </br> Informationen zu diesen und vielen weiteren Funktionen, die in dieser Version von Windows hinzugefügt wurden, finden Sie im [Dev Center](https://developer.microsoft.com/windows/windows-10-for-developers) oder auf der ausführlicheren Seite unter [Neuigkeiten für Entwickler in Windows10](../whats-new/windows-10-version-1703.md).  |
| Build 14393 (Anniversary Update) | Diese Version von Windows10 wurde im Juli2016 veröffentlicht. Einige Highlights dieser Version sind: </br> \* **Windows Ink:** Neue InkCanvas- und InkToolbar-Steuerelemente. </br> \* **Cortana-APIs:** Verwenden Sie neue Cortana-Aktionen, um die Cortana-Unterstützung in bestimmte Funktionen Ihrer App zu integrieren. </br> \* **Windows Hello:** Microsoft Edge unterstützt jetzt Windows Hello, sodass Webentwickler Zugang zur biometrischen Authentifizierung erhalten. </br> Informationen zu diesen und vielen weiteren Funktionen, die in dieser Version von Windows hinzugefügt wurden, finden Sie im [Dev Center](https://developer.microsoft.com/windows/windows-10-for-developers) oder auf der ausführlicheren Seite unter [Neuigkeiten für Entwickler in Windows10](../whats-new/windows-10-version-1607.md).  |
| Build10586 | Diese Version von Windows10 wurde im November2015 veröffentlicht. Zu den besonderen Funktionen gehören die Einführung von ORTC-APIs (Object Real-Time Communications) für die Videokommunikation in Microsoft Edge und Anbieter-APIs, damit Apps die Windows Hello-Gesichtsauthentifizierung nutzen können. [Weitere Informationen zu neuen Features in diesem Build](../whats-new/windows-10-version-1511.md) |
| Build10240 | Dies ist die erste veröffentlichte Version von Windows10 (Juli2015). [Weitere Informationen zu neuen Features in diesem Build](../whats-new/windows-10-version-1507.md) |

Es wird dringend empfohlen, dass neue Entwickler und Entwickler, die Code für eine allgemeine Zielgruppe schreiben, immer den aktuellen Build von Windows (15063) verwenden. Für Entwickler, die Enterprise-Apps schreiben, ist es ratsam, die Unterstützung einer früheren **Mindestversion** in Erwägung zu ziehen.

## <a name="whats-different-in-each-uwp-version"></a>Wodurch unterscheiden sich die einzelnen UWP-Versionen?

Neue und geänderte APIs für UWP sind in jeder neuen Version von Windows10 verfügbar. Ausführlichere Informationen dazu, welche Funktionen in welcher Version hinzugefügt wurden, finden Sie unter [Neuigkeiten für Entwickler in Windows10](../whats-new/windows-10-version-1703.md).

Referenzthemen, in denen alle Gerätefamilien mit ihren Versionen und alle API-Verträge mit ihren Versionen aufgeführt sind, finden Sie unter [Gerätefamilien](https://msdn.microsoft.com/library/windows/apps/dn706137.aspx) und [API-Verträge](https://msdn.microsoft.com/library/windows/apps/dn706135.aspx).

## <a name="choose-which-version-to-use-for-your-app"></a>Auswählen der Version für die App

In Visual Studio können Sie im Dialogfeld **Neues universelles Windows-Projekt** eine Version für **Zielversion** und **Mindestens erforderliche Version** auswählen. Darüber hinaus können Sie die **Zielversion** und die **Mindestens erforderliche Version** Ihrer UWP-App im Abschnitt *Anwendung* in den **Eigenschaften** der App ändern.

* **Zielversion**: Legt die Einstellung *TargetPlatformVersion* in Ihrer Projektdatei fest. Außerdem wird der Wert des Attributs *TargetDeviceFamily@MaxVersionTested* im App-Paketmanifest bestimmt. Mit dem von Ihnen gewählten Wert wird die Version der UWP-Plattform angegeben, für die Ihr Projekt bestimmt ist, und somit auch der in der App verfügbare API-Satz. Wir empfehlen Ihnen also, möglichst die aktuelle Version zu wählen. Weitere Informationen zum App-Paketmanifest und einige Richtlinien zur manuellen Konfiguration von TargetDeviceFamily finden Sie unter [TargetDeviceFamily](https://msdn.microsoft.com/library/windows/apps/dn986903).
* **Mindestens erforderliche Version**: Legt die Einstellung *TargetPlatformMinVersion* in Ihrer Projektdatei fest. Außerdem wird der Wert des Attributs *TargetDeviceFamily@MinVersion* im App-Paketmanifest bestimmt. Mit dem von Ihnen ausgewählten Wert wird die Mindestversion der UWP-Plattform angegeben, die von Ihrem Projekt verwendet werden kann.

Seien Sie sich hierbei bewusst, dass Sie Folgendes deklarieren: Ihre App funktioniert mit jeder Windows-Version, die zwischen **Mindestens erforderliche Version** und **Zielversion** liegt. Falls es sich um dieselbe Version handelt, müssen Sie nichts Besonderes unternehmen. Wenn es unterschiedliche Versionen sind, sollten Sie die hier angegebenen Hinweise beachten.

* Im Code können Sie frei (also ohne Bedingungsprüfungen) alle APIs aufrufen, die in der unter **Mindestens erforderliche Version** angegebenen API vorhanden sind.
* Testen Sie Ihren Code auf einem Gerät, auf dem die **Mindestens erforderliche Version** ausgeführt wird, um sicherzustellen, dass er ohne die APIs funktioniert, die nur in der **Zielversion** vorhanden sind.
* Der Wert von **Zielversion** wird zum Identifizieren aller Verweise (Vertrags-WinMds) genutzt, die zum Kompilieren des Projekts verwendet werden. Mit diesen Verweisen können Sie Ihren Code aber mit Aufrufen von APIs kompilieren, die nicht unbedingt auf Geräten vorhanden sind, für die Sie die Unterstützung deklariert haben (mit **Mindestens erforderliche Version**). Daher müssen alle APIs, die nach **Mindestens erforderliche Version** eingeführt wurden, mit adaptivem Code aufgerufen werden. Weitere Informationen zu adaptivem Code finden Sie unter [Anleitung für Apps für die Universelle Windows-Plattform (UWP)](../get-started/universal-application-platform-guide.md).
