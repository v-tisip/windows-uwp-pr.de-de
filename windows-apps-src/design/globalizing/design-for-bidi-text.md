---
Description: Design your app to provide bidirectional text support (BiDi) so that you can combine script from left-to-right (LTR) and right-to-left (RTL) writing systems, which generally contain different types of alphabets.
title: Entwerfen einer App für bidirektionalen Text
template: detail.hbs
ms.date: 11/10/2017
ms.topic: article
keywords: Windows 10, UWP, Globalisierung, Lokalisierbarkeit, Lokalisierung, rtl, ltr
ms.localizationpriority: medium
ms.openlocfilehash: 66a158a96fcab5391030f4517b6420ba4585bf04
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8896945"
---
# <a name="design-your-app-for-bidirectional-text"></a><span data-ttu-id="82785-103">Entwerfen der App für bidirektionalen Text</span><span class="sxs-lookup"><span data-stu-id="82785-103">Design your app for bidirectional text</span></span>

<span data-ttu-id="82785-104">Entwerfen Sie Ihre App so, dass bidirektionale Textunterstützung (BiDi) bereitgestellt wird, sodass Sie Texte von rechts nach links (RTL) und von links nach rechts (LTR) kombinieren können, die im Allgemeinen unterschiedliche Alphabete enthalten.</span><span class="sxs-lookup"><span data-stu-id="82785-104">Design your app to provide bidirectional text support (BiDi) so that you can combine script from right to left (RTL) and left to right (LTR) writing systems, which generally contain different types of alphabets.</span></span>

<span data-ttu-id="82785-105">Rechts-nach-links-Schriftsysteme, wie sie im Nahen Osten, in Zentral- und Südasien und in Afrika verwendet werden, haben besondere Designanforderungen.</span><span class="sxs-lookup"><span data-stu-id="82785-105">Right-to-left writing systems, such as those used in the Middle East, Central and South Asia, and in Africa, have unique design requirements.</span></span> <span data-ttu-id="82785-106">Diese Schreibsysteme erfordern Unterstützung von bidirektionalem Text (BiDi).</span><span class="sxs-lookup"><span data-stu-id="82785-106">These writing systems require bidirectional text support (BiDi).</span></span> <span data-ttu-id="82785-107">Bei BiDi-Unterstützung handelt es sich um die Möglichkeit, Text sowohl von rechts nach links (RTL) als auch von links nach rechts (LTR) einzugeben und anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="82785-107">BiDi support is the ability to input and display text layout in either right to left (RTL) or left to right (LTR) order.</span></span>

<span data-ttu-id="82785-108">In Windows werden insgesamt neun BiDi-Sprachen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="82785-108">A total of nine BiDi languages are included with Windows.</span></span>
- <span data-ttu-id="82785-109">Zwei vollständig lokalisierte Sprachen.</span><span class="sxs-lookup"><span data-stu-id="82785-109">Two fully localized languages.</span></span> <span data-ttu-id="82785-110">Arabisch und Hebräisch.</span><span class="sxs-lookup"><span data-stu-id="82785-110">Arabic, and Hebrew.</span></span>
- <span data-ttu-id="82785-111">Sieben Benutzeroberflächen-Sprachpakete für aufstrebende Märkte.</span><span class="sxs-lookup"><span data-stu-id="82785-111">Seven Language Interface Packs for emerging markets.</span></span> <span data-ttu-id="82785-112">Persisch, Urdu, Dari, Zentralkurdisch, Sindhi, Punjabi (Pakistan) und Uigurisch.</span><span class="sxs-lookup"><span data-stu-id="82785-112">Persian, Urdu, Dari, Central Kurdish, Sindhi, Punjabi (Pakistan), and Uyghur.</span></span>

<span data-ttu-id="82785-113">Dieses Thema enthält die Design-Philosophie von Windows BiDi und Fallstudien mit Überlegungen zum BiDi-Design.</span><span class="sxs-lookup"><span data-stu-id="82785-113">This topic contains the Windows BiDi design philosophy, and case studies that show BiDi design considerations.</span></span>

## <a name="bidi-design-elements"></a><span data-ttu-id="82785-114">Bidirektionale Gestaltungselemente</span><span class="sxs-lookup"><span data-stu-id="82785-114">Bidi design elements</span></span>

<span data-ttu-id="82785-115">Die BiDi-Gestaltung in Windows wird von 4 Prinzipien bestimmt.</span><span class="sxs-lookup"><span data-stu-id="82785-115">Four elements influence BiDi design decisions in Windows.</span></span>

