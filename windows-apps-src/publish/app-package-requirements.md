---
author: jnHs
Description: Follow these guidelines to prepare your app's packages for submission to the Microsoft Store.
title: App-Paketanforderungen
ms.assetid: 651B82BA-9D0C-45AC-8997-88CD93DC903C
ms.author: wdg-dev-content
ms.date: 05/16/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP, Paketanforderungen, Pakete, Paketformat, unterstützte Version, übermitteln
ms.localizationpriority: medium
ms.openlocfilehash: d7d748f36dafd93066928f01f9aa42414f2ffc1f
ms.sourcegitcommit: f5cf806a595969ecbb018c3f7eea86c7a34940f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "3821194"
---
# <a name="app-package-requirements"></a>App-Paketanforderungen

Halten Sie die folgenden Richtlinien ein, wenn Sie die App-Pakete für die Übermittlung an den Microsoft Store vorbereiten.

## <a name="before-you-build-your-apps-package-for-the-microsoft-store"></a>Vor dem Erstellen des App-Pakets für den Microsoft Store

Denken Sie daran, [Ihre App mit dem Zertifizierungskit für Windows-Apps zu testen](../debug-test-perf/windows-app-certification-kit.md). Außerdem wird empfohlen, Ihre App mit verschiedenen Hardwaretypen zu testen. Beachten Sie, dass Ihre App nur auf Computern mit Entwicklerlizenzen installiert und ausgeführt werden kann, bis wir die App zertifiziert und im Microsoft Store verfügbar gemacht haben.

## <a name="building-the-app-package-using-microsoft-visual-studio"></a>Erstellen des App-Pakets mit Microsoft Visual Studio

Wenn Sie Microsoft Visual Studio als Entwicklungsumgebung verwenden, verfügen Sie bereits über integrierte Tools zum schnellen und einfachen Erstellen eines App-Pakets. Weitere Informationen finden Sie unter [Verpacken von Apps](../packaging/index.md).

> [!NOTE]
> Achten Sie darauf, für alle Dateinamen ANSI zu verwenden. 

Um Ihr Paket in Visual Studio zu erstellen, müssen Sie sich mit demselben Konto anmelden, das Ihrem Entwicklerkonto zugeordnet ist. Einige Teile des Paketmanifests enthalten spezifische kontobezogene Details. Diese Informationen werden erkannt und automatisch hinzugefügt. Ohne die zusätzlichen Informationen, die dem Manifest hinzugefügt wurden, können beim Hochladen von Paketen Fehler auftreten. 

Beim Erstellen der App-Pakete kann Visual Studio eine APPX-Datei oder eine APPXUPLOAD-Datei erstellen (bzw. eine XAP-Datei für Windows Phone 8.1 und frühere Versionen). Bei Apps für Windows 10 laden Sie immer die APPXUPLOAD-Datei auf die Seite [Pakete](upload-app-packages.md) hoch. Weitere Informationen zum Verpacken von UWP-Apps für den Store finden Sie unter [Verpacken einer UWP-App mit Visual Studio](../packaging/packaging-uwp-apps.md).

App-Pakete müssen nicht mit einem Stammzertifikat einer vertrauenswürdigen Zertifizierungsstelle signiert werden.


### <a name="app-bundles"></a>App-Bündel

Für apps, die Windows 10, Windows 8.1 und/oder Windows Phone 8.1 ausgerichtet sind, kann Visual Studio generiert ein app-Bündel (.appxbundle), um die Größe der app reduzieren, die Benutzer herunterladen. Dieser Schritt ist in der Regel sinnvoll, wenn Sie sprachspezifische Ressourcen, mehrere Ressourcen für die Bildgröße oder Ressourcen für bestimmte Versionen von Microsoft DirectX definiert haben.

> [!NOTE]
> Ein App-Bündel kann Ihre Pakete für alle Architekturen enthalten. Pro Zielbetriebssystem sollte nur ein App-Bündel eingereicht werden.

Bei einem App-Bündel lädt der Benutzer nicht alle vorhandenen Ressourcen, sondern nur relevante Dateien herunter. Weitere Informationen zu App-Bündeln finden Sie unter [Verpacken von Apps](../packaging/index.md) und [Verpacken von UWP-App mit Visual Studio](../packaging/packaging-uwp-apps.md).


## <a name="building-the-app-package-manually"></a>Manuelles Erstellen des App-Pakets

