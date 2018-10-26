---
author: Xansky
Description: Before you can run an experiment in your Universal Windows Platform (UWP) app with A/B testing, you must create a project and define your remote variables in the Dev Center dashboard.
title: Erstellen eines Experimentprojekts im Dashboard
ms.assetid: C3809FF1-0A6A-4715-B989-BE9D0E8C9013
ms.author: mhopkins
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Microsoft Store Services SDK, A/B-Tests, Experimente
ms.localizationpriority: medium
ms.openlocfilehash: 2abd7b9dda062cdb5210e74f6f2fde4c86e1470b
ms.sourcegitcommit: 6cc275f2151f78db40c11ace381ee2d35f0155f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5567737"
---
# <a name="create-an-experiment-project-in-the-dashboard"></a><span data-ttu-id="cd195-103">Erstellen eines Experimentprojekts im Dashboard</span><span class="sxs-lookup"><span data-stu-id="cd195-103">Create an experiment project in the dashboard</span></span>

<span data-ttu-id="cd195-104">Erstellen Sie zunächst für das Experiment ein [Projekt](run-app-experiments-with-a-b-testing.md#terms) für Ihre App im Dev Center-Dashboard, und definieren Sie die Remotevariablen, auf die Ihre App zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="cd195-104">To get started with experimentation, create an experimentation [project](run-app-experiments-with-a-b-testing.md#terms) for your app in the Dev Center dashboard and define the remote variables that your app can access.</span></span>

<span data-ttu-id="cd195-105">Die folgenden Anweisungen beschreiben die wichtigsten Schritte für die Erstellung eines Projekts.</span><span class="sxs-lookup"><span data-stu-id="cd195-105">The following instructions describe the core steps to create a project.</span></span> <span data-ttu-id="cd195-106">Eine ausführliche Erläuterung, die den gesamten Erstellungs- und Ausführungsprozess für ein Projekt und die Durchführung eines Experiments veranschaulicht, finden Sie unter [Erstellen und Durchführen eines ersten Experiments mit A/B-Tests](create-and-run-your-first-experiment-with-a-b-testing.md).</span><span class="sxs-lookup"><span data-stu-id="cd195-106">For a detailed walkthrough that demonstrates the end-to-end process of creating a project and then running an experiment, see [Create and run your first experiment with A/B testing](create-and-run-your-first-experiment-with-a-b-testing.md).</span></span>

## <a name="instructions"></a><span data-ttu-id="cd195-107">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="cd195-107">Instructions</span></span>

1. <span data-ttu-id="cd195-108">Melden Sie sich beim [Dev Center-Dashboard](https://dev.windows.com/overview) an.</span><span class="sxs-lookup"><span data-stu-id="cd195-108">Sign in to the [Dev Center dashboard](https://dev.windows.com/overview).</span></span>
2. <span data-ttu-id="cd195-109">Wählen Sie unter **Ihre Apps** die App aus, für die Sie ein Experiment erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="cd195-109">Under **Your apps**, select the app for which you want to create an experiment.</span></span>
3. <span data-ttu-id="cd195-110">Wählen Sie im Navigationsbereich **Dienste** und dann **Experimente**.</span><span class="sxs-lookup"><span data-stu-id="cd195-110">In the navigation pane, select **Services** and then select **Experimentation**.</span></span>
4. <span data-ttu-id="cd195-111">Klicken Sie auf der Seite **Experimente** im Abschnitt **Projekte** auf die Schaltfläche **Neues Projekt**.</span><span class="sxs-lookup"><span data-stu-id="cd195-111">On the **Experimentation** page, click the **New project** button in the **Projects** section.</span></span> <span data-ttu-id="cd195-112">Wenn Sie bereits ein oder mehrere Projekte erstellt haben, werden diese Projekte im Abschnitt **Projekte** aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="cd195-112">If you have already created one or more projects, those projects are listed in the **Projects** section.</span></span>
5. <span data-ttu-id="cd195-113">Geben Sie auf der Seite **Neues Projekt** einen Namen für das neue Projekt ein.</span><span class="sxs-lookup"><span data-stu-id="cd195-113">In the **New project** page, enter a name for your new project.</span></span>
6. <span data-ttu-id="cd195-114">Fügen Sie im Abschnitt **Remotevariablen** die [Variablen](run-app-experiments-with-a-b-testing.md#terms) hinzu, die für alle Experimente in diesem Projekt verfügbar sein sollen, und definieren Sie die Standardwerte für jede Variable.</span><span class="sxs-lookup"><span data-stu-id="cd195-114">In the **Remote variables** section, add the [variables](run-app-experiments-with-a-b-testing.md#terms) that you want to be available to all experiments in this project, and define default values for each variable.</span></span> <span data-ttu-id="cd195-115">Die hier festgelegten Standardwerte werden für die Steuerelementgruppe der Experimente verwendet, sowie für alle Benutzer, die an dem Experiment nicht teilnehmen.</span><span class="sxs-lookup"><span data-stu-id="cd195-115">The default values you specify here are used for the control group of the experiments, and for any users who do not participate in the experiment.</span></span>
  1. <span data-ttu-id="cd195-116">Falls der Abschnitt **Remotevariablen** reduziert ist, klicken Sie in der Abschnittsüberschrift auf **Anzeigen**.</span><span class="sxs-lookup"><span data-stu-id="cd195-116">If the **Remote variables** section is collapsed, click **Show** on the section heading.</span></span>
  2. <span data-ttu-id="cd195-117">Klicken Sie auf **Variable hinzufügen**, um jede neue Variable zu erstellen, die für jedes Experiment in diesem Projekt verfügbar sein soll, und geben Sie den Variablennamen und den Standardwert der Variablen ein.</span><span class="sxs-lookup"><span data-stu-id="cd195-117">Click **Add variable** to create each new variable that you want to be available to any experiment in this project, and type the variable name and the default value of the variable.</span></span>
  3. <span data-ttu-id="cd195-118">Wenn Sie das Hinzufügen von Variablen beendet haben, klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="cd195-118">When you are done adding variables, click **Save**.</span></span>
3. <span data-ttu-id="cd195-119">Notieren Sie im Abschnitt **SDK-Integration** den Wert der [Projekt-ID](run-app-experiments-with-a-b-testing.md#terms).</span><span class="sxs-lookup"><span data-stu-id="cd195-119">In the **SDK integration** section, make note of the [Project ID](run-app-experiments-with-a-b-testing.md#terms) value.</span></span> <span data-ttu-id="cd195-120">Zum [Codieren der App für das Experiment](code-your-experiment-in-your-app.md), müssen Sie auf diese Projekt-ID in Ihrem Code verweisen, damit Sie Variantendaten empfangen sowie Anzeige- und Umwandlungsereignisse an das Dev Center melden können.</span><span class="sxs-lookup"><span data-stu-id="cd195-120">When you [code your app for experimentation](code-your-experiment-in-your-app.md), you must reference this project ID in your code so you can receive variation data and report view and conversion events to Dev Center.</span></span>

> [!NOTE]
> <span data-ttu-id="cd195-121">Sie können keine Remotevariablen bearbeiten, hinzufügen oder entfernen, während ein Experiment im Projekt aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="cd195-121">You cannot edit, add, or remove remote variables while an experiment in the project is active.</span></span> <span data-ttu-id="cd195-122">Diese Einschränkung hilft, die Integrität der Daten der Steuerelementgruppe für das aktive Experiment zu schützen.</span><span class="sxs-lookup"><span data-stu-id="cd195-122">This limitation helps protect the integrity of the data for the control group for the active experiment.</span></span>


## <a name="next-steps"></a><span data-ttu-id="cd195-123">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="cd195-123">Next steps</span></span>

<span data-ttu-id="cd195-124">Nachdem Sie ein Projekt erstellt haben, können Sie mit dem [Codieren der App für das Experiment](code-your-experiment-in-your-app.md) beginnen, indem Sie Werte von Remotevariablen in Ihrer App abrufen, und Sie können [ein Experiment im Projekt erstellen](define-your-experiment-in-the-dev-center-dashboard.md).</span><span class="sxs-lookup"><span data-stu-id="cd195-124">After you create a project, you can [code your app for experimentation](code-your-experiment-in-your-app.md) to start retrieving remote variable values in your app, and you can [create an experiment in the project](define-your-experiment-in-the-dev-center-dashboard.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="cd195-125">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="cd195-125">Related topics</span></span>

* [<span data-ttu-id="cd195-126">Codieren der App für das Experiment</span><span class="sxs-lookup"><span data-stu-id="cd195-126">Code your app for experimentation</span></span>](code-your-experiment-in-your-app.md)
* [<span data-ttu-id="cd195-127">Definieren des Experiments im Dev Center-Dashboard</span><span class="sxs-lookup"><span data-stu-id="cd195-127">Define your experiment in the Dev Center dashboard</span></span>](define-your-experiment-in-the-dev-center-dashboard.md)
* [<span data-ttu-id="cd195-128">Verwalten des Experiments im Dev Center-Dashboard</span><span class="sxs-lookup"><span data-stu-id="cd195-128">Manage your experiment in the Dev Center dashboard</span></span>](manage-your-experiment.md)
* [<span data-ttu-id="cd195-129">Erstellen und Ausführen eines ersten Experiments mit A/B-Tests</span><span class="sxs-lookup"><span data-stu-id="cd195-129">Create and run your first experiment with A/B testing</span></span>](create-and-run-your-first-experiment-with-a-b-testing.md)
* [<span data-ttu-id="cd195-130">Ausführen von App-Experimenten mit A/B-Tests</span><span class="sxs-lookup"><span data-stu-id="cd195-130">Run app experiments with A/B testing</span></span>](run-app-experiments-with-a-b-testing.md)
