---
# required metadata

title: Page module
description: This topic covers the page module and describes how to add one to site page in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 02/11/2021
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

# Container module

[!include [banner](includes/banner.md)]

This topic covers the page module and describes how to add one to site page in Microsoft Dynamics 365 Commerce.

A page module is a special module that becomes the root of a page and can only be added to a template **Body** slot. Only one page module is available with the module library but additional ones can be created using the [online channel extensibility SDK](e-commerce-extensibility/overview.md) if desired.  The page model defines the core slots ("Header Slot", "Sub Header Slot", "Main Slot", "Sub Footer Slot" and "Footer Slot") that will show up in the page editor within site builder as shown in the below image.

![Page module slots](media/page-module-1.png)

## Examples of container modules in e-Commerce

- A site author wants a three-column layout, where three modules appear side by side. Therefore, the site author uses a container module of the container with 3-slots type.
- A site author wants a six-column layout, where six modules appear side by side. Therefore, the site author uses a container of the contain type that has six columns inside it.
- A site author wants to put a module on a page but doesn't want it to fill the screen. Therefore, the site author adds the module to a container module and sets the container's **Width** property to **Fit container**.

The following image shows an example of a container module that contains a carousel module in Commerce site builder. In this example, the **Width** property of the container module is set to **Fill Screen**.

![Example of a container module](./media/ecommerce-container.PNG)

## Container module properties

| Property name     | Values | Description |
|-------------------|--------|-------------|
| Heading           | Heading text and heading tag (**H1**, **H2**, **H3**, **H4**, **H5**, or **H6**) | An optional heading can be provided for the container. By default, the **H2** heading tag is used for the heading. However, the tag can be changed to meet accessibility requirements. |
| Width             | **Fit container** or **Fill screen** | If the value is set to **Fit container** (the default value), the modules inside the container are limited to the width of the container. If the value is set to **Fill screen**, the modules aren't limited to the container width but can fill the screen. |
| Number of columns | **1**, **2**, **3**, **4**, **6**, or **12** | This property defines the number of columns in the container. A container can have up to 12 columns. |

## Adding a page module to a template



## Additional resources

[Module library overview](starter-kit-overview.md)

[Footer module](author-footer-module.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
