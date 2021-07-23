---
# required metadata

title: Select account groups for Chinese voucher types
description: This topic provides information about how to select account groups when setting up voucher types for China.
author: anasyash
ms.date: 07/22/2021
ms.topic: article
ms.prod: 
ms.technology: 


# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: China (PRC)
# ms.search.industry: 
ms.author: anasyash
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Select account groups for Chinese voucher types

[!include [banner](../includes/banner.md)]

This topic provides information about how to set up account groups when setting up voucher types for China.

## Enable the feature

1. Go to **Workspaces** > **Feature management**.
2. In the list, locate and select the feature, **Account groups selection for Chinese voucher types**, and then select **Enable now**. 
3. This feature introduces a new table where the voucher type setup is stored. To copy existing Chinese voucher type setup information to a new table, go to **System administration** > **Periodic tasks** > **Database** > **Consistency check**. Expand **Program** > **General ledger** and select **Restriction type for voucher**.
4. In the **Check/Fix** field, select **Check** to check whether there are settings in existing setup to copy to a new table.
5. In the **Check/Fix** field, select **Fix** to copy settings from an existing table to a new table.

## Set up voucher type

1. Go to **General ledger** > **Journal setup** > **Chinese voucher type** > **Voucher type**.
2. On the **Rules** FastTab, select the line with specific restriction.
3. On the **Impacted accounts** FastTab, select **Add** and set up the accounts for the selected rule.
   
    1. In the **Account type** field, select **Ledger**, **Customer**, **Vendor**, **Project**, **Fixed assets**, **Bank**.
    2. In the **Account code**, select **Account**, **Group**, or **All**. Note that the value **Group** is not available for **Ledger** account code.
    3. In the **Group number** field, select **Customer group**, **Vendor group**, **Project group**, **Fixed asset group**, or **Bank group** to match the value in the **Account type** field, if you selected **Group** in the **Account code** field.
    4. In the **Account number** field, select **Ledger account**, **Customer account**, **Vendor account**, **Project ID**, **Fixed asset number**, or **Bank account value** in the **Account type** field, if you selected **Table** in the **Account code** field.

For information about how to set up Chinese voucher types, see [Set up Chinese vouchers](tasks/set-up-chinese-vouchers.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
