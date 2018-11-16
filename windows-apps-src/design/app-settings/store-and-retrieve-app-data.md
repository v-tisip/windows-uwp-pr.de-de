---
author: mijacobs
Description: Learn how to store and retrieve local, roaming, and temporary app data.
title: Speichern und Abrufen von Einstellungen und anderen App-Daten
ms.assetid: 41676A02-325A-455E-8565-C9EC0BC3A8FE
label: App settings and data
template: detail.hbs
ms.author: mijacobs
ms.date: 11/14/2017
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 2af9aec9742a950f7bd35794ff4d10763e6c2c5c
ms.sourcegitcommit: e2fca6c79f31e521ba76f7ecf343cf8f278e6a15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "6995224"
---
# <a name="store-and-retrieve-settings-and-other-app-data"></a><span data-ttu-id="13833-103">Speichern und Abrufen von Einstellungen und anderen App-Daten</span><span class="sxs-lookup"><span data-stu-id="13833-103">Store and retrieve settings and other app data</span></span>

<span data-ttu-id="13833-104">*App-Daten* sind änderbare Daten, die für eine bestimmte App spezifisch sind.</span><span class="sxs-lookup"><span data-stu-id="13833-104">*App data* is mutable data that is specific to a particular app.</span></span> <span data-ttu-id="13833-105">Dazu zählen der Laufzeitstatus, die Benutzereinstellungen und weitere Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="13833-105">It includes runtime state, user preferences, and other settings.</span></span> <span data-ttu-id="13833-106">App-Daten unterscheiden sich von *Benutzerdaten*, Daten, die der Benutzer beim Verwenden einer App erstellt und verwaltet.</span><span class="sxs-lookup"><span data-stu-id="13833-106">App data is different from *user data*, data that the user creates and manages when using an app.</span></span> <span data-ttu-id="13833-107">Benutzerdaten umfassen Dokument- oder Mediendateien, E-Mail- oder Kommunikationstranskripte oder Datenbankeinträge, mit vom Benutzer erstellte Inhalte enthalten.</span><span class="sxs-lookup"><span data-stu-id="13833-107">User data includes document or media files, email or communication transcripts, or database records holding content created by the user.</span></span> <span data-ttu-id="13833-108">Benutzerdaten können für mehrere Apps nützlich oder von Bedeutung sein.</span><span class="sxs-lookup"><span data-stu-id="13833-108">User data may be useful or meaningful to more than one app.</span></span> <span data-ttu-id="13833-109">Häufig handelt es sich dabei um Daten, die der Benutzer als von der App unabhängige Entität ändern oder übertragen möchte (z.B. ein Dokument).</span><span class="sxs-lookup"><span data-stu-id="13833-109">Often, this is data that the user wants to manipulate or transmit as an entity independent of the app itself, such as a document.</span></span>

<span data-ttu-id="13833-110">\*\*Wichtiger Hinweis zu App-Daten: \*\*Die Lebensdauer der App-Daten ist an die Lebensdauer der App gebunden.</span><span class="sxs-lookup"><span data-stu-id="13833-110">**Important note about app data:** The lifetime of the app data is tied to the lifetime of the app.</span></span> <span data-ttu-id="13833-111">Wenn die App entfernt wird, gehen auch alle App-Daten verloren.</span><span class="sxs-lookup"><span data-stu-id="13833-111">If the app is removed, all of the app data will be lost as a consequence.</span></span> <span data-ttu-id="13833-112">Verwenden Sie App-Daten nicht zum Speichern von Benutzerdaten oder anderen Daten, die Benutzer als wertvoll und unersetzlich betrachten.</span><span class="sxs-lookup"><span data-stu-id="13833-112">Don't use app data to store user data or anything that users might perceive as valuable and irreplaceable.</span></span> <span data-ttu-id="13833-113">Solche Informationen sollten in den Bibliotheken des Benutzers und auf Microsoft OneDrive gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="13833-113">We recommend that the user's libraries and Microsoft OneDrive be used to store this sort of information.</span></span> <span data-ttu-id="13833-114">App-Daten eignen sich perfekt zum Speichern von App-spezifischen (Benutzer-)Einstellungen und Favoriten.</span><span class="sxs-lookup"><span data-stu-id="13833-114">App data is ideal for storing app-specific user preferences, settings, and favorites.</span></span>

## <a name="types-of-app-data"></a><span data-ttu-id="13833-115">App-Datentypen</span><span class="sxs-lookup"><span data-stu-id="13833-115">Types of app data</span></span>


<span data-ttu-id="13833-116">Es gibt zwei Arten von App-Daten: Einstellungen und Dateien.</span><span class="sxs-lookup"><span data-stu-id="13833-116">There are two types of app data: settings and files.</span></span>

