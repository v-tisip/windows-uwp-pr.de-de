---
author: rmpablos
title: "Einrichten automatisierter Builds für UWP-Apps"
description: "Erfahren Sie, wie Sie automatisierte Builds konfigurieren, um Pakete zum Querladen oder zum Übermitteln an den Store zu erzeugen."
ms.author: wdg-dev-content
ms.date: 02/15/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.assetid: f9b0d6bd-af12-4237-bc66-0c218859d2fd
ms.openlocfilehash: f4c68af97e5d5b11a0c5320c9fa6040b9ab94e5a
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="set-up-automated-builds-for-your-uwp-app"></a>Einrichten automatisierter Builds für UWP-Apps

Mithilfe von Visual Studio Team Services (VSTS) können Sie automatisierte Builds für UWP-Projekte erstellen. In diesem Artikel werden verschiedene Erstellungsmöglichkeiten erläutert.  Außerdem wird erläutert, wie Sie diese Aufgaben über die Befehlszeile ausführen, um die Integration in andere Buildsysteme, z.B. AppVeyor, zu ermöglichen. 

## <a name="select-the-right-type-of-build-agent"></a>Die Wahl des richtigen Build-Agents

Wählen Sie aus, welche Art von Build-Agent VSTS beim Ausführen des Buildprozesses verwenden soll. Ein gehosteter Build-Agent wird mit den gängigsten Tools und SDKs bereitgestellt und bietet Unterstützung für die meisten Szenarien. Weitere Informationen finden Sie im Artikel zu [Software auf dem gehosteten Buildserver](https://www.visualstudio.com/docs/build/admin/agents/hosted-pool#software). Wenn Sie jedoch mehr Kontrolle über die Buildschritte benötigen, können Sie auch einen benutzerdefinierten Build-Agent erstellen. Die folgende Tabelle soll Sie bei der richtigen Entscheidung unterstützen.

|**Szenario**|**Benutzerdefinierter Agent**|**Gehosteter Build-Agent**|
-------------|----------------|----------------------|
|Grundlegender UWP-Build (einschließlich .NET Native)|:white_check_mark:|:white_check_mark:|
|Generieren von Paketen für das Querladen|:white_check_mark:|:white_check_mark:|
|Generieren von Paketen für die Übermittlung an den Store|:white_check_mark:|:white_check_mark:|
|Verwenden benutzerdefinierter Zertifikate|:white_check_mark:||
|Spezieller Build für ein benutzerdefiniertes Windows SDK|:white_check_mark:||
|Ausführen von Komponententests|:white_check_mark:||
|Verwenden inkrementeller Builds|:white_check_mark:||

>Hinweis: Wenn Sie beabsichtigen, das Windows Anniversary Update SDK (Build 14393) für den Build zu verwenden, müssen Sie Ihren benutzerdefinierten Build-Agent einrichten, da der gehostete Buildpool nur die SDKs 10586 und 10240 unterstützt. Weitere Informationen zum [Auswählen einer UWP-Version](https://msdn.microsoft.com/windows/uwp/updates-and-versions/choose-a-uwp-version).

#### <a name="create-a-custom-build-agent-optional"></a>Erstellen eines benutzerdefinierten Build-Agents (optional)

Wenn Sie einen benutzerdefinierten Build-Agent erstellen möchten, benötigen Sie die Tools für die universelle Windows-Plattform. Diese Tools sind Bestandteil von Visual Studio. Sie können Visual Studio Community Edition verwenden.

Weitere Informationen finden Sie unter [Bereitstellen eines Agents unter Windows](https://www.visualstudio.com/docs/build/admin/agents/v2-windows). 

Zum Ausführen von UWP-Komponententests müssen Sie folgende Schritte ausführen: •    Bereitstellen und Starten der App. •    Ausführen des VSTS-Agents im interaktiven Modus. •    Konfigurieren des Agents für die automatische Anmeldung nach einem Neustart.

Wir beschreiben jetzt, wie ein automatisierter Build eingerichtet wird.

## <a name="set-up-an-automated-build"></a>Einrichten eines automatisierten Builds
Wir beginnen mit der standardmäßigen UWP-Builddefinition, die in VSTS verfügbar ist, und erläutern dann, wie Sie diese Definition so konfigurieren, dass erweiterte Buildaufgaben ausgeführt werden können.

**Hinzufügen des Projektzertifikats zu einem Quellcoderepository**

VSTS unterstützt sowohl TFS- als auch Git-basierte Coderepositorys.  
Bei Verwendung eines Git-Repositorys fügen Sie die Zertifikatdatei Ihres Projekts dem Repository hinzu, damit der Build-Agent das APPX-Paket signieren kann. Andernfalls wird die Zertifikatdatei vom Git-Repository ignoriert. Zum Hinzufügen der Zertifikatdatei zum Repository klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf die Zertifikatdatei und wählen dann im Kontextmenü den Befehl „Ignorierte Datei zur Quellcodeverwaltung hinzufügen“ aus. 

![Einschließen eines Zertifikats](images/building-screen1.png)

Die [erweiterte Zertifikatverwaltung](#certificates-best-practices) wird weiter unten in diesem Leitfaden erläutert. 

Um die erste Builddefinition in VSTS zu erstellen, navigieren Sie zur Registerkarte „Builds“ und wählen dann die Schaltfläche „+“ aus.

![Erstellen der Builddefinition](images/building-screen2.png)

Wählen Sie in der Liste der Builddefinitionsvorlagen die Vorlage *Universelle Windows-Plattform* aus.

![Auswählen des UWP-Builds](images/building-screen3.png)

Diese Builddefinition enthält die folgenden Buildaufgaben:

- NuGet-Wiederherstellung **\*.sln
- Projektmappe erstellen **\*.sln
- Symbole veröffentlichen
- Artefakt veröffentlichen: Drop

#### <a name="configure-the-nuget-restore-build-task"></a>Konfigurieren der Buildaufgabe „NuGet-Wiederherstellen“

Mit dieser Aufgabe werden die in Ihrem Projekt definierten NuGet-Pakete wiederhergestellt. Für einige Pakete ist eine benutzerdefinierte Version von „NuGet.exe“ erforderlich. Bei Verwendung eines Pakets, das eine benutzerdefinierte Version erfordert, verweisen Sie erst in Ihrem Repository auf die Version von „NuGet.exe“ und dann in der erweiterten Eigenschaft *Pfad zu „NuGet.exe“*.

![Standardbuilddefinition](images/building-screen4.png)

#### <a name="configure-the-build-solution-build-task"></a>Konfigurieren der Buildaufgabe „Projektmappe erstellen“

Mit dieser Aufgabe wird eine im Arbeitsordner enthaltene Projektmappe in Binärdateien kompiliert, und die AppX-Ausgabedatei wird erstellt. In dieser Aufgabe werden MSBuild-Argumente verwendet.  Sie müssen den Wert dieser Argumente angeben. Orientieren Sie sich an der folgenden Tabelle. 

|**MSBuild-Argument**|**Wert**|**Beschreibung**|
|--------------------|---------|---------------|
|AppxPackageDir|$(Build.ArtifactStagingDirectory)\AppxPackages|Definiert den Ordner, in dem die generierten Artefakte gespeichert werden.|
|AppxBundlePlatforms|$(Build.BuildPlatform)|Sie können festlegen, welche Plattformen im Bündel enthalten sein sollen.|
|AppxBundle|Always|Erstellt ein APPX-Bündel mit den APPX-Dateien für die angegebene Plattform.|
|**UapAppxPackageBuildMode**|StoreUpload|Definiert die Art des zu generierenden APPX-Pakets. (Standardmäßig nicht enthalten)|


Wenn Sie Ihre Projektmappe über die Befehlszeile oder mit einem anderen Buildsystem erstellen möchten, führen Sie MSBuild mit diesen Argumenten aus.

```
/p:AppxPackageDir="$(Build.ArtifactStagingDirectory)\AppxPackages\\"  
/p:UapAppxPackageBuildMode=StoreUpload 
/p:AppxBundlePlatforms="$(Build.BuildPlatform)"
/p:AppxBundle=Always
```

Die mit der $()-Syntax definierten Parameter sind Variablen, die in der Builddefinition definiert sind und sich in anderen Buildsystemen unterscheiden.

![Standardvariablen](images/building-screen5.png)

Unter [Verwenden von Buildvariablen](https://www.visualstudio.com/docs/build/define/variables) sind alle vordefinierten Variablen aufgeführt.

#### <a name="configure-the-publish-artifact-build-task"></a>Konfigurieren der Buildaufgabe „Artefakt veröffentlichen“ 
Mit dieser Aufgabe werden die generierten Artefakte in VSTS gespeichert. Sie werden auf der Registerkarte „Artefakte“ auf der Seite mit den Buildergebnissen angezeigt. VSTS verwendet den zuvor definierten Ordner `$Build.ArtifactStagingDirectory)\AppxPackages`.

![Artefakte](images/building-screen6.png)

Da wir die `UapAppxPackageBuildMode`-Eigenschaft auf `StoreUpload` festgelegt haben, enthält der Artefaktordner das Paket, das Sie in den Store hochladen („appxupload“), und die Pakete, die das Querladen ermöglichen („appxbundle“).


>Hinweis: Der VSTS-Agent behält standardmäßig die letzten generierten APPX-Pakete bei. Wenn Sie nur die Artefakte des aktuellen Builds speichern möchten, konfigurieren Sie den Build so, dass das Verzeichnis mit Binärdateien bereinigt wird. Fügen Sie dazu eine Variable namens `Build.Clean` hinzu, und legen Sie sie auf den Wert `all` fest. Weitere Informationen finden Sie unter [Angeben des Repositorys](https://www.visualstudio.com/docs/build/define/repository#how-can-i-clean-the-repository-in-a-different-way).

#### <a name="the-types-of-automated-builds"></a>Typen automatisierter Builds
Als Nächstes verwenden Sie die Builddefinition zum Erstellen eines automatisierten Builds. In der folgenden Tabelle werden die einzelnen Typen automatisierter Builds beschrieben, die Sie erstellen können. 

|**Buildtyp**|**Artefakt**|**Empfohlene Häufigkeit**|**Beschreibung**|
|-----------------|------------|-------------------------|---------------|
|Continuous Integration|Buildprotokoll, Testergebnisse|Jeder Commit|Dieser Buildtyp ist schnell und wird mehrmals täglich ausgeführt.|
|Continuous Deployment-Build zum Querladen|Bereitstellungspakete|Täglich |Dieser Buildtyp kann Komponententests enthalten, dauert jedoch etwas länger. Er unterstützt manuelle Tests und kann in andere Tools, wie z.B. HockeyApp, integriert werden.|
|Continuous Deployment-Build, durch den ein Paket an den Store übermittelt wird|Veröffentlichungspakete|Bedarfsgesteuert|Durch diesen Buildtyp wird ein Paket erstellt, das Sie im Store veröffentlichen können.|

Im Folgenden wird die Konfiguration der einzelnen Typen beschrieben.


## <a name="set-up-a-continuous-integration-ci-build"></a>Einrichten eines Continuous Integration (CI)-Builds 
Dieser Buildtyp ermöglicht die schnelle Diagnose codebezogener Probleme. Er wird in der Regel nur für eine Plattform ausgeführt und muss nicht durch die .NET Native-Toolkette verarbeitet werden. Außerdem können Sie mit CI-Builds Komponententests ausführen, durch die ein Bericht mit Testergebnissen erstellt wird.  

Wenn Sie UWP-Komponententests im Rahmen Ihres CI-Builds ausführen möchten, müssen Sie einen benutzerdefinierten Build-Agent anstelle des gehosteten Build-Agents verwenden.

>Hinweis: Wenn Sie mehr als eine App in der gleichen Projektmappe bündeln, erhalten Sie möglicherweise eine Fehlermeldung. Unterstützung beim Beheben dieses Fehlers finden Sie im Thema [Beheben von Fehlern, die beim Bündeln von mehr als einer App in derselben Projektmappe auftreten](#bundle-errors). 


### <a name="configure-a-ci-build-definition"></a>Konfigurieren einer CI-Builddefinition
Verwenden Sie die UWP-Standardvorlage, um eine Builddefinition zu erstellen. Konfigurieren Sie dann den Trigger, der bei jedem Einchecken ausgeführt werden soll.  

![CI-Trigger](images/building-screen7.png)

Da der CI-Build nicht für Benutzer bereitgestellt wird, ist es ratsam, unterschiedliche Versionsnummern zu verwenden, um Verwechslungen mit den CD-Builds zu vermeiden. Beispiel: `$(BuildDefinitionName)_0.0.$(DayOfYear)$(Rev:.r)`.


#### <a name="configure-a-custom-build-agent-for-unit-testing"></a>Konfigurieren eines benutzerdefinierten Build-Agents für Komponententests

1. Aktivieren Sie zuerst den Entwicklermodus auf Ihrem PC. Siehe „Aktivieren Ihres Geräts für die Entwicklung“. 2. Ermöglichen Sie die Ausführung des Diensts als interaktiver Prozess. Siehe „Bereitstellen eines Agents unter Windows“. 3. Stellen Sie das Signaturzertifikat für den Agent bereit.

Doppelklicken Sie dazu auf die CER-Datei, wählen Sie „Lokaler Computer“ aus, und wählen Sie dann den Speicher für vertrauenswürdige Personen aus.

<span id="uwp-unit-tests" />
### <a name="configure-the-build-definition-to-run-uwp-unit-tests"></a>Konfigurieren der Builddefinition für die Ausführung von UWP-Komponententests
Verwenden Sie zum Ausführen von Komponententests den Visual Studio Test-Buildschritt.


![Hinzufügen von Komponententests](images/building-screen8.png)

Da UWP-Komponententests im Kontext einer bestimmten APPX-Datei ausgeführt werden, ist es nicht möglich, das generierte Bündel zu verwenden. Außerdem müssen Sie den Pfad zu einer konkreten APPX-Plattformdatei angeben. Beispiel:

```
$(Build.ArtifactStagingDirectory)\AppxPackages\MyUWPApp.UnitTest\x86\MyUWPApp.UnitTest_$(AppxVersion)_x86.appx
```

>Hinweis: Verwenden Sie folgenden Befehl, um die Komponententests lokal über die Befehlszeile auszuführen:
`"%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Common7\IDE\CommonExtensions\Microsoft\TestWindow\vstest.console.exe"`

#### <a name="access-test-results"></a>Zugreifen auf Testergebnisse
In VSTS werden auf der Seite „Buildzusammenfassung“ Testergebnisse für jeden Build angezeigt, der Komponententests ausführt.  Dort können Sie die Seite „Testergebnisse“ öffnen, um weitere Details zu den Testergebnissen zu erhalten. 

![Testergebnisse](images/building-screen9.png)

#### <a name="improve-the-speed-of-a-ci-build"></a>Verbessern der Geschwindigkeit eines CI-Builds
Wenn Sie Ihren CI-Build nur verwenden möchten, um die Qualität der Eincheckvorgänge zu überwachen, können Sie Ihre Buildzeiten verringern.

#### <a name="to-improve-the-speed-of-a-ci-build"></a>So verbessern Sie die Geschwindigkeit eines CI-Builds
1.    Erstellen Sie den Build nur für eine Plattform.
2.    Bearbeiten Sie die BuildPlatform-Variable, um nur x86 zu verwenden. ![CI-Konfiguration](images/building-screen10.png) 
3.    Fügen Sie im Buildschritt „/p:AppxBundle=Never“ zur Eigenschaft „MSBuild-Argumente“ hinzu, und legen Sie die Eigenschaft „Plattform“ fest. ![Konfigurieren der Plattform](images/building-screen11.png)
4.    Deaktivieren Sie im Komponententestprojekt .NET Native. 

Öffnen Sie dazu die Projektdatei, und legen Sie die `UseDotNetNativeToolchain`-Eigenschaft in den Projekteigenschaften auf `false` fest.

>Hinweis: Da die Verwendung der .NET Native-Toolkette immer noch einen wichtigen Bestandteil des Workflows darstellt, sollten Sie sie weiterhin zum Testen von Releasebuilds verwenden. 

<span id="bundle-errors" />
#### <a name="address-errors-that-appear-when-you-bundle-more-than-one-app-in-the-same-solution"></a>Beheben von Fehlern, die beim Bündeln von mehr als einer App in derselben Projektmappe auftreten 
Wenn Sie Ihrer Projektmappe mehr als ein UWP-Projekt hinzufügen und dann versuchen, ein Bündel zu erstellen, erhalten Sie möglicherweise eine mit der folgenden vergleichbare Fehlermeldung: 

```
MakeAppx(0,0): Error : Error info: error 80080204: The package with file name "AppOne.UnitTests_0.1.2595.0_x86.appx" and package full name "8ef641d1-4557-4e33-957f-6895b122f1e6_0.1.2595.0_x86__scrj5wvaadcy6" is not valid in the bundle because it has a different package family name than other packages in the bundle
```

Dieser Fehler tritt auf, da auf Projektmappenebene nicht eindeutig ist, welche App im Bündel enthalten sein soll. Um dieses Problem zu beheben, öffnen Sie jede Projektdatei und fügen am Ende des ersten `<PropertyGroup>`-Elements die folgenden Eigenschaften hinzu:

|**Projekt**|**Eigenschaften**|
|-------|----------|
|App|`<AppxBundle>Always</AppxBundle>`|
|UnitTests|`<AppxBundle>Never</AppxBundle>`|

Entfernen Sie dann das MSBuild-Argument `AppxBundle` aus dem Buildschritt.

## <a name="set-up-a-continuous-deployment-build-for-sideloading"></a>Einrichten eines Continuous Deployment-Builds zum Querladen
Nach Abschluss dieses Buildtyps können Benutzer die APPXBUNDLE-Datei aus dem Artefaktabschnitt der Seite mit den Buildergebnissen herunterladen. Wenn Sie Betatests für die App durchführen möchten, indem Sie eine komplexere Verteilung erstellen, können Sie den HockeyApp-Dienst verwenden. Dieser Dienst bietet erweiterte Funktionen für Betatests, Benutzeranalysen und Absturzdiagnosen.


### <a name="applying-version-numbers-to-your-builds"></a>Anwenden von Versionsnummern auf Builds

Die Manifestdatei enthält die Versionsnummer der App.  Aktualisieren Sie die Manifestdatei im Repository der Quellcodeverwaltung, um die Versionsnummer zu ändern. Eine weitere Möglichkeit zum Aktualisieren der Versionsnummer Ihrer App besteht darin, die von VSTS generierte Buildnummer zu verwenden und dann das App-Manifest zu ändern, direkt bevor Sie die App kompilieren. Sie dürfen diese Änderungen nur nicht im Quellcoderepository committen.

Sie müssen das Format der Versionsbuildnummer in der Builddefinition definieren und dann mit der resultierenden Versionsnummer das AppxManifest und optional die Dateien „AssemblyInfo.cs“ aktualisieren, bevor Sie kompilieren.

Definieren Sie das Buildnummernformat auf der Registerkarte *Allgemein* der Builddefinition:

![Buildversion](images/building-screen12.png) 

Angenommen, Sie legen das Buildnummernformat auf den folgenden Wert fest:  
``` 
$(BuildDefinitionName)_1.1.$(DayOfYear)$(Rev:r).0 
```

In diesem Fall generiert VSTS eine Versionsnummer wie die Folgende:
```
CI_MyUWPApp_1.1.2501.0
```

>Hinweis: Für den Store ist es erforderlich, dass die letzte Zahl in der Versionsangabe 0 lautet.

Damit Sie die Versionsnummer extrahieren und auf die Manifestdateien und/oder `AssemblyInfo`-Dateien anwenden können, verwenden Sie ein benutzerdefiniertes PowerShell-Skript ([hier](https://go.microsoft.com/fwlink/?prd=12560&pver=14&plcid=0x409&clcid=0x9&ar=DevCenter&sar=docs) verfügbar). Das Skript liest die Versionsnummer aus der `BUILD_BUILDNUMBER`-Umgebungsvariablen und ändert dann die AssemblyInfo- und AppxManifest-Dateien. Sie müssen dieses Skript Ihrem Quellrepository hinzufügen und dann eine PowerShell-Buildaufgabe konfigurieren, wie hier veranschaulicht:


![Aktualisieren der Version](images/building-screen13.png) 

Die `$(AppxVersion)`-Variable enthält die Versionsnummer. Sie können diese Nummer in anderen Buildschritten verwenden. 


#### <a name="optional-integrate-with-hockeyapp"></a>Optional: Integration in HockeyApp
Installieren Sie zuerst die Visual Studio-Erweiterung [HockeyApp](https://marketplace.visualstudio.com/items?itemName=ms.hockeyapp). 

>Hinweis: Sie müssen diese Erweiterung als VSTS-Administrator installieren. 


![HockeyApp](images/building-screen14.png) 

Konfigurieren Sie als Nächstes die HockeyApp-Verbindung mithilfe dieser Anleitung: [How to use HockeyApp with Visual Studio Team Services (VSTS) or Team Foundation Server (TFS)](https://support.hockeyapp.net/kb/third-party-bug-trackers-services-and-webhooks/how-to-use-hockeyapp-with-visual-studio-team-services-vsts-or-team-foundation-server-tfs). Sie können Ihr Microsoft-Konto, ein Social Media-Konto oder einfach eine E-Mail-Adresse verwenden, um Ihr HockeyApp-Konto einzurichten. Der kostenlose Plan umfasst zwei Apps, einen Besitzer und keine Dateneinschränkungen.

Anschließend können Sie eine HockeyApp-App manuell erstellen oder eine vorhandene APPX-Paketdatei hochladen. Weitere Informationen finden Sie unter [How to create a new app](https://support.hockeyapp.net/kb/app-management-2/how-to-create-a-new-app).  

Um eine vorhandene APPX-Paketdatei zu verwenden, fügen Sie einen Buildschritt hinzu und legen den Parameter für den binären Dateipfad des Buildschritts fest. 

![Konfigurieren von HockeyApp](images/building-screen15.png) 

Um diesen Parameter festzulegen, kombinieren Sie den Namen der App, die AppxVersion-Variable und die unterstützten Plattformen in einer Zeichenfolge wie dieser:

``` 
$(Build.ArtifactStagingDirectory)\AppxPackages\MyUWPApp_$(AppxVersion)_Test\MyUWPApp_$(AppxVersion)_x86_x64_ARM.appxbundle
```

>Hinweis: Obwohl die HockeyApp-Aufgabe die Möglichkeit bietet, den Pfad zur Symboldatei anzugeben, empfiehlt es sich, die Symbole (APPXSYM-Dateien) in das Bündel einzuschließen.

Die Installation und Ausführung eines quergeladenen Pakets wird [weiter unten](#sideloading-best-practices) in diesem Leitfaden erläutert. 

## <a name="set-up-a-continuous-deployment-build-that-submits-a-package-to-the-store"></a>Einrichten eines Continuous Deployment-Builds, durch den ein Paket an den Store übermittelt wird 

Um Pakete für die Übermittlung an den Store zu generieren, verknüpfen Sie die App mithilfe des Assistenten für die Store-Verknüpfung in Visual Studio mit dem Store.

![Verknüpfen mit dem Store](images/building-screen16.png) 

>Hinweis: Dieser Assistent generiert eine Datei mit dem Namen „Package.StoreAssociation.xml“, die die Informationen zur Store-Verknüpfung enthält. Wenn Sie den Quellcode in einem öffentlichen Repository wie GitHub speichern, enthält diese Datei alle reservierten Namen der App für dieses Konto. Sie können diese Datei vor der Veröffentlichung ausschließen oder löschen.

Wenn Sie keinen Zugriff auf das Dev Center-Konto haben, mit dem die App veröffentlicht wurde, können Sie die Anweisungen in diesem Dokument befolgen: [Building an app for a 3rd party? How to package their Store app](https://blogs.windows.com/buildingapps/2015/12/15/building-an-app-for-a-3rd-party-how-to-package-their-store-app/#e35YzR5aRG6uaBqK.97). 

Anschließend müssen Sie sicherstellen, dass der Buildschritt den folgenden Parameter enthält:

```
/p:UapAppxPackageBuildMode=StoreUpload 
```

Dadurch wird die APPXUPLOAD-Datei generiert, die an den Store übermittelt werden kann.


#### <a name="configure-automatic-store-submission"></a>Konfigurieren der automatischen Übermittlung an den Store

Verwenden Sie für die Integration in die Store-API die Visual Studio Team Services-Erweiterung für den Windows Store, und senden Sie das APPXUPLOAD-Paket an den Store.

Sie müssen Ihr Dev Center-Konto mit Azure Active Directory (AD) verbinden und dann eine App in AD erstellen, um die Anforderungen zu authentifizieren. Befolgen Sie dazu die Anweisungen auf der Seite der Erweiterung. 

Nachdem Sie die Erweiterung konfiguriert haben, können Sie die Buildaufgabe hinzufügen und mit der App-ID und dem Speicherort der APPXUPLOAD-Datei konfigurieren.

![Konfigurieren im Dev Center](images/building-screen17.png) 

Der Wert des `Package File`-Parameters lautet dabei:

```
$(Build.ArtifactStagingDirectory)\
AppxPackages\MyUWPApp__$(AppxVersion)_x86_x64_ARM_bundle.appxupload
```

>Hinweis: Sie müssen diesen Build manuell aktivieren. Sie können ihn zum Aktualisieren vorhandener Apps verwenden, aber nicht für die erste Übermittlung an den Store. Weitere Informationen finden Sie unter [Erstellen und Verwalten von Store-Übermittlungen mit WindowsStore-Diensten](https://msdn.microsoft.com/windows/uwp/monetize/create-and-manage-submissions-using-windows-store-services).

## <a name="best-practices"></a>Bewährte Methoden

<span id="sideloading-best-practices"/>
### <a name="best-practices-for-sideloading-apps"></a>Bewährte Methoden für das Querladen von Apps

Wenn Sie Ihre App verteilen möchten, ohne sie im Store zu veröffentlichen, können Sie die App direkt auf Geräte querladen, solange die Geräte das Zertifikat, das zum Signieren des App-Pakets verwendet wurde, als vertrauenswürdig ansehen. 

Verwenden Sie zum Installieren von Apps das PowerShell-Skript `Add-AppDevPackage.ps1`. Das Skript fügt das Zertifikat dem Abschnitt für vertrauenswürdige Stammzertifizierungsstellen des lokalen Computers hinzu und installiert oder aktualisiert dann die APPX-Datei.

#### <a name="sideloading-your-app-with-the-windows-10-anniversary-update"></a>Querladen einer App mit dem Windows10 Anniversary Update
Im Windows10 Anniversary Update können Sie auf die APPXBUNDLE-Datei doppelklicken und die App mithilfe der Schaltfläche „Installieren“ in einem Dialogfeld installieren. 


![Querladen in rs1](images/building-screen18.png) 

>Hinweis: Durch diese Methode werden keine Zertifikate oder zugehörigen Abhängigkeiten installiert.

Wenn Sie Ihre APPX-Pakete von einer Website wie VSTS oder HockeyApp verteilen möchten, müssen Sie diese Website der Liste vertrauenswürdiger Websites in Ihrem Browser hinzufügen. Andernfalls wird die Datei von Windows als gesperrt markiert. 

<span id="certificates-best-practices"/>
### <a name="best-practices-for-signing-certificates"></a>Bewährte Methoden für das Signieren von Zertifikaten 
Visual Studio generiert ein Zertifikat für jedes Projekt. Dadurch wird es schwierig, eine geordnete Liste gültiger Zertifikate zu führen. Wenn Sie mehrere Apps erstellen möchten, können Sie ein einzelnes Zertifikat zum Signieren aller Apps erstellen. Danach kann jedes Gerät, für das das Zertifikat als vertrauenswürdig gilt, alle Ihre Apps querladen, ohne dass ein weiteres Zertifikat installiert werden muss. Weitere Informationen finden Sie unter [Erstellen eines Signaturzertifikats für ein App-Paket](https://msdn.microsoft.com/library/windows/desktop/jj835832(v=vs.85).aspx).


#### <a name="create-a-signing-certificate"></a>Erstellen eines Signaturzertifikats
Verwenden Sie das Tool [MakeCert.exe](https://msdn.microsoft.com/library/windows/desktop/ff548309.aspx), um ein Zertifikat zu erstellen. Im folgenden Beispiel wird ein Zertifikat mit dem Tool „MakeCert.exe“ erstellt.

```
MakeCert /n publisherName /r /h 0 /eku "1.3.6.1.5.5.7.3.3,1.3.6.1.4.1.311.10.3.13" /e expirationDate /sv MyKey.pvk MyKey.cer
```

Anschließend können Sie mit dem Tool „Pvk2Pfx“ eine PFX-Datei generieren, die den kennwortgeschützten privaten Schlüssel enthält.

Stellen Sie diese Zertifikate für jede Computerrolle bereit:

|**Computer**|**Verwendungszweck**|**Zertifikat**|**Zertifikatspeicher**|
|-----------|---------|---------------|---------------------|
|Entwickler/Buildcomputer|Signieren von Builds|MyCert.PFX|Aktueller Benutzer/Persönlich|
|Entwickler/Buildcomputer|Ausführen|MyCert.cer|Lokaler Computer/Vertrauenswürdige Personen|
|Benutzer|Ausführen|MyCert.cer|Lokaler Computer/Vertrauenswürdige Personen|

>Hinweis: Sie können auch ein Unternehmenszertifikat verwenden, dem Ihre Benutzer bereits vertrauen.

#### <a name="sign-your-uwp-app"></a>Signieren der UWP-App
Visual Studio und MSBuild bieten verschiedene Möglichkeiten zum Verwalten des Zertifikats, das Sie zum Signieren der App verwenden:

Eine Möglichkeit besteht darin, das Zertifikat mit dem privaten Schlüssel (normalerweise in Form einer PFX-Datei) in Ihre Projektmappe aufzunehmen und dann in der Projektdatei auf die PFX-Datei zu verweisen. Zu diesem Zweck können Sie die Registerkarte „Paket“ des Manifest-Editors verwenden.


![Erstellen eines Zertifikats](images/building-screen19.png) 

Eine weitere Möglichkeit besteht darin, das Zertifikat auf dem Buildcomputer („Current User/Personal“) zu installieren und dann die Option „Aus Zertifikatspeicher auswählen“ zu verwenden. Dadurch wird der Fingerabdruck des Zertifikats in der Projektdatei angegeben. Auf diese Weise wird das Zertifikat auf allen Computern installiert, die zum Erstellen des Projekts verwendet werden.

#### <a name="trust-the-signing-certificate-in-the-target-devices"></a>Akzeptieren der Vertrauenswürdigkeit des Signaturzertifikats auf den Zielgeräten
Das Zertifikat muss für ein Zielgerät vertrauenswürdig sein, bevor die App darauf installiert werden kann. 

Registrieren Sie den öffentlichen Schlüssel des Zertifikats im Zertifikatspeicher des lokalen Computers unter dem Knoten für vertrauenswürdige Personen oder für den vertrauenswürdigen Stamm.

Die einfachste Möglichkeit zum Registrieren des Zertifikats besteht darin, in der CER-Datei zu doppelklicken und dann die Schritte im Assistenten auszuführen, um das Zertifikat im Speicher des lokalen Computers und im Speicher für vertrauenswürdige Personen zu speichern.

## <a name="related-topics"></a>Verwandte Themen
* [Erstellen einer .NET-App für Windows](https://www.visualstudio.com/docs/build/get-started/dot-net) 
* [Verpacken von UWP-Apps](https://msdn.microsoft.com/windows/uwp/packaging/packaging-uwp-apps)
* [Querladen von branchenspezifischen Apps in Windows10](https://technet.microsoft.com/itpro/windows/deploy/sideload-apps-in-windows-10)
* [Erstellen eines Signaturzertifikats für ein App-Paket](https://msdn.microsoft.com/library/windows/desktop/jj835832(v=vs.85).aspx)
