---
# required metadata

title: Metatags module
description: This topic describes the metatags module and how to add it to a template in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 03/23/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Metatags modules

[!include [banner](includes/banner.md)]

This topic describes the metatags module and how to add it to a template in Microsoft Dynamics 365 Commerce.

The metatags module can be added to a template's **HTML Head** slot.  One or more meta tags can be added using the **Add Meta Tag** configuration field button.  An example below shows a metatags module added to the HTML head of a template:

![Metatags modules](media/metatags-module-1.png)

## Metatags module properties

| Property name     | Values | Description |
|-------------------|--------|-------------|
| Meta Tags | Text | One or more meta tags can be added to the module. |

## Adding a metatags module to a template

1. From within a site builder template select the **Add Module** option within the **...** of the **HTML Head** slot as shown below.

    ![Add new module](media/metatags-module-2.png)

1. Select the metatags module followed by the **OK** button as shown below. 

    ![Add script module](media/metatags-module-3.png)

Once the module is added it can now be configured and the template can be saved and published.

## Additional resources

[Module library overview](starter-kit-overview.md)

[Default page module](default-page-module.md)

[Page summary modules](page-summary-module.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
