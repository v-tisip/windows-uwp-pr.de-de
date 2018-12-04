---
Description: How to use thumbnail images to help users preview files in UWP apps.
title: Richtlinien für Miniaturbilder in UWP-Apps
label: Thumbnail images
template: detail.hbs
ms.date: 01/08/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 92899333f0bc787fc6538e0bb22c148ac9f5c56f
ms.sourcegitcommit: b4c502d69a13340f6e3c887aa3c26ef2aeee9cee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "8465043"
---
# <a name="thumbnail-images"></a><span data-ttu-id="fe6c4-103">Miniaturbilder</span><span class="sxs-lookup"><span data-stu-id="fe6c4-103">Thumbnail images</span></span>

<span data-ttu-id="fe6c4-104">Diese Richtlinien beschreiben, wie Miniaturbilder verwendet werden, um den Benutzern eine Dateivorschau zu bieten, während sie in Ihrer UWP-App navigieren.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-104">These guidelines describe how to use thumbnail images to help users preview files as they browse in your UWP app.</span></span> 

> <span data-ttu-id="fe6c4-105">**Wichtige APIs**: [ThumbnailMode-Enumeration](https://docs.microsoft.com/uwp/api/windows.storage.fileproperties.thumbnailmode)</span><span class="sxs-lookup"><span data-stu-id="fe6c4-105">**Important APIs**: [ThumbnailMode enum](https://docs.microsoft.com/uwp/api/windows.storage.fileproperties.thumbnailmode)</span></span>

## <a name="should-my-app-include-thumbnails"></a><span data-ttu-id="fe6c4-106">Sollte meine App Miniaturansichten beinhalten?</span><span class="sxs-lookup"><span data-stu-id="fe6c4-106">Should my app include thumbnails?</span></span>

<span data-ttu-id="fe6c4-107">Wenn Ihre App das Durchsuchen von Dateien ermöglicht, können Sie Miniaturbilder anzeigen, damit Benutzer eine schnelle Vorschau auf diese Dateien erhalten.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-107">If your app allows users to browse files, you can display thumbnail images to help users quickly preview those files.</span></span> 

<span data-ttu-id="fe6c4-108">Verwenden Sie Miniaturansichten für Folgendes:</span><span class="sxs-lookup"><span data-stu-id="fe6c4-108">Use thumbnails when:</span></span> 
- <span data-ttu-id="fe6c4-109">Anzeigen einer Vorschau für mehrere Elemente in einer Galeriesammlung (beispielsweise Dateien und Ordner)</span><span class="sxs-lookup"><span data-stu-id="fe6c4-109">Displaying previews for many items in a gallery collection (like files and folders).</span></span> <span data-ttu-id="fe6c4-110">In einer Fotogalerie sollten zum Beispiel Miniaturansichten verwendet werden, um den Benutzern eine kleine Vorschau der einzelnen Bilder anzuzeigen, während sie ihre Fotodateien durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-110">For example, a photo gallery should use thumbnails to give users a small view of each picture as they browse through their photo files.</span></span>

    ![Videogalerie](images/thumbnail-gallery.png)

- <span data-ttu-id="fe6c4-112">Anzeigen einer Vorschau für ein einzelnes Element in einer Liste (beispielsweise eine bestimmte Datei)</span><span class="sxs-lookup"><span data-stu-id="fe6c4-112">Displaying a preview for an individual item in a list (like a specific file).</span></span> <span data-ttu-id="fe6c4-113">Möglicherweise möchte ein Benutzer mehr Informationen über eine Datei sehen, darunter eine größere Miniaturansicht für eine bessere Vorschau, bevor er entscheidet, ob er die Datei öffnet.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-113">For example, the user may want to see more information about a file, including a larger thumbnail for a better preview, before deciding whether to open the file.</span></span> 

    ![Videovorschau](images/thumbnail-preview.png)

## <a name="dos-and-donts"></a><span data-ttu-id="fe6c4-115">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="fe6c4-115">Dos and don'ts</span></span>
- <span data-ttu-id="fe6c4-116">Geben Sie den [Miniaturansichtsmodus](https://docs.microsoft.com/uwp/api/windows.storage.fileproperties.thumbnailmode) (PicturesView, VideosView, DocumentsView, MusicView, ListView oder SingleItem) an, wenn Sie Miniaturansichten abrufen.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-116">Specify the [thumbnail mode](https://docs.microsoft.com/uwp/api/windows.storage.fileproperties.thumbnailmode) (PicturesView, VideosView, DocumentsView, MusicView, ListView, or SingleItem) when you retrieve thumbnails.</span></span> <span data-ttu-id="fe6c4-117">So stellen Sie sicher, dass Miniaturbilder für die Anzeige der Dateitypen optimiert sind, die Benutzer anzeigen möchten.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-117">This ensures that thumbnail images are optimized to display the type of files users want to see.</span></span> 
    - <span data-ttu-id="fe6c4-118">Verwenden Sie den SingleItem-Modus, um unabhängig vom Dateityp eine Miniaturansicht für ein einzelnes Element abzurufen.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-118">Use the SingleItem mode to retrieve a thumbnail for a single item, regardless of file type.</span></span> <span data-ttu-id="fe6c4-119">Die anderen Miniaturansichtsmodi dienen zum Anzeigen von Vorschauen auf mehrere Dateien.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-119">The other thumbnail modes are meant to display previews of multiple files.</span></span> 

- <span data-ttu-id="fe6c4-120">Zeigen Sie generische Platzhalterbilder anstelle von Miniaturansichten an, während die Miniaturansichten geladen werden.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-120">Display generic placeholder images in place of thumbnails while thumbnails load.</span></span> <span data-ttu-id="fe6c4-121">Wenn Sie Platzhalter auf diese Weise verwenden, scheint die App besser zu reagieren, da Benutzer mit Vorschauen interagieren können, bevor die Miniaturansicht geladen ist.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-121">Using placeholders helps your app seem more responsive because users can interact with previews before the thumbnail load.</span></span> 

    <span data-ttu-id="fe6c4-122">Platzhalterbilder sollten folgende Merkmale aufweisen:</span><span class="sxs-lookup"><span data-stu-id="fe6c4-122">Placeholder images should be:</span></span>
    * <span data-ttu-id="fe6c4-123">Sie sollten sich konkret auf die Art des Elements beziehen, das sie darstellen.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-123">Specific to the kind of item that it stands in for.</span></span> <span data-ttu-id="fe6c4-124">Beispielsweise sollten Ordner, Bilder und Videos alle eigene spezielle Platzhalter haben.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-124">For example, folders, pictures, and videos should all have their own specialized placeholders.</span></span> 
    * <span data-ttu-id="fe6c4-125">Sie sollten die gleiche Größe und das gleiche Seitenverhältnis aufweisen wie das Miniaturbild, das sie darstellen.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-125">The same size and aspect ratio as the thumbnail image it stands in for.</span></span> 
    * <span data-ttu-id="fe6c4-126">Sie sollten angezeigt werden, bis das Miniaturbild geladen ist.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-126">Displayed until the thumbnail image is loaded.</span></span> 

- <span data-ttu-id="fe6c4-127">Verwenden Sie Platzhalterbilder mit Beschriftungen, um Ordner oder Dateigruppen darzustellen und von einzelnen Dateien zu unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-127">Use placeholder images with text labels to represent folders and file groups to differentiate from individual files.</span></span>

- <span data-ttu-id="fe6c4-128">Wenn Sie eine Miniaturansicht nicht abrufen können, zeigen Sie stattdessen ein Platzhalterbild an.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-128">If you can't retrieve a thumbnail, display a placeholder image.</span></span> 

- <span data-ttu-id="fe6c4-129">Zeigen Sie zusätzliche Dateiinformationen an, wenn Sie Vorschauen für Dokumente und Musikdateien bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-129">Display additional file information when providing previews for document and music files.</span></span> <span data-ttu-id="fe6c4-130">Benutzer können dann wichtige Informationen über eine Datei identifizieren, die durch ein Miniaturbild allein möglicherweise nicht vermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-130">Users can then identify key information about a file that might not be readily available from a thumbnail image alone.</span></span> <span data-ttu-id="fe6c4-131">Beispielsweise können Sie für eine Musikdatei neben der Miniaturansicht des Albumcovers auch den Namen des Interpreten anzeigen.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-131">For example, for a music file, you might display the name of the artist along with the thumbnail of the album art.</span></span> 

- <span data-ttu-id="fe6c4-132">Zeigen Sie für Bild- und Videodateien keine zusätzlichen Dateiinformationen an.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-132">Don't display additional file info for picture and video files.</span></span> <span data-ttu-id="fe6c4-133">In den meisten Fällen ist ein Miniaturbild ausreichend für Benutzer, die Bilder und Videos durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-133">In most cases, a thumbnail image is sufficient for users browsing through pictures and videos.</span></span> 

## <a name="additional-usage-guidelines"></a><span data-ttu-id="fe6c4-134">Weitere Richtlinien zur Verwendung</span><span class="sxs-lookup"><span data-stu-id="fe6c4-134">Additional usage guidelines</span></span>
<span data-ttu-id="fe6c4-135">Empfohlene [Miniaturansichtsmodi](https://docs.microsoft.com/uwp/api/windows.storage.fileproperties.thumbnailmode) und deren Features:</span><span class="sxs-lookup"><span data-stu-id="fe6c4-135">Recommended [thumbnail modes](https://docs.microsoft.com/uwp/api/windows.storage.fileproperties.thumbnailmode) and their features:</span></span>

<table>
<tr>
<th> <span data-ttu-id="fe6c4-136">Vorschauanzeige für</span><span class="sxs-lookup"><span data-stu-id="fe6c4-136">Display previews for</span></span></th>
<th> <span data-ttu-id="fe6c4-137">Miniaturansichtsmodi</span><span class="sxs-lookup"><span data-stu-id="fe6c4-137">Thumbnail modes</span></span> </th>
<th> <span data-ttu-id="fe6c4-138">Features der abgerufenen Miniaturansichten</span><span class="sxs-lookup"><span data-stu-id="fe6c4-138">Features of the retrieved thumbnail images</span></span> </th>
</tr>
<tr>
<td> <span data-ttu-id="fe6c4-139">Bilder</span><span class="sxs-lookup"><span data-stu-id="fe6c4-139">Pictures</span></span><br /> <span data-ttu-id="fe6c4-140">Videos</span><span class="sxs-lookup"><span data-stu-id="fe6c4-140">Videos</span></span> </td>
<td> <span data-ttu-id="fe6c4-141">PicturesView</span><span class="sxs-lookup"><span data-stu-id="fe6c4-141">PicturesView</span></span> <br /><span data-ttu-id="fe6c4-142">VideosView</span><span class="sxs-lookup"><span data-stu-id="fe6c4-142">VideosView</span></span> </td>
<td> <span data-ttu-id="fe6c4-143"><b>Größe</b>: Mittel, vorzugsweise mindestens 190 (bei einer Bildgröße von 190x130)</span><span class="sxs-lookup"><span data-stu-id="fe6c4-143"><b>Size</b>: Medium, preferably at least 190 (if the image size is 190x130)</span></span> <br /><span data-ttu-id="fe6c4-144">
<b>Seitenverhältnis</b>:Gleichmäßiges, breites Seitenverhältnis von ca. 0,7 (190x130 bei einer Größe von 190)</span><span class="sxs-lookup"><span data-stu-id="fe6c4-144">
<b>Aspect ratio</b>: Uniform, wide aspect ratio of about .7 (190x130 if the size is 190)</span></span> <br />
<span data-ttu-id="fe6c4-145">Zugeschnitten für die Vorschau</span><span class="sxs-lookup"><span data-stu-id="fe6c4-145">Cropped for previews.</span></span> <br /> 
<span data-ttu-id="fe6c4-146">Gute Ausrichtung von Bildern in einem Raster durch einheitliches Seitenverhältnis</span><span class="sxs-lookup"><span data-stu-id="fe6c4-146">Good for aligning images in a grid because of uniform aspect ratio.</span></span>  </td>
</tr>
<tr>
<td> <span data-ttu-id="fe6c4-147">Dokumente</span><span class="sxs-lookup"><span data-stu-id="fe6c4-147">Documents</span></span><br /><span data-ttu-id="fe6c4-148">Musik</span><span class="sxs-lookup"><span data-stu-id="fe6c4-148">Music</span></span> </td>
<td> <span data-ttu-id="fe6c4-149">DocumentsView</span><span class="sxs-lookup"><span data-stu-id="fe6c4-149">DocumentsView</span></span> <br /><span data-ttu-id="fe6c4-150">MusicView</span><span class="sxs-lookup"><span data-stu-id="fe6c4-150">MusicView</span></span> <br /> <span data-ttu-id="fe6c4-151">ListView</span><span class="sxs-lookup"><span data-stu-id="fe6c4-151">ListView</span></span></td>
<td> <span data-ttu-id="fe6c4-152"><b>Größe</b>: Klein, vorzugsweise mindestens 40 x 40 Pixel</span><span class="sxs-lookup"><span data-stu-id="fe6c4-152"><b>Size</b>: Small, preferably at least 40 x 40 pixels</span></span> <br /><span data-ttu-id="fe6c4-153">
<b>Seitenverhältnis:</b> Einheitliches, quadratisches Seitenverhältnis</span><span class="sxs-lookup"><span data-stu-id="fe6c4-153">
<b>Aspect ratio</b>:  Uniform, square aspect ratio</span></span>  <br />
<span data-ttu-id="fe6c4-154">Aufgrund des quadratischen Seitenverhältnisses gut geeignet für die Vorschau von Albumcovern</span><span class="sxs-lookup"><span data-stu-id="fe6c4-154">Good for previewing album art because of the square aspect ratio.</span></span> <br /> 
<span data-ttu-id="fe6c4-155">Dokumente sehen ebenso aus wie in einem Dateiauswahlfenster (Verwendung derselben Symbole).</span><span class="sxs-lookup"><span data-stu-id="fe6c4-155">Documents look the same as they look in a file picker window (it uses the same icons).</span></span> </td>
</tr>
</tr>
<tr>
<td> <span data-ttu-id="fe6c4-156">Alle einzelnen Elemente (unabhängig vom Dateityp)</span><span class="sxs-lookup"><span data-stu-id="fe6c4-156">Any single item (regardless of file type)</span></span> </td>
<td> <span data-ttu-id="fe6c4-157">SingleItem</span><span class="sxs-lookup"><span data-stu-id="fe6c4-157">SingleItem</span></span> </td>
<td> <span data-ttu-id="fe6c4-158"><b>Größe</b>: Klein, vorzugsweise mindestens 40 x 40 Pixel</span><span class="sxs-lookup"><span data-stu-id="fe6c4-158"><b>Size</b>: Small, preferably at least 40 x 40 pixels</span></span> <br /><span data-ttu-id="fe6c4-159">
<b>Seitenverhältnis:</b> Einheitliches, quadratisches Seitenverhältnis</span><span class="sxs-lookup"><span data-stu-id="fe6c4-159">
<b>Aspect ratio</b>:  Uniform, square aspect ratio</span></span>  <br />
<span data-ttu-id="fe6c4-160">Aufgrund des quadratischen Seitenverhältnisses gut geeignet für die Vorschau von Albumcovern</span><span class="sxs-lookup"><span data-stu-id="fe6c4-160">Good for previewing album art because of the square aspect ratio.</span></span> <br /> 
<span data-ttu-id="fe6c4-161">Dokumente sehen ebenso aus wie in einem Dateiauswahlfenster (Verwendung derselben Symbole).</span><span class="sxs-lookup"><span data-stu-id="fe6c4-161">Documents look the same as they look in a file picker window (it uses the same icons).</span></span> </td>
</tr>
</table>

<span data-ttu-id="fe6c4-162">Hier sehen Sie Beispiele dafür, wie sich abgerufene Miniaturbilder je nach Dateityp und Miniaturansichtsmodus unterscheiden:</span><span class="sxs-lookup"><span data-stu-id="fe6c4-162">Here are examples showing how retrieved thumbnail images differ depending on file type and thumbnail mode:</span></span>
<div class="mx-responsive-img">
<table>
<tr>
<th><span data-ttu-id="fe6c4-163">Elementtyp</span><span class="sxs-lookup"><span data-stu-id="fe6c4-163">Item type</span></span></th>
<th><span data-ttu-id="fe6c4-164">Beim Abruf mithilfe von:</span><span class="sxs-lookup"><span data-stu-id="fe6c4-164">When retrieved using:</span></span> <ul><li><span data-ttu-id="fe6c4-165">PicturesView</span><span class="sxs-lookup"><span data-stu-id="fe6c4-165">PicturesView</span></span> <li><span data-ttu-id="fe6c4-166">VideosView</span><span class="sxs-lookup"><span data-stu-id="fe6c4-166">VideosView</span></span></ul></th>
<th><span data-ttu-id="fe6c4-167">Beim Abruf mithilfe von:</span><span class="sxs-lookup"><span data-stu-id="fe6c4-167">When retrieved using:</span></span> <ul><li><span data-ttu-id="fe6c4-168">DocumentsView</span><span class="sxs-lookup"><span data-stu-id="fe6c4-168">DocumentsView</span></span> <li><span data-ttu-id="fe6c4-169">MusicView</span><span class="sxs-lookup"><span data-stu-id="fe6c4-169">MusicView</span></span> <li><span data-ttu-id="fe6c4-170">ListView</span><span class="sxs-lookup"><span data-stu-id="fe6c4-170">ListView</span></span></ul></th>
<th><span data-ttu-id="fe6c4-171">Beim Abruf mithilfe von:</span><span class="sxs-lookup"><span data-stu-id="fe6c4-171">When retrieved using:</span></span> <ul><li><span data-ttu-id="fe6c4-172">SingleItem</span><span class="sxs-lookup"><span data-stu-id="fe6c4-172">SingleItem</span></span></ul></th>
<tr>
<tr>
<td><span data-ttu-id="fe6c4-173">Picture</span><span class="sxs-lookup"><span data-stu-id="fe6c4-173">Picture</span></span></td>
<td><span data-ttu-id="fe6c4-174">Für das Miniaturbild wird das ursprüngliche Seitenverhältnis der Datei verwendet.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-174">The thumbnail image uses the original aspect ratio of the file.</span></span> <br />
<img src="images/thumbnail-pic-picvidmode.png" alt="Picture thumbnail in picture or video mode"/></td>
<td><span data-ttu-id="fe6c4-175">Die Miniaturansicht wird auf das quadratische Seitenverhältnis zugeschnitten.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-175">The thumbnail is cropped to a square aspect ratio.</span></span> <br />
<img src="images/thumbnail-pic-doclistmusic-modes.png" alt="Picture thumbnail in documents, music, or list modes"/></td>
<td><span data-ttu-id="fe6c4-176">Für das Miniaturbild wird das ursprüngliche Seitenverhältnis der Datei verwendet.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-176">The thumbnail image uses the original aspect ratio of the file.</span></span><br />
<img src="images/thumbnail-pic-single-mode.png" alt="Picture thumbnail in single mode"/> </td>
</tr>
<tr>
<td><span data-ttu-id="fe6c4-177">Video</span><span class="sxs-lookup"><span data-stu-id="fe6c4-177">Video</span></span></td>
<td><span data-ttu-id="fe6c4-178">Die Miniaturansicht weist ein Symbol auf, wodurch sie sich von Bildern unterscheidet.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-178">The thumbnail has an icon that differentiates it from pictures.</span></span> <br />
<img src="images/thumbnail-vid-picvid-modes.png" alt="Video thumbnail in picture or video mode"/></td>
<td><span data-ttu-id="fe6c4-179">Die Miniaturansicht wird auf das quadratische Seitenverhältnis zugeschnitten.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-179">The thumbnail is cropped to a square aspect ratio.</span></span> <br />
<img src="images/thumbnail-vid-doclistmusic-modes.png" alt="Video thumbnail in documents, music, or list mode"/> </td>
<td><span data-ttu-id="fe6c4-180">Für das Miniaturbild wird das ursprüngliche Seitenverhältnis der Datei verwendet.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-180">The thumbnail image uses the original aspect ratio of the file.</span></span> <br />
<img src="images/thumbnail-vid-single-mode.png" alt="Video thumbnail in single mode"/></td>
</tr>
<tr>
<td><span data-ttu-id="fe6c4-181">Musik</span><span class="sxs-lookup"><span data-stu-id="fe6c4-181">Music</span></span></td>
<td><span data-ttu-id="fe6c4-182">Bei der Miniaturansicht handelt es sich um ein Symbol vor einem Hintergrund entsprechender Größe.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-182">The thumbnail is an icon on a background of appropriate size.</span></span> <span data-ttu-id="fe6c4-183">Die Hintergrundfarbe wird von der Hintergrundfarbe der Kachel der App bestimmt.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-183">The background color is determined by the app's tile background color.</span></span> <br />
<img src="images/thumbnail-music-picvid-modes.png" alt="Music thumbnail in picture or video mode"/></td>
<td><span data-ttu-id="fe6c4-184">Wenn die Datei über ein Albumcover verfügt, entspricht die Miniaturansicht dem Albumcover.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-184">If the file has album art, then the thumbnail is the album art.</span></span>  <br />
<img src="images/thumbnail-music-doclistmusic-modes.png" alt="Music thumbnail in documents, music, or list mode"/> <br />
<span data-ttu-id="fe6c4-185">Andernfalls handelt es sich bei der Miniaturansicht um ein Symbol vor einem Hintergrund entsprechender Größe.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-185">Otherwise, the thumbnail is an icon on a background of appropriate size.</span></span></td>
<td><span data-ttu-id="fe6c4-186">Wenn die Datei über ein Albumcover verfügt, entspricht die Miniaturansicht dem Albumcover mit dem ursprünglichen Seitenverhältnis der Datei.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-186">If the file has album art, then the thumbnail is the album art with the original aspect ratio of the file.</span></span>  <br />
<img src="images/thumbnail-music-single-mode.png" alt="Music thumbnail in single mode"/> <br />
<span data-ttu-id="fe6c4-187">Anderenfalls ist die Miniaturansicht ein Symbol.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-187">Otherwise, the thumbnail is an icon.</span></span> </td>
</tr>
<tr>
<td><span data-ttu-id="fe6c4-188">Dokument</span><span class="sxs-lookup"><span data-stu-id="fe6c4-188">Document</span></span></td>
<td><span data-ttu-id="fe6c4-189">Bei der Miniaturansicht handelt es sich um ein Symbol vor einem Hintergrund entsprechender Größe.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-189">The thumbnail is an icon on a background of appropriate size.</span></span> <span data-ttu-id="fe6c4-190">Die Hintergrundfarbe wird von der Hintergrundfarbe der Kachel der App bestimmt.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-190">The background color is determined by the app's tile background color.</span></span> <br />
<img src="images/thumbnail-docs-picvid-modes.png" alt="Document thumbnail in picture or video mode"/></td>
<td><span data-ttu-id="fe6c4-191">Bei der Miniaturansicht handelt es sich um ein Symbol vor einem Hintergrund entsprechender Größe.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-191">The thumbnail is an icon on a background of appropriate size.</span></span> <span data-ttu-id="fe6c4-192">Die Hintergrundfarbe wird von der Hintergrundfarbe der Kachel der App bestimmt.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-192">The background color is determined by the app's tile background color.</span></span> <br />
<img src="images/thumbnail-doc-doclistmusic-modes.png" alt="Document thumbnail in documents, music, or list mode"/></td>
<td><span data-ttu-id="fe6c4-193">Die Miniaturansicht für das Dokument, sofern vorhanden.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-193">The document thumbnail, if one exists.</span></span> <br />
<img src="images/thumbnail-doc1-single-mode.png" alt="Document thumbnail in single mode"/><br />
<span data-ttu-id="fe6c4-194">Anderenfalls ist die Miniaturansicht ein Symbol.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-194">Otherwise, the thumbnail is an icon.</span></span> <br />
<img src="images/thumbnail-doc2-single-mode.png" alt="Document thumbnail icon in single mode"/></td>
</tr>
<tr>
<td><span data-ttu-id="fe6c4-195">Ordner</span><span class="sxs-lookup"><span data-stu-id="fe6c4-195">Folder</span></span></td>
<td><span data-ttu-id="fe6c4-196">Wenn der Ordner eine Bilddatei enthält, wird die Miniaturansicht für das Bild verwendet.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-196">If there is a picture file in the folder, then the picture thumbnail is used.</span></span>  <br />
<img src="images/thumbnail-dir-picvid-modes.png" alt="Folder thumbnail in picture or video mode"/> <br />
<span data-ttu-id="fe6c4-197">Andernfalls wird keine Miniaturansicht abgerufen.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-197">Otherwise, no thumbnail is retrieved.</span></span></td>
<td><span data-ttu-id="fe6c4-198">Es wird keine Miniaturansicht abgerufen.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-198">No thumbnail image is retrieved.</span></span></td>
<td><span data-ttu-id="fe6c4-199">Das Miniaturbild ist das Ordnersymbol.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-199">The thumbnail is the folder icon.</span></span><br />
<img src="images/thumbnail-dir-single-mode.png" alt="Folder icon thumbnail in single mode"/></td>
</tr>
<tr>
<td><span data-ttu-id="fe6c4-200">Dateigruppe</span><span class="sxs-lookup"><span data-stu-id="fe6c4-200">File group</span></span></td>
<td><span data-ttu-id="fe6c4-201">Wenn der Ordner eine Bilddatei enthält, wird die Miniaturansicht für das Bild verwendet.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-201">If there is a picture file in the folder, then the picture thumbnail is used.</span></span><br />
<img src="images/thumbnail-grp-picvid-modes.png" alt="File group thumbnail in picture or video mode"/> <br /> <span data-ttu-id="fe6c4-202">Andernfalls wird keine Miniaturansicht abgerufen.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-202">Otherwise, no thumbnail is retrieved.</span></span> </td>
<td><span data-ttu-id="fe6c4-203">Wenn die Dateigruppe eine Datei mit einem Albumcover enthält, ist die Miniaturansicht das Albumcover.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-203">If there is a file that has album art among the files in the group, the thumbnail is the album art.</span></span> <br />
<img src="images/thumbnail-grp-doclistmusic-modes.png" alt="File group thumbnail in documents, music or list mode"/> <br /><span data-ttu-id="fe6c4-204">Andernfalls wird keine Miniaturansicht abgerufen.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-204">Otherwise, no thumbnail is retrieved.</span></span> </td>
<td><span data-ttu-id="fe6c4-205">Wenn die Dateigruppe eine Datei mit einem Albumcover enthält, ist die Miniaturansicht das Albumcover und verwendet das ursprüngliche Seitenverhältnis der Datei.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-205">If there is a file that has album art among the files in the group, the thumbnail is the album art and uses the original aspect ratio of the file.</span></span> <br />
<img src="images/thumbnail-grp1-single-mode.png" alt="File group thumbnail in picture or video mode"/> <br /><span data-ttu-id="fe6c4-206">Andernfalls handelt es sich bei der Miniaturansicht um ein Symbol, das eine Gruppe von Dateien darstellt.</span><span class="sxs-lookup"><span data-stu-id="fe6c4-206">Otherwise, the thumbnail is an icon that represents a group of files.</span></span> <br />
<img src="images/thumbnail-grp2-single-mode.png" alt="File group icon in single mode"/> 
</td>
</tr>
</table>
</div>

## <a name="related-topics"></a><span data-ttu-id="fe6c4-207">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="fe6c4-207">Related topics</span></span>
- [<span data-ttu-id="fe6c4-208">ThumbnailMode-Enumeration</span><span class="sxs-lookup"><span data-stu-id="fe6c4-208">ThumbnailMode enum</span></span>](https://docs.microsoft.com/uwp/api/windows.storage.fileproperties.thumbnailmode)
- [<span data-ttu-id="fe6c4-209">StorageItemThumbnail-Klasse</span><span class="sxs-lookup"><span data-stu-id="fe6c4-209">StorageItemThumbnail class</span></span>](https://docs.microsoft.com/uwp/api/Windows.Storage.FileProperties.StorageItemThumbnail)
- [<span data-ttu-id="fe6c4-210">StorageFile-Klasse</span><span class="sxs-lookup"><span data-stu-id="fe6c4-210">StorageFile class</span></span>](https://docs.microsoft.com/uwp/api/windows.storage.storagefile)
- [<span data-ttu-id="fe6c4-211">Beispiel für Datei- und Ordnerminiaturansicht (GitHub)</span><span class="sxs-lookup"><span data-stu-id="fe6c4-211">File and folder thumbnail sample (GitHub)</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/FileThumbnails)
- [<span data-ttu-id="fe6c4-212">Listen- und Rasteransicht</span><span class="sxs-lookup"><span data-stu-id="fe6c4-212">List and grid view</span></span>](../design/controls-and-patterns/lists.md)