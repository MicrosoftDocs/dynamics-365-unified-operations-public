---
# required metadata

title: Dual use
description: This topic describes how to keep track of products identified as dual use, store certificate numbers for each relevant product and destination country, and print valid certificate numbers on relevant invoices, packing slips, and/or sales orders.
author: dasani-madipalli
manager: tfehr
ms.date: 07/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: damadipa
ms.search.validFrom: 2020-07-01
ms.dyn365.ops.version: Release 10.0.13
---

# Dual use

Some companies have products that can be used for more than one purpose. Specifically, these companies ship products that can both be used for civilian and military purposes. For example, a chemical could be both used as a fertilizer or and explosive weapon. These products are called dual use goods and different nations have specific policies and regulations for products that fall under this category. So keeping track of different policies is important if a company is involved in foriegn trade and ships dual use products.

The dual use feature helps companies keep track of products identified as dual use, stores certificate numbers for each relevant product and destination country, and can print valid certificate numbers on relevant invoices, packing slips, and/or sales orders. 

This feature helps to ensure that your products alway ship with up-to-date certifications. Consider the following scenario:

1. Your **Dual use country setup** page indicates that shipments to France require a certification.
1. The **Released product details** page for product X-100 indicates that it is a dual use product. The code/category/group/regime will indicate which export control classification the product belongs to.
1. Your **Dual use certificates** page includes a certificate for product X-100 when shipped to France, which expires on January 1, 2020
1. On June 17, 2020, you create create a sales order for a customer company based in France, and the order includes product X-100.
1. When you save the sales order, the system checks the following:
    - Does the order include any products that are dual use goods? <!-- KFM: Is this checked? If so, what effect does the code/category/group/regime have? D: If it the answer to all of these questions is yes then it will show a warning message -->
    - Does the destination country require dual use certificates?
    - Does a valid certificate exist for each dual use product for the destination country?
1. Because the order includes item X-100 being shipped to france, but the certificate is expired, the following warning is shown: "Dual use certificates for one or more dual use items in this sales order aren't valid. Do you want to proceed with the confirmation?"

This topic describes how to make each of the settings required to set up dual use products and support the previous scenario.

## Store dual use requirements for each relevant country

Different countries have different requirements for dual use products. Use the **Dual use country setup** page to keep track of which countries require a certificate and which ones don't. The information you set here will get checked when you create sales orders and you'll be reminded to provide the necessary certifications.

To set this information, go to **Product information management \> Setup \> Product compliance \> Dual use products \> Dual use country setup**. Then select an existing country setup to edit it, or select **New** on the Action Pane to create a new one, and make the following settings for the new or selected country setup:

| **Setting** | **Description** |
| --- | --- |
| **Country/region** | Select the country you are tracking requirements for. |
| **Certificate Required** | Select this check box for countries that require a certification for dual use products. Clear this check box for countries that don't require this certification. |

## Create dual use categories

Dual use items often need to be categorized according to their export control classification number (ECCN). The ECCN is an alphanumeric code that categorizes items based on commodity, technology, and so on.

The **Dual use categories** page helps you make a list of those categorizations that you  use for reporting purposes. To set this up, go to **Product information management \> Setup \> Product compliance \> Dual use products \> Dual use categories**. Then select an existing category to edit it, or select **New** on the Action Pane to create a new one, and make the following settings for the new or selected category:

| **Setting** | **Description** |
| --- | --- |
| **Dual use code** | This refers to the category value of the ECCN|
| **Dual use category** |  This refers to the sub-category value of the ECCN|
| **Dual use group** |  This value specifies the group of the originating regime for the ECCN|
| **Dual use regime** | This value reflects the originating regime value of the ECCN|

## Apply dual use categories to products

To identify a product as a dual use good and apply a dual use category to it:

1. Go to **Product information management \> Products \> Released products**.
1. Select or create the product to open its **Released product details** page.
1. Expand the **Foreign trade** FastTab.
1. Set **Dual use products** to **Yes** to identify the current product as a dual use good. <!-- KFM: Is it too late to change the labels for this feature? There are multiple grammar and capitalization mistakes in them. D: yeah. we could have a work item to change it in the future-->
1. Set the **Dual use code** to the code that applies for the current product (as defined on the **Dual use categories** page).

This setup is helpful as it gets checked when you create a sales order.
## Set up dual use certificates

Use the **Dual use certificates** page to set up and manage the required dual use certificates for each product and country. You can track each certificate's details, such as country and dates of validity, and set options for where to print this information. (such as invoice, packing slip, and/or sales order). This setup is checked when you create a sales order.

To do this, go to **Product information management \> Setup \> Product compliance \> Dual use products \> Dual use certificates**. Then select an existing certificate to edit it, or select **New** on the Action Pane to create a new one, and make the following settings for the new or selected certificate:

| **Setting** | **Description** |
| --- | --- |
| **Item number** | Select the item number of the dual use product where this certificate applies. |
| **Country/region** | The destination country or region where you must use this certificate. |
| **Certificate number** | The number on the certificate issued to the vendor/customer |
| **Effective** | Select the first date on which the current certificate is valid.|
| **Expiration** | Select the last date on which the current certificate is valid. |
| **Print on invoice** | Select this check box to print this certificate number on invoices. <!-- KFM: All invoices, or just those addressed to the specified country within the specified date range? D: the latter--> |
| **Print on packing slip** | Select this check box to print this certificate number on  packing slips. <!-- KFM: All slips, or just those addressed to the specified country within the specified date range? D: the latter -->  |
| **Print on sales order** | Select this check box to print this certificate number on  sales orders.<!-- KFM: All orders, or just those addressed to the specified country within the specified date range? the latter --> |
