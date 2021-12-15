---
# required metadata

title: Recommended practices for posting profiles
description: This topic describes recommended practices for configuring posting profiles.  
author: rachel-profitt
ms.date: 12/03/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerSystemSetup, CustPosting, VendPosting, InventPosting, AssetPosting, ProjPosting, AssetLeasePostingAccounts, ProjCategory, ITMCostTypeTable, ProdGroup, WrkCtrTable, WrkCtrResourceGroup, MainAccount, SysDatabaseLogSetup, CustGroup, VendGroup, InventItemGroup
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: c64eed1d-df17-448e-8bb6-d94d63b14607
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2022-01-03
ms.dyn365.ops.version: AX 7.0.0

---
# Recommended practices for posting profiles

There are a variety of recommended practices to follow when you configure posting profiles throughout Dynamics 365. This page includes details about each scenario and recommended practice.

## Do not allow manual entry

Any main account that is used for a posting profile should have the **Do not allow manual entry** flag set on the **Main accounts** page. This setting on this check box ensures that a user can't manually post a journal entry into the main account. This helps to ensure that the subledger remains in balance with the general ledger and helps make the reconciliation process easier. If adjustments are required to an account that is controlled by the system and posted to automatically, you can do one of two things:

1.  Create a secondary main account where the adjustments can be posted. Then use a Total account or special row on your financial reports to group and sum the accounts together.

2.  Reverse the original transactions in the appropriate subledger, make any necessary corrections and then repost the transaction through the same subledger.

## Making changes to posting profiles after transactions exist

If you make a change to a posting profile after transactions exist, this can cause the reconciliation to fail and your subledger and ledger to be out of balance. In general, it is not recommended to make changes to the posting profile after transactions exist.

If a change is necessary, use the following guidelines to help ensure the integrity of the system:

-   Make the change during a period close.

-   Make the change when no other transactions are happening in the system.

-   Validate and reconcile the ledger to subledger before and after the change is made.

-   Making a change to the posting profile does not update any posted transactions. Consider carefully if any adjusting entries are required for your change.

-   If you are making changes to inventory posting profiles, consider how the change will affect your on-hand inventory and ledger balances. Some changes may require that you bring the inventory to zero, close the inventory, and then bring the inventory back in after the adjustments are made.

-   Always test your changes in a non-production environment prior to making the change in production.

## Use database logging to audit changes to posting profiles

Consider setting up database logging for each posting profile and parameters tables that control posting. In the event a parameter or profile is changed, you will have a full audit record of what value was changed, who changed the value, when the value was changed, and what the previous value was. This information can be critical in your reconciliation process and your auditor may need the supporting documentation.

For more information, refer to [Database logging](../../../fin-ops-core/dev-itpro/sysadmin/configure-manage-database-log).

Use the following table as a reference for common table names related to posting profiles and related posting parameters:

| Page name | Menu path | Table name |
|-------------------------|-------------------------|-------------------------|
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
| Asset leasing parameters | Asset leasing &gt; Setup &gt; Asset leasing parameters | AssetLeasePostingAccounts</br>AssetLeaseJournalParameters</br>AssetLeaseExecutoryCostPostingAccounts |
| Bank accounts | Cash and bank management &gt; Bank accounts &gt; Bank accounts | BankAccountsTable |
| Bank transaction types | Cash and bank management &gt; Setup &gt; Bank transaction types | BankTransType |
| Elimination rules | Consolidations &gt; Setup &gt; Elimination rule | LedgerEliminationRule</br>LedgerEliminationRuleLines |
| Expense categories | Expense management &gt; Setup &gt; General &gt; Expense categories | ProjCategories |
| Fixed asset parameters | Fixed assets &gt; Setup &gt; Fixed asset parameters | AssetParameters |
| Fixed asset posting profiles | Fixed assets &gt; Setup &gt; Fixed asset posting profiles | AssetLedgerAccounts</br>AssetDisposalParameters |
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


## Change groups after transactions exist

Use caution when changing groups on master data. If you are using groups to define your posting profiles, making a change to a group on a master record can have a negative impact on the ability to reconcile the ledger to the sub-ledger. For example, you can configure the **Inventory posting profile** for sales order revenue to use a different **Revenue account** for each **Item group**. If you change the item group that is assigned to an item after transactions exist, the revenue on new transactions will post to the updated account, but any revenue posted prior to the update will remain in the original account.

## Testing posting profiles

Prior to your go-live and after making any changes or additions to your posting profiles or related parameters, you should test each scenario. At a minimum you should test each posting type to validate the posting works correctly. However, the recommended approach is to test each posting profile transaction and combination.

For example, if you have two **Customer posting profiles** and each posting profile has three records specific to **Customer groups**, you should test each transaction type.

Posting Profiles:

-   GEN – General with one group for Employees, Customers, and Intercompany, each pointing to a different Accounts receivable Trade account.

-   PRE – Prepayment posting profile with one record for all prepayments pointing to the Customer prepaids accounts.

Testing Scenarios:

-   Free text invoice for a customer in the Employee group with the General posting profile

-   Free text invoice for a customer in the Employee group with the Prepayment posting profile

-   Sales order invoice for a customer in the Employee group with the General posting profile

-   Sales order invoice for a customer in the Employee group with the Prepayment posting profile

-   Customer payment journal for a customer in the Employee group with the General posting profile

-   Customer payment journal for a customer in the Employee group with the Prepayment posting profile

Using the example above, repeat one testing scenario for each customer group, and repeat each group of testing scenarios for each additional transaction type (for example, Project invoices, Service management, and so on).

## Reconciling the ledger to the sub ledger

Each period, the ledger should be reconciled to sub ledger. Many modules contain reports out of the box that can be used to help reconcile the ledger to the sub ledger. Depending on your local requirements, you may need to develop custom reports or extend the existing reports to meet your reporting requirements.

It is recommended that you perform a mock period close and reconcile each of your sub ledgers to the ledger prior to your go live. Additionally, it is recommended to perform a mock cutover of all open balances and open transactions prior to your initial go live. As a part of this process a complete reconciliation process should be executed to ensure that the migration of balances and open transactions balance with the legacy system(s) and to ensure that all subledgers balance with the ledger prior to creating new transactions.
