---
# required metadata

title: Author an order confirmation module
description: This topic covers order confirmation modules and how to author them in Dynamics 365 Commerce.
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
# Author an order confirmation module

[!include [banner](../../includes/preview-banner.md)]
[!include [banner](../../includes/banner.md)]

This topic covers order confirmation modules and how to author them in Dynamics 365 Commerce.

## Overview

An order confirmation module is used to show a confirmation message on an order confirmation page once an order is placed. The order confirmation module displays the order confirmation number and the customer email address that was provided during checkout.

When an order is placed during checkout, the order confirmation number and customer email address are passed to the order confirmation page as a query string in the page URL. The order confirmation module receives this information and renders the order status on the order confirmation page. This page context is required for the module to provide the status of the order.

## Order confirmation module properties

|     Property name     | Values                                                       | Property description                                         |
| :-------------------: | ------------------------------------------------------------ | ------------------------------------------------------------ |
|        Heading        | Heading text<br />Heading tag                                | The heading text and heading tag. The default heading tag is H2 but can be changed to meet accessibility requirements. |

## Modules available in an order confirmation page module 

- **Recommendations**: The recommendations module can be placed on the order confirmation page to suggest other products to the customer. 

- **Marketing**: The marketing module can add marketing content to the order confirmation page.

## Author an order confirmation page module

1. Create a new page template named "order confirmation template."

1. In the **Main** slot of the default page, add an order confirmation module. Then, add a recommendations module to the new module.

1. Save and preview the template. The order confirmation module will not render since it needs the context of the order confirmation ID.

1. Check-in and publish the template.

1. Create a new page named "order confirmation page" using the order confirmation template you created.

1. Add the default page to the page outline.

1. In the **Header** slot, add a header fragment.

1. In the **Footer** slot, add a footer fragment.

1. In the **Main** slot, add an order confirmation module.

1. In the property pane of the order confirmation module, add the heading "Order confirmation."

1. Below the order confirmation module, add a recommendations module and configure it with the settings ""New" and "Best Selling."

1. Save, preview, check in, and publish the page.


