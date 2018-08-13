---
author: Mtoepke
title: Erste Schritte bei der Entwicklung von UWP-Apps auf Xbox One
description: Einrichten des Computers und der Xbox One für die UWP-Entwicklung
ms.author: mtoepke
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: ea8262f0aad4112ce2ce6d661156f5692541a4ce
ms.sourcegitcommit: de6bc8acec2cd5ebc36bb21b2ce1a9980c3e78b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2017
ms.locfileid: "901000"
---
#<a name="getting-started-with-uwp-app-development-on-xbox-one"></a><span data-ttu-id="f7210-104">Erste Schritte bei der Entwicklung von UWP-Apps auf Xbox One</span><span class="sxs-lookup"><span data-stu-id="f7210-104">Getting started with UWP app development on Xbox One</span></span>

<span data-ttu-id="f7210-105">Führen Sie die folgenden Schritte **sorgfältig** aus, um Ihren PC und Xbox One erfolgreich für die Entwicklung für die Universelle Windows-Plattform einzurichten.</span><span class="sxs-lookup"><span data-stu-id="f7210-105">**Carefully** follow these steps to successfully set up your PC and Xbox One for Universal Windows Platform (UWP) development.</span></span> <span data-ttu-id="f7210-106">Lesen Sie nach der Einrichtung die Seite [UWP für Xbox One](index.md), um mehr über den Entwicklermodus auf Xbox One und das Erstellen von UWP-Apps zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="f7210-106">After you’ve got things set up, you can learn more about Developer Mode on Xbox One and building UWP apps on the [UWP for Xbox One](index.md) page.</span></span> 

## <a name="before-you-start"></a><span data-ttu-id="f7210-107">Vorbereitung</span><span class="sxs-lookup"><span data-stu-id="f7210-107">Before you start</span></span>
<span data-ttu-id="f7210-108">Bevor Sie beginnen, müssen Sie die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="f7210-108">Before you start you will need to do the following:</span></span>
-   <span data-ttu-id="f7210-109">Richten Sie einen PC mit Windows10 ein.</span><span class="sxs-lookup"><span data-stu-id="f7210-109">Set up a PC with Windows 10.</span></span>
-   <span data-ttu-id="f7210-110">Installieren Sie Microsoft Visual Studio 2015 Update 3.</span><span class="sxs-lookup"><span data-stu-id="f7210-110">Install Microsoft Visual Studio 2015 Update 3.</span></span>
- <span data-ttu-id="f7210-111">Sorgen Sie für mindestens 5GB freien Speicherplatz auf Ihrer Xbox One.</span><span class="sxs-lookup"><span data-stu-id="f7210-111">Have at least five gigabytes of free space on your Xbox One console.</span></span>

## <a name="setting-up-your-development-pc"></a><span data-ttu-id="f7210-112">Einrichten des Entwicklungs-PCs</span><span class="sxs-lookup"><span data-stu-id="f7210-112">Setting up your development PC</span></span>
1.  <span data-ttu-id="f7210-113">Installieren Sie Visual Studio 2015 Update.</span><span class="sxs-lookup"><span data-stu-id="f7210-113">Install Visual Studio 2015 Update.</span></span> <span data-ttu-id="f7210-114">Wählen Sie die **benutzerdefinierte** Installation aus, und aktivieren Sie das Kontrollkästchen **Entwicklungstools für universelle Windows-Apps** (dieses gehört nicht zur standardmäßigen Installation).</span><span class="sxs-lookup"><span data-stu-id="f7210-114">Make sure that you choose **Custom** install and select the **Universal Windows App Development Tools** check box – it's not part of the default install.</span></span> <span data-ttu-id="f7210-115">Achten Sie als C++-Entwickler darauf, **Benutzerdefinierte Installation** auszuwählen. Wählen Sie **C++** aus.</span><span class="sxs-lookup"><span data-stu-id="f7210-115">If you are a C++ developer, make sure that you choose **Custom install** and select **C++**.</span></span> <span data-ttu-id="f7210-116">Weitere Informationen finden Sie unter [Einrichtung der Entwicklungsumgebung](development-environment-setup.md).</span><span class="sxs-lookup"><span data-stu-id="f7210-116">For more information, see [Development environment setup](development-environment-setup.md).</span></span> 

