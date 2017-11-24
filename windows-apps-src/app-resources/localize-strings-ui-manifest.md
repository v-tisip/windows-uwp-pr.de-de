---
author: stevewhims
Description: "Wenn Sie möchten, dass Ihre App verschiedene Anzeigesprachen unterstützt, und Ihr Code oder XAML-Markup- oder App-Paketmanifest Zeichenfolgenliterale enthält, verschieben Sie diese Zeichenfolgen in eine Ressourcendatei (.resw). Sie können dann eine übersetzte Kopie dieser Ressourcendatei für jede Sprache erstellen, die Ihre App unterstützt."
title: "Lokalisieren von Zeichenfolgen in der Benutzeroberfläche und im App-Paketmanifest"
ms.assetid: E420B9BB-C0F6-4EC0-BA3A-BA2875B69722
label: Localize strings in your UI and app package manifest
template: detail.hbs
ms.author: stwhi
ms.date: 11/01/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Ressourcen, Bild, Element, MRT, Qualifizierer
localizationpriority: medium
ms.openlocfilehash: cca9c9b731831ce1c87ee74b7f8b502130ef97fd
ms.sourcegitcommit: d0c93d734639bd31f264424ae5b6fead903a951d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2017
---
<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

# <a name="localize-strings-in-your-ui-and-app-package-manifest"></a>Lokalisieren von Zeichenfolgen in der Benutzeroberfläche und im App-Paketmanifest

Weitere Informationen zu einer Werterhöhung Ihrer App durch Lokalisierung finden Sie unter [Globalisierung und Lokalisierung](../globalizing/globalizing-portal.md).

Wenn Sie möchten, dass Ihre App verschiedene Anzeigesprachen unterstützt, sollten Sie Zeichenfolgenliterale, die in Ihrem Code oder XAML-Markup oder App-Paketmanifest enthalten sind, in eine Ressourcendatei (.resw) verschieben. Sie können dann eine übersetzte Kopie dieser Ressourcendatei für jede Sprache erstellen, die Ihre App unterstützt.

Hartcodierte Zeichenfolgenliterale können in imperativem Code oder in XAML-Markup stehen, z.B. die **Text** Eigenschaft für einen **TextBlock**. Sie können auch in Ihrem App-Paketmanifest (die Datei `Package.appxmanifest`) auftreten, z.B. als Wert für den Anzeigenamen auf der Registerkarte „Anwendung” im Manifest-Designer von Visual Studio. Verschieben Sie diese Zeichenfolgen in eine Ressourcendatei (.resw), und ersetzen Sie die hartcodierten Zeichenfolgenliterale in Ihrer App und in Ihrem Manifest durch Verweise auf Ressourcenbezeichner.

Während eine Bildressourcendatei immer nur eine Bildressource enthält, sind in einer Zeichenfolgen-Ressourcendatei *mehrere* Zeichenfolgenressourcen enthalten. Eine Zeichenfolgen-Ressourcendatei ist die Art von Ressourcendatei (.resw), die Sie üblicherweise in einem \Strings-Ordner Ihres Projekts erstellen. Hintergrundinformationen zur Verwendung von Qualifizierern in den Namen von Ressourcendateien (.resw) finden Sie unter [Anpassen von Ressourcen mit Qualifizierern für Sprache, Skalierung und andere Eigenschaften](tailor-resources-lang-scale-contrast.md).

## <a name="create-a-resources-file-resw-and-put-your-strings-in-it"></a>Erstellen einer Ressourcendatei (.resw) und Einfügen von Zeichenfolgen

1. Legen Sie die Standardsprache Ihrer App fest.
    1. Öffnen Sie `Package.appxmanifest`, während Ihre Projektmappe in Visual Studio geöffnet ist.
    2. Vergewissern Sie sich auf der Registerkarte „Anwendung”, dass die Standardsprache passend festgelegt ist (z.B. auf „en” oder „en-US”). Für die verbleibenden Schritte wird davon ausgegangen, dass Sie die Standardsprache auf "en-US" festgelegt haben.
    <br>**Hinweis:** Sie müssen zumindest Zeichenfolgenressourcen in der Standardsprache bereitstellen. Diese Ressourcen werden geladen, wenn für die bevorzugte Sprache des Benutzers oder die eingestellte Anzeigesprache keine bessere Übereinstimmung gefunden wird.
