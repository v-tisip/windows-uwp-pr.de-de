---
author: mijacobs
Description: "In diesem Artikel werden bewährte Methoden für das Erstellen und Anzeigen von App-Einstellungen beschrieben."
title: "Richtlinien für App-Einstellungen"
ms.assetid: 2D765E90-3FA0-42F5-A5CB-BEDC14C3F60A
label: Guidelines
template: detail.hbs
ms.author: mijacobs
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 67714d0b7a95e1034486d39853c91c9a7590bfa5
ms.sourcegitcommit: 45490bd85e6f8d247a041841d547ecac2ff48250
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2017
---
# <a name="guidelines-for-app-settings"></a><span data-ttu-id="584da-104">Richtlinien für App-Einstellungen</span><span class="sxs-lookup"><span data-stu-id="584da-104">Guidelines for app settings</span></span>

<link rel="stylesheet" href="https://az835927.vo.msecnd.net/sites/uwp/Resources/css/custom.css">

<span data-ttu-id="584da-105">App-Einstellungen sind die vom Benutzer anpassbaren Teile Ihrer App und live innerhalb der Einstellungsseite einer App.</span><span class="sxs-lookup"><span data-stu-id="584da-105">App settings are the user-customizable portions of your app and live within an app settings page.</span></span> <span data-ttu-id="584da-106">Beispielsweise kann ein Benutzer in einer Newsreader-App angeben, welche neuen Quellen oder wie viele Spalten auf dem Bildschirm angezeigt werden sollen. Und die Einstellungen einer Wetter-App können es dem Benutzer ermöglichen, zwischen Celsius und Fahrenheit als Standardmaßeinheit zu wählen.</span><span class="sxs-lookup"><span data-stu-id="584da-106">For example, app settings in a news reader app might let the user specify which news sources to display or how many columns to display on the screen, while a weather app's settings could let the user choose between Celsius and Fahrenheit as the default unit of measurement.</span></span> <span data-ttu-id="584da-107">In diesem Artikel werden bewährte Methoden für das Erstellen und Anzeigen von App-Einstellungen beschrieben.</span><span class="sxs-lookup"><span data-stu-id="584da-107">This article describes best practices for creating and displaying app settings.</span></span>

![Beispiel für einen Einstellungsbereich](images/app-settings.png)

## <a name="should-i-include-a-settings-page-in-my-app"></a><span data-ttu-id="584da-109">Sollte die App eine Seite für App-Einstellungen beinhalten?</span><span class="sxs-lookup"><span data-stu-id="584da-109">Should I include a settings page in my app?</span></span>

<span data-ttu-id="584da-110">Hier sind Beispiele für App-Optionen, die zu einer Seite für App-Einstellungen gehören:</span><span class="sxs-lookup"><span data-stu-id="584da-110">Here are examples of app options that belong in an app settings page:</span></span>

-   <span data-ttu-id="584da-111">Konfigurationsoptionen, die sich auf das Verhalten der App auswirken und keine häufige erneute Anpassung erfordern (z.B. die Auswahl der Standardtemperatureinheit Celsius oder Fahrenheit in einer Wetter-App, das Ändern der Kontoeinstellungen für eine E-Mail-App, Einstellungen für Benachrichtigungen oder Barrierefreiheitsoptionen).</span><span class="sxs-lookup"><span data-stu-id="584da-111">Configuration options that affect the behavior of the app and don't require frequent readjustment, like choosing between Celsius or Fahrenheit as default units for temperature in a weather app, changing account settings for a mail app, settings for notifications, or accessibility options.</span></span>
-   <span data-ttu-id="584da-112">Optionen, die von den bevorzugten Benutzereinstellungen abhängen, wie Musik, Soundeffekte oder Farbdesigns.</span><span class="sxs-lookup"><span data-stu-id="584da-112">Options that depend on the user's preferences, like music, sound effects, or color themes.</span></span>
-   <span data-ttu-id="584da-113">App-Infos, die eher selten benötigt werden, z.B. Datenschutzrichtlinie, Hilfe, App-Version oder Copyright-Informationen.</span><span class="sxs-lookup"><span data-stu-id="584da-113">App information that isn't accessed very often, such as privacy policy, help, app version, or copyright info.</span></span>