- <span data-ttu-id="82785-116">**Spiegeln der Benutzeroberfläche (UI)**.</span><span class="sxs-lookup"><span data-stu-id="82785-116">**User interface (UI) mirroring**.</span></span> <span data-ttu-id="82785-117">Der Benutzeroberflächenfluss ermöglicht die Darstellung von Inhalten mit Leserichtung von rechts nach links in einem einheitlichen Layout.</span><span class="sxs-lookup"><span data-stu-id="82785-117">User interface (UI) flow allows right-to-left content to be presented in its native layout.</span></span> <span data-ttu-id="82785-118">Die Benutzeroberfläche für Länder mit BiDi-Sprachen orientiert sich an den örtlichen Konventionen.</span><span class="sxs-lookup"><span data-stu-id="82785-118">UI design feels local to BiDi markets.</span></span>
- <span data-ttu-id="82785-119">**Einheitliche Benutzererfahrung**.</span><span class="sxs-lookup"><span data-stu-id="82785-119">**Consistency in user experience**.</span></span> <span data-ttu-id="82785-120">Ein Design wird in der Ausrichtung von rechts nach links als natürlich empfunden.</span><span class="sxs-lookup"><span data-stu-id="82785-120">The design feels natural in right-to-left orientation.</span></span> <span data-ttu-id="82785-121">Die Elemente der Benutzeroberfläche weisen eine einheitliche Layoutrichtung auf und werden so dargestellt, wie der Benutzer dies erwartet.</span><span class="sxs-lookup"><span data-stu-id="82785-121">UI elements share a consistent layout direction and appear as the user expects them.</span></span>
- <span data-ttu-id="82785-122">**Optimierung der Fingereingabe**.</span><span class="sxs-lookup"><span data-stu-id="82785-122">**Touch optimization**.</span></span> <span data-ttu-id="82785-123">Wie in nicht gespiegelten Benutzeroberflächen sind alle Elemente leicht zugänglich und ermöglichen eine natürliche Interaktion per Toucheingabe.</span><span class="sxs-lookup"><span data-stu-id="82785-123">Similar to touch UI in non-mirrored UI, elements are easy to reach, and they natural to touch interaction.</span></span>
- <span data-ttu-id="82785-124">**Unterstützung für gemischten Text**.</span><span class="sxs-lookup"><span data-stu-id="82785-124">**Mixed text support**.</span></span> <span data-ttu-id="82785-125">Die Unterstützung verschiedener Textausrichtungen erlaubt eine weitgehende Mischung von Textrichtungen (deutscher Text in BiDi-Builds und umgekehrt).</span><span class="sxs-lookup"><span data-stu-id="82785-125">Text directionality support enables great mixed text presentation (English text on BiDi builds, and vice versa).</span></span>

## <a name="feature-design-overview"></a><span data-ttu-id="82785-126">Überblick über die Gestaltungselemente</span><span class="sxs-lookup"><span data-stu-id="82785-126">Feature design overview</span></span>

<span data-ttu-id="82785-127">Windows unterstützt vier BiDi-Gestaltungselemente.</span><span class="sxs-lookup"><span data-stu-id="82785-127">Windows supports the four BiDi design elements.</span></span> <span data-ttu-id="82785-128">Wir betrachten nun einige der wichtigsten Features in Windows und erläutern, wie sie sich auf Ihre App auswirken.</span><span class="sxs-lookup"><span data-stu-id="82785-128">Let's look at some of the major relevant features in Windows, and provide some context around how they affect your app.</span></span>

### <a name="navigate-in-the-direction-that-feels-natural"></a><span data-ttu-id="82785-129">Navigieren in die gewohnte Richtung</span><span class="sxs-lookup"><span data-stu-id="82785-129">Navigate in the direction that feels natural</span></span>

<span data-ttu-id="82785-130">Windows passt die Richtung des typografischen Rasters so an, dass es von rechts nach links verläuft, d. h. die erste Kachel im Raster befindet sich in der oberen rechten Ecke und die letzte Kachel unten links.</span><span class="sxs-lookup"><span data-stu-id="82785-130">Windows adjusts the direction of the typographic grid so that it flows from right to left, meaning that the first tile on the grid is placed at the top right corner, and the last tile at the bottom left.</span></span> <span data-ttu-id="82785-131">Dies entspricht dem RTL-Muster von gedruckten Publikationen wie Büchern und Zeitschriften. Darin wird auch von rechts oben nach links unten gelesen.</span><span class="sxs-lookup"><span data-stu-id="82785-131">This matches the RTL pattern of printed publications such as books and magazines, where the reading pattern always starts at the top right corner and progresses to the left.</span></span>

![<span data-ttu-id="82785-132">BiDi-Startmenü](images/56283_BIDI_01_startscreen_resized.png)
![BiDi-Startmenü mit Charms</span><span class="sxs-lookup"><span data-stu-id="82785-132">BiDi start menu](images/56283_BIDI_01_startscreen_resized.png)
![BiDi start menu with charms</span></span>](images/56283_BIDI_02_startscreen_charm_resized.png)

