---
# required metadata

title: Taxes on online orders are incorrectly calculated
description: This topic provides troubleshooting guidance for when taxes on online orders are calculated incorrectly or the tax group on the sales line isn't set correctly. 
author: Reza-Assadi
manager: AnnBe
ms.date: 02/24/2021
ms.topic: Troubleshooting
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
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

This topic provides troubleshooting guidance for when taxes on online orders are calculated incorrectly or the tax group on the sales line isn't set correctly.

## Description

When placing an e-commerce order, the taxes are calculated incorrectly or the tax group on the sales line is set incorrectly.

## Resolution

### Configure the sales tax for a retail store in Commerce headquarters

To configure the sales tax for a retail store in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channels \> All stores**.
1. Select the store that you want to configure sales tax for.
1. In the **Sales tax** section of the **General** FastTab, configure the sales tax information for the store.

> [!NOTE]
> For product pickup from a store, the tax group comes from the store selected for pickup. For more information, see [Set other tax options for stores](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-other-tax-options-for-stores).

### Configure the sales tax for the customer's address in Commerce headquarters

To configure the sales tax for a customer's address in Commerce headquarters, follow these steps.

1. Go to **Accounts receivable \> Customers \> All customers**.
1. Select the customer that you want to configure sales taxes for.
1. On the **Addresses** FastTab, select the address that you want to configure sales taxes for, select **More options**, and then select **Advanced**.
1. On the **General** FastTab, select the **Tax group**.
1. For **Sales tax**, select the appropriate value.

> [!NOTE]
> For shipping with a sales tax on the customer's address, the delivery address for the line determines the tax group for the line. If the customer is shipping to an existing address that has a tax group that's already configured, the existing tax group will be used. By default, addresses aren't created with a tax group.

### Configure general sales tax groups in Commerce headquarters

To configure general sales tax groups in Commerce headquarters, follow these steps.

1. Go to **Tax \> Indirect taxes \> Sales tax \> Sales tax group**.
1. In the left navigation pane, select the tax group that you want to configure.
1. On the **Retail destination based tax** FastTab, configure the taxes for the sales tax group.

> [!NOTE]
> For shipping without a sales tax on the customer's address, the tax group is defined using the delivery address of the line and the
destination-based taxes configured for the tax group. For more information, see [Set up taxes for online stores based on destination](https://docs.microsoft.com/dynamicsax-2012/appuser-itpro/set-up-taxes-for-online-stores-based-on-destination).

## Additional resources

[Configure sales tax for online orders](../sales-tax-config.md)
