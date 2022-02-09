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

## Working with credit limits
With the customer account payment capabilities enabled on the B2B site, the organizations usually want to display the credit limit and credit limit balance information during the order capture process. The credit limit for a customer is defined on the customer record using the “Credit limit” property under the “Credit and collections” fast tab. However, it is common in the B2B scenarios that the order placed by the user should be invoiced under the organization account, where this user belongs. To do so, you need to set the customer account id of the organization on the **“Invoice account”** property under “Invoice and delivery” fast tab of the customer record. With this setup, when the customer places an order on the B2B site, not only the orders will be invoiced against the organization added to the invoice account, but also the B2B site will use the credit limit of the organization, instead of the credit limit defined on the customer record. 

The credit limit calculation and balance shown on the B2B website depends on the property “Credit limit type”. This property can be found under the **Account receivable parameters** -> **“Credit rating”** if the feature named **“Credit management”** is disabled in the Feature management workspace or under **“Credit and collections”** -> **“Setup” ** -> ** “Credit and collections parameters”** if the above feature is enabled. The values supported by this property are **“None”**, **“Balance”**, **“Balance + packing slip or product receipt”** , **“Balance + All”**. You can find the details about these values here [Credit limit type values](/dynamics365/supply-chain/sales-marketing/credit-limits-customers).

> [!NOTE]
> We recommend setting this property to “Balance + packaging slip or product slip” because then the open sales orders will not contribute towards the balance calculation. Thus, if your customers are placing orders for future, then they do not have to worry that these orders will impact their current balance.

Another property that impacts the ordering on account is the **“Mandatory credit limit”** property. This is present on the customer record under the “Credit and collections” fast tab. The main purpose of this property is that if the ‘Credit limit type’ is set to “None” i.e. do not check the credit limit for any customer, then you can selectively force the system to check the credit limit on certain customers which have “Mandatory credit limit” set to yes. Currently, the B2B site ties one additional functionality with this property i.e. **if you set this property to Yes on the customer record, then while placing the order, the B2B site enforces that the customer cannot pay more than the remaining credit balance using the on account payment.** For e.g. if the credit remaining balance of the customer is $1000, but the order is worth $1200, then the customer will only be able to pay $1000 on account, and the rest has to be paid with some other payment method. If the “Mandatory credit limit” is set to No, then the user can pay any amount using the on account payment method. Please note that even though the customer will be able to place the orders, but the system will not allow to fulfill such orders if they exceed the credit limit. So if you need to check the credit limit for all customers who are eligible for on account payments, **we recommend setting the “Credit limit type” property to “Balance + packaging slip or product slip” and setting the “Mandatory credit limit” property to No.**

The Credit and collections module has released new credit management capabilities such as putting the sales order on hold based on the blocking rules and the credit manager persona can release or reject these orders based on further analysis. These capabilities are enabled by enabling the “Credit management” feature from the Feature management workspace. However, as mentioned in the [document](/dynamics365/finance/accounts-receivable/cm-sales-order-credit-holds#free-text-invoices-orders-and-project-invoice-support-in-credit-management) the capability to put sales orders on hold is **not applicable** for Commerce orders. The main reason is that is common for Commerce orders to have a pre-payment and some of these scenarios are not currently supported. So, irrespective of whether the above feature is enabled or not, during order fulfillment, if the customer balance goes over the credit limit, the Commerce orders either throw a warning or throw an error depending on the value set for the field **“Message when exceeding credit limit”**, but the sales orders will not go on hold. 

> [!NOTE]
> The capability to allow the Commerce sales orders to go on hold based on the blocking rules is on our roadmap, but until it is supported, if it is required to force the Commerce orders to go through the new credit management flows, then you can customize the below files. You would need to set the flag “CredManExcludeSalesOrder” to No for Commerce orders. This flag is currently set to yes for all Commerce orders and hence these orders are skipped from the new flow. But as mentioned earlier, turning it on can cause issues with certain orders which have a pre-payment amount associated with them. Additionally, it can cause posting of cash and carry transactions to fail if the B2B customer can also purchase from stores using the POS. For e.g. if there is a blocking rule on the Cash payment type, and the B2B customer bought some items in the store using cash. Thus, during posting, the resulting sales order would not be successfully invoiced as it would go on hold. This causes the posting to fail. Thus, we recommend performing and end to end test after this customization. 
> 1.	RetailCreateCustomerOrderExtensions_CredMan_Extension.xml
> 2.	RetailCallCenterOrderExtensions_CredMan_Extension.xml

## Additional resources

[Set up a B2B e-commerce site](set-up-b2b-site.md)

[Create org modeling hierarchies for B2B organizations](org-model.md)

[Manage business partner users on B2B e-commerce sites](manage-b2b-users.md)

[Set product quantity limits for B2B e-commerce sites](quantity-limits.md)

[SDK and Module library updates](../e-commerce-extensibility/sdk-updates.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
