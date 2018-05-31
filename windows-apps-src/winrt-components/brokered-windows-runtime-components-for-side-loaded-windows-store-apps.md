---
author: msatranjr
title: Vermittelte Komponenten für Windows-Runtime für eine quergeladene UWP-App
description: In diesem Dokument wird ein Unternehmensfeature beschrieben, das von Windows10 unterstützt wird und .NET-Apps mit Toucheingabemöglichkeit die Verwendung von vorhandenem Code ermöglicht, der für wichtige unternehmenskritische Vorgänge verantwortlich ist.
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.assetid: 81b3930c-6af9-406d-9d1e-8ee6a13ec38a
ms.localizationpriority: medium
ms.openlocfilehash: 71fd511a109022d265d13b575bd696e8c346567b
ms.sourcegitcommit: ab92c3e0dd294a36e7f65cf82522ec621699db87
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "1832401"
---
# <a name="brokered-windows-runtime-components-for-a-side-loaded-uwp-app"></a><span data-ttu-id="af1c5-104">Vermittelte Komponenten für Windows-Runtime für eine quergeladene UWP-App</span><span class="sxs-lookup"><span data-stu-id="af1c5-104">Brokered Windows Runtime Components for a side-loaded UWP app</span></span>

<span data-ttu-id="af1c5-105">In diesem Artikel wird ein Unternehmensfeature beschrieben, das von Windows10 unterstützt wird und .NET-Apps mit Toucheingabemöglichkeit die Verwendung von vorhandenem Code ermöglicht, der für wichtige unternehmenskritische Vorgänge verantwortlich ist.</span><span class="sxs-lookup"><span data-stu-id="af1c5-105">This article discusses an enterprise-targeted feature supported by Windows 10, which allows touch-friendly .NET apps to use the existing code responsible for key business-critical operations.</span></span>

## <a name="introduction"></a><span data-ttu-id="af1c5-106">Einführung</span><span class="sxs-lookup"><span data-stu-id="af1c5-106">Introduction</span></span>

