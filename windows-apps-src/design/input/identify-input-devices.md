---
Description: Identify the input devices connected to a Universal Windows Platform (UWP) device and identify their capabilities and attributes.
title: Identifizieren von Eingabegeräten
ms.assetid: B2E93FBF-C508-44D9-BA46-ECFDAA8746F4
label: Identify input devices
template: detail.hbs
keywords: Gerät, Digitalisierer, Eingabe, Interaktion
ms.date: 02/08/2017
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: c45ad71643b0d75efcb130c1175952822197a161
ms.sourcegitcommit: b11f305dbf7649c4b68550b666487c77ea30d98f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "7827049"
---
# <a name="identify-input-devices"></a><span data-ttu-id="98ad9-103">Identifizieren von Eingabegeräten</span><span class="sxs-lookup"><span data-stu-id="98ad9-103">Identify input devices</span></span>


<span data-ttu-id="98ad9-104">Identifizieren Sie die Eingabegeräte, die mit einem Gerät für die universelle Windows-Plattform (UWP) verbunden sind, sowie deren Funktionen und Attribute.</span><span class="sxs-lookup"><span data-stu-id="98ad9-104">Identify the input devices connected to a Universal Windows Platform (UWP) device and identify their capabilities and attributes.</span></span>

> <span data-ttu-id="98ad9-105">**Wichtige APIs**: [**Windows.Devices.Input**](https://msdn.microsoft.com/library/windows/apps/br225648), [**Windows.UI.Input**](https://msdn.microsoft.com/library/windows/apps/br208383), [**Windows.UI.Xaml.Input**](https://msdn.microsoft.com/library/windows/apps/br242084)</span><span class="sxs-lookup"><span data-stu-id="98ad9-105">**Important APIs**: [**Windows.Devices.Input**](https://msdn.microsoft.com/library/windows/apps/br225648), [**Windows.UI.Input**](https://msdn.microsoft.com/library/windows/apps/br208383), [**Windows.UI.Xaml.Input**](https://msdn.microsoft.com/library/windows/apps/br242084)</span></span>

## <a name="retrieve-mouse-properties"></a><span data-ttu-id="98ad9-106">Abrufen von Mauseigenschaften</span><span class="sxs-lookup"><span data-stu-id="98ad9-106">Retrieve mouse properties</span></span>


<span data-ttu-id="98ad9-107">Der [**Windows.Devices.Input**](https://msdn.microsoft.com/library/windows/apps/br225648)-Namespace enthält die [**MouseCapabilities**](https://msdn.microsoft.com/library/windows/apps/br225626)-Klasse, mit der Sie die Eigenschaften abrufen können, die von einer oder mehreren angeschlossenen Mäusen bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="98ad9-107">The [**Windows.Devices.Input**](https://msdn.microsoft.com/library/windows/apps/br225648) namespace contains the [**MouseCapabilities**](https://msdn.microsoft.com/library/windows/apps/br225626) class used to retrieve the properties exposed by one or more connected mice.</span></span> <span data-ttu-id="98ad9-108">Erstellen Sie einfach ein neues **MouseCapabilities**-Objekt, und rufen Sie die benötigten Eigenschaften ab.</span><span class="sxs-lookup"><span data-stu-id="98ad9-108">Just create a new **MouseCapabilities** object and get the properties you're interested in.</span></span>

<span data-ttu-id="98ad9-109">**Hinweis:** die von den hier beschriebenen Eigenschaften zurückgegebenen Werte basieren auf allen ermittelten Mäusen: boolesche Eigenschaften geben ungleich 0 zurück, wenn mindestens eine Maus eine bestimmte Funktion unterstützt, während numerische Eigenschaften den größten Wert von jedem anderen zurückgeben Maus.</span><span class="sxs-lookup"><span data-stu-id="98ad9-109">**Note**The values returned by the properties discussed here are based on all detected mice: Boolean properties return non-zero if at least one mouse supports a specific capability, and numeric properties return the maximum value exposed by any one mouse.</span></span>

 

<span data-ttu-id="98ad9-110">Der folgende Code verwendet eine Reihe von [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652)-Elementen, um die einzelnen Mauseigenschaften und -werte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="98ad9-110">The following code uses a series of [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) elements to display the individual mouse properties and values.</span></span>

```CSharp
private void GetMouseProperties()
{
    MouseCapabilities mouseCapabilities = new Windows.Devices.Input.MouseCapabilities();
    MousePresent.Text = mouseCapabilities.MousePresent != 0 ? "Yes" : "No";
    VertWheel.Text = mouseCapabilities.VerticalWheelPresent != 0 ? "Yes" : "No";
    HorzWheel.Text = mouseCapabilities.HorizontalWheelPresent != 0 ? "Yes" : "No";
    SwappedButtons.Text = mouseCapabilities.SwapButtons != 0 ? "Yes" : "No";
    NumButtons.Text = mouseCapabilities.NumberOfButtons.ToString();
}
```

## <a name="retrieve-keyboard-properties"></a><span data-ttu-id="98ad9-111">Abrufen von Tastatureigenschaften</span><span class="sxs-lookup"><span data-stu-id="98ad9-111">Retrieve keyboard properties</span></span>


<span data-ttu-id="98ad9-112">Der [**Windows.Devices.Input**](https://msdn.microsoft.com/library/windows/apps/br225648)-Namespace enthält die [**KeyboardCapabilities**](https://msdn.microsoft.com/library/windows/apps/br225623)-Klasse, mit der Sie ermitteln können, ob eine Tastatur angeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="98ad9-112">The [**Windows.Devices.Input**](https://msdn.microsoft.com/library/windows/apps/br225648) namespace contains the [**KeyboardCapabilities**](https://msdn.microsoft.com/library/windows/apps/br225623) class used to retrieve whether a keyboard is connected.</span></span> <span data-ttu-id="98ad9-113">Erstellen Sie einfach ein neues **KeyboardCapabilities**-Objekt, und rufen Sie die [**KeyboardPresent**](https://msdn.microsoft.com/library/windows/apps/br225625)-Eigenschaft ab.</span><span class="sxs-lookup"><span data-stu-id="98ad9-113">Just create a new **KeyboardCapabilities** object and get the [**KeyboardPresent**](https://msdn.microsoft.com/library/windows/apps/br225625) property.</span></span>

<span data-ttu-id="98ad9-114">Der folgende Code verwendet ein [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652)-Element, um die Tastatureigenschaft und ihren Wert anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="98ad9-114">The following code uses a [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) element to display the keyboard property and value.</span></span>

```CSharp
private void GetKeyboardProperties()
{
    KeyboardCapabilities keyboardCapabilities = new Windows.Devices.Input.KeyboardCapabilities();
    KeyboardPresent.Text = keyboardCapabilities.KeyboardPresent != 0 ? "Yes" : "No";
}
```

## <a name="retrieve-touch-properties"></a><span data-ttu-id="98ad9-115">Abrufen von Berührungseigenschaften</span><span class="sxs-lookup"><span data-stu-id="98ad9-115">Retrieve touch properties</span></span>


<span data-ttu-id="98ad9-116">Der [**Windows.Devices.Input**](https://msdn.microsoft.com/library/windows/apps/br225648)-Namespace enthält die [**TouchCapabilities**](https://msdn.microsoft.com/library/windows/apps/br225644)-Klasse, mit der Sie ermitteln können, ob Touchdigitalisierungsgeräte angeschlossen sind.</span><span class="sxs-lookup"><span data-stu-id="98ad9-116">The [**Windows.Devices.Input**](https://msdn.microsoft.com/library/windows/apps/br225648) namespace contains the [**TouchCapabilities**](https://msdn.microsoft.com/library/windows/apps/br225644) class used to retrieve whether any touch digitizers are connected.</span></span> <span data-ttu-id="98ad9-117">Erstellen Sie einfach ein neues **TouchCapabilities**-Objekt, und rufen Sie die benötigten Eigenschaften ab.</span><span class="sxs-lookup"><span data-stu-id="98ad9-117">Just create a new **TouchCapabilities** object and get the properties you're interested in.</span></span>

<span data-ttu-id="98ad9-118">**Hinweis:** die von den hier beschriebenen Eigenschaften zurückgegebenen Werte basieren auf allen ermittelten touchdigitalisierungsgeräten: boolesche Eigenschaften geben ungleich 0 zurück, wenn mindestens ein Digitalisierungsgerät eine bestimmte Funktion unterstützt, während numerische Eigenschaften den größten Wert zurückgeben von eines verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="98ad9-118">**Note**The values returned by the properties discussed here are based on all detected touch digitizers: Boolean properties return non-zero if at least one digitizer supports a specific capability, and numeric properties return the maximum value exposed by any one digitizer.</span></span>

 

<span data-ttu-id="98ad9-119">Der folgende Code verwendet eine Reihe von [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652)-Elementen, um die Eigenschaften und Werte der einzelnen Touchdigitalisierer anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="98ad9-119">The following code uses a series of [**TextBlock**](https://msdn.microsoft.com/library/windows/apps/br209652) elements to display the touch properties and values.</span></span>

```CSharp
private void GetTouchProperties()
{
    TouchCapabilities touchCapabilities = new Windows.Devices.Input.TouchCapabilities();
    TouchPresent.Text = touchCapabilities.TouchPresent != 0 ? "Yes" : "No";
    Contacts.Text = touchCapabilities.Contacts.ToString();
}
```

## <a name="retrieve-pointer-properties"></a><span data-ttu-id="98ad9-120">Abrufen von Zeigereigenschaften</span><span class="sxs-lookup"><span data-stu-id="98ad9-120">Retrieve pointer properties</span></span>


<span data-ttu-id="98ad9-121">Der [**Windows.Devices.Input**](https://msdn.microsoft.com/library/windows/apps/br225648)-Namespace enthält die [**PointerDevice**](https://msdn.microsoft.com/library/windows/apps/br225633)-Klasse, mit der Sie abrufen können, ob eines der erkannten Geräte Zeigereingaben (Toucheingabe, Stift oder Maus) unterstützt.</span><span class="sxs-lookup"><span data-stu-id="98ad9-121">The [**Windows.Devices.Input**](https://msdn.microsoft.com/library/windows/apps/br225648) namespace contains the [**PointerDevice**](https://msdn.microsoft.com/library/windows/apps/br225633) class used to retrieve whether any detected devices support pointer input (touch, touchpad, mouse, or pen).</span></span> <span data-ttu-id="98ad9-122">Erstellen Sie einfach ein neues **PointerDevice**-Objekt, und rufen Sie die benötigten Eigenschaften ab.</span><span class="sxs-lookup"><span data-stu-id="98ad9-122">Just create a new **PointerDevice** object and get the properties you're interested in.</span></span>

<span data-ttu-id="98ad9-123">**Hinweis:** die von den hier beschriebenen Eigenschaften zurückgegebenen Werte basieren auf allen ermittelten Zeigegeräten: boolesche Eigenschaften geben ungleich 0 zurück, wenn mindestens ein Gerät eine bestimmte Funktion unterstützt, während numerische Eigenschaften den größten Wert zurückgeben von jedem Gerät einen Zeiger.</span><span class="sxs-lookup"><span data-stu-id="98ad9-123">**Note**The values returned by the properties discussed here are based on all detected pointer devices: Boolean properties return non-zero if at least one device supports a specific capability, and numeric properties return the maximum value exposed by any one pointer device.</span></span>

<span data-ttu-id="98ad9-124">Der folgende Code zeigt in einer Tabelle die Eigenschaften und Werte der einzelnen Zeigergeräte an.</span><span class="sxs-lookup"><span data-stu-id="98ad9-124">The following code uses a table to display the properties and values for each pointer device.</span></span>

```CSharp
private void GetPointerDevices()
{
    IReadOnlyList<PointerDevice> pointerDevices = Windows.Devices.Input.PointerDevice.GetPointerDevices();
    int gridRow = 0;
    int gridColumn = 0;

    for (int i = 0; i < pointerDevices.Count; i++)
    {
        // Pointer device type.
        TextBlock textBlock1 = new TextBlock();
        Grid_PointerProps.Children.Add(textBlock1);
        textBlock1.Text = (i + 1).ToString() + " Pointer Device Type:";
        Grid.SetRow(textBlock1, gridRow);
        Grid.SetColumn(textBlock1, gridColumn);

        TextBlock textBlock2 = new TextBlock();
        textBlock2.Text = pointerDevices[i].PointerDeviceType.ToString();
        Grid_PointerProps.Children.Add(textBlock2);
        Grid.SetRow(textBlock2, gridRow++);
        Grid.SetColumn(textBlock2, gridColumn + 1);

        // Is external?
        TextBlock textBlock3 = new TextBlock();
        Grid_PointerProps.Children.Add(textBlock3);
        textBlock3.Text = (i + 1).ToString() + " Is External?";
        Grid.SetRow(textBlock3, gridRow);
        Grid.SetColumn(textBlock3, gridColumn);

        TextBlock textBlock4 = new TextBlock();
        Grid_PointerProps.Children.Add(textBlock4);
        textBlock4.Text = pointerDevices[i].IsIntegrated.ToString();
        Grid.SetRow(textBlock4, gridRow++);
        Grid.SetColumn(textBlock4, gridColumn + 1);

        // Maximum contacts.
        TextBlock textBlock5 = new TextBlock();
        Grid_PointerProps.Children.Add(textBlock5);
        textBlock5.Text = (i + 1).ToString() + " Max Contacts:";
        Grid.SetRow(textBlock5, gridRow);
        Grid.SetColumn(textBlock5, gridColumn);

        TextBlock textBlock6 = new TextBlock();
        Grid_PointerProps.Children.Add(textBlock6);
        textBlock6.Text = pointerDevices[i].MaxContacts.ToString();
        Grid.SetRow(textBlock6, gridRow++);
        Grid.SetColumn(textBlock6, gridColumn + 1);

        // Physical device rectangle.
        TextBlock textBlock7 = new TextBlock();
        Grid_PointerProps.Children.Add(textBlock7);
        textBlock7.Text = (i + 1).ToString() + " Physical Device Rect:";
        Grid.SetRow(textBlock7, gridRow);
        Grid.SetColumn(textBlock7, gridColumn);

        TextBlock textBlock8 = new TextBlock();
        Grid_PointerProps.Children.Add(textBlock8);
        textBlock8.Text = pointerDevices[i].PhysicalDeviceRect.X.ToString() + "," +
            pointerDevices[i].PhysicalDeviceRect.Y.ToString() + "," +
            pointerDevices[i].PhysicalDeviceRect.Width.ToString() + "," +
            pointerDevices[i].PhysicalDeviceRect.Height.ToString();
        Grid.SetRow(textBlock8, gridRow++);
        Grid.SetColumn(textBlock8, gridColumn + 1);

        // Screen rectangle.
        TextBlock textBlock9 = new TextBlock();
        Grid_PointerProps.Children.Add(textBlock9);
        textBlock9.Text = (i + 1).ToString() + " Screen Rect:";
        Grid.SetRow(textBlock9, gridRow);
        Grid.SetColumn(textBlock9, gridColumn);

        TextBlock textBlock10 = new TextBlock();
        Grid_PointerProps.Children.Add(textBlock10);
        textBlock10.Text = pointerDevices[i].ScreenRect.X.ToString() + "," +
            pointerDevices[i].ScreenRect.Y.ToString() + "," +
            pointerDevices[i].ScreenRect.Width.ToString() + "," +
            pointerDevices[i].ScreenRect.Height.ToString();
        Grid.SetRow(textBlock10, gridRow++);
        Grid.SetColumn(textBlock10, gridColumn + 1);

        gridColumn += 2;
        gridRow = 0;
    }
```

## <a name="related-articles"></a><span data-ttu-id="98ad9-125">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="98ad9-125">Related articles</span></span>


**<span data-ttu-id="98ad9-126">Beispiele</span><span class="sxs-lookup"><span data-stu-id="98ad9-126">Samples</span></span>**
* [<span data-ttu-id="98ad9-127">Einfaches Eingabebeispiel</span><span class="sxs-lookup"><span data-stu-id="98ad9-127">Basic input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620302)
* [<span data-ttu-id="98ad9-128">Beispiel für Eingabe mit niedriger Latenz</span><span class="sxs-lookup"><span data-stu-id="98ad9-128">Low latency input sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=620304)
* [<span data-ttu-id="98ad9-129">Beispiel für den Benutzerinteraktionsmodus</span><span class="sxs-lookup"><span data-stu-id="98ad9-129">User interaction mode sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=619894)

**<span data-ttu-id="98ad9-130">Archivbeispiele</span><span class="sxs-lookup"><span data-stu-id="98ad9-130">Archive samples</span></span>**
* [<span data-ttu-id="98ad9-131">Eingabe: Beispiel für Gerätefunktionen</span><span class="sxs-lookup"><span data-stu-id="98ad9-131">Input: Device capabilities sample</span></span>](http://go.microsoft.com/fwlink/p/?linkid=231530)
 

 