<span data-ttu-id="584da-114">Befehle, die Teil des typischen App-Workflows sind (z.B. das Ändern der Pinselgröße in einer Zeichen-App), sollten sich nicht auf einer Einstellungsseite befinden.</span><span class="sxs-lookup"><span data-stu-id="584da-114">Commands that are part of the typical app workflow (for example, changing the brush size in an art app) shouldn't be in a settings page.</span></span> <span data-ttu-id="584da-115">Weitere Informationen zur Platzierung von Befehlen finden Sie unter [Befehlsdesigngrundlagen](https://msdn.microsoft.com/library/windows/apps/dn958433).</span><span class="sxs-lookup"><span data-stu-id="584da-115">To learn more about command placement, see [Command design basics](https://msdn.microsoft.com/library/windows/apps/dn958433).</span></span>

## <a name="general-recommendations"></a><span data-ttu-id="584da-116">Allgemeine Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="584da-116">General recommendations</span></span>


-   <span data-ttu-id="584da-117">Halten Sie die Einstellungsseiten möglichst einfach, und verwenden Sie binäre Steuerelemente (an/aus).</span><span class="sxs-lookup"><span data-stu-id="584da-117">Keep settings pages simple and make use of binary (on/off) controls.</span></span> <span data-ttu-id="584da-118">Ein [Umschalter](../controls-and-patterns/toggles.md) ist in der Regel das beste Steuerelement für binäre Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="584da-118">A [toggle switch](../controls-and-patterns/toggles.md) is usually the best control for a binary setting.</span></span>
-   <span data-ttu-id="584da-119">Verwenden Sie für Einstellungen, mit denen Benutzer aus bis zu fünf zusammenhängenden Optionen, die sich gegenseitig ausschließen, eine auswählen können, [Optionsfelder](../controls-and-patterns/radio-button.md).</span><span class="sxs-lookup"><span data-stu-id="584da-119">For settings that let users choose one item from a set of up to 5 mutually exclusive, related options, use [radio buttons](../controls-and-patterns/radio-button.md).</span></span>
-   <span data-ttu-id="584da-120">Erstellen Sie einen Einstiegspunkt für alle App-Einstellungen auf der Einstellungsseite Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="584da-120">Create an entry point for all app settings in your app setting's page.</span></span>
-   <span data-ttu-id="584da-121">Verwenden Sie einfache Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="584da-121">Keep your settings simple.</span></span> <span data-ttu-id="584da-122">Definieren Sie intelligente Standardwerte, und halten Sie die Anzahl von Einstellungen so gering wie möglich.</span><span class="sxs-lookup"><span data-stu-id="584da-122">Define smart defaults and keep the number of settings to a minimum.</span></span>
-   <span data-ttu-id="584da-123">Wenn ein Benutzer eine Einstellung ändert, sollte die App die Änderung sofort wiedergeben.</span><span class="sxs-lookup"><span data-stu-id="584da-123">When a user changes a setting, the app should immediately reflect the change.</span></span>
-   <span data-ttu-id="584da-124">Fügen Sie keine Befehle hinzu, die zu einem häufig verwendeten App-Workflow gehören.</span><span class="sxs-lookup"><span data-stu-id="584da-124">Don't include commands that are part of the common app workflow.</span></span>

## <a name="entry-point"></a><span data-ttu-id="584da-125">Einstiegspunkt</span><span class="sxs-lookup"><span data-stu-id="584da-125">Entry point</span></span>


<span data-ttu-id="584da-126">Die Methode, mit der Benutzer auf die Einstellungsseite Ihrer App zugreifen, sollte auf dem Layout Ihrer App basieren.</span><span class="sxs-lookup"><span data-stu-id="584da-126">The way that users get to your app settings page should be based on your app's layout.</span></span>

