---
ms.assetid: 90BB59FC-90FE-453E-A8DE-9315E29EB98C
title: Abrufen von Akkuinformationen
description: Erfahren Sie, wie Sie mithilfe von APIs im Windows.Devices.Power-Namespace ausführliche Akkuinformationen erhalten
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 81f4232d038b89f2c49cf584346d632911fb70e2
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8695249"
---
# <a name="get-battery-information"></a><span data-ttu-id="6a2c9-104">Abrufen von Akkuinformationen</span><span class="sxs-lookup"><span data-stu-id="6a2c9-104">Get battery information</span></span>


<span data-ttu-id="6a2c9-105">\*\* Wichtige APIs \*\*</span><span class="sxs-lookup"><span data-stu-id="6a2c9-105">\*\* Important APIs \*\*</span></span>

-   [**<span data-ttu-id="6a2c9-106">Windows.Devices.Power</span><span class="sxs-lookup"><span data-stu-id="6a2c9-106">Windows.Devices.Power</span></span>**](https://msdn.microsoft.com/library/windows/apps/Dn895017)
-   [**<span data-ttu-id="6a2c9-107">DeviceInformation.FindAllAsync</span><span class="sxs-lookup"><span data-stu-id="6a2c9-107">DeviceInformation.FindAllAsync</span></span>**](https://msdn.microsoft.com/library/windows/apps/BR225432)

<span data-ttu-id="6a2c9-108">Erfahren Sie, wie Sie mithilfe von APIs im [**Windows.Devices.Power**](https://msdn.microsoft.com/library/windows/apps/Dn895017)-Namespace ausführliche Akkuinformationen erhalten</span><span class="sxs-lookup"><span data-stu-id="6a2c9-108">Learn how to get detailed battery information using APIs in the [**Windows.Devices.Power**](https://msdn.microsoft.com/library/windows/apps/Dn895017) namespace.</span></span> <span data-ttu-id="6a2c9-109">In einem *Akkubericht* ([**BatteryReport**](https://msdn.microsoft.com/library/windows/apps/Dn895005)) werden der Ladezustand, die Kapazität und der Status eines Akkus oder Akkuaggregats beschrieben.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-109">A *battery report* ([**BatteryReport**](https://msdn.microsoft.com/library/windows/apps/Dn895005)) describes the charge, capacity, and status of a battery or aggregate of batteries.</span></span> <span data-ttu-id="6a2c9-110">In diesem Thema wird veranschaulicht, wie Ihre App Akkuberichte abrufen und über Veränderungen informiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-110">This topic demonstrates how your app can get battery reports and be notified of changes.</span></span> <span data-ttu-id="6a2c9-111">Die Codebeispiele stammen aus der einfachen Akku-App, die am Ende dieses Themas angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-111">Code examples are from the basic battery app that's listed at the end of this topic.</span></span>

## <a name="get-aggregate-battery-report"></a><span data-ttu-id="6a2c9-112">Abrufen eines zusammengefassten Akkuberichts</span><span class="sxs-lookup"><span data-stu-id="6a2c9-112">Get aggregate battery report</span></span>


<span data-ttu-id="6a2c9-113">Einige Geräte verfügen über mehr als einen Akku, und es ist nicht immer eindeutig, in welcher Form die einzelnen Akkus zur gesamten Energiekapazität des Geräts beitragen.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-113">Some devices have more than one battery and it's not always obvious how each battery contributes to the overall energy capacity of the device.</span></span> <span data-ttu-id="6a2c9-114">An dieser Stelle wird die [**AggregateBattery**](https://msdn.microsoft.com/library/windows/apps/Dn895011)-Klasse verwendet.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-114">This is where the [**AggregateBattery**](https://msdn.microsoft.com/library/windows/apps/Dn895011) class comes in.</span></span> <span data-ttu-id="6a2c9-115">*AggregateBattery* repräsentiert alle Akkucontroller, die mit dem Gerät verbunden sind. Damit kann ein zusammengefasstes [**BatteryReport**](https://msdn.microsoft.com/library/windows/apps/Dn895005)-Objekt bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-115">The *aggregate battery* represents all battery controllers connected to the device and can provide a single overall [**BatteryReport**](https://msdn.microsoft.com/library/windows/apps/Dn895005) object.</span></span>

<span data-ttu-id="6a2c9-116">**Hinweis:** eine [**den Akku**](https://msdn.microsoft.com/library/windows/apps/Dn895004) -Klasse entspricht einem akkucontroller.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-116">**Note**A [**Battery**](https://msdn.microsoft.com/library/windows/apps/Dn895004) class actually corresponds to a battery controller.</span></span> <span data-ttu-id="6a2c9-117">Je nach Gerät kann der Controller auch am physischen Akku angeschlossen sein, und es kommt auch vor, dass er am Gehäuse des Geräts angeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-117">Depending on the device, sometimes the controller is attached to the physical battery and sometimes it's attached to the device enclosure.</span></span> <span data-ttu-id="6a2c9-118">So kann auch dann ein Akkuobjekt erstellt werden, wenn keine Akkus vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-118">Thus, it's possible to create a battery object even when no batteries are present.</span></span> <span data-ttu-id="6a2c9-119">In anderen Fällen kann für das Akkuobjekt **null** gelten.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-119">Other times, the battery object may be **null**.</span></span>

<span data-ttu-id="6a2c9-120">Wenn Sie über ein zusammengefasstes Akkuobjekt verfügen, rufen Sie [**GetReport**](https://msdn.microsoft.com/library/windows/apps/windows.devices.power.battery.getreport) auf, um den entsprechenden [**BatteryReport**](https://msdn.microsoft.com/library/windows/apps/Dn895005) abzurufen.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-120">Once you have an aggregate battery object, call [**GetReport**](https://msdn.microsoft.com/library/windows/apps/windows.devices.power.battery.getreport) to get the corresponding [**BatteryReport**](https://msdn.microsoft.com/library/windows/apps/Dn895005).</span></span>

```csharp
private void RequestAggregateBatteryReport()
{
    // Create aggregate battery object
    var aggBattery = Battery.AggregateBattery;

    // Get report
    var report = aggBattery.GetReport();

    // Update UI
    AddReportUI(BatteryReportPanel, report, aggBattery.DeviceId);
}
```

## <a name="get-individual-battery-reports"></a><span data-ttu-id="6a2c9-121">Abrufen von individuellen Akkuberichten</span><span class="sxs-lookup"><span data-stu-id="6a2c9-121">Get individual battery reports</span></span>

<span data-ttu-id="6a2c9-122">Sie können auch ein [**BatteryReport**](https://msdn.microsoft.com/library/windows/apps/Dn895005)-Objekt für individuelle Akkus erstellen.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-122">You can also create a [**BatteryReport**](https://msdn.microsoft.com/library/windows/apps/Dn895005) object for individual batteries.</span></span> <span data-ttu-id="6a2c9-123">Verwenden Sie [**GetDeviceSelector**](https://msdn.microsoft.com/library/windows/apps/windows.devices.power.battery.getdeviceselector.aspx) mit der [**FindAllAsync**](https://msdn.microsoft.com/library/windows/apps/BR225432)-Methode zum Abrufen einer Sammlung mit [**DeviceInformation**](https://msdn.microsoft.com/library/windows/apps/BR225393)-Objekten, die alle mit dem Gerät verbundenen Akkucontroller repräsentieren.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-123">Use [**GetDeviceSelector**](https://msdn.microsoft.com/library/windows/apps/windows.devices.power.battery.getdeviceselector.aspx) with the [**FindAllAsync**](https://msdn.microsoft.com/library/windows/apps/BR225432) method to obtain a collection of [**DeviceInformation**](https://msdn.microsoft.com/library/windows/apps/BR225393) objects that represent any battery controllers that are connected to the device.</span></span> <span data-ttu-id="6a2c9-124">Erstellen Sie anschließend mit der **Id**-Eigenschaft des gewünschten **DeviceInformation**-Objekts ein entsprechendes [**Battery**](https://msdn.microsoft.com/library/windows/apps/Dn895004)-Element mit der Methode [**FromIdAsync**](https://msdn.microsoft.com/library/windows/apps/windows.devices.power.battery.fromidasync.aspx).</span><span class="sxs-lookup"><span data-stu-id="6a2c9-124">Then, using the **Id** property of the desired **DeviceInformation** object, create a corresponding [**Battery**](https://msdn.microsoft.com/library/windows/apps/Dn895004) with the [**FromIdAsync**](https://msdn.microsoft.com/library/windows/apps/windows.devices.power.battery.fromidasync.aspx) method.</span></span> <span data-ttu-id="6a2c9-125">Rufen Sie zuletzt [**GetReport**](https://msdn.microsoft.com/library/windows/apps/windows.devices.power.battery.getreport) auf, um den individuellen Akkubericht abzurufen.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-125">Finally, call [**GetReport**](https://msdn.microsoft.com/library/windows/apps/windows.devices.power.battery.getreport) to get the individual battery report.</span></span>

<span data-ttu-id="6a2c9-126">Dieses Beispiel zeigt, wie Sie einen Akkubericht für alle Akkus erstellen, die mit dem Gerät verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-126">This example shows how to create a battery report for all batteries connected to the device.</span></span>

```csharp
async private void RequestIndividualBatteryReports()
{
    // Find batteries 
    var deviceInfo = await DeviceInformation.FindAllAsync(Battery.GetDeviceSelector());
    foreach(DeviceInformation device in deviceInfo)
    {
        try
        {
        // Create battery object
        var battery = await Battery.FromIdAsync(device.Id);

        // Get report
        var report = battery.GetReport();

        // Update UI
        AddReportUI(BatteryReportPanel, report, battery.DeviceId);
        }
        catch { /* Add error handling, as applicable */ }
    }
}
```

## <a name="access-report-details"></a><span data-ttu-id="6a2c9-127">Zugreifen auf Berichtdetails</span><span class="sxs-lookup"><span data-stu-id="6a2c9-127">Access report details</span></span>

<span data-ttu-id="6a2c9-128">Das [**BatteryReport**](https://msdn.microsoft.com/library/windows/apps/Dn895005)-Objekt liefert zahlreiche Akkuinformationen.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-128">The [**BatteryReport**](https://msdn.microsoft.com/library/windows/apps/Dn895005) object provides a lot of battery information.</span></span> <span data-ttu-id="6a2c9-129">Weitere Informationen finden Sie in der API-Referenz für die Eigenschaften: **Status** (eine [**BatteryStatus**](https://msdn.microsoft.com/library/windows/apps/Dn818458)-Enumerierung), [**ChargeRateInMilliwatts**](https://msdn.microsoft.com/library/windows/apps/windows.devices.power.batteryreport.chargerateinmilliwatts.aspx), [**DesignCapacityInMilliwattHours**](https://msdn.microsoft.com/library/windows/apps/windows.devices.power.batteryreport.designcapacityinmilliwatthours.aspx), [**FullChargeCapacityInMilliwattHours**](https://msdn.microsoft.com/library/windows/apps/windows.devices.power.batteryreport.fullchargecapacityinmilliwatthours.aspx) und [**RemainingCapacityInMilliwattHours**](https://msdn.microsoft.com/library/windows/apps/windows.devices.power.batteryreport.remainingcapacityinmilliwatthours).</span><span class="sxs-lookup"><span data-stu-id="6a2c9-129">For more info, see the API reference for its properties: **Status** (a [**BatteryStatus**](https://msdn.microsoft.com/library/windows/apps/Dn818458) enumeration), [**ChargeRateInMilliwatts**](https://msdn.microsoft.com/library/windows/apps/windows.devices.power.batteryreport.chargerateinmilliwatts.aspx), [**DesignCapacityInMilliwattHours**](https://msdn.microsoft.com/library/windows/apps/windows.devices.power.batteryreport.designcapacityinmilliwatthours.aspx), [**FullChargeCapacityInMilliwattHours**](https://msdn.microsoft.com/library/windows/apps/windows.devices.power.batteryreport.fullchargecapacityinmilliwatthours.aspx), and [**RemainingCapacityInMilliwattHours**](https://msdn.microsoft.com/library/windows/apps/windows.devices.power.batteryreport.remainingcapacityinmilliwatthours).</span></span> <span data-ttu-id="6a2c9-130">Dieses Beispiel enthält einige Eigenschaften des Akkuberichts, die von der einfachen Akku-App verwendet werden. Die App wird weiter unten in diesem Thema bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-130">This example shows some of the battery report properties used by the basic battery app, that's provided later in this topic.</span></span>

```csharp
...
TextBlock txt3 = new TextBlock { Text = "Charge rate (mW): " + report.ChargeRateInMilliwatts.ToString() };
TextBlock txt4 = new TextBlock { Text = "Design energy capacity (mWh): " + report.DesignCapacityInMilliwattHours.ToString() };
TextBlock txt5 = new TextBlock { Text = "Fully-charged energy capacity (mWh): " + report.FullChargeCapacityInMilliwattHours.ToString() };
TextBlock txt6 = new TextBlock { Text = "Remaining energy capacity (mWh): " + report.RemainingCapacityInMilliwattHours.ToString() };
...
...
```

## <a name="request-report-updates"></a><span data-ttu-id="6a2c9-131">Anfordern von Berichtsaktualisierungen</span><span class="sxs-lookup"><span data-stu-id="6a2c9-131">Request report updates</span></span>

<span data-ttu-id="6a2c9-132">Das [**Battery**](https://msdn.microsoft.com/library/windows/apps/Dn895004)-Objekt löst das [**ReportUpdated**](https://msdn.microsoft.com/library/windows/apps/windows.devices.power.battery.reportupdated)-Ereignis aus, wenn sich Ladezustand, Kapazität oder Status des Akkus ändern.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-132">The [**Battery**](https://msdn.microsoft.com/library/windows/apps/Dn895004) object triggers the [**ReportUpdated**](https://msdn.microsoft.com/library/windows/apps/windows.devices.power.battery.reportupdated) event when charge, capacity, or status of the battery changes.</span></span> <span data-ttu-id="6a2c9-133">Dies geschieht für Statusänderungen in der Regel sofort, und für alle anderen Änderungen in regelmäßigen Abständen.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-133">This typically happens immediately for status changes and periodically for all other changes.</span></span> <span data-ttu-id="6a2c9-134">Dieses Beispiel zeigt, wie Sie die Registrierung für Aktualisierungen des Akkuberichts durchführen.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-134">This example shows how to register for battery report updates.</span></span>

```csharp
...
Battery.AggregateBattery.ReportUpdated += AggregateBattery_ReportUpdated;
...
```

## <a name="handle-report-updates"></a><span data-ttu-id="6a2c9-135">Behandeln von Berichtsaktualisierungen</span><span class="sxs-lookup"><span data-stu-id="6a2c9-135">Handle report updates</span></span>

<span data-ttu-id="6a2c9-136">Bei einer Aktualisierung des Akkuberichts übergibt das [**ReportUpdated**](https://msdn.microsoft.com/library/windows/apps/windows.devices.power.battery.reportupdated)-Ereignis das entsprechende [**Battery**](https://msdn.microsoft.com/library/windows/apps/Dn895004)-Objekt an die Ereignishandlermethode.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-136">When a battery update occurs, the [**ReportUpdated**](https://msdn.microsoft.com/library/windows/apps/windows.devices.power.battery.reportupdated) event passes the corresponding [**Battery**](https://msdn.microsoft.com/library/windows/apps/Dn895004) object to the event handler method.</span></span> <span data-ttu-id="6a2c9-137">Dieser Ereignishandler wird jedoch nicht über den UI-Thread aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-137">However, this event handler is not called from the UI thread.</span></span> <span data-ttu-id="6a2c9-138">Sie müssen das [**Dispatcher**](https://msdn.microsoft.com/library/windows/apps/BR208211)-Objekt verwenden, um UI-Änderungen aufzurufen. Dies wird im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-138">You'll need to use the [**Dispatcher**](https://msdn.microsoft.com/library/windows/apps/BR208211) object to invoke any UI changes, as shown in this example.</span></span>

```csharp
async private void AggregateBattery_ReportUpdated(Battery sender, object args)
{
    if (reportRequested)
    {

        await Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () =>
        {
            // Clear UI
            BatteryReportPanel.Children.Clear();


            if (AggregateButton.IsChecked == true)
            {
                // Request aggregate battery report
                RequestAggregateBatteryReport();
            }
            else
            {
                // Request individual battery report
                RequestIndividualBatteryReports();
            }
        });
    }
}
```

## <a name="example-basic-battery-app"></a><span data-ttu-id="6a2c9-139">Beispiel: einfache Akku-App</span><span class="sxs-lookup"><span data-stu-id="6a2c9-139">Example: basic battery app</span></span>

<span data-ttu-id="6a2c9-140">Testen Sie diese APIs, indem Sie die folgende einfache Akku-App in Microsoft Visual Studio erstellen.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-140">Test out these APIs by building the following basic battery app in Microsoft Visual Studio.</span></span> <span data-ttu-id="6a2c9-141">Klicken Sie auf der Startseite von Visual Studio auf **Neues Projekt**, und erstellen Sie dann im Bereich mit den Vorlagen unter **Visual C# &gt; Windows &gt; Universal** eine neue App, indem Sie die Vorlage **Leere App** verwenden.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-141">From the Visual Studio start page, click **New Project**, and then under the **Visual C# &gt; Windows &gt; Universal** templates, create a new app using the **Blank App** template.</span></span>

<span data-ttu-id="6a2c9-142">Öffnen Sie als Nächstes die Datei **MainPage.xaml**, und kopieren Sie den folgenden XML-Code in diese Datei, sodass der Originalinhalt ersetzt wird.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-142">Next, open the file **MainPage.xaml** and copy the following XML into this file (replacing its original contents).</span></span>

```xml
<Page
    x:Class="App1.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:App1"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d">

    <StackPanel Background="{ThemeResource ApplicationPageBackgroundThemeBrush}" >
        <StackPanel VerticalAlignment="Center" Margin="15,30,0,0" >
            <RadioButton x:Name="AggregateButton" Content="Aggregate results" GroupName="Type" IsChecked="True" />
            <RadioButton x:Name="IndividualButton" Content="Individual results" GroupName="Type" IsChecked="False" />
        </StackPanel>
        <StackPanel Orientation="Horizontal">
        <Button x:Name="GetBatteryReportButton" 
                Content="Get battery report" 
                Margin="15,15,0,0" 
                Click="GetBatteryReport"/>
        </StackPanel>
        <StackPanel x:Name="BatteryReportPanel" Margin="15,15,0,0"/>
    </StackPanel>
</Page>
```

<span data-ttu-id="6a2c9-143">Wenn Ihre App nicht den Namen **App1** hat, müssen Sie den ersten Teil des Klassennamens im vorhergehenden Codeausschnitt durch den Namespace Ihrer App ersetzen.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-143">If your app isn't named **App1**, you'll need to replace the first part of the class name in the previous snippet with the namespace of your app.</span></span> <span data-ttu-id="6a2c9-144">Wenn Sie z.B. ein Projekt mit dem Namen **BasicBatteryApp** erstellt haben, ersetzen Sie `x:Class="App1.MainPage"` durch `x:Class="BasicBatteryApp.MainPage"`.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-144">For example, if you created a project named **BasicBatteryApp**, you'd replace `x:Class="App1.MainPage"` with `x:Class="BasicBatteryApp.MainPage"`.</span></span> <span data-ttu-id="6a2c9-145">Außerdem sollten Sie `xmlns:local="using:App1"` durch `xmlns:local="using:BasicBatteryApp"` ersetzen.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-145">You should also replace `xmlns:local="using:App1"` with `xmlns:local="using:BasicBatteryApp"`.</span></span>

<span data-ttu-id="6a2c9-146">Öffnen Sie als Nächstes die Datei **MainPage.xaml.cs** des Projekts, und ersetzen Sie den vorhandenen Code durch Folgendes.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-146">Next, open your project's **MainPage.xaml.cs** file and replace the existing code with the following.</span></span>

```csharp
using System;
using Windows.UI.Xaml;
using Windows.UI.Xaml.Controls;
using Windows.UI.Xaml.Media;
using Windows.Devices.Enumeration;
using Windows.Devices.Power;
using Windows.UI.Core;

namespace App1
{
    public sealed partial class MainPage : Page
    {
        bool reportRequested = false;
        public MainPage()
        {
            this.InitializeComponent();
            Battery.AggregateBattery.ReportUpdated += AggregateBattery_ReportUpdated;
        }


        private void GetBatteryReport(object sender, RoutedEventArgs e)
        {
            // Clear UI
            BatteryReportPanel.Children.Clear();


            if (AggregateButton.IsChecked == true)
            {
                // Request aggregate battery report
                RequestAggregateBatteryReport();
            }
            else
            {
                // Request individual battery report
                RequestIndividualBatteryReports();
            }

            // Note request
            reportRequested = true;
        }

        private void RequestAggregateBatteryReport()
        {
            // Create aggregate battery object
            var aggBattery = Battery.AggregateBattery;

            // Get report
            var report = aggBattery.GetReport();

            // Update UI
            AddReportUI(BatteryReportPanel, report, aggBattery.DeviceId);
        }

        async private void RequestIndividualBatteryReports()
        {
            // Find batteries 
            var deviceInfo = await DeviceInformation.FindAllAsync(Battery.GetDeviceSelector());
            foreach(DeviceInformation device in deviceInfo)
            {
                try
                {
                // Create battery object
                var battery = await Battery.FromIdAsync(device.Id);

                // Get report
                var report = battery.GetReport();

                // Update UI
                AddReportUI(BatteryReportPanel, report, battery.DeviceId);
                }
                catch { /* Add error handling, as applicable */ }
            }
        }


        private void AddReportUI(StackPanel sp, BatteryReport report, string DeviceID)
        {
            // Create battery report UI
            TextBlock txt1 = new TextBlock { Text = "Device ID: " + DeviceID };
            txt1.FontSize = 15;
            txt1.Margin = new Thickness(0, 15, 0, 0);
            txt1.TextWrapping = TextWrapping.WrapWholeWords;

            TextBlock txt2 = new TextBlock { Text = "Battery status: " + report.Status.ToString() };
            txt2.FontStyle = Windows.UI.Text.FontStyle.Italic;
            txt2.Margin = new Thickness(0, 0, 0, 15);

            TextBlock txt3 = new TextBlock { Text = "Charge rate (mW): " + report.ChargeRateInMilliwatts.ToString() };
            TextBlock txt4 = new TextBlock { Text = "Design energy capacity (mWh): " + report.DesignCapacityInMilliwattHours.ToString() };
            TextBlock txt5 = new TextBlock { Text = "Fully-charged energy capacity (mWh): " + report.FullChargeCapacityInMilliwattHours.ToString() };
            TextBlock txt6 = new TextBlock { Text = "Remaining energy capacity (mWh): " + report.RemainingCapacityInMilliwattHours.ToString() };

            // Create energy capacity progress bar & labels
            TextBlock pbLabel = new TextBlock { Text = "Percent remaining energy capacity" };
            pbLabel.Margin = new Thickness(0,10, 0, 5);
            pbLabel.FontFamily = new FontFamily("Segoe UI");
            pbLabel.FontSize = 11;

            ProgressBar pb = new ProgressBar();
            pb.Margin = new Thickness(0, 5, 0, 0);
            pb.Width = 200;
            pb.Height = 10;
            pb.IsIndeterminate = false;
            pb.HorizontalAlignment = HorizontalAlignment.Left;

            TextBlock pbPercent = new TextBlock();
            pbPercent.Margin = new Thickness(0, 5, 0, 10);
            pbPercent.FontFamily = new FontFamily("Segoe UI");
            pbLabel.FontSize = 11;

            // Disable progress bar if values are null
            if ((report.FullChargeCapacityInMilliwattHours == null)||
                (report.RemainingCapacityInMilliwattHours == null))
            {
                pb.IsEnabled = false;
                pbPercent.Text = "N/A";
            }
            else
            {
                pb.IsEnabled = true;
                pb.Maximum = Convert.ToDouble(report.FullChargeCapacityInMilliwattHours);
                pb.Value = Convert.ToDouble(report.RemainingCapacityInMilliwattHours);
                pbPercent.Text = ((pb.Value / pb.Maximum) * 100).ToString("F2") + "%";
            }

            // Add controls to stackpanel
            sp.Children.Add(txt1);
            sp.Children.Add(txt2);
            sp.Children.Add(txt3);
            sp.Children.Add(txt4);
            sp.Children.Add(txt5);
            sp.Children.Add(txt6);
            sp.Children.Add(pbLabel);
            sp.Children.Add(pb);
            sp.Children.Add(pbPercent);
        }

        async private void AggregateBattery_ReportUpdated(Battery sender, object args)
        {
            if (reportRequested)
            {

                await Dispatcher.RunAsync(CoreDispatcherPriority.Normal, () =>
                {
                    // Clear UI
                    BatteryReportPanel.Children.Clear();


                    if (AggregateButton.IsChecked == true)
                    {
                        // Request aggregate battery report
                        RequestAggregateBatteryReport();
                    }
                    else
                    {
                        // Request individual battery report
                        RequestIndividualBatteryReports();
                    }
                });
            }
        }
    }
}
```

<span data-ttu-id="6a2c9-147">Wenn Ihre App nicht den Namen **App1** hat, müssen Sie den Namespace im vorherigen Beispiel durch den Namen ersetzen, den Sie für Ihr Projekt vergeben haben.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-147">If your app isn't named **App1**, you'll need to rename the namespace in the previous example with the name you gave your project.</span></span> <span data-ttu-id="6a2c9-148">Wenn Sie z.B. ein Projekt mit dem Namen **BasicBatteryApp** erstellt haben, ersetzen Sie den Namespace `App1` durch den Namespace `BasicBatteryApp`.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-148">For example, if you created a project named **BasicBatteryApp**, you'd replace namespace `App1` with namespace `BasicBatteryApp`.</span></span>

<span data-ttu-id="6a2c9-149">Führen Sie schließlich Folgendes aus, um diese einfache Akku-App auszuführen: Klicken Sie im Menü **Debuggen** auf **Debuggen starten**, um die Projektmappe zu testen.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-149">Finally, to run this basic battery app: on the **Debug** menu, click **Start Debugging** to test the solution.</span></span>

<span data-ttu-id="6a2c9-150">**Tipp:** um numerische Werte aus dem [**BatteryReport**](https://msdn.microsoft.com/library/windows/apps/Dn895005) -Objekt zu erhalten, Debuggen Sie Ihre app auf dem **Lokalen Computer** oder ein externes **Gerät** (z. B. eine Windows Phone).</span><span class="sxs-lookup"><span data-stu-id="6a2c9-150">**Tip**To receive numeric values from the [**BatteryReport**](https://msdn.microsoft.com/library/windows/apps/Dn895005) object, debug your app on the **Local Machine** or an external **Device** (such as a Windows Phone).</span></span> <span data-ttu-id="6a2c9-151">Beim Debuggen mit einem Geräteemulator gibt das **BatteryReport**-Objekt für die Kapazitäts- und Rateneigenschaften **null** zurück.</span><span class="sxs-lookup"><span data-stu-id="6a2c9-151">When debugging on a device emulator, the **BatteryReport** object returns **null** to the capacity and rate properties.</span></span>

 

