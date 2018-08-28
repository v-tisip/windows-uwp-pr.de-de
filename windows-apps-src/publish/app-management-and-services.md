---
author: jnHs
Description: Manage and view details related to each of your apps in the Windows Dev Center dashboard, and configure services such as A/B testing and maps.
title: App-Verwaltung und -Dienste
ms.assetid: 99DA2BC1-9B5D-4746-8BC0-EC723D516EEF
ms.author: wdg-dev-content
ms.date: 07/18/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: d0e4be450aa972ad8561f27a8d4749050458520a
ms.sourcegitcommit: 9a17266f208ec415fc718e5254d5b4c08835150c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2018
ms.locfileid: "2891937"
---
# <a name="app-management-and-services"></a>App-Verwaltung und -Dienste

Im WindowsDevCenter-Dashboard können Sie Details zu einzelnen Apps verwalten und anzeigen sowie Dienste wie Benachrichtigungen, A/B-Tests und Karten konfigurieren.

Wenn Sie in Ihrem Dashboard mit einer App arbeiten, sehen Sie im linken Navigationsmenü Abschnitte für **Dienste** und **App-Verwaltung**. Sie können diese Abschnitte erweitern, um auf die unten beschriebenen Funktionen zuzugreifen.

## <a name="services"></a>Dienste

Im Abschnitt **Dienste** können Sie verschiedene Dienste für Ihre Apps verwalten.

## <a name="xbox-live"></a>Xbox Live

