---
author: mijacobs
Description: A tile is an app's representation on the Start menu. Every app has a tile. When you create a new Universal Windows Platform (UWP) app project in Microsoft Visual Studio, it includes a default tile that displays your app's name and logo.
title: Kacheln
ms.assetid: 09C7E1B1-F78D-4659-8086-2E428E797653
label: Tiles
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: f4388b67335bce497987ab22e3b281cf86e029af
ms.sourcegitcommit: 71e8eae5c077a7740e5606298951bb78fc42b22c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6661718"
---
# <a name="tiles-for-uwp-apps"></a><span data-ttu-id="a5848-103">Kacheln für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="a5848-103">Tiles for UWP apps</span></span>

 

<span data-ttu-id="a5848-104">Eine *Kachel* ist die Darstellung einer App im Startmenü.</span><span class="sxs-lookup"><span data-stu-id="a5848-104">A *tile* is an app's representation on the Start menu.</span></span> <span data-ttu-id="a5848-105">Jede App verfügt über eine Kachel.</span><span class="sxs-lookup"><span data-stu-id="a5848-105">Every app has a tile.</span></span> <span data-ttu-id="a5848-106">Wenn Sie ein neues UWP-App-Projekt in Microsoft Visual Studio erstellen, enthält es eine Standardkachel, die den Namen und das Logo Ihrer App anzeigt.</span><span class="sxs-lookup"><span data-stu-id="a5848-106">When you create a new Universal Windows Platform (UWP) app project in Microsoft Visual Studio, it includes a default tile that displays your app's name and logo.</span></span><span data-ttu-id="a5848-107">Windows zeigt diese Kachel bei der erstmaligen Installation Ihrer App an.</span><span class="sxs-lookup"><span data-stu-id="a5848-107">Windows displays this tile when your app is first installed.</span></span> <span data-ttu-id="a5848-108">Nachdem Ihre App installiert wurde, können Sie den Inhalt der Kachel mithilfe von Benachrichtigungen ändern. Sie können die Kachel zum Beispiel so ändern, dass dem Benutzer neue Informationen angezeigt werden, wie etwa neue Schlagzeilen oder der Betreff der letzten ungelesenen Nachricht.</span><span class="sxs-lookup"><span data-stu-id="a5848-108">After your app is installed, you can change your tile's content through notifications; for example, you can change the tile to communicate new information to the user, such as news headlines, or the subject of the most recent unread message.</span></span>

## <a name="configure-the-default-tile"></a><span data-ttu-id="a5848-109">Konfigurieren der Standardkachel</span><span class="sxs-lookup"><span data-stu-id="a5848-109">Configure the default tile</span></span>


<span data-ttu-id="a5848-110">Wenn Sie ein neues Projekt in Visual Studio erstellen, wird eine einfache Standardkachel erstellt, die den Namen und das Logo Ihrer App anzeigt.</span><span class="sxs-lookup"><span data-stu-id="a5848-110">When you create a new project in Visual Studio, it creates a simple default tile that displays your app's name and logo.</span></span>

<span data-ttu-id="a5848-111">Um die Kachel zu bearbeiten, doppelklicken Sie auf die Datei **Package.appxmanifest** in Ihrem Haupt-UWP-Projekt, öffnen Sie den Designer (oder klicken Sie mit der rechten Maustaste auf die Datei, und wählen Sie „Code anzeigen” aus).</span><span class="sxs-lookup"><span data-stu-id="a5848-111">To edit your tile, double click the **Package.appxmanifest** file in your main UWP project to open the designer (or right click the file and select View Code).</span></span>

```XML
  <Applications>
    <Application Id="App"
      Executable="$targetnametoken$.exe"
      EntryPoint="ExampleApp.App">
      <uap:VisualElements
        DisplayName="ExampleApp"
        Square150x150Logo="Assets\Square150x150Logo.png"
        Square44x44Logo="Assets\Square44x44Logo.png"
        Description="ExampleApp"
        BackgroundColor="#464646">
        <uap:SplashScreen Image="Assets\SplashScreen.png" />
      </uap:VisualElements>
    </Application>
  </Applications>
```

<span data-ttu-id="a5848-112">Aktualisieren Sie die folgenden Elemente:</span><span class="sxs-lookup"><span data-stu-id="a5848-112">There are a few items you should update:</span></span>

