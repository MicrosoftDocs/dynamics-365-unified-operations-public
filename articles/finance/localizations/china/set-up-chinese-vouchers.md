---
title: Set up Chinese vouchers
description: This article describes how to set up Chinese vouchers using specific demo data in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/05/2025
ms.reviewer: johnmichalak
ms.search.region: China (PRC)
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerVoucherType_CN, HcmWorkerLookUp, LedgerParameters, LedgerPrintLayoutGroup_CN
ms.custom: 
  - bap-template
---

# Set up Chinese vouchers

[!include [banner](../../includes/banner.md)]

This article describes how to set up Chinese vouchers by using specific demo data in Microsoft Dynamics 365 Finance.

Chinese voucher numbers form the foundation for Chinese financial reporting. You must set them up before you post any financial transactions. You can set up the vouchers one at a time or use the Voucher type setup wizard.

The following procedures walk you through how to set up Chinese vouchers with specific demo data. This procedure uses the demo data company CNMF.

## Set up a Chinese voucher type

To set up a Chinese voucher type, follow these steps.

1. In Dynamics 365 Finance, go to **General ledger \> Journal setup \> Chinese voucher type \> Voucher type**.
1. Select **New**.
1. In the **Voucher type** field, enter a value.
1. In the **Voucher type number** field, enter a value. This value is used as the **Type ID** in the GB/T24589 export file.  
1. In the **Description** field, enter a value.
1. In the **Priority** field, enter a number. For financial vouchers such as posting sales invoices that are generated from source documents, if more than one voucher type matches according to the voucher type rule, the first priority voucher type is assigned. You can also set a voucher type as **Default**, which sets it as the default voucher type.  
1. In the **Number sequence code** field, enter or select a value.
1. In the **Print layout group** field, enter or select a value.
1. Enter the name of the person who is responsible for making this type of voucher. This name is used in the GB/T24589 export file, and should be for a person other than the person who can approve this type of voucher.  
1. Enter the name of the person who can approve this type of voucher. This name is used in the GB/T24589 export file, and should be for a person other than the person who can create this type of voucher.  
1. Select **Add**. Voucher type rules define the criteria for vouchers. Only transactions in a voucher that meet these criteria can be assigned to this voucher type and posted. In this example, only bank accounts and cash accounts are allowed in debit and credit sides for this **Cash type** voucher.  
1. In the **Restriction** field, select **All debits must include (one of the selected accounts)**.
1. Select **Add**.
1. In the **Main account** field, enter **100101**.
1. Select **Add**.
1. In the **Main account** field, enter **100102**.
1. Select **Add**.
1. In the list, mark the selected row.
1. In the **Main account** field, enter **100103**.
1. Select **Add**.
1. In the **Account type** field, select **Bank**.
1. In the **Main account** field, enter **CNYBANK**.
1. Select **Add**.
1. In the **Account type** field, select **Bank**.
1. In the **Main account** field, enter **USDBANK**.
1. Select **Add**.
1. In the **Account type** field, select **Bank**.
1. In the **Main account** field, enter **HKDBANK**.
1. Select **Add**.
1. In the **Restriction** field, select **All credits must include (one of the selected accounts)**.
1. Select **Add**.
1. In the **Main account** field, enter **100101**.
1. Select **Add**.
1. In the **Main account** field, enter **100102**.
1. Select **Add**.
1. In the **Main account** field, enter **100103**.
1. Select **Add**.
1. In the **Account type** field, select **Bank**.
1. In the **Main account** field, enter **CNYBANK**.
1. Select **Add**.
1. In the **Account type** field, select **Bank**.
1. In the **Main account** field, enter **USDBANK**.
1. Select **Add**.
1. In the **Account type** field, select **Bank**.
1. In the **Main account** field, enter **HKDBANK**.
1. Select **Save**.

## Set up more parameters

To set up more parameters, follow these steps.

1. In Dynamics 365 Finance, go to **General ledger \> Ledger setup \> General ledger parameters**. On the **General ledger parameters** page, first enable **Chinese voucher**, then allow duplicate vouchers in the fiscal year. Chinese vouchers must be renumbered starting from "1" for each fiscal period.  
1. In the **Check for voucher used** field, select an option.

## Set up the print layout

To set up the print layout, follow these steps.

1. In Dynamics 365 Finance, go to **General ledger \> Journal setup \> Chinese voucher type \> Print layout**.
1. Select **New**.
1. In the **Print layout group** field, enter a value.
1. In the **Description** field, enter a value.
1. Select **Add**.
1. In the **Print layout code** field, select an option.
1. Select **Add**.
1. In the **Print layout code** field, select an option.
1. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
