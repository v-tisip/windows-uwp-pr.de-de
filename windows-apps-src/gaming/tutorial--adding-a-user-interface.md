---
author: abbycar
title: Hinzufügen einer Benutzeroberfläche
description: Erfahren Sie, wie ein DirectX-UWP-Spiel ein 2D benutzeroberflächenoverlay hinzu.
ms.assetid: fa40173e-6cde-b71b-e307-db90f0388485
ms.author: abigailc
ms.date: 10/24/2017
ms.topic: article
keywords: Windows10, UWP, Spiele, Benutzeroberfläche, directx
ms.localizationpriority: medium
ms.openlocfilehash: 9962cc9043bd650390721715ca73b2e85a219c25
ms.sourcegitcommit: f2c9a050a9137a473f28b613968d5782866142c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2018
ms.locfileid: "6274099"
---
# <a name="add-a-user-interface"></a><span data-ttu-id="ac404-104">Hinzufügen einer Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="ac404-104">Add a user interface</span></span>


<span data-ttu-id="ac404-105">Nun, da unser Spiel seine 3D-Grafik eingerichtet hat, ist es Zeit zu konzentrieren, einige 2D Elemente hinzufügen, damit das Spiel Spielzustand dem Spieler Feedback zu kann.</span><span class="sxs-lookup"><span data-stu-id="ac404-105">Now that our game has its 3D visuals in place, it's time to focus on adding some 2D elements so that the game can provide feedback about game state to the player.</span></span> <span data-ttu-id="ac404-106">Dies kann erfolgen durch Hinzufügen von einfache Menüoptionen und Head-Up-Anzeigekomponenten der 3D-Grafiken pipeline Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="ac404-106">This can be accomplished by adding simple menu options and heads-up display components on top of the 3-D graphics pipeline output.</span></span>

>[!Note]
><span data-ttu-id="ac404-107">Wenn Sie den neuesten Code für dieses Beispiel noch nicht heruntergeladen haben, wechseln Sie zu [Direct3D-Spielbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Simple3DGameDX).</span><span class="sxs-lookup"><span data-stu-id="ac404-107">If you haven't downloaded the latest game code for this sample, go to [Direct3D game sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Simple3DGameDX).</span></span> <span data-ttu-id="ac404-108">Dieses Beispiel gehört zu einer großen Sammlung von UWP-Featurebeispielen.</span><span class="sxs-lookup"><span data-stu-id="ac404-108">This sample is part of a large collection of UWP feature samples.</span></span> <span data-ttu-id="ac404-109">Anweisungen zum Herunterladen des Beispiels finden Sie unter [Abrufen der UWP-Beispiele von GitHub](https://docs.microsoft.com/windows/uwp/get-started/get-uwp-app-samples).</span><span class="sxs-lookup"><span data-stu-id="ac404-109">For instructions on how to download the sample, see [Get the UWP samples from GitHub](https://docs.microsoft.com/windows/uwp/get-started/get-uwp-app-samples).</span></span>

## <a name="objective"></a><span data-ttu-id="ac404-110">Ziel</span><span class="sxs-lookup"><span data-stu-id="ac404-110">Objective</span></span>

<span data-ttu-id="ac404-111">Fügen Sie mithilfe von Direct2D, eine Reihe von benutzeroberflächengrafiken und-Verhalten zu unserem UWP-DirectX-Spiel-einschließlich:</span><span class="sxs-lookup"><span data-stu-id="ac404-111">Using Direct2D, add a number of user interface graphics and behaviors to our UWP DirectX game including:</span></span>
- <span data-ttu-id="ac404-112">Heads-Up-Anzeige, einschließlich der [bewegungs-/ Controller](tutorial--adding-controls.md) ist Rechtecke</span><span class="sxs-lookup"><span data-stu-id="ac404-112">Heads-up display, including [move-look controller](tutorial--adding-controls.md) boundry rectangles</span></span>
- <span data-ttu-id="ac404-113">Spielzustand Menüs</span><span class="sxs-lookup"><span data-stu-id="ac404-113">Game state menus</span></span>


## <a name="the-user-interface-overlay"></a><span data-ttu-id="ac404-114">Benutzeroberflächenoverlay</span><span class="sxs-lookup"><span data-stu-id="ac404-114">The user interface overlay</span></span>


