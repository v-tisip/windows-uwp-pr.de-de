---
title: Freigabe von Zertifikaten zwischen Apps
description: UWP-Apps, die über eine Kombination aus Benutzer-ID und Kennwort hinaus eine sichere Authentifizierung benötigen, können Zertifikate für die Authentifizierung verwenden.
ms.assetid: 159BA284-9FD4-441A-BB45-A00E36A386F9
author: PatrickFarley
ms.author: pafarley
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Sicherheit
ms.localizationpriority: medium
ms.openlocfilehash: 863658438ce53f2c74faddb845a7d17c6ec3130c
ms.sourcegitcommit: 00d27738325d6db5b5e481911ae7fac0711b05eb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2018
ms.locfileid: "3660340"
---
# <a name="share-certificates-between-apps"></a><span data-ttu-id="6c08e-104">Freigabe von Zertifikaten zwischen Apps</span><span class="sxs-lookup"><span data-stu-id="6c08e-104">Share certificates between apps</span></span>




<span data-ttu-id="6c08e-105">UWP-Apps, die über eine Kombination aus Benutzer-ID und Kennwort hinaus eine sichere Authentifizierung benötigen, können Zertifikate für die Authentifizierung verwenden.</span><span class="sxs-lookup"><span data-stu-id="6c08e-105">Universal Windows Platform (UWP) apps that require secure authentication beyond a user Id and password combination can use certificates for authentication.</span></span> <span data-ttu-id="6c08e-106">Die Zertifikatauthentifizierung bietet eine hohe Vertrauenswürdigkeit bei der Benutzerauthentifizierung.</span><span class="sxs-lookup"><span data-stu-id="6c08e-106">Certificate authentication provides a high level of trust when authenticating a user.</span></span> <span data-ttu-id="6c08e-107">Es kann vorkommen, dass eine Gruppe von Diensten einen Benutzer für mehrere Apps authentifizieren möchte.</span><span class="sxs-lookup"><span data-stu-id="6c08e-107">In some cases, a group of services will want to authenticate a user for multiple apps.</span></span> <span data-ttu-id="6c08e-108">In diesem Artikel wird veranschaulicht, wie Sie mehrere Apps mit demselben Zertifikat authentifizieren und für einen Benutzer geeigneten Code zum Importieren eines Zertifikats bereitstellen können, das für den Zugriff auf sichere Webdienste bestimmt ist.</span><span class="sxs-lookup"><span data-stu-id="6c08e-108">This article shows how you can authenticate multiple apps using the same certificate, and how you can provide convenient code for a user to import a certificate that was provided to access secured web services.</span></span>

<span data-ttu-id="6c08e-109">Apps können für die Authentifizierung bei einem Webdienst ein Zertifikat verwenden, und mehrere Apps können ein einzelnes Zertifikat aus dem Zertifikatspeicher verwenden, um denselben Benutzer zu authentifizieren.</span><span class="sxs-lookup"><span data-stu-id="6c08e-109">Apps can authenticate to a web service using a certificate, and multiple apps can use a single certificate from the certificate store to authenticate the same user.</span></span> <span data-ttu-id="6c08e-110">Falls im Speicher kein Zertifikat vorhanden ist, können Sie der App Code für den Import eines Zertifikats aus einer PFX-Datei hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="6c08e-110">If a certificate does not exist in the store, you can add code to your app to import a certificate from a PFX file.</span></span>

## <a name="enable-microsoft-internet-information-services-iis-and-client-certificate-mapping"></a><span data-ttu-id="6c08e-111">Aktivieren von Microsoft Internet Information Services (IIS) und Clientzertifikatszuordnungen</span><span class="sxs-lookup"><span data-stu-id="6c08e-111">Enable Microsoft Internet Information Services (IIS) and client certificate mapping</span></span>