-   <span data-ttu-id="a5848-113">DisplayName: Ersetzen Sie diesen Wert mit dem Namen, der auf der Kachel angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="a5848-113">DisplayName: Replace this value with the name you want to display on your tile.</span></span>
-   <span data-ttu-id="a5848-114">ShortName: Da der Platz für Ihren Anzeigenamen auf Kacheln begrenzt ist, empfehlen wir, auch einen ShortName (Kurznamen) anzugeben, um sicherzustellen, dass der Name Ihrer App nicht abgeschnitten wird.</span><span class="sxs-lookup"><span data-stu-id="a5848-114">ShortName: Because there is limited room for your display name to fit on tiles, we recommend that you to specify a ShortName as well, to make sure your app's name doesn’t get truncated.</span></span>
-   <span data-ttu-id="a5848-115">Logobilder:</span><span class="sxs-lookup"><span data-stu-id="a5848-115">Logo images:</span></span>

    <span data-ttu-id="a5848-116">Ersetzen Sie diese Bilder durch eigene.</span><span class="sxs-lookup"><span data-stu-id="a5848-116">You should replace these images with your own.</span></span> <span data-ttu-id="a5848-117">Sie können Bilder für verschiedene visuelle Skalierungen bereitstellen, Sie müssen aber nicht alle bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="a5848-117">You have the option of supplying images for different visual scales, but you are not required to supply them all.</span></span> <span data-ttu-id="a5848-118">Um sicherzustellen, dass die App auf vielen Geräten gut aussieht, wird empfohlen, skalierte Versionen der Bilder mit jeweils 100 %, 200 % und 400 % bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="a5848-118">To ensure that you app looks good on a range of devices, we recommend that you provide 100%, 200%, and 400% scale versions of each image.</span></span> <span data-ttu-id="a5848-119">Weitere Informationen zum Erstellen dieser Ressourcen finden Sie unter [Ressourcen für Kacheln und Symbole](app-assets.md).</span><span class="sxs-lookup"><span data-stu-id="a5848-119">See [Tile and icon assets](app-assets.md) to learn more about generating these assets.</span></span>

    <span data-ttu-id="a5848-120">Skalierte Bilder haben die folgende Benennungskonvention:</span><span class="sxs-lookup"><span data-stu-id="a5848-120">Scaled images follow this naming convention:</span></span>
    
    <span data-ttu-id="a5848-121">*&lt;Bildname&gt;*.scale-*&lt;Skalierungsfaktor&gt;*.*&lt;Bilddateierweiterung&gt;*</span><span class="sxs-lookup"><span data-stu-id="a5848-121">*&lt;image name&gt;*.scale-*&lt;scale factor&gt;*.*&lt;image file extension&gt;*</span></span> 

    <span data-ttu-id="a5848-122">Beispiel: SplashScreen.scale-100.png</span><span class="sxs-lookup"><span data-stu-id="a5848-122">For example: SplashScreen.scale-100.png</span></span>

    <span data-ttu-id="a5848-123">Wenn Sie auf das Bild verweisen, verweisen Sie auf *&lt;Bildname&gt;*.*&lt;Bilddateierweiterung&gt;* („SplashScreen.png“ in diesem Beispiel).</span><span class="sxs-lookup"><span data-stu-id="a5848-123">When you refer to the image, you refer to it as *&lt;image name&gt;*.*&lt;image file extension&gt;* ("SplashScreen.png" in this example).</span></span> <span data-ttu-id="a5848-124">Das System wählt aus den bereitgestellten Bildern automatisch das entsprechend skalierte Bild für das Gerät aus.</span><span class="sxs-lookup"><span data-stu-id="a5848-124">The system will automatically select the appropriate scaled image for the device from the images you've provided.</span></span>

-   <span data-ttu-id="a5848-125">Es wird ausdrücklich empfohlen, Logos für breite und große Kacheln bereitzustellen, damit der Benutzer die Größe der Kachel Ihrer App entsprechend anpassen kann.</span><span class="sxs-lookup"><span data-stu-id="a5848-125">You don't have to, but we highly recommend supplying logos for wide and large tile sizes so that the user can resize your app's tile to those sizes.</span></span> <span data-ttu-id="a5848-126">Erstellen Sie zum Bereitstellen dieser zusätzlichen Bilder ein **DefaultTile**-Element, und verwenden Sie die **Wide310x150Logo**- und **Square310x310Logo**-Attribute, um zusätzliche Bilder anzugeben:</span><span class="sxs-lookup"><span data-stu-id="a5848-126">To provide these additional images, you create a **DefaultTile** element and use the **Wide310x150Logo** and **Square310x310Logo** attributes to specify the additional images:</span></span>
```    XML
  <Applications>
        <Application Id="App"
          Executable="$targetnametoken$.exe"
          EntryPoint="ExampleApp.App">
          <uap:VisualElements
            DisplayName="ExampleApp"
            Square150x150Logo="Assets\Square150x150Logo.png"
            Square44x44Logo="Assets\Square44x44Logo.png"
            Description="ExampleApp"
            BackgroundColor="#464646">
            <uap:DefaultTile
              Wide310x150Logo="Assets\Wide310x150Logo.png"
              Square310x310Logo="Assets\Square310x310Logo.png">
            </uap:DefaultTile>
            <uap:SplashScreen Image="Assets\SplashScreen.png" />
          </uap:VisualElements>
        </Application>
      </Applications>
```

## <a name="use-notifications-to-customize-your-tile"></a><span data-ttu-id="a5848-127">Verwenden von Benachrichtigungen zum Anpassen der Kachel</span><span class="sxs-lookup"><span data-stu-id="a5848-127">Use notifications to customize your tile</span></span>


<span data-ttu-id="a5848-128">Nachdem Ihre App installiert wurde, können Sie die Kachel mit Benachrichtigungen anpassen.</span><span class="sxs-lookup"><span data-stu-id="a5848-128">After your app is installed, you can use notifications to customize your tile.</span></span> <span data-ttu-id="a5848-129">Dies kann entweder beim ersten Start der App oder als Reaktion auf ein Ereignis wie eine Pushbenachrichtigung geschehen.</span><span class="sxs-lookup"><span data-stu-id="a5848-129">You can do this the first time your app launches or in response to an event, such as a push notification.</span></span>

<span data-ttu-id="a5848-130">Informationen über das Senden von Kachelbenachrichtigungen finden Sie unter [Senden einer lokalen Kachelbenachrichtigung ](sending-a-local-tile-notification.md).</span><span class="sxs-lookup"><span data-stu-id="a5848-130">To learn how to send tile notifications, see [Send a local tile notification](sending-a-local-tile-notification.md).</span></span>