<span data-ttu-id="ac404-115">Während es viele Möglichkeiten zum Anzeigen von Text und UI-Elementen in einem DirectX-Spiel gibt, werden zu konzentrieren wir zur Verwendung von [Direct2D](https://msdn.microsoft.com/library/windows/apps/dd370990.aspx).</span><span class="sxs-lookup"><span data-stu-id="ac404-115">While there are many ways to display text and user interface elements in a DirectX game, we're going to focus on using [Direct2D](https://msdn.microsoft.com/library/windows/apps/dd370990.aspx).</span></span> <span data-ttu-id="ac404-116">Wir werden auch [DirectWrite](https://msdn.microsoft.com/library/windows/desktop/dd368038) für die Textelemente verwenden.</span><span class="sxs-lookup"><span data-stu-id="ac404-116">We'll also be using [DirectWrite](https://msdn.microsoft.com/library/windows/desktop/dd368038) for the text elements.</span></span>


<span data-ttu-id="ac404-117">Direct2D ist, dass eine Reihe von 2D zeichnen APIs zum Zeichnen von pixelbasierten Grundtypen und Effekten verwendet.</span><span class="sxs-lookup"><span data-stu-id="ac404-117">Direct2D is a set of 2D drawing APIs used to draw pixel-based primitives and effects.</span></span> <span data-ttu-id="ac404-118">Wenn Sie mit Direct2D fangen an, empfiehlt es sich Einfachheit halber.</span><span class="sxs-lookup"><span data-stu-id="ac404-118">When starting out with Direct2D, it's best to keep things simple.</span></span> <span data-ttu-id="ac404-119">Komplexe Layouts und Benutzeroberflächenverhalten erfordern Zeit und Planung.</span><span class="sxs-lookup"><span data-stu-id="ac404-119">Complex layouts and interface behaviors need time and planning.</span></span> <span data-ttu-id="ac404-120">Wenn Ihr Spiel eine komplexe Benutzeroberfläche wie in Simulations- und Strategiespielen, erfordert sollten Sie XAML stattdessen.</span><span class="sxs-lookup"><span data-stu-id="ac404-120">If your game requires a complex user interface, like those found in simulation and strategy games, consider using XAML instead.</span></span>

> [!NOTE]
> <span data-ttu-id="ac404-121">Informationen zum Entwickeln einer Benutzeroberfläche mit XAML in einem UWP-DirectX-Spiel finden Sie unter [Erweitern des spielbeispiels](tutorial-resources.md).</span><span class="sxs-lookup"><span data-stu-id="ac404-121">For info about developing a user interface with XAML in a UWP DirectX game, see [Extending the game sample](tutorial-resources.md).</span></span>

<span data-ttu-id="ac404-122">Direct2D ist nicht speziell für Benutzeroberflächen oder Layouts wie HTML- und XAML.</span><span class="sxs-lookup"><span data-stu-id="ac404-122">Direct2D isn't specifically designed for user interfaces or layouts like HTML and XAML.</span></span> <span data-ttu-id="ac404-123">Es stellt keine Benutzeroberflächenkomponenten wie Listen, Felder oder Schaltflächen bereit.</span><span class="sxs-lookup"><span data-stu-id="ac404-123">It doesn't provide user interface components like lists, boxes, or buttons.</span></span> <span data-ttu-id="ac404-124">Außerdem keine Layoutkomponenten wie Divs, Tabellen oder Raster zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="ac404-124">It also doesn't provide layout components like divs, tables, or grids.</span></span>


<span data-ttu-id="ac404-125">Für dieses Spielbeispiel haben wir zwei hauptoberflächenkomponenten.</span><span class="sxs-lookup"><span data-stu-id="ac404-125">For this game sample we have two major UI components.</span></span>
1. <span data-ttu-id="ac404-126">Für die Bewertung und spielinterne Steuerelemente Heads-up-Anzeige.</span><span class="sxs-lookup"><span data-stu-id="ac404-126">A heads-up display for the score and in-game controls.</span></span>
2. <span data-ttu-id="ac404-127">Eine Überlagerung verwendet, um Optionen wie etwa pauseninformationen und Spielzustand Text anzuzeigen und Ebene Startoptionen.</span><span class="sxs-lookup"><span data-stu-id="ac404-127">An overlay used to display game state text and options such as pause info and level start options.</span></span>

### <a name="using-direct2d-for-a-heads-up-display"></a><span data-ttu-id="ac404-128">Verwenden von Direct2D für die Heads-Up-Anzeige</span><span class="sxs-lookup"><span data-stu-id="ac404-128">Using Direct2D for a heads-up display</span></span>

<span data-ttu-id="ac404-129">Die folgende Abbildung zeigt die spielinterne Heads-up-Anzeige für das Beispiel.</span><span class="sxs-lookup"><span data-stu-id="ac404-129">The following image shows the in-game heads-up display for the sample.</span></span> <span data-ttu-id="ac404-130">Es ist einfach und übersichtlich, sodass sich der Spieler auf die Navigation in der 3D-Welt und das Abschießen der Ziele konzentrieren.</span><span class="sxs-lookup"><span data-stu-id="ac404-130">It's simple and uncluttered, allowing the player to focus on navigating the 3D world and shooting targets.</span></span> <span data-ttu-id="ac404-131">Eine gute Benutzeroberfläche oder Head-Up müssen Sie die Möglichkeit des Players zum Verarbeiten und reagieren auf die Ereignisse im Spiel nie erschweren.</span><span class="sxs-lookup"><span data-stu-id="ac404-131">A good interface or heads-up display must never complicate the ability of the player to process and react to the events in the game.</span></span>

![Screenshot des Spieloverlays](images/simple-dx-game-ui-overlay.png)

<span data-ttu-id="ac404-133">Die folgenden grundlegenden primitiven besteht das Overlay aus.</span><span class="sxs-lookup"><span data-stu-id="ac404-133">The overlay consists of the following basic primitives.</span></span>
- <span data-ttu-id="ac404-134">In der oberen rechten Ecke, die den Spieler über informiert [**DirectWrite**](https://msdn.microsoft.com/en-us/library/windows/desktop/dd368038) -text</span><span class="sxs-lookup"><span data-stu-id="ac404-134">[**DirectWrite**](https://msdn.microsoft.com/en-us/library/windows/desktop/dd368038) text in the upper-right corner that informs the player of</span></span> 
    - <span data-ttu-id="ac404-135">Treffern</span><span class="sxs-lookup"><span data-stu-id="ac404-135">Successful hits</span></span>
    - <span data-ttu-id="ac404-136">Anzahl von Screenshots, die der Spieler vorgenommen hat</span><span class="sxs-lookup"><span data-stu-id="ac404-136">Number of shots the player has made</span></span>
    - <span data-ttu-id="ac404-137">Verbleibende Zeit auf der Ebene</span><span class="sxs-lookup"><span data-stu-id="ac404-137">Time remaining in the level</span></span>
    - <span data-ttu-id="ac404-138">Aktuelle Levelnummer</span><span class="sxs-lookup"><span data-stu-id="ac404-138">Current level number</span></span> 
- <span data-ttu-id="ac404-139">Zwei sich schneidende Liniensegmente verwendet, um ein Fadenkreuz bilden</span><span class="sxs-lookup"><span data-stu-id="ac404-139">Two intersecting line segments used to form a cross hair</span></span>
- <span data-ttu-id="ac404-140">Zwei Rechtecke an den Ecken unten für den [bewegungs-und blickrichtungscontrollers](tutorial--adding-controls.md) lassen.</span><span class="sxs-lookup"><span data-stu-id="ac404-140">Two rectangles at the bottom corners for the [move-look controller](tutorial--adding-controls.md) boundries.</span></span> 


<span data-ttu-id="ac404-141">Der spielinterne Head-Up-Anzeigezustand des Overlays wird in der [**gamehud:: Render**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameHud.cpp#L234-L358) -Methode der Klasse [**GameHud**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameHud.h) gezeichnet.</span><span class="sxs-lookup"><span data-stu-id="ac404-141">The in-game heads-up display state of the overlay is drawn in the [**GameHud::Render**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameHud.cpp#L234-L358) method of the [**GameHud**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameHud.h) class.</span></span> <span data-ttu-id="ac404-142">In dieser Methode ist das Direct2D-Overlay, das unsere Benutzeroberfläche darstellt aktualisiert, um die Änderungen in die Anzahl von Treffern, Zeit verbleibenden und Ebene Anzahl wiederzugeben.</span><span class="sxs-lookup"><span data-stu-id="ac404-142">Within this method, the Direct2D overlay that represents our UI is updated to reflect the changes in the number of hits, time remaining, and level number.</span></span>

<span data-ttu-id="ac404-143">Wenn das Spiel initialisiert wurde, fügen wir `TotalHits()`, `TotalShots()`, und `TimeRemaining()` auf eine [**Swprintf_s**](https://docs.microsoft.com/cpp/c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l) Puffer und geben Sie den Druck-Format.</span><span class="sxs-lookup"><span data-stu-id="ac404-143">If the game has been initialized, we add `TotalHits()`, `TotalShots()`, and `TimeRemaining()` to a [**swprintf_s**](https://docs.microsoft.com/cpp/c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l) buffer and specify the print format.</span></span> <span data-ttu-id="ac404-144">Wir können dann mit der Methode [**DrawText**](https://msdn.microsoft.com/en-us/library/windows/desktop/dd742848) zeichnen.</span><span class="sxs-lookup"><span data-stu-id="ac404-144">We can then draw it using the [**DrawText**](https://msdn.microsoft.com/en-us/library/windows/desktop/dd742848) method.</span></span> <span data-ttu-id="ac404-145">Wir gehen Sie genauso für den aktuellen Ebene Indikator zeichnen leeren Zahlen anzeigen nicht abgeschlossene Ebenen wie ➀ und gefüllte Zahlen wie ➊ angezeigt, dass die spezifischen Level abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="ac404-145">We do the same for the current level indicator, drawing empty numbers to show uncompleted levels like ➀, and filled numbers like ➊ to show that the specific level was completed.</span></span>


<span data-ttu-id="ac404-146">Der folgende Codeausschnitt führt durch die **gamehud:: Render** -Methode für</span><span class="sxs-lookup"><span data-stu-id="ac404-146">The following code snippet walks through the **GameHud::Render** method's process for</span></span> 
- <span data-ttu-id="ac404-147">Erstellen einer Bitmap mit [\*\* ID2D1RenderTarget::DrawBitmap \*\*](https://msdn.microsoft.com/en-us/library/windows/desktop/dd371880)</span><span class="sxs-lookup"><span data-stu-id="ac404-147">Creating a Bitmap using [\*\*ID2D1RenderTarget::DrawBitmap \*\*](https://msdn.microsoft.com/en-us/library/windows/desktop/dd371880)</span></span>
- <span data-ttu-id="ac404-148">UI-Bereiche unterteilen in Rechtecke mit [ **D2D1::RectF**](https://msdn.microsoft.com/en-us/library/windows/desktop/dd368184)</span><span class="sxs-lookup"><span data-stu-id="ac404-148">Sectioning off UI areas into rectangles using [**D2D1::RectF**](https://msdn.microsoft.com/en-us/library/windows/desktop/dd368184)</span></span>
- <span data-ttu-id="ac404-149">Mit **DrawText** Textelemente werden kann</span><span class="sxs-lookup"><span data-stu-id="ac404-149">Using **DrawText** to make text elements</span></span>

```cpp
void GameHud::Render(_In_ Simple3DGame^ game)
{
    auto d2dContext = m_deviceResources->GetD2DDeviceContext();
    auto windowBounds = m_deviceResources->GetLogicalSize();

    if (m_showTitle)
    {
        d2dContext->DrawBitmap(
            m_logoBitmap.Get(),
            D2D1::RectF(
                GameConstants::Margin,
                GameConstants::Margin,
                m_logoSize.width + GameConstants::Margin,
                m_logoSize.height + GameConstants::Margin
                )
            );
        d2dContext->DrawTextLayout(
            Point2F(m_logoSize.width + 2.0f * GameConstants::Margin, GameConstants::Margin),
            m_titleHeaderLayout.Get(),
            m_textBrush.Get()
            );
        d2dContext->DrawTextLayout(
            Point2F(GameConstants::Margin, m_titleBodyVerticalOffset),
            m_titleBodyLayout.Get(),
            m_textBrush.Get()
            );
    }

    // Draw text for number of hits, total shots, and time remaining
    if (game != nullptr)
    {
        // This section is only used after the game state has been initialized.
        static const int bufferLength = 256;
        static char16 wsbuffer[bufferLength];
        int length = swprintf_s(
            wsbuffer,
            bufferLength,
            L"Hits:\t%10d\nShots:\t%10d\nTime:\t%8.1f",
            game->TotalHits(),
            game->TotalShots(),
            game->TimeRemaining()
            );
        
        // Draw the upper right portion of the HUD displaying total hits, shots, and time remaining
        d2dContext->DrawText(
            wsbuffer,
            length,
            m_textFormatBody.Get(),
            D2D1::RectF(
                windowBounds.Width - GameConstants::HudRightOffset,
                GameConstants::HudTopOffset,
                windowBounds.Width,
                GameConstants::HudTopOffset + (GameConstants::HudBodyPointSize + GameConstants::Margin) * 3
                ),
            m_textBrush.Get()
            );

        // Using the unicode characters starting at 0x2780 ( ➀ ) for the consecutive levels of the game.
        // For completed levels start with 0x278A ( ➊ ) (This is 0x2780 + 10).
        uint32 levelCharacter[6];
        for (uint32 i = 0; i < 6; i++)
        {
            levelCharacter[i] = 0x2780 + i + ((static_cast<uint32>(game->LevelCompleted()) == i) ? 10 : 0);
        }
        length = swprintf_s(
            wsbuffer,
            bufferLength,
            L"%lc %lc %lc %lc %lc %lc",
            levelCharacter[0],
            levelCharacter[1],
            levelCharacter[2],
            levelCharacter[3],
            levelCharacter[4],
            levelCharacter[5]
            );
        // Create a new rectangle and draw the current level info text inside
        d2dContext->DrawText(
            wsbuffer,
            length,
            m_textFormatBodySymbol.Get(),
            D2D1::RectF(
                windowBounds.Width - GameConstants::HudRightOffset,
                GameConstants::HudTopOffset + (GameConstants::HudBodyPointSize + GameConstants::Margin) * 3 + GameConstants::Margin,
                windowBounds.Width,
                GameConstants::HudTopOffset + (GameConstants::HudBodyPointSize+ GameConstants::Margin) * 4
                ),
            m_textBrush.Get()
            );

        if (game->IsActivePlay())
        {
            // Draw the move and fire rectangles
            // Draw the crosshairs
        }
    }
}
```

<span data-ttu-id="ac404-150">Unterbrechen die Methode unten dieser Teil der [**gamehud:: Render**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameHud.cpp#L320-L358) -Methode zeichnet weiter, unsere verschieben und das schießrechteck werden mit [**ID2D1RenderTarget::DrawRectangle**](https://msdn.microsoft.com/library/windows/desktop/dd371902)und Fadenkreuze mit zwei Aufrufe von [**ID2D1RenderTarget::DrawLine**](https://msdn.microsoft.com/library/windows/desktop/dd371895).</span><span class="sxs-lookup"><span data-stu-id="ac404-150">Breaking the method down further, this piece of the [**GameHud::Render**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameHud.cpp#L320-L358) method draws our move and fire rectangles with [**ID2D1RenderTarget::DrawRectangle**](https://msdn.microsoft.com/library/windows/desktop/dd371902), and crosshairs using two calls to [**ID2D1RenderTarget::DrawLine**](https://msdn.microsoft.com/library/windows/desktop/dd371895).</span></span>

```cpp
        // Check if game is playing
        if (game->IsActivePlay())
        {
            // Draw a rectangle for the touch input for the move control.
            d2dContext->DrawRectangle(
                D2D1::RectF(
                    0.0f,
                    windowBounds.Height - GameConstants::TouchRectangleSize,
                    GameConstants::TouchRectangleSize,
                    windowBounds.Height
                    ),
                m_textBrush.Get()
                );
            // Draw a rectangle for the touch input of the fire control.
            d2dContext->DrawRectangle(
                D2D1::RectF(
                    windowBounds.Width - GameConstants::TouchRectangleSize,
                    windowBounds.Height - GameConstants::TouchRectangleSize,
                    windowBounds.Width,
                    windowBounds.Height
                    ),
                m_textBrush.Get()
                );

            // Draw two lines to form crosshairs
            d2dContext->DrawLine(
                D2D1::Point2F(windowBounds.Width / 2.0f - GameConstants::CrossHairHalfSize, windowBounds.Height / 2.0f),
                D2D1::Point2F(windowBounds.Width / 2.0f + GameConstants::CrossHairHalfSize, windowBounds.Height / 2.0f),
                m_textBrush.Get(),
                3.0f
                );
            d2dContext->DrawLine(
                D2D1::Point2F(windowBounds.Width / 2.0f, windowBounds.Height / 2.0f - GameConstants::CrossHairHalfSize),
                D2D1::Point2F(windowBounds.Width / 2.0f, windowBounds.Height / 2.0f + GameConstants::CrossHairHalfSize),
                m_textBrush.Get(),
                3.0f
                );
        }
```

<span data-ttu-id="ac404-151">In der **gamehud:: Render** -Methode, die wir Speichern der logischen Größe des Spielfensters in der `windowBounds` Variable.</span><span class="sxs-lookup"><span data-stu-id="ac404-151">In the **GameHud::Render** method we store the logical size of the game window in the `windowBounds` variable.</span></span> <span data-ttu-id="ac404-152">Dies wird verwendet, die [`GetLogicalSize`](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/Common/DeviceResources.h#L41) Methode der Klasse **DeviceResources** .</span><span class="sxs-lookup"><span data-stu-id="ac404-152">This uses the [`GetLogicalSize`](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/Common/DeviceResources.h#L41) method of the **DeviceResources** class.</span></span> 
```cpp
auto windowBounds = m_deviceResources->GetLogicalSize();
```

 <span data-ttu-id="ac404-153">Abrufen der Größe des Spielfensters ist entscheidend für die UI-Programmierung.</span><span class="sxs-lookup"><span data-stu-id="ac404-153">Obtaining the size of the game window is essential for UI programming.</span></span> <span data-ttu-id="ac404-154">Die Größe des Fensters erhält eine Messung DIPs (Device independent Pixels) aufgerufen, wobei ein DIP als 1/96 Zoll definiert ist.</span><span class="sxs-lookup"><span data-stu-id="ac404-154">The size of the window is given in a measurement called DIPs (device independent pixels), where a DIP is defined as 1/96 of an inch.</span></span> <span data-ttu-id="ac404-155">Direct2D skaliert die Zeichnungseinheiten in tatsächliche Pixel beim die Zeichnung auftritt, dies mithilfe der Dots per Inch (DPI)-Einstellung von Windows.</span><span class="sxs-lookup"><span data-stu-id="ac404-155">Direct2D scales the drawing units to actual pixels when the drawing occurs, doing so by using the Windows dots per inch (DPI) setting.</span></span> <span data-ttu-id="ac404-156">Wenn Sie Text mit [**DirectWrite**](https://msdn.microsoft.com/en-us/library/windows/desktop/dd368038)zeichnen, geben Sie auf ähnliche Weise DIPs anstelle von Punkten für die Größe der Schriftart.</span><span class="sxs-lookup"><span data-stu-id="ac404-156">Similarly, when you draw text using [**DirectWrite**](https://msdn.microsoft.com/en-us/library/windows/desktop/dd368038), you specify DIPs rather than points for the size of the font.</span></span> <span data-ttu-id="ac404-157">DIPs werden als Gleitkommazahlen angegeben.</span><span class="sxs-lookup"><span data-stu-id="ac404-157">DIPs are expressed as floating point numbers.</span></span>

 

### <a name="displaying-game-state-info"></a><span data-ttu-id="ac404-158">Anzeigen von Informationen zum Spielzustand</span><span class="sxs-lookup"><span data-stu-id="ac404-158">Displaying game state info</span></span>

<span data-ttu-id="ac404-159">Neben der Heads-up-Anzeige enthält das Beispielspiel ein Overlay, die sechs spielzustände darstellt.</span><span class="sxs-lookup"><span data-stu-id="ac404-159">Besides the heads-up display, the game sample has an overlay that represents six game states.</span></span> <span data-ttu-id="ac404-160">Alle Zustände Grundtyp eines großen schwarzen Rechtecks Text für den Spieler zu lesen.</span><span class="sxs-lookup"><span data-stu-id="ac404-160">All states feature a large black rectangle primitive with text for the player to read.</span></span> <span data-ttu-id="ac404-161">Die Rechtecke für bewegungs-/ blickcontroller und die Fadenkreuze werden nicht gezeichnet, da sie in diesen Zuständen nicht aktiv sind.</span><span class="sxs-lookup"><span data-stu-id="ac404-161">The move-look controller rectangles and crosshairs are not drawn because they are not active in these states.</span></span>

<span data-ttu-id="ac404-162">Die Überlagerung wird erstellt, mit der [**GameInfoOverlay**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.h) -Klasse, da wir, welche Text angezeigt wird, um den Zustand des Spiels Manifestschema wechseln.</span><span class="sxs-lookup"><span data-stu-id="ac404-162">The overlay is created using the [**GameInfoOverlay**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.h) class, allowing us to switch out what text is displayed to align with the state of the game.</span></span>

![Status und Aktion des Overlays](images/simple-dx-game-ui-finaloverlay.png)

<span data-ttu-id="ac404-164">Die Überlagerung ist in zwei Abschnitte aufgeteilt: **Status** und **Aktion**.</span><span class="sxs-lookup"><span data-stu-id="ac404-164">The overlay is broken up into two sections: **Status** and **Action**.</span></span> <span data-ttu-id="ac404-165">Der Abschnitt **Status** wird weiter in \*\* **Titel-** und\*\* Rechtecke aufgeteilt.</span><span class="sxs-lookup"><span data-stu-id="ac404-165">The **Status** secton is further broken down into **Title** and **Body** rectangles.</span></span> <span data-ttu-id="ac404-166">Die **Aktion** Abschnitt hat nur ein Rechteck.</span><span class="sxs-lookup"><span data-stu-id="ac404-166">The **Action** section only has one rectangle.</span></span> <span data-ttu-id="ac404-167">Jedes Rechteck hat einen anderen Zweck.</span><span class="sxs-lookup"><span data-stu-id="ac404-167">Each rectangle has a different purpose.</span></span>

-   `titleRectangle` <span data-ttu-id="ac404-168">enthält den Titeltext an.</span><span class="sxs-lookup"><span data-stu-id="ac404-168">contains the title text.</span></span>
-   `bodyRectangle` <span data-ttu-id="ac404-169">enthält den Textkörper.</span><span class="sxs-lookup"><span data-stu-id="ac404-169">contains the body text.</span></span>
-   `actionRectangle` <span data-ttu-id="ac404-170">enthält den Text, der der Spieler zum Ausführen einer bestimmten Aktion.</span><span class="sxs-lookup"><span data-stu-id="ac404-170">contains the text that informs the player to take a specific action.</span></span>

<span data-ttu-id="ac404-171">Das Spiel verfügt über sechs Zustände, die festgelegt werden können.</span><span class="sxs-lookup"><span data-stu-id="ac404-171">The game has six states that can be set.</span></span> <span data-ttu-id="ac404-172">Der Zustand des Spiels vermittelt werden, mit dem **Status** Teil der Überlagerung.</span><span class="sxs-lookup"><span data-stu-id="ac404-172">The state of the game conveyed using the **Status** portion of the overlay.</span></span> <span data-ttu-id="ac404-173">Die Rechtecke für den **Status** werden aktualisiert, indem eine Reihe von Methoden mit den folgenden Staaten entsprechen.</span><span class="sxs-lookup"><span data-stu-id="ac404-173">The **Status** rectangles are updated using a number of methods corresponding with the following states.</span></span>

- <span data-ttu-id="ac404-174">Laden</span><span class="sxs-lookup"><span data-stu-id="ac404-174">Loading</span></span>
- <span data-ttu-id="ac404-175">Anfängliche Start/hohen Punktzahl Statistiken</span><span class="sxs-lookup"><span data-stu-id="ac404-175">Initial start/high score stats</span></span>
- <span data-ttu-id="ac404-176">Levelstart</span><span class="sxs-lookup"><span data-stu-id="ac404-176">Level start</span></span>
- <span data-ttu-id="ac404-177">Spiel angehalten</span><span class="sxs-lookup"><span data-stu-id="ac404-177">Game paused</span></span>
- <span data-ttu-id="ac404-178">Spielende</span><span class="sxs-lookup"><span data-stu-id="ac404-178">Game over</span></span>
- <span data-ttu-id="ac404-179">Spiel gewonnen</span><span class="sxs-lookup"><span data-stu-id="ac404-179">Game won</span></span>


<span data-ttu-id="ac404-180">Die **Aktion** Teil der Überlagerung wird aktualisiert, mit der [**gameinfooverlay:: Setaction**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L522-L564) -Methode, mit der Aktionstext, der auf eine der folgenden festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="ac404-180">The **Action** portion of the overlay is updated using the [**GameInfoOverlay::SetAction**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L522-L564) method, allowing the action text to be set to one of the following.</span></span>
- <span data-ttu-id="ac404-181">"Tap to erneut abspielen"</span><span class="sxs-lookup"><span data-stu-id="ac404-181">"Tap to play again..."</span></span>
- <span data-ttu-id="ac404-182">"Ebene laden, bitte warten"</span><span class="sxs-lookup"><span data-stu-id="ac404-182">"Level loading, please wait ..."</span></span>
- <span data-ttu-id="ac404-183">"Tap to continue..."</span><span class="sxs-lookup"><span data-stu-id="ac404-183">"Tap to continue ..."</span></span>
- <span data-ttu-id="ac404-184">Keine</span><span class="sxs-lookup"><span data-stu-id="ac404-184">None</span></span>

> [!NOTE]
> <span data-ttu-id="ac404-185">Beide Methoden werden erläutert werden im Abschnitt [darstellen des Spielzustands](#representing-game-state) weiter.</span><span class="sxs-lookup"><span data-stu-id="ac404-185">Both of these methods will be discussed further in the [Representing game state](#representing-game-state) section.</span></span>

<span data-ttu-id="ac404-186">Je nachdem, was in das Spiel, den **Status** und die **Aktion** Abschnitt passiert werden Textfelder angepasst.</span><span class="sxs-lookup"><span data-stu-id="ac404-186">Depending on the what's going on in the game, the **Status** and **Action** section text fields are adjusted.</span></span>
<span data-ttu-id="ac404-187">Sehen wir uns ansehen, wie wir initialisieren und zeichnen das Overlay für diese sechs Zustände.</span><span class="sxs-lookup"><span data-stu-id="ac404-187">Let's look at how we initialize and draw the overlay for these six states.</span></span>

### <a name="initializing-and-drawing-the-overlay"></a><span data-ttu-id="ac404-188">Initialisieren und Zeichnen des Overlays</span><span class="sxs-lookup"><span data-stu-id="ac404-188">Initializing and drawing the overlay</span></span>

<span data-ttu-id="ac404-189">**Die sechs Zustände** haben ein paar Dinge gemeinsam, vornehmen, die Ressourcen und Methoden müssen sie sehr ähnlich.</span><span class="sxs-lookup"><span data-stu-id="ac404-189">The six **Status** states have a few things in common, making the resources and methods they need very similar.</span></span>
    - <span data-ttu-id="ac404-190">Sie alle verwenden ein schwarzes Rechteck in der Mitte des Bildschirms als Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="ac404-190">They all use a black rectangle in the center of the screen as their background.</span></span>
    - <span data-ttu-id="ac404-191">Der angezeigte Text ist entweder **Titel** oder eines **Textkörpers** .</span><span class="sxs-lookup"><span data-stu-id="ac404-191">The displayed text is either **Title** or **Body** text.</span></span>
    - <span data-ttu-id="ac404-192">Der Text verwendet die Schriftart Segoe UI und über dem zurück Rechteck gezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="ac404-192">The text uses the Segoe UI font and is drawn on top of the back rectangle.</span></span> 


<span data-ttu-id="ac404-193">Das beispielsspiel verfügt über vier Methoden, die kommen, wenn das Overlay erstellen.</span><span class="sxs-lookup"><span data-stu-id="ac404-193">The game sample has four methods that come into play when creating the overlay.</span></span>
 

#### <a name="gameinfooverlaygameinfooverlay"></a><span data-ttu-id="ac404-194">GameInfoOverlay::GameInfoOverlay</span><span class="sxs-lookup"><span data-stu-id="ac404-194">GameInfoOverlay::GameInfoOverlay</span></span>
<span data-ttu-id="ac404-195">Der [**GameInfoOverlay::GameInfoOverlay**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L30-L78) -Konstruktor initialisiert die Überlagerung, verwalten die Bitmap-Oberfläche, die wir zum Anzeigen von Informationen für den Spieler auf verwenden.</span><span class="sxs-lookup"><span data-stu-id="ac404-195">The [**GameInfoOverlay::GameInfoOverlay**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L30-L78) constructor initializes the overlay, maintaining the bitmap surface that we will use to display info to the player on.</span></span> <span data-ttu-id="ac404-196">Der Konstruktor ruft eine Factory von dem übergebenen hinzu, der verwendet wird, um einen [**ID2D1DeviceContext**](https://msdn.microsoft.com/library/windows/desktop/hh404479) zu erstellen, das das overlayobjekt selbst, um zeichnen kann [**ID2D1Device**](https://msdn.microsoft.com/library/windows/desktop/hh404478) -Objekt.</span><span class="sxs-lookup"><span data-stu-id="ac404-196">The constructor obtains a factory from the [**ID2D1Device**](https://msdn.microsoft.com/library/windows/desktop/hh404478) object passed to it, which it uses to create an [**ID2D1DeviceContext**](https://msdn.microsoft.com/library/windows/desktop/hh404479) that the overlay object itself can draw to.</span></span> [<span data-ttu-id="ac404-197">IDWriteFactory::CreateTextFormat</span><span class="sxs-lookup"><span data-stu-id="ac404-197">IDWriteFactory::CreateTextFormat</span></span>](https://msdn.microsoft.com/en-us/library/windows/desktop/dd368203) 


#### <a name="gameinfooverlaycreatedevicedependentresources"></a><span data-ttu-id="ac404-198">Gameinfooverlay:: Createdevicedependentresources</span><span class="sxs-lookup"><span data-stu-id="ac404-198">GameInfoOverlay::CreateDeviceDependentResources</span></span>
<span data-ttu-id="ac404-199">[**Gameinfooverlay:: Createdevicedependentresources**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L82-L104) handelt es sich um unsere Methode zum Erstellen von Pinsel, die zum Zeichnen von Text verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ac404-199">[**GameInfoOverlay::CreateDeviceDependentResources**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L82-L104) is our method for creating brushes that will be used to draw our text.</span></span> <span data-ttu-id="ac404-200">Zu diesem Zweck müssen wir erhalten ein [**ID2D1DeviceContext2**](https://msdn.microsoft.com/en-us/library/windows/desktop/dn890789) -Objekt ermöglicht die Erstellung und Zeichnen der Geometrie, sowie Funktionen wie z. B. Freihand- und Farbverlauf Gitter rendern.</span><span class="sxs-lookup"><span data-stu-id="ac404-200">To do this, we obtain a [**ID2D1DeviceContext2**](https://msdn.microsoft.com/en-us/library/windows/desktop/dn890789) object which enables the creation and drawing of geometry, plus functionality such as ink and gradient mesh rendering.</span></span> <span data-ttu-id="ac404-201">Anschließend erstellen wir eine Reihe von farbigen Pinsel mit [**ID2D1SolidColorBrush**](https://msdn.microsoft.com/en-us/library/windows/desktop/dd372207) um die folgenden UI-Elemente zu zeichnen.</span><span class="sxs-lookup"><span data-stu-id="ac404-201">We then create a series of colored brushes using [**ID2D1SolidColorBrush**](https://msdn.microsoft.com/en-us/library/windows/desktop/dd372207) to draw the folling UI elements.</span></span>
- <span data-ttu-id="ac404-202">Schwarzen Pinsel für Rechteck Hintergründe</span><span class="sxs-lookup"><span data-stu-id="ac404-202">Black brush for rectangle backgrounds</span></span>
- <span data-ttu-id="ac404-203">Weißen Pinsel für Statustext</span><span class="sxs-lookup"><span data-stu-id="ac404-203">White brush for status text</span></span>
- <span data-ttu-id="ac404-204">Orangefarbenen Pinsel für Aktionstext</span><span class="sxs-lookup"><span data-stu-id="ac404-204">Orange brush for action text</span></span>

#### <a name="deviceresourcessetdpi"></a><span data-ttu-id="ac404-205">DeviceResources::SetDpi</span><span class="sxs-lookup"><span data-stu-id="ac404-205">DeviceResources::SetDpi</span></span>
<span data-ttu-id="ac404-206">Der DPI-Wert des Fensters legt die [**DeviceResources::SetDpi**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/Common/DeviceResources.cpp#L514-L527) -Methode.</span><span class="sxs-lookup"><span data-stu-id="ac404-206">The [**DeviceResources::SetDpi**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/Common/DeviceResources.cpp#L514-L527) method sets the dots per inch of the window.</span></span> <span data-ttu-id="ac404-207">Diese Methode wird aufgerufen, wenn der DPI-Wert geändert wird, und muss angepasst, die geschieht, wenn das Spielfenster geändert wird.</span><span class="sxs-lookup"><span data-stu-id="ac404-207">This method gets called when the DPI is changed and needs to be readjusted which happens when the game window is resized.</span></span> <span data-ttu-id="ac404-208">Nach dem Aktualisieren des DPI-WERTS, ruft diese Methode auch[**deviceresources:: Createwindowsizedependentresources**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/Common/DeviceResources.cpp#L214-L487) , um sicherzustellen, dass jedes Mal, wenn der Fenstergröße erforderliche Ressourcen neu erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="ac404-208">After updating the DPI, this method also calls[**DeviceResources::CreateWindowSizeDependentResources**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/Common/DeviceResources.cpp#L214-L487) to make sure necessary resources are recreated every time the window is resized.</span></span>


#### <a name="gameinfooverlaycreatewindowssizedependentresources"></a><span data-ttu-id="ac404-209">GameInfoOverlay::CreateWindowsSizeDependentResources</span><span class="sxs-lookup"><span data-stu-id="ac404-209">GameInfoOverlay::CreateWindowsSizeDependentResources</span></span>
<span data-ttu-id="ac404-210">Die [**GameInfoOverlay::CreateWindowsSizeDependentResources**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L108-L225) -Methode ist, in denen alle unsere Zeichnung stattfindet.</span><span class="sxs-lookup"><span data-stu-id="ac404-210">The [**GameInfoOverlay::CreateWindowsSizeDependentResources**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L108-L225) method is where all our drawing takes place.</span></span> <span data-ttu-id="ac404-211">Im folgenden finden eine Übersicht über die Methode Schritte.</span><span class="sxs-lookup"><span data-stu-id="ac404-211">The following is an outline of the method's steps.</span></span>
- <span data-ttu-id="ac404-212">Drei Rechtecke werden zum Abschnitt aus dem UI-Text für den **Titel**, **Textkörper**und **Aktion** Text erstellt.</span><span class="sxs-lookup"><span data-stu-id="ac404-212">Three rectangles are created to section off the UI text for the **Title**, **Body**, and **Action** text.</span></span>
    ```cpp 
    m_titleRectangle = D2D1::RectF(
        GameInfoOverlayConstant::SideMargin,
        GameInfoOverlayConstant::TopMargin,
        overlaySize.width - GameInfoOverlayConstant::SideMargin,
        GameInfoOverlayConstant::TopMargin + GameInfoOverlayConstant::TitleHeight
        );
    m_actionRectangle = D2D1::RectF(
        GameInfoOverlayConstant::SideMargin,
        overlaySize.height - (GameInfoOverlayConstant::ActionHeight + GameInfoOverlayConstant::BottomMargin),
        overlaySize.width - GameInfoOverlayConstant::SideMargin,
        overlaySize.height - GameInfoOverlayConstant::BottomMargin
        );
    m_bodyRectangle = D2D1::RectF(
        GameInfoOverlayConstant::SideMargin,
        m_titleRectangle.bottom + GameInfoOverlayConstant::Separator,
        overlaySize.width - GameInfoOverlayConstant::SideMargin,
        m_actionRectangle.top - GameInfoOverlayConstant::Separator
        );
    ```

- <span data-ttu-id="ac404-213">Eine Bitmap erstellt, benannt `m_levelBitmap`, Berücksichtigung der aktuellen DPI-Wert **CreateBitmap**.</span><span class="sxs-lookup"><span data-stu-id="ac404-213">A Bitmap is created named `m_levelBitmap`, taking the current DPI into account using **CreateBitmap**.</span></span>
- `m_levelBitmap` <span data-ttu-id="ac404-214">wird festgelegt, wie unsere 2D Renderziel mit [**ID2D1DeviceContext::SetTarget**](https://msdn.microsoft.com/en-us/library/windows/desktop/hh404533).</span><span class="sxs-lookup"><span data-stu-id="ac404-214">is set as our 2D render target using [**ID2D1DeviceContext::SetTarget**](https://msdn.microsoft.com/en-us/library/windows/desktop/hh404533).</span></span>
- <span data-ttu-id="ac404-215">Die Bitmap mit jedes Pixel vorgenommen deaktiviert ist schwarz [**ID2D1RenderTarget::Clear**](https://msdn.microsoft.com/en-us/library/windows/desktop/dd371772)verwenden.</span><span class="sxs-lookup"><span data-stu-id="ac404-215">The Bitmap is cleared with every pixel made black using [**ID2D1RenderTarget::Clear**](https://msdn.microsoft.com/en-us/library/windows/desktop/dd371772).</span></span>
- <span data-ttu-id="ac404-216">[**ID2D1RenderTarget::beginDraw**](https://msdn.microsoft.com/en-us/library/windows/desktop/dd371768) wird aufgerufen, um die Zeichnung zu initiieren.</span><span class="sxs-lookup"><span data-stu-id="ac404-216">[**ID2D1RenderTarget::BeginDraw**](https://msdn.microsoft.com/en-us/library/windows/desktop/dd371768) is called to initiate drawing.</span></span> 
- <span data-ttu-id="ac404-217">**DrawText** wird aufgerufen, um das Zeichnen des Texts im gespeicherten `m_titleString`, `m_bodyString`, und `m_actionString` im Rechtecke neu auf Rechteck mit dem entsprechenden **ID2D1SolidColorBrush**.</span><span class="sxs-lookup"><span data-stu-id="ac404-217">**DrawText** is called to draw the text stored in `m_titleString`, `m_bodyString`, and `m_actionString` in the approperiate rectangle using the corresponding **ID2D1SolidColorBrush**.</span></span>
- <span data-ttu-id="ac404-218">[**ID2D1RenderTarget::EndDraw**](ID2D1RenderTarget::EndDraw) wird aufgerufen, um alle Zeichenvorgänge auf Beenden `m_levelBitmap`.</span><span class="sxs-lookup"><span data-stu-id="ac404-218">[**ID2D1RenderTarget::EndDraw**](ID2D1RenderTarget::EndDraw) is called to stop all drawing operations on `m_levelBitmap`.</span></span>
- <span data-ttu-id="ac404-219">Eine andere Bitmap erstellt mithilfe von **CreateBitmap** mit dem Namen `m_tooSmallBitmap` als Fallback, nur angezeigt, wenn der Anzeigekonfiguration zu klein für das Spiel verwenden.</span><span class="sxs-lookup"><span data-stu-id="ac404-219">Another Bitmap is created using **CreateBitmap** named `m_tooSmallBitmap` to use as a fallback, showing only if the display configuration is too small for the game.</span></span>
- <span data-ttu-id="ac404-220">Wiederholen Sie die Verfahren zum Zeichnen auf `m_levelBitmap` für `m_tooSmallBitmap`, zeichnen die Zeichenfolge nur einmal `Paused` im Textkörper.</span><span class="sxs-lookup"><span data-stu-id="ac404-220">Repeat process for drawing on `m_levelBitmap` for `m_tooSmallBitmap`, this time only drawing the string `Paused` in the body.</span></span>




<span data-ttu-id="ac404-221">Jetzt können wir müssen sechs Methoden zum Ausfüllen des Text der unsere sechs overlayzustände!</span><span class="sxs-lookup"><span data-stu-id="ac404-221">Now all we need are six methods to fill the text of our six overlay states!</span></span>

### <a name="representing-game-state"></a><span data-ttu-id="ac404-222">Darstellen des Spielzustands</span><span class="sxs-lookup"><span data-stu-id="ac404-222">Representing game state</span></span>


<span data-ttu-id="ac404-223">Jede der sechs overlayzustände im Spiel verfügt über eine entsprechende Methode des **GameInfoOverlay** -Objekts.</span><span class="sxs-lookup"><span data-stu-id="ac404-223">Each of the six overlay states in the game has a corresponding method in the **GameInfoOverlay** object.</span></span> <span data-ttu-id="ac404-224">Diese Methoden zeichnen eine Variante des Overlays, um dem Spieler explizite Informationen zum Spiel selbst mitzuteilen.</span><span class="sxs-lookup"><span data-stu-id="ac404-224">These methods draw a variation of the overlay to communicate explicit info to the player about the game itself.</span></span> <span data-ttu-id="ac404-225">Diese Kommunikation wird mit einer Zeichenfolge, die \*\* **Titel-** und\*\* dargestellt.</span><span class="sxs-lookup"><span data-stu-id="ac404-225">This communication is represented with a **Title** and **Body** string.</span></span> <span data-ttu-id="ac404-226">Da im Beispiel bereits konfiguriert werden, die Ressourcen und das Layout für diese Informationen, wenn es initialisiert wurde und mit der [**gameinfooverlay:: Createdevicedependentresources**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L82-L104) -Methode, muss es nur die Überlagerung Zustandsspezifische Zeichenfolgen angeben.</span><span class="sxs-lookup"><span data-stu-id="ac404-226">Because the sample already configured the resources and layout for this info when it was initialized and with the [**GameInfoOverlay::CreateDeviceDependentResources**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L82-L104) method, it only needs to provide the overlay state-specific strings.</span></span>

<span data-ttu-id="ac404-227">Der **Status** Teil der Überlagerung wird mit einem Aufruf von einer der folgenden Methoden festgelegt.</span><span class="sxs-lookup"><span data-stu-id="ac404-227">The **Status** portion of the overlay is set with a call to one of the following methods.</span></span>

<span data-ttu-id="ac404-228">Spielzustand</span><span class="sxs-lookup"><span data-stu-id="ac404-228">Game state</span></span> | <span data-ttu-id="ac404-229">Status set-Methode</span><span class="sxs-lookup"><span data-stu-id="ac404-229">Status set method</span></span> | <span data-ttu-id="ac404-230">Statusfelder</span><span class="sxs-lookup"><span data-stu-id="ac404-230">Status fields</span></span>
:----- | :------- | :---------
<span data-ttu-id="ac404-231">Laden</span><span class="sxs-lookup"><span data-stu-id="ac404-231">Loading</span></span> | [<span data-ttu-id="ac404-232">GameInfoOverlay::SetGameLoading</span><span class="sxs-lookup"><span data-stu-id="ac404-232">GameInfoOverlay::SetGameLoading</span></span>](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L254-L306) |**<span data-ttu-id="ac404-233">Title</span><span class="sxs-lookup"><span data-stu-id="ac404-233">Title</span></span>**</br><span data-ttu-id="ac404-234">Laden von Ressourcen</span><span class="sxs-lookup"><span data-stu-id="ac404-234">Loading Resources</span></span> </br>**<span data-ttu-id="ac404-235">Textkörper</span><span class="sxs-lookup"><span data-stu-id="ac404-235">Body</span></span>**</br> <span data-ttu-id="ac404-236">Inkrementell druckt "." zum Laden von Aktivität implizieren.</span><span class="sxs-lookup"><span data-stu-id="ac404-236">Incrementally prints "." to imply loading activity.</span></span>
<span data-ttu-id="ac404-237">Anfängliche Start/hohen Punktzahl Statistiken</span><span class="sxs-lookup"><span data-stu-id="ac404-237">Initial start/high score stats</span></span> | [<span data-ttu-id="ac404-238">Setgamestats</span><span class="sxs-lookup"><span data-stu-id="ac404-238">GameInfoOverlay::SetGameStats</span></span>](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L310-L354) |**<span data-ttu-id="ac404-239">Title</span><span class="sxs-lookup"><span data-stu-id="ac404-239">Title</span></span>**</br><span data-ttu-id="ac404-240">Bestenliste</span><span class="sxs-lookup"><span data-stu-id="ac404-240">High Score</span></span></br> **<span data-ttu-id="ac404-241">Textkörper</span><span class="sxs-lookup"><span data-stu-id="ac404-241">Body</span></span>**</br> <span data-ttu-id="ac404-242">Ebenen abgeschlossen #</span><span class="sxs-lookup"><span data-stu-id="ac404-242">Levels Completed #</span></span> </br><span data-ttu-id="ac404-243">Insgesamt verweist #</span><span class="sxs-lookup"><span data-stu-id="ac404-243">Total Points #</span></span></br><span data-ttu-id="ac404-244">Insgesamt Bildschirmdarstellung #</span><span class="sxs-lookup"><span data-stu-id="ac404-244">Total Shots #</span></span>
<span data-ttu-id="ac404-245">Levelstart</span><span class="sxs-lookup"><span data-stu-id="ac404-245">Level start</span></span> | [<span data-ttu-id="ac404-246">GameInfoOverlay::SetLevelStart</span><span class="sxs-lookup"><span data-stu-id="ac404-246">GameInfoOverlay::SetLevelStart</span></span>](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L413-L471) |**<span data-ttu-id="ac404-247">Title</span><span class="sxs-lookup"><span data-stu-id="ac404-247">Title</span></span>**</br><span data-ttu-id="ac404-248">Ebene #</span><span class="sxs-lookup"><span data-stu-id="ac404-248">Level #</span></span></br>**<span data-ttu-id="ac404-249">Textkörper</span><span class="sxs-lookup"><span data-stu-id="ac404-249">Body</span></span>**</br><span data-ttu-id="ac404-250">Ebene objektiven Beschreibung.</span><span class="sxs-lookup"><span data-stu-id="ac404-250">Level objective description.</span></span>
<span data-ttu-id="ac404-251">Spiel angehalten</span><span class="sxs-lookup"><span data-stu-id="ac404-251">Game paused</span></span> | [<span data-ttu-id="ac404-252">GameInfoOverlay::SetPause</span><span class="sxs-lookup"><span data-stu-id="ac404-252">GameInfoOverlay::SetPause</span></span>](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L475-L502) |**<span data-ttu-id="ac404-253">Title</span><span class="sxs-lookup"><span data-stu-id="ac404-253">Title</span></span>**</br><span data-ttu-id="ac404-254">Spiel angehalten</span><span class="sxs-lookup"><span data-stu-id="ac404-254">Game Paused</span></span></br>**<span data-ttu-id="ac404-255">Textkörper</span><span class="sxs-lookup"><span data-stu-id="ac404-255">Body</span></span>**</br><span data-ttu-id="ac404-256">Keine</span><span class="sxs-lookup"><span data-stu-id="ac404-256">None</span></span>
<span data-ttu-id="ac404-257">Spielende</span><span class="sxs-lookup"><span data-stu-id="ac404-257">Game over</span></span> | [<span data-ttu-id="ac404-258">GameInfoOverlay::SetGameOver</span><span class="sxs-lookup"><span data-stu-id="ac404-258">GameInfoOverlay::SetGameOver</span></span>](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L358-L409) |**<span data-ttu-id="ac404-259">Title</span><span class="sxs-lookup"><span data-stu-id="ac404-259">Title</span></span>**</br><span data-ttu-id="ac404-260">Spielende</span><span class="sxs-lookup"><span data-stu-id="ac404-260">Game Over</span></span></br> **<span data-ttu-id="ac404-261">Textkörper</span><span class="sxs-lookup"><span data-stu-id="ac404-261">Body</span></span>**</br> <span data-ttu-id="ac404-262">Ebenen abgeschlossen #</span><span class="sxs-lookup"><span data-stu-id="ac404-262">Levels Completed #</span></span> </br><span data-ttu-id="ac404-263">Insgesamt verweist #</span><span class="sxs-lookup"><span data-stu-id="ac404-263">Total Points #</span></span></br><span data-ttu-id="ac404-264">Insgesamt Bildschirmdarstellung #</span><span class="sxs-lookup"><span data-stu-id="ac404-264">Total Shots #</span></span></br><span data-ttu-id="ac404-265">Ebenen abgeschlossen #</span><span class="sxs-lookup"><span data-stu-id="ac404-265">Levels Completed #</span></span></br><span data-ttu-id="ac404-266">Hohen Punktzahl #</span><span class="sxs-lookup"><span data-stu-id="ac404-266">High Score #</span></span>
<span data-ttu-id="ac404-267">Spiel gewonnen</span><span class="sxs-lookup"><span data-stu-id="ac404-267">Game won</span></span> | [<span data-ttu-id="ac404-268">GameInfoOverlay::SetGameOver</span><span class="sxs-lookup"><span data-stu-id="ac404-268">GameInfoOverlay::SetGameOver</span></span>](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L358-L409) |**<span data-ttu-id="ac404-269">Title</span><span class="sxs-lookup"><span data-stu-id="ac404-269">Title</span></span>**</br><span data-ttu-id="ac404-270">Sie haben gewonnen!</span><span class="sxs-lookup"><span data-stu-id="ac404-270">You WON!</span></span></br> **<span data-ttu-id="ac404-271">Textkörper</span><span class="sxs-lookup"><span data-stu-id="ac404-271">Body</span></span>**</br> <span data-ttu-id="ac404-272">Ebenen abgeschlossen #</span><span class="sxs-lookup"><span data-stu-id="ac404-272">Levels Completed #</span></span> </br><span data-ttu-id="ac404-273">Insgesamt verweist #</span><span class="sxs-lookup"><span data-stu-id="ac404-273">Total Points #</span></span></br><span data-ttu-id="ac404-274">Insgesamt Bildschirmdarstellung #</span><span class="sxs-lookup"><span data-stu-id="ac404-274">Total Shots #</span></span></br><span data-ttu-id="ac404-275">Ebenen abgeschlossen #</span><span class="sxs-lookup"><span data-stu-id="ac404-275">Levels Completed #</span></span></br><span data-ttu-id="ac404-276">Hohen Punktzahl #</span><span class="sxs-lookup"><span data-stu-id="ac404-276">High Score #</span></span>




<span data-ttu-id="ac404-277">Mit der Methode [**GameInfoOverlay::CreateWindowSizeDependentResources**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L117-L134) deklariert das Beispiel drei rechteckige Bereiche, die bestimmten Bereichen des Overlays entsprechen.</span><span class="sxs-lookup"><span data-stu-id="ac404-277">With the [**GameInfoOverlay::CreateWindowSizeDependentResources**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L117-L134) method, the sample declared three rectangular areas that correspond to specific regions of the overlay.</span></span>



<span data-ttu-id="ac404-278">Unter Berücksichtigung dieser Bereiche wollen wir nun eine der zustandsspezifischen Methoden (**GameInfoOverlay::SetGameStats**) näher untersuchen und sehen, wie das Overlay gezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="ac404-278">With these areas in mind, let's look at one of the state-specific methods, **GameInfoOverlay::SetGameStats**, and see how the overlay is drawn.</span></span>

```cpp
void GameInfoOverlay::SetGameStats(int maxLevel, int hitCount, int shotCount)
{
    int length;

    auto d2dContext = m_deviceResources->GetD2DDeviceContext();

    d2dContext->SetTarget(m_levelBitmap.Get());
    d2dContext->BeginDraw();
    d2dContext->SetTransform(D2D1::Matrix3x2F::Identity());
    d2dContext->FillRectangle(&m_titleRectangle, m_backgroundBrush.Get());
    d2dContext->FillRectangle(&m_bodyRectangle, m_backgroundBrush.Get());
    m_titleString = "High Score";

    d2dContext->DrawText(
        m_titleString->Data(),
        m_titleString->Length(),
        m_textFormatTitle.Get(),
        m_titleRectangle,
        m_textBrush.Get()
        );
    length = swprintf_s(
        wsbuffer,
        bufferLength,
        L"Levels Completed %d\nTotal Points %d\nTotal Shots %d",
        maxLevel,
        hitCount,
        shotCount
        );
    m_bodyString = ref new Platform::String(wsbuffer, length);
    d2dContext->DrawText(
        m_bodyString->Data(),
        m_bodyString->Length(),
        m_textFormatBody.Get(),
        m_bodyRectangle,
        m_textBrush.Get()
        );

    // We ignore D2DERR_RECREATE_TARGET here. This error indicates that the device
    // is lost. It will be handled during the next call to Present.
    HRESULT hr = d2dContext->EndDraw();
    if (hr != D2DERR_RECREATE_TARGET)
    {
        // The D2DERR_RECREATE_TARGET indicates there has been a problem with the underlying
        // D3D device.  All subsequent rendering will be ignored until the device is recreated.
        // This error will be propagated and the appropriate D3D error will be returned from the
        // swapchain->Present(...) call.   At that point, the sample will recreate the device
        // and all associated resources.  As a result, the D2DERR_RECREATE_TARGET doesn't
        // need to be handled here.
        DX::ThrowIfFailed(hr);
    }
}
```

<span data-ttu-id="ac404-279">Mit dem Direct2D-Gerätekontext, den das **GameInfoOverlay** -Objekt initialisiert, füllt diese Methode die Titel- und Rechtecke mit Schwarz mithilfe des Hintergrundpinsels.</span><span class="sxs-lookup"><span data-stu-id="ac404-279">Using the Direct2D device context that the **GameInfoOverlay** object initialized, this method fills the title and body rectangles with black using the background brush.</span></span> <span data-ttu-id="ac404-280">Sie zeichnet mit dem weißen Textpinsel den Text für die Zeichenfolge „High Score“ im Titelrechteck und eine Zeichenfolge mit den aktualisierten Spielzuständen im Textkörperrechteck.</span><span class="sxs-lookup"><span data-stu-id="ac404-280">It draws the text for the "High Score" string to the title rectangle and a string containing the updates game state information to the body rectangle using the white text brush.</span></span>


<span data-ttu-id="ac404-281">Das aktionsrechteck wird durch einen nachfolgenden Aufruf von [**gameinfooverlay:: Setaction**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L522-L564) von einer Methode für das **GameMain** -Objekt, die die **gameinfooverlay:: Setaction** um zu bestimmen, die passende Meldung für erforderlichen Informationen zum Spielzustand bereitstellt aktualisiert die Players, z. B. "Tap to continue".</span><span class="sxs-lookup"><span data-stu-id="ac404-281">The action rectangle is updated by a subsequent call to [**GameInfoOverlay::SetAction**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L522-L564) from a method on the **GameMain** object, which provides the game state info needed by **GameInfoOverlay::SetAction** to determine the right message to the player, such as "Tap to continue".</span></span>

<span data-ttu-id="ac404-282">Das Overlay für einen bestimmten Zustand wird ausgewählt, in der [**GameMain::SetGameInfoOverlay**](https://github.com/Microsoft/Windows-universal-samples/blob/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/Simple3DGameXaml/cpp/GameMain.cpp#L606-L661) -Methode wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="ac404-282">The overlay for any given state is chosen in the [**GameMain::SetGameInfoOverlay**](https://github.com/Microsoft/Windows-universal-samples/blob/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/Simple3DGameXaml/cpp/GameMain.cpp#L606-L661) method like this:</span></span>

```cpp
void GameMain::SetGameInfoOverlay(GameInfoOverlayState state)
{
    m_gameInfoOverlayState = state;
    switch (state)
    {
    case GameInfoOverlayState::Loading:
        m_uiControl->SetGameLoading();
        break;

    case GameInfoOverlayState::GameStats:
        m_uiControl->SetGameStats(
            m_game->HighScore().levelCompleted + 1,
            m_game->HighScore().totalHits,
            m_game->HighScore().totalShots
            );
        break;

    case GameInfoOverlayState::LevelStart:
        m_uiControl->SetLevelStart(
            m_game->LevelCompleted() + 1,
            m_game->CurrentLevel()->Objective(),
            m_game->CurrentLevel()->TimeLimit(),
            m_game->BonusTime()
            );
        break;

    case GameInfoOverlayState::GameOverCompleted:
        m_uiControl->SetGameOver(
            true,
            m_game->LevelCompleted() + 1,
            m_game->TotalHits(),
            m_game->TotalShots(),
            m_game->HighScore().totalHits
            );
        break;

    case GameInfoOverlayState::GameOverExpired:
        m_uiControl->SetGameOver(
            false,
            m_game->LevelCompleted(),
            m_game->TotalHits(),
            m_game->TotalShots(),
            m_game->HighScore().totalHits
            );
        break;

    case GameInfoOverlayState::Pause:
        m_uiControl->SetPause(
            m_game->LevelCompleted() + 1,
            m_game->TotalHits(),
            m_game->TotalShots(),
            m_game->TimeRemaining()
            );
        break;
    }
}
```

<span data-ttu-id="ac404-283">Das Spiel verfügt jetzt über eine Möglichkeit für den Spieler basierend auf dem Spielzustand Textinformationen, und wir haben eine Möglichkeit, wechseln, was sie während des Spiels angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ac404-283">Now the game has a way to communicate text info to the player based on game state, and we have a way of switching what's displayed to them throughout the game.</span></span>

### <a name="next-steps"></a><span data-ttu-id="ac404-284">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="ac404-284">Next steps</span></span>

<span data-ttu-id="ac404-285">Im nächsten Thema zum [Hinzufügen von Steuerungen](tutorial--adding-controls.md) untersuchen wir, wie der Spieler mit dem Beispielspiel interagiert und wie sich der Spielzustand durch Eingaben ändert.</span><span class="sxs-lookup"><span data-stu-id="ac404-285">In the next topic, [Adding controls](tutorial--adding-controls.md), we look at how the player interacts with the game sample, and how input changes game state.</span></span>



 