<span data-ttu-id="82785-133">Um einen einheitlichen Benutzeroberflächenfluss sicherzustellen, behalten die Kachelinhalte im Raster immer ihre Ausrichtung von rechts nach links bei. Der Name Ihrer App und das Logo werden daher unabhängig von der Sprache der Benutzeroberfläche Ihrer App immer rechts unten auf der Kachel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="82785-133">To preserve a consistent UI flow, content on tiles retain a right-to-left layout, meaning that the app name and logo are positioned at the bottom right corner of the tile regardless of the app UI language.</span></span>

#### <a name="bidi-tile"></a><span data-ttu-id="82785-134">BiDi-Kachel</span><span class="sxs-lookup"><span data-stu-id="82785-134">BiDi tile</span></span>

![BiDi-Kachel](images/56284_BIDI_03_tile_callouts_withKey.png)

#### <a name="english-tile"></a><span data-ttu-id="82785-136">Englische Kachel</span><span class="sxs-lookup"><span data-stu-id="82785-136">English tile</span></span>

![Englische Kachel](images/56284_BIDI_03_tile_callouts_en-us.png)

### <a name="get-tile-notifications-that-read-correctly"></a><span data-ttu-id="82785-138">Ordnungsgemäß zu lesende Kachelbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="82785-138">Get tile notifications that read correctly</span></span>

<span data-ttu-id="82785-139">Kacheln unterstützen gemischte Texte.</span><span class="sxs-lookup"><span data-stu-id="82785-139">Tiles have mixed text support.</span></span> <span data-ttu-id="82785-140">Der Benachrichtigungsbereich weist eine integrierte Flexibilität auf, sodass die Textausrichtung an die jeweils verwendete Sprache angepasst werden kann.</span><span class="sxs-lookup"><span data-stu-id="82785-140">The notification region has built-in flexibility to adjust the text alignment based on the notification language.</span></span>  <span data-ttu-id="82785-141">Wenn eine App Benachrichtigungen in einer BiDi-Sprache wie Arabisch oder Hebräisch sendet, wird der Text rechts ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="82785-141">When an app sends Arabic, Hebrew, or other BiDi language notifications, the text is aligned to the right.</span></span> <span data-ttu-id="82785-142">Und wenn eine Benachrichtigung in Englisch (oder einer anderen LTR-Sprache) eingeht, wird sie am linken Rand ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="82785-142">And when an English (or other LTR) notification arrives, it will align to the left.</span></span>

![Kachelbenachrichtigungen](images/56285_BIDI_04_bidirectional_tiles_white.png)

### <a name="a-consistent-easy-to-touch-rtl-user-experience"></a><span data-ttu-id="82785-144">Eine konsistente, per Toucheingabe einfach zu bedienende RTL-Benutzererfahrung</span><span class="sxs-lookup"><span data-stu-id="82785-144">A consistent, easy-to-touch RTL user experience</span></span>

<span data-ttu-id="82785-145">Alle Elemente der Benutzeroberfläche von Windows sind mit der RTL-Ausrichtung kompatibel.</span><span class="sxs-lookup"><span data-stu-id="82785-145">Every element in the Windows UI fits into the RTL orientation.</span></span> <span data-ttu-id="82785-146">Charms und Flyouts wurden auf der linken Seite des Bildschirms platziert, um das Überlappen von Suchergebnissen oder eine Beeinträchtigung der Toucheingabe zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="82785-146">Charms and flyouts have been positioned on the left edge of the screen so that they don't overlap search results or degrade touch optimization.</span></span> <span data-ttu-id="82785-147">Sie sind leicht mit dem Daumen erreichbar.</span><span class="sxs-lookup"><span data-stu-id="82785-147">They can be easily reached with the thumbs.</span></span>

![<span data-ttu-id="82785-148">BiDi-Screenshot](images/56286_BIDI_05_search_flyout_resized.png)
![BiDi-Screenshot</span><span class="sxs-lookup"><span data-stu-id="82785-148">BiDi screenshot](images/56286_BIDI_05_search_flyout_resized.png)
![BiDi screenshot</span></span>](images/56286_BIDI_06_print_flyout_resized.png)

![<span data-ttu-id="82785-149">BiDi-Screenshot](images/56286_BIDI_07_settings_flyout_resized.png)
![BiDi-Screenshot</span><span class="sxs-lookup"><span data-stu-id="82785-149">BiDi screenshot](images/56286_BIDI_07_settings_flyout_resized.png)
![BiDi screenshot</span></span>](images/56286_BIDI_08_app_bars_resized.png)

### <a name="text-input-in-any-direction"></a><span data-ttu-id="82785-150">Texteingabe in beliebiger Richtung</span><span class="sxs-lookup"><span data-stu-id="82785-150">Text input in any direction</span></span>

