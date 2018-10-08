---
author: andrewleader
Description: Notifications Visualizer is a new Universal Windows Platform (UWP) app in the Store that helps developers design adaptive live tiles for Windows 10.
title: Notifications Visualizer
ms.assetid: FCBB7BB1-2C79-484B-8FFC-26FE1934EC1C
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: af8b2489346e1ef81c5cae304802814b79b8b950
ms.sourcegitcommit: fbdc9372dea898a01c7686be54bea47125bab6c0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/08/2018
ms.locfileid: "4415868"
---
# <a name="notifications-visualizer"></a><span data-ttu-id="7210c-103">Notifications Visualizer</span><span class="sxs-lookup"><span data-stu-id="7210c-103">Notifications Visualizer</span></span>

 


<span data-ttu-id="7210c-104">Notifications Visualizer ist eine neue App für die Universelle Windows-Plattform (UWP) im [Store](https://www.microsoft.com/store/apps/notifications-visualizer/9nblggh5xsl1), die Entwickler dabei unterstützt, adaptive Livekacheln und interaktive Popupbenachrichtigungen für Windows 10 zu entwerfen.</span><span class="sxs-lookup"><span data-stu-id="7210c-104">Notifications Visualizer is a new Universal Windows Platform (UWP) app [in the Store](https://www.microsoft.com/store/apps/notifications-visualizer/9nblggh5xsl1) that helps developers design adaptive Live Tiles and interactive toast notifications for Windows 10.</span></span>


## <a name="overview"></a><span data-ttu-id="7210c-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="7210c-105">Overview</span></span>

<span data-ttu-id="7210c-106">Die App „Notifications Visualizer” bietet beim Bearbeiten der XML-Nutzlast eine sofortige visuelle Vorschau Ihrer Kachel und Popupbenachrichtigung, vergleichbar mit dem XAML-Editor/der Designansicht von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7210c-106">Notifications Visualizer provides instant visual previews of your tile and toast notification as you edit the XML payload, similar to Visual Studio's XAML editor/design view.</span></span> <span data-ttu-id="7210c-107">Die App prüft auch auf Fehler. So wird sichergestellt, dass Sie eine gültige Kachel- oder Popupbenachrichtigungsnutzlast erstellen.</span><span class="sxs-lookup"><span data-stu-id="7210c-107">The app also checks for errors, which ensures that you create a valid tile or toast notification payload.</span></span>

<span data-ttu-id="7210c-108">Dieser Screenshot der App zeigt die XML-Nutzlast und die Art und Weise, wie Kachelgrößen auf einem bestimmten Gerät angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="7210c-108">This screenshot from the app shows the XML payload and how tile sizes appear on a selected device:</span></span>

![Screenshot des App-Editors von Notifications Visualizer mit Code und Kacheln](images/notif-visualizer-001.png)

 

<span data-ttu-id="7210c-110">Mit Notifications Visualizer können Sie adaptive Kachel-oder Popupnutzlasten erstellen und testen, ohne Ihre App selbst bearbeiten und bereitstellen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="7210c-110">With Notifications Visualizer, you can create and test adaptive tile and toast payloads without having to edit and deploy your own app.</span></span> <span data-ttu-id="7210c-111">Nachdem Sie eine Nutzlast mit idealen visuellen Ergebnisse erstellt haben, können Sie sie in Ihre App integrieren.</span><span class="sxs-lookup"><span data-stu-id="7210c-111">Once you've created a payload with ideal visual results, you can integrate that into your app.</span></span> <span data-ttu-id="7210c-112">Informationen finden Sie unter [Senden einer lokalen Kachelbenachrichtigung](sending-a-local-tile-notification.md) und [Senden einer lokalen Popupbenachrichtigung](send-local-toast.md).</span><span class="sxs-lookup"><span data-stu-id="7210c-112">See [Send a local tile notification](sending-a-local-tile-notification.md) and [Send a local toast](send-local-toast.md) to learn more.</span></span>

<span data-ttu-id="7210c-113">**Hinweis**   Die Simulation des Windows-Startmenüs und der Popupbenachrichtigung mit Notifications Visualizer ist nicht immer hundertprozentig genau, und bestimmte erweiterte Nutzlasteigenschaften werden nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="7210c-113">**Note**   Notifications Visualizer's simulation of the Windows Start menu and toast notifications isn't always completely accurate, and it doesn't support some advanced payload properties.</span></span> <span data-ttu-id="7210c-114">Wenn Sie das gewünschte Kachel- oder Popupdesign fertig haben, testen Sie es, indem Sie die Kachel oder Popupbenachrichtigung an das tatsächliche Startmenü anheften, um sicherzustellen, dass es wie gewünscht angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="7210c-114">When you have the tile or toast you want, test it by pinning the tile or popping the toast to verify that it appears as you intend.</span></span>

 

## <a name="features"></a><span data-ttu-id="7210c-115">Features</span><span class="sxs-lookup"><span data-stu-id="7210c-115">Features</span></span>

<span data-ttu-id="7210c-116">Notifications Visualizer enthält eine Reihe von Beispielnutzlasten, um zu zeigen, was mit adaptiven Live-Kacheln und interativen Popups möglich ist und um Sie bei den ersten Schritten zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="7210c-116">Notifications Visualizer comes with a number of sample payloads to showcase what's possible with adaptive Live Tiles and interactive toasts to help you get started.</span></span> <span data-ttu-id="7210c-117">Sie können mit den verschiedenen Textoptionen, Gruppen/Untergruppen, Hintergrundbildern experimentieren und sehen, wie sich die Kachel an verschiedene Geräte und Bildschirme anpasst.</span><span class="sxs-lookup"><span data-stu-id="7210c-117">You can experiment with all the different text options, groups/subgroups, background images, and you can see how the tile adapts to different devices and screens.</span></span> <span data-ttu-id="7210c-118">Wenn Sie Änderungen vornehmen, können Sie Ihre aktualisierte Nutzlast in einer Datei zur späteren Verwendung speichern.</span><span class="sxs-lookup"><span data-stu-id="7210c-118">Once you've made changes, you can save your updated payload to a file for future use.</span></span>

<span data-ttu-id="7210c-119">Der Editor stellt Fehler und Warnungen in Echtzeit bereit.</span><span class="sxs-lookup"><span data-stu-id="7210c-119">The editor provides real-time errors and warnings.</span></span> <span data-ttu-id="7210c-120">Wenn Ihre App-Nutzlast beispielsweise größer als 5KB (eine Plattformbeschränkung) ist, warnt Notifications Visualizer Sie, falls Ihre Nutzlast diese Grenze überschreitet.</span><span class="sxs-lookup"><span data-stu-id="7210c-120">For example, if your payload is greater than 5 KB (a platform limitation), Notifications Visualizer warns you that your payload exceeds that limit.</span></span> <span data-ttu-id="7210c-121">Sie erhalten Warnungen aufgrund falscher Attributnamen oder Werte, wodurch das Debuggen visueller Probleme erleichtert wird.</span><span class="sxs-lookup"><span data-stu-id="7210c-121">It gives you warnings for incorrect attribute names or values, which helps you debug visual issues.</span></span>

<span data-ttu-id="7210c-122">Sie können Kacheleigenschaften, wie Anzeigename, Farbe, Logos, ShowName und Signalwert, steuern.</span><span class="sxs-lookup"><span data-stu-id="7210c-122">You can control tile properties like display name, color, logos, ShowName, and badge value.</span></span> <span data-ttu-id="7210c-123">Anhand dieser Optionen verstehen Sie sofort, wie Ihre Kacheleigenschaften und Kachelbenachrichtigungsnutzlasten interagieren und welche Ergebnisse sie produzieren.</span><span class="sxs-lookup"><span data-stu-id="7210c-123">These options help you instantly understand how your tile properties and tile notification payloads interact, and the results they produce.</span></span>

<span data-ttu-id="7210c-124">Dieser Screenshot der App zeigt den Kachel-Editor:</span><span class="sxs-lookup"><span data-stu-id="7210c-124">This screenshot from the app shows the tile editor:</span></span>

![Screenshot des Notifications Visualizer-Editors mit Kacheln](images/notif-visualizer-004.png)

 

## <a name="related-topics"></a><span data-ttu-id="7210c-126">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="7210c-126">Related topics</span></span>

* [<span data-ttu-id="7210c-127">Notifications Visualizer aus dem Store herunterladen</span><span class="sxs-lookup"><span data-stu-id="7210c-127">Get Notifications Visualizer in the Store</span></span>](https://www.microsoft.com/store/apps/notifications-visualizer/9nblggh5xsl1)
* [<span data-ttu-id="7210c-128">Erstellen adaptiver Kacheln</span><span class="sxs-lookup"><span data-stu-id="7210c-128">Create adaptive tiles</span></span>](create-adaptive-tiles.md)
* [<span data-ttu-id="7210c-129">Interaktive Popupbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="7210c-129">Interactive toasts</span></span>](adaptive-interactive-toasts.md)