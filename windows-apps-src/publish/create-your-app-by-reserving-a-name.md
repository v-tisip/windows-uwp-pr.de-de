---
author: jnHs
Description: The first step in creating a new app in your Windows Dev Center dashboard is reserving an app name. See how to reserve app names and find suggestions for choosing a great name for your app.
title: Erstellen einer App durch Reservieren eines Namens
keywords: Windows10, UWP, Namen reservieren, App-Name, App-Namen, Namen, Produktname, benennen
ms.assetid: 6DC58A9A-DF47-4652-8D13-0AC9289F5950
ms.author: wdg-dev-content
ms.date: 01/22/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
ms.localizationpriority: high
ms.openlocfilehash: 960acceb9f665b9d2f2d1def680626876c3aa29b
ms.sourcegitcommit: b6915c7fa2c7292e9b4e3d3e9927dc8746ec1ffb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2018
---
# <a name="create-your-app-by-reserving-a-name"></a>Erstellen einer App durch Reservieren eines Namens


Der erste Schritt beim Erstellen einer neuen App im Windows Dev Center-Dashboard besteht darin, einen App-Namen zu reservieren. In diesem Thema wird erläutert, wie Sie App-Namen reservieren. Es enthält einige [Vorschläge zur Wahl aussagekräftiger App-Namen](#choosing-your-apps-name). Jeder reservierter Name muss im gesamten Microsoft Store eindeutig sein.

Wenn Sie Ihre [App-Pakete hochladen](upload-app-packages.md), muss der [**Package/Properties/DisplayName**](https://docs.microsoft.com/uwp/schemas/appxpackage/appxmanifestschema/element-1-displayname) -Wert dem Namen entsprechen, den Sie für Ihre App reserviert haben. Wenn Sie das App-Paket mit MicrosoftVisual Studio erstellen, wird dieses Attribut für Sie ausgefüllt.

## <a name="create-your-app-by-reserving-a-new-name"></a>App-Erstellung durch Reservierung eines neuen Namens

Das Reservieren eines Namens ist der erste Schritt bei der App-Erstellung im Dashboard. Die Reservierung ist möglich, auch wenn Sie noch nicht mit der App-Erstellung begonnen haben. Wir empfehlen, die Reservierung so früh wie möglich vorzunehmen, damit der Name nicht von jemand anderem verwendet wird.

1.  Klicken Sie auf der Seite **Übersicht** auf **Neue App erstellen**.
2.  Geben Sie im Textfeld den Namen ein, den Sie verwenden möchten, und wählen Sie dann **Verfügbarkeit überprüfen**. Wenn der Name verfügbar ist, wird ein grünes Häkchen angezeigt. (Ist der von Ihnen eingegebene Name bereits reserviert oder wird von einem anderen Entwickler verwendet, wird eine Fehlermeldung angezeigt, dass der Name nicht verfügbar ist.)
3.  Klicken Sie auf **Produktnamen reservieren**.

Der Name ist jetzt für Sie reserviert, und Sie können mit der [Einreichung](app-submissions.md) beginnen, sobald Sie dazu bereit sind.

> [!NOTE]
> Vielleicht können Sie einen Namen nicht reservieren, obwohl keine Apps mit diesem Namen im Microsoft Store gelistet sind. Das liegt normalerweise daran, dass ein anderer Entwickler den Namen für seine App reserviert, aber die entsprechende App noch nicht eingereicht hat. Wenn Sie einen Namen, den Sie markenrechtlich oder anderweitig geschützt haben, nicht reservieren können oder im MicrosoftStore eine andere App mit diesem Namen entdecken, [wenden Sie sich an Microsoft](http://go.microsoft.com/fwlink/p/?LinkId=233777).

Nach dem Reservieren eines Namens haben Sie ein Jahr Zeit, um die App einzureichen. Wenn Sie sie nicht innerhalb eines Jahres einreichen, läuft die Reservierung des Namens ab, und ein anderer Entwickler kann eventuell den Namen für seine App verwenden. Wenn Sie versuchen, eine App unter einem abgelaufenen Namen einzureichen, tritt ein Fehler auf.

> [!NOTE]
> Wenn Sie über eine bereits in einem älteren Windows Phone-Dashboard erstellte Windows Phone-App verfügen, für die noch kein Name reserviert wurde, müssen Sie dies jetzt tun, um AppX-Pakete dafür hochladen zu können oder zum [Anzeigen von Details zur App-Identität](view-app-identity-details.md). Durch das Reservieren des Namens wird außerdem verhindert, dass eine andere Person diesen Namen für sich selbst reserviert. Wenn Sie keinen Namen reservieren, können Sie die App für Ihre Windows Phone8.x-Kunden trotzdem verwalten und übermitteln.


## <a name="choosing-your-apps-name"></a>Auswählen des App-Namens

Es ist sehr wichtig, für Ihre App den richtigen Namen auszuwählen. Wählen Sie einen Namen, der die Aufmerksamkeit von Kunden auf sich zieht und diese dazu animiert, sich ausführlicher über Ihre App zu informieren. Hier sind ein paar Tipps zum Auswählen eines geeigneten App-Namens.

-   **Halten Sie den Namen kurz.** Für die Anzeige des App-Namens ist meist nur wenig Platz – lassen Sie sich also einen möglichst kurzen Namen einfallen. Der Name der App kann bis zu 256Zeichen haben, aber möglicherweise ist das Ende eines sehr langen Namens für Kunden nicht immer sichtbar.

   > [!NOTE]
   > Die tatsächliche Anzahl von an unterschiedlichen Stellen angezeigten Zeichen kann je nach zugewiesener Länge und im App-Namen verwendetem Zeichentyp variieren. So benötigen beispielsweise in der von Windows verwendeten Schriftart „SegoeUI“ etwa 30I-Zeichen genauso viel Platz wie zehn W-Zeichen. Sie sollten die App aufgrund dieser Abweichungen also auf jeden Fall testen und prüfen, wie der Name auf den Kacheln (falls Sie sich für die Überlagerung mit dem App-Namen entscheiden), in Suchergebnissen und in der App selbst angezeigt wird, bevor Sie die App einreichen. Berücksichtigen Sie auch die Sprachen, in denen Sie die App anbieten möchten. Denken Sie daran, dass ostasiatische Zeichen im Allgemeinen breiter sind als lateinische Zeichen, sodass weniger Zeichen angezeigt werden.

-   **Seien Sie unverwechselbar.** Suchen Sie einen eindeutigen App-Namen aus, damit die App nicht so leicht mit einer anderen App verwechselt werden kann.
-   **Verwenden Sie keine von anderen geschützten Namen.** Stellen Sie sicher, dass sie zum Verwenden des reservierten Namens berechtigt sind. Wurde der Name als Marke eingetragen, kann ein Verstoß gemeldet werden, und Sie dürfen den Namen nicht weiter verwenden. Geschieht dies nach der Veröffentlichung Ihrer App, wird sie aus dem Store entfernt. Sie müssen dann den Namen der App sowie alle Vorkommen des Namens innerhalb Ihrer App und der zugehörigen Inhalte ändern, bevor Sie [die App erneut zur Zertifizierung einreichen](app-submissions.md).
-   **Fügen Sie Informationen zur Unterscheidung nicht am Ende des Namens hinzu.** Wenn Infos zur Unterscheidung mehrerer Apps am Ende eines Namens angefügt werden, werden sie von den Kunden vor allem bei langen Namen vielleicht übersehen, und es scheint, als hätten alle Apps den gleichen Namen. Falls sich dies nicht vermeiden lässt, verwenden Sie unterschiedliche Logos und App-Bilder, um die Unterscheidung zwischen Apps zu erleichtern.
-   **Verwenden Sie in Ihrem Namen keine Emoticons.** Sie können keinen Namen reservieren, der Emoticons oder andere nicht unterstützte Zeichen enthält.


## <a name="manage-additional-app-names"></a>Verwalten zusätzlicher App-Namen

Auf der Seite **Verwalten von App-Namen** im Abschnitt **App-Verwaltung** für jede der Apps im Windows Dev Center-Dashboard können Sie zusätzliche Namen für die Apps hinzufügen und verwalten.

In einigen Fällen möchten Sie u. U. mehrere Namen reservieren, die für dieselbe App verwendet werden sollen; beispielsweise wenn Sie Ihre App unter verschiedenen Namen für jede Sprache anbieten möchten. Sie müssen einen zusätzlichen Namen reservieren, wenn Sie den Namen einer App vollständig ändern möchten.

Auf dieser Seite können Sie auch reservierte Namen, die Sie nicht mehr verwenden, löschen.

Weitere Informationen finden Sie unter [Verwalten von App-Namen](manage-app-names.md).

 

 




