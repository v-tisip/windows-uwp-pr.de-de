---
ms.assetid: 76776b0f-3163-48c9-835b-3f4213968079
title: Datenzugriff
description: In diesem Abschnitt wird das Speichern von Daten auf dem Gerät in einer privaten Datenbank und die Verwendung der objektrelationalen Zuordnung in UWP-Apps (Universelle Windows-Plattform) erläutert.
ms.date: 11/13/2017
ms.topic: article
keywords: Windows 10, UWP, Daten, Datenbank, relational, Tabellen, sqlite
ms.localizationpriority: medium
ms.openlocfilehash: eb5adbdd3ae12d039d934e8d0cbe468ae5c1187c
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8899999"
---
# <a name="data-access"></a>Datenzugriff

Sie können Daten auf dem Gerät des Benutzers speichern, mit einer SQLite-Datenbank. Sie können Ihre app auch direkt mit einer SQL Server-Datenbank verbinden, ohne jegliche Art von Dienstebene verwenden zu müssen.

| Thema | Beschreibung|
|-------|------------|
| [Verwenden einer SQLite-Datenbank in einer UWP-App](sqlite-databases.md) | Zeigt, wie Sie SQLite verwenden, um speichern und Abrufen von Daten in einer Lightweight-Datenbank auf dem Gerät des Benutzers. SQLite ist ein eingebettetes Datenbankmodul ohne Server. |
| [Verwenden einer SQL Server-Datenbank in einer UWP-app](sql-server-databases.md) | Sie zeigt, wie Sie sich direkt mit einer SQL Server-Datenbank verbinden und dann speichern und Abrufen von Daten mithilfe der Klassen im [System.Data.SqlClient](https://msdn.microsoft.com/library/system.data.sqlclient.aspx) -Namespace. Es ist keine Dienstebene erforderlich. |

## <a name="related-topics"></a>Verwandte Themen

* [Beispiel für Kunden-Datenbank für Kundenaufträge](https://github.com/Microsoft/Windows-appsample-customers-orders-database)
