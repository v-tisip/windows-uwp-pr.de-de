---
author: eliotcowley
title: Abrufen und Verstehen von Magnetstreifendaten
description: Enthält Informationen zum Erhalt und interpretiert die Daten aus einer Magnetstreifen.
ms.author: elcowle
ms.date: 10/04/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, zeigen Sie Service, pos, Magnetstreifenleser
ms.localizationpriority: medium
ms.openlocfilehash: ad954e8c03d92307fa72ead236d5428ac2bdddab
ms.sourcegitcommit: 1c6325aa572868b789fcdd2efc9203f67a83872a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2018
ms.locfileid: "4749901"
---
# <a name="obtain-and-understand-magnetic-stripe-data"></a>Abrufen und Verstehen von Magnetstreifendaten

Nachdem Sie Ihre Magnetstreifenleser in Ihrer Anwendung mithilfe der Schritte in [Erste Schritte mit Point of Service](pos-basics.md)eingerichtet haben, können Sie mit dem Abrufen von Daten von ihm begonnen.

## <a name="subscribe-to-datareceived-events"></a>Abonnieren Sie * DataReceived-Ereignisse

Wenn der Reader eine gezogene Karte erkannt wird, wird eine der drei Ereignisse ausgelöst:

* [AamvaCardDataReceived Ereignis](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedmagneticstripereader.aamvacarddatareceived): tritt auf, wenn eine Karte Motor Fahrzeugs gewischt ist.
* [BankCardDataReceived Ereignis](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedmagneticstripereader.aamvacarddatareceived): tritt auf, wenn eine Bankkarte gewischt ist.
* [VendorSpecificDataReceived Ereignis](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedmagneticstripereader.vendorspecificdatareceived): tritt auf, wenn eine herstellerspezifische Karte das gezogen wird.

Die Anwendung muss nur, um die Ereignisse zu abonnieren, die von der Magnetstreifenleser unterstützt werden. Sie können sehen, welche Arten von Karten mit [MagneticStripeReader.SupportedCardTypes](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereader.supportedcardtypes
)unterstützt werden.

Der folgende Code veranschaulicht die drei abonnieren ***DataReceived** Ereignisse:

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

[ClaimedMagneticStripeReader](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedmagneticstripereader) und ein *Args* -Objekt, das das Ereignis, dessen Typ abhängig ist, wird der Ereignishandler übergeben werden:

* Ereignis **AamvaCardDataReceived** : [MagneticStripeReaderAamvaCardDataReceivedEventArgs-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderaamvacarddatareceivedeventargs)
* Ereignis **BankCardDataReceived** : [MagneticStripeReaderBankCardDataReceivedEventArgs-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderbankcarddatareceivedeventargs)
* Ereignis **VendorSpecificDataReceived** : [MagneticStripeReaderVendorSpecificCardDataReceivedEventArgs-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereadervendorspecificcarddatareceivedeventargs)

## <a name="get-the-data"></a>Abrufen der Daten

Für die Ereignisse **AamvaCardDataReceived** und **BankCardDataReceived** können Sie einige der Daten direkt aus dem *Args* -Objekt abrufen. Das folgende Beispiel zeigt einige Eigenschaften abrufen und zuweisen Membervariablen hinzu:

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

Allerdings müssen einige Daten, einschließlich aller Daten aus dem Ereignis **VendorSpecificDataReceived** über das Objekt **Bericht** abgerufen werden eine Eigenschaft des *EventArgs* -Parameters. Dies ist vom Typ [MagneticStripeReaderReport](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderreport).

Sie können mit der [CardType](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderreport.cardtype) -Eigenschaft können Sie herausfinden, welche Art von Karte gewischt wurde, und verwenden diese, um darüber zu informieren, wie Sie die Daten aus [Track1](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderreport.track1), [Track2](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderreport.track2), [Track3](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderreport.track3)und [Track4](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderreport.track4)interpretiert werden.

Die Daten über die einzelnen Titel werden als [MagneticStripeReaderTrackData](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereadertrackdata) Objekte dargestellt. Von dieser Klasse können Sie die folgenden Arten von Daten erhalten:

* [Daten](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereadertrackdata.data): die unformatierten oder decodierten Daten.
* [DiscretionaryData](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereadertrackdata.discretionarydata): die verfügbare Daten. 
* [EncryptedData](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereadertrackdata.encrypteddata): die verschlüsselten Daten.

Der folgende Codeausschnitt Ruft den Bericht und die Track-Daten, und dann überprüft die Kartentyp:

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

## <a name="see-also"></a>Weitere Informationen:

* [Magnetstreifenleser](pos-magnetic-stripe-reader.md)
* [ClaimedMagneticStripeReader-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.claimedmagneticstripereader)
* [MagneticStripeReaderAamvaCardDataReceivedEventArgs-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderaamvacarddatareceivedeventargs)
* [MagneticStripeReaderBankCardDataReceivedEventArgs-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderbankcarddatareceivedeventargs)
* [MagneticStripeReaderVendorSpecificCardDataReceivedEventArgs-Klasse](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereadervendorspecificcarddatareceivedeventargs)
* [MagneticStripeReaderReport](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereaderreport)
* [MagneticStripeReaderTrackData](https://docs.microsoft.com/uwp/api/windows.devices.pointofservice.magneticstripereadertrackdata)