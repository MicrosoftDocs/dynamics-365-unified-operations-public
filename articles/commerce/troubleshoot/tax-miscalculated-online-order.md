---
# required metadata

title: Taxes on online orders are incorrectly calculated
description: This topic provides troubleshooting guidance that can help when taxes on online orders are incorrectly calculated, or when the tax group on the sales line isn't correctly set.
author: Reza-Assadi
ms.date: 02/16/2022
ms.topic: Troubleshooting
ms.prod: 
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

This topic provides troubleshooting guidance that can help when taxes on online orders are incorrectly calculated, or when the tax group on the sales line isn't correctly set.

## Description

When an e-commerce order is placed, the taxes are incorrectly calculated, or the tax group on the sales line is incorrectly set.

## Resolution

### Configure general sales tax groups in Commerce headquarters

To configure general sales tax groups in Commerce headquarters, follow these steps.

1. Go to **Tax \> Indirect taxes \> Sales tax \> Sales tax group**.
1. In the left navigation pane, select the tax group to configure.
1. On the **Retail destination based tax** FastTab, configure the taxes for the sales tax group.

> [!NOTE]
> For shipping that doesn't include sales tax that is determined by the customer's address, the delivery address of the line and the destination-based taxes that are configured for the tax group determine the tax group. For more information, see [Set up taxes for online stores based on destination](/dynamicsax-2012/appuser-itpro/set-up-taxes-for-online-stores-based-on-destination).

### Configure the sales tax for a retail store in Commerce headquarters

To configure the sales tax for a retail store in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channels \> All stores**.
1. Select the store to configure sales tax for.
1. On the **General** FastTab, in the **Sales tax** section, configure the sales tax information for the store.

> [!NOTE]
> For product pickup from a store, the tax group comes from the store that is selected for pickup. For more information, see [Set other tax options for stores](/dynamicsax-2012/appuser-itpro/set-other-tax-options-for-stores).

### Configure the sales tax for a customer's address in Commerce headquarters

To configure the sales tax for a customer's address in Commerce headquarters, follow these steps.

1. Go to **Accounts receivable \> Customers \> All customers**.
1. Select the customer to configure sales taxes for.
1. On the **Addresses** FastTab, select the address to configure sales taxes for, select **More options**, and then select **Advanced**.
1. On the **General** FastTab, select the **Tax group**.
1. In the **Sales tax** field, select the appropriate value.

> [!NOTE]
> For shipping that involves sales tax on the customer's address, the delivery address of the line determines the tax group for the line. If the customer is shipping to an existing address that has a tax group that is already configured, the existing tax group will be used. By default, addresses don't have a tax group when they are created.

## Additional resources

[Configure sales tax for online orders](../sales-tax-config.md)
