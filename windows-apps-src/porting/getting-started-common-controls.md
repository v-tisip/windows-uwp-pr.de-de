---
author: stevewhims
ms.assetid: E2B73380-D673-48C6-9026-96976D745017
description: Erste Schritte mit allgemeinen Steuerelementen
title: Erste Schritte mit allgemeinen Steuerelementen
ms.author: stwhi
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: db2b4a74b5b40060779dd82764dcf2ed2799b285
ms.sourcegitcommit: 70ab58b88d248de2332096b20dbd6a4643d137a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2018
ms.locfileid: "5919006"
---
# <a name="getting-started-common-controls"></a>Erste Schritte: Allgemeine Steuerelemente


## <a name="common-controls-list"></a>Liste "Allgemeine Steuerelemente"

Im vorherigen Abschnitt haben Sie mit nur zwei Steuerelementen gearbeitet: Schaltflächen und Textblöcken. Es gibt natürlich auch viele weitere Steuerelemente, die Ihnen zur Verfügung stehen. Hier sind einige gängige Steuerelemente, die Sie in Ihren Apps und unter iOS verwenden können. Die iOS-Steuerelemente sind in alphabetischer Reihenfolge neben den entsprechenden UWP-Steuerelementen aufgeführt.

Das Besondere bei UWP-Steuerelementen ist, dass sie den Typ des Geräts erkennen, auf dem sie ausgeführt werden, und ihre Darstellung und Funktionalität entsprechend ändern können. Wenn Ihr Projekt z.B. das [**DatePicker**](https://msdn.microsoft.com/library/windows/apps/br211681)-Steuerelement verwendet, ist dieses in der Lage, seine Darstellung und sein Verhalten auf einem Desktopcomputer im Vergleich zu einem Telefon entsprechend zu optimieren und anzupassen. Sie müssen nichts weiter unternehmen: die Steuerelemente passen sich automatisch zur Laufzeit an.

| iOS-Steuerelement (Klasse/Protokoll) | Entsprechende UWP-Steuerelement |
|------------------------------|--------------------------------------|
| Aktivitätsanzeige (**UIActivityIndicatorView**) | [**ProgressRing**](https://msdn.microsoft.com/library/windows/apps/br227538) <br/> Siehe auch [Schnellstart: Hinzufügen von Statussteuerelementen](https://msdn.microsoft.com/library/windows/apps/xaml/hh780651) |
| Anzeigenbanner-Ansicht (**ADBannerView**) und Anzeigenbanner-Ansichtsdelegat (**ADBannerViewDelegate**) | [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx) <br/> Siehe auch [Anzeigen von Werbung in Ihrer App](../monetize/display-ads-in-your-app.md) |
| Schaltfläche (UIButton) | [Taste](https://msdn.microsoft.com/library/windows/apps/br209265) <br/> Siehe auch [Schnellstart: Hinzufügen von Schaltflächensteuerelementen](https://msdn.microsoft.com/library/windows/apps/xaml/jj153346) |
| Datumsauswahl (UIDatePicker) | [DatePicker](https://msdn.microsoft.com/library/windows/apps/br211681) |
| Bildansicht (UIImageView) | [Image](https://msdn.microsoft.com/library/windows/apps/br242752) <br/> Siehe auch [Image und ImageBrush](https://msdn.microsoft.com/library/windows/apps/mt280382) |
| Bezeichnung (UILabel) | [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652) <br/> Siehe auch [Schnellstart: Anzeigen von Text](https://msdn.microsoft.com/library/windows/apps/xaml/hh700392) |
| Kartenansicht (MKMapView) und Kartenansichtsdelegat (MKMapViewDelegate) | Finden Sie unter [Bing Maps für UWP-apps](http://go.microsoft.com/fwlink/p/?LinkId=263496) |
| Navigationscontrollerdelegat (UINavigationController) und Navigationscontrollerdelegat (UINavigationControllerDelegate) | [Frame](https://msdn.microsoft.com/library/windows/apps/br242682) <br/> Siehe auch [Navigation](https://msdn.microsoft.com/library/windows/apps/mt187344) |
| Seitensteuerung (UIPageControl) | [Page](https://msdn.microsoft.com/library/windows/apps/br227503) <br/> Siehe auch [Navigation](https://msdn.microsoft.com/library/windows/apps/mt187344) |
| Auswahlansicht (UIPickerView) und Auswahlansichtsdelegat (UIPickerViewDelegate) | [ComboBox](https://msdn.microsoft.com/library/windows/apps/br209348) <br/> Siehe auch [Hinzufügen von Kombinationsfeldern und Listenfeldern](https://msdn.microsoft.com/library/windows/apps/xaml/hh780616) |
| Statusleiste (UIProgressView) | [ProgressBar](https://msdn.microsoft.com/library/windows/apps/br227529) <br/> Siehe auch [Schnellstart: Hinzufügen von Statussteuerelementen](https://msdn.microsoft.com/library/windows/apps/xaml/hh780651) |
| Bildlaufansicht (UIScrollView) und Bildlaufansichtsdelegat (UIScrollViewDelegate) | [ScrollViewer](https://msdn.microsoft.com/library/windows/apps/br209527) <br/>  Siehe auch [Beispiele zu Bildlauf, Verschieben und Zoomen von Extensible Application Markup Language (XAML)](http://go.microsoft.com/fwlink/p/?LinkId=238577) |
| Suchleiste (UISearchBar) und Suchleistendelegat (UISearchBarDelegate) | Siehe [Hinzufügen von Suchfunktionen zu einer App](https://msdn.microsoft.com/library/windows/apps/xaml/jj130767) <br/>  Siehe auch [Schnellstart: Hinzufügen von Suchfunktionen zu einer App](https://msdn.microsoft.com/library/windows/apps/xaml/hh868180) |
| Segmentiertes Steuerelement (UISegmentedControl) | Keine |
| Schieberegler (UISlider) | [Slider](https://msdn.microsoft.com/library/windows/apps/br209614) <br/>  Siehe auch [So wird's gemacht: Hinzufügen eines Schiebereglers](https://msdn.microsoft.com/library/windows/apps/xaml/hh868197) |
| Controller für geteilte Ansicht (UISplitViewController) und Controllerdelegat für geteilte Ansicht (UISplitViewControllerDelegate) | Keine |
| Schalter (UISwitch) | [ToggleSwitch](https://msdn.microsoft.com/library/windows/apps/br209712) <br/>  Siehe auch [So wird's gemacht: Hinzufügen von Umschaltern](https://msdn.microsoft.com/library/windows/apps/xaml/hh868198) |
| Registerkartenleisten-Controller (UITabBarController) und Registerkartenleisten-Controllerdelegat (UITabBarControllerDelegate) | Keine |
| Tabellenansichtscontroller (UITableViewController), Tabellenansicht (UITableView), Tabellenansichtsdelegat (UITableViewDelegate) und Tabellenzelle (UITableViewCell) | [ListView](https://msdn.microsoft.com/library/windows/apps/br242878) <br/>  Siehe auch [Schnellstart: Hinzufügen von ListView- und GridView-Steuerelementen](https://msdn.microsoft.com/library/windows/apps/xaml/hh780650) |
| Textfeld (UITextField) und Textfelddelegat (UITextFieldDelegate) | [TextBox](https://msdn.microsoft.com/library/windows/apps/br209683) <br/>  Siehe auch [Anzeigen und Bearbeiten von Text](https://msdn.microsoft.com/library/windows/apps/mt280218) |
| Textansicht (UITextView) und Textansichtsdelegat (UITextViewDelegate) | [TextBlock](https://msdn.microsoft.com/library/windows/apps/br209652) <br/>  Siehe auch [Schnellstart: Anzeigen von Text](https://msdn.microsoft.com/library/windows/apps/xaml/hh700392) |
| Ansicht (UIView) und Ansichtscontroller (UIViewController) | [Page](https://msdn.microsoft.com/library/windows/apps/br227503) <br/>  Siehe auch [Navigation](https://msdn.microsoft.com/library/windows/apps/mt187344) |
| Webansicht (UIWebView) und Webansichtsdelegat (UIWebViewDelegate) | [WebView](https://msdn.microsoft.com/library/windows/apps/br227702) <br/>  Siehe auch [Beispiel für XAML-WebView-Steuerelement](http://go.microsoft.com/fwlink/p/?LinkId=238582) |
| Fenster (UIWindow) | [Frame](https://msdn.microsoft.com/library/windows/apps/br242682) <br/>  Siehe auch [Navigation](https://msdn.microsoft.com/library/windows/apps/mt187344) |

Unter [Steuerelementliste](https://msdn.microsoft.com/library/windows/apps/mt185406) finden Sie noch mehr Steuerelemente.

**Hinweis:** eine Liste mit Steuerelementen für UWP-apps mit JavaScript und HTML, finden Sie in der [Liste der Steuerelemente](https://msdn.microsoft.com/library/windows/apps/hh465453).

### <a name="next-step"></a>Nächster Schritt

[Erste Schritte: Navigation](getting-started-navigation.md)

## <a name="related-topics"></a>Verwandte Themen

* [Build2014: Was ist mit XAML-Benutzeroberflächen und -Steuerelementen?](http://go.microsoft.com/fwlink/p/?LinkID=397897)
* [Build2014: Entwickeln von Apps mit dem gemeinsamen XAML-Benutzeroberflächenframework](http://go.microsoft.com/fwlink/p/?LinkID=397898)
* [Build2014: Erstellen von zusammengeführten XAML-Apps mit Visual Studio](http://go.microsoft.com/fwlink/p/?LinkID=397876)
