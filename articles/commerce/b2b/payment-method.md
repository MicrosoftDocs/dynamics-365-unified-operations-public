---
# required metadata

title: Configure payment methods for B2B
description: This topic describes how to configure payment menthods for B2B e-commerce sites.
author: josaw1
manager: AnnBe
ms.date: 01/12/2021
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

# Configure payment methods for B2B

[!include [banner](../../includes/banner.md)]

Retailers can accept various types of payment in exchange for the
products and services that they sell in the e-commerce channel. Each
payment type that the retailer accepts on the e-commerce channel must be
configured in Dynamics 365 Commerce when the system is set up. 'Customer
account' or 'On Account' payment is one payment method which needs to be
supported on the eCommerce channel especially the B2B e-commerce
channel. 

## Prerequisites

1.  Add Customer Account Payment method in Headquarters 

2.  Associate Customer Account Payment method to eCommerce Channel 

3.  Ensure that Customer has a 'Credit limit' enabled (In the navigation
    pane, go to Modules &gt; Retail and commerce &gt; Customers &gt; All
    customers.) 

## Setup eCommerce website to use 'Customer Account' payment method.

### Step 1 - Enable the Site setting for 'Customer Account' payment method

1.  In the eCommerce Site Builder Tool go to **Site Settings**

2.  Select the **Extensions** TAB on the bottom left corner

3.  In the list of extensions search for **Enable Customer account
    payments**

4.  There are 4 possible options for the site.

    -   Disabled for all customers : 'Does not allow any customer type
        to use 'Customer Account / Credit limit' for eCommerce.

    -   Enabled for B2B customers only : 'Only enables B2B customers to
        use the 'Customer Account' payment method in eCommerce.

    -   Enabled for B2C customers only : 'Only enables B2C customers to
        use the 'Customer Account' payment method in eCommerce.

    -   Enabled for all customers : 'Enables all customers to use the
        'Customer Account' payment method in eCommerce.

Note: The new 'site settings' will only be available after the
App.Settings.Jason file has been updated. Please follow this below
link: [*SDK and Module library
updates*](https://docs.microsoft.com/en-us/dynamics365/commerce/e-commerce-extensibility/sdk-updates)

1.  Save the changes and publish

### Step 2 - Enable the 'Customer Account' Payment method in the 'Checkout Page'

1.  Search for the **Checkout page** (based on your setup it may be
    in *Pages* or *Fragements* and edit the **Checkout** container.

2.  For the 'Checkout' contianer click **Add Module** and add a
    the **Customer Account** payment method module.



1.  Position the module using 'Move Up' / 'Move Down'

2.  Click **Finish Editing**

3. **Save and Publish** the site

### Step 3 - Confirmation

1.  On the eCommerce website - log in as the user type which was
    'Enabled'

2.  Add product and Checkout.

3.  In the Checkout page - you should see the new Payment method:
    'Customer Account'

# Troubleshooting

1.  Ensure the pre-requisites are met

2.  Ensure the Site settings and site is published.

3.  Ensure that the Credit limit for the customer is available in
    HeadQuarters in the Customer Form.

4.  If the Credit limit check is not mandatory - the customers can buy
    using customer account without any credit limit check

5.  Credit limit on eCommerce only shows the invoiced order balance (in
    some cases there may be a delay in updating the balance)

6.  If the credit balance has crossed and if the user has already
    purchased a product using customer account - based on the checkout
    flow the orders may not be invoiced.


