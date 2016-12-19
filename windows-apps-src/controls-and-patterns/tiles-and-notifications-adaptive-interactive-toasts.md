---
author: mijacobs
Description: "Mit adaptiven und interaktiven Popupbenachrichtigungen können Sie flexible Popupbenachrichtigungen mit mehr Inhalt, optionalen Inlinebildern und optionaler Benutzerinteraktion erstellen."
title: Adaptive und interaktive Popupbenachrichtigungen
ms.assetid: 1FCE66AF-34B4-436A-9FC9-D0CF4BDA5A01
label: Adaptive and interactive toast notifications
template: detail.hbs
translationtype: Human Translation
ms.sourcegitcommit: 2ac3a4a1efa85a3422d8964ad4ee62db28bc975f
ms.openlocfilehash: cfbbf110ed6df1b7e81e0505dcf55a63ba8739aa

---
# <a name="adaptive-and-interactive-toast-notifications"></a>Adaptive und interaktive Popupbenachrichtigungen

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css"> 

Mit adaptiven und interaktiven Popupbenachrichtigungen können Sie flexible Popupbenachrichtigungen mit mehr Inhalt, optionalen Inlinebildern und optionaler Benutzerinteraktion erstellen.

Beim adaptiven und interaktiven Popupbenachrichtigungsmodell haben diese Updates Vorrang vor dem Legacy-Popupvorlagenkatalog:

-   Die Option zum Einschließen von Schaltflächen und Eingaben in den Benachrichtigungen.
-   Drei verschiedene Aktivierungstypen für die wichtigste Popupbenachrichtigung und für jede Aktion.
-   Die Option zum Erstellen von Benachrichtigungen für bestimmte Szenarios wie Alarme, Erinnerungen und eingehende Anrufe.

