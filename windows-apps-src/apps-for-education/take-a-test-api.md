---
Description: The JavaScript API for the Microsoft Take a Test app allows you to do secure assessments. Take a Test provides a secure browser that prevents students from using other computer or internet resources during a test.
title: JavaScript-API „Prüfung”
author: PatrickFarley
ms.author: pafarley
ms.assetid: 9bff6318-504c-4d0e-ba80-1a5ea45743da
ms.date: 08/08/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, education
ms.localizationpriority: medium
ms.openlocfilehash: 38596ad12ac309db5dc60e4a5183eee9bf8c7b7c
ms.sourcegitcommit: 4f6dc806229a8226894c55ceb6d6eab391ec8ab6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2018
ms.locfileid: "4084385"
---
# <a name="take-a-test-javascript-api"></a>JavaScript-API „Prüfung”

[Prüfung](https://technet.microsoft.com/edu/windows/take-tests-in-windows-10) ist eine Browser-basierte UWP-app, die gesperrte onlinebewertungen für wichtige Prüfungen rendert, gerendert wird, sodass Dozenten auf den Prüfungsinhalt konzentrieren anstatt sich um eine sichere testumgebung bereitzustellen. Um dies zu erreichen, wird eine JavaScript-API verwendet, die von jeder Web-Anwendung genutzt werden kann. Die API „Prüfung“ unterstützt den [Browser-API-Standard SBAC](http://www.smarterapp.org/documents/SecureBrowserRequirementsSpecifications_0-3.pdf) zur Durchführung wichtiger allgemeiner Kernprüfungen.

Weitere Informationen zur App selbst finden Sie unter [Technische Referenz zur App „Prüfung“](https://technet.microsoft.com/edu/windows/take-a-test-app-technical?f=255&MSPPError=-2147217396). Hilfe zur Problembehandlung finden Sie unter [Problembehandlung bei Microsoft Prüfung mithilfe der Ereignisanzeige](troubleshooting.md).

## <a name="reference-documentation"></a>Referenzdokumentation
Die Prüfungs-APIs gibt es in den folgenden Namespaces. Beachten Sie, dass alle APIs von einem globalen `SecureBrowser`-Objekt abhängen.

| Namespace | Beschreibung |
|-----------|-------------|
|[Sicherheitsnamespace](#security-namespace)|Enthält APIs, mit denen Sie das Gerät zu Testzwecken sperren und eine Testumgebung erzwingen können. |

### <a name="security-namespace"></a>Sicherheitsnamespace

Der sicherheitsnamespace können Sie das Gerät sperren, überprüfen Sie die Liste der Benutzer- und Systemprozesse, Abrufen von Mac- und IP-Adressen und Löschen von zwischengespeicherten Webressourcen.

| Methode | Beschreibung   |
|--------|---------------|
|[lockDown](#lockDown) | Sperrt das Gerät für Testzwecke. |
|[isEnvironmentSecure](#isEnvironmentSecure) | Stellt fest, ob auf das Gerät noch der Sperrmodus-Kontext angewendet wird. |
|[getDeviceInfo](#getDeviceInfo) | Ruft Details zur Plattform ab, auf der die Testanwendung ausgeführt wird. |
|[examineProcessList](#examineProcessList)|Ruft die Liste der ausgeführten Benutzer- und Systemprozesse ab.|
|[close](#close) | Schließt den Browser und entsperrt das Gerät. |
|[getPermissiveMode](#getPermissiveMode)|Überprüft, ob der eingeschränkte Modus aktiviert oder deaktiviert ist.|
|[setPermissiveMode](#setPermissiveMode)|Schaltet den eingeschränkten Modus ein oder aus.|
|[emptyClipBoard](#emptyClipBoard)|Löscht die Zwischenablage des Systems.|
|[getMACAddress](#getMACAddress)|Ruft die Liste der MAC-Adressen für das Gerät ab.|
|[getStartTime](#getStartTime) | Ruft die Zeit ab, zu der die Test-App gestartet wurde. |
|[getCapability](#getCapability) | Fragt ab, ob eine Funktion aktiviert oder deaktiviert ist. |
|[setCapability](#setCapability)|Aktiviert oder deaktiviert die angegebene Funktion.| 
|[isRemoteSession](#isRemoteSession) | Überprüft, ob die aktuelle Sitzung remote angemeldet ist. |
|[isVMSession](#isVMSession) | Überprüft, ob die aktuelle Sitzung auf einem virtuellen Computer ausgeführt wird. |

---

<span id="lockDown"/>

### <a name="lockdown"></a>lockDown
Sperrt das Gerät. Wird auch zum Entsperren des Geräts verwendet. Die Test-Webanwendung führt diesen Aufruf aus, bevor Studenten mit dem Testen beginnen dürfen. Der Implementierer ist erforderlich, um alle notwendigen Aktionen zum Schutz der Testumgebung durchzuführen. Die Schritte zum Schutz der Umgebung sind gerätespezifisch und beinhalten Aspekte wie z.B. das Deaktivieren von Bildschirmaufnahmen, das Deaktivieren des Sprachchats im sicheren Modus, das Löschen der Zwischenablage des Systems, das Wechseln zu einem Kioskmodus, das Deaktivieren von Leerzeichen in OSX10.7+-Geräten usw. Die Testanwendung aktiviert den Sperrmodus, bevor eine Prüfung beginnt, und deaktiviert den Sperrmodus wieder, wenn der Student die Prüfung abgeschlossen und den sicheren Test verlassen hat.

**Syntax**  
`void SecureBrowser.security.lockDown(Boolean enable, Function onSuccess, Function onError);`

**Parameter**  
* `enable` - **true**, wenn die App „Prüfung“ über dem Sperrbildschirm ausgeführt werden soll und die in diesem [Dokument](https://technet.microsoft.com/edu/windows/take-a-test-app-technical?f=255&MSPPError=-2147217396) behandelten Richtlinien angewendet werden sollen. **false** hält die Ausführung von „Prüfung“ über dem Sperrbildschirm an und beendet sie. Wirkungslos, wenn die App nicht gesperrt ist.  
* `onSuccess` - [optional] Die Funktion, die aufgerufen wird, nachdem der Sperrmodus erfolgreich aktiviert oder deaktiviert wurde. Sie muss im Format `Function(Boolean currentlockdownstate)` vorliegen.  
* `onError` - [optional] Die Funktion, die aufgerufen wird, wenn der Sperrvorgang fehlgeschlagen ist. Sie muss im Format `Function(Boolean currentlockdownstate)` vorliegen.  

**Anforderungen**  
Windows10, Version1709

---

<span id="isEnvironmentSecure" />

### <a name="isenvironmentsecure"></a>isEnvironmentSecure
Stellt fest, ob auf das Gerät noch der Sperrmodus-Kontext angewendet wird. Die Test-Webanwendung ruft diese Funktion auf, bevor Studenten mit dem Testen beginnen dürfen, sowie in regelmäßigen Abständen während des Tests.

**Syntax**  
`void SecureBrowser.security.isEnvironmentSecure(Function callback);`

**Parameter**  
* `callback` - Die Funktion, die aufgerufen wird, wenn diese Funktion abgeschlossen wurde. Sie muss im Format `Function(String state)` vorliegen, wobei `state` eine JSON-Zeichenfolge ist, die zwei Felder enthält. Das erste Feld ist `secure`. Dieses Feld zeigt nur dann `true` an, wenn alle erforderlichen Sperren aktiviert (oder Features deaktiviert) wurden, um eine sichere Testumgebung zu ermöglichen, und wenn nichts beschädigt wurde, seitdem die App in den Sperrmodus gewechselt ist. Das andere Feld, `messageKey`, enthält weitere anbieterspezifische Details. Hier können Hersteller zusätzliche Informationen hinterlegen, die das boolesche Kennzeichen `secure` erweitern:

```JSON
{
    'secure' : "true/false",
    'messageKey' : "some message"
}
```

**Anforderungen**  
Windows10, Version1709

---

<span id="getDeviceInfo" />

### <a name="getdeviceinfo"></a>getDeviceInfo
Ruft Details zur Plattform ab, auf der die Testanwendung ausgeführt wird. Wird verwendet, um die Informationen anzureichern, die vom Benutzer-Agent erkennbar waren.

**Syntax**  
`void SecureBrowser.security.getDeviceInfo(Function callback);`

**Parameter**  
* `callback` - Die Funktion, die aufgerufen wird, wenn diese Funktion abgeschlossen wurde. Sie muss im Format `Function(String infoObj)` vorliegen, wobei `infoObj` eine JSON-Zeichenfolge ist, die mehrere Felder enthält. Die folgenden Felder müssen unterstützt werden:
    * `os` steht für den Typ des Betriebssystems (z.B. Windows, MacOS, Linux, iOS, Android usw.)
    * `name` steht für den Namen der Betriebssystemversion, sofern vorhanden (z.B. Sierra, Ubuntu).
    * `version` steht für die Version des Betriebssystems (z.B. 10.1, 10 Pro usw.).
    * `brand` steht für das sichere Browser-Branding (z.B. OAKS, CA, SmarterApp usw.).
    * `model` gibt nur das Gerätemodell für mobile Geräte an; null/nicht verwendet bei Desktopbrowsern.

**Anforderungen**  
Windows10, Version1709

---

<span id="examineProcessList" />

### <a name="examineprocesslist"></a>examineProcessList
Ruft die Liste aller Prozesse ab, die auf dem Clientcomputer im Besitz des Benutzers ausgeführt werden. Die Testanwendung ruft diese Funktion auf, um die Liste zu überprüfen und mit einer Liste der Prozesse zu vergleichen, die während der Testphase auf die Blacklist gesetzt wurden. Dieser Aufruf sollte sowohl zu Beginn einer Prüfung sowie in regelmäßigen Abständen während der Prüfung ausgeführt werden. Wenn ein Prozess auf der Blacklist erkannt wird, sollte die Prüfung beendet werden, um die Integrität des Tests zu wahren.

**Syntax**  
`void SecureBrowser.security.examineProcessList(String[] blacklistedProcessList, Function callback);`

**Parameter**  
* `blacklistedProcessList` - Die Liste der Prozesse, die von der Testanwendung auf die Blacklist gesetzt wurden.  
`callback` - Die Funktion, die aufgerufen wird, sobald die aktiven Prozesse gefunden wurden. Sie muss im Format `Function(String foundBlacklistedProcesses)` vorliegen, wobei `foundBlacklistedProcesses` das Format `"['process1.exe','process2.exe','processEtc.exe']"` hat. Sie ist leer, wenn keine Prozesse auf der Blacklist gefunden wurden. Wenn sie null ist, bedeutet dies, dass im ursprünglichen Funktionsaufruf ein Fehler aufgetreten ist.

**Hinweise** Diese Liste enthält keine Systemprozesse.

**Anforderungen**  
Windows10, Version1709

---

<span id="close"/>

### <a name="close"></a>close
Schließt den Browser und entsperrt das Gerät. Die Testanwendung sollte diese Funktion aufrufen, wenn der Benutzer beschließt, den Browser zu beenden.

**Syntax**  
`void SecureBrowser.security.close(restart);`

**Parameter**  
* `restart` - Dieser Parameter wird ignoriert, muss aber angegeben werden.

**Hinweise** In Windows10, Version 1607, muss das Gerät zunächst gesperrt werden. In späteren Versionen schließt diese Methode den Browser unabhängig davon, ob das Gerät gesperrt ist.

**Anforderungen**  
Windows10, Version1709

---

<span id="getPermissiveMode" />

### <a name="getpermissivemode"></a>getPermissiveMode
Die Testanwendung sollte diese Funktion aufrufen, um zu bestimmen, ob der eingeschränkte Modus aktiviert oder deaktiviert ist. Im eingeschränkten Modus lockert ein Browser erwartungsgemäß einige seiner strengen Sicherheitregeln, damit Hilfstechnologien mit dem sicheren Browser funktionieren. Browser, die die Benutzeroberflächen anderer Anwendungen strikt daran hindern, über diesen angezeigt zu werden, könnten dieses Verhalten im eingeschränkten Modus lockern. 

**Syntax**  
`void SecureBrowser.security.getPermissiveMode(Function callback)`

**Parameter**  
* `callback` - Die Funktion, die aufgerufen wird, wenn dieser Aufruf abgeschlossen wurde. Sie muss im Format `Function(Boolean permissiveMode)` vorliegen, wobei `permissiveMode` angibt, ob für den Browser aktuell der eingeschränkte Modus aktiviert ist. Wenn sie nicht definiert oder null ist, ist beim GET-Vorgang ein Fehler aufgetreten.

**Anforderungen**  
Windows10, Version1709

---

<span id="setPermissiveMode" />

### <a name="setpermissivemode"></a>setPermissiveMode
Die Testanwendung sollte diese Funktion aufrufen, um den eingeschränkten Modus zu aktivieren oder zu deaktivieren. Im eingeschränkten Modus lockert ein Browser erwartungsgemäß einige seiner strengen Sicherheitregeln, damit Hilfstechnologien mit dem sicheren Browser funktionieren. Browser, die die Benutzeroberflächen anderer Anwendungen strikt daran hindern, über diesen angezeigt zu werden, könnten dieses Verhalten im eingeschränkten Modus lockern. 

**Syntax**  
`void SecureBrowser.security.setPermissiveMode(Boolean enable, Function callback)`

**Parameter**  
* `enable` – Der boolesche Wert, der den Status des vorgesehenen eingeschränkten Modus angibt.  
* `callback` - Die Funktion, die aufgerufen wird, wenn dieser Aufruf abgeschlossen wurde. Sie muss im Format `Function(Boolean permissiveMode)` vorliegen, wobei `permissiveMode` angibt, ob für den Browser aktuell der eingeschränkte Modus aktiviert ist. Wenn sie nicht definiert oder null ist, ist beim SET-Vorgang ein Fehler aufgetreten.

**Anforderungen**  
Windows10, Version1709

---

<span id="emptyClipBoard"/>

### <a name="emptyclipboard"></a>emptyClipBoard
Löscht die Zwischenablage des Systems. Die Testanwendung sollte diese Funktion aufrufen, um zu erzwingen, dass alle Daten gelöscht werden, die unter Umständen in der Zwischenablage des Systems gespeichert sind. Dieser Vorgang wird auch von der Funktion **[lockDown](#lockDown)** ausgeführt.

**Syntax**  
`void SecureBrowser.security.emptyClipBoard();`

**Anforderungen**  
Windows10, Version1709

---

<span id="getMACAddress" />

### <a name="getmacaddress"></a>getMACAddress
Ruft die Liste der MAC-Adressen für das Gerät ab. Die Testanwendung sollte diese Funktion aufrufen, um Unterstützung bei der Diagnose zu bieten. 

**Syntax**  
`void SecureBrowser.security.getMACAddress(Function callback);`

**Parameter**  
* `callback` - Die Funktion, die aufgerufen wird, wenn dieser Aufruf abgeschlossen wurde. Sie muss im Format `Function(String addressArray)` vorliegen, wobei `addressArray` das Format `"['00:11:22:33:44:55','etc']"` hat.

**Hinweise**  
Es ist schwierig, sich bei der Unterscheidung zwischen den Endnutzercomputern innerhalb der Testserver auf die Quell-IP-Adressen zu verlassen, da in Schulen für gewöhnlich Firewalls/NATs/Proxys verwendet werden. Anhand der MAC-Adressen kann die App für Diagnosezwecke zwischen den Endbenutzercomputern hinter einer gängigen Firewall unterscheiden.

**Anforderungen**  
Windows10, Version1709

---

<span id="getStartTime" />

### <a name="getstarttime"></a>getStartTime
Ruft die Zeit ab, zu der die Test-App gestartet wurde.

**Syntax**  
`DateTime SecureBrowser.settings.getStartTime();`

**Rückgabe**  
Ein DateTime-Objekt, das den Zeitpunkt angibt, zu dem die Test-App gestartet wurde.

**Anforderungen**  
Windows10, Version1709

---

<span id="getCapability"/>

### <a name="getcapability"></a>getCapability
Fragt ab, ob eine Funktion aktiviert oder deaktiviert ist. 

**Syntax**  
`Object SecureBrowser.security.getCapability(String feature)`

**Parameter**  
`feature` - Die Zeichenfolge, die festlegt, welche Funktion abgefragt werden soll. Gültige Funktionszeichenfolgen sind „screenMonitoring“, „printing“ und „textSuggestions“ (Groß-/Kleinschreibung spielt keine Rolle).

**Rückgabewert**  
Diese Funktion gibt ein JavaScript-Objekt oder Literalzeichen im folgenden Format zurück: `{<feature>:true|false}`. **true**, wenn die abgefragte Funktion aktiviert ist, **false**, wenn die Funktion nicht aktiviert oder die Funktionszeichenfolge ungültig ist.

**Anforderungen** Windows10, Version 1703

---

<span id="setCapability"/>

### <a name="setcapability"></a>setCapability
Aktiviert oder deaktiviert eine bestimmte Funktion des Browsers.

**Syntax**  
`void SecureBrowser.security.setCapability(String feature, String value, Function onSuccess, Function onError)`

**Parameter**  
* `feature` - Die Zeichenfolge, mit der bestimmt wird, welche Funktion festgelegt wird. Gültige Funktionszeichenfolgen sind `"screenMonitoring"`, `"printing"` und `"textSuggestions"` (Groß-/Kleinschreibung spielt keine Rolle).  
* `value` – Die gewünschte Einstellung für das Feature. Muss entweder `"true"` oder `"false"` sein.  
* `onSuccess` - [optional] Die Funktion, die aufgerufen wird, nachdem der SET-Vorgang erfolgreich abgeschlossen wurde. Sie muss im Format `Function(String jsonValue)` vorliegen, wobei *jsonValue* das Format `{<feature>:true|false|undefined}` hat.  
* `onError` - [optional] Die Funktion, die aufgerufen wird, wenn der SET-Vorgang fehlgeschlagen ist. Sie muss im Format `Function(String jsonValue)` vorliegen, wobei *jsonValue* das Format `{<feature>:true|false|undefined}` hat.

**Hinweise**  
Wenn die Zielfunktion dem Browser nicht bekannt ist, übergibt diese Funktion den Wert `undefined` an die Rückruffunktion.

**Anforderungen** Windows10, Version 1703

---

<span id="isRemoteSession"/>

### <a name="isremotesession"></a>isRemoteSession
Überprüft, ob die aktuelle Sitzung remote angemeldet ist.

**Syntax**  
`Boolean SecureBrowser.security.isRemoteSession();`

**Rückgabewert**  
**true**, wenn es sich bei der aktuellen Sitzung um eine Remotesitzung handelt, andernfalls **false**.

**Anforderungen**  
Windows10, Version1709

---

<span id="isVMSession"/>

### <a name="isvmsession"></a>isVMSession
Überprüft, ob die aktuelle Sitzung auf einem virtuellen Computer ausgeführt wird.

**Syntax**  
`Boolean SecureBrowser.security.isVMSession();`

**Rückgabewert**  
**true**, wenn die aktuelle Sitzung auf einem virtuellen Computer ausgeführt wird, andernfalls **false**.

**Hinweise**  
Diese API-Prüfung erkennt nur VM Sitzungen, die in bestimmten Hypervisoren ausgeführt werden, die die entsprechenden APIs implementieren.

**Anforderungen**  
Windows10, Version1709

---