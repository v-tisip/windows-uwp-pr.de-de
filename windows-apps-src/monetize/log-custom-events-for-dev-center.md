---
author: Xansky
Description: You can log custom events from your UWP app and review those events in the Usage report in Partner Center.
title: Protokollieren Sie benutzerdefinierter Ereignisse für Partner Center
ms.author: mhopkins
ms.date: 06/01/2018
ms.topic: article
keywords: Windows10, UWP, Microsoft Store-Services-SDK, Ereignisse protokollieren
ms.assetid: 4aa591e0-c22a-4c90-b316-0b5d0410af19
ms.localizationpriority: medium
ms.openlocfilehash: 47c1eb02434dc71cb7da949d58ec38cf3b4cf65a
ms.sourcegitcommit: e814a13978f33654d8e995584f4b047cb53e0aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "6047455"
---
# <a name="log-custom-events-for-partner-center"></a>Protokollieren Sie benutzerdefinierter Ereignisse für Partner Center

Der [Bericht "Nutzung"](https://msdn.microsoft.com/windows/uwp/publish/usage-report) im Partner Center können Sie das Abrufen von Informationen über benutzerdefinierte Ereignisse, die Sie in Ihrer app (universelle Windows Plattform) definiert haben. Ein benutzerdefiniertes Ereignis ist eine beliebige Zeichenfolge, die ein Ereignis oder eine Aktivität in Ihrer App repräsentiert. Beispielsweise kann ein Spiel benutzerdefinierte Ereignisse mit den Bezeichnungen *FirstLevelPassed*, *SecondLevelPassed*usw. definieren, die protokolliert werden, wenn der Benutzer die einzelnen Levels des Spiels durchläuft.

Um ein benutzerdefiniertes Ereignis aus Ihrer App zu protokollieren, übergeben Sie die Zeichenfolge des benutzerdefinierten Ereignisses an die [Log](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicescustomeventlogger.log)-Methode des Microsoft Store Services SDK. Sie können alle Instanzen für Ihre benutzerdefinierten Ereignisse im Abschnitt **benutzerdefinierte Ereignisse** im [Bericht "Nutzung"](https://msdn.microsoft.com/windows/uwp/publish/usage-report) im Partner Center überprüfen.

> [!NOTE]
> Benutzerdefinierte Ereignisse, die Sie in das Partner Center anmelden, werden nicht im Zusammenhang mit [Windows-Ereignisse](https://msdn.microsoft.com/library/windows/desktop/aa964766.aspx), und sie werden nicht in der **Ereignisanzeige**angezeigt.

## <a name="prerequisites"></a>Voraussetzungen

Bevor Sie benutzerdefinierte Protokollereignisse im **Bericht "Nutzung"** für Ihre app im Partner Center überprüfen können, muss Ihre app im Store veröffentlicht werden.

## <a name="how-to-log-custom-events"></a>Protokollieren von benutzerdefinierten Ereignissen

1. Falls noch nicht geschehen, [installieren Sie das Microsoft Store Services SDK](microsoft-store-services-sdk.md#install-the-sdk) auf Ihrem Entwicklungscomputer.

2. Öffnen Sie das Projekt in Visual Studio.

3. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Knoten **Verweise** für Ihr Projekt, und wählen Sie anschließend **Verweis hinzufügen** aus.

4. Erweitern Sie im **Verweis-Manager** die Option **Universelle Windows-App**, und klicken Sie auf **Erweiterungen**.

5. Klicken Sie in der Liste der SDKs auf das Kontrollkästchen neben **Microsoft Engagement Framework** und anschließend auf **OK**.

6. Fügen Sie die folgende Anweisung am Anfang jeder Codedatei hinzu, in der Sie benutzerdefinierte Ereignisse protokollieren möchten.
    [!code-cs[EventLogger](./code/StoreSDKSamples/cs/LogEvents.cs#EngagementNamespace)]

7. Rufen Sie in jedem Abschnittdes Codes, in dem Sie ein benutzerdefiniertes Ereignis protokollieren möchten, ein [StoreServicesCustomEventLogger](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicescustomeventlogger.log)-Objekt ab, und rufen Sie dann die [Protokoll](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicescustomeventlogger.log)-Methode auf. Übergeben Sie die Zeichenfolge für das benutzerdefinierte Ereignis an die Methode.
    [!code-cs[EventLogger](./code/StoreSDKSamples/cs/LogEvents.cs#Log)]

    > [!NOTE]
    > Möglicherweise dauert das Laden des [Nutzungsberichts](https://msdn.microsoft.com/windows/uwp/publish/usage-report) lange, wenn Ihre App viele benutzerdefinierte Ereignisse mit langen Namen protokolliert. Es wird empfohlen, dass kurze Namen für Ihre benutzerdefinierten Ereignisse zu verwenden. 

## <a name="related-topics"></a>Verwandte Themen

* [Nutzungsbericht](https://msdn.microsoft.com/windows/uwp/publish/usage-report)
* [Protokollierungsmethode](https://docs.microsoft.com/uwp/api/microsoft.services.store.engagement.storeservicescustomeventlogger.log)
* [Microsoft Store Services SDK](https://msdn.microsoft.com/windows/uwp/monetize/microsoft-store-services-sdk)
