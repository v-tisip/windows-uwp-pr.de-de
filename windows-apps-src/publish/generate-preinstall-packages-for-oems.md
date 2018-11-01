---
author: jnHs
Description: If your developer account has been granted the appropriate permissions, you can generate and download preinstall packages so that an OEM can include your app in their OS image.
title: Generieren von Vorinstallationspaketen für OEMs
ms.assetid: AC3A45E8-7BBD-44E9-B2D3-B74B7C9B2BC9
ms.author: wdg-dev-content
ms.date: 10/31/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 02f7c1ad1a396464532a1c63c925bf9e19600f1b
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5873865"
---
# <a name="generate-preinstall-packages-for-oems"></a><span data-ttu-id="a4c2c-103">Generieren von Vorinstallationspaketen für OEMs</span><span class="sxs-lookup"><span data-stu-id="a4c2c-103">Generate preinstall packages for OEMs</span></span>

<span data-ttu-id="a4c2c-104">Wenn Ihrem Entwicklerkonto die entsprechenden Berechtigungen gewährt wurden, können Sie Vorinstallationspakete generieren und herunterladen, damit das OEM Ihre App in ein OS-Image einschließen kann.</span><span class="sxs-lookup"><span data-stu-id="a4c2c-104">If your developer account has been granted the appropriate permissions, you can generate and download preinstall packages so that an OEM can include your app in their OS image.</span></span> <span data-ttu-id="a4c2c-105">Vorinstallationsberechtigungen werden nur für Entwicklerkonten aktiviert, die von OEMs unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="a4c2c-105">Preinstall permissions are only enabled on developer accounts that are sponsored by OEMs.</span></span>


## <a name="important-preinstall-policy--limitations"></a><span data-ttu-id="a4c2c-106">Wichtige Vorinstallationsrichtlinien und -beschränkungen</span><span class="sxs-lookup"><span data-stu-id="a4c2c-106">Important preinstall policy & limitations</span></span>

<span data-ttu-id="a4c2c-107">Vorinstallations-apps müssen zertifiziert sein, über das [Partner Center](https://partner.microsoft.com/dashboard) die aktuelle Store-Lizenz verfügen, damit es ist nicht möglich, eine Verbindung herstellen, an den Store und app-Updates zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="a4c2c-107">Preinstall apps must be certified through [Partner Center](https://partner.microsoft.com/dashboard) to have the latest Store license so that they are able to connect to the Store and receive app updates.</span></span>

<span data-ttu-id="a4c2c-108">Jede vorinstallierte App muss zum aktuellen Zeitpunkt und in Zukunft auf allen Märkten kostenlos angeboten werden.</span><span class="sxs-lookup"><span data-stu-id="a4c2c-108">Any app that is preinstalled must be and remain free in all markets.</span></span>


## <a name="generating-preinstall-packages"></a><span data-ttu-id="a4c2c-109">Generieren von Vorinstallationspaketen</span><span class="sxs-lookup"><span data-stu-id="a4c2c-109">Generating preinstall packages</span></span>

<span data-ttu-id="a4c2c-110">Nachdem ein Konto mit Vorinstallationsberechtigungen aktiviert wurde, führen Sie die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="a4c2c-110">Once an account has been enabled with preinstall permissions, complete the following steps:</span></span>

1.  <span data-ttu-id="a4c2c-111">Navigieren Sie im Partner Center an die app, die vorinstalliert werden soll.</span><span class="sxs-lookup"><span data-stu-id="a4c2c-111">In Partner Center, navigate to the app that is to be preinstalled.</span></span>
2.  <span data-ttu-id="a4c2c-112">Erweitern Sie im linken Navigationsmenü **App-Verwaltung**, und wählen Sie **Aktuelle Pakete** aus.</span><span class="sxs-lookup"><span data-stu-id="a4c2c-112">In the left navigation menu, expand **App management** and select **Current packages**.</span></span>
3.  <span data-ttu-id="a4c2c-113">Wählen Sie im Abschnitt **Pakete für die Vorinstallation des Betriebssystems anfordern** **Downloadbare Pakete ermöglichen** aus.</span><span class="sxs-lookup"><span data-stu-id="a4c2c-113">In the **Request packages for OS preinstallation** section, select **Enable downloadable packages**.</span></span>
4.  <span data-ttu-id="a4c2c-114">Wählen Sie im Bestätigungsdialogfeld **Aktivieren** aus.</span><span class="sxs-lookup"><span data-stu-id="a4c2c-114">In the confirmation dialog will, select **Enable**.</span></span>
5.  <span data-ttu-id="a4c2c-115">Suchen Sie das Paket, das Sie herunterladen möchten, und wählen Sie den entsprechenden Link **Paket generieren**.</span><span class="sxs-lookup"><span data-stu-id="a4c2c-115">Find the package that you want to download and select the appropriate **Generate package** link.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a4c2c-116">Die Dauer zum Generieren von Vorinstallationspaketen hängt von der Größe des ausgewählten Pakets ab.</span><span class="sxs-lookup"><span data-stu-id="a4c2c-116">Generation time for preinstall packages will vary depending on the size of the package you have selected.</span></span> <span data-ttu-id="a4c2c-117">Sie können diese Seite verlassen und später darauf zurückkehren, oder Sie können die Seite geöffnet lassen, während das Paket generiert wird.</span><span class="sxs-lookup"><span data-stu-id="a4c2c-117">You can leave this page and come back later, or you can leave the page open while your package is being generated.</span></span>

6.  <span data-ttu-id="a4c2c-118">Nachdem das Paket generiert wurde, wird ein Link zu **Paket herunterladen** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a4c2c-118">After the package has been generated, a link to **Download package** will appear.</span></span> <span data-ttu-id="a4c2c-119">Wählen Sie das Link aus, um die ZIP-Datei herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="a4c2c-119">Select this link to download the .zip file.</span></span>

<span data-ttu-id="a4c2c-120">Die ZIP-Datei kann dem OEM zur Verfügung gestellt werden, damit er sie in sein Betriebssystemimage einschließt.</span><span class="sxs-lookup"><span data-stu-id="a4c2c-120">You can then provide the .zip file to the OEM for inclusion in their OS image.</span></span>


## <a name="support"></a><span data-ttu-id="a4c2c-121">Support</span><span class="sxs-lookup"><span data-stu-id="a4c2c-121">Support</span></span>

<span data-ttu-id="a4c2c-122">Wenn Sie weitere Fragen zum Generieren von Vorinstallationspaketen haben, senden Sie eine E-Mail an <partnerops@microsoft.com>.</span><span class="sxs-lookup"><span data-stu-id="a4c2c-122">If you have further questions about generating preinstall packages, please email <partnerops@microsoft.com>.</span></span>

 

 