><span data-ttu-id="af1c5-107">**Hinweis:**  Der Beispielcode in diesem Dokument kann für [Visual Studio2015 und 2017](https://aka.ms/brokeredsample) heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="af1c5-107">**Note**  The sample code that accompanies this paper may be downloaded for [Visual Studio 2015 & 2017](https://aka.ms/brokeredsample).</span></span> <span data-ttu-id="af1c5-108">Die Microsoft Visual Studio-Vorlage für das Erstellen vermittelter Komponenten für Windows-Runtime kann hier heruntergeladen werden: [Visual Studio 2015-Vorlage für universelle Windows-Apps für Windows10](https://visualstudiogallery.msdn.microsoft.com/10be07b3-67ef-4e02-9243-01b78cd27935).</span><span class="sxs-lookup"><span data-stu-id="af1c5-108">The Microsoft Visual Studio template to build Brokered Windows Runtime Components can be downloaded here: [Visual Studio 2015 template targeting Universal Windows Apps for Windows 10](https://visualstudiogallery.msdn.microsoft.com/10be07b3-67ef-4e02-9243-01b78cd27935)</span></span>

<span data-ttu-id="af1c5-109">Windows enthält ein neues Feature namens *Vermittelte Windows-Runtime-Komponenten für quergeladene Anwendungen*.</span><span class="sxs-lookup"><span data-stu-id="af1c5-109">Windows includes a new feature called *Brokered Windows Runtime Components for side-loaded applications*.</span></span> <span data-ttu-id="af1c5-110">Wir verwenden den Begriff „prozessübergreifende Kommunikation“ (Inter-Process Communication, IPC), um die Fähigkeit zu beschreiben, vorhandene Desktopsoftwareressourcen in einem einzigen Prozess (Desktopkomponente) auszuführen und gleichzeitig mit diesem Code in einer UWP-App zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="af1c5-110">We use the term IPC (inter-process communication) to describe the ability to run existing desktop software assets in one process (desktop component) while interacting with this code in a UWP App.</span></span> <span data-ttu-id="af1c5-111">Dieses Modell ist Unternehmensentwicklern vertraut, da Datenbankanwendungen und Anwendungen, die NT-Dienste unter Windows verwenden, eine ähnliche, aus mehreren Prozessen bestehende Architektur verwenden.</span><span class="sxs-lookup"><span data-stu-id="af1c5-111">This is a familiar model to enterprise developers as database applications and applications utilizing NT Services in Windows share a similar multi-process architecture.</span></span>

<span data-ttu-id="af1c5-112">Das Querladen der App ist eine kritische Komponente dieses Features.</span><span class="sxs-lookup"><span data-stu-id="af1c5-112">Side-loading of the app is a critical component of this feature.</span></span>
<span data-ttu-id="af1c5-113">Unternehmensspezifische Anwendungen gehören nicht in den allgemeinen Microsoft Store für Verbraucher, und Unternehmen besitzen sehr spezielle Anforderungen hinsichtlich Sicherheit, Datenschutz, Verteilung, Einrichtung und Wartung.</span><span class="sxs-lookup"><span data-stu-id="af1c5-113">Enterprise-specific applications have no place in the general consumer Microsoft Store and corporations have very specific requirements around security, privacy, distribution, setup, and servicing.</span></span> <span data-ttu-id="af1c5-114">Das Querlademodell ist daher als solches eine Anforderung derer, die dieses Feature verwenden, und ein wichtiges Implementierungsdetail.</span><span class="sxs-lookup"><span data-stu-id="af1c5-114">As such, the side-loading model is both a requirement of those who would use this feature and a critical implementation detail.</span></span>

<span data-ttu-id="af1c5-115">Auf Daten ausgerichtete Anwendungen sind ein Hauptziel für diese Anwendungsarchitektur.</span><span class="sxs-lookup"><span data-stu-id="af1c5-115">Data-centric applications are a key target for this application architecture.</span></span> <span data-ttu-id="af1c5-116">Es ist vorgesehen, dass vorhandene Unternehmensregeln, die beispielsweise in SQL Server integriert sind, ein häufig verwendeter Teil der Desktopkomponente sind.</span><span class="sxs-lookup"><span data-stu-id="af1c5-116">It is envisioned that existing business rules ensconced, for example, in SQL Server, will be a common part of the desktop component.</span></span> <span data-ttu-id="af1c5-117">Dies ist sicher nicht die einzige Art von Funktionalität, die die Desktopkomponente bietet, aber ein großer Teil der Notwendigkeit dieses Features beruht auf vorhandenen Daten und Unternehmenslogiken.</span><span class="sxs-lookup"><span data-stu-id="af1c5-117">This is certainly not the only type of functionality that can be proffered by the desktop component, but a large part of the demand for this feature is related to existing data and business logic.</span></span>

<span data-ttu-id="af1c5-118">Da in der Unternehmensentwicklung die .NET-Laufzeit und die Sprache C\# deutlich vorherrschen, wurde dieses Feature unter Betonung auf der Verwendung von .NET für die UWP-App und die Desktopkomponente entwickelt.</span><span class="sxs-lookup"><span data-stu-id="af1c5-118">Lastly, given the overwhelming penetration of the .NET runtime and the C\# language in enterprise development, this feature was developed with an emphasis on using .NET for both the UWP app and the desktop component sides.</span></span> <span data-ttu-id="af1c5-119">Es können zwar auch andere Sprachen und Laufzeiten für die UWP-App verwendet werden, aber das begleitende Beispiel zeigt lediglich C\# und ist ausschließlich auf die .NET-Laufzeit beschränkt.</span><span class="sxs-lookup"><span data-stu-id="af1c5-119">While there are other languages and runtimes possible for the UWP app, the accompanying sample only illustrates C\#, and is restricted to the .NET runtime exclusively.</span></span>

## <a name="application-components"></a><span data-ttu-id="af1c5-120">Anwendungskomponenten</span><span class="sxs-lookup"><span data-stu-id="af1c5-120">Application components</span></span>

><span data-ttu-id="af1c5-121">**Hinweis**  Dieses Feature ist ausschließlich für die Verwendung von .NET bestimmt.</span><span class="sxs-lookup"><span data-stu-id="af1c5-121">**Note**  This feature is exclusively for the use of .NET.</span></span> <span data-ttu-id="af1c5-122">Sowohl die Client-App als auch die Desktopkomponente müssen mit .NET erstellt worden sein.</span><span class="sxs-lookup"><span data-stu-id="af1c5-122">Both client app and the desktop component must be authored using .NET.</span></span>

**<span data-ttu-id="af1c5-123">Anwendungsmodell</span><span class="sxs-lookup"><span data-stu-id="af1c5-123">Application model</span></span>**

<span data-ttu-id="af1c5-124">Dieses Feature basiert auf der allgemeinen Anwendungsarchitektur, die als MVVM (Model View View-Model) bekannt ist.</span><span class="sxs-lookup"><span data-stu-id="af1c5-124">This feature is built around the general application architecture known as MVVM (Model View View-Model).</span></span> <span data-ttu-id="af1c5-125">Daher wird angenommen, dass sich das „Modell“ vollständig in der Desktopkomponente befindet.</span><span class="sxs-lookup"><span data-stu-id="af1c5-125">As such, it is assumed that the "model" is housed entirely in the desktop component.</span></span> <span data-ttu-id="af1c5-126">Daher sollte sofort offensichtlich sein, dass die Desktopkomponente „kopflos“ ist (d.h., sie enthält keine Benutzeroberfläche).</span><span class="sxs-lookup"><span data-stu-id="af1c5-126">Therefore, it should be immediately obvious that the desktop component will be "headless" (i.e. contains no UI).</span></span> <span data-ttu-id="af1c5-127">Die Ansicht ist komplett in der quergeladenen Unternehmensanwendung enthalten.</span><span class="sxs-lookup"><span data-stu-id="af1c5-127">The view will be entirely contained in the side-loaded enterprise application.</span></span> <span data-ttu-id="af1c5-128">Auch wenn es keine Anforderung gibt, dass diese Anwendung auf dem „Ansichtsmodell“-Konstrukt (View-Model-Konstrukt) basiert, gehen wir davon aus, dass dieses Muster allgemein verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="af1c5-128">While there is no requirement that this application be built with the "view-model" construct, we anticipate that usage of this pattern will be common.</span></span>

**<span data-ttu-id="af1c5-129">Desktopkomponente</span><span class="sxs-lookup"><span data-stu-id="af1c5-129">Desktop component</span></span>**

<span data-ttu-id="af1c5-130">Bei der Desktopkomponente in diesem Feature handelt es sich um einen neuen Anwendungstyp, der als Teil dieses Features eingeführt wird.</span><span class="sxs-lookup"><span data-stu-id="af1c5-130">The desktop component in this feature is a new application type being introduced as part of this feature.</span></span> <span data-ttu-id="af1c5-131">Diese Desktopkomponente kann nur in C\# geschrieben werden und muss auf .NET4.6 oder höher für Windows10 ausgerichtet sein.</span><span class="sxs-lookup"><span data-stu-id="af1c5-131">This desktop component can only be written in C\# and must target .NET 4.6 or greater for Windows 10.</span></span> <span data-ttu-id="af1c5-132">Der Projekttyp ist ein Hybrid für die Common Language Runtime (CLR) für UWP, da das Format für die prozessübergreifende Kommunikation UWP-Typen und -Klassen enthält, während die Desktopkomponente alle Teile der .NET-Laufzeit-Klassenbibliothek aufrufen darf.</span><span class="sxs-lookup"><span data-stu-id="af1c5-132">The project type is a hybrid between the CLR targeting UWP as the inter-process communication format comprises UWP types and classes, while the desktop component is allowed to call all parts of the .NET runtime class library.</span></span> <span data-ttu-id="af1c5-133">Die Auswirkungen auf das Visual Studio-Projekt werden später ausführlich beschrieben.</span><span class="sxs-lookup"><span data-stu-id="af1c5-133">The impact on the Visual Studio project will be described in detail later.</span></span> <span data-ttu-id="af1c5-134">Diese Hybridkonfiguration ermöglicht den Aufruf von UWP-Typen für die auf den Desktopkomponenten basierenden Anwendung, während gleichzeitig der Desktop-CLR-Code innerhalb der Desktopkomponentenimplementierung aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="af1c5-134">This hybrid configuration allows marshaling UWP types between the application built on the desktop components while allowing desktop CLR code to be called inside the desktop component implementation.</span></span>

**<span data-ttu-id="af1c5-135">Vertrag</span><span class="sxs-lookup"><span data-stu-id="af1c5-135">Contract</span></span>**

<span data-ttu-id="af1c5-136">Der Vertrag zwischen der quergeladenen Anwendung und der Desktopkomponente wird mithilfe des UWP-Typsystems beschrieben.</span><span class="sxs-lookup"><span data-stu-id="af1c5-136">The contract between the side-loaded application and the desktop component is described in terms of the UWP type system.</span></span> <span data-ttu-id="af1c5-137">Dies umfasst die Deklarierung mindestens einer C\#-Klasse, die eine UWP darstellen kann.</span><span class="sxs-lookup"><span data-stu-id="af1c5-137">This involves declaring one or more C\# classes that can represent a UWP.</span></span> <span data-ttu-id="af1c5-138">Weitere Informationen zu bestimmten Anforderungen im Zusammenhang mit dem Erstellen von Windows-Runtime-Klassen mit C\# finden Sie im MSDN-Thema [Erstellen von Komponenten für Windows-Runtime in C# und Visual Basic](https://msdn.microsoft.com/library/br230301.aspx).</span><span class="sxs-lookup"><span data-stu-id="af1c5-138">See MSDN topic [Creating Windows Runtime Components in C\# and Visual Basic](https://msdn.microsoft.com/library/br230301.aspx) for specific requirement of creating Windows Runtime Class using C\#.</span></span>

><span data-ttu-id="af1c5-139">**Hinweis**  Enumerationen werden im Vertrag für Windows-Runtime-Komponenten zwischen Desktopkomponente und quergeladener Anwendung zu diesem Zeitpunkt nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="af1c5-139">**Note**  Enums are not supported in the Windows Runtime Components Contract between desktop component and side-loaded application at this time.</span></span>

**<span data-ttu-id="af1c5-140">Quergeladene Anwendung</span><span class="sxs-lookup"><span data-stu-id="af1c5-140">Side-loaded application</span></span>**

<span data-ttu-id="af1c5-141">Bei der quergeladenen Anwendung handelt es sich in jeder Hinsicht um eine normale UWP-App, mit einer Ausnahme: Sie wird quergeladen und nicht über den Microsoft Store installiert.</span><span class="sxs-lookup"><span data-stu-id="af1c5-141">The side-loaded application is a normal UWP app in every respect except one: it is side-loaded instead of installed via the Microsoft Store.</span></span> <span data-ttu-id="af1c5-142">Viele der Installationsmechanismen sind identisch: Das Manifest und das Anwendungspaket ähneln sich (ein Zusatz zum Manifest wird später ausführlich erläutert).</span><span class="sxs-lookup"><span data-stu-id="af1c5-142">Most of the installation mechanisms are identical: the manifest and application packaging are similar (one addition to the manifest is described in detail later).</span></span> <span data-ttu-id="af1c5-143">Nach der Aktivierung des Querladens kann ein einfaches PowerShell-Skript die erforderlichen Zertifikate und die Anwendung selbst installieren.</span><span class="sxs-lookup"><span data-stu-id="af1c5-143">Once side-loading is enabled, a simple PowerShell script can install the necessary certificates and the application itself.</span></span> <span data-ttu-id="af1c5-144">Normalerweise besteht die bewährte Methode darin, dass die quergeladene Anwendung den WACK-Zertifizierungstest durchläuft, der in Visual Studio im Menü „Projekt/Store“ enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="af1c5-144">It is the normal best practice that the side-loaded application passes the WACK certification test that is included in the Project / Store menu in Visual Studio</span></span>

><span data-ttu-id="af1c5-145">**Hinweis**  Das Querladen kann in „Einstellungen &gt; Update & Sicherheit &gt; Für Entwickler“ aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="af1c5-145">**Note** Side-loading can be turned on in Settings-&gt; Update & security -&gt; For developers.</span></span>

<span data-ttu-id="af1c5-146">Es muss unbedingt angemerkt werden, dass der im Lieferumfang von Windows10 enthaltene App-Broker nur als 32-Bit-Version vorliegt.</span><span class="sxs-lookup"><span data-stu-id="af1c5-146">One important point to note is that the App Broker mechanism shipped as part of Windows 10 is 32-bit only.</span></span> <span data-ttu-id="af1c5-147">Die Desktopkomponente muss eine 32-Bit-Version sein.</span><span class="sxs-lookup"><span data-stu-id="af1c5-147">The desktop component must be 32-bit.</span></span>
<span data-ttu-id="af1c5-148">Quergeladene Anwendungen können als 64-Bit-Version vorliegen (vorausgesetzt, dass 64-Bit- und 32-Bit-Proxys registriert sind), aber dies wäre untypisch.</span><span class="sxs-lookup"><span data-stu-id="af1c5-148">Side-loaded applications can be 64-bit (provided there is both a 64-bit and 32-bit proxies registered), but this will be atypical.</span></span> <span data-ttu-id="af1c5-149">Beim Erstellen von quergeladenen Anwendungen in C\# mithilfe der normalen „neutralen“ Konfiguration und dem bevorzugten 32-Bit-Standard werden natürlich quergeladene 32-Bit-Anwendungen erstellt.</span><span class="sxs-lookup"><span data-stu-id="af1c5-149">Building the side-loaded application in C\# using the normal "neutral" configuration and the "prefer 32-bit" default naturally creates 32-bit side-loaded applications.</span></span>

**<span data-ttu-id="af1c5-150">Serverinstanzerstellung und AppDomains</span><span class="sxs-lookup"><span data-stu-id="af1c5-150">Server instancing and AppDomains</span></span>**

<span data-ttu-id="af1c5-151">Jede quergeladene Anwendung erhält eine eigene Instanz eines App-Broker-Servers (so genannte „Multiinstanzerstellung“).</span><span class="sxs-lookup"><span data-stu-id="af1c5-151">Each sided-loaded application receives its own instance of an App Broker server (so-called "multi-instancing").</span></span> <span data-ttu-id="af1c5-152">Der Servercode wird innerhalb einer einzelnen AppDomain ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="af1c5-152">The server code runs inside of a single AppDomain.</span></span> <span data-ttu-id="af1c5-153">Dadurch können mehrere Bibliotheksversionen in separaten Instanzen ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="af1c5-153">This allows for having multiple version of libraries run in separate instances.</span></span> <span data-ttu-id="af1c5-154">Beispielsweise benötigt Anwendung A die Version V1.1 einer Komponente, und Anwendung B benötigt Version V2.</span><span class="sxs-lookup"><span data-stu-id="af1c5-154">For example, application A needs V1.1 of a component and application B needs V2.</span></span> <span data-ttu-id="af1c5-155">Diese werden sauber voneinander getrennt, indem V1.1- und V2-Komponenten in separaten Serververzeichnissen gespeichert werden und die Anwendung auf den Server verweist, der die gewünschte Version unterstützt.</span><span class="sxs-lookup"><span data-stu-id="af1c5-155">These are cleanly separated by having V1.1 and V2 components in separate server directories and pointing the application to whichever server supports the correct version desired.</span></span>

<span data-ttu-id="af1c5-156">Die Servercodeimplementierung kann auf mehrere App-Broker-Serverinstanzen verteilt werden, indem mehrere Anwendungen auf dasselbe Serververzeichnis verweisen.</span><span class="sxs-lookup"><span data-stu-id="af1c5-156">Server code implementation can be shared amongst multiple App Broker server instance by pointing multiple applications to the same server directory.</span></span> <span data-ttu-id="af1c5-157">Es sind nach wie vor mehrere Instanzen des App-Broker-Servers vorhanden, auf ihnen wird jedoch identischer Code ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="af1c5-157">There will still be multiple instances of the App Broker server but they will be running identical code.</span></span> <span data-ttu-id="af1c5-158">Alle in einer einzelnen Anwendung verwendeten Implementierungskomponenten sollten sich unter demselben Pfad befinden.</span><span class="sxs-lookup"><span data-stu-id="af1c5-158">All implementation components used in a single application should be present in the same path.</span></span>

## <a name="defining-the-contract"></a><span data-ttu-id="af1c5-159">Definieren des Vertrags</span><span class="sxs-lookup"><span data-stu-id="af1c5-159">Defining the contract</span></span>

<span data-ttu-id="af1c5-160">Der erste Schritt beim Erstellen einer Anwendung mithilfe dieses Features besteht darin, einen Vertrag zwischen der quergeladenen Anwendung und der Desktopkomponente zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="af1c5-160">The first step in creating an application using this feature is to create the contract between the side-loaded application and the desktop component.</span></span> <span data-ttu-id="af1c5-161">Dies darf nur mit Windows-Runtime-Typen erfolgen.</span><span class="sxs-lookup"><span data-stu-id="af1c5-161">This must be done exclusively using Windows Runtime types.</span></span>
<span data-ttu-id="af1c5-162">Glücklicherweise können diese mithilfe von C\#-Klassen einfach deklariert werden.</span><span class="sxs-lookup"><span data-stu-id="af1c5-162">Fortunately, these are easy to declare using C\# classes.</span></span> <span data-ttu-id="af1c5-163">Es gibt wichtige jedoch wichtige Überlegungen hinsichtlich der Leistung, wenn diese Konversationen definiert werden, die in einem späteren Abschnitt behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="af1c5-163">There are important performance considerations, however, when defining these conversations, which is covered in a later section.</span></span>

<span data-ttu-id="af1c5-164">Die Sequenz zum Definieren des Vertrags wird wie folgt eingeführt:</span><span class="sxs-lookup"><span data-stu-id="af1c5-164">The sequence to define the contract is introduced as following:</span></span>

<span data-ttu-id="af1c5-165">**Schritt1:** Erstellen Sie in Visual Studio eine neue Klassenbibliothek.</span><span class="sxs-lookup"><span data-stu-id="af1c5-165">**Step 1:** Create a new class library in Visual Studio.</span></span> <span data-ttu-id="af1c5-166">Stellen Sie sicher, dass Sie das Projekt mit der Klassenbibliotheksvorlage und nicht mit der Windows-Runtime-Komponentenvorlage erstellen.</span><span class="sxs-lookup"><span data-stu-id="af1c5-166">Make sure to create the project using Class Library template not Windows Runtime Component template</span></span>

<span data-ttu-id="af1c5-167">In der Regel folgt an dieser Stelle eine Implementierung, in diesem Abschnitt wird jedoch lediglich die Definition des prozessübergreifenden Vertrags erläutert.</span><span class="sxs-lookup"><span data-stu-id="af1c5-167">An implementation obviously follows, but this section is only covering the definition of the inter-process contract.</span></span> <span data-ttu-id="af1c5-168">Das Begleitbeispiel enthält die folgende Klasse (EnterpriseServer.cs), deren Anfangsform wie folgt aussieht:</span><span class="sxs-lookup"><span data-stu-id="af1c5-168">The accompanying sample includes the following class (EnterpriseServer.cs), the beginning shape of which looks like:</span></span>

```csharp
namespace Fabrikam
{
    public sealed class EnterpriseServer
    {

        public ILis<String> TestMethod(String input)
        {
            throw new NotImplementedException();
        }
        
        public IAsyncOperation<int> FindElementAsync(int input)
        {
            throw new NotImplementedException();
        }
        
        public string[] RetrieveData()
        {
            throw new NotImplementedException();
        }
        
        public event EventHandler<string> PeriodicEvent;
    }
}
```

<span data-ttu-id="af1c5-169">Hierdurch wird die Klasse „EnterpriseServer“ definiert, die von der quergeladenen Anwendung instanziiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="af1c5-169">This defines a class "EnterpriseServer" that can be instantiated from the side-loaded application.</span></span> <span data-ttu-id="af1c5-170">Diese Klasse stellt die in der RuntimeClass zugesagte Funktionalität bereit.</span><span class="sxs-lookup"><span data-stu-id="af1c5-170">This class provides the functionality promised in the RuntimeClass.</span></span> <span data-ttu-id="af1c5-171">Die RuntimeClass kann verwendet werden, um die WINMD-Verweisdatei zu generieren, die Bestandteil der quergeladenen Anwendung ist.</span><span class="sxs-lookup"><span data-stu-id="af1c5-171">The RuntimeClass can be used to generate the reference winmd that will be included in the side-loaded application.</span></span>

<span data-ttu-id="af1c5-172">**Schritt2:** Bearbeiten Sie die Projektdatei manuell, um den Ausgabetyp des Projekts in „Windows-Runtime-Komponente“ zu ändern.</span><span class="sxs-lookup"><span data-stu-id="af1c5-172">**Step 2:** Edit the project file manually to change the output type of project to Windows Runtime Component</span></span>

<span data-ttu-id="af1c5-173">Klicken Sie dazu in Visual Studio mit der rechten Maustaste auf das neu erstellte Projekt, und wählen Sie „Projekt entladen“ aus. Klicken Sie anschließend erneut mit der rechten Maustaste, und wählen Sie „EnterpriseServer.csproj bearbeiten“ aus, um die Projektdatei, eine XML-Datei, für die Bearbeitung zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="af1c5-173">To do this in Visual Studio, right click on the newly created project and select “Unload Project”, then right click again and select “Edit EnterpriseServer.csproj” to open the project file, an XML file, for editing.</span></span>

<span data-ttu-id="af1c5-174">Suchen Sie in der geöffneten Datei das Tag \<OutputType\>, und ändern Sie den Wert in „Winmdobj“.</span><span class="sxs-lookup"><span data-stu-id="af1c5-174">In the opened file, search for the \<OutputType\> tag and change its value to “winmdobj”.</span></span>

<span data-ttu-id="af1c5-175">**Schritt3:** Erstellen Sie eine Buildregel, die eine Windows-Metadatendatei (WINMD-Datei) als „Verweis“ erstellt.</span><span class="sxs-lookup"><span data-stu-id="af1c5-175">**Step 3:** Create a build rule that creates a "reference" Windows metadata file (.winmd file).</span></span> <span data-ttu-id="af1c5-176">Das bedeutet, es gibt keine Implementierung.</span><span class="sxs-lookup"><span data-stu-id="af1c5-176">i.e. has no implementation.</span></span>

<span data-ttu-id="af1c5-177">**Schritt4:** Erstellen Sie eine Buildregel, die eine Windows-Metadatendatei für die „Implementierung“ erstellt, d.h., sie enthält dieselben Metadateninformationen und dazu die Implementierung.</span><span class="sxs-lookup"><span data-stu-id="af1c5-177">**Step 4:** Create a build rule that creates an "implementation" Windows metadata file, i.e. has the same metadata information, but also includes the implementation.</span></span>

<span data-ttu-id="af1c5-178">Dies erfolgt durch die folgenden Skripts.</span><span class="sxs-lookup"><span data-stu-id="af1c5-178">This will is done by the following scripts.</span></span> <span data-ttu-id="af1c5-179">Fügen Sie die Skripts der Befehlszeile nach dem Build-Ereignis im Projekt **Eigenschaften** > **Buildereignisse** hinzu.</span><span class="sxs-lookup"><span data-stu-id="af1c5-179">Add the scripts to the Post-build event command line, in project **Properties** > **Build Events**.</span></span>

> <span data-ttu-id="af1c5-180">**Hinweis**  Das Skript unterscheidet sich abhängig von der Version von Windows, auf die Sie abzielen (Windows10) und der verwendeten Version von Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="af1c5-180">**Note** the script is different based on the version of Windows you are targeting (Windows 10) and the version of Visual Studio in use.</span></span>

**<span data-ttu-id="af1c5-181">VisualStudio2015</span><span class="sxs-lookup"><span data-stu-id="af1c5-181">Visual Studio 2015</span></span>**
```cmd
    call "$(DevEnvDir)..\..\vc\vcvarsall.bat" x86 10.0.14393.0

    md "$(TargetDir)"\impl    md "$(TargetDir)"\reference

    erase "$(TargetDir)\impl\*.winmd"
    erase "$(TargetDir)\impl\*.pdb"
    rem erase "$(TargetDir)\reference\*.winmd"

    xcopy /y "$(TargetPath)" "$(TargetDir)impl"
    xcopy /y "$(TargetDir)*.pdb" "$(TargetDir)impl"

    winmdidl /nosystemdeclares /metadata_dir:C:\Windows\System32\Winmetadata "$(TargetPath)"

    midl /metadata_dir "%WindowsSdkDir%UnionMetadata" /iid "$(SolutionDir)BrokeredProxyStub\$(TargetName)_i.c" /env win32 /x86 /h   "$(SolutionDir)BrokeredProxyStub\$(TargetName).h" /winmd "$(TargetName).winmd" /W1 /char signed /nologo /winrt /dlldata "$(SolutionDir)BrokeredProxyStub\dlldata.c" /proxy "$(SolutionDir)BrokeredProxyStub\$(TargetName)_p.c"  "$(TargetName).idl"
    mdmerge -n 1 -i "$(ProjectDir)bin\$(ConfigurationName)" -o "$(TargetDir)reference" -metadata_dir "%WindowsSdkDir%UnionMetadata" -partial

    rem erase "$(TargetPath)"

```


**<span data-ttu-id="af1c5-182">VisualStudio2017</span><span class="sxs-lookup"><span data-stu-id="af1c5-182">Visual Studio 2017</span></span>**
```cmd
    call "$(DevEnvDir)..\..\vc\auxiliary\build\vcvarsall.bat" x86 10.0.16299.0

    md "$(TargetDir)"\impl
    md "$(TargetDir)"\reference

    erase "$(TargetDir)\impl\*.winmd"
    erase "$(TargetDir)\impl\*.pdb"
    rem erase "$(TargetDir)\reference\*.winmd"

    xcopy /y "$(TargetPath)" "$(TargetDir)impl"
    xcopy /y "$(TargetDir)*.pdb" "$(TargetDir)impl"

    winmdidl /nosystemdeclares /metadata_dir:C:\Windows\System32\Winmetadata "$(TargetPath)"

    midl /metadata_dir "%WindowsSdkDir%UnionMetadata" /iid "$(SolutionDir)BrokeredProxyStub\$(TargetName)_i.c" /env win32 /x86 /h "$(SolutionDir)BrokeredProxyStub\$(TargetName).h" /winmd "$(TargetName).winmd" /W1 /char signed /nologo /winrt /dlldata "$(SolutionDir)BrokeredProxyStub\dlldata.c" /proxy "$(SolutionDir)BrokeredProxyStub\$(TargetName)_p.c"  "$(TargetName).idl"
    mdmerge -n 1 -i "$(ProjectDir)bin\$(ConfigurationName)" -o "$(TargetDir)reference" -metadata_dir "%WindowsSdkDir%UnionMetadata" -partial

    rem erase "$(TargetPath)"
```

<span data-ttu-id="af1c5-183">Nachdem der Verweis **winmd** erstellt wurde (im Ordner „Verweis“ unterhalb des Zielordners für das Projekt), wird er manuell in jedes verarbeitende quergeladene Anwendungsprojekt kopiert und referenziert.</span><span class="sxs-lookup"><span data-stu-id="af1c5-183">Once the reference **winmd** is created (in folder “reference” under the project’s Target folder), it is hand carried (copied) to each consuming side-loaded application project and referenced.</span></span> <span data-ttu-id="af1c5-184">Dies wird im folgenden Abschnitt näher erläutert.</span><span class="sxs-lookup"><span data-stu-id="af1c5-184">This will be described further in the next section.</span></span> <span data-ttu-id="af1c5-185">Die in den oben erwähnten Buildregeln verkörperte Projektstruktur stellt sicher, dass sich die Implementierung und die **winmd**-Verweisdatei in klar getrennten Verzeichnissen in der Buildhierarchie befinden, um Verwirrung zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="af1c5-185">The project structure embodied in the build rules above ensure that the implementation and the reference **winmd** are in clearly segregated directories in the build hierarchy to avoid confusion.</span></span>

## <a name="side-loaded-applications-in-detail"></a><span data-ttu-id="af1c5-186">Quergeladene Anwendungen im Detail</span><span class="sxs-lookup"><span data-stu-id="af1c5-186">Side-loaded applications in detail</span></span>
<span data-ttu-id="af1c5-187">Wie bereits erwähnt, wird die quergeladene Anwendung genau wie jede andere UWP-App erstellt, aber es gibt ein zusätzliches Detail: das Deklarieren der Verfügbarkeit der RuntimeClass(es) im Manifest der quergeladenen Anwendung.</span><span class="sxs-lookup"><span data-stu-id="af1c5-187">As stated previously, the side-loaded application is built like any other UWP app, but there is one additional detail: declaring the availability of the RuntimeClass (es) in the side-loaded application's manifest.</span></span> <span data-ttu-id="af1c5-188">Dies ermöglicht der Anwendung das einfache Neuschreiben, um auf die Funktionalität in der Desktopkomponente zuzugreifen.</span><span class="sxs-lookup"><span data-stu-id="af1c5-188">This allows the application to simply write new to access the functionality in the desktop component.</span></span> <span data-ttu-id="af1c5-189">Ein Manifesteintrag im Abschnitt <Extension> beschreibt die in der Desktopkomponente implementierte RuntimeClass und enthält Informationen darüber, wo sie sich befindet.</span><span class="sxs-lookup"><span data-stu-id="af1c5-189">A new manifest entry in the <Extension> section describes the RuntimeClass implemented in the desktop component and information on where it is located.</span></span> <span data-ttu-id="af1c5-190">Diese Deklarationsinhalte im Manifest der Anwendung sind mit denen von Apps für Windows10 identisch.</span><span class="sxs-lookup"><span data-stu-id="af1c5-190">These declaration content in application’s manifest is the same for apps targeting Windows 10.</span></span> <span data-ttu-id="af1c5-191">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="af1c5-191">For example:</span></span>

```XML
<Extension Category="windows.activatableClass.inProcessServer">
    <InProcessServer>
        <Path>clrhost.dll</Path>
        <ActivatableClass ActivatableClassId="Fabrikam.EnterpriseServer" ThreadingModel="both">
            <ActivatableClassAttribute Name="DesktopApplicationPath" Type="string" Value="c:\test" />
        </ActivatableClass>
    </InProcessServer>
</Extension>
```

<span data-ttu-id="af1c5-192">Die Kategorie lautet „inProcessServer“, da die outOfProcessServer-Kategorie mehrere Einträge enthält, die für diese Anwendungskonfiguration nicht anwendbar sind.</span><span class="sxs-lookup"><span data-stu-id="af1c5-192">The category is inProcessServer because there are several entries in the outOfProcessServer category that are not applicable to this application configuration.</span></span> <span data-ttu-id="af1c5-193">Beachten Sie, dass die <Path>-Komponente stets „clrhost.dll“ enthalten muss (dies wird jedoch **nicht** erzwungen, und das Angeben eines anderen Werts führt zu einem undefinierten Fehler).</span><span class="sxs-lookup"><span data-stu-id="af1c5-193">Note that the <Path> component must always contain clrhost.dll (however this is **not** enforced and specifying a different value will fail in undefined ways).</span></span>

<span data-ttu-id="af1c5-194">Der <ActivatableClass>-Abschnitt entspricht einer echten prozessinternen RuntimeClass, die von einer Windows-Runtime-Komponente im App-Paket bevorzugt wird.</span><span class="sxs-lookup"><span data-stu-id="af1c5-194">The <ActivatableClass> section is the same as a true in-process RuntimeClass preferred by a Windows Runtime component in the app's package.</span></span> <ActivatableClassAttribute> <span data-ttu-id="af1c5-195">ist ein neues Element, und die Attribute Name="DesktopApplicationPath"" und Type="string" sind obligatorisch und unveränderlich.</span><span class="sxs-lookup"><span data-stu-id="af1c5-195">is a new element, and the attributes Name="DesktopApplicationPath" and Type="string" are mandatory and invariant.</span></span> <span data-ttu-id="af1c5-196">Das Value-Attribut verweist auf den Ort, an dem sich die winmd-Implementierungsdatei der Desktopkomponente befindet (weitere Einzelheiten hierzu finden Sie im folgenden Abschnitt).</span><span class="sxs-lookup"><span data-stu-id="af1c5-196">The Value attribute points to the location where the desktop component's implementation winmd resides (more detail on this in the next section).</span></span> <span data-ttu-id="af1c5-197">Jede von der Desktopkomponente bevorzugte RuntimeClass sollte eine eigene <ActivatableClass>-Elementstruktur besitzen.</span><span class="sxs-lookup"><span data-stu-id="af1c5-197">Each RuntimeClass preferred by the desktop component should have its own <ActivatableClass> element tree.</span></span> <span data-ttu-id="af1c5-198">Die ActivatableClassId muss dem vollständig qualifizierten Namespacenamen der RuntimeClass entsprechen.</span><span class="sxs-lookup"><span data-stu-id="af1c5-198">The ActivatableClassId must match the fully namespace-qualified name of the RuntimeClass.</span></span>

<span data-ttu-id="af1c5-199">Wie im Abschnitt „Definieren des Vertrags“ erwähnt wurde, muss ein Projektverweis auf die winmd-Verweisdatei der Desktopkomponente vorgenommen werden.</span><span class="sxs-lookup"><span data-stu-id="af1c5-199">As mentioned in the section "Defining the contract", a project reference must be made to the desktop component's reference winmd.</span></span> <span data-ttu-id="af1c5-200">Das Visual Studio-Projektsystem erstellt normalerweise eine aus zwei Ebenen bestehende Verzeichnisstruktur mit demselben Namen.</span><span class="sxs-lookup"><span data-stu-id="af1c5-200">The Visual Studio project system normally creates a two level directory structure with the same name.</span></span> <span data-ttu-id="af1c5-201">Im Beispiel lautet dieser „EnterpriseIPCApplication\\EnterpriseIPCApplication“.</span><span class="sxs-lookup"><span data-stu-id="af1c5-201">In the sample it is EnterpriseIPCApplication\\EnterpriseIPCApplication.</span></span> <span data-ttu-id="af1c5-202">Die **winmd**-Verweisdatei wird manuell in dieses Verzeichnis der zweiten Ebene kopiert. Anschließend wird das Dialogfeld „Projektverweise“ verwendet (klicken Sie auf die Schaltfläche **Durchsuchen**...),</span><span class="sxs-lookup"><span data-stu-id="af1c5-202">The reference **winmd** is manually copied to this second level directory and then the Project References dialog is used (click the **Browse..**</span></span> <span data-ttu-id="af1c5-203">um diese **winmd**-Datei zu suchen und zu referenzieren.</span><span class="sxs-lookup"><span data-stu-id="af1c5-203">button) to locate and reference this **winmd**.</span></span> <span data-ttu-id="af1c5-204">Danach sollte der Namespace der obersten Ebene der Desktopkomponente (z.B. Fabrikam) als Knoten der obersten Ebene im Teil „Verweise“ des Projekts angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="af1c5-204">After this, the top level namespace of the desktop component (e.g. Fabrikam) should appear as a top level node in the References part of the project.</span></span>

><span data-ttu-id="af1c5-205">**Hinweis**  Es ist sehr wichtig, die **WINMD-Verweisdatei** in der quergeladenen Anwendung zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="af1c5-205">**Note** It is very important to use the **reference winmd** in the side-loaded application.</span></span> <span data-ttu-id="af1c5-206">Wenn Sie versehentlich die **WINMD-Implementierungsdatei** in das Verzeichnis mit der quergeladenen App übernehmen und auf sie verweisen, wird wahrscheinlich ein Fehler wie „IStringable wurde nicht gefunden“ angezeigt.</span><span class="sxs-lookup"><span data-stu-id="af1c5-206">If you accidentally carry over the **implementation winmd** to the side-loaded app directory and reference it, you will likely receive an error related to "cannot find IStringable".</span></span> <span data-ttu-id="af1c5-207">Dies ist ein sicheres Zeichen dafür, dass auf die falsche **WINMD-Datei** verwiesen wurde.</span><span class="sxs-lookup"><span data-stu-id="af1c5-207">This is one sure sign that the wrong **winmd** has been referenced.</span></span> <span data-ttu-id="af1c5-208">Die Postbuildregeln in der IPC-Server-App (im folgenden Abschnitt ausführlich erläutert) trennen diese beiden **WINMD**-Dateien sorgfältig in zwei separaten Verzeichnissen.</span><span class="sxs-lookup"><span data-stu-id="af1c5-208">The post-build rules in the IPC server app (detailed in the next section) carefully segregate these two **winmd** into separate directories.</span></span>

<span data-ttu-id="af1c5-209">In <ActivatableClassAttribute Value="path"> können Umgebungsvariablen verwendet werden (insbesondere „%ProgramFiles%“). Wie bereits erwähnt, werden vom App-Broker nur 32-Bit-Versionen unterstützt. Daher wird „%ProgramFiles%“ zu „C:\Programme (x86)“ aufgelöst, wenn die Anwendung auf einem 64-Bit-Betriebssystem ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="af1c5-209">Environment variables (especially %ProgramFiles%) can be used in <ActivatableClassAttribute Value="path"> .As noted earlier, the App Broker only supports 32-bit so %ProgramFiles% will resolve to C:\\Program Files (x86) if the application is run on a 64-bit OS.</span></span>

## <a name="desktop-ipc-server-detail"></a><span data-ttu-id="af1c5-210">Desktop-IPC-Serverdetail</span><span class="sxs-lookup"><span data-stu-id="af1c5-210">Desktop IPC server detail</span></span>

<span data-ttu-id="af1c5-211">In den vorherigen beiden Abschnitten wurden die Deklaration der Klasse und die Mechanismen zur Übertragung der **WINMD**-Verweisdatei in das quergeladene Anwendungsprojekt erläutert.</span><span class="sxs-lookup"><span data-stu-id="af1c5-211">The previous two sections describe declaration of the class and the mechanics of transporting the reference **winmd** to the side-loaded application project.</span></span> <span data-ttu-id="af1c5-212">Der Großteil der restlichen Arbeit in der Desktopkomponente betrifft die Implementierung.</span><span class="sxs-lookup"><span data-stu-id="af1c5-212">The bulk of the remaining work in the desktop component involves implementation.</span></span> <span data-ttu-id="af1c5-213">Da die gesamte Desktopkomponente Desktopcode aufrufen kann (in der Regel zum Wiederverwenden vorhandener Coderessourcen), muss das Projekt auf spezielle Weise konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="af1c5-213">Since the whole point of the desktop component is to be able to call desktop code (usually to re-utilize existing code assets), the project must be configured in a special way.</span></span>
<span data-ttu-id="af1c5-214">In der Regel wird bei einem Visual Studio-Projekt mit .NET eines von zwei „Profilen“ verwendet.</span><span class="sxs-lookup"><span data-stu-id="af1c5-214">Normally, a Visual Studio project using .NET uses one of two "profiles".</span></span>
<span data-ttu-id="af1c5-215">Eines ist für den Desktop („.NetFramework“) und eines ist auf den UWP-App-Teil der CLR ausgerichtet („.NetCore“).</span><span class="sxs-lookup"><span data-stu-id="af1c5-215">One is for desktop (".NetFramework") and one is targeting the UWP app portion of the CLR (".NetCore").</span></span> <span data-ttu-id="af1c5-216">Bei einer Desktopkomponente in diesem Feature handelt es sich um einen Hybrid aus diesen beiden.</span><span class="sxs-lookup"><span data-stu-id="af1c5-216">A desktop component in this feature is a hybrid between these two.</span></span> <span data-ttu-id="af1c5-217">Daher wird der Verweisabschnitt sehr sorgfältig konstruiert, um diese beiden Profile zu mischen.</span><span class="sxs-lookup"><span data-stu-id="af1c5-217">As a result, the references section is very carefully constructed to blend these two profiles.</span></span>

<span data-ttu-id="af1c5-218">Ein normales UWP-App-Projekt enthält keine expliziten Projektverweise, da die gesamte Windows-Runtime-API-Oberfläche implizit enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="af1c5-218">A normal UWP app project contains no explicit project references because the entirety of the Windows Runtime API surface is implicitly included.</span></span>
<span data-ttu-id="af1c5-219">In der Regel werden nur andere projektübergreifenden Verweise vorgenommen.</span><span class="sxs-lookup"><span data-stu-id="af1c5-219">Normally only other inter-project references are made.</span></span> <span data-ttu-id="af1c5-220">Ein Desktopkomponentenprojekt verfügt jedoch über einen sehr speziellen Satz an Verweisen.</span><span class="sxs-lookup"><span data-stu-id="af1c5-220">However, a desktop component project has a very special set of references.</span></span> <span data-ttu-id="af1c5-221">Sein Lebenszyklus beginnt als Projekt vom Typ „Classic Desktop\\Class Library“, und daher handelt es sich um ein Desktopprojekt.</span><span class="sxs-lookup"><span data-stu-id="af1c5-221">It starts life as a "Classic Desktop\\Class Library" project and therefore is a desktop project.</span></span> <span data-ttu-id="af1c5-222">Deshalb müssen explizite Verweise auf die Windows-Runtime-API (mithilfe von Verweisen auf **WINMD**-Dateien) vorgenommen werden.</span><span class="sxs-lookup"><span data-stu-id="af1c5-222">So explicit references to the Windows Runtime API (via references to **winmd** files) must be made.</span></span> <span data-ttu-id="af1c5-223">Fügen Sie die korrekten Verweise wie unten gezeigt hinzu.</span><span class="sxs-lookup"><span data-stu-id="af1c5-223">Add proper references as shown below.</span></span>

```XML
<ItemGroup>
    <!-- These reference are added by VS automatically when you create a Class Library project-->
    <Reference Include="System" />
    <Reference Include="System.Core" />
    <Reference Include="System.Xml.Linq" />
    <Reference Include="System.Data.DataSetExtensions" />
    <Reference Include="Microsoft.CSharp" />
    <Reference Include="System.Data" />
    <Reference Include="System.Net.Http" />
<Reference Include="System.Xml" />
    <!-- These reference should be added manually by editing .csproj file-->

    <Reference Include="System.Runtime.WindowsRuntime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL">
      <HintPath>$(MSBuildProgramFiles32)\Microsoft SDKs\NETCoreSDK\System.Runtime.WindowsRuntime\4.0.10\lib\netcore50\System.Runtime.WindowsRuntime.dll</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows">
      <HintPath>$(MSBuildProgramFiles32)\Windows Kits\10\UnionMetadata\Facade\Windows.WinMD</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Foundation.FoundationContract">
      <HintPath>$(MSBuildProgramFiles32)\Windows Kits\10\References\Windows.Foundation.FoundationContract\1.0.0.0\Windows.Foundation.FoundationContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Foundation.UniversalApiContract">
      <HintPath>$(MSBuildProgramFiles32)\Windows Kits\10\References\Windows.Foundation.UniversalApiContract\1.0.0.0\Windows.Foundation.UniversalApiContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Networking.Connectivity.WwanContract">
      <HintPath>$(MSBuildProgramFiles32)\Windows Kits\10\References\Windows.Networking.Connectivity.WwanContract\1.0.0.0\Windows.Networking.Connectivity.WwanContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.ApplicationModel.Activation.ActivatedEventsContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.ApplicationModel.Activation.ActivatedEventsContract\1.0.0.0\Windows.ApplicationModel.Activation.ActivatedEventsContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.ApplicationModel.Activation.ActivationCameraSettingsContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.ApplicationModel.Activation.ActivationCameraSettingsContract\1.0.0.0\Windows.ApplicationModel.Activation.ActivationCameraSettingsContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.ApplicationModel.Activation.ContactActivatedEventsContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.ApplicationModel.Activation.ContactActivatedEventsContract\1.0.0.0\Windows.ApplicationModel.Activation.ContactActivatedEventsContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.ApplicationModel.Activation.WebUISearchActivatedEventsContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.ApplicationModel.Activation.WebUISearchActivatedEventsContract\1.0.0.0\Windows.ApplicationModel.Activation.WebUISearchActivatedEventsContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.ApplicationModel.Background.BackgroundAlarmApplicationContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.ApplicationModel.Background.BackgroundAlarmApplicationContract\1.0.0.0\Windows.ApplicationModel.Background.BackgroundAlarmApplicationContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.ApplicationModel.Calls.LockScreenCallContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.ApplicationModel.Calls.LockScreenCallContract\1.0.0.0\Windows.ApplicationModel.Calls.LockScreenCallContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.ApplicationModel.Resources.Management.ResourceIndexerContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.ApplicationModel.Resources.Management.ResourceIndexerContract\1.0.0.0\Windows.ApplicationModel.Resources.Management.ResourceIndexerContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.ApplicationModel.Search.Core.SearchCoreContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.ApplicationModel.Search.Core.SearchCoreContract\1.0.0.0\Windows.ApplicationModel.Search.Core.SearchCoreContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.ApplicationModel.Search.SearchContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.ApplicationModel.Search.SearchContract\1.0.0.0\Windows.ApplicationModel.Search.SearchContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.ApplicationModel.Wallet.WalletContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.ApplicationModel.Wallet.WalletContract\1.0.0.0\Windows.ApplicationModel.Wallet.WalletContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Devices.Custom.CustomDeviceContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.Devices.Custom.CustomDeviceContract\1.0.0.0\Windows.Devices.Custom.CustomDeviceContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Devices.Portable.PortableDeviceContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.Devices.Portable.PortableDeviceContract\1.0.0.0\Windows.Devices.Portable.PortableDeviceContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Devices.Printers.Extensions.ExtensionsContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.Devices.Printers.Extensions.ExtensionsContract\1.0.0.0\Windows.Devices.Printers.Extensions.ExtensionsContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Devices.Printers.PrintersContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.Devices.Printers.PrintersContract\1.0.0.0\Windows.Devices.Printers.PrintersContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Devices.Scanners.ScannerDeviceContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.Devices.Scanners.ScannerDeviceContract\1.0.0.0\Windows.Devices.Scanners.ScannerDeviceContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Devices.Sms.LegacySmsApiContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.Devices.Sms.LegacySmsApiContract\1.0.0.0\Windows.Devices.Sms.LegacySmsApiContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Gaming.Preview.GamesEnumerationContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.Gaming.Preview.GamesEnumerationContract\1.0.0.0\Windows.Gaming.Preview.GamesEnumerationContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Globalization.GlobalizationJapanesePhoneticAnalyzerContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.Globalization.GlobalizationJapanesePhoneticAnalyzerContract\1.0.0.0\Windows.Globalization.GlobalizationJapanesePhoneticAnalyzerContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Graphics.Printing3D.Printing3DContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.Graphics.Printing3D.Printing3DContract\1.0.0.0\Windows.Graphics.Printing3D.Printing3DContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Management.Deployment.Preview.DeploymentPreviewContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.Management.Deployment.Preview.DeploymentPreviewContract\1.0.0.0\Windows.Management.Deployment.Preview.DeploymentPreviewContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Management.Workplace.WorkplaceSettingsContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.Management.Workplace.WorkplaceSettingsContract\1.0.0.0\Windows.Management.Workplace.WorkplaceSettingsContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Media.Capture.AppCaptureContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.Media.Capture.AppCaptureContract\1.0.0.0\Windows.Media.Capture.AppCaptureContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Media.Capture.CameraCaptureUIContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.Media.Capture.CameraCaptureUIContract\1.0.0.0\Windows.Media.Capture.CameraCaptureUIContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Media.Devices.CallControlContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.Media.Devices.CallControlContract\1.0.0.0\Windows.Media.Devices.CallControlContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Media.MediaControlContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.Media.MediaControlContract\1.0.0.0\Windows.Media.MediaControlContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Media.Playlists.PlaylistsContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.Media.Playlists.PlaylistsContract\1.0.0.0\Windows.Media.Playlists.PlaylistsContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Media.Protection.ProtectionRenewalContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.Media.Protection.ProtectionRenewalContract\1.0.0.0\Windows.Media.Protection.ProtectionRenewalContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Networking.NetworkOperators.LegacyNetworkOperatorsContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.Networking.NetworkOperators.LegacyNetworkOperatorsContract\1.0.0.0\Windows.Networking.NetworkOperators.LegacyNetworkOperatorsContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Networking.Sockets.ControlChannelTriggerContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.Networking.Sockets.ControlChannelTriggerContract\1.0.0.0\Windows.Networking.Sockets.ControlChannelTriggerContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Security.EnterpriseData.EnterpriseDataContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.Security.EnterpriseData.EnterpriseDataContract\1.0.0.0\Windows.Security.EnterpriseData.EnterpriseDataContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Security.ExchangeActiveSyncProvisioning.EasContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.Security.ExchangeActiveSyncProvisioning.EasContract\1.0.0.0\Windows.Security.ExchangeActiveSyncProvisioning.EasContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Services.Maps.GuidanceContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.Services.Maps.GuidanceContract\1.0.0.0\Windows.Services.Maps.GuidanceContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Services.Maps.LocalSearchContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.Services.Maps.LocalSearchContract\1.0.0.0\Windows.Services.Maps.LocalSearchContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.System.Profile.SystemManufacturers.SystemManufacturersContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.System.Profile.SystemManufacturers.SystemManufacturersContract\1.0.0.0\Windows.System.Profile.SystemManufacturers.SystemManufacturersContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.System.Profile.ProfileHardwareTokenContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.System.Profile.ProfileHardwareTokenContract\1.0.0.0\Windows.System.Profile.ProfileHardwareTokenContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.System.Profile.ProfileRetailInfoContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.System.Profile.ProfileRetailInfoContract\1.0.0.0\Windows.System.Profile.ProfileRetailInfoContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.System.UserProfile.UserProfileContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.System.UserProfile.UserProfileContract\1.0.0.0\Windows.System.UserProfile.UserProfileContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.System.UserProfile.UserProfileLockScreenContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.System.UserProfile.UserProfileLockScreenContract\1.0.0.0\Windows.System.UserProfile.UserProfileLockScreenContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.UI.ApplicationSettings.ApplicationsSettingsContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.UI.ApplicationSettings.ApplicationsSettingsContract\1.0.0.0\Windows.UI.ApplicationSettings.ApplicationsSettingsContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.UI.Core.AnimationMetrics.AnimationMetricsContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.UI.Core.AnimationMetrics.AnimationMetricsContract\1.0.0.0\Windows.UI.Core.AnimationMetrics.AnimationMetricsContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.UI.Core.CoreWindowDialogsContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.UI.Core.CoreWindowDialogsContract\1.0.0.0\Windows.UI.Core.CoreWindowDialogsContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.UI.Xaml.Hosting.HostingContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.UI.Xaml.Hosting.HostingContract\1.0.0.0\Windows.UI.Xaml.Hosting.HostingContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
    <Reference Include="Windows.Web.Http.Diagnostics.HttpDiagnosticsContract">
      <HintPath>$(MsBuildProgramFiles32)\Windows Kits\10\References\Windows.Web.Http.Diagnostics.HttpDiagnosticsContract\1.0.0.0\Windows.Web.Http.Diagnostics.HttpDiagnosticsContract.winmd</HintPath>
      <Private>False</Private>
    </Reference>
</ItemGroup>
```

<span data-ttu-id="af1c5-224">Die oben erwähnten Verweise sind eine sorgfältige Mischung aus Verweisen, die für die korrekte Ausführung dieses Hybridservers entscheidend sind.</span><span class="sxs-lookup"><span data-stu-id="af1c5-224">The references above are a careful mix of eferences that are critical to the proper operation of this hybrid server.</span></span> <span data-ttu-id="af1c5-225">Das normale Verfahren besteht darin, die CSPROJ-Datei (wie für die Bearbeitung des Projekts OutputType beschrieben) zu öffnen und diese Verweise wie erforderlich hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="af1c5-225">The protocol is to open the .csproj file (as described in how to edit the project OutputType) and add these references as necessary.</span></span>

<span data-ttu-id="af1c5-226">Sobald die Verweise korrekt konfiguriert wurden, besteht die nächste Aufgabe darin, die Funktionalität des Servers zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="af1c5-226">Once the references are properly configured, the next task is to implement the server's functionality.</span></span> <span data-ttu-id="af1c5-227">Weitere Informationen finden Sie im MSDN-Thema [Bewährte Methoden für die Interoperabilität mit Komponenten für Windows-Runtime (UWP-Apps mit C\#/VB/C++ und XAML)](https://msdn.microsoft.com/library/windows/apps/hh750311.aspx).</span><span class="sxs-lookup"><span data-stu-id="af1c5-227">See the MSDN topic [Best practices for interoperability with Windows Runtime Components (UWP apps using C\#/VB/C++ and XAML)](https://msdn.microsoft.com/library/windows/apps/hh750311.aspx).</span></span>
<span data-ttu-id="af1c5-228">Die Aufgabe besteht darin, eine DLL-Datei für die Komponente für Windows-Runtime zu erstellen, die Desktopcode als Teil der Implementierung aufrufen kann.</span><span class="sxs-lookup"><span data-stu-id="af1c5-228">The task is to create a Windows Runtime component dll that is able to call desktop code as part of its implementation.</span></span> <span data-ttu-id="af1c5-229">Das Begleitbeispiel enthält die in der Windows-Runtime verwendeten Hauptmuster:</span><span class="sxs-lookup"><span data-stu-id="af1c5-229">The accompanying sample includes the major patterns used in Windows Runtime:</span></span>

-   <span data-ttu-id="af1c5-230">Methodenaufrufe</span><span class="sxs-lookup"><span data-stu-id="af1c5-230">Method calls</span></span>

-   <span data-ttu-id="af1c5-231">Windows-Runtime-Ereignisquellen der Desktopkomponente</span><span class="sxs-lookup"><span data-stu-id="af1c5-231">Windows Runtime Events sources by the desktop component</span></span>

-   <span data-ttu-id="af1c5-232">Asynchrone Windows-Runtime-Vorgänge</span><span class="sxs-lookup"><span data-stu-id="af1c5-232">Windows Runtime Async operations</span></span>

-   <span data-ttu-id="af1c5-233">Zurückgegebene Arrays grundlegender Typen</span><span class="sxs-lookup"><span data-stu-id="af1c5-233">Returning arrays of basic types</span></span>

**<span data-ttu-id="af1c5-234">Installieren</span><span class="sxs-lookup"><span data-stu-id="af1c5-234">Install</span></span>**

<span data-ttu-id="af1c5-235">Zum Installieren der App kopieren Sie die **WINMD**-Implementierung in das richtige Verzeichnis, das im Manifest der zugehörigen quergeladenen Anwendung angegeben ist: der Wert Value="path" von <ActivatableClassAttribute>.</span><span class="sxs-lookup"><span data-stu-id="af1c5-235">To install the app, copy the implementation **winmd** to the correct directory specified in the associated side-loaded application's manifest: <ActivatableClassAttribute>'s Value="path".</span></span> <span data-ttu-id="af1c5-236">Kopieren Sie auch alle zugehörigen Unterstützungsdateien und die Proxy-/Stub-DLL (letztere wird weiter unten erläutert).</span><span class="sxs-lookup"><span data-stu-id="af1c5-236">Also copy any associated support files and the proxy/stub dll (this latter detail is covered below).</span></span> <span data-ttu-id="af1c5-237">Wenn die **WINMD**-Implementierung nicht an den Speicherort im Serververzeichnis kopiert wird, führt dies dazu, dass alle zu erneuernden Aufrufe der quergeladenen Anwendung für die RuntimeClass einen Fehler des Typs „Klasse nicht registriert“ zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="af1c5-237">Failing to copy the implementation **winmd** to the server directory location will cause all of the side-loaded application's calls to new on the RuntimeClass will throw a "class not registered" error.</span></span> <span data-ttu-id="af1c5-238">Wenn der Proxy/Stub nicht installiert (oder nicht registriert) wird, tritt bei allen Aufrufen ein Fehler auf, und es werden keine Werte zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="af1c5-238">Failure to install the proxy/stub (or failure to register) will cause all calls to fail with no return values.</span></span> <span data-ttu-id="af1c5-239">Dieser letzte Fehler ist häufig **nicht** mit sichtbaren Ausnahmen verbunden.</span><span class="sxs-lookup"><span data-stu-id="af1c5-239">This latter error is frequently **not** associated with visible exceptions.</span></span>
<span data-ttu-id="af1c5-240">Wenn aufgrund dieses Fehlers Ausnahmen beobachtet werden, beziehen sie sich unter Umständen auf eine „ungültige Umwandlung“.</span><span class="sxs-lookup"><span data-stu-id="af1c5-240">If exceptions are observed due to this configuration error, they may refer to "invalid cast".</span></span>

**<span data-ttu-id="af1c5-241">Überlegungen zur Serverimplementierung</span><span class="sxs-lookup"><span data-stu-id="af1c5-241">Server implementation considerations</span></span>**

<span data-ttu-id="af1c5-242">Sie können sich den Desktop-Windows-Runtime-Server als arbeits- oder aufgabenbasierten Server vorstellen.</span><span class="sxs-lookup"><span data-stu-id="af1c5-242">The desktop Windows Runtime server can be thought of as "worker" or "task" based.</span></span> <span data-ttu-id="af1c5-243">Jeder Aufruf an den Server fungiert als Nicht-UI-Thread, und der gesamte Code muss Multithread-fähig und sicher sein.</span><span class="sxs-lookup"><span data-stu-id="af1c5-243">Every call into the server operates on a non-UI thread and all code must be multi-thread aware and safe.</span></span> <span data-ttu-id="af1c5-244">Es ist auch wichtig, welcher Teil der quergeladenen Anwendung den Server aufruft.</span><span class="sxs-lookup"><span data-stu-id="af1c5-244">Which part of the side-loaded application is calling the server's functionality is also important.</span></span> <span data-ttu-id="af1c5-245">Es sollte auch immer vermieden werden, Code mit langer Ausführungsdauer über einen Benutzeroberflächen-Thread in der quergeladenen Anwendung auszuführen.</span><span class="sxs-lookup"><span data-stu-id="af1c5-245">It is critical to always avoid calling long-running code from any UI thread in the side-loaded application.</span></span> <span data-ttu-id="af1c5-246">Dazu gibt es zwei wesentlichen Möglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="af1c5-246">There are two main ways to accomplish this:</span></span>

1.  <span data-ttu-id="af1c5-247">Verwenden Sie beim Aufrufen einer Serverfunktionalität über einen Benutzeroberflächen-Thread immer ein asynchrones Muster in der öffentlichen Oberfläche und der Implementierung des Servers.</span><span class="sxs-lookup"><span data-stu-id="af1c5-247">If calling server functionality from a UI thread, always use an async pattern in the server's public surface area and implementation.</span></span>

2.  <span data-ttu-id="af1c5-248">Rufen Sie die Funktionalität des Servers über einen Hintergrundthread in der quergeladenen Anwendung auf.</span><span class="sxs-lookup"><span data-stu-id="af1c5-248">Call the server's functionality from a background thread in the side-loaded application.</span></span>

**<span data-ttu-id="af1c5-249">Asynchrone Windows-Runtime im Server</span><span class="sxs-lookup"><span data-stu-id="af1c5-249">Windows Runtime async in the server</span></span>**

<span data-ttu-id="af1c5-250">Aufgrund der prozessübergreifenden Natur des Anwendungsmodells erzeugen Aufrufe an den Server mehr Mehraufwand als Code, der ausschließlich innerhalb eines Prozesses ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="af1c5-250">Given the cross-process nature of the application model, calls to the server have more overhead than code that runs exclusively in-process.</span></span> <span data-ttu-id="af1c5-251">In der Regel ist es sicher, eine einfache Eigenschaft aufzurufen, die einen speicherinternen Wert zurückgibt, da dies schnell genug ausgeführt wird, um den UI-Thread nicht zu blockieren.</span><span class="sxs-lookup"><span data-stu-id="af1c5-251">It is normally safe to call a simple property that returns an in-memory value because it will execute quickly enough that blocking the UI thread is not a concern.</span></span> <span data-ttu-id="af1c5-252">Allerdings können alle Aufrufe, die E/A-Vorgänge beinhalten (dazu zählen sämtliche Dateiverarbeitungen und Datenbankabrufe), den aufrufenden UI-Thread potenziell blockieren und dazu führen, dass die Anwendung beendet wird, weil sie nicht reagiert.</span><span class="sxs-lookup"><span data-stu-id="af1c5-252">However, any call that involves I/O of any sort (this includes all file handling and database retrievals) can potentially block the calling UI thread and cause the application to be terminated due to unresponsiveness.</span></span> <span data-ttu-id="af1c5-253">Außerdem wird bei dieser Anwendungsarchitektur aus Leistungsgründen von Eigenschaftsaufrufen für Objekte abgeraten.</span><span class="sxs-lookup"><span data-stu-id="af1c5-253">In addition, property calls on objects are discouraged in this application architecture for performance reasons.</span></span>
<span data-ttu-id="af1c5-254">Eine ausführlichere Erläuterung finden Sie im folgenden Abschnitt.</span><span class="sxs-lookup"><span data-stu-id="af1c5-254">This is covered in more depth in the following section.</span></span>

<span data-ttu-id="af1c5-255">Ein korrekt implementierter Server implementiert über UI-Threads ausgeführte Aufrufe normalerweise direkt über das asynchrone Windows-Runtime-Muster.</span><span class="sxs-lookup"><span data-stu-id="af1c5-255">A properly implemented server will normally implement calls made directly from UI threads via the Windows Runtime async pattern.</span></span> <span data-ttu-id="af1c5-256">Dies kann durch das folgende Muster implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="af1c5-256">This can be implemented by following this pattern.</span></span> <span data-ttu-id="af1c5-257">Zunächst erfolgt die Deklaration (erneut aus dem Begleitbeispiel):</span><span class="sxs-lookup"><span data-stu-id="af1c5-257">First, the declaration (again, from the accompanying sample):</span></span>

```csharp
public IAsyncOperation<int> FindElementAsync(int input)
```

<span data-ttu-id="af1c5-258">Hiermit wird ein asynchroner Widows-Runtime-Vorgang deklariert, der eine ganze Zahl zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="af1c5-258">This declares a Windows Runtime async operation that returns an integer.</span></span>
<span data-ttu-id="af1c5-259">Die Implementierung des asynchronen Vorgangs sieht in der Regel wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="af1c5-259">The implementation of the async operation normally takes the form:</span></span>

```csharp
return Task<int>.Run( () =>
{
    int retval = ...
    // execute some potentially long-running code here 
}).AsAsyncOperation<int>();

```

><span data-ttu-id="af1c5-260">**Hinweis**  Beachten Sie, dass es beim Schreiben der Implementierung normal ist, auf andere Vorgänge mit potenziell langer Ausführungsdauer zu warten.</span><span class="sxs-lookup"><span data-stu-id="af1c5-260">**Note** It is common to await some other potentially long running operations while writing the implementation.</span></span> <span data-ttu-id="af1c5-261">In diesem Fall muss der **Task.Run**-Code deklariert werden:</span><span class="sxs-lookup"><span data-stu-id="af1c5-261">If so, the **Task.Run** code needs to be declared:</span></span>

```csharp
return Task<int>.Run(async () =>
{
    int retval = ...
    // execute some potentially long-running code here 
    await ... // some other WinRT async operation or Task
}).AsAsyncOperation<int>();
```

<span data-ttu-id="af1c5-262">Clients dieser asynchronen Methode können wie bei jedem anderen asynchronen Windows-Runtime-Vorgang auf den Vorgang warten.</span><span class="sxs-lookup"><span data-stu-id="af1c5-262">Clients of this async method can await this operation like any other Windows Runtime aysnc operation.</span></span>

**<span data-ttu-id="af1c5-263">Aufrufen der Serverfunktionalität aus dem Hintergrundthread einer Anwendung</span><span class="sxs-lookup"><span data-stu-id="af1c5-263">Call server functionality from an application background thread</span></span>**

<span data-ttu-id="af1c5-264">Da Client und Server in der Regel von derselben Organisation geschrieben werden, kann eine Programmiermethode angewendet werden, bei der alle Aufrufe an den Server durch einen Hintergrundthread in der quergeladenen Anwendung erfolgen.</span><span class="sxs-lookup"><span data-stu-id="af1c5-264">Since it is typical that both client and server will be written by the same organization, a programming practice can be adopted that all calls to the server will be made by a background thread in the side-loaded application.</span></span> <span data-ttu-id="af1c5-265">Ein direkter Aufruf, bei dem ein oder mehrere Datenstapel vom Server abgerufen werden, kann über einen Hintergrundthread erfolgen.</span><span class="sxs-lookup"><span data-stu-id="af1c5-265">A direct call that collects one or more batches of data from the server can be made from a background thread.</span></span> <span data-ttu-id="af1c5-266">Wenn die Ergebnisse vollständig abgerufen wurden, kann der Datenstapel, der sich im Speicher des Anwendungsprozesses befindet, in der Regel direkt über den Benutzeroberflächen-Thread abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="af1c5-266">When the result(s) are completely retrieved, the batch of data that is in-memory in the application process can usually be directly retrieved from the UI thread.</span></span> <span data-ttu-id="af1c5-267">C\#-Objekte sind von sich aus zwischen Hintergrundthreads und Benutzeroberflächen-Threads agil und somit für diese Art des Aufrufmusters besonders nützlich.</span><span class="sxs-lookup"><span data-stu-id="af1c5-267">C\# objects are naturally agile between background threads and UI threads so are especially useful for this kind of calling pattern.</span></span>

## <a name="creating-and-deploying-the-windows-runtime-proxy"></a><span data-ttu-id="af1c5-268">Erstellen und Bereitstellen des Windows-Runtime-Proxys</span><span class="sxs-lookup"><span data-stu-id="af1c5-268">Creating and deploying the Windows Runtime proxy</span></span>

<span data-ttu-id="af1c5-269">Da die IPC-Methode das Marshalling von Windows-Runtime-Schnittstellen zwischen zwei Prozessen beinhaltet, muss ein global registrierter Windows-Runtime-Proxy und -Stub verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="af1c5-269">Since the IPC approach involves marshaling Windows Runtime interfaces between two processes, a globally registered Windows Runtime proxy and stub must be used.</span></span>

**<span data-ttu-id="af1c5-270">Erstellen des Proxys in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="af1c5-270">Creating the proxy in Visual Studio</span></span>**

<span data-ttu-id="af1c5-271">Der Prozess zum Erstellen und Registrieren von Proxys und Stubs für die Verwendung innerhalb eines standardmäßigen UWP-App-Pakets ist im Thema [Auslösen von Ereignissen in Komponenten für Windows-Runtime](https://msdn.microsoft.com/library/windows/apps/dn169426.aspx) erläutert.</span><span class="sxs-lookup"><span data-stu-id="af1c5-271">The process for creating and registering proxies and stubs for use inside a regular UWP app package are described in the topic [Raising Events in Windows Runtime Components](https://msdn.microsoft.com/library/windows/apps/dn169426.aspx).</span></span>
<span data-ttu-id="af1c5-272">Die in diesem Artikel beschriebenen Schritte sind komplizierter als der nachfolgend beschriebene Prozess, da sie das Registrieren des Proxys/Stubs innerhalb des Anwendungspakets enthalten (im Gegensatz zur globalen Registrierung).</span><span class="sxs-lookup"><span data-stu-id="af1c5-272">The steps described in this article are more complicated than the process described below because it involves registering the proxy/stub inside the application package (as opposed to registering it globally).</span></span>

<span data-ttu-id="af1c5-273">**Schritt1:** Erstellen Sie mithilfe der Projektmappe für das Desktopkomponentenprojekt ein Proxy-/Stub-Projekt in Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="af1c5-273">**Step 1:** Using the solution for the desktop component project, create a Proxy/Stub project in Visual Studio:</span></span>

**<span data-ttu-id="af1c5-274">Projektmappe > Hinzufügen > Projekt > Visual C++ > Win32-Konsolenoption „DLL auswählen“.</span><span class="sxs-lookup"><span data-stu-id="af1c5-274">Solution > Add > Project > Visual C++ > Win32 Console Select DLL option.</span></span>**

<span data-ttu-id="af1c5-275">Bei den nachfolgenden Schritten wird davon ausgegangen, dass der Name der Serverkomponente **MyWinRTComponent** lautet.</span><span class="sxs-lookup"><span data-stu-id="af1c5-275">For the steps below, we assume the server component is called **MyWinRTComponent**.</span></span>

<span data-ttu-id="af1c5-276">**Schritt3:** Löschen Sie alle CPP/H-Dateien im Projekt.</span><span class="sxs-lookup"><span data-stu-id="af1c5-276">**Step 3:** Delete all the CPP/H files from the project.</span></span>

<span data-ttu-id="af1c5-277">**Schritt 4:** Der vorherige Abschnitt „Definieren des Vertrags“ enthält einen Postbuildbefehl, der **winmdidl.exe**, **midl.exe**, **mdmerge.exe** usw. ausführt.</span><span class="sxs-lookup"><span data-stu-id="af1c5-277">**Step 4:** The previous section "Defining the Contract" contains a Post-Build command that runs **winmdidl.exe**, **midl.exe**, **mdmerge.exe**, and so on.</span></span> <span data-ttu-id="af1c5-278">Eine der Ausgaben des midl-Schritts dieses Postbuildbefehls generiert vier wichtige Ausgaben:</span><span class="sxs-lookup"><span data-stu-id="af1c5-278">One of the outputs from the midl step of this post-build command generates four important outputs:</span></span>

<span data-ttu-id="af1c5-279">a) Dlldata.c</span><span class="sxs-lookup"><span data-stu-id="af1c5-279">a) Dlldata.c</span></span>

