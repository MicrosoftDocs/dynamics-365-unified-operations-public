---
# required metadata

title: Create an order confirmation module
description: This topic covers order confirmation modules and describes how to create them in Microsoft Dynamics 365 Commerce.
author: anupamar
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anupamar-ms
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Create an order confirmation module

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers order confirmation modules and describes how to create them in Microsoft Dynamics 365 Commerce.

## Overview

An order confirmation module is used to show a confirmation message on an order confirmation page after an order is placed. The order confirmation module shows the order confirmation number and the customer email address that was provided during checkout.

When an order is placed during checkout, the order confirmation number and customer email address are passed to the order confirmation page as a query string in the page's URL. The order confirmation module receives this information and renders the order status on the order confirmation page. The order confirmation module requires this page context to provide the status of the order.

## Order confirmation module properties

| Property name | Values | Description |
|---------------|--------|-------------|
| Heading       | Heading text and heading tag (**H1**, **H2**, **H3**, **H4**, **H5**, or **H6**) | The order confirmation module can have a heading. By default, the **H2** heading tag is used for the heading. However, the tag can be changed to meet accessibility requirements. |

## Modules that can be used in an order confirmation page module 

- **Recommendations** – The recommendations module can be put on the order confirmation page to suggest other products to the customer.
- **Marketing** – The marketing module can add marketing content to the order confirmation page.

## Create an order confirmation page module

1. Create a page template that is named **order confirmation template**.
1. In the **Main** slot of the default page, add an order confirmation module.
1. In the order confirmation module, add a recommendations module.
1. Save and preview the template. The order confirmation module should not be rendered, because it requires the context of the order confirmation number.
1. Check in the template, and publish it.
1. Use the order confirmation template that you just created to create a page that is named **order confirmation page**.
1. Add the default page to the page outline.
1. In the **Header** slot, add a header fragment.
1. In the **Footer** slot, add a footer fragment.
1. In the **Main** slot, add an order confirmation module.
1. In the property pane of the order confirmation module, add the heading **Order confirmation**.
1. Below the order confirmation module, add a recommendations module, and configure it so that it uses the **New** and **Best Selling** settings.
1. Save and preview the page, check it in, and publish it.
