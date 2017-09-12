---
author: normesta
Description: "Sie können Erweiterungen verwenden, um Ihre verpackte Desktop-App in Windows10 auf vordefinierter Weise zu integrieren."
Search.Product: eADQiWindows 10XVcnh
title: "Integrieren Sie Ihre App in Windows10 (Desktop-Brücke)"
ms.author: normesta
ms.date: 05/25/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.assetid: 0a8cedac-172a-4efd-8b6b-67fd3667df34
ms.openlocfilehash: 0c3427a7b49b17fda9a3ba0680e59b134732e9fa
ms.sourcegitcommit: 38ef208ef457ce1857038c9cde3658c884d29b75
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/13/2017
---
# <a name="integrate-your-app-with-windows-10-desktop-bridge"></a><span data-ttu-id="af57e-104">Integrieren Sie Ihre App in Windows10 (Desktop-Brücke)</span><span class="sxs-lookup"><span data-stu-id="af57e-104">Integrate your app with Windows 10 (Desktop Bridge)</span></span>

<span data-ttu-id="af57e-105">Verwenden Sie Erweiterungen, um Ihre App in Windows10 auf vordefinierter Weise zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="af57e-105">Use extensions to integrate your app with Windows 10 in predefined ways.</span></span>

<span data-ttu-id="af57e-106">Verwenden Sie z.B. eine Erweiterung, um eine Firewallausnahme festzulegen, machen Sie Ihre App die Standard-App für einen Dateityp oder verweisen Sie mit Startkacheln auf die verpackte Version Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="af57e-106">For example, use an extension to create a firewall exception, make your app the default app for a file type, or point start tiles to the packaged version of your app.</span></span> <span data-ttu-id="af57e-107">Um eine Erweiterung zu verwenden, fügen Sie einfach XML-Codes zur Paketmanifestdatei Ihrer App hinzu.</span><span class="sxs-lookup"><span data-stu-id="af57e-107">To use an extension, just add some XML to your app's package manifest file.</span></span> <span data-ttu-id="af57e-108">Es ist kein Code erforderlich.</span><span class="sxs-lookup"><span data-stu-id="af57e-108">No code is required.</span></span>

<span data-ttu-id="af57e-109">In diesem Thema werden diese Erweiterungen und die Aufgaben beschrieben, die Sie anhand dieser Erweiterungen ausführen können.</span><span class="sxs-lookup"><span data-stu-id="af57e-109">This topic describes these extensions and the tasks that you can perform by using them.</span></span>

## <a name="transition-users-to-your-app"></a><span data-ttu-id="af57e-110">Den Übergang Ihrer Benutzer auf Ihre App bereitstellen</span><span class="sxs-lookup"><span data-stu-id="af57e-110">Transition users to your app</span></span>

<span data-ttu-id="af57e-111">Helfen Sie Ihren Benutzern, auf Ihre verpackte App umzustellen.</span><span class="sxs-lookup"><span data-stu-id="af57e-111">Help users transition to your packaged app.</span></span>