<span data-ttu-id="82785-151">Windows enthält eine kompakte und übersichtliche Bildschirmtastatur.</span><span class="sxs-lookup"><span data-stu-id="82785-151">Windows offers an on-screen touch keyboard that is clean and clutter-free.</span></span> <span data-ttu-id="82785-152">Für BiDi-Sprachen kann die Texteingaberichtung über eine entsprechende Steuerungstaste nach Bedarf umgeschaltet werden.</span><span class="sxs-lookup"><span data-stu-id="82785-152">For BiDi languages, there is a text direction control key so that the text input direction can be switched as needed.</span></span>

![Bildschirmtastatur für BiDi-Sprachen](images/56287_BIDI_09_keyboard_layout_resized.png)

### <a name="use-any-app-in-any-language"></a><span data-ttu-id="82785-154">Jede App in jeder Sprache verwenden</span><span class="sxs-lookup"><span data-stu-id="82785-154">Use any app in any language</span></span>

<span data-ttu-id="82785-155">Installieren und verwenden Sie Ihre bevorzugten Apps in jeder beliebigen Sprache.</span><span class="sxs-lookup"><span data-stu-id="82785-155">Install and use your favorite apps in any language.</span></span> <span data-ttu-id="82785-156">Die Apps funktionieren genau so wie in Nicht-BiDi-Versionen von Windows und werden auch entsprechend dargestellt</span><span class="sxs-lookup"><span data-stu-id="82785-156">The apps appear and function as they would on non-BiDi versions of Windows.</span></span> <span data-ttu-id="82785-157">Elemente in Apps werden stets einheitlich an vorhersehbaren Positionen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="82785-157">Elements within apps are always placed in a consistent and predictable position.</span></span>

![Englische App mit BiDi-Inhalt](images/56288_BIDI_10_english_app_resized.png)

### <a name="display-parentheses-correctly"></a><span data-ttu-id="82785-159">Ordnungsgemäße Darstellung von Klammern</span><span class="sxs-lookup"><span data-stu-id="82785-159">Display parentheses correctly</span></span>

<span data-ttu-id="82785-160">Dank der Einführung des BiDi-Klammeralgorithmus (BiDi Parenthesis Algorithm, BPA) werden Klammerpaare unabhängig von den Sprach- oder Textausrichtungseigenschaften stets korrekt dargestellt.</span><span class="sxs-lookup"><span data-stu-id="82785-160">With the introduction of the BiDi Parenthesis Algorithm (BPA), paired parentheses always display properly regardless of language or text alignment properties.</span></span>

#### <a name="incorrect-parentheses"></a><span data-ttu-id="82785-161">Falsche Klammern</span><span class="sxs-lookup"><span data-stu-id="82785-161">Incorrect parentheses</span></span>

![BiDi-App mit falschen Klammern](images/56289_BIDI_11_parentheses_resized.png)

#### <a name="correct-parentheses"></a><span data-ttu-id="82785-163">Korrekte Klammern</span><span class="sxs-lookup"><span data-stu-id="82785-163">Correct parentheses</span></span>

![BiDi-App mit korrekten Klammern](images/56289_BIDI_12_parentheses_fixed_resized.png)

### <a name="typography"></a><span data-ttu-id="82785-165">Typografie</span><span class="sxs-lookup"><span data-stu-id="82785-165">Typography</span></span>

<span data-ttu-id="82785-166">Windows verwendet die Schrift „Segoe UI” für alle BiDi-Sprachen.</span><span class="sxs-lookup"><span data-stu-id="82785-166">Windows uses the Segoe UI font for all BiDi languages.</span></span> <span data-ttu-id="82785-167">Diese Schrift wird für die Windows-Benutzeroberfläche angepasst und skaliert.</span><span class="sxs-lookup"><span data-stu-id="82785-167">This font is shaped and scaled for the Windows UI.</span></span>

![<span data-ttu-id="82785-168">Schrift „Segoe UI” für BiDi-Sprachen](images/56290_BIDI_13_start_screen_segoe.png)
![Schrift „Segoe UI” für BiDi-Sprachen</span><span class="sxs-lookup"><span data-stu-id="82785-168">Segoe UI font for BiDi language](images/56290_BIDI_13_start_screen_segoe.png)
![Segoe UI font for BiDi language</span></span>](images/56290_BIDI_13_start_screen_segoe_arabic.png)

## <a name="case-study-1-a-bidi-music-app"></a><span data-ttu-id="82785-169">Fallstudie 1: BiDi-Musik-App</span><span class="sxs-lookup"><span data-stu-id="82785-169">Case study #1: A BiDi music app</span></span>

### <a name="overview"></a><span data-ttu-id="82785-170">Übersicht</span><span class="sxs-lookup"><span data-stu-id="82785-170">Overview</span></span>

