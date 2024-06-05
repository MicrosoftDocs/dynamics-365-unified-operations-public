---
title: Recommended practices for posting profiles
description: Learn about recommended practices for configuring posting profiles, including outlines on setting manual entry flags and changing posting profiles.
author: rachel-profitt
ms.author: kweekley
ms.topic: article
ms.date: 12/03/2021
ms.custom: 
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2022-01-03
ms.search.form: LedgerSystemSetup, CustPosting, VendPosting, InventPosting, AssetPosting, ProjPosting, AssetLeasePostingAccounts, ProjCategory, ITMCostTypeTable, ProdGroup, WrkCtrTable, WrkCtrResourceGroup, MainAccount, SysDatabaseLogSetup, CustGroup, VendGroup, InventItemGroup
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: c64eed1d-df17-448e-8bb6-d94d63b14607
---

# Recommended practices for posting profiles

There are several recommended practices that you should follow when you configure posting profiles throughout the system. This article describes different scenarios and the corresponding recommended practices.

## Setting the Do not allow manual entry flag

On the **Main accounts** page, the **Do not allow manual entry** checkbox should be selected for any main account that is used for a posting profile. This setting prevents users from manually posting a journal entry to the main account. Therefore, it helps ensure that the subledger remains in balance with the general ledger and helps make the reconciliation process easier.

If adjustments are required to an account that is controlled by the system and automatically posted, you can use one of these approaches:

- Create a secondary main account where the adjustments can be posted. Then use a Total account or a special row on your financial reports to group and sum the accounts together.
- Reverse the original transactions in the appropriate subledger, make any required corrections, and then repost the transaction through the same subledger.

## Changing posting profiles after transactions exist

If you change a posting profile after transactions exist, the reconciliation can fail, and your subledger and ledger can become out of balance. In general, we recommend that you **not** change the posting profile after transactions exist.

If changes are required, use the following guidelines to help ensure the integrity of the system:

- Make the changes during a period close.
- Make the changes when no other transactions are occurring in the system.
- Validate the ledger and reconcile it to subledger before and after you make the changes.
- Posted transactions aren't updated if you change the posting profile. Carefully consider whether any adjusting entries are required for your change.
- If you're changing inventory posting profiles, consider how the changes will affect your on-hand inventory and ledger balances. Some changes might require that you bring the inventory to 0 (zero), close the inventory, and then bring the inventory back in after the changes are made.
- Always test your changes in a non-production environment before you make them in production.

## Using database logging to audit changes to posting profiles

Consider setting up database logging for each posting profile and parameters tables that control posting. Then, if a parameter or profile is changed, you will have a full audit record of what value was changed, who changed it, when it was changed, and what the previous value was. This information can be critical during your reconciliation process, and your auditor might require the supporting documentation.

For more information, see [Configure database logging](../../fin-ops-core/dev-itpro/sysadmin/configure-manage-database-log.md).

Use the following table as a reference for common table names that are related to posting profiles and related posting parameters.

