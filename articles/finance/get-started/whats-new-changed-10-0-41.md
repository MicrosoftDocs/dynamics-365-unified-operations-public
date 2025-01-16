---
title: What's new or changed in Dynamics 365 Finance 10.0.41 (September 2024)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.41 preview release distributed in September 2024.
author: twheeloc
ms.author: twheeloc
ms.topic: faq
ms.date: 9/17/2024
ms.custom:   
  - bap-template
  - evergreen
ms.reviewer: twheeloc
ms.search.region: Global
---

# What's new or changed in Dynamics 365 Finance 10.0.41 (September 2024)


[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article lists the features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.41. This version has a build number of 10.0.2015.16 and is available on the following schedule:

- **Preview of release:** July 2024
- **General availability of release (self-update):** September 2024
- **General availability of release (auto-update):** October 2024

## Features included in this release

This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Accounts payable | Enable financial tags for purchase order invoicing | This feature takes advantage of financial tags to help track processes and ensure accurate analysis of financial data across procurement-to-pay transactions. | Feature management |
| Accounts receivable | Prepayment customer invoice feature | This feature creates and manages invoices for customer prepayments. Customers can issue prepayment invoices to require a deposit before a sales order is fulfilled. | Feature management |
| Accounts receivable | Free text invoice performance boost | <p>The increasing volume of data was causing the free text invoice page in Dynamics 365 Finance to be loaded slowly. It was also causing performance issues when the workflow was enabled. To address these issues, two key changes were made:</p><ul><li>The **All free text invoices** menu item now shows only invoices that have a status of **Not posted**.</li><li>A new **Optimized invoice loading page** menu item provides a streamlined interface and faster data loading capabilities.</li></ul> | Feature management |
| Cash and bank management | Modern bank reconciliation | This feature improves the usability and performance of advanced bank reconciliation and provides feature enhancements. Several new capabilities are available on the bank reconciliation worksheet. For example, there are capabilities to clear reversal company transactions, generate vouchers and payment journals, and settle open customer invoices. Bank reconciliation matching rules are enhanced to automatically run these capabilities through user-defined criteria. This feature is generally available for production environments in Dynamics 365 Finance version 10.0.41. | Feature management |
| Cash and bank management | Automatic clear bridged transactions through advanced bank reconciliation | This feature automatically clears bridged payment transactions through bank reconciliation. The transactions don't have to be manually cleared in the general ledger. Users can set up a bridging account for each bank account. This feature is generally available for production environments in Dynamics 365 Finance version 10.0.41. | Feature management |
| Cash and bank management | Skip reversal flag validation when matching reversal bank statement lines | A mandatory validation determines whether one of the bank statement lines has the reversal field set to **Yes** to match the corresponding original statement line. This new feature skips the validation for manual matching and provides a configurable parameter for matching rule setup. This feature is generally available for production environments in Dynamics 365 Finance version 10.0.41. | Feature management |
| Cash and bank management | Enable batch mode for bank statement and bank statement line posting in advanced bank reconciliation | This feature enables batch processing option for bank statement posting and bank statement line posting in bank reconciliation worksheet. To post bank statement lines in bank reconciliation worksheet, the **Enable posting of new transactions in bank reconciliation** feature has to be enabled. | Feature management |
 |Credit and collections |	Customer balance statistics deletion job	 |Users can efficiently manage long-term data stored in the Customer balance statistics table. This enhancement includes a **Delete outdated balance statistics records** periodic task designed to remove unnecessary records from the table, alleviating potential performance impacts associated with data overload. |	Feature management |
 |Credit and collections	 |Customer data maintenance |	A new data maintenance page is available that streamlines data consistency. This page allows customers to view and manually retry failed updates, and resolve issues without relying on support tickets.  |	Feature management |
| Fixed assets | Consider split transaction in derived books posting (Public preview) | This feature automates the process of posting split transactions from the main book to specified derived books, based on the configuration that is set up on the **Asset book** page. That configuration defines how transactions are posted based on transaction type. After the feature is enabled, split transactions are automatically posted according to the predefined settings. Therefore, manual intervention isn't required. | Feature management |
| Fixed assets | Allow depreciation when placed in service and disposal are in the same fiscal year (Public preview) | This feature allows for depreciation when assets are put into service and disposed of during the same fiscal year. When the **Allow depreciation when placed in service and disposal are in the same fiscal year** option is enabled on the **Fixed assets parameters** page, depreciation is calculated when an asset is both put into service and disposed of during the same fiscal year. This setting is the default behavior for any new asset books that are created. Changes at the asset book level apply only to new asset books that are created after those changes are made. They don't retroactively affect existing asset books. | Feature management |
| Fixed assets | Lease import framework update | This feature involves enhancements to Asset leasing's lease import framework and affects two tables: `AssetLeaseLeaseImportHeader` and `AssetLeaseLeaseDetailsImport`. Additional functionality allows for easier deletion in the lease import records. | |
| General ledger | Validation feature for year-end close process | This feature validates the year-end closing to detect issues. If any issues are found, the feature suggests a resolution. This feature ensures accurate ledger balances in both accounting and reporting currencies, and recommends best practices for managing large dimension sets. | |
| Tax | Enable Include corrections option on Sales tax settlement periods | The **Include corrections** option affects the sales tax settlement process and periodic sales tax reporting. This feature controls the **Include corrections** option for each sales tax settlement period instead of the whole legal entity. | Feature management |
| Tax (India) | Add and synchronize tax hierarchy versions in batch mode | This feature improves performance when a sales tax hierarchy version is added and synced, by enabling the processes to run in batch mode. | Feature management |
| Tax | Adjust sales tax amount per vendor charged sales tax | The **Accrue sales tax type - adjustment** feature in the vendor master and the vendor invoice header allows for the vendor charged sales tax amount to be entered on the vendor invoice header. This amount overrides the sales tax result calculated using sales tax adjustment. | Feature management |
| Electronic Invoicing | E-Invoicing for Panama: ISV last-mile connector with Edicom | This feature is the last-mile integration with the Panamanian Tax Authorities via the Edicom certification authorization provider. It provides the required end-to-end process for the outbound flow of electronic invoice submission. For more information, see [Get started with Electronic invoicing for Panama](../localizations/iberoamerica/ltm-panama-ei-connec-configuration.md). | |

## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Cash and bank management | Modern bank reconciliation | When the **Modern bank reconciliation** feature is enabled, bank statement reconciliation matching rule functionality is improved for the **Settle customer invoice** and **Generate customer payment** actions. This improved functionality enables automatic searches of a customer account, based on a matching customer bank International Bank Account Number (IBAN). | Feature management |
| Cash and bank management | Modern bank reconciliation | When the **Modern bank reconciliation** feature is enabled, users can define a journal description when a voucher or payment journal is generated during the bank reconciliation process. | Feature management |
| Cash and bank management | Modern bank reconciliation | When the **Modern bank reconciliation** feature is enabled, customers can define financial dimensions when a general voucher is generated during the bank reconciliation process. | Feature management |
|Credits and collections|	Customer payment journals|	Payment journals with multiple payment lines, with undisputed collections status, is now faster and more efficient.|  |
|Credits and collections|	Customer aging report	|Performance improvement when calculating the aging bucket balances in the customer aging report.|  |
| Subscription billing | Use fiscal data from invoice account includes sales order from subscription billing | When the **Use fiscal data from invoice account** feature is enabled, sales orders that are created from billing schedules in Subscription billing now follow the setting on the **Accounts receivable parameters** page. If the setting is **Always**, the fiscal data on the sales order comes from the invoice account. | Feature management |
| Subscription billing | Performance improvement for the **Schedules lines inquiry** report for deferrals | On the **Schedules lines inquiry** report, the inquiry has been changed to set-based. This change, together with a new date restriction and the relocation of the totals to a button at the top of the page, significantly speed up the display of the inquiry report. | Default on |
| General ledger | Reset workflow approval status for unposted journals | A new periodic task lets administrators reset the workflow approval status of a journal entry to **Draft** or **Not submitted**. A journal can be reset if it belongs to the current entity, it isn't posted, and it isn't a system-blocked journal. | Default on |
| General ledger | OANDA Central Banks currency provider option added | A new currency provider option of OANDA Central Banks is available to select in the **Configure exchange rate providers** page. This new provider option allows you to select a supported central bank for the exchange rates. Contact OANDA directly for the updated key and full list of central banks you can use.  | Default on |
| Tax calculation | Support multiple VAT registration numbers for Sales orders | The restriction has been removed for the scenario where sales tax codes are assigned to different registration numbers under the same sales order. Invoice posting requires a single value-added tax (VAT) number. You can't have different VAT registration numbers on the same invoice. During sales invoice posting, order lines that have the same VAT registration are included in one invoice. Sales orders that have different VAT registrations at the line level are split into separate invoices. Validation is managed by the **Check tax registration number in document lines** parameter on the **Accounts receivable parameters** page. The parameter options are **None**, **Warning**, and **Error**. | Parameter |
| Tax (India) | Copy the assessable value and TCS/TDS group from the original item journal. | The assessable value is copied when the standard copy functionality is used on item journals. Tax information is initialized with default values instead of being copied from the original journals. This behavior remains unchanged for tax information. | Default on |
| Tax calculation | Customer type and vendor type in the standard data model | The standard data model is extended through the following fields on the header: **Customer account type**, **Customer invoice account type**, **Vendor account type**, and **Vendor invoice account type**. | Tax configuration |
| Tax | Global withholding tax performance improvement | The performance of the withholding tax calculation process is improved when customer or vendor invoices are settled. | Default on |
| Tax (India) | Performance improvements for posting journals | Posting performance is improved when there is a large volume of journal entries where India's Goods and Services Tax (GST) is applied. | Default on|
| Electronic Invoicing | E-Invoicing for Chile: Vendor electronic invoice import | This feature enhances the last-mile integration with the Chilean Tax Authorities via the Edicom certification authorization provider. It provides the required end-to-end process for the inbound flow of electronic invoice import. For more information, see [Vendor electronic invoice import in Chile](../localizations/iberoamerica/ltm-chl-vend-e-invoice.md). | |
| Regulatory reporting | VAT declaration for Lithuania | New **VAT declaration XML (LT)** and **VAT declaration Excel (LT)** ER formats are introduced under the **Tax declaration model**. For more information, see [VAT declaration for Lithuania (FR0600)](../localizations/lithuania/emea-ltu-vat-declaration-lithuania.md). | |

## Features turned on by default in this release

The following table lists the features that are turned on by default in version 10.0.41. Most features that have been turned on atomically can be turned off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). In the future, some features that have been turned on automatically might be removed from Feature management and will become mandatory. This change ensures that customers are using current functionality, so that as enhancements are added, they can build on the current functionality. Features will never be automatically enabled in less than one year, unless they are determined to be essential.

