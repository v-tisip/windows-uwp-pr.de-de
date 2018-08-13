---
author: jwmsft
description: Stellt einen Wert für ein beliebiges XAML-Attribut bereit, indem ein Verweis auf eine Ressource aus einer benutzerdefinierten Ressourcennachschlage-Implementierung untersucht wird. Das Nachschlagen der Ressource erfolgt mithilfe einer Implementierung der CustomXamlResourceLoader-Klasse.
title: CustomResource-Markuperweiterung
ms.assetid: 3A59A8DE-E805-4F04-B9D9-A91E053F3642
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows10, UWP
ms.openlocfilehash: a14ae2e327805c5d123cc3b6232bfa18863f9da9
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
ms.translationtype: MT
ms.contentlocale: de-DE
ms.locfileid: "235053"
---
# <a name="customresource-markup-extension"></a>{CustomResource}-Markuperweiterung

\[ Aktualisiert für UWP-Apps unter Windows10. Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]

Stellt einen Wert für ein beliebiges XAML-Attribut bereit, indem ein Verweis auf eine Ressource aus einer benutzerdefinierten Ressourcennachschlage-Implementierung untersucht wird. Das Nachschlagen der Ressource erfolgt mithilfe einer Implementierung der [**CustomXamlResourceLoader**](https://msdn.microsoft.com/library/windows/apps/br243327)-Klasse.

## <a name="xaml-attribute-usage"></a>XAML-Attributverwendung

``` syntax
<object property="{CustomResource key}" .../>
```

## <a name="xaml-values"></a>XAML-Werte

| Benennung | Beschreibung |
|------|-------------|
| Schlüssel | Der Schlüssel für die angeforderte Ressource. Die ursprüngliche Zuweisung des Schlüssels ist abhängig von der Implementierung der [**CustomXamlResourceLoader**](https://msdn.microsoft.com/library/windows/apps/br243327)-Klasse, die aktuell zur Verwendung registriert wurde. |

## <a name="remarks"></a>Hinweise

**CustomResource** ist eine Methode zum Abrufen von Werten, die an anderer Stelle in einem benutzerdefinierten Ressourcenrepository definiert sind. Diese Technik ist relativ komplex und wird in den meisten Szenarien für Windows-Runtime-App-Szenarien nicht verwendet.

Die Auflösung einer **CustomResource** in ein Ressourcenwörterbuch wird in diesem Thema nicht beschrieben, da diese sehr unterschiedlich sein kann, abhängig von der Implementierung von [**CustomXamlResourceLoader**](https://msdn.microsoft.com/library/windows/apps/br243327).

Die [**GetResource**](https://msdn.microsoft.com/library/windows/apps/br243340)-Methode der Implementierung von [**CustomXamlResourceLoader**](https://msdn.microsoft.com/library/windows/apps/br243327) wird vom XAML-Parser der Windows-Runtime aufgerufen, wenn eine `{CustomResource}` im Markup gefunden wird. Die *resourceId*, die an **GetResource** übergeben wird, stammt aus dem *key*-Argument. Die anderen Eingabeparameter sind kontextabhängig und richten sich beispielsweise nach der Eigenschaft, auf die sich die Verwendung bezieht.

Eine `{CustomResource}`-Syntax funktioniert standardmäßig nicht (die Basisimplementierung von [**GetResource**](https://msdn.microsoft.com/library/windows/apps/br243340) ist unvollständig). Für einen gültigen `{CustomResource}`-Verweis müssen Sie die folgenden Schritte ausführen:

1.  Leiten Sie eine benutzerdefinierte Klasse von [**CustomXamlResourceLoader**](https://msdn.microsoft.com/library/windows/apps/br243327) ab, und überschreiben Sie die [**GetResource**](https://msdn.microsoft.com/library/windows/apps/br243340)-Methode. Rufen Sie in der Implementierung nicht die Methode der Basisklasse auf.
2.  Legen Sie [**CustomXamlResourceLoader.Current**](https://msdn.microsoft.com/library/windows/apps/br243328) fest, um auf Ihre Klasse in der Initialisierungslogik zu verweisen. Dies muss erfolgen, bevor XAML-Code auf Seitenebene geladen wird, der die `{CustomResource}`-Erweiterungssyntax enthält. Eine Stelle, an der **CustomXamlResourceLoader.Current** festgelegt werden kann, ist im [**Application**](https://msdn.microsoft.com/library/windows/apps/br242324)-Unterklassenkonstruktor, der in den App.xaml-CodeBehind-Vorlagen für Sie generiert wird.
3.  Jetzt können Sie `{CustomResource}`-Erweiterungen in dem XAML-Code, den Ihre App als Seiten lädt, oder in XAML-Ressourcenverzeichnissen verwenden.

**CustomResource** ist eine Markuperweiterung. Markuperweiterungen werden in der Regel implementiert, wenn für Attributwerte Escapezeichen verwendet werden müssen, damit sie keine Literalwerte oder Handlernamen darstellen, und es nicht ausreicht, Typkonverter für bestimmte Typen oder Eigenschaften zu verwenden. Alle Markuperweiterungen in XAML verwenden die Zeichen „\{” und „\}” in ihrer Attributsyntax. Anhand dieser Konvention erkennt ein XAML-Prozessor, dass eine Markuperweiterung das Attribut verarbeiten muss.

## <a name="related-topics"></a>Verwandte Themen

* [ResourceDictionary- und XAML-Ressourcenreferenzen](https://msdn.microsoft.com/library/windows/apps/mt187273)
* [**CustomXamlResourceLoader**](https://msdn.microsoft.com/library/windows/apps/br243327)
* [**GetResource**](https://msdn.microsoft.com/library/windows/apps/br243340)

