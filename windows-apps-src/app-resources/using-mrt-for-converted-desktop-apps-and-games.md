---
title: Verwenden von MRT für konvertierte Desktop-Apps und -Spiele
description: Indem Sie Ihre .NET- oder Win32-App oder Ihr Spiel als AppX-Paket verpacken, können Sie das Ressourcenverwaltungssystem nutzen, um App-Ressourcen zu laden, die auf den Laufzeitkontext zugeschnitten sind. In diesem Thema werden die erforderlichen Techniken detailliert beschrieben.
ms.date: 10/25/2017
ms.topic: article
keywords: Windows10, UWP, mrt, pri. Ressourcen, Spiele, Centennial, Desktop App Converter, mui, Satellitenassembly
ms.localizationpriority: medium
ms.openlocfilehash: 620efc73502c741e415d210170ea53deefd4e974
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8927953"
---
# <a name="use-the-windows-10-resource-management-system-in-a-legacy-app-or-game"></a><span data-ttu-id="d0d0e-106">Verwenden des Ressourcenverwaltungssystem für Windows 10 in älteren Apps oder Spielen</span><span class="sxs-lookup"><span data-stu-id="d0d0e-106">Use the Windows 10 Resource Management System in a legacy app or game</span></span>

## <a name="overview"></a><span data-ttu-id="d0d0e-107">Übersicht</span><span class="sxs-lookup"><span data-stu-id="d0d0e-107">Overview</span></span>

<span data-ttu-id="d0d0e-108">Apps und Spiele für .NET und Win32 werden häufig in verschiedene Sprachen übersetzt, um die Anzahl potenzieller Märkte zu vergrößern.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-108">.NET and Win32 apps and games are often localized into different languages to expand their total addressable market.</span></span> <span data-ttu-id="d0d0e-109">Weitere Informationen zu einer Werterhöhung Ihrer App durch Lokalisierung finden Sie unter [Globalisierung und Lokalisierung](../design/globalizing/globalizing-portal.md).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-109">For more info about the value proposition of localizing your app, see [Globalization and localization](../design/globalizing/globalizing-portal.md).</span></span> <span data-ttu-id="d0d0e-110">Indem Sie Ihre .NET- oder Win32-App oder Ihr Spiel als AppX-Paket verpacken, können Sie das Ressourcenverwaltungssystem nutzen, um App-Ressourcen zu laden, die auf den Laufzeitkontext zugeschnitten sind.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-110">By packaging your .NET or Win32 app or game as an AppX package, you can leverage the Resource Management System to load app resources tailored to the run-time context.</span></span> <span data-ttu-id="d0d0e-111">In diesem Thema werden die erforderlichen Techniken detailliert beschrieben.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-111">This in-depth topic describes the techniques.</span></span>

