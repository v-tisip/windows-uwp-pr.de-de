---
author: drewbat
ms.assetid: 
title: Entwickeln von UWP-Apps mit APIs von Vorabversionen
description: Grundlegendes zu den Vorteilen und Problemen bei Verwendung der APIs von Vorabversionen, die in den UWP-SDK-Vorschauversionen enthalten sind.
ms.openlocfilehash: ede7e8d5e9cce39850edbdb70a715d76c78f0c01
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="developing-uwp-apps-with-pre-release-apis"></a>Entwickeln von UWP-Apps mit APIs von Vorabversionen

Microsoft veröffentlicht Vorabversionen des UWP-SDKs (Universelle Windows-Plattform), um Entwicklern die Verwendung neuer Plattformfeatures vor deren Finalisierung zu ermöglichen. Dies bietet Ihnen einen Vorsprung bei der Einbindung von Features in Ihre App und hilft Ihnen dabei, Ihre App früher nach der Veröffentlichung der offiziellen RTM-Version des SDK zu veröffentlichen. Das Verwenden der APIs von Vorabversionen ermöglicht Ihnen auch, Feedback an Microsoft zu senden, um die Richtung der Plattform in zukünftigen Versionen zu beeinflussen.

## <a name="important-limitations-on-the-use-of-pre-release-apis"></a>Wichtige Einschränkungen bei der Verwendung der APIs von Vorabversionen
Beachten Sie vor der Verwendung der API einer Vorabversion in Ihrer App die folgenden wichtigen Auswirkungen davon: 
* Apps, die APIs von Vorabversion verwenden, können erst an den Windows Store übermittelt werden, wenn die APIs in einer RTM-Version offiziell veröffentlicht wurden. Es wird dringend empfohlen, dass Sie den Entwicklungscode von Vorabversionen vom Code für Ihre derzeit veröffentlichten Apps getrennt halten. 
* Apps, die Sie mit einer SDK-Vorschauversion entwickeln, können nicht an den Store übermittelt werden, auch wenn Sie keine APIs von Vorabversionen verwenden. Installieren Sie die Vorschautools auf einem Computer oder virtuellen Computer, der vom Produktionscomputer, den Sie für Ihre primäre Entwicklung verwenden, getrennt ist. 
* APIs von Vorabversion ändern sich vor der RTM-Veröffentlichung wahrscheinlich Wenn APIs in einem Vorschau-SDK enthalten sind, ist es wahrscheinlich, dass das Feature oder Szenario, das sie ermöglichen, im endgültigen SDK enthalten sein wird. Aber die Namen, Signaturen und das Verhalten bestimmter APIs ändern sich möglicherweise vor der endgültigen Version, und es ist möglich, dass die API vollständig entfernt wird. 

## <a name="how-to-identify-a-prerelease-api"></a>So identifizieren Sie eine API einer Vorabversion 
In der API-Referenzdokumentation für UWP sind APIs von Vorabversionen mit dem folgenden Text beschriftet: 

Dieser Artikel beschreibt die API oder das Feature einer Vorabversion, die sich vor der kommerziellen Veröffentlichung grundlegend ändern kann. Sie können dieses Feature derzeit für die Entwicklung und zum Testen verwenden, aber Apps, die es verwenden, können erst nach der kommerziellen Veröffentlichung des Features an den Windows Store übermittelt werden. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen. Weitere Informationen zum Entwickeln mit APIs von Vorabversionen finden Sie unter Entwickeln von UWP-Apps mit APIs von Vorabversionen. 

## <a name="get-the-latest-sdk-insider-preview"></a>Aktuelle SDK Insider Preview-Version abrufen 
1. [Melden Sie sich für das Windows-Insider-Programm](https://insider.windows.com/) an, um Zugriff auf Vorabversionen des SDK zu erhalten. 
3. Überprüfen Sie vor der Installation der Entwicklervorschautools die [Versionshinweise für das aktuelle SDK und den Mobile-Emulator](http://go.microsoft.com/fwlink/?LinkId=829180).
4. Installieren Sie das [SDK Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewSDK).
5. Sehen Sie sich das [Windows Insider Preview-Community-Forum](http://go.microsoft.com/fwlink/p/?LinkId=507620) an.
