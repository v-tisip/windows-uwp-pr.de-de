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
# <a name="entity-framework-core-with-sqlite-for-c-apps"></a>Entity Framework Core mit SQLite für C#-Apps

\[ Aktualisiert für UPW-Apps unter Windows 10. Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132). \]

Entity Framework (EF) ist eine objektrelationale Zuordnung, die Ihnen über domänenspezifische Objekte die Verwendung relationaler Daten ermöglicht. In diesem Artikel wird erläutert, wie Sie Entity Framework Core mit einer SQLite-Datenbank in einer universellen Windows-App verwenden können.

Mit Entity Framework Core, das ursprünglich für .NET-Entwickler konzipiert wurde, können Sie mit SQLite auf der universellen Windows-Plattform (UWP) relationale Daten mit domänenspezifischen Objekten speichern und bearbeiten. Sie können EF-Code aus einer .NET-App zu einer UWP-App migrieren und davon ausgehen, dass die App bei entsprechenden Änderungen der Verbindungszeichenfolge funktioniert.

Derzeit unterstützt EF auf der UWP nur SQLite. Eine ausführliche exemplarische Vorgehensweise zur Installation von Entity Framework Core und zum Erstellen von Modellen finden Sie unter [Getting Started on Universal Windows Platform](http://go.microsoft.com/fwlink/p/?LinkId=735013). Die folgenden Themen werden behandelt:

-   Voraussetzungen
-   Erstellen eines neuen Projekts
-   Installieren von Entity Framework
-   Erstellen Ihres Modells
-   Erstellen Ihrer Datenbank
-   Verwenden Ihres Modells
