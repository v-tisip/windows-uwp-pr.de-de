---
author: normesta
title: Verwenden einer SQLite-Datenbank in einer UWP-App
description: Verwenden Sie eine SQLite-Datenbank in einer UWP-App.
ms.author: normesta
ms.date: 06/08/2018
ms.topic: article
keywords: Windows 10, UWP, SQLite, Datenbank
ms.localizationpriority: medium
ms.openlocfilehash: 77911b101f488bb7bfef82b9cc480679ce15b1f3
ms.sourcegitcommit: 93c0a60cf531c7d9fe7b00e7cf78df86906f9d6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2018
ms.locfileid: "7563383"
---
# <a name="use-a-sqlite-database-in-a-uwp-app"></a><span data-ttu-id="810d3-104">Verwenden einer SQLite-Datenbank in einer UWP-App</span><span class="sxs-lookup"><span data-stu-id="810d3-104">Use a SQLite database in a UWP app</span></span>
<span data-ttu-id="810d3-105">Sie können SQLite verwenden, um Daten in einer einfachen Datenbank auf dem Gerät des Benutzers zu speichern und abzurufen.</span><span class="sxs-lookup"><span data-stu-id="810d3-105">You can use SQLite to store and retrieve data in a light-weight database on the users device.</span></span> <span data-ttu-id="810d3-106">Dieser Leitfaden zeigt Ihnen wie.</span><span class="sxs-lookup"><span data-stu-id="810d3-106">This guide shows you how.</span></span>

## <a name="some-benefits-of-using-sqlite-for-local-storage"></a><span data-ttu-id="810d3-107">Einige Vorteile der Verwendung von SQLite für die lokale Speicherung</span><span class="sxs-lookup"><span data-stu-id="810d3-107">Some benefits of using SQLite for local storage</span></span>

<span data-ttu-id="810d3-108">:heavy_check_mark: SQLite ist einfach und eigenständig.</span><span class="sxs-lookup"><span data-stu-id="810d3-108">:heavy_check_mark: SQLite is light-weight and self-contained.</span></span> <span data-ttu-id="810d3-109">Es ist eine Code-Bibliothek ohne weitere Abhängigkeiten.</span><span class="sxs-lookup"><span data-stu-id="810d3-109">It's a code library without any other dependencies.</span></span> <span data-ttu-id="810d3-110">Es gibt nichts zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="810d3-110">There's nothing to configure.</span></span>

<span data-ttu-id="810d3-111">:heavy_check_mark: Es gibt keinen Datenbankserver.</span><span class="sxs-lookup"><span data-stu-id="810d3-111">:heavy_check_mark: There's no database server.</span></span> <span data-ttu-id="810d3-112">Client und der Server laufen im selben Prozess.</span><span class="sxs-lookup"><span data-stu-id="810d3-112">The client and the server run in the same process.</span></span>

<span data-ttu-id="810d3-113">:heavy_check_mark: SQLite ist öffentlich zugänglich, so dass Sie es mit Ihrer App frei verwenden und verteilen können.</span><span class="sxs-lookup"><span data-stu-id="810d3-113">:heavy_check_mark: SQLite is in the public domain so you can freely use and distribute it with your app.</span></span>

<span data-ttu-id="810d3-114">:heavy_check_mark: SQLite arbeitet plattform- und architekturübergreifend.</span><span class="sxs-lookup"><span data-stu-id="810d3-114">:heavy_check_mark: SQLite works across platforms and architectures.</span></span>