| Feature name | Feature state | Module |
|--------------|---------------|--------|
| Vendor invoice automation with tax registration | On by default | Accounts payable |
| Enable recurring Accounts payable invoice | On by default | Accounts payable |
| Vendor invoice register approved | On by default | Accounts payable |
| Enable external tax solution providers for Tax calculation service (Universal tax rate API) | On by default | Tax |
| Enable the Global general journal page to select multiple companies for posting | Mandatory| General ledger |
| Delete journal performance using batch | Mandatory | General ledger |
| Sales tax rate on invoice date in purchase order credit note | Mandatory | Tax |
| (India) Enable initial TDS threshold under section 194Q | On by default | Tax |
| Tax in transfer order | Mandatory | Tax |
| Control zero-amount sales tax difference entries for Czech Republic (CZ) | Mandatory | Tax |
| (India) GST/TDS-TCS tax support for Project integration journal | On by default | Tax |
| Tax calculation service | Mandatory | Tax |
| Credit and collections analytics performance improvements| Enabled by default |	Credit and collections|
| Consistency check for tax transaction general journal account entry association for bank exchange rate | On by default | Tax |
| Display vouchers in bank statement | Mandatory | Cash and bank management |
| Advanced bank reconciliation improvement: enable group conditions in reconciliation matching rules | Mandatory | Cash and bank management |
| Advanced bank reconciliation improvement: enable filtering and provide separate grid for new transactions | Mandatory | Cash and bank management |
| Automatic importing bank statement from SharePoint folder | Mandatory | Cash and bank management |
| Enable batch mode for **Mark as reconciled** in advance bank reconciliation | Mandatory | Cash and bank management |
| Reverse correction amount in advanced bank reconciliation when use bank statements as confirmation of electronic payments parameter is enabled | On by default | Cash and bank management |
| Use the time zone option on the **Bank statement import** page for BAI2 format bank statement ID generation | On by default | Cash and bank management |
| Petty cash | On by default | Cash and bank management |
| Enable check number validation | On by default | Cash and bank management |
| Exchange rate type enhancement for accounts payable and accounts receivable foreign currency revaluation | On by default | Cash and bank management |
| Exchange rate type enhancement for bank foreign currency revaluation | On by default | Cash and bank management |
| Accounts payable and accounts receivable foreign currency revaluation performance improvement by splitting into even batches | On by default | Cash and bank management |

