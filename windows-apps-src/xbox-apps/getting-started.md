---
author: Mtoepke
title: Erste Schritte bei der Entwicklung von UWP-Apps auf Xbox One
description: Einrichten des Computers und der Xbox One für die UWP-Entwicklung
ms.author: scotmi
ms.date: 10/12/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: da260b4f9f5f50d97d39af883217dfbae91a566e
ms.sourcegitcommit: 310a4555fedd4246188a98b31f6c094abb33ec60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "5128818"
---
# <a name="getting-started-with-uwp-app-development-on-xbox-one"></a><span data-ttu-id="fc449-104">Erste Schritte bei der Entwicklung von UWP-Apps auf Xbox One</span><span class="sxs-lookup"><span data-stu-id="fc449-104">Getting started with UWP app development on Xbox One</span></span>

<span data-ttu-id="fc449-105">Führen Sie die folgenden Schritte **sorgfältig** aus, um Ihren PC und Xbox One erfolgreich für die Entwicklung für die Universelle Windows-Plattform einzurichten.</span><span class="sxs-lookup"><span data-stu-id="fc449-105">**Carefully** follow these steps to successfully set up your PC and Xbox One for Universal Windows Platform (UWP) development.</span></span> <span data-ttu-id="fc449-106">Lesen Sie nach der Einrichtung die Seite [UWP für Xbox One](index.md), um mehr über den Entwicklermodus auf Xbox One und das Erstellen von UWP-Apps zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="fc449-106">After you’ve got things set up, you can learn more about Developer Mode on Xbox One and building UWP apps on the [UWP for Xbox One](index.md) page.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="fc449-107">Vorbereitung</span><span class="sxs-lookup"><span data-stu-id="fc449-107">Before you start</span></span>

<span data-ttu-id="fc449-108">Bevor Sie beginnen, müssen Sie die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="fc449-108">Before you start you will need to do the following:</span></span>
-   <span data-ttu-id="fc449-109">Richten Sie einen PC mit der neuesten Version von Windows 10.</span><span class="sxs-lookup"><span data-stu-id="fc449-109">Set up a PC with the latest version of Windows 10.</span></span>
<!-- -  Install Microsoft Visual Studio 2015 Update 3 or Microsoft Visual Studio 2017.

    > [!NOTE]
    > Visual Studio 2017 is required if you are using the Windows 10, build 15063 SDK. -->

- <span data-ttu-id="fc449-110">Sorgen Sie für mindestens 5GB freien Speicherplatz auf Ihrer Xbox One.</span><span class="sxs-lookup"><span data-stu-id="fc449-110">Have at least five gigabytes of free space on your Xbox One console.</span></span>

## <a name="setting-up-your-development-pc"></a><span data-ttu-id="fc449-111">Einrichten des Entwicklungs-PCs</span><span class="sxs-lookup"><span data-stu-id="fc449-111">Setting up your development PC</span></span>

1.  <span data-ttu-id="fc449-112">Installieren Sie Visual Studio 2015 Update 3 oder Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="fc449-112">Install Visual Studio 2015 Update 3 or Visual Studio 2017.</span></span>

    <span data-ttu-id="fc449-113">Wenn Sie Visual Studio 2015 Update 3 installieren, stellen Sie sicher, dass Sie **benutzerdefinierte** Installation auswählen und aktivieren Sie das Kontrollkästchen **Entwicklungstools für universelle Windows App** – es nicht Teil der Standardinstallation ist.</span><span class="sxs-lookup"><span data-stu-id="fc449-113">If you're installing Visual Studio 2015 Update 3, make sure that you choose **Custom** install and select the **Universal Windows App Development Tools** check box – it's not part of the default install.</span></span> <span data-ttu-id="fc449-114">Achten Sie als C++-Entwickler darauf, **Benutzerdefinierte Installation** auszuwählen. Wählen Sie **C++** aus.</span><span class="sxs-lookup"><span data-stu-id="fc449-114">If you are a C++ developer, make sure that you choose **Custom install** and select **C++**.</span></span>

    <span data-ttu-id="fc449-115">Wenn Sie Visual Studio2017 erneut installieren, stellen Sie sicher, dass Sie die Arbeitsauslastung **Entwicklung für die universelle Windows-Plattform** auswählen.</span><span class="sxs-lookup"><span data-stu-id="fc449-115">If you're installing Visual Studio 2017, make sure that you choose the **Universal Windows Platform development** workload.</span></span> <span data-ttu-id="fc449-116">Wenn Sie ein C++-Entwickler im Bereich " **Zusammenfassung** " auf der rechten Seite sind in der **Entwicklung von universellen Windows-Plattform**, stellen Sie sicher, dass Sie das Kontrollkästchen " **C++ universelle Windows-Plattform-Tools** " auswählen.</span><span class="sxs-lookup"><span data-stu-id="fc449-116">If you're a C++ developer, in the **Summary** pane on the right, under **Universal Windows Platform development**, make sure that you select the **C++ Universal Windows Platform tools** checkbox.</span></span> <span data-ttu-id="fc449-117">Es ist nicht Teil der Standardinstallation.</span><span class="sxs-lookup"><span data-stu-id="fc449-117">It's not part of the default install.</span></span>

    <span data-ttu-id="fc449-118">Weitere Informationen finden Sie in der [Einrichten Ihrer UWP-Entwicklungsumgebung auf Xbox](development-environment-setup.md).</span><span class="sxs-lookup"><span data-stu-id="fc449-118">For more information, see [Set up your UWP on Xbox development environment](development-environment-setup.md).</span></span>