-   **<span data-ttu-id="13833-117">Einstellungen</span><span class="sxs-lookup"><span data-stu-id="13833-117">Settings</span></span>**

    <span data-ttu-id="13833-118">Verwenden Sie die Einstellungen zum Speichern von Benutzereinstellungen und Anwendungsstatus-Informationen.</span><span class="sxs-lookup"><span data-stu-id="13833-118">Use settings to store user preferences and application state info.</span></span> <span data-ttu-id="13833-119">Mit der App-Daten-API können Sie ganz einfach Einstellungen erstellen und abrufen (später in diesem Artikel zeigen wir Ihnen einige Beispiele dazu).</span><span class="sxs-lookup"><span data-stu-id="13833-119">The app data API enables you to easily create and retrieve settings (we'll show you some examples later in this article).</span></span>

    <span data-ttu-id="13833-120">Im Folgenden finden Sie Datentypen, die Sie für App-Einstellungen verwenden können:</span><span class="sxs-lookup"><span data-stu-id="13833-120">Here are data types you can use for app settings:</span></span>

    -   <span data-ttu-id="13833-121">**UInt8**, **Int16**, **UInt16**, **Int32**, **UInt32**, **Int64**, **UInt64**, **Single**, **Double**</span><span class="sxs-lookup"><span data-stu-id="13833-121">**UInt8**, **Int16**, **UInt16**, **Int32**, **UInt32**, **Int64**, **UInt64**, **Single**, **Double**</span></span>
    -   **<span data-ttu-id="13833-122">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="13833-122">Boolean</span></span>**
    -   <span data-ttu-id="13833-123">**Char16**, **String**</span><span class="sxs-lookup"><span data-stu-id="13833-123">**Char16**, **String**</span></span>
    -   <span data-ttu-id="13833-124">[**DateTime**](https://msdn.microsoft.com/library/windows/apps/br206576), [**TimeSpan**](https://msdn.microsoft.com/library/windows/apps/br225996)</span><span class="sxs-lookup"><span data-stu-id="13833-124">[**DateTime**](https://msdn.microsoft.com/library/windows/apps/br206576), [**TimeSpan**](https://msdn.microsoft.com/library/windows/apps/br225996)</span></span>
    -   <span data-ttu-id="13833-125">**GUID**, [**Point**](https://msdn.microsoft.com/library/windows/apps/br225870), [**Size**](https://msdn.microsoft.com/library/windows/apps/br225995), [**Rect**](https://msdn.microsoft.com/library/windows/apps/br225994)</span><span class="sxs-lookup"><span data-stu-id="13833-125">**GUID**, [**Point**](https://msdn.microsoft.com/library/windows/apps/br225870), [**Size**](https://msdn.microsoft.com/library/windows/apps/br225995), [**Rect**](https://msdn.microsoft.com/library/windows/apps/br225994)</span></span>
    -   <span data-ttu-id="13833-126">[**ApplicationDataCompositeValue**](https://msdn.microsoft.com/library/windows/apps/br241588): eine Reihe von verwandten App-Einstellungen, die atomisch serialisiert und deserialisiert werden müssen.</span><span class="sxs-lookup"><span data-stu-id="13833-126">[**ApplicationDataCompositeValue**](https://msdn.microsoft.com/library/windows/apps/br241588): A set of related app settings that must be serialized and deserialized atomically.</span></span> <span data-ttu-id="13833-127">Verwenden Sie Verbundeinstellungen, um atomische Aktualisierungen voneinander abhängiger Einstellungen problemlos behandeln zu können.</span><span class="sxs-lookup"><span data-stu-id="13833-127">Use composite settings to easily handle atomic updates of interdependent settings.</span></span> <span data-ttu-id="13833-128">Das System stellt die Integrität von Verbundeinstellungen bei gleichzeitigem Zugriff und Roaming sicher.</span><span class="sxs-lookup"><span data-stu-id="13833-128">The system ensures the integrity of composite settings during concurrent access and roaming.</span></span> <span data-ttu-id="13833-129">Verbundeinstellungen sind für kleine Datenmengen vorgesehen. Bei Verwendung für große Datasets kann die Leistung beeinträchtigt werden.</span><span class="sxs-lookup"><span data-stu-id="13833-129">Composite settings are optimized for small amounts of data, and performance can be poor if you use them for large data sets.</span></span>
-   **<span data-ttu-id="13833-130">Dateien</span><span class="sxs-lookup"><span data-stu-id="13833-130">Files</span></span>**

    <span data-ttu-id="13833-131">Verwenden Sie Dateien zum Speichern von Binärdaten oder zum Aktivieren Ihrer eigenen, benutzerdefinierten, serialisierten Typen.</span><span class="sxs-lookup"><span data-stu-id="13833-131">Use files to store binary data or to enable your own, customized serialized types.</span></span>

## <a name="storing-app-data-in-the-app-data-stores"></a><span data-ttu-id="13833-132">Speichern von App-Daten in den App-Datenspeichern</span><span class="sxs-lookup"><span data-stu-id="13833-132">Storing app data in the app data stores</span></span>


<span data-ttu-id="13833-133">Bei der Installation einer App weist das System der App eigene, benutzerspezifische Datenspeicher für Einstellungen und Dateien zu.</span><span class="sxs-lookup"><span data-stu-id="13833-133">When an app is installed, the system gives it its own per-user data stores for settings and files.</span></span> <span data-ttu-id="13833-134">Sie müssen nicht wissen, wo und wie diese Daten vorhanden ist, da das System für die Verwaltung des physischen Speichers zuständig ist. Damit wird sichergestellt, dass die Daten von anderen Apps und anderen Benutzern isoliert gehalten werden.</span><span class="sxs-lookup"><span data-stu-id="13833-134">You don't need to know where or how this data exists, because the system is responsible for managing the physical storage, ensuring that the data is kept isolated from other apps and other users.</span></span> <span data-ttu-id="13833-135">Das System behält außerdem den Inhalt dieser Datenspeicher bei, wenn der Benutzer ein App-Update installiert, und entfernt den Inhalt dieser Datenspeicher vollständig und sauber, wenn die App deinstalliert wird.</span><span class="sxs-lookup"><span data-stu-id="13833-135">The system also preserves the contents of these data stores when the user installs an update to your app and removes the contents of these data stores completely and cleanly when your app is uninstalled.</span></span>

<span data-ttu-id="13833-136">Jede App verfügt in ihrem jeweiligen App-Datenspeicher über systemdefinierte Stammverzeichnisse: eines für lokale Dateien, eines für Roamingdateien und eines für temporäre Dateien.</span><span class="sxs-lookup"><span data-stu-id="13833-136">Within its app data store, each app has system-defined root directories: one for local files, one for roaming files, and one for temporary files.</span></span> <span data-ttu-id="13833-137">Ihre App kann den Stammverzeichnissen neue Dateien und Container hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="13833-137">Your app can add new files and new containers to each of these root directories.</span></span>

## <a name="local-app-data"></a><span data-ttu-id="13833-138">Lokale App-Daten</span><span class="sxs-lookup"><span data-stu-id="13833-138">Local app data</span></span>


<span data-ttu-id="13833-139">Lokale App-Daten sollten für alle Informationen verwendet werden, die zwischen App-Sitzungen beibehalten werden müssen und die nicht als App-Roamingdaten geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="13833-139">Local app data should be used for any information that needs to be preserved between app sessions and is not suitable for roaming app data.</span></span> <span data-ttu-id="13833-140">Daten, die auf anderen Geräten nicht verwendet werden können, sollten ebenfalls dort gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="13833-140">Data that is not applicable on other devices should be stored here as well.</span></span> <span data-ttu-id="13833-141">Es gibt keine allgemeinen Größenbeschränkungen für lokal gespeicherte Daten.</span><span class="sxs-lookup"><span data-stu-id="13833-141">There is no general size restriction on local data stored.</span></span> <span data-ttu-id="13833-142">Verwenden Sie den lokalen App-Datenspeicher für Daten, für die ein Roaming nicht sinnvoll ist, sowie für große Datasets.</span><span class="sxs-lookup"><span data-stu-id="13833-142">Use the local app data store for data that it does not make sense to roam and for large data sets.</span></span>

### <a name="retrieve-the-local-app-data-store"></a><span data-ttu-id="13833-143">Abrufen des lokalen App-Datenspeichers</span><span class="sxs-lookup"><span data-stu-id="13833-143">Retrieve the local app data store</span></span>

<span data-ttu-id="13833-144">Bevor Sie lokale App-Daten lesen oder schreiben können, müssen Sie den lokalen App-Datenspeicher abrufen.</span><span class="sxs-lookup"><span data-stu-id="13833-144">Before you can read or write local app data, you must retrieve the local app data store.</span></span> <span data-ttu-id="13833-145">Verwenden Sie zum Abrufen des lokalen App-Datenspeichers die [**ApplicationData.LocalSettings**](https://msdn.microsoft.com/library/windows/apps/br241622)-Eigenschaft, um die lokalen Einstellungen der App als [**ApplicationDataContainer**](https://msdn.microsoft.com/library/windows/apps/br241599)-Objekt abzurufen.</span><span class="sxs-lookup"><span data-stu-id="13833-145">To retrieve the local app data store, use the [**ApplicationData.LocalSettings**](https://msdn.microsoft.com/library/windows/apps/br241622) property to get the app's local settings as an [**ApplicationDataContainer**](https://msdn.microsoft.com/library/windows/apps/br241599) object.</span></span> <span data-ttu-id="13833-146">Verwenden Sie die [**ApplicationData.LocalFolder**](https://msdn.microsoft.com/library/windows/apps/br241621)-Eigenschaft, um die Dateien aus einem [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230)-Objekt abzurufen.</span><span class="sxs-lookup"><span data-stu-id="13833-146">Use the [**ApplicationData.LocalFolder**](https://msdn.microsoft.com/library/windows/apps/br241621) property to get the files in a [**StorageFolder**](https://msdn.microsoft.com/library/windows/apps/br227230) object.</span></span> <span data-ttu-id="13833-147">Verwenden Sie die [**ApplicationData.LocalCacheFolder**](https://msdn.microsoft.com/library/windows/apps/dn633825)-Eigenschaft, um den Ordner im lokalen App-Datenspeicher abzurufen, in dem Sie Dateien speichern können, die nicht in der Sicherung und Wiederherstellung enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="13833-147">Use the [**ApplicationData.LocalCacheFolder**](https://msdn.microsoft.com/library/windows/apps/dn633825) property to get the folder in the local app data store where you can save files that are not included in backup and restore.</span></span>

```CSharp
Windows.Storage.ApplicationDataContainer localSettings = 
    Windows.Storage.ApplicationData.Current.LocalSettings;
Windows.Storage.StorageFolder localFolder = 
    Windows.Storage.ApplicationData.Current.LocalFolder;
```

### <a name="create-and-retrieve-a-simple-local-setting"></a><span data-ttu-id="13833-148">Erstellen und Abrufen einer einfachen lokalen Einstellung</span><span class="sxs-lookup"><span data-stu-id="13833-148">Create and retrieve a simple local setting</span></span>

<span data-ttu-id="13833-149">Um eine Einstellung zu erstellen oder zu schreiben, verwenden Sie die [**ApplicationDataContainer.Values**](https://msdn.microsoft.com/library/windows/apps/br241615)-Eigenschaft, um auf die Einstellungen im `localSettings`-Container zuzugreifen, den wir im vorherigen Schritt abgerufen haben.</span><span class="sxs-lookup"><span data-stu-id="13833-149">To create or write a setting, use the [**ApplicationDataContainer.Values**](https://msdn.microsoft.com/library/windows/apps/br241615) property to access the settings in the `localSettings` container we got in the previous step.</span></span> <span data-ttu-id="13833-150">In diesem Beispiel wird eine Einstellung namens `exampleSetting` erstellt.</span><span class="sxs-lookup"><span data-stu-id="13833-150">This example creates a setting named `exampleSetting`.</span></span>

```CSharp
// Simple setting

localSettings.Values["exampleSetting"] = "Hello Windows";
```

<span data-ttu-id="13833-151">Um die Einstellung abzurufen, verwenden Sie dieselbe [**ApplicationDataContainer.Values**](https://msdn.microsoft.com/library/windows/apps/br241615)-Eigenschaft, mit der Sie die Einstellung erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="13833-151">To retrieve the setting, you use the same [**ApplicationDataContainer.Values**](https://msdn.microsoft.com/library/windows/apps/br241615) property that you used to create the setting.</span></span> <span data-ttu-id="13833-152">Dieses Beispiel zeigt, wie Sie die gerade erstellte Einstellung abrufen können.</span><span class="sxs-lookup"><span data-stu-id="13833-152">This example shows how to retrieve the setting we just created.</span></span>

```CSharp
// Simple setting
Object value = localSettings.Values["exampleSetting"];
```

### <a name="create-and-retrieve-a-local-composite-value"></a><span data-ttu-id="13833-153">Erstellen und Abrufen eines lokalen zusammengesetzten Werts</span><span class="sxs-lookup"><span data-stu-id="13833-153">Create and retrieve a local composite value</span></span>

<span data-ttu-id="13833-154">Erstellen Sie zum Erstellen oder Schreiben eines zusammengesetzten Werts ein [**ApplicationDataCompositeValue**](https://msdn.microsoft.com/library/windows/apps/br241588)-Objekt.</span><span class="sxs-lookup"><span data-stu-id="13833-154">To create or write a composite value, create an [**ApplicationDataCompositeValue**](https://msdn.microsoft.com/library/windows/apps/br241588) object.</span></span> <span data-ttu-id="13833-155">In diesem Beispiel wird eine Verbundeinstellung namens `exampleCompositeSetting` erstellt und dem Container `localSettings` hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="13833-155">This example creates a composite setting named `exampleCompositeSetting` and adds it to the `localSettings` container.</span></span>

```CSharp
// Composite setting

Windows.Storage.ApplicationDataCompositeValue composite = 
    new Windows.Storage.ApplicationDataCompositeValue();
composite["intVal"] = 1;
composite["strVal"] = "string";

localSettings.Values["exampleCompositeSetting"] = composite;
```

<span data-ttu-id="13833-156">In diesem Beispiel wird veranschaulicht, wie der gerade erstellte, zusammengesetzte Wert abgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="13833-156">This example shows how to retrieve the composite value we just created.</span></span>

```CSharp
// Composite setting

Windows.Storage.ApplicationDataCompositeValue composite = 
   (Windows.Storage.ApplicationDataCompositeValue)localSettings.Values["exampleCompositeSetting"];

if (composite == null)
{
   // No data
}
else
{
   // Access data in composite["intVal"] and composite["strVal"]
}
```

### <a name="create-and-read-a-local-file"></a><span data-ttu-id="13833-157">Erstellen und Lesen einer lokalen Datei</span><span class="sxs-lookup"><span data-stu-id="13833-157">Create and read a local file</span></span>

<span data-ttu-id="13833-158">Verwenden Sie die Datei-APIs (z.B. [**Windows.Storage.StorageFolder.CreateFileAsync**](https://msdn.microsoft.com/library/windows/apps/br227249) und [**Windows.Storage.FileIO.WriteTextAsync**](https://msdn.microsoft.com/library/windows/apps/hh701505)), um eine Datei im lokalen App-Datenspeicher zu erstellen und zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="13833-158">To create and update a file in the local app data store, use the file APIs, such as [**Windows.Storage.StorageFolder.CreateFileAsync**](https://msdn.microsoft.com/library/windows/apps/br227249) and [**Windows.Storage.FileIO.WriteTextAsync**](https://msdn.microsoft.com/library/windows/apps/hh701505).</span></span> <span data-ttu-id="13833-159">In diesem Beispiel wird im Container `localFolder` die Datei `dataFile.txt` erstellt, in die das aktuelle Datum und die Uhrzeit geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="13833-159">This example creates a file named `dataFile.txt` in the `localFolder` container and writes the current date and time to the file.</span></span> <span data-ttu-id="13833-160">Der Wert **ReplaceExisting** aus der [**CreationCollisionOption**](https://msdn.microsoft.com/library/windows/apps/br241631)-Enumeration gibt an, dass die Datei ersetzt werden soll, falls sie bereits vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="13833-160">The **ReplaceExisting** value from the [**CreationCollisionOption**](https://msdn.microsoft.com/library/windows/apps/br241631) enumeration indicates to replace the file if it already exists.</span></span>

```csharp
async void WriteTimestamp()
{
   Windows.Globalization.DateTimeFormatting.DateTimeFormatter formatter = 
       new Windows.Globalization.DateTimeFormatting.DateTimeFormatter("longtime");

   StorageFile sampleFile = await localFolder.CreateFileAsync("dataFile.txt", 
       CreationCollisionOption.ReplaceExisting);
   await FileIO.WriteTextAsync(sampleFile, formatter.Format(DateTimeOffset.Now));
}
```

<span data-ttu-id="13833-161">Verwenden Sie die Datei-APIs (z.B. [**Windows.Storage.StorageFolder.GetFileAsync**](https://msdn.microsoft.com/library/windows/apps/br227272), [**Windows.Storage.StorageFile.GetFileFromApplicationUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701741) und [**Windows.Storage.FileIO.ReadTextAsync**](https://msdn.microsoft.com/library/windows/apps/hh701482)), um eine Datei im lokalen App-Datenspeicher zu öffnen und zu lesen.</span><span class="sxs-lookup"><span data-stu-id="13833-161">To open and read a file in the local app data store, use the file APIs, such as [**Windows.Storage.StorageFolder.GetFileAsync**](https://msdn.microsoft.com/library/windows/apps/br227272), [**Windows.Storage.StorageFile.GetFileFromApplicationUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701741), and [**Windows.Storage.FileIO.ReadTextAsync**](https://msdn.microsoft.com/library/windows/apps/hh701482).</span></span> <span data-ttu-id="13833-162">In diesem Beispiel wird die im vorherigen Schritt erstellte Datei `dataFile.txt` geöffnet und das Datum aus der Datei gelesen.</span><span class="sxs-lookup"><span data-stu-id="13833-162">This example opens the `dataFile.txt` file created in the previous step and reads the date from the file.</span></span> <span data-ttu-id="13833-163">Einzelheiten zum Laden von Dateiressourcen aus verschiedenen Speicherorten finden Sie unter [So wird's gemacht: Laden von Dateiressourcen](https://msdn.microsoft.com/library/windows/apps/xaml/hh965322).</span><span class="sxs-lookup"><span data-stu-id="13833-163">For details on loading file resources from various locations, see [How to load file resources](https://msdn.microsoft.com/library/windows/apps/xaml/hh965322).</span></span>

```csharp
async void ReadTimestamp()
{
   try
   {
      StorageFile sampleFile = await localFolder.GetFileAsync("dataFile.txt");
      String timestamp = await FileIO.ReadTextAsync(sampleFile);
      // Data is contained in timestamp
   }
   catch (Exception)
   {
      // Timestamp not found
   }
}
```

## <a name="roaming-data"></a><span data-ttu-id="13833-164">Roamingdaten</span><span class="sxs-lookup"><span data-stu-id="13833-164">Roaming data</span></span>


<span data-ttu-id="13833-165">Wenn Sie Roamingdaten in Ihrer App verwenden, können Benutzer die App-Daten der App problemlos für mehrere Geräte synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="13833-165">If you use roaming data in your app, your users can easily keep your app's app data in sync across multiple devices.</span></span> <span data-ttu-id="13833-166">Installiert ein Benutzer eine App auf mehreren Geräten, sorgt das Betriebssystem dafür, dass die App-Daten synchronisiert sind, und verringert so den Einrichtungsaufwand für die App auf weiteren Geräten.</span><span class="sxs-lookup"><span data-stu-id="13833-166">If a user installs your app on multiple devices, the OS keeps the app data in sync, reducing the amount of setup work that the user needs to do for your app on their second device.</span></span> <span data-ttu-id="13833-167">Mittels Roaming können Benutzer außerdem eine Aufgabe (beispielsweise das Erstellen einer Liste) an genau dem Punkt fortsetzen, an dem sie die Aufgabe auf einem anderen Gerät unterbrochen haben.</span><span class="sxs-lookup"><span data-stu-id="13833-167">Roaming also enables your users to continue a task, such as composing a list, right where they left off even on a different device.</span></span> <span data-ttu-id="13833-168">Das Betriebssystem repliziert aktualisierte Roamingdaten in der Cloud und synchronisiert die Daten mit den anderen Geräten, auf denen die App installiert ist.</span><span class="sxs-lookup"><span data-stu-id="13833-168">The OS replicates roaming data to the cloud when it is updated, and synchronizes the data to the other devices on which the app is installed.</span></span>

<span data-ttu-id="13833-169">Das Betriebssystem begrenzt für jede App die Menge der App-Daten für das Roaming.</span><span class="sxs-lookup"><span data-stu-id="13833-169">The OS limits the size of the app data that each app may roam.</span></span> <span data-ttu-id="13833-170">Siehe [**ApplicationData.RoamingStorageQuota**](https://msdn.microsoft.com/library/windows/apps/br241625).</span><span class="sxs-lookup"><span data-stu-id="13833-170">See [**ApplicationData.RoamingStorageQuota**](https://msdn.microsoft.com/library/windows/apps/br241625).</span></span> <span data-ttu-id="13833-171">Erreicht die App diese Grenze, werden keine App-Daten der App mehr in die Cloud repliziert, bis die Gesamtmenge der App-Roamingdaten wieder unter dem Grenzwert liegt.</span><span class="sxs-lookup"><span data-stu-id="13833-171">If the app hits this limit, none of the app's app data will be replicated to the cloud until the app's total roamed app data is less than the limit again.</span></span> <span data-ttu-id="13833-172">Aus diesem Grund ist es empfehlenswert, Roamingdaten nur für Benutzereinstellungen, Links und kleine Datendateien zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="13833-172">For this reason, it is a best practice to use roaming data only for user preferences, links, and small data files.</span></span>

<span data-ttu-id="13833-173">Roamingdaten für Apps sind in der Cloud verfügbar, solange der Benutzer innerhalb des erforderlichen Zeitintervalls mit einem Gerät darauf zugreift.</span><span class="sxs-lookup"><span data-stu-id="13833-173">Roaming data for an app is available in the cloud as long as it is accessed by the user from some device within the required time interval.</span></span> <span data-ttu-id="13833-174">Führt ein Benutzer eine App für eine dieses Zeitintervall nicht überschreitende Spanne aus, werden die Roamingdaten aus der Cloud gelöscht.</span><span class="sxs-lookup"><span data-stu-id="13833-174">If the user does not run an app for longer than this time interval, its roaming data is removed from the cloud.</span></span> <span data-ttu-id="13833-175">Bei der Deinstallation einer App werden die entsprechenden Roamingdaten in der Cloud nicht automatisch gelöscht, sondern beibehalten.</span><span class="sxs-lookup"><span data-stu-id="13833-175">If a user uninstalls an app, its roaming data isn't automatically removed from the cloud, it's preserved.</span></span> <span data-ttu-id="13833-176">Installiert der Benutzer die App innerhalb des Zeitintervalls wieder, werden die Roamingdaten über die Cloud synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="13833-176">If the user reinstalls the app within the time interval, the roaming data is synchronized from the cloud.</span></span>

### <a name="roaming-data-dos-and-donts"></a><span data-ttu-id="13833-177">Empfohlene und nicht empfohlene Vorgehensweisen für Roamingdaten</span><span class="sxs-lookup"><span data-stu-id="13833-177">Roaming data do's and don'ts</span></span>

-   <span data-ttu-id="13833-178">Verwenden Sie Roaming für Benutzereinstellungen und -anpassungen, Links und kleine Datendateien.</span><span class="sxs-lookup"><span data-stu-id="13833-178">Use roaming for user preferences and customizations, links, and small data files.</span></span> <span data-ttu-id="13833-179">Sie können mithilfe von Roaming beispielsweise dafür sorgen, dass die vom Benutzer vorgenommene Einstellung für die Hintergrundfarbe auf allen Geräten angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="13833-179">For example, use roaming to preserve a user's background color preference across all devices.</span></span>
-   <span data-ttu-id="13833-180">Verwenden Sie Roaming, damit Benutzer eine Aufgabe auf mehreren Geräten fortsetzen können.</span><span class="sxs-lookup"><span data-stu-id="13833-180">Use roaming to let users continue a task across devices.</span></span> <span data-ttu-id="13833-181">Sie können das Roaming für Anwendungsdaten beispielsweise implementieren, um den Inhalt eines E-Mail-Entwurfs oder die zuletzt angezeigte Seite in einer Lese-App zu speichern.</span><span class="sxs-lookup"><span data-stu-id="13833-181">For example, roam app data like the contents of an drafted email or the most recently viewed page in a reader app.</span></span>
-   <span data-ttu-id="13833-182">Behandeln Sie das [**DataChanged**](https://msdn.microsoft.com/library/windows/apps/br241620)-Ereignis, indem Sie App-Daten aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="13833-182">Handle the [**DataChanged**](https://msdn.microsoft.com/library/windows/apps/br241620) event by updating app data.</span></span> <span data-ttu-id="13833-183">Dieses Ereignis tritt unmittelbar nach der Synchronisierung der App-Daten mit der Cloud auf.</span><span class="sxs-lookup"><span data-stu-id="13833-183">This event occurs when app data has just finished syncing from the cloud.</span></span>
-   <span data-ttu-id="13833-184">Führen Sie Roaming für Verweise auf Inhalte durch, anstelle für unformatierte Daten.</span><span class="sxs-lookup"><span data-stu-id="13833-184">Roam references to content rather than raw data.</span></span> <span data-ttu-id="13833-185">Das Roaming für eine URL eines Onlineartikel ist beispielsweise sinnvoller als das Roaming für den Inhalt des Artikels.</span><span class="sxs-lookup"><span data-stu-id="13833-185">For example, roam a URL rather than the content of an online article.</span></span>
-   <span data-ttu-id="13833-186">Verwenden Sie für wichtige, zeitkritische Informationen die Einstellung *HighPriority* zusammen mit [**RoamingSettings**](https://msdn.microsoft.com/library/windows/apps/br241624).</span><span class="sxs-lookup"><span data-stu-id="13833-186">For important, time critical settings, use the *HighPriority* setting associated with [**RoamingSettings**](https://msdn.microsoft.com/library/windows/apps/br241624).</span></span>
-   <span data-ttu-id="13833-187">Führen Sie kein Roaming für gerätespezifische App-Daten durch.</span><span class="sxs-lookup"><span data-stu-id="13833-187">Don't roam app data that is specific to a device.</span></span> <span data-ttu-id="13833-188">Manche dieser Informationen sind ausschließlich lokal relevant, wie beispielsweise der Pfadname zu einer lokalen Dateiressource.</span><span class="sxs-lookup"><span data-stu-id="13833-188">Some info is only pertinent locally, such as a path name to a local file resource.</span></span> <span data-ttu-id="13833-189">Wenn Sie lokale Informationen als Roamingdaten verwenden möchten, stellen Sie sicher, dass die App wiederhergestellt werden kann, wenn die Informationen auf dem zweiten Gerät nicht gültig sind.</span><span class="sxs-lookup"><span data-stu-id="13833-189">If you do decide to roam local information, make sure that the app can recover if the info isn't valid on the secondary device.</span></span>
-   <span data-ttu-id="13833-190">Führen Sie kein Roaming für große App-Datenmengen durch.</span><span class="sxs-lookup"><span data-stu-id="13833-190">Don't roam large sets of app data.</span></span> <span data-ttu-id="13833-191">Die Menge der App-Daten für das Roaming ist begrenzt. Verwenden Sie die Eigenschaft [**RoamingStorageQuota**](https://msdn.microsoft.com/library/windows/apps/br241625), um diese maximale Datenmenge zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="13833-191">There's a limit to the amount of app data an app may roam; use [**RoamingStorageQuota**](https://msdn.microsoft.com/library/windows/apps/br241625) property to get this maximum.</span></span> <span data-ttu-id="13833-192">Wenn eine App diese Grenze erreicht, wird so lange kein Datenroaming durchgeführt, bis die Größe des App-Datenspeichers wieder unter die Grenze fällt.</span><span class="sxs-lookup"><span data-stu-id="13833-192">If an app hits this limit, no data can roam until the size of the app data store no longer exceeds the limit.</span></span> <span data-ttu-id="13833-193">Berücksichtigen Sie beim App-Design, wie eine Grenze für größere Datenmengen festgelegt wird, sodass die Begrenzung nicht überschritten wird.</span><span class="sxs-lookup"><span data-stu-id="13833-193">When you design your app, consider how to put a bound on larger data so as to not exceed the limit.</span></span> <span data-ttu-id="13833-194">Wenn für das Speichern eines Spielstands beispielsweise jeweils 10KB erforderlich sind, sollte die App unter Umständen höchstens zulassen, dass 10 Spielstände gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="13833-194">For example, if saving a game state requires 10KB each, the app might only allow the user store up to 10 games.</span></span>
-   <span data-ttu-id="13833-195">Verwenden Sie Roaming nicht für Daten, die von einer sofortigen Synchronisierung abhängig sind.</span><span class="sxs-lookup"><span data-stu-id="13833-195">Don't use roaming for data that relies on instant syncing.</span></span> <span data-ttu-id="13833-196">Windows garantiert keine sofortige Synchronisierung; die Synchronisierung kann erheblich verzögert werden, wenn Benutzer offline oder mit einem Netzwerk mit hoher Latenz verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="13833-196">Windows doesn't guarantee an instant sync; roaming could be significantly delayed if a user is offline or on a high latency network.</span></span> <span data-ttu-id="13833-197">Stellen Sie sicher, dass die UI nicht von einer sofortigen Synchronisierung abhängig ist.</span><span class="sxs-lookup"><span data-stu-id="13833-197">Ensure that your UI doesn't depend on instant syncing.</span></span>
-   <span data-ttu-id="13833-198">Verwenden Sie roaming nicht für häufig ändernde Daten.</span><span class="sxs-lookup"><span data-stu-id="13833-198">Don't use roaming for frequently changing data.</span></span> <span data-ttu-id="13833-199">Wenn Ihre App beispielsweise Informationen nachverfolgt, die sich häufig ändern (z.B. die Position eines Musiktitels in Sekunden), speichern Sie diese Daten nicht als Roaming-App-Daten.</span><span class="sxs-lookup"><span data-stu-id="13833-199">For example, if your app tracks frequently changing info, such as the position in a song by second, don't store this as roaming app data.</span></span> <span data-ttu-id="13833-200">Wählen Sie stattdessen eine weniger häufige angepasste Darstellung, die trotzdem eine gute Benutzererfahrung gewährleistet, z. B. den aktuell wiedergegebenen Titel.</span><span class="sxs-lookup"><span data-stu-id="13833-200">Instead, pick a less frequent representation that still provides a good user experience, like the currently playing song.</span></span>

### <a name="roaming-pre-requisites"></a><span data-ttu-id="13833-201">Voraussetzungen für Roaming</span><span class="sxs-lookup"><span data-stu-id="13833-201">Roaming pre-requisites</span></span>

<span data-ttu-id="13833-202">Jeder Benutzer kann von Roaming-App-Daten profitieren, wenn ein Microsoft-Konto zur Anmeldung am Gerät verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="13833-202">Any user can benefit from roaming app data if they use a Microsoft account to log on to their device.</span></span> <span data-ttu-id="13833-203">Benutzer und Gruppenrichtlinienadministratoren haben jedoch die Möglichkeit, das Roaming von App-Daten auf einem Gerät zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="13833-203">However, users and group policy administrators can switch off roaming app data on a device at any time.</span></span> <span data-ttu-id="13833-204">Benutzer, die kein Microsoft-Konto verwenden oder die Datenroamingfunktion deaktivieren, können Ihre App auch weiterhin verwenden, die App-Daten sind dann jedoch auf jedem Gerät lokal vorhanden.</span><span class="sxs-lookup"><span data-stu-id="13833-204">If a user chooses not to use a Microsoft account or disables roaming data capabilities, she will still be able to use your app, but app data be local to each device.</span></span>

<span data-ttu-id="13833-205">Daten, die im [**PasswordVault**](https://msdn.microsoft.com/library/windows/apps/br227081) gespeichert sind, werden nur übertragen, wenn ein Benutzer ein Gerät als "vertrauenswürdig" eingestuft hat.</span><span class="sxs-lookup"><span data-stu-id="13833-205">Data stored in the [**PasswordVault**](https://msdn.microsoft.com/library/windows/apps/br227081) will only transition if a user has made a device “trusted”.</span></span> <span data-ttu-id="13833-206">Wird einem Gerät nicht vertraut, werden die in diesem Tresor gespeicherten Daten nicht für das Roaming verwendet.</span><span class="sxs-lookup"><span data-stu-id="13833-206">If a device isn't trusted, data secured in this vault will not roam.</span></span>

### <a name="conflict-resolution"></a><span data-ttu-id="13833-207">Konfliktlösung</span><span class="sxs-lookup"><span data-stu-id="13833-207">Conflict resolution</span></span>

<span data-ttu-id="13833-208">Das Roaming von App-Daten ist nicht für eine gleichzeitige Verwendung auf mehreren Geräten vorgesehen</span><span class="sxs-lookup"><span data-stu-id="13833-208">Roaming app data is not intended for simultaneous use on more than one device at a time.</span></span> <span data-ttu-id="13833-209">Wenn es während der Synchronisierung zu einem Konflikt kommt, weil eine bestimmte Dateneinheit auf beiden Geräten geändert wurde, verwendet das System vorzugsweise immer den zuletzt geschriebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="13833-209">If a conflict arises during synchronization because a particular data unit was changed on two devices, the system will always favor the value that was written last.</span></span> <span data-ttu-id="13833-210">Dadurch wird sichergestellt, dass der App immer die aktuellsten Informationen zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="13833-210">This ensures that the app utilizes the most up-to-date information.</span></span> <span data-ttu-id="13833-211">Handelt es sich bei der Dateneinheit um eine zusammengesetzte Einstellung, findet die Konfliktlösung trotzdem auf der Ebene der Einstellungseinheit statt, d.h. der zuletzt geänderte Wert der Zusammensetzung wird synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="13833-211">If the data unit is a setting composite, conflict resolution will still occur on the level of the setting unit, which means that the composite with the latest change will be synchronized.</span></span>

### <a name="when-to-write-data"></a><span data-ttu-id="13833-212">Zeitpunkt für das Schreiben von Daten</span><span class="sxs-lookup"><span data-stu-id="13833-212">When to write data</span></span>

<span data-ttu-id="13833-213">Je nach erwarteter Lebensdauer der Einstellung sollten Daten zu unterschiedlichen Zeitpunkten geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="13833-213">Depending on the expected lifetime of the setting, data should be written at different times.</span></span> <span data-ttu-id="13833-214">Selten bzw. langsam geänderte App-Daten sollten sofort geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="13833-214">Infrequently or slowly changing app data should be written immediately.</span></span> <span data-ttu-id="13833-215">Häufig geänderte App-Daten sollten dagegen nur in bestimmten Zeiträumen regelmäßig (beispielsweise einmal alle fünf Minuten) und bei angehaltener App geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="13833-215">However, app data that changes frequently should only be written periodically at regular intervals (such as once every 5 minutes), as well as when the app is suspended.</span></span> <span data-ttu-id="13833-216">So kann eine Musik-App beispielsweise die Einstellung für den aktuellen Titel schreiben, wenn ein neuer Titel wiedergegeben wird, aber die aktuelle Position im Titel sollte nur in angehaltenem Zustand der Anwendung geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="13833-216">For example, a music app might write the “current song” settings whenever a new song starts to play, however, the actual position in the song should only be written on suspend.</span></span>

### <a name="excessive-usage-protection"></a><span data-ttu-id="13833-217">Schutz vor übermäßiger Nutzung</span><span class="sxs-lookup"><span data-stu-id="13833-217">Excessive usage protection</span></span>

<span data-ttu-id="13833-218">Das System verfügt über verschiedene Schutzmechanismen, um unangemessene Verwendung der Ressourcen zu verhindern.</span><span class="sxs-lookup"><span data-stu-id="13833-218">The system has various protection mechanisms in place to avoid inappropriate use of resources.</span></span> <span data-ttu-id="13833-219">Falls App-Daten nicht wie erwartet übertragen werden, wurde das Gerät wahrscheinlich vorübergehend beschränkt.</span><span class="sxs-lookup"><span data-stu-id="13833-219">If app data does not transition as expected, it is likely that the device has been temporarily restricted.</span></span> <span data-ttu-id="13833-220">Wenn Sie einige Zeit warten, wird dieses Problem normalerweise automatisch behoben, ohne dass eine Aktion erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="13833-220">Waiting for some time will usually resolve this situation automatically and no action is required.</span></span>

### <a name="versioning"></a><span data-ttu-id="13833-221">Versionsverwaltung</span><span class="sxs-lookup"><span data-stu-id="13833-221">Versioning</span></span>

<span data-ttu-id="13833-222">App-Daten können die Versionsinformationen nutzen, um von einer Datenstruktur auf eine andere zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="13833-222">App data can utilize versioning to upgrade from one data structure to another.</span></span> <span data-ttu-id="13833-223">Die Versionsnummer unterscheidet sich von der App-Version und kann nach Belieben festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="13833-223">The version number is different from the app version and can be set at will.</span></span> <span data-ttu-id="13833-224">Auch wenn es nicht zwingend erforderlich ist, empfiehlt es sich, aufsteigende Versionsnummern zu verwenden, da beim Übergang zu einer kleineren Nummer, die neuere Daten darstellt, unerwünschte Komplikationen (z.B. Datenverluste) entstehen können.</span><span class="sxs-lookup"><span data-stu-id="13833-224">Although not enforced, it is highly recommended that you use increasing version numbers, since undesirable complications (including data loss)could occur if you try to transition to a lower data version number that represents newer data.</span></span>

<span data-ttu-id="13833-225">Das Roaming für App-Daten wird nur in installierten Apps mit der gleichen Versionsnummer durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="13833-225">App data only roams between installed apps with the same version number.</span></span> <span data-ttu-id="13833-226">Beispiel: Geräte mit der Versionsnummer2 tauschen Daten untereinander aus. Gleiches gilt für Geräte mit der Version3. Es erfolgt jedoch kein Roaming zwischen Geräten mit Version2 und Geräten mit Version3.</span><span class="sxs-lookup"><span data-stu-id="13833-226">For example, devices on version 2 will transition data between each other and devices on version 3 will do the same, but no roaming will occur between a device running version 2 and a device running version 3.</span></span> <span data-ttu-id="13833-227">Wenn Sie eine neue App installieren, die auf anderen Geräten unterschiedliche Versionsnummern verwendet hat, synchronisiert die neu installierte App die App-Daten, die mit der höchsten Versionsnummer verknüpft sind.</span><span class="sxs-lookup"><span data-stu-id="13833-227">If you install a new app that utilized various version numbers on other devices, the newly installed app will sync the app data associated with the highest version number.</span></span>

### <a name="testing-and-tools"></a><span data-ttu-id="13833-228">Tests und Tools</span><span class="sxs-lookup"><span data-stu-id="13833-228">Testing and tools</span></span>

<span data-ttu-id="13833-229">Entwickler können ihr Gerät sperren, um eine Synchronisierung von Roaming-App-Daten auszulösen.</span><span class="sxs-lookup"><span data-stu-id="13833-229">Developers can lock their device in order to trigger a synchronization of roaming app data.</span></span> <span data-ttu-id="13833-230">Wenn die App-Daten scheinbar nicht innerhalb eines bestimmten Zeitrahmens übertragen werden, überprüfen Sie die folgenden Elemente, und stellen Sie sicher, dass:</span><span class="sxs-lookup"><span data-stu-id="13833-230">If it seems that the app data does not transition within a certain time frame, please check the following items and make sure that:</span></span>

-   <span data-ttu-id="13833-231">Ihre Roamingdaten nicht die maximal zulässige Größe überschreiten (siehe auch [**RoamingStorageQuota**](https://msdn.microsoft.com/library/windows/apps/br241625)).</span><span class="sxs-lookup"><span data-stu-id="13833-231">Your roaming data does not exceed the maximum size (see [**RoamingStorageQuota**](https://msdn.microsoft.com/library/windows/apps/br241625) for details).</span></span>
-   <span data-ttu-id="13833-232">Ihre Dateien geschlossen und ordnungsgemäß veröffentlicht wurden.</span><span class="sxs-lookup"><span data-stu-id="13833-232">Your files are closed and released properly.</span></span>
-   <span data-ttu-id="13833-233">Sie über mindestens zwei Geräte mit derselben App-Version verfügen.</span><span class="sxs-lookup"><span data-stu-id="13833-233">There are at least two devices running the same version of the app.</span></span>


### <a name="register-to-receive-notification-when-roaming-data-changes"></a><span data-ttu-id="13833-234">Registrieren, um Benachrichtigungen bei der Änderung von Roamingdaten zu erhalten</span><span class="sxs-lookup"><span data-stu-id="13833-234">Register to receive notification when roaming data changes</span></span>

<span data-ttu-id="13833-235">Um das Roaming von App-Daten verwenden zu können, müssen Sie die Roamingdatenänderungen registrieren und die Roamingdatencontainer abrufen, damit Sie Einstellungen lesen und schreiben können.</span><span class="sxs-lookup"><span data-stu-id="13833-235">To use roaming app data, you need to register for roaming data changes and retrieve the roaming data containers so you can read and write settings.</span></span>

1.  <span data-ttu-id="13833-236">Nehmen Sie eine Registrierung für den Empfang einer Benachrichtigung vor, wenn sich Roamingdaten ändern.</span><span class="sxs-lookup"><span data-stu-id="13833-236">Register to receive notification when roaming data changes.</span></span>

    <span data-ttu-id="13833-237">Das [**DataChanged**](https://msdn.microsoft.com/library/windows/apps/br241620)-Ereignis benachrichtigt Sie, wenn sich Roamingdaten ändern.</span><span class="sxs-lookup"><span data-stu-id="13833-237">The [**DataChanged**](https://msdn.microsoft.com/library/windows/apps/br241620) event notifies you when roaming data changes.</span></span> <span data-ttu-id="13833-238">In diesem Beispiel wird `DataChangeHandler` als Handler für Änderungen an Roamingdaten festgelegt.</span><span class="sxs-lookup"><span data-stu-id="13833-238">This example sets `DataChangeHandler` as the handler for roaming data changes.</span></span>

```csharp
void InitHandlers()
    {
       Windows.Storage.ApplicationData.Current.DataChanged += 
          new TypedEventHandler<ApplicationData, object>(DataChangeHandler);
    }

    void DataChangeHandler(Windows.Storage.ApplicationData appData, object o)
    {
       // TODO: Refresh your data
    }
```

2.  <span data-ttu-id="13833-239">Rufen Sie die Container für die Einstellungen und Dateien der App ab.</span><span class="sxs-lookup"><span data-stu-id="13833-239">Get the containers for the app's settings and files.</span></span>

    <span data-ttu-id="13833-240">Rufen Sie mit der [**ApplicationData.RoamingSettings**](https://msdn.microsoft.com/library/windows/apps/br241624)-Eigenschaft die Einstellungen und mit der [**ApplicationData.RoamingFolder**](https://msdn.microsoft.com/library/windows/apps/br241623)-Eigenschaft die Dateien ab.</span><span class="sxs-lookup"><span data-stu-id="13833-240">Use the [**ApplicationData.RoamingSettings**](https://msdn.microsoft.com/library/windows/apps/br241624) property to get the settings and the [**ApplicationData.RoamingFolder**](https://msdn.microsoft.com/library/windows/apps/br241623) property to get the files.</span></span>

```csharp
Windows.Storage.ApplicationDataContainer roamingSettings = 
        Windows.Storage.ApplicationData.Current.RoamingSettings;
    Windows.Storage.StorageFolder roamingFolder = 
        Windows.Storage.ApplicationData.Current.RoamingFolder;
```

### <a name="create-and-retrieve-roaming-settings"></a><span data-ttu-id="13833-241">Erstellen und Abrufen von Roamingeinstellungen</span><span class="sxs-lookup"><span data-stu-id="13833-241">Create and retrieve roaming settings</span></span>

<span data-ttu-id="13833-242">Verwenden Sie die [**ApplicationDataContainer.Values**](https://msdn.microsoft.com/library/windows/apps/br241615)-Eigenschaft, um auf die Einstellungen im Container `roamingSettings` zuzugreifen, den wir im vorherigen Abschnitt abgerufen haben.</span><span class="sxs-lookup"><span data-stu-id="13833-242">Use the [**ApplicationDataContainer.Values**](https://msdn.microsoft.com/library/windows/apps/br241615) property to access the settings in the `roamingSettings` container we got in the previous section.</span></span> <span data-ttu-id="13833-243">In diesem Beispiel wird eine einfache Einstellung namens `exampleSetting` und ein zusammengesetzter Wert namens `composite` erstellt.</span><span class="sxs-lookup"><span data-stu-id="13833-243">This example creates a simple setting named `exampleSetting` and a composite value named `composite`.</span></span>

```csharp
// Simple setting

roamingSettings.Values["exampleSetting"] = "Hello World";
// High Priority setting, for example, last page position in book reader app
roamingSettings.values["HighPriority"] = "65";

// Composite setting

Windows.Storage.ApplicationDataCompositeValue composite = 
    new Windows.Storage.ApplicationDataCompositeValue();
composite["intVal"] = 1;
composite["strVal"] = "string";

roamingSettings.Values["exampleCompositeSetting"] = composite;

```

<span data-ttu-id="13833-244">Dieses Beispiel ruft die gerade erstellten Einstellungen ab.</span><span class="sxs-lookup"><span data-stu-id="13833-244">This example retrieves the settings we just created.</span></span>

```csharp
// Simple setting

Object value = roamingSettings.Values["exampleSetting"];

// Composite setting

Windows.Storage.ApplicationDataCompositeValue composite = 
   (Windows.Storage.ApplicationDataCompositeValue)roamingSettings.Values["exampleCompositeSetting"];

if (composite == null)
{
   // No data
}
else
{
   // Access data in composite["intVal"] and composite["strVal"]
}
```

### <a name="create-and-retrieve-roaming-files"></a><span data-ttu-id="13833-245">Erstellen und Abrufen von Roamingdateien</span><span class="sxs-lookup"><span data-stu-id="13833-245">Create and retrieve roaming files</span></span>

<span data-ttu-id="13833-246">Verwenden Sie die Datei-APIs, z.B. [**Windows.Storage.StorageFolder.CreateFileAsync**](https://msdn.microsoft.com/library/windows/apps/br227249) und [**Windows.Storage.FileIO.WriteTextAsync**](https://msdn.microsoft.com/library/windows/apps/hh701505), um eine Datei im Roamingspeicher für App-Daten zu erstellen und zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="13833-246">To create and update a file in the roaming app data store, use the file APIs, such as [**Windows.Storage.StorageFolder.CreateFileAsync**](https://msdn.microsoft.com/library/windows/apps/br227249) and [**Windows.Storage.FileIO.WriteTextAsync**](https://msdn.microsoft.com/library/windows/apps/hh701505).</span></span> <span data-ttu-id="13833-247">In diesem Beispiel wird im Container `roamingFolder` die Datei `dataFile.txt` erstellt, in die das aktuelle Datum und die Uhrzeit geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="13833-247">This example creates a file named `dataFile.txt` in the `roamingFolder` container and writes the current date and time to the file.</span></span> <span data-ttu-id="13833-248">Der Wert **ReplaceExisting** aus der [**CreationCollisionOption**](https://msdn.microsoft.com/library/windows/apps/br241631)-Enumeration gibt an, dass die Datei ersetzt werden soll, falls sie bereits vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="13833-248">The **ReplaceExisting** value from the [**CreationCollisionOption**](https://msdn.microsoft.com/library/windows/apps/br241631) enumeration indicates to replace the file if it already exists.</span></span>

```csharp
async void WriteTimestamp()
{
   Windows.Globalization.DateTimeFormatting.DateTimeFormatter formatter = 
       new Windows.Globalization.DateTimeFormatting.DateTimeFormatter("longtime");

   StorageFile sampleFile = await roamingFolder.CreateFileAsync("dataFile.txt", 
       CreationCollisionOption.ReplaceExisting);
   await FileIO.WriteTextAsync(sampleFile, formatter.Format(DateTimeOffset.Now));
}
```

<span data-ttu-id="13833-249">Verwenden Sie die Datei-APIs, z.B. [**Windows.Storage.StorageFolder.GetFileAsync**](https://msdn.microsoft.com/library/windows/apps/br227272), [**Windows.Storage.StorageFile.GetFileFromApplicationUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701741) und [**Windows.Storage.FileIO.ReadTextAsync**](https://msdn.microsoft.com/library/windows/apps/hh701482), um eine Datei im Roamingspeicher für App-Daten zu öffnen und zu lesen.</span><span class="sxs-lookup"><span data-stu-id="13833-249">To open and read a file in the roaming app data store, use the file APIs, such as [**Windows.Storage.StorageFolder.GetFileAsync**](https://msdn.microsoft.com/library/windows/apps/br227272), [**Windows.Storage.StorageFile.GetFileFromApplicationUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701741), and [**Windows.Storage.FileIO.ReadTextAsync**](https://msdn.microsoft.com/library/windows/apps/hh701482).</span></span> <span data-ttu-id="13833-250">In diesem Beispiel wird die im vorherigen Abschnitt erstellte Datei `dataFile.txt` geöffnet und das Datum aus der Datei gelesen.</span><span class="sxs-lookup"><span data-stu-id="13833-250">This example opens the `dataFile.txt` file created in the previous section and reads the date from the file.</span></span> <span data-ttu-id="13833-251">Einzelheiten zum Laden von Dateiressourcen aus verschiedenen Speicherorten finden Sie unter [So wird's gemacht: Laden von Dateiressourcen](https://msdn.microsoft.com/library/windows/apps/xaml/hh965322).</span><span class="sxs-lookup"><span data-stu-id="13833-251">For details on loading file resources from various locations, see [How to load file resources](https://msdn.microsoft.com/library/windows/apps/xaml/hh965322).</span></span>

```csharp
async void ReadTimestamp()
{
   try
   {
      StorageFile sampleFile = await roamingFolder.GetFileAsync("dataFile.txt");
      String timestamp = await FileIO.ReadTextAsync(sampleFile);
      // Data is contained in timestamp
   }
   catch (Exception)
   {
      // Timestamp not found
   }
}
```


## <a name="temporary-app-data"></a><span data-ttu-id="13833-252">Temporäre App-Daten</span><span class="sxs-lookup"><span data-stu-id="13833-252">Temporary app data</span></span>


<span data-ttu-id="13833-253">Der temporäre App-Datenspeicher funktioniert wie ein Cache.</span><span class="sxs-lookup"><span data-stu-id="13833-253">The temporary app data store works like a cache.</span></span> <span data-ttu-id="13833-254">Für diese Dateien erfolgt kein Roaming, und sie können jederzeit gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="13833-254">Its files do not roam and could be removed at any time.</span></span> <span data-ttu-id="13833-255">Daten, die an diesem Speicherort gespeichert werden, können von der Aufgabe zur Systemverwaltung jederzeit automatisch gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="13833-255">The System Maintenance task can automatically delete data stored at this location at any time.</span></span> <span data-ttu-id="13833-256">Benutzer können Dateien im temporären Datenspeicher auch mit der Datenträgerbereinigung löschen.</span><span class="sxs-lookup"><span data-stu-id="13833-256">The user can also clear files from the temporary data store using Disk Cleanup.</span></span> <span data-ttu-id="13833-257">Temporäre App-Daten können zum Speichern temporärer Informationen während einer App-Sitzung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="13833-257">Temporary app data can be used for storing temporary information during an app session.</span></span> <span data-ttu-id="13833-258">Es gibt jedoch keine Garantie dafür, dass diese Daten über die App-Sitzung hinaus beibehalten werden, da der verwendete Speicherplatz ggf. vom System zurückgefordert wird.</span><span class="sxs-lookup"><span data-stu-id="13833-258">There is no guarantee that this data will persist beyond the end of the app session as the system might reclaim the used space if needed.</span></span> <span data-ttu-id="13833-259">Der Speicherort ist über die [**temporaryFolder**](https://msdn.microsoft.com/library/windows/apps/br241629)-Eigenschaft verfügbar.</span><span class="sxs-lookup"><span data-stu-id="13833-259">The location is available via the [**temporaryFolder**](https://msdn.microsoft.com/library/windows/apps/br241629) property.</span></span>

### <a name="retrieve-the-temporary-data-container"></a><span data-ttu-id="13833-260">Abrufen des temporären Datencontainers</span><span class="sxs-lookup"><span data-stu-id="13833-260">Retrieve the temporary data container</span></span>

<span data-ttu-id="13833-261">Rufen Sie die Dateien mit der [**ApplicationData.TemporaryFolder**](https://msdn.microsoft.com/library/windows/apps/br241629)-Eigenschaft ab.</span><span class="sxs-lookup"><span data-stu-id="13833-261">Use the [**ApplicationData.TemporaryFolder**](https://msdn.microsoft.com/library/windows/apps/br241629) property to get the files.</span></span> <span data-ttu-id="13833-262">In den nächsten Schritten wird die `temporaryFolder`-Variable aus diesem Schritt verwendet.</span><span class="sxs-lookup"><span data-stu-id="13833-262">The next steps use the `temporaryFolder` variable from this step.</span></span>

```csharp
Windows.Storage.StorageFolder temporaryFolder = ApplicationData.Current.TemporaryFolder;
```

### <a name="create-and-read-temporary-files"></a><span data-ttu-id="13833-263">Erstellen und Lesen von temporären Dateien</span><span class="sxs-lookup"><span data-stu-id="13833-263">Create and read temporary files</span></span>

<span data-ttu-id="13833-264">Verwenden Sie die Datei-APIs, z.B. [**Windows.Storage.StorageFolder.CreateFileAsync**](https://msdn.microsoft.com/library/windows/apps/br227249) und [**Windows.Storage.FileIO.WriteTextAsync**](https://msdn.microsoft.com/library/windows/apps/hh701505), um eine Datei im temporären App-Datenspeicher zu erstellen und zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="13833-264">To create and update a file in the temporary app data store, use the file APIs, such as [**Windows.Storage.StorageFolder.CreateFileAsync**](https://msdn.microsoft.com/library/windows/apps/br227249) and [**Windows.Storage.FileIO.WriteTextAsync**](https://msdn.microsoft.com/library/windows/apps/hh701505).</span></span> <span data-ttu-id="13833-265">In diesem Beispiel wird im Container `temporaryFolder` die Datei `dataFile.txt` erstellt, in die das aktuelle Datum und die Uhrzeit geschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="13833-265">This example creates a file named `dataFile.txt` in the `temporaryFolder` container and writes the current date and time to the file.</span></span> <span data-ttu-id="13833-266">Der Wert **ReplaceExisting** aus der [**CreationCollisionOption**](https://msdn.microsoft.com/library/windows/apps/br241631)-Enumeration gibt an, dass die Datei ersetzt werden soll, falls sie bereits vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="13833-266">The **ReplaceExisting** value from the [**CreationCollisionOption**](https://msdn.microsoft.com/library/windows/apps/br241631) enumeration indicates to replace the file if it already exists.</span></span>


```csharp
async void WriteTimestamp()
{
   Windows.Globalization.DateTimeFormatting.DateTimeFormatter formatter = 
       new Windows.Globalization.DateTimeFormatting.DateTimeFormatter("longtime");

   StorageFile sampleFile = await temporaryFolder.CreateFileAsync("dataFile.txt", 
       CreateCollisionOption.ReplaceExisting);
   await FileIO.WriteTextAsync(sampleFile, formatter.Format(DateTimeOffset.Now));
}
```

<span data-ttu-id="13833-267">Verwenden Sie die Datei-APIs, z.B. [**Windows.Storage.StorageFolder.GetFileAsync**](https://msdn.microsoft.com/library/windows/apps/br227272), [**Windows.Storage.StorageFile.GetFileFromApplicationUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701741) und [**Windows.Storage.FileIO.ReadTextAsync**](https://msdn.microsoft.com/library/windows/apps/hh701482), um eine Datei im temporären App-Datenspeicher zu öffnen und zu lesen.</span><span class="sxs-lookup"><span data-stu-id="13833-267">To open and read a file in the temporary app data store, use the file APIs, such as [**Windows.Storage.StorageFolder.GetFileAsync**](https://msdn.microsoft.com/library/windows/apps/br227272), [**Windows.Storage.StorageFile.GetFileFromApplicationUriAsync**](https://msdn.microsoft.com/library/windows/apps/hh701741), and [**Windows.Storage.FileIO.ReadTextAsync**](https://msdn.microsoft.com/library/windows/apps/hh701482).</span></span> <span data-ttu-id="13833-268">In diesem Beispiel wird die im vorherigen Schritt erstellte Datei `dataFile.txt` geöffnet und das Datum aus der Datei gelesen.</span><span class="sxs-lookup"><span data-stu-id="13833-268">This example opens the `dataFile.txt` file created in the previous step and reads the date from the file.</span></span> <span data-ttu-id="13833-269">Einzelheiten zum Laden von Dateiressourcen aus verschiedenen Speicherorten finden Sie unter [So wird's gemacht: Laden von Dateiressourcen](https://msdn.microsoft.com/library/windows/apps/xaml/hh965322).</span><span class="sxs-lookup"><span data-stu-id="13833-269">For details on loading file resources from various locations, see [How to load file resources](https://msdn.microsoft.com/library/windows/apps/xaml/hh965322).</span></span>

```csharp
async void ReadTimestamp()
{
   try
   {
      StorageFile sampleFile = await temporaryFolder.GetFileAsync("dataFile.txt");
      String timestamp = await FileIO.ReadTextAsync(sampleFile);
      // Data is contained in timestamp
   }
   catch (Exception)
   {
      // Timestamp not found
   }
}
```

## <a name="organize-app-data-with-containers"></a><span data-ttu-id="13833-270">Organisieren von App-Daten mit Containern</span><span class="sxs-lookup"><span data-stu-id="13833-270">Organize app data with containers</span></span>


<span data-ttu-id="13833-271">Um Ihre Einstellungen für App-Daten und Dateien strukturiert zu speichern, erstellen Sie Container (dargestellt durch [**ApplicationDataContainer**](https://msdn.microsoft.com/library/windows/apps/br241599)-Objekte), statt direkt mit Verzeichnissen zu arbeiten.</span><span class="sxs-lookup"><span data-stu-id="13833-271">To help you organize your app data settings and files, you create containers (represented by [**ApplicationDataContainer**](https://msdn.microsoft.com/library/windows/apps/br241599) objects) instead of working directly with directories.</span></span> <span data-ttu-id="13833-272">Sie können Container zu den lokalen, Roaming- und temporären App-Datenspeichern hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="13833-272">You can add containers to the local, roaming, and temporary app data stores.</span></span> <span data-ttu-id="13833-273">Container können in bis zu 32 Ebenen geschachtelt werden.</span><span class="sxs-lookup"><span data-stu-id="13833-273">Containers can be nested up to 32 levels deep.</span></span>

<span data-ttu-id="13833-274">Rufen Sie die [**ApplicationDataContainer.CreateContainer**](https://msdn.microsoft.com/library/windows/apps/br241611)-Methode auf, um einen Einstellungscontainer zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="13833-274">To create a settings container, call the [**ApplicationDataContainer.CreateContainer**](https://msdn.microsoft.com/library/windows/apps/br241611) method.</span></span> <span data-ttu-id="13833-275">In diesem Beispiel wird ein lokaler Einstellungscontainer namens `exampleContainer` erstellt und eine Einstellung namens `exampleSetting` hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="13833-275">This example creates a local settings container named `exampleContainer` and adds a setting named `exampleSetting`.</span></span> <span data-ttu-id="13833-276">Der Wert **Always** aus der [**ApplicationDataCreateDisposition**](https://msdn.microsoft.com/library/windows/apps/br241616)-Enumeration gibt an, dass der Container erstellt wird, sofern er noch nicht vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="13833-276">The **Always** value from the [**ApplicationDataCreateDisposition**](https://msdn.microsoft.com/library/windows/apps/br241616) enumeration indicates that the container is created if it doesn't already exist.</span></span>

```csharp
Windows.Storage.ApplicationDataContainer localSettings = 
    Windows.Storage.ApplicationData.Current.LocalSettings;
Windows.Storage.StorageFolder localFolder = 
    Windows.Storage.ApplicationData.Current.LocalFolder;

// Setting in a container
Windows.Storage.ApplicationDataContainer container = 
   localSettings.CreateContainer("exampleContainer", Windows.Storage.ApplicationDataCreateDisposition.Always);

if (localSettings.Containers.ContainsKey("exampleContainer"))
{
   localSettings.Containers["exampleContainer"].Values["exampleSetting"] = "Hello Windows";
}
```

## <a name="delete-app-settings-and-containers"></a><span data-ttu-id="13833-277">Löschen von App-Einstellungen und Containern</span><span class="sxs-lookup"><span data-stu-id="13833-277">Delete app settings and containers</span></span>


<span data-ttu-id="13833-278">Verwenden Sie die [**ApplicationDataContainerSettings.Remove**](https://msdn.microsoft.com/library/windows/apps/br241608)-Methode, um eine einfache Einstellung zu löschen, die Ihre App nicht mehr benötigt.</span><span class="sxs-lookup"><span data-stu-id="13833-278">To delete a simple setting that your app no longer needs, use the [**ApplicationDataContainerSettings.Remove**](https://msdn.microsoft.com/library/windows/apps/br241608) method.</span></span> <span data-ttu-id="13833-279">In diesem Beispiel wird die zuvor erstellte, lokale `exampleSetting`-Einstellung gelöscht.</span><span class="sxs-lookup"><span data-stu-id="13833-279">This example deletesthe `exampleSetting` local setting that we created earlier.</span></span>

```csharp
Windows.Storage.ApplicationDataContainer localSettings = 
    Windows.Storage.ApplicationData.Current.LocalSettings;
Windows.Storage.StorageFolder localFolder = 
    Windows.Storage.ApplicationData.Current.LocalFolder;

// Delete simple setting

localSettings.Values.Remove("exampleSetting");
```

<span data-ttu-id="13833-280">Verwenden Sie die [**ApplicationDataCompositeValue.Remove**](https://msdn.microsoft.com/library/windows/apps/br241597)-Methode, um eine zusammengesetzte Einstellung zu löschen.</span><span class="sxs-lookup"><span data-stu-id="13833-280">To delete a composite setting, use the [**ApplicationDataCompositeValue.Remove**](https://msdn.microsoft.com/library/windows/apps/br241597) method.</span></span> <span data-ttu-id="13833-281">In diesem Beispiel wird die lokale, zusammengesetzte `exampleCompositeSetting`-Einstellung gelöscht, die in einem früheren Beispiel erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="13833-281">This example deletes the local `exampleCompositeSetting` composite setting we created in an earlier example.</span></span>

```csharp
Windows.Storage.ApplicationDataContainer localSettings = 
    Windows.Storage.ApplicationData.Current.LocalSettings;
Windows.Storage.StorageFolder localFolder = 
    Windows.Storage.ApplicationData.Current.LocalFolder;

// Delete composite setting

localSettings.Values.Remove("exampleCompositeSetting");
```

<span data-ttu-id="13833-282">Rufen Sie die [**ApplicationDataContainer.DeleteContainer**](https://msdn.microsoft.com/library/windows/apps/br241612)-Methode auf, um einen Container zu löschen.</span><span class="sxs-lookup"><span data-stu-id="13833-282">To delete a container, call the [**ApplicationDataContainer.DeleteContainer**](https://msdn.microsoft.com/library/windows/apps/br241612) method.</span></span> <span data-ttu-id="13833-283">In diesem Beispiel wird der zuvor erstellte, lokale `exampleContainer`-Einstellungscontainer gelöscht.</span><span class="sxs-lookup"><span data-stu-id="13833-283">This example deletes the local `exampleContainer` settings container we created earlier.</span></span>

```csharp
Windows.Storage.ApplicationDataContainer localSettings = 
    Windows.Storage.ApplicationData.Current.LocalSettings;
Windows.Storage.StorageFolder localFolder = 
    Windows.Storage.ApplicationData.Current.LocalFolder;

// Delete container

localSettings.DeleteContainer("exampleContainer");
```

## <a name="versioning-your-app-data"></a><span data-ttu-id="13833-284">Versionsverwaltung Ihrer App-Daten</span><span class="sxs-lookup"><span data-stu-id="13833-284">Versioning your app data</span></span>


<span data-ttu-id="13833-285">Optional können Sie die App-Daten für Ihre App mit einer Versionsnummer versehen.</span><span class="sxs-lookup"><span data-stu-id="13833-285">You can optionally version the app data for your app.</span></span> <span data-ttu-id="13833-286">In diesem Fall können Sie neue Versionen der betreffenden App erstellen, mit denen das Format der App-Daten geändert wird, ohne dass es dadurch zu Kompatibilitätsproblemen mit der Vorgängerversion der App kommt.</span><span class="sxs-lookup"><span data-stu-id="13833-286">This would enable you to create a future version of your app that changes the format of its app data without causing compatibility problems with the previous version of your app.</span></span> <span data-ttu-id="13833-287">Die App prüft die Version der App-Daten im Dateispeicher. Handelt es sich um eine niedrigere Version als erwartet, aktualisiert die App sowohl die Anwendungsdaten auf das neue Format als auch die Version.</span><span class="sxs-lookup"><span data-stu-id="13833-287">The app checks the version of the app data in the data store, and if the version is less than the version the app expects, the app should update the app data to the new format and update the version.</span></span> <span data-ttu-id="13833-288">Weitere Informationen finden Sie in den Artikeln zur [**Application.Version**](https://msdn.microsoft.com/library/windows/apps/br241630)-Eigenschaft und zur [**ApplicationData.SetVersionAsync**](https://msdn.microsoft.com/library/windows/apps/hh701429)-Methode.</span><span class="sxs-lookup"><span data-stu-id="13833-288">For more info, see the[**Application.Version**](https://msdn.microsoft.com/library/windows/apps/br241630) property and the [**ApplicationData.SetVersionAsync**](https://msdn.microsoft.com/library/windows/apps/hh701429) method.</span></span>

## <a name="related-articles"></a><span data-ttu-id="13833-289">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="13833-289">Related articles</span></span>

* [**<span data-ttu-id="13833-290">Windows.Storage.ApplicationData</span><span class="sxs-lookup"><span data-stu-id="13833-290">Windows.Storage.ApplicationData</span></span>**](https://msdn.microsoft.com/library/windows/apps/br241587)
* [**<span data-ttu-id="13833-291">Windows.Storage.ApplicationData.RoamingSettings</span><span class="sxs-lookup"><span data-stu-id="13833-291">Windows.Storage.ApplicationData.RoamingSettings</span></span>**](https://msdn.microsoft.com/library/windows/apps/br241624)
* [**<span data-ttu-id="13833-292">Windows.Storage.ApplicationData.RoamingFolder</span><span class="sxs-lookup"><span data-stu-id="13833-292">Windows.Storage.ApplicationData.RoamingFolder</span></span>**](https://msdn.microsoft.com/library/windows/apps/br241623)
* [**<span data-ttu-id="13833-293">Windows.Storage.ApplicationData.RoamingStorageQuota</span><span class="sxs-lookup"><span data-stu-id="13833-293">Windows.Storage.ApplicationData.RoamingStorageQuota</span></span>**](https://msdn.microsoft.com/library/windows/apps/br241625)
* [**<span data-ttu-id="13833-294">Windows.Storage.ApplicationDataCompositeValue</span><span class="sxs-lookup"><span data-stu-id="13833-294">Windows.Storage.ApplicationDataCompositeValue</span></span>**](https://msdn.microsoft.com/library/windows/apps/br241588)
