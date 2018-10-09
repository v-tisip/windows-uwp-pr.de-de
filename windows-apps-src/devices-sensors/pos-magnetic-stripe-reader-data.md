---
author: eliotcowley
title: Abrufen und Magnetstreifen Daten verstehen
description: Enthält Informationen zum Sammeln und Interpretieren von Daten aus einer Magnetstreifenleser.
ms.author: elcowle
ms.date: 10/04/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, zeigen Sie Service, pos, Magnetstreifenleser
ms.localizationpriority: medium
ms.openlocfilehash: ad954e8c03d92307fa72ead236d5428ac2bdddab
ms.sourcegitcommit: 49aab071aa2bd88f1c165438ee7e5c854b3e4f61
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2018
ms.locfileid: "4463557"
---
# <a name="obtain-and-understand-magnetic-stripe-data"></a><span data-ttu-id="3f1a3-104">Abrufen und Magnetstreifen Daten verstehen</span><span class="sxs-lookup"><span data-stu-id="3f1a3-104">Obtain and understand magnetic stripe data</span></span>

<span data-ttu-id="3f1a3-105">Nachdem Sie Ihre Magnetstreifenleser in Ihrer Anwendung mithilfe der Schritte in [Erste Schritte mit Point of Service](pos-basics.md)eingerichtet haben, können Sie zum Abrufen von Daten aus starten.</span><span class="sxs-lookup"><span data-stu-id="3f1a3-105">Once you've set up your magnetic stripe reader in your application using the steps outlined in [Getting started with Point of Service](pos-basics.md), you're ready to start getting data from it.</span></span>

## <a name="subscribe-to-datareceived-events"></a><span data-ttu-id="3f1a3-106">Abonnieren Sie \* DataReceived-Ereignisse</span><span class="sxs-lookup"><span data-stu-id="3f1a3-106">Subscribe to \*DataReceived events</span></span>

<span data-ttu-id="3f1a3-107">Wenn der Reader eine gezogene Karte erkennt, wird eine der drei Ereignisse ausgelöst:</span><span class="sxs-lookup"><span data-stu-id="3f1a3-107">Whenever the reader recognizes a swiped card, it will raise one of three events:</span></span>

* <span data-ttu-id="3f1a3-108">[Ereignis AamvaCardDataReceived](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedmagneticstripereader.aamvacarddatareceived): tritt auf, wenn eine Karte Motor Fahrzeugs das gezogen wird.</span><span class="sxs-lookup"><span data-stu-id="3f1a3-108">[AamvaCardDataReceived Event](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedmagneticstripereader.aamvacarddatareceived): Occurs when a motor vehicle card is swiped.</span></span>
* <span data-ttu-id="3f1a3-109">[Ereignis BankCardDataReceived](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedmagneticstripereader.aamvacarddatareceived): tritt auf, wenn eine Bankkarte das gezogen wird.</span><span class="sxs-lookup"><span data-stu-id="3f1a3-109">[BankCardDataReceived Event](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedmagneticstripereader.aamvacarddatareceived): Occurs when a bank card is swiped.</span></span>
* <span data-ttu-id="3f1a3-110">[Ereignis VendorSpecificDataReceived](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedmagneticstripereader.vendorspecificdatareceived): tritt auf, wenn eine herstellerspezifische Karte das gezogen wird.</span><span class="sxs-lookup"><span data-stu-id="3f1a3-110">[VendorSpecificDataReceived Event](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedmagneticstripereader.vendorspecificdatareceived): Occurs when a vendor-specific card is swiped.</span></span>

<span data-ttu-id="3f1a3-111">Die Anwendung muss nur, um die Ereignisse zu abonnieren, die von der Magnetstreifenleser unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="3f1a3-111">Your application only needs to subscribe to the events that are supported by the magnetic stripe reader.</span></span> <span data-ttu-id="3f1a3-112">Sie können sehen, welche Arten von Karten mit [MagneticStripeReader.SupportedCardTypes](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereader.supportedcardtypes
)unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="3f1a3-112">You can see what types of cards are supported with [MagneticStripeReader.SupportedCardTypes](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereader.supportedcardtypes
).</span></span>

<span data-ttu-id="3f1a3-113">Der folgende Code veranschaulicht die drei abonnieren \***DataReceived** Ereignisse:</span><span class="sxs-lookup"><span data-stu-id="3f1a3-113">The following code demonstrates subscribing to the three \***DataReceived** events:</span></span>

```cs
private void SubscribeToEvents(ClaimedMagneticStripeReader claimedReader, MagneticStripeReader reader)
{
    foreach (var type in reader.SupportedCardTypes)
    {
        if (item == MagneticStripeReaderCardTypes.Aamva)
        {
            claimedReader.AamvaCardDataReceived += Reader_AamvaCardDataReceived;
        }
        else if (item == MagneticStripeReaderCardTypes.Bank)
        {
            claimedReader.BankCardDataReceived += Reader_BankCardDataReceived;
        }
        else if (item == MagneticStripeReaderCardTypes.ExtendedBase)
        {
            claimedReader.VendorSpecificDataReceived += Reader_VendorSpecificDataReceived;
        }
    }
}
```

