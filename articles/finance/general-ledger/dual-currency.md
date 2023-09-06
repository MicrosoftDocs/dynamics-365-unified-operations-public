---
# required metadata

title: Dual currency
description: This article provides information about dual currency, where the reporting currency is used as a second accounting currency for Microsoft Dynamics 365 Finance.
author: kweekley
ms.date: 04/17/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerJournalTable, Ledger, AssetTransReportingCurrencyAmountsWizard,BankAccountTransReportingCurrencyAmountsWizard, LedgerTrialBalanceListPage
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom:
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2018-10
ms.dyn365.ops.version: 8.1

---

# Dual currency

[!include [banner](../includes/banner.md)]

Functionality that was introduced in Microsoft Dynamics 365 Finance version 8.1 (October 2018) enables the reporting currency to be repurposed and used as a second accounting currency. This functionality is referred to as *dual currency*. The changes for dual currency can't be turned off through a configuration key or parameter. Because the reporting currency is used as a second accounting currency, the way that the reporting currency is calculated in the posting logic has changed.

In addition, several modules have been enhanced to track, report, and use the reporting currency in various processes. The modules that are affected include:

- General ledger 
- Financial reporting 
- Accounts payable
- Accounts receivable 
- Cash and bank management 
- Fixed assets 
- Consolidations

After an upgrade, you must complete specific steps for Cash and bank management and Fixed assets. Therefore, be sure to read and understand the relevant sections of this article.

## Posting process

The posting logic has been changed for all transactions that generate an accounting entry to general ledger. Here is how the reporting currency was previously calculated:

Transaction currency amount \> Accounting currency amount \> Reporting currency amount

For example, a transaction is entered in the Canadian dollar (CAD) currency. The CAD amount is translated to the accounting currency, which is the US dollar (USD). The USD amount is then translated to the reporting currency, which is the euro (EUR). Therefore, the exchange rates must exist between CAD and USD, and between USD and EUR.

Here is the new calculation:

Transaction currency amount \> Accounting currency amount

Transaction currency amount \> Reporting currency amount

Because of this change, exchange rates must now exist between CAD and USD, and between CAD and EUR.

## Reports and inquiries

Various reports and inquiries now show both reporting currency amounts and accounting currency amounts. Not every report and inquiry has been updated. For example, reports that show amounts only in the transaction currency haven't changed.

The changes follow one of two patterns:

- If the report or inquiry had enough space to show amounts in both the accounting currency and the reporting currency, the reporting currency amounts were added.
- If the report or inquiry didn't have enough space to show amounts in both currencies, an option was added so that users can select which currency is shown.

For various reports and inquiries, logic was also added to suppress the reporting currency amounts if the reporting currency is the same as the accounting currency, or if the reporting currency wasn't defined on the ledger for the legal entity.

## Financial journals

The financial journals, such as the general journal and vendor invoice journal, have been updated so that they include additional information about the reporting currency. Totals for the voucher and journal are now shown in the reporting currency. Additionally, information about the reporting currency's exchange rate now appears on the **General** tab of the journal lines. Therefore, you can override the reporting currency's exchange rate when you enter transactions.

## Vendor invoices, sales orders, and sales agreements
Vendor invoices, sales orders, and sales agreements have been updated to include a fixed exchange rate for the reporting currency. A fixed exchange rate can be defined for both the accounting currency and reporting currency when the transaction currency is different. When the accounting currency and reporting currency are the same, the fixed exchange rate will be kept in sync by using the accounting currency’s fixed rate as the reporting currency’s fixed rate. The reporting currency fixed exchange rate cannot be changed for this configuration. When the accounting currency and reporting currency differ, a fixed exchange rate can be defined for both the accounting currency and reporting currency during transaction entry. If the reporting currency has not been defined on the ledger, the **Reporting currency fixed exchange rate** field is not enabled, and no reporting currency amount is calculated.

## Module changes

The following modules use the reporting currency as a second accounting currency:

