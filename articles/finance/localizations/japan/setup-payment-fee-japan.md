---
title: Set up payment fee for Japan
description: Learn how to set up a payment fee for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: 
  - BankGroup
  - VendPaymFeeGroup_JP, VendTable, PaymFeeBankRule_JP, SysFieldLookUp, VendPaymFee, VendPaymModeFee, TaxGroupLookup
ms.custom: 
  - bap-template
---

# Set up payment fee for Japan

[!include [banner](../../includes/banner.md)]

This article explains how to set up a payment fee for Japan in Microsoft Dynamics 365 Finance.

The following procedures use the demo data company JPMF.

## Create a bank group

To create a bank group, follow these steps:

1. In Dynamics 365 Finance, go to **Cash and bank management \> Setup \> Bank groups**.
1. Select **New**.
1. In the **Bank groups** field, enter a value.
1. In the **Name** field, enter a value.
1. Expand the **General** section.
1. In the **Bank code** field, enter a value.
1. In the **Branch code** field, enter a value.
1. Select **Save**.

## Create a vendor payment fee group

To create a vendor payment fee group, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable \> Payment setup \> Vendor payment fee groups**.
1. Select **New**.
1. In the **Vendor payment fee group** field, enter a value. For example, enter "PaymFee".  
1. In the **Description** field, enter a value.
1. Select **Save**.

## Specify a payment fee group for a vendor

To specify a payment fee group for a vendor, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable \> Vendors \> All vendors**.
1. In the list, select the link in the selected row.
1. Select **Edit**.
1. Expand the **Payment** section.
1. In the **Vendor payment fee group** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row. For example, select **VendPayFee**.  
1. Select **Save**.

## Create bank rules for a payment fee

To create bank rules for a payment fee, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable \> Payment setup \> Bank rules for payment fee**.
1. Select **New**.
1. In the **ID** field, enter a value.
1. In the **Name** field, enter a value.
1. Expand the **General** section.
1. Select **Add**.
1. Add one or more filters to create the bank rule.  
1. In the **Third party bank group** field, select the drop-down button to open the lookup. Enter the vendor's bank criteria to filter results.  
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row. For example, select **Bank code**.  
1. In the **Company bank group** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. Repeat the steps to add criteria for the payment fee generation rule. The criteria in one bank rule are applied using "AND" logic.  
1. Select **Save**.

## Create a payment fee

To create a payment fee, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts payable \> Payment setup \> Payment fee**.
1. Select **New**.
1. In the **Fee ID** field, enter a value.
1. In the **Name** field, enter a value.
1. In the **Fee description** field, enter a value.
1. In the **Charge** field, select **Ledger**.
1. In the **Ledger account** field, enter a value.
1. In the **Payment fee account** field, enter a value.
1. In the **Journal type** field, select an option. For example, select **Vendor disbursement**.  
1. Select **Save**.
1. Select **Payment fee setup**.
1. In the **Groupings** field, select an option. For example, select **Group**.  
1. In the **Bank relation** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row. For example, select **0001_009**.  
1. In the **Vendor group type** field, select an option. If you select **Group**, it's easier to configure.  
1. In the **Vendor account/group** field, enter a value. For example, enter **VendPayFee**.  
1. In the **Method of payment** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row. For example, select **Bank**.  
1. In the **Bank rule ID for payment fee** field, enter a value. For example, enter **DiffBank**.  
1. Select the **General** tab.
1. In the **Payment currency** field, enter a value. For example, enter "JPY".  
1. In the **Minimum** field, enter a number.
1. In the **Percentage/Amount** field, select an option. For example, select **Amount**.  
1. In the **Fee amount** field, enter a number.
1. In the **Fee currency** field, enter a value. For example, enter "JPY".  
1. In the **Sales tax group** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. In the **Item sales tax group** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row. For example, select **Taxable**.  
1. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
