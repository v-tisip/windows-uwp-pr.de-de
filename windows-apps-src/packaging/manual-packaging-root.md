---
ms.assetid: ee51eae3-ed55-419e-ad74-6adf1e1fb8b9
title: Manuelles Verpacken von Apps
description: Dieser Abschnitt enthält Artikel oder Links zum manuellen Verpacken von UWP (Universelle Windows-Plattform)-Apps.
ms.date: 04/30/2018
ms.topic: article
keywords: Windows10, UWP, Verpacken
ms.localizationpriority: medium
ms.openlocfilehash: 5c429c3c88b0ae23cb518a59cab2e5a3c4f380a2
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7718754"
---
# <a name="manual-app-packaging"></a><span data-ttu-id="ceb71-104">Manuelles Verpacken von Apps</span><span class="sxs-lookup"><span data-stu-id="ceb71-104">Manual app packaging</span></span>

<span data-ttu-id="ceb71-105">Wenn Sie ein App-Paket erstellen und signieren möchten, für die Entwicklung der App aber nicht Visual Studio verwendet haben, müssen Sie die Tools für die manuelle App-Verpackung verwenden.</span><span class="sxs-lookup"><span data-stu-id="ceb71-105">If you want to create and sign an app package, but you didn't use Visual Studio to develop your app, you'll need to use the manual app packaging tools.</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="ceb71-106">Wenn Sie Visual Studio zum Entwickeln der App verwendet haben, wird empfohlen, dass Sie den Visual Studio-Assistenten zum Erstellen und Signieren des App-Pakets verwenden.</span><span class="sxs-lookup"><span data-stu-id="ceb71-106">If you used Visual Studio to develop your app, it's recommended that you use the Visual Studio wizard to create and sign your app package.</span></span> <span data-ttu-id="ceb71-107">Weitere Informationen finden Sie unter [Verpacken einer UWP-App mit Visual Studio](https://msdn.microsoft.com/windows/uwp/packaging/packaging-uwp-apps).</span><span class="sxs-lookup"><span data-stu-id="ceb71-107">For more information, see [Package a UWP app with Visual Studio](https://msdn.microsoft.com/windows/uwp/packaging/packaging-uwp-apps).</span></span>

## <a name="purpose"></a><span data-ttu-id="ceb71-108">Zweck</span><span class="sxs-lookup"><span data-stu-id="ceb71-108">Purpose</span></span>

<span data-ttu-id="ceb71-109">Dieser Abschnitt enthält Artikel oder Links zum manuellen Verpacken von UWP (Universelle Windows-Plattform)-Apps.</span><span class="sxs-lookup"><span data-stu-id="ceb71-109">This section contains or links to articles about manually packaging Universal Windows Platform (UWP) apps.</span></span>

| <span data-ttu-id="ceb71-110">Thema</span><span class="sxs-lookup"><span data-stu-id="ceb71-110">Topic</span></span> | <span data-ttu-id="ceb71-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ceb71-111">Description</span></span> |
|-------|-------------|
| [<span data-ttu-id="ceb71-112">Erstellen eines App-Pakets mit dem Tool „MakeAppx.exe“</span><span class="sxs-lookup"><span data-stu-id="ceb71-112">Create an app package with the MakeAppx.exe tool</span></span>](create-app-package-with-makeappx-tool.md) | <span data-ttu-id="ceb71-113">MakeAppx.exe erstellt, verschlüsselt, entschlüsselt und extrahiert Dateien aus App-Paketen und -Bündeln.</span><span class="sxs-lookup"><span data-stu-id="ceb71-113">MakeAppx.exe creates, encrypts, decrypts, and extracts files from app packages and bundles.</span></span> |
| [<span data-ttu-id="ceb71-114">Erstellen von Zertifikaten für die Paketsignatur</span><span class="sxs-lookup"><span data-stu-id="ceb71-114">Create a certificate for package signing</span></span>](create-certificate-package-signing.md) | <span data-ttu-id="ceb71-115">Erstellen und Exportieren eines Zertifikats für die App-Paketsignatur mit PowerShell-Tools.</span><span class="sxs-lookup"><span data-stu-id="ceb71-115">Create and export a certificate for app package signing with PowerShell tools.</span></span> |
| [<span data-ttu-id="ceb71-116">Signieren eines App-Pakets mit SignTool</span><span class="sxs-lookup"><span data-stu-id="ceb71-116">Sign an app package using SignTool</span></span>](sign-app-package-using-signtool.md) | <span data-ttu-id="ceb71-117">Verwenden von SignTool zur manuellen Signatur eines App-Pakets mit einem Zertifikat.</span><span class="sxs-lookup"><span data-stu-id="ceb71-117">Use SignTool to manually sign an app package with a certificate.</span></span> |

