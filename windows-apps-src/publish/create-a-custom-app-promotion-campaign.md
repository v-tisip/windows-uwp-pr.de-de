---
author: shawjohn
Description: "Neben dem Erstellen einer Anzeigenkampagne für Ihre App, die in Windows-Apps ausgeführt wird, können Sie Ihre App auch über andere Kanäle bewerben."
title: "Erstellen einer Werbekampagne für benutzerdefinierte Apps"
ms.assetid: 7C9BF73E-B811-4FC7-B1DD-4A0C2E17E95D
ms.author: johnshaw
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, benutzerdefiniert, App, Werbung, Kampagnen
ms.openlocfilehash: 1e56b1df4b5501ded5db799c3ad67f97c0e1cfcd
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="create-a-custom-app-promotion-campaign"></a>Erstellen einer Werbekampagne für benutzerdefinierte Apps

Neben dem Erstellen einer [Anzeigenkampagne für Ihre App](create-an-ad-campaign-for-your-app.md), die in Windows-Apps ausgeführt wird, können Sie Ihre App auch über andere Kanäle bewerben. Beispielsweise können Sie Ihre App mit einem Drittanbieter für App-Marketing bewerben oder Links zu Ihrer App in sozialen Netzwerken bereitstellen. Diese Aktivitäten werden als *benutzerdefinierte Kampagnen* bezeichnet.

Wenn Sie benutzerdefinierte Kampagnen für Ihre App ausführen, können Sie die relative Leistung der einzelnen Kampagnen nachverfolgen, indem Sie für jede benutzerdefinierte Kampagne eine andere Windows Store-App-URL mit jeweils unterschiedlichen Kampagnen-IDs erstellen. Wenn ein Kunde, der Windows10 ausführt, auf eine URL mit einer Kampagnen-ID klickt, ordnet Microsoft den Klick der entsprechenden benutzerdefinierten Kampagne zu und stellt Ihnen diese Daten zur Verfügung.

