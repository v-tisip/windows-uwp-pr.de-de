---
title: Smartcards
description: In diesem Thema wird erläutert, wie UWP-Apps Smartcards verwenden können, um Benutzer mit sicheren Netzwerkdiensten zu verbinden, einschließlich Informationen für den Zugriff auf physische Smartcardleser, zum Erstellen virtueller Smartcards, zum Kommunizieren mit Smartcards, Authentifizieren von Benutzern, zum Zurücksetzen von Benutzer-PINs und zum Entfernen oder Trennen von Smartcards.
ms.assetid: 86524267-50A0-4567-AE17-35C4B6D24745
author: PatrickFarley
ms.author: pafarley
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, Uwp, Sicherheit
ms.localizationpriority: medium
ms.openlocfilehash: dda2b580a82c72ad2e31c771a9c76f8d770049ec
ms.sourcegitcommit: 2c4daa36fb9fd3e8daa83c2bd0825f3989d24be8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "5519911"
---
# <a name="smart-cards"></a><span data-ttu-id="14327-104">Smartcards</span><span class="sxs-lookup"><span data-stu-id="14327-104">Smart cards</span></span>




<span data-ttu-id="14327-105">In diesem Thema wird erläutert, wie UWP-Apps Smartcards verwenden können, um Benutzer mit sicheren Netzwerkdiensten zu verbinden, einschließlich Informationen für den Zugriff auf physische Smartcardleser, zum Erstellen virtueller Smartcards, zum Kommunizieren mit Smartcards, Authentifizieren von Benutzern, zum Zurücksetzen von Benutzer-PINs und zum Entfernen oder Trennen von Smartcards.</span><span class="sxs-lookup"><span data-stu-id="14327-105">This topic explains how Universal Windows Platform (UWP) apps can use smart cards to connect users to secure network services, including how to access physical smart card readers, create virtual smart cards, communicate with smart cards, authenticate users, reset user PINs, and remove or disconnect smart cards.</span></span> 

## <a name="configure-the-app-manifest"></a><span data-ttu-id="14327-106">Konfigurieren des App-Manifests</span><span class="sxs-lookup"><span data-stu-id="14327-106">Configure the app manifest</span></span>


<span data-ttu-id="14327-107">Bevor Ihre App Benutzer mithilfe von Smartcards oder virtuellen Smartcards authentifizieren kann, müssen Sie die Funktion **Freigegebene Benutzerzertifikate** in der Datei „Package.appxmanifest“ festlegen.</span><span class="sxs-lookup"><span data-stu-id="14327-107">Before your app can authenticate users using smart cards or virtual smart cards, you must set the **Shared User Certificates** capability in the project Package.appxmanifest file.</span></span>

## <a name="access-connected-card-readers-and-smart-cards"></a><span data-ttu-id="14327-108">Zugriff auf verbundene Kartenleser und Smartcards</span><span class="sxs-lookup"><span data-stu-id="14327-108">Access connected card readers and smart cards</span></span>


