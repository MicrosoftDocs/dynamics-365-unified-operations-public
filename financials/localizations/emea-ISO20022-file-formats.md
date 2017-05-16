---
# required metadata

title: ISO20022 file formats
description: [Full description that appears in the search results. Often the first paragraph of your topic.]
author: neserovleo
manager: AnnBe
ms.date: 05/11/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
# ms.search.scope: [Which Operations client to show this topic as help for, to be set by content strategist, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
# ms.tgt_pltfrm: 
# ms.custom: [used by loc]
ms.assetid: [Go get from guidgenerator.com]
ms.search.region: [Global for most topics. Set Country/Region name for localizations]
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: [Microsoft alias]
ms.search.validFrom: [month/year of release that feature was introduced in, in format yyyy-mm-dd]
ms.dyn365.ops.version: [name of release that feature was introduced in, see list here: https://microsoft.sharepoint.com/teams/DynDoc/_layouts/15/WopiFrame.aspx?sourcedoc={23419e1c-eb64-42e9-aa9b-79875b428718}&action=edit&wd=target%28Core%20Dynamics%20AX%20CP%20requirements%2Eone%7C4CC185C0%2DEFAA%2D42CD%2D94B9%2D8F2A45E7F61A%2FVersions%20list%20for%20docs%20topics%7CC14BE630%2D5151%2D49D6%2D8305%2D554B5084593C%2F%29]
---

# ISO20022 files import in Microsoft Dynamics 365 for Operations


## Overview
This article describes features which allows to import payment files in Microsoft Dynamics 365 for Operations in following formats: 

 - incoming payments from the ISO20022 camt.054 credit advice file into Customer payment journal 
 - return files in ISO20022 format: pain.002 status return and camt.054 debit advice into AP Payment transfer journal

## Camt.054 credit advice import into AR payment journal
This feature allows to import bank notification messages in camt.054.001.002 format into Customer payment journal.

To use this feature, following setup should be completed:


 - Import ER configuration "ISO20022 Camt.054" from the LCS and select it on the customer Method of payment form in the Import format configuration field. For more info, see also ﻿[wiki ﻿article](https://docs.microsoft.com/en-us/dynamics365/operations/financials/localizations/emea-select-file-formats-for-the-method-of-payments)﻿.
 - On the All customers form, set up Name and Organization number for required customers. On the Customer bank account form, set up customer bank account record: IBAN or Bank account number, SWIFT or Routing number.
 - Set up legal entity bank accounts on the Bank accounts form:
	 - IBAN or Bank account number, SWIFT or Routing number, Currency,   
   Address.
   

	 - If you are going to use Advanced bank reconciliation, activate parameter Advanced bank reconciliation in Reconciliation fast tab. If you are going to reconcile unposted imported payments, activate also parameter Use bank statements as confirmation of electronic payments.


	 - (Optionally) Set up mapping between bank transaction codes in the file and bank transaction type in system on the Transaction code mapping form.


 - If file contains transaction charges which you decide to post along with posting of incoming payment, create payment fee on the customer Payment fee form, and then associate it with the bank account on the Payment fee setup on the Methods of payment form.
 - If ESR payments will be imported which contain ISR reference (applicable for legal entities in Switzerland), additional settings should be entered:


	 - Length of customer code used in ISR referencef or automatic identification of customer (field "Customer payments, account lengths"). 



	 - Also make sure that Customer number and invoice number (number sequences) contain only digits and no other characters. Also, invoice number must not have leading zeros.



	 - ESR, BESR and Routing number for the legal entity Bank account.For more info see also [legacy ESR feature](https://docs.microsoft.com/en-us/dynamics365/operations/financials/localizations/emea-che-esr-customer-payments-import), which requires similar settings.

To run the file import, open customer payment journal lines form and click Functions/ Import payments button. On the dialog screen select method of payment which have required settings for ISO20022 camt.054 format. On the opened dialog, specify required parameters and path to the file location. Click OK. File is successfully imported.


##Pain.002 status return and camt.054 debit advice import into AP Payment transfer journal
This feature allows to import bank messages in ISO20022 formats: pain.002.001.003 status return messages and camt.054.001.002 debit advice on the Vendor payment transfer form.

To use this feature, following setup should be completed:

 - Import ER configurations "ISO20022 Camt.054" and "ISO20022 pain.002" from the LCS and select it on the vendor Method of payment form in the Return format configuration and Return format secondary configuration fields. It will require to activate Generic electronic Return format for the selected method of payment.

 - Set up mapping of status codes between pain.002 statuses and vendor payment journal statuses on the Return format status mapping form.

Example setup:

Return status	| Payment status
-------- | ---
RJCT| Rejected
ACCP| Accepted 
ACSP| Recieved 


 - Set up pain.002 error codes and descriptions on the Return format error codes form per external ISO20022 Status reason codes.

Example setup:


Code	| Name
-------- | ---
AC01| IncorrectAccountNumber
AC02| InvalidDebtorAccountNumber
AC03| InvalidCreditorAccountNumber
AC04| ClosedAccountNumber
AC05| ClosedDebtorAccountNumber
AC06| BlockedAccount


 - If camt.054 file contains transaction charges which you decide to post along with posting of incoming payment, create payment fee on the vendor Payment fee form, and then associate it with the bank account on the Payment fee setup on the Methods of payment form.  

To run the file import, open vendor payment transfers form and click Return file - vendor button. On the dialog screen select method of payment which have required settings for ISO20022 files and press OK. Then, select which file format do you plan to import and click OK. On the opened dialog, specify required parameters and path to the file location and click OK.  

If you're importing pain.002 file, then status of vendor payment lines will be updated according to the information in imported file.

If you're importing camt.054 file, then additional parameters should be specified:

 - Fee ID - new Payment fee lines will be created in vendor payment journal line if charges amount is present in camt.054 file.

 - New journal name, New journal description - payment journal parameters where processed payments will be transferred. After transferring, new voucher numbers should be assigned within the new journal. See the Known limitations section for more information.


 - Import direct debit transactions - activate Import direct debit transactions if outgoing direct debits need to be imported to the vendor payment journal.



 - Journal name - define a new journal name for the imported direct debit transactions

 - Settle transactions - activate if imported vendor payments will need to be settled with invoices found in the system.



Imported information can be reviewed on the Payment transfers form. 
In case of any issues in records in the file, they should be imported as is (i.e. with empty vendor account if it is not possible to find one).
