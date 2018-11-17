---
author: muhsinking
Description: Use an inverted list to add new items at the bottom.
title: Invertierte Listen
label: Inverted lists
template: detail.hbs
ms.author: mukin
ms.date: 05/19/2017
ms.topic: article
keywords: Windows 10, UWP
ms.assetid: 52c1d63d-69c1-48d6-a234-6f39296e4bfd
pm-contact: predavid
design-contact: kimsea
doc-status: Published
ms.localizationpriority: medium
ms.openlocfilehash: d19d18d55c973644f5c3f99ae3d442e6dbf3a724
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2018
ms.locfileid: "7163585"
---
# <a name="inverted-lists"></a><span data-ttu-id="dc203-103">Invertierte Listen</span><span class="sxs-lookup"><span data-stu-id="dc203-103">Inverted lists</span></span>

 

<span data-ttu-id="dc203-104">Mit einer Listenansicht können Sie eine Unterhaltung in einer Chat-Darstellung optisch so aufbereitet darstellen, dass die beiden Gesprächspartner voneinander abgehoben sind.</span><span class="sxs-lookup"><span data-stu-id="dc203-104">You can use a list view to present a conversation in a chat experience with items that are visually distinct to represent the sender/receiver.</span></span>  <span data-ttu-id="dc203-105">Mit unterschiedlichen Farben und alternierender horizontaler Ausrichtung zur Kennzeichnung der Nachrichten des Absenders/Empfängers lassen sich Unterhaltungen leichter lesen und durchblättern.</span><span class="sxs-lookup"><span data-stu-id="dc203-105">Using different colors and horizontal alignment to separate messages from the sender/receiver helps the user quickly orient themselves in a conversation.</span></span>

> <span data-ttu-id="dc203-106">**Wichtige APIs**:  [ListView-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx), [ItemsStackPanel-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemsstackpanel.aspx), [ItemsUpdatingScrollMode-Eigenschaft](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemsstackpanel.itemsupdatingscrollmode.aspx)</span><span class="sxs-lookup"><span data-stu-id="dc203-106">**Important APIs**:  [ListView class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.listview.aspx), [ItemsStackPanel class](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemsstackpanel.aspx), [ItemsUpdatingScrollMode property](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemsstackpanel.itemsupdatingscrollmode.aspx)</span></span>
 
<span data-ttu-id="dc203-107">Sie müssen die Liste in der Regel so anzeigen, dass sie von unten nach oben anstelle von oben nach unten wächst.</span><span class="sxs-lookup"><span data-stu-id="dc203-107">You will typically need to present the list such that it appears to grow from the bottom up instead of from the top down.</span></span>  <span data-ttu-id="dc203-108">Wenn eine neue Nachricht eintrifft und am Ende hinzugefügt wird, werden die vorherigen Nachrichten nach oben verschoben, um die Aufmerksamkeit des Benutzers auf die aktuelle Nachricht zu richten.</span><span class="sxs-lookup"><span data-stu-id="dc203-108">When a new message arrives and is added to the end, the previous messages slide up to make room drawing the user’s attention to the latest arrival.</span></span>  <span data-ttu-id="dc203-109">Wenn der Benutzer jedoch einen Bildlauf zu den vorherigen Antworten durchführt, darf eine neue Nachricht nicht dazu führen, das automatisch diese Nachricht angezeigt wird, weil dies den Benutzer beim Lesen der vorherigen Nachrichten stören würde.</span><span class="sxs-lookup"><span data-stu-id="dc203-109">However, if a user has scrolled up to view previous replies then the arrival of a new message must not cause a visual shift that would disrupt their focus.</span></span>

![Chat-App mit invertierter Liste](images/listview-inverted.png)

## <a name="create-an-inverted-list"></a><span data-ttu-id="dc203-111">Erstellen einer invertierten Liste</span><span class="sxs-lookup"><span data-stu-id="dc203-111">Create an inverted list</span></span>

