---
Description: After your packages have been successfully uploaded, you'll see a table that indicates which packages will be offered to specific Windows 10 device families (and earlier OS versions, if applicable), in ranked order.
title: Verfügbarkeit von Gerätefamilien
ms.date: 10/31/2018
ms.topic: article
keywords: Windows10, UWP, Pakete, hochladen, Verfügbarkeit von Gerätefamilien
ms.localizationpriority: medium
ms.openlocfilehash: 217a6ab9f25ee533a754138db5cf83c2ac81e3e9
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8893550"
---
# <a name="device-family-availability"></a>Verfügbarkeit von Gerätefamilien

Nachdem die Pakete von der Seite **Pakete** erfolgreich hochgeladen wurden, wird im Abschnitt **Gerätefamilienverfügbarkeit** eine Tabelle angezeigt, die angibt, welche Pakete für bestimmte Windows10-Gerätefamilien (und ggf. für frühere Betriebssystemversionen) angeboten werden. In diesem Abschnittkönnen Sie auswählen, ob die Übermittlung Kunden mit bestimmten Windows10-Gerätefamilien angeboten werden soll oder nicht.

> [!NOTE]
> Nachdem die Pakete erfolgreich hochgeladen wurden, wird im Abschnitt **Gerätefamilienverfügbarkeit** eine Tabelle mit Kontrollkästchen der Gerätefamilie von Windows 10 angezeigt, die Ihnen ermöglicht anzugeben, ob die Übermittlung Kunden auf diesen Gerätefamilien angeboten werden soll. Diese Tabelle wird angezeigt, nachdem Sie ein oder mehrere Pakete hochgeladen haben.

Dieser Bereich enthält ein Kontrollkästchen, in dem Sie angeben können, ob Microsoft die App allen zukünftigen Windows 10-Gerätefamilien zur Verfügung stellen soll. Es wird empfohlen, diese Option aktiviert zu lassen, sodass Ihre App für mehr potenzielle Kunden zur Verfügung gestellt wird, wenn neue Gerätefamilien eingeführt werden.


## <a name="choosing-which-device-families-to-support"></a>Auswählen der unterstützten Gerätefamilien

Wenn Sie Pakete für eine einzelne Gerätefamilie hochladen, wird das Kontrollkästchen aktiviert, um diese Pakete den neuen Kunden zur Verfügung zu stellen, die über diesen Gerätetyp verfügen. Wenn ein Paket z. B. auf Windows.Desktop ausgerichtet ist, ist das Kontrollkästchen **Windows10 Desktop** für dieses Paket aktiviert (Sie können kein anderes Kontrollkästchen für andere Gerätefamilien aktivieren).

Pakete, die auf die Gerätefamilie Windows.Universal abzielen, können auf jedem Windows10-Gerät (einschließlich Xbox One) ausgeführt werden. Wir stellen diese Pakete standardmäßig neuen Kunden auf allen Gerätetypen *außer* für Xbox zur Verfügung.

Sie können das Kontrollkästchen für eine Windows10-Gerätefamilie deaktivieren, wenn Sie Kunden auf diesem Gerät keine Übermittlung anbieten möchten. Wenn das Kontrollkästchen für eine Gerätefamilie deaktiviert ist, können neue Kunden die App auf diesem Gerätetyp nicht erwerben (Kunden, die bereits über die App verfügen, können diese allerdings weiterhin nutzen und erhalten alle von Ihnen übermittelten Aktualisierungen).