<span data-ttu-id="82785-171">Multimediale Apps stellen eine interessante Herausforderung hinsichtlich der Gestaltung dar. Von den Steuerelementen für entsprechende Medien wird i.d.R. ein Layout mit ähnlicher Ausrichtung (links-nach-rechts) wie bei Nicht-BiDi-Sprachen erwartet.</span><span class="sxs-lookup"><span data-stu-id="82785-171">Multimedia apps make for a very interesting design challenge, because media controls are generally expected to have a left-to-right layout similar to that of non-BiDi languages.</span></span>

![Mediensteuerelemente (links nach rechts)](images/56291_BIDI_1415_music_player_layouts_left-withcallouts.png)

![Mediensteuerelemente (rechts nach links)](images/56291_BIDI_1415_music_player_layouts_right-withcallouts.png)

### <a name="establishing-ui-directionality"></a><span data-ttu-id="82785-174">Festlegen der Ausrichtung von Elementen der Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="82785-174">Establishing UI directionality</span></span>

<span data-ttu-id="82785-175">Die Beibehaltung der Rechts-nach-links-Ausrichtung auf der Benutzeroberfläche ist im Hinblick auf die BiDi-Märkte für eine einheitliche Gestaltung von großer Bedeutung.</span><span class="sxs-lookup"><span data-stu-id="82785-175">Retaining the right-to-left UI flow is important for consistent design for BiDi markets.</span></span> <span data-ttu-id="82785-176">Das Hinzufügen von Elementen mit Links-nach-rechts-Fluss in diesem Kontext ist schwierig, da einige Navigationselemente wie die Zurück-Schaltfläche unter Umständen der direktionalen Ausrichtung der Zurück-Schaltfläche in den Audiosteuerelementen widerspricht.</span><span class="sxs-lookup"><span data-stu-id="82785-176">Adding elements that have left-to-right flow within this context is difficult, because some navigational elements such as the back button may contradict the directional orientation of the back button in the audio controls.</span></span>

![Titelseite der Musik-App](images/56292_BIDI_16_app_layout_callouts_resized.png)

<span data-ttu-id="82785-178">Die Musik-App von Microsoft übernimmt die Rechts-nach-links-Ausrichtung des Rasters.</span><span class="sxs-lookup"><span data-stu-id="82785-178">This music app retains a right-to-left-oriented grid.</span></span> <span data-ttu-id="82785-179">Dadurch wirkt die App für Benutzer, die diese Navigationsrichtung bereits auf der Windows-Benutzeroberfläche verwenden, sehr natürlich.</span><span class="sxs-lookup"><span data-stu-id="82785-179">This gives the app a very natural feel for users who already navigate in this direction across the Windows UI.</span></span> <span data-ttu-id="82785-180">Bei der Beibehaltung des Flusses wird nicht nur dafür gesorgt, dass die Hauptelemente von links nach rechts angeordnet werden, sondern es wird auch auf eine ordnungsgemäße Ausrichtung in den Abschnittsüberschriften geachtet, um eine fließende Verwendung der Benutzeroberfläche zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="82785-180">The flow is retained by ensuring that the main elements are not just ordered from right to left, but also aligned properly in the section headers to help maintain the UI flow.</span></span>

![Musik-App: Albumseite](images/56292_BIDI_17_app_layout_callouts_resized.png)

### <a name="text-handling"></a><span data-ttu-id="82785-182">Textbehandlung</span><span class="sxs-lookup"><span data-stu-id="82785-182">Text handling</span></span>

<span data-ttu-id="82785-183">Die Biografie des Künstlers im Screenshot oben wird linksbündig dargestellt. Andere auf den Künstler bezogene Textelemente wie der Name des Albums und die Namen der Einzeltitel werden weiterhin rechtsbündig dargestellt.</span><span class="sxs-lookup"><span data-stu-id="82785-183">The artist bio in the screenshot above is left-aligned, while other artist-related text pieces such as album and track names preserve right alignment.</span></span> <span data-ttu-id="82785-184">Das Feld mit der Biografie ist ein relativ großes Textelement, das schlecht lesbar ist, wenn es nach rechts ausgerichtet ist, weil es beim Lesen eines breiteren Textblocks schwierig ist, die Orientierung zu behalten</span><span class="sxs-lookup"><span data-stu-id="82785-184">The bio field is a fairly large text element, which reads poorly when aligned to the right simply because it's hard to track between the lines while reading a wider text block.</span></span> <span data-ttu-id="82785-185">Allgemein gilt: Jedes Textelement mit mehr als zwei oder drei Zeilen und mindestens fünf Wörtern pro Zeile kann ähnlichen Ausnahmen bezüglich der Ausrichtung unterworfen sein, sodass die Ausrichtung der Textblöcke nicht der allgemeinen Layoutausrichtung der App entspricht.</span><span class="sxs-lookup"><span data-stu-id="82785-185">In general, any text element with more than two or three lines containing five or more words should be considered for similar alignment exceptions, where the text block alignment is opposite to that of the overall app directional layout.</span></span>

