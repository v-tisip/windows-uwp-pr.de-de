---
author: jnHs
Description: "Zeigen Sie die Namen an, die Sie für Ihre App reserviert haben, reservieren Sie zusätzliche Namen (für andere Sprachen oder um den Namen Ihrer App zu ändern), und löschen Sie reservierte Namen, die Sie nicht mehr benötigen."
title: Verwalten von App-Namen
ms.assetid: D95A6227-746E-4729-AE55-648A7102401C
ms.author: wdg-dev-content
ms.date: 06/28/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: 539ccc671ae3f66c6c17a077ac1c09d989d86fdc
ms.sourcegitcommit: d2ec178103f49b198da2ee486f1681e38dcc8e7b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/28/2017
---
# <a name="manage-app-names"></a>Verwalten von App-Namen


Sie können alle Namen anzeigen, die Sie für Ihre App reserviert haben, zusätzliche Namen reservieren (für andere Sprachen oder um den Namen Ihrer App zu ändern) und Namen löschen, die Sie nicht benötigen. Hierfür navigieren Sie zur Seite **App-Namen verwalten** im Abschnitt **App-Verwaltung** für alle Ihre Apps im Windows Dev Center-Dashboard.

## <a name="reserve-additional-names-for-your-app"></a>Reservieren zusätzlicher Namen für Ihre App

Sie können mehrere App-Namen reservieren, die für dieselbe App verwendet werden. Dies ist besonders hilfreich, wenn Sie Ihre App in mehreren Sprachen anbieten und für die verschiedenen Sprachen unterschiedliche Namen verwenden möchten. Sie können auch einen neuen Namen reservieren, um den Namen einer App zu ändern.

Im Abschnitt **Weitere Namen reservieren** der Seite **App-Namen verwalten** sehen Sie ein Textfeld. Geben Sie den zu reservierenden Namen ein, und klicken Sie auf **Verfügbarkeit überprüfen**. Wenn der Name verfügbar ist, klicken Sie auf **Produktnamen reservieren**.

> [!NOTE]
> Weitere Informationen zum Reservieren von App-Namen und den Gründen, warum ein bestimmter Name u. U. nicht verfügbar ist, finden Sie unter [App-Erstellung durch Reservierung eines Namens](create-your-app-by-reserving-a-name.md).

Bei Bedarf können Sie hier weitere App-Namen reservieren.

## <a name="delete-app-names"></a>Löschen von App-Namen

Wenn Sie einen zuvor reservierten Namen nicht mehr verwenden möchten, können Sie ihn wieder freigeben, indem Sie ihn hier löschen. Überlegen Sie sich Ihre Entscheidung genau, da der Name danach sofort von einer anderen Person reserviert und verwendet werden kann.

Um einen reservierten Namen Ihrer App zu löschen, suchen Sie den nicht mehr verwendeten Namen, und klicken Sie auf **Löschen**. Klicken Sie im Bestätigungsdialogfeld erneut auf **Löschen**, um den Vorgang zu bestätigen.

Beachten Sie, dass Ihre App mindestens einen reservierten Namen aufweisen muss. Um eine App vollständig aus Ihrem Dashboard zu entfernen (und auch alle für diese App reservierten Namen freizugegeben), klicken Sie auf der Seite **App-Übersicht** auf **Diese App löschen**. (Wenn die App in Bearbeitung eine Übermittlung enthält, müssen Sie diese zuerst löschen.) Wenn Sie die App bereits im Store veröffentlicht haben, können Sie sie nicht vom Dashboard löschen (Sie können sie allerdings mit der Funktionen **Produkte einblenden/ausblenden** in der **Übersicht** ausgeblendet). 

## <a name="rename-an-app-that-has-already-been-published"></a>Umbenennen einer bereits veröffentlichten App

Wenn Ihre App bereits im Store veröffentlicht wurde und Sie sie umbenennen möchten, können Sie dazu (mithilfe der oben beschriebenen Schritte) einen neuen Namen für die App reservieren und eine neue App-Übermittlung vornehmen.

Sie müssen die Paket der App aktualisieren, um den neuen Namen einzuschließen. Nur so wird die App unter dem neuen Namen im Store angezeigt. Aktualisieren Sie zuerst die Package.StoreAssociation.xml-Datei, um den neuen Namen, entweder manuell oder mithilfe von Visual Studio, zu verwenden (**Projekt > Store > App mit Store verknüpfen **). Weitere Informationen finden Sie unter [Verpacken von UWP-Apps](../packaging/packaging-uwp-apps.md).

Aktualisieren Sie ebenfalls das [**Package/Properties/DisplayName**](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-1-displayname)-Element im App-Manifest, und aktualisieren Sie Grafiken oder Texte, die den App-Namen enthalten. 

> [!IMPORTANT]
> Achten Sie darauf, dass Sie die Datei Package.StoreAssociation.xml aktualisieren, bevor Sie **Paket/Eigenschaften/Anzeigenname** im App-Manifest ändern, andernfalls erhalten Sie möglicherweise einen Fehler.

Sie können auch den Store- Eintrag Ihrer App überprüfen und den Namen, falls er an anderer Stelle erwähnt wird, ändern. Nachdem Ihre App unter dem neuen Namen veröffentlicht wurde, können Sie den alten, nicht mehr verwendeten Namen löschen.

 

 




