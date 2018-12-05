---
title: Auswählen einer Programmiersprache
ms.assetid: 6CA46432-BF03-4B20-9187-565B3503B497
description: Auswählen einer Programmiersprache
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: a9544c1eecc4c1a86552d053694872743a17142c
ms.sourcegitcommit: d7613c791107f74b6a3dc12a372d9de916c0454b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2018
ms.locfileid: "8734596"
---
# <a name="getting-started-choosing-a-programming-language"></a><span data-ttu-id="d4a52-104">Erste Schritte: Auswählen einer Programmiersprache</span><span class="sxs-lookup"><span data-stu-id="d4a52-104">Getting started: Choosing a programming language</span></span>


## <a name="choosing-a-programming-language"></a><span data-ttu-id="d4a52-105">Auswählen einer Programmiersprache</span><span class="sxs-lookup"><span data-stu-id="d4a52-105">Choosing a programming language</span></span>

<span data-ttu-id="d4a52-106">Bevor wir weiter ins Detail gehen, sollten Sie die Programmiersprachen kennen, die Ihnen bei der Entwicklung von universellen Windows-Plattform-Apps (UWP) zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="d4a52-106">Before we go any further, you should know about the programming languages that you can choose from when you develop Universal Windows Platform (UWP) apps.</span></span> <span data-ttu-id="d4a52-107">Obwohl bei der exemplarischen Vorgehensweise in diesem Artikel C# verwendet wird, können Sie UWP-Apps ggf. mit mehreren Programmiersprachen entwickeln (siehe [Sprachen, Tools und Frameworks](https://msdn.microsoft.com/library/windows/apps/dn465799)).</span><span class="sxs-lookup"><span data-stu-id="d4a52-107">Although the walkthroughs in this article use C#, you can develop UWP apps using one or more programming languages (see [Languages, tools and frameworks](https://msdn.microsoft.com/library/windows/apps/dn465799)).</span></span>

<span data-ttu-id="d4a52-108">UWP-Apps können mit C++, C#, Microsoft Visual Basic und JavaScript entwickelt werden.</span><span class="sxs-lookup"><span data-stu-id="d4a52-108">You can develop using C++, C#, Microsoft Visual Basic, and JavaScript.</span></span> <span data-ttu-id="d4a52-109">JavaScript verwendet HTML5-Markup für das Benutzeroberflächenlayout, und andere Programmiersprachen verwenden die Markupsprache *Extensible Application Markup Language (XAML)* für die Beschreibung der Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="d4a52-109">JavaScript uses HTML5 markup for UI layout, and the other languages use a markup language called *Extensible Application Markup Language (XAML)* to describe their UI.</span></span>

<span data-ttu-id="d4a52-110">Obwohl wir uns in diesem Artikel auf C# konzentrieren, bieten die restlichen Sprachen ebenfalls klare Vorteile, die Sie kennen sollten.</span><span class="sxs-lookup"><span data-stu-id="d4a52-110">Although we're focusing on C# in this article, the other languages offer unique benefits, which you may want to explore.</span></span> <span data-ttu-id="d4a52-111">Wenn Sie bei der App beispielsweise in erster Linie Wert auf die Leistung legen, ist C++ möglicherweise die richtige Wahl (insbesondere bei einer aufwändigen Grafik).</span><span class="sxs-lookup"><span data-stu-id="d4a52-111">For example, if your app's performance is a primary concern, especially for intensive graphics, then C++ might be the right choice.</span></span> <span data-ttu-id="d4a52-112">Die Microsoft .NET-Version von Visual Basic ist hervorragend für Visual Basic-App-Entwickler geeignet.</span><span class="sxs-lookup"><span data-stu-id="d4a52-112">The Microsoft .NET version of Visual Basic is great for Visual Basic app developers.</span></span> <span data-ttu-id="d4a52-113">JavaScript mit HTML5 ist eine gute Wahl für Entwickler mit Webentwicklungshintergrund.</span><span class="sxs-lookup"><span data-stu-id="d4a52-113">JavaScript with HTML5 is great for those coming from a web development background.</span></span> <span data-ttu-id="d4a52-114">Weitere Informationen finden Sie unter einem der folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="d4a52-114">For more info, see one of the following:</span></span>