<span data-ttu-id="6c08e-112">In diesem Artikel werden die Microsoft-Internetinformationsdienste (Microsoft Internet Information Services, IIS) als Beispiel verwendet.</span><span class="sxs-lookup"><span data-stu-id="6c08e-112">This article uses Microsoft Internet Information Services (IIS) for example purposes.</span></span> <span data-ttu-id="6c08e-113">IIS ist standardmäßig nicht aktiviert.</span><span class="sxs-lookup"><span data-stu-id="6c08e-113">IIS is not enabled by default.</span></span> <span data-ttu-id="6c08e-114">Sie können IIS über die Systemsteuerung aktivieren.</span><span class="sxs-lookup"><span data-stu-id="6c08e-114">You can enable IIS by using the Control Panel.</span></span>

1.  <span data-ttu-id="6c08e-115">Öffnen Sie die Systemsteuerung, und wählen Sie **Programme** aus.</span><span class="sxs-lookup"><span data-stu-id="6c08e-115">Open the Control Panel and select **Programs**.</span></span>
2.  <span data-ttu-id="6c08e-116">Wählen Sie die Option **Windows-Features aktivieren oder deaktivieren** aus.</span><span class="sxs-lookup"><span data-stu-id="6c08e-116">Select **Turn Windows features on or off**.</span></span>
3.  <span data-ttu-id="6c08e-117">Erweitern Sie **Internetinformationsdienste** und dann **WWW-Dienste**.</span><span class="sxs-lookup"><span data-stu-id="6c08e-117">Expand **Internet Information Services** and then expand **World Wide Web Services**.</span></span> <span data-ttu-id="6c08e-118">Erweitern Sie **Anwendungsentwicklungsfeatures**, und wählen Sie **ASP.NET3.5** und **ASP.NET4.5**.</span><span class="sxs-lookup"><span data-stu-id="6c08e-118">Expand **Application Development Features** and select **ASP.NET 3.5** and **ASP.NET 4.5**.</span></span> <span data-ttu-id="6c08e-119">Das Auswählen führt dazu, dass **Internetinformationsdienste** automatisch aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="6c08e-119">Making these selections will automatically enable **Internet Information Services**.</span></span>
4.  <span data-ttu-id="6c08e-120">Klicken Sie auf **OK**, um die Änderungen zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="6c08e-120">Click **OK** to apply the changes.</span></span>

## <a name="create-and-publish-a-secured-web-service"></a><span data-ttu-id="6c08e-121">Erstellen und Veröffentlichen eines sicheren Webdiensts</span><span class="sxs-lookup"><span data-stu-id="6c08e-121">Create and publish a secured web service</span></span>


1.  <span data-ttu-id="6c08e-122">Führen Sie Microsoft Visual Studio als Administrator aus, und wählen Sie auf der Startseite die Option **Neues Projekt** aus.</span><span class="sxs-lookup"><span data-stu-id="6c08e-122">Run Microsoft Visual Studio as administrator and select **New Project** from the start page.</span></span> <span data-ttu-id="6c08e-123">Für die Veröffentlichung eines Webdiensts auf einem IIS-Server ist Administratorzugriff erforderlich.</span><span class="sxs-lookup"><span data-stu-id="6c08e-123">Administrator access is required to publish a web service to an IIS server.</span></span> <span data-ttu-id="6c08e-124">Ändern Sie im Dialogfeld „Neues Projekt“ das Framework in **.NET Framework 3.5**.</span><span class="sxs-lookup"><span data-stu-id="6c08e-124">In the New Project dialog, change the framework to **.NET Framework 3.5**.</span></span> <span data-ttu-id="6c08e-125">Wählen Sie **Visual C#** -&gt; **Web** -&gt; **Visual Studio** -&gt; **ASP.NET-Webdienstanwendung** aus.</span><span class="sxs-lookup"><span data-stu-id="6c08e-125">Select **Visual C#** -&gt; **Web** -&gt; **Visual Studio** -&gt; **ASP.NET Web Service Application**.</span></span> <span data-ttu-id="6c08e-126">Geben Sie der Anwendung den Namen „FirstContosoBank“.</span><span class="sxs-lookup"><span data-stu-id="6c08e-126">Name the application "FirstContosoBank".</span></span> <span data-ttu-id="6c08e-127">Klicken Sie auf **OK**, um das Projekt zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="6c08e-127">Click **OK** to create the project.</span></span>
2.  <span data-ttu-id="6c08e-128">Ersetzen Sie in der Datei **Service1.asmx.cs** die standardmäßige Webmethode **HelloWorld** durch die folgende "Login"-Methode.</span><span class="sxs-lookup"><span data-stu-id="6c08e-128">In the **Service1.asmx.cs** file, replace the default **HelloWorld** web method with the following "Login" method.</span></span>
    ```cs
            [WebMethod]
            public string Login()
            {
                // Verify certificate with CA
                var cert = new System.Security.Cryptography.X509Certificates.X509Certificate2(
                    this.Context.Request.ClientCertificate.Certificate);
                bool test = cert.Verify();
                return test.ToString();
            }
    ```

