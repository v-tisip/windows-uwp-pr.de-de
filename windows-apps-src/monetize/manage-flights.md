---
author: mcleanbyron
ms.assetid: 37F2C162-4910-4336-BEED-8536C88DCA65
description: "Verwenden Sie diese Methoden in der Windows Store-Übermittlungs-API, um Flight-Pakete für Apps zu verwalten, die in Ihrem Windows Dev Center-Konto registriert wurden."
title: "Verwalten von Flight-Paketen mithilfe der Windows Store-Übermittlungs-API"
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP, Windows Store-Übermittlung-API, Flights"
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 51d7481d0491c85bddcae906a846cb8773f33417
ms.lasthandoff: 02/07/2017

---

# <a name="manage-package-flights-using-the-windows-store-submission-api"></a>Verwalten von Flight-Paketen mithilfe der Windows Store-Übermittlungs-API

Mithilfe der folgenden Methoden in der Windows Store-Übermittlungs-API können Sie Flight-Pakete für Ihre Apps verwalten. Eine Einführung in die Windows Store-Übermittlungs-API einschließlich der Voraussetzungen für die Verwendung der API finden Sie unter [Erstellen und Verwalten von Übermittlungen mit Windows Store-Diensten](create-and-manage-submissions-using-windows-store-services.md).

>**Hinweis**&nbsp;&nbsp;Diese Methoden können nur für Windows Dev Center-Konten verwendet werden, die zur Verwendung der Windows Store-Übermittlungs-API berechtigt sind. Diese Berechtigung wird für Entwicklerkonten phasenweise aktiviert, und die Berechtigung ist zu diesem Zeitpunkt nicht für alle Konten aktiviert. Um früheren Zugriff anfordern, melden Sie sich beim Dev Center-Dashboard an, klicken Sie am unteren Rand des Dashboards auf **Feedback**, wählen Sie **Übermittlungs-API** für den Feedback-Bereich, und übermitteln Sie Ihre Anforderung. Sie erhalten eine E-Mail, wenn diese Berechtigung für Ihr Konto aktiviert ist.

Diese Methoden können nur verwendet werden, um Flight-Pakete abzurufen, zu erstellen oder zu löschen. Verwenden Sie zum Erstellen von Übermittlungen für Flight-Pakete die Methoden unter [Verwalten von Flight-Paket-Übermittlungen](manage-flight-submissions.md).

<table>
<colgroup>
<col width="10%" />
<col width="30%" />
<col width="60%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Methode</th>
<th align="left">URI</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr>
<td align="left">GET</td>
<td align="left">```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}```</td>
<td align="left">[Abrufen eines Flight-Pakets](get-a-flight.md)</td>
</tr>
<tr>
<td align="left">POST</td>
<td align="left">```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights```</td>
<td align="left">[Erstellen eines Flight-Pakets](create-a-flight.md)</td>
</tr>
<tr>
<td align="left">DELETE</td>
<td align="left">```https://manage.devcenter.microsoft.com/v1.0/my/applications/{applicationId}/flights/{flightId}```</td>
<td align="left">[Löschen eines Flight-Pakets](delete-a-flight.md)</td>
</tr>
</tbody>
</table>

## <a name="prerequisites"></a>Voraussetzungen

Falls noch nicht geschehen, sorgen Sie vor der Verwendung dieser Methoden dafür, dass alle [Voraussetzungen](create-and-manage-submissions-using-windows-store-services.md#prerequisites) für die Windows Store-Übermittlungs-API erfüllt sind.

## <a name="related-topics"></a>Verwandte Themen

* [Erstellen und Verwalten von Übermittlungen mit Windows Store-Diensten](create-and-manage-submissions-using-windows-store-services.md)
* [Verwalten von Flight-Paket-Übermittlungen](manage-flight-submissions.md)

