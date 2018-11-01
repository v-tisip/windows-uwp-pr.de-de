---
author: TylerMSFT
title: Experimentelle APIs
description: Grundlegendes zu experimentellen APIs
ms.author: twhitney
ms.date: 11/13/2017
ms.topic: article
keywords: Windows10, UWP, experimentell,-API
ms.localizationpriority: medium
ms.openlocfilehash: fe5fa437c5a1e564be07b7277de0f190d6eab862
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "5884779"
---
# <a name="experimental-apis"></a><span data-ttu-id="a358b-104">Experimentelle APIs</span><span class="sxs-lookup"><span data-stu-id="a358b-104">Experimental APIs</span></span>

<span data-ttu-id="a358b-105">Experimentelle APIs befinden sich in der Anfangsphase des Designs und ändern sich wahrscheinlich, wenn die Besitzer Feedback einarbeiten und Unterstützung für zusätzliche Szenarien hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="a358b-105">Experimental APIs are in the early stages of design and are likely to change as the owners incorporate feedback and add support for additional scenarios.</span></span>

<span data-ttu-id="a358b-106">Für diese APIs werden externe Test-Flights mit [Windows-Insider-SDKs](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewSDK) durchgeführt, damit Entwickler sie ausprobieren und Feedback bereitstellen können, bevor sie Teil der offiziellen Plattform werden.</span><span class="sxs-lookup"><span data-stu-id="a358b-106">These APIs are flighted externally using [Windows Insider SDKs](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewSDK) so that developers can try them out and provide feedback before they become part of the official platform.</span></span> <span data-ttu-id="a358b-107">Während der Test-Flights gibt es keine Zusage bezügliche Stabilität oder Verpflichtung.</span><span class="sxs-lookup"><span data-stu-id="a358b-107">While they are flighted, there is no promise of stability or commitment.</span></span>

## <a name="consuming-experimental-apis"></a><span data-ttu-id="a358b-108">Nutzung experimenteller APIs</span><span class="sxs-lookup"><span data-stu-id="a358b-108">Consuming experimental APIs</span></span>
<span data-ttu-id="a358b-109">IntelliSense informiert Sie, ob eine API experimentell ist.</span><span class="sxs-lookup"><span data-stu-id="a358b-109">Intellisense will let you know if an API is experimental.</span></span> <span data-ttu-id="a358b-110">Außerdem erhalten Sie eine Compilerwarnung, wenn Sie eine experimentelle API verwenden, z. B. „... ist nur zu Testzwecken vorgesehen und kann in zukünftigen Updates geändert oder entfernt werden“.</span><span class="sxs-lookup"><span data-stu-id="a358b-110">You will also get a compiler warning when you use an experimental API such as "... is for evaluation purposes only and is subject to change or removal in future updates".</span></span>

<span data-ttu-id="a358b-111">Diese Warnungen schützen Sie vor der Erstellung von Abhängigkeiten von experimentellen APIs in Produktionsprojekten.</span><span class="sxs-lookup"><span data-stu-id="a358b-111">These warnings help protect you from creating dependencies on experimental APIs in production projects.</span></span> <span data-ttu-id="a358b-112">Bei experimentellen Projekten können Sie diese Warnungen ignorieren oder deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="a358b-112">For experimental projects, you can ignore or disable these warnings.</span></span>

<span data-ttu-id="a358b-113">Standardmäßig sind diese APIs zur Laufzeit deaktiviert und ein Aufruf der APIs führt zu einer Laufzeitausnahme.</span><span class="sxs-lookup"><span data-stu-id="a358b-113">By default, these APIs are disabled at runtime and calling them will result in a runtime exception.</span></span> <span data-ttu-id="a358b-114">Das ist eine weitere Vorsichtsmaßnahme, um unbeabsichtigte Abhängigkeiten und eine umfangreiche Verteilung von Apps zu verhindern, die experimentelle APIs nutzen.</span><span class="sxs-lookup"><span data-stu-id="a358b-114">This is another safeguard to help prevent inadvertent dependencies and broad distribution of apps that consume experimental APIs.</span></span>

<span data-ttu-id="a358b-115">Um diese APIs für experimentelle Zwecke zu aktivieren, verwenden Sie das Plug-In für [Windows-Geräteportal (WDP)](https://docs.microsoft.com/en-us/windows/uwp/debug-test-perf/device-portal)-Features, um das Feature zu aktivieren, das der API entspricht, die Sie aufrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="a358b-115">To enable these APIs for experimentation, use the [Windows Device Portal (WDP)](https://docs.microsoft.com/en-us/windows/uwp/debug-test-perf/device-portal) Features plug-in on the target device to enable the feature corresponding to the API you want to call.</span></span>

<span data-ttu-id="a358b-116">Die Dokumentation für eine bestimmte experimentelle API liegt im Ermessen des Teams, die diese besitzt.</span><span class="sxs-lookup"><span data-stu-id="a358b-116">Documentation for a particular experimental API is at the discretion of the team that owns it.</span></span>

## <a name="providing-feedback"></a><span data-ttu-id="a358b-117">Bereitstellen von Feedback</span><span class="sxs-lookup"><span data-stu-id="a358b-117">Providing feedback</span></span>

<span data-ttu-id="a358b-118">Wenn Sie eine experimentelle API ausprobiert haben und Feedback dazu abgeben möchten, verwenden Sie die Kategorie **Entwicklerplattform** im [Windows-Feedback-Hub](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app).</span><span class="sxs-lookup"><span data-stu-id="a358b-118">If you've tried an experimental API and would like to provide feedback, use the **Developer Platform** category in the [Windows Feedback Hub](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app).</span></span>