---
ms.assetid: 0C69521B-47E0-421F-857B-851B0E9605F2
title: Binden von hierarchischen Daten und Erstellen einer Master/Details-Ansicht
description: Sie können eine Master/Detailansicht mit mehreren Ebenen (auch bekannt als Listendetailansicht) hierarchischer Daten erstellen, indem Sie Elementsteuerelemente an CollectionViewSource-Instanzen binden, die in einer Kette verbunden sind.
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 194bbeefbd3ca5f8237bb3449ec935211056aea3
ms.sourcegitcommit: 49d58bc66c1c9f2a4f81473bcb25af79e2b1088d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "8923682"
---
# <a name="bind-hierarchical-data-and-create-a-masterdetails-view"></a><span data-ttu-id="dd02e-104">Binden von hierarchischen Daten und Erstellen einer Master/Details-Ansicht</span><span class="sxs-lookup"><span data-stu-id="dd02e-104">Bind hierarchical data and create a master/details view</span></span>



> <span data-ttu-id="dd02e-105">**Hinweis:** finden Sie auch das [Master/Detail-Beispiel](http://go.microsoft.com/fwlink/p/?linkid=619991).</span><span class="sxs-lookup"><span data-stu-id="dd02e-105">**Note**Also see the [Master/detail sample](http://go.microsoft.com/fwlink/p/?linkid=619991).</span></span>

<span data-ttu-id="dd02e-106">Sie können eine Master/Details-Ansicht mit mehreren Ebenen (auch bekannt als Listen-Details-Ansicht) von hierarchischen Daten erstellen, indem Sie Elementsteuerelemente an [**CollectionViewSource**](https://msdn.microsoft.com/library/windows/apps/BR209833)-Instanzen binden, die in einer Kette verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="dd02e-106">You can make a multi-level master/details (also known as list-details) view of hierarchical data by binding items controls to [**CollectionViewSource**](https://msdn.microsoft.com/library/windows/apps/BR209833) instances that are bound together in a chain.</span></span> <span data-ttu-id="dd02e-107">In diesem Thema verwenden wir nach Möglichkeit die [{x:Bind}-Markuperweiterung](https://msdn.microsoft.com/library/windows/apps/Mt204783) und die flexiblere (aber weniger leistungsfähige) [{Binding}-Markuperweiterung](https://msdn.microsoft.com/library/windows/apps/Mt204782), wenn nötig.</span><span class="sxs-lookup"><span data-stu-id="dd02e-107">In this topic we use the [{x:Bind} markup extension](https://msdn.microsoft.com/library/windows/apps/Mt204783) where possible, and the more flexible (but less performant) [{Binding} markup extension](https://msdn.microsoft.com/library/windows/apps/Mt204782) where necessary.</span></span>

<span data-ttu-id="dd02e-108">Eine häufig verwendete Struktur für UWP-Apps (Universelle Windows-Plattform) ist die Navigation zu unterschiedlichen Detailseiten, wenn der Benutzer in einer Masterliste eine Auswahl trifft.</span><span class="sxs-lookup"><span data-stu-id="dd02e-108">One common structure for Universal Windows Platform (UWP) apps is to navigate to different details pages when a user makes a selection in a master list.</span></span> <span data-ttu-id="dd02e-109">Dies ist hilfreich, wenn Sie eine anschauliche visuelle Darstellung jedes Elements auf allen Ebenen in einer Hierarchie erzielen möchten.</span><span class="sxs-lookup"><span data-stu-id="dd02e-109">This is useful when you want to provide a rich visual representation of each item at every level in a hierarchy.</span></span> <span data-ttu-id="dd02e-110">Eine weitere Möglichkeit ist die Anzeige von mehreren Datenebenen auf einer einzelnen Seite.</span><span class="sxs-lookup"><span data-stu-id="dd02e-110">Another option is to display multiple levels of data on a single page.</span></span> <span data-ttu-id="dd02e-111">Dies ist nützlich, wenn Sie einige einfache Listen anzeigen möchten, in denen der Benutzer schnell Detailinformationen für ein bestimmtes Element anzeigen kann.</span><span class="sxs-lookup"><span data-stu-id="dd02e-111">This is useful when you want to display a few simple lists that let the user quickly drill down to an item of interest.</span></span> <span data-ttu-id="dd02e-112">In diesem Thema wird die Implementierung dieser Interaktion beschrieben.</span><span class="sxs-lookup"><span data-stu-id="dd02e-112">This topic describes how to implement this interaction.</span></span> <span data-ttu-id="dd02e-113">Die [**CollectionViewSource**](https://msdn.microsoft.com/library/windows/apps/BR209833)-Instanzen verfolgen die aktuelle Auswahl auf jeder Hierarchieebene nach.</span><span class="sxs-lookup"><span data-stu-id="dd02e-113">The [**CollectionViewSource**](https://msdn.microsoft.com/library/windows/apps/BR209833) instances keep track of the current selection at each hierarchical level.</span></span>

<span data-ttu-id="dd02e-114">Wir erstellen eine Ansicht einer Sportmannschaftshierarchie, die in Listen für Ligen, Divisionen und Mannschaften unterteilt ist und eine Detailansicht für Mannschaften enthält.</span><span class="sxs-lookup"><span data-stu-id="dd02e-114">We'll create a view of a sports team hierarchy that is organized into lists for leagues, divisions, and teams, and includes a team details view.</span></span> <span data-ttu-id="dd02e-115">Wenn Sie ein Element in einer Liste auswählen, werden die nachfolgenden Ansichten automatisch aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="dd02e-115">When you select an item from any list, the subsequent views update automatically.</span></span>

![Master/Details-Ansicht einer Sporthierarchie](images/xaml-masterdetails.png)

## <a name="prerequisites"></a><span data-ttu-id="dd02e-117">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="dd02e-117">Prerequisites</span></span>

<span data-ttu-id="dd02e-118">In diesem Thema wird vorausgesetzt, dass Sie eine UWP-App erstellen können.</span><span class="sxs-lookup"><span data-stu-id="dd02e-118">This topic assumes that you know how to create a basic UWP app.</span></span> <span data-ttu-id="dd02e-119">Anweisungen zum Erstellen Ihrer ersten UWP-App finden Sie unter [Erstellen Ihrer ersten UWP-App mit C# oder Visual Basic](https://msdn.microsoft.com/library/windows/apps/Hh974581).</span><span class="sxs-lookup"><span data-stu-id="dd02e-119">For instructions on creating your first UWP app, see [Create your first UWP app using C# or Visual Basic](https://msdn.microsoft.com/library/windows/apps/Hh974581).</span></span>

## <a name="create-the-project"></a><span data-ttu-id="dd02e-120">Erstellen des Projekts</span><span class="sxs-lookup"><span data-stu-id="dd02e-120">Create the project</span></span>

<span data-ttu-id="dd02e-121">Erstellen Sie ein neues Projekt vom Typ **Leere Anwendung (Windows Universal)**.</span><span class="sxs-lookup"><span data-stu-id="dd02e-121">Create a new **Blank Application (Windows Universal)** project.</span></span> <span data-ttu-id="dd02e-122">Weisen Sie ihm den Namen „MasterDetailsBinding“ zu.</span><span class="sxs-lookup"><span data-stu-id="dd02e-122">Name it "MasterDetailsBinding".</span></span>

## <a name="create-the-data-model"></a><span data-ttu-id="dd02e-123">Erstellen des Datenmodells</span><span class="sxs-lookup"><span data-stu-id="dd02e-123">Create the data model</span></span>

<span data-ttu-id="dd02e-124">Fügen Sie Ihrem Projekt eine neue Klasse hinzu, nennen Sie sie „ViewModel.cs“, und fügen Sie ihr diesen Code hinzu.</span><span class="sxs-lookup"><span data-stu-id="dd02e-124">Add a new class to your project, name it ViewModel.cs, and add this code to it.</span></span> <span data-ttu-id="dd02e-125">Dies ist die Bindungsquellklasse.</span><span class="sxs-lookup"><span data-stu-id="dd02e-125">This will be your binding source class.</span></span>

```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace MasterDetailsBinding
{
    public class Team
    {
        public string Name { get; set; }
        public int Wins { get; set; }
        public int Losses { get; set; }
    }

    public class Division
    {
        public string Name { get; set; }
        public IEnumerable<Team> Teams { get; set; }
    }

    public class League
    {
        public string Name { get; set; }
        public IEnumerable<Division> Divisions { get; set; }
    }

    public class LeagueList : List<League>
    {
        public LeagueList()
        {
            this.AddRange(GetLeague().ToList());
        }

        public IEnumerable<League> GetLeague()
        {
            return from x in Enumerable.Range(1, 2)
                   select new League
                   {
                       Name = "League " + x,
                       Divisions = GetDivisions(x).ToList()
                   };
        }

        public IEnumerable<Division> GetDivisions(int x)
        {
            return from y in Enumerable.Range(1, 3)
                   select new Division
                   {
                       Name = String.Format("Division {0}-{1}", x, y),
                       Teams = GetTeams(x, y).ToList()
                   };
        }

        public IEnumerable<Team> GetTeams(int x, int y)
        {
            return from z in Enumerable.Range(1, 4)
                   select new Team
                   {
                       Name = String.Format("Team {0}-{1}-{2}", x, y, z),
                       Wins = 25 - (x * y * z),
                       Losses = x * y * z
                   };
        }
    }
}
```

## <a name="create-the-view"></a><span data-ttu-id="dd02e-126">Erstellen der Ansicht</span><span class="sxs-lookup"><span data-stu-id="dd02e-126">Create the view</span></span>

<span data-ttu-id="dd02e-127">Machen Sie als Nächstes die Bindungsquellklasse aus der Klasse verfügbar, die die Markupseite darstellt.</span><span class="sxs-lookup"><span data-stu-id="dd02e-127">Next, expose the binding source class from the class that represents your page of markup.</span></span> <span data-ttu-id="dd02e-128">Zu diesem Zweck fügen Sie eine Eigenschaft vom Typ **LeagueList** zu **MainPage** hinzu.</span><span class="sxs-lookup"><span data-stu-id="dd02e-128">We do that by adding a property of type **LeagueList** to **MainPage**.</span></span>

```cs
namespace MasterDetailsBinding
{
    /// <summary>
    /// An empty page that can be used on its own or navigated to within a Frame.
    /// </summary>
    public sealed partial class MainPage : Page
    {
        public MainPage()
        {
            this.InitializeComponent();
            this.ViewModel = new LeagueList();
        }
        public LeagueList ViewModel { get; set; }
    }
}
```

<span data-ttu-id="dd02e-129">Schließlich ersetzen Sie den Inhalt der Datei „MainPage.xaml“ durch das folgende Markup, mit dem drei [**CollectionViewSource**](https://msdn.microsoft.com/library/windows/apps/BR209833)-Instanzen deklariert und zu einer Kette verbunden werden.</span><span class="sxs-lookup"><span data-stu-id="dd02e-129">Finally, replace the contents of the MainPage.xaml file with the following markup, which declares three [**CollectionViewSource**](https://msdn.microsoft.com/library/windows/apps/BR209833) instances and binds them together in a chain.</span></span> <span data-ttu-id="dd02e-130">Die nachfolgenden Steuerelemente können dann abhängig von der Hierarchieebene an die entsprechende **CollectionViewSource**-Instanz gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="dd02e-130">The subsequent controls can then bind to the appropriate **CollectionViewSource**, depending on its level in the hierarchy.</span></span>

```xml
<Page
    x:Class="MasterDetailsBinding.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:MasterDetailsBinding"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d">

    <Page.Resources>
        <CollectionViewSource x:Name="Leagues"
            Source="{x:Bind ViewModel}"/>
        <CollectionViewSource x:Name="Divisions"
            Source="{Binding Divisions, Source={StaticResource Leagues}}"/>
        <CollectionViewSource x:Name="Teams"
            Source="{Binding Teams, Source={StaticResource Divisions}}"/>

        <Style TargetType="TextBlock">
            <Setter Property="FontSize" Value="15"/>
            <Setter Property="FontWeight" Value="Bold"/>
        </Style>

        <Style TargetType="ListBox">
            <Setter Property="FontSize" Value="15"/>
        </Style>

        <Style TargetType="ContentControl">
            <Setter Property="FontSize" Value="15"/>
        </Style>

    </Page.Resources>

    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">

        <StackPanel Orientation="Horizontal">

            <!-- All Leagues view -->

            <StackPanel Margin="5">
                <TextBlock Text="All Leagues"/>
                <ListBox ItemsSource="{Binding Source={StaticResource Leagues}}" 
                    DisplayMemberPath="Name"/>
            </StackPanel>

            <!-- League/Divisions view -->

            <StackPanel Margin="5">
                <TextBlock Text="{Binding Name, Source={StaticResource Leagues}}"/>
                <ListBox ItemsSource="{Binding Source={StaticResource Divisions}}" 
                    DisplayMemberPath="Name"/>
            </StackPanel>

            <!-- Division/Teams view -->

            <StackPanel Margin="5">
                <TextBlock Text="{Binding Name, Source={StaticResource Divisions}}"/>
                <ListBox ItemsSource="{Binding Source={StaticResource Teams}}" 
                    DisplayMemberPath="Name"/>
            </StackPanel>

            <!-- Team view -->

            <ContentControl Content="{Binding Source={StaticResource Teams}}">
                <ContentControl.ContentTemplate>
                    <DataTemplate>
                        <StackPanel Margin="5">
                            <TextBlock Text="{Binding Name}" 
                                FontSize="15" FontWeight="Bold"/>
                            <StackPanel Orientation="Horizontal" Margin="10,10">
                                <TextBlock Text="Wins:" Margin="0,0,5,0"/>
                                <TextBlock Text="{Binding Wins}"/>
                            </StackPanel>
                            <StackPanel Orientation="Horizontal" Margin="10,0">
                                <TextBlock Text="Losses:" Margin="0,0,5,0"/>
                                <TextBlock Text="{Binding Losses}"/>
                            </StackPanel>
                        </StackPanel>
                    </DataTemplate>
                </ContentControl.ContentTemplate>
            </ContentControl>

        </StackPanel>

    </Grid>
</Page>
```

<span data-ttu-id="dd02e-131">Beachten Sie, dass Sie durch die direkte Bindung an die [**CollectionViewSource**](https://msdn.microsoft.com/library/windows/apps/BR209833)-Instanz implizieren, dass Sie in Bindungen, in denen der Pfad in der Sammlung selbst nicht gefunden werden kann, an das aktuelle Element binden möchten.</span><span class="sxs-lookup"><span data-stu-id="dd02e-131">Note that by binding directly to the [**CollectionViewSource**](https://msdn.microsoft.com/library/windows/apps/BR209833), you're implying that you want to bind to the current item in bindings where the path cannot be found on the collection itself.</span></span> <span data-ttu-id="dd02e-132">Die **CurrentItem**-Eigenschaft muss nicht als Pfad für die Bindung angegeben werden, obwohl dies im Zweifelsfall möglich ist.</span><span class="sxs-lookup"><span data-stu-id="dd02e-132">There's no need to specify the **CurrentItem** property as the path for the binding, although you can do that if there's any ambiguity.</span></span> <span data-ttu-id="dd02e-133">Beispielsweise wird die [**Content**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.contentcontrol.content)-Eigenschaft der [**ContentControl**](https://msdn.microsoft.com/library/windows/apps/BR209365)-Klasse, welche die Teamansicht darstellt, an `Teams`**CollectionViewSource** gebunden.</span><span class="sxs-lookup"><span data-stu-id="dd02e-133">For example, the [**ContentControl**](https://msdn.microsoft.com/library/windows/apps/BR209365) representing the team view has its [**Content**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.contentcontrol.content) property bound to the `Teams`**CollectionViewSource**.</span></span> <span data-ttu-id="dd02e-134">Die Steuerelemente in der [**DataTemplate**](https://msdn.microsoft.com/library/windows/apps/BR242348) werden jedoch an Eigenschaften der `Team`-Klasse gebunden, da die **CollectionViewSource** bei Bedarf automatisch das aktuell aus der Teamliste ausgewählte Team liefert.</span><span class="sxs-lookup"><span data-stu-id="dd02e-134">However, the controls in the [**DataTemplate**](https://msdn.microsoft.com/library/windows/apps/BR242348) bind to properties of the `Team` class because the **CollectionViewSource** automatically supplies the currently selected team from the teams list when necessary.</span></span>

 

 

