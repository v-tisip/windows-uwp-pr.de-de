---
author: Xansky
ms.assetid: E322DFFE-8EEC-499D-87BC-EDA5CFC27551
description: Jede Microsoft Store-Transaktion, die zu einem erfolgreichen Produktkauf führt, kann optional einen Transaktionsbeleg zurückgeben.
title: Überprüfen von Produktkäufen anhand von Belegen
ms.author: mhopkins
ms.date: 04/16/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, In-App-Einkäufe, IAPs, Belege, Windows.ApplicationModel.Store
ms.localizationpriority: medium
ms.openlocfilehash: ee6ca7876588efd8b8a5c86cfc8896d84ede91b9
ms.sourcegitcommit: 106aec1e59ba41aae2ac00f909b81bf7121a6ef1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2018
ms.locfileid: "4610419"
---
# <a name="use-receipts-to-verify-product-purchases"></a><span data-ttu-id="774f1-104">Überprüfen von Produktkäufen anhand von Belegen</span><span class="sxs-lookup"><span data-stu-id="774f1-104">Use receipts to verify product purchases</span></span>

<span data-ttu-id="774f1-105">Jede Microsoft Store-Transaktion, die zu einem erfolgreichen Produktkauf führt, kann optional einen Transaktionsbeleg zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="774f1-105">Each Microsoft Store transaction that results in a successful product purchase can optionally return a transaction receipt.</span></span> <span data-ttu-id="774f1-106">Dieser Beleg enthalten Informationen zum gelisteten Produkt und zu den Kosten für den Kunden.</span><span class="sxs-lookup"><span data-stu-id="774f1-106">This receipt provides information about the listed product and monetary cost to the customer.</span></span>

<span data-ttu-id="774f1-107">Der Zugriff auf diese Informationen unterstützt Szenarien, in denen Ihre App überprüfen muss, ob ein Benutzer Ihre App oder ein Add-On (auch als In-App-Produkt oder IAP bezeichnet) im MicrosoftStore gekauft hat.</span><span class="sxs-lookup"><span data-stu-id="774f1-107">Having access to this information supports scenarios where your app needs to verify that a user purchased your app, or has made add-on (also called in-app product or IAP) purchases from the Microsoft Store.</span></span> <span data-ttu-id="774f1-108">Das kann zum Beispiel bei einem Spiel der Fall sein, für das Inhalte heruntergeladen werden können.</span><span class="sxs-lookup"><span data-stu-id="774f1-108">For example, imagine a game that offers downloaded content.</span></span> <span data-ttu-id="774f1-109">Wenn der Benutzer, der die Spielinhalte gekauft hat, das Spiel auf einem anderen Gerät spielen möchte, müssen Sie überprüfen, ob der Benutzer die Inhalte bereits besitzt.</span><span class="sxs-lookup"><span data-stu-id="774f1-109">If the user who purchased the game content wants to play it on a different device, you need to verify that the user already owns the content.</span></span> <span data-ttu-id="774f1-110">Gehen Sie dazu wie folgt vor.</span><span class="sxs-lookup"><span data-stu-id="774f1-110">Here's how.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="774f1-111">Dieser Artikel beschreibt, wie Sie Mitglieder des [Windows.ApplicationModel.Store](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Store)-Namespace verwenden, um einen Beleg für einen In-App-Kauf abzurufen und zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="774f1-111">This article shows how to use members of the [Windows.ApplicationModel.Store](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Store) namespace to get and validate a receipt for an in-app purchase.</span></span> <span data-ttu-id="774f1-112">Wenn Sie den [Windows.Services.Store](https://docs.microsoft.com/uwp/api/Windows.Services.Store)-Namespace für In-App-Käufe verwenden (eingeführt in Windows 10, Version 1607, und für Projekte verfügbar, die die **Windows 10 Anniversary Edition (10.0; Build 14393)** oder eine spätere Freigabe in Visual Studio verwenden), müssen Sie beachten, dass dieser Namespace keine API zum Abrufen von Kaufbelegen für In-App-Käufen enthält.</span><span class="sxs-lookup"><span data-stu-id="774f1-112">If you are using the [Windows.Services.Store](https://docs.microsoft.com/uwp/api/Windows.Services.Store) namespace for in-app purchases (introduced in Windows 10, version 1607, and available to projects that target **Windows 10 Anniversary Edition (10.0; Build 14393)** or a later release in Visual Studio), this namespace does not provide an API for getting purchase receipts for in-app purchases.</span></span> <span data-ttu-id="774f1-113">Sie können jedoch eine REST-Methode in der Microsoft Store-Sammlungs-API verwenden, um Daten für eine Kauftransaktion abzurufen.</span><span class="sxs-lookup"><span data-stu-id="774f1-113">However, you can use a REST method in the Microsoft Store collection API to get data for a purchase transaction.</span></span> <span data-ttu-id="774f1-114">Weitere Informationen finden Sie unter [Belege für In-App-Käufe](in-app-purchases-and-trials.md#receipts).</span><span class="sxs-lookup"><span data-stu-id="774f1-114">For more information, see [Receipts for in-app purchases](in-app-purchases-and-trials.md#receipts).</span></span>

