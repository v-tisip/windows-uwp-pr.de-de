---
author: jnHs
Description: View the names that you've reserved for your app, reserve additional names (for other languages or to change your app's name), and delete reserved names that you don't need anymore.
title: Verwalten von App-Namen
ms.assetid: D95A6227-746E-4729-AE55-648A7102401C
ms.author: wdg-dev-content
ms.date: 8/07/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Anw.-Name Anw.-Name Update Spielname, Produktname ändern Windows 10 Uwp, app-Namen
ms.localizationpriority: medium
ms.openlocfilehash: f0d2c6f72e2f69f0b768af55f9bddeb9bb008027
ms.sourcegitcommit: 5dda01da4702cbc49c799c750efe0e430b699502
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/21/2018
ms.locfileid: "4115492"
---
# <a name="manage-app-names"></a>Verwalten von App-Namen

**App-Namen verwalten** können alle Namen anzeigen, die Sie für Ihre Anwendung reserviert haben zusätzliche Namen (für andere Sprachen oder Ihre app Namen ändern) reserviert, und löschen Sie Namen, die Sie benötigen. Diese Seite finden im [Windows-Entwicklungscenter Dashboard](https://partner.microsoft.com/dashboard) Sie im Abschnitt **App verwalten** im linken Navigationsmenü für Ihre Apps erweitern.


## <a name="reserve-additional-names-for-your-app"></a>Reservieren zusätzlicher Namen für Ihre App

Sie können mehrere App-Namen reservieren, die für dieselbe App verwendet werden. Dies ist besonders hilfreich, wenn Sie Ihre App in mehreren Sprachen anbieten und für die verschiedenen Sprachen unterschiedliche Namen verwenden möchten. Sie können auch einen neuen Namen reservieren, um den Namen einer App ändern wie unten beschrieben.

Reservieren Sie einen neuen Namen für die Anwendung finden Sie das Textfeld im Abschnitt **Weitere Namen reservieren** der Seite **app verwalten** . Geben Sie den zu reservierenden Namen ein, und klicken Sie auf **Verfügbarkeit überprüfen**. Wenn der Name verfügbar ist, klicken Sie auf **Produktnamen reservieren**. Sie können mehrere app-Namen reservieren, wiederholen Sie diese Schritte ggf..

> [!NOTE]
> Weitere Informationen zum Reservieren von App-Namen und den Gründen, warum ein bestimmter Name u. U. nicht verfügbar ist, finden Sie unter [App-Erstellung durch Reservierung eines Namens](create-your-app-by-reserving-a-name.md).


## <a name="delete-app-names"></a>Löschen von App-Namen

Wenn Sie einen zuvor reservierten Namen nicht mehr verwenden möchten, können Sie ihn wieder freigeben, indem Sie ihn hier löschen. Überlegen Sie sich Ihre Entscheidung genau, da der Name danach sofort von einer anderen Person reserviert und verwendet werden kann.

Um einen reservierten Namen Ihrer App zu löschen, suchen Sie den nicht mehr verwendeten Namen, und klicken Sie auf **Löschen**. Klicken Sie im Bestätigungsdialogfeld erneut auf **Löschen**, um den Vorgang zu bestätigen.

Beachten Sie, dass Ihre app mindestens ein reservierten Name muss. Um vollständig entfernen einer Anwendung aus dem Dashboard, und lassen die Namen für die Anwendung reserviert haben klicken Sie auf die **App** -Übersichtsseite **app löschen** . (Wenn die App in Bearbeitung eine Übermittlung enthält, müssen Sie diese zuerst löschen.) Beachten Sie, dass wenn die app im Speicher bereits veröffentlicht haben, Sie es aus dem Dashboard löschen können (obwohl Sie **Blendet Produkte** Funktionen auf **der Übersichtsseite** können ausgeblendet). 


## <a name="rename-an-app-that-has-already-been-published"></a>Umbenennen einer bereits veröffentlichten App

Wenn Ihre App bereits im Store veröffentlicht wurde und Sie sie umbenennen möchten, können Sie dazu (mithilfe der oben beschriebenen Schritte) einen neuen Namen für die App reservieren und eine neue App-Übermittlung vornehmen. 

Sie müssen Ihre app-Pakete ersetzt den alten Namen durch den neuen und aktualisierten Pakete auf Ihren Beitrag hochladen aktualisieren.
- Aktualisieren Sie zunächst die Datei Package.StoreAssociation.xml, um den neuen Namen manuell oder mithilfe von Visual Studio verwenden (**Projekt > Shop > zuordnen App Store...**). Weitere Informationen finden Sie unter [Package eine UWP app mit Visual Studio](../packaging/packaging-uwp-apps.md).
- Aktualisieren Sie ebenfalls das [**Package/Properties/DisplayName**](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-displayname)-Element im App-Manifest, und aktualisieren Sie Grafiken oder Texte, die den App-Namen enthalten. 
  > [!IMPORTANT]
  > Achten Sie darauf, dass Sie die Datei Package.StoreAssociation.xml aktualisieren, bevor Sie **Paket/Eigenschaften/Anzeigenname** im App-Manifest ändern, andernfalls erhalten Sie möglicherweise einen Fehler.

Speicher mit, dass der neue Name verwendet, gehen Sie auf der [Eintragsseite Speicher](create-app-store-listings.md) für diese Sprache und wählen aus **Produktnamen** . Achten Sie darauf, die Beschreibung und andere Teile des Angebots für alle Vorkommnisse des Namens überprüfen und Updates bei Bedarf.

> [!NOTE]
> Wenn Ihre app-Pakete oder Shop-Angebote in mehreren Sprachen, müssen Sie Pakete aktualisieren bzw. speichern Angebote für jede Sprache, in der der Name aktualisiert werden muss.

Wenn Ihre Anwendung mit dem neuen Namen veröffentlicht wurde, können Sie alle älteren Namen löschen, die Sie nicht mehr verwenden.

> [!TIP]
> Jede Anwendung wird im Dashboard mit den Vornamen der für sie reserviert. **Umbenennen eine Anwendung Schritte befolgt haben, und möchten sie das Dashboard mit dem neuen Namen angezeigt, müssen Sie den ursprünglichen Namen löschen (auf der Seite **Anwendung verwalten** ).** 

 

 




