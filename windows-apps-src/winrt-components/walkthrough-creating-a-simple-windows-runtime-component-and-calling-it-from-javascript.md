---
author: msatranjr
title: Erstellen einer einfachen Komponente für Windows-Runtime und Aufrufen der Komponente über JavaScript
description: In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie .NET Framework mit Visual Basic oder C# verwenden können, um eigene Windows-Runtime-Typen zu erstellen, die in einer Komponente für Windows-Runtime verpackt sind, und wie Sie die Komponente von Ihrer universellen Windows-App aus aufrufen, die mit JavaScript für Windows erstellt wurde.
ms.assetid: 1565D86C-BF89-4EF3-81FE-35367DB8D671
ms.author: misatran
ms.date: 02/08/2017
ms.topic: article
keywords: Windows 10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 49b9fe0833151155b11b7d7b796e395bb6a2ca7f
ms.sourcegitcommit: e38b334edb82bf2b1474ba686990f4299b8f59c7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/14/2018
ms.locfileid: "6835624"
---
# <a name="walkthrough-creating-a-simple-windows-runtime-component-and-calling-it-from-javascript"></a><span data-ttu-id="8d207-104">Exemplarische Vorgehensweise: Erstellen einer einfachen Komponente für Windows-Runtime und Aufrufen der Komponente über JavaScript</span><span class="sxs-lookup"><span data-stu-id="8d207-104">Walkthrough: Creating a Simple Windows Runtime component and calling it from JavaScript</span></span>




<span data-ttu-id="8d207-105">In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie .NET Framework mit Visual Basic oder C# verwenden, um eigene Windows-Runtime-Typen zu erstellen, die in einer Komponente für Windows-Runtime verpackt sind, und wie Sie die Komponente in Ihrer universellen Windows-App aufrufen, die mit JavaScript für Windows erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="8d207-105">This walkthrough shows how you can use the .NET Framework with Visual Basic or C# to create your own Windows Runtime types, packaged in a Windows Runtime component, and how to call the component from your Universal Windows app built for Windows using JavaScript.</span></span>

<span data-ttu-id="8d207-106">Visual Studio erleichtert das Hinzufügen einer Komponente für Windows-Runtime, die mit C# oder Visual Basic geschrieben wurde, zu Ihrer App, und das Erstellen von Windows-Runtime-Typen, die Sie von JavaScript aus aufrufen können.</span><span class="sxs-lookup"><span data-stu-id="8d207-106">Visual Studio makes it easy to add a Windows Runtime component written with C# or Visual Basic to your app, and to create Windows Runtime types that you can call from JavaScript.</span></span> <span data-ttu-id="8d207-107">Intern können Ihre Windows-Runtime-Typen jede .NET Framework-Funktion verwenden, die in einer universellen Windows-App zulässig ist.</span><span class="sxs-lookup"><span data-stu-id="8d207-107">Internally, your Windows Runtime types can use any .NET Framework functionality that's allowed in a Universal Windows app.</span></span> <span data-ttu-id="8d207-108">(Weitere Informationen finden Sie unter [Erstellen von Windows-Runtime-Komponenten in c# und Visual Basic](creating-windows-runtime-components-in-csharp-and-visual-basic.md) und [.NET für UWP-apps-Übersicht](https://msdn.microsoft.com/library/windows/apps/xaml/mt185501.aspx).) Extern können können die Member des Typs nur Windows-Runtime-Typen für ihre Parameter und Rückgabewerte verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="8d207-108">(For more information, see [Creating Windows Runtime Components in C# and Visual Basic](creating-windows-runtime-components-in-csharp-and-visual-basic.md) and [.NET for UWP apps overview](https://msdn.microsoft.com/library/windows/apps/xaml/mt185501.aspx).) Externally, the members of your type can expose only Windows Runtime types for their parameters and return values.</span></span> <span data-ttu-id="8d207-109">Wenn Sie Ihre Projektmappe erstellen, erstellt Visual Studio das .NET Framework-Komponentenprojekt für Windows-Runtime und führt dann einen Buildschritt aus, der eine Windows-Metadatendatei (WINMD) erstellt.</span><span class="sxs-lookup"><span data-stu-id="8d207-109">When you build your solution, Visual Studio builds your .NET Framework Windows Runtime Component project and then executes a build step that creates a Windows metadata (.winmd) file.</span></span> <span data-ttu-id="8d207-110">Hierbei handelt es sich um Ihre Komponente für Windows-Runtime, die Visual Studio in Ihre App einschließt.</span><span class="sxs-lookup"><span data-stu-id="8d207-110">This is your Windows Runtime component, which Visual Studio includes in your app.</span></span>

> <span data-ttu-id="8d207-111">**Hinweis:**.NET Framework ordnet automatisch einige häufig verwendeten .NET Framework-Typen, z. B. primitive Datentypen und collectiontypen, ihren Windows-Runtime-Entsprechungen.</span><span class="sxs-lookup"><span data-stu-id="8d207-111">**Note**The .NET Framework automatically maps some commonly used .NET Framework types, such as primitive data types and collection types, to their Windows Runtime equivalents.</span></span> <span data-ttu-id="8d207-112">Diese .NET Framework-Typen können in der öffentlichen Schnittstelle einer Komponente für Windows-Runtime verwendet werden und werden Benutzern der Komponente als die entsprechenden Windows-Runtime-Typen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8d207-112">These .NET Framework types can be used in the public interface of a Windows Runtime component, and will appear to users of the component as the corresponding Windows Runtime types.</span></span> <span data-ttu-id="8d207-113">Informationen finden Sie unter [Erstellen von Komponenten für Windows-Runtime in C# und Visual Basic](creating-windows-runtime-components-in-csharp-and-visual-basic.md).</span><span class="sxs-lookup"><span data-stu-id="8d207-113">See [Creating Windows Runtime Components in C# and Visual Basic](creating-windows-runtime-components-in-csharp-and-visual-basic.md).</span></span>

<span data-ttu-id="8d207-114">In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="8d207-114">This walkthrough illustrates the following tasks.</span></span> <span data-ttu-id="8d207-115">Nachdem Sie den ersten Abschnitt abgeschlossen haben, in dem die Windows-App mit JavaScript einrichtet wird, können Sie die restlichen Abschnitte in beliebiger Reihenfolge abschließen.</span><span class="sxs-lookup"><span data-stu-id="8d207-115">After you've completed the first section, which sets up the Windows app with JavaScript, you can complete the remaining sections in any order.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8d207-116">Voraussetzungen:</span><span class="sxs-lookup"><span data-stu-id="8d207-116">Prerequisites:</span></span>

-   <span data-ttu-id="8d207-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="8d207-117">Windows10</span></span>
-   <span data-ttu-id="8d207-118">Microsoft Visual Studio2015 oder Microsoft Visual Studio Community2015</span><span class="sxs-lookup"><span data-stu-id="8d207-118">Microsoft Visual Studio2015 or Microsoft Visual Studio Community2015</span></span>

## <a name="creating-a-simple-windows-runtime-class"></a><span data-ttu-id="8d207-119">Erstellen eine einfache Windows-Runtime-Klasse</span><span class="sxs-lookup"><span data-stu-id="8d207-119">Creating a simple Windows Runtime class</span></span>


<span data-ttu-id="8d207-120">In diesem Abschnitt wird eine universelle Windows-App für Windows mit JavaScript erstellt und ein Visual Basic- oder C#-Komponentenprojekt für Windows-Runtime hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="8d207-120">This section creates a Universal Windows app built for Windows using JavaScript, and adds a Visual Basic or C# Windows Runtime Component project.</span></span> <span data-ttu-id="8d207-121">Es wird gezeigt, wie ein verwalteter Windows-Runtime-Typ definiert, eine Instanz des Typs aus JavaScript erstellt und statische sowie Instanzmember aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="8d207-121">It shows how to define a managed Windows Runtime type, create an instance of the type from JavaScript, and call static and instance members.</span></span> <span data-ttu-id="8d207-122">Die visuelle Darstellung der Beispiel-App ist absichtlich einfach, um den Fokus auf der Komponente zu behalten.</span><span class="sxs-lookup"><span data-stu-id="8d207-122">The visual display of the example app is deliberately dull to keep the focus on the component.</span></span> <span data-ttu-id="8d207-123">Sie können die Darstellung gerne verschönern.</span><span class="sxs-lookup"><span data-stu-id="8d207-123">Feel free to make it prettier.</span></span>

