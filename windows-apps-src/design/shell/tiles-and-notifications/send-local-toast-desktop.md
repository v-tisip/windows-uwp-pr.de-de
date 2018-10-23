---
author: andrewleader
Description: Learn how Win32 C# apps can send local toast notifications and handle the user clicking the toast.
title: Senden von Popupbenachrichtigungen über C#-Apps
ms.assetid: E9AB7156-A29E-4ED7-B286-DA4A6E683638
label: Send a local toast notification from desktop C# apps
template: detail.hbs
ms.author: mijacobs
ms.date: 01/23/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, win32, Desktop, Popupbenachrichtigungen, Popup senden, lokale Popupbenachrichtigungen senden, Desktop Bridge, C#, C-Sharp
ms.localizationpriority: medium
ms.openlocfilehash: 3bda3e85fd89ef7a8b819fcd809acea4fd9a276b
ms.sourcegitcommit: c4d3115348c8b54fcc92aae8e18fdabc3deb301d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2018
ms.locfileid: "5408452"
---
# <a name="send-a-local-toast-notification-from-desktop-c-apps"></a><span data-ttu-id="76847-103">Senden von Popupbenachrichtigungen über C#-Apps</span><span class="sxs-lookup"><span data-stu-id="76847-103">Send a local toast notification from desktop C# apps</span></span>

<span data-ttu-id="76847-104">Desktop-Apps (Desktop-Brücke und klassische Win32) können interaktive Popupbenachrichtigungen wie Universelle Windows-Plattform (UWP)-Apps senden.</span><span class="sxs-lookup"><span data-stu-id="76847-104">Desktop apps (both Desktop Bridge and classic Win32) can send interactive toast notifications just like Universal Windows Platform (UWP) apps.</span></span> <span data-ttu-id="76847-105">Es gibt jedoch einige besondere Schritte für Desktop-Apps mit anderen Aktivierungsschematas und dem potenziellen Mangel der Paketidentität, wenn Sie die Desktop-Brücke nicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="76847-105">However, there are a few special steps for desktop apps due to the different activation schemes and the potential lack of package identity if you're not using the Desktop Bridge.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="76847-106">Wenn Sie eine UWP-App entwickeln, finden Sie Informationen in der [UWP-Dokumentation](send-local-toast.md).</span><span class="sxs-lookup"><span data-stu-id="76847-106">If you're writing a UWP app, please see the [UWP documentation](send-local-toast.md).</span></span> <span data-ttu-id="76847-107">Bei anderen Desktop Sprachen finden Sie Informationen unter [Desktop C++ WRL](send-local-toast-desktop-cpp-wrl.md).</span><span class="sxs-lookup"><span data-stu-id="76847-107">For other desktop languages, please see [Desktop C++ WRL](send-local-toast-desktop-cpp-wrl.md).</span></span>


## <a name="step-1-enable-the-windows-10-sdk"></a><span data-ttu-id="76847-108">Schritt1: Aktivieren von Windows10 SDK</span><span class="sxs-lookup"><span data-stu-id="76847-108">Step 1: Enable the Windows 10 SDK</span></span>

<span data-ttu-id="76847-109">Wenn Sie Windows10 SDK nicht für Ihre Win32-App aktiviert haben, müssen Sie dies zuerst tun.</span><span class="sxs-lookup"><span data-stu-id="76847-109">If you haven't enabled the Windows 10 SDK for your Win32 app, you must do that first.</span></span>

<span data-ttu-id="76847-110">Klicken Sie mit der rechten Maustaste auf Ihr Projekt, und wählen Sie dann **Projekt entladen** aus.</span><span class="sxs-lookup"><span data-stu-id="76847-110">Right click your project and select **Unload Project**.</span></span>

![Entladen eines Projekts](images/win32-unload-project.png)

<span data-ttu-id="76847-112">Klicken Sie dann mit der rechten Maustaste auf das Projekt, und wählen Sie **[Projektname] csproj bearbeiten** aus</span><span class="sxs-lookup"><span data-stu-id="76847-112">Then right click your project again, and select **Edit [projectname].csproj**</span></span>

![Bearbeiten eines Projekts](images/win32-edit-project.png)

<span data-ttu-id="76847-114">Unterhalb des vorhandenen `<TargetFrameworkVersion>`-Knotens, fügen Sie einen neuen `<TargetPlatformVersion>`-Knoten hinzu und geben Sie Ihre Mindestversion von Windows10 an.</span><span class="sxs-lookup"><span data-stu-id="76847-114">Below the existing `<TargetFrameworkVersion>` node, add a new `<TargetPlatformVersion>` node specifying your min version of Windows 10 supported.</span></span> <span data-ttu-id="76847-115">Das aktuell verwendete SDK ist die aktuelle SDK-Version, die Sie auf Ihrem Entwicklercomputer installiert haben.</span><span class="sxs-lookup"><span data-stu-id="76847-115">The actual SDK used will be the latest SDK that you have installed on your dev machine.</span></span> <span data-ttu-id="76847-116">Dies gibt Ihre erlaubte Mindestversion an (und ermöglicht es Ihnen, auf das Windows SDK zu verweisen).</span><span class="sxs-lookup"><span data-stu-id="76847-116">This simply specifies your min allowed version (and allows you to reference the Windows SDK).</span></span>

```xml
...
<TargetFrameworkVersion>...</TargetFrameworkVersion>
<TargetPlatformVersion>10.0.10240.0</TargetPlatformVersion>
...
```