2.  <span data-ttu-id="fc449-119">Installieren Sie das neueste [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="fc449-119">Install the latest [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

3.  <span data-ttu-id="fc449-120">Aktivieren des Entwicklermodus für Ihren Entwicklungs-PC (**Einstellungen / Update und Sicherheit / für Entwickler / verwenden von Entwicklerfeatures / Entwicklermodus**).</span><span class="sxs-lookup"><span data-stu-id="fc449-120">Enable Developer Mode for your development PC (**Settings / Update & Security / For developers / Use developer features / Developer mode**).</span></span>

<span data-ttu-id="fc449-121">Nachdem Ihr Entwicklungs-PC nun bereit ist, können Sie sich dieses Video ansehen oder weiterlesen, um zu erfahren, wie Sie Ihre Xbox One für die Entwicklung einrichten und darauf eine UWP-App erstellen und bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="fc449-121">Now that your development PC is ready, you can watch this video or continue reading to see how to set up your Xbox One for development and create and deploy a UWP app to it.</span></span>
</br>
</br>
<iframe src="https://channel9.msdn.com/Events/Xbox/App-Dev-on-Xbox/Get-started-with-App-Dev-on-Xbox/player#time=51s:paused" width="600" height="338"  allowFullScreen frameBorder="0"></iframe>

## <a name="setting-up-your-xbox-one-console"></a><span data-ttu-id="fc449-122">Einrichten Ihrer Xbox One-Konsole</span><span class="sxs-lookup"><span data-stu-id="fc449-122">Setting up your Xbox One console</span></span>

1.  <span data-ttu-id="fc449-123">Aktivieren Sie den Entwicklermodus auf der Xbox One.</span><span class="sxs-lookup"><span data-stu-id="fc449-123">Activate Developer Mode on your Xbox One.</span></span> <span data-ttu-id="fc449-124">Herunterladen Sie die app, erhalten Sie den Aktivierungscode, und geben sie dann in der Seite " [Verwalten von Xbox One-Konsolen](https://partner.microsoft.com/xboxactivate) " in Ihrem Dev Center-Konto.</span><span class="sxs-lookup"><span data-stu-id="fc449-124">Download the app, get the activation code, and then enter it into the [Manage Xbox One consoles](https://partner.microsoft.com/xboxactivate) page in your Dev Center account.</span></span> <span data-ttu-id="fc449-125">Weitere Informationen finden Sie unter [Aktivierung des Xbox One-Entwicklermodus](devkit-activation.md).</span><span class="sxs-lookup"><span data-stu-id="fc449-125">For more information, see [Xbox One Developer Mode activation](devkit-activation.md).</span></span> 

2.  <span data-ttu-id="fc449-126">Öffnen Sie die **DEVMODE-Aktivierungs** -app zu, und wählen Sie **wechseln und neu starten**.</span><span class="sxs-lookup"><span data-stu-id="fc449-126">Open the **Dev Mode Activation** app and select **Switch and restart**.</span></span> <span data-ttu-id="fc449-127">Herzlichen Glückwunsch! Ihre Xbox One befindet sich nun im Entwicklermodus.</span><span class="sxs-lookup"><span data-stu-id="fc449-127">Congratulations, you now have an Xbox One in Developer Mode!</span></span>
  
  > [!NOTE]
  > <span data-ttu-id="fc449-128">Ihre Einzelhandelsspiele und -Apps werden im Entwicklermodus nicht ausgeführt, die von Ihnen erstellten Apps oder Spiele werden jedoch ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="fc449-128">Your retail games and apps won’t run in Developer Mode, but the apps or games you create will.</span></span> <span data-ttu-id="fc449-129">Wechseln Sie zurück in den Einzelhandelsmodus, um Ihre Lieblingsspiele und -Apps auszuführen.</span><span class="sxs-lookup"><span data-stu-id="fc449-129">Switch back to Retail Mode to run your favorite games and apps.</span></span>
    
  > [!NOTE]
  > <span data-ttu-id="fc449-130">Damit Sie eine App auf der Xbox One-Konsole im Entwicklermodus bereitstellen können, muss ein Benutzer an der Konsole angemeldet sein.</span><span class="sxs-lookup"><span data-stu-id="fc449-130">Before you can deploy an app to your Xbox One in Developer Mode, you must have a user signed in on the console.</span></span> <span data-ttu-id="fc449-131">Sie können entweder ein vorhandenes Xbox Live-Konto verwenden oder ein neues Konto für Ihre Konsole im Entwicklermodus erstellen.</span><span class="sxs-lookup"><span data-stu-id="fc449-131">You can either use your existing Xbox Live account or create a new account for your console in Developer Mode.</span></span> 

## <a name="creating-your-first-project-in-visual-studio"></a><span data-ttu-id="fc449-132">Erstellen Ihres ersten Projekts in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fc449-132">Creating your first project in Visual Studio</span></span>

<span data-ttu-id="fc449-133">Ausführlichere Informationen finden Sie unter [Einrichten Ihrer UWP-Entwicklungsumgebung auf Xbox](development-environment-setup.md).</span><span class="sxs-lookup"><span data-stu-id="fc449-133">For more detailed information, see [Set up your UWP on Xbox development environment](development-environment-setup.md).</span></span>

1.  <span data-ttu-id="fc449-134">**Für c#**: Erstellen eines neuen universellen Windows-Projekts, und klicken Sie im **Projektmappen-Explorer**mit der Maustaste des Projekts und wählen Sie **Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="fc449-134">**For C#**: Create a new Universal Windows project, and in the **Solution Explorer**, right-click the project and select **Properties**.</span></span> <span data-ttu-id="fc449-135">Wählen Sie die Registerkarte " **Debuggen** ", ändern Sie **Zielgerät** auf **Remotecomputer**zu, geben Sie die IP-Adresse oder den Hostnamen der Xbox One-Konsole in das Feld **Remotecomputer** , und wählen Sie **universell (unverschlüsseltes Protokoll)** in der \*\* Authentifizierungsmodus\*\* Dropdown-Liste.</span><span class="sxs-lookup"><span data-stu-id="fc449-135">Select the **Debug** tab, change **Target device** to **Remote Machine**, type the IP address or hostname of your Xbox One console into the **Remote machine** field, and select **Universal (Unencrypted Protocol)** in the **Authentication Mode** drop-down list.</span></span>   

    <span data-ttu-id="fc449-136">Die IP-Adresse Ihrer Xbox One finden Sie, indem Sie Dev Home auf der Konsole starten (die große Kachel auf der rechten Seite der Startseite) und in der oberen linken Ecke suchen.</span><span class="sxs-lookup"><span data-stu-id="fc449-136">You can find your Xbox One IP address by starting Dev Home on your console (the big tile on the right side of Home) and looking at the top left corner.</span></span> <span data-ttu-id="fc449-137">Weitere Informationen zu Dev Home finden Sie unter [Einführung in Xbox One-Tools](introduction-to-xbox-tools.md).</span><span class="sxs-lookup"><span data-stu-id="fc449-137">For more information about Dev Home, see [Introduction to Xbox One tools](introduction-to-xbox-tools.md).</span></span>  

2.  <span data-ttu-id="fc449-138">**Für C++ und HTML/Javascript-Projekte**: Sie folgen einen ähnlichen Pfad zu C#-Projekten, aber in den Projekteigenschaften finden Sie unter der Registerkarte " **Debuggen** ", wählen Sie **Remotecomputer** in den Debugger so öffnen Sie die Dropdown-Liste, geben Sie die IP-Adresse oder den Hostnamen der die die Konsole in den **Computernamen ein** Feld und wählen **universell (unverschlüsseltes Protokoll)** im Feld **Authentifizierungstyp** .</span><span class="sxs-lookup"><span data-stu-id="fc449-138">**For C++ and HTML/Javascript projects**: You follow a path similar to C# projects, but in the project properties go to the **Debugging** tab, select **Remote Machine** in the Debugger to open the drop-down list, type the IP address or hostname of the console into the **Machine Name** field, and select **Universal (Unencrypted Protocol)** in the **Authentication Type** field.</span></span>

3. <span data-ttu-id="fc449-139">Wählen Sie **X64** aus der Dropdown-Liste auf der linken Seite des die grüne Wiedergabeschaltfläche in der oberen Menüleiste.</span><span class="sxs-lookup"><span data-stu-id="fc449-139">Select **x64** from the dropdown to the left of the green play button in the top menu bar.</span></span>
   
4.  <span data-ttu-id="fc449-140">Wenn Sie F5 drücken, wird Ihre App erstellt, und die Bereitstellung auf der Xbox One wird gestartet.</span><span class="sxs-lookup"><span data-stu-id="fc449-140">When you press F5, your app will build and start to deploy on your Xbox One.</span></span>
  
5.  <span data-ttu-id="fc449-141">Wenn Sie diesen Vorgang zum ersten Mal durchführen, fordert Visual Studio Sie zur Eingabe einer PIN für Ihre Xbox One auf.</span><span class="sxs-lookup"><span data-stu-id="fc449-141">The first time you do this, Visual Studio will prompt you for a PIN for your Xbox One.</span></span> <span data-ttu-id="fc449-142">Indem Sie Dev Home auf Ihrer Xbox One starten und die Schaltfläche " **Visual Studio-Pin anzeigen** " auswählen, können Sie eine PIN abrufen.</span><span class="sxs-lookup"><span data-stu-id="fc449-142">You can get a PIN by starting Dev Home on your Xbox One and selecting the **Show Visual Studio pin** button.</span></span>
  
6.  <span data-ttu-id="fc449-143">Nach der Kopplung wird die Bereitstellung der App gestartet.</span><span class="sxs-lookup"><span data-stu-id="fc449-143">After you have paired, your app will start to deploy.</span></span> <span data-ttu-id="fc449-144">Beim ersten Mal kann diese Bereitstellung ein wenig langsam sein (da alle Tools auf Ihre Xbox kopiert werden müssen). Wenn dieser Vorgang jedoch länger als wenige Minuten dauert, ist wahrscheinlich ein Problem aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="fc449-144">The first time you do this it might be a bit slow (we have to copy all the tools over to your Xbox), but if it takes more than a few minutes, something is probably wrong.</span></span> <span data-ttu-id="fc449-145">Stellen Sie sicher, dass Sie alle oben genannten Schritte ausgeführt haben – haben Sie den **Authentifizierungsmodus** auf **Universell** festgelegt? Vergewissern Sie sich außerdem, dass Sie eine drahtgebundene Netzwerkverbindung mit der Xbox One verwenden.</span><span class="sxs-lookup"><span data-stu-id="fc449-145">Make sure that you have followed all of the steps above (particularly, did you set the **Authentication Mode** to **Universal**?) and that you are using a wired network connection to your Xbox One.</span></span>  

7. <span data-ttu-id="fc449-146">Lehnen Sie sich nun ganz entspannt zurück.</span><span class="sxs-lookup"><span data-stu-id="fc449-146">Sit back and relax.</span></span> <span data-ttu-id="fc449-147">Viel Spaß mit Ihrer ersten App auf der Konsole!</span><span class="sxs-lookup"><span data-stu-id="fc449-147">Enjoy your first app running on the console!</span></span>  

## <a name="thats-it"></a><span data-ttu-id="fc449-148">Das war's.</span><span class="sxs-lookup"><span data-stu-id="fc449-148">That's it!</span></span>

![Hello World](images/getting-started-hello-world.png)

## <a name="see-also"></a><span data-ttu-id="fc449-150">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="fc449-150">See also</span></span>  
- [<span data-ttu-id="fc449-151">Häufig gestellte Fragen</span><span class="sxs-lookup"><span data-stu-id="fc449-151">Frequently asked questions</span></span>](frequently-asked-questions.md)  
- [<span data-ttu-id="fc449-152">Bekannte Probleme mit UWP im Zusammenhang mit dem Xbox One-Entwicklerprogramm</span><span class="sxs-lookup"><span data-stu-id="fc449-152">Known issues with UWP on Xbox Developer Program</span></span>](known-issues.md)
- [<span data-ttu-id="fc449-153">UWP auf Xbox One</span><span class="sxs-lookup"><span data-stu-id="fc449-153">UWP on Xbox One</span></span>](index.md) 
