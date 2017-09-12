---
author: ptorr-msft
title: "Verwenden von MRT für konvertierte Desktop-Apps und -Spiele"
description: Dieses Whitepaper beschreibt die Verfahren zum Migrieren von .NET- und Win32-Apps von alten Win32-Ressourcen zu MRT-Ressourcen, wenn sie als AppX-Pakete gepackt sind.
ms.author: ptorr
ms.date: 03/09/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, mrt, pri. Ressourcen, Spiele, Centennial, Desktop App Converter, mui, Satellitenassembly
ms.openlocfilehash: 9a7d084b847a455e0759790054afad218b3a1f11
ms.sourcegitcommit: e7e8de39e963b73ba95cb34d8049e35e8d5eca61
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2017
---
# <a name="migrating-legacy-resources-to-the-windows-10-resource-management-platform"></a><span data-ttu-id="bcbff-105">Migrieren von Legacy-Ressourcen zur Ressourcenmanagement-Plattform von Windows10</span><span class="sxs-lookup"><span data-stu-id="bcbff-105">Migrating legacy resources to the Windows 10 resource management platform</span></span>

## <a name="executive-summary"></a><span data-ttu-id="bcbff-106">Kurzfassung</span><span class="sxs-lookup"><span data-stu-id="bcbff-106">Executive Summary</span></span>

