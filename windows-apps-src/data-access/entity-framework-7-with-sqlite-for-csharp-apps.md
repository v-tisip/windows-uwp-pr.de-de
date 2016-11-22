---
author: mcleblanc
ms.assetid: BC7E8130-A28A-443C-8D7E-353E7DA33AE3
description: "Entity Framework (EF) ist eine objektrelationale Zuordnung, die Ihnen über domänenspezifische Objekte die Verwendung relationaler Daten ermöglicht."
title: "Entity Framework7 mit SQLite für C#-Apps"
translationtype: Human Translation
ms.sourcegitcommit: a4680f50b8ef45e4e995d0b9997c0266478fe233
ms.openlocfilehash: 07244b35b2ec20227bccc43638b56b9fda88956a

---

# Entity Framework Core1 mit SQLite für C#-Apps

\[ Aktualisiert für UWP-Apps unter Windows10. Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132). \]

Entity Framework (EF) ist eine objektrelationale Zuordnung, die Ihnen über domänenspezifische Objekte die Verwendung relationaler Daten ermöglicht. In diesem Artikel wird erläutert, wie Sie Entity Framework Core1 mit einer SQLite-Datenbank in einer universellen Windows-App verwenden können.

Mit Entity Framework Core1, das ursprünglich für .NET-Entwickler konzipiert wurde, können Sie mit SQLite auf der universellen Windows-Plattform (UWP) relationale Daten mit domänenspezifischen Objekten speichern und bearbeiten. Sie können EF-Code aus einer .NET-App zu einer UWP-App migrieren und davon ausgehen, dass die App bei entsprechenden Änderungen der Verbindungszeichenfolge funktioniert.

Derzeit unterstützt EF auf der UWP nur SQLite. Eine ausführliche exemplarische Vorgehensweise zur Installation von Entity Framework Core1 und zum Erstellen von Modellen finden Sie unter [Getting Started on Universal Windows Platform](http://go.microsoft.com/fwlink/p/?LinkId=735013). Die folgenden Themen werden behandelt:

-   Voraussetzungen
-   Erstellen eines neuen Projekts
-   Installieren von Entity Framework
-   Erstellen Ihres Modells
-   Erstellen Ihrer Datenbank
-   Verwenden Ihres Modells




<!--HONumber=Nov16_HO1-->


