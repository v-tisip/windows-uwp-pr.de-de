---
author: WilliamsJason
title: "Geräteportal – API-Referenz für Fiddler"
description: Erfahren Sie, wie Sie die Fiddler-Ablaufverfolgung programmgesteuert aktivieren/deaktivieren.
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.assetid: e7d4225e-ac2c-41dc-aca7-9b1a95ec590b
translationtype: Human Translation
ms.sourcegitcommit: 5645eee3dc2ef67b5263b08800b0f96eb8a0a7da
ms.openlocfilehash: 24e966f953928d238f9197359e0b539b8a3e5c3c
ms.lasthandoff: 02/08/2017

---

# <a name="fiddler-settings-api-reference"></a>Fiddler-Einstellungen – API-Referenz   
Sie können die Fiddler-Netzwerkablaufverfolgung für Ihr Dev Kit mittels dieser REST-API aktivieren und deaktivieren.

## <a name="enable-fiddler-tracing"></a>Aktivieren der Fiddler-Ablaufverfolgung

**Anforderung**

Sie können die Fiddler-Ablaufverfolgung mittels der folgenden Anforderung für das Dev Kit verwenden.  Beachten Sie, dass das Gerät neu gestartet werden muss, bevor dies wirksam wird.

Methode      | Anforderungs-URI
:------     | :-----
POST | /ext/fiddler
<br />
**URI-Parameter**

Sie können im Anforderungs-URI die folgenden zusätzlichen Parameter angeben:

| URI-Parameter      | Beschreibung     | 
| ------------------ |-----------------|
| proxyAddress       | Die IP-Adresse oder der Hostnamen des Geräts, auf dem Fiddler ausgeführt wird. |
| proxyPort          | Der Port, den Fiddler für die Überwachung des Datenverkehrs verwendet. Der Standardport ist 8888. |
| updateCert (optional)| Ein boolescher Wert, der angibt, ob das Fiddler-Stammzertifikat angegeben wird. Dieser Wert muss true sein, wenn Fiddler nie zuvor für dieses Dev Kit oder für einen anderen Host konfiguriert wurde.  |
<br>

**Anforderungsheader**

- Keiner

**Anforderungstext**

- Keiner, wenn updateCert false ist oder nicht angegeben wird. Andernfalls mehrteiliger konformer http-Text, der die Datei FiddlerRoot.cer enthält.

**Antwort**   

- Keine  

**Statuscode**

Diese API hat die folgenden erwarteten Statuscodes.

HTTP-Statuscode      | Beschreibung
:------     | :-----
204 | Die Anforderung für die Aktivierung von Fiddler wurde akzeptiert. Fiddler wird aktiviert, wenn das Gerät das nächste Mal neu gestartet wird.
4XX | Fehlercodes
5XX | Fehlercodes

## <a name="disable-fiddler-tracing-on-the-devkit"></a>Deaktivieren Sie die Fiddler-Ablaufverfolgung für das Dev Kit.

**Anforderung**

Sie können die Fiddler-Ablaufverfolgung mithilfe der folgenden Anforderung für das Gerät deaktivieren. Beachten Sie, dass das Gerät neu gestartet werden muss, bevor dies wirksam wird.

Methode      | Anforderungs-URI
:------     | :-----
DELETE | /ext/fiddler
<br />
**URI-Parameter**

- Keiner

**Anforderungsheader**

- Keiner

**Anforderungstext**   

- Keiner

**Antwort**   

- Keine 

**Statuscode**

Diese API hat die folgenden erwarteten Statuscodes.

HTTP-Statuscode      | Beschreibung
:------     | :-----
204 | Die Anforderung zum Deaktivieren der Fiddler-Ablaufverfolgung war erfolgreich. Die Nachverfolgung wird deaktiviert, wenn das Gerät das nächste Mal neu gestartet wird.
4XX | Fehlercodes
5XX | Fehlercodes

<br />
**Verfügbare Gerätefamilien**

* Windows Xbox

## <a name="see-also"></a>Siehe auch
- [Konfigurieren von Fiddler für UWP auf Xbox](uwp-fiddler.md)