-   [<span data-ttu-id="d4a52-115">Erstellen Sie Ihrer ersten UWP-app mit C++</span><span class="sxs-lookup"><span data-stu-id="d4a52-115">Create your first UWP app using C++</span></span>](../get-started/create-a-basic-windows-10-app-in-cpp.md)
-   [<span data-ttu-id="d4a52-116">Erstellen Sie Ihrer ersten UWP-app mit c# oder Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d4a52-116">Create your first UWP app using C# or Visual Basic</span></span>](../get-started/create-a-hello-world-app-xaml-universal.md)
-   [<span data-ttu-id="d4a52-117">Erstellen Sie Ihrer ersten UWP-app mit JavaScript</span><span class="sxs-lookup"><span data-stu-id="d4a52-117">Create your first UWP app using JavaScript</span></span>](../get-started/create-a-hello-world-app-js-uwp.md)

<span data-ttu-id="d4a52-118">**Hinweis:** für apps mit 3D-Grafiken die Standards OpenGL und OpenGL ES sind nicht nativ verfügbar für UWP-apps.</span><span class="sxs-lookup"><span data-stu-id="d4a52-118">**Note**For apps that use 3D graphics, the OpenGL and OpenGL ES standards are not natively available for UWP apps.</span></span> <span data-ttu-id="d4a52-119">Wenn Sie Ihren OpenGL ES-Code in Microsoft DirectX nicht neu schreiben möchten, könnte **Angle** von Interesse für Sie sein.</span><span class="sxs-lookup"><span data-stu-id="d4a52-119">If you would rather not rewrite your OpenGL ES code into Microsoft DirectX, you may be interested to know about **Angle**.</span></span> <span data-ttu-id="d4a52-120">Angle ist ein laufendes Projekt, das zum Konvertieren von OpenGL in DirectX entwickelt wurde, indem OpenGL-API-Aufrufe in DirectX-API-Aufrufe übersetzt werden.</span><span class="sxs-lookup"><span data-stu-id="d4a52-120">Angle is an on-going project designed to convert OpenGL to DirectX by translating OpenGL API calls into DirectX API calls.</span></span> <span data-ttu-id="d4a52-121">Weitere Informationen hierzu finden Sie unter den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="d4a52-121">To learn more, see the following:</span></span>
-   [<span data-ttu-id="d4a52-122">Angle</span><span class="sxs-lookup"><span data-stu-id="d4a52-122">Angle</span></span>](https://code.google.com/p/angleproject/)
-   [<span data-ttu-id="d4a52-123">Erstellen Sie Ihrer ersten UWP-app mit DirectX</span><span class="sxs-lookup"><span data-stu-id="d4a52-123">Create your first UWP app using DirectX</span></span>](https://msdn.microsoft.com/library/windows/apps/br229580)
-   [<span data-ttu-id="d4a52-124">Beispiele für UWP-Apps, die DirectX nutzen</span><span class="sxs-lookup"><span data-stu-id="d4a52-124">UWP app samples that use DirectX</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=263603)
-   [<span data-ttu-id="d4a52-125">Wo finde ich das DirectX SDK?</span><span class="sxs-lookup"><span data-stu-id="d4a52-125">Where is the DirectX SDK?</span></span>](https://msdn.microsoft.com/library/windows/desktop/ee663275)

## <a name="giving-c-a-go"></a><span data-ttu-id="d4a52-126">Testen von C#</span><span class="sxs-lookup"><span data-stu-id="d4a52-126">Giving C# a go</span></span>

<span data-ttu-id="d4a52-127">Als iOS-Entwickler sind Sie die Arbeit mit Objective-C und Swift gewohnt.</span><span class="sxs-lookup"><span data-stu-id="d4a52-127">As an iOS developer, you're accustomed to Objective-C and Swift.</span></span> <span data-ttu-id="d4a52-128">C# ist die Microsoft-Programmiersprache, die beiden am ähnlichsten ist.</span><span class="sxs-lookup"><span data-stu-id="d4a52-128">The closest Microsoft programming language to both is C#.</span></span> <span data-ttu-id="d4a52-129">Unserer Meinung nach ist C# für die meisten Entwickler und die meisten Apps die Sprache, die am einfachsten und schnellsten erlernbar ist. Daher liegt der Schwerpunkt der Informationen und exemplarischen Vorgehensweisen in diesem Artikel auf dieser Sprache.</span><span class="sxs-lookup"><span data-stu-id="d4a52-129">For most developers and most apps, we think C# is the easiest and fastest language to learn and use, so this article's info and walkthroughs focus on that language.</span></span> <span data-ttu-id="d4a52-130">Weitere Informationen zu C# finden Sie unter den folgenden Themen:</span><span class="sxs-lookup"><span data-stu-id="d4a52-130">To learn more about C#, see the following:</span></span>

-   [<span data-ttu-id="d4a52-131">Erstellen Sie Ihrer ersten UWP-app mit c# oder Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d4a52-131">Create your first UWP app using C# or Visual Basic</span></span>](../get-started/create-a-hello-world-app-xaml-universal.md)
-   [<span data-ttu-id="d4a52-132">Beispiele für UWP-Apps, die Verwendung von c#</span><span class="sxs-lookup"><span data-stu-id="d4a52-132">UWP app samples that use C#</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=263453)
-   [<span data-ttu-id="d4a52-133">Visual C#-</span><span class="sxs-lookup"><span data-stu-id="d4a52-133">Visual C#</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=263450)

<span data-ttu-id="d4a52-134">Es folgt ein Vergleich einer Klasse, die sowohl in Objective-C als auch in C# geschrieben wurde.</span><span class="sxs-lookup"><span data-stu-id="d4a52-134">Following is a class written in Objective-C and C#.</span></span> <span data-ttu-id="d4a52-135">Die Objective-C-Version wird zuerst dargestellt. Die C#-Version folgt danach.</span><span class="sxs-lookup"><span data-stu-id="d4a52-135">The Objective-C version is shown first, followed by the C# version.</span></span>

```obj-c
// Objective-C header: SampleClass.h.

#import <Foundation/Foundation.h>

@interface SampleClass : NSObject {
    BOOL localVariable;
}

@property (nonatomic) BOOL localVariable;

-(int) addThis: (int) firstNumber andThis: (int) secondNumber;

@end
```

```obj-c
// Objective-C implementation.

#import "SampleClass.h"

@implementation SampleClass

@synthesize localVariable = _localVariable;

- (id)init {
    self = [super init];
    if (self) {
        localVariable = true;
    }
    return self;
}

-(int) addThis: (int) firstNumber andThis: (int) secondNumber {
    return firstNumber + secondNumber;
}

@end
```

```obj-c
// Objective-C usage.

SampleClass *mySampleClass = [[SampleClass alloc] init];
mySampleClass.localVariable = false;
int result = [mySampleClass addThis:1 andThis:2];
```

<span data-ttu-id="d4a52-136">Nun die C#-Version.</span><span class="sxs-lookup"><span data-stu-id="d4a52-136">Now, for the C# version.</span></span> <span data-ttu-id="d4a52-137">Wie Sie sehen, befinden sich Header und Implementierung, wie auch bei Swift, nicht in separaten Dateien.</span><span class="sxs-lookup"><span data-stu-id="d4a52-137">You'll see that like Swift, the header and the implementation are not in separate files.</span></span>

```csharp
// C# header and implementation.

using System;

namespace MyApp  // Defines this code' s scope.
{
    class SampleClass
    {
        private bool localVariable;

        public SampleClass() // Constructor.
        {
            localVariable = true;
        }

        public bool myLocalVariable // Property.
        {
            get
            {
                return localVariable;
            }
            set
            {
                localVariable = value; 
            }
        }

        public int AddTwoNumbers(int numberOne, int numberTwo)
        {
            return numberOne + numberTwo;
        }        
    }
}
```

```csharp
// C# usage.

SampleClass mySampleClass = new SampleClass();
mySampleClass.myLocalVariable = false;
int result = mySampleClass.AddTwoNumbers(1, 2);
```

<span data-ttu-id="d4a52-138">C# ist eine einfach erlernbare Sprache und verfügt über viele Unterstützungsklassen und Frameworks, die .NET ausmachen.</span><span class="sxs-lookup"><span data-stu-id="d4a52-138">C# is an easy language to pick up, and comes with the many support classes and frameworks that make up .NET.</span></span> <span data-ttu-id="d4a52-139">Sie werden in kürzester Zeit problemlos Ihren Code ohne eine eckige Klammer schreiben können!</span><span class="sxs-lookup"><span data-stu-id="d4a52-139">In no time, you'll be happily writing your code without a square bracket in sight!</span></span>

## <a name="next-step"></a><span data-ttu-id="d4a52-140">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="d4a52-140">Next step</span></span>

[<span data-ttu-id="d4a52-141">Erste Schritte: Aufbau von Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d4a52-141">Getting started: Getting around in Visual Studio</span></span>](getting-started-getting-around-in-visual-studio.md)