<span data-ttu-id="dc203-112">Verwenden Sie zum Erstellen einer invertierten Liste eine Listenansicht mit einem [ItemsStackPanel](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemsstackpanel.aspx) als Elementpanel.</span><span class="sxs-lookup"><span data-stu-id="dc203-112">To create an inverted list, use a list view with an [ItemsStackPanel](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemsstackpanel.aspx) as its items panel.</span></span> <span data-ttu-id="dc203-113">Stellen Sie am ItemsStackPanel den [ItemsUpdatingScrollMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemsstackpanel.itemsupdatingscrollmode.aspx) auf [KeepLastItemInView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemsupdatingscrollmode.aspx).</span><span class="sxs-lookup"><span data-stu-id="dc203-113">On the ItemsStackPanel, set the [ItemsUpdatingScrollMode](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemsstackpanel.itemsupdatingscrollmode.aspx) to [KeepLastItemInView](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.itemsupdatingscrollmode.aspx).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dc203-114">Der Enumerationswert **KeepLastItemInView** ist ab Windows 10, Version 1607, verfügbar.</span><span class="sxs-lookup"><span data-stu-id="dc203-114">The **KeepLastItemInView** enum value is available starting with Windows 10, version 1607.</span></span> <span data-ttu-id="dc203-115">Wenn Ihre App unter einer früheren Version von Windows 10 ausgeführt wird, können Sie diesen Wert nicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="dc203-115">You can't use this value when your app runs on earlier versions of Windows 10.</span></span>

<span data-ttu-id="dc203-116">Dieses Beispiel zeigt, wie Sie in der Listenansicht Elemente nach unten ausrichten und angeben, dass das zuletzt angezeigte Element bei einer Änderung der Elemente in der Ansicht verbleiben soll.</span><span class="sxs-lookup"><span data-stu-id="dc203-116">This example shows how to align the list view’s items to the bottom and indicate that when there is a change to the items the last item should remain in view.</span></span>
 
 **<span data-ttu-id="dc203-117">XAML</span><span class="sxs-lookup"><span data-stu-id="dc203-117">XAML</span></span>**
 ```xaml
<ListView>
    <ListView.ItemsPanel>
        <ItemsPanelTemplate>
            <ItemsStackPanel VerticalAlignment="Bottom"
                             ItemsUpdatingScrollMode="KeepLastItemInView"/>
        </ItemsPanelTemplate>
    </ListView.ItemsPanel>
</ListView>
```

## <a name="dos-and-donts"></a><span data-ttu-id="dc203-118">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="dc203-118">Do's and don'ts</span></span>

- <span data-ttu-id="dc203-119">Richten Sie Nachrichten von dem Absender/Empfänger auf gegenüberliegenden Seiten des Bildschirms aus, damit dem Benutzer die Abfolge der Nachrichten klar angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="dc203-119">Align messages from the sender/receiver on opposite sides to make the flow of conversation clear to users.</span></span>
- <span data-ttu-id="dc203-120">Verschieben Sie die vorhandenen Nachrichten mit einer Animation nach oben, um die neuesten Nachrichten anzuzeigen, wenn der Benutzer bereits am Ende der Unterhaltung ist und auf die nächste Nachricht wartet.</span><span class="sxs-lookup"><span data-stu-id="dc203-120">Animate the existing messages out of the way to display the latest message if the user is already at the end of the conversation awaiting the next message.</span></span>
- <span data-ttu-id="dc203-121">Unterbrechen Sie nicht die Lektüre des Benutzers, indem Sie Nachrichten verschieben, wenn er gerade nicht am Ende der Unterhaltung liest.</span><span class="sxs-lookup"><span data-stu-id="dc203-121">Don’t disrupt the users focus by moving items if they’re not reading the end of the conversation.</span></span>

## <a name="get-the-sample-code"></a><span data-ttu-id="dc203-122">Beispielcode herunterladen</span><span class="sxs-lookup"><span data-stu-id="dc203-122">Get the sample code</span></span>

- [<span data-ttu-id="dc203-123">Beispiel für XAML-Bottom-Up-Liste</span><span class="sxs-lookup"><span data-stu-id="dc203-123">XAML Bottom-up list sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/XamlBottomUpList)