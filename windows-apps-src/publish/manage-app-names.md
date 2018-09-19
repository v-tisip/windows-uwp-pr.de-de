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
keywords: Windows 10, Uwp, app-Namen ändern, app-Namen, Namen der Update-app, Spiel Namen, Produktname
ms.localizationpriority: medium
ms.openlocfilehash: f0d2c6f72e2f69f0b768af55f9bddeb9bb008027
ms.sourcegitcommit: 68fcac3288d5698a13dbcbd57f51b30592f24860
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2018
ms.locfileid: "4060190"
---
# <a name="manage-app-names"></a>Verwalten von App-Namen

Mit dem **app-Namen verwalten** können Sie alle Namen anzeigen, die Sie für Ihre app reserviert haben zusätzliche Namen reservieren (für andere Sprachen oder um den Namen Ihrer app zu ändern), und löschen die Namen, die Sie nicht benötigen. Finden Sie auf dieser Seite im [Windows Dev Center-Dashboard](https://partner.microsoft.com/dashboard) , indem Sie erweitern im linken Navigationsmenü für alle Ihre apps Abschnitt **App-Verwaltung** .


## <a name="reserve-additional-names-for-your-app"></a>Reservieren zusätzlicher Namen für Ihre App

Sie können mehrere App-Namen reservieren, die für dieselbe App verwendet werden. Dies ist besonders hilfreich, wenn Sie Ihre App in mehreren Sprachen anbieten und für die verschiedenen Sprachen unterschiedliche Namen verwenden möchten. Sie können auch einen neuen Namen reservieren, um den Namen einer App ändern wie unten beschrieben.

Um einen neuen app-Namen reservieren, finden Sie das Textfeld im Abschnitt der Seite **app-Namen verwalten** **Weitere Namen reservieren** . Geben Sie den zu reservierenden Namen ein, und klicken Sie auf **Verfügbarkeit überprüfen**. Wenn der Name verfügbar ist, klicken Sie auf **Produktnamen reservieren**. Wenn gewünscht, können Sie mehrere app-Namen reservieren, indem Sie diese Schritte wiederholen.

> [!NOTE]
> Weitere Informationen zum Reservieren von App-Namen und den Gründen, warum ein bestimmter Name u. U. nicht verfügbar ist, finden Sie unter [App-Erstellung durch Reservierung eines Namens](create-your-app-by-reserving-a-name.md).


## <a name="delete-app-names"></a>Löschen von App-Namen

Wenn Sie einen zuvor reservierten Namen nicht mehr verwenden möchten, können Sie ihn wieder freigeben, indem Sie ihn hier löschen. Überlegen Sie sich Ihre Entscheidung genau, da der Name danach sofort von einer anderen Person reserviert und verwendet werden kann.

Um einen reservierten Namen Ihrer App zu löschen, suchen Sie den nicht mehr verwendeten Namen, und klicken Sie auf **Löschen**. Klicken Sie im Bestätigungsdialogfeld erneut auf **Löschen**, um den Vorgang zu bestätigen.

Beachten Sie, dass Ihre app mindestens einen reservierten Namen aufweisen muss. Um vollständig eine app aus Ihrem Dashboard entfernen (und alle für diese app reservierten Namen freizugeben), klicken Sie in der **App-Übersicht** auf **diese app löschen** . (Wenn die App in Bearbeitung eine Übermittlung enthält, müssen Sie diese zuerst löschen.) Beachten Sie, wenn Sie die app bereits im Store veröffentlicht haben, Sie es aus Ihrem Dashboard nicht löschen (Wenn Sie die **Produkte einblenden/ausblenden** -Funktionalität auf **der Übersichtsseite** ausgeblendet verwenden können). 


## <a name="rename-an-app-that-has-already-been-published"></a>Umbenennen einer bereits veröffentlichten App

Wenn Ihre App bereits im Store veröffentlicht wurde und Sie sie umbenennen möchten, können Sie dazu (mithilfe der oben beschriebenen Schritte) einen neuen Namen für die App reservieren und eine neue App-Übermittlung vornehmen. 

Aktualisieren Sie Ihre app-Pakete zum Ersetzen des alten Namens durch das neue und aktualisierte Pakete für Ihre Übermittlung hochladen.
- Aktualisieren Sie zuerst die Package.StoreAssociation.xml-Datei, um den neuen Namen, entweder manuell oder mithilfe von Visual Studio verwenden (**Projekt > Store > App mit dem Store... verknüpfen**). Weitere Informationen finden Sie unter [Paket eine UWP-app mit Visual Studio](../packaging/packaging-uwp-apps.md).
- Aktualisieren Sie ebenfalls das [**Package/Properties/DisplayName**](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-displayname)-Element im App-Manifest, und aktualisieren Sie Grafiken oder Texte, die den App-Namen enthalten. 
  > [!IMPORTANT]
  > Achten Sie darauf, dass Sie die Datei Package.StoreAssociation.xml aktualisieren, bevor Sie **Paket/Eigenschaften/Anzeigenname** im App-Manifest ändern, andernfalls erhalten Sie möglicherweise einen Fehler.

Um eine Store-Eintrag, dass der neue Name verwendet zu aktualisieren, öffnen Sie die [Store-Eintragsseite](create-app-store-listings.md) für die jeweilige Sprache, und wählen Sie den Namen aus der Dropdownliste, **Produktname** . Achten Sie darauf, um zu überprüfen, die Beschreibung und andere Teile der Eintrag für alle ist der der Name und führen Sie Updates bei Bedarf.

> [!NOTE]
> Wenn Ihre app Pakete und/oder Store-Einträge in mehreren Sprachen enthält, müssen Sie die Pakete aktualisieren und/oder Store-Einträge für jede Sprache, in dem der Name muss aktualisiert werden.

Nachdem Ihre app mit dem neuen Namen veröffentlicht wurde, können Sie alle älteren Namen löschen, die Sie nicht mehr verwenden müssen.

> [!TIP]
> Jede app wird in Ihrem Dashboard mit den Vornamen, die Sie für sie reserviert. Wenn Sie die oben beschriebenen Schritte zum Benennen Sie einer app befolgt haben, und Sie es in Ihrem Dashboard mit dem neuen Namen angezeigt werden möchten, müssen Sie den ursprünglichen Namen löschen, (durch Klicken auf " **Löschen** " auf der Seite " **app-Namen verwalten** "). 

 

 