## <a name="requesting-a-receipt"></a><span data-ttu-id="774f1-115">Anfordern eines Belegs</span><span class="sxs-lookup"><span data-stu-id="774f1-115">Requesting a receipt</span></span>


<span data-ttu-id="774f1-116">Der **Windows.ApplicationModel.Store**-Namespace unterstützt verschiedene Möglichkeiten für das Abrufen eines Belegs:</span><span class="sxs-lookup"><span data-stu-id="774f1-116">The **Windows.ApplicationModel.Store** namespace supports several ways to get a receipt:</span></span>

* <span data-ttu-id="774f1-117">Wenn Sie mithilfe von [CurrentApp.RequestAppPurchaseAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp.requestapppurchaseasync) oder [CurrentApp.RequestProductPurchaseAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp.requestproductpurchaseasync) (oder eine andere Überladung dieser Methode) einen Kauf durchführen, enthält der Rückgabewert den Beleg.</span><span class="sxs-lookup"><span data-stu-id="774f1-117">When you make a purchase by using [CurrentApp.RequestAppPurchaseAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp.requestapppurchaseasync) or [CurrentApp.RequestProductPurchaseAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp.requestproductpurchaseasync) (or one of the other overloads of this method), the return value contains the receipt.</span></span>
* <span data-ttu-id="774f1-118">Sie können die Methode [CurrentApp.GetAppReceiptAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp.getappreceiptasync) aufrufen, um die aktuellen Beleginformationen für Ihre App und alle Add-Ons in Ihrer App abzurufen.</span><span class="sxs-lookup"><span data-stu-id="774f1-118">You can call the [CurrentApp.GetAppReceiptAsync](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp.getappreceiptasync) method to retrieve the current receipt info for your app and any add-ons in your app.</span></span>

<span data-ttu-id="774f1-119">Ein App-Beleg sieht ungefähr wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="774f1-119">An app receipt looks something like this.</span></span>

> [!NOTE]
> <span data-ttu-id="774f1-120">Dieses Beispiel ist formatiert, damit das XML lesbar ist.</span><span class="sxs-lookup"><span data-stu-id="774f1-120">This example is formatted to help make the XML readable.</span></span> <span data-ttu-id="774f1-121">Echte App-Belege enthalten keine Leerzeichen zwischen Elementen.</span><span class="sxs-lookup"><span data-stu-id="774f1-121">Real app receipts do not include whitespace between elements.</span></span>

