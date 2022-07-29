---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.29 (September 2022)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.29 preview release.
author: kfend
ms.date: 07/29/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2022-08-01
ms.dyn365.ops.version: 10.0.29

---

# What's new or changed in Dynamics 365 Finance 10.0.29 (September 2022)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.29. This version has a build number of 10.0.xxxx and is available on the following schedule:

- **Preview of release:** August 2022
- **General availability of release (self-update):** September 2022
- **General availability of release (auto-update):** October 2022

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this article was initially published.

| Feature area | Feature | More information | Enabled by |
|----|----|----|----|
| Accounts payable | Match the detail for vendor invoices | Use the total invoice matching feature to match the details of the total invoice amount. The details of the invoice total amount include: Subtotal, Total discount, Charges, Sales tax, and invoice. | Feature maangement |
| Accounts payable | New data entities for vendor invoice charges  | This feature introduces a new data entity which allows you to import charges on the vendor invoice header or lines by using DMF or OData. | Default |
| Accounts receivable | Line creation sequence number  | You’ll have the option to create sequential **Line creation sequence numbers** when you post customer invoice lines. Line creation sequence numbers are assigned during the posting process. Allowing non-sequential numbering can improve customer invoice posting. The line creation sequence number may be used by third-party integrations that expect sequential ordering. Consult your IT department about any extensions that may integrate with the line creation sequence number. To set up or view this information, select **Assign sequential line numbers when posting customer invoice lines** on the **Updates** tab of the **Accounts receivable parameters** page. | Parameter | 
| Cash and bank management | Time zone for importing bank statements using Electronic reporting  | With this feature, you can specify a time zone when you import a bank statement using Electronic reporting. If statements are imported for multiple bank accounts at the same time, the time zone setting on the bank accounts will determine which time zone is used.  | Default |
| Cash and bank management | Reverse the debit and credit on imported  bank statement transactions using advanced bank reconciliation | In advanced bank reconciliation, imported bank statement transactions display as a credit, instead of debit and vice versa. Use this feature to reverse the debit and credit on imported bank statement transactions in advanced bank reconciliation. | Default |
| Cash and bank management | Ability to printing payment advice for vendor payments with status of Approved | Payment advice of vendor payments can be printed in both the **Approved** and **Sent** status. Previously, a payment advice with only a status of **Sent** was able to be printed. After you post a vendor payment journal, on the Action Pane, select **Print** > **Payment advice**. Select a payment advice with a **Payment status** of **Sent** or **Approved**. Use the payment advice to inform suppliers that money has been successfully remitted through the bank. An additional payment vendor status of **Approved** was added to the printed payment advice. For customers who connect Dynamics 365 Finance with their bank and synchronize the vendor payment journal status with bank information, this status is helpful in determining if bank transactions were successful. | Default |
| Fixed assets | Increase the length of fixed asset name  | This feature increases the length of the fixed asset name in Fixed assets up to 150 characters. This increase gives you more flexibility to adapt the fixed asset name in ways that better serve your organization's needs. Extending the data types that determine the length of fixed asset name won't adversely affect other extended data types. | Default |
| Fixed assets | Split transaction subtype | This feature ensures there is no dependency between the split journal’s description and the subsequent calculation of split calculations. This allows you to adopt the split journal description in ways that better serve your organization’s needs. The **Transaction subtype** is automatically set to split in the fixed asset journal line and fixed assets transactions.  | Default |
| Fixed assets | Amend fixed assets depreciation description | This feature gives better representation to the depreciation automatic description text by using the format of f**rom MM/DD/YYY to MM/DD/YYYY**. This clears the representation of the covered period for the depreciation.    | Default |
| General ledger    | Allow edits to internal data on general ledger vouchers    | This feature gives users who are assigned the Accounting manager and Accounting supervisor roles the ability to modify internal data on posted vouchers. The feature is currently limited to editing the **Description** field. An audit trail is maintained for all changes.   | Feature management    |
| General ledger    | Include or exclude reporting currency adjustments in the general ledger foreign currency revaluation  | When you run the general ledger foreign currency revaluation, you can select to include or exclude reporting currency adjustment transactions from the revaluation process. The default is to include reporting currency adjustments in the revaluation.   | Parameter    |
| Globalization    | (Russia) Import addresses from the State Address Register (GAR)    | Starting in version 10.0.29, address import is available in a new State Address Register (GAR) format: Import from GAR. For more information, see [Import from State Address Register (GAR)](https://go.microsoft.com/fwlink/?linkid=2200866)    | Feature management    |
| Globalization    | Global withholding tax |Starting in version 10.0.29, the global withholding tax currency exchange rate type and calculation date type can be specified for foreign currency transactions. For more information, see [Global withholding tax - Enable global withholding tax currency exchange rate type and date type setup](https://go.microsoft.com/fwlink/?linkid=2197949).    | Parameter    |
| Globalization    | Electronic Invoicing service – French e-invoice integration with Chorus Pro   | The configurable Electronic Invoicing service supports integration with French Chorus Pro and the automatic submission of electronic invoices in PEPPOL UBL Biz 3 format to the Chorus Pro Platform.   | Parameter   |
| Globalization    | Electronic Invoicing service – Configurable Polish e-invoice and integration   | The Configurable Electronic Invoicing service supports generating and submitting electronic invoices in the format legally required by Polish authorities.   | Parameter   |
|Globalization    | Electronic Invoicing service – Saudi Arabia e-invoice integration    | The configurable Electronic Invoicing supports submitting electronic invoices to Saudi Arabian tax authorities in the format legally required in Saudi Arabia.   | Parameter   |
| Subscription billing | Customer split billing | There are times where a billing schedule may need to be billed to more than one customer. With Customer split you can add additional customers, start and end dates and the percentage of the billing for the added customer. When the Generate invoice process runs, one sales order is created for the parent customer and one for each customer in Customer split page.  | Parameter |
| Subscription billing | Terminate one time billing | A billing schedule with a Billing frequency of One-time can be terminated after invoicing, creating a refund issued to the customer. Previously, after a One-time billing schedule was billed the status changed from Active to Terminated and you could not refund the customer through the Termination process. | Parameter |
| Subscription billing | Calculate unit price | The ability to calculate unit price or one-time billing lines has been added. This includes entity support for one-time billing lines with calculate unit price. | Default |
| Tax calculation    | Integration with the periodical journal    | [Tax Calculation integration with finance and operations apps](../localizations/global-tax-calcuation-service-overview.md)    | Parameter    |


## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/dynamics365-finance).

| Feature area | Feature name | More information |
|--------------|--------------|------------------|
| Credit and collections | Default dimensions for write-off account from original invoice's revenue account | This feature provides a new way to default the dimensions for a write-off transaction. When writing off a sales order invoice transaction, the dimensions for the write-off account will only default from the original sales order invoice’s ‘Revenue’ posting type. Previously, the default dimensions for the write-off account defaulted from all the original sales order invoice’s distribution posting types. Based on the original values posted to the dimensions, the system prorated the write-off value to the various dimensions. |
| Credit and collections | New option in interest calculation: Open and closed including grace period | Interest will only calculate on the overdue portion on invoices if they are partially paid within the grace period. Previously, the grace period was not included and interest would calculate on the entire invoice amount, including the amount partially paid. A new option has been added in the C**ollections parameter** page under **Interest calculation**. | 
| Credit management | Prevent update picking quantity and release to warehouse if a sales order is on hold | This feature checks for credit holds on sales orders when updating the pick quantity from the sales line item. Previously, if a sales order was in credit hold, the pick quantity could be updated. This feature will prevent a pick quantity on the line as well as not allow the release to warehouse if the sales order is in credit hold. |
| Accounts receivable | Assign employee responsible from other legal entities | On the customer or prospect, in the **Sales demographics** tab, the **Employee responsible** field is no longer restricted to just the current legal entity. When the parameter is set to **Yes** you can assign an employee responsible to a customer or prospect from another legal entity.  Set the new parameter in **Accounts receivable parameters** page on the **General** tab. | 
| Subscription billing | Unbilled revenue discount account added along with Use unbilled offset accounts | The Unbilled revenue setup page now has Unbilled discount account to track any discounts on the billing schedule using Unbilled revenue. The Use unbilled offset accounts parameter can be set when billing schedules are setup in currencies other than the accounting currency. These two accounts will ensure the Unbilled accounts are using the proper exchange rates when invoicing the billing schedule. | 
| Subscription billing | Sales tax group | When creating a sales order from a billing schedule the sales tax group will default based on the delivery address when the terms of delivery of the customer has Sales tax address set to Delivery.  |
| Tax calculation   | Tax Calculation service   | Use customer/vendor tax exempt numbers from the document header as tax group applicability conditions to determine matrix output. For more information, see [Multiple VAT registration numbers](../localizations/emea-multiple-vat-registration-numbers.md).                  |
| Tax calculation   | Tax Calculation service  | The loading address on a free text invoice header can be used as the ship from address to build applicability rules. For more information, see [Tax calculation data model](./localizations/tax-calculation-data-model-overview.md). |
| Tax calculation   | Tax Calculation service     | The **Adjust execution sequence** function is available now in the applicability rule matrix to support adjusting applicability rule execution seuqnce within the same weight. For more information, see [Sales tax applicability and sales tax group determination logic](../localizations/global-sales-tax-group-determination.md#matching-logic).  |
| Budget Control | Budget control document filtering enhancement  | You can use the new query-based filter option for each document that's included in budget control to specify which budget control documents are budget checked. This release adds the ability for journals to be filtered by a user-defined query extending this feature from the prior release. |
| Budget Control| Budget control data maintenance - Journal reprocessing | This enhancement to budget control data maintenance allows for reprocessing budget data for journal documents. |
| General Ledger| Default journal sorting direction | This journal enhancement allows you to select the journal list to have the default sorting set to either ascending or descending by journal batch number. The sorting direction is set in the General ledger parameters.|
| Globalization | Indonesian Commercial invoice and tax invoices  | A commercial invoice can be issued in a foreign currency, while the tax invoice (which is a file created as a subset of data in the commercial invoice) must always be in the local currency. Commercial invoices can have separate numbering, different from the numbering of e-invoices as mandated by the authorities. |
| General ledger    | Ability to edit the fiscal year name  | A new dialog has been added to the **Fiscal calendar setup** page which you can use to change the name of a fiscal year within the selected fiscal calendar.      |
| General ledger | Dimension statement data limitation | The dimension statement is now limited to run for 31 days or less. If transaction detail is necessary for a larger date range, use the General journal account entry reporting entity. |
| General ledger  | Require year-end close to be run in fiscal year order | When you run the general ledger year-end close, the previous fiscal year must be closed before you can run the close for the selected fiscal year. This requirement ensures that the correct balances exist in the fiscal year being closed.    |

## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Finance 10.0.29 includes platform updates. To learn more, see [Platform updates for version 10.0.29 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-29.md).

### Bug fixes

For information about the bug fixes included in this update, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=xxxxx).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to LCS and view the planned regulatory updates using the issue search tool. Issue search lets you search by country, type of feature, and release.

### Dynamics 365 and industry clouds: 2022 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2022 release wave 1 plan](/dynamics365-release-plan/2022wave1/finance-operations/dynamics365-finance). We've captured all the details, end to end, top to bottom, that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article describes features that have been removed or deprecated for Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
