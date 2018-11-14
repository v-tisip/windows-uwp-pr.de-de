---
author: andrewleader
Description: Learn how to use headers to visually group your toast notifications in Action Center.
title: Popup-Header
label: Toast headers
template: detail.hbs
ms.author: mijacobs
ms.date: 12/7/2017
ms.topic: article
keywords: Windows10, UWP, Popup, Header, Popup-Header, Benachrichtigungen, Gruppen-Popups, Info-Center
ms.localizationpriority: medium
ms.openlocfilehash: fcc515b811a11be045ce80ed816708d230720a29
ms.sourcegitcommit: 4d88adfaf544a3dab05f4660e2f59bbe60311c00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2018
ms.locfileid: "6446190"
---
# <a name="toast-headers"></a><span data-ttu-id="38185-103">Popup-Header</span><span class="sxs-lookup"><span data-stu-id="38185-103">Toast headers</span></span>

<span data-ttu-id="38185-104">Sie können eine Reihe verwandter Benachrichtigungen visuell im Info-Center mit einem Popup-Header für Ihre Benachrichtigungen gruppieren.</span><span class="sxs-lookup"><span data-stu-id="38185-104">You can visually group a set of related notifications inside Action Center by using a toast header on your notifications.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38185-105">**Erfordert Desktop Creators Update und 1.4.0 der Benachrichtigungsbibliothek**: Sie müssen Desktop Build 15063 oder höher ausführen, um Popup-Header zu sehen.</span><span class="sxs-lookup"><span data-stu-id="38185-105">**Requires Desktop Creators Update and 1.4.0 of Notifications library**: You must be running Desktop build 15063 or higher to see toast headers.</span></span> <span data-ttu-id="38185-106">Sie müssen Version 1.4.0 oder höher der [UWP Community Toolkit Benachrichtigungen NuGet-Bibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) verwenden, um den Header der Popup-Inhalte zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="38185-106">You must use version 1.4.0 or higher of the [UWP Community Toolkit Notifications NuGet library](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) to construct the header in your toast's content.</span></span> <span data-ttu-id="38185-107">Header werden nur auf Desktop unterstützt.</span><span class="sxs-lookup"><span data-stu-id="38185-107">Headers are only supported on Desktop.</span></span>

<span data-ttu-id="38185-108">Wie unten dargestellt wird, ist diese Gruppenunterhaltung unter einer einzelnen Kopfzeile vereint: "Camping!!".</span><span class="sxs-lookup"><span data-stu-id="38185-108">As seen below, this group conversation is unified under a single header, "Camping!!".</span></span> <span data-ttu-id="38185-109">Jede einzelne Nachricht in der Unterhaltung ist eine separate Popupbenachrichtigung, die die gemeinsame Nutzung des gleichen Popup-Headers teilt.</span><span class="sxs-lookup"><span data-stu-id="38185-109">Each individual message in the conversation is a separate toast notification sharing the same toast header.</span></span>

<img alt="Toasts with header" src="images/toast-headers-action-center.png" width="396"/>

<span data-ttu-id="38185-110">Sie können auch auswählen, Ihre Benachrichtigungen visuell nach Kategorie zu gruppieren, z.B. Test-Flight-Erinnerungen, Paketverfolgung und mehr.</span><span class="sxs-lookup"><span data-stu-id="38185-110">You can also choose to visually group your notifications by category too, like flight reminders, package tracking, and more.</span></span>

## <a name="add-a-header-to-a-toast"></a><span data-ttu-id="38185-111">Hinzufügen eines Headers zu einem Popup</span><span class="sxs-lookup"><span data-stu-id="38185-111">Add a header to a toast</span></span>

<span data-ttu-id="38185-112">Hier erfahren Sie, wie Sie einer Popupbenachrichtigung einen Header hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="38185-112">Here's how you add a header to a toast notification.</span></span>

> [!NOTE]
> <span data-ttu-id="38185-113">Header werden nur auf Desktop unterstützt.</span><span class="sxs-lookup"><span data-stu-id="38185-113">Headers are only supported on Desktop.</span></span> <span data-ttu-id="38185-114">Geräte, die Header nicht unterstützen, ignoriert den Header einfach.</span><span class="sxs-lookup"><span data-stu-id="38185-114">Devices that don't support headers will simply ignore the header.</span></span>

