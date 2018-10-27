---
author: stevewhims
ms.assetid: 08C8F359-E8B6-4A45-8F4B-8A1962F0CE38
description: Microsoft Visual Studio ist für Windows gleichbedeutend mit Xcode für iOS und Mac OS. In dieser exemplarischen Vorgehensweise möchten wir Ihnen helfen, sich mit der Verwendung von Visual Studio vertraut zu machen.
title: Erstellen eines Projekts in Visual Studio
ms.author: stwhi
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 3b10d615146c8989231c4fe36ad9588716c59c34
ms.sourcegitcommit: 086001cffaf436e6e4324761d59bcc5e598c15ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "5705257"
---
# <a name="getting-started-creating-a-project"></a>Erste Schritte: Erstellen eines Projekts

## <a name="creating-a-project"></a>Erstellen eines Projekts

Microsoft Visual Studio ist für Windows gleichbedeutend mit Xcode für iOS und Mac OS. In dieser exemplarischen Vorgehensweise möchten wir Ihnen helfen, sich mit der Verwendung von Visual Studio vertraut zu machen. Sie lernen die Grundlagen kennen, die Sie beherrschen müssen, um mit der Entwicklung zu beginnen. Jedes Mal, wenn Sie eine App erstellen, führen Sie Schritte aus, die sich an dieser Beschreibung orientieren.

Im folgenden Video werden Xcode und Visual Studio verglichen.

> [!VIDEO https://channel9.msdn.com/Blogs/One-Dev-Minute/Comparing-Xcode-to-Visual-Studio/player]

Sie werden außerdem den [Blogbeitrag zum Erstellen von Apps für Windows](https://blogs.windows.com/buildingapps/2016/01/27/visual-studio-walkthrough-for-ios-developers/) sehr hilfreich finden.

Erstellen einer app für Windows 10 (formeller als universelle Windows-Plattform (UWP)-app bezeichnet) entspricht in etwa dem Erstellen einer iOS-app mit Storyboards. Die Windows 10-app wird häufig über mehrere Seiten jeder Seite mit einem anderen Teil der Benutzeroberfläche, z. B. eine Website erstellt. Jeder Seite sind normalerweise zwei Quelldateien zugeordnet: eine zum Speichern der Benutzeroberfläche im unter [Übersicht über XAML](https://msdn.microsoft.com/library/windows/apps/mt185595) definierten Format und eine für den Quellcode, häufig C#. Beim Interagieren mit der App navigiert der Benutzer zwischen diesen Seiten. In dieser exemplarischen Vorgehensweise wird eine App mit zwei Seiten erstellt.

**Hinweis:** ein wichtiges Feature von Windows 10-apps ist die Tatsache, dass der gleiche Quellcode und die gleiche API-Satz, unabhängig von der Plattform für Sie verfügbar ist. Wie Sie wissen, können Sie beim Schreiben einer universellen iOS-App für iPhone und iPad zur Laufzeit feststellen, auf welcher Plattform Ihre App ausgeführt wird, und entsprechende Maßnahmen ergreifen. Auf ähnliche Weise können Windows 10-apps, zur Laufzeit, mitteilen welchem Gerät, das Sie ausgeführt werden. Bei einer UWP-App entfallen die \#ifdefs in Ihrem Quellcode zum Erstellen von Telefon- bzw. Desktopbuilds. Windows 10-apps verwenden praktischerweise auf intelligente Weise auch ihre Benutzeroberflächen-Steuerelemente abhängig vom Gerät: z. B. Ihre app kann ein Datumsauswahl-Steuerelement verweisen, und das Steuerelement wird automatisch suchen und je nachdem, ob sie verfügt auf einem Desktop- oder telefonbildschirm ausgeführt. Der Quellcode bleibt jedoch unverändert.

Sehen wir uns an, wie wir eine Windows 10-app erstellen können. Führen Sie zuerst Visual Studio2013 aus. Bei der ersten Ausführung des Programms werden Sie von Visual Studio zum Anfordern einer Entwicklerlizenz aufgefordert. Mithilfe einer Entwicklerlizenz können Sie UWP-Apps auf Ihrem lokalen Computer installieren und testen, bevor Sie sie an den Microsoft Store senden. Befolgen Sie zum Anfordern einer Lizenz die Bildschirmanweisungen, um sich mit einem Microsoft-Konto anzumelden. Wenn Sie kein Microsoft-Konto haben, klicken Sie im Dialogfeld **Entwicklerlizenz** auf den Link **Registrieren** und befolgen Sie die Bildschirmanweisungen.

Zum Vergleich: beim Starten von Xcode wird zunächst der Bildschirm **Willkommen zu Xcode** angezeigt, der der folgenden Abbildung ähnelt.

![Xcode-Willkommensbildschirm](images/ios-to-uwp/ios-to-uwp-xcode-welcome.png)

Visual Studio ist sehr ähnlich aufgebaut. Es wird eine **Startseite** ähnlich der Seite in der folgenden Abbildung angezeigt.

![Visual Studio-Startbildschirm](images/ios-to-uwp/ios-to-uwp-vs-welcome.png)

Zum Erstellen einer neuen App müssen Sie zunächst ein Projekt anlegen. Gehen Sie hierzu folgendermaßen vor:

-   Tippen Sie im Bereich **Start** auf **Neues Projekt**.
-   Tippen Sie auf das Menü **Datei** und dann auf **Neues Projekt**.

Zum Vergleich: beim Erstellen eines neuen Projekts in Xcode wird eine Liste mit Projektvorlagen angezeigt, siehe folgende Abbildung.

![Xcode-Dialogfeld für neues Projekt](images/ios-to-uwp/ios-to-uwp-xcode-choose-template.png)

In Visual Studio können Sie ebenfalls aus einer Vielzahl von Projektvorlagen wählen, wie in der folgenden Abbildung dargestellt.

![Visual Studio-Dialogfeld für neues Projekt](images/ios-to-uwp/ios-to-uwp-vs-choose-template.png) Für diese exemplarische Vorgehensweise tippen Sie auf **Visual C#**, und tippen Sie dann auf **Windows**, **Windows Universal** und auf **Leere App (universelle Windows-App)**. Geben Sie „MyApp“ in das Feld **Name** ein, und tippen Sie dann auf **OK**. Daraufhin erstellt Visual Studio Ihr erstes Projekt und zeigt es an. Nun können Sie mit dem Entwerfen der App beginnen und Code hinzufügen.

## <a name="next-step"></a>Nächster Schritt

[Erste Schritte: Auswählen einer Programmiersprache](getting-started-choosing-a-programming-language.md)
