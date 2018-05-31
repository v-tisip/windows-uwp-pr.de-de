---
author: mcleanbyron
ms.assetid: E64030CA-EC00-4113-9939-26D5688C61BC
description: Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die CAB-Datei für einen Hardwarefehler herunterladen. Diese Methode ist nur für OEMs bestimmt.
title: Herunterladen der CAB-Datei für einen OEM-Hardwarefehler
ms.author: mcleans
ms.date: 03/17/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Microsoft Store-Analyse-API, CAB herunterladen
ms.localizationpriority: medium
ms.openlocfilehash: 0be709136ed5875d69431f0ab60efd76f5bbc80b
ms.sourcegitcommit: 1773bec0f46906d7b4d71451ba03f47017a87fec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2018
ms.locfileid: "1662820"
---
# <a name="download-the-cab-file-for-an-oem-hardware-error"></a>Herunterladen der CAB-Datei für einen OEM-Hardwarefehler

Verwenden Sie diese Methode in der Microsoft Store-Analyse-API, um die CAB-Datei herunterzuladen, die einem bestimmten OEM-Hardwarefehler zugeordnet ist. Bevor Sie diese Methode verwenden können, müssen Sie zuerst anhand der Methode zum [Abrufen von Informationen zu einem OEM-Hardwarefehler](get-details-for-an-oem-hardware-error.md) die ID der CAB-Datei abrufen, die Sie herunterladen möchten.

Anhand der Methoden zum [Abrufen von Fehlerberichtsdaten für OEM-Hardware](get-oem-hardware-error-reporting-data.md) und zum [Abrufen von Informationen zu einem OEM-Hardwarefehler](get-details-for-an-oem-hardware-error.md) in der Microsoft Store-Analyse-API können Sie weitere Informationen zu OEM-Hardwarefehlern abrufen.

> [!NOTE]
> Diese Methode kann nur von Entwicklerkonten verwendet werden, die zum [Windows Hardware Dev Center-Programm](https://msdn.microsoft.com/windows/hardware/drivers/dashboard/get-started-with-the-hardware-dashboard) gehören.

## <a name="prerequisites"></a>Voraussetzungen

Zur Verwendung dieser Methode sind folgende Schritte erforderlich:

* Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Microsoft Store-Analyse-API.
* [Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird. Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft. Wenn das Token abgelaufen ist, können Sie ein neues abrufen.
* Rufen Sie die ID der CAB-Datei ab, die Sie herunterladen möchten. Verwenden Sie zum Abrufen dieser ID die Methode zum [Abrufen von Informationen zu einem OEM-Hardwarefehler](get-details-for-an-oem-hardware-error.md), um Details zu einem bestimmten Hardwarefehler in Ihrer App abzurufen, und verwenden Sie den **cabIdHash**-Wert im Antworttext dieser Methode.

## <a name="request"></a>Anforderung


### <a name="request-syntax"></a>Anforderungssyntax

| Methode | Anforderungs-URI                                                          |
|--------|----------------------------------------------------------------------|
| GET    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/hardware/cabdownload``` |


### <a name="request-header"></a>Anforderungsheader

| Header        | Typ   | Beschreibung                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| Autorisierung | String | Erforderlich. Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;. |


### <a name="request-parameters"></a>Anforderungsparameter

| Parameter        | Typ   |  Beschreibung      |  Erforderlich  |
|---------------|--------|---------------|------|
| cabIdHash | String | Die eindeutige ID der CAB-Datei ab, die Sie herunterladen möchten. Verwenden Sie zum Abrufen dieser ID die Methode zum [Abrufen von Informationen zu einem OEM-Hardwarefehler](get-details-for-an-oem-hardware-error.md), um Details zu einem bestimmten Fehler in Ihrer App abzurufen, und verwenden Sie den **cabIdHash**-Wert im Antworttext dieser Methode. |  Ja  |

 
### <a name="request-example"></a>Anforderungsbeispiel

Im folgenden Beispiel wird gezeigt, wie Sie mit dieser Methode eine CAB-Datei herunterladen.

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/hardware/cabdownload?cabIdHash=c1a51104-d682-4230-be14-7278b18e3555 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a>Antwort

Bei dieser Methode wird ein 302-Antwortcode (Umleitung) zurückgegeben, und der **Speicherort**-Header in der Antwort wird der Shared Access Signature (SAS)-URI der CAB-Datei zugewiesen. Der Aufrufer wird zu dieser URI für den automatischen Download der CAB-Datei weitergeleitet.

## <a name="related-topics"></a>Verwandte Themen

* [Abrufen von Fehlerberichtsdaten für OEM-Hardware](get-oem-hardware-error-reporting-data.md)
* [Abrufen von Informationen zu einem OEM-Hardwarefehler](get-details-for-an-oem-hardware-error.md)
