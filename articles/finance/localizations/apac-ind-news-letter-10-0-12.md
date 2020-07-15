---
# required metadata

title: What's new or changed for APAC India GST Localization in 10.0.12 (July 2020)
description: This topic describes new or changed functionality for APAC India GST features released in Dynamics 365 Finance version 10.0.12.
author: prabhatb
manager: Wangcheng
ms.date: 07/15/2020
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
ms.dyn365.ops.version: 10.0.12

---

# What's new or changed for APAC India GST Localization in 10.0.12 (July 2020)

[!include [banner](../includes/banner.md)]

This topic includes a summary of the new features and critical bug fixes released in Dynamics 365 Finance version 10.0.12 for APAC India GST localization. 

**Important Announcement** 

The previous version of newsletters are available on Microsoft Docs and can be downloaded from below link.     

(https://docs.microsoft.com/en-us/dynamics365/finance/localizations/apac-ind-news-letter-10-0-00)   

Please note that we are going to stop the circulation of the upcoming newsletter through e-mail and future version of the newsletter will be published directly on Microsoft docs.  

## New features

### Improvements in unit price and cost price handling in Stock transfer orders  

This feature introduces the following improvements in the Stock transfer order functionality: 

- Default values of Transfer type and Price type can be configured in Inventory and warehouse management parameters. 

- Unit price in a stock transfer order line is correctly recalculated based on the inventory dimensions specified in the line until the first shipment is posted for the line. 

- Shipment of a stock transfer order line having zero Unit price can be prevented. 

- Correct inventory costs are posted for stock transfer orders in case of partial shipment or receipts, batch-controlled items, etc. 

- Unrealized profit or loss is not posted upon shipment or receipt of a stock transfer line if the unit price differs from the inventory cost price of the item. 

- The feature also restricts changing Unit of measure in stock transfer order lines. 

Feature can be enabled through feature management:  

![](media/GST-tax-settlement-new-rule-1-10-0-11.PNG )

*** New parameter under Inventory management:***  

### Inventory & warehouse management > Setup> Parameters > Transfer orders   

![](media/GST-tax-settlement-new-rule-1-10-0-11.PNG )

*** Enable stock transfer for master planning :***  

### Master planning > Parameter > Transfer type  

![](media/GST-tax-settlement-new-rule-1-10-0-11.PNG )

## Critical fixes 

- Stock transfer same tax rate applicability at the time of shipment and receipt (Including partial receipt): Tax was computing on the new HSN code percentage and causing Revenue loss to the Customer instead of making the Transfer order before the change in the HSN code percentage.   

- Tax information fields are not getting updated automatically when we copied from the original free text invoice. After this fix When user copy the lines from the original invoice line after defined tax information system is expected to update the tax information related fields in the copied lines for free text invoice. Also, tax document will display the tax amount correctly.   

- The issue was when the Invoice Journal is posted with TDS. Users reverse the one transaction line from vendor transaction form and adjust withholding tax through General journal. When run Withholding tax payment getting error. This issue is fixed because the issue was occurring because the vendor invoice journal with TDS is not getting the ledger account through the table "TaxWHTransGeneralJournalAccountEntry  

- In multi-line invoice Journal when the transaction date is modified, in the tax document only first line is updated with the latest correction date.  All the lines must be updated with the latest transaction date.  

- When we try to post the general journal entry by using Account type as project and offset Account type as a vendor with the load on inventory and Reverse charge percentage 100%. The system is not allowing to post the entry and throwing an error as “the transaction on voucher INMF-00545 do not balance as per 3/25/2020 (Accounting currency: -2500, Reporting currency: -2500)”.  After this fix If posting the Project entry with the load on inventory and reverse charge percentage from the General journal system will allow posting without any imbalance error  

- Removed/inactive addresses are appearing again under Location on Tax Information form of Invoices that are generated through Invoice Journal/ Free Text Invoice. After this fix Removed/Inactive addresses will not appear again under location on the tax information form  

- Lookup Condition linked to two different component measure owners  

- Voucher details are not showing in the posted journal during the process of settling the Post-dated Cheque in the customer environment. After this fix Line will show on the grid.  

- Getting error message while posting invoice journal with multiple lines with TDS where exchange rate changed after creating lines in the invoice journal. After this fix System will post Invoice Journal (Multiline) transaction successfully including TDS where the exchange rate is changed after creating will lines in Invoice Journal. The system will pick the latest defined exchange rate for the whole transaction.  

- WHT tax group is not editable during invoice processing in India Legal Entity when posting transaction through Pending Invoice form.  After this fix TDS/ TCS group will be editable in Purchase order pending invoice form for the line. User will be able to update the TDS/ TCS related fields in pending invoice form during invoicing.  

- The system allows deleting the source details in the GST number sequence group. After this fix System will not allow deleting the source details in the GST reference number sequence group if attached to a transaction. If the user does not attach with the transaction and allowed to delete the source details than the user will be allowed to add it again.  

- Charges are not auto-updated in assessable value on the sales order line when user apply charges through Auto charges functionality. if the user marks assessable value checkbox in auto-charge setup. Charges are not auto-updating on the sales order line to include charge amount in the assessable value of goods. After this fix Charges will be auto-updated on the sales order line when user mark assessable value field in Auto charges setup and it will be part of the assessable value for tax calculation  

- Importing the general journal lines with tax through data import-export feature successfully but on verification of tax document, it is showing empty tax information for imported general journal transaction. To fix this issue updated the data entity "Ledger journal line transaction tax information".  

- When balancing financial dimension is updated in ledger form and the financial dimension is not set in the authority vendor, the user is getting the error: The transactions on voucher xxx do not balance as per xxx” This message is misleading. Under this fix when balancing the financial dimension is updated in ledger form, an error message will appear to check whether the financial dimension is set in the authorized vendor.   

- When create a new customer, it write a record TaxInformationCustTable_IN  with TaxInformationCustTable_IN.CustTable='', and then update it with the customer account number. When the second step cancelled by exception, the first step will not roll back and left the record there. it blocks to create customer later, because of column TaxInformationCustTable_IN.CustTable is a unique index of the table. It should not save the record with TaxInformationCustTable_IN.CustTable=''. After this fix when the CustTable field exists, records can be inserted into the related table.  

- BOE Assessable value is not updating as per Purchase order line Assessable value. After this fix  When a user creates new BOE after the cancellation of earlier one, the new Bill of entry will display the updated assessable value of import order line.  

- Importing data via data entity "Ledger journal line transaction tax information" thrown following  2 errors:  

          a. Matching record with key 'Registration Number': 29AGNPB4831B1Z1 for the data source 'GSTIN' does not exist  
          b. update not allowed for field 'TransTaxInformationEntity.TaxWithholdNatureOfAssessee' Under this fix updated the data entity "Ledger journal line transaction tax information" to resolve this.   

  
## Upcoming fixes in 10.0.13

- In the inter-company transaction one company post sales order and in another company purchase order is generated automatically. However, the location of the buyer 
  company in tax information is not defaulting correctly in the auto generated purchase order. After this fix in the auto generated purchase order tax location of 
  buyer company will default based on warehouse information attached with the purchase order. 
- When withholding tax transaction is posted in foreign currency than at the time of withholding tax settlement to authority imbalance error will pop up. After this 
  fix user will able to run settlement to authority successfully.  
- The withholding tax (TCS) is not getting calculated for inter-company purchase return order even after updating the line details. After this fix Withholding 
  tax (TCS) is calculated correctly for Inter-company Purchase return order after updating the line details. 
- Importing data via data entity "Ledger journal line transaction tax information" thrown error: 
  Results “ Matching record with key 'Registration Number': 29AGNPB4831B1Z1 for the data source 'GSTIN' does not exist” .This fix  will update the 
  data entity "Ledger journal line transaction tax information" to resolve the issue. 
- Vendor tax information is imported through data entity form then on refreshing data. System is allowing the user to select more than one primary tax information 
  details in  vendor tax information. After this fix system will restrict the user to enable more than one primary tax information details for a same vendor. 
- When customer is trying to do import purchase order the value of IGST tax is not getting displayed in Totals tab after doing purchase order totals 
  and purchase order invoice. After this fix value of IGST tax will displayed in Totals tab in purchase order and purchase order invoice. However, user has
  to enable check box in parameter to unable this option.  
- Field transaction type should be disabled in sales quotation form. User can manually add and update the field transaction type in sales quotation form. If it is 
  updated to a value except None or Expense, the Customer tax information will be invisible. Through this fix the field Transaction type will  only available
  for project quotations  and it will  not be available to enable on Sales quotation form. 
- While posting foreign vendor payment and applied withholding tax of Non-Residence.  If user changes currency rates on transaction, similar exchange rate not 
  applied for withholding tax calculation. instead it is taking from system. Due to this there is imbalance in posting and stopped posting the transaction. 
  With this fix vendor payment with TDS in foreign currency transaction will post successfully. 
 - System is not showing the tax adjusted amount at the time of bill of entry to tax document form of invoice posting form. After this fix system
   ax amount adjusted in  Bill of entry form will flow and display in tax document of posting Invoice form. 
-  BOE (Bill of entry) number column is present in Product receipt form but BOE number is not being displayed in the same. After this fix Bill of entry number will 
   default in lines of product receipt form 

-  Load on inventory tax  amount posting to Purchase expenditure for expense account instead of  Cost of project account/ Fixed asset account when purchase order placed 
   with procurement category (Transaction posted with  Project -vendor  or fixed asset – vendor combination ). After this fix tax amount will load to offset account.    

 - After posting the import PO invoice still system allows user to create invoice through pending vendor invoice form through product receipt option. With 
   this fix Once import PO invoice posted it will not be available in the pending vendor invoice form through Product receipt option. 

 
