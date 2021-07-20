---
# required metadata

title: Configure the customer account payment method for B2B e-commerce sites
description: This topic describes how to configure the customer account payment method for business-to-business (B2B) e-commerce sites.
author: josaw1
ms.date: 01/20/2021
ms.topic: article
ms.prod: 
ms.technology: 
# optional metadata
ms.search.form: RetailOperations
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: v-chgri
#ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: josaw
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.14

---

# Configure the customer account payment method for B2B e-commerce sites

[!include [banner](../../includes/banner.md)]

This topic describes how to configure the customer account payment method for business-to-business (B2B) e-commerce sites.

Retailers can accept various types of payment in exchange for the products and services that they sell in an e-commerce channel. Each payment type that a retailer accepts must be configured in Microsoft Dynamics 365 Commerce when the system is set up. The customer account (or "on account") payment method must be supported on B2B e-commerce sites. 

## Prerequisites

1. Add the customer account payment method in Commerce headquarters.
2. Associate the customer account payment method with the e-commerce channel.
3. Make sure that **Allow on account** is enabled for the customer at **Retail and Commerce \> Customers \> All customers \> Payment defaults** in Commerce headquarters. Also make sure that **Credit limit** parameters are set appropriately for the customer at **Retail and Commerce \> Customers \> All customers \> Credit and Collections** in Commerce headquarters. 

## Enable the customer account payment method in Commerce site builder 

To enable the customer account payment method in Commerce site builder, follow these steps.

1. Go to **Site Settings \> Extensions**.
1. Set the **Enable customer account payments** property to **Enabled for B2B customers**. 
1. Select **Save and Publish**.

> [!NOTE]
> The new site settings take effect only after the app.settings.json file is updated. For more information, see [SDK and Module library updates](../e-commerce-extensibility/sdk-updates.md).

## Enable the customer account payment method on the checkout page for the B2B e-commerce site

To enable the customer account payment method on the checkout page for the B2B e-commerce site, follow these steps.

1. In Commerce site builder, find and edit the checkout page or fragment that contains the checkout module for the B2B e-commerce site.
1. In the **Checkout section container** slot, select **Add Module**, and then add a **Customer account payment** module.
1. Position the **Customer account payment** module by selecting the ellipsis (**...**), and then selecting **Move Up** or **Move Down** as required.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Confirm that the customer account payment method has been enabled and published

To confirm that the customer account payment method has been enabled, follow these steps.

1. Sign in to the e-commerce site.
1. Add a product to the cart.
1. Go to the checkout page. You should see the new **Customer Account** payment method.

## Additional resources

[Set up a B2B e-commerce site](set-up-b2b-site.md)

[Create org modeling hierarchies for B2B organizations](org-model.md)

[Manage business partner users on B2B e-commerce sites](manage-b2b-users.md)

[Set product quantity limits for B2B e-commerce sites](quantity-limits.md)

[SDK and Module library updates](../e-commerce-extensibility/sdk-updates.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]