```csharp
ToastContent toastContent = new ToastContent()
{
    Header = new ToastHeader()
    {
        Id = "6289",
        Title = "Camping!!",
        Arguments = "action=openConversation&id=6289",
    },

    Visual = new ToastVisual() { ... }
};
```

```xml
<toast>

    <header
        id="6289"
        title="Camping!!"
        arguments="action=openConversation&amp;id=6289"/>

    <visual>
        ...
    </visual>

</toast>
```

<span data-ttu-id="38185-115">Zusammenfassung...</span><span class="sxs-lookup"><span data-stu-id="38185-115">In summary...</span></span>

1. <span data-ttu-id="38185-116">Fügen Sie den **Header** zu Ihrem **ToastContent** hinzu</span><span class="sxs-lookup"><span data-stu-id="38185-116">Add the **Header** to your **ToastContent**</span></span>
2. <span data-ttu-id="38185-117">Weisen Sie die erforderlichen Eigenschaften zu, wie **ID**, **Titel** und **Argumente**</span><span class="sxs-lookup"><span data-stu-id="38185-117">Assign the required **Id**, **Title**, and **Arguments** properties</span></span>
3. <span data-ttu-id="38185-118">Senden der Benachrichtigung ([Hier erfahren Sie mehr](send-local-toast.md))</span><span class="sxs-lookup"><span data-stu-id="38185-118">Send your notification ([learn more](send-local-toast.md))</span></span>
4. <span data-ttu-id="38185-119">Verwenden Sie auf einer anderen Benachrichtigung die gleiche Überschrift-**ID**, um diese unter dem Header zu vereinheitlichen.</span><span class="sxs-lookup"><span data-stu-id="38185-119">On another notification, use the same header **Id** to unify them under the header.</span></span> <span data-ttu-id="38185-120">Die **ID** ist die einzige Eigenschaft, die bestimmt, ob die Benachrichtigungen gruppiert werden sollen, d.h. dass **Titel** und **Argumente** unterschiedlich sein können.</span><span class="sxs-lookup"><span data-stu-id="38185-120">The **Id** is the only property used to determine whether the notifications should be grouped, meaning the **Title** and **Arguments** can be different.</span></span> <span data-ttu-id="38185-121">Es werden die **Titel** und **Argumente** aus der letzten Benachrichtigung innerhalb einer Gruppe verwendet.</span><span class="sxs-lookup"><span data-stu-id="38185-121">The **Title** and **Arguments** from the most recent notification within a group are used.</span></span> <span data-ttu-id="38185-122">Wenn die Benachrichtigung entfernt wird, greifen **Titel** und **Argumente** auf die nächste aktuelle Benachrichtigung zurück.</span><span class="sxs-lookup"><span data-stu-id="38185-122">If that notification gets removed, then the **Title** and **Arguments** falls back to the next most recent notification.</span></span>


## <a name="handle-activation-from-a-header"></a><span data-ttu-id="38185-123">Behandeln der Aktivierung über einen Header</span><span class="sxs-lookup"><span data-stu-id="38185-123">Handle activation from a header</span></span>

<span data-ttu-id="38185-124">Header können von Benutzern angeklickt werden, damit der Benutzer den Header anklicken kann, um mehr über Ihre App zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="38185-124">Headers are clickable by users, so that the user can click the header to find out more from your app.</span></span>

<span data-ttu-id="38185-125">Daher können Apps **Argumente** im Header enthalten, ähnlich wie die Startargumente des Popup.</span><span class="sxs-lookup"><span data-stu-id="38185-125">Therefore, apps can provide **Arguments** on the header, similar to the launch arguments on the toast itself.</span></span>

