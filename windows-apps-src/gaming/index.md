---
author: mtoepke
title: Programmierung von Spielen
description: Die Universelle Windows-Plattform (UWP) bietet neue Möglichkeiten zum Erstellen, Verteilen und Monetisieren von Spielen. Hier erhalten Sie Informationen zum Starten eines neuen Spiels oder Portieren eines vorhandenen Spiels.
ms.assetid: 4073b835-c900-4ff2-9fc5-da52f9432a1f
ms.author: mtoepke
ms.date: 06/13/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Spiele, DirectX
ms.openlocfilehash: 2f98c038c745615d16227334d7e87426394d5c79
ms.sourcegitcommit: a61e9fc06f74dc54c36abf7acb85eeb606e475b8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2017
ms.locfileid: "678225"
---
# <a name="game-programming"></a><span data-ttu-id="3058c-105">Programmierung von Spielen</span><span class="sxs-lookup"><span data-stu-id="3058c-105">Game programming</span></span>

<span data-ttu-id="3058c-106">Die Universelle Windows-Plattform (UWP) bietet neue Möglichkeiten zum Erstellen, Verteilen und Monetisieren von Spielen.</span><span class="sxs-lookup"><span data-stu-id="3058c-106">Universal Windows Platform (UWP) offers new opportunities to create, distribute, and monetize games.</span></span> <span data-ttu-id="3058c-107">Informationen Sie zum Erstellen eines Spiels für Windows10.</span><span class="sxs-lookup"><span data-stu-id="3058c-107">Learn about creating a game for Windows 10.</span></span>

| <span data-ttu-id="3058c-108">Thema</span><span class="sxs-lookup"><span data-stu-id="3058c-108">Topic</span></span> | <span data-ttu-id="3058c-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3058c-109">Description</span></span> |
|---------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [<span data-ttu-id="3058c-110">Handbuch zur Entwicklung von Spielen unter Windows10</span><span class="sxs-lookup"><span data-stu-id="3058c-110">Windows 10 game development guide</span></span>](e2e.md) | <span data-ttu-id="3058c-111">Ein umfassender Leitfaden für Ressourcen und Informationen zur Entwicklung von UWP-Spielen.</span><span class="sxs-lookup"><span data-stu-id="3058c-111">An end-to-end guide with resources and information for developing UWP games.</span></span> |
| [<span data-ttu-id="3058c-112">Planen</span><span class="sxs-lookup"><span data-stu-id="3058c-112">Planning</span></span>](planning.md) | <span data-ttu-id="3058c-113">Dieses Thema enthält eine Liste der Artikel für die Phase der Spieleplanung.</span><span class="sxs-lookup"><span data-stu-id="3058c-113">This topic contains a list of articles for the game planning stage.</span></span> |
| [<span data-ttu-id="3058c-114">UWP-Programmierung</span><span class="sxs-lookup"><span data-stu-id="3058c-114">UWP programming</span></span>](uwp-programming.md) | <span data-ttu-id="3058c-115">Erfahren Sie, wie Sie Windows-Runtime-APIs zum Entwickeln von UWP-Spielen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="3058c-115">Learn how to use Windows Runtime APIs to develop UWP games.</span></span> |
| [<span data-ttu-id="3058c-116">Entwicklung von Spielen (Video)</span><span class="sxs-lookup"><span data-stu-id="3058c-116">Game development videos</span></span>](game-development-videos.md) | <span data-ttu-id="3058c-117">Eine Sammlung von Videos zur Spieleentwicklung von wichtigen Konferenzen und Veranstaltungen.</span><span class="sxs-lookup"><span data-stu-id="3058c-117">A collection of game dev videos from major conferences and events.</span></span> |

<span data-ttu-id="3058c-118">Weitere Informationen zum Entwickeln von UWP-Spielen mit DirectX finden Sie unter [DirectX-Programmierung ](directx-programming.md).</span><span class="sxs-lookup"><span data-stu-id="3058c-118">To learn about developing UWP games using DirectX, go to [DirectX programming](directx-programming.md).</span></span>

> **<span data-ttu-id="3058c-119">Hinweis:</span><span class="sxs-lookup"><span data-stu-id="3058c-119">Note</span></span>**  
<span data-ttu-id="3058c-120">Dieser Artikel ist für Windows10-Entwickler bestimmt, die Apps für die universelle Windows-Plattform (UWP) schreiben.</span><span class="sxs-lookup"><span data-stu-id="3058c-120">This article is for Windows 10 developers writing Universal Windows Platform (UWP) apps.</span></span> <span data-ttu-id="3058c-121">Wenn Sie für Windows8.x oder Windows Phone8.x entwickeln, hilft Ihnen die [archivierte Dokumentation](http://go.microsoft.com/fwlink/p/?linkid=619132) weiter.</span><span class="sxs-lookup"><span data-stu-id="3058c-121">If you’re developing for Windows 8.x or Windows Phone 8.x, see the [archived documentation](http://go.microsoft.com/fwlink/p/?linkid=619132).</span></span>

 

<span data-ttu-id="3058c-122">Damit Sie die Übersichten und Lernprogramme zur Spieleentwicklung optimal nutzen können, sollten Sie mit den folgenden Themen vertraut sein:</span><span class="sxs-lookup"><span data-stu-id="3058c-122">To make the best use of the game development overviews and tutorials, you should be familiar with the following subjects:</span></span>

-   <span data-ttu-id="3058c-123">Microsoft C++ mit Komponentenerweiterungen (C++/CX).</span><span class="sxs-lookup"><span data-stu-id="3058c-123">Microsoft C++ with Component Extensions (C++/CX).</span></span> <span data-ttu-id="3058c-124">Dies ist ein Update für MicrosoftC++, das die automatische Verweiszählung einführt. Außerdem handelt es sich hierbei um die Sprache für die Entwicklung eines UWP-Spiels mit DirectX11.1 oder einer höheren Version</span><span class="sxs-lookup"><span data-stu-id="3058c-124">This is an update to Microsoft C++ that incorporates automatic reference counting, and is the language for developing UWP games with DirectX 11.1 or later versions</span></span>
-   <span data-ttu-id="3058c-125">Grundlegende Terminologie für die Grafikprogrammierung</span><span class="sxs-lookup"><span data-stu-id="3058c-125">Basic graphics programming terminology</span></span>
-   <span data-ttu-id="3058c-126">Grundlegende Konzepte der Windows-Programmierung</span><span class="sxs-lookup"><span data-stu-id="3058c-126">Basic Windows programming concepts</span></span>
-   <span data-ttu-id="3058c-127">Grundlegende Kenntnisse der APIs von Direct3D 9 oder 11</span><span class="sxs-lookup"><span data-stu-id="3058c-127">Basic familiarity with the Direct3D 9 or 11 APIs</span></span>

 

 