<span data-ttu-id="82785-186">Die Änderung der Ausrichtung innerhalb der App mag recht unkompliziert wirken, offenbart aber häufig einige Einschränkungen und Schwachstellen der verschiedenen Renderingmodule bei der neutralen Zeichenplatzierung in BiDi-Zeichenfolgen.</span><span class="sxs-lookup"><span data-stu-id="82785-186">Manipulating the alignment across the app can look simple, but it often exposes some of the boundaries and limitations of the rendering engines in terms of neutral character placement across BiDi strings.</span></span> <span data-ttu-id="82785-187">So wird möglicherweise die folgende Zeichenfolge je nach Ausrichtung unterschiedlich dargestellt.</span><span class="sxs-lookup"><span data-stu-id="82785-187">For example, the following string can display differently based on alignment.</span></span>

| | <span data-ttu-id="82785-188">Englische Zeichenfolge (LTR)</span><span class="sxs-lookup"><span data-stu-id="82785-188">English String (LTR)</span></span> | <span data-ttu-id="82785-189">Hebräische Zeichenfolge (RTL)</span><span class="sxs-lookup"><span data-stu-id="82785-189">Hebrew String (RTL)</span></span> |
| -------------- | ------------------- | ------------------- |
| **<span data-ttu-id="82785-190">Linksbündig</span><span class="sxs-lookup"><span data-stu-id="82785-190">Left-alignment</span></span>** | <span data-ttu-id="82785-191">Hello, World!</span><span class="sxs-lookup"><span data-stu-id="82785-191">Hello, World!</span></span> | <span data-ttu-id="82785-192">בוקר טוב!</span><span class="sxs-lookup"><span data-stu-id="82785-192">בוקר טוב!</span></span> |
| **<span data-ttu-id="82785-193">Rechtsbündig</span><span class="sxs-lookup"><span data-stu-id="82785-193">Right-alignment</span></span>** | <span data-ttu-id="82785-194">!Hello, World</span><span class="sxs-lookup"><span data-stu-id="82785-194">!Hello, World</span></span> | <span data-ttu-id="82785-195">!בוקר טוב</span><span class="sxs-lookup"><span data-stu-id="82785-195">!בוקר טוב</span></span> |

<span data-ttu-id="82785-196">Um sicherzustellen, dass die Informationen zum jeweiligen Künstler in der Musik-App fehlerfrei angezeigt werden, wurden die Eigenschaften für das Textlayout und die Ausrichtung vom Entwicklungsteam getrennt behandelt.</span><span class="sxs-lookup"><span data-stu-id="82785-196">To ensure that artist information is properly displayed across the music app, the development team separated text layout properties from alignment.</span></span> <span data-ttu-id="82785-197">Mit anderen Worten: Die Informationen über den Künstler werden zwar möglicherweise in vielen Fällen rechtsbündig dargestellt, die Layoutausrichtung wird jedoch auf der Grundlage einer angepassten Hintergrundverarbeitung festgelegt.</span><span class="sxs-lookup"><span data-stu-id="82785-197">In other words, the artist info might be displayed as right-aligned in many of the cases, but the string layout adjustment is set based on customized background processing.</span></span> <span data-ttu-id="82785-198">Die Hintergrundverarbeitung bestimmt die auf Basis des Zeichenfolgeninhalts das am besten geeignete Ausrichtungslayout.</span><span class="sxs-lookup"><span data-stu-id="82785-198">The background processing determines the best directional layout setting based on the content of the string.</span></span>

![Musik-App: Künstlerseite](images/56292_BIDI_18_app_layout_callouts_resized.png)

<span data-ttu-id="82785-200">Beispiel: Ohne benutzerdefinierte Verarbeitung des Zeichenfolgenlayouts würde der Interpretenname „The Contoso Band.”</span><span class="sxs-lookup"><span data-stu-id="82785-200">For example, without custom string layout processing, the artist name "The Contoso Band."</span></span> <span data-ttu-id="82785-201">dargestellt als „.The Contoso Band”.</span><span class="sxs-lookup"><span data-stu-id="82785-201">would appear as ".The Contoso Band".</span></span>

### <a name="specialized-string-direction-preprocessing"></a><span data-ttu-id="82785-202">Spezielle Verarbeitung der Zeichenfolgenausrichtung</span><span class="sxs-lookup"><span data-stu-id="82785-202">Specialized string direction preprocessing</span></span>