Wenn Sie Ihr Paket nicht mit Visual Studio erstellen, müssen Sie Ihr [Paketmanifest manuell erstellen](https://docs.microsoft.com/uwp/schemas/appxpackage/how-to-create-a-package-manifest-manually).

Ausführliche Informationen und die Anforderungen für Manifeste finden Sie in der Dokumentation zum [App-Paketmanifest](https://docs.microsoft.com/uwp/schemas/appxpackage/appx-package-manifest). Es werden nur Apps zertifiziert, deren Manifest dem Paketmanifestschema entspricht.

Ihr Manifest muss spezifische konto- und App-bezogene Informationen enthalten. Sie finden diese Informationen unter [Anzeigen von Details zur App-Identität](view-app-identity-details.md) im Abschnitt **App-Verwaltung** der App-Übersichtsseite im Dashboard.

> [!NOTE]
> Bei den Werten im Manifest wird die Groß-/Kleinschreibung berücksichtigt. Leerzeichen und Satzzeichen müssen ebenfalls übereinstimmen. Geben Sie die Werte richtig ein, und überprüfen Sie sie anschließend auf ihre Korrektheit.


App-Bündel (.appxbundle) verwenden ein anderes Manifest. Ausführliche Informationen und die Anforderungen für App-Bündel finden Sie in der Dokumentation zum [Bündelmanifest](https://docs.microsoft.com/uwp/schemas/bundlemanifestschema/bundle-manifest). Beachten Sie, dass in appxbundle, die .appxmanifest der einzelnen Pakete enthalten die gleichen Elemente und Attribute, mit Ausnahme der **ProcessorArchitecture** -Attribut des Elements [Identität](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-identity) verwenden müssen.

> [!TIP]
> Führen Sie vor dem Einreichen Ihrer Pakete unbedingt das [Zertifizierungskit für Windows-Apps](../debug-test-perf/windows-app-certification-kit.md) aus. So können Sie feststellen, ob es mit Ihrem Manifest Probleme gibt, die Zertifizierungs- oder Einreichungsfehler verursachen können.


## <a name="package-format-requirements"></a>Paketformatanforderungen

Ihre App-Pakete müssen die folgenden Anforderungen erfüllen:

| App-Paketeigenschaft | Anforderung                                                          |
|----------------------|----------------------------------------------------------------------|
| Paketgröße         | APPX-Bündel: maximal 25GB pro Bündel <br>APPX-Pakete für Windows 10: maximal 25 GB pro Paket<br>APPX-Pakete für Windows 8.1: maximal 8 GB pro Paket <br> APPX-Pakete für Windows 8: maximal 2 GB pro Paket <br> APPX-Pakete für WindowsPhone 8.1: maximal 4GB pro Paket <br> XAP-Pakete: maximal 1 GB pro Paket                                                                           |
| Hashes für Blockzuordnung     | SHA2-256-Algorithmus                                                   |


## <a name="supported-versions"></a>Unterstützte Versionen

Für UWP-Apps müssen alle Pakete auf eine Version von Windows10 ausgerichtet sein, die vom Store unterstützt wird. Die Versionen, die von Ihrem Paket unterstützt werden, müssen in den Attributen **MinVersion** und **MaxVersionTested** des [TargetDeviceFamily](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily)-Element im App-Manifest angegeben werden.

Derzeit wird der folgende Versionsbereich unterstützt: 
- Minimum: 10.0.10240.0
- Maximum: 10.0.17134.0


## <a name="storemanifest-xml-file"></a>Datei „StoreManifest.xml“

„StoreManifest.xml“ ist eine optionale Konfigurationsdatei, die in App-Pakete aufgenommen werden kann. Sie dient zum Aktivieren von Features, die vom Paketmanifest nicht abgedeckt werden – beispielsweise Features zum Deklarieren Ihrer App als Microsoft Store-Geräte-App oder zum Deklarieren von Anforderungen, die für ein Paket erfüllt werden müssen, damit es auf ein Gerät angewendet werden kann. Wenn verwendet, wird "storemanifest.xml" wird mit dem app-Paket eingereicht und muss im Stammordner des app Hauptprojekts sein. Weitere Informationen finden Sie unter [StoreManifest-Schema](https://docs.microsoft.com/uwp/schemas/storemanifest/store-manifest-schema-portal).

 

 




