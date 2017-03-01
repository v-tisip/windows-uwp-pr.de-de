---
author: seksenov
title: "Gehostete Web-Apps – Konvertieren Ihrer Webanwendung in eine App für die Universelle Windows-Plattform (UWP) und Zugreifen auf systemeigene Windows 10-Features"
description: "Hier finden Sie die Ressourcen, die erforderlich sind, um Ihre Web-App in eine Universelle Windows-Plattform (UWP)-App für den Windows Store zu konvertieren."
ms.author: wdg-dev-content
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: "Gehostete Web-Apps, Umwandeln einer Website in eine Windows-App, Web-Apps im Windows Store, Chrome-Apps für Windows"
translationtype: Human Translation
ms.sourcegitcommit: 2e230e95be01f0b14fa6346be9fa836c66a812cf
ms.openlocfilehash: c9239f3a3c14bf9da99e60cfef8154eefb4305b4
ms.lasthandoff: 01/20/2017

---

# <a name="hosted-web-apps---access-windows-10-features-from-your-web-app"></a>Gehostete Web Apps – Zugriff auf Windows 10-Features über Ihre Web-App

Ihre Webanwendung kann vollständigen Zugriff auf die Universelle Windows-Plattform (UWP) erhalten, einschließlich des Aufrufens von Windows-Runtime-APIs direkt über ein auf einem Server gehostetes Skript, der Nutzung der Cortana-Integration und der Verwendung eines Onlineauthentifizierungsanbieters. Hybrid-Apps werden ebenfalls unterstützt, da Sie lokalen Code, der vom gehosteten Skript aufgerufen werden soll, einbinden und die App-Navigation zwischen Remoteseiten und lokalen Seiten verwalten können.

## <a name="get-started"></a>Erste Schritte

Unabhängig davon, ob Sie auf einem Mac oder einen PC arbeiten, können Sie in wenigen Minuten eine gehostete Web-App erstellen. Für die ersten Schritte sollten Sie die kostenlose, funktionsmäßig nicht eingeschränkte Anwendung [Visual Studio Community 2015](https://www.visualstudio.com/vs/community/) verwenden – besonders dann, wenn Sie auf einem Windows-Gerät arbeiten. Wenn Sie keinen Zugriff auf Visual Studio haben, gibt es einige Optionen, aus denen Sie wählen können. Wenn Sie mit Hilfsprogrammen für die Befehlszeilenschnittstelle (CLI) vertraut sind, lesen Sie [ManifoldJS](http://manifoldjs.com/). Sie können auch [App Studio](http://appstudio.windows.com/) verwenden, ein kostenloses Onlinetool, mit dem Sie Windows 10-Apps schnell und ohne Programmierung erstellen können.

- [Schritt-für-Schritt-Anweisungen für die Konvertierung Ihrer Webanwendung in eine App für die Universelle Windows-Plattform (UWP) auf einem Windows-Computer](hwa-create-windows.md)

- [Schritt-für-Schritt-Anweisungen für die Konvertierung Ihrer Webanwendung in eine App für die Universelle Windows-Plattform (UWP) auf einem Mac-Computer](hwa-create-mac.md)

## <a name="enhance-your-app"></a>Optimieren Sie Ihre App

- Optimieren Sie Ihre App mit [systemeigenen Windows-Runtime-Features](hwa-access-features.md), die Sie direkt über JavaScript aufrufen können.

- Schützen Sie Ihre App, indem Sie Application Content URI-Regeln (ACURs) mithilfe des Content Security Policy (CSP)-Modells festlegen.

- Integrieren Sie die Erkennung von Cortana-Sprachbefehlen in Ihre App.

- Gewähren Sie programmgesteuerten Zugriff auf Benutzerressourcen und Gerätefunktionen, indem Sie entsprechende App-Funktionen freischalten.

- Erstellen Sie einen einfachen und reibungslosen Anmeldungsablauf für Ihre Benutzer, indem ihre Identität mit OpenID und OAuth überprüft wird.

- Beenden Sie den Zustand, dass Sie sich zwischen einer verpackten und einer gehosteten Web-App entscheiden müssen. Durch die Erstellung einer Hybrid-App können Sie die Vorteile beider Modelle nutzen.

## <a name="convert-your-existing-chrome-app"></a>Konvertieren Ihrer vorhandenen Chrome-App

Wir haben das [Konvertieren Ihrer vorhandenen gehosteten Chrome-App](hwa-chrome-conversion.md) in eine gehostete Windows-Web-App einfach gemacht. [ManifoldJS](http://manifoldjs.com/) akzeptiert nun Chrome-Manifeste als Eingaben. Wir haben außerdem ein [CLI-Tool](https://github.com/MicrosoftEdge/hwa-cli) entwickelt, das ein `.appx`-Paket aus Ihren vorhandenen `.zip`- oder `.crx`-Dateien generiert.

## <a name="demos"></a>Demos

- [Contoso-Reise-App](http://contosotravel.azurewebsites.net/)