<span data-ttu-id="82785-203">Wenn die App Medienmetadaten vom Server abruft, wird jede einzelne Zeichenfolge zunächst verarbeitet, bevor der Benutzer sie sehen kann.</span><span class="sxs-lookup"><span data-stu-id="82785-203">When the app contacts the server for media metadata, it preprocesses each string prior to displaying it to the user.</span></span> <span data-ttu-id="82785-204">Bei dieser Vorverarbeitung findet auch eine Umwandlung statt, um für eine einheitliche Textrichtung zu sorgen.</span><span class="sxs-lookup"><span data-stu-id="82785-204">During this preprocessing, the app also does a transformation to make the text direction consistent.</span></span> <span data-ttu-id="82785-205">Hierzu prüft die App, ob am Ende der Zeichenfolge neutrale Zeichen stehen.</span><span class="sxs-lookup"><span data-stu-id="82785-205">To do this, it checks whether there are neutral characters on the ends of the string.</span></span> <span data-ttu-id="82785-206">Und wenn die Textausrichtung der Zeichenfolge nicht der durch die Windows-Spracheinstellungen festgelegten Richtung für die App entspricht, werden Unicode-Richtungsmarker an die Zeichenfolge angefügt (und manchmal auch vorangestellt).</span><span class="sxs-lookup"><span data-stu-id="82785-206">Also, if the text direction of the string is opposite to the app direction set by the Windows language settings, then it appends (and sometimes prepends) Unicode direction markers.</span></span> <span data-ttu-id="82785-207">Die Transformationsfunktion sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="82785-207">The transformation function looks like this.</span></span>

```csharp
string NormalizeTextDirection(string data) 
{
    if (data.Length > 0) {
        var lastCharacterDirection = DetectCharacterDirection(data[data.Length - 1]);

        // If the last character has strong directionality (direction is not null), then the text direction for the string is already consistent.
        if (!lastCharacterDirection) {
            // If the last character has no directionality (neutral character, direction is null), then we may need to add a direction marker to
            // ensure that the last character doesn't inherit directionality from the outside context.
            var appTextDirection = GetAppTextDirection(); // checks the <html> element's "dir" attribute.
            var dataTextDirection = DetectStringDirection(data); // Run through the string until a non-neutral character is encountered,
                                                                 // which determines the text direction.

            if (appTextDirection != dataTextDirection) {
                // Add a direction marker only if the data text runs opposite to the directionality of the app as a whole,
                // which would cause the neutral characters at the ends to flip.
                var directionMarkerCharacter =
                    dataTextDirection == TextDirections.RightToLeft ?
                        UnicodeDirectionMarkers.RightToLeftDirectionMarker : // "\u200F"
                        UnicodeDirectionMarkers.LeftToRightDirectionMarker; // "\u200E"

                data += directionMarkerCharacter;

                // Prepend the direction marker if the data text begins with a neutral character.
                var firstCharacterDirection = DetectCharacterDirection(data[0]);
                if (!firstCharacterDirection) {
                    data = directionMarkerCharacter + data;
                }
            }
        }
    }

    return data;
}
```

<span data-ttu-id="82785-208">Die hinzugefügten Unicode-Zeichen sind Nullbreitenzeichen und wirken sich daher nicht auf die Zeichenfolgenabstände aus.</span><span class="sxs-lookup"><span data-stu-id="82785-208">The added Unicode characters are zero-width, so they don't impact the spacing of the strings.</span></span> <span data-ttu-id="82785-209">Dieser Code beeinträchtigt unter Umständen die Leistung, da die Zeichenfolge zum Erkennen der Richtung durchlaufen werden muss, bis ein nicht neutrales Zeichen gefunden wird.</span><span class="sxs-lookup"><span data-stu-id="82785-209">This code carries a potential performance penalty, since detecting the direction of a string requires running through the string until a non-neutral character is encountered.</span></span> <span data-ttu-id="82785-210">Da jedes Zeichen, dessen Neutralität überprüft wird, zunächst mit mehreren Unicode-Bereichen abgeglichen wird, handelt es sich um eine umfangreiche Prüfung.</span><span class="sxs-lookup"><span data-stu-id="82785-210">Each character that's checked for neutrality is first compared against several Unicode ranges as well, so it isn't a trivial check.</span></span>

## <a name="case-study-2-a-bidi-mail-app"></a><span data-ttu-id="82785-211">Fallstudie Nr. 2: BiDi-Mail-App</span><span class="sxs-lookup"><span data-stu-id="82785-211">Case study #2: A BiDi mail app</span></span>

### <a name="overview"></a><span data-ttu-id="82785-212">Übersicht</span><span class="sxs-lookup"><span data-stu-id="82785-212">Overview</span></span>

<span data-ttu-id="82785-213">Im Hinblick auf die Anforderungen an das Layout der Benutzeroberfläche gestaltet sich der Entwurf eines Mail-Clients relativ einfach.</span><span class="sxs-lookup"><span data-stu-id="82785-213">In terms of UI layout requirements, a mail client is fairly simple to design.</span></span> <span data-ttu-id="82785-214">Die Mail-App in Windows wird standardmäßig gespiegelt.</span><span class="sxs-lookup"><span data-stu-id="82785-214">The Mail app in Windows is mirrored by default.</span></span> <span data-ttu-id="82785-215">Im Hinblick auf die Textbehandlung erfordert die Mail-App eine leistungsfähigere Textanzeige und leistungsfähigere Erstellungsfunktionen, um Szenarien mit gemischter Textausrichtung behandeln zu können.</span><span class="sxs-lookup"><span data-stu-id="82785-215">From a text-handling perspective the mail app is required to have more robust text display and composition capabilities in order to accommodate mixed text scenarios.</span></span>

