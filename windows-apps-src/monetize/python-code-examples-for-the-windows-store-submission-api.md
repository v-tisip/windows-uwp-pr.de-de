---
author: mcleanbyron
ms.assetid: 8AC56AAF-8D8C-4193-A6B3-BB5D0669D994
description: "Verwenden Sie die Python-Codebeispiele in diesem Abschnitt, um mehr über die Verwendung der Windows Store-Übermittlungs-API zu erfahren."
title: "Python-Codebeispiele für die Übermittlungs-API"
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows10, UWP, Windows Store-Übermittlungs-API, Codebeispiele"
ms.openlocfilehash: a46907ecfea1de60b8a32cdaea7076f056a41ff5
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="python-code-examples-for-the-submission-api"></a>Python-Codebeispiele für die Übermittlungs-API

Dieser Artikel enthält Python-Codebeispiele für das Verwenden der *Windows Store-Übermittlungs-API*. Weitere Informationen über diese API finden Sie unter [Erstellen und Verwalten von Übermittlungen mit WindowsStore-Diensten](create-and-manage-submissions-using-windows-store-services.md).

In diesen Codebeispielen werden die folgenden Aufgaben gezeigt:

* [Abrufen eines Azure AD-Zugriffstokens](#token)
* [Erstellen eines Add-Ons](#create-add-on)
* [Erstellen eines Flight-Pakets](#create-package-flight)
* [Erstellen einer App-Übermittlung](#create-app-submission)
* [Erstellen einer Add-On-Übermittlung](#create-add-on-submission)
* [Erstellen einer Flight-Paket-Übermittlung](#create-flight-submission)

<span id="token" />
## <a name="obtain-an-azure-ad-access-token"></a>Abrufen eines Azure AD-Zugriffstokens

Im folgenden Beispiel wird gezeigt, wie Sie ein [Azure AD-Zugriffstoken abrufen](create-and-manage-submissions-using-windows-store-services.md#obtain-an-azure-ad-access-token), mit dem Sie Methoden in der Windows Store-Übermittlungs-API aufrufen können. Nach dem Abruf eines Zugriffstokens können Sie es für einen Zeitraum von 60Minuten in Aufrufen von Windows Store-Übermittlungs-APIs verwenden, bevor es abläuft. Nach Ablauf des Tokens können Sie ein neues Token generieren.

[!code[SubmissionApi](./code/StoreServicesExamples_Submission/python/Examples.py#L1-L20)]

<span id="create-add-on" />
## <a name="create-an-add-on"></a>Erstellen eines Add-Ons

Das folgende Beispiel zeigt, wie Sie ein Add-On [erstellen](create-an-add-on.md) und anschließend [löschen](delete-an-add-on.md). (Add-Ons werden auch als In-App-Produkte oder IAP bezeichnet.)

[!code[SubmissionApi](./code/StoreServicesExamples_Submission/python/Examples.py#L26-L52)]

<span id="create-package-flight" />
## <a name="create-a-package-flight"></a>Erstellen eines Flight-Pakets

Das folgende Beispiel zeigt, wie Sie EIN Flight-Paket [erstellen](create-a-flight.md) und anschließend [löschen](delete-a-flight.md).

[!code[SubmissionApi](./code/StoreServicesExamples_Submission/python/Examples.py#L58-L87)]

<span id="create-app-submission" />
## <a name="create-an-app-submission"></a>Erstellen einer App-Übermittlung

Das folgende Beispiel zeigt, wie Sie verschiedene Methoden in der Windows Store-Übermittlungs-API verwenden, um eine App-Übermittlung zu erstellen. Hierzu erstellt der Code eine neue Übermittlung als Klon der letzten veröffentlichten Übermittlung, aktualisiert anschließend die geklonte Übermittlung und sendet sie dann an Windows Dev Center. Insbesondere werden im Beispiel folgende Aufgaben gezeigt:

1. Zunächst [werden Daten für die angegebene App abgerufen](get-an-app.md).
2. Als Nächstes [wird eine ausstehende Übermittlung für die App gelöscht](delete-an-app-submission.md), wenn vorhanden.
3. Anschließend [wird eine neue Übermittlung für die App erstellt](create-an-app-submission.md). (Die neue Übermittlung ist eine Kopie der letzten veröffentlichten Übermittlung.)
4. Es werden einige Details für die neue Übermittlung geändert und ein neues Paket für die Übermittlung zu Azure Blob Storage hochgeladen.
5. Als Nächstes wird die neue Übermittlung [aktualisiert](update-an-app-submission.md) und anschließend an Windows Dev Center [gesendet](commit-an-app-submission.md).
6. Schließlich [wird der Status der neuen Übermittlung regelmäßig überprüft](get-status-for-an-app-submission.md), bis die Übermittlung erfolgreich gesendet wurde.

[!code[SubmissionApi](./code/StoreServicesExamples_Submission/python/Examples.py#L93-L166)]

<span id="create-add-on-submission" />
## <a name="create-an-add-on-submission"></a>Erstellen einer Add-On-Übermittlung

Das folgende Beispiel zeigt, wie Sie verschiedene Methoden in der Windows Store-Übermittlungs-API verwenden, um eine Add-On-Übermittlung zu erstellen. Hierzu erstellt der Code eine neue Übermittlung als Klon der letzten veröffentlichten Übermittlung, aktualisiert anschließend die geklonte Übermittlung und sendet sie dann an Windows Dev Center. Insbesondere werden im Beispiel folgende Aufgaben gezeigt:

1. Zunächst [werden Daten für das angegebene Add-On abgerufen](get-an-add-on.md).
2. Als Nächstes [wird eine ausstehende Übermittlung für das Add-On gelöscht](delete-an-add-on-submission.md), wenn vorhanden.
3. Anschließend [wird eine neue Übermittlung für das Add-On erstellt](create-an-add-on-submission.md). (Die neue Übermittlung ist eine Kopie der letzten veröffentlichten Übermittlung.)
4. Es wird ein ZIP-Archiv hochgeladen, das Symbole für die Übermittlung an Azure Blob Storage enthält. Weitere Informationen finden Sie in den entsprechenden Anweisungen zum Hochladen von ZIP-Archiven zu Azure Blob Storage in [Erstellen einer Add-On-Übermittlung](manage-add-on-submissions.md#create-an-add-on-submission).
5. Als Nächstes wird die neue Übermittlung [aktualisiert](update-an-add-on-submission.md) und anschließend an Windows Dev Center [gesendet](commit-an-add-on-submission.md).
6. Schließlich [wird der Status der neuen Übermittlung regelmäßig überprüft](get-status-for-an-add-on-submission.md), bis die Übermittlung erfolgreich gesendet wurde.

[!code[SubmissionApi](./code/StoreServicesExamples_Submission/python/Examples.py#L172-L245)]

<span id="create-flight-submission" />
## <a name="create-a-package-flight-submission"></a>Erstellen einer Flight-Paket-Übermittlung

Das folgende Beispiel zeigt, wie Sie verschiedene Methoden in der Windows Store-Übermittlungs-API verwenden, um eine Flight-Paket-Übermittlung zu erstellen. Hierzu erstellt der Code eine neue Übermittlung als Klon der letzten veröffentlichten Übermittlung, aktualisiert anschließend die geklonte Übermittlung und sendet sie dann an Windows Dev Center. Insbesondere werden im Beispiel folgende Aufgaben gezeigt:

1. Zunächst [werden Daten für das angegebene Flight-Paket abgerufen](get-a-flight.md).
2. Als Nächstes [wird eine ausstehende Übermittlung für das Flight-Paket gelöscht](delete-a-flight-submission.md), wenn vorhanden.
3. Anschließend [wird eine neue Übermittlung für das Flight-Paket erstellt](create-a-flight-submission.md). (Die neue Übermittlung ist eine Kopie der letzten veröffentlichten Übermittlung.)
4. Es wird ein neues Paket für die Übermittlung an Azure Blob Storage hochgeladen. Weitere Informationen finden Sie in den entsprechenden Anweisungen zum Hochladen von ZIP-Archiven zu Azure Blob Storage in [Erstellen einer Flight-Paket-Übermittlung](manage-flight-submissions.md#create-a-package-flight-submission).
5. Als Nächstes wird die neue Übermittlung [aktualisiert](update-a-flight-submission.md) und anschließend an Windows Dev Center [gesendet](commit-a-flight-submission.md).
6. Schließlich [wird der Status der neuen Übermittlung regelmäßig überprüft](get-status-for-a-flight-submission.md), bis die Übermittlung erfolgreich gesendet wurde.

[!code[SubmissionApi](./code/StoreServicesExamples_Submission/python/Examples.py#L251-L325)]

## <a name="related-topics"></a>Verwandte Themen

* [Erstellen und Verwalten von Übermittlungen mit WindowsStore-Diensten](create-and-manage-submissions-using-windows-store-services.md)
