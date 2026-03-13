---
title: Import ISO20022 files
description: Learn how to import payment files of the ISO 20022 camt.054 and pain.002 formats into Microsoft Dynamics 365 Finance, including prerequisites.
author: kailiang
ms.author: kailiang
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/06/2026
ms.reviewer: johnmichalak
ms.search.region: Austria, Belgium, Czech Republic, Denmark, Estonia, Finland, France, Germany, Hungary, Italy, Latvia, Lithuania, Norway, Poland, Spain, Sweden, Switzerland, United Kingdom
ms.search.validFrom: 2017-06-01
ms.search.form: CustPaymMode, CustBankAccounts, VendPaymMode, VendBankAccounts
---

# Import ISO20022 files

[!include [banner](../../includes/banner.md)]

You can import payment files that use the following formats:

- **ISO 20022 camt.054 credit advice** – Import incoming payments from a file in this format into the Customer payment journal.
- **ISO 20022 pain.002 status return** and **ISO 20022 camt.054 debit advice** – Import return files in these formats into the AP Payment transfer journal.

## Prerequisites for importing the camt.054 credit advice file

To import bank notification messages in the camt.054.001.002 format into the Customer payment journal, complete the following prerequisites.

1. Import the **ISO20022 camt.054** Electronic reporting (ER) configuration from Microsoft Dynamics Lifecycle Services (LCS). Then, on the **Customer method of payment** page, in the **Import format configuration** field, select that configuration. For more information, see [File formats for methods of payment](emea-select-file-formats-for-the-method-of-payments.md).
1. On the **All customers** page, enter a name and organization number for each customer.
1. On the **Customer bank account** page, set up a customer bank account record by entering the following information: IBAN or bank account number, and SWIFT code or routing number.
1. On the **Bank accounts** page, set up legal entity bank accounts by entering the following information: IBAN or bank account number, SWIFT code or routing number, currency, and address.

   > [!NOTE]
   > If you plan to use Advanced bank reconciliation, on the **Reconciliation** FastTab, set the **Advanced bank reconciliation** option to **Yes**. If you plan to reconcile unposted imported payments, set the **Use bank statements as confirmation of electronic payments** option to **Yes**.

1. (Optional) On the **Transaction code mapping** page, set up the mapping between bank transaction codes in the file and bank transaction types.
1. If the file contains transaction charges that you want to post together with the incoming payment, create a payment fee on the **Customer payment fee** page. Then, on the **Methods of payment** page, associate the payment fee with the bank account in the payment fee setup.
1. If you import ESR payments and they contain ISR references (applicable for legal entities in Switzerland), complete the following setup:

- In the **Customer payments, account lengths** field, enter the length of the customer code that you use in ISR references or for automatic identification of the customer.
- Make sure that the customer number and invoice number (number sequences) contain only digits. They must contain no other characters. The invoice number must not have leading zeros.
- Enter the ESR, BESR, and routing number for the legal entity bank account. For more information, see [ESR customer payments import](../switzerland/emea-che-esr-customer-payments-import.md), because similar settings are required.

## Import the camt.054 credit advice file into the Customer payment journal

1. On **Customer payment journal lines**, select **Functions** > **Import payments**.
1. Select the method of payment that has the required settings for the ISO 20022 camt.054 format.
1. Enter the required parameters and the path of the file, and then select **OK**. The file is imported.

## Prerequisites for importing files in the pain.002 status return and camt.054 debit advice formats into the AP Payment transfer journal

You must complete the following prerequisites to import bank messages in the following ISO20022 formats to the **Vendor payment transfer** page: pain.002.001.003 status return messages and camt.054.001.002 debit advice.

1. Import the **ISO20022 camt.054** and **ISO20022 pain.002** ER configurations from LCS.
1. On the **Vendor method of payment** page, in the **Return format configuration** and **Return format secondary configuration** fields, select the ER configurations that you imported. You must activate the generic electronic return format for the selected method of payment.
1. On the **Return format status mapping** page, set up the mapping of status codes between pain.002 statuses and Vendor payment journal statuses.

    Here's an example of a status setup.

    Return status | Payment status
    --------------|---------------
    RJCT          | Rejected
    ACCP          | Accepted
    ACSP          | Received

