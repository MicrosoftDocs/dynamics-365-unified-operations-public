---
# required metadata

title: What's new or changed for the Indian GST localization in 10.0.20-10.0.22
description: This topic describes new or changed functionality for Indian Goods and Services Tax (GST) features in Microsoft Dynamics 365 Finance versions 10.0.20 through 10.0.22.
author: prabhatb
ms.date: 10/22/2021
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

- The **Transaction ID** and **Transaction date** disappear from the **Posted tax document transaction** report after the registration number is added. This is a known issue with the old personalization subsystem. This issue no longer exists however, after the feature, **Saved views**, which was made generally available in version 10.0.13, is enabled. Consider enabling this feature to resolve the issue.
- Invoices marked as **Export Order** aren't included in the GSTR-1 report. For example, a free text invoice that is marked as **With the payment of tax- No** and is created for a foreign customer will not be included in the report. This invoice should be included in the GSTR-1 Govt. offline tool under the export sheet and flagged wtih **WOPT** as the export type. 
- Tax isn't calculated correctly when a purchase order is created from a sales order. To work around this issue, clear the customer location on the purchase order and update the vendor location after the tax information is copied from the sales order. 
- Tax on a project invoice is calculated incorrectly when a project sales order is created from an item requirement. After this fix, the assessable tax value is derived based on the value on the packing slip and tax would be calculated accordingly. 
- During the settlement process, reversed GST entries aren't visible on the **Tax adjustment** page. After this fix, the reversed GST entries will be included in the settlement process. 
- The system isn't generating a credit note number sequence when the tax rate is zero for a free text invoice. After this fix, the system will generate a credit note number sequence when a free text invoice is posted with a negative value and a zero tax rate. 
- A balancing error occured while reversing the check because of a missing default dimension in the vendor transactions of withholding tax. This issue has been fixed by adding the default dimension to the vendor transactions of withholding tax. 
- A general journal reversal doesn't show the TCS amount on the **Vendor transaction** page. After this fix, when you reverse the General journal, the system will create a new **VendTrans_W** record which will include the TCS/TDS amount on the **Vendor transaction** page. 
- The meessage, **Changing current field will void the tax adjustment journal and journal will be treated as a regular general journal. Do you wish to continue?** occurs when you try to post a withholding tax journal. After this fix, you should be able to post the withholding tax journal without any error. 

### 10.0.22

- When you update the **India - tax information** tab on a project invoice proposal, the following error occurs, **Error executing code: The field with ID '0' does not exist in table 'SalesPurchJournalLine'**. After this fix, in the **ProjCostTrans** table, no **InventDimID** will return an empty value in the corresponding **TaxModelDocLine** class.
- Sales order invoices can't be posted because of the error, **Reference number sequence groups is not specified in the tax information fo the location**. When a supplier, receiver, or supply location is outside of India, there is no need to have a GST reference ID For the transaction. 

## Upcoming critical fixes in 10.0.23

### IN-GSTR report is generated for only 30 days

When you generate a GSTR report through a batch job, the system should generate the report per the selected date range. For example, if the date range is 1 August - 31st August then batch job must generate a report for 31 days. 

### IN-BOE cancel option isn't enabled after a product receipt in canceled

After a product receipt for an import order is canceled, the **Cancel** button is enabled on the BOE Journal and you can cancel the posted BOE. 

### GST isn't calculated on an invoice proposal for the expense journal because of an assessable value refresh issue

GST must be calculated on an invoice proposal for the expense journal. The assessable value for sales must also be updated and saved. 

### A validation message occurs when you create an item requirement from the master project for a project with a contract listed to a customer with an updated TCS/TDS group

If you create a new line, and no item or category is selected and the **TCS group** field value defaults from the customer account, when you create the next new line, the message, **Item or category must be specified** will occur. The message shouldn't occur when there is no item or category selected on an existing line and you try to create a new line. 
 

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
