---
title: Reduce long-running transactions in TempDB preprocessing SSRS reports
description: Opt out your TempDB preprocessing report of the framework's transaction scope to reduce long-running transactions and tempDB log pressure.
author: ishaankochar
ms.author: ishaankochar
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 10/01/2026
ms.reviewer: twheeloc
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2026-06-16
ms.dyn365.ops.version: Platform update 55
---

# Reduce long-running transactions in TempDB preprocessing reports

[!INCLUDE [banner](../includes/banner.md)]

This article explains how to reduce long-running transactions and TempDB transaction log pressure caused by preprocessing SSRS reports that use the TempDB pattern, by opting out of the reporting framework's transaction scope.

This article is for anyone who maintains custom SSRS reports and whose Report Data Provider (RDP) class extends `SrsReportDataProviderPreProcessTempDB`.

## Applies to

Platform Update 55 and later. Every currently supported environment includes the fix.

## Background

Reports that use the TempDB preprocessing pattern stage their results in temporary database tables during a preprocessing step. By default, the reporting framework wraps the entire preprocessing step in a single transaction scope and commits only after preprocessing finishes.

On cloud deployments backed by Azure SQL, the TempDB transaction log is a shared resource. While a long-lived transaction stays open, log space can't be released. For reports that process large data sets, this behavior can hold a transaction open for the full duration of preprocessing, delay log truncation, and in extreme cases, fill the TempDB log and impact other workloads on the same database.

## What this capability changes

The framework exposes an opt-in switch (`parmSkipReportTransaction`) that lets a report data provider skip the framework's transaction scope. When a report opts in:

- The framework no longer opens transactions around your `processReport` method.
- Each statement you execute commits independently.
- Transaction log space is released as work progresses, instead of being held until the end of preprocessing.

This change isn't a runtime optimization for the report itself. The report does the same amount of work in roughly the same amount of time. What changes is the transaction boundary, which improves the health of the shared environment.

## When to use it

For any report that extends `SrsReportDataProviderPreProcessTempDB` and processes meaningful data volumes, **opt in**. The legacy behavior (a framework-managed transaction wrapping the entire preprocessing step) exists for historical reasons, not because it's the better design. Holding a single transaction open during preprocessing increases tempDB log pressure and can contend with other operations running in your environment at the same time: batch jobs, other reports, and interactive users.

The only valid reason to keep the legacy behavior is when your preprocessing step has a genuine business requirement for atomic rollback of the entire step, and the work can't be restructured into explicit transaction boundaries. This situation is uncommon. "It's easier to leave it as-is" isn't a valid reason. The transaction management you take on is straightforward and is fully covered in the next section.

## How to opt in

Override `parmSkipReportTransaction` in your report data provider so it returns `true`. The recommended pattern mirrors the platform team's reference implementation:

```xpp
public class MyLargeReportDP extends SrsReportDataProviderPreProcessTempDB
{
    public boolean parmSkipReportTransaction(boolean _skipReportTransaction = skipReportTransaction)
    {
        skipReportTransaction = true;
        return skipReportTransaction;
    }

    public void processReport()
    {
        // Your preprocessing logic.
        // See "Manage your own transactions" below.
    }
}
```

The override is read at run time, so the change is scoped to the report data providers you explicitly opt in to. All other reports continue to behave as before.

## Important: manage your own transactions

When you opt in, the framework removes **two** transactions that previously surrounded your `processReport` call:

| Transaction | What it covered | What replaces it when you opt in |
| --- | --- | --- |
| Ambient transaction (`ttsbegin` / `ttscommit`) | Regular table operations in `processReport` | You wrap them yourself with `ttsbegin;` / `ttscommit;` where needed. |
| User connection transaction (`userConnection.ttsBegin()` / `ttsCommit()`) | Operations against tables attached to the report's user connection (the temp tables) | You wrap them yourself with `parmUserConnection().ttsBegin()` / `ttsCommit()`. |

The most common mistake is updating or deleting a user-connection-bound record without an open transaction on that connection. You see the following error message:

> Cannot select a record for update when the transaction is not started on the user connection attached. You need to begin transaction on the user connection first.

A plain `ttsbegin;` doesn't resolve this issue. The data tables are on the user connection, not the ambient connection. Begin the transaction on the user connection explicitly:

```xpp
public void processReport()
{
    UserConnection userConnection = this.parmUserConnection();

    // Wrap operations that update or delete user-connection-bound records.
    userConnection.ttsBegin();
    // selectForUpdate / update() / delete() against temp tables
    userConnection.ttsCommit();

    // Wrap operations against regular (non-temp) tables if they need atomicity.
    ttsbegin;
    // updates against regular tables
    ttscommit;
}
```

Guidelines:

- Prefer set-based operations (`insert_recordset`, `update_recordset`, `delete_from`). They minimize the time any transaction stays open.
- Watch for silent row-by-row downgrades. A set-based statement that is internally downgraded to row-by-row execution (for example, because a data event handler is registered on the table) reintroduces the same long-running pattern you were trying to avoid. Where possible, restructure the code or remove the cause of the downgrade.
- Keep each explicit transaction as small as possible. Wrapping the whole `processReport` body defeats the purpose of opting in.

## How to opt out

Opt-out is the default. To revert a report you previously opted in, change the override to return `false` or remove the override entirely, and redeploy.

## Things to keep in mind

- **No automatic rollback.** A failure partway through preprocessing no longer rolls back the whole step. If a section needs all-or-nothing behavior, define an explicit transaction boundary around it (on the right connection).
- **Review customizations.** Code paths that update or delete records during preprocessing are the most common source of the user-connection error. Audit them before enabling the switch.
- **Validate report output.** Confirm the report produces the same output as before, particularly in failure and cancellation scenarios.

## Recommended rollout

Roll out the change gradually so you can isolate and revert any individual report quickly.

1. **Development / test.** Opt in one report at a time. Exercise the update and delete paths and any failure paths. Confirm the report produces correct output.
1. **Sandbox (UAT) with production-like data.** Validate correctness at realistic scale and confirm that the long-running transaction is gone.
1. **Production.** Enable for a small set of high-impact reports first, then expand.

## Common issues

| Symptom | Likely cause | Action |
| --- | --- | --- |
| "Can't select a record for update when the transaction isn't started on the user connection attached." | An update or delete on a user-connection-bound table is no longer inside a transaction. | Wrap the affected statements in `parmUserConnection().ttsBegin()` / `ttsCommit()`. A plain `ttsbegin` doesn't resolve this issue. |
| Partial or inconsistent data after a failure | No explicit transaction boundary around logic that needs atomicity. | Add an explicit transaction block around the section that must be all-or-nothing, on the correct connection (ambient or user connection). |
| Report compiles but `parmSkipReportTransaction` is reported as unknown. | Environment is on a platform build older than PU55. | Update the environment to a current platform release. |