<span data-ttu-id="810d3-115">Mehr über SQLite [erfahren Sie hier](https://sqlite.org/about.html).</span><span class="sxs-lookup"><span data-stu-id="810d3-115">You can read more about SQLite [here](https://sqlite.org/about.html).</span></span>

## <a name="choose-an-abstraction-layer"></a><span data-ttu-id="810d3-116">Auswahl einer Abstraktionsschicht</span><span class="sxs-lookup"><span data-stu-id="810d3-116">Choose an abstraction layer</span></span>

<span data-ttu-id="810d3-117">Wir empfehlen, dass Sie entweder Entity Framework Core oder die Open-Source-[SQLite-Bibliothek](https://github.com/aspnet/Microsoft.Data.Sqlite/) von Microsoft verwenden.</span><span class="sxs-lookup"><span data-stu-id="810d3-117">We recommend that you use either the Entity Framework Core or the open-source [SQLite library](https://github.com/aspnet/Microsoft.Data.Sqlite/) built by Microsoft.</span></span>

### <a name="entity-framework-core"></a><span data-ttu-id="810d3-118">Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="810d3-118">Entity Framework Core</span></span>

<span data-ttu-id="810d3-119">Entity Framework (EF) ist eine objektrelationale Zuordnung, die Ihnen über domänenspezifische Objekte die Verwendung relationaler Daten ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="810d3-119">Entity Framework (EF) is an object-relational mapper that you can use to work with relational data by using domain-specific objects.</span></span> <span data-ttu-id="810d3-120">Wenn Sie dieses Framework bereits für die Arbeit mit Daten in anderen .NET-Apps verwendet haben, können Sie diesen Code in eine UWP-App migrieren. Es funktioniert mit entsprechenden Änderungen an der Verbindungszeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="810d3-120">If you've already used this framework to work with data in other .NET apps, you can migrate that code to a UWP app and it will work with appropriate changes to the connection string.</span></span>

<span data-ttu-id="810d3-121">Weitere Informationen finden Sie unter [Erste Schritte mit EF Core auf der Universellen Windows-Plattform (UWP) mit einer neuen Datenbank](https://docs.microsoft.com/ef/core/get-started/uwp/getting-started).</span><span class="sxs-lookup"><span data-stu-id="810d3-121">To try it out, see [Getting started with EF Core on Universal Windows Platform (UWP) with a New Database](https://docs.microsoft.com/ef/core/get-started/uwp/getting-started).</span></span>

### <a name="sqlite-library"></a><span data-ttu-id="810d3-122">SQLite-Bibliothek</span><span class="sxs-lookup"><span data-stu-id="810d3-122">SQLite library</span></span>

<span data-ttu-id="810d3-123">Die [Microsoft.Data.Sqlite](https://docs.microsoft.com/dotnet/api/microsoft.data.sqlite?view=msdata-sqlite-2.0.0)-Bibliothek implementiert die Schnittstellen im [System.Data.Common](https://msdn.microsoft.com/library/system.data.common.aspx)-Namespace.</span><span class="sxs-lookup"><span data-stu-id="810d3-123">The [Microsoft.Data.Sqlite](https://docs.microsoft.com/dotnet/api/microsoft.data.sqlite?view=msdata-sqlite-2.0.0) library implements the interfaces in the [System.Data.Common](https://msdn.microsoft.com/library/system.data.common.aspx) namespace.</span></span> <span data-ttu-id="810d3-124">Microsoft pflegt diese Implementierungen aktiv und bietet einen intuitiven Wrapper für die native SQLite-API auf niedriger Ebene.</span><span class="sxs-lookup"><span data-stu-id="810d3-124">Microsoft actively maintains these implementations, and they provide an intuitive wrapper around the low-level native SQLite API.</span></span>

<span data-ttu-id="810d3-125">Der Rest dieses Leitfaden hilft Ihnen bei der Verwendung dieser Bibliothek.</span><span class="sxs-lookup"><span data-stu-id="810d3-125">The rest of this guide helps you to use this library.</span></span>

## <a name="set-up-your-solution-to-use-the-microsoftdatasqlite-library"></a><span data-ttu-id="810d3-126">Richten Sie Ihre Lösung für die Verwendung der Microsoft.Data.SQlite Bibliothek ein.</span><span class="sxs-lookup"><span data-stu-id="810d3-126">Set up your solution to use the Microsoft.Data.SQlite library</span></span>

<span data-ttu-id="810d3-127">Wir beginnen mit einem einfachen UWP-Projekt, fügen eine Klassenbibliothek hinzu und installieren dann die entsprechenden Nuget-Pakete.</span><span class="sxs-lookup"><span data-stu-id="810d3-127">We'll start with a basic UWP project, add a class library, and then install the appropriate Nuget packages.</span></span>

<span data-ttu-id="810d3-128">Die Art der Klassenbibliothek, die Sie zu Ihrer Lösung hinzufügen, und die spezifischen Pakete, die Sie installieren, hängen von der Mindestversion des Windows SDKs ab, auf das Ihre Anwendung abzielt.</span><span class="sxs-lookup"><span data-stu-id="810d3-128">The type of class library that you add to your solution,  and the specific packages that you install depends on the minimum version of the Windows SDK that your app targets.</span></span> <span data-ttu-id="810d3-129">Sie finden diese Informationen auf der Eigenschaftsseite Ihres UWP-Projekts.</span><span class="sxs-lookup"><span data-stu-id="810d3-129">You can find that information in the properties page of your UWP project.</span></span>

![Mindestversion des Windows SDKs](images/min-version.png)

<span data-ttu-id="810d3-131">Verwenden Sie einen der folgenden Abschnitte, abhängig von der Mindestversion des Windows SDKs, auf die Ihr UWP-Projekt abzielt.</span><span class="sxs-lookup"><span data-stu-id="810d3-131">Use one of the following sections depending on the minimum version of the Windows SDK that your UWP project targets.</span></span>

### <a name="the-minimum-version-of-your-project-does-not-target-the-fall-creators-update"></a><span data-ttu-id="810d3-132">Die Mindestversion Ihres Projekts zielt nicht auf das Fall Creators Update ab.</span><span class="sxs-lookup"><span data-stu-id="810d3-132">The minimum version of your project does not target the Fall Creators Update</span></span>

<span data-ttu-id="810d3-133">Wenn Sie Visual Studio 2015 verwenden, klicken Sie auf **Hilfe**->**Info über Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="810d3-133">If you're using Visual Studio 2015, click **Help**->**About Microsoft Visual Studio**.</span></span> <span data-ttu-id="810d3-134">Stellen Sie dann in der Liste der installierten Programme sicher, dass Sie den NuGet Package Manager Version **3.5** oder höher haben.</span><span class="sxs-lookup"><span data-stu-id="810d3-134">Then in the list of installed programs, make sure that you have NuGet package manager version of **3.5** or higher.</span></span> <span data-ttu-id="810d3-135">Wenn Ihre Versionsnummer niedriger ist, [installieren Sie hier](https://www.nuget.org/downloads) eine spätere Version von NuGet.</span><span class="sxs-lookup"><span data-stu-id="810d3-135">If your version number is lower than that, install a later version of NuGet [here](https://www.nuget.org/downloads).</span></span> <span data-ttu-id="810d3-136">Auf dieser Seite finden Sie unter der Überschrift **Visual Studio 2015** alle Versionen von Nuget.</span><span class="sxs-lookup"><span data-stu-id="810d3-136">On that page, you'll find all of the versions of Nuget listed beneath the **Visual Studio 2015** heading.</span></span>

<span data-ttu-id="810d3-137">Als nächstes fügen Sie Ihrer Lösung eine Klassenbibliothek hinzu.</span><span class="sxs-lookup"><span data-stu-id="810d3-137">Next, add class library to your solution.</span></span> <span data-ttu-id="810d3-138">Sie müssen keine Klassenbibliothek verwenden, um Ihren Datenzugriffscode zu enthalten, aber wir verwenden eines in unserem Beispiel.</span><span class="sxs-lookup"><span data-stu-id="810d3-138">You don't have to use a class library to contain your data access code, but we'll use one our example.</span></span> <span data-ttu-id="810d3-139">Wir nennen die Bibliothek **DataAccessLibrary** und die Klasse in der Bibliothek **DataAccess**.</span><span class="sxs-lookup"><span data-stu-id="810d3-139">We'll name the library **DataAccessLibrary** and we'll name the class in the library to **DataAccess**.</span></span>

![Klassenbibliothek](images/class-library.png)

<span data-ttu-id="810d3-141">Klicken Sie mit der rechten Maustaste auf die Lösung, und klicken Sie dann auf **NuGet-Pakete für Lösung verwalten**.</span><span class="sxs-lookup"><span data-stu-id="810d3-141">Right-click the solution, and then click **Manage NuGet Packages for Solution**.</span></span>

![NuGet-Pakete verwalten](images/manage-nuget.png)

<span data-ttu-id="810d3-143">Wenn Sie Visual Studio 2015 verwenden, wählen Sie die Registerkarte **Installiert** aus, und stellen Sie sicher, dass die Versionsnummer des **Microsoft.NETCore.UniversalWindowsPlatform**-Pakets **5.2.2** oder höher ist.</span><span class="sxs-lookup"><span data-stu-id="810d3-143">If you're using Visual Studio 2015, Choose the **Installed** tab, and make sure that the version number of the **Microsoft.NETCore.UniversalWindowsPlatform** package is **5.2.2** or higher.</span></span>

![Version von .NETCore](images/package-version.png)

<span data-ttu-id="810d3-145">Ist dies nicht der Fall, aktualisieren Sie das Paket auf eine neuere Version.</span><span class="sxs-lookup"><span data-stu-id="810d3-145">If it isn't, update the package to a newer version.</span></span>

<span data-ttu-id="810d3-146">Wählen Sie die Registerkarte **Durchsuchen** aus und suchen Sie nach dem Paket **Microsoft.Data.SQLite**.</span><span class="sxs-lookup"><span data-stu-id="810d3-146">Choose the **Browse** tab, and search for the **Microsoft.Data.SQLite** package.</span></span> <span data-ttu-id="810d3-147">Installieren Sie Version **1.1.1** (oder niedriger) dieses Pakets.</span><span class="sxs-lookup"><span data-stu-id="810d3-147">Install version **1.1.1** (or lower) of that package.</span></span>

![SQLite-Paket](images/sqlite-package.png)

<span data-ttu-id="810d3-149">Gehen Sie zum Abschnitt [Hinzufügen und Abrufen von Daten in einer SQLite-Datenbank](#use-data) in diesem Handbuch.</span><span class="sxs-lookup"><span data-stu-id="810d3-149">Move onto the [Add and retrieve data in a SQLite database](#use-data) section of this guide.</span></span>

### <a name="the-minimum-version-of-your-project-targets-the-fall-creators-update"></a><span data-ttu-id="810d3-150">Die Mindestversion Ihres Projekts zielt auf das Fall Creators Update.</span><span class="sxs-lookup"><span data-stu-id="810d3-150">The minimum version of your project targets the Fall Creators Update</span></span>

<span data-ttu-id="810d3-151">Es gibt eine Reihe von Vorteilen, um die Mindestversion Ihres UWP-Projekts auf das Fall Creators Update zu erhöhen.</span><span class="sxs-lookup"><span data-stu-id="810d3-151">There's a couple of benefits to raising the minimum version of your UWP project to the Fall Creators update.</span></span>

<span data-ttu-id="810d3-152">Zunächst einmal können Sie .NET Standard 2.0-Bibliotheken anstelle von regulären Klassenbibliotheken verwenden.</span><span class="sxs-lookup"><span data-stu-id="810d3-152">First off, you can use .NET Standard 2.0 libraries instead of regular class libraries.</span></span> <span data-ttu-id="810d3-153">Das bedeutet, dass Sie Ihren Datenzugriffscode mit jeder anderen .NET-basierten Anwendung wie WPF, Windows Forms, Android, iOS oder ASP.NET teilen können.</span><span class="sxs-lookup"><span data-stu-id="810d3-153">That means that you can share your data access code with any other .NET-based app such as a WPF, Windows Forms, Android, iOS, or ASP.NET app.</span></span>

<span data-ttu-id="810d3-154">Zweitens hat Ihre App keine Paket-SQLite-Bibliotheken.</span><span class="sxs-lookup"><span data-stu-id="810d3-154">Secondly, your app does not have package SQLite libraries.</span></span> <span data-ttu-id="810d3-155">Stattdessen kann Ihre App die Version von SQLite verwenden, die mit Windows installiert wird.</span><span class="sxs-lookup"><span data-stu-id="810d3-155">Instead, your app can use the version of SQLite that comes installed with Windows.</span></span> <span data-ttu-id="810d3-156">Das hilft Ihnen in mehrfacher Hinsicht.</span><span class="sxs-lookup"><span data-stu-id="810d3-156">This helps you in a few ways.</span></span>

<span data-ttu-id="810d3-157">:heavy_check_mark: Reduziert die Größe Ihrer App, da Sie die SQLite-Binärdatei nicht herunterladen und dann als Teil Ihrer App verpacken müssen.</span><span class="sxs-lookup"><span data-stu-id="810d3-157">:heavy_check_mark: Reduces the size of your application because you don't have to download the SQLite binary, and then package it as part of your application.</span></span>

<span data-ttu-id="810d3-158">:heavy_check_mark: Verhindert, dass Sie eine neue Version Ihrer App an Benutzer weitergeben müssen, falls SQLite kritische Fehlerbehebungen und Sicherheitslücken in SQLite veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="810d3-158">:heavy_check_mark: Prevents you from having to push a new version of your app to users in the event that SQLite publishes critical fixes to bugs and security vulnerabilities in SQLite.</span></span> <span data-ttu-id="810d3-159">Die Windows-Version von SQLite wird von Microsoft in Abstimmung mit SQLite.org gepflegt.</span><span class="sxs-lookup"><span data-stu-id="810d3-159">The Windows version of SQLite is maintained by Microsoft in coordination with SQLite.org.</span></span>

<span data-ttu-id="810d3-160">:heavy_check_mark: Die Ladezeit der App kann kürzer sein, da die SDK-Version von SQLite wahrscheinlich bereits in den Speicher geladen wird.</span><span class="sxs-lookup"><span data-stu-id="810d3-160">:heavy_check_mark: App load time has the potential to be faster because most likely, the SDK version of SQLite will already be loaded into memory.</span></span>

<span data-ttu-id="810d3-161">Beginnen wir mit dem Hinzufügen einer .NET Standard 2.0-Klassenbibliothek zu Ihrer Lösung.</span><span class="sxs-lookup"><span data-stu-id="810d3-161">Lets start by adding a .NET Standard 2.0 class library to your solution.</span></span> <span data-ttu-id="810d3-162">Es ist nicht notwendig, dass Sie eine Klassenbibliothek verwenden, um Ihren Datenzugriffscode zu enthalten, aber wir verwenden eine in unserem Beispiel.</span><span class="sxs-lookup"><span data-stu-id="810d3-162">It's not necessary that you use a class library to contain your data access code, but we'll use one our example.</span></span> <span data-ttu-id="810d3-163">Wir nennen die Bibliothek **DataAccessLibrary** und die Klasse in der Bibliothek **DataAccess**.</span><span class="sxs-lookup"><span data-stu-id="810d3-163">We'll name the library **DataAccessLibrary** and we'll name the class in the library to **DataAccess**.</span></span>

![Klassenbibliothek](images/dot-net-standard.png)

<span data-ttu-id="810d3-165">Klicken Sie mit der rechten Maustaste auf die Lösung, und klicken Sie dann auf **NuGet-Pakete für Lösung verwalten**.</span><span class="sxs-lookup"><span data-stu-id="810d3-165">Right-click the solution, and then click **Manage NuGet Packages for Solution**.</span></span>

![NuGet-Pakete verwalten](images/manage-nuget-2.png)

<span data-ttu-id="810d3-167">An diesem Punkt haben Sie die Wahl.</span><span class="sxs-lookup"><span data-stu-id="810d3-167">At this point, you have a choice.</span></span> <span data-ttu-id="810d3-168">Sie können die Version von SQLite verwenden, die in Windows enthalten ist, oder wenn Sie einen Grund haben, eine bestimmte Version von SQLite zu verwenden, können Sie die SQLite-Bibliothek in Ihr Paket aufnehmen.</span><span class="sxs-lookup"><span data-stu-id="810d3-168">You can use the version of SQLite that is included with Windows or if you have some reason to use a specific version of SQLite, you can include the SQLite library in your package.</span></span>

<span data-ttu-id="810d3-169">Beginnen wir damit, wie Sie die Version von SQLite verwenden, die in Windows enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="810d3-169">Let's start with how you use the version of SQLite that included with Windows.</span></span>

#### <a name="to-use-the-version-of-sqlite-that-is-installed-with-windows"></a><span data-ttu-id="810d3-170">So verwenden Sie die unter Windows installierte Version von SQLite</span><span class="sxs-lookup"><span data-stu-id="810d3-170">To use the version of SQLite that is installed with Windows</span></span>

<span data-ttu-id="810d3-171">Wählen Sie die Registerkarte **Durchsuchen** und suchen Sie nach dem **Microsoft.Data.SQLite.core**-Paket, und installieren Sie es dann.</span><span class="sxs-lookup"><span data-stu-id="810d3-171">Choose the **Browse** tab, and search for the **Microsoft.Data.SQLite.core** package, and then install it.</span></span>

![SQLite Core-Paket](images/sqlite-core-package.png)

<span data-ttu-id="810d3-173">Suchen Sie nach dem Paket **SQLitePCLRaw.bundle_winsqlite3** und installieren Sie es dann nur im UWP-Projekt Ihrer Lösung.</span><span class="sxs-lookup"><span data-stu-id="810d3-173">Search for the **SQLitePCLRaw.bundle_winsqlite3** package, and then install it only to the UWP project in your solution.</span></span>

![SQLite PCL Raw-Paket](images/sqlite-raw-package.png)

#### <a name="to-include-sqlite-with-your-app"></a><span data-ttu-id="810d3-175">So binden Sie SQLite in Ihre App ein</span><span class="sxs-lookup"><span data-stu-id="810d3-175">To include SQLite with your app</span></span>

<span data-ttu-id="810d3-176">Sie müssen dies nicht tun.</span><span class="sxs-lookup"><span data-stu-id="810d3-176">You don't have to do this.</span></span> <span data-ttu-id="810d3-177">Wenn Sie jedoch einen Grund haben, eine bestimmte Version von SQLite in Ihre App aufzunehmen, wählen Sie die Registerkarte **Durchsuchen** aus und suchen Sie nach dem Paket **Microsoft.Data.SQLite**.</span><span class="sxs-lookup"><span data-stu-id="810d3-177">But if you have a reason to include a specific version of SQLite with your app, choose the **Browse** tab, and search for the **Microsoft.Data.SQLite** package.</span></span> <span data-ttu-id="810d3-178">Installieren Sie Version **2.0** (oder niedriger) dieses Pakets.</span><span class="sxs-lookup"><span data-stu-id="810d3-178">Install version **2.0** (or lower) of that package.</span></span>

![SQLite-Paket](images/sqlite-package-v2.png)

<a id="use-data" />

## <a name="add-and-retrieve-data-in-a-sqlite-database"></a><span data-ttu-id="810d3-180">Hinzufügen und Abrufen von Daten in einer SQLite-Datenbank</span><span class="sxs-lookup"><span data-stu-id="810d3-180">Add and retrieve data in a SQLite database</span></span>

<span data-ttu-id="810d3-181">Wir werden die folgenden Dinge durchführen:</span><span class="sxs-lookup"><span data-stu-id="810d3-181">We'll do these things:</span></span>

<span data-ttu-id="810d3-182">:one: Bereiten Sie die Datenzugriffsklasse vor.</span><span class="sxs-lookup"><span data-stu-id="810d3-182">:one: Prepare the data access class.</span></span>

<span data-ttu-id="810d3-183">:two: Initialisieren Sie die SQLite-Datenbank.</span><span class="sxs-lookup"><span data-stu-id="810d3-183">:two: Initialize the SQLite database.</span></span>

<span data-ttu-id="810d3-184">:three: Fügen Sie Daten in die SQLite-Datenbank ein.</span><span class="sxs-lookup"><span data-stu-id="810d3-184">:three: Insert data into the SQLite database.</span></span>

<span data-ttu-id="810d3-185">:four: Rufen Sie Daten aus der SQLite-Datenbank ab.</span><span class="sxs-lookup"><span data-stu-id="810d3-185">:four: Retrieve data from the SQLite database.</span></span>

<span data-ttu-id="810d3-186">:five: Fügen Sie eine einfache Benutzeroberfläche hinzu.</span><span class="sxs-lookup"><span data-stu-id="810d3-186">:five: Add a basic user interface.</span></span>

### <a name="prepare-the-data-access-class"></a><span data-ttu-id="810d3-187">Vorbereitung der Datenzugriffsklasse</span><span class="sxs-lookup"><span data-stu-id="810d3-187">Prepare the data access class</span></span>

<span data-ttu-id="810d3-188">Fügen Sie aus Ihrem UWP-Projekt einen Verweis auf das **DataAccessLibrary**-Projekt in Ihrer Lösung hinzu.</span><span class="sxs-lookup"><span data-stu-id="810d3-188">From your UWP project, add a reference to the **DataAccessLibrary** project in your solution.</span></span>

![Datenzugriffsklassenbibliothek](images/ref-class-library.png)

<span data-ttu-id="810d3-190">Fügen Sie die folgende ``using``-Anweisung zu den Dateien **App.xaml.cs** und **MainPage.xaml.cs** in Ihrem UWP-Projekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="810d3-190">Add the following ``using`` statement to the **App.xaml.cs** and **MainPage.xaml.cs** files in your UWP project.</span></span>

```csharp
using DataAccessLibrary;
```

<span data-ttu-id="810d3-191">Öffnen Sie die **DataAccess**-Klasse in Ihrer **DataAccessLibrary**-Lösung, und deklarieren Sie diese Klasse als statisch.</span><span class="sxs-lookup"><span data-stu-id="810d3-191">Open the **DataAccess** class in your **DataAccessLibrary** solution and make that class static.</span></span>

>[!NOTE]
><span data-ttu-id="810d3-192">Unser Beispiel platziert den Datenzugriffscode in einer statischen Klasse. Dies ist jedoch nur eine Designentscheidung und völlig optional.</span><span class="sxs-lookup"><span data-stu-id="810d3-192">While our example will place data access code in a static class, it's just a design choice and is completely optional.</span></span>

```csharp
namespace DataAccessLibrary
{
    public static class DataAccess
    {

    }
}

```

<span data-ttu-id="810d3-193">Fügen Sie die folgende Anweisung am Anfang dieser Datei ein.</span><span class="sxs-lookup"><span data-stu-id="810d3-193">Add the following using statement to the top of this file.</span></span>

```csharp
using Microsoft.Data.Sqlite;
```

<a id="initialize" />

### <a name="initialize-the-sqlite-database"></a><span data-ttu-id="810d3-194">Initialisierung der SQLite-Datenbank</span><span class="sxs-lookup"><span data-stu-id="810d3-194">Initialize the SQLite database</span></span>

<span data-ttu-id="810d3-195">Fügen Sie der **DataAccess**-Klasse eine Methode hinzu, die die SQLite-Datenbank initialisiert.</span><span class="sxs-lookup"><span data-stu-id="810d3-195">Add a method to the **DataAccess** class that initializes the SQLite database.</span></span>

```csharp
public static void InitializeDatabase()
{
    using (SqliteConnection db =
        new SqliteConnection("Filename=sqliteSample.db"))
    {
        db.Open();

        String tableCommand = "CREATE TABLE IF NOT " +
            "EXISTS MyTable (Primary_Key INTEGER PRIMARY KEY, " +
            "Text_Entry NVARCHAR(2048) NULL)";

        SqliteCommand createTable = new SqliteCommand(tableCommand, db);

        createTable.ExecuteReader();
    }
}
```

<span data-ttu-id="810d3-196">Dieser Code erstellt die SQLite-Datenbank und speichert sie im lokalen Datenspeicher der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="810d3-196">This code creates the SQLite database and stores it in the application's local data store.</span></span>

<span data-ttu-id="810d3-197">In diesem Beispiel benennen wir die Datenbank als ``sqlliteSample.db``. Sie können aber jeden beliebigen Namen verwenden, solange Sie diesen Namen in allen [SqliteConnection](https://docs.microsoft.com/dotnet/api/microsoft.data.sqlite.sqliteconnection?view=msdata-sqlite-2.0.0)-Objekten verwenden.</span><span class="sxs-lookup"><span data-stu-id="810d3-197">In this example, we name the database ``sqlliteSample.db`` but you can use whatever name you want as long as you use that name in all [SqliteConnection](https://docs.microsoft.com/dotnet/api/microsoft.data.sqlite.sqliteconnection?view=msdata-sqlite-2.0.0) objects that you instantiate.</span></span>

<span data-ttu-id="810d3-198">Rufen Sie im Konstruktor der Datei **App.xaml.cs** Ihres UWP-Projekts die ``InitializeDatabase``-Methode der **DataAccess**-Klasse auf.</span><span class="sxs-lookup"><span data-stu-id="810d3-198">In the constructor of the **App.xaml.cs** file of your UWP project, call the ``InitializeDatabase`` method of the **DataAccess** class.</span></span>

```csharp
public App()
{
    this.InitializeComponent();
    this.Suspending += OnSuspending;

    DataAccess.InitializeDatabase();

}
```

<a id="insert" />

### <a name="insert-data-into-the-sqlite-database"></a><span data-ttu-id="810d3-199">Daten in die SQLite-Datenbank einfügen</span><span class="sxs-lookup"><span data-stu-id="810d3-199">Insert data into the SQLite database</span></span>

<span data-ttu-id="810d3-200">Fügen Sie der **DataAccess**-Klasse eine Methode hinzu, die Daten in die SQLite-Datenbank einfügt.</span><span class="sxs-lookup"><span data-stu-id="810d3-200">Add a method to the **DataAccess** class that inserts data into the SQLite database.</span></span> <span data-ttu-id="810d3-201">Dieser Code verwendet Parameter in der Abfrage, um SQL-Injection-Angriffe zu verhindern.</span><span class="sxs-lookup"><span data-stu-id="810d3-201">This code uses parameters in the query to prevent SQL injection attacks.</span></span>

```csharp
public static void AddData(string inputText)
{
    using (SqliteConnection db =
        new SqliteConnection("Filename=sqliteSample.db"))
    {
        db.Open();

        SqliteCommand insertCommand = new SqliteCommand();
        insertCommand.Connection = db;

        // Use parameterized query to prevent SQL injection attacks
        insertCommand.CommandText = "INSERT INTO MyTable VALUES (NULL, @Entry);";
        insertCommand.Parameters.AddWithValue("@Entry", inputText);

        insertCommand.ExecuteReader();

        db.Close();
    }

}
```

<a id="retrieve" />

### <a name="retrieve-data-from-the-sqlite-database"></a><span data-ttu-id="810d3-202">Abrufen von Daten aus der SQLite-Datenbank</span><span class="sxs-lookup"><span data-stu-id="810d3-202">Retrieve data from the SQLite database</span></span>

<span data-ttu-id="810d3-203">Fügen Sie eine Methode hinzu, die Datenzeilen aus einer SQLite-Datenbank abruft.</span><span class="sxs-lookup"><span data-stu-id="810d3-203">Add a method that gets rows of data from a SQLite database.</span></span>

```csharp
public static List<String> GetData()
{
    List<String> entries = new List<string>();

    using (SqliteConnection db =
        new SqliteConnection("Filename=sqliteSample.db"))
    {
        db.Open();

        SqliteCommand selectCommand = new SqliteCommand
            ("SELECT Text_Entry from MyTable", db);

        SqliteDataReader query = selectCommand.ExecuteReader();

        while (query.Read())
        {
            entries.Add(query.GetString(0));
        }

        db.Close();
    }

    return entries;
}
```

<span data-ttu-id="810d3-204">Die [Read](https://docs.microsoft.com/dotnet/api/microsoft.data.sqlite.sqlitedatareader.read?view=msdata-sqlite-2.0.0#Microsoft_Data_Sqlite_SqliteDataReader_Read)-Methode durchläuft die Zeilen der zurückgegebenen Daten.</span><span class="sxs-lookup"><span data-stu-id="810d3-204">The [Read](https://docs.microsoft.com/dotnet/api/microsoft.data.sqlite.sqlitedatareader.read?view=msdata-sqlite-2.0.0#Microsoft_Data_Sqlite_SqliteDataReader_Read) method advances through the rows of returned data.</span></span> <span data-ttu-id="810d3-205">Sie gibt **true** zurück, wenn noch Zeilen übrig sind, andernfalls **false**.</span><span class="sxs-lookup"><span data-stu-id="810d3-205">It returns **true** if there are rows left, otherwise it returns **false**.</span></span>

<span data-ttu-id="810d3-206">Die Methode [GetString](https://docs.microsoft.com/dotnet/api/microsoft.data.sqlite.sqlitedatareader.getstring?view=msdata-sqlite-2.0.0#Microsoft_Data_Sqlite_SqliteDataReader_GetString_System_Int32_) gibt den Wert der angegebenen Spalte als String zurück.</span><span class="sxs-lookup"><span data-stu-id="810d3-206">The [GetString](https://docs.microsoft.com/dotnet/api/microsoft.data.sqlite.sqlitedatareader.getstring?view=msdata-sqlite-2.0.0#Microsoft_Data_Sqlite_SqliteDataReader_GetString_System_Int32_) method returns the value of the specified column as a string.</span></span> <span data-ttu-id="810d3-207">Sie akzeptiert einen Integer-Wert, der die Null-basierte Spalten-Ordinalzahl der gewünschten Daten darstellt.</span><span class="sxs-lookup"><span data-stu-id="810d3-207">It accepts an integer value that represents the zero-based column ordinal of the data that you want.</span></span> <span data-ttu-id="810d3-208">Sie können Methoden wie [GetDataTime](https://docs.microsoft.com/dotnet/api/microsoft.data.sqlite.sqlitedatareader.getdatetime?view=msdata-sqlite-2.0.0#Microsoft_Data_Sqlite_SqliteDataReader_GetDateTime_System_Int32_) und [GetBoolean](https://docs.microsoft.com/dotnet/api/microsoft.data.sqlite.sqlitedatareader.getboolean?view=msdata-sqlite-2.0.0#Microsoft_Data_Sqlite_SqliteDataReader_GetBoolean_System_Int32_) verwenden.</span><span class="sxs-lookup"><span data-stu-id="810d3-208">You can use similar methods such as [GetDataTime](https://docs.microsoft.com/dotnet/api/microsoft.data.sqlite.sqlitedatareader.getdatetime?view=msdata-sqlite-2.0.0#Microsoft_Data_Sqlite_SqliteDataReader_GetDateTime_System_Int32_) and [GetBoolean](https://docs.microsoft.com/dotnet/api/microsoft.data.sqlite.sqlitedatareader.getboolean?view=msdata-sqlite-2.0.0#Microsoft_Data_Sqlite_SqliteDataReader_GetBoolean_System_Int32_).</span></span> <span data-ttu-id="810d3-209">Wählen Sie eine Methode für den Datentyp der Spalte aus.</span><span class="sxs-lookup"><span data-stu-id="810d3-209">Choose a method based on what type of data the column contains.</span></span>

<span data-ttu-id="810d3-210">Der Ordinalparameter ist in diesem Beispiel nicht so wichtig, da wir alle Einträge in einer einzigen Spalte auswählen.</span><span class="sxs-lookup"><span data-stu-id="810d3-210">The ordinal parameter isn't as important in this example because we are selecting all of the entries in a single column.</span></span> <span data-ttu-id="810d3-211">Wenn jedoch mehrere Spalten Teil Ihrer Abfrage sind, verwenden Sie den Ordinalwert, um die Spalte zu erhalten, aus der Sie Daten ziehen möchten.</span><span class="sxs-lookup"><span data-stu-id="810d3-211">However, if multiple columns are part of your query, use the ordinal value to obtain the column you want to pull data from.</span></span>

## <a name="add-a-basic-user-interface"></a><span data-ttu-id="810d3-212">Hinzufügen einer einfachen Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="810d3-212">Add a basic user interface</span></span>

<span data-ttu-id="810d3-213">Fügen Sie in der Datei **MainPage.xaml** des UWP-Projekts den folgende XAML-Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="810d3-213">In the **MainPage.xaml** file of the UWP project, add the following XAML.</span></span>

```xml
<Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <StackPanel>
        <TextBox Name="Input_Box"></TextBox>
        <Button Click="AddData">Add</Button>
        <ListView Name="Output">
            <ListView.ItemTemplate>
                <DataTemplate>
                    <TextBlock Text="{Binding}"/>
                </DataTemplate>
            </ListView.ItemTemplate>
        </ListView>
    </StackPanel>
</Grid>
```

<span data-ttu-id="810d3-214">Diese grundlegende Benutzeroberfläche bietet dem Benutzer eine ``TextBox``, über die er eine Zeichenfolge eingeben kann, die wir der SQLite-Datenbank hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="810d3-214">This basic user interface gives the user a ``TextBox`` that they can use to type a string that we'll add to the SQLite database.</span></span> <span data-ttu-id="810d3-215">Wir verbinden den ``Button`` in dieser Benutzeroberfläche mit einem Event-Handler, der Daten aus der SQLite-Datenbank abruft und diese Daten dann in der ``ListView`` anzeigt.</span><span class="sxs-lookup"><span data-stu-id="810d3-215">We'll connect the ``Button`` in this UI to an event handler that will retrieve data from the SQLite database and then show that data in the ``ListView``.</span></span>

<span data-ttu-id="810d3-216">Fügen Sie in der Datei **MainPage.xaml.cs** den folgenden Handler hinzu.</span><span class="sxs-lookup"><span data-stu-id="810d3-216">In the **MainPage.xaml.cs** file, add the following handler.</span></span> <span data-ttu-id="810d3-217">Dies ist die Methode, die wir mit dem ``Click``-Ereignis des ``Button`` im UI zugeordnet haben.</span><span class="sxs-lookup"><span data-stu-id="810d3-217">This is the method that we associated with the ``Click`` event of the ``Button`` in the UI.</span></span>

```csharp
private void AddData(object sender, RoutedEventArgs e)
{
    DataAccess.AddData(Input_Box.Text);

    Output.ItemsSource = DataAccess.GetData();
}
```

<span data-ttu-id="810d3-218">Das war's.</span><span class="sxs-lookup"><span data-stu-id="810d3-218">That's it.</span></span> <span data-ttu-id="810d3-219">Erkunden Sie [Microsoft.Data.Sqlite](https://docs.microsoft.com/dotnet/api/microsoft.data.sqlite?view=msdata-sqlite-2.0.0), um zu sehen, was Sie sonst noch mit Ihrer SQLite-Datenbank machen können.</span><span class="sxs-lookup"><span data-stu-id="810d3-219">Explore the [Microsoft.Data.Sqlite](https://docs.microsoft.com/dotnet/api/microsoft.data.sqlite?view=msdata-sqlite-2.0.0) to see what other things you can do with your SQLite database.</span></span> <span data-ttu-id="810d3-220">Sehen Sie sich die folgenden Links an, um mehr über andere Möglichkeiten der Datenverwendung in Ihrer UWP-App zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="810d3-220">Check out the links below to learn about other ways to use data in your UWP app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="810d3-221">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="810d3-221">Next steps</span></span>

**<span data-ttu-id="810d3-222">Verbinden Sie Ihre App direkt mit einer SQL Server-Datenbank.</span><span class="sxs-lookup"><span data-stu-id="810d3-222">Connect your app directly to a SQL Server database</span></span>**

<span data-ttu-id="810d3-223">Mehr unter [Verwenden einer SQL Server-Datenbank in einer UWP-App](sql-server-databases.md).</span><span class="sxs-lookup"><span data-stu-id="810d3-223">See [Use a SQL Server database in a UWP app](sql-server-databases.md).</span></span>

**<span data-ttu-id="810d3-224">Nutzen Sie Code zwischen verschiedenen Apps auf verschiedenen Plattformen</span><span class="sxs-lookup"><span data-stu-id="810d3-224">Share code between different apps across different platforms</span></span>**

<span data-ttu-id="810d3-225">Weitere Informationen finden Sie unter [Teilen von Code zwischen einer Desktop-App und einer UWP-App](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-migrate)</span><span class="sxs-lookup"><span data-stu-id="810d3-225">See [Share code between desktop and UWP](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-migrate).</span></span>

**<span data-ttu-id="810d3-226">Hinzufügen von Master-Detailseiten mit Azure SQL-Backends</span><span class="sxs-lookup"><span data-stu-id="810d3-226">Add master detail pages with Azure SQL back ends</span></span>**

<span data-ttu-id="810d3-227">Mehr unter [Beispiel einer Kundenauftragsdatenbank.](https://github.com/Microsoft/Windows-appsample-customers-orders-database)</span><span class="sxs-lookup"><span data-stu-id="810d3-227">See [Customer Orders Database sample](https://github.com/Microsoft/Windows-appsample-customers-orders-database).</span></span>
