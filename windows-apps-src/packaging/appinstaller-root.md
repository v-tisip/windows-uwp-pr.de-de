---
author: laurenhughes
title: Installieren von UWP-Apps mit dem App-Installer
description: Dieser Abschnitt enthält Artikel oder Links zum App-Installer und erläutert die Funktionen des App-Installers.
ms.author: lahugh
ms.date: 10/10/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, App-Installer, AppInstaller, querladen, verwandte Gruppe, optionale Pakete
ms.localizationpriority: medium
ms.openlocfilehash: 06ccb50e3c1a97a69041ca2d3b4de59a550e3399
ms.sourcegitcommit: ab92c3e0dd294a36e7f65cf82522ec621699db87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "1831804"
---
# <a name="install-uwp-apps-with-app-installer"></a><span data-ttu-id="b8ce1-104">Installieren von UWP-Apps mit dem App-Installer</span><span class="sxs-lookup"><span data-stu-id="b8ce1-104">Install UWP apps with App Installer</span></span>

## <a name="purpose"></a><span data-ttu-id="b8ce1-105">Zweck</span><span class="sxs-lookup"><span data-stu-id="b8ce1-105">Purpose</span></span>
<span data-ttu-id="b8ce1-106">Dieser Abschnitt enthält Artikel oder Links zum App-Installer und erläutert die Funktionen des App-Installers.</span><span class="sxs-lookup"><span data-stu-id="b8ce1-106">This section contains or links to articles about App Installer and how to use the features of App Installer.</span></span> 

<span data-ttu-id="b8ce1-107">Mit dem App-Installer können UWP-Apps durch Doppelklicken auf das App-Paket installiert werden.</span><span class="sxs-lookup"><span data-stu-id="b8ce1-107">App Installer allows for UWP apps to be installed by double clicking the app package.</span></span> <span data-ttu-id="b8ce1-108">Dies bedeutet, dass Benutzer weder PowerShell noch andere Entwicklungstools verwenden müssen, um UWP-Apps bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="b8ce1-108">This means that users don't need to use PowerShell or other developer tools to deploy UWP apps.</span></span> <span data-ttu-id="b8ce1-109">Der App-Installer kann ebenfalls eine App aus dem Web, von optionalen Paketen oder verwandten Gruppen installieren.</span><span class="sxs-lookup"><span data-stu-id="b8ce1-109">The App Installer can also install an app from the web, optional packages, and related sets.</span></span> <span data-ttu-id="b8ce1-110">Informationen über die Verwendung des App-Installers zur Installation Ihrer App finden Sie in den in der folgenden Tabelle aufgeführten Themen.</span><span class="sxs-lookup"><span data-stu-id="b8ce1-110">To learn how to use the App Installer to install your app, see the topics in the table.</span></span>

| <span data-ttu-id="b8ce1-111">Thema</span><span class="sxs-lookup"><span data-stu-id="b8ce1-111">Topic</span></span> | <span data-ttu-id="b8ce1-112">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b8ce1-112">Description</span></span> |
|-------|-------------|
| [<span data-ttu-id="b8ce1-113">Erstellen einer App-Installer-Datei mit Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b8ce1-113">Create App Installer file with Visual Studio</span></span>](create-appinstallerfile-vs.md)| <span data-ttu-id="b8ce1-114">Hier erfahren Sie, wie Sie Visual Studio verwenden, um automatische Updates mithilfe der .appinstaller-Datei zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="b8ce1-114">Learn how to use Visual Studio to enable automatic updates using the .appinstaller file.</span></span> |
| [<span data-ttu-id="b8ce1-115">Installieren von UWP-Apps von einer Webseite</span><span class="sxs-lookup"><span data-stu-id="b8ce1-115">Install UWP apps from a web page</span></span>](installing-UWP-apps-web.md) | <span data-ttu-id="b8ce1-116">In diesem Abschnitt werden die erforderlichen Schritte aufgeführt, damit Sie Benutzern die Installation Ihre Apps direkt von der Webseite ermöglichen können.</span><span class="sxs-lookup"><span data-stu-id="b8ce1-116">In this section, we will review the steps you need to take to allow users to install your apps directly from the web page.</span></span> |
| [<span data-ttu-id="b8ce1-117">Installieren Sie mithilfe einer App-Installer-Datei eine verwandte Gruppe</span><span class="sxs-lookup"><span data-stu-id="b8ce1-117">Install a related set using an App Installer file</span></span>](install-related-set.md) | <span data-ttu-id="b8ce1-118">Erfahren Sie in diesem Abschnitt, wie Sie die Installation von verwandten Gruppen über den App-Installer ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="b8ce1-118">In this section, learn how to allow the installation of a related set via App Installer.</span></span> <span data-ttu-id="b8ce1-119">Wir durchlaufen ebenfalls die notwendigen Schritte zum Erstellen einer App-Installer-Datei, die Ihre verwandten Gruppen definieren.</span><span class="sxs-lookup"><span data-stu-id="b8ce1-119">We will also go through the steps to construct an App Installer file that will define your related set.</span></span> |
| [<span data-ttu-id="b8ce1-120">Problembehandlung bei der Installation der App-Installer-Datei</span><span class="sxs-lookup"><span data-stu-id="b8ce1-120">Troubleshoot installation issues with the App Installer file</span></span>](troubleshoot-appinstaller-issues.md) | <span data-ttu-id="b8ce1-121">Allgemeine Probleme und Lösungen beim Querladen von Anwendungen mit der App-Installer-Datei.</span><span class="sxs-lookup"><span data-stu-id="b8ce1-121">Common issues and solutions when sideloading applications with the App Installer file.</span></span> |
| [<span data-ttu-id="b8ce1-122">Verweis auf die App-Installer-Datei (.appinstaller)</span><span class="sxs-lookup"><span data-stu-id="b8ce1-122">App Installer file (.appinstaller) reference</span></span>](https://docs.microsoft.com/uwp/schemas/appinstallerschema/app-installer-file) | <span data-ttu-id="b8ce1-123">Das vollständige XML-Schema für die App-Installer-Datei anzeigen.</span><span class="sxs-lookup"><span data-stu-id="b8ce1-123">View the full XML schema for the App Installer file.</span></span> |