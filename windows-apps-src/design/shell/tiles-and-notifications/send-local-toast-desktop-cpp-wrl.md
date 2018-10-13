---
author: andrewleader
Description: Learn how Win32 C++ WRL apps can send local toast notifications and handle the user clicking the toast.
title: Senden von Popupbenachrichtigungen über C++ WRL-Apps
label: Send a local toast notification from desktop C++ WRL apps
template: detail.hbs
ms.author: mijacobs
ms.date: 03/7/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, win32, Desktop, Popupbenachrichtigungen, Popup senden, lokale Popupbenachrichtigungen senden, Desktop Bridge, C++, cpp, cplusplus, WRL
ms.localizationpriority: medium
ms.openlocfilehash: a6134e65a27563f96c03880dea026bed11f46641
ms.sourcegitcommit: d10fb9eb5f75f2d10e1c543a177402b50fe4019e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "4573497"
---
# <a name="send-a-local-toast-notification-from-desktop-c-wrl-apps"></a><span data-ttu-id="63373-103">Senden von Popupbenachrichtigungen über C++ WRL-Apps</span><span class="sxs-lookup"><span data-stu-id="63373-103">Send a local toast notification from desktop C++ WRL apps</span></span>

<span data-ttu-id="63373-104">Desktop-Apps (Desktop-Brücke und klassische Win32) können interaktive Popupbenachrichtigungen wie Universelle Windows-Plattform (UWP)-Apps senden.</span><span class="sxs-lookup"><span data-stu-id="63373-104">Desktop apps (both Desktop Bridge and classic Win32) can send interactive toast notifications just like Universal Windows Platform (UWP) apps.</span></span> <span data-ttu-id="63373-105">Es gibt jedoch einige besondere Schritte für Desktop-Apps mit anderen Aktivierungsschematas und dem potenziellen Mangel der Paketidentität, wenn Sie die Desktop-Brücke nicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="63373-105">However, there are a few special steps for desktop apps due to the different activation schemes and the potential lack of package identity if you're not using the Desktop Bridge.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="63373-106">Wenn Sie eine UWP-App entwickeln, finden Sie Informationen in der [UWP-Dokumentation](send-local-toast.md).</span><span class="sxs-lookup"><span data-stu-id="63373-106">If you're writing a UWP app, please see the [UWP documentation](send-local-toast.md).</span></span> <span data-ttu-id="63373-107">Bei anderen Desktop Sprachen finden Sie Informationen unter [Desktop C#](send-local-toast-desktop.md).</span><span class="sxs-lookup"><span data-stu-id="63373-107">For other desktop languages, please see [Desktop C#](send-local-toast-desktop.md).</span></span>


## <a name="step-1-enable-the-windows-10-sdk"></a><span data-ttu-id="63373-108">Schritt1: Aktivieren von Windows10 SDK</span><span class="sxs-lookup"><span data-stu-id="63373-108">Step 1: Enable the Windows 10 SDK</span></span>

<span data-ttu-id="63373-109">Wenn Sie Windows10 SDK nicht für Ihre Win32-App aktiviert haben, müssen Sie dies zuerst tun.</span><span class="sxs-lookup"><span data-stu-id="63373-109">If you haven't enabled the Windows 10 SDK for your Win32 app, you must do that first.</span></span> <span data-ttu-id="63373-110">Es sind einige wichtige Schritte erforderlich...</span><span class="sxs-lookup"><span data-stu-id="63373-110">There are a few key steps...</span></span>

1. <span data-ttu-id="63373-111">Hinzufügen von `runtimeobject.lib` auf **Zusätzliche Abhängigkeiten**</span><span class="sxs-lookup"><span data-stu-id="63373-111">Add `runtimeobject.lib` to **Additional Dependencies**</span></span>
2. <span data-ttu-id="63373-112">Aufrufen von Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="63373-112">Target the Windows 10 SDK</span></span>

<span data-ttu-id="63373-113">Klicken Sie mit der rechten Maustaste auf Ihr Projekt, und wählen Sie dann **Eigenschaften** aus.</span><span class="sxs-lookup"><span data-stu-id="63373-113">Right click your project and select **Properties**.</span></span>

<span data-ttu-id="63373-114">Wählen Sie im oberen **Konfigurationsmenü** **alle Konfigurationen** aus, damit die folgende Änderung auf das Debuggen und die Freigabe angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="63373-114">In the top **Configuration** menu, select **All Configurations** so that the following change is applied to both Debug and Release.</span></span>

<span data-ttu-id="63373-115">Fügen Sie unter **Linker-> Eingabe** `runtimeobject.lib` den **zusätzlichen Abhängigkeiten** hinzu.</span><span class="sxs-lookup"><span data-stu-id="63373-115">Under **Linker -> Input**, add `runtimeobject.lib` to the **Additional Dependencies**.</span></span>

<span data-ttu-id="63373-116">Unter **Allgemein**, stellen Sie sicher, dass die **Windows SDK-Version** auf 10.0 oder höher festgelegt ist (nicht Windows8.1).</span><span class="sxs-lookup"><span data-stu-id="63373-116">Then under **General**, make sure that the **Windows SDK Version** is set to something 10.0 or higher (not Windows 8.1).</span></span>


## <a name="step-2-copy-compat-library-code"></a><span data-ttu-id="63373-117">Schritt2: Kopieren des Compat-Bibliothekscodes</span><span class="sxs-lookup"><span data-stu-id="63373-117">Step 2: Copy compat library code</span></span>

<span data-ttu-id="63373-118">Kopieren Sie [DesktopNotificationManagerCompat.h](https://raw.githubusercontent.com/WindowsNotifications/desktop-toasts/master/CPP-WRL/DesktopToastsCppWrlApp/DesktopNotificationManagerCompat.h) und [DesktopNotificationManagerCompat.cpp](https://raw.githubusercontent.com/WindowsNotifications/desktop-toasts/master/CPP-WRL/DesktopToastsCppWrlApp/DesktopNotificationManagerCompat.cpp) von GitHub-Datei in Ihr Projekt.</span><span class="sxs-lookup"><span data-stu-id="63373-118">Copy the [DesktopNotificationManagerCompat.h](https://raw.githubusercontent.com/WindowsNotifications/desktop-toasts/master/CPP-WRL/DesktopToastsCppWrlApp/DesktopNotificationManagerCompat.h) and [DesktopNotificationManagerCompat.cpp](https://raw.githubusercontent.com/WindowsNotifications/desktop-toasts/master/CPP-WRL/DesktopToastsCppWrlApp/DesktopNotificationManagerCompat.cpp) file from GitHub into your project.</span></span> <span data-ttu-id="63373-119">Die Compat-Bibliothek abstrahiert einen Großteil der Komplexität der Desktop-Benachrichtigungen.</span><span class="sxs-lookup"><span data-stu-id="63373-119">The compat library abstracts much of the complexity of desktop notifications.</span></span> <span data-ttu-id="63373-120">Die folgenden Anweisungen erfordern die Compat-Bibliothek.</span><span class="sxs-lookup"><span data-stu-id="63373-120">The following instructions require the compat library.</span></span>

<span data-ttu-id="63373-121">Wenn Sie vorkompilierte Header verwenden, stellen Sie sicher, dass `#include "stdafx.h"` als erste Zeile in der Datei DesktopNotificationManagerCompat.cpp erscheint.</span><span class="sxs-lookup"><span data-stu-id="63373-121">If you're using precompiled headers, make sure to `#include "stdafx.h"` as the first line of the DesktopNotificationManagerCompat.cpp file.</span></span>


## <a name="step-3-include-the-header-files-and-namespaces"></a><span data-ttu-id="63373-122">Schritt3: Fügen Sie Headerdateien und Namespaces hinzu</span><span class="sxs-lookup"><span data-stu-id="63373-122">Step 3: Include the header files and namespaces</span></span>

<span data-ttu-id="63373-123">Fügen Sie die Headerdatei der Compat-Bibliothek und die Headerdatei und den Namespaces hinzu, die im Zusammenhang mit UWP-Popup-APIs verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="63373-123">Include the compat library header file, and the header files and namespaces related to using the UWP toast APIs.</span></span>

```cpp
#include "DesktopNotificationManagerCompat.h"
#include "NotificationActivationCallback.h"
#include <windows.ui.notifications.h>

using namespace ABI::Windows::Data::Xml::Dom;
using namespace ABI::Windows::UI::Notifications;
using namespace Microsoft::WRL;
```


## <a name="step-4-implement-the-activator"></a><span data-ttu-id="63373-124">Schritt 4: Implementieren des Aktivators</span><span class="sxs-lookup"><span data-stu-id="63373-124">Step 4: Implement the activator</span></span>

<span data-ttu-id="63373-125">Sie müssen einen Handler für die Popup-Aktivierung implementieren, damit, wenn der Benutzer auf das Popup klickt, Ihre App eine Aktion ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="63373-125">You must impelment a handler for toast activation, so that when the user clicks on your toast, your app can do something.</span></span> <span data-ttu-id="63373-126">Dies ist erforderlich für das Popup, damit es im Info-Center beibehalten wird (da auf das Popup Tage später geklickt werden kann, wenn die App geschlossen ist).</span><span class="sxs-lookup"><span data-stu-id="63373-126">This is required for your toast to persist in Action Center (since the toast could be clicked days later when your app is closed).</span></span> <span data-ttu-id="63373-127">Diese Klasse kann an eine beliebige Stelle in Ihrem Projekt platziert werden.</span><span class="sxs-lookup"><span data-stu-id="63373-127">This class can be placed anywhere in your project.</span></span>

<span data-ttu-id="63373-128">Implementieren Sie die **INotificationActivationCallback**-Schnittstelle wie folgt, einschließlich der UUID, und rufen Sie auch **CoCreatableClass** auf, um die Klasse als COM-erstellbar zu kennzeichnen.</span><span class="sxs-lookup"><span data-stu-id="63373-128">Implement the **INotificationActivationCallback** interface as seen below, including a UUID, and also call **CoCreatableClass** to flag your class as COM creatable.</span></span> <span data-ttu-id="63373-129">Erstellen Sie mithilfe einer der vielen online GUID-Generatoren eine eindeutige GUID für die UUID.</span><span class="sxs-lookup"><span data-stu-id="63373-129">For your UUID, create a unique GUID using one of the many online GUID generators.</span></span> <span data-ttu-id="63373-130">Durch diese GUID CLSID (Klassen-ID) weiß das Info-Center, welche Klasse für COM aktiviert werden soll.</span><span class="sxs-lookup"><span data-stu-id="63373-130">This GUID CLSID (class identifier) is how Action Center knows what class to COM activate.</span></span>

```cpp
// The UUID CLSID must be unique to your app. Create a new GUID if copying this code.
class DECLSPEC_UUID("replaced-with-your-guid-C173E6ADF0C3") NotificationActivator WrlSealed WrlFinal
    : public RuntimeClass<RuntimeClassFlags<ClassicCom>, INotificationActivationCallback>
{
public:
    virtual HRESULT STDMETHODCALLTYPE Activate(
        _In_ LPCWSTR appUserModelId,
        _In_ LPCWSTR invokedArgs,
        _In_reads_(dataCount) const NOTIFICATION_USER_INPUT_DATA* data,
        ULONG dataCount) override
    {
        // TODO: Handle activation
    }
};

// Flag class as COM creatable
CoCreatableClass(NotificationActivator);
```


## <a name="step-5-register-with-notification-platform"></a><span data-ttu-id="63373-131">Schritt5: Registrieren mit der Benachrichtigungsplattform</span><span class="sxs-lookup"><span data-stu-id="63373-131">Step 5: Register with notification platform</span></span>

<span data-ttu-id="63373-132">Anschließend müssen Sie eine Registrierung mit der Benachrichtigungsplattform durchführen.</span><span class="sxs-lookup"><span data-stu-id="63373-132">Then, you must register with the notification platform.</span></span> <span data-ttu-id="63373-133">Es sind unterschiedliche Schritte erforderlich, je nachdem, ob Sie die Desktop-Brücke oder klassische Win32 verwenden.</span><span class="sxs-lookup"><span data-stu-id="63373-133">There are different steps depending on whether you are using the Desktop Bridge or classic Win32.</span></span> <span data-ttu-id="63373-134">Wenn Sie beide unterstützen, müssen Sie beide Schritte durchführen (der Code bleibt allerdings gleich, die Bibliothek führt die Verzweigung für Sie durch!).</span><span class="sxs-lookup"><span data-stu-id="63373-134">If you support both, you must do both steps (however, no need to fork your code, our library handles that for you!).</span></span>


### <a name="desktop-bridge"></a><span data-ttu-id="63373-135">Desktop-Brücke</span><span class="sxs-lookup"><span data-stu-id="63373-135">Desktop Bridge</span></span>

<span data-ttu-id="63373-136">Bei Verwendung der Desktop-Brücke (oder wenn Sie beide Modi unterstützen), fügen Sie Ihrem **Package.appxmanifest** hinzu:</span><span class="sxs-lookup"><span data-stu-id="63373-136">If you're using Desktop Bridge (or if you support both), in your **Package.appxmanifest**, add:</span></span>

1. <span data-ttu-id="63373-137">Deklaration für **Xmlns:com**</span><span class="sxs-lookup"><span data-stu-id="63373-137">Declaration for **xmlns:com**</span></span>
2. <span data-ttu-id="63373-138">Deklaration für **xmlns:desktop**</span><span class="sxs-lookup"><span data-stu-id="63373-138">Declaration for **xmlns:desktop**</span></span>
3. <span data-ttu-id="63373-139">Im **IgnorableNamespaces**-Attribut **com** und **desktop**</span><span class="sxs-lookup"><span data-stu-id="63373-139">In the **IgnorableNamespaces** attribute, **com** and **desktop**</span></span>
4. <span data-ttu-id="63373-140">**com:Extension** für den COM-Aktivator mithilfe der GUID aus Schritt 4.</span><span class="sxs-lookup"><span data-stu-id="63373-140">**com:Extension** for the COM activator using the GUID from step #4.</span></span> <span data-ttu-id="63373-141">Stellen Sie sicher, dass `Arguments="-ToastActivated"` hinzugefügt wurde, damit Sie wissen, dass der Start über ein Popup ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="63373-141">Be sure to include the `Arguments="-ToastActivated"` so that you know your launch was from a toast</span></span>
5. <span data-ttu-id="63373-142">**desktop:Extension** für **windows.toastNotificationActivation**, um den Popup-Aktivator CLSID zu deklarieren (der GUID aus Schritt #4).</span><span class="sxs-lookup"><span data-stu-id="63373-142">**desktop:Extension** for **windows.toastNotificationActivation** to declare your toast activator CLSID (the GUID from step #4).</span></span>

**<span data-ttu-id="63373-143">Package.appxmanifest</span><span class="sxs-lookup"><span data-stu-id="63373-143">Package.appxmanifest</span></span>**

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


### <a name="classic-win32"></a><span data-ttu-id="63373-144">Klassisch Win32</span><span class="sxs-lookup"><span data-stu-id="63373-144">Classic Win32</span></span>

<span data-ttu-id="63373-145">Wenn Sie eine klassische Win32 verwenden (oder wenn Sie beide Modi unterstützen), müssen Sie Ihre Anwendungsbenutzermodell-ID (AUMID) und den Popupbenachrichtigungs-Aktivator CLSID (der GUID aus Schritt4 #) auf der App-Verknüpfung im Startmenü deklarieren.</span><span class="sxs-lookup"><span data-stu-id="63373-145">If you're using classic Win32 (or if you support both), you have to declare your Application User Model ID (AUMID) and toast activator CLSID (the GUID from step #4) on your app's shortcut in Start.</span></span>

<span data-ttu-id="63373-146">Wählen Sie einen eindeutigen AUMID, der Ihrer Win32-App identifiziert.</span><span class="sxs-lookup"><span data-stu-id="63373-146">Pick a unique AUMID that will identify your Win32 app.</span></span> <span data-ttu-id="63373-147">Dies geschieht in der Regel in Form von [Firmenname].[AppName], es sollte allerdings in allen Apps eindeutig sein (fügen Sie Ziffern am Ende hinzu).</span><span class="sxs-lookup"><span data-stu-id="63373-147">This is typically in the form of [CompanyName].[AppName], but you want to ensure this is unique across all apps (feel free to add some digits at the end).</span></span>

#### <a name="step-51-wix-installer"></a><span data-ttu-id="63373-148">Schritt 5.1: WiX Installer</span><span class="sxs-lookup"><span data-stu-id="63373-148">Step 5.1: WiX Installer</span></span>

<span data-ttu-id="63373-149">Wenn Sie WiX als Installer verwenden, bearbeiten Sie die **Product.wxs**-Datei, um dem Startmenü zwei Verknüpfungseigenschaften hinzuzufügen, wie unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="63373-149">If you're using WiX for your installer, edit the **Product.wxs** file to add the two shortcut properties to your Start menu shortcut as seen below.</span></span> <span data-ttu-id="63373-150">Stellen Sie sicher, dass Ihre GUID aus Schritt4 # in `{}` eingeschlossen ist, wie unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="63373-150">Be sure that your GUID from step #4 is enclosed in `{}` as seen below.</span></span>

**<span data-ttu-id="63373-151">Product.wxs</span><span class="sxs-lookup"><span data-stu-id="63373-151">Product.wxs</span></span>**

```xml
<Shortcut Id="ApplicationStartMenuShortcut" Name="Wix Sample" Description="Wix Sample" Target="[INSTALLFOLDER]WixSample.exe" WorkingDirectory="INSTALLFOLDER">
                    
    <!--AUMID-->
    <ShortcutProperty Key="System.AppUserModel.ID" Value="YourCompany.YourApp"/>
    
    <!--COM CLSID-->
    <ShortcutProperty Key="System.AppUserModel.ToastActivatorCLSID" Value="{replaced-with-your-guid-C173E6ADF0C3}"/>
    
</Shortcut>
```

> [!IMPORTANT]
> <span data-ttu-id="63373-152">Um Benachrichtigungen tatsächlich verwenden zu können, müssen Sie Ihrer App durch den Installer einmal vor dem Debuggen installieren, damit die Verknüpfung auf dem Startmenü mit AUMID und CLSID vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="63373-152">In order to actually use notifications, you must install your app through the installer once before debugging normally, so that the Start shortcut with your AUMID and CLSID is present.</span></span> <span data-ttu-id="63373-153">Nachdem die Verknüpfung auf dem Startmenü vorhanden ist, können Sie mithilfe von F5 in Visual Studio debuggen.</span><span class="sxs-lookup"><span data-stu-id="63373-153">After the Start shortcut is present, you can debug using F5 from Visual Studio.</span></span>


#### <a name="step-52-register-aumid-and-com-server"></a><span data-ttu-id="63373-154">Schritt5.2: Registrieren des AUMID und COM-Servers</span><span class="sxs-lookup"><span data-stu-id="63373-154">Step 5.2: Register AUMID and COM server</span></span>

<span data-ttu-id="63373-155">Rufen Sie unabhängig vom Installer im App Startcode (vor dem Aufrufen der Benachrichtigungs-APIs), die **RegisterAumidAndComServer**-Methode auf, und geben Sie die Benachrichtigungs-Aktivator-Klasse von Schritt 4 und die oben verwendete AUMID an.</span><span class="sxs-lookup"><span data-stu-id="63373-155">Then, regardless of your installer, in your app's startup code (before calling any notification APIs), call the **RegisterAumidAndComServer** method, specifying your notification activator class from step #4 and your AUMID used above.</span></span>

```cpp
// Register AUMID and COM server (for Desktop Bridge apps, this no-ops)
hr = DesktopNotificationManagerCompat::RegisterAumidAndComServer(L"YourCompany.YourApp", __uuidof(NotificationActivator));
```

<span data-ttu-id="63373-156">Wenn Desktop-Brücke und klassisches Win32 unterstützt werden, können Sie diese Methode unabhängig davon aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="63373-156">If you support both Desktop Bridge and classic Win32, feel free to call this method regardless.</span></span> <span data-ttu-id="63373-157">Wenn Sie die Methode mit der Desktop-Brücke ausführen, wird sie sofort zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="63373-157">If you're running under Desktop Bridge, this method will simply return immediately.</span></span> <span data-ttu-id="63373-158">Sie müssen den Code nicht verzweigen.</span><span class="sxs-lookup"><span data-stu-id="63373-158">There's no need to fork your code.</span></span>

<span data-ttu-id="63373-159">Mit dieser Methode können Sie Compat-APIs zum Senden und Verwalten von Benachrichtigungen aufrufen, ohne ständig die AUMID angeben zu müssen.</span><span class="sxs-lookup"><span data-stu-id="63373-159">This method allows you to call the compat APIs to send and manage notifications without having to constantly provide your AUMID.</span></span> <span data-ttu-id="63373-160">Es fügt ebenfalls den LocalServer32-Schlüssel für den COM-Server hinzu.</span><span class="sxs-lookup"><span data-stu-id="63373-160">And it inserts the LocalServer32 registry key for the COM server.</span></span>


## <a name="step-6-register-com-activator"></a><span data-ttu-id="63373-161">Schritt 6: Registrieren des COM-Aktivators</span><span class="sxs-lookup"><span data-stu-id="63373-161">Step 6: Register COM activator</span></span>

<span data-ttu-id="63373-162">Für Desktop-Brücken und klassische Win32-Apps müssen Sie Ihren Benachrichtigung-Aktivatortyp registrieren, damit Sie Popupaktivierungen behandeln können.</span><span class="sxs-lookup"><span data-stu-id="63373-162">For both Desktop Bridge and classic Win32 apps, you must register your notification activator type, so that you can handle toast activations.</span></span>

<span data-ttu-id="63373-163">Rufen Sie im Startcode Ihrer App, die folgende **RegisterActivator**-Methode auf.</span><span class="sxs-lookup"><span data-stu-id="63373-163">In your app's startup code, call the following **RegisterActivator** method.</span></span> <span data-ttu-id="63373-164">Dies muss in der Reihenfolge aufgerufen werden, in der Sie alle Popupaktivierungen erhalten.</span><span class="sxs-lookup"><span data-stu-id="63373-164">This must be called in order for you to receive any toast activations.</span></span>

```cpp
// Register activator type
hr = DesktopNotificationManagerCompat::RegisterActivator();
```


## <a name="step-7-send-a-notification"></a><span data-ttu-id="63373-165">Schritt 7: Senden einer Benachrichtigung</span><span class="sxs-lookup"><span data-stu-id="63373-165">Step 7: Send a notification</span></span>

<span data-ttu-id="63373-166">Das Senden einer Benachrichtigung ist für UWP-Apps identisch, außer dass Sie **DesktopNotificationManagerCompat** zum Erstellen eines **ToastNotifier** verwenden.</span><span class="sxs-lookup"><span data-stu-id="63373-166">Sending a notification is identical to UWP apps, except that you will use **DesktopNotificationManagerCompat** to create a **ToastNotifier**.</span></span> <span data-ttu-id="63373-167">Die Compat-Bibliothek behandelt den Unterschied zwischen Desktop-Brücke und klassischer Win32 automatisch, damit Sie keinen Code verzweigen müssen.</span><span class="sxs-lookup"><span data-stu-id="63373-167">The compat library automatically handles the difference between Desktop Bridge and classic Win32 so you do not have to fork your code.</span></span> <span data-ttu-id="63373-168">Für klassisches Win32 speichert die Compat-Bibliothek Ihre AUMID, die Sie beim Aufrufen von **RegisterAumidAndComServer** bereitgestellt haben, damit Sie sich nicht die AUMID kümmern müssen, wann Sie diese bereitstellen und wann nicht.</span><span class="sxs-lookup"><span data-stu-id="63373-168">For classic Win32, the compat library caches your AUMID you provided when calling **RegisterAumidAndComServer** so that you don't need to worry about when to provide or not provide the AUMID.</span></span>

<span data-ttu-id="63373-169">Stellen Sie sicher, dass Sie den unten angezeigten **ToastGeneric** verwenden, da ältere Vorlagen der Windows8.1 Popupbenachrichtigungen nicht den COM-Benachrichtigungs-Aktivator aktivieren, den Sie in Schritt4 # erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="63373-169">Make sure you use the **ToastGeneric** binding as seen below since the legacy Windows 8.1 toast notification templates will not activate your COM notification activator you created in step #4.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="63373-170">HTTP-Bilder werden nur in Desktop-Brücken-Apps unterstützt, die die Internetfunktion im Manifest haben.</span><span class="sxs-lookup"><span data-stu-id="63373-170">Http images are only supported in Desktop Bridge apps that have the internet capability in their manifest.</span></span> <span data-ttu-id="63373-171">Klassische Win32-Apps unterstützen keine HTTP-Bilder. Sie müssen das Bild in die lokale App-Daten herunterladen und lokal darauf verweisen.</span><span class="sxs-lookup"><span data-stu-id="63373-171">Classic Win32 apps do not support http images; you must download the image to your local app data and reference it locally.</span></span>

```cpp
// Construct XML
ComPtr<IXmlDocument> doc;
hr = DesktopNotificationManagerCompat::CreateXmlDocumentFromString(
    L"<toast><visual><binding template='ToastGeneric'><text>Hello world</text></binding></visual></toast>",
    &doc);
if (SUCCEEDED(hr))
{
    // See full code sample to learn how to inject dynamic text, buttons, and more

    // Create the notifier
    // Classic Win32 apps MUST use the compat method to create the notifier
    ComPtr<IToastNotifier> notifier;
    hr = DesktopNotificationManagerCompat::CreateToastNotifier(&notifier);
    if (SUCCEEDED(hr))
    {
        // Create the notification itself (using helper method from compat library)
        ComPtr<IToastNotification> toast;
        hr = DesktopNotificationManagerCompat::CreateToastNotification(doc, &toast);
        if (SUCCEEDED(hr))
        {
            // And show it!
            hr = notifier->Show(toast.Get());
        }
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="63373-172">Klassische Win32-Apps können keine älteren Popupvorlagen (z.B. ToastText02) verwenden.</span><span class="sxs-lookup"><span data-stu-id="63373-172">Classic Win32 apps cannot use legacy toast templates (like ToastText02).</span></span> <span data-ttu-id="63373-173">Die Aktivierung älterer Vorlagen schlägt fehl, wenn die COM-CLSID angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="63373-173">Activation of the legacy templates will fail when the COM CLSID is specified.</span></span> <span data-ttu-id="63373-174">Wie oben erwähnt müssen Sie die Windows10 ToastGeneric-Vorlagen verwenden.</span><span class="sxs-lookup"><span data-stu-id="63373-174">You must use the Windows 10 ToastGeneric templates as seen above.</span></span>


## <a name="step-8-handling-activation"></a><span data-ttu-id="63373-175">Schritt 8: Behandeln der Aktivierung</span><span class="sxs-lookup"><span data-stu-id="63373-175">Step 8: Handling activation</span></span>

<span data-ttu-id="63373-176">Wenn der Benutzer auf das Popup oder auf Schaltflächen im Popup klickt, wird die **Activate**-Methode Ihrer **NotificationActivator**-Klasse aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="63373-176">When the user clicks on your toast, or buttons in the toast, the **Activate** method of your **NotificationActivator** class is invoked.</span></span>

<span data-ttu-id="63373-177">Innerhalb der Activate-Methode können Sie die Argumente analysieren, die Sie im Popup angegeben haben und die Benutzereingabe abrufen, die der Benutzer eingegeben oder ausgewählt hat und dann entsprechend Ihre App aktivieren.</span><span class="sxs-lookup"><span data-stu-id="63373-177">Inside the Activate method, you can parse the args that you specified in the toast and obtain the user input that the user typed or selected, and then activate your app accordingly.</span></span>

> [!NOTE]
> <span data-ttu-id="63373-178">Die **Activate**-Methode wird in einem separaten Thread aus dem Hauptthread aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="63373-178">The **Activate** method is called on a separte thread from your main thread.</span></span>

```cpp
// The GUID must be unique to your app. Create a new GUID if copying this code.
class DECLSPEC_UUID("replaced-with-your-guid-C173E6ADF0C3") NotificationActivator WrlSealed WrlFinal
    : public RuntimeClass<RuntimeClassFlags<ClassicCom>, INotificationActivationCallback>
{
public: 
    virtual HRESULT STDMETHODCALLTYPE Activate(
        _In_ LPCWSTR appUserModelId,
        _In_ LPCWSTR invokedArgs,
        _In_reads_(dataCount) const NOTIFICATION_USER_INPUT_DATA* data,
        ULONG dataCount) override
    {
        std::wstring arguments(invokedArgs);
        HRESULT hr = S_OK;

        // Background: Quick reply to the conversation
        if (arguments.find(L"action=reply") == 0)
        {
            // Get the response user typed.
            // We know this is first and only user input since our toasts only have one input
            LPCWSTR response = data[0].Value;

            hr = DesktopToastsApp::SendResponse(response);
        }

        else
        {
            // The remaining scenarios are foreground activations,
            // so we first make sure we have a window open and in foreground
            hr = DesktopToastsApp::GetInstance()->OpenWindowIfNeeded();
            if (SUCCEEDED(hr))
            {
                // Open the image
                if (arguments.find(L"action=viewImage") == 0)
                {
                    hr = DesktopToastsApp::GetInstance()->OpenImage();
                }

                // Open the app itself
                // User might have clicked on app title in Action Center which launches with empty args
                else
                {
                    // Nothing to do, already launched
                }
            }
        }

        if (FAILED(hr))
        {
            // Log failed HRESULT
        }

        return S_OK;
    }

    ~NotificationActivator()
    {
        // If we don't have window open
        if (!DesktopToastsApp::GetInstance()->HasWindow())
        {
            // Exit (this is for background activation scenarios)
            exit(0);
        }
    }
};

// Flag class as COM creatable
CoCreatableClass(NotificationActivator);
```

<span data-ttu-id="63373-179">Si sollten in der WinMain-Funktion festlegen, ob Sie über ein Popup oder nicht gestartet werden soll, um einen ordnungsgemäßen Start zu unterstützen, während die App geschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="63373-179">To properly support being launched while your app is closed, in your WinMain function, you'll want to determine whether you're being launched from a toast or not.</span></span> <span data-ttu-id="63373-180">Wenn dies von einem Popup gestartet wird, wird ein Start-Argument von "-ToastActivated" gesendet.</span><span class="sxs-lookup"><span data-stu-id="63373-180">If launched from a toast, there will be a launch arg of "-ToastActivated".</span></span> <span data-ttu-id="63373-181">Sobald dies angezeigt wird, sollten Sie das Ausführen aller normaler Aktivierungscodes beenden, und den Start von **NotificationActivator**-Fenstern zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="63373-181">When you see this, you should stop performing any normal launch activation code, and allow your **NotificationActivator** to handle launching windows if needed.</span></span>

```cpp
// Main function
int WINAPI wWinMain(_In_ HINSTANCE hInstance, _In_opt_ HINSTANCE, _In_ LPWSTR cmdLineArgs, _In_ int)
{
    RoInitializeWrapper winRtInitializer(RO_INIT_MULTITHREADED);

    HRESULT hr = winRtInitializer;
    if (SUCCEEDED(hr))
    {
        // Register AUMID and COM server (for Desktop Bridge apps, this no-ops)
        hr = DesktopNotificationManagerCompat::RegisterAumidAndComServer(L"WindowsNotifications.DesktopToastsCpp", __uuidof(NotificationActivator));
        if (SUCCEEDED(hr))
        {
            // Register activator type
            hr = DesktopNotificationManagerCompat::RegisterActivator();
            if (SUCCEEDED(hr))
            {
                DesktopToastsApp app;
                app.SetHInstance(hInstance);

                std::wstring cmdLineArgsStr(cmdLineArgs);

                // If launched from toast
                if (cmdLineArgsStr.find(TOAST_ACTIVATED_LAUNCH_ARG) != std::string::npos)
                {
                    // Let our NotificationActivator handle activation
                }

                else
                {
                    // Otherwise launch like normal
                    app.Initialize(hInstance);
                }

                app.RunMessageLoop();
            }
        }
    }

    return SUCCEEDED(hr);
}
```


### <a name="activation-sequence-of-events"></a><span data-ttu-id="63373-182">Aktivierungssequenz von Ereignissen</span><span class="sxs-lookup"><span data-stu-id="63373-182">Activation sequence of events</span></span>

<span data-ttu-id="63373-183">Die Aktivierungssequenz wie folgt...</span><span class="sxs-lookup"><span data-stu-id="63373-183">The activation sequence is the following...</span></span>

<span data-ttu-id="63373-184">Wenn Ihre App bereits ausgeführt wird:</span><span class="sxs-lookup"><span data-stu-id="63373-184">If your app is already running:</span></span>

1. <span data-ttu-id="63373-185">**Activate** in Ihrer **NotificationActivator** wird aufgerufen</span><span class="sxs-lookup"><span data-stu-id="63373-185">**Activate** in your **NotificationActivator** is called</span></span>

<span data-ttu-id="63373-186">Wenn Ihre App nicht ausgeführt wird:</span><span class="sxs-lookup"><span data-stu-id="63373-186">If your app is not running:</span></span>

1. <span data-ttu-id="63373-187">Ihre App wird über eine exe-Datei gestartet, und Sie erhalten ein Befehlszeilenargument von "-ToastActivated"</span><span class="sxs-lookup"><span data-stu-id="63373-187">Your app is EXE launched, you get a command line args of "-ToastActivated"</span></span>
2. <span data-ttu-id="63373-188">**Activate** in Ihrer **NotificationActivator** wird aufgerufen</span><span class="sxs-lookup"><span data-stu-id="63373-188">**Activate** in your **NotificationActivator** is called</span></span>


### <a name="foreground-vs-background-activation"></a><span data-ttu-id="63373-189">Vordergrund- und Hintergrundaktivierung</span><span class="sxs-lookup"><span data-stu-id="63373-189">Foreground vs background activation</span></span>
<span data-ttu-id="63373-190">Für Desktop-Apps erfolgt die Vordergrund und Hintergrundaktivierung genauso – die COM-Aktivierung wird aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="63373-190">For desktop apps, foreground and background activation is handled identically - your COM activator is called.</span></span> <span data-ttu-id="63373-191">Je nach dem Code Ihrer App wird entschieden, ob ein Fenster angezeigt wird oder einfach einige Aufgaben ausgeführt werden und die Aktion anschließend beendet wird.</span><span class="sxs-lookup"><span data-stu-id="63373-191">It's up to your app's code to decide whether to show a window or to simply perform some work and then exit.</span></span> <span data-ttu-id="63373-192">Aus diesem Grund ändert die Angabe eines **activationType** im **Hintergrund** Ihres Popup-Inhalts nichts am Verhalten.</span><span class="sxs-lookup"><span data-stu-id="63373-192">Therefore, specifying an **activationType** of **background** in your toast content doesn't change the behavior.</span></span>


## <a name="step-9-remove-and-manage-notifications"></a><span data-ttu-id="63373-193">Schritt9: Entfernen und Verwalten von Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="63373-193">Step 9: Remove and manage notifications</span></span>

<span data-ttu-id="63373-194">Das Entfernen und Verwalten von Benachrichtigungen ist identisch mit UWP-Apps.</span><span class="sxs-lookup"><span data-stu-id="63373-194">Removing and managing notifications is identical to UWP apps.</span></span> <span data-ttu-id="63373-195">Es wird jedoch empfohlen, dass Sie unsere Compat-Bibliothek verwenden, um eine **DesktopNotificationHistoryCompat** zu erhalten, damit Sie sich keine Gedanken über das Bereitstellen der AUMID machen müssen, wenn Sie die klassische Win32 verwenden.</span><span class="sxs-lookup"><span data-stu-id="63373-195">However, we recommend you use our compat library to obtain a **DesktopNotificationHistoryCompat** so you don't have to worry about providing the AUMID if you're using classic Win32.</span></span>

```cpp
std::unique_ptr<DesktopNotificationHistoryCompat> history;
auto hr = DesktopNotificationManagerCompat::get_History(&history);
if (SUCCEEDED(hr))
{
    // Remove a specific toast
    hr = history->Remove(L"Message2");

    // Clear all toasts
    hr = history->Clear();
}
```


## <a name="step-10-deploying-and-debugging"></a><span data-ttu-id="63373-196">Schritt 10: Bereitstellen und Debuggen</span><span class="sxs-lookup"><span data-stu-id="63373-196">Step 10: Deploying and debugging</span></span>

<span data-ttu-id="63373-197">Wenn Sie die Desktop-Brücke-App bereitstellen und debuggen möchten, lesen Sie [Ausführen, Debuggen und Testen eine verpackten Desktop-App](/porting/desktop-to-uwp-debug.md).</span><span class="sxs-lookup"><span data-stu-id="63373-197">To deploy and debug your Desktop Bridge app, see [Run, debug, and test a packaged desktop app](/porting/desktop-to-uwp-debug.md).</span></span>

<span data-ttu-id="63373-198">Um eine klassische Win32-App bereitzustellen und zu verwalten, müssen Sie Ihrer App durch den Installer einmal vor dem Debuggen installieren, damit die Verknüpfung auf dem Startmenü mit AUMID und CLSID vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="63373-198">To deploy and debug your classic Win32 app, you must install your app through the installer once before debugging normally, so that the Start shortcut with your AUMID and CLSID is present.</span></span> <span data-ttu-id="63373-199">Nachdem die Verknüpfung auf dem Startmenü vorhanden ist, können Sie mithilfe von F5 in Visual Studio debuggen.</span><span class="sxs-lookup"><span data-stu-id="63373-199">After the Start shortcut is present, you can debug using F5 from Visual Studio.</span></span>

<span data-ttu-id="63373-200">Wenn Ihre Benachrichtigungen nicht einfach in Ihrer klassische Win32-App angezeigt werden (und keine Ausnahmen ausgelöst werden), bedeutet dies wahrscheinlich, dass die Verknüpfung im Startmenü nicht vorhanden ist (installieren Sie Ihre App über das Installationsprogramm), oder die AUMID, die Sie im Code verwendet haben, nicht der AUMID der Verknüpfung auf dem Startmenü entspricht.</span><span class="sxs-lookup"><span data-stu-id="63373-200">If your notifications simply fail to appear in your classic Win32 app (and no exceptions are thrown), that likely means the Start shortcut isn't present (install your app via the installer), or the AUMID you used in code doesn't match the AUMID in your Start shortcut.</span></span>

<span data-ttu-id="63373-201">Wenn Ihre Benachrichtigungen im Info-Center erscheinen aber nicht dort angezeigt werden (verschwinden, nachdem das Popup geschlossen ist) beibehalten werden nicht persistent angezeigt werden, bedeutet dies, dass Sie die den COM-Aktivator nicht ordnungsgemäß implementiert haben.</span><span class="sxs-lookup"><span data-stu-id="63373-201">If your notifications appear but aren't persisted in Action Center (disappearing after the popup is dismissed), that means you haven't implemented the COM activator correctly.</span></span>

<span data-ttu-id="63373-202">Wenn Sie sowohl Ihre Desktop-Brücke und die klassische Win32-App installiert haben, beachten Sie, dass die App Desktop-Brücke die klassische Win32-App bei der Behandlung von Popup-Aktivierungen ablöst.</span><span class="sxs-lookup"><span data-stu-id="63373-202">If you've installed both your Desktop Bridge and classic Win32 app, note that the Desktop Bridge app will supersede the classic Win32 app when handling toast activations.</span></span> <span data-ttu-id="63373-203">Dies bedeutet, dass Popups aus der klassische Win32-App beim Klicken auf die Desktop-Brücke-App gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="63373-203">That means that toasts from the classic Win32 app will still launch the Desktop Bridge app when clicked.</span></span> <span data-ttu-id="63373-204">Das Deinstallieren der App Desktop-Brücke setzt die Aktivierung auf die klassische Win32-App zurück.</span><span class="sxs-lookup"><span data-stu-id="63373-204">Uninstalling the Desktop Bridge app will revert activations back to the classic Win32 app.</span></span>

<span data-ttu-id="63373-205">Wenn Sie `HRESULT 0x800401f0 CoInitialize has not been called.` erhalten, müssen Sie `CoInitialize(nullptr)` in Ihrer App vor dem Aufrufen der APIs aufrufen.</span><span class="sxs-lookup"><span data-stu-id="63373-205">If you receive `HRESULT 0x800401f0 CoInitialize has not been called.`, be sure to call `CoInitialize(nullptr)` in your app before calling the APIs.</span></span>

<span data-ttu-id="63373-206">Wenn Sie `HRESULT 0x8000000e A method was called at an unexpected time.` beim Aufrufen der Compat APIs erhalten, bedeutet dies wahrscheinlich, dass Sie die erforderliche Register-Methoden nicht aufgerufen haben (oder bei einer Desktop-Brücke-App, dass Sie derzeit die App nicht unter im Desktop-Brücken-Kontext ausführen).</span><span class="sxs-lookup"><span data-stu-id="63373-206">If you receive `HRESULT 0x8000000e A method was called at an unexpected time.` while calling the Compat APIs, that likely means you failed to call the required Register methods (or if a Desktop Bridge app, you're not currently running your app under the Desktop Bridge context).</span></span>

<span data-ttu-id="63373-207">Wenn Sie zahlreiche `unresolved external symbol` Kompilierungsfehler erhalten, haben Sie wahrscheinlich vergessen, `runtimeobject.lib` auf die **zusätzliche Abhängigkeiten** in Schritt 1 hinzuzufügen (oder Sie haben sie nur der Debugkonfiguration und nicht der Releasekonfiguration hinzugefügt).</span><span class="sxs-lookup"><span data-stu-id="63373-207">If you get numerous `unresolved external symbol` compilation errors, you likely forgot to add `runtimeobject.lib` to the **Additional Dependencies** in step #1 (or you only added it to the Debug configuration and not Release configuration).</span></span>


## <a name="handling-older-versions-of-windows"></a><span data-ttu-id="63373-208">Behandeln von älteren Versionen von Windows</span><span class="sxs-lookup"><span data-stu-id="63373-208">Handling older versions of Windows</span></span>

<span data-ttu-id="63373-209">Wenn Sie Windows8.1 oder niedriger unterstützen, sollten Sie zur Laufzeit überprüfen, ob Sie Windows10 ausführen, bevor Sie eine **DesktopNotificationManagerCompat**-API aufrufen oder ToastGeneric-Popupbenachrichtigungen senden.</span><span class="sxs-lookup"><span data-stu-id="63373-209">If you support Windows 8.1 or lower, you'll want to check at runtime whether you're running on Windows 10 before calling any **DesktopNotificationManagerCompat** APIs or sending any ToastGeneric toasts.</span></span>

<span data-ttu-id="63373-210">Mit Windows8 wurden Popupbenachrichtigungen eingeführt, allerdings verwendet es die [älteren Popupvorlagen](https://docs.microsoft.com/en-us/previous-versions/windows/apps/hh761494(v=win.10)) wie z.B. ToastText01.</span><span class="sxs-lookup"><span data-stu-id="63373-210">Windows 8 introduced toast notifications, but used the [legacy toast templates](https://docs.microsoft.com/en-us/previous-versions/windows/apps/hh761494(v=win.10)), like ToastText01.</span></span> <span data-ttu-id="63373-211">Die Aktivierung wurde vom **Activated**-Ereignis im Speicher von der **ToastNotification**-Klasse behandelt, da Popups nur als kurze Popups angezeigt wurden, die nicht beibehalten wurden.</span><span class="sxs-lookup"><span data-stu-id="63373-211">Activation was handled by the in-memory **Activated** event on the **ToastNotification** class since toasts were only brief popups that weren't persisted.</span></span> <span data-ttu-id="63373-212">Windows10 führte [interaktive ToastGeneric-Popups](adaptive-interactive-toasts.md) ein sowie das Info-Center, in dem Benachrichtigungen für mehrere Tage beibehalten werden.</span><span class="sxs-lookup"><span data-stu-id="63373-212">Windows 10 introduced [interactive ToastGeneric toasts](adaptive-interactive-toasts.md), and also introduced Action Center where notifications are persisted for multiple days.</span></span> <span data-ttu-id="63373-213">Die Einführung des Info-Centers erforderte die Einführung eines COM-Aktivators, damit Ihr Popups auch noch einige Tage nach dem Erstellen aktiviert werden können.</span><span class="sxs-lookup"><span data-stu-id="63373-213">The introduction of Action Center required the introduction of a COM activator, so that your toast can be activated days after you created it.</span></span>

| <span data-ttu-id="63373-214">Betriebssystem</span><span class="sxs-lookup"><span data-stu-id="63373-214">OS</span></span> | <span data-ttu-id="63373-215">ToastGeneric</span><span class="sxs-lookup"><span data-stu-id="63373-215">ToastGeneric</span></span> | <span data-ttu-id="63373-216">COM-Aktivator</span><span class="sxs-lookup"><span data-stu-id="63373-216">COM activator</span></span> | <span data-ttu-id="63373-217">Ältere Popupvorlagen</span><span class="sxs-lookup"><span data-stu-id="63373-217">Legacy toast templates</span></span> |
| -- | ------------ | ------------- | ---------------------- |
| <span data-ttu-id="63373-218">Windows10</span><span class="sxs-lookup"><span data-stu-id="63373-218">Windows 10</span></span> | <span data-ttu-id="63373-219">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="63373-219">Supported</span></span> | <span data-ttu-id="63373-220">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="63373-220">Supported</span></span> | <span data-ttu-id="63373-221">Unterstützt (aktiviert den COM-Server nicht)</span><span class="sxs-lookup"><span data-stu-id="63373-221">Supported (but won't activate COM server)</span></span> |
| <span data-ttu-id="63373-222">Windows 8.1 / 8</span><span class="sxs-lookup"><span data-stu-id="63373-222">Windows 8.1 / 8</span></span> | <span data-ttu-id="63373-223">n.a.</span><span class="sxs-lookup"><span data-stu-id="63373-223">N/A</span></span> | <span data-ttu-id="63373-224">n.a.</span><span class="sxs-lookup"><span data-stu-id="63373-224">N/A</span></span> | <span data-ttu-id="63373-225">Unterstützt</span><span class="sxs-lookup"><span data-stu-id="63373-225">Supported</span></span> |
| <span data-ttu-id="63373-226">Windows 7 und niedriger</span><span class="sxs-lookup"><span data-stu-id="63373-226">Windows 7 and lower</span></span> | <span data-ttu-id="63373-227">n.a.</span><span class="sxs-lookup"><span data-stu-id="63373-227">N/A</span></span> | <span data-ttu-id="63373-228">n.a.</span><span class="sxs-lookup"><span data-stu-id="63373-228">N/A</span></span> | <span data-ttu-id="63373-229">n.a.</span><span class="sxs-lookup"><span data-stu-id="63373-229">N/A</span></span> |

<span data-ttu-id="63373-230">Um zu überprüfen, ob Sie Windows10 ausführen, geben Sie den `<VersionHelpers.h>` Header an und überprüfen Sie die **IsWindows10OrGreater**-Methode.</span><span class="sxs-lookup"><span data-stu-id="63373-230">To check if you're running on Windows 10, include the `<VersionHelpers.h>` header and check the **IsWindows10OrGreater** method.</span></span> <span data-ttu-id="63373-231">Wenn „true” zurückgegeben wird, rufen Sie weiterhin alle in dieser Dokumentation beschriebenen Methoden auf.</span><span class="sxs-lookup"><span data-stu-id="63373-231">If this returns true, continue calling all the methods described in this documentation!</span></span> 

```cpp
#include <VersionHelpers.h>

if (IsWindows10OrGreater())
{
    // Running Windows 10, continue with sending Windows 10 toasts!
}
```


## <a name="known-issues"></a><span data-ttu-id="63373-232">Bekannte Probleme</span><span class="sxs-lookup"><span data-stu-id="63373-232">Known issues</span></span>

<span data-ttu-id="63373-233">**FIXED: Die App hat nach dem Klicken auf die Popupbenachrichtigung keinen Fokus**: In Build 15063 und früher wurden die Vordergrundrechte nicht auf Ihre Anwendung übertragen, wenn wir den COM-Server aktivierten.</span><span class="sxs-lookup"><span data-stu-id="63373-233">**FIXED: App doesn't become focused after clicking toast**: In builds 15063 and earlier, foreground rights weren't being transferred to your application when we activated the COM server.</span></span> <span data-ttu-id="63373-234">Aus diesem Grund führte Ihre App einfach einen Flash aus, bei dem Versuch, sie in den Vordergrund zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="63373-234">Therefore, your app would simply flash when you tried to move it to the foreground.</span></span> <span data-ttu-id="63373-235">Es gibt hierfür keine Problemumgehung.</span><span class="sxs-lookup"><span data-stu-id="63373-235">There was no workaround for this issue.</span></span> <span data-ttu-id="63373-236">Wir haben dies in Build 16299 und höher behoben.</span><span class="sxs-lookup"><span data-stu-id="63373-236">We fixed this in builds 16299 and higher.</span></span>


## <a name="resources"></a><span data-ttu-id="63373-237">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="63373-237">Resources</span></span>

* [<span data-ttu-id="63373-238">Vollständiges Codebeispiel auf GitHub</span><span class="sxs-lookup"><span data-stu-id="63373-238">Full code sample on GitHub</span></span>](https://github.com/WindowsNotifications/desktop-toasts)
* [<span data-ttu-id="63373-239">Popupbenachrichtigungen über Desktop-Apps</span><span class="sxs-lookup"><span data-stu-id="63373-239">Toast notifications from desktop apps</span></span>](toast-desktop-apps.md)
* [<span data-ttu-id="63373-240">Dokumentation zu Popupinhalt</span><span class="sxs-lookup"><span data-stu-id="63373-240">Toast content documentation</span></span>](adaptive-interactive-toasts.md)