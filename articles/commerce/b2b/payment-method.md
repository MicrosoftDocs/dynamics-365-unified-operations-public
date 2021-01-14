---
# required metadata

title: Configure payment methods for B2B e-commerce sites
description: This topic describes how to configure payment menthods for B2B e-commerce sites.
author: josaw1
manager: AnnBe
ms.date: 01/13/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 
# optional metadata
ms.search.form:  RetailOperations
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: josaw
#ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: josaw
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.14

---

# Configure payment methods for B2B e-commerce sites

[!include [banner](../../includes/banner.md)]

This topic describes how to configure payment menthods for B2B e-commerce sites.

Retailers can accept various types of payment in exchange for the products and services that they sell in an e-commerce channel. Each payment type that a retailer accepts must be configured in Dynamics 365 Commerce when the system is set up. "Customer account" or "on account" payment is one payment method which needs to be supported on B2B e-commerce channels. 

## Prerequisites

1. Add Customer Account payment method in Commerce headquarters.
2. Associate Customer Account payment method to with e-commerce channel.
3. Ensure that customer has a **Credit limit** enabled in headquarters at **Modules \> Retail and commerce \> Customers \> All customers**. 

## Set up B2B e-commerce site to use 'Customer Account' payment method

### Step 1 - Enable the "Customer Account" payment method in Commerce site builder Site Settings 

1. In Commerce site builder, go to **Site Settings**.
1. Select the **Extensions** tab on the bottom left corner
1. In the list of extensions search for **Enable customer account payments**
1. There are four possible options for the site.

    - Disabled for all customers: 'Does not allow any customer type to use 'Customer Account / Credit limit' for eCommerce.
    - Enabled for B2B customers: 'Only enables B2B customers to use the 'Customer Account' payment method in eCommerce.
    - Enabled for B2C customers: 'Only enables B2C customers to use the 'Customer Account' payment method in eCommerce.
    - Enabled for all customers: 'Enables all customers to use the 'Customer Account' payment method in eCommerce.
 
> [!NOTE]
> The new 'site settings' will only be available after the App.Settings.Jason file has been updated. Please follow this below link: [SDK and Module library
updates](../e-commerce-extensibility/sdk-updates.md)

1. Save the changes and publish

### Step 2 - Enable the 'Customer Account' Payment method in the 'Checkout Page'

1. Search for the **Checkout page** (based on your setup it may be in *Pages* or *Fragements* and edit the **Checkout** container.
1. For the 'Checkout' container click **Add Module** and add a **Customer Account** payment method module.
1. Position the module using 'Move Up' / 'Move Down'
1. Select **Finish Editing**
1. **Save and Publish** the site

### Step 3 - Confirmation

1. On the e-commerce website - log in as the user type which was 'Enabled'
1. Add product and Checkout.
1. In the Checkout page - you should see the new Payment method: 'Customer Account'

## Troubleshooting

- Ensure the prerequisites are met.
- Ensure the site settings and and the e-commerce site are published.
- Ensure that the credit limit for the customer is available in headquarters in the customer form.
- If the credit limit check is not mandatory, customers can buy using their customer account without any credit limit check.
- Credit limit on e-commerce only shows the invoiced order balance (in some cases there may be a delay in updating the balance).
- If the credit balance has crossed and if the user has already purchased a product using customer account, based on the checkout flow the orders may not be invoiced.