<span data-ttu-id="d0d0e-112">Es gibt viele Möglichkeiten zum Lokalisieren einer herkömmlichen Win32-Anwendung, aber unter Windows 8 wurde ein neues [Ressourcenverwaltungssystem](https://msdn.microsoft.com/en-us/library/windows/apps/jj552947.aspx) eingeführt, das sich für alle Programmiersprachen und alle Anwendungstypen eignet und Funktionalität für mehr als eine einfache Lokalisierung bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-112">There are many ways to localize a traditional Win32 application, but Windows 8 introduced a [new resource-management system](https://msdn.microsoft.com/en-us/library/windows/apps/jj552947.aspx) that works across programming languages, across application types, and provides functionality over and above simple localization.</span></span> <span data-ttu-id="d0d0e-113">Dieses System wird im vorliegenden Artikel als „MRT” bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-113">This system will be referred to as "MRT" in this topic.</span></span> <span data-ttu-id="d0d0e-114">Früher bedeutete dies „Modern Resource Technology“. Der Bestandteil „Modern“ wird jedoch nicht mehr verwendet.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-114">Historically, that stood for "Modern Resource Technology" but the term "Modern" has been discontinued.</span></span> <span data-ttu-id="d0d0e-115">Der Ressourcen-Manager ist möglicherweise auch unter den Namen MRM (Modern Resource Manager, moderner Ressourcen-Manager) oder PRI (Package Resource Index, Paketressourcenindex) bekannt.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-115">The resource manager might also be known as MRM (Modern Resource Manager) or PRI (Package Resource Index).</span></span>

<span data-ttu-id="d0d0e-116">In Kombination mit einer AppX-basierten Bereitstellung (z.B. über den Microsoft Store) kann MRT automatisch die am besten anwendbaren Ressourcen für einen bestimmten Benutzer/ein bestimmtes Gerät bereitstellen, wodurch die Größe des Downloads und der Installationsumfang der Anwendung verringert werden.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-116">Combined with AppX-based deployment (for example, from the Microsoft Store), MRT can automatically deliver the most-applicable resources for a given user / device which minimizes the download and install size of your application.</span></span> <span data-ttu-id="d0d0e-117">Die Größenreduzierung kann bei Anwendungen mit einer großen Menge an lokalisiertem Inhalt erheblich sein, möglicherweise in einer Größenordnung von mehreren *Gigabytes* für AAA-Spiele.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-117">This size reduction can be significant for applications with a large amount of localized content, perhaps on the order of several *gigabytes* for AAA games.</span></span> <span data-ttu-id="d0d0e-118">Weitere Vorteile von MRT sind lokalisierte Angebote in der Windows-Shell und im Microsoft Store sowie eine automatische Fallback-Logik für den Fall, dass die bevorzugte Sprache eines Benutzers nicht den verfügbaren Ressourcen entspricht.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-118">Additional benefits of MRT include localized listings in the Windows Shell and the Microsoft Store, automatic fallback logic when a user's preferred language doesn't match your available resources.</span></span>

<span data-ttu-id="d0d0e-119">Dieses Dokument beschreibt die allgemeine MRT-Architektur und stellt ein Handbuch für das Portieren bereit, sodass ältere Win32-Anwendungen mit minimalen Codeänderungen zu MRT verschoben werden können.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-119">This document describes the high-level architecture of MRT and provides a porting guide to help move legacy Win32 applications to MRT with minimal code changes.</span></span> <span data-ttu-id="d0d0e-120">Wenn der Wechsel zu MRT erfolgt sind, stehen Entwicklern weitere Vorteile zur Verfügung (z.B. die Möglichkeit, Ressourcen nach Skalierungsfaktor oder Systemdesign zu segmentieren).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-120">Once the move to MRT is made, additional benefits (such as the ability to segment resources by scale factor or system theme) become available to the developer.</span></span> <span data-ttu-id="d0d0e-121">Beachten Sie, dass die MRT-basierte Lokalisierung sowohl für UWP-Anwendungen als auch für Win32-Anwendungen funktioniert, die von der Desktop-Brücke verarbeitet werden (auch bekannt als „Centennial”).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-121">Note that MRT-based localization works for both UWP applications and Win32 applications processed by the Desktop Bridge (aka "Centennial").</span></span>

<span data-ttu-id="d0d0e-122">In vielen Fällen können Sie Ihre vorhandenen Lokalisierungsformate und Ihren Quellcode auch nach der Integration mit MRT noch verwenden, um Ressourcen zur Laufzeit aufzulösen und Downloadgrößen zu verringern – es ist kein „Ganz-oder-gar-nicht-Ansatz”.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-122">In many situations, you can continue to use your existing localization formats and source code whilst integrating with MRT for resolving resources at runtime and minimizing download sizes - it's not an all-or-nothing approach.</span></span> <span data-ttu-id="d0d0e-123">Die folgende Tabelle fasst die Aufgabe und die geschätzten Kosten bzw. den Nutzen jeder Phase zusammen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-123">The following table summarizes the work and estimated cost/benefit of each stage.</span></span> <span data-ttu-id="d0d0e-124">Diese Tabelle enthält nur Aufgaben, welche die Lokalisierung betreffen, also keine Aufgaben wie z. B. das Bereitstellen von Anwendungssymbolen mit hoher Auflösung oder hohem Kontrast.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-124">This table doesn't include non-localization tasks, such as providing high-resolution or high-contrast application icons.</span></span> <span data-ttu-id="d0d0e-125">Weitere Informationen zum Bereitstellen von mehreren Ressourcen für Kacheln, Symbole usw. finden Sie unter [Anpassen von Ressourcen mit Qualifizierern für Sprache, Skalierung, hohen Kontrast und anderen Qualifizierern](tailor-resources-lang-scale-contrast.md).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-125">For more info about providing multiple assets for tiles, icons, etc., See [Tailor your resources for language, scale, high contrast, and other qualifiers](tailor-resources-lang-scale-contrast.md).</span></span>

<table>
<tr>
<th><span data-ttu-id="d0d0e-126">Aufgabe</span><span class="sxs-lookup"><span data-stu-id="d0d0e-126">Work</span></span></th>
<th><span data-ttu-id="d0d0e-127">Vorteil</span><span class="sxs-lookup"><span data-stu-id="d0d0e-127">Benefit</span></span></th>
<th><span data-ttu-id="d0d0e-128">Geschätzte Kosten</span><span class="sxs-lookup"><span data-stu-id="d0d0e-128">Estimated cost</span></span></th>
</tr>
<tr>
<td><span data-ttu-id="d0d0e-129">Lokalisieren des AppX-Manifests</span><span class="sxs-lookup"><span data-stu-id="d0d0e-129">Localize AppX manifest</span></span></td>
<td><span data-ttu-id="d0d0e-130">Kaum Arbeitsaufwand erforderlich, damit der lokalisierte Inhalt in der Windows-Shell und im Microsoft Store angezeigt wird</span><span class="sxs-lookup"><span data-stu-id="d0d0e-130">Bare minimum work required to have your localized content appear in the Windows Shell and in the Microsoft Store</span></span></td>
<td><span data-ttu-id="d0d0e-131">Gering</span><span class="sxs-lookup"><span data-stu-id="d0d0e-131">Small</span></span></td>
</tr>
<tr>
<td><span data-ttu-id="d0d0e-132">Verwenden von MRT zum Erkennen und Suchen von Ressourcen</span><span class="sxs-lookup"><span data-stu-id="d0d0e-132">Use MRT to identify and locate resources</span></span></td>
<td><span data-ttu-id="d0d0e-133">Voraussetzung für die Verringerung der Download- und Installationsgrößen; automatischer Fallback für Sprachen</span><span class="sxs-lookup"><span data-stu-id="d0d0e-133">Pre-requisite to minimizing download and install sizes; automatic language fallback</span></span></td>
<td><span data-ttu-id="d0d0e-134">Mittel</span><span class="sxs-lookup"><span data-stu-id="d0d0e-134">Medium</span></span></td>
</tr>
<tr>
<td><span data-ttu-id="d0d0e-135">Erstellen von Ressourcenpaketen</span><span class="sxs-lookup"><span data-stu-id="d0d0e-135">Build resource packs</span></span></td>
<td><span data-ttu-id="d0d0e-136">Letzter Schritt für die Verringerung der Download- und Installationsgrößen</span><span class="sxs-lookup"><span data-stu-id="d0d0e-136">Final step to minimize download and install sizes</span></span></td>
<td><span data-ttu-id="d0d0e-137">Gering</span><span class="sxs-lookup"><span data-stu-id="d0d0e-137">Small</span></span></td>
</tr>
<tr>
<td><span data-ttu-id="d0d0e-138">Migrieren von MRT-Ressourcenformaten und APIs</span><span class="sxs-lookup"><span data-stu-id="d0d0e-138">Migrate to MRT resource formats and APIs</span></span></td>
<td><span data-ttu-id="d0d0e-139">Erheblich geringere Dateigrößen (je nach vorhandener Ressourcentechnologie)</span><span class="sxs-lookup"><span data-stu-id="d0d0e-139">Significantly smaller file sizes (depending on existing resource technology)</span></span></td>
<td><span data-ttu-id="d0d0e-140">Hoch</span><span class="sxs-lookup"><span data-stu-id="d0d0e-140">Large</span></span></td>
</tr>
</table>

## <a name="introduction"></a><span data-ttu-id="d0d0e-141">Einführung</span><span class="sxs-lookup"><span data-stu-id="d0d0e-141">Introduction</span></span>

<span data-ttu-id="d0d0e-142">Die meisten umfassenden Anwendungen enthalten Benutzeroberflächenelemente, auch als *Ressourcen* bezeichnet, die von dem Code der Anwendung entkoppelt werden (im Gegensatz zu *hartcodierten Werte*, die im Quellcode selbst verfasst werden).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-142">Most non-trivial applications contain user-interface elements known as *resources* that are decoupled from the application's code (contrasted with *hard-coded values* that are authored in the source code itself).</span></span> <span data-ttu-id="d0d0e-143">Es gibt verschiedene Gründe dafür, Ressourcen gegenüber hartcodierten Werten zu bevorzugen – wie beispielsweise die einfache Bearbeitung durch Nicht-Entwickler –, einer der wichtigsten Gründe ist jedoch, dass die App auf diese Weise verschiedene Darstellungen derselben logischen Ressource zur Laufzeit auswählen kann.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-143">There are several reasons to prefer resources over hard-coded values - ease of editing by non-developers, for example - but one of the key reasons is to enable the application to pick different representations of the same logical resource at runtime.</span></span> <span data-ttu-id="d0d0e-144">Beispielsweise unterscheidet sich der auf einer Schaltfläche anzuzeigende Text (oder das in einem Symbol anzuzeigende Bild) abhängig von der/den Sprache(n), die ein Benutzer versteht, den Eigenschaften des Anzeigegeräts oder davon, ob eine Hilfstechnologie aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-144">For example, the text to display on a button (or the image to display in an icon) might differ depending on the language(s) the user understands, the characteristics of the display device, or whether the user has any assistive technologies enabled.</span></span>

<span data-ttu-id="d0d0e-145">Daher besteht der Hauptzweck von Ressourcenverwaltungstechnologien darin, zur Laufzeit eine Anfrage für einen logischen oder symbolischen *Ressourcennamen* (z.B. `SAVE_BUTTON_LABEL`) aus einer Reihe von möglichen *Kandidaten* (z.B. „Save”, „Speichern” oder „저장”) in den bestmöglichen tatsächlichen *Wert* (z.B. „Speichern”) zu übersetzen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-145">Thus the primary purpose of any resource-management technology is to translate, at runtime, a request for a logical or symbolic *resource name* (such as `SAVE_BUTTON_LABEL`) into the best possible actual *value* (eg, "Save") from a set of possible *candidates* (eg, "Save", "Speichern", or "저장").</span></span> <span data-ttu-id="d0d0e-146">MRT stellt eine solche Funktion bereit und ermöglicht es Anwendungen, Ressourcenkandidaten mithilfe von verschiedenen Attributen, den *Qualifizierern*, wie beispielsweise der Sprache des Benutzers, dem Skalierungsfaktor des Displays, dem ausgewählten Design des Benutzers und anderen Umgebungsfaktoren, zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-146">MRT provides such a function, and enables applications to identify resource candidates using a wide variety of attributes, called *qualifiers*, such as the user's language, the display scale-factor, the user's selected theme, and other environmental factors.</span></span> <span data-ttu-id="d0d0e-147">MRT unterstützt auch benutzerdefinierte Qualifizierer für Anwendungen, die diese benötigen (beispielsweise könnte eine Anwendung für Benutzer, die sich mit einem Konto angemeldet haben, und für Gastbenutzer unterschiedliche grafische Ressourcen bereitstellen, ohne dass diese Prüfung explizit zu jedem Teil der Anwendung hinzugefügt wird).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-147">MRT even supports custom qualifiers for applications that need it (for example, an application could provide different graphic assets for users that had logged in with an account vs. guest users, without explicitly adding this check into every part of their application).</span></span> <span data-ttu-id="d0d0e-148">MRT funktioniert sowohl mit Zeichenfolgenressourcen als auch mit dateibasierten Ressourcen, wenn dateibasierte Ressourcen als Verweise auf die externen Daten (die Dateien selbst) implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-148">MRT works with both string resources and file-based resources, where file-based resources are implemented as references to the external data (the files themselves).</span></span> 

### <a name="example"></a><span data-ttu-id="d0d0e-149">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d0d0e-149">Example</span></span>

<span data-ttu-id="d0d0e-150">Dies ist ein einfaches Beispiel für eine Anwendung mit Beschriftungen auf zwei Schaltflächen (`openButton` und `saveButton`) und einer PNG-Datei, die für ein Logo verwendet wird (`logoImage`).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-150">Here's a simple example of an application that has text labels on two buttons (`openButton` and `saveButton`) and a PNG file used for a logo (`logoImage`).</span></span> <span data-ttu-id="d0d0e-151">Die Beschriftungen werden ins Englische und ins Deutsche übersetzt, und das Logo ist für normale Desktopdisplays (Skalierungsfaktor 100%) und hochauflösende Smartphones (Skalierungsfaktor 300%) optimiert.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-151">The text labels are localized into English and German, and the logo is optimized for normal desktop displays (100% scale factor) and high-resolution phones (300% scale factor).</span></span> <span data-ttu-id="d0d0e-152">Beachten Sie, dass dieses Diagramm eine allgemeine konzeptionelle Ansicht des Modells darstellt. Es entspricht nicht genau der Implementierung.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-152">Note that this diagram presents a high-level, conceptual view of the model; it does not map exactly to implementation.</span></span>

<p><img src="images\conceptual-resource-model.png"/></p>

<span data-ttu-id="d0d0e-153">In der Grafik verweist der Anwendungscode auf die drei logischen Ressourcennamen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-153">In the graphic, the application code references the three logical resource names.</span></span> <span data-ttu-id="d0d0e-154">Zur Laufzeit verwendet die Pseudo-Funktion `GetResource` MRT, um diese Ressourcennamen in der Ressourcentabelle (als PRI-Datei bezeichnet) zu suchen und basierend auf den Umgebungsbedingungen (der Sprache des Benutzers und dem Skalierungsfaktor des Displays) den am besten geeigneten Kandidaten zu finden.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-154">At runtime, the `GetResource` pseudo-function uses MRT to look those resource names up in the resource table (known as PRI file) and find the most appropriate candidate based on the ambient conditions (the user's language and the display's scale-factor).</span></span> <span data-ttu-id="d0d0e-155">Bei Beschriftungen werden die Zeichenfolgen direkt verwendet.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-155">In the case of the labels, the strings are used directly.</span></span> <span data-ttu-id="d0d0e-156">Beim Logobild werden die Zeichenfolgen als Dateinamen interpretiert, und die Dateien werden von der Festplatte gelesen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-156">In the case of the logo image, the strings are interpreted as filenames and the files are read off disk.</span></span> 

<span data-ttu-id="d0d0e-157">Wenn der Benutzer eine andere Sprache als Englisch oder Deutsch spricht oder einen anderen Skalierungsfaktor als 100% oder 300% verwendet, wählt MRT auf Grundlager einer Reihe von Fallbackregeln den Kandidaten mit den größten Übereinstimmung (weitere Hintergrundinformationen dazu im [Thema **Ressourcenverwaltungssystem** auf MSDN](https://msdn.microsoft.com/en-us/library/windows/apps/jj552947.aspx)).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-157">If the user speaks a language other than English or German, or has a display scale-factor other than 100% or 300%, MRT picks the "closest" matching candidate based on a set of fallback rules (see [the **Resource Management System** topic on MSDN](https://msdn.microsoft.com/en-us/library/windows/apps/jj552947.aspx) for more background).</span></span> 

<span data-ttu-id="d0d0e-158">Beachten Sie, dass MRT Ressourcen unterstützt, die auf mehrere Qualifizierer zugeschnitten sind – wenn beispielsweise das Logobild eingebetteten Text enthält, der auch lokalisiert werden muss, würde das Logo über vier Kandidaten verfügen: EN/Scale-100, DE/Scale-100, EN/Scale-300 and DE/Scale-300.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-158">Note that MRT supports resources that are tailored to more than one qualifier - for example, if the logo image contained embedded text that also needed to be localized, the logo would have four candidates: EN/Scale-100, DE/Scale-100, EN/Scale-300 and DE/Scale-300.</span></span>

### <a name="sections-in-this-document"></a><span data-ttu-id="d0d0e-159">Abschnitte in diesem Dokument</span><span class="sxs-lookup"><span data-stu-id="d0d0e-159">Sections in this document</span></span>

<span data-ttu-id="d0d0e-160">In den folgenden Abschnitten werden die allgemeinen Aufgaben dargestellt, die für die Integration von MRT in Ihre Anwendung erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-160">The following sections outline the high-level tasks required to integrate MRT with your application.</span></span>

**<span data-ttu-id="d0d0e-161">Phase 0: Erstellen eines Anwendungspakets</span><span class="sxs-lookup"><span data-stu-id="d0d0e-161">Phase 0: Build an application package</span></span>**

<span data-ttu-id="d0d0e-162">In diesem Abschnitt wird beschrieben, wie Sie Ihre vorhandene Desktopanwendung zu einem Anwendungspaket machen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-162">This section outlines how to get your existing Desktop application building as an application package.</span></span> <span data-ttu-id="d0d0e-163">In dieser Phase werden keine MRT-Features verwendet.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-163">No MRT features are used at this stage.</span></span>

**<span data-ttu-id="d0d0e-164">Phase 1: Lokalisieren des Anwendungsmanifests</span><span class="sxs-lookup"><span data-stu-id="d0d0e-164">Phase 1: Localize the application manifest</span></span>**

<span data-ttu-id="d0d0e-165">In diesem Abschnitt wird beschrieben, wie Sie das Manifest Ihrer Anwendung lokalisieren (damit es richtig in der Windows-Shell angezeigt wird), während noch Ihr älteres Ressourcenformat und Ihre älteren APIs verwendet werden, um Ressourcen zu packen und zu suchen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-165">This section outlines how to localize your application's manifest (so that it appears correctly in the Windows Shell) whilst still using your legacy resource format and API to package and locate resources.</span></span> 

**<span data-ttu-id="d0d0e-166">Phase 2: Verwenden von MRT, um Ressourcen zu identifizieren und zu suchen</span><span class="sxs-lookup"><span data-stu-id="d0d0e-166">Phase 2: Use MRT to identify and locate resources</span></span>**

<span data-ttu-id="d0d0e-167">In diesem Abschnitt wird beschrieben, wie Sie Ihren Anwendungscode (und gegebenenfalls das Ressourcenlayout) so ändern, dass eine Suche von Ressourcen mithilfe von MRT möglich ist, während noch Ihre vorhandenen Ressourcenformate und Ihre älteren APIs verwendet werden, um die Ressourcen zu laden und zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-167">This section outlines how to modify your application code (and possibly resource layout) to locate resources using MRT, whilst still using your existing resource formats and APIs to load and consume the resources.</span></span> 

**<span data-ttu-id="d0d0e-168">Phase 3: Erstellen von Ressourcenpaketen</span><span class="sxs-lookup"><span data-stu-id="d0d0e-168">Phase 3: Build resource packs</span></span>**

<span data-ttu-id="d0d0e-169">In diesem Abschnitt werden die endgültigen Änderungen beschrieben, die erforderlich sind, um Ihre Ressourcen in separate *Ressourcenpakete* zu teilen, wodurch die Größe des Downloads (und der Installation) Ihrer App verringert wird.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-169">This section outlines the final changes needed to separate your resources into separate *resource packs*, minimizing the download (and install) size of your app.</span></span>

### <a name="not-covered-in-this-document"></a><span data-ttu-id="d0d0e-170">In diesem Dokument nicht behandelt</span><span class="sxs-lookup"><span data-stu-id="d0d0e-170">Not covered in this document</span></span>

<span data-ttu-id="d0d0e-171">Nach Abschluss der oben beschriebenen Phasen 0 bis 3 verfügen Sie über ein „Anwendungsbündel”, das an den Microsoft Store übermittelt werden kann und das den Download- und Installationsumfang für Benutzer verringert, indem die nicht benötigten Ressourcen ausgelassen werden (z.B. nicht verwendete Sprachen).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-171">After completing Phases 0-3 above, you will have an application "bundle" that can be submitted to the Microsoft Store and that will minimize the download & install size for users by omitting the resources they don't need (eg, languages they don't speak).</span></span> <span data-ttu-id="d0d0e-172">Weitere Verbesserungen hinsichtlich Größe der Anwendung und Funktionen können über einen letzten Schritt vorgenommen werden.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-172">Further improvements in application size and functionality can be made by taking one final step.</span></span> 

**<span data-ttu-id="d0d0e-173">Phase 4: Migrieren von MRT-Ressourcenformaten und APIs</span><span class="sxs-lookup"><span data-stu-id="d0d0e-173">Phase 4: Migrate to MRT resource formats and APIs</span></span>**

<span data-ttu-id="d0d0e-174">Diese Phase kann in diesem Dokument nicht behandelt werden. Sie umfasst das Übertragen Ihrer Ressourcen (insbesondere Zeichenfolgen) von älteren Formate wie beispielsweise MUI DLLs oder.NET-Ressourcenassemblys in PRI-Dateien.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-174">This phase is beyond the scope of this document; it entails moving your resources (particularly strings) from legacy formats such as MUI DLLs or .NET resource assemblies into PRI files.</span></span> <span data-ttu-id="d0d0e-175">Dies kann zu einer weiteren Platzeinsparung hinsichtlich der Größen für den Download und die Installation führen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-175">This can lead to further space savings for download & install sizes.</span></span> <span data-ttu-id="d0d0e-176">Es ermöglicht darüber hinaus die Verwendung weiterer MRT-Features, z.B. das Verringern der Größen für den Download und die Installation von Bilddateien auf Grundlage eines Skalierungsfaktors, Barrierefreiheiteinstellungen usw.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-176">It also allows use of other MRT features such as minimizing the download and install of image files by based on scale factor, accessibility settings, and so on.</span></span>

- - -

## <a name="phase-0-build-an-application-package"></a><span data-ttu-id="d0d0e-177">Phase 0: Erstellen eines Anwendungspakets</span><span class="sxs-lookup"><span data-stu-id="d0d0e-177">Phase 0: Build an application package</span></span>

<span data-ttu-id="d0d0e-178">Bevor Sie Änderungen an den Ressourcen Ihrer Anwendung vornehmen, müssen Sie zunächst Ihre aktuelle Paketerstellungs- und Installationstechnologie durch die standardmäßige UWP-Paketerstellungs und Bereitstellungstechnologie ersetzen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-178">Before you make any changes to your application's resources, you must first replace your current packaging and installation technology with the standard UWP packaging and deployment technology.</span></span> <span data-ttu-id="d0d0e-179">Hierfür gibt es drei Möglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-179">There are three ways to do this:</span></span>

0. <span data-ttu-id="d0d0e-180">Wenn Sie über eine große Desktopanwendung mit einem komplexen Installationsprogramm verfügen oder viele Erweiterungspunkte für das Betriebssystem verwenden, können Sie das Tool Desktop App Converter verwenden, um das Layout der UWP-Datei und die Manifestinformationen aus dem vorhandenen App-Installationsprogramm (z.B. eine MSI-Datei) zu generieren.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-180">If you have a large Desktop application with a complex installer or you utilize lots of OS extensibility points, you can use the Desktop App Converter tool to generate the UWP file layout and manifest information from your existing app installer (eg, an MSI)</span></span>
0. <span data-ttu-id="d0d0e-181">Wenn Sie über eine kleinere Desktopanwendung mit relativ wenigen Dateien oder einem einfachen Installationsprogramm und keinen Hooks für die Erweiterbarkeit verfügen, können Sie das Dateilayout und die Manifestinformationen manuell erstellen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-181">If you have a smaller Desktop application with relatively few files or a simple installer and no extensibility hooks, you can create the file layout and manifest information manually</span></span>
0. <span data-ttu-id="d0d0e-182">Wenn Sie eine Neuerstellung aus der Quelle vornehmen und Ihre App so aktualisieren möchten, dass sie eine „reine” UWP-Anwendung ist, können Sie ein neues Projekt in Visual Studio erstellen und die IDE einen Großteil der Arbeit durchführen lassen</span><span class="sxs-lookup"><span data-stu-id="d0d0e-182">If you're rebuilding from source and want to update your app to be a "pure" UWP application, you can create a new project in Visual Studio and rely on the IDE to do much of the work for you</span></span>

<span data-ttu-id="d0d0e-183">Wenn Sie den [Desktop App Converter](https://aka.ms/converter) verwenden möchten, können Sie im [Thema **Desktop-zu-UWP-Brücke: Desktop App Converter** auf MSDN](https://aka.ms/converterdocs) weitere Informationen zum Konvertierungsprozess finden.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-183">If you want to use the [Desktop App Converter](https://aka.ms/converter), please refer to [the **Desktop to UWP Bridge: Desktop App Converter** topic on MSDN](https://aka.ms/converterdocs) for more information on the conversion process.</span></span> <span data-ttu-id="d0d0e-184">Einen vollständigen Satz an Desktop Converter-Beispielen finden Sie im [GitHub-Repository **Desktop-Brücke-zu-UWP – Beispiele**](https://github.com/Microsoft/DesktopBridgeToUWP-Samples).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-184">A complete set of Desktop Converter samples can be found on [the **Desktop Bridge to UWP samples** GitHub repo](https://github.com/Microsoft/DesktopBridgeToUWP-Samples).</span></span>

<span data-ttu-id="d0d0e-185">Wenn Sie das Paket manuell erstellen möchten, müssen Sie eine Verzeichnisstruktur erstellen, die alle Dateien Ihrer Anwendung (ausführbare Dateien und Inhalte, aber keinen Quellcode) und eine `AppXManifest.xml`-Datei enthält.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-185">If you want to manually create the package, you will need to create a directory structure that includes all your application's files (executables and content, but not source code) and an `AppXManifest.xml` file.</span></span> <span data-ttu-id="d0d0e-186">Ein Beispiel finden Sie im [GitHub-Beispiel **Hello, World**](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/blob/master/Samples/HelloWorldSample/CentennialPackage/AppxManifest.xml); eine einfache `AppXManifest.xml` -Datei, die die ausführbare Desktopdatei mit dem Namen `ContosoDemo.exe` ausführt, würde folgendermaßen aussehen, wobei der <span style="background-color: yellow">hervorgehobene Text</span> mit Ihren eigenen Werte ersetzt würde:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-186">An example can be found in [the **Hello, World** GitHub sample](https://github.com/Microsoft/DesktopBridgeToUWP-Samples/blob/master/Samples/HelloWorldSample/CentennialPackage/AppxManifest.xml), but a basic `AppXManifest.xml` file that runs the Desktop executable named `ContosoDemo.exe` is as follows, where the <span style="background-color: yellow">highlighted text</span> would be replaced by your own values:</span></span>

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

<span data-ttu-id="d0d0e-187">Weitere Informationen zur Datei `AppXManifest.xml` und dem Paketlayout finden Sie im [Thema **App-Paketmanifest** auf MSDN](https://msdn.microsoft.com/en-us/library/windows/apps/br211474.aspx).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-187">For more information about the `AppXManifest.xml` file and package layout, see [the **App package manifest** topic on MSDN](https://msdn.microsoft.com/en-us/library/windows/apps/br211474.aspx).</span></span>

<span data-ttu-id="d0d0e-188">Wenn Sie zum Erstellen eines neuen Projekts und zum Migrieren des vorhandenen Codes Visual Studio verwenden, können Sie weitere Informationen in der [MSDN-Dokumentation für die Erstellung eines neuen UWP-Projekts](https://msdn.microsoft.com/en-us/windows/uwp/get-started/create-a-hello-world-app-xaml-universal) finden.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-188">Finally, if you're using Visual Studio to create a new project and migrate your existing code across, see [the MSDN documentation for building a new UWP project](https://msdn.microsoft.com/en-us/windows/uwp/get-started/create-a-hello-world-app-xaml-universal).</span></span> <span data-ttu-id="d0d0e-189">Sie können den vorhandenen Code in das neue Projekt einfügen, Sie müssen aber wahrscheinlich noch erhebliche Änderungen am Code vornehmen (insbesondere in der Benutzeroberfläche), damit die App als „reine” UWP-App ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-189">You can include your existing code into the new project, but you will likely have to make significant code changes (particularly in the user interface) in order to run as a "pure" UWP.</span></span> <span data-ttu-id="d0d0e-190">Diese Änderungen werden in diesem Dokument nicht behandelt.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-190">These changes are outside the scope of this document.</span></span>

***

## <a name="phase-1-localize-the-application-manifest"></a><span data-ttu-id="d0d0e-191">Phase 1: Lokalisieren des Anwendungsmanifests</span><span class="sxs-lookup"><span data-stu-id="d0d0e-191">Phase 1: Localize the application manifest</span></span>

### <a name="step-11-update-strings--assets-in-the-appxmanifest"></a><span data-ttu-id="d0d0e-192">Schritt1.1: Aktualisieren von Zeichenfolgen und Ressourcen in AppXManifest</span><span class="sxs-lookup"><span data-stu-id="d0d0e-192">Step 1.1: Update strings & assets in the AppXManifest</span></span>

<span data-ttu-id="d0d0e-193">In Phase 0 haben Sie eine einfache `AppXManifest.xml`-Datei für Ihre Anwendung erstellt (basierend auf dem Converter bereitgestellten Werten, die aus der MSI-Datei extrahiert oder manuell in das Paketmanifest eingegeben wurden). Diese enthält jedoch weder lokalisierte Informationen noch werden zusätzliche Features wie Ressourcen für Startkacheln mit hoher Auflösung usw. unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-193">In Phase 0 you created a basic `AppXManifest.xml` file for your application (based on values provided to the converter, extracted from the MSI, or manually entered into the manifest) but it will not contain localized information, nor will it support additional features like high-resolution Start tile assets, etc.</span></span> 

<span data-ttu-id="d0d0e-194">Um sicherzustellen, dass der Name und die Beschreibung Ihrer Anwendung richtig lokalisiert sind, müssen Sie einige Ressourcen in einer Reihe von Ressourcendateien definieren und AppX-Manifest aktualisieren, damit diese Datei auf sie verweist.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-194">To ensure your application's name and description are correctly localized, you must define some resources in a set of resource files, and update the AppX Manifest to reference them.</span></span>

**<span data-ttu-id="d0d0e-195">Erstellen eine Standardressourcendatei</span><span class="sxs-lookup"><span data-stu-id="d0d0e-195">Creating a default resource file</span></span>**

<span data-ttu-id="d0d0e-196">Der erste Schritt ist das Erstellen einer Standardressourcendatei in der Standardsprache (z.B. Englisch (USA)).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-196">The first step is to create a default resource file in your default language (eg, US English).</span></span> <span data-ttu-id="d0d0e-197">Sie können dies entweder manuell mit einem Text-Editor oder über den Ressourcen-Designer in Visual Studio vornehmen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-197">You can do this either manually with a text editor, or via the Resource Designer in Visual Studio.</span></span>

<span data-ttu-id="d0d0e-198">Wenn Sie die Ressourcen manuell erstellen möchten:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-198">If you want to create the resources manually:</span></span>

0. <span data-ttu-id="d0d0e-199">Erstellen Sie eine XML-Datei mit dem Namen `resources.resw`, und legen Sie sie in einem `Strings\en-us`-Unterordner Ihres Projekts ab.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-199">Create an XML file named `resources.resw` and place it in a `Strings\en-us` subfolder of your project.</span></span> 
 * <span data-ttu-id="d0d0e-200">Verwenden Sie den entsprechenden Code BCP-47, wenn die Standardsprache nicht Englisch (USA) ist.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-200">Use the appropriate BCP-47 code if your default language is not US English</span></span> 
0. <span data-ttu-id="d0d0e-201">Fügen Sie in der XML-Datei den folgenden Inhalt hinzu. Ersetzten Sie dabei den <span style="background-color: yellow">hervorgehobenen Text</span> durch den entsprechenden Text in der Standardsprache Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-201">In the XML file, add the following content, where the <span style="background-color: yellow">highlighted text</span> is replaced with the appropriate text for your app, in your default language.</span></span>

<span data-ttu-id="d0d0e-202">**Hinweis:** Es gibt Einschränkungen bezüglich der Länge einiger dieser Strings.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-202">**Note** There are restrictions on the lengths of some of these strings.</span></span> <span data-ttu-id="d0d0e-203">Weitere Informationen finden Sie unter [VisualElements](/uwp/schemas/appxpackage/appxmanifestschema/element-visualelements?branch=live).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-203">For more info, see [VisualElements](/uwp/schemas/appxpackage/appxmanifestschema/element-visualelements?branch=live).</span></span>

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

<span data-ttu-id="d0d0e-204">Wenn Sie den Designer in Visual Studio verwenden möchten:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-204">If you want to use the designer in Visual Studio:</span></span>

0. <span data-ttu-id="d0d0e-205">Erstellen Sie den Ordner `Strings\en-us` (oder nach Bedarf eine andere Sprache ) in Ihrem Projekt, und fügen Sie ein **Neues Element** zum Stammordner des Projekts hinzu. Verwenden Sie dabei den Standardnamen</span><span class="sxs-lookup"><span data-stu-id="d0d0e-205">Create the `Strings\en-us` folder (or other language as appropriate) in your project and add a **New Item** to the root folder of your project, using the default name of</span></span> `resources.resw`
 * <span data-ttu-id="d0d0e-206">Wählen Sie **Ressourcendatei (.resw)** und nicht **Ressourcenverzeichnis** – ein Ressourcenverzeichnis ist eine Datei, die von XAML-Anwendungen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-206">Be sure to choose **Resources File (.resw)** and not **Resource Dictionary** - a Resource Dictionary is a file used by XAML applications</span></span>
0. <span data-ttu-id="d0d0e-207">Geben Sie im Designer die folgenden Zeichenfolgen ein (verwenden Sie dieselben `Names`, ersetzen Sie die `Values` jedoch mit dem entsprechenden Text für Ihre Anwendung):</span><span class="sxs-lookup"><span data-stu-id="d0d0e-207">Using the designer, enter the following strings (use the same `Names` but replace the `Values` with the appropriate text for your application):</span></span>

<img src="images\editing-resources-resw.png"/>

<span data-ttu-id="d0d0e-208">Hinweis: Wenn Sie mit dem Visual Studio-Designer starten, können Sie die XML-Datei jederzeit durch Drücken von `F7` bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-208">Note: if you start with the Visual Studio designer, you can always edit the XML directly by pressing `F7`.</span></span> <span data-ttu-id="d0d0e-209">Wenn Sie jedoch mit einer kleinen XML-Datei starten, *erkennt der Designer die Datei nicht*, weil viele zusätzliche Metadaten fehlen. Dies lässt sich durch Kopieren der XSD-Textbausteininformationen aus einer mit dem Designer erstellten Datei in die manuell bearbeitete XML-Datei beheben.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-209">But if you start with a minimal XML file, *the designer will not recognize the file* because it's missing a lot of additional metadata; you can fix this by copying the boilerplate XSD information from a designer-generated file into your hand-edited XML file.</span></span> 

**<span data-ttu-id="d0d0e-210">Aktualisieren des Manifests, um auf die Ressourcen zu verweisen</span><span class="sxs-lookup"><span data-stu-id="d0d0e-210">Update the manifest to reference the resources</span></span>**

<span data-ttu-id="d0d0e-211">Wenn Sie die Werte in der `.resw` -Datei definiert haben, besteht der nächste Schritt darin, das Manifest zu aktualisieren, um auf die Ressourcenzeichenfolgen zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-211">Once you have the values defined in the `.resw` file, the next step is to update the manifest to reference the resource strings.</span></span> <span data-ttu-id="d0d0e-212">Auch in diesem Fall können Sie eine XML-Datei direkt bearbeiten oder dies durch den Manifest-Designer von Visual Studio vornehmen lassen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-212">Again, you can edit an XML file directly, or rely on the Visual Studio Manifest Designer.</span></span>

<span data-ttu-id="d0d0e-213">Wenn Sie XML-Code direkt bearbeiten, öffnen Sie die Datei `AppxManifest.xml`, und nehmen Sie die folgenden Änderungen an den <span style="background-color: lightgreen">hervorgehoben Werten</span> vor – verwenden Sie *genau* diesen Text und keinen für Ihre Anwendung spezifischen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-213">If you are editing XML directly, open the `AppxManifest.xml` file and make the following changes to the <span style="background-color: lightgreen">highlighted values</span> - use this *exact* text, not text specific to your application.</span></span> <span data-ttu-id="d0d0e-214">Es besteht keine Notwendigkeit, genau diese Ressourcennamen zu verwenden.&mdash;Sie können eigene Ressourcennamen verwenden&mdash;, die jedoch genau mit den Angaben in der Datei `.resw` übereinstimmen müssen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-214">There is no requirement to use these exact resource names&mdash;you can choose your own&mdash;but whatever you choose must exactly match whatever is in the `.resw` file.</span></span> <span data-ttu-id="d0d0e-215">Diese Namen sollten den `Names` entsprechen, die Sie in der `.resw`-Datei erstellt haben, und als Präfix das `ms-resource:`-Schema und den `Resources/`-Namespace aufweisen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-215">These names should match the `Names` you created in the `.resw` file, prefixed with the `ms-resource:` scheme and the `Resources/` namespace.</span></span> 

*<span data-ttu-id="d0d0e-216">Hinweis: Viele Elemente des Manifests wurden in diesem Codeausschnitt ausgelassen – löschen Sie nichts!</span><span class="sxs-lookup"><span data-stu-id="d0d0e-216">Note: many elements of the manifest have been omitted from this snippet - do not delete anything!</span></span>*

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

<span data-ttu-id="d0d0e-217">Wenn Sie den Manifest-Designer von Visual Studio verwenden, öffnen Sie die Datei `Package.appxmanifest`, und ändern Sie die <span style="background-color: lightgreen">hervorgehoben Werte</span> auf der Registerkarte `Application` und der Registerkarte `Packaging`:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-217">If you are using the Visual Studio manifest designer, open the `Package.appxmanifest` file and change the <span style="background-color: lightgreen">highlighted values</span> values in the `Application` tab and the `Packaging` tab:</span></span>

<img src="images\editing-application-info.png"/>
<img src="images\editing-packaging-info.png"/>

### <a name="step-12-build-pri-file-make-an-appx-package-and-verify-its-working"></a><span data-ttu-id="d0d0e-218">Schritt1.2: Erstellen einer PRI-Datei, Erstellen eines AppX-Pakets und Sicherstellen, dass es funktioniert</span><span class="sxs-lookup"><span data-stu-id="d0d0e-218">Step 1.2: Build PRI file, make an AppX package, and verify it's working</span></span>

<span data-ttu-id="d0d0e-219">Sie sollten jetzt in der Lage sein, die `.pri`-Datei zu erstellen und die Anwendung bereitzustellen, um sicherzustellen, dass die richtigen Informationen (in Ihrer Standardsprache) im Startmenü angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-219">You should now be able to build the `.pri` file and deploy the application to verify that the correct information (in your default language) is appearing in the Start Menu.</span></span> 

<span data-ttu-id="d0d0e-220">Wenn Sie in Visual Studio erstellen, drücken Sie einfach `Ctrl+Shift+B`, um das Projekt zu erstellen, und klicken Sie dann mit der rechten Maustaste auf das Projekt, und wählen Sie im Kontextmenü `Deploy` aus.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-220">If you're building in Visual Studio, simply press `Ctrl+Shift+B` to build the project and then right-click on the project and choose `Deploy` from the context menu.</span></span> 

<span data-ttu-id="d0d0e-221">Führen Sie bei einer manuellen Erstellung die folgenden Schritte aus, um eine Konfigurationsdatei für `MakePRI`-Tool zu erstellen und die `.pri`-Datei selbst zu generieren (weitere Informationen finden Sie im [Thema **Manuelles Verpacken von Apps** auf MSDN](https://docs.microsoft.com/en-us/windows/uwp/packaging/manual-packaging-root)):</span><span class="sxs-lookup"><span data-stu-id="d0d0e-221">If you're building manually, follow these steps to create a configuration file for `MakePRI` tool and to generate the `.pri` file itself (more information can be found in [the **Manual app packaging** topic on MSDN](https://docs.microsoft.com/en-us/windows/uwp/packaging/manual-packaging-root)):</span></span>

0. <span data-ttu-id="d0d0e-222">Öffnen Sie eine Developer-Eingabeaufforderung über den Ordner `Visual Studio 2015` im Startmenü.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-222">Open a developer command prompt from the `Visual Studio 2015` folder in the Start menu</span></span>
0. <span data-ttu-id="d0d0e-223">Wechseln Sie zum Stammverzeichnis des Projekts (d.h. zu demjenigen, dass die Datei `AppxManifest.xml` und den Ordner `Strings` enthält).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-223">Switch to the project root directory (the one that contains the `AppxManifest.xml` file and the `Strings` folder)</span></span>
0. <span data-ttu-id="d0d0e-224">Geben Sie den folgenden Befehl ein, und ersetzen Sie dabei „contoso_demo.xml” mit einem für Ihr Projekt geeigneten Namen und „en-US” mit der Standardsprache Ihrer App (oder lassen Sie es nach Bedarf auf en-US).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-224">Type the following command, replacing "contoso_demo.xml" with a name suitable for your project, and "en-US" with the default language of your app (or keep it en-US if applicable).</span></span> <span data-ttu-id="d0d0e-225">Beachten Sie, dass die XML-Datei im übergeordneten Verzeichnis (**nicht** im Projektverzeichnis) erstellt wird, da sie nicht Teil der Anwendung ist. (Sie können ein beliebiges anderes Verzeichnis auswählen, müssen dies aber in zukünftigen Befehlen verwenden.)</span><span class="sxs-lookup"><span data-stu-id="d0d0e-225">Note the xml file is created in the parent directory (**not** in the project directory) since it's not part of the application (you can choose any other directory you want, but be sure to substitute that in future commands).</span></span>

```CMD
    makepri createconfig /cf ..\contoso_demo.xml /dq en-US /pv 10.0 /o
```

0. <span data-ttu-id="d0d0e-226">Sie können `makepri createconfig /?` eingeben, um zu sehen, was die einzelnen Parameter bedeuten. Kurz zusammengefasst:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-226">You can type `makepri createconfig /?` to see what each parameter does, but in summary:</span></span>
 * `/cf` <span data-ttu-id="d0d0e-227">legt den Konfigurationsdateinamen fest (die Ausgabe dieses Befehls)</span><span class="sxs-lookup"><span data-stu-id="d0d0e-227">sets the Configuration Filename (the output of this command)</span></span>
 * `/dq` <span data-ttu-id="d0d0e-228">legt die Standardqualifizierer fest, in diesem Fall die Sprache</span><span class="sxs-lookup"><span data-stu-id="d0d0e-228">sets the Default Qualifiers, in this case the language</span></span> `en-US`
 * `/pv` <span data-ttu-id="d0d0e-229">legt die Plattformversion fest, in diesem Fall Windows10</span><span class="sxs-lookup"><span data-stu-id="d0d0e-229">sets the Platform Version, in this case Windows 10</span></span>
 * `/o` <span data-ttu-id="d0d0e-230">legt ein Überschreiben der Ausgabedatei fest, wenn vorhanden</span><span class="sxs-lookup"><span data-stu-id="d0d0e-230">sets it to Overwrite the output file if it exists</span></span>
0. <span data-ttu-id="d0d0e-231">Sie verfügen jetzt über eine Konfigurationsdatei. Führen Sie `MakePRI` erneut aus, um auf der Festplatte tatsächlich nach Ressourcen zu suchen und diese in einer PRI-Datei zu verpacken.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-231">Now you have a configuration file, run `MakePRI` again to actually search the disk for resources and package them into a PRI file.</span></span> <span data-ttu-id="d0d0e-232">Ersetzen Sie „contoso_demop.xml” mit dem XML-Dateinamen, den Sie im vorherigen Schritt verwendet haben, und legen Sie das übergeordnete Verzeichnis für Eingabe und Ausgabe fest:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-232">Replace "contoso_demop.xml" with the XML filename you used in the previous step, and be sure to specify the parent directory for both input and output:</span></span> 

    `makepri new /pr . /cf ..\contoso_demo.xml /of ..\resources.pri /mf AppX /o`
0. <span data-ttu-id="d0d0e-233">Sie können `makepri new /?` eingeben, um zu sehen, was die einzelnen Parameter bedeuten. Kurz zusammengefasst:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-233">You can type `makepri new /?` to see what each parameter does, but in a nutshell:</span></span>
 * `/pr` <span data-ttu-id="d0d0e-234">legt den Projektstamm fest (in diesem Fall das aktuelle Verzeichnis)</span><span class="sxs-lookup"><span data-stu-id="d0d0e-234">sets the Project Root (in this case, the current directory)</span></span>
 * `/cf` <span data-ttu-id="d0d0e-235">legt den Konfigurationsdateinamen fest, der im vorherigen Schritt erstellt wurde</span><span class="sxs-lookup"><span data-stu-id="d0d0e-235">sets the Configuration Filename, created in the previous step</span></span>
 * `/of` <span data-ttu-id="d0d0e-236">legt die Ausgabedatei fest</span><span class="sxs-lookup"><span data-stu-id="d0d0e-236">sets the Output File</span></span> 
 * `/mf` <span data-ttu-id="d0d0e-237">erstellt eine Zuordnungsdatei (sodass wir Dateien im Paket in einem späteren Schritt ausschließen können)</span><span class="sxs-lookup"><span data-stu-id="d0d0e-237">creates a Mapping File (so we can exclude files in the package in a later step)</span></span>
 * `/o` <span data-ttu-id="d0d0e-238">legt ein Überschreiben der Ausgabedatei fest, wenn vorhanden</span><span class="sxs-lookup"><span data-stu-id="d0d0e-238">sets it to Overwrite the output file if it exists</span></span>
0. <span data-ttu-id="d0d0e-239">Sie verfügen jetzt über eine `.pri`-Datei mit den Standardsprachressourcen (z.B. en-US).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-239">Now you have a `.pri` file with the default language resources (eg, en-US).</span></span> <span data-ttu-id="d0d0e-240">Um sicherzustellen, dass es ordnungsgemäß funktioniert hat, können Sie den folgenden Befehl ausführen:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-240">To verify that it worked correctly, you can run the following command:</span></span>

    `makepri dump /if ..\resources.pri /of ..\resources /o`
0. <span data-ttu-id="d0d0e-241">Sie können `makepri dump /?` eingeben, um zu sehen, was die einzelnen Parameter bedeuten. Kurz zusammengefasst:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-241">You can type `makepri dump /?` to see what each parameter does, but in a nutshell:</span></span>
 * `/if` <span data-ttu-id="d0d0e-242">legt den Eingabedateinamen fest</span><span class="sxs-lookup"><span data-stu-id="d0d0e-242">sets the Input Filename</span></span> 
 * `/of` <span data-ttu-id="d0d0e-243">legt den Ausgabedateinamen fest (`.xml` wird automatisch angefügt)</span><span class="sxs-lookup"><span data-stu-id="d0d0e-243">sets the Output Filename (`.xml` will be appended automatically)</span></span>
 * `/o` <span data-ttu-id="d0d0e-244">legt ein Überschreiben der Ausgabedatei fest, wenn vorhanden</span><span class="sxs-lookup"><span data-stu-id="d0d0e-244">sets it to Overwrite the output file if it exists</span></span>
0. <span data-ttu-id="d0d0e-245">Zuletzt können Sie `..\resources.xml` in einem Text-Editor öffnen und überprüfen, ob Ihre `<NamedResource>`-Werte (z.B. `ApplicationDescription` und `PublisherDisplayName`) zusammen mit den `<Candidate>`-Werten für die ausgewählte Standardsprache aufgeführt werden (am Anfang der Datei befinden sich auch weitere Inhalte; diese können Sie vorerst ignorieren).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-245">Finally, you can open `..\resources.xml` in a text editor and verify it lists your `<NamedResource>` values (like `ApplicationDescription` and `PublisherDisplayName`) along with `<Candidate>` values for your chosen default language (there will be other content in the beginning of the file; ignore that for now).</span></span>

<span data-ttu-id="d0d0e-246">Wenn Sie möchten, können Sie die Zuordnungsdatei `..\resources.map.txt` öffnen, um zu überprüfen, ob sie die für Ihr Projekt benötigten Dateien enthält (einschließlich der PRI-Datei, die nicht Teil des Projektverzeichnisses ist).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-246">If you like, you can open the mapping file `..\resources.map.txt` to verify it contains the files needed for your project (including the PRI file, which is not part of the project's directory).</span></span> <span data-ttu-id="d0d0e-247">Besonders wichtig ist, dass die Zuordnungsdatei *keinen* Verweis auf Ihre `resources.resw`-Datei enthält, da der Inhalt dieser Datei bereits in die PRI-Datei eingebettet wurde.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-247">Importantly, the mapping file will *not* include a reference to your `resources.resw` file because the contents of that file have already been embedded in the PRI file.</span></span> <span data-ttu-id="d0d0e-248">Sie enthält jedoch andere Ressourcen wie die Dateinamen Ihrer Bilder.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-248">It will, however, contain other resources like the filenames of your images.</span></span>

**<span data-ttu-id="d0d0e-249">Erstellen und Signieren des Pakets</span><span class="sxs-lookup"><span data-stu-id="d0d0e-249">Building and signing the package</span></span>**

<span data-ttu-id="d0d0e-250">Nachdem die PRI-Datei jetzt erstellt wurde, können Sie das Paket erstellen und signieren:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-250">Now the PRI file is built, you can build and sign the package:</span></span>

0. <span data-ttu-id="d0d0e-251">Um das App-Paket zu erstellen, führen Sie den folgenden Befehl aus, und ersetzen Sie dabei `contoso_demo.appx` mit dem Namen der AppX Datei, die Sie erstellen möchten. Wählen Sie ein anderes Verzeichnis für die `.AppX`-Datei (in diesem Beispiel wird das übergeordnete Verzeichnis verwendet; sie können jedes beliebige Verzeichnis verwenden, jedoch **nicht** das Projektverzeichnis):</span><span class="sxs-lookup"><span data-stu-id="d0d0e-251">To create the app package, run the following command replacing `contoso_demo.appx` with the name of the AppX file you want to create and making sure to choose a different directory for the `.AppX` file (this sample uses the parent directory; it can be anywhere but should **not** be the project directory):</span></span>

    `makeappx pack /m AppXManifest.xml /f ..\resources.map.txt /p ..\contoso_demo.appx /o`
0. <span data-ttu-id="d0d0e-252">Sie können `makeappx pack /?` eingeben, um zu sehen, was die einzelnen Parameter bedeuten. Kurz zusammengefasst:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-252">You can type `makeappx pack /?` to see what each parameter does, but in a nutshell:</span></span>
 * `/m` <span data-ttu-id="d0d0e-253">legt die zu verwendende Manifestdatei fest</span><span class="sxs-lookup"><span data-stu-id="d0d0e-253">sets the Manifest file to use</span></span>
 * `/f` <span data-ttu-id="d0d0e-254">legt die zu verwendende Zuordnungsdatei fest (die im vorherigen Schritt erstellt wurde)</span><span class="sxs-lookup"><span data-stu-id="d0d0e-254">sets the mapping File to use (created in the previous step)</span></span> 
 * `/p` <span data-ttu-id="d0d0e-255">legt den Namen des Ausgabepakets fest</span><span class="sxs-lookup"><span data-stu-id="d0d0e-255">sets the output Package name</span></span>
 * `/o` <span data-ttu-id="d0d0e-256">legt ein Überschreiben der Ausgabedatei fest, wenn vorhanden</span><span class="sxs-lookup"><span data-stu-id="d0d0e-256">sets it to Overwrite the output file if it exists</span></span>
0. <span data-ttu-id="d0d0e-257">Wenn das Paket erstellt wurde, muss es signiert werden.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-257">Once the package is created, it must be signed.</span></span> <span data-ttu-id="d0d0e-258">Die einfachste Methode zum Abrufen eines Signaturzertifikats ist, erstellen ein leeres universelles Windows-Projekt in Visual Studio, und Kopieren der `.pfx` -Datei erstellt, aber Sie können manuell mit Erstellen der `MakeCert` und `Pvk2Pfx` gemäß der Verwaltungsdienstprogramme für [der **So erstellen Sie ein app-Paket, das Signaturzertifikat** Thema auf MSDN] (https://msdn.microsoft.com/en-us/library/windows/desktop/jj835832(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-258">The easiest way to get a signing certificate is by creating an empty Universal Windows project in Visual Studio and copying the `.pfx` file it creates, but you can create one manually using the `MakeCert` and `Pvk2Pfx` utilities as described in [the **How to create an app package signing certificate** topic on MSDN] (https://msdn.microsoft.com/en-us/library/windows/desktop/jj835832(v=vs.85).aspx).</span></span> 
 * <span data-ttu-id="d0d0e-259">**Wichtig:** Wenn Sie ein Signaturzertifikat manuell erstellen, stellen Sie sicher, dass Sie die Dateien in einem anderen Verzeichnis als Ihr Quellprojekt oder die Paketquelle ablegen, andernfalls wird es möglicherweise in das Paket eingefügt, einschließlich des privaten Schlüssels!</span><span class="sxs-lookup"><span data-stu-id="d0d0e-259">**Important:** If you manually create a signing certificate, make sure you place the files in a different directory than your source project or your package source, otherwise it might get included as part of the package, including the private key!</span></span>
0. <span data-ttu-id="d0d0e-260">Verwenden Sie zum Signieren des Pakets den folgenden Befehl.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-260">To sign the package, use the following command.</span></span> <span data-ttu-id="d0d0e-261">Beachten Sie, dass der im Element `Identity` der Datei `AppxManifest.xml` angegebene `Publisher` mit dem `Subject` des Zertifikats übereinstimmen muss (hierbei handelt es sich **nicht** um das Element `<PublisherDisplayName>`; dieses ist der lokalisierte Anzeigename, der den Benutzern angezeigt wird).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-261">Note that the `Publisher` specified in the `Identity` element of the `AppxManifest.xml` must match the `Subject` of the certificate (this is **not** the `<PublisherDisplayName>` element, which is the localized display name to show to users).</span></span> <span data-ttu-id="d0d0e-262">Ersetzen Sie wie gewohnt die `contoso_demo...`-Dateinamen mit den Namen für Ihr Projekt, und (**sehr wichtig**) stellen Sie sicher, dass die `.pfx`-Datei sich nicht im aktuellen Verzeichnis befindet (andernfalls wäre sie als Teil Ihres Pakets erstellt worden, einschließlich des privaten Signaturschlüssels!):</span><span class="sxs-lookup"><span data-stu-id="d0d0e-262">As usual, replace the `contoso_demo...` filenames with the names appropriate for your project, and (**very important**) make sure the `.pfx` file is not in the current directory (otherwise it would have been created as part of your package, including the private signing key!):</span></span>

    `signtool sign /fd SHA256 /a /f ..\contoso_demo_key.pfx ..\contoso_demo.appx`
0. <span data-ttu-id="d0d0e-263">Sie können `signtool sign /?` eingeben, um zu sehen, was die einzelnen Parameter bedeuten. Kurz zusammengefasst:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-263">You can type `signtool sign /?` to see what each parameter does, but in a nutshell:</span></span>
 * `/fd` <span data-ttu-id="d0d0e-264">legt den Datei-Digestalgorithmus fest (SHA256 ist die Standardeinstellung für AppX)</span><span class="sxs-lookup"><span data-stu-id="d0d0e-264">sets the File Digest algorithm (SHA256 is the default for AppX)</span></span>
 * `/a` <span data-ttu-id="d0d0e-265">wählt automatisch das beste Zertifikat</span><span class="sxs-lookup"><span data-stu-id="d0d0e-265">will Automatically select the best certificate</span></span>
 * `/f` <span data-ttu-id="d0d0e-266">legt die Eingabedatei fest, die das Signaturzertifikat enthält</span><span class="sxs-lookup"><span data-stu-id="d0d0e-266">specifies the input File that contains the signing certificate</span></span>

<span data-ttu-id="d0d0e-267">Zuletzt können Sie auf die Datei `.appx` doppelklicken, um diese zu installieren. Wenn Sie lieber die Befehlszeile verwenden, können Sie eine PowerShell-Eingabeaufforderung öffnen, zum Verzeichnis mit dem Paket wechseln, und Folgendes eingeben (wobei Sie `contoso_demo.appx` mit Ihrem Paketnamen ersetzen müssen):</span><span class="sxs-lookup"><span data-stu-id="d0d0e-267">Finally, you can now double-click on the `.appx` file to install it, or if you prefer the command-line you can open a PowerShell prompt, change to the directory containing the package, and type the following (replacing `contoso_demo.appx` with your package name):</span></span>

```CMD
    add-appxpackage contoso_demo.appx
```

<span data-ttu-id="d0d0e-268">Wenn Sie Fehlermeldungen erhalten, dass das Zertifikat nicht als vertrauenswürdig eingestuft wird, stellen Sie sicher, dass es zum lokalen Speicher hinzugefügt wurde (**nicht** zum Benutzerspeicher).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-268">If you receive errors about the certificate not being trusted, make sure it is added to the machine store (**not** the user store).</span></span> <span data-ttu-id="d0d0e-269">Um das Zertifikat zum lokalen Speicher hinzufügen, können Sie entweder die Befehlszeile oder Windows Explorer verwenden.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-269">To add the certificate to the machine store, you can either use the command-line or Windows Explorer.</span></span>

<span data-ttu-id="d0d0e-270">Verwenden der Befehlszeile:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-270">To use the command-line:</span></span>

0. <span data-ttu-id="d0d0e-271">Führen Sie eine Visual Studio2015-Befehlszeile als Administrator aus.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-271">Run a Visual Studio 2015 command prompt as an Administrator.</span></span>
0. <span data-ttu-id="d0d0e-272">Wechseln Sie zu dem Verzeichnis mit der `.cer`-Datei (stellen Sie sicher, dass dies nicht das Verzeichnis Ihrer Quelle oder Ihres Projekts ist!)</span><span class="sxs-lookup"><span data-stu-id="d0d0e-272">Switch to the directory that contains the `.cer` file (remember to ensure this is outside of your source or project directories!)</span></span>
0. <span data-ttu-id="d0d0e-273">Geben Sie folgenden Befehl ein, und ersetzen Sie dabei `contoso_demo.cer` mit Ihrem Dateinamen:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-273">Type the following command, replacing `contoso_demo.cer` with your filename:</span></span>

    `certutil -addstore TrustedPeople contoso_demo.cer`
0. <span data-ttu-id="d0d0e-274">Sie können `certutil -addstore /?` ausführen, um zu sehen, was die einzelnen Parameter bedeuten. Kurz zusammengefasst:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-274">You can run `certutil -addstore /?` to see what each parameter does, but in a nutshell:</span></span>
 * `-addstore` <span data-ttu-id="d0d0e-275">fügt ein Zertifikat zu einem Zertifikatspeicher hinzu</span><span class="sxs-lookup"><span data-stu-id="d0d0e-275">adds a certificate to a certificate store</span></span>
 * `TrustedPeople` <span data-ttu-id="d0d0e-276">gibt den Speicher an, in dem das Zertifikat gespeichert wird</span><span class="sxs-lookup"><span data-stu-id="d0d0e-276">indicates the store into which the certificate is placed</span></span>

<span data-ttu-id="d0d0e-277">Verwenden von Windows Explorer:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-277">To use Windows Explorer:</span></span>

0. <span data-ttu-id="d0d0e-278">Navigieren Sie zum Ordner mit der `.pfx`-Datei</span><span class="sxs-lookup"><span data-stu-id="d0d0e-278">Navigate to the folder that contains the `.pfx` file</span></span>
0. <span data-ttu-id="d0d0e-279">Doppelklicken Sie auf die `.pfx`-Datei. Der **Zertifikatimport-Assistent** sollte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-279">Double-click on the `.pfx` file and the **Certicicate Import Wizard** should appear</span></span>
0. <span data-ttu-id="d0d0e-280">Wählen Sie `Local Machine`, und klicken Sie auf</span><span class="sxs-lookup"><span data-stu-id="d0d0e-280">Choose `Local Machine` and click</span></span> `Next`
0. <span data-ttu-id="d0d0e-281">Akzeptieren Sie die Benutzerkontensteuerung- Eingabeaufforderung für erhöhte Rechte für Administratoren, wenn diese angezeigt wird, und klicken Sie auf</span><span class="sxs-lookup"><span data-stu-id="d0d0e-281">Accept the User Account Control admin elevation prompt, if it appears, and click</span></span> `Next`
0. <span data-ttu-id="d0d0e-282">Geben Sie das Kennwort für den privaten Schlüssel ein, sofern vorhanden, und klicken Sie auf</span><span class="sxs-lookup"><span data-stu-id="d0d0e-282">Enter the password for the private key, if there is one, and click</span></span> `Next`
0. <span data-ttu-id="d0d0e-283">Wählen Sie</span><span class="sxs-lookup"><span data-stu-id="d0d0e-283">Select</span></span> `Place all certificates in the following store`
0. <span data-ttu-id="d0d0e-284">Klicken Sie auf `Browse`, und wählen Sie den Ordner `Trusted People` (**nicht** „Vertrauenswürdige Herausgeber”)</span><span class="sxs-lookup"><span data-stu-id="d0d0e-284">Click `Browse`, and choose the `Trusted People` folder (**not** "Trusted Publishers")</span></span>
0. <span data-ttu-id="d0d0e-285">Klicken Sie auf `Next` und dann auf</span><span class="sxs-lookup"><span data-stu-id="d0d0e-285">Click `Next` and then</span></span> `Finish`

<span data-ttu-id="d0d0e-286">Versuchen Sie nach dem Hinzufügen des Zertifikats zum `Trusted People`-Speicher erneut, das Paket zu installieren.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-286">After adding the certificate to the `Trusted People` store, try installing the package again.</span></span>

<span data-ttu-id="d0d0e-287">Ihre App sollte jetzt in der Liste „Alle Apps” im Startmenü angezeigt werden, mit den richtigen Informationen aus der Datei `.resw` / `.pri`.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-287">You should now see your app appear in the Start Menu's "All Apps" list, with the correct information from the `.resw` / `.pri` file.</span></span> <span data-ttu-id="d0d0e-288">Wenn Sie eine leere Zeichenfolge oder die Zeichenfolge `ms-resource:...` sehen, ist ein Fehler aufgetreten – überprüfen Sie Ihre Bearbeitungen, und stellen Sie sicher, dass sie richtig sind.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-288">If you see a blank string or the string `ms-resource:...` then something has gone wrong - double check your edits and make sure they're correct.</span></span> <span data-ttu-id="d0d0e-289">Wenn Sie im Startmenü Ihrer App mit der rechten Maustaste klicken, können Sie sie als Kachel anheften und überprüfen, ob dort die richtigen Informationen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-289">If you right-click on your app in the Start Menu, you can Pin it as a tile and verify the correct information is displayed there also.</span></span>

### <a name="step-13-add-more-supported-languages"></a><span data-ttu-id="d0d0e-290">Schritt 1.3: Hinzufügen von mehr unterstützten Sprachen</span><span class="sxs-lookup"><span data-stu-id="d0d0e-290">Step 1.3: Add more supported languages</span></span>

<span data-ttu-id="d0d0e-291">Nachdem die Änderungen am AppX-Manifest vorgenommen und die ursprüngliche `resources.resw`-Datei erstellt wurde, ist es ganz einfache, zusätzliche Sprachen hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-291">Once the changes have been made to the AppX manifest and the initial `resources.resw` file has been created, adding additional languages is easy.</span></span>

**<span data-ttu-id="d0d0e-292">Erstellen zusätzlicher lokalisierter Ressourcen</span><span class="sxs-lookup"><span data-stu-id="d0d0e-292">Create additional localized resources</span></span>**

<span data-ttu-id="d0d0e-293">Erstellen Sie zunächst die Werte für die zusätzlich lokalisierten Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-293">First, create the additional localized resource values.</span></span> 

<span data-ttu-id="d0d0e-294">Erstellen Sie im Ordner `Strings` zusätzliche Ordner für jede Sprache, die Sie unterstützen. Verwenden Sie dafür den entsprechenden BCP-47-Code (z.B. `Strings\de-DE`).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-294">Within the `Strings` folder, create additional folders for each language you support using the appropriate BCP-47 code (for example, `Strings\de-DE`).</span></span> <span data-ttu-id="d0d0e-295">Erstellen Sie in jedem dieser Ordner eine `resources.resw`-Datei (mithilfe von XML-Editor oder dem Visual Studio-Designer), die die Werte der übersetzten Ressourcen enthält.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-295">Within each of these folders, create a `resources.resw` file (using either an XML editor or the Visual Studio designer) that includes the translated resource values.</span></span> <span data-ttu-id="d0d0e-296">Es wird vorausgesetzt, dass die lokalisierten Zeichenfolgen bereits verfügbar sind. Sie müssen diese nur in die Datei `.resw` kopieren; der Übersetzungsschritt selbst wird in diesem Dokument nicht behandelt.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-296">It is assumed you already have the localized strings available somewhere, and you just need to copy them into the `.resw` file; this document does not cover the translation step itself.</span></span> 

<span data-ttu-id="d0d0e-297">Die Datei `Strings\de-DE\resources.resw` könnte beispielsweise wie folgt aussehen, der <span style="background-color: yellow">hervorgehobene Text</span> wurde von `en-US` geändert:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-297">For example, the `Strings\de-DE\resources.resw` file might look like this, with the <span style="background-color: yellow">highlighted text</span> changed from `en-US`:</span></span>

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

<span data-ttu-id="d0d0e-298">Für die folgenden Schritte gilt die Annahme, dass Sie sowohl für `de-DE` als auch für `fr-FR` Ressourcen hinzugefügt haben, dasselbe Muster kann jedoch für alle Sprachen befolgt werden.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-298">The following steps assume you added resources for both `de-DE` and `fr-FR`, but the same pattern can be followed for any language.</span></span>

**<span data-ttu-id="d0d0e-299">Aktualisieren von AppX-Manifest, um die unterstützten Sprachen aufzuführen</span><span class="sxs-lookup"><span data-stu-id="d0d0e-299">Update AppX manifest to list supported languages</span></span>**

<span data-ttu-id="d0d0e-300">AppX-Manifest muss aktualisiert werden, um die von der App unterstützten Sprachen aufzuführen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-300">The AppX manifest must be updated to list the languages supported by the app.</span></span> <span data-ttu-id="d0d0e-301">Der Desktop App Converter fügt die Standardsprache hinzu, die anderen müssen jedoch explizit hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-301">The Desktop App Converter adds the default language, but the others must be added explicitly.</span></span> <span data-ttu-id="d0d0e-302">Aktualisieren Sie beim direkten Bearbeiten der Datei `AppxManifest.xml` den `Resources`-Knoten wie folgt, fügen Sie dabei so viele Elemente hinzu, wie Sie benötigen, und ersetzen die <span style="background-color: yellow">entsprechenden Sprachen, die Sie unterstützen</span>. Stellen Sie dabei außerdem sicher, dass der erste Eintrag in der Liste die Standard- (Fallback-)Sprache ist.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-302">If you're editing the `AppxManifest.xml` file directly, update the `Resources` node as follows, adding as many elements as you need, and substituting the <span style="background-color: yellow">appropriate languages you support</span> and making sure the first entry in the list is the default (fallback) language.</span></span> <span data-ttu-id="d0d0e-303">In diesem Beispiel ist der Standard Englisch (USA) mit zusätzlicher Unterstützung für Deutsch (Deutschland) und Französisch (Frankreich):</span><span class="sxs-lookup"><span data-stu-id="d0d0e-303">In this example, the default is English (US) with additional support for both German (Germany) and French (France):</span></span>

<blockquote>
<pre>
&lt;Resources&gt;
  &lt;Resource Language="<span style="background-color: yellow">EN-US</span>" /&gt;
  &lt;Resource Language="<span style="background-color: yellow">DE-DE</span>" /&gt;
  &lt;Resource Language="<span style="background-color: yellow">FR-FR</span>" /&gt;
&lt;/Resources&gt;
</pre>
</blockquote>

<span data-ttu-id="d0d0e-304">Wenn Sie Visual Studio verwenden, sollte Sie nichts weiter tun müssen; wenn Sie `Package.appxmanifest` betrachten, sollten Sie den speziellen Wert <span style="background-color: yellow">x generate</span> sehen. Dieser bewirkt, dass der Buildprozess die Sprachen einfügt, die sich in Ihrem Projekt befinden (basierend auf den Ordnern, die mit den BCP-47 Codes benannt sind).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-304">If you are using Visual Studio, you shouldn't need to do anything; if you look at `Package.appxmanifest` you should see the special <span style="background-color: yellow">x-generate</span> value, which causes the build process to insert the languages it finds in your project (based on the folders named with BCP-47 codes).</span></span> <span data-ttu-id="d0d0e-305">Beachten Sie, dass dies kein gültiger Wert für echte Appx-Manifeste ist. Es funktioniert nur für Visual Studio-Projekte:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-305">Note that this is not a valid value for a real Appx Manifest; it only works for Visual Studio projects:</span></span>

<blockquote>
<pre>
&lt;Resources&gt;
  &lt;Resource Language="<span style="background-color: yellow">x-generate</span>" /&gt;
&lt;/Resources&gt;
</pre>
</blockquote>

**<span data-ttu-id="d0d0e-306">Neuerstellen mit den lokalisierten Werten</span><span class="sxs-lookup"><span data-stu-id="d0d0e-306">Re-build with the localized values</span></span>**

<span data-ttu-id="d0d0e-307">Sie können Ihre Anwendung jetzt erneut erstellen und bereitstellen, und wenn Sie Ihre bevorzugte Sprache in Windows ändern, sollten die neu lokalisierten Werte im Startmenü angezeigt werden (Informationen zum Ändern Ihrer Sprache finden Sie unten).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-307">Now you can build and deploy your application, again, and if you change your language preference in Windows you should see the newly-localized values appear in the Start menu (instructions for how to change your language are below).</span></span>

<span data-ttu-id="d0d0e-308">Bei Visual Studio können Sie wieder einfach `Ctrl+Shift+B` zum Erstellen verwenden, und mit der rechten Maustaste auf das Projekt klicken, um es bereitzustellen (`Deploy`).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-308">For Visual Studio, again you can just use `Ctrl+Shift+B` to build, and right-click the project to `Deploy`.</span></span>

<span data-ttu-id="d0d0e-309">Wenn Sie das Projekt manuell erstellen, führen Sie die gleichen Schritte wie oben beschrieben aus, fügen Sie jedoch die zusätzlichen Sprachen getrennt durch Unterstriche zur Liste der Standardqualifizierer (`/dq`) hinzu, wenn Sie die Konfigurationsdatei erstellen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-309">If you're manually building the project, follow the same steps as above but add the additional languages, separated by underscores, to the default qualifiers list (`/dq`) when creating the configuration file.</span></span> <span data-ttu-id="d0d0e-310">Beispiel: Unterstützung der Ressourcen für Englisch, Deutsch und Französisch, die im vorherigen Schritt hinzugefügt wurden:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-310">For example, to support the English, German, and French resources added in the previous step:</span></span>

```CMD
    makepri createconfig /cf ..\contoso_demo.xml /dq en-US_de-DE_fr-FR /pv 10.0 /o
```

<span data-ttu-id="d0d0e-311">Dadurch wird eine PRI-Datei erstellt, die alle angegebenen Sprachen enthält, die Sie einfach zum Testen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-311">This will create a PRI file that contains all the specified languagesthat you can easily use for testing.</span></span> <span data-ttu-id="d0d0e-312">Wenn die Gesamtgröße der Ressourcen gering ist, oder Sie nur eine geringe Anzahl von Sprachen unterstützen, kann dies für den Versand Ihrer App ausreichend sein. Wenn Sie jedoch von einer möglichst geringen Installations- oder Downloadgröße Ihrer Ressource profitieren möchten, müssen Sie separate Sprachpakete erstellen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-312">If the total size of your resources is small, or you only support a small number of languages, this might be acceptable for your shipping app; it's only if you want the benefits of minimizing install / download size for your resources that you need to do the additional work of building separate language packs.</span></span>

**<span data-ttu-id="d0d0e-313">Test mit den lokalisierten Werten</span><span class="sxs-lookup"><span data-stu-id="d0d0e-313">Test with the localized values</span></span>**

<span data-ttu-id="d0d0e-314">Zum Testen der neuen lokalisierten Änderungen müssen Sie einfach eine neue bevorzugte UI-Sprache zu Windows hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-314">To test the new localized changes, you simply add a new preferred UI language to Windows.</span></span> <span data-ttu-id="d0d0e-315">Es ist nicht erforderlich, Language Packs herunterzuladen, das System neu zu starten, oder die gesamte Windows-UI in einer fremden Sprache anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-315">There is no need to download language packs, reboot the system, or have your entire Windows UI appear in a foreign language.</span></span> 

0. <span data-ttu-id="d0d0e-316">Führen Sie die `Settings`-App aus (`Windows + I`).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-316">Run the `Settings` app (`Windows + I`)</span></span>
0. <span data-ttu-id="d0d0e-317">Wechseln Sie zu</span><span class="sxs-lookup"><span data-stu-id="d0d0e-317">Go to</span></span> `Time & language`
0. <span data-ttu-id="d0d0e-318">Wechseln Sie zu</span><span class="sxs-lookup"><span data-stu-id="d0d0e-318">Go to</span></span> `Region & language`
0. <span data-ttu-id="d0d0e-319">Klick</span><span class="sxs-lookup"><span data-stu-id="d0d0e-319">Click</span></span> `Add a language`
0. <span data-ttu-id="d0d0e-320">Geben (oder wählen) Sie die gewünschte Sprache ein (z.B. `Deutsch` oder `German`)</span><span class="sxs-lookup"><span data-stu-id="d0d0e-320">Type (or select) the language you want (eg `Deutsch` or `German`)</span></span>
 * <span data-ttu-id="d0d0e-321">Wenn untergeordnete Sprachen vorhanden sind, wählen Sie die gewünschte Sprache aus (z.B. `Deutsch / Deutschland`)</span><span class="sxs-lookup"><span data-stu-id="d0d0e-321">If there are sub-languages, choose the one you want (eg, `Deutsch / Deutschland`)</span></span>
0. <span data-ttu-id="d0d0e-322">Wählen Sie die neue Sprache in der Liste der Sprachen aus.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-322">Select the new language in the language list</span></span>
0. <span data-ttu-id="d0d0e-323">Klick</span><span class="sxs-lookup"><span data-stu-id="d0d0e-323">Click</span></span> `Set as default`

<span data-ttu-id="d0d0e-324">Öffnen Sie nun das Startmenü und suchen Sie Ihre Anwendung, und die lokalisierten Werte für die ausgewählte Sprache (andere Apps können auch lokalisiert angezeigt werden) sollten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-324">Now open the Start menu and search for your application, and you should see the localized values for the selected language (other apps might also appear localized).</span></span> <span data-ttu-id="d0d0e-325">Wenn Sie den lokalisierten Namen nicht sofort sehen, warten Sie einige Minuten, bis der Cache des Startmenüs aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-325">If you don't see the localized name right away, wait a few minutes until the Start Menu's cache is refreshed.</span></span> <span data-ttu-id="d0d0e-326">Um auf Ihre Muttersprache zurückzuwechseln, stellen Sie sie als Standardsprache in der Liste der Sprachen ein.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-326">To return to your native language, just make it the default language in the language list.</span></span> 

### <a name="step-14-localizing-more-parts-of-the-appx-manifest-optional"></a><span data-ttu-id="d0d0e-327">Schritt1.4: Lokalisieren weiterer Teile des AppX-Manifests (optional)</span><span class="sxs-lookup"><span data-stu-id="d0d0e-327">Step 1.4: Localizing more parts of the AppX manifest (optional)</span></span>

<span data-ttu-id="d0d0e-328">Andere Abschnitte des AppX-Manifests können lokalisiert werden.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-328">Other sections of the AppX Manifest can be localized.</span></span> <span data-ttu-id="d0d0e-329">Wenn Ihre Anwendung beispielsweise Dateierweiterungen bearbeitet, dann sollte sie eine `windows.fileTypeAssociation`-Erweiterung im Manifest aufweisen, die den <span style="background-color: lightgreen">grün hervorgehobenen Text gemäß der Abbildung verwendet</span> (da es auf Ressourcen verweisen wird), und den <span style="background-color: yellow">gelb hervorgehobenen Text</span> mit Informationen ersetzt, die für Ihre Anwendung spezifisch sind:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-329">For example, if your application handles file-extensions then it should have a `windows.fileTypeAssociation` extension in the manifest, using the <span style="background-color: lightgreen">green highlighted text</span> exactly as shown (since it will refer to resources), and replacing the <span style="background-color: yellow">yellow highlighted text</span> with information specific to your application:</span></span>

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

<span data-ttu-id="d0d0e-330">Darüber hinaus können Sie diese Informationen mit dem Visual Studio-Manifest-Designer anhand der Registerkarte `Declarations` hinzufügen. Achten Sie dabei auf die <span style="background-color: lightgreen">hervorgehobenen Werte</span>:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-330">You can also add this information using the Visual Studio Manifest Designer, using the `Declarations` tab, taking note of the <span style="background-color: lightgreen">highlighted values</span>:</span></span>

<p><img src="images\editing-declarations-info.png"/></p>

<span data-ttu-id="d0d0e-331">Fügen Sie jetzt die entsprechenden Ressourcennamen zu den einzelnen `.resw`-Dateien hinzu und ersetzen Sie somit den <span style="background-color: yellow">hervorgehobenen Text</span> mit dem entsprechenden Text Ihrer App (denken Sie daran, dass Sie diesen Vorgang für *jede unterstützte Sprache* durchführen müssen!):</span><span class="sxs-lookup"><span data-stu-id="d0d0e-331">Now add the corresponding resource names to each of your `.resw` files, replacing the <span style="background-color: yellow">highlighted text</span> with the appropriate text for your app (remember to do this for *each supported language!*):</span></span>

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

<span data-ttu-id="d0d0e-332">Dies wird dann in Teilen der Windows-Shell angezeigt, z.B. im Datei-Explorer:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-332">This will then show up in parts of the Windows shell, such as File Explorer:</span></span>

<p><img src="images\file-type-tool-tip.png"/></p>

<span data-ttu-id="d0d0e-333">Erstellen und testen Sie das Paket wie zuvor. Führen Sie dabei alle neuen Szenarien aus, die die neuen UI-Zeichenfolgen anzeigen sollten.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-333">Build and test the package as before, exercising any new scenarios that should show the new UI strings.</span></span>

- - -

## <a name="phase-2-use-mrt-to-identify-and-locate-resources"></a><span data-ttu-id="d0d0e-334">Phase 2: Verwenden von MRT, um Ressourcen zu identifizieren und zu suchen</span><span class="sxs-lookup"><span data-stu-id="d0d0e-334">Phase 2: Use MRT to identify and locate resources</span></span>

<span data-ttu-id="d0d0e-335">Im vorherigen Abschnitt wurde gezeigt, wie MRT verwendet wird, um die Manifestdatei der App zu lokalisieren, damit der Name der App und andere Metadaten durch Windows-Shell richtig angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-335">The previous section showed how to use MRT to localize your app's manifest file so that the Windows Shell can correctly display the app's name and other metadata.</span></span> <span data-ttu-id="d0d0e-336">Keine Code-Änderungen waren dafür erforderlich. Es ist lediglich die Verwendung von `.resw`-Dateien und einigen weiteren Tools erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-336">No code changes were required for this; it simply required the use of `.resw` files and some additional tools.</span></span> <span data-ttu-id="d0d0e-337">In diesem Abschnitt wird Ihnen gezeigt, wie Sie MRT zum Suchen von Ressourcen in Ihren vorhandenen Ressourcenformaten und Ihren vorhandenen Ressourcenbehandlungscode mit minimalen Änderungen verwenden.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-337">This section will show how to use MRT to locate resources in your existing resource formats and using your existing resource-handling code with minimal changes.</span></span>

### <a name="assumptions-about-existing-file-layout--application-code"></a><span data-ttu-id="d0d0e-338">Annahmen über vorhandenes Datei-Layout und Anwendungscode</span><span class="sxs-lookup"><span data-stu-id="d0d0e-338">Assumptions about existing file layout & application code</span></span>

<span data-ttu-id="d0d0e-339">Da es viele Möglichkeiten gibt, Win32-Desktop-Apps zu lokalisieren, wird dieses Dokument einige vereinfachende Annahmen über die vorhandene App-Struktur machen, die Sie zum Zuordnen Ihrer Umgebung benötigen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-339">Because there are many ways to localize Win32 Desktop apps, this paper will make some simplifying assumptions about the existing application's structure that you will need to map to your specific environment.</span></span> <span data-ttu-id="d0d0e-340">Möglicherweise müssen Sie einige Änderungen an Ihre vorhandene Codebasis oder Ressourcen-Layout vornehmen, um den Anforderungen der MRT zu entsprechen. Diese gehören nicht zum Umfang dieses Dokuments.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-340">You might need to make some changes to your existing codebase or resource layout to conform to the requirements of MRT, and those are largely out of scope for this document.</span></span>

**<span data-ttu-id="d0d0e-341">Layout der Ressourcendatei</span><span class="sxs-lookup"><span data-stu-id="d0d0e-341">Resource file layout</span></span>**

<span data-ttu-id="d0d0e-342">Dieses Whitepaper setzt voraus, dass all Ihre lokalisierten Ressourcen die gleichen Dateinamen aufweisen (z.B. `contoso_demo.exe.mui` oder `contoso_strings.dll` oder `contoso.strings.xml`), dass sie jedoch in unterschiedlichen Ordnern mit BCP-47 Namen (`en-US`, `de-DE` usw.) abgelegt wurden.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-342">This whitepaper assumes your localized resources all have the same filenames (eg, `contoso_demo.exe.mui` or `contoso_strings.dll` or `contoso.strings.xml`) but that they are placed in different folders with BCP-47 names (`en-US`, `de-DE`, etc.).</span></span> <span data-ttu-id="d0d0e-343">Es spielt keine Rolle, wie viele Ressourcendateien Sie haben, wie sie benannt sind, welche Dateiformate/verknüpften APIs sie aufweisen usw. Das einzig Wichtige ist, dass alle *logischen* Ressourcen den gleichen Dateinamen aufweisen (sie müssen jedoch in verschiedenen *physischen* Verzeichnissen abgelegt werden).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-343">It doesn't matter how many resource files you have, what their names are, what their file-formats / associated APIs are, etc. The only thing that matters is that every *logical* resource has the same filename (but placed in a different *physical* directory).</span></span> 

<span data-ttu-id="d0d0e-344">Gegenbeispiel: wenn Ihre Anwendung eine flache Dateistruktur mit einem einzigen `Resources`-Verzeichnis verwendet, das die Dateien `english_strings.dll` und `french_strings.dll` enthält, würde sie sich nicht gut zu MRT zuordnen lassen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-344">As a counter-example, if your application uses a flat file-structure with a single `Resources` directory containing the files `english_strings.dll` and `french_strings.dll`, it would not map well to MRT.</span></span> <span data-ttu-id="d0d0e-345">Eine bessere Struktur wäre ein `Resources`-Verzeichnis mit Unterverzeichnissen und den Dateien `en\strings.dll` und `fr\strings.dll`.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-345">A better structure would be a `Resources` directory with subdirectories and files `en\strings.dll` and `fr\strings.dll`.</span></span> <span data-ttu-id="d0d0e-346">Es ist auch möglich, den gleichen Basisdateinamen mit eingebetteten Qualifizierern zu verwenden, z.B. `strings.lang-en.dll` und `strings.lang-fr.dll`. Die Verwendung von Verzeichnissen mit Sprachcodes ist jedoch konzeptionell einfacher. Daher konzentrieren wir uns auf diese Vorgehensweise.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-346">It's also possible to use the same base filename but with embedded qualifiers, such as `strings.lang-en.dll` and `strings.lang-fr.dll`, but using directories with the language codes is conceptually simpler so it's what we'll focus on.</span></span>

<span data-ttu-id="d0d0e-347">**Hinweis:** Es ist weiterhin möglich, MRT und die Vorteile von AppX-Paketen zu verwenden, selbst wenn Sie diese Dateinamenskonvention nicht befolgen können – es macht nur mehr Arbeit.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-347">**Note** It is still possible to use MRT and the benefits of AppX packaging even if you can't follow this filenaming convention; it just requires more work.</span></span>

<span data-ttu-id="d0d0e-348">Die Anwendung weist beispielweise eine Reihe von benutzerdefinierten Benutzeroberflächenbefehlen auf (die für Schaltflächenbeschriftungen usw. verwendet werden), die sich in einer einfachen Textdatei mit dem Namen <span style="background-color: yellow">ui.txt</span> befinden, die unter einem <span style="background-color: yellow">UICommands</span>-Ordner dargestellt wird:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-348">For example, the application might have a set of custom UI commands (used for button labels etc.) in a simple text file named <span style="background-color: yellow">ui.txt</span>, laid out under a <span style="background-color: yellow">UICommands</span> folder:</span></span>

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

**<span data-ttu-id="d0d0e-349">Ressourcenladecode</span><span class="sxs-lookup"><span data-stu-id="d0d0e-349">Resource loading code</span></span>**

<span data-ttu-id="d0d0e-350">In diesem Whitepaper wird angenommen, dass Sie an einer bestimmten Stelle in Ihrem Code die Datei finden möchten, die eine lokalisierte Ressource enthält, und dass Sie diese laden und verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-350">This whitepaper assumes that at some point in your code you want to locate the file that contains a localized resource, load it, and then use it.</span></span> <span data-ttu-id="d0d0e-351">Die APIs, die zum Laden der Ressourcen verwendet werden und die APIs, die zum Extrahieren der Ressourcen verwendet werden, sind nicht wichtig.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-351">The APIs used to load the resources, the APIs used to extract the resources, etc. are not important.</span></span> <span data-ttu-id="d0d0e-352">Im Pseudocode gibt es im Wesentlichen drei Schritte:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-352">In pseudocode, there are basically three steps:</span></span>

```
set userLanguage = GetUsersPreferredLanguage()
set resourceFile = FindResourceFileForLanguage(MY_RESOURCE_NAME, userLanguage)
set resource = LoadResource(resourceFile) 
    
// now use 'resource' however you want
```

<span data-ttu-id="d0d0e-353">MRT erfordert nur das Ändern der ersten beiden Schritte in diesem Prozess – wie Sie die besten Ressourcen festlegen und wie Sie sie finden.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-353">MRT only requires changing the first two steps in this process - how you determine the best candidate resources and how you locate them.</span></span> <span data-ttu-id="d0d0e-354">Es ist nicht erforderlich, das Laden oder die Verwendung der Ressourcen zu ändern (obwohl Ihnen dafür Hilftsmittel bereitgestellt, wenn Sie davon profitieren möchten).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-354">It doesn't require you to change how you load or use the resources (although it provides facilities for doing that if you want to take advantage of them).</span></span>
 
<span data-ttu-id="d0d0e-355">Die Anwendung kann z.B. die Win32-API `GetUserPreferredUILanguages`, die CRT-Funktion `sprintf` und die Win32-API `CreateFile` verwenden, um die drei oben genannten Pseudocode-Funktionen zu ersetzen, und dann die Textdatei auf `name=value`-Paare manuell analysieren.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-355">For example, the application might use the Win32 API `GetUserPreferredUILanguages`, the CRT function `sprintf`, and the Win32 API `CreateFile` to replace the three pseudocode functions above, then manually parse the text file looking for `name=value` pairs.</span></span> <span data-ttu-id="d0d0e-356">(Die Details sind nicht wichtig; dies dient lediglich der Veranschaulichung der Tatsache, dass MRT keine Auswirkung auf die Techniken hat, die für die Verarbeitung der Ressourcen verwendet wird, nachdem sie gefunden wurden).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-356">(The details are not important; this is merely to illustrate that MRT has no impact on the techniques used to handle resources once they have been located).</span></span>

### <a name="step-21-code-changes-to-use-mrt-to-locate-files"></a><span data-ttu-id="d0d0e-357">Schritt2.1: Codeänderungen für die Verwendung von MRT, um Dateien zu suchen</span><span class="sxs-lookup"><span data-stu-id="d0d0e-357">Step 2.1: Code changes to use MRT to locate files</span></span>

<span data-ttu-id="d0d0e-358">Das Wechseln zwischen Codes für die Verwendung von MRT zum Suchen von Ressourcen ist nicht schwierig.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-358">Switching your code to use MRT for locating resources is not difficult.</span></span> <span data-ttu-id="d0d0e-359">Es erfordert die Verwendung einer Handvoll von WinRT-Typen und ein paar Codezeilen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-359">It requires using a handful of WinRT types and a few lines of code.</span></span> <span data-ttu-id="d0d0e-360">Die Haupttypen, die Sie verwenden werden, lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-360">The main types that you will use are as follows:</span></span>

* <span data-ttu-id="d0d0e-361">[ResourceContext](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Resources.Core.ResourceContext), das den derzeit aktiven Satz von Qualifiziererwerten enthält (Sprache, Skalierungsfaktor usw.).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-361">[ResourceContext](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Resources.Core.ResourceContext), which encapsulates the currently active set of qualifier values (language, scale factor, etc.)</span></span>
* <span data-ttu-id="d0d0e-362">[ResourceManager](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.resources.core.resourcemanager), (die WinRT-Version, nicht die .NET-Version) der den Zugriff auf alle Ressourcen aus der PRI-Datei ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-362">[ResourceManager](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.resources.core.resourcemanager) (the WinRT version, not the .NET version), which enables access to all the resources from the PRI file</span></span>
* <span data-ttu-id="d0d0e-363">[ResourceMap](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.resources.core.resourcemap), die eine bestimmte Teilmenge der Ressourcen in der PRI-Datei (in diesem Beispiel stehen die dateibasierten Ressourcen im Vergleich zu den Zeichenfolgenressourcen) darstellt.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-363">[ResourceMap](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.resources.core.resourcemap), which represents a specific subset of the resources in the PRI file (in this example, the file-based resources vs. the string resources)</span></span>
* <span data-ttu-id="d0d0e-364">[NamedResource](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Resources.Core.NamedResource), die eine logische Ressource mit allen möglichen Kandidaten darstellt.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-364">[NamedResource](https://docs.microsoft.com/en-us/uwp/api/Windows.ApplicationModel.Resources.Core.NamedResource), which represents a logical resource and all its possible candidates</span></span>
* <span data-ttu-id="d0d0e-365">[ResourceCandidate](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.resources.core.resourcecandidate), die eine konkrete Kandidatenressource darstellt.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-365">[ResourceCandidate](https://docs.microsoft.com/en-us/uwp/api/windows.applicationmodel.resources.core.resourcecandidate), which represents a single concrete candidate resource</span></span> 

<span data-ttu-id="d0d0e-366">In Pseudocode würden Sie eine bestimmte Ressource würden Sie wie folgt einen gegebenen Ressourcen-Dateinamen (z.B. `UICommands\ui.txt` im obigen Beispiel) auflösen:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-366">In pseudo-code, the way you would resolve a given resource file name (like `UICommands\ui.txt` in the sample above) is as follows:</span></span>

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

<span data-ttu-id="d0d0e-367">Beachten Sie insbesondere, dass der Code **nicht** einen bestimmten Sprachordner anfordert – z. B. `UICommands\en-US\ui.txt` – auch wenn die Dateien dementsprechend auf dem Datenträger gespeichert sind.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-367">Note in particular that the code does **not** request a specific language folder - like `UICommands\en-US\ui.txt` - even though that is how the files exist on-disk.</span></span> <span data-ttu-id="d0d0e-368">Stattdessen wird nach dem *logischen* Dateinamen `UICommands\ui.txt` gefragt und der Code ist von MRT abhängig, um die entsprechende Datei auf dem Datenträger in einem der Sprachverzeichnisse zu finden.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-368">Instead, it asks for the *logical* filename `UICommands\ui.txt` and relies on MRT to find the appropriate on-disk file in one of the language directories.</span></span>

<span data-ttu-id="d0d0e-369">Ab dieser Stelle kann die Beispiel-App weiterhin `CreateFile` zum Laden der `absoluteFileName` und Analysieren der `name=value`-Paare wie zuvor verwenden; diese Logik muss in der App nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-369">From here, the sample app could continue to use `CreateFile` to load the `absoluteFileName` and parse the `name=value` pairs just as before; none of that logic needs to change in the app.</span></span> <span data-ttu-id="d0d0e-370">Beim Schreiben in C# oder C++/CX ist der tatsächliche Code ist nicht viel komplizierter als dieser (und in der Tat können viele der temporären Variablen ausgelassen werden) – weitere Informationen finden Sie unten im Abschnitt **Laden der .NET-Ressourcen**.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-370">If you are writing in C# or C++/CX, the actual code is not much more complicated than this (and in fact many of the intermediate variables can be elided) - see the section on **Loading .NET resources**, below.</span></span> <span data-ttu-id="d0d0e-371">C++/WRL-basierte Anwendungen werden aufgrund der COM-basierten APIs auf niedriger Ebene zum Aktivieren und Aufrufen der WinRT-APIs komplexer sein, aber die grundlegenden Schritte sind identisch. Weitere Informationen finden Sie unten im Abschnitt **Laden von Win32-MUI-Ressourcen**.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-371">C++/WRL-based applications will be more complex due to the low-level COM-based APIs used to activate and call the WinRT APIs, but the fundamental steps you take are the same - see the section on **Loading Win32 MUI resources**, below.</span></span>

**<span data-ttu-id="d0d0e-372">Laden von .NET-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="d0d0e-372">Loading .NET resources</span></span>**

<span data-ttu-id="d0d0e-373">Da .NET über einen integrierten Mechanismus für das Suchen und Laden von Ressourcen (als „Satellitenassemblys” bekannt) verfügt, muss für kein expliziter Code wie im obigen synthetischen Beispiel ersetzt werden – in. NET benötigen Sie lediglich die Ressourcen-DLL-Dateien in den entsprechenden Verzeichnissen, und sie werden automatisch für Sie gefunden.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-373">Because .NET has a built-in mechanism for locating and loading resources (known as "Satellite Assemblies"), there is no explicit code to replace as in the synthetic example above - in .NET you just need your resource DLLs in the appropriate directories and they are automatically located for you.</span></span> <span data-ttu-id="d0d0e-374">Wenn eine App als ein AppX-Paket anhand von Ressourcenpaketen verpackt wird, ist die Verzeichnisstruktur etwas anders – statt die Ressourcenverzeichnisse als Unterverzeichnisse des Hauptverzeichnisses der Anwendung festzulegen, werden sie als Peers vom Hauptverzeichnis festgelegt (oder sie sind gar nicht vorhanden, wenn der Benutzer die Sprache nicht in seinen Präferenzen aufgelistet hat).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-374">When an app is packaged as an AppX using resource packs, the directory structure is somewhat different - rather than having the resource directories be subdirectories of the main application directory, they are peers of it (or not present at all if the user doesn't have the language listed in their preferences).</span></span> 

<span data-ttu-id="d0d0e-375">Stellen Sie sich beispielsweise eine .NET-Anwendung mit dem folgenden Layout vor, in dem alle Dateien unter dem `MainApp`-Ordner vorhanden sind:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-375">For example, imagine a .NET application with the following layout, where all the files exist under the `MainApp` folder:</span></span>

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

<span data-ttu-id="d0d0e-376">Nach der Konvertierung zu AppX wird das Layout etwa wie folgt aussehen, sofern `en-US` als die Standardsprache festgelegt wurde und der Benutzer sowohl Deutsch als auch Französisch in seiner Liste aufgeführt hat:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-376">After conversion to AppX, the layout will look something like this, assuming `en-US` was the default language and the user has both German and French listed in their language list:</span></span>

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

<span data-ttu-id="d0d0e-377">Da die lokalisierten Ressourcen in den Unterverzeichnissen unterhalb des Installationsorts der ausführbaren Datei nicht mehr vorhanden sind, schlägt die integrierte .NET-Ressource fehl.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-377">Because the localized resources no longer exist in sub-directories underneath the main executable's install location, the built-in .NET resource resolution fails.</span></span> <span data-ttu-id="d0d0e-378">Zum Glück verfügt .NET über einen klar definierten Mechanismus für die Behandlung von fehlgeschlagenen Assembly-Ladeversuchen – das `AssemblyResolve`-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-378">Luckily, .NET has a well-defined mechanism for handling failed assembly load attempts - the `AssemblyResolve` event.</span></span> <span data-ttu-id="d0d0e-379">Eine .NET-App, die MRT verwendet, muss für dieses Ereignis registriert werden und die fehlende Assembly für das .NET-Ressourcen-Subsystems bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-379">A .NET app using MRT must register for this event and provide the missing assembly for the .NET resource subsystem.</span></span> 

<span data-ttu-id="d0d0e-380">Ein präzises Beispiel für die Verwendung von WinRT-APIs für das Suchen von durch .NET verwendeten Satelliten-Assemblys lautet wie folgt: der dargestellte Code wird absichtlich komprimiert, um eine minimale Implementierung anzuzeigen, obwohl sie wie Sie sehen können fast genau dem oben genannten Pseudocode entspricht, mit übergebenen `ResolveEventArgs`, die den zu suchenden Namen der Assembly bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-380">A concise example of how to use the WinRT APIs to locate satellite assemblies used by .NET is as follows; the code as-presented is intentionally compressed to show a minimal implementation, although you can see it maps closely to the pseudo-code above, with the passed-in `ResolveEventArgs` providing the name of the assembly we need to locate.</span></span> <span data-ttu-id="d0d0e-381">Eine ausführbare Version dieses Codes (mit ausführlichen Kommentare und Fehlerbehandlung) finden Sie in der Datei `PriResourceRsolver.cs` im [der **.NET Assembly Resolver**-Beispiel auf GitHub](https://aka.ms/fvgqt4).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-381">A runnable version of this code (with detailed comments and error-handling) can be found in the file `PriResourceRsolver.cs` in [the **.NET Assembly Resolver** sample on GitHub](https://aka.ms/fvgqt4).</span></span>

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

<span data-ttu-id="d0d0e-382">Angesichts der oben aufgeführten Klasse, würden Sie Folgendes an einer beliebigen frühen Stelle im Startcode Ihrer Anwendung hinzufügen (bevor lokalisierte Ressourcen geladen werden müssten):</span><span class="sxs-lookup"><span data-stu-id="d0d0e-382">Given the class above, you would add the following somewhere early-on in your application's startup code (before any localized resources would need to load):</span></span>

```C#
void EnableMrtResourceLookup()
{
  AppDomain.CurrentDomain.AssemblyResolve += PriResourceResolver.ResolveResourceDll;
}
```

<span data-ttu-id="d0d0e-383">Die .NET-Laufzeit löst das Ereignis `AssemblyResolve` aus, wenn die Ressourcen-DLLs nicht gefunden werden kann. An diesem Punkt sucht der bereitgestellten Ereignishandler die gewünschte Datei über MRT und gibt die Assembly zurück.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-383">The .NET runtime will raise the `AssemblyResolve` event whenever it can't find the resource DLLs, at which point the provided event handler will locate the desired file via MRT and return the assembly.</span></span>

<span data-ttu-id="d0d0e-384">**Hinweis:** Wenn Ihre App bereits einen `AssemblyResolve`-Handler für andere Zwecke besitzt, müssen Sie den ressourcenauflösenden Code in den vorhandenen Code integrieren.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-384">**Note** If your app already has an `AssemblyResolve` handler for other purposes, you will need to integrate the resource-resolving code with your existing code.</span></span>

**<span data-ttu-id="d0d0e-385">Laden von Win32-MUI-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="d0d0e-385">Loading Win32 MUI resources</span></span>**

<span data-ttu-id="d0d0e-386">Das Laden von Win32-MUI-Ressourcen ist im Wesentlichen identisch mit dem Laden von .NET-Satellitenassemblys, es wird jedoch entweder der Code C++/CX oder C++/WRL verwendet.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-386">Loading Win32 MUI resources is essentially the same as loading .NET Satellite Assemblies, but using either C++/CX or C++/WRL code instead.</span></span> <span data-ttu-id="d0d0e-387">Die Verwendung von C++/CX ermöglicht einen viel einfacheren Code, der dem oben aufgeführten Code C# sehr ähnelt, jedoch C++-Erweiterungen, Compiler-Switches und zusätzlichen Laufzeitaufwand verwendet, die Sie vielleicht vermeiden möchten.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-387">Using C++/CX allows for much simpler code that closely matches the C# code above, but it uses C++ language extensions, compiler switches, and additional runtime overheard you might wish to avoid.</span></span> <span data-ttu-id="d0d0e-388">Wenn dies der Fall ist, stellt C++/WRL eine Lösung mit deutlich geringeren Auswirkungen dar – für den Preis von ausführlicherem Code.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-388">If that is the case, using C++/WRL provides a much lower-impact solution at the cost of more verbose code.</span></span> <span data-ttu-id="d0d0e-389">Wenn Sie jedoch mit der ATL-Programmierung (oder mit COM im Allgemeinen) vertraut sind, sollte WRL ihnen vertraut vorkommen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-389">Nevertheless, if you are familiar with ATL programming (or COM in general) then WRL should feel familiar.</span></span> 

<span data-ttu-id="d0d0e-390">Die folgende Beispielfunktion veranschaulicht, wie C++/WRL verwendet werden kann, um eine bestimmte Ressourcen-DLL zu laden und ein `HINSTANCE` zurückzugeben, das zum Laden weiterer Ressourcen mithilfe von Win32-Ressourcen-APIs verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-390">The following sample function shows how to use C++/WRL to load a specific resource DLL and return an `HINSTANCE` that can be used to load further resources using the usual Win32 resource APIs.</span></span> <span data-ttu-id="d0d0e-391">Beachten Sie, dass dieser Code auf der aktuellen Sprache des Benutzers beruht – anders als bei dem C#-Beispiel, bei dem der `ResourceContext` explizit mit der Sprache initialisiert wird, die von der .NET-Laufzeit angefordert wird.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-391">Note that unlike the C# sample that explicitly initializes the `ResourceContext` with the language requested by the .NET runtime, this code relies on the user's current language.</span></span>

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

## <a name="phase-3-building-resource-packs"></a><span data-ttu-id="d0d0e-392">Phase 3: Erstellen von Ressourcenpaketen</span><span class="sxs-lookup"><span data-stu-id="d0d0e-392">Phase 3: Building resource packs</span></span>

<span data-ttu-id="d0d0e-393">Jetzt, da Sie über ein umfangreiches Paket verfügen, das alle Ressourcen enthält, gibt es zwei Möglichkeiten, das Hauptpaket und Ressourcenpakete separat zu erstellen, um die Größen für den Download und die Installation zu verringern:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-393">Now that you have a "fat pack" that contains all resources, there are two paths towards building separate main package and resource packages in order to minimize download and install sizes:</span></span>

0. <span data-ttu-id="d0d0e-394">Nehmen Sie ein vorhandenes umfangreiches Paket, und führen Sie es im [Bündel-Generator-Tool](https://aka.ms/bundlegen) aus, um automatisch Ressourcenpakete zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-394">Take an existing fat pack and run it through [the Bundle Generator tool](https://aka.ms/bundlegen) to automatically create resource packs.</span></span> <span data-ttu-id="d0d0e-395">Dies ist der bevorzugte Ansatz, wenn Sie über ein Buildsystem verfügen, das bereits ein umfangreiches Paket erstellt, und Sie dieses im Nachhinein verarbeiten möchten, um die Ressourcenpakete zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-395">This is the preferred approach if you have a build system that already produces a fat pack and you want to post-process it to generate the resource packs.</span></span>
0. <span data-ttu-id="d0d0e-396">Erzeugen Sie die einzelnen Ressourcenpakete direkt, und integrieren Sie sie in ein Bündel.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-396">Directly produce the individual resource packages and build them into a bundle.</span></span> <span data-ttu-id="d0d0e-397">Dies ist der bevorzugte Ansatz, wenn Sie mehr Kontrolle über Ihr Buildsystem haben und die Pakete direkt erstellen können.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-397">This is the preferred approach if you have more control over your build system and can build the packages directly.</span></span>

### <a name="step-31-creating-the-bundle"></a><span data-ttu-id="d0d0e-398">Schritt3.1: Erstellen des Bündels</span><span class="sxs-lookup"><span data-stu-id="d0d0e-398">Step 3.1: Creating the bundle</span></span>

**<span data-ttu-id="d0d0e-399">Verwenden des Bündel-Generator-Tools</span><span class="sxs-lookup"><span data-stu-id="d0d0e-399">Using the Bundle Generator tool</span></span>**

<span data-ttu-id="d0d0e-400">Um das Bündel-Generator-Tool zu verwenden, muss die für das Paket erstellte PRI-Konfigurationsdatei manuell aktualisiert werden, um den Abschnitt `<packaging>` zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-400">In order to use the Bundle Generator tool, the PRI config file created for the package needs to be manually updated to remove the `<packaging>` section.</span></span>

<span data-ttu-id="d0d0e-401">Wenn Sie Visual Studio verwenden, finden Sie im [Thema **Sicherstellen, dass Ressourcen auf einem Gerät installiert sind...** auf MSDN](https://msdn.microsoft.com/en-us/library/dn482043.aspx) Informationen dazu, wie Sie alle Sprachen in das Hauptpaket integrieren, indem Sie die Dateien `priconfig.packaging.xml` und `priconfig.default.xml` erstellen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-401">If you're using Visual Studio, refer to [the **Ensure that resources are installed...** topic on MSDN](https://msdn.microsoft.com/en-us/library/dn482043.aspx) for information on how to build all languages into the main package by creating the files `priconfig.packaging.xml` and `priconfig.default.xml`.</span></span>

<span data-ttu-id="d0d0e-402">Wenn Sie Dateien manuell bearbeiten, gehen Sie folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-402">If you're manually editing files, follow these steps:</span></span> 

0. <span data-ttu-id="d0d0e-403">Erstellen Sie die Konfigurationsdatei auf die gleiche Weise wie zuvor, indem Sie den richtigen Pfad, den richtigen Dateinamen und die Sprachen ersetzen:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-403">Create the config file the same way as before, substituting the correct path, file name and languages:</span></span>

    `makepri createconfig /cf ..\contoso_demo.xml /dq en-US_de-DE_es-MX /pv 10.0 /o`
0. <span data-ttu-id="d0d0e-404">Öffnen Sie die erstellte `.xml`-Datei manuell, und löschen Sie den gesamten Abschnitt `&lt;packaging&rt;` (alles andere muss jedoch intakt bleiben):</span><span class="sxs-lookup"><span data-stu-id="d0d0e-404">Manually open the created `.xml` file and delete the entire `&lt;packaging&rt;` section (but keep everything else intact):</span></span>

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

0. <span data-ttu-id="d0d0e-405">Erstellen Sie die `.pri`-Datei und das `.appx`-Paket wie zuvor, indem Sie die aktualisierte Konfigurationsdatei und die entsprechenden Verzeichnis- und Dateinamen verwenden (oben finden Sie weitere Informationen zu diesen Befehlen):</span><span class="sxs-lookup"><span data-stu-id="d0d0e-405">Build the `.pri` file and the `.appx` package as before, using the updated configuration file and the appropriate directory and file names (see above for more information on these commands):</span></span>

```CMD
makepri new /pr . /cf ..\contoso_demo.xml /of ..\resources.pri /mf AppX /o
makeappx pack /m AppXManifest.xml /f ..\resources.map.txt /p ..\contoso_demo.appx /o
```

0. <span data-ttu-id="d0d0e-406">Nachdem das Paket erstellt wurde, verwenden Sie den folgenden Befehl, um das Bündel zu erstellen, indem Sie das richtige Verzeichnis und die richtigen Dateinamen verwenden:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-406">Once the package has been created, use the following command to create the bundle, using the appropriate directory and file names:</span></span>

    `BundleGenerator.exe -Package ..\contoso_demo.appx -Destination ..\bundle -BundleName contoso_demo`

<span data-ttu-id="d0d0e-407">Nun können Sie mit dem letzten Schritt fortfahren, der Signierung (siehe unten).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-407">Now you can move to the final step, which is Signing (see below).</span></span>

**<span data-ttu-id="d0d0e-408">Manuelles Erstellen von Ressourcenpaketen</span><span class="sxs-lookup"><span data-stu-id="d0d0e-408">Manually creating resource packages</span></span>**

<span data-ttu-id="d0d0e-409">Das manuelle Erstellen von Ressourcenpaketem erfordert die Ausführung eines etwas anderen Satzes von Befehlen, um eigene `.pri`- und `.appx`-Dateien zu erstellen. Diese sind den Befehlen ähnlich, die oben im Zusammenhang mit der Erstellung von FAT-Paketen beschrieben wurden. Daher werden sie nur wenig erklärt.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-409">Manually creating resource packages requires running a slightly different set of commands to build separate `.pri` and `.appx` files - these are all similar to the commands used above to create fat packages, so minimal explanation is given.</span></span> <span data-ttu-id="d0d0e-410">Hinweis: Alle Befehle gehen davon aus, dass das aktuelle Verzeichnis das Verzeichnis ist, in dem sich die Datei `AppXManifest.xml` befindet. Alle Dateien werden jedoch in das übergeordnete Verzeichnis platziert. (Sie können ein anderes Verzeichnis verwenden, wenn erforderlich, sollten das Projektverzeichnis jedoch nicht mit einer dieser Dateien kontaminieren.)</span><span class="sxs-lookup"><span data-stu-id="d0d0e-410">Note: All the commands assume that the current directory is the directory containing the `AppXManifest.xml` file, but all files are placed into the parent directory (you can use a different directory, if necessary, but you shouldn't pollute the project directory with any of these files).</span></span> <span data-ttu-id="d0d0e-411">Wie immer, ersetzen Sie die „Contoso“-Dateinamen durch eigene Dateinamen.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-411">As always, replace the "Contoso" filenames with your own file names.</span></span>

0. <span data-ttu-id="d0d0e-412">Verwenden Sie den folgenden Befehl, um eine Konfigurationsdatei zu erstellen, die **nur** die Standardsprache als den Standardqualifizierer nennt, in diesem Fall `en-US`:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-412">Use the following command to create a config file that names **only** the default language as the default qualifier - in this case, `en-US`:</span></span>

    `makepri createconfig /cf ..\contoso_demo.xml /dq en-US /pv 10.0 /o`
0. <span data-ttu-id="d0d0e-413">Erstellen Sie eine `.pri`- und `.map.txt`-Standarddatei für das Hauptpaket sowie einen zusätzlichen Satz von Dateien für jede Sprache in Ihrem Projekt. Verwenden Sie hierzu den folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-413">Create a default `.pri` and `.map.txt` file for the main package, plus an additional set of files for each language found in your project, with the following command:</span></span>

    `makepri new /pr . /cf ..\contoso_demo.xml /of ..\resources.pri /mf AppX /o`
0. <span data-ttu-id="d0d0e-414">Verwenden Sie den folgenden Befehl, um das Hauptpaket zu erstellen (das den ausführbaren Code und die Standardsprachressourcen enthält).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-414">Use the following command to create the main package (which contains the executable code and default language resources).</span></span> <span data-ttu-id="d0d0e-415">Wie immer, ändern Sie den Namen wie gewünscht. Sie sollten das Paket jedoch in einem eigenen Verzeichnis platzieren, um das Erstellen des Bündels zu vereinfachen (dieses Beispiel verwendet das Verzeichnis `..\bundle`):</span><span class="sxs-lookup"><span data-stu-id="d0d0e-415">As always, change the name as you see fit, although you should put the package in a separate directory to make creating the bundle easier later (this example uses the `..\bundle` directory):</span></span>

    `makeappx pack /m .\AppXManifest.xml /f ..\resources.map.txt /p ..\bundle\contoso_demo.main.appx /o`
0. <span data-ttu-id="d0d0e-416">Nachdem das Hauptpaket erstellt wurde, verwenden Sie den folgenden Befehl einmal für jede weitere Sprache (d.h., Sie wiederholen diesen Befehl für jede Sprachzuordnungsdatei, die im vorherigen Schritt generiert wurde).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-416">After the main package has been created, use the following command once for each additional language (ie, repeat this command for each language map file generated in the previous step).</span></span> <span data-ttu-id="d0d0e-417">Auch hier sollten Sie die Ausgabe in einem separaten Verzeichnis platzieren (in demselben Verzeichnis wie das Hauptpaket).</span><span class="sxs-lookup"><span data-stu-id="d0d0e-417">Again, the output should be in a separate directory (the same one as the main package).</span></span> <span data-ttu-id="d0d0e-418">Beachten Sie, dass die Sprache **sowohl** in der Option `/f` als auch in der Option `/p` angegeben ist, sowie die Verwendung des neuen Arguments `/r` (das anzeigt, dass ein Ressourcenpaket gewünscht wird):</span><span class="sxs-lookup"><span data-stu-id="d0d0e-418">Note the language is specified **both** in the `/f` option and the `/p` option, and the use of the new `/r` argument (which indicates a Resource Package is desired):</span></span>

    `makeappx pack /r /m .\AppXManifest.xml /f ..\resources.language-de.map.txt /p ..\bundle\contoso_demo.de.appx /o`
0. <span data-ttu-id="d0d0e-419">Kombinieren Sie alle Pakete aus dem Bündelverzeichnis in einer einzigen `.appxbundle`-Datei.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-419">Combine all the packages from the bundle directory into a single `.appxbundle` file.</span></span> <span data-ttu-id="d0d0e-420">Die neue Option `/d` gibt das Verzeichnis für alle Dateien im Bündel an (daher wurden die `.appx`-Dateien im vorherigen Schritt in ein eigenes Verzeichnis platziert):</span><span class="sxs-lookup"><span data-stu-id="d0d0e-420">The new `/d` option specifies the directory to use for all the files in the bundle (this is why the `.appx` files are put into a separate directory in the previous step):</span></span>

    `makeappx bundle /d ..\bundle /p ..\contoso_demo.appxbundle /o`

<span data-ttu-id="d0d0e-421">Der letzte Schritt beim Erstellen des Pakets ist das Signieren.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-421">The final step to building the package is Signing.</span></span>

### <a name="step-32-signing-the-bundle"></a><span data-ttu-id="d0d0e-422">Schritt3.2: Signieren des Bündels</span><span class="sxs-lookup"><span data-stu-id="d0d0e-422">Step 3.2: Signing the bundle</span></span>

<span data-ttu-id="d0d0e-423">Nachdem Sie die `.appxbundle`-Datei erstellt haben (entweder über das Bündel-Generator-Tool oder manuell), erhalten Sie eine einzelne Datei, die das Hauptpaket sowie alle Ressourcenpakete enthält.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-423">Once you have created the `.appxbundle` file (either through the Bundle Generator tool or manually) you will have a single file that contains the main package plus all the resource packages.</span></span> <span data-ttu-id="d0d0e-424">Der letzte Schritt besteht im Signieren der Datei, damit sie von Windows installiert wird:</span><span class="sxs-lookup"><span data-stu-id="d0d0e-424">The final step is to sign the file so that Windows will install it:</span></span>

    signtool sign /fd SHA256 /a /f ..\contoso_demo_key.pfx ..\contoso_demo.appxbundle

<span data-ttu-id="d0d0e-425">In diesem Vorgang wird eine signierte `.appxbundle`-Datei erstellt, die das Hauptpaket sowie alle sprachspezifischen Ressourcenpakete enthält.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-425">This will produce a signed `.appxbundle` file that contains the main package plus all the language-specific resource packages.</span></span> <span data-ttu-id="d0d0e-426">Wie bei einer Paketdatei werden durch Doppelklicken auf diese Datei die App und alle relevanten Sprachpakete installiert, abhängig von den Windows-Spracheinstellungen des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="d0d0e-426">It can be double-clicked just like a package file to install the app plus any appropriate language(s) based on the user's Windows language preferences.</span></span>

## <a name="related-topics"></a><span data-ttu-id="d0d0e-427">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="d0d0e-427">Related topics</span></span>

* [<span data-ttu-id="d0d0e-428">Anpassen von Ressourcen mit Qualifizierern für Sprache, Skalierung, hohen Kontrast und anderen Qualifizierern</span><span class="sxs-lookup"><span data-stu-id="d0d0e-428">Tailor your resources for language, scale, high contrast, and other qualifiers</span></span>](tailor-resources-lang-scale-contrast.md)