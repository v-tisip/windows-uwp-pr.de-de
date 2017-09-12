---
author: mukin
title: "Unterstützung für Magnetstreifenlesegeräte"
description: "Dieser Artikel enthält Informationen über die Magnetstreifenleser-Point of Service-Gerätefamilie"
ms.author: mukin
ms.date: 05/11/2017
ms.topic: article
ms.prod: windows
ms.technology: uwp
keywords: windows10, UWP
ms.openlocfilehash: 8bf2d6bf355c20e673fd2180d3bd70cbdede920c
ms.sourcegitcommit: ca060f051e696da2c1e26e9dd4d2da3fa030103d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2017
---
# <a name="magnetic-stripe-reader-device-support"></a><span data-ttu-id="a60c8-104">Unterstützung für Magnetstreifenlesegeräte</span><span class="sxs-lookup"><span data-stu-id="a60c8-104">Magnetic stripe reader device support</span></span>

<span data-ttu-id="a60c8-105">Windows enthält für USB-verbundene Magnetstreifenleser einen integrierten Klassentreiber, dessen Spezifikation auf der von [USB.org](http://www.usb.org/developers/hidpage/) definierten HID POS-Scanner-Nutzungstabelle (8 c) basiert.</span><span class="sxs-lookup"><span data-stu-id="a60c8-105">Windows contains a in-box class driver for USB connected Magnetic stripe readers, which is based on the HID POS Scanner Usage Table (8c) specification defined by [USB.org](http://www.usb.org/developers/hidpage/).</span></span>

## <a name="vendor-specific-support"></a><span data-ttu-id="a60c8-106">Herstellerspezifische Unterstützung</span><span class="sxs-lookup"><span data-stu-id="a60c8-106">Vendor specific support</span></span>
<span data-ttu-id="a60c8-107">Windows bietet Unterstützung für die folgenden Magnetstreifenleser von Magtek und IDTech, basierend auf deren Anbieter-ID und Produkt-ID (VID/PID).</span><span class="sxs-lookup"><span data-stu-id="a60c8-107">Windows provides support for the following magnetic stripe readers from Magtek and IDTech based on their Vendor ID and Product ID (VID/PID).</span></span>

| <span data-ttu-id="a60c8-108">Hersteller</span><span class="sxs-lookup"><span data-stu-id="a60c8-108">Manufacturer</span></span> |    <span data-ttu-id="a60c8-109">Model(le)</span><span class="sxs-lookup"><span data-stu-id="a60c8-109">Model(s)</span></span> |  <span data-ttu-id="a60c8-110">Teilenummer</span><span class="sxs-lookup"><span data-stu-id="a60c8-110">Part Number</span></span> |
|--------------|-----------|--------------|
| <span data-ttu-id="a60c8-111">IDTech</span><span class="sxs-lookup"><span data-stu-id="a60c8-111">IDTech</span></span> | <span data-ttu-id="a60c8-112">SecureMag (VID:0ACD PID:2010)</span><span class="sxs-lookup"><span data-stu-id="a60c8-112">SecureMag (VID:0ACD PID:2010)</span></span> | <span data-ttu-id="a60c8-113">IDRE-3x5xxxx</span><span class="sxs-lookup"><span data-stu-id="a60c8-113">IDRE-3x5xxxx</span></span> |
| | <span data-ttu-id="a60c8-114">MiniMag (VID:0ACD PID:0500)</span><span class="sxs-lookup"><span data-stu-id="a60c8-114">MiniMag (VID:0ACD PID:0500)</span></span> |   <span data-ttu-id="a60c8-115">IDMB-3x5xxxx</span><span class="sxs-lookup"><span data-stu-id="a60c8-115">IDMB-3x5xxxx</span></span> |
| <span data-ttu-id="a60c8-116">Magtek</span><span class="sxs-lookup"><span data-stu-id="a60c8-116">Magtek</span></span> | <span data-ttu-id="a60c8-117">MagneSafe (VID:0801 PID:0011)</span><span class="sxs-lookup"><span data-stu-id="a60c8-117">MagneSafe (VID:0801 PID:0011)</span></span> |  <span data-ttu-id="a60c8-118">210730xx</span><span class="sxs-lookup"><span data-stu-id="a60c8-118">210730xx</span></span> |
| | <span data-ttu-id="a60c8-119">Dynamag (VID:0801 PID:0002)</span><span class="sxs-lookup"><span data-stu-id="a60c8-119">Dynamag (VID:0801 PID:0002)</span></span> |   <span data-ttu-id="a60c8-120">210401xx</span><span class="sxs-lookup"><span data-stu-id="a60c8-120">210401xx</span></span> |

## <a name="custom-vendor-specific"></a><span data-ttu-id="a60c8-121">Spezifisch für benutzerdefinierten Anbieter</span><span class="sxs-lookup"><span data-stu-id="a60c8-121">Custom vendor specific</span></span>
<span data-ttu-id="a60c8-122">Windows unterstützt die Implementierung der zusätzlichen anbieterspezifischen Treiber zur Unterstützung von Magnetstreifenlesern.</span><span class="sxs-lookup"><span data-stu-id="a60c8-122">Windows supports implementation of additional vendor specific drivers to support additional magnetic stripe readers.</span></span> <span data-ttu-id="a60c8-123">Bitte prüfen Sie die Verfügbarkeit des Magnetstreifenlesers bei Ihrem Hersteller.</span><span class="sxs-lookup"><span data-stu-id="a60c8-123">Please check with your magnetic stripe reader manufacturer for availability.</span></span>

## <a name="see-also"></a><span data-ttu-id="a60c8-124">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a60c8-124">See also</span></span>
+   [<span data-ttu-id="a60c8-125">Windows.Devices.PointOfService namespace</span><span class="sxs-lookup"><span data-stu-id="a60c8-125">Windows.Devices.PointOfService namespace</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.devices.pointofservice)
+   [<span data-ttu-id="a60c8-126">MagneticStripeReader class</span><span class="sxs-lookup"><span data-stu-id="a60c8-126">MagneticStripeReader class</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.devices.pointofservice.magneticstripereader)
+   [<span data-ttu-id="a60c8-127">Magnetstreifenleser-Beispiel</span><span class="sxs-lookup"><span data-stu-id="a60c8-127">Magnetic stripe reader sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MagneticStripeReader)
