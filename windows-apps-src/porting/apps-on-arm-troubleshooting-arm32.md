---
title: Problembehandlung bei ARM32 UWP-Apps
author: msatranjr
description: Häufig auftretende Probleme mit ARM32-Apps bei der Ausführung auf ARM, und wie diese Probleme behoben werden können.
ms.author: misatran
ms.date: 01/18/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10 s, always connected, ARM32-Apps auf ARM, windows10 auf ARM, problembehandlung
ms.localizationpriority: medium
ms.openlocfilehash: 71d92ec26311514e0eebdfa4a1dab39e86ce72fc
ms.sourcegitcommit: 11edca90aaf7856c762e68903483079d30ad3877
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2018
ms.locfileid: "1595136"
---
# <a name="troubleshooting-arm32-uwp-apps"></a><span data-ttu-id="86231-104">Problembehandlung bei ARM32 UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="86231-104">Troubleshooting ARM32 UWP apps</span></span>
<span data-ttu-id="86231-105">Wenn Ihre ARM32 UWP-App auf ARM nicht ordnungsgemäß funktioniert, finden Sie hier einige Anleitungen, die helfen können.</span><span class="sxs-lookup"><span data-stu-id="86231-105">If your ARM32 UWP app isn't working correctly on ARM, here's some guidance that may help.</span></span> 

## <a name="common-issues"></a><span data-ttu-id="86231-106">Allgemeine Probleme</span><span class="sxs-lookup"><span data-stu-id="86231-106">Common issues</span></span>
<span data-ttu-id="86231-107">Hier sind einige allgemeine Probleme, die Sie bei der Problembehandlung bei ARM32-Apps beachten sollten.</span><span class="sxs-lookup"><span data-stu-id="86231-107">Here are some common issues to keep in mind when troubleshooting ARM32 apps.</span></span>

