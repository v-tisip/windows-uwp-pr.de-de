---
author: JnHs
Description: Target specific segments of your customers with personalized content to increase engagement, retention, and monetization.
title: Verwenden Sie gezielte Angebote, um Interaktionen und Abschlüsse zu maximieren.
ms.author: wdg-dev-content
ms.date: 11/10/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, gezielte Angebote, Angebote, Benachrichtigungen
ms.localizationpriority: medium
ms.openlocfilehash: 727c438bacf51fd2ead03df72421363116c4701b
ms.sourcegitcommit: 49aab071aa2bd88f1c165438ee7e5c854b3e4f61
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2018
ms.locfileid: "4462531"
---
# <a name="use-targeted-offers-to-maximize-engagement-and-conversions"></a>Verwenden Sie gezielte Angebote, um Interaktionen und Abschlüsse zu maximieren.

Sprechen Sie für bessere Interaktion, Kundenbindung und Monetarisierung bestimmte Segmente Ihrer Kunden mit attraktivem, personalisiertem Inhalt an.

> [!IMPORTANT]
> Zielgerichtete Angebote können nur mit UWP-Apps verwendet werden, die Add-Ons enthalten.

## <a name="targeted-offer-overview"></a>Übersicht über zielgerichtete Angebote

Allgemein gesagt müssen Sie drei durchführen, um die zielgerichteten Angebote zu verwenden:

1. **Erstellen Sie das Angebot auf Ihrem Dashboard.** Navigieren Sie zur Seite **Bewerben > zielgerichtete Angebote**, um Angebote zu erstellen. Weitere Informationen zu diesem Prozess sind im Folgenden beschrieben.
2. **Implementieren Sie das In-App-Angebot.** Verwenden Sie die *Microsoft Store für gezielte Angebote API* in Ihrem app Code, um die verfügbaren Angebote für einen bestimmten Benutzer abzurufen. Sie müssen auch die In-App-Umgebung für das gezielte Angebot erstellen. Weitere Informationen finden Sie unter [Verwalten gezielter Angebote mithilfe von Store-Diensten](../monetize/manage-targeted-offers-using-windows-store-services.md).
3. **Übermitteln Ihrer App an den Store.** Ihre App muss mit dem integrierten In-App-Angebot veröffentlicht werden, damit die Angebote für Kunden verfügbar sind.

Nachdem Sie diese Schritte abgeschlossen haben, werden Kunden, die Ihre App verwenden, die Angebote angezeigt, die zu diesem Zeitpunkt für ihn verfügbar sind, basierend auf seiner Mitgliedschaft in dem diesem Angebot zugeordneten Segment. Beachten Sie, dass wir zwar bemüht sind, alle verfügbaren Angebote für Ihre Kunden anzuzeigen, es jedoch gelegentlich zu Problemen kommen kann, die die Angebotsverfügbarkeit beeinträchtigen.


## <a name="to-create-and-send-a-targeted-offer"></a>So erstellen und senden Sie ein gezieltes Angebot

Führen Sie diese Schritte aus, um ein gezieltes Angebot im Dashboard zu erstellen.

1.  Erweitern Sie im Windows Dev Center-Dashboard **Einbeziehen** im linken Navigationsmenü und wählen Sie dann **zielgerichtete Angebote** aus.
2.  Überprüfen Sie auf der Seite **zielgerichtete Angebote** die verfügbaren Angebote. Wählen Sie **Create new offer** für ein Angebot, das Sie implementieren möchten.

    > [!NOTE]
    > Die angezeigten verfügbaren Angebote ändern sich im Laufe der Zeit und auf der Grundlage von Kontokriterien.

3.  Wählen Sie in der neuen Zeile, die unter den verfügbaren Angebote angezeigt wird, das Produkt (App) aus, in dem das Angebot zur Verfügung steht. Wählen Sie dann das Add-On aus, das Sie dem Angebot zuordnen möchten.
4.  Wiederholen Sie die Schritte2 und 3, wenn Sie weitere Angebote erstellen möchten. Sie können den gleichen Angebotstyp mehrmals in derselben App implementieren, solange Sie für jedes Angebot andere Add-Ons auswählen. Darüber hinaus können Sie das gleiche Add-On mehr als einem Angebotstyp zuordnen.
5.  Klicken Sie auf **Speichern**, wenn Sie mit dem Erstellen der Angebote fertig sind.

Nachdem Sie Ihr Angebot implementiert haben, können Sie die Gesamtanzahl von Abschlüssen für jedes Angebot auf der Seite **Zielgerichtete Angebote** in Ihrem Dashboard anzeigen.

Wenn Sie sich entscheiden, kein Angebot zu verwenden (oder wenn Sie es nicht mehr verwenden möchten), klicken Sie auf **Löschen**.

> [!IMPORTANT]
> Achten Sie darauf, dass Sie den Code veröffentlichen, um die verfügbaren Angebote für einen bestimmten Benutzer abzurufen und die In-App-Umgebung zu erstellen. Weitere Informationen finden Sie unter [Verwalten gezielter Angebote mithilfe von Store-Diensten](../monetize/manage-targeted-offers-using-windows-store-services.md).
>
> Beachten Sie bei den Inhalten gezielter Angebote, dass sie wie der gesamte App-Inhalt die [Inhaltsrichtlinien](https://docs.microsoft.com/en-us/legal/windows/agreements/store-policies) des Stores erfüllen müssen.
>
> Beachten Sie außerdem Folgendes: Wenn ein Kunde, der Ihre App verwendet (und zum Zeitpunkt, zu dem die Segmentmitgliedschaft bestimmt wird, mit seinem Microsoft-Konto angemeldet ist) das Gerät später an eine andere Person übergibt, sieht die andere Person unter Umständen das Angebot, das für den ursprünglichen Kunden bestimmt war.
