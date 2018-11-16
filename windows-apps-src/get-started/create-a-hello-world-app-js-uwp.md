---
author: GrantMeStrength
ms.assetid: 3a17e682-40be-41b4-8bd3-fbf0b15259d6
title: Erstellen der App Hello, world (JS)
description: In diesem Lernprogramm erfahren Sie, wie Sie JavaScript und HTML zum Erstellen einer einfachen & \#0034; Hello, World & \#0034; App, die die universelle Windows-Plattform (UWP) auf Windows 10 ausgerichtet ist.
ms.author: jken
ms.date: 03/06/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 4d8fb1dc486c039007c3ea0d4ee36d72c0c511f9
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "6975740"
---
# <a name="create-a-hello-world-app-js"></a>Erstellen der App Hello, world (JS)

In diesem Lernprogramm erfahren Sie, wie Sie JavaScript und HTML zum Erstellen einer einfachen "Hello, World"-App für die universelle Windows-Plattform (UWP) auf Windows 10 verwenden. Mit einem einzigen Projekt in Microsoft Visual Studio können Sie eine app erstellen, die auf jedem Windows 10-Gerät ausgeführt wird.

> [!NOTE]
> In diesem Lernprogramm wird Visual Studio Community 2017 verwendet. Wenn Sie eine andere Version von Visual Studio verwenden, kann das Programm für Sie etwas anders aussehen.


Hier erfahren Sie Folgendes:

-   Erstellen Sie ein neues **Visual Studio 2017** -Projekt, das auf **Windows 10** und die **UWP**abzielt.
-   Fügen Sie HTML und JavaScript-Inhalt hinzu
-   Führen Sie das Projekt auf dem lokalen Desktop in Visual Studio aus

## <a name="before-you-start"></a>Vorbereitung

-   [Was ist eine UWP-App?](universal-application-platform-guide.md).
-   Zum Durcharbeiten dieses Lernprogramms benötigen Sie Windows 10 und Visual Studio2017. [Vorbereiten](get-set-up.md).
-   Außerdem wird davon ausgegangen, dass Sie das Standardfensterlayout in Visual Studio verwenden. Wenn Sie das Standardlayout ändern, können Sie es im Menü **Fenster** mit dem Befehl **Fensterlayout zurücksetzen** wiederherstellen.

## <a name="step-1-create-a-new-project-in-visual-studio"></a>Schritt 1: Erstellen eines neuen Projekts in Visual Studio

1.  Starten Sie Visual Studio 2017.

2.  Wählen Sie im Menü **Datei** die Befehle **Neu > Projekt...** aus, um das Dialogfeld *Neues Projekt* anzuzeigen.

