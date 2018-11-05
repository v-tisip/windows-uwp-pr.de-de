---
author: eliotcowley
title: Fehlende .NET-APIs in Unity und UWP
description: Informieren Sie sich über die fehlenden .NET-APIs beim Erstellen von UWP-Spielen in Unity sowie über Lösungen für häufig auftretende Probleme.
ms.assetid: 28A8B061-5AE8-4CDA-B4AB-2EF0151E57C1
ms.author: elcowle
ms.date: 2/21/2018
ms.topic: article
keywords: Windows10, UWP, Spiele, .NET, Unity
ms.localizationpriority: medium
ms.openlocfilehash: 4b795ed47249eee1f9dc21b195d46f450997019e
ms.sourcegitcommit: e814a13978f33654d8e995584f4b047cb53e0aef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "6037272"
---
# <a name="missing-net-apis-in-unity-and-uwp"></a><span data-ttu-id="55b8c-104">Fehlende .NET-APIs in Unity und UWP</span><span class="sxs-lookup"><span data-stu-id="55b8c-104">Missing .NET APIs in Unity and UWP</span></span>

<span data-ttu-id="55b8c-105">Beim Erstellen eines UWP-Spiels mithilfe von .NET werden Sie möglicherweise feststellen, dass einige APIs, die Sie im Unity-Editor oder für ein eigenständiges PC-Spiel verwenden möchten, für UWP nicht vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="55b8c-105">When building a UWP game using .NET, you may find that some APIs that you might use in the Unity editor or for a standalone PC game are not present for UWP.</span></span> <span data-ttu-id="55b8c-106">Der Grund ist, dass .NET für UWP-Apps nur eine Teilmenge der Typen enthält, die im vollständigen .NET-Framework für jeden Namespace bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="55b8c-106">That's because .NET for UWP apps includes a subset of the types provided in the full .NET Framework for each namespace.</span></span>

<span data-ttu-id="55b8c-107">Zudem verwenden einige Spiele-Engines verschiedene Arten von .NET, die mit .NET für UWP nicht vollständig kompatibel sind, z.B. Mono von Unity.</span><span class="sxs-lookup"><span data-stu-id="55b8c-107">Additionally, some game engines use different flavors of .NET that aren't fully compatible with .NET for UWP, such as Unity's Mono.</span></span> <span data-ttu-id="55b8c-108">Wenn Sie Ihr Spiel schreiben, wird wahrscheinlich im Editor alles funktionieren, aber sobald Sie einen UWP-Build erstellen, erhalten Sie möglicherweise folgende Fehlermeldung: **Der Typ oder Namespace "Formatters" ist im Namespace 'System.Runtime.Serialization' nicht vorhanden. (Fehlt ein Assemblyverweis?)**.</span><span class="sxs-lookup"><span data-stu-id="55b8c-108">So when you're writing your game, everything might work fine in the editor, but when you go to build for UWP, you might get errors like this: **The type or namespace 'Formatters' does not exist in the namespace 'System.Runtime.Serialization' (are you missing an assembly reference?)**</span></span>

