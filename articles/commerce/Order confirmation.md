---
# required metadata

title: Show order confirmation on ecommerce
description: This topic describes how to show order confirmation on ecommerce
author: anupamar-ms
manager: BrendanS
ms.date: 07/23/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form:  RetailOperations, RetailFunctionalityProfile
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: anupamar-ms
ms.search.validFrom: 2019-07-23
ms.dyn365.ops.version: 

---
# Order confirmation

Order confirmation page is used to show a confirmation message once an order is placed. This page will have the Order confirmation module which shows the order confirmation number and the email address that was provided during checkout.

Once an order is placed during checkout, the order confirmation number and the email address are passed as query string to the order confirmation page. Order confirmation module receives the order confirmation number and the email address from the page url to render this module. This page context is required for the module to provide the status of the order.

## Usage in ecommerce:

* To show confirmation message once an order is placed. 

  

## Properties of Order confirmation module

|     Property name     | Values                                                       | Property Description                                         |
| :-------------------: | ------------------------------------------------------------ | ------------------------------------------------------------ |
|        Heading        | Heading text<br />Heading tag                                | The module can have a heading. Heading supports heading tag which defaults   to H2 but can be changed to meet accessibility requirements |

 

## More modules on Order confirmation page

**Recommendations**:: Recommendations can be placed on the order confirmation page to allow the user to continue their shopping journey. Any existing list can be used except Frequently bought together. 

**Marketing modules**: Any marketing content can added to this page – E.g. Feature, Content Placement, Content rich block etc.

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
