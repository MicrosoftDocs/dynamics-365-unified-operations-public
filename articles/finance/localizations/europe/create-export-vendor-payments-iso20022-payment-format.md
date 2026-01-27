--- 
title: Create and export vendor payments using ISO20022 payment format
description: Learn how to create payment lines in the vendor payment journal and generate a vendor payment file using ISO2022 Credit transfer example. 
author: kailiang
ms.author: kailiang
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 08/01/2023
ms.reviewer: johnmichalak  
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerJournalTable, LedgerJournalTransVendPaym, SysQueryForm, VendPaymProposalEdit, BankAccountTableLookUp
ms.dyn365.ops.version: Version 7.0.0 
---

# Create and export vendor payments using ISO20022 payment format

[!include [banner](../../includes/banner.md)]

Complete the following steps to create payment lines in the vendor payment journal and generate a vendor payment file using ISO2022 Credit transfer example.

1. Go to **Accounts payable** > **Payments** > **Payment journal** and select **New**.
2. In the **Name** field, enter or select a value.
3. Select **Lines** > **Payment proposal** > **Create payment proposal**.
4. Expand the **Records to include** section and select **Filter**.
5. In the list, select the row for the **Vendors table** and **Vendor account field**.
6. In the **Criteria** field, enter or select a value. You can apply any criteria for selecting vendor transactions to pay.
7. Select **OK** and select **OK** again.
8. Select **Create payments**.
9. Select **Generate payments** to generate the ISO20022 payment file.
10. In the **Method of payment** field, enter or select a value.
11. In the **File name** field, enter a value. ISO20022 credit transfer as well as other vendor payment formats can be used to generate payments in other currencies.
12. In the **Bank account** field, enter or select a value.

>[!NOTE]
>If the feature **Display payee name for customer/vendor payment information** is enabled, the users have an option to define a payee name defined on the customer and vendor bank account details. Once defined, the payee name is visible in customer and vendor payment journals, payment proposals, and generated payment files. The payee name can be different from the name of the customer/vendor defined on the master data, and should align with banking requirements, ensuring accurate identification of payment recipients.
>This enhancement improves compliance and flexibility for SEPA credit transfers by introducing support for an alternative payee name linked to IBAN. It ensures accurate mapping of payee details in payment transactions and exported XML files.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