<span data-ttu-id="3f1a3-114">Die [ClaimedMagneticStripeReader](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedmagneticstripereader) und ein *Args* -Objekt, das das Ereignis, dessen Typ abhängig ist, wird der Ereignishandler übergeben werden:</span><span class="sxs-lookup"><span data-stu-id="3f1a3-114">The event handler will be passed the [ClaimedMagneticStripeReader](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedmagneticstripereader) and an *args* object, whose type will vary depending on the event:</span></span>

* <span data-ttu-id="3f1a3-115">Ereignis **AamvaCardDataReceived** : [MagneticStripeReaderAamvaCardDataReceivedEventArgs-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderaamvacarddatareceivedeventargs)</span><span class="sxs-lookup"><span data-stu-id="3f1a3-115">**AamvaCardDataReceived** event: [MagneticStripeReaderAamvaCardDataReceivedEventArgs Class](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderaamvacarddatareceivedeventargs)</span></span>
* <span data-ttu-id="3f1a3-116">Ereignis **BankCardDataReceived** : [MagneticStripeReaderBankCardDataReceivedEventArgs-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderbankcarddatareceivedeventargs)</span><span class="sxs-lookup"><span data-stu-id="3f1a3-116">**BankCardDataReceived** event: [MagneticStripeReaderBankCardDataReceivedEventArgs Class](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderbankcarddatareceivedeventargs)</span></span>
* <span data-ttu-id="3f1a3-117">Ereignis **VendorSpecificDataReceived** : [MagneticStripeReaderVendorSpecificCardDataReceivedEventArgs-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereadervendorspecificcarddatareceivedeventargs)</span><span class="sxs-lookup"><span data-stu-id="3f1a3-117">**VendorSpecificDataReceived** event: [MagneticStripeReaderVendorSpecificCardDataReceivedEventArgs Class](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereadervendorspecificcarddatareceivedeventargs)</span></span>

## <a name="get-the-data"></a><span data-ttu-id="3f1a3-118">Abrufen der Daten</span><span class="sxs-lookup"><span data-stu-id="3f1a3-118">Get the data</span></span>

<span data-ttu-id="3f1a3-119">Für die Ereignisse **AamvaCardDataReceived** und **BankCardDataReceived** können Sie einige der Daten direkt aus dem *Args* -Objekt abrufen.</span><span class="sxs-lookup"><span data-stu-id="3f1a3-119">For the **AamvaCardDataReceived** and **BankCardDataReceived** events, you can get some of the data directly from the *args* object.</span></span> <span data-ttu-id="3f1a3-120">Das folgende Beispiel veranschaulicht das Abrufen von ein paar Eigenschaften und Membervariablen zuweisen:</span><span class="sxs-lookup"><span data-stu-id="3f1a3-120">The following example demonstrates getting a few properties and assigning them to member variables:</span></span>

```cs
private string _accountNumber;
private string _expirationDate;
private string _firstName;

private void Reader_BankCardDataReceived(
    ClaimedMagneticStripeReader sender, 
    MagneticStripeReaderBankCardDataReceivedEventArgs args)
{
    _accountNumber = args.AccountNumber;
    _expirationDate = args.ExpirationDate;
    _firstName = args.FirstName;
    // etc...
}
```

<span data-ttu-id="3f1a3-121">Einige Daten, einschließlich alle Daten vom **VendorSpecificDataReceived** -Ereignis, müssen jedoch über den **Bericht** -Objekt, abgerufen werden, die eine Eigenschaft des Parameters *Args* ist.</span><span class="sxs-lookup"><span data-stu-id="3f1a3-121">However, some data, including all data from the **VendorSpecificDataReceived** event, must be retrieved through the **Report** object, which is a property of the *args* parameter.</span></span> <span data-ttu-id="3f1a3-122">Dies ist vom Typ [MagneticStripeReaderReport](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderreport).</span><span class="sxs-lookup"><span data-stu-id="3f1a3-122">This is of type [MagneticStripeReaderReport](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderreport).</span></span>

<span data-ttu-id="3f1a3-123">Sie können mit der [CardType](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderreport.cardtype) -Eigenschaft können Sie herausfinden, welche Art von Karte gewischt wurde und dann verwenden, um darüber zu informieren, wie Sie die Daten aus [Track1](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderreport.track1), [Track2](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderreport.track2), [Track3](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderreport.track3)und [Track4](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderreport.track4)interpretiert werden.</span><span class="sxs-lookup"><span data-stu-id="3f1a3-123">You can use the [CardType](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderreport.cardtype) property to figure out what type of card has been swiped, and then use that to inform how you interpret the data from [Track1](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderreport.track1), [Track2](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderreport.track2), [Track3](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderreport.track3), and [Track4](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderreport.track4).</span></span>

