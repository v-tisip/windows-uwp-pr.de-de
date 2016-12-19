---
author: QuinnRadich
title: "Auswählen einer UWP-Version"
description: "Beim Schreiben einer UWP-App in Microsoft Visual Studio können Sie wählen, für welche Version die App bestimmt ist. Sie erhalten Informationen zum Unterschied zwischen unterschiedlichen UWP-Versionen und zur Konfiguration Ihrer Auswahl in neuen und vorhandenen Projekten."
translationtype: Human Translation
ms.sourcegitcommit: 006b5d01c2474591a81e4d7a83c5735dc0b3d9d8
ms.openlocfilehash: 5d05c427ecc1ec57856b7c3909be50c3d87daa28

---

# <a name="choose-a-uwp-version"></a>Auswählen einer UWP-Version

Beim Schreiben einer UWP-App in Microsoft Visual Studio können Sie wählen, für welche Version die App bestimmt ist. Derzeit sind nur drei mögliche Versionen verfügbar.

| Version | Beschreibung |
| --- | --- |
| Build 14393 (Anniversary Edition) | Dies ist die neueste Version von Windows 10, die im Juli 2016 veröffentlicht wurde. Einige Highlights dieser Version sind: </br> \* **Windows Ink:** Neue InkCanvas- und InkToolbar-Steuerelemente. </br> \* **Cortana-APIs:** Verwenden Sie neue Cortana-Aktionen, um die Cortana-Unterstützung in bestimmte Funktionen Ihrer App zu integrieren. </br> \* **Windows Hello:** Microsoft Edge unterstützt jetzt Windows Hello, sodass Webentwickler Zugang zur biometrischen Authentifizierung erhalten. </br> Informationen zu diesen und vielen weiteren Funktionen, die in dieser Version von Windows hinzugefügt wurden, finden Sie im [Dev Center](https://developer.microsoft.com/en-us/windows/windows-10-for-developers) oder auf der ausführlicheren Seite unter [Neuigkeiten für Entwickler in Windows 10](../whats-new/windows-10-version-1607.md).  |
| Build 10586 | Diese Version von Windows 10 wurde im November 2015 veröffentlicht. Zu den besonderen Funktionen gehören die Einführung von ORTC-APIs (Object Real-Time Communications) für die Videokommunikation in Microsoft Edge und Anbieter-APIs, damit Apps die Windows Hello-Gesichtsauthentifizierung nutzen können. [Weitere Informationen zu neuen Features in diesem Build](../whats-new/windows-10-version-1511.md) |
| Build 10240 | Dies ist die erste veröffentlichte Version von Windows 10 (Juli 2015). [Weitere Informationen zu neuen Features in diesem Build](../whats-new/windows-10-version-1507.md) |

Es wird dringend empfohlen, dass neue Entwickler und Entwickler, die Code für eine allgemeine Zielgruppe schreiben, immer den aktuellen Build von Windows (14393) verwenden. Für Entwickler, die Enterprise-Apps schreiben, ist es ratsam, die Unterstützung einer früheren **Mindestversion** in Erwägung zu ziehen.

## <a name="whats-different-in-each-uwp-version"></a>Wodurch unterscheiden sich die einzelnen UWP-Versionen?

Neue und geänderte APIs für UWP sind in jeder neuen Version von Windows 10 verfügbar. Ausführlichere Informationen dazu, welche Funktionen in welcher Version hinzugefügt wurden, finden Sie unter [Neuigkeiten für Entwickler in Windows 10](../whats-new/windows-10-version-1607.md).

Referenzthemen, in denen alle Gerätefamilien mit ihren Versionen und alle API-Verträge mit ihren Versionen aufgeführt sind, finden Sie unter [Gerätefamilien](https://msdn.microsoft.com/library/windows/apps/dn706137.aspx) und [API-Verträge](https://msdn.microsoft.com/library/windows/apps/dn706135.aspx).

## <a name="choose-which-version-to-use-for-your-app"></a>Auswählen der Version für die App

In Visual Studio können Sie im Dialogfeld **Neues universelles Windows-Projekt** eine Version für **Zielversion** und **Mindestens erforderliche Version** auswählen.

* **Zielversion**: Legt die Einstellung *TargetPlatformVersion* in Ihrer Projektdatei fest. Außerdem wird der Wert des Attributs *TargetDeviceFamily@MaxVersionTested* im App-Paketmanifest bestimmt. Mit dem von Ihnen gewählten Wert wird die Version der UWP-Plattform angegeben, für die Ihr Projekt bestimmt ist, und somit auch der in der App verfügbare API-Satz. Wir empfehlen Ihnen also, möglichst die aktuelle Version zu wählen. Weitere Informationen zum App-Paketmanifest und einige Richtlinien zur manuellen Konfiguration von TargetDeviceFamily finden Sie unter [TargetDeviceFamily](https://msdn.microsoft.com/library/windows/apps/dn986903).
* **Mindestens erforderliche Version**: Legt die Einstellung *TargetPlatformMinVersion* in Ihrer Projektdatei fest. Außerdem wird der Wert des Attributs *TargetDeviceFamily@MinVersion* im App-Paketmanifest bestimmt. Mit dem von Ihnen ausgewählten Wert wird die Mindestversion der UWP-Plattform angegeben, die von Ihrem Projekt verwendet werden kann.

Seien Sie sich hierbei bewusst, dass Sie Folgendes deklarieren: Ihre App funktioniert mit jeder Windows-Version, die zwischen **Mindestens erforderliche Version** und **Zielversion** liegt. Falls es sich um dieselbe Version handelt, müssen Sie nichts Besonderes unternehmen. Wenn es unterschiedliche Versionen sind, sollten Sie die hier angegebenen Hinweise beachten.

* Im Code können Sie frei (also ohne Bedingungsprüfungen) alle APIs aufrufen, die in der unter **Mindestens erforderliche Version** angegebenen API vorhanden sind.
* Testen Sie Ihren Code auf einem Gerät, auf dem die **Mindestens erforderliche Version** ausgeführt wird, um sicherzustellen, dass er ohne die APIs funktioniert, die nur in der **Zielversion** vorhanden sind.
* Der Wert von **Zielversion** wird zum Identifizieren aller Verweise (Vertrags-WinMds) genutzt, die zum Kompilieren des Projekts verwendet werden. Mit diesen Verweisen können Sie Ihren Code aber mit Aufrufen von APIs kompilieren, die nicht unbedingt auf Geräten vorhanden sind, für die Sie die Unterstützung deklariert haben (mit **Mindestens erforderliche Version**). Daher müssen alle APIs, die nach **Mindestens erforderliche Version** eingeführt wurden, mit adaptivem Code aufgerufen werden. Weitere Informationen zu adaptivem Code finden Sie unter [Anleitung für Apps für die Universelle Windows-Plattform (UWP)](../get-started/universal-application-platform-guide.md).



<!--HONumber=Dec16_HO1-->