<span data-ttu-id="bcbff-107">Win32-Anwendungen werden häufig in verschiedene Sprachen lokalisiert, um ihren Gesamtzielmarkt zu erweitern<a name="footnote1_ref" href="#footnote1"><sup>1</sup></a>.</span><span class="sxs-lookup"><span data-stu-id="bcbff-107">Win32 applications are often localized into different languages, expanding their total addressable market<a name="footnote1_ref" href="#footnote1"><sup>1</sup></a>.</span></span> <span data-ttu-id="bcbff-108">Es gibt viele Möglichkeiten zum Lokalisieren herkömmlicher Win32-Anwendungen, aber unter Windows8 wurde ein [neues Ressourcenverwaltungssystem](https://msdn.microsoft.com/en-us/library/windows/apps/jj552947.aspx) eingeführt (in diesem Dokument als „MRT” bezeichnet <a name="footnote2_ref" href="#footnote2"><sup>2</sup></a>), das sich für alle Programmiersprachen und alle App-Typen eignet und zusätzlich zu einer einfachen Lokalisierung Funktionalität bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="bcbff-108">There are many ways to localize traditional Win32 applications, but Windows 8 introduced a [new resource-management system](https://msdn.microsoft.com/en-us/library/windows/apps/jj552947.aspx) (referred to as "MRT" in this document <a name="footnote2_ref" href="#footnote2"><sup>2</sup></a>) that works across programming languages, across application types, and provides functionality over and above simple localization.</span></span> 

<span data-ttu-id="bcbff-109">In Kombination mit einer AppX-basierten Bereitstellung (z.B. über den Windows Store) kann MRT automatisch die am besten anwendbaren Ressourcen für einen bestimmten Benutzer/ein bestimmtes Gerät bereitstellen, wodurch die Größe des Downloads und der Installation der Anwendung verringert wird.</span><span class="sxs-lookup"><span data-stu-id="bcbff-109">Combined with AppX-based deployment (eg, from the Windows Store), MRT can automatically deliver the most-applicable resources for a given user / device which minimizes the download and install size of your application.</span></span> <span data-ttu-id="bcbff-110">Die Größenreduzierung kann bei Anwendungen mit einer großen Menge an lokalisiertem Inhalt erheblich sein, möglicherweise in einer Größenordnung von mehreren *Gigabytes* für AAA-Spiele.</span><span class="sxs-lookup"><span data-stu-id="bcbff-110">This size reduction can be significant for applications with a large amount of localized content, perhaps on the order of several *gigabytes* for AAA games.</span></span> <span data-ttu-id="bcbff-111">Weitere Vorteile von MRT sind lokalisierte Angebote in der Windows-Shell und im Windows Store sowie eine automatische Fallback-Logik, wenn die bevorzugte Sprache eines Benutzers nicht den verfügbaren Ressourcen entspricht.</span><span class="sxs-lookup"><span data-stu-id="bcbff-111">Additional benefits of MRT include localized listings in the Windows Shell and the Windows Store, automatic fallback logic when a user's preferred language doesn't match your available resources.</span></span>

<span data-ttu-id="bcbff-112">Dieses Dokument beschreibt die allgemeine MRT-Architektur und stellt ein Handbuch für das Portieren bereit, sodass ältere Win32-Anwendungen mit minimalen Codeänderungen zu MRT verschoben werden können.</span><span class="sxs-lookup"><span data-stu-id="bcbff-112">This document describes the high-level architecture of MRT and provides a porting guide to help move legacy Win32 applications to MRT with minimal code changes.</span></span> <span data-ttu-id="bcbff-113">Wenn der Wechsel zu MRT erfolgt sind, stehen Entwicklern weitere Vorteile zur Verfügung (z.B. die Möglichkeit, Ressourcen nach Skalierungsfaktor oder Systemdesign zu segmentieren).</span><span class="sxs-lookup"><span data-stu-id="bcbff-113">Once the move to MRT is made, additional benefits (such as the ability to segment resources by scale factor or system theme) become available to the developer.</span></span> <span data-ttu-id="bcbff-114">Beachten Sie, dass die MRT-basierte Lokalisierung sowohl für UWP-Anwendungen als auch für Win32-Anwendungen funktioniert, die von der Desktop-Brücke verarbeitet werden (auch bekannt als „Centennial”).</span><span class="sxs-lookup"><span data-stu-id="bcbff-114">Note that MRT-based localization works for both UWP applications and Win32 applications processed by the Desktop Bridge (aka "Centennial").</span></span>

<span data-ttu-id="bcbff-115">In vielen Fällen können Sie Ihre vorhandenen Lokalisierungsformate und Ihren Quellcode auch nach der Integration mit MRT noch verwenden, um Ressourcen zur Laufzeit aufzulösen und Downloadgrößen zu verringern – es ist kein „Ganz-oder-gar-nicht-Ansatz”.</span><span class="sxs-lookup"><span data-stu-id="bcbff-115">In many situations, you can continue to use your existing localization formats and source code whilst integrating with MRT for resolving resources at runtime and minimizing download sizes - it's not an all-or-nothing approach.</span></span> <span data-ttu-id="bcbff-116">In der folgenden Tabelle werden der Arbeitsaufwand und die geschätzte Kosten/Vorteile der einzelnen Phasen zusammengefasst <a name="footnote3_ref" href="#footnote3"><sup>3</sup></a>:</span><span class="sxs-lookup"><span data-stu-id="bcbff-116">The following table summarizes the work and estimated cost / benefit of each stage <a name="footnote3_ref" href="#footnote3"><sup>3</sup></a>:</span></span>

<table>
<tr>
<th><span data-ttu-id="bcbff-117">Arbeitsaufwand</span><span class="sxs-lookup"><span data-stu-id="bcbff-117">Work</span></span></th>
<th><span data-ttu-id="bcbff-118">Vorteil</span><span class="sxs-lookup"><span data-stu-id="bcbff-118">Benefit</span></span></th>
<th><span data-ttu-id="bcbff-119">Geschätzte Kosten</span><span class="sxs-lookup"><span data-stu-id="bcbff-119">Estimated cost</span></span></th>
</tr>
<tr>
<td><span data-ttu-id="bcbff-120">Lokalisieren von AppX-Manifest</span><span class="sxs-lookup"><span data-stu-id="bcbff-120">Localize AppX manifest</span></span></td>
<td><span data-ttu-id="bcbff-121">Äußerst wenig Arbeitsaufwand erforderlich, damit der lokalisierte Inhalt in der Windows-Shell und im Windows Store angezeigt wird</span><span class="sxs-lookup"><span data-stu-id="bcbff-121">Bare minimum work required to have your localized content appear in the Windows Shell and in the Windows Store</span></span></td>
<td><span data-ttu-id="bcbff-122">Gering</span><span class="sxs-lookup"><span data-stu-id="bcbff-122">Small</span></span></td>
</tr>
<tr>
<td><span data-ttu-id="bcbff-123">Verwenden von MRT zum Erkennen und Suchen von Ressourcen</span><span class="sxs-lookup"><span data-stu-id="bcbff-123">Use MRT to identify and locate resources</span></span></td>
<td><span data-ttu-id="bcbff-124">Voraussetzung für die Verringerung der Download- und Installationsgrößen; automatischer Fallback für Sprachen</span><span class="sxs-lookup"><span data-stu-id="bcbff-124">Pre-requisite to minimizing download and install sizes; automatic language fallback</span></span></td>
<td><span data-ttu-id="bcbff-125">Mittel</span><span class="sxs-lookup"><span data-stu-id="bcbff-125">Medium</span></span></td>
</tr>
<tr>
<td><span data-ttu-id="bcbff-126">Erstellen von Ressourcenpaketen</span><span class="sxs-lookup"><span data-stu-id="bcbff-126">Build resource packs</span></span></td>
<td><span data-ttu-id="bcbff-127">Letzter Schritt für die Verringerung der Download- und Installationsgrößen</span><span class="sxs-lookup"><span data-stu-id="bcbff-127">Final step to minimize download and install sizes</span></span></td>
<td><span data-ttu-id="bcbff-128">Gering</span><span class="sxs-lookup"><span data-stu-id="bcbff-128">Small</span></span></td>
</tr>
<tr>
<td><span data-ttu-id="bcbff-129">Migrieren von MRT-Ressourcenformaten und APIs</span><span class="sxs-lookup"><span data-stu-id="bcbff-129">Migrate to MRT resource formats and APIs</span></span></td>
<td><span data-ttu-id="bcbff-130">Erheblich geringere Dateigrößen (je nach vorhandener Ressourcentechnologie)</span><span class="sxs-lookup"><span data-stu-id="bcbff-130">Significantly smaller file sizes (depending on existing resource technology)</span></span></td>
<td><span data-ttu-id="bcbff-131">Hoch</span><span class="sxs-lookup"><span data-stu-id="bcbff-131">Large</span></span></td>
</tr>
</table>

## <a name="introduction"></a><span data-ttu-id="bcbff-132">Einführung</span><span class="sxs-lookup"><span data-stu-id="bcbff-132">Introduction</span></span>

<span data-ttu-id="bcbff-133">Die meisten umfassenden Anwendungen enthalten Benutzeroberflächenelemente, auch als *Ressourcen* bezeichnet, die von dem Code der Anwendung entkoppelt werden (im Gegensatz zu *hartcodierten Werte*, die im Quellcode selbst verfasst werden).</span><span class="sxs-lookup"><span data-stu-id="bcbff-133">Most non-trivial applications contain user-interface elements known as *resources* that are decoupled from the application's code (contrasted with *hard-coded values* that are authored in the source code itself).</span></span> <span data-ttu-id="bcbff-134">Es gibt verschiedene Gründe dafür, Ressourcen gegenüber hartcodierten Werten zu bevorzugen – wie beispielsweise die einfache Bearbeitung durch Nicht-Entwickler –, einer der wichtigsten Gründe ist jedoch, dass die App auf diese Weise verschiedene Darstellungen derselben logischen Ressource zur Laufzeit auswählen kann.</span><span class="sxs-lookup"><span data-stu-id="bcbff-134">There are several reasons to prefer resources over hard-coded values - ease of editing by non-developers, for example - but one of the key reasons is to enable the application to pick different representations of the same logical resource at runtime.</span></span> <span data-ttu-id="bcbff-135">Beispielsweise unterscheidet sich der auf einer Schaltfläche anzuzeigende Text (oder das in einem Symbol anzuzeigende Bild) abhängig von der/den Sprache(n), die ein Benutzer versteht, den Eigenschaften des Anzeigegeräts oder davon, ob eine Hilfstechnologie aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="bcbff-135">For example, the text to display on a button (or the image to display in an icon) might differ depending on the language(s) the user understands, the characteristics of the display device, or whether the user has any assistive technologies enabled.</span></span>

<span data-ttu-id="bcbff-136">Daher besteht der Hauptzweck von Ressourcenverwaltungstechnologien darin, zur Laufzeit eine Anfrage für einen logischen oder symbolischen *Ressourcennamen* (z.B. `SAVE_BUTTON_LABEL`) aus einer Reihe von möglichen *Kandidaten* (z.B. „Save”, „Speichern” oder „저장”) in den bestmöglichen tatsächlichen *Wert* (z.B. „Speichern”) zu übersetzen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-136">Thus the primary purpose of any resource-management technology is to translate, at runtime, a request for a logical or symbolic *resource name* (such as `SAVE_BUTTON_LABEL`) into the best possible actual *value* (eg, "Save") from a set of possible *candidates* (eg, "Save", "Speichern", or "저장").</span></span> <span data-ttu-id="bcbff-137">MRT stellt eine solche Funktion bereit und ermöglicht es Anwendungen, Ressourcenkandidaten mithilfe von verschiedenen Attributen, den *Qualifizierern*, wie beispielsweise der Sprache des Benutzers, dem Skalierungsfaktor des Displays, dem ausgewählten Design des Benutzers und anderen Umgebungsfaktoren, zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="bcbff-137">MRT provides such a function, and enables applications to identify resource candidates using a wide variety of attributes, called *qualifiers*, such as the user's language, the display scale-factor, the user's selected theme, and other environmental factors.</span></span> <span data-ttu-id="bcbff-138">MRT unterstützt auch benutzerdefinierte Qualifizierer für Anwendungen, die diese benötigen (beispielsweise könnte eine Anwendung für Benutzer, die sich mit einem Konto angemeldet haben, und für Gastbenutzer unterschiedliche grafische Ressourcen bereitstellen, ohne dass diese Prüfung explizit zu jedem Teil der Anwendung hinzugefügt wird).</span><span class="sxs-lookup"><span data-stu-id="bcbff-138">MRT even supports custom qualifiers for applications that need it (for example, an application could provide different graphic assets for users that had logged in with an account vs. guest users, without explicitly adding this check into every part of their application).</span></span> <span data-ttu-id="bcbff-139">MRT funktioniert sowohl mit Zeichenfolgenressourcen als auch mit dateibasierten Ressourcen, wenn dateibasierte Ressourcen als Verweise auf die externen Daten (die Dateien selbst) implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="bcbff-139">MRT works with both string resources and file-based resources, where file-based resources are implemented as references to the external data (the files themselves).</span></span> 

### <a name="example"></a><span data-ttu-id="bcbff-140">Beispiel</span><span class="sxs-lookup"><span data-stu-id="bcbff-140">Example</span></span>

<span data-ttu-id="bcbff-141">Dies ist ein einfaches Beispiel für eine Anwendung mit Beschriftungen auf zwei Schaltflächen (`openButton` und `saveButton`) und einer PNG-Datei, die für ein Logo verwendet wird (`logoImage`).</span><span class="sxs-lookup"><span data-stu-id="bcbff-141">Here's a simple example of an application that has text labels on two buttons (`openButton` and `saveButton`) and a PNG file used for a logo (`logoImage`).</span></span> <span data-ttu-id="bcbff-142">Die Beschriftungen werden ins Englische und ins Deutsche lokalisiert, und das Logo ist für normale Desktopdisplays (Skalierungsfaktor 100%) und hochauflösende Smartphones (Skalierungsfaktor 300%) optimiert <a name="footnote4_ref" href="#footnote4"><sup>4</sup></a>.</span><span class="sxs-lookup"><span data-stu-id="bcbff-142">The text labels are localized into English and German, and the logo is optimized for normal desktop displays (100% scale factor) and hi-resolution phones (300% scale factor) <a name="footnote4_ref" href="#footnote4"><sup>4</sup></a>.</span></span> <span data-ttu-id="bcbff-143">Beachten Sie, dass dieses Diagramm eine allgemeine konzeptionelle Ansicht des Modells darstellt. Es wird der Implementierung nicht genau zugeordnet:</span><span class="sxs-lookup"><span data-stu-id="bcbff-143">Note this diagram presents a high-level, conceptual view of the model; it does not map exactly to implementation:</span></span>

<p><img src="images\conceptual-resource-model.png"/></p>

<span data-ttu-id="bcbff-144">In der Grafik verweist der Anwendungscode auf die drei logischen Ressourcennamen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-144">In the graphic, the application code references the three logical resource names.</span></span> <span data-ttu-id="bcbff-145">Zur Laufzeit verwendet die Pseudo-Funktion `GetResource` MRT, um diese Ressourcennamen in der Ressourcentabelle (als PRI-Datei bezeichnet) zu suchen und basierend auf den Umgebungsbedingungen (der Sprache des Benutzers und dem Skalierungsfaktor des Displays) den am besten geeigneten Kandidaten zu finden.</span><span class="sxs-lookup"><span data-stu-id="bcbff-145">At runtime, the `GetResource` pseudo-function uses MRT to look those resource names up in the resource table (known as PRI file) and find the most appropriate candidate based on the ambient conditions (the user's language and the display's scale-factor).</span></span> <span data-ttu-id="bcbff-146">Bei Beschriftungen werden die Zeichenfolgen direkt verwendet.</span><span class="sxs-lookup"><span data-stu-id="bcbff-146">In the case of the labels, the strings are used directly.</span></span> <span data-ttu-id="bcbff-147">Beim Logobild werden die Zeichenfolgen als Dateinamen interpretiert, und die Dateien werden von der Festplatte gelesen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-147">In the case of the logo image, the strings are interpreted as filenames and the files are read off disk.</span></span> 

<span data-ttu-id="bcbff-148">Wenn der Benutzer eine andere Sprache als Englisch oder Deutsch spricht oder einen anderen Skalierungsfaktor als 100% oder 300% verwendet, wählt MRT auf Grundlager einer Reihe von Fallbackregeln den Kandidaten mit den größten Übereinstimmung (weitere Hintergrundinformationen dazu im [Thema **Ressourcenverwaltungssystem** auf MSDN](https://msdn.microsoft.com/en-us/library/windows/apps/jj552947.aspx)).</span><span class="sxs-lookup"><span data-stu-id="bcbff-148">If the user speaks a language other than English or German, or has a display scale-factor other than 100% or 300%, MRT picks the "closest" matching candidate based on a set of fallback rules (see [the **Resource Management System** topic on MSDN](https://msdn.microsoft.com/en-us/library/windows/apps/jj552947.aspx) for more background).</span></span> 

<span data-ttu-id="bcbff-149">Beachten Sie, dass MRT Ressourcen unterstützt, die auf mehrere Qualifizierer zugeschnitten sind – wenn beispielsweise das Logobild eingebetteten Text enthält, der auch lokalisiert werden muss, würde das Logo über vier Kandidaten verfügen: EN/Scale-100, DE/Scale-100, EN/Scale-300 and DE/Scale-300.</span><span class="sxs-lookup"><span data-stu-id="bcbff-149">Note that MRT supports resources that are tailored to more than one qualifier - for example, if the logo image contained embedded text that also needed to be localized, the logo would have four candidates: EN/Scale-100, DE/Scale-100, EN/Scale-300 and DE/Scale-300.</span></span>

### <a name="sections-in-this-document"></a><span data-ttu-id="bcbff-150">Abschnitte in diesem Dokument</span><span class="sxs-lookup"><span data-stu-id="bcbff-150">Sections in this document</span></span>

<span data-ttu-id="bcbff-151">In den folgenden Abschnitten werden die allgemeinen Aufgaben dargestellt, die für die Integration von MRT in Ihre Anwendung erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="bcbff-151">The following sections outline the high-level tasks required to integrate MRT with your application.</span></span>

**<span data-ttu-id="bcbff-152">Phase 0: Erstellen eines Anwendungspakets</span><span class="sxs-lookup"><span data-stu-id="bcbff-152">Phase 0: Build an application package</span></span>**

<span data-ttu-id="bcbff-153">In diesem Abschnitt wird beschrieben, wie Sie Ihre vorhandene Desktopanwendung zu einem Anwendungspaket machen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-153">This section outlines how to get your existing Desktop application building as an application package.</span></span> <span data-ttu-id="bcbff-154">In dieser Phase werden keine MRT-Features verwendet.</span><span class="sxs-lookup"><span data-stu-id="bcbff-154">No MRT features are used at this stage.</span></span>

**<span data-ttu-id="bcbff-155">Phase 1: Lokalisieren des Anwendungsmanifests</span><span class="sxs-lookup"><span data-stu-id="bcbff-155">Phase 1: Localize the application manifest</span></span>**

<span data-ttu-id="bcbff-156">In diesem Abschnitt wird beschrieben, wie Sie das Manifest Ihrer Anwendung lokalisieren (damit es richtig in der Windows-Shell angezeigt wird), während noch Ihr älteres Ressourcenformat und Ihre älteren APIs verwendet werden, um Ressourcen zu packen und zu suchen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-156">This section outlines how to localize your application's manifest (so that it appears correctly in the Windows Shell) whilst still using your legacy resource format and API to package and locate resources.</span></span> 

**<span data-ttu-id="bcbff-157">Phase 2: Verwenden von MRT, um Ressourcen zu identifizieren und zu suchen</span><span class="sxs-lookup"><span data-stu-id="bcbff-157">Phase 2: Use MRT to identify and locate resources</span></span>**

<span data-ttu-id="bcbff-158">In diesem Abschnitt wird beschrieben, wie Sie Ihren Anwendungscode (und gegebenenfalls das Ressourcenlayout) so ändern, dass eine Suche von Ressourcen mithilfe von MRT möglich ist, während noch Ihre vorhandenen Ressourcenformate und Ihre älteren APIs verwendet werden, um die Ressourcen zu laden und zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="bcbff-158">This section outlines how to modify your application code (and possibly resource layout) to locate resources using MRT, whilst still using your existing resource formats and APIs to load and consume the resources.</span></span> 

**<span data-ttu-id="bcbff-159">Phase 3: Erstellen von Ressourcenpaketen</span><span class="sxs-lookup"><span data-stu-id="bcbff-159">Phase 3: Build resource packs</span></span>**

<span data-ttu-id="bcbff-160">In diesem Abschnitt werden die endgültigen Änderungen beschrieben, die erforderlich sind, um Ihre Ressourcen in separate *Ressourcenpakete* zu teilen, wodurch die Größe des Downloads (und der Installation) Ihrer App verringert wird.</span><span class="sxs-lookup"><span data-stu-id="bcbff-160">This section outlines the final changes needed to separate your resources into separate *resource packs*, minimizing the download (and install) size of your app.</span></span>

### <a name="not-covered-in-this-document"></a><span data-ttu-id="bcbff-161">In diesem Dokument nicht behandelt</span><span class="sxs-lookup"><span data-stu-id="bcbff-161">Not covered in this document</span></span>

<span data-ttu-id="bcbff-162">Nach Abschluss der oben beschriebenen Phasen 0 bis 3 verfügen Sie über ein „Anwendungsbündel”, das an den Windows Store übermittelt werden kann und das die Größe für den Download und die Installation für Benutzer verringert, indem die nicht benötigten Ressourcen ausgelassen werden (wie beispielsweise Sprachen, die sie nicht sprechen).</span><span class="sxs-lookup"><span data-stu-id="bcbff-162">After completing Phases 0-3 above, you will have an application "bundle" that can be submitted to the Windows Store and that will minimize the download & install size for users by omitting the resources they don't need (eg, languages they don't speak).</span></span> <span data-ttu-id="bcbff-163">Weitere Verbesserungen hinsichtlich Größe der Anwendung und Funktionen können über einen letzten Schritt vorgenommen werden.</span><span class="sxs-lookup"><span data-stu-id="bcbff-163">Further improvements in application size and functionality can be made by taking one final step.</span></span> 

**<span data-ttu-id="bcbff-164">Phase 4: Migrieren von MRT-Ressourcenformaten und APIs</span><span class="sxs-lookup"><span data-stu-id="bcbff-164">Phase 4: Migrate to MRT resource formats and APIs</span></span>**

<span data-ttu-id="bcbff-165">Diese Phase kann in diesem Dokument nicht behandelt werden. Sie umfasst das Übertragen Ihrer Ressourcen (insbesondere Zeichenfolgen) von älteren Formate wie beispielsweise MUI DLLs oder.NET-Ressourcenassemblys in PRI-Dateien.</span><span class="sxs-lookup"><span data-stu-id="bcbff-165">This phase is beyond the scope of this document; it entails moving your resources (particularly strings) from legacy formats such as MUI DLLs or .NET resource assemblies into PRI files.</span></span> <span data-ttu-id="bcbff-166">Dies kann zu einer weiteren Platzeinsparung hinsichtlich der Größen für den Download und die Installation führen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-166">This can lead to further space savings for download & install sizes.</span></span> <span data-ttu-id="bcbff-167">Es ermöglicht darüber hinaus die Verwendung weiterer MRT-Features, z.B. das Verringern der Größen für den Download und die Installation von Bilddateien auf Grundlage eines Skalierungsfaktors, Barrierefreiheiteinstellungen usw.</span><span class="sxs-lookup"><span data-stu-id="bcbff-167">It also allows use of other MRT features such as minimizing the download and install of image files by based on scale factor, accessibility settings, and so on.</span></span>

- - -

## <a name="phase-0-build-an-application-package"></a><span data-ttu-id="bcbff-168">Phase 0: Erstellen eines Anwendungspakets</span><span class="sxs-lookup"><span data-stu-id="bcbff-168">Phase 0: Build an application package</span></span>

<span data-ttu-id="bcbff-169">Bevor Sie Änderungen an den Ressourcen Ihrer Anwendung vornehmen, müssen Sie zunächst Ihre aktuelle Paketerstellungs- und Installationstechnologie durch die standardmäßige UWP-Paketerstellungs und Bereitstellungstechnologie ersetzen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-169">Before you make any changes to your application's resources, you must first replace your current packaging and installation technology with the standard UWP packaging and deployment technology.</span></span> <span data-ttu-id="bcbff-170">Hierfür gibt es drei Möglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="bcbff-170">There are three ways to do this:</span></span>

0. <span data-ttu-id="bcbff-171">Wenn Sie über eine große Desktopanwendung mit einem komplexen Installationsprogramm verfügen oder viele Erweiterungspunkte für das Betriebssystem verwenden, können Sie das Tool Desktop App Converter verwenden, um das Layout der UWP-Datei und die Manifestinformationen aus dem vorhandenen App-Installationsprogramm (z.B. eine MSI-Datei) zu generieren.</span><span class="sxs-lookup"><span data-stu-id="bcbff-171">If you have a large Desktop application with a complex installer or you utilize lots of OS extensibility points, you can use the Desktop App Converter tool to generate the UWP file layout and manifest information from your existing app installer (eg, an MSI)</span></span>
0. <span data-ttu-id="bcbff-172">Wenn Sie über eine kleinere Desktopanwendung mit relativ wenigen Dateien oder einem einfachen Installationsprogramm und keinen Hooks für die Erweiterbarkeit verfügen, können Sie das Dateilayout und die Manifestinformationen manuell erstellen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-172">If you have a smaller Desktop application with relatively few files or a simple installer and no extensibility hooks, you can create the file layout and manifest information manually</span></span>
0. <span data-ttu-id="bcbff-173">Wenn Sie eine Neuerstellung aus der Quelle vornehmen und Ihre App so aktualisieren möchten, dass sie eine „reine” UWP-Anwendung ist, können Sie ein neues Projekt in Visual Studio erstellen und die IDE einen Großteil der Arbeit durchführen lassen</span><span class="sxs-lookup"><span data-stu-id="bcbff-173">If you're rebuilding from source and want to update your app to be a "pure" UWP application, you can create a new project in Visual Studio and rely on the IDE to do much of the work for you</span></span>

<span data-ttu-id="bcbff-174">Wenn Sie den [Desktop App Converter](https://aka.ms/converter) verwenden möchten, können Sie im [Thema **Desktop-zu-UWP-Brücke: Desktop App Converter** auf MSDN](https://aka.ms/converterdocs) weitere Informationen zum Konvertierungsprozess finden.</span><span class="sxs-lookup"><span data-stu-id="bcbff-174">If you want to use the [Desktop App Converter](https://aka.ms/converter), please refer to [the **Desktop to UWP Bridge: Desktop App Converter** topic on MSDN](https://aka.ms/converterdocs) for more information on the conversion process.</span></span> <span data-ttu-id="bcbff-175">Einen vollständigen Satz an Desktop Converter-Beispielen finden Sie im [GitHub-Repository **Desktop-Brücke-zu-UWP – Beispiele**](https://github.com/Microsoft/DesktopBridgeToUWP-Samples).</span><span class="sxs-lookup"><span data-stu-id="bcbff-175">A complete set of Desktop Converter samples can be found on [the **Desktop Bridge to UWP samples** GitHub repo](https://github.com/Microsoft/DesktopBridgeToUWP-Samples).</span></span>

<span data-ttu-id="bcbff-176">Wenn Sie das Paket manuell erstellen möchten, müssen Sie eine Verzeichnisstruktur erstellen, die alle Dateien Ihrer Anwendung (ausführbare Dateien und Inhalte, aber keinen Quellcode) und eine `AppXManifest.xml`-Datei enthält.</span><span class="sxs-lookup"><span data-stu-id="bcbff-176">If you want to manually create the package, you will need to create a directory structure that includes all your application's files (executables and content, but not source code) and an `AppXManifest.xml` file.</span></span> <span data-ttu-id="bcbff-177">Ein Beispiel finden Sie im [GitHub-Beispiel **Hello, World**](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/blob/master/Samples/HelloWorldSample/CentennialPackage/AppxManifest.xml); eine einfache `AppXManifest.xml` -Datei, die die ausführbare Desktopdatei mit dem Namen `ContosoDemo.exe` ausführt, würde folgendermaßen aussehen, wobei der <span style="background-color: yellow">hervorgehobene Text</span> mit Ihren eigenen Werte ersetzt würde:</span><span class="sxs-lookup"><span data-stu-id="bcbff-177">An example can be found in [the **Hello, World** GitHub sample](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/blob/master/Samples/HelloWorldSample/CentennialPackage/AppxManifest.xml), but a basic `AppXManifest.xml` file that runs the Desktop executable named `ContosoDemo.exe` is as follows, where the <span style="background-color: yellow">highlighted text</span> would be replaced by your own values:</span></span>

<blockquote>
<pre>
&lt;?xml version="1.0" encoding="utf-8" ?&gt;
&lt;Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
         xmlns:rescap="http://schemas.microsoft.com/appx/manifest/foundation/windows10/restrictedcapabilities"
         IgnorableNamespaces="uap mp rescap"&gt;
    &lt;Identity Name="<span style="background-color: yellow">Contoso.Demo</span>"
              Publisher="<span style="background-color: yellow">CN=Contoso.Demo</span>"
              Version="<span style="background-color: yellow">1.0.0.0</span>" /&gt;
    &lt;Properties&gt;
    &lt;DisplayName&gt;<span style="background-color: yellow">Contoso App</span>&lt;/DisplayName&gt;
    &lt;PublisherDisplayName&gt;<span style="background-color: yellow">Contoso, Inc</span>&lt;/PublisherDisplayName&gt;
    &lt;Logo&gt;Assets\StoreLogo.png&lt;/Logo&gt;
  &lt;/Properties&gt;
    &lt;Dependencies&gt;
    &lt;TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.14393.0" 
                        MaxVersionTested="10.0.14393.0" /&gt;
  &lt;/Dependencies&gt;
    &lt;Resources&gt;
    &lt;Resource Language="<span style="background-color: yellow">en-US</span>" /&gt;
  &lt;/Resources&gt;
    &lt;Applications&gt;
    &lt;Application Id="<span style="background-color: yellow">ContosoDemo</span>" Executable="<span style="background-color: yellow">ContosoDemo.exe</span>" 
                 EntryPoint="Windows.FullTrustApplication"&gt;
    &lt;uap:VisualElements DisplayName="<span style="background-color: yellow">Contoso Demo</span>" BackgroundColor="#777777" 
                        Square150x150Logo="Assets\Square150x150Logo.png" 
                        Square44x44Logo="Assets\Square44x44Logo.png" 
        Description="<span style="background-color: yellow">Contoso Demo</span>"&gt;
      &lt;/uap:VisualElements&gt;
    &lt;/Application&gt;
  &lt;/Applications&gt;
    &lt;Capabilities&gt;
    &lt;rescap:Capability Name="runFullTrust" /&gt;
  &lt;/Capabilities&gt;
&lt;/Package&gt;
</pre>
</blockquote>

<span data-ttu-id="bcbff-178">Weitere Informationen zur Datei `AppXManifest.xml` und dem Paketlayout finden Sie im [Thema **App-Paketmanifest** auf MSDN](https://msdn.microsoft.com/en-us/library/windows/apps/br211474.aspx).</span><span class="sxs-lookup"><span data-stu-id="bcbff-178">For more information about the `AppXManifest.xml` file and package layout, see [the **App package manifest** topic on MSDN](https://msdn.microsoft.com/en-us/library/windows/apps/br211474.aspx).</span></span>

<span data-ttu-id="bcbff-179">Wenn Sie zum Erstellen eines neuen Projekts und zum Migrieren des vorhandenen Codes Visual Studio verwenden, können Sie weitere Informationen in der [MSDN-Dokumentation für die Erstellung eines neuen UWP-Projekts](https://msdn.microsoft.com/en-us/windows/uwp/get-started/create-a-hello-world-app-xaml-universal) finden.</span><span class="sxs-lookup"><span data-stu-id="bcbff-179">Finally, if you're using Visual Studio to create a new project and migrate your existing code across, see [the MSDN documentation for building a new UWP project](https://msdn.microsoft.com/en-us/windows/uwp/get-started/create-a-hello-world-app-xaml-universal).</span></span> <span data-ttu-id="bcbff-180">Sie können den vorhandenen Code in das neue Projekt einfügen, Sie müssen aber wahrscheinlich noch erhebliche Änderungen am Code vornehmen (insbesondere in der Benutzeroberfläche), damit die App als „reine” UWP-App ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="bcbff-180">You can include your existing code into the new project, but you will likely have to make significant code changes (particularly in the user interface) in order to run as a "pure" UWP.</span></span> <span data-ttu-id="bcbff-181">Diese Änderungen werden in diesem Dokument nicht behandelt.</span><span class="sxs-lookup"><span data-stu-id="bcbff-181">These changes are outside the scope of this document.</span></span>

***

## <a name="phase-1-localize-the-application-manifest"></a><span data-ttu-id="bcbff-182">Phase 1: Lokalisieren des Anwendungsmanifests</span><span class="sxs-lookup"><span data-stu-id="bcbff-182">Phase 1: Localize the application manifest</span></span>

### <a name="step-11-update-strings--assets-in-the-appxmanifest"></a><span data-ttu-id="bcbff-183">Schritt1.1: Aktualisieren von Zeichenfolgen und Ressourcen in AppXManifest</span><span class="sxs-lookup"><span data-stu-id="bcbff-183">Step 1.1: Update strings & assets in the AppXManifest</span></span>

<span data-ttu-id="bcbff-184">In Phase 0 haben Sie eine einfache `AppXManifest.xml`-Datei für Ihre Anwendung erstellt (basierend auf dem Converter bereitgestellten Werten, die aus der MSI-Datei extrahiert oder manuell in das Paketmanifest eingegeben wurden). Diese enthält jedoch weder lokalisierte Informationen noch werden zusätzliche Features wie Ressourcen für Startkacheln mit hoher Auflösung usw. unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bcbff-184">In Phase 0 you created a basic `AppXManifest.xml` file for your application (based on values provided to the converter, extracted from the MSI, or manually entered into the manifest) but it will not contain localized information, nor will it support additional features like high-resolution Start tile assets, etc.</span></span> 

<span data-ttu-id="bcbff-185">Um sicherzustellen, dass der Name und die Beschreibung Ihrer Anwendung richtig lokalisiert sind, müssen Sie einige Ressourcen in einer Reihe von Ressourcendateien definieren und AppX-Manifest aktualisieren, damit diese Datei auf sie verweist.</span><span class="sxs-lookup"><span data-stu-id="bcbff-185">To ensure your application's name and description are correctly localized, you must define some resources in a set of resource files, and update the AppX Manifest to reference them.</span></span>

**<span data-ttu-id="bcbff-186">Erstellen eine Standardressourcendatei</span><span class="sxs-lookup"><span data-stu-id="bcbff-186">Creating a default resource file</span></span>**

<span data-ttu-id="bcbff-187">Der erste Schritt ist das Erstellen einer Standardressourcendatei in der Standardsprache (z.B. Englisch (USA)).</span><span class="sxs-lookup"><span data-stu-id="bcbff-187">The first step is to create a default resource file in your default language (eg, US English).</span></span> <span data-ttu-id="bcbff-188">Sie können dies entweder manuell mit einem Text-Editor oder über den Ressourcen-Designer in Visual Studio vornehmen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-188">You can do this either manually with a text editor, or via the Resource Designer in Visual Studio.</span></span>

<span data-ttu-id="bcbff-189">Wenn Sie die Ressourcen manuell erstellen möchten:</span><span class="sxs-lookup"><span data-stu-id="bcbff-189">If you want to create the resources manually:</span></span>

0. <span data-ttu-id="bcbff-190">Erstellen Sie eine XML-Datei mit dem Namen `resources.resw`, und legen Sie sie in einem `Strings\en-us`-Unterordner Ihres Projekts ab.</span><span class="sxs-lookup"><span data-stu-id="bcbff-190">Create an XML file named `resources.resw` and place it in a `Strings\en-us` subfolder of your project.</span></span> 
 * <span data-ttu-id="bcbff-191">Verwenden Sie den entsprechenden Code BCP-47, wenn die Standardsprache nicht Englisch (USA) ist.</span><span class="sxs-lookup"><span data-stu-id="bcbff-191">Use the appropriate BCP-47 code if your default language is not US English</span></span> 
0. <span data-ttu-id="bcbff-192">Fügen Sie in der XML-Datei den folgenden Inhalt in Ihrer Standardsprache hinzu, sodass der <span style="background-color: yellow">hervorgehobene Text</span> mit dem entsprechenden Text für Ihre App ersetzt wird<a name="footnote5_ref" href="#footnote5"><sup>5</sup></a></span><span class="sxs-lookup"><span data-stu-id="bcbff-192">In the XML file, add the following content, where the <span style="background-color: yellow">highlighted text</span> is replaced with the appropriate text for your app, in your default language<a name="footnote5_ref" href="#footnote5"><sup>5</sup></a></span></span>

<blockquote>
<pre>
&lt;?xml version="1.0" encoding="utf-8"?&gt;
&lt;root&gt;
  &lt;data name="ApplicationDescription"&gt;
    &lt;value&gt;<span style="background-color: yellow">Contoso Demo app with localized resources (English)</span>&lt;/value&gt;
  &lt;/data&gt;
  &lt;data name="ApplicationDisplayName"&gt;
    &lt;value&gt;<span style="background-color: yellow">Contoso Demo Sample (English)</span>&lt;/value&gt;
  &lt;/data&gt;
  &lt;data name="PackageDisplayName"&gt;
    &lt;value&gt;<span style="background-color: yellow">Contoso Demo Package (English)</span>&lt;/value&gt;
  &lt;/data&gt;
  &lt;data name="PublisherDisplayName"&gt;
    &lt;value&gt;<span style="background-color: yellow">Contoso Samples, USA</span>&lt;/value&gt;
  &lt;/data&gt;
  &lt;data name="TileShortName"&gt;
    &lt;value&gt;<span style="background-color: yellow">Contoso (EN)</span>&lt;/value&gt;
  &lt;/data&gt;
&lt;/root&gt;
</pre>
</blockquote>

<span data-ttu-id="bcbff-193">Wenn Sie den Designer in Visual Studio verwenden möchten:</span><span class="sxs-lookup"><span data-stu-id="bcbff-193">If you want to use the designer in Visual Studio:</span></span>

0. <span data-ttu-id="bcbff-194">Erstellen Sie den Ordner `Strings\en-us` (oder nach Bedarf eine andere Sprache ) in Ihrem Projekt, und fügen Sie ein **Neues Element** zum Stammordner des Projekts hinzu. Verwenden Sie dabei den Standardnamen</span><span class="sxs-lookup"><span data-stu-id="bcbff-194">Create the `Strings\en-us` folder (or other language as appropriate) in your project and add a **New Item** to the root folder of your project, using the default name of</span></span> `resources.resw`
 * <span data-ttu-id="bcbff-195">Wählen Sie **Ressourcendatei (.resw)** und nicht **Ressourcenverzeichnis** – ein Ressourcenverzeichnis ist eine Datei, die von XAML-Anwendungen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="bcbff-195">Be sure to choose **Resources File (.resw)** and not **Resource Dictionary** - a Resource Dictionary is a file used by XAML applications</span></span>
0. <span data-ttu-id="bcbff-196">Geben Sie im Designer die folgenden Zeichenfolgen ein (verwenden Sie dieselben `Names`, ersetzen Sie die `Values` jedoch mit dem entsprechenden Text für Ihre Anwendung):</span><span class="sxs-lookup"><span data-stu-id="bcbff-196">Using the designer, enter the following strings (use the same `Names` but replace the `Values` with the appropriate text for your application):</span></span>

<img src="images\editing-resources-resw.png"/>

<span data-ttu-id="bcbff-197">Hinweis: Wenn Sie mit dem Visual Studio-Designer starten, können Sie die XML-Datei jederzeit durch Drücken von `F7` bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="bcbff-197">Note: if you start with the Visual Studio designer, you can always edit the XML directly by pressing `F7`.</span></span> <span data-ttu-id="bcbff-198">Wenn Sie jedoch mit einer kleinen XML-Datei starten, *erkennt der Designer die Datei nicht*, weil viele zusätzliche Metadaten fehlen. Dies lässt sich durch Kopieren der XSD-Textbausteininformationen aus einer mit dem Designer erstellten Datei in die manuell bearbeitete XML-Datei beheben.</span><span class="sxs-lookup"><span data-stu-id="bcbff-198">But if you start with a minimal XML file, *the designer will not recognize the file* because it's missing a lot of additional metadata; you can fix this by copying the boilerplate XSD information from a designer-generated file into your hand-edited XML file.</span></span> 

**<span data-ttu-id="bcbff-199">Aktualisieren des Manifests, um auf die Ressourcen zu verweisen</span><span class="sxs-lookup"><span data-stu-id="bcbff-199">Update the manifest to reference the resources</span></span>**

<span data-ttu-id="bcbff-200">Wenn Sie die Werte in der `.resw` -Datei definiert haben, besteht der nächste Schritt darin, das Manifest zu aktualisieren, um auf die Ressourcenzeichenfolgen zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-200">Once you have the values defined in the `.resw` file, the next step is to update the manifest to reference the resource strings.</span></span> <span data-ttu-id="bcbff-201">Auch in diesem Fall können Sie eine XML-Datei direkt bearbeiten oder dies durch den Manifest-Designer von Visual Studio vornehmen lassen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-201">Again, you can edit an XML file directly, or rely on the Visual Studio Manifest Designer.</span></span>

<span data-ttu-id="bcbff-202">Wenn Sie XML-Code direkt bearbeiten, öffnen Sie die Datei `AppxManifest.xml`, und nehmen Sie die folgenden Änderungen an den <span style="background-color: lightgreen">hervorgehoben Werten</span> vor – verwenden Sie *genau* diesen Text und keinen für Ihre Anwendung spezifischen<a name="footnote6_ref" href="#footnote6"><sup>6</sup></a>.</span><span class="sxs-lookup"><span data-stu-id="bcbff-202">If you are editing XML directly, open the `AppxManifest.xml` file and make the following changes to the <span style="background-color: lightgreen">highlighted values</span> - use this *exact* text, not text specific to your application<a name="footnote6_ref" href="#footnote6"><sup>6</sup></a>.</span></span> <span data-ttu-id="bcbff-203">Diese Namen sollten den `Names` entsprechen, die Sie in der `.resw`-Datei erstellt haben, und als Präfix das `ms-resource:`-Schema und den `Resources/`-Namespace aufweisen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-203">These names should match the `Names` you created in the `.resw` file, prefixed with the `ms-resource:` scheme and the `Resources/` namespace.</span></span> 

*<span data-ttu-id="bcbff-204">Hinweis: Viele Elemente des Manifests wurden in diesem Codeausschnitt ausgelassen – löschen Sie nichts!</span><span class="sxs-lookup"><span data-stu-id="bcbff-204">Note: many elements of the manifest have been omitted from this snippet - do not delete anything!</span></span>*

<blockquote>
<pre>
&lt;?xml version="1.0" encoding="utf-8"?&gt;
&lt;Package&gt;
  &lt;Properties&gt;
    &lt;DisplayName&gt;<span style="background-color: lightgreen">ms-resource:Resources/PackageDisplayName</span>&lt;/DisplayName&gt;
    &lt;PublisherDisplayName&gt;<span style="background-color: lightgreen">ms-resource:Resources/PublisherDisplayName</span>&lt;/PublisherDisplayName&gt;
  &lt;/Properties&gt;
  &lt;Applications&gt;
    &lt;Application&gt;
      &lt;uap:VisualElements DisplayName="<span style="background-color: lightgreen">ms-resource:Resources/ApplicationDisplayName</span>"
        Description="<span style="background-color: lightgreen">ms-resource:Resources/ApplicationDescription</span>"&gt;
        &lt;uap:DefaultTile ShortName="<span style="background-color: lightgreen">ms-resource:Resources/TileShortName</span>"&gt;
          &lt;uap:ShowNameOnTiles&gt;
            &lt;uap:ShowOn Tile="square150x150Logo" /&gt;
          &lt;/uap:ShowNameOnTiles&gt;
        &lt;/uap:DefaultTile&gt;
      &lt;/uap:VisualElements&gt;
    &lt;/Application&gt;
  &lt;/Applications&gt;
&lt;/Package&gt;
</pre>
</blockquote>

<span data-ttu-id="bcbff-205">Wenn Sie den Manifest-Designer von Visual Studio verwenden, öffnen Sie die Datei `Package.appxmanifest`, und ändern Sie die <span style="background-color: lightgreen">hervorgehoben Werte</span> auf der Registerkarte `Application` und der Registerkarte `Packaging`:</span><span class="sxs-lookup"><span data-stu-id="bcbff-205">If you are using the Visual Studio manifest designer, open the `Package.appxmanifest` file and change the <span style="background-color: lightgreen">highlighted values</span> values in the `Application` tab and the `Packaging` tab:</span></span>

<img src="images\editing-application-info.png"/>
<img src="images\editing-packaging-info.png"/>

### <a name="step-12-build-pri-file-make-an-appx-package-and-verify-its-working"></a><span data-ttu-id="bcbff-206">Schritt1.2: Erstellen einer PRI-Datei, Erstellen eines AppX-Pakets und Sicherstellen, dass es funktioniert</span><span class="sxs-lookup"><span data-stu-id="bcbff-206">Step 1.2: Build PRI file, make an AppX package, and verify it's working</span></span>

<span data-ttu-id="bcbff-207">Sie sollten jetzt in der Lage sein, die `.pri`-Datei zu erstellen und die Anwendung bereitzustellen, um sicherzustellen, dass die richtigen Informationen (in Ihrer Standardsprache) im Startmenü angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bcbff-207">You should now be able to build the `.pri` file and deploy the application to verify that the correct information (in your default language) is appearing in the Start Menu.</span></span> 

<span data-ttu-id="bcbff-208">Wenn Sie in Visual Studio erstellen, drücken Sie einfach `Ctrl+Shift+B`, um das Projekt zu erstellen, und klicken Sie dann mit der rechten Maustaste auf das Projekt, und wählen Sie im Kontextmenü `Deploy` aus.</span><span class="sxs-lookup"><span data-stu-id="bcbff-208">If you're building in Visual Studio, simply press `Ctrl+Shift+B` to build the project and then right-click on the project and choose `Deploy` from the context menu.</span></span> 

<span data-ttu-id="bcbff-209">Führen Sie bei einer manuellen Erstellung die folgenden Schritte aus, um eine Konfigurationsdatei für `MakePRI`-Tool zu erstellen und die `.pri`-Datei selbst zu generieren (weitere Informationen finden Sie im [Thema **Manuelles Verpacken von Apps** auf MSDN](https://docs.microsoft.com/en-us/windows/uwp/packaging/manual-packaging-root)):</span><span class="sxs-lookup"><span data-stu-id="bcbff-209">If you're building manually, follow these steps to create a configuration file for `MakePRI` tool and to generate the `.pri` file itself (more information can be found in [the **Manual app packaging** topic on MSDN](https://docs.microsoft.com/en-us/windows/uwp/packaging/manual-packaging-root)):</span></span>

0. <span data-ttu-id="bcbff-210">Öffnen Sie eine Developer-Eingabeaufforderung über den Ordner `Visual Studio 2015` im Startmenü.</span><span class="sxs-lookup"><span data-stu-id="bcbff-210">Open a developer command prompt from the `Visual Studio 2015` folder in the Start menu</span></span>
0. <span data-ttu-id="bcbff-211">Wechseln Sie zum Stammverzeichnis des Projekts (d.h. zu demjenigen, dass die Datei `AppxManifest.xml` und den Ordner `Strings` enthält).</span><span class="sxs-lookup"><span data-stu-id="bcbff-211">Switch to the project root directory (the one that contains the `AppxManifest.xml` file and the `Strings` folder)</span></span>
0. <span data-ttu-id="bcbff-212">Geben Sie den folgenden Befehl ein, und ersetzen Sie dabei „contoso_demo.xml” mit einem für Ihr Projekt geeigneten Namen und „en-US” mit der Standardsprache Ihrer App (oder lassen Sie es nach Bedarf auf en-US).</span><span class="sxs-lookup"><span data-stu-id="bcbff-212">Type the following command, replacing "contoso_demo.xml" with a name suitable for your project, and "en-US" with the default language of your app (or keep it en-US if applicable).</span></span> <span data-ttu-id="bcbff-213">Beachten Sie, dass die XML-Datei im übergeordneten Verzeichnis erstellt wird (**nicht** im Projektverzeichnis), da sie kein Teil der Anwendung ist<a name="footnote7_ref" href="#footnote7"><sup>7</sup></a>:</span><span class="sxs-lookup"><span data-stu-id="bcbff-213">Note the xml file is created in the parent directory (**not** in the project directory) since it's not part of the application<a name="footnote7_ref" href="#footnote7"><sup>7</sup></a>:</span></span>

```CMD
    makepri createconfig /cf ..\contoso_demo.xml /dq en-US /pv 10.0 /o
```

0. <span data-ttu-id="bcbff-214">Sie können `makepri createconfig /?` eingeben, um zu sehen, was die einzelnen Parameter bedeuten. Kurz zusammengefasst:</span><span class="sxs-lookup"><span data-stu-id="bcbff-214">You can type `makepri createconfig /?` to see what each parameter does, but in summary:</span></span>
 * `/cf` <span data-ttu-id="bcbff-215">legt den Konfigurationsdateinamen fest (die Ausgabe dieses Befehls)</span><span class="sxs-lookup"><span data-stu-id="bcbff-215">sets the Configuration Filename (the output of this command)</span></span>
 * `/dq` <span data-ttu-id="bcbff-216">legt die Standardqualifizierer fest, in diesem Fall die Sprache</span><span class="sxs-lookup"><span data-stu-id="bcbff-216">sets the Default Qualifiers, in this case the language</span></span> `en-US`
 * `/pv` <span data-ttu-id="bcbff-217">legt die Plattformversion fest, in diesem Fall Windows10</span><span class="sxs-lookup"><span data-stu-id="bcbff-217">sets the Platform Version, in this case Windows 10</span></span>
 * `/o` <span data-ttu-id="bcbff-218">legt ein Überschreiben der Ausgabedatei fest, wenn vorhanden</span><span class="sxs-lookup"><span data-stu-id="bcbff-218">sets it to Overwrite the output file if it exists</span></span>
0. <span data-ttu-id="bcbff-219">Sie verfügen jetzt über eine Konfigurationsdatei. Führen Sie `MakePRI` erneut aus, um auf der Festplatte tatsächlich nach Ressourcen zu suchen und diese in einer PRI-Datei zu verpacken.</span><span class="sxs-lookup"><span data-stu-id="bcbff-219">Now you have a configuration file, run `MakePRI` again to actually search the disk for resources and package them into a PRI file.</span></span> <span data-ttu-id="bcbff-220">Ersetzen Sie „contoso_demop.xml” mit dem XML-Dateinamen, den Sie im vorherigen Schritt verwendet haben, und legen Sie das übergeordnete Verzeichnis für Eingabe und Ausgabe fest:</span><span class="sxs-lookup"><span data-stu-id="bcbff-220">Replace "contoso_demop.xml" with the XML filename you used in the previous step, and be sure to specify the parent directory for both input and output:</span></span> 

    `makepri new /pr . /cf ..\contoso_demo.xml /of ..\resources.pri /mf AppX /o`
0. <span data-ttu-id="bcbff-221">Sie können `makepri new /?` eingeben, um zu sehen, was die einzelnen Parameter bedeuten. Kurz zusammengefasst:</span><span class="sxs-lookup"><span data-stu-id="bcbff-221">You can type `makepri new /?` to see what each parameter does, but in a nutshell:</span></span>
 * `/pr` <span data-ttu-id="bcbff-222">legt den Projektstamm fest (in diesem Fall das aktuelle Verzeichnis)</span><span class="sxs-lookup"><span data-stu-id="bcbff-222">sets the Project Root (in this case, the current directory)</span></span>
 * `/cf` <span data-ttu-id="bcbff-223">legt den Konfigurationsdateinamen fest, der im vorherigen Schritt erstellt wurde</span><span class="sxs-lookup"><span data-stu-id="bcbff-223">sets the Configuration Filename, created in the previous step</span></span>
 * `/of` <span data-ttu-id="bcbff-224">legt die Ausgabedatei fest</span><span class="sxs-lookup"><span data-stu-id="bcbff-224">sets the Output File</span></span> 
 * `/mf` <span data-ttu-id="bcbff-225">erstellt eine Zuordnungsdatei (sodass wir Dateien im Paket in einem späteren Schritt ausschließen können)</span><span class="sxs-lookup"><span data-stu-id="bcbff-225">creates a Mapping File (so we can exclude files in the package in a later step)</span></span>
 * `/o` <span data-ttu-id="bcbff-226">legt ein Überschreiben der Ausgabedatei fest, wenn vorhanden</span><span class="sxs-lookup"><span data-stu-id="bcbff-226">sets it to Overwrite the output file if it exists</span></span>
0. <span data-ttu-id="bcbff-227">Sie verfügen jetzt über eine `.pri`-Datei mit den Standardsprachressourcen (z.B. en-US).</span><span class="sxs-lookup"><span data-stu-id="bcbff-227">Now you have a `.pri` file with the default language resources (eg, en-US).</span></span> <span data-ttu-id="bcbff-228">Um sicherzustellen, dass es ordnungsgemäß funktioniert hat, können Sie den folgenden Befehl ausführen:</span><span class="sxs-lookup"><span data-stu-id="bcbff-228">To verify that it worked correctly, you can run the following command:</span></span>

    `makepri dump /if ..\resources.pri /of ..\resources /o`
0. <span data-ttu-id="bcbff-229">Sie können `makepri dump /?` eingeben, um zu sehen, was die einzelnen Parameter bedeuten. Kurz zusammengefasst:</span><span class="sxs-lookup"><span data-stu-id="bcbff-229">You can type `makepri dump /?` to see what each parameter does, but in a nutshell:</span></span>
 * `/if` <span data-ttu-id="bcbff-230">legt den Eingabedateinamen fest</span><span class="sxs-lookup"><span data-stu-id="bcbff-230">sets the Input Filename</span></span> 
 * `/of` <span data-ttu-id="bcbff-231">legt den Ausgabedateinamen fest (`.xml` wird automatisch angefügt)</span><span class="sxs-lookup"><span data-stu-id="bcbff-231">sets the Output Filename (`.xml` will be appended automatically)</span></span>
 * `/o` <span data-ttu-id="bcbff-232">legt ein Überschreiben der Ausgabedatei fest, wenn vorhanden</span><span class="sxs-lookup"><span data-stu-id="bcbff-232">sets it to Overwrite the output file if it exists</span></span>
0. <span data-ttu-id="bcbff-233">Zuletzt können Sie `..\resources.xml` in einem Text-Editor öffnen und überprüfen, ob Ihre `<NamedResource>`-Werte (z.B. `ApplicationDescription` und `PublisherDisplayName`) zusammen mit den `<Candidate>`-Werten für die ausgewählte Standardsprache aufgeführt werden (am Anfang der Datei befinden sich auch weitere Inhalte; diese können Sie vorerst ignorieren).</span><span class="sxs-lookup"><span data-stu-id="bcbff-233">Finally, you can open `..\resources.xml` in a text editor and verify it lists your `<NamedResource>` values (like `ApplicationDescription` and `PublisherDisplayName`) along with `<Candidate>` values for your chosen default language (there will be other content in the beginning of the file; ignore that for now).</span></span>

<span data-ttu-id="bcbff-234">Wenn Sie möchten, können Sie die Zuordnungsdatei `..\resources.map.txt` öffnen, um zu überprüfen, ob sie die für Ihr Projekt benötigten Dateien enthält (einschließlich der PRI-Datei, die nicht Teil des Projektverzeichnisses ist).</span><span class="sxs-lookup"><span data-stu-id="bcbff-234">If you like, you can open the mapping file `..\resources.map.txt` to verify it contains the files needed for your project (including the PRI file, which is not part of the project's directory).</span></span> <span data-ttu-id="bcbff-235">Besonders wichtig ist, dass die Zuordnungsdatei *keinen* Verweis auf Ihre `resources.resw`-Datei enthält, da der Inhalt dieser Datei bereits in die PRI-Datei eingebettet wurde.</span><span class="sxs-lookup"><span data-stu-id="bcbff-235">Importantly, the mapping file will *not* include a reference to your `resources.resw` file because the contents of that file have already been embedded in the PRI file.</span></span> <span data-ttu-id="bcbff-236">Sie enthält jedoch andere Ressourcen wie die Dateinamen Ihrer Bilder.</span><span class="sxs-lookup"><span data-stu-id="bcbff-236">It will, however, contain other resources like the filenames of your images.</span></span>

**<span data-ttu-id="bcbff-237">Erstellen und Signieren des Pakets</span><span class="sxs-lookup"><span data-stu-id="bcbff-237">Building and signing the package</span></span>**

<span data-ttu-id="bcbff-238">Nachdem die PRI-Datei jetzt erstellt wurde, können Sie das Paket erstellen und signieren:</span><span class="sxs-lookup"><span data-stu-id="bcbff-238">Now the PRI file is built, you can build and sign the package:</span></span>

0. <span data-ttu-id="bcbff-239">Um das App-Paket zu erstellen, führen Sie den folgenden Befehl aus, und ersetzen Sie dabei `contoso_demo.appx` mit dem Namen der AppX Datei, die Sie erstellen möchten. Wählen Sie ein anderes Verzeichnis für die `.AppX`-Datei (in diesem Beispiel wird das übergeordnete Verzeichnis verwendet; sie können jedes beliebige Verzeichnis verwenden, jedoch **nicht** das Projektverzeichnis):</span><span class="sxs-lookup"><span data-stu-id="bcbff-239">To create the app package, run the following command replacing `contoso_demo.appx` with the name of the AppX file you want to create and making sure to choose a different directory for the `.AppX` file (this sample uses the parent directory; it can be anywhere but should **not** be the project directory):</span></span>

    `makeappx pack /m AppXManifest.xml /f ..\resources.map.txt /p ..\contoso_demo.appx /o`
0. <span data-ttu-id="bcbff-240">Sie können `makeappx pack /?` eingeben, um zu sehen, was die einzelnen Parameter bedeuten. Kurz zusammengefasst:</span><span class="sxs-lookup"><span data-stu-id="bcbff-240">You can type `makeappx pack /?` to see what each parameter does, but in a nutshell:</span></span>
 * `/m` <span data-ttu-id="bcbff-241">legt die zu verwendende Manifestdatei fest</span><span class="sxs-lookup"><span data-stu-id="bcbff-241">sets the Manifest file to use</span></span>
 * `/f` <span data-ttu-id="bcbff-242">legt die zu verwendende Zuordnungsdatei fest (die im vorherigen Schritt erstellt wurde)</span><span class="sxs-lookup"><span data-stu-id="bcbff-242">sets the mapping File to use (created in the previous step)</span></span> 
 * `/p` <span data-ttu-id="bcbff-243">legt den Namen des Ausgabepakets fest</span><span class="sxs-lookup"><span data-stu-id="bcbff-243">sets the output Package name</span></span>
 * `/o` <span data-ttu-id="bcbff-244">legt ein Überschreiben der Ausgabedatei fest, wenn vorhanden</span><span class="sxs-lookup"><span data-stu-id="bcbff-244">sets it to Overwrite the output file if it exists</span></span>
0. <span data-ttu-id="bcbff-245">Wenn das Paket erstellt wurde, muss es signiert werden.</span><span class="sxs-lookup"><span data-stu-id="bcbff-245">Once the package is created, it must be signed.</span></span> <span data-ttu-id="bcbff-246">Die einfachste Methode zum Abrufen eines Signaturzertifikats besteht darin, in Visual Studio ein leeres universelles Windows-Projekt zu erstellen und die dadurch erstellte `.pfx`-Datei zu kopieren. Es besteht jedoch auch die Möglichkeit des manuellen Erstellens. Verwenden Sie dazu die Hilfsprogramme `MakeCert` und `Pvk2Pfx`, wie im [Thema **How to create an app package signing certificate (So erstellen Sie ein App-Paketsignaturzertifikat)** auf MSDN] (https://msdn.microsoft.com/en-us/library/Windows/Desktop/jj835832(v=vs.85).aspx) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="bcbff-246">The easiest way to get a signing certificate is by creating an empty Universal Windows project in Visual Studio and copying the `.pfx` file it creates, but you can create one manually using the `MakeCert` and `Pvk2Pfx` utilities as described in [the **How to create an app package signing certificate** topic on MSDN] (https://msdn.microsoft.com/en-us/library/windows/desktop/jj835832(v=vs.85).aspx).</span></span> 
 * <span data-ttu-id="bcbff-247">**Wichtig:** Wenn Sie ein Signaturzertifikat manuell erstellen, stellen Sie sicher, dass Sie die Dateien in einem anderen Verzeichnis als Ihr Quellprojekt oder die Paketquelle ablegen, andernfalls wird es möglicherweise in das Paket eingefügt, einschließlich des privaten Schlüssels!</span><span class="sxs-lookup"><span data-stu-id="bcbff-247">**Important:** If you manually create a signing certificate, make sure you place the files in a different directory than your source project or your package source, otherwise it might get included as part of the package, including the private key!</span></span>
0. <span data-ttu-id="bcbff-248">Verwenden Sie zum Signieren des Pakets den folgenden Befehl.</span><span class="sxs-lookup"><span data-stu-id="bcbff-248">To sign the package, use the following command.</span></span> <span data-ttu-id="bcbff-249">Beachten Sie, dass der im Element `Identity` der Datei `AppxManifest.xml` angegebene `Publisher` mit dem `Subject` des Zertifikats übereinstimmen muss (hierbei handelt es sich **nicht** um das Element `<PublisherDisplayName>`; dieses ist der lokalisierte Anzeigename, der den Benutzern angezeigt wird).</span><span class="sxs-lookup"><span data-stu-id="bcbff-249">Note that the `Publisher` specified in the `Identity` element of the `AppxManifest.xml` must match the `Subject` of the certificate (this is **not** the `<PublisherDisplayName>` element, which is the localized display name to show to users).</span></span> <span data-ttu-id="bcbff-250">Ersetzen Sie wie gewohnt die `contoso_demo...`-Dateinamen mit den Namen für Ihr Projekt, und (**sehr wichtig**) stellen Sie sicher, dass die `.pfx`-Datei sich nicht im aktuellen Verzeichnis befindet (andernfalls wäre sie als Teil Ihres Pakets erstellt worden, einschließlich des privaten Signaturschlüssels!):</span><span class="sxs-lookup"><span data-stu-id="bcbff-250">As usual, replace the `contoso_demo...` filenames with the names appropriate for your project, and (**very important**) make sure the `.pfx` file is not in the current directory (otherwise it would have been created as part of your package, including the private signing key!):</span></span>

    `signtool sign /fd SHA256 /a /f ..\contoso_demo_key.pfx ..\contoso_demo.appx`
0. <span data-ttu-id="bcbff-251">Sie können `signtool sign /?` eingeben, um zu sehen, was die einzelnen Parameter bedeuten. Kurz zusammengefasst:</span><span class="sxs-lookup"><span data-stu-id="bcbff-251">You can type `signtool sign /?` to see what each parameter does, but in a nutshell:</span></span>
 * `/fd` <span data-ttu-id="bcbff-252">legt den Datei-Digestalgorithmus fest (SHA256 ist die Standardeinstellung für AppX)</span><span class="sxs-lookup"><span data-stu-id="bcbff-252">sets the File Digest algorithm (SHA256 is the default for AppX)</span></span>
 * `/a` <span data-ttu-id="bcbff-253">wählt automatisch das beste Zertifikat</span><span class="sxs-lookup"><span data-stu-id="bcbff-253">will Automatically select the best certificate</span></span>
 * `/f` <span data-ttu-id="bcbff-254">legt die Eingabedatei fest, die das Signaturzertifikat enthält</span><span class="sxs-lookup"><span data-stu-id="bcbff-254">specifies the input File that contains the signing certificate</span></span>

<span data-ttu-id="bcbff-255">Zuletzt können Sie auf die Datei `.appx` doppelklicken, um diese zu installieren. Wenn Sie lieber die Befehlszeile verwenden, können Sie eine PowerShell-Eingabeaufforderung öffnen, zum Verzeichnis mit dem Paket wechseln, und Folgendes eingeben (wobei Sie `contoso_demo.appx` mit Ihrem Paketnamen ersetzen müssen):</span><span class="sxs-lookup"><span data-stu-id="bcbff-255">Finally, you can now double-click on the `.appx` file to install it, or if you prefer the command-line you can open a PowerShell prompt, change to the directory containing the package, and type the following (replacing `contoso_demo.appx` with your package name):</span></span>

```CMD
    add-appxpackage contoso_demo.appx
```

<span data-ttu-id="bcbff-256">Wenn Sie Fehlermeldungen erhalten, dass das Zertifikat nicht als vertrauenswürdig eingestuft wird, stellen Sie sicher, dass es zum lokalen Speicher hinzugefügt wurde (**nicht** zum Benutzerspeicher).</span><span class="sxs-lookup"><span data-stu-id="bcbff-256">If you receive errors about the certificate not being trusted, make sure it is added to the machine store (**not** the user store).</span></span> <span data-ttu-id="bcbff-257">Um das Zertifikat zum lokalen Speicher hinzufügen, können Sie entweder die Befehlszeile oder Windows Explorer verwenden.</span><span class="sxs-lookup"><span data-stu-id="bcbff-257">To add the certificate to the machine store, you can either use the command-line or Windows Explorer.</span></span>

<span data-ttu-id="bcbff-258">Verwenden der Befehlszeile:</span><span class="sxs-lookup"><span data-stu-id="bcbff-258">To use the command-line:</span></span>

0. <span data-ttu-id="bcbff-259">Führen Sie eine Visual Studio2015-Befehlszeile als Administrator aus.</span><span class="sxs-lookup"><span data-stu-id="bcbff-259">Run a Visual Studio 2015 command prompt as an Administrator.</span></span>
0. <span data-ttu-id="bcbff-260">Wechseln Sie zu dem Verzeichnis mit der `.cer`-Datei (stellen Sie sicher, dass dies nicht das Verzeichnis Ihrer Quelle oder Ihres Projekts ist!)</span><span class="sxs-lookup"><span data-stu-id="bcbff-260">Switch to the directory that contains the `.cer` file (remember to ensure this is outside of your source or project directories!)</span></span>
0. <span data-ttu-id="bcbff-261">Geben Sie folgenden Befehl ein, und ersetzen Sie dabei `contoso_demo.cer` mit Ihrem Dateinamen:</span><span class="sxs-lookup"><span data-stu-id="bcbff-261">Type the following command, replacing `contoso_demo.cer` with your filename:</span></span>

    `certutil -addstore TrustedPeople contoso_demo.cer`
0. <span data-ttu-id="bcbff-262">Sie können `certutil -addstore /?` ausführen, um zu sehen, was die einzelnen Parameter bedeuten. Kurz zusammengefasst:</span><span class="sxs-lookup"><span data-stu-id="bcbff-262">You can run `certutil -addstore /?` to see what each parameter does, but in a nutshell:</span></span>
 * `-addstore` <span data-ttu-id="bcbff-263">fügt ein Zertifikat zu einem Zertifikatspeicher hinzu</span><span class="sxs-lookup"><span data-stu-id="bcbff-263">adds a certificate to a certificate store</span></span>
 * `TrustedPeople` <span data-ttu-id="bcbff-264">gibt den Speicher an, in dem das Zertifikat gespeichert wird</span><span class="sxs-lookup"><span data-stu-id="bcbff-264">indicates the store into which the certificate is placed</span></span>

<span data-ttu-id="bcbff-265">Verwenden von Windows Explorer:</span><span class="sxs-lookup"><span data-stu-id="bcbff-265">To use Windows Explorer:</span></span>

0. <span data-ttu-id="bcbff-266">Navigieren Sie zum Ordner mit der `.pfx`-Datei</span><span class="sxs-lookup"><span data-stu-id="bcbff-266">Navigate to the folder that contains the `.pfx` file</span></span>
0. <span data-ttu-id="bcbff-267">Doppelklicken Sie auf die `.pfx`-Datei. Der **Zertifikatimport-Assistent** sollte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bcbff-267">Double-click on the `.pfx` file and the **Certicicate Import Wizard** should appear</span></span>
0. <span data-ttu-id="bcbff-268">Wählen Sie `Local Machine`, und klicken Sie auf</span><span class="sxs-lookup"><span data-stu-id="bcbff-268">Choose `Local Machine` and click</span></span> `Next`
0. <span data-ttu-id="bcbff-269">Akzeptieren Sie die Benutzerkontensteuerung- Eingabeaufforderung für erhöhte Rechte für Administratoren, wenn diese angezeigt wird, und klicken Sie auf</span><span class="sxs-lookup"><span data-stu-id="bcbff-269">Accept the User Account Control admin elevation prompt, if it appears, and click</span></span> `Next`
0. <span data-ttu-id="bcbff-270">Geben Sie das Kennwort für den privaten Schlüssel ein, sofern vorhanden, und klicken Sie auf</span><span class="sxs-lookup"><span data-stu-id="bcbff-270">Enter the password for the private key, if there is one, and click</span></span> `Next`
0. <span data-ttu-id="bcbff-271">Wählen Sie</span><span class="sxs-lookup"><span data-stu-id="bcbff-271">Select</span></span> `Place all certificates in the following store`
0. <span data-ttu-id="bcbff-272">Klicken Sie auf `Browse`, und wählen Sie den Ordner `Trusted People` (**nicht** „Vertrauenswürdige Herausgeber”)</span><span class="sxs-lookup"><span data-stu-id="bcbff-272">Click `Browse`, and choose the `Trusted People` folder (**not** "Trusted Publishers")</span></span>
0. <span data-ttu-id="bcbff-273">Klicken Sie auf `Next` und dann auf</span><span class="sxs-lookup"><span data-stu-id="bcbff-273">Click `Next` and then</span></span> `Finish`

<span data-ttu-id="bcbff-274">Versuchen Sie nach dem Hinzufügen des Zertifikats zum `Trusted People`-Speicher erneut, das Paket zu installieren.</span><span class="sxs-lookup"><span data-stu-id="bcbff-274">After adding the certificate to the `Trusted People` store, try installing the package again.</span></span>

<span data-ttu-id="bcbff-275">Ihre App sollte jetzt in der Liste „Alle Apps” im Startmenü angezeigt werden, mit den richtigen Informationen aus der Datei `.resw` / `.pri`.</span><span class="sxs-lookup"><span data-stu-id="bcbff-275">You should now see your app appear in the Start Menu's "All Apps" list, with the correct information from the `.resw` / `.pri` file.</span></span> <span data-ttu-id="bcbff-276">Wenn Sie eine leere Zeichenfolge oder die Zeichenfolge `ms-resource:...` sehen, ist ein Fehler aufgetreten – überprüfen Sie Ihre Bearbeitungen, und stellen Sie sicher, dass sie richtig sind.</span><span class="sxs-lookup"><span data-stu-id="bcbff-276">If you see a blank string or the string `ms-resource:...` then something has gone wrong - double check your edits and make sure they're correct.</span></span> <span data-ttu-id="bcbff-277">Wenn Sie im Startmenü Ihrer App mit der rechten Maustaste klicken, können Sie sie als Kachel anheften und überprüfen, ob dort die richtigen Informationen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bcbff-277">If you right-click on your app in the Start Menu, you can Pin it as a tile and verify the correct information is displayed there also.</span></span>

### <a name="step-13-add-more-supported-languages"></a><span data-ttu-id="bcbff-278">Schritt 1.3: Hinzufügen von mehr unterstützten Sprachen</span><span class="sxs-lookup"><span data-stu-id="bcbff-278">Step 1.3: Add more supported languages</span></span>

<span data-ttu-id="bcbff-279">Nachdem die Änderungen am AppX-Manifest vorgenommen und die ursprüngliche `resources.resw`-Datei erstellt wurde, ist es ganz einfache, zusätzliche Sprachen hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-279">Once the changes have been made to the AppX manifest and the initial `resources.resw` file has been created, adding additional languages is easy.</span></span>

**<span data-ttu-id="bcbff-280">Erstellen zusätzlicher lokalisierter Ressourcen</span><span class="sxs-lookup"><span data-stu-id="bcbff-280">Create additional localized resources</span></span>**

<span data-ttu-id="bcbff-281">Erstellen Sie zunächst die Werte für die zusätzlich lokalisierten Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-281">First, create the additional localized resource values.</span></span> 

<span data-ttu-id="bcbff-282">Erstellen Sie im Ordner `Strings` zusätzliche Ordner für jede Sprache, die Sie unterstützen. Verwenden Sie dafür den entsprechenden BCP-47-Code (z.B. `Strings\de-DE`).</span><span class="sxs-lookup"><span data-stu-id="bcbff-282">Within the `Strings` folder, create additional folders for each language you support using the appropriate BCP-47 code (for example, `Strings\de-DE`).</span></span> <span data-ttu-id="bcbff-283">Erstellen Sie in jedem dieser Ordner eine `resources.resw`-Datei (mithilfe von XML-Editor oder dem Visual Studio-Designer), die die Werte der übersetzten Ressourcen enthält.</span><span class="sxs-lookup"><span data-stu-id="bcbff-283">Within each of these folders, create a `resources.resw` file (using either an XML editor or the Visual Studio designer) that includes the translated resource values.</span></span> <span data-ttu-id="bcbff-284">Es wird vorausgesetzt, dass die lokalisierten Zeichenfolgen bereits verfügbar sind. Sie müssen diese nur in die Datei `.resw` kopieren; der Übersetzungsschritt selbst wird in diesem Dokument nicht behandelt.</span><span class="sxs-lookup"><span data-stu-id="bcbff-284">It is assumed you already have the localized strings available somewhere, and you just need to copy them into the `.resw` file; this document does not cover the translation step itself.</span></span> 

<span data-ttu-id="bcbff-285">Die Datei `Strings\de-DE\resources.resw` könnte beispielsweise wie folgt aussehen, der <span style="background-color: yellow">hervorgehobene Text</span> wurde von `en-US` geändert:</span><span class="sxs-lookup"><span data-stu-id="bcbff-285">For example, the `Strings\de-DE\resources.resw` file might look like this, with the <span style="background-color: yellow">highlighted text</span> changed from `en-US`:</span></span>

<blockquote>
<pre>
&lt;?xml version="1.0" encoding="utf-8"?&gt;
&lt;root&gt;
  &lt;data name="ApplicationDescription"&gt;
    &lt;value&gt;<span style="background-color: yellow">Contoso Demo app with localized resources (German)</span>&lt;/value&gt;
  &lt;/data&gt;
  &lt;data name="ApplicationDisplayName"&gt;
    &lt;value&gt;<span style="background-color: yellow">Contoso Demo Sample (German)</span>&lt;/value&gt;
  &lt;/data&gt;
  &lt;data name="PackageDisplayName"&gt;
    &lt;value&gt;<span style="background-color: yellow">Contoso Demo Package (German)</span>&lt;/value&gt;
  &lt;/data&gt;
  &lt;data name="PublisherDisplayName"&gt;
    &lt;value&gt;<span style="background-color: yellow">Contoso Samples, DE</span>&lt;/value&gt;
  &lt;/data&gt;
  &lt;data name="TileShortName"&gt;
    &lt;value&gt;<span style="background-color: yellow">Contoso (DE)</span>&lt;/value&gt;
  &lt;/data&gt;
&lt;/root&gt;
</pre>
</blockquote>

<span data-ttu-id="bcbff-286">Für die folgenden Schritte gilt die Annahme, dass Sie sowohl für `de-DE` als auch für `fr-FR` Ressourcen hinzugefügt haben, dasselbe Muster kann jedoch für alle Sprachen befolgt werden.</span><span class="sxs-lookup"><span data-stu-id="bcbff-286">The following steps assume you added resources for both `de-DE` and `fr-FR`, but the same pattern can be followed for any language.</span></span>

**<span data-ttu-id="bcbff-287">Aktualisieren von AppX-Manifest, um die unterstützten Sprachen aufzuführen</span><span class="sxs-lookup"><span data-stu-id="bcbff-287">Update AppX manifest to list supported languages</span></span>**

<span data-ttu-id="bcbff-288">AppX-Manifest muss aktualisiert werden, um die von der App unterstützten Sprachen aufzuführen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-288">The AppX manifest must be updated to list the languages supported by the app.</span></span> <span data-ttu-id="bcbff-289">Der Desktop App Converter fügt die Standardsprache hinzu, die anderen müssen jedoch explizit hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="bcbff-289">The Desktop App Converter adds the default language, but the others must be added explicitly.</span></span> <span data-ttu-id="bcbff-290">Aktualisieren Sie beim direkten Bearbeiten der Datei `AppxManifest.xml` den `Resources`-Knoten wie folgt, fügen Sie dabei so viele Elemente hinzu, wie Sie benötigen, und ersetzen die <span style="background-color: yellow">entsprechenden Sprachen, die Sie unterstützen</span>. Stellen Sie dabei außerdem sicher, dass der erste Eintrag in der Liste die Standard- (Fallback-)Sprache ist.</span><span class="sxs-lookup"><span data-stu-id="bcbff-290">If you're editing the `AppxManifest.xml` file directly, update the `Resources` node as follows, adding as many elements as you need, and substituting the <span style="background-color: yellow">appropriate languages you support</span> and making sure the first entry in the list is the default (fallback) language.</span></span> <span data-ttu-id="bcbff-291">In diesem Beispiel ist der Standard Englisch (USA) mit zusätzlicher Unterstützung für Deutsch (Deutschland) und Französisch (Frankreich):</span><span class="sxs-lookup"><span data-stu-id="bcbff-291">In this example, the default is English (US) with additional support for both German (Germany) and French (France):</span></span>

<blockquote>
<pre>
&lt;Resources&gt;
  &lt;Resource Language="<span style="background-color: yellow">EN-US</span>" /&gt;
  &lt;Resource Language="<span style="background-color: yellow">DE-DE</span>" /&gt;
  &lt;Resource Language="<span style="background-color: yellow">FR-FR</span>" /&gt;
&lt;/Resources&gt;
</pre>
</blockquote>

<span data-ttu-id="bcbff-292">Wenn Sie Visual Studio verwenden, sollte Sie nichts weiter tun müssen; wenn Sie `Package.appxmanifest` betrachten, sollten Sie den speziellen Wert <span style="background-color: yellow">x generate</span> sehen. Dieser bewirkt, dass der Buildprozess die Sprachen einfügt, die sich in Ihrem Projekt befinden (basierend auf den Ordnern, die mit den BCP-47 Codes benannt sind).</span><span class="sxs-lookup"><span data-stu-id="bcbff-292">If you are using Visual Studio, you shouldn't need to do anything; if you look at `Package.appxmanifest` you should see the special <span style="background-color: yellow">x-generate</span> value, which causes the build process to insert the languages it finds in your project (based on the folders named with BCP-47 codes).</span></span> <span data-ttu-id="bcbff-293">Beachten Sie, dass dies kein gültiger Wert für echte Appx-Manifeste ist. Es funktioniert nur für Visual Studio-Projekte:</span><span class="sxs-lookup"><span data-stu-id="bcbff-293">Note that this is not a valid value for a real Appx Manifest; it only works for Visual Studio projects:</span></span>

<blockquote>
<pre>
&lt;Resources&gt;
  &lt;Resource Language="<span style="background-color: yellow">x-generate</span>" /&gt;
&lt;/Resources&gt;
</pre>
</blockquote>

**<span data-ttu-id="bcbff-294">Neuerstellen mit den lokalisierten Werten</span><span class="sxs-lookup"><span data-stu-id="bcbff-294">Re-build with the localized values</span></span>**

<span data-ttu-id="bcbff-295">Sie können Ihre Anwendung jetzt erneut erstellen und bereitstellen, und wenn Sie Ihre bevorzugte Sprache in Windows ändern, sollten die neu lokalisierten Werte im Startmenü angezeigt werden (Informationen zum Ändern Ihrer Sprache finden Sie unten).</span><span class="sxs-lookup"><span data-stu-id="bcbff-295">Now you can build and deploy your application, again, and if you change your language preference in Windows you should see the newly-localized values appear in the Start menu (instructions for how to change your language are below).</span></span>

<span data-ttu-id="bcbff-296">Bei Visual Studio können Sie wieder einfach `Ctrl+Shift+B` zum Erstellen verwenden, und mit der rechten Maustaste auf das Projekt klicken, um es bereitzustellen (`Deploy`).</span><span class="sxs-lookup"><span data-stu-id="bcbff-296">For Visual Studio, again you can just use `Ctrl+Shift+B` to build, and right-click the project to `Deploy`.</span></span>

<span data-ttu-id="bcbff-297">Wenn Sie das Projekt manuell erstellen, führen Sie die gleichen Schritte wie oben beschrieben aus, fügen Sie jedoch die zusätzlichen Sprachen getrennt durch Unterstriche zur Liste der Standardqualifizierer (`/dq`) hinzu, wenn Sie die Konfigurationsdatei erstellen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-297">If you're manually building the project, follow the same steps as above but add the additional languages, separated by underscores, to the default qualifiers list (`/dq`) when creating the configuration file.</span></span> <span data-ttu-id="bcbff-298">Beispiel: Unterstützung der Ressourcen für Englisch, Deutsch und Französisch, die im vorherigen Schritt hinzugefügt wurden:</span><span class="sxs-lookup"><span data-stu-id="bcbff-298">For example, to support the English, German, and French resources added in the previous step:</span></span>

```CMD
    makepri createconfig /cf ..\contoso_demo.xml /dq en-US_de-DE_fr-FR /pv 10.0 /o
```

<span data-ttu-id="bcbff-299">Dadurch wird eine PRI-Datei erstellt, die alle angegebenen Sprachen enthält, die Sie einfach zum Testen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="bcbff-299">This will create a PRI file that contains all the specified languagesthat you can easily use for testing.</span></span> <span data-ttu-id="bcbff-300">Wenn die Gesamtgröße der Ressourcen gering ist, oder Sie nur eine geringe Anzahl von Sprachen unterstützen, kann dies für den Versand Ihrer App ausreichend sein. Wenn Sie jedoch von einer möglichst geringen Installations- oder Downloadgröße Ihrer Ressource profitieren möchten, müssen Sie separate Sprachpakete erstellen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-300">If the total size of your resources is small, or you only support a small number of languages, this might be acceptable for your shipping app; it's only if you want the benefits of minimizing install / download size for your resources that you need to do the additional work of building separate language packs.</span></span>

**<span data-ttu-id="bcbff-301">Test mit den lokalisierten Werten</span><span class="sxs-lookup"><span data-stu-id="bcbff-301">Test with the localized values</span></span>**

<span data-ttu-id="bcbff-302">Zum Testen der neuen lokalisierten Änderungen müssen Sie einfach eine neue bevorzugte UI-Sprache zu Windows hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-302">To test the new localized changes, you simply add a new preferred UI language to Windows.</span></span> <span data-ttu-id="bcbff-303">Es ist nicht erforderlich, Language Packs herunterzuladen, das System neu zu starten, oder die gesamte Windows-UI in einer fremden Sprache anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-303">There is no need to download language packs, reboot the system, or have your entire Windows UI appear in a foreign language.</span></span> 

0. <span data-ttu-id="bcbff-304">Führen Sie die `Settings`-App aus (`Windows + I`).</span><span class="sxs-lookup"><span data-stu-id="bcbff-304">Run the `Settings` app (`Windows + I`)</span></span>
0. <span data-ttu-id="bcbff-305">Wechseln Sie zu</span><span class="sxs-lookup"><span data-stu-id="bcbff-305">Go to</span></span> `Time & language`
0. <span data-ttu-id="bcbff-306">Wechseln Sie zu</span><span class="sxs-lookup"><span data-stu-id="bcbff-306">Go to</span></span> `Region & language`
0. <span data-ttu-id="bcbff-307">Klick</span><span class="sxs-lookup"><span data-stu-id="bcbff-307">Click</span></span> `Add a language`
0. <span data-ttu-id="bcbff-308">Geben (oder wählen) Sie die gewünschte Sprache ein (z.B. `Deutsch` oder `German`)</span><span class="sxs-lookup"><span data-stu-id="bcbff-308">Type (or select) the language you want (eg `Deutsch` or `German`)</span></span>
 * <span data-ttu-id="bcbff-309">Wenn untergeordnete Sprachen vorhanden sind, wählen Sie die gewünschte Sprache aus (z.B. `Deutsch / Deutschland`)</span><span class="sxs-lookup"><span data-stu-id="bcbff-309">If there are sub-languages, choose the one you want (eg, `Deutsch / Deutschland`)</span></span>
0. <span data-ttu-id="bcbff-310">Wählen Sie die neue Sprache in der Liste der Sprachen aus.</span><span class="sxs-lookup"><span data-stu-id="bcbff-310">Select the new language in the language list</span></span>
0. <span data-ttu-id="bcbff-311">Klick</span><span class="sxs-lookup"><span data-stu-id="bcbff-311">Click</span></span> `Set as default`

<span data-ttu-id="bcbff-312">Öffnen Sie nun das Startmenü und suchen Sie Ihre Anwendung, und die lokalisierten Werte für die ausgewählte Sprache (andere Apps können auch lokalisiert angezeigt werden) sollten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bcbff-312">Now open the Start menu and search for your application, and you should see the localized values for the selected language (other apps might also appear localized).</span></span> <span data-ttu-id="bcbff-313">Wenn Sie den lokalisierten Namen nicht sofort sehen, warten Sie einige Minuten, bis der Cache des Startmenüs aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="bcbff-313">If you don't see the localized name right away, wait a few minutes until the Start Menu's cache is refreshed.</span></span> <span data-ttu-id="bcbff-314">Um auf Ihre Muttersprache zurückzuwechseln, stellen Sie sie als Standardsprache in der Liste der Sprachen ein.</span><span class="sxs-lookup"><span data-stu-id="bcbff-314">To return to your native language, just make it the default language in the language list.</span></span> 

### <a name="step-14-localizing-more-parts-of-the-appx-manifest-optional"></a><span data-ttu-id="bcbff-315">Schritt1.4: Lokalisieren weiterer Teile des AppX-Manifests (optional)</span><span class="sxs-lookup"><span data-stu-id="bcbff-315">Step 1.4: Localizing more parts of the AppX manifest (optional)</span></span>

<span data-ttu-id="bcbff-316">Andere Abschnitte des AppX-Manifests können lokalisiert werden.</span><span class="sxs-lookup"><span data-stu-id="bcbff-316">Other sections of the AppX Manifest can be localized.</span></span> <span data-ttu-id="bcbff-317">Wenn Ihre Anwendung beispielsweise Dateierweiterungen bearbeitet, dann sollte sie eine `windows.fileTypeAssociation`-Erweiterung im Manifest aufweisen, die den <span style="background-color: lightgreen">grün hervorgehobenen Text gemäß der Abbildung verwendet</span> (da es auf Ressourcen verweisen wird), und den <span style="background-color: yellow">gelb hervorgehobenen Text</span> mit Informationen ersetzt, die für Ihre Anwendung spezifisch sind:</span><span class="sxs-lookup"><span data-stu-id="bcbff-317">For example, if your application handles file-extensions then it should have a `windows.fileTypeAssociation` extension in the manifest, using the <span style="background-color: lightgreen">green highlighted text</span> exactly as shown (since it will refer to resources), and replacing the <span style="background-color: yellow">yellow highlighted text</span> with information specific to your application:</span></span>

<blockquote>
<pre>
&lt;Extensions&gt;
  &lt;uap:Extension Category="windows.fileTypeAssociation"&gt;
    &lt;uap:FileTypeAssociation Name="default"&gt;
      &lt;uap:DisplayName&gt;<span style="background-color: lightgreen">ms-resource:Resources/FileTypeDisplayName</span>&lt;/uap:DisplayName&gt;
      &lt;uap:Logo&gt;<span style="background-color: yellow">Assets\StoreLogo.png</span>&lt;/uap:Logo&gt;
      &lt;uap:InfoTip&gt;<span style="background-color: lightgreen">ms-resource:Resources/FileTypeInfoTip</span>&lt;/uap:InfoTip&gt;
      &lt;uap:SupportedFileTypes&gt;
        &lt;uap:FileType ContentType="<span style="background-color: yellow">application/x-contoso</span>"&gt;<span style="background-color: yellow">.contoso</span>&lt;/uap:FileType&gt;
      &lt;/uap:SupportedFileTypes&gt;
    &lt;/uap:FileTypeAssociation&gt;
  &lt;/uap:Extension&gt;
&lt;/Extensions&gt;
</pre>
</blockquote>

<span data-ttu-id="bcbff-318">Darüber hinaus können Sie diese Informationen mit dem Visual Studio-Manifest-Designer anhand der Registerkarte `Declarations` hinzufügen. Achten Sie dabei auf die <span style="background-color: lightgreen">hervorgehobenen Werte</span>:</span><span class="sxs-lookup"><span data-stu-id="bcbff-318">You can also add this information using the Visual Studio Manifest Designer, using the `Declarations` tab, taking note of the <span style="background-color: lightgreen">highlighted values</span>:</span></span>

<p><img src="images\editing-declarations-info.png"/></p>

<span data-ttu-id="bcbff-319">Fügen Sie jetzt die entsprechenden Ressourcennamen zu den einzelnen `.resw`-Dateien hinzu und ersetzen Sie somit den <span style="background-color: yellow">hervorgehobenen Text</span> mit dem entsprechenden Text Ihrer App (denken Sie daran, dass Sie diesen Vorgang für *jede unterstützte Sprache* durchführen müssen!):</span><span class="sxs-lookup"><span data-stu-id="bcbff-319">Now add the corresponding resource names to each of your `.resw` files, replacing the <span style="background-color: yellow">highlighted text</span> with the appropriate text for your app (remember to do this for *each supported language!*):</span></span>

<blockquote>
<pre>
... existing content...

&lt;data name="FileTypeDisplayName"&gt;
  &lt;value&gt;<span style="background-color: yellow">Contoso Demo File</span>&lt;/value&gt;
&lt;/data&gt;
&lt;data name="FileTypeInfoTip"&gt;
  &lt;value&gt;<span style="background-color: yellow">Files used by Contoso Demo App</span>&lt;/value&gt;
&lt;/data&gt;
</pre>
</blockquote>

<span data-ttu-id="bcbff-320">Dies wird dann in Teilen der Windows-Shell angezeigt, z.B. im Datei-Explorer:</span><span class="sxs-lookup"><span data-stu-id="bcbff-320">This will then show up in parts of the Windows shell, such as File Explorer:</span></span>

<p><img src="images\file-type-tool-tip.png"/></p>

<span data-ttu-id="bcbff-321">Erstellen und testen Sie das Paket wie zuvor. Führen Sie dabei alle neuen Szenarien aus, die die neuen UI-Zeichenfolgen anzeigen sollten.</span><span class="sxs-lookup"><span data-stu-id="bcbff-321">Build and test the package as before, exercising any new scenarios that should show the new UI strings.</span></span>

- - -

## <a name="phase-2-use-mrt-to-identify-and-locate-resources"></a><span data-ttu-id="bcbff-322">Phase 2: Verwenden von MRT, um Ressourcen zu identifizieren und zu suchen</span><span class="sxs-lookup"><span data-stu-id="bcbff-322">Phase 2: Use MRT to identify and locate resources</span></span>

<span data-ttu-id="bcbff-323">Im vorherigen Abschnitt wurde gezeigt, wie MRT verwendet wird, um die Manifestdatei der App zu lokalisieren, damit der Name der App und andere Metadaten durch Windows-Shell richtig angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="bcbff-323">The previous section showed how to use MRT to localize your app's manifest file so that the Windows Shell can correctly display the app's name and other metadata.</span></span> <span data-ttu-id="bcbff-324">Keine Code-Änderungen waren dafür erforderlich. Es ist lediglich die Verwendung von `.resw`-Dateien und einigen weiteren Tools erforderlich.</span><span class="sxs-lookup"><span data-stu-id="bcbff-324">No code changes were required for this; it simply required the use of `.resw` files and some additional tools.</span></span> <span data-ttu-id="bcbff-325">In diesem Abschnitt wird Ihnen gezeigt, wie Sie MRT zum Suchen von Ressourcen in Ihren vorhandenen Ressourcenformaten und Ihren vorhandenen Ressourcenbehandlungscode mit minimalen Änderungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="bcbff-325">This section will show how to use MRT to locate resources in your existing resource formats and using your existing resource-handling code with minimal changes.</span></span>

### <a name="assumptions-about-existing-file-layout--application-code"></a><span data-ttu-id="bcbff-326">Annahmen über vorhandenes Datei-Layout und Anwendungscode</span><span class="sxs-lookup"><span data-stu-id="bcbff-326">Assumptions about existing file layout & application code</span></span>

<span data-ttu-id="bcbff-327">Da es viele Möglichkeiten gibt, Win32-Desktop-Apps zu lokalisieren, wird dieses Dokument einige vereinfachende Annahmen über die vorhandene App-Struktur machen, die Sie zum Zuordnen Ihrer Umgebung benötigen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-327">Because there are many ways to localize Win32 Desktop apps, this paper will make some simplifying assumptions about the existing application's structure that you will need to map to your specific environment.</span></span> <span data-ttu-id="bcbff-328">Möglicherweise müssen Sie einige Änderungen an Ihre vorhandene Codebasis oder Ressourcen-Layout vornehmen, um den Anforderungen der MRT zu entsprechen. Diese gehören nicht zum Umfang dieses Dokuments.</span><span class="sxs-lookup"><span data-stu-id="bcbff-328">You might need to make some changes to your existing codebase or resource layout to conform to the requirements of MRT, and those are largely out of scope for this document.</span></span>

**<span data-ttu-id="bcbff-329">Layout der Ressourcendatei</span><span class="sxs-lookup"><span data-stu-id="bcbff-329">Resource file layout</span></span>**

<span data-ttu-id="bcbff-330">Dieses Whitepaper setzt voraus, dass all Ihre lokalisierten Ressourcen die gleichen Dateinamen aufweisen (z.B. `contoso_demo.exe.mui` oder `contoso_strings.dll` oder `contoso.strings.xml`), dass sie jedoch in unterschiedlichen Ordnern mit BCP-47 Namen (`en-US`, `de-DE` usw.) abgelegt wurden.</span><span class="sxs-lookup"><span data-stu-id="bcbff-330">This whitepaper assumes your localized resources all have the same filenames (eg, `contoso_demo.exe.mui` or `contoso_strings.dll` or `contoso.strings.xml`) but that they are placed in different folders with BCP-47 names (`en-US`, `de-DE`, etc.).</span></span> <span data-ttu-id="bcbff-331">Es spielt keine Rolle, wie viele Ressourcendateien Sie haben, wie sie benannt sind, welche Dateiformate/verknüpften APIs sie aufweisen usw. Das einzig Wichtige ist, dass alle *logischen* Ressourcen den gleichen Dateinamen aufweisen (sie müssen jedoch in verschiedenen *physischen* Verzeichnissen abgelegt werden).</span><span class="sxs-lookup"><span data-stu-id="bcbff-331">It doesn't matter how many resource files you have, what their names are, what their file-formats / associated APIs are, etc. The only thing that matters is that every *logical* resource has the same filename (but placed in a different *physical* directory).</span></span> 

<span data-ttu-id="bcbff-332">Gegenbeispiel: wenn Ihre Anwendung eine flache Dateistruktur mit einem einzigen `Resources`-Verzeichnis verwendet, das die Dateien `english_strings.dll` und `french_strings.dll` enthält, würde sie sich **nicht** gut zu MRT zuordnen lassen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-332">As a counter-example, if your application uses a flat file-structure with a single `Resources` directory containing the files `english_strings.dll` and `french_strings.dll`, it **would not** map well to MRT.</span></span> <span data-ttu-id="bcbff-333">Eine bessere Struktur wäre ein `Resources`-Verzeichnis mit Unterverzeichnissen und den Dateien `en\strings.dll` und `fr\strings.dll`
<a name="footnote8_ref" href="#footnote8"><sup>8</sup></a>.</span><span class="sxs-lookup"><span data-stu-id="bcbff-333">A better structure would be a `Resources` directory with subdirectories and files `en\strings.dll` and `fr\strings.dll`
<a name="footnote8_ref" href="#footnote8"><sup>8</sup></a>.</span></span> <span data-ttu-id="bcbff-334">Beachten Sie, dass es weiterhin möglich ist, MRT und die Vorteile von AppX-Paketen zu verwenden, auch wenn Sie dieser Konvention für die Dateibenennung nicht folgen können. Es ist einfach mehr Arbeit erforderlich.</span><span class="sxs-lookup"><span data-stu-id="bcbff-334">Note that it is still possible to use MRT and the benefits of AppX packaging even if you can't follow this filenaming convention; it just requires more work.</span></span> <span data-ttu-id="bcbff-335">Dieser Fall wird in einem künftigen Whitepaper behandelt.</span><span class="sxs-lookup"><span data-stu-id="bcbff-335">A future whitepaper will cover this case.</span></span> 

<span data-ttu-id="bcbff-336">Die Anwendung weist beispielweise eine Reihe von benutzerdefinierten Benutzeroberflächenbefehlen auf (die für Schaltflächenbeschriftungen usw. verwendet werden), die sich in einer einfachen Textdatei mit dem Namen <span style="background-color: yellow">ui.txt</span> befinden, die unter einem <span style="background-color: yellow">UICommands</span>-Ordner dargestellt wird:</span><span class="sxs-lookup"><span data-stu-id="bcbff-336">For example, the application might have a set of custom UI commands (used for button labels etc.) in a simple text file named <span style="background-color: yellow">ui.txt</span>, laid out under a <span style="background-color: yellow">UICommands</span> folder:</span></span>

<blockquote>
<pre>
+ ProjectRoot
|--+ Strings
|  |--+ en-US
|  |  \--- resources.resw
|  \--+ de-DE
|     \--- resources.resw
|--+ <span style="background-color: yellow">UICommands</span>
|  |--+ en-US
|  |  \--- <span style="background-color: yellow">ui.txt</span>
|  \--+ de-DE
|     \--- <span style="background-color: yellow">ui.txt</span>
|--- AppxManifest.xml
|--- ...rest of project...
</pre>
</blockquote>

**<span data-ttu-id="bcbff-337">Ressourcenladecode</span><span class="sxs-lookup"><span data-stu-id="bcbff-337">Resource loading code</span></span>**

<span data-ttu-id="bcbff-338">In diesem Whitepaper wird angenommen, dass Sie an einer bestimmten Stelle in Ihrem Code die Datei finden möchten, die eine lokalisierte Ressource enthält, und dass Sie diese laden und verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="bcbff-338">This whitepaper assumes that at some point in your code you want to locate the file that contains a localized resource, load it, and then use it.</span></span> <span data-ttu-id="bcbff-339">Die APIs, die zum Laden der Ressourcen verwendet werden und die APIs, die zum Extrahieren der Ressourcen verwendet werden, sind nicht wichtig.</span><span class="sxs-lookup"><span data-stu-id="bcbff-339">The APIs used to load the resources, the APIs used to extract the resources, etc. are not important.</span></span> <span data-ttu-id="bcbff-340">Im Pseudocode gibt es im Wesentlichen drei Schritte:</span><span class="sxs-lookup"><span data-stu-id="bcbff-340">In pseudocode, there are basically three steps:</span></span>

```
set userLanguage = GetUsersPreferredLanguage()
set resourceFile = FindResourceFileForLanguage(MY_RESOURCE_NAME, userLanguage)
set resource = LoadResource(resourceFile) 
    
// now use 'resource' however you want
```

<span data-ttu-id="bcbff-341">MRT erfordert nur das Ändern der ersten beiden Schritte in diesem Prozess – wie Sie die besten Ressourcen festlegen und wie Sie sie finden.</span><span class="sxs-lookup"><span data-stu-id="bcbff-341">MRT only requires changing the first two steps in this process - how you determine the best candidate resources and how you locate them.</span></span> <span data-ttu-id="bcbff-342">Es ist nicht erforderlich, das Laden oder die Verwendung der Ressourcen zu ändern (obwohl Ihnen dafür Hilftsmittel bereitgestellt, wenn Sie davon profitieren möchten).</span><span class="sxs-lookup"><span data-stu-id="bcbff-342">It doesn't require you to change how you load or use the resources (although it provides facilities for doing that if you want to take advantage of them).</span></span>
 
<span data-ttu-id="bcbff-343">Die Anwendung kann z.B. die Win32-API `GetUserPreferredUILanguages`, die CRT-Funktion `sprintf` und die Win32-API `CreateFile` verwenden, um die drei oben genannten Pseudocode-Funktionen zu ersetzen, und dann die Textdatei auf `name=value`-Paare manuell analysieren.</span><span class="sxs-lookup"><span data-stu-id="bcbff-343">For example, the application might use the Win32 API `GetUserPreferredUILanguages`, the CRT function `sprintf`, and the Win32 API `CreateFile` to replace the three pseudocode functions above, then manually parse the text file looking for `name=value` pairs.</span></span> <span data-ttu-id="bcbff-344">(Die Details sind nicht wichtig; dies dient lediglich der Veranschaulichung der Tatsache, dass MRT keine Auswirkung auf die Techniken hat, die für die Verarbeitung der Ressourcen verwendet wird, nachdem sie gefunden wurden).</span><span class="sxs-lookup"><span data-stu-id="bcbff-344">(The details are not important; this is merely to illustrate that MRT has no impact on the techniques used to handle resources once they have been located).</span></span>

### <a name="step-21-code-changes-to-use-mrt-to-locate-files"></a><span data-ttu-id="bcbff-345">Schritt2.1: Codeänderungen für die Verwendung von MRT, um Dateien zu suchen</span><span class="sxs-lookup"><span data-stu-id="bcbff-345">Step 2.1: Code changes to use MRT to locate files</span></span>

<span data-ttu-id="bcbff-346">Das Wechseln zwischen Codes für die Verwendung von MRT zum Suchen von Ressourcen ist nicht schwierig.</span><span class="sxs-lookup"><span data-stu-id="bcbff-346">Switching your code to use MRT for locating resources is not difficult.</span></span> <span data-ttu-id="bcbff-347">Es erfordert die Verwendung einer Handvoll von WinRT-Typen und ein paar Codezeilen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-347">It requires using a handful of WinRT types and a few lines of code.</span></span> <span data-ttu-id="bcbff-348">Die Haupttypen, die Sie verwenden werden, lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="bcbff-348">The main types that you will use are as follows:</span></span>

* <span data-ttu-id="bcbff-349">[ResourceContext](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Resources.Core.ResourceContext), das den derzeit aktiven Satz von Qualifiziererwerten enthält (Sprache, Skalierungsfaktor usw.).</span><span class="sxs-lookup"><span data-stu-id="bcbff-349">[ResourceContext](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Resources.Core.ResourceContext), which encapsulates the currently active set of qualifier values (language, scale factor, etc.)</span></span>
* <span data-ttu-id="bcbff-350">[ResourceManager](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.resources.core.resourcemanager), (die WinRT-Version, nicht die .NET-Version) der den Zugriff auf alle Ressourcen aus der PRI-Datei ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="bcbff-350">[ResourceManager](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.resources.core.resourcemanager) (the WinRT version, not the .NET version), which enables access to all the resources from the PRI file</span></span>
* <span data-ttu-id="bcbff-351">[ResourceMap](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.resources.core.resourcemap), die eine bestimmte Teilmenge der Ressourcen in der PRI-Datei (in diesem Beispiel stehen die dateibasierten Ressourcen im Vergleich zu den Zeichenfolgenressourcen) darstellt.</span><span class="sxs-lookup"><span data-stu-id="bcbff-351">[ResourceMap](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.resources.core.resourcemap), which represents a specific subset of the resources in the PRI file (in this example, the file-based resources vs. the string resources)</span></span>
* <span data-ttu-id="bcbff-352">[NamedResource](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Resources.Core.NamedResource), die eine logische Ressource mit allen möglichen Kandidaten darstellt.</span><span class="sxs-lookup"><span data-stu-id="bcbff-352">[NamedResource](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Resources.Core.NamedResource), which represents a logical resource and all its possible candidates</span></span>
* <span data-ttu-id="bcbff-353">[ResourceCandidate](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.resources.core.resourcecandidate), die eine konkrete Kandidatenressource darstellt.</span><span class="sxs-lookup"><span data-stu-id="bcbff-353">[ResourceCandidate](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.resources.core.resourcecandidate), which represents a single concrete candidate resource</span></span> 

<span data-ttu-id="bcbff-354">In Pseudocode würden Sie eine bestimmte Ressource würden Sie wie folgt einen gegebenen Ressourcen-Dateinamen (z.B. `UICommands\ui.txt` im obigen Beispiel) auflösen:</span><span class="sxs-lookup"><span data-stu-id="bcbff-354">In pseudo-code, the way you would resolve a given resource file name (like `UICommands\ui.txt` in the sample above) is as follows:</span></span>

```
// Get the ResourceContext that applies to this app
set resourceContext = ResourceContext.GetForViewIndependentUse()
    
// Get the current ResourceManager (there's one per app)
set resourceManager = ResourceManager.Current
    
// Get the "Files" ResourceMap from the ResourceManager
set fileResources = resourceManager.MainResourceMap.GetSubtree("Files")
    
// Find the NamedResource with the logical filename we're looking for,
// by indexing into the ResourceMap
set desiredResource = fileResources["UICommands\ui.txt"]
    
// Get the ResourceCandidate that best matches our ResourceContext
set bestCandidate = desiredResource.Resolve(resourceContext)
   
// Get the string value (the filename) from the ResourceCandidate
set absoluteFileName = bestCandidate.ValueAsString
```

<span data-ttu-id="bcbff-355">Beachten Sie insbesondere, dass der Code **nicht** einen bestimmten Sprachordner anfordert – z. B. `UICommands\en-US\ui.txt` – auch wenn die Dateien dementsprechend auf dem Datenträger gespeichert sind.</span><span class="sxs-lookup"><span data-stu-id="bcbff-355">Note in particular that the code does **not** request a specific language folder - like `UICommands\en-US\ui.txt` - even though that is how the files exist on-disk.</span></span> <span data-ttu-id="bcbff-356">Stattdessen wird nach dem *logischen* Dateinamen `UICommands\ui.txt` gefragt und der Code ist von MRT abhängig, um die entsprechende Datei auf dem Datenträger in einem der Sprachverzeichnisse zu finden.</span><span class="sxs-lookup"><span data-stu-id="bcbff-356">Instead, it asks for the *logical* filename `UICommands\ui.txt` and relies on MRT to find the appropriate on-disk file in one of the language directories.</span></span>

<span data-ttu-id="bcbff-357">Ab dieser Stelle kann die Beispiel-App weiterhin `CreateFile` zum Laden der `absoluteFileName` und Analysieren der `name=value`-Paare wie zuvor verwenden; diese Logik muss in der App nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="bcbff-357">From here, the sample app could continue to use `CreateFile` to load the `absoluteFileName` and parse the `name=value` pairs just as before; none of that logic needs to change in the app.</span></span> <span data-ttu-id="bcbff-358">Beim Schreiben in C# oder C++/CX ist der tatsächliche Code ist nicht viel komplizierter als dieser (und in der Tat können viele der temporären Variablen ausgelassen werden) – weitere Informationen finden Sie unten im Abschnitt **Laden der .NET-Ressourcen**.</span><span class="sxs-lookup"><span data-stu-id="bcbff-358">If you are writing in C# or C++/CX, the actual code is not much more complicated than this (and in fact many of the intermediate variables can be elided) - see the section on **Loading .NET resources**, below.</span></span> <span data-ttu-id="bcbff-359">C++/WRL-basierte Anwendungen werden aufgrund der COM-basierten APIs auf niedriger Ebene zum Aktivieren und Aufrufen der WinRT-APIs komplexer sein, aber die grundlegenden Schritte sind identisch. Weitere Informationen finden Sie unten im Abschnitt **Laden von Win32-MUI-Ressourcen**.</span><span class="sxs-lookup"><span data-stu-id="bcbff-359">C++/WRL-based applications will be more complex due to the low-level COM-based APIs used to activate and call the WinRT APIs, but the fundamental steps you take are the same - see the section on **Loading Win32 MUI resources**, below.</span></span>

**<span data-ttu-id="bcbff-360">Laden von .NET-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="bcbff-360">Loading .NET resources</span></span>**

<span data-ttu-id="bcbff-361">Da .NET über einen integrierten Mechanismus für das Suchen und Laden von Ressourcen (als „Satellitenassemblys” bekannt) verfügt, muss für kein expliziter Code wie im obigen synthetischen Beispiel ersetzt werden – in. NET benötigen Sie lediglich die Ressourcen-DLL-Dateien in den entsprechenden Verzeichnissen, und sie werden automatisch für Sie gefunden.</span><span class="sxs-lookup"><span data-stu-id="bcbff-361">Because .NET has a built-in mechanism for locating and loading resources (known as "Satellite Assemblies"), there is no explicit code to replace as in the synthetic example above - in .NET you just need your resource DLLs in the appropriate directories and they are automatically located for you.</span></span> <span data-ttu-id="bcbff-362">Wenn eine App als ein AppX-Paket anhand von Ressourcenpaketen verpackt wird, ist die Verzeichnisstruktur etwas anders – statt die Ressourcenverzeichnisse als Unterverzeichnisse des Hauptverzeichnisses der Anwendung festzulegen, werden sie als Peers vom Hauptverzeichnis festgelegt (oder sie sind gar nicht vorhanden, wenn der Benutzer die Sprache nicht in seinen Präferenzen aufgelistet hat).</span><span class="sxs-lookup"><span data-stu-id="bcbff-362">When an app is packaged as an AppX using resource packs, the directory structure is somewhat different - rather than having the resource directories be subdirectories of the main application directory, they are peers of it (or not present at all if the user doesn't have the language listed in their preferences).</span></span> 

<span data-ttu-id="bcbff-363">Stellen Sie sich beispielsweise eine .NET-Anwendung mit dem folgenden Layout vor, in dem alle Dateien unter dem `MainApp`-Ordner vorhanden sind:</span><span class="sxs-lookup"><span data-stu-id="bcbff-363">For example, imagine a .NET application with the following layout, where all the files exist under the `MainApp` folder:</span></span>

<blockquote>
<pre>
+ MainApp
|--+ en-us
|  \--- MainApp.resources.dll
|--+ de-de
|  \--- MainApp.resources.dll
|--+ fr-fr
|  \--- MainApp.resources.dll
\--- MainApp.exe
</pre>
</blockquote>

<span data-ttu-id="bcbff-364">Nach der Konvertierung zu AppX wird das Layout etwa wie folgt aussehen, sofern `en-US` als die Standardsprache festgelegt wurde und der Benutzer sowohl Deutsch als auch Französisch in seiner Liste aufgeführt hat:</span><span class="sxs-lookup"><span data-stu-id="bcbff-364">After conversion to AppX, the layout will look something like this, assuming `en-US` was the default language and the user has both German and French listed in their language list:</span></span>

<blockquote>
<pre>
+ WindowsAppsRoot
|--+ MainApp_neutral
|  |--+ en-us
|  |  \--- <span style="background-color: yellow">MainApp.resources.dll</span>
|  \--- MainApp.exe
|--+ MainApp_neutral_resources.language_de
|  \--+ de-de
|     \--- <span style="background-color: yellow">MainApp.resources.dll</span>
\--+ MainApp_neutral_resources.language_fr
   \--+ fr-fr
      \--- <span style="background-color: yellow">MainApp.resources.dll</span>
</pre>
</blockquote>

<span data-ttu-id="bcbff-365">Da die lokalisierten Ressourcen in den Unterverzeichnissen unterhalb des Installationsorts der ausführbaren Datei nicht mehr vorhanden sind, schlägt die integrierte .NET-Ressource fehl.</span><span class="sxs-lookup"><span data-stu-id="bcbff-365">Because the localized resources no longer exist in sub-directories underneath the main executable's install location, the built-in .NET resource resolution fails.</span></span> <span data-ttu-id="bcbff-366">Zum Glück verfügt .NET über einen klar definierten Mechanismus für die Behandlung von fehlgeschlagenen Assembly-Ladeversuchen – das `AssemblyResolve`-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="bcbff-366">Luckily, .NET has a well-defined mechanism for handling failed assembly load attempts - the `AssemblyResolve` event.</span></span> <span data-ttu-id="bcbff-367">Eine .NET-App, die MRT verwendet, muss für dieses Ereignis registriert werden und die fehlende Assembly für das .NET-Ressourcen-Subsystems bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-367">A .NET app using MRT must register for this event and provide the missing assembly for the .NET resource subsystem.</span></span> 

<span data-ttu-id="bcbff-368">Ein präzises Beispiel für die Verwendung von WinRT-APIs für das Suchen von durch .NET verwendeten Satelliten-Assemblys lautet wie folgt: der dargestellte Code wird absichtlich komprimiert, um eine minimale Implementierung anzuzeigen, obwohl sie wie Sie sehen können fast genau dem oben genannten Pseudocode entspricht, mit übergebenen `ResolveEventArgs`, die den zu suchenden Namen der Assembly bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="bcbff-368">A concise example of how to use the WinRT APIs to locate satellite assemblies used by .NET is as follows; the code as-presented is intentionally compressed to show a minimal implementation, although you can see it maps closely to the pseudo-code above, with the passed-in `ResolveEventArgs` providing the name of the assembly we need to locate.</span></span> <span data-ttu-id="bcbff-369">Eine ausführbare Version dieses Codes (mit ausführlichen Kommentare und Fehlerbehandlung) finden Sie in der Datei `PriResourceRsolver.cs` im [der **.NET Assembly Resolver**-Beispiel auf GitHub](https://aka.ms/fvgqt4).</span><span class="sxs-lookup"><span data-stu-id="bcbff-369">A runnable version of this code (with detailed comments and error-handling) can be found in the file `PriResourceRsolver.cs` in [the **.NET Assembly Resolver** sample on GitHub](https://aka.ms/fvgqt4).</span></span>

```C#
static class PriResourceResolver
{
  internal static Assembly ResolveResourceDll(object sender, ResolveEventArgs args)
  {
    var fullAssemblyName = new AssemblyName(args.Name);
    var fileName = string.Format(@"{0}.dll", fullAssemblyName.Name);

    var resourceContext = ResourceContext.GetForViewIndependentUse();
    resourceContext.Languages = new[] { fullAssemblyName.CultureName };

    var resource = ResourceManager.Current.MainResourceMap.GetSubtree("Files")[fileName];

    // Note use of 'UnsafeLoadFrom' - this is required for apps installed with AppX, but
    // in general is discouraged. The full sample provides a safer wrapper of this method
    return Assembly.UnsafeLoadFrom(resource.Resolve(resourceContext).ValueAsString);
  }
}
```

<span data-ttu-id="bcbff-370">Angesichts der oben aufgeführten Klasse, würden Sie Folgendes an einer beliebigen frühen Stelle im Startcode Ihrer Anwendung hinzufügen (bevor lokalisierte Ressourcen geladen werden müssten):</span><span class="sxs-lookup"><span data-stu-id="bcbff-370">Given the class above, you would add the following somewhere early-on in your application's startup code (before any localized resources would need to load):</span></span>

```C#
void EnableMrtResourceLookup()
{
  AppDomain.CurrentDomain.AssemblyResolve += PriResourceResolver.ResolveResourceDll;
}
```

<span data-ttu-id="bcbff-371">Die .NET-Laufzeit löst das Ereignis `AssemblyResolve` aus, wenn die Ressourcen-DLLs nicht gefunden werden kann. An diesem Punkt sucht der bereitgestellten Ereignishandler die gewünschte Datei über MRT, und gibt die Assembly zurück<a name="footnote9_ref" href="#footnote9"><sup>9</sup></a>.</span><span class="sxs-lookup"><span data-stu-id="bcbff-371">The .NET runtime will raise the `AssemblyResolve` event whenever it can't find the resource DLLs, at which point the provided event handler will locate the desired file via MRT and return the assembly<a name="footnote9_ref" href="#footnote9"><sup>9</sup></a>.</span></span>

**<span data-ttu-id="bcbff-372">Laden von Win32-MUI-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="bcbff-372">Loading Win32 MUI resources</span></span>**

<span data-ttu-id="bcbff-373">Das Laden von Win32-MUI-Ressourcen ist im Wesentlichen identisch mit dem Laden von .NET-Satellitenassemblys, es wird jedoch entweder der Code C++/CX oder C++/WRL verwendet.</span><span class="sxs-lookup"><span data-stu-id="bcbff-373">Loading Win32 MUI resources is essentially the same as loading .NET Satellite Assemblies, but using either C++/CX or C++/WRL code instead.</span></span> <span data-ttu-id="bcbff-374">Die Verwendung von C++/CX ermöglicht einen viel einfacheren Code, der dem oben aufgeführten Code C# sehr ähnelt, jedoch C++-Erweiterungen, Compiler-Switches und zusätzlichen Laufzeitaufwand verwendet, die Sie vielleicht vermeiden möchten.</span><span class="sxs-lookup"><span data-stu-id="bcbff-374">Using C++/CX allows for much simpler code that closely matches the C# code above, but it uses C++ language extensions, compiler switches, and additional runtime overheard you might wish to avoid.</span></span> <span data-ttu-id="bcbff-375">Wenn dies der Fall ist, stellt C++/WRL eine Lösung mit deutlich geringeren Auswirkungen dar – für den Preis von ausführlicherem Code.</span><span class="sxs-lookup"><span data-stu-id="bcbff-375">If that is the case, using C++/WRL provides a much lower-impact solution at the cost of more verbose code.</span></span> <span data-ttu-id="bcbff-376">Wenn Sie jedoch mit der ATL-Programmierung (oder mit COM im Allgemeinen) vertraut sind, sollte WRL ihnen vertraut vorkommen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-376">Nevertheless, if you are familiar with ATL programming (or COM in general) then WRL should feel familiar.</span></span> 

<span data-ttu-id="bcbff-377">Die folgende Beispielfunktion veranschaulicht, wie C++/WRL verwendet werden kann, um eine bestimmte Ressourcen-DLL zu laden und ein `HINSTANCE` zurückzugeben, das zum Laden weiterer Ressourcen mithilfe von Win32-Ressourcen-APIs verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="bcbff-377">The following sample function shows how to use C++/WRL to load a specific resource DLL and return an `HINSTANCE` that can be used to load further resources using the usual Win32 resource APIs.</span></span> <span data-ttu-id="bcbff-378">Beachten Sie, dass dieser Code auf der aktuellen Sprache des Benutzers beruht – anders als bei dem C#-Beispiel, bei dem der `ResourceContext` explizit mit der Sprache initialisiert wird, die von der .NET-Laufzeit angefordert wird.</span><span class="sxs-lookup"><span data-stu-id="bcbff-378">Note that unlike the C# sample that explicitly initializes the `ResourceContext` with the language requested by the .NET runtime, this code relies on the user's current language.</span></span>

```CPP
#include <roapi.h>
#include <wrl\client.h>
#include <wrl\wrappers\corewrappers.h>
#include <Windows.ApplicationModel.resources.core.h>
#include <Windows.Foundation.h>
   
#define IF_FAIL_RETURN(hr) if (FAILED((hr))) return hr;
    
HRESULT GetMrtResourceHandle(LPCWSTR resourceFilePath,  HINSTANCE* resourceHandle)
{
  using namespace Microsoft::WRL;
  using namespace Microsoft::WRL::Wrappers;
  using namespace ABI::Windows::ApplicationModel::Resources::Core;
  using namespace ABI::Windows::Foundation;
    
  *resourceHandle = nullptr;
  HRESULT hr{ S_OK };
  RoInitializeWrapper roInit{ RO_INIT_SINGLETHREADED };
  IF_FAIL_RETURN(roInit);
    
  // Get Windows.ApplicationModel.Resources.Core.ResourceManager statics
  ComPtr<IResourceManagerStatics> resourceManagerStatics;
  IF_FAIL_RETURN(GetActivationFactory(
    HStringReference(
    RuntimeClass_Windows_ApplicationModel_Resources_Core_ResourceManager).Get(),
    &resourceManagerStatics));
    
  // Get .Current property
  ComPtr<IResourceManager> resourceManager;
  IF_FAIL_RETURN(resourceManagerStatics->get_Current(&resourceManager));
    
  // get .MainResourceMap property
  ComPtr<IResourceMap> resourceMap;
  IF_FAIL_RETURN(resourceManager->get_MainResourceMap(&resourceMap));
    
  // Call .GetValue with supplied filename
  ComPtr<IResourceCandidate> resourceCandidate;
  IF_FAIL_RETURN(resourceMap->GetValue(HStringReference(resourceFilePath).Get(),
    &resourceCandidate));
    
  // Get .ValueAsString property
  HString resolvedResourceFilePath;
  IF_FAIL_RETURN(resourceCandidate->get_ValueAsString(
    resolvedResourceFilePath.GetAddressOf()));
    
  // Finally, load the DLL and return the hInst.
  *resourceHandle = LoadLibraryEx(resolvedResourceFilePath.GetRawBuffer(nullptr),
    nullptr, LOAD_LIBRARY_AS_DATAFILE | LOAD_LIBRARY_AS_IMAGE_RESOURCE);
    
  return S_OK;
}
```

## <a name="phase-3-building-resource-packs"></a><span data-ttu-id="bcbff-379">Phase 3: Erstellen von Ressourcenpaketen</span><span class="sxs-lookup"><span data-stu-id="bcbff-379">Phase 3: Building resource packs</span></span>

<span data-ttu-id="bcbff-380">Jetzt, da Sie über ein umfangreiches Paket verfügen, das alle Ressourcen enthält, gibt es zwei Möglichkeiten, das Hauptpaket und Ressourcenpakete separat zu erstellen, um die Größen für den Download und die Installation zu verringern:</span><span class="sxs-lookup"><span data-stu-id="bcbff-380">Now that you have a "fat pack" that contains all resources, there are two paths towards building separate main package and resource packages in order to minimize download and install sizes:</span></span>

0. <span data-ttu-id="bcbff-381">Nehmen Sie ein vorhandenes umfangreiches Paket, und führen Sie es im [Bündel-Generator-Tool](https://aka.ms/bundlegen) aus, um automatisch Ressourcenpakete zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-381">Take an existing fat pack and run it through [the Bundle Generator tool](https://aka.ms/bundlegen) to automatically create resource packs.</span></span> <span data-ttu-id="bcbff-382">Dies ist der bevorzugte Ansatz, wenn Sie über ein Buildsystem verfügen, das bereits ein umfangreiches Paket erstellt, und Sie dieses im Nachhinein verarbeiten möchten, um die Ressourcenpakete zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-382">This is the preferred approach if you have a build system that already produces a fat pack and you want to post-process it to generate the resource packs.</span></span>
0. <span data-ttu-id="bcbff-383">Erzeugen Sie die einzelnen Ressourcenpakete direkt, und integrieren Sie sie in ein Bündel.</span><span class="sxs-lookup"><span data-stu-id="bcbff-383">Directly produce the individual resource packages and build them into a bundle.</span></span> <span data-ttu-id="bcbff-384">Dies ist der bevorzugte Ansatz, wenn Sie mehr Kontrolle über Ihr Buildsystem haben und die Pakete direkt erstellen können.</span><span class="sxs-lookup"><span data-stu-id="bcbff-384">This is the preferred approach if you have more control over your build system and can build the packages directly.</span></span>

### <a name="step-31-creating-the-bundle"></a><span data-ttu-id="bcbff-385">Schritt3.1: Erstellen des Bündels</span><span class="sxs-lookup"><span data-stu-id="bcbff-385">Step 3.1: Creating the bundle</span></span>

**<span data-ttu-id="bcbff-386">Verwenden des Bündel-Generator-Tools</span><span class="sxs-lookup"><span data-stu-id="bcbff-386">Using the Bundle Generator tool</span></span>**

<span data-ttu-id="bcbff-387">Um das Bündel-Generator-Tool zu verwenden, muss die für das Paket erstellte PRI-Konfigurationsdatei manuell aktualisiert werden, um den Abschnitt `<packaging>` zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-387">In order to use the Bundle Generator tool, the PRI config file created for the package needs to be manually updated to remove the `<packaging>` section.</span></span>

<span data-ttu-id="bcbff-388">Wenn Sie Visual Studio verwenden, finden Sie im [Thema **Sicherstellen, dass Ressourcen auf einem Gerät installiert sind...** auf MSDN](https://msdn.microsoft.com/en-us/library/dn482043.aspx) Informationen dazu, wie Sie alle Sprachen in das Hauptpaket integrieren, indem Sie die Dateien `priconfig.packaging.xml` und `priconfig.default.xml` erstellen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-388">If you're using Visual Studio, refer to [the **Ensure that resources are installed...** topic on MSDN](https://msdn.microsoft.com/en-us/library/dn482043.aspx) for information on how to build all languages into the main package by creating the files `priconfig.packaging.xml` and `priconfig.default.xml`.</span></span>

<span data-ttu-id="bcbff-389">Wenn Sie Dateien manuell bearbeiten, gehen Sie folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="bcbff-389">If you're manually editing files, follow these steps:</span></span> 

0. <span data-ttu-id="bcbff-390">Erstellen Sie die Konfigurationsdatei auf die gleiche Weise wie zuvor, indem Sie den richtigen Pfad, den richtigen Dateinamen und die Sprachen ersetzen:</span><span class="sxs-lookup"><span data-stu-id="bcbff-390">Create the config file the same way as before, substituting the correct path, file name and languages:</span></span>

    `makepri createconfig /cf ..\contoso_demo.xml /dq en-US_de-DE_es-MX /pv 10.0 /o`
0. <span data-ttu-id="bcbff-391">Öffnen Sie die erstellte `.xml`-Datei manuell, und löschen Sie den gesamten Abschnitt `&lt;packaging&rt;` (alles andere muss jedoch intakt bleiben):</span><span class="sxs-lookup"><span data-stu-id="bcbff-391">Manually open the created `.xml` file and delete the entire `&lt;packaging&rt;` section (but keep everything else intact):</span></span>

<blockquote>
<pre>
&lt;?xml version="1.0" encoding="UTF-8" standalone="yes" ?&gt; 
&lt;resources targetOsVersion="10.0.0" majorVersion="1"&gt;
  &lt;!-- Packaging section has been deleted... --&gt;
  &lt;index root="\" startIndexAt="\"&gt;
    &lt;default&gt;
    ...
    ...
</pre>
</blockquote>

0. <span data-ttu-id="bcbff-392">Erstellen Sie die `.pri`-Datei und das `.appx`-Paket wie zuvor, indem Sie die aktualisierte Konfigurationsdatei und die entsprechenden Verzeichnis- und Dateinamen verwenden (oben finden Sie weitere Informationen zu diesen Befehlen):</span><span class="sxs-lookup"><span data-stu-id="bcbff-392">Build the `.pri` file and the `.appx` package as before, using the updated configuration file and the appropriate directory and file names (see above for more information on these commands):</span></span>

```CMD
makepri new /pr . /cf ..\contoso_demo.xml /of ..\resources.pri /mf AppX /o
makeappx pack /m AppXManifest.xml /f ..\resources.map.txt /p ..\contoso_demo.appx /o
```

0. <span data-ttu-id="bcbff-393">Nachdem das Paket erstellt wurde, verwenden Sie den folgenden Befehl, um das Bündel zu erstellen, indem Sie das richtige Verzeichnis und die richtigen Dateinamen verwenden:</span><span class="sxs-lookup"><span data-stu-id="bcbff-393">Once the package has been created, use the following command to create the bundle, using the appropriate directory and file names:</span></span>

    `BundleGenerator.exe -Package ..\contoso_demo.appx -Destination ..\bundle -BundleName contoso_demo`

<span data-ttu-id="bcbff-394">Nun können Sie mit dem letzten Schritt fortfahren, der Signierung (siehe unten).</span><span class="sxs-lookup"><span data-stu-id="bcbff-394">Now you can move to the final step, which is Signing (see below).</span></span>

**<span data-ttu-id="bcbff-395">Manuelles Erstellen von Ressourcenpaketen</span><span class="sxs-lookup"><span data-stu-id="bcbff-395">Manually creating resource packages</span></span>**

<span data-ttu-id="bcbff-396">Das manuelle Erstellen von Ressourcenpaketem erfordert die Ausführung eines etwas anderen Satzes von Befehlen, um eigene `.pri`- und `.appx`-Dateien zu erstellen. Diese sind den Befehlen ähnlich, die oben im Zusammenhang mit der Erstellung von FAT-Paketen beschrieben wurden. Daher werden sie nur wenig erklärt.</span><span class="sxs-lookup"><span data-stu-id="bcbff-396">Manually creating resource packages requires running a slightly different set of commands to build separate `.pri` and `.appx` files - these are all similar to the commands used above to create fat packages, so minimal explanation is given.</span></span> <span data-ttu-id="bcbff-397">Hinweis: Alle Befehle gehen davon aus, dass das aktuelle Verzeichnis das Verzeichnis ist, in dem sich die Datei `AppXManifest.xml` befindet. Alle Dateien werden jedoch in das übergeordnete Verzeichnis platziert. (Sie können ein anderes Verzeichnis verwenden, wenn erforderlich, sollten das Projektverzeichnis jedoch nicht mit einer dieser Dateien kontaminieren.)</span><span class="sxs-lookup"><span data-stu-id="bcbff-397">Note: All the commands assume that the current directory is the directory containing the `AppXManifest.xml` file, but all files are placed into the parent directory (you can use a different directory, if necessary, but you shouldn't pollute the project directory with any of these files).</span></span> <span data-ttu-id="bcbff-398">Wie immer, ersetzen Sie die „Contoso“-Dateinamen durch eigene Dateinamen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-398">As always, replace the "Contoso" filenames with your own file names.</span></span>

0. <span data-ttu-id="bcbff-399">Verwenden Sie den folgenden Befehl, um eine Konfigurationsdatei zu erstellen, die **nur** die Standardsprache als den Standardqualifizierer nennt, in diesem Fall `en-US`:</span><span class="sxs-lookup"><span data-stu-id="bcbff-399">Use the following command to create a config file that names **only** the default language as the default qualifier - in this case, `en-US`:</span></span>

    `makepri createconfig /cf ..\contoso_demo.xml /dq en-US /pv 10.0 /o`
0. <span data-ttu-id="bcbff-400">Erstellen Sie eine `.pri`- und `.map.txt`-Standarddatei für das Hauptpaket sowie einen zusätzlichen Satz von Dateien für jede Sprache in Ihrem Projekt. Verwenden Sie hierzu den folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="bcbff-400">Create a default `.pri` and `.map.txt` file for the main package, plus an additional set of files for each language found in your project, with the following command:</span></span>

    `makepri new /pr . /cf ..\contoso_demo.xml /of ..\resources.pri /mf AppX /o`
0. <span data-ttu-id="bcbff-401">Verwenden Sie den folgenden Befehl, um das Hauptpaket zu erstellen (das den ausführbaren Code und die Standardsprachressourcen enthält).</span><span class="sxs-lookup"><span data-stu-id="bcbff-401">Use the following command to create the main package (which contains the executable code and default language resources).</span></span> <span data-ttu-id="bcbff-402">Wie immer, ändern Sie den Namen wie gewünscht. Sie sollten das Paket jedoch in einem eigenen Verzeichnis platzieren, um das Erstellen des Bündels zu vereinfachen (dieses Beispiel verwendet das Verzeichnis `..\bundle`):</span><span class="sxs-lookup"><span data-stu-id="bcbff-402">As always, change the name as you see fit, although you should put the package in a separate directory to make creating the bundle easier later (this example uses the `..\bundle` directory):</span></span>

    `makeappx pack /m .\AppXManifest.xml /f ..\resources.map.txt /p ..\bundle\contoso_demo.main.appx /o`
0. <span data-ttu-id="bcbff-403">Nachdem das Hauptpaket erstellt wurde, verwenden Sie den folgenden Befehl einmal für jede weitere Sprache (d.h., Sie wiederholen diesen Befehl für jede Sprachzuordnungsdatei, die im vorherigen Schritt generiert wurde).</span><span class="sxs-lookup"><span data-stu-id="bcbff-403">After the main package has been created, use the following command once for each additional language (ie, repeat this command for each language map file generated in the previous step).</span></span> <span data-ttu-id="bcbff-404">Auch hier sollten Sie die Ausgabe in einem separaten Verzeichnis platzieren (in demselben Verzeichnis wie das Hauptpaket).</span><span class="sxs-lookup"><span data-stu-id="bcbff-404">Again, the output should be in a separate directory (the same one as the main package).</span></span> <span data-ttu-id="bcbff-405">Beachten Sie, dass die Sprache **sowohl** in der Option `/f` als auch in der Option `/p` angegeben ist, sowie die Verwendung des neuen Arguments `/r` (das anzeigt, dass ein Ressourcenpaket gewünscht wird):</span><span class="sxs-lookup"><span data-stu-id="bcbff-405">Note the language is specified **both** in the `/f` option and the `/p` option, and the use of the new `/r` argument (which indicates a Resource Package is desired):</span></span>

    `makeappx pack /r /m .\AppXManifest.xml /f ..\resources.language-de.map.txt /p ..\bundle\contoso_demo.de.appx /o`
0. <span data-ttu-id="bcbff-406">Kombinieren Sie alle Pakete aus dem Bündelverzeichnis in einer einzigen `.appxbundle`-Datei.</span><span class="sxs-lookup"><span data-stu-id="bcbff-406">Combine all the packages from the bundle directory into a single `.appxbundle` file.</span></span> <span data-ttu-id="bcbff-407">Die neue Option `/d` gibt das Verzeichnis für alle Dateien im Bündel an (daher wurden die `.appx`-Dateien im vorherigen Schritt in ein eigenes Verzeichnis platziert):</span><span class="sxs-lookup"><span data-stu-id="bcbff-407">The new `/d` option specifies the directory to use for all the files in the bundle (this is why the `.appx` files are put into a separate directory in the previous step):</span></span>

    `makeappx bundle /d ..\bundle /p ..\contoso_demo.appxbundle /o`

<span data-ttu-id="bcbff-408">Der letzte Schritt beim Erstellen des Pakets ist das Signieren.</span><span class="sxs-lookup"><span data-stu-id="bcbff-408">The final step to building the package is Signing.</span></span>

### <a name="step-32-signing-the-bundle"></a><span data-ttu-id="bcbff-409">Schritt3.2: Signieren des Bündels</span><span class="sxs-lookup"><span data-stu-id="bcbff-409">Step 3.2: Signing the bundle</span></span>

<span data-ttu-id="bcbff-410">Nachdem Sie die `.appxbundle`-Datei erstellt haben (entweder über das Bündel-Generator-Tool oder manuell), erhalten Sie eine einzelne Datei, die das Hauptpaket sowie alle Ressourcenpakete enthält.</span><span class="sxs-lookup"><span data-stu-id="bcbff-410">Once you have created the `.appxbundle` file (either through the Bundle Generator tool or manually) you will have a single file that contains the main package plus all the resource packages.</span></span> <span data-ttu-id="bcbff-411">Der letzte Schritt besteht im Signieren der Datei, damit sie von Windows installiert wird:</span><span class="sxs-lookup"><span data-stu-id="bcbff-411">The final step is to sign the file so that Windows will install it:</span></span>

    signtool sign /fd SHA256 /a /f ..\contoso_demo_key.pfx ..\contoso_demo.appxbundle

<span data-ttu-id="bcbff-412">In diesem Vorgang wird eine signierte `.appxbundle`-Datei erstellt, die das Hauptpaket sowie alle sprachspezifischen Ressourcenpakete enthält.</span><span class="sxs-lookup"><span data-stu-id="bcbff-412">This will produce a signed `.appxbundle` file that contains the main package plus all the language-specific resource packages.</span></span> <span data-ttu-id="bcbff-413">Wie bei einer Paketdatei werden durch Doppelklicken auf diese Datei die App und alle relevanten Sprachpakete installiert, abhängig von den Windows-Spracheinstellungen des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="bcbff-413">It can be double-clicked just like a package file to install the app plus any appropriate language(s) based on the user's Windows language preferences.</span></span> 
 
## <a name="footnotes"></a><span data-ttu-id="bcbff-414">Fußnoten</span><span class="sxs-lookup"><span data-stu-id="bcbff-414">Footnotes</span></span>

<span data-ttu-id="bcbff-415">Klicken Sie auf die Zahl, um zum ursprünglichen Ort im Dokument zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="bcbff-415">Click on the number to return to the source location in the document.</span></span>

<span data-ttu-id="bcbff-416"><a name="footnote1" href="#footnote1_ref">1.</a> Dieses Dokument stellt keine weiteren Gründe für die eigentliche Lokalisierung bereit. Es wird angenommen, dass der Leser bereits hiermit vertraut ist.</span><span class="sxs-lookup"><span data-stu-id="bcbff-416"><a name="footnote1" href="#footnote1_ref">1.</a> This paper provides no further motivation for localization itself; it is assumed the reader already understands this.</span></span>

<span data-ttu-id="bcbff-417"><a name="footnote2" href="#footnote2_ref">2.</a> In der Vergangenheit bedeutete dies „Modern Resource Technology“ (moderne Ressourcentechnologie). Der Bestandteil „Modern“ wird jedoch nicht mehr verwendet.</span><span class="sxs-lookup"><span data-stu-id="bcbff-417"><a name="footnote2" href="#footnote2_ref">2.</a> Historically this stood for "Modern Resource Technology" but the term "Modern" has been discontinued.</span></span> <span data-ttu-id="bcbff-418">Der Ressourcen-Manager ist möglicherweise auch unter den Namen MRM (Modern Resource Manager, moderner Ressourcen-Manager) oder PRI (Package Resource Index, Paketressourcenindex) bekannt.</span><span class="sxs-lookup"><span data-stu-id="bcbff-418">The resource manager might also be known as MRM (Modern Resource Manager) or PRI (Package Resource Index).</span></span>

<span data-ttu-id="bcbff-419"><a name="footnote3" href="#footnote3_ref">3.</a> Diese Tabelle keine Angaben zu anderen als Lokalisierungsaufgaben, z.B. das Bereitstellen von Anwendungssymbolen mit hoher Auflösung oder einem hohen Kontrastverhältnis.</span><span class="sxs-lookup"><span data-stu-id="bcbff-419"><a name="footnote3" href="#footnote3_ref">3.</a> This table doesn't include non-localization tasks, such as providing high-resolution or high-contrast application icons.</span></span> <span data-ttu-id="bcbff-420">Weitere Informationen zum Bereitstellen mehrerer Ressourcen für Kacheln, Symbole usw. finden Sie auf MSDN.</span><span class="sxs-lookup"><span data-stu-id="bcbff-420">See MSDN for more information about providing multiple assets for tiles, icons, etc.</span></span>

<span data-ttu-id="bcbff-421"><a name="footnote4" href="#footnote4_ref">4.</a> Die Einzelheiten im Zusammenhang mit dem Skalierungsfaktor werden hier nicht behandelt.</span><span class="sxs-lookup"><span data-stu-id="bcbff-421"><a name="footnote4" href="#footnote4_ref">4.</a> The specifics of scale factor are not covered here</span></span>

<span data-ttu-id="bcbff-422"><a name="footnote5" href="#footnote5_ref">5.</a> Beachten Sie, dass es Einschränkungen in Bezug auf die Länge einiger Zeichenfolgen gibt; weitere Informationen finden Sie im [Thema **VisualElements** auf MSDN](https://msdn.microsoft.com/en-us/library/windows/apps/br211471.aspx).</span><span class="sxs-lookup"><span data-stu-id="bcbff-422"><a name="footnote5" href="#footnote5_ref">5.</a> Note that there are restrictions on the lengths of some of these strings; see [the **VisualElements** topic on MSDN](https://msdn.microsoft.com/en-us/library/windows/apps/br211471.aspx) for more information</span></span> 

<span data-ttu-id="bcbff-423"><a name="footnote6" href="#footnote6_ref">6.</a> Es besteht keine Notwendigkeit, genau diese Ressourcennamen zu verwenden. Sie können eigene Ressourcennamen verwenden, die jedoch genau mit den Angaben in der Datei `.resw` übereinstimmen müssen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-423"><a name="footnote6" href="#footnote6_ref">6.</a> There is no requirement to use these exact resource names - you can choose your own - but whatever you choose must exactly match whatever is in the `.resw` file.</span></span>

<span data-ttu-id="bcbff-424"><a name="footnote7" href="#footnote7_ref">7.</a> Sie können ein anderes Verzeichnis wählen. Achten Sie jedoch darauf, dieses in zukünftigen Befehlen zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="bcbff-424"><a name="footnote7" href="#footnote7_ref">7.</a> You can choose any other directory you want, but be sure to substitute that in future commands</span></span>

<span data-ttu-id="bcbff-425"><a name="footnote8" href="#footnote8_ref">8.</a> Es ist auch möglich, den gleichen Basisdateinamen mit eingebetteten Qualifizierern zu verwenden, z.B. `strings.lang-en.dll` und `strings.lang-fr.dll`. Die Verwendung von Verzeichnissen mit Sprachcodes ist jedoch konzeptionell einfacher. Daher konzentrieren wir uns auf diese Vorgehensweise.</span><span class="sxs-lookup"><span data-stu-id="bcbff-425"><a name="footnote8" href="#footnote8_ref">8.</a> It's also possible to use the same base filename but with embedded qualifiers, such as `strings.lang-en.dll` and `strings.lang-fr.dll`, but using directories with the language codes is conceptually simpler so it's what we'll focus on.</span></span>

<span data-ttu-id="bcbff-426"><a name="footnote9" href="#footnote9_ref">9.</a> Beachten Sie, dass Ihre App bereits einen `AssemblyResolve`-Handler für andere Zwecke besitzt. Sie müssen den ressourcenauflösenden Code mit dem vorhandenen Code integrieren.</span><span class="sxs-lookup"><span data-stu-id="bcbff-426"><a name="footnote9" href="#footnote9_ref">9.</a> Note that if your app already has an `AssemblyResolve` handler for other purposes, you will need to integrate the resource-resolving code with your existing code.</span></span>
