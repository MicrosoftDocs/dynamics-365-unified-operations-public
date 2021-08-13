---
title: Order lookup module 
description: This topic covers the order lookup module and how to configure it in Microsoft Dynamics 365 Commerce to support order lookups for orders that were submitted as guest checkouts.
author: stuharg
ms.date: 09/03/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: stuharg
ms.search.validFrom: 2021-08-15
ms.dyn365.ops.version: Release 10.0.22

---

# Order lookup module

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic covers the order lookup module and how to configure it in Microsoft Dynamics 365 Commerce to support order lookups for orders that were submitted as guest checkouts.

The order lookup module provides a form for looking up orders from an e-commerce site. This module is used as part of the [Enable order lookup for guest checkouts feature](order-lookup.md). It can be used to look up orders that were submitted through e-commerce, retail point of sale (POS) or call center. The form can retrieve orders that were submitted with guest checkout as well orders submitted by registered users.

Below is an example of the form that is rendered by the order lookup module. When customers fill out the form and click the "Find your order" button, they're taken to the order details page. 

![Screenshot of the order lookup module displayed on a page.](./media/OrderLookup_module.PNG)

## Order lookup module properties

| Property name     | Value     | Description                                                  |
| ----------------- | --------- | ------------------------------------------------------------ |
| Heading           | Text      | The heading that displays at the top of the form. "Find your order" in the example  above. |
| Rich text         | Rich text | Optional  explanatory text that appears below the heading.   |
| Order status type | Enum      | Dropdown for  selecting the type of information the form will request from the customer in  addition to their order confirmation ID. The values currently supported are:<br />**Email** - provides a field for customers to provide the email addresses they entered when they placed their oder.   <br />**None** - no additional information besides Order confirmation ID is requested in the form. |

## Add an order lookup module to a page

The order lookup module can be added within the body of any page of your e-commerce site. If you wish to use this module to enable guest order lookup, ensure that you're adding it to a page that does not require the user to be signed in. This setting is found in the tree view for a page in site builder. Click on the **Default page (Required)** node and look for the **Requires sign in?** setting at the bottom of the right pane. 

## Additional resources

[Enable order lookup for guest checkouts](order-lookup.md)

[Module library overview](starter-kit-overview.md)




[!INCLUDE[footer-include](../includes/footer-banner.md)]