### <a name="establishing-ui-directionality"></a><span data-ttu-id="82785-216">Festlegen der Ausrichtung von Elementen der Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="82785-216">Establishing UI directionality</span></span>

<span data-ttu-id="82785-217">Das Layout der Benutzeroberfläche für die Mail-App wird gespiegelt.</span><span class="sxs-lookup"><span data-stu-id="82785-217">The UI layout for the Mail app is mirrored.</span></span> <span data-ttu-id="82785-218">Die Ausrichtung der drei Bereiche wurde so angepasst, dass der Ordnerbereich rechts im Bildschirm dargestellt wird. Die Liste der E-Mail-Elemente wird links davon angezeigt, gefolgt vom Bereich zum Verfassen von E-Mails.</span><span class="sxs-lookup"><span data-stu-id="82785-218">The three panes have been reoriented so that the folder pane is positioned on the right edge of the screen, followed by the mail item list pane to the left, and then the email composition pane.</span></span>

![Gespiegelte Mail-App](images/56293_BIDI_19_icon_realignment_cropped_resized.png)

<span data-ttu-id="82785-220">Auch die Ausrichtung zusätzlicher Elemente wurde an den allgemeinen Benutzeroberflächenfluss und die Optimierung für die Toucheingabe angepasst.</span><span class="sxs-lookup"><span data-stu-id="82785-220">Additional items have been reoriented to match the overall UI flow, and touch optimization.</span></span> <span data-ttu-id="82785-221">Dazu gehören die App-Leiste und die Symbole zum Erstellen, Beantworten und Löschen.</span><span class="sxs-lookup"><span data-stu-id="82785-221">These include the app bar and the compose, reply, and delete icons.</span></span>

![Gespiegelte Mail-App mit App-Leiste](images/56294_BIDI_20_email_orientation_email_resized.png)

### <a name="text-handling"></a><span data-ttu-id="82785-223">Textverarbeitung</span><span class="sxs-lookup"><span data-stu-id="82785-223">Text Handling</span></span>

#### <a name="ui"></a><span data-ttu-id="82785-224">Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="82785-224">UI</span></span>

<span data-ttu-id="82785-225">Texte auf der Benutzeroberfläche sind im Allgemeinen rechtsbündig ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="82785-225">Text alignment across the UI is usually right-aligned.</span></span> <span data-ttu-id="82785-226">Dies gilt auch für den Ordner- und Elementbereich.</span><span class="sxs-lookup"><span data-stu-id="82785-226">This includes the folder pane and items pane.</span></span> <span data-ttu-id="82785-227">Der Elementbereich ist auf zwei Textzeilen (Adresse und Titel) begrenzt.</span><span class="sxs-lookup"><span data-stu-id="82785-227">The item pane is limited to two lines of text (Address, and Title).</span></span> <span data-ttu-id="82785-228">Dies ist wichtig, um die Rechts-nach-links-Ausrichtung beizubehalten, ohne dass ein Textblock entsteht, der nur schwer zu lesen ist, wenn die Inhaltsrichtung nicht der Flussrichtung der Benutzeroberfläche entspricht.</span><span class="sxs-lookup"><span data-stu-id="82785-228">This is important for retaining the right-to-left alignment, without introducing a block of text that would be difficult to read when the content direction is opposite to the UI direction flow.</span></span>

#### <a name="text-editing"></a><span data-ttu-id="82785-229">Textbearbeitung</span><span class="sxs-lookup"><span data-stu-id="82785-229">Text Editing</span></span>

<span data-ttu-id="82785-230">Bei der Textbearbeitung muss es möglich sein, Text sowohl von rechts nach links als auch von links nach rechts zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="82785-230">Text editing requires the ability to compose in both right-to-left and left-to-right form.</span></span> <span data-ttu-id="82785-231">Darüber hinaus muss das Layout zum Erstellen von Nachrichten mithilfe eines Formats wie&mdash;Rich-Text&mdash;beibehalten werden, das Ausrichtungsinformationen speichern kann.</span><span class="sxs-lookup"><span data-stu-id="82785-231">In addition, the composition layout must be preserved by using a format&mdash;such as rich text&mdash;that has the ability to save directional information.</span></span>

![Mail-App (links-nach-rechts)](images/56294_BIDI_21_email_orientation_LtR_resized.png)

![Mail-App (rechts-nach-links)](images/56294_BIDI_22_email_orientation_RtL_resized.png)
