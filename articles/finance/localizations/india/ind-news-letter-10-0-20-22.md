---
title: What's new or changed for the India localization in 10.0.20-10.0.22
description: Learn about new or changed functionality for India localization features in Microsoft Dynamics 365 Finance versions 10.0.20 through 10.0.22.
author: prabhatb
ms.author: prabhatb
ms.topic: whats-new
ms.custom:
  - bap-template
  - evergreen
ms.date: 07/15/2024
ms.reviewer: johnmichalak 
ms.search.region: India
ms.dyn365.ops.version: 10.0.20, 10.0.21, 10.0.22
---

# What's new or changed for the India localization in 10.0.20-10.0.22

[!include [banner](../../includes/banner.md)]

This article provides a summary of the new features and critical bug fixes that were released in Microsoft Dynamics 365 Finance versions 10.0.20 through 10.0.22 for the India localization.

## Released critical fixes

### 10.0.20

- The **Invoice amount** field isn't refreshed when the tax amount is changed. After this fix, when updates are made to the Harmonized System of Nomenclature (HSN) code/Service Accounting Code (SAC) in the tax information form of the proposal, the **Invoice amount** field on the project invoice proposal header correctly updates and calculates the tax.
- For a sales return, the **Posted withholding tax** page has no Tax Collected at Source (TCS) value and is blank. After this fix, the **Posted withholding tax** page shows data even when the data is posted after the source document transaction date.
- If the **Enable uniform tax amount and GST transaction ID For both shipment and receipts transaction of a stock transfer order** feature is enabled, GST isn't calculated when a stock transfer order is received. After this fix, GST is correctly calculated when a stock transfer order shipment is received.
- Multi-line debit note transactions appear in the **Invoice and bill of supply** section of the GSTR-2 report instead of in the **Debit/credit note** section. After this fix, multi-line debit note transactions appear in the **Debit/credit note** section, regardless of the line number and regardless of whether the transactions include tax.
- Tax Deducted at Source (TDS) is incorrectly calculated on the purchase invoice for a foreign vendor if the exchange is manually updated. After this fix, TDS for foreign transactions is correctly calculated based on the TDS exchange rate for the purchase invoice, even when the exchange rate is manually updated for the transaction.
- Company tax information for charges is shown instead of warehouse tax information from the purchase line. This fix synchronizes the warehouse location of the charge tax information with the purchase order line location of the warehouse tax information. Therefore, the tax information for charges will match the purchase line tax information.
- Tax posting performance must be optimized when a sales order is invoiced. After this fix, **SaleParmLine::findInventTransId** is cached to help reduce the round trips in the database. Performance is also improved in several sales order posting and printing scenarios. Use this fix together with KB 4615799.

### 10.0.21

- The **Transaction ID** and **Transaction date** fields disappear from the **Posted tax document transaction** report after the registration number is added. This issue is a known issue with the old personalization subsystem. However, it no longer exists after the **Saved views** feature is enabled. (The **Saved views** feature was made generally available in version 10.0.13.) To fix the issue, consider enabling the **Saved views** feature.
- Invoices that are marked as **Export Order** aren't included on the GSTR-1 report. For example, a free text invoice that has the **With the payment of tax** option set to **No** and that is created for a foreign customer isn't included on the report. This invoice should be included on the export sheet in the GSTR-1 Govt. offline tool, and the export type should be set to **WOPT**.
- Tax is incorrectly calculated when a purchase order is created from a sales order. To work around this issue, clear the customer location on the purchase order, and update the vendor location after the tax information is copied from the sales order.
- Tax on a project invoice is incorrectly calculated when a project sales order is created from an item requirement. After this fix, the assessable tax value is derived from the value on the packing slip, and tax is calculated accordingly.
- During the settlement process, reversed GST entries aren't visible on the **Tax adjustment** page. After this fix, the reversed GST entries are included in the settlement process.
- The system doesn't generate a credit note number sequence when the tax rate for a free text invoice is 0 (zero). After this fix, the system generates a credit note number sequence when a free text invoice is posted that has a negative value and a tax rate of 0 (zero).
- Because of a missing default dimension in the vendor transactions of withholding tax, a balancing error occurs when a check is reversed. This issue has been fixed by adding the default dimension to the vendor transactions of withholding tax.
- A general journal reversal doesn't show the TCS amount on the **Vendor transaction** page. After this fix, when you reverse the General journal, the system creates a new **VendTrans_W** record that includes the TCS/TDS amount on the **Vendor transaction** page.
- When you try to post a withholding tax journal, you receive the following message: "Changing current field will void the tax adjustment journal and journal will be treated as a regular general journal. Do you wish to continue?" After this fix, you should be able to post the withholding tax journal without encountering any error.

### 10.0.22

- When you update the **India - tax information** tab on a project invoice proposal, the following error occurs: "Error executing code: The field with ID '0' does not exist in table 'SalesPurchJournalLine'." After this fix, in the **ProjCostTrans** table, no **InventDimID** will return an empty value in the corresponding **TaxModelDocLine** class.
- Sales order invoices can't be posted because the following error occurs: "Reference number sequence groups is not specified in the tax information for the location." When a supplier, receiver, or supply location is outside India, no GST reference ID is required for the transaction.

## Upcoming critical fixes in 10.0.23

### The IN-GSTR report is generated for only 30 days

When you generate a GSTR report through a batch job, the system should generate the report for the selected date range. For example, if the date range is August 1 through August 31, the batch job must generate a report for 31 days.

### The IN-BOE cancel option isn't enabled after a product receipt is canceled

After a product receipt for an import order is canceled, the **Cancel** button is available in the Bill of entry (BOE) journal, and you can cancel the posted BOE.

### Because of an issue with assessable value updates, GST isn't calculated on an invoice proposal for the expense journal 

GST must be calculated on an invoice proposal for the expense journal. The assessable value for sales must also be updated and saved.

### A validation message is shown when you create an item requirement from the master project for a project where a contract is listed for a customer that has an updated TCS/TDS group

After you create a new line where you don't select an item or category, and where the **TCS group** field is set to the default value from the customer account, you receive the following message when you create the next new line: "Item or category must be specified." If no item or category is selected on an existing line, that message should not be shown when you try to create a new line.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
