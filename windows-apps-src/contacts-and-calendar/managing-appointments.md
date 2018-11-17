---
author: normesta
description: Mit dem Windows.ApplicationModel.Appointments-Namespace können Sie in der Kalender-App eines Benutzers Termine erstellen und verwalten.
title: Verwalten von Terminen
ms.assetid: 292E9249-07C3-4791-B32C-6EC153C2B538
ms.author: normesta
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Termine, Kalender
ms.localizationpriority: medium
ms.openlocfilehash: 345bbabb2bd80f0cbb8465941bec07c7172156e8
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2018
ms.locfileid: "7169473"
---
# <a name="manage-appointments"></a><span data-ttu-id="028f1-104">Verwalten von Terminen</span><span class="sxs-lookup"><span data-stu-id="028f1-104">Manage appointments</span></span>



<span data-ttu-id="028f1-105">Mit dem [**Windows.ApplicationModel.Appointments**](https://msdn.microsoft.com/library/windows/apps/Dn263359)-Namespace können Sie in der Kalender-App eines Benutzers Termine erstellen und verwalten.</span><span class="sxs-lookup"><span data-stu-id="028f1-105">Through the [**Windows.ApplicationModel.Appointments**](https://msdn.microsoft.com/library/windows/apps/Dn263359) namespace, you can create and manage appointments in a user's calendar app.</span></span> <span data-ttu-id="028f1-106">Hier erfahren Sie, wie Sie einen Termin erstellen, einer Kalender-App hinzufügen, in der Kalender-App ersetzen und aus der Kalender-App entfernen.</span><span class="sxs-lookup"><span data-stu-id="028f1-106">Here, we'll show you how to create an appointment, add it to a calendar app, replace it in the calendar app, and remove it from the calendar app.</span></span> <span data-ttu-id="028f1-107">Außerdem wird erläutert, wie Sie eine Zeitspanne für eine Kalender-App anzeigen und ein Terminwiederholungsobjekt erstellen.</span><span class="sxs-lookup"><span data-stu-id="028f1-107">We'll also show how to display a time span for a calendar app and create an appointment-recurrence object.</span></span>

## <a name="create-an-appointment-and-apply-data-to-it"></a><span data-ttu-id="028f1-108">Erstellen eines Termins und Anwenden von Daten</span><span class="sxs-lookup"><span data-stu-id="028f1-108">Create an appointment and apply data to it</span></span>

<span data-ttu-id="028f1-109">Erstellen Sie ein [**Windows.ApplicationModel.Appointments.Appointment**](https://msdn.microsoft.com/library/windows/apps/Dn297221)-Objekt, und weisen Sie es einer Variablen zu.</span><span class="sxs-lookup"><span data-stu-id="028f1-109">Create a [**Windows.ApplicationModel.Appointments.Appointment**](https://msdn.microsoft.com/library/windows/apps/Dn297221) object and assign it to a variable.</span></span> <span data-ttu-id="028f1-110">Weisen Sie dem **Appointment**-Element dann die Termineigenschaften zu, die von einem Benutzer über die UI bereitgestellt wurden.</span><span class="sxs-lookup"><span data-stu-id="028f1-110">Then, apply to the **Appointment** the appointment properties that were supplied through the UI by a user.</span></span>

```cs
private void Create-Click(object sender, RoutedEventArgs e)
{
    bool isAppointmentValid = true;
    var appointment = new Windows.ApplicationModel.Appointments.Appointment();

    // StartTime
    var date = StartTimeDatePicker.Date;
    var time = StartTimeTimePicker.Time;
    var timeZoneOffset = TimeZoneInfo.Local.GetUtcOffset(DateTime.Now);
    var startTime = new DateTimeOffset(date.Year, date.Month, date.Day, time.Hours, time.Minutes, 0, timeZoneOffset);
    appointment.StartTime = startTime;

    // Subject
    appointment.Subject = SubjectTextBox.Text;

    if (appointment.Subject.Length > 255)
    {
        isAppointmentValid = false;
        ResultTextBlock.Text = "The subject cannot be greater than 255 characters.";
    }

    // Location
    appointment.Location = LocationTextBox.Text;

    if (appointment.Location.Length > 32768)
    {
        isAppointmentValid = false;
        ResultTextBlock.Text = "The location cannot be greater than 32,768 characters.";
    }

    // Details
    appointment.Details = DetailsTextBox.Text;

    if (appointment.Details.Length > 1073741823)
    {
        isAppointmentValid = false;
        ResultTextBlock.Text = "The details cannot be greater than 1,073,741,823 characters.";
    }

    // Duration
    if (DurationComboBox.SelectedIndex == 0)
    {
        // 30 minute duration is selected
        appointment.Duration = TimeSpan.FromMinutes(30);
    }
    else
    {
        // 1 hour duration is selected
        appointment.Duration = TimeSpan.FromHours(1);
    }

    // All Day
    appointment.AllDay = AllDayCheckBox.IsChecked.Value;

    // Reminder
    if (ReminderCheckBox.IsChecked.Value)
    {
        switch (ReminderComboBox.SelectedIndex)
        {
            case 0:
                appointment.Reminder = TimeSpan.FromMinutes(15);
                break;
            case 1:
                appointment.Reminder = TimeSpan.FromHours(1);
                break;
            case 2:
                appointment.Reminder = TimeSpan.FromDays(1);
                break;
        }
    }

    //Busy Status
    switch (BusyStatusComboBox.SelectedIndex)
    {
        case 0:
            appointment.BusyStatus = Windows.ApplicationModel.Appointments.AppointmentBusyStatus.Busy;
            break;
        case 1:
            appointment.BusyStatus = Windows.ApplicationModel.Appointments.AppointmentBusyStatus.Tentative;
            break;
        case 2:
            appointment.BusyStatus = Windows.ApplicationModel.Appointments.AppointmentBusyStatus.Free;
            break;
        case 3:
            appointment.BusyStatus = Windows.ApplicationModel.Appointments.AppointmentBusyStatus.OutOfOffice;
            break;
        case 4:
            appointment.BusyStatus = Windows.ApplicationModel.Appointments.AppointmentBusyStatus.WorkingElsewhere;
            break;
    }

    // Sensitivity
    switch (SensitivityComboBox.SelectedIndex)
    {
        case 0:
            appointment.Sensitivity = Windows.ApplicationModel.Appointments.AppointmentSensitivity.Public;
            break;
        case 1:
            appointment.Sensitivity = Windows.ApplicationModel.Appointments.AppointmentSensitivity.Private;
            break;
    }

    // Uri
    if (UriTextBox.Text.Length > 0)
    {
        try
        {
            appointment.Uri = new System.Uri(UriTextBox.Text);
        }
        catch (Exception)
        {
            isAppointmentValid = false;
            ResultTextBlock.Text = "The Uri provided is invalid.";
        }
    }

    // Organizer
    // Note: Organizer can only be set if there are no invitees added to this appointment.
    if (OrganizerRadioButton.IsChecked.Value)
    {
        var organizer = new Windows.ApplicationModel.Appointments.AppointmentOrganizer();

        // Organizer Display Name
        organizer.DisplayName = OrganizerDisplayNameTextBox.Text;

        if (organizer.DisplayName.Length > 256)
        {
            isAppointmentValid = false;
            ResultTextBlock.Text = "The organizer display name cannot be greater than 256 characters.";
        }
        else
        {
            // Organizer Address (e.g. Email Address)
            organizer.Address = OrganizerAddressTextBox.Text;

            if (organizer.Address.Length > 321)
            {
                isAppointmentValid = false;
                ResultTextBlock.Text = "The organizer address cannot be greater than 321 characters.";
            }
            else if (organizer.Address.Length == 0)
            {
                isAppointmentValid = false;
                ResultTextBlock.Text = "The organizer address must be greater than 0 characters.";
            }
            else
            {
                appointment.Organizer = organizer;
            }
        }
    }

    // Invitees
    // Note: If the size of the Invitees list is not zero, then an Organizer cannot be set.
    if (InviteeRadioButton.IsChecked.Value)
    {
        var invitee = new Windows.ApplicationModel.Appointments.AppointmentInvitee();

        // Invitee Display Name
        invitee.DisplayName = InviteeDisplayNameTextBox.Text;

        if (invitee.DisplayName.Length > 256)
        {
            isAppointmentValid = false;
            ResultTextBlock.Text = "The invitee display name cannot be greater than 256 characters.";
        }
        else
        {
            // Invitee Address (e.g. Email Address)
            invitee.Address = InviteeAddressTextBox.Text;

            if (invitee.Address.Length > 321)
            {
                isAppointmentValid = false;
                ResultTextBlock.Text = "The invitee address cannot be greater than 321 characters.";
            }
            else if (invitee.Address.Length == 0)
            {
                isAppointmentValid = false;
                ResultTextBlock.Text = "The invitee address must be greater than 0 characters.";
            }
            else
            {
                // Invitee Role
                switch (RoleComboBox.SelectedIndex)
                {
                    case 0:
                        invitee.Role = Windows.ApplicationModel.Appointments.AppointmentParticipantRole.RequiredAttendee;
                        break;
                    case 1:
                        invitee.Role = Windows.ApplicationModel.Appointments.AppointmentParticipantRole.OptionalAttendee;
                        break;
                    case 2:
                        invitee.Role = Windows.ApplicationModel.Appointments.AppointmentParticipantRole.Resource;
                        break;
                }

                // Invitee Response
                switch (ResponseComboBox.SelectedIndex)
                {
                    case 0:
                        invitee.Response = Windows.ApplicationModel.Appointments.AppointmentParticipantResponse.None;
                        break;
                    case 1:
                        invitee.Response = Windows.ApplicationModel.Appointments.AppointmentParticipantResponse.Tentative;
                        break;
                    case 2:
                        invitee.Response = Windows.ApplicationModel.Appointments.AppointmentParticipantResponse.Accepted;
                        break;
                    case 3:
                        invitee.Response = Windows.ApplicationModel.Appointments.AppointmentParticipantResponse.Declined;
                        break;
                    case 4:
                        invitee.Response = Windows.ApplicationModel.Appointments.AppointmentParticipantResponse.Unknown;
                        break;
                }

                appointment.Invitees.Add(invitee);
            }
        }
    }

    if (isAppointmentValid)
    {
        ResultTextBlock.Text = "The appointment was created successfully and is valid.";
    }
}
```

## <a name="add-an-appointment-to-the-users-calendar"></a><span data-ttu-id="028f1-111">Hinzufügen eines Termins zum Kalender des Benutzers</span><span class="sxs-lookup"><span data-stu-id="028f1-111">Add an appointment to the user's calendar</span></span>

<span data-ttu-id="028f1-112">Erstellen Sie ein [**Windows.ApplicationModel.Appointments.Appointment**](https://msdn.microsoft.com/library/windows/apps/Dn297221)-Objekt, und weisen Sie es einer Variablen zu.</span><span class="sxs-lookup"><span data-stu-id="028f1-112">Create a [**Windows.ApplicationModel.Appointments.Appointment**](https://msdn.microsoft.com/library/windows/apps/Dn297221) object and assign it to a variable.</span></span> <span data-ttu-id="028f1-113">Rufen Sie anschließend die [**AppointmentManager.ShowAddAppointmentAsync(Appointment, Rect, Placement)**](https://msdn.microsoft.com/library/windows/apps/dn297261)-Methode auf, um die standardmäßige Terminanbieter-UI zum Hinzufügen von Terminen anzuzeigen, damit der Benutzer einen Termin hinzufügen kann.</span><span class="sxs-lookup"><span data-stu-id="028f1-113">Then, call the [**AppointmentManager.ShowAddAppointmentAsync(Appointment, Rect, Placement)**](https://msdn.microsoft.com/library/windows/apps/dn297261) method to show the default appointments provider add-appointment UI, to enable the user to add an appointment.</span></span> <span data-ttu-id="028f1-114">Wenn der Benutzer auf **Hinzufügen** geklickt hat, wird im Beispiel der Terminbezeichner ausgegeben, der von **ShowAddAppointmentAsync** zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="028f1-114">If the user clicked **Add**, the sample prints the appointment identifier that **ShowAddAppointmentAsync** returned.</span></span>

```cs
private async void Add-Click(object sender, RoutedEventArgs e)
{
    // Create an Appointment that should be added the user's appointments provider app.
    var appointment = new Windows.ApplicationModel.Appointments.Appointment();

    // Get the selection rect of the button pressed to add this appointment
    var rect = GetElementRect(sender as FrameworkElement);

    // ShowAddAppointmentAsync returns an appointment id if the appointment given was added to the user's calendar.
    // This value should be stored in app data and roamed so that the appointment can be replaced or removed in the future.
    // An empty string return value indicates that the user canceled the operation before the appointment was added.
    String appointmentId = await Windows.ApplicationModel.Appointments.AppointmentManager.ShowAddAppointmentAsync(
                           appointment, rect, Windows.UI.Popups.Placement.Default);
    if (appointmentId != String.Empty)
    {
        ResultTextBlock.Text = "Appointment Id: " + appointmentId;
    }
    else
    {
        ResultTextBlock.Text = "Appointment not added.";
    }
}
```

<span data-ttu-id="028f1-115">**Hinweis:** für Windows Phone Store-apps, [**ShowAddAppointment**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appointments.appointmentmanager.showaddappointmentasync) Funktionen wie [**ShowEditNewAppointment**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appointments.appointmentmanager.showeditnewappointmentasync) , das zum Hinzufügen des Termins angezeigte Dialogfeld bearbeitet werden kann.</span><span class="sxs-lookup"><span data-stu-id="028f1-115">**Note**For Windows Phone Store apps, [**ShowAddAppointment**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appointments.appointmentmanager.showaddappointmentasync) functions just like [**ShowEditNewAppointment**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appointments.appointmentmanager.showeditnewappointmentasync) in that the dialog displayed for adding the appointment is editable.</span></span>

## <a name="replace-an-appointment-in-the-users-calendar"></a><span data-ttu-id="028f1-116">Ersetzen eines Termins im Kalender des Benutzers</span><span class="sxs-lookup"><span data-stu-id="028f1-116">Replace an appointment in the user's calendar</span></span>

<span data-ttu-id="028f1-117">Erstellen Sie ein [**Windows.ApplicationModel.Appointments.Appointment**](https://msdn.microsoft.com/library/windows/apps/Dn297221)-Objekt, und weisen Sie es einer Variablen zu.</span><span class="sxs-lookup"><span data-stu-id="028f1-117">Create a [**Windows.ApplicationModel.Appointments.Appointment**](https://msdn.microsoft.com/library/windows/apps/Dn297221) object and assign it to a variable.</span></span> <span data-ttu-id="028f1-118">Rufen Sie anschließend die passende [**AppointmentManager.ShowReplaceAppointmentAsync**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appointments.appointmentmanager.showreplaceappointmentasync)-Methode auf, um die standardmäßige Terminanbieter-UI zum Ersetzen von Terminen anzuzeigen, damit der Benutzer einen Termin ersetzen kann.</span><span class="sxs-lookup"><span data-stu-id="028f1-118">Then, call the appropriate [**AppointmentManager.ShowReplaceAppointmentAsync**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appointments.appointmentmanager.showreplaceappointmentasync) method to show the default appointments provider replace-appointment UI to enable the user to replace an appointment.</span></span> <span data-ttu-id="028f1-119">Der Benutzer stellt auch den Terminbezeichner bereit, der ersetzt werden soll.</span><span class="sxs-lookup"><span data-stu-id="028f1-119">The user also provides the appointment identifier that they want to replace.</span></span> <span data-ttu-id="028f1-120">Dieser Bezeichner wurde von [**AppointmentManager.ShowAddAppointmentAsync**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appointments.appointmentmanager.showaddappointmentasync) zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="028f1-120">This identifier was returned from [**AppointmentManager.ShowAddAppointmentAsync**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appointments.appointmentmanager.showaddappointmentasync).</span></span> <span data-ttu-id="028f1-121">Wenn der Benutzer auf **Ersetzen**geklickt hat, wird im Beispiel ausgegeben, dass der Terminbezeichner aktualisiert wurde.</span><span class="sxs-lookup"><span data-stu-id="028f1-121">If the user clicked **Replace**, the sample prints that it updated that appointment identifier.</span></span>

```cs
private async void Replace-Click(object sender, RoutedEventArgs e)
{
    // The appointment id argument for ReplaceAppointmentAsync is typically retrieved from AddAppointmentAsync and stored in app data.
    String appointmentIdOfAppointmentToReplace = AppointmentIdTextBox.Text;

    if (String.IsNullOrEmpty(appointmentIdOfAppointmentToReplace))
    {
        ResultTextBlock.Text = "The appointment id cannot be empty";
    }
    else
    {
        // The Appointment argument for ReplaceAppointmentAsync should contain all of the Appointment' s properties including those that may have changed.
        var appointment = new Windows.ApplicationModel.Appointments.Appointment();

        // Get the selection rect of the button pressed to replace this appointment
        var rect = GetElementRect(sender as FrameworkElement);

        // ReplaceAppointmentAsync returns an updated appointment id when the appointment was successfully replaced.
        // The updated id may or may not be the same as the original one retrieved from AddAppointmentAsync.
        // An optional instance start time can be provided to indicate that a specific instance on that date should be replaced
        // in the case of a recurring appointment.
        // If the appointment id returned is an empty string, that indicates that the appointment was not replaced.
        String updatedAppointmentId;
        if (InstanceStartDateCheckBox.IsChecked.Value)
        {
            // Replace a specific instance starting on the date provided.
            var instanceStartDate = InstanceStartDateDatePicker.Date;
            updatedAppointmentId = await Windows.ApplicationModel.Appointments.AppointmentManager.ShowReplaceAppointmentAsync(
                                   appointmentIdOfAppointmentToReplace, appointment, rect, Windows.UI.Popups.Placement.Default, instanceStartDate);
        }
        else
        {
            // Replace an appointment that occurs only once or in the case of a recurring appointment, replace the entire series.
            updatedAppointmentId = await Windows.ApplicationModel.Appointments.AppointmentManager.ShowReplaceAppointmentAsync(
                                   appointmentIdOfAppointmentToReplace, appointment, rect, Windows.UI.Popups.Placement.Default);
        }

        if (updatedAppointmentId != String.Empty)
        {
            ResultTextBlock.Text = "Updated Appointment Id: " + updatedAppointmentId;
        }
        else
        {
            ResultTextBlock.Text = "Appointment not replaced.";
        }
    }
}
```

## <a name="remove-an-appointment-from-the-users-calendar"></a><span data-ttu-id="028f1-122">Entfernen eines Termins aus dem Kalender des Benutzers</span><span class="sxs-lookup"><span data-stu-id="028f1-122">Remove an appointment from the user's calendar</span></span>

<span data-ttu-id="028f1-123">Rufen Sie die passende [**AppointmentManager.ShowRemoveAppointmentAsync**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appointments.appointmentmanager.showremoveappointmentasync)-Methode auf, um die standardmäßige Terminanbieter-UI zum Entfernen von Terminen anzuzeigen, damit der Benutzer einen Termin entfernen kann.</span><span class="sxs-lookup"><span data-stu-id="028f1-123">Call the appropriate [**AppointmentManager.ShowRemoveAppointmentAsync**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appointments.appointmentmanager.showremoveappointmentasync) method to show the default appointments provider remove-appointment UI, to enable the user to remove an appointment.</span></span> <span data-ttu-id="028f1-124">Der Benutzer stellt auch den Terminbezeichner bereit, der entfernt werden soll.</span><span class="sxs-lookup"><span data-stu-id="028f1-124">The user also provides the appointment identifier that they want to remove.</span></span> <span data-ttu-id="028f1-125">Dieser Bezeichner wurde von [**AppointmentManager.ShowAddAppointmentAsync**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appointments.appointmentmanager.showaddappointmentasync) zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="028f1-125">This identifier was returned from [**AppointmentManager.ShowAddAppointmentAsync**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appointments.appointmentmanager.showaddappointmentasync).</span></span> <span data-ttu-id="028f1-126">Wenn der Benutzer auf **Löschen**geklickt hat, wird im Beispiel ausgegeben, dass der mit diesem Terminbezeichner angegebene Termin entfernt wurde.</span><span class="sxs-lookup"><span data-stu-id="028f1-126">If the user clicked **Delete**, the sample prints that it removed the appointment specified by that appointment identifier.</span></span>

```cs
private async void Remove-Click(object sender, RoutedEventArgs e)
{
    // The appointment id argument for ShowRemoveAppointmentAsync is typically retrieved from AddAppointmentAsync and stored in app data.
    String appointmentId = AppointmentIdTextBox.Text;

    // The appointment id cannot be null or empty.
    if (String.IsNullOrEmpty(appointmentId))
    {
        ResultTextBlock.Text = "The appointment id cannot be empty";
    }
    else
    {
        // Get the selection rect of the button pressed to remove this appointment
        var rect = GetElementRect(sender as FrameworkElement);

        // ShowRemoveAppointmentAsync returns a boolean indicating whether or not the appointment related to the appointment id given was removed.
        // An optional instance start time can be provided to indicate that a specific instance on that date should be removed
        // in the case of a recurring appointment.
        bool removed;
        if (InstanceStartDateCheckBox.IsChecked.Value)
        {
            // Remove a specific instance starting on the date provided.
            var instanceStartDate = InstanceStartDateDatePicker.Date;
            removed = await Windows.ApplicationModel.Appointments.AppointmentManager.ShowRemoveAppointmentAsync(
                      appointmentId, rect, Windows.UI.Popups.Placement.Default, instanceStartDate);
        }
        else
        {
            // Remove an appointment that occurs only once or in the case of a recurring appointment, replace the entire series.
            removed = await Windows.ApplicationModel.Appointments.AppointmentManager.ShowRemoveAppointmentAsync(
                      appointmentId, rect, Windows.UI.Popups.Placement.Default);
        }

        if (removed)
        {
            ResultTextBlock.Text = "Appointment removed";
        }
        else
        {
            ResultTextBlock.Text = "Appointment not removed";
        }
    }
}
```

## <a name="show-a-time-span-for-the-appointments-provider"></a><span data-ttu-id="028f1-127">Anzeigen einer Zeitspanne für den Terminanbieter</span><span class="sxs-lookup"><span data-stu-id="028f1-127">Show a time span for the appointments provider</span></span>

<span data-ttu-id="028f1-128">Rufen Sie die [**AppointmentManager.ShowTimeFrameAsync**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appointments.appointmentmanager.showtimeframeasync)-Methode auf, um eine bestimmte Zeitspanne für die primäre UI des standardmäßigen Terminanbieters anzuzeigen, wenn der Benutzer auf **Anzeigen** geklickt hat.</span><span class="sxs-lookup"><span data-stu-id="028f1-128">Call the [**AppointmentManager.ShowTimeFrameAsync**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appointments.appointmentmanager.showtimeframeasync) method to show a specific time span for the default appointments provider's primary UI if the user clicked **Show**.</span></span> <span data-ttu-id="028f1-129">Im Beispiel wird ausgegeben, dass der standardmäßige Terminanbieter auf dem Bildschirm angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="028f1-129">The sample prints that the default appointments provider appeared on screen.</span></span>

```cs
private async void Show-Click(object sender, RoutedEventArgs e)
{
    var dateToShow = new DateTimeOffset(2015, 6, 12, 18, 32, 0, 0, TimeSpan.FromHours(-8));
    var duration = TimeSpan.FromHours(1);
    await Windows.ApplicationModel.Appointments.AppointmentManager.ShowTimeFrameAsync(dateToShow, duration);
    ResultTextBlock.Text = "The default appointments provider should have appeared on screen.";
}
```

## <a name="create-an-appointment-recurrence-object-and-apply-data-to-it"></a><span data-ttu-id="028f1-130">Erstellen eines Terminwiederholungsobjekts und Anwenden von Daten</span><span class="sxs-lookup"><span data-stu-id="028f1-130">Create an appointment-recurrence object and apply data to it</span></span>

<span data-ttu-id="028f1-131">Erstellen Sie ein [**Windows.ApplicationModel.Appointments.AppointmentRecurrence**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appointments.appointmentrecurrence)-Objekt, und weisen Sie es einer Variablen zu.</span><span class="sxs-lookup"><span data-stu-id="028f1-131">Create an [**Windows.ApplicationModel.Appointments.AppointmentRecurrence**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appointments.appointmentrecurrence) object and assign it to a variable.</span></span> <span data-ttu-id="028f1-132">Weisen Sie dem **AppointmentRecurrence**-Objekt dann die Wiederholungseigenschaften zu, die von einem Benutzer über die Benutzeroberfläche bereitgestellt wurden.</span><span class="sxs-lookup"><span data-stu-id="028f1-132">Then, apply to the **AppointmentRecurrence** the recurrence properties that were supplied through the UI by a user.</span></span>

```cs
private void Create-Click(object sender, RoutedEventArgs e)
{
    bool isRecurrenceValid = true;
    var recurrence = new Windows.ApplicationModel.Appointments.AppointmentRecurrence();

    // Unit
    switch (UnitComboBox.SelectedIndex)
    {
        case 0:
            recurrence.Unit = Windows.ApplicationModel.Appointments.AppointmentRecurrenceUnit.Daily;
            break;
        case 1:
            recurrence.Unit = Windows.ApplicationModel.Appointments.AppointmentRecurrenceUnit.Weekly;
            break;
        case 2:
            recurrence.Unit = Windows.ApplicationModel.Appointments.AppointmentRecurrenceUnit.Monthly;
            break;
        case 3:
            recurrence.Unit = Windows.ApplicationModel.Appointments.AppointmentRecurrenceUnit.MonthlyOnDay;
            break;
        case 4:
            recurrence.Unit = Windows.ApplicationModel.Appointments.AppointmentRecurrenceUnit.Yearly;
            break;
        case 5:
            recurrence.Unit = Windows.ApplicationModel.Appointments.AppointmentRecurrenceUnit.YearlyOnDay;
            break;
    }

    // Occurrences
    // Note: Occurrences and Until properties are mutually exclusive.
    if (OccurrencesRadioButton.IsChecked.Value)
    {
        recurrence.Occurrences = (uint)OccurrencesSlider.Value;
    }

    // Until
    // Note: Until and Occurrences properties are mutually exclusive.
    if (UntilRadioButton.IsChecked.Value)
    {
        recurrence.Until = UntilDatePicker.Date;
    }

    // Interval
    recurrence.Interval = (uint)IntervalSlider.Value;

    // Week of the month
    switch (WeekOfMonthComboBox.SelectedIndex)
    {
        case 0:
            recurrence.WeekOfMonth = Windows.ApplicationModel.Appointments.AppointmentWeekOfMonth.First;
            break;
        case 1:
            recurrence.WeekOfMonth = Windows.ApplicationModel.Appointments.AppointmentWeekOfMonth.Second;
            break;
        case 2:
            recurrence.WeekOfMonth = Windows.ApplicationModel.Appointments.AppointmentWeekOfMonth.Third;
            break;
        case 3:
            recurrence.WeekOfMonth = Windows.ApplicationModel.Appointments.AppointmentWeekOfMonth.Fourth;
            break;
        case 4:
            recurrence.WeekOfMonth = Windows.ApplicationModel.Appointments.AppointmentWeekOfMonth.Last;
            break;
    }

    // Days of the Week
    // Note: For Weekly, MonthlyOnDay or YearlyOnDay recurrence unit values, at least one day must be specified.
    if (SundayCheckBox.IsChecked.Value) { recurrence.DaysOfWeek |= Windows.ApplicationModel.Appointments.AppointmentDaysOfWeek.Sunday; }
    if (MondayCheckBox.IsChecked.Value) { recurrence.DaysOfWeek |= Windows.ApplicationModel.Appointments.AppointmentDaysOfWeek.Monday; }
    if (TuesdayCheckBox.IsChecked.Value) { recurrence.DaysOfWeek |= Windows.ApplicationModel.Appointments.AppointmentDaysOfWeek.Tuesday; }
    if (WednesdayCheckBox.IsChecked.Value) { recurrence.DaysOfWeek |= Windows.ApplicationModel.Appointments.AppointmentDaysOfWeek.Wednesday; }
    if (ThursdayCheckBox.IsChecked.Value) { recurrence.DaysOfWeek |= Windows.ApplicationModel.Appointments.AppointmentDaysOfWeek.Thursday; }
    if (FridayCheckBox.IsChecked.Value) { recurrence.DaysOfWeek |= Windows.ApplicationModel.Appointments.AppointmentDaysOfWeek.Friday; }
    if (SaturdayCheckBox.IsChecked.Value) { recurrence.DaysOfWeek |= Windows.ApplicationModel.Appointments.AppointmentDaysOfWeek.Saturday; }

    if (((recurrence.Unit == Windows.ApplicationModel.Appointments.AppointmentRecurrenceUnit.Weekly) ||
         (recurrence.Unit == Windows.ApplicationModel.Appointments.AppointmentRecurrenceUnit.MonthlyOnDay) ||
         (recurrence.Unit == Windows.ApplicationModel.Appointments.AppointmentRecurrenceUnit.YearlyOnDay)) &&
        (recurrence.DaysOfWeek == Windows.ApplicationModel.Appointments.AppointmentDaysOfWeek.None))
    {
        isRecurrenceValid = false;
        ResultTextBlock.Text = "The recurrence specified is invalid. For Weekly, MonthlyOnDay or YearlyOnDay recurrence unit values, " +
                               "at least one day must be specified.";
    }

    // Month of the year
    recurrence.Month = (uint)MonthSlider.Value;

    // Day of the month
    recurrence.Day = (uint)DaySlider.Value;

    if (isRecurrenceValid)
    {
        ResultTextBlock.Text = "The recurrence specified was created successfully and is valid.";
    }
}
```

## <a name="add-a-new-editable-appointment"></a><span data-ttu-id="028f1-133">Hinzufügen neuer bearbeitbarer Termine</span><span class="sxs-lookup"><span data-stu-id="028f1-133">Add a new editable appointment</span></span>

<span data-ttu-id="028f1-134">[**ShowEditNewAppointmentAsync**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appointments.appointmentmanager.showeditnewappointmentasync) funktioniert wie [**ShowAddAppointmentAsync**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appointments.appointmentmanager.showaddappointmentasync). Das Dialogfeld für das Hinzufügen des Termins ist hier jedoch bearbeitbar, sodass der Benutzer die Termindaten vor dem Speichern ändern kann.</span><span class="sxs-lookup"><span data-stu-id="028f1-134">[**ShowEditNewAppointmentAsync**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appointments.appointmentmanager.showeditnewappointmentasync) works just like [**ShowAddAppointmentAsync**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appointments.appointmentmanager.showaddappointmentasync) except that the dialog for adding the appointment is editable so that the user can modify the appointment data before saving it.</span></span>

``` cs
private async void AddAndEdit-Click(object sender, RoutedEventArgs e)
{
    // Create an Appointment that should be added the user' s appointments provider app.
    var appointment = new Windows.ApplicationModel.Appointments.Appointment();

    appointment.StartTime = DateTime.Now + TimeSpan.FromDays(1);
    appointment.Duration = TimeSpan.FromHours(1);
    appointment.Location = "Meeting location";
    appointment.Subject = "Meeting subject";
    appointment.Details = "Meeting description";
    appointment.Reminder = TimeSpan.FromMinutes(15); // Remind me 15 minutes prior


    // ShowAddAppointmentAsync returns an appointment id if the appointment given was added to the user' s calendar.
    // This value should be stored in app data and roamed so that the appointment can be replaced or removed in the future.
    // An empty string return value indicates that the user canceled the operation before the appointment was added.
    String appointmentId =
        await Windows.ApplicationModel.Appointments.AppointmentManager.ShowEditNewAppointmentAsync(appointment);

    if (appointmentId != String.Empty)
    {
        ResultTextBlock.Text = "Appointment Id: " + appointmentId;
    }
    else
    {
        ResultTextBlock.Text = "Appointment not added.";
    }
}
```

## <a name="show-appointment-details"></a><span data-ttu-id="028f1-135">Anzeigen von Termindetails</span><span class="sxs-lookup"><span data-stu-id="028f1-135">Show appointment details</span></span>

<span data-ttu-id="028f1-136">[**ShowAppointmentDetailsAsync**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appointments.appointmentmanager.showappointmentdetailsasync) dient zum Anzeigen von Details für den angegebenen Termin durch das System.</span><span class="sxs-lookup"><span data-stu-id="028f1-136">[**ShowAppointmentDetailsAsync**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.appointments.appointmentmanager.showappointmentdetailsasync) causes the system to show details for the specified appointment.</span></span> <span data-ttu-id="028f1-137">Für Apps mit App-Kalendern kann das Anzeigen von Termindetails in den Kalendern aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="028f1-137">An app that implements app calendars may choose to be activated to show details for appointments in calendars it owns.</span></span> <span data-ttu-id="028f1-138">Andernfalls werden vom System die Termindetails angezeigt.</span><span class="sxs-lookup"><span data-stu-id="028f1-138">Otherwise, the system will show the appointment details.</span></span> <span data-ttu-id="028f1-139">Eine Überladung der Methode, die ein Startdatumargument akzeptiert, wird zum Anzeigen von Details für eine Instanz einer Terminserie bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="028f1-139">An overload of the method that accepts a start date argument is provided to show details for an instance of a recurring appointment.</span></span>

```cs
private async void ShowAppointmentDetails-Click(object sender, RoutedEventArgs e)
{

    if (instanceStartTime == null)
    {
        await Windows.ApplicationModel.Appointments.AppointmentManager.ShowAppointmentDetailsAsync(
            currentAppointment.LocalId);
    }
    else
    {
        // Specify a start time to show an instance of a recurring appointment
        await Windows.ApplicationModel.Appointments.AppointmentManager.ShowAppointmentDetailsAsync(
            currentAppointment.LocalId, instanceStartTime);
    }

}
```

## <a name="summary-and-next-steps"></a><span data-ttu-id="028f1-140">Zusammenfassung und nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="028f1-140">Summary and next steps</span></span>

<span data-ttu-id="028f1-141">Sie verfügen nun über Grundkenntnisse zur Terminverwaltung.</span><span class="sxs-lookup"><span data-stu-id="028f1-141">Now you have a basic understanding of how to manage appointments.</span></span> <span data-ttu-id="028f1-142">Laden Sie die [Beispiele für universelle Windows-Apps](http://go.microsoft.com/fwlink/p/?linkid=619979) von GitHub herunter, um sich weitere Terminverwaltungsbeispiele anzusehen.</span><span class="sxs-lookup"><span data-stu-id="028f1-142">Download the [Universal Windows app samples](http://go.microsoft.com/fwlink/p/?linkid=619979) from GitHub to see more examples of how to manage appointments.</span></span>

## <a name="related-topics"></a><span data-ttu-id="028f1-143">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="028f1-143">Related topics</span></span>

* [<span data-ttu-id="028f1-144">Beispiel zur Termin-API</span><span class="sxs-lookup"><span data-stu-id="028f1-144">Appointments API sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=309836)
 

 