**<span data-ttu-id="584da-127">Navigationsbereich</span><span class="sxs-lookup"><span data-stu-id="584da-127">Navigation pane</span></span>**

<span data-ttu-id="584da-128">Bei einem Navigationsbereichs-Layout sollten App-Einstellungen das letzte Element in der Navigationsliste und am Ende der Liste angeheftet sein:</span><span class="sxs-lookup"><span data-stu-id="584da-128">For a nav pane layout, app settings should be the last item in the list of navigational choices and be pinned to the bottom:</span></span>

![App-Einstellungen-Einstiegspunkt für Navigationsbereich](images/appsettings-entrypoint-navpane.png)

**<span data-ttu-id="584da-130">App-Leiste</span><span class="sxs-lookup"><span data-stu-id="584da-130">App bar</span></span>**

<span data-ttu-id="584da-131">Bei Verwendung einer [App-Leiste](../controls-and-patterns/app-bars.md) oder Toolleiste sollte der Einstiegspunkt für die Einstellungen das letzte Element im Überlaufmenü „Mehr“ sein.</span><span class="sxs-lookup"><span data-stu-id="584da-131">If you're using an [app bar](../controls-and-patterns/app-bars.md) or tool bar, place the settings entry point as the last item in the "More" overflow menu.</span></span> <span data-ttu-id="584da-132">Wenn Sie den Einstiegspunkt für die Einstellungen in Ihrer App intuitiver positionieren möchten, platzieren Sie ihn direkt auf die App-Leiste und nicht ins Überlaufmenü.</span><span class="sxs-lookup"><span data-stu-id="584da-132">If greater discoverability for the settings entry point is important for your app, place the entry point directly on the app bar and not within the overflow.</span></span>

![App-Einstellungen – Einstiegspunkt für die App-Leiste](images/appsettings-entrypoint-tabs.png)

**<span data-ttu-id="584da-134">Hub</span><span class="sxs-lookup"><span data-stu-id="584da-134">Hub</span></span>**

<span data-ttu-id="584da-135">Wenn Sie ein Hublayout verwenden, sollte sich der Einstiegspunkt für App-Einstellungen im Überlaufmenü „Mehr“ einer App-Leiste befinden.</span><span class="sxs-lookup"><span data-stu-id="584da-135">If you're using a hub layout, the entry point for app settings should be placed inside the "More" overflow menu of an app bar.</span></span>

**<span data-ttu-id="584da-136">Registerkarten/Pivots</span><span class="sxs-lookup"><span data-stu-id="584da-136">Tabs/pivots</span></span>**

<span data-ttu-id="584da-137">Bei einem Registerkarten- oder Pivots-Layout raten wir davon ab, den Einstiegspunkt für App-Einstellungen als eines der Elemente der obersten Ebene in der Navigation zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="584da-137">For a tabs or pivots layout, we don't recommended placing the app settings entry point as one of the top items within the navigation.</span></span> <span data-ttu-id="584da-138">Stattdessen sollte der Einstiegspunkt für App-Einstellungen im Überlaufmenü „Mehr“ einer App-Leiste platziert werden.</span><span class="sxs-lookup"><span data-stu-id="584da-138">Instead, the entry point for app settings should be placed inside the "More" overflow menu of an app bar.</span></span>

**<span data-ttu-id="584da-139">Master/Details-Ansicht</span><span class="sxs-lookup"><span data-stu-id="584da-139">Master-details</span></span>**

<span data-ttu-id="584da-140">Anstatt den Einstiegspunkt für App-Einstellungen innerhalb eines Master/Details-Bereichs zu u verstecken, machen Sie ihn als letztes angeheftete Element auf der obersten Ebene des Masterbereichs verfügbar.</span><span class="sxs-lookup"><span data-stu-id="584da-140">Instead of burying the app settings entry point deeply within a master-details pane, make it the last pinned item on the top level of the master pane.</span></span>