Wenn Sie ein Spiel veröffentlichen, können Sie die [Xbox Live Ersteller Programm](http://xbox.com/developers/creators-program) auf dieser Seite. Auf diese Weise können Sie konfigurieren und Testen Xbox Live-Funktionen zu starten, und schließlich Veröffentlichen Ihrer Xbox Live Ersteller Programm Spiel.

Weitere Informationen finden Sie unter [Erste Schritte mit dem Xbox Live Ersteller Programm](../xbox-live/get-started-with-creators/get-started-with-xbox-live-creators.md) und [erstellen einen neuen Xbox Live Ersteller Programm Titel und Veröffentlichen in die testumgebung](../xbox-live/get-started-with-creators/create-and-test-a-new-creators-title.md).

## <a name="experimentation"></a>Experimentation

Auf der Seite **Experimentation** können Sie Experimente mit A/B-Tests für Ihre Apps für die universelle Windows-Plattform (UWP) erstellen und ausführen. Bei einem A/B-Test wird die Effektivität von Featureänderungen (oder Abweichungen) in Ihrer App für einige Kunden ermittelt, bevor die Änderungen für die Allgemeinheit aktiviert werden.

Weitere Informationen finden Sie unter [Ausführen von App-Experimenten mit A/B-Tests](../monetize/run-app-experiments-with-a-b-testing.md).

## <a name="maps"></a>Karten

Wenn Sie Kartendienste in Apps unter Windows Phone8.1 und früheren Versionen verwenden möchten, müssen Sie eine Kartendienst-Anwendungs-ID und ein Token in Ihren App-Code einfügen. Sie finden das Token auf der Seite **Karten** im Abschnitt **Dienste**.

> [!NOTE]
> Um Kartendienste in Apps zu verwenden, die auf Windows 10 or Windows 8.x ausgerichtet sind, besuchen Sie das [Bing Karten Dev Center](http://go.microsoft.com/fwlink/p/?LinkId=614880). Weitere Informationen finden Sie unter [Anfordern eines Kartenauthentifizierungsschlüssels](https://docs.microsoft.com/windows/uwp/maps-and-location/authentication-key).

Weitere Informationen finden Sie unter [Verwenden von Kartendiensten](use-map-services.md).

## <a name="product-collections-and-purchases"></a>Produktsammlungen und Einkäufe

Um Microsoft Store Auflistung-API und die Microsoft Store Purchase-API verwenden, um die Besitzerinformationen für apps und Add-ons zuzugreifen, müssen Sie die zugeordnete eingeben hier Azure AD-Client-IDs. Beachten Sie, dass es bis zu 16 Stunden dauern kann, bis diese Änderungen wirksam werden.

Weitere Informationen finden Sie unter [Verwalten von Produktansprüchen aus einem Dienst](../monetize/view-and-grant-products-from-a-service.md).

## <a name="administrator-consent"></a>Administrator Zustimmung

f Ihr Produkt Azure AD integriert und ruft APIs, die entweder eine [Anwendungsberechtigungen oder delegierte Berechtigungen](https://developer.microsoft.com/graph/docs/concepts/permissions_reference) anfordern, die vom Administrator Zustimmung erfordern Geben Sie Ihre Azure AD-Client-ID ein. Auf diese Weise können Administratoren, die die app für ihre Organisation Grant Zustimmung für das Produkt, die für alle Benutzer in den Mandanten fungiert erwerben.

Weitere Informationen finden Sie unter [Requesting für eine gesamte Mandanten stimmen](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-v2-scopes#requesting-consent-for-an-entire-tenant).

## <a name="app-management"></a>App-Verwaltung

Im Abschnitt **App-Verwaltung** können Sie Identitäts- und Paketdetails anzeigen sowie die Namen Ihrer App verwalten.

## <a name="app-identity"></a>App-Identität

Diese Seite enthält die Details zur eindeutigen App-Identität im Store, einschließlich den URL(s) zur Verknüpfung der App mit dem App-Eintrag.

Weitere Informationen finden Sie unter [Anzeigen von Details zur App-Identität](view-app-identity-details.md).

## <a name="manage-app-names"></a>Verwalten von App-Namen

Auf dieser Seite können Sie alle für Ihre App reservierten Namen anzeigen. Sie können hier auch zusätzliche Namen reservieren oder nicht mehr verwendete Namen löschen.

Weitere Informationen finden Sie unter [Verwalten von App-Namen](manage-app-names.md).

## <a name="current-packages"></a>Aktuelle Pakete

Auf dieser Seite können Sie Details zu allen veröffentlichten Paketen anzeigen.

> [!NOTE]
> Hier werden erst Informationen angezeigt, wenn Ihre App veröffentlicht wurde.

Der Name, die Version und die Architektur der einzelnen Pakete werden angezeigt. Klicken Sie auf **Details**, um zusätzliche Informationen wie z. B. unterstützte Sprache, App-Funktionen und Dateigrößen anzuzeigen. Welche Informationen jeweils für ein Paket angezeigt werden, variiert abhängig vom Zielbetriebssystem und anderen Faktoren. 

Entwickler mit OEM-Berechtigungen können auf der Seite **Aktuelle Pakete** außerdem [Vorinstallationspakete generieren](generate-preinstall-packages-for-oems.md).

## <a name="wnsmpns"></a>WNS/MPNS

Im Abschnitt **WNS/MPNS** bietet Optionen zum Erstellen und Senden von Benachrichtigungen für Ihre app-Kunden. 

> [!TIP]
> UWP-apps wird empfohlen, mit der Option **Benachrichtigungen** in das Dashboard. Mit diesem Feature können Sie Benachrichtigungen an alle Ihre app-Kunden zu senden, oder auf eine gezielte Teilmenge von Ihrem Windows-10-Kunden, die die Kriterien erfüllen, die Sie in einem [Kundensegment](create-customer-segments.md)definiert haben. Weitere Informationen finden Sie unter [Senden von Benachrichtigung an die Kunden Ihrer App](send-push-notifications-to-your-apps-customers.md).

Je nach Ihrer app-Paket-Typ und den spezifischen Anforderungen können Sie auch eine der folgenden Optionen verwenden: 

-   **Windows-Pushbenachrichtigungsdienste (Windows Push Notification Services, WNS)** ermöglichen es, Popup-, Kachel- und Badgeupdates sowie unformatierte Updates von Ihren eigenen Clouddiensten aus zu senden. Weitere Informationen finden Sie unter [Übersicht über den Windows-Pushbenachrichtigungsdienst (Windows Push Notification Service, WNS)](../design/shell/tiles-and-notifications/windows-push-notification-services--wns--overview.md).

-   **Microsoft Azure Mobile Apps** ermöglichen das Senden von Pushbenachrichtigungen, die Authentifizierung und Verwaltung von App-Benutzern und das Speichern von App-Daten in der Cloud. Weitere Informationen finden Sie in der [MobileApps-Dokumentation](http://go.microsoft.com/fwlink/p/?LinkId=221116).

-   Der **Microsoft-Pushbenachrichtigungsdienst (Microsoft Push Notification Service, MPNS)** kann mit Ihren XAP-Paketen für Windows Phone verwendet werden. Sie können eine begrenzte Anzahl nicht authentifizierter Benachrichtigungen senden, ohne hier eine Konfiguration vorzunehmen. Zur Vermeidung von Drosselungslimits wird jedoch empfohlen, authentifizierte Benachrichtigungen zu verwenden. Wenn Sie MPNS verwenden, müssen Sie ein Zertifikat auf das entsprechende Feld auf der Seite **WNS/MPNS** hochladen. Weitere Informationen finden Sie unter [Einrichten eines authentifizierten Webdiensts zum Senden von Pushbenachrichtigungen für Windows Phone 8](http://go.microsoft.com/fwlink/p/?LinkId=528736).
 

 
