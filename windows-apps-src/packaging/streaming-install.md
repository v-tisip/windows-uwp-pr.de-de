---
ms.assetid: df4d227c-21f9-4f99-9e95-3305b149d9c5
title: UWP-App-Streaming-Installation
description: Durch die Installation des Universelle Windows Plattform (UWP)-App-Streaming können Sie angeben, welche Teile der App der Microsoft Store zuerst herunterladen soll. Wenn die wichtigen Dateien der App zuerst heruntergeladen werden, können Benutzer die App starten und mit dieser interagieren, während der Rest noch im Hintergrund heruntergeladen wird.
ms.date: 04/05/2017
ms.topic: article
keywords: Windows 10, Uwp, streaming-Installation, Uwp-app-streaming installieren
ms.localizationpriority: medium
ms.openlocfilehash: 3fa33410be31b1732a04c51d14dbbd114e1f5e0c
ms.sourcegitcommit: b4c502d69a13340f6e3c887aa3c26ef2aeee9cee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "8466980"
---
# <a name="uwp-app-streaming-install"></a><span data-ttu-id="c616c-105">UWP-App-Streaming-Installation</span><span class="sxs-lookup"><span data-stu-id="c616c-105">UWP App Streaming Install</span></span>
<span data-ttu-id="c616c-106">Durch die Installation des Universelle Windows Plattform (UWP)-App-Streaming können Sie angeben, welche Teile der App der Microsoft Store zuerst herunterladen soll.</span><span class="sxs-lookup"><span data-stu-id="c616c-106">Universal Windows Platform (UWP) App Streaming Install enables you to specify which parts of your app you would like the Microsoft Store to download first.</span></span> <span data-ttu-id="c616c-107">Wenn die wichtigen Dateien der App zuerst heruntergeladen werden, können Benutzer die App starten und mit dieser interagieren, während der Rest noch im Hintergrund heruntergeladen wird.</span><span class="sxs-lookup"><span data-stu-id="c616c-107">When the essential files of the app are downloaded first, the user can launch and interact with the app while the rest of it finishes downloading in the background.</span></span> 

<span data-ttu-id="c616c-108">UWP-App-Streaming-Installation verwenden, Sie die Dateien der app in Abschnitte unterteilen müssen.</span><span class="sxs-lookup"><span data-stu-id="c616c-108">To use UWP App Streaming Install you'll need to divide your app's files into sections.</span></span> <span data-ttu-id="c616c-109">Zu diesem Zweck erstellen Sie eine Inhalts-gruppenzuordnung, die eine XML-Datei, die mit Ihrer app verpackt ist, sodass Sie einen Satz Download Priorität und die Reihenfolge.</span><span class="sxs-lookup"><span data-stu-id="c616c-109">To do this, you'll create a content group map, which is an XML file that's packaged with your app, allowing you to set download priority and order.</span></span> <span data-ttu-id="c616c-110">Finden Sie weitere Informationen unter folgendem Link.</span><span class="sxs-lookup"><span data-stu-id="c616c-110">See the topic linked below for more information.</span></span>

<span data-ttu-id="c616c-111">Eine vollständige Anleitung zum Hinzufügen von UWP-App-Streaming-Installation zu Ihrer UWP-app sehen Sie sich diese [blogreihe](https://blogs.msdn.microsoft.com/appinstaller/2017/03/15/uwp-streaming-app-installation/).</span><span class="sxs-lookup"><span data-stu-id="c616c-111">For a complete guide on adding UWP App Streaming Install to your UWP app, check out this [blog series](https://blogs.msdn.microsoft.com/appinstaller/2017/03/15/uwp-streaming-app-installation/).</span></span>

| <span data-ttu-id="c616c-112">Thema</span><span class="sxs-lookup"><span data-stu-id="c616c-112">Topic</span></span> | <span data-ttu-id="c616c-113">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c616c-113">Description</span></span> | 
|-------|-------------|
| [<span data-ttu-id="c616c-114">Erstellen und konvertieren Sie eine Quellinhalt-Gruppenzuordnung.</span><span class="sxs-lookup"><span data-stu-id="c616c-114">Create and convert a source content group map</span></span>](create-cgm.md) | <span data-ttu-id="c616c-115">Um Ihre Universelle Windows-Plattform (UWP)-App für die UWP-App-Streaming-Installation vorzubereiten, müssen Sie eine Inhalts-Gruppenzuordnung erstellen.</span><span class="sxs-lookup"><span data-stu-id="c616c-115">To get your Universal Windows Platform (UWP) app ready for UWP App Streaming Install, you'll need to create a content group map.</span></span> <span data-ttu-id="c616c-116">Dieser Artikel hilft Ihnen mit den Einzelheiten für das Erstellen und Konvertieren einer Inhalts-Gruppenzuordnung und bietet gleichzeitig einige Tipps und Tricks.</span><span class="sxs-lookup"><span data-stu-id="c616c-116">This article will help you with the specifics of creating and converting a content group map while providing some tips and tricks along the way.</span></span> |