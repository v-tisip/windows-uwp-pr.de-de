---
title: Aktivierung des Xbox One-Entwicklermodus
description: Dieser Artikel beschreibt das Aktivieren des Entwicklermodus, sodass Sie zwischen Retailmodus und Entwicklermodus wechseln können.
ms.date: 02/08/2017
ms.topic: article
keywords: windows 10, uwp
ms.assetid: ade80769-17ae-46e9-9c2f-bf08ae5a51ee
ms.localizationpriority: medium
ms.openlocfilehash: 3664ecae152b7178709bffc373a877e58a86461a
ms.sourcegitcommit: eaee5a45d5eace64c69e67691e5330b466cc74c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2019
ms.locfileid: "9083260"
---
# <a name="xbox-one-developer-mode-activation"></a><span data-ttu-id="7fe18-104">Aktivierung des Xbox One-Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="7fe18-104">Xbox One Developer Mode activation</span></span>

## <a name="how-developer-mode-works"></a><span data-ttu-id="7fe18-105">Funktionsweise des Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="7fe18-105">How Developer Mode works</span></span>
<span data-ttu-id="7fe18-106">Die Xbox One verfügt über zwei Modi: *Einzelhandelsmodus* (**1**) und *Entwicklermodus* (**2**).</span><span class="sxs-lookup"><span data-stu-id="7fe18-106">Xbox One has two modes, *Retail* Mode (**1**) and *Developer* Mode (**2**).</span></span> <span data-ttu-id="7fe18-107">Im Einzelhandelsmodus ist die Konsole in dem Zustand, in dem sie von jedem Kunden oder Benutzer einer Xbox One-Konsole verwendet wird: Sie können als Benutzer Spiele spielen und Apps ausführen.</span><span class="sxs-lookup"><span data-stu-id="7fe18-107">In Retail Mode, the console is in the state that any customer or user of an Xbox One console would use: you can play games and run apps as a user.</span></span> <span data-ttu-id="7fe18-108">Im Entwicklermodus können Sie Software für die Konsole entwickeln, jedoch keine Spiele spielen und Apps ausführen.</span><span class="sxs-lookup"><span data-stu-id="7fe18-108">In Developer Mode, you can develop software for the console, but you cannot play retail games or run retail apps.</span></span>

<span data-ttu-id="7fe18-109">Der Entwicklermodus kann auf jeder Xbox One-Konsole aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="7fe18-109">Developer Mode can be enabled on any retail Xbox One console.</span></span> <span data-ttu-id="7fe18-110">Nach dem Aktivieren des Entwicklermodus können Sie zwischen dem Einzelhandelsmodus (**2a**) und dem Entwicklermodus (**2b**) wechseln.</span><span class="sxs-lookup"><span data-stu-id="7fe18-110">After Developer Mode is enabled, you can switch back and forth between Retail (**2a**) and Developer Modes (**2b**).</span></span>

![Xbox One-Modi](images/dev-mode-flow.png)

## <a name="activate-developer-mode-on-your-retail-xbox-one-console"></a><span data-ttu-id="7fe18-112">Aktivieren des Entwicklermodus auf der Xbox One-Konsole</span><span class="sxs-lookup"><span data-stu-id="7fe18-112">Activate Developer Mode on your retail Xbox One console</span></span>

1.  <span data-ttu-id="7fe18-113">Starten Sie die Xbox One-Konsole.</span><span class="sxs-lookup"><span data-stu-id="7fe18-113">Start your Xbox One console.</span></span>

2.  <span data-ttu-id="7fe18-114">Suchen Sie die **DevMode-Aktivierungs**-App im Xbox One-Store, und installieren Sie sie.</span><span class="sxs-lookup"><span data-stu-id="7fe18-114">Search for and install the **Dev Mode Activation** app from the Xbox One store.</span></span>

    ![Installieren der DevMode-Aktivierungs-App](images/devkit-activation-1.png)

3.  <span data-ttu-id="7fe18-116">Starten Sie die App über die Store-Seite.</span><span class="sxs-lookup"><span data-stu-id="7fe18-116">Launch the app from the Store page.</span></span>

    ![DevMode-Aktivierungs-App](images/devkit-activation-2.png)

