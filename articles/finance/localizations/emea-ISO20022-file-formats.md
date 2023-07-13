---
title: Import ISO20022 files
description: This article explains how to import payment files of the ISO 20022 camt.054 and pain.002 formats into Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.date: 07/27/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Austria, Belgium, Czech Republic, Denmark, Estonia, Finland, France, Germany, Hungary, Italy, Latvia, Lithuania, Norway, Poland, Spain, Sweden, Switzerland, United Kingdom
ms.author: atrukawk
ms.search.validFrom: 2017-06-01
ms.dyn365.ops.version: July 2017 update
ms.search.form: CustPaymMode, CustBankAccounts, VendPaymMode, VendBankAccounts
---

# Import ISO20022 files

[!include [banner](../includes/banner.md)]

You can import payment files that have the following formats:

 - **ISO20022 camt.054 credit advice** – Import incoming payments from a file in this format into the Customer payment journal.
 - **ISO20022 pain.002 status return** and **ISO20022 camt.054 debit advice** – Import return files in these formats into the AP Payment transfer journal.

## Prerequisites for importing the camt.054 credit advice file
You must complete the following prerequisites to import bank notification messages in the camt.054.001.002 format into the Customer payment journal.

1. Import the **ISO20022 camt.054** Electronic reporting (ER) configuration from Microsoft Dynamics Lifecycle Services (LCS). Then, on the **Customer method of payment** page, in the **Import format configuration** field, select that configuration. For more information, see [File formats for methods of payment](emea-select-file-formats-for-the-method-of-payments.md).
2. On the **All customers** page, enter a name and organization number for each customer.
3. On the **Customer bank account** page, set up a customer bank account record by entering the following information: IBAN or bank account number, and SWIFT code or routing number.
4. On the **Bank accounts** page, set up legal entity bank accounts by entering the following information: IBAN or bank account number, SWIFT code or routing number, currency, and address.

   > [!NOTE]
   > If you plan to use Advanced bank reconciliation, on the **Reconciliation** FastTab, set the **Advanced bank reconciliation** option to **Yes**. If you plan to reconcile unposted imported payments, set the **Use bank statements as confirmation of electronic payments** option to **Yes**.

5. Optional: On the **Transaction code mapping** page, set up the mapping between bank transaction codes in the file and bank transaction types.
6. If the file contains transaction charges that you want to post together with the incoming payment, create a payment fee on the **Customer payment fee** page. Then, on the **Methods of payment** page, associate the payment fee with the bank account in the payment fee setup.
7. If ESR payments will be imported and will contain ISR references (applicable for legal entities in Switzerland), complete the following setup:

	- In the **Customer payments, account lengths** field, enter the length of the customer code that is used in ISR references or for automatic identification of the customer.
	- Make sure that the customer number and invoice number (number sequences) contain only digits. They must contain no other characters. The invoice number must not have leading zeros.
	- Enter the ESR, BESR, and routing number for the legal entity bank account. For more information, see [ESR customer payments import](emea-che-esr-customer-payments-import.md), because similar settings are required.
	
## Import the camt.054 credit advice file into the Customer payment journal
1. On the **Customer payment journal lines** page, click **Functions** > **Import payments**.
2. Select the method of payment that has the required settings for the ISO20022 camt.054 format.
3. Specify the required parameters and the path of the file, and then click **OK**. The file is imported.

## Prerequisites for importing files in the pain.002 status return and camt.054 debit advice formats into the AP Payment transfer journal
You must complete the following prerequisites to import bank messages in the following ISO20022 formats to the **Vendor payment transfer** page: pain.002.001.003 status return messages and camt.054.001.002 debit advice.

1. Import the **ISO20022 camt.054** and **ISO20022 pain.002** ER configurations from LCS.
2. On the **Vendor method of payment** page, in the **Return format configuration** and **Return format secondary configuration** fields, select the ER configurations that you imported. You will have to activate the generic electronic return format for the selected method of payment.
3. On the **Return format status mapping** page, set up the mapping of status codes between pain.002 statuses and Vendor payment journal statuses.

    Here is an example of a status setup.

    Return status | Payment status
    --------------|---------------
    RJCT          | Rejected
    ACCP          | Accepted
    ACSP          | Received

4. On the **Return format error codes** page, set up pain.002 error codes and descriptions in accordance with external ISO20022 status reason codes.

    Here is an example of part of an error code setup.

    Code | Name
    -----|-----
    AC01 | IncorrectAccountNumber
    AC02 | InvalidDebtorAccountNumber
    AC03 | InvalidCreditorAccountNumber
    AC04 | ClosedAccountNumber
    AC05 | ClosedDebtorAccountNumber
    AC06 | BlockedAccount