> [!div class="tabbedCodeSnippets"]
```xml
<Receipt Version="1.0" ReceiptDate="2012-08-30T23:10:05Z" CertificateId="b809e47cd0110a4db043b3f73e83acd917fe1336" ReceiptDeviceId="4e362949-acc3-fe3a-e71b-89893eb4f528">
    <AppReceipt Id="8ffa256d-eca8-712a-7cf8-cbf5522df24b" AppId="55428GreenlakeApps.CurrentAppSimulatorEventTest_z7q3q7z11crfr" PurchaseDate="2012-06-04T23:07:24Z" LicenseType="Full" />
    <ProductReceipt Id="6bbf4366-6fb2-8be8-7947-92fd5f683530" ProductId="Product1" PurchaseDate="2012-08-30T23:08:52Z" ExpirationDate="2012-09-02T23:08:49Z" ProductType="Durable" AppId="55428GreenlakeApps.CurrentAppSimulatorEventTest_z7q3q7z11crfr" />
    <Signature xmlns="http://www.w3.org/2000/09/xmldsig#">
        <SignedInfo>
            <CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#" />
            <SignatureMethod Algorithm="http://www.w3.org/2001/04/xmldsig-more#rsa-sha256" />
            <Reference URI="">
                <Transforms>
                    <Transform Algorithm="http://www.w3.org/2000/09/xmldsig#enveloped-signature" />
                </Transforms>
                <DigestMethod Algorithm="http://www.w3.org/2001/04/xmlenc#sha256" />
                <DigestValue>cdiU06eD8X/w1aGCHeaGCG9w/kWZ8I099rw4mmPpvdU=</DigestValue>
            </Reference>
        </SignedInfo>
        <SignatureValue>SjRIxS/2r2P6ZdgaR9bwUSa6ZItYYFpKLJZrnAa3zkMylbiWjh9oZGGng2p6/gtBHC2dSTZlLbqnysJjl7mQp/A3wKaIkzjyRXv3kxoVaSV0pkqiPt04cIfFTP0JZkE5QD/vYxiWjeyGp1dThEM2RV811sRWvmEs/hHhVxb32e8xCLtpALYx3a9lW51zRJJN0eNdPAvNoiCJlnogAoTToUQLHs72I1dECnSbeNPXiG7klpy5boKKMCZfnVXXkneWvVFtAA1h2sB7ll40LEHO4oYN6VzD+uKd76QOgGmsu9iGVyRvvmMtahvtL1/pxoxsTRedhKq6zrzCfT8qfh3C1w==</SignatureValue>
    </Signature>
</Receipt>
```

<span data-ttu-id="774f1-122">Ein Produktbeleg sieht wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="774f1-122">A product receipt looks like this.</span></span>

> [!NOTE]
> <span data-ttu-id="774f1-123">Dieses Beispiel ist formatiert, damit das XML lesbar ist.</span><span class="sxs-lookup"><span data-stu-id="774f1-123">This example is formatted to help make the XML readable.</span></span> <span data-ttu-id="774f1-124">Echte Produkt-Belege enthalten keine Leerzeichen zwischen Elementen.</span><span class="sxs-lookup"><span data-stu-id="774f1-124">Real product receipts do not include whitespace between elements.</span></span>

> [!div class="tabbedCodeSnippets"]
```xml
<Receipt Version="1.0" ReceiptDate="2012-08-30T23:08:52Z" CertificateId="b809e47cd0110a4db043b3f73e83acd917fe1336" ReceiptDeviceId="4e362949-acc3-fe3a-e71b-89893eb4f528">
    <ProductReceipt Id="6bbf4366-6fb2-8be8-7947-92fd5f683530" ProductId="Product1" PurchaseDate="2012-08-30T23:08:52Z" ExpirationDate="2012-09-02T23:08:49Z" ProductType="Durable" AppId="55428GreenlakeApps.CurrentAppSimulatorEventTest_z7q3q7z11crfr" />
    <Signature xmlns="http://www.w3.org/2000/09/xmldsig#">
        <SignedInfo>
            <CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#" />
            <SignatureMethod Algorithm="http://www.w3.org/2001/04/xmldsig-more#rsa-sha256" />
            <Reference URI="">
                <Transforms>
                    <Transform Algorithm="http://www.w3.org/2000/09/xmldsig#enveloped-signature" />
                </Transforms>
                <DigestMethod Algorithm="http://www.w3.org/2001/04/xmlenc#sha256" />
                <DigestValue>Uvi8jkTYd3HtpMmAMpOm94fLeqmcQ2KCrV1XmSuY1xI=</DigestValue>
            </Reference>
        </SignedInfo>
        <SignatureValue>TT5fDET1X9nBk9/yKEJAjVASKjall3gw8u9N5Uizx4/Le9RtJtv+E9XSMjrOXK/TDicidIPLBjTbcZylYZdGPkMvAIc3/1mdLMZYJc+EXG9IsE9L74LmJ0OqGH5WjGK/UexAXxVBWDtBbDI2JLOaBevYsyy+4hLOcTXDSUA4tXwPa2Bi+BRoUTdYE2mFW7ytOJNEs3jTiHrCK6JRvTyU9lGkNDMNx9loIr+mRks+BSf70KxPtE9XCpCvXyWa/Q1JaIyZI7llCH45Dn4SKFn6L/JBw8G8xSTrZ3sBYBKOnUDbSCfc8ucQX97EyivSPURvTyImmjpsXDm2LBaEgAMADg==</SignatureValue>
    </Signature>
</Receipt>
```