3.  Öffnen Sie in der Liste der Vorlagen auf der linken Seite **Installiert > Vorlagen > JavaScript**, und wählen Sie dann **Windows Universal** aus, um eine Liste der UWP-Projektvorlagen anzuzeigen.

    (Wenn keine universellen Vorlagen angezeigt werden, fehlen möglicherweise die Komponenten zum Erstellen von UWP-Apps. Sie können die Installation wiederholen und UWP-Unterstützung hinzufügen, indem Sie im Dialogfeld *Neues Projekt* auf **Visual Studio-Installer öffnen** klicken. Siehe [Vorbereiten](get-set-up.md)

4.  Wählen Sie die Vorlage **Leere App (universelle Windows-App)** aus, und geben Sie „HelloWorld“ als **Name** ein. Wählen Sie **OK** aus.

    ![Das Fenster für ein neues Projekt](images/win10-js-01.png)

> [!NOTE]
> Wenn Sie Visual Studio zum ersten Mal verwenden, wird möglicherweise das Dialogfeld „Einstellungen“ angezeigt, in dem Sie aufgefordert werden, **Entwicklermodus** zu aktivieren. Der Entwicklermodus ist eine spezielle Einstellung, die bestimmte Features ermöglicht, z.B. die Berechtigung zum Ausführen von Apps, direkt und nicht nur aus dem Store. Weitere Informationen finden Sie in [Aktivieren Ihres Geräts für die Entwicklung](enable-your-device-for-development.md). Wählen Sie **Entwicklermodus** aus, klicken Sie auf **Ja**, und schließen Sie das Dialogfeld, um mit dem Lernprogramm fortzufahren.

 ![Aktivieren des Dialogfelds für Entwicklermodus](images/win10-cs-00.png)

5.  Das Dialogfeld für die Zielversion/mindestens erforderliche Version wird angezeigt. Die Standardeinstellungen sind für dieses Lernprogramm in Ordnung, wählen Sie daher **OK** aus, um das Projekt zu erstellen.

    ![Das Fenster „Projektmappen-Explorer“](images/win10-cs-02.png)

6.  Wenn das neue Projekt geöffnet wird, werden die Dateien im Bereich **Projektmappen-Explorer** auf der rechten Seite angezeigt. Möglicherweise müssen Sie die Registerkarte **Projektmappen-Explorer** anstelle der Registerkarte **Eigenschaften** auswählen, um die Dateien anzuzeigen.

    ![Das Fenster „Projektmappen-Explorer“](images/win10-js-02.png)

**Leere App (universelle Windows-App)** ist zwar nur eine Minimalvorlage, umfasst aber trotzdem eine Reihe von Dateien. Diese Dateien werden für alle UWP-Apps mit JavaScript benötigt. Sie sind Teil jedes Projekts, das Sie mit Visual Studio erstellen.


### <a name="whats-in-the-files"></a>Inhalt der Dateien

Doppelklicken Sie zum Anzeigen und Bearbeiten einer Datei im Projekt im **Projektmappen-Explorer** auf die gewünschte Datei. 

*default.css*

-  Der von der App verwendete Standard-Stylesheet.

*main.js*

- Die JavaScript-Datei „default.js“ Auf sie wird in der Datei index.html verwiesen.

*index.html*

- Die Website der App, die beim Start der App geladen und angezeigt wird.

*Ein Satz mit Logobildern*
-   „Assets/Square150x150Logo.scale-200.png“ stellt Ihre App im Startmenü dar.
-   „Assets/StoreLogo.png“ stellt Ihre App im Microsoft Store dar.
-   „Assets/SplashScreen.scale-200.png“ ist der Begrüßungsbildschirm, der beim Start der App angezeigt wird.

## <a name="step-2-adding-a-button"></a>Schritt 2: Hinzufügen von Schaltflächen

Klicken Sie auf *index.html*, um die Datei im Editor auszuwählen, und ändern Sie den darin enthaltenen HTML-Code wie folgt:

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8" />
    <title>Hello World</title>
    <script src="js/main.js"></script>
    <link href="css/default.css" rel="stylesheet" />
</head>

<body>
    <p>Click the button..</p>
    <button id="button">Hello world!</button>
</body>

</html>
```

Er sollte wie folgt aussehen:

 ![HTML-Code des Projekts](images/win10-js-03.png)

Dieser HTML-Code verweist auf die Datei *main.js*, die das JavaScript enthält, und fügt dann dem Hauptteil der Webseite eine einzelne Textzeile und eine Schaltfläche hinzu. Die Schaltfläche erhält eine *ID*, damit JavaScript darauf verweisen kann.


## <a name="step-3-adding-some-javascript"></a>Schritt3: Hinzufügen von JavaScript

Jetzt fügen wir JavaScript hinzu. Klicken Sie auf die Datei *main.js*, um sie auszuwählen, und fügen Sie Folgendes hinzu:

```javascript
// Your code here!

window.onload = function () {
    document.getElementById("button").onclick = function (evt) {
        sayHello()
    }
}


function sayHello() {
    var messageDialog = new Windows.UI.Popups.MessageDialog("Hello, world!", "Alert");
    messageDialog.showAsync();
}

```

Es sollte wie folgt aussehen:

 ![JavaScript-Code des Projekts](images/win10-js-04.png)

In diesem JavaScript werden zwei Funktionen deklariert. Die Funktion *window.onload* wird automatisch aufgerufen, wenn *index.html* angezeigt wird. Die Schaltfläche wird (anhand der angegebenen ID) ermittelt, und es wird ein Onclick-Handler hinzugefügt. Dies ist die Methode, die aufgerufen wird, wenn auf die Schaltfläche geklickt wird.

Die zweite Funktion, *sayHello()*, erstellt ein Dialogfeld und zeigt es an. Diese Funktion ist der Funktion *Alert()*, die Sie möglicherweise aus vorheriger JavaScript-Entwicklung kennen, sehr ähnlich.


## <a name="step-4-run-the-app"></a>Schritt4: Ausführen der App

Jetzt können Sie die App ausführen, indem Sie F5 drücken. Die App wird geladen, und die Webseite wird angezeigt. Klicken Sie auf die Schaltfläche, und das Meldungsdialogfeld wird angezeigt.

 ![Ausführen des Projekts](images/win10-js-05.png)



## <a name="summary"></a>Zusammenfassung


Herzlichen Glückwunsch, Sie haben eine JavaScript-app für Windows 10 und die UWP erstellt! Dies ist ein sehr einfaches Beispiel, aber nun können Sie Ihre bevorzugten JavaScript-Bibliotheken und -Frameworks zum Erstellen Ihrer eigenen App hinzufügen. Und da es sich um eine UWP-App handelt, können Sie sie im Store veröffentlichen. Beispiele zum Hinzufügen von Drittanbieter-Frameworks finden Sie in diesen Projekten:

* [Ein einfaches 2D-UWP-Spiel für den Microsoft Store, geschrieben in JavaScript und CreateJS](get-started-tutorial-game-js2d.md)
* [Ein 3D-UWP-Spiel für den Microsoft Store, geschrieben in JavaScript und ThreeJS](get-started-tutorial-game-js3d.md)


