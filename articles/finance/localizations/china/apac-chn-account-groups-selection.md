---
title: Select account groups for Chinese voucher types
description: Learn how to select account groups when you set up voucher types for China, including a step-by-step process for enabling the feature for selecting account groups.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 12/05/2025
ms.reviewer: johnmichalak
ms.search.region: China (PRC)
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
---

# Select account groups for Chinese voucher types

[!include [banner](../../includes/banner.md)]

This article explains how to select account groups when you set up voucher types for China.

## Enable the feature

1. Go to **Workspaces** \> **Feature management**.
1. In the list, find and select the feature named **Account groups selection for Chinese voucher types**. Then select **Enable now**.
1. The feature introduces a new table that stores the setup for voucher types. To copy information about the setup of existing Chinese voucher types to a new table, go to **System administration** \> **Periodic tasks** \> **Database** \> **Consistency check**. Then expand **Program** \> **General ledger**, and select **Restriction type for voucher**.
1. In the **Check/Fix** field, select **Check** to determine whether there are any settings in the existing setup to copy to a new table.
1. In the **Check/Fix** field, select **Fix** to copy settings from the existing table to a new table.

## Set up voucher type

1. Go to **General ledger** \> **Journal setup** \> **Chinese voucher type** \> **Voucher type**.
1. On the **Rules** FastTab, select the line that has the specific restriction.
1. On the **Impacted accounts** FastTab, select **Add**.
   You must now set up the accounts for the selected rule.
1. In the **Account type** field, select **Ledger**, **Customer**, **Vendor**, **Project**, **Fixed assets**, or **Bank**.
1. In the **Account code** field, select **Table**, **Group**, or **All**. The value **Group** isn't available for the **Ledger** account type.
1. Follow one of these steps, depending on the value that you selected in the **Account code** field:
   - If you selected **Group**: In the **Group number** field, select customer group, vendor group, project group, fixed asset group, or bank group, based on the account type that you selected in the **Account type** field.
   - If you selected **Table**: In the **Account number** field, select ledger account, customer account, vendor account, project ID, fixed asset number, or bank account value, based on the account type that you selected in the **Account type** field.

For information about how to set up Chinese voucher types, see [Set up Chinese vouchers](set-up-chinese-vouchers.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
