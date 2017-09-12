---
author: mijacobs
Description: "Eine Kachel ist die Darstellung einer App im Startmenü. Jede App verfügt über eine Kachel. Wenn Sie ein neues App-Projekt für die Universelle Windows-Plattform (UWP) in Microsoft Visual Studio erstellen, enthält es eine Standardkachel, die den Namen und das Logo der App anzeigt."
title: Kacheln
ms.assetid: 09C7E1B1-F78D-4659-8086-2E428E797653
label: Tiles
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.openlocfilehash: 8907b57bce9c39c1c508b97536485a08e8e1bf83
ms.sourcegitcommit: 9a1310468970c8d1ade0fb200126dff56ea8c9e1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/14/2017
---
# <a name="tiles-for-uwp-apps"></a><span data-ttu-id="f0943-106">Kacheln für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="f0943-106">Tiles for UWP apps</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

<span data-ttu-id="f0943-107">Eine *Kachel* ist die Darstellung einer App im Startmenü.</span><span class="sxs-lookup"><span data-stu-id="f0943-107">A *tile* is an app's representation on the Start menu.</span></span> <span data-ttu-id="f0943-108">Jede App verfügt über eine Kachel.</span><span class="sxs-lookup"><span data-stu-id="f0943-108">Every app has a tile.</span></span> <span data-ttu-id="f0943-109">Wenn Sie ein neues UWP-App-Projekt in Microsoft Visual Studio erstellen, enthält es eine Standardkachel, die den Namen und das Logo Ihrer App anzeigt.</span><span class="sxs-lookup"><span data-stu-id="f0943-109">When you create a new Universal Windows Platform (UWP) app project in Microsoft Visual Studio, it includes a default tile that displays your app's name and logo.</span></span> <span data-ttu-id="f0943-110">Windows zeigt diese Kachel bei der erstmaligen Installation Ihrer App an.</span><span class="sxs-lookup"><span data-stu-id="f0943-110">Windows displays this tile when your app is first installed.</span></span> <span data-ttu-id="f0943-111">Nachdem Ihre App installiert wurde, können Sie den Inhalt der Kachel mithilfe von Benachrichtigungen ändern. Sie können die Kachel zum Beispiel so ändern, dass dem Benutzer neue Informationen angezeigt werden, wie etwa neue Schlagzeilen oder der Betreff der letzten ungelesenen Nachricht.</span><span class="sxs-lookup"><span data-stu-id="f0943-111">After your app is installed, you can change your tile's content through notifications; for example, you can change the tile to communicate new information to the user, such as news headlines, or the subject of the most recent unread message.</span></span>

## <a name="configure-the-default-tile"></a><span data-ttu-id="f0943-112">Konfigurieren der Standardkachel</span><span class="sxs-lookup"><span data-stu-id="f0943-112">Configure the default tile</span></span>


<span data-ttu-id="f0943-113">Wenn Sie ein neues Projekt in Visual Studio erstellen, wird eine einfache Standardkachel erstellt, die den Namen und das Logo Ihrer App anzeigt.</span><span class="sxs-lookup"><span data-stu-id="f0943-113">When you create a new project in Visual Studio, it creates a simple default tile that displays your app's name and logo.</span></span>

<span data-ttu-id="f0943-114">Um die Kachel zu bearbeiten, doppelklicken Sie auf die Datei **Package.appxmanifest** in Ihrem Haupt-UWP-Projekt, öffnen Sie den Designer (oder klicken Sie mit der rechten Maustaste auf die Datei, und wählen Sie „Code anzeigen” aus).</span><span class="sxs-lookup"><span data-stu-id="f0943-114">To edit your tile, double click the **Package.appxmanifest** file in your main UWP project to open the designer (or right click the file and select View Code).</span></span>

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

<span data-ttu-id="f0943-115">Aktualisieren Sie die folgenden Elemente:</span><span class="sxs-lookup"><span data-stu-id="f0943-115">There are a few items you should update:</span></span>

