---
author: stevewhims
description: Wir empfehlen dringend, dieses Handbuch für das Portieren vollständig zu lesen. Wir wissen aber auch, dass Sie möglichst schnell die Phase erreichen möchten, in der Ihr Projekt erstellt und ausgeführt wird.
title: Problembehandlung bei der Portierung WindowsPhone Silverlight zu UWP
ms.assetid: d9a9a2a7-9401-4990-a992-4b13887f2661
ms.author: stwhi
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 3a5d3ab7b50721b969859006831b33e9b00e300f
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2018
ms.locfileid: "7167941"
---
#  <a name="troubleshooting-porting-windowsphone-silverlight-to-uwp"></a>Problembehandlung bei der Portierung WindowsPhone Silverlight zu UWP


Im vorherigen Thema ging es um das [Portieren des Projekts](wpsl-to-uwp-porting-to-a-uwp-project.md).

Wir empfehlen dringend, dieses Handbuch für das Portieren vollständig zu lesen. Wir wissen aber auch, dass Sie möglichst schnell die Phase erreichen möchten, in der Ihr Projekt erstellt und ausgeführt wird. Zu diesem Zweck können Sie einen temporären Fortschritt erzielen, indem Sie allen nicht unbedingt erforderlichen Code auskommentieren und anschließend zurückkehren, um die Schulden später zu bezahlen. Die Tabelle mit Symptomen und Möglichkeiten zur Problembehandlung in diesem Thema kann in dieser Phase hilfreich für Sie sein, ersetzt jedoch nicht das Lesen der nächsten Themen. Sie können die Tabelle jederzeit zu Rate ziehen, während Sie die weiteren Themen lesen.

## <a name="tracking-down-issues"></a>Ermitteln von Problemen

XAML-Analyseausnahmen sind uU. schwierig zu diagnostizieren, insbesondere wenn keine sinnvollen Fehlermeldungen innerhalb der Ausnahme vorhanden sind. Stellen Sie sicher, dass der Debugger für die Erfassung von Ausnahmen (erste Chance) konfiguriert ist (um die Analyseausnahme möglichst früh zu erfassen). Möglicherweise können Sie die Ausnahmevariable im Debugger überprüfen, um zu ermitteln, ob das HRESULT oder die Meldung hilfreiche Informationen enthält. Überprüfen Sie auch das Visual Studio-Ausgabefenster auf Fehlermeldungen des XAML-Parsers.

Wenn Ihre app beendet wird, und Sie wissen, dass während der XAML-markupanalyse ein Ausnahmefehler ausgelöst wurde, klicken Sie dann, die möglicherweise ein Verweis auf eine fehlende Ressource (d. h. eine Ressource, deren Schlüssel für WindowsPhone Silverlight-apps jedoch nicht für Windows 10 vorhanden ist Apps, z. B. einige **TextBlock** -Stil Systemschlüsseln). Es kann sich auch um eine Ausnahme handeln, die innerhalb eines **UserControl**-Elements, eines benutzerdefinierten Steuerelements oder eines benutzerdefinierten Layoutpanels ausgelöst wurde.

Als letzte Möglichkeit kann eine Binärdatei aufgeteilt werden. Entfernen Sie etwa die Hälfte des Markups von einer Seite, und führen Sie die App erneut aus. So können Sie feststellen, ob sich der Fehler in der entfernten Hälfte (die Sie jetzt in jedem Fall wiederherstellen sollten) oder in der *nicht* entfernten Hälfte befindet. Wiederholen Sie den Vorgang durch Teilen der Hälfte mit den Fehler solange, Sie das Problem eingegrenzt haben.

## <a name="targetplatformversion"></a>TargetPlatformVersion

In diesem Abschnitt wird erläutert, was Sie tun müssen, wenn auf ein Windows 10-Projekt in Visual Studio öffnen der Meldung "Visual Studio-Update erforderlich. Mindestens ein Projekt erfordert ein Plattform-SDK (&lt;version&gt;), das entweder nicht installiert oder in einem zukünftigen Update von Visual Studio enthalten ist.“

-   Ermitteln Sie zunächst die Versionsnummer des SDK für Windows 10, die Sie installiert haben. Navigieren Sie zu **C:\\Programme (x86)\\Windows Kits\\10\\Include\\&lt;versionfoldername&gt;**, und notieren Sie sich *&lt;versionfoldername&gt;* in der Vierernotation „Hauptversion.Nebenversion.Build.Revision“.
-   Öffnen Sie Ihre Projektdatei zur Bearbeitung, und suchen Sie das `TargetPlatformVersion`-Element und das `TargetPlatformMinVersion`-Element. Bearbeiten Sie sie folgendermaßen: Ersetzen Sie *&lt;versionfoldername&gt;* durch die Versionsnummer in Vierernotation, die Sie auf dem Datenträger gefunden haben:

```xml
   <TargetPlatformVersion><versionfoldername></TargetPlatformVersion>
   <TargetPlatformMinVersion><versionfoldername></TargetPlatformMinVersion>
```

## <a name="troubleshooting-symptoms-and-remedies"></a>Symptome und Möglichkeiten zur Problembehandlung

Die Lösungsinformationen in der Tabelle sollten ausreichen, um Ihr Problem selbst zu behandeln. Weitere Details zu den einzelnen Problemen finden Sie in den späteren Themen.

| Symptom | Abhilfe |
|---------|--------|
| Der XAML-Parser oder -Compiler meldet den Fehler „_Der Name „&lt;typename&gt;“ ist im Namespace „[…]“ nicht vorhanden_“. | Wenn &lt;typename&gt; ein benutzerdefinierter Typ ist, ändern Sie in Ihren Namespace-Präfixdeklarationen im XAML-Markup „clr-namespace“ in „using“, und entfernen Sie alle Assemblytoken. Für Plattformtypen bedeutet dies, dass der Typ nicht für die Universelle Windows-Plattform (UWP) gilt. Suchen Sie also nach der Entsprechung, und aktualisieren Sie Ihr Markup damit. Die Beispiele `phone:PhoneApplicationPage` und `shell:SystemTray.IsVisible` können sofort auftreten. | 
| Der XAML-Parser oder -Compiler meldet den Fehler „_Der Member „&lt;membername&gt;“ wurde nicht erkannt, oder es kann nicht auf den Member zugegriffen werden_“ oder „_Die „&lt;propertyname&gt;“-Eigenschaft wurde in Typ „[…]“ nicht gefunden_“. | Diese Fehler werden angezeigt, nachdem Sie einige Typnamen portiert haben, z.B. das **Page**-Stammelement. Der Member oder die Eigenschaft gilt nicht für die UWP. Suchen Sie also nach der Entsprechung, und aktualisieren Sie Ihr Markup damit. Die Beispiele `SupportedOrientations` und `Orientation` können sofort auftreten. |
| Der XAML-Parser oder -Compiler meldet den Fehler „_Die anfügbare […]-Eigenschaft wurde nicht gefunden […]_“ oder „_Unbekannter verknüpfbarer Member [...]_“. | Dies wird wahrscheinlich durch den Typ und nicht durch die angefügte Eigenschaft verursacht; in diesem Fall tritt bereits ein Fehler für diesen Typ auf, der verschwindet, sobald sie ihn behoben haben. Die Beispiele `phone:PhoneApplicationPage.Resources` und `phone:PhoneApplicationPage.DataContext` können sofort auftreten. | 
|Der XAML-Parser bzw. -Compiler oder eine Laufzeitausnahme meldet den Fehler „_Die Ressource „&lt;resourcekey&gt;“ konnte nicht aufgelöst werden_“. | Der Ressourcenschlüssel gilt nicht für UWP (Universelle Windows-Plattform)-Apps. Suchen Sie nach dem richtigen äquivalenten Ressourcenobjekt, und aktualisieren Sie Ihr Markup. System-**TextBlock**-Stilschlüssel wie `PhoneTextNormalStyle` können sofort auftreten. |
| Der C#-Compiler gibt folgenden Fehler aus: „_Der Typ- oder Namespacename „&lt;name&gt;“ konnte nicht gefunden werden […]_“ oder „_Der Typ- oder Namespacename „&lt;name&gt;“ ist im Namespace […] nicht vorhanden_“ oder „_Der Typ- oder Namespacename „&lt;name&gt;“ ist im aktuellen Kontext nicht vorhanden_“. | Dies bedeutet wahrscheinlich, dass der Compiler den richtigen UWP-Namespace für einen Typ noch nicht kennt. Sie können den Visual Studio-Befehl **Auflösen** verwenden, um dieses Problem zu beheben. <br/>Wenn die API nicht in der Gruppe der APIs enthalten ist, die als Familie der universellen Geräte bezeichnet wird (die API also in einem Erweiterungs-SDK implementiert ist), verwenden Sie die [Erweiterungs-SDKs](wpsl-to-uwp-porting-to-a-uwp-project.md).<br/>Es kann andere Fälle geben, in denen das Portieren weniger einfach ist. Die Beispiele `DesignerProperties` und `BitmapImage` können sofort auftreten. | 
|Wenn auf dem Gerät ausgeführt wird, die app beendet oder in Visual Studio gestartet wird, sehen Sie den Fehler "kann nicht Windows Runtime 8.x-app […] zu aktivieren. Fehler bei der Aktivierungsanforderung: „Windows konnte nicht mit der Zielanwendung kommunizieren.“ Dies weist in der Regel darauf hin, dass der Prozess der Zielanwendung abgebrochen wurde. […]”. | Das Problem ist möglicherweise der imperative Code, der während der Initialisierung auf Ihren eigenen Seiten oder in gebundenen Eigenschaften (oder anderen Typen) ausgeführt wird. Es könnte auch beim Analysieren der XAML-Datei passieren, die angezeigt wird, wenn die App beendet wird (beim Starten in Visual Studio ist dies die Startseite). Suchen Sie nach ungültigen Ressourcenschlüsseln, und/oder probieren Sie einige der Anleitungen im Abschnitt [Ermitteln von Problemen](#tracking-down-issues) in diesem Thema aus.|
| _XamlCompiler-Fehler WMC0055: Der Textwert „&lt;your stream geometry&gt;“ kann nicht für die Clip-Eigenschaft von Typ „RectangleGeometry“ zugewiesen werden._ | In der UWP der Typ der UWP-App mit [Microsoft DirectX](https://msdn.microsoft.com/library/windows/desktop/ee663274) XAML und C++. |
| _XamlCompiler-Fehler WMC0001: Unbekannter Typ „RadialGradientBrush“ im XML-Namespace [...]_ | Die UWP verfügt nicht über den **RadialGradientBrush**-Typ. Entfernen Sie das **RadialGradientBrush**-Element aus dem Markup, und verwenden Sie einen anderen Typ von UWP-App mit [Microsoft DirectX](https://msdn.microsoft.com/library/windows/desktop/ee663274), XAML und C++. |
| _XamlCompiler-Fehler WMC0011: Unbekannter Member „OpacityMask“ in Element „&lt;UIElement type&gt;“_ | Die UWP-App mit [Microsoft DirectX](https://msdn.microsoft.com/library/windows/desktop/ee663274), XAML und C++. |
| _Eine Ausnahme (erste Chance) vom Typ „System.Runtime.InteropServices.COMException“ ist in SYSTEM.NI.DLL aufgetreten. Weitere Informationen: Die Anwendung hat eine Schnittstelle aufgerufen, die für einen anderen Thread gemarshalled wurde. (Ausnahme von HRESULT: 0x8001010E (RPC_E_WRONG_THREAD))._ | Die Schritte, die Sie gerade ausführen, müssen im UI-Thread ausgeführt werden. Rufen Sie den [**CoreWindow.GetForCurrentThread**](https://msdn.microsoft.com/library/windows/apps/hh701589)) auf. |
| Eine Animation wird ausgeführt, hat jedoch keine Auswirkungen auf ihre Zieleigenschaft. | Gestalten Sie die Animation unabhängig, oder legen Sie `EnableDependentAnimation="True"` dafür fest. Siehe [Animation](wpsl-to-uwp-porting-xaml-and-ui.md). |
| Auf einem Windows 10-Projekt in Visual Studio öffnen, sehen Sie die Meldung "Visual Studio-Update erforderlich. Mindestens ein Projekt erfordert ein Plattform-SDK (&lt;version&gt;), das entweder nicht installiert oder in einem zukünftigen Update von Visual Studio enthalten ist.“ | Weitere Informationen finden Sie im Abschnitt [TargetPlatformVersion](#targetplatformversion) in diesem Thema. |
| Wenn in einer XAML.CS-Datei „InitializeComponent“ aufgerufen wird, wird eine „System.InvalidCastException“ ausgelöst. | Dies kann passieren, wenn mehrere XAML-Dateien (mindestens eine davon MRT-qualifiziert) dieselbe XAML.CS-Datei verwenden und Elemente x:Name-Attribute aufweisen, die zwischen den beiden XAML-Dateien inkonsistent sind. Versuchen Sie, den gleichen Elementen in XAML-Dateien denselben Namen hinzuzufügen, oder lassen Sie Namen ganz weg. | 

Das nächste Thema ist [Portieren von XAML und UI](wpsl-to-uwp-porting-xaml-and-ui.md).