<span data-ttu-id="76847-117">Speichern und Laden Sie das Projekt dann neu.</span><span class="sxs-lookup"><span data-stu-id="76847-117">Save your changes and then reload your project.</span></span>

![Ein Projekt neu laden](images/win32-reload-project.png)


## <a name="step-2-reference-the-apis"></a><span data-ttu-id="76847-119">Schritt2: Referenzieren der APIs</span><span class="sxs-lookup"><span data-stu-id="76847-119">Step 2: Reference the APIs</span></span>

<span data-ttu-id="76847-120">Öffnen Sie den Verweis-Manager (klicken Sie mit der rechten Maustaste auf das Projekt, wählen Sie **Hinzufügen -> Verweis hinzufügen**) und dann **Windows -> Core** aus und geben Sie folgende Referenzen an:</span><span class="sxs-lookup"><span data-stu-id="76847-120">Open the Reference Manager (right click project, select **Add -> Reference**), and select **Windows -> Core** and include the following references:</span></span>

* <span data-ttu-id="76847-121">Windows.Data</span><span class="sxs-lookup"><span data-stu-id="76847-121">Windows.Data</span></span>
* <span data-ttu-id="76847-122">Windows.UI</span><span class="sxs-lookup"><span data-stu-id="76847-122">Windows.UI</span></span>

![Verweis-Manager](images/win32-add-windows-reference.png)


## <a name="step-3-copy-compat-library-code"></a><span data-ttu-id="76847-124">Schritt3: Kopieren des Compat-Bibliothekscodes</span><span class="sxs-lookup"><span data-stu-id="76847-124">Step 3: Copy compat library code</span></span>

