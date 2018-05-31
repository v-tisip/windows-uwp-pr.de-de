---
title: Erstellen einer Windows Hello-Anmelde-App
description: Dies ist der erste Teil einer umfassenden Schritt-für-Schritt-Lösung zum Erstellen einer Windows 10-App für die Universelle Windows-Plattform (UWP), die Windows Hello als Alternative zu herkömmlichen Authentifizierungssystemen mit Benutzername und Kennwort verwendet.
ms.assetid: A9E11694-A7F5-4E27-95EC-889307E0C0EF
author: PatrickFarley
ms.author: pafarley
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 23a4bd392689a71191e19ea245f984a6984839e3
ms.sourcegitcommit: 91511d2d1dc8ab74b566aaeab3ef2139e7ed4945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2018
ms.locfileid: "1817328"
---
# <a name="create-a-windows-hello-login-app"></a><span data-ttu-id="49d48-104">Erstellen einer Windows Hello-Anmelde-App</span><span class="sxs-lookup"><span data-stu-id="49d48-104">Create a Windows Hello login app</span></span>




<span data-ttu-id="49d48-105">\[Einige Informationen beziehen sich auf die Vorabversion, die vor der kommerziellen Freigabe möglicherweise wesentlichen Änderungen unterliegt.</span><span class="sxs-lookup"><span data-stu-id="49d48-105">\[Some information relates to pre-released product which may be substantially modified before it's commercially released.</span></span> <span data-ttu-id="49d48-106">Microsoft übernimmt keine Garantie, weder ausdrücklicher noch impliziter Art, für die hier bereitgestellten Informationen.\]</span><span class="sxs-lookup"><span data-stu-id="49d48-106">Microsoft makes no warranties, express or implied, with respect to the information provided here.\]</span></span>

<span data-ttu-id="49d48-107">Dies ist der erste Teil einer umfassenden Schritt-für-Schritt-Lösung zum Erstellen einer Windows 10-App für die Universelle Windows-Plattform (UWP), die Windows Hello als Alternative zu herkömmlichen Authentifizierungssystemen mit Benutzername und Kennwort verwendet.</span><span class="sxs-lookup"><span data-stu-id="49d48-107">This is Part 1 of a complete walkthrough on how to create a Windows 10 UWP (Universal Windows Platform) app that uses Windows Hello as an alternative to traditional username and password authentication systems.</span></span> <span data-ttu-id="49d48-108">Die App verwendet einen Benutzernamen für die Anmeldung und erstellt einen Hello-Schlüssel für jedes Konto.</span><span class="sxs-lookup"><span data-stu-id="49d48-108">The app uses a username for sign-in and create a Hello Key for each account.</span></span> <span data-ttu-id="49d48-109">Diese Konten werden durch die PIN geschützt, die in den Windows-Einstellungen beim Konfigurieren von Windows Hello eingerichtet wird.</span><span class="sxs-lookup"><span data-stu-id="49d48-109">These accounts will be protected by the PIN that is setup in Windows Settings on configuration of Windows Hello.</span></span>

<span data-ttu-id="49d48-110">Diese Schritt-für-Schritt-Lösung ist in zwei Teile aufgeteilt: Erstellen der App und Herstellen der Verbindung mit dem Back-End-Dienst.</span><span class="sxs-lookup"><span data-stu-id="49d48-110">This walkthrough is split into two parts: building the app and connecting the backend service.</span></span> <span data-ttu-id="49d48-111">Fahren Sie nach Abschluss dieses Artikels mit Teil2 fort: [Windows-Hello-Anmeldedienst](microsoft-passport-login-auth-service.md).</span><span class="sxs-lookup"><span data-stu-id="49d48-111">When you're finished with this article, continue on to Part 2: [Windows Hello login service](microsoft-passport-login-auth-service.md).</span></span>

<span data-ttu-id="49d48-112">Machen Sie sich in der Übersicht [Windows Hello](microsoft-passport.md) zunächst mit grundlegenden Informationen zur Funktionsweise von Windows Hello vertraut.</span><span class="sxs-lookup"><span data-stu-id="49d48-112">Before you begin, you should read the [Windows Hello](microsoft-passport.md) overview for a general understanding of how Windows Hello works.</span></span>

## <a name="get-started"></a><span data-ttu-id="49d48-113">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="49d48-113">Get started</span></span>


<span data-ttu-id="49d48-114">Die Erstellung dieses Projekts setzt Erfahrung mit C# und XAML voraus.</span><span class="sxs-lookup"><span data-stu-id="49d48-114">In order to build this project, you'll need some experience with C#, and XAML.</span></span> <span data-ttu-id="49d48-115">Außerdem muss Visual Studio2015 (mindestens Community Edition) auf einem Computer unter Windows10 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="49d48-115">You'll also need to be using Visual Studio 2015 (Community Edition or greater) on a Windows 10 machine.</span></span>

-   <span data-ttu-id="49d48-116">Öffnen Sie Visual Studio2015, und wählen Sie „Datei“ > „Neu“ > „Projekt“ aus.</span><span class="sxs-lookup"><span data-stu-id="49d48-116">Open Visual Studio 2015 and select File > New > Project.</span></span>
-   <span data-ttu-id="49d48-117">Din Fenster für ein neues Projekt wird geöffnet.</span><span class="sxs-lookup"><span data-stu-id="49d48-117">This will open a “New Project” window.</span></span> <span data-ttu-id="49d48-118">Navigieren Sie zu „Vorlagen“ > „Visual C#“.</span><span class="sxs-lookup"><span data-stu-id="49d48-118">Navigation to Templates > Visual C#.</span></span>
-   <span data-ttu-id="49d48-119">Wählen Sie „ Leere App (Universelle Windows-App)“ aus, und nennen Sie die Anwendung „PassportLogin“.</span><span class="sxs-lookup"><span data-stu-id="49d48-119">Choose Blank App (Universal Windows) and name your application "PassportLogin".</span></span>
-   <span data-ttu-id="49d48-120">Erstellen Sie die neue Anwendung, und führen Sie sie aus (F5). Anschließend sollte Ihnen auf dem Bildschirm ein leeres Fenster angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="49d48-120">Build and Run the new application (F5), you should see a blank window shown on the screen.</span></span> <span data-ttu-id="49d48-121">Schließen Sie die Anwendung.</span><span class="sxs-lookup"><span data-stu-id="49d48-121">Close the application.</span></span>

![Neue Windows-Hello-Projekt](images/passport-login-1.png)

## <a name="exercise-1-login-with-microsoft-passport"></a><span data-ttu-id="49d48-123">Übung1: Anmelden mit Microsoft Passport</span><span class="sxs-lookup"><span data-stu-id="49d48-123">Exercise 1: Login with Microsoft Passport</span></span>


<span data-ttu-id="49d48-124">In dieser Übung lernen Sie, wie Sie prüfen, ob Windows Hello auf dem Computer eingerichtet ist, und wie Sie sich mit Windows Hello bei einem Konto anmelden.</span><span class="sxs-lookup"><span data-stu-id="49d48-124">In this exercise you will learn how to check if Windows Hello is setup on the machine, and how to sign into an account using Windows Hello.</span></span>

-   <span data-ttu-id="49d48-125">Erstellen Sie in dem neuen Projekt einen neuen Projektmappenordner namens „Views“.</span><span class="sxs-lookup"><span data-stu-id="49d48-125">In the new project create a new folder in the solution called "Views".</span></span> <span data-ttu-id="49d48-126">Dieser Ordner enthält die Seiten, zu denen in diesem Beispiel navigiert wird.</span><span class="sxs-lookup"><span data-stu-id="49d48-126">This folder will contain the pages that will be navigated to in this sample.</span></span> <span data-ttu-id="49d48-127">Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, wählen Sie „Hinzufügen“ > „Neuer Ordner“ aus, und benennen Sie den Ordner anschließend in „Views“ um.</span><span class="sxs-lookup"><span data-stu-id="49d48-127">Right click on the project in solution explorer, select Add > New Folder, then rename the folder to Views.</span></span>

    ![Windows-Hello-Ordner hinzufügen](images/passport-login-2.png)

-   <span data-ttu-id="49d48-129">Klicken Sie mit der rechten Maustaste auf den neuen Ordner „Views“. Wählen Sie „Hinzufügen“ > „Neues Element“ und anschließend die Option „Leere Seite“ aus.</span><span class="sxs-lookup"><span data-stu-id="49d48-129">Right click on the new Views folder, select Add > New Item and select Blank Page.</span></span> <span data-ttu-id="49d48-130">Nennen Sie die Seite „Login.xaml“.</span><span class="sxs-lookup"><span data-stu-id="49d48-130">Name this page "Login.xaml".</span></span>

    ![Windows Hello - leere Seite hinzufügen](images/passport-login-3.png)

-   <span data-ttu-id="49d48-132">Fügen Sie den folgenden XAML-Code hinzu, um die Benutzeroberfläche für die neue Anmeldeseite zu definieren.</span><span class="sxs-lookup"><span data-stu-id="49d48-132">To define the user interface for the new login page, add the following XAML.</span></span> <span data-ttu-id="49d48-133">Dieser XAML-Code definiert ein StackPanel-Element zur Ausrichtung folgender untergeordneter Elemente:</span><span class="sxs-lookup"><span data-stu-id="49d48-133">This XAML defines a StackPanel to align the following children:</span></span>

    -   <span data-ttu-id="49d48-134">TextBlock-Element für einen Titel.</span><span class="sxs-lookup"><span data-stu-id="49d48-134">TextBlock that will contain a title.</span></span>
    -   <span data-ttu-id="49d48-135">TextBlock-Element für Fehlermeldungen.</span><span class="sxs-lookup"><span data-stu-id="49d48-135">TextBlock for error messages.</span></span>
    -   <span data-ttu-id="49d48-136">TextBox-Element für die Eingabe des Benutzernamens.</span><span class="sxs-lookup"><span data-stu-id="49d48-136">TextBox for the username to input.</span></span>
    -   <span data-ttu-id="49d48-137">Schaltfläche für die Navigation zu einer Registrierungsseite.</span><span class="sxs-lookup"><span data-stu-id="49d48-137">Button to navigate to a register page.</span></span>
    -   <span data-ttu-id="49d48-138">TextBlock-Element für den Status von Windows Hello.</span><span class="sxs-lookup"><span data-stu-id="49d48-138">TextBlock to contain the status of Windows Hello.</span></span>
    -   <span data-ttu-id="49d48-139">TextBlock-Element zur Erläuterung der Anmeldeseite, da kein Back-End und keine konfigurierten Benutzer vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="49d48-139">TextBlock to explain the Login page as there is no backend or configured users.</span></span>

    ```xml
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
      <StackPanel Orientation="Vertical">
        <TextBlock Text="Login" FontSize="36" Margin="4" TextAlignment="Center"/>
        <TextBlock x:Name="ErrorMessage" Text="" FontSize="20" Margin="4" Foreground="Red" TextAlignment="Center"/>
        <TextBlock Text="Enter your username below" Margin="0,0,0,20"
                   TextWrapping="Wrap" Width="300"
                   TextAlignment="Center" VerticalAlignment="Center" FontSize="16"/>
        <TextBox x:Name="UsernameTextBox" Margin="4" Width="250"/>
        <Button x:Name="PassportSignInButton" Content="Login" Background="DodgerBlue" Foreground="White"
            Click="PassportSignInButton_Click" Width="80" HorizontalAlignment="Center" Margin="0,20"/>
        <TextBlock Text="Don't have an account?"
                    TextAlignment="Center" VerticalAlignment="Center" FontSize="16"/>
        <TextBlock x:Name="RegisterButtonTextBlock" Text="Register now"
                   PointerPressed="RegisterButtonTextBlock_OnPointerPressed"
                   Foreground="DodgerBlue"
                   TextAlignment="Center" VerticalAlignment="Center" FontSize="16"/>
        <Border x:Name="PassportStatus" Background="#22B14C"
                   Margin="0,20" Height="100" >
          <TextBlock x:Name="PassportStatusText" Text="Microsoft Passport is ready to use!"
                 Margin="4" TextAlignment="Center" VerticalAlignment="Center" FontSize="20"/>
        </Border>
        <TextBlock x:Name="LoginExplaination" FontSize="24" TextAlignment="Center" TextWrapping="Wrap" 
            Text="Please Note: To demonstrate a login, validation will only occur using the default username 'sampleUsername'"/>
      </StackPanel>
    </Grid>
    ```

-   <span data-ttu-id="49d48-140">Dem CodeBehind müssen einige Methoden hinzugefügt werden, damit die Lösung erstellt werden kann.</span><span class="sxs-lookup"><span data-stu-id="49d48-140">A few methods need to be added to the code behind to get the solution building.</span></span> <span data-ttu-id="49d48-141">Drücken Sie entweder F7, oder verwenden Sie den Projektmappen-Explorer, um zu „Login.xaml.cs“ zu gelangen.</span><span class="sxs-lookup"><span data-stu-id="49d48-141">Either press F7 or use the Solution Explorer to get to the Login.xaml.cs.</span></span> <span data-ttu-id="49d48-142">Fügen Sie zur Behandlung des Anmelde- und Registrierungsereignisses die beiden folgenden Ereignismethoden hinzu.</span><span class="sxs-lookup"><span data-stu-id="49d48-142">Add in the following two event methods to handle the Login and Register events.</span></span> <span data-ttu-id="49d48-143">Durch diese Methoden wird „ErrorMessage.Text“ vorerst auf eine leere Zeichenfolge festgelegt.</span><span class="sxs-lookup"><span data-stu-id="49d48-143">For now these methods will set the ErrorMessage.Text to an empty string.</span></span>

    ```cs
    namespace PassportLogin.Views
    {
        public sealed partial class Login : Page
        {
            public Login()
            {
                this.InitializeComponent();
            }
     
            private void PassportSignInButton_Click(object sender, RoutedEventArgs e)
            {
                ErrorMessage.Text = "";
            }
            private void RegisterButtonTextBlock_OnPointerPressed(object sender, PointerRoutedEventArgs e)
            {
                ErrorMessage.Text = "";
            }
        }
    }
    ```

-   <span data-ttu-id="49d48-144">Bearbeiten Sie zum Rendern der Anmeldeseite den MainPage-Code so, dass beim Laden der Hauptseite zur Anmeldeseite navigiert wird.</span><span class="sxs-lookup"><span data-stu-id="49d48-144">In order to render the Login page, edit the MainPage code to navigate to the Login page when the MainPage is loaded.</span></span> <span data-ttu-id="49d48-145">Öffnen Sie die Datei „MainPage.xaml.cs“.</span><span class="sxs-lookup"><span data-stu-id="49d48-145">Open the MainPage.xaml.cs file.</span></span> <span data-ttu-id="49d48-146">Doppelklicken Sie im Projektmappen-Explorer auf „MainPage.xaml.cs“.</span><span class="sxs-lookup"><span data-stu-id="49d48-146">In the solution explorer double click on MainPage.xaml.cs.</span></span> <span data-ttu-id="49d48-147">Sollten Sie das Element nicht finden, klicken Sie auf den kleinen Pfeil neben „MainPage.xaml“, um das CodeBehind anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="49d48-147">If you can’t find this click the little arrow next to MainPage.xaml to show the code behind.</span></span> <span data-ttu-id="49d48-148">Erstellen Sie eine geladene Ereignishandlermethode für die Navigation zur Anmeldeseite.</span><span class="sxs-lookup"><span data-stu-id="49d48-148">Create a loaded event handler method that will navigate to the login page.</span></span> <span data-ttu-id="49d48-149">Sie müssen einen Verweis auf den Views-Namespace hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="49d48-149">You will need to add a reference to the Views namespace.</span></span>

    ```cs
    using PassportLogin.Views;
     
    namespace PassportLogin
    {
        public sealed partial class MainPage : Page
        {
            public MainPage()
            {
                this.InitializeComponent();
                Loaded += MainPage_Loaded;
            }
     
            private void MainPage_Loaded(object sender, RoutedEventArgs e)
            {
                Frame.Navigate(typeof(Login));
            }
        }
    }
    ```

-   <span data-ttu-id="49d48-150">Auf der Anmeldeseite müssen Sie durch Behandeln des OnNavigatedTo-Ereignisses überprüfen, ob Windows Hello auf diesem Computer verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="49d48-150">In the Login page you need to handle the OnNavigatedTo event to validate if Windows Hello is available on this machine.</span></span> <span data-ttu-id="49d48-151">Implementieren Sie Folgendes in „Login.xaml.cs“.</span><span class="sxs-lookup"><span data-stu-id="49d48-151">In Login.xaml.cs implement the following.</span></span> <span data-ttu-id="49d48-152">Das MicrosoftPassportHelper-Objekt gibt einen Fehler aus.</span><span class="sxs-lookup"><span data-stu-id="49d48-152">You will notice that the MicrosoftPassportHelper object flags an error.</span></span> <span data-ttu-id="49d48-153">Das liegt daran, dass es noch nicht implementiert wurde.</span><span class="sxs-lookup"><span data-stu-id="49d48-153">This is because we have not implement it yet.</span></span>

    ```cs
    public sealed partial class Login : Page
    {
        public Login()
        {
            this.InitializeComponent();
        }
     
        protected override async void OnNavigatedTo(NavigationEventArgs e)
        {
            // Check Microsoft Passport is setup and available on this machine
            if (await MicrosoftPassportHelper.MicrosoftPassportAvailableCheckAsync())
            {
            }
            else
            {
                // Microsoft Passport is not setup so inform the user
                PassportStatus.Background = new SolidColorBrush(Windows.UI.Color.FromArgb(255, 50, 170, 207));
                PassportStatusText.Text = "Microsoft Passport is not setup!\n" + 
                    "Please go to Windows Settings and set up a PIN to use it.";
                PassportSignInButton.IsEnabled = false;
            }
        }
    }
    ```

-   <span data-ttu-id="49d48-154">Klicken Sie zum Erstellen der MicrosoftPassportHelper-Klasse mit der rechten Maustaste auf die Projektmappe „PassportLogin (Universelle Windows-App)“, und wählen Sie „Hinzufügen“ > „Neuer Ordner“ aus.</span><span class="sxs-lookup"><span data-stu-id="49d48-154">To create the MicrosoftPassportHelper class, right click on the solution PassportLogin (Universal Windows) and click Add > New Folder.</span></span> <span data-ttu-id="49d48-155">Nennen Sie den Ordner „Utils“.</span><span class="sxs-lookup"><span data-stu-id="49d48-155">Name this folder Utils.</span></span>

    ![Passport – Erstellen von Helferklassen](images/passport-login-5.png)

-   <span data-ttu-id="49d48-157">Klicken Sie mit der rechten Maustaste auf den Ordner „Utils“, und wählen Sie „Hinzufügen“ > „Klasse“ aus.</span><span class="sxs-lookup"><span data-stu-id="49d48-157">Right click on the Utils folder and click Add > Class.</span></span> <span data-ttu-id="49d48-158">Nennen Sie die Klasse „MicrosoftPassportHelper.cs“.</span><span class="sxs-lookup"><span data-stu-id="49d48-158">Name this class "MicrosoftPassportHelper.cs".</span></span>
-   <span data-ttu-id="49d48-159">Definieren Sie „MicrosoftPassportHelper“ als öffentliche, statische Klasse, und fügen Sie anschließend die folgende Methode hinzu, um den Benutzer darüber zu informieren, ob Windows Hello verwendungsbereit ist.</span><span class="sxs-lookup"><span data-stu-id="49d48-159">Change the class definition of MicrosoftPassportHelper to public static, then add the following method that to inform the user if Windows Hello is ready to be used or not.</span></span> <span data-ttu-id="49d48-160">Sie müssen die erforderlichen Namensräume hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="49d48-160">You will need to add the required namespaces.</span></span>

    ```cs
    using System;
    using System.Diagnostics;
    using System.Threading.Tasks;
    using Windows.Security.Credentials;
     
    namespace PassportLogin.Utils
    {
        public static class MicrosoftPassportHelper
        {
            /// <summary>
            /// Checks to see if Passport is ready to be used.
            /// 
            /// Passport has dependencies on:
            ///     1. Having a connected Microsoft Account
            ///     2. Having a Windows PIN set up for that _account on the local machine
            /// </summary>
            public static async Task<bool> MicrosoftPassportAvailableCheckAsync()
            {
                bool keyCredentialAvailable = await KeyCredentialManager.IsSupportedAsync();
                if (keyCredentialAvailable == false)
                {
                    // Key credential is not enabled yet as user 
                    // needs to connect to a Microsoft Account and select a PIN in the connecting flow.
                    Debug.WriteLine("Microsoft Passport is not setup!\nPlease go to Windows Settings and set up a PIN to use it.");
                    return false;
                }
     
                return true;
            }
        }
    }
    ```

-   <span data-ttu-id="49d48-161">Fügen Sie in „Login.xaml.cs“ einen Verweis auf den Utils-Namespace hinzu.</span><span class="sxs-lookup"><span data-stu-id="49d48-161">In Login.xaml.cs add a reference to the Utils namespace.</span></span> <span data-ttu-id="49d48-162">Dadurch wird der Fehler in der OnNavigatedTo-Methode behoben.</span><span class="sxs-lookup"><span data-stu-id="49d48-162">This will resolve the error in the OnNavigatedTo method.</span></span>

    ```cs
    using PassportLogin.Utils;
    ```

-   <span data-ttu-id="49d48-163">Erstellen Sie die Anwendung und führen Sie sie aus (F5).</span><span class="sxs-lookup"><span data-stu-id="49d48-163">Build and run the application (F5).</span></span> <span data-ttu-id="49d48-164">Sie werden auf die Anmeldeseite weitergeleitet, und das Windows-Hello-Banner gibt Aufschluss darüber, ob Hello verwendungsbereit ist.</span><span class="sxs-lookup"><span data-stu-id="49d48-164">You will be navigated to the login page and the Windows Hello banner will indicate to you if Hello is ready to be used.</span></span> <span data-ttu-id="49d48-165">Das Banner ist entweder grün oder blau und gibt den Status von Windows Hello auf Ihrem Computer an.</span><span class="sxs-lookup"><span data-stu-id="49d48-165">You should see either the green or blue banner indicating the Windows Hello status on your machine.</span></span>

    ![Windows Hello - Anmeldebildschirm bereit](images/passport-login-6.png)

    ![Windows Hello - Anmeldebildschirm nicht eingerichtet](images/passport-login-7.png)

-   <span data-ttu-id="49d48-168">Als Nächstes muss die Anmeldelogik erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="49d48-168">The next thing you need to do is build the logic for signing in.</span></span> <span data-ttu-id="49d48-169">Erstellen Sie einen neuen Ordner namens „Models“.</span><span class="sxs-lookup"><span data-stu-id="49d48-169">Create a new folder called "Models".</span></span>
-   <span data-ttu-id="49d48-170">Erstellen Sie im Ordner „Models“ eine neue Klasse namens „Account.cs“.</span><span class="sxs-lookup"><span data-stu-id="49d48-170">In the Models folder create a new class called "Account.cs".</span></span> <span data-ttu-id="49d48-171">Diese Klasse fungiert als Modell für Ihr Konto.</span><span class="sxs-lookup"><span data-stu-id="49d48-171">This class will act as your account model.</span></span> <span data-ttu-id="49d48-172">Da es sich hierbei um ein Beispiel handelt, enthält es lediglich einen Benutzernamen.</span><span class="sxs-lookup"><span data-stu-id="49d48-172">As this is a sample it will only contain a username.</span></span> <span data-ttu-id="49d48-173">Definieren Sie die Klasse als öffentliche Klasse, und fügen Sie die Username-Eigenschaft hinzu.</span><span class="sxs-lookup"><span data-stu-id="49d48-173">Change the class definition to public and add the Username property.</span></span>
    
    ```cs
    namespace PassportLogin.Models
    {
        public class Account
        {
            public string Username { get; set; }
        }
    }
    ```

-   <span data-ttu-id="49d48-174">Sie benötigen eine Möglichkeit zur Behandlung von Konten.</span><span class="sxs-lookup"><span data-stu-id="49d48-174">You will need a way to handle accounts.</span></span> <span data-ttu-id="49d48-175">Da in dieser praktischen Übung weder ein Server noch eine Datenbank vorhanden ist, wird eine Liste mit Benutzern lokal gespeichert und geladen.</span><span class="sxs-lookup"><span data-stu-id="49d48-175">For this hands on lab as there is no server, or a database, a list of users will be saved and loaded locally.</span></span> <span data-ttu-id="49d48-176">Klicken Sie mit der rechten Maustaste auf den Ordner „Utils“, und fügen Sie eine neue Klasse namens „AccountHelper.cs“ hinzu.</span><span class="sxs-lookup"><span data-stu-id="49d48-176">Right click on the Utils folder and add a new class called "AccountHelper.cs".</span></span> <span data-ttu-id="49d48-177">Definieren Sie die Klasse als öffentliche, statische Klasse.</span><span class="sxs-lookup"><span data-stu-id="49d48-177">Change the class definition to be public static.</span></span> <span data-ttu-id="49d48-178">„AccountHelper“ ist eine statische Klasse mit allen erforderlichen Methoden zum lokalen Speichern und Laden der Kontenliste.</span><span class="sxs-lookup"><span data-stu-id="49d48-178">The AccountHelper is a static class that will contain all the necessary methods to save and load the list of accounts locally.</span></span> <span data-ttu-id="49d48-179">Zum Speichern und Laden wird ein XmlSerializer-Element verwendet.</span><span class="sxs-lookup"><span data-stu-id="49d48-179">Saving and loading will work by using an XmlSerializer.</span></span> <span data-ttu-id="49d48-180">Darüber hinaus müssen Sie sich die gespeicherte Datei und ihren Speicherort merken.</span><span class="sxs-lookup"><span data-stu-id="49d48-180">You will also need to remember the file you saved and where you saved it.</span></span> <span data-ttu-id="49d48-181">Dazu werden Verweise auf weitere Namespaces benötigt.</span><span class="sxs-lookup"><span data-stu-id="49d48-181">Additional namespaces will be need to be referenced.</span></span>
    
    ```cs
    using System.IO;
    using System.Xml.Serialization;
    using Windows.Storage;
    using PassportLogin.Models;

    namespace PassportLogin.Utils
    {
        public static class AccountHelper
        {
            // In the real world this would not be needed as there would be a server implemented that would host a user account database.
            // For this tutorial we will just be storing accounts locally.
            private const string USER_ACCOUNT_LIST_FILE_NAME = "accountlist.txt";
            private static string _accountListPath = Path.Combine(ApplicationData.Current.LocalFolder.Path, USER_ACCOUNT_LIST_FILE_NAME);
            public static List<Account> AccountList = new List<Account>();
     
            /// <summary>
            /// Create and save a useraccount list file. (Updating the old one)
            /// </summary>
            private static async void SaveAccountListAsync()
            {
                string accountsXml = SerializeAccountListToXml();
     
                if (File.Exists(_accountListPath))
                {
                    StorageFile accountsFile = await StorageFile.GetFileFromPathAsync(_accountListPath);
                    await FileIO.WriteTextAsync(accountsFile, accountsXml);
                }
                else
                {
                    StorageFile accountsFile = await ApplicationData.Current.LocalFolder.CreateFileAsync(USER_ACCOUNT_LIST_FILE_NAME);
                    await FileIO.WriteTextAsync(accountsFile, accountsXml);
                }
            }
     
            /// <summary>
            /// Gets the useraccount list file and deserializes it from XML to a list of useraccount objects.
            /// </summary>
            /// <returns>List of useraccount objects</returns>
            public static async Task<List<Account>> LoadAccountListAsync()
            {
                if (File.Exists(_accountListPath))
                {
                    StorageFile accountsFile = await StorageFile.GetFileFromPathAsync(_accountListPath);
     
                    string accountsXml = await FileIO.ReadTextAsync(accountsFile);
                    DeserializeXmlToAccountList(accountsXml);
                }
     
                return AccountList;
            }
     
            /// <summary>
            /// Uses the local list of accounts and returns an XML formatted string representing the list
            /// </summary>
            /// <returns>XML formatted list of accounts</returns>
            public static string SerializeAccountListToXml()
            {
                XmlSerializer xmlizer = new XmlSerializer(typeof(List<Account>));
                StringWriter writer = new StringWriter();
                xmlizer.Serialize(writer, AccountList);
     
                return writer.ToString();
            }
     
            /// <summary>
            /// Takes an XML formatted string representing a list of accounts and returns a list object of accounts
            /// </summary>
            /// <param name="listAsXml">XML formatted list of accounts</param>
            /// <returns>List object of accounts</returns>
            public static List<Account> DeserializeXmlToAccountList(string listAsXml)
            {
                XmlSerializer xmlizer = new XmlSerializer(typeof(List<Account>));
                TextReader textreader = new StreamReader(new MemoryStream(Encoding.UTF8.GetBytes(listAsXml)));
     
                return AccountList = (xmlizer.Deserialize(textreader)) as List<Account>;
            }
        }
    }
    ```

-   <span data-ttu-id="49d48-182">Implementieren Sie als Nächstes eine Möglichkeit zum Hinzufügen und Entfernen eines Kontos aus der lokalen Kontenliste.</span><span class="sxs-lookup"><span data-stu-id="49d48-182">Next, implement a way to add and remove an account from the local list of accounts.</span></span> <span data-ttu-id="49d48-183">Durch diese Aktionen wird die Liste jeweils gespeichert.</span><span class="sxs-lookup"><span data-stu-id="49d48-183">These actions will each save the list.</span></span> <span data-ttu-id="49d48-184">Zum Abschluss wird für diese praktische Übung noch eine Überprüfungsmethode benötigt.</span><span class="sxs-lookup"><span data-stu-id="49d48-184">The final method that you will need for this hands on lab is a validation method.</span></span> <span data-ttu-id="49d48-185">Da weder ein Authentifizierungsserver noch eine Benutzerdatenbank zur Verfügung steht, erfolgt die Überprüfung anhand eines einzelnen, hartcodierten Benutzers.</span><span class="sxs-lookup"><span data-stu-id="49d48-185">As there is no auth server or database of users, this will validate against a single user which is hard coded.</span></span> <span data-ttu-id="49d48-186">Die folgenden Methoden müssen der AccountHelper-Klasse hinzugefügt werden:</span><span class="sxs-lookup"><span data-stu-id="49d48-186">These methods should be added to the AccountHelper class.</span></span>
    
    ```cs
    public static Account AddAccount(string username)
            {
                // Create a new account with the username
                Account account = new Account() { Username = username };
                // Add it to the local list of accounts
                AccountList.Add(account);
                // SaveAccountList and return the account
                SaveAccountListAsync();
                return account;
            }
     
            public static void RemoveAccount(Account account)
            {
                // Remove the account from the accounts list
                AccountList.Remove(account);
                // Re save the updated list
                SaveAccountListAsync();
            }
     
            public static bool ValidateAccountCredentials(string username)
            {
                // In the real world, this method would call the server to authenticate that the account exists and is valid.
                // For this tutorial however we will just have a existing sample user that is just "sampleUsername"
                // If the username is null or does not match "sampleUsername" it will fail validation. In which case the user should register a new passport user
     
                if (string.IsNullOrEmpty(username))
                {
                    return false;
                }
     
                if (!string.Equals(username, "sampleUsername"))
                {
                    return false;
                }
     
                return true;
            }
    ```

-   <span data-ttu-id="49d48-187">Als Nächstes müssen Sie eine Anmeldeanforderung des Benutzers behandeln.</span><span class="sxs-lookup"><span data-stu-id="49d48-187">The next thing you need to do is handle a sign in request from the user.</span></span> <span data-ttu-id="49d48-188">Erstellen Sie in „Login.xaml.cs“ eine neue private Variable, die das aktuelle Konto für die Anmeldung enthält.</span><span class="sxs-lookup"><span data-stu-id="49d48-188">In Login.xaml.cs create a new private variable that will hold the current account logging in.</span></span> <span data-ttu-id="49d48-189">Fügen Sie dann einen neuen SignInPassport-Methodenaufruf hinzu.</span><span class="sxs-lookup"><span data-stu-id="49d48-189">Then add a new method call SignInPassport.</span></span> <span data-ttu-id="49d48-190">Dadurch werden die Anmeldeinformationen des Kontos mithilfe der AccountHelper.ValidateAccountCredentials-Methode überprüft.</span><span class="sxs-lookup"><span data-stu-id="49d48-190">This will validate the account credentials using the AccountHelper.ValidateAccountCredentials method.</span></span> <span data-ttu-id="49d48-191">Diese Methode gibt einen booleschen Wert zurück, wenn der eingegebene Benutzername dem hartcodierten Zeichenfolgenwert entspricht, den Sie im vorherigen Schritt festgelegt haben.</span><span class="sxs-lookup"><span data-stu-id="49d48-191">This method will return a Boolean value if the entered user name is the same as the hard coded string value you set in the previous step.</span></span> <span data-ttu-id="49d48-192">Der hartcodierte Wert für dieses Beispiel lautet „sampleUsername“.</span><span class="sxs-lookup"><span data-stu-id="49d48-192">The hard coded value for this sample is "sampleUsername".</span></span>

    ```cs
    using PassportLogin.Models;
    using PassportLogin.Utils;
    using System.Diagnostics;
     
    namespace PassportLogin.Views
    {
        public sealed partial class Login : Page
        {
            private Account _account;
     
            public Login()
            {
                this.InitializeComponent();
            }
     
            protected override async void OnNavigatedTo(NavigationEventArgs e)
            {
                // Check Microsoft Passport is setup and available on this machine
                if (await MicrosoftPassportHelper.MicrosoftPassportAvailableCheckAsync())
                {
                }
                else
                {
                    // Microsoft Passport is not setup so inform the user
                    PassportStatus.Background = new SolidColorBrush(Windows.UI.Color.FromArgb(255, 50, 170, 207));
                    PassportStatusText.Text = "Microsoft Passport is not setup!\nPlease go to Windows Settings and set up a PIN to use it.";
                    PassportSignInButton.IsEnabled = false;
                }
            }
     
            private void PassportSignInButton_Click(object sender, RoutedEventArgs e)
            {
                ErrorMessage.Text = "";
                SignInPassport();
            }
     
            private void RegisterButtonTextBlock_OnPointerPressed(object sender, PointerRoutedEventArgs e)
            {
                ErrorMessage.Text = "";
            }
     
            private async void SignInPassport()
            {
                if (AccountHelper.ValidateAccountCredentials(UsernameTextBox.Text))
                {
                    // Create and add a new local account
                    _account = AccountHelper.AddAccount(UsernameTextBox.Text);
                    Debug.WriteLine("Successfully signed in with traditional credentials and created local account instance!");
     
                    //if (await MicrosoftPassportHelper.CreatePassportKeyAsync(UsernameTextBox.Text))
                    //{
                    //    Debug.WriteLine("Successfully signed in with Microsoft Passport!");
                    //}
                }
                else
                {
                    ErrorMessage.Text = "Invalid Credentials";
                }
            }
        }
    }
    ```

-   <span data-ttu-id="49d48-193">Sie haben wahrscheinlich den auskommentierten Code bemerkt, der auf eine Methode in „MicrosoftPassportHelper“ verweist.</span><span class="sxs-lookup"><span data-stu-id="49d48-193">You may have noticed the commented code that was referencing a method in MicrosoftPassportHelper.</span></span> <span data-ttu-id="49d48-194">Fügen Sie in „MicrosoftPassportHelper.cs“ eine neue Methode namens „CreatePassportKeyAsync“ hinzu.</span><span class="sxs-lookup"><span data-stu-id="49d48-194">In MicrosoftPassportHelper.cs add in a new method called CreatePassportKeyAsync.</span></span> <span data-ttu-id="49d48-195">Diese Methode verwendet die Windows-Hello-API in der [**KeyCredentialManager**](https://msdn.microsoft.com/library/windows/apps/dn973043).</span><span class="sxs-lookup"><span data-stu-id="49d48-195">This method uses the Windows Hello API in the [**KeyCredentialManager**](https://msdn.microsoft.com/library/windows/apps/dn973043).</span></span> <span data-ttu-id="49d48-196">Durch Aufrufen von [**RequestCreateAsync**](https://msdn.microsoft.com/library/windows/apps/dn973048) wird ein spezifischer Passport-Schlüssel für die *accountId* und den lokalen Computer erstellt.</span><span class="sxs-lookup"><span data-stu-id="49d48-196">Calling [**RequestCreateAsync**](https://msdn.microsoft.com/library/windows/apps/dn973048) will create a Passport key that is specific to the *accountId* and the local machine.</span></span> <span data-ttu-id="49d48-197">Beachten Sie die Kommentare in der switch-Anweisung, falls Sie dies in der Praxis umsetzen möchten.</span><span class="sxs-lookup"><span data-stu-id="49d48-197">Please note the comments in the switch statement if you are interested in implementing this in a real world scenario.</span></span>

    ```cs
    /// <summary>
    /// Creates a Passport key on the machine using the _account id passed.
    /// </summary>
    /// <param name="accountId">The _account id associated with the _account that we are enrolling into Passport</param>
    /// <returns>Boolean representing if creating the Passport key succeeded</returns>
    public static async Task<bool> CreatePassportKeyAsync(string accountId)
    {
        KeyCredentialRetrievalResult keyCreationResult = await KeyCredentialManager.RequestCreateAsync(accountId, KeyCredentialCreationOption.ReplaceExisting);

        switch (keyCreationResult.Status)
        {
            case KeyCredentialStatus.Success:
                Debug.WriteLine("Successfully made key");

                // In the real world authentication would take place on a server.
                // So every time a user migrates or creates a new Microsoft Passport account Passport details should be pushed to the server.
                // The details that would be pushed to the server include:
                // The public key, keyAttesation if available, 
                // certificate chain for attestation endorsement key if available,  
                // status code of key attestation result: keyAttestationIncluded or 
                // keyAttestationCanBeRetrievedLater and keyAttestationRetryType
                // As this sample has no concept of a server it will be skipped for now
                // for information on how to do this refer to the second Passport sample

                //For this sample just return true
                return true;
            case KeyCredentialStatus.UserCanceled:
                Debug.WriteLine("User cancelled sign-in process.");
                break;
            case KeyCredentialStatus.NotFound:
                // User needs to setup Microsoft Passport
                Debug.WriteLine("Microsoft Passport is not setup!\nPlease go to Windows Settings and set up a PIN to use it.");
                break;
            default:
                break;
        }

        return false;
    }
    ```

-   <span data-ttu-id="49d48-198">Nachdem Sie nun die CreatePassportKeyAsync-Methode erstellt haben, kehren Sie zur Datei „Login.xaml.cs“ zurück, und heben Sie die Auskommentierung des Codes in der SignInPassport-Methode auf.</span><span class="sxs-lookup"><span data-stu-id="49d48-198">Now you have created the CreatePassportKeyAsync method, return to the Login.xaml.cs file and uncomment the code inside the SignInPassport method.</span></span>

    ```cs
    private async void SignInPassport()
    {
        if (AccountHelper.ValidateAccountCredentials(UsernameTextBox.Text))
        {
            //Create and add a new local account
            _account = AccountHelper.AddAccount(UsernameTextBox.Text);
            Debug.WriteLine("Successfully signed in with traditional credentials and created local account instance!");

            if (await MicrosoftPassportHelper.CreatePassportKeyAsync(UsernameTextBox.Text))
            {
                Debug.WriteLine("Successfully signed in with Microsoft Passport!");
            }
        }
        else
        {
            ErrorMessage.Text = "Invalid Credentials";
        }
    }
    ```

-   <span data-ttu-id="49d48-199">Erstellen Sie die Anwendung, und führen Sie sie aus.</span><span class="sxs-lookup"><span data-stu-id="49d48-199">Build and run the application.</span></span> <span data-ttu-id="49d48-200">Sie werden auf die Anmeldeseite weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="49d48-200">You will be taken to the Login page.</span></span> <span data-ttu-id="49d48-201">Geben Sie „sampleUsername“ ein, und klicken Sie auf „Anmelden“.</span><span class="sxs-lookup"><span data-stu-id="49d48-201">Type in "sampleUsername" and click login.</span></span> <span data-ttu-id="49d48-202">Daraufhin werden Sie von Windows Hello zur Eingabe Ihrer PIN aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="49d48-202">You will be prompted with a Windows Hello prompt asking you to enter your PIN.</span></span> <span data-ttu-id="49d48-203">Nach korrekter PIN-Eingabe kann von der CreatePassportKeyAsync-Methode ein Windows-Hello-Schlüssel erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="49d48-203">Upon entering your PIN correctly the CreatePassportKeyAsync method will be able to create a Windows Hello key.</span></span> <span data-ttu-id="49d48-204">Überwachen Sie die Ausgabefenster auf Erfolgsmeldungen.</span><span class="sxs-lookup"><span data-stu-id="49d48-204">Monitor the output windows to see if the messages indicating success are shown.</span></span>

    ![Windows-Hello-Anmelde-Pin-Aufforderung](images/passport-login-8.png)

## <a name="exercise-2-welcome-and-user-selection-pages"></a><span data-ttu-id="49d48-206">Übung2: Begrüßungs- und Benutzerauswahlseiten</span><span class="sxs-lookup"><span data-stu-id="49d48-206">Exercise 2: Welcome and User Selection Pages</span></span>


<span data-ttu-id="49d48-207">Diese Übung baut direkt auf der vorherigen Übung auf.</span><span class="sxs-lookup"><span data-stu-id="49d48-207">In this exercise, you will continue from the previous exercise.</span></span> <span data-ttu-id="49d48-208">Nach erfolgreicher Anmeldung soll der Benutzer auf eine Begrüßungsseite weitergeleitet werden, auf der er sich abmelden oder sein Konto löschen kann.</span><span class="sxs-lookup"><span data-stu-id="49d48-208">When a person successfully logs in they should be taken to a welcome page where they can sign out or delete their account.</span></span> <span data-ttu-id="49d48-209">Da von Windows Hello ein computerspezifischer Schlüssel erstellt wird, kann ein Benutzerauswahlbildschirm erstellt werden, der alle Benutzer anzeigt, die auf diesem Computer angemeldet waren.</span><span class="sxs-lookup"><span data-stu-id="49d48-209">As Windows Hello creates a key for every machine, a user selection screen can be created, which displays all users that have been signed in on that machine.</span></span> <span data-ttu-id="49d48-210">Ein Benutzer kann dann eines dieser Konten auswählen, um direkt und ohne erneute Kennworteingabe zur Willkommensseite zu gelangen, da er bereits für den Zugriff auf den Computer authentifiziert wurde.</span><span class="sxs-lookup"><span data-stu-id="49d48-210">A user can then select one of these accounts and go directly to the welcome screen without needed to re-enter a password as they have already authenticated to access the machine.</span></span>

-   <span data-ttu-id="49d48-211">Fügen Sie im Ordner „Views“ eine neue leere Seite namens „Welcome.xaml“ hinzu.</span><span class="sxs-lookup"><span data-stu-id="49d48-211">In the Views folder add a new blank page called "Welcome.xaml".</span></span> <span data-ttu-id="49d48-212">Fügen Sie zur Vervollständigung der Benutzeroberfläche den folgenden XAML-Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="49d48-212">Add the following XAML to complete the user interface.</span></span> <span data-ttu-id="49d48-213">Dadurch werden ein Titel, der Benutzername des angemeldeten Benutzers und zwei Schaltflächen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="49d48-213">This will display a title, the logged in username, and two buttons.</span></span> <span data-ttu-id="49d48-214">Über eine der Schaltflächen gelangt der Benutzer wieder zur Benutzerliste (die Sie später noch erstellen), die andere Schaltfläche dient zum Löschen des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="49d48-214">One of the buttons will navigate back to a user list (that you will create later), and the other button will handle forgetting this user.</span></span>

    ```xml
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
      <StackPanel Orientation="Vertical">
        <TextBlock x:Name="Title" Text="Welcome" FontSize="40" TextAlignment="Center"/>
        <TextBlock x:Name="UserNameText" FontSize="28" TextAlignment="Center" Foreground="Black"/>

        <Button x:Name="BackToUserListButton" Content="Back to User List" Click="Button_Restart_Click"
                HorizontalAlignment="Center" Margin="0,20" Foreground="White" Background="DodgerBlue"/>

        <Button x:Name="ForgetButton" Content="Forget Me" Click="Button_Forget_User_Click"
                Foreground="White"
                Background="Gray"
                HorizontalAlignment="Center"/>
      </StackPanel>
    </Grid>
    ```

-   <span data-ttu-id="49d48-215">Fügen Sie in der CodeBehind-Datei „Welcome.xaml.cs“ eine neue private Variable hinzu, die das angemeldete Konto enthält.</span><span class="sxs-lookup"><span data-stu-id="49d48-215">In the Welcome.xaml.cs code behind file, add a new private variable that will hold the account that is logged in.</span></span> <span data-ttu-id="49d48-216">Sie müssen eine Methode zum Überschreiben des OnNavigatedTo-Ereignisses implementieren. Dadurch wird das an die Willkommensseite übergebene Konto gespeichert.</span><span class="sxs-lookup"><span data-stu-id="49d48-216">You will need to implement a method to override the OnNavigateTo event, this will store the account passed to the welcome page.</span></span> <span data-ttu-id="49d48-217">Außerdem müssen Sie das Klickereignis für die beiden im XAML-Code definierten Schaltflächen implementieren.</span><span class="sxs-lookup"><span data-stu-id="49d48-217">You will also need to implement the click event for the two buttons defined in the XAML.</span></span> <span data-ttu-id="49d48-218">Sie benötigen einen Verweis auf die Ordner „Models“ und „Utils“.</span><span class="sxs-lookup"><span data-stu-id="49d48-218">You will need a reference to the Models and Utils folders.</span></span>

    ```cs
    using PassportLogin.Models;
    using PassportLogin.Utils;
    using System.Diagnostics;
     
    namespace PassportLogin.Views
    {
        public sealed partial class Welcome : Page
        {
            private Account _activeAccount;
     
            public Welcome()
            {
                InitializeComponent();
            }
     
            protected override void OnNavigatedTo(NavigationEventArgs e)
            {
                _activeAccount = (Account)e.Parameter;
                if (_activeAccount != null)
                {
                    UserNameText.Text = _activeAccount.Username;
                }
            }
     
            private void Button_Restart_Click(object sender, RoutedEventArgs e)
            {
            }
     
            private void Button_Forget_User_Click(object sender, RoutedEventArgs e)
            {
                // Remove it from Microsoft Passport
                // MicrosoftPassportHelper.RemovePassportAccountAsync(_activeAccount);
     
                // Remove it from the local accounts list and resave the updated list
                AccountHelper.RemoveAccount(_activeAccount);
     
                Debug.WriteLine("User " + _activeAccount.Username + " deleted.");
            }
        }
    }
    ```

-   <span data-ttu-id="49d48-219">Wahrscheinlich haben Sie bemerkt, dass im Klickereignis zum Löschen des Benutzers eine Zeile auskommentiert ist.</span><span class="sxs-lookup"><span data-stu-id="49d48-219">You may have noticed a line commented out in the forget user click event.</span></span> <span data-ttu-id="49d48-220">Das Konto wird aus Ihrer lokalen Liste entfernt, kann derzeit aber nicht aus Windows Hello entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="49d48-220">The account is being removed from your local list but currently there is no way to be removed from Windows Hello.</span></span> <span data-ttu-id="49d48-221">Sie müssen in „MicrosoftPassportHelper.cs“ eine neue Methode implementieren, die das Entfernen eines Windows-Hello-Benutzers behandelt.</span><span class="sxs-lookup"><span data-stu-id="49d48-221">You need to implement a new method in MicrosoftPassportHelper.cs that will handle removing a Windows Hello user.</span></span> <span data-ttu-id="49d48-222">Diese Methode verwendet andere Windows Hello-API zum Öffnen und Löschen des Kontos.</span><span class="sxs-lookup"><span data-stu-id="49d48-222">This method will use other Windows Hello APIs to open and delete the account.</span></span> <span data-ttu-id="49d48-223">In der Praxis muss beim Löschen eines Kontos der Server oder die Datenbank benachrichtigt werden, damit die Benutzerdatenbank gültig bleibt.</span><span class="sxs-lookup"><span data-stu-id="49d48-223">In the real world when you delete an account the server or database should be notified so the user database remains valid.</span></span> <span data-ttu-id="49d48-224">Sie benötigen einen Verweis auf den Ordner „Models“.</span><span class="sxs-lookup"><span data-stu-id="49d48-224">You will need a reference to the Models folder.</span></span>

    ```cs
    using PassportLogin.Models;

    /// <summary>
    /// Function to be called when user requests deleting their account.
    /// Checks the KeyCredentialManager to see if there is a Passport for the current user
    /// Then deletes the local key associated with the Passport.
    /// </summary>
    public static async void RemovePassportAccountAsync(Account account)
    {
        // Open the account with Passport
        KeyCredentialRetrievalResult keyOpenResult = await KeyCredentialManager.OpenAsync(account.Username);

        if (keyOpenResult.Status == KeyCredentialStatus.Success)
        {
            // In the real world you would send key information to server to unregister
            //e.g. RemovePassportAccountOnServer(account);
        }

        // Then delete the account from the machines list of Passport Accounts
        await KeyCredentialManager.DeleteAsync(account.Username);
    }
    ```

-   <span data-ttu-id="49d48-225">Heben Sie in „Welcome.xaml.cs“ die Auskommentierung der Zeile mit dem RemovePassportAccountAsync-Aufruf auf.</span><span class="sxs-lookup"><span data-stu-id="49d48-225">Back in Welcome.xaml.cs, uncomment the line that calls RemovePassportAccountAsync.</span></span>

    ```cs
    private void Button_Forget_User_Click(object sender, RoutedEventArgs e)
    {
        // Remove it from Microsoft Passport
        MicrosoftPassportHelper.RemovePassportAccountAsync(_activeAccount);
     
        // Remove it from the local accounts list and resave the updated list
        AccountHelper.RemoveAccount(_activeAccount);
     
        Debug.WriteLine("User " + _activeAccount.Username + " deleted.");
    }
    ```

-   <span data-ttu-id="49d48-226">Nach erfolgreicher Ausführung von „CreatePassportKeyAsync“ navigiert die SignInPassport-Methode (in „Login.xaml.cs“) zur Willkommensseite und übergibt das Konto.</span><span class="sxs-lookup"><span data-stu-id="49d48-226">In the SignInPassport method (of Login.xaml.cs), once the CreatePassportKeyAsync is successful it should navigate to the Welcome screen and pass the Account.</span></span>

    ```cs
    private async void SignInPassport()
    {
        if (AccountHelper.ValidateAccountCredentials(UsernameTextBox.Text))
        {
            // Create and add a new local account
            _account = AccountHelper.AddAccount(UsernameTextBox.Text);
            Debug.WriteLine("Successfully signed in with traditional credentials and created local account instance!");

            if (await MicrosoftPassportHelper.CreatePassportKeyAsync(UsernameTextBox.Text))
            {
                Debug.WriteLine("Successfully signed in with Microsoft Passport!");
                Frame.Navigate(typeof(Welcome), _account);
            }
        }
        else
        {
            ErrorMessage.Text = "Invalid Credentials";
        }
    }
    ```

-   <span data-ttu-id="49d48-227">Erstellen Sie die Anwendung, und führen Sie sie aus.</span><span class="sxs-lookup"><span data-stu-id="49d48-227">Build and run the application.</span></span> <span data-ttu-id="49d48-228">Geben Sie „sampleUsername“ ein, und klicken Sie auf „Anmelden“.</span><span class="sxs-lookup"><span data-stu-id="49d48-228">Login with "sampleUsername" and click login.</span></span> <span data-ttu-id="49d48-229">Geben Sie Ihre PIN ein. Bei erfolgreicher Eingabe werden Sie auf die Willkommensseite weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="49d48-229">Enter your PIN and if successful you should be navigated to the welcome screen.</span></span> <span data-ttu-id="49d48-230">Klicken Sie auf die Schaltfläche zum Löschen des Benutzers, und prüfen Sie im Ausgabefenster, ob der Benutzer gelöscht wurde.</span><span class="sxs-lookup"><span data-stu-id="49d48-230">Try clicking forget user and monitor the output window to see if the user was deleted.</span></span> <span data-ttu-id="49d48-231">Beachten Sie, dass nach dem Löschen des Benutzers weiterhin die Willkommensseite angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="49d48-231">Notice that when the user is deleted you remain on the welcome page.</span></span> <span data-ttu-id="49d48-232">Sie müssen eine Benutzerauswahlseite erstellen, zu der die App navigieren kann.</span><span class="sxs-lookup"><span data-stu-id="49d48-232">You will need to create a user selection page that the app can navigate to.</span></span>

    ![Windows-Hello-Begrüßungsseite](images/passport-login-9.png)

-   <span data-ttu-id="49d48-234">Erstellen Sie im Ordner „Views“ eine neue leere Seite mit dem Namen „UserSelection.xaml“, und fügen Sie den folgenden XAML-Code hinzu, um die Benutzeroberfläche zu definieren.</span><span class="sxs-lookup"><span data-stu-id="49d48-234">In the Views folder create a new blank page called "UserSelection.xaml" and add the following XAML to define the user interface.</span></span> <span data-ttu-id="49d48-235">Diese Seite enthält ein [**ListView**](https://msdn.microsoft.com/library/windows/apps/br242878)-Element, das alle Benutzer in der lokalen Kontenliste anzeigt, sowie eine Schaltfläche, über die der Benutzer zur Anmeldeseite navigieren und ein weiteres Konto hinzufügen kann.</span><span class="sxs-lookup"><span data-stu-id="49d48-235">This page will contain a [**ListView**](https://msdn.microsoft.com/library/windows/apps/br242878) that displays all the users in the local accounts list, and a Button that will navigate to the login page to allow the user to add another account.</span></span>

    ```xml
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
      <StackPanel Orientation="Vertical">
        <TextBlock x:Name="Title" Text="Select a User" FontSize="36" Margin="4" TextAlignment="Center" HorizontalAlignment="Center"/>

        <ListView x:Name="UserListView" Margin="4" MaxHeight="200" MinWidth="250" Width="250" HorizontalAlignment="Center">
          <ListView.ItemTemplate>
            <DataTemplate>
              <Grid Background="DodgerBlue" Height="50" Width="250" HorizontalAlignment="Stretch" VerticalAlignment="Stretch">
                <TextBlock Text="{Binding Username}" HorizontalAlignment="Center" TextAlignment="Center" VerticalAlignment="Center" Foreground="White"/>
              </Grid>
            </DataTemplate>
          </ListView.ItemTemplate>
        </ListView>

        <Button x:Name="AddUserButton" Content="+" FontSize="36" Width="60" Click="AddUserButton_Click" HorizontalAlignment="Center"/>
      </StackPanel>
    </Grid>
    ```

-   <span data-ttu-id="49d48-236">Implementieren Sie in „UserSelection.xaml.cs“ die geladene Methode, die zur Anmeldeseite navigiert, falls die lokale Liste keine Konten enthält.</span><span class="sxs-lookup"><span data-stu-id="49d48-236">In UserSelection.xaml.cs implement the loaded method that will navigate to the login page if there are no accounts in the local list.</span></span> <span data-ttu-id="49d48-237">Implementieren Sie außerdem das SelectionChanged-Ereignis für das ListView-Element und ein Klickereignis für die Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="49d48-237">Also implement the SelectionChanged event for the ListView and a click event for the Button.</span></span>

    ```cs
    using System.Diagnostics;
    using PassportLogin.Models;
    using PassportLogin.Utils;

    namespace PassportLogin.Views
    {
        public sealed partial class UserSelection : Page
        {
            public UserSelection()
            {
                InitializeComponent();
                Loaded += UserSelection_Loaded;
            }

            private void UserSelection_Loaded(object sender, RoutedEventArgs e)
            {
                if (AccountHelper.AccountList.Count == 0)
                {
                    //If there are no accounts navigate to the LoginPage
                    Frame.Navigate(typeof(Login));
                }


                UserListView.ItemsSource = AccountHelper.AccountList;
                UserListView.SelectionChanged += UserSelectionChanged;
            }

            /// <summary>
            /// Function called when an account is selected in the list of accounts
            /// Navigates to the Login page and passes the chosen account
            /// </summary>
            private void UserSelectionChanged(object sender, RoutedEventArgs e)
            {
                if (((ListView)sender).SelectedValue != null)
                {
                    Account account = (Account)((ListView)sender).SelectedValue;
                    if (account != null)
                    {
                        Debug.WriteLine("Account " + account.Username + " selected!");
                    }
                    Frame.Navigate(typeof(Login), account);
                }
            }

            /// <summary>
            /// Function called when the "+" button is clicked to add a new user.
            /// Navigates to the Login page with nothing filled out
            /// </summary>
            private void AddUserButton_Click(object sender, RoutedEventArgs e)
            {
                Frame.Navigate(typeof(Login));
            }
        }
    }
    ```

<!-- -->

-   <span data-ttu-id="49d48-238">Es gibt einige Orte in der App, an denen eine Navigation zur UserSelection-Seite erfolgen soll.</span><span class="sxs-lookup"><span data-stu-id="49d48-238">There are a few places in the app where you want to navigated to the UserSelection page.</span></span> <span data-ttu-id="49d48-239">In „MainPage.xaml.cs“ müssen Sie anstatt zur Anmeldeseite zur UserSelection-Seite navigieren.</span><span class="sxs-lookup"><span data-stu-id="49d48-239">In MainPage.xaml.cs you should navigate to the UserSelection page instead of the Login page.</span></span> <span data-ttu-id="49d48-240">Während Sie sich in „MainPage“ im geladenen Ereignis befinden, müssen Sie die Kontenliste laden, damit von der UserSelection-Seite geprüft werden kann, ob Konten vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="49d48-240">While you are in the loaded event in MainPage you will need to load the accounts list so that the UserSelection page can check if there are any accounts.</span></span> <span data-ttu-id="49d48-241">Dies erfordert eine asynchrone Lademethode sowie einen Verweis auf den Ordner „Utils“.</span><span class="sxs-lookup"><span data-stu-id="49d48-241">This will require changing the loaded method to be async and also adding a reference to the Utils folder.</span></span>

    ```cs
    using PassportLogin.Utils;

    private async void MainPage_Loaded(object sender, RoutedEventArgs e)
    {
        // Load the local Accounts List before navigating to the UserSelection page
        await AccountHelper.LoadAccountListAsync();
        Frame.Navigate(typeof(UserSelection));
    }
    ```

-   <span data-ttu-id="49d48-242">Als Nächstes möchten Sie von der Willkommensseite zur UserSelection-Seite navigieren.</span><span class="sxs-lookup"><span data-stu-id="49d48-242">Next you will want to navigate to the UserSelection page from the Welcome page.</span></span> <span data-ttu-id="49d48-243">In beiden Klickereignissen müssen Sie wieder zur UserSelection-Seite navigieren.</span><span class="sxs-lookup"><span data-stu-id="49d48-243">In both click events you should navigate back to the UserSelection page.</span></span>

    ```cs
    private void Button_Restart_Click(object sender, RoutedEventArgs e)
    {
        Frame.Navigate(typeof(UserSelection));
    }

    private void Button_Forget_User_Click(object sender, RoutedEventArgs e)
    {
        // Remove it from Microsoft Passport
        MicrosoftPassportHelper.RemovePassportAccountAsync(_activeAccount);

        // Remove it from the local accounts list and resave the updated list
        AccountHelper.RemoveAccount(_activeAccount);

        Debug.WriteLine("User " + _activeAccount.Username + " deleted.");

        // Navigate back to UserSelection page.
        Frame.Navigate(typeof(UserSelection));
    }
    ```

-   <span data-ttu-id="49d48-244">Auf der Anmeldeseite benötigen Sie Code für die Anmeldung bei dem Konto, das in der Liste der UserSelection-Seite ausgewählt wurde.</span><span class="sxs-lookup"><span data-stu-id="49d48-244">In the Login page you need code to log in to the account selected from the list in the UserSelection page.</span></span> <span data-ttu-id="49d48-245">Speichern Sie im OnNavigatedTo-Ereignis das an die Navigation übergebene Konto.</span><span class="sxs-lookup"><span data-stu-id="49d48-245">In OnNavigatedTo event store the account passed to the navigation.</span></span> <span data-ttu-id="49d48-246">Fügen Sie zunächst eine neue private Variable hinzu, die angibt, ob es sich bei dem Konto um ein vorhandenes Konto handelt.</span><span class="sxs-lookup"><span data-stu-id="49d48-246">Start by adding a new private variable that will identify if the account is an existing account.</span></span> <span data-ttu-id="49d48-247">Behandeln Sie dann das OnNavigatedTo-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="49d48-247">Then handle the OnNavigatedTo event.</span></span>

    ```cs
    namespace PassportLogin.Views
    {
        public sealed partial class Login : Page
        {
            private Account _account;
            private bool _isExistingAccount;

            public Login()
            {
                InitializeComponent();
            }

            /// <summary>
            /// Function called when this frame is navigated to.
            /// Checks to see if Microsoft Passport is available and if an account was passed in.
            /// If an account was passed in set the "_isExistingAccount" flag to true and set the _account
            /// </summary>
            protected override async void OnNavigatedTo(NavigationEventArgs e)
            {
                // Check Microsoft Passport is setup and available on this machine
                if (await MicrosoftPassportHelper.MicrosoftPassportAvailableCheckAsync())
                {
                    if (e.Parameter != null)
                    {
                        _isExistingAccount = true;
                        // Set the account to the existing account being passed in
                        _account = (Account)e.Parameter;
                        UsernameTextBox.Text = _account.Username;
                        SignInPassport();
                    }
                }
                else
                {
                    // Microsoft Passport is not setup so inform the user
                    PassportStatus.Background = new SolidColorBrush(Windows.UI.Color.FromArgb(255, 50, 170, 207));
                    PassportStatusText.Text = "Microsoft Passport is not setup!\n" + 
                        "Please go to Windows Settings and set up a PIN to use it.";
                    PassportSignInButton.IsEnabled = false;
                }
            }
        }
    }
    ```

-   <span data-ttu-id="49d48-248">Die SignInPassport-Methode muss für die Anmeldung bei dem ausgewählten Konto aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="49d48-248">The SignInPassport method will need to be updated to sign in to the selected account.</span></span> <span data-ttu-id="49d48-249">Da für das Konto bereits ein Passport-Schlüssel erstellt wurde, benötigt „MicrosoftPassportHelper“ eine weitere Methode, um das Konto mit Passport zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="49d48-249">The MicrosoftPassportHelper will need another method to open the account with Passport, as the account already has a Passport key created for it.</span></span> <span data-ttu-id="49d48-250">Implementieren Sie die neue Methode in „MicrosoftPassportHelper.cs“, um einen vorhandenen Benutzer mit Passport anzumelden.</span><span class="sxs-lookup"><span data-stu-id="49d48-250">Implement the new method in MicrosoftPassportHelper.cs to sign in an existing user with passport.</span></span> <span data-ttu-id="49d48-251">Informationen zu den einzelnen Teilen des Codes finden Sie in den Codekommentaren.</span><span class="sxs-lookup"><span data-stu-id="49d48-251">For information on each part of the code please read through the code comments.</span></span>

    ```cs
    /// <summary>
    /// Attempts to sign a message using the Passport key on the system for the accountId passed.
    /// </summary>
    /// <returns>Boolean representing if creating the Passport authentication message succeeded</returns>
    public static async Task<bool> GetPassportAuthenticationMessageAsync(Account account)
    {
        KeyCredentialRetrievalResult openKeyResult = await KeyCredentialManager.OpenAsync(account.Username);
        // Calling OpenAsync will allow the user access to what is available in the app and will not require user credentials again.
        // If you wanted to force the user to sign in again you can use the following:
        // var consentResult = await Windows.Security.Credentials.UI.UserConsentVerifier.RequestVerificationAsync(account.Username);
        // This will ask for the either the password of the currently signed in Microsoft Account or the PIN used for Microsoft Passport.

        if (openKeyResult.Status == KeyCredentialStatus.Success)
        {
            // If OpenAsync has succeeded, the next thing to think about is whether the client application requires access to backend services.
            // If it does here you would Request a challenge from the Server. The client would sign this challenge and the server
            // would check the signed challenge. If it is correct it would allow the user access to the backend.
            // You would likely make a new method called RequestSignAsync to handle all this
            // e.g. RequestSignAsync(openKeyResult);
            // Refer to the second Microsoft Passport sample for information on how to do this.

            // For this sample there is not concept of a server implemented so just return true.
            return true;
        }
        else if (openKeyResult.Status == KeyCredentialStatus.NotFound)
        {
            // If the _account is not found at this stage. It could be one of two errors. 
            // 1. Microsoft Passport has been disabled
            // 2. Microsoft Passport has been disabled and re-enabled cause the Microsoft Passport Key to change.
            // Calling CreatePassportKey and passing through the account will attempt to replace the existing Microsoft Passport Key for that account.
            // If the error really is that Microsoft Passport is disabled then the CreatePassportKey method will output that error.
            if (await CreatePassportKeyAsync(account.Username))
            {
                // If the Passport Key was again successfully created, Microsoft Passport has just been reset.
                // Now that the Passport Key has been reset for the _account retry sign in.
                return await GetPassportAuthenticationMessageAsync(account);
            }
        }

        // Can't use Passport right now, try again later
        return false;
    }
    ```

-   <span data-ttu-id="49d48-252">Aktualisieren Sie die SignInPassport-Methode in „Login.xaml.cs“, um das vorhandene Konto zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="49d48-252">Update the SignInPassport method in Login.xaml.cs to handle the existing account.</span></span> <span data-ttu-id="49d48-253">Dadurch wird die neue Methode in „MicrosoftPassportHelper.cs“ verwendet.</span><span class="sxs-lookup"><span data-stu-id="49d48-253">This will use the new method in the MicrosoftPassportHelper.cs.</span></span> <span data-ttu-id="49d48-254">Ist der Vorgang erfolgreich, wird das Konto angemeldet, und der Benutzer wird auf die Willkommensseite weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="49d48-254">If successful the account will be signed in and the user navigated to the welcome screen.</span></span>

    ```cs
    private async void SignInPassport()
    {
        if (_isExistingAccount)
        {
            if (await MicrosoftPassportHelper.GetPassportAuthenticationMessageAsync(_account))
            {
                Frame.Navigate(typeof(Welcome), _account);
            }
        }
        else if (AccountHelper.ValidateAccountCredentials(UsernameTextBox.Text))
        {
            //Create and add a new local account
            _account = AccountHelper.AddAccount(UsernameTextBox.Text);
            Debug.WriteLine("Successfully signed in with traditional credentials and created local account instance!");

            if (await MicrosoftPassportHelper.CreatePassportKeyAsync(UsernameTextBox.Text))
            {
                Debug.WriteLine("Successfully signed in with Microsoft Passport!");
                Frame.Navigate(typeof(Welcome), _account);
            }
        }
        else
        {
            ErrorMessage.Text = "Invalid Credentials";
        }
    }
    ```

-   <span data-ttu-id="49d48-255">Erstellen Sie die Anwendung, und führen Sie sie aus.</span><span class="sxs-lookup"><span data-stu-id="49d48-255">Build and run the application.</span></span> <span data-ttu-id="49d48-256">Melden Sie sich mit „sampleUsername“ an.</span><span class="sxs-lookup"><span data-stu-id="49d48-256">Login with "sampleUsername".</span></span> <span data-ttu-id="49d48-257">Geben Sie Ihre PIN ein. Bei erfolgreicher Eingabe werden Sie auf die Willkommensseite weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="49d48-257">Type in your PIN and if successful you will be navigated to the Welcome screen.</span></span> <span data-ttu-id="49d48-258">Klicken Sie auf die Schaltfläche für die Rückkehr zur Benutzerliste.</span><span class="sxs-lookup"><span data-stu-id="49d48-258">Click back to user list.</span></span> <span data-ttu-id="49d48-259">Daraufhin wird ein einzelner Benutzer in der Liste angezeigt.</span><span class="sxs-lookup"><span data-stu-id="49d48-259">You should now see a user in the list.</span></span> <span data-ttu-id="49d48-260">Wenn Sie auf diesen Benutzer klicken, können Sie sich mithilfe von Passport direkt und ohne erneute Kennworteingabe erneut anmelden.</span><span class="sxs-lookup"><span data-stu-id="49d48-260">If you click on this Passport enables you to sign back in without having to re-enter any passwords etc.</span></span>

    ![Windows Hello - Benutzerliste auswählen](images/passport-login-10.png)

## <a name="exercise-3-registering-a-new-windows-hello-user"></a><span data-ttu-id="49d48-262">Übung 3: Registrieren eines neuen Windows-Hello-Benutzers</span><span class="sxs-lookup"><span data-stu-id="49d48-262">Exercise 3: Registering a new Windows Hello user</span></span>


<span data-ttu-id="49d48-263">In dieser Übung erstellen Sie eine neue Seite für die Erstellung eines neuen Windows-Hello-Kontos.</span><span class="sxs-lookup"><span data-stu-id="49d48-263">In this exercise you will be creating a new page that will create a new account with Windows Hello.</span></span> <span data-ttu-id="49d48-264">Das funktioniert ähnlich wie bei der Anmeldeseite.</span><span class="sxs-lookup"><span data-stu-id="49d48-264">This will work similarly to how the Login page works.</span></span> <span data-ttu-id="49d48-265">Die Anmeldeseite wird für einen vorhandenen Benutzer implementiert, der für die Verwendung von Windows Hello migriert wird.</span><span class="sxs-lookup"><span data-stu-id="49d48-265">The Login page is implemented for an existing user that is migrating to use Windows Hello.</span></span> <span data-ttu-id="49d48-266">Eine PassportRegister-Seite erstellt die Windows-Hello-Registrierung für einen neuen Benutzer.</span><span class="sxs-lookup"><span data-stu-id="49d48-266">A PassportRegister page will create Windows Hello registration for a new user.</span></span>

-   <span data-ttu-id="49d48-267">Erstellen Sie im Ordner „Views“ eine neue leere Seite namens „PassportRegister.xaml“.</span><span class="sxs-lookup"><span data-stu-id="49d48-267">In the views folder create a new blank page called "PassportRegister.xaml".</span></span> <span data-ttu-id="49d48-268">Fügen Sie dem XAML-Code Folgendes hinzu, um die Benutzeroberfläche einzurichten.</span><span class="sxs-lookup"><span data-stu-id="49d48-268">In the XAML add in the following to setup the user interface.</span></span> <span data-ttu-id="49d48-269">Diese Benutzeroberfläche ähnelt der Benutzeroberfläche für die Anmeldeseite.</span><span class="sxs-lookup"><span data-stu-id="49d48-269">The interface here is similar to the Login page.</span></span>

    ```xml
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
      <StackPanel Orientation="Vertical">
        <TextBlock x:Name="Title" Text="Register New Passport User" FontSize="24" Margin="4" TextAlignment="Center"/>

        <TextBlock x:Name="ErrorMessage" Text="" FontSize="20" Margin="4" Foreground="Red" TextAlignment="Center"/>

        <TextBlock Text="Enter your new username below" Margin="0,0,0,20"
                   TextWrapping="Wrap" Width="300"
                   TextAlignment="Center" VerticalAlignment="Center" FontSize="16"/>

        <TextBox x:Name="UsernameTextBox" Margin="4" Width="250"/>

        <Button x:Name="PassportRegisterButton" Content="Register" Background="DodgerBlue" Foreground="White"
            Click="RegisterButton_Click_Async" Width="80" HorizontalAlignment="Center" Margin="0,20"/>

        <Border x:Name="PassportStatus" Background="#22B14C"
                   Margin="4" Height="100">
          <TextBlock x:Name="PassportStatusText" Text="Microsoft Passport is ready to use!" FontSize="20"
                 Margin="4" TextAlignment="Center" VerticalAlignment="Center"/>
        </Border>
      </StackPanel>
    </Grid>
    ```

-   <span data-ttu-id="49d48-270">Implementieren Sie in der CodeBehind-Datei „PassportRegister.xaml.cs“ eine private Kontovariable und ein Klickereignis für die Registrierungsschaltfläche.</span><span class="sxs-lookup"><span data-stu-id="49d48-270">In the PassportRegister.xaml.cs code behind file implement a private Account variable and a click event for the register Button.</span></span> <span data-ttu-id="49d48-271">Dadurch wird ein neues lokales Konto hinzugefügt und ein Passport-Schlüssel erstellt.</span><span class="sxs-lookup"><span data-stu-id="49d48-271">This will add a new local account and create a Passport key.</span></span>

    ```cs
    using PassportLogin.Models;
    using PassportLogin.Utils;

    namespace PassportLogin.Views
    {
        public sealed partial class PassportRegister : Page
        {
            private Account _account;

            public PassportRegister()
            {
                InitializeComponent();
            }

            private async void RegisterButton_Click_Async(object sender, RoutedEventArgs e)
            {
                ErrorMessage.Text = "";

                //In the real world you would normally validate the entered credentials and information before 
                //allowing a user to register a new account. 
                //For this sample though we will skip that step and just register an account if username is not null.

                if (!string.IsNullOrEmpty(UsernameTextBox.Text))
                {
                    //Register a new account
                    _account = AccountHelper.AddAccount(UsernameTextBox.Text);
                    //Register new account with Microsoft Passport
                    await MicrosoftPassportHelper.CreatePassportKeyAsync(_account.Username);
                    //Navigate to the Welcome Screen. 
                    Frame.Navigate(typeof(Welcome), _account);
                }
                else
                {
                    ErrorMessage.Text = "Please enter a username";
                }
            }
        }
    }
    ```

-   <span data-ttu-id="49d48-272">Beim Klicken auf die Registrierungsschaltfläche muss von der Anmeldeseite zu dieser Seite navigiert werden.</span><span class="sxs-lookup"><span data-stu-id="49d48-272">You need to navigate to this page from the Login page when register is clicked.</span></span>

    ```cs
    private void RegisterButtonTextBlock_OnPointerPressed(object sender, PointerRoutedEventArgs e)
    {
        ErrorMessage.Text = "";
        Frame.Navigate(typeof(PassportRegister));
    }
    ```

-   <span data-ttu-id="49d48-273">Erstellen Sie die Anwendung, und führen Sie sie aus.</span><span class="sxs-lookup"><span data-stu-id="49d48-273">Build and run the application.</span></span> <span data-ttu-id="49d48-274">Versuchen Sie, einen neuen Benutzer zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="49d48-274">Try to register a new user.</span></span> <span data-ttu-id="49d48-275">Kehren Sie anschließend zur Benutzerliste zurück und vergewissern Sie sich, dass Sie den Benutzer auswählen und sich anmelden können.</span><span class="sxs-lookup"><span data-stu-id="49d48-275">Then return to the user list and validate that you can select that user and login.</span></span>

    ![Windows Hello - Registrieren neuer Benutzer](images/passport-login-11.png)

<span data-ttu-id="49d48-277">In dieser Übung wurden die Grundlagen für die Verwendung der neuen Windows-Hello-API zum Authentifizieren vorhandener Benutzer und zum Erstellen von Konten für neue Benutzer vermittelt.</span><span class="sxs-lookup"><span data-stu-id="49d48-277">In this lab you have learned the essential skills you need to use the new Windows Hello API to authenticate existing users and create accounts for new users.</span></span> <span data-ttu-id="49d48-278">Dank dieser neuen Kenntnisse müssen sich die Benutzer bald keine Kennwörter für Ihre Anwendung mehr merken, während gleichzeitig der Schutz durch die Benutzerauthentifizierung erhalten bleibt.</span><span class="sxs-lookup"><span data-stu-id="49d48-278">With this new knowledge you can start removing the need for users to remember passwords for your application, yet remain confident that your applications remain protected by user authentication.</span></span> <span data-ttu-id="49d48-279">Windows10 verwendet die neue Authentifizierung-Technologie von Windows Hello zur Unterstützung der biometrischen Anmeldungsoptionen.</span><span class="sxs-lookup"><span data-stu-id="49d48-279">Windows 10 uses Windows Hello's new authentication technology to support its biometrics login options.</span></span>

## <a name="related-topics"></a><span data-ttu-id="49d48-280">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="49d48-280">Related topics</span></span>

* [<span data-ttu-id="49d48-281">Windows Hello</span><span class="sxs-lookup"><span data-stu-id="49d48-281">Windows Hello</span></span>](microsoft-passport.md)
* [<span data-ttu-id="49d48-282">Windows-Hello-Anmeldedienst</span><span class="sxs-lookup"><span data-stu-id="49d48-282">Windows Hello login service</span></span>](microsoft-passport-login-auth-service.md)