<span data-ttu-id="55b8c-109">Glücklicherweise stellt Unity einige dieser fehlenden APIs als Erweiterungsmethoden und Ersatztypen bereit. Sie werden beschriebenen im Artikel [Universelle Windows-Plattform: Fehlende .NET-Typen im .NET Scripting-Backend](https://docs.unity3d.com/Manual/windowsstore-missingtypes.html).</span><span class="sxs-lookup"><span data-stu-id="55b8c-109">Fortunately, Unity provides some of these missing APIs as extension methods and replacement types, which are described in [Universal Windows Platform: Missing .NET Types on .NET Scripting Backend](https://docs.unity3d.com/Manual/windowsstore-missingtypes.html).</span></span> <span data-ttu-id="55b8c-110">Hilfe für den Fall, dass die benötigte Funktionalität nicht vorhanden ist, finden Sie unter [Überblick über Apps für .NET für Windows 8.x](https://msdn.microsoft.com/library/windows/apps/br230302). Dort wird erläutert, wie Sie Ihren Code konvertieren können, um WinRT- oder „.NET für UWP”-APIs zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="55b8c-110">However, if the functionality you need is not here, [.NET for Windows 8.x apps overview](https://msdn.microsoft.com/library/windows/apps/br230302) discusses ways you can convert your code to use WinRT or .NET for UWP APIs.</span></span> <span data-ttu-id="55b8c-111">(Es wird Windows 8 behandelt, aber die Erläuterung gilt auch für UWP-Apps unter Windows 10.)</span><span class="sxs-lookup"><span data-stu-id="55b8c-111">(It discusses Windows 8, but is applicable to Windows 10 UWP apps as well.)</span></span>

## <a name="net-standard"></a><span data-ttu-id="55b8c-112">.NET-Standard</span><span class="sxs-lookup"><span data-stu-id="55b8c-112">.NET Standard</span></span>

<span data-ttu-id="55b8c-113">Um zu verstehen, warum einige APIs möglicherweise nicht funktionieren, ist es wichtig, die verschiedenen .NET-Varianten zu kennen und zu verstehen, wie .NET von UWP implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="55b8c-113">To understand why some APIs might not be working, it's important to understand the different .NET flavors and how UWP implements .NET.</span></span> <span data-ttu-id="55b8c-114">Der [.NET-Standard](https://docs.microsoft.com/dotnet/standard/net-standard) ist eine formale Spezifikation von .NET-APIs, die plattformübergreifend sein und die verschiedenen .NET-Varianten vereinheitlichen soll.</span><span class="sxs-lookup"><span data-stu-id="55b8c-114">The [.NET Standard](https://docs.microsoft.com/dotnet/standard/net-standard) is a formal specification of .NET APIs that is meant to be cross-platform, and unify the different .NET flavors.</span></span> <span data-ttu-id="55b8c-115">Jede Implementierung von .NET unterstützt eine bestimmte Version des .NET-Standards.</span><span class="sxs-lookup"><span data-stu-id="55b8c-115">Each implementation of .NET supports a certain version of the .NET Standard.</span></span> <span data-ttu-id="55b8c-116">Eine Tabelle mit Standards und Implementierungen finden Sie unter [Unterstützung für die .NET-Implementierung](https://docs.microsoft.com/dotnet/standard/net-standard#net-implementation-support).</span><span class="sxs-lookup"><span data-stu-id="55b8c-116">You can see a table of standards and implementations at [.NET implementation support](https://docs.microsoft.com/dotnet/standard/net-standard#net-implementation-support).</span></span>

<span data-ttu-id="55b8c-117">Jede Version des UWP SDK entspricht einer anderen Ebene des .NET-Standards.</span><span class="sxs-lookup"><span data-stu-id="55b8c-117">Each version of the UWP SDK conforms to a different level of .NET Standard.</span></span> <span data-ttu-id="55b8c-118">Beispielsweise unterstützt das 16299-SDK (Fall Creators Update) den .NET-Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="55b8c-118">For example, the 16299 SDK (the Fall Creators Update) supports .NET Standard 2.0.</span></span>

<span data-ttu-id="55b8c-119">Wenn Sie wissen möchten, ob eine bestimmte .NET-API in der von Ihnen ausgewählten UWP-Version unterstützt wird, können Sie in der [API-Referenz für den .NET-Standard](https://docs.microsoft.com/dotnet/api/index?view=netstandard-2.0) die Version des .NET-Standards suchen, die von dieser UWP-Version unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="55b8c-119">If you want to know if a certain .NET API is supported in the UWP version that you're targeting, you can check the [.NET Standard API Reference](https://docs.microsoft.com/dotnet/api/index?view=netstandard-2.0) and select the version of the .NET Standard that's supported by that version of UWP.</span></span>

## <a name="scripting-backend-configuration"></a><span data-ttu-id="55b8c-120">Scripting-Backend-Konfiguration</span><span class="sxs-lookup"><span data-stu-id="55b8c-120">Scripting backend configuration</span></span>

<span data-ttu-id="55b8c-121">Wenn Sie Probleme mit Builds für UWP haben, sollten Sie zuerst die **Player-Einstellungen** überprüfen (**Datei > Build-Einstellungen**, wählen Sie **Universelle Windows-Plattform**, und dann **Player-Einstellungen**).</span><span class="sxs-lookup"><span data-stu-id="55b8c-121">The first thing you should do if you're having trouble building for UWP is check the **Player Settings** (**File > Build Settings**, select **Universal Windows Platform**, and then **Player Settings**).</span></span> <span data-ttu-id="55b8c-122">Unter **Andere Einstellungen > Konfiguration** sind die ersten drei Dropdowns (**Scripting-Laufzeitversion**, **Scripting-Backend** und **Api-Kompatibilitätsgrad**) wichtige Einstellungen, die zu berücksichtigen sind.</span><span class="sxs-lookup"><span data-stu-id="55b8c-122">Under **Other Settings > Configuration**, the first three dropdowns (**Scripting Runtime Version**, **Scripting Backend**, and **Api Compatibility Level**) are all important settings to consider.</span></span>

<span data-ttu-id="55b8c-123">Anhand der vom Unity-Scripting-Backend verwendeten **Scripting-Laufzeitversion** können Sie die (ungefähre) äquivalente Version der von Ihnen gewählten .NET Framework-Unterstützung ermitteln.</span><span class="sxs-lookup"><span data-stu-id="55b8c-123">The **Scripting Runtime Version** is what the Unity scripting backend uses which allows you to get the (roughly) equivalent version of .NET Framework support that you choose.</span></span> <span data-ttu-id="55b8c-124">Beachten Sie jedoch, dass nicht alle APIs in dieser Version des .NET-Frameworks unterstützt werden, sondern nur die in der Version des .NET-Standards, auf die Ihr UWP abzielt.</span><span class="sxs-lookup"><span data-stu-id="55b8c-124">However, keep in mind that not all APIs in that version of the .NET Framework will be supported, only those in the version of .NET Standard that your UWP is targeting.</span></span>

<span data-ttu-id="55b8c-125">Mit neuen .NET-Versionen werden häufig zusätzliche APIs zu .NET-Standard hinzugefügt, die es Ihnen ermöglichen, für eigenständige und UWP-Anwendungen den gleichen Code zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="55b8c-125">Often with new .NET releases, more APIs are added to .NET Standard which might allow you to use the same code across standalone and UWP.</span></span> <span data-ttu-id="55b8c-126">Beispielsweise wurde der Namespace [System.Runtime.Serialization.Json](https://docs.microsoft.com/dotnet/api/system.runtime.serialization.json) mit .NET-Standard 2.0 eingeführt.</span><span class="sxs-lookup"><span data-stu-id="55b8c-126">For example, the [System.Runtime.Serialization.Json](https://docs.microsoft.com/dotnet/api/system.runtime.serialization.json) namespace was introduced in .NET Standard 2.0.</span></span> <span data-ttu-id="55b8c-127">Wenn Sie die **Scripting-Laufzeitversion** auf **.NET 3.5 Equivalent** festlegen (wodurch auf eine frühere Version von .NET-Standard abgezielt wird), tritt ein Fehler auf bei dem Versuch, die API zu verwenden. Wenn Sie **.NET 4.6 Equivalent** (unterstützt .NET-Standard 2.0) wählen, wird die API funktionieren.</span><span class="sxs-lookup"><span data-stu-id="55b8c-127">If you set the **Scripting Runtime Version** to **.NET 3.5 Equivalent** (which targets an earlier version of the .NET Standard), you will get an error when trying to use the API; switch it to **.NET 4.6 Equivalent** (which supports .NET Standard 2.0), and the API will work.</span></span>

<span data-ttu-id="55b8c-128">Das **Scripting-Backend-** kann **.NET** oder **IL2CPP** sein.</span><span class="sxs-lookup"><span data-stu-id="55b8c-128">The **Scripting Backend** can be **.NET** or **IL2CPP**.</span></span> <span data-ttu-id="55b8c-129">In diesem Thema wird angenommen, dass Sie **.NET** gewählt haben, da in diesem Fall die hier beschriebenen Probleme auftreten.</span><span class="sxs-lookup"><span data-stu-id="55b8c-129">For this topic, we assume you have chosen **.NET**, since that's where the problems discussed here arise.</span></span> <span data-ttu-id="55b8c-130">Weitere Informationen finden Sie unter [Scripting-Backends](https://docs.unity3d.com/Manual/windowsstore-scriptingbackends.html).</span><span class="sxs-lookup"><span data-stu-id="55b8c-130">See [Scripting Backends](https://docs.unity3d.com/Manual/windowsstore-scriptingbackends.html) for more information.</span></span>

<span data-ttu-id="55b8c-131">Außerdem sollten Sie den **Api-Kompatibilitätsgrad** auf die Version von .NET festlegen, mit der Ihr Spiel ausgeführt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="55b8c-131">Finally, you should set the **Api Compatibility Level** to the version of .NET that you want your game to run on.</span></span> <span data-ttu-id="55b8c-132">Dieser muss der **Scripting-Laufzeitversion** entsprechen.</span><span class="sxs-lookup"><span data-stu-id="55b8c-132">This should match the **Scripting Runtime Version**.</span></span>

<span data-ttu-id="55b8c-133">Im Allgemeinen sollten Sie für **Scripting-Laufzeitversion** und **Api-Kompatibilitätsgrad** die neueste verfügbare Version wählen, um die bestmögliche Kompatibilität mit dem .NET Framework sicherzustellen und möglichst viele .NET-APIs bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="55b8c-133">In general, for **Scripting Runtime Version** and **Api Compatibility Level**, you should select the latest version available so as to have more compatibility with the .NET Framework, and thus allow you to use more .NET APIs.</span></span>

![Konfiguration: Scripting-Laufzeitversion; Skripting-Backend; Api-Kompatibilitätsebene](images/missing-dot-net-apis-in-unity-1.png)

## <a name="platform-dependent-compilation"></a><span data-ttu-id="55b8c-135">Plattformabhängige Kompilierung</span><span class="sxs-lookup"><span data-stu-id="55b8c-135">Platform-dependent compilation</span></span>

<span data-ttu-id="55b8c-136">Wenn Sie Ihr Unity-Spiel für mehrere Plattformen, einschließlich UWP, erstellen, sollten Sie plattformabhängige Kompilierung verwenden, um sicherzustellen, dass für UWP vorgesehener Code nur ausgeführt wird, wenn das Spiel als eine UWP-Anwendung erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="55b8c-136">If you're building your Unity game for multiple platforms, including UWP, you'll want to use platform-dependent compilation to make sure that code intended for UWP is only run when the game is built as a UWP.</span></span> <span data-ttu-id="55b8c-137">Auf diese Weise können Sie das vollständige .NET-Framework für eigenständige Desktops sowie andere Plattformen und WinRT-APIs für UWP verwenden, ohne dass Buildfehler auftreten.</span><span class="sxs-lookup"><span data-stu-id="55b8c-137">This way, you can use the full .NET Framework for standalone desktop and other platforms, and WinRT APIs for UWP, without getting build errors.</span></span>

<span data-ttu-id="55b8c-138">Verwenden Sie die folgenden Direktiven, um Code nur zu kompilieren, wenn er als UWP-App ausgeführt wird:</span><span class="sxs-lookup"><span data-stu-id="55b8c-138">Use the following directives to only compile code when running as a UWP app:</span></span>

```csharp
#if NETFX_CORE
    // Your UWP code here
#else
    // Your standard code here
#endif
```

> [!NOTE]
> `NETFX_CORE` <span data-ttu-id="55b8c-139">dient nur zur Prüfung, wenn Sie C#-Code mit dem .NET-Scripting-Backend kompilieren.</span><span class="sxs-lookup"><span data-stu-id="55b8c-139">is only meant to check if you're compiling C# code against the .NET scripting backend.</span></span> <span data-ttu-id="55b8c-140">Verwenden Sie `UNITY_WSA_10_0`, wenn Sie ein anderes Scripting-Backend verwenden, beispielsweise IL2CPP.</span><span class="sxs-lookup"><span data-stu-id="55b8c-140">If you're using a different scripting backend, such as IL2CPP, use `UNITY_WSA_10_0` instead.</span></span>

<span data-ttu-id="55b8c-141">Die vollständige Liste der plattformabhängigen Kompilierungsdirektiven finden Sie unter [Plattformabhängige Kompilierung](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html).</span><span class="sxs-lookup"><span data-stu-id="55b8c-141">For the full list of platform-dependent compilation directives, see [Platform dependent compilation](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html).</span></span>

## <a name="common-issues-and-workarounds"></a><span data-ttu-id="55b8c-142">Häufige Probleme und deren Umgehung</span><span class="sxs-lookup"><span data-stu-id="55b8c-142">Common issues and workarounds</span></span>

<span data-ttu-id="55b8c-143">In den folgenden Szenarien werden häufig auftretende Probleme beschrieben, die auftreten können, wenn .NET-APIs in der UWP-Teilmenge fehlen, und es werden Möglichkeiten aufgezeigt, diese Probleme zu umgehen.</span><span class="sxs-lookup"><span data-stu-id="55b8c-143">The following scenarios describe common issues that might arise where .NET APIs are missing from the UWP subset, and ways to get around them.</span></span>

### <a name="data-serialization-using-binaryformatter"></a><span data-ttu-id="55b8c-144">Datenserialisierung mit BinaryFormatter</span><span class="sxs-lookup"><span data-stu-id="55b8c-144">Data serialization using BinaryFormatter</span></span>

<span data-ttu-id="55b8c-145">Es ist üblich, dass Spiele Daten speichern, damit sie von Spielern nicht einfach manipuliert werden können.</span><span class="sxs-lookup"><span data-stu-id="55b8c-145">It is common for games to serialize save data so that players can't easily manipulate it.</span></span> <span data-ttu-id="55b8c-146">Allerdings ist [BinaryFormatter](https://docs.microsoft.com/dotnet/api/system.runtime.serialization.formatters.binary.binaryformatter), womit ein Objekt in die Binärform serialisiert wird, in früheren Versionen des .NET-Standard (vor 2.0) nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="55b8c-146">However, [BinaryFormatter](https://docs.microsoft.com/dotnet/api/system.runtime.serialization.formatters.binary.binaryformatter), which serializes an object into binary, is not available in earlier versions of the .NET Standard (prior to 2.0).</span></span> <span data-ttu-id="55b8c-147">Verwenden Sie stattdessen [XmlSerializer](https://docs.microsoft.com/dotnet/api/system.xml.serialization.xmlserializer) oder [DataContractJsonSerializer](https://docs.microsoft.com/dotnet/api/system.runtime.serialization.json.datacontractjsonserializer).</span><span class="sxs-lookup"><span data-stu-id="55b8c-147">Consider using [XmlSerializer](https://docs.microsoft.com/dotnet/api/system.xml.serialization.xmlserializer) or [DataContractJsonSerializer](https://docs.microsoft.com/dotnet/api/system.runtime.serialization.json.datacontractjsonserializer) instead.</span></span>

```csharp
private void Save()
{
    SaveData data = new SaveData(); // User-defined object to serialize

    DataContractJsonSerializer serializer = 
      new DataContractJsonSerializer(typeof(SaveData));

    FileStream stream = 
      new FileStream(Application.persistentDataPath, FileMode.CreateNew);

    serializer.WriteObject(stream, data);
    stream.Dispose();
}
```

### <a name="io-operations"></a><span data-ttu-id="55b8c-148">E/A-Operationen</span><span class="sxs-lookup"><span data-stu-id="55b8c-148">I/O operations</span></span>

<span data-ttu-id="55b8c-149">Einige Typen im Namespace [System.IO](https://docs.microsoft.com/dotnet/api/system.io) sind in früheren Versionen von .NET-Standard nicht verfügbar, z.B. [FileStream](https://docs.microsoft.com/dotnet/api/system.io.filestream).</span><span class="sxs-lookup"><span data-stu-id="55b8c-149">Some types in the [System.IO](https://docs.microsoft.com/dotnet/api/system.io) namespace, such as [FileStream](https://docs.microsoft.com/dotnet/api/system.io.filestream), are not available in earlier versions of the .NET Standard.</span></span> <span data-ttu-id="55b8c-150">Unity bietet jedoch die Typen [Directory](https://docs.microsoft.com/dotnet/api/system.io.directory), [File](https://docs.microsoft.com/dotnet/api/system.io.file) und **FileStream**, die Sie stattdessen in Ihrem Spiel verwenden können.</span><span class="sxs-lookup"><span data-stu-id="55b8c-150">However, Unity does provide the [Directory](https://docs.microsoft.com/dotnet/api/system.io.directory), [File](https://docs.microsoft.com/dotnet/api/system.io.file), and **FileStream** types so you can use them in your game.</span></span>

<span data-ttu-id="55b8c-151">Sie können auch die [Windows.Storage](https://docs.microsoft.com/uwp/api/Windows.Storage)-APIs verwenden, die nur für UWP-Apps verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="55b8c-151">Alternatively, you can use the [Windows.Storage](https://docs.microsoft.com/uwp/api/Windows.Storage) APIs, which are only available to UWP apps.</span></span> <span data-ttu-id="55b8c-152">Diese APIs beschränken die App jedoch auf das Schreiben in ihren spezifischen Speicher und gewähren ihr keinen freien Zugriff auf das gesamte Dateisystem.</span><span class="sxs-lookup"><span data-stu-id="55b8c-152">However, these APIs restrict the app to writing to their specific storage, and do not give it free access to the entire file system.</span></span> <span data-ttu-id="55b8c-153">Weitere Informationen finden Sie unter [Dateien, Ordner und Bibliotheken](https://docs.microsoft.com/windows/uwp/files/).</span><span class="sxs-lookup"><span data-stu-id="55b8c-153">See [Files, folders, and libraries](https://docs.microsoft.com/windows/uwp/files/) for more information.</span></span>

<span data-ttu-id="55b8c-154">Wichtiger Hinweis: Die Methode [Close](https://docs.microsoft.com/dotnet/api/system.io.stream.close) ist nur im .NET-Standard 2.0 und höheren Versionen verfügbar (obwohl Unity eine Erweiterungsmethode enthält).</span><span class="sxs-lookup"><span data-stu-id="55b8c-154">One important note is that the [Close](https://docs.microsoft.com/dotnet/api/system.io.stream.close) method is only available in .NET Standard 2.0 and later (though Unity provides an extension method).</span></span> <span data-ttu-id="55b8c-155">Verwenden Sie stattdessen [Dispose](https://docs.microsoft.com/dotnet/api/system.io.stream.dispose).</span><span class="sxs-lookup"><span data-stu-id="55b8c-155">Use [Dispose](https://docs.microsoft.com/dotnet/api/system.io.stream.dispose) instead.</span></span>

### <a name="threading"></a><span data-ttu-id="55b8c-156">Threading</span><span class="sxs-lookup"><span data-stu-id="55b8c-156">Threading</span></span>

<span data-ttu-id="55b8c-157">Einige Typen im Namespace [System.Threading](https://docs.microsoft.com/dotnet/api/system.threading) sind in früheren Versionen des .NET-Standards nicht verfügbar, z.B. [ThreadPool](https://docs.microsoft.com/dotnet/api/system.threading.threadpool).</span><span class="sxs-lookup"><span data-stu-id="55b8c-157">Some types in the [System.Threading](https://docs.microsoft.com/dotnet/api/system.threading) namespaces, such as [ThreadPool](https://docs.microsoft.com/dotnet/api/system.threading.threadpool), are not available in earlier versions of the .NET Standard.</span></span> <span data-ttu-id="55b8c-158">In diesen Fällen können Sie stattdessen den Namespace [Windows.System.Threading](https://docs.microsoft.com/uwp/api/windows.system.threading) verwenden.</span><span class="sxs-lookup"><span data-stu-id="55b8c-158">In these cases, you can use the [Windows.System.Threading](https://docs.microsoft.com/uwp/api/windows.system.threading) namespace instead.</span></span>

<span data-ttu-id="55b8c-159">So können Sie das Threading in einem Unity-Spiel anwenden und mithilfe der plattformabhängigen Kompilierung sowohl auf UWP- als auch auf Nicht-UWP-Plattformen abzielen:</span><span class="sxs-lookup"><span data-stu-id="55b8c-159">Here's how you could handle threading in a Unity game, using platform-dependent compilation to prepare for both UWP and non-UWP platforms:</span></span>

```csharp
private void UsingThreads()
{
#if NETFX_CORE
    Windows.System.Threading.ThreadPool.RunAsync(workItem => SomeMethod());
#else
    System.Threading.ThreadPool.QueueUserWorkItem(workItem => SomeMethod());
#endif
}
```

### <a name="security"></a><span data-ttu-id="55b8c-160">Sicherheit</span><span class="sxs-lookup"><span data-stu-id="55b8c-160">Security</span></span>

<span data-ttu-id="55b8c-161">Einige der \*\*System.Security.\*\*\*-Namespaces, z.B. [System.Security.Cryptography.X509Certificates](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates?view=netstandard-2.0), sind nicht verfügbar, wenn Sie ein Unity-Spiel für UWP erstellen.</span><span class="sxs-lookup"><span data-stu-id="55b8c-161">Some of the **System.Security.**\* namespaces, such as [System.Security.Cryptography.X509Certificates](https://docs.microsoft.com/dotnet/api/system.security.cryptography.x509certificates?view=netstandard-2.0), are not available when you build a Unity game for UWP.</span></span> <span data-ttu-id="55b8c-162">Verwenden Sie in diesen Fällen die \*\*Windows.Security.\*\*\*-APIs, die die gleichen Funktionen behandelt.</span><span class="sxs-lookup"><span data-stu-id="55b8c-162">In these cases, use the **Windows.Security.**\* APIs, which cover much of the same functionality.</span></span>

<span data-ttu-id="55b8c-163">Das folgende Beispiel erhält die Zertifikate aus einem Zertifikatspeicher mit dem angegebenen Namen:</span><span class="sxs-lookup"><span data-stu-id="55b8c-163">The following example simply gets the certificates from a certificate store with the given name:</span></span>

```cs
private async void GetCertificatesAsync(string certStoreName)
    {
#if NETFX_CORE
        IReadOnlyList<Certificate> certs = await CertificateStores.FindAllAsync();
        IEnumerable<Certificate> myCerts = 
            certs.Where((certificate) => certificate.StoreName == certStoreName);
#else
        X509Store store = new X509Store(certStoreName, StoreLocation.CurrentUser);
        store.Open(OpenFlags.OpenExistingOnly);
        X509Certificate2Collection certs = store.Certificates;
#endif
    }
```

<span data-ttu-id="55b8c-164">Weitere Informationen zur Verwendung von WinRT Sicherheits-APIs finden Sie unter [Sicherheit](https://docs.microsoft.com/windows/uwp/security/).</span><span class="sxs-lookup"><span data-stu-id="55b8c-164">See [Security](https://docs.microsoft.com/windows/uwp/security/) for more information about using the WinRT security APIs.</span></span>

### <a name="networking"></a><span data-ttu-id="55b8c-165">Networking</span><span class="sxs-lookup"><span data-stu-id="55b8c-165">Networking</span></span>

<span data-ttu-id="55b8c-166">Einige der \*\*System&period;Net.\*\*\*-Namespaces, z.B. [System.Net. Mail](https://docs.microsoft.com/dotnet/api/system.net.mail?view=netstandard-2.0), sind ebenfalls nicht verfügbar, um ein Unity-Spiel für UWP zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="55b8c-166">Some of the **System&period;Net.**\* namespaces, such as [System.Net.Mail](https://docs.microsoft.com/dotnet/api/system.net.mail?view=netstandard-2.0), are also not available when building a Unity game for UWP.</span></span> <span data-ttu-id="55b8c-167">Für die meisten dieser APIs, verwenden Sie die entsprechenden **Windows.Networking.**\* und \*\*Windows.Web.\*\*\*-WinRT-APIs, um ähnliche Funktionen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="55b8c-167">For most of these APIs, use the corresponding **Windows.Networking.**\* and **Windows.Web.**\* WinRT APIs to get similar functionality.</span></span> <span data-ttu-id="55b8c-168">Weitere Informationen finden Sie unter [Netzwerk und Webdienste](https://docs.microsoft.com/windows/uwp/networking/).</span><span class="sxs-lookup"><span data-stu-id="55b8c-168">See [Networking and web services](https://docs.microsoft.com/windows/uwp/networking/) for more information.</span></span>

<span data-ttu-id="55b8c-169">Im Fall von **System.Net. Mail**, verwenden Sie den [Windows.ApplicationModel.Email](https://docs.microsoft.com/uwp/api/windows.applicationmodel.email)-Namespace.</span><span class="sxs-lookup"><span data-stu-id="55b8c-169">In the case of **System.Net.Mail**, use the [Windows.ApplicationModel.Email](https://docs.microsoft.com/uwp/api/windows.applicationmodel.email) namespace.</span></span> <span data-ttu-id="55b8c-170">Weitere Informationen finden Sie unter [E-Mail senden](https://docs.microsoft.com/windows/uwp/contacts-and-calendar/sending-email).</span><span class="sxs-lookup"><span data-stu-id="55b8c-170">See [Send email](https://docs.microsoft.com/windows/uwp/contacts-and-calendar/sending-email) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="55b8c-171">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="55b8c-171">See also</span></span>

* [<span data-ttu-id="55b8c-172">Universelle Windows-Plattform: Fehlende .NET-Typen im .NET Scripting-Backend</span><span class="sxs-lookup"><span data-stu-id="55b8c-172">Universal Windows Platform: Missing .NET Types on .NET Scripting Backend</span></span>](https://docs.unity3d.com/Manual/windowsstore-missingtypes.html)
* [<span data-ttu-id="55b8c-173">Überblick über .NET für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="55b8c-173">.NET for UWP apps overview</span></span>](https://msdn.microsoft.com/library/windows/apps/br230302)
* [<span data-ttu-id="55b8c-174">Handbücher zum Portieren für Unity und UWP</span><span class="sxs-lookup"><span data-stu-id="55b8c-174">Unity UWP porting guides</span></span>](https://unity3d.com/partners/microsoft/porting-guides)