5. If the camt.054 file contains transaction charges that you want to post together with the incoming payment, create a payment fee on the **Vendor payment fee** page. Then, on the **Methods of payment** page, associate the payment fee with the bank account in the payment fee setup.

## Import the pain.002 status return or camt.054 debit advice files into the Vendor payment journal
1. Open the **Payment transfers** page in Accounts Payable menu.
2. On the **Payment transfers** page, click **Return file - vendor**.
3. Select the method of payment that has the required settings for ISO20022 files, and then click **OK**.
4. Select the file format that you plan to import, and then click **OK**.
5. Specify the required parameters and the path of the file, and then click **OK**.

If you're importing the pain.002 file, the status of vendor payment lines is updated, based the information in the imported file.

If you're importing the camt.054 file, you should specify the following additional parameters:

- **Fee ID** – Enter the Fee ID which will define new payment fee lines, which will be created on the Vendor payment journal line if a charge amount is present in the camt.054 file.
- **New journal name** and **New journal description** – Enter the name and description of the journal that processed transactions will be transferred to. After the transfer, new voucher numbers should be assigned in the new journal.
- **Import direct debit transactions** – Set this option to **Yes** if outgoing direct debits must be imported into the Vendor payment journal.
- **Journal name** – Define a new journal name for the imported direct debit transactions.
- **Settle transactions** – Set this option to **Yes** if imported vendor payments must be settled with invoices that are found in the system.

You can view the imported information on the **Payment transfers** page. 

## Additional details

When you import a format configuration from LCS, you import the whole configuration tree which means that the Model and Model mapping configurations are included. 
In the Payment model starting from version 8, the mappings are located in separate ER configurations in the solution tree (Payment model mapping 1611, Payment model mapping to destination ISO20022, etc). There are many different payment formats under one model (Payment model), thus separate mapping handling is a key for easy solution maintenance. 
For example, consider this scenario: you use ISO20022 payments to generate credit transfer files and then you import the return messages from the bank. In this scenario, you should use the following configurations:

 - **Payment model**
 - **Payment model mapping 1611** – this mapping will be used to generate the export file
 - **Payment model mapping to destination ISO20022** – this configuration includes all mappings which will be used to import the data (“to destination” mapping direction)
 - **ISO20022 Credit transfer** – this configuration includes a format component that is responsible for export file generation (pain.001) based on the Payment model mapping 1611, as well as a format to model mapping component which will be used together with Payment model mapping to destination ISO20022 to register exported payments in the system for further import purposes (import in CustVendProcessedPayments technical table)
 - **ISO20022 Credit transfer (CE)**, where CE correspond to country/region extension – derived format to the ISO20022 Credit transfer with the same structure and with certain country/region-specific differences
 - **Pain.002** – this format will be used together with the Payment model mapping to destination ISO20022 in order to import the pain.002 file into vendor payments transfers journal
 - **Camt.054** – this format will be used together with the Payment model mapping to destination ISO20022 to import the camt.054 file into vendor payments transfers journal. The same format configuration will be used in customer payments import functionality, but the different mapping will be used in the Payment model mapping to destination ISO20022 configuration.

For more information about Electronic reporting, refer to [Electronic reporting overview](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md).

## Additional resources
- [Create and export vendor payments using ISO20022 payment format](./tasks/create-export-vendor-payments-iso20022-payment-format.md)
- [Import ISO20022 credit transfer configuration](./tasks/import-iso20022-credit-transfer-configuration.md)
- [Import ISO20022 direct debit configuration](./tasks/import-iso20022-direct-debit-configuration.md)
- [Set up company bank accounts for ISO20022 credit transfers](./tasks/set-up-company-bank-accounts-iso20022-credit-transfers.md)
- [Set up company bank accounts for ISO20022 direct debits](./tasks/set-up-company-bank-accounts-iso20022-direct-debits.md)
- [Set up customers and customer bank accounts for ISO20022 direct debits](./tasks/set-up-bank-accounts-iso20022-direct-debits.md)
- [Set up method of payment for ISO20022 credit transfer](./tasks/set-up-method-payment-iso20022-credit-transfer.md)
- [Setup method of payment for ISO20022 direct debit](./tasks/setup-method-payment-iso20022-direct-debit.md)
- [Set up vendors and vendor bank accounts for ISO20022 credit transfers](./tasks/set-up-vendor-iso20022-credit-transfers.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