<span data-ttu-id="38185-126">Die Aktivierung wird identisch behandelt wie eine [normale Popup-Aktivierung](send-local-toast.md#handling-activation-1), d.h., Sie können diese Argumente in der **OnActivated**-Methode der `App.xaml.cs` genauso abrufen, als ob der Benutzer auf den Text des Popups oder die Schaltfläche des Popup klickt.</span><span class="sxs-lookup"><span data-stu-id="38185-126">Activation is handled identical to [normal toast activation](send-local-toast.md#handling-activation-1), meaning you can retrieve these arguments in the **OnActivated** method of `App.xaml.cs` just like you do when the user clicks the body of your toast or a button on your toast.</span></span>

```csharp
protected override void OnActivated(IActivatedEventArgs e)
{
    // Handle toast activation
    if (e is ToastNotificationActivatedEventArgs)
    {
        // Arguments specified from the header
        string arguments = (e as ToastNotificationActivatedEventArgs).Argument;
    }
}
```


## <a name="additional-info"></a><span data-ttu-id="38185-127">Zusätzliche Infos</span><span class="sxs-lookup"><span data-stu-id="38185-127">Additional info</span></span>

<span data-ttu-id="38185-128">Der Header trennt und gruppiert visuell Gruppenbenachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="38185-128">The header visually separates and groups notifications.</span></span> <span data-ttu-id="38185-129">Dadurch ändert sich die andere Logistik über die maximalen Anzahl der Benachrichtigungen und das Verhalten der Reihenfolge der Benachrichtigungsliste nicht, über die eine App verfügen kann (20).</span><span class="sxs-lookup"><span data-stu-id="38185-129">It doesn't change any other logistics about the maximum number of notifications an app can have (20) and the first-in-first-out behavior of the notifications list.</span></span>

<span data-ttu-id="38185-130">Die Reihenfolge der Benachrichtigungen im Header sind wie folgt: Für eine bestimmte App wird die aktuelle Benachrichtigung aus der App angezeigt (und die gesamte Header-Gruppe, wenn sie Teil eines Headers ist).</span><span class="sxs-lookup"><span data-stu-id="38185-130">The order of notifications within headers are as follows... For a given app, the most recent notification from the app (and the entire header group if part of a header) will appear first.</span></span>

<span data-ttu-id="38185-131">Die **ID** kann eine beliebige Zeichenfolge sein, die Sie auswählen.</span><span class="sxs-lookup"><span data-stu-id="38185-131">The **Id** can be any string you choose.</span></span> <span data-ttu-id="38185-132">Es gelten keine Beschränkung für die Länge- oder die Zeichensätze auf den Eigenschaften des **ToastHeaders**.</span><span class="sxs-lookup"><span data-stu-id="38185-132">There are no length or character restrictions on any of the properties in **ToastHeader**.</span></span> <span data-ttu-id="38185-133">Die einzige Einschränkung besteht darin, dass der gesamte XML-Popupinhalt nicht größer als 5KB sein kann.</span><span class="sxs-lookup"><span data-stu-id="38185-133">The only constraint is that your entire XML toast content cannot be larger than 5 KB.</span></span>

<span data-ttu-id="38185-134">Das Erstellen der Überschriften ändert die Anzahl der angezeigten Benachrichtigungen im Info-Center nicht, bevor die Schaltfläche "Weitere" angezeigt wird (diese Nummer ist standardmäßig 3 und kann vom Benutzer für jede App in den Systemeinstellungen für Benachrichtigungen konfiguriert werden).</span><span class="sxs-lookup"><span data-stu-id="38185-134">Creating headers doesn't change the number of notifications shown inside Action Center before the "See more" button appears (this number is 3 by default and can be configured by the user for each app in system Settings for notifications).</span></span>

<span data-ttu-id="38185-135">Das Klicken auf die Überschrift, genau wie das Klicken auf den App-Titel, löscht keine Benachrichtigungen, die zu diesem Header gehören (Ihre App sollte die Popup-APIs verwenden,und die entsprechenden Benachrichtigungen zu löschen).</span><span class="sxs-lookup"><span data-stu-id="38185-135">Clicking on the header, just like clicking on the app title, does not clear any notifications belonging to this header (your app should use the toast APIs to clear the relevant notifications).</span></span>


## <a name="related-topics"></a><span data-ttu-id="38185-136">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="38185-136">Related topics</span></span>

- [<span data-ttu-id="38185-137">Senden einer lokalen Popupbenachrichtigung und Behandeln der Aktivierung</span><span class="sxs-lookup"><span data-stu-id="38185-137">Send a local toast and handle activation</span></span>](send-local-toast.md)
- [<span data-ttu-id="38185-138">Dokumentation zu Popupinhalt</span><span class="sxs-lookup"><span data-stu-id="38185-138">Toast content documentation</span></span>](adaptive-interactive-toasts.md)