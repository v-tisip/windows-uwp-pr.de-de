---
author: normesta
ms.assetid: BC7E8130-A28A-443C-8D7E-353E7DA33AE3
description: "Entity Framework (EF) ist eine objektrelationale Zuordnung, die Ihnen über domänenspezifische Objekte die Verwendung relationaler Daten ermöglicht."
title: "Entity Framework Core mit SQLite für C#-Apps"
ms.author: normesta
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, SQLite-, C#-, EF, Entity Framework
ms.openlocfilehash: 9d447b8a197ed7eaea0f991749064912dffb66d7
ms.sourcegitcommit: 378382419f1fda4e4df76ffa9c8cea753d271e6a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
# <a name="entity-framework-core-with-sqlite-for-c-apps"></a><span data-ttu-id="8bb6c-104">Entity Framework Core mit SQLite für C#-Apps</span><span class="sxs-lookup"><span data-stu-id="8bb6c-104">Entity Framework Core with SQLite for C# apps</span></span>

<span data-ttu-id="8bb6c-105">\[ Aktualisiert für UPW-Apps unter Windows 10.</span><span class="sxs-lookup"><span data-stu-id="8bb6c-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="8bb6c-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132). \]</span><span class="sxs-lookup"><span data-stu-id="8bb6c-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="8bb6c-107">Entity Framework (EF) ist eine objektrelationale Zuordnung, die Ihnen über domänenspezifische Objekte die Verwendung relationaler Daten ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="8bb6c-107">Entity Framework (EF) is an object-relational mapper that enables you to work with relational data using domain-specific objects.</span></span> <span data-ttu-id="8bb6c-108">In diesem Artikel wird erläutert, wie Sie Entity Framework Core mit einer SQLite-Datenbank in einer universellen Windows-App verwenden können.</span><span class="sxs-lookup"><span data-stu-id="8bb6c-108">This article explains how you can use Entity Framework Core with a SQLite database in a Universal Windows app.</span></span>

<span data-ttu-id="8bb6c-109">Mit Entity Framework Core, das ursprünglich für .NET-Entwickler konzipiert wurde, können Sie mit SQLite auf der universellen Windows-Plattform (UWP) relationale Daten mit domänenspezifischen Objekten speichern und bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="8bb6c-109">Originally for .NET developers, Entity Framework Core can be used with SQLite on Universal Windows Platform (UWP) to store and manipulate relational data using domain specific objects.</span></span> <span data-ttu-id="8bb6c-110">Sie können EF-Code aus einer .NET-App zu einer UWP-App migrieren und davon ausgehen, dass die App bei entsprechenden Änderungen der Verbindungszeichenfolge funktioniert.</span><span class="sxs-lookup"><span data-stu-id="8bb6c-110">You can migrate EF code from a .NET app to a UWP app and expect it work with appropriate changes to the connection string.</span></span>

<span data-ttu-id="8bb6c-111">Derzeit unterstützt EF auf der UWP nur SQLite.</span><span class="sxs-lookup"><span data-stu-id="8bb6c-111">Currently EF only supports SQLite on UWP.</span></span> <span data-ttu-id="8bb6c-112">Eine ausführliche exemplarische Vorgehensweise zur Installation von Entity Framework Core und zum Erstellen von Modellen finden Sie unter [Getting Started on Universal Windows Platform](http://go.microsoft.com/fwlink/p/?LinkId=735013).</span><span class="sxs-lookup"><span data-stu-id="8bb6c-112">A detailed walkthrough on installing Entity Framework Core, and creating models is available at the [Getting Started on Universal Windows Platform page](http://go.microsoft.com/fwlink/p/?LinkId=735013).</span></span> <span data-ttu-id="8bb6c-113">Die folgenden Themen werden behandelt:</span><span class="sxs-lookup"><span data-stu-id="8bb6c-113">It covers the following topics:</span></span>

-   <span data-ttu-id="8bb6c-114">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="8bb6c-114">Prerequisites</span></span>
-   <span data-ttu-id="8bb6c-115">Erstellen eines neuen Projekts</span><span class="sxs-lookup"><span data-stu-id="8bb6c-115">Create a new project</span></span>
-   <span data-ttu-id="8bb6c-116">Installieren von Entity Framework</span><span class="sxs-lookup"><span data-stu-id="8bb6c-116">Install Entity Framework</span></span>
-   <span data-ttu-id="8bb6c-117">Erstellen Ihres Modells</span><span class="sxs-lookup"><span data-stu-id="8bb6c-117">Create your model</span></span>
-   <span data-ttu-id="8bb6c-118">Erstellen Ihrer Datenbank</span><span class="sxs-lookup"><span data-stu-id="8bb6c-118">Create your database</span></span>
-   <span data-ttu-id="8bb6c-119">Verwenden Ihres Modells</span><span class="sxs-lookup"><span data-stu-id="8bb6c-119">Use your model</span></span>
