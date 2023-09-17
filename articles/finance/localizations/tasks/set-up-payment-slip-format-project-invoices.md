--- 
# required metadata 
 
title: Set up payment slip format for project invoices
description: This article explains how to attach printed payment slips to project invoices and provide a payment reference for posting and settlement. 
author: EvgenyPopovMBS
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: OMLegalEntity, CustFormletterParameters   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up payment slip format for project invoices

[!include [banner](../../includes/banner.md)]

Businesses commonly attach printed payment slips to invoices to assist customers and provide a payment reference for posting and settlement. The payment slip can be used for project or service invoices, collection letters, interest notes, and account statements, in addition to sales invoices and free text invoices. To process payment slips, first set up your creditor identification number and payment slip attachment formats.

This procedure uses the DEMF demo company. 

This functionality is available for legal entities whose primary address is in Denmark.


## Set up a creditor ID number
1. Go to Organization administration > Organizations > Legal entities.
2. Expand or collapse the Bank account information section.
3. Click Edit.
4. In the FI-Creditor ID field, type a value.
5. Click Save.
6. Close the page.

## Set up a payment slip format for invoices, notes, letters, and statements
1. Go to Accounts receivable > Setup > Forms > Form setup.
2. Click the Invoice tab.
3. In the Associated payment attachment on customer invoice field, select an option.
    * None – Do not print a payment slip. Choose this option if the payment amount is in a currency other than Danish kroner (DKK).   FIK 751 – Print an FIK 751 payment slip if you intend to manually write the payment amount and due date on the payment slip.   FIK 752 – Print an FIK 752 payment slip if you intend to use a computer-generated payment slip with a preprinted payment amount and due date.  
4. Click Save.
5. Click the Free text invoice tab.
6. In the Associated payment attachment on free text invoice field, select an option.
    * None – Do not print a payment slip. Choose this option if the payment amount is in a currency other than Danish kroner (DKK).   FIK 751 – Print an FIK 751 payment slip if you intend to write the payment amount and due date on the payment slip manually.   FIK 752 – Print an FIK 752 payment slip if you intend to use a computer-generated payment slip with a preprinted payment amount and due date.  
7. Click Save.
8. Click the Interest note tab.
9. In the Associated payment attachment on interest note field, select an option.
    * None – Do not print a payment slip. Choose this option if the payment amount is in a currency other than Danish kroner (DKK).   FIK 751 – Print an FIK 751 payment slip if you intend to write the payment amount and due date on the payment slip manually.   FIK 752 – Print an FIK 752 payment slip if you intend to use a computer-generated payment slip with a preprinted payment amount and due date.  
10. Click Save.
11. Click the Collection letter tab.
12. In the Associated payment attachment on collection letter field, select an option.
    * None – Do not print a payment slip. Choose this option if the payment amount is in a currency other than Danish kroner (DKK).   FIK 751 – Print an FIK 751 payment slip if you intend to write the payment amount and due date on the payment slip manually.   FIK 752 – Print an FIK 752 payment slip if you intend to use a computer-generated payment slip with a preprinted payment amount and due date.  
13. Click Save.
14. Click the Account statement tab.
15. In the Associated payment attachment on account statement field, select an option.
    * None – Do not print a payment slip. Choose this option if the payment amount is in a currency other than Danish kroner (DKK).   FIK 751 – Print an FIK 751 payment slip if you intend to write the payment amount and due date on the payment slip manually.   FIK 752 – Print an FIK 752 payment slip if you intend to use a computer-generated payment slip with a preprinted payment amount and due date.  
16. Click Save.
17. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
