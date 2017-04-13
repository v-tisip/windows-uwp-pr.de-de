---
author: mcleanbyron
Description: "Sie können benutzerdefinierte Ereignisse von Ihrer UWP-App aus protokollieren und sie im Nutzungsbericht im Windows Dev Center-Dashboard prüfen."
title: "Protokollieren benutzerdefinierter Ereignisse für Dev Center"
ms.author: mcleans
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Microsoft Store-Services-SDK, Ereignisse protokollieren
ms.assetid: 4aa591e0-c22a-4c90-b316-0b5d0410af19
ms.openlocfilehash: b2fad3ea78a2007b2519e4b0b27276f9f003af2c
ms.sourcegitcommit: d053f28b127e39bf2aee616aa52bb5612194dc53
translationtype: HT
---
# <a name="log-custom-events-for-dev-center"></a>Protokollieren benutzerdefinierter Ereignisse für Dev Center

Der [Nutzungsbericht](https://msdn.microsoft.com/windows/uwp/publish/usage-report) im Windows Dev Center-Dashboard informiert Sie über benutzerdefinierte Ereignisse, die Sie in Ihrer App für die universelle Windows-Plattform (UWP) definiert haben. Ein benutzerdefiniertes Ereignis ist eine beliebige Zeichenfolge, die ein Ereignis oder eine Aktivität in Ihrer App repräsentiert. Beispielsweise kann ein Spiel benutzerdefinierte Ereignisse mit den Bezeichnungen *FirstLevelPassed*, *SecondLevelPassed*usw. definieren, die protokolliert werden, wenn der Benutzer die einzelnen Levels des Spiels durchläuft.

Um ein benutzerdefiniertes Ereignis aus Ihrer App zu protokollieren, übergeben Sie die Zeichenfolge des benutzerdefinierten Ereignisses an die [Log](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicescustomeventlogger.log.aspx)-Methode des Microsoft Store Services SDK. Sie können alle Instanzen für Ihre benutzerdefinierten Ereignisse im Abschnitt **Benutzerdefinierte Ereignisse** des [Nutzungsberichts](https://msdn.microsoft.com/windows/uwp/publish/usage-report) im Dev Center-Dashboard überprüfen.

> [!NOTE]
> Benutzerdefinierte Ereignisse, die Sie im Dev Center protokollieren, sind unabhängig von [Windows-Ereignissen](https://msdn.microsoft.com/library/windows/desktop/aa964766.aspx) und erscheinen nicht in der **Ereignisanzeige**.

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

8. Rufen Sie in jedem Abschnittdes Codes, in dem Sie ein benutzerdefiniertes Ereignis protokollieren möchten, ein [StoreServicesCustomEventLogger](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicescustomeventlogger.log.aspx)-Objekt ab, und rufen Sie dann die [Protokoll](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicescustomeventlogger.log.aspx)-Methode auf. Übergeben Sie die Zeichenfolge für das benutzerdefinierte Ereignis an die Methode.

  > [!div class="tabbedCodeSnippets"]
  [!code-cs[EventLogger](./code/StoreSDKSamples/cs/LogEvents.cs#Log)]

## <a name="related-topics"></a>Verwandte Themen

* [Nutzungsbericht](https://msdn.microsoft.com/windows/uwp/publish/usage-report)
* [Protokollierungsmethode](https://msdn.microsoft.com/library/windows/apps/microsoft.services.store.engagement.storeservicescustomeventlogger.log.aspx)
* [Microsoft Store Services SDK](https://msdn.microsoft.com/windows/uwp/monetize/microsoft-store-services-sdk)
