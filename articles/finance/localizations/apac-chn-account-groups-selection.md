---
# required metadata

title: Account groups selection for Chinese voucher types
description: This feature allows you to select accounts groups when setting up voucher types for China.
author: AKroshkina
ms.date: 07/22/2021
ms.topic: article
ms.prod: 
ms.technology: 

---
# Account groups selection for Chinese voucher types
This feature allows you to select accounts groups when setting up voucher types for China.

## Enable the feature

1.  Enable the feature in the **Workspaces &gt; Feature management**.
2.  This introduces a new table where voucher type setup is stored. To copy existing Chinese voucher type setup information to a new table, go to **System administration &gt; Periodic tasks &gt; Database &gt; Consistency check**. Expand **Program &gt; General ledger** and select **Restriction type for voucher**.
3.  Select **Check** in the **Check/Fix** field to check whether there are settings in existing setup to copy to a new table.
4.  Select **Fix** in the **Check/Fix** field to copy settings from an existing table to a new table.

## Set up voucher type

1.  Go to **General ledger &gt; Journal setup &gt; Chinese voucher type &gt; Voucher type**.
2.  Under the **Rules** FastTab, select the line with specific restriction.
3.  Under the **Impacted accounts** FastTab, click **Add** and set up the accounts for the selected rule:
   
    -   In the **Account type** field, select **Ledger**, **Customer**, **Vendor**, **Project**, **Fixed assets**, **Bank**.
    -   In the **Account code**, select **Account**, **Group**, or **All**. Note that the value **Group** is not available for **Ledger** account code.
    -   In the **Group number** field, select **Customer group**, **Vendor group**, **Project group**, **Fixed asset group**, or **Bank group** to match the value in the **Account type** field, if you selected **Group** in the **Account code** field.
    -   In the **Account number** field, select **Ledger account**, **Customer account**, **Vendor account**, **Project ID**, **Fixed asset number**, or **Bank account value** in the **Account type** field, if you selected **Table** in the **Account code** field.

For details about how to set up Chinese voucher types, see [*Set up Chinese vouchers*](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/tasks/set-up-chinese-vouchers).