<span data-ttu-id="76847-125">Kopieren Sie [DesktopNotificationManagerCompat.cs-Datei von GitHub](https://raw.githubusercontent.com/WindowsNotifications/desktop-toasts/master/CS/DesktopToastsApp/DesktopNotificationManagerCompat.cs) in Ihr Projekt.</span><span class="sxs-lookup"><span data-stu-id="76847-125">Copy the [DesktopNotificationManagerCompat.cs file from GitHub](https://raw.githubusercontent.com/WindowsNotifications/desktop-toasts/master/CS/DesktopToastsApp/DesktopNotificationManagerCompat.cs) into your project.</span></span> <span data-ttu-id="76847-126">Die Compat-Bibliothek abstrahiert einen Großteil der Komplexität der Desktop-Benachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="76847-126">The compat library abstracts much of the complexity of desktop notifications.</span></span> <span data-ttu-id="76847-127">Die folgenden Anweisungen erfordern die Compat-Bibliothek.</span><span class="sxs-lookup"><span data-stu-id="76847-127">The following instructions require the compat library.</span></span>


## <a name="step-4-implement-the-activator"></a><span data-ttu-id="76847-128">Schritt 4: Implementieren des Aktivators</span><span class="sxs-lookup"><span data-stu-id="76847-128">Step 4: Implement the activator</span></span>

<span data-ttu-id="76847-129">Sie müssen einen Handler für die Popup-Aktivierung implementieren, damit, wenn der Benutzer auf das Popup klickt, Ihre app eine Aktion ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="76847-129">You must implement a handler for toast activation, so that when the user clicks on your toast, your app can do something.</span></span> <span data-ttu-id="76847-130">Dies ist erforderlich für das Popup, damit es im Info-Center beibehalten wird (da auf das Popup Tage später geklickt werden kann, wenn die App geschlossen ist).</span><span class="sxs-lookup"><span data-stu-id="76847-130">This is required for your toast to persist in Action Center (since the toast could be clicked days later when your app is closed).</span></span> <span data-ttu-id="76847-131">Diese Klasse kann an eine beliebige Stelle in Ihrem Projekt platziert werden.</span><span class="sxs-lookup"><span data-stu-id="76847-131">This class can be placed anywhere in your project.</span></span>

<span data-ttu-id="76847-132">Erweitern Sie die **NotificationActivator**-Klasse, und fügen Sie die drei Attribute hinzu, die unten aufgeführt sind. Erstellen Sie dann eine eindeutige GUID CLSID für Ihre App mithilfe einer der vielen online GUID-Generatoren.</span><span class="sxs-lookup"><span data-stu-id="76847-132">Extend the **NotificationActivator** class and then add the three attributes listed below, and create a unique GUID CLSID for your app using one of the many online GUID generators.</span></span> <span data-ttu-id="76847-133">Durch diese CLSID (Klassen-ID) weiß das Info-Center, welche Klasse für COM aktiviert werden soll.</span><span class="sxs-lookup"><span data-stu-id="76847-133">This CLSID (class identifier) is how Action Center knows what class to COM activate.</span></span>

```csharp
// The GUID CLSID must be unique to your app. Create a new GUID if copying this code.
[ClassInterface(ClassInterfaceType.None)]
[ComSourceInterfaces(typeof(INotificationActivationCallback))]
[Guid("replaced-with-your-guid-C173E6ADF0C3"), ComVisible(true)]
public class MyNotificationActivator : NotificationActivator
{
    public override void OnActivated(string invokedArgs, NotificationUserInput userInput, string appUserModelId)
    {
        // TODO: Handle activation
    }
}
```


## <a name="step-5-register-with-notification-platform"></a><span data-ttu-id="76847-134">Schritt5: Registrieren mit der Benachrichtigungsplattform</span><span class="sxs-lookup"><span data-stu-id="76847-134">Step 5: Register with notification platform</span></span>

<span data-ttu-id="76847-135">Anschließend müssen Sie eine Registrierung mit der Benachrichtigungsplattform durchführen.</span><span class="sxs-lookup"><span data-stu-id="76847-135">Then, you must register with the notification platform.</span></span> <span data-ttu-id="76847-136">Es sind unterschiedliche Schritte erforderlich, je nachdem, ob Sie die Desktop-Brücke oder klassische Win32 verwenden.</span><span class="sxs-lookup"><span data-stu-id="76847-136">There are different steps depending on whether you are using the Desktop Bridge or classic Win32.</span></span> <span data-ttu-id="76847-137">Wenn Sie beide unterstützen, müssen Sie beide Schritte durchführen (der Code bleibt allerdings gleich, die Bibliothek führt die Verzweigung für Sie durch!).</span><span class="sxs-lookup"><span data-stu-id="76847-137">If you support both, you must do both steps (however, no need to fork your code, our library handles that for you!).</span></span>


### <a name="desktop-bridge"></a><span data-ttu-id="76847-138">Desktop-Brücke</span><span class="sxs-lookup"><span data-stu-id="76847-138">Desktop Bridge</span></span>

<span data-ttu-id="76847-139">Bei Verwendung der Desktop-Brücke (oder wenn Sie beide Modi unterstützen), fügen Sie Ihrem **Package.appxmanifest** hinzu:</span><span class="sxs-lookup"><span data-stu-id="76847-139">If you're using Desktop Bridge (or if you support both), in your **Package.appxmanifest**, add:</span></span>

1. <span data-ttu-id="76847-140">Deklaration für **Xmlns:com**</span><span class="sxs-lookup"><span data-stu-id="76847-140">Declaration for **xmlns:com**</span></span>
2. <span data-ttu-id="76847-141">Deklaration für **xmlns:desktop**</span><span class="sxs-lookup"><span data-stu-id="76847-141">Declaration for **xmlns:desktop**</span></span>
3. <span data-ttu-id="76847-142">Im **IgnorableNamespaces**-Attribut **com** und **desktop**</span><span class="sxs-lookup"><span data-stu-id="76847-142">In the **IgnorableNamespaces** attribute, **com** and **desktop**</span></span>
4. <span data-ttu-id="76847-143">**com:Extension** für den COM-Aktivator mithilfe der GUID aus Schritt 4.</span><span class="sxs-lookup"><span data-stu-id="76847-143">**com:Extension** for the COM activator using the GUID from step #4.</span></span> <span data-ttu-id="76847-144">Stellen Sie sicher, dass `Arguments="-ToastActivated"` hinzugefügt wurde, damit Sie wissen, dass der Start über ein Popup ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="76847-144">Be sure to include the `Arguments="-ToastActivated"` so that you know your launch was from a toast</span></span>
5. <span data-ttu-id="76847-145">**desktop:Extension** für **windows.toastNotificationActivation**, um den Popup-Aktivator CLSID zu deklarieren (der GUID aus Schritt #4).</span><span class="sxs-lookup"><span data-stu-id="76847-145">**desktop:Extension** for **windows.toastNotificationActivation** to declare your toast activator CLSID (the GUID from step #4).</span></span>

**<span data-ttu-id="76847-146">Package.appxmanifest</span><span class="sxs-lookup"><span data-stu-id="76847-146">Package.appxmanifest</span></span>**

```xml
<Package
  ...
  xmlns:com="http://schemas.microsoft.com/appx/manifest/com/windows10"
  xmlns:desktop="http://schemas.microsoft.com/appx/manifest/desktop/windows10"
  IgnorableNamespaces="... com desktop">
  ...
  <Applications>
    <Application>
      ...
      <Extensions>

        <!--Register COM CLSID LocalServer32 registry key-->
        <com:Extension Category="windows.comServer">
          <com:ComServer>
            <com:ExeServer Executable="YourProject\YourProject.exe" Arguments="-ToastActivated" DisplayName="Toast activator">
              <com:Class Id="replaced-with-your-guid-C173E6ADF0C3" DisplayName="Toast activator"/>
            </com:ExeServer>
          </com:ComServer>
        </com:Extension>

        <!--Specify which CLSID to activate when toast clicked-->
        <desktop:Extension Category="windows.toastNotificationActivation">
          <desktop:ToastNotificationActivation ToastActivatorCLSID="replaced-with-your-guid-C173E6ADF0C3" /> 
        </desktop:Extension>

      </Extensions>
    </Application>
  </Applications>
 </Package>
```


### <a name="classic-win32"></a><span data-ttu-id="76847-147">Klassisch Win32</span><span class="sxs-lookup"><span data-stu-id="76847-147">Classic Win32</span></span>

<span data-ttu-id="76847-148">Wenn Sie eine klassische Win32 verwenden (oder wenn Sie beide Modi unterstützen), müssen Sie Ihre Anwendungsbenutzermodell-ID (AUMID) und den Popupbenachrichtigungs-Aktivator CLSID (der GUID aus Schritt4 #) auf der App-Verknüpfung im Startmenü deklarieren.</span><span class="sxs-lookup"><span data-stu-id="76847-148">If you're using classic Win32 (or if you support both), you have to declare your Application User Model ID (AUMID) and toast activator CLSID (the GUID from step #4) on your app's shortcut in Start.</span></span>

<span data-ttu-id="76847-149">Wählen Sie einen eindeutigen AUMID, der Ihrer Win32-App identifiziert.</span><span class="sxs-lookup"><span data-stu-id="76847-149">Pick a unique AUMID that will identify your Win32 app.</span></span> <span data-ttu-id="76847-150">Dies geschieht in der Regel in Form von [Firmenname].[AppName], es sollte allerdings in allen Apps eindeutig sein (fügen Sie Ziffern am Ende hinzu).</span><span class="sxs-lookup"><span data-stu-id="76847-150">This is typically in the form of [CompanyName].[AppName], but you want to ensure this is unique across all apps (feel free to add some digits at the end).</span></span>

#### <a name="step-51-wix-installer"></a><span data-ttu-id="76847-151">Schritt 5.1: WiX Installer</span><span class="sxs-lookup"><span data-stu-id="76847-151">Step 5.1: WiX Installer</span></span>

<span data-ttu-id="76847-152">Wenn Sie WiX als Installer verwenden, bearbeiten Sie die **Product.wxs**-Datei, um dem Startmenü zwei Verknüpfungseigenschaften hinzuzufügen, wie unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="76847-152">If you're using WiX for your installer, edit the **Product.wxs** file to add the two shortcut properties to your Start menu shortcut as seen below.</span></span> <span data-ttu-id="76847-153">Stellen Sie sicher, dass Ihre GUID aus Schritt4 # in `{}` eingeschlossen ist, wie unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="76847-153">Be sure that your GUID from step #4 is enclosed in `{}` as seen below.</span></span>

**<span data-ttu-id="76847-154">Product.wxs</span><span class="sxs-lookup"><span data-stu-id="76847-154">Product.wxs</span></span>**

```xml
<Shortcut Id="ApplicationStartMenuShortcut" Name="Wix Sample" Description="Wix Sample" Target="[INSTALLFOLDER]WixSample.exe" WorkingDirectory="INSTALLFOLDER">
                    
    <!--AUMID-->
    <ShortcutProperty Key="System.AppUserModel.ID" Value="YourCompany.YourApp"/>
    
    <!--COM CLSID-->
    <ShortcutProperty Key="System.AppUserModel.ToastActivatorCLSID" Value="{replaced-with-your-guid-C173E6ADF0C3}"/>
    
</Shortcut>
```

> [!IMPORTANT]
> <span data-ttu-id="76847-155">Um Benachrichtigungen tatsächlich verwenden zu können, müssen Sie Ihrer App durch den Installer einmal vor dem Debuggen installieren, damit die Verknüpfung auf dem Startmenü mit AUMID und CLSID vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="76847-155">In order to actually use notifications, you must install your app through the installer once before debugging normally, so that the Start shortcut with your AUMID and CLSID is present.</span></span> <span data-ttu-id="76847-156">Nachdem die Verknüpfung auf dem Startmenü vorhanden ist, können Sie mithilfe von F5 in Visual Studio debuggen.</span><span class="sxs-lookup"><span data-stu-id="76847-156">After the Start shortcut is present, you can debug using F5 from Visual Studio.</span></span>


#### <a name="step-52-register-aumid-and-com-server"></a><span data-ttu-id="76847-157">Schritt5.2: Registrieren des AUMID und COM-Servers</span><span class="sxs-lookup"><span data-stu-id="76847-157">Step 5.2: Register AUMID and COM server</span></span>

<span data-ttu-id="76847-158">Rufen Sie unabhängig vom Installer im App Startcode (vor dem Aufrufen der Benachrichtigungs-APIs), die **RegisterAumidAndComServer**-Methode auf, und geben Sie die Benachrichtigungs-Aktivator-Klasse von Schritt 4 und die oben verwendete AUMID an.</span><span class="sxs-lookup"><span data-stu-id="76847-158">Then, regardless of your installer, in your app's startup code (before calling any notification APIs), call the **RegisterAumidAndComServer** method, specifying your notification activator class from step #4 and your AUMID used above.</span></span>

```csharp
// Register AUMID and COM server (for Desktop Bridge apps, this no-ops)
DesktopNotificationManagerCompat.RegisterAumidAndComServer<MyNotificationActivator>("YourCompany.YourApp");
```

<span data-ttu-id="76847-159">Wenn Desktop-Brücke und klassisches Win32 unterstützt werden, können Sie diese Methode unabhängig davon aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="76847-159">If you support both Desktop Bridge and classic Win32, feel free to call this method regardless.</span></span> <span data-ttu-id="76847-160">Wenn Sie die Methode mit der Desktop-Brücke ausführen, wird sie sofort zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="76847-160">If you're running under Desktop Bridge, this method will simply return immediately.</span></span> <span data-ttu-id="76847-161">Sie müssen den Code nicht verzweigen.</span><span class="sxs-lookup"><span data-stu-id="76847-161">There's no need to fork your code.</span></span>

<span data-ttu-id="76847-162">Mit dieser Methode können Sie Compat-APIs zum Senden und Verwalten von Benachrichtigungen aufrufen, ohne ständig die AUMID angeben zu müssen.</span><span class="sxs-lookup"><span data-stu-id="76847-162">This method allows you to call the compat APIs to send and manage notifications without having to constantly provide your AUMID.</span></span> <span data-ttu-id="76847-163">Es fügt ebenfalls den LocalServer32-Schlüssel für den COM-Server hinzu.</span><span class="sxs-lookup"><span data-stu-id="76847-163">And it inserts the LocalServer32 registry key for the COM server.</span></span>


## <a name="step-6-register-com-activator"></a><span data-ttu-id="76847-164">Schritt 6: Registrieren des COM-Aktivators</span><span class="sxs-lookup"><span data-stu-id="76847-164">Step 6: Register COM activator</span></span>

<span data-ttu-id="76847-165">Für Desktop-Brücken und klassische Win32-Apps müssen Sie Ihren Benachrichtigung-Aktivatortyp registrieren, damit Sie Popupaktivierungen behandeln können.</span><span class="sxs-lookup"><span data-stu-id="76847-165">For both Desktop Bridge and classic Win32 apps, you must register your notification activator type, so that you can handle toast activations.</span></span>

<span data-ttu-id="76847-166">Rufen Sie im App-Startcode die folgende **RegisterActivator**-Methode auf und übergeben Sie die Implementierung der **NotificationActivator**-Klasse, die Sie in Schritt4 # erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="76847-166">In your app's startup code, call the following **RegisterActivator** method, passing in your implementation of the **NotificationActivator** class you created in step #4.</span></span> <span data-ttu-id="76847-167">Dies muss in der Reihenfolge aufgerufen werden, in der Sie alle Popupaktivierungen erhalten.</span><span class="sxs-lookup"><span data-stu-id="76847-167">This must be called in order for you to receive any toast activations.</span></span>

```csharp
// Register COM server and activator type
DesktopNotificationManagerCompat.RegisterActivator<MyNotificationActivator>();
```


## <a name="step-7-send-a-notification"></a><span data-ttu-id="76847-168">Schritt 7: Senden einer Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="76847-168">Step 7: Send a notification</span></span>

<span data-ttu-id="76847-169">Das Senden einer Benachrichtigung ist für UWP-Apps identisch, außer dass Sie die **DesktopNotificationManagerCompat**-Klasse zum Erstellen eines **ToastNotifier** verwenden.</span><span class="sxs-lookup"><span data-stu-id="76847-169">Sending a notification is identical to UWP apps, except that you will use the **DesktopNotificationManagerCompat** class to create a **ToastNotifier**.</span></span> <span data-ttu-id="76847-170">Die Compat-Bibliothek behandelt den Unterschied zwischen Desktop-Brücke und klassischer Win32 automatisch, damit Sie keinen Code verzweigen müssen.</span><span class="sxs-lookup"><span data-stu-id="76847-170">The compat library automatically handles the difference between Desktop Bridge and classic Win32 so you do not have to fork your code.</span></span> <span data-ttu-id="76847-171">Für klassisches Win32 speichert die Compat-Bibliothek Ihre AUMID, die Sie beim Aufrufen von **RegisterAumidAndComServer** bereitgestellt haben, damit Sie sich nicht die AUMID kümmern müssen, wann Sie diese bereitstellen und wann nicht.</span><span class="sxs-lookup"><span data-stu-id="76847-171">For classic Win32, the compat library caches your AUMID you provided when calling **RegisterAumidAndComServer** so that you don't need to worry about when to provide or not provide the AUMID.</span></span>

> [!NOTE]
> <span data-ttu-id="76847-172">Installieren Sie die [Benachrichtigungsbibliothek](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/), damit Sie Benachrichtigungen mithilfe von C#-Code erstellen können anstelle von unformatiertem XML.</span><span class="sxs-lookup"><span data-stu-id="76847-172">Install the [Notifications library](https://www.nuget.org/packages/Microsoft.Toolkit.Uwp.Notifications/) so that you can construct notifications using C# as seen below, instead of using raw XML.</span></span>

<span data-ttu-id="76847-173">Stellen Sie sicher, dass Sie den unten angezeigten **ToastContent** verwenden (oder die Vorlage „ToastGeneric”, wenn Sie XML selbst erstellen), da ältere Vorlagen der Windows8.1 Popupbenachrichtigungen nicht den COM-Benachrichtigungs-Aktivator aktivieren, den Sie in Schritt4 # erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="76847-173">Make sure you use the **ToastContent** seen below (or the ToastGeneric template if you're hand-crafting XML) since the legacy Windows 8.1 toast notification templates will not activate your COM notification activator you created in step #4.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="76847-174">HTTP-Bilder werden nur in Desktop-Brücken-Apps unterstützt, die die Internetfunktion im Manifest haben.</span><span class="sxs-lookup"><span data-stu-id="76847-174">Http images are only supported in Desktop Bridge apps that have the internet capability in their manifest.</span></span> <span data-ttu-id="76847-175">Klassische Win32-Apps unterstützen keine HTTP-Bilder. Sie müssen das Bild in die lokalen App-Daten herunterladen und lokal darauf verweisen.</span><span class="sxs-lookup"><span data-stu-id="76847-175">Classic Win32 apps do not support http images; you must download the image to your local app data and reference it locally.</span></span>

```csharp
// Construct the visuals of the toast (using Notifications library)
ToastContent toastContent = new ToastContent()
{
    // Arguments when the user taps body of toast
    Launch = "action=viewConversation&conversationId=5",

    Visual = new ToastVisual()
    {
        BindingGeneric = new ToastBindingGeneric()
        {
            Children =
            {
                new AdaptiveText()
                {
                    Text = "Hello world!"
                }
            }
        }
    }
};

// Create the XML document (BE SURE TO REFERENCE WINDOWS.DATA.XML.DOM)
var doc = new XmlDocument();
doc.LoadXml(toastContent.GetContent());

// And create the toast notification
var toast = new ToastNotification(doc);

// And then show it
DesktopNotificationManagerCompat.CreateToastNotifier().Show(toast);
```

> [!IMPORTANT]
> <span data-ttu-id="76847-176">Klassische Win32-Apps können keine älteren Popupvorlagen (z.B. ToastText02) verwenden.</span><span class="sxs-lookup"><span data-stu-id="76847-176">Classic Win32 apps cannot use legacy toast templates (like ToastText02).</span></span> <span data-ttu-id="76847-177">Die Aktivierung älterer Vorlagen schlägt fehl, wenn die COM-CLSID angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="76847-177">Activation of the legacy templates will fail when the COM CLSID is specified.</span></span> <span data-ttu-id="76847-178">Wie oben erwähnt, müssen Sie die Windows10 ToastGeneric-Vorlagen verwenden.</span><span class="sxs-lookup"><span data-stu-id="76847-178">You must use the Windows 10 ToastGeneric templates as seen above.</span></span>


## <a name="step-8-handling-activation"></a><span data-ttu-id="76847-179">Schritt 8: Behandeln der Aktivierung</span><span class="sxs-lookup"><span data-stu-id="76847-179">Step 8: Handling activation</span></span>

<span data-ttu-id="76847-180">Wenn der Benutzer auf das Popup klickt, wird die **OnActivated**-Methode Ihre **NotificationActivator**-Klasse aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="76847-180">When the user clicks on your toast, the **OnActivated** method of your **NotificationActivator** class is invoked.</span></span>

<span data-ttu-id="76847-181">Innerhalb der OnActivated-Methode können Sie die Argumente analysieren, die Sie im Popup angegeben haben und die Benutzereingabe abrufen, die der Benutzer eingegeben oder ausgewählt hat und dann entsprechend Ihre App aktivieren.</span><span class="sxs-lookup"><span data-stu-id="76847-181">Inside the OnActivated method, you can parse the args that you specified in the toast and obtain the user input that the user typed or selected, and then activate your app accordingly.</span></span>

> [!NOTE]
> <span data-ttu-id="76847-182">Die **OnActivated**-Methode wird nicht im UI-Thread aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="76847-182">The **OnActivated** method is not called on the UI thread.</span></span> <span data-ttu-id="76847-183">Wenn Sie UI-Thread Vorgänge ausführen möchten, rufen Sie `Application.Current.Dispatcher.Invoke(callback)` auf.</span><span class="sxs-lookup"><span data-stu-id="76847-183">If you'd like to perform UI thread operations, you must call `Application.Current.Dispatcher.Invoke(callback)`.</span></span>

```csharp
// The GUID must be unique to your app. Create a new GUID if copying this code.
[ClassInterface(ClassInterfaceType.None)]
[ComSourceInterfaces(typeof(INotificationActivationCallback))]
[Guid("replaced-with-your-guid-C173E6ADF0C3"), ComVisible(true)]
public class MyNotificationActivator : NotificationActivator
{
    public override void OnActivated(string invokedArgs, NotificationUserInput userInput, string appUserModelId)
    {
        Application.Current.Dispatcher.Invoke(delegate
        {
            // Tapping on the top-level header launches with empty args
            if (arguments.Length == 0)
            {
                // Perform a normal launch
                OpenWindowIfNeeded();
                return;
            }

            // Parse the query string (using NuGet package QueryString.NET)
            QueryString args = QueryString.Parse(invokedArgs);

            // See what action is being requested 
            switch (args["action"])
            {
                // Open the image
                case "viewImage":

                    // The URL retrieved from the toast args
                    string imageUrl = args["imageUrl"];

                    // Make sure we have a window open and in foreground
                    OpenWindowIfNeeded();

                    // And then show the image
                    (App.Current.Windows[0] as MainWindow).ShowImage(imageUrl);

                    break;

                // Background: Quick reply to the conversation
                case "reply":

                    // Get the response the user typed
                    string msg = userInput["tbReply"];

                    // And send this message
                    SendMessage(msg);

                    // If there's no windows open, exit the app
                    if (App.Current.Windows.Count == 0)
                    {
                        Application.Current.Shutdown();
                    }

                    break;
            }
        });
    }

    private void OpenWindowIfNeeded()
    {
        // Make sure we have a window open (in case user clicked toast while app closed)
        if (App.Current.Windows.Count == 0)
        {
            new MainWindow().Show();
        }

        // Activate the window, bringing it to focus
        App.Current.Windows[0].Activate();

        // And make sure to maximize the window too, in case it was currently minimized
        App.Current.Windows[0].WindowState = WindowState.Normal;
    }
}
```

<span data-ttu-id="76847-184">Si sollten in der `App.xaml.cs`-Datei die **OnStartup**-Methode (für WPF-Apps) überschreiben, um festzulegen, ob Sie über ein Popup oder nicht gestartet werden soll, um einen ordnungsgemäßen Start zu unterstützen, während die App geschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="76847-184">To properly support being launched while your app is closed, in your `App.xaml.cs` file, you'll want to override **OnStartup** method (for WPF apps) to determine whether you're being launched from a toast or not.</span></span> <span data-ttu-id="76847-185">Wenn dies von einem Popup gestartet wird, wird ein Start-Argument von "-ToastActivated" gesendet.</span><span class="sxs-lookup"><span data-stu-id="76847-185">If launched from a toast, there will be a launch arg of "-ToastActivated".</span></span> <span data-ttu-id="76847-186">Sobald dies angezeigt wird, sollten Sie das Ausführen aller normaler Aktivierungscodes beenden, und den Start des **OnActivated**-Code Handler starten.</span><span class="sxs-lookup"><span data-stu-id="76847-186">When you see this, you should stop performing any normal launch activation code, and allow your **OnActivated** code handle launching.</span></span>

```csharp
protected override async void OnStartup(StartupEventArgs e)
{
    // Register AUMID, COM server, and activator
    DesktopNotificationManagerCompat.RegisterAumidAndComServer<MyNotificationActivator>("YourCompany.YourApp");
    DesktopNotificationManagerCompat.RegisterActivator<MyNotificationActivator>();

    // If launched from a toast
    if (e.Args.Contains("-ToastActivated"))
    {
        // Our NotificationActivator code will run after this completes,
        // and will show a window if necessary.
    }

    else
    {
        // Show the window
        // In App.xaml, be sure to remove the StartupUri so that a window doesn't
        // get created by default, since we're creating windows ourselves (and sometimes we
        // don't want to create a window if handling a background activation).
        new MainWindow().Show();
    }

    base.OnStartup(e);
}
```


### <a name="activation-sequence-of-events"></a><span data-ttu-id="76847-187">Aktivierungssequenz von Ereignissen</span><span class="sxs-lookup"><span data-stu-id="76847-187">Activation sequence of events</span></span>

<span data-ttu-id="76847-188">Für WPF ist die Aktivierungssequenz wie folgt...</span><span class="sxs-lookup"><span data-stu-id="76847-188">For WPF, the activation sequence is the following...</span></span>

<span data-ttu-id="76847-189">Wenn Ihre App bereits ausgeführt wird:</span><span class="sxs-lookup"><span data-stu-id="76847-189">If your app is already running:</span></span>

1. <span data-ttu-id="76847-190">**OnActivated** in Ihrer **NotificationActivator** wird aufgerufen</span><span class="sxs-lookup"><span data-stu-id="76847-190">**OnActivated** in your **NotificationActivator** is called</span></span>

<span data-ttu-id="76847-191">Wenn Ihre App nicht ausgeführt wird:</span><span class="sxs-lookup"><span data-stu-id="76847-191">If your app is not running:</span></span>

1. <span data-ttu-id="76847-192">**OnStartup** in `App.xaml.cs` wird mit **Args** von "-ToastActivated" aufgerufen</span><span class="sxs-lookup"><span data-stu-id="76847-192">**OnStartup** in `App.xaml.cs` is called with **Args** of "-ToastActivated"</span></span>
2. <span data-ttu-id="76847-193">**OnActivated** in Ihrer **NotificationActivator** wird aufgerufen</span><span class="sxs-lookup"><span data-stu-id="76847-193">**OnActivated** in your **NotificationActivator** is called</span></span>


### <a name="foreground-vs-background-activation"></a><span data-ttu-id="76847-194">Vordergrund- und Hintergrundaktivierung</span><span class="sxs-lookup"><span data-stu-id="76847-194">Foreground vs background activation</span></span>
<span data-ttu-id="76847-195">Für Desktop-Apps erfolgt die Vordergrund und Hintergrundaktivierung genauso – die COM-Aktivierung wird aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="76847-195">For desktop apps, foreground and background activation is handled identically - your COM activator is called.</span></span> <span data-ttu-id="76847-196">Je nach dem Code Ihrer App wird entschieden, ob ein Fenster angezeigt wird oder einfach einige Aufgaben ausgeführt werden und die Aktion anschließend beendet wird.</span><span class="sxs-lookup"><span data-stu-id="76847-196">It's up to your app's code to decide whether to show a window or to simply perform some work and then exit.</span></span> <span data-ttu-id="76847-197">Aus diesem Grund ändert die Angabe eines **ActivationType** im **Hintergrund** Ihres Popup-Inhalts nichts am Verhalten.</span><span class="sxs-lookup"><span data-stu-id="76847-197">Therefore, specifying an **ActivationType** of **Background** in your toast content doesn't change the behavior.</span></span>


## <a name="step-9-remove-and-manage-notifications"></a><span data-ttu-id="76847-198">Schritt9: Entfernen und Verwalten von Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="76847-198">Step 9: Remove and manage notifications</span></span>

<span data-ttu-id="76847-199">Das Entfernen und Verwalten von Benachrichtigungen ist identisch mit UWP-Apps.</span><span class="sxs-lookup"><span data-stu-id="76847-199">Removing and managing notifications is identical to UWP apps.</span></span> <span data-ttu-id="76847-200">Es wird jedoch empfohlen, dass Sie unsere Compat-Bibliothek verwenden, um eine **DesktopNotificationHistoryCompat** zu erhalten, damit Sie sich keine Gedanken über das Bereitstellen der AUMID machen müssen, wenn Sie die klassische Win32 verwenden.</span><span class="sxs-lookup"><span data-stu-id="76847-200">However, we recommend you use our compat library to obtain a **DesktopNotificationHistoryCompat** so you don't have to worry about providing the AUMID if you're using classic Win32.</span></span>

```csharp
// Remove the toast with tag "Message2"
DesktopNotificationManagerCompat.History.Remove("Message2");

// Clear all toasts
DesktopNotificationManagerCompat.History.Clear();
```


## <a name="step-10-deploying-and-debugging"></a><span data-ttu-id="76847-201">Schritt 10: Bereitstellen und Debuggen</span><span class="sxs-lookup"><span data-stu-id="76847-201">Step 10: Deploying and debugging</span></span>

<span data-ttu-id="76847-202">Wenn Sie die Desktop-Brücke-App bereitstellen und debuggen möchten, lesen Sie [Ausführen, Debuggen und Testen eine verpackten Desktop-App](/porting/desktop-to-uwp-debug.md).</span><span class="sxs-lookup"><span data-stu-id="76847-202">To deploy and debug your Desktop Bridge app, see [Run, debug, and test a packaged desktop app](/porting/desktop-to-uwp-debug.md).</span></span>

<span data-ttu-id="76847-203">Um eine klassische Win32-App bereitzustellen und zu verwalten, müssen Sie Ihrer App durch den Installer einmal vor dem Debuggen installieren, damit die Verknüpfung auf dem Startmenü mit AUMID und CLSID vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="76847-203">To deploy and debug your classic Win32 app, you must install your app through the installer once before debugging normally, so that the Start shortcut with your AUMID and CLSID is present.</span></span> <span data-ttu-id="76847-204">Nachdem die Verknüpfung auf dem Startmenü vorhanden ist, können Sie mithilfe von F5 in Visual Studio debuggen.</span><span class="sxs-lookup"><span data-stu-id="76847-204">After the Start shortcut is present, you can debug using F5 from Visual Studio.</span></span>

<span data-ttu-id="76847-205">Wenn Ihre Benachrichtigungen nicht einfach in Ihrer klassische Win32-App angezeigt werden (und keine Ausnahmen ausgelöst werden), bedeutet dies wahrscheinlich, dass die Verknüpfung im Startmenü nicht vorhanden ist (installieren Sie Ihre App über das Installationsprogramm), oder die AUMID, die Sie im Code verwendet haben, nicht der AUMID der Verknüpfung auf dem Startmenü entspricht.</span><span class="sxs-lookup"><span data-stu-id="76847-205">If your notifications simply fail to appear in your classic Win32 app (and no exceptions are thrown), that likely means the Start shortcut isn't present (install your app via the installer), or the AUMID you used in code doesn't match the AUMID in your Start shortcut.</span></span>

<span data-ttu-id="76847-206">Wenn Ihre Benachrichtigungen im Info-Center erscheinen aber nicht dort angezeigt werden (verschwinden, nachdem das Popup geschlossen ist) beibehalten werden nicht persistent angezeigt werden, bedeutet dies, dass Sie die den COM-Aktivator nicht ordnungsgemäß implementiert haben.</span><span class="sxs-lookup"><span data-stu-id="76847-206">If your notifications appear but aren't persisted in Action Center (disappearing after the popup is dismissed), that means you haven't implemented the COM activator correctly.</span></span>

<span data-ttu-id="76847-207">Wenn Sie sowohl Ihre Desktop-Brücke und die klassische Win32-App installiert haben, beachten Sie, dass die App Desktop-Brücke die klassische Win32-App bei der Behandlung von Popup-Aktivierungen ablöst.</span><span class="sxs-lookup"><span data-stu-id="76847-207">If you've installed both your Desktop Bridge and classic Win32 app, note that the Desktop Bridge app will supersede the classic Win32 app when handling toast activations.</span></span> <span data-ttu-id="76847-208">Dies bedeutet, dass Popups aus der klassische Win32-App beim Klicken auf die Desktop-Brücke-App gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="76847-208">That means that toasts from the classic Win32 app will still launch the Desktop Bridge app when clicked.</span></span> <span data-ttu-id="76847-209">Das Deinstallieren der App Desktop-Brücke setzt die Aktivierung auf die klassische Win32-App zurück.</span><span class="sxs-lookup"><span data-stu-id="76847-209">Uninstalling the Desktop Bridge app will revert activations back to the classic Win32 app.</span></span>


## <a name="known-issues"></a><span data-ttu-id="76847-210">Bekannte Probleme</span><span class="sxs-lookup"><span data-stu-id="76847-210">Known issues</span></span>

<span data-ttu-id="76847-211">**FIXED: Die App hat nach dem Klicken auf die Popupbenachrichtigung keinen Fokus**: In Build 15063 und früher wurden die Vordergrundrechte nicht auf Ihre Anwendung übertragen, wenn wir den COM-Server aktivierten.</span><span class="sxs-lookup"><span data-stu-id="76847-211">**FIXED: App doesn't become focused after clicking toast**: In builds 15063 and earlier, foreground rights weren't being transferred to your application when we activated the COM server.</span></span> <span data-ttu-id="76847-212">Aus diesem Grund führte Ihre App einfach einen Flash aus, bei dem Versuch, sie in den Vordergrund zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="76847-212">Therefore, your app would simply flash when you tried to move it to the foreground.</span></span> <span data-ttu-id="76847-213">Es gibt hierfür keine Problemumgehung.</span><span class="sxs-lookup"><span data-stu-id="76847-213">There was no workaround for this issue.</span></span> <span data-ttu-id="76847-214">Wir haben dies in Builds 16299 und höher behoben.</span><span class="sxs-lookup"><span data-stu-id="76847-214">We fixed this in builds 16299 and higher.</span></span>


## <a name="resources"></a><span data-ttu-id="76847-215">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="76847-215">Resources</span></span>

* [<span data-ttu-id="76847-216">Vollständiges Codebeispiel auf GitHub</span><span class="sxs-lookup"><span data-stu-id="76847-216">Full code sample on GitHub</span></span>](https://github.com/WindowsNotifications/desktop-toasts)
* [<span data-ttu-id="76847-217">Popupbenachrichtigungen über Desktop-Apps</span><span class="sxs-lookup"><span data-stu-id="76847-217">Toast notifications from desktop apps</span></span>](toast-desktop-apps.md)
* [<span data-ttu-id="76847-218">Dokumentation zu Popupinhalt</span><span class="sxs-lookup"><span data-stu-id="76847-218">Toast content documentation</span></span>](adaptive-interactive-toasts.md)

