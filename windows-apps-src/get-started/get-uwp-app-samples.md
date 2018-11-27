---
title: Beispiele für UWP-Apps abrufen
description: Erfahren Sie, wie Sie die Beispiele für UWP-Codes von GitHub herunterladen können.
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Beispielcode, Codebeispiele
ms.assetid: 393c5a81-ee14-45e7-acd7-495e5d916909
ms.localizationpriority: medium
ms.openlocfilehash: 64eb0d13db1fbcf49d9da28e57eb85ff84823bf1
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7830485"
---
# <a name="get-uwp-app-samples"></a><span data-ttu-id="a7e42-104">Beispiele für UWP-Apps abrufen</span><span class="sxs-lookup"><span data-stu-id="a7e42-104">Get UWP app samples</span></span>

<span data-ttu-id="a7e42-105">Die Beispiele für Universelle Windows Plattform-Apps (UWP-Apps) sind über Repositorys auf GitHub verfügbar.</span><span class="sxs-lookup"><span data-stu-id="a7e42-105">The Universal Windows Platform (UWP) app samples are available through repositories on GitHub.</span></span> <span data-ttu-id="a7e42-106">Unter [Samples](https://developer.microsoft.com/windows/samples "Dev Center Beispiele") finden Sie eine durchsuchbare, kategorisierte Liste, oder durchsuchen Sie die Repository [Microsoft/Windows-universal-samples](https://github.com/Microsoft/Windows-universal-samples "GitHub-Repository mit App-Beispielen für die Universelle Windows-Plattform"), die Beispiele für alle UWP-Features und ihre API-Verwendungsmuster enthält.</span><span class="sxs-lookup"><span data-stu-id="a7e42-106">See [Samples](https://developer.microsoft.com/windows/samples "Dev Center samples") for a searchable, categorized list, or browse the [Microsoft/Windows-universal-samples](https://github.com/Microsoft/Windows-universal-samples "Universal Windows Platform app samples GitHub repository") repository, which contains samples that demonstrate all of the UWP features and their API usage patterns.</span></span>  
![GitHub-UWP-Beispiel-Repository](images/GitHubUWPSamplesPage.png)

## <a name="download-the-code"></a><span data-ttu-id="a7e42-108">Code herunterladen</span><span class="sxs-lookup"><span data-stu-id="a7e42-108">Download the code</span></span>

<span data-ttu-id="a7e42-109">Informationen zum Herunterladen der Beispiele finden Sie unter [Repository](https://github.com/Microsoft/Windows-universal-samples "GitHub-Repository mit App-Beispielen für die Universelle Windows-Plattform"). Wählen Sie **Clone or download** und dann **Herunterladen der ZIP-Datei**.</span><span class="sxs-lookup"><span data-stu-id="a7e42-109">To download the samples, go to the [repository](https://github.com/Microsoft/Windows-universal-samples "Universal Windows Platform app samples GitHub repository") and select **Clone or download**, then **Download ZIP**.</span></span> <span data-ttu-id="a7e42-110">Oder klicken Sie einfach [hier](https://github.com/Microsoft/Windows-universal-samples/archive/master.zip "ZIP-Datei mit App-Beispielen für die Universelle Windows-Plattform herunterladen").</span><span class="sxs-lookup"><span data-stu-id="a7e42-110">Or, just click [here](https://github.com/Microsoft/Windows-universal-samples/archive/master.zip "Universal Windows Platform app samples zip file download").</span></span>

<span data-ttu-id="a7e42-111">Die ZIP-Datei enthält stets die neuesten Beispiele.</span><span class="sxs-lookup"><span data-stu-id="a7e42-111">The zip file will always have the latest samples.</span></span> <span data-ttu-id="a7e42-112">Sie benötigen zum Herunterladen kein GitHub-Konto.</span><span class="sxs-lookup"><span data-stu-id="a7e42-112">You don’t need a GitHub account to download it.</span></span> <span data-ttu-id="a7e42-113">Wenn ein SDK-Update veröffentlicht wird oder wenn Sie alle aktuellen Änderungen/Ergänzungen übernehmen möchten, suchen Sie einfach nach der neuesten ZIP-Datei.</span><span class="sxs-lookup"><span data-stu-id="a7e42-113">When an SDK update is released or if you want to pick up any recent changes/additions, just check back for the latest zip file.</span></span>

![Beispieldownload](images/SamplesDownloadButton.png)


> [!NOTE]
> <span data-ttu-id="a7e42-115">Für das Öffnen, Erstellen und Ausführen der UWP-Beispiele sind Visual Studio2015 oder höher und das Windows SDK erforderlich.</span><span class="sxs-lookup"><span data-stu-id="a7e42-115">The UWP samples require Visual Studio 2015 or later and the Windows SDK to open, build, and run.</span></span> <span data-ttu-id="a7e42-116">Eine kostenlose Kopie von Visual Studio Community mit Unterstützung für die Erstellung von UWP-Apps erhalten Sie [hier](http://go.microsoft.com/fwlink/p/?LinkID=280676 "Downloads für Windows-Entwicklungstools").</span><span class="sxs-lookup"><span data-stu-id="a7e42-116">You can get a free copy of Visual Studio Community with support for building UWP apps [here](http://go.microsoft.com/fwlink/p/?LinkID=280676 "Windows development tools downloads").</span></span>  
>
> <span data-ttu-id="a7e42-117">Zudem sollten Sie sicherstellen, dass nicht nur einzelne Beispiele, sondern das gesamte Archiv entpackt wurde.</span><span class="sxs-lookup"><span data-stu-id="a7e42-117">Also, be sure to unzip the entire archive, and not just individual samples.</span></span> <span data-ttu-id="a7e42-118">Alle Beispiele erfordern den Archivordner „SharedContent“.</span><span class="sxs-lookup"><span data-stu-id="a7e42-118">The samples all depend on the SharedContent folder in the archive.</span></span> <span data-ttu-id="a7e42-119">Die Beispiele für UWP-Features verfügen über verknüpfte Dateien in Visual Studio, um das Duplizieren gemeinsam verwendeter Dateien zu vermeiden, z.B. von Beispieldateien für Vorlagen und Bildressourcen.</span><span class="sxs-lookup"><span data-stu-id="a7e42-119">The UWP feature samples use Linked files in Visual Studio to reduce duplication of common files, including sample template files and image assets.</span></span> <span data-ttu-id="a7e42-120">Diese gemeinsamen Dateien werden im Ordner „SharedContent“ im Stammverzeichnis des Repositorys gespeichert. Der Verweis in den Projektdateien erfolgt über Links.</span><span class="sxs-lookup"><span data-stu-id="a7e42-120">These common files are stored in the SharedContent folder at the root of the repository, and are referred to in the project files using links.</span></span>

<span data-ttu-id="a7e42-121">Öffnen Sie nach dem Herunterladen der ZIP-Datei die Beispiele in Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="a7e42-121">After you download the zip file, open the samples in Visual Studio:</span></span>

1.  <span data-ttu-id="a7e42-122">Klicken Sie vor dem Extrahieren des Archivs mit der rechten Maustaste darauf, und wählen Sie **Eigenschaften** > **Blockierung aufheben** > **Übernehmen** aus.</span><span class="sxs-lookup"><span data-stu-id="a7e42-122">Before you unzip the archive, right-click it, select **Properties** > **Unblock** > **Apply**.</span></span> <span data-ttu-id="a7e42-123">Entpacken Sie anschließend das Archiv in einen lokalen Ordner auf Ihrem Computer.</span><span class="sxs-lookup"><span data-stu-id="a7e42-123">Then, unzip the archive to a local folder on your machine.</span></span>

    ![Entpacktes Archiv](images/SamplesUnzip1.png)
2.  <span data-ttu-id="a7e42-125">Im Beispielordner wird eine Reihe von Ordnern angezeigt, die jeweils ein Beispiel für UWP-Features enthalten.</span><span class="sxs-lookup"><span data-stu-id="a7e42-125">Within the samples folder, you’ll see a number of folders, each of which contains a UWP feature sample.</span></span>

    ![Beispielordner](images/SamplesUnzip2.png)

3.  <span data-ttu-id="a7e42-127">Wählen Sie ein Beispiel wie z.B. Höhenmesser aus, um mehrere Ordner mit den unterstützten Sprachen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a7e42-127">Select a sample, such as Altimeter, and you’ll see multiple folders indicating the languages supported.</span></span>

    ![Sprachordner](images/SamplesUnzip3.png)

4.  <span data-ttu-id="a7e42-129">Wählen Sie die gewünschte Sprache (z.B. CS für C\#) aus. Es wird eine Visual Studio-Projektmappendatei angezeigt, die Sie in Visual Studio öffnen können.</span><span class="sxs-lookup"><span data-stu-id="a7e42-129">Select the language you’d like to use, such as CS for C\#, and you’ll see a Visual Studio solution file, which you can open in Visual Studio.</span></span>

    ![VS-Projektmappe](images/SamplesUnzip4.png)

## <a name="give-feedback-ask-questions-and-report-issues"></a><span data-ttu-id="a7e42-131">Geben Sie Feedback, stellen Sie Fragen und melden Sie Probleme</span><span class="sxs-lookup"><span data-stu-id="a7e42-131">Give feedback, ask questions, and report issues</span></span>

<span data-ttu-id="a7e42-132">Wenn Sie Fragen oder Probleme haben, klicken Sie einfach auf die Registerkarte „Probleme“ im Repository, um ein neues Problem zu erstellen. Wir werden versuchen, zu helfen.</span><span class="sxs-lookup"><span data-stu-id="a7e42-132">If you have problems or questions, just use the Issues tab on the repository to create a new issue and we’ll do what we can to help.</span></span>

![Feedback-Bild](images/GitHubUWPSamplesFeedback.png)