Es gibt im Wesentlichen zwei Typen von Daten zu benutzerdefinierten Kampagnen: Seitenaufrufe für Ihre App und *Konvertierungen*. Als Konvertierung wird ein App-Erwerb bezeichnet, der daraus resultiert, dass ein Kunde von einer über eine benutzerdefinierte Kampagne beworbenen URL aus auf die Windows Store-Seite für Ihre App klickt. Weitere Informationen zu Konvertierungen finden Sie unter [Wann gelten App-Erwerbe als Konvertierungen?](#understanding-how-app-acquisitions-qualify-as-conversions) in diesem Thema.

Sie können Leistungsdaten einer benutzerdefinierten Kampagne für Ihre App auf folgende Arten abrufen:

* Sie können Seitenaufrufe und Konvertierungen für Ihre App oder Ihr Add-On aus dem Bericht [Kanäle und Konvertierungen](channels-and-conversions-report.md) im Dev Center-Dashboard abrufen.
* Wenn es sich bei Ihrer App um eine App für die universelle Windows-Plattform (UWP) handelt, kann sie mit APIs im Windows SDK programmgesteuert die benutzerdefinierte Kampagnen-ID abrufen, die zu einer Konvertierung geführt hat.

> **Wichtig:**&nbsp;&nbsp;Diese Daten werden nur für Kunden nachverfolgt, die Windows10 ausführen. Kunden, die andere Betriebssysteme verwenden, können trotzdem den Link zu Ihrem App-Eintrag aufrufen, es werden jedoch keine Daten über die Aktivitäten dieser Kunden eingeschlossen.

## <a name="example-custom-campaign-scenario"></a>Beispielszenario für eine benutzerdefinierte Kampagne

Stellen Sie sich vor, ein Spieleentwickler hat die Entwicklung eines neuen Spiels abgeschlossen und möchte dafür bei Spielern seiner bereits vorhandenen Spiele werben. Er veröffentlicht die Ankündigung des neuen Spiels auf seiner Facebook-Seite, zusammen mit einem Link zur WindowsStore-Seite für das Spiel. Viele Spieler folgen ihm auch auf Twitter, darum twittert er die Ankündigung mit dem Link zur Windows Store-Seite des Spiels auch dort.

Um den Erfolg der einzelnen Werbekanäle nachzuverfolgen, erstellt der Entwickler zwei Varianten der URL für die Windows Store-Seite des Spiels:

* Die URL, die er auf seiner Facebook-Seite postet, enthält die benutzerdefinierte Kampagnen-ID `my-facebook-campaign`.
* Die URL, die er auf Twitter postet, enthält die benutzerdefinierte Kampagnen-ID `my-twitter-campaign`.

Wenn seine Facebook- und Twitter-Follower auf die URLs klicken, verfolgt Microsoft jeden Klick und ordnet ihn der entsprechenden benutzerdefinierten Kampagne zu. Nachfolgende qualifizierende Käufe des Spiels und Käufe von Add-Ons werden der benutzerdefinierten Kampagne zugeordnet und als Konvertierungen gemeldet.

<span id="conversions" />
## <a name="understanding-how-app-acquisitions-qualify-as-conversions"></a>Wann gelten App-Erwerbe als Konvertierungen?

Als *Konvertierung* wird ein App-Erwerb bezeichnet, der daraus resultiert, dass ein Kunde von einer über eine benutzerdefinierte Kampagne beworbenen URL aus auf die Windows Store-Seite für Ihre App klickt. Für die Qualifizierung als Konvertierung für den Bericht [Kanäle und Konvertierungen](channels-and-conversions-report.md) im Dev Center-Dashboard und für die Qualifizierung als Konvertierung für [programmgesteuertes Abrufen der Kampagnen-ID](#programmatically) gelten verschiedene Szenarios.

### <a name="qualifying-conversions-for-the-dashboard-report"></a>Qualifizieren von Konvertierungen für den Dashboardbericht

Um als Konvertierung für den Bericht [Kanäle und Konvertierungen](channels-and-conversions-report.md) zu gelten, müssen die folgenden Szenarien erfüllt sein:

* Ein Kunde *mit oder ohne einem bekannten Microsoft-Konto* klickt auf eine App-URL, die eine benutzerdefinierte Kampagnen-ID enthält, und wird auf die Windows Store-Seite für die App weitergeleitet. Der gleiche Kunde erwirbt die App innerhalb von 24 Stunden, nachdem er zuerst auf die Windows Store-URL mit der benutzerdefinierten Kampagnen-ID geklickt hat.

* Wenn der Kunde die App auf einem anderen Computer oder Gerät als auf dem erwirbt, auf dem er auf die Windows Store-URL mit der benutzerdefinierten Kampagnen-ID geklickt hat, zählt die Konvertierung nur dann, wenn der Kunde ein Microsoft-Konto hat.

> **Hinweis**&nbsp;&nbsp;Für App-Erwerbe, die als Konvertierungen für eine benutzerdefinierte Kampagne gezählt werden, werden Add-On-Einkäufe in der App ebenfalls als Konvertierungen für dieselbe benutzerdefinierte Kampagne gezählt.

### <a name="qualifying-conversions-for-programmatically-retrieving-the-campaign-id"></a>Qualifizieren von Konvertierungen für programmgesteuertes Abrufen der Kampagnen-ID

Damit eine App-Installation beim programmgesteuerten Abrufen der Kampagnen-ID der App als Konvertierung gilt, müssen die folgenden Bedingungen erfüllt sein:

* Auf einem Gerät mit **Windows10, Version 1607 oder höher**: ein Kunde *mit oder ohne ein gültiges Microsoft-Konto* klickt auf eine App-URL, die eine benutzerdefinierte Kampagnen-ID enthält, und wird zur Windows Store-Seite für die App weitergeleitet. Der Kunde erwirbt die App während desselben Aufrufs der Windows Store-Seite, nachdem er auf die URL geklickt hat.

* Auf einem Gerät mit **Windows10, Version 1511 oder früher**: ein Kunde *mit einem gültigen Microsoft-Konto* klickt auf eine App-URL, die eine benutzerdefinierte Kampagnen-ID enthält, und wird zur Windows Store-Seite für die App weitergeleitet. Der Kunde erwirbt die App während desselben Aufrufs der Windows Store-Seite, nachdem er auf die URL geklickt hat. Bei diesen Versionen von Windows10 muss der Benutzer ein gültiges Microsoft-Konto besitzen, damit der Erwerb von Volumenlizenzen als Konvertierung eingeordnet wird, wenn die Kampagnen-ID programmgesteuert abgerufen wird.

>**Hinweis**&nbsp;&nbsp;Wenn der Kunde die Seite verlässt und dann innerhalb von 24 Stunden darauf zurückkehrt (entweder auf dem gleichen Computer oder Gerät oder auf einem anderen Computer oder Gerät, wenn er über ein Microsoft-Konto verfügt) und die App erwirbt, gilt dies als Konvertierung auf dem [Bericht zu Kanälen und Konvertierungen](channels-and-conversions-report.md). Dies gilt allerdings nicht als Konvertierung, wenn Sie die Kampagnen-ID programmgesteuert abrufen.

## <a name="embed-a-custom-campaign-id-to-your-apps-windows-store-page-url"></a>Einbetten einer benutzerdefinierten Kampagnen-ID in die URL der Windows Store-Seite Ihrer App

So erstellen Sie eine Windows Store-Seiten-URL für Ihre App mit einer benutzerdefinierten Kampagnen-ID

1.  Erstellen Sie eine ID-Zeichenfolge für Ihre benutzerdefinierte Kampagne. Diese Zeichenfolge kann bis zu 100 Zeichen enthalten. Es wird jedoch empfohlen, kurze, leicht erkennbare Kampagnen-IDs zu definieren.

  >**Hinweis:**&nbsp;&nbsp;Die Kampagnen-ID-Zeichenfolge ist für andere Entwickler in einem Bericht zu Kanälen und Konvertierungen sichtbar. Dies kann passieren, wenn ein Kunde auf Ihre Kampagnen-ID für den Store klickt, aber eine andere Entwickler-App in der gleichen Sitzung erwirbt. Obwohl der Name Ihrer Kampagnen-ID für einen anderen Entwickler sichtbar sein kann, kann der Entwickler nur sehen, wie viele Konvertierungen für deren eigene App aus dem anfänglichen Klick auf die Kampagnen-ID resultierten. Er sieht nicht die Daten über die Anzahl der Benutzer, die Ihre App von einem Klicken auf Ihre Kampagnen-ID erworben haben.

2.  Rufen Sie die Windows Store-Seiten-URL für Ihre App im HTML- oder Protokollformat ab.

    * Verwenden Sie das HTTP-Format, wenn Sie möchten, dass Kunden in einem Browser auf die Windows Store-Seite Ihrer App navigieren (diese URL startet auch die Windows Store-App mit Ihrem App-Eintrag, wenn die Windows Store-App installiert ist). Diese URL hat das Format **`https://www.microsoft.com/store/apps/*your app name*/*your app ID*`**. Die HTTP-URL für Skype lautet beispielsweise `https://www.microsoft.com/store/apps/skype/9wzdncrfj364`. Die HTML-Format-URL ist auf der Seite [**App-Identität** im Dev Center-Dashboard](link-to-your-app.md) verfügbar. Hinweis: URLs im HTTP-Format können zum Navigieren zum Windows Store in einem Browser auf Computern und Tablets unter Windows7 und neueren Versionen sowie auf Smartphones mit mindestens Windows Phone8 verwendet werden.

    * Verwenden Sie das Protokollformat, wenn Sie Ihre App in anderen Windows-Apps bewerben, die auf einem Gerät oder Computer mit installierter WindowsStore-App ausgeführt werden, und Sie möchten, dass Kunden die Seite Ihrer App in der WindowsStore-App öffnen. Diese URL hat das Format **`ms-windows-store://pdp/?PRODUCTID=*your app id*`**. Die Protokoll-URL für Skype lautet beispielsweise `ms-windows-store://pdp/?PRODUCTID=9wzdncrfj364`.

3.  Fügen Sie am Ende der URL für Ihre App die folgende Zeichenfolge an:

    * Fügen Sie an eine HTTP-Format-URL **`?cid=*my custom campaign ID*`** an. Wenn Skype beispielsweise eine Kampagnen-ID mit dem Wert **custom\_campaign** einführt, würde die neue HTTP-URL einschließlich der Kampagnen-ID folgendermaßen lauten: `https://www.microsoft.com/store/apps/skype/9wzdncrfj364?cid=custom\_campaign`.

    * Fügen Sie für eine URL im Protokoll-Format **`&cid=*my custom campaign ID*`** an. Wenn Skype beispielsweise eine Kampagnen-ID mit dem Wert **custom\_campaign** einführt, würde die neue Protokoll-URL einschließlich der Kampagnen-ID folgendermaßen lauten: `ms-windows-store://pdp/?PRODUCTID=9wzdncrfj364&cid=custom\_campaign`.

<span id="programmatically" />
## <a name="programmatically-retrieve-the-custom-campaign-id-for-an-app"></a>Programmgesteuertes Abrufen der benutzerdefinierten Kampagnen-ID für eine App

Wenn es sich bei Ihrer App um eine UWP-App handelt, können Sie die Ihrer App zugeordnete benutzerdefinierte Kampagnen-ID programmgesteuert mit APIs im Windows SDK abrufen. Diese APIs ermöglichen viele Analysen und Monetarisierungsszenarien. Beispielsweise können Sie feststellen, ob der aktuelle Benutzer Ihre App erworben hat, nachdem er sie über Ihre Facebook-Kampagne entdeckt hat. Dann können Sie die App-Oberfläche entsprechend anpassen. Oder wenn Sie einen Drittanbieter für App-Marketing verwenden, können Sie Daten zurück an den Anbieter senden.

Diese APIs geben nur dann eine Kampagnen-ID-Zeichenfolge zurück, wenn der Kunde auf die URL mit der eingebetteten Kampagnen-ID klickt, auf die WindowsStore-Seite für Ihre App weitergeleitet wird und dann die App ohne Verlassen der Seite erwirbt. Wenn der Benutzer die Seite verlässt und dann später zurückkehrt und die App erwirbt, gilt dies bei der Verwendung dieser APIs [nicht als Konvertierung](#conversions).

Sie können verschiedene APIs verwenden, je nach der Version von Windows10, auf die Ihre App ausgerichtet ist:

* Windows10, Version 1607 oder höher: Verwenden Sie die [**StoreContext**](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext)-Klasse im **Windows.Services.Store**-Namespace. Bei der Verwendung dieser API können Sie die benutzerdefinierten Kampagnen-IDs für alle [qualifizierten Einkäufe](#conversions) abrufen, unabhängig davon, ob der Benutzer ein gültiges Microsoft-Konto hat.
* Windows10, Version 1511 oder früher: Verwenden Sie die [**CurrentApp**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.store.currentapp.aspx)-Klasse im **Windows.ApplicationModel.Store**-Namespace. Bei der Verwendung dieser API können Sie nur die benutzerdefinierten Kampagnen-IDs für [qualifizierte Einkäufe](#conversions) abrufen, wenn der Benutzer ein gültiges Microsoft-Konto hat.

>**Hinweis**&nbsp;&nbsp;Auch wenn der **Windows.ApplicationModel.Store**-Namespace in allen Versionen von Windows10 verfügbar ist, empfehlen wir, dass Sie die APIs im **Windows.Services.Store**-Namespace verwenden, wenn Ihre App auf Windows10, Version 1607 oder höher, ausgerichtet ist. Weitere Informationen zu den Unterschieden zwischen diesen Namespaces finden Sie unter [In-App-Käufe und Testversionen](../monetize/in-app-purchases-and-trials.md#choose-namespace). Im folgenden Codebeispiel wird veranschaulicht, wie Sie Ihren Code strukturieren, um die beiden APIs im selben Projekt zu verwenden.

### <a name="code-example"></a>Codebeispiel

Im folgenden Codebeispiel wird veranschaulicht, wie Sie die benutzerdefinierte Kampagnen-ID abrufen. In diesem Beispiel werden beide Gruppen von APIs im **Windows.Services.Store**- und im **Windows.ApplicationModel.Store**-Namespace mit [versionsadaptivem Code](../debug-test-perf/version-adaptive-code.md) verwendet. Mit diesem Prozess kann Ihr Code auf allen Versionen von Windows10 ausgeführt werden. Um diesen Code zu verwenden, muss mit die Ziel-Betriebssystemversion des Projekts **Windows 10 Anniversary Edition (10.0; Build 14394)** oder höher sein, auch wenn die minimale Betriebssystemversion eine frühere Version sein kann.

``` csharp
// This example assumes the code file has using statements for
// System.Linq, System.Threading.Tasks, Windows.Data.Json,
// and Windows.Services.Store.
public async Task<string> GetCampaignId()
{
    // Use APIs in the Windows.Services.Store namespace if they are available
    // (the app is running on a device with Windows 10, version 1607, or later).
    if (Windows.Foundation.Metadata.ApiInformation.IsTypePresent(
         "Windows.Services.Store.StoreContext"))
    {
        StoreContext context = StoreContext.GetDefault();

        // Try to get the campaign ID for users with a recognized Microsoft account.
        StoreProductResult result = await context.GetStoreProductForCurrentAppAsync();
        if (result.Product != null)
        {
            StoreSku sku = result.Product.Skus.FirstOrDefault(s => s.IsInUserCollection);

            if (sku != null)
            {
                return sku.CollectionData.CampaignId;
            }
        }

        // Try to get the campaign ID from the license data for users without a
        // recognized Microsoft account.
        StoreAppLicense license = await context.GetAppLicenseAsync();
        JsonObject json = JsonObject.Parse(license.ExtendedJsonData);
        if (json.ContainsKey("customPolicyField1"))
        {
            return json["customPolicyField1"].GetString();
        }

        // No campaign ID was found.
        return String.Empty;
    }
    // Fall back to using APIs in the Windows.ApplicationModel.Store namespace instead
    // (the app is running on a device with Windows 10, version 1577, or earlier).
    else
    {
#if DEBUG
        return await Windows.ApplicationModel.Store.CurrentAppSimulator.GetAppPurchaseCampaignIdAsync();
#else
        return await Windows.ApplicationModel.Store.CurrentApp.GetAppPurchaseCampaignIdAsync() ;
#endif
    }
}
```

Dieser Code bewirkt Folgendes:

1. Zunächst überprüft er, ob die [**StoreContext**](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext)-Klasse im **Windows.Services.Store**-Namespace auf dem aktuellen Gerät verfügbar ist (Das bedeutet, dass das Gerät Windows10, Version 1607 oder höher, ausführt). Wenn dies der Fall ist, verwendet der Code diese Klasse weiter.

2. Als Nächstes wird versucht, die benutzerdefinierte Kampagnen-ID für den Fall abzurufen, dass der aktuelle Benutzer ein gültiges Microsoft-Konto hat. Dazu ruft der Code ein [**StoreSku**](https://docs.microsoft.com/uwp/api/Windows.Services.Store.StoreSku)-Objekt ab, das die aktuelle App-SKU darstellt, und ruft dann die [**CampaignId**](https://docs.microsoft.com/uwp/api/windows.services.store.storecollectiondata#Windows_Services_Store_StoreCollectionData_CampaignId)-Eigenschaft auf, um die Kampagnen-ID abzurufen, sofern verfügbar.

2. Der Code versucht dann, die Kampagnen-ID für den Fall abzurufen, dass der aktuelle Benutzer über kein gültiges Microsoft-Konto verfügt. In diesem Fall ist die Kampagnen-ID in die App-Lizenz eingebettet. Der Code ruft die Lizenz mit der [**GetAppLicenseAsync**](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext#Windows_Services_Store_StoreContext_GetAppLicenseAsync)-Methode ab und analysiert dann den JSON-Inhalt der Lizenz auf den Wert eines Schlüssel mit dem Namen *customPolicyField1*. Dieser Wert enthält die Kampagnen-ID.

3. Wenn die [**StoreContext**](https://docs.microsoft.com/uwp/api/windows.services.store.storecontext)-Klasse im **Windows.Services.Store**-Namespace nicht verfügbar ist, verwendet der Code dann wieder die[**GetAppPurchaseCampaignIdAsync**](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.store.currentapp.getapppurchasecampaignidasync.aspx)-Methode im **Windows.ApplicationModel.Store**-Namespace, um die benutzerdefinierte Kampagnen-ID abzurufen (Dieser Namespace ist in allen Versionen von Windows10 verfügbar, einschließlich Version 1511 und früher). Beachten Sie, dass Sie bei Verwendung dieser Methode nur die benutzerdefinierten Kampagnen-IDs für [qualifizierte Einkäufe](#conversions) abrufen können, wenn der Benutzer ein gültiges Microsoft-Konto hat.

  >**Hinweis:**&nbsp;&nbsp;Der **Windows.ApplicationModel.Store**-Namespace umfasst [**CurrentAppSimulator**](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentappsimulator), eine spezielle Klasse, die Store-Vorgänge zum Testen von Code vor dem Übermitteln Ihrer App an den Store simuliert. Diese Klasse ruft Daten aus [einer lokalen Datei mit dem Namen "Windows.StoreProxy.xml"](../monetize/in-app-purchases-and-trials-using-the-windows-applicationmodel-store-namespace.md#using-the-windowsstoreproxyxml-file-with-currentappsimulator) ab. Im vorherigen Codebeispiel wird veranschaulicht, wie **CurrentApp** und **CurrentAppSimulator** in Debug- und Nicht-Debug-Code in Ihrem Projekt eingefügt werden. Um diesen Code in einer Debugumgebung zu testen, fügen Sie ein **AppPurchaseCampaignId**-Element zur Datei "WindowsStoreProxy.xml" auf Ihrem Entwicklungscomputer hinzu, wie im folgenden Beispiel gezeigt. Wenn Sie die App ausführen, gibt die [**GetAppPurchaseCampaignIdAsync**](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentappsimulator#Windows_ApplicationModel_Store_CurrentAppSimulator_GetAppPurchaseCampaignIdAsync)-Methode immer diesen Wert zurück.

  ``` xml
  <CurrentApp>
      ...
      <AppPurchaseCampaignId>your custom campaign ID</AppPurchaseCampaignId>
  </CurrentApp>
  ```

  >**Hinweis**&nbsp;&nbsp;Der **Windows.Services.Store**-Namespace stellt keine Klasse bereit, mit der Sie während der Tests Lizenzinformationen simulieren können. Stattdessen müssen Sie eine App im Store veröffentlichen und diese App auf Ihr Gerät für die Entwicklung herunterladen, um die Lizenz zum Testen zu verwenden. Weitere Informationen finden Sie unter [In-App-Käufe und Testversionen](../monetize/in-app-purchases-and-trials.md#testing).

## <a name="test-your-custom-campaign"></a>Testen der benutzerdefinierten Kampagne

Bevor Sie eine URL für eine benutzerdefinierte Kampagnen bewerben, empfehlen wir, Ihre benutzerdefinierte Kampagne folgendermaßen zu testen:

1.  Melden Sie sich bei Ihrem Microsoft-Konto auf dem Computer oder Gerät an, das Sie zum Testen verwenden.
2.  Klicken Sie auf die URL für Ihre benutzerdefinierte Kampagne. Stellen Sie sicher, dass Ihre App-Seite korrekt im Windows Store geladen wird, und schließen Sie dann die Windows Store-App bzw. die Browserseite.
3.  Klicken Sie noch einige weitere Male auf die URL, und schließen Sie nach jedem Besuch der App-Seite die Windows Store-App oder die Browserseite. Erwerben Sie bei einem der Besuche Ihrer App-Seite die App, um eine Konvertierung zu generieren. Zählen Sie, wie oft Sie insgesamt auf die URL geklickt haben.
4. Bestätigen Sie, ob die erwarteten Seitenaufrufe und Konvertierungen im [Bericht zu Kanälen und Konvertierungen](channels-and-conversions-report.md) angezeigt werden, und testen Sie den App-Code, um festzustellen, ob die Kampagnen-ID erfolgreich abgerufen werden kann.
