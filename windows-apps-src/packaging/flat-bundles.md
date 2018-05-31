---
author: laurenhughes
title: Flat-Bundle App-Pakete
description: Beschreibt, wie ein Flat-Bundle erstellt wird, um die .appx-Paketdateien Ihrer App mit Verweisen auf App-Pakete zu bündeln.
ms.author: lahugh
ms.date: 04/30/2018
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, verpacken, paketkonfiguration, flat bundle
ms.localizationpriority: medium
ms.openlocfilehash: 757f95a5f46bad6dbe650b4b552f3de486d84e1b
ms.sourcegitcommit: 91511d2d1dc8ab74b566aaeab3ef2139e7ed4945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2018
ms.locfileid: "1818357"
---
# <a name="flat-bundle-app-packages"></a>Flat-Bundle App-Pakete 

> [!IMPORTANT]
> Wenn Sie Ihre App an den Store übermitteln möchten, müssen Sie sich an den [Windows-Support für Entwickler](https://developer.microsoft.com/windows/support) wenden und eine Genehmigung für die Verwendung von Flat Bundles erhalten.

Flat Bundles sind eine bessere Möglichkeit, die .appx-Paketdateien Ihrer App zu bündeln. Eine typische .appxbundle-Datei verwendet eine mehrstufige Verpackungsstruktur, in der die .appx-Paketdateien im Bündel enthalten sein müssen. Bei Flat Bundles entfällt diese Notwendigkeit, indem sie nur auf die .appx-Paketdateien verweisen, sodass sich diese außerhalb des App-Bündels befinden können. Da die .appx-Paketdateien nicht mehr im Bündel enthalten sind, können sie parallel verarbeitet werden, was zu einer kürzeren Uploadzeit, einer schnelleren Veröffentlichung (da jede .appx-Paketdatei gleichzeitig verarbeitet werden kann) und letztendlich zu schnelleren Entwicklungsiterationen führt.

![Flat Bundle-Diagramm](images/bundle-combined.png)

Ein weiterer Vorteil von Flat Bundles ist, dass weniger Pakete erstellt werden müssen. Da auf .appx-Paketdateien nur verwiesen wird, können zwei Versionen der App auf die gleiche Paketdatei verweisen, wenn sich das Paket in den beiden Versionen nicht geändert hat. Dadurch müssen Sie beim Erstellen der Pakete für die nächste Version Ihrer App lediglich die App-Pakete erstellen, die geändert wurden.
Standardmäßig verweisen die Flat Bundles auf .appx-Paketdateien innerhalb desselben Ordners. Diese Referenz kann jedoch in andere Pfade (relative Pfade, Netzwerkfreigaben und http-Speicherorte) geändert werden. Dazu müssen Sie während des Erstellens des Flat Bundles ein **BundleManifest** direkt bereitstellen. 

## <a name="how-to-create-a-flat-bundle"></a>So erstellen Sie ein Flat Bundle

Ein Flat Bundle kann mithilfe des MakeAppx.exe-Tools erstellt werden. Sie können auch das Verpackungslayout verwenden, um die Struktur Ihres Bundles zu definieren.

### <a name="using-makeappxexe"></a>Verwenden der MakeAppx.exe
Um ein Flat Bundle mit MakeAppx.exe zu erstellen, verwenden Sie wie gewohnt den Befehl „MakeAppx.exe bundle”, jedoch mit dem /fb-Switch, um die flache .appxbundle-Datei zu generieren (die extrem klein ist, da sie nur auf die .appx-Pakete verweist und keine tatsächlichen Nutzlasten enthält). 

Hier sehen Sie ein Beispiel für die Befehlssyntax:

```syntax
MakeAppx bundle [options] /d <content directory> /fb <output flat bundle name>
```

Weitere Informationen zur Verwendung von MakeApp.exe finden Sie unter [Erstellen eines App-Pakets mit dem Tool „MakeAppx.exe“](https://docs.microsoft.com/windows/uwp/packaging/create-app-package-with-makeappx-tool).

### <a name="using-packaging-layout"></a>Verwenden des Verpackungslayouts
Alternativ können Sie ein Flat Bundle mit dem Verpackungslayout erstellen. Legen Sie dazu das **FlatBundle**-Attribut im **PackageFamily**-Element Ihres App-Bündelmanifests auf **true** fest. Weitere Informationen zum Verpackungslayout finden Sie unter [Erstellen eines Pakets mit dem Verpackungslayout](packaging-layout.md).

## <a name="how-to-deploy-a-flat-bundle"></a>So stellen Sie ein Flat Bundle bereit 
Bevor ein Flat Bundle bereitgestellt werden kann, muss jedes App-Paket (zusätzlich zu den App-Bündeln) mit demselben Zertifikat signiert werden. Der Grund hierfür ist, dass alle App-Paketdateien (.appx) nun unabhängige Dateien sind und nicht mehr in der App-Bündel-Datei (.appxbundle) enthalten sind. Nachdem die Pakete signiert sind, verwenden Sie das [„Add-AppxPackage”-Cmdlet](https://docs.microsoft.com/powershell/module/appx/add-appxpackage?view=win10-ps) in PowerShell, um auf die .appxbundle-Datei zu zeigen und die App bereitzustellen (unter der Annahme, dass sich die App-Pakete dort befinden, wo dies vom App-Bündel erwartet wird). 