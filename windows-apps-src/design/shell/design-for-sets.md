---
author: jwmsft
description: Erfahren Sie, wie Sie Ihre App optimieren können, um die beste Erfahrung in der Sets-Benutzeroberfläche zu bieten.
title: Entwerfen für Sets
template: detail.hbs
ms.author: jimwalk
ms.date: 05/07/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Titelleiste
doc-status: Draft
ms.localizationpriority: medium
ms.openlocfilehash: 7c3e0e6ec7331e860c9153e2a2e29a51fb5848bd
ms.sourcegitcommit: e6daa7ff878f2f0c7015aca9787e7f2730abcfbf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2018
ms.locfileid: "4318356"
---
# <a name="designing-for-sets"></a>Entwerfen für Sets

> [!IMPORTANT]
> In diesem Artikel werden Funktionen beschrieben, die noch nicht veröffentlicht wurden und vor der kommerziellen Freigabe evtl. geändert werden. Microsoft übernimmt keine Garantie, weder ausdrücklich noch stillschweigend, für die hier bereitgestellten Informationen.

Beginnen mit der Windows Insider Preview ist das Sets-Feature für Benutzer Ihrer App verfügbar. Mit Sets wird Ihre App in einem Fenster dargestellt, das möglicherweise andere Apps enthält, wobei die Titelleiste des Fensters für jede App eine eigene Registerkarte enthält.

In diesem Artikel gehen wir auf die Bereiche ein, in denen Sie Ihre App optimieren können, um die beste Benutzererfahrung in der Sets-Benutzeroberfläche zu erzielen.