<span data-ttu-id="774f1-125">Sie können beide Belegbeispiele verwenden, um den Überprüfungscode zu testen.</span><span class="sxs-lookup"><span data-stu-id="774f1-125">You can use either of these receipt examples to test your validation code.</span></span> <span data-ttu-id="774f1-126">Weitere Informationen zum Inhalt des Belegs finden Sie unter [Beschreibungen von Elementen und Attributen](#receipt-descriptions).</span><span class="sxs-lookup"><span data-stu-id="774f1-126">For more information about the contents of the receipt, see the [element and attribute descriptions](#receipt-descriptions).</span></span>

## <a name="validating-a-receipt"></a><span data-ttu-id="774f1-127">Überprüfen eines Belegs</span><span class="sxs-lookup"><span data-stu-id="774f1-127">Validating a receipt</span></span>

<span data-ttu-id="774f1-128">Um die Authentizität eines Belegs zu überprüfen, muss das Back-End-System (ein Webdienst oder ähnlich) die Belegsignatur mithilfe des öffentlichen Zertifikats überprüfen.</span><span class="sxs-lookup"><span data-stu-id="774f1-128">To validate a receipt's authenticity, you need your back-end system (a web service or something similar) to check the receipt's signature using the public certificate.</span></span> <span data-ttu-id="774f1-129">Um dieses Zertifikat abzurufen, verwenden Sie die URL ```https://go.microsoft.com/fwlink/p/?linkid=246509&cid=CertificateId```, wobei ```CertificateId``` der **CertificateId**-Wert im Beleg ist.</span><span class="sxs-lookup"><span data-stu-id="774f1-129">To get this certificate, use the URL ```https://go.microsoft.com/fwlink/p/?linkid=246509&cid=CertificateId```, where ```CertificateId``` is the **CertificateId** value in the receipt.</span></span>

<span data-ttu-id="774f1-130">Im Folgenden sehen Sie ein Beispiel für diesen Überprüfungsvorgang.</span><span class="sxs-lookup"><span data-stu-id="774f1-130">Here's an example of that validation process.</span></span> <span data-ttu-id="774f1-131">Dieser Code wird in einer .NET Framework-Konsolenanwendung ausgeführt, die einen Verweis auf die **System.Security**-Assembly enthält.</span><span class="sxs-lookup"><span data-stu-id="774f1-131">This code runs in a .NET Framework console application that includes a reference to the **System.Security** assembly.</span></span>

> [!div class="tabbedCodeSnippets"]
[!code-cs[ReceiptVerificationSample](./code/ReceiptVerificationSample/cs/Program.cs#ReceiptVerificationSample)]

<span id="receipt-descriptions" />

## <a name="element-and-attribute-descriptions-for-a-receipt"></a><span data-ttu-id="774f1-132">Beschreibungen von Elementen und Attributen eines Belegs</span><span class="sxs-lookup"><span data-stu-id="774f1-132">Element and attribute descriptions for a receipt</span></span>

<span data-ttu-id="774f1-133">In diesem Abschnitt werden die Elemente und Attribute in einen Beleg beschrieben.</span><span class="sxs-lookup"><span data-stu-id="774f1-133">This section describes the elements and attributes in a receipt.</span></span>

### <a name="receipt-element"></a><span data-ttu-id="774f1-134">Element „Receipt“</span><span class="sxs-lookup"><span data-stu-id="774f1-134">Receipt element</span></span>

<span data-ttu-id="774f1-135">Das Stammelement dieser Datei ist das Element **Receipt**, das Informationen zu App- und In-App-Käufen enthält.</span><span class="sxs-lookup"><span data-stu-id="774f1-135">The root element of this file is the **Receipt** element, which contains information about app and in-app purchases.</span></span> <span data-ttu-id="774f1-136">Dieses Element enthält die folgenden untergeordneten Elemente.</span><span class="sxs-lookup"><span data-stu-id="774f1-136">This element contains the following child elements.</span></span>

|  <span data-ttu-id="774f1-137">Element</span><span class="sxs-lookup"><span data-stu-id="774f1-137">Element</span></span>  |  <span data-ttu-id="774f1-138">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="774f1-138">Required</span></span>  |  <span data-ttu-id="774f1-139">Menge</span><span class="sxs-lookup"><span data-stu-id="774f1-139">Quantity</span></span>  |  <span data-ttu-id="774f1-140">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="774f1-140">Description</span></span>   |
|-------------|------------|--------|--------|
|  [<span data-ttu-id="774f1-141">AppReceipt</span><span class="sxs-lookup"><span data-stu-id="774f1-141">AppReceipt</span></span>](#appreceipt)  |    <span data-ttu-id="774f1-142">Nein</span><span class="sxs-lookup"><span data-stu-id="774f1-142">No</span></span>        |  <span data-ttu-id="774f1-143">0 oder 1</span><span class="sxs-lookup"><span data-stu-id="774f1-143">0 or 1</span></span>  |  <span data-ttu-id="774f1-144">Enthält Kaufinformationen für die aktuelle App.</span><span class="sxs-lookup"><span data-stu-id="774f1-144">Contains purchase information for the current app.</span></span>            |
|  [<span data-ttu-id="774f1-145">ProductReceipt</span><span class="sxs-lookup"><span data-stu-id="774f1-145">ProductReceipt</span></span>](#productreceipt)  |     <span data-ttu-id="774f1-146">Nein</span><span class="sxs-lookup"><span data-stu-id="774f1-146">No</span></span>       |  <span data-ttu-id="774f1-147">0 oder mehr</span><span class="sxs-lookup"><span data-stu-id="774f1-147">0 or more</span></span>    |   <span data-ttu-id="774f1-148">Enthält Informationen zu einem In-App-Kauf für die aktuelle App.</span><span class="sxs-lookup"><span data-stu-id="774f1-148">Contains information about an in-app purchase for the current app.</span></span>     |
|  <span data-ttu-id="774f1-149">Signature</span><span class="sxs-lookup"><span data-stu-id="774f1-149">Signature</span></span>  |      <span data-ttu-id="774f1-150">Ja</span><span class="sxs-lookup"><span data-stu-id="774f1-150">Yes</span></span>      |  <span data-ttu-id="774f1-151">1</span><span class="sxs-lookup"><span data-stu-id="774f1-151">1</span></span>   |   <span data-ttu-id="774f1-152">Dieses Element ist ein standardmäßiges [XML-DSIG-Konstrukt](http://go.microsoft.com/fwlink/p/?linkid=251093).</span><span class="sxs-lookup"><span data-stu-id="774f1-152">This element is a standard [XML-DSIG construct](http://go.microsoft.com/fwlink/p/?linkid=251093).</span></span> <span data-ttu-id="774f1-153">Es enthält ein **SignatureValue**-Element, das die Signatur enthält, die Sie für die Überprüfung des Belegs verwenden können, und ein **SignedInfo**-Element.</span><span class="sxs-lookup"><span data-stu-id="774f1-153">It contains a **SignatureValue** element, which contains the signature you can use to validate the receipt, and a **SignedInfo** element.</span></span>      |

<span data-ttu-id="774f1-154">**Receipt** hat die folgenden Attribute.</span><span class="sxs-lookup"><span data-stu-id="774f1-154">**Receipt** has the following attributes.</span></span>

|  <span data-ttu-id="774f1-155">Attribut</span><span class="sxs-lookup"><span data-stu-id="774f1-155">Attribute</span></span>  |  <span data-ttu-id="774f1-156">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="774f1-156">Description</span></span>   |
|-------------|-------------------|
|  **<span data-ttu-id="774f1-157">Version</span><span class="sxs-lookup"><span data-stu-id="774f1-157">Version</span></span>**  |    <span data-ttu-id="774f1-158">Die Versionsnummer des Belegs.</span><span class="sxs-lookup"><span data-stu-id="774f1-158">The version number of the receipt.</span></span>            |
|  **<span data-ttu-id="774f1-159">CertificateId</span><span class="sxs-lookup"><span data-stu-id="774f1-159">CertificateId</span></span>**  |     <span data-ttu-id="774f1-160">Der Fingerabdruck des Zertifikats, der für die Signierung des Belegs verwendet wurde.</span><span class="sxs-lookup"><span data-stu-id="774f1-160">The certificate thumbprint used to sign the receipt.</span></span>          |
|  **<span data-ttu-id="774f1-161">ReceiptDate</span><span class="sxs-lookup"><span data-stu-id="774f1-161">ReceiptDate</span></span>**  |    <span data-ttu-id="774f1-162">Das Datum, an dem der Beleg signiert und heruntergeladen wurde.</span><span class="sxs-lookup"><span data-stu-id="774f1-162">Date the receipt was signed and downloaded.</span></span>           |  
|  **<span data-ttu-id="774f1-163">ReceiptDeviceId</span><span class="sxs-lookup"><span data-stu-id="774f1-163">ReceiptDeviceId</span></span>**  |   <span data-ttu-id="774f1-164">Identifiziert das Gerät, das für die Anforderung dieses Belegs verwendet wurde.</span><span class="sxs-lookup"><span data-stu-id="774f1-164">Identifies the device used to request this receipt.</span></span>         |  |

<span id="appreceipt" />

### <a name="appreceipt-element"></a><span data-ttu-id="774f1-165">Element „AppReceipt“</span><span class="sxs-lookup"><span data-stu-id="774f1-165">AppReceipt element</span></span>

<span data-ttu-id="774f1-166">Dieses Element enthält Kaufinformationen für die aktuelle App.</span><span class="sxs-lookup"><span data-stu-id="774f1-166">This element contains purchase information for the current app.</span></span>

<span data-ttu-id="774f1-167">**AppReceipt** hat die folgenden Attribute.</span><span class="sxs-lookup"><span data-stu-id="774f1-167">**AppReceipt** has the following attributes.</span></span>

|  <span data-ttu-id="774f1-168">Attribut</span><span class="sxs-lookup"><span data-stu-id="774f1-168">Attribute</span></span>  |  <span data-ttu-id="774f1-169">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="774f1-169">Description</span></span>   |
|-------------|-------------------|
|  **<span data-ttu-id="774f1-170">Id</span><span class="sxs-lookup"><span data-stu-id="774f1-170">Id</span></span>**  |    <span data-ttu-id="774f1-171">Identifiziert den Kauf.</span><span class="sxs-lookup"><span data-stu-id="774f1-171">Identifies the purchase.</span></span>           |
|  **<span data-ttu-id="774f1-172">AppId</span><span class="sxs-lookup"><span data-stu-id="774f1-172">AppId</span></span>**  |     <span data-ttu-id="774f1-173">Der Paketfamilienname-Wert, den das Betriebssystem für die App verwendet.</span><span class="sxs-lookup"><span data-stu-id="774f1-173">The Package Family Name value that the OS uses for the app.</span></span>           |
|  **<span data-ttu-id="774f1-174">LicenseType</span><span class="sxs-lookup"><span data-stu-id="774f1-174">LicenseType</span></span>**  |    <span data-ttu-id="774f1-175">**Full**, wenn der Benutzer die Vollversion der App gekauft hat.</span><span class="sxs-lookup"><span data-stu-id="774f1-175">**Full**, if the user purchased the full version of the app.</span></span> <span data-ttu-id="774f1-176">**Trial**, wenn der Benutzer eine Testversion der App heruntergeladen hat.</span><span class="sxs-lookup"><span data-stu-id="774f1-176">**Trial**, if the user downloaded a trial version of the app.</span></span>           |  
|  **<span data-ttu-id="774f1-177">PurchaseDate</span><span class="sxs-lookup"><span data-stu-id="774f1-177">PurchaseDate</span></span>**  |    <span data-ttu-id="774f1-178">Das Datum, an dem die App gekauft wurde.</span><span class="sxs-lookup"><span data-stu-id="774f1-178">Date when the app was acquired.</span></span>          |  |

<span id="productreceipt" />

### <a name="productreceipt-element"></a><span data-ttu-id="774f1-179">Element „ProductReceipt“</span><span class="sxs-lookup"><span data-stu-id="774f1-179">ProductReceipt element</span></span>

<span data-ttu-id="774f1-180">Dieses Element enthält Informationen zu einem In-App-Kauf für die aktuelle App.</span><span class="sxs-lookup"><span data-stu-id="774f1-180">This element contains information about an in-app purchase for the current app.</span></span>

<span data-ttu-id="774f1-181">**ProductReceipt** hat die folgenden Attribute.</span><span class="sxs-lookup"><span data-stu-id="774f1-181">**ProductReceipt** has the following attributes.</span></span>

|  <span data-ttu-id="774f1-182">Attribut</span><span class="sxs-lookup"><span data-stu-id="774f1-182">Attribute</span></span>  |  <span data-ttu-id="774f1-183">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="774f1-183">Description</span></span>   |
|-------------|-------------------|
|  **<span data-ttu-id="774f1-184">Id</span><span class="sxs-lookup"><span data-stu-id="774f1-184">Id</span></span>**  |    <span data-ttu-id="774f1-185">Identifiziert den Kauf.</span><span class="sxs-lookup"><span data-stu-id="774f1-185">Identifies the purchase.</span></span>           |
|  **<span data-ttu-id="774f1-186">AppId</span><span class="sxs-lookup"><span data-stu-id="774f1-186">AppId</span></span>**  |     <span data-ttu-id="774f1-187">Identifiziert die App, über die der Benutzer den Kauf durchgeführt hat.</span><span class="sxs-lookup"><span data-stu-id="774f1-187">Identifies the app through which the user made the purchase.</span></span>           |
|  **<span data-ttu-id="774f1-188">ProductId</span><span class="sxs-lookup"><span data-stu-id="774f1-188">ProductId</span></span>**  |     <span data-ttu-id="774f1-189">Identifiziert das gekaufte Produkt.</span><span class="sxs-lookup"><span data-stu-id="774f1-189">Identifies the product purchased.</span></span>           |
|  **<span data-ttu-id="774f1-190">ProductType</span><span class="sxs-lookup"><span data-stu-id="774f1-190">ProductType</span></span>**  |    <span data-ttu-id="774f1-191">Legt den Produkttyp fest.</span><span class="sxs-lookup"><span data-stu-id="774f1-191">Determines the product type.</span></span> <span data-ttu-id="774f1-192">Zurzeit wird nur der Wert **Durable** unterstützt.</span><span class="sxs-lookup"><span data-stu-id="774f1-192">Currently only supports a value of **Durable**.</span></span>          |  
|  **<span data-ttu-id="774f1-193">PurchaseDate</span><span class="sxs-lookup"><span data-stu-id="774f1-193">PurchaseDate</span></span>**  |    <span data-ttu-id="774f1-194">Das Datum, an dem der Kauf erfolgte.</span><span class="sxs-lookup"><span data-stu-id="774f1-194">Date when the purchase occurred.</span></span>          |  |

 

 