## <a name="layout"></a><span data-ttu-id="584da-141">Layout</span><span class="sxs-lookup"><span data-stu-id="584da-141">Layout</span></span>


<span data-ttu-id="584da-142">Auf Desktops und Mobilgeräten sollte sich das Fenster der App-Einstellungen im Vollbildmodus öffnen und das gesamte Fenster ausfüllen.</span><span class="sxs-lookup"><span data-stu-id="584da-142">On both desktop and mobile, the app settings window should open full-screen and fill the whole window.</span></span> <span data-ttu-id="584da-143">Wenn das App-Einstellungsmenü über bis zu vier Gruppen auf oberster Ebene verfügt, sollten diese Gruppen eine Spalte nach unten kaskadieren.</span><span class="sxs-lookup"><span data-stu-id="584da-143">If your app settings menu has up to four top-level groups, those groups should cascade down one column.</span></span>

<span data-ttu-id="584da-144">Desktop:</span><span class="sxs-lookup"><span data-stu-id="584da-144">Desktop:</span></span>

![Layout der Seite für App-Einstellungen auf Desktops](images/appsettings-layout-navpane-desktop.png)

<span data-ttu-id="584da-146">Mobilgeräte:</span><span class="sxs-lookup"><span data-stu-id="584da-146">Mobile:</span></span>

![Layout der Seite für App-Einstellungen auf Smartphones](images/appsettings-layout-navpane-mobile.png)

## <a name="color-mode-settings"></a><span data-ttu-id="584da-148">Einstellungen für den Farbmodus</span><span class="sxs-lookup"><span data-stu-id="584da-148">"Color mode" settings</span></span>