## Features removed from Feature management

The following table lists the features that have been removed from Feature management in version 10.0.41.

| Feature name | Feature state | Module |
|--------------|---------------|--------|
| Support batch input of tax codes in tax group setup and item tax group setup. | The related functionality is enabled out of the box. | Tax |
| (Russia) Tax differences registers by balance method | The related functionality is enabled out of the box. | Tax |
| Calculate origin amount for sales tax specification by ledger transaction report. | The related functionality is enabled out of the box. | Tax |
| Tax setup validation | The related functionality is enabled out of the box. | Tax |
| Performance improvements for VAT register transactions page. | The related functionality is enabled out of the box. | Tax |
| Generate GST transaction ID at export invoice posting. | The related functionality is enabled out of the box. | Tax |
| Tax settlement rounding based on the customized currency decimal places. | The related functionality is enabled out of the box. | Tax |
| (Poland) Tax exempt number in sales tax transactions. | The related functionality is enabled out of the box. | Tax |
| Sales tax rate on invoice date in vendor invoice journals. | The related functionality is enabled out of the box. | Tax |
| Packing slip date as the delivery date for sales tax calculation (sales tax rate determination). | The related functionality is enabled out of the box. | Tax |
| Enable tax registration data advanced search for reports. | The related functionality is enabled out of the box. | Tax |
| Copy tax registration number as default VAT exempt number. | The related functionality is enabled out of the box. | Tax |
| Keep GST tax document for confirmation journal. | The related functionality is enabled out of the box. | Tax |
| Disable Russian address format validation. | The related functionality is enabled out of the box. | Tax |
| Separate sales tax payment report generation from sales tax settlement. | This feature is now controlled by the **Print report** option during sales tax settlement. | Tax |
| Sales tax payment performance improvement. | This feature is now controlled by the **Combine transactions for tax settlement** parameter on the **General ledger parameters** page. | Tax |
| Populate financial dimensions to the realized currency adjustment profits/loss accounts for sales tax settlement | This feature is now controlled by the **Populate financial dimensions for sales tax settlement** parameter on the **General ledger parameters** page. | Tax |
| (India) Reversal of vendor TDS at the time of settlement when deducted on both the invoice and payment. | The related functionality is enabled out of the box. To disable this feature, enable the **Disable vendor TDS reversal for duplicate deduction** parameter on the **General ledger parameters** page. | Tax |
| Ability to post detailed vendor and customer payments, but summarize amounts to bank account | The related functionality is enabled out of the box. | Cash and bank management |
| Enhanced filtering on the cash position inquiry | The related functionality is enabled out of the box. | Cash and bank management |
| Calculate the average exchange rate based on the main account code only | The related functionality is enabled out of the box. | Cash and bank management |
| (Italy) Posting invoices with zero amount | The related functionality is enabled out of the box. | Accounts payable, Accounts receivable, and General ledger |
| Product name translation fix | The related functionality is enabled out of the box. | Accounts receivable |


## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.41 includes platform updates. To learn more, see [Platform updates for version 10.0.41 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-41.md).

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=948711).


### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle Services and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2024 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2024 release wave 2 plan](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-finance). We've captured all the details, end to end, top to bottom, that you can use for planning.
