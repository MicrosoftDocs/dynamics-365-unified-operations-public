--- 
title: Create and export vendor payments using ISO20022 payment format
description: Learn how to create payment lines in the vendor payment journal and generate a vendor payment file using ISO2022 Credit transfer example. 
author: kailiang
ms.author: kailiang
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/06/2026
ms.reviewer: johnmichalak  
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerJournalTable, LedgerJournalTransVendPaym, SysQueryForm, VendPaymProposalEdit, BankAccountTableLookUp
---

# Create and export vendor payments using ISO20022 payment format

[!include [banner](../../includes/banner.md)]

Complete the following steps to create payment lines in the vendor payment journal and generate a vendor payment file using ISO 20022 Credit transfer example.

1. Go to **Accounts payable** > **Payments** > **Payment journal** and select **New**.
1. In the **Name** field, enter or select a value.
1. Select **Lines** > **Payment proposal** > **Create payment proposal**.
1. Expand the **Records to include** section and select **Filter**.
1. In the list, select the row for the **Vendors table** and **Vendor account field**.
1. In the **Criteria** field, enter or select a value. You can apply any criteria for selecting vendor transactions to pay.
1. Select **OK** and select **OK** again.
1. Select **Create payments**.
1. Select **Generate payments** to generate the ISO 20022 payment file.
1. In the **Method of payment** field, enter or select a value.
1. In the **File name** field, enter a value. You can use ISO 20022 credit transfer and other vendor payment formats to generate payments in other currencies.
1. In the **Bank account** field, enter or select a value.

> [!NOTE]
> - If you enable the feature **Display payee name for customer/vendor payment information**, you can define a payee name on the customer and vendor bank account details. Once defined, the payee name appears in customer and vendor payment journals, payment proposals, and generated payment files. The payee name can be different from the name of the customer or vendor defined on the master data, and it should align with banking requirements to ensure accurate identification of payment recipients.
> - This enhancement improves compliance and flexibility for SEPA credit transfers by introducing support for an alternative payee name linked to IBAN. It ensures accurate mapping of payee details in payment transactions and exported XML files.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