<span data-ttu-id="14327-109">Sie können Lesegeräte und verbundene Smartcards abrufen, indem Sie die Geräte-ID (in [**DeviceInformation**](https://msdn.microsoft.com/library/windows/apps/br225393) angegeben) an die [**SmartCardReader.FromIdAsync**](https://msdn.microsoft.com/library/windows/apps/dn263890)-Methode übergeben.</span><span class="sxs-lookup"><span data-stu-id="14327-109">You can query for readers and attached smart cards by passing the device ID (specified in [**DeviceInformation**](https://msdn.microsoft.com/library/windows/apps/br225393)) to the [**SmartCardReader.FromIdAsync**](https://msdn.microsoft.com/library/windows/apps/dn263890) method.</span></span> <span data-ttu-id="14327-110">Zum Zugriff auf die derzeit mit dem zurückgegebenen Lesegerät verbundenen Smartcards rufen Sie [**SmartCardReader.FindAllCardsAsync**](https://msdn.microsoft.com/library/windows/apps/dn263887) auf.</span><span class="sxs-lookup"><span data-stu-id="14327-110">To access the smart cards currently attached to the returned reader device, call [**SmartCardReader.FindAllCardsAsync**](https://msdn.microsoft.com/library/windows/apps/dn263887).</span></span>

```cs
string selector = SmartCardReader.GetDeviceSelector();
DeviceInformationCollection devices =
    await DeviceInformation.FindAllAsync(selector);

foreach (DeviceInformation device in devices)
{
    SmartCardReader reader =
        await SmartCardReader.FromIdAsync(device.Id);

    // For each reader, we want to find all the cards associated
    // with it.  Then we will create a SmartCardListItem for
    // each (reader, card) pair.
    IReadOnlyList<SmartCard> cards =
        await reader.FindAllCardsAsync();
}
```

<span data-ttu-id="14327-111">Zudem sollten Sie der App ermöglichen, [**CardAdded**](https://msdn.microsoft.com/library/windows/apps/dn263866)-Ereignisse zu beobachten, indem eine Methode zum Behandeln des App-Verhaltens beim Einsetzen einer Karte implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="14327-111">You should also enable your app to observe for [**CardAdded**](https://msdn.microsoft.com/library/windows/apps/dn263866) events by implementing a method to handle app behavior on card insertion.</span></span>

```cs
private void reader_CardAdded(SmartCardReader sender, CardAddedEventArgs args)
{
  // A card has been inserted into the sender SmartCardReader.
}
```

<span data-ttu-id="14327-112">Anschließend können Sie jedes zurückgegebene [**SmartCard**](https://msdn.microsoft.com/library/windows/apps/dn297565)-Objekt an [**SmartCardProvisioning**](https://msdn.microsoft.com/library/windows/apps/dn263801) übergeben, um auf die Methoden zuzugreifen, die Ihrer App den Zugriff auf und die Anpassung ihrer Konfiguration ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="14327-112">You can then pass each returned [**SmartCard**](https://msdn.microsoft.com/library/windows/apps/dn297565) object to [**SmartCardProvisioning**](https://msdn.microsoft.com/library/windows/apps/dn263801) to access the methods that allow your app to access and customize its configuration.</span></span>

## <a name="create-a-virtual-smart-card"></a><span data-ttu-id="14327-113">Erstellen einer virtuellen Smartcard</span><span class="sxs-lookup"><span data-stu-id="14327-113">Create a virtual smart card</span></span>


<span data-ttu-id="14327-114">Zum Erstellen einer virtuellen Smartcard mithilfe von [**SmartCardProvisioning**](https://msdn.microsoft.com/library/windows/apps/dn263801) muss Ihre App zunächst einen Anzeigenamen, einen Administratorschlüssel und eine [**SmartCardPinPolicy**](https://msdn.microsoft.com/library/windows/apps/dn297642) bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="14327-114">To create a virtual smart card using [**SmartCardProvisioning**](https://msdn.microsoft.com/library/windows/apps/dn263801), your app will first need to provide a friendly name, an admin key, and a [**SmartCardPinPolicy**](https://msdn.microsoft.com/library/windows/apps/dn297642).</span></span> <span data-ttu-id="14327-115">Der Anzeigename wird der App in der Regel bereitgestellt, die App muss jedoch trotzdem einen Administratorschlüssel bereitstellen und eine Instanz der aktuellen **SmartCardPinPolicy** generieren, bevor alle drei Werte an [**RequestVirtualSmartCardCreationAsync**](https://msdn.microsoft.com/library/windows/apps/dn263830) übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="14327-115">The friendly name is generally something provided to the app, but your app will still need to provide an admin key and generate an instance of the current **SmartCardPinPolicy** before passing all three values to [**RequestVirtualSmartCardCreationAsync**](https://msdn.microsoft.com/library/windows/apps/dn263830).</span></span>

1.  <span data-ttu-id="14327-116">Erstellen einer neuen Instanz einer [**SmartCardPinPolicy**](https://msdn.microsoft.com/library/windows/apps/dn297642)</span><span class="sxs-lookup"><span data-stu-id="14327-116">Create a new instance of a [**SmartCardPinPolicy**](https://msdn.microsoft.com/library/windows/apps/dn297642)</span></span>
2.  <span data-ttu-id="14327-117">Generieren Sie den Administratorschlüsselwert durch Aufrufen von [**CryptographicBuffer.GenerateRandom**](https://msdn.microsoft.com/library/windows/apps/br241392) für den vom Dienst oder Verwaltungstool bereitgestellten Administratorschlüsselwert.</span><span class="sxs-lookup"><span data-stu-id="14327-117">Generate the admin key value by calling [**CryptographicBuffer.GenerateRandom**](https://msdn.microsoft.com/library/windows/apps/br241392) on the admin key value provided by the service or management tool.</span></span>
3.  <span data-ttu-id="14327-118">Übergeben Sie diese Werte zusammen mit der *FriendlyNameText*-Zeichenfolge an [**RequestVirtualSmartCardCreationAsync**](https://msdn.microsoft.com/library/windows/apps/dn263830).</span><span class="sxs-lookup"><span data-stu-id="14327-118">Pass these values along with the *FriendlyNameText* string to [**RequestVirtualSmartCardCreationAsync**](https://msdn.microsoft.com/library/windows/apps/dn263830).</span></span>

```cs
SmartCardPinPolicy pinPolicy = new SmartCardPinPolicy();
pinPolicy.MinLength = 6;

IBuffer adminkey = CryptographicBuffer.GenerateRandom(24);

SmartCardProvisioning provisioning = await
     SmartCardProvisioning.RequestVirtualSmartCardCreationAsync(
          "Card friendly name",
          adminkey,
          pinPolicy);
```

<span data-ttu-id="14327-119">Sobald [**RequestVirtualSmartCardCreationAsync**](https://msdn.microsoft.com/library/windows/apps/dn263830) das zugehörige [**SmartCardProvisioning**](https://msdn.microsoft.com/library/windows/apps/dn263801)-Objekt zurückgegeben hat, wird die virtuelle Smartcard bereitgestellt und kann verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="14327-119">Once [**RequestVirtualSmartCardCreationAsync**](https://msdn.microsoft.com/library/windows/apps/dn263830) has returned the associated [**SmartCardProvisioning**](https://msdn.microsoft.com/library/windows/apps/dn263801) object, the virtual smart card is provisioned and ready for use.</span></span>

## <a name="handle-authentication-challenges"></a><span data-ttu-id="14327-120">Behandeln von Authentifizierungsaufforderungen</span><span class="sxs-lookup"><span data-stu-id="14327-120">Handle authentication challenges</span></span>


<span data-ttu-id="14327-121">Für die Authentifizierung mit Smartcards oder virtuellen Smartcards muss Ihre App das Verhalten bereitstellen, um Aufforderungen zwischen den auf der Karte gespeicherten Administratorschlüsseldaten und den vom Authentifizierungsserver oder Verwaltungstool verwalteten Administratorschlüsseldaten abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="14327-121">To authenticate with smart cards or virtual smart cards, your app must provide the behavior to complete challenges between the admin key data stored on the card, and the admin key data maintained by the authentication server or management tool.</span></span>

<span data-ttu-id="14327-122">Der folgende Code ist ein Beispiel für die Unterstützung der Smartcard-Authentifizierung für Dienste oder die Änderung von physischen oder virtuellen Kartendetails.</span><span class="sxs-lookup"><span data-stu-id="14327-122">The following code shows how to support smart card authentication for services or modification of physical or virtual card details.</span></span> <span data-ttu-id="14327-123">Wenn die mithilfe des Administratorschlüssels auf der Karte generierten Daten ("challenge") mit den vom Server oder Verwaltungstool bereitgestellten Daten ("adminkey") übereinstimmen, ist die Authentifizierung erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="14327-123">If the data generated using the admin key on the card ("challenge") is the same as the admin key data provided by the server or management tool ("adminkey"), authentication is successful.</span></span>

```cs
static class ChallengeResponseAlgorithm
{
    public static IBuffer CalculateResponse(IBuffer challenge, IBuffer adminkey)
    {
        if (challenge == null)
            throw new ArgumentNullException("challenge");
        if (adminkey == null)
            throw new ArgumentNullException("adminkey");

        SymmetricKeyAlgorithmProvider objAlg = SymmetricKeyAlgorithmProvider.OpenAlgorithm(SymmetricAlgorithmNames.TripleDesCbc);
        var symmetricKey = objAlg.CreateSymmetricKey(adminkey);
        var buffEncrypted = CryptographicEngine.Encrypt(symmetricKey, challenge, null);
        return buffEncrypted;
    }
}
```

<span data-ttu-id="14327-124">Auf diesen Code wird im gesamten verbleibenden Teil dieses Themas verwiesen, wenn erläutert wird, wie eine Authentifizierungsaktion abgeschlossen und Änderungen an Informationen zu Smartcards und virtuellen Smartcards übernommen werden.</span><span class="sxs-lookup"><span data-stu-id="14327-124">You will see this code referenced throughout the remainder of this topic was we review how to complete an authentication action, and how to apply changes to smart card and virtual smart card information.</span></span>

## <a name="verify-smart-card-or-virtual-smart-card-authentication-response"></a><span data-ttu-id="14327-125">Überprüfen der Authentifizierungsantwort von Smartcards oder virtuellen Smartcards</span><span class="sxs-lookup"><span data-stu-id="14327-125">Verify smart card or virtual smart card authentication response</span></span>


<span data-ttu-id="14327-126">Nachdem wir die Logik für Authentifizierungsaufforderungen definiert haben, können wir jetzt mit dem Leser kommunizieren, um auf die Smartcard oder alternativ auf eine virtuelle Smartcard zuzugreifen, um die Authentifizierung durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="14327-126">Now that we have the logic for authentication challenges defined, we can communicate with the reader to access the smart card, or alternatively, access a virtual smart card for authentication.</span></span>

1.  <span data-ttu-id="14327-127">Rufen Sie zum Starten der Aufforderung [**GetChallengeContextAsync**](https://msdn.microsoft.com/library/windows/apps/dn263811) vom [**SmartCardProvisioning**](https://msdn.microsoft.com/library/windows/apps/dn263801)-Objekt auf, das der Smartcard zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="14327-127">To begin the challenge, call [**GetChallengeContextAsync**](https://msdn.microsoft.com/library/windows/apps/dn263811) from the [**SmartCardProvisioning**](https://msdn.microsoft.com/library/windows/apps/dn263801) object associated with the smart card.</span></span> <span data-ttu-id="14327-128">Dadurch wird eine Instanz von [**SmartCardChallengeContext**](https://msdn.microsoft.com/library/windows/apps/dn297570) erstellt, die den [**Challenge**](https://msdn.microsoft.com/library/windows/apps/dn297578)-Wert der Karte enthält.</span><span class="sxs-lookup"><span data-stu-id="14327-128">This will generate an instance of [**SmartCardChallengeContext**](https://msdn.microsoft.com/library/windows/apps/dn297570), which contains the card's [**Challenge**](https://msdn.microsoft.com/library/windows/apps/dn297578) value.</span></span>

2.  <span data-ttu-id="14327-129">Übergeben Sie als Nächstes den Aufforderungswert der Karte und den vom Dienst oder Verwaltungstool bereitgestellten Administratorschlüssel an das **ChallengeResponseAlgorithm**-Element, das wir im vorhergehenden Beispiel definiert haben.</span><span class="sxs-lookup"><span data-stu-id="14327-129">Next, pass the card's challenge value and the admin key provided by the service or management tool to the **ChallengeResponseAlgorithm** that we defined in the previous example.</span></span>

3.  <span data-ttu-id="14327-130">[**VerifyResponseAsync**](https://msdn.microsoft.com/library/windows/apps/dn297627) gibt bei erfolgreicher Authentifizierung den Wert **true** zurück.</span><span class="sxs-lookup"><span data-stu-id="14327-130">[**VerifyResponseAsync**](https://msdn.microsoft.com/library/windows/apps/dn297627) will return **true** if authentication is successful.</span></span>

```cs
bool verifyResult = false;
SmartCard card = await rootPage.GetSmartCard();
SmartCardProvisioning provisioning =
    await SmartCardProvisioning.FromSmartCardAsync(card);

using (SmartCardChallengeContext context =
       await provisioning.GetChallengeContextAsync())
{
    IBuffer response = ChallengeResponseAlgorithm.CalculateResponse(
        context.Challenge,
        rootPage.AdminKey);

    verifyResult = await context.VerifyResponseAsync(response);
}
```

## <a name="change-or-reset-a-user-pin"></a><span data-ttu-id="14327-131">Ändern oder Zurücksetzen einer Benutzer-PIN</span><span class="sxs-lookup"><span data-stu-id="14327-131">Change or reset a user PIN</span></span>


<span data-ttu-id="14327-132">So ändern Sie die einer Smartcard zugeordnete PIN:</span><span class="sxs-lookup"><span data-stu-id="14327-132">To change the PIN associated with a smart card:</span></span>

1.  <span data-ttu-id="14327-133">Greifen Sie auf die Karte zu, und generieren Sie das zugehörige [**SmartCardProvisioning**](https://msdn.microsoft.com/library/windows/apps/dn263801)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="14327-133">Access the card and generate the associated [**SmartCardProvisioning**](https://msdn.microsoft.com/library/windows/apps/dn263801) object.</span></span>
2.  <span data-ttu-id="14327-134">Rufen Sie [**RequestPinChangeAsync**](https://msdn.microsoft.com/library/windows/apps/dn263823) auf, um eine Benutzeroberfläche anzuzeigen, auf der der Benutzer diesen Vorgang abschließen kann.</span><span class="sxs-lookup"><span data-stu-id="14327-134">Call [**RequestPinChangeAsync**](https://msdn.microsoft.com/library/windows/apps/dn263823) to display a UI to the user to complete this operation.</span></span>
3.  <span data-ttu-id="14327-135">Wenn die PIN erfolgreich geändert wurde, gibt der Aufruf den Wert **true** zurück.</span><span class="sxs-lookup"><span data-stu-id="14327-135">If the PIN was successfully changed the call will return **true**.</span></span>

```cs
SmartCardProvisioning provisioning =
    await SmartCardProvisioning.FromSmartCardAsync(card);

bool result = await provisioning.RequestPinChangeAsync();
```

<span data-ttu-id="14327-136">So fordern Sie das Zurücksetzen einer PIN an:</span><span class="sxs-lookup"><span data-stu-id="14327-136">To request a PIN reset:</span></span>

1.  <span data-ttu-id="14327-137">Rufen Sie [**RequestPinResetAsync**](https://msdn.microsoft.com/library/windows/apps/dn263825) auf, um den Vorgang zu initiieren.</span><span class="sxs-lookup"><span data-stu-id="14327-137">Call [**RequestPinResetAsync**](https://msdn.microsoft.com/library/windows/apps/dn263825) to initiate the operation.</span></span> <span data-ttu-id="14327-138">Dieser Aufruf enthält eine [**SmartCardPinResetHandler**](https://msdn.microsoft.com/library/windows/apps/dn297701)-Methode, die die Smartcard und die Anforderung der PIN-Zurücksetzung darstellt.</span><span class="sxs-lookup"><span data-stu-id="14327-138">This call includes a [**SmartCardPinResetHandler**](https://msdn.microsoft.com/library/windows/apps/dn297701) method that represents the smart card and the pin reset request.</span></span>
2.  <span data-ttu-id="14327-139">[**SmartCardPinResetHandler**](https://msdn.microsoft.com/library/windows/apps/dn297701) stellt Informationen bereit, die mit dem in einen [**SmartCardPinResetDeferral**](https://msdn.microsoft.com/library/windows/apps/dn297693)-Aufruf eingeschlossenen **ChallengeResponseAlgorithm**-Element den Aufforderungswert der Karte und den vom Dienst oder Verwaltungstool bereitgestellten Administratorschlüssel zur Authentifizierung der Anforderung vergleichen.</span><span class="sxs-lookup"><span data-stu-id="14327-139">[**SmartCardPinResetHandler**](https://msdn.microsoft.com/library/windows/apps/dn297701) provides information that our **ChallengeResponseAlgorithm**, wrapped in a [**SmartCardPinResetDeferral**](https://msdn.microsoft.com/library/windows/apps/dn297693) call, uses to compare the card's challenge value and the admin key provided by the service or management tool to authenticate the request.</span></span>

3.  <span data-ttu-id="14327-140">Bei einer erfolgreichen Aufforderung ist der [**RequestPinResetAsync**](https://msdn.microsoft.com/library/windows/apps/dn263825)-Aufruf abgeschlossen; bei einem erfolgreichen Zurücksetzen der PIN wird der Wert **true** zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="14327-140">If the challenge is successful, the [**RequestPinResetAsync**](https://msdn.microsoft.com/library/windows/apps/dn263825) call is completed; returning **true** if the PIN was successfully reset.</span></span>

```cs
SmartCardProvisioning provisioning =
    await SmartCardProvisioning.FromSmartCardAsync(card);

bool result = await provisioning.RequestPinResetAsync(
    (pinResetSender, request) =>
    {
        SmartCardPinResetDeferral deferral =
            request.GetDeferral();

        try
        {
            IBuffer response =
                ChallengeResponseAlgorithm.CalculateResponse(
                    request.Challenge,
                    rootPage.AdminKey);
            request.SetResponse(response);
        }
        finally
        {
            deferral.Complete();
        }
    });
}
```

## <a name="remove-a-smart-card-or-virtual-smart-card"></a><span data-ttu-id="14327-141">Entfernen einer Smartcard oder virtuellen Smartcard</span><span class="sxs-lookup"><span data-stu-id="14327-141">Remove a smart card or virtual smart card</span></span>


<span data-ttu-id="14327-142">Wenn eine physische Smartcard entfernt wird, wird beim Löschen der Karte ein [**CardRemoved**](https://msdn.microsoft.com/library/windows/apps/dn263875)-Ereignis ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="14327-142">When a physical smart card is removed a [**CardRemoved**](https://msdn.microsoft.com/library/windows/apps/dn263875) event will fire when the card is deleted.</span></span>

<span data-ttu-id="14327-143">Ordnen Sie das Auslösen dieses Ereignisses mithilfe der Methode, die das Verhalten Ihrer App beim Entfernen einer Karte oder eines Lesers definiert, dem Kartenleser als Ereignishandler zu.</span><span class="sxs-lookup"><span data-stu-id="14327-143">Associate the firing of this event with the card reader with the method that defines your app's behavior on card or reader removal as an event handler.</span></span> <span data-ttu-id="14327-144">Bei diesem Verhalten kann es sich z.B. einfach um eine Benachrichtigung des Benutzers handeln, dass die Karte entfernt wurde.</span><span class="sxs-lookup"><span data-stu-id="14327-144">This behavior can be something as simply as providing notification to the user that the card was removed.</span></span>

```cs
reader = card.Reader;
reader.CardRemoved += HandleCardRemoved;
```

<span data-ttu-id="14327-145">Das Entfernen einer virtuellen Smartcard wird programmgesteuert behandelt, indem zuerst die Karte abgerufen und anschließend [**RequestVirtualSmartCardDeletionAsync**](https://msdn.microsoft.com/library/windows/apps/dn263850) aus dem zurückgegebenen [**SmartCardProvisioning**](https://msdn.microsoft.com/library/windows/apps/dn263801)-Objekt aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="14327-145">The removal of a virtual smart card is handled programmatically by first retrieving the card and then calling [**RequestVirtualSmartCardDeletionAsync**](https://msdn.microsoft.com/library/windows/apps/dn263850) from the [**SmartCardProvisioning**](https://msdn.microsoft.com/library/windows/apps/dn263801) returned object.</span></span>

```cs
bool result = await SmartCardProvisioning
    .RequestVirtualSmartCardDeletionAsync(card);
```