---
# required metadata

title: Taxes on online orders are incorrectly calculated
description: This topic provides a resolution if taxes on online orders are calculated incorrectly or the tax group on the sales line isn't set correctly. 
author: Reza-Assadi
manager: AnnBe
ms.date: 02/17/2021
ms.topic: Troubleshooting
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: rassadi
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.18

---

# Taxes on online orders are incorrectly calculated

[!include [banner](../../includes/banner.md)]

## Description
When placing an e-commerce order, the taxes are calculated incorrectly or the tax group on the sales line is set incorrectly.

## Resolution

### Configure the sales tax for the retail store

For pickup in a store, the tax group comes from the store that's selected for pickup. Refer to the [Set other tax options for stores](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-other-tax-options-for-stores) article for details.

1. Go to Dynamics 365 Commerce headquarters.

1. Go to **Retail and Commerce > Channels > Stores > All stores**.

1. Select the store that you want to configure sales tax for.

1. On the **General** tab, in the **Sales tax** section, configure the tax information for the store.

### Configure the sales tax for the customer's address 

For shipping with a sales tax on the customer's address, the delivery address for the line determines the tax group for the line. If the customer is shipping to an existing address that has a tax group that's already configured, the existing tax group will be used. By default, addresses aren't created with a tax group.

1. Go to Dynamics 365 Commerce headquarters.

1. Go to **Accounts receivable > Customers > All customers**.

1. Select the customer that you want to configure sales taxes for.

1. On the **Addresses** tab, select the address that you want to configure sales taxes for, select **More options**, and then select **Advanced**.

1. On the **General** tab, select the **Tax group**.

1. In the **Sales tax** field, select the appropriate value.

### Configure general sales tax groups

For shipping without a sales tax on the customer's address, the tax group is defined using the delivery address of the line and the
destination-based taxes configured for the tax group. Refer to the [Set up taxes for online stores based on destination](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-up-taxes-for-online-stores-based-on-destination) article for details.

1. Go to Dynamics 365 Commerce headquarters.

1. Go to **Tax > Indirect taxes > Sales tax > Sales tax group.**

!. Select the tax group on the left that you want to configure.

1. In the **Retail destination based tax** section, configure the taxes for the sales tax group.

## Additional Resources
- [Configure sales tax for online orders](../sales-tax-config.md)
