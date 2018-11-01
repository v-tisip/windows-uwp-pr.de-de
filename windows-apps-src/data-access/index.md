---
author: normesta
ms.assetid: 76776b0f-3163-48c9-835b-3f4213968079
title: Datenzugriff
description: In diesem Abschnitt wird das Speichern von Daten auf dem Gerät in einer privaten Datenbank und die Verwendung der objektrelationalen Zuordnung in UWP-Apps (Universelle Windows-Plattform) erläutert.
ms.author: normesta
ms.date: 11/13/2017
ms.topic: article
keywords: Windows 10, UWP, Daten, Datenbank, relational, Tabellen, sqlite
ms.localizationpriority: medium
ms.openlocfilehash: beca20d358430ecd82cd1bc57459a6f6af36be77
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5877207"
---
# <a name="data-access"></a><span data-ttu-id="ae46f-104">Datenzugriff</span><span class="sxs-lookup"><span data-stu-id="ae46f-104">Data access</span></span>

<span data-ttu-id="ae46f-105">Sie können Daten mithilfe einer SQLite-Datenbank auf dem Gerät des Benutzers speichern.</span><span class="sxs-lookup"><span data-stu-id="ae46f-105">You can store data on the user's device by using a SQLite database.</span></span> <span data-ttu-id="ae46f-106">Sie können Ihre app auch direkt mit einer SQL Server-Datenbank verbinden, ohne jegliche Art von Dienstebene verwenden zu müssen.</span><span class="sxs-lookup"><span data-stu-id="ae46f-106">You can also connect your app directly to a SQL Server database without having to use any sort of service layer.</span></span>

| <span data-ttu-id="ae46f-107">Thema</span><span class="sxs-lookup"><span data-stu-id="ae46f-107">Topic</span></span> | <span data-ttu-id="ae46f-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ae46f-108">Description</span></span>|
|-------|------------|
| [<span data-ttu-id="ae46f-109">Verwenden einer SQLite-Datenbank in einer UWP-App</span><span class="sxs-lookup"><span data-stu-id="ae46f-109">Use a SQLite database in a UWP app</span></span>](sqlite-databases.md) | <span data-ttu-id="ae46f-110">Zeigt, wie Sie SQLite verwenden, um Daten in einer Lightweight-Datenbank auf dem Gerät des Benutzers speichern und abrufen.</span><span class="sxs-lookup"><span data-stu-id="ae46f-110">Shows you how to use SQLite to store and retrieve data in a light-weight database on the users device.</span></span> <span data-ttu-id="ae46f-111">SQLite ist ein eingebettetes Datenbankmodul ohne Server.</span><span class="sxs-lookup"><span data-stu-id="ae46f-111">SQLite is a server-less, embedded database engine.</span></span> |
| [<span data-ttu-id="ae46f-112">Verwenden einer SQL Server-Datenbank in einer UWP-app</span><span class="sxs-lookup"><span data-stu-id="ae46f-112">Use a SQL server database in a UWP app</span></span>](sql-server-databases.md) | <span data-ttu-id="ae46f-113">Beschreibt, wie Sie sich direkt mit einer SQL Server-Datenbank verbinden und dann speichern und Abrufen von Daten mithilfe der Klassen im [System.Data.SqlClient](https://msdn.microsoft.com/library/system.data.sqlclient.aspx) -Namespace.</span><span class="sxs-lookup"><span data-stu-id="ae46f-113">Shows you how to connect directly to a SQL Server database and then store and retrieve data by using classes in the [System.Data.SqlClient](https://msdn.microsoft.com/library/system.data.sqlclient.aspx) namespace.</span></span> <span data-ttu-id="ae46f-114">Es ist keine Dienstebene erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ae46f-114">No service layer required.</span></span> |

## <a name="related-topics"></a><span data-ttu-id="ae46f-115">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="ae46f-115">Related topics</span></span>

* [<span data-ttu-id="ae46f-116">Customer Orders Database-Beispiel</span><span class="sxs-lookup"><span data-stu-id="ae46f-116">Customer Orders Database sample</span></span>](https://github.com/Microsoft/Windows-appsample-customers-orders-database)