**Hinweis**   Die Legacyvorlagen von Windows 8.1 und Windows Phone 8.1 finden Sie im [Legacy-Popupvorlagenkatalog](https://msdn.microsoft.com/library/windows/apps/hh761494).


## <a name="getting-started"></a>Erste Schritte

**Installieren Sie die Benachrichtigungsbibliothek.** Wenn Sie C# anstelle von XML verwenden möchten, um Benachrichtigungen zu generieren, installieren Sie das NuGet-Paket mit dem Namen [Microsoft.Toolkit.Uwp.Notifications](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/). (Suchen Sie nach „Benachrichtigungen UWP“.) Die in diesem Artikel bereitgestellten C#-Beispiele verwenden Version 1.0.0 des NuGet-Pakets.

**Installieren Sie den Notifications Visualizer.** Diese kostenlose UWP-App hilft Ihnen, interaktive Popupbenachrichtigungen zu entwerfen, indem sie während der Bearbeitung des Popups sofort eine Vorschau des Popups bereitstellen, ähnlich dem XAML-Editor/der Entwurfsansicht von Visual Studio. Weitere Informationen finden Sie in [diesem Blogbeitrag](http://blogs.msdn.com/b/tiles_and_toasts/archive/2015/09/22/introducing-notifications-visualizer-for-windows-10.aspx). Der Download von Notifications Visualizer steht [hier](https://www.microsoft.com/store/apps/notifications-visualizer/9nblggh5xsl1) bereit.


## <a name="toast-notification-structure"></a>Struktur der Popupbenachrichtigung


Popupbenachrichtigungen werden mit XML erstellt und enthalten in der Regel diese wichtigen Elemente:

-   &lt;visual&gt; umfasst den Inhalt, den Benutzer visuell wahrnehmen können, z. B. Text und Bilder
-   &lt;actions&gt; enthält Schaltflächen/Eingaben, die der Entwickler innerhalb der Benachrichtigung hinzufügen möchte
-   &lt;audio&gt; legt den Ton beim Anzeigen der Benachrichtigung fest

Hier sehen Sie ein Codebeispiel:

```XML
<toast launch="app-defined-string">
  <visual>
    <binding template="ToastGeneric">
      <text>Sample</text>
      <text>This is a simple toast notification example</text>
      <image placement="AppLogoOverride" src="oneAlarm.png" />
    </binding>
  </visual>
  <actions>
    <action content="check" arguments="check" imageUri="check.png" />
    <action content="cancel" arguments="cancel" />
  </actions>
  <audio src="ms-winsoundevent:Notification.Reminder"/>
</toast>
```

```CSharp
ToastContent content = new ToastContent()
{
    Launch = "app-defined-string",
 
    Visual = new ToastVisual()
    {
        BindingGeneric = new ToastBindingGeneric()
        {
            Children =
            {
                new AdaptiveText()
                {
                    Text = "Sample"
                },
 
                new AdaptiveText()
                {
                    Text = "This is a simple toast notification example"
                }
            },
 
            AppLogoOverride = new ToastGenericAppLogo()
            {
                Source = "oneAlarm.png"
            }
        }
    },
 
    Actions = new ToastActionsCustom()
    {
        Buttons =
        {
            new ToastButton("check", "check")
            {
                ImageUri = "check.png"
            },
 
            new ToastButton("cancel", "cancel")
            {
                ImageUri = "cancel.png"
            }
        }
    },
 
    Audio = new ToastAudio()
    {
        Src = new Uri("ms-winsoundevent:Notification.Reminder")
    }
};
```

Sie können diesen Code anschließend verwenden, um das Popupfenster zu erstellen und zu senden.

```CSharp
ToastNotification notification = new ToastNotification(content.GetXml());
ToastNotificationManager.CreateToastNotifier().Show(notification);
```

Eine vollständige funktionierende App mit Popupbenachrichtigungen finden Sie unter [Schnellstart: Senden einer lokalen Popupbenachrichtigung](https://github.com/WindowsNotifications/quickstart-sending-local-toast-win10).

Und eine visuelle Darstellung der Struktur:

![Struktur der Popupbenachrichtigung](images/adaptivetoasts-structure.jpg)

### <a name="visual"></a>Visuelle Elemente

Innerhalb des visuellen Elements benötigen Sie exakt ein Bindungselement, das den visuellen Inhalt des Popups aufweist.

Kachelbenachrichtigungen in Apps für die Universelle Windows-Plattform (UWP) unterstützen mehrere Vorlagen, die auf unterschiedlichen Kachelgrößen basieren. Popupbenachrichtigungen haben jedoch nur einen Vorlagennamen: **ToastGeneric**. Mit nur einer Vorlage profitieren Sie mehrfach:

-   Sie können den Popupinhalt ändern, indem Sie z. B. eine weitere Textzeile bzw. ein Inlinebild hinzufügen oder die Anzeige der Miniaturansicht so ändern, dass statt des App-Symbols etwas anderes angezeigt wird. Dabei müssen Sie weder die gesamte Vorlage ändern noch eine ungültige Nutzlast aufgrund einer Nichtübereinstimmung zwischen dem Vorlagennamen und dem Inhalt riskieren.
-   Sie können denselben Code verwenden, um die gleiche Nutzlast für die **Popupbenachrichtigung** an verschiedene Arten von Microsoft Windows-Geräten wie Smartphones, Tablets, PCs und Xbox zu schaffen. Diese Geräte akzeptieren die Benachrichtigung und zeigt sie dem Benutzer gemäß ihren UI-Richtlinien mit den entsprechenden visuellen Angeboten und Interaktionsmodellen an.

Alle Attribute, die im Abschnitt „Visuelle Elemente“ und dessen untergeordneten Elemente unterstützt werden, finden Sie im Abschnitt mit den Schemas. Weitere Beispiele finden Sie unten im Abschnitt mit den XML-Beispielen.

Die Identität Ihrer App wird über ein App-Symbol angegeben. Wenn Sie jedoch AppLogoOverride verwenden, wird der Name Ihrer App unterhalb der Textzeilen angezeigt.

| Normales Popupfenster                                                                              | Popupfenster mit appLogoOverride                                                          |
| ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| ![Benachrichtigung ohne appLogoOverride](images/adaptivetoasts-withoutapplogooverride.jpg) | ![Benachrichtigung mit appLogoOverride](images/adaptivetoasts-withapplogooverride.jpg) |

### <a name="actions"></a>Aktionen

In UWP-Apps können Sie Ihren Popupbenachrichtigungen Schaltflächen und andere Eingaben hinzufügen, um Benutzern mehr Aktionen außerhalb der App zu ermöglichen. Diese Aktionen werden unter dem Element &lt;actions&gt; angegeben. Davon können Sie zwei Arten angeben:

-   &lt;action&gt; wird als Schaltfläche auf Desktops und mobilen Geräten angezeigt. Sie können bis zu fünf benutzerdefinierte Aktionen oder Systemaktionen innerhalb einer Popupbenachrichtigung angeben.
-   &lt;input&gt; ermöglicht Benutzereingaben, z. B. schnelles Beantworten einer Nachricht oder Auswählen einer Option aus einem Dropdown-Menü.

Sowohl &lt;action&gt; als auch &lt;input&gt; gelten für die Windows-Gerätefamilie. Bei mobilen Geräten oder Desktop-Geräten stellt &lt;action&gt; beispielsweise eine Schaltfläche dar, auf die Benutzer tippen/klicken können. &lt;input&gt; für Text ist ein Feld, in dem Benutzer über eine physische Tastatur oder eine Bildschirmtastatur Text eingeben können. Diese Elemente passen sich auch an zukünftige Interaktionsszenarios an, z. B. eine per Sprachansage angekündigte Aktion oder eine Texteingabe per Diktat.

Wenn vom Benutzer eine Aktion ausgeführt wird, können Sie eine der folgenden Aktionen ausführen, indem Sie das Attribut [**ActivationType**](https://msdn.microsoft.com/library/windows/desktop/dn408447) im &lt;action&gt;-Element angeben:

-   Aktivieren der App im Vordergrund mit einem aktionsspezifischen Argument, das zum Navigieren zu einer bestimmten Seite bzw. einem bestimmten Kontext verwendet werden kann
-   Aktivieren der Hintergrundaufgabe der App ohne Auswirkung auf die Benutzer.
-   Aktivieren einer anderen App per Protokollstart.
-   Angeben einer auszuführenden Systemaktion. Die aktuell verfügbaren Systemaktionen sind die Funktionen zum erneuten Erinnern und zum Schließen geplanter Alarme/Erinnerungen. Auf diese wird in einem späteren Abschnitt eingegangen.

Alle Attribute, die im Abschnitt „Visuelle Elemente“ und dessen untergeordneten Elemente unterstützt werden, finden Sie im Abschnitt mit den Schemas. Weitere Beispiele finden Sie unten im Abschnitt mit den XML-Beispielen.

### <a name="audio"></a>Audio

Benutzerdefinierte Töne werden derzeit nicht von UWP-Apps für die Desktop-Plattform unterstützt. Stattdessen können Sie aus der Liste „ms-winsoundevents“ für Ihre App auf dem Desktop wählen. UWP-Apps auf mobilen Plattformen unterstützen sowohl „ms-winsoundevents“ als auch benutzerdefinierte Töne in den folgenden Formaten:

-   ms-appx:///
-   ms-appdata:///

Auf der [Seite mit den Audioschemas](https://msdn.microsoft.com/library/windows/apps/br230842) finden Sie Informationen zu Tönen für Popupbenachrichtigungen, darunter die vollständige Liste „ms-winsoundevents“.

## <a name="alarms-reminders-and-incoming-calls"></a>Alarme, Erinnerungen und eingehende Anrufe


Sie können Popupbenachrichtigungen für Alarme, Erinnerungen und eingehende Anrufe verwenden. Das Design dieser speziellen Popups stimmt mit dem von Standardpopups überein. Für einige benutzerdefinierte, szenariobasierte Benutzeroberflächen und Muster sind jedoch spezielle Popups möglich:

-   Eine Erinnerungs-Popupbenachrichtigung bleibt auf dem Bildschirm, bis der Benutzer sie schließt oder eine Aktion ausführt. Unter Windows Mobile können Erinnerungs-Popupbenachrichtigungen auch vorab vergrößert angezeigt werden.
-   Alarmbenachrichtigungen teilen nicht nur die oben genannten Verhaltensweisen mit Erinnerungsbenachrichtigungen, sondern können zudem automatisch Audioschleifen abspielen.
-   Benachrichtigungen über eingehende Anrufe werden auf Windows Mobile-Geräten im Vollbildmodus angezeigt. Dies erfolgt durch Angabe des Szenarioattributs innerhalb des Stammelements einer &lt;Popupbenachrichtigung&gt;: &lt;Popupszenario = " {default | alarm | reminder | incomingCall }" &gt;

## <a name="xml-examples"></a>XML-Beispiele


**Hinweis**  Die Screenshots für diese Beispiele zu Popupbenachrichtigungen stammen aus einer Desktop-App. Auf mobilen Geräten wird die Popupbenachrichtigung möglicherweise reduziert angezeigt. Über einen Ziehpunkt am unteren Rand des Popups kann sie vergrößert werden.

 

**Benachrichtigung mit umfassenden Visualisierungen**

Dieses Beispiel zeigt, wie Sie mehrere Textzeilen, ein optionales kleines Bild zum Außerkraftsetzen des Anwendungslogos und eine optionale Miniaturansicht für ein Inlinebild erstellen.

```XML
<toast launch="app-defined-string">
  <visual>
    <binding template="ToastGeneric">
      <text>Photo Share</text>
      <text>Andrew sent you a picture</text>
      <text>See it in full size!</text>
      <image src="https://unsplash.it/360/180?image=1043" />
      <image placement="appLogoOverride" src="https://unsplash.it/64?image=883" hint-crop="circle" />
    </binding>
  </visual>
</toast>
```

```CSharp
ToastContent content = new ToastContent()
{
    Launch = "app-defined-string",
 
    Visual = new ToastVisual()
    {
        BindingGeneric = new ToastBindingGeneric()
        {
            Children =
            {
                new AdaptiveText()
                {
                    Text = "Photo Share"
                },
 
                new AdaptiveText()
                {
                    Text = "Andrew sent you a picture"
                },
 
                new AdaptiveText()
                {
                    Text = "See it in full size!"
                },
 
                new AdaptiveImage()
                {
                    Source = "https://unsplash.it/360/180?image=1043"
                }
            },
 
            AppLogoOverride = new ToastGenericAppLogo()
            {
                Source = "https://unsplash.it/64?image=883",
                HintCrop = ToastGenericAppLogoCrop.Circle
            }
        }
    }
};
```

![Benachrichtigung mit umfassenden Visualisierungen](images/adaptivetoasts-xmlsample01.jpg)

 

**Benachrichtigung mit Aktionen, Beispiel 1**

Dieses Beispiel zeigt Folgendes:

```XML
<toast launch="app-defined-string">
  <visual>
    <binding template="ToastGeneric">
      <text>Microsoft Company Store</text>
      <text>New Halo game is back in stock!</text>
    </binding>
  </visual>
  <actions>
    <action activationType="foreground" content="See more details" arguments="details"/>
    <action activationType="background" content="Remind me later" arguments="later"/>
  </actions>
</toast>
```

```CSharp
ToastContent content = new ToastContent()
{
    Launch = "app-defined-string",
 
    Visual = new ToastVisual()
    {
        BindingGeneric = new ToastBindingGeneric()
        {
            Children =
            {
                new AdaptiveText()
                {
                    Text = "Microsoft Company Store"
                },
 
                new AdaptiveText()
                {
                    Text = "New Halo game is back in stock!"
                }
            }
        }
    },
 
    Actions = new ToastActionsCustom()
    {
        Buttons =
        {
            new ToastButton("See more details", "details"),
 
            new ToastButton("Remind me later", "later")
            {
                ActivationType = ToastActivationType.Background
            }
        }
    }
};
```

![Benachrichtigung mit Aktionen, Beispiel 1](images/adaptivetoasts-xmlsample02.jpg)

 

**Benachrichtigung mit Aktionen, Beispiel 2**

Dieses Beispiel zeigt Folgendes:

```XML
<toast launch="app-defined-string">
  <visual>
    <binding template="ToastGeneric">
      <text>Restaurant suggestion...</text>
      <text>We noticed that you are near Wasaki. Thomas left a 5 star rating after his last visit, do you want to try it?</text>
    </binding>
  </visual>
  <actions>
    <action activationType="foreground" content="Reviews" arguments="reviews" />
    <action activationType="protocol" content="Show map" arguments="bingmaps:?q=sushi" />
  </actions>
</toast>
```

```CSharp
ToastContent content = new ToastContent()
{
    Launch = "app-defined-string",
 
    Visual = new ToastVisual()
    {
        BindingGeneric = new ToastBindingGeneric()
        {
            Children =
            {
                new AdaptiveText()
                {
                    Text = "Restaurant suggestion..."
                },
 
                new AdaptiveText()
                {
                    Text = "We noticed that you are near Wasaki. Thomas left a 5 star rating after his last visit, do you want to try it?"
                }
            }
        }
    },
 
    Actions = new ToastActionsCustom()
    {
        Buttons =
        {
            new ToastButton("Reviews", "reviews"),
 
            new ToastButton("Show map", "bingmaps:?q=sushi")
            {
                ActivationType = ToastActivationType.Protocol
            }
        }
    }
};
```

![Benachrichtigung mit Aktionen, Beispiel 2](images/adaptivetoasts-xmlsample03.jpg)

 

**Benachrichtigung mit Texteingabe und Aktionen, Beispiel 1**

Dieses Beispiel zeigt Folgendes:

```XML
<toast launch="developer-defined-string">
  <visual>
    <binding template="ToastGeneric">
      <text>Andrew B.</text>
      <text>Shall we meet up at 8?</text>
      <image placement="appLogoOverride" src="https://unsplash.it/64?image=883" hint-crop="circle" />
    </binding>
  </visual>
  <actions>
    <input id="message" type="text" placeHolderContent="Type a reply" />
    <action activationType="background" content="Reply" arguments="reply" />
    <action activationType="foreground" content="Video call" arguments="video" />
  </actions>
</toast>
```

```CSharp
ToastContent content = new ToastContent()
{
    Launch = "app-defined-string",
 
    Visual = new ToastVisual()
    {
        BindingGeneric = new ToastBindingGeneric()
        {
            Children =
            {
                new AdaptiveText()
                {
                    Text = "Andrew B."
                },
 
                new AdaptiveText()
                {
                    Text = "Shall we meet up at 8?"
                }
            },
 
            AppLogoOverride = new ToastGenericAppLogo()
            {
                Source = "https://unsplash.it/64?image=883",
                HintCrop = ToastGenericAppLogoCrop.Circle
            }
        }
    },
 
    Actions = new ToastActionsCustom()
    {
        Inputs =
        {
            new ToastTextBox("message")
            {
                PlaceholderContent = "Type a reply"
            }
        },
 
        Buttons =
        {
            new ToastButton("Reply", "reply")
            {
                ActivationType = ToastActivationType.Background
            },
 
            new ToastButton("Video call", "video")
            {
                ActivationType = ToastActivationType.Foreground
            }
        }
    }
};
```

![Benachrichtigung mit Texteingabe und Aktionen](images/adaptivetoasts-xmlsample04.jpg)

 

**Benachrichtigung mit Texteingabe und Aktionen, Beispiel 2**

Dieses Beispiel zeigt Folgendes:

```XML
<toast launch="developer-defined-string">
  <visual>
    <binding template="ToastGeneric">
      <text>Andrew B.</text>
      <text>Shall we meet up at 8?</text>
      <image placement="appLogoOverride" src="https://unsplash.it/64?image=883" hint-crop="circle" />
    </binding>
  </visual>
  <actions>
    <input id="message" type="text" placeHolderContent="Type a reply" />
    <action activationType="background" content="Reply" arguments="reply" hint-inputId="message" imageUri="Assets/Icons/send.png"/>
  </actions>
</toast>
```

```CSharp
ToastContent content = new ToastContent()
{
    Launch = "app-defined-string",
 
    Visual = new ToastVisual()
    {
        BindingGeneric = new ToastBindingGeneric()
        {
            Children =
            {
                new AdaptiveText()
                {
                    Text = "Andrew B."
                },
 
                new AdaptiveText()
                {
                    Text = "Shall we meet up at 8?"
                }
            },
 
            AppLogoOverride = new ToastGenericAppLogo()
            {
                Source = "https://unsplash.it/64?image=883",
                HintCrop = ToastGenericAppLogoCrop.Circle
            }
        }
    },
 
    Actions = new ToastActionsCustom()
    {
        Inputs =
        {
            new ToastTextBox("message")
            {
                PlaceholderContent = "Type a reply"
            }
        },
 
        Buttons =
        {
            new ToastButton("Reply", "reply")
            {
                TextBoxId = "message",
                ImageUri = "Assets/Icons/send.png",
                ActivationType = ToastActivationType.Background
            }
        }
    }
};
```

![Benachrichtigung mit Texteingabe und Aktionen](images/adaptivetoasts-xmlsample05.jpg)

 

**Benachrichtigung mit Auswahleingabe und Aktionen**

Dieses Beispiel zeigt Folgendes:

```XML
<toast launch="developer-defined-string">
  <visual>
    <binding template="ToastGeneric">
      <text>Spicy Heaven</text>
      <text>When do you plan to come in tomorrow?</text>
    </binding>
  </visual>
  <actions>
    <input id="time" type="selection" defaultInput="2" >
      <selection id="1" content="Breakfast" />
      <selection id="2" content="Lunch" />
      <selection id="3" content="Dinner" />
    </input>
    <action activationType="background" content="Reserve" arguments="reserve" />
    <action activationType="foreground" content="Call Restaurant" arguments="call" />
  </actions>
</toast>
```

```CSharp
ToastContent content = new ToastContent()
{
    Launch = "app-defined-string",
 
    Visual = new ToastVisual()
    {
        BindingGeneric = new ToastBindingGeneric()
        {
            Children =
            {
                new AdaptiveText()
                {
                    Text = "Spicy Heaven"
                },
 
                new AdaptiveText()
                {
                    Text = "When do you plan to come in tomorrow?"
                }
            }
        }
    },
 
    Actions = new ToastActionsCustom()
    {
        Inputs =
        {
            new ToastSelectionBox("time")
            {
                DefaultSelectionBoxItemId = "2",
                Items =
                {
                    new ToastSelectionBoxItem("1", "Breakfast"),
                    new ToastSelectionBoxItem("2", "Lunch"),
                    new ToastSelectionBoxItem("3", "Dinner")
                }
            }
        },
 
        Buttons =
        {
            new ToastButton("Reserve", "reserve")
            {
                ActivationType = ToastActivationType.Background
            },
 
            new ToastButton("Call Restaurant", "call")
            {
                ActivationType = ToastActivationType.Foreground
            }
        }
    }
};
```

![Benachrichtigung mit Auswahleingabe und Aktionen](images/adaptivetoasts-xmlsample06.jpg)

 

**Erinnerungsbenachrichtigung**

Dieses Beispiel zeigt Folgendes:

```XML
<toast scenario="reminder" launch="action=viewEvent&amp;eventId=1983">
   
  <visual>
    <binding template="ToastGeneric">
      <text>Adaptive Tiles Meeting</text>
      <text>Conf Room 2001 / Building 135</text>
      <text>10:00 AM - 10:30 AM</text>
    </binding>
  </visual>
 
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

```CSharp
ToastContent content = new ToastContent()
{
    Launch = "action=viewEvent&eventId=1983",
    Scenario = ToastScenario.Reminder,
 
    Visual = new ToastVisual()
    {
        BindingGeneric = new ToastBindingGeneric()
        {
            Children =
            {
                new AdaptiveText()
                {
                    Text = "Adaptive Tiles Meeting"
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
    },
 
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

![Erinnerungsbenachrichtigung](images/adaptivetoasts-xmlsample07.jpg)

 

## <a name="handling-activation-foreground-and-background"></a>Behandeln der Aktivierung (Vordergrund und Hintergrund)

Informationen zum Behandeln von Popupaktivierungen (wenn der Benutzer auf das Popup oder auf Schaltflächen im Popup klickt) finden Sie unter [Schnellstart: Senden einer lokalen Popupbenachrichtigung und Behandeln der Aktivierung](https://blogs.msdn.microsoft.com/tiles_and_toasts/2015/07/08/quickstart-sending-a-local-toast-notification-and-handling-activations-from-it-windows-10/).


## <a name="schemas-ltvisualgt-and-ltaudiogt"></a>Schemas: &lt;visual&gt; und &lt;audio&gt;


In den folgenden XML-Schemas bedeutet das Suffix „?“, dass ein Attribut optional ist.

```
<toast launch? duration? activationType? scenario? >
  <visual lang? baseUri? addImageQuery? >
    <binding template? lang? baseUri? addImageQuery? >
      <text lang? hint-maxLines? >content</text>
      <image src placement? alt? addImageQuery? hint-crop? />
      <group>
        <subgroup hint-weight? hint-textStacking? >
          <text />
          <image />
        </subgroup>
      </group>
    </binding>
  </visual>
  <audio src? loop? silent? />
</toast>
```

```
ToastContent content = new ToastContent()
{
    Launch = ?,
    Duration = ?,
    ActivationType = ?,
    Scenario = ?,
 
    Visual = new ToastVisual()
    {
        Language = ?,
        BaseUri = ?,
        AddImageQuery = ?,
        BindingGeneric = new ToastBindingGeneric()
        {
            Children =
            {
                new AdaptiveText()
                {
                    Text = ?,
                    Language = ?,
                    HintMaxLines = ?
                },
 
                new AdaptiveGroup()
                {
                    Children =
                    {
                        new AdaptiveSubgroup()
                        {
                            HintWeight = ?,
                            HintTextStacking = ?,
                            Children =
                            {
                                new AdaptiveText(),
                                new AdaptiveImage()
                            }
                        }
                    }
                },
 
                new AdaptiveImage()
                {
                    Source = ?,
                    AddImageQuery = ?,
                    AlternateText = ?,
                    HintCrop = ?
                }
            }
        }
    },
 
    Audio = new ToastAudio()
    {
        Src = ?,
        Loop = ?,
        Silent = ?
    }
};
```

**Attribute in &lt;toast&gt;**

launch?

-   launch? = string
-   Dies ist ein optionales Attribut.
-   Eine Zeichenfolge wird an die Anwendung übergeben, wenn sie durch das Popup aktiviert wird.
-   Abhängig vom Wert für „activationType“ kann dieser Wert von der App im Vordergrund, innerhalb der Hintergrundaufgabe oder von einer anderen App empfangen werden, die per Protokollstart über die ursprüngliche App gestartet wird.
-   Das Format und der Inhalt dieser Zeichenfolge werden von der App für eigene Zwecke definiert.
-   Wenn der Benutzer zum Starten der zugeordneten App auf das Popup tippt oder klickt, stellt die Startzeichenfolge der App den Kontext bereit, um dem Benutzer eine Ansicht passend zum Popupinhalt zu ermöglichen, anstatt sie in der Standardgröße starten.
-   Ist die Aktivierung erfolgt, weil der Benutzer auf eine Aktion statt auf den Popuptext geklickt hat, erhält der Entwickler die vordefinierten „Argumente“ in diesem &lt;action&gt;-Tag zurück, statt des vordefinierten „launch“ im &lt;toast&gt;-Tag.

duration?

-   duration? = "short|long"
-   Dies ist ein optionales Attribut. Der Standardwert lautet „kurz“.
-   Es dient nur für bestimmte Szenarien und appCompat. Im Alarmszenario wird es nicht mehr benötigt.
-   Die Verwendung dieser Eigenschaft wird nicht empfohlen.

activationType?

-   activationType? = "foreground | background | protocol | system"
-   Dies ist ein optionales Attribut.
-   Der Standardwert lautet „foreground“

scenario?

-   scenario? = "default | alarm | reminder | incomingCall"
-   Dies ist ein optionales Attribut, der Standardwert lautet „default“.
-   Sie benötigen es nur, wenn es sich bei Ihrem Szenario um einen Alarm, eine Erinnerung oder einen eingehenden Anruf handelt.
-   Verwenden Sie es nicht, um die Benachrichtigung dauerhaft auf dem Bildschirm anzuzeigen.

**Attribute in &lt;visual&gt;**

lang?

-   In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230847) finden Sie ausführliche Informationen zu diesem optionalen Attribut.

baseUri?

-   In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230847) finden Sie ausführliche Informationen zu diesem optionalen Attribut.

addImageQuery?

-   In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230847) finden Sie ausführliche Informationen zu diesem optionalen Attribut.

**Attribute in &lt;binding&gt;**

template?

-   \[Important\] template? = "ToastGeneric"
-   Wenn Sie eines der neuen Features für adaptive und interaktive Benachrichtigungen verwenden, stellen Sie sicher, dass Sie mit der Vorlage „ToastGeneric“ statt mit der Legacyvorlage beginnen.
-   Möglicherweise können Sie die Legacyvorlagen mit den neuen Aktionen verwenden, aber da dies nicht der gewünschte Anwendungsfall ist, können wir keinen Erfolg garantieren.

lang?

-   In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230847) finden Sie ausführliche Informationen zu diesem optionalen Attribut.

baseUri?

-   In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230847) finden Sie ausführliche Informationen zu diesem optionalen Attribut.

addImageQuery?

-   In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230847) finden Sie ausführliche Informationen zu diesem optionalen Attribut.

**Attribute in &lt;text&gt;**

lang?

-   In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230847) finden Sie ausführliche Informationen zu diesem optionalen Attribut.

**Attribute in &lt;image&gt;**

src

-   In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230844) finden Sie ausführliche Informationen zu diesem erforderlichen Attribut.

placement?

-   placement? = "inline" | "appLogoOverride"
-   Dieses Attribut ist optional.
-   Es bestimmt, wo dieses Bild angezeigt wird.
-   „inline“ bedeutet innerhalb des Popuptextes, unter dem Text; „appLogoOverride“ steht für das Ersetzen des Anwendungssymbols (das in der oberen linken Ecke des Popups angezeigt wird).
-   Für jeden Platzierungswert ist maximal ein Bild möglich.

alt?

-   In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230844) finden Sie ausführliche Informationen zu diesem optionalen Attribut.

addImageQuery?

-   In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230844) finden Sie ausführliche Informationen zu diesem optionalen Attribut.

