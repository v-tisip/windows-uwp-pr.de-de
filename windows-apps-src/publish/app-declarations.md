---
author: jnHs
Description: Product declarations help make sure your app is displayed appropriately in the Microsoft Store and offered to the right set of customers.
title: Produktdeklarationen
ms.assetid: 3AF618F3-2B47-4A57-B7E8-1DF979D4A82C
ms.author: wdg-dev-content
ms.date: 10/31/2018
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: de519f37c5eacfa64f23d0f438701d4ae9dbc934
ms.sourcegitcommit: 3257416aebb5a7b1515e107866806f8bd57845a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2018
ms.locfileid: "7168515"
---
# <a name="product-declarations"></a>Produktdeklarationen

Im Abschnitt **produktdeklarationen** der [Eigenschaftenseite des [Übermittlungsprozesses](app-submissions.md) ](enter-app-properties.md) hilft dabei, stellen Sie sicher, Ihre app entsprechend angezeigt und die richtigen Kunden und hilft ihnen verstehen, wie sie Ihre app verwenden können angeboten wird.

Den folgenden Abschnitten werden einige der Deklarationen und was Sie bei der Entscheidung, ob sich eine Deklaration für Ihre app gilt berücksichtigen müssen. Beachten Sie, dass zwei dieser Deklarationen standardmäßig aktiviert sind (wie unten beschrieben). Je nach Kategorie des Produkts möglicherweise auch zusätzliche Deklarationen angezeigt. Achten Sie darauf, dass der Deklarationen überprüfen und sicherzustellen, dass sie Ihre Übermittlung genau widerspiegeln.

## <a name="this-app-allows-users-to-make-purchases-but-does-not-use-the-microsoft-store-commerce-system"></a>Diese app ermöglicht es Benutzern, Einkäufe zu tätigen, verwendet jedoch nicht des Microsoft Store-e-Commerce-Systems.

Nahezu jede Übermittlung sollten Sie diese Option deaktiviert lassen, seit apps, die Möglichkeiten zum Kauf anbieten müssen Elemente sind oder können genutzt oder innerhalb Ihrer app verwendet die Microsoft Store in-app-Einkaufs-API erstellen und Übermitteln von Add-ons verwenden. Gemäß der [Vereinbarung für App-Entwickler](https://docs.microsoft.com/legal/windows/agreements/app-developer-agreement)könnte apps, die erstellt und vor 29 Juni 2015 eingereicht wurden, weiterhin in-app-einkauffunktionalität anbieten, ohne Verwendung von Microsoft e-Commerce-Moduls, solange die einkaufsfunktionalität die [aber Microsoft Store-Richtlinien](https://docs.microsoft.com/legal/windows/agreements/store-policies#108-financial-transactions). Wenn dies auf Ihre App zutrifft, müssen Sie dieses Kontrollkästchen aktivieren. Lassen Sie das Kontrollkästchen andernfalls deaktiviert.

## <a name="this-app-has-been-tested-to-meet-accessibility-guidelines"></a>Diese App wurde auf Einhaltung der Richtlinien zur Barrierefreiheit getestet.

Wenn Sie dieses Kontrollkästchen aktivieren, kann die App von Kunden gefunden werden, die im Store speziell nach barrierefreien Apps suchen.

Sie sollten dieses Kontrollkästchen erst aktivieren, nachdem Sie die folgenden Schritte erledigt haben:

-   Alle relevanten Barrierefreiheitsinfos für UI-Elemente festlegen, z.B. barrierefreie Namen
-   Tastaturnavigation und -vorgänge unter Berücksichtigung der Registerkartenreihenfolge, Tastaturaktivierung, Navigation mit Pfeiltasten und Tastenkombinationen implementieren
-   Barrierefreie visuelle Darstellung sicherstellen, z. B. durch Berücksichtigen eines Textkontrastverhältnisses von 4,5:1 (und nicht nur durch die Verwendung farblich gekennzeichneter Informationen)
-   Tools zum Testen der Barrierefreiheit verwenden, z.B. Inspect oder AccChecker, um Ihre App zu überprüfen und alle von diesen Tools ermittelten Fehler mit hoher Priorität zu beheben
-   Die wichtigsten Szenarien der App unter Verwendung von Funktionen und Tools wie „Sprachausgabe“, „Bildschirmlupe“, „Bildschirmtastatur“, „Hoher Kontrast“ und „Hoher DPI-Wert“ vollständig überprüfen

Wenn Sie Ihre App als barrierefrei ausweisen, erklären Sie ausdrücklich, dass Ihre App eine Barrierefreiheit für alle Kunden aufweist, einschließlich für Personen mit Behinderungen. Das bedeutet beispielsweise, dass Sie die App im Modus mit hohem Kontrast und die Sprachausgabe getestet haben. Sie haben außerdem sichergestellt, dass die Benutzeroberfläche ordnungsgemäß mit der Tastatur, der Bildschirmlupe und weiteren Tools zur Unterstützung der Barrierefreiheit funktioniert.

Weitere Informationen finden Sie unter [Eingabehilfen](../design/accessibility/accessibility.md), [zum Testen der Barrierefreiheit](../design/accessibility/accessibility-testing.md)und [Barrierefreiheit im Store](../design/accessibility/accessibility-in-the-store.md).

> [!IMPORTANT]
> Weisen Sie die App nur dann als barrierefrei aus, wenn Sie sie ausdrücklich für diesen Zweck entwickelt und getestet haben. Falls Ihre App als barrierefrei ausgewiesen ist, jedoch eigentlich keine Barrierefreiheit unterstützt, werden Sie wahrscheinlich negatives Feedback von der Community erhalten.

## <a name="customers-can-install-this-app-to-alternate-drives-or-removable-storage"></a>Kunden können diese App auf alternativen Laufwerken oder Wechselmedien installieren.

Dieses Kontrollkästchen ist standardmäßig aktiviert, damit Kunden Ihre app auf externen oder auf Wechseldatenträgern installieren können z. B. einer SD-Karte oder auf einem systemfremden Volumelaufwerk wie einem externen Laufwerk.

Wenn Sie verhindern, dass Ihre app auf alternativen Laufwerken oder Wechselmedien installiert wird, und nur die Installation auf die interne Festplatte auf dem Gerät zulassen möchten, deaktivieren Sie dieses Kontrollkästchen. (Beachten Sie, dass es ist keine Option zum Einschränken der Installation eine app kann *nur* installiert werden auf Wechselmedien.)


## <a name="windows-can-include-this-apps-data-in-automatic-backups-to-onedrive"></a>Windows kann die Daten dieser App in automatische Sicherungen auf OneDrive einschließen.

Dieses Kontrollkästchen ist standardmäßig aktiviert, damit die Daten Ihrer App eingeschlossen werden können, wenn ein Kunde automatische OneDrive-Sicherungen von Windows erstellen lässt.

Wenn Sie verhindern möchten, dass die App-Daten in automatische Sicherungen eingeschlossen werden, deaktivieren Sie das Kontrollkästchen.


## <a name="this-app-sends-kinect-data-to-external-services"></a>Diese app sendet Kinect-Daten an externe Dienste. 

Wenn Ihre app Kinect-Daten verwendet und sie an einen externen Dienst sendet, müssen Sie dieses Kontrollkästchen aktivieren.



 

 

 