1. On the **Return format error codes** page, set up pain.002 error codes and descriptions in accordance with external ISO20022 status reason codes.

    Here's an example of part of an error code setup.

    Code | Name
    -----|-----
    AC01 | IncorrectAccountNumber
    AC02 | InvalidDebtorAccountNumber
    AC03 | InvalidCreditorAccountNumber
    AC04 | ClosedAccountNumber
    AC05 | ClosedDebtorAccountNumber
    AC06 | BlockedAccount

1. If the camt.054 file contains transaction charges that you want to post together with the incoming payment, create a payment fee on the **Vendor payment fee** page. Then, on the **Methods of payment** page, associate the payment fee with the bank account in the payment fee setup.

## Import the pain.002 status return or camt.054 debit advice files into the Vendor payment journal

1. Open the **Payment transfers** page in the Accounts Payable menu.
1. On the **Payment transfers** page, select **Return file - vendor**.
1. Select the method of payment that has the required settings for ISO20022 files, and then select **OK**.
1. Select the file format that you plan to import, and then select **OK**.
1. Specify the required parameters and the path of the file, and then select **OK**.

If you import the pain.002 file, the status of vendor payment lines is updated based on the information in the imported file.

If you import the camt.054 file, specify the following additional parameters:

- **Fee ID** – Enter the Fee ID to define new payment fee lines. The process creates these lines on the Vendor payment journal line if a charge amount is present in the camt.054 file.
- **New journal name** and **New journal description** – Enter the name and description of the journal that processed transactions are transferred to. After the transfer, new voucher numbers are assigned in the new journal.
- **Import direct debit transactions** – Set this option to **Yes** if you want to import outgoing direct debits into the Vendor payment journal.
- **Journal name** – Define a new journal name for the imported direct debit transactions.
- **Settle transactions** – Set this option to **Yes** if you want to settle imported vendor payments with invoices that are found in the system.

You can view the imported information on the **Payment transfers** page.

## Additional details

When you import a format configuration from LCS, you import the whole configuration tree, which means that the import includes the Model and Model mapping configurations.
In the Payment model starting from version 8, the solution tree places the mappings in separate ER configurations (Payment model mapping 1611, Payment model mapping to destination ISO20022, and so on). Under one model (Payment model), you can find many different payment formats. Therefore, separate mapping handling is key for easy solution maintenance.
For example, consider this scenario: you use ISO20022 payments to generate credit transfer files, and then you import the return messages from the bank. In this scenario, use the following configurations:

- **Payment model**
- **Payment model mapping 1611** – use this mapping to generate the export file
- **Payment model mapping to destination ISO20022** – this configuration includes all mappings that you use to import the data (“to destination” mapping direction)
- **ISO20022 Credit transfer** – this configuration includes a format component that's responsible for export file generation (pain.001) based on the Payment model mapping 1611, as well as a format to model mapping component which you use together with Payment model mapping to destination ISO20022 to register exported payments in the system for further import purposes (import in CustVendProcessedPayments technical table)
- **ISO20022 Credit transfer (CE)**, where CE corresponds to country/region extension – derived format to the ISO20022 Credit transfer with the same structure and with certain country/region-specific differences
- **Pain.002** – use this format together with the Payment model mapping to destination ISO20022 in order to import the pain.002 file into vendor payments transfers journal
- **Camt.054** – use this format together with the Payment model mapping to destination ISO20022 to import the camt.054 file into vendor payments transfers journal. The same format configuration is used in customer payments import functionality, but the different mapping is used in the Payment model mapping to destination ISO20022 configuration.

For more information about Electronic reporting, see [Electronic reporting overview](../../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

## Additional resources

[Create and export vendor payments using ISO20022 payment format](create-export-vendor-payments-iso20022-payment-format.md)

[Import ISO20022 credit transfer configuration](import-iso20022-credit-transfer-configuration.md)

[Import ISO20022 direct debit configuration](import-iso20022-direct-debit-configuration.md)

[Set up company bank accounts for ISO20022 credit transfers](set-up-company-bank-accounts-iso20022-credit-transfers.md)

[Set up company bank accounts for ISO20022 direct debits](set-up-company-bank-accounts-iso20022-direct-debits.md)

[Set up customers and customer bank accounts for ISO20022 direct debits](set-up-bank-accounts-iso20022-direct-debits.md)

[Set up method of payment for ISO20022 credit transfer](set-up-method-payment-iso20022-credit-transfer.md)

[Set up method of payment for ISO20022 direct debit](setup-method-payment-iso20022-direct-debit.md)

[Set up vendors and vendor bank accounts for ISO20022 credit transfers](set-up-vendor-iso20022-credit-transfers.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
