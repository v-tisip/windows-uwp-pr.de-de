---
title: Behandeln der URI-Aktivierung
description: Erfahren Sie, wie Sie eine App registrieren, damit sie der Standardhandler eines Uniform Resource Identifier (URI)-Schemanamens wird.
ms.assetid: 92D06F3E-C8F3-42E0-A476-7E94FD14B2BE
ms.date: 07/05/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: aaaf7e6b13a3ce05bd30dd0ebf3e1d7d98915d6e
ms.sourcegitcommit: 89ff8ff88ef58f4fe6d3b1368fe94f62e59118ad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/29/2018
ms.locfileid: "8217993"
---
# <a name="handle-uri-activation"></a>Behandeln der URI-Aktivierung

**Wichtige APIs**

-   [**Windows.ApplicationModel.Activation.ProtocolActivatedEventArgs**](https://msdn.microsoft.com/library/windows/apps/br224742)
-   [**Windows.UI.Xaml.Application.OnActivated**](https://msdn.microsoft.com/library/windows/apps/br242330)

Erfahren Sie, wie Sie eine App registrieren müssen, damit sie der Standardhandler eines URI-Schemanamens (Uniform Resource Identifier) wird. Windows-Desktop-Apps und UWP (Universelle Windows-Plattform)-Apps können als Standarddateihandler für URI-Schemanamen registriert werden. Wenn Ihre App vom Benutzer als Standardhandler für einen URI-Schemanamen ausgewählt wird, wird sie immer dann aktiviert, wenn dieser URI-Typ gestartet wird.

Wir empfehlen, die Registrierung für einen URI-Schemanamen nur durchzuführen, wenn davon auszugehen ist, dass Sie alle entsprechenden Vorgänge für diesen URI-Schematyp behandeln werden. Wenn Sie sich entscheiden, die Registrierung für einen bestimmten URI-Schemanamen durchzuführen, müssen Sie die entsprechenden Funktionen bereitstellen, die vom Benutzer bei der Aktivierung für dieses URI-Schemas erwartet werden. Beispielsweise sollte eine App, die für den URI-Schemanamen "mailto:" registriert wird, eine neue E-Mail-Nachricht öffnen, damit Benutzer eine neue E-Mail erstellen können. Weitere Informationen zu URI-Zuordnungen finden Sie unter [Richtlinien und Prüflisten für Dateitypen und URIs](https://msdn.microsoft.com/library/windows/apps/hh700321).

Die folgenden Schritte zeigen, wie Sie den benutzerdefinierten Schemanamen `alsdk://` registrieren und Ihre App aktivieren, wenn der Benutzer einen URI vom Typ `alsdk://` startet.

> [!NOTE]
> In UWP-Apps sind bestimmte URIs und Dateierweiterungen für die Verwendung durch vorinstallierte Apps und das Betriebssystem reserviert. Versuche, die App mit einem reservierten URI oder einer reservierten Dateierweiterung zu registrieren, werden ignoriert. Eine alphabetische Liste der URI-Schemas, die Sie nicht für Ihre UWP-Apps registrieren können, da diese entweder reserviert oder verboten sind, finden Sie unter [Reservierte URI-Schemanamen und Dateitypen](reserved-uri-scheme-names.md).

## <a name="step-1-specify-the-extension-point-in-the-package-manifest"></a>Schritt 1: Angeben des Erweiterungspunkts im Paketmanifest

Die App empfängt nur für die im Paketmanifest angegebenen URI-Schemanamen Aktivierungsereignisse. Im Folgenden wird beschrieben, wie Sie festlegen, dass die App den URI-Schemanamen `alsdk` behandelt.

1. Doppelklicken Sie im **Projektmappen-Explorer** auf „package.appxmanifest“, um den Manifest-Designer zu öffnen. Wählen Sie die Registerkarte **Deklarationen** und in der Dropdownliste **Verfügbare Deklarationen** die Option **Protokoll** aus, und klicken Sie dann auf **Hinzufügen**.

    Es folgt eine kurze Beschreibung der einzelnen Felder, die Sie im Manifest-Designer für das Protokoll ausfüllen können (Einzelheiten finden Sie unter [**AppX Package Manifest**](https://msdn.microsoft.com/library/windows/apps/dn934791)):

| Feld | Beschreibung |
|-------|-------------|
| **Logo** | Geben Sie das Logo zur Identifikation des URI-Schemanamens in der **Systemsteuerung** unter [Standardprogramme festlegen](https://msdn.microsoft.com/library/windows/desktop/cc144154) an. Wenn kein Logo angegeben wird, wird das kleine Logo für die App verwendet. |
| **Anzeigename** | Geben Sie den Anzeigenamen zur Identifikation des URI-Schemanamens in der **Systemsteuerung** unter [Standardprogramme festlegen](https://msdn.microsoft.com/library/windows/desktop/cc144154) an. |
| **Name** | Wählen Sie einen Namen für das URI-Schema aus. |
|  | **Hinweis**  Der Name darf nur aus Kleinbuchstaben bestehen. |
|  | **Reservierte und verbotene Dateitypen** Eine alphabetische Liste der URI-Schemas, die Sie nicht für Ihre UWP-Apps registrieren können, da diese entweder reserviert oder verboten sind, finden Sie unter [Reservierte URI-Schemanamen und Dateitypen](reserved-uri-scheme-names.md). |
| **Ausführbare Datei** | Gibt die standardmäßige ausführbare Datei für den Start des Protokolls an. Wenn keine Datei angegeben wird, wird die ausführbare Datei der App verwendet. Wenn angegeben, muss die Zeichenfolge zwischen 1 und 256 Zeichen lang sein und mit „.exe“ enden. Sie darf die folgenden Zeichen nicht enthalten: &gt;, &lt;, :, ", &#124;, ? oder \*. Bei Angabe einer Datei wird auch der **Einstiegspunkt** verwendet. Wenn der **Einstiegspunkt** nicht angegeben wird, wird der für die App definierte Einstiegspunkt verwendet. |
| **Einstiegspunkt** | Gibt die Aufgabe an, die die Protokollerweiterung behandelt. Dies ist normalerweise der vollständig qualifizierte Namespacename eines Windows-Runtime-Typs. Wenn keine Angabe erfolgt, wird der Einstiegspunkt für die App verwendet. |
| **Startseite** | Die Webseite, die den Erweiterungspunkt behandelt. |
| **Ressourcengruppe** | Eine Markierung, die Sie zum Gruppieren von Erweiterungsaktivierungen zu Zwecken der Ressourcenverwaltung verwenden können. |
| **Gewünschte Ansicht** (nur Windows) | Verwenden Sie das Feld **Gewünschte Ansicht**, um anzugeben, wie viel Platz für das Fenster der App benötigt wird, wenn sie für den URI-Schemanamen gestartet wird. Die möglichen Werte für **Gewünschte Ansicht** sind **Default**, **UseLess**, **UseHalf**, **UseMore** oder **UseMinimum**.<br/>**Hinweis**  Windows bestimmt die endgültige Fenstergröße einer Ziel-App anhand mehrerer Faktoren, z.B. der Einstellung der Quell-App, der Anzahl der Apps auf dem Bildschirm, der Bildschirmausrichtung usw. Das Festlegen von **Gewünschte Ansicht** ist keine Garantie, dass das Fenster für die Ziel-App auch wirklich so angezeigt wird.<br/>**Mobilgerätfamilie: Gewünschte Ansicht** wird für die Mobilgerätfamilie nicht unterstützt. |

2. Geben Sie `images\Icon.png` als **Logo** ein.
3. Geben Sie `SDK Sample URI Scheme` als **Anzeigenamen** ein.
4. Geben Sie `alsdk` in das Feld **Name** ein.
5. Drücken Sie STRG+S, um die an „package.appxmanifest“ vorgenommenen Änderungen zu speichern.

    Dadurch wird dem Paketmanifest ein [**Extension**](https://msdn.microsoft.com/library/windows/apps/br211400)-Element wie das unten dargestellte hinzugefügt. Die **windows.protocol**-Kategorie gibt an, dass die App den URI-Schemanamen `alsdk` behandelt.

```xml
    <Applications>
        <Application Id= ... >
            <Extensions>
                <uap:Extension Category="windows.protocol">
                  <uap:Protocol Name="alsdk">
                    <uap:Logo>images\icon.png</uap:Logo>
                    <uap:DisplayName>SDK Sample URI Scheme</uap:DisplayName>
                  </uap:Protocol>
                </uap:Extension>
          </Extensions>
          ...
        </Application>
   <Applications>
```

## <a name="step-2-add-the-proper-icons"></a>Schritt 2: Hinzufügen der geeigneten Symbole

Die Symbole von Apps, die für einen URI-Schemanamen zum Standard werden, werden an verschiedenen Stellen innerhalb des Systems angezeigt wie beispielsweise in der Systemsteuerung unter "Standardprogramme". Fügen Sie daher ein 44 x 44-Symbol in das Projekt ein. Stimmen Sie das Erscheinungsbild des Logos der App-Kachel ab, und verwenden Sie die Hintergrundfarbe der App, anstatt das Symbol transparent darzustellen. Erweitern Sie das Logo bis zum Rand, ohne eine Auffüllung vorzunehmen. Testen Sie Ihre Symbole auf weißem Hintergrund. Weitere Einzelheiten zu den Symbolen finden Sie unter [Richtlinien für Kacheln und Symbole](https://docs.microsoft.com/windows/uwp/shell/tiles-and-notifications/app-assets).

## <a name="step-3-handle-the-activated-event"></a>Schritt 3: Behandeln des activated-Ereignisses

Der [**OnActivated**](https://msdn.microsoft.com/library/windows/apps/br242330)-Ereignishandler empfängt alle Aktivierungsereignisse. Die **Kind**-Eigenschaft gibt den Typ des Aktivierungsereignisses an. In diesem Beispiel werden [**Protocol**](https://msdn.microsoft.com/library/windows/apps/xaml/windows.applicationmodel.activation.activationkind.aspx#Protocol)-Aktivierungsereignisse behandelt.

```csharp
public partial class App
{
   protected override void OnActivated(IActivatedEventArgs args)
  {
      if (args.Kind == ActivationKind.Protocol)
      {
         ProtocolActivatedEventArgs eventArgs = args as ProtocolActivatedEventArgs;
         // TODO: Handle URI activation
         // The received URI is eventArgs.Uri.AbsoluteUri
      }
   }
}
```

```vb
Protected Overrides Sub OnActivated(ByVal args As Windows.ApplicationModel.Activation.IActivatedEventArgs)
   If args.Kind = ActivationKind.Protocol Then
      ProtocolActivatedEventArgs eventArgs = args As ProtocolActivatedEventArgs
      
      ' TODO: Handle URI activation
      ' The received URI is eventArgs.Uri.AbsoluteUri
 End If
End Sub
```

```cppwinrt
void App::OnActivated(Windows::ApplicationModel::Activation::IActivatedEventArgs const& args)
{
    if (args.Kind() == Windows::ApplicationModel::Activation::ActivationKind::Protocol)
    {
        auto protocolActivatedEventArgs{ args.as<Windows::ApplicationModel::Activation::ProtocolActivatedEventArgs>() };
        // TODO: Handle URI activation  
        auto receivedURI{ protocolActivatedEventArgs.Uri().RawUri() };
    }
}
```

```cpp
void App::OnActivated(Windows::ApplicationModel::Activation::IActivatedEventArgs^ args)
{
   if (args->Kind == Windows::ApplicationModel::Activation::ActivationKind::Protocol)
   {
      Windows::ApplicationModel::Activation::ProtocolActivatedEventArgs^ eventArgs =
          dynamic_cast<Windows::ApplicationModel::Activation::ProtocolActivatedEventArgs^>(args);
      
      // TODO: Handle URI activation  
      // The received URI is eventArgs->Uri->RawUri
   }
}
```

> [!NOTE]
> Achten Sie darauf, dass beim Start über einen Protokollvertrag der Benutzer über die Zurück-Schaltfläche zu dem Bildschirm zurückkehren muss, von dem aus die App gestartet wurde, und nicht zum vorherigen Inhalt der App.

Im folgende Code wird die App über den URI programmgesteuert gestartet:

```csharp
   // Launch the URI
   var uri = new Uri("alsdk:");
   var success = await Windows.System.Launcher.LaunchUriAsync(uri)
```

Weitere Details zum Starten von Apps mithilfe des URIs finden Sie unter [Starten der Standard-App für einen URI](launch-default-app.md).

Apps sollten für jedes Aktivierungsereignis, durch das eine neue Seite geöffnet wird, einen neuen XAML-[**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682) erstellen. So enthält der Navigationsbackstack für den neuen XAML-**Frame** keinen vorherigen Inhalt, der beim Anhalten der App im aktuellen Fenster angezeigt wurde. Apps, für die ein einziger XAML-**Frame** für Start- und Dateiverträge verwendet wird, sollten vor dem Navigieren zu einer neuen Seite die Seiten im **Frame**-Navigationsjournal löschen.

Per Protokollaktivierung gestartete Apps sollten ggf. eine Benutzeroberfläche enthalten, über die der Benutzer zur ersten Seite der App zurückkehren kann.

## <a name="remarks"></a>Anmerkungen

Ihr URI-Schemaname kann von jeder App oder Website verwendet werden, auch von schädlichen. Alle im URI empfangenen Daten könnten daher von einer nicht vertrauenswürdigen Quelle stammen. Wir empfehlen, niemals eine endgültige Aktion auf Grundlage der Parameter auszuführen, die Sie im URI erhalten. URI-Parameter können z.B. zum Starten der App mit der Kontoseite eines Benutzers, aber nicht zum direkten Ändern des Kontos des Benutzers verwendet werden.

> [!NOTE]
> Wenn Sie für ihre App einen neuen URI-Schemanamen erstellen, ist es wichtig, dass Sie die Ratschläge in [RFC 4395](http://go.microsoft.com/fwlink/p/?LinkID=266550) befolgen. Damit wird sichergestellt, dass Ihr Name die Standards für URI-Schemas erfüllt.

> [!NOTE]
> Achten Sie darauf, dass beim Start über einen Protokollvertrag der Benutzer über die Zurück-Schaltfläche zu dem Bildschirm zurückkehren muss, von dem aus die App gestartet wurde, und nicht zum vorherigen Inhalt der App.

Apps sollten für jedes Aktivierungsereignis, durch das ein neues URI-Ziel geöffnet wird, einen neuen XAML-[**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682) erstellen. So enthält der Navigationsbackstack für den neuen XAML-**Frame** keinen vorherigen Inhalt, der beim Anhalten der App im aktuellen Fenster angezeigt wurde.

Falls Ihre Apps für Start- und Protokollverträge einen einzelnen XAML-[**Frame**](https://msdn.microsoft.com/library/windows/apps/br242682) verwenden sollen, müssen vor dem Navigieren zu einer neuen Seite die Seiten im **Frame**-Navigationsjournal gelöscht werden. Über den Protokollvertrag gestartete Apps sollten ggf. eine Benutzeroberfläche enthalten, über die der Benutzer zum Anfang der App zurückkehren kann.

## <a name="related-topics"></a>Verwandte Themen

### <a name="complete-sample-app"></a>Vollständiges Beispiel-app

- [Beispiel für Assoziationsstart](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/AssociationLaunching)

### <a name="concepts"></a>Konzepte

- [Standardprogramme](https://msdn.microsoft.com/library/windows/desktop/cc144154)
- [Dateityp- und URI-Zuordnungsmodell](https://msdn.microsoft.com/library/windows/desktop/hh848047)

### <a name="tasks"></a>Aufgaben

- [Starten der Standard-App für einen URI](launch-default-app.md)
- [Behandeln der Dateiaktivierung](handle-file-activation.md)

### <a name="guidelines"></a>Richtlinien

- [Richtlinien für Dateitypen und URIs](https://msdn.microsoft.com/library/windows/apps/hh700321)

### <a name="reference"></a>Referenz

- [AppX Package Manifest](https://msdn.microsoft.com/library/windows/apps/dn934791)
- [Windows.ApplicationModel.Activation.ProtocolActivatedEventArgs](https://msdn.microsoft.com/library/windows/apps/br224742)
- [Windows.UI.Xaml.Application.OnActivated](https://msdn.microsoft.com/library/windows/apps/br242330)
