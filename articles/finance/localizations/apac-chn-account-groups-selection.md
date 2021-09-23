---
# required metadata

title: Select account groups for Chinese voucher types
description: This topic explains how to select account groups when you set up voucher types for China.
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

This topic explains how to select account groups when you set up voucher types for China.

## Enable the feature

1. Go to **Workspaces** \> **Feature management**.
2. In the list, find and select the feature that is named **Account groups selection for Chinese voucher types**. Then select **Enable now**.
3. The feature introduces a new table that stores the setup for voucher types. To copy information about the setup of existing Chinese voucher types to a new table, go to **System administration** \> **Periodic tasks** \> **Database** \> **Consistency check**. Then expand **Program** \> **General ledger**, and select **Restriction type for voucher**.
4. In the **Check/Fix** field, select **Check** to determine whether there are any settings in the existing setup to copy to a new table.
5. In the **Check/Fix** field, select **Fix** to copy settings from the existing table to a new table.

## Set up voucher type

1. Go to **General ledger** \> **Journal setup** \> **Chinese voucher type** \> **Voucher type**.
2. On the **Rules** FastTab, select the line that has the specific restriction.
3. On the **Impacted accounts** FastTab, select **Add**.

    You must now set up the accounts for the selected rule.

4. In the **Account type** field, select **Ledger**, **Customer**, **Vendor**, **Project**, **Fixed assets**, or **Bank**.
5. In the **Account code** field, select **Table**, **Group**, or **All**. Note that the value **Group** isn't available for the **Ledger** account type.
6. Follow one of these steps, depending on the value that you selected in the **Account code** field:

    - If you selected **Group**: In the **Group number** field, select customer group, vendor group, project group, fixed asset group, or bank group, based on the account type that you selected in the **Account type** field.
    - If you selected **Table**: In the **Account number** field, select ledger account, customer account, vendor account, project ID, fixed asset number, or bank account value, based on the account type that you selected in the **Account type** field.

For information about how to set up Chinese voucher types, see [Set up Chinese vouchers](tasks/set-up-chinese-vouchers.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
