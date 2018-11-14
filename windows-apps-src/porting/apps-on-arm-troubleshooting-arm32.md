---
title: Problembehandlung bei ARM32 UWP-Apps
author: msatranjr
description: Häufig auftretende Probleme mit ARM32-Apps bei der Ausführung auf ARM, und wie diese Probleme behoben werden können.
ms.author: misatran
ms.date: 05/09/2018
ms.topic: article
keywords: windows10 s, always connected, ARM32-Apps auf ARM, windows10 auf ARM, problembehandlung
ms.localizationpriority: medium
ms.openlocfilehash: 4eaeccb8b4003bb835ee4700d1df57cd8cefcda0
ms.sourcegitcommit: bdc40b08cbcd46fc379feeda3c63204290e055af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/08/2018
ms.locfileid: "6155839"
---
# <a name="troubleshooting-arm32-uwp-apps"></a>Problembehandlung bei ARM32 UWP-Apps
>[!IMPORTANT]
> Das ARM64-SDK ist jetzt als Teil von Visual Studio15.8 Preview 1 verfügbar. Wir empfehlen, die App für ARM64 erneut zu kompilieren, damit sie mit der höchstmöglichen systemeigenen Geschwindigkeit ausgeführt wird. Weitere Informationen finden Sie im Blogbeitrag [Early preview of Visual Studio support for Windows 10 on ARM development](https://blogs.windows.com/buildingapps/2018/05/08/visual-studio-support-for-windows-10-on-arm-development/).

Wenn Ihre ARM32 UWP-App auf ARM nicht ordnungsgemäß funktioniert, finden Sie hier einige Anleitungen, die helfen können. 

## <a name="common-issues"></a>Allgemeine Probleme
Hier sind einige allgemeine Probleme, die Sie bei der Problembehandlung bei ARM32-Apps beachten sollten.

### <a name="using-windows-10-mobile-only-apis-on-arm-based-processors"></a>Verwenden von Windows 10 Nur-Mobil-APIs auf ARM-basierten Prozessoren 
Bei ARM32-Apps treten bei der Verwendung von Nur-Mobil-APIs (z.B. **HardwareButtons**) möglicherweise Probleme auf. Um dies zu verringern, können Sie dynamisch erkennen, ob Ihre App auf Windows 10 Mobile ausgeführt wird, bevor Sie diese APIs aufrufen. Befolgen Sie die Anleitungen im Blogbeitrag [Dynamisches Erkennen von Features mithilfe von API-Verträgen](https://blogs.windows.com/buildingapps/2015/09/15/dynamically-detecting-features-with-api-contracts-10-by-10/).

### <a name="including-dependencies-not-supported-by-uwp-apps"></a>Einschließen von Abhängigkeiten, die von UWP-Apps nicht unterstützt werden
Universelle Windows-Plattform (UWP)-Apps, die nicht ordnungsgemäß mit Visual Studio und dem UWP-SDK erstellt wurden, können Abhängigkeiten von Betriebssystemkomponenten aufweisen, die für ARM32-Apps, die auf einem ARM64-System ausgeführt werden, nicht verfügbar sind. Beispiele für diese Abhängigkeiten sind:

- Zu erwarten, dass Teile vom .NET Framework verfügbar sind.
- Auf .NET-Komponenten von Drittanbietern zu verweisen, die nicht mit UWP kompatibel sind.

Diese Probleme können wie folgt gelöst werden: Entfernen der nicht verfügbaren Abhängigkeiten und Neuerstellen der App mithilfe der neuesten Versionen von Microsoft Visual Studio und UWP SDK; oder als letzte Möglichkeit, die ARM32-App aus dem Microsoft Store zu entfernen, damit die x86-Version der App (falls verfügbar) auf die PCs der Benutzer heruntergeladen wird. 

Weitere Informationen zu .NET-APIs, die für UWP-Apps verfügbar sind, finden Sie unter [.NET für UWP-Apps](https://msdn.microsoft.com/library/windows/apps/mt185501.aspx)

### <a name="compiling-an-app-with-an-older-version-of-visual-studio-and-sdk"></a>Kompilieren einer App mit einer älteren Version von Visual Studio und SDK
Wenn Probleme auftreten, stellen Sie sicher, dass Sie die neueste Version von Microsoft Visual Studio und Windows SDK zum Kompilieren Ihrer App verwenden. Apps, die mit einer früheren Version von Visual Studio und SDK kompiliert wurden, verursachen möglicherweise Probleme, die in späteren Versionen behoben wurden.

## <a name="debugging"></a>Debuggen
Sie können vorhandene Tools zum Entwickeln von ARM32-Apps für die ARM-Plattform verwenden. Hier finden Sie einige hilfreiche Ressourcen.

- Visual Studio15.5 Preview 1 und höher unterstützt das Ausführen von ARM32-Apps mithilfe des universellen Authentifizierungsmodus. Dies bootet automatisch die erforderlichen Remotedebuggingtools.
- Siehe [Debugging auf ARM64](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/debugging-arm64), um mehr über Tools und Strategien zum Debuggen auf ARM zu erfahren.