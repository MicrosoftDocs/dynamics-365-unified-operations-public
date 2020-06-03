---
# required metadata

title: APAC-IND-Newsletter-10-0-10
description: This topic describes changes incorporated in Dynamics 365 Application version 10-0-10
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

# Welcome to the newsletter for version 10.0.10! 

This newsletter includes a summary of the new features and critical bug fixes released in version 10.0.10 for India.
You can learn more about the shipped features in 
-[ What's new or changed in Finance and Operations version ] (https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-changed-10-0-10)

# New Features
## Import order over-delivery setup respected at Invoice registration stage

In case of import order user do setup to accept over delivery . At the time of invoice registration user can adjust receive quantity.
Earlier user was not allowed to adjust Import order quantity in invoice registration form. 
Now user can update invoice registration quantity till over delivery quantity derived as per setup. 
### Steps : 
### Setup Accept Over Delivery
Procurement and Sourcing Module -> Setup -> Procurement and Sourcing Parameters 
-> Deliver Tab: Accept Delivery set to YES -> Save
### Update over delivery Quantity: 
Invoice registration Page -> Select Import invoice above -> Update Receive Quantity

![](media/Over Delivery -import order-10.0.10.png)

## TDS on Foreign vendor transaction 
TDS on foreign vendor invoice gives Voucher imbalance error . The transactions on voucher do not balance . 
As per rule 26 of Income tax act TDS on foreign currency transaction is converted  on the TTR buying rate instead of normal GAP rate .

### TDS on transaction in foreign currency : 

- Main transaction in GAP rate or manually updated exchange rate 
- TDS on transaction as per TDS exchange rate 

Setup TDS exchange rate as TDS and Accounting currency exchange rate type as Default in Ledger form

![](media/TDS on Foreign currency-10.0.10.png

### Accounting entries :
| Description                | Dr.(US$)     | Dr.(INR)          | Cr.(US$)                | Cr.(INR)                                        |
|----------------------------|--------------|-------------------|-------------------------|-------------------------------------------------|
|     Service /Lease exp.    |     100      |     GAP Rate      |                         |                                                 |
|     CGST                   |        9     |      GAP Rate     |                         |                                                 |
|     SGST                   |        9     |      GAP Rate     |                         |                                                 |
|     Vendor                 |              |                   |     108     (118-10)    |     (118@GAP rate-     10@TDS exchange rate)    |
|     TDS Payable            |              |                   |     10                  |     TDS Exchange Rate                           |
|     Total                  |     118      |                   |     118                 |                                                 |

# Critical Fixes 

- Enable date time tracking for tax run time lookup condition table. 
-	Transaction type not showing in case of tax Journal posting . 
-	Unable to generate recurring Free Text Invoice getting error 
  Path : Accounts Receivable>Recurring Invoice>Free Text Invoice template 
-	Difference is appearing between sales tax payment and actual transaction posted to tax authorities. 
  Through this fix it is ensured that Sales tax settlement amount and actual amount posted to tax authority is matched. 
-	Adjusted amount origin field showing wrong value - System is picking the adjusted base amount posted in the 
  initial transaction and same base amount is fetching for subsequent transactions. 
-	Tax calculation is appearing wrong when discount is applied through General Journal in multi-line transaction.
  (Discount ledger account either Debit or Credit) 

  Two scenarios are covered :
  
  - Creating credit note to customer (GST is calculating negative value for discount) 
  - Creating Invoice/Debit note to customer (GST is calculating positive value for discount) 


# Upcoming critical fixes in 10.0.11 

-	When created one main vendor with multiple sub-vendor. Currently system is picking the main supplier name and
  address and displaying in GSTR-2 ,
  which not selected in the Tax Information at the time of posting . 
-	Withholding tax Journal is crated to  adjust the withholding tax (TDS) amount and select the voucher transaction for adjustment. 
  When post the Journal system is throwing an error log once the transaction has been selected and transfer to General Journal. 
-	This fix was done to display warning message  when user defined the charge code with the posting type as Ledger and item combination
  on the transaction. 
-	System through error while running withholding (TDS) tax payment .
-	Wrong Tax information in Sales order created from sales agreement. In this issue address field is populating legal entity address
  instead of warehouse address. 
-	When user posted Free text Invoice with GST tax amount and do rounding off setup under  currencies  system not
  rounding invoice amount
  for customer sub-ledger account but customer main ledger is rounding off correctly in voucher.  
  Path >General ledger module>> currencies >>currencies Go to INR currencies >> Go to Rounding rules >>General rounding 
  rule 0.01 >> Sales order rounding rule 1.00 
-	TDS section code and invoice number is not  appearing in TDS inquiries 
 
