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
ms.sourcegitcommit: e814a13978f33654d8e995584f4b047cb53e0aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "6048218"
---
# <a name="data-access"></a>Datenzugriff

Sie können Daten mithilfe einer SQLite-Datenbank auf dem Gerät des Benutzers speichern. Sie können Ihre app auch direkt mit einer SQL Server-Datenbank verbinden, ohne jegliche Art von Dienstebene verwenden zu müssen.

| Thema | Beschreibung|
|-------|------------|
| [Verwenden einer SQLite-Datenbank in einer UWP-App](sqlite-databases.md) | Zeigt, wie Sie SQLite verwenden, um Daten in einer Lightweight-Datenbank auf dem Gerät des Benutzers speichern und abrufen. SQLite ist ein eingebettetes Datenbankmodul ohne Server. |
| [Verwenden einer SQL Server-Datenbank in einer UWP-app](sql-server-databases.md) | Beschreibt, wie Sie sich direkt mit einer SQL Server-Datenbank verbinden und dann speichern und Abrufen von Daten mithilfe der Klassen im [System.Data.SqlClient](https://msdn.microsoft.com/library/system.data.sqlclient.aspx) -Namespace. Es ist keine Dienstebene erforderlich. |

## <a name="related-topics"></a>Verwandte Themen

* [Customer Orders Database-Beispiel](https://github.com/Microsoft/Windows-appsample-customers-orders-database)
