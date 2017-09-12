---
author: mijacobs
Description: "Dialogfelder und Flyouts zeigen vorübergehende UI-Elemente an, die angezeigt werden, wenn der Benutzer sie anfordert oder eine Aktion erfolgt, die eine Benachrichtigung oder Genehmigung erfordert."
title: Dialogfelder und Flyouts
label: Dialogs
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows 10, uwp
ms.assetid: ad6affd9-a3c0-481f-a237-9a1ecd561be8
pm-contact: yulikl
design-contact: kimsea
dev-contact: niallm
doc-status: Published
ms.openlocfilehash: a1e7ecd60c960459d8d146bbda0fa6fba4bfc7f6
ms.sourcegitcommit: 10d6736a0827fe813c3c6e8d26d67b20ff110f6c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2017
---
# <a name="dialogs-and-flyouts"></a>Dialogfelder und Flyouts

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

Dialogfelder und Flyouts sind vorübergehende UI-Elemente, die angezeigt werden, wenn Ereignisse Benachrichtigungen, Genehmigungen oder zusätzliche Informationen vom Benutzer erfordern.

> **Wichtige APIs**: [ContentDialog-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.contentdialog.aspx), [Flyout-Klasse](https://msdn.microsoft.com/library/windows/apps/dn279496)

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
   <p><b>Dialogfelder</b> <br/><br/>
    ![Beispiel für ein Dialogfeld](images/dialogs/dialog_RS2_delete_file.png)</p>
<p>Dialogfelder sind modale Benutzeroberflächenüberlagerungen, die kontextbezogene App-Informationen enthalten. Dialogfelder blockieren Interaktionen mit dem App-Fenster, bis sie explizit geschlossen werden. Sie verlangen häufig eine Aktion vom Benutzer.   
</p><br/>

  </div>
  <div class="side-by-side-content-right">
   <p><b>Flyouts</b> <br/><br/>
   ![Flyout-Beispiel](images/flyout-example2.png)</p>
<p>Ein Flyout ist ein einfaches, kontextbezogenes Popupmenü, das die UI entsprechend den Aktionen des Benutzers anzeigt. Es umfasst die Platzierungs- und Größenlogik und kann dazu verwendet werden, ein sekundäres Steuerelement oder weitere Einzelheiten zu einem Element anzuzeigen.
</p><p>Im Gegensatz zu einem Dialogfeld kann ein Flyout durch Tippen oder Klicken auf eine Stelle außerhalb des Flyouts schnell geschlossen werden. Das Drücken der ESC- oder Zurück-Taste sowie das Ändern der Größe des App-Fensters oder der Ausrichtung des Geräts haben denselben Effekt.
</p><br/>

  </div>
</div>
</div>

## <a name="is-this-the-right-control"></a>Ist dies das richtige Steuerelement?

* Verwenden Sie Dialogfelder und Flyouts, um Benutzern wichtige Informationen mitzuteilen oder deren Bestätigung bzw. zusätzliche Informationen anzufordern, bevor eine Aktion abgeschlossen werden kann.
* Verwenden Sie Flyouts nicht anstelle von [QuickInfos](tooltips.md) oder [Kontextmenüs](menus.md). Verwenden Sie QuickInfos, um kurze Beschreibungen anzuzeigen, die nach einer festgelegten Zeit ausgeblendet werden. Verwenden Sie ein Kontextmenü für kontextbezogene Aktionen im Zusammenhang mit UI-Elementen (beispielsweise Kopieren und Einfügen).  


Dialogfelder und Flyouts stellen sicher, dass den Benutzern wichtige Informationen bekannt sind, stellen jedoch auch eine Unterbrechung dar. Da Dialogfelder modal (blockierend) sind, werden die Benutzer unterbrochen und daran gehindert, andere Schritte durchzuführen, bis eine Interaktion mit dem Dialogfeld erfolgt ist. Flyouts sind weniger störend. Zu viele Flyouts können jedoch als störend empfunden werden.

Berücksichtigen Sie die Bedeutung der zu vermittelnden Informationen: Sind sie wichtig genug, um den Benutzer zu unterbrechen? Berücksichtigen Sie zudem, wie häufig die Informationen angezeigt werden müssen. Wenn ein Dialogfeld oder eine Benachrichtigung alle paar Minuten angezeigt wird, sollten Sie diese Informationen stattdessen in die primäre UI einbinden. So können Sie z.B. in einem Chat-Client anstatt eines Flyouts, der jedes Mal angezeigt wird, wenn sich ein Freund anmeldet, eine Liste der Freunde anzeigen, die derzeit online sind, und diejenigen Freunde hervorheben, die sich gerade anmelden.

Dialogfelder werden häufig zum Bestätigen einer Aktion vor deren Ausführung verwendet (z.B. vor dem Löschen einer Datei). Wenn Sie davon ausgehen, dass die Benutzer häufig eine bestimmte Aktion ausführen, sollten Sie eine Möglichkeit bereitstellen, versehentliche Aktionen rückgängig zu machen, anstatt jedes Mal die Bestätigung der Aktion zu erzwingen.

## <a name="dialogs-vs-flyouts"></a>Dialogfelder im Vergleich zu Flyouts

Wenn ein Dialogfeld oder Flyout eingesetzt werden soll, müssen Sie sich für eine der beiden Optionen entscheiden.

Angesichts der Tatsache, dass Dialogfelder im Gegensatz zu Flyouts Interaktionen blockieren, sollten Dialogfelder auf Situationen beschränkt bleiben, in denen der Benutzer unterbrochen werden soll, um sich auf eine bestimmte Information oder die Beantwortung einer Frage zu konzentrieren. Flyouts hingegen können verwendet werden, wenn Sie auf etwas aufmerksam machen möchten, das der Benutzer jedoch ignorieren kann.

<div class="side-by-side">
<div class="side-by-side-content">
  <div class="side-by-side-content-left">
   <p><b>Fälle, in denen ein Dialogfeld verwendet werden sollte:</b> <br/>
<ul>
<li>Für wichtige Informationen, die der Benutzer vor dem Fortsetzen lesen und bestätigen **muss**. Beispiele:
<ul>
  <li>Die Sicherheit des Benutzers ist möglicherweise gefährdet.</li>
  <li>Der Benutzer möchte eine wertvolle Ressource endgültig ändern.</li>
  <li>Der Benutzer möchte eine wertvolle Ressource löschen.</li>
  <li>Bestätigen eines In-App-Einkaufs</li>
</ul>

</li>
<li>Fehlermeldungen, die sich auf den Gesamtkontext der App beziehen, z. B. Verbindungsfehler.</li>
<li>Fragen, wenn dem Benutzer eine blockierende Frage gestellt werden muss, z. B. wenn die App nicht im Auftrag des Benutzers eine Auswahl treffen kann. Eine blockierende Frage kann nicht ignoriert oder verschoben werden und sollte dem Benutzer klar definierte Auswahlmöglichkeiten bieten.</li>
</ul>
</p>
  </div>
  <div class="side-by-side-content-right">
   <p><b>Fälle, in denen ein Flyout verwendet werden sollte:</b> <br/>
<ul>
<li>Erfassen zusätzlicher Informationen, die erforderlich sind, bevor eine Aktion abgeschlossen werden kann.</li>
<li>Anzeigen von Informationen, die nur vorübergehend relevant sind. So können Sie z.B. in einer Fotogalerie-App ein Flyout einsetzen, damit eine große Version des Bilds angezeigt wird, wenn der Benutzer auf eine Miniaturansicht klickt.</li>
<li>Anzeigen weiterer Informationen, z. B. von Details oder ausführlicheren Beschreibungen eines Elements auf der Seite.</li>
</ul></p>
  </div>
</div>
</div>

## <a name="dialogs"></a>Dialogfelder
### <a name="general-guidelines"></a>Allgemeine Richtlinien

-   Sie sollten das Problem oder das Ziel des Benutzers in der ersten Zeile des Dialogfeldtexts deutlich benennen.
-   Der Dialogfeldtitel ist die Hauptanweisung und optional.
    -   Verwenden Sie einen kurzen Titel, um dem Benutzer die erforderlichen Aktionen im Dialogfeld zu erklären.
    -   Wenn Sie mit dem Dialogfeld eine einfache Meldung, einen Fehler oder eine Frage anzeigen möchten, können Sie den Titel optional auslassen. Vermitteln Sie dann im Inhalt die wichtigsten Informationen.
    -   Stellen Sie sicher, dass sich der Titel direkt auf die Auswahlmöglichkeiten der Schaltflächen bezieht.
-   Der Inhalt des Dialogfelds enthält den beschreibenden Text und ist erforderlich.
    -   Stellen Sie die Meldung, den Fehler oder die blockierende Frage so einfach wie möglich dar.
    -   Stellen Sie bei Verwendung eines Dialogfeldtitels mithilfe des Inhaltsbereichs weitere Details bereit, oder definieren Sie Terminologie. Wiederholen Sie nicht den Titel mit anderen Worten.
-   Mindestens eine Dialogfeldschaltfläche muss angezeigt werden.
    -   Stellen Sie sicher, dass Ihr Dialogfeld mindestens eine Schaltfläche aufweist, die eine sichere, nicht-destruktive Aktion wie „Alles klar!“, „Schließen“ oder „Abbrechen“ auslöst. Verwenden Sie die CloseButton-API, um diese Schaltfläche hinzuzufügen.
    -   Verwenden Sie für den Schaltflächentext konkrete Antworten auf die Hauptanweisung oder den Inhalt. Beispiel: „Möchten Sie AppName den Zugriff auf Ihren Standort erlauben?“, gefolgt von den Schaltflächen „Zulassen“ und „Blockieren“. Konkrete Antworten erleichtern das Verständnis und ermöglichen somit eine schnelle Entscheidungsfindung.
    - Stellen Sie sicher, dass der Text der Aktionsschaltflächen kurz ist. Kurze Anweisungen ermöglichen dem Benutzer, schnell und zuverlässig eine Entscheidung zu treffen.
    - Zusätzlich zur sicheren, nicht-destruktiven Aktion können Sie dem Benutzer optional ein oder zwei Aktionsschaltflächen anzeigen, die im Zusammenhang mit der Hauptanweisung stehen. Diese „bestätigenden“ Aktionsschaltflächen unterstreichen den Hauptgrund des Dialogfelds. Verwenden Sie die PrimaryButton- und SecondaryButton-APIs, um diese „bestätigenden“ Aktionen hinzufügen.
    - Die „bestätigenden“ Aktionsschaltflächen sollten als die am weitesten links stehenden Schaltflächen angezeigt werden. Die sichere, nicht-destruktive Aktion sollte als die am weitesten rechts stehende Schaltfläche angezeigt werden.
    - Sie können optional eine der drei Schaltflächen als Standardschaltfläche des Dialogfelds festlegen. Verwenden Sie die DefaultButton-API, um eine der Schaltflächen abzugrenzen.  
-   Verwenden Sie Dialogfelder nicht für kontextbezogene Fehler, die sich auf eine bestimmte Stelle auf der Seite beziehen, beispielsweise Validierungsfehler (wie in Kennwortfeldern). Verwenden Sie die Canvas der App selbst zum Anzeigen von Inlinefehlern.
- Verwenden Sie die [ContentDialog-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.contentdialog.aspx), um Ihre Dialogfeldumgebung zu erstellen. Verwenden Sie nicht die veraltete MessageDialog-API.

### <a name="dialog-scenarios"></a>Dialogfeld-Szenarien
Da Dialogfelder Benutzerinteraktion blockieren, und Schaltflächen für die Benutzer das primäre Mittel sind, ein Dialogfeld zu schließen, sollten Sie sicherstellen, dass Ihr Dialogfeld mindestens eine „sichere“, nicht-destruktive Schaltfläche wie z.B. „Schließen“ oder „Alles klar!“ enthält. **Alle Dialogfelder sollten mindestens eine sichere Aktionsschaltfläche enthalten, um das Dialogfeld zu schließen.** Dadurch wird sichergestellt, dass der Benutzer das Dialogfeld zuverlässig schließen kann, ohne eine Aktion auszuführen.
![Dialogfeld mit einer Schaltfläche](images/dialogs/dialog_RS2_one_button.png)

```csharp
private async void DisplayNoWifiDialog()
{
    ContentDialog noWifiDialog = new ContentDialog
    {
        Title = "No wifi connection",
        Content = "Check your connection and try again.",
        CloseButtonText = "Ok"
    };

    ContentDialogResult result = await noWifiDialog.ShowAsync();
}
```

Wenn Dialogfelder dazu verwendet werden, eine blockierende Frage anzuzeigen, sollte Ihr Dialogfeld dem Benutzer Aktionsschaltflächen bieten, die im Zusammenhang mit der Frage stehen. Die „sichere“, nicht-destruktive Schaltfläche kann durch ein oder zwei „bestätigende“ Aktionsschaltflächen ergänzt werden. Wenn dem Benutzer mehrere Optionen angezeigt werden, stellen Sie sicher, dass die Schaltflächen für die „bestätigende“ und die sichere/„ablehnende“ Aktion den Bezug zur Frage eindeutig darstellen.

![Dialogfeld mit zwei Schaltflächen](images/dialogs/dialog_RS2_two_button.png)

```csharp
private async void DisplayLocationPromptDialog()
{
    ContentDialog locationPromptDialog = new ContentDialog
    {
        Title = "Allow AppName to access your location?",
        Content = "AppName uses this information to help you find places, connect with friends, and more.",
        CloseButtonText = "Block",
        PrimaryButtonText = "Allow"
    };

    ContentDialogResult result = await locationPromptDialog.ShowAsync();
}
```

Dialogfelder mit drei Schaltflächen werden verwendet, wenn Sie dem Benutzer zwei „bestätigende“ und eine „ablehnende“ Aktion präsentierten möchten. Dialogfelder mit drei Schaltflächen sollten sparsam verwendet werden und eine klare Unterscheidung zwischen der Sekundäraktion und der sicheren/ablehnenden Aktion enthalten.

![Dialogfeld mit drei Schaltflächen](images/dialogs/dialog_RS2_three_button.png)

```csharp
private async void DisplaySubscribeDialog()
{
    ContentDialog subscribeDialog = new ContentDialog
    {
        Title = "Subscribe to App Service?",
        Content = "Listen, watch, and play in high definition for only $9.99/month. Free to try, cancel anytime.",
        CloseButtonText = "Not Now",
        PrimaryButtonText = "Subscribe",
        SecondaryButtonText = "Try it"
    };

    ContentDialogResult result = await subscribeDialog.ShowAsync();
}
```

### <a name="the-three-dialog-buttons"></a>Die drei Schaltflächen des Dialogfelds
Der ContentDialog umfasst drei unterschiedliche Arten von Schaltflächen, die Sie zur Erstellung einer Dialogfeldumgebung verwenden können.

- **CloseButton** – erforderlich – Stellt die sichere, nicht-destruktive Aktion dar, die es dem Benutzer ermöglicht, das Dialogfeld zu schließen. Wird als die am weitesten rechts stehende Schaltfläche angezeigt.
- **PrimaryButton** – optional – Stellt die erste „bestätigende“ Aktion dar. Wird als die am weitesten links stehende Schaltfläche angezeigt.
- **SecondaryButton** – optional – Stellt die zweite „bestätigende“ Aktion dar. Wird als mittlere Schaltfläche angezeigt.

Mithilfe der integrierten Schaltflächen kann das Dialogfeld optisch an andere Dialogfelder angepasst werden sowie die Position der Schaltflächen passend ausgerichtet werden. Stellen Sie sicher, dass die Schaltflächen entsprechend auf Tastaturbefehle reagieren und der Befehlsbereich sichtbar bleibt, auch wenn die Bildschirmtastatur aufgerufen ist.

#### <a name="closebutton"></a>CloseButton
Jedes Dialogfeld sollte eine sichere, nicht-destruktive Aktionsschaltfläche aufweisen, die dem Benutzer das zuverlässige Beenden des Dialogfelds ermöglicht.

Verwenden Sie die ContentDialog.CloseButton-API, um diese Schaltfläche zu erstellen. Dadurch schaffen Sie die jeweils richtige Benutzerumgebung für alle Eingabemöglichkeiten wie z.B. Maus, Tastatur, Fingereingabe und Gamepad. Dies ist nötig, wenn:
<ol>
    <li>Der Benutzer auf CloseButton klickt oder tippt </li>
    <li>Der Benutzer die Zurück-Taste des Systems betätigt </li>
    <li>Der Benutzer auf der Tastatur die ESC-Taste betätigt </li>
    <li>Der Benutzer auf dem Gamepad die B-Taste betätigt </li>
</ol>

Wenn der Benutzer auf eine Dialogfeldschaltfläche klickt, gibt die Methode [ShowAsync](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.contentdialog.showasync.aspx) ein [ContentDialogResult](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.contentdialogresult.aspx) zurück, damit Sie wissen, auf welche Schaltfläche der Benutzer klickt. Klicken auf CloseButton resultiert in ContentDialogResult.None.

#### <a name="primarybutton-and-secondarybutton"></a>PrimaryButton und SecondaryButton
Zusätzlich zu CloseButton können Sie dem Benutzer optional ein oder zwei Aktionsschaltflächen anbieten, die im Zusammenhang mit der Hauptanweisung stehen.
Nutzen Sie PrimaryButton für die erste „bestätigende“ Aktion und SecondaryButton für die zweite „bestätigende“ Aktion. Bei Dialogfeldern mit drei Schaltflächen stellt PrimaryButton in der Regel eine eindeutig „bestätigende“ Aktion dar, während SecondaryButton in der Regel eine neutrale oder sekundäre, „bestätigende“ Aktion darstellt.
Beispielsweise kann eine App den Benutzer dazu auffordern, einen Dienst zu abonnieren. In diesem Fall ist PrimaryButton die eindeutig „bestätigende“ Aktion und enthält den Text „Abonnieren“, während SecondaryButton als neutrale, „bestätigende“ Aktion den Text „Testen“ aufweist. CloseButton ermöglicht dem Benutzer in diesem Fall, die Aktion ohne Interaktion abzubrechen.

Klickt der Benutzer auf PrimaryButton, wird von der Methode [ShowAsync](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.contentdialog.showasync.aspx) ContentDialogResult.Primary zurückgegeben.
Klickt der Benutzer auf die SecondaryButton, wird von der Methode [ShowAsync](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.contentdialog.showasync.aspx) ContentDialogResult.Primary zurückgegeben.

![Dialogfeld mit drei Schaltflächen](images/dialogs/dialog_RS2_three_button.png)

#### <a name="defaultbutton"></a>DefaultButton
Sie können optional eine der drei Schaltflächen als Standardschaltfläche festlegen. Das Festlegen einer Standardschaltfläche hat zur Folge, dass:
- die Schaltfläche optisch als Akzentschaltfläche behandelt wird
- die Schaltfläche automatisch auf die EINGABETASTE reagiert
    - Drückt der Benutzer auf der Tastatur die EINGABETASTE, wird der mit der Standardschaltfläche verknüpfte Click-Handler ausgelöst und das ContentDialogResult gibt den mit der Standardschaltfläche verknüpften Wert zurück
    - Wenn der Benutzer den Tastaturfokus auf ein Steuerelement gelegt hat, das die EINGABETASTE handhabt, reagiert die Standardschaltfläche nicht auf Drücken der EINGABETASTE
- Die Schaltfläche erhält den Fokus automatisch, wenn das Dialogfeld geöffnet wird, es sei denn, der Inhalt des Dialogfelds enthält fokussierbare UI

Verwenden Sie die ContentDialog.DefaultButton-Eigenschaft, um die Standardschaltfläche anzugeben. Standardmäßig wird keine Standardschaltfläche festgelegt.

![Ein Dialogfeld mit drei Schaltflächen mit einer Standardschaltfläche](images/dialogs/dialog_RS2_three_button_default.png)

```csharp
private async void DisplaySubscribeDialog()
{
    ContentDialog subscribeDialog = new ContentDialog
    {
        Title = "Subscribe to App Service?",
        Content = "Listen, watch, and play in high definition for only $9.99/month. Free to try, cancel anytime.",
        CloseButtonText = "Not Now",
        PrimaryButtonText = "Subscribe",
        SecondaryButtonText = "Try it",
        DefaultButton = ContentDialogButton.Primary
    };

    ContentDialogResult result = await subscribeDialog.ShowAsync();
}
```

### <a name="confirmation-dialogs-okcancel"></a>Bestätigungsdialogfelder (OK/Abbrechen)
In einem Bestätigungsdialogfeld können Benutzer bestätigen, dass sie eine Aktion ausführen möchten. Sie können die Aktion bestätigen oder den Vorgang abbrechen.  
Ein typisches Bestätigungsdialogfeld verfügt über zwei Schaltflächen: eine Schaltfläche zur Bestätigung („OK“) und eine Schaltfläche zum Abbrechen.  

<ul>
    <li>
        <p>Die Bestätigungsschaltfläche sollte sich im Allgemeinen auf der linken Seite (die primäre Schaltfläche) und die Abbruchschaltfläche (die sekundäre Schaltfläche) auf der rechten Seite befinden.</p>
         ![Dialogfeld zum Bestätigen/Abbrechen einer Aktion](images/dialogs/dialog_RS2_delete_file.png)

    </li>
    <li>Wie in den allgemeinen Empfehlungen erwähnt, sollten Sie Schaltflächen mit Text verwenden, der konkrete Antworten auf die Hauptanweisung bzw. den Hauptinhalt bietet.
    </li>
</ul>

> Auf einigen Plattformen befindet sich die Bestätigungsschaltfläche auf der rechten anstatt auf der linken Seite. Warum empfehlen wir die Platzierung auf der linken Seite?  Wenn Sie davon ausgehen, dass die meisten Benutzer Rechtshänder sind und ihr Telefon in dieser Hand halten, ist es bequemer, eine Bestätigungsschaltfläche zu drücken, die sich auf der linken Seite befindet, weil sie für den Benutzer wahrscheinlich einfacher mit dem Daumen erreichbar ist. Bei Schaltflächen auf der rechten Bildschirmseite muss der Benutzer seinen Daumen in eine weniger bequeme Position nach innen bewegen.

### <a name="create-a-dialog"></a>Erstellen eines Dialogfelds
Um ein Dialogfeld zu erstellen, verwenden Sie die [ContentDialog-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.contentdialog.aspx). Sie können ein Dialogfeld im Code oder Markup erstellen. Obwohl es in der Regel leichter ist, UI-Elemente in XAML zu definieren, ist es bei einem einfachen Dialogfeld unkomplizierter, Code zu verwenden. In diesem Beispiel wird ein Dialogfeld erstellt, um dem Benutzer mitzuteilen, dass keine WLAN-Verbindung vorhanden ist. Für die Anzeige wird die Methode [ShowAsync](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.contentdialog.showasync.aspx) verwendet.

```csharp
private async void DisplayNoWifiDialog()
{
    ContentDialog noWifiDialog = new ContentDialog
    {
        Title = "No wifi connection",
        Content = "Check your connection and try again.",
        CloseButtonText = "Ok"
    };

    ContentDialogResult result = await noWifiDialog.ShowAsync();
}
```

Wenn der Benutzer auf eine Dialogfeldschaltfläche klickt, gibt die Methode [ShowAsync](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.contentdialog.showasync.aspx) ein [ContentDialogResult](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.contentdialogresult.aspx) zurück, damit Sie wissen, auf welche Schaltfläche der Benutzer klickt.

Das Dialogfeld in diesem Beispiel stellt eine Frage und verwendet das zurückgegebene [ContentDialogResult](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.contentdialogresult.aspx), um die Antwort des Benutzers zu ermitteln.

```csharp
private async void DisplayDeleteFileDialog()
{
    ContentDialog deleteFileDialog = new ContentDialog
    {
        Title = "Delete file permanently?",
        Content = "If you delete this file, you won't be able to recover it. Do you want to delete it?",
        PrimaryButtonText = "Delete",
        CloseButtonText = "Cancel"
    };

    ContentDialogResult result = await deleteFileDialog.ShowAsync();

    // Delete the file if the user clicked the primary button.
    /// Otherwise, do nothing.
    if (result == ContentDialogResult.Primary)
    {
        // Delete the file.
    }
    else
    {
        // The user clicked the CLoseButton, pressed ESC, Gamepad B, or the system back button.
        // Do nothing.
    }
}
```

## <a name="flyouts"></a>Flyouts
###  <a name="create-a-flyout"></a>Erstellen eines Flyouts

Ein Flyout ist ein einfach ausblendbarer Container, der beliebige UI als Inhalt anzeigen kann. Flyouts können andere Flyouts oder Kontextmenüs enthalten, um eine geschachtelte Umgebung zu kreieren.

![Kontextmenü geschachtelt in einem Flyout](images/flyout-nested.png)

Flyouts sind an bestimmte Steuerelemente angefügt. Sie können mit der [Placement](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.placement.aspx)-Eigenschaft angeben, wo das Flyout angezeigt werden soll: oben, links, unten, rechts oder als Vollbild. Wenn Sie den [vollständigen Platzierungsmodus](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutplacementmode.aspx) auswählen, streckt die App das Flyout und zentriert es innerhalb des App-Fensters. Einige Steuerelemente wie z.B. [Schaltflächen](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.button.aspx), verfügen über eine [Flyout](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.button.flyout.aspx)-Eigenschaft, mit der Sie ein Flyout oder [Kontextmenü](menus.md) zuordnen können.

In diesem Beispiel wird ein einfaches Flyout erstellt, das Text anzeigt, wenn die Schaltfläche gedrückt wird.
````xaml
<Button Content="Click me">
  <Button.Flyout>
     <Flyout>
        <TextBlock Text="This is a flyout!"/>
     </Flyout>
  </Button.Flyout>
</Button>
````

Wenn das Steuerelement nicht über eine Flyout-Eigenschaft verfügt, können Sie stattdessen die angefügte Eigenschaft [FlyoutBase.AttachedFlyout](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.attachedflyout.aspx) verwenden. In diesem Fall müssen Sie zudem die [FlyoutBase.ShowAttachedFlyout](https://msdn.microsoft.com/en-us/library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.showattachedflyout)-Methode aufrufen, um das Flyout anzuzeigen.

In diesem Beispiel wird einem Bild ein einfaches Flyout hinzugefügt. Wenn der Benutzer auf das Bild tippt, zeigt die App das Flyout an.

````xaml
<Image Source="Assets/cliff.jpg" Width="50" Height="50"
  Margin="10" Tapped="Image_Tapped">
  <FlyoutBase.AttachedFlyout>
    <Flyout>
      <TextBlock Text="This is some text in a flyout."  />
    </Flyout>        
  </FlyoutBase.AttachedFlyout>
</Image>
````

````csharp
private void Image_Tapped(object sender, TappedRoutedEventArgs e)
{
    FlyoutBase.ShowAttachedFlyout((FrameworkElement)sender);
}
````

In den vorherigen Beispielen wurden die Flyouts inline definiert. Sie können ein Flyout auch als statische Ressource definieren und sie dann mit mehreren Elementen verwenden. In diesem Beispiel wird ein komplizierteres Flyout erstellt, mit dem eine größere Version eines Bilds angezeigt wird, wenn auf die Miniaturansicht getippt wird.

````xaml
<!-- Declare the shared flyout as a resource. -->
<Page.Resources>
    <Flyout x:Key="ImagePreviewFlyout" Placement="Right">
        <!-- The flyout's DataContext must be the Image Source
             of the image the flyout is attached to. -->
        <Image Source="{Binding Path=Source}"
            MaxHeight="400" MaxWidth="400" Stretch="Uniform"/>
    </Flyout>
</Page.Resources>
````

````xaml
<!-- Assign the flyout to each element that shares it. -->
<StackPanel>
    <Image Source="Assets/cliff.jpg" Width="50" Height="50"
           Margin="10" Tapped="Image_Tapped"
           FlyoutBase.AttachedFlyout="{StaticResource ImagePreviewFlyout}"
           DataContext="{Binding RelativeSource={RelativeSource Mode=Self}}"/>
    <Image Source="Assets/grapes.jpg" Width="50" Height="50"
           Margin="10" Tapped="Image_Tapped"
           FlyoutBase.AttachedFlyout="{StaticResource ImagePreviewFlyout}"
           DataContext="{Binding RelativeSource={RelativeSource Mode=Self}}"/>
    <Image Source="Assets/rainier.jpg" Width="50" Height="50"
           Margin="10" Tapped="Image_Tapped"
           FlyoutBase.AttachedFlyout="{StaticResource ImagePreviewFlyout}"
           DataContext="{Binding RelativeSource={RelativeSource Mode=Self}}"/>
</StackPanel>
````

````csharp
private void Image_Tapped(object sender, TappedRoutedEventArgs e)
{
    FlyoutBase.ShowAttachedFlyout((FrameworkElement)sender);  
}
````

### <a name="style-a-flyout"></a>Gestalten eines Flyouts
Um ein Flyout zu formatieren, ändern Sie den [FlyoutPresenterStyle](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.flyout.flyoutpresenterstyle.aspx). In diesem Beispiel wird ein Absatz mit Textumbruch dargestellt, was den Textblock für Bildschirmleseprogramme zugänglich gemacht.

![Zugängliches Flyout mit Textumbruch](images/flyout-wrapping-text.png)

````xaml
<Flyout>
  <Flyout.FlyoutPresenterStyle>
    <Style TargetType="FlyoutPresenter">
      <Setter Property="ScrollViewer.HorizontalScrollMode"
          Value="Disabled"/>
      <Setter Property="ScrollViewer.HorizontalScrollBarVisibility" Value="Disabled"/>
      <Setter Property="IsTabStop" Value="True"/>
      <Setter Property="TabNavigation" Value="Cycle"/>
    </Style>
  </Flyout.FlyoutPresenterStyle>
  <TextBlock Style="{StaticResource BodyTextBlockStyle}" Text="Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat."/>
</Flyout>
````

#### <a name="styling-flyouts-for-10-foot-experience"></a>Formatieren von Flyouts für die 10 Fuß-Umgebung

Einfach ausblendbare Steuerelemente wie Flyouts erhalten den Tastatur- bzw. Gamepad-Fokus, bis sie nicht mehr angezeigt werden. Um dieses Verhalten optisch zu kennzeichnen, werden diese einfach ausblendbaren Steuerelemente auf der Xbox als Überlagerung gezeichnet, wobei der Kontrast und die Helligkeit bzw. Sichtbarkeit der umgebenden Benutzeroberfläche reduziert wird. Dieses Verhalten kann mit der Eigenschaft [`LightDismissOverlayMode`](https://msdn.microsoft.com/ library/windows/apps/windows.ui.xaml.controls.primitives.flyoutbase.lightdismissoverlaymode.aspx) geändert werden. Standardmäßig erhalten Flyouts auf der Xbox (jedoch nicht auf anderen Gerätefamilien) die einfach ausblendbare Überlagerung. Apps können jedoch durchsetzen, dass die Überlagerung stets **An** oder stets **Aus** ist.

![Flyout mit Abblend-Überlagerung](images/flyout-smoke.png)

```xaml
<MenuFlyout LightDismissOverlayMode="On">
```

### <a name="light-dismiss-behavior"></a>Verhalten für einfaches Ausblenden
Flyouts können schnell mit einer einfachen Ausblend-Aktion geschlossen werden. Dazu zählen:
-    Tippen außerhalb des Flyouts
-    Drücken der ESC-Taste auf der Tastatur
-    Drücken der Zurück-Taste des Systems (Hardware oder Software)
-    Drücken der B-Taste auf dem Gamepad

Wird das Ausblenden durch Tippen vorgenommen, wird die Geste in der Regel absorbiert und nicht an die UI unterhalb weitergegeben. Ist beispielsweise hinter einem geöffneten Flyout eine Schaltfläche sichtbar, wird durch einfaches Antippen durch den Benutzer das Flyout ausgeblendet, ohne jedoch diese Schaltfläche zu aktivieren. Um die Schaltfläche zu drücken, ist ein weiteres Antippen nötig.

Sie können dieses Verhalten ändern, indem Sie die Schaltfläche als Pass-Through-Eingabeelement für das Flyout gestalten. Das Flyout wird wie oben beschriebenen durch die einfache Ausblend-Aktion geschlossen, gibt den Antipp-Vorgang aber gleichzeitig an das entsprechende `OverlayInputPassThroughElement` weiter. Erwägen Sie, dieses Verhalten zu übernehmen, um Interaktionen des Benutzers bei ähnlich funktionierenden Elementen zu beschleunigen. Wenn Ihre App eine Sammlung von Favoriten beinhaltet und jedes Element der Sammlung ein angefügtes Flyout enthält, kann man davon auszugehen, dass die Benutzer mehrere Flyouts in schneller Abfolge abarbeiten möchten.

[!NOTE] Achten Sie darauf, kein Überlagerungseingabeelement mit Pass-Through festzulegen, da dies in einer destruktiven Aktion resultiert. Die Benutzer sind an diskrete, einfach ausblendbare Aktionen gewöhnt, die die Primär-UI nicht aktivieren. Schließen, Löschen oder ähnlich destruktive Schaltflächen sollten nicht über einfach ausblendbare Elemente aktiviert werden, um unerwartetes und störendes Verhalten zu vermeiden.

Im folgenden Beispiel werden alle drei Schaltflächen in der Favoritenleiste durch einfaches Antippen aktiviert.

````xaml
<Page>
    <Page.Resources>
        <Flyout x:Name="TravelFlyout" x:Key="TravelFlyout"
                OverlayInputPassThroughElement="{x:Bind FavoritesBar}">
            <StackPanel>
                <HyperlinkButton Content="Washington Trails Association"/>
                <HyperlinkButton Content="Washington Cascades - Go Northwest! A Travel Guide"/>  
            </StackPanel>
        </Flyout>
    </Page.Resources>

    <Grid>
        <Grid.RowDefinitions>
            <RowDefinition Height="Auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
        <StackPanel x:Name="FavoritesBar" Orientation="Horizontal">
            <HyperlinkButton x:Name="PageLinkBtn">Bing</HyperlinkButton>  
            <Button x:Name="Folder1" Content="Travel" Flyout="{StaticResource TravelFlyout}"/>
            <Button x:Name="Folder2" Content="Entertainment" Click="Folder2_Click"/>
        </StackPanel>
        <ScrollViewer Grid.Row="1">
            <WebView x:Name="WebContent"/>
        </ScrollViewer>
    </Grid>
</Page>
````
````csharp
private void Folder2_Click(object sender, RoutedEventArgs e)
{
     Flyout flyout = new Flyout();
     flyout.OverlayInputPassThroughElement = FavoritesBar;
     ...
     flyout.ShowAt(sender as FrameworkElement);
{
````

## <a name="get-the-samples"></a>Beispiele herunterladen
*   [XAML-UI-Grundlagen](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/XamlUIBasics)<br/>
    Hier werden alle XAML-Steuerelemente in einem interaktiven Format dargestellt.

## <a name="related-articles"></a>Verwandte Artikel
- [QuickInfos](tooltips.md)
- [Menüs und Kontextmenü](menus.md)
- [Flyout-Klasse](https://msdn.microsoft.com/library/windows/apps/dn279496)
- [ContentDialog-Klasse](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.contentdialog.aspx)