3.  <span data-ttu-id="6c08e-129">Speichern Sie die Datei **Service1.asmx.cs**.</span><span class="sxs-lookup"><span data-stu-id="6c08e-129">Save the **Service1.asmx.cs** file.</span></span>
4.  <span data-ttu-id="6c08e-130">Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die App "FirstContosoBank", und wählen Sie **Veröffentlichen**.</span><span class="sxs-lookup"><span data-stu-id="6c08e-130">In the **Solution Explorer**, right-click the "FirstContosoBank" app and select **Publish**.</span></span>
5.  <span data-ttu-id="6c08e-131">Erstellen Sie im Dialogfeld **Web veröffentlichen** ein neues Profil, und geben Sie ihm den Namen "ContosoProfile".</span><span class="sxs-lookup"><span data-stu-id="6c08e-131">In the **Publish Web** dialog, create a new profile and name it "ContosoProfile".</span></span> <span data-ttu-id="6c08e-132">Klicken Sie auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="6c08e-132">Click **Next.**</span></span>
6.  <span data-ttu-id="6c08e-133">Geben Sie auf der nächsten Seite den Servernamen für Ihren IIS-Server ein, und geben Sie dann den Websitenamen "Standardwebsite/FirstContosoBank" an.</span><span class="sxs-lookup"><span data-stu-id="6c08e-133">On the next page, enter the server name for your IIS server, and specify a site name of "Default Web Site/FirstContosoBank".</span></span> <span data-ttu-id="6c08e-134">Klicken Sie auf **Veröffentlichen**, um den Webdienst zu veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="6c08e-134">Click **Publish** to publish your web service.</span></span>

## <a name="configure-your-web-service-to-use-client-certificate-authentication"></a><span data-ttu-id="6c08e-135">Konfigurieren des Webdiensts für die Verwendung der Clientzertifikatauthentifizierung</span><span class="sxs-lookup"><span data-stu-id="6c08e-135">Configure your web service to use client certificate authentication</span></span>


