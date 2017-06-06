---
# required metadata

title: ISO20022 files import
description: This topic describes importing payment files of the ISO 20022 camt.054 and pain.002 formats into Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.
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

 - Incoming payments from the ISO20022 camt.054 credit advice file into the Customer payment journal. 
 - Return files in ISO20022 format: pain.002 status return and camt.054 debit advice into the AP Payment transfer journal.

## Prerequisites for importing the Camt.054 credit advice file
Complete the following prerequisites so you can import bank notification messages in the camt.054.001.002 format into the Customer payment journal.

1. Import the Electronic Reporting(ER) configuration "ISO20022 Camt.054" from Lifecycle Services and select it on the **Customer method of payment** page in the **Import format configuration** field. For more information, see [File formats for methods of payment](emea-select-file-formats-for-the-method-of-payments.md).
2. On the **All customers** page, enter a name and organization number for customers. 
3. On the **Customer bank account** page, set up a customer bank account record: IBAN or Bank account number, SWIFT, or Routing number.
4. On the **Bank accounts** page, set up legal entity bank accounts by entering the following information: IBAN or Bank account number, SWIFT or Routing number, Currency, Address.
  	> [!NOTE] If you plan to use Advanced bank reconciliation, activate the parameter **Advanced bank reconciliation** on the 		>**Reconciliation** FastTab. If you plan to reconcile unposted imported payments, activate parameter **Use bank statements as confirmation of electronic payments**.
5. (Optional) Set up mapping between bank transaction codes in the file and bank transaction types on the **Transaction code mapping** page.
6. If  the file contains transaction charges that you want to post along with posting of incoming payment, create a payment fee on the **Customer payment fee** page, and then associate it with the bank account on the payment fee setup on the **Methods of payment** page.
7. If ESR payments will be imported and contain ISR references (applicable for legal entities in Switzerland), the following settings should be entered:
	- Length of customer code used in ISR references or automatic identification of customer (**Customer payments, account lengths** field). 
	- Enure that customer number and invoice number (number sequences) contain only digits and no other characters. The invoice number must not have leading zeros.
	- ESR, BESR, and Routing number for the legal entity bank account. For more information, see [legacy ESR feature](emea-che-esr-customer-payments-import.md), which requires similar settings.
	
## Import the Camt.054 credit advice file into the Customer payment journal	
1. On the **Customer payment journal lines** page, click the **Functions/Import payments** button. 
2. Select the method of payment that has the required settings for the ISO20022 camt.054 format. 
3. Specify the required parameters and path to the file location. 
4. Click **OK**. The file will be imported.

## Prerequisites Pain.002 status return and camt.054 debit advice import into the AP Payment transfer journal
This feature allows you to import bank messages in the following ISO20022 formats to the **Vendor payment transfer** page: pain.002.001.003 status return messages and camt.054.001.002 debit advice.

1. Import ER configurations "ISO20022 Camt.054" and "ISO20022 pain.002" from Lifecycle Services.
2. On the **Vendor method of payment** page,  in the **Return format configuration** and **Return format secondary configuration** fields, select the ER configuration that you imported. This will require you to activate generic electronic return format for the selected method of payment. 
3. On the **Return format status mapping** page, set up the mapping of status codes between pain.002 statuses and vendor payment journal statuses.

Here's an example of the status setup.

Return status	| Payment status
-------- | ---
RJCT| Rejected
ACCP| Accepted 
ACSP| Recieved 

4. Set up pain.002 error codes and descriptions on the **Return format error codes** page per external ISO20022 Status reason codes.

Here's an example of the setup.

|Code	| Name|
-------- | ---
AC01| IncorrectAccountNumber
AC02| InvalidDebtorAccountNumber
AC03| InvalidCreditorAccountNumber
AC04| ClosedAccountNumber
AC05| ClosedDebtorAccountNumber
AC06| BlockedAccount
...| ...

5. If the camt.054 file contains transaction charges that you want to post along with the incoming payment, create a payment fee on the **Vendor payment fee** page, and then associate it with the bank account on the payment fee setup on the **Methods of payment** page.  

## Import the Pain.002 status return or camt.054 debit advice files into the Vendor payment journal
1. Open vendor the **Payment transfers** page.
2. Click **Return file - vendor**. 
3. Select the method of payment that has the required settings for ISO20022 files. 
4. Click **OK**. 
5. Select the file format that you plan to import and the click **OK**.
6. Specify the required parameters and path to the file location, and then click **OK**.  

If you're importing pain.002 file, then the status of vendor payment lines will be updated according to the information that is in the imported file.

If you're importing camt.054 file, then the following additional parameters should be specified:

 - **Fee ID** - New payment fee lines will be created on the vendor payment journal line if a charge amount is present in the camt.054 file.

 - **New journal name, New journal description** - Payment journal parameters where processed payments will be transferred. After transferring, new voucher numbers should be assigned within the new journal. 
 - **Import direct debit transactions** - Activate import direct debit transactions if outgoing direct debits need to be imported to the vendor payment journal.
 - **Journal name** - Define a new journal name for the imported direct debit transactions.
 - **Settle transactions** - Activate this field if imported vendor payments will need to be settled with invoices that are found in the system.

You can view the imported information on the **Payment transfers** page. 
