---
title: Configure the customer account payment method for B2B e-commerce sites
description: This article describes how to configure the customer account payment method in Microsoft Dynamics 365 Commerce. It also describes how credit limits affect on-account payment capture on business-to-business (B2B) e-commerce sites.
author: josaw1
ms.date: 05/28/2024
ms.update-cycle: 1095-days
ms.topic: how-to
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2021-01-31
ms.search.form: RetailOperations
ms.custom: 
  - bap-template
  - evergreen
---

# Configure the customer account payment method for B2B e-commerce sites

[!include [banner](../../includes/banner.md)]

This article describes how to configure the customer account payment method in Microsoft Dynamics 365 Commerce. It also describes how credit limits affect on-account payment capture on business-to-business (B2B) e-commerce sites.

Retailers can accept various types of payment in exchange for the products and services that they sell in an e-commerce channel. Each payment type that a retailer accepts must be configured in Dynamics 365 Commerce when the system is set up. The customer account (or "on-account") payment method must be supported on B2B e-commerce sites. 

## Prerequisites

1. Add the customer account payment method in Commerce headquarters.
2. Associate the customer account payment method with the e-commerce channel.
3. Ensure that the **Allow on account** property is enabled for the customer at **Retail and Commerce \> Customers \> All customers \> Payment defaults** in Commerce headquarters.

    > [!NOTE]
    > If all customers should be allowed to have the on-account payment method enabled, you can set the **Allow on account** property to **Yes** for the default customer of the channel that is associated with the B2B site. 

## Enable the customer account payment method in Commerce site builder 

To enable the customer account payment method in Commerce site builder, follow these steps:

1. Go to **Site Settings \> Extensions**.
1. Set the **Enable customer account payments** property to **Enabled for B2B customers**. 
1. Select **Save and Publish**.

> [!NOTE]
> The new site settings take effect only after the app.settings.json file is updated. For more information, see [SDK and Module library updates](../e-commerce-extensibility/sdk-updates.md).

## Enable the customer account payment method on the checkout page for the B2B e-commerce site

To enable the customer account payment method on the checkout page for the B2B e-commerce site, follow these steps:

1. In Commerce site builder, find and edit the checkout page or fragment that contains the checkout module for the B2B e-commerce site.
1. In the **Checkout section container** slot, select **Add Module**, and then add a **Customer account payment** module.
1. Position the **Customer account payment** module by selecting the ellipsis (**...**), and then selecting **Move Up** or **Move Down** as required.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Confirm that the customer account payment method has been enabled and published

To confirm that the customer account payment method has been enabled, follow these steps:

1. Sign in to the e-commerce site.
1. Add a product to the cart.
1. Go to the checkout page. You should see the new **Customer Account** payment method.

## Work with credit limits

When the capabilities for customer account payments are enabled on the B2B site, organizations usually want to show information about credit limits and credit limit balances during the order capture process. The credit limit for a customer is defined by the **Credit limit** property on the **Credit and collections** FastTab of the customer record in Commerce headquarters. However, in B2B scenarios, an order that a customer places should often be invoiced to the account of the organization that the customer belongs to. Therefore, you must set the **Invoice account** property on the **Invoice and delivery** FastTab of the customer record to the customer account ID of the organization. Then, when the customer places an order on the B2B site, the order will be invoiced to the organization. The B2B site will also use the credit limit of the organization instead of the credit limit that is defined on the customer record.

The credit limit calculation and balance that are shown on the B2B website depend on the setting of the **Credit limit type** property in Commerce headquarters under **Credit limits** FastTab at **Credit and collections \> Setup \> Credit and collections parameters \> Credit**. 
The values that the **Credit limit type** property supports are **None**, **Balance**, **Balance + packing slip or product receipt**, and **Balance + All**. For more information about these values, see [Credit limit type values](/dynamics365/supply-chain/sales-marketing/credit-limits-customers).

> [!NOTE]
> We recommend that you set the **Credit limit type** property to **Balance + packaging slip or product slip**, so that open sales orders don't contribute to the balance calculation. Then, if your customers place future orders, they don't have to worry that those orders will affect their current balance.

Another property that affects on-account ordering is the **Mandatory credit limit** property, which is located on the **Credit and collections** FastTab of the customer record. By setting this property to **Yes** for specific customers, you can force the system to check their credit limit, even if the **Credit limit type** property has been set to **None** to specify that the credit limit shouldn't be checked for any customer.

Starting in Dynamics 365 Commerce version **10.0.48**, you can configure customer orders to follow the full credit management flow. When you enable this feature, the system evaluates orders against credit management blocking rules and can put orders on credit hold for your finance team's visibility and control before fulfillment proceeds.

To enable this behavior, configure the following settings:

- Enable the **Leverage credit management setup for Commerce orders** feature in the **Feature management** workspace.
- Enable the **Credit management** option in **Accounts receivable parameters** > **Credit management**.

> [!NOTE]
> If you don't enable either of these settings, Commerce orders use the default behavior where the system directly blocks the order or transaction when a customer's credit limit is exceeded, instead of routing it through the credit hold flow.

You can control whether the system checks the credit limit at the time of order capture. To let B2B buyers on e-commerce site place orders even after the credit limit is exceeded, enable a new setting named **Skip credit check during order capture** in the **Functionality profile** for online stores. After the order is placed, the e-commerce orders go through the credit management flow. Depending on the configured blocking rules, orders might be placed on credit hold for review.

> [!NOTE]
> For the **Credit limit used** blocking rule to take effect, you must also enable **Check credit limit on sales order** in **Credit and collections parameters**. This setting applies to all credit management checkpoints, including order confirmation, picking list generation, and invoicing. Other blocking rules don't require this setting.

## Additional resources

[Set up a B2B e-commerce site](set-up-b2b-site.md)

[Manage B2B business partners using customer hierarchies](partners-customer-hierarchies.md)

[Manage business partner users on B2B e-commerce sites](manage-b2b-users.md)

[Set product quantity limits for B2B e-commerce sites](quantity-limits.md)

[SDK and Module library updates](../e-commerce-extensibility/sdk-updates.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
