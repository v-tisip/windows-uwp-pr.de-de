---
author: andrewleader
Description: Here are the elements and attributes you use to create adaptive tiles.
title: Adaptive Kacheln – Schema und Vorlagen
ms.assetid: 858FB05E-87A2-49CF-BE48-570980AD36C8
label: Adaptive tile schema and templates
template: detail.hbs
ms.author: mijacobs
ms.date: 05/19/2017
ms.topic: article
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: 1ed938ec247f308559566ad299bec8eb8ea75674
ms.sourcegitcommit: cd00bb829306871e5103db481cf224ea7fb613f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "5875433"
---
# <a name="adaptive-tile-templates-schema-and-guidance"></a><span data-ttu-id="0396f-103">Vorlagen für adaptive Kacheln: Schema und Richtlinien</span><span class="sxs-lookup"><span data-stu-id="0396f-103">Adaptive tile templates: schema and guidance</span></span>

 

<span data-ttu-id="0396f-104">Im Folgenden werden Elemente und Attribute aufgeführt, mit denen Sie adaptive Kacheln erstellen können.</span><span class="sxs-lookup"><span data-stu-id="0396f-104">Here are the elements and attributes you use to create adaptive tiles.</span></span> <span data-ttu-id="0396f-105">Anweisungen und Beispiele finden Sie unter [Erstellen adaptiver Kacheln](create-adaptive-tiles.md).</span><span class="sxs-lookup"><span data-stu-id="0396f-105">For instructions and examples, see [Create adaptive tiles](create-adaptive-tiles.md).</span></span>

## <a name="tile-element"></a><span data-ttu-id="0396f-106">Kachel-Element</span><span class="sxs-lookup"><span data-stu-id="0396f-106">tile element</span></span>


``` xml
<tile>
  
  <!-- Child elements -->
  visual
  
</tile>
```

## <a name="visual-element"></a><span data-ttu-id="0396f-107">Visuelles Element</span><span class="sxs-lookup"><span data-stu-id="0396f-107">visual element</span></span>


``` xml
<visual
  version? = integer
  lang? = string
  baseUri? = anyURI
  branding? = "none" | "logo" | "name" | "nameAndLogo"
  addImageQuery? = boolean
  contentId? = string
  displayName? = string >
    
  <!-- Child elements -->
  binding+

</visual>
```

## <a name="binding-element"></a><span data-ttu-id="0396f-108">Bindungselement</span><span class="sxs-lookup"><span data-stu-id="0396f-108">binding element</span></span>


``` xml
<binding
  template = tileTemplateNameV3
  fallback? = tileTemplateNameV1
  lang? = string
  baseUri? = anyURI
  branding? = "none" | "logo" | "name" | "nameAndLogo"
  addImageQuery? = boolean
  contentId? = string
  displayName? = string
  hint-textStacking? = "top" | "center" | "bottom"
  hint-overlay? = [0-100] >

  <!-- Child elements -->
  ( image
  | text
  | group
  )*

</binding>
```

## <a name="image-element"></a><span data-ttu-id="0396f-109">Bildelement</span><span class="sxs-lookup"><span data-stu-id="0396f-109">image element</span></span>


``` xml
<image
  src = string
  placement? = "inline" | "background" | "peek"
  alt? = string
  addImageQuery? = boolean
  hint-crop? = "none" | "circle"
  hint-removeMargin? = boolean
  hint-align? = "stretch" | "left" | "center" | "right" />
```

## <a name="text-element"></a><span data-ttu-id="0396f-110">Textelement</span><span class="sxs-lookup"><span data-stu-id="0396f-110">text element</span></span>


``` xml
<text
  lang? = string
  hint-style? = textStyle
  hint-wrap? = boolean
  hint-maxLines? = integer
  hint-minLines? = integer
  hint-align? = "left" | "center" | "right" >

  <!-- text goes here -->

</text>
```

<span data-ttu-id="0396f-111">textStyle values: caption captionSubtle body bodySubtle base baseSubtle subtitle subtitleSubtle title titleSubtle titleNumeral subheader subheaderSubtle subheaderNumeral header headerSubtle headerNumeral</span><span class="sxs-lookup"><span data-stu-id="0396f-111">textStyle values: caption captionSubtle body bodySubtle base baseSubtle subtitle subtitleSubtle title titleSubtle titleNumeral subheader subheaderSubtle subheaderNumeral header headerSubtle headerNumeral</span></span>

## <a name="group-element"></a><span data-ttu-id="0396f-112">Gruppenelement</span><span class="sxs-lookup"><span data-stu-id="0396f-112">group element</span></span>


``` xml
<group>

  <!-- Child elements -->
  subgroup+

</group>
```

## <a name="subgroup-element"></a><span data-ttu-id="0396f-113">Untergruppenelement</span><span class="sxs-lookup"><span data-stu-id="0396f-113">subgroup element</span></span>


``` xml
<subgroup
  hint-weight? = [0-100]
  hint-textStacking? = "top" | "center" | "bottom" >

  <!-- Child elements -->
  ( text
  | image
  )*

</subgroup>
```

## <a name="related-topics"></a><span data-ttu-id="0396f-114">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="0396f-114">Related topics</span></span>


* [<span data-ttu-id="0396f-115">Erstellen adaptiver Kacheln</span><span class="sxs-lookup"><span data-stu-id="0396f-115">Create adaptive tiles</span></span>](create-adaptive-tiles.md)
 

 