1.  <span data-ttu-id="6c08e-136">Führen Sie den **Internetinformationsdienste (IIS)-Manager** aus.</span><span class="sxs-lookup"><span data-stu-id="6c08e-136">Run the **Internet Information Services (IIS) Manager**.</span></span>
2.  <span data-ttu-id="6c08e-137">Erweitern Sie die Websites für Ihren IIS-Server.</span><span class="sxs-lookup"><span data-stu-id="6c08e-137">Expand the sites for your IIS server.</span></span> <span data-ttu-id="6c08e-138">Wählen Sie unter **Standardwebsite** den neuen Webdienst "FirstContosoBank".</span><span class="sxs-lookup"><span data-stu-id="6c08e-138">Under the **Default Web Site**, select the new "FirstContosoBank" web service.</span></span> <span data-ttu-id="6c08e-139">Wählen Sie im Abschnitt **Aktionen** die Option **Erweiterte Einstellungen...**.</span><span class="sxs-lookup"><span data-stu-id="6c08e-139">In the **Actions** section, select **Advanced Settings...**.</span></span>
3.  <span data-ttu-id="6c08e-140">Legen Sie den **Anwendungspool** auf **.NET v2.0** fest, und klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="6c08e-140">Set the **Application Pool** to **.NET v2.0** and click **OK**.</span></span>
4.  <span data-ttu-id="6c08e-141">Wählen Sie im **Internetinformationsdienste (IIS)-Manager** Ihren IIS-Server aus, und doppelklicken Sie anschließend auf **Serverzertifikate**.</span><span class="sxs-lookup"><span data-stu-id="6c08e-141">In the **Internet Information Services (IIS) Manager**, select your IIS server and then double-click **Server Certificates**.</span></span> <span data-ttu-id="6c08e-142">Wählen Sie im Abschnitt **Aktionen** die Option **Selbstsigniertes Zertifikat erstellen...** aus. Geben Sie „ContosoBank“ als Anzeigenamen für das Zertifikat ein, und klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="6c08e-142">In the **Actions** section, select **Create Self-Signed Certificate...**. Enter "ContosoBank" as the friendly name for the certificate and click **OK**.</span></span> <span data-ttu-id="6c08e-143">Es wird ein neues Zertifikat zur Verwendung durch den IIS-Server im Format „&lt;Servername&gt;.&lt;Domänenname&gt;“ erstellt.</span><span class="sxs-lookup"><span data-stu-id="6c08e-143">This will create a new certificate for use by the IIS server in the form of "&lt;server-name&gt;.&lt;domain-name&gt;".</span></span>
5.  <span data-ttu-id="6c08e-144">Wählen Sie im **Internetinformationsdienste (IIS)-Manager** die Standardwebsite aus.</span><span class="sxs-lookup"><span data-stu-id="6c08e-144">In the **Internet Information Services (IIS) Manager**, select the default web site.</span></span> <span data-ttu-id="6c08e-145">Wählen Sie im Abschnitt **Aktionen** die Option **Bindung** aus, und klicken Sie dann auf **Hinzufügen...**. Wählen Sie als Typ „https“ aus, legen Sie den Port auf „443“ fest, und geben Sie den vollständigen Hostnamen für Ihren IIS-Server ein (&lt;Servername&gt;.&lt;Domänenname&gt;).</span><span class="sxs-lookup"><span data-stu-id="6c08e-145">In the **Actions** section, select **Binding** and then click **Add...**. Select "https" as the type, set the port to "443", and enter the full host name for your IIS server ("&lt;server-name&gt;.&lt;domain-name&gt;").</span></span> <span data-ttu-id="6c08e-146">Legen Sie das SSL-Zertifikat auf „ContosoBank“ fest.</span><span class="sxs-lookup"><span data-stu-id="6c08e-146">Set the SSL certificate to "ContosoBank".</span></span> <span data-ttu-id="6c08e-147">Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="6c08e-147">Click **OK**.</span></span> <span data-ttu-id="6c08e-148">Klicken Sie im Fenster **Sitebindungen** auf **Schließen**.</span><span class="sxs-lookup"><span data-stu-id="6c08e-148">Click **Close** in the **Site Bindings** window.</span></span>
6.  <span data-ttu-id="6c08e-149">Wählen Sie im **Internetinformationsdienste (IIS)-Manager** den Webdienst "FirstContosoBank" aus.</span><span class="sxs-lookup"><span data-stu-id="6c08e-149">In the **Internet Information Services (IIS) Manager**, select the "FirstContosoBank" web service.</span></span> <span data-ttu-id="6c08e-150">Doppelklicken Sie auf **SSL-Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="6c08e-150">Double-click **SSL Settings**.</span></span> <span data-ttu-id="6c08e-151">Aktivieren Sie **SSL erforderlich**.</span><span class="sxs-lookup"><span data-stu-id="6c08e-151">Check **Require SSL**.</span></span> <span data-ttu-id="6c08e-152">Wählen Sie unter **Clientzertifikate** die Option **Erforderlich**.</span><span class="sxs-lookup"><span data-stu-id="6c08e-152">Under **Client certificates**, select **Require**.</span></span> <span data-ttu-id="6c08e-153">Klicken Sie im Abschnitt **Aktionen** auf **Übernehmen**.</span><span class="sxs-lookup"><span data-stu-id="6c08e-153">In the **Actions** section, click **Apply**.</span></span>
7.  <span data-ttu-id="6c08e-154">Sie können überprüfen, ob der Webdienst richtig konfiguriert ist, indem Sie den Webbrowser öffnen und die folgende Webadresse eingeben: https://&lt;server-name&gt;.&lt;domain-name&gt;/FirstContosoBank/Service1.asmx.</span><span class="sxs-lookup"><span data-stu-id="6c08e-154">You can verify that the web service is configured correctly by opening your web browser and entering the following web address: "https://&lt;server-name&gt;.&lt;domain-name&gt;/FirstContosoBank/Service1.asmx".</span></span> <span data-ttu-id="6c08e-155">Beispiel: https://myserver.example.com/FirstContosoBank/Service1.asmx.</span><span class="sxs-lookup"><span data-stu-id="6c08e-155">For example, "https://myserver.example.com/FirstContosoBank/Service1.asmx".</span></span> <span data-ttu-id="6c08e-156">Wenn der Webdienst richtig konfiguriert ist, werden Sie zum Auswählen eines Clientzertifikats für den Zugriff auf den Webdienst aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="6c08e-156">If your web service is configured correctly, you will be prompted to select a client certificate in order to access the web service.</span></span>

