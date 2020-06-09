---
# required metadata

title: What's new and changed for APAC India GST Localization in 10.0.11 (July 2020)
description: This topic describes new and changed functionality for APAC India GST features released in Dynamics 365 Finance version 10.0.11.
author: prabhatb
manager: Wangcheng
ms.date: 06/09/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: prabhatb
ms.search.validFrom: 
ms.dyn365.ops.version: 10.0.11

---
[!include [banner](../includes/banner.md)]

# What's new and changed for APAC India GST Localization in 10.0.11 (July 2020)

This topic includes a summary of the new features and critical bug fixes released in Dynamics 365 Finance version 10.0.11 for APAC India GST localization. 

## New Features

### GST Tax settlement as per new settlement rules  (vide Circular No. 98/17)

Based on the newlt amended GST law, the following sequence is required to be maintained:

| IGST liability | CGST liability | SGST liability  |
|----------------|----------------|-----------------|
| IGST credit    | IGST credit    | IGST credit     |
| CGST credit    | CGST credit    | SGST credit     |
| SGST credit    |                |                 |

To set up the new settlement rule, go to **Tax** > **Setup** > **Sales tax hierarchies** > **View** > **Setoff rules for sales tax hierarchies**.  

![](media/GST-tax-settlement-new-rules-1-10-0-11.PNG)

A new tax settlement change has been incorporated in the tax settlement hierarchy. You can define the tax set off hierarchy for a tax component with any  tax settlement priority. Previously, each tax component recoverable amount was settled against the tax payable amount of it's own tax component and then with other tax components. Going forward, you can define the set off priority of a tax component with any other tax component. For example, you can set up a settlement priority of the input tax credit for CGST against IGST  first and then with CGST. Similarly, SGST can be set off against IGST first and then SGST.

## Data entity for stock transfer order transaction 
The stock transfer transaction upload through the data entity is provided so that large size stock transfer orders can use 
data management to upload stock transfer transactions.  

## Critical fixes 

- The **TDS adjustment journal** for adjusting the TDS amount on an already posted transaction is not working correctly and instead, results in an error. This hqappens when the adjustment amount is transferred from the **Tax journal** to the **General journal** for posting.  
-	When you create charge codes with a credit type of Ledger Account, you must also define an SAC code for the charge. The charge will be credited to the defined ledger account and will not be included in the vendor balance after the purchase order is posted. With this posting, you should not be allwed to define the SAC/HSN code in the charge code.  
-	On the **Account structure** page, if blank values are not allowed for the financial dimension, then when the invoice with a tax withholding payment is posted, the defined financial dimension must be have a value for the TDS Authority vendor and invoice transaction. 
-	If a sales order is created from sales agreement, the tax information in the sales order should populate from the legal entity instead of the warehouse. If the state of origin is different from the state of the legal entity, the system calculates IGST instead of CGST, SGST, and vice versa. 
-	When you post the free text invoice with a GST tax amount, the system should round the amount for the Trade debtors account and the Main ledger trade receivable account to the Reconciliation main ledger with sub-ledger. 
-	The **Customer balance and total** button on the **Free text invoice credit note** is updated with wrong value. However, the voucher is posted correctly.  
-	When a withholding tax authority payment is processed, by default all the related withholding tax settlement transactions should be marked as ready for settlement. If there is a separate journal transaction posting in progress, all of these withholding tax settlement transactions will be closed even though the withholding tax authority payment has not been made. 
-	Vendor invoices that were created by customers using the **Vendor invoice journal** will have GST paid for the invoices on a reverse charge basis.
  User want to generate self- invoice. User cannot  Reverse charge tax Invoice with GST reference id.  
-	When posting a vendor invoice journal that includes tax, the section code is not appearing in the **TDS inquiry transaction** page.
  Similarly Project Sales Order, Section code and Invoice number are not appearing in TDS inquiry transaction form. 
-	Tax information adjustment is not working on project timesheet transactions.   
-	A sales return order with an SEZ customer is not showing the option **With tax payment** even though it was selected in the original sales order . 
-	An error message occurs when posting an invoice journal with multiple lines, applied TDS, and an exchange rate that was updated after lines were created in the in invoice journal. The system is not picking up the latest defined exchange rate for the whole transaction. 


## Upcoming critical fixes in 10.0.12 

- Tax information fields are not updated automatically when a user copies lines from an original free text invoice. 
-	In the TDS statement and voucher reversal, a tax payment error occurrs when a **Vendor invoice journal** with TDS is posted.  
- When an invoice journal is posted with TDS and a user reverses a transaction line on the **Vendor transaction** page and adjusts
  withholding tax through the **General journal**, the withholding tax payment results in an error. 
-	When the transaction date on an invoice journal with multiple lines is modified, only the first line in the tax document is updated with the new date when all of the lines must be updated. 
-	A voucher balancing error occurs when the **General journal** is posted with a Project/Vendor combination that specifies an inventory load and reverse charge percentage for the selected HSN/SAC code. 
-	Removed and inactive addresses are appearing again under **Location** on the **Tax information** page of invoices that are generated 
 from the **Invoice journal** and **Free text invoice**. 
-	An issue occurs when posting the **Withholding tax adjustment journal** and the TDS main account is marked as **Do not allow manual entry**.  
-	The **Withholding tax** tax group can't be modified during invoice processing in the India Legal Entity when posting transactions using the **Pending invoice** page.
- It is possible to delete the source details in the GST number sequence group even when the details are attached to a transaction.   
-	Charges are not automatically updated in the **Assessable value** field on the sales order line when user applies charges through the **Auto charges** functionality. If the **Assessable value** check box is marked when setting up auto charge, charges are not automatically updating on the sales order line to include charge amount in the assessable value of goods.  
-	Importing the **General journal** lines with tax using the data import/export feature seems successful, but when verifying the tax document, there is not tax information for the imported **General journal** transactions.
