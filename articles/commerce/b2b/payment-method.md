---
# required metadata

title: Configure the customer account payment method for B2B e-commerce sites
description: This topic describes how to configure the customer account payment method in Microsoft Dynamics 365 Commerce and describes how credit limits impact the on-account payment capture on business-to-business (B2B) e-commerce sites.
author: josaw1
ms.date: 02/08/2022
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

This topic describes how to configure the customer account payment method in Microsoft Dynamics 365 Commerce and describes how credit limits impact the on-account payment capture on business-to-business (B2B) e-commerce sites.

Retailers can accept various types of payment in exchange for the products and services that they sell in an e-commerce channel. Each payment type that a retailer accepts must be configured in Dynamics 365 Commerce when the system is set up. The customer account (or "on-account") payment method must be supported on B2B e-commerce sites. 

## Prerequisites

1. Add the customer account payment method in Commerce headquarters.
2. Associate the customer account payment method with the e-commerce channel.
3. Ensure that **Allow on account** property is enabled for the customer at **Retail and Commerce \> Customers \> All customers \> Payment defaults** in Commerce headquarters.

    > [!NOTE]
    > If all customers should be allowed to have the on-account payment method enabled, you can set the **Allow on account** property to **Yes** for the default customer of the channel associated with the B2B site. 

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

## Work with credit limits

With customer account payment capabilities enabled on the B2B site, organizations usually want to display the credit limit and credit limit balance information during the order capture process. The credit limit for a customer is defined on the customer record using the **Credit limit** property under the **Credit and collections** FastTab. However, it is common in B2B scenarios that an order placed by a customer should be invoiced under the organization account to which that customer belongs. To do so, you must set the customer account ID of the organization on the **“Invoice account”** property under the **Invoice and delivery** FastTab of the customer record. With this setup, when a customer places an order on the B2B site the order will be invoiced against the organization added to the invoice account. The B2B site will also use the credit limit of the organization instead of the credit limit defined on the customer record. 

The credit limit calculation and balance shown on the B2B website depends on the **Credit limit type** property. This property can be found: 

- Under the **Accounts receivable parameters \> Credit rating** if the **Credit management** feature is disabled in the feature management workspace.
- Under the **Credit limits** FastTab at **Credit and collections \> Setup \> Credit and collections parameters \> Credit** if the **“Credit management** feature is enabled in the feature management workspace. 

The values supported by this property are **None**, **Balance**, **Balance + packing slip or product receipt** , and **Balance + All**. For more information about these values, see [Credit limit type values](/dynamics365/supply-chain/sales-marketing/credit-limits-customers).

> [!NOTE]
> It is recommended that you set the **Credit limit type** property to **Balance + packaging slip or product slip** so that open sales orders will not contribute towards the balance calculation. Then if your customers place future orders, they will not have to worry that those orders will impact their current balance.

Another property that impacts on-account ordering is the **Mandatory credit limit** property, which is located on the customer record under the **Credit and collections** FastTab. The main purpose of this property is that if the **Credit limit type** is set to **None** (that is, do not check the credit limit for any customer) you can then selectively force the system to check the credit limit on certain customers that have the **Mandatory credit limit** property set to **Yes**. 

Currently, B2B sites with the **Mandatory credit limit** property enabled have additional functionality. If the property is enabled on the customer record, when placing an order the B2B site enforces that the customer cannot pay more than the remaining credit balance using the on-account payment. For example, if the customer's remaining credit balance is $1000 but the order is worth $1200, then the customer will only be able to pay $1000 on-account and the balance will need to be paid with some other payment method. Conversely, if the **Mandatory credit limit** is disabled a customer can pay any amount using the on-account payment method. Note that even though the customer will be able to place orders, the system will not allow such orders to be fulfilled if they exceed the credit limit. If you need to check the credit limit for all customers who are eligible for on-account payments, it is recommended that the  **Credit limit type** property is set to **Balance + packaging slip or product slip** and that the **Mandatory credit limit** property is set to **No**.

The credit and collections module has new credit management capabilities such as putting sales orders on hold based on blocking rules. The credit manager persona can release or reject such orders based on further analysis. These capabilities are turned on by enabling the **Credit management** feature in the feature management workspace. However, the capability to put sales orders on hold is not applicable for Commerce orders because it is common for Commerce orders to have a prepayment and some of these scenarios are not currently supported. Regardless of whether or not the **Credit management** feature is enabled, if a customer balance goes over the credit limit during order fulfillment Commerce will generate either a warning or an error, but the sales orders will not go on hold. Whether Commerce generates a warning or error depends on the value set for the **Message when exceeding credit limit** field.

The capability to allow Commerce sales orders to go on hold based on blocking rules is planned for future Commerce releases, but until it is supported if it is required to force the Commerce orders to go through the new credit management flows, then you can customize the following files by setting the **CredManExcludeSalesOrder** flag to **No** for Commerce orders.

- RetailCreateCustomerOrderExtensions_CredMan_Extension.xml
- RetailCallCenterOrderExtensions_CredMan_Extension.xml

The **CredManExcludeSalesOrder** flag is currently set to **Yes** by default for all Commerce orders, which results in orders being omitted from the new flow. However, turning the flag on can cause issues with orders that have a prepayment amount associated with them. Turning the flag on can also cause the posting of cash and carry transactions to fail if the B2B customer can also purchase from stores using the point of sale (POS), for example if there is a blocking rule on the cash payment type and the B2B customer bought some items in the store using cash. Then during posting the resulting sales order would not be successfully invoiced as it would go on hold, which would cause the posting to fail. For this reason it is recommended that you perform an end-to-end test after implementing this customization. 

## Additional resources

[Set up a B2B e-commerce site](set-up-b2b-site.md)

[Create org modeling hierarchies for B2B organizations](org-model.md)

[Manage business partner users on B2B e-commerce sites](manage-b2b-users.md)

[Set product quantity limits for B2B e-commerce sites](quantity-limits.md)

[SDK and Module library updates](../e-commerce-extensibility/sdk-updates.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
