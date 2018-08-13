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
# <a name="data-access"></a>Datenzugriff

\[ Aktualisiert für UWP-Apps unter Windows10. Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]

In diesem Abschnitt wird das Speichern von Daten auf dem Gerät in einer privaten Datenbank und die Verwendung der objektrelationalen Zuordnung in UWP-Apps (Universelle Windows-Plattform) erläutert.

SQLite ist im UWP-SDK enthalten. Entity FrameworkCore funktioniert mit SQLite in UWP-Apps. Verwenden Sie diese Technologien, um für Offline- bzw. zeitweilige Konnektivitätsszenarien zu entwickeln und um Daten zwischen App-Sitzungen beizubehalten.

| Thema | Beschreibung|
|-------|------------|
| [Entity Framework Core mit SQLite für C#-Apps](entity-framework-7-with-sqlite-for-csharp-apps.md) | Entity Framework (EF) ist eine objektrelationale Zuordnung, die Ihnen über domänenspezifische Objekte die Verwendung relationaler Daten ermöglicht. In diesem Artikel wird erläutert, wie Sie Entity Framework Core mit einer SQLite-Datenbank in einer universellen Windows-App verwenden können. |
| [SQLite-Datenbanken](sqlite-databases.md) | SQLite ist ein eingebettetes Datenbankmodul ohne Server. In diesem Artikel wird erläutert, wie die im SDK enthaltene SQLite-Bibliothek verwendet wird und wie Ihre eigene SQLite-Bibliothek in einer universellen Windows-App verpackt oder aus der Quelle erstellt wird. |
