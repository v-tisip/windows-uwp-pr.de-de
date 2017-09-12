---
author: normesta
ms.assetid: 5A47301A-2291-4FC8-8BA7-55DB2A5C653F
title: SQLite-Datenbanken
description: "SQLite ist ein eingebettetes Datenbankmodul ohne Server. In diesem Artikel wird erläutert, wie die im SDK enthaltene SQLite-Bibliothek verwendet wird und wie Ihre eigene SQLite-Bibliothek in einer universellen Windows-App verpackt oder aus der Quelle erstellt wird."
ms.author: normesta
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP, SQLite, Datenbank
ms.openlocfilehash: 3b075a6c55373e91e9f12fb5359f5aa4a985f602
ms.sourcegitcommit: 378382419f1fda4e4df76ffa9c8cea753d271e6a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
# <a name="sqlite-databases"></a><span data-ttu-id="09c86-105">SQLite-Datenbanken</span><span class="sxs-lookup"><span data-stu-id="09c86-105">SQLite databases</span></span>

<span data-ttu-id="09c86-106">\[ Aktualisiert für UWP-Apps unter Windows10.</span><span class="sxs-lookup"><span data-stu-id="09c86-106">\[ Updated for UWP apps on Windows 10.</span></span> <span data-ttu-id="09c86-107">Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span><span class="sxs-lookup"><span data-stu-id="09c86-107">For Windows 8.x articles, see the [archive](http://go.microsoft.com/fwlink/p/?linkid=619132) \]</span></span>


<span data-ttu-id="09c86-108">SQLite ist ein eingebettetes Datenbankmodul ohne Server.</span><span class="sxs-lookup"><span data-stu-id="09c86-108">SQLite is a server-less, embedded database engine.</span></span> <span data-ttu-id="09c86-109">In diesem Artikel wird erläutert, wie die im SDK enthaltene SQLite-Bibliothek verwendet wird und wie Ihre eigene SQLite-Bibliothek in einer universellen Windows-App verpackt oder aus der Quelle erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="09c86-109">This article explains how to use the SQLite library included in the SDK, package your own SQLite library in a Universal Windows app, or build it from the source.</span></span>

## <a name="what-sqlite-is-and-when-to-use-it"></a><span data-ttu-id="09c86-110">Was ist SQLite und wann wird es verwendet?</span><span class="sxs-lookup"><span data-stu-id="09c86-110">What SQLite is and when to use it</span></span>

<span data-ttu-id="09c86-111">SQLite ist eine eingebettete Open-Source-Datenbank ohne Server.</span><span class="sxs-lookup"><span data-stu-id="09c86-111">SQLite is an open source, embedded, server-less database.</span></span> <span data-ttu-id="09c86-112">In den letzten Jahren hat es sich zur dominanten geräteseitigen Technologie für die Speicherung von Daten auf vielen Plattformen und Geräten entwickelt.</span><span class="sxs-lookup"><span data-stu-id="09c86-112">Over the years it has emerged as the dominant device side technology for data storage on many platforms and devices.</span></span> <span data-ttu-id="09c86-113">Universelle Windows-Plattform (UWP) unterstützt und empfiehlt SQLite für den lokalen Speicher in allen Windows 10-Gerätefamilien.</span><span class="sxs-lookup"><span data-stu-id="09c86-113">Universal Windows Platform (UWP) supports and recommends SQLite for local storage across all Windows 10 device families.</span></span>

<span data-ttu-id="09c86-114">SQLite eignet sich am besten für Telefon-Apps, eingebettete Apps für Windows 10 IoT Core (IoT Core) und als Cache für RDBS-Daten (Relations Database Server) von Unternehmen.</span><span class="sxs-lookup"><span data-stu-id="09c86-114">SQLite is best suited for phone apps, embedded applications for Windows 10 IoT Core (IoT Core), and as a cache for enterprise relations database server (RDBS) data.</span></span> <span data-ttu-id="09c86-115">Es erfüllt die meisten Anforderungen an den lokalen Datenzugriff, sofern keine umfangreichen gleichzeitigen Schreibvorgänge oder BigData-Szenarios vorliegen, was für die meisten Apps aber unwahrscheinlich ist.</span><span class="sxs-lookup"><span data-stu-id="09c86-115">It will satisfy most local data access needs unless they entail heavy concurrent writes, or a big data scale—scenarios unlikely for most apps.</span></span>

<span data-ttu-id="09c86-116">In Anwendungen für Medienwiedergabe und Spiele kann SQLite auch als Dateiformat zum Speichern von Katalogen oder anderen Ressourcen verwendet werden, zum Beispiel für die Level eines Spiels, die unverändert von einem Webserver heruntergeladen werden können.</span><span class="sxs-lookup"><span data-stu-id="09c86-116">In media playback and gaming applications, SQLite can also be used as a file format to store catalogues or other assets, such as levels of a game, that can be downloaded as-is from a web server.</span></span>

## <a name="adding-sqlite-to-a-uwp-app-project"></a><span data-ttu-id="09c86-117">Hinzufügen von SQLite zu einem UWP-App-Projekt</span><span class="sxs-lookup"><span data-stu-id="09c86-117">Adding SQLite to a UWP app project</span></span>

<span data-ttu-id="09c86-118">Es gibt drei Möglichkeiten zum Hinzufügen von SQLite zu einem UWP-Projekt.</span><span class="sxs-lookup"><span data-stu-id="09c86-118">There are three ways of adding SQLite to a UWP project.</span></span>

1.  [<span data-ttu-id="09c86-119">Verwenden des SDK SQLite</span><span class="sxs-lookup"><span data-stu-id="09c86-119">Using the SDK SQLite</span></span>](#using-the-sdk-sqlite)
2.  [<span data-ttu-id="09c86-120">Einschließen von SQLite in das App-Paket</span><span class="sxs-lookup"><span data-stu-id="09c86-120">Including SQLite in the App Package</span></span>](#including-sqlite-in-the-app-package)
3.  [<span data-ttu-id="09c86-121">Erstellen von SQLite aus der Quelle in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="09c86-121">Building SQLite from source in Visual Studio</span></span>](#building-sqlite-from-source-in-visual-studio)

### <a name="using-the-sdk-sqlite"></a><span data-ttu-id="09c86-122">Verwenden des SDK SQLite</span><span class="sxs-lookup"><span data-stu-id="09c86-122">Using the SDK SQLite</span></span>

<span data-ttu-id="09c86-123">Sie können die im UWP-SDK enthaltene SQLite-Bibliothek verwenden, um die Größe des Anwendungspakets zu reduzieren, und sich für die regelmäßige Aktualisierung der Bibliothek auf die Plattform verlassen.</span><span class="sxs-lookup"><span data-stu-id="09c86-123">You may wish to use the SQLite library included in the UWP SDK to reduce the size of your application package, and rely on the platform to update the library periodically.</span></span> <span data-ttu-id="09c86-124">Mit dem SDK SQLite können Sie auch Leistungsvorteile erzielen, z. B. kürzere Startzeiten, sofern die SQLite-Bibliothek mit großer Wahrscheinlichkeit bereits in den Arbeitsspeicher für die Verwendung durch Systemkomponenten geladen wurde.</span><span class="sxs-lookup"><span data-stu-id="09c86-124">Using the SDK SQLite might also lead to performance advantages such as faster launch times given the SQLite library is highly likely to already be loaded in memory for use by system components.</span></span>

<span data-ttu-id="09c86-125">Um auf das SDK SQLite zu verweisen, schließen Sie den folgenden Header in Ihrem Projekt ein.</span><span class="sxs-lookup"><span data-stu-id="09c86-125">To reference the SDK SQLite, include the following header in your project.</span></span> <span data-ttu-id="09c86-126">Der Header enthält auch die Version von SQLite, die von der Plattform unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="09c86-126">The header also contains the version of SQLite supported in the platform.</span></span>

`#include <winsqlite/winsqlite3.h>`

<span data-ttu-id="09c86-127">Konfigurieren Sie das Projekt zur Verknüpfung mit winsqlite3.lib.</span><span class="sxs-lookup"><span data-stu-id="09c86-127">Configure the project to link to winsqlite3.lib.</span></span> <span data-ttu-id="09c86-128">Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften** &gt; **Linker** &gt; **Eingabe** aus. Fügen Sie dann winsqlite3.lib zu **Zusätzliche Abhängigkeiten** hinzu.</span><span class="sxs-lookup"><span data-stu-id="09c86-128">In **Solution Explorer**, right-click your project and select **Properties** &gt; **Linker** &gt; **Input**, then add winsqlite3.lib to **Additional Dependencies**.</span></span>

### <a name="including-sqlite-in-the-app-package"></a><span data-ttu-id="09c86-129">Einschließen von SQLite in das App-Paket</span><span class="sxs-lookup"><span data-stu-id="09c86-129">Including SQLite in the App Package</span></span>

<span data-ttu-id="09c86-130">Manchmal möchten Sie Ihre eigene Bibliothek möglicherweise packen, anstatt die SDK-Version zu verwenden, wenn Sie z. B. eine bestimmte Version für die plattformübergreifenden Clients verwenden möchten, die sich von der im SDK enthaltenen Version von SQLite unterscheidet.</span><span class="sxs-lookup"><span data-stu-id="09c86-130">Sometimes, you might wish to package your own library instead of using the SDK version, for example, you might wish to use a particular version of it in your cross-platform clients that is different from the version of SQLite included in the SDK.</span></span>

<span data-ttu-id="09c86-131">Installieren Sie die SQLite-Bibliothek auf der Visual Studio-Erweiterung der universellen Windows-Plattform über SQLite.org oder über das Tool für Erweiterungen und Updates.</span><span class="sxs-lookup"><span data-stu-id="09c86-131">Install the SQLite library on the Universal Windows Platform Visual Studio extension available from SQLite.org, or through the Extensions and Updates tool.</span></span>

![Bildschirm „Erweiterungen und Updates“](./images/extensions-and-updates.png)

<span data-ttu-id="09c86-133">Sobald die Erweiterung installiert ist, verweisen Sie in Ihrem Code auf die folgende Headerdatei.</span><span class="sxs-lookup"><span data-stu-id="09c86-133">Once the extension is installed, reference the following header file in your code.</span></span>

`#include <sqlite3.h>`

### <a name="building-sqlite-from-source-in-visual-studio"></a><span data-ttu-id="09c86-134">Erstellen von SQLite aus der Quelle in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="09c86-134">Building SQLite from source in Visual Studio</span></span>

<span data-ttu-id="09c86-135">Manchmal möchten Sie Ihre eigene SQLite-Binärdatei möglicherweise für die Verwendung [verschiedener Compileroptionen](http://www.sqlite.org/compile.html) kompilieren, um die Dateigröße zu reduzieren, die Leistung der Bibliothek zu optimieren, oder die Funktionen auf Ihre Anwendung anzupassen.</span><span class="sxs-lookup"><span data-stu-id="09c86-135">Sometimes you might wish to compile your own SQLite binary to use [various compiler options](http://www.sqlite.org/compile.html) to reduce the file size, performance tune the library, or tailor the feature set to your application.</span></span> <span data-ttu-id="09c86-136">SQLite stellt Optionen für die Plattformkonfiguration, für das Festlegen von Standardparameterwerten, für das Festlegen von Größeneinschränkungen, für das Steuern von Betriebsmerkmalen, für das Aktivieren von Funktionen, die normalerweise deaktiviert sind, für das Deaktivieren von Features, die normalerweise aktiviert sind, für das Auslassen von Features, für das Aktivieren der Analyse und des Debuggens und für das Verwalten des Arbeitsspeicher-Zuweisungsverhaltens unter Windows bereit.</span><span class="sxs-lookup"><span data-stu-id="09c86-136">SQLite provides options for platform configuration, setting default parameter values, setting size limits, controlling operating characteristics, enabling features normally turned off, disabling features normally turned on, omitting features, enabling analysis and debugging, and managing memory allocation behavior on Windows.</span></span>

*<span data-ttu-id="09c86-137">Hinzufügen einer Quelle zu einem Visual Studio-Projekt</span><span class="sxs-lookup"><span data-stu-id="09c86-137">Adding source to a Visual Studio project</span></span>*

<span data-ttu-id="09c86-138">Der SQLite-Quellcode steht zum Download auf der [SQLite.org-Downloadseite](https://www.sqlite.org/download.html) zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="09c86-138">The SQLite source code is available for download at the [SQLite.org download page](https://www.sqlite.org/download.html).</span></span> <span data-ttu-id="09c86-139">Fügen Sie diese Datei dem Visual Studio-Projekt der Anwendung hinzu, in der Sie SQLite verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="09c86-139">Add this file to the Visual Studio project of the application you wish to use SQLite in.</span></span>

*<span data-ttu-id="09c86-140">Konfigurieren von Präprozessoren</span><span class="sxs-lookup"><span data-stu-id="09c86-140">Configure Preprocessors</span></span>*

<span data-ttu-id="09c86-141">Verwenden Sie immer SQLITE\_OS\_WINRT und SQLITE\_API=\_\_declspec(dllexport) zusätzlich zu allen anderen [Kompilierzeitoptionen](http://www.sqlite.org/compile.html).</span><span class="sxs-lookup"><span data-stu-id="09c86-141">Always use SQLITE\_OS\_WINRT and SQLITE\_API=\_\_declspec(dllexport) in addition to any other [compile time options](http://www.sqlite.org/compile.html).</span></span>

![Bildschirm mit den SQLite-Eigenschaftsseiten](./images/property-pages.png)

## <a name="managing-a-sqlite-database"></a><span data-ttu-id="09c86-143">Verwalten einer SQLite-Datenbank</span><span class="sxs-lookup"><span data-stu-id="09c86-143">Managing a SQLite Database</span></span>

<span data-ttu-id="09c86-144">SQLite-Datenbanken können mit den SQLite-C-APIs erstellt, aktualisiert und gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="09c86-144">SQLite databases can be created, updated, and deleted with the SQLite C APIs.</span></span> <span data-ttu-id="09c86-145">Weitere Informationen zur SQLite-C-API finden Sie auf der SQLite.org-Seite unter [Einführung in die SQLite-C/C++-Schnittstelle](http://www.sqlite.org/cintro.html).</span><span class="sxs-lookup"><span data-stu-id="09c86-145">Details of the SQLite C API can be found at the SQLite.org [Introduction To The SQLite C/C++ Interface](http://www.sqlite.org/cintro.html) page.</span></span>

<span data-ttu-id="09c86-146">Um ein fundiertes Verständnis der Funktionsweise von SQLite zu erhalten, arbeiten Sie von der Hauptaufgabe der SQL-Datenbank (das Auswerten von SQL-Anweisungen) aus rückwärts.</span><span class="sxs-lookup"><span data-stu-id="09c86-146">To gain sound understanding of how SQLite works, work backwards from the main task of the SQL database which is to evaluate SQL statements.</span></span> <span data-ttu-id="09c86-147">Zwei Objekte müssen Sie berücksichtigen:</span><span class="sxs-lookup"><span data-stu-id="09c86-147">There are two objects to keep in mind:</span></span>

-   [<span data-ttu-id="09c86-148">Das Datenbankverbindungs-Handle</span><span class="sxs-lookup"><span data-stu-id="09c86-148">The database connection handle</span></span>](https://www.sqlite.org/c3ref/sqlite3.html)
-   [<span data-ttu-id="09c86-149">Das vorbereitete Anweisungsobjekt</span><span class="sxs-lookup"><span data-stu-id="09c86-149">The prepared statement object</span></span>](https://www.sqlite.org/c3ref/stmt.html)

<span data-ttu-id="09c86-150">Es gibt sechs Schnittstellen zum Ausführen von Datenbankvorgängen für diese Objekte:</span><span class="sxs-lookup"><span data-stu-id="09c86-150">There are six interfaces to perform database operations on these objects:</span></span>

-   [<span data-ttu-id="09c86-151">sqlite3\_open()</span><span class="sxs-lookup"><span data-stu-id="09c86-151">sqlite3\_open()</span></span>](https://web.archive.org/web/20141228070025/http:/www.sqlite.org/c3ref/open.html)
-   [<span data-ttu-id="09c86-152">sqlite3\_prepare()</span><span class="sxs-lookup"><span data-stu-id="09c86-152">sqlite3\_prepare()</span></span>](https://web.archive.org/web/20141228070025/http:/www.sqlite.org/c3ref/prepare.html)
-   [<span data-ttu-id="09c86-153">sqlite3\_step()</span><span class="sxs-lookup"><span data-stu-id="09c86-153">sqlite3\_step()</span></span>](https://web.archive.org/web/20141228070025/http:/www.sqlite.org/c3ref/step.html)
-   [<span data-ttu-id="09c86-154">sqlite3\_column()</span><span class="sxs-lookup"><span data-stu-id="09c86-154">sqlite3\_column()</span></span>](https://web.archive.org/web/20141228070025/http:/www.sqlite.org/c3ref/column_blob.html)
-   [<span data-ttu-id="09c86-155">sqlite3\_finalize()</span><span class="sxs-lookup"><span data-stu-id="09c86-155">sqlite3\_finalize()</span></span>](https://web.archive.org/web/20141228070025/http:/www.sqlite.org/c3ref/finalize.html)
-   [<span data-ttu-id="09c86-156">sqlite3\_close()</span><span class="sxs-lookup"><span data-stu-id="09c86-156">sqlite3\_close()</span></span>](https://web.archive.org/web/20141228070025/http:/www.sqlite.org/c3ref/close.html)

 

 
