---
author: mcleanbyron
Description: "Sie können benutzerdefinierte Ereignisse von Ihrer UWP-App aus protokollieren und sie im Nutzungsbericht im Windows Dev Center-Dashboard prüfen."
title: "Protokollieren benutzerdefinierter Ereignisse für Dev Center"
translationtype: Human Translation
ms.sourcegitcommit: ffda100344b1264c18b93f096d8061570dd8edee
ms.openlocfilehash: e0012d586d9b79db77bdeded6f0e1d2ce848bbea

---

# <a name="log-custom-events-for-dev-center"></a>Protokollieren benutzerdefinierter Ereignisse für Dev Center

Der [Nutzungsbericht](https://msdn.microsoft.com/windows/uwp/publish/usage-report) im Windows Dev Center-Dashboard informiert Sie über benutzerdefinierte Ereignisse, die Sie in Ihrer App für die universelle Windows-Plattform (UWP) definiert haben. Ein benutzerdefiniertes Ereignis ist eine beliebige Zeichenfolge, die ein Ereignis oder eine Aktivität in Ihrer App repräsentiert. Beispielsweise kann ein Spiel benutzerdefinierte Ereignisse mit den Bezeichnungen *FirstLevelPassed*, *SecondLevelPassed*usw. definieren, die protokolliert werden, wenn der Benutzer die einzelnen Levels des Spiels durchläuft.

Um ein benutzerdefiniertes Ereignis aus Ihrer App zu protokollieren, übergeben Sie die Zeichenfolge des benutzerdefinierten Ereignisses an die [Log](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicescustomeventlogger.log.aspx)-Methode des Microsoft Store Services SDK. Sie können alle Instanzen für Ihre benutzerdefinierten Ereignisse im Abschnitt **Benutzerdefinierte Ereignisse** des [Nutzungsberichts](https://msdn.microsoft.com/windows/uwp/publish/usage-report) im Dev Center-Dashboard überprüfen.

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



<!--HONumber=Dec16_HO1-->


