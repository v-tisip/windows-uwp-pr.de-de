---
author: jnHs
Description: Follow these guidelines to prepare your app's packages for submission to the Microsoft Store.
title: App-Paketanforderungen
ms.assetid: 651B82BA-9D0C-45AC-8997-88CD93DC903C
ms.author: wdg-dev-content
ms.date: 10/31/2018
ms.topic: article
keywords: Windows10, UWP, Paketanforderungen, Pakete, Paketformat, unterstützte Version, übermitteln
ms.localizationpriority: medium
ms.openlocfilehash: 1c76cb26d91ecd1f72b71f90b9ef464cdf52ba55
ms.sourcegitcommit: f2c9a050a9137a473f28b613968d5782866142c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2018
ms.locfileid: "6274049"
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

Wenn Sie Ihre app UWP-Pakete erstellen, kann Visual Studio ein .msix oder Appx-Datei oder eine .msixupload oder appxupload-Datei erstellen. Für UWP-apps wird empfohlen, dass Sie immer die .msixupload oder appxupload-Datei in die Seite " [Pakete](upload-app-packages.md) " hochladen. Weitere Informationen zum Verpacken von UWP-Apps für den Store finden Sie unter [Verpacken einer UWP-App mit Visual Studio](../packaging/packaging-uwp-apps.md).

App-Pakete müssen nicht mit einem Stammzertifikat einer vertrauenswürdigen Zertifizierungsstelle signiert werden.


### <a name="app-bundles"></a>App-Bündel

Für UWP-apps können Visual Studio generiert ein app-Bündel (.msixbundle oder .appxbundle), um die Größe der app zu reduzieren, die Benutzer herunterladen. Dieser Schritt ist in der Regel sinnvoll, wenn Sie sprachspezifische Ressourcen, mehrere Ressourcen für die Bildgröße oder Ressourcen für bestimmte Versionen von Microsoft DirectX definiert haben.

> [!NOTE]
> Ein App-Bündel kann Ihre Pakete für alle Architekturen enthalten.

Bei einem App-Bündel lädt der Benutzer nicht alle vorhandenen Ressourcen, sondern nur relevante Dateien herunter. Weitere Informationen zu App-Bündeln finden Sie unter [Verpacken von Apps](../packaging/index.md) und [Verpacken von UWP-App mit Visual Studio](../packaging/packaging-uwp-apps.md).


## <a name="building-the-app-package-manually"></a>Manuelles Erstellen des App-Pakets

Wenn Sie Ihr Paket nicht mit Visual Studio erstellen, müssen Sie Ihr [Paketmanifest manuell erstellen](https://docs.microsoft.com/uwp/schemas/appxpackage/how-to-create-a-package-manifest-manually).

Ausführliche Informationen und die Anforderungen für Manifeste finden Sie in der Dokumentation zum [App-Paketmanifest](https://docs.microsoft.com/uwp/schemas/appxpackage/appx-package-manifest). Es werden nur Apps zertifiziert, deren Manifest dem Paketmanifestschema entspricht.

Ihr Manifest muss spezifische konto- und App-bezogene Informationen enthalten. Sie finden diese Informationen unter [Anzeigen von Details zur App-Identität](view-app-identity-details.md) im Abschnitt **App-Verwaltung** der App-Übersichtsseite im Dashboard.

> [!NOTE]
> Bei den Werten im Manifest wird die Groß-/Kleinschreibung berücksichtigt. Leerzeichen und Satzzeichen müssen ebenfalls übereinstimmen. Geben Sie die Werte richtig ein, und überprüfen Sie sie anschließend auf ihre Korrektheit.


App-Bündel (.msixbundle oder .appxbundle) verwenden Sie ein anderes Manifest. Ausführliche Informationen und die Anforderungen für App-Bündel finden Sie in der Dokumentation zum [Bündelmanifest](https://docs.microsoft.com/uwp/schemas/bundlemanifestschema/bundle-manifest). Beachten Sie, dass in einem .msixbundle oder .appxbundle, das Manifest der einzelnen Pakete enthalten die gleichen Elemente und Attribute, mit Ausnahme der **ProcessorArchitecture** -Attribut des Elements [Identität](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-identity) verwenden muss.

> [!TIP]
> Führen Sie vor dem Einreichen Ihrer Pakete unbedingt das [Zertifizierungskit für Windows-Apps](../debug-test-perf/windows-app-certification-kit.md) aus. So können Sie feststellen, ob es mit Ihrem Manifest Probleme gibt, die Zertifizierungs- oder Einreichungsfehler verursachen können.


## <a name="package-format-requirements"></a>Paketformatanforderungen

Ihre App-Pakete müssen die folgenden Anforderungen erfüllen:

| App-Paketeigenschaft | Anforderung                                                          |
|----------------------|----------------------------------------------------------------------|
| Paketgröße         | .msixbundle oder .appxbundle: maximal 25 GB pro Bündel <br>.msix oder AppX-Pakete, die für Windows 10:25 maximal GB pro Paket<br>APPX-Pakete für Windows 8.1: maximal 8 GB pro Paket <br> APPX-Pakete für Windows 8: maximal 2 GB pro Paket <br> APPX-Pakete für WindowsPhone 8.1: maximal 4GB pro Paket <br> XAP-Pakete: maximal 1 GB pro Paket                                                                           |
| Hashes für Blockzuordnung     | SHA2-256-Algorithmus                                                   |

> [!IMPORTANT]
> Ab dem 31. Oktober 2018 darf keine Produkte neu erstellten Pakete für Windows-8.x/Windows enthalten Phone 8.x oder früher. Weitere Informationen finden Sie in diesem [Blogbeitrag](https://blogs.windows.com/buildingapps/2018/08/20/important-dates-regarding-apps-with-windows-phone-8-x-and-earlier-and-windows-8-8-1-packages-submitted-to-microsoft-store/#SzKghBbqDMlmAO4c.97).

## <a name="supported-versions"></a>Unterstützte Versionen

Für UWP-Apps müssen alle Pakete auf eine Version von Windows10 ausgerichtet sein, die vom Store unterstützt wird. Die Versionen, die von Ihrem Paket unterstützt werden, müssen in den Attributen **MinVersion** und **MaxVersionTested** des [TargetDeviceFamily](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily)-Element im App-Manifest angegeben werden.

Derzeit wird der folgende Versionsbereich unterstützt: 
- Minimum: 10.0.10240.0
- Maximale: 10.0.17763.1


## <a name="storemanifest-xml-file"></a>Datei „StoreManifest.xml“

„StoreManifest.xml“ ist eine optionale Konfigurationsdatei, die in App-Pakete aufgenommen werden kann. Sie dient zum Aktivieren von Features, die vom Paketmanifest nicht abgedeckt werden – beispielsweise Features zum Deklarieren Ihrer App als Microsoft Store-Geräte-App oder zum Deklarieren von Anforderungen, die für ein Paket erfüllt werden müssen, damit es auf ein Gerät angewendet werden kann. Wenn verwendet, muss "storemanifest.xml" wird mit dem app-Paket eingereicht und im Stammordner des app Hauptprojekts. Weitere Informationen finden Sie unter [StoreManifest-Schema](https://docs.microsoft.com/uwp/schemas/storemanifest/store-manifest-schema-portal).

 

 