### <a name="using-windows-10-mobile-only-apis-on-arm-based-processors"></a><span data-ttu-id="86231-108">Verwenden von Windows 10 Nur-Mobil-APIs auf ARM-basierten Prozessoren</span><span class="sxs-lookup"><span data-stu-id="86231-108">Using Windows 10 Mobile-only APIs on ARM-based processors</span></span> 
<span data-ttu-id="86231-109">Bei ARM32-Apps treten bei der Verwendung von Nur-Mobil-APIs (z.B. **HardwareButtons**) möglicherweise Probleme auf.</span><span class="sxs-lookup"><span data-stu-id="86231-109">ARM32 apps may run into problems when using mobile-only APIs (for example, **HardwareButtons**).</span></span> <span data-ttu-id="86231-110">Um dies zu verringern, können Sie dynamisch erkennen, ob Ihre App auf Windows 10 Mobile ausgeführt wird, bevor Sie diese APIs aufrufen.</span><span class="sxs-lookup"><span data-stu-id="86231-110">To mitigate this, you can dynamically detect whether your app is running on Windows 10 Mobile before calling these APIs.</span></span> <span data-ttu-id="86231-111">Befolgen Sie die Anleitungen im Blogbeitrag [Dynamisches Erkennen von Features mithilfe von API-Verträgen](https://blogs.windows.com/buildingapps/2015/09/15/dynamically-detecting-features-with-api-contracts-10-by-10/).</span><span class="sxs-lookup"><span data-stu-id="86231-111">Follow the guidance in the blog post, [Dynamically detecting features with API contracts](https://blogs.windows.com/buildingapps/2015/09/15/dynamically-detecting-features-with-api-contracts-10-by-10/).</span></span>

### <a name="including-dependencies-not-supported-by-uwp-apps"></a><span data-ttu-id="86231-112">Einschließen von Abhängigkeiten, die von UWP-Apps nicht unterstützt werden</span><span class="sxs-lookup"><span data-stu-id="86231-112">Including dependencies not supported by UWP apps</span></span>
<span data-ttu-id="86231-113">Universelle Windows-Plattform (UWP)-Apps, die nicht ordnungsgemäß mit Visual Studio und dem UWP-SDK erstellt wurden, können Abhängigkeiten von Betriebssystemkomponenten aufweisen, die für ARM32-Apps, die auf einem ARM64-System ausgeführt werden, nicht verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="86231-113">Universal Windows Platform (UWP) apps that aren't properly built with Visual Studio and the UWP SDK may have dependencies on OS components that aren't available to ARM32 apps running on an ARM64 system.</span></span> <span data-ttu-id="86231-114">Beispiele für diese Abhängigkeiten sind:</span><span class="sxs-lookup"><span data-stu-id="86231-114">Examples of these dependencies include:</span></span>

- <span data-ttu-id="86231-115">Zu erwarten, dass Teile vom .NET Framework verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="86231-115">Expecting parts of the .NET Framework to be available.</span></span>
- <span data-ttu-id="86231-116">Auf .NET-Komponenten von Drittanbietern zu verweisen, die nicht mit UWP kompatibel sind.</span><span class="sxs-lookup"><span data-stu-id="86231-116">Referencing third-party .NET components that aren't compatible with UWP.</span></span>

<span data-ttu-id="86231-117">Diese Probleme können wie folgt gelöst werden: Entfernen der nicht verfügbaren Abhängigkeiten und Neuerstellen der App mithilfe der neuesten Versionen von Microsoft Visual Studio und UWP SDK; oder als letzte Möglichkeit, die ARM32-App aus dem Microsoft Store zu entfernen, damit die x86-Version der App (falls verfügbar) auf die PCs der Benutzer heruntergeladen wird.</span><span class="sxs-lookup"><span data-stu-id="86231-117">These issues can be resolved by: removing the unavailable dependencies and rebuilding the app by using the latest Microsoft Visual Studio and UWP SDK versions; or as a last resort, removing the ARM32 app from the Microsoft Store, so that the x86 version of the app (if available) is downloaded to users’ PCs.</span></span> 

<span data-ttu-id="86231-118">Weitere Informationen zu .NET-APIs, die für UWP-Apps verfügbar sind, finden Sie unter [.NET für UWP-Apps](https://msdn.microsoft.com/library/windows/apps/mt185501.aspx)</span><span class="sxs-lookup"><span data-stu-id="86231-118">For more info on .NET APIs available for UWP apps, see [.NET for UWP apps](https://msdn.microsoft.com/library/windows/apps/mt185501.aspx)</span></span>

### <a name="compiling-an-app-with-an-older-version-of-visual-studio-and-sdk"></a><span data-ttu-id="86231-119">Kompilieren einer App mit einer älteren Version von Visual Studio und SDK</span><span class="sxs-lookup"><span data-stu-id="86231-119">Compiling an app with an older version of Visual Studio and SDK</span></span>
<span data-ttu-id="86231-120">Wenn Probleme auftreten, stellen Sie sicher, dass Sie die neueste Version von Microsoft Visual Studio und Windows SDK zum Kompilieren Ihrer App verwenden.</span><span class="sxs-lookup"><span data-stu-id="86231-120">If you're running into issues, be sure to use the latest versions of Microsoft Visual Studio and the Windows SDK to compile your app.</span></span> <span data-ttu-id="86231-121">Apps, die mit einer früheren Version von Visual Studio und SDK kompiliert wurden, verursachen möglicherweise Probleme, die in späteren Versionen behoben wurden.</span><span class="sxs-lookup"><span data-stu-id="86231-121">Apps compiled with an earlier version of Visual Studio and the SDK may have issues that have been fixed in later versions.</span></span>

## <a name="debugging"></a><span data-ttu-id="86231-122">Debuggen</span><span class="sxs-lookup"><span data-stu-id="86231-122">Debugging</span></span>
<span data-ttu-id="86231-123">Sie können vorhandene Tools zum Entwickeln von ARM32-Apps für die ARM-Plattform verwenden.</span><span class="sxs-lookup"><span data-stu-id="86231-123">You can use existing tools for developing ARM32 apps for the ARM platform.</span></span> <span data-ttu-id="86231-124">Hier finden Sie einige hilfreiche Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="86231-124">Here are some helpful resources.</span></span>

- <span data-ttu-id="86231-125">Visual Studio15.5 Preview 1 und höher unterstützt das Ausführen von ARM32-Apps mithilfe des universellen Authentifizierungsmodus.</span><span class="sxs-lookup"><span data-stu-id="86231-125">Visual Studio 15.5 Preview 1 and later supports running ARM32 apps by using Universal Authentication mode.</span></span> <span data-ttu-id="86231-126">Dies bootet automatisch die erforderlichen Remotedebuggingtools.</span><span class="sxs-lookup"><span data-stu-id="86231-126">This automatically bootstraps the necessary remote debugging tools.</span></span>
- <span data-ttu-id="86231-127">Siehe [Debugging auf ARM64](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/debugging-arm64), um mehr über Tools und Strategien zum Debuggen auf ARM zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="86231-127">See [Debugging on ARM64](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/debugging-arm64) to learn more about tools and strategies for debugging on ARM.</span></span>