---
author: Jwmsft
ms.assetid: 90F07341-01F4-4205-8161-92DD2EB49860
title: 3D-Perspektiveneffekte für XAML-UI
description: Mithilfe der perspektivischen Transformation können Sie 3D-Effekte auf Inhalte in Ihren Windows-Runtime-Apps anwenden. Sie können z. B. die Illusion schaffen, dass sich ein Objekt auf Sie zu oder von Ihnen wegbewegt, wie hier gezeigt wird.
ms.author: jimwalk
ms.date: 02/08/2017
ms.topic: article
keywords: Windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: f0b50ca4cb3f74c7c8e8bccb4fceb58e0151bcf2
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5869939"
---
# <a name="3-d-perspective-effects-for-xaml-ui"></a><span data-ttu-id="48230-105">3D-Perspektiveneffekte für XAML-UI</span><span class="sxs-lookup"><span data-stu-id="48230-105">3-D perspective effects for XAML UI</span></span>


<span data-ttu-id="48230-106">Mithilfe der perspektivischen Transformation können Sie 3D-Effekte auf Inhalte in Ihren Windows-Runtime-Apps anwenden.</span><span class="sxs-lookup"><span data-stu-id="48230-106">You can apply 3-D effects to content in your Windows Runtime apps using perspective transforms.</span></span> <span data-ttu-id="48230-107">Sie können z.B. wie hier gezeigt die Illusion schaffen, dass sich ein Objekt auf Sie zu oder von Ihnen wegbewegt.</span><span class="sxs-lookup"><span data-stu-id="48230-107">For example, you can create the illusion that an object is rotated toward or away from you, as shown here.</span></span>

![Bild mit perspektivischer Transformation](images/3dsimple.png)

<span data-ttu-id="48230-109">Eine weitere häufige Anwendung von perspektivischen Transformationen besteht in der Anordnung von Objekten relativ zueinander, wodurch wie hier ein 3D-Effekt erzeugt wird.</span><span class="sxs-lookup"><span data-stu-id="48230-109">Another common usage for perspective transforms is to arrange objects in relation to one another to create a 3-D effect, as here.</span></span>

![Stapeln von Objekten zum Erzeugen eines 3D-Effekts](images/3dstacking.png)

<span data-ttu-id="48230-111">Neben dem Erzeugen von statischen 3D-Effekten können Sie die Eigenschaften der perspektivischen Transformation animieren, um 3D-Bewegungseffekte zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="48230-111">Besides creating static 3-D effects, you can animate the perspective transform properties to create moving 3-D effects.</span></span>