### <a name="advanced-topics"></a><span data-ttu-id="ceb71-118">Fortgeschrittene Themen</span><span class="sxs-lookup"><span data-stu-id="ceb71-118">Advanced topics</span></span>

<span data-ttu-id="ceb71-119">Dieser Abschnittenthält fortgeschrittene Themen zum Aufschlüsseln einer großen und/oder komplexen App für eine effizientere Verpackung und Installation.</span><span class="sxs-lookup"><span data-stu-id="ceb71-119">This section contains more advanced topics for componentizing a large and/or complex app for more efficient packaging and installation.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="ceb71-120">Wenn Sie Ihre App an den Store übermitteln möchten, müssen Sie sich an den [Windows-Support für Entwickler](https://developer.microsoft.com/windows/support) wenden und eine Genehmigung für die Verwendung der erweiterten Funktionen in diesem Abschnitt erhalten.</span><span class="sxs-lookup"><span data-stu-id="ceb71-120">If you intend to submit your app to the Store, you need to contact [Windows developer support](https://developer.microsoft.com/windows/support) and get approval to use any of the advanced features in this section.</span></span>


| <span data-ttu-id="ceb71-121">Thema</span><span class="sxs-lookup"><span data-stu-id="ceb71-121">Topic</span></span> | <span data-ttu-id="ceb71-122">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ceb71-122">Description</span></span> |
|-------|-------------|
| [<span data-ttu-id="ceb71-123">Einführung zu Bestandspaketen</span><span class="sxs-lookup"><span data-stu-id="ceb71-123">Introduction to asset packages</span></span>](asset-packages.md) | <span data-ttu-id="ceb71-124">Asset-Pakete sind ein Pakettyp, der als zentraler Speicherort für die gemeinsamen Dateien einer Anwendung fungiert. Dadurch wird die Notwendigkeit doppelter Dateien in allen Architekturpaketen effektiv eliminiert.</span><span class="sxs-lookup"><span data-stu-id="ceb71-124">Asset packages are a type of package that act as a centralized location for an application’s common files – effectively eliminating the necessity for duplicated files throughout its architecture packages.</span></span> |
| [<span data-ttu-id="ceb71-125">Entwickeln mit Bestandspaketen und Paketfaltung</span><span class="sxs-lookup"><span data-stu-id="ceb71-125">Developing with asset packages and package folding</span></span>](package-folding.md) | <span data-ttu-id="ceb71-126">Hier erfahren Sie, wie Sie Ihre App mit Bestandspaketen und Paketfaltung effizient organisieren.</span><span class="sxs-lookup"><span data-stu-id="ceb71-126">Learn how to efficiently organize your app with asset packages and package folding.</span></span> |
| [<span data-ttu-id="ceb71-127">Flat-Bundle App-Pakete</span><span class="sxs-lookup"><span data-stu-id="ceb71-127">Flat bundle app packages</span></span>](flat-bundles.md) | <span data-ttu-id="ceb71-128">Beschreibt, wie Sie ein flat Bundle für Ihre app-Paket-Dateien erstellen.</span><span class="sxs-lookup"><span data-stu-id="ceb71-128">Describes how to create a flat bundle for your app’s package files.</span></span> |
| [<span data-ttu-id="ceb71-129">Paketerstellung mit dem Verpackungslayout</span><span class="sxs-lookup"><span data-stu-id="ceb71-129">Package creation with the packaging layout</span></span>](packaging-layout.md) | <span data-ttu-id="ceb71-130">Das Verpackungslayout ist ein Dokument, das die Verpackungsstruktur der App beschreibt.</span><span class="sxs-lookup"><span data-stu-id="ceb71-130">The packaging layout is a single document that describes packaging structure of the app.</span></span> <span data-ttu-id="ceb71-131">Es gibt die Bündel einer App („primär” und „optional”), die Pakete in den Bündeln sowie die Dateien in den Paketen an.</span><span class="sxs-lookup"><span data-stu-id="ceb71-131">It specifies the bundles of an app (primary and optional), the packages in the bundles, and the files in the packages.</span></span> |