- [General ledger](#general-ledger)
- [Financial reporting](#financial-reporting)
- [Accounts payable](#accounts-payable-and-accounts-receivable)
- [Accounts receivable](#accounts-payable-and-accounts-receivable)
- [Cash and bank management](#cash-and-bank-management)
- [Fixed assets](#fixed-assets)
- [Consolidations](#consolidations)

### General ledger

If a reporting currency was defined on the ledger, the general ledger already tracked reporting currency amounts on every accounting entry. However, those amounts are now translated from the transaction currency amounts.

The following additional changes were made in the **General ledger** module:

- A separate exchange rate type for the reporting currency can be defined on the ledger. If an organization doesn't want to use a different exchange rate type, you can leave the field for the exchange rate type for the reporting currency blank. Alternatively, you can select the same exchange rate type that is used for the accounting currency. If you leave the field blank, the system uses the exchange rate type for the accounting currency.
- A new journal, the Reporting currency adjustment journal, enables adjustments to be posted to ledger accounts in the reporting currency only. This journal enables posting only to ledger accounts. It doesn't support intercompany, and the currency must be the reporting currency of the legal entity where the journal is posted. When the journal is posted, the transaction currency and accounting currency amounts are 0 (zero), and the reporting currency amount is posted with the amount that is entered on the transaction. Because the way that the reporting currency is used in the **Accounts payable**, **Accounts receivable**, and **Fixed assets** modules has changed, this journal can be used for adjustments after an upgrade. For examples that show how this journal can be used, see the sections for those modules.
- The process for period allocation has been updated so that it allocates amounts in the transaction, accounting, and reporting currencies. Previously, amounts were allocated in the transaction and accounting currencies, and then the accounting currency amount was translated to the reporting currency. That behavior could cause a balance to remain on the ledger account in the reporting currency. Now, when amounts are calculated and used in the accounting entry, no translation occurs.
- The process for foreign currency revaluation already revalued amounts in the reporting currency. However, the reporting currency amount is now calculated through the transaction currency amount, as described in the [Posting process](#posting-process) section earlier in this article.
- Many reports and inquiries in General ledger already had the reporting currency, but a few didn't. One example is the **Trial balance** list page. This list page now includes columns for both the accounting currency and the reporting currency. Note that the columns for the reporting currency are hidden if the accounting currency and the reporting currency are the same, or if no reporting currency was defined on the ledger.

### Financial reporting

An enhancement to the **Financial reporting** module lets you include reporting currency amounts on a financial statement in two ways. On the column definition, you can report directly on the reporting currency amounts that are posted to the ledger (new functionality). Alternatively, you can continue to translate amounts from the accounting currency to the reporting currency (existing functionality).

This change is available through the **Currency display** setting in the column definition. If you select **Reporting currency from ledger**, amounts in the column aren't translated. Instead, they are reported directly from the general ledger. If you want the column to show translated amounts, select the **Translate to XXXX** option, where *XXXX* is the reporting currency that the column should show. In this case, accounting currency amounts will be translated to the selected currency by using the existing translation functionality.

### Accounts payable and Accounts receivable

The **Accounts payable** and **Accounts receivable** modules already tracked reporting currency amounts. However, the amounts weren't shown or used for various processes. The following changes were made:

- Reporting currency amounts are now shown on transactions for both customers and vendors. Reporting currency amounts are also shown for the open balance of each transaction.
- The aging process has been updated so that an organization can view the aging buckets in either the accounting currency or the reporting currency.
- Various inquiries and reports were updated so that they show reporting currency amounts. Examples include the **Customer to ledger reconciliation** and **Vendor to ledger reconciliation** reports.
- The process for foreign currency revaluation already revalued amounts in the reporting currency. However, the reporting currency amount is now calculated through the transaction currency amount, as described in the [Posting process](#posting-process) section.
- **Upgrade consideration:** Before an upgrade, the reporting currency amounts for documents (invoices, payments, and so on) are calculated through the accounting currency. For example, an invoice is posted before an organization upgrades, and the invoice isn't paid. During the upgrade, the invoice's accounting entry isn't changed. However, after the upgrade, the changes for dual currency are in effect. Therefore, when a payment is made for the invoice, the payment's reporting currency amount is now calculated through the transaction currency amount. When the payment and invoice are settled, a slight difference might be calculated in the realized gain/loss amount, because reporting currency amounts are now calculated differently. If the difference that is calculated is considered significant, the new Reporting currency adjustment journal can be used to adjust the balance of the realized gain/loss and Accounts payable/Accounts receivable ledger accounts in the reporting currency only.

### Cash and bank management

Previously, the **Cash and bank management** module didn't track any reporting currency amounts for transactions that were posted against each bank account. After an upgrade, reporting currency amounts are automatically tracked for any new transactions that are posted. However, reporting currency amounts must be added to previously posted transactions in the subledger.

- **Upgrade consideration:** Because bank account transactions didn't previously track reporting currency amounts in the subledger, a wizard has been added so that you can add reporting currency amounts to bank account transactions. This wizard does **not** post to the general ledger again. Instead, it takes the reporting currency amounts from the general ledger and updates them in the subledger tables.

    - To start the wizard, select **Cash and bank management** \> **Setup** \> **Add reporting currency amounts to bank account transactions**.
    - The wizard shows transactions for all bank accounts in the current company that have a reporting currency amount of 0 (zero). Only transactions that were posted before the upgrade are included.
    - For each bank account transaction, the wizard finds the corresponding accounting entries in the general ledger and enters a default reporting currency amount. Although the amounts can be edited, we recommend that you **not** edit them. Otherwise, you might not be able to reconcile the bank account balances to the general ledger. The only time that you should edit an amount should is if the reporting currency amount can't be found in the general ledger. In that case, the wizard will show an amount of 0 (zero) for the reporting currency.
    - If you select **Cancel** in the wizard, the bank account transactions and any changes to the reporting currency amounts are saved until the next time that you run the wizard. However, the reporting currency amounts aren't updated on the bank account transactions. That update occurs only when you select **Finish** in the wizard. You can run the wizard multiple times. Therefore, you can fix any incorrect reporting currency amounts if you make a mistake.

- No processes in Cash and bank management were changed, but various reports and inquiries were updated so that they show reporting currency amounts. The cash flow forecasting reports are an exception. They weren't updated to include the reporting currency amounts.

### Fixed assets

Previously, the **Fixed assets** module didn't track any reporting currency amounts for transactions that were posted against each fixed asset book. After an upgrade, reporting currency amounts are automatically tracked for any new transactions that are posted. However, reporting currency amounts must be added to previously posted transactions in the subledger.

In addition, major changes have been made to the depreciation process. These changes require user action after an upgrade. It's important that you read and understand the following changes, even if you aren't yet using Fixed assets.

- The way that the depreciation process determines the reporting currency amount has changed. The following scenario compares how depreciation previously determined the reporting currency amount and how it determines the reporting currency amount now.



    **Depreciation scenario**

    An asset is acquired and posted with the following amounts. Note that the reporting currency amount is posted in the general ledger, but it isn't stored in the Fixed asset subledger tables.

    | Transaction type | Transaction amount | Exchange rate | Accounting currency amount | Exchange rate | Reporting currency amount |
    |------------------|--------------------|---------------|----------------------------|---------------|---------------------------|
    | Acquisition      | 1,000,000 DKK      | 2.0           | 500,000 USD                | 2.5           | 200,000 EUR               |

    **Previous depreciation for the reporting currency**

    At the end of the year, the depreciation proposal is run and calculates the following amounts.

    | Transaction type | Transaction amount | Exchange rate | Accounting currency amount | Exchange rate | Reporting currency amount |
    |------------------|--------------------|---------------|----------------------------|---------------|---------------------------|
    | Depreciation     | 50,000 USD         | 1.0           | 50,000 USD                 | 2.6           | 19,230.77 EUR             |

    When the depreciation proposal is run, it calculates the accounting currency amount by using the depreciation method. It then translates that amount to the reporting currency by using the current exchange rate between USD and EUR. This translation causes issues, because the asset can't be fully depreciated in the reporting currency when the spot rate is used.

    **New depreciation for the reporting currency**

    The depreciation process has been changed so that the reporting currency amount is also calculated by using the depreciation method. Here are the results when depreciation is run on the asset.

    | Transaction type | Transaction amount | Exchange rate | Accounting currency amount | Exchange rate                                                       | Reporting currency amount |
    |------------------|--------------------|---------------|----------------------------|---------------------------------------------------------------------|---------------------------|
    | Depreciation     | 50,000 USD         | 1.0           | 50,000 USD                 | 2.5 **NOTE:**  Although this exchange rate is shown, it isn't used to translate to the reporting currency. | 20,000 EUR                |

    When the depreciation proposal is run, it calculates both the accounting currency amount and the reporting currency amount by using the depreciation method. The amounts are then used in the accounting entry in the general ledger. No translation is done to determine the reporting currency amount.

- **Upgrade consideration:** Because fixed asset book transactions didn't previously track the reporting currency, a wizard has been added so that you can add reporting currency amounts to fixed asset book transactions. This wizard does **not** post to the general ledger again. Because the way that the depreciation proposal calculates reporting currency amounts has changed, the wizard **must** be run and completed for every company before an organization can enter any depreciation transactions.

    - To start the wizard, select **Fixed assets** \> **Setup** \> **Add reporting currency amounts to fixed asset books**.
    - The wizard shows transactions for all fixed asset books in the current company that have a reporting currency amount of 0 (zero). Only transactions that were posted before the upgrade are included.
    - The wizard does **not** pull the reporting currency amounts from the general ledger. As was described in the previous scenario, the reporting currency amounts that were originally posted to the general ledger incorrectly used the spot rate. Those amounts should not appear in the fixed asset subledger, because the next depreciation calculation will use the incorrect amounts. Instead, the wizard finds the exchange rate on the date of the first acquisition. It then uses that exchange rate to recommend the reporting currency amount that should be posted in the subledger. For example, here is what the wizard might show for the previous scenario.

        | Fixed asset | Book      | Transaction type | Transaction date | Currency | Amount in transaction currency | Amount  | Exch rate | Reporting currency amount |
        |-------------|-----------|------------------|------------------|----------|--------------------------------|---------|-----------|---------------------------|
        | BUIL-00001  | 200\_SLLT | Acquisition      | 6/3/2016         | DKK      | 1,000,000                      | 500,000 | 2.5       | 250,000                   |
        | BUIL-00001  | 200\_SLLT | Depreciation     | 6/3/2016         | USD      | 50,000                         | 50,000  | 2.5       |  25,000                   |
        | BUIL-00001  | 200\_SLLT | Depreciation     | 6/3/2016         | USD      | 50,000                         | 50,000  | 2.5       |  25,000                   |
        | BUIL-00001  | 200\_SLLT | Depreciation     | 6/3/2016         | USD      | 50,000                         | 50,000  | 2.5       |  25,000                   |

    - Many customers tracked their asset transaction details in workbooks. These details include the exchange rates and amounts. If you have this data in a workbook, you can create a custom exchange rate type and update it with the exchange rates from the workbook. This exchange rate type will then be used to enter a default exchange rate on the acquisition date and calculate the reporting currency amount. If an exchange rate type isn't selected, the wizard uses the exchange rate type that was defined on the ledger.
    - The exchange rate and reporting currency amounts can be changed. If the exchange rate is changed, the reporting currency amount is recalculated by using the new rate.
    - If you select **Cancel** in the wizard, the fixed asset book transactions and any changes to the exchange rate or reporting currency amounts are saved until the next time that you run the wizard. However, the reporting currency amounts aren't updated on the fixed asset book transactions. That update occurs only when you select **Finish** in the wizard. You can run the wizard multiple times. Therefore, you can fix any incorrect reporting currency amounts if you make a mistake.
    - When the reporting currency amounts are completely updated in the subledger, you **must** set the **Have you updated all the reporting currency amounts on the fixed asset book transactions?** option to **Yes** and then select **Finish**. Depreciation calculations can't be completed until you set the **Have you updated all the reporting currency amounts on the fixed asset book transactions?** option to **Yes**. After that option is set to **Yes**, the wizard is no longer available.
    - After the fixed asset transactions in the subledger are updated with reporting currency amounts, those amounts won't match the amounts that were originally posted to the general ledger. However, the Reporting currency adjustment journal can be used to update the balances of the depreciation ledger accounts in the general ledger, so that they match the amounts that were originally posted.
    - A new **Asset transaction reporting currency amounts** entity that has been added in the **Data management** workspace lets you export the data from the wizard. You can then use the data to determine the balance in the fixed asset subledger for the depreciation transactions. That balance can then be used to determine the amount of the reporting currency adjustment in the general ledger.

- **Upgrade consideration:** New setup fields have been added to fixed assets and are used in the depreciation calculation. You might have to update these fields before the next depreciation calculation.

    - On the fixed asset book (**Fixed assets** \> **Books**), the **General** FastTab has a new **Acquisition price in reporting currency** field.
    - On the fixed asset book (**Fixed assets** \> **Books**), the **Depreciation** FastTab has a new **Expected scrap value in reporting currency** field.
    - In the Fixed asset parameters (**Fixed assets** \> **Setup** \> **Fixed asset parameters**), the **General** FastTab has a new **Minimum depreciation amount in reporting currency** field.
    - On books (**Fixed assets** \> **Setup** \> **Books**), the **General** FastTab has two new fields: **Round off depreciation in reporting currency** and **Leave net book value at reporting currency**.

- Because the depreciation proposal now calculates amounts in both the accounting currency and the reporting currency, the Fixed asset journal has been updated so that it shows depreciation amounts in the reporting currency. For depreciation transactions, the transaction currency is always the accounting currency. Therefore, those amounts will continue to appear in the **Debit** and **Credit** columns. Two new columns, **Debit in reporting currency** and **Credit in reporting currency**, have been added to the grid.

    - The new fields are available only when the transaction type is one of the four depreciation types: **Deprecation**, **Depreciation adjustment**, **Extraordinary depreciation**, or **Special depreciation allowance**.
    - If a deprecation transaction type is entered in the Fixed asset journal, the reporting currency amounts will appear in the new columns. Those amounts can be changed.
    - If the accounting currency and the reporting currencies on the ledger are the same, the amounts will be kept in sync. If you change the **Credit** amount, the **Credit in reporting currency** amount will automatically be changed so that it matches it.
    - If any other transaction type is entered in the Fixed asset journal, the **Debit in reporting currency** and **Credit in reporting currency** amounts are never shown, either before or after posting. The accounting currency and reporting currency amounts are still available on the voucher that posts to the general ledger.
    
### Consolidations
    
Functionality that was introduced in Dynamics 365 Finance version 10.0.5 (October 2019) enables functionality through feature management for enhanced flexibility for consolidation and dual currency. To enable this functionality, go to the **Feature management** workspace and select **Enable dual currency functionality in General ledger consolidation**.

In General ledger consolidation, a new option has been added to consolidate either the accounting or reporting currency amounts from the source companies. If the accounting or reporting currency is the same as the accounting or reporting currency in the consolidation company, the amounts will be copied directly rather than translated.

-  You can now choose whether to use the accounting currency or the reporting currency from the source company as the transaction currency in the consolidation company.

- The accounting or reporting currency amounts from the source company will be copied directly to the accounting or reporting currency amounts in the consolidation company, if either of the currencies are the same. The accounting and reporting currency amounts in the consolidation company are calculated using the exchange rate if neither of the currencies is the same.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]

