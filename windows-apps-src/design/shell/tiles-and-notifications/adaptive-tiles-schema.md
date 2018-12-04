---
Description: Here are the elements and attributes you use to create adaptive tiles.
title: Adaptive Kacheln – Schema und Vorlagen
ms.assetid: 858FB05E-87A2-49CF-BE48-570980AD36C8
label: Adaptive tile schema and templates
template: detail.hbs
ms.date: 05/19/2017
ms.topic: article
keywords: windows10, UWP
ms.localizationpriority: medium
ms.openlocfilehash: ed9124b0b66239c10b277f070ac2c9594c336fdd
ms.sourcegitcommit: b4c502d69a13340f6e3c887aa3c26ef2aeee9cee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "8463504"
---
# <a name="adaptive-tile-templates-schema-and-guidance"></a><span data-ttu-id="bc90a-103">Vorlagen für adaptive Kacheln: Schema und Richtlinien</span><span class="sxs-lookup"><span data-stu-id="bc90a-103">Adaptive tile templates: schema and guidance</span></span>

 

<span data-ttu-id="bc90a-104">Im Folgenden werden Elemente und Attribute aufgeführt, mit denen Sie adaptive Kacheln erstellen können.</span><span class="sxs-lookup"><span data-stu-id="bc90a-104">Here are the elements and attributes you use to create adaptive tiles.</span></span> <span data-ttu-id="bc90a-105">Anweisungen und Beispiele finden Sie unter [Erstellen adaptiver Kacheln](create-adaptive-tiles.md).</span><span class="sxs-lookup"><span data-stu-id="bc90a-105">For instructions and examples, see [Create adaptive tiles](create-adaptive-tiles.md).</span></span>

## <a name="tile-element"></a><span data-ttu-id="bc90a-106">Kachel-Element</span><span class="sxs-lookup"><span data-stu-id="bc90a-106">tile element</span></span>


``` xml
<tile>
  
  <!-- Child elements -->
  visual
  
</tile>
```

## <a name="visual-element"></a><span data-ttu-id="bc90a-107">Visuelles Element</span><span class="sxs-lookup"><span data-stu-id="bc90a-107">visual element</span></span>


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

## <a name="binding-element"></a><span data-ttu-id="bc90a-108">Bindungselement</span><span class="sxs-lookup"><span data-stu-id="bc90a-108">binding element</span></span>


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

## <a name="image-element"></a><span data-ttu-id="bc90a-109">Bildelement</span><span class="sxs-lookup"><span data-stu-id="bc90a-109">image element</span></span>


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

## <a name="text-element"></a><span data-ttu-id="bc90a-110">Textelement</span><span class="sxs-lookup"><span data-stu-id="bc90a-110">text element</span></span>


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

<span data-ttu-id="bc90a-111">textStyle values: caption captionSubtle body bodySubtle base baseSubtle subtitle subtitleSubtle title titleSubtle titleNumeral subheader subheaderSubtle subheaderNumeral header headerSubtle headerNumeral</span><span class="sxs-lookup"><span data-stu-id="bc90a-111">textStyle values: caption captionSubtle body bodySubtle base baseSubtle subtitle subtitleSubtle title titleSubtle titleNumeral subheader subheaderSubtle subheaderNumeral header headerSubtle headerNumeral</span></span>

## <a name="group-element"></a><span data-ttu-id="bc90a-112">Gruppenelement</span><span class="sxs-lookup"><span data-stu-id="bc90a-112">group element</span></span>


``` xml
<group>

  <!-- Child elements -->
  subgroup+

</group>
```

## <a name="subgroup-element"></a><span data-ttu-id="bc90a-113">Untergruppenelement</span><span class="sxs-lookup"><span data-stu-id="bc90a-113">subgroup element</span></span>


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

## <a name="related-topics"></a><span data-ttu-id="bc90a-114">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="bc90a-114">Related topics</span></span>


* [<span data-ttu-id="bc90a-115">Erstellen adaptiver Kacheln</span><span class="sxs-lookup"><span data-stu-id="bc90a-115">Create adaptive tiles</span></span>](create-adaptive-tiles.md)
 

 




