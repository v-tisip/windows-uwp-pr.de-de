---
author: mcleblanc
ms.assetid: 83b4be37-6613-4d00-a48a-0451a24a30fb
title: Datenbindung
description: "Die Datenbindung ist eine Methode, mit der die Benutzeroberfläche Ihrer App Daten anzeigen und diese Daten optional synchronisieren kann."
ms.author: markl
ms.date: 02/08/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: Windows 10, UWP
ms.openlocfilehash: 9af7c4a3bf5cfacf8fcdddc276c4cff127ae9ea8
ms.sourcegitcommit: 909d859a0f11981a8d1beac0da35f779786a6889
translationtype: HT
---
# <a name="data-binding"></a>Datenbindung

\[ Aktualisiert für UWP-Apps unter Windows10. Artikel zu Windows8.x finden Sie im [Archiv](http://go.microsoft.com/fwlink/p/?linkid=619132) \]

Die Datenbindung ist eine Methode, mit der die Benutzeroberfläche Ihrer App Daten anzeigen und diese Daten optional synchronisieren kann. Mit der Datenbindung können Sie Datenaspekte von Benutzeroberflächenaspekten trennen, was zu einem einfacheren konzeptionellen Modell und besserer Lesbarkeit, Testbarkeit und Wartung Ihrer App führt. Im Markup können Sie entweder die [{X:Bind}-Markuperweiterung](https://msdn.microsoft.com/library/windows/apps/Mt204783) oder die [{Binding}-Markuperweiterung](https://msdn.microsoft.com/library/windows/apps/Mt204782) verwenden. Sie können sogar eine Mischung aus den beiden in derselben App verwenden – sogar im gleichen Benutzeroberflächenelement. {x:Bind} ist neu in Windows10 und bietet eine bessere Leistung.

| Thema | Beschreibung |
|-------|-------------|
| [Übersicht über Datenbindung](data-binding-quickstart.md) | In diesem Thema erfahren Sie, wie Sie in einer UWP-App (Universelle Windows-Plattform) ein Steuerelement (oder ein anderes Benutzeroberflächenelement) an ein einzelnes Element oder ein Elementsteuerelement an eine Sammlung von Elementen binden. Darüber hinaus wird erläutert, wie Sie die Anzeige von Elementen steuern, eine Detailansicht auf Grundlage einer Auswahl implementieren und Daten für die Anzeige umwandeln. Ausführliche Informationen finden Sie unter [Datenbindung im Detail](data-binding-in-depth.md). | 
| [Datenbindung im Detail](data-binding-in-depth.md) | In diesem Thema werden die Datenbindungsfeatures ausführlich beschrieben. |
| [Beispieldaten für die Entwurfsoberfläche und Prototyperstellung](displaying-data-in-the-designer.md) | Es gibt mehrere Möglichkeiten, Entwurfszeit-Beispieldaten zu verwenden, damit Steuerelemente im Visual Studio-Designer mit Daten aufgefüllt werden (sodass Sie das Layout, die Vorlagen und andere visuelle Eigenschaften der App bearbeiten können). Beispieldaten können auch hilfreich sein und Zeit sparen, wenn Sie eine App als Skizze (oder Prototyp) erstellen. Sie können zur Laufzeit Beispieldaten in der Skizze oder im Prototyp verwenden, um Ihre Ideen zu veranschaulichen, ohne echte Livedaten nutzen zu müssen. |
| [Binden von hierarchischen Daten und Erstellen einer Master/Details-Ansicht](how-to-bind-to-hierarchical-data-and-create-a-master-details-view.md) | Sie können eine Master/Details-Ansicht mit mehreren Ebenen (auch bekannt als Listen-Details-Ansicht) von hierarchischen Daten erstellen, indem Sie Elementsteuerelemente an [<strong>CollectionViewSource</strong>](https://msdn.microsoft.com/library/windows/apps/BR209833)-Instanzen binden, die in einer Kette verbunden sind. |

