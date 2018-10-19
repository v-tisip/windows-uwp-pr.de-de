---
author: abbycar
title: Hinzufügen einer Benutzeroberfläche
description: Hier erfahren Sie, wie Sie ein 2D benutzeroberflächenoverlay zu einem DirectX-UWP-Spiel hinzufügen.
ms.assetid: fa40173e-6cde-b71b-e307-db90f0388485
ms.author: abigailc
ms.date: 10/24/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Spiele, Benutzeroberfläche, directx
ms.localizationpriority: medium
ms.openlocfilehash: 3a82958f01530b84276823ea8d025d292bd664ac
ms.sourcegitcommit: 310a4555fedd4246188a98b31f6c094abb33ec60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "5126981"
---
# <a name="add-a-user-interface"></a>Hinzufügen einer Benutzeroberfläche


Nun, da unser Spiel seine 3D-Grafik verfügt, ist es Zeit zu konzentrieren Sie sich auf einige 2D Elemente hinzufügen, damit das Spiel dem Spieler Feedback zum Spielzustand bereitstellen kann. Dies kann erfolgen durch Hinzufügen von einfache Menüoptionen und Head-Up-Anzeigekomponenten der 3D-Grafiken Grafikpipeline Ausgabe.

>[!Note]
>Wenn Sie den neuesten Code für dieses Beispiel noch nicht heruntergeladen haben, wechseln Sie zu [Direct3D-Spielbeispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/Simple3DGameDX). Dieses Beispiel gehört zu einer großen Sammlung von UWP-Featurebeispielen. Anweisungen zum Herunterladen des Beispiels finden Sie unter [Abrufen der UWP-Beispiele von GitHub](https://docs.microsoft.com/windows/uwp/get-started/get-uwp-app-samples).

## <a name="objective"></a>Ziel

Fügen Sie mit Direct2D, eine Reihe von benutzeroberflächengrafiken und-Verhalten zu unseren UWP-DirectX-Spiel-einschließlich:
- Heads-Up-Anzeige, einschließlich der [bewegungs-/ blickcontroller](tutorial--adding-controls.md) ist Rechtecke
- Spielzustand Menüs


## <a name="the-user-interface-overlay"></a>Benutzeroberflächenoverlay


Während es viele Möglichkeiten zum Anzeigen von Text und UI-Elementen in einem DirectX-Spiel gibt, werden zu konzentrieren wir zur Verwendung von [Direct2D](https://msdn.microsoft.com/library/windows/apps/dd370990.aspx). Wir werden auch [DirectWrite](https://msdn.microsoft.com/library/windows/desktop/dd368038) für die Textelemente verwendet werden.


Direct2D ist eine Reihe von 2D zeichnen APIs zum Zeichnen von pixelbasierten Grundtypen und Effekten. Wenn der Anfang der Entwicklung mit Direct2D stehen, empfiehlt es sich Einfachheit halber. Komplexe Layouts und Benutzeroberflächenverhalten erfordern Zeit und Planung. Wenn Ihr Spiel eine komplexe Benutzeroberfläche wie in Simulations- und Strategiespielen vorkommen, erfordert sollten Sie stattdessen von XAML-Code.

> [!NOTE]
> Informationen zum Entwickeln einer Benutzeroberfläche mit XAML in einem UWP-DirectX-Spiel finden Sie in der [Erweitern des spielbeispiels](tutorial-resources.md).

Direct2D ist nicht speziell für Benutzeroberflächen oder Layouts wie HTML- und XAML. Es stellt keine Benutzeroberflächenkomponenten wie Listen, Felder oder Schaltflächen bereit. Es bietet auch keine Layoutkomponenten wie Divs, Tabellen oder Raster bereit.


Für dieses Spielbeispiel sind wir zwei hauptoberflächenkomponenten.
1. Für die Bewertung und spielinterne Steuerelemente Heads-up-Anzeige.
2. Ein Overlay zum Anzeigen von Spielzustand Text und Optionen wie etwa pauseninformationen und Ebene Startoptionen.

### <a name="using-direct2d-for-a-heads-up-display"></a>Verwenden von Direct2D für die Heads-Up-Anzeige

Die folgende Abbildung zeigt die spielinterne Heads-up-Anzeige für das Beispiel. Es ist einfach und übersichtlich, sodass sich der Spieler auf die Navigation in der 3D-Welt und das Abschießen der Ziele konzentrieren. Eine gute Benutzeroberfläche oder Head-Up-Anzeige müssen Sie die Möglichkeit des Players zum Verarbeiten und reagieren auf die Ereignisse im Spiel nie erschweren.

![Screenshot des Spieloverlays](images/simple-dx-game-ui-overlay.png)

Die Überlagerung umfasst die folgenden grundlegenden primitiven.
- In der oberen rechten Ecke, die der Spieler über informiert [**DirectWrite**](https://msdn.microsoft.com/en-us/library/windows/desktop/dd368038) -text 
    - Treffern
    - Anzahl von Screenshots der Spieler vorgenommene
    - Verbleibende Zeit auf der Stufe ""
    - Aktuelle Levelnummer 
- Zwei sich schneidende Liniensegmente verwendet, um ein Fadenkreuz bilden
- Zwei Rechtecke an den Ecken unten für den [bewegungs-/ blickcontroller](tutorial--adding-controls.md) lassen. 


Der spielinterne Head-Up-Anzeigezustand des Overlays wird in der [**gamehud:: Render**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameHud.cpp#L234-L358) -Methode der Klasse [**GameHud**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameHud.h) gezeichnet. In dieser Methode wird das Direct2D-Overlay, das unsere Benutzeroberfläche darstellt aktualisiert, und die Änderungen in die Anzahl von Treffern, Zeit verbleibenden und Ebene Anzahl an.

Wenn das Spiel initialisiert wurde, fügen wir `TotalHits()`, `TotalShots()`, und `TimeRemaining()` auf eine [**Swprintf_s**](https://docs.microsoft.com/cpp/c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l) -Puffer und geben Sie das Drucken Format. Wir können dann mit der Methode [**DrawText**](https://msdn.microsoft.com/en-us/library/windows/desktop/dd742848) zeichnen. Wir gehen Sie genauso für den aktuellen Ebene Indikator zeichnen leere Zahlen, die nicht abgeschlossene Ebenen wie ➀ anzeigen und gefüllte Zahlen wie ➊ um anzuzeigen, dass die spezifischen Level abgeschlossen wurde.


Der folgende Codeausschnitt führt durch die **gamehud:: Render** -Methode für 
- Erstellen einer Bitmap mit [** ID2D1RenderTarget::DrawBitmap **](https://msdn.microsoft.com/en-us/library/windows/desktop/dd371880)
- UI-Bereiche unterteilen in Rechtecke mit [ **D2D1::RectF**](https://msdn.microsoft.com/en-us/library/windows/desktop/dd368184)
- Mit **DrawText** Textelemente werden kann

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

Unterbrechen die Methode unten dieser Teil der [**gamehud:: Render**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameHud.cpp#L320-L358) -Methode zeichnet weiter, unsere verschieben und das schießrechteck werden mit [**ID2D1RenderTarget::DrawRectangle**](https://msdn.microsoft.com/library/windows/desktop/dd371902)und Fadenkreuze mit zwei Aufrufe von [**ID2D1RenderTarget::DrawLine**](https://msdn.microsoft.com/library/windows/desktop/dd371895).

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

In der **gamehud:: Render** -Methode speichern wir die logische Größe das Fenster des Spiels in das `windowBounds` Variable. Dies wird verwendet, die [`GetLogicalSize`](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/Common/DeviceResources.h#L41) Methode der Klasse **DeviceResources** . 
```cpp
auto windowBounds = m_deviceResources->GetLogicalSize();
```

 Abrufen der Größe des Spielfensters ist entscheidend für die UI-Programmierung. Die Größe des Fensters erhält eine Messung aufgerufen DIPs (geräteunabhängige Pixel), wobei ein DIP als 1/96 Zoll definiert ist. Direct2D skaliert die Zeichnungseinheiten in tatsächliche Pixel beim die Zeichnung auftritt, dies mithilfe der Dots per Inch (DPI)-Einstellung von Windows. Wenn Sie Text mit [**DirectWrite**](https://msdn.microsoft.com/en-us/library/windows/desktop/dd368038)zeichnen, geben Sie auf ähnliche Weise DIPs anstelle von Punkten für die Größe der Schriftart. DIPs werden als Gleitkommazahlen angegeben.

 

### <a name="displaying-game-state-info"></a>Anzeigen von Informationen zum Spielzustand

Neben der Heads-up-Anzeige enthält das Beispielspiel ein Overlay, die sechs spielzustände darstellt. Alle Zustände der Grundtyp eines großen schwarzen Rechtecks mit Text für den Spieler zu lesen. Die Rechtecke für bewegungs-/ blickcontroller und die Fadenkreuze werden nicht gezeichnet, da sie in diesen Zuständen nicht aktiv sind.

Die Überlagerung wird erstellt mit der [**GameInfoOverlay**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.h) -Klasse, da wir, welche Text angezeigt wird, um den Zustand des Spiels Manifestschema wechseln.

![Status und die Aktion des Overlays](images/simple-dx-game-ui-finaloverlay.png)

Die Überlagerung ist in zwei Abschnitte aufgeteilt: **Status** und die **Aktion zu sehen**. Der Abschnitt **Status** wird weiter in ** **Titel-** und** Rechtecke unterteilt. Der Abschnitt **Aktion** hat nur ein Rechteck. Jedes Rechteck hat einen anderen Zweck.

-   `titleRectangle` enthält den Titeltext an.
-   `bodyRectangle` enthält die Textkörper.
-   `actionRectangle` enthält den Text, der der Spieler zum Ausführen einer bestimmten Aktion.

Das Spiel verfügt über sechs Zustände, die festgelegt werden können. Der Zustand des Spiels vermittelt werden, mit dem **Status** Teil der Überlagerung. Die Rechtecke für den **Status** werden aktualisiert, indem eine Reihe von Methoden mit den folgenden Staaten entsprechen.

- Laden
- Anfängliche Start/hoch Punktestand Statistiken
- Levelstart
- Spiel angehalten
- Spielende
- Spiel gewonnen


Die **Aktion** Teil der Überlagerung wird mit der [**gameinfooverlay:: Setaction**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L522-L564) -Methode, mit der Aktionstext, der auf eine der folgenden festgelegt werden aktualisiert.
- "Tap to erneut abspielen"
- "Ebene laden, bitte warten"
- "Tap to continue..."
- Keine

> [!NOTE]
> Beide Methoden erläutert im Abschnitt [darstellen des Spielzustands](#representing-game-state) weiter.

Je nachdem, was in das Spiel, den **Status** und die **Aktion** Abschnitt vor sich geht werden Textfelder angepasst.
Sehen wir uns ansehen, wie wir initialisieren und zeichnen Sie das Overlay für diese sechs Zustände.

### <a name="initializing-and-drawing-the-overlay"></a>Initialisieren und Zeichnen des Overlays

**Die sechs Zustände** haben ein paar Dinge gemeinsam, machen die Ressourcen und Methoden müssen diese sehr ähnlich.
    - Sie alle verwenden – ein schwarzes Rechteck in der Mitte des Bildschirms als Hintergrund.
    - Der angezeigte Text ist entweder **Titel** oder eines **Textkörpers** .
    - Der Text verwendet die Schriftart Segoe UI und über dem zurück Rechteck gezeichnet wird. 


Das beispielsspiel verfügt über vier Methoden, die kommen, wenn das Overlay erstellen.
 

#### <a name="gameinfooverlaygameinfooverlay"></a>GameInfoOverlay::GameInfoOverlay
Der [**GameInfoOverlay::GameInfoOverlay**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L30-L78) -Konstruktor initialisiert die Überlagerung, verwalten die Bitmap-Oberfläche, die wir zum Anzeigen von Informationen für den Spieler auf verwenden. Der Konstruktor ruft eine Factory von dem übergebenen darauf, die verwendet wird, um einen [**ID2D1DeviceContext**](https://msdn.microsoft.com/library/windows/desktop/hh404479) zu erstellen, das das overlayobjekt selbst, um zeichnen kann [**ID2D1Device**](https://msdn.microsoft.com/library/windows/desktop/hh404478) -Objekt. [IDWriteFactory::CreateTextFormat](https://msdn.microsoft.com/en-us/library/windows/desktop/dd368203) 


#### <a name="gameinfooverlaycreatedevicedependentresources"></a>Gameinfooverlay:: Createdevicedependentresources
[**Gameinfooverlay:: Createdevicedependentresources**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L82-L104) handelt es sich um unsere Methode zum Erstellen von Pinsel, die zum Zeichnen von Text verwendet werden. Zu diesem Zweck müssen wir Abrufen eines Objekts [**ID2D1DeviceContext2**](https://msdn.microsoft.com/en-us/library/windows/desktop/dn890789) ermöglicht die Erstellung und Zeichnen der Geometrie, plus Funktionen wie z. B. Freihand- und Farbverlauf Gitter Rendering. Anschließend erstellen wir eine Reihe von farbigen Pinsel mit [**ID2D1SolidColorBrush**](https://msdn.microsoft.com/en-us/library/windows/desktop/dd372207) um die folgenden UI-Elemente zu zeichnen.
- Schwarzen Pinsel für Rechteck Hintergründe
- Weißen Pinsel für Statustext
- Orangefarbenen Pinsel für Aktionstext

#### <a name="deviceresourcessetdpi"></a>DeviceResources::SetDpi
Der DPI-Wert des Fensters legt die [**DeviceResources::SetDpi**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/Common/DeviceResources.cpp#L514-L527) -Methode. Diese Methode wird aufgerufen, wenn der DPI-Wert geändert wird, und muss angepasst, die tritt auf, wenn das Spielfenster geändert wird. Nach dem Aktualisieren des DPI-WERTS, ruft diese Methode auch[**deviceresources:: Createwindowsizedependentresources**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/Common/DeviceResources.cpp#L214-L487) , um sicherzustellen, dass die erforderliche Ressourcen neu erstellt werden, jedes Mal, wenn der Fenstergröße.


#### <a name="gameinfooverlaycreatewindowssizedependentresources"></a>GameInfoOverlay::CreateWindowsSizeDependentResources
Die Methode [**GameInfoOverlay::CreateWindowsSizeDependentResources**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L108-L225) ist, in denen alle unsere Zeichnung stattfindet. Im folgenden finden eine Übersicht über die Methode Schritte.
- Drei Rechtecke werden zum Abschnitt Deaktivieren der UI-Text für den **Titel**, **Text**und **Aktion** Text erstellt.
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

- Eine Bitmap erstellt, benannt `m_levelBitmap`, Berücksichtigung der aktuellen DPI-Wert **CreateBitmap**.
- `m_levelBitmap` wird festgelegt, wie unsere 2D Renderziel mit [**ID2D1DeviceContext::SetTarget**](https://msdn.microsoft.com/en-us/library/windows/desktop/hh404533).
- Die Bitmap mit jedes Pixel vorgenommen deaktiviert ist schwarz [**ID2D1RenderTarget::Clear**](https://msdn.microsoft.com/en-us/library/windows/desktop/dd371772)verwenden.
- [**ID2D1RenderTarget::beginDraw**](https://msdn.microsoft.com/en-us/library/windows/desktop/dd371768) wird aufgerufen, um die Zeichnung zu initiieren. 
- **DrawText** wird aufgerufen, um Zeichnen des Texts im gespeicherten `m_titleString`, `m_bodyString`, und `m_actionString` in die Rechtecke neu auf Rechteck mit dem entsprechenden **ID2D1SolidColorBrush**.
- [**ID2D1RenderTarget::EndDraw**](ID2D1RenderTarget::EndDraw) wird aufgerufen, um alle Zeichenvorgänge auf Beenden `m_levelBitmap`.
- Eine andere Bitmap wird mit **CreateBitmap** mit dem Namen erstellt `m_tooSmallBitmap` als Fallback, nur angezeigt, wenn der Anzeigekonfiguration zu klein für das Spiel verwendet.
- Wiederholen Sie die Verfahren zum Zeichnen auf `m_levelBitmap` für `m_tooSmallBitmap`, zeichnen die Zeichenfolge nur einmal `Paused` im Textkörper.




Jetzt können wir brauchen sechs Methoden auf, um den Text der unsere sechs overlayzustände füllen!

### <a name="representing-game-state"></a>Darstellen des Spielzustands


Jede der sechs overlayzustände im Spiel verfügt über eine entsprechende Methode des Objekts **GameInfoOverlay** . Diese Methoden zeichnen eine Variante des Overlays, um dem Spieler explizite Informationen zum Spiel selbst mitzuteilen. Diese Kommunikation wird mit einer Zeichenfolge, die ** **Titel-** und** dargestellt. Da im Beispiel bereits konfiguriert werden, die Ressourcen und das Layout für diese Informationen, wenn es initialisiert wurde und mit der [**gameinfooverlay:: Createdevicedependentresources**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L82-L104) -Methode, muss es nur die Überlagerung Zustandsspezifische Zeichenfolgen angeben.

Der **Status** Teil der Überlagerung wird mit einem Aufruf von einer der folgenden Methoden festgelegt.

Spielzustand | Status set-Methode | Statusfelder
:----- | :------- | :---------
Laden | [GameInfoOverlay::SetGameLoading](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L254-L306) |**Title**</br>Das Laden von Ressourcen </br>**Textkörper**</br> Inkrementell druckt "." zum Laden von Aktivität implizieren.
Anfängliche Start/hoch Punktestand Statistiken | [Setgamestats](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L310-L354) |**Title**</br>Bestenliste</br> **Textkörper**</br> Ebenen abgeschlossen # </br>Insgesamt verweist #</br>Insgesamt Bildschirmdarstellung #
Levelstart | [GameInfoOverlay::SetLevelStart](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L413-L471) |**Title**</br>Ebene #</br>**Textkörper**</br>Objektiven Beschreibung.
Spiel angehalten | [GameInfoOverlay::SetPause](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L475-L502) |**Title**</br>Spiel angehalten</br>**Textkörper**</br>Keine
Spielende | [GameInfoOverlay::SetGameOver](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L358-L409) |**Title**</br>Spielende</br> **Textkörper**</br> Ebenen abgeschlossen # </br>Insgesamt verweist #</br>Insgesamt Bildschirmdarstellung #</br>Ebenen abgeschlossen #</br>Hohen Punktzahl #
Spiel gewonnen | [GameInfoOverlay::SetGameOver](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L358-L409) |**Title**</br>Sie haben gewonnen!</br> **Textkörper**</br> Ebenen abgeschlossen # </br>Insgesamt verweist #</br>Insgesamt Bildschirmdarstellung #</br>Ebenen abgeschlossen #</br>Hohen Punktzahl #




Mit der Methode [**GameInfoOverlay::CreateWindowSizeDependentResources**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L117-L134) deklariert das Beispiel drei rechteckige Bereiche, die bestimmten Bereichen des Overlays entsprechen.



Unter Berücksichtigung dieser Bereiche wollen wir nun eine der zustandsspezifischen Methoden (**GameInfoOverlay::SetGameStats**) näher untersuchen und sehen, wie das Overlay gezeichnet wird.

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

Mit dem Direct2D-Gerätekontext, den das **GameInfoOverlay** -Objekt initialisiert, füllt diese Methode die Titel- und Rechtecke mit Schwarz mithilfe des Hintergrundpinsels. Sie zeichnet mit dem weißen Textpinsel den Text für die Zeichenfolge „High Score“ im Titelrechteck und eine Zeichenfolge mit den aktualisierten Spielzuständen im Textkörperrechteck.


Das aktionsrechteck wird durch einen nachfolgenden Aufruf von [**gameinfooverlay:: Setaction**](https://github.com/Microsoft/Windows-universal-samples/blob/5f0d0912214afc1c2a7c7470203933ddb46f7c89/Samples/Simple3DGameDX/cpp/GameInfoOverlay.cpp#L522-L564) von einer Methode für das **GameMain** -Objekt, das die erforderlichen **gameinfooverlay:: Setaction** um zu bestimmen, die passende Meldung für Informationen zum Spielzustand bereitstellt aktualisiert die Players, z. B. "Tap to continue".

Das Overlay für einen bestimmten Zustand wird ausgewählt, in der [**GameMain::SetGameInfoOverlay**](https://github.com/Microsoft/Windows-universal-samples/blob/6370138b150ca8a34ff86de376ab6408c5587f5d/Samples/Simple3DGameXaml/cpp/GameMain.cpp#L606-L661) -Methode wie folgt aus:

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

Das Spiel verfügt jetzt über eine Möglichkeit für den Spieler basierend auf dem Spielzustand Textinformationen, und wir haben eine Möglichkeit, wechseln, was Ihnen während des Spiels angezeigt wird.

### <a name="next-steps"></a>Nächste Schritte

Im nächsten Thema zum [Hinzufügen von Steuerungen](tutorial--adding-controls.md) untersuchen wir, wie der Spieler mit dem Beispielspiel interagiert und wie sich der Spielzustand durch Eingaben ändert.



 




