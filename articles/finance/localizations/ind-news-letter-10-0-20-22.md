---
# required metadata

title: What's new or changed for the Indian GST localization in 10.0.20-10.0.22
description: This topic describes new or changed functionality for Indian Goods and Services Tax (GST) features in Microsoft Dynamics 365 Finance versions 10.0.20 through 10.0.22.
author: prabhatb
ms.date: 10/20/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: prabhatb
ms.search.validFrom: 
ms.dyn365.ops.version: 10.0.20, 10.0.21, 10.0.22

---

# What's new or changed for the Indian GST localization in 10.0.20-10.0.22

[!include [banner](../includes/banner.md)]

This topic provides a summary of the new features and critical bug fixes that were released in Microsoft Dynamics 365 Finance versions 10.0.20 through 10.0.22 for the Indian Goods and Services Tax (GST) localization.

## Released critical fixes

### 10.0.20

- The **Invoice amount** field isn't refreshed when the tax amount is changed. After this fix, when updates are made to the **HSN/SAC** code in the tax information form of the proposal, the **Invoice amount** field on the project invoice proposal header updates and calculates the tax correctly.
- For a sales return, the **Posted withholding tax** page has no TCS value and is blank. With this fix, the **Posted withholding tax** page shows data even when the data is posted after the source document transaction date.
- GST isn't calculated when a stock transfer order is received if the feature, **Enable uniform tax amount and GST transaction ID For both shipment and receipts transaction of a stock transfer order** is enabled. With this fix, GST is calculated correctly when a stock transfer order shipment is received. 
- Multi-line debit note transactions appear under the **Invoice and bill of supply** section of the GSTR2 report instead of the **Debit/credit note** section. With this fix, in multi-line debit note transactions appear in the **Debit/credit note** section regardless of line number or whether the transactions include tax.
- TDS on the purchase invoice for a foreign vendor is calculated incorrectly if the exchange is manually updated. After this fix, TDS for foreign transactions is calculated correctly based on the TDS exchange rate for the purchase invoice even when the exchange rate is manually updated for the transaction.
- Company tax information for charges is being displayed instead of warehouse tax information from the purchase line. This fix synchronizes the warehouse location of charge tax information with the purchase order line location of the warehouse tax information. This means that the tax information for the charges will be the same as the purchase line tax information.   
- When invoicing a sales order, the tax posting performance needs to be optimized. WIth this fix, **SaleParmLine::findInventTransId** is cached and this would help reduce the round trips in the database. The performance will also improve several sales order posting and printing scenarios. Use this fix together with KB 4615799.

### 10.0.21

- The **Transaction ID** and **Transaction date** are disappearing from the **Posted tax document transaction** report after the registration number is added. This is a known issue with the old personalization subsystem; however, this issue no longer exists once the Saved views feature, 
                      which was made generally available with 10.0.13 / Platform update 37, has been enabled. Please consider enabling this feature. 
•	IN -Invoices marked as Export Order does not come in GSTR-1 New Report : 
      Free text invoice posted with foreign customer for service item and marked the invoice as "With the payment of tax- No". 
      This transaction should display in GSTR-1 Govt. offline tool under the export sheet and flagged as " WOPT " as export type. 
•	IN- Tax is getting calculated wrongly when the purchase order was created from the sales order. 
                   The User must Clear PO's customer location and update its vendor location after the tax information is copied from SO. 
•	IN-Project sales order is created from Item requirement observed in Project invoice proposal tax is getting wrongly computed for partial sales order 
                   The assessable value would be derived based on the value on the packing slip and tax would be calculated accordingly. 
•	IN- Issue in GST Settlement Process, Reversed GST entries is not visible in Tax Adjustment Form:  
                    After this fix, the reversed GST entries will be included in the settlement process. 
•	IN-system is not generating credit note number sequence when the tax rate is zero for free text invoice  
                    The system will generate a credit note number sequence when a free text invoice is posted with a negative value with a zero tax rate. 
•	IN- Balancing error while reversing the check 
                   The issue is due to the missing default dimension in vendor transactions of withholding tax. The issue is fixed by adding the default dimension 
                   to the vendor transactions of withholding tax. 
•	IN General Journal reversal not showing TCS amount on the vendor transaction page 
                   After this fix when performing General Journal reversal, the system will create a new VendTrans_W record which would display 
                   the TCS/TDS amount on the vendor transaction page. 
•	The system is prompting a message indicating that “Changing current field will void the tax adjustment journal and journal will be treated as a regular general journal. Do you wish to continue? 
                   After this fix User should be able to post the withholding tax Journal successfully without any error. 


### 10.0.22

- When you update the **India - tax information** tab on a project invoice proposal, the following error occurs, **Error executing code: The field with ID '0' does not exist in table 'SalesPurchJournalLine'**. After this fix, in the **ProjCostTrans** table, no **InventDimID** will return an empty value in the corresponding **TaxModelDocLine** class.
- Sales order invoices can't be posted because of the error, **Reference number sequence groups is not specified in the tax information fo the location**. When a supplier, receiver, or supply location is outside of India, there is no need to have a GST reference ID For the transaction. 

## Upcoming critical fixes in 10.0.23

### IN-GSTR report is generated for only 30 days

To provide a better performance experience, TDS and TCS inquiries will be included on the **Posted Withholding tax** inquiry page.

### IN-BOE cancel option isn't enabled after a product receipt in canceled

The upcoming release will fix an issue where the system selects the base value of a sale price at the item level but doesn't select the net amount value of the assessable value for an item-type bill of materials (BOM).

### GST isn't calculated in an invoice proposal for the expense journal because of an assessable value refresh issue

When you select the plus sign (**+**) to create vendor invoice lines, GST might not be applied when a vendor invoice is posted. The upcoming release will fix this issue.

### A validation message occurs when you create an item requirement from the master project for a project with a contract listed to a customer iwth an updated TCS/TDS group

When a sales return order that is posted has TCS, the posted withholding tax is blank. If a sales return invoice is posted at a time other than the transaction date of the source document, the issue occurs. For example, if the source document is posted on February 25, 2021, and the sales return is invoiced today, the sales return transactions on the **Posted withholding tax** page are blank. The upcoming release will enable TCS to be posted on sales return orders.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
