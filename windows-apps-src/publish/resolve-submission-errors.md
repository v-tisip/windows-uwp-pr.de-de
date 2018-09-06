---
author: jnHs
Description: If you encounter errors after submitting your app to the Store, you must resolve them in order to continue the certification process.
title: Beheben von Übermittlungsfehlern
ms.assetid: 68199E09-0C66-4EB4-BFE8-D2EEB139C4F3
ms.author: wdg-dev-content
ms.date: 09/13/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 9d027e35f8fe76a0d4139301f1a7dabc7798348a
ms.sourcegitcommit: 914b38559852aaefe7e9468f6f53a7465bf36e30
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "3393764"
---
# <a name="resolve-submission-errors"></a>Beheben von Übermittlungsfehlern

Wenn nach der Übermittlung Ihrer App an den Store Fehler auftreten, müssen Sie diese beheben, bevor Sie den [Zertifizierungsprozess](the-app-certification-process.md) fortsetzen können. Die Fehlermeldung weist darauf hin, worin das Problem besteht und was eventuell erforderlich ist, um das Problem zu beheben. Nachfolgend sind einige zusätzliche Informationen aufgeführt, die Ihnen beim Beheben dieser Fehler helfen können.

## <a name="uwp-apps"></a>UWP-Apps

Wenn Sie eine UWP-App einreichen, wird während der Vorverarbeitung möglicherweise ein Fehler angezeigt, wenn die Paketdatei keine von Visual Studio für den Store generierte „.appxupload“-Datei ist. Achten Sie darauf, dass Sie die Schritte in [einer UWP-app mit Visual Studio-Paket](../packaging/packaging-uwp-apps.md) beim Erstellen der Datei der app-Paket, und nur die appxupload-Datei auf der Seite " [Pakete](upload-app-packages.md) ", der die Übermittlung keine Appx oder .appxbundle hochzuladen.

