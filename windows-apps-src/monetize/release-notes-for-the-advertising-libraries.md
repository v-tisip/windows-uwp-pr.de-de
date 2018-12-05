---
ms.assetid: ca92bed1-ad9e-4947-ad91-87d12de727c0
description: Überprüfen Sie die Versionshinweise für die Microsoft Advertising-Bibliotheken.
title: Versionshinweise für die Advertising-Bibliotheken
ms.date: 08/23/2017
ms.topic: article
keywords: Windows10, UWP, Anzeigen, Werbung, Versionshinweise
ms.localizationpriority: medium
ms.openlocfilehash: 1bab822c81cdd5af1e6b00ca8d33ed7f7ea3838f
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8738122"
---
# <a name="release-notes-for-the-advertising-libraries"></a><span data-ttu-id="d9a77-104">Versionshinweise für die Advertising-Bibliotheken</span><span class="sxs-lookup"><span data-stu-id="d9a77-104">Release notes for the advertising libraries</span></span>




<span data-ttu-id="d9a77-105">Dieser Abschnittenthält Versionshinweise für die aktuelle Version der Microsoft Advertising-Bibliotheken.</span><span class="sxs-lookup"><span data-stu-id="d9a77-105">This section provides release notes for the current release of the Microsoft advertising libraries.</span></span> <span data-ttu-id="d9a77-106">Diese Bibliotheken unterstützt XAML- und JavaScript/HTML-apps für Windows 10, Windows8.1, Windows Phone 8.1 und WindowsPhone8.</span><span class="sxs-lookup"><span data-stu-id="d9a77-106">These libraries support XAML and JavaScript/HTML apps for Windows10, Windows8.1, Windows Phone 8.1 and WindowsPhone8.</span></span>

## <a name="installation"></a><span data-ttu-id="d9a77-107">Installation</span><span class="sxs-lookup"><span data-stu-id="d9a77-107">Installation</span></span>