2.  <span data-ttu-id="f7210-117">Installieren Sie das aktuelle Windows10 SDK.</span><span class="sxs-lookup"><span data-stu-id="f7210-117">Install the latest Windows 10 SDK.</span></span> <span data-ttu-id="f7210-118">Dieses können Sie unter [https://developer.microsoft.com/windows/downloads/windows-10-sdk](https://developer.microsoft.com/windows/downloads/windows-10-sdk) abrufen.</span><span class="sxs-lookup"><span data-stu-id="f7210-118">You can get this from [https://developer.microsoft.com/windows/downloads/windows-10-sdk](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

3.  <span data-ttu-id="f7210-119">Aktivieren Sie den Entwicklermodus für Ihren Entwicklungs-PC (Einstellungen > Update und Sicherheit > Für Entwickler > Entwicklermodus).</span><span class="sxs-lookup"><span data-stu-id="f7210-119">Enable Developer Mode for your development PC (Settings / Update & security / For developers / Developer mode).</span></span>


<span data-ttu-id="f7210-120">Nachdem Ihr Entwicklungs-PC nun bereit ist, können Sie sich dieses Video ansehen oder weiterlesen, um zu erfahren, wie Sie Ihre Xbox One für die Entwicklung einrichten und darauf eine UWP-App erstellen und bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="f7210-120">Now that your development PC is ready, you can watch this video or continue reading to see how to set up your Xbox One for development and create and deploy a UWP app to it.</span></span>
</br>
</br>
<iframe src="https://channel9.msdn.com/Events/Xbox/App-Dev-on-Xbox/Get-started-with-App-Dev-on-Xbox/player#time=51s:paused" width="600" height="338"  allowFullScreen frameBorder="0"></iframe>

## <a name="setting-up-your-xbox-one-console"></a><span data-ttu-id="f7210-121">Einrichten Ihrer Xbox One-Konsole</span><span class="sxs-lookup"><span data-stu-id="f7210-121">Setting up your Xbox One console</span></span>

1.  <span data-ttu-id="f7210-122">Aktivieren Sie den Entwicklermodus auf der Xbox One.</span><span class="sxs-lookup"><span data-stu-id="f7210-122">Activate Developer Mode on your Xbox One.</span></span> <span data-ttu-id="f7210-123">Laden Sie die App herunter, und geben Sie dann den erhaltenen Aktivierungscode im Dev Center-Konto auf der xboxactivate-Seite ein.</span><span class="sxs-lookup"><span data-stu-id="f7210-123">Download the app, get the activation code, and then enter it into the xboxactivate page in your Dev Center account.</span></span> <span data-ttu-id="f7210-124">Weitere Informationen finden Sie unter [Aktivieren des Entwicklermodus auf Xbox One](devkit-activation.md).</span><span class="sxs-lookup"><span data-stu-id="f7210-124">For more information, see [Enabling Developer Mode on Xbox One](devkit-activation.md).</span></span> 

2.  <span data-ttu-id="f7210-125">Öffnen Sie die DevMode-Aktivierungsapp, und wählen Sie **Wechseln und neu starten** aus.</span><span class="sxs-lookup"><span data-stu-id="f7210-125">Go into the Dev Mode Activation app and select **Switch and restart**.</span></span> <span data-ttu-id="f7210-126">Herzlichen Glückwunsch! Ihre Xbox One befindet sich nun im Entwicklermodus.</span><span class="sxs-lookup"><span data-stu-id="f7210-126">Congratulations, you now have an Xbox One in Developer Mode!</span></span>
  
  > [!NOTE]
  > <span data-ttu-id="f7210-127">Ihre Einzelhandelsspiele und -Apps werden im Entwicklermodus nicht ausgeführt, die von Ihnen erstellten Apps oder Spiele werden jedoch ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="f7210-127">Your retail games and apps won’t run in Developer Mode, but the apps or games you create will.</span></span> <span data-ttu-id="f7210-128">Wechseln Sie zurück in den Einzelhandelsmodus, um Ihre Lieblingsspiele und -Apps auszuführen.</span><span class="sxs-lookup"><span data-stu-id="f7210-128">Switch back to Retail Mode to run your favorite games and apps.</span></span>
    
  > [!NOTE]
  > <span data-ttu-id="f7210-129">Damit Sie eine App auf der Xbox One-Konsole im Entwicklermodus bereitstellen können, muss ein Benutzer an der Konsole angemeldet sein.</span><span class="sxs-lookup"><span data-stu-id="f7210-129">Before you can deploy an app to your Xbox One in Developer Mode, you must have a user signed in on the console.</span></span> <span data-ttu-id="f7210-130">Sie können entweder ein vorhandenes Xbox Live-Konto verwenden oder ein neues Konto für Ihre Konsole im Entwicklermodus erstellen.</span><span class="sxs-lookup"><span data-stu-id="f7210-130">You can either use your existing Xbox Live account or create a new account for your console in Developer Mode.</span></span> 

## <a name="creating-your-first-project-in-visual-studio-2015"></a><span data-ttu-id="f7210-131">Erstellen Ihres ersten Projekts in Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="f7210-131">Creating your first project in Visual Studio 2015</span></span>

<span data-ttu-id="f7210-132">Ausführliche Informationen finden Sie unter [Einrichtung der Entwicklungsumgebung](development-environment-setup.md).</span><span class="sxs-lookup"><span data-stu-id="f7210-132">For more detailed information, see [Development environment setup](development-environment-setup.md).</span></span>

1.  <span data-ttu-id="f7210-133">**Für C#**: Erstellen Sie ein neues universelles Windows-Projekt, öffnen Sie die Projekteigenschaften, und wählen Sie die Registerkarte **Debuggen** aus. Ändern Sie **Zielgerät** in **Remotecomputer**, geben Sie die IP-Adresse oder den Hostnamen Ihrer Xbox One im Feld **Remotecomputer** ein, und wählen Sie die Option **Universell (unverschlüsseltes Protokoll)** in der Dropdownliste **Authentifizierungsmodus** aus.</span><span class="sxs-lookup"><span data-stu-id="f7210-133">**For C#**: Create a new Universal Windows project, go into the project properties and select the **Debug** tab, change **Target device** to **Remote Machine**, type the IP address or hostname of your Xbox One console into the **Remote machine** field, and select **Universal (Unencrypted Protocol)** in the **Authentication Mode** drop-down list.</span></span>   

    <span data-ttu-id="f7210-134">Die IP-Adresse Ihrer Xbox One finden Sie, indem Sie Dev Home auf der Konsole starten (die große Kachel auf der rechten Seite der Startseite) und in der oberen linken Ecke suchen.</span><span class="sxs-lookup"><span data-stu-id="f7210-134">You can find your Xbox One IP address by starting Dev Home on your console (the big tile on the right side of Home) and looking at the top left corner.</span></span> <span data-ttu-id="f7210-135">Weitere Informationen zu Dev Home finden Sie unter [Einführung in Xbox One-Tools](introduction-to-xbox-tools.md).</span><span class="sxs-lookup"><span data-stu-id="f7210-135">For more information about Dev Home, see [Introduction to Xbox One tools](introduction-to-xbox-tools.md).</span></span>  

2.  <span data-ttu-id="f7210-136">**Für C++- und HTML-/Javascript-Projekte**: Sie folgen einem ähnlichen Pfad, wechseln aber in den Projekteigenschaften zur Registerkarte **Debuggen**, wählen die Option **Remotecomputer** aus, um die Dropdownliste zu öffnen, geben die IP-Adresse oder den Hostnamen der Konsole im Feld **Computername** ein, und wählen die Option **Universell (unverschlüsseltes Protokoll)** im Feld **Authentifizierungstyp** aus.</span><span class="sxs-lookup"><span data-stu-id="f7210-136">**For C++ and HTML/Javascript projects**:  You follow a similar path, but in project properties go to the **Debugging** tab, select **Remote Machine** in the Debugger to open the drop-down list, type the IP address or hostname of the console into the **Machine Name** field, and select **Universal (Unencrypted Protocol)** in the **Authentication Type** field.</span></span>
   
3.  <span data-ttu-id="f7210-137">Wenn Sie F5 drücken, wird Ihre App erstellt, und die Bereitstellung auf der Xbox One wird gestartet.</span><span class="sxs-lookup"><span data-stu-id="f7210-137">When you press F5, your app will build and start to deploy on your Xbox One.</span></span>
  
4.  <span data-ttu-id="f7210-138">Wenn Sie diesen Vorgang zum ersten Mal durchführen, fordert Visual Studio Sie zur Eingabe einer PIN für Ihre Xbox One auf.</span><span class="sxs-lookup"><span data-stu-id="f7210-138">The first time you do this, Visual Studio will prompt you for a PIN for your Xbox One.</span></span> <span data-ttu-id="f7210-139">Eine PIN erhalten Sie, indem Sie Dev Home auf der Xbox One starten und die Schaltfläche **Mit Visual Studio koppeln** auswählen.</span><span class="sxs-lookup"><span data-stu-id="f7210-139">You can get a PIN by starting Dev Home on your Xbox One and selecting the **Pair with Visual Studio** button.</span></span>
  
5.  <span data-ttu-id="f7210-140">Nach der Kopplung wird die Bereitstellung der App gestartet.</span><span class="sxs-lookup"><span data-stu-id="f7210-140">After you have paired, your app will start to deploy.</span></span> <span data-ttu-id="f7210-141">Beim ersten Mal kann diese Bereitstellung ein wenig langsam sein (da alle Tools auf Ihre Xbox kopiert werden müssen). Wenn dieser Vorgang jedoch länger als wenige Minuten dauert, ist wahrscheinlich ein Problem aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="f7210-141">The first time you do this it might be a bit slow (we have to copy all the tools over to your Xbox), but if it takes more than a few minutes, something is probably wrong.</span></span> <span data-ttu-id="f7210-142">Stellen Sie sicher, dass Sie alle oben genannten Schritte ausgeführt haben – haben Sie den **Authentifizierungsmodus** auf **Universell** festgelegt? Vergewissern Sie sich außerdem, dass Sie eine drahtgebundene Netzwerkverbindung mit der Xbox One verwenden.</span><span class="sxs-lookup"><span data-stu-id="f7210-142">Make sure that you have followed all of the steps above (particularly, did you set the **Authentication Mode** to **Universal**?) and that you are using a wired network connection to your Xbox One.</span></span>  

6. <span data-ttu-id="f7210-143">Lehnen Sie sich nun ganz entspannt zurück.</span><span class="sxs-lookup"><span data-stu-id="f7210-143">Sit back and relax.</span></span> <span data-ttu-id="f7210-144">Viel Spaß mit Ihrer ersten App auf der Konsole!</span><span class="sxs-lookup"><span data-stu-id="f7210-144">Enjoy your first app running on the console!</span></span>  

## <a name="thats-it"></a><span data-ttu-id="f7210-145">Das war's.</span><span class="sxs-lookup"><span data-stu-id="f7210-145">That's it!</span></span>

![Hello World](images/getting-started-hello-world.png)

## <a name="see-also"></a><span data-ttu-id="f7210-147">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f7210-147">See also</span></span>  
- [<span data-ttu-id="f7210-148">FAQ</span><span class="sxs-lookup"><span data-stu-id="f7210-148">FAQ</span></span>](frequently-asked-questions.md)  
- [<span data-ttu-id="f7210-149">Bekannte Probleme</span><span class="sxs-lookup"><span data-stu-id="f7210-149">Known issues</span></span>](known-issues.md)
- [<span data-ttu-id="f7210-150">UWP auf XboxOne</span><span class="sxs-lookup"><span data-stu-id="f7210-150">UWP on Xbox One</span></span>](index.md) 
