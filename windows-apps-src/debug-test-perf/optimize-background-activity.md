---
author: PatrickFarley
ms.assetid: 24351dad-2ee3-462a-ae78-2752bb3374c2
title: Nutzen von Stromsparfeatures
description: "Erstellen Sie UWP-Apps, die mit dem System interagieren, um Hintergrundaufgaben auf eine den Akku effizient nutzende Weise auszuführen."
ms.author: pafarley
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 045dfeb4696a4854b114d88da2a2cbb75d621a58
ms.lasthandoff: 02/07/2017

---

# <a name="optimize-background-activity"></a>Optimieren von Hintergrundaktivitäten

Universelle Windows-Apps sollten auf allen Gerätefamilien mit konsistenter Qualität ausgeführt werden. Auf akkubetriebenen Geräten stellt der Energieverbrauch einen wichtigen Faktor in Bezug auf die allgemeine Erfahrung der Benutzer mit Ihrer App dar. Jeder Benutzer wünscht sich eine Akkulaufzeit für den ganzen Tag. Hierfür muss jedoch jede auf dem Gerät installierte Software, einschließlich Ihrer Software, effizient ausgeführt werden. 

Das Verhalten von Hintergrundaufgaben stellt unbestritten den wichtigsten Faktor in Bezug auf den Energieverbrauch von Apps dar. Eine Hintergrundaufgabe ist eine Programmaktivität, die beim System zur Ausführung registriert wurde, ohne dass die App geöffnet ist. Weitere Informationen finden Sie unter [Erstellen und Registrieren einer Hintergrundaufgabe außerhalb von Prozessen](https://msdn.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task).

## <a name="background-activity-allowance"></a>Einschränkungen für Hintergrundaktivitäten

In Windows 10, Version 1607, können Benutzer im Abschnitt **Akku** der Einstellungs-App die „Akkunutzung nach App“ anzeigen. Hier wird ihnen eine Liste von Apps und der Prozentsatz der Akkulaufzeit (als Anteil an der Akkulaufzeit, die seit dem letzten Aufladen verwendet wurde) angezeigt, den die einzelnen Apps verbraucht haben. 

![Akkunutzung nach App](images/battery-usage-by-app.png)

Im Fall von UWP-Apps in dieser Liste können Benutzer die Behandlung von Hintergrundaktivitäten durch das System bis zu einem gewissen Grad steuern. Hintergrundaktivitäten können als „Immer zugelassen“, „Von Windows verwaltet“ (Standardeinstellung) oder „Nie zugelassen“ angegeben werden. (Weitere Informationen hierzu finden Sie weiter unten.) Sie verwenden den **BackgroundAccessStatus**-Enumerationswert, der von der [**BackgroundExecutionManager.RequestAccessAsync()**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.backgroundexecutionmanager.requestaccessasync.aspx)-Methode zurückgegeben wird, um festzustellen, welche Einschränkungen für Hintergrundaktivitäten für Ihre App vorhanden sind.

![Berechtigungen für Hintergrundaufgaben](images/background-task-permissions.png)

Wenn Ihre App keine verantwortliche Verwaltung von Hintergrundaufgaben implementiert, lehnen Benutzer möglicherweise Genehmigungen für Hintergrundaktivitäten für Ihre App insgesamt ab. Dies ist für keine der beiden Parteien vorteilhaft.

## <a name="work-with-the-battery-saver-feature"></a>Arbeiten mit dem Stromsparmodus-Feature
Der Stromsparmodus ist ein Feature auf Systemebene, das Benutzer in den Einstellungen konfigurieren können. Es deaktiviert alle Hintergrundaktivitäten aller Apps, wenn der Akkustand einen benutzerdefinierten Schwellenwert unterschreitet. *Ausgenommen* sind Hintergrundaktivitäten von Apps, für die „Immer zugelassen“ festgelegt wurde.

Wenn Ihre App als „Von Windows verwaltet“ gekennzeichnet ist und **BackgroundExecutionManager.RequestAccessAsync()** aufruft, um eine Hintergrundaktivität zu registrieren, während der Stromsparmodus aktiviert ist, wird ein **DeniedSubjectToSystemPolicy**-Wert zurückgegeben. Ihre App sollte in diesem Fall die Benutzer benachrichtigen, dass die angegebene(n) Hintergrundaufgabe(n) nicht ausgeführt wird/werden, bis der Stromsparmodus deaktiviert wurde und sie erneut beim System registriert wird/werden. Wenn eine Hintergrundaufgabe bereits zur Ausführung registriert wurde und der Stromsparmodus zum Zeitpunkt der Auslösung aktiviert ist, wird die Aufgabe nicht ausgeführt und die Benutzer werden nicht benachrichtigt. Um die Wahrscheinlichkeit hierfür zu verringern, sollten Sie Ihre App so programmieren, dass Hintergrundaufgaben bei jedem Öffnen erneut registriert werden.

Auch wenn die Verwaltung von Hintergrundaufgaben den primären Zweck des Stromsparmodus-Features darstellen, kann Ihre App zusätzliche Anpassungen vornehmen, um bei aktiviertem Stromsparmodus zusätzlich Energie zu sparen. Sie überprüfen den Status des Stromsparmodus innerhalb Ihrer App, indem Sie auf die [**PowerManager.PowerSavingMode**](https://msdn.microsoft.com/library/windows/apps/windows.phone.system.power.powermanager.powersavingmode.aspx)-Eigenschaft verweisen. Dies ist ein Enumerationswert: entweder **PowerSavingMode.Off** oder **PowerSavingMode.On**. Wenn der Stromsparmodus aktiviert ist, könnte Ihre App die Verwendung von Animationen reduzieren, das Abrufen von Standorten beenden oder Synchronisierungen und Sicherungen verzögern. 

## <a name="further-optimize-background-tasks"></a>Zusätzliches Optimieren von Hintergrundaufgaben
Im Folgenden finden Sie zusätzliche Schritte, die Sie beim Registrieren von Hintergrundaufgaben ausführen können, um zusätzliche Energie zu sparen.

Verwenden Sie einen Wartungsauslöser. Sie können ein [**MaintenanceTrigger**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.maintenancetrigger.aspx)-Objekt anstelle eines [**SystemTrigger**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.systemtrigger.aspx)-Objekts verwenden, um festzulegen, wann eine Hintergrundaufgabe gestartet wird. Aufgaben, die Wartungsauslöser verwenden, werden nur ausgeführt, wenn das Gerät an die Stromversorgung angeschlossen ist, und dürfen länger ausgeführt werden. Weitere Anweisungen finden Sie unter [Verwenden von Wartungsauslösern](https://msdn.microsoft.com/windows/uwp/launch-resume/use-a-maintenance-trigger).

Verwenden Sie den **BackgroundWorkCostNotHigh**-Systembedingungstyp. Die Systembedingungen müssen erfüllt sein, damit Hintergrundaufgaben ausgeführt werden. (Weitere Informationen finden Sie unter [Festlegen von Bedingungen zum Ausführen einer Hintergrundaufgabe](https://msdn.microsoft.com/windows/uwp/launch-resume/set-conditions-for-running-a-background-task)). Die Kosten für Hintergrundaufgaben stellen eine Messung dar, die die *relativen* Auswirkungen auf den Energieverbrauch angibt, wenn die Hintergrundaufgabe ausgeführt wird. Eine Aufgabe, die ausgeführt wird, während das Gerät an die Stromversorgung angeschlossen ist, würde als **niedrig** markiert werden (wenig/keine Auswirkung auf den Akku). Eine Aufgabe, die ausgeführt wird, wenn das Gerät mit Akkustrom betrieben wird und der Bildschirm ausgeschaltet ist, wird als **hoch** markiert, da zu diesem Zeitpunkt vermutlich nur wenige Programmaktivitäten auf dem Gerät ausgeführt werden. Daher verursacht eine Hintergrundaufgabe höhere relative Kosten. Eine Aufgabe, die ausgeführt wird, während das Gerät mit Akkustrom betrieben wird und der Bildschirm *eingeschaltet* ist, wird als **mittel** markiert, da vermutlich einige Programmaktivitäten bereits ausgeführt werden und die Hintergrundaufgabe etwas mehr zum Energieverbrauch beiträgt. Die **BackgroundWorkCostNotHigh**-Systembedingung verzögert einfach die Fähigkeit Ihrer Aufgabe, ausgeführt zu werden, bis der Bildschirm eingeschaltet ist oder das Gerät an die Stromversorgung angeschlossen ist.

## <a name="test-battery-efficiency"></a>Testen der Akkueffizienz

Testen Sie Ihre App auf realen Geräten, wenn Sie Szenarien mit hohem Energieverbrauch untersuchen. Es ist sinnvoll, Ihre App auf vielen unterschiedlichen Geräten bei aktiviertem und deaktiviertem Stromsparmodus und in Umgebungen mit unterschiedlichen Netzwerksignalstärken zu testen.

## <a name="related-topics"></a>Verwandte Themen

* [Erstellen und Registrieren einer Hintergrundaufgabe außerhalb von Prozessen](https://msdn.microsoft.com/windows/uwp/launch-resume/create-and-register-a-background-task)  
* [Planen der Leistung](https://msdn.microsoft.com/windows/uwp/debug-test-perf/planning-and-measuring-performance)  