<span data-ttu-id="584da-149">Wenn Ihre App Benutzern die Auswahl des Farbmodus ermöglicht, machen Sie diese Optionen mit [Optionsfeldern](../controls-and-patterns/radio-button.md) oder einem [Kombinationsfeld](../controls-and-patterns/lists.md#drop-down-lists) mit dem Header „Wählen Sie einen Modus“ verfügbar.</span><span class="sxs-lookup"><span data-stu-id="584da-149">If your app allows users to choose the app's color mode, present these options using [radio buttons](../controls-and-patterns/radio-button.md) or a [combo box](../controls-and-patterns/lists.md#drop-down-lists) with the header "Choose a mode".</span></span> <span data-ttu-id="584da-150">Die Optionen sollten lauten:</span><span class="sxs-lookup"><span data-stu-id="584da-150">The options should read</span></span>
- <span data-ttu-id="584da-151">Hell</span><span class="sxs-lookup"><span data-stu-id="584da-151">Light</span></span>
- <span data-ttu-id="584da-152">Dunkel</span><span class="sxs-lookup"><span data-stu-id="584da-152">Dark</span></span>
- <span data-ttu-id="584da-153">Windows-Standard</span><span class="sxs-lookup"><span data-stu-id="584da-153">Windows default</span></span>

<span data-ttu-id="584da-154">Wir empfehlen außerdem, einen Link zur Seite „Farben“ der Windows-App „Einstellungen“ hinzuzufügen, in der Benutzer das Windows-Standarddesign überprüfen können.</span><span class="sxs-lookup"><span data-stu-id="584da-154">We also recommend adding a hyperlink to the Colors page of the Windows Settings app where users can check the Windows default theme.</span></span> <span data-ttu-id="584da-155">Verwenden Sie die Zeichenfolge „Windows-Farbeinstellungen“ als Text für den Link.</span><span class="sxs-lookup"><span data-stu-id="584da-155">Use the string "Windows color settings" for the hyperlink text.</span></span>

![Abschnitt für die Modusauswahl](images/appsettings_mode.png)

<!--
<div class="microsoft-internal-note">
Detailed redlines showing preferred text strings for the "Choose a mode" section are available on [UNI](http://uni/DesignDepot.FrontEnd/#/ProductNav/2543/0/dv/?t=Windows%7CControls%7CColorMode&f=RS2).
</div>
-->

## <a name="about-section-and-give-feedback-button"></a><span data-ttu-id="584da-157">Abschnitt „Info“ und Schaltfläche „Feedback“</span><span class="sxs-lookup"><span data-stu-id="584da-157">"About" section and "Give feedback" button</span></span>


<span data-ttu-id="584da-158">Wenn Sie einen Abschnitt „Info zu dieser App“ in Ihrer App benötigen, erstellen Sie dafür eine dedizierte App-Einstellungsseite.</span><span class="sxs-lookup"><span data-stu-id="584da-158">If you need an "About this app" section in your app, create a dedicated app settings page for that.</span></span> <span data-ttu-id="584da-159">Platzieren Sie eine gewünschte Schaltfläche „Feedback“ im unteren Bereich der Seite „Info zu dieser App“.</span><span class="sxs-lookup"><span data-stu-id="584da-159">If you want a "Give Feedback" button, place that toward the bottom of the "About this app" page.</span></span>

<span data-ttu-id="584da-160">„Nutzungsbedingungen“ und „Datenschutzbestimmungen“ sollten [Linkschaltflächen](../controls-and-patterns/hyperlinks.md) mit Textumbruch sein.</span><span class="sxs-lookup"><span data-stu-id="584da-160">"Terms of Use" and "Privacy Statement" should be [hyperlink buttons](../controls-and-patterns/hyperlinks.md) with wrapping text.</span></span>

![Abschnitt „Info“ mit Schaltfläche „Feedback“](images/appsettings-about.png)


## <a name="recommended-page-content"></a><span data-ttu-id="584da-162">Empfohlene Seiteninhalte</span><span class="sxs-lookup"><span data-stu-id="584da-162">Recommended page content</span></span>


<span data-ttu-id="584da-163">Wenn Sie eine Liste der gewünschten Elemente auf der Seite für App-Einstellungen erstellt haben, berücksichtigen Sie die folgenden Richtlinien:</span><span class="sxs-lookup"><span data-stu-id="584da-163">Once you have a list of items that you want to include in your app settings page, consider these guidelines:</span></span>

-   <span data-ttu-id="584da-164">Gruppieren Sie ähnliche oder verwandte Einstellungen unter einer Einstellungsbezeichnung.</span><span class="sxs-lookup"><span data-stu-id="584da-164">Group similar or related settings under one settings label.</span></span>
-   <span data-ttu-id="584da-165">Versuchen Sie, die Gesamtanzahl der Einstellungen auf maximal vier oder fünf zu begrenzen.</span><span class="sxs-lookup"><span data-stu-id="584da-165">Try to keep the total number of settings to a maximum of four or five.</span></span>
-   <span data-ttu-id="584da-166">Zeigen Sie unabhängig vom App-Kontext dieselben Einstellungen an.</span><span class="sxs-lookup"><span data-stu-id="584da-166">Display the same settings regardless of the app context.</span></span> <span data-ttu-id="584da-167">Sind einige Einstellungen in einem bestimmten Kontext nicht relevant, deaktivieren Sie sie im Einstellungen-Flyout der App.</span><span class="sxs-lookup"><span data-stu-id="584da-167">If some settings aren't relevant in a certain context, disable those in the app settings flyout.</span></span>
-   <span data-ttu-id="584da-168">Verwenden Sie für Einstellungen informative Beschriftungen, die nur aus einem Wort bestehen.</span><span class="sxs-lookup"><span data-stu-id="584da-168">Use descriptive, one-word labels for settings.</span></span> <span data-ttu-id="584da-169">Nennen Sie für kontobezogene Einstellungen die Einstellung „Konten“ statt „Kontoeinstellungen“.</span><span class="sxs-lookup"><span data-stu-id="584da-169">For example, name the setting "Accounts" instead of "Account settings" for account-related settings.</span></span> <span data-ttu-id="584da-170">Wenn Sie nur eine Option für Ihre Einstellungen festlegen möchten und die Einstellungen selbst sich nicht als Beschriftung eignen, verwenden Sie „Optionen“ oder „Standardeinstellungen“.</span><span class="sxs-lookup"><span data-stu-id="584da-170">If you only want one option for your settings and the settings don't lend themselves to a descriptive label, use "Options" or "Defaults."</span></span>
-   <span data-ttu-id="584da-171">Wird über eine Einstellung direkt das Web anstelle eines Flyouts aufgerufen, informieren Sie den Benutzer mit einem als [Hyperlink](../controls-and-patterns/hyperlinks.md) formatierten visuellen Hinweis darüber, z.B. mit „Hilfe (online)“ oder „Webforen“.</span><span class="sxs-lookup"><span data-stu-id="584da-171">If a setting directly links to the web instead of to a flyout, let the user know this with a visual clue, such as "Help (online)" or "Web forums" styled as a [hyperlink](../controls-and-patterns/hyperlinks.md).</span></span> <span data-ttu-id="584da-172">Mehrere Weblinks sollten Sie in einem Flyout mit einer einzelnen Einstellung gruppieren.</span><span class="sxs-lookup"><span data-stu-id="584da-172">Consider grouping multiple links to the web into a flyout with a single setting.</span></span> <span data-ttu-id="584da-173">Beispiel: Die Einstellung „Info“ könnte ein Flyout mit Links zu Ihren Nutzungsbedingungen, Datenschutzbestimmungen und App-Support-Infos öffnen.</span><span class="sxs-lookup"><span data-stu-id="584da-173">For example, an "About" setting could open a flyout with links to your terms of use, privacy policy, and app support.</span></span>
-   <span data-ttu-id="584da-174">Fassen Sie selten verwendete Einstellungen zu einem einzelnen Eintrag zusammen, damit für gängigere Einstellungen jeweils ein eigener Eintrag zur Verfügung steht.</span><span class="sxs-lookup"><span data-stu-id="584da-174">Combine less-used settings into a single entry so that more common settings can each have their own entry.</span></span> <span data-ttu-id="584da-175">Fassen Sie Inhalte oder Links, die nur Informationen enthalten, unter der Einstellung „Info“ zusammen.</span><span class="sxs-lookup"><span data-stu-id="584da-175">Put content or links that only contain information in an "About" setting.</span></span>
-   <span data-ttu-id="584da-176">Wiederholen Sie die Funktionen nicht im Berechtigungsbereich.</span><span class="sxs-lookup"><span data-stu-id="584da-176">Don't duplicate the functionality in the "Permissions" pane.</span></span> <span data-ttu-id="584da-177">Windows stellt diesen Bereich standardmäßig bereit, und er kann nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="584da-177">Windows provides this pane by default and you can't modify it.</span></span>

-   <span data-ttu-id="584da-178">Hinzufügen von Einstellungsinhalten zum Einstellungen-Flyout</span><span class="sxs-lookup"><span data-stu-id="584da-178">Add settings content to Settings flyouts</span></span>
-   <span data-ttu-id="584da-179">Stellen Sie Inhalte von oben nach unten in einer einzelnen, ggf. bildlauffähigen Spalte dar.</span><span class="sxs-lookup"><span data-stu-id="584da-179">Present content from top to bottom in a single column, scrollable if necessary.</span></span> <span data-ttu-id="584da-180">Beschränken Sie den Bildlauf auf die doppelte Bildschirmhöhe.</span><span class="sxs-lookup"><span data-stu-id="584da-180">Limit scrolling to a maximum of twice the screen height.</span></span>
-   <span data-ttu-id="584da-181">Verwenden Sie die folgenden Steuerelemente für App-Einstellungen:</span><span class="sxs-lookup"><span data-stu-id="584da-181">Use the following controls for app settings:</span></span>

    -   <span data-ttu-id="584da-182">[Umschalter](../controls-and-patterns/toggles.md): Benutzer können Werte aktivieren oder deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="584da-182">[Toggle switches](../controls-and-patterns/toggles.md): To let users set values on or off.</span></span>
    -   <span data-ttu-id="584da-183">[Optionsfelder](../controls-and-patterns/radio-button.md): Benutzer können aus bis zu fünf zusammenhängenden, sich gegenseitig ausschließenden Optionen eine Option auswählen.</span><span class="sxs-lookup"><span data-stu-id="584da-183">[Radio buttons](../controls-and-patterns/radio-button.md): To let users choose one item from a set of up to 5 mutually exclusive, related options.</span></span>
    -   <span data-ttu-id="584da-184">[Texteingabefeld](../controls-and-patterns/text-block.md): Benutzer können hier Text eingeben.</span><span class="sxs-lookup"><span data-stu-id="584da-184">[Text input box](../controls-and-patterns/text-block.md): To let users enter text.</span></span> <span data-ttu-id="584da-185">Wählen Sie die Art des Texteingabefelds passend zum Typ des vom Benutzer erhaltenen Texts aus, beispielsweise für E-Mail-Adressen oder Kennwörter.</span><span class="sxs-lookup"><span data-stu-id="584da-185">Use the type of text input box that corresponds to the type of text you're getting from the user, such as an email or password.</span></span>
    -   <span data-ttu-id="584da-186">[Hyperlinks](../controls-and-patterns/hyperlinks.md): Benutzer werden zu einer anderen Seite innerhalb der App oder zu einer externen Website weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="584da-186">[Hyperlinks](../controls-and-patterns/hyperlinks.md): To take the user to another page within the app or to an external website.</span></span> <span data-ttu-id="584da-187">Wenn ein Benutzer auf einen Hyperlink klickt, wird das Einstellungen-Flyout geschlossen.</span><span class="sxs-lookup"><span data-stu-id="584da-187">When a user clicks a hyperlink, the Settings flyout will be dismissed.</span></span>
    -   <span data-ttu-id="584da-188">[Schaltflächen](../controls-and-patterns/buttons.md): Benutzer können eine Aktion sofort ausführen, ohne das aktuell geöffnete Flyoutmenü für Einstellungen zu schließen.</span><span class="sxs-lookup"><span data-stu-id="584da-188">[Buttons](../controls-and-patterns/buttons.md): To let users initiate an immediate action without dismissing the current Settings flyout.</span></span>
-   <span data-ttu-id="584da-189">Wenn eines der Steuerelemente deaktiviert ist, fügen Sie eine beschreibende Meldung hinzu.</span><span class="sxs-lookup"><span data-stu-id="584da-189">Add a descriptive message if one of the controls is disabled.</span></span> <span data-ttu-id="584da-190">Platzieren Sie diese Meldung über dem deaktivierten Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="584da-190">Place this message above the disabled control.</span></span>
-   <span data-ttu-id="584da-191">Zeigen Sie Inhalte und Steuerelemente als einzelnen Block per Animation an, nachdem das Einstellungen-Flyout und die Überschrift eingeblendet wurden.</span><span class="sxs-lookup"><span data-stu-id="584da-191">Animate content and controls as a single block after the Settings flyout and header have animated.</span></span> <span data-ttu-id="584da-192">Animieren Sie Inhalte mit der Animation [**enterPage**](https://msdn.microsoft.com/library/windows/apps/br212672) oder [**EntranceThemeTransition**](https://msdn.microsoft.com/library/windows/apps/br210288) mit einem Offset links von 100Pixel.</span><span class="sxs-lookup"><span data-stu-id="584da-192">Animate content using the [**enterPage**](https://msdn.microsoft.com/library/windows/apps/br212672) or [**EntranceThemeTransition**](https://msdn.microsoft.com/library/windows/apps/br210288) animations with a 100px left offset.</span></span>
-   <span data-ttu-id="584da-193">Verwenden Sie Abschnittsüberschriften, Absätze und Bezeichnungen, um Inhalte ggf. zu organisieren und zu erläutern.</span><span class="sxs-lookup"><span data-stu-id="584da-193">Use section headers, paragraphs, and labels to aid organize and clarify content, if necessary.</span></span>
-   <span data-ttu-id="584da-194">Verwenden Sie zum Wiederholen von Einstellungen eine zusätzliche UI-Ebene oder ein Model zum Erweitern und Reduzieren. Beschränken Sie Hierarchien jedoch auf maximal zweiEbenen.</span><span class="sxs-lookup"><span data-stu-id="584da-194">If you need to repeat settings, use an additional level of UI or an expand/collapse model, but avoid hierarchies deeper than two levels.</span></span> <span data-ttu-id="584da-195">So könnte zum Beispiel in einer Wetter-App, deren Einstellungen sich auf die jeweilige Stadt beziehen, eine Liste mit Städten angezeigt werden. Der Benutzer muss dann nur auf die gewünschte Stadt zu tippen, um ein neues Flyout zu öffnen oder zu erweitern, um die Einstellungsoptionen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="584da-195">For example, a weather app that provides per-city settings could list the cities and let the user tap on the city to either open a new flyout or expand to show the settings options.</span></span>
-   <span data-ttu-id="584da-196">Wenn das Laden von Steuerelementen oder Webinhalten längere Zeit in Anspruch nimmt, informieren Sie den Benutzer mithilfe eines unbestimmten Statussteuerelements darüber, dass Informationen geladen werden.</span><span class="sxs-lookup"><span data-stu-id="584da-196">If loading controls or web content takes time, use an indeterminate progress control to indicate to users that info is loading.</span></span> <span data-ttu-id="584da-197">Weitere Informationen finden Sie unter [Richtlinien für Statussteuerelemente](https://msdn.microsoft.com/library/windows/apps/hh465469).</span><span class="sxs-lookup"><span data-stu-id="584da-197">For more info, see [Guidelines for progress controls](https://msdn.microsoft.com/library/windows/apps/hh465469).</span></span>
-   <span data-ttu-id="584da-198">Verwenden Sie keine Schaltflächen für die Navigation oder zum Übernehmen von Änderungen.</span><span class="sxs-lookup"><span data-stu-id="584da-198">Don't use buttons for navigation or to commit changes.</span></span> <span data-ttu-id="584da-199">Verwenden Sie Hyperlinks, um zu anderen Seiten zu navigieren, und speichern Sie Änderungen an App-Einstellungen automatisch, wenn ein Benutzer das Einstellungen-Flyout schließt, anstatt eine Schaltfläche für das Übernehmen von Änderungen zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="584da-199">Use hyperlinks to navigate to other pages, and instead of using a button to commit changes, automatically save changes to app settings when a user dismisses the Settings flyout.</span></span>



## <a name="related-articles"></a><span data-ttu-id="584da-200">Verwandte Artikel</span><span class="sxs-lookup"><span data-stu-id="584da-200">Related articles</span></span>

* [<span data-ttu-id="584da-201">Befehlsdesigngrundlagen</span><span class="sxs-lookup"><span data-stu-id="584da-201">Command design basics</span></span>](https://msdn.microsoft.com/library/windows/apps/dn958433)
* [<span data-ttu-id="584da-202">Richtlinien für Statussteuerelemente</span><span class="sxs-lookup"><span data-stu-id="584da-202">Guidelines for progress controls</span></span>](https://msdn.microsoft.com/library/windows/apps/hh465469)
* [<span data-ttu-id="584da-203">Speichern und Abrufen von App-Daten</span><span class="sxs-lookup"><span data-stu-id="584da-203">Store and retrieve app data</span></span>](https://msdn.microsoft.com/library/windows/apps/mt299098)
* [**<span data-ttu-id="584da-204">EntranceThemeTransition</span><span class="sxs-lookup"><span data-stu-id="584da-204">EntranceThemeTransition</span></span>**](https://msdn.microsoft.com/library/windows/apps/br210288)