-   <span data-ttu-id="f0943-116">DisplayName: Ersetzen Sie diesen Wert mit dem Namen, der auf der Kachel angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="f0943-116">DisplayName: Replace this value with the name you want to display on your tile.</span></span>
-   <span data-ttu-id="f0943-117">ShortName: Da der Platz für Ihren Anzeigenamen auf Kacheln begrenzt ist, empfehlen wir, auch einen ShortName (Kurznamen) anzugeben, um sicherzustellen, dass der Name Ihrer App nicht abgeschnitten wird.</span><span class="sxs-lookup"><span data-stu-id="f0943-117">ShortName: Because there is limited room for your display name to fit on tiles, we recommend that you to specify a ShortName as well, to make sure your app's name doesn’t get truncated.</span></span>
-   <span data-ttu-id="f0943-118">Logobilder:</span><span class="sxs-lookup"><span data-stu-id="f0943-118">Logo images:</span></span>

    <span data-ttu-id="f0943-119">Ersetzen Sie diese Bilder durch eigene.</span><span class="sxs-lookup"><span data-stu-id="f0943-119">You should replace these images with your own.</span></span> <span data-ttu-id="f0943-120">Sie können Bilder für verschiedene visuelle Skalierungen bereitstellen, Sie müssen aber nicht alle bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="f0943-120">You have the option of supplying images for different visual scales, but you are not required to supply them all.</span></span> <span data-ttu-id="f0943-121">Um sicherzustellen, dass die App auf vielen Geräten gut aussieht, wird empfohlen, skalierte Versionen der Bilder mit jeweils 100 %, 200 % und 400 % bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="f0943-121">To ensure that you app looks good on a range of devices, we recommend that you provide 100%, 200%, and 400% scale versions of each image.</span></span> <span data-ttu-id="f0943-122">Weitere Informationen zum Erstellen dieser Ressourcen finden Sie unter [Ressourcen für Kacheln und Symbole](tiles-and-notifications-app-assets.md).</span><span class="sxs-lookup"><span data-stu-id="f0943-122">See [Tile and icon assets](tiles-and-notifications-app-assets.md) to learn more about generating these assets.</span></span>

    <span data-ttu-id="f0943-123">Skalierte Bilder haben die folgende Benennungskonvention:</span><span class="sxs-lookup"><span data-stu-id="f0943-123">Scaled images follow this naming convention:</span></span>
    
    <span data-ttu-id="f0943-124">*&lt;Bildname&gt;*.scale-*&lt;Skalierungsfaktor&gt;*.*&lt;Bilddateierweiterung&gt;*</span><span class="sxs-lookup"><span data-stu-id="f0943-124">*&lt;image name&gt;*.scale-*&lt;scale factor&gt;*.*&lt;image file extension&gt;*</span></span> 

    <span data-ttu-id="f0943-125">Beispiel: SplashScreen.scale-100.png</span><span class="sxs-lookup"><span data-stu-id="f0943-125">For example: SplashScreen.scale-100.png</span></span>

    <span data-ttu-id="f0943-126">Wenn Sie auf das Bild verweisen, verweisen Sie auf *&lt;Bildname&gt;*.*&lt;Bilddateierweiterung&gt;* („SplashScreen.png“ in diesem Beispiel).</span><span class="sxs-lookup"><span data-stu-id="f0943-126">When you refer to the image, you refer to it as *&lt;image name&gt;*.*&lt;image file extension&gt;* ("SplashScreen.png" in this example).</span></span> <span data-ttu-id="f0943-127">Das System wählt aus den bereitgestellten Bildern automatisch das entsprechend skalierte Bild für das Gerät aus.</span><span class="sxs-lookup"><span data-stu-id="f0943-127">The system will automatically select the appropriate scaled image for the device from the images you've provided.</span></span>

-   <span data-ttu-id="f0943-128">Es wird ausdrücklich empfohlen, Logos für breite und große Kacheln bereitzustellen, damit der Benutzer die Größe der Kachel Ihrer App entsprechend anpassen kann.</span><span class="sxs-lookup"><span data-stu-id="f0943-128">You don't have to, but we highly recommend supplying logos for wide and large tile sizes so that the user can resize your app's tile to those sizes.</span></span> <span data-ttu-id="f0943-129">Erstellen Sie zum Bereitstellen dieser zusätzlichen Bilder ein `DefaultTile`-Element, und verwenden Sie die `Wide310x150Logo`- und `Square310x310Logo`-Attribute, um zusätzliche Bilder anzugeben:</span><span class="sxs-lookup"><span data-stu-id="f0943-129">To provide these additional images, you create a `DefaultTile` element and use the `Wide310x150Logo` and `Square310x310Logo` attributes to specify the additional images:</span></span>
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

## <a name="use-notifications-to-customize-your-tile"></a><span data-ttu-id="f0943-130">Verwenden von Benachrichtigungen zum Anpassen der Kachel</span><span class="sxs-lookup"><span data-stu-id="f0943-130">Use notifications to customize your tile</span></span>


<span data-ttu-id="f0943-131">Nachdem Ihre App installiert wurde, können Sie die Kachel mit Benachrichtigungen anpassen.</span><span class="sxs-lookup"><span data-stu-id="f0943-131">After your app is installed, you can use notifications to customize your tile.</span></span> <span data-ttu-id="f0943-132">Dies kann entweder beim ersten Start der App oder als Reaktion auf ein Ereignis wie eine Pushbenachrichtigung geschehen.</span><span class="sxs-lookup"><span data-stu-id="f0943-132">You can do this the first time your app launches or in response to an event, such as a push notification.</span></span>

<span data-ttu-id="f0943-133">Informationen über das Senden von Kachelbenachrichtigungen finden Sie unter [Senden einer lokalen Kachelbenachrichtigung ](tiles-and-notifications-sending-a-local-tile-notification.md).</span><span class="sxs-lookup"><span data-stu-id="f0943-133">To learn how to send tile notifications, see [Send a local tile notification](tiles-and-notifications-sending-a-local-tile-notification.md).</span></span>