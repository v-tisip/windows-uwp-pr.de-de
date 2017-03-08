---
author: mcleblanc
ms.assetid: BC7E8130-A28A-443C-8D7E-353E7DA33AE3
description: "Entity Framework (EF) ist eine objektrelationale Zuordnung, die Ihnen über domänenspezifische Objekte die Verwendung relationaler Daten ermöglicht."
title: "Entity Framework 7 mit SQLite für C#-Apps"
ms.author: markl
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Windows 10, UWP, SQLite-, C#-, EF, Entity Framework"
translationtype: Human Translation
ms.sourcegitcommit: c6b64cff1bbebc8ba69bc6e03d34b69f85e798fc
ms.openlocfilehash: 2ab2a12f6c2bc2f0f8853b404afaf13bf80635b7
ms.lasthandoff: 02/07/2017

---

# <a name="entity-framework-core-1-with-sqlite-for-c-apps"></a>Entity Framework Core 1 mit SQLite für C#-Apps

\[ Aktualisiert für UWP-Apps unter Windows 10. Artikel zu Windows 8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132). \]

Entity Framework (EF) ist eine objektrelationale Zuordnung, die Ihnen über domänenspezifische Objekte die Verwendung relationaler Daten ermöglicht. In diesem Artikel wird erläutert, wie Sie Entity Framework Core 1 mit einer SQLite-Datenbank in einer universellen Windows-App verwenden können.

Mit Entity Framework Core 1, das ursprünglich für .NET-Entwickler konzipiert wurde, können Sie mit SQLite auf der universellen Windows-Plattform (UWP) relationale Daten mit domänenspezifischen Objekten speichern und bearbeiten. Sie können EF-Code aus einer .NET-App zu einer UWP-App migrieren und davon ausgehen, dass die App bei entsprechenden Änderungen der Verbindungszeichenfolge funktioniert.

Derzeit unterstützt EF auf der UWP nur SQLite. Eine ausführliche exemplarische Vorgehensweise zur Installation von Entity Framework Core 1 und zum Erstellen von Modellen finden Sie unter [Getting Started on Universal Windows Platform](http://go.microsoft.com/fwlink/p/?LinkId=735013). Die folgenden Themen werden behandelt:

-   Voraussetzungen
-   Erstellen eines neuen Projekts
-   Installieren von Entity Framework
-   Erstellen Ihres Modells
-   Erstellen Ihrer Datenbank
-   Verwenden Ihres Modells

