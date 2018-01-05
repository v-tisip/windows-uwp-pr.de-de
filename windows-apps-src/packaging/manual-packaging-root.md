---
author: laurenhughes
ms.assetid: ee51eae3-ed55-419e-ad74-6adf1e1fb8b9
title: Manuelles Verpacken von Apps
description: "Dieser Abschnitt enthält Artikel oder Links zum manuellen Verpacken von UWP (Universelle Windows-Plattform)-Apps."
ms.author: lahugh
ms.date: 03/07/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Verpacken
ms.openlocfilehash: 8eca88588b2e444450daccd997aebb9e838a90d4
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: HT
ms.contentlocale: de-DE
---
# <a name="manual-app-packaging"></a><span data-ttu-id="e1f9f-104">Manuelles Verpacken von Apps</span><span class="sxs-lookup"><span data-stu-id="e1f9f-104">Manual app packaging</span></span>

<span data-ttu-id="e1f9f-105">Wenn Sie ein App-Paket erstellen und signieren möchten, für die Entwicklung der App aber nicht Visual Studio verwendet haben, müssen Sie die Tools für die manuelle App-Verpackung verwenden.</span><span class="sxs-lookup"><span data-stu-id="e1f9f-105">If you want to create and sign an app package, but you didn't use Visual Studio to develop your app, you'll need to use the manual app packaging tools.</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="e1f9f-106">Wenn Sie Visual Studio zum Entwickeln der App verwendet haben, wird empfohlen, dass Sie den Visual Studio-Assistenten zum Erstellen und Signieren des App-Pakets verwenden.</span><span class="sxs-lookup"><span data-stu-id="e1f9f-106">If you used Visual Studio to develop your app, it's recommended that you use the Visual Studio wizard to create and sign your app package.</span></span> <span data-ttu-id="e1f9f-107">Weitere Informationen finden Sie unter [Verpacken einer UWP-App mit Visual Studio](https://msdn.microsoft.com/windows/uwp/packaging/packaging-uwp-apps).</span><span class="sxs-lookup"><span data-stu-id="e1f9f-107">For more information, see [Package a UWP app with Visual Studio](https://msdn.microsoft.com/windows/uwp/packaging/packaging-uwp-apps).</span></span>

## <a name="purpose"></a><span data-ttu-id="e1f9f-108">Zweck</span><span class="sxs-lookup"><span data-stu-id="e1f9f-108">Purpose</span></span>

<span data-ttu-id="e1f9f-109">Dieser Abschnitt enthält Artikel oder Links zum manuellen Verpacken von UWP (Universelle Windows-Plattform)-Apps.</span><span class="sxs-lookup"><span data-stu-id="e1f9f-109">This section contains or links to articles about manually packaging Universal Windows Platform (UWP) apps.</span></span>

| <span data-ttu-id="e1f9f-110">Thema</span><span class="sxs-lookup"><span data-stu-id="e1f9f-110">Topic</span></span> | <span data-ttu-id="e1f9f-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e1f9f-111">Description</span></span> |
|-------|-------------|
| [<span data-ttu-id="e1f9f-112">Erstellen eines App-Pakets mit dem Tool „MakeAppx.exe“</span><span class="sxs-lookup"><span data-stu-id="e1f9f-112">Create an app package with the MakeAppx.exe tool</span></span>](create-app-package-with-makeappx-tool.md) | <span data-ttu-id="e1f9f-113">MakeAppx.exe erstellt, verschlüsselt, entschlüsselt und extrahiert Dateien aus App-Paketen und -Bündeln.</span><span class="sxs-lookup"><span data-stu-id="e1f9f-113">MakeAppx.exe creates, encrypts, decrypts, and extracts files from app packages and bundles.</span></span> |
| [<span data-ttu-id="e1f9f-114">Erstellen von Zertifikaten für die Paketsignatur</span><span class="sxs-lookup"><span data-stu-id="e1f9f-114">Create a certificate for package signing</span></span>](create-certificate-package-signing.md) | <span data-ttu-id="e1f9f-115">Erstellen und Exportieren eines Zertifikats für die App-Paketsignatur mit PowerShell-Tools.</span><span class="sxs-lookup"><span data-stu-id="e1f9f-115">Create and export a certificate for app package signing with PowerShell tools.</span></span> |
| [<span data-ttu-id="e1f9f-116">Signieren eines App-Pakets mit SignTool</span><span class="sxs-lookup"><span data-stu-id="e1f9f-116">Sign an app package using SignTool</span></span>](sign-app-package-using-signtool.md) | <span data-ttu-id="e1f9f-117">Verwenden von SignTool zur manuellen Signatur eines App-Pakets mit einem Zertifikat.</span><span class="sxs-lookup"><span data-stu-id="e1f9f-117">Use SignTool to manually sign an app package with a certificate.</span></span> |