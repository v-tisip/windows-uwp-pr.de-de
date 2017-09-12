---
author: mijacobs
Description: "Notifications Visualizer ist eine neue App für die Universelle Windows-Plattform (UWP) im Store, die Entwickler dabei unterstützt, adaptive Livekacheln für Windows 10 zu entwerfen."
title: Notifications Visualizer
ms.assetid: FCBB7BB1-2C79-484B-8FFC-26FE1934EC1C
label: TBD
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.openlocfilehash: 04e1a2e4c2bff8c7d7f75604e5665c3525f72174
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="notifications-visualizer"></a><span data-ttu-id="2f971-104">Notifications Visualizer</span><span class="sxs-lookup"><span data-stu-id="2f971-104">Notifications Visualizer</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 


<span data-ttu-id="2f971-105">Notifications Visualizer ist eine neue App für die Universelle Windows-Plattform (UWP) im [Store](https://www.microsoft.com/store/apps/notifications-visualizer/9nblggh5xsl1), die Entwickler dabei unterstützt, adaptive Livekacheln für Windows 10 zu entwerfen.</span><span class="sxs-lookup"><span data-stu-id="2f971-105">Notifications Visualizer is a new Universal Windows Platform (UWP) app in [the Store](https://www.microsoft.com/store/apps/notifications-visualizer/9nblggh5xsl1) that helps developers design adaptive live tiles for Windows 10.</span></span>

## <a name="overview"></a><span data-ttu-id="2f971-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="2f971-106">Overview</span></span>


<span data-ttu-id="2f971-107">Die App „Notifications Visualizer” bietet beim Bearbeiten eine sofortige visuelle Vorschau Ihrer Kachel, vergleichbar mit dem XAML-Editor/der Designansicht von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2f971-107">The Notifications Visualizer app provides instant visual previews of your tile as you edit, similar to Visual Studio's XAML editor/design view.</span></span> <span data-ttu-id="2f971-108">Die App prüft auch auf Fehler. So wird sichergestellt, dass Sie eine gültige Kachelnutzlast erstellen.</span><span class="sxs-lookup"><span data-stu-id="2f971-108">The app also checks for errors, which ensures that you create a valid tile payload.</span></span>

<span data-ttu-id="2f971-109">Dieser Screenshot der App zeigt die XML-Nutzlast und die Art und Weise, wie Kachelgrößen auf einem bestimmten Gerät angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="2f971-109">This screenshot from the app shows the XML payload and how tile sizes appear on a selected device:</span></span>

![Screenshot des App-Editors von Notifications Visualizer mit Code und Kacheln](images/notif-visualizer-001.png)

 

<span data-ttu-id="2f971-111">Mit Notifications Visualizer können Sie adaptive Kachelnutzlasten erstellen und testen, ohne die App selbst bearbeiten und bereitstellen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="2f971-111">With Notifications Visualizer, you can create and test adaptive tile payloads without having to edit and deploy the app itself.</span></span> <span data-ttu-id="2f971-112">Nachdem Sie eine Nutzlast mit idealen visuellen Ergebnisse erstellt haben, können Sie sie in Ihre App integrieren.</span><span class="sxs-lookup"><span data-stu-id="2f971-112">Once you've created a payload with ideal visual results you can integrate that into your app.</span></span> <span data-ttu-id="2f971-113">Weitere Informationen finden Sie unter [Senden einer lokalen Kachelbenachrichtigung](tiles-and-notifications-sending-a-local-tile-notification.md).</span><span class="sxs-lookup"><span data-stu-id="2f971-113">See [Send a local tile notification](tiles-and-notifications-sending-a-local-tile-notification.md) to learn more.</span></span>

<span data-ttu-id="2f971-114">**Hinweis**   Die Simulation des Windows-Startmenüs mit Notifications Visualizer ist nicht immer hundertprozentig genau, und bestimmte Nutzlasteigenschaften wie [baseUri](https://msdn.microsoft.com/library/windows/apps/br208712) werden nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="2f971-114">**Note**   Notifications Visualizer's simulation of the Windows Start menu isn't always completely accurate, and it doesn't support some payload properties like [baseUri](https://msdn.microsoft.com/library/windows/apps/br208712).</span></span> <span data-ttu-id="2f971-115">Wenn Sie das gewünschte Kacheldesign fertig haben, testen Sie es, indem Sie die Kachel an das tatsächliche Startmenü anheften, um sicherzustellen, dass es wie gewünscht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="2f971-115">When you have the tile design you want, test it by pinning the tile to the actual Start menu to verify that it appears as you intend.</span></span>

 

## <a name="features"></a><span data-ttu-id="2f971-116">Features</span><span class="sxs-lookup"><span data-stu-id="2f971-116">Features</span></span>


<span data-ttu-id="2f971-117">Notifications Visualizer enthält eine Reihe von Beispielnutzlasten, um zu zeigen, was mit adaptiven Live-Kacheln möglich ist und um Sie bei den ersten Schritten zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="2f971-117">Notifications Visualizer comes with a number of sample payloads to showcase what's possible with adaptive live tiles and to help you get started.</span></span> <span data-ttu-id="2f971-118">Sie können mit den verschiedenen Textoptionen, Gruppen/Untergruppen, Hintergrundbildern experimentieren und sehen, wie sich die Kachel an verschiedene Geräte und Bildschirme anpasst.</span><span class="sxs-lookup"><span data-stu-id="2f971-118">You can experiment with all the different text options, groups/subgroups, background images, and you can see how the tile adapts to different devices and screens.</span></span> <span data-ttu-id="2f971-119">Wenn Sie Änderungen vornehmen, können Sie Ihre aktualisierte Nutzlast in einer Datei zur späteren Verwendung speichern.</span><span class="sxs-lookup"><span data-stu-id="2f971-119">Once you've made changes, you can save your updated payload to a file for future use.</span></span>

<span data-ttu-id="2f971-120">Der Editor stellt Fehler und Warnungen in Echtzeit bereit.</span><span class="sxs-lookup"><span data-stu-id="2f971-120">The editor provides real-time errors and warnings.</span></span> <span data-ttu-id="2f971-121">Wenn Ihre App-Nutzlast beispielsweise auf weniger als 5KB (eine Plattformbeschränkung) begrenzt ist, warnt Notifications Visualizer Sie, falls Ihre Nutzlast diese Grenze überschreitet.</span><span class="sxs-lookup"><span data-stu-id="2f971-121">For example, if your app payload is limited to less than 5 KB (a platform limitation), Notifications Visualizer warns you if your payload exceeds that limit.</span></span> <span data-ttu-id="2f971-122">Sie erhalten Warnungen aufgrund falscher Attributnamen oder Werte, wodurch das Debuggen visueller Probleme erleichtert wird.</span><span class="sxs-lookup"><span data-stu-id="2f971-122">It gives you warnings for incorrect attribute names or values, which helps you debug visual issues.</span></span>

<span data-ttu-id="2f971-123">Sie können Kacheleigenschaften, wie Anzeigename, Farbe, Logos, ShowName, Signalwert, steuern.</span><span class="sxs-lookup"><span data-stu-id="2f971-123">You can control tile properties like display name, color, logos, ShowName, badge value.</span></span> <span data-ttu-id="2f971-124">Anhand dieser Optionen verstehen Sie sofort, wie Ihre Kacheleigenschaften und Kachelbenachrichtigungsnutzlasten interagieren und welche Ergebnisse sie produzieren.</span><span class="sxs-lookup"><span data-stu-id="2f971-124">These options help you instantly understand how your tile properties and tile notification payloads interact, and the results they produce.</span></span>

<span data-ttu-id="2f971-125">Dieser Screenshot der App zeigt den Kachel-Editor:</span><span class="sxs-lookup"><span data-stu-id="2f971-125">This screenshot from the app shows the tile editor:</span></span>

![Screenshot des Notifications Visualizer-Editors mit Kacheln](images/notif-visualizer-004.png)

 

## <a name="related-topics"></a><span data-ttu-id="2f971-127">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="2f971-127">Related topics</span></span>


* [<span data-ttu-id="2f971-128">Notifications Visualizer aus dem Store herunterladen</span><span class="sxs-lookup"><span data-stu-id="2f971-128">Get Notifications Visualizer in the Store</span></span>](https://www.microsoft.com/store/apps/notifications-visualizer/9nblggh5xsl1)
* [<span data-ttu-id="2f971-129">Erstellen adaptiver Kacheln</span><span class="sxs-lookup"><span data-stu-id="2f971-129">Create adaptive tiles</span></span>](tiles-and-notifications-create-adaptive-tiles.md)
* [<span data-ttu-id="2f971-130">Vorlagen für adaptive Kacheln: Schema und Dokumentation</span><span class="sxs-lookup"><span data-stu-id="2f971-130">Adaptive tile templates: schema and documentation</span></span>](tiles-and-notifications-adaptive-tiles-schema.md)
* [<span data-ttu-id="2f971-131">Kacheln und Popups (MSDN-Blog)</span><span class="sxs-lookup"><span data-stu-id="2f971-131">Tiles and toasts (MSDN blog)</span></span>](http://blogs.msdn.com/b/tiles_and_toasts/)