* [<span data-ttu-id="af57e-112">Verweisen Sie mit vorhandenen Startkacheln Taskleistenschaltflächen auf die verpackte App.</span><span class="sxs-lookup"><span data-stu-id="af57e-112">Point existing Start tiles and taskbar buttons to your packaged app</span></span>](#point)
* [<span data-ttu-id="af57e-113">Stellen Sie ein, dass die verpackte App und nicht Ihre Desktop-App Dateien öffnet.</span><span class="sxs-lookup"><span data-stu-id="af57e-113">Make your packaged app open files instead of your desktop app</span></span>](#make)
* [<span data-ttu-id="af57e-114">Ihre verpackte App einer Gruppe von Dateitypen zuordnen.</span><span class="sxs-lookup"><span data-stu-id="af57e-114">Associate your packaged app with a set of file types</span></span>](#associate)
* [<span data-ttu-id="af57e-115">Fügen Sie den Kontextmenüs der Dateien, die einen bestimmten Dateityp haben, Optionen hinzu.</span><span class="sxs-lookup"><span data-stu-id="af57e-115">Add options to the context menus of files that have a certain file type</span></span>](#add)
* [<span data-ttu-id="af57e-116">Öffnen Sie bestimmte Dateitypen direkt anhand einer URL</span><span class="sxs-lookup"><span data-stu-id="af57e-116">Open certain types of files directly by using a URL</span></span>](#open)

<span id="point" />
### <a name="point-existing-start-tiles-and-taskbar-buttons-to-your-packaged-app"></a><span data-ttu-id="af57e-117">Verweisen Sie mit vorhandenen Startkacheln Taskleistenschaltflächen auf die verpackte App.</span><span class="sxs-lookup"><span data-stu-id="af57e-117">Point existing Start tiles and taskbar buttons to your packaged app</span></span>

<span data-ttu-id="af57e-118">Ihre Benutzer haben möglicherweise Ihre Desktop-Anwendung an die Taskleiste oder das Startmenü angeheftet.</span><span class="sxs-lookup"><span data-stu-id="af57e-118">Your users might have pinned your desktop application to the taskbar or the Start menu.</span></span> <span data-ttu-id="af57e-119">Sie mit diesen Verknüpfungen auf Ihre neu verpackte App verweisen.</span><span class="sxs-lookup"><span data-stu-id="af57e-119">You can point those shortcuts to your new packaged app.</span></span>

#### <a name="xml-namespace"></a><span data-ttu-id="af57e-120">XML-Namespace</span><span class="sxs-lookup"><span data-stu-id="af57e-120">XML namespace</span></span>

<span data-ttu-id="af57e-121">http://schemas.microsoft.com/appx/Manifest/foundation/windows10/restrictedcapabilities/3</span><span class="sxs-lookup"><span data-stu-id="af57e-121">http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities/3</span></span>

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="af57e-122">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="af57e-122">Elements and attributes of this extension</span></span>

```XML
<Extension Category="windows.desktopAppMigration">
    <DesktopAppMigration>
        <DesktopApp AumId="[your_app_aumid]" />
        <DesktopApp ShortcutPath="[path]" />
    </DesktopAppMigration>
</Extension>

```

<span data-ttu-id="af57e-123">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-rescap3-desktopappmigration).</span><span class="sxs-lookup"><span data-stu-id="af57e-123">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-rescap3-desktopappmigration).</span></span>

|<span data-ttu-id="af57e-124">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-124">Name</span></span> | <span data-ttu-id="af57e-125">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="af57e-125">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="af57e-126">Category</span><span class="sxs-lookup"><span data-stu-id="af57e-126">Category</span></span> |<span data-ttu-id="af57e-127">Immer ``windows.desktopAppMigration``.</span><span class="sxs-lookup"><span data-stu-id="af57e-127">Always ``windows.desktopAppMigration``.</span></span>
|<span data-ttu-id="af57e-128">AumID</span><span class="sxs-lookup"><span data-stu-id="af57e-128">AumID</span></span> |<span data-ttu-id="af57e-129">Die Anwendungsbenutzermodell-ID der verpackten App.</span><span class="sxs-lookup"><span data-stu-id="af57e-129">The Application User Model ID of your packaged app.</span></span> |
|<span data-ttu-id="af57e-130">Verknüpfungspfad</span><span class="sxs-lookup"><span data-stu-id="af57e-130">ShortcutPath</span></span> |<span data-ttu-id="af57e-131">Der Pfad zu den Ink-Dateien, die die Desktop-Version Ihrer App starten.</span><span class="sxs-lookup"><span data-stu-id="af57e-131">The path to .lnk files that start the desktop version of your app.</span></span> |

#### <a name="example"></a><span data-ttu-id="af57e-132">Beispiel</span><span class="sxs-lookup"><span data-stu-id="af57e-132">Example</span></span>

```XML
<Package
  xmlns:rescap3="http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities/3"
  IgnorableNamespaces="rescap3">
  <Applications>
    <Application>
      <Extensions>
        <rescap3:Extension Category="windows.desktopAppMigration">
          <rescap3:DesktopAppMigration>
            <rescap3:DesktopApp AumId="[your_app_aumid]" />
            <rescap3:DesktopApp ShortcutPath="%USERPROFILE%\Desktop\[my_app].lnk" />
            <rescap3:DesktopApp ShortcutPath="%APPDATA%\Microsoft\Windows\Start Menu\Programs\[my_app].lnk" />
            <rescap3:DesktopApp ShortcutPath="%PROGRAMDATA%\Microsoft\Windows\Start Menu\Programs\[my_app_folder]\[my_app].lnk"/>
         </rescap3:DesktopAppMigration>
        </rescap3:Extension>
      </Extensions>
    </Application>
  </Applications>
</Package>
```
#### <a name="related-sample"></a><span data-ttu-id="af57e-133">Verwandte Beispiele</span><span class="sxs-lookup"><span data-stu-id="af57e-133">Related sample</span></span>

[<span data-ttu-id="af57e-134">WPF-Bildanzeige mit Übergang/Migration/Deinstallation</span><span class="sxs-lookup"><span data-stu-id="af57e-134">WPF picture viewer with transition/migration/uninstallation</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/DesktopAppTransition)

<span id="make" />
### <a name="make-your-packaged-app-open-files-instead-of-your-desktop-app"></a><span data-ttu-id="af57e-135">Stellen Sie ein, dass die verpackte App und nicht Ihre Desktop-App Dateien öffnet.</span><span class="sxs-lookup"><span data-stu-id="af57e-135">Make your packaged app open files instead of your desktop app</span></span>

<span data-ttu-id="af57e-136">Sie können sicherstellen, dass Benutzer standardmäßig Ihre neu verpackte Version statt die Desktop-Version Ihrer App für bestimmte Dateitypen öffnen.</span><span class="sxs-lookup"><span data-stu-id="af57e-136">You can make sure that users open your new packaged app by default for specific types of files instead of opening the desktop version of your app.</span></span>

<span data-ttu-id="af57e-137">Dazu müssen Sie den [programmgesteuerten Bezeichner (Programm-ID)](https://msdn.microsoft.com/library/windows/desktop/cc144152.aspx) jeder Anwendung angeben, aus der Sie Dateizuordnungen übernehmen möchten.</span><span class="sxs-lookup"><span data-stu-id="af57e-137">To do that, you'll specify the [programmatic identifier (ProgID)](https://msdn.microsoft.com/library/windows/desktop/cc144152.aspx) of each application from which you want to inherit file associations.</span></span>

#### <a name="xml-namespaces"></a><span data-ttu-id="af57e-138">XML-Namespaces</span><span class="sxs-lookup"><span data-stu-id="af57e-138">XML namespaces</span></span>

* <span data-ttu-id="af57e-139">http://schemas.microsoft.com/appx/Manifest/uap/windows10/3</span><span class="sxs-lookup"><span data-stu-id="af57e-139">http://schemas.microsoft.com/appx/manifest/uap/windows10/3</span></span>
* <span data-ttu-id="af57e-140">http://schemas.microsoft.com/appx/Manifest/foundation/windows10/restrictedcapabilities/3</span><span class="sxs-lookup"><span data-stu-id="af57e-140">http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities/3</span></span>

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="af57e-141">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="af57e-141">Elements and attributes of this extension</span></span>

```XML
<Extension Category="windows.fileTypeAssociation">
<FileTypeAssociation Name="[AppID]">
         <MigrationProgIds>
            <MigrationProgId>"[ProgID]"</MigrationProgId>
        </MigrationProgIds>
    </FileTypeAssociation>
</Extension>
```

<span data-ttu-id="af57e-142">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span><span class="sxs-lookup"><span data-stu-id="af57e-142">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span></span>

|<span data-ttu-id="af57e-143">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-143">Name</span></span> |<span data-ttu-id="af57e-144">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="af57e-144">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="af57e-145">Kategorie</span><span class="sxs-lookup"><span data-stu-id="af57e-145">Category</span></span> |<span data-ttu-id="af57e-146">Immer ``windows.fileTypeAssociation``.</span><span class="sxs-lookup"><span data-stu-id="af57e-146">Always ``windows.fileTypeAssociation``.</span></span>
|<span data-ttu-id="af57e-147">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-147">Name</span></span> |<span data-ttu-id="af57e-148">Eine eindeutige ID für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="af57e-148">A unique Id for your app.</span></span> <span data-ttu-id="af57e-149">Diese ID wird intern verwendet, um einen [programmgesteuerte Bezeichner (Programm-ID)](https://msdn.microsoft.com/library/windows/desktop/cc144152.aspx) mit Hash zu generieren, die mit Ihrer Dateitypzuordnung verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="af57e-149">This Id is used internally to generate a hashed [programmatic identifier (ProgID)](https://msdn.microsoft.com/library/windows/desktop/cc144152.aspx) associated with your file type association.</span></span> <span data-ttu-id="af57e-150">Mithilfe dieser ID können Sie Änderungen in zukünftigen Versionen Ihrer App verwalten.</span><span class="sxs-lookup"><span data-stu-id="af57e-150">You can use this Id to manage changes in future versions of your app.</span></span> |
|<span data-ttu-id="af57e-151">MigrationProgId</span><span class="sxs-lookup"><span data-stu-id="af57e-151">MigrationProgId</span></span> |<span data-ttu-id="af57e-152">Der [programmgesteuerte Bezeichner (Programm-ID)](https://msdn.microsoft.com/library/windows/desktop/cc144152.aspx), der die Anwendung, die Komponente und die Version der Desktop-App beschreibt, aus der die Dateizuordnungen übernommen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="af57e-152">The [programmatic identifier (ProgID)](https://msdn.microsoft.com/library/windows/desktop/cc144152.aspx) that describes the application, component, and version of the desktop app from which you want to inherit file associations.</span></span>|

#### <a name="example"></a><span data-ttu-id="af57e-153">Beispiel</span><span class="sxs-lookup"><span data-stu-id="af57e-153">Example</span></span>

```XML
<Package
  xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"
  xmlns:rescap3="http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities/3"
  IgnorableNamespaces="uap3, rescap3">
  <Applications>
    <Application>
      <Extensions>
        <uap:Extension Category="windows.fileTypeAssociation">
          <uap3:FileTypeAssociation Name="Contoso">
            <rescap3:MigrationProgIds>
              <rescap3:MigrationProgId>Foo.Bar.1</rescap3:MigrationProgId>
              <rescap3:MigrationProgId>Foo.Bar.2</rescap3:MigrationProgId>
            </rescap3:MigrationProgIds>
          </uap3:FileTypeAssociation>
        </uap:Extension>
      </Extensions>
    </Application>
  </Applications>
</Package>
```
#### <a name="related-sample"></a><span data-ttu-id="af57e-154">Verwandte Beispiele</span><span class="sxs-lookup"><span data-stu-id="af57e-154">Related sample</span></span>

[<span data-ttu-id="af57e-155">WPF-Bildanzeige mit Übergang/Migration/Deinstallation</span><span class="sxs-lookup"><span data-stu-id="af57e-155">WPF picture viewer with transition/migration/uninstallation</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/DesktopAppTransition)

<span id="associate" />
### <a name="associate-your-packaged-app-with-a-set-of-file-types"></a><span data-ttu-id="af57e-156">Ihre verpackte App einer Gruppe von Dateitypen zuordnen.</span><span class="sxs-lookup"><span data-stu-id="af57e-156">Associate your packaged app with a set of file types</span></span>

<span data-ttu-id="af57e-157">Sie können Ihre verpackte App mit Dateityperweiterungen zuordnen.</span><span class="sxs-lookup"><span data-stu-id="af57e-157">You can associated your packaged app with file type extensions.</span></span> <span data-ttu-id="af57e-158">Wenn ein Benutzer mit der rechten Maustaste auf eine Datei klickt und **Öffnen mit** auswählt, wird Ihre App in der Vorschlagsliste angezeigt.</span><span class="sxs-lookup"><span data-stu-id="af57e-158">If a user right-clicks a file and then selects the **Open with** option, your app appears in the list of suggestions.</span></span>

#### <a name="xml-namespace"></a><span data-ttu-id="af57e-159">XML-Namespace</span><span class="sxs-lookup"><span data-stu-id="af57e-159">XML namespace</span></span>

* <span data-ttu-id="af57e-160">http://schemas.microsoft.com/appx/manifest/uap/windows10</span><span class="sxs-lookup"><span data-stu-id="af57e-160">http://schemas.microsoft.com/appx/manifest/uap/windows10</span></span>
* <span data-ttu-id="af57e-161">http://schemas.microsoft.com/appx/manifest/uap/windows10/3</span><span class="sxs-lookup"><span data-stu-id="af57e-161">http://schemas.microsoft.com/appx/manifest/uap/windows10/3</span></span>

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="af57e-162">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="af57e-162">Elements and attributes of this extension</span></span>

```XML
<Extension Category="windows.fileTypeAssociation">
    <FileTypeAssociation Name="[AppID]">
        <SupportedFileTypes>
            <FileType>"[file extension]"</FileType>
        </SupportedFileTypes>
    </FileTypeAssociation>
</Extension>
```

<span data-ttu-id="af57e-163">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span><span class="sxs-lookup"><span data-stu-id="af57e-163">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span></span>

|<span data-ttu-id="af57e-164">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-164">Name</span></span> |<span data-ttu-id="af57e-165">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="af57e-165">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="af57e-166">Kategorie</span><span class="sxs-lookup"><span data-stu-id="af57e-166">Category</span></span> |<span data-ttu-id="af57e-167">Immer ``windows.fileTypeAssociation``.</span><span class="sxs-lookup"><span data-stu-id="af57e-167">Always ``windows.fileTypeAssociation``.</span></span>
|<span data-ttu-id="af57e-168">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-168">Name</span></span> |<span data-ttu-id="af57e-169">Eine eindeutige ID für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="af57e-169">A unique Id for your app.</span></span> <span data-ttu-id="af57e-170">Diese ID wird intern verwendet, um einen [programmgesteuerte Bezeichner (Programm-ID)](https://msdn.microsoft.com/library/windows/desktop/cc144152.aspx) mit Hash zu generieren, die mit Ihrer Dateitypzuordnung verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="af57e-170">This Id is used internally to generate a hashed [programmatic identifier (ProgID)](https://msdn.microsoft.com/library/windows/desktop/cc144152.aspx) associated with your file type association.</span></span> <span data-ttu-id="af57e-171">Mithilfe dieser ID können Sie Änderungen in zukünftigen Versionen Ihrer App verwalten.</span><span class="sxs-lookup"><span data-stu-id="af57e-171">You can use this Id to manage changes in future versions of your app.</span></span>   |
|<span data-ttu-id="af57e-172">FileType</span><span class="sxs-lookup"><span data-stu-id="af57e-172">FileType</span></span> |<span data-ttu-id="af57e-173">Die Erweiterung, die von Ihrer App unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="af57e-173">The file extension supported by your app.</span></span> |

#### <a name="example"></a><span data-ttu-id="af57e-174">Beispiel</span><span class="sxs-lookup"><span data-stu-id="af57e-174">Example</span></span>

```XML
<Package
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"
  IgnorableNamespaces="uap, uap3">
  <Applications>
    <Application>
      <Extensions>
        <uap:Extension Category="windows.fileTypeAssociation">
          <uap3:FileTypeAssociation Name="Contoso">
            <uap:SupportedFileTypes>
              <uap:FileType>.txt</uap:FileType>
              <uap:FileType>.avi</uap:FileType>
            </uap:SupportedFileTypes>
          </uap3:FileTypeAssociation>
        </uap:Extension>
      </Extensions>
    </Application>
  </Applications>
</Package>
```

#### <a name="related-sample"></a><span data-ttu-id="af57e-175">Verwandte Beispiele</span><span class="sxs-lookup"><span data-stu-id="af57e-175">Related sample</span></span>

[<span data-ttu-id="af57e-176">WPF-Bildanzeige mit Übergang/Migration/Deinstallation</span><span class="sxs-lookup"><span data-stu-id="af57e-176">WPF picture viewer with transition/migration/uninstallation</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/DesktopAppTransition)

<span id="add" />
### <a name="add-options-to-the-context-menus-of-files-that-have-a-certain-file-type"></a><span data-ttu-id="af57e-177">Fügen Sie den Kontextmenüs der Dateien, die einen bestimmten Dateityp haben, Optionen hinzu.</span><span class="sxs-lookup"><span data-stu-id="af57e-177">Add options to the context menus of files that have a certain file type</span></span>

<span data-ttu-id="af57e-178">In den meisten Fällen klicken Benutzer doppelt auf Dateien, um sie zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="af57e-178">In most cases, users double-click files to open them.</span></span> <span data-ttu-id="af57e-179">Wenn Benutzer mit der rechten Maustaste auf eine Datei klicken, werden verschiedene Optionen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="af57e-179">If users, right click a file, various options appear.</span></span>

<span data-ttu-id="af57e-180">Sie können diesem Menü Optionen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="af57e-180">You can add options to that menu.</span></span> <span data-ttu-id="af57e-181">Diese Optionen geben Benutzern weitere Möglichkeiten zur Interaktion mit der Datei, wie etwa Drucken, Bearbeiten oder das Anzeigen einer Vorschau.</span><span class="sxs-lookup"><span data-stu-id="af57e-181">These options give users other ways to interact with your file such as print, edit, or preview the file.</span></span>

#### <a name="xml-namespaces"></a><span data-ttu-id="af57e-182">XML-Namespaces</span><span class="sxs-lookup"><span data-stu-id="af57e-182">XML namespaces</span></span>

* <span data-ttu-id="af57e-183">http://schemas.microsoft.com/appx/manifest/uap/windows10</span><span class="sxs-lookup"><span data-stu-id="af57e-183">http://schemas.microsoft.com/appx/manifest/uap/windows10</span></span>
* <span data-ttu-id="af57e-184">http://schemas.microsoft.com/appx/manifest/uap/windows10/2</span><span class="sxs-lookup"><span data-stu-id="af57e-184">http://schemas.microsoft.com/appx/manifest/uap/windows10/2</span></span>
* <span data-ttu-id="af57e-185">http://schemas.microsoft.com/appx/manifest/uap/windows10/3</span><span class="sxs-lookup"><span data-stu-id="af57e-185">http://schemas.microsoft.com/appx/manifest/uap/windows10/3</span></span>


#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="af57e-186">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="af57e-186">Elements and attributes of this extension</span></span>

```XML
<Extension Category="windows.fileTypeAssociation">
    <FileTypeAssociation Name="[AppID]">
        <SupportedVerbs>
              <Verb Id="[ID]" Extended="[Extended]" Parameters="[parameters]">"[verb label]"</Verb>
        </SupportedVerbs>
    </FileTypeAssociation>
</Extension>
```

<span data-ttu-id="af57e-187">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span><span class="sxs-lookup"><span data-stu-id="af57e-187">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span></span>

|<span data-ttu-id="af57e-188">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-188">Name</span></span> |<span data-ttu-id="af57e-189">Description</span><span class="sxs-lookup"><span data-stu-id="af57e-189">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="af57e-190">Category</span><span class="sxs-lookup"><span data-stu-id="af57e-190">Category</span></span> | <span data-ttu-id="af57e-191">Immer ``windows.fileTypeAssociation``.</span><span class="sxs-lookup"><span data-stu-id="af57e-191">Always ``windows.fileTypeAssociation``.</span></span>
|<span data-ttu-id="af57e-192">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-192">Name</span></span> |<span data-ttu-id="af57e-193">Eine eindeutige ID für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="af57e-193">A unique Id for your app.</span></span> |
|<span data-ttu-id="af57e-194">Verb</span><span class="sxs-lookup"><span data-stu-id="af57e-194">Verb</span></span> |<span data-ttu-id="af57e-195">Der Name, der im Kontextmenü des Datei-Explorers angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="af57e-195">The name that appears in the File Explorer context menu.</span></span> <span data-ttu-id="af57e-196">Diese Zeichenfolge kann mithilfe von ```ms-resource``` lokalisiert werden.</span><span class="sxs-lookup"><span data-stu-id="af57e-196">This string is localizable that uses ```ms-resource```.</span></span>|
|<span data-ttu-id="af57e-197">ID</span><span class="sxs-lookup"><span data-stu-id="af57e-197">Id</span></span> |<span data-ttu-id="af57e-198">Die eindeutige ID des Verbs.</span><span class="sxs-lookup"><span data-stu-id="af57e-198">The unique Id of the verb.</span></span> <span data-ttu-id="af57e-199">Bei UWP-Apps wird sie im Rahmen der Aktivierungsereignisargumente übergeben, um eine entsprechende Behandlung der Benutzerauswahl zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="af57e-199">If your app is a UWP app, this is passed to your app as part of its activation event args so it can handle the user’s selection appropriately.</span></span> <span data-ttu-id="af57e-200">Bei vertrauenswürdig verpackten Apps werden dagegen Parameter übergeben (siehe nächster Aufzählungspunkt).</span><span class="sxs-lookup"><span data-stu-id="af57e-200">If your app is a full-trust packaged app, it receives parameters instead (see the next bullet).</span></span> |
|<span data-ttu-id="af57e-201">Parameter</span><span class="sxs-lookup"><span data-stu-id="af57e-201">Parameters</span></span> |<span data-ttu-id="af57e-202">Die Liste mit Argumentparametern und -werten für das Verb.</span><span class="sxs-lookup"><span data-stu-id="af57e-202">The list of argument parameters and values associated with the verb.</span></span> <span data-ttu-id="af57e-203">Wenn Ihre App eine vertrauenswürdig verpackte App ist, werden diese Parameter bei der Aktivierung der App als Ereignisargumente an die App übergeben.</span><span class="sxs-lookup"><span data-stu-id="af57e-203">If your app is a full-trust packaged app, these parameters are passed to the app as event args when the app is activated.</span></span> <span data-ttu-id="af57e-204">Sie können das Verhalten Ihrer App auf Basis anderer Aktivierungsverben anpassen.</span><span class="sxs-lookup"><span data-stu-id="af57e-204">You can customize the behavior of your app based on different activation verbs.</span></span> <span data-ttu-id="af57e-205">Wenn eine Variable einen Dateipfad enthalten kann, schließen Sie den Parameterwert in Anführungszeichen.</span><span class="sxs-lookup"><span data-stu-id="af57e-205">If a variable can contain a file path, wrap the parameter value in quotes.</span></span> <span data-ttu-id="af57e-206">Dadurch werden jegliche Probleme vermieden, die in Fällen auftreten, bei denen der Pfad Leerzeichen enthält.</span><span class="sxs-lookup"><span data-stu-id="af57e-206">That will avoid any issues that happen in cases where the path includes spaces.</span></span> <span data-ttu-id="af57e-207">Wenn Ihre App eine UWP-App ist, können Sie keine Parameter übergeben.</span><span class="sxs-lookup"><span data-stu-id="af57e-207">If your app is a UWP app, you can’t pass parameters.</span></span> <span data-ttu-id="af57e-208">Die App empfängt stattdessen die ID (siehe das vorherige Aufzählungszeichen).</span><span class="sxs-lookup"><span data-stu-id="af57e-208">The app receives the Id instead (see the previous bullet).</span></span>|
|<span data-ttu-id="af57e-209">Erweitert</span><span class="sxs-lookup"><span data-stu-id="af57e-209">Extended</span></span> |<span data-ttu-id="af57e-210">Gibt an, dass das Verb nur angezeigt werden soll, wenn der Benutzer zum Anzeigen des Kontextmenüs **UMSCHALT** gedrückt hält, bevor er mit der rechten Maustaste auf die Datei klickt.</span><span class="sxs-lookup"><span data-stu-id="af57e-210">Specifies that the verb appears only if the user shows the context menu by holding the **Shift** key before right-clicking the file.</span></span> <span data-ttu-id="af57e-211">Dieses Attribut ist optional und standardmäßig auf den Wert von **False** (Verb soll immer angezeigt werden) festgelegt.</span><span class="sxs-lookup"><span data-stu-id="af57e-211">This attribute is optional and defaults to a value of **False** (e.g., always show the verb) if not listed.</span></span> <span data-ttu-id="af57e-212">Dieses Verhalten muss für jedes Verb einzeln angegeben werden – mit Ausnahme von „Öffnen“: Bei diesem Verb ist der Wert immer **False**.</span><span class="sxs-lookup"><span data-stu-id="af57e-212">You specify this behavior individually for each verb (except for "Open," which is always **False**).</span></span>|

#### <a name="example"></a><span data-ttu-id="af57e-213">Beispiel</span><span class="sxs-lookup"><span data-stu-id="af57e-213">Example</span></span>

```XML
<Package
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
  xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"

  IgnorableNamespaces="uap, uap2, uap3">
  <Applications>
    <Application>
      <Extensions>
        <uap:Extension Category="windows.fileTypeAssociation">
          <uap3:FileTypeAssociation Name="Contoso">
            <uap2:SupportedVerbs>
              <uap3:Verb Id="Edit" Parameters="/e &quot;%1&quot;">Edit</uap3:Verb>
              <uap3:Verb Id="Print" Extended="true" Parameters="/p &quot;%1&quot;">Print</uap3:Verb>
            </uap2:SupportedVerbs>
          </uap3:FileTypeAssociation>
        </uap:Extension>
      </Extensions>
    </Application>
  </Applications>
</Package>
```
#### <a name="related-sample"></a><span data-ttu-id="af57e-214">Verwandte Beispiele</span><span class="sxs-lookup"><span data-stu-id="af57e-214">Related sample</span></span>

[<span data-ttu-id="af57e-215">WPF-Bildanzeige mit Übergang/Migration/Deinstallation</span><span class="sxs-lookup"><span data-stu-id="af57e-215">WPF picture viewer with transition/migration/uninstallation</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/DesktopAppTransition)

<span id="open" />
### <a name="open-certain-types-of-files-directly-by-using-a-url"></a><span data-ttu-id="af57e-216">Öffnen Sie bestimmte Dateitypen direkt anhand einer URL</span><span class="sxs-lookup"><span data-stu-id="af57e-216">Open certain types of files directly by using a URL</span></span>

<span data-ttu-id="af57e-217">Sie können sicherstellen, dass Benutzer standardmäßig Ihre neu verpackte Version statt die Desktop-Version Ihrer App für bestimmte Dateitypen öffnen.</span><span class="sxs-lookup"><span data-stu-id="af57e-217">You can make sure that users open your new packaged app by default for specific types of files instead of opening the desktop version of your app.</span></span>

#### <a name="xml-namespaces"></a><span data-ttu-id="af57e-218">XML-Namespaces</span><span class="sxs-lookup"><span data-stu-id="af57e-218">XML namespaces</span></span>

* <span data-ttu-id="af57e-219">http://schemas.microsoft.com/appx/manifest/uap/windows10</span><span class="sxs-lookup"><span data-stu-id="af57e-219">http://schemas.microsoft.com/appx/manifest/uap/windows10</span></span>
* <span data-ttu-id="af57e-220">http://schemas.microsoft.com/appx/manifest/uap/windows10/3"</span><span class="sxs-lookup"><span data-stu-id="af57e-220">http://schemas.microsoft.com/appx/manifest/uap/windows10/3"</span></span>

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="af57e-221">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="af57e-221">Elements and attributes of this extension</span></span>

```XML
<Extension Category="windows.fileTypeAssociation">
    <FileTypeAssociation Name="[AppID]" UseUrl="true" Parameters="%1">
        <SupportedFileTypes>
            <FileType>"[FileExtension]"</FileType>
        </SupportedFileTypes> 
    </FileTypeAssociation>
</Extension>
```

<span data-ttu-id="af57e-222">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span><span class="sxs-lookup"><span data-stu-id="af57e-222">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span></span>

|<span data-ttu-id="af57e-223">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-223">Name</span></span> |<span data-ttu-id="af57e-224">Description</span><span class="sxs-lookup"><span data-stu-id="af57e-224">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="af57e-225">Category</span><span class="sxs-lookup"><span data-stu-id="af57e-225">Category</span></span> |<span data-ttu-id="af57e-226">Immer ``windows.fileTypeAssociation``.</span><span class="sxs-lookup"><span data-stu-id="af57e-226">Always ``windows.fileTypeAssociation``.</span></span>
|<span data-ttu-id="af57e-227">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-227">Name</span></span> |<span data-ttu-id="af57e-228">Eine eindeutige ID für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="af57e-228">A unique Id for your app.</span></span> |
|<span data-ttu-id="af57e-229">UseUrl</span><span class="sxs-lookup"><span data-stu-id="af57e-229">UseUrl</span></span> |<span data-ttu-id="af57e-230">Gibt an, ob Dateien direkt über eine URL-Ziel geöffnet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="af57e-230">Indicates whether to open files directly from a URL target.</span></span> <span data-ttu-id="af57e-231">Wenn Sie diesen Wert nicht festlegen, wird das System die Datei zunächst lokal herunterladen, wenn Ihre App versucht, die Datei durch eine URL zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="af57e-231">If you do not set this value, attempts by your app to open a file by using a URL cause the system to first download the file locally.</span></span> |
|<span data-ttu-id="af57e-232">Parameter</span><span class="sxs-lookup"><span data-stu-id="af57e-232">Parameters</span></span> |<span data-ttu-id="af57e-233">Optionale Parameter.</span><span class="sxs-lookup"><span data-stu-id="af57e-233">optional parameters.</span></span> |
|<span data-ttu-id="af57e-234">FileType</span><span class="sxs-lookup"><span data-stu-id="af57e-234">FileType</span></span> |<span data-ttu-id="af57e-235">Die relevanten Dateierweiterungen.</span><span class="sxs-lookup"><span data-stu-id="af57e-235">The relevant file extensions.</span></span> |

#### <a name="example"></a><span data-ttu-id="af57e-236">Beispiel</span><span class="sxs-lookup"><span data-stu-id="af57e-236">Example</span></span>

```XML
<Package
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"
  IgnorableNamespaces="uap, uap3">
  <Applications>
      <Application>
        <Extensions>
          <uap:Extension Category="windows.fileTypeAssociation">
            <uap3:FileTypeAssociation Name="documenttypes" UseUrl="true" Parameters="%1">
              <uap:SupportedFileTypes>
                <uap:FileType>.txt</uap:FileType>
                <uap:FileType>.doc</uap:FileType>
              </uap:SupportedFileTypes> 
            </uap3:FileTypeAssociation>
          </uap:Extension>
        </Extensions>
      </Application>
    </Applications>
</Package>
```

## <a name="perform-setup-tasks"></a><span data-ttu-id="af57e-237">Setup-Aufgaben ausführen</span><span class="sxs-lookup"><span data-stu-id="af57e-237">Perform setup tasks</span></span>

* [<span data-ttu-id="af57e-238">Erstellen von Firewallausnahmen für Ihre App</span><span class="sxs-lookup"><span data-stu-id="af57e-238">Create firewall exception for your app</span></span>](#rules)

<span id="rules" />
### <a name="create-firewall-exception-for-your-app"></a><span data-ttu-id="af57e-239">Erstellen von Firewallausnahmen für Ihre App</span><span class="sxs-lookup"><span data-stu-id="af57e-239">Create firewall exception for your app</span></span>

<span data-ttu-id="af57e-240">Wenn bei Ihrer App eine Kommunikation über einen Anschluss erforderlich ist, können Sie Ihre App zur Liste der Firewallausnahmen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="af57e-240">If your app requires communication through a port, you can add your app to the list of firewall exceptions.</span></span>

#### <a name="xml-namespace"></a><span data-ttu-id="af57e-241">XML-Namespace</span><span class="sxs-lookup"><span data-stu-id="af57e-241">XML namespace</span></span>

<span data-ttu-id="af57e-242">http://schemas.microsoft.com/appx/manifest/desktop/windows10/2</span><span class="sxs-lookup"><span data-stu-id="af57e-242">http://schemas.microsoft.com/appx/manifest/desktop/windows10/2</span></span>

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="af57e-243">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="af57e-243">Elements and attributes of this extension</span></span>

```XML
<Extension Category="windows.firewallRules">  
  <FirewallRules Executable="[executable file name]">  
    <Rule
      Direction="[Direction]"
      IPProtocol="[Protocol]"
      LocalPortMin="[LocalPortMin]"
      LocalPortMax="LocalPortMax"
      RemotePortMin="RemotePortMin"
      RemotePortMax="RemotePortMax"
      Profile="[Profile]"/>  
  </FirewallRules>  
</Extension>
```
<span data-ttu-id="af57e-244">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-desktop2-firewallrules).</span><span class="sxs-lookup"><span data-stu-id="af57e-244">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-desktop2-firewallrules).</span></span>

|<span data-ttu-id="af57e-245">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-245">Name</span></span> |<span data-ttu-id="af57e-246">Description</span><span class="sxs-lookup"><span data-stu-id="af57e-246">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="af57e-247">Category</span><span class="sxs-lookup"><span data-stu-id="af57e-247">Category</span></span> |<span data-ttu-id="af57e-248">Immer</span><span class="sxs-lookup"><span data-stu-id="af57e-248">Always</span></span> ``windows.firewallRules``|
|<span data-ttu-id="af57e-249">Ausführbare Datei</span><span class="sxs-lookup"><span data-stu-id="af57e-249">Executable</span></span> |<span data-ttu-id="af57e-250">Der Name der ausführbaren Datei, die Sie der Liste der Firewallausnahmen hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="af57e-250">The name of the executable file that you want to add to the list of firewall exceptions</span></span> |
|<span data-ttu-id="af57e-251">Richtung</span><span class="sxs-lookup"><span data-stu-id="af57e-251">Direction</span></span> |<span data-ttu-id="af57e-252">Gibt an, ob die Regel eine ein- oder ausgehende Regel ist.</span><span class="sxs-lookup"><span data-stu-id="af57e-252">Indicates whether the rule is an inbound or outbound rule</span></span> |
|<span data-ttu-id="af57e-253">IPProtocol</span><span class="sxs-lookup"><span data-stu-id="af57e-253">IPProtocol</span></span> |<span data-ttu-id="af57e-254">Das Kommunikationsprotokoll</span><span class="sxs-lookup"><span data-stu-id="af57e-254">The communication protocol</span></span> |
|<span data-ttu-id="af57e-255">LocalPortMin</span><span class="sxs-lookup"><span data-stu-id="af57e-255">LocalPortMin</span></span> |<span data-ttu-id="af57e-256">Die untere Portnummer in einer Auswahl von lokalen Portnummern.</span><span class="sxs-lookup"><span data-stu-id="af57e-256">The lower port number in a range of local port numbers.</span></span> |
|<span data-ttu-id="af57e-257">LocalPortMax</span><span class="sxs-lookup"><span data-stu-id="af57e-257">LocalPortMax</span></span> |<span data-ttu-id="af57e-258">Die höchste Portnummer in einer Auswahl von lokalen Portnummern.</span><span class="sxs-lookup"><span data-stu-id="af57e-258">The highest port number of a range of local port numbers.</span></span> |
|<span data-ttu-id="af57e-259">RemotePortMax</span><span class="sxs-lookup"><span data-stu-id="af57e-259">RemotePortMax</span></span> |<span data-ttu-id="af57e-260">Die niedrigere Portnummer in einer Auswahl von Remoteportnummern.</span><span class="sxs-lookup"><span data-stu-id="af57e-260">The lower port number in a range of remote port numbers.</span></span> |
|<span data-ttu-id="af57e-261">RemotePortMax</span><span class="sxs-lookup"><span data-stu-id="af57e-261">RemotePortMax</span></span> |<span data-ttu-id="af57e-262">Die höchste Portnummer in einer Auswahl Remoteportnummern.</span><span class="sxs-lookup"><span data-stu-id="af57e-262">The highest port number of a range of remote port numbers.</span></span> |
|<span data-ttu-id="af57e-263">Profil</span><span class="sxs-lookup"><span data-stu-id="af57e-263">Profile</span></span> |<span data-ttu-id="af57e-264">Der Netzwerktyp</span><span class="sxs-lookup"><span data-stu-id="af57e-264">The network type</span></span> |



#### <a name="example"></a><span data-ttu-id="af57e-265">Beispiel</span><span class="sxs-lookup"><span data-stu-id="af57e-265">Example</span></span>

```XML
<Package
  xmlns:desktop2="http://schemas.microsoft.com/appx/manifest/desktop/windows10/2"
  IgnorableNamespaces="desktop2">
  <Extensions>
    <desktop2:Extension Category="windows.firewallRules">  
      <desktop2:FirewallRules Executable="Contoso.exe">  
          <desktop2:Rule Direction="in" IPProtocol="TCP" Profile="all"/>  
          <desktop2:Rule Direction="in" IPProtocol="UDP" LocalPortMin="1337" LocalPortMax="1338" Profile="domain"/>  
          <desktop2:Rule Direction="in" IPProtocol="UDP" LocalPortMin="1337" LocalPortMax="1338" Profile="public"/>  
          <desktop2:Rule Direction="out" IPProtocol="UDP" LocalPortMin="1339" LocalPortMax="1340" RemotePortMin="15"
                         RemotePortMax="19" Profile="domainAndPrivate"/>  
          <desktop2:Rule Direction="out" IPProtocol="GRE" Profile="private"/>  
      </desktop2:FirewallRules>  
  </desktop2:Extension>
</Extensions>
</Package>
```

## <a name="integrate-with-file-explorer"></a><span data-ttu-id="af57e-266">Integration mit dem Datei-Explorer</span><span class="sxs-lookup"><span data-stu-id="af57e-266">Integrate with File Explorer</span></span>

<span data-ttu-id="af57e-267">Helfen Sie Benutzern beim Organisieren von Dateien und interagieren Sie mit Ihnen auf vertrauter Weise.</span><span class="sxs-lookup"><span data-stu-id="af57e-267">Help users organize your files and interact with them in familiar ways.</span></span>

* [<span data-ttu-id="af57e-268">Definieren Sie, wie sich Ihre App verhält, wenn Benutzer mehrere Dateien gleichzeitig auswählen und öffnen.</span><span class="sxs-lookup"><span data-stu-id="af57e-268">Define how your app behaves when users select and open multiple files at the same time</span></span>](#define)
* [<span data-ttu-id="af57e-269">Zeigen Sie Dateiinhalte in einem Miniaturbild im Datei-Explorer an.</span><span class="sxs-lookup"><span data-stu-id="af57e-269">Show file contents in a thumbnail image within File Explorer</span></span>](#show)
* [<span data-ttu-id="af57e-270">Zeigen Sie Dateiinhalte in einer Vorschau des Datei-Explorers an.</span><span class="sxs-lookup"><span data-stu-id="af57e-270">Show file contents in a Preview pane of File Explorer</span></span>](#preview)
* [<span data-ttu-id="af57e-271">Ermöglichen Sie es Benutzern, Dateien mithilfe der Spalte „Art” im Datei-Explorer zu gruppieren.</span><span class="sxs-lookup"><span data-stu-id="af57e-271">Enable users to group files by using the Kind column in File Explorer</span></span>](#enable)
* [<span data-ttu-id="af57e-272">Stellen Sie den Bereichen Suchen, Index, Eigenschaftendialogfelder und Details Dateieigenschaften zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="af57e-272">Make file properties available to search, index, property dialogs, and the details pane</span></span>](#make-file-properties)

<span id="define" />
### <a name="define-how-your-app-behaves-when-users-select-and-open-multiple-files-at-the-same-time"></a><span data-ttu-id="af57e-273">Definieren Sie, wie sich Ihre App verhält, wenn Benutzer mehrere Dateien gleichzeitig auswählen und öffnen.</span><span class="sxs-lookup"><span data-stu-id="af57e-273">Define how your app behaves when users select and open multiple files at the same time</span></span>

<span data-ttu-id="af57e-274">Geben Sie an, wie sich die App verhält, wenn ein Benutzer mehrere Dateien gleichzeitig öffnet.</span><span class="sxs-lookup"><span data-stu-id="af57e-274">Specify how your app behaves when a user opens multiple files simultaneously.</span></span>

#### <a name="xml-namespaces"></a><span data-ttu-id="af57e-275">XML-Namespaces</span><span class="sxs-lookup"><span data-stu-id="af57e-275">XML namespaces</span></span>

* <span data-ttu-id="af57e-276">http://schemas.microsoft.com/appx/manifest/uap/windows10</span><span class="sxs-lookup"><span data-stu-id="af57e-276">http://schemas.microsoft.com/appx/manifest/uap/windows10</span></span>
* <span data-ttu-id="af57e-277">http://schemas.microsoft.com/appx/manifest/uap/windows10/2</span><span class="sxs-lookup"><span data-stu-id="af57e-277">http://schemas.microsoft.com/appx/manifest/uap/windows10/2</span></span>
* <span data-ttu-id="af57e-278">http://schemas.microsoft.com/appx/manifest/uap/windows10/3</span><span class="sxs-lookup"><span data-stu-id="af57e-278">http://schemas.microsoft.com/appx/manifest/uap/windows10/3</span></span>

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="af57e-279">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="af57e-279">Elements and attributes of this extension</span></span>

```XML
<Extension Category="windows.fileTypeAssociation">
    <FileTypeAssociation Name="[AppID]" MultiSelectModel="[SelectionModel]">
        <SupportedVerbs>
            <Verb Id="Edit" MultiSelectModel="[SelectionModel]">Edit</Verb>
        </SupportedVerbs>
          <SupportedFileTypes>
                <FileType>"[FileExtension]"</FileType>
        </SupportedFileTypes>
</Extension>
```
<span data-ttu-id="af57e-280">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span><span class="sxs-lookup"><span data-stu-id="af57e-280">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span></span>

|<span data-ttu-id="af57e-281">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-281">Name</span></span> |<span data-ttu-id="af57e-282">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="af57e-282">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="af57e-283">Kategorie</span><span class="sxs-lookup"><span data-stu-id="af57e-283">Category</span></span> |<span data-ttu-id="af57e-284">Immer ``windows.fileTypeAssociation``.</span><span class="sxs-lookup"><span data-stu-id="af57e-284">Always ``windows.fileTypeAssociation``.</span></span>
|<span data-ttu-id="af57e-285">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-285">Name</span></span> |<span data-ttu-id="af57e-286">Eine eindeutige ID für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="af57e-286">A unique Id for your app.</span></span> |
|<span data-ttu-id="af57e-287">MultiSelectModel</span><span class="sxs-lookup"><span data-stu-id="af57e-287">MultiSelectModel</span></span> |<span data-ttu-id="af57e-288">Weitere Informationen finden Sie unter unten.</span><span class="sxs-lookup"><span data-stu-id="af57e-288">See below</span></span> |
|<span data-ttu-id="af57e-289">FileType</span><span class="sxs-lookup"><span data-stu-id="af57e-289">FileType</span></span> |<span data-ttu-id="af57e-290">Die relevanten Dateierweiterungen.</span><span class="sxs-lookup"><span data-stu-id="af57e-290">The relevant file extensions.</span></span> |

**<span data-ttu-id="af57e-291">MultSelectModel</span><span class="sxs-lookup"><span data-stu-id="af57e-291">MultSelectModel</span></span>**

<span data-ttu-id="af57e-292">Bei verpackten Desktop-Apps stehen die gleichen drei Optionen zur Verfügung wie bei regulären Desktop-Apps.</span><span class="sxs-lookup"><span data-stu-id="af57e-292">packaged desktop apps have the same three options as regular desktop apps.</span></span>

 * ``Player``<span data-ttu-id="af57e-293">: Ihre App wird ein Mal aktiviert.</span><span class="sxs-lookup"><span data-stu-id="af57e-293">: Your app is activated one time.</span></span> <span data-ttu-id="af57e-294">Alle der ausgewählten Dateien werden an Ihre App als Argument-Parameter übergeben.</span><span class="sxs-lookup"><span data-stu-id="af57e-294">All of the selected files are passed to your app as argument parameters.</span></span>
 * ``Single``<span data-ttu-id="af57e-295">: Ihre App wird einmal für die erste markierte Datei aktiviert.</span><span class="sxs-lookup"><span data-stu-id="af57e-295">: Your app is activated one time for the first selected file.</span></span> <span data-ttu-id="af57e-296">Andere Dateien werden ignoriert.</span><span class="sxs-lookup"><span data-stu-id="af57e-296">Other files are ignored.</span></span>
 * ``Document``<span data-ttu-id="af57e-297">: Für die markierten Dateien wird jeweils eine neue (eigene) Instanz Ihrer App aktiviert.</span><span class="sxs-lookup"><span data-stu-id="af57e-297">: A new, separate instance of your app is activated for each selected file.</span></span>

 <span data-ttu-id="af57e-298">Für unterschiedliche Dateitypen und Aktionen können unterschiedliche Einstellungen festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="af57e-298">You can set different preferences for different file types and actions.</span></span> <span data-ttu-id="af57e-299">So können beispielsweise *Dokumente* im Modus *Document* und *Bilder* im Modus *Player* geöffnet werden.</span><span class="sxs-lookup"><span data-stu-id="af57e-299">For example, you may wish to open *Documents* in *Document* mode and *Images* in *Player* mode.</span></span>

#### <a name="example"></a><span data-ttu-id="af57e-300">Beispiel</span><span class="sxs-lookup"><span data-stu-id="af57e-300">Example</span></span>

```XML
<Package
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
  xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"
  IgnorableNamespaces="uap, uap2, uap3">
  <Applications>
    <Application>
      <Extensions>
        <uap:Extension Category="windows.fileTypeAssociation">
          <uap3:FileTypeAssociation Name="myapp" MultiSelectModel="Document">
            <uap2:SupportedVerbs>
              <uap3:Verb Id="Edit" MultiSelectModel="Player">Edit</uap3:Verb>
              <uap3:Verb Id="Preview" MultiSelectModel="Document">Preview</uap3:Verb>
            </uap2:SupportedVerbs>
            <uap:SupportedFileTypes>
                <uap:FileType>.txt</uap:FileType>
            </uap:SupportedFileTypes>
        </uap:Extension>
      </Extensions>
    </Application>
  </Applications>
</Package>
```

<span data-ttu-id="af57e-301">Wenn der Benutzer 15 oder weniger Dateien öffnet, ist die Standardauswahl des **MultiSelectModel**-Attributs *Player*.</span><span class="sxs-lookup"><span data-stu-id="af57e-301">If the user opens 15 or fewer files, the default choice for the **MultiSelectModel** attribute is *Player*.</span></span> <span data-ttu-id="af57e-302">Andernfalls ist die Standardauswahl *Document*.</span><span class="sxs-lookup"><span data-stu-id="af57e-302">Otherwise, the default is *Document*.</span></span> <span data-ttu-id="af57e-303">UWP-Apps werden immer als *Player* gestartet.</span><span class="sxs-lookup"><span data-stu-id="af57e-303">UWP apps are always started as *Player*.</span></span>

<span id="show" />
### <a name="show-file-contents-in-a-thumbnail-image-within-file-explorer"></a><span data-ttu-id="af57e-304">Zeigen Sie Dateiinhalte in einem Miniaturbild im Datei-Explorer an.</span><span class="sxs-lookup"><span data-stu-id="af57e-304">Show file contents in a thumbnail image within File Explorer</span></span>

<span data-ttu-id="af57e-305">Ermöglichen Sie es Benutzern, eine Miniaturansicht des Dateiinhalts anzuzeigen, wenn das Symbol der Datei in den Größen Mittel, Groß, oder extra Groß angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="af57e-305">Enable users to view a thumbnail image of the file's contents when the icon of the file appears in the medium, large, or extra large size.</span></span>

#### <a name="xml-namespace"></a><span data-ttu-id="af57e-306">XML-Namespace</span><span class="sxs-lookup"><span data-stu-id="af57e-306">XML namespace</span></span>

* <span data-ttu-id="af57e-307">http://schemas.microsoft.com/appx/manifest/uap/windows10</span><span class="sxs-lookup"><span data-stu-id="af57e-307">http://schemas.microsoft.com/appx/manifest/uap/windows10</span></span>
* <span data-ttu-id="af57e-308">http://schemas.microsoft.com/appx/manifest/uap/windows10/2</span><span class="sxs-lookup"><span data-stu-id="af57e-308">http://schemas.microsoft.com/appx/manifest/uap/windows10/2</span></span>
* <span data-ttu-id="af57e-309">http://schemas.microsoft.com/appx/manifest/uap/windows10/3</span><span class="sxs-lookup"><span data-stu-id="af57e-309">http://schemas.microsoft.com/appx/manifest/uap/windows10/3</span></span>
* <span data-ttu-id="af57e-310">http://schemas.microsoft.com/appx/manifest/desktop/windows10/2</span><span class="sxs-lookup"><span data-stu-id="af57e-310">http://schemas.microsoft.com/appx/manifest/desktop/windows10/2</span></span>

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="af57e-311">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="af57e-311">Elements and attributes of this extension</span></span>

```XML
<Extension Category="windows.fileTypeAssociation">
    <FileTypeAssociation Name="[AppID]">
        <SupportedFileTypes>
            <FileType>"[FileExtension]"</FileType>
        </SupportedFileTypes>
        <ThumbnailHandler
            Clsid  ="[Clsid  ]"
            Cutoff="[Cutoff]"
            Treatment="[Treatment]" />
    </FileTypeAssociation>
</Extension>
```

<span data-ttu-id="af57e-312">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span><span class="sxs-lookup"><span data-stu-id="af57e-312">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span></span>

|<span data-ttu-id="af57e-313">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-313">Name</span></span> |<span data-ttu-id="af57e-314">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="af57e-314">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="af57e-315">Kategorie</span><span class="sxs-lookup"><span data-stu-id="af57e-315">Category</span></span> |<span data-ttu-id="af57e-316">Immer ``windows.fileTypeAssociation``.</span><span class="sxs-lookup"><span data-stu-id="af57e-316">Always ``windows.fileTypeAssociation``.</span></span>
|<span data-ttu-id="af57e-317">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-317">Name</span></span> |<span data-ttu-id="af57e-318">Eine eindeutige ID für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="af57e-318">A unique Id for your app.</span></span> |
|<span data-ttu-id="af57e-319">FileType</span><span class="sxs-lookup"><span data-stu-id="af57e-319">FileType</span></span> |<span data-ttu-id="af57e-320">Die relevanten Dateierweiterungen.</span><span class="sxs-lookup"><span data-stu-id="af57e-320">The relevant file extensions.</span></span> |
|<span data-ttu-id="af57e-321">Clsid</span><span class="sxs-lookup"><span data-stu-id="af57e-321">Clsid</span></span>   |<span data-ttu-id="af57e-322">Die Klassen-ID Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="af57e-322">The class ID of your app.</span></span> |
|<span data-ttu-id="af57e-323">Trennungswert</span><span class="sxs-lookup"><span data-stu-id="af57e-323">Cutoff</span></span> |<span data-ttu-id="af57e-324">Die Größe, unter der eine Miniaturansicht nicht verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="af57e-324">The size below which a thumbnail image is not used.</span></span> <span data-ttu-id="af57e-325">Weitere Informationen finden Sie unter [Miniaturansichtscache und Anpassung](https://msdn.microsoft.com/library/windows/desktop/cc144118.aspx#cache)</span><span class="sxs-lookup"><span data-stu-id="af57e-325">See [Thumbnail Cache and Sizing](https://msdn.microsoft.com/library/windows/desktop/cc144118.aspx#cache)</span></span> |
|<span data-ttu-id="af57e-326">Behandlung</span><span class="sxs-lookup"><span data-stu-id="af57e-326">Treatment</span></span> |<span data-ttu-id="af57e-327">Das [Miniaturansicht-Zusatzelement](https://msdn.microsoft.com/library/windows/desktop/cc144118.aspx#adornments), das das Erscheinungsbild des Miniaturansichtsymbols definiert.</span><span class="sxs-lookup"><span data-stu-id="af57e-327">The [thumbnail adornment](https://msdn.microsoft.com/library/windows/desktop/cc144118.aspx#adornments) that defines the look of the thumbnail icon.</span></span> |

#### <a name="example"></a><span data-ttu-id="af57e-328">Beispiel</span><span class="sxs-lookup"><span data-stu-id="af57e-328">Example</span></span>

```XML
<Package
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
  xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"
  xmlns:desktop2="http://schemas.microsoft.com/appx/manifest/desktop/windows10/2"
  IgnorableNamespaces="uap, uap2, uap3, desktop2">
  <Applications>
    <Application>
      <Extensions>
        <uap:Extension Category="windows.fileTypeAssociation">
          <uap3:FileTypeAssociation Name="Contoso">
            <uap2:SupportedFileTypes>
              <uap:FileType>.bar</uap:FileType>
            </uap2:SupportedFileTypes>
            <desktop2:ThumbnailHandler
              Clsid  ="20000000-0000-0000-0000-000000000001"
              Cutoff="20x20"
              Treatment="Video Sprockets" />
            </uap3:FileTypeAssociation>
         </uap::Extension>
      </Extensions>
    </Application>
  </Applications>
</Package>
```

<span id="preview" />
### <a name="show-file-contents-in-the-preview-pane-of-file-explorer"></a><span data-ttu-id="af57e-329">Zeigen Sie Dateiinhalte in der Vorschau des Datei-Explorers an.</span><span class="sxs-lookup"><span data-stu-id="af57e-329">Show file contents in the Preview pane of File Explorer</span></span>

<span data-ttu-id="af57e-330">Ermöglichen Sie es Benutzern, den Inhalt einer Datei in Vorschaubereich des Datei-Explorers anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="af57e-330">Enable users to preview a file's contents in the Preview pane of File Explorer.</span></span>

#### <a name="xml-namespace"></a><span data-ttu-id="af57e-331">XML-Namespace</span><span class="sxs-lookup"><span data-stu-id="af57e-331">XML namespace</span></span>

* <span data-ttu-id="af57e-332">http://schemas.microsoft.com/appx/manifest/uap/windows10</span><span class="sxs-lookup"><span data-stu-id="af57e-332">http://schemas.microsoft.com/appx/manifest/uap/windows10</span></span>
* <span data-ttu-id="af57e-333">http://schemas.microsoft.com/appx/manifest/uap/windows10/2</span><span class="sxs-lookup"><span data-stu-id="af57e-333">http://schemas.microsoft.com/appx/manifest/uap/windows10/2</span></span>
* <span data-ttu-id="af57e-334">http://schemas.microsoft.com/appx/manifest/uap/windows10/3</span><span class="sxs-lookup"><span data-stu-id="af57e-334">http://schemas.microsoft.com/appx/manifest/uap/windows10/3</span></span>
* <span data-ttu-id="af57e-335">http://schemas.microsoft.com/appx/manifest/desktop/windows10/2</span><span class="sxs-lookup"><span data-stu-id="af57e-335">http://schemas.microsoft.com/appx/manifest/desktop/windows10/2</span></span>

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="af57e-336">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="af57e-336">Elements and attributes of this extension</span></span>

```XML
<Extension Category="windows.fileTypeAssociation">
    <FileTypeAssociation Name="[AppID]">
        <SupportedFileTypes>
            <FileType>"[FileExtension]"</FileType>
        </SupportedFileTypes>
        <DesktopPreviewHandler Clsid  ="[Clsid  ]" />
    </FileTypeAssociation>
</Extension>
```

<span data-ttu-id="af57e-337">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span><span class="sxs-lookup"><span data-stu-id="af57e-337">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span></span>

|<span data-ttu-id="af57e-338">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-338">Name</span></span> |<span data-ttu-id="af57e-339">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="af57e-339">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="af57e-340">Kategorie</span><span class="sxs-lookup"><span data-stu-id="af57e-340">Category</span></span> |<span data-ttu-id="af57e-341">Immer ``windows.fileTypeAssociation``.</span><span class="sxs-lookup"><span data-stu-id="af57e-341">Always ``windows.fileTypeAssociation``.</span></span>
|<span data-ttu-id="af57e-342">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-342">Name</span></span> |<span data-ttu-id="af57e-343">Eine eindeutige ID für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="af57e-343">A unique Id for your app.</span></span> |
|<span data-ttu-id="af57e-344">FileType</span><span class="sxs-lookup"><span data-stu-id="af57e-344">FileType</span></span> |<span data-ttu-id="af57e-345">Die relevanten Dateierweiterungen.</span><span class="sxs-lookup"><span data-stu-id="af57e-345">The relevant file extensions.</span></span> |
|<span data-ttu-id="af57e-346">Clsid</span><span class="sxs-lookup"><span data-stu-id="af57e-346">Clsid</span></span>   |<span data-ttu-id="af57e-347">Die Klassen-ID Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="af57e-347">The class ID of your app.</span></span> |

#### <a name="example"></a><span data-ttu-id="af57e-348">Beispiel</span><span class="sxs-lookup"><span data-stu-id="af57e-348">Example</span></span>

```XML
<Package
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
  xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"
  xmlns:desktop2="http://schemas.microsoft.com/appx/manifest/desktop/windows10/2"
  IgnorableNamespaces="uap, uap2, uap3, desktop2">
  <Applications>
    <Application>
      <Extensions>
        <uap:Extension Category="windows.fileTypeAssociation">
          <uap3:FileTypeAssociation Name="Contoso">
            <uap2SupportedFileTypes>
              <uap:FileType>.bar</uap:FileType>
                </uap2SupportedFileTypes>
              <desktop2:DesktopPreviewHandler Clsid ="20000000-0000-0000-0000-000000000001" />
           </uap3:FileTypeAssociation>
        </uap:Extension>
      </Extensions>
    </Application>
  </Applications>
</Package>
```

<span id="enable" />
### <a name="enable-users-to-group-files-by-using-the-kind-column-in-file-explorer"></a><span data-ttu-id="af57e-349">Ermöglichen Sie es Benutzern, Dateien mithilfe der Spalte „Art” im Datei-Explorer zu gruppieren.</span><span class="sxs-lookup"><span data-stu-id="af57e-349">Enable users to group files by using the Kind column in File Explorer</span></span>

<span data-ttu-id="af57e-350">Sie können einen oder mehrere vordefinierte Werte für die Dateitypen mit dem **Art**-Feld zuordnen.</span><span class="sxs-lookup"><span data-stu-id="af57e-350">You can associate one or more predefined values for your file types with the **Kind** field.</span></span>

<span data-ttu-id="af57e-351">Im Datei-Explorer können Benutzer diese Dateien mithilfe dieses Felds gruppieren.</span><span class="sxs-lookup"><span data-stu-id="af57e-351">In File Explorer, users can group those files by using that field.</span></span> <span data-ttu-id="af57e-352">Systemkomponenten verwenden auch dieses Feld für verschiedene Zwecke, wie etwa für die Indizierung.</span><span class="sxs-lookup"><span data-stu-id="af57e-352">System components also use this field for various purposes such as indexing.</span></span>

<span data-ttu-id="af57e-353">Für weitere Informationen zum **Art**-Feld und die Werte, die Sie für dieses Feld verwenden können, finden Sie unter [Art Namen verwenden](https://msdn.microsoft.com/library/windows/desktop/cc144136.aspx).</span><span class="sxs-lookup"><span data-stu-id="af57e-353">For more information about the **Kind** field and the values that you can use for this field, see [Using Kind Names](https://msdn.microsoft.com/library/windows/desktop/cc144136.aspx).</span></span>

#### <a name="xml-namespaces"></a><span data-ttu-id="af57e-354">XML-Namespaces</span><span class="sxs-lookup"><span data-stu-id="af57e-354">XML namespaces</span></span>

* <span data-ttu-id="af57e-355">http://schemas.microsoft.com/appx/manifest/uap/windows10</span><span class="sxs-lookup"><span data-stu-id="af57e-355">http://schemas.microsoft.com/appx/manifest/uap/windows10</span></span>
* <span data-ttu-id="af57e-356">http://schemas.microsoft.com/appx/Manifest/foundation/windows10/restrictedcapabilities/3</span><span class="sxs-lookup"><span data-stu-id="af57e-356">http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities/3</span></span>

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="af57e-357">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="af57e-357">Elements and attributes of this extension</span></span>

```XML
<Extension Category="windows.fileTypeAssociation">
    <FileTypeAssociation Name="[AppID]">
        <SupportedFileTypes>
            <FileType>"[FileExtension]"</FileType>
        </SupportedFileTypes>
        <KindMap>
            <Kind value="[KindValue]">
        </KindMap>
    </FileTypeAssociation>
</Extension>
```
<span data-ttu-id="af57e-358">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span><span class="sxs-lookup"><span data-stu-id="af57e-358">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span></span>

|<span data-ttu-id="af57e-359">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-359">Name</span></span> |<span data-ttu-id="af57e-360">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="af57e-360">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="af57e-361">Kategorie</span><span class="sxs-lookup"><span data-stu-id="af57e-361">Category</span></span> |<span data-ttu-id="af57e-362">Immer ``windows.fileTypeAssociation``.</span><span class="sxs-lookup"><span data-stu-id="af57e-362">Always ``windows.fileTypeAssociation``.</span></span>
|<span data-ttu-id="af57e-363">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-363">Name</span></span> |<span data-ttu-id="af57e-364">Eine eindeutige ID für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="af57e-364">A unique Id for your app.</span></span> |
|<span data-ttu-id="af57e-365">FileType</span><span class="sxs-lookup"><span data-stu-id="af57e-365">FileType</span></span> |<span data-ttu-id="af57e-366">Die relevanten Dateierweiterungen.</span><span class="sxs-lookup"><span data-stu-id="af57e-366">The relevant file extensions.</span></span> |
|<span data-ttu-id="af57e-367">Wert</span><span class="sxs-lookup"><span data-stu-id="af57e-367">value</span></span> |<span data-ttu-id="af57e-368">Ein gültiger [Art-Wert](https://msdn.microsoft.com/en-us/library/windows/desktop/cc144136.aspx#kind_hierarchy)</span><span class="sxs-lookup"><span data-stu-id="af57e-368">A valid [Kind value](https://msdn.microsoft.com/en-us/library/windows/desktop/cc144136.aspx#kind_hierarchy)</span></span> |

#### <a name="example"></a><span data-ttu-id="af57e-369">Beispiel</span><span class="sxs-lookup"><span data-stu-id="af57e-369">Example</span></span>

```XML
<Package
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:rescap="http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities/3"
  IgnorableNamespaces="uap, rescap">
  <Applications>
    <Application>
      <Extensions>
        <uap:Extension Category="windows.fileTypeAssociation">
           <uap:FileTypeAssociation Name="Contoso">
             <uap:SupportedFileTypes>
               <uap:FileType>.m4a</uap:FileType>
               <uap:FileType>.mta</uap:FileType>
             </uap:SupportedFileTypes>
             <rescap:KindMap>
               <rescap:Kind value="Item">
               <rescap:Kind value="Communications">
               <rescap:Kind value="Task">
             </rescap:KindMap>
          </uap:FileTypeAssociation>
      </uap:Extension>
      </Extensions>
    </Application>
  </Applications>
</Package>
```
<span id="make-file-properties" />
### <a name="make-file-properties-available-to-search-index-property-dialogs-and-the-details-pane"></a><span data-ttu-id="af57e-370">Stellen Sie den Bereichen Suchen, Index, Eigenschaftendialogfelder und Details Dateieigenschaften zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="af57e-370">Make file properties available to search, index, property dialogs, and the details pane</span></span>

#### <a name="xml-namespace"></a><span data-ttu-id="af57e-371">XML-Namespace</span><span class="sxs-lookup"><span data-stu-id="af57e-371">XML namespace</span></span>

* <span data-ttu-id="af57e-372">http://schemas.microsoft.com/appx/manifest/uap/windows10</span><span class="sxs-lookup"><span data-stu-id="af57e-372">http://schemas.microsoft.com/appx/manifest/uap/windows10</span></span>
* <span data-ttu-id="af57e-373">http://schemas.microsoft.com/appx/manifest/uap/windows10/3</span><span class="sxs-lookup"><span data-stu-id="af57e-373">http://schemas.microsoft.com/appx/manifest/uap/windows10/3</span></span>
* <span data-ttu-id="af57e-374">http://schemas.microsoft.com/appx/manifest/desktop/windows10/2</span><span class="sxs-lookup"><span data-stu-id="af57e-374">http://schemas.microsoft.com/appx/manifest/desktop/windows10/2</span></span>

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="af57e-375">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="af57e-375">Elements and attributes of this extension</span></span>

```XML
<uap:Extension Category="windows.fileTypeAssociation">
    <uap:FileTypeAssociation Name="[AppID]">
        <SupportedFileTypes>
            <FileType>.bar</FileType>
        </SupportedFileTypes>
        <DesktopPropertyHandler Clsid ="[Clsid ]"/>
    </uap:FileTypeAssociation>
</uap:Extension>
```
**<span data-ttu-id="af57e-376">Wichtige Element- und Attributbeschreibungen</span><span class="sxs-lookup"><span data-stu-id="af57e-376">Key element and attribute descriptions</span></span>**

<span data-ttu-id="af57e-377">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span><span class="sxs-lookup"><span data-stu-id="af57e-377">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span></span>

|<span data-ttu-id="af57e-378">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-378">Name</span></span> |<span data-ttu-id="af57e-379">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="af57e-379">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="af57e-380">Kategorie</span><span class="sxs-lookup"><span data-stu-id="af57e-380">Category</span></span> |<span data-ttu-id="af57e-381">Immer ``windows.fileTypeAssociation``.</span><span class="sxs-lookup"><span data-stu-id="af57e-381">Always ``windows.fileTypeAssociation``.</span></span>
|<span data-ttu-id="af57e-382">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-382">Name</span></span> |<span data-ttu-id="af57e-383">Eine eindeutige ID für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="af57e-383">A unique Id for your app.</span></span> |
|<span data-ttu-id="af57e-384">FileType</span><span class="sxs-lookup"><span data-stu-id="af57e-384">FileType</span></span> |<span data-ttu-id="af57e-385">Die relevanten Dateierweiterungen.</span><span class="sxs-lookup"><span data-stu-id="af57e-385">The relevant file extensions.</span></span> |
|<span data-ttu-id="af57e-386">Clsid</span><span class="sxs-lookup"><span data-stu-id="af57e-386">Clsid</span></span>  |<span data-ttu-id="af57e-387">Die Klassen-ID Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="af57e-387">The class ID of your app.</span></span> |

#### <a name="example"></a><span data-ttu-id="af57e-388">Beispiel</span><span class="sxs-lookup"><span data-stu-id="af57e-388">Example</span></span>

```XML
<Package
  xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
  xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"
  xmlns:desktop2="http://schemas.microsoft.com/appx/manifest/desktop/windows10/2"
  IgnorableNamespaces="uap, uap3, desktop2">
  <Applications>
    <Application>
      <Extensions>
        <uap:Extension Category="windows.fileTypeAssociation">
          <uap3:FileTypeAssociation Name="Contoso">
            <uap:SupportedFileTypes>
              <uap:FileType>.bar</uap:FileType>
            </uap:SupportedFileTypes>
            <desktop2:DesktopPropertyHandler Clsid ="20000000-0000-0000-0000-000000000001"/>
          </uap3:FileTypeAssociation>
        </uap:Extension>
      </Extensions>
    </Application>
  </Applications>
</Package>
```

<span id="start" />
## <a name="start-your-app-in-different-ways"></a><span data-ttu-id="af57e-389">Starten Sie Ihre App auf unterschiedlicher Weise.</span><span class="sxs-lookup"><span data-stu-id="af57e-389">Start your app in different ways</span></span>

* [<span data-ttu-id="af57e-390">Starten Sie die App über ein Protokoll.</span><span class="sxs-lookup"><span data-stu-id="af57e-390">Start your app by using a protocol</span></span>](#protocol)
* [<span data-ttu-id="af57e-391">Starten Sie Ihre App unter Verwendung eines Alias.</span><span class="sxs-lookup"><span data-stu-id="af57e-391">Start your app by using an alias</span></span>](#alias)
* [<span data-ttu-id="af57e-392">Starten Sie eine ausführbare Datei, wenn Benutzer sich bei Windows anmelden.</span><span class="sxs-lookup"><span data-stu-id="af57e-392">Start an executable file when users log into Windows</span></span>](#executable)
* [<span data-ttu-id="af57e-393">Nach dem Empfang einer Aktualisierung aus dem Windows Store starten Sie automatisch neu</span><span class="sxs-lookup"><span data-stu-id="af57e-393">Restart automatically after receiving an update from the Windows Store</span></span>](#updates)

<span id="protocol" />
### <a name="start-your-app-by-using-a-protocol"></a><span data-ttu-id="af57e-394">Starten Sie die App über ein Protokoll.</span><span class="sxs-lookup"><span data-stu-id="af57e-394">Start your app by using a protocol</span></span>

<span data-ttu-id="af57e-395">Protokollzuordnungen ermöglichen es anderen Programmen und Systemkomponenten, mit ihrer verpackten App zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="af57e-395">Protocol associations can enable other programs and system components to interoperate with your packaged app.</span></span> <span data-ttu-id="af57e-396">Wenn Ihre verpackte App anhand eines Protokolls gestartet wird, können Sie bestimmte Parameter angeben, die an die Aktivierungsereignisargumente übergeben werden sollen, um ein entsprechendes Verhalten zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="af57e-396">When your packaged app is started by using a protocol, you can specify specific parameters to pass to its activation event arguments so it can behave accordingly.</span></span> <span data-ttu-id="af57e-397">Parameter werden nur für verpackte, vertrauenswürdige Apps unterstützt.</span><span class="sxs-lookup"><span data-stu-id="af57e-397">Parameters are supported only for packaged, full-trust apps.</span></span> <span data-ttu-id="af57e-398">UWP-Apps können die Parameter nicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="af57e-398">UWP apps can't use parameters.</span></span>  

#### <a name="xml-namespace"></a><span data-ttu-id="af57e-399">XML-Namespace</span><span class="sxs-lookup"><span data-stu-id="af57e-399">XML namespace</span></span>

<span data-ttu-id="af57e-400">http://schemas.microsoft.com/appx/manifest/uap/windows10/3</span><span class="sxs-lookup"><span data-stu-id="af57e-400">http://schemas.microsoft.com/appx/manifest/uap/windows10/3</span></span>


#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="af57e-401">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="af57e-401">Elements and attributes of this extension</span></span>

```XML
<Extension
    Category="windows.protocol">
    <Protocol
      Name="[Protocol name]"
      Parameters="[Parameters]" />
</Extension>
```

<span data-ttu-id="af57e-402">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-protocol).</span><span class="sxs-lookup"><span data-stu-id="af57e-402">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-protocol).</span></span>

|<span data-ttu-id="af57e-403">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-403">Name</span></span> |<span data-ttu-id="af57e-404">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="af57e-404">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="af57e-405">Kategorie</span><span class="sxs-lookup"><span data-stu-id="af57e-405">Category</span></span> |<span data-ttu-id="af57e-406">Immer ``windows.protocol``.</span><span class="sxs-lookup"><span data-stu-id="af57e-406">Always ``windows.protocol``.</span></span>
|<span data-ttu-id="af57e-407">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-407">Name</span></span> |<span data-ttu-id="af57e-408">Der Name des Protokolls.</span><span class="sxs-lookup"><span data-stu-id="af57e-408">The name of the protocol.</span></span> |
|<span data-ttu-id="af57e-409">Parameter</span><span class="sxs-lookup"><span data-stu-id="af57e-409">Parameters</span></span> |<span data-ttu-id="af57e-410">Die Liste der Parameter und Werte, die bei der Aktivierung Ihrer App als Ereignisargumente an Ihre App übergeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="af57e-410">The list of parameters and values to pass to your app as event arguments when the app is activated.</span></span> <span data-ttu-id="af57e-411">Wenn eine Variable einen Dateipfad enthalten kann, schließen Sie den Parameterwert in Anführungszeichen.</span><span class="sxs-lookup"><span data-stu-id="af57e-411">If a variable can contain a file path, wrap the parameter value in quotes.</span></span> <span data-ttu-id="af57e-412">Dadurch werden jegliche Probleme vermieden, die in Fällen auftreten, bei denen der Pfad Leerzeichen enthält.</span><span class="sxs-lookup"><span data-stu-id="af57e-412">That will avoid any issues that happen in cases where the path includes spaces.</span></span> |

### <a name="example"></a><span data-ttu-id="af57e-413">Beispiel</span><span class="sxs-lookup"><span data-stu-id="af57e-413">Example</span></span>

```XML
<Package
  xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"
  IgnorableNamespaces="uap3">
  <Applications>
    <Application>
      <Extensions>
        <uap3:Extension
          Category="windows.protocol">
        <uap3:Protocol
          Name="myapp-cmd"
          Parameters="/p &quot;%1&quot;" />
        </uap3:Extension>
      </Extensions>
    </Application>
  </Applications>
</Package>
```
<span id="alias" />
### <a name="start-your-app-by-using-an-alias"></a><span data-ttu-id="af57e-414">Starten Sie Ihre App unter Verwendung eines Alias.</span><span class="sxs-lookup"><span data-stu-id="af57e-414">Start your app by using an alias</span></span>

<span data-ttu-id="af57e-415">Benutzer und andere Prozesse können einen Alias verwenden, um Ihre App zu starten, ohne den vollständigen Pfad zu Ihrer App angeben zu müssen.</span><span class="sxs-lookup"><span data-stu-id="af57e-415">Users and other processes can use an alias to start your app without having to specify the full path to your app.</span></span> <span data-ttu-id="af57e-416">Sie können diesen Aliasnamen angeben.</span><span class="sxs-lookup"><span data-stu-id="af57e-416">You can specify that alias name.</span></span>

#### <a name="xml-namespaces"></a><span data-ttu-id="af57e-417">XML-Namespaces</span><span class="sxs-lookup"><span data-stu-id="af57e-417">XML namespaces</span></span>

* <span data-ttu-id="af57e-418">http://schemas.microsoft.com/appx/manifest/uap/windows10/3</span><span class="sxs-lookup"><span data-stu-id="af57e-418">http://schemas.microsoft.com/appx/manifest/uap/windows10/3</span></span>
* <span data-ttu-id="af57e-419">http://schemas.microsoft.com/appx/manifest/desktop/windows10</span><span class="sxs-lookup"><span data-stu-id="af57e-419">http://schemas.microsoft.com/appx/manifest/desktop/windows10</span></span>


#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="af57e-420">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="af57e-420">Elements and attributes of this extension</span></span>

```XML
<Extension
    Category="windows.appExecutionAlias"
    Executable="[ExecutableName]"
    EntryPoint="Windows.FullTrustApplication">
    <AppExecutionAlias>
            <desktop:ExecutionAlias Alias="[AliasName]" />
      </AppExecutionAlias>
</Extension>
```

|<span data-ttu-id="af57e-421">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-421">Name</span></span> |<span data-ttu-id="af57e-422">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="af57e-422">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="af57e-423">Kategorie</span><span class="sxs-lookup"><span data-stu-id="af57e-423">Category</span></span> |<span data-ttu-id="af57e-424">Immer ``windows.appExecutionAlias``.</span><span class="sxs-lookup"><span data-stu-id="af57e-424">Always ``windows.appExecutionAlias``.</span></span>
|<span data-ttu-id="af57e-425">Ausführbare Datei</span><span class="sxs-lookup"><span data-stu-id="af57e-425">Executable</span></span> |<span data-ttu-id="af57e-426">Der relative Pfad zur ausführbaren Datei, die beim Aufrufen des Alias gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="af57e-426">The relative path to the executable to start when the alias is invoked.</span></span> |
|<span data-ttu-id="af57e-427">Alias</span><span class="sxs-lookup"><span data-stu-id="af57e-427">Alias</span></span> |<span data-ttu-id="af57e-428">Der kurze Name für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="af57e-428">The short name for your app.</span></span> <span data-ttu-id="af57e-429">Er muss immer mit der Erweiterung „.exe“ enden.</span><span class="sxs-lookup"><span data-stu-id="af57e-429">It must always end with the ".exe" extension.</span></span> <span data-ttu-id="af57e-430">Für die einzelnen Anwendungen im Paket kann immer nur einzelner App-Ausführungsalias angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="af57e-430">You can only specify a single app execution alias for each application in the package.</span></span> <span data-ttu-id="af57e-431">Wenn sich mehrere Apps mit dem gleichen Alias registrieren, ruft das System die zuletzt registrierte App auf. Wählen Sie daher einen eindeutigen Alias, um die Wahrscheinlichkeit einer Überschreibung durch andere Apps möglichst gering zu halten.</span><span class="sxs-lookup"><span data-stu-id="af57e-431">If multiple apps register for the same alias, the system will invoke the last one that was registered, so make sure to choose a unique alias other apps are unlikely to override.</span></span>
|

#### <a name="example"></a><span data-ttu-id="af57e-432">Beispiel</span><span class="sxs-lookup"><span data-stu-id="af57e-432">Example</span></span>

```XML
<Package
  xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"
  xmlns:desktop="http://schemas.microsoft.com/appx/manifest/desktop/windows10"
  IgnorableNamespaces="uap3, desktop">
  ...
  <uap3:Extension
        Category="windows.appExecutionAlias"
        Executable="exes\launcher.exe"
        EntryPoint="Windows.FullTrustApplication">
        <uap3:AppExecutionAlias>
            <desktop:ExecutionAlias Alias="Contoso.exe" />
        </uap3:AppExecutionAlias>
  </uap3:Extension>
...
</Package>
```

<span data-ttu-id="af57e-433">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span><span class="sxs-lookup"><span data-stu-id="af57e-433">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span></span>

|<span data-ttu-id="af57e-434">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-434">Name</span></span> |<span data-ttu-id="af57e-435">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="af57e-435">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="af57e-436">Kategorie</span><span class="sxs-lookup"><span data-stu-id="af57e-436">Category</span></span> |<span data-ttu-id="af57e-437">Immer ``windows.fileTypeAssociation``.</span><span class="sxs-lookup"><span data-stu-id="af57e-437">Always ``windows.fileTypeAssociation``.</span></span>
|<span data-ttu-id="af57e-438">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-438">Name</span></span> |<span data-ttu-id="af57e-439">Eine eindeutige ID für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="af57e-439">A unique Id for your app.</span></span> <span data-ttu-id="af57e-440">Diese ID wird intern verwendet, um einen [programmgesteuerte Bezeichner (Programm-ID)](https://msdn.microsoft.com/library/windows/desktop/cc144152.aspx) mit Hash zu generieren, die mit Ihrer Dateitypzuordnung verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="af57e-440">This Id is used internally to generate a hashed [programmatic identifier (ProgID)](https://msdn.microsoft.com/library/windows/desktop/cc144152.aspx) associated with your file type association.</span></span> <span data-ttu-id="af57e-441">Mithilfe dieser ID können Sie Änderungen in zukünftigen Versionen Ihrer App verwalten.</span><span class="sxs-lookup"><span data-stu-id="af57e-441">You can use this Id to manage changes in future versions of your app.</span></span>   |
|<span data-ttu-id="af57e-442">FileType</span><span class="sxs-lookup"><span data-stu-id="af57e-442">FileType</span></span> |<span data-ttu-id="af57e-443">Die Erweiterung, die von Ihrer App unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="af57e-443">The file extension supported by your app.</span></span> |

<span id="executable" />
### <a name="start-an-executable-file-when-users-log-into-windows"></a><span data-ttu-id="af57e-444">Starten Sie eine ausführbare Datei, wenn Benutzer sich bei Windows anmelden.</span><span class="sxs-lookup"><span data-stu-id="af57e-444">Start an executable file when users log into Windows</span></span>

<span data-ttu-id="af57e-445">Startaufgaben ermöglichen der App das automatische Ausführen einer ausführbaren Datei, wenn sich ein Benutzer anmeldet.</span><span class="sxs-lookup"><span data-stu-id="af57e-445">Startup tasks allow your app to run an executable automatically whenever a user logs on.</span></span>

> [!NOTE]
> <span data-ttu-id="af57e-446">Der Benutzer muss Ihre App mindestens ein Mal starten, um diese Startaufgabe registrieren.</span><span class="sxs-lookup"><span data-stu-id="af57e-446">The user has to start your app at least one time to register this startup task.</span></span>

<span data-ttu-id="af57e-447">Ihre App kann mehrere Startaufgaben deklarieren.</span><span class="sxs-lookup"><span data-stu-id="af57e-447">Your app can declare multiple startup tasks.</span></span> <span data-ttu-id="af57e-448">Die Aufgaben beginnen unabhängig voneinander.</span><span class="sxs-lookup"><span data-stu-id="af57e-448">Each task starts independently.</span></span> <span data-ttu-id="af57e-449">Alle Startaufgaben werden im Task-Manager auf der Registerkarte **Autostart** mit dem Namen aus Ihrem App-Manifest und dem Symbol Ihrer App angezeigt.</span><span class="sxs-lookup"><span data-stu-id="af57e-449">All startup tasks will appear in Task Manager under the **Startup** tab with the name that you specify in your app's manifest and your app's icon.</span></span> <span data-ttu-id="af57e-450">Der Task-Manager analysiert automatisch die Startauswirkungen Ihrer Aufgaben.</span><span class="sxs-lookup"><span data-stu-id="af57e-450">Task Manager will automatically analyze the startup impact of your tasks.</span></span>

<span data-ttu-id="af57e-451">Benutzer können die Startaufgabe Ihrer App manuell mithilfe des Task-Managers deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="af57e-451">Users can manually disable your app's startup task by using Task Manager.</span></span> <span data-ttu-id="af57e-452">Wenn ein Benutzer eine Aufgabe deaktiviert, können Sie sie nicht erneut programmgesteuert aktivieren.</span><span class="sxs-lookup"><span data-stu-id="af57e-452">If a user disables a task, you can't programmatically re-enable it.</span></span>

#### <a name="xml-namespace"></a><span data-ttu-id="af57e-453">XML-Namespace</span><span class="sxs-lookup"><span data-stu-id="af57e-453">XML namespace</span></span>

<span data-ttu-id="af57e-454">http://schemas.microsoft.com/appx/manifest/desktop/windows10</span><span class="sxs-lookup"><span data-stu-id="af57e-454">http://schemas.microsoft.com/appx/manifest/desktop/windows10</span></span>

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="af57e-455">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="af57e-455">Elements and attributes of this extension</span></span>

```XML
<Extension
    Category="windows.startupTask"
    Executable="[ExecutableName]"
    EntryPoint="Windows.FullTrustApplication">
    <StartupTask
      TaskId="[TaskID]"
      Enabled="true"
      DisplayName="[DisplayName]" />
</Extension>
```

|<span data-ttu-id="af57e-456">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-456">Name</span></span> |<span data-ttu-id="af57e-457">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="af57e-457">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="af57e-458">Kategorie</span><span class="sxs-lookup"><span data-stu-id="af57e-458">Category</span></span> |<span data-ttu-id="af57e-459">Immer ``windows.startupTask``.</span><span class="sxs-lookup"><span data-stu-id="af57e-459">Always ``windows.startupTask``.</span></span>|
|<span data-ttu-id="af57e-460">Ausführbare Datei</span><span class="sxs-lookup"><span data-stu-id="af57e-460">Executable</span></span> |<span data-ttu-id="af57e-461">Der relative Pfad der ausführbaren Datei, die gestartet werden soll.</span><span class="sxs-lookup"><span data-stu-id="af57e-461">The relative path to the executable file to start.</span></span> |
|<span data-ttu-id="af57e-462">TaskId</span><span class="sxs-lookup"><span data-stu-id="af57e-462">TaskId</span></span> |<span data-ttu-id="af57e-463">Ein eindeutiger Bezeichner Ihrer Aufgabe.</span><span class="sxs-lookup"><span data-stu-id="af57e-463">A unique identifier for your task.</span></span> <span data-ttu-id="af57e-464">Mit diesem Bezeichner kann Ihre App die APIs in der [Windows.ApplicationModel.StartupTask](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.StartupTask)-Klasse aufrufen, um eine Startaufgabe programmgesteuert zu aktivieren oder zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="af57e-464">Using this identifier, your app can call the APIs in the [Windows.ApplicationModel.StartupTask](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.StartupTask) class to programmatically enable or disable a startup task.</span></span> |
|<span data-ttu-id="af57e-465">Enabled</span><span class="sxs-lookup"><span data-stu-id="af57e-465">Enabled</span></span> |<span data-ttu-id="af57e-466">Gibt an, ob die Aufgabe erst aktiviert oder deaktiviert gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="af57e-466">Indicates whether the task first starts enabled or disabled.</span></span> <span data-ttu-id="af57e-467">Aktivierte Aufgaben werden bei der nächsten Anmeldung des Benutzers ausgeführt (es sei denn, der Benutzer deaktiviert sie).</span><span class="sxs-lookup"><span data-stu-id="af57e-467">Enabled tasks will run the next time the user logs on (unless the user disables it).</span></span> |
|<span data-ttu-id="af57e-468">DisplayName</span><span class="sxs-lookup"><span data-stu-id="af57e-468">DisplayName</span></span> |<span data-ttu-id="af57e-469">Der Name der Aufgabe, die im Task-Manager angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="af57e-469">The name of the task that appears in Task Manager.</span></span> <span data-ttu-id="af57e-470">Sie können diese Zeichenfolge mit ```ms-resource``` lokalisieren.</span><span class="sxs-lookup"><span data-stu-id="af57e-470">You can localize this string by using ```ms-resource```.</span></span> |

#### <a name="example"></a><span data-ttu-id="af57e-471">Beispiel</span><span class="sxs-lookup"><span data-stu-id="af57e-471">Example</span></span>

```XML
<Package
  xmlns:desktop="http://schemas.microsoft.com/appx/manifest/desktop/windows10"
  IgnorableNamespaces="desktop">
  <Applications>
    <Application>
      <Extensions>
        <desktop:Extension
          Category="windows.startupTask"
          Executable="bin\MyStartupTask.exe"
          EntryPoint="Windows.FullTrustApplication">
          <desktop:StartupTask
          TaskId="MyStartupTask"
          Enabled="true"
          DisplayName="My App Service" />
        </desktop:Extension>
      </Extensions>
    </Application>
  </Applications>
 </Package>
```

<span id="updates" />
### <a name="restart-automatically-after-receiving-an-update-from-the-windows-store"></a><span data-ttu-id="af57e-472">Nach dem Empfang einer Aktualisierung aus dem Windows Store starten Sie automatisch neu</span><span class="sxs-lookup"><span data-stu-id="af57e-472">Restart automatically after receiving an update from the Windows Store</span></span>

<span data-ttu-id="af57e-473">Wenn Ihre App geöffnet ist, wenn Benutzer ein Update installieren, wird die App geschlossen.</span><span class="sxs-lookup"><span data-stu-id="af57e-473">If your app is open when users install an update to it, the app closes.</span></span>

<span data-ttu-id="af57e-474">Wenn Sie möchten, dass die App neu startet, nachdem das Update abgeschlossen ist, rufen Sie die [RegisterApplicationRestart ist](https://msdn.microsoft.com/library/windows/desktop/aa373347.aspx) Funktion in jedem neu zu startenden Prozess auf.</span><span class="sxs-lookup"><span data-stu-id="af57e-474">If you want that app to restart after the update completes, call the  [RegisterApplicationRestart](https://msdn.microsoft.com/library/windows/desktop/aa373347.aspx) function in every process that you want to restart.</span></span>

<span data-ttu-id="af57e-475">Jedes aktiven Fenster in Ihrer App erhält eine [WM_QUERYENDSESSION](https://msdn.microsoft.com/library/windows/desktop/aa376890.aspx) Nachricht.</span><span class="sxs-lookup"><span data-stu-id="af57e-475">Each active window in your app receives a [WM_QUERYENDSESSION](https://msdn.microsoft.com/library/windows/desktop/aa376890.aspx) message.</span></span> <span data-ttu-id="af57e-476">An diesem Punkt kann Ihre App die [RegisterApplicationRestart ist](https://msdn.microsoft.com/library/windows/desktop/aa373347.aspx) Funktion erneut aufrufen, um die Befehlszeile bei Bedarf zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="af57e-476">At this point, your app can call the [RegisterApplicationRestart](https://msdn.microsoft.com/library/windows/desktop/aa373347.aspx) function again to update the command line if necessary.</span></span>

<span data-ttu-id="af57e-477">Wenn jedes aktiven Fenster in Ihre App die [WM_ENDSESSION](https://msdn.microsoft.com/library/windows/desktop/aa376889.aspx)-Nachricht erhält, sollte die App die Daten speichern und herunterfahren.</span><span class="sxs-lookup"><span data-stu-id="af57e-477">When each active window in your app receives the [WM_ENDSESSION](https://msdn.microsoft.com/library/windows/desktop/aa376889.aspx) message, your app should save data and shut down.</span></span>

>[!NOTE]
<span data-ttu-id="af57e-478">Die aktiven Fenster erhalte ebenfalls die [WM_CLOSE](https://msdn.microsoft.com/library/windows/desktop/ms632617.aspx)-Nachricht falls die App nicht die [WM_ENDSESSION](https://msdn.microsoft.com/library/windows/desktop/aa376889.aspx)-Nachricht behandelt.</span><span class="sxs-lookup"><span data-stu-id="af57e-478">Your active windows also receive the [WM_CLOSE](https://msdn.microsoft.com/library/windows/desktop/ms632617.aspx) message in case the app doesn't handle the [WM_ENDSESSION](https://msdn.microsoft.com/library/windows/desktop/aa376889.aspx) message.</span></span>

<span data-ttu-id="af57e-479">Zu diesem Zeitpunkt hat Ihre App 30Sekunden, um ihre eigenen Prozesse zu schließen (oder die Plattform beendet diese).</span><span class="sxs-lookup"><span data-stu-id="af57e-479">At this point, your app has 30 seconds to close it's own processes or the platform terminates them forcefully.</span></span>

<span data-ttu-id="af57e-480">Nachdem das Update abgeschlossen ist, startet Ihre App neu.</span><span class="sxs-lookup"><span data-stu-id="af57e-480">After the update is complete, your app restarts.</span></span>

## <a name="work-with-other-applications"></a><span data-ttu-id="af57e-481">Zusammenarbeit mit anderen Anwendungen</span><span class="sxs-lookup"><span data-stu-id="af57e-481">Work with other applications</span></span>

<span data-ttu-id="af57e-482">Mit anderen Apps integrieren, andere Prozesse starten oder Informationen freigeben.</span><span class="sxs-lookup"><span data-stu-id="af57e-482">Integrate with other apps, start other processes or share information.</span></span>

* [<span data-ttu-id="af57e-483">Legen Sie Ihre App als Druckerziel in Anwendungen fest, die das Drucken unterstützen.</span><span class="sxs-lookup"><span data-stu-id="af57e-483">Make your app appear as the print target in applications that support printing</span></span>](#printing)
* [<span data-ttu-id="af57e-484">Freigeben von Schriftarten für andere Windows-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="af57e-484">Share fonts with other Windows applications</span></span>](#fonts)
* [<span data-ttu-id="af57e-485">Starten Sie einen Win32-Prozess aus einer Universellen Windows-Plattform-App (UWP-App).</span><span class="sxs-lookup"><span data-stu-id="af57e-485">Start a Win32 process from a Universal Windows Platform (UWP) app</span></span>](#win32-process)

<span id="printing" />
### <a name="make-your-app-appear-as-the-print-target-in-applications-that-support-printing"></a><span data-ttu-id="af57e-486">Legen Sie Ihre App als Druckerziel in Anwendungen fest, die das Drucken unterstützen.</span><span class="sxs-lookup"><span data-stu-id="af57e-486">Make your app appear as the print target in applications that support printing</span></span>

<span data-ttu-id="af57e-487">Wenn Benutzer Benutzer Daten aus einer anderen App wie z.B. Editor drucken möchten, können Sie Ihre App als Druckerziel in der App-Liste der verfügbaren Druckerziele anzeigen lassen.</span><span class="sxs-lookup"><span data-stu-id="af57e-487">When users want to print data from another app such as Notepad, you can make your app appear as a print target in the app's list of available print targets.</span></span>

<span data-ttu-id="af57e-488">Sie müssen Ihre App so einrichten, dass sie Daten im XML Paper Specification-Format (XPS-Format) empfängt.</span><span class="sxs-lookup"><span data-stu-id="af57e-488">You'll have to modify your app so that it receives print data in XML Paper Specification (XPS) format.</span></span>

#### <a name="xml-namespaces"></a><span data-ttu-id="af57e-489">XML-Namespaces</span><span class="sxs-lookup"><span data-stu-id="af57e-489">XML namespaces</span></span>

<span data-ttu-id="af57e-490">http://schemas.microsoft.com/appx/manifest/desktop/windows10/2</span><span class="sxs-lookup"><span data-stu-id="af57e-490">http://schemas.microsoft.com/appx/manifest/desktop/windows10/2</span></span>

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="af57e-491">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="af57e-491">Elements and attributes of this extension</span></span>

```XML
<Extension Category="windows.appPrinter">
    <AppPrinter
        DisplayName="[DisplayName]"
        Parameters="[Parameters]" />
</Extension>
```

<span data-ttu-id="af57e-492">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-desktop2-appprinter).</span><span class="sxs-lookup"><span data-stu-id="af57e-492">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-desktop2-appprinter).</span></span>

|<span data-ttu-id="af57e-493">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-493">Name</span></span> |<span data-ttu-id="af57e-494">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="af57e-494">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="af57e-495">Kategorie</span><span class="sxs-lookup"><span data-stu-id="af57e-495">Category</span></span> |<span data-ttu-id="af57e-496">Immer ``windows.appPrinter``.</span><span class="sxs-lookup"><span data-stu-id="af57e-496">Always ``windows.appPrinter``.</span></span>
|<span data-ttu-id="af57e-497">DisplayName</span><span class="sxs-lookup"><span data-stu-id="af57e-497">DisplayName</span></span> |<span data-ttu-id="af57e-498">Der Name, der in der Liste der Druckerziele für eine App angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="af57e-498">The name that you want to appear in the list of print targets for an app.</span></span> |
|<span data-ttu-id="af57e-499">Parameter</span><span class="sxs-lookup"><span data-stu-id="af57e-499">Parameters</span></span> |<span data-ttu-id="af57e-500">Parameter, die Ihre App benötigt, um die Anforderung ordnungsgemäß zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="af57e-500">Any parameters that your app requires to properly handle the request.</span></span> |

#### <a name="example"></a><span data-ttu-id="af57e-501">Beispiel</span><span class="sxs-lookup"><span data-stu-id="af57e-501">Example</span></span>

```XML
<Package
  xmlns:desktop2="http://schemas.microsoft.com/appx/manifest/desktop/windows10/2"
  IgnorableNamespaces="desktop2">
  <Applications>
  <Application>
    <Extensions>
      <desktop2:Extension Category="windows.appPrinter">
        <desktop2:AppPrinter
          DisplayName="Send to Contoso"
          Parameters="/insertdoc %1" />
      </desktop2:Extension>
    </Extensions>
  </Application>
</Applications>
</Package>
```
<span data-ttu-id="af57e-502">Suchen Sie [hier](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/PrintToPDF) ein Beispiel, in dem diese Erweiterung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="af57e-502">Find a sample that uses this extension [Here](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/PrintToPDF)</span></span>

<span id="fonts" />
### <a name="share-fonts-with-other-windows-applications"></a><span data-ttu-id="af57e-503">Freigeben von Schriftarten für andere Windows-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="af57e-503">Share fonts with other Windows applications</span></span>

<span data-ttu-id="af57e-504">Teilen Sie Ihre benutzerdefinierten Schriftarten mit einer anderen Windows-Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="af57e-504">Share your custom fonts with other Windows applications.</span></span>

#### <a name="xml-namespaces"></a><span data-ttu-id="af57e-505">XML-Namespaces</span><span class="sxs-lookup"><span data-stu-id="af57e-505">XML namespaces</span></span>

<span data-ttu-id="af57e-506">http://schemas.microsoft.com/appx/manifest/desktop/windows10/2</span><span class="sxs-lookup"><span data-stu-id="af57e-506">http://schemas.microsoft.com/appx/manifest/desktop/windows10/2</span></span>

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="af57e-507">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="af57e-507">Elements and attributes of this extension</span></span>

```XML
<Extension Category="windows.sharedFonts">
    <SharedFonts>
      <Font File="[FontFile]" />
    </SharedFonts>
  </Extension>
```

<span data-ttu-id="af57e-508">Die vollständige Schemareferenz finden Sie [hier](https://review.docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap4-sharedfonts).</span><span class="sxs-lookup"><span data-stu-id="af57e-508">Find the complete schema reference [here](https://review.docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap4-sharedfonts).</span></span>


|<span data-ttu-id="af57e-509">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-509">Name</span></span> |<span data-ttu-id="af57e-510">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="af57e-510">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="af57e-511">Kategorie</span><span class="sxs-lookup"><span data-stu-id="af57e-511">Category</span></span> |<span data-ttu-id="af57e-512">Immer ``windows.sharedFonts``.</span><span class="sxs-lookup"><span data-stu-id="af57e-512">Always ``windows.sharedFonts``.</span></span>
|<span data-ttu-id="af57e-513">Datei</span><span class="sxs-lookup"><span data-stu-id="af57e-513">File</span></span> |<span data-ttu-id="af57e-514">Die Datei mit der Schriftart, die Sie teilen möchten.</span><span class="sxs-lookup"><span data-stu-id="af57e-514">The file that contains the fonts that you want to share.</span></span> |

#### <a name="example"></a><span data-ttu-id="af57e-515">Beispiel</span><span class="sxs-lookup"><span data-stu-id="af57e-515">Example</span></span>

```XML
<Package
  xmlns:uap4="http://schemas.microsoft.com/appx/manifest/uap/windows10/4"
  IgnorableNamespaces="uap4">
  <Applications>
    <Application>
      <Extensions>
        <uap4:Extension Category="windows.sharedFonts">
          <uap4:SharedFonts>
            <uap4:Font File="Fonts\JustRealize.ttf" />
            <uap4:Font File="Fonts\JustRealizeBold.ttf" />
          </uap4:SharedFonts>
        </uap4:Extension>
      </Extensions>
    </Application>
  </Applications>
</Package>
```
<span id="win32-process" />
### <a name="start-a-win32-process-from-a-universal-windows-platform-uwp-app"></a><span data-ttu-id="af57e-516">Starten Sie einen Win32-Prozess aus einer Universellen Windows-Plattform-App (UWP-App).</span><span class="sxs-lookup"><span data-stu-id="af57e-516">Start a Win32 process from a Universal Windows Platform (UWP) app</span></span>

<span data-ttu-id="af57e-517">Starten Sie einen vertrauenswürdigen Win32-Prozess.</span><span class="sxs-lookup"><span data-stu-id="af57e-517">Start a Win32 process that runs in full-trust.</span></span>

#### <a name="xml-namespaces"></a><span data-ttu-id="af57e-518">XML-Namespaces</span><span class="sxs-lookup"><span data-stu-id="af57e-518">XML namespaces</span></span>

<span data-ttu-id="af57e-519">http://schemas.microsoft.com/appx/manifest/desktop/windows10</span><span class="sxs-lookup"><span data-stu-id="af57e-519">http://schemas.microsoft.com/appx/manifest/desktop/windows10</span></span>

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="af57e-520">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="af57e-520">Elements and attributes of this extension</span></span>

```XML
<xtension Category="windows.fullTrustProcess" Executable="[executable file]">
  <FullTrustProcess>
    <ParameterGroup GroupId="[GroupID]" Parameters="[Parameters]"/>
  </FullTrustProcess>
</Extension>
```

|<span data-ttu-id="af57e-521">Name</span><span class="sxs-lookup"><span data-stu-id="af57e-521">Name</span></span> |<span data-ttu-id="af57e-522">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="af57e-522">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="af57e-523">Kategorie</span><span class="sxs-lookup"><span data-stu-id="af57e-523">Category</span></span> |<span data-ttu-id="af57e-524">Immer ``windows.fullTrustProcess``.</span><span class="sxs-lookup"><span data-stu-id="af57e-524">Always ``windows.fullTrustProcess``.</span></span>
|<span data-ttu-id="af57e-525">Gruppen-ID</span><span class="sxs-lookup"><span data-stu-id="af57e-525">GroupID</span></span> |<span data-ttu-id="af57e-526">Eine Zeichenfolge, die eine Reihe von Parametern identifiziert, die an die ausführbare Datei übergeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="af57e-526">A string that identifies a set of parameters that you want to pass to the executable.</span></span> |
|<span data-ttu-id="af57e-527">Parameter</span><span class="sxs-lookup"><span data-stu-id="af57e-527">Parameters</span></span> |<span data-ttu-id="af57e-528">Parameter, die an die ausführbare Datei übergeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="af57e-528">Parameters that you want to pass to the executable.</span></span> |

#### <a name="example"></a><span data-ttu-id="af57e-529">Beispiel</span><span class="sxs-lookup"><span data-stu-id="af57e-529">Example</span></span>

```XML
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
         xmlns:rescap=
"http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities"
         xmlns:desktop="http://schemas.microsoft.com/appx/manifest/desktop/windows10">
  ...
  <Capabilities>
      <rescap:Capability Name="runFullTrust"/>
  </Capabilities>
  <Applications>
    <Application>
      <Extensions>
          <desktop:Extension Category="windows.fullTrustProcess" Executable="fulltrustprocess.exe">
              <desktop:FullTrustProcess>
                  <desktop:ParameterGroup GroupId="SyncGroup" Parameters="/Sync"/>
                  <desktop:ParameterGroup GroupId="OtherGroup" Parameters="/Other"/>
              </desktop:FullTrustProcess>
           </desktop:Extension>
      </Extensions>
    </Application>
  </Applications>
</Package>
```
<span data-ttu-id="af57e-530">Diese Erweiterung kann hilfreich sein, wenn Sie eine Universelle Windows-Plattform-Benutzeroberfläche erstellen möchten, die auf allen Geräten ausgeführt werden soll. Dabei sollen aber auch die Komponenten der Win32-App weiterhin in voller Vertrauenswürdigkeit ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="af57e-530">This extension might be useful if you want to create a Universal Windows Platform User interface that runs on all devices, but you want components of your Win32 app to continue running in full-trust.</span></span>

<span data-ttu-id="af57e-531">Erstellen Sie einfach ein Desktop-Brücke-Paket für die Win32-App.</span><span class="sxs-lookup"><span data-stu-id="af57e-531">Just create a desktop bridge package for your Win32 app.</span></span> <span data-ttu-id="af57e-532">Fügen Sie dann der Paketdatei Ihrer UWP-App diese Erweiterung hinzu.</span><span class="sxs-lookup"><span data-stu-id="af57e-532">Then, add this extension to the package file of your UWP app.</span></span> <span data-ttu-id="af57e-533">Diese Erweiterungen gibt an, dass Sie eine ausführbare Datei im Desktop-Brücke-Paket starten möchten.</span><span class="sxs-lookup"><span data-stu-id="af57e-533">This extensions indicates that you want to start an executable file in the desktop bridge package.</span></span>  <span data-ttu-id="af57e-534">Wenn Sie zwischen Ihrer UWP-App und Ihrer Win32-App kommunizieren möchten, können Sie einen oder mehrere [App-Dienste](../launch-resume/app-services.md) dafür festlegen.</span><span class="sxs-lookup"><span data-stu-id="af57e-534">If you want to communicate between your UWP app and your Win32 app, you can set up one or more [app services](../launch-resume/app-services.md) to do that.</span></span> <span data-ttu-id="af57e-535">Weitere Informationen zu diesem Szenario finden Sie [hier](https://blogs.msdn.microsoft.com/appconsult/2016/12/19/desktop-bridge-the-migrate-phase-invoking-a-win32-process-from-a-uwp-app/).</span><span class="sxs-lookup"><span data-stu-id="af57e-535">You can read more about this scenario [here](https://blogs.msdn.microsoft.com/appconsult/2016/12/19/desktop-bridge-the-migrate-phase-invoking-a-win32-process-from-a-uwp-app/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="af57e-536">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="af57e-536">Next steps</span></span>

**<span data-ttu-id="af57e-537">Antworten auf bestimmte Fragen finden</span><span class="sxs-lookup"><span data-stu-id="af57e-537">Find answers to specific questions</span></span>**

<span data-ttu-id="af57e-538">Unser Team überwacht diese [StackOverflow-Tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="af57e-538">Our team monitors these [StackOverflow tags](http://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span>

**<span data-ttu-id="af57e-539">Geben Sie Feedback zu diesem Artikel</span><span class="sxs-lookup"><span data-stu-id="af57e-539">Give feedback about this article</span></span>**

<span data-ttu-id="af57e-540">Verwenden Sie den Kommentarabschnitt weiter unten.</span><span class="sxs-lookup"><span data-stu-id="af57e-540">Use the comments section below.</span></span>