<span data-ttu-id="48230-112">Sie haben sich soeben damit vertraut gemacht, wie perspektivische Transformationen auf Bilder angewendet werden. Sie können diese Effekte jedoch auf jedes [**UIElement**](https://msdn.microsoft.com/library/windows/apps/BR208911) anwenden, einschließlich von Steuerelementen.</span><span class="sxs-lookup"><span data-stu-id="48230-112">You just saw perspective transforms applied to images, but you can apply these effects to any [**UIElement**](https://msdn.microsoft.com/library/windows/apps/BR208911), including controls.</span></span> <span data-ttu-id="48230-113">Sie können beispielsweise wie folgt einen 3D-Effekt auf einen ganzen Container von Steuerelementen anwenden:</span><span class="sxs-lookup"><span data-stu-id="48230-113">For example, you can apply a 3-D effect to an entire container of controls like this:</span></span>

![Auf einen Container von Elementen angewendeter 3D-Effekt](images/skewedstackpanel.png)

<span data-ttu-id="48230-115">Dieses Beispiel wurde mit folgendem XAML-Code erstellt:</span><span class="sxs-lookup"><span data-stu-id="48230-115">Here is the XAML code used to create this sample:</span></span>

```xml
<StackPanel Margin="35" Background="Gray">    
    <StackPanel.Projection>        
        <PlaneProjection RotationX="-35" RotationY="-35" RotationZ="15"  />    
    </StackPanel.Projection>    
    <TextBlock Margin="10">Type Something Below</TextBlock>    
    <TextBox Margin="10"></TextBox>    
    <Button Margin="10" Content="Click" Width="100" />
</StackPanel>
```

<span data-ttu-id="48230-116">Wenden Sie sich nun den Eigenschaften von [**PlaneProjection**](https://msdn.microsoft.com/library/windows/apps/BR210192) zu. Damit werden Objekte im 3D-Raum gedreht und bewegt.</span><span class="sxs-lookup"><span data-stu-id="48230-116">Here we focus on the properties of [**PlaneProjection**](https://msdn.microsoft.com/library/windows/apps/BR210192) which is used to rotate and move objects in 3-D space.</span></span> <span data-ttu-id="48230-117">Im folgenden Beispiel können Sie mit den Eigenschaften experimentieren und feststellen, wie sie sich auf ein Objekt auswirken.</span><span class="sxs-lookup"><span data-stu-id="48230-117">The next sample allows you to experiment with these properties and see their effect on an object.</span></span>

## <a name="planeprojection-class"></a><span data-ttu-id="48230-118">PlaneProjection-Klasse</span><span class="sxs-lookup"><span data-stu-id="48230-118">PlaneProjection class</span></span>

<span data-ttu-id="48230-119">Sie können 3D-Effekte auf jedes [**UIElement**](https://msdn.microsoft.com/library/windows/apps/BR208911) anwenden. Dazu legen Sie die [**Projection**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.projection)-Eigenschaft für das UIElement mit einer [**PlaneProjection**](https://msdn.microsoft.com/library/windows/apps/BR210192) fest.</span><span class="sxs-lookup"><span data-stu-id="48230-119">You can apply 3D effects can to any [**UIElement**](https://msdn.microsoft.com/library/windows/apps/BR208911), by setting the UIElement's [**Projection**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.uielement.projection) property using a [**PlaneProjection**](https://msdn.microsoft.com/library/windows/apps/BR210192).</span></span> <span data-ttu-id="48230-120">Die **PlaneProjection** definiert, wie die Transformation im Raum gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="48230-120">The **PlaneProjection** defines how the transform is rendered in space.</span></span> <span data-ttu-id="48230-121">Im nächsten Beispiel wird ein einfacher Fall veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="48230-121">The next example shows a simple case.</span></span>

```xml
<Image Source="kid.png">
    <Image.Projection>
        <PlaneProjection RotationX="-35"   />
    </Image.Projection>
</Image>
```

<span data-ttu-id="48230-122">Die Abbildung zeigt, wie das Bild gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="48230-122">This figure shows what the image renders as.</span></span> <span data-ttu-id="48230-123">Die X-Achse, die Y-Achse und die Z-Achse sind als rote Linien dargestellt.</span><span class="sxs-lookup"><span data-stu-id="48230-123">The x-axis, y-axis, and z-axis are shown as red lines.</span></span> <span data-ttu-id="48230-124">Das Bild wird mit der [**RotationX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.rotationx)-Eigenschaft um 35 Grad um die X-Achse rückwärts gedreht.</span><span class="sxs-lookup"><span data-stu-id="48230-124">The image is rotated backward 35 degrees around the x-axis using the [**RotationX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.rotationx) property.</span></span>

![RotateX minus 35 Grad](images/3drotatexminus35.png)

<span data-ttu-id="48230-126">Die [**RotationY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.rotationy)-Eigenschaft führt eine Drehung um die Y-Achse des Drehmittelpunkts aus.</span><span class="sxs-lookup"><span data-stu-id="48230-126">The [**RotationY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.rotationy) property rotates around the y-axis of the center of rotation.</span></span>

```xml
<Image Source="kid.png">
    <Image.Projection>
        <PlaneProjection RotationY="-35"   />
    </Image.Projection>
</Image>
```

![RotateY minus 35 Grad](images/3drotateyminus35.png)

<span data-ttu-id="48230-128">Die [**RotationZ**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.rotationz)-Eigenschaft führt eine Drehung um die Z-Achse des Drehmittelpunkts aus (eine Linie, die eine Senkrechte zur Objektfläche darstellt).</span><span class="sxs-lookup"><span data-stu-id="48230-128">The [**RotationZ**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.rotationz) property rotates around the z-axis of the center of rotation (a line that is perpendicular to the plane of the object).</span></span>

```xml
<Image Source="kid.png">
    <Image.Projection>
        <PlaneProjection RotationZ="-45"/>
    </Image.Projection>
</Image>
```

![RotateZ minus 45Grad](images/3drotatezminus35.png)

<span data-ttu-id="48230-130">Für die Drehungseigenschaften kann ein positiver oder negativer Wert für die Drehung in beiden Richtungen angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="48230-130">The rotation properties can specify a positive or negative value to rotate in either direction.</span></span> <span data-ttu-id="48230-131">Die absolute Zahl kann größer als 360 sein, wodurch das Objekt um mehr als eine volle Drehung gedreht wird.</span><span class="sxs-lookup"><span data-stu-id="48230-131">The absolute number can be greater than 360, which rotates the object more than one full rotation.</span></span>

<span data-ttu-id="48230-132">Sie können den Drehmittelpunkt mithilfe der Eigenschaften [**CenterOfRotationX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.centerofrotationx), [**CenterOfRotationY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.centerofrotationy) und [**CenterOfRotationZ**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.centerofrotationz) verschieben.</span><span class="sxs-lookup"><span data-stu-id="48230-132">You can move the center of rotation by using the [**CenterOfRotationX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.centerofrotationx), [**CenterOfRotationY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.centerofrotationy), and [**CenterOfRotationZ**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.centerofrotationz) properties.</span></span> <span data-ttu-id="48230-133">Standardmäßig verläuft die Drehachse direkt durch den Objektmittelpunkt, wodurch das Objekt um seinen Mittelpunkt gedreht wird.</span><span class="sxs-lookup"><span data-stu-id="48230-133">By default, the axes of rotation run directly through the center of the object, causing the object to rotate around its center.</span></span> <span data-ttu-id="48230-134">Wenn Sie jedoch den Drehmittelpunkt an den Rand des Objekts verschieben, wird das Objekt um den betreffenden Rand gedreht.</span><span class="sxs-lookup"><span data-stu-id="48230-134">But if you move the center of rotation to the outer edge of the object, it will rotate around that edge.</span></span> <span data-ttu-id="48230-135">Der Standardwert für **CenterOfRotationX** und **CenterOfRotationY** ist 0,5, und der Standardwert für **CenterOfRotationZ** ist 0.</span><span class="sxs-lookup"><span data-stu-id="48230-135">The default values for **CenterOfRotationX** and **CenterOfRotationY** are 0.5, and the default value for **CenterOfRotationZ** is 0.</span></span> <span data-ttu-id="48230-136">Für **CenterOfRotationX** und **CenterOfRotationY** wird der Drehpunkt mit Werten zwischen 0 und 1 auf eine bestimmte Position auf dem Objekt festgelegt.</span><span class="sxs-lookup"><span data-stu-id="48230-136">For **CenterOfRotationX** and **CenterOfRotationY**, values between 0 and 1 set the pivot point at some location within the object.</span></span> <span data-ttu-id="48230-137">Durch den Wert "0" wird ein Rand des Objekts angegeben, während mit dem Wert "1" der gegenüberliegende Rand angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="48230-137">A value of 0 denotes one object edge and 1 denotes the opposite edge.</span></span> <span data-ttu-id="48230-138">Werte außerhalb dieses Bereichs sind zulässig, und der Drehmittelpunkt wird entsprechend verschoben.</span><span class="sxs-lookup"><span data-stu-id="48230-138">Values outside of this range are allowed and will move the center of rotation accordingly.</span></span> <span data-ttu-id="48230-139">Da die Z-Achse des Drehmittelpunkts durch die Fläche des Objekts gezeichnet wird, können Sie den Drehmittelpunkt mit einer negativen Zahl hinter das Objekt und mit einer positiven Zahl vor das Objekt (auf den Betrachter zu) verschieben.</span><span class="sxs-lookup"><span data-stu-id="48230-139">Because the z-axis of the center of rotation is drawn through the plane of the object, you can move the center of rotation behind the object using a negative number and in front of the object (toward you) using a positive number.</span></span>

<span data-ttu-id="48230-140">[**CenterOfRotationX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.centerofrotationx) verschiebt den Drehmittelpunkt entlang der X-Achse parallel zum Objekt, während [**CenterOfRotationY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.centerofrotationy) den Drehmittelpunkt entlang der Y-Achse des Objekts verschiebt.</span><span class="sxs-lookup"><span data-stu-id="48230-140">[**CenterOfRotationX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.centerofrotationx) moves the center of rotation along the x-axis parallel to the object while [**CenterOfRotationY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.centerofrotationy) moves the center or rotation along the y-axis of the object.</span></span> <span data-ttu-id="48230-141">In der folgenden Abbildung wird die Auswirkung von verschiedenen Werten für **CenterOfRotationY** veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="48230-141">The next illustrations demonstrate using different values for **CenterOfRotationY**.</span></span>

```xml
<Image Source="kid.png">
    <Image.Projection>
        <PlaneProjection RotationX="-35" CenterOfRotationY="0.5" />
    </Image.Projection>
</Image>
```

**<span data-ttu-id="48230-142">CenterOfRotationY = "0,5" (Standardeinstellung)</span><span class="sxs-lookup"><span data-stu-id="48230-142">CenterOfRotationY = "0.5" (default)</span></span>**

![CenterOfRotationY ist "0,5"](images/3drotatexminus35.png)
```xml
<Image Source="kid.png">
    <Image.Projection>
        <PlaneProjection RotationX="-35" CenterOfRotationY="0.1"/>
    </Image.Projection>
</Image>
```

**<span data-ttu-id="48230-144">CenterOfRotationY = "0,1"</span><span class="sxs-lookup"><span data-stu-id="48230-144">CenterOfRotationY = "0.1"</span></span>**

![CenterOfRotationY ist "0,1"](images/3dcenterofrotationy0point1.png)

<span data-ttu-id="48230-146">Beachten Sie, wie das Bild um den Mittelpunkt gedreht wird, wenn die [**CenterOfRotationY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.centerofrotationy)-Eigenschaft auf den Standardwert "0,5" festgelegt ist. Es wird nahe seinem oberen Rand gedreht, wenn die Eigenschaft auf "0,1" festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="48230-146">Notice how the image rotates around the center when the [**CenterOfRotationY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.centerofrotationy) property is set to the default value of 0.5 and rotates near the upper edge when set to 0.1.</span></span> <span data-ttu-id="48230-147">Ein ähnliches Verhalten ist zu beobachten, wenn die [**CenterOfRotationX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.centerofrotationx)-Eigenschaft geändert wird, um eine Verschiebung zu bewirken, wobei das Objekt durch die [**RotationY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.rotationy)-Eigenschaft gedreht wird.</span><span class="sxs-lookup"><span data-stu-id="48230-147">You see similar behavior when changing the [**CenterOfRotationX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.centerofrotationx) property to move where the [**RotationY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.rotationy) property rotates the object.</span></span>

```xml
<Image Source="kid.png">
    <Image.Projection>
        <PlaneProjection RotationY="-35" CenterOfRotationX="0.5" />
    </Image.Projection>
</Image>
```

**<span data-ttu-id="48230-148">CenterOfRotationX = "0,5" (Standardeinstellung)</span><span class="sxs-lookup"><span data-stu-id="48230-148">CenterOfRotationX = "0.5" (default)</span></span>**

![CenterOfRotationX ist "0,5"](images/3drotateyminus35.png)
```xml
<Image Source="kid.png">
    <Image.Projection>
        <PlaneProjection RotationY="-35" CenterOfRotationX="0.5" />
    </Image.Projection>
</Image>
```

**<span data-ttu-id="48230-150">CenterOfRotationX = "0,9" (rechter Rand)</span><span class="sxs-lookup"><span data-stu-id="48230-150">CenterOfRotationX = "0.9" (right-hand edge)</span></span>**

![CenterOfRotationX ist "0,9"](images/3dcenterofrotationx0point9.png)

<span data-ttu-id="48230-152">Platzieren Sie den Drehmittelpunkt mithilfe von [**CenterOfRotationZ**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.centerofrotationz) über bzw. unter der Fläche des Objekts.</span><span class="sxs-lookup"><span data-stu-id="48230-152">Use the [**CenterOfRotationZ**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.centerofrotationz) to place the center of rotation above or below the plane of the object.</span></span> <span data-ttu-id="48230-153">Auf diese Weise können Sie das Objekt wie einen Planeten auf seiner Umlaufbahn um einen Stern um den betreffenden Punkt drehen.</span><span class="sxs-lookup"><span data-stu-id="48230-153">This way, you can rotate the object around the point analogous to a planet orbiting around a star.</span></span>

## <a name="positioning-an-object"></a><span data-ttu-id="48230-154">Positionieren eines Objekts</span><span class="sxs-lookup"><span data-stu-id="48230-154">Positioning an object</span></span>

<span data-ttu-id="48230-155">Sie haben nun erfahren, wie Sie ein Objekt im Raum drehen können.</span><span class="sxs-lookup"><span data-stu-id="48230-155">So far, you learned how to rotate an object in space.</span></span> <span data-ttu-id="48230-156">Mit den folgenden Eigenschaften können Sie diese gedrehten Objekte relativ zueinander im Raum positionieren:</span><span class="sxs-lookup"><span data-stu-id="48230-156">You can position these rotated objects in space relative to one another by using these properties:</span></span>

-   <span data-ttu-id="48230-157">[**LocalOffsetX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.localoffsetx) verschiebt ein Objekt entlang der X-Achse der Fläche eines gedrehten Objekts.</span><span class="sxs-lookup"><span data-stu-id="48230-157">[**LocalOffsetX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.localoffsetx) moves an object along the x-axis of the plane of a rotated object.</span></span>
-   <span data-ttu-id="48230-158">[**LocalOffsetY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.localoffsety) verschiebt ein Objekt entlang der Y-Achse der Fläche eines gedrehten Objekts.</span><span class="sxs-lookup"><span data-stu-id="48230-158">[**LocalOffsetY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.localoffsety) moves an object along the y-axis of the plane of a rotated object.</span></span>
-   <span data-ttu-id="48230-159">[**LocalOffsetZ**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.localoffsetz) verschiebt ein Objekt entlang der Z-Achse der Fläche eines gedrehten Objekts.</span><span class="sxs-lookup"><span data-stu-id="48230-159">[**LocalOffsetZ**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.localoffsetz) moves an object along the z-axis of the plane of a rotated object.</span></span>
-   <span data-ttu-id="48230-160">[**GlobalOffsetX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.globaloffsetx) verschiebt ein Objekt entlang der am Bildschirm ausgerichteten X-Achse.</span><span class="sxs-lookup"><span data-stu-id="48230-160">[**GlobalOffsetX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.globaloffsetx) moves an object along the screen-aligned x-axis.</span></span>
-   <span data-ttu-id="48230-161">[**GlobalOffsetY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.globaloffsety) verschiebt ein Objekt entlang der am Bildschirm ausgerichteten Y-Achse.</span><span class="sxs-lookup"><span data-stu-id="48230-161">[**GlobalOffsetY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.globaloffsety) moves an object along the screen-aligned y-axis.</span></span>
-   <span data-ttu-id="48230-162">[**GlobalOffsetZ**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.globaloffsetz) verschiebt ein Objekt entlang der am Bildschirm ausgerichteten Z-Achse.</span><span class="sxs-lookup"><span data-stu-id="48230-162">[**GlobalOffsetZ**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.globaloffsetz) moves an object along the screen-aligned z-axis.</span></span>

**<span data-ttu-id="48230-163">Lokaler Versatz</span><span class="sxs-lookup"><span data-stu-id="48230-163">Local offset</span></span>**

<span data-ttu-id="48230-164">Die Eigenschaften [**LocalOffsetX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.localoffsetx), [**LocalOffsetY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.localoffsety) und [**LocalOffsetZ**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.localoffsetz) versetzen ein Objekt entlang der entsprechenden Achse der Fläche des Objekts, nachdem dieses gedreht wurde.</span><span class="sxs-lookup"><span data-stu-id="48230-164">The [**LocalOffsetX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.localoffsetx), [**LocalOffsetY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.localoffsety), and [**LocalOffsetZ**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.localoffsetz) properties translate an object along the respective axis of the plane of the object after it has been rotated.</span></span> <span data-ttu-id="48230-165">Daher bestimmt die Drehung des Objekts die Richtung, in die das Objekt versetzt wird.</span><span class="sxs-lookup"><span data-stu-id="48230-165">Therefore, the rotation of the object determines the direction that the object is translated.</span></span> <span data-ttu-id="48230-166">Zum Verdeutlichen dieses Konzepts wird im folgenden Beispiel **LocalOffsetX** von 0 bis 400 Grad animiert, und [**RotationY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.rotationy) wird von 0 bis 65 Grad animiert.</span><span class="sxs-lookup"><span data-stu-id="48230-166">To demonstrate this concept, the next sample animates **LocalOffsetX** from 0 to 400 and [**RotationY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.rotationy) from 0 to 65 degrees.</span></span>

<span data-ttu-id="48230-167">Im vorigen Beispiel ist zu beobachten, dass das Objekt entlang seiner eigenen X-Achse verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="48230-167">Notice in the preceding sample that the object is moving along its own x-axis.</span></span> <span data-ttu-id="48230-168">Das Objekt wird gleich zu Beginn der Animation, wenn der Wert von [**RotationY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.rotationy) nahe null liegt (d. h. parallel zum Bildschirm), entlang des Bildschirms in der X-Richtung verschoben. Während das Objekt jedoch in Richtung des Betrachters gedreht wird, erfolgt eine Verschiebung entlang der X-Achse der Objektfläche in Richtung Betrachter.</span><span class="sxs-lookup"><span data-stu-id="48230-168">At the very beginning of the animation, when the [**RotationY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.rotationy) value is near zero (parallel to the screen), the object moves along the screen in the x direction, but as the object rotates toward you, the object moves along the x-axis of the plane of the object toward you.</span></span> <span data-ttu-id="48230-169">Wenn Sie die **RotationY**-Eigenschaft jedoch mit einem Wert von -65 Grad animiert haben, wird das Objekt in einer Kurvenbewegung vom Betrachter weg gedreht.</span><span class="sxs-lookup"><span data-stu-id="48230-169">On the other hand, if you animated the **RotationY** property to -65 degrees, the object would curve away from you.</span></span>

<span data-ttu-id="48230-170">[**LocalOffsetY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.localoffsety) funktioniert ähnlich wie [**LocalOffsetX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.localoffsetx), die Bewegung erfolgt jedoch entlang der vertikalen Achse. Eine Änderung von [**RotationX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.rotationx) wirkt sich daher auf die Richtung aus, in der **LocalOffsetY** das Objekt verschiebt.</span><span class="sxs-lookup"><span data-stu-id="48230-170">[**LocalOffsetY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.localoffsety) works similarly to [**LocalOffsetX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.localoffsetx), except that it moves along the vertical axis, so changing [**RotationX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.rotationx) affects the direction **LocalOffsetY** moves the object.</span></span> <span data-ttu-id="48230-171">Im nächsten Beispiel wird **LocalOffsetY** von 0 bis 400 Grad animiert, und **RotationX** wird von 0 bis 65 Grad animiert.</span><span class="sxs-lookup"><span data-stu-id="48230-171">In the next sample, **LocalOffsetY** is animated from 0 to 400 and **RotationX** from 0 to 65 degrees.</span></span>

<span data-ttu-id="48230-172">[**LocalOffsetZ**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.localoffsetz) versetzt das Objekt senkrecht zur Fläche des Objekts, als ob durch den Mittelpunkt an der Objektrückseite ein Vektor direkt in Richtung des Betrachters gezeichnet würde.</span><span class="sxs-lookup"><span data-stu-id="48230-172">[**LocalOffsetZ**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.localoffsetz) translates the object perpendicular to the plane of the object as though a vector was drawn directly through the center from behind the object out toward you.</span></span> <span data-ttu-id="48230-173">Zum Veranschaulichen der Funktionsweise von **LocalOffsetZ** wird im folgenden Beispiel **LocalOffsetZ** von 0 bis 400 Grad animiert, und [**RotationX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.rotationx) wird von 0 bis 65 Grad animiert.</span><span class="sxs-lookup"><span data-stu-id="48230-173">To demonstrate how **LocalOffsetZ** works, the next sample animates **LocalOffsetZ** from 0 to 400 and [**RotationX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.rotationx) from 0 to 65 degrees.</span></span>

<span data-ttu-id="48230-174">Das Objekt bewegt sich zu Beginn der Animation, wenn der Wert von [**RotationX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.rotationx) nahe null liegt (d. h. parallel zum Bildschirm), direkt in Richtung des Betrachters, mit der Abwärtsdrehung des Objekts wird dieses jedoch nach unten verschoben.</span><span class="sxs-lookup"><span data-stu-id="48230-174">At the beginning of the animation, when the [**RotationX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.rotationx) value is near zero (parallel to the screen), the object moves directly out toward you, but as the face of the object rotates down, the object moves down instead.</span></span>

**<span data-ttu-id="48230-175">Globaler Versatz</span><span class="sxs-lookup"><span data-stu-id="48230-175">Global offset</span></span>**

<span data-ttu-id="48230-176">Die Eigenschaften [**GlobalOffsetX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.globaloffsetx), [**GlobalOffsetY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.globaloffsety) und [**GlobalOffsetZ**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.globaloffsetz) versetzen das Objekt entlang der Achsen relativ zum Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="48230-176">The [**GlobalOffsetX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.globaloffsetx), [**GlobalOffsetY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.globaloffsety), and [**GlobalOffsetZ**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.globaloffsetz) properties translate the object along axes relative to the screen.</span></span> <span data-ttu-id="48230-177">Anders als bei den Eigenschaften für den lokalen Versatz ist daher die Achse, entlang der das Objekt verschoben wird, unabhängig von der auf das Objekt angewendeten Drehung.</span><span class="sxs-lookup"><span data-stu-id="48230-177">That is, unlike the local offset properties, the axis the object moves along is independent of any rotation applied to the object.</span></span> <span data-ttu-id="48230-178">Diese Eigenschaften sind hilfreich, wenn Sie das Objekt lediglich entlang der X-, Y- oder Z-Achse des Bildschirms verschieben möchten und eine Drehung des Objekts keine Rolle spielt.</span><span class="sxs-lookup"><span data-stu-id="48230-178">These properties are useful when you want to simply move the object along the x-, y-, or z-axis of the screen without worrying about the rotation applied to the object.</span></span>

<span data-ttu-id="48230-179">Im nächsten Beispiel wird [**GlobalOffsetX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.globaloffsetx) von 0 bis 400 Grad animiert, und [**RotationY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.rotationy) wird von 0 bis 65 Grad animiert.</span><span class="sxs-lookup"><span data-stu-id="48230-179">The next sample animates [**GlobalOffsetX**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.globaloffsetx) from 0 to 400 and [**RotationY**](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.planeprojection.rotationy) from 0 to 65 degrees.</span></span>

<span data-ttu-id="48230-180">Sie stellen fest, dass in diesem Beispiel die Richtung des Objekts während seiner Drehung nicht geändert wird.</span><span class="sxs-lookup"><span data-stu-id="48230-180">Notice in this sample that the object does not change course as it rotates.</span></span> <span data-ttu-id="48230-181">Dies liegt daran, dass das Objekt ungeachtet seiner Drehung entlang der X-Achse des Bildschirms gedreht wird.</span><span class="sxs-lookup"><span data-stu-id="48230-181">That is because the object is being moved along the x-axis of the screen without regard to its rotation.</span></span>

## <a name="positioning-an-object"></a><span data-ttu-id="48230-182">Positionieren eines Objekts</span><span class="sxs-lookup"><span data-stu-id="48230-182">Positioning an object</span></span>

<span data-ttu-id="48230-183">Sie können den [**Matrix3DProjection**](https://msdn.microsoft.com/library/windows/apps/BR210128)-Typ und den [**Matrix3D**](https://msdn.microsoft.com/library/windows/apps/BR243266)-Typ für Semi-3D-Szenarien nutzen, die komplexer als die von [**PlaneProjection**](https://msdn.microsoft.com/library/windows/apps/BR210192) unterstützten sind.</span><span class="sxs-lookup"><span data-stu-id="48230-183">You can use the [**Matrix3DProjection**](https://msdn.microsoft.com/library/windows/apps/BR210128) and [**Matrix3D**](https://msdn.microsoft.com/library/windows/apps/BR243266) types for more complex semi-3D scenarios than are possible with the [**PlaneProjection**](https://msdn.microsoft.com/library/windows/apps/BR210192).</span></span> <span data-ttu-id="48230-184">**Matrix3DProjection** bietet Ihnen eine komplette 3D-Transformationsmatrix, die auf ein beliebiges [**UIElement**](https://msdn.microsoft.com/library/windows/apps/BR208911) angewendet werden kann. Somit können Sie Transformationsmatrizen und Perspektivmatrizen beliebiger Modelle auf Elemente anwenden.</span><span class="sxs-lookup"><span data-stu-id="48230-184">**Matrix3DProjection** provides you with a complete 3D transform matrix to apply to any [**UIElement**](https://msdn.microsoft.com/library/windows/apps/BR208911), so that you can apply arbitrary model transformation matrices and perspective matrices to elements.</span></span> <span data-ttu-id="48230-185">Beachten Sie, dass diese APIs nur im Minimalzustand vorliegen. Wenn Sie sie also nutzen möchten, müssen Sie den Code schreiben, mit dem die 3D-Transformationsmatrizen ordnungsgemäß erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="48230-185">Keep in mind that these API are minimal and therefore if you use them, you will need to write the code that correctly creates the 3D transform matrices.</span></span> <span data-ttu-id="48230-186">Daher ist es einfacher, für einfache 3D-Szenarien **PlaneProjection** zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="48230-186">Because of this, it is easier to use **PlaneProjection** for simple 3D scenarios.</span></span>