4.  <span data-ttu-id="7fe18-118">Notieren Sie sich den in der DevMode-Aktivierungs-App angezeigten Code.</span><span class="sxs-lookup"><span data-stu-id="7fe18-118">Note the code displayed in the Dev Mode Activation app.</span></span>

    ![Aktivierungsschritt 5](images/activation-step-5.png)  
    
5.  <span data-ttu-id="7fe18-120">[Ein app-Entwickler-Konto im Partner Center registrieren](https://developer.microsoft.com/store/register).</span><span class="sxs-lookup"><span data-stu-id="7fe18-120">[Register an app developer account in Partner Center](https://developer.microsoft.com/store/register).</span></span>  <span data-ttu-id="7fe18-121">Dies ist auch der erste Schritt beim Veröffentlichen Ihres Spiels.</span><span class="sxs-lookup"><span data-stu-id="7fe18-121">This is also the first step towards publishing your game.</span></span>

6.  <span data-ttu-id="7fe18-122">Melden Sie sich beim [Partner Center](https://partner.microsoft.com/dashboard) mit Ihrem gültig, aktuellen Partner Center-app-Entwicklerkonto an.</span><span class="sxs-lookup"><span data-stu-id="7fe18-122">Sign in to [Partner Center](https://partner.microsoft.com/dashboard) with your valid, current Partner Center app developer account.</span></span>  <span data-ttu-id="7fe18-123">Wenn Sie nicht mehrere Optionen im linken Navigationsbereich angezeigt oder nicht finden Sie unter der Option **eine neue app erstellen** , in **der Übersicht auf, die folgenden Schritte und Aktivierung Links _funktioniert nicht_** . Stellen Sie sicher, dass Sie Ihr Entwicklerkonto app aus dem vorherigen Schritt vollständig registriert.</span><span class="sxs-lookup"><span data-stu-id="7fe18-123">If you don't see multiple options in the left hand navigation pane, or don't see the **Create a new app** option in the **Overview** section, the following steps and activation links _will not work_; make sure you fully registered your app developer account from the previous step.</span></span>

7.  <span data-ttu-id="7fe18-124">Wechseln Sie zu [partner.microsoft.com/xboxconfig/devices](https://partner.microsoft.com/xboxconfig/devices).</span><span class="sxs-lookup"><span data-stu-id="7fe18-124">Go to [partner.microsoft.com/xboxconfig/devices](https://partner.microsoft.com/xboxconfig/devices).</span></span>

8.  <span data-ttu-id="7fe18-125">Geben Sie den in der DevMode Aktivierungs-App angezeigten Aktivierungscode ein.</span><span class="sxs-lookup"><span data-stu-id="7fe18-125">Enter the activation code displayed in the Dev Mode Activation app.</span></span> <span data-ttu-id="7fe18-126">Ihrem Konto ist eine begrenzte Anzahl von Aktivierungen zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="7fe18-126">You have a limited number of activations associated with your account.</span></span> <span data-ttu-id="7fe18-127">Nach dem Aktivieren des Entwicklermodus aktiviert wurde, wird die Partner Center angegeben, dass Sie eine der mit Ihrem Konto verknüpften Aktivierungen verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="7fe18-127">After Developer Mode has been activated, Partner Center will indicate you have used one of the activations associated with your account.</span></span>

    ![Aktivierungsschritt 8](images/activation-step-8-rs2.png)    
    
9.  <span data-ttu-id="7fe18-129">Klicken Sie auf **Agree and activate**.</span><span class="sxs-lookup"><span data-stu-id="7fe18-129">Click **Agree and activate**.</span></span> <span data-ttu-id="7fe18-130">Dadurch wird die Seite neu geladen, und Ihr Gerät wird in der Tabelle aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="7fe18-130">This will cause the page to reload, and you will see your device populate in the table.</span></span> <span data-ttu-id="7fe18-131">Die Nutzungsbedingungen für das Aktivierungsprogramm für den Xbox One-Entwicklermodus finden Sie unter [Programm zur Aktivierung des Xbox One-Entwicklermodus](https://go.microsoft.com/fwlink/p/?LinkId=760399).</span><span class="sxs-lookup"><span data-stu-id="7fe18-131">Terms for the Xbox One Developer Mode Activation Program agreement can be found at [Xbox One Developer Mode Activation Program](https://go.microsoft.com/fwlink/p/?LinkId=760399).</span></span>

10. <span data-ttu-id="7fe18-132">Nachdem Sie den Aktivierungscode eingegeben haben, wird auf der Konsole ein Statusbildschirm für den Aktivierungsvorgang angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7fe18-132">After you’ve entered your activation code, your console will display a progress screen for the activation process.</span></span>  
    
11. <span data-ttu-id="7fe18-133">Öffnen Sie nach Abschluss der Aktivierung die DevMode-Aktivierungs-App, und klicken Sie auf **Switch und restart**, um zum Entwicklermodus zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="7fe18-133">After activation has completed, open the Dev Mode Activation app and click **Switch and restart** to go to Developer Mode.</span></span> <span data-ttu-id="7fe18-134">Beachten Sie, dass dies länger als gewöhnlich dauert.</span><span class="sxs-lookup"><span data-stu-id="7fe18-134">Note that this will take longer than usual.</span></span>

    ![Aktivierungsschritt 12](images/activation-step-12.png)   

## <a name="switch-between-retail-and-developer-mode"></a><span data-ttu-id="7fe18-136">Wechseln zwischen Einzelhandels- und Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="7fe18-136">Switch between Retail and Developer Mode</span></span>
<span data-ttu-id="7fe18-137">Nachdem der Entwicklermodus auf der Konsole aktiviert wurde, können Sie mithilfe von **Dev Home** zwischen Einzelhandelsmodus und Entwicklermodus wechseln.</span><span class="sxs-lookup"><span data-stu-id="7fe18-137">After Developer Mode has been enabled on your console, use **Dev Home** to switch between Retail Mode and Developer Mode.</span></span> <span data-ttu-id="7fe18-138">Weitere Informationen zum Starten und Verwenden von Dev Home finden Sie unter [Einführung in Xbox One-Tools](introduction-to-xbox-tools.md).</span><span class="sxs-lookup"><span data-stu-id="7fe18-138">To learn more about starting and using Dev Home, see [Introduction to Xbox One tools](introduction-to-xbox-tools.md).</span></span>

* <span data-ttu-id="7fe18-139">Um in den Einzelhandelsmodus wechseln, öffnen Sie **Dev Home**.</span><span class="sxs-lookup"><span data-stu-id="7fe18-139">To switch to Retail Mode, open **Dev Home**.</span></span> <span data-ttu-id="7fe18-140">Wählen Sie unter **Schnelle Aktionen** die Option **Entwicklermodus verlassen**.</span><span class="sxs-lookup"><span data-stu-id="7fe18-140">Under **Quick Actions**, select **Leave Dev Mode**.</span></span> <span data-ttu-id="7fe18-141">Dadurch wird die Konsole im Einzelhandelsmodus neu gestartet.</span><span class="sxs-lookup"><span data-stu-id="7fe18-141">This will restart your console in Retail Mode.</span></span>    

  ![Aktivierungsschritt 13](images/activation-step-13-rs4.png)  
  
* <span data-ttu-id="7fe18-143">Um zum Entwicklermodus zu wechseln, verwenden Sie die DevMode-Aktivierungsapp.</span><span class="sxs-lookup"><span data-stu-id="7fe18-143">To switch to Developer Mode, use the Dev Mode Activation app.</span></span> <span data-ttu-id="7fe18-144">Öffnen Sie die App, und wählen Sie **Wechseln und neu starten**.</span><span class="sxs-lookup"><span data-stu-id="7fe18-144">Open the app and select **Switch and restart**.</span></span> <span data-ttu-id="7fe18-145">Dadurch wird die Konsole im Entwicklermodus neu gestartet.</span><span class="sxs-lookup"><span data-stu-id="7fe18-145">This will restart your console in Developer Mode.</span></span>  

  ![Aktivierungsschritt 14](images/activation-step-12.png)  

## <a name="see-also"></a><span data-ttu-id="7fe18-147">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7fe18-147">See also</span></span>
- [<span data-ttu-id="7fe18-148">Deaktivierung des Xbox One-Entwicklermodus</span><span class="sxs-lookup"><span data-stu-id="7fe18-148">Xbox One Developer Mode deactivation</span></span>](devkit-deactivation.md)
- [<span data-ttu-id="7fe18-149">UWP auf Xbox One</span><span class="sxs-lookup"><span data-stu-id="7fe18-149">UWP on Xbox One</span></span>](index.md)
