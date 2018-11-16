---
author: TylerMSFT
title: Hinzufügen eines Begrüßungsbildschirms
description: Legen Sie das Bild für den Begrüßungsbildschirm und die Hintergrundfarbe Ihrer App mithilfe von Microsoft Visual Studio fest.
ms.assetid: 41F53046-8AB7-4782-9E90-964D744B7D66
ms.author: twhitney
ms.date: 05/08/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 143b96171091406fb91954685143e4f86c036ffb
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6972893"
---
# <a name="add-a-splash-screen"></a>Hinzufügen eines Begrüßungsbildschirms

Legen Sie das Bild für den Begrüßungsbildschirm und die Hintergrundfarbe Ihrer App mithilfe von Microsoft Visual Studio fest.

## <a name="set-the-splash-screen-image-and-background-color-in-visual-studio"></a>Festlegen von Begrüßungsbildschirm und Hintergrundfarbe einer App mithilfe von Visual Studio

Wenn Sie eine Visual Studio-Vorlage zum Erstellen der App verwenden, wird dem Projekt ein Standardbild hinzugefügt und als Bild für den Begrüßungsbildschirm festgelegt. Als Hintergrundfarbe für den Begrüßungsbildschirm wird standardmäßig Hellgrau verwendet. Führen Sie die folgenden Schritte aus, wenn Sie das Standardbild oder die Farbe des App-Begrüßungsbildschirms ändern möchten:

1. Öffnen Sie das vorhandene App-Projekt für die Universelle Windows-Plattform (UWP) in Visual Studio.
2. Öffnen Sie im **Projektmappen-Explorer** die Datei „Package.appxmanifest“. Sie können diese Datei auch über die Menüleiste öffnen, indem Sie **Projekt** &gt; **Store** &gt; **App-Manifest bearbeiten** auswählen.
3. Öffnen Sie die Registerkarte **Visuelle Anlagen**, und wählen Sie links im Fenster „Package.appxmanifest“ unter **Alle Bildanlagen** die Option **Begrüßungsbildschirm**. Falls Sie den Begrüßungsbildschirm zum ersten Mal ändern, wird im Feld **Begrüßungsbildschirm** der Pfad „Assets\\SplashScreen.png“ angezeigt.

    Im folgenden Screenshot ist das Fenster „Package.appxmanifest“ in Visual Studio dargestellt. Je nach Art des Projekts werden leicht unterschiedliche Sätze von visuellen Ressourcen angezeigt.

    ![Screenshot des Fensters „Package.appxmanifest“ in Visual Studio 2017](images/appmanifest.png)

    Wenn Sie „Package.appxmanifest“ in einem Text-Editor öffnen, wird das [**SplashScreen**](https://msdn.microsoft.com/library/windows/apps/br211467)-Element als untergeordnetes Element des [**VisualElements**](https://msdn.microsoft.com/library/windows/apps/br211471)-Elements angezeigt. Das standardmäßige Begrüßungsbildschirm-Markup in der Manifestdatei sieht in einem Text-Editor wie folgt aus:

    ```xml
    <uap:SplashScreen Image="Assets\SplashScreen.png" />
    ```

4. Drücken Sie zum Auswählen eines neuen Begrüßungsbildschirm-Bilds für eine UWP-App die Schaltfläche mit den Auslassungspunkten, die neben der Bezeichnung **1240 x 600 px** unterhalb von **Skalierte Anlagen** angezeigt wird. Wählen Sie das Bild mit 1240 x 600 Pixeln (PNG, JPG oder JPEG) aus, das Sie für den Begrüßungsbildschirm verwenden möchten.

    **Wichtige**Auswahl Bild für den Begrüßungsbildschirm muss 620 x 300 Pixel, die mit einem 1 x Skalierungsfaktor sein. Beachten Sie beim Entwerfen des Begrüßungsbildschirms zudem, dass er kleiner als der Bildschirm und zentriert angezeigt wird. Im Gegensatz zum Begrüßungsbildschirm einer Windows Phone Store-App füllt er den Bildschirm nicht komplett aus.

5. Drücken Sie zum Auswählen eines neuen Bilds für eine Windows Phone Store-App die Schaltfläche mit den Auslassungszeichen, die neben der Bezeichnung **1152 x 1920 px** unterhalb von **Skalierte Anlagen** angezeigt wird. Wählen Sie das Bild mit 1152 x 1920 Pixeln (.png, .jpg oder .jpeg) aus, das Sie für den Begrüßungsbildschirm verwenden möchten.

    **Wichtige**Auswahl Bild für den Begrüßungsbildschirm muss 1152 x 1920 Pixel werden die ist die richtige Größe für einen Skalierungsfaktor von 2,4. Ist dies die einzige Ressource, die Sie bereitstellen, wird es auf die Skalierungsfaktoren 1.4x und 1x nach unten skaliert.

6. Legen Sie im Abschnitt **Begrüßungsbildschirm** im Feld **Hintergrundfarbe** die Hintergrundfarbe fest, die zusammen mit Ihrem Bild angezeigt werden soll. Sie können entweder einen Farbnamen oder „\#“ und den Hexadezimalwert einer Farbe eingeben. Eine Liste mit den Namen der verfügbaren Farben finden Sie unter [**SplashScreen-Element**](https://msdn.microsoft.com/library/windows/apps/br211467). Das Festlegen einer Hintergrundfarbe für Ihren Begrüßungsbildschirm ist nicht unbedingt erforderlich. Wenn Sie keine Farbe für eine UWP-App (Universelle Windows-Plattform) angeben, wird als Hintergrundfarbe für den Begrüßungsbildschirm standardmäßig Hellgrau (Hexadezimalwert \#464646) verwendet. Dies ist die gleiche Farbe wie die standardmäßige Hintergrundfarbe für eine **Kachel** (siehe Feld **Hintergrundfarbe** im Abschnitt **Bilder für Kacheln und Logos** auf der Registerkarte **Visuelle Anlagen**). Wenn Sie keine Farbe für ein Windows Phone angeben oder „transparent“ festlegen, wird die Hintergrundfarbe des Begrüßungsbildschirms transparent sein.

## <a name="summary-and-next-steps"></a>Zusammenfassung und nächste Schritte

Falls das Laden der App einige Zeit dauert, können Sie erwägen, einen erweiterten Begrüßungsbildschirm hinzuzufügen. Eine Schritt-für-Schritt-Anleitung finden Sie unter [Erstellen eines benutzerdefinierten Begrüßungsbildschirms](create-a-customized-splash-screen.md).

## <a name="related-topics"></a>Verwandte Themen

* [Erstellen eines benutzerdefinierten Begrüßungsbildschirms](create-a-customized-splash-screen.md)
* [Schemareferenz zum Paketmanifest: SplashScreen-Element](https://msdn.microsoft.com/library/windows/apps/br211467)
* [Windows.ApplicationModel.Activation.SplashScreen-Klasse](https://msdn.microsoft.com/library/windows/apps/br224763)