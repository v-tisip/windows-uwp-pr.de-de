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
ms.sourcegitcommit: 38f06f1714334273d865935d9afb80efffe97a17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "6189723"
---
# <a name="data-access"></a><span data-ttu-id="982cb-104">Datenzugriff</span><span class="sxs-lookup"><span data-stu-id="982cb-104">Data access</span></span>

<span data-ttu-id="982cb-105">Sie können Daten auf dem Gerät des Benutzers speichern, mit einer SQLite-Datenbank.</span><span class="sxs-lookup"><span data-stu-id="982cb-105">You can store data on the user's device by using a SQLite database.</span></span> <span data-ttu-id="982cb-106">Sie können Ihre app auch direkt mit einer SQL Server-Datenbank verbinden, ohne jegliche Art von Dienstebene verwenden zu müssen.</span><span class="sxs-lookup"><span data-stu-id="982cb-106">You can also connect your app directly to a SQL Server database without having to use any sort of service layer.</span></span>

| <span data-ttu-id="982cb-107">Thema</span><span class="sxs-lookup"><span data-stu-id="982cb-107">Topic</span></span> | <span data-ttu-id="982cb-108">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="982cb-108">Description</span></span>|
|-------|------------|
| [<span data-ttu-id="982cb-109">Verwenden einer SQLite-Datenbank in einer UWP-App</span><span class="sxs-lookup"><span data-stu-id="982cb-109">Use a SQLite database in a UWP app</span></span>](sqlite-databases.md) | <span data-ttu-id="982cb-110">Zeigt, wie Sie SQLite verwenden, um Daten in einer Lightweight-Datenbank auf dem Gerät des Benutzers speichern und abrufen.</span><span class="sxs-lookup"><span data-stu-id="982cb-110">Shows you how to use SQLite to store and retrieve data in a light-weight database on the users device.</span></span> <span data-ttu-id="982cb-111">SQLite ist ein eingebettetes Datenbankmodul ohne Server.</span><span class="sxs-lookup"><span data-stu-id="982cb-111">SQLite is a server-less, embedded database engine.</span></span> |
| [<span data-ttu-id="982cb-112">Verwenden einer SQL Server-Datenbank in einer UWP-app</span><span class="sxs-lookup"><span data-stu-id="982cb-112">Use a SQL server database in a UWP app</span></span>](sql-server-databases.md) | <span data-ttu-id="982cb-113">Sie zeigt, wie Sie direkt mit einer SQL Server-Datenbank verbinden und dann speichern und Abrufen von Daten mithilfe der Klassen im [System.Data.SqlClient](https://msdn.microsoft.com/library/system.data.sqlclient.aspx) -Namespace.</span><span class="sxs-lookup"><span data-stu-id="982cb-113">Shows you how to connect directly to a SQL Server database and then store and retrieve data by using classes in the [System.Data.SqlClient](https://msdn.microsoft.com/library/system.data.sqlclient.aspx) namespace.</span></span> <span data-ttu-id="982cb-114">Es ist keine Dienstebene erforderlich.</span><span class="sxs-lookup"><span data-stu-id="982cb-114">No service layer required.</span></span> |

## <a name="related-topics"></a><span data-ttu-id="982cb-115">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="982cb-115">Related topics</span></span>

* [<span data-ttu-id="982cb-116">Customer Orders Database-Beispiel</span><span class="sxs-lookup"><span data-stu-id="982cb-116">Customer Orders Database sample</span></span>](https://github.com/Microsoft/Windows-appsample-customers-orders-database)