2. Erstellen Sie eine Ressourcendatei (.resw) für die Standardsprache.
    1. Erstellen Sie unter Ihrem Projektknoten einen neuen Ordner mit dem Namen „Strings”.
    2. Erstellen Sie unter `Strings` einen neuen Unterordner mit dem Namen „en-US”.
    3. Erstellen Sie unter `en-US` eine neue Ressourcendatei (.resw). Vergewissern Sie sich, dass sie „Resources.resw” heißt.
    <br>**Hinweis:** Informationen für den Fall, dass Sie vorhandene .NET-Ressourcendateien (.resx) portieren möchten, finden Sie unter [Portieren von XAML und UI](../porting/wpsl-to-uwp-porting-xaml-and-ui.md#localization-and-globalization).
3.  Öffnen Sie `Resources.resw`, und fügen Sie diese Zeichenfolgenressourcen hinzu.

    `Strings/en-US/Resources.resw`

    ![Ressource hinzufügen, Englisch](images/addresource-en-us.png)

    In diesem Beispiel ist „Greeting” der Bezeichner einer Zeichenfolgenressource, auf den Sie, wie noch gezeigt wird, im Markup verweisen können. Für den Bezeichner „Greeting” wird eine Zeichenfolge für eine Text-Eigenschaft bereitgestellt, und es wird eine Zeichenfolge für eine Width-Eigenschaft bereitgestellt. „Greeting.Text” ist ein Beispiel für einen Eigenschaftsbezeichner, da er der Eigenschaft eines Benutzeroberflächenelements entspricht. Es wäre auch möglich, „Greeting.Foreground” in der Spalte „Name” hinzuzufügen, beispielsweise mit dem Wert „Red” in der Spalte „Value”. Der Bezeichner „Farewell” ist ein einfacher Bezeichner für eine Zeichenfolgenressource. Er verfügt über keine untergeordneten Eigenschaften und kann, wie noch gezeigt wird, aus imperativem Code geladen werden. Die Spalte „Kommentar” ist gut geeignet, um spezielle Anweisungen für Übersetzer bereitzustellen.

    Da wir in diesem Beispiel mit „Farewell” einen einfachen Bezeichner für Zeichenfolgenressourcen eingetragen haben, können wir *zusätzlich* keine Eigenschaftsbezeichner verwenden, die auf demselben Bezeichner basieren. Das Hinzufügen von „Farewell.Text” würde deshalb dazu führen, dass beim Erstellen von `Resources.resw` der Fehler „Doppelter Eintrag” auftritt.

## <a name="refer-to-a-string-resource-identifier-from-xaml-markup"></a>Referenzieren eines Bezeichners für Zeichenfolgenressourcen im XAML-Markup

Verwenden Sie eine [x:Uid-Direktive](../xaml-platform/x-uid-directive.md), um ein Steuerelement oder ein anderes Element in Ihrem Markup mit dem Bezeichner einer Zeichenfolgenressource zu verknüpfen.

**XAML**
```xml
<TextBlock x:Uid="Greeting"/>
```

Zur Laufzeit wird `\Strings\en-US\Resources.resw` geladen (da diese momentan die einzige Ressourcendatei im Projekt ist). Die Direktive **x:Uid** im **TextBlock**-Element bewirkt in `Resources.resw` eine Suche nach Eigenschaftsbezeichnern, die den Zeichenfolgenressourcen-Bezeichner „Greeting” enthalten. Die Eigenschaftsbezeichner „Greeting.Text” und „Greeting.Width” werden gefunden, und ihre Werte werden auf den **TextBlock** angewendet, wobei alle Werte, die lokal im Markup festgelegt sind, überschrieben werden. Der Wert „Greeting.Foreground” würde ebenfalls angewendet, wenn Sie ihn hinzugefügt hätten. Es hätte aber keine Auswirkung, wenn Sie in diesem TextBlock-Element **a:Uid** auf „Farewell” festlegen würden, da nur Eigenschaftsbezeichner verwendet werden, um Eigenschaften für XAML-Markupelemente festzulegen. `Resources.resw` „Resources.resw” *enthält zwar* den Zeichenfolgenressourcen-Bezeichner „Farewell”, aber keine zugehörigen Eigenschaftsbezeichner.

Sollten Sie einem XAML-Element einen Zeichenfolgeressourcen-Bezeichner zuordnen, müssen Sie sicherstellen, dass *alle* Eigenschaftsbezeichner für diesen Bezeichner für das XAML-Element geeignet sind. Wenn Sie beispielsweise `x:Uid="Greeting"` in einem **TextBlock**-Element verwenden, wird „Greeting.Text” korrekt zugeordnet, da der Typ **TextBlock** über eine Text-Eigenschaft verfügt. Wenn Sie `x:Uid="Greeting"` aber in einem **Button**-Element verwenden, wird „Greeting.Text” einen Laufzeitfehler verursachen, da der Typ **Button** nicht über eine Texteigenschaft verfügt. Eine Lösung für diesen Fall ist, einen Eigenschaftsbezeichner mit dem Namen "ButtonGreeting.Content" zu erstellen und `x:Uid="ButtonGreeting"` im **Button**-Element zu verwenden.

Statt **Width** mithilfe einer Ressourcendatei festzulegen, können Sie veranlassen, dass sich Steuerelemente in ihrer Größe dynamisch an Inhalte anpassen.

**Hinweis:** Für [angefügte Eigenschaften](../xaml-platform/attached-properties-overview.md) ist eine spezielle Syntax in der Spalte „Name” einer resw-Datei erforderlich. Um beispielsweise einen Wert für die angefügte Eigenschaft [AutomationProperties.Name](/uwp/api/windows.ui.xaml.automation.automationproperties?branch=live#Windows_UI_Xaml_Automation_AutomationProperties_NameProperty) des Bezeichners „Greeting” festzulegen, müssen Sie Folgendes in der Spalte „Name” eingeben:

```
Greeting.[using:Windows.UI.Xaml.Automation]AutomationProperties.Name
```

## <a name="refer-to-a-string-resource-identifier-from-code"></a>Referenzieren eines Bezeichners für Zeichenfolgenressourcen im Code

Sie können eine Zeichenfolgenressource explizit durch Angabe eines einfachen Zeichenfolgenressourcen-Bezeichners laden:

**C#**
```csharp
var resourceLoader = Windows.ApplicationModel.Resources.ResourceLoader.GetForCurrentView();
this.myXAMLTextBlockElement.Text = resourceLoader.GetString("Farewell");
```

**C++**
```cpp
auto resourceLoader = Windows::ApplicationModel::Resources::ResourceLoader::GetForCurrentView();
this->myXAMLTextBlockElement->Text = resourceLoader->GetString("Farewell");
```

Sie können diesen Code in einer Klassenbibliothek (Universal Windows) oder in einem [Windows Runtime Library (Universal Windows)](../winrt-components/index.md)-Projekt verwenden. Zur Laufzeit werden die Ressourcen der App geladen, die die Bibliothek hostet. Wir empfehlen, dass eine Bibliothek Ressourcen aus der App lädt, die sie hostet, da die App wahrscheinlich einen höheren Lokalisierungsgrad aufweist. Wenn eine Bibliothek Ressourcen bereitstellen muss, sollte sie es der App, die sie hostet, ermöglichen, diese Ressourcen als Eingabe zu ersetzen.

**Hinweis:** Sie können den Wert auf diese Weise nur für einen einfachen Zeichenfolgenressourcen-Bezeichner laden, nicht jedoch für einen Eigenschaftsbezeichner. So können Sie mit solchem Code zwar den Wert für „Farewell” laden, nicht aber den für „Greeting.Text”. Wenn Sie es versuchen, wird eine leere Zeichenfolge zurückgegeben.

## <a name="refer-to-a-string-resource-identifier-from-your-app-package-manifest"></a>Verweisen auf einen Ressourcenbezeichner aus dem App-Paketmanifest

1. Öffnen Sie das App-Paketmanifest (die Datei `Package.appxmanifest`). Darin ist der Anzeigenamen Ihrer App standardmäßig als Zeichenfolgenliteral angegeben.

   ![Ressource hinzufügen, Englisch](images/display-name-before.png)

2. Um eine lokalisierbare Version dieser Zeichenfolge zu erstellen, öffnen Sie `Resources.resw` und fügen eine neue Zeichenfolgenressource mit dem Namen „AppDisplayName” und dem Wert „Adventure Works Cycles” hinzu.

3. Ersetzen Sie das Zeichenfolgenliteral für den Anzeigennamen durch einen Verweis auf den Zeichenfolgenressourcen-Bezeichner, den Sie gerade erstellt haben („AppDisplayName”). Verwenden Sie dazu das URI (Uniform Resource Identifier)-Schema `ms-resource`.

   ![Ressource hinzufügen, Englisch](images/display-name-after.png)

4. Wiederholen Sie den Vorgang für alle Zeichenfolgen im Manifest, die Sie lokalisieren möchten. Beispielsweise für den Kurznamen Ihrer App (den Sie so konfigurieren können, dass er im Startmenü auf der App-Kachel angezeigt wird). Eine Liste aller Elemente im App-Paketmanifest, die Sie lokalisieren können, finden Sie unter [Lokalisierbare Manifestelemente](/uwp/schemas/appxpackage/uapmanifestschema/localizable-manifest-items-win10?branch=live).

## <a name="localize-the-string-resources"></a>Lokalisieren der Zeichenfolgenressourcen

1. Erstellen Sie eine Kopie der Ressourcendatei (.resw) für eine andere Sprache.
    1. Erstellen Sie unter „Strings” einen neuen Unterordner, und nennen Sie ihn „de-DE” für Deutsch (Deutschland).
   <br>**Hinweis:** Für den Namen des Ordners können Sie jeden [BCP-47-Sprachtag](http://go.microsoft.com/fwlink/p/?linkid=227302) verwenden. Details zum Sprachqualifizierer und eine Liste häufiger Sprachtags finden Sie unter [Anpassen von Ressourcen mit Qualifizierern für Sprache, Skalierung und anderen](tailor-resources-lang-scale-contrast.md).
   2. Erstellen Sie im Ordner `Strings/de-DE` eine Kopie von `Strings/en-US/Resources.resw`.
2. Übersetzen Sie die Zeichenfolgen.
    1. Öffnen Sie `Strings/de-DE/Resources.resw`, und übersetzen Sie die Werte in der Spalte „Value”. Sie müssen die Kommentare nicht übersetzen.

    `Strings/de-DE/Resources.resw`

    ![Ressource hinzufügen, Deutsch](images/addresource-de-de.png)

Bei Bedarf wiederholen Sie die Schritte 1 und 2 für eine weitere Sprache.

`Strings/fr-FR/Resources.resw`

![Ressource hinzufügen, Französisch](images/addresource-fr-fr.png)

## <a name="test-your-app"></a>Testen der App

Testen Sie die App hinsichtlich der Standardanzeigesprache. Sie können dann die Anzeigesprache in **Einstellungen** > **Zeit & Sprache** > **Region & Sprache** (oder **Sprache**) ändern und die App erneut testen. Beachten Sie Zeichenfolgen in der Benutzeroberfläche und auch in der Shell (z.B. den Anzeigenamen in der Titelleiste und den Kurznamen für Ihre Kacheln).

**Hinweis:** Wenn ein Ordnername gefunden wird, der mit der Einstellung für die Anzeigesprache übereinstimmt, wird die Ressourcendatei in diesem Ordner geladen. Andernfalls erfolgt ein Fallback bis auf die Ressourcen für die standardmäßige Sprache Ihrer App.

## <a name="factoring-strings-into-multiple-resources-files"></a>Verteilen von Zeichenfolgen in mehrere Ressourcendateien

Sie können alle Zeichenfolgen in einer einzelnen Ressourcendatei (resw) zusammenfassen oder sie auf mehrere Ressourcendateien verteilen. Beispielsweise können in einer Ressourcendatei Fehlermeldungen ablegen, die Zeichenfolgen für das App-Paketmanifest in einer anderen, und die Zeichenfolgen für die Benutzeroberfläche in einer dritten Ressourcendatei. In diesem Fall würde die Ordnerstruktur wie folgt aussehen.

![Ressource hinzufügen, Englisch](images/manifest-resources.png)

Um den Verweis auf den Bezeichner einer Zeichenfolgenressource auf eine bestimmte Datei zu beziehen, setzen Sie einfach `/<resources-file-name>/` vor den Bezeichner. Im folgenden Markupbeispiel wird davon ausgegangen, dass `ErrorMessages.resw` eine Ressource mit dem Namen „PasswordTooWeak.Text” enthält, deren Wert einen Fehler beschreibt.

**XAML**
```xml
<TextBlock x:Uid="/ErrorMessages/PasswordTooWeak"/>
```

Im folgenden Codebeispiel wird davon ausgegangen, dass `ErrorMessages.resw` eine Ressource mit dem Namen „MismatchedPasswords” enthält, deren Wert einen Fehler beschreibt.

**C#**
```csharp
var resourceLoader = Windows.ApplicationModel.Resources.ResourceLoader.GetForCurrentView("ManifestResources");
this.myXAMLTextBlockElement.Text = resourceLoader.GetString("/ErrorMessages/MismatchedPasswords");
```

**C++**
```cpp
auto resourceLoader = Windows::ApplicationModel::Resources::ResourceLoader::GetForCurrentView("ManifestResources");
this->myXAMLTextBlockElement->Text = resourceLoader->GetString("/ErrorMessages/MismatchedPasswords");
```

Würden Sie die Ressource „AppDisplayName” aus `Resources.resw` in `ManifestResources.resw` verschieben, müssten Sie in Ihrem App-Paketmanifest `ms-resource:AppDisplayName` in `ms-resource:/ManifestResources/AppDisplayName` ändern.

Für *andere Ressourcendateien* als `Resources.resw` müssen nur `/<resources-file-name>/` vor den Bezeichner für die Zeichenfolgenressource setzten. Der Grund ist, dass „Resources.resw” der Standarddateiname ist, der verwendet wird, wenn Sie keinen Dateinamen angeben (wie in früheren Beispielen in diesem Thema).

## <a name="load-a-string-for-a-specific-language-or-other-context"></a>Laden einer Zeichenfolge für eine bestimmte Sprache oder einen anderen Kontext

Der standardmäßige [**ResourceContext**](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live) (abgerufen über [**ResourceContext.GetForCurrentView**](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live#Windows_ApplicationModel_Resources_Core_ResourceContext_GetForCurrentView)) enthält einen Qualifiziererwert für jeden Qualifizierernamen, der den standardmäßigen Laufzeitkontext darstellt (also die Einstellungen für den aktuellen Benutzer und Computer). Ressourcendateien (.resw) werden anhand der Qualifizierer in ihren Namen mit den Qualifiziererwerten in diesem Laufzeitkontext abgeglichen.

In einigen Fällen wünschen Sie vielleicht, dass Ihre App die Systemeinstellungen überschreiben und Sprache, Skalierung oder andere Qualifiziererwerte explizit angeben kann, wenn sie nach einer passenden Ressourcendatei sucht, um sie zu laden. So könnten Sie es Ihren Benutzern beispielsweise ermöglichen, eine alternative Sprache für QuickInfos oder Fehlermeldungen auszuwählen.

Das ist möglich, indem Sie einen neuen **ResourceContext** erstellen (statt den standardmäßigen Kontext zu verwenden), dessen Werte überschreiben und dann dieses Kontextobjekt bei der Suche nach Zeichenfolgen verwenden.

**C#**
```csharp
var resourceContext = new Windows.ApplicationModel.Resources.Core.ResourceContext(); // not using ResourceContext.GetForCurrentView
resourceContext.QualifierValues["Language"] = "de-DE";
var resourceMap = Windows.ApplicationModel.Resources.Core.ResourceManager.Current.MainResourceMap.GetSubtree("Resources");
this.myXAMLTextBlockElement.Text = resourceMap.GetValue("Farewell", resourceContext).ValueAsString;
```

Wie **QualifierValues** im obigen Codebeispiel kann jeder Qualifizierer verwendet werden. Für den Sonderfall Language können Sie alternativ wie folgt verfahren.

**C#**
```csharp
resourceContext.Languages = new string[] { "de-DE" };
```

Um den gleichen Effekt auf einer globalen Ebene zu erzielen, *könnten* Sie die Qualifiziererwerte im standardmäßigen **ResourceContext** überschreiben. Wir empfehlen, stattdessen [**ResourceContext.SetGlobalQualifierValue**](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live#Windows_ApplicationModel_Resources_Core_ResourceContext_SetGlobalQualifierValue_System_String_System_String_Windows_ApplicationModel_Resources_Core_ResourceQualifierPersistence_) aufzurufen. Wenn Sie Werte einmal mit einem Aufruf von **SetGlobalQualifierValue** festlegen, werden sie bei jedem Suchvorgang mit dem standardmäßigen **ResourceContext** auf diesen angewendet.

**C#**
```csharp
Windows.ApplicationModel.Resources.Core.ResourceContext.SetGlobalQualifierValue("Language", "de-DE");
var resourceLoader = Windows.ApplicationModel.Resources.ResourceLoader.GetForCurrentView();
this.myXAMLTextBlockElement.Text = resourceLoader.GetString("Farewell");
```

Einige Qualifizierer besitzen einen Systemdatenanbieter. Statt **SetGlobalQualifierValue** aufzurufen, können Sie dann den Anbieter über seine eigene API anpassen. Der folgende Code zeigt an einem Beispiel, wie [**PrimaryLanguageOverride**](/uwp/api/Windows.Globalization.ApplicationLanguages?branch=live#Windows_Globalization_ApplicationLanguages_PrimaryLanguageOverride) festzulegen ist.

**C#**
```csharp
Windows.Globalization.ApplicationLanguages.PrimaryLanguageOverride = "de-DE";
```

## <a name="updating-strings-in-response-to-qualifier-value-change-events"></a>Aktualisieren von Zeichenfolgen als Reaktion auf Änderungen von Qualifiziererwerten

Eine aktive App kann auf Änderungen der Systemeinstellungen reagieren, wenn sich diese Änderungen auf Qualifiziererwerte im standardmäßigen **ResourceContext** auswirken. Jede dieser Systemeinstellungen löst das Ereignis [**MapChanged**](/uwp/api/windows.foundation.collections.iobservablemap_k_v_?branch=live#Windows_Foundation_Collections_IObservableMap_2_MapChanged) für [**ResourceContext.QualifierValues**](/uwp/api/windows.applicationmodel.resources.core.resourcecontext?branch=live#Windows_ApplicationModel_Resources_Core_ResourceContext_QualifierValues) aus.

Als Reaktion auf dieses Ereignis können Sie die Zeichenfolgen aus dem standardmäßigen **ResourceContext** laden.

**C#**
```csharp
public MainPage()
{
    this.InitializeComponent();

    ...

    // Subscribe to the event that's raised when a qualifier value changes.
    var qualifierValues = Windows.ApplicationModel.Resources.Core.ResourceContext.GetForCurrentView().QualifierValues;
    qualifierValues.MapChanged += new Windows.Foundation.Collections.MapChangedEventHandler<string, string>(QualifierValues_MapChanged);
}

private async void QualifierValues_MapChanged(IObservableMap<string, string> sender, IMapChangedEventArgs<string> @event)
{
    var dispatcher = this.myXAMLTextBlockElement.Dispatcher;
    if (dispatcher.HasThreadAccess)
    {
        this.RefreshUIText();
    }
    else
    {
        await dispatcher.RunAsync(Windows.UI.Core.CoreDispatcherPriority.Normal, () => this.RefreshUIText());
    }
}

private void RefreshUIText()
{
    var resourceLoader = Windows.ApplicationModel.Resources.ResourceLoader.GetForCurrentView();
    this.myXAMLTextBlockElement.Text = resourceLoader.GetString("Farewell");
}
```

## <a name="loading-strings-from-a-class-library-or-a-windows-runtime-library"></a>Laden von Zeichenfolgen aus einer Klassenbibliothek oder eine Windows-Runtime-Bibliothek

Die Zeichenfolgenressourcen einer referenzierten Klassenbibliothek (Universal Windows) oder [Windows-Runtime Library (Universal Windows)](../winrt-components/index.md) stehen in der Regel in einem Unterordner des Pakets. Dort werden sie während des Buildprozesses eingefügt. Der Ressourcenbezeichner solche Zeichenfolgen besitzen in der Regel die Form *Bibliotheksname/Ressourcendateiname/Ressourcenbezeichner*.

Eine Bibliothek kann einen ResourceLoader für ihre eigenen Ressourcen abrufen. Der folgende Code zeigt beispielsweise, wie eine Bibliothek oder eine App durch einen entsprechenden Verweis einen ResourceLoader für die Zeichenfolgenressourcen der Bibliothek abrufen kann.

**C#**
```csharp
var resourceLoader = new Windows.ApplicationModel.Resources.ResourceLoader("ContosoControl/Resources");
resourceLoader.GetString("string1");
```

## <a name="loading-strings-from-other-packages"></a>Laden von Zeichenfolgen aus anderen Paketen

Die Ressourcen für ein App-Paket werden über die oberste Ebene der [ResourceMap](/uwp/api/windows.applicationmodel.resources.core.resourcemap?branch=live) des Pakets verwaltet und erreicht, auf die über den aktuellen [ResourceManager](/uwp/api/windows.applicationmodel.resources.core.resourcemanager?branch=live) zugegriffen werden kann. In jedem Paket können Komponenten eigene ResourceMap-Unterstrukturen besitzen, auf die Sie über [ResourceMap.GetSubtree](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Resources.Core.ResourceMap#Windows_ApplicationModel_Resources_Core_ResourceMap_GetSubtree_System_String_) zugreifen können.

Ein Frameworkpaket kann auf seine eigenen Ressourcen über einen absolute Ressourcenbezeichner-URI zugreifen. Weitere Informationen finden Sie unter [URI-Schemas](uri-schemes.md).

## <a name="important-apis"></a>Wichtige APIs

* [ApplicationModel.Resources.ResourceLoader](https://msdn.microsoft.com/library/windows/apps/br206014)

## <a name="related-topics"></a>Verwandte Themen

* [Portieren von XAML und UI](../porting/wpsl-to-uwp-porting-xaml-and-ui.md#localization-and-globalization)
* [x:Uid-Direktive](../xaml-platform/x-uid-directive.md)
* [Angefügte Eigenschaften](../xaml-platform/attached-properties-overview.md)
* [Lokalisierbare Manifestelemente](/uwp/schemas/appxpackage/uapmanifestschema/localizable-manifest-items-win10?branch=live)
* [BCP-47-Sprachtag](http://go.microsoft.com/fwlink/p/?linkid=227302)
* [Anpassen von Ressourcen mit Qualifizierern für Sprache, Skalierung und anderen](tailor-resources-lang-scale-contrast.md)
* [Laden von Zeichenfolgenressourcen](https://msdn.microsoft.com/library/windows/apps/xaml/hh965323)