<span data-ttu-id="d9a77-108">Diese Microsoft Advertising-Bibliotheken stehen als Teil von [Microsoft Advertising-SDK](http://aka.ms/ads-sdk-uwp) zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="d9a77-108">The Microsoft advertising libraries are available as part of the [Microsoft Advertising SDK](http://aka.ms/ads-sdk-uwp).</span></span> <span data-ttu-id="d9a77-109">Weitere Informationen zur SDK-Installation finden Sie unter [Installieren von Microsoft Advertising-SDK](install-the-microsoft-advertising-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="d9a77-109">For more information about installing the SDK, see [Install the Microsoft Advertising SDK](install-the-microsoft-advertising-libraries.md).</span></span>

## <a name="uninstall-previous-versions"></a><span data-ttu-id="d9a77-110">Deinstallieren früherer Versionen</span><span class="sxs-lookup"><span data-stu-id="d9a77-110">Uninstall previous versions</span></span>

<span data-ttu-id="d9a77-111">Vor der Installation der neuesten Microsoft Advertising-SDK wird dringend empfohlen, alle vorherigen Instanzen von SDK zu deinstallieren.</span><span class="sxs-lookup"><span data-stu-id="d9a77-111">Before you install the latest Microsoft Advertising SDK, it is highly recommended that you uninstall all prior instances of the SDK.</span></span> <span data-ttu-id="d9a77-112">Weitere Informationen finden Sie unter [Installieren von Microsoft Advertising-SDK](install-the-microsoft-advertising-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="d9a77-112">For more information, see [Install the Microsoft Advertising SDK](install-the-microsoft-advertising-libraries.md).</span></span>

## <a name="target-architecture-specific-build-outputs"></a><span data-ttu-id="d9a77-113">Zielarchitekturspezifische Buildausgabe</span><span class="sxs-lookup"><span data-stu-id="d9a77-113">Target architecture-specific build outputs</span></span>

<span data-ttu-id="d9a77-114">Wenn Sie die Microsoft Advertising-Bibliotheken verwenden, können Sie in Ihrem Projekt nicht das Ziel **Any CPU** angeben.</span><span class="sxs-lookup"><span data-stu-id="d9a77-114">When using the Microsoft advertising libraries, you cannot target **Any CPU** in your project.</span></span> <span data-ttu-id="d9a77-115">Sollte in Ihrem Projekt die Zielplattform **Any CPU** definiert sein, wird in Ihrem Projekt eine Warnung ausgegeben, sobald Sie einen Verweis auf die Microsoft Advertising-Bibliotheken hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="d9a77-115">If your project targets the **Any CPU** platform, you may see a warning in your project after you add a reference to the Microsoft advertising libraries.</span></span> <span data-ttu-id="d9a77-116">Um diese Warnung zu entfernen, müssen Sie eine architekturspezifische Buildausgabe verwenden (beispielsweise **x86**) und das Projekt entsprechend aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="d9a77-116">To remove this warning, update your project to use an architecture-specific build output (for example, **x86**).</span></span> <span data-ttu-id="d9a77-117">Weitere Informationen finden Sie unter [Bekannte Probleme](known-issues-for-the-advertising-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="d9a77-117">For more information, see [Known issues](known-issues-for-the-advertising-libraries.md).</span></span>

## <a name="c-support"></a><span data-ttu-id="d9a77-118">C++-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="d9a77-118">C++ Support</span></span>

<span data-ttu-id="d9a77-119">Die Microsoft Advertising-Bibliotheken (in den die Klassen **AdControl** und **InterstitialAd** enthalten sind) unterstützen in C++ geschriebene Apps sowie DirectX mit Windows-Runtime-Interoperabilität (*interop*).</span><span class="sxs-lookup"><span data-stu-id="d9a77-119">The Microsoft advertising libraries (which include the **AdControl** and **InterstitialAd** classes) support apps written in C++ and DirectX using Windows Runtime Interoperability (*interop*).</span></span> <span data-ttu-id="d9a77-120">Weitere Informationen und Beispiele zum Programmieren mit XAML und C++ finden Sie unter [Typsystem](https://docs.microsoft.com/cpp/cppcx/type-system-c-cx).</span><span class="sxs-lookup"><span data-stu-id="d9a77-120">For more information and examples about programming using XAML and C++, see [Type System](https://docs.microsoft.com/cpp/cppcx/type-system-c-cx).</span></span>

## <a name="no-toolbox-control"></a><span data-ttu-id="d9a77-121">Kein Toolbox-Steuerelement</span><span class="sxs-lookup"><span data-stu-id="d9a77-121">No toolbox control</span></span>

<span data-ttu-id="d9a77-122">In der aktuellen Version der Microsoft Advertising-Bibliotheken im [Microsoft Advertising-SDK](http://aka.ms/ads-sdk-uwp) gibt es kein Toolbox-Steuerelement zum Ziehen eines **AdControl** oder **InterstitialAd** in die Entwurfsoberfläche Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="d9a77-122">In the current release of the Microsoft advertising libraries in the [Microsoft Advertising SDK](http://aka.ms/ads-sdk-uwp), there is no toolbox control for dragging an **AdControl** or **InterstitialAd** to a design surface in your app.</span></span> <span data-ttu-id="d9a77-123">Informationen zum Hinzufügen dieser Steuerelemente in Ihrem Markup und Code finden Sie in der [Exemplarische Vorgehensweisen für Entwickler](developer-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="d9a77-123">For instructions about adding these controls in your markup and code, see the [developer walkthroughs](developer-walkthroughs.md).</span></span>

## <a name="latitude-and-longitude-properties-no-longer-available"></a><span data-ttu-id="d9a77-124">Eigenschaften Latitude und Longitude nicht mehr verfügbar</span><span class="sxs-lookup"><span data-stu-id="d9a77-124">Latitude and longitude properties no longer available</span></span>

<span data-ttu-id="d9a77-125">Die **AdControl**-Klasse verfügt nicht mehr über die Eigenschaften **Latitude** und **Longitude** für UWP-Apps.</span><span class="sxs-lookup"><span data-stu-id="d9a77-125">The **AdControl** class no longer has **Latitude** and **Longitude** properties for UWP apps.</span></span> <span data-ttu-id="d9a77-126">Stattdessen erkennt der Code im Anzeigensteuerelement diese Werte und sendet sie für die App an die Anzeigenserver.</span><span class="sxs-lookup"><span data-stu-id="d9a77-126">Instead, code built into the ad control will detect and send these values to the ad servers on the app’s behalf.</span></span>


 

 
