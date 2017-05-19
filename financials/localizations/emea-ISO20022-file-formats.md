---
# required metadata

title: ISO20022 files import in Microsoft Dynamics 365 for Operations
description: This topic describes features that enable you to import payment files in ISO 20022 camt.054 and pain.002 payment files in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.
author: neserovleo
manager: AnnBe
ms.date: 05/17/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
# ms.search.scope: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Austria, Belgium, Czech Republic, Sweden, Switzerland, Germany, Denmark, Spain, Estonia, Finland, France, Hungary, Italy, Lithuania, Latvia, Poland, Norway, Great Britain
# ms.search.industry: 
ms.author: v-lenest
ms.search.validFrom: 2017-06-01
ms.dyn365.ops.version: 
---

# ISO20022 files import in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition


## Overview
This topic describes features that enable you to import payment files in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition in following formats: 

 - Incoming payments from the ISO20022 camt.054 credit advice file into the Customer payment journal. 
 - Return files in ISO20022 format: pain.002 status return and camt.054 debit advice into the AP Payment transfer journal.

## Camt.054 credit advice import into Accounts Receivable payment journal
This feature allows you to import bank notification messages in camt.054.001.002 format into the Customer payment journal.

To use this feature, complete the following steps:

 - Import ER configuration "ISO20022 Camt.054" from Lifecycle Services and select it on the **Customer method of payment** page in the **Import format configuration** field. For more information, see [File formats for methods of payment](emea-select-file-formats-for-the-method-of-payments.md).
 - On the **All customers** page, enter a name and organization number for required customers. On the **Customer bank account** page, set up a customer bank account record: IBAN or Bank account number, SWIFT, or Routing number.
 - Set up legal entity bank accounts on the **Bank accounts** page:
	 - IBAN or Bank account number, SWIFT or Routing number, Currency,   
   Address.
   	 - If you plan to use Advanced bank reconciliation, activate parameter **Advanced bank reconciliation** on the **Reconciliation** FastTab. If you plan to reconcile unposted imported payments, activate parameter **Use bank statements as confirmation of electronic payments**.
	 - (Optionally) Set up mapping between bank transaction codes in the file and bank transaction types in the system on the **Transaction code mapping** page.

 - If  the file contains transaction charges that you want to post along with posting of incoming payment, create a payment fee on the **Customer payment fee** page, and then associate it with the bank account on the payment fee setup on the **Methods of payment** page.
 - If ESR payments will be imported and contain ISR references (applicable for legal entities in Switzerland), the following settings should be entered:

	 - Length of customer code used in ISR references or automatic identification of customer (**Customer payments, account lengths** field). 
	 - Enure that customer number and invoice number (number sequences) contain only digits and no other characters. The invoice number must not have leading zeros.
	 - ESR, BESR, and Routing number for the legal entity bank account. For more information, see [legacy ESR feature](emea-che-esr-customer-payments-import.md), which requires similar settings.

To run the file import, open the **Customer payment journal lines** page and click the **Functions/Import payments** button. In the dialog box, select the method of payment which have required settings for ISO20022 camt.054 format. In the dialog box, specify the required parameters and path to the file location. Click **OK**. The file will be imported.

## Pain.002 status return and camt.054 debit advice import into AP Payment transfer journal
This feature allows you to import bank messages in ISO20022 formats: pain.002.001.003 status return messages and camt.054.001.002 debit advice on the **Vendor payment transfer** page.

To use this feature, complete the following steps:

 - Import ER configurations "ISO20022 Camt.054" and "ISO20022 pain.002" from Lifecycle Services and select it on the **Vendor method of payment** page in the **Return format configuration** and **Return format secondary configuration** fields. This will require you to activate generic electronic return format for the selected method of payment. 

 - Set up mapping of status codes between pain.002 statuses and vendor payment journal statuses on the **Return format status mapping** page.

Here's an example of the setup.

Return status	| Payment status
-------- | ---
RJCT| Rejected
ACCP| Accepted 
ACSP| Recieved 

 - Set up pain.002 error codes and descriptions on the **Return format error codes** page per external ISO20022 Status reason codes.

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

 - If camt.054 file contains transaction charges that you want to post along with posting of incoming payment, create a payment fee on the **Vendor payment fee** page, and then associate it with the bank account on the payment fee setup on the **Methods of payment** page.  

To run the file import, open vendor the **Payment transfers** page and click the **Return file - vendor** button. In the dialog box, select the method of payment that has required settings for ISO20022 files. Clikc **OK**. Select the file format that you plan to import and click **OK**. In the dialog box, specify the required parameters and path to the file location, and then click **OK**.  

If you're importing pain.002 file, then the status of vendor payment lines will be updated according to the information that is in the imported file.

If you're importing camt.054 file, then the following additional parameters should be specified:

 - **Fee ID** - New payment fee lines will be created on the vendor payment journal line if a charge amount is present in the camt.054 file.

 - **New journal name, New journal description** - Payment journal parameters where processed payments will be transferred. After transferring, new voucher numbers should be assigned within the new journal. See the Known limitations section for more information.
 - **Import direct debit transactions** - Cctivate import direct debit transactions if outgoing direct debits need to be imported to the vendor payment journal.
 - **Journal name** - Define a new journal name for the imported direct debit transactions.
 - **Settle transactions** - Activate this field if imported vendor payments will need to be settled with invoices that are found in the system.

Imported information can be reviewed on the **Payment transfers** page. 
