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
keywords: Windows 10, Uwp, app-Namen ändern, app-Name, Update app-Name, Spiel Name, Produktname
ms.localizationpriority: medium
ms.openlocfilehash: f0d2c6f72e2f69f0b768af55f9bddeb9bb008027
ms.sourcegitcommit: 9c79fdab9039ff592edf7984732d300a14e81d92
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2018
ms.locfileid: "2816362"
---
# <a name="manage-app-names"></a>Verwalten von App-Namen

Mit dem **app-Namen verwalten** können Sie alle Namen anzeigen, die Sie für Ihre app reserviert haben reserviert zusätzliche Namen (für andere Sprachen oder den Namen Ihrer app zu ändern), und löschen Sie nicht benötigte Namen. Finden Sie auf dieser Seite im [Windows-Entwicklungscenter Dashboard](https://partner.microsoft.com/dashboard) , erweitern Sie im linken Navigationsbereich Menü Ihrer Apps aus einem Abschnitt **App-Verwaltung** .


## <a name="reserve-additional-names-for-your-app"></a>Reservieren zusätzlicher Namen für Ihre App

Sie können mehrere App-Namen reservieren, die für dieselbe App verwendet werden. Dies ist besonders hilfreich, wenn Sie Ihre App in mehreren Sprachen anbieten und für die verschiedenen Sprachen unterschiedliche Namen verwenden möchten. Sie können auch einen neuen Namen reservieren, um das Ändern des Namens einer App wie unten beschrieben.

Um einen neuen Namen für die app zu reservieren, finden Sie im Textfeld im Abschnitt **Weitere Namen reservieren** der Seite **app-Namen verwalten** . Geben Sie den zu reservierenden Namen ein, und klicken Sie auf **Verfügbarkeit überprüfen**. Wenn der Name verfügbar ist, klicken Sie auf **Produktnamen reservieren**. Sie können mehrere app-Namen reservieren, indem Sie diese Schritte wiederholen, bei Bedarf.

> [!NOTE]
> Weitere Informationen zum Reservieren von App-Namen und den Gründen, warum ein bestimmter Name u. U. nicht verfügbar ist, finden Sie unter [App-Erstellung durch Reservierung eines Namens](create-your-app-by-reserving-a-name.md).


## <a name="delete-app-names"></a>Löschen von App-Namen

Wenn Sie einen zuvor reservierten Namen nicht mehr verwenden möchten, können Sie ihn wieder freigeben, indem Sie ihn hier löschen. Überlegen Sie sich Ihre Entscheidung genau, da der Name danach sofort von einer anderen Person reserviert und verwendet werden kann.

Um einen reservierten Namen Ihrer App zu löschen, suchen Sie den nicht mehr verwendeten Namen, und klicken Sie auf **Löschen**. Klicken Sie im Bestätigungsdialogfeld erneut auf **Löschen**, um den Vorgang zu bestätigen.

Beachten Sie, dass Ihre app muss mindestens einen reservierten Namen aufweisen muss. Klicken Sie auf **diese app löschen** aus der **App** -Übersichtsseite, um vollständig entfernen einer app aus dem Dashboard (und die Namen, den, die Sie für diese app reserviert haben-Version). (Wenn die App in Bearbeitung eine Übermittlung enthält, müssen Sie diese zuerst löschen.) Beachten Sie, wenn Sie bereits im Speicher die app veröffentlicht haben, Sie es aus dem Dashboard nicht löschen (obwohl Sie die Funktionalität **Produkte einblenden/ausblenden** auf **der Übersichtsseite** auszublenden verwenden können). 


## <a name="rename-an-app-that-has-already-been-published"></a>Umbenennen einer bereits veröffentlichten App

Wenn Ihre App bereits im Store veröffentlicht wurde und Sie sie umbenennen möchten, können Sie dazu (mithilfe der oben beschriebenen Schritte) einen neuen Namen für die App reservieren und eine neue App-Übermittlung vornehmen. 

Aktualisieren Sie Ihre app-Pakete zum Ersetzen Sie den alten Namens durch den neuen und aktualisierten Pakete an Ihre Bereitstellung hochladen.
- Aktualisieren Sie zuerst die Package.StoreAssociation.xml-Datei, um den neuen Namen, verwenden Sie entweder manuell oder mithilfe von Visual Studio (**Projekt > Store > zuordnen App mit Store...**). Weitere Informationen finden Sie unter [Package eine UWP-app mit Visual Studio](../packaging/packaging-uwp-apps.md).
- Aktualisieren Sie ebenfalls das [**Package/Properties/DisplayName**](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-displayname)-Element im App-Manifest, und aktualisieren Sie Grafiken oder Texte, die den App-Namen enthalten. 
  > [!IMPORTANT]
  > Achten Sie darauf, dass Sie die Datei Package.StoreAssociation.xml aktualisieren, bevor Sie **Paket/Eigenschaften/Anzeigenname** im App-Manifest ändern, andernfalls erhalten Sie möglicherweise einen Fehler.

Um eine Store mit, dass den neuen Name verwendet zu aktualisieren, wechseln Sie zu der [Store Angebot Seite](create-app-store-listings.md) für die Sprache, und wählen Sie den Namen aus der Dropdownliste **Produktname** aus. Achten Sie darauf überprüfen Ihrer Beschreibung und andere Teile der Auflistung wird für alle Vorkommnisse des Namens und Updates bei Bedarf.

> [!NOTE]
> Wenn Ihre app-Pakete und/oder Store-Auflistungen in mehreren Sprachen verfügt, müssen Sie die System-Updatepakete und/oder speichern Auflistungen für jede Sprache, in dem der Name muss aktualisiert werden.

Nachdem Ihre app mit den neuen Namen veröffentlicht wurde, können Sie alle älteren Namen löschen, die Sie nicht mehr verwenden müssen.

> [!TIP]
> Jede app wird im Dashboard mit den Vornamen, das Sie vorbehalten angezeigt. Wenn Sie die oben beschriebenen Schritte zum Umbenennen einer app befolgt haben, und Sie in das Dashboard mithilfe des neuen Namens angezeigt werden soll möchten, müssen Sie den ursprünglichen Namen (durch Klicken auf " **Löschen** " auf der Seite **app-Namen verwalten** ) löschen. 

 

 




