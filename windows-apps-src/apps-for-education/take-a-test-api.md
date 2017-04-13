---
author: TylerMSFT
Description: "Mit der JavaScript-API für die App „Prüfung“ von Microsoft können Sie zuverlässige Bewertungen durchführen. „Prüfung“ stellt einen sicheren Browser bereit, der die Lernenden daran hindert, während eines Tests andere Computer- oder Internet-Ressourcen zu verwenden."
title: "JavaScript-API „Prüfung”."
ms.author: twhitney
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.assetid: 9bff6318-504c-4d0e-ba80-1a5ea45743da
ms.openlocfilehash: e308280fcecf825061ddf503ce91f8607fcece72
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="take-a-test-javascript-api"></a>JavaScript-API „Prüfung”

Bei [Prüfung](https://technet.microsoft.com/edu/windows/take-tests-in-windows-10) handelt es sich um eine browserbasierte App, die gesperrte Onlinebewertungen für wichtige Prüfungen rendert. Es werden API-Standards des SBAC-Browsers für wichtige Tests nach dem Common-Core-Bildungsplan unterstützt. Sie können sich auf den Inhalt der Bewertung anstatt auf das Sperren von Windows konzentrieren.

Prüfung wird vom Microsoft-Browser Edge unterstützt und bietet eine JavaScript-API, mit der Webanwendungen Geräte für Prüfungen sperren können.

Die API (basierend auf der [Common Core SBAC API](http://www.smarterapp.org/documents/SecureBrowserRequirementsSpecifications_0-3.pdf)) stellt Text-zu-Sprache und die Möglichkeit von diversen Abfragen bereit (z.B. ob das Gerät gesperrt ist, wer der ausführende Benutzer ist oder welche Prozesse auf dem System ausgeführt werden).

Weitere Informationen zur App selbst finden Sie unter [Technische Referenz zur App „Prüfung“](https://technet.microsoft.com/edu/windows/take-a-test-app-technical).

> [!Important]
> Diese APIs funktionieren nicht in Remotesitzungen.  

Hilfe zur Problembehandlung finden Sie unter [Problembehandlung bei Microsoft Prüfung mithilfe der Ereignisanzeige](troubleshooting.md).

## <a name="reference-documentation"></a>Referenzdokumentation
Die Prüfungs-API umfasst die folgenden Namespaces. 

| Namespace | Beschreibung |
|-----------|-------------|
|[Sicherheitsnamespace](#security-namespace)|Ermöglicht das Sperren des Geräts|
|[TTS-Namespace](#tts-namespace)|Text-zu-Sprache-Funktion|


 ### <a name="security-namespace"></a>Sicherheitsnamespace

Der Sicherheitsnamespace ermöglicht das Sperren des Geräts, das Überprüfen der Liste der Benutzer- und Systemprozesse, das Abrufen von MAC- und IP-Adressen und das Löschen von zwischengespeicherten Webressourcen.

| Methode | Beschreibung   |
|--------|---------------|
|[clearCache](#clearCache) | Löscht zwischengespeicherte Webressourcen |
|[close](#close) | Schließt den Browser und entsperrt das Gerät |
|[enableLockDown](#enableLockDown) | Sperrt das Gerät. Wird auch zum Entsperren des Geräts verwendet |
|[getIPAddressList](#getIPAddressList) | Ruft die Liste der IP-Adressen für das Gerät ab |
|[getMACAddress](#getMACAddress)|Ruft die Liste der MAC-Adressen für das Gerät ab|
|[getProcessList](#getProcessList)|Ruft die Liste der ausgeführten Benutzer- und Systemprozesse ab|
|[isEnvironmentSecure](#isEnvironmentSecure)|Stellt fest, ob auf das Gerät noch der Sperrmodus-Kontext angewendet wird|  

---
<span id="clearCache"/>
### <a name="void-clearcache"></a>void clearCache()
Löscht zwischengespeicherte Webressourcen.

**Syntax**  
`browser.security.clearCache();`

**Parameter**  
`None`

**Rückgabewert**  
`None`

**Anforderungen**  
Windows10, Version1607

---

<span id="close"/>
### <a name="closeboolean-restart"></a>close(boolean restart)
Schließt den Browser und entsperrt das Gerät.

**Syntax**  
`browser.security.close(false);`

**Parameter**  
`restart` - Dieser Parameter wird ignoriert, muss aber angegeben werden.

**Rückgabewert**  
`None`

**Anforderungen**  
Windows10, Version1607

---

<span id="enableLockDown"/>
### <a name="enablelockdownboolean-lockdown"></a>enableLockdown(boolean lockdown)
Sperrt das Gerät. Wird auch zum Entsperren des Geräts verwendet.

**Syntax**  
`browser.security.enableLockDown(true|false);`

**Parameter**  
`lockdown` - `true` wenn die App „Prüfung“ auf dem Sperrbildschirm ausgeführt werden soll und die in dem folgenden[Dokument](https://technet.microsoft.com/edu/windows/take-a-test-app-technical?f=255&MSPPError=-2147217396) behandelten Richtlinien angewendet werden sollen. `False` hält die Ausführung von „Prüfung“ auf dem Sperrbildschirm an und beendet sie. Wirkungslos, wenn die App nicht gesperrt ist.

**Rückgabewert**  
`None`

**Anforderungen**  
Windows10, Version1607

---

<span id="getIPAddressList"/>
### <a name="string-getipaddresslist"></a>string[] getIPAddressList()
Ruft die Liste der IP-Adressen für das Gerät ab.

**Syntax**  
`browser.security.getIPAddressList();`

**Parameter**  
`None`

**Rückgabewert**  
`An array of IP addresses.`

---

<span id="getMACAddress" />
### <a name="string-getmacaddress"></a>string[] getMACAddress()
Ruft die Liste der MAC-Adressen für das Gerät ab.

**Syntax**  
`browser.security.getMACAddress();`

**Parameter**  
`None`

**Rückgabewert**  
`An array of MAC addresses.`

**Anforderungen**  
Windows10, Version1607

---

<span id="getProcessList" />
### <a name="string-getprocesslist"></a>string[] getProcessList()
Ruft die Liste der ausgeführten Benutzerprozesse ab.

**Syntax**  
`browser.security.getProcessList();`

**Parameter**  
`None`

**Rückgabewert**  
`An array of running process names.`

**Anmerkung** Diese Liste enthält keine Systemprozesse.

**Anforderungen**  
Windows10, Version1607

---

<span id="isEnvironmentSecure" />
### <a name="boolean-isenvironmentsecure"></a>boolean isEnvironmentSecure()
Stellt fest, ob auf das Gerät noch der Sperrmodus-Kontext angewendet wird.

**Syntax**  
`browser.security.isEnvironmentSecure();`

**Parameter**  
`None`

**Rückgabewert**  
`True indicates that the lockdown context is applied to the device; otherwise false.`

**Anforderungen**  
Windows10, Version1607

---

### <a name="tts-namespace"></a>TTS-Namespace

Der TTS-Namespace behandelt die Text-zu-Sprache-Funktion der App.

| Methode | Beschreibung |
|--------|-------------|
|[getStatus](#getStatus) | Ruft den Status der Sprachwiedergabe ab|
|[getVoices](#getVoices) | Ruft eine Liste der verfügbaren Sprachbefehlpakete ab|
|[pause](#pause)|Hält die Sprachsynthese an|
|[resume](#resume)|Setzt die angehaltene Sprachsynthese fort|
|[speak](#speak)|Clientseitige Text-zu-Sprache-Synthese|
|[stop](#stop)|Beendet die Sprachsynthese|

> [!Tip]
> Die [Microsoft Edge Speech Synthesis API](https://blogs.windows.com/msedgedev/2016/06/01/introducing-speech-synthesis-api/) ist eine Implementierung der [W3C-Sprach-API](https://dvcs.w3.org/hg/speech-api/raw-file/tip/webspeechapi.html). Entwicklern wird empfohlen, diese API nach Möglichkeit zu verwenden.

---

<span id="getStatus" />
### <a name="string-getstatus"></a>string getStatus()
Ruft den Status der Sprachwiedergabe ab.

**Syntax**  
`browser.tts.getStatus();`

**Parameter**  
`None`

**Rückgabewert**  
`The speech playback status. Possible values are: “available”, “idle”, “paused”, and “speaking”.`

**Anforderungen**  
Windows10, Version1607

---

<span id="getVoices" />
### <a name="string-getvoices"></a>string[] getVoices()
Ruft eine Liste der verfügbaren Sprachbefehlpakete ab.

**Syntax**  
`browser.tts.getVoices();`

**Parameter**  
`None`

**Rückgabewert**  
`The available voice packs. For example: “Microsoft Zira Mobile”, “Microsoft Mark Mobile”`

**Anforderungen**  
Windows10, Version1607

---

<span id="pause" />
### <a name="void-pause"></a>void pause()

Hält die Sprachsynthese an.

**Syntax**  
`browser.tts.pause();`

**Parameter**

`None`

**Rückgabewert**

`None`

**Anforderungen**  
Windows10, Version1607

---

<span id="resume" />
### <a name="void-resume"></a>void resume()
Setzt die angehaltene Sprachsynthese fort.

**Syntax**  
`browser.tts.resume();`

**Parameter**
`None`

**Rückgabewert**
`None`

**Anforderungen**  
Windows10, Version1607

---

<span id="speak" />
### <a name="void-speakstring-text-object-options-function-callback"></a>void speak(string text, object options, function callback)
Startet die clientseitige Text-zu-Sprache-Synthese.

**Syntax**  
`void browser.tts.speak(“Hello world”, options, callback);`

**Parameter**  
`Speech options such as gender, pitch, rate, volume. For example:`  
```
var options = {
   'gender': this.currentGender,
   'language': this.currentLanguage,
   'pitch': 1,
   'rate': 1,
   'voice': this.currentVoice,
   'volume': 1
};
```

**Rückgabewert**  
`None`

**Anmerkung** Optionsvariablen müssen mit Kleinbuchstaben geschrieben werden. Die Parameter „gender“, „language“ und „voice“ müssen als Zeichenfolgen angegeben werden.
Das Markup für Lautstärke und Tonhöhe muss innerhalb der SSML-Datei (Speech Synthesis Markup Language) und nicht innerhalb des options-Objekts erfolgen.
Beim options-Objekt müssen Reihenfolge, Bezeichnung und Groß-/Kleinschreibung dem obigen Beispiel entsprechen.

**Anforderungen**  
Windows10, Version1607

---

<span id="stop" />
### <a name="void-stop"></a>void stop()
Beendet die Sprachsynthese.

**Syntax**  
`void browser.tts.speak(“Hello world”, options, callback);`

**Parameter**  
`None`

**Rückgabewert**  
`None`

**Anforderungen**  
Windows10, Version1607
