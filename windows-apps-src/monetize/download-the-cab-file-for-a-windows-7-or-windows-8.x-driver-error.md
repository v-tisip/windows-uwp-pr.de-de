---
author: mcleanbyron
ms.assetid: 48D891CD-706C-4759-AB33-B0663774A829
description: "Verwenden Sie diese Methode in der Windows Store-Analyse-API, um die CAB-Datei für einen Windows7- oder Windows8.x Treiberfehler herunterzuladen. Diese Methode ist nur für IHVs bestimmt."
title: "Herunterladen der CAB-Datei für einen Windows7- oder Windows8.x-Treiberfehler"
ms.author: mcleans
ms.date: 03/17/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Windows Store-Analyse-API, CAB herunterladen
ms.openlocfilehash: 622ad656a64381e80549bc286a4d30490e488631
ms.sourcegitcommit: 64cfb79fd27b09d49df99e8c9c46792c884593a7
translationtype: HT
---
# <a name="download-the-cab-file-for-a-windows-7-or-windows-8x-driver-error"></a>Herunterladen der CAB-Datei für einen Windows7- oder Windows8.x-Treiberfehler

Verwenden Sie diese Methode in der Windows Store-Analyse-API, um die CAB-Datei herunterzuladen, die mit einem bestimmten Windows7-/Windows8.x-Treiberfehler verknüpft ist. Bevor Sie diese Methode verwenden können, müssen Sie zuerst anhand der Methode zum [Abrufen von Informationen zu einem Windows7- oder Windows8.x-Treiberfehler](get-details-for-a-windows-7-or-windows-8.x-driver-error.md) die ID der CAB-Datei abrufen, die Sie herunterladen möchten.

Anhand der Methoden zum [Abrufen von Fehlerberichtsdaten für Windows7- und Windows8.x-Treiber](get-error-reporting-data-for-windows-7-and-windows-8.x-drivers.md) und [Abrufen von Informationen zu einem Windows7- oder Windows8.x-Treiberfehler](get-details-for-a-windows-7-or-windows-8.x-driver-error.md) in der Windows Store-Analyse-API können Sie weitere Informationen zu Windows7-/Windows8.x-Treiberfehlern abrufen.

> [!NOTE]
> Diese Methode kann nur von Entwicklerkonten verwendet werden, die zum [Windows Hardware Dev Center-Programm](https://msdn.microsoft.com/windows/hardware/drivers/dashboard/get-started-with-the-hardware-dashboard) gehören.

## <a name="prerequisites"></a>Voraussetzungen

Zur Verwendung dieser Methode sind folgende Schritte erforderlich:

* Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](access-analytics-data-using-windows-store-services.md#prerequisites) für die Windows Store-Analyse-API.
* [Rufen Sie ein Azure AD-Zugriffstoken ab](access-analytics-data-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird. Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft. Wenn das Token abgelaufen ist, können Sie ein neues abrufen.
* Rufen Sie die ID der CAB-Datei ab, die Sie herunterladen möchten. Verwenden Sie zum Abrufen dieser ID die Methode zum [Abrufen von Informationen zu einem Windows7- oder Windows8.x-Treiberfehler](get-details-for-a-windows-7-or-windows-8.x-driver-error.md), um Details zu einem bestimmten Treiberfehler abzurufen, und verwenden Sie den **cabIdHash**-Wert im Antworttext dieser Methode.

## <a name="request"></a>Anforderung


### <a name="request-syntax"></a>Anforderungssyntax

| Methode | Anforderungs-URI                                                          |
|--------|----------------------------------------------------------------------|
| GET    | ```https://manage.devcenter.microsoft.com/v1.0/my/analytics/ihvdriver/cabdownload``` |

<span/> 

### <a name="request-header"></a>Anforderungsheader

| Header        | Typ   | Beschreibung                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| Autorisierung | String | Erforderlich. Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;. |

<span/> 

### <a name="request-parameters"></a>Anforderungsparameter

| Parameter        | Typ   |  Beschreibung      |  Erforderlich  |
|---------------|--------|---------------|------|
| cabIdHash | String | Die eindeutige ID der CAB-Datei ab, die Sie herunterladen möchten. Verwenden Sie zum Abrufen dieser ID die Methode zum [Abrufen von Informationen zu einem Windows7- oder Windows8.x-Treiberfehler](get-details-for-a-windows-7-or-windows-8.x-driver-error.md), um Details zu einem bestimmten Fehler in Ihrer App abzurufen, und verwenden Sie den **cabIdHash**-Wert im Antworttext dieser Methode. |  Ja  |

<span/>
 
### <a name="request-example"></a>Anforderungsbeispiel

Im folgenden Beispiel wird gezeigt, wie Sie mit dieser Methode eine CAB-Datei herunterladen.

```syntax
GET https://manage.devcenter.microsoft.com/v1.0/my/analytics/ihvdriver/cabdownload?cabIdHash=c1a51104-d682-4230-be14-7278b18e3555 HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a>Antwort

Bei dieser Methode wird ein 302-Antwortcode (Umleitung) zurückgegeben, und der **Speicherort**-Header in der Antwort wird der Shared Access Signature (SAS)-URI der CAB-Datei zugewiesen. Der Aufrufer wird zu dieser URI für den automatischen Download der CAB-Datei weitergeleitet.

## <a name="related-topics"></a>Verwandte Themen

* [Abrufen von Fehlerberichtsdaten für Windows7- und Windows8.x-Treiber](get-error-reporting-data-for-windows-7-and-windows-8.x-drivers.md)
* [Abrufen von Informationen zu einem Windows7- oder Windows8.x-Treiberfehler](get-details-for-a-windows-7-or-windows-8.x-driver-error.md)
