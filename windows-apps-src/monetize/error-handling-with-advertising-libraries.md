---
author: mcleanbyron
ms.assetid: cb7380d0-bc14-4936-aa1c-206304b3dc70
description: Hier erfahren Sie, wie Sie mit Fehlern umgehen, die in den Microsoft Advertising-Bibliotheken von der AdControl-Klasse generiert werden.
title: Fehlerbehandlung mit den Microsoft Advertising-Bibliotheken
translationtype: Human Translation
ms.sourcegitcommit: 2b5dbf872dd7aad48373f6a6df3dffbcbaee8090
ms.openlocfilehash: 56df2b0f0a41d128f02aa5e2aa0ce11e6f6ca16a

---

# <a name="error-handling-with-the-microsoft-advertising-libraries"></a>Fehlerbehandlung mit den Microsoft Advertising-Bibliotheken

Dieses Thema enthält grundlegende Informationen zum Behandeln von Fehlern, die von der [AdControl](https://msdn.microsoft.com/library/windows/apps/microsoft.advertising.winrt.ui.adcontrol.aspx)-Klasse in den Microsoft Advertising-Bibliotheken generiert werden.

<span id="bkmk-javascript"/>
## <a name="javascripthtml-apps"></a>JavaScript/HTML-Apps

So behandeln Sie **AdControl** Fehler in einer JavaScript-App:

1.  Weisen Sie das **OnErrorOccurred**-Ereignis einem Ereignishandler zu.

2.  Codieren Sie den Ereignishandler.

Der **OnErrorOccurred**-Ereignishandler wird im Attribut **data-win-options** für das **div** des **AdControl** festgelegt. Im folgenden Beispiel wird für das **OnErrorOccurred**-Ereignis festgelegt, dass es durch eine Funktion namens **ErrorLogger** behandelt wird.

> [!div class="tabbedCodeSnippets"]
``` html
<div id="myAd" style="position: absolute; top: 53px; left: 0px; width: 250px; height: 250px; z-index: 1"
     data-win-control="MicrosoftNSJS.Advertising.AdControl"
     data-win-options="{applicationId: 'd25517cb-12d4-4699-8bdc-52040c712cab', adUnitId: 'ADPT33', onErrorOccurred: errorLogger}">
</div>
```

Die Fehlerbehandlungsfunktion ist deklarativ und muss in die Funktion [MarkSupportedForProcessing](http://msdn.microsoft.com/library/windows/apps/Hh967819.aspx) eingeschlossen werden.

Der Fehlerhandler fängt das JavaScript-Fehlerobjekt auf, wenn ein **AdControl**-Fehler auftritt. Das Fehlerobjekt liefert dem Fehlerhandler zwei Argumente. Weitere Informationen finden Sie unter [Eigenschaften spezieller Fehler von asynchronen Methoden von Windows-Runtime](http://msdn.microsoft.com/library/windows/apps/hh994690.aspx).

Hier ist ein Beispiel für eine Fehlerbehandlungsfunktion mit dem Namen **ErrorLogger**, die das Ereignis **OnErrorOccurred** behandelt.

> [!div class="tabbedCodeSnippets"]
``` javascript
WinJS.Utilities.markSupportedForProcessing(
window.errorLogger = function (sender, evt) {
    console.log(new Date()).toLocaleTimeString() + ": " + sender.element.id + " error: " + evt.errorMessage +
    " error code: " + evt.errorCode + \n");
});
```

Unter [Exemplarische Vorgehensweise zur Fehlerbehandlung in JavaScript](error-handling-in-javascript-walkthrough.md) finden Sie eine exemplarische Vorgehensweise zur Veranschaulichung der **AdControl**-Fehlerbehandlung in JavaScript.

<span id="bkmk-dotnet"/>
## <a name="xaml-apps"></a>XAML-Apps

So behandeln Sie **AdControl**-Fehler in einer XAML-App:

* Weisen Sie das **ErrorOccurred**-Ereignis dem Namen eines Ereignishandlerdelegaten zu.

* Codieren Sie den Ereignishandlerdelegaten so, dass er zwei Parameter verwendet: ein **Objekt** für den Absender und ein **AdErrorEventArgs**-Objekt.

Hier ist ein Beispiel, das einen Delegaten mit dem Namen **OnAdError** dem Ereignis **ErrorOccurred** zuweist.

> [!div class="tabbedCodeSnippets"]
``` csharp
this.ErrorOccurred = OnAdError;
```

Hier ist eine Beispieldefinition des **OnAdError**-Delegaten, die Fehlerinformationen in das Ausgabefenster in Visual Studio schreibt.

> [!div class="tabbedCodeSnippets"]
``` csharp
private void OnAdError(object sender, AdErrorEventArgs e)
{
    System.Diagnostics.Debug.WriteLine("AdControl error (" + ((AdControl)sender).Name + "): " + e.Error +
        " ErrorCode: " + e.ErrorCode.ToString());
}
```

Unter [Exemplarische Vorgehensweise zur Fehlerbehandlung in XAML/C#](error-handling-in-xamlc-walkthrough.md) finden Sie eine exemplarische Vorgehensweise zur Veranschaulichung der **AdControl**-Fehlerbehandlung in XAML und C#.

 

 



<!--HONumber=Dec16_HO2-->