1.  <span data-ttu-id="8d207-124">Erstellen Sie in Visual Studio ein neues JavaScript-Projekt: Wählen Sie auf der Menüleiste **Datei, Neu, Projekt** aus.</span><span class="sxs-lookup"><span data-stu-id="8d207-124">In Visual Studio, create a new JavaScript project: On the menu bar, choose **File, New, Project**.</span></span> <span data-ttu-id="8d207-125">Wählen Sie im Abschnitt **Installierte Vorlagen** des Dialogfelds **Neues Projekt** die Option **JavaScript** und dann **Windows** sowie **Universelle** aus.</span><span class="sxs-lookup"><span data-stu-id="8d207-125">In the **Installed Templates** section of the **New Project** dialog box, choose **JavaScript**, and then choose **Windows**, and then **Universal**.</span></span> <span data-ttu-id="8d207-126">(Falls Windows nicht verfügbar ist, stellen Sie sicher, dass Sie Windows 8 oder höher verwenden.) Wählen Sie die Vorlage **Leere Anwendung** aus, und geben Sie „SampleApp“ als Namen des Projekts ein.</span><span class="sxs-lookup"><span data-stu-id="8d207-126">(If Windows is not available, make sure you're using Windows 8 or later.) Choose the **Blank Application** template and enter SampleApp for the project name.</span></span>
2.  <span data-ttu-id="8d207-127">Erstellen Sie das Komponentenprojekt: Öffnen Sie im Projektmappen-Explorer das Kontextmenü für die Projektmappe „SampleApp“, und wählen Sie **Hinzufügen** und dann **Neues Projekt** aus, um ein neues C#- oder Visual Basic-Projekt der Projektmappe hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="8d207-127">Create the component project: In Solution Explorer, open the shortcut menu for the SampleApp solution and choose **Add**, and then choose **New Project** to add a new C# or Visual Basic project to the solution.</span></span> <span data-ttu-id="8d207-128">Wählen Sie im Abschnitt **Installierte Vorlagen** des Dialogfelds **Neues Projekt hinzufügen** die Option **Visual Basic** oder **Visual C#** und dann **Windows** und **Universelle** aus.</span><span class="sxs-lookup"><span data-stu-id="8d207-128">In the **Installed Templates** section of the **Add New Project** dialog box, choose **Visual Basic** or **Visual C#**, and then choose **Windows**, and then **Universal**.</span></span> <span data-ttu-id="8d207-129">Wählen Sie die Vorlage **Komponente für Windows-Runtime** aus, und geben Sie **SampleComponent** als Projektnamen ein.</span><span class="sxs-lookup"><span data-stu-id="8d207-129">Choose the **Windows Runtime Component** template and enter **SampleComponent** for the project name.</span></span>
3.  <span data-ttu-id="8d207-130">Ändern Sie den Namen der Klasse in **Example**.</span><span class="sxs-lookup"><span data-stu-id="8d207-130">Change the name of the class to **Example**.</span></span> <span data-ttu-id="8d207-131">Beachten Sie, dass die Klasse standardmäßig mit **public sealed** (**Public NotInheritable** in Visual Basic) gekennzeichnet ist.</span><span class="sxs-lookup"><span data-stu-id="8d207-131">Notice that by default, the class is marked **public sealed** (**Public NotInheritable** in Visual Basic).</span></span> <span data-ttu-id="8d207-132">Die Windows-Runtime-Klassen, die Sie von Ihrer Komponente aus bereitstellen, müssen versiegelt sein.</span><span class="sxs-lookup"><span data-stu-id="8d207-132">All the Windows Runtime classes you expose from your component must be sealed.</span></span>
4.  <span data-ttu-id="8d207-133">Fügen Sie der Klasse zwei einfache Member hinzu, eine **static**-Methode (**Shared**-Methode in Visual Basic) und eine Instanzeigenschaft:</span><span class="sxs-lookup"><span data-stu-id="8d207-133">Add two simple members to the class, a **static** method (**Shared** method in Visual Basic) and an instance property:</span></span>

    > [!div class="tabbedCodeSnippets"]
    > ```csharp
    > namespace SampleComponent
    > {
    >     public sealed class Example
    >     {
    >         public static string GetAnswer()
    >         {
    >             return "The answer is 42.";
    >         }
    >
    >         public int SampleProperty { get; set; }
    >     }
    > }
    > ```
    > ```vb
    > Public NotInheritable Class Example
    >     Public Shared Function GetAnswer() As String
    >         Return "The answer is 42."
    >     End Function
    >
    >     Public Property SampleProperty As Integer
    > End Class
    > ```

5.  <span data-ttu-id="8d207-134">Optional: Um IntelliSense für die neu hinzugefügte Member zu aktivieren, öffnen Sie im Projektmappen-Explorer das Kontextmenü für das Projekt „SampleComponent“, und wählen Sie dann **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="8d207-134">Optional: To enable IntelliSense for the newly added members, in Solution Explorer, open the shortcut menu for the SampleComponent project, and then choose **Build**.</span></span>
6.  <span data-ttu-id="8d207-135">Öffnen Sie im Projektmappen-Explorer im JavaScript-Projekt das Kontextmenü für **Verweise**, und wählen Sie dann **Verweis hinzufügen** aus, um den **Verweis-Manager** zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="8d207-135">In Solution Explorer, in the JavaScript project, open the shortcut menu for **References**, and then choose **Add Reference** to open the **Reference Manager**.</span></span> <span data-ttu-id="8d207-136">Wählen Sie **Projekte** und dann **Projektmappe** aus.</span><span class="sxs-lookup"><span data-stu-id="8d207-136">Choose **Projects**, and then choose **Solution**.</span></span> <span data-ttu-id="8d207-137">Aktivieren Sie das Kontrollkästchen für das Projekt „SampleComponent“, und wählen Sie **OK** aus, um einen Verweis hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="8d207-137">Select the check box for the SampleComponent project and choose **OK** to add a reference.</span></span>

## <a name="call-the-component-from-javascript"></a><span data-ttu-id="8d207-138">Aufrufen der Komponente über JavaScript</span><span class="sxs-lookup"><span data-stu-id="8d207-138">Call the component from JavaScript</span></span>


<span data-ttu-id="8d207-139">Um den Windows-Runtime-Typ aus JavaScript zu verwenden, fügen Sie den folgenden Code in der anonymen Funktion in der Datei „default.js“ (im Ordner „js“ des Projekts) hinzu, die von der Visual Studio-Vorlage bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="8d207-139">To use the Windows Runtime type from JavaScript, add the following code in the anonymous function in the default.js file (in the js folder of the project) that is provided by the Visual Studio template.</span></span> <span data-ttu-id="8d207-140">Sie sollten ihn nach dem Ereignishandler „app.oncheckpoint“ und vor dem Aufruf von „app.start“ einfügen.</span><span class="sxs-lookup"><span data-stu-id="8d207-140">It should go after the app.oncheckpoint event handler and before the call to app.start.</span></span>

```javascript
var ex;

function basics1() {
   document.getElementById('output').innerHTML =
        SampleComponent.Example.getAnswer();

    ex = new SampleComponent.Example();

   document.getElementById('output').innerHTML += "<br/>" +
       ex.sampleProperty;

}

function basics2() {
    ex.sampleProperty += 1;
    document.getElementById('output').innerHTML += "<br/>" +
        ex.sampleProperty;
}
```

<span data-ttu-id="8d207-141">Beachten Sie, dass der erste Buchstaben der einzelnen Membernamen von Großbuchstaben in Kleinbuchstaben geändert wird.</span><span class="sxs-lookup"><span data-stu-id="8d207-141">Notice that the first letter of each member name is changed from uppercase to lowercase.</span></span> <span data-ttu-id="8d207-142">Diese Transformation ist Teil der Unterstützung, die JavaScript bereitstellt, um die natürliche Verwendung von Windows-Runtime zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="8d207-142">This transformation is part of the support that JavaScript provides to enable the natural use of the Windows Runtime.</span></span> <span data-ttu-id="8d207-143">Für Namespaces und Klassennamen wird die Pascal-Schreibweise verwendet.</span><span class="sxs-lookup"><span data-stu-id="8d207-143">Namespaces and class names are Pascal-cased.</span></span> <span data-ttu-id="8d207-144">Für Membernamen wird mit Ausnahme von Ereignisnamen, die nur aus Kleinbuchstaben bestehen, die Camel-Schreibweise verwendet.</span><span class="sxs-lookup"><span data-stu-id="8d207-144">Member names are camel-cased except for event names, which are all lowercase.</span></span> <span data-ttu-id="8d207-145">Informationen finden Sie unter [Verwenden der Windows-Runtime in JavaScript](https://msdn.microsoft.com/library/hh710230.aspx).</span><span class="sxs-lookup"><span data-stu-id="8d207-145">See [Using the Windows Runtime in JavaScript](https://msdn.microsoft.com/library/hh710230.aspx).</span></span> <span data-ttu-id="8d207-146">Die Regeln für die Camel-Schreibweise können verwirrend sein.</span><span class="sxs-lookup"><span data-stu-id="8d207-146">The rules for camel casing can be confusing.</span></span> <span data-ttu-id="8d207-147">Normalerweise wird eine Reihe von anfänglichen Großbuchstaben als Kleinbuchstaben angezeigt, aber wenn ein Kleinbuchstabe drei Großbuchstaben folgt, werden nur die ersten beiden Buchstaben in Kleinbuchstaben angezeigt: Ein Element mit dem Namen „IDStringKind“ wird z. B. als „idStringKind“ angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8d207-147">A series of initial uppercase letters normally appears as lowercase, but if three uppercase letters are followed by a lowercase letter, only the first two letters appear in lowercase: for example, a member named IDStringKind appears as idStringKind.</span></span> <span data-ttu-id="8d207-148">In Visual Studio können Sie Ihr Komponentenprojekt für Windows-Runtime erstellen und dann IntelliSense in Ihrem JavaScript-Projekt verwenden, um die richtige Groß- und Kleinschreibung anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="8d207-148">In Visual Studio, you can build your Windows Runtime component project and then use IntelliSense in your JavaScript project to see the correct casing.</span></span>

<span data-ttu-id="8d207-149">In ähnlicher Weise unterstützt .NET Framework die natürliche Verwendung der Windows-Runtime in verwaltetem Code.</span><span class="sxs-lookup"><span data-stu-id="8d207-149">In similar fashion, the .NET Framework provides support to enable the natural use of the Windows Runtime in managed code.</span></span> <span data-ttu-id="8d207-150">Dies wird in den folgenden Abschnitten dieses Artikels und in den Artikeln [Erstellen von Windows-Runtime-Komponenten in c# und Visual Basic](creating-windows-runtime-components-in-csharp-and-visual-basic.md) und [.NET Framework-Unterstützung für UWP-apps und Windows-Runtime](https://msdn.microsoft.com/library/hh694558.aspx)erläutert.</span><span class="sxs-lookup"><span data-stu-id="8d207-150">This is discussed in subsequent sections of this article, and in the articles [Creating Windows Runtime Components in C# and Visual Basic](creating-windows-runtime-components-in-csharp-and-visual-basic.md) and [.NET Framework Support for UWP apps and Windows Runtime](https://msdn.microsoft.com/library/hh694558.aspx).</span></span>

## <a name="create-a-simple-user-interface"></a><span data-ttu-id="8d207-151">Erstellen einer einfachen Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="8d207-151">Create a simple user interface</span></span>


<span data-ttu-id="8d207-152">Öffnen Sie in Ihrem JavaScript-Projekt die Datei „default.HTML“, und aktualisieren Sie den Text wie im folgenden Code dargestellt.</span><span class="sxs-lookup"><span data-stu-id="8d207-152">In your JavaScript project, open the default.html file and update the body as shown in the following code.</span></span> <span data-ttu-id="8d207-153">Dieser Code enthält den vollständigen Satz von Steuerelementen für die Beispiel-App und gibt die Funktionsnamen für die Klickereignisse an.</span><span class="sxs-lookup"><span data-stu-id="8d207-153">This code includes the complete set of controls for the example app and specifies the function names for the click events.</span></span>

> <span data-ttu-id="8d207-154">**Hinweis:** Wenn Sie die app zum ersten Mal ausführen, werden nur die Schaltflächen "basics1" und "Basics2" unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8d207-154">**Note**When you first run the app, only the Basics1 and Basics2 button are supported.</span></span>

```html
<body>
            <div id="buttons">
            <button id="button1" >Basics 1</button>
            <button id="button2" >Basics 2</button>

            <button id="runtimeButton1">Runtime 1</button>
            <button id="runtimeButton2">Runtime 2</button>

            <button id="returnsButton1">Returns 1</button>
            <button id="returnsButton2">Returns 2</button>

            <button id="events1Button">Events 1</button>

            <button id="btnAsync">Async</button>
            <button id="btnCancel" disabled="disabled">Cancel Async</button>
            <progress id="primeProg" value="25" max="100" style="color: yellow;"></progress>
        </div>
        <div id="output">
        </div>
</body>
```

<span data-ttu-id="8d207-155">Öffnen Sie in Ihrem JavaScript-Projekt im Ordner „css“ die Datei „default.css“.</span><span class="sxs-lookup"><span data-stu-id="8d207-155">In your JavaScript project, in the css folder, open default.css.</span></span> <span data-ttu-id="8d207-156">Ändern Sie den Textabschnitt wie dargestellt, und fügen Sie Formate hinzu, um das Layout von Schaltflächen und die Anordnung des Ausgabetexts zu steuern.</span><span class="sxs-lookup"><span data-stu-id="8d207-156">Modify the body section as shown, and add styles to control the layout of buttons and the placement of output text.</span></span>

```css
body
{
    -ms-grid-columns: 1fr;
    -ms-grid-rows: 1fr 14fr;
    display: -ms-grid;
}

#buttons {
    -ms-grid-rows: 1fr;
    -ms-grid-columns: auto;
    -ms-grid-row-align: start;
}
#output {
    -ms-grid-row: 2;
    -ms-grid-column: 1;
}
```

<span data-ttu-id="8d207-157">Fügen Sie jetzt Ereignislistener-Registrierungscode hinzu, indem Sie dem processAll-Aufruf in „app.onactivated“ in „default.js“ eine THEN-Klausel hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8d207-157">Now add the event listener registration code by adding a then clause to the processAll call in app.onactivated in default.js.</span></span> <span data-ttu-id="8d207-158">Ersetzen Sie die vorhandene Codezeile, die „setPromise“ aufruft, durch folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="8d207-158">Replace the existing line of code that calls setPromise and change it to the following code:</span></span>

```javascript
args.setPromise(WinJS.UI.processAll().then(function () {
    var button1 = document.getElementById("button1");
    button1.addEventListener("click", basics1, false);
    var button2 = document.getElementById("button2");
    button2.addEventListener("click", basics2, false);
}));
```

<span data-ttu-id="8d207-159">Dies ist eine bessere Möglichkeit, Ereignisse zu HTML-Steuerelementen hinzuzufügen, als das Hinzufügen eines Klickereignishandlers direkt im HTML-Code.</span><span class="sxs-lookup"><span data-stu-id="8d207-159">This is a better way to add events to HTML controls than adding a click event handler directly in HTML.</span></span> <span data-ttu-id="8d207-160">Informationen finden Sie unter [Erstellen der App „Hello, world“ (JS)](https://msdn.microsoft.com/library/windows/apps/mt280216).</span><span class="sxs-lookup"><span data-stu-id="8d207-160">See [Create a "Hello World" app (JS)](https://msdn.microsoft.com/library/windows/apps/mt280216).</span></span>

## <a name="build-and-run-the-app"></a><span data-ttu-id="8d207-161">Erstellen und Ausführen der App</span><span class="sxs-lookup"><span data-stu-id="8d207-161">Build and run the app</span></span>


<span data-ttu-id="8d207-162">Ändern Sie vor dem Erstellen die Zielplattform für alle Projekte auf ARM, x64 oder x86 – je nachdem, was für Ihren Computer erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="8d207-162">Before you build, change the target platform for all projects to ARM, x64, or x86, as appropriate for your computer.</span></span>

<span data-ttu-id="8d207-163">Drücken Sie zum Erstellen und Ausführen der Projektmappe die F5-TASTE.</span><span class="sxs-lookup"><span data-stu-id="8d207-163">To build and run the solution, choose the F5 key.</span></span> <span data-ttu-id="8d207-164">(Falls ein Laufzeitfehler angezeigt wird, der besagt, dass „SampleComponent“ nicht definiert ist, fehlt der Verweis auf das Klassenbibliotheksprojekt.)</span><span class="sxs-lookup"><span data-stu-id="8d207-164">(If you get a run-time error message stating that SampleComponent is undefined, the reference to the class library project is missing.)</span></span>

<span data-ttu-id="8d207-165">Visual Studio kompiliert zunächst die Klassenbibliothek und führt dann eine MSBuild-Aufgabe aus, die [Winmdexp.exe (Windows-Runtime-Metadatenexporttool)](https://msdn.microsoft.com/library/hh925576.aspx) ausführt, um Ihre Komponente für Windows-Runtime zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="8d207-165">Visual Studio first compiles the class library, and then executes an MSBuild task that runs [Winmdexp.exe (Windows Runtime Metadata Export Tool)](https://msdn.microsoft.com/library/hh925576.aspx) to create your Windows Runtime component.</span></span> <span data-ttu-id="8d207-166">Die Komponente wird in eine WINMD-Datei eingeschlossen, die den verwalteten Code und die Windows-Metadaten enthält, die den Code beschreiben.</span><span class="sxs-lookup"><span data-stu-id="8d207-166">The component is included in a .winmd file that contains both the managed code and the Windows metadata that describes the code.</span></span> <span data-ttu-id="8d207-167">„WinMdExp.exe“ generiert Build-Fehlermeldungen, wenn Sie Code schreiben, der in einer Komponente für Windows-Runtime ungültig ist, und die Fehlermeldungen werden in der Visual Studio-IDE angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8d207-167">WinMdExp.exe generates build error messages when you write code that's invalid in a Windows Runtime component, and the error messages are displayed in the Visual Studio IDE.</span></span> <span data-ttu-id="8d207-168">Visual Studio fügt die Komponente zum App-Paket (APPX-Datei) für Ihre universelle Windows-App hinzu und generiert das entsprechende Manifest.</span><span class="sxs-lookup"><span data-stu-id="8d207-168">Visual Studio adds your component to the app package (.appx file) for your Universal Windows app, and generates the appropriate manifest.</span></span>

<span data-ttu-id="8d207-169">Wählen Sie die Schaltfläche „Basics1“ aus, um dem Ausgabebereich den Rückgabewert aus der statischen GetAnswer-Methode zuzuweisen, eine Instanz der Example-Klasse zu erstellen und den Wert der SampleProperty-Eigenschaft im Ausgabebereich anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="8d207-169">Choose the Basics 1 button to assign the return value from the static GetAnswer method to the output area, create an instance of the Example class, and display the value of its SampleProperty property in the output area.</span></span> <span data-ttu-id="8d207-170">Die Ausgabe ist hier dargestellt:</span><span class="sxs-lookup"><span data-stu-id="8d207-170">The output is shown here:</span></span>

``` syntax
"The answer is 42."
0
```

<span data-ttu-id="8d207-171">Wählen Sie Schaltfläche „Basics2“ aus, um den Wert der SampleProperty-Eigenschaft zu erhöhen und den neuen Wert im Ausgabebereich anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="8d207-171">Choose the Basics 2 button to increment the value of the SampleProperty property and to display the new value in the output area.</span></span> <span data-ttu-id="8d207-172">Primitive Typen wie Zeichenfolgen und Zahlen können als Parameter- und Rückgabetypen verwendet werden und zwischen verwaltetem Code und JavaScript übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="8d207-172">Primitive types such as strings and numbers can be used as parameter types and return types, and can be passed between managed code and JavaScript.</span></span> <span data-ttu-id="8d207-173">Da Zahlen in JavaScript im Gleitkommaformat mit doppelter Genauigkeit gespeichert werden, werden sie in numerische .NET Framework-Typen konvertiert.</span><span class="sxs-lookup"><span data-stu-id="8d207-173">Because numbers in JavaScript are stored in double-precision floating-point format, they are converted to .NET Framework numeric types.</span></span>

> <span data-ttu-id="8d207-174">**Hinweis:** standardmäßig können Sie Haltepunkte nur im JavaScript-Code festlegen.</span><span class="sxs-lookup"><span data-stu-id="8d207-174">**Note**By default, you can set breakpoints only in your JavaScript code.</span></span> <span data-ttu-id="8d207-175">Informationen zum Debuggen des Visual Basic- oder C#-Codes finden Sie unter „Erstellen von Komponenten für Windows-Runtime in C# und Visual Basic“.</span><span class="sxs-lookup"><span data-stu-id="8d207-175">To debug your Visual Basic or C# code, see Creating Windows Runtime Components in C# and Visual Basic.</span></span>

 

<span data-ttu-id="8d207-176">Wechseln Sie von der App zu Visual Studio, und drücken Sie Umschalt+F5, um den Debugmodus zu beenden und die App zu schließen.</span><span class="sxs-lookup"><span data-stu-id="8d207-176">To stop debugging and close your app, switch from the app to Visual Studio, and choose Shift+F5.</span></span>

## <a name="using-the-windows-runtime-from-javascript-and-managed-code"></a><span data-ttu-id="8d207-177">Verwenden von Windows-Runtime aus JavaScript und verwaltetem Code</span><span class="sxs-lookup"><span data-stu-id="8d207-177">Using the Windows Runtime from JavaScript and managed code</span></span>


<span data-ttu-id="8d207-178">Windows-Runtime kann aus JavaScript oder verwaltetem Code aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="8d207-178">The Windows Runtime can be called from either JavaScript or managed code.</span></span> <span data-ttu-id="8d207-179">Windows-Runtime-Objekte können zwischen den beiden übergeben werden, und Ergebnisse können auf beiden Seiten behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="8d207-179">Windows Runtime objects can be passed back and forth between the two, and events can be handled from either side.</span></span> <span data-ttu-id="8d207-180">Allerdings unterscheiden sich die Verwendungsmöglichkeiten der Windows-Runtime-Typen in den beiden Umgebungen in einigen Details, da JavaScript und .NET Framework Windows-Runtime unterschiedlich unterstützen.</span><span class="sxs-lookup"><span data-stu-id="8d207-180">However, the ways you use Windows Runtime types in the two environments differ in some details, because JavaScript and the .NET Framework support the Windows Runtime differently.</span></span> <span data-ttu-id="8d207-181">Das folgende Beispiel veranschaulicht diese Unterschiede mithilfe der [Windows.Foundation.Collections.PropertySet](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.propertyset.aspx)-Klasse.</span><span class="sxs-lookup"><span data-stu-id="8d207-181">The following example demonstrates these differences, using the [Windows.Foundation.Collections.PropertySet](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.propertyset.aspx) class.</span></span> <span data-ttu-id="8d207-182">In diesem Beispiel erstellen Sie eine Instanz der PropertySet-Sammlung in verwaltetem Code und registrieren einen Ereignishandler zum Nachverfolgen der Änderungen in der Sammlung.</span><span class="sxs-lookup"><span data-stu-id="8d207-182">In this example, you create an instance of the PropertySet collection in managed code and register an event handler to track changes in the collection.</span></span> <span data-ttu-id="8d207-183">Dann fügen Sie JavaScript-Code hinzu, der die Auflistung abruft, einen eigenen Ereignishandler registriert und die Auflistung verwendet.</span><span class="sxs-lookup"><span data-stu-id="8d207-183">Then you add JavaScript code that gets the collection, registers its own event handler, and uses the collection.</span></span> <span data-ttu-id="8d207-184">Zuletzt fügen Sie eine Methode hinzu, die Änderungen an der Sammlung von verwaltetem Code aus vornimmt und das Behandeln einer verwalteten Ausnahme durch JavaScript zeigt.</span><span class="sxs-lookup"><span data-stu-id="8d207-184">Finally, you add a method that makes changes to the collection from managed code and shows JavaScript handling a managed exception.</span></span>

> <span data-ttu-id="8d207-185">**Wichtige**In diesem Beispiel wird das Ereignis im UI-Thread ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="8d207-185">**Important**In this example, the event is being fired on the UI thread.</span></span> <span data-ttu-id="8d207-186">Wenn Sie das Ereignis über einen Hintergrundthread auslösen, z. B. in einem asynchronen Aufruf, müssen Sie einige zusätzliche Arbeiten ausführen, damit JavaScript das Ereignis behandelt.</span><span class="sxs-lookup"><span data-stu-id="8d207-186">If you fire the event from a background thread, for example in an async call, you will need to do some extra work in order for JavaScript to handle the event.</span></span> <span data-ttu-id="8d207-187">Weitere Informationen finden Sie unter [Auslösen von Ereignissen in Komponenten für Windows-Runtime](raising-events-in-windows-runtime-components.md).</span><span class="sxs-lookup"><span data-stu-id="8d207-187">For more information, see [Raising Events in Windows Runtime Components](raising-events-in-windows-runtime-components.md).</span></span>

 

<span data-ttu-id="8d207-188">Fügen Sie im SampleComponent-Projekt eine neue **public sealed**-Klasse (**Public NotInheritable**-Klasse in Visual Basic) mit dem Namen „PropertySetStats“ hinzu.</span><span class="sxs-lookup"><span data-stu-id="8d207-188">In the SampleComponent project, add a new **public sealed** class (**Public NotInheritable** class in Visual Basic) named PropertySetStats.</span></span> <span data-ttu-id="8d207-189">Die Klasse umschließt eine PropertySet-Auflistung und behandelt das MapChanged-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="8d207-189">The class wraps a PropertySet collection and handles its MapChanged event.</span></span> <span data-ttu-id="8d207-190">Der Ereignishandler verfolgt die Anzahl der aufgetretenen Änderungen jeder Art, und die DisplayStats-Methode erstellt einen Bericht, der in HTML formatiert ist.</span><span class="sxs-lookup"><span data-stu-id="8d207-190">The event handler tracks the number of changes of each kind that occur, and the DisplayStats method produces a report that is formatted in HTML.</span></span> <span data-ttu-id="8d207-191">Beachten Sie die zusätzliche **using**-Anweisung (**Imports**-Anweisung in Visual Basic). Achten Sie darauf, diese Anweisung den vorhandenen **using**-Anweisungen hinzuzufügen, anstatt sie zu überschreiben.</span><span class="sxs-lookup"><span data-stu-id="8d207-191">Notice the additional **using** statement (**Imports** statement in Visual Basic); be careful to add this to the existing **using** statements rather than overwriting them.</span></span>

> [!div class="tabbedCodeSnippets"]
> ```csharp
> using Windows.Foundation.Collections;
>
> namespace SampleComponent
> {
>     public sealed class PropertySetStats
>     {
>         private PropertySet _ps;
>         public PropertySetStats()
>         {
>             _ps = new PropertySet();
>             _ps.MapChanged += this.MapChangedHandler;
>         }
>
>         public PropertySet PropertySet { get { return _ps; } }
>
>         int[] counts = { 0, 0, 0, 0 };
>         private void MapChangedHandler(IObservableMap<string, object> sender,
>             IMapChangedEventArgs<string> args)
>         {
>             counts[(int)args.CollectionChange] += 1;
>         }
>
>         public string DisplayStats()
>         {
>             StringBuilder report = new StringBuilder("<br/>Number of changes:<ul>");
>             for (int i = 0; i < counts.Length; i++)
>             {
>                 report.Append("<li>" + (CollectionChange)i + ": " + counts[i] + "</li>");
>             }
>             return report.ToString() + "</ul>";
>         }
>     }
> }
> ```
> ```vb
> Imports System.Text
>
> Public NotInheritable Class PropertySetStats
>     Private _ps As PropertySet
>     Public Sub New()
>         _ps = New PropertySet()
>         AddHandler _ps.MapChanged, AddressOf Me.MapChangedHandler
>     End Sub
>
>     Public ReadOnly Property PropertySet As PropertySet
>         Get
>             Return _ps
>         End Get
>     End Property
>
>     Dim counts() As Integer = {0, 0, 0, 0}
>     Private Sub MapChangedHandler(ByVal sender As IObservableMap(Of String, Object),
>         ByVal args As IMapChangedEventArgs(Of String))
>
>         counts(CInt(args.CollectionChange)) += 1
>     End Sub
>
>     Public Function DisplayStats() As String
>         Dim report As New StringBuilder("<br/>Number of changes:<ul>")
>         For i As Integer = 0 To counts.Length - 1
>             report.Append("<li>" & CType(i, CollectionChange).ToString() &
>                           ": " & counts(i) & "</li>")
>         Next
>         Return report.ToString() & "</ul>"
>     End Function
> End Class
> ```

<span data-ttu-id="8d207-192">Der Ereignishandler folgt das vertraute .NET Framework-Ereignismuster, mit der Ausnahme, dass der Absender des Ereignisses (in diesem Fall das PropertySet-Objekt) in das IObservableMap umgewandelt wird&lt;Zeichenfolge, Objekt&gt; Schnittstelle (IObservableMap (Of String, Object) in Visual Basic), wird eine Instanziierung der Windows-Runtime-Schnittstelle [IObservableMap&lt;K, V&gt;](https://msdn.microsoft.com/library/windows/apps/br226050.aspx).</span><span class="sxs-lookup"><span data-stu-id="8d207-192">The event handler follows the familiar .NET Framework event pattern, except that the sender of the event (in this case, the PropertySet object) is cast to the IObservableMap&lt;string, object&gt; interface (IObservableMap(Of String, Object) in Visual Basic), which is an instantiation of the Windows Runtime interface [IObservableMap&lt;K, V&gt;](https://msdn.microsoft.com/library/windows/apps/br226050.aspx).</span></span> <span data-ttu-id="8d207-193">(Sie können den Absender zu deren Typ ggf. umwandeln.) Darüber hinaus werden die Ereignisargumente als Schnittstelle und nicht als Objekt dargestellt.</span><span class="sxs-lookup"><span data-stu-id="8d207-193">(You can cast the sender to its type if necessary.) Also, the event arguments are presented as an interface rather than as an object.</span></span>

<span data-ttu-id="8d207-194">Fügen Sie in der Datei „default.js“ die Runtime1-Funktion wie gezeigt hinzu:</span><span class="sxs-lookup"><span data-stu-id="8d207-194">In the default.js file, add the Runtime1 function as shown.</span></span> <span data-ttu-id="8d207-195">Dieser Code erstellt ein PropertySetStats-Objekt, ruft die PropertySet-Auflistung ab und fügt einen eigenen Ereignishandler, die OnMapChanged-Funktion, für die Behandlung des MapChanged-Ereignisses hinzu.</span><span class="sxs-lookup"><span data-stu-id="8d207-195">This code creates a PropertySetStats object, gets its PropertySet collection, and adds its own event handler, the onMapChanged function, to handle the MapChanged event.</span></span> <span data-ttu-id="8d207-196">Nach dem Ändern der Auflistung ruft „runtime1“ die DisplayStats-Methode auf, um eine Zusammenfassung der Änderungstypen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="8d207-196">After making changes to the collection, runtime1 calls the DisplayStats method to show a summary of change types.</span></span>

```javascript
var propertysetstats;

function runtime1() {
    document.getElementById('output').innerHTML = "";

    propertysetstats = new SampleComponent.PropertySetStats();
    var propertyset = propertysetstats.propertySet;

    propertyset.addEventListener("mapchanged", onMapChanged);

    propertyset.insert("FirstProperty", "First property value");
    propertyset.insert("SuperfluousProperty", "Unnecessary property value");
    propertyset.insert("AnotherProperty", "A property value");

    propertyset.insert("SuperfluousProperty", "Altered property value")
    propertyset.remove("SuperfluousProperty");

    document.getElementById('output').innerHTML +=
        propertysetstats.displayStats();
}

function onMapChanged(change) {
    var result
    switch (change.collectionChange) {
        case Windows.Foundation.Collections.CollectionChange.reset:
            result = "All properties cleared";
            break;
        case Windows.Foundation.Collections.CollectionChange.itemInserted:
            result = "Inserted " + change.key + ": '" +
                change.target.lookup(change.key) + "'";
            break;
        case Windows.Foundation.Collections.CollectionChange.itemRemoved:
            result = "Removed " + change.key;
            break;
        case Windows.Foundation.Collections.CollectionChange.itemChanged:
            result = "Changed " + change.key + " to '" +
                change.target.lookup(change.key) + "'";
            break;
        default:
            break;
     }

     document.getElementById('output').innerHTML +=
         "<br/>" + result;
}
```

<span data-ttu-id="8d207-197">Die Art und Weise der Behandlung von Windows-Runtime-Ereignissen in JavaScript unterscheidet sich von der Art und Weise der Behandlung im .NET Framework-Code.</span><span class="sxs-lookup"><span data-stu-id="8d207-197">The way you handle Windows Runtime events in JavaScript is very different from the way you handle them in .NET Framework code.</span></span> <span data-ttu-id="8d207-198">Der JavaScript-Ereignishandler verwendet nur ein Argument.</span><span class="sxs-lookup"><span data-stu-id="8d207-198">The JavaScript event handler takes only one argument.</span></span> <span data-ttu-id="8d207-199">Wenn Sie dieses Objekt im Visual Studio-Debugger anzeigen, ist die erste Eigenschaft der Absender.</span><span class="sxs-lookup"><span data-stu-id="8d207-199">When you view this object in the Visual Studio debugger, the first property is the sender.</span></span> <span data-ttu-id="8d207-200">Die Member der Ereignisargumentschnittstelle werden ebenfalls direkt auf diesem Objekt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8d207-200">The members of the event argument interface also appear directly on this object.</span></span>

<span data-ttu-id="8d207-201">Drücken Sie zum Ausführen der App die F5-TASTE.</span><span class="sxs-lookup"><span data-stu-id="8d207-201">To run the app, choose the F5 key.</span></span> <span data-ttu-id="8d207-202">Wenn die Klasse nicht versiegelt ist, erhalten Sie die Fehlermeldung wie „Das Exportieren des nicht versiegelten Typs 'SampleComponent.Example' wird derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8d207-202">If the class is not sealed, you get the error message, "Exporting unsealed type 'SampleComponent.Example' is not currently supported.</span></span> <span data-ttu-id="8d207-203">Markieren Sie ihn als versiegelt.“</span><span class="sxs-lookup"><span data-stu-id="8d207-203">Please mark it as sealed."</span></span>

<span data-ttu-id="8d207-204">Wählen Sie die Schaltfläche **Runtime1** aus.</span><span class="sxs-lookup"><span data-stu-id="8d207-204">Choose the **Runtime 1** button.</span></span> <span data-ttu-id="8d207-205">Der Ereignishandler zeigt Änderungen an, wenn Elemente hinzugefügt oder geändert werden, und am Ende wird die DisplayStats-Methode aufgerufen, um eine Zusammenfassung der Anzahl zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="8d207-205">The event handler displays changes as elements are added or changed, and at the end the DisplayStats method is called to produce a summary of counts.</span></span> <span data-ttu-id="8d207-206">Wechseln Sie zu Visual Studio zurück, und drücken Sie Umschalt+F5, um den Debugmodus zu beenden und die App zu schließen.</span><span class="sxs-lookup"><span data-stu-id="8d207-206">To stop debugging and close the app, switch back to Visual Studio and choose Shift+F5.</span></span>

<span data-ttu-id="8d207-207">Um der „PropertySet“-Sammlung zwei weitere Elemente aus dem verwalteten Code hinzuzufügen, fügen Sie den folgenden Code der „PropertySetStats“-Klasse hinzu:</span><span class="sxs-lookup"><span data-stu-id="8d207-207">To add two more items to the PropertySet collection from managed code, add the following code to the PropertySetStats class:</span></span>

> [!div class="tabbedCodeSnippets"]
> ```csharp
> public void AddMore()
> {
>     _ps.Add("NewProperty", "New property value");
>     _ps.Add("AnotherProperty", "A property value");
> }
> ```
> ```vb
> Public Sub AddMore()
>     _ps.Add("NewProperty", "New property value")
>     _ps.Add("AnotherProperty", "A property value")
> End Sub
> ```

<span data-ttu-id="8d207-208">In diesem Code wird ein weiterer Unterschied bei der Verwendung von Windows-Runtime Typen in zwei Umgebungen deutlich.</span><span class="sxs-lookup"><span data-stu-id="8d207-208">This code highlights another difference in the way you use Windows Runtime types in the two environments.</span></span> <span data-ttu-id="8d207-209">Wenn Sie diesen Code selbst eingeben, werden Sie feststellen, dass IntelliSense die Insert-Methode, die Sie im JavaScript-Code verwendet haben, nicht anzeigt.</span><span class="sxs-lookup"><span data-stu-id="8d207-209">If you type this code yourself, you'll notice that IntelliSense doesn't show the insert method you used in the JavaScript code.</span></span> <span data-ttu-id="8d207-210">Stattdessen wird die Add-Methode angezeigt, die häufig bei Auflistungen in .NET Framework zu sehen ist.</span><span class="sxs-lookup"><span data-stu-id="8d207-210">Instead, it shows the Add method commonly seen on collections in the .NET Framework.</span></span> <span data-ttu-id="8d207-211">Das liegt daran, dass einige häufig verwendete Sammlungsschnittstellen unterschiedliche Namen aber ähnliche Funktionalität in Windows-Runtime und .NET Framework haben.</span><span class="sxs-lookup"><span data-stu-id="8d207-211">This is because some commonly used collection interfaces have different names but similar functionality in the Windows Runtime and the .NET Framework.</span></span> <span data-ttu-id="8d207-212">Wenn Sie diese Schnittstellen in verwaltetem Code verwenden, werden sie als die jeweiligen .NET Framework-Entsprechung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8d207-212">When you use these interfaces in managed code, they appear as their .NET Framework equivalents.</span></span> <span data-ttu-id="8d207-213">Informationen dazu finden Sie unter [Erstellen von Komponenten für Windows-Runtime in C# und VisualBasic](creating-windows-runtime-components-in-csharp-and-visual-basic.md).</span><span class="sxs-lookup"><span data-stu-id="8d207-213">This is discussed in [Creating Windows Runtime Components in C# and Visual Basic](creating-windows-runtime-components-in-csharp-and-visual-basic.md).</span></span> <span data-ttu-id="8d207-214">Wenn Sie die gleichen Schnittstellen in JavaScript verwenden, besteht der einzige Unterschied zu Windows-Runtime darin, dass Großbuchstaben am Anfang der Membernamen zu Kleinbuchstaben werden.</span><span class="sxs-lookup"><span data-stu-id="8d207-214">When you use the same interfaces in JavaScript, the only change from the Windows Runtime is that uppercase letters at the beginning of member names become lowercase.</span></span>

<span data-ttu-id="8d207-215">Fügen Sie zum Schluss zum Aufrufen der AddMore-Methode mit der Ausnahmebehandlung die Runtime2-Funktion zu „default.js“ hinzu.</span><span class="sxs-lookup"><span data-stu-id="8d207-215">Finally, to call the AddMore method with exception handling, add the runtime2 function to default.js.</span></span>

```javascript
function runtime2() {
   try {
      propertysetstats.addMore();
    }
   catch(ex) {
       document.getElementById('output').innerHTML +=
          "<br/><b>" + ex + "<br/>";
   }

   document.getElementById('output').innerHTML +=
       propertysetstats.displayStats();
}
```

<span data-ttu-id="8d207-216">Fügen Sie den Ereignishandlercode für die Registrierung auf die gleiche Weise wie zuvor hinzu.</span><span class="sxs-lookup"><span data-stu-id="8d207-216">Add the event handler registration code the same way you did previously.</span></span>

```javascript
var runtimeButton1 = document.getElementById("runtimeButton1");
runtimeButton1.addEventListener("click", runtime1, false);
var runtimeButton2 = document.getElementById("runtimeButton2");
runtimeButton2.addEventListener("click", runtime2, false);
```

<span data-ttu-id="8d207-217">Drücken Sie zum Ausführen der App die F5-TASTE.</span><span class="sxs-lookup"><span data-stu-id="8d207-217">To run the app, choose the F5 key.</span></span> <span data-ttu-id="8d207-218">Wählen Sie **Runtime1** und dann **Runtime2** aus.</span><span class="sxs-lookup"><span data-stu-id="8d207-218">Choose **Runtime 1** and then **Runtime 2**.</span></span> <span data-ttu-id="8d207-219">Der JavaScript-Ereignishandler meldet die erste Änderung an die Sammlung.</span><span class="sxs-lookup"><span data-stu-id="8d207-219">The JavaScript event handler reports the first change to the collection.</span></span> <span data-ttu-id="8d207-220">Die zweite Änderung verfügt jedoch über einen doppelten Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="8d207-220">The second change, however, has a duplicate key.</span></span> <span data-ttu-id="8d207-221">Benutzer von .NET Framework-Wörterbüchern erwarten, dass die Add-Methode eine Ausnahme auslöst, was auch geschieht.</span><span class="sxs-lookup"><span data-stu-id="8d207-221">Users of .NET Framework dictionaries expect the Add method to throw an exception, and that is what happens.</span></span> <span data-ttu-id="8d207-222">JavaScript behandelt die .NET Framework-Ausnahme.</span><span class="sxs-lookup"><span data-stu-id="8d207-222">JavaScript handles the .NET Framework exception.</span></span>

> <span data-ttu-id="8d207-223">**Hinweis:** die Ausnahmemeldung aus JavaScript-Code können nicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="8d207-223">**Note**You can't display the exception's message from JavaScript code.</span></span> <span data-ttu-id="8d207-224">Der Meldungstext wird durch eine Ablaufverfolgung ersetzt.</span><span class="sxs-lookup"><span data-stu-id="8d207-224">The message text is replaced by a stack trace.</span></span> <span data-ttu-id="8d207-225">Weitere Informationen finden Sie unter „Auslösen von Ausnahmen“ unter „Erstellen von Komponenten für Windows-Runtime in C# und Visual Basic“.</span><span class="sxs-lookup"><span data-stu-id="8d207-225">For more information, see "Throwing exceptions" in Creating Windows Runtime Components in C# and Visual Basic.</span></span>

<span data-ttu-id="8d207-226">Im Gegensatz dazu wird der Wert des Elements geändert, wenn JavaScript die Insert-Methode mit einem doppelten Schlüssel aufruft.</span><span class="sxs-lookup"><span data-stu-id="8d207-226">By contrast, when JavaScript called the insert method with a duplicate key, the value of the item was changed.</span></span> <span data-ttu-id="8d207-227">Dieser Verhaltensunterschied entsteht aufgrund der unterschiedlichen Methoden, mit denen JavaScript und .NET Framework Windows-Runtime unterstützen, wie in [Erstellen von Komponenten für Windows-Runtime in C# und Visual Basic](creating-windows-runtime-components-in-csharp-and-visual-basic.md) erläutert wird.</span><span class="sxs-lookup"><span data-stu-id="8d207-227">This difference in behavior is due to the different ways that JavaScript and the .NET Framework support the Windows Runtime, as explained in [Creating Windows Runtime Components in C# and Visual Basic](creating-windows-runtime-components-in-csharp-and-visual-basic.md).</span></span>

## <a name="returning-managed-types-from-your-component"></a><span data-ttu-id="8d207-228">Zurückgeben von verwalteten Typen von der Komponente</span><span class="sxs-lookup"><span data-stu-id="8d207-228">Returning managed types from your component</span></span>


<span data-ttu-id="8d207-229">Wie zuvor erwähnt, können Sie systemeigene Windows-Runtime-Typen frei zwischen dem JavaScript-Code und dem C#- oder Visual Basic-Code übergeben.</span><span class="sxs-lookup"><span data-stu-id="8d207-229">As discussed previously, you can pass native Windows Runtime types back and forth freely between your JavaScript code and your C# or Visual Basic code.</span></span> <span data-ttu-id="8d207-230">In den meisten Fällen sind die Namen und Membernamen in beiden Fällen identisch (die Namen der Member beginnen in JavaScript lediglich mit Kleinbuchstaben).</span><span class="sxs-lookup"><span data-stu-id="8d207-230">Most of the time, the type names and member names will be the same in both cases (except that the member names start with lowercase letters in JavaScript).</span></span> <span data-ttu-id="8d207-231">Im vorherigen Abschnitt schien die PropertySet-Klasse allerdings andere Member im verwalteten Code zu haben.</span><span class="sxs-lookup"><span data-stu-id="8d207-231">However, in the preceding section, the PropertySet class appeared to have different members in managed code.</span></span> <span data-ttu-id="8d207-232">(Sie haben beispielsweise in JavaScript die Insert-Methode und im .NET Framework-Code die Add-Methode aufgerufen.) In diesem Abschnitt wird erläutert, wie sich diese Unterschiede auf .NET Framework-Typen auswirken, die an JavaScript übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="8d207-232">(For example, in JavaScript you called the insert method, and in the .NET Framework code you called the Add method.) This section explores the way those differences affect .NET Framework types passed to JavaScript.</span></span>

<span data-ttu-id="8d207-233">Zusätzlich zum Zurückgeben von Windows-Runtime-Typen, die Sie in der Komponente erstellt oder von JavaScript an die Komponente übergeben haben, können Sie einen verwalteten Typ, der in verwaltetem Code erstellt wurde, an JavaScript so zurückgeben, als wäre er der entsprechende Windows-Runtime-Typ.</span><span class="sxs-lookup"><span data-stu-id="8d207-233">In addition to returning Windows Runtime types that you created in your component or passed to your component from JavaScript, you can return a managed type, created in managed code, to JavaScript as if it were the corresponding Windows Runtime type.</span></span> <span data-ttu-id="8d207-234">Auch im ersten, einfachen Beispiel einer Laufzeitklasse waren die Parameter und die Rückgabetypen der Member Visual Basic- oder primitive C#-Typen, die .NET Framework-Typen entsprechen.</span><span class="sxs-lookup"><span data-stu-id="8d207-234">Even in the first, simple example of a runtime class, the parameters and return types of the members were Visual Basic or C# primitive types, which are .NET Framework types.</span></span> <span data-ttu-id="8d207-235">Fügen Sie den folgenden Code zur „Example“-Klasse hinzu, um dies für Sammlungen zu demonstrieren und eine Methode zu erstellen, die ein generisches Wörterbuch mit Zeichenfolgen zurückgibt, die durch Ganzzahlen indiziert sind:</span><span class="sxs-lookup"><span data-stu-id="8d207-235">To demonstrate this for collections, add the following code to the Example class, to create a method that returns a generic dictionary of strings, indexed by integers:</span></span>

> [!div class="tabbedCodeSnippets"]
> ```csharp
> public static IDictionary<int, string> GetMapOfNames()
> {
>     Dictionary<int, string> retval = new Dictionary<int, string>();
>     retval.Add(1, "one");
>     retval.Add(2, "two");
>     retval.Add(3, "three");
>     retval.Add(42, "forty-two");
>     retval.Add(100, "one hundred");
>     return retval;
> }
> ```
> ```vb
> Public Shared Function GetMapOfNames() As IDictionary(Of Integer, String)
>     Dim retval As New Dictionary(Of Integer, String)
>     retval.Add(1, "one")
>     retval.Add(2, "two")
>     retval.Add(3, "three")
>     retval.Add(42, "forty-two")
>     retval.Add(100, "one hundred")
>     Return retval
> End Function
> ```

<span data-ttu-id="8d207-236">Beachten Sie, dass das Wörterbuch als Schnittstelle zurückgegeben werden muss, die von [Dictionary&lt;TKey, TValue&gt;](https://msdn.microsoft.com/library/xfhwa508.aspx) implementiert wird und die einer Windows-Runtime-Schnittstelle zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="8d207-236">Notice that the dictionary must be returned as an interface that is implemented by [Dictionary&lt;TKey, TValue&gt;](https://msdn.microsoft.com/library/xfhwa508.aspx), and that maps to a Windows Runtime interface.</span></span> <span data-ttu-id="8d207-237">In diesem Fall ist die Schnittstelle „IDictionary&lt;int, string&gt;“ („IDictionary(Of Integer, String)“ in Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="8d207-237">In this case, the interface is IDictionary&lt;int, string&gt; (IDictionary(Of Integer, String) in Visual Basic).</span></span> <span data-ttu-id="8d207-238">Wenn der Windows-Runtime-Typ „IMap&lt;int, string&gt;“ an verwalteten Code übergeben wird, wird er als „IDictionary&lt;int, string&gt; angezeigt. Der umgekehrte Fall gilt, wenn der verwaltete Typ an JavaScript übergeben wird.</span><span class="sxs-lookup"><span data-stu-id="8d207-238">When the Windows Runtime type IMap&lt;int, string&gt; is passed to managed code, it appears as IDictionary&lt;int, string&gt;, and the reverse is true when the managed type is passed to JavaScript.</span></span>

<span data-ttu-id="8d207-239">**Wichtige**Wenn ein verwalteter Typ mehrere Schnittstellen implementiert, verwendet JavaScript die Schnittstelle, die zuerst in der Liste angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8d207-239">**Important**When a managed type implements multiple interfaces, JavaScript uses the interface that appears first in the list.</span></span> <span data-ttu-id="8d207-240">Wenn Sie beispielsweise Dictionary&lt;int, string&gt; an JavaScript-Code zurückgeben, wird IDictionary&lt;int, string&gt; angezeigt, unabhängig davon, welche Schnittstelle Sie als Rückgabetyp angeben.</span><span class="sxs-lookup"><span data-stu-id="8d207-240">For example, if you return Dictionary&lt;int, string&gt; to JavaScript code, it appears as IDictionary&lt;int, string&gt; no matter which interface you specify as the return type.</span></span> <span data-ttu-id="8d207-241">Das bedeutet, dass die erste Schnittstelle Member enthalten muss, die in den nächsten Schnittstellen erscheinen, damit diese Member für JavaScript sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="8d207-241">This means that if the first interface doesn't include a member that appears on later interfaces, that member isn't visible to JavaScript.</span></span>

 

<span data-ttu-id="8d207-242">Fügen Sie zum Testen der neuen Methode und Verwenden des Wörterbuchs die Funktionen „returns1“ und „returns2“ zu „default.js“ hinzu:</span><span class="sxs-lookup"><span data-stu-id="8d207-242">To test the new method and use the dictionary, add the returns1 and returns2 functions to default.js:</span></span>

```javascript
var names;

function returns1() {
    names = SampleComponent.Example.getMapOfNames();
    document.getElementById('output').innerHTML = showMap(names);
}

var ct = 7;

function returns2() {
    if (!names.hasKey(17)) {
        names.insert(43, "forty-three");
        names.insert(17, "seventeen");
    }
    else {
        var err = names.insert("7", ct++);
        names.insert("forty", "forty");
    }
    document.getElementById('output').innerHTML = showMap(names);
}

function showMap(map) {
    var item = map.first();
    var retval = "<ul>";

    for (var i = 0, len = map.size; i < len; i++) {
        retval += "<li>" + item.current.key + ": " + item.current.value + "</li>";
        item.moveNext();
    }
    return retval + "</ul>";
}
```

<span data-ttu-id="8d207-243">Fügen Sie den Ereignisregistrierungscode dem gleichen THEN-Block hinzu, dem Sie auch den anderen Ereignisregistrierungscode hinzugefügt haben:</span><span class="sxs-lookup"><span data-stu-id="8d207-243">Add the event registration code to the same then block as the other event registration code:</span></span>

```javascript
var returnsButton1 = document.getElementById("returnsButton1");
returnsButton1.addEventListener("click", returns1, false);
var returnsButton2 = document.getElementById("returnsButton2");
returnsButton2.addEventListener("click", returns2, false);
```

<span data-ttu-id="8d207-244">Zu diesem JavaScript-Code gibt es einige interessante Aspekte.</span><span class="sxs-lookup"><span data-stu-id="8d207-244">There are a few interesting things to observe about this JavaScript code.</span></span> <span data-ttu-id="8d207-245">Zunächst einmal enthält er eine showMap-Funktion, um den Inhalt des Wörterbuchs in HTML-Code anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="8d207-245">First of all, it includes a showMap function to display the contents of the dictionary in HTML.</span></span> <span data-ttu-id="8d207-246">Beachten Sie im Code für „showMap“ das Iterationsmuster.</span><span class="sxs-lookup"><span data-stu-id="8d207-246">In the code for showMap, notice the iteration pattern.</span></span> <span data-ttu-id="8d207-247">In .NET Framework gibt es keine First-Methode für die generische IDictionary-Schnittstelle, und die Größe wird durch eine Count-Eigenschaft anstatt durch eine Size-Methode zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="8d207-247">In the .NET Framework, there's no First method on the generic IDictionary interface, and the size is returned by a Count property rather than by a Size method.</span></span> <span data-ttu-id="8d207-248">Für JavaScript entspricht „IDictionary&lt;int, string&gt;“ dem Windows-Runtime-Typ „IMap&lt;int, string&gt;“.</span><span class="sxs-lookup"><span data-stu-id="8d207-248">To JavaScript, IDictionary&lt;int, string&gt; appears to be the Windows Runtime type IMap&lt;int, string&gt;.</span></span> <span data-ttu-id="8d207-249">(Siehe die [IMap&lt;K,V&gt;](https://msdn.microsoft.com/library/windows/apps/br226042.aspx)-Schnittstelle.)</span><span class="sxs-lookup"><span data-stu-id="8d207-249">(See the [IMap&lt;K,V&gt;](https://msdn.microsoft.com/library/windows/apps/br226042.aspx) interface.)</span></span>

<span data-ttu-id="8d207-250">In der returns2-Funktion ruft JavaScript wie in früheren Beispielen die Insert-Methode („Insert“ in JavaScript) auf, um dem Wörterbuch Elemente hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="8d207-250">In the returns2 function, as in earlier examples, JavaScript calls the Insert method (insert in JavaScript) to add items to the dictionary.</span></span>

<span data-ttu-id="8d207-251">Drücken Sie zum Ausführen der App die F5-TASTE.</span><span class="sxs-lookup"><span data-stu-id="8d207-251">To run the app, choose the F5 key.</span></span> <span data-ttu-id="8d207-252">Um den anfänglichen Inhalt des Wörterbuchs zu erstellen und anzuzeigen, wählen Sie die Schaltfläche **Returns1** aus.</span><span class="sxs-lookup"><span data-stu-id="8d207-252">To create and display the initial contents of the dictionary, choose the **Returns 1** button.</span></span> <span data-ttu-id="8d207-253">Um zwei weitere Einträge zum Wörterbuch hinzuzufügen, wählen Sie die Schaltfläche **Returns2** aus.</span><span class="sxs-lookup"><span data-stu-id="8d207-253">To add two more entries to the dictionary, choose the **Returns 2** button.</span></span> <span data-ttu-id="8d207-254">Beachten Sie, dass die Einträge in der Reihenfolge der Einfügung angezeigt werden, wie Sie dies von „Dictionary&lt;TKey, TValue&gt;“ erwarten würden.</span><span class="sxs-lookup"><span data-stu-id="8d207-254">Notice that the entries are displayed in order of insertion, as you would expect from Dictionary&lt;TKey, TValue&gt;.</span></span> <span data-ttu-id="8d207-255">Wenn sie sortiert werden sollen, können Sie „SortedDictionary&lt;int, string&gt;“ von „GetMapOfNames“ zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="8d207-255">If you want them sorted, you can return a SortedDictionary&lt;int, string&gt; from GetMapOfNames.</span></span> <span data-ttu-id="8d207-256">(Die PropertySet-Klasse, die in früheren Beispielen verwendet wurde, hat eine andere interne Organisation als „Dictionary&lt;TKey, TValue&gt;“.)</span><span class="sxs-lookup"><span data-stu-id="8d207-256">(The PropertySet class used in earlier examples has a different internal organization from Dictionary&lt;TKey, TValue&gt;.)</span></span>

<span data-ttu-id="8d207-257">JavaScript ist natürlich keine stark typisierte Sprache, sodass das Verwenden stark typisierter generischer Collections zu überraschenden Ergebnissen führen kann.</span><span class="sxs-lookup"><span data-stu-id="8d207-257">Of course, JavaScript is not a strongly typed language, so using strongly typed generic collections can lead to some surprising results.</span></span> <span data-ttu-id="8d207-258">Wählen Sie erneut die Schaltfläche **Returns2** aus.</span><span class="sxs-lookup"><span data-stu-id="8d207-258">Choose the **Returns 2** button again.</span></span> <span data-ttu-id="8d207-259">JavaScript wandelt die „7“ pflichtgemäß in eine numerische 7 um, und die numerische 7 wird in ct in einer Zeichenfolge gespeichert.</span><span class="sxs-lookup"><span data-stu-id="8d207-259">JavaScript obligingly coerces the "7" to a numeric 7, and the numeric 7 that's stored in ct to a string.</span></span> <span data-ttu-id="8d207-260">Außerdem wird die Zeichenfolge „forty“ in „null“ umgewandelt.</span><span class="sxs-lookup"><span data-stu-id="8d207-260">And it coerces the string "forty" to zero.</span></span> <span data-ttu-id="8d207-261">Aber das ist erst der Anfang.</span><span class="sxs-lookup"><span data-stu-id="8d207-261">But that's only the beginning.</span></span> <span data-ttu-id="8d207-262">Wählen Sie die Schaltfläche **Returns2** noch einige weitere Male aus.</span><span class="sxs-lookup"><span data-stu-id="8d207-262">Choose the **Returns 2** button a few more times.</span></span> <span data-ttu-id="8d207-263">Im verwalteten Code würde die Add-Methode Ausnahmen aufgrund doppelter Schlüssel auch dann generieren, wenn die Werte in die richtigen Typen umgewandelt wurden.</span><span class="sxs-lookup"><span data-stu-id="8d207-263">In managed code, the Add method would generate duplicate key exceptions, even if the values were cast to the correct types.</span></span> <span data-ttu-id="8d207-264">Im Gegensatz dazu aktualisiert die Insert-Methode den Wert, der einem bestehenden Schlüssel zugeordnet ist, und gibt einen booleschen Wert zurück, der angibt, ob ein neuer Schlüssel zum Wörterbuch hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="8d207-264">In contrast, the Insert method updates the value associated with an existing key and returns a Boolean value that indicates whether a new key was added to the dictionary.</span></span> <span data-ttu-id="8d207-265">Deshalb ändert sich der dem Schlüssel 7 zugeordnete Wert ständig.</span><span class="sxs-lookup"><span data-stu-id="8d207-265">This is why the value associated with the key 7 keeps changing.</span></span>

<span data-ttu-id="8d207-266">Ein weiteres unerwartetes Verhalten: Wenn Sie eine nicht zugewiesene JavaScript-Variable als Zeichenfolgenargument übergeben, erhalten Sie die Zeichenfolge „undefined“.</span><span class="sxs-lookup"><span data-stu-id="8d207-266">Another unexpected behavior: If you pass an unassigned JavaScript variable as a string argument, what you get is the string "undefined".</span></span> <span data-ttu-id="8d207-267">Kurz gesagt sollten Sie mit Bedacht vorgehen, wenn Sie .NET Framework-Sammlungstypen an Ihren JavaScript-Code übergeben.</span><span class="sxs-lookup"><span data-stu-id="8d207-267">In short, be careful when you pass .NET Framework collection types to your JavaScript code.</span></span>

> <span data-ttu-id="8d207-268">**Hinweis:** Wenn große Textmengen verkettet werden müssen, können Sie dies tun effizienter durch den Code in einer .NET Framework-Methode verschieben und die StringBuilder-Klasse, wie in der ShowMap-Funktion gezeigt.</span><span class="sxs-lookup"><span data-stu-id="8d207-268">**Note**If you have large quantities of text to concatenate, you can do it more efficiently by moving the code into a .NET Framework method and using the StringBuilder class, as shown in the showMap function.</span></span>

<span data-ttu-id="8d207-269">Obwohl Sie Ihre eigenen generischen Typen aus einer Komponente für Windows-Runtime nicht verfügbar machen können, können Sie generische .NET Framework-Collections für Windows-Runtime-Klassen zurückgeben, indem Sie Code wie den folgenden verwenden:</span><span class="sxs-lookup"><span data-stu-id="8d207-269">Although you can't expose your own generic types from a Windows Runtime component, you can return .NET Framework generic collections for Windows Runtime classes by using code such as the following:</span></span>

> [!div class="tabbedCodeSnippets"]
> ```csharp
> public static object GetListOfThis(object obj)
> {
>     Type target = obj.GetType();
>     return Activator.CreateInstance(typeof(List<>).MakeGenericType(target));
> }
> ```
> ```vb
> Public Shared Function GetListOfThis(obj As Object) As Object
>     Dim target As Type = obj.GetType()
>     Return Activator.CreateInstance(GetType(List(Of )).MakeGenericType(target))
> End Function
> ```

<span data-ttu-id="8d207-270">„List&lt;T&gt;“ implementiert „IList&lt;T&gt;“, der als Windows-Runtime-Typ „IVector&lt;T&gt;“ in JavaScript angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8d207-270">List&lt;T&gt; implements IList&lt;T&gt;, which appears as the Windows Runtime type IVector&lt;T&gt; in JavaScript.</span></span>

## <a name="declaring-events"></a><span data-ttu-id="8d207-271">Deklarieren von Ereignissen</span><span class="sxs-lookup"><span data-stu-id="8d207-271">Declaring events</span></span>


<span data-ttu-id="8d207-272">Sie können Ereignisse mit dem standardmäßigen .NET Framework-Ereignismuster oder mit anderen Mustern deklarieren, die von Windows-Runtime verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="8d207-272">You can declare events by using the standard .NET Framework event pattern or other patterns used by the Windows Runtime.</span></span> <span data-ttu-id="8d207-273">.NET Framework unterstützt die Äquivalenz zwischen dem System.EventHandler&lt;TEventArgs&gt;-Delegaten und dem EventHandler&lt;T&gt;-Delegaten von Windows-Runtime, sodass sich die Verwendung von „EventHandler&lt;TEventArgs&gt;“ gut zum Implementieren des .NET Framework-Standardmusters eignet.</span><span class="sxs-lookup"><span data-stu-id="8d207-273">The .NET Framework supports equivalence between the System.EventHandler&lt;TEventArgs&gt; delegate and the Windows Runtime EventHandler&lt;T&gt; delegate, so using EventHandler&lt;TEventArgs&gt; is a good way to implement the standard .NET Framework pattern.</span></span> <span data-ttu-id="8d207-274">Fügen Sie zur Demonstration der Funktionsweise das folgende Klassenpaar dem „SampleComponent“-Projekt hinzu:</span><span class="sxs-lookup"><span data-stu-id="8d207-274">To see how this works, add the following pair of classes to the SampleComponent project:</span></span>

> [!div class="tabbedCodeSnippets"]
> ```csharp
> namespace SampleComponent
> {
>     public sealed class Eventful
>     {
>         public event EventHandler<TestEventArgs> Test;
>         public void OnTest(string msg, long number)
>         {
>             EventHandler<TestEventArgs> temp = Test;
>             if (temp != null)
>             {
>                 temp(this, new TestEventArgs()
>                 {
>                     Value1 = msg,
>                     Value2 = number
>                 });
>             }
>         }
>     }
>
>     public sealed class TestEventArgs
>     {
>         public string Value1 { get; set; }
>         public long Value2 { get; set; }
>     }
> }
> ```
> ```vb
> Public NotInheritable Class Eventful
>     Public Event Test As EventHandler(Of TestEventArgs)
>     Public Sub OnTest(ByVal msg As String, ByVal number As Long)
>         RaiseEvent Test(Me, New TestEventArgs() With {
>                             .Value1 = msg,
>                             .Value2 = number
>                             })
>     End Sub
> End Class
>
> Public NotInheritable Class TestEventArgs
>     Public Property Value1 As String
>     Public Property Value2 As Long
> End Class
> ```

<span data-ttu-id="8d207-275">Wenn Sie ein Ereignis in Windows-Runtime verfügbar machen, erbt die „EventArgs“-Klasse von „System.Object“.</span><span class="sxs-lookup"><span data-stu-id="8d207-275">When you expose an event in the Windows Runtime, the event argument class inherits from System.Object.</span></span> <span data-ttu-id="8d207-276">Sie erbt anders als in .NET Framework nicht von System.EventArgs, da EventArgs kein Windows-Runtime-Typ ist.</span><span class="sxs-lookup"><span data-stu-id="8d207-276">It doesn't inherit from System.EventArgs, as it would in the .NET Framework, because EventArgs is not a Windows Runtime type.</span></span>

<span data-ttu-id="8d207-277">Wenn Sie benutzerdefinierte Ereignisaccessoren für das Ereignis deklarieren (**Custom**-Schlüsselwort in Visual Basic), müssen Sie das Windows-Runtime-Ereignismuster verwenden.</span><span class="sxs-lookup"><span data-stu-id="8d207-277">If you declare custom event accessors for your event (**Custom** keyword in Visual Basic), you must use the Windows Runtime event pattern.</span></span> <span data-ttu-id="8d207-278">Siehe [Benutzerdefinierte Ereignisse und Ereignisaccessoren in Komponenten für Windows-Runtime](custom-events-and-event-accessors-in-windows-runtime-components.md).</span><span class="sxs-lookup"><span data-stu-id="8d207-278">See [Custom events and event accessors in Windows Runtime Components](custom-events-and-event-accessors-in-windows-runtime-components.md).</span></span>

<span data-ttu-id="8d207-279">Fügen Sie die events1-Funktion zu „default.js“ hinzu, um das Testereignis zu behandeln.</span><span class="sxs-lookup"><span data-stu-id="8d207-279">To handle the Test event, add the events1 function to default.js.</span></span> <span data-ttu-id="8d207-280">Die „events1“Funktion erstellt eine Ereignishandlerfunktion für das Testereignis und ruft sofort die „OnTest-Methode“ zum Auslösen des Ereignisses auf.</span><span class="sxs-lookup"><span data-stu-id="8d207-280">The events1 function creates an event handler function for the Test event, and immediately invokes the OnTest method to raise the event.</span></span> <span data-ttu-id="8d207-281">Wenn Sie einen Haltepunkt im Textbereich des Ereignishandlers platzieren, können Sie sehen, dass das Objekt, das an den einzelnen Parameter übergeben wird, das Quellobjekt und beide Member von „TestEventArgs“ enthält.</span><span class="sxs-lookup"><span data-stu-id="8d207-281">If you place a breakpoint in the body of the event handler, you can see that the object passed to the single parameter includes the source object and both members of TestEventArgs.</span></span>

```javascript
var ev;

function events1() {
   ev = new SampleComponent.Eventful();
   ev.addEventListener("test", function (e) {
       document.getElementById('output').innerHTML = e.value1;
       document.getElementById('output').innerHTML += "<br/>" + e.value2;
   });
   ev.onTest("Number of feet in a mile:", 5280);
}
```

<span data-ttu-id="8d207-282">Fügen Sie den Ereignisregistrierungscode dem gleichen THEN-Block hinzu, dem Sie auch den anderen Ereignisregistrierungscode hinzugefügt haben:</span><span class="sxs-lookup"><span data-stu-id="8d207-282">Add the event registration code to the same then block as the other event registration code:</span></span>

```javascript
var events1Button = document.getElementById("events1Button");
events1Button.addEventListener("click", events1, false);
```

## <a name="exposing-asynchronous-operations"></a><span data-ttu-id="8d207-283">Bereitstellen asynchroner Vorgänge</span><span class="sxs-lookup"><span data-stu-id="8d207-283">Exposing asynchronous operations</span></span>


<span data-ttu-id="8d207-284">.NET Framework verfügt über eine Vielzahl von Tools für die asynchrone und parallele Verarbeitung – basierend auf der Aufgabe und auf generischen [Task&lt;TResult&gt;](https://msdn.microsoft.com/library/dd321424.aspx)-Klassen.</span><span class="sxs-lookup"><span data-stu-id="8d207-284">The .NET Framework has a rich set of tools for asynchronous processing and parallel processing, based on the Task and generic [Task&lt;TResult&gt;](https://msdn.microsoft.com/library/dd321424.aspx) classes.</span></span> <span data-ttu-id="8d207-285">Um die aufgabenbasierte asynchrone Verarbeitung in einer Komponente für Windows-Runtime verfügbar zu machen, verwenden Sie die Windows-Runtime-Schnittstellen [IAsyncAction](https://msdn.microsoft.com/library/br205781.aspx), [IAsyncActionWithProgress&lt;TProgress&gt;](https://msdn.microsoft.com/library/br205784.aspx), [IAsyncOperation&lt;TResult&gt;](https://msdn.microsoft.com/library/br205802.aspx) und [IAsyncOperationWithProgress&lt;TResult, TProgress&gt;](https://msdn.microsoft.com/library/br205807.aspx).</span><span class="sxs-lookup"><span data-stu-id="8d207-285">To expose task-based asynchronous processing in a Windows Runtime component, use the Windows Runtime interfaces [IAsyncAction](https://msdn.microsoft.com/library/br205781.aspx), [IAsyncActionWithProgress&lt;TProgress&gt;](https://msdn.microsoft.com/library/br205784.aspx), [IAsyncOperation&lt;TResult&gt;](https://msdn.microsoft.com/library/br205802.aspx), and [IAsyncOperationWithProgress&lt;TResult, TProgress&gt;](https://msdn.microsoft.com/library/br205807.aspx).</span></span> <span data-ttu-id="8d207-286">(In Windows-Runtime geben Vorgänge Ergebnisse zurück, Aktionen aber nicht.)</span><span class="sxs-lookup"><span data-stu-id="8d207-286">(In the Windows Runtime, operations return results, but actions do not.)</span></span>

<span data-ttu-id="8d207-287">In diesem Abschnitt wird ein abbrechbarer asynchroner Vorgang veranschaulicht, der den Status meldet und Ergebnisse zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="8d207-287">This section demonstrates a cancelable asynchronous operation that reports progress and returns results.</span></span> <span data-ttu-id="8d207-288">Die GetPrimesInRangeAsync-Methode verwendet die [AsyncInfo](https://msdn.microsoft.com/library/system.runtime.interopservices.windowsruntime.asyncinfo.aspx)-Klasse, um eine Aufgabe zu generieren und die Abbruch- und Statusmeldungsfeatures mit einem WinJS.Promise-Objekt zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="8d207-288">The GetPrimesInRangeAsync method uses the [AsyncInfo](https://msdn.microsoft.com/library/system.runtime.interopservices.windowsruntime.asyncinfo.aspx) class to generate a task and to connect its cancellation and progress-reporting features to a WinJS.Promise object.</span></span> <span data-ttu-id="8d207-289">Fügen Sie der Beispielklasse zunächst die GetPrimesInRangeAsync-Methode hinzu:</span><span class="sxs-lookup"><span data-stu-id="8d207-289">Begin by adding the GetPrimesInRangeAsync method to the example class:</span></span>

> [!div class="tabbedCodeSnippets"]
> ```csharp
> using System.Runtime.InteropServices.WindowsRuntime;
> using Windows.Foundation;
>
> public static IAsyncOperationWithProgress<IList<long>, double>
> GetPrimesInRangeAsync(long start, long count)
> {
>     if (start < 2 || count < 1) throw new ArgumentException();
>
>     return AsyncInfo.Run<IList<long>, double>((token, progress) =>
>
>         Task.Run<IList<long>>(() =>
>         {
>             List<long> primes = new List<long>();
>             double onePercent = count / 100;
>             long ctProgress = 0;
>             double nextProgress = onePercent;
>
>             for (long candidate = start; candidate < start + count; candidate++)
>             {
>                 ctProgress += 1;
>                 if (ctProgress >= nextProgress)
>                 {
>                     progress.Report(ctProgress / onePercent);
>                     nextProgress += onePercent;
>                 }
>                 bool isPrime = true;
>                 for (long i = 2, limit = (long)Math.Sqrt(candidate); i <= limit; i++)
>                 {
>                     if (candidate % i == 0)
>                     {
>                         isPrime = false;
>                         break;
>                     }
>                 }
>                 if (isPrime) primes.Add(candidate);
>
>                 token.ThrowIfCancellationRequested();
>             }
>             progress.Report(100.0);
>             return primes;
>         }, token)
>     );
> }
> ```
> ```vb
> Imports System.Runtime.InteropServices.WindowsRuntime
>
> Public Shared Function GetPrimesInRangeAsync(ByVal start As Long, ByVal count As Long)
> As IAsyncOperationWithProgress(Of IList(Of Long), Double)
>
>     If (start < 2 Or count < 1) Then Throw New ArgumentException()
>
>     Return AsyncInfo.Run(Of IList(Of Long), Double)( _
>         Function(token, prog)
>             Return Task.Run(Of IList(Of Long))( _
>                 Function()
>                     Dim primes As New List(Of Long)
>                     Dim onePercent As Long = count / 100
>                     Dim ctProgress As Long = 0
>                     Dim nextProgress As Long = onePercent
>
>                     For candidate As Long = start To start + count - 1
>                         ctProgress += 1
>
>                         If ctProgress >= nextProgress Then
>                             prog.Report(ctProgress / onePercent)
>                             nextProgress += onePercent
>                         End If
>
>                         Dim isPrime As Boolean = True
>                         For i As Long = 2 To CLng(Math.Sqrt(candidate))
>                             If (candidate Mod i) = 0 Then
>                                 isPrime = False
>                                 Exit For
>                             End If
>                         Next
>
>                         If isPrime Then primes.Add(candidate)
>
>                         token.ThrowIfCancellationRequested()
>                     Next
>                     prog.Report(100.0)
>                     Return primes
>                 End Function, token)
>         End Function)
> End Function
> ```

<span data-ttu-id="8d207-290">„GetPrimesInRangeAsync“ ist eine sehr einfache Primzahlensuche – das ist beabsichtigt.</span><span class="sxs-lookup"><span data-stu-id="8d207-290">GetPrimesInRangeAsync is a very simple prime number finder, and that's by design.</span></span> <span data-ttu-id="8d207-291">Hier liegt der Schwerpunkt auf der Implementierung eines asynchronen Vorgangs. Einfachheit ist also wichtig, und eine langsame Implementierung ist von Vorteil, wenn wir den Abbruch demonstrieren.</span><span class="sxs-lookup"><span data-stu-id="8d207-291">The focus here is on implementing an asynchronous operation, so simplicity is important, and a slow implementation is an advantage when we're demonstrating cancellation.</span></span> <span data-ttu-id="8d207-292">„GetPrimesInRangeAsync“ sucht einfach nur Primzahlen: Die Methode teilt einen Kandidaten durch alle Ganzzahlen, die kleiner oder gleich dessen Quadratwurzel sind, anstatt nur die Primzahlen zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="8d207-292">GetPrimesInRangeAsync finds primes by brute force: It divides a candidate by all the integers that are less than or equal to its square root, rather than using only the prime numbers.</span></span> <span data-ttu-id="8d207-293">Schrittweises Durchlaufen des Codes:</span><span class="sxs-lookup"><span data-stu-id="8d207-293">Stepping through this code:</span></span>

-   <span data-ttu-id="8d207-294">Führen Sie vor dem Start eines asynchronen Vorgangs Aufgaben wie z. B. das Überprüfen von Parametern und das Auslösen von Ausnahmen bei einer ungültigen Eingabe aus.</span><span class="sxs-lookup"><span data-stu-id="8d207-294">Before starting an asynchronous operation, perform housekeeping activities such as validating parameters and throwing exceptions for invalid input.</span></span>
-   <span data-ttu-id="8d207-295">Der zentrale Punkt dieser Implementierung sind die Methode [AsyncInfo.Run&lt;TResult, TProgress&gt;(Func&lt;CancellationToken, IProgress&lt;TProgress&gt;, Task&lt;TResult&gt;](https://msdn.microsoft.com/library/hh779740.aspx)&gt;) und der Delegat, der den einzigen Parameter der Methode darstellt.</span><span class="sxs-lookup"><span data-stu-id="8d207-295">The key to this implementation is the [AsyncInfo.Run&lt;TResult, TProgress&gt;(Func&lt;CancellationToken, IProgress&lt;TProgress&gt;, Task&lt;TResult&gt;](https://msdn.microsoft.com/library/hh779740.aspx)&gt;) method, and the delegate that is the method's only parameter.</span></span> <span data-ttu-id="8d207-296">Der Delegat muss ein Abbruchtoken und eine Schnittstelle für Statusmeldungen akzeptieren und muss eine gestartete Aufgabe zurückgeben, die diese Parameter verwendet.</span><span class="sxs-lookup"><span data-stu-id="8d207-296">The delegate must accept a cancellation token and an interface for reporting progress, and must return a started task that uses those parameters.</span></span> <span data-ttu-id="8d207-297">Wenn JavaScript die GetPrimesInRangeAsync-Methode aufruft, treten die folgenden Schritte auf (nicht unbedingt in der hier angegebenen Reihenfolge):</span><span class="sxs-lookup"><span data-stu-id="8d207-297">When JavaScript calls the GetPrimesInRangeAsync method, the following steps occur (not necessarily in the order given here):</span></span>

    -   <span data-ttu-id="8d207-298">Das [WinJS.Promise](https://msdn.microsoft.com/library/windows/apps/br211867.aspx)-Objekt stellt Funktionen zum Verarbeiten der zurückgegebenen Ergebnisse, zum Reagieren auf einen Abbruch und zum Behandeln von Statusberichten bereit.</span><span class="sxs-lookup"><span data-stu-id="8d207-298">The [WinJS.Promise](https://msdn.microsoft.com/library/windows/apps/br211867.aspx) object supplies functions to process the returned results, react to cancellation, and handle progress reports.</span></span>
    -   <span data-ttu-id="8d207-299">Die AsyncInfo.Run-Methode erstellt eine Abbruchquelle und ein Objekt, das die IProgress&lt;T&gt;-Schnittstelle implementiert.</span><span class="sxs-lookup"><span data-stu-id="8d207-299">The AsyncInfo.Run method creates a cancellation source and an object that implements the IProgress&lt;T&gt; interface.</span></span> <span data-ttu-id="8d207-300">Sie übergibt ein [CancellationToken](https://msdn.microsoft.com/library/system.threading.cancellationtoken.aspx)-Token aus der Abbruchquelle und die [IProgress&lt;T&gt;](https://msdn.microsoft.com/library/hh138298.aspx)-Schnittstelle an den Delegaten.</span><span class="sxs-lookup"><span data-stu-id="8d207-300">To the delegate, it passes both a [CancellationToken](https://msdn.microsoft.com/library/system.threading.cancellationtoken.aspx) token from the cancellation source, and the [IProgress&lt;T&gt;](https://msdn.microsoft.com/library/hh138298.aspx) interface.</span></span>

        > <span data-ttu-id="8d207-301">**Hinweis:** Wenn das Promise-Objekt keine Funktion auf einen Abbruch reagieren auf angeben, "asyncinfo.Run" dennoch ein abbrechbarer Token übergibt und Abbruch weiterhin möglich.</span><span class="sxs-lookup"><span data-stu-id="8d207-301">**Note**If the Promise object doesn't supply a function to react to cancellation, AsyncInfo.Run still passes a cancelable token, and cancellation can still occur.</span></span> <span data-ttu-id="8d207-302">Wenn das Promise-Objekt keine Funktion zum Behandeln von Statusaktualisierungen bereitstellt, stellt „AsyncInfo.Run“ dennoch ein Objekt bereit, das „ IProgress&lt;T&gt;“ implementiert, aber seine Berichte werden ignoriert.</span><span class="sxs-lookup"><span data-stu-id="8d207-302">If the Promise object doesn't supply a function to handle progress updates, AsyncInfo.Run still supplies an object that implements IProgress&lt;T&gt;, but its reports are ignored.</span></span>

    -   <span data-ttu-id="8d207-303">Der Delegat verwendet die Methode [Task.Run&lt;TResult&gt;(Func&lt;TResult&gt;, CancellationToken](https://msdn.microsoft.com/library/hh160376.aspx)), um eine gestartete Aufgabe zu erstellen, die das Token und die Statusschnittstelle verwendet.</span><span class="sxs-lookup"><span data-stu-id="8d207-303">The delegate uses the [Task.Run&lt;TResult&gt;(Func&lt;TResult&gt;, CancellationToken](https://msdn.microsoft.com/library/hh160376.aspx)) method to create a started task that uses the token and the progress interface.</span></span> <span data-ttu-id="8d207-304">Der Delegat für die gestartete Aufgabe wird durch eine Lambdafunktion bereitgestellt, die das gewünschte Ergebnis berechnet.</span><span class="sxs-lookup"><span data-stu-id="8d207-304">The delegate for the started task is provided by a lambda function that computes the desired result.</span></span> <span data-ttu-id="8d207-305">Mehr dazu später.</span><span class="sxs-lookup"><span data-stu-id="8d207-305">More about that in a moment.</span></span>
    -   <span data-ttu-id="8d207-306">Die AsyncInfo.Run-Methode erstellt ein Objekt, das die Schnittstelle [IAsyncOperationWithProgress&lt;TResult, TProgress&gt;](https://msdn.microsoft.com/library/windows/apps/br206594.aspx) implementiert, den Windows-Runtime-Abbruchmechanismus mit der Tokenquelle verbindet und die Statusberichtsfunktion des Promise-Objekts mit der IProgress&lt;T&gt;-Schnittstelle verbindet.</span><span class="sxs-lookup"><span data-stu-id="8d207-306">The AsyncInfo.Run method creates an object that implements the [IAsyncOperationWithProgress&lt;TResult, TProgress&gt;](https://msdn.microsoft.com/library/windows/apps/br206594.aspx) interface, connects the Windows Runtime cancellation mechanism with the token source, and connects the Promise object's progress-reporting function with the IProgress&lt;T&gt; interface.</span></span>
    -   <span data-ttu-id="8d207-307">Die IAsyncOperationWithProgress&lt;TResult, TProgress&gt;-Schnittstelle wird an JavaScript zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="8d207-307">The IAsyncOperationWithProgress&lt;TResult, TProgress&gt; interface is returned to JavaScript.</span></span>

-   <span data-ttu-id="8d207-308">Die Lambdafunktion, die durch die gestartete Aufgabe dargestellt wird, verwendet keine Argumente.</span><span class="sxs-lookup"><span data-stu-id="8d207-308">The lambda function that is represented by the started task doesn't take any arguments.</span></span> <span data-ttu-id="8d207-309">Da es sich um eine Lambdafunktion handelt, ist der Zugriff auf das Token und die IProgress-Schnittstelle möglich.</span><span class="sxs-lookup"><span data-stu-id="8d207-309">Because it's a lambda function, it has access to the token and the IProgress interface.</span></span> <span data-ttu-id="8d207-310">Jedes Mal, wenn eine Kandidatenzahl ausgewertet wird, geschieht Folgendes:</span><span class="sxs-lookup"><span data-stu-id="8d207-310">Each time a candidate number is evaluated, the lambda function:</span></span>

    -   <span data-ttu-id="8d207-311">Die Lambdafunktion überprüft, ob der nächste Prozentpunkt des Status erreicht wurde.</span><span class="sxs-lookup"><span data-stu-id="8d207-311">Checks to see whether the next percentage point of progress has been reached.</span></span> <span data-ttu-id="8d207-312">Ist dies der Fall, ruft die Lambdafunktion die IProgress&lt;T&gt;.Report-Methode auf, und der Prozentsatz wird an die Funktion übergeben, die das Promise-Objekt für Statusberichte angegeben hat.</span><span class="sxs-lookup"><span data-stu-id="8d207-312">If it has, the lambda function calls the IProgress&lt;T&gt;.Report method, and the percentage is passed through to the function that the Promise object specified for reporting progress.</span></span>
    -   <span data-ttu-id="8d207-313">Verwendet das Abbruchtoken zum Auslösen einer Ausnahme, wenn der Vorgang abgebrochen wurde.</span><span class="sxs-lookup"><span data-stu-id="8d207-313">Uses the cancellation token to throw an exception if the operation has been canceled.</span></span> <span data-ttu-id="8d207-314">Wenn die [IAsyncInfo.Cancel](https://msdn.microsoft.com/library/windows/apps/windows.foundation.iasyncinfo.cancel.aspx)-Methode (die von der IAsyncOperationWithProgress&lt;TResult, TProgress&gt;-Schnittstelle geerbt wird) aufgerufen wurde, sorgt die von der AsyncInfo.Run-Methode eingerichtete Verbindung dafür, dass das Abbruchtoken benachrichtigt wird.</span><span class="sxs-lookup"><span data-stu-id="8d207-314">If the [IAsyncInfo.Cancel](https://msdn.microsoft.com/library/windows/apps/windows.foundation.iasyncinfo.cancel.aspx) method (which the IAsyncOperationWithProgress&lt;TResult, TProgress&gt; interface inherits) has been called, the connection that the AsyncInfo.Run method set up ensures that the cancellation token is notified.</span></span>
-   <span data-ttu-id="8d207-315">Wenn die Lambdafunktion die Liste mit den Primzahlen zurückgibt, wird die Liste an die Funktion übergeben, die das WinJS.Promise-Objekt für die Verarbeitung der Ergebnisse angegeben hat.</span><span class="sxs-lookup"><span data-stu-id="8d207-315">When the lambda function returns the list of prime numbers, the list is passed to the function that the WinJS.Promise object specified for processing the results.</span></span>

<span data-ttu-id="8d207-316">Zum Erstellen der JavaScript-Zusage und zum Einrichten des Abbruchmechanismus fügen Sie die Funktionen „AsyncRun“ und „AsyncCancel“ zu „default.js“ hinzu.</span><span class="sxs-lookup"><span data-stu-id="8d207-316">To create the JavaScript promise and set up the cancellation mechanism, add the asyncRun and asyncCancel functions to default.js.</span></span>

```javascript
var resultAsync;
function asyncRun() {
    document.getElementById('output').innerHTML = "Retrieving prime numbers.";
    btnAsync.disabled = "disabled";
    btnCancel.disabled = "";

    resultAsync = SampleComponent.Example.getPrimesInRangeAsync(10000000000001, 2500).then(
        function (primes) {
            for (i = 0; i < primes.length; i++)
                document.getElementById('output').innerHTML += " " + primes[i];

            btnCancel.disabled = "disabled";
            btnAsync.disabled = "";
        },
        function () {
            document.getElementById('output').innerHTML += " -- getPrimesInRangeAsync was canceled. -- ";

            btnCancel.disabled = "disabled";
            btnAsync.disabled = "";
        },
        function (prog) {
            document.getElementById('primeProg').value = prog;
        }
    );
}

function asyncCancel() {    
    resultAsync.cancel();
}
```

<span data-ttu-id="8d207-317">Vergessen Sie nicht den Ereignisregistrierungscode (der gleiche wie zuvor).</span><span class="sxs-lookup"><span data-stu-id="8d207-317">Don't forget the event registration code the same as you did previously.</span></span>

```javascript
var btnAsync = document.getElementById("btnAsync");
btnAsync.addEventListener("click", asyncRun, false);
var btnCancel = document.getElementById("btnCancel");
btnCancel.addEventListener("click", asyncCancel, false);
```

<span data-ttu-id="8d207-318">Durch den Aufruf der asynchronen GetPrimesInRangeAsync-Methode erstellt die AsyncRun-Funktion ein WinJS.Promise-Objekt.</span><span class="sxs-lookup"><span data-stu-id="8d207-318">By calling the asynchronous GetPrimesInRangeAsync method, the asyncRun function creates a WinJS.Promise object.</span></span> <span data-ttu-id="8d207-319">Die then-Methode des Objekts verwendet drei Funktionen, die die zurückgegebenen Ergebnisse verarbeiten, auf Fehler reagieren (einschließlich Abbruch) und Statusberichte behandeln.</span><span class="sxs-lookup"><span data-stu-id="8d207-319">The object's then method takes three functions that process the returned results, react to errors (including cancellation), and handle progress reports.</span></span> <span data-ttu-id="8d207-320">In diesem Beispiel werden die zurückgegebenen Ergebnisse im Ausgabebereich angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8d207-320">In this example, the returned results are printed in the output area.</span></span> <span data-ttu-id="8d207-321">Bei Abbruch oder Abschluss werden die Schaltflächen, die den Vorgang starten und abbrechen, zurückgesetzt.</span><span class="sxs-lookup"><span data-stu-id="8d207-321">Cancellation or completion resets the buttons that launch and cancel the operation.</span></span> <span data-ttu-id="8d207-322">Die Statusberichte aktualisieren das Statussteuerelement.</span><span class="sxs-lookup"><span data-stu-id="8d207-322">Progress reporting updates the progress control.</span></span>

<span data-ttu-id="8d207-323">Die asyncCancel-Funktion ruft einfach die cancel-Methode des WinJS.Promise-Objekts auf.</span><span class="sxs-lookup"><span data-stu-id="8d207-323">The asyncCancel function just calls the cancel method of the WinJS.Promise object.</span></span>

<span data-ttu-id="8d207-324">Drücken Sie zum Ausführen der App die F5-TASTE.</span><span class="sxs-lookup"><span data-stu-id="8d207-324">To run the app, choose the F5 key.</span></span> <span data-ttu-id="8d207-325">Wählen Sie zum Starten des asynchronen Vorgangs die Schaltfläche **Async** aus.</span><span class="sxs-lookup"><span data-stu-id="8d207-325">To start the asynchronous operation, choose the **Async** button.</span></span> <span data-ttu-id="8d207-326">Was als Nächstes passiert, hängt von der Geschwindigkeit des Computers ab.</span><span class="sxs-lookup"><span data-stu-id="8d207-326">What happens next depends on how fast your computer is.</span></span> <span data-ttu-id="8d207-327">Wenn die Statusleiste den Abschluss erreicht, bevor Sie auch nur blinzeln können, erhöhen Sie die Startzahl, die an „GetPrimesInRangeAsync“ übergeben wird, um den Faktor zehn oder ein Vielfaches davon.</span><span class="sxs-lookup"><span data-stu-id="8d207-327">If the progress bar zips to completion before you have time to blink, increase the size of the starting number that is passed to GetPrimesInRangeAsync by one or more factors of ten.</span></span> <span data-ttu-id="8d207-328">Sie können die Dauer des Vorgangs optimieren, indem Sie die Anzahl der Testzahlen erhöhen oder verringern, allerdings hat das Hinzufügen von Nullen (0) in der Mitte der Startzahl einen größeren Einfluss.</span><span class="sxs-lookup"><span data-stu-id="8d207-328">You can fine-tune the duration of the operation by increasing or decreasing the count of numbers to test, but adding zeros in the middle of the starting number will have a bigger impact.</span></span> <span data-ttu-id="8d207-329">Um den Vorgang abzubrechen, wählen Sie die Schaltfläche **Cancel Async** aus.</span><span class="sxs-lookup"><span data-stu-id="8d207-329">To cancel the operation, choose the **Cancel Async** button.</span></span>

## <a name="related-topics"></a><span data-ttu-id="8d207-330">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="8d207-330">Related topics</span></span>

* [<span data-ttu-id="8d207-331">.NET für UWP-apps-Übersicht</span><span class="sxs-lookup"><span data-stu-id="8d207-331">.NET for UWP apps Overview</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/br230302.aspx)
* [<span data-ttu-id="8d207-332">.NET für UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="8d207-332">.NET for UWP apps</span></span>](https://msdn.microsoft.com/library/windows/apps/xaml/mt185501.aspx)
* [<span data-ttu-id="8d207-333">Exemplarische Vorgehensweise: Erstellen einer einfachen Komponente für Windows-Runtime und Aufrufen der Komponente über JavaScript</span><span class="sxs-lookup"><span data-stu-id="8d207-333">Walkthrough: Creating a Simple Windows Runtime Component and calling it from JavaScript</span></span>](walkthrough-creating-a-simple-windows-runtime-component-and-calling-it-from-javascript.md)
