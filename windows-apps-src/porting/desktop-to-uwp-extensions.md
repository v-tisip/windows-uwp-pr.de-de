---
Description: You can use extensions to integrate your packaged desktop app with Windows 10 in predefined ways.
Search.Product: eADQiWindows 10XVcnh
title: Integrieren Ihrer App in Windows10 (Desktop-Brücke)
ms.date: 04/18/2018
ms.topic: article
keywords: windows10, UWP
ms.assetid: 0a8cedac-172a-4efd-8b6b-67fd3667df34
ms.localizationpriority: medium
ms.openlocfilehash: 19ae09190b916fdaae68a67a2b9c11caa20d30e2
ms.sourcegitcommit: c01c29cd97f1cbf050950526e18e15823b6a12a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8713553"
---
# <a name="integrate-your-packaged-desktop-application-with-windows-10"></a><span data-ttu-id="b7e66-103">Integrieren Sie Ihre verpackte desktop-Anwendung mit Windows 10</span><span class="sxs-lookup"><span data-stu-id="b7e66-103">Integrate your packaged desktop application with Windows 10</span></span>

<span data-ttu-id="b7e66-104">Verwenden Sie Erweiterungen, um Ihre verpackte desktop-Anwendung mit Windows 10 auf vordefinierter Weise zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="b7e66-104">Use extensions to integrate your packaged desktop application with Windows 10 in predefined ways.</span></span>

<span data-ttu-id="b7e66-105">Verwenden Sie z. B. eine Erweiterung, um eine Firewallausnahme festzulegen, machen Ihre Anwendung die standardanwendung für einen Dateityp oder verweisen Sie mit startkacheln auf die verpackte Version Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="b7e66-105">For example, use an extension to create a firewall exception, make your application the default application for a file type, or point start tiles to the packaged version of your app.</span></span> <span data-ttu-id="b7e66-106">Um eine Erweiterung zu verwenden, fügen Sie einfach XML-Codes zur Paketmanifestdatei Ihrer App hinzu.</span><span class="sxs-lookup"><span data-stu-id="b7e66-106">To use an extension, just add some XML to your app's package manifest file.</span></span> <span data-ttu-id="b7e66-107">Es ist kein Code erforderlich.</span><span class="sxs-lookup"><span data-stu-id="b7e66-107">No code is required.</span></span>

<span data-ttu-id="b7e66-108">In diesem Thema werden diese Erweiterungen und die Aufgaben beschrieben, die Sie anhand dieser Erweiterungen ausführen können.</span><span class="sxs-lookup"><span data-stu-id="b7e66-108">This topic describes these extensions and the tasks that you can perform by using them.</span></span>

## <a name="transition-users-to-your-app"></a><span data-ttu-id="b7e66-109">Den Übergang Ihrer Benutzer auf Ihre App bereitstellen</span><span class="sxs-lookup"><span data-stu-id="b7e66-109">Transition users to your app</span></span>

<span data-ttu-id="b7e66-110">Helfen Sie Ihren Benutzern, auf Ihre verpackte App umzustellen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-110">Help users transition to your packaged app.</span></span>

