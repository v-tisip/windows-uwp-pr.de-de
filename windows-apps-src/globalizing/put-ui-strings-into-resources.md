---
author: DelfCo
Description: "Nehmen Sie Zeichenfolgenressourcen für Ihre Benutzeroberfläche in Ressourcendateien auf. Sie können anschließend im Code oder Markup auf diese Zeichenfolgen verweisen."
title: Aufnehmen von UI-Zeichenfolgen in Ressourcen
ms.assetid: E420B9BB-C0F6-4EC0-BA3A-BA2875B69722
label: Put UI strings into resources
template: detail.hbs
ms.author: bobdel
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 9f4ebe843b30d5bc408a705cfc9dda5d6731d4d1
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="put-ui-strings-into-resources"></a>Aufnehmen von UI-Zeichenfolgen in Ressourcen
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

Nehmen Sie Zeichenfolgenressourcen für Ihre Benutzeroberfläche in Ressourcendateien auf. Sie können anschließend im Code oder Markup auf diese Zeichenfolgen verweisen.

<div class="important-apis" >
<b>Wichtige APIs</b><br/>
<ul>
<li>[**ApplicationModel.Resources.ResourceLoader**](https://msdn.microsoft.com/library/windows/apps/br206014)</li>
<li>[**WinJS.Resources.processAll**](https://msdn.microsoft.com/library/windows/apps/br211864)</li>
</ul>
</div>


In diesem Thema wird gezeigt, welche Schritte Sie ausführen müssen, um Ihrer universellen Windows-App Zeichenfolgenressourcen für mehrere Sprachen hinzuzufügen und die App kurz zu testen.

## <a name="put-strings-into-resource-files-instead-of-putting-them-directly-in-code-or-markup"></a>Platzieren Sie Zeichenfolgen in Ressourcendateien und nicht direkt im Code oder Markup.


1.  Öffnen Sie Ihre Projektmappe in Visual Studio (oder erstellen Sie eine neue).

2.  Öffnen Sie in Visual Studio „package.appxmanifest“, rufen Sie die Registerkarte **Anwendung** auf, und legen Sie (in diesem Beispiel) die Standardsprache auf „en-US“ fest. Wenn Ihre Projektmappe mehrere Dateien namens „package.appxmanifest“ enthält, führen Sie die Schritte für jede Datei aus.
    <br>**Hinweis**  Damit haben Sie die Standardsprache für das Projekt festgelegt. Die Standardsprachressourcen werden verwendet, wenn die bevorzugte Sprache des Benutzers oder die Anzeigesprachen nicht mit den von der Anwendung bereitgestellten Sprachressourcen übereinstimmen.
3.  Erstellen Sie einen Ordner, um dort die Ressourcendateien zu speichern.
    1.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt (das freigegebene Projekt, falls die Projektmappe mehrere Projekte enthält), und wählen Sie **Hinzufügen** &gt; **Neuer Ordner** aus.
    2.  Geben Sie dem neuen Ordner den Namen „Strings“.
    3.  Wenn der neue Ordner nicht im Projektmappen-Explorer sichtbar ist, wählen Sie im Microsoft Visual Studio-Menü **Projekt** &gt; **Alle Dateien anzeigen** aus, während das Projekt noch ausgewählt ist.

4.  Erstellen Sie einen Unterordner und eine Ressourcendatei für Englisch (USA).
    1.  Klicken Sie mit der rechten Maustaste auf den Ordner „Strings“, und fügen Sie darunter einen neuen Ordner hinzu. Geben Sie ihm den Namen „en-US“. Die Ressourcendatei muss in einem Ordner mit dem Sprachtag [BCP-47](http://go.microsoft.com/fwlink/p/?linkid=227302) abgelegt werden. Details zum Sprachqualifizierer und eine Liste häufiger Sprachtags finden Sie unter [Benennen von Ressourcen mit Qualifizierern](https://msdn.microsoft.com/library/windows/apps/xaml/hh965324).
    2.  Klicken Sie mit der rechten Maustaste auf den Ordner „en-US“, und wählen Sie **Hinzufügen** &gt; **Neues Element...** aus.
    3.  Wählen Sie „Ressourcendatei (.resw)“ aus.

    4.  Klicken Sie auf **Hinzufügen**. Hierdurch wird eine Ressourcendatei mit dem Standardnamen „Resources.resw“ hinzugefügt. Es wird empfohlen, diesen Standarddateinamen zu verwenden. Apps können ihre Ressourcen in andere Dateien partitionieren. Sie müssen jedoch darauf achten, richtig auf die Dateien zu verweisen (siehe [Laden von Zeichenfolgenressourcen](https://msdn.microsoft.com/library/windows/apps/xaml/hh965323)).
    5.  Wenn Sie ausschließlich RESX-Dateien mit Zeichenfolgenressourcen aus vorherigen .NET-Projekten verwenden, wählen Sie **Hinzufügen** &gt; **Vorhandenes Element** aus, fügen die RESX-Datei hinzu und benennen sie in .resw um.
    6.  Öffnen Sie die Datei, und fügen Sie im Editor die folgenden Ressourcen hinzu:


        Strings/en-US/Resources.resw ![Ressource hinzufügen, Englisch](images/addresource-en-us.png) In diesem Beispiel identifizieren „Greeting.Text“ und „Farewell“ die Zeichenfolgen, die angezeigt werden sollen. „Greeting.Width“ identifiziert die „Width“-Eigenschaft der „Greeting“-Zeichenfolge. Kommentare sind gut geeignet, um spezielle Anweisungen für Übersetzer bereitzustellen, die die Zeichenfolgen in andere Sprachen lokalisieren.

## <a name="associate-controls-to-resources"></a>Ordnen Sie Steuerelemente zu Ressourcen zu.

Sie müssen alle Steuerelemente, deren Texte lokalisiert werden müssen, mit der RESW-Datei verknüpfen. Verwenden Sie dazu das **x:Uid**-Attribut in den XAML-Elementen wie folgt:

```XML
<TextBlock x:Uid="Greeting" Text="" />
```

Für den Ressourcennamen geben Sie den **Uid**-Attributwert und die Eigenschaft an, die die übersetzte Zeichenfolge erhält (in diesem Fall die Eigenschaft „Text“). Sie können andere Eigenschaften/Werte für verschiedene Sprachen festlegen, z.B. "Greeting.Width". Sie sollten mit solchen layoutbezogenen Eigenschaften jedoch vorsichtig umgehen. Versuchen Sie stets, ein dynamisches Layout auf Grundlage des Gerätebildschirms für die Steuerelemente zu verwenden.

Beachten Sie weiterhin, dass die verknüpften Eigenschaften unterschiedlich in RESW-Dateien behandelt werden, z.B. "AutomationPeer.Name". Sie müssen den Namespace explizit wie folgt ausschreiben:

```XML
MediumButton.[using:Windows.UI.Xaml.Automation]AutomationProperties.Name</code></pre></td>
```

## <a name="add-string-resource-identifiers-to-code-and-markup"></a>Fügen Sie Code und Markup Zeichenfolgenressourcen-Bezeichner hinzu.

Sie können im Code dynamisch auf Zeichenfolgen verweisen:

**C#**
```CSharp
var loader = new Windows.ApplicationModel.Resources.ResourceLoader();
var str = loader.GetString("Farewell");
```

**C++**
```cpp
auto loader = ref new Windows::ApplicationModel::Resources::ResourceLoader();
auto str = loader->GetString("Farewell");
```


## <a name="add-folders-and-resource-files-for-two-additional-languages"></a>Fügen Sie Ordner und Ressourcendateien für zwei zusätzliche Sprachen hinzu.


1.  Fügen Sie unter dem Ordner „Strings“ einen weiteren Ordner für Deutsch hinzu. Geben Sie dem Ordner den Namen „de-DE“ für Deutsch (Deutschland).
2.  Erstellen Sie eine weitere Ressourcendatei im Ordner „de-DE“, und fügen Sie Folgendes hinzu:

    strings/de-DE/Resources.resw

    ![Ressource hinzufügen, Deutsch](images/addresource-de-de.png)


3.  Erstellen Sie einen weiteren Ordner mit dem Namen „fr-FR“ für Französisch (Frankreich). Erstellen Sie eine neue Ressourcendatei, und fügen Sie Folgendes hinzu:

    strings/fr-FR/Resources.resw ![Ressource hinzufügen, Französisch,](images/addresource-fr-fr.png)

## <a name="build-and-run-the-app"></a>Erstellen Sie die App, und führen Sie sie aus.


Testen Sie die App hinsichtlich der Standardanzeigesprache.

1.  Drücken Sie F5, um die App zu erstellen und auszuführen.
2.  Wie Sie sehen, werden Begrüßung und Verabschiedung in der bevorzugten Sprache des Benutzers angezeigt.
3.  Beenden Sie die App.

Testen Sie die App für die anderen Sprachen.

1.  Rufen Sie **Einstellungen** auf Ihrem Gerät auf.
2.  Wählen Sie **Zeit & Sprache** aus.
3.  Wählen Sie **Region & Sprache** (oder auf einem Telefon oder im Phone-Emulator) **Sprache**) aus.
4.  Wie Sie sehen, wird die Sprache, die beim Ausführen der App angezeigt wurde, als erste Sprache aufgeführt, also Englisch, Deutsch oder Französisch. Wenn die zuerst aufgeführte Sprache keine der drei genannten Sprachen ist, greift die App auf die erste Sprache in der Liste zurück, die von der App unterstützt wird.
5.  Wenn nicht alle drei Sprachen auf Ihrem Computer verfügbar sind, fügen Sie die fehlenden Sprache hinzu, indem Sie auf **Sprache hinzufügen** klicken und die Sprachen dann zur Liste hinzufügen.
6.  Um die App mit einer anderen Sprache zu testen, wählen Sie die Sprache in der Liste aus, und klicken Sie auf **Als Standard**. (Auf einem Telefon oder im Phone-Emulator wählen Sie die Sprache mit Tippen und Halten aus der Liste aus und tippen dann auf **Nach oben**, bis sie am Anfang der Liste steht.) Führen Sie die App anschließend aus.

## <a name="related-topics"></a>Verwandte Themen


* [Benennen von Ressourcen mithilfe von Qualifizierern](https://msdn.microsoft.com/library/windows/apps/xaml/hh965324)
* [Laden von Zeichenfolgenressourcen](https://msdn.microsoft.com/library/windows/apps/xaml/hh965323)
* [Das BCP-47-Sprachtag](http://go.microsoft.com/fwlink/p/?linkid=227302)
 

 