Wenn Ihre App dies unterstützt, empfehlen wir, diese Kontrollkästchen hier aktiviert zu lassen, es sei denn, Sie möchten aus einem bestimmten Grund die Windows 10-Gerätetypen einschränken, die Ihre App erwerben können. Wenn Sie beispielsweise wissen, dass Ihre App kein hohes Maß an Benutzerfreundlichkeit auf [Surface Hub](https://developer.microsoft.com/windows/surfacehub) und/oder [Microsoft HoloLens](https://developer.microsoft.com/windows/mixed-reality) bietet, deaktivieren Sie das Kontrollkästchen **Windows10 Team** und/oder **Windows10 Holographic**. Dadurch wird verhindert, dass neuen Kunden die App auf diesen Geräten erwerben. Wenn Sie die App später für diese Kunden anbieten möchten, können Sie eine neue Übermittlung Erstellen, bei der die Kontrollkästchen aktiviert sind.

<span id="xbox" />

Ist die einzige Windows10-Gerätefamilie, die für Windows.Universal Pakete standardmäßig nicht aktiviert ist, ist **Windows10 Xbox**. Wenn Ihre App kein Spiel ist (oder wenn sie ein Spiel ist und Sie das [Xbox Live Creators-Programm](../xbox-live/get-started-with-creators/get-started-with-xbox-live-creators.md) aktiviert haben oder die [Konzeptgenehmigung](../gaming/concept-approval.md) durchlaufen haben), und Ihre Übermittlung neutrale und/oder x64-UWP-Pakete enthält, die mit Windows10 SDK Version 14393 kompiliert wurden, können Sie das Kontrollkästchen Windows10 Xbox aktivieren, wenn Sie die App Kunden auf **Windows 10 Xbox** anbieten möchten.

> [!IMPORTANT]
> Ihre App kann nur dann auf Xbox-Geräten gestartet werden, wenn sie ein mit Windows SDK Version 14393 oder höher kompiliertes neutrales oder x64-Paket enthält. Wenn Sie **Windows10 Xbox** aktivieren, wird ein für Xbox geeignete Paket mit der Versionsnummer (d.h., ein neutrales oder x64 Paket, das für die Gerätefamilien „Xbox“ oder „Universell“ bestimmt ist) Kunden auf Xbox jedoch immer angeboten – auch dann, wenn es mit einer früheren Version des SDK kompiliert wurde. Daher müssen Sie unbedingt sicherstellen, dass das für Xbox geeignete Paket mit der höchsten Versionsnummer mit Windows SDK-Version 14393 oder höher kompiliert wurde. Andernfalls wird eine Fehlermeldung angezeigt, in der darauf hingewiesen wird, dass Xbox-Kunden die App nicht starten können. 
> 
> Um diesen Fehler zu beheben, können Sie einen der folgenden Schritteausführen:
> - Ersetzen Sie die entsprechenden Pakete durch neue, die mit Windows SDK-Version 14393 oder höher kompiliert wurden.
> - Wenn Sie bereits über ein Paket verfügen, das Xbox unterstützt und mit Windows SDK-Version 14393 oder höher kompiliert wurde, erhöhen Sie die Versionsnummer, sodass dieses Paket die höchste Versionsnummer innerhalb der Übermittlung trägt.
> - Deaktivieren Sie das Kontrollkästchen für **Windows10 Xbox**.
>   
> Wenn Sie das Problem immer noch nicht beheben können, wenden Sie sich an den Support.

Wenn Sie eine UWP-App für Windows10 IoT Core übermitteln, sollten Sie nach dem Hochladen der Pakete die Standardauswahl nicht ändern. Es gibt kein separates Kontrollkästchen für Windows10 IoT. Weitere Informationen zum Veröffentlichen von IoT Core-UWP-Apps finden Sie unter [Microsoft Store-Unterstützung für IoT Core UWP-Apps](https://docs.microsoft.com/windows/iot-core/commercialize-your-device/installingandservicing).

Wenn Ihre Übermittlung für eine bereits veröffentlichte app Pakete enthält, die auf **Windows 8/8.1** ausgeführt werden kann und **Windows Phone 8.x und früheren Versionen**, diese Pakete verfügbar gemacht werden für Kunden unter diesen Betriebssystemversionen. Wenn Sie das Angebot der App für diese Kunden beenden möchten, entfernen Sie die entsprechenden Pakete aus Ihrer Übermittlung.

> [!IMPORTANT]
> Um vollständig eine bestimmte Windows 10-Gerätefamilie verhindern können, dass Ihre Übermittlung, aktualisieren Sie das [**TargetDeviceFamily**](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily) -Element in Ihrem Manifest nur die Gerätefamilie ausgerichtet, die Sie unterstützen möchten (d. h. Windows.Mobile oder Windows.Desktop), anstatt als verlassen es als den Windows.Universal-Wert (für die universelle Gerätefamilie), die Microsoft Visual Studio im Manifest ist standardmäßig enthalten.

Beachten Sie außerdem, dass die unter **Verfügbarkeit von Gerätefamilien** getroffene Auswahl nur für neue Verkäufe gilt. Kunden, die Ihre App bereits verwenden, können dies weiterhin tun und erhalten alle zur Verfügung gestellten Updates, selbst wenn Sie diese Gerätefamilie an dieser Stelle entfernen. Dies gilt auch für Kunden, die Ihre App vor dem Upgrade auf Windows 10 erworben haben. Beispielsweise werden, wenn Sie eine veröffentlichte app mit Windows Phone 8.1-Pakete haben, und ein Windows 10 (UWP)-Paket auf die Gerätefamilie Windows.Universal hinzufügen, Windows 10 mobile-Kunden, die Ihre Windows Phone 8.1-Paket verwendet haben ein Update auf diese Windows angeboten 10 (UWP) Verpacken, auch wenn Sie haben deaktiviert das Kontrollkästchen für **Windows 10 Mobile**.

Weitere Informationen über die Gerätefamilien finden Sie unter [**Übersicht über die Gerätefamilien**](https://docs.microsoft.com/uwp/extension-sdks/device-families-overview).


## <a name="understanding-ranking"></a>Grundlegendes zur Bewertung

Die **Verfügbarkeit von gerätefamilien** -Abschnitt erfahren Sie nicht wie Sie angeben, welche Windows 10-gerätefamilien Ihre Übermittlung herunterladen können, die bestimmte Pakete, die für andere gerätefamilien verfügbar gemacht werden. Wenn mehrere Ihrer Pakete auf einer bestimmten Gerätefamilie ausgeführt werden können, wird in der Tabelle die Reihenfolge angegeben, in der Pakete basierend auf der Versionsnummer angeboten werden. Weitere Informationen dazu, wie der Store Pakete auf Grundlage der Versionsnummern bewertet, finden Sie unter [Paketversionsnummern](package-version-numbering.md). 

Angenommen, Sie haben die beiden Pakete Package_A.appxupload und Package_B.appxupload. Wenn für eine bestimmte Gerätefamilie, Package_A.appxupload den Rang 1 und Package_B.appxupload den Rang 2 hat, bedeutet dies, das der Store an einen Kunden mit diesem Gerätetyp, der Ihre App erwirbt, zunächst Package_A.appxupload ausliefert. Wenn Package_A.appxupload auf den Gerät des Kunden nicht ausgeführt werden kann, bietet der Store Package_B.appxupload an. Wenn das Gerät des Kunden die Pakete für diese Gerätefamilie nicht ausgeführt werden kann (z. B. wenn **MinVersion** Ihrer app unterstützt ist höher als die Version auf dem Gerät des Kunden) und der Kunde die app auf dem Gerät herunterladen werden kann.

> [!NOTE]
> Die Versionsnummern in XAP-Pakete (für bereits veröffentlichte apps) werden nicht berücksichtigt, beim Ermitteln der für einen gegebenen Kunden bereitzustellenden Pakete ignoriert. Daher wird bei mehreren gleichrangigen XAP-Paketen keine Nummer, sondern ein Sternchen angezeigt, und die Kunden können jedes der Pakete erhalten. Wenn ein XAP-Paket für einen Kunden auf ein neueres aktualisiert werden soll, stellen Sie sicher, dass die älteren XAP-Dateien aus der neuen Übermittlung entfernt werden.

