---
description: Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API, um den Paketrollout für eine App-Übermittlung fertigzustellen.
title: Abschließen des Rollouts einer App-Übermittlung
ms.date: 04/17/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Übermittlungs-API, Paketrollout, App-Übermittlung, fertigstellen
ms.assetid: c7dd39e6-5162-455a-b03b-1ed76bffcf6e
ms.localizationpriority: medium
ms.openlocfilehash: c8fe211268190ac269018a6bd47acb4b824d2075
ms.sourcegitcommit: a3dc929858415b933943bba5aa7487ffa721899f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "8808535"
---
# <a name="finalize-the-rollout-for-an-app-submission"></a>Abschließen des Rollouts einer App-Übermittlung


Verwenden Sie diese Methode der Microsoft Store-Übermittlungs-API zur [Fertigstellung des Paketrollouts](../publish/gradual-package-rollout.md#completing-the-rollout) für eine App-Übermittlung. Weitere Informationen zum Erstellungsprozess einer App-Übermittlung mithilfe der Microsoft Store-Übermittlungs-API finden Sie unter [Verwalten von App-Übermittlungen](manage-app-submissions.md).

## <a name="prerequisites"></a>Voraussetzungen

Zur Verwendung dieser Methode sind folgende Schritte erforderlich:

* Falls noch nicht geschehen, erfüllen Sie alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Microsoft Store-Übermittlungs-API.
* [Rufen Sie ein Azure AD-Zugriffstoken ab](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), das im Anforderungsheader für diese Methode verwendet wird. Nachdem Sie ein Zugriffstoken abgerufen haben, können Sie es 60 Minuten lang verwenden, bevor es abläuft. Wenn das Token abgelaufen ist, können Sie ein neues abrufen.
* Erstellen Sie eine Übermittlung für eine app im Partner Center-Konto. Sie können dies im Partner Center oder können Sie dies tun, indem Sie mithilfe der Methode zum [Erstellen einer app-Übermittlungs](create-an-app-submission.md) .
* Ermöglichen Sie einen schrittweisen Paketrollout für die Übermittlung. Sie können diese [im Partner Center](../publish/gradual-package-rollout.md), oder Sie können dies tun, indem Sie [mithilfe der Microsoft Store-Übermittlungs-API](manage-app-submissions.md#manage-gradual-package-rollout).

## <a name="request"></a>Anforderung

Diese Methode hat die folgende Syntax. In den folgenden Abschnitten finden Sie Verwendungsbeispiele und Beschreibungen des Headers und der Anforderungsparameter.

| Methode | Anforderungs-URI                                                      |
|--------|------------------------------------------------------------------|
| POST   | ```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/submissions/{submissionId}/finalizepackagerollout``` |


### <a name="request-header"></a>Anforderungsheader

| Header        | Typ   | Beschreibung                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| Autorisierung | String | Erforderlich. Das Azure AD-Zugriffstoken im Format **Bearer** &lt;*token*&gt;. |


### <a name="request-parameters"></a>Anforderungsparameter

| Name        | Typ   | Beschreibung                                                                 |
|---------------|--------|-----------------------------------------------------------------------------|
| applicationId | String | Erforderlich. Die Store-ID der App mit der Übermittlung, deren Paketrollout fertig gestellt werden soll. Weitere Informationen zur Store-ID finden Sie unter [Anzeigen von Details zur App-Identität](https://msdn.microsoft.com/windows/uwp/publish/view-app-identity-details).  |
| submissionId | String | Erforderlich. Die ID der Übermittlung mit dem Paketrollout, der fertig gestellt werden soll. Diese ID ist in den Antwortdaten für Anforderungen zum [Erstellen einer App-Übermittlung](create-an-app-submission.md) verfügbar. Für eine Übermittlung, die im Partner Center erstellt wurde, ist diese ID auch in der URL für die übermittlungsseite im Partner Center verfügbar.  |


### <a name="request-body"></a>Anforderungstext

Stellen Sie keinen Anforderungstext für diese Methode bereit.

### <a name="request-example"></a>Anforderungsbeispiel

Im folgenden Beispiel wird die Fertigstellung des Paketrollouts für eine Flight-Paket-Übermittlung veranschaulicht.

```
POST https://manage.devcenter.microsoft.com/v1.0/my/applications/9NBLGGH4R315/submissions/1152921504621243680/finalizepackagerollout HTTP/1.1
Authorization: Bearer <your access token>
```

## <a name="response"></a>Antwort

Das folgende Beispiel veranschaulicht den JSON-Antworttext für einen erfolgreichen Aufruf dieser Methode. Weitere Informationen zu den Werten im Antworttext finden Sie unter der [Ressource zum Paketrollout](manage-app-submissions.md#package-rollout-object).

```json
{
    "isPackageRollout": true,
    "packageRolloutPercentage": 100.0,
    "packageRolloutStatus": "PackageRolloutComplete",
    "fallbackSubmissionId": "1212922684621243058"
}
```


## <a name="error-codes"></a>Fehlercodes

Wenn die Anforderung nicht erfolgreich abgeschlossen werden kann, enthält die Antwort einen der folgenden HTTP-Fehlercodes.

| Fehlercode |  Beschreibung   |
|--------|------------------|
| 404  | Die Übermittlung konnte nicht gefunden werden. |
| 409  | Dieser Code weist auf einen der folgenden Fehler hin:<br/><br/><ul><li>Die Übermittlung befindet sich nicht in einem gültigen Status für den schrittweisen Rollout (vor dem Aufrufen dieser Methode muss die Übermittlung veröffentlicht und der Wert für [PackageRolloutStatus](manage-app-submissions.md#package-rollout-object) auf **PackageRolloutInProgress** festgelegt werden).</li><li>Die Übermittlung gehört nicht zur angegebenen App.</li><li>Die app verwendet ein DevPartner Center-Feature, das [derzeit nicht von der Microsoft Store-Übermittlungs-API unterstützt](create-and-manage-submissions-using-windows-store-services.md#not_supported)wird.</li></ul> |   


## <a name="related-topics"></a>Verwandte Themen

* [Schrittweiser Paketrollout](../publish/gradual-package-rollout.md)
* [Verwalten von App-Übermittlungen mithilfe der Microsoft Store-Übermittlungs-API](manage-app-submissions.md)
* [Erstellen und Verwalten von Übermittlungen mit Microsoft Store-Diensten](create-and-manage-submissions-using-windows-store-services.md)
