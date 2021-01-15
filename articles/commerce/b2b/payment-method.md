---
# required metadata

title: Configure customer account payment method for B2B e-commerce sites
description: This topic describes how to configure the customer account payment menthod for B2B e-commerce sites.
author: josaw1
manager: AnnBe
ms.date: 01/15/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 
# optional metadata
ms.search.form:  RetailOperations
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

# Configure customer account payment method for B2B e-commerce sites

[!include [banner](../../includes/banner.md)]

This topic describes how to configure the customer account payment menthod for B2B e-commerce sites.

Retailers can accept various types of payment in exchange for the products and services that they sell in an e-commerce channel. Each payment type that a retailer accepts must be configured in Dynamics 365 Commerce when the system is set up. The "customer account" (or "on account") payment method must be supported on B2B e-commerce sites. 

## Prerequisites

1. Add customer account payment method in Commerce headquarters.
2. Associate customer account payment method with e-commerce channel.
3. Ensure that customer has **Credit limit** enabled in headquarters at **Modules \> Retail and commerce \> Customers \> All customers**. 

## Enable the customer account payment method in Commerce site builder 

1. Go to **Site Settings \> Extensions**.
1. For **Enable customer account payments**, select **Enabled for B2B customers** from the drop-down menu. The customer account payment method will also work if **Enabled for all customers** is selected.
1. Select **Save and Publish**.

> [!NOTE]
> The new 'site settings' will only be available after the App.Settings.Jason file has been updated. Please follow this below link: [SDK and Module library
updates](../e-commerce-extensibility/sdk-updates.md)

## Enable the customer account payment method on the B2B e-commerce site checkout page

Enable the customer account payment method on the B2B e-commerce site checkout page, follow these steps.

1. In Commerce site builder, find and edit the checkout page or fragment that contains the checkout module for the B2B e-commerce site. Based on your setup, the checkout module may be in *Pages* or *Fragments* and edit the **Checkout** container.
1. In the **Checkout section container** slot, select **Add Module** and add a **Customer account payment** module.
1. Position the **Customer Account** module as needed using **Move Up** or **Move Down** on the ellipsis menu.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Confirm that the customer account payment method has been enabled and published

To confirm that the customer account payment method has been enabled, follow these steps.

1. Sign in to the e-commerce site.
1. Add a product to the cart.
1. Go to the **Checkout** page. You should see the new payment method "Customer Account".

## Troubleshooting

- Ensure the prerequisites are met.
- Ensure the site settings and and the e-commerce site are published.
- Ensure that the credit limit for the customer is available in headquarters in the customer form.
- If the credit limit check is not mandatory, customers can buy using their customer account without any credit limit check.
- Credit limit on e-commerce only shows the invoiced order balance (in some cases there may be a delay in updating the balance).
- If the credit balance has crossed and if the user has already purchased a product using customer account, based on the checkout flow the orders may not be invoiced.


