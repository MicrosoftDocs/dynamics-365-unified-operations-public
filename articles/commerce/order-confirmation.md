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

## Example of order confirmation module usage in e-Commerce

- The order confirmation module shows a confirmation message on the order confirmation page once an order is placed. 

  
## Order confirmation module properties

|     Property name     | Values                                                       | Property description                                         |
| :-------------------: | ------------------------------------------------------------ | ------------------------------------------------------------ |
|        Heading        | Heading text<br />Heading tag                                | The heading text and heading tag. The default heading tag is H2 but can be changed to meet accessibility requirements. |

## Modules available in an order confirmation page module 

**Recommendations**:: The recommendations module can be placed on the order confirmation page to suggest other products to the customer. 

**Marketing**: The marketing module can add marketing content to the order confirmation page.

## Authoring order confirmation page

1. Create a template for Order confirmation page “Order confirmation template”

2. To Main Slot of the Default page, add Order confirmation module and Recommendations.

3. Save and Preview. Order confirmation module will not render since it needs context of the order confirmation id.

4. Check-in and Publish.

5. Create a page with the “Order confirmation template” and call it “Order confirmation page”

6. Add the Default Page on the page outline

7. In the Header of the Main slot, add the Header fragment.

8. In the Footer of the Main slot, add the Footer fragment.

9. In the Body of the Main slot add the order confirmation module

10. In the property panel of the order confirmation module, add Heading “Order confirmation”

11. Below the Order confirmation module, add Recommendations – New, Best Selling.

12. Save and preview. 

13. Check-in and Publish

14. Any other marketing module can be added to this page if needed. 