## Standard report controls in Dynamics 365 Finance version 10.0.49

The following report inventory lists standard production reports in Dynamics 365 Finance version 10.0.49 whose report data providers implement transaction-scope control behavior. The list excludes test objects, reports without an implementation, and changes that aren't merged into Dynamics 365 Finance version 10.0.49.

> [!IMPORTANT]
> If a customized or extended report fails after its transaction-scope feature is enabled, temporarily disabling the feature can restore the previous behavior while you investigate the customization. Feature disablement is a short-term mitigation, not a permanent solution. Update the extension to manage transactions on the correct connection, validate the correction in a sandbox environment, and then re-enable the feature. For implementation guidance, see [Important: Manage your own transactions](#important-manage-your-own-transactions).

You can't change flight-controlled behavior through Feature management. Contact Microsoft support if a flight-controlled report requires temporary mitigation.

### Control types

- **Feature** - The behavior is controlled through Feature management.
- **Flight** - The behavior is controlled by a service-managed flight.
- **Feature and flight** - Both controls participate in the behavior.
- **Hard-coded** - The behavior is enabled in code and has no feature or flight control.

### Report inventory

The inventory contains 219 report entries that represent 228 SSRS reports:

- 168 feature-controlled entries
- 45 flight-controlled entries
- 1 entry controlled by both a feature and a flight
- 5 hard-coded entries

| Report and caption | Menu item and caption | Control type | Control name |
| --- | --- | --- | --- |
| **Accelerated depreciation declaration report**<br>Report: `AssetAcceleratedDepreciation_JP` | **Accelerated depreciation declaration report**<br>`AssetAcceleratedDepreciation_JP` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Account statement**<br>**Dimension statement**<br>**Dimension statement with simulations**<br>Report: `LedgerTransStatement`<br>Report: `LedgerTransStatementSim_IT` | **Account statement**<br>`LedgerAccountTransStatement`<br><br>**Account statement**<br>`LedgerAccountTransStatementAction`<br><br>**Dimension statement**<br>`LedgerDimensionTransStatement`<br><br>**Dimension statement with simulations**<br>`LedgerDimensionTransStatementSim_IT` | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| **Account statement by currency**<br>Report: `LedgerAccountStatementPerCurrency` | **Account statement by currency**<br>`LedgerAccountStatemenPerCurrency` | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| **Accrued purchases excluding sales tax report**<br>Report: `VendAccruedPurchases` | **Accrued purchases excluding sales tax report**<br>`VendAccruedPurchases` | Flight | `SsrsPreProcessReportSkipDefaultDatabaseTrxScope` |
| **Additional depreciation transaction summary - reserve method**<br>Report: `AssetAdditionalDepreciation_JP` | **Additional depreciation transaction summary - reserve method**<br>`AssetAdditionalDepreciation_JP` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Adjustments**<br>Report: `InventSettlementAdjustment` | **Adjustments**<br>`InventSettlementAdjustment` | Flight | `CostManagementSSRSSkipReportTxnFlight` |
| **Appended table 1 report**<br>**Appended table 2 report**<br>Report: `AssetCorpTaxActAppendedTables_JP` | **Appended table 1 report**<br>`AssetCorpTaxActAppendedTable1_JP`<br><br>**Appended table 2 report**<br>`AssetCorpTaxActAppendedTable2_JP` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Appended table 6 report**<br>Report: `AssetCorpTaxActAppendedTable6_JP` | **Appended table 6 report**<br>`AssetCorpTaxActAppendedTable6_JP` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Appended table 7 report**<br>Report: `AssetCorpTaxActAppendedTable7_JP` | **Appended table 7 report**<br>`AssetCorpTaxActAppendedTable7_JP` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Appended table 8 report**<br>Report: `AssetCorpTaxActAppendedTable8_JP` | **Appended table 8 report**<br>`AssetCorpTaxActAppendedTable8_JP` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Appended table 9 report**<br>Report: `AssetCorpTaxActAppendedTable9_JP` | **Appended table 9 report**<br>`AssetCorpTaxActAppendedTable9_JP` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Asset counting report**<br>Report: `AssetCountingEELV` | **Asset counting report**<br>`AssetCountingEELV` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Asset inventory statement report**<br>Report: `AssetCountingCZLT` | **Asset inventory statement report**<br>`AssetCountingCZLT` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Asset movement**<br>Report: `AssetLeaseAssetMovement` | **Asset movement**<br>`AssetLeaseAssetMovement` | Feature | `AssetLeaseSSRSSkipReportTransactionFeature` |
| **Asset record**<br>**Fixed asset record report**<br>Report: `AssetRecord` | **Asset record**<br>`AssetRecord`<br><br>**Fixed asset record report**<br>`AssetTableReport` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Asset retirement obligation summary report**<br>Report: `AssetRetirementSummary_JP` | **Asset retirement obligation summary report**<br>`AssetRetirementSummary_JP` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| Report: `AssetBalanceReportColumnsHU` | *No direct menu item mapping* | Feature | `AssetSSRSSkipReportTransactionFeature` |
| Report: `AssetBalanceReportColumnsLV` | *No direct menu item mapping* | Feature | `AssetSSRSSkipReportTransactionFeature` |
| Report: `AssetBalances_IN` | *No direct menu item mapping* | Feature | `AssetSSRSSkipReportTransactionFeature` |
| Report: `AssetBasis_IN` | *No direct menu item mapping* | Feature | `AssetSSRSSkipReportTransactionFeature` |
| Report: `AssetDisposal_IN` | *No direct menu item mapping* | Feature | `AssetSSRSSkipReportTransactionFeature` |
| Report: `AssetDisposalLV` | *No direct menu item mapping* | Feature | `AssetSSRSSkipReportTransactionFeature` |
| Report: `AssetLeaseLeaseImportDifference` | *No direct menu item mapping* | Feature | `AssetLeaseSSRSSkipReportTransactionFeature` |
| Report: `AssetLeaseMovementReport` | *No direct menu item mapping* | Feature | `AssetLeaseSSRSSkipReportTransactionFeature` |
| Report: `AssetListing_IN` | *No direct menu item mapping* | Feature | `AssetSSRSSkipReportTransactionFeature` |
| Report: `AssetTransactionListing_IN` | *No direct menu item mapping* | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Average VAT**<br>Report: `TaxAverageVAT` | **Average VAT**<br>`TaxAverageVATReport` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Balance sheet**<br>Report: `LedgerBalanceSheet` | **Balance sheet**<br>`LedgerBalanceSheet` | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| **Bank to ledger reconciliation report**<br>Report: `BankLedgerReconciliation` | **Bank to ledger reconciliation report**<br>`BankLedgerReconciliation` | Flight | `SsrsPreProcessReportSkipDefaultDatabaseTrxScope` |
| **Bill of materials where-used**<br>Report: `BOMPartOfV2` | **Bill of materials where-used**<br>`BOMPartOfReport` | Flight | `ProdTempDbSkipReportTransactionFlight` |
| Report: `BudgetPlanHCMReportV2` | *No direct menu item mapping* | Flight | `BudgetPlanningSSRSSkipReportTxnFlight` |
| **Calculation details for cost and price**<br>**Complete**<br>**Print**<br>Report: `BOMCalcTrans` | **Complete**<br>`BOMCalcTrans`<br><br>**Print**<br>`BOMCalcTransPrint` | Flight | `CostManagementSSRSSkipReportTxnFlight` |
| **Category actual transactions**<br>**Project actual transactions**<br>**Resource/item actual transactions**<br>**Transaction - subscription report**<br>**Transactions**<br>Report: `ProjListTrans` | **Category actual transactions**<br>`ProjListTransCategory`<br><br>**Resource/item actual transactions**<br>`ProjListTransID`<br><br>**Project actual transactions**<br>`ProjListTransProj`<br><br>**Transaction - subscription report**<br>`ProjListTransSubscription`<br><br>**Transactions**<br>`ProjListTransSubscription_Action` | Hard-coded | No configurable control (enabled in code) |
| **Category forecast transactions**<br>**Project forecast transactions**<br>**Resource/item forecast transactions**<br>Report: `ProjListBudget` | **Category forecast transactions**<br>`ProjListBudgetCategory`<br><br>**Resource/item forecast transactions**<br>`ProjListBudgetID`<br><br>**Project forecast transactions**<br>`ProjListBudgetProj` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| **Category profit and loss**<br>Report: `ProjProfitLossCateg` | **Category profit and loss**<br>`ProjListProjProfitLossCategory` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| **Category profit and loss (2 periods)**<br>Report: `ProjProfitLossCateg2Prd` | **Category profit and loss (2 periods)**<br>`ProjListProjProfitLossCategory2ColPeriod` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| **Category profit and loss (actual vs. budget)**<br>Report: `ProjProfitLossCateg2Column` | **Category profit and loss (actual vs. budget)**<br>`ProjListProjProfitLossCategory2Column` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| **Category sales report**<br>Report: `RetailPerformanceByCategory` | **Category sales report**<br>`RetailPerformanceByCategorySSRSReport` | Flight | `RetailMerchSSRSSkipReportTransFlight` |
| **Category WIP**<br>Report: `ProjWIPCateg` | **Category WIP**<br>`ProjListProjWIPCategory` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| **Category WIP (2 periods)**<br>Report: `ProjWIPCateg2Prd` | **Category WIP (2 periods)**<br>`ProjListProjWIPCategory2ColumnPeriod` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| **Category WIP (actual vs budget)**<br>Report: `ProjWIPCateg2Column` | **Category WIP (actual vs budget)**<br>`ProjListProjWIPCategory2Column` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| **Chinese voucher print**<br>Report: `LedgerVoucher_CN` | **Chinese voucher print**<br>`LedgerVoucher_CN` | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| **Committed costs**<br>Report: `ProjListTransCommittedCost` | **Committed costs**<br>`ProjListProjCommittedCost` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| **Component depreciation schedule**<br>**Depreciation schedule**<br>Report: `AssetDepreciationSchedule_IN` | **Component depreciation schedule**<br>`AssetComponentDepreciationSchedule_IN`<br><br>**Depreciation schedule**<br>`AssetDepreciationSchedule_IN` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Consumption tax calculation sheet**<br>Report: `TaxReportCalcSheet_JP`<br>Report: `TaxReportCalcSheet2023_JP`<br>Report: `TaxReportCalcSheet2024_JP` | **Consumption tax calculation sheet**<br>`TaxReportCalcSheet_JP`<br><br>**Consumption tax calculation sheet**<br>`TaxReportCalcSheet2023_JP`<br><br>**Consumption tax calculation sheet**<br>`TaxReportCalcSheet2024_JP` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Consumption tax report**<br>**Japanese sales tax report**<br>Report: `TaxReport_JP`<br>Report: `TaxReport2023_JP` | **Japanese sales tax report**<br>`TaxReport_JP`<br><br>**Consumption tax report**<br>`TaxReport2023_JP` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Cost estimates and costings**<br>**Price calculation**<br>Report: `ProdCalcTrans` | **Price calculation**<br>`ProdCalcTrans` | Flight | `CostManagementSSRSSkipReportTxnFlight` |
| **Create consumption proposal**<br>**Fixed asset book compare**<br>Report: `AssetBookCompare` | **Fixed asset book compare**<br>`AssetBookCompare`<br><br>**Create consumption proposal**<br>`AssetConsumptionCreateProposal` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Cross-border services**<br>Report: `LedgerXBorderActivityAT` | **Cross-border services**<br>`LedgerReport_XBorderActivityAT` | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| **Customer aging report**<br>Report: `CustAgingReport` | **Customer aging report**<br>`CustAgingBalance` | Flight | `CustSSRSReportSkipReportTransactionFlight` |
| **Customer payment retention**<br>Report: `PSACustomerRetention` | **Customer payment retention**<br>`PSACustomerRetention` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| **Customer to ledger reconciliation**<br>**Customer to ledger reconciliation report**<br>Report: `CustLedgerReconciliation` | **Customer to ledger reconciliation report**<br>`CustLedgerReconciliation`<br><br>**Customer to ledger reconciliation**<br>`CustLedgerReconciliationPeriodicTask` | Flight | `SsrsPreProcessReportSkipDefaultDatabaseTrxScope` |
| **Customer turnover and balances statement report**<br>**Vendor turnover and balances statement**<br>Report: `CustVendTurnoverAndBalance` | **Customer turnover and balances statement report**<br>`CustTurnoverAndBalance`<br><br>**Vendor turnover and balances statement**<br>`VendTurnoverAndBalance` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Depreciation plan report**<br>Report: `AssetDepreciationPlan` | **Depreciation plan report**<br>`AssetDepreciationPlan` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Depreciation summary report**<br>Report: `AssetDepreciationSummary` | **Depreciation summary report**<br>`AssetDepreciationSummary` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Dutch sales tax report**<br>Report: `TaxReport_NL` | **Dutch sales tax report**<br>`TaxReport_NL` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **EU summary VAT register**<br>**Purchase VAT register**<br>**Sales VAT register**<br>Report: `TaxVatRegister` | **Purchase VAT register**<br>`TaxVatRegisterPurch`<br><br>**Sales VAT register**<br>`TaxVatRegisterSales`<br><br>**EU summary VAT register**<br>`TaxVatRegisterWNT` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Extended journal list**<br>Report: `LedgerJournalizeReportTransLog` | **Extended journal list**<br>`LEDGERJOURNALIZEREPORT2` | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| **Financial journals**<br>Report: `LedgerFinancialJournalReportBE` | **Financial journals**<br>`LedgerFinancialJournalReportBE` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Five years undiscounted payment forecast**<br>Report: `AssetLeaseUndiscountedYearlyPaymentReport` | **Five years undiscounted payment forecast**<br>`AssetLeaseSsrsUndiscountedYearlyPayments` | Feature | `AssetLeaseSSRSSkipReportTransactionFeature` |
| **Fixed asset - low value pool statement**<br>Report: `AssetStatementLowValuePool_AU` | **Fixed asset - low value pool statement**<br>`AssetStatementLowValuePool` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed asset acquisition statement**<br>Report: `AssetExploitation` | **Fixed asset acquisition statement**<br>`AssetExploitation` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed asset acquisition statement**<br>Report: `AssetAcquisitionStatement` | **Fixed asset acquisition statement**<br>`AssetAcquisitionStatement` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed asset acquisitions**<br>**Fixed asset acquisitions report**<br>Report: `AssetAcquisition` | **Fixed asset acquisitions**<br>`AssetAcquisition`<br><br>**Fixed asset acquisitions report**<br>`AssetAcquisitionReport` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed asset balances**<br>Report: `AssetBalances` | **Fixed asset balances**<br>`AssetBalances` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed asset bar codes report**<br>Report: `AssetBarcode` | **Fixed asset bar codes report**<br>`AssetBarcode` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed asset book report - Italy**<br>Report: `AssetDepreciationLedger_IT` | **Fixed asset book report - Italy**<br>`AssetDepreciationLedger_IT` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed asset card statement**<br>Report: `AssetCard` | **Fixed asset card statement**<br>`AssetCard` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed asset disposal statement**<br>Report: `AssetDisposalActCZLV` | **Fixed asset disposal statement**<br>`AssetDisposalActCZLV` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed asset disposal statement**<br>Report: `AssetLiquidation` | **Fixed asset disposal statement**<br>`AssetLiquidation` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed asset disposals**<br>Report: `AssetDisposal` | **Fixed asset disposals**<br>`AssetDisposal` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed asset due for replacement report**<br>Report: `AssetDueReplacement` | **Fixed asset due for replacement report**<br>`AssetDueReplacement` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed asset internal transfers**<br>Report: `AssetMovement` | **Fixed asset internal transfers**<br>`FixedAssetInternalTransfers` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed asset listing report**<br>Report: `AssetListing` | **Fixed asset listing report**<br>`AssetListing` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed asset mid-quarter applicability**<br>**Fixed asset mid-quarter applicability report**<br>Report: `AssetMidQuarter` | **Fixed asset mid-quarter applicability**<br>`AssetMidQuarter`<br><br>**Fixed asset mid-quarter applicability report**<br>`AssetMidQuarterReport` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed asset movements**<br>Report: `AssetBalancesPeriod` | **Fixed asset movements**<br>`AssetBalancesPeriod` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed asset note**<br>Report: `AssetBalanceReportColumns` | **Fixed asset note**<br>`AssetReport_BalanceReportColumns` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed asset packing slip**<br>Report: `AssetPackingSlip` | **Fixed asset packing slip**<br>`AssetPackingSlip` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed asset physical inventory worksheet report**<br>Report: `AssetInventoryWorkSheet` | **Fixed asset physical inventory worksheet report**<br>`AssetInventoryWorksheet` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed asset reserve transactions**<br>Report: `AssetReserveTransactions` | **Fixed asset reserve transactions**<br>`AssetReserveTransactions` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed asset statement**<br>Report: `AssetStatement` | **Fixed asset statement**<br>`AssetStatement` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed asset statement rows report**<br>Report: `AssetStatementRowSetup` | **Fixed asset statement rows report**<br>`AssetStatementRowSetup` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed asset statement validation report**<br>Report: `AssetsInAssetStatement` | **Fixed asset statement validation report**<br>`AssetsInAssetStatement` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed asset status**<br>Report: `AssetSourceTypeStatus_CN` | **Fixed asset status**<br>`AssetSourceTypeStatus_CN` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed asset transactions**<br>Report: `AssetTransactionListing`<br>Report: `AssetTransactionListingPL` | **Fixed asset transactions**<br>`AssetTransactionListing` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed assets annual depreciation plan report**<br>Report: `AssetYearDepreciationPlan` | **Fixed assets annual depreciation plan report**<br>`AssetYearDepreciationPlan` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed assets repair**<br>Report: `AssetRepair` | **Fixed assets repair**<br>`AssetRepair` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fixed assets report - Belgium**<br>Report: `AssetOverviewBE` | **Fixed assets report - Belgium**<br>`AssetOverviewBE` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Forecast positions by budget plan report**<br>Report: `BudgetPlanHCMReport` | **Forecast positions by budget plan report**<br>`BudgetPlanHCMReport` | Flight | `BudgetPlanningSSRSSkipReportTxnFlight` |
| **Form 26 - 1: Detailed report by type for all and additional assets**<br>**Form 26 - 2: Detailed report by type for decreased assets**<br>**Form 26: Depreciable assets taxation ledger report**<br>Report: `AssetDepreciableAssets_JP` | **Form 26: Depreciable assets taxation ledger report**<br>`AssetDepreciableAssets_JP`<br><br>**Form 26 - 1: Detailed report by type for all and additional assets**<br>`AssetDepreciableAssetsAppended1_JP`<br><br>**Form 26 - 2: Detailed report by type for decreased assets**<br>`AssetDepreciableAssetsAppended2_JP` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Fully depreciated fixed assets report**<br>Report: `AssetFullyDepreciated` | **Fully depreciated fixed assets report**<br>`AssetFullyDepreciated` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Future value of fixed assets report**<br>Report: `AssetFutureValue` | **Future value of fixed assets report**<br>`AssetFutureValue` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **GAAP - cash flows**<br>Report: `AssetLeaseDisclosureGAAPCashflow` | **GAAP - cash flows**<br>`AssetLeaseDisclosureGAAPCashFLows` | Feature | `AssetLeaseSSRSSkipReportTransactionFeature` |
| **General journal entries that you didn't post**<br>Report: `LedgerOpenTransactions` | **General journal entries that you didn't post**<br>`LedgerOpenTransactions` | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| **General ledger**<br>**Ledger inquiry report**<br>Report: `LedgerGeneralLedger_CN` | **General ledger**<br>`LedgerGeneralLedger_CN` | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| **Generate DIOT declaration**<br>Report: `DIOTDeclarationReport_MX` | **Generate DIOT declaration**<br>`DIOTDeclarationReport_MX` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **German journal list**<br>Report: `LedgerJournalizeReport_DE` | **German journal list**<br>`LedgerJournalizeReport_DE` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **GST report by configuration**<br>Report: `TaxGSTTaxTransReport_MY` | **GST report by configuration**<br>`TaxGSTTaxTransReport_MY` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **ICMS tax assessment book**<br>Report: `FBAssessmentBookIcms_BR` | **ICMS tax assessment book**<br>`FBAssessmentBookIcms_BR` | Hard-coded | No configurable control (enabled in code) |
| **Impairment report (Method I: on a bigger group than CGU)**<br>**Impairment report (Method II: Allocate carrying amount of shared asset / goodwill to CGUs)**<br>Report: `AssetImpairmentAccountingReport_JP` | **Impairment report (Method I: on a bigger group than CGU)**<br>`AssetImpairmentAccountingRptMethodI_JP`<br><br>**Impairment report (Method II: Allocate carrying amount of shared asset / goodwill to CGUs)**<br>`AssetImpairmentAccountingRptMethodII_JP` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Impairment transactions report**<br>Report: `AssetImpairmentTransactions_JP` | **Impairment transactions report**<br>`AssetImpairmentTransactions_JP` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Information on the average period of payments to suppliers**<br>Report: `DueDateCompliance_ES` | **Information on the average period of payments to suppliers**<br>`DueDateCompliance_ES` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Internal transfer statement**<br>Report: `AssetInternalTransfer` | **Internal transfer statement**<br>`AssetInternalTransfer` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Inventory and Production**<br>Report: `FBInventoryAndProduction_BR` | **Inventory and Production**<br>`FBInventoryAndProduction_BR` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Invoice specification report**<br>Report: `CustInvoiceSpec` | **Invoice specification report**<br>`CustInvoiceSpec` | Hard-coded | No configurable control (enabled in code) |
| **Item/Vendor statistics**<br>**Vendor/Item statistics**<br>Report: `PurchStatisticsItemVend`<br>Report: `PurchStatisticsVendItem` | **Item/Vendor statistics**<br>`PurchStatistics_ItemVend`<br><br>**Vendor/Item statistics**<br>`PurchStatistics_VendItem` | Feature | `ProcurementAndSourcingSSRSSkipReportTransactionFeature` |
| **Journal list**<br>**Journalized journals**<br>Report: `LedgerJournalizeReport` | **Journalized journals**<br>`LedgerJournalizeReport` | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| **Lease balances forecast**<br>Report: `AssetLeaseForecastReport` | **Lease balances forecast**<br>`AssetLeaseForecastReport` | Feature | `AssetLeaseSSRSSkipReportTransactionFeature` |
| **Lease commencements**<br>Report: `AssetLeaseCommencementLeases` | **Lease commencements**<br>`AssetLeaseCommencementLeases` | Feature | `AssetLeaseSSRSSkipReportTransactionFeature` |
| **Lease modifications**<br>Report: `AssetLeaseModified` | **Lease modifications**<br>`AssetLeaseModified` | Feature | `AssetLeaseSSRSSkipReportTransactionFeature` |
| **Ledger inquiry report**<br>Report: `LedgerDetailDailyLedger_CN` | **Ledger inquiry report**<br>`LedgerDailyLedger_CN`<br><br>**Ledger inquiry report**<br>`LedgerDetailLedger_CN` | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| **Ledger inquiry report**<br>Report: `LedgerTransactionList_CN` | **Ledger inquiry report**<br>`LedgerTransactionList_CN` | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| **Ledger posting for purchase orders**<br>**Ledger posting for sales orders**<br>**Ledger transaction list**<br>Report: `LedgerTransListAccount` | **Ledger transaction list**<br>`LedgerTransListAccount`<br><br>**Ledger posting for sales orders**<br>`LedgerTransListAccountCust`<br><br>**Ledger posting for purchase orders**<br>`LedgerTransListAccountVend` | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| **Ledger reconciliation - payroll allocation**<br>**Ledger reconciliation - profit and loss**<br>**Ledger reconciliation - WIP**<br>Report: `ProjListLedgerRecon` | **Ledger reconciliation - payroll allocation**<br>`ProjListLedgerReconPayroll`<br><br>**Ledger reconciliation - profit and loss**<br>`ProjListLedgerReconProfitLoss`<br><br>**Ledger reconciliation - WIP**<br>`ProjListLedgerReconWIP` | Hard-coded | No configurable control (enabled in code) |
| **Ledger reconciliation - WIP accounts**<br>Report: `ProjListLedgerReconWIPAccount` | **Ledger reconciliation - WIP accounts**<br>`ProjListLedgerReconWIPAccount` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| **Ledger statement**<br>Report: `LedgerStatement` | **Ledger statement**<br>`LedgerStatement` | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| **Ledger totals by periods**<br>Report: `LedgerPeriodSum_FR` | **Ledger totals by periods**<br>`LedgerReport_PeriodSum_fr` | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| **Ledger transactions including dimension details**<br>Report: `LedgerDetailedTransactionsbyDimension_CN` | **Ledger transactions including dimension details**<br>`LedgerDetailedTransactionsbyDim_CN` | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| **Ledger updates - profit and loss**<br>Report: `ProjListLedgerUpdatesProfitLoss` | **Ledger updates - profit and loss**<br>`ProjListLedgerUpdatesProfitLoss` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| Report: `LedgerActivityZakat_SA` | *No direct menu item mapping* | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| Report: `LedgerMainReportZakat_SA` | *No direct menu item mapping* | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| Report: `LedgerProvisions_SA` | *No direct menu item mapping* | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| Report: `LedgerRevenueActivity_SA` | *No direct menu item mapping* | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| Report: `LedgerTransAccountVoucher_FR`<br>Report: `LedgerTransAccountVoucherMultiSelect_FR` | *No direct menu item mapping* | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| **Mass transfer**<br>Report: `AssetTransferMassReport` | **Mass transfer**<br>`AssetTransferMass` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Mass update**<br>Report: `AssetBookMassUpdate` | **Mass update**<br>`AssetBookMassUpdate` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Matrix account report (China)**<br>Report: `LedgerMatrixAccount_CN` | **Matrix account report (China)**<br>`LedgerMatrixAccount_CN` | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| **Matrix dimension**<br>Report: `LedgerMatrixDimension_CN` | **Matrix dimension**<br>`LedgerMatrixDimension_CN` | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| **Matrix report with dimensions**<br>Report: `LedgerMatrixReportWithDim_CN` | **Matrix report with dimensions**<br>`LedgerMatrixReportWithDim_CN` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Norwegian sales tax report**<br>Report: `TaxReport_NO` | **Norwegian sales tax report**<br>`TaxReport_NO` | Flight | `TaxReportDPSkipReportTransactionScopeFlight` |
| **Open purchase order lines with unconfirmed delivery date report**<br>Report: `PurchLineLeadTimeDetail` | **Open purchase order lines with unconfirmed delivery date report**<br>`PurchLineLeadTimeDetail` | Feature | `ProcurementAndSourcingSSRSSkipReportTransactionFeature` |
| **Other journals**<br>Report: `LedgerOtherJournalBE` | **Other journals**<br>`LedgerOtherJournalReportBE` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Overview journals**<br>Report: `LedgerCentralisationJournalReportBE` | **Overview journals**<br>`LedgerCentralisationJournalReportBE` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Pay specification report**<br>Report: `JmgPaySpec` | **Pay specification report**<br>`JmgEmployeeTimeSpec` | Flight | `ProdTempDbSkipReportTransactionFlight` |
| **Posted sales tax**<br>**Sales tax transactions**<br>Report: `TaxTrans` | **Posted sales tax**<br>`TaxTrans` | Flight | `TaxTransDPSkipReportTransactionScopeFlight` |
| **Posted transactions by journal**<br>Report: `LedgerTransPerJournal` | **Posted transactions by journal**<br>`LedgerTransPerJournal`<br><br>**Posted transactions by journal**<br>`LedgerTransPerJournalAction` | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| **Preview journal transactions**<br>**Print journal**<br>Report: `LedgerTransPreview_RU` | **Preview journal transactions**<br>`LedgerTransPreview_RU` | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| **Price list**<br>Report: `RetailPriceList` | **Price list**<br>`RetailPriceList`<br><br>**Price list**<br>`RetailPriceListAction` | Flight | `RetailPricingSSRSSkipReportTransFlight` |
| **Price report**<br>Report: `RetailPriceReport` | **Price report**<br>`RetailPriceReportOutput` | Flight | `RetailPricingSSRSSkipReportTransFlight` |
| **Print**<br>Report: `AssetDepPreTaxDedProcResult_JP` | **Print**<br>`AssetDepPreTaxDedProcessResultPrint_JP` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Print**<br>**Print Credit Memo**<br>Report: `TaxDocumentsReport` | **Print Credit Memo**<br>`CzTaxCreditMemo_Cust`<br><br>**Print Credit Memo**<br>`CzTaxCreditMemo_Vend`<br><br>**Print**<br>`CzTaxDocumentTable_Cust`<br><br>**Print**<br>`CzTaxDocumentTable_Vend` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Print report**<br>Report: `TaxWithholdReport_BR` | **Print report**<br>`TaxWithholdReporting` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Project actual transactions**<br>**Project transactions report**<br>Report: `ProjListTransProj` | **Project actual transactions**<br>`ProjListTransProj`<br><br>**Project transactions report**<br>`ProjListTransProject` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| **Project hour rate**<br>Report: `ProjHourRateProj` | **Project hour rate**<br>`ProjListProjHourRateProj` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| **Project on-account**<br>Report: `ProjOnAccProj` | **Project on-account**<br>`ProjListProjOnAccountProj` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| **Project on-account (2 periods)**<br>Report: `ProjOnAccProj2Prd` | **Project on-account (2 periods)**<br>`ProjListProjOnAccountProj2ColumnPeriod` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| **Project on-account (actual vs. budget)**<br>Report: `ProjOnAccProj2Column` | **Project on-account (actual vs. budget)**<br>`ProjListProjOnAccountProj2Column` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| **Project profit and loss**<br>Report: `ProjProfitLossProj` | **Project profit and loss**<br>`ProjListProjProfitLossProj` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| **Project profit and loss (2 periods)**<br>Report: `ProjProfitLossProj2Prd` | **Project profit and loss (2 periods)**<br>`ProjListProjProfitLossProj2ColumnPeriod` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| **Project profit and loss (actual vs. budget)**<br>Report: `ProjProfitLossProj2Column` | **Project profit and loss (actual vs. budget)**<br>`ProjListProjProfitLossProj2Column` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| **Project WIP**<br>Report: `ProjWIPProj` | **Project WIP**<br>`ProjListProjWIPProj` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| **Project WIP (2 periods)**<br>Report: `ProjWIPProj2Prd` | **Project WIP (2 periods)**<br>`ProjListProjWIPProj2ColumnPeriod` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| **Project WIP (actual vs. budget)**<br>Report: `ProjWIPProj2Column` | **Project WIP (actual vs. budget)**<br>`ProjListProjWIPProj2Column` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| **Purchase agreement fulfillment report**<br>**Sales agreement fulfillment report**<br>Report: `AgreementFollowUp` | **Purchase agreement fulfillment report**<br>`PurchAgreementFulfillment`<br><br>**Sales agreement fulfillment report**<br>`SalesAgreementFulfillment` | Feature | `ProcurementAndSourcingSSRSSkipReportTransactionFeature` |
| **Purchase duty**<br>Report: `TaxPurchaseTaxReport` | **Purchase duty**<br>`TaxPurchaseTaxReport` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Purchase journals**<br>Report: `LedgerPurchaseJournalReportBE` | **Purchase journals**<br>`LedgerPurchaseJournalReportBE` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Purchase list by tax code**<br>**Supply list by tax code**<br>Report: `TaxGSTReportSalesPurchList_MY` | **Purchase list by tax code**<br>`TaxGSTReportPurchListByTaxCode_MY`<br><br>**Supply list by tax code**<br>`TaxGSTReportSalesListByTaxCode_MY` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Purchase sales tax transactions**<br>Report: `TaxPurchLedger` | **Purchase sales tax transactions**<br>`TaxPurchLedger` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Purchase tax**<br>**Sales tax**<br>Report: `TaxVatDetailedReport_MX` | **Purchase tax**<br>`TaxVatPurchReport_MX`<br><br>**Sales tax**<br>`TaxVatSalesReport_MX` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Purchase Unrealized VAT Remaining**<br>Report: `TaxUnrealizedVATRemaining` | **Purchase Unrealized VAT Remaining**<br>`TaxUnrealizedVATRemaining` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Purchase VAT report**<br>**Purchase VAT report (for internal use)**<br>**Sales VAT report**<br>**Sales VAT report (for internal use)**<br>Report: `TaxInputOutputVAT` | **Purchase VAT report**<br>`TaxReportUnrealized_Input`<br><br>**Purchase VAT report (for internal use)**<br>`TaxReportUnrealized_InputDetail`<br><br>**Sales VAT report**<br>`TaxReportUnrealized_Output`<br><br>**Sales VAT report (for internal use)**<br>`TaxReportUnrealized_OutputDetail` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Reconciliation mitigate exceptions**<br>**Snapshot**<br>Report: `ReconciliationAutomationSnapshot` | **Reconciliation mitigate exceptions**<br>`ReconciliationAutomationSnapshot` | Flight | `SsrsPreProcessReportSkipDefaultDatabaseTrxScope` |
| **Redeemed**<br>Report: `MCRGiftCertRedeemed` | **Redeemed**<br>`MCRGiftCardRedeemed`<br><br>**Redeemed**<br>`MCRGiftCertRedeemed` | Flight | `MCRGiftCardRedeemedReportDPSkipTransactionScopeFlight` |
| **Reduction entry transaction summary report**<br>Report: `AssetDocumentReductionEntryTrans_JP` | **Reduction entry transaction summary report**<br>`AssetReductionEntryTransactionSummary_JP` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Resource/item profit and loss**<br>Report: `ProjProfitLossEmpl` | **Resource/item profit and loss**<br>`ProjListProjProfitLossEmplItem` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| **Resource/item profit and loss (2 periods)**<br>Report: `ProjProfitLossEmpl2Prd` | **Resource/item profit and loss (2 periods)**<br>`ProjListProjProfitLossEmplItem2ColPeriod` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| **Resource/item profit and loss (actual vs. budget)**<br>Report: `ProjProfitLossEmpl2Column` | **Resource/item profit and loss (actual vs. budget)**<br>`ProjListProjProfitLossEmplItem2Column` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| **Resource/item WIP**<br>Report: `ProjWIPEmpl` | **Resource/item WIP**<br>`ProjListProjWIPEmplItem` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| **Resource/item WIP (2 periods)**<br>Report: `ProjWIPEmpl2Prd` | **Resource/item WIP (2 periods)**<br>`ProjListProjWIPEmplItem2ColumnPeriod` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| **Resource/item WIP (actual vs. budget)**<br>Report: `ProjWIPEmpl2Column` | **Resource/item WIP (actual vs. budget)**<br>`ProjListProjWIPEmplItem2Column` | Feature | `ProjSSRSSkipReportTransactionFeature` |
| Report: `RetailPriceOverridesReport` | *No direct menu item mapping* | Flight | `RetailPricingSSRSSkipReportTransFlight` |
| Report: `RetailSalesByCustomer` | *No direct menu item mapping* | Flight | `RetailSalesSSRSSkipReportTransFlight` |
| Report: `RetailSalesByDiscount` | *No direct menu item mapping* | Flight | `RetailSalesSSRSSkipReportTransFlight` |
| Report: `RetailSalesByDiscountV2` | *No direct menu item mapping* | Flight | `RetailSalesSSRSSkipReportTransFlight` |
| Report: `RetailSalesByHour` | *No direct menu item mapping* | Flight | `RetailSalesSSRSSkipReportTransFlight` |
| Report: `RetailSalesByStaff` | *No direct menu item mapping* | Flight | `RetailSalesSSRSSkipReportTransFlight` |
| Report: `RetailSalesByTerminal` | *No direct menu item mapping* | Flight | `RetailSalesSSRSSkipReportTransFlight` |
| Report: `RetailSalesYearOverYear` | *No direct menu item mapping* | Flight | `RetailSalesSSRSSkipReportTransFlight` |
| Report: `RetailSlicedPriceReport` | *No direct menu item mapping* | Flight | `RetailPricingSSRSSkipReportTransFlight` |
| **Sales journals**<br>Report: `LedgerSalesJournalReportBE` | **Sales journals**<br>`LedgerSalesJournalReportBE` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Sales order lines**<br>Report: `SalesLinesExtended` | **Sales order lines**<br>`SalesLinesExtended` | Flight | `SalesSSRSReportSkipReportTransactionParmFlight` |
| **Sales tax (Italy)**<br>Report: `TaxReport_IT` | **Sales tax (Italy)**<br>`TaxReport_IT` | Flight | `TaxReportSkipReportTransactionFlight_IT` |
| **Sales tax by vendor - Belgium**<br>Report: `TaxAmountByVendor_BE` | **Sales tax by vendor - Belgium**<br>`TaxAmountByVendor_BE` | Flight | `TaxAmountByVendorDPSkipReportTransactionScopeFlight` |
| **Sales tax deviations**<br>Report: `TaxDeviation` | **Sales tax deviations**<br>`TaxDeviation` | Flight | `TaxDeviationDPSkipReportTransactionScopeFlight` |
| **Sales tax general journal reconciliation**<br>Report: `TaxGeneralJournalReconciliation` | **Sales tax general journal reconciliation**<br>`TaxGeneralJournalReconciliation` | Flight | `TaxGeneralJournalReconciliationDPSkipReportTransactionScopeFlight` |
| **Sales tax list**<br>Report: `TaxList` | **Sales tax list**<br>`TaxList` | Flight | `TaxListDPSkipReportTransactionScopeFlight` |
| **Sales tax list - Belgium**<br>Report: `TaxList_BE` | **Sales tax list - Belgium**<br>`TaxList_BE` | Flight | `TaxListDPSkipReportTransactionScopeFlight` |
| **Sales tax payment by code**<br>Report: `TaxReportById` | **Sales tax payment by code**<br>`TaxReportById` | Flight | `TaxReportByIdDPSkipReportTransactionScopeFlight` |
| **Sales tax report**<br>Report: `TaxReporting`<br>Report: `TaxReporting_IN` | **Sales tax report**<br>`TaxReporting` | Flight | `TaxReportingDPSkipReportTransactionScopeFlight` |
| **Sales tax report incl. corrections**<br>Report: `TaxReportInclAdjustment` | **Sales tax report incl. corrections**<br>`TaxReportInclAdjustment` | Flight | `TaxReportInclAdjustmentDPSkipReportTransactionScopeFlight` |
| **Sales tax specification by ledger transaction**<br>Report: `TaxSpecPerLedgerTrans` | **Sales tax specification by ledger transaction**<br>`TaxSpecPerLedgerTrans` | Flight | `TaxSpecPerLedgerTransDPSkipReportTransactionScopeFlight` |
| **Sales tax transactions - Belgium**<br>Report: `TaxTrans_BE` | **Sales tax transactions - Belgium**<br>`TaxTrans_BE` | Flight | `TaxTransDPSkipReportTransactionScopeFlight` |
| **Sales tax transactions - details**<br>Report: `TaxTransDetail` | **Sales tax transactions - details**<br>`TaxTransDetail` | Flight | `TaxTransDetailDPSkipReportTransactionScopeFlight` |
| **Sales tax transactions - details - Belgium**<br>Report: `TaxTransDetail_BE` | **Sales tax transactions - details - Belgium**<br>`TaxTransDetail_BE` | Flight | `TaxTransDetailDPSkipReportTransactionScopeFlight` |
| **Sales tax transactions - details - Hungary**<br>Report: `TaxTransDetail_HU` | **Sales tax transactions - details - Hungary**<br>`TaxTransDetail_HU` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Sales tax transactions re sales**<br>Report: `TaxSalesLedger` | **Sales tax transactions re sales**<br>`TaxSalesLedger` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Sales tax/Ledger reconciliation**<br>Report: `TaxLedgerReconciliation` | **Sales tax/Ledger reconciliation**<br>`TaxReport_LedgerReconciliation` | Flight | `SsrsPreProcessReportSkipDefaultDatabaseTrxScope` |
| **Singaporean sales tax report**<br>Report: `TaxReport_SG` | **Singaporean sales tax report**<br>`TaxReport_SG` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Spanish journal list**<br>Report: `LedgerJournalizeReport_ES` | **Spanish journal list**<br>`LedgerJournalizeReport_ES` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Specification**<br>Report: `TaxTransCode` | **Specification**<br>`TaxTransCode` | Flight | `TaxTransCodeDPSkipReportTransactionScopeFlight` |
| **Summarized general ledger**<br>Report: `LedgerSummarizedGL_CN` | **Summarized general ledger**<br>`LedgerSummarizedGL_CN` | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| **Summary tax**<br>Report: `TaxVatSummaryReport_MX` | **Summary tax**<br>`TaxVatSummaryReport_MX` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Tax declaration of import**<br>Report: `TaxReportAlandImport_FI` | **Tax declaration of import**<br>`TaxReportAlandImport_FI` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Tax depreciation**<br>Report: `AssetTaxCategoryDepreciation` | **Tax depreciation**<br>`AssetTaxCategoryDepreciation` | Feature | `AssetSSRSSkipReportTransactionFeature` |
| **Tax reconciliation report**<br>Report: `TaxReconciliationReport` | **Tax reconciliation report**<br>`TaxReconciliationReport` | Feature and flight | `UseNewCalculationMethodForTaxReconciliationReportFeature`<br>`SsrsPreProcessReportSkipDefaultDatabaseTrxScope` |
| **TCS statement**<br>**TDS statement**<br>Report: `TaxWithholdStatement` | **TCS statement**<br>`TaxWithholdStatementTCS`<br><br>**TDS statement**<br>`TaxWithholdStatementTDS` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Top 100 vendors**<br>Report: `PurchRanking` | **Top 100 vendors**<br>`PurchRankingReport` | Feature | `ProcurementAndSourcingSSRSSkipReportTransactionFeature` |
| **Top products report**<br>Report: `RetailTopProducts` | **Top products report**<br>`RetailTopProductsSSRSReport` | Flight | `RetailMerchSSRSSkipReportTransFlight` |
| **Transaction list by date**<br>Report: `LedgerTransListDate` | **Transaction list by date**<br>`LedgerTransListDate` | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| **Transaction list by date or voucher**<br>Report: `LedgerTransDateVoucher_FR` | **Transaction list by date or voucher**<br>`LedgerReport_TransDateVoucher_Fr` | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| **Transaction origin**<br>Report: `LedgerTransBase` | **Transaction origin**<br>`LedgerTransBase` | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| **Trial balance**<br>Report: `LedgerTrialBalanceReport_CN` | **Trial balance**<br>`LedgerTrialBalance_CN` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Turnover and balances statement**<br>Report: `LedgerTurnoverAndBalance` | **Turnover and balances statement**<br>`LedgerTurnoverAndBalance` | Feature | `GFMRegulatoryReportingSSRSSkipReportTransactionFeature` |
| **Unsettled transactions report**<br>Report: `LedgerTransOpen` | **Unsettled transactions report**<br>`LedgerReport_TransOpen` | Feature | `GeneralLedgerSSRSSkipReportTransactionFeature` |
| **VendInvoice**<br>**Vendor invoice transactions report**<br>Report: `VendInvoice` | **VendInvoice**<br>`VendInvoice` | Hard-coded | No configurable control (enabled in code) |
| **Vendor to ledger reconciliation**<br>**Vendor to ledger reconciliation report**<br>Report: `VendLedgerReconciliation` | **Vendor to ledger reconciliation report**<br>`VendLedgerReconciliation`<br><br>**Vendor to ledger reconciliation**<br>`VendLedgerReconciliation_NoReportLabel` | Flight | `SsrsPreProcessReportSkipDefaultDatabaseTrxScope` |
| **Vendors**<br>Report: `VendorListBasic` | **Vendors**<br>`VendorListBasic` | Feature | `ProcurementAndSourcingSSRSSkipReportTransactionFeature` |
| **Weighted-average discount rate**<br>**Weighted-average remaining lease term**<br>Report: `AssetLeaseDiscountRateReport`<br>Report: `AssetLeaseLeaseTermReport` | **Weighted-average discount rate**<br>`AssetLeaseDisclosureDiscountRate`<br><br>**Weighted-average remaining lease term**<br>`AssetLeaseLeaseTermReport` | Feature | `AssetLeaseSSRSSkipReportTransactionFeature` |
| **Work order consumption**<br>Report: `EntAssetWorkOrderConsumption` | **Work order consumption**<br>`EntAssetWorkOrderConsumptionReport` | Feature | `EntAssetSSRSSkipReportTransactionFeature` |

Menu items and captions are included when a high-confidence metadata mapping is available.
