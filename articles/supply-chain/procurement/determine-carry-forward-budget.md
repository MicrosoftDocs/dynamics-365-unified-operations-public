---
# required metadata

title: Define what happens with purchase order carry-forward budget
description: 
author: TaylorVH 
ms.date: 2/01/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 267074
ms.assetid: 1d293b3a-2fa2-418d-9347-78c2809d67fe
ms.search.region: global
# ms.search.industry: 
ms.author: v-savanh
ms.dyn365.ops.version: Version 1611
ms.search.validFrom: 2022-02-01

---

# Define what happens with purchase order carry-forward budget

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes what happens with purchase order carry-forward budget when purchase orders are cancelled or reduced. You can configure the system so that the associated budget is moved to the new year when carrying forward purchase orders from one year to another. This process creates a budget register entry in the new year that represents the remaining balance of the purchase order. There are two ways to handle the carry-forward budget when a purchase order is cancelled or reduced. The carry-forward budget can remain as created or it can be automatically adjusted to remove the cancelled or reduced amount. The automatic budget adjustment is controlled by settings found on the fund records in General ledger. Only purchase order lines with distributions that include a fund are available for automatic budget adjustment. The automatic budget adjustment takes place when the purchase order is finalized.
 
The following setup must be completed for all funds where you want to define this behavior.
 
1. Open **General ledger > Chart of accounts > Funds > Funds**.
2. For the Purchase order year-end process, the **Override selected year-end option** must be set to **Yes**.
3. For Carry-forward budget status, the **Reinstate the budget when a carry-forward purchase order is cancelled or reduced** can be set to the following values.
   - No Creates a budget register entry for the purchase order remaining balance that is cancelled or reduced.
   - Yes Allows the purchase order to be cancelled or reduced without the creation of a budget register entry. This results in the carry-forward budget remaining available for consumption by additional documents.

## Reduce carry-forward budget when an Invoice unit price is reduced
 
When a carry-forward purchase order is invoiced with a reduced price there is a price variance. Posting the invoice will reduce the purchase order encumbrance by the amount of the price variance. By default, the carry-forward budget is not reduced in this scenario. That leaves the remaining carry-forward budget behind for the amount of the price variance. You can automatically remove remaining carry-forward budget in this scenario using the feature, **Reduce carry-forward budget when an Invoice unit price is reduced**. This feature can be set up to create a budget a register entry to remove excess carry-forward budget.
 
Once the feature is enabled, the same fund setup that was defined earlier will be used. This setup is defined below and must be completed for any funds that you want to be able to carry budget amounts forward when an invoice price is reduced.
 
1. Open **General ledger > Chart of accounts > Funds > Funds**.
2. For the Purchase order year-end process, set the **Override selected year-end option** field to **Yes**.
3. For Carry-forward budget status, the **Reinstate the budget when a carry-forward purchase order is cancelled or reduced** can be set to the following values.
   - No creates a budget register entry against the purchase order for the price variance reduction amount.
   - Yes allows the invoice unit price reduction without the creation of a budget register entry. This results in the carry-forward budget remaining available for consumption by additional documents.

