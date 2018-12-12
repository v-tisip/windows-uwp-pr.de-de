---
Description: Simulate and automate input from devices such as keyboard, mouse, touch, pen, and gamepad in your UWP apps.
title: Simulieren der Benutzereingabe über die Eingabeeinfügung
label: Input injection
template: detail.hbs
keywords: Gerät, Digitalisierer, Eingabe, Interaktion, Einfügung
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: de3f0b1377d4f4209dc012ff56adb2de9c68625f
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8933974"
---
# <a name="simulate-user-input-through-input-injection"></a><span data-ttu-id="f39ee-103">Simulieren der Benutzereingabe über die Eingabeeinfügung</span><span class="sxs-lookup"><span data-stu-id="f39ee-103">Simulate user input through input injection</span></span>

<span data-ttu-id="f39ee-104">Sie können Benutzereingaben über Geräte wie Tastatur, Maus, Touch, Stift und Gamepad in Ihren UWP-Anwendungen simulieren und automatisieren.</span><span class="sxs-lookup"><span data-stu-id="f39ee-104">Simulate and automate user input from devices such as keyboard, mouse, touch, pen, and gamepad in your UWP applications.</span></span>

> <span data-ttu-id="f39ee-105">**Wichtige APIs**: [**Windows.UI.Input.Preview.Injection**](https://docs.microsoft.com/uwp/api/windows.ui.input.preview.injection)</span><span class="sxs-lookup"><span data-stu-id="f39ee-105">**Important APIs**: [**Windows.UI.Input.Preview.Injection**](https://docs.microsoft.com/uwp/api/windows.ui.input.preview.injection)</span></span>

## <a name="overview"></a><span data-ttu-id="f39ee-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="f39ee-106">Overview</span></span>

<span data-ttu-id="f39ee-107">Über die Eingabeeinfügung kann Ihre UWP-Anwendung die Eingabe über eine Vielzahl von Eingabegeräten simulieren und diese Eingabe überall hinleiten, z.B. außerhalb des Clientbereichs Ihrer App (selbst zu Apps, die mit Administratorberechtigungen ausgeführt werden, wie etwa der Registrierungs-Editor).</span><span class="sxs-lookup"><span data-stu-id="f39ee-107">Input injection enables your UWP application to simulate input from a variety of input devices and direct that input anywhere, including outside your app's client area (even to apps running with Adminstrator privileges, such as the Registry Editor).</span></span>

<span data-ttu-id="f39ee-108">Die Eingabeeinfügung ist nützlich für UWP-Apps und -Tools, die eine Funktionalität mit Bedienungshilfen, Testfunktionen (ad hoc, automatisiert) und Remotezugriff sowie Supportfeatures bereitstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="f39ee-108">Input injection is useful for UWP apps and tools that need to provide functionality that includes accessibility, testing (ad-hoc, automated), and remote access and support features.</span></span>

## <a name="setup"></a><span data-ttu-id="f39ee-109">Setup</span><span class="sxs-lookup"><span data-stu-id="f39ee-109">Setup</span></span>

<span data-ttu-id="f39ee-110">Um die Eingabeeinfügungs-APIs in Ihrer UWP-App verwenden zu können, müssen Sie Folgendes zum App-Manifest hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="f39ee-110">To use the input injection APIs in your UWP app you'll need to add the following to the app manifest:</span></span>

1. <span data-ttu-id="f39ee-111">Klicken Sie mit der rechten Maustaste auf die Datei **Package.appxmanifest**, und wählen Sie die Option **Code anzeigen** aus.</span><span class="sxs-lookup"><span data-stu-id="f39ee-111">Right click the **Package.appxmanifest** file and select **View code**.</span></span>
1. <span data-ttu-id="f39ee-112">Fügen Sie Folgendes in den Knoten `Package` ein:</span><span class="sxs-lookup"><span data-stu-id="f39ee-112">Insert the following into the `Package` node:</span></span>
    - `xmlns:rescap="http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities"`
    - `IgnorableNamespaces="rescap"`
1. <span data-ttu-id="f39ee-113">Fügen Sie Folgendes in den Knoten `Capabilities` ein:</span><span class="sxs-lookup"><span data-stu-id="f39ee-113">Insert the following into the `Capabilities` node:</span></span>
    - `<rescap:Capability Name="inputInjectionBrokered" />`

## <a name="duplicate-user-input"></a><span data-ttu-id="f39ee-114">Duplizieren der Benutzereingabe</span><span class="sxs-lookup"><span data-stu-id="f39ee-114">Duplicate user input</span></span>

| ![Beispiel für die Touch-Eingabeeinfügung](images/injection/touch-input-injection.gif) | 
|:--:|
| *<span data-ttu-id="f39ee-116">Beispiel für die Touch-Eingabeeinfügung</span><span class="sxs-lookup"><span data-stu-id="f39ee-116">Touch input injection sample</span></span>* |

<span data-ttu-id="f39ee-117">In diesem Beispiel wird veranschaulicht, wie Sie die Eingabeeinfügungs-APIs ([Windows.UI.Input.Preview.Injection](https://docs.microsoft.com/uwp/api/windows.ui.input.preview.injection)) verwenden, um Mauseingabeereignisse in einem Bereich einer App zu überwachen und entsprechende Toucheingabe-Ereignisse in einem anderen Bereich zu simulieren.</span><span class="sxs-lookup"><span data-stu-id="f39ee-117">In this example, we demonstrate how to use the input injection APIs ([Windows.UI.Input.Preview.Injection](https://docs.microsoft.com/uwp/api/windows.ui.input.preview.injection)) to listen for mouse input events in one region of an app, and simulate corresponding touch input events in another region.</span></span>

**<span data-ttu-id="f39ee-118">Laden Sie dieses Beispiel unter [Beispiel für Eingabeeinfügung (Maus zu Touch)](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-input-injection-mouse-to-touch.zip) herunter.</span><span class="sxs-lookup"><span data-stu-id="f39ee-118">Download this sample from [Input injection sample (mouse to touch)](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-input-injection-mouse-to-touch.zip)</span></span>**

1. <span data-ttu-id="f39ee-119">Zunächst richten wir die Benutzeroberfläche ein (MainPage.xaml).</span><span class="sxs-lookup"><span data-stu-id="f39ee-119">First, we set up the UI (MainPage.xaml).</span></span>

    <span data-ttu-id="f39ee-120">Wir verfügen über zwei Rasterbereiche (einen für die Mauseingabe und einen für die eingefügte Toucheingabe), jeweils mit vier Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="f39ee-120">We have two Grid areas (one for mouse input and one for injected touch input), each with four buttons.</span></span>
       > [!NOTE] The Grid background must be assigned a value (`Transparent`, in this case), otherwise pointer events are not detected.

    <span data-ttu-id="f39ee-121">Wenn im Eingabebereich Mausklicks erkannt werden, wird ein entsprechendes Touchereignis in den Eingabeeinfügungsbereich eingefügt.</span><span class="sxs-lookup"><span data-stu-id="f39ee-121">When any mouse clicks are detected in the input area, a corresponding touch event is injected into the input injection area.</span></span> <span data-ttu-id="f39ee-122">Klicks auf Schaltflächen von der Eingabeeinfügung werden im Titelbereich gemeldet.</span><span class="sxs-lookup"><span data-stu-id="f39ee-122">Button clicks from inject input are reported in the title area.</span></span>

    ```xaml
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto"/>
            <RowDefinition Height="Auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
        <StackPanel Grid.Row="0"
                    Margin="10">
            <TextBlock Style="{ThemeResource TitleTextBlockStyle}" 
                       Name="titleText"
                       Text="Touch input injection"
                       HorizontalTextAlignment="Center" />
            <TextBlock Style="{ThemeResource BodyTextBlockStyle}"
                       Name="statusText"
                       HorizontalTextAlignment="Center" />
        </StackPanel>
        <Grid HorizontalAlignment="Center"
                        Grid.Row="1">
            <Grid.RowDefinitions>
                <RowDefinition Height="Auto"/>
                <RowDefinition Height="*"/>
            </Grid.RowDefinitions>
            <Grid.ColumnDefinitions>
                <ColumnDefinition/>
                <ColumnDefinition/>
            </Grid.ColumnDefinitions>
            <TextBlock Grid.Column="0" 
                       Grid.Row="0" 
                       Style="{ThemeResource CaptionTextBlockStyle}"
                       Text="User mouse input area"/>
            <!-- Background must be set to something, otherwise pointer events are not detected. -->
            <Grid Name="ContainerInput" 
                  Grid.Column="0" 
                  Grid.Row="1"
                  HorizontalAlignment="Stretch" 
                  Background="Transparent" 
                  BorderBrush="Green" 
                  BorderThickness="2" 
                  MinHeight="100" MinWidth="300" 
                  Margin="10">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition/>
                    <ColumnDefinition/>
                    <ColumnDefinition/>
                    <ColumnDefinition/>
                </Grid.ColumnDefinitions>
                <Button Name="B1" 
                        Grid.Column="0" 
                        HorizontalAlignment="Center" 
                        Width="50" Height="50"
                        Content="B1" />
                <Button Name="B2" 
                        Grid.Column="1" 
                        HorizontalAlignment="Center" 
                        Width="50" Height="50"
                        Content="B2" />
                <Button Name="B3" 
                        Grid.Column="2" 
                        HorizontalAlignment="Center" 
                        Width="50" Height="50"
                        Content="B3" />
                <Button Name="B4" 
                        Grid.Column="3" 
                        HorizontalAlignment="Center" 
                        Width="50" Height="50"
                        Content="B4" />
            </Grid>
            <TextBlock Grid.Column="1" 
                       Grid.Row="0"                         
                       Style="{ThemeResource CaptionTextBlockStyle}"
                       Text="Injected touch input area"/>
            <Grid Name="ContainerInject"
                  Grid.Column="1"  
                  Grid.Row="1"
                  HorizontalAlignment="Stretch"
                  BorderBrush="Red" 
                  BorderThickness="2" 
                  MinHeight="100" MinWidth="300" 
                  Margin="10">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition/>
                    <ColumnDefinition/>
                    <ColumnDefinition/>
                    <ColumnDefinition/>
                </Grid.ColumnDefinitions>
                <Button Name="B1i" Click="Button_Click_Injected"
                        Content="B1i"
                        Grid.Column="0" 
                        HorizontalAlignment="Center" 
                        Width="50" Height="50" />
                <Button Name="B2i" Click="Button_Click_Injected"
                        Content="B2i"
                        Grid.Column="1" 
                        HorizontalAlignment="Center" 
                        Width="50" Height="50" />
                <Button Name="B3i" Click="Button_Click_Injected"
                        Content="B3i"
                        Grid.Column="2" 
                        HorizontalAlignment="Center" 
                        Width="50" Height="50" />
                <Button Name="B4i" Click="Button_Click_Injected"
                        Content="B4i"
                        Grid.Column="3" 
                        HorizontalAlignment="Center" 
                        Width="50" Height="50" />
            </Grid>
        </Grid>
    </Grid>
    ```

2. <span data-ttu-id="f39ee-123">Als Nächstes initialisieren wir unsere App.</span><span class="sxs-lookup"><span data-stu-id="f39ee-123">Next, we initialize our app.</span></span>
    
    <span data-ttu-id="f39ee-124">In diesem Codeausschnitt deklarieren wir unsere globalen Objekte und Listener für Zeigerereignisse ([AddHandler](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.addhandler)) innerhalb des Mauseingabebereichs, die in den Schaltflächenklickereignissen möglicherweise als verarbeitet gekennzeichnet sind.</span><span class="sxs-lookup"><span data-stu-id="f39ee-124">In this snippet, we declare our global objects and declare listeners for pointer events ([AddHandler](https://docs.microsoft.com/uwp/api/windows.ui.xaml.uielement.addhandler)) within the mouse input area that might be marked as handled in the button click events.</span></span>

    <span data-ttu-id="f39ee-125">Das [InputInjector](https://docs.microsoft.com/api/windows.ui.input.preview.injection.inputinjector)-Objekt stellt das virtuelle Eingabegerät zum Senden der eingegebenen Daten dar.</span><span class="sxs-lookup"><span data-stu-id="f39ee-125">The [InputInjector](https://docs.microsoft.com/api/windows.ui.input.preview.injection.inputinjector) object represents the virtual input device for sending the input data.</span></span>

    <span data-ttu-id="f39ee-126">Im Handler `ContainerInput_PointerPressed` rufen wir die Toucheinfügungsfunktion auf.</span><span class="sxs-lookup"><span data-stu-id="f39ee-126">In the `ContainerInput_PointerPressed` handler we call the touch injection function.</span></span>

    <span data-ttu-id="f39ee-127">Im Handler `ContainerInput_PointerReleased` rufen wir UninitializeTouchInjection auf, um das [InputInjector](https://docs.microsoft.com/api/windows.ui.input.preview.injection.inputinjector)-Objekt zu beenden.</span><span class="sxs-lookup"><span data-stu-id="f39ee-127">In the `ContainerInput_PointerReleased` handler, we call UninitializeTouchInjection to shut down the [InputInjector](https://docs.microsoft.com/api/windows.ui.input.preview.injection.inputinjector) object.</span></span>

    ```csharp
    public sealed partial class MainPage : Page
    {
        /// <summary>
        /// The virtual input device.
        /// </summary>
        InputInjector _inputInjector;

        /// <summary>
        /// Initialize the app, set the window size, 
        /// and add pointer input handlers for the container.
        /// </summary>
        public MainPage()
        {
            this.InitializeComponent();

            ApplicationView.PreferredLaunchViewSize =
                new Size(600, 200);
            ApplicationView.PreferredLaunchWindowingMode =
                ApplicationViewWindowingMode.PreferredLaunchViewSize;

            // Button handles PointerPressed/PointerReleased in 
            // the Tapped routed event, but we need the container Grid 
            // to handle them also. Add a handler for both 
            // PointerPressedEvent and PointerReleasedEvent on the input Grid 
            // and set handledEventsToo to true.
            ContainerInput.AddHandler(PointerPressedEvent,
                new PointerEventHandler(ContainerInput_PointerPressed), true);
            ContainerInput.AddHandler(PointerReleasedEvent,
                new PointerEventHandler(ContainerInput_PointerReleased), true);
        }

        /// <summary>
        /// PointerReleased handler for all pointer conclusion events.
        /// PointerPressed and PointerReleased events do not always occur 
        /// in pairs, so your app should listen for and handle any event that 
        /// might conclude a pointer down (such as PointerExited, PointerCanceled, 
        /// and PointerCaptureLost).  
        /// </summary>
        /// <param name="sender">Source of the click event</param>
        /// <param name="e">Event args for the button click routed event</param>
        private void ContainerInput_PointerReleased(
            object sender, PointerRoutedEventArgs e)
        {
            // Prevent most handlers along the event route from handling event again.
            e.Handled = true;

            // Shut down the virtual input device.
            _inputInjector.UninitializeTouchInjection();
        }

        /// <summary>
        /// PointerPressed handler.
        /// PointerPressed and PointerReleased events do not always occur 
        /// in pairs. Your app should listen for and handle any event that 
        /// might conclude a pointer down (such as PointerExited, 
        /// PointerCanceled, and PointerCaptureLost).  
        /// </summary>
        /// <param name="sender">Source of the click event</param>
        /// <param name="e">Event args for the button click routed event</param>
        private void ContainerInput_PointerPressed(
            object sender, PointerRoutedEventArgs e)
        {
            // Prevent most handlers along the event route from 
            // handling the same event again.
            e.Handled = true;

            InjectTouchForMouse(e.GetCurrentPoint(ContainerInput));

        }
        ...
    }
    ```
3. <span data-ttu-id="f39ee-128">Dies ist die Toucheingabeeinfügungsfunktion.</span><span class="sxs-lookup"><span data-stu-id="f39ee-128">Here's the touch input injection function.</span></span>

    <span data-ttu-id="f39ee-129">Zuerst rufen wir [TryCreate](https://docs.microsoft.com/uwp/api/windows.ui.input.preview.injection.inputinjector.trycreate) auf, um das [InputInjector](https://docs.microsoft.com/api/windows.ui.input.preview.injection.inputinjector)-Objekt zu instanziieren.</span><span class="sxs-lookup"><span data-stu-id="f39ee-129">First, we call [TryCreate](https://docs.microsoft.com/uwp/api/windows.ui.input.preview.injection.inputinjector.trycreate) to instantiate the [InputInjector](https://docs.microsoft.com/api/windows.ui.input.preview.injection.inputinjector) object.</span></span>

    <span data-ttu-id="f39ee-130">Anschließend rufen wir [InitializeTouchInjection](https://docs.microsoft.com/uwp/api/windows.ui.input.preview.injection.inputinjector.initializetouchinjection) mit dem [InjectedInputVisualizationMode](https://docs.microsoft.com/uwp/api/windows.ui.input.preview.injection.injectedinputvisualizationmode) von `Default` auf.</span><span class="sxs-lookup"><span data-stu-id="f39ee-130">Then, we call [InitializeTouchInjection](https://docs.microsoft.com/uwp/api/windows.ui.input.preview.injection.inputinjector.initializetouchinjection) with an [InjectedInputVisualizationMode](https://docs.microsoft.com/uwp/api/windows.ui.input.preview.injection.injectedinputvisualizationmode) of `Default`.</span></span>

    <span data-ttu-id="f39ee-131">Nach der Berechnung des Einfügungspunktes rufen wir [InjectedInputTouchInfo](https://docs.microsoft.com/uwp/api/windows.ui.input.preview.injection.injectedinputtouchinfo) auf, um die Liste der Touchpunkte zum Einfügen zu initialisieren (in diesem Beispiel erstellen wir einen Touchpunkt entsprechend dem Mauseingabezeiger).</span><span class="sxs-lookup"><span data-stu-id="f39ee-131">After calculating the point of injection, we call [InjectedInputTouchInfo](https://docs.microsoft.com/uwp/api/windows.ui.input.preview.injection.injectedinputtouchinfo) to initialize the list of touch points to inject (for this example, we create one touch point corresponding to the mouse input pointer).</span></span>

    <span data-ttu-id="f39ee-132">Abschließend rufen wir zweimal [InjectTouchInput](https://docs.microsoft.com/uwp/api/windows.ui.input.preview.injection.inputinjector.injecttouchinput) auf, einmal für einen Zeiger nach unten und einmal für einen Zeiger nach oben.</span><span class="sxs-lookup"><span data-stu-id="f39ee-132">Finally, we call [InjectTouchInput](https://docs.microsoft.com/uwp/api/windows.ui.input.preview.injection.inputinjector.injecttouchinput) twice, the first for a pointer down and the second for a pointer up.</span></span>

    ```csharp
    /// <summary>
    /// Inject touch input on injection target corresponding 
    /// to mouse click on input target.
    /// </summary>
    /// <param name="pointerPoint">The mouse click pointer.</param>
    private void InjectTouchForMouse(PointerPoint pointerPoint)
    {
        // Create the touch injection object.
        _inputInjector = InputInjector.TryCreate();

        if (_inputInjector != null)
        {
            _inputInjector.InitializeTouchInjection(
                InjectedInputVisualizationMode.Default);

            // Create a unique pointer ID for the injected touch pointer.
            // Multiple input pointers would require more robust handling.
            uint pointerId = pointerPoint.PointerId + 1;

            // Get the bounding rectangle of the app window.
            Rect appBounds =
                Windows.UI.ViewManagement.ApplicationView.GetForCurrentView().VisibleBounds;

            // Get the top left screen coordinates of the app window rect.
            Point appBoundsTopLeft = new Point(appBounds.Left, appBounds.Top);

            // Get a reference to the input injection area.
            GeneralTransform injectArea =
                ContainerInject.TransformToVisual(Window.Current.Content);

            // Get the top left screen coordinates of the input injection area.
            Point injectAreaTopLeft = injectArea.TransformPoint(new Point(0, 0));

            // Get the screen coordinates (relative to the input area) 
            // of the input pointer.
            int pointerPointX = (int)pointerPoint.Position.X;
            int pointerPointY = (int)pointerPoint.Position.Y;

            // Create the point for input injection and calculate its screen location.
            Point injectionPoint =
                new Point(
                    appBoundsTopLeft.X + injectAreaTopLeft.X + pointerPointX,
                    appBoundsTopLeft.Y + injectAreaTopLeft.Y + pointerPointY);

            // Create a touch data point for pointer down.
            // Each element in the touch data list represents a single touch contact. 
            // For this example, we're mirroring a single mouse pointer.
            List<InjectedInputTouchInfo> touchData =
                new List<InjectedInputTouchInfo>
                {
                    new InjectedInputTouchInfo
                    {
                        Contact = new InjectedInputRectangle
                        {
                            Left = 30, Top = 30, Bottom = 30, Right = 30
                        },
                        PointerInfo = new InjectedInputPointerInfo
                        {
                            PointerId = pointerId,
                            PointerOptions =
                            InjectedInputPointerOptions.PointerDown |
                            InjectedInputPointerOptions.InContact |
                            InjectedInputPointerOptions.New,
                            TimeOffsetInMilliseconds = 0,
                            PixelLocation = new InjectedInputPoint
                            {
                                PositionX = (int)injectionPoint.X ,
                                PositionY = (int)injectionPoint.Y
                            }
                    },
                    Pressure = 1.0,
                    TouchParameters =
                        InjectedInputTouchParameters.Pressure |
                        InjectedInputTouchParameters.Contact
                }
            };

            // Inject the touch input. 
            _inputInjector.InjectTouchInput(touchData);

            // Create a touch data point for pointer up.
            touchData = new List<InjectedInputTouchInfo>
            {
                new InjectedInputTouchInfo
                {
                    PointerInfo = new InjectedInputPointerInfo
                    {
                        PointerId = pointerId,
                        PointerOptions = InjectedInputPointerOptions.PointerUp
                    }
                }
            };

            // Inject the touch input. 
            _inputInjector.InjectTouchInput(touchData);
        }
    }
    ```

4. <span data-ttu-id="f39ee-133">Schließlich verarbeiten wir alle [Click](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.primitives.buttonbase)-Weiterleitungsereignisse im Eingabeeinfügungsbereich und aktualisieren die Benutzeroberfläche mit dem Namen der angeklickten Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="f39ee-133">Finally, we handle any Button [Click](https://docs.microsoft.com/uwp/api/windows.ui.xaml.controls.primitives.buttonbase) routed events in the input injection area and update the UI with the name of the button clicked.</span></span>

## <a name="see-also"></a><span data-ttu-id="f39ee-134">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="f39ee-134">See also</span></span>

### <a name="topic-samples"></a><span data-ttu-id="f39ee-135">Themenbeispiele</span><span class="sxs-lookup"><span data-stu-id="f39ee-135">Topic samples</span></span>

- [<span data-ttu-id="f39ee-136">Beispiel für Eingabeeinfügung (Maus zu Touch)</span><span class="sxs-lookup"><span data-stu-id="f39ee-136">Input injection sample (mouse to touch)</span></span>](https://github.com/MicrosoftDocs/windows-topic-specific-samples/archive/uwp-input-injection-mouse-to-touch.zip)