Wenn ein Kompilierungsfehler angezeigt wird, stellen Sie sicher, dass Sie die Anwendung erfolgreich im Releasemodus erstellen können. Weitere Informationen finden Sie unter [Systemeigene .NET-Compilerfehler](http://go.microsoft.com/fwlink/p/?LinkID=613098).

## <a name="desktop-application"></a>Desktop-Anwendung

Wenn Sie beabsichtigen, ein Paket zu übermitteln, die Win32- und UWP-Binärdateien enthält, stellen Sie sicher, dass Sie dieses Paket erstellen, indem Sie mithilfe von Windows Paketprojekts, die in Visual Studio 2017 Update 4 verfügbar ist. Wenn Sie das Paket mithilfe einer UWP-Projekt-Vorlage erstellen, können Sie möglicherweise nicht übermitteln, dass, die im Store oder das querladen es auf anderen PCs Paket. Auch wenn das Paket erfolgreich veröffentlicht werden, kann es auf dem PC des Benutzers unerwartetem Verhalten. Weitere Informationen finden Sie unter [Package einer app mit Visual Studio (Desktop-Brücke)]( https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

## <a name="windows-phone-apps"></a>Windows Phone-Apps

Wenn während der Vorverarbeitung Probleme mit Windows Phone-Paketen auftreten, wird möglicherweise **Fehler 2001** angezeigt. In den meisten Fällen müssen Sie das Paket Ihrer App neu erstellen, um den Fehler zu beheben. Sobald Sie damit fertig sind, ersetzen Sie auf der Seite [Pakete](upload-app-packages.md) der Einreichung das alte durch das neue Paket, bevor Sie erneut auf **An Store einreichen** klicken.

Es gibt eine Reihe von Problemen, die diesen Fehler verursachen können. Überprüfen Sie die nachfolgende Liste, um zu ermitteln, welches Problem möglicherweise auf Ihre Pakete zutrifft.

-   **Mindestens eine Assembly im Paket wurde nicht ordnungsgemäß verborgen:** Verwenden Sie ein anderes Tool zum Verbergen, oder verzichten Sie auf das Verbergen. Der Kompilierungsprozess optimiert die verborgenen Assemblys, aber gelegentlich werden jedoch einige Assemblys mit einem Tool verborgen, das die MSIL auf nicht unterstützt Weise verändert und daher einen Fehler auslöst.
-   **Die Größe mindestens einer Methode in der App beträgt mehr als 256 KB.** Gestalten Sie die betreffende Methode so um, dass kleinere Funktionen entstehen. Die MSIL-Größe für Methoden in einer Assembly kann mit dem ILDASM-Tool ermittelt werden.
-   **Die Prüfung der starken Namenssignatur ist für mindestens eine Assembly fehlgeschlagen:** Dieser Fehler tritt meist auf, wenn für die starke Namenssignatur ein anderer Schlüssel als der in den Assembly-Metadaten erwartete verwendet wurde. Verwenden Sie den richtigen Schlüssel zum Signieren, oder entfernen Sie die starke Namenssignatur.
-   **Das Paket enthält Assemblys mit gemischtem Modus (also mit verwaltetem und nativem Code):** Assemblys mit gemischtem Modus werden unter Windows Phone nicht unterstützt. Entfernen Sie die betreffenden Assemblys aus dem Paket, und reichen Sie die App erneut ein.
-   **Eine Windows Phone 8.1-XAP oder appx-/appxbundle-Assembly ist ungültig:** Stellen Sie sicher, dass die WINMD-Datei mindestens über einen öffentlichen Einstiegspunkt verfügt. Sie können ggf. eine beliebige Dekompilierungsanwendung verwenden, um den Code zu überprüfen und öffentliche Einstiegspunkte zu suchen.

Ein weiterer Fehler, der möglicherweise nach dem Einreichen Ihrer App angezeigt wird, ist **Fehler 1300**. Dieser Fehler tritt auf, wenn mindestens eine Assembly (oder das gesamte Paket) bereits vorkompiliert ist. Um dieses Problem zu beheben, erstellen Sie das App-Paket in Microsoft Visual Studio neu und reichen dann das neu generierte Paket ein.

## <a name="nameidentity-errors"></a>Fehler für Name/Identität

Möglicherweise wird Ihnen der folgende Fehler angezeigt: **Der Name des Pakets stimmt mit keinem der von Ihnen reservierten App-Namen überein. Reservieren Sie den App-Namen, und/oder aktualisieren Sie das Paket mit dem korrekten App-Namen für diese Sprache.**. Dies bedeutet, dass Sie einen falschen Namen für das Paket eingegeben haben. Dieser Fehler kann auch auftreten, wenn Sie einen App-Namen verwenden, den Sie im Dev Center nicht reserviert haben. In der Regel können Sie diesen Fehler beheben, indem Sie folgende Schritte ausführen:

- Wechseln Sie zur Seite [App-Identität](view-app-identity-details.md) für Ihre App (unter **App-Verwaltung**), um zu überprüfen, ob Ihrer App eine Identität zugewiesen wurde. Wenn dies nicht der Fall ist, wird Ihnen die Option für das Erstellen von Identitäten angezeigt. Sie müssen einen Namen für Ihre App reservieren, um die Identität zu erstellen. Stellen Sie sicher, dass dies der Name ist, den Sie in Ihrem Paket verwendet haben.
- Wenn Ihre App bereits über eine Identität verfügt, müssen Sie möglicherweise dennoch den Namen reservieren, den Sie in Ihrem Paket verwenden möchten. Klicken Sie unter **App-Verwaltung** auf [App-Namen verwalten](manage-app-names.md). Geben Sie den Namen ein, den Sie reservieren möchten, und klicken Sie auf **App-Namen reservieren**.

> [!IMPORTANT]
>  Wenn der Name, den Sie verwenden möchten, nicht verfügbar ist, eine andere app möglicherweise bereits den Namen reserviert haben. Wenn Ihre app bereits unter diesem Namen veröffentlicht wurde, oder wenn Sie sich vorstellen, Sie haben das Recht, [kontaktieren Sie den Support](https://go.microsoft.com/fwlink/p/?LinkId=331509)verwenden.  

 

 




