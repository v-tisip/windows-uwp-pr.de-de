---
author: laurenhughes
title: Flat-Bundle App-Pakete
description: Beschreibt, wie ein Flat-Bundle erstellt wird, um die .appx-Paketdateien Ihrer App mit Verweisen auf App-Pakete zu bündeln.
ms.author: lahugh
ms.date: 09/30/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, verpacken, paketkonfiguration, flat bundle
ms.localizationpriority: medium
ms.openlocfilehash: 63206619d75bedb92ad6c6d05c3188272c0760de
ms.sourcegitcommit: 49aab071aa2bd88f1c165438ee7e5c854b3e4f61
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2018
ms.locfileid: "4471647"
---
# <a name="flat-bundle-app-packages"></a>Flat-Bundle App-Pakete 

> [!IMPORTANT]
> Wenn Sie Ihre App an den Store übermitteln möchten, müssen Sie sich an den [Windows-Support für Entwickler](https://developer.microsoft.com/windows/support) wenden und eine Genehmigung für die Verwendung von Flat Bundles erhalten.

Flat Bundles sind eine bessere Möglichkeit, Ihre app-Paket-Dateien zu bündeln. Eine typische Windows app-Bündel-Datei eine mehrstufige Verpackungsstruktur verwendet, in der die app-Paketdateien im Bündel enthalten sein müssen, flat Bundles entfällt diese Notwendigkeit, indem Sie nur die app auf Paketdateien verweisen, sodass sie außerhalb des app-Bündels befinden. Da die app-Paket-Dateien nicht mehr im Bündel enthalten sind, kann es sich um parallel verarbeitet, wodurch geringere Uploadzeit, einer schnelleren Veröffentlichung (da jede app-Paketdatei gleichzeitig verarbeitet werden kann) und letztendlich zu schnelleren Entwicklung Iterationen.

![Flat Bundle-Diagramm](images/bundle-combined.png)

Ein weiterer Vorteil von Flat Bundles ist, dass weniger Pakete erstellt werden müssen. Da app-Paketdateien nur verwiesen werden, können zwei Versionen der app die gleiche Paketdatei verweisen, wenn das Paket in den beiden Versionen nicht geändert hat. Dadurch müssen Sie beim Erstellen der Pakete für die nächste Version Ihrer App lediglich die App-Pakete erstellen, die geändert wurden.
Standardmäßig verweisen die flat Bundles app-Paketdateien innerhalb desselben Ordners als selbst. Diese Referenz kann jedoch in andere Pfade (relative Pfade, Netzwerkfreigaben und http-Speicherorte) geändert werden. Dazu müssen Sie während des Erstellens des Flat Bundles ein **BundleManifest** direkt bereitstellen. 

## <a name="how-to-create-a-flat-bundle"></a>So erstellen Sie ein Flat Bundle

Ein Flat Bundle kann mithilfe des MakeAppx.exe-Tools erstellt werden. Sie können auch das Verpackungslayout verwenden, um die Struktur Ihres Bundles zu definieren.

### <a name="using-makeappxexe"></a>Verwenden der MakeAppx.exe
Um ein flat Bundle mit MakeAppx.exe zu erstellen, verwenden Sie den Befehl "MakeAppx.exe Bundle" wie gewohnt jedoch mit dem/FB-Switch um die flache app-Bundle-Datei generieren (die extrem klein ist, da sie nur verweist auf die app-Paket-Dateien und enthält keine tatsächlichen Nutzlasten enthält ). 

Hier sehen Sie ein Beispiel für die Befehlssyntax:

```syntax
MakeAppx bundle [options] /d <content directory> /fb <output flat bundle name>
```

Weitere Informationen zur Verwendung von MakeApp.exe finden Sie unter [Erstellen eines App-Pakets mit dem Tool „MakeAppx.exe“](https://docs.microsoft.com/windows/uwp/packaging/create-app-package-with-makeappx-tool).

### <a name="using-packaging-layout"></a>Verwenden des Verpackungslayouts
Alternativ können Sie ein Flat Bundle mit dem Verpackungslayout erstellen. Legen Sie dazu das **FlatBundle**-Attribut im **PackageFamily**-Element Ihres App-Bündelmanifests auf **true** fest. Weitere Informationen zum Verpackungslayout finden Sie unter [Erstellen eines Pakets mit dem Verpackungslayout](packaging-layout.md).

## <a name="how-to-deploy-a-flat-bundle"></a>So stellen Sie ein Flat Bundle bereit 
Bevor ein Flat Bundle bereitgestellt werden kann, muss jedes App-Paket (zusätzlich zu den App-Bündeln) mit demselben Zertifikat signiert werden. Dies ist, da alle app-Paket-Dateien (.appx/.msix) nun unabhängige Dateien und nicht in der app-Bundle (.appxbundle/.msixbundle)-Datei nicht mehr enthalten sind. Nachdem die Pakete signiert sind, verwenden Sie das [Add-AppxPackage-Cmdlet](https://docs.microsoft.com/powershell/module/appx/add-appxpackage?view=win10-ps) in PowerShell, zeigen Sie auf der app-Bündel-Datei und Bereitstellen der app (vorausgesetzt, dass app-Pakete sind, in denen die app-Bündel erwartet). 