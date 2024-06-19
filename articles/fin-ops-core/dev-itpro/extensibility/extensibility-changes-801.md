---
title: Extensibility changes in Finance and Operations update 8.0.1
description: Learn about the extensibility features that were released in Dynamics 365 for Finance and Operations update 8.0.1.
author: FrankDahl
ms.author: fdahl
ms.topic: article
ms.date: 05/17/2018
ms.custom:
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2018-05-31
ms.dyn365.ops.version: App 8.0.1
---

# Extensibility changes in Finance and Operations update 8.0.1

[!include [banner](../includes/banner.md)]

This is a list of extensibility features that were implemented in Dynamics 365 for Finance and Operations update 8.0.1. For more information about the schedule of changes that support extensibility, see [Application extensibility plans](extensibility-roadmap.md).

## Refactored methods to support extensibility

These methods have been refactored to support extensibility through chain of command, delegates, or by providing access to members.

| Method|
| --------------- |
|Class ProjControlPeriod::PeriodInsert|
|Class ProjInvoiceChoose::doSalesLine|
|Class CustInvoiceJour::printFreeTextJournal|
|Class ProjCostControl.createEmptyTransactionType|
|Class ProjEstimate::autoGenerateEstimateLinesFromTask|
|Class ProjEstimateDataContract.updateEstimates|
|Class ProjForecastBudget.Run|
|Class ProjHierarchyProvider.preDeleteHierarchy|
|Class ProjPlanVersionsManager::CopyTasks|
|Class ProjPlanVersionsManager.createDraftFromPublishedVersion|
|Class ProjPlanVersionsManager.PublishQuotationSubHierarchy|
|Class ProjPlanVersionsManager.CreateDraftVersion|
|Class ProjTask.addTask|
|Class ProjInvoiceProposalCreateLines.performTransTypeSelectionCtrlLookup|
|Class VendOpenTrans.editMarkTrans|
|Class CustVendReversePosting.reverseTaxWithholdTrans|
|Class CustVendSettle.postPennyDiff|
|Class CustVendSettle.processStillOpenTransactions|
|Class InventTransferOrderOverviewDP.insertTmp|
|Class LedgerJournalTransCost.LedgerJournalTrans.Create|
|Class ProjAdjustmentSelect.dialog|
|Class ProjEstimate.syncEstimateLinesFromTask|
|Class ProjEstimateDataContract.UpdateEstimates|
|Class ProjForecastTransferFromWbs.transferToForecast|
|Class ProjWizardActivityCtrl.insertDBOnServer|
|Class ProjTaskEstimatesSynchronizer.calcTotalEstimateLineHours|
|Class ProjTaskEstimatesSynchronizer.countNumberOfHourEstimateLines|
|Class ProjTaskEstimatesSynchronizer.syncExistingHourEstimatesWithTask|
|Class ProjTaskEstimatesSynchronizer.syncHourEstimatesWithTaskEffort|
|Class ProjWbsCostPlanningServerActions.executeDataRetrievalAction|
|Class ProjWbsCostPlanningServerActions.getProjectCategoryTypes|
|Class ProjWbsSchedulePlanningServerActions.executeAction|
|Class ProjWbsSchedulePlanningServerActions.executeDataRetrievalAction|
|Class ProjStatisticCalc.validate|
|Class WHSInventReserve.insert|
|Class WHSInventReserveDelta.insert|
|Class ProjInvoiceProposalCreateLines.performTransTypeSelectionCtrlLookup|
|Class ProjJournalTransEmpl - Datasource: ProjJournalTrans.Validate|
|Class LedgerJournalEngine.initTaxItemGroup|
|Class LedgerJournalEngine.initValue|
|Class ProjJournalTrans.mergeResourceDimensionDefault|
|Class ProjTask.setTaskinfo|
|Class ProjJournalName.standardJournalName|
|Form ProjInvoiceProposalCreateLines.performTransTypeSelectionCtrlLookup|

## Other extensibility enhancements

In addition to the refactored methods, the following extensibility enhancements have been made.

- Support variable number of decimals - InventTestLowerLimit
- Support variable number of decimals -  InventTestLowerTolerance
- Support variable number of decimals -  InventTestStandardValue 
- Support variable number of decimals -  InventTestUpperLimit
- Support variable number of decimals - InventTestUpperTolerance
- Support to skip prompt on transaction reversal
- Enable extension of PSAProjQuotationApproval workflow


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
