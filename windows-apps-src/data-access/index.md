---
ms.assetid: 76776b0f-3163-48c9-835b-3f4213968079
title: Datenzugriff
description: In diesem Abschnitt wird das Speichern von Daten auf dem Gerät in einer privaten Datenbank und die Verwendung der objektrelationalen Zuordnung in UWP-Apps (Universelle Windows-Plattform) erläutert.
ms.date: 11/13/2017
ms.topic: article
keywords: Windows 10, UWP, Daten, Datenbank, relational, Tabellen, sqlite
ms.localizationpriority: medium
ms.openlocfilehash: eb5adbdd3ae12d039d934e8d0cbe468ae5c1187c
ms.sourcegitcommit: 681c70f964210ab49ac5d06357ae96505bb78741
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2018
ms.locfileid: "7695119"
---
# <a name="data-access"></a><span data-ttu-id="5e3cd-104">Datenzugriff</span><span class="sxs-lookup"><span data-stu-id="5e3cd-104">Data access</span></span>

<span data-ttu-id="5e3cd-105">Sie können Daten auf dem Gerät des Benutzers speichern, mit einer SQLite-Datenbank.</span><span class="sxs-lookup"><span data-stu-id="5e3cd-105">You can store data on the user's device by using a SQLite database.</span></span> <span data-ttu-id="5e3cd-106">Sie können Ihre app auch direkt mit einer SQL Server-Datenbank verbinden, ohne jegliche Art von Dienstebene verwenden zu müssen.</span><span class="sxs-lookup"><span data-stu-id="5e3cd-106">You can also connect your app directly to a SQL Server database without having to use any sort of service layer.</span></span>

| <span data-ttu-id="5e3cd-107">Thema</span><span class="sxs-lookup"><span data-stu-id="5e3cd-107">Topic</span></span> | <span data-ttu-id="5e3cd-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="5e3cd-108">Description</span></span>|
|-------|------------|
| [<span data-ttu-id="5e3cd-109">Verwenden einer SQLite-Datenbank in einer UWP-App</span><span class="sxs-lookup"><span data-stu-id="5e3cd-109">Use a SQLite database in a UWP app</span></span>](sqlite-databases.md) | <span data-ttu-id="5e3cd-110">Zeigt, wie Sie SQLite verwenden, um Daten in einer Lightweight-Datenbank auf dem Gerät des Benutzers speichern und abrufen.</span><span class="sxs-lookup"><span data-stu-id="5e3cd-110">Shows you how to use SQLite to store and retrieve data in a light-weight database on the users device.</span></span> <span data-ttu-id="5e3cd-111">SQLite ist ein eingebettetes Datenbankmodul ohne Server.</span><span class="sxs-lookup"><span data-stu-id="5e3cd-111">SQLite is a server-less, embedded database engine.</span></span> |
| [<span data-ttu-id="5e3cd-112">Verwenden einer SQL Server-Datenbank in einer UWP-app</span><span class="sxs-lookup"><span data-stu-id="5e3cd-112">Use a SQL server database in a UWP app</span></span>](sql-server-databases.md) | <span data-ttu-id="5e3cd-113">Sie zeigt, wie Sie direkt mit einer SQL Server-Datenbank verbinden und dann speichern und Abrufen von Daten mithilfe der Klassen im [System.Data.SqlClient](https://msdn.microsoft.com/library/system.data.sqlclient.aspx) -Namespace.</span><span class="sxs-lookup"><span data-stu-id="5e3cd-113">Shows you how to connect directly to a SQL Server database and then store and retrieve data by using classes in the [System.Data.SqlClient](https://msdn.microsoft.com/library/system.data.sqlclient.aspx) namespace.</span></span> <span data-ttu-id="5e3cd-114">Es ist keine Dienstebene erforderlich.</span><span class="sxs-lookup"><span data-stu-id="5e3cd-114">No service layer required.</span></span> |

## <a name="related-topics"></a><span data-ttu-id="5e3cd-115">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="5e3cd-115">Related topics</span></span>

* [<span data-ttu-id="5e3cd-116">Customer Orders Database-Beispiel</span><span class="sxs-lookup"><span data-stu-id="5e3cd-116">Customer Orders Database sample</span></span>](https://github.com/Microsoft/Windows-appsample-customers-orders-database)