hint-crop?

-   hint-crop? = "none" | "circle"
-   Dieses Attribut ist optional.
-   „none“ ist der Standardwert, sodass kein Zuschneiden möglich ist.
-   „circle“ schneidet das Bild in Kreisform. Verwenden Sie diese Option für Profilbilder eines Kontakts, Bilder einer Person usw.

**Attribute in &lt;audio&gt;**

src?

-   In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230842) finden Sie ausführliche Informationen zu diesem optionalen Attribut.

loop?

-   In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230842) finden Sie ausführliche Informationen zu diesem optionalen Attribut.

silent?

-   In [diesem Artikel zu Elementschemas](https://msdn.microsoft.com/library/windows/apps/br230842) finden Sie ausführliche Informationen zu diesem optionalen Attribut.

## <a name="schemas-ltactiongt"></a>Schemas: &lt;action&gt;


In den folgenden XML-Schemas bedeutet das Suffix „?“, dass ein Attribut optional ist.

```
<toast>
  <visual>
  </visual>
  <audio />
  <actions>
    <input id type title? placeHolderContent? defaultInput? >
      <selection id content />
    </input>
    <action content arguments activationType? imageUri? hint-inputId />
  </actions>
</toast>
```

```
ToastContent content = new ToastContent()
{
    Visual = ...
 
    Actions = new ToastActionsCustom()
    {
        Inputs =
        {
            new ToastSelectionBox("id")
            {
                Title = ?
                DefaultSelectionBoxItemId = ?,
                Items =
                {
                    new ToastSelectionBoxItem("id", "content")
                }
            },
 
            new ToastTextBox("id")
            {
                Title = ?,
                PlaceholderContent = ?,
                DefaultInput = ?
            }
        },
 
        Buttons =
        {
            new ToastButton("content", "args")
            {
                ActivationType = ?,
                ImageUri = ?,
                TextBoxId = ?
            },
 
            new ToastButtonSnooze("content")
            {
                SelectionBoxId = "snoozeTime"
            },
 
            new ToastButtonDismiss("content")
        }
    }
};
```

**Attribute in &lt;input&gt;**

id

-   id = string
-   Dieses Attribut ist erforderlich.
-   Das id-Attribut ist erforderlich und wird von Entwicklern verwendet, um Eingaben des Benutzers abzurufen, sobald die App (im Vordergrund oder im Hintergrund) aktiviert ist.

type

-   type = "text | selection"
-   Dieses Attribut ist erforderlich.
-   Damit wird eine Texteingabe oder Eingabe aus einer Liste von vordefinierten Optionen angegeben.
-   Auf Mobilgeräten und Desktops wird damit angegeben, ob eine Eingabe per Textfeld oder per Listenfeld erfolgen soll.

title?

-   title? = string
-   Das Title-Attribut ist optional. Entwickler können damit einen Titel für die Eingabe festlegen, damit Shells gerendert werden können.
-   Auf Mobilgeräten und Desktops wird dieser Titel über der Eingabe angezeigt.

placeHolderContent?

-   placeHolderContent? = string
-   Das Attribut „placeHolderContent“ ist optional und der ausgegraute Hinweistext für den Texteingabetyp. Dieses Attribut wird ignoriert, wenn der Eingabetyp nicht „text“ lautet.

defaultInput?

-   defaultInput? = string
-   Das Attribut „defaultInput“ ist optional und wird verwendet, um einen Standardeingabewert bereitzustellen.
-   Beim Eingabetyp „text“ wird dieser als Zeichenfolgeneingabe behandelt.
-   Lautet der Eingabetyp „selection“, wird angenommen, dass dieser die ID einer der verfügbaren Auswahl in diesen Eingabeelementen ist.

**Attribute in &lt;selection&gt;**

id

-   Dieses Attribut ist erforderlich. Hiermit wird die Auswahl des Benutzers ermittelt. Die ID wird an Ihre App zurückgegeben.

content

-   Dieses Attribut ist erforderlich. Es enthält die Zeichenfolge, die für dieses Auswahlelement angezeigt werden soll.

**Attribute in &lt;action&gt;**

content

-   content = string
-   Das Inhaltsattribut ist erforderlich. Es enthält die Textzeichenfolge, die auf der Schaltfläche angezeigt wird.

arguments

-   arguments = string
-   Die Argument-Attribut ist erforderlich. Es beschreibt die von der App definierten Daten, die die App später abrufen kann, nachdem sie vom Benutzer durch diese Aktion aktiviert wird.

activationType?

-   activationType? = "foreground | background | protocol | system"
-   Das Attribut „activationType“ ist optional und der Standardwert lautet „foreground“.
-   Es beschreibt die Art der Aktivierung, die diese Aktion auslöst: im Vordergrund, im Hintergrund, Starten einer anderen App über Protokollstart oder Aufrufen einer Systemaktion.

imageUri?

-   imageUri? = string
-   ImageUri ist optional und wird verwendet, um ein Bildsymbol für diese Aktion bereitzustellen, welches auf der Schaltfläche im Textkontext angezeigt wird.

hint-inputId

-   hint-inputId = string
-   Das hint-inpudId-Attribut ist erforderlich. Es wird speziell für das schnelle Beantworten einer Nachricht verwendet.
-   Der Wert muss der ID entsprechen, die dem Eingabeelement zugeordnet werden soll.
-   Auf Mobilgeräten und Desktops wird die Schaltfläche rechts neben dem Eingabefeld platziert.

## <a name="attributes-for-system-handled-actions"></a>Attribute für systemgesteuerte Aktionen


Das System kann Aktionen für die Funktionen zum erneuen Erinnern und zum Schließen von Benachrichtigungen auslösen, wenn Sie nicht wünschen, dass Ihre App das erneute Erinnern/Neuplanen von Benachrichtigungen im Hintergrund ausführt. Systemgesteuerte Aktionen können kombiniert (oder einzeln festgelegt) werden. Wir raten jedoch davon ab, eine erneute Erinnerung ohne Möglichkeit zum Schließen zu implementieren.

Kombinationsfeld für Systembefehle: SnoozeAndDismiss

```
<toast>
  <visual>
  </visual>
  <actions hint-systemCommands="SnoozeAndDismiss" />
</toast>
```

```
ToastContent content = new ToastContent()
{
    Visual = ...
 
    Actions = new ToastActionsSnoozeAndDismiss()
};
```

Einzelne systemgesteuerte Aktionen

```
<toast>
  <visual>
  </visual>
  <actions>
  <input id="snoozeTime" type="selection" defaultInput="10">
    <selection id="5" content="5 minutes" />
    <selection id="10" content="10 minutes" />
    <selection id="20" content="20 minutes" />
    <selection id="30" content="30 minutes" />
    <selection id="60" content="1 hour" />
  </input>
  <action activationType="system" arguments="snooze" hint-inputId="snoozeTime" content=""/>
  <action activationType="system" arguments="dismiss" content=""/>
  </actions>
</toast>
```

```
ToastContent content = new ToastContent()
{
    Visual = ...
 
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
                    new ToastSelectionBoxItem("10", "10 minutes"),
                    new ToastSelectionBoxItem("20", "20 minutes"),
                    new ToastSelectionBoxItem("30", "30 minutes"),
                    new ToastSelectionBoxItem("60", "1 hour")
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

Gehen Sie wie folgt vor, um individuelle Aktionen zum erneuten Erinnern und Schließen zu erstellen:

-   Legen Sie Folgendes fest: activationType = "system"
-   Legen Sie Argumente fest = "snooze" | "dismiss"
-   Legen Sie Inhalt fest:
    -   Wenn Sie wünschen, dass lokalisierte Zeichenfolgen für „snooze“ und „dismiss“ in den Aktionen angezeigt werden, legen Sie den Inhalt als leere Zeichenfolge fest: &lt;action content = ""/&gt;
    -   Wenn Sie eine benutzerdefinierte Zeichenfolge wünschen, geben Sie seinen Wert an: &lt;action content="Erinnere mich später" /&gt;
-   Legen Sie Eingaben fest:
    -   Wenn Sie nicht möchten, dass der Benutzer ein Intervall für das erneute Erinnern auswählen kann, sondern das erneute Erinnern an die Benachrichtigung nur einmal in einem vom System definierten (in allen Betriebssystemen einheitlichen) Zeitintervall erfolgt, legen Sie keinen Wert für &lt;input&gt; fest.
    -   Wenn Sie mögliche Intervalle für das erneute Erinnern bereitstellen möchten:
        -   Gegen Sie „hint-inputId“ in der Aktion für das erneute Erinnerung an.
        -   Stimmen Sie die ID der Eingabe auf den Wert für „hint-inputId“ der Aktion für das erneute Erinnern ab: &lt;input id="snoozeTime"&gt;&lt;/input&gt;&lt;action hint-inputId="snoozeTime"/&gt;
        -   Legen Sie für die Auswahl-ID eine positive ganze Zahl (nonNegativeInteger) fest, die dem Intervall für das erneute Erinnern in Minuten entspricht: &lt;selection id="240" /&gt; bedeutet, dass die erneute Erinnerung in vier Stunden erfolgt.
        -   Stellen Sie sicher, dass der Wert für „defaultInput“ in &lt;input&gt; einer der IDs der untergeordneten &lt;selection&gt; -Elemente entspricht.
        -   Sie können bis zu (jedoch nicht mehr als) 5 &lt;selection&gt;-Werte bereitstellen

 

 
## <a name="related-topics"></a>Verwandte Themen

* [Schnellstart: Senden einer lokalen Popupbenachrichtigung und Behandeln der Aktivierung](http://blogs.msdn.com/b/tiles_and_toasts/archive/2015/07/08/quickstart-sending-a-local-toast-notification-and-handling-activations-from-it-windows-10.aspx)
* [Benachrichtigungsbibliothek auf GitHub](https://github.com/Microsoft/UWPCommunityToolkit/tree/dev/Notifications)


<!--HONumber=Dec16_HO1-->


