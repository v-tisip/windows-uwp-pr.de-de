---
author: mijacobs
Description: "Mit adaptiven und interaktiven Popupbenachrichtigungen können Sie flexible Popupbenachrichtigungen mit mehr Inhalt, optionalen Inlinebildern und optionaler Benutzerinteraktion erstellen."
title: Adaptive und interaktive Popupbenachrichtigungen
ms.assetid: 1FCE66AF-34B4-436A-9FC9-D0CF4BDA5A01
label: Adaptive and interactive toast notifications
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.openlocfilehash: c8e77773b9118c3177dc958ddc7b51d32a452fa5
ms.sourcegitcommit: 9d1ca16a7edcbbcae03fad50a4a10183a319c63a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2017
---
# <a name="adaptive-and-interactive-toast-notifications"></a>Adaptive und interaktive Popupbenachrichtigungen

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

Mit adaptiven und interaktiven Popupbenachrichtigungen können Sie flexible Benachrichtigungen mit Text, Bildern und Schaltflächen/Eingaben erstellen.

> **Wichtige APIs**: [UWP Community Toolkit Notifications-NuGet-Paket](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/)

> [!NOTE]
> Die Legacyvorlagen von Windows8.1 und Windows Phone8.1 finden Sie im [Legacy-Popupvorlagenkatalog](https://msdn.microsoft.com/library/windows/apps/hh761494).


## <a name="getting-started"></a>Erste Schritte

**Installieren Sie die Benachrichtigungsbibliothek.** Wenn Sie C# anstelle von XML verwenden möchten, um Benachrichtigungen zu generieren, installieren Sie das NuGet-Paket mit dem Namen [Microsoft.Toolkit.Uwp.Notifications](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/). (Suchen Sie nach „Benachrichtigungen UWP“.) Die in diesem Artikel bereitgestellten C#-Beispiele verwenden Version 1.0.0 des NuGet-Pakets.

**Installieren Sie den Notifications Visualizer.** Diese kostenlose UWP-App hilft Ihnen, interaktive Popupbenachrichtigungen zu entwerfen, indem sie während der Bearbeitung des Popups sofort eine Vorschau des Popups bereitstellen, ähnlich dem XAML-Editor/der Entwurfsansicht von Visual Studio. Weitere Informationen finden Sie in [diesem Blogbeitrag](http://blogs.msdn.com/b/tiles_and_toasts/archive/2015/09/22/introducing-notifications-visualizer-for-windows-10.aspx). Der Download von Notifications Visualizer steht [hier](https://www.microsoft.com/store/apps/notifications-visualizer/9nblggh5xsl1) bereit.


## <a name="sending-a-toast-notification"></a>Senden einer Popupbenachrichtigung

Weitere Informationen zum Senden einer Benachrichtigung finden Sie unter [Senden einer lokalen Popupbenachrichtigung](tiles-and-notifications-send-local-toast.md). In dieser Dokumentation wird nur die Erstellung des Popupinhalts behandelt.


## <a name="toast-notification-structure"></a>Struktur der Popupbenachrichtigung

Popupbenachrichtigungen sind eine Kombination aus einigen Dateneigenschaften wie Tag/Group (mit denen Sie die Benachrichtigung identifizieren können) und dem *Popupinhalt*.

Die Kernkomponenten des Popupinhalts sind...
* **launch**: Hiermit wird definiert, welche Argumente wieder an Ihre App übergeben werden, wenn der Benutzer auf Ihr Popup klickt, sodass Sie einen Deep-Link zum richtigen Inhalt bereitstellen können, der im Popup angezeigt wurde. Weitere Informationen hierzu finden Sie unter [Senden einer lokalen Popupbenachrichtigung](tiles-and-notifications-send-local-toast.md).
* **visual**: der visuelle Teil des Popups, einschließlich der generischen Bindung, die Text, Bilder und App-Logos enthält
* **actions**: der interaktive Teil des Popups, einschließlich Eingaben und Aktionen
* **audio**: steuert die Tonwiedergabe, während dem Benutzer das Popup angezeigt wird

Der Popupinhalt ist in XML-Rohdaten definiert, aber Sie können unsere [NuGet-Bibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) verwenden, um ein C# (oder C++)-Objektmodell für die Erstellung des Popupinhalts zu erhalten. In diesem Artikel werden alle Elemente des Popupinhalts dokumentiert.

```csharp
ToastContent content = new ToastContent()
{
    Launch = "app-defined-string",
 
    Visual = new ToastVisual()
    {
        BindingGeneric = new ToastBindingGeneric() { ... }
    },
 
    Actions = new ToastActionsCustom() { ... },
 
    Audio = new ToastAudio() { ... }
};
```

```xml
<toast launch="app-defined-string">

  <visual>
    <binding template="ToastGeneric">
      ...
    </binding>
  </visual>

  <actions>
    ...
  </actions>

  <audio src="ms-winsoundevent:Notification.Reminder"/>

</toast>
```

Hier sehen Sie eine visuelle Darstellung des Inhalts des Popups:

![Aufbau einer Popupbenachrichtigung](images/adaptivetoasts-structure.jpg)


## <a name="visual"></a>Visuelles Element

Jedes Popup muss ein visuelles Element angeben, in dem Sie eine generische Popupbindung angeben müssen, die Text, Bilder, Logos und vieles mehr enthalten kann. Diese Elemente werden auf verschiedenen Windows-Geräten wie Desktops, Smartphones, Tablets und Xbox wiedergegeben.

Alle Attribute, die im Abschnitt „Visuelle Elemente“ unterstützt werden, sowie die untergeordneten Elemente [finden Sie in der Schemadokumentation](tiles-and-notifications-toast-schema.md#toastvisual).

Die Identität Ihrer App in der Popupbenachrichtigung wird über Ihr App-Symbol angegeben. Wenn Sie jedoch die App-Logo-Überschreibung verwenden, wird der Name Ihrer App unterhalb der Textzeilen angezeigt.

| Normales Popupfenster                                                                              | Popupfenster mit appLogoOverride                                                          |
| ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| ![Benachrichtigung ohne appLogoOverride](images/adaptivetoasts-withoutapplogooverride.jpg) | ![Benachrichtigung mit appLogoOverride](images/adaptivetoasts-withapplogooverride.jpg) |


## <a name="text-elements"></a>Textelemente

Jedes Popup muss mindestens ein Textelement enthalten und kann zwei zusätzliche Textelemente enthalten, wobei alle den Typ [AdaptiveText](tiles-and-notifications-toast-schema.md#adaptivetext) aufweisen müssen.

![Popup mit Titel und Beschreibung](images/toast-title-and-description.jpg)

Seit dem Anniversary Update können Sie mithilfe der **HintMaxLines**-Eigenschaft für den Text steuern, wie viele Zeilen Text angezeigt werden. In der Standardeinstellung werden im Titel zeigt bis zu 2 Textzeilen angezeigt. Die Beschreibungszeilen zeigen jeweils bis zu 4 Textzeilen an.

```csharp
new ToastBindingGeneric()
{
    Children =
    {
        new AdaptiveText()
        {
            Text = "Adaptive Tiles Meeting",
            HintMaxLines = 1
        },

        new AdaptiveText()
        {
            Text = "Conf Room 2001 / Building 135"
        },

        new AdaptiveText()
        {
            Text = "10:00 AM - 10:30 AM"
        }
    }
}
```

```xml
<binding template="ToastGeneric">
    <text hint-maxLines="1">Adaptive Tiles Meeting</text>
    <text>Conf Room 2001 / Building 135</text>
    <text>10:00 AM - 10:30 AM</text>
</binding>
```


## <a name="app-logo-override"></a>Überschreibung des App-Logos

Standardmäßig zeigt das Popup Ihr App-Logo an. Allerdings können Sie dieses Logo mit Ihrem eigenen [ToastGenericAppLogo](tiles-and-notifications-toast-schema.md#toastgenericapplogo)-Bild überschreiben. Wenn es sich beispielsweise um eine Benachrichtigung von einer Person handelt, empfehlen wir, das App-Logo mit einem Bild der betreffenden Person zu überschreiben.

![Popup mit App-Logo-Überschreibung](images/toast-applogooverride.jpg)

Sie können die **HintCrop**-Eigenschaft verwenden, um den Zuschnitt des Bilds zu ändern. So ergibt *Kreis* z. B. ein kreisförmig zugeschnittenes Bild. Andernfalls ist das Bild quadratisch. Bildabmessungen sind 64x64Pixel bei einer Skalierung von 100%.

```csharp
new ToastBindingGeneric()
{
    ...

    AppLogoOverride = new ToastGenericAppLogo()
    {
        Source = "https://unsplash.it/64?image=883",
        HintCrop = ToastGenericAppLogoCrop.Circle
    }
}
```

```xml
<binding template="ToastGeneric">
    ...
    <image placement="appLogoOverride" hint-crop="circle" src="https://unsplash.it/64?image=883"/>
</binding>
```


## <a name="hero-image"></a>Favoritenbild

**Neu im Anniversary Update**: Popups können ein Favoritenbild anzeigen. Dabei handelt es sich um ein ausgewähltes [ToastGenericHeroImage](tiles-and-notifications-toast-schema.md#toastgenericheroimage), das an hervorgehobener Stelle innerhalb des Popup-Banners und im Info-Center angezeigt wird. Bildabmessungen sind 360x180Pixel bei einer Skalierung von 100%.

![Popup mit Favoritenbild](images/toast-heroimage.jpg)

```csharp
new ToastBindingGeneric()
{
    ...

    HeroImage = new ToastHeroImage()
    {
        Source = "https://unsplash.it/360/180?image=1043"
    }
}
```

```xml
<binding template="ToastGeneric">
    ...
    <image placement="hero" src="https://unsplash.it/360/180?image=1043"/>
</binding>
```


## <a name="inline-image"></a>Inline-Bild

Sie können ein Inline-Bild in voller Breite bereitstellen, das angezeigt wird, wenn das Popup erweitert wird.

![Popup mit zusätzlichem Bild](images/toast-additionalimage.jpg)

```csharp
new ToastBindingGeneric()
{
    Children =
    {
        ...

        new AdaptiveImage()
        {
            Source = "https://unsplash.it/360/180?image=1043"
        }
    }
}
```

```xml
<binding template="ToastGeneric">
    ...
    <image src="https://unsplash.it/360/180?image=1043" />
</binding>
```


## <a name="attribution-text"></a>Zuschreibungstext

**Neu im Anniversary Update**: Wenn Sie die Quelle des Inhalts angeben müssen, können Sie Zuschreibungstext verwenden. Dieser Text wird zusammen mit der Identität Ihrer App oder dem Zeitstempel der Benachrichtigung immer am unteren Rand der Benachrichtigung angezeigt.

Für ältere Versionen von Windows, die Zuschreibungstext nicht unterstützen, wird der Text einfach als weiteres Textelement angezeigt (sofern Sie nicht bereits die maximalen drei Textelemente verwenden).

![Popup mit Zuschreibungstext](images/toast-attributiontext.jpg)

```csharp
new ToastBindingGeneric()
{
    ...

    Attribution = new ToastGenericAttributionText()
    {
        Text = "Via SMS"
    }
}
```

```xml
<binding template="ToastGeneric">
    ...
    <text placement="attribution">Via SMS</text>
</binding>
```


## <a name="custom-timestamp"></a>Benutzerdefinierter Zeitstempel

**Neu im Creators Update**: Sie können jetzt den vom System bereitgestellten Zeitstempel mit Ihrem eigenen Zeitstempel überschreiben, der genau angibt, wann die Nachricht/die Informationen/der Inhalt erstellt wurden. Dieser Zeitstempel wird im Info-Center angezeigt.

![Popup mit benutzerdefiniertem Zeitstempel](images/toast-customtimestamp.jpg)

Weitere Informationen zum Verwenden eines benutzerdefinierten Zeitstempels [finden Sie in diesem Blogbeitrag](https://blogs.msdn.microsoft.com/tiles_and_toasts/2017/01/09/custom-timestamp-on-toast-notifications-windows-10-creators-update/).

```csharp
ToastContent toastContent = new ToastContent()
{
    DisplayTimestamp = new DateTime(2017, 04, 15, 19, 45, 00, DateTimeKind.Utc),
    ...
};
```

```xml
<toast displayTimestamp="2017-04-15T19:45:00Z">
  ...
</toast>
```


## <a name="adaptive-content"></a>Adaptiver Inhalt

**Neu im Anniversary Update**: Zusätzlich zu dem oben angegebenen Inhalt können Sie auch zusätzlichen adaptiven Inhalt anzeigen, der sichtbar ist, wenn das Popup erweitert wird.

Dieser zusätzliche Inhalt wird mit Adaptive angegeben. Mehr zu diesem Thema erfahren Sie in der [Dokumentation zu adaptiven Kacheln](tiles-and-notifications-create-adaptive-tiles.md).

Beachten Sie, dass jeglicher adaptiver Inhalt in einer AdaptiveGroup enthalten sein müssen. Andernfalls wird der nicht mit Adaptive gerendert.


### <a name="columns-and-text-elements"></a>Spalten und Textelemente

Hier ist ein Beispiel, in dem Spalten und einige erweiterte adaptive Textelemente verwendet werden. Da die Textelemente in einer AdaptiveGroup enthalten sind, unterstützen sie alle erweiterten adaptiven Stileigenschaften.

![Popup mit zusätzlichem Text](images/toast-additionaltext.jpg)

```csharp
new ToastBindingGeneric()
{
    Children =
    {
        ...

        new AdaptiveGroup()
        {
            Children =
            {
                new AdaptiveSubgroup()
                {
                    Children =
                    {
                        new AdaptiveText()
                        {
                            Text = "52 attendees",
                            HintStyle = AdaptiveTextStyle.Base
                        },
                        new AdaptiveText()
                        {
                            Text = "23 minute drive",
                            HintStyle = AdaptiveTextStyle.CaptionSubtle
                        }
                    }
                },
                new AdaptiveSubgroup()
                {
                    Children =
                    {
                        new AdaptiveText()
                        {
                            Text = "1 Microsoft Way",
                            HintStyle = AdaptiveTextStyle.CaptionSubtle,
                            HintAlign = AdaptiveTextAlign.Right
                        },
                        new AdaptiveText()
                        {
                            Text = "Bellevue, WA 98008",
                            HintStyle = AdaptiveTextStyle.CaptionSubtle,
                            HintAlign = AdaptiveTextAlign.Right
                        }
                    }
                }
            }
        }
    }
}
```

```xml
<binding template="ToastGeneric">
    ...
    <group>
        <subgroup>
            <text hint-style="base">52 attendees</text>
            <text hint-style="captionSubtle">23 minute drive</text>
        </subgroup>
        <subgroup>
            <text hint-style="captionSubtle" hint-align="right">1 Microsoft Way</text>
            <text hint-style="captionSubtle" hint-align="right">Bellevue, WA 98008</text>
        </subgroup>
    </group>
</binding>
```


## <a name="inputs-and-buttons"></a>Eingaben und Schaltflächen

Eingaben und Schaltflächen werden innerhalb des Bereichs „Aktionen“ der Popupregion des Popups angegeben. Das bedeutet, dass sie nur angezeigt werden, wenn das Popup erweitert wird.


### <a name="quick-reply-text-box"></a>Textfeld für schnelle Antworten

Um ein Textfeld für schnelle Antworten– etwa für ein Nachrichten-Szenario – zu aktivieren, fügen Sie eine Texteingabe und eine Schaltfläche hinzu, und verweisen Sie auf die ID der Texteingabe, damit die Schaltfläche neben der Eingabe angezeigt wird.

![Benachrichtigung mit Texteingabe und Aktionen](images/adaptivetoasts-xmlsample05.jpg)

```csharp
ToastContent content = new ToastContent()
{
    ...
 
    Actions = new ToastActionsCustom()
    {
        Inputs =
        {
            new ToastTextBox("tbReply")
            {
                PlaceholderContent = "Type a reply"
            }
        },

        Buttons =
        {
            new ToastButton("Reply", "action=reply&convId=9318")
            {
                ActivationType = ToastActivationType.Background,

                // To place the button next to the text box,
                // reference the text box's Id and provide an image
                TextBoxId = "tbReply",
                ImageUri = "Assets/Reply.png"
            }
        }
    }
};
```

```xml
<toast launch="app-defined-string">

    ...

    <actions>

        <input id="textBox" type="text" placeholderContent="Type a reply"/>

        <action
            content="Send",
            arguments="action=reply&amp;convId=9318"
            activationType="background"
            hint-inputId="textBox"
            imageUri="Assets/Reply.png"/>

    </actions>

</toast>
```


### <a name="inputs-with-buttons-bar"></a>Eingaben mit Schaltflächenleiste

Es können auch eine oder mehrere Eingaben mit normalen Schaltflächen unterhalb der Eingaben angezeigt werden.

![Benachrichtigung mit Text und Eingabeaktionen](images/adaptivetoasts-xmlsample04.jpg)

```csharp
ToastContent content = new ToastContent()
{
    ...
 
    Actions = new ToastActionsCustom()
    {
        Inputs =
        {
            new ToastTextBox("tbReply")
            {
                PlaceholderContent = "Type a reply"
            }
        },

        Buttons =
        {
            new ToastButton("Reply", "action=reply&threadId=9218")
            {
                ActivationType = ToastActivationType.Background
            },

            new ToastButton("Video call", "action=videocall&threadId=9218")
            {
                ActivationType = ToastActivationType.Foreground
            }
        }
    }
};
```

```xml
<toast launch="app-defined-string">

    ...

    <actions>

        <input id="textBox" type="text" placeholderContent="Type a reply"/>

        <action
            content="Reply",
            arguments="action=reply&amp;threadId=9218"
            activationType="background"/>

        <action
            content="Video call",
            arguments="action=videocall&amp;threadId=9218"
            activationType="foreground"/>

    </actions>

</toast>
```


### <a name="selection-input"></a>Auswahleingabe

Zusätzlich zu Textfeldern können Sie auch ein Auswahlmenü verwenden.

![Benachrichtigung mit Auswahleingabe und Aktionen](images/adaptivetoasts-xmlsample06.jpg)

```csharp
ToastContent content = new ToastContent()
{
    ...
 
    Actions = new ToastActionsCustom()
    {
        Inputs =
        {
            new ToastSelectionBox("time")
            {
                DefaultSelectionBoxItemId = "lunch",
                Items =
                {
                    new ToastSelectionBoxItem("breakfast", "Breakfast"),
                    new ToastSelectionBoxItem("lunch", "Lunch"),
                    new ToastSelectionBoxItem("dinner", "Dinner")
                }
            }
        },

        Buttons = { ... }
};
```

```xml
<toast launch="app-defined-string">

    ...

    <actions>

        <input id="time" type="selection" defaultInput="lunch">
            <selection id="breakfast" content="Breakfast" />
            <selection id="lunch" content="Lunch" />
            <selection id="dinner" content="Dinner" />
        </input>

        ...

    </actions>

</toast>
```


## <a name="buttons"></a>Schaltflächen

Schaltflächen machen Ihr Popup interaktiv. Sie erlauben dem Benutzer, in Ihrer Popupbenachrichtigung schnelle Aktionen auszuführen, ohne den aktuellen Workflow zu unterbrechen. Benutzer können z.B. eine Nachricht direkt in einem Popup beantworten oder eine E-Mail löschen, ohne die E-Mail-App überhaupt zu öffnen.

Schaltflächen können die folgenden verschiedenen Aktionen ausführen...

-   Aktivieren der App im Vordergrund mit einem Argument, das zum Navigieren zu einer bestimmten Seite bzw. einem bestimmten Kontext verwendet werden kann
-   Aktivieren der Hintergrundaufgabe der App für eine schnelle Antwort oder ein ähnliches Szenario
-   Aktivieren einer anderen App per Protokollstart
-   Durchführen einer Systemaktion, z.B. erneute Erinnerung oder Schließen der Benachrichtigung

Beachten Sie, dass Sie nur bis zu 5 Schaltflächen haben können (einschließlich Elementen des Kontextmenüs, die später erläutert werden).

![Benachrichtigung mit Aktionen, Beispiel1](images/adaptivetoasts-xmlsample02.jpg)

```csharp
ToastContent content = new ToastContent()
{
    ...
 
    Actions = new ToastActionsCustom()
    {
        Buttons =
        {
            new ToastButton("See more details", "action=viewdetails&contentId=351")
            {
                ActivationType = ToastActivationType.Foreground
            },

            new ToastButton("Remind me later", "action=remindlater&contentId=351")
            {
                ActivationType = ToastActivationType.Background
            }
        }
    }
};
```

```xml
<toast launch="app-defined-string">

    ...

    <actions>

        <action
            content="See more details",
            arguments="action=viewdetails&amp;contentId=351"
            activationType="foreground"/>

        <action
            content="Remind me later",
            arguments="action=remindlater&amp;contentId=351"
            activationType="background"/>

    </actions>

</toast>
```


### <a name="snoozedismiss-buttons"></a>Schaltflächen für erneutes Erinnern/Schließen

Mithilfe eines Auswahlmenüs und zwei Schaltflächen können wir eine Erinnerungsbenachrichtigung erstellen, welche die Systemaktionen zum erneuten Erinnern und Schließen verwendet. Legen Sie unbedingt das Szenario für die Benachrichtigung auf „Erinnerung“ fest, damit sie sich wie eine Erinnerung verhält.

![Erinnerungsbenachrichtigung](images/adaptivetoasts-xmlsample07.jpg)

Wir verknüpfen die Schaltfläche „Erneut erinnern“ mithilfe der *SepectionBoxId*-Eigenschaft der Popupschaltfläche mit der Auswahlmenüeingabe.

```csharp
ToastContent content = new ToastContent()
{
    Scenario = ToastScenario.Reminder,

    ...
 
    Actions = new ToastActionsCustom()
    {
        Inputs =
        {
            new ToastSelectionBox("snoozeTime")
            {
                DefaultSelectionBoxItemId = "15",
                Items =
                {
                    new ToastSelectionBoxItem("5", "5 minutes"),
                    new ToastSelectionBoxItem("15", "15 minutes"),
                    new ToastSelectionBoxItem("60", "1 hour"),
                    new ToastSelectionBoxItem("240", "4 hours"),
                    new ToastSelectionBoxItem("1440", "1 day")
                }
            }
        },

        Buttons =
        {
            new ToastButtonSnooze()
            {
                SelectionBoxId = "snoozeTime"
            },
 
            new ToastButtonDismiss()
        }
    }
};
```

```xml
<toast scenario="reminder" launch="action=viewEvent&amp;eventId=1983">
   
  ...
 
  <actions>
     
    <input id="snoozeTime" type="selection" defaultInput="15">
      <selection id="1" content="1 minute"/>
      <selection id="15" content="15 minutes"/>
      <selection id="60" content="1 hour"/>
      <selection id="240" content="4 hours"/>
      <selection id="1440" content="1 day"/>
    </input>
 
    <action activationType="system" arguments="snooze" hint-inputId="snoozeTime" content="" />
 
    <action activationType="system" arguments="dismiss" content=""/>
     
  </actions>
   
</toast>
```

Gehen Sie wie folgt vor, um die Systemaktionen zum erneuten Erinnern und Schließen zu verwenden:

-   Angeben eines ToastButtonSnooze oder ToastButtonDismiss
-   Geben Sie optional eine benutzerdefinierte Inhaltszeichenfolge an:
    -   Wenn Sie keine Zeichenfolge bereitstellen, verwenden wir für „Erneut erinnern“ und „Schließen“ automatisch lokalisierte Zeichenfolgen.
-   Geben Sie optional die *SelectionBoxId* an:
    -   Wenn Sie nicht möchten, dass der Benutzer ein Intervall für das erneute Erinnern auswählen kann, sondern das erneute Erinnern an die Benachrichtigung nur einmal in einem vom System definierten (in allen Betriebssystemen einheitlichen) Zeitintervall erfolgt, legen Sie keinen Wert für &lt;input&gt; fest.
    -   Wenn Sie Intervalle für das erneute Erinnern angeben möchten:
        -   Geben Sie *SelectionBoxId* in der Aktion für das erneute Erinnern an
        -   Stimmen Sie die ID der Eingabe auf den Wert für *SelectionBoxId* der Aktion für das erneute Erinnern ab
        -   Legen Sie für den Wert von *ToastSelectionBoxItem* eine positive ganze Zahl (nonNegativeInteger) fest, die dem Intervall für das erneute Erinnern in Minuten entspricht.



## <a name="audio"></a>Audio

Benutzerdefinierte Audioeffekte wurden schon immer von Mobile unterstützt und wird in der Desktop-Version 1511 (Build 10586) oder einer neueren Version unterstützt. Benutzerdefinierte Audioeffekte können über die folgenden Pfade verwiesen werden:

-   ms-appx:///
-   ms-appdata:///

Sie können alternativ aus der [Liste "ms-winsoundevents"](https://msdn.microsoft.com/library/windows/apps/br230842) auswählen, welche bisher immer auf beiden Plattformen unterstützt wurden.

```csharp
ToastContent content = new ToastContent()
{
    ...

    Audio = new ToastAudio()
    {
        Src = new Uri("ms-appx:///Assets/NewMessage.mp3")
    }
}
```

```xml
<toast launch="app-defined-string">

    ...

    <audio src="ms-appx:///Assets/NewMessage.mp3"/>

</toast>
```

Erhalten Sie unter der [Seite](https://msdn.microsoft.com/library/windows/apps/br230842) Informationen zu Töne für Popupbenachrichtigungen. Informationen für das Senden einer Popupbenachrichtigung mit benutzerdefinierten Audioeffekten [finden Sie unter folgenden Blogbeitrag](https://blogs.msdn.microsoft.com/tiles_and_toasts/2016/06/18/quickstart-sending-a-toast-notification-with-custom-audio/).


## <a name="alarms-reminders-and-incoming-calls"></a>Alarme, Erinnerungen und eingehende Anrufe

Um Alarme, Erinnerungen und Benachrichtigungen über eingehende Anrufe zu erstellen, verwenden Sie einfach eine normale Popupbenachrichtigung mit einem zugewiesenen Szenariowert. Das Szenario umfasst einige Verhaltensweisen, um eine konsistente und einheitliche Benutzererfahrung zu schaffen.

* **Erinnerung**: Die Benachrichtigung bleibt auf dem Bildschirm, bis der Benutzer sie schließt oder eine Aktion ausführt. Unter Windows Mobile wird das Popup auch vorab vergrößert angezeigt. Ein Erinnerungston wird wiedergegeben.
* **Alarm**: Zusätzlich zu den Erinnerungsverhaltensweisen wird bei Alarmen zusätzlich eine Audioschleife mit einem standardmäßigen Alarmton wiedergegeben.
* **IncomingCall**: Benachrichtigungen über eingehende Anrufe werden auf Windows Mobile-Geräten im Vollbildmodus angezeigt. Andernfalls weisen sie die gleichen Verhaltensweisen wie Alarme auf, außer dass sie einen Klingelton verwenden.

```csharp
ToastContent content = new ToastContent()
{
    Scenario = ToastScenario.Reminder,

    ...
}
```

```xml
<toast scenario="reminder" launch="app-defined-string">

    ...

</toast>
```


## <a name="handling-activation"></a>Behandeln der Aktivierung
Informationen dazu, wie Sie Popupaktivierungen behandeln (der Benutzer klickt auf Ihr Popup oder auf Schaltflächen im Popup), finden Sie unter [Senden einer lokalen Popupbenachrichtigung](tiles-and-notifications-send-local-toast.md).


 
## <a name="related-topics"></a>Verwandte Themen

* [Senden einer lokalen Popupbenachrichtigung und Behandeln der Aktivierung](tiles-and-notifications-send-local-toast.md)
* [Benachrichtigungsbibliothek auf GitHub](https://github.com/Microsoft/UWPCommunityToolkit/tree/dev/Notifications)