<span data-ttu-id="6c08e-157">Sie können diese Schritte wiederholen, um mehrere Webdienste zu erstellen, auf die mit demselben Clientzertifikat zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="6c08e-157">You can repeat the previous steps to create multiple web services that can be accessed using the same client certificate.</span></span>

## <a name="create-a-uwp-app-that-uses-certificate-authentication"></a><span data-ttu-id="6c08e-158">Erstellen einer UWP-App mit Verwendung der Authentifizierung per Zertifikat</span><span class="sxs-lookup"><span data-stu-id="6c08e-158">Create a UWP app that uses certificate authentication</span></span>


<span data-ttu-id="6c08e-159">Nachdem Sie nun über mindestens einen sicheren Webdienst verfügen, können Ihre Apps Zertifikate für die Authentifizierung bei diesen Webdiensten verwenden.</span><span class="sxs-lookup"><span data-stu-id="6c08e-159">Now that you have one or more secured web services, your apps can use certificates to authenticate to those web services.</span></span> <span data-ttu-id="6c08e-160">Wenn Sie mithilfe des [**HttpClient**](https://msdn.microsoft.com/library/windows/apps/dn298639)-Objekts eine Anforderung an einen authentifizierten Webdienst senden, enthält die erste Anforderung kein Clientzertifikat.</span><span class="sxs-lookup"><span data-stu-id="6c08e-160">When you make a request to an authenticated web service using the [**HttpClient**](https://msdn.microsoft.com/library/windows/apps/dn298639) object, the initial request will not contain a client certificate.</span></span> <span data-ttu-id="6c08e-161">Der authentifizierte Webdienst antwortet mit einer Anforderung der Clientauthentifizierung.</span><span class="sxs-lookup"><span data-stu-id="6c08e-161">The authenticated web service will respond with a request for client authentication.</span></span> <span data-ttu-id="6c08e-162">Daraufhin fragt der Windows-Client den Zertifikatspeicher automatisch nach verfügbaren Clientzertifikaten ab.</span><span class="sxs-lookup"><span data-stu-id="6c08e-162">When this occurs, the Windows client will automatically query the certificate store for available client certificates.</span></span> <span data-ttu-id="6c08e-163">Der Benutzer kann für die Authentifizierung beim Webdienst eine Auswahl aus diesen Zertifikaten treffen.</span><span class="sxs-lookup"><span data-stu-id="6c08e-163">Your user can select from these certificates to authenticate to the web service.</span></span> <span data-ttu-id="6c08e-164">Da einige Zertifikate kennwortgeschützt sind, müssen Sie es Benutzern ermöglichen, das Kennwort für ein Zertifikat einzugeben.</span><span class="sxs-lookup"><span data-stu-id="6c08e-164">Some certificates are password protected, so you will need to provide the user with a way to input the password for a certificate.</span></span>

<span data-ttu-id="6c08e-165">Falls keine Clientzertifikate verfügbar sind, muss der Benutzer dem Zertifikatspeicher ein Zertifikat hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="6c08e-165">If there are no client certificates available, then the user will need to add a certificate to the certificate store.</span></span> <span data-ttu-id="6c08e-166">Sie können Code in die App einfügen, der Benutzern die Auswahl einer PFX-Datei mit einem Clientzertifikat und das Importieren dieses Zertifikats in den Clientzertifikatspeicher ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="6c08e-166">You can include code in your app that enables a user to select a PFX file that contains a client certificate and then import that certificate into the client certificate store.</span></span>

<span data-ttu-id="6c08e-167">**Tipp** Verwenden Sie „makecert.exe“ zum Erstellen einer PFX-Datei zur Verwendung für diese Schnellstartanleitung.</span><span class="sxs-lookup"><span data-stu-id="6c08e-167">**Tip**  You can use makecert.exe to create a PFX file to use with this quickstart.</span></span> <span data-ttu-id="6c08e-168">Informationen zur Verwendung von „makecert.exe“ finden Sie unter [MakeCert](https://msdn.microsoft.com/library/windows/desktop/aa386968).</span><span class="sxs-lookup"><span data-stu-id="6c08e-168">For information on using makecert.exe, see [MakeCert.](https://msdn.microsoft.com/library/windows/desktop/aa386968)</span></span>

 

1.  <span data-ttu-id="6c08e-169">Öffnen Sie Visual Studio, und erstellen Sie auf der Startseite ein neues Projekt.</span><span class="sxs-lookup"><span data-stu-id="6c08e-169">Open Visual Studio and create a new project from the start page.</span></span> <span data-ttu-id="6c08e-170">Geben Sie dem neuen Projekt den Namen "FirstContosoBankApp".</span><span class="sxs-lookup"><span data-stu-id="6c08e-170">Name the new project "FirstContosoBankApp".</span></span> <span data-ttu-id="6c08e-171">Klicken Sie auf **OK**, um das neue Projekt zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="6c08e-171">Click **OK** to create the new project.</span></span>
2.  <span data-ttu-id="6c08e-172">Fügen Sie in der Datei "MainPage.xaml" dem standardmäßigen **Grid**-Element den folgenden XAML-Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="6c08e-172">In the MainPage.xaml file, add the following XAML to the default **Grid** element.</span></span> <span data-ttu-id="6c08e-173">Dieser XAML-Code enthält Folgendes: eine Schaltfläche zum Suchen nach einer zu importierenden PFX-Datei, ein Textfeld zum Eingeben eines Kennworts für eine kennwortgeschützte PFX-Datei, eine Schaltfläche zum Importieren einer ausgewählten PFX-Datei, eine Schaltfläche zum Anmelden beim sicheren Webdienst und einen Textblock zum Anzeigen des Zustands der aktuellen Aktion.</span><span class="sxs-lookup"><span data-stu-id="6c08e-173">This XAML includes a button to browse for a PFX file to import, a text box to enter a password for a password-protected PFX file, a button to import a selected PFX file, a button to log in to the secured web service, and a text block to display the status of the current action.</span></span>
    ```xml
    <Button x:Name="Import" Content="Import Certificate (PFX file)" HorizontalAlignment="Left" Margin="352,305,0,0" VerticalAlignment="Top" Height="77" Width="260" Click="Import_Click" FontSize="16"/>
    <Button x:Name="Login" Content="Login" HorizontalAlignment="Left" Margin="611,305,0,0" VerticalAlignment="Top" Height="75" Width="240" Click="Login_Click" FontSize="16"/>
    <TextBlock x:Name="Result" HorizontalAlignment="Left" Margin="355,398,0,0" TextWrapping="Wrap" VerticalAlignment="Top" Height="153" Width="560"/>
    <PasswordBox x:Name="PfxPassword" HorizontalAlignment="Left" Margin="483,271,0,0" VerticalAlignment="Top" Width="229"/>
    <TextBlock HorizontalAlignment="Left" Margin="355,271,0,0" TextWrapping="Wrap" Text="PFX password" VerticalAlignment="Top" FontSize="18" Height="32" Width="123"/>
    <Button x:Name="Browse" Content="Browse for PFX file" HorizontalAlignment="Left" Margin="352,189,0,0" VerticalAlignment="Top" Click="Browse_Click" Width="499" Height="68" FontSize="16"/>
    <TextBlock HorizontalAlignment="Left" Margin="717,271,0,0" TextWrapping="Wrap" Text="(Optional)" VerticalAlignment="Top" Height="32" Width="83" FontSize="16"/>
    ```
    
3.  <span data-ttu-id="6c08e-174">Speichern Sie die Datei "MainPage.xaml".</span><span class="sxs-lookup"><span data-stu-id="6c08e-174">Save the MainPage.xaml file.</span></span>
4.  <span data-ttu-id="6c08e-175">Fügen Sie in der Datei "MainPage.xaml.cs" die folgenden using-Anweisungen hinzu:</span><span class="sxs-lookup"><span data-stu-id="6c08e-175">In the MainPage.xaml.cs file, add the following using statements.</span></span>
    ```cs
    using Windows.Web.Http;
    using System.Text;
    using Windows.Security.Cryptography.Certificates;
    using Windows.Storage.Pickers;
    using Windows.Storage;
    using Windows.Storage.Streams;
    ```

5.  <span data-ttu-id="6c08e-176">Fügen Sie in der Datei "MainPage.xaml.cs" der **MainPage**-Klasse die folgenden Variablen hinzu.</span><span class="sxs-lookup"><span data-stu-id="6c08e-176">In the MainPage.xaml.cs file, add the following variables to the **MainPage** class.</span></span> <span data-ttu-id="6c08e-177">Damit werden die Adresse für die sichere Login-Methode des Webdiensts „FirstContosoBank“ sowie eine globale Variable, die ein PFX-Zertifikat zum Importieren in den Zertifikatspeicher enthält, angegeben.</span><span class="sxs-lookup"><span data-stu-id="6c08e-177">They specify the address for the secured "Login" method of your "FirstContosoBank" web service, and a global variable that holds a PFX certificate to import into the certificate store.</span></span> <span data-ttu-id="6c08e-178">Ersetzen Sie &lt;Servername&gt; durch den vollqualifizierten Servernamen Ihres IIS-Servers (Microsoft Internet Information Server).</span><span class="sxs-lookup"><span data-stu-id="6c08e-178">Update the &lt;server-name&gt; to the fully-qualified server name for your Microsoft Internet Information Server (IIS) server.</span></span>
    ```cs
    private Uri requestUri = new Uri("https://<server-name>/FirstContosoBank/Service1.asmx?op=Login");
    private string pfxCert = null;
    ```

6.  <span data-ttu-id="6c08e-179">Fügen Sie in der Datei "MainPage.xaml.cs" den folgenden Klickhandler für die Anmeldeschaltfläche und -methode zum Zugreifen auf den sicheren Webdienst hinzu.</span><span class="sxs-lookup"><span data-stu-id="6c08e-179">In the MainPage.xaml.cs file, add the following click handler for the login button and method to access the secured web service.</span></span>
    ```cs
    private void Login_Click(object sender, RoutedEventArgs e)
    {
        MakeHttpsCall();
    }

    private async void MakeHttpsCall()
    {

        StringBuilder result = new StringBuilder("Login ");
        HttpResponseMessage response;
        try
        {
            Windows.Web.Http.HttpClient httpClient = new Windows.Web.Http.HttpClient();
            response = await httpClient.GetAsync(requestUri);
            if (response.StatusCode == HttpStatusCode.Ok)
            {
                result.Append("successful");
            }
            else
            {
                result = result.Append("failed with ");
                result = result.Append(response.StatusCode);
            }
        }
        catch (Exception ex)
        {
            result = result.Append("failed with ");
            result = result.Append(ex.Message);
        }

        Result.Text = result.ToString();
    }
    ```

7.  <span data-ttu-id="6c08e-180">Fügen Sie in der Datei „MainPage.xaml.cs“ die folgenden Klickhandler für die Schaltfläche zum Suchen nach einer PFX-Datei und die Schaltfläche zum Importieren einer ausgewählten PFX-Datei in den Zertifikatspeicher hinzu.</span><span class="sxs-lookup"><span data-stu-id="6c08e-180">In the MainPage.xaml.cs file, add the following click handlers for the button to browse for a PFX file and the button to import a selected PFX file into the certificate store.</span></span>
    ```cs
    private async void Import_Click(object sender, RoutedEventArgs e)
    {
        try
        {
            Result.Text = "Importing selected certificate into user certificate store....";
            await CertificateEnrollmentManager.UserCertificateEnrollmentManager.ImportPfxDataAsync(
                pfxCert,
                PfxPassword.Password,
                ExportOption.Exportable,
                KeyProtectionLevel.NoConsent,
                InstallOptions.DeleteExpired,
                "Import Pfx");

            Result.Text = "Certificate import succeded";
        }
        catch (Exception ex)
        {
            Result.Text = "Certificate import failed with " + ex.Message;
        }
    }

    private async void Browse_Click(object sender, RoutedEventArgs e)
    {

        StringBuilder result = new StringBuilder("Pfx file selection ");
        FileOpenPicker pfxFilePicker = new FileOpenPicker();
        pfxFilePicker.FileTypeFilter.Add(".pfx");
        pfxFilePicker.CommitButtonText = "Open";
        try
        {
            StorageFile pfxFile = await pfxFilePicker.PickSingleFileAsync();
            if (pfxFile != null)
            {
                IBuffer buffer = await FileIO.ReadBufferAsync(pfxFile);
                using (DataReader dataReader = DataReader.FromBuffer(buffer))
                {
                    byte[] bytes = new byte[buffer.Length];
                    dataReader.ReadBytes(bytes);
                    pfxCert = System.Convert.ToBase64String(bytes);
                    PfxPassword.Password = string.Empty;
                    result.Append("succeeded");
                }
            }
            else
            {
                result.Append("failed");
            }
        }
        catch (Exception ex)
        {
            result.Append("failed with ");
            result.Append(ex.Message); ;
        }

        Result.Text = result.ToString();
    }
    ```

8.  <span data-ttu-id="6c08e-181">Führen Sie Ihre App aus, und melden Sie sich beim sicheren Webdienst an. Importieren Sie eine PFX-Datei in den lokalen Zertifikatspeicher.</span><span class="sxs-lookup"><span data-stu-id="6c08e-181">Run your app and log in to your secured web service as well as import a PFX file into the local certificate store.</span></span>

<span data-ttu-id="6c08e-182">Mithilfe dieser Schritte können Sie mehrere Apps erstellen, für die dasselbe Benutzerzertifikat verwendet wird, um auf dieselben oder unterschiedliche sichere Webdienste zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="6c08e-182">You can use these steps to create multiple apps that use the same user certificate to access the same or different secured web services.</span></span>