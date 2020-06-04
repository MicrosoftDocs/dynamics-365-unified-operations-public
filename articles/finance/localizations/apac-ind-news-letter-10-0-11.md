---
# required metadata

title: APAC India GST Localization Newsletter 10.0.11
description: This topic describes changes incorporated in Dynamics 365 Application version 10.0.11
author: prabhatb
manager: Wangcheng
ms.date: 05/31/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: 
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: 
ms.search.validFrom: 
ms.dyn365.ops.version: 

---
[!include [banner](../includes/banner.md)]

# Welcome to the newsletter for version 10.0.11! 

This newsletter includes a summary of the new features and critical bug fixes released in version 10.0.11 for India.
You can learn more about the shipped features in 
-[ What's new or changed in Finance and Operations version ] (https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-changed-10-0-11)

## New Features

## GST Tax settlement as per new settlement rules  (vide Circular No. 98/17)

As per new amended GST Law : The following sequence is required to be maintained 
| IGST Liability | CGST liability | SGST Liability  |
|----------------|----------------|-----------------|
| IGST Credit    | IGST Credit    | IGST Credit     |
| CGST Credit    | CGST Credit    | SGST Credit     |
| SGST Credit    |                |                 |

### New settlement rule can be configured as below :  
### Path :- Tax > Setup > Sales tax hierarchies > View > Setoff rules for sales tax hierarchies  

![](media/GST-tax-settlement-new-rules-1-10-0-11.PNG)

New tax settlement change has been incorporated in Tax settlement  hierarchy. User can define tax set off hierarchy for a tax component
with any  tax settlement priority. In existing solution by default each tax component recoverable amount will settle against tax payable amount of own tax component first and later on with other tax components. Going forward user can define set off priority of a tax component with any other tax component.For example  user can set up settlement priority of Input tax credit of CGST again IGST  first and then with CGST,similarly SGST can be set off against IGST first, than with SGST. Previously IGST, CGST and SGST  can be settle first with own tax components only.  

## DATA entity for Stock transfer order transaction 
Stock transfer transaction upload through data entity is provided so that user having large size  stock transfer order can use 
the data management to upload stock transfer transactions.  

## Critical Fixes 

- TDS adjustment Journal for adjusting TDS amount on already posted  transaction is not taking place and throwing an error message.
  This is happening when transfer adjustment amount from tax journal to general Journal for posting.  
-	Create charge codes with credit type as Ledger Account also define SAC code for the charge  and the charge would be
  credited to the defined ledger account and not be part of  the vendor balance after posting purchase order. With this posting 
  system should not allow user to define the SAC/HSN code in charge code.  
-	In account structure form, if it is provided that blank values are not allowed for the financial dimension.
  Then at the time of  posting invoice with tax withhold payment,  the defined financial dimension must be have
  value for the TDS Authority vendor and invoice transaction. 
-	If sales order is created from sales agreement, then tax information in sales order should flow from legal
  entity instead of warehouse. In case the state of origin is different from state of legal entity, then system
  is calculating IGST instead of CGST , SGST and vice versa. 
-	When user post the free text invoice with GST tax amount system should rounding the amount for trade debtors account
  and main ledger trade receivable account to reconciliation main ledger with sub-ledger. 
-	Customer Balance  and total button on free text invoice credit note is updated with wrong value however
  voucher is posted correctly.  
-	When a withholding tax authority payment is processed, by default all the related withholding tax settlement transaction
  should be marked as ready for settlement. Meantime if there is another irrelevant journal transaction posting take place,
  all these withholding tax settlement transaction will be closed even the withholding tax authority payment has not yet made . 
-	Customer created vendor invoices through Vendor Invoice Journal and GST is to be paid for those invoices on reverse charge basis.
  User want to generate self- invoice. User cannot  Reverse charge tax Invoice with GST reference id.  
-	When user is posting vendor invoice journal including tax, Section code is not appearing in TDS inquiry transaction form.
  Similarly Project Sales Order, Section code and Invoice number are not appearing in TDS inquiry transaction form. 
-	Tax information adjustment is not working on project timesheet transactions   
-	Sales Return order with SEZ customer is not showing the option "with tax payment "even such option was selected in the
  original sales order . 
-	Getting error message while posting invoice journal with multiple lines and applying TDS and where exchange rate
  updated in exchange rate master after creating lines in invoice journal. System is not picking latest defined exchange
  rate for the whole transaction 


## Upcoming critical fixes in 10.0.12 

- Tax information fields are not getting updated automatically when user copy lines from original free text invoice   
-	TDS statement and Voucher reversal, tax payment error was appearing when vendor invoice Journal with TDS is posted.  
- Invoice Journal is posted with TDS . User reverse the one transaction line from vendor transaction form and  adjust
  withholding tax through General journal . When run  Withholding tax payment getting error. 
-	Multi- line invoice Journal when transaction date is modified , in the tax document only first line is updated with
  latest correction date.  Actually all the lines must be updated with latest transaction date. 
-	Voucher Balancing Error is coming in Case  General Journal is posted with  Project and  Vendor combination specifying 
  load of inventory and reverse charge % for the selected HSN/SAC code. 
-	Removed/inactive addresses are appearing again under Location on Tax Information form of Invoices that are generated 
  through Invoice Journal/ Free Text Invoice. 
-	User is facing an issue while posting Withholding Tax adjustment journal, system is throwing an error when TDS main
  account is marked as ‘Do not allow manual entry’ .  
-	WHT tax group is not editable during invoice processing in India Legal Entity when posting transaction through
  Pending Invoice form. 
- System allows to delete the  source details in the GST number sequence group even attached to a  transaction.   
-	Charges are not auto updated in assessable value on the sales order line when user apply charges through Auto charges
  functionality. Also if user  mark assessable value check box in auto charge setup . Charges are not  auto updating on 
  the sales order line to include charge amount in assessable value of goods  
-	Importing the general journal lines with tax through data import export feature  successfully but on verification of
  tax document it is showing empty tax information for imported general journal transaction.
