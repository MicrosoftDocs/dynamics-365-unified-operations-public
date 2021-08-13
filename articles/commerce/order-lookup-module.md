---
title: Order lookup module 
description: This topic covers the order lookup module and explains how to configure it in Microsoft Dynamics 365 Commerce.
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

This topic covers the order lookup module and explains how to configure it in Microsoft Dynamics 365 Commerce.

how to configure it to support order lookups for orders that were submitted as guest checkouts.

The order lookup module provides a form for looking up orders placed on an e-commerce site and is used as part of the [Enable order lookup for guest checkouts](order-lookup.md) feature. The order lookup module can be used to look up orders that were submitted through an e-commerce site, retail point of sale (POS), or call center. The form can retrieve orders that were submitted using guest checkout as well as orders submitted by registered users.

The following illustration shows an example of the form that is rendered by the order lookup module. When customers fill out the form and select **Find your order**, they are then redirected to the order details page. 

![Screenshot of the order lookup module displayed on a page.](./media/OrderLookup_module.PNG)

## Order lookup module properties

| Property name     | Value     | Description                                                  |
| ----------------- | --------- | ------------------------------------------------------------ |
| Heading           | Text      | The heading that displays at the top of the form (for example, "Find your order"). |
| Rich text         | Rich text | Optional explanatory text that appears below the heading.   |
| Order status type | Enum      | Dropdown list value for selecting the type of information the form will request from the customer in addition to the order confirmation ID. The values currently supported are:<br/><br/><ul><li><b>Email</b> - Provides a field for customers to provide the email addresses used when they placed their order.</li><li><b>None</b> - No additional information besides order confirmation ID is requested in the form.</li></ul> |

## Add an order lookup module to a page

The order lookup module can be added within the body of any page of your e-commerce site. If you want to use the order lookup module to enable guest checkout order lookup, ensure that you're adding it to a page that does not require the user to be signed in. A page's **Requires sign in?** setting can be found in Commerce site builder tree view by selecting the **Default page (Required)** node and looking at the bottom of the right pane. 

## Additional resources

[Enable order lookup for guest checkouts](order-lookup.md)

[Module library overview](starter-kit-overview.md)




[!INCLUDE[footer-include](../includes/footer-banner.md)]