* [<span data-ttu-id="b7e66-111">Verweisen Sie mit vorhandenen Startkacheln Taskleistenschaltflächen auf die verpackte App.</span><span class="sxs-lookup"><span data-stu-id="b7e66-111">Point existing Start tiles and taskbar buttons to your packaged app</span></span>](#point)
* [<span data-ttu-id="b7e66-112">Stellen Sie die verpackte Anwendung und nicht Ihre desktop-app Dateien öffnet</span><span class="sxs-lookup"><span data-stu-id="b7e66-112">Make your packaged application open files instead of your desktop app</span></span>](#make)
* [<span data-ttu-id="b7e66-113">Eine Gruppe von Dateitypen ordnen Sie Ihres Anwendungspakets zu</span><span class="sxs-lookup"><span data-stu-id="b7e66-113">Associate your packaged application with a set of file types</span></span>](#associate)
* [<span data-ttu-id="b7e66-114">Fügen Sie den Kontextmenüs der Dateien, die einen bestimmten Dateityp haben, Optionen hinzu.</span><span class="sxs-lookup"><span data-stu-id="b7e66-114">Add options to the context menus of files that have a certain file type</span></span>](#add)
* [<span data-ttu-id="b7e66-115">Öffnen Sie bestimmte Dateitypen direkt anhand einer URL</span><span class="sxs-lookup"><span data-stu-id="b7e66-115">Open certain types of files directly by using a URL</span></span>](#open)

<a id="point" />

### <a name="point-existing-start-tiles-and-taskbar-buttons-to-your-packaged-app"></a><span data-ttu-id="b7e66-116">Verweisen Sie mit vorhandenen Startkacheln Taskleistenschaltflächen auf die verpackte App.</span><span class="sxs-lookup"><span data-stu-id="b7e66-116">Point existing Start tiles and taskbar buttons to your packaged app</span></span>

<span data-ttu-id="b7e66-117">Ihre Benutzer haben möglicherweise Ihre Desktop-Anwendung an die Taskleiste oder das Startmenü angeheftet.</span><span class="sxs-lookup"><span data-stu-id="b7e66-117">Your users might have pinned your desktop application to the taskbar or the Start menu.</span></span> <span data-ttu-id="b7e66-118">Sie mit diesen Verknüpfungen auf Ihre neu verpackte App verweisen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-118">You can point those shortcuts to your new packaged app.</span></span>

#### <a name="xml-namespace"></a><span data-ttu-id="b7e66-119">XML-Namespace</span><span class="sxs-lookup"><span data-stu-id="b7e66-119">XML namespace</span></span>

http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities/3

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="b7e66-120">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b7e66-120">Elements and attributes of this extension</span></span>

```XML
<Extension Category="windows.desktopAppMigration">
    <DesktopAppMigration>
        <DesktopApp AumId="[your_app_aumid]" />
        <DesktopApp ShortcutPath="[path]" />
    </DesktopAppMigration>
</Extension>

```

<span data-ttu-id="b7e66-121">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-rescap3-desktopappmigration).</span><span class="sxs-lookup"><span data-stu-id="b7e66-121">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-rescap3-desktopappmigration).</span></span>

|<span data-ttu-id="b7e66-122">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-122">Name</span></span> | <span data-ttu-id="b7e66-123">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b7e66-123">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="b7e66-124">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b7e66-124">Category</span></span> |<span data-ttu-id="b7e66-125">Immer ``windows.desktopAppMigration``.</span><span class="sxs-lookup"><span data-stu-id="b7e66-125">Always ``windows.desktopAppMigration``.</span></span>
|<span data-ttu-id="b7e66-126">AumID</span><span class="sxs-lookup"><span data-stu-id="b7e66-126">AumID</span></span> |<span data-ttu-id="b7e66-127">Die Anwendungsbenutzermodell-ID der verpackten App.</span><span class="sxs-lookup"><span data-stu-id="b7e66-127">The Application User Model ID of your packaged app.</span></span> |
|<span data-ttu-id="b7e66-128">Verknüpfungspfad</span><span class="sxs-lookup"><span data-stu-id="b7e66-128">ShortcutPath</span></span> |<span data-ttu-id="b7e66-129">Der Pfad zu den Ink-Dateien, die die Desktop-Version Ihrer App starten.</span><span class="sxs-lookup"><span data-stu-id="b7e66-129">The path to .lnk files that start the desktop version of your app.</span></span> |

#### <a name="example"></a><span data-ttu-id="b7e66-130">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b7e66-130">Example</span></span>

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

#### <a name="related-sample"></a><span data-ttu-id="b7e66-131">Verwandte Beispiele</span><span class="sxs-lookup"><span data-stu-id="b7e66-131">Related sample</span></span>

[<span data-ttu-id="b7e66-132">WPF-Bildanzeige mit Übergang/Migration/Deinstallation</span><span class="sxs-lookup"><span data-stu-id="b7e66-132">WPF picture viewer with transition/migration/uninstallation</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/DesktopAppTransition)

<a id="make" />

### <a name="make-your-packaged-application-open-files-instead-of-your-desktop-app"></a><span data-ttu-id="b7e66-133">Stellen Sie die verpackte Anwendung und nicht Ihre desktop-app Dateien öffnet</span><span class="sxs-lookup"><span data-stu-id="b7e66-133">Make your packaged application open files instead of your desktop app</span></span>

<span data-ttu-id="b7e66-134">Sie können überprüfen, dass Benutzer Ihre neue verpackte Anwendung in der Standardeinstellung für bestimmte Arten von Dateien, statt die desktop-Version Ihrer App öffnen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-134">You can make sure that users open your new packaged application by default for specific types of files instead of opening the desktop version of your app.</span></span>

<span data-ttu-id="b7e66-135">Dazu müssen Sie den [programmgesteuerten Bezeichner (Programm-ID)](https://msdn.microsoft.com/library/windows/desktop/cc144152.aspx) jeder Anwendung angeben, aus der Sie Dateizuordnungen übernehmen möchten.</span><span class="sxs-lookup"><span data-stu-id="b7e66-135">To do that, you'll specify the [programmatic identifier (ProgID)](https://msdn.microsoft.com/library/windows/desktop/cc144152.aspx) of each application from which you want to inherit file associations.</span></span>

#### <a name="xml-namespaces"></a><span data-ttu-id="b7e66-136">XML-Namespaces</span><span class="sxs-lookup"><span data-stu-id="b7e66-136">XML namespaces</span></span>

* http://schemas.microsoft.com/appx/manifest/uap/windows10/3
* http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities/3

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="b7e66-137">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b7e66-137">Elements and attributes of this extension</span></span>

```XML
<Extension Category="windows.fileTypeAssociation">
<FileTypeAssociation Name="[AppID]">
         <MigrationProgIds>
            <MigrationProgId>"[ProgID]"</MigrationProgId>
        </MigrationProgIds>
    </FileTypeAssociation>
</Extension>
```

<span data-ttu-id="b7e66-138">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span><span class="sxs-lookup"><span data-stu-id="b7e66-138">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span></span>

|<span data-ttu-id="b7e66-139">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-139">Name</span></span> |<span data-ttu-id="b7e66-140">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b7e66-140">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="b7e66-141">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b7e66-141">Category</span></span> |<span data-ttu-id="b7e66-142">Immer ``windows.fileTypeAssociation``.</span><span class="sxs-lookup"><span data-stu-id="b7e66-142">Always ``windows.fileTypeAssociation``.</span></span>
|<span data-ttu-id="b7e66-143">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-143">Name</span></span> |<span data-ttu-id="b7e66-144">Eine eindeutige ID für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="b7e66-144">A unique Id for your app.</span></span> <span data-ttu-id="b7e66-145">Diese ID wird intern verwendet, um einen [programmgesteuerte Bezeichner (Programm-ID)](https://msdn.microsoft.com/library/windows/desktop/cc144152.aspx) mit Hash zu generieren, die mit Ihrer Dateitypzuordnung verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="b7e66-145">This Id is used internally to generate a hashed [programmatic identifier (ProgID)](https://msdn.microsoft.com/library/windows/desktop/cc144152.aspx) associated with your file type association.</span></span> <span data-ttu-id="b7e66-146">Mithilfe dieser ID können Sie Änderungen in zukünftigen Versionen Ihrer App verwalten.</span><span class="sxs-lookup"><span data-stu-id="b7e66-146">You can use this Id to manage changes in future versions of your app.</span></span> |
|<span data-ttu-id="b7e66-147">MigrationProgId</span><span class="sxs-lookup"><span data-stu-id="b7e66-147">MigrationProgId</span></span> |<span data-ttu-id="b7e66-148">Der [programmgesteuerte Bezeichner (Programm-ID)](https://msdn.microsoft.com/library/windows/desktop/cc144152.aspx) wird beschrieben, die die Anwendung, die Komponente und die Version der Desktopanwendung, aus der Sie dateizuordnungen übernehmen möchten.</span><span class="sxs-lookup"><span data-stu-id="b7e66-148">The [programmatic identifier (ProgID)](https://msdn.microsoft.com/library/windows/desktop/cc144152.aspx) that describes the application, component, and version of the desktop application from which you want to inherit file associations.</span></span>|

#### <a name="example"></a><span data-ttu-id="b7e66-149">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b7e66-149">Example</span></span>

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

#### <a name="related-sample"></a><span data-ttu-id="b7e66-150">Verwandte Beispiele</span><span class="sxs-lookup"><span data-stu-id="b7e66-150">Related sample</span></span>

[<span data-ttu-id="b7e66-151">WPF-Bildanzeige mit Übergang/Migration/Deinstallation</span><span class="sxs-lookup"><span data-stu-id="b7e66-151">WPF picture viewer with transition/migration/uninstallation</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/DesktopAppTransition)

<a id="associate" />

### <a name="associate-your-packaged-application-with-a-set-of-file-types"></a><span data-ttu-id="b7e66-152">Eine Gruppe von Dateitypen ordnen Sie Ihres Anwendungspakets zu</span><span class="sxs-lookup"><span data-stu-id="b7e66-152">Associate your packaged application with a set of file types</span></span>

<span data-ttu-id="b7e66-153">Sie können die verpackte Anwendung mit dateityperweiterungen zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="b7e66-153">You can associated your packaged application with file type extensions.</span></span> <span data-ttu-id="b7e66-154">Wenn ein Benutzer eine Datei klickt und die Option " **Öffnen mit** " auswählt, wird die Anwendung in der Liste der Vorschläge angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b7e66-154">If a user right-clicks a file and then selects the **Open with** option, your application appears in the list of suggestions.</span></span>

#### <a name="xml-namespace"></a><span data-ttu-id="b7e66-155">XML-Namespace</span><span class="sxs-lookup"><span data-stu-id="b7e66-155">XML namespace</span></span>

* http://schemas.microsoft.com/appx/manifest/uap/windows10
* http://schemas.microsoft.com/appx/manifest/uap/windows10/3

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="b7e66-156">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b7e66-156">Elements and attributes of this extension</span></span>

```XML
<Extension Category="windows.fileTypeAssociation">
    <FileTypeAssociation Name="[AppID]">
        <SupportedFileTypes>
            <FileType>"[file extension]"</FileType>
        </SupportedFileTypes>
    </FileTypeAssociation>
</Extension>
```

<span data-ttu-id="b7e66-157">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span><span class="sxs-lookup"><span data-stu-id="b7e66-157">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span></span>

|<span data-ttu-id="b7e66-158">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-158">Name</span></span> |<span data-ttu-id="b7e66-159">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b7e66-159">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="b7e66-160">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b7e66-160">Category</span></span> |<span data-ttu-id="b7e66-161">Immer ``windows.fileTypeAssociation``.</span><span class="sxs-lookup"><span data-stu-id="b7e66-161">Always ``windows.fileTypeAssociation``.</span></span>
|<span data-ttu-id="b7e66-162">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-162">Name</span></span> |<span data-ttu-id="b7e66-163">Eine eindeutige ID für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="b7e66-163">A unique Id for your app.</span></span> <span data-ttu-id="b7e66-164">Diese ID wird intern verwendet, um einen [programmgesteuerte Bezeichner (Programm-ID)](https://msdn.microsoft.com/library/windows/desktop/cc144152.aspx) mit Hash zu generieren, die mit Ihrer Dateitypzuordnung verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="b7e66-164">This Id is used internally to generate a hashed [programmatic identifier (ProgID)](https://msdn.microsoft.com/library/windows/desktop/cc144152.aspx) associated with your file type association.</span></span> <span data-ttu-id="b7e66-165">Mithilfe dieser ID können Sie Änderungen in zukünftigen Versionen Ihrer App verwalten.</span><span class="sxs-lookup"><span data-stu-id="b7e66-165">You can use this Id to manage changes in future versions of your app.</span></span>   |
|<span data-ttu-id="b7e66-166">FileType</span><span class="sxs-lookup"><span data-stu-id="b7e66-166">FileType</span></span> |<span data-ttu-id="b7e66-167">Die Erweiterung, die von Ihrer App unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="b7e66-167">The file extension supported by your app.</span></span> |

#### <a name="example"></a><span data-ttu-id="b7e66-168">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b7e66-168">Example</span></span>

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

#### <a name="related-sample"></a><span data-ttu-id="b7e66-169">Verwandte Beispiele</span><span class="sxs-lookup"><span data-stu-id="b7e66-169">Related sample</span></span>

[<span data-ttu-id="b7e66-170">WPF-Bildanzeige mit Übergang/Migration/Deinstallation</span><span class="sxs-lookup"><span data-stu-id="b7e66-170">WPF picture viewer with transition/migration/uninstallation</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/DesktopAppTransition)

<a id="add" />

### <a name="add-options-to-the-context-menus-of-files-that-have-a-certain-file-type"></a><span data-ttu-id="b7e66-171">Fügen Sie den Kontextmenüs der Dateien, die einen bestimmten Dateityp haben, Optionen hinzu.</span><span class="sxs-lookup"><span data-stu-id="b7e66-171">Add options to the context menus of files that have a certain file type</span></span>

<span data-ttu-id="b7e66-172">In den meisten Fällen klicken Benutzer doppelt auf Dateien, um sie zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-172">In most cases, users double-click files to open them.</span></span> <span data-ttu-id="b7e66-173">Wenn Benutzer mit der rechten Maustaste auf eine Datei klicken, werden verschiedene Optionen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b7e66-173">If users, right click a file, various options appear.</span></span>

<span data-ttu-id="b7e66-174">Sie können diesem Menü Optionen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-174">You can add options to that menu.</span></span> <span data-ttu-id="b7e66-175">Diese Optionen geben Benutzern weitere Möglichkeiten zur Interaktion mit der Datei, wie etwa Drucken, Bearbeiten oder das Anzeigen einer Vorschau.</span><span class="sxs-lookup"><span data-stu-id="b7e66-175">These options give users other ways to interact with your file such as print, edit, or preview the file.</span></span>

#### <a name="xml-namespaces"></a><span data-ttu-id="b7e66-176">XML-Namespaces</span><span class="sxs-lookup"><span data-stu-id="b7e66-176">XML namespaces</span></span>

* http://schemas.microsoft.com/appx/manifest/uap/windows10
* http://schemas.microsoft.com/appx/manifest/uap/windows10/2
* http://schemas.microsoft.com/appx/manifest/uap/windows10/3

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="b7e66-177">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b7e66-177">Elements and attributes of this extension</span></span>

```XML
<Extension Category="windows.fileTypeAssociation">
    <FileTypeAssociation Name="[AppID]">
        <SupportedVerbs>
           <Verb Id="[ID]" Extended="[Extended]" Parameters="[parameters]">"[verb label]"</Verb>
        </SupportedVerbs>
    </FileTypeAssociation>
</Extension>
```

<span data-ttu-id="b7e66-178">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span><span class="sxs-lookup"><span data-stu-id="b7e66-178">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span></span>

|<span data-ttu-id="b7e66-179">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-179">Name</span></span> |<span data-ttu-id="b7e66-180">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b7e66-180">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="b7e66-181">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b7e66-181">Category</span></span> | <span data-ttu-id="b7e66-182">Immer ``windows.fileTypeAssociation``.</span><span class="sxs-lookup"><span data-stu-id="b7e66-182">Always ``windows.fileTypeAssociation``.</span></span>
|<span data-ttu-id="b7e66-183">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-183">Name</span></span> |<span data-ttu-id="b7e66-184">Eine eindeutige ID für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="b7e66-184">A unique Id for your app.</span></span> |
|<span data-ttu-id="b7e66-185">Verb</span><span class="sxs-lookup"><span data-stu-id="b7e66-185">Verb</span></span> |<span data-ttu-id="b7e66-186">Der Name, der im Kontextmenü des Datei-Explorers angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b7e66-186">The name that appears in the File Explorer context menu.</span></span> <span data-ttu-id="b7e66-187">Diese Zeichenfolge kann mithilfe von ```ms-resource``` lokalisiert werden.</span><span class="sxs-lookup"><span data-stu-id="b7e66-187">This string is localizable that uses ```ms-resource```.</span></span>|
|<span data-ttu-id="b7e66-188">ID</span><span class="sxs-lookup"><span data-stu-id="b7e66-188">Id</span></span> |<span data-ttu-id="b7e66-189">Die eindeutige ID des Verbs.</span><span class="sxs-lookup"><span data-stu-id="b7e66-189">The unique Id of the verb.</span></span> <span data-ttu-id="b7e66-190">Wenn Ihre Anwendung eine UWP-app ist, wird übergeben, um Ihre app im Rahmen der aktivierungsereignisargumente Sie auch die Auswahl des Benutzers entsprechend verarbeiten kann.</span><span class="sxs-lookup"><span data-stu-id="b7e66-190">If your application is a UWP app, this is passed to your app as part of its activation event args so it can handle the user’s selection appropriately.</span></span> <span data-ttu-id="b7e66-191">Wenn Ihre Anwendung eine vertrauenswürdig verpackte app ist, empfängt er Parameter stattdessen (siehe nächsten Aufzählungspunkt).</span><span class="sxs-lookup"><span data-stu-id="b7e66-191">If your application is a full-trust packaged app, it receives parameters instead (see the next bullet).</span></span> |
|<span data-ttu-id="b7e66-192">Parameter</span><span class="sxs-lookup"><span data-stu-id="b7e66-192">Parameters</span></span> |<span data-ttu-id="b7e66-193">Die Liste mit Argumentparametern und -werten für das Verb.</span><span class="sxs-lookup"><span data-stu-id="b7e66-193">The list of argument parameters and values associated with the verb.</span></span> <span data-ttu-id="b7e66-194">Wenn Ihre Anwendung eine vertrauenswürdig verpackte app ist, werden diese Parameter an die Anwendung als Ereignisargumente übergeben, wenn die Anwendung aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="b7e66-194">If your application is a full-trust packaged app, these parameters are passed to the application as event args when the application is activated.</span></span> <span data-ttu-id="b7e66-195">Sie können das Verhalten von Ihrer Anwendung auf Grundlage anderer aktivierungsverben anpassen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-195">You can customize the behavior of your application based on different activation verbs.</span></span> <span data-ttu-id="b7e66-196">Wenn eine Variable einen Dateipfad enthalten kann, schließen Sie den Parameterwert in Anführungszeichen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-196">If a variable can contain a file path, wrap the parameter value in quotes.</span></span> <span data-ttu-id="b7e66-197">Dadurch werden jegliche Probleme vermieden, die in Fällen auftreten, bei denen der Pfad Leerzeichen enthält.</span><span class="sxs-lookup"><span data-stu-id="b7e66-197">That will avoid any issues that happen in cases where the path includes spaces.</span></span> <span data-ttu-id="b7e66-198">Wenn Ihre Anwendung eine UWP-app ist, können Sie keine Parameter übergeben.</span><span class="sxs-lookup"><span data-stu-id="b7e66-198">If your application is a UWP app, you can’t pass parameters.</span></span> <span data-ttu-id="b7e66-199">Die App empfängt stattdessen die ID (siehe das vorherige Aufzählungszeichen).</span><span class="sxs-lookup"><span data-stu-id="b7e66-199">The app receives the Id instead (see the previous bullet).</span></span>|
|<span data-ttu-id="b7e66-200">Erweitert</span><span class="sxs-lookup"><span data-stu-id="b7e66-200">Extended</span></span> |<span data-ttu-id="b7e66-201">Gibt an, dass das Verb nur angezeigt werden soll, wenn der Benutzer zum Anzeigen des Kontextmenüs **UMSCHALT** gedrückt hält, bevor er mit der rechten Maustaste auf die Datei klickt.</span><span class="sxs-lookup"><span data-stu-id="b7e66-201">Specifies that the verb appears only if the user shows the context menu by holding the **Shift** key before right-clicking the file.</span></span> <span data-ttu-id="b7e66-202">Dieses Attribut ist optional und standardmäßig auf den Wert von **False** (Verb soll immer angezeigt werden) festgelegt.</span><span class="sxs-lookup"><span data-stu-id="b7e66-202">This attribute is optional and defaults to a value of **False** (e.g., always show the verb) if not listed.</span></span> <span data-ttu-id="b7e66-203">Dieses Verhalten muss für jedes Verb einzeln angegeben werden – mit Ausnahme von „Öffnen“: Bei diesem Verb ist der Wert immer **False**.</span><span class="sxs-lookup"><span data-stu-id="b7e66-203">You specify this behavior individually for each verb (except for "Open," which is always **False**).</span></span>|

#### <a name="example"></a><span data-ttu-id="b7e66-204">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b7e66-204">Example</span></span>

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

#### <a name="related-sample"></a><span data-ttu-id="b7e66-205">Verwandte Beispiele</span><span class="sxs-lookup"><span data-stu-id="b7e66-205">Related sample</span></span>

[<span data-ttu-id="b7e66-206">WPF-Bildanzeige mit Übergang/Migration/Deinstallation</span><span class="sxs-lookup"><span data-stu-id="b7e66-206">WPF picture viewer with transition/migration/uninstallation</span></span>](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/DesktopAppTransition)

<a id="open" />

### <a name="open-certain-types-of-files-directly-by-using-a-url"></a><span data-ttu-id="b7e66-207">Öffnen Sie bestimmte Dateitypen direkt anhand einer URL</span><span class="sxs-lookup"><span data-stu-id="b7e66-207">Open certain types of files directly by using a URL</span></span>

<span data-ttu-id="b7e66-208">Sie können überprüfen, dass Benutzer Ihre neue verpackte Anwendung in der Standardeinstellung für bestimmte Arten von Dateien, statt die desktop-Version Ihrer App öffnen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-208">You can make sure that users open your new packaged application by default for specific types of files instead of opening the desktop version of your app.</span></span>

#### <a name="xml-namespaces"></a><span data-ttu-id="b7e66-209">XML-Namespaces</span><span class="sxs-lookup"><span data-stu-id="b7e66-209">XML namespaces</span></span>

* http://schemas.microsoft.com/appx/manifest/uap/windows10
* <span data-ttu-id="b7e66-210">http://schemas.microsoft.com/appx/manifest/uap/windows10/3"</span><span class="sxs-lookup"><span data-stu-id="b7e66-210">http://schemas.microsoft.com/appx/manifest/uap/windows10/3"</span></span>

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="b7e66-211">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b7e66-211">Elements and attributes of this extension</span></span>

```XML
<Extension Category="windows.fileTypeAssociation">
    <FileTypeAssociation Name="[AppID]" UseUrl="true" Parameters="%1">
        <SupportedFileTypes>
            <FileType>"[FileExtension]"</FileType>
        </SupportedFileTypes>
    </FileTypeAssociation>
</Extension>
```

<span data-ttu-id="b7e66-212">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span><span class="sxs-lookup"><span data-stu-id="b7e66-212">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span></span>

|<span data-ttu-id="b7e66-213">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-213">Name</span></span> |<span data-ttu-id="b7e66-214">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b7e66-214">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="b7e66-215">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b7e66-215">Category</span></span> |<span data-ttu-id="b7e66-216">Immer ``windows.fileTypeAssociation``.</span><span class="sxs-lookup"><span data-stu-id="b7e66-216">Always ``windows.fileTypeAssociation``.</span></span>
|<span data-ttu-id="b7e66-217">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-217">Name</span></span> |<span data-ttu-id="b7e66-218">Eine eindeutige ID für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="b7e66-218">A unique Id for your app.</span></span> |
|<span data-ttu-id="b7e66-219">UseUrl</span><span class="sxs-lookup"><span data-stu-id="b7e66-219">UseUrl</span></span> |<span data-ttu-id="b7e66-220">Gibt an, ob Dateien direkt über eine URL-Ziel geöffnet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-220">Indicates whether to open files directly from a URL target.</span></span> <span data-ttu-id="b7e66-221">Wenn Sie diesen Wert nicht festlegen, versucht Ihre Anwendung zum Öffnen einer Datei durch einer URL zu das System zum ersten Download die Datei lokal.</span><span class="sxs-lookup"><span data-stu-id="b7e66-221">If you do not set this value, attempts by your application to open a file by using a URL cause the system to first download the file locally.</span></span> |
|<span data-ttu-id="b7e66-222">Parameter</span><span class="sxs-lookup"><span data-stu-id="b7e66-222">Parameters</span></span> |<span data-ttu-id="b7e66-223">Optionale Parameter.</span><span class="sxs-lookup"><span data-stu-id="b7e66-223">optional parameters.</span></span> |
|<span data-ttu-id="b7e66-224">FileType</span><span class="sxs-lookup"><span data-stu-id="b7e66-224">FileType</span></span> |<span data-ttu-id="b7e66-225">Die relevanten Dateierweiterungen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-225">The relevant file extensions.</span></span> |

#### <a name="example"></a><span data-ttu-id="b7e66-226">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b7e66-226">Example</span></span>

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

## <a name="perform-setup-tasks"></a><span data-ttu-id="b7e66-227">Setup-Aufgaben ausführen</span><span class="sxs-lookup"><span data-stu-id="b7e66-227">Perform setup tasks</span></span>

* [<span data-ttu-id="b7e66-228">Erstellen von Firewallausnahmen für Ihre App</span><span class="sxs-lookup"><span data-stu-id="b7e66-228">Create firewall exception for your app</span></span>](#rules)
* [<span data-ttu-id="b7e66-229">Speichern Sie die DLL-Dateien in einem beliebigen Ordner des Pakets</span><span class="sxs-lookup"><span data-stu-id="b7e66-229">Place your DLL files into any folder of the package</span></span>](#load-paths)

<a id="rules" />

### <a name="create-firewall-exception-for-your-app"></a><span data-ttu-id="b7e66-230">Erstellen von Firewallausnahmen für Ihre App</span><span class="sxs-lookup"><span data-stu-id="b7e66-230">Create firewall exception for your app</span></span>

<span data-ttu-id="b7e66-231">Wenn Ihre Anwendung Kommunikation über einen Anschluss erforderlich ist, können Sie Ihre Anwendung zur Liste der Firewallausnahmen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-231">If your application requires communication through a port, you can add your application to the list of firewall exceptions.</span></span>

#### <a name="xml-namespace"></a><span data-ttu-id="b7e66-232">XML-Namespace</span><span class="sxs-lookup"><span data-stu-id="b7e66-232">XML namespace</span></span>

http://schemas.microsoft.com/appx/manifest/desktop/windows10/2

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="b7e66-233">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b7e66-233">Elements and attributes of this extension</span></span>

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

<span data-ttu-id="b7e66-234">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-desktop2-firewallrules).</span><span class="sxs-lookup"><span data-stu-id="b7e66-234">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-desktop2-firewallrules).</span></span>

|<span data-ttu-id="b7e66-235">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-235">Name</span></span> |<span data-ttu-id="b7e66-236">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b7e66-236">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="b7e66-237">Category</span><span class="sxs-lookup"><span data-stu-id="b7e66-237">Category</span></span> |<span data-ttu-id="b7e66-238">Immer</span><span class="sxs-lookup"><span data-stu-id="b7e66-238">Always</span></span> ``windows.firewallRules``|
|<span data-ttu-id="b7e66-239">Ausführbare Datei</span><span class="sxs-lookup"><span data-stu-id="b7e66-239">Executable</span></span> |<span data-ttu-id="b7e66-240">Der Name der ausführbaren Datei, die Sie der Liste der Firewallausnahmen hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="b7e66-240">The name of the executable file that you want to add to the list of firewall exceptions</span></span> |
|<span data-ttu-id="b7e66-241">Richtung</span><span class="sxs-lookup"><span data-stu-id="b7e66-241">Direction</span></span> |<span data-ttu-id="b7e66-242">Gibt an, ob die Regel eine ein- oder ausgehende Regel ist.</span><span class="sxs-lookup"><span data-stu-id="b7e66-242">Indicates whether the rule is an inbound or outbound rule</span></span> |
|<span data-ttu-id="b7e66-243">IPProtocol</span><span class="sxs-lookup"><span data-stu-id="b7e66-243">IPProtocol</span></span> |<span data-ttu-id="b7e66-244">Das Kommunikationsprotokoll</span><span class="sxs-lookup"><span data-stu-id="b7e66-244">The communication protocol</span></span> |
|<span data-ttu-id="b7e66-245">LocalPortMin</span><span class="sxs-lookup"><span data-stu-id="b7e66-245">LocalPortMin</span></span> |<span data-ttu-id="b7e66-246">Die untere Portnummer in einer Auswahl von lokalen Portnummern.</span><span class="sxs-lookup"><span data-stu-id="b7e66-246">The lower port number in a range of local port numbers.</span></span> |
|<span data-ttu-id="b7e66-247">LocalPortMax</span><span class="sxs-lookup"><span data-stu-id="b7e66-247">LocalPortMax</span></span> |<span data-ttu-id="b7e66-248">Die höchste Portnummer in einer Auswahl von lokalen Portnummern.</span><span class="sxs-lookup"><span data-stu-id="b7e66-248">The highest port number of a range of local port numbers.</span></span> |
|<span data-ttu-id="b7e66-249">RemotePortMax</span><span class="sxs-lookup"><span data-stu-id="b7e66-249">RemotePortMax</span></span> |<span data-ttu-id="b7e66-250">Die niedrigere Portnummer in einer Auswahl von Remoteportnummern.</span><span class="sxs-lookup"><span data-stu-id="b7e66-250">The lower port number in a range of remote port numbers.</span></span> |
|<span data-ttu-id="b7e66-251">RemotePortMax</span><span class="sxs-lookup"><span data-stu-id="b7e66-251">RemotePortMax</span></span> |<span data-ttu-id="b7e66-252">Die höchste Portnummer in einer Auswahl Remoteportnummern.</span><span class="sxs-lookup"><span data-stu-id="b7e66-252">The highest port number of a range of remote port numbers.</span></span> |
|<span data-ttu-id="b7e66-253">Profil</span><span class="sxs-lookup"><span data-stu-id="b7e66-253">Profile</span></span> |<span data-ttu-id="b7e66-254">Der Netzwerktyp</span><span class="sxs-lookup"><span data-stu-id="b7e66-254">The network type</span></span> |

#### <a name="example"></a><span data-ttu-id="b7e66-255">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b7e66-255">Example</span></span>

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

<a id="load-paths" />

### <a name="place-your-dll-files-into-any-folder-of-the-package"></a><span data-ttu-id="b7e66-256">Speichern Sie die DLL-Dateien in einem beliebigen Ordner des Pakets</span><span class="sxs-lookup"><span data-stu-id="b7e66-256">Place your DLL files into any folder of the package</span></span>

<span data-ttu-id="b7e66-257">Verwenden Sie eine Erweiterung, um diese Ordner zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="b7e66-257">Use an extension to identify those folders.</span></span> <span data-ttu-id="b7e66-258">Auf diese Weise kann das System die Dateien finden und laden, die Sie darin abgelegt haben.</span><span class="sxs-lookup"><span data-stu-id="b7e66-258">That way, the system can find and load the files that you place in them.</span></span> <span data-ttu-id="b7e66-259">Stellen Sie sich diese Erweiterung als Ersatz für die Umgebungsvariable _%PATH%_ vor.</span><span class="sxs-lookup"><span data-stu-id="b7e66-259">Think of this extension as a replacement of the _%PATH%_ environment variable.</span></span>

<span data-ttu-id="b7e66-260">Wenn Sie diese Erweiterung nicht verwenden, durchsucht das System das Paketabhängigkeitsdiagramm des Prozesses, den Paketstammordner und anschließend das Systemverzeichnis (_%SystemRoot%\system32_) in dieser Reihenfolge.</span><span class="sxs-lookup"><span data-stu-id="b7e66-260">If you don't use this extension, the system searches the package dependency graph of the process, the package root folder, and then the system directory (_%SystemRoot%\system32_) in that order.</span></span> <span data-ttu-id="b7e66-261">Weitere Informationen hierzu finden Sie unter [Suchreihenfolge von Windows-Apps](https://msdn.microsoft.com/library/windows/desktop/ms682586.aspx#_search_order_for_windows_store_apps).</span><span class="sxs-lookup"><span data-stu-id="b7e66-261">To learn more, see [Search order of Windows apps](https://msdn.microsoft.com/library/windows/desktop/ms682586.aspx#_search_order_for_windows_store_apps).</span></span>

<span data-ttu-id="b7e66-262">Jedes Paket kann nur eine dieser Erweiterungen enthalten.</span><span class="sxs-lookup"><span data-stu-id="b7e66-262">Each package can contain only one of these extensions.</span></span> <span data-ttu-id="b7e66-263">Das bedeutet, Sie können Ihrem Hauptpaket, und dann jedem Ihrer [optionalen Pakete und zugehörigen Sets](https://docs.microsoft.com/windows/uwp/packaging/optional-packages) eine hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-263">That means that you can add one of them to your main package, and then add one to each of your [optional packages, and related sets](https://docs.microsoft.com/windows/uwp/packaging/optional-packages).</span></span>

#### <a name="xml-namespace"></a><span data-ttu-id="b7e66-264">XML-Namespace</span><span class="sxs-lookup"><span data-stu-id="b7e66-264">XML namespace</span></span>

http://schemas.microsoft.com/appx/manifest/uap/windows10/6

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="b7e66-265">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b7e66-265">Elements and attributes of this extension</span></span>

<span data-ttu-id="b7e66-266">Deklarieren Sie diese Erweiterung auf der Paketebene des App-Manifests.</span><span class="sxs-lookup"><span data-stu-id="b7e66-266">Declare this extension at the package-level of your app manifest.</span></span>

```XML
<Extension Category="windows.loaderSearchPathOverride">
  <LoaderSearchPathOverride>
    <LoaderSearchPathEntry FolderPath="[path]"/>
  </LoaderSearchPathOverride>
</Extension>

```

|<span data-ttu-id="b7e66-267">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-267">Name</span></span> | <span data-ttu-id="b7e66-268">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b7e66-268">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="b7e66-269">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b7e66-269">Category</span></span> |<span data-ttu-id="b7e66-270">Immer ``windows.loaderSearchPathOverride``.</span><span class="sxs-lookup"><span data-stu-id="b7e66-270">Always ``windows.loaderSearchPathOverride``.</span></span>
|<span data-ttu-id="b7e66-271">FolderPath</span><span class="sxs-lookup"><span data-stu-id="b7e66-271">FolderPath</span></span> | <span data-ttu-id="b7e66-272">Der Pfad des Ordners, der die DLL-Dateien enthält.</span><span class="sxs-lookup"><span data-stu-id="b7e66-272">The path of the folder that contains your dll files.</span></span> <span data-ttu-id="b7e66-273">Geben Sie einen Pfad relativ zum Stammordner des Pakets an.</span><span class="sxs-lookup"><span data-stu-id="b7e66-273">Specify a path that is relative to the root folder of the package.</span></span> <span data-ttu-id="b7e66-274">Sie können bis zu fünf Pfade in einer Erweiterung angeben.</span><span class="sxs-lookup"><span data-stu-id="b7e66-274">You can specify up to five paths in one extension.</span></span> <span data-ttu-id="b7e66-275">Wenn das System nach Dateien im Stammordner des Pakets suchen soll, verwenden Sie eine leere Zeichenfolge für einen dieser Pfade.</span><span class="sxs-lookup"><span data-stu-id="b7e66-275">If you want the system to search for files in the root folder of the package, use an empty string for one of these paths.</span></span> <span data-ttu-id="b7e66-276">Fügen Sie keine doppelten Pfade ein und stellen Sie sicher, dass die Pfade keine voran- bzw. nachgestellten Schrägstriche oder umgekehrten Schrägstriche enthalten.</span><span class="sxs-lookup"><span data-stu-id="b7e66-276">Don't included duplicate paths and make sure that your paths don't contain leading and trailing slashes or backslashes.</span></span> <br><br> <span data-ttu-id="b7e66-277">Das System durchsucht keine Unterordner. Stellen Sie daher sicher, dass Sie jeden Ordner mit DLL-Dateien, die das System laden soll, explizit auflisten.</span><span class="sxs-lookup"><span data-stu-id="b7e66-277">The system won't search subfolders, so make sure to explicitly list each folder that contains DLL files that you want the system to load.</span></span>|

#### <a name="example"></a><span data-ttu-id="b7e66-278">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b7e66-278">Example</span></span>

```XML
<Package
  xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
  IgnorableNamespaces="uap6">
  ...
    <Extensions>
      <uap6:Extension Category="windows.loaderSearchPathOverride">
        <uap6:LoaderSearchPathOverride>
          <uap6:LoaderSearchPathEntry FolderPath=""/>
          <uap6:LoaderSearchPathEntry FolderPath="folder1/subfolder1"/>
          <uap6:LoaderSearchPathEntry FolderPath="folder2/subfolder2"/>
        </uap6:LoaderSearchPathOverride>
      </uap6:Extension>
    </Extensions>
...
</Package>
```

## <a name="integrate-with-file-explorer"></a><span data-ttu-id="b7e66-279">Integration mit dem Datei-Explorer</span><span class="sxs-lookup"><span data-stu-id="b7e66-279">Integrate with File Explorer</span></span>

<span data-ttu-id="b7e66-280">Helfen Sie Benutzern beim Organisieren von Dateien und interagieren Sie mit Ihnen auf vertrauter Weise.</span><span class="sxs-lookup"><span data-stu-id="b7e66-280">Help users organize your files and interact with them in familiar ways.</span></span>

* [<span data-ttu-id="b7e66-281">Definieren Sie, wie die Anwendung verhält, wenn Benutzer auswählen und öffnen mehrere Dateien gleichzeitig</span><span class="sxs-lookup"><span data-stu-id="b7e66-281">Define how your application behaves when users select and open multiple files at the same time</span></span>](#define)
* [<span data-ttu-id="b7e66-282">Zeigen Sie Dateiinhalte in einem Miniaturbild im Datei-Explorer an.</span><span class="sxs-lookup"><span data-stu-id="b7e66-282">Show file contents in a thumbnail image within File Explorer</span></span>](#show)
* [<span data-ttu-id="b7e66-283">Zeigen Sie Dateiinhalte in einer Vorschau des Datei-Explorers an.</span><span class="sxs-lookup"><span data-stu-id="b7e66-283">Show file contents in a Preview pane of File Explorer</span></span>](#preview)
* [<span data-ttu-id="b7e66-284">Ermöglichen Sie es Benutzern, Dateien mithilfe der Spalte „Art” im Datei-Explorer zu gruppieren.</span><span class="sxs-lookup"><span data-stu-id="b7e66-284">Enable users to group files by using the Kind column in File Explorer</span></span>](#enable)
* [<span data-ttu-id="b7e66-285">Stellen Sie den Bereichen Suchen, Index, Eigenschaftendialogfelder und Details Dateieigenschaften zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="b7e66-285">Make file properties available to search, index, property dialogs, and the details pane</span></span>](#make-file-properties)
* [<span data-ttu-id="b7e66-286">Zeigen Sie Dateien von Ihrem Clouddienst im Datei-Explorer an</span><span class="sxs-lookup"><span data-stu-id="b7e66-286">Make files from your cloud service appear in File Explorer</span></span>](#cloud-files)

<a id="define" />

### <a name="define-how-your-application-behaves-when-users-select-and-open-multiple-files-at-the-same-time"></a><span data-ttu-id="b7e66-287">Definieren Sie, wie die Anwendung verhält, wenn Benutzer auswählen und öffnen mehrere Dateien gleichzeitig</span><span class="sxs-lookup"><span data-stu-id="b7e66-287">Define how your application behaves when users select and open multiple files at the same time</span></span>

<span data-ttu-id="b7e66-288">Geben Sie an, wie die Anwendung verhält, wenn ein Benutzer mehrere Dateien gleichzeitig öffnet.</span><span class="sxs-lookup"><span data-stu-id="b7e66-288">Specify how your application behaves when a user opens multiple files simultaneously.</span></span>

#### <a name="xml-namespaces"></a><span data-ttu-id="b7e66-289">XML-Namespaces</span><span class="sxs-lookup"><span data-stu-id="b7e66-289">XML namespaces</span></span>

* http://schemas.microsoft.com/appx/manifest/uap/windows10
* http://schemas.microsoft.com/appx/manifest/uap/windows10/2
* http://schemas.microsoft.com/appx/manifest/uap/windows10/3

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="b7e66-290">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b7e66-290">Elements and attributes of this extension</span></span>

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

<span data-ttu-id="b7e66-291">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span><span class="sxs-lookup"><span data-stu-id="b7e66-291">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span></span>

|<span data-ttu-id="b7e66-292">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-292">Name</span></span> |<span data-ttu-id="b7e66-293">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b7e66-293">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="b7e66-294">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b7e66-294">Category</span></span> |<span data-ttu-id="b7e66-295">Immer ``windows.fileTypeAssociation``.</span><span class="sxs-lookup"><span data-stu-id="b7e66-295">Always ``windows.fileTypeAssociation``.</span></span>
|<span data-ttu-id="b7e66-296">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-296">Name</span></span> |<span data-ttu-id="b7e66-297">Eine eindeutige ID für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="b7e66-297">A unique Id for your app.</span></span> |
|<span data-ttu-id="b7e66-298">MultiSelectModel</span><span class="sxs-lookup"><span data-stu-id="b7e66-298">MultiSelectModel</span></span> |<span data-ttu-id="b7e66-299">Weitere Informationen finden Sie unter unten.</span><span class="sxs-lookup"><span data-stu-id="b7e66-299">See below</span></span> |
|<span data-ttu-id="b7e66-300">FileType</span><span class="sxs-lookup"><span data-stu-id="b7e66-300">FileType</span></span> |<span data-ttu-id="b7e66-301">Die relevanten Dateierweiterungen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-301">The relevant file extensions.</span></span> |

**<span data-ttu-id="b7e66-302">MultSelectModel</span><span class="sxs-lookup"><span data-stu-id="b7e66-302">MultSelectModel</span></span>**

<span data-ttu-id="b7e66-303">Bei verpackten Desktop-Apps stehen die gleichen drei Optionen zur Verfügung wie bei regulären Desktop-Apps.</span><span class="sxs-lookup"><span data-stu-id="b7e66-303">packaged desktop apps have the same three options as regular desktop apps.</span></span>

* ``Player``<span data-ttu-id="b7e66-304">: Ihre Anwendung wird einmal aktiviert.</span><span class="sxs-lookup"><span data-stu-id="b7e66-304">: Your application is activated one time.</span></span> <span data-ttu-id="b7e66-305">Alle der ausgewählten Dateien werden an die Anwendung als Argument-Parameter übergeben.</span><span class="sxs-lookup"><span data-stu-id="b7e66-305">All of the selected files are passed to your application as argument parameters.</span></span>
* ``Single``<span data-ttu-id="b7e66-306">: Ihre Anwendung wird einmal für die erste markierte Datei aktiviert.</span><span class="sxs-lookup"><span data-stu-id="b7e66-306">: Your application is activated one time for the first selected file.</span></span> <span data-ttu-id="b7e66-307">Andere Dateien werden ignoriert.</span><span class="sxs-lookup"><span data-stu-id="b7e66-307">Other files are ignored.</span></span>
* ``Document``<span data-ttu-id="b7e66-308">: Eine neue (eigene) Instanz Ihrer Anwendung wird für jede markierte Datei aktiviert.</span><span class="sxs-lookup"><span data-stu-id="b7e66-308">: A new, separate instance of your application is activated for each selected file.</span></span>

 <span data-ttu-id="b7e66-309">Für unterschiedliche Dateitypen und Aktionen können unterschiedliche Einstellungen festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="b7e66-309">You can set different preferences for different file types and actions.</span></span> <span data-ttu-id="b7e66-310">So können beispielsweise *Dokumente* im Modus *Document* und *Bilder* im Modus *Player* geöffnet werden.</span><span class="sxs-lookup"><span data-stu-id="b7e66-310">For example, you may wish to open *Documents* in *Document* mode and *Images* in *Player* mode.</span></span>

#### <a name="example"></a><span data-ttu-id="b7e66-311">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b7e66-311">Example</span></span>

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

<span data-ttu-id="b7e66-312">Wenn der Benutzer 15 oder weniger Dateien öffnet, ist die Standardauswahl des **MultiSelectModel**-Attributs *Player*.</span><span class="sxs-lookup"><span data-stu-id="b7e66-312">If the user opens 15 or fewer files, the default choice for the **MultiSelectModel** attribute is *Player*.</span></span> <span data-ttu-id="b7e66-313">Andernfalls ist die Standardauswahl *Document*.</span><span class="sxs-lookup"><span data-stu-id="b7e66-313">Otherwise, the default is *Document*.</span></span> <span data-ttu-id="b7e66-314">UWP-Apps werden immer als *Player* gestartet.</span><span class="sxs-lookup"><span data-stu-id="b7e66-314">UWP apps are always started as *Player*.</span></span>

<a id="show" />

### <a name="show-file-contents-in-a-thumbnail-image-within-file-explorer"></a><span data-ttu-id="b7e66-315">Zeigen Sie Dateiinhalte in einem Miniaturbild im Datei-Explorer an.</span><span class="sxs-lookup"><span data-stu-id="b7e66-315">Show file contents in a thumbnail image within File Explorer</span></span>

<span data-ttu-id="b7e66-316">Ermöglichen Sie es Benutzern, eine Miniaturansicht des Dateiinhalts anzuzeigen, wenn das Symbol der Datei in den Größen Mittel, Groß, oder extra Groß angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b7e66-316">Enable users to view a thumbnail image of the file's contents when the icon of the file appears in the medium, large, or extra large size.</span></span>

#### <a name="xml-namespace"></a><span data-ttu-id="b7e66-317">XML-Namespace</span><span class="sxs-lookup"><span data-stu-id="b7e66-317">XML namespace</span></span>

* http://schemas.microsoft.com/appx/manifest/uap/windows10
* http://schemas.microsoft.com/appx/manifest/uap/windows10/2
* http://schemas.microsoft.com/appx/manifest/uap/windows10/3
* http://schemas.microsoft.com/appx/manifest/desktop/windows10/2

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="b7e66-318">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b7e66-318">Elements and attributes of this extension</span></span>

```XML
<Extension Category="windows.fileTypeAssociation">
    <FileTypeAssociation Name="[AppID]">
        <SupportedFileTypes>
            <FileType>"[FileExtension]"</FileType>
        </SupportedFileTypes>
        <ThumbnailHandler
            Clsid  ="[Clsid  ]" />
    </FileTypeAssociation>
</Extension>
```

<span data-ttu-id="b7e66-319">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span><span class="sxs-lookup"><span data-stu-id="b7e66-319">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span></span>

|<span data-ttu-id="b7e66-320">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-320">Name</span></span> |<span data-ttu-id="b7e66-321">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b7e66-321">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="b7e66-322">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b7e66-322">Category</span></span> |<span data-ttu-id="b7e66-323">Immer ``windows.fileTypeAssociation``.</span><span class="sxs-lookup"><span data-stu-id="b7e66-323">Always ``windows.fileTypeAssociation``.</span></span>
|<span data-ttu-id="b7e66-324">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-324">Name</span></span> |<span data-ttu-id="b7e66-325">Eine eindeutige ID für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="b7e66-325">A unique Id for your app.</span></span> |
|<span data-ttu-id="b7e66-326">FileType</span><span class="sxs-lookup"><span data-stu-id="b7e66-326">FileType</span></span> |<span data-ttu-id="b7e66-327">Die relevanten Dateierweiterungen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-327">The relevant file extensions.</span></span> |
|<span data-ttu-id="b7e66-328">Clsid</span><span class="sxs-lookup"><span data-stu-id="b7e66-328">Clsid</span></span>   |<span data-ttu-id="b7e66-329">Die Klassen-ID Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="b7e66-329">The class ID of your app.</span></span> |

#### <a name="example"></a><span data-ttu-id="b7e66-330">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b7e66-330">Example</span></span>

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
              Clsid  ="20000000-0000-0000-0000-000000000001"  />
            </uap3:FileTypeAssociation>
         </uap::Extension>
      </Extensions>
    </Application>
  </Applications>
</Package>
```

<a id="preview" />

### <a name="show-file-contents-in-the-preview-pane-of-file-explorer"></a><span data-ttu-id="b7e66-331">Zeigen Sie Dateiinhalte in der Vorschau des Datei-Explorers an.</span><span class="sxs-lookup"><span data-stu-id="b7e66-331">Show file contents in the Preview pane of File Explorer</span></span>

<span data-ttu-id="b7e66-332">Ermöglichen Sie es Benutzern, den Inhalt einer Datei in Vorschaubereich des Datei-Explorers anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-332">Enable users to preview a file's contents in the Preview pane of File Explorer.</span></span>

#### <a name="xml-namespace"></a><span data-ttu-id="b7e66-333">XML-Namespace</span><span class="sxs-lookup"><span data-stu-id="b7e66-333">XML namespace</span></span>

* http://schemas.microsoft.com/appx/manifest/uap/windows10
* http://schemas.microsoft.com/appx/manifest/uap/windows10/2
* http://schemas.microsoft.com/appx/manifest/uap/windows10/3
* http://schemas.microsoft.com/appx/manifest/desktop/windows10/2

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="b7e66-334">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b7e66-334">Elements and attributes of this extension</span></span>

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

<span data-ttu-id="b7e66-335">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span><span class="sxs-lookup"><span data-stu-id="b7e66-335">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span></span>

|<span data-ttu-id="b7e66-336">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-336">Name</span></span> |<span data-ttu-id="b7e66-337">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b7e66-337">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="b7e66-338">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b7e66-338">Category</span></span> |<span data-ttu-id="b7e66-339">Immer ``windows.fileTypeAssociation``.</span><span class="sxs-lookup"><span data-stu-id="b7e66-339">Always ``windows.fileTypeAssociation``.</span></span>
|<span data-ttu-id="b7e66-340">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-340">Name</span></span> |<span data-ttu-id="b7e66-341">Eine eindeutige ID für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="b7e66-341">A unique Id for your app.</span></span> |
|<span data-ttu-id="b7e66-342">FileType</span><span class="sxs-lookup"><span data-stu-id="b7e66-342">FileType</span></span> |<span data-ttu-id="b7e66-343">Die relevanten Dateierweiterungen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-343">The relevant file extensions.</span></span> |
|<span data-ttu-id="b7e66-344">Clsid</span><span class="sxs-lookup"><span data-stu-id="b7e66-344">Clsid</span></span>   |<span data-ttu-id="b7e66-345">Die Klassen-ID Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="b7e66-345">The class ID of your app.</span></span> |

#### <a name="example"></a><span data-ttu-id="b7e66-346">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b7e66-346">Example</span></span>

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

<a id="enable" />

### <a name="enable-users-to-group-files-by-using-the-kind-column-in-file-explorer"></a><span data-ttu-id="b7e66-347">Ermöglichen Sie es Benutzern, Dateien mithilfe der Spalte „Art” im Datei-Explorer zu gruppieren.</span><span class="sxs-lookup"><span data-stu-id="b7e66-347">Enable users to group files by using the Kind column in File Explorer</span></span>

<span data-ttu-id="b7e66-348">Sie können einen oder mehrere vordefinierte Werte für die Dateitypen mit dem **Art**-Feld zuordnen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-348">You can associate one or more predefined values for your file types with the **Kind** field.</span></span>

<span data-ttu-id="b7e66-349">Im Datei-Explorer können Benutzer diese Dateien mithilfe dieses Felds gruppieren.</span><span class="sxs-lookup"><span data-stu-id="b7e66-349">In File Explorer, users can group those files by using that field.</span></span> <span data-ttu-id="b7e66-350">Systemkomponenten verwenden auch dieses Feld für verschiedene Zwecke, wie etwa für die Indizierung.</span><span class="sxs-lookup"><span data-stu-id="b7e66-350">System components also use this field for various purposes such as indexing.</span></span>

<span data-ttu-id="b7e66-351">Für weitere Informationen zum **Art**-Feld und die Werte, die Sie für dieses Feld verwenden können, finden Sie unter [Art Namen verwenden](https://msdn.microsoft.com/library/windows/desktop/cc144136.aspx).</span><span class="sxs-lookup"><span data-stu-id="b7e66-351">For more information about the **Kind** field and the values that you can use for this field, see [Using Kind Names](https://msdn.microsoft.com/library/windows/desktop/cc144136.aspx).</span></span>

#### <a name="xml-namespaces"></a><span data-ttu-id="b7e66-352">XML-Namespaces</span><span class="sxs-lookup"><span data-stu-id="b7e66-352">XML namespaces</span></span>

* http://schemas.microsoft.com/appx/manifest/uap/windows10
* http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities/3

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="b7e66-353">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b7e66-353">Elements and attributes of this extension</span></span>

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

<span data-ttu-id="b7e66-354">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span><span class="sxs-lookup"><span data-stu-id="b7e66-354">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span></span>

|<span data-ttu-id="b7e66-355">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-355">Name</span></span> |<span data-ttu-id="b7e66-356">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b7e66-356">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="b7e66-357">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b7e66-357">Category</span></span> |<span data-ttu-id="b7e66-358">Immer ``windows.fileTypeAssociation``.</span><span class="sxs-lookup"><span data-stu-id="b7e66-358">Always ``windows.fileTypeAssociation``.</span></span>
|<span data-ttu-id="b7e66-359">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-359">Name</span></span> |<span data-ttu-id="b7e66-360">Eine eindeutige ID für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="b7e66-360">A unique Id for your app.</span></span> |
|<span data-ttu-id="b7e66-361">FileType</span><span class="sxs-lookup"><span data-stu-id="b7e66-361">FileType</span></span> |<span data-ttu-id="b7e66-362">Die relevanten Dateierweiterungen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-362">The relevant file extensions.</span></span> |
|<span data-ttu-id="b7e66-363">Wert</span><span class="sxs-lookup"><span data-stu-id="b7e66-363">value</span></span> |<span data-ttu-id="b7e66-364">Ein gültiger [Art-Wert](https://msdn.microsoft.com/en-us/library/windows/desktop/cc144136.aspx#kind_hierarchy)</span><span class="sxs-lookup"><span data-stu-id="b7e66-364">A valid [Kind value](https://msdn.microsoft.com/en-us/library/windows/desktop/cc144136.aspx#kind_hierarchy)</span></span> |

#### <a name="example"></a><span data-ttu-id="b7e66-365">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b7e66-365">Example</span></span>

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

<a id="make-file-properties" />

### <a name="make-file-properties-available-to-search-index-property-dialogs-and-the-details-pane"></a><span data-ttu-id="b7e66-366">Stellen Sie den Bereichen Suchen, Index, Eigenschaftendialogfelder und Details Dateieigenschaften zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="b7e66-366">Make file properties available to search, index, property dialogs, and the details pane</span></span>

#### <a name="xml-namespace"></a><span data-ttu-id="b7e66-367">XML-Namespace</span><span class="sxs-lookup"><span data-stu-id="b7e66-367">XML namespace</span></span>

* http://schemas.microsoft.com/appx/manifest/uap/windows10
* http://schemas.microsoft.com/appx/manifest/uap/windows10/3
* http://schemas.microsoft.com/appx/manifest/desktop/windows10/2

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="b7e66-368">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b7e66-368">Elements and attributes of this extension</span></span>

```XML
<uap:Extension Category="windows.fileTypeAssociation">
    <uap:FileTypeAssociation Name="[AppID]">
        <SupportedFileTypes>
            <FileType>.bar</FileType>
        </SupportedFileTypes>
        <DesktopPropertyHandler Clsid ="[Clsid]"/>
    </uap:FileTypeAssociation>
</uap:Extension>
```

<span data-ttu-id="b7e66-369">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span><span class="sxs-lookup"><span data-stu-id="b7e66-369">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span></span>

|<span data-ttu-id="b7e66-370">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-370">Name</span></span> |<span data-ttu-id="b7e66-371">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b7e66-371">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="b7e66-372">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b7e66-372">Category</span></span> |<span data-ttu-id="b7e66-373">Immer ``windows.fileTypeAssociation``.</span><span class="sxs-lookup"><span data-stu-id="b7e66-373">Always ``windows.fileTypeAssociation``.</span></span>
|<span data-ttu-id="b7e66-374">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-374">Name</span></span> |<span data-ttu-id="b7e66-375">Eine eindeutige ID für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="b7e66-375">A unique Id for your app.</span></span> |
|<span data-ttu-id="b7e66-376">FileType</span><span class="sxs-lookup"><span data-stu-id="b7e66-376">FileType</span></span> |<span data-ttu-id="b7e66-377">Die relevanten Dateierweiterungen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-377">The relevant file extensions.</span></span> |
|<span data-ttu-id="b7e66-378">Clsid</span><span class="sxs-lookup"><span data-stu-id="b7e66-378">Clsid</span></span>  |<span data-ttu-id="b7e66-379">Die Klassen-ID Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="b7e66-379">The class ID of your app.</span></span> |

#### <a name="example"></a><span data-ttu-id="b7e66-380">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b7e66-380">Example</span></span>

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

<a id="cloud-files" />

### <a name="make-files-from-your-cloud-service-appear-in-file-explorer"></a><span data-ttu-id="b7e66-381">Zeigen Sie Dateien von Ihrem Clouddienst im Datei-Explorer an</span><span class="sxs-lookup"><span data-stu-id="b7e66-381">Make files from your cloud service appear in File Explorer</span></span>

<span data-ttu-id="b7e66-382">Registrieren Sie die Handler, die Sie in Ihrer Anwendung implementieren.</span><span class="sxs-lookup"><span data-stu-id="b7e66-382">Register the handlers that you implement in your application.</span></span> <span data-ttu-id="b7e66-383">Sie können auch Kontextmenüoptionen hinzufügen, die angezeigt werden, wenn Ihre Benutzer im Datei-Explorer mit der rechten Maustaste auf die cloudbasierten Dateien klicken.</span><span class="sxs-lookup"><span data-stu-id="b7e66-383">You can also add context menu options that appear when you users right-click your cloud-based files in File Explorer.</span></span>

#### <a name="xml-namespace"></a><span data-ttu-id="b7e66-384">XML-Namespace</span><span class="sxs-lookup"><span data-stu-id="b7e66-384">XML namespace</span></span>

* http://schemas.microsoft.com/appx/manifest/desktop/windows10

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="b7e66-385">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b7e66-385">Elements and attributes of this extension</span></span>

```XML
<Extension Category="windows.cloudfiles" >
    <CloudFiles IconResource="[Icon]">
        <CustomStateHandler Clsid ="[Clsid]"/>
        <ThumbnailProviderHandler Clsid ="[Clsid]"/>
        <ExtendedPropertyhandler Clsid ="[Clsid]"/>
        <CloudFilesContextMenus>
            <Verb Id ="Command3" Clsid= "[GUID]">[Verb Label]</Verb>
        </CloudFilesContextMenus>
    </CloudFiles>
</Extension>

```

|<span data-ttu-id="b7e66-386">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-386">Name</span></span> |<span data-ttu-id="b7e66-387">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b7e66-387">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="b7e66-388">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b7e66-388">Category</span></span> |<span data-ttu-id="b7e66-389">Immer ``windows.cloudfiles``.</span><span class="sxs-lookup"><span data-stu-id="b7e66-389">Always ``windows.cloudfiles``.</span></span>
|<span data-ttu-id="b7e66-390">iconResource</span><span class="sxs-lookup"><span data-stu-id="b7e66-390">iconResource</span></span> |<span data-ttu-id="b7e66-391">Das Symbol, das den Dienst Ihres Cloud-Datei-Anbieters darstellt.</span><span class="sxs-lookup"><span data-stu-id="b7e66-391">The icon that represents your cloud file provider service.</span></span> <span data-ttu-id="b7e66-392">Dieses Symbol wird im Navigationsbereich des Datei-Explorers angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b7e66-392">This icon appears in the Navigation pane of File Explorer.</span></span>  <span data-ttu-id="b7e66-393">Benutzer wählen dieses Symbol, um Dateien von Ihrem Clouddienst anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-393">Users choose this icon to show files from your cloud service.</span></span> |
|<span data-ttu-id="b7e66-394">CustomStateHandler Clsid</span><span class="sxs-lookup"><span data-stu-id="b7e66-394">CustomStateHandler Clsid</span></span> |<span data-ttu-id="b7e66-395">Die Klassen-ID der Anwendung, die die CustomStateHandler implementiert.</span><span class="sxs-lookup"><span data-stu-id="b7e66-395">The class ID of the application that implements the CustomStateHandler.</span></span> <span data-ttu-id="b7e66-396">Das System verwendet diese Klassen-ID, um benutzerdefinierte Zustände und Spalten für Cloud-Dateien anzufordern.</span><span class="sxs-lookup"><span data-stu-id="b7e66-396">The system uses this Class ID to request custom states and columns for cloud files.</span></span> |
|<span data-ttu-id="b7e66-397">ThumbnailProviderHandler Clsid</span><span class="sxs-lookup"><span data-stu-id="b7e66-397">ThumbnailProviderHandler Clsid</span></span> |<span data-ttu-id="b7e66-398">Die Klassen-ID der Anwendung, die den ThumbnailProviderHandler implementiert.</span><span class="sxs-lookup"><span data-stu-id="b7e66-398">The class ID of the application that implements the ThumbnailProviderHandler.</span></span> <span data-ttu-id="b7e66-399">Das System verwendet diese Klassen-ID, um Miniaturansichten für Cloud-Dateien anzufordern.</span><span class="sxs-lookup"><span data-stu-id="b7e66-399">The system uses this Class ID to request thumbnail images for cloud files.</span></span> |
|<span data-ttu-id="b7e66-400">ExtendedPropertyHandler Clsid</span><span class="sxs-lookup"><span data-stu-id="b7e66-400">ExtendedPropertyHandler Clsid</span></span> |<span data-ttu-id="b7e66-401">Die Klassen-ID der Anwendung, die den ExtendedPropertyHandler implementiert.</span><span class="sxs-lookup"><span data-stu-id="b7e66-401">The class ID of the application that implements the ExtendedPropertyHandler.</span></span>  <span data-ttu-id="b7e66-402">Das System verwendet diese Klassen-ID, um erweiterte Eigenschaften für eine Cloud-Datei anzufordern.</span><span class="sxs-lookup"><span data-stu-id="b7e66-402">The system uses this Class ID to request extended properties for a cloud file.</span></span> |
|<span data-ttu-id="b7e66-403">Verb</span><span class="sxs-lookup"><span data-stu-id="b7e66-403">Verb</span></span> |<span data-ttu-id="b7e66-404">Der Name, der im Kontextmenü des Datei-Explorers für Dateien angezeigt wird, die von Ihrem Clouddienst bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="b7e66-404">The name that appears in the File Explorer context menu for files provided by your cloud service.</span></span> |
|<span data-ttu-id="b7e66-405">ID</span><span class="sxs-lookup"><span data-stu-id="b7e66-405">Id</span></span> |<span data-ttu-id="b7e66-406">Die eindeutige ID des Verbs.</span><span class="sxs-lookup"><span data-stu-id="b7e66-406">The unique ID of the verb.</span></span> |

#### <a name="example"></a><span data-ttu-id="b7e66-407">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b7e66-407">Example</span></span>

```XML
<Package
    xmlns:desktop="http://schemas.microsoft.com/appx/manifest/desktop/windows10"
    IgnorableNamespaces="desktop">
  <Applications>
    <Application>
      <Extensions>
        <Extension Category="windows.cloudfiles" >
            <CloudFiles IconResource="images\Wide310x150Logo.png">
                <CustomStateHandler Clsid ="20000000-0000-0000-0000-000000000001"/>
                <ThumbnailProviderHandler Clsid ="20000000-0000-0000-0000-000000000001"/>
                <ExtendedPropertyhandler Clsid ="20000000-0000-0000-0000-000000000001"/>
                <desktop:CloudFilesContextMenus>
                    <desktop:Verb Id ="keep" Clsid=
                       "20000000-0000-0000-0000-000000000001">
                       Always keep on this device</desktop:Verb>
                </desktop:CloudFilesContextMenus>
            </CloudFiles>
          </Extension>
      </Extensions>
    </Application>
  </Applications>
</Package>
```

<a id="start" />

## <a name="start-your-application-in-different-ways"></a><span data-ttu-id="b7e66-408">Starten Sie die Anwendung auf unterschiedliche Weise</span><span class="sxs-lookup"><span data-stu-id="b7e66-408">Start your application in different ways</span></span>

* [<span data-ttu-id="b7e66-409">Starten Sie die Anwendung über ein Protokoll</span><span class="sxs-lookup"><span data-stu-id="b7e66-409">Start your application by using a protocol</span></span>](#protocol)
* [<span data-ttu-id="b7e66-410">Starten Sie die Anwendung durch die Verwendung eines Alias.</span><span class="sxs-lookup"><span data-stu-id="b7e66-410">Start your application by using an alias</span></span>](#alias)
* [<span data-ttu-id="b7e66-411">Starten Sie eine ausführbare Datei, wenn Benutzer sich bei Windows anmelden.</span><span class="sxs-lookup"><span data-stu-id="b7e66-411">Start an executable file when users log into Windows</span></span>](#executable)
* [<span data-ttu-id="b7e66-412">Ermöglichen Sie es Benutzern, Ihre Anwendung zu starten, wenn sie ein Gerät an seinen PC anschließen</span><span class="sxs-lookup"><span data-stu-id="b7e66-412">Enable users to start your application when they connect a device to their PC</span></span>](#autoplay)
* [<span data-ttu-id="b7e66-413">Starten Sie nach Erhalt eines Updates vom Microsoft Store automatisch neu</span><span class="sxs-lookup"><span data-stu-id="b7e66-413">Restart automatically after receiving an update from the Microsoft Store</span></span>](#updates)

<a id="protocol" />

### <a name="start-your-application-by-using-a-protocol"></a><span data-ttu-id="b7e66-414">Starten Sie die Anwendung über ein Protokoll</span><span class="sxs-lookup"><span data-stu-id="b7e66-414">Start your application by using a protocol</span></span>

<span data-ttu-id="b7e66-415">Protokollzuordnungen ermöglichen es anderen Programmen und Systemkomponenten, mit Ihrer verpackten App zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="b7e66-415">Protocol associations can enable other programs and system components to interoperate with your packaged app.</span></span> <span data-ttu-id="b7e66-416">Wenn Ihre Anwendung anhand eines Protokolls gestartet wird, können Sie bestimmte Parameter angeben, an die aktivierungsereignisargumente übergeben werden soll, werden entsprechend Verhalten zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-416">When your packaged application is started by using a protocol, you can specify specific parameters to pass to its activation event arguments so it can behave accordingly.</span></span> <span data-ttu-id="b7e66-417">Parameter werden nur für verpackte, vertrauenswürdige Apps unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b7e66-417">Parameters are supported only for packaged, full-trust apps.</span></span> <span data-ttu-id="b7e66-418">UWP-Apps können die Parameter nicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="b7e66-418">UWP apps can't use parameters.</span></span>

#### <a name="xml-namespace"></a><span data-ttu-id="b7e66-419">XML-Namespace</span><span class="sxs-lookup"><span data-stu-id="b7e66-419">XML namespace</span></span>

http://schemas.microsoft.com/appx/manifest/uap/windows10/3

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="b7e66-420">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b7e66-420">Elements and attributes of this extension</span></span>

```XML
<Extension
    Category="windows.protocol">
  <Protocol
      Name="[Protocol name]"
      Parameters="[Parameters]" />
</Extension>
```

<span data-ttu-id="b7e66-421">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-protocol).</span><span class="sxs-lookup"><span data-stu-id="b7e66-421">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-protocol).</span></span>

|<span data-ttu-id="b7e66-422">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-422">Name</span></span> |<span data-ttu-id="b7e66-423">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b7e66-423">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="b7e66-424">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b7e66-424">Category</span></span> |<span data-ttu-id="b7e66-425">Immer ``windows.protocol``.</span><span class="sxs-lookup"><span data-stu-id="b7e66-425">Always ``windows.protocol``.</span></span>
|<span data-ttu-id="b7e66-426">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-426">Name</span></span> |<span data-ttu-id="b7e66-427">Der Name des Protokolls.</span><span class="sxs-lookup"><span data-stu-id="b7e66-427">The name of the protocol.</span></span> |
|<span data-ttu-id="b7e66-428">Parameter</span><span class="sxs-lookup"><span data-stu-id="b7e66-428">Parameters</span></span> |<span data-ttu-id="b7e66-429">Die Liste der Parameter und Werte, die an die Anwendung als Ereignisargumente übergeben, wenn die Anwendung aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="b7e66-429">The list of parameters and values to pass to your application as event arguments when the application is activated.</span></span> <span data-ttu-id="b7e66-430">Wenn eine Variable einen Dateipfad enthalten kann, schließen Sie den Parameterwert in Anführungszeichen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-430">If a variable can contain a file path, wrap the parameter value in quotes.</span></span> <span data-ttu-id="b7e66-431">Dadurch werden jegliche Probleme vermieden, die in Fällen auftreten, bei denen der Pfad Leerzeichen enthält.</span><span class="sxs-lookup"><span data-stu-id="b7e66-431">That will avoid any issues that happen in cases where the path includes spaces.</span></span> |

### <a name="example"></a><span data-ttu-id="b7e66-432">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b7e66-432">Example</span></span>

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

<a id="alias" />

### <a name="start-your-application-by-using-an-alias"></a><span data-ttu-id="b7e66-433">Starten Sie die Anwendung durch die Verwendung eines Alias.</span><span class="sxs-lookup"><span data-stu-id="b7e66-433">Start your application by using an alias</span></span>

<span data-ttu-id="b7e66-434">Benutzer und andere Prozesse können einen Alias verwenden, um die Anwendung zu starten, ohne den vollständigen Pfad zu Ihrer app angeben zu müssen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-434">Users and other processes can use an alias to start your application without having to specify the full path to your app.</span></span> <span data-ttu-id="b7e66-435">Sie können diesen Aliasnamen angeben.</span><span class="sxs-lookup"><span data-stu-id="b7e66-435">You can specify that alias name.</span></span>

#### <a name="xml-namespaces"></a><span data-ttu-id="b7e66-436">XML-Namespaces</span><span class="sxs-lookup"><span data-stu-id="b7e66-436">XML namespaces</span></span>

* http://schemas.microsoft.com/appx/manifest/uap/windows10/3
* http://schemas.microsoft.com/appx/manifest/desktop/windows10

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="b7e66-437">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b7e66-437">Elements and attributes of this extension</span></span>

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

|<span data-ttu-id="b7e66-438">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-438">Name</span></span> |<span data-ttu-id="b7e66-439">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b7e66-439">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="b7e66-440">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b7e66-440">Category</span></span> |<span data-ttu-id="b7e66-441">Immer ``windows.appExecutionAlias``.</span><span class="sxs-lookup"><span data-stu-id="b7e66-441">Always ``windows.appExecutionAlias``.</span></span>
|<span data-ttu-id="b7e66-442">Ausführbare Datei</span><span class="sxs-lookup"><span data-stu-id="b7e66-442">Executable</span></span> |<span data-ttu-id="b7e66-443">Der relative Pfad zur ausführbaren Datei, die beim Aufrufen des Alias gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="b7e66-443">The relative path to the executable to start when the alias is invoked.</span></span> |
|<span data-ttu-id="b7e66-444">Alias</span><span class="sxs-lookup"><span data-stu-id="b7e66-444">Alias</span></span> |<span data-ttu-id="b7e66-445">Der kurze Name für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="b7e66-445">The short name for your app.</span></span> <span data-ttu-id="b7e66-446">Er muss immer mit der Erweiterung „.exe“ enden.</span><span class="sxs-lookup"><span data-stu-id="b7e66-446">It must always end with the ".exe" extension.</span></span> <span data-ttu-id="b7e66-447">Für die einzelnen Anwendungen im Paket kann immer nur einzelner App-Ausführungsalias angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="b7e66-447">You can only specify a single app execution alias for each application in the package.</span></span> <span data-ttu-id="b7e66-448">Wenn sich mehrere Apps mit dem gleichen Alias registrieren, ruft das System die zuletzt registrierte App auf. Wählen Sie daher einen eindeutigen Alias, um die Wahrscheinlichkeit einer Überschreibung durch andere Apps möglichst gering zu halten.</span><span class="sxs-lookup"><span data-stu-id="b7e66-448">If multiple apps register for the same alias, the system will invoke the last one that was registered, so make sure to choose a unique alias other apps are unlikely to override.</span></span>
|

#### <a name="example"></a><span data-ttu-id="b7e66-449">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b7e66-449">Example</span></span>

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

<span data-ttu-id="b7e66-450">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span><span class="sxs-lookup"><span data-stu-id="b7e66-450">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap-filetypeassociation).</span></span>

<a id="executable" />

### <a name="start-an-executable-file-when-users-log-into-windows"></a><span data-ttu-id="b7e66-451">Starten Sie eine ausführbare Datei, wenn Benutzer sich bei Windows anmelden.</span><span class="sxs-lookup"><span data-stu-id="b7e66-451">Start an executable file when users log into Windows</span></span>

<span data-ttu-id="b7e66-452">Startaufgaben können eine Anwendung auf eine ausführbare Datei automatisch ausgeführt werden, wenn sich ein Benutzer anmeldet.</span><span class="sxs-lookup"><span data-stu-id="b7e66-452">Startup tasks allow your application to run an executable automatically whenever a user logs on.</span></span>

> [!NOTE]
> <span data-ttu-id="b7e66-453">Der Benutzer muss die Anwendung mindestens ein Mal starten, um diese Startaufgabe registrieren.</span><span class="sxs-lookup"><span data-stu-id="b7e66-453">The user has to start your application at least one time to register this startup task.</span></span>

<span data-ttu-id="b7e66-454">Ihre Anwendung kann mehrere Startaufgaben deklarieren.</span><span class="sxs-lookup"><span data-stu-id="b7e66-454">Your application can declare multiple startup tasks.</span></span> <span data-ttu-id="b7e66-455">Die Aufgaben beginnen unabhängig voneinander.</span><span class="sxs-lookup"><span data-stu-id="b7e66-455">Each task starts independently.</span></span> <span data-ttu-id="b7e66-456">Alle Startaufgaben werden im Task-Manager auf der Registerkarte **Autostart** mit dem Namen aus Ihrem App-Manifest und dem Symbol Ihrer App angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b7e66-456">All startup tasks will appear in Task Manager under the **Startup** tab with the name that you specify in your app's manifest and your app's icon.</span></span> <span data-ttu-id="b7e66-457">Der Task-Manager analysiert automatisch die Startauswirkungen Ihrer Aufgaben.</span><span class="sxs-lookup"><span data-stu-id="b7e66-457">Task Manager will automatically analyze the startup impact of your tasks.</span></span>

<span data-ttu-id="b7e66-458">Benutzer können die Startaufgabe Ihrer App manuell mithilfe des Task-Managers deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="b7e66-458">Users can manually disable your app's startup task by using Task Manager.</span></span> <span data-ttu-id="b7e66-459">Wenn ein Benutzer eine Aufgabe deaktiviert, können Sie sie nicht erneut programmgesteuert aktivieren.</span><span class="sxs-lookup"><span data-stu-id="b7e66-459">If a user disables a task, you can't programmatically re-enable it.</span></span>

#### <a name="xml-namespace"></a><span data-ttu-id="b7e66-460">XML-Namespace</span><span class="sxs-lookup"><span data-stu-id="b7e66-460">XML namespace</span></span>

http://schemas.microsoft.com/appx/manifest/desktop/windows10

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="b7e66-461">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b7e66-461">Elements and attributes of this extension</span></span>

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

|<span data-ttu-id="b7e66-462">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-462">Name</span></span> |<span data-ttu-id="b7e66-463">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b7e66-463">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="b7e66-464">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b7e66-464">Category</span></span> |<span data-ttu-id="b7e66-465">Immer ``windows.startupTask``.</span><span class="sxs-lookup"><span data-stu-id="b7e66-465">Always ``windows.startupTask``.</span></span>|
|<span data-ttu-id="b7e66-466">Ausführbare Datei</span><span class="sxs-lookup"><span data-stu-id="b7e66-466">Executable</span></span> |<span data-ttu-id="b7e66-467">Der relative Pfad der ausführbaren Datei, die gestartet werden soll.</span><span class="sxs-lookup"><span data-stu-id="b7e66-467">The relative path to the executable file to start.</span></span> |
|<span data-ttu-id="b7e66-468">TaskId</span><span class="sxs-lookup"><span data-stu-id="b7e66-468">TaskId</span></span> |<span data-ttu-id="b7e66-469">Ein eindeutiger Bezeichner Ihrer Aufgabe.</span><span class="sxs-lookup"><span data-stu-id="b7e66-469">A unique identifier for your task.</span></span> <span data-ttu-id="b7e66-470">Mit diesem Bezeichner kann Ihre Anwendung die APIs aufrufen in der [Windows.ApplicationModel.StartupTask](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.StartupTask) -Klasse, um programmgesteuert zu aktivieren oder deaktivieren eine Startaufgabe.</span><span class="sxs-lookup"><span data-stu-id="b7e66-470">Using this identifier, your application can call the APIs in the [Windows.ApplicationModel.StartupTask](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.StartupTask) class to programmatically enable or disable a startup task.</span></span> |
|<span data-ttu-id="b7e66-471">Enabled</span><span class="sxs-lookup"><span data-stu-id="b7e66-471">Enabled</span></span> |<span data-ttu-id="b7e66-472">Gibt an, ob die Aufgabe erst aktiviert oder deaktiviert gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="b7e66-472">Indicates whether the task first starts enabled or disabled.</span></span> <span data-ttu-id="b7e66-473">Aktivierte Aufgaben werden bei der nächsten Anmeldung des Benutzers ausgeführt (es sei denn, der Benutzer deaktiviert sie).</span><span class="sxs-lookup"><span data-stu-id="b7e66-473">Enabled tasks will run the next time the user logs on (unless the user disables it).</span></span> |
|<span data-ttu-id="b7e66-474">DisplayName</span><span class="sxs-lookup"><span data-stu-id="b7e66-474">DisplayName</span></span> |<span data-ttu-id="b7e66-475">Der Name der Aufgabe, die im Task-Manager angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b7e66-475">The name of the task that appears in Task Manager.</span></span> <span data-ttu-id="b7e66-476">Sie können diese Zeichenfolge mit ```ms-resource``` lokalisieren.</span><span class="sxs-lookup"><span data-stu-id="b7e66-476">You can localize this string by using ```ms-resource```.</span></span> |

#### <a name="example"></a><span data-ttu-id="b7e66-477">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b7e66-477">Example</span></span>

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

<a id="autoplay" />

### <a name="enable-users-to-start-your-application-when-they-connect-a-device-to-their-pc"></a><span data-ttu-id="b7e66-478">Ermöglichen Sie es Benutzern, Ihre Anwendung zu starten, wenn sie ein Gerät an seinen PC anschließen</span><span class="sxs-lookup"><span data-stu-id="b7e66-478">Enable users to start your application when they connect a device to their PC</span></span>

<span data-ttu-id="b7e66-479">Automatische Wiedergabe kann Ihre Anwendung als Option darstellen, wenn ein Benutzer ein Gerät an seinen PC anschließt.</span><span class="sxs-lookup"><span data-stu-id="b7e66-479">AutoPlay can present your application as an option when a user connects a device to their PC.</span></span>

#### <a name="xml-namespace"></a><span data-ttu-id="b7e66-480">XML-Namespace</span><span class="sxs-lookup"><span data-stu-id="b7e66-480">XML namespace</span></span>

http://schemas.microsoft.com/appx/manifest/desktop/windows10/3

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="b7e66-481">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b7e66-481">Elements and attributes of this extension</span></span>

```XML
<Extension Category="windows.autoPlayHandler">
  <AutoPlayHandler>
    <InvokeAction ActionDisplayName="[action string]" ProviderDisplayName="[name of your app/service]">
      <Content ContentEvent="[Content event]" Verb="[any string]" DropTargetHandler="[Clsid]" />
      <Content ContentEvent="[Content event]" Verb="[any string]" Parameters="[Initialization parameter]"/>
      <Device DeviceEvent="[Device event]" HWEventHandler="[Clsid]" InitCmdLine="[Initialization parameter]"/>
    </InvokeAction>
  </AutoPlayHandler>
```

|<span data-ttu-id="b7e66-482">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-482">Name</span></span> |<span data-ttu-id="b7e66-483">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b7e66-483">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="b7e66-484">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b7e66-484">Category</span></span> |<span data-ttu-id="b7e66-485">Immer ``windows.autoPlayHandler``.</span><span class="sxs-lookup"><span data-stu-id="b7e66-485">Always ``windows.autoPlayHandler``.</span></span>
|<span data-ttu-id="b7e66-486">ActionDisplayName</span><span class="sxs-lookup"><span data-stu-id="b7e66-486">ActionDisplayName</span></span> |<span data-ttu-id="b7e66-487">Eine Zeichenfolge, die die Aktion darstellt, die Benutzer mit einem Gerät ausführen können, das sie an einen PC anschließen (z.B.: „Dateien importieren” oder „Video wiedergeben”).</span><span class="sxs-lookup"><span data-stu-id="b7e66-487">A string that represents the action that users can take with a device that they connect to a PC (For example: "Import files", or "Play video").</span></span> |
|<span data-ttu-id="b7e66-488">ProviderDisplayName</span><span class="sxs-lookup"><span data-stu-id="b7e66-488">ProviderDisplayName</span></span> | <span data-ttu-id="b7e66-489">Eine Zeichenfolge, die Ihre Anwendung oder Ihren Dienst darstellt (z. B.: "Contoso-video-Player").</span><span class="sxs-lookup"><span data-stu-id="b7e66-489">A string that represents your application or service (For example: "Contoso video player").</span></span> |
|<span data-ttu-id="b7e66-490">ContentEvent</span><span class="sxs-lookup"><span data-stu-id="b7e66-490">ContentEvent</span></span> |<span data-ttu-id="b7e66-491">Der Name eines Inhaltsereignisses, bei dem Benutzer mit Ihrem ``ActionDisplayName`` und ``ProviderDisplayName`` aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="b7e66-491">The name of a content event that causes users to be prompted with your ``ActionDisplayName`` and ``ProviderDisplayName``.</span></span> <span data-ttu-id="b7e66-492">Ein Inhaltsereignis wird ausgelöst, wenn ein Volumegerät wie etwa die Speicherkarte einer Kamera, eine DVD oder ein USB-Stick in den PC eingelegt bzw. daran angeschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="b7e66-492">A content event is raised when a volume device such as a camera memory card, thumb drive, or DVD is inserted into the PC.</span></span> <span data-ttu-id="b7e66-493">Sie finden die vollständige Liste dieser Ereignisse [hier](https://docs.microsoft.com/windows/uwp/launch-resume/auto-launching-with-autoplay#autoplay-event-reference).</span><span class="sxs-lookup"><span data-stu-id="b7e66-493">You can find the full list of those events [here](https://docs.microsoft.com/windows/uwp/launch-resume/auto-launching-with-autoplay#autoplay-event-reference).</span></span>  |
|<span data-ttu-id="b7e66-494">Verb</span><span class="sxs-lookup"><span data-stu-id="b7e66-494">Verb</span></span> |<span data-ttu-id="b7e66-495">Die Einstellung Verb angeben eines Werts, das für Ihre Anwendung für die ausgewählte Option übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="b7e66-495">The Verb setting identifies a value that is passed to your application for the selected option.</span></span> <span data-ttu-id="b7e66-496">Sie können mehrere Startaktionen für Ereignisse der automatischen Wiedergabe angeben und mit der Einstellung Verb ermitteln, welche Option ein Benutzer für Ihre App ausgewählt hat.</span><span class="sxs-lookup"><span data-stu-id="b7e66-496">You can specify multiple launch actions for an AutoPlay event and use the Verb setting to determine which option a user has selected for your app.</span></span> <span data-ttu-id="b7e66-497">Für welche Option sich der Benutzer entschieden hat, erfahren Sie durch Überprüfen der verb-Eigenschaft der an die App übergebenen Startereignisargumente.</span><span class="sxs-lookup"><span data-stu-id="b7e66-497">You can tell which option the user selected by checking the verb property of the startup event arguments passed to your app.</span></span> <span data-ttu-id="b7e66-498">Für die Einstellung Verb können Sie einen beliebigen Wert verwenden. Einzige Ausnahme ist open: Dieser Wert ist reserviert.</span><span class="sxs-lookup"><span data-stu-id="b7e66-498">You can use any value for the Verb setting except, open, which is reserved.</span></span> |
|<span data-ttu-id="b7e66-499">DropTargetHandler</span><span class="sxs-lookup"><span data-stu-id="b7e66-499">DropTargetHandler</span></span> |<span data-ttu-id="b7e66-500">Die Klassen-ID der Anwendung, die die [IDropTarget](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.idroptarget?view=visualstudiosdk-2017) -Schnittstelle implementiert.</span><span class="sxs-lookup"><span data-stu-id="b7e66-500">The class ID of the application that implements the [IDropTarget](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.idroptarget?view=visualstudiosdk-2017) interface.</span></span> <span data-ttu-id="b7e66-501">Dateien aus Wechselmedien werden an die [Drop](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.idroptarget.drop?view=visualstudiosdk-2017#Microsoft_VisualStudio_OLE_Interop_IDropTarget_Drop_Microsoft_VisualStudio_OLE_Interop_IDataObject_System_UInt32_Microsoft_VisualStudio_OLE_Interop_POINTL_System_UInt32__)-Methode Ihrer [IDropTarget](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.idroptarget?view=visualstudiosdk-2017)-Implementierung übergeben.</span><span class="sxs-lookup"><span data-stu-id="b7e66-501">Files from the removable media are passed to the [Drop](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.idroptarget.drop?view=visualstudiosdk-2017#Microsoft_VisualStudio_OLE_Interop_IDropTarget_Drop_Microsoft_VisualStudio_OLE_Interop_IDataObject_System_UInt32_Microsoft_VisualStudio_OLE_Interop_POINTL_System_UInt32__) method of your [IDropTarget](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.idroptarget?view=visualstudiosdk-2017) implementation.</span></span>  |
|<span data-ttu-id="b7e66-502">Parameter</span><span class="sxs-lookup"><span data-stu-id="b7e66-502">Parameters</span></span> |<span data-ttu-id="b7e66-503">Sie müssen die [IDropTarget](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.idroptarget?view=visualstudiosdk-2017)-Schnittstelle nicht für alle Inhaltsereignisse implementieren.</span><span class="sxs-lookup"><span data-stu-id="b7e66-503">You don't have to implement the [IDropTarget](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.idroptarget?view=visualstudiosdk-2017) interface for all content events.</span></span> <span data-ttu-id="b7e66-504">Für jedes der Inhaltsereignisse können Sie Befehlszeilenparameter bereitstellen, anstatt die [IDropTarget](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.idroptarget?view=visualstudiosdk-2017)-Schnittstelle zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="b7e66-504">For any of the content events, you could provide command line parameters instead of implementing the [IDropTarget](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.ole.interop.idroptarget?view=visualstudiosdk-2017) interface.</span></span> <span data-ttu-id="b7e66-505">Für diese Ereignisse wird automatische Wiedergabe diese Befehlszeilenparameter verwenden, um die Anwendung starten.</span><span class="sxs-lookup"><span data-stu-id="b7e66-505">For those events, AutoPlay will start your application by using those command line parameters.</span></span> <span data-ttu-id="b7e66-506">Sie können diese Parameter im Initialisierungscode Ihrer App analysieren, um festzustellen, ob sie von der automatischen Wiedergabe gestartet wurde, und dann Ihre benutzerdefinierte Implementierung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-506">You can parse those parameters in your app's initialization code to determine if it was started by AutoPlay and then provide your custom implementation.</span></span> |
|<span data-ttu-id="b7e66-507">DeviceEvent</span><span class="sxs-lookup"><span data-stu-id="b7e66-507">DeviceEvent</span></span> |<span data-ttu-id="b7e66-508">Der Name eines Geräteereignisses, bei dem Benutzer mit Ihrem ``ActionDisplayName`` und ``ProviderDisplayName`` aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="b7e66-508">The name of a device event that causes users to be prompted with your ``ActionDisplayName`` and ``ProviderDisplayName``.</span></span> <span data-ttu-id="b7e66-509">Ein Geräteereignis wird ausgelöst, wenn ein Gerät an den PC angeschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="b7e66-509">A device event is raised when a device is connected to the PC.</span></span> <span data-ttu-id="b7e66-510">Geräteereignisse beginnen mit der Zeichenfolge ``WPD`` und sind [hier](https://docs.microsoft.com/windows/uwp/launch-resume/auto-launching-with-autoplay#autoplay-event-reference) aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="b7e66-510">Device events begin with the string ``WPD`` and you can find them listed [here](https://docs.microsoft.com/windows/uwp/launch-resume/auto-launching-with-autoplay#autoplay-event-reference).</span></span> |
|<span data-ttu-id="b7e66-511">HWEventHandler</span><span class="sxs-lookup"><span data-stu-id="b7e66-511">HWEventHandler</span></span> |<span data-ttu-id="b7e66-512">Die Klassen-ID der Anwendung, die die [IHWEventHandler](https://msdn.microsoft.com/library/windows/desktop/bb775492.aspx) -Schnittstelle implementiert.</span><span class="sxs-lookup"><span data-stu-id="b7e66-512">The Class ID of the application that implements the [IHWEventHandler](https://msdn.microsoft.com/library/windows/desktop/bb775492.aspx) interface.</span></span> |
|<span data-ttu-id="b7e66-513">InitCmdLine</span><span class="sxs-lookup"><span data-stu-id="b7e66-513">InitCmdLine</span></span> |<span data-ttu-id="b7e66-514">Der Zeichenfolgeparameter, der an die [Initialize](https://msdn.microsoft.com/en-us/library/windows/desktop/bb775495.aspx)-Methode der [IHWEventHandler](https://msdn.microsoft.com/library/windows/desktop/bb775492.aspx)-Schnittstelle übergeben werden soll.</span><span class="sxs-lookup"><span data-stu-id="b7e66-514">The string parameter that you want to pass into the [Initialize](https://msdn.microsoft.com/en-us/library/windows/desktop/bb775495.aspx) method of the [IHWEventHandler](https://msdn.microsoft.com/library/windows/desktop/bb775492.aspx) interface.</span></span> |

### <a name="example"></a><span data-ttu-id="b7e66-515">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b7e66-515">Example</span></span>

```XML
<Package
  xmlns:desktop3="http://schemas.microsoft.com/appx/manifest/desktop/windows10/3"
  IgnorableNamespaces="desktop3">
  <Applications>
    <Application>
      <Extensions>
        <desktop3:Extension Category="windows.autoPlayHandler">
          <desktop3:AutoPlayHandler>
            <desktop3:InvokeAction ActionDisplayName="Import my files" ProviderDisplayName="ms-resource:AutoPlayDisplayName">
              <desktop3:Content ContentEvent="ShowPicturesOnArrival" Verb="show" DropTargetHandler="CD041BAE-0DEA-4472-9B7B-C98043D26EA8"/>
              <desktop3:Content ContentEvent="PlayVideoFilesOnArrival" Verb="play" Parameters="%1" />
              <desktop3:Device DeviceEvent="WPD\ImageSource" HWEventHandler="CD041BAE-0DEA-4472-9B7B-C98043D26EA8" InitCmdLine="/autoplay"/>
            </desktop3:InvokeAction>
          </desktop3:AutoPlayHandler>
      </Extensions>
    </Application>
  </Applications>
</Package>
```

<a id="updates" />

### <a name="restart-automatically-after-receiving-an-update-from-the-microsoft-store"></a><span data-ttu-id="b7e66-516">Starten Sie nach Erhalt eines Updates vom Microsoft Store automatisch neu</span><span class="sxs-lookup"><span data-stu-id="b7e66-516">Restart automatically after receiving an update from the Microsoft Store</span></span>

<span data-ttu-id="b7e66-517">Wenn Ihre Anwendung geöffnet ist, wenn Benutzer ein Update installieren, wird die Anwendung geschlossen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-517">If your application is open when users install an update to it, the application closes.</span></span>

<span data-ttu-id="b7e66-518">Wenn Sie möchten diese Anwendung neu starten, nachdem das Update abgeschlossen ist, rufen Sie die Funktion [RegisterApplicationRestart ist](https://msdn.microsoft.com/library/windows/desktop/aa373347.aspx) in jeder Prozess, der Sie neu starten möchten.</span><span class="sxs-lookup"><span data-stu-id="b7e66-518">If you want that application to restart after the update completes, call the  [RegisterApplicationRestart](https://msdn.microsoft.com/library/windows/desktop/aa373347.aspx) function in every process that you want to restart.</span></span>

<span data-ttu-id="b7e66-519">Jedes aktiven Fenster in Ihrer Anwendung erhält eine [WM_QUERYENDSESSION](https://msdn.microsoft.com/library/windows/desktop/aa376890.aspx) Nachricht.</span><span class="sxs-lookup"><span data-stu-id="b7e66-519">Each active window in your application receives a [WM_QUERYENDSESSION](https://msdn.microsoft.com/library/windows/desktop/aa376890.aspx) message.</span></span> <span data-ttu-id="b7e66-520">An diesem Punkt kann Ihre Anwendung die [RegisterApplicationRestart ist](https://msdn.microsoft.com/library/windows/desktop/aa373347.aspx) Funktion erneut aus, um die Befehlszeile bei Bedarf aktualisieren aufrufen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-520">At this point, your application can call the [RegisterApplicationRestart](https://msdn.microsoft.com/library/windows/desktop/aa373347.aspx) function again to update the command line if necessary.</span></span>

<span data-ttu-id="b7e66-521">Wenn jedes aktiven Fenster in Ihrer Anwendung die [WM_ENDSESSION](https://msdn.microsoft.com/library/windows/desktop/aa376889.aspx) Nachricht empfängt, sollte Ihre Anwendung Daten speichern und Herunterfahren.</span><span class="sxs-lookup"><span data-stu-id="b7e66-521">When each active window in your application receives the [WM_ENDSESSION](https://msdn.microsoft.com/library/windows/desktop/aa376889.aspx) message, your application should save data and shut down.</span></span>

>[!NOTE]
<span data-ttu-id="b7e66-522">Die aktiven Fenster auch Meldung die [WM_CLOSE](https://msdn.microsoft.com/library/windows/desktop/ms632617.aspx) für den Fall, dass die Anwendung die [WM_ENDSESSION](https://msdn.microsoft.com/library/windows/desktop/aa376889.aspx) Nachricht nicht behandelt.</span><span class="sxs-lookup"><span data-stu-id="b7e66-522">Your active windows also receive the [WM_CLOSE](https://msdn.microsoft.com/library/windows/desktop/ms632617.aspx) message in case the application doesn't handle the [WM_ENDSESSION](https://msdn.microsoft.com/library/windows/desktop/aa376889.aspx) message.</span></span>

<span data-ttu-id="b7e66-523">Zu diesem Zeitpunkt die Anwendung weist 30 Sekunden, um einen eigenen Prozesse zu schließen, oder die Plattform beendet diese erzwingen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-523">At this point, your application has 30 seconds to close it's own processes or the platform terminates them forcefully.</span></span>

<span data-ttu-id="b7e66-524">Nachdem das Update abgeschlossen ist, startet die Anwendung neu.</span><span class="sxs-lookup"><span data-stu-id="b7e66-524">After the update is complete, your application restarts.</span></span>

## <a name="work-with-other-applications"></a><span data-ttu-id="b7e66-525">Zusammenarbeit mit anderen Anwendungen</span><span class="sxs-lookup"><span data-stu-id="b7e66-525">Work with other applications</span></span>

<span data-ttu-id="b7e66-526">Mit anderen Apps integrieren, andere Prozesse starten oder Informationen freigeben.</span><span class="sxs-lookup"><span data-stu-id="b7e66-526">Integrate with other apps, start other processes or share information.</span></span>

* [<span data-ttu-id="b7e66-527">Die Anwendung als Druckerziel in Anwendungen, die unterstützen Drucken angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="b7e66-527">Make your application appear as the print target in applications that support printing</span></span>](#printing)
* [<span data-ttu-id="b7e66-528">Freigeben von Schriftarten für andere Windows-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="b7e66-528">Share fonts with other Windows applications</span></span>](#fonts)
* [<span data-ttu-id="b7e66-529">Starten Sie einen Win32-Prozess aus einer Universellen Windows-Plattform-App (UWP-App).</span><span class="sxs-lookup"><span data-stu-id="b7e66-529">Start a Win32 process from a Universal Windows Platform (UWP) app</span></span>](#win32-process)

<a id="printing" />

### <a name="make-your-application-appear-as-the-print-target-in-applications-that-support-printing"></a><span data-ttu-id="b7e66-530">Die Anwendung als Druckerziel in Anwendungen, die unterstützen Drucken angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="b7e66-530">Make your application appear as the print target in applications that support printing</span></span>

<span data-ttu-id="b7e66-531">Wenn Benutzer Daten aus einer anderen Anwendung wie z. B. Editor drucken möchten, können Sie Ihre Anwendung als Druckerziel in der app Liste der verfügbaren Druckerziele angezeigt werden lassen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-531">When users want to print data from another application such as Notepad, you can make your application appear as a print target in the app's list of available print targets.</span></span>

<span data-ttu-id="b7e66-532">Sie müssen Ihre Anwendung so anpassen, dass sie Daten im XML Paper Specification (XPS) Format empfängt.</span><span class="sxs-lookup"><span data-stu-id="b7e66-532">You'll have to modify your application so that it receives print data in XML Paper Specification (XPS) format.</span></span>

#### <a name="xml-namespaces"></a><span data-ttu-id="b7e66-533">XML-Namespaces</span><span class="sxs-lookup"><span data-stu-id="b7e66-533">XML namespaces</span></span>

http://schemas.microsoft.com/appx/manifest/desktop/windows10/2

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="b7e66-534">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b7e66-534">Elements and attributes of this extension</span></span>

```XML
<Extension Category="windows.appPrinter">
    <AppPrinter
        DisplayName="[DisplayName]"
        Parameters="[Parameters]" />
</Extension>
```

<span data-ttu-id="b7e66-535">Die vollständige Schemareferenz finden Sie [hier](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-desktop2-appprinter).</span><span class="sxs-lookup"><span data-stu-id="b7e66-535">Find the complete schema reference [here](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-desktop2-appprinter).</span></span>

|<span data-ttu-id="b7e66-536">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-536">Name</span></span> |<span data-ttu-id="b7e66-537">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b7e66-537">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="b7e66-538">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b7e66-538">Category</span></span> |<span data-ttu-id="b7e66-539">Immer ``windows.appPrinter``.</span><span class="sxs-lookup"><span data-stu-id="b7e66-539">Always ``windows.appPrinter``.</span></span>
|<span data-ttu-id="b7e66-540">DisplayName</span><span class="sxs-lookup"><span data-stu-id="b7e66-540">DisplayName</span></span> |<span data-ttu-id="b7e66-541">Der Name, der in der Liste der Druckerziele für eine App angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="b7e66-541">The name that you want to appear in the list of print targets for an app.</span></span> |
|<span data-ttu-id="b7e66-542">Parameter</span><span class="sxs-lookup"><span data-stu-id="b7e66-542">Parameters</span></span> |<span data-ttu-id="b7e66-543">Parameter, die Ihre Anwendung erfordert, um die Anforderung ordnungsgemäß zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="b7e66-543">Any parameters that your application requires to properly handle the request.</span></span> |

#### <a name="example"></a><span data-ttu-id="b7e66-544">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b7e66-544">Example</span></span>

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

<span data-ttu-id="b7e66-545">Suchen Sie [hier](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/PrintToPDF) ein Beispiel, in dem diese Erweiterung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b7e66-545">Find a sample that uses this extension [Here](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/tree/master/Samples/PrintToPDF)</span></span>

<a id="fonts" />

### <a name="share-fonts-with-other-windows-applications"></a><span data-ttu-id="b7e66-546">Freigeben von Schriftarten für andere Windows-Anwendungen</span><span class="sxs-lookup"><span data-stu-id="b7e66-546">Share fonts with other Windows applications</span></span>

<span data-ttu-id="b7e66-547">Teilen Sie Ihre benutzerdefinierten Schriftarten mit einer anderen Windows-Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-547">Share your custom fonts with other Windows applications.</span></span>

#### <a name="xml-namespaces"></a><span data-ttu-id="b7e66-548">XML-Namespaces</span><span class="sxs-lookup"><span data-stu-id="b7e66-548">XML namespaces</span></span>

http://schemas.microsoft.com/appx/manifest/desktop/windows10/2

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="b7e66-549">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b7e66-549">Elements and attributes of this extension</span></span>

```XML
<Extension Category="windows.sharedFonts">
    <SharedFonts>
      <Font File="[FontFile]" />
    </SharedFonts>
  </Extension>
```

<span data-ttu-id="b7e66-550">Die vollständige Schemareferenz finden Sie [hier](https://review.docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap4-sharedfonts).</span><span class="sxs-lookup"><span data-stu-id="b7e66-550">Find the complete schema reference [here](https://review.docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-uap4-sharedfonts).</span></span>

|<span data-ttu-id="b7e66-551">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-551">Name</span></span> |<span data-ttu-id="b7e66-552">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b7e66-552">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="b7e66-553">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b7e66-553">Category</span></span> |<span data-ttu-id="b7e66-554">Immer ``windows.sharedFonts``.</span><span class="sxs-lookup"><span data-stu-id="b7e66-554">Always ``windows.sharedFonts``.</span></span>
|<span data-ttu-id="b7e66-555">Datei</span><span class="sxs-lookup"><span data-stu-id="b7e66-555">File</span></span> |<span data-ttu-id="b7e66-556">Die Datei mit der Schriftart, die Sie teilen möchten.</span><span class="sxs-lookup"><span data-stu-id="b7e66-556">The file that contains the fonts that you want to share.</span></span> |

#### <a name="example"></a><span data-ttu-id="b7e66-557">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b7e66-557">Example</span></span>

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

<a id="win32-process" />

### <a name="start-a-win32-process-from-a-universal-windows-platform-uwp-app"></a><span data-ttu-id="b7e66-558">Starten Sie einen Win32-Prozess aus einer Universellen Windows-Plattform-App (UWP-App).</span><span class="sxs-lookup"><span data-stu-id="b7e66-558">Start a Win32 process from a Universal Windows Platform (UWP) app</span></span>

<span data-ttu-id="b7e66-559">Starten Sie einen vertrauenswürdigen Win32-Prozess.</span><span class="sxs-lookup"><span data-stu-id="b7e66-559">Start a Win32 process that runs in full-trust.</span></span>

#### <a name="xml-namespaces"></a><span data-ttu-id="b7e66-560">XML-Namespaces</span><span class="sxs-lookup"><span data-stu-id="b7e66-560">XML namespaces</span></span>

http://schemas.microsoft.com/appx/manifest/desktop/windows10

#### <a name="elements-and-attributes-of-this-extension"></a><span data-ttu-id="b7e66-561">Elemente und Attribute dieser Erweiterung</span><span class="sxs-lookup"><span data-stu-id="b7e66-561">Elements and attributes of this extension</span></span>

```XML
<Extension Category="windows.fullTrustProcess" Executable="[executable file]">
  <FullTrustProcess>
    <ParameterGroup GroupId="[GroupID]" Parameters="[Parameters]"/>
  </FullTrustProcess>
</Extension>
```

|<span data-ttu-id="b7e66-562">Name</span><span class="sxs-lookup"><span data-stu-id="b7e66-562">Name</span></span> |<span data-ttu-id="b7e66-563">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b7e66-563">Description</span></span> |
|-------|-------------|
|<span data-ttu-id="b7e66-564">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b7e66-564">Category</span></span> |<span data-ttu-id="b7e66-565">Immer ``windows.fullTrustProcess``.</span><span class="sxs-lookup"><span data-stu-id="b7e66-565">Always ``windows.fullTrustProcess``.</span></span>
|<span data-ttu-id="b7e66-566">Gruppen-ID</span><span class="sxs-lookup"><span data-stu-id="b7e66-566">GroupID</span></span> |<span data-ttu-id="b7e66-567">Eine Zeichenfolge, die eine Reihe von Parametern identifiziert, die an die ausführbare Datei übergeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-567">A string that identifies a set of parameters that you want to pass to the executable.</span></span> |
|<span data-ttu-id="b7e66-568">Parameter</span><span class="sxs-lookup"><span data-stu-id="b7e66-568">Parameters</span></span> |<span data-ttu-id="b7e66-569">Parameter, die an die ausführbare Datei übergeben werden sollen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-569">Parameters that you want to pass to the executable.</span></span> |

#### <a name="example"></a><span data-ttu-id="b7e66-570">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b7e66-570">Example</span></span>

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

<span data-ttu-id="b7e66-571">Diese Erweiterung kann hilfreich sein, wenn eine universelle Windows-Plattform-Benutzeroberfläche zu erstellen, die auf allen Geräten ausgeführt werden soll, aber Komponenten der Win32-Anwendung weiterhin in voller Vertrauenswürdigkeit ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="b7e66-571">This extension might be useful if you want to create a Universal Windows Platform User interface that runs on all devices, but you want components of your Win32 application to continue running in full-trust.</span></span>

<span data-ttu-id="b7e66-572">Erstellen Sie einfach ein Windows-app-Paket für Ihre Win32-app.</span><span class="sxs-lookup"><span data-stu-id="b7e66-572">Just create a Windows app package for your Win32 app.</span></span> <span data-ttu-id="b7e66-573">Fügen Sie dann der Paketdatei Ihrer UWP-App diese Erweiterung hinzu.</span><span class="sxs-lookup"><span data-stu-id="b7e66-573">Then, add this extension to the package file of your UWP app.</span></span> <span data-ttu-id="b7e66-574">Diese Erweiterungen gibt an, dass Sie eine ausführbare Datei in der Windows-app-Paket starten möchten.</span><span class="sxs-lookup"><span data-stu-id="b7e66-574">This extensions indicates that you want to start an executable file in the Windows app package.</span></span>  <span data-ttu-id="b7e66-575">Wenn Sie zwischen Ihrer UWP-App und Ihrer Win32-App kommunizieren möchten, können Sie einen oder mehrere [App-Dienste](../launch-resume/app-services.md) dafür festlegen.</span><span class="sxs-lookup"><span data-stu-id="b7e66-575">If you want to communicate between your UWP app and your Win32 app, you can set up one or more [app services](../launch-resume/app-services.md) to do that.</span></span> <span data-ttu-id="b7e66-576">Weitere Informationen zu diesem Szenario finden Sie [hier](https://blogs.msdn.microsoft.com/appconsult/2016/12/19/desktop-bridge-the-migrate-phase-invoking-a-win32-process-from-a-uwp-app/).</span><span class="sxs-lookup"><span data-stu-id="b7e66-576">You can read more about this scenario [here](https://blogs.msdn.microsoft.com/appconsult/2016/12/19/desktop-bridge-the-migrate-phase-invoking-a-win32-process-from-a-uwp-app/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="b7e66-577">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="b7e66-577">Next steps</span></span>

**<span data-ttu-id="b7e66-578">Finden Sie Antworten auf Ihre Fragen</span><span class="sxs-lookup"><span data-stu-id="b7e66-578">Find answers to your questions</span></span>**

<span data-ttu-id="b7e66-579">Haben Sie Fragen?</span><span class="sxs-lookup"><span data-stu-id="b7e66-579">Have questions?</span></span> <span data-ttu-id="b7e66-580">Fragen Sie uns auf Stack Overflow.</span><span class="sxs-lookup"><span data-stu-id="b7e66-580">Ask us on Stack Overflow.</span></span> <span data-ttu-id="b7e66-581">Unser Team überwacht diese [Tags](https://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span><span class="sxs-lookup"><span data-stu-id="b7e66-581">Our team monitors these [tags](https://stackoverflow.com/questions/tagged/project-centennial+or+desktop-bridge).</span></span> <span data-ttu-id="b7e66-582">Fragen Sie uns [hier](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span><span class="sxs-lookup"><span data-stu-id="b7e66-582">You can also ask us [here](https://social.msdn.microsoft.com/Forums/en-US/home?filter=alltypes&sort=relevancedesc&searchTerm=%5BDesktop%20Converter%5D).</span></span>

**<span data-ttu-id="b7e66-583">Geben Sie Feedback oder Verbesserungsvorschläge</span><span class="sxs-lookup"><span data-stu-id="b7e66-583">Give feedback or make feature suggestions</span></span>**

<span data-ttu-id="b7e66-584">Weitere Informationen finden Sie unter [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span><span class="sxs-lookup"><span data-stu-id="b7e66-584">See [UserVoice](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/161895-desktop-bridge-centennial).</span></span>
