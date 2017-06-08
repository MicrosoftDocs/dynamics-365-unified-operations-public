---
# required metadata

title: ISO20022 files import
description: This topic explains how to import payment files of the ISO 20022 camt.054 and pain.002 formats into Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.
author: neserovleo
manager: AnnBe
ms.date: 05/25/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Austria, Belgium, Czech Republic, Sweden, Switzerland, Germany, Denmark, Spain, Estonia, Finland, France, Hungary, Italy, Lithuania, Latvia, Poland, Norway, Great Britain
# ms.search.industry: 
ms.author: v-lenest
ms.search.validFrom: 2017-06-01
ms.dyn365.ops.version: Enterprise edition, July 2017 update
---

# ISO20022 files import

## Overview
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
	- Enter the ESR, BESR, and routing number for the legal entity bank account. For more information, see [legacy ESR feature](emea-che-esr-customer-payments-import.md), because similar settings are required.
	
## Import the camt.054 credit advice file into the Customer payment journal
1. On the **Customer payment journal lines** page, click **Functions** > **Import payments**.
2. Select the method of payment that has the required settings for the ISO20022 camt.054 format.
3. Specify the required parameters and the path of the file, and then click **OK**.

The file is imported.

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
1. Open vendor the **Payment transfers** page.
2. Click **Return file - vendor**.
3. Select the method of payment that has the required settings for ISO20022 files, and then click **OK**.
4. Select the file format that you plan to import, and then click **OK**.
5. Specify the required parameters and the path of the file, and then click **OK**.

If you're importing the pain.002 file, the status of vendor payment lines is updated, based the information in the imported file.

If you're importing the camt.054 file, you should specify the following additional parameters:

- **Fee ID** – New payment fee lines will be created on the Vendor payment journal line if a charge amount is present in the camt.054 file.
- **New journal name** and **New journal description** – Enter the name and description of the journal that processed transactions will be transferred to. After the transfer, new voucher numbers should be assigned in the new journal.
- **Import direct debit transactions** – Activate this field if outgoing direct debits must be imported into the Vendor payment journal.
- **Journal name** – Define a new journal name for the imported direct debit transactions.
- **Settle transactions** – Activate this field if imported vendor payments must be settled with invoices that are found in the system.

You can view the imported information on the **Payment transfers** page. 