<span data-ttu-id="3f1a3-124">Die Daten über die einzelnen Titel werden als [MagneticStripeReaderTrackData](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereadertrackdata) Objekte dargestellt.</span><span class="sxs-lookup"><span data-stu-id="3f1a3-124">The data from each of the tracks are represented as [MagneticStripeReaderTrackData](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereadertrackdata) objects.</span></span> <span data-ttu-id="3f1a3-125">Von dieser Klasse können Sie die folgenden Arten von Daten abrufen:</span><span class="sxs-lookup"><span data-stu-id="3f1a3-125">From this class, you can get the following types of data:</span></span>

* <span data-ttu-id="3f1a3-126">[Daten](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereadertrackdata.data): die unformatierten oder decodierten Daten.</span><span class="sxs-lookup"><span data-stu-id="3f1a3-126">[Data](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereadertrackdata.data): The raw or decoded data.</span></span>
* <span data-ttu-id="3f1a3-127">[DiscretionaryData](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereadertrackdata.discretionarydata): die verfügbare Daten.</span><span class="sxs-lookup"><span data-stu-id="3f1a3-127">[DiscretionaryData](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereadertrackdata.discretionarydata): The discretionary data.</span></span> 
* <span data-ttu-id="3f1a3-128">[EncryptedData](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereadertrackdata.encrypteddata): die verschlüsselten Daten.</span><span class="sxs-lookup"><span data-stu-id="3f1a3-128">[EncryptedData](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereadertrackdata.encrypteddata): The encrypted data.</span></span>

<span data-ttu-id="3f1a3-129">Der folgende Codeausschnitt Ruft den Bericht und die Track-Daten, und überprüft dann die Kartentyp:</span><span class="sxs-lookup"><span data-stu-id="3f1a3-129">The following code snippet gets the report and the track data, and then checks the card type:</span></span>

```cs
private void GetTrackData(MagneticStripeReaderBankCardDataReceivedEventArgs args)
{
    MagneticStripeReaderReport report = args.Report;
    IBuffer track1 = report.Track1.Data;
    IBuffer track2 = report.Track2.Data;
    IBuffer track3 = report.Track3.Data;
    IBuffer track4 = report.Track4.Data;

    if (report.CardType == MagneticStripeReaderCardTypes.Aamva)
    {
        // Card type is AAMVA
    }
    else if (report.CardType == MagneticStripeReaderCardTypes.Bank)
    {
        // Card type is bank card
    }
    else if (report.CardType == MagneticStripeReaderCardTypes.ExtendedBase)
    {
        // Card type is vendor-specific
    }
    else if (report.CardType == MagneticStripeReaderCardTypes.Unknown)
    {
        // Card type is unknown
    }
}
```

[!INCLUDE [feedback](./includes/pos-feedback.md)]

## <a name="see-also"></a><span data-ttu-id="3f1a3-130">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="3f1a3-130">See also</span></span>

* [<span data-ttu-id="3f1a3-131">Magnetstreifenleser</span><span class="sxs-lookup"><span data-stu-id="3f1a3-131">Magnetic stripe reader</span></span>](pos-magnetic-stripe-reader.md)
* [<span data-ttu-id="3f1a3-132">ClaimedMagneticStripeReader-Klasse</span><span class="sxs-lookup"><span data-stu-id="3f1a3-132">ClaimedMagneticStripeReader Class</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedmagneticstripereader)
* [<span data-ttu-id="3f1a3-133">MagneticStripeReaderAamvaCardDataReceivedEventArgs-Klasse</span><span class="sxs-lookup"><span data-stu-id="3f1a3-133">MagneticStripeReaderAamvaCardDataReceivedEventArgs Class</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderaamvacarddatareceivedeventargs)
* [<span data-ttu-id="3f1a3-134">MagneticStripeReaderBankCardDataReceivedEventArgs-Klasse</span><span class="sxs-lookup"><span data-stu-id="3f1a3-134">MagneticStripeReaderBankCardDataReceivedEventArgs Class</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderbankcarddatareceivedeventargs)
* [<span data-ttu-id="3f1a3-135">MagneticStripeReaderVendorSpecificCardDataReceivedEventArgs-Klasse</span><span class="sxs-lookup"><span data-stu-id="3f1a3-135">MagneticStripeReaderVendorSpecificCardDataReceivedEventArgs Class</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereadervendorspecificcarddatareceivedeventargs)
* [<span data-ttu-id="3f1a3-136">MagneticStripeReaderReport</span><span class="sxs-lookup"><span data-stu-id="3f1a3-136">MagneticStripeReaderReport</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderreport)
* [<span data-ttu-id="3f1a3-137">MagneticStripeReaderTrackData</span><span class="sxs-lookup"><span data-stu-id="3f1a3-137">MagneticStripeReaderTrackData</span></span>](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereadertrackdata)