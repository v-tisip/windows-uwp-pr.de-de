---
author: normesta
ms.assetid: 76776b0f-3163-48c9-835b-3f4213968079
title: Datenzugriff
description: In diesem Abschnitt wird das Speichern von Daten auf dem Gerät in einer privaten Datenbank und die Verwendung der objektrelationalen Zuordnung in UWP-Apps (Universelle Windows-Plattform) erläutert.
ms.author: normesta
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, Daten, Datenbank, relational, Tabellen, sqlite
ms.openlocfilehash: 19690b6877fb4304b7740e6098711ca0b097d567
ms.sourcegitcommit: 378382419f1fda4e4df76ffa9c8cea753d271e6a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
ms.locfileid: "665320"
---
# <a name="data-access"></a><span data-ttu-id="1439f-104">Datenzugriff</span><span class="sxs-lookup"><span data-stu-id="1439f-104">Data access</span></span>

<span data-ttu-id="1439f-105">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="1439f-105">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="1439f-106">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="1439f-106">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>

<span data-ttu-id="1439f-107">In diesem Abschnitt wird das Speichern von Daten auf dem Gerät in einer privaten Datenbank und die Verwendung der objektrelationalen Zuordnung in UWP-Apps (Universelle Windows-Plattform) erläutert.</span><span class="sxs-lookup"><span data-stu-id="1439f-107">This section discusses storing data on the device in a private database and using object relational mapping in Universal Windows Platform (UWP) apps.</span></span>

<span data-ttu-id="1439f-108">SQLite ist im UWP-SDK enthalten.</span><span class="sxs-lookup"><span data-stu-id="1439f-108">SQLite is included in the UWP SDK.</span></span> <span data-ttu-id="1439f-109">Entity FrameworkCore funktioniert mit SQLite in UWP-Apps.</span><span class="sxs-lookup"><span data-stu-id="1439f-109">Entity Framework Core works with SQLite in UWP apps.</span></span> <span data-ttu-id="1439f-110">Verwenden Sie diese Technologien, um für Offline- bzw. zeitweilige Konnektivitätsszenarien zu entwickeln und um Daten zwischen App-Sitzungen beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="1439f-110">Use these technologies to develop for offline / intermittent connectivity scenarios, and to persist data across app sessions.</span></span>

| <span data-ttu-id="1439f-111">Thema</span><span class="sxs-lookup"><span data-stu-id="1439f-111">Topic</span></span> | <span data-ttu-id="1439f-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="1439f-112">Description</span></span>|
|-------|------------|
| [<span data-ttu-id="1439f-113">Entity Framework Core mit SQLite für C#-Apps</span><span class="sxs-lookup"><span data-stu-id="1439f-113">Entity framework Core with SQLite for C# apps</span></span>](entity-framework-7-with-sqlite-for-csharp-apps.md) | <span data-ttu-id="1439f-114">Entity Framework (EF) ist eine objektrelationale Zuordnung, die Ihnen über domänenspezifische Objekte die Verwendung relationaler Daten ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="1439f-114">Entity Framework (EF) is an object-relational mapper that enables you to work with relational data using domain-specific objects.</span></span> <span data-ttu-id="1439f-115">In diesem Artikel wird erläutert, wie Sie Entity Framework Core mit einer SQLite-Datenbank in einer universellen Windows-App verwenden können.</span><span class="sxs-lookup"><span data-stu-id="1439f-115">This article explains how you can use Entity Framework Core with a SQLite database in a Universal Windows app.</span></span> |
| [<span data-ttu-id="1439f-116">SQLite-Datenbanken</span><span class="sxs-lookup"><span data-stu-id="1439f-116">SQLite databases</span></span>](sqlite-databases.md) | <span data-ttu-id="1439f-117">SQLite ist ein eingebettetes Datenbankmodul ohne Server.</span><span class="sxs-lookup"><span data-stu-id="1439f-117">SQLite is a server-less, embedded database engine.</span></span> <span data-ttu-id="1439f-118">In diesem Artikel wird erläutert, wie die im SDK enthaltene SQLite-Bibliothek verwendet wird und wie Ihre eigene SQLite-Bibliothek in einer universellen Windows-App verpackt oder aus der Quelle erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="1439f-118">This article explains how to use the SQLite library included in the SDK, package your own SQLite library in a Universal Windows app, or build it from the source.</span></span> |
