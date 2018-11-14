---
author: jnHs
Description: Manage and view details related to each of your apps in Partner Center, and configure services such as A/B testing and maps.
title: App-Verwaltung und -Dienste
ms.assetid: 99DA2BC1-9B5D-4746-8BC0-EC723D516EEF
ms.author: wdg-dev-content
ms.date: 10/31/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 7ffac7fa77191bbe56e7aa3870c71c3c02254d72
ms.sourcegitcommit: 4d88adfaf544a3dab05f4660e2f59bbe60311c00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "6458200"
---
# <a name="app-management-and-services"></a>App-Verwaltung und -Dienste

Sie können verwalten und Anzeigen von Details zu einzelnen apps in [Partner Center, und konfigurieren Sie Dienste wie Benachrichtigungen, A / B-Tests und Karten.

Bei der Arbeit mit einer app im Partner Center sehen Sie im linken Navigationsmenü Abschnitte für **Dienste** und **App-Verwaltung**. Sie können diese Abschnitte erweitern, um auf die unten beschriebenen Funktionen zuzugreifen.

## <a name="services"></a>Dienste

Im Abschnitt **Dienste** können Sie verschiedene Dienste für Ihre Apps verwalten.

## <a name="xbox-live"></a>Xbox Live

Wenn Sie ein Spiel veröffentlichen, können Sie die [Xbox Live Creators-Programm](http://xbox.com/developers/creators-program) auf dieser Seite aktivieren. Auf diese Weise können Sie die Starten konfigurieren und Testen Xbox Live-Features, und schließlich veröffentlichen Sie Ihr Spiel Xbox Live Creators-Programm.

Weitere Informationen finden Sie unter [Erste Schritte mit Xbox Live Creators-Programm](../xbox-live/get-started-with-creators/get-started-with-xbox-live-creators.md) und [Erstellen eines neuen Titels für Xbox Live Creators-Programm und in der testumgebung veröffentlichen](../xbox-live/get-started-with-creators/create-and-test-a-new-creators-title.md).

## <a name="experimentation"></a>Experimentation

Auf der Seite **Experimentation** können Sie Experimente mit A/B-Tests für Ihre Apps für die universelle Windows-Plattform (UWP) erstellen und ausführen. Bei einem A/B-Test wird die Effektivität von Featureänderungen (oder Abweichungen) in Ihrer App für einige Kunden ermittelt, bevor die Änderungen für die Allgemeinheit aktiviert werden.

Weitere Informationen finden Sie unter [Ausführen von App-Experimenten mit A/B-Tests](../monetize/run-app-experiments-with-a-b-testing.md).

## <a name="maps"></a>Karten

Um Kartendienste in Apps zu verwenden, die auf Windows 10 or Windows 8.x ausgerichtet sind, besuchen Sie das [Bing Karten Dev Center](http://go.microsoft.com/fwlink/p/?LinkId=614880). Informationen dazu, wie Sie einen kartenauthentifizierungsschlüssel aus dem Bing Maps Developer Center anfordern und Ihrer app hinzufügen finden Sie weitere Informationen [Anfordern eines kartenauthentifizierungsschlüssels](../maps-and-location/authentication-key.md) . 

Verwenden Sie die Seite " **Karten** " nur für zuvor veröffentlichten apps für Windows Phone 8.1 und früheren Versionen. Um Kartendienste in diese apps verwenden, müssen Sie eine Kartendienst-Anwendungs-ID und ein Token in Ihrem app Code einfügen anfordern. Beim **Abrufen von token**anklicken, wir einen Map-Dienst Anwendungs-ID (**ApplicationID**) zu generieren und Service Authentifizierungstoken (**AuthenticationToken**) für Ihre app zuordnen. Achten Sie darauf, dass Ihr Code vor dem Paket Sie diese Werte hinzufügen und übermitteln Ihrer app. Weitere Informationen finden Sie unter [Hinzufügen eines Kartensteuerelements zu einer Seite (Windows Phone 8.1)](http://go.microsoft.com/fwlink/p/?LinkId=614882).

## <a name="product-collections-and-purchases"></a>Produktsammlungen und Einkäufe

Um den Zugriff auf Besitzerinformationen für apps und Add-ons im Microsoft Store-Sammlungs-API und der Microsoft Store-Einkaufs-API zu verwenden, müssen Sie das zugehörige eingeben hier Azure AD-Client-IDs. Beachten Sie, dass es bis zu 16 Stunden dauern kann, bis diese Änderungen wirksam werden.

Weitere Informationen finden Sie unter [Verwalten von Produktansprüchen aus einem Dienst](../monetize/view-and-grant-products-from-a-service.md).

## <a name="administrator-consent"></a>Zustimmung des Administrators

f Ihr Produkt mit Azure AD integriert und APIs aufruft, die [Anwendung oder delegierte Berechtigungen verfügen](https://developer.microsoft.com/graph/docs/concepts/permissions_reference) anfordern, die Zustimmung des Administrators, erfordern Geben Sie Ihre Azure AD-Client-ID ein. Dadurch können Administratoren, die die app für ihre Organisation gewähren Zustimmung für Ihr Produkt, die für alle Benutzer im Mandanten fungieren erwerben.

Weitere Informationen finden Sie unter [für eine gesamte Mandanten Zustimmung anfordern](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-v2-scopes#requesting-consent-for-an-entire-tenant).

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

**WNS/MPNS** Abschnitt enthält Optionen zum Erstellen und Senden von Benachrichtigungen an die Kunden Ihrer app. 

> [!TIP]
> Es wird empfohlen, für UWP-apps mithilfe des **Benachrichtigungen** in Partner Center. Dieses Feature können Sie die Benachrichtigungen an alle Kunden Ihrer app zu senden, oder auf eine benutzerorientierte Teilmenge Ihrer Windows 10-Kunden, die die Kriterien erfüllen, die Sie in einem [Kundensegment](create-customer-segments.md)definiert haben. Weitere Informationen finden Sie unter [Senden von Benachrichtigung an die Kunden Ihrer App](send-push-notifications-to-your-apps-customers.md).

Je nach Pakettyp Ihrer app und den jeweiligen Anforderungen können Sie auch eine der folgenden Optionen verwenden: 

-   **Windows-Pushbenachrichtigungsdienste (Windows Push Notification Services, WNS)** ermöglichen es, Popup-, Kachel- und Badgeupdates sowie unformatierte Updates von Ihren eigenen Clouddiensten aus zu senden. Weitere Informationen finden Sie unter [Übersicht über den Windows-Pushbenachrichtigungsdienst (Windows Push Notification Service, WNS)](../design/shell/tiles-and-notifications/windows-push-notification-services--wns--overview.md).

-   **Microsoft Azure Mobile Apps** ermöglichen das Senden von Pushbenachrichtigungen, die Authentifizierung und Verwaltung von App-Benutzern und das Speichern von App-Daten in der Cloud. Weitere Informationen finden Sie in der [MobileApps-Dokumentation](http://go.microsoft.com/fwlink/p/?LinkId=221116).

-   **Microsoft Push Notification Service (MPNS)** kann mit zuvor veröffentlichten XAP-Paketen für Windows Phone verwendet werden. Sie können eine begrenzte Anzahl nicht authentifizierter Benachrichtigungen senden, ohne hier eine Konfiguration vorzunehmen. Zur Vermeidung von Drosselungslimits wird jedoch empfohlen, authentifizierte Benachrichtigungen zu verwenden. Wenn Sie MPNS verwenden, müssen Sie ein Zertifikat in das auf der Seite " **WNS/MPNS** " bereitgestellte Feld hochladen. Weitere Informationen finden Sie unter [Einrichten eines authentifizierten Webdiensts zum Senden von Pushbenachrichtigungen für Windows Phone 8](http://go.microsoft.com/fwlink/p/?LinkId=528736).
 

 