<span data-ttu-id="af1c5-280">b) Eine Headerdatei (z.B. MyWinRTComponent.h)</span><span class="sxs-lookup"><span data-stu-id="af1c5-280">b) A header file (e.g. MyWinRTComponent.h)</span></span>

<span data-ttu-id="af1c5-281">c) Eine \*\_i.c-Datei (z.B. MyWinRTComponent\_i.c)</span><span class="sxs-lookup"><span data-stu-id="af1c5-281">c) A \*\_i.c file (e.g. MyWinRTComponent\_i.c)</span></span>

<span data-ttu-id="af1c5-282">d) Eine \*\_p.c-Datei (z.B. MyWinRTComponent\_p.c)</span><span class="sxs-lookup"><span data-stu-id="af1c5-282">d) A \*\_p.c file (e.g. MyWinRTComponent\_p.c)</span></span>

<span data-ttu-id="af1c5-283">**Schritt5:** Fügen Sie diese vier generierten Dateien dem Projekt „MyWinRTProxy“ hinzu.</span><span class="sxs-lookup"><span data-stu-id="af1c5-283">**Step 5:** Add these four generated files to the "MyWinRTProxy" project.</span></span>

<span data-ttu-id="af1c5-284">**Schritt6:** Fügen Sie dem Projekt „MyWinRTProxy“ eine Definitionsdatei hinzu **(Projekt/Neues Element hinzufügen/Code/Moduldefinitionsdatei)**, und aktualisieren Sie den Inhalt wie folgt:</span><span class="sxs-lookup"><span data-stu-id="af1c5-284">**Step 6:** Add a def file to "MyWinRTProxy" project **(Project > Add New Item > Code > Module-Definition File**) and update the contents to be:</span></span>

