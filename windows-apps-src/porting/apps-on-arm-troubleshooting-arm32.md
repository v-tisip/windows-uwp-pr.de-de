---
title: Problembehandlung bei ARM32 UWP-Apps
description: Häufig auftretende Probleme mit ARM32-Apps bei der Ausführung auf ARM, und wie diese Probleme behoben werden können.
ms.date: 01/03/2019
ms.topic: article
keywords: windows10 s, always connected, ARM32-Apps auf ARM, windows10 auf ARM, problembehandlung
ms.localizationpriority: medium
ms.openlocfilehash: 75019df4b7d70dad20aea1a256abac05c93a481d
ms.sourcegitcommit: 62bc4936ca8ddf1fea03d43a4ede5d14a5755165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "8991636"
---
# <a name="troubleshooting-arm-uwp-apps"></a>Problembehandlung für ARM-UWP-apps

Wenn Ihre ARM32 oder ARM64-UWP-app auf ARM nicht korrekt funktioniert, wird hier einige Anleitungen, die hilfreich sein können.

>[!NOTE]
> Um Ihrer UWP-Anwendung für die ARM64 nativ Zielplattform zu erstellen, müssen Sie Visual Studio 2017 Version 15.9 oder höher verfügen. Weitere Informationen finden Sie in [diesem Blogbeitrag](https://blogs.windows.com/buildingapps/2018/11/15/official-support-for-windows-10-on-arm-development).

## <a name="common-issues"></a>Allgemeine Probleme
Hier sind einige allgemeine Probleme bei der Problembehandlung für ARM32 und ARM64-apps Bedenken.

### <a name="using-windows-10-mobile-only-apis-on-arm-based-processors"></a>Verwenden von Windows 10 Nur-Mobil-APIs auf ARM-basierten Prozessoren
ARM-apps möglicherweise Probleme stoßen, bei Verwendung von nur-Mobil APIs (z. B. **HardwareButtons**). Um dies zu verringern, können Sie dynamisch erkennen, ob Ihre App auf Windows 10 Mobile ausgeführt wird, bevor Sie diese APIs aufrufen. Befolgen Sie die Anleitungen im Blogbeitrag [Dynamisches Erkennen von Features mithilfe von API-Verträgen](https://blogs.windows.com/buildingapps/2015/09/15/dynamically-detecting-features-with-api-contracts-10-by-10/).

### <a name="including-dependencies-not-supported-by-uwp-apps"></a>Einschließen von Abhängigkeiten, die von UWP-Apps nicht unterstützt werden
Universelle Windows-Plattform (UWP)-apps, die ordnungsgemäß mit Visual Studio und UWP-SDK erstellt wurden können Abhängigkeiten von Betriebssystemkomponenten aufweisen, die nicht für ARM-apps, die auf einem ARM64-System zur Verfügung stehen. Beispiele für diese Abhängigkeiten sind:

- Zu erwarten, dass Teile vom .NET Framework verfügbar sind.
- Auf .NET-Komponenten von Drittanbietern zu verweisen, die nicht mit UWP kompatibel sind.

Diese Probleme können durch aufgelöst werden: Entfernen der nicht verfügbaren Abhängigkeiten und Neuerstellen der app mithilfe der neuesten Versionen von Microsoft Visual Studio und UWP SDK; oder als letzte Möglichkeit, die ARM-app aus dem Microsoft Store zu entfernen, damit die X86 Version der app (falls verfügbar) auf die PCs der Benutzer heruntergeladen wird.

Weitere Informationen zu .NET-APIs, die für UWP-Apps verfügbar sind, finden Sie unter [.NET für UWP-Apps](https://msdn.microsoft.com/library/windows/apps/mt185501.aspx)

### <a name="compiling-an-app-with-an-older-version-of-visual-studio-and-sdk"></a>Kompilieren einer App mit einer älteren Version von Visual Studio und SDK
Wenn Probleme auftreten, stellen Sie sicher, dass Sie die neueste Version von Microsoft Visual Studio und Windows SDK zum Kompilieren Ihrer App verwenden. Apps, die mit einer früheren Version von Visual Studio und SDK kompiliert wurden, verursachen möglicherweise Probleme, die in späteren Versionen behoben wurden.

## <a name="debugging"></a>Debuggen
Sie können vorhandene Tools zum Entwickeln von apps für die ARM-Plattform verwenden. Hier finden Sie einige hilfreiche Ressourcen.

- Visual Studio15.5 Preview 1 und höher unterstützt das Ausführen von ARM32-Apps mithilfe des universellen Authentifizierungsmodus. Dies bootet automatisch die erforderlichen Remotedebuggingtools.
- Siehe [Debugging auf ARM64](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/debugging-arm64), um mehr über Tools und Strategien zum Debuggen auf ARM zu erfahren.
