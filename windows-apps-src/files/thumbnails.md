---
Description: How to use thumbnail images to help users preview files in UWP apps.
title: Richtlinien für Miniaturbilder in UWP-Apps
label: Thumbnail images
template: detail.hbs
ms.date: 12/19/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 15984e00b036bf44d6e4a7f60cb6435ea1add291
ms.sourcegitcommit: 1cf708443d132306e6c99027662de8ec99177de6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "8980348"
---
# <a name="thumbnail-images"></a><span data-ttu-id="9cba2-103">Miniaturbilder</span><span class="sxs-lookup"><span data-stu-id="9cba2-103">Thumbnail images</span></span>

<span data-ttu-id="9cba2-104">Diese Richtlinien beschreiben, wie Miniaturbilder verwendet werden, um den Benutzern eine Dateivorschau zu bieten, während sie in Ihrer UWP-App navigieren.</span><span class="sxs-lookup"><span data-stu-id="9cba2-104">These guidelines describe how to use thumbnail images to help users preview files as they browse in your UWP app.</span></span> 

**<span data-ttu-id="9cba2-105">Wichtige APIs</span><span class="sxs-lookup"><span data-stu-id="9cba2-105">Important APIs</span></span>**

-   [**<span data-ttu-id="9cba2-106">ThumbnailMode</span><span class="sxs-lookup"><span data-stu-id="9cba2-106">ThumbnailMode</span></span>**](https://docs.microsoft.com/uwp/api/windows.storage.fileproperties.thumbnailmode)

## <a name="should-my-app-include-thumbnails"></a><span data-ttu-id="9cba2-107">Sollte meine App Miniaturansichten beinhalten?</span><span class="sxs-lookup"><span data-stu-id="9cba2-107">Should my app include thumbnails?</span></span>

<span data-ttu-id="9cba2-108">Wenn Ihre App das Durchsuchen von Dateien ermöglicht, können Sie Miniaturbilder anzeigen, damit Benutzer eine schnelle Vorschau auf diese Dateien erhalten.</span><span class="sxs-lookup"><span data-stu-id="9cba2-108">If your app allows users to browse files, you can display thumbnail images to help users quickly preview those files.</span></span> 

<span data-ttu-id="9cba2-109">Verwenden Sie Miniaturansichten für Folgendes:</span><span class="sxs-lookup"><span data-stu-id="9cba2-109">Use thumbnails when:</span></span> 
- <span data-ttu-id="9cba2-110">Anzeigen einer Vorschau für mehrere Elemente in einer Galeriesammlung (beispielsweise Dateien und Ordner)</span><span class="sxs-lookup"><span data-stu-id="9cba2-110">Displaying previews for many items in a gallery collection (like files and folders).</span></span> <span data-ttu-id="9cba2-111">In einer Fotogalerie sollten zum Beispiel Miniaturansichten verwendet werden, um den Benutzern eine kleine Vorschau der einzelnen Bilder anzuzeigen, während sie ihre Fotodateien durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="9cba2-111">For example, a photo gallery should use thumbnails to give users a small view of each picture as they browse through their photo files.</span></span>

    ![Videogalerie](images/thumbnail-gallery.png)

- <span data-ttu-id="9cba2-113">Anzeigen einer Vorschau für ein einzelnes Element in einer Liste (beispielsweise eine bestimmte Datei)</span><span class="sxs-lookup"><span data-stu-id="9cba2-113">Displaying a preview for an individual item in a list (like a specific file).</span></span> <span data-ttu-id="9cba2-114">Möglicherweise möchte ein Benutzer mehr Informationen über eine Datei sehen, darunter eine größere Miniaturansicht für eine bessere Vorschau, bevor er entscheidet, ob er die Datei öffnet.</span><span class="sxs-lookup"><span data-stu-id="9cba2-114">For example, the user may want to see more information about a file, including a larger thumbnail for a better preview, before deciding whether to open the file.</span></span> 

    ![Videovorschau](images/thumbnail-preview.png)

## <a name="dos-and-donts"></a><span data-ttu-id="9cba2-116">Empfohlene und nicht empfohlene Vorgehensweisen</span><span class="sxs-lookup"><span data-stu-id="9cba2-116">Dos and don'ts</span></span>
- <span data-ttu-id="9cba2-117">Geben Sie den [Miniaturansichtsmodus](https://docs.microsoft.com/uwp/api/windows.storage.fileproperties.thumbnailmode) (PicturesView, VideosView, DocumentsView, MusicView, ListView oder SingleItem) an, wenn Sie Miniaturansichten abrufen.</span><span class="sxs-lookup"><span data-stu-id="9cba2-117">Specify the [thumbnail mode](https://docs.microsoft.com/uwp/api/windows.storage.fileproperties.thumbnailmode) (PicturesView, VideosView, DocumentsView, MusicView, ListView, or SingleItem) when you retrieve thumbnails.</span></span> <span data-ttu-id="9cba2-118">So stellen Sie sicher, dass Miniaturbilder für die Anzeige der Dateitypen optimiert sind, die Benutzer anzeigen möchten.</span><span class="sxs-lookup"><span data-stu-id="9cba2-118">This ensures that thumbnail images are optimized to display the type of files users want to see.</span></span> 
    - <span data-ttu-id="9cba2-119">Verwenden Sie den SingleItem-Modus, um unabhängig vom Dateityp eine Miniaturansicht für ein einzelnes Element abzurufen.</span><span class="sxs-lookup"><span data-stu-id="9cba2-119">Use the SingleItem mode to retrieve a thumbnail for a single item, regardless of file type.</span></span> <span data-ttu-id="9cba2-120">Die anderen Miniaturansichtsmodi dienen zum Anzeigen von Vorschauen auf mehrere Dateien.</span><span class="sxs-lookup"><span data-stu-id="9cba2-120">The other thumbnail modes are meant to display previews of multiple files.</span></span> 

- <span data-ttu-id="9cba2-121">Zeigen Sie generische Platzhalterbilder anstelle von Miniaturansichten an, während die Miniaturansichten geladen werden.</span><span class="sxs-lookup"><span data-stu-id="9cba2-121">Display generic placeholder images in place of thumbnails while thumbnails load.</span></span> <span data-ttu-id="9cba2-122">Wenn Sie Platzhalter auf diese Weise verwenden, scheint die App besser zu reagieren, da Benutzer mit Vorschauen interagieren können, bevor die Miniaturansicht geladen ist.</span><span class="sxs-lookup"><span data-stu-id="9cba2-122">Using placeholders helps your app seem more responsive because users can interact with previews before the thumbnail load.</span></span> 

    <span data-ttu-id="9cba2-123">Platzhalterbilder sollten folgende Merkmale aufweisen:</span><span class="sxs-lookup"><span data-stu-id="9cba2-123">Placeholder images should be:</span></span>
    * <span data-ttu-id="9cba2-124">Sie sollten sich konkret auf die Art des Elements beziehen, das sie darstellen.</span><span class="sxs-lookup"><span data-stu-id="9cba2-124">Specific to the kind of item that it stands in for.</span></span> <span data-ttu-id="9cba2-125">Beispielsweise sollten Ordner, Bilder und Videos alle eigene spezielle Platzhalter haben.</span><span class="sxs-lookup"><span data-stu-id="9cba2-125">For example, folders, pictures, and videos should all have their own specialized placeholders.</span></span> 
    * <span data-ttu-id="9cba2-126">Sie sollten die gleiche Größe und das gleiche Seitenverhältnis aufweisen wie das Miniaturbild, das sie darstellen.</span><span class="sxs-lookup"><span data-stu-id="9cba2-126">The same size and aspect ratio as the thumbnail image it stands in for.</span></span> 
    * <span data-ttu-id="9cba2-127">Sie sollten angezeigt werden, bis das Miniaturbild geladen ist.</span><span class="sxs-lookup"><span data-stu-id="9cba2-127">Displayed until the thumbnail image is loaded.</span></span> 

- <span data-ttu-id="9cba2-128">Verwenden Sie Platzhalterbilder mit Beschriftungen, um Ordner oder Dateigruppen darzustellen und von einzelnen Dateien zu unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="9cba2-128">Use placeholder images with text labels to represent folders and file groups to differentiate from individual files.</span></span>

- <span data-ttu-id="9cba2-129">Wenn Sie eine Miniaturansicht nicht abrufen können, zeigen Sie stattdessen ein Platzhalterbild an.</span><span class="sxs-lookup"><span data-stu-id="9cba2-129">If you can't retrieve a thumbnail, display a placeholder image.</span></span> 

- <span data-ttu-id="9cba2-130">Zeigen Sie zusätzliche Dateiinformationen an, wenn Sie Vorschauen für Dokumente und Musikdateien bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="9cba2-130">Display additional file information when providing previews for document and music files.</span></span> <span data-ttu-id="9cba2-131">Benutzer können dann wichtige Informationen über eine Datei identifizieren, die durch ein Miniaturbild allein möglicherweise nicht vermittelt werden.</span><span class="sxs-lookup"><span data-stu-id="9cba2-131">Users can then identify key information about a file that might not be readily available from a thumbnail image alone.</span></span> <span data-ttu-id="9cba2-132">Beispielsweise können Sie für eine Musikdatei neben der Miniaturansicht des Albumcovers auch den Namen des Interpreten anzeigen.</span><span class="sxs-lookup"><span data-stu-id="9cba2-132">For example, for a music file, you might display the name of the artist along with the thumbnail of the album art.</span></span> 

- <span data-ttu-id="9cba2-133">Zeigen Sie für Bild- und Videodateien keine zusätzlichen Dateiinformationen an.</span><span class="sxs-lookup"><span data-stu-id="9cba2-133">Don't display additional file info for picture and video files.</span></span> <span data-ttu-id="9cba2-134">In den meisten Fällen ist ein Miniaturbild ausreichend für Benutzer, die Bilder und Videos durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="9cba2-134">In most cases, a thumbnail image is sufficient for users browsing through pictures and videos.</span></span> 

## <a name="additional-usage-guidelines"></a><span data-ttu-id="9cba2-135">Weitere Richtlinien zur Verwendung</span><span class="sxs-lookup"><span data-stu-id="9cba2-135">Additional usage guidelines</span></span>
<span data-ttu-id="9cba2-136">Empfohlene [Miniaturansichtsmodi](https://docs.microsoft.com/uwp/api/windows.storage.fileproperties.thumbnailmode) und deren Features:</span><span class="sxs-lookup"><span data-stu-id="9cba2-136">Recommended [thumbnail modes](https://docs.microsoft.com/uwp/api/windows.storage.fileproperties.thumbnailmode) and their features:</span></span>

<table>
<tr>
<th> <span data-ttu-id="9cba2-137">Vorschauanzeige für</span><span class="sxs-lookup"><span data-stu-id="9cba2-137">Display previews for</span></span></th>
<th> <span data-ttu-id="9cba2-138">Miniaturansichtsmodi</span><span class="sxs-lookup"><span data-stu-id="9cba2-138">Thumbnail modes</span></span> </th>
<th> <span data-ttu-id="9cba2-139">Features der abgerufenen Miniaturansichten</span><span class="sxs-lookup"><span data-stu-id="9cba2-139">Features of the retrieved thumbnail images</span></span> </th>
</tr>
<tr>
<td> <span data-ttu-id="9cba2-140">Bilder</span><span class="sxs-lookup"><span data-stu-id="9cba2-140">Pictures</span></span><br /> <span data-ttu-id="9cba2-141">Videos</span><span class="sxs-lookup"><span data-stu-id="9cba2-141">Videos</span></span> </td>
<td> <span data-ttu-id="9cba2-142">PicturesView</span><span class="sxs-lookup"><span data-stu-id="9cba2-142">PicturesView</span></span> <br /><span data-ttu-id="9cba2-143">VideosView</span><span class="sxs-lookup"><span data-stu-id="9cba2-143">VideosView</span></span> </td>
<td> <span data-ttu-id="9cba2-144"><b>Größe</b>: Mittel, vorzugsweise mindestens 190 (bei einer Bildgröße von 190x130)</span><span class="sxs-lookup"><span data-stu-id="9cba2-144"><b>Size</b>: Medium, preferably at least 190 (if the image size is 190x130)</span></span> <br /><span data-ttu-id="9cba2-145">
<b>Seitenverhältnis</b>:Gleichmäßiges, breites Seitenverhältnis von ca. 0,7 (190x130 bei einer Größe von 190)</span><span class="sxs-lookup"><span data-stu-id="9cba2-145">
<b>Aspect ratio</b>: Uniform, wide aspect ratio of about .7 (190x130 if the size is 190)</span></span> <br />
<span data-ttu-id="9cba2-146">Zugeschnitten für die Vorschau</span><span class="sxs-lookup"><span data-stu-id="9cba2-146">Cropped for previews.</span></span> <br /> 
<span data-ttu-id="9cba2-147">Gute Ausrichtung von Bildern in einem Raster durch einheitliches Seitenverhältnis</span><span class="sxs-lookup"><span data-stu-id="9cba2-147">Good for aligning images in a grid because of uniform aspect ratio.</span></span>  </td>
</tr>
<tr>
<td> <span data-ttu-id="9cba2-148">Dokumente</span><span class="sxs-lookup"><span data-stu-id="9cba2-148">Documents</span></span><br /><span data-ttu-id="9cba2-149">Musik</span><span class="sxs-lookup"><span data-stu-id="9cba2-149">Music</span></span> </td>
<td> <span data-ttu-id="9cba2-150">DocumentsView</span><span class="sxs-lookup"><span data-stu-id="9cba2-150">DocumentsView</span></span> <br /><span data-ttu-id="9cba2-151">MusicView</span><span class="sxs-lookup"><span data-stu-id="9cba2-151">MusicView</span></span> <br /> <span data-ttu-id="9cba2-152">ListView</span><span class="sxs-lookup"><span data-stu-id="9cba2-152">ListView</span></span></td>
<td> <span data-ttu-id="9cba2-153"><b>Größe</b>: Klein, vorzugsweise mindestens 40 x 40 Pixel</span><span class="sxs-lookup"><span data-stu-id="9cba2-153"><b>Size</b>: Small, preferably at least 40 x 40 pixels</span></span> <br /><span data-ttu-id="9cba2-154">
<b>Seitenverhältnis:</b> Einheitliches, quadratisches Seitenverhältnis</span><span class="sxs-lookup"><span data-stu-id="9cba2-154">
<b>Aspect ratio</b>:  Uniform, square aspect ratio</span></span>  <br />
<span data-ttu-id="9cba2-155">Aufgrund des quadratischen Seitenverhältnisses gut geeignet für die Vorschau von Albumcovern</span><span class="sxs-lookup"><span data-stu-id="9cba2-155">Good for previewing album art because of the square aspect ratio.</span></span> <br /> 
<span data-ttu-id="9cba2-156">Dokumente sehen ebenso aus wie in einem Dateiauswahlfenster (Verwendung derselben Symbole).</span><span class="sxs-lookup"><span data-stu-id="9cba2-156">Documents look the same as they look in a file picker window (it uses the same icons).</span></span> </td>
</tr>
</tr>
<tr>
<td> <span data-ttu-id="9cba2-157">Alle einzelnen Elemente (unabhängig vom Dateityp)</span><span class="sxs-lookup"><span data-stu-id="9cba2-157">Any single item (regardless of file type)</span></span> </td>
<td> <span data-ttu-id="9cba2-158">SingleItem</span><span class="sxs-lookup"><span data-stu-id="9cba2-158">SingleItem</span></span> </td>
<td> <span data-ttu-id="9cba2-159"><b>Größe</b>: Klein, vorzugsweise mindestens 40 x 40 Pixel</span><span class="sxs-lookup"><span data-stu-id="9cba2-159"><b>Size</b>: Small, preferably at least 40 x 40 pixels</span></span> <br /><span data-ttu-id="9cba2-160">
<b>Seitenverhältnis:</b> Einheitliches, quadratisches Seitenverhältnis</span><span class="sxs-lookup"><span data-stu-id="9cba2-160">
<b>Aspect ratio</b>:  Uniform, square aspect ratio</span></span>  <br />
<span data-ttu-id="9cba2-161">Aufgrund des quadratischen Seitenverhältnisses gut geeignet für die Vorschau von Albumcovern</span><span class="sxs-lookup"><span data-stu-id="9cba2-161">Good for previewing album art because of the square aspect ratio.</span></span> <br /> 
<span data-ttu-id="9cba2-162">Dokumente sehen ebenso aus wie in einem Dateiauswahlfenster (Verwendung derselben Symbole).</span><span class="sxs-lookup"><span data-stu-id="9cba2-162">Documents look the same as they look in a file picker window (it uses the same icons).</span></span> </td>
</tr>
</table>

<span data-ttu-id="9cba2-163">Hier sehen Sie Beispiele dafür, wie sich abgerufene Miniaturbilder je nach Dateityp und Miniaturansichtsmodus unterscheiden:</span><span class="sxs-lookup"><span data-stu-id="9cba2-163">Here are examples showing how retrieved thumbnail images differ depending on file type and thumbnail mode:</span></span>
<div class="mx-responsive-img">
<table>
<tr>
<th><span data-ttu-id="9cba2-164">Elementtyp</span><span class="sxs-lookup"><span data-stu-id="9cba2-164">Item type</span></span></th>
<th><span data-ttu-id="9cba2-165">Beim Abruf mithilfe von:</span><span class="sxs-lookup"><span data-stu-id="9cba2-165">When retrieved using:</span></span> <ul><li><span data-ttu-id="9cba2-166">PicturesView</span><span class="sxs-lookup"><span data-stu-id="9cba2-166">PicturesView</span></span> <li><span data-ttu-id="9cba2-167">VideosView</span><span class="sxs-lookup"><span data-stu-id="9cba2-167">VideosView</span></span></ul></th>
<th><span data-ttu-id="9cba2-168">Beim Abruf mithilfe von:</span><span class="sxs-lookup"><span data-stu-id="9cba2-168">When retrieved using:</span></span> <ul><li><span data-ttu-id="9cba2-169">DocumentsView</span><span class="sxs-lookup"><span data-stu-id="9cba2-169">DocumentsView</span></span> <li><span data-ttu-id="9cba2-170">MusicView</span><span class="sxs-lookup"><span data-stu-id="9cba2-170">MusicView</span></span> <li><span data-ttu-id="9cba2-171">ListView</span><span class="sxs-lookup"><span data-stu-id="9cba2-171">ListView</span></span></ul></th>
<th><span data-ttu-id="9cba2-172">Beim Abruf mithilfe von:</span><span class="sxs-lookup"><span data-stu-id="9cba2-172">When retrieved using:</span></span> <ul><li><span data-ttu-id="9cba2-173">SingleItem</span><span class="sxs-lookup"><span data-stu-id="9cba2-173">SingleItem</span></span></ul></th>
<tr>
<tr>
<td><span data-ttu-id="9cba2-174">Picture</span><span class="sxs-lookup"><span data-stu-id="9cba2-174">Picture</span></span></td>
<td><span data-ttu-id="9cba2-175">Für das Miniaturbild wird das ursprüngliche Seitenverhältnis der Datei verwendet.</span><span class="sxs-lookup"><span data-stu-id="9cba2-175">The thumbnail image uses the original aspect ratio of the file.</span></span> <br />
<img src="images/thumbnail-pic-picvidmode.png" alt="Picture thumbnail in picture or video mode"/></td>
<td><span data-ttu-id="9cba2-176">Die Miniaturansicht wird auf das quadratische Seitenverhältnis zugeschnitten.</span><span class="sxs-lookup"><span data-stu-id="9cba2-176">The thumbnail is cropped to a square aspect ratio.</span></span> <br />
<img src="images/thumbnail-pic-doclistmusic-modes.png" alt="Picture thumbnail in documents, music, or list modes"/></td>
<td><span data-ttu-id="9cba2-177">Für das Miniaturbild wird das ursprüngliche Seitenverhältnis der Datei verwendet.</span><span class="sxs-lookup"><span data-stu-id="9cba2-177">The thumbnail image uses the original aspect ratio of the file.</span></span><br />
<img src="images/thumbnail-pic-single-mode.png" alt="Picture thumbnail in single mode"/> </td>
</tr>
<tr>
<td><span data-ttu-id="9cba2-178">Video</span><span class="sxs-lookup"><span data-stu-id="9cba2-178">Video</span></span></td>
<td><span data-ttu-id="9cba2-179">Die Miniaturansicht weist ein Symbol auf, wodurch sie sich von Bildern unterscheidet.</span><span class="sxs-lookup"><span data-stu-id="9cba2-179">The thumbnail has an icon that differentiates it from pictures.</span></span> <br />
<img src="images/thumbnail-vid-picvid-modes.png" alt="Video thumbnail in picture or video mode"/></td>
<td><span data-ttu-id="9cba2-180">Die Miniaturansicht wird auf das quadratische Seitenverhältnis zugeschnitten.</span><span class="sxs-lookup"><span data-stu-id="9cba2-180">The thumbnail is cropped to a square aspect ratio.</span></span> <br />
<img src="images/thumbnail-vid-doclistmusic-modes.png" alt="Video thumbnail in documents, music, or list mode"/> </td>
<td><span data-ttu-id="9cba2-181">Für das Miniaturbild wird das ursprüngliche Seitenverhältnis der Datei verwendet.</span><span class="sxs-lookup"><span data-stu-id="9cba2-181">The thumbnail image uses the original aspect ratio of the file.</span></span> <br />
<img src="images/thumbnail-vid-single-mode.png" alt="Video thumbnail in single mode"/></td>
</tr>
<tr>
<td><span data-ttu-id="9cba2-182">Musik</span><span class="sxs-lookup"><span data-stu-id="9cba2-182">Music</span></span></td>
<td><span data-ttu-id="9cba2-183">Bei der Miniaturansicht handelt es sich um ein Symbol vor einem Hintergrund entsprechender Größe.</span><span class="sxs-lookup"><span data-stu-id="9cba2-183">The thumbnail is an icon on a background of appropriate size.</span></span> <span data-ttu-id="9cba2-184">Die Hintergrundfarbe wird von der Hintergrundfarbe der Kachel der App bestimmt.</span><span class="sxs-lookup"><span data-stu-id="9cba2-184">The background color is determined by the app's tile background color.</span></span> <br />
<img src="images/thumbnail-music-picvid-modes.png" alt="Music thumbnail in picture or video mode"/></td>
<td><span data-ttu-id="9cba2-185">Wenn die Datei über ein Albumcover verfügt, entspricht die Miniaturansicht dem Albumcover.</span><span class="sxs-lookup"><span data-stu-id="9cba2-185">If the file has album art, then the thumbnail is the album art.</span></span>  <br />
<img src="images/thumbnail-music-doclistmusic-modes.png" alt="Music thumbnail in documents, music, or list mode"/> <br />
<span data-ttu-id="9cba2-186">Andernfalls handelt es sich bei der Miniaturansicht um ein Symbol vor einem Hintergrund entsprechender Größe.</span><span class="sxs-lookup"><span data-stu-id="9cba2-186">Otherwise, the thumbnail is an icon on a background of appropriate size.</span></span></td>
<td><span data-ttu-id="9cba2-187">Wenn die Datei über ein Albumcover verfügt, entspricht die Miniaturansicht dem Albumcover mit dem ursprünglichen Seitenverhältnis der Datei.</span><span class="sxs-lookup"><span data-stu-id="9cba2-187">If the file has album art, then the thumbnail is the album art with the original aspect ratio of the file.</span></span>  <br />
<img src="images/thumbnail-music-single-mode.png" alt="Music thumbnail in single mode"/> <br />
<span data-ttu-id="9cba2-188">Anderenfalls ist die Miniaturansicht ein Symbol.</span><span class="sxs-lookup"><span data-stu-id="9cba2-188">Otherwise, the thumbnail is an icon.</span></span> </td>
</tr>
<tr>
<td><span data-ttu-id="9cba2-189">Dokument</span><span class="sxs-lookup"><span data-stu-id="9cba2-189">Document</span></span></td>
<td><span data-ttu-id="9cba2-190">Bei der Miniaturansicht handelt es sich um ein Symbol vor einem Hintergrund entsprechender Größe.</span><span class="sxs-lookup"><span data-stu-id="9cba2-190">The thumbnail is an icon on a background of appropriate size.</span></span> <span data-ttu-id="9cba2-191">Die Hintergrundfarbe wird von der Hintergrundfarbe der Kachel der App bestimmt.</span><span class="sxs-lookup"><span data-stu-id="9cba2-191">The background color is determined by the app's tile background color.</span></span> <br />
<img src="images/thumbnail-docs-picvid-modes.png" alt="Document thumbnail in picture or video mode"/></td>
<td><span data-ttu-id="9cba2-192">Bei der Miniaturansicht handelt es sich um ein Symbol vor einem Hintergrund entsprechender Größe.</span><span class="sxs-lookup"><span data-stu-id="9cba2-192">The thumbnail is an icon on a background of appropriate size.</span></span> <span data-ttu-id="9cba2-193">Die Hintergrundfarbe wird von der Hintergrundfarbe der Kachel der App bestimmt.</span><span class="sxs-lookup"><span data-stu-id="9cba2-193">The background color is determined by the app's tile background color.</span></span> <br />
<img src="images/thumbnail-doc-doclistmusic-modes.png" alt="Document thumbnail in documents, music, or list mode"/></td>
<td><span data-ttu-id="9cba2-194">Die Miniaturansicht für das Dokument, sofern vorhanden.</span><span class="sxs-lookup"><span data-stu-id="9cba2-194">The document thumbnail, if one exists.</span></span> <br />
<img src="images/thumbnail-doc1-single-mode.png" alt="Document thumbnail in single mode"/><br />
<span data-ttu-id="9cba2-195">Anderenfalls ist die Miniaturansicht ein Symbol.</span><span class="sxs-lookup"><span data-stu-id="9cba2-195">Otherwise, the thumbnail is an icon.</span></span> <br />
<img src="images/thumbnail-doc2-single-mode.png" alt="Document thumbnail icon in single mode"/></td>
</tr>
<tr>
<td><span data-ttu-id="9cba2-196">Ordner</span><span class="sxs-lookup"><span data-stu-id="9cba2-196">Folder</span></span></td>
<td><span data-ttu-id="9cba2-197">Wenn der Ordner eine Bilddatei enthält, wird die Miniaturansicht für das Bild verwendet.</span><span class="sxs-lookup"><span data-stu-id="9cba2-197">If there is a picture file in the folder, then the picture thumbnail is used.</span></span>  <br />
<img src="images/thumbnail-dir-picvid-modes.png" alt="Folder thumbnail in picture or video mode"/> <br />
<span data-ttu-id="9cba2-198">Andernfalls wird keine Miniaturansicht abgerufen.</span><span class="sxs-lookup"><span data-stu-id="9cba2-198">Otherwise, no thumbnail is retrieved.</span></span></td>
<td><span data-ttu-id="9cba2-199">Es wird keine Miniaturansicht abgerufen.</span><span class="sxs-lookup"><span data-stu-id="9cba2-199">No thumbnail image is retrieved.</span></span></td>
<td><span data-ttu-id="9cba2-200">Das Miniaturbild ist das Ordnersymbol.</span><span class="sxs-lookup"><span data-stu-id="9cba2-200">The thumbnail is the folder icon.</span></span><br />
<img src="images/thumbnail-dir-single-mode.png" alt="Folder icon thumbnail in single mode"/></td>
</tr>
<tr>
<td><span data-ttu-id="9cba2-201">Dateigruppe</span><span class="sxs-lookup"><span data-stu-id="9cba2-201">File group</span></span></td>
<td><span data-ttu-id="9cba2-202">Wenn der Ordner eine Bilddatei enthält, wird die Miniaturansicht für das Bild verwendet.</span><span class="sxs-lookup"><span data-stu-id="9cba2-202">If there is a picture file in the folder, then the picture thumbnail is used.</span></span><br />
<img src="images/thumbnail-grp-picvid-modes.png" alt="File group thumbnail in picture or video mode"/> <br /> <span data-ttu-id="9cba2-203">Andernfalls wird keine Miniaturansicht abgerufen.</span><span class="sxs-lookup"><span data-stu-id="9cba2-203">Otherwise, no thumbnail is retrieved.</span></span> </td>
<td><span data-ttu-id="9cba2-204">Wenn die Dateigruppe eine Datei mit einem Albumcover enthält, ist die Miniaturansicht das Albumcover.</span><span class="sxs-lookup"><span data-stu-id="9cba2-204">If there is a file that has album art among the files in the group, the thumbnail is the album art.</span></span> <br />
<img src="images/thumbnail-grp-doclistmusic-modes.png" alt="File group thumbnail in documents, music or list mode"/> <br /><span data-ttu-id="9cba2-205">Andernfalls wird keine Miniaturansicht abgerufen.</span><span class="sxs-lookup"><span data-stu-id="9cba2-205">Otherwise, no thumbnail is retrieved.</span></span> </td>
<td><span data-ttu-id="9cba2-206">Wenn die Dateigruppe eine Datei mit einem Albumcover enthält, ist die Miniaturansicht das Albumcover und verwendet das ursprüngliche Seitenverhältnis der Datei.</span><span class="sxs-lookup"><span data-stu-id="9cba2-206">If there is a file that has album art among the files in the group, the thumbnail is the album art and uses the original aspect ratio of the file.</span></span> <br />
<img src="images/thumbnail-grp1-single-mode.png" alt="File group thumbnail in picture or video mode"/> <br /><span data-ttu-id="9cba2-207">Andernfalls handelt es sich bei der Miniaturansicht um ein Symbol, das eine Gruppe von Dateien darstellt.</span><span class="sxs-lookup"><span data-stu-id="9cba2-207">Otherwise, the thumbnail is an icon that represents a group of files.</span></span> <br />
<img src="images/thumbnail-grp2-single-mode.png" alt="File group icon in single mode"/> 
</td>
</tr>
</table>
</div>

## <a name="related-topics"></a><span data-ttu-id="9cba2-208">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="9cba2-208">Related topics</span></span>
- [<span data-ttu-id="9cba2-209">ThumbnailMode-Enumeration</span><span class="sxs-lookup"><span data-stu-id="9cba2-209">ThumbnailMode enum</span></span>](https://docs.microsoft.com/uwp/api/windows.storage.fileproperties.thumbnailmode)
- [<span data-ttu-id="9cba2-210">StorageItemThumbnail-Klasse</span><span class="sxs-lookup"><span data-stu-id="9cba2-210">StorageItemThumbnail class</span></span>](https://docs.microsoft.com/uwp/api/Windows.Storage.FileProperties.StorageItemThumbnail)
- [<span data-ttu-id="9cba2-211">StorageFile-Klasse</span><span class="sxs-lookup"><span data-stu-id="9cba2-211">StorageFile class</span></span>](https://docs.microsoft.com/uwp/api/windows.storage.storagefile)
- [<span data-ttu-id="9cba2-212">Beispiel für Datei- und Ordnerminiaturansicht (GitHub)</span><span class="sxs-lookup"><span data-stu-id="9cba2-212">File and folder thumbnail sample (GitHub)</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/FileThumbnails)
- [<span data-ttu-id="9cba2-213">Listen- und Rasteransicht</span><span class="sxs-lookup"><span data-stu-id="9cba2-213">List and grid view</span></span>](../design/controls-and-patterns/lists.md)