<span data-ttu-id="af1c5-285">LIBRARY MyWinRTComponent.Proxies.dll</span><span class="sxs-lookup"><span data-stu-id="af1c5-285">LIBRARY MyWinRTComponent.Proxies.dll</span></span>

<span data-ttu-id="af1c5-286">EXPORTS</span><span class="sxs-lookup"><span data-stu-id="af1c5-286">EXPORTS</span></span>

<span data-ttu-id="af1c5-287">DllCanUnloadNow PRIVATE</span><span class="sxs-lookup"><span data-stu-id="af1c5-287">DllCanUnloadNow PRIVATE</span></span>

<span data-ttu-id="af1c5-288">DllGetClassObject PRIVATE</span><span class="sxs-lookup"><span data-stu-id="af1c5-288">DllGetClassObject PRIVATE</span></span>

<span data-ttu-id="af1c5-289">DllRegisterServer PRIVATE</span><span class="sxs-lookup"><span data-stu-id="af1c5-289">DllRegisterServer PRIVATE</span></span>

<span data-ttu-id="af1c5-290">DllUnregisterServer PRIVATE</span><span class="sxs-lookup"><span data-stu-id="af1c5-290">DllUnregisterServer PRIVATE</span></span>

<span data-ttu-id="af1c5-291">**Schritt7:** Öffnen Sie Eigenschaften für das Projekt „MyWinRTProxy“:</span><span class="sxs-lookup"><span data-stu-id="af1c5-291">**Step 7:** Open properties for the "MyWinRTProxy" project:</span></span>

**<span data-ttu-id="af1c5-292">Konfigurationseigenschaften > Allgemein > Zielname:</span><span class="sxs-lookup"><span data-stu-id="af1c5-292">Comfiguration Properties > General > Target Name :</span></span>**

<span data-ttu-id="af1c5-293">MyWinRTComponent.Proxies</span><span class="sxs-lookup"><span data-stu-id="af1c5-293">MyWinRTComponent.Proxies</span></span>

**<span data-ttu-id="af1c5-294">C/C++ > Präprozessordefinitionen > Hinzufügen</span><span class="sxs-lookup"><span data-stu-id="af1c5-294">C/C++ > Preprocessor Definitions > Add</span></span>**

<span data-ttu-id="af1c5-295">"WIN32;\_WINDOWS;REGISTER\_PROXY\_DLL"</span><span class="sxs-lookup"><span data-stu-id="af1c5-295">"WIN32;\_WINDOWS;REGISTER\_PROXY\_DLL"</span></span>

**<span data-ttu-id="af1c5-296">C/C++ > Vorkompilierte Headerdatei: „Keine vorkompilierte Headerdatei verwenden“ auswählen</span><span class="sxs-lookup"><span data-stu-id="af1c5-296">C/C++ > Precompiled Header : Select "Not Using Precompiled Header"</span></span>**

**<span data-ttu-id="af1c5-297">Linker > Allgemein > Importbibliothek ignorieren: „Ja“ auswählen</span><span class="sxs-lookup"><span data-stu-id="af1c5-297">Linker > General > Ignore Import Library : Select "Yes"</span></span>**

**<span data-ttu-id="af1c5-298">Linker > Eingabe > Zusätzliche Abhängigkeiten: „rpcrt4.lib;runtimeobject.lib“ hinzufügen</span><span class="sxs-lookup"><span data-stu-id="af1c5-298">Linker > Input > Additional Dependencies : Add rpcrt4.lib;runtimeobject.lib</span></span>**

**<span data-ttu-id="af1c5-299">Linker > Windows-Metadaten > Windows-Metadaten generieren: „Nein“ auswählen</span><span class="sxs-lookup"><span data-stu-id="af1c5-299">Linker > Windows Metadata > Generate Windows Metadata : Select "No"</span></span>**

<span data-ttu-id="af1c5-300">**Schritt8:** Erstellen Sie das Projekt „MyWinRTProxy“.</span><span class="sxs-lookup"><span data-stu-id="af1c5-300">**Step 8:** Build the "MyWinRTProxy" project.</span></span>

**<span data-ttu-id="af1c5-301">Bereitstellen des Proxys</span><span class="sxs-lookup"><span data-stu-id="af1c5-301">Deploying the proxy</span></span>**

<span data-ttu-id="af1c5-302">Der Proxy muss global registriert werden.</span><span class="sxs-lookup"><span data-stu-id="af1c5-302">The proxy must be globally registered.</span></span> <span data-ttu-id="af1c5-303">Die einfachste Möglichkeit hierzu besteht darin, dass beim Installationsprozess „DllRegisterServer“ in der Proxy-DLL aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="af1c5-303">The simplest way to do this is to have your install process call DllRegisterServer on the proxy dll.</span></span> <span data-ttu-id="af1c5-304">Da das Feature nur x86-Server unterstützt (d.h. keine 64-Bit-Unterstützung), besteht die einfachste Konfiguration in der Verwendung eines 32-Bit-Servers, eines 32-Bit-Proxys und einer quergeladenen 32-Bit-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="af1c5-304">Note that since the feature only supports servers built for x86 (i.e. no 64-bit support), the simplest configuration is to use a 32-bit server, a 32-bit proxy, and a 32-bit side-loaded application.</span></span> <span data-ttu-id="af1c5-305">Der Proxy befindet sich normalerweise in der **WINMD**-Implementierung für die Desktopkomponente.</span><span class="sxs-lookup"><span data-stu-id="af1c5-305">The proxy normally sits alongside the implementation **winmd** for the desktop component.</span></span>

<span data-ttu-id="af1c5-306">Es muss ein weiterer Konfigurationsschritt vorgenommen werden.</span><span class="sxs-lookup"><span data-stu-id="af1c5-306">One additional configuration step must be performed.</span></span> <span data-ttu-id="af1c5-307">Damit der Proxy vom quergeladenen Prozess geladen und ausgeführt wird, muss das Verzeichnis mit „lesen/ausführen“ für ALL_APPLICATION_PACKAGES gekennzeichnet sein.</span><span class="sxs-lookup"><span data-stu-id="af1c5-307">In order for the side-loaded process to load and execute the proxy, the directory must be marked "read / execute" for ALL_APPLICATION_PACKAGES.</span></span> <span data-ttu-id="af1c5-308">Dies erfolgt über das Befehlszeilentool **icacls.exe**.</span><span class="sxs-lookup"><span data-stu-id="af1c5-308">This is done via the **icacls.exe** command line tool.</span></span> <span data-ttu-id="af1c5-309">Dieser Befehl muss in dem Verzeichnis ausgeführt werden, in dem sich die **WINMD**-Implementierung und die Proxy-/Stub-DLL befinden:</span><span class="sxs-lookup"><span data-stu-id="af1c5-309">This command should execute in the directory where the implementation **winmd** and proxy/stub dll resides:</span></span>

*<span data-ttu-id="af1c5-310">icacls.</span><span class="sxs-lookup"><span data-stu-id="af1c5-310">icacls .</span></span> <span data-ttu-id="af1c5-311">/T /grant \*S-1-15-2-1:RX</span><span class="sxs-lookup"><span data-stu-id="af1c5-311">/T /grant \*S-1-15-2-1:RX</span></span>*

## <a name="patterns-and-performance"></a><span data-ttu-id="af1c5-312">Muster und Leistung</span><span class="sxs-lookup"><span data-stu-id="af1c5-312">Patterns and performance</span></span>

<span data-ttu-id="af1c5-313">Es ist sehr wichtig, die Leistung bei prozessübergreifenden Übertragungen genau zu überwachen.</span><span class="sxs-lookup"><span data-stu-id="af1c5-313">It is very important that performance of the cross-process transport be carefully monitored.</span></span> <span data-ttu-id="af1c5-314">Ein prozessübergreifender Aufruf ist mindestens zweimal so teuer wie ein prozessinterner Aufruf.</span><span class="sxs-lookup"><span data-stu-id="af1c5-314">A cross-process call is at least twice as expensive than an in-process call.</span></span> <span data-ttu-id="af1c5-315">Das Erstellen prozessübergreifender „geschwätziger“ Konversationen oder das Ausführen wiederholter Übertragungen von großen Objekten wie Bitmapbildern kann zu einer unerwarteten und unerwünschten Leistung der Anwendung führen.</span><span class="sxs-lookup"><span data-stu-id="af1c5-315">Creating "chatty" conversations cross-process or performing repeated transfers of large objects like bitmap images, can cause unexpected and undesirable application performance.</span></span>

<span data-ttu-id="af1c5-316">Es folgt eine unvollständige Liste mit zu berücksichtigenden Punkten:</span><span class="sxs-lookup"><span data-stu-id="af1c5-316">Here is a non-exhaustive list of things to consider:</span></span>

-   <span data-ttu-id="af1c5-317">Synchrone Methodenaufrufe über den Benutzeroberflächen-Thread einer Anwendung an den Server sollten immer vermieden werden.</span><span class="sxs-lookup"><span data-stu-id="af1c5-317">Synchronous method calls from application's UI thread to the server should always be avoided.</span></span> <span data-ttu-id="af1c5-318">Rufen Sie die Methode über einen Hintergrundthread in der Anwendung auf, und verwenden Sie dann bei Bedarf „CoreWindowDispatcher“, um die Ergebnisse in den Benutzeroberflächen-Thread zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="af1c5-318">Call the method from a background thread in the application and then use CoreWindowDispatcher to get the results onto the UI thread if necessary.</span></span>

-   <span data-ttu-id="af1c5-319">Das Aufrufen asynchroner Vorgänge aus dem Benutzeroberflächen-Thread einer Anwendung ist zwar sicher, aber Sie sollten dabei die nachfolgend erläuterten Leistungsprobleme berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="af1c5-319">Calling async operations from an application UI thread is safe, but consider the performance problems discussed below.</span></span>

-   <span data-ttu-id="af1c5-320">Eine Massenübertragung von Ergebnissen reduziert die prozessübergreifende "Geschwätzigkeit".</span><span class="sxs-lookup"><span data-stu-id="af1c5-320">Bulk transfer of results reduces cross-process chattiness.</span></span> <span data-ttu-id="af1c5-321">Dazu wird in der Regel das Windows-Runtime-Array-Konstrukt verwendet.</span><span class="sxs-lookup"><span data-stu-id="af1c5-321">This is normally performed by using the Windows Runtime Array construct.</span></span>

-   <span data-ttu-id="af1c5-322">Beim Zurückgeben von *List<T>*, wobei *T* ein Objekt aus einem asynchronen Vorgang oder einem Eigenschaftsabruf ist, wird viel „Geschwätzigkeit“ erzeugt.</span><span class="sxs-lookup"><span data-stu-id="af1c5-322">Returning *List<T>* where *T* is an object from an async operation or property fetch, will cause a lot of cross-process chattiness.</span></span> <span data-ttu-id="af1c5-323">Angenommen, Sie geben ein *List&lt;People&gt;*-Objekt zurück.</span><span class="sxs-lookup"><span data-stu-id="af1c5-323">For example, assume you return a*List&lt;People&gt;* objects.</span></span> <span data-ttu-id="af1c5-324">Bei jedem Iterationsdurchlauf handelt es sich um einen prozessübergreifenden Aufruf.</span><span class="sxs-lookup"><span data-stu-id="af1c5-324">Each iteration pass will be a cross-process call.</span></span> <span data-ttu-id="af1c5-325">Jedes zurückgegebene *People*-Objekt wird durch einen Proxy dargestellt, und jeder Methoden- oder Eigenschaftsaufruf für dieses einzelne Objekt führt zu einem prozessübergreifenden Aufruf.</span><span class="sxs-lookup"><span data-stu-id="af1c5-325">Each *People* object returned is represented by a proxy and each call to a method or property on that individual object will result in a cross-process call.</span></span> <span data-ttu-id="af1c5-326">Daher führt ein „harmloses“ *List&lt;People&gt;*-Objekt, wobei *Count* hoch ist, zu einer Vielzahl von langsamen Aufrufen.</span><span class="sxs-lookup"><span data-stu-id="af1c5-326">So an "innocent" *List&lt;People&gt;* object where *Count* is large will cause a large number of slow calls.</span></span> <span data-ttu-id="af1c5-327">Durch Massenübertragung von Inhaltsstrukturen in einem Array wird eine bessere Leistung erzielt.</span><span class="sxs-lookup"><span data-stu-id="af1c5-327">Better performance results from bulk transfer of structs of the content in an array.</span></span> <span data-ttu-id="af1c5-328">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="af1c5-328">For example:</span></span>

```csharp
struct PersonStruct
{
    String LastName;
    String FirstName;
    int Age;
   // etc.
}
```

<span data-ttu-id="af1c5-329">Geben Sie dann* PersonStruct\[\]* anstelle von *List&lt;PersonObject&gt;* zurück.</span><span class="sxs-lookup"><span data-stu-id="af1c5-329">Then return* PersonStruct\[\]* instead of *List&lt;PersonObject&gt;*.</span></span>
<span data-ttu-id="af1c5-330">Dadurch werden alle Daten in einem prozessübergreifenden Hop verteilt.</span><span class="sxs-lookup"><span data-stu-id="af1c5-330">This gets all the data across in one cross-process "hop"</span></span>

<span data-ttu-id="af1c5-331">Wie bei allen Überlegungen in Bezug auf die Leistung sind Messungen und Tests erforderlich.</span><span class="sxs-lookup"><span data-stu-id="af1c5-331">As with all performance considerations, measurement and testing is critical.</span></span> <span data-ttu-id="af1c5-332">Idealerweise sollte eine Telemetrie in die zahlreichen Vorgänge integriert werden, um deren Dauer zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="af1c5-332">Ideally telemetry should be inserted into the various operations to determine how long they take.</span></span> <span data-ttu-id="af1c5-333">Dabei ist es wichtig, einen Bereich zu messen: Wie lange dauert es beispielsweise tatsächlich, bis alle *People*-Objekte von einer bestimmten Warteschlange in der quergeladenen Anwendung verarbeitet wurden?</span><span class="sxs-lookup"><span data-stu-id="af1c5-333">It is important to measure across a range: for example, how long does it actually take to consume all the *People* objects for a particular query in the side-loaded application?</span></span>

<span data-ttu-id="af1c5-334">Eine weitere Technik ist das Testen variabler Lasten.</span><span class="sxs-lookup"><span data-stu-id="af1c5-334">Another technique is variable load testing.</span></span> <span data-ttu-id="af1c5-335">Dazu können Leistungstest-Hooks in die Anwendung eingefügt werden, die Lasten mit variabler Verzögerung in die Serververarbeitung integrieren.</span><span class="sxs-lookup"><span data-stu-id="af1c5-335">This can be done by putting performance test hooks into the application that introduce variable delay loads into the server processing.</span></span> <span data-ttu-id="af1c5-336">So können verschiedene Lastenarten und die Reaktion der Anwendung auf die variierende Serverleistung simuliert werden.</span><span class="sxs-lookup"><span data-stu-id="af1c5-336">This can simulate various kinds of load and the application's reaction to varying server performance.</span></span>
<span data-ttu-id="af1c5-337">Im Beispiel ist dargestellt, wie mithilfe entsprechender asynchroner Techniken Zeitverzögerungen in den Code eingefügt werden können.</span><span class="sxs-lookup"><span data-stu-id="af1c5-337">The sample illustrates how to put time delays into code using proper async techniques.</span></span> <span data-ttu-id="af1c5-338">Die genaue Dauer der zu integrierenden Verzögerung und die Zufallshäufigkeit für diese künstliche Last variieren je nach Anwendungsdesign und der voraussichtlichen Umgebung, in der die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="af1c5-338">The exact amount of delay to inject and the range of randomization to put into that artificial load will vary by application design and the anticipated environment in which the application will run.</span></span>

## <a name="development-process"></a><span data-ttu-id="af1c5-339">Entwicklungsprozess</span><span class="sxs-lookup"><span data-stu-id="af1c5-339">Development process</span></span>

<span data-ttu-id="af1c5-340">Wenn Sie Änderungen am Server vornehmen, müssen Sie sicherstellen, dass zuvor ausgeführte Instanzen nicht mehr ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="af1c5-340">When you make changes to the server, it is necessary to make sure any previously running instances are no longer running.</span></span> <span data-ttu-id="af1c5-341">COM sorgt schließlich für das Bereinigen des Prozesses, die vom Rundown-Timer benötigte Zeit ist jedoch zu lang für eine iterative Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="af1c5-341">COM will eventually scavenge the process, but the rundown timer takes longer than is efficient for iterative development.</span></span> <span data-ttu-id="af1c5-342">Das Beenden einer zuvor ausgeführten Instanz ist somit ein regulärer Schritt im Rahmen der Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="af1c5-342">Thus, killing a previously running instance is a normal step during development.</span></span> <span data-ttu-id="af1c5-343">Hierfür muss der Entwickler laufend verfolgen, welche dllhost-Instanz den Server hostet.</span><span class="sxs-lookup"><span data-stu-id="af1c5-343">This requires that the developer keep track of which dllhost instance is hosting the server.</span></span>

<span data-ttu-id="af1c5-344">Der Serverprozess kann im Task-Manager oder in anderen Drittanbieter-Apps aufgesucht und beendet werden.</span><span class="sxs-lookup"><span data-stu-id="af1c5-344">The server process can be found and killed using Task Manager or other third party apps.</span></span> <span data-ttu-id="af1c5-345">Das Befehlszeilentool **TaskList.exe **ist ebenfalls enthalten; es weist eine flexible Syntax wie die Folgende auf:</span><span class="sxs-lookup"><span data-stu-id="af1c5-345">The command line tool **TaskList.exe **is also included and has flexible syntax, for example:</span></span>

  
 | **<span data-ttu-id="af1c5-346">Befehl</span><span class="sxs-lookup"><span data-stu-id="af1c5-346">Command</span></span>** | **<span data-ttu-id="af1c5-347">Aktion</span><span class="sxs-lookup"><span data-stu-id="af1c5-347">Action</span></span>** |
 | ------------| ---------- |
 | <span data-ttu-id="af1c5-348">tasklist</span><span class="sxs-lookup"><span data-stu-id="af1c5-348">tasklist</span></span> | <span data-ttu-id="af1c5-349">Listet alle ausgeführten Prozesse in annähernder Reihenfolge des Erstellungszeitpunkts auf, wobei die zuletzt erstellten Prozesse unten aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="af1c5-349">Lists all the running processes in approximate order of creation time, with the most recently created processes near the bottom.</span></span> |
 | <span data-ttu-id="af1c5-350">tasklist /FI "IMAGENAME eq dllhost.exe" /M</span><span class="sxs-lookup"><span data-stu-id="af1c5-350">tasklist /FI "IMAGENAME eq dllhost.exe" /M</span></span> | <span data-ttu-id="af1c5-351">Listet Informationen zu allen Instanzen von „dllhost.exe“ auf.</span><span class="sxs-lookup"><span data-stu-id="af1c5-351">Lists info on all the dllhost.exe instances.</span></span> <span data-ttu-id="af1c5-352">Vom /M-Schalter werden die von ihnen geladenen Module aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="af1c5-352">The /M switch lists the modules that they have loaded.</span></span> |
 | <span data-ttu-id="af1c5-353">tasklist /FI "PID eq 12564" /M</span><span class="sxs-lookup"><span data-stu-id="af1c5-353">tasklist /FI "PID eq 12564" /M</span></span> | <span data-ttu-id="af1c5-354">Sie können mit dieser Option die „dllhost.exe“ abfragen, wenn Ihnen die zugehörige PID bekannt ist.</span><span class="sxs-lookup"><span data-stu-id="af1c5-354">You can use this option to query the dllhost.exe if you know its PID.</span></span> |

<span data-ttu-id="af1c5-355">In der Liste der Module für einen Broker-Server muss *clrhost.dll* als geladenes Modul aufgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="af1c5-355">The module list for a broker server should list *clrhost.dll* in its list of loaded modules.</span></span>

## <a name="resources"></a><span data-ttu-id="af1c5-356">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="af1c5-356">Resources</span></span>

-   [<span data-ttu-id="af1c5-357">Projektvorlagen für vermittelte WinRT-Komponenten für Windows10 und Visual Studio2015</span><span class="sxs-lookup"><span data-stu-id="af1c5-357">Brokered WinRT Component Project Templates for Windows 10 and VS 2015</span></span>](https://visualstudiogallery.msdn.microsoft.com/10be07b3-67ef-4e02-9243-01b78cd27935)

-   [<span data-ttu-id="af1c5-358">NorthwindRT-Beispiel zu Projektvorlagen für vermittelte WinRT-Komponenten</span><span class="sxs-lookup"><span data-stu-id="af1c5-358">NorthwindRT Brokered WinRT Component Sample</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=397349)

-   [<span data-ttu-id="af1c5-359">Bereitstellen von zuverlässigen und vertrauenswürdigen Microsoft Store-Apps</span><span class="sxs-lookup"><span data-stu-id="af1c5-359">Delivering reliable and trustworthy Microsoft Store apps</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=393644)

-   [<span data-ttu-id="af1c5-360">App-Verträge und -Erweiterungen (Windows Store-Apps)</span><span class="sxs-lookup"><span data-stu-id="af1c5-360">App contracts and extensions (Windows Store apps)</span></span>](https://msdn.microsoft.com/library/windows/apps/hh464906.aspx)

-   [<span data-ttu-id="af1c5-361">Querladen von Apps unter Windows10</span><span class="sxs-lookup"><span data-stu-id="af1c5-361">How to sideload apps on Windows 10</span></span>](https://msdn.microsoft.com/windows/uwp/get-started/enable-your-device-for-development#GroupPolicy)

-   [<span data-ttu-id="af1c5-362">Bereitstellen von UWP-Apps für Unternehmen</span><span class="sxs-lookup"><span data-stu-id="af1c5-362">Deploying UWP apps to businesses</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=264770)

