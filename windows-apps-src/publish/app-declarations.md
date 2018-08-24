---
author: jnHs
Description: Product declarations help make sure your app is displayed appropriately in the Microsoft Store and offered to the right set of customers.
title: Produktdeklarationen
ms.assetid: 3AF618F3-2B47-4A57-B7E8-1DF979D4A82C
ms.author: wdg-dev-content
ms.date: 12/05/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 959e056d5edf5e1fe7a1c51a2f855c9e11512cb0
ms.sourcegitcommit: c6d6f8b54253e79354f8db14e5cf3b113a3e5014
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "2839657"
---
# <a name="product-declarations"></a>Produktdeklarationen

**Produkt** Deklarationsabschnitt der [Eigenschaftenseite des [den Prozess zum Absenden](app-submissions.md) ](enter-app-properties.md) kann, stellen Sie sicher, Ihre app entsprechend angezeigt und Angeboten den richtigen Satz von Kunden und hilft ihnen verstehen, wie sie Ihre app verwenden können.

In den folgenden Abschnitten werden einige der Deklarationen und was Sie benötigen, beachten Sie beim bestimmen, ob jede Deklaration für Ihre app gilt beschrieben. Beachten Sie, dass zwei dieser Deklarationen standardmäßig überprüft werden (siehe die nachfolgende Beschreibung). Je nach Ihrer Produktkategorie sehen Sie auch zusätzliche Deklarationen. Achten Sie darauf, überprüfen Sie die Deklarationen und sicherstellen, dass sie Ihre Bereitstellung genau widerspiegeln.

## <a name="this-app-allows-users-to-make-purchases-but-does-not-use-the-microsoft-store-commerce-system"></a>Diese app ermöglicht es Benutzern, Einkäufe tätigen, aber Microsoft Store-Commerce-System wird nicht verwendet.

Für die fast jeder Übermittlung sollten Sie dieses Kontrollkästchen deaktiviert lassen, seit apps, die Möglichkeiten zum Kauf anbieten müssen Elementen, die sind oder können verbraucht oder Ihrer App verwendet den Microsoft Store-app-Einkauf API verwenden, um erstellen und senden die Add-ons. Pro [App Developer Vereinbarung](https://docs.microsoft.com/legal/windows/agreements/app-developer-agreement)konnte apps, die erstellt und vor dem 29 Juni 2015 übermittelt wurden weiterhin-app-Einkauf Funktionen anbieten ohne Verwendung von Microsoft Commerce-Moduls, solange die Bestellung Funktionalität der [entspricht Richtlinien für Microsoft](https://docs.microsoft.com/legal/windows/agreements/store-policies#108-financial-transactions). Wenn dies auf Ihre App zutrifft, müssen Sie dieses Kontrollkästchen aktivieren. Lassen Sie das Kontrollkästchen andernfalls deaktiviert.

## <a name="this-app-has-been-tested-to-meet-accessibility-guidelines"></a>Diese App wurde auf Einhaltung der Richtlinien zur Barrierefreiheit getestet.

Wenn Sie dieses Kontrollkästchen aktivieren, kann die App von Kunden gefunden werden, die im Store speziell nach barrierefreien Apps suchen.

Sie sollten dieses Kontrollkästchen erst aktivieren, nachdem Sie die folgenden Schritte erledigt haben:

-   Alle relevanten Barrierefreiheitsinfos für UI-Elemente festlegen, z.B. barrierefreie Namen
-   Tastaturnavigation und -vorgänge unter Berücksichtigung der Registerkartenreihenfolge, Tastaturaktivierung, Navigation mit Pfeiltasten und Tastenkombinationen implementieren
-   Barrierefreie visuelle Darstellung sicherstellen, z. B. durch Berücksichtigen eines Textkontrastverhältnisses von 4,5:1 (und nicht nur durch die Verwendung farblich gekennzeichneter Informationen)
-   Tools zum Testen der Barrierefreiheit verwenden, z.B. Inspect oder AccChecker, um Ihre App zu überprüfen und alle von diesen Tools ermittelten Fehler mit hoher Priorität zu beheben
-   Die wichtigsten Szenarien der App unter Verwendung von Funktionen und Tools wie „Sprachausgabe“, „Bildschirmlupe“, „Bildschirmtastatur“, „Hoher Kontrast“ und „Hoher DPI-Wert“ vollständig überprüfen

Wenn Sie Ihre App als barrierefrei ausweisen, erklären Sie ausdrücklich, dass Ihre App eine Barrierefreiheit für alle Kunden aufweist, einschließlich für Personen mit Behinderungen. Das bedeutet beispielsweise, dass Sie die App im Modus mit hohem Kontrast und die Sprachausgabe getestet haben. Sie haben außerdem sichergestellt, dass die Benutzeroberfläche ordnungsgemäß mit der Tastatur, der Bildschirmlupe und weiteren Tools zur Unterstützung der Barrierefreiheit funktioniert.

Weitere Informationen finden Sie unter [Eingabehilfen](../design/accessibility/accessibility.md), [Eingabehilfen testen](../design/accessibility/accessibility-testing.md)und [Eingabehilfen im Speicher](../design/accessibility/accessibility-in-the-store.md).

> [!IMPORTANT]
> Weisen Sie die App nur dann als barrierefrei aus, wenn Sie sie ausdrücklich für diesen Zweck entwickelt und getestet haben. Falls Ihre App als barrierefrei ausgewiesen ist, jedoch eigentlich keine Barrierefreiheit unterstützt, werden Sie wahrscheinlich negatives Feedback von der Community erhalten.

## <a name="customers-can-install-this-app-to-alternate-drives-or-removable-storage"></a>Kunden können diese App auf alternativen Laufwerken oder Wechselmedien installieren.

In diesem Feld wird in der Standardeinstellung können Kunden Ihre app auf externe oder austauschbaren Speicher installieren, die Media wie etwa einer SD-Karte oder auf einen Systemdatenträger wie ein externes Laufwerk Laufwerk überprüft. (Für Windows Phone 8.1, wurde dieser zuvor über StoreManifest.xml angezeigt.)

Wenn Sie verhindern, dass Ihre app auf alternative Laufwerke oder Wechselspeicher installiert wird und Installation auf die interne Festplatte auf ihrem Gerät nur zulassen möchten, deaktivieren Sie dieses Kontrollkästchen.

Beachten Sie, dass es keine Option Installation einschränken gibt, sodass eine app kann *nur* werden auf Speichermedien installiert.


## <a name="windows-can-include-this-apps-data-in-automatic-backups-to-onedrive"></a>Windows kann die Daten dieser App in automatische Sicherungen auf OneDrive einschließen.

Dieses Kontrollkästchen ist standardmäßig aktiviert, damit die Daten Ihrer App eingeschlossen werden können, wenn ein Kunde automatische OneDrive-Sicherungen von Windows erstellen lässt. (Für Windows Phone 8.1, wurde dieser zuvor über StoreManifest.xml angezeigt.)

Wenn Sie verhindern möchten, dass die App-Daten in automatische Sicherungen eingeschlossen werden, deaktivieren Sie das Kontrollkästchen.


## <a name="this-app-sends-kinect-data-to-external-services"></a>Diese app sendet Kinect Daten an externe Dienste an. 

Wenn Ihre app Kinect Daten verwendet und ihn an einen externen Dienst sendet, müssen Sie dieses Kontrollkästchen.



 

 

 