> [!TIP]
> Weitere Informationen zu Sets finden Sie im Blogbeitrag [Einführung in Sets](https://insider.windows.com/en-us/articles/introducing-sets/) sowie im Vortrag [Entwickeln für Sets](https://developer.microsoft.com/events/build/content/developing-for-sets-on-windows-10) von der Microsoft Build 2018.

## <a name="customizing-tab-visuals"></a>Anpassen der Registerkarten

Standardmäßig versucht das System, geeignete Text- und Symbolfarben für die Registerkarte Ihrer App auszuwählen, wenn diese aktiv ist. Dadurch wird sichergestellt, dass die Registerkarte Ihrer App mit minimalem Aufwand ihrerseits Seite gut aussieht, auch wenn Sie keine Optimierung für Sets vornehmen.

Es kann jedoch Fälle geben, in denen es am besten ist, die Registerkartenfarbe Ihrer App anzupassen. In diesem Abschnitt beschreiben wir das Standardverhalten der Registerkarte und erläutern, wenn Sie es für Ihre App ändern sollen und wann nicht.

### <a name="tab-states"></a>Registerkartenzustände

Wenn Ihre App in einem Set enthalten ist, kann die Registerkarte einen von drei Zuständen annehmen: „ausgewählt und aktiv”, „ausgewählt und inaktiv” oder „nicht ausgewählt und inaktiv”.

- **Ausgewählt und aktiv**: Eine Registerkarte, die in einem Set ausgewählt ist und zum aktiven Vordergrundfenster gehört.

    (In diesem Dokument ist mit einer _aktiven_ Registerkarte immer die ausgewählte und aktive Registerkarte gemeint.)
- **Ausgewählt und inaktiv**: Eine Registerkarte, die in einem Set ausgewählt ist, aber nicht zum aktiven Vordergrundfenster gehört.
- **Nicht ausgewählt und inaktiv**: Jede Registerkarte in einem Set, die nicht ausgewählt ist.

Die Farbe jeder inaktiven Registerkarte wird vom System basierend auf dem Systemdesign aktualisiert und verwaltet. Es gibt keine Möglichkeit, diese Farbe durch Ihre App zu beeinflussen.

Standardmäßig übernimmt die ausgewählte und aktive Registerkarte die vom Benutzer in den Windows-Einstellungen angegebenen Systemdesignfarbe. Sie können die Registerkartenfarbe für Ihre App nur anpassen, wenn die Registerkarte aktive ist.

![Registerkartezustände in Sets](images/sets-tab-states.jpg)

### <a name="coloring-of-active-tabs"></a>Farben aktiver Registerkarten

Die Farbe der aktiven Registerkarte wird bestimmt durch die Werte, die Sie in Ihrer App festlegen, oder durch die Systemeinstellungen. Die Registerkartenfarbe für eine aktive App wird wie folgt festgelegt:

- Wenn Sie eine Registerkartenfarbe in Ihrer App angeben, hat diese Farbe die höchste Priorität. Die Registerkartenfarbe, die Sie in Ihrer App angeben, wird verwendet, wenn Ihre App aktiv ist, unabhängig von den Systemeinstellungen.
- Wenn der Benutzer aber in den Windows-Einstellungen die Option auswählt, dass die Akzentfarbe in den Titelleisten anzuzeigen ist, wird die Systemakzentfarbe verwendet.
  - Diese Einstellung befindet sich in der Windows-App „Einstellungen” unter Personalisierung > Farben > Akzentfarbe auf folgenden Flächen anzeigen: Titelleisten.
- Wenn keine App- oder Benutzereinstellungen angewendet werden, erhält die Registerkarte die aktuelle Systemdesignfarbe.

### <a name="considerations-when-you-modify-tab-colors"></a>Hinweise zum Ändern von Registerkartenfarben

Im Folgenden erörtern wir Situationen, in denen Sie die Registerkartenfarbe für Ihre App ändern möchten, und die dabei zu berücksichtigenden Umstände. Wir berücksichtigen auch einige Situationen, in denen wir empfehlen, die Farbe der Registerkarte nicht zu ändern, sondern vom System verwalten zu lassen.

#### <a name="match-your-brand-colors"></a>Verwenden der Unternehmensfarben

Normalerweise ist der ausschlaggebende Faktor für eine Änderung der Registerkartenfarbe der Wunsch, die Markenfarben des Unternehmens zu verwenden. Wenn Sie Ihre App-Registerkarte so ändern, dass sie Ihrer Markenfarbe entspricht, sollten Sie dies anhand der anderen in diesem Abschnitt beschriebenen Überlegungen testen, wie z. B. dem Layout Ihrer App oder verschiedenen Systemdesignfarben.

#### <a name="horizontal-layout"></a>Horizontales Layout

Wenn Ihr App-Layout ein durchgehendes (nicht acrylfarbenes) Farbband enthält, das horizontal über die Oberseite verläuft, ist es in der Regel ansprechend, wenn Sie die App durch eine übereinstimmende Farbe mit der Registerkarte verknüpfen. Wählen Sie eine Volltonfarbe für Ihre Registerkarte, die eine Verbindung zur App herstellt, idealerweise durch Kontinuität mit der Farbe, die oben in der App verwendet wird.

#### <a name="horizontal-layout-with-acrylic"></a>Horizontales Layout mit Acryl

Wenn in Ihrer App ein acrylfarbenes Band verwendet wird, das horizontal über die Oberseite verläuft, empfehlen wir, dass Sie die Registerkartenfarbe vom System bestimmen lassen.

Wir empfehlen zudem, hier In-App-Acryl anstelle von Hintergrund-Acryl zu verwenden, um Ihren Anwendungshintergrund in diesen Bereich fließen zu lassen, anstatt einen Streifeneffekt zu erzeugen, der durch die Anwendung oder den Desktop hinter diesem Band angezeigt wird.

Bitte beachten Sie, dass der Benutzer in diesem Fall für die Registerkarten eine Akzentfarbe festlegen kann, so dass sie entweder in einem Hell/Dunkel-Design oder mit der Akzentfarbe angezeigt werden können.

#### <a name="vertical-layout"></a>Vertikales Layout

Wenn Ihr App-Layout einen vertikalen Bereich mit Volltonfarben enthält, die vertikal verlaufen, sollten Sie die Farben der Registerkarten nicht anpassen. Die Position der Registerkarte über Ihrer App kann jederzeit vom Benutzer geändert werden. Sie können also keine Farbkontinuität zwischen dem oberen Teil Ihrer App und der Registerkarte voraussetzen. Das System verwendet andere visuelle Hinweise wie Schatten, um die Registerkarte mit Ihrer App zu verbinden.

### <a name="how-to-modify-tab-colors"></a>Ändern von Registerkartenfarben

Die Farbe der aktiven Registerkarte verwendet die APIs zur Anpassung der Titelleiste. Wenn Sie bereits die Farbe der Titelleiste Ihrer App angepasst haben, gilt die Änderung auch auf für die App-Registerkarte, wenn Ihre App zu einem Set gehört.

Zum Ändern der Registerkartenfarbe legen Sie mit den [ApplicationViewTitleBar](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationviewtitlebar)-Eigenschaften Folgendes fest:

- Eine Vollton-Hintergrundfarbe für die Registerkarte.
- Eine Vollton-Vordergrundfarbe für den Registerkartentext.

Dieses Beispiel zeigt, wie Sie eine Instanz der ApplicationViewTitleBar aufrufen und die Farbeigenschaften festlegen.

```csharp
// using Windows.UI.ViewManagement;
var titleBar = ApplicationView.GetForCurrentView().TitleBar;

// Set active window colors
titleBar.ForegroundColor = Windows.UI.Colors.White;
titleBar.BackgroundColor = Windows.UI.Colors.Green;
```

Weitere Informationen finden Sie im Abschnitt _Einfache Farbanpassung_ des Artikels [Anpassung der Titelleiste](title-bar.md#simple-color-customization) und im [Beispiel zur Anpassung der Titelleiste](http://go.microsoft.com/fwlink/p/?LinkId=620613).

### <a name="considerations-for-full-title-bar-customization"></a>Überlegungen zur vollständigen Anpassung der Titelleiste

Sie können die Titelleiste Ihrer App auch vollständig anpassen. Das ist beschrieben im Abschnitt _Vollständige Anpassung_ des Artikels [Anpassung der Titelleiste](title-bar.md#full-customization). Der Grund dafür ist in der Regel die [Übernahme von Acryl in die Titelleiste](../style/acrylic.md#extend-acrylic-into-the-title-bar) oder die Anzeige von benutzerdefiniertem Inhalt in der Titelleiste. Wenn Sie dies tun, achten Sie darauf, die Richtlinien für den Vollbildmodus und den Tabletmodus zu beachten, und zeigen Sie den benutzerdefinierten Inhalt der Titelleiste nur an, wenn [CoreApplicationViewTitleBar.IsVisible](/uwp/api/windows.applicationmodel.core.coreapplicationviewtitlebar.isvisible) den Wert **true** hat.

Wenn Ihre App in einem Set ausgeführt wird, hat CoreApplicationViewTitleBar.IsVisible den Wert **false**, und der Titelleisteninhalt sollte nicht angezeigt werden. Wenn Sie den benutzerdefinierten Titelleisteninhalt jedoch nicht wie beschrieben verbergen, wird er unter der Registerkarte der App und nicht im Titelleistenbereich angezeigt.

Wenn Sie Inhalte oder Funktionalität in der benutzerdefinierten Titelleisten-UI platziert haben, sollten Sie diese in einer anderen Benutzeroberfläche in Ihrer App verfügbar machen.

### <a name="how-to-modify-the-tab-icon"></a>Ändern des Registerkartensymbols

Um sicherzustellen, dass Ihr App-Symbol in einem Set optimal aussieht, sollten Sie ein alternatives, nicht belegtes Symbol für Ihre App bereitstellen. (Das auf der Registerkarte Ihrer App verwendete App-Symbol ist das gleiche Symbol, das in der Taskleiste verwendet wird.) Der Zweck des alternativen Symbols ist, vor jeder Hintergrundfarbe gut auszusehen. Das alternative Symbol wird verwendet, falls verfügbar.

Geben Sie in Ihrem App-Manifest zusätzlich zu Ihrem regulären Symbol ein anderes unbelegtes Symbol an. Weitere Informationen finden Sie in der [App-Symbole und Logos](/windows/uwp/design/style/app-icons-and-logos). Das anzugebende Symbol wird als "Target-Size List Assets without Plate" im Abschnitt [Weitere Informationen zu app-Symbolressourcen](/windows/uwp/design/style/app-icons-and-logos#more-about-app-icon-assets) des Artikels dokumentiert.

Wenn Sie im App-Manifest kein alternatives Symbol angeben, wird das System das Kachelsymbol wieder mit der Registerkartenfarbe versehen und es so verwenden.

![In Sets verwendete Symbole](images/sets-icons.png)

> In der Taskleiste und in der App-Registerkarte wird dasselbe Symbol verwendet.

## <a name="restore-previous-sets-with-user-activities"></a>Wiederherstellen vorheriger Sets durch Benutzeraktivitäten

Ein Vorteil von Sets ist, dass Benutzer zuvor geöffnete Registerkarten für Apps und Webinhalte wiederherstellen können, wenn sie eine App starten oder ein Dokument öffnen. (Weitere Informationen finden Sie als Blogbeitrag im Video [Introducing Sets](https://insider.windows.com/en-us/articles/introducing-sets/).) Dies erfolgt über _Benutzeraktivitäten_.

Standardmäßig erstellt das System für Ihre App Benutzeraktivitäten, wodurch die App auf einer Registerkarte wiederhergestellt werden kann, wenn ein Benutzer eine App startet oder ein Dokument öffnet. Die vom System erstellten Standardbenutzeraktivitäten können die App jedoch nur im Standardzustand starten. Sie können die App nicht in dem Zustand wiederherstellen, in dem sie sich zuvor als Teil des Sets befand.

Sie können Ihre App für Sets optimieren, indem Sie eigene Benutzeraktivitäten bereitstellen. Eine von Ihnen bereitgestellte Benutzeraktivität enthält einen Deep-Link zu Ihrer App, um sie in dem Zustand wiederherzustellen, in dem sie zuletzt als Teil des wiederherzustellenden Sets enthalten war.

So stellen Sie eine eigene Benutzeraktivität bereit:

- Antworten Sie auf einen vom Betriebssystem initiierten [UserActivityRequest](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivityrequest) mit der entsprechenden [UserActivity](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivity).
- UserActivity enthält einen Aktivierungs-Deep-Link-URI, über den das System Ihre App mit einem bestimmten Kontext startet.

Weitere Informationen finden Sie unter [UserActivityRequestManager.UserActivityRequested Event](https://docs.microsoft.com/uwp/api/windows.applicationmodel.useractivities.useractivityrequestmanager.useractivityrequested), [Behandeln der URI-Aktivierung](https://docs.microsoft.com/windows/uwp/launch-resume/handle-uri-activation), und [Benutzeraktivitäten geräteübergreifend fortsetzen](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities).

## <a name="enable-multi-instance-for-uwp-apps"></a>Aktivieren der Multiinstanzfähigkeit in UWP-Apps

Ab Windows 10, Version 1803, unterstützen UWP-Apps die Multiinstanziierung. UWP-Apps sind standardmäßig noch immer Einzelinstanzen. Daher müssen Sie die Multiinstanzfähigkeit für eine App explizit aktivieren.

Wenn Sie Ihre App multiinstanzfähig machen, können Benutzer die App in mehreren Sets gleichzeitig ausführen. Eine Einzelinstanz-App kann jeweils nur in einem Set ausgeführt werden.

Weitere Informationen dazu, wie Sie die Multiinstanzfähigkeit für eine UWP-App aktivieren können, finden Sie unter [Universelle Windows-App mit mehreren Instanzen erstellen](https://docs.microsoft.com/windows/uwp/launch-resume/multi-instance-uwp).

## <a name="use-an-in-app-back-button"></a>Verwenden einer Schaltfläche „Zurück” in der App

Um die Rückwärtsnavigation in Ihrer App zu ermöglichen, empfehlen wir, eine Schaltfläche „Zurück” in der Benutzeroberfläche der App einzufügen. Informationen dazu finden Sie in der [Anleitung für Schaltflächen zur Rückwärtsnavigation](../basics/navigation-history-and-backwards-navigation.md). Wenn Sie in Ihrer App das NavigationView-Steuerelement einsetzen, sollten Sie die zu NavigationView gehörende Schaltfläche „Zurück” verwenden.

Wenn Ihre App die Schaltfläche „Zurück” des Systems verwendet, sollten Sie diese Funktionalität durch eine Zurück-Schaltfläche in der App ersetzen. Dadurch wird eine konsistente Rückwärtsnavigation für den Benutzer sichergestellt, unabhängig davon, ob die App in einem Set ausgeführt wird oder nicht. Darüber hinaus wird erreicht, dass die Darstellung der Zurück-Schaltflächen in allen Apps konsistent bleibt.

Eine ausführliche Anleitung zum Integrieren einer Schaltfläche „Zurück” in eine App finden Sie unter [Navigationsverlauf und Rückwärtsnavigation](../basics/navigation-history-and-backwards-navigation.md).

### <a name="support-for-the-system-back-button-in-sets"></a>Unterstützung in Sets für die systemeigene Schaltfläche „Zurück”

Wenn Ihre App die systemeigene Schaltfläche „Zurück” und nicht eine entsprechende Schaltfläche in der App verwendet, rendert die System-UI weiterhin die systemeigene Zurück-Schaltfläche, um die Abwärtskompatibilität zu gewährleisten

- Wenn Ihre App nicht zu einem Set gehört, wird die Zurück-Schaltfläche in der Titelleiste gerendert. Die visuelle Erfahrung und den Benutzerinteraktionen für die Zurück-Schaltfläche bleiben unverändert.
- Wenn Ihre App zu einem Set gehört, wird die Zurück-Schaltfläche in der systemeigenen Rückwärtsnavigationsleiste gerendert.

Die systemeigene Rückwärtsnavigationsleiste ist ein „Band”, das zwischen dem Registerkartenband und dem Inhaltsbereich der App eingefügt wird. Das Band läuft über die Breite der App und enthält die Zurück-Schaltfläche auf der linken Seite. Die vertikale Höhe des Bands ist so bemessen, dass eine ausreichende Berührungszielgröße für die Zurück-Schaltfläche sichergestellt ist.

![Die systemeigene Rückwärtsnavigationsleiste in Sets](images/sets-system-back-bar.png)

> Die systemeigene Rückwärtsnavigationsleiste wird in einer App angezeigt.

Die systemeigene Rückwärtsnavigationsleiste wird dynamisch angezeigt, abhängig von der Sichtbarkeit der Zurück-Schaltfläche. Wenn die Zurück-Schaltfläche angezeigt wird, wird die systemeigene Rückwärtsnavigationsleiste zwischen Registerkartenband und App-Inhalt eingefügt. Nach dem Ausblenden der Zurück-Schaltfläche wird die systemeigene Rückwärtsnavigationsleiste dynamisch entfernt und der App-Inhalt nach oben an das Registerkartenband verschoben.

Um zu vermeiden, dass die Benutzeroberfläche Ihrer App nach oben oder unten verschoben wird, empfehlen wir, anstelle der systemeigenen Zurück-Schaltfläche eine Schaltfläche „Zurück” in der App zu verwenden.

Anpassungen der Titelleiste werden sowohl auf die App-Registerkarte als auch auf die systemeigene Rückwärtsnavigationsleiste angewendet. Wenn Sie ApplicationViewTitleBar-APIs verwenden, um Hintergrund- und Vordergrund-Farbeigenschaften anzugeben, gelten die Farben für die App-Registerkarte und die systemeigene Rückwärtsnavigationsleiste.

## <a name="related-articles"></a>Verwandte Artikel

- [Anpassen der Titelleiste](title-bar.md)
- [Navigationsverlauf und Rückwärtsnavigation](../basics/navigation-history-and-backwards-navigation.md)
- [Farbe](../style/color.md)
