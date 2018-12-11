---
title: Unity – Versionskontrolle für Ihr UWP-Projekt
description: Versionsverwaltung für Ihr Unity-UWP.
ms.localizationpriority: medium
ms.topic: article
ms.date: 02/08/2017
ms.openlocfilehash: 064eaf42fe7d664be273cd7e2222fa5d90be1a11
ms.sourcegitcommit: 8921a9cc0dd3e5665345ae8eca7ab7aeb83ccc6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "8873105"
---
# <a name="unity-version-control-your-uwp-project"></a>Unity: Versionskontrolle für Ihr UWP-Projekt

Sie haben Ihr Unity-Spiel für Xbox noch immer nicht in die universelle Windows-Plattform (UWP) portiert?  Lesen Sie zunächst [Portieren von Unity-Spielen für Xbox auf die UWP](development-lanes-unity.md).

Es gibt verschiedene Gründe dafür, Teile Ihres generierten UWP-Verzeichnisses der Versionskontrolle hinzuzufügen. Hierzu zählt unter anderem das Hinzufügen von Abhängigkeiten (z.B. Xbox Live SDK).  Dieses Szenario wird in diesem Lernprogramm als Beispiel herangezogen und hilft Ihnen hoffentlich dabei, die individuellen Anforderungen Ihres Projekts zu erfüllen.

***Hinweis: Wir verwenden Git als Versionskontrolllösung.  Die Konzepte sind jedoch üblicherweise auf andere Lösungen übertragbar.***

Zur Erinnerung: Das Verzeichnis für unser Spiel ***ScrapyardPhoenix*** sieht aktuell wie folgt aus:

![Build-Zielordner](images/build-destination.png)

Und unser UWP-Verzeichnis sieht wie folgt aus:

![UWP-VS-Lösung](images/uwp-vs-solution.png)

In diesem Verzeichnis interessiert uns nur der Ordner ***ScrapyardPhoenix*** (Name Ihres Spiels).  Alles andere ist für unsere Versionskontrolle nicht relevant.

***Noch keine Erfahrung mit GITIGNORE-Dateien?  Siehe [Gitignore](https://git-scm.com/docs/gitignore).***

    ##################################################################
    # The original .gitignore file can be found at
    # https://github.com/github/gitignore/blob/master/Unity.gitignore
    ##################################################################

    # standard ignores for a Unity Project
    ...

    # ignore the whole UWP directory
    /UWP/**

    # except we want to keep... (this line will be modified and removed further down)
    !/UWP/ScrapyardPhoenix/

Wir möchten einige unterschiedliche Dateien und Ordner aus dem Ordner **UWP/ScrapyardPhoenix** auswählen und unserer Versionskontrolle hinzufügen.  Sehen wir uns das Ganze erst einmal im Detail an:

![UWP-Buildverzeichnis](images/uwp-build-directory.png)  

## <a name="folders"></a>Ordner  

`Assets` | ***Enthalten*** | Microsoft Store-Bilder enthält  
`Data`   | ***Ignorieren Sie*** | In denen kompiliert Unity Ihr Projekt auf (Szenen, Shader, Skripts, Prefabs usw.).  
`Dependencies` | ***Enthalten*** | Diese Ordner werden alle UWP-Abhängigkeiten (z. B. xboxlivesdk.dll) gespeichert erstellten  
`Properties` | ***Enthalten*** | Enthält erweiterte Einstellungen, die vom Entwickler geändert werden können  
`Unprocessed` | ***Ignorieren Sie*** | Enthält Unity `.dll` und `.pdb` Dateien  

## <a name="files"></a>Dateien  

`App.cs` | ***Enthalten*** | Der Einstiegspunkt für Ihre UWP-Anwendung; Dies kann geändert und mit anderen Quelldateien erweitert werden  
`Package.appxmanifest` | ***Enthalten*** | App-Paket manifest Quelldatei für Ihr AppX-Paket  
`project.json` | ***Enthalten*** | Beschreibt die NuGet-Pakete Ihre `*.csproj` hängt  
`ScrapyardPhoenix.csproj` | ***Enthalten*** | Beschreibt Ihr UWP-Buildziel. Wenn Sie zusätzliche Abhängigkeiten zu Ihrer UWP-Projekt hinzufügen, dies `*.csproj` -Datei, die Informationen enthält  
`ScrapyardPhoenix.csproj.user` | ***Ignorieren Sie*** | Diese Datei enthält lokaler Benutzerinformationen

## <a name="resulting-gitignore"></a>Resultierende GITIGNORE-Datei

    ##################################################################
    # The original .gitignore file can be found at
    # https://github.com/github/gitignore/blob/master/Unity.gitignore
    ##################################################################

    # standard ignores for a Unity Project
    ...

    # ignore the whole UWP directory
    /UWP/**

    # except we want to keep...
    !/UWP/ScrapyardPhoenix/Assets/*
    !/UWP/ScrapyardPhoenix/Dependencies/*
    !/UWP/ScrapyardPhoenix/Properties/*
    !/UWP/ScrapyardPhoenix/App.cs
    !/UWP/ScrapyardPhoenix/Package.appxmanifest
    !/UWP/ScrapyardPhoenix/project.json
    !/UWP/ScrapyardPhoenix/ScrapyardPhoenix.csproj

Geschafft: Ihre Teammitglieder sind nun mit dem von Ihnen generierten UWP-Projekt synchronisiert. Nun können Sie Ihrem UWP-Projekt problemlos zusätzliche Ressourcen, Quellen und Abhängigkeiten hinzufügen.

Einige weitere Versionsverwaltungsbeispiele für den UWP-Ordner finden Sie [hier](https://bitbucket.org/Unity-Technologies/windowsstoreappssamples/overview).

## <a name="adding-dependencies-to-your-uwp-app"></a>Hinzufügen von Abhängigkeiten zu Ihrer UWP-App

Fügen Sie Abhängigkeiten zu DLL- und WINMD-Dateien hinzu, indem Sie diese im Unterordner **Unity Assets** des Ordners **Plug-Ins** ablegen und auswählen. Legen Sie anschließend im Paketprüfungstool die Plattform-Zieleinstellungen fest.

![UWP-Lösung](images/uwp-solution.PNG)

***ScrapyardPhoenix (Universal Windows)*** ist das Projekt, dem Sie einen Verweis (etwa auf das Xbox Live SDK) hinzufügen würden.

## <a name="see-also"></a>Weitere Informationen
- [Portieren vorhandener Spiele zu Xbox](development-lanes-landing.md)
- [UWP auf XboxOne](index.md)
