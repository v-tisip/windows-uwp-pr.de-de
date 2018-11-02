---
author: Xansky
description: Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API, um Paketrollout-Informationen für eine App-Übermittlung abzurufen.
title: Abrufen von Informationen zum Rollout für eine App-Übermittlung
ms.author: mhopkins
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Paketrollout, App-Übermittlung
ms.assetid: 9ada5ac3-a86e-4bb6-8ebc-915ba9649e3c
ms.localizationpriority: medium
ms.openlocfilehash: 247c4e58740450bb9846c543e883ac62a8009429
ms.sourcegitcommit: 144f5f127fc4fbd852f2f6780ef26054192d68fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "5969080"
---
# <a name="get-rollout-info-for-an-app-submission"></a>Abrufen von Informationen zum Rollout für eine App-Übermittlung


Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API, um [Paketrollout](../publish/gradual-package-rollout.md)-Informationen für eine Flight-Paket-Übermittlung abzurufen. Weitere Informationen zum Erstellungsprozess einer App-Übermittlung mithilfe der Microsoft Store-Übermittlungs-API finden Sie unter [Verwalten von App-Übermittlungen](manage-app-submissions.md).

## <a name="prerequisites"></a>Voraussetzungen

Zur Verwendung dieser Methode sind folgende Schritte erforderlich:

* Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.
* [Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird. Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft. Wenn das Token abgelaufen ist, können Sie ein neues abrufen.
* Erstellen Sie eine Übermittlung für eine Ihrer apps. Sie erreichen dies im Partner Center, oder Sie können dies tun, indem Sie mit der Methode zum [Erstellen einer app-Übermittlungs](create-an-app-submission.md) .

## <a name="request"></a>Anforderung

Diese Methode hat die folgende Syntax. In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Headers und der Anforderungsparameter.

| Methode | Anforderungs-URI                                                      |
|--------|------------------------------------------------------------------|
| GET   | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/submissions/{submissionId}/packagerollout   ``` |


### <a name="request-header"></a>Anforderungsheader

| Header        | Typ   | Beschreibung                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| Autorisierung | String | Erforderlich. Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;. |


### <a name="request-parameters"></a>Anforderungsparameter

| Name        | Typ   | Beschreibung                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| applicationId | String | Erforderlich. Die Store-ID der App mit der Übermittlung, deren Paketrollout-Informationen abgerufen werden sollen. Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).  |
| submissionId | String | Erforderlich. Die ID der Übermittlung mit den Paketrollout-Informationen, die Sie abrufen möchten. Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer App-Übermittlung](create-an-app-submission.md) verfügbar. Für eine Übermittlung, die im Partner Center erstellt wurde, ist diese ID auch in der URL für die übermittlungsseite im Partner Center verfügbar.  |


### <a name="request-body"></a>Anforderungstext

Stellen Sie keinen Anforderungstext für diese Methode bereit.

### <a name="request-example"></a>Anforderungsbeispiel

Im folgenden Beispiel wird das Abrufen der Paketrollout-Informationen einer App-Übermittlung veranschaulicht.

```
GET https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/submissions/1152921504621243649/packagerollout HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a>Antwort

Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode für eine App-Übermittlung mit aktiviertem schrittweisem Paketrollout. Weitere Informationen zu den Werten im Antworttext finden Sie unter [Paketrollout-Ressource](manage-app-submissions.md#package-rollout-object).

```json
{
    "isPackageRollout": true,
    "packageRolloutPercentage": 25.0,
    "packageRolloutStatus": "PackageRolloutInProgress",
    "fallbackSubmissionId": "1212922684621243058"
}
```

Ist für die App-Übermittlung schrittweises Paketrollout nicht aktiviert, wird folgender Antworttext zurückgegeben.

```json
{
    "isPackageRollout": false,
    "packageRolloutPercentage": 0.0,
    "packageRolloutStatus": "PackageRolloutNotStarted",
    "fallbackSubmissionId": "0"
}
```

## <a name="error-codes"></a>Fehlercodes

Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.

| Fehlercode |  Beschreibung   |
|--------|------------------|
| 404  | Die Übermittlung konnte nicht gefunden werden. |
| 409  | Die Übermittlung gehört nicht zur angegebenen app, oder die app verwendet ein Partner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird. |   


## <a name="related-topics"></a>Verwandte Themen

* [Schrittweiser Paketrollout](../publish/gradual-package-rollout.md)
* [Verwalten von App-Übermittlungen mithilfe der Microsoft Store-Übermittlungs-API](manage-app-submissions.md)
* [Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten](create-and-manage-submissions-using-windows-store-services.md)
