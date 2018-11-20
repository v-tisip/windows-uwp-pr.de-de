---
author: normesta
title: Anfordern eines Kartenauthentifizierungsschlüssels
description: Ihre universelle Windows-App muss authentifiziert werden, bevor sie die MapControl-Klasse und Kartendienste im Windows.Services.Maps-Namespace verwenden kann.
ms.assetid: 13B400D7-E13F-4F07-ACC3-9C34087F0F73
ms.author: normesta
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP, Kartenauthentifizierungsschlüssel, Kartensteuerelement
ms.localizationpriority: medium
ms.openlocfilehash: c42255ec42432d0674533492e141c4a48f3bb9ff
ms.sourcegitcommit: cbe7cf620622a5e4df7414f9e38dfecec1cfca99
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "7441452"
---
# <a name="request-a-maps-authentication-key"></a><span data-ttu-id="90e40-104">Anfordern eines Kartenauthentifizierungsschlüssels</span><span class="sxs-lookup"><span data-stu-id="90e40-104">Request a maps authentication key</span></span>




<span data-ttu-id="90e40-105">Ihre [universelle Windows-App](https://msdn.microsoft.com/library/windows/apps/dn894631) muss authentifiziert werden, bevor sie die [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004)-Klasse und Kartendienste im [**Windows.Services.Maps**](https://msdn.microsoft.com/library/windows/apps/dn636979)-Namespace verwenden kann.</span><span class="sxs-lookup"><span data-stu-id="90e40-105">Your [Universal Windows app](https://msdn.microsoft.com/library/windows/apps/dn894631) must be authenticated before it can use the [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) and map services in the [**Windows.Services.Maps**](https://msdn.microsoft.com/library/windows/apps/dn636979) namespace.</span></span> <span data-ttu-id="90e40-106">Zum Authentifizieren Ihrer App müssen Sie einen Kartenauthentifizierungsschlüssel angeben.</span><span class="sxs-lookup"><span data-stu-id="90e40-106">To authenticate your app, you must specify a maps authentication key.</span></span> <span data-ttu-id="90e40-107">In diesem Thema wird beschrieben, wie Sie einen Kartenauthentifizierungsschlüssel vom [Bing Maps Developer Center](https://www.bingmapsportal.com/) anfordern und Ihrer App hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="90e40-107">This topic describes how to request a maps authentication key from the [Bing Maps Developer Center](https://www.bingmapsportal.com/) and add it to your app.</span></span>

<span data-ttu-id="90e40-108">**Tipp** Um mehr über die Verwendung von Karten in Ihrer App zu erfahren, können Sie das folgende Beispiel aus den [API-Beispielen für die Universelle Windows-Plattform](http://go.microsoft.com/fwlink/p/?LinkId=619979) auf GitHub herunterladen.</span><span class="sxs-lookup"><span data-stu-id="90e40-108">**Tip** To learn more about using maps in your app, download the following sample from the [Windows-universal-samples repo](http://go.microsoft.com/fwlink/p/?LinkId=619979) on GitHub:</span></span>

-   [<span data-ttu-id="90e40-109">Kartenbeispiel für die Universelle Windows-Plattform (UWP)</span><span class="sxs-lookup"><span data-stu-id="90e40-109">Universal Windows Platform (UWP) map sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619977)

## <a name="get-a-key"></a><span data-ttu-id="90e40-110">Abrufen eines Schlüssels</span><span class="sxs-lookup"><span data-stu-id="90e40-110">Get a key</span></span>


<span data-ttu-id="90e40-111">Erstellen und verwalten Sie Kartenauthentifizierungsschlüssel für Ihre universellen Windows-Apps im [Bing Maps Developer Center](https://www.bingmapsportal.com/).</span><span class="sxs-lookup"><span data-stu-id="90e40-111">Create and manage map authentication keys for your Universal Windows apps using the [Bing Maps Developer Center](https://www.bingmapsportal.com/).</span></span>

<span data-ttu-id="90e40-112">So erstellen Sie einen neuen Schlüssel</span><span class="sxs-lookup"><span data-stu-id="90e40-112">To create a new key</span></span>

1.  <span data-ttu-id="90e40-113">Navigieren Sie in Ihrem Browser zum Bing Maps Developer Center ([https://www.bingmapsportal.com](https://www.bingmapsportal.com/)).</span><span class="sxs-lookup"><span data-stu-id="90e40-113">In your browser, navigate to the Bing Maps Developer Center ([https://www.bingmapsportal.com](https://www.bingmapsportal.com/)).</span></span>

2.  <span data-ttu-id="90e40-114">Wenn Sie zum Anmelden aufgefordert werden, geben Sie Ihre Microsoft-Kontoinformationen ein, und klicken Sie auf **Anmelden**.</span><span class="sxs-lookup"><span data-stu-id="90e40-114">If you are asked to sign in, enter your Microsoft account and click **Sign in**.</span></span>

3.  <span data-ttu-id="90e40-115">Wählen Sie das Konto, das mit Ihrem Bing Karten-Konto verknüpft werden soll.</span><span class="sxs-lookup"><span data-stu-id="90e40-115">Choose the account to associate with your Bing Maps account.</span></span> <span data-ttu-id="90e40-116">Wenn Sie Ihr Microsoft-Konto verwenden möchten, klicken Sie auf **Ja**.</span><span class="sxs-lookup"><span data-stu-id="90e40-116">If you want to use your Microsoft account, click **Yes**.</span></span> <span data-ttu-id="90e40-117">Andernfalls klicken Sie auf die Option zum **Anmelden mit einem anderen Konto**.</span><span class="sxs-lookup"><span data-stu-id="90e40-117">Otherwise, click **Sign in with another account**.</span></span>

4.  <span data-ttu-id="90e40-118">Wenn Sie noch kein Bing Karten-Konto besitzen, erstellen Sie ein neues Bing Karten-Konto.</span><span class="sxs-lookup"><span data-stu-id="90e40-118">If you don't already have a Bing Maps account, create a new Bing Maps account.</span></span> <span data-ttu-id="90e40-119">Geben Sie **Kontoname**, **Kontaktname**, **Firmenname**, **E-Mail-Adresse** und **Telefonnummer** ein.</span><span class="sxs-lookup"><span data-stu-id="90e40-119">Enter the **Account Name**, **Contact Name**, **Company Name**, **Email Address**, and **Phone Number**.</span></span> <span data-ttu-id="90e40-120">Akzeptieren Sie die Nutzungsbedingungen, und klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="90e40-120">After accepting the terms of use, click **Create**.</span></span>

5.  <span data-ttu-id="90e40-121">Klicken Sie im Menü **Mein Konto** auf **Eigene Schlüssel**.</span><span class="sxs-lookup"><span data-stu-id="90e40-121">Under the **My account** menu, click **My Keys**.</span></span>

6.  <span data-ttu-id="90e40-122">Wenn Sie bereits einen Schlüssel erstellt haben, klicken Sie auf den Link, um einen neuen Schlüssel zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="90e40-122">If you have previously created a key, click on the link to create a new key.</span></span> <span data-ttu-id="90e40-123">“Andernfalls fahren Sie mit dem Formular „Schlüssel erstellen” fort.</span><span class="sxs-lookup"><span data-stu-id="90e40-123">Otherwise proceed to the Create Key form.</span></span>

7.  <span data-ttu-id="90e40-124">Füllen Sie das Formular **Schlüssel erstellen** aus, und klicken Sie dann auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="90e40-124">Complete the **Create Key** form and then click **Create**.</span></span>

    -   <span data-ttu-id="90e40-125">**Anwendungsname:** Der Name Ihrer Anwendung.</span><span class="sxs-lookup"><span data-stu-id="90e40-125">**Application name:** The name of your application.</span></span>
    -   <span data-ttu-id="90e40-126">**Anwendungs-URL (optional):** Die URL Ihrer Anwendung.</span><span class="sxs-lookup"><span data-stu-id="90e40-126">**Application URL (optional):** The URL of your application.</span></span>
    -   <span data-ttu-id="90e40-127">**Schlüsseltyp:** Wählen Sie **Basic** oder **Enterprise** aus.</span><span class="sxs-lookup"><span data-stu-id="90e40-127">**Key type:** Select **Basic** or **Enterprise**.</span></span>
    -   <span data-ttu-id="90e40-128">**Anwendungstyp:** Wählen Sie **Universelle Windows-App** für die Verwendung in Ihrer universellen Windows-App aus.</span><span class="sxs-lookup"><span data-stu-id="90e40-128">**Application type:** Select **Universal Windows App** for use in your Universal Windows app.</span></span>

    <span data-ttu-id="90e40-129">So sieht das Formular aus.</span><span class="sxs-lookup"><span data-stu-id="90e40-129">This is an example of what the form looks like.</span></span>

    ![Beispiel des Formulars „Schlüssel erstellen“.](images/createkeydialog.png)

8.  <span data-ttu-id="90e40-131">Nachdem Sie auf **Erstellen** geklickt haben, wird der neue Schlüssel unterhalb des Formulars **Schlüssel erstellen** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="90e40-131">After you click **Create**, the new key appears below the **Create Key** form.</span></span> <span data-ttu-id="90e40-132">Kopieren Sie ihn an einen sicheren Ort, oder fügen Sie ihn sofort wie im nächsten Schritt beschrieben Ihrer App hinzu.</span><span class="sxs-lookup"><span data-stu-id="90e40-132">Copy it to a safe place or immediately add it to your app, as described in the next step.</span></span>

## <a name="add-the-key-to-your-app"></a><span data-ttu-id="90e40-133">Hinzufügen des Schlüssels zur App</span><span class="sxs-lookup"><span data-stu-id="90e40-133">Add the key to your app</span></span>


<span data-ttu-id="90e40-134">Der Kartenauthentifizierungsschlüssel ist erforderlich, um die [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004)-Klasse und Kartendienste ([**Windows.Services.Maps**](https://msdn.microsoft.com/library/windows/apps/dn636979)) in Ihrer universellenWindows-App zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="90e40-134">The map authentication key is required to use the [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004) and map services ([**Windows.Services.Maps**](https://msdn.microsoft.com/library/windows/apps/dn636979)) in your Universal Windows app.</span></span> <span data-ttu-id="90e40-135">Fügen Sie ihn ggf. dem Kartensteuerelement und Kartendienstobjekten hinzu.</span><span class="sxs-lookup"><span data-stu-id="90e40-135">Add it to the map control and map service objects, as applicable.</span></span>

### <a name="to-add-the-key-to-a-map-control"></a><span data-ttu-id="90e40-136">So fügen Sie den Schlüssel einem Kartensteuerelement hinzu</span><span class="sxs-lookup"><span data-stu-id="90e40-136">To add the key to a map control</span></span>

<span data-ttu-id="90e40-137">Setzen Sie zum Authentifizieren der [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004)-Klasse die [**MapServiceToken**](https://msdn.microsoft.com/library/windows/apps/dn637036)-Eigenschaft auf den Wert des Authentifizierungsschlüssels.</span><span class="sxs-lookup"><span data-stu-id="90e40-137">To authenticate the [**MapControl**](https://msdn.microsoft.com/library/windows/apps/dn637004), set the [**MapServiceToken**](https://msdn.microsoft.com/library/windows/apps/dn637036) property to the authentication key value.</span></span> <span data-ttu-id="90e40-138">Sie können diese Eigenschaft je nach Ihren Einstellungen im Code oder im XAML-Markup festlegen.</span><span class="sxs-lookup"><span data-stu-id="90e40-138">You can set this property in code or in XAML markup, depending on your preferences.</span></span> <span data-ttu-id="90e40-139">Weitere Informationen zur Verwendung der **MapControl**-Klasse finden Sie unter [Anzeigen von Karten mit 2D-, 3D- und Streetside-Ansichten](display-maps.md).</span><span class="sxs-lookup"><span data-stu-id="90e40-139">For more info about using the **MapControl**, see [Display maps with 2D, 3D, and Streetside views](display-maps.md).</span></span>

-   <span data-ttu-id="90e40-140">In diesem Beispiel wird die **MapServiceToken**-Eingeschaft auf den Wert des Authentifizierungsschlüssels im Code gesetzt.</span><span class="sxs-lookup"><span data-stu-id="90e40-140">This example sets the **MapServiceToken** to the value of the authentication key in code.</span></span>

    ```cs
    MapControl1.MapServiceToken = "abcdef-abcdefghijklmno";
    ```

-   <span data-ttu-id="90e40-141">In diesem Beispiel wird die **MapServiceToken**-Eingeschaft auf den Wert des Authentifizierungsschlüssels im XAML-Markup gesetzt.</span><span class="sxs-lookup"><span data-stu-id="90e40-141">This example sets the **MapServiceToken** to the value of the authentication key in XAML markup.</span></span>

    ```xml
    <Maps:MapControl x:Name="MapControl1" MapServiceToken="abcdef-abcdefghijklmno"/>
    ```

### <a name="to-add-the-key-to-map-services"></a><span data-ttu-id="90e40-142">So fügen Sie den Schlüssel Kartendiensten hinzu</span><span class="sxs-lookup"><span data-stu-id="90e40-142">To add the key to map services</span></span>

<span data-ttu-id="90e40-143">Um Dienste im [**Windows.Services.Maps**](https://msdn.microsoft.com/library/windows/apps/dn636979)-Namespace zu verwenden, setzen Sie die [**ServiceToken**](https://msdn.microsoft.com/library/windows/apps/dn636977)-Eigenschaft auf den Wert des Authentifizierungsschlüssels.</span><span class="sxs-lookup"><span data-stu-id="90e40-143">To use services in the [**Windows.Services.Maps**](https://msdn.microsoft.com/library/windows/apps/dn636979) namespace, set the [**ServiceToken**](https://msdn.microsoft.com/library/windows/apps/dn636977) property to the authentication key value.</span></span> <span data-ttu-id="90e40-144">Weitere Informationen zur Verwendung von Kartendiensten finden Sie unter [Anzeigen von Routen und Wegbeschreibungen auf einer Karte](routes-and-directions.md) und [Durchführen der Geocodierung und umgekehrten Geocodierung](geocoding.md).</span><span class="sxs-lookup"><span data-stu-id="90e40-144">For more info about using map services, see [Display routes and directions](routes-and-directions.md) and [Perform geocoding and reverse geocoding](geocoding.md).</span></span>

-   <span data-ttu-id="90e40-145">In diesem Beispiel wird die **ServiceToken**-Eingeschaft auf den Wert des Authentifizierungsschlüssels im Code gesetzt.</span><span class="sxs-lookup"><span data-stu-id="90e40-145">This example sets the **ServiceToken** to the value of the authentication key in code.</span></span>

    ```cs
    MapService.ServiceToken = "abcdef-abcdefghijklmno";
    ```

## <a name="related-topics"></a><span data-ttu-id="90e40-146">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="90e40-146">Related topics</span></span>

* [<span data-ttu-id="90e40-147">Bing Maps Developer Center</span><span class="sxs-lookup"><span data-stu-id="90e40-147">Bing Maps Developer Center</span></span>](https://www.bingmapsportal.com/)
* [<span data-ttu-id="90e40-148">Beispiel für UWP-Karte</span><span class="sxs-lookup"><span data-stu-id="90e40-148">UWP map sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619977)
* [<span data-ttu-id="90e40-149">Entwurfsrichtlinien für Karten</span><span class="sxs-lookup"><span data-stu-id="90e40-149">Design guidelines for maps</span></span>](https://msdn.microsoft.com/library/windows/apps/dn596102)
* [<span data-ttu-id="90e40-150">Build 2015-Video: Nutzen von Karten und Ortung über Telefon, Tablet und PC in Ihren Windows-Apps</span><span class="sxs-lookup"><span data-stu-id="90e40-150">Build 2015 video: Leveraging Maps and Location Across Phone, Tablet, and PC in Your Windows Apps</span></span>](https://channel9.msdn.com/Events/Build/2015/2-757)
* [<span data-ttu-id="90e40-151">Beispiel für eine UWP-App mit Verkehrsinformationen</span><span class="sxs-lookup"><span data-stu-id="90e40-151">UWP traffic app sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=619982)
