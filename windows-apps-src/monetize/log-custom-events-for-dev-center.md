---
author: mcleanbyron
Description: "Sie können benutzerdefinierte Ereignisse von Ihrer UWP-App aus protokollieren und sie im Nutzungsbericht im Windows Dev Center-Dashboard überprüfen."
title: "Protokollieren benutzerdefinierter Ereignisse für Dev Center"
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP, Microsoft Store-Services-SDK, Ereignisse protokollieren"
ms.assetid: 4aa591e0-c22a-4c90-b316-0b5d0410af19
translationtype: Human Translation
ms.sourcegitcommit: 5645eee3dc2ef67b5263b08800b0f96eb8a0a7da
ms.openlocfilehash: 80cc3ec6aab90549c55ff8c8f78b54f5827f61ff
ms.lasthandoff: 02/08/2017

---

# <a name="log-custom-events-for-dev-center"></a>Protokollieren benutzerdefinierter Ereignisse für Dev Center

Der [Nutzungsbericht](https://msdn.microsoft.com/windows/uwp/publish/usage-report) im Windows Dev Center-Dashboard informiert Sie über benutzerdefinierte Ereignisse, die Sie in Ihrer App für die universelle Windows-Plattform (UWP) definiert haben. Ein benutzerdefiniertes Ereignis ist eine beliebige Zeichenfolge, die ein Ereignis oder eine Aktivität in Ihrer App repräsentiert. Beispielsweise kann ein Spiel benutzerdefinierte Ereignisse mit den Bezeichnungen *FirstLevelPassed*, *SecondLevelPassed*usw. definieren, die protokolliert werden, wenn der Benutzer die einzelnen Levels des Spiels durchläuft.

Um ein benutzerdefiniertes Ereignis aus Ihrer App zu protokollieren, übergeben Sie die Zeichenfolge des benutzerdefinierten Ereignisses an die [Log](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicescustomeventlogger.log.aspx)-Methode des Microsoft Store Services SDK. Sie können alle Instanzen für Ihre benutzerdefinierten Ereignisse im Abschnitt **Benutzerdefinierte Ereignisse** des [Nutzungsberichts](https://msdn.microsoft.com/windows/uwp/publish/usage-report) im Dev Center-Dashboard überprüfen.

>**Hinweis:**&nbsp;&nbsp;Benutzerdefinierte Ereignisse, die Sie im Dev Center protokollieren, sind unabhängig von [Windows-Ereignissen](https://msdn.microsoft.com/library/windows/desktop/aa964766.aspx) und erscheinen nicht in der **Ereignisanzeige**.

## <a name="prerequisites"></a>Voraussetzungen

Bevor Sie benutzerdefinierte Protokollereignisse im **Nutzungsbericht** für Ihre App im Dashboard überprüfen können, muss Ihre App im Store veröffentlicht werden.

## <a name="how-to-log-custom-events"></a>Protokollieren von benutzerdefinierten Ereignissen

1. Falls noch nicht geschehen, [installieren Sie das Microsoft Store Services SDK](microsoft-store-services-sdk.md#install-the-sdk) auf Ihrem Entwicklungscomputer. Neben der API zur Protokollierung benutzerdefinierter Ereignisse bietet dieses SDK auch APIs für andere Features, wie beispielsweise das Durchführen von Experimenten in Ihren Apps mit A/B-Tests und das Einblenden von Anzeigen.
2. Öffnen Sie das Projekt in Visual Studio.
3. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf den Knoten **Verweise** für Ihr Projekt, und wählen Sie anschließend **Verweis hinzufügen** aus.
4. Erweitern Sie im **Verweis-Manager** die Option **Universelle Windows-App**, und klicken Sie auf **Erweiterungen**.
5. Klicken Sie in der Liste der SDKs auf das Kontrollkästchen neben **Microsoft Engagement Framework** und anschließend auf **OK**.
7. Fügen Sie die folgende Anweisung am Anfang jeder Codedatei hinzu, in der Sie benutzerdefinierte Ereignisse protokollieren möchten.

  > [!div class="tabbedCodeSnippets"]
  [!code-cs[EventLogger](./code/StoreSDKSamples/cs/LogEvents.cs#EngagementNamespace)]

8. Rufen Sie in jedem Abschnitt des Codes, in dem Sie ein benutzerdefiniertes Ereignis protokollieren möchten, ein [StoreServicesCustomEventLogger](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicescustomeventlogger.log.aspx)-Objekt ab, und rufen Sie dann die [Protokoll](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicescustomeventlogger.log.aspx)-Methode auf. Übergeben Sie die Zeichenfolge für das benutzerdefinierte Ereignis an die Methode.

  > [!div class="tabbedCodeSnippets"]
  [!code-cs[EventLogger](./code/StoreSDKSamples/cs/LogEvents.cs#Log)]

## <a name="related-topics"></a>Verwandte Themen

* [Nutzungsbericht](https://msdn.microsoft.com/windows/uwp/publish/usage-report)
* [Protokollierungsmethode](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicescustomeventlogger.log.aspx)
* [Microsoft Store Services SDK](https://msdn.microsoft.com/windows/uwp/monetize/microsoft-store-services-sdk)