| Page name | Navigation path | Table name |
|-----------|-----------------|------------|
| Accounts payable parameters | Accounts payable &gt; Setup &gt; Accounts payable parameters | VendParm |
| Vendor posting profile | Accounts payable &gt; Setup &gt; Vendor posting profile | VendPosting |
| Charges code | Accounts payable &gt; Charges setup &gt; Charges code or Accounts receivable &gt; Charges setup &gt; Charges code | MarkupTable |
| Methods of payment | Accounts payable &gt; Payment setup &gt; Methods of payment | VendPaymMode |
| Cash discounts | Accounts payable &gt; Payment setup &gt; Cash discounts or Accounts receivable &gt; Payment setup &gt; Cash discounts | CashDisc |
| Payment fee (Vendor) | Accounts payable &gt; Payment setup &gt; Payment Fee | VendPaymFee |
| Accounts receivable parameters | Accounts receivable &gt; Setup &gt; Accounts receivable parameters | CustParm |
| Customer posting profiles | Accounts receivable &gt; Setup &gt; Customer posting profile | CustPosting |
| Methods of payment | Accounts receivable &gt; Payments setup &gt; Methods of payment | CustPaymMode |
| Payment fee (Customer) | Accounts receivable &gt; Payments setup &gt; Methods of payments | CustPaymFee |
| Asset leasing parameters | Asset leasing &gt; Setup &gt; Asset leasing parameters | AssetLeasePostingAccounts<br>AssetLeaseJournalParameters<br>AssetLeaseExecutoryCostPostingAccounts |
| Bank accounts | Cash and bank management &gt; Bank accounts &gt; Bank accounts | BankAccountsTable |
| Bank transaction types | Cash and bank management &gt; Setup &gt; Bank transaction types | BankTransType |
| Elimination rules | Consolidations &gt; Setup &gt; Elimination rule | LedgerEliminationRule<br>LedgerEliminationRuleLines |
| Expense categories | Expense management &gt; Setup &gt; General &gt; Expense categories | ProjCategories |
| Fixed asset parameters | Fixed assets &gt; Setup &gt; Fixed asset parameters | AssetParameters |
| Fixed asset posting profiles | Fixed assets &gt; Setup &gt; Fixed asset posting profiles | AssetLedgerAccounts<br>AssetDisposalParameters |
| Currency revaluation accounts | General ledger &gt; Currencies &gt; Currency revaluation accounts | CurrencyLedgerGainLossAccount |
| Accounts for automatic transactions | General ledger &gt; Posting setup &gt; Accounts for automatic transactions | LedgerSystemAccounts |
| Intercompany accounting | General ledger &gt; Posting setup &gt; Intercompany accounts | LedgerIntercompany |
| Transaction posting definitions | General ledger &gt; Posting setup &gt; Transaction posting definitions | JournalizingDefinitionTrans |
| Posting definitions | General ledger &gt; Posting setup &gt; Posting definitions | JournalizingDefintion |
| Posting (Inventory) | Inventory management &gt; Setup &gt; Posting &gt; Posting | InventPosting |
| Cost type codes | Landed cost &gt; Costing setup &gt; Cost type codes | ITMCostTypeTable |
| Resources | Production control &gt; Setup &gt; Resources &gt; Resources | WrkCtrTable |
| Resource groups | Production control &gt; Setup &gt; Resources &gt; Resource groups | WrkCtrResourceGroup |
| Production groups | Production control &gt; Setup &gt; Production &gt; Production group | ProdGroup |
| Cost categories | Production control &gt; Setup &gt; Routes &gt; Cost categories | ProjCategory |
| Project groups | Project management and accounting &gt; Setup &gt; Posting &gt; Project groups | ProjGroup |
| Ledger posting setup (Projects) | Project management and accounting &gt; Setup &gt; Posting &gt; Ledger posting setup | ProjPosting |
| Default offset accounts for expenses | Project management and accounting &gt; Setup &gt; Posting &gt; Default offset accounts for expenses | ProjDefaultOffsetSetup |
| Rebate management posting profiles | Rebate management &gt; Rebate management posting setup &gt; Rebate management posting profiles | TAMRebatePosting |
| Ledger posting group (Tax) | Tax &gt; Setup &gt; Sales tax &gt; Ledger posting group | TaxAccountGroup |

## Changing groups after transactions exist

Use caution when you change groups in master data. If you're using groups to define your posting profiles, any change to a group on a master record can have a negative impact on the ability to reconcile the ledger to the subledger. For example, you can configure the inventory posting profile for sales order revenue so that a different revenue account is used for each item group. If you change the item group that is assigned to an item after transactions exist, the revenue on new transactions will be posted to the updated account. However, any revenue that was posted before the change will remain in the original account.

## Testing posting profiles

Before your go-live, and after you make any changes or additions to your posting profiles or related parameters, you should test each scenario. At a minimum, you should test each posting type to validate that posting works correctly. However, the recommended approach is to test each posting profile transaction and combination.

For example, you have two customer posting profiles, each of which has three records that are specific to customer groups. In this case, you should test each transaction type.

**Posting profiles:**

- **GEN** – The general posting profile that has one group for employees, one for customers, and one for intercompany. Each group points to a different Accounts receivable Trade account.
- **PRE** – The prepayment posting profile that has one record for all prepayments that points to the Customer prepaids accounts.

### Testing scenarios

- Free text invoice for a customer in the **Employee** group that uses the **GEN** posting profile
- Free text invoice for a customer in the **Employee** group that uses the **PRE** posting profile
- Sales order invoice for a customer in the **Employee** group that uses the **GEN** posting profile
- Sales order invoice for a customer in the **Employee** group that uses the **PRE** posting profile
- Customer payment journal for a customer in the **Employee** group that uses the **GEN** posting profile
- Customer payment journal for a customer in the **Employee** group that uses the **PRE** posting profile

For the preceding example, repeat one testing scenario for each customer group, and repeat each group of testing scenarios for each additional transaction type (for example, project invoices and service management).

## Reconciling the ledger to the subledger

The ledger should be reconciled to the subledger every period. Many modules contain out-of-box reports that can be used to help do this reconciliation. However, depending on your local requirements, you might have to develop custom reports or extend the existing reports to meet your reporting requirements.

We recommend that you do a mock period close and reconcile each of your subledgers to the ledger before your go-live. We also recommend that you do a mock cutover of all open balances and open transactions before your initial go-live. As part of this process, you should run a complete reconciliation to ensure that the migration of balances and open transactions balance with the legacy systems, and that all subledgers balance with the ledger before new transactions are created.
