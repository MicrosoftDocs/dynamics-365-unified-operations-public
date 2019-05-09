---
# required metadata

title: Extensibility changes in Dynamics 365 for Finance and Operations version 10.0.2
description: This topic lists the extensibility features that were released in Dynamics 365 for Finance and Operations version 10.0.2.
author: FrankDahl
manager: AnnBe
ms.date: 05/10/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 


# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: fdahl
ms.search.validFrom: 2019-05-10
ms.dyn365.ops.version: App 10.0

---

# Extensibility changes in Dynamics 365 for Finance and Operations version 10.0.2

[!include [banner](../includes/banner.md)]


This is a list of extensibility features that were implemented in Dynamics 365 for Finance and Operations version 10.0.2. For more information about the schedule of changes that support extensibility, see [Application extensibility plans](extensibility-roadmap.md).

## Enumerations made extensible

These enumerations have been made extensible in this update.

## Enumerations made extensible
| Enumeration |
|---|
| MarkupModuleType |
| MCRCustPaymType |
| PaymSchedBy |


## SQL operations made extensible

These SQL operations have been made extensible in this update.

| Operations |
|---|
| JmgPayAdjustment.payAdjustLoop |
| ProjPosting.ExtensionHash.New field |
| WmsArrivalOverviewGeneration.buildPurch |
| WmsArrivalOverviewGeneration.buildTransferOrder |

## Metadata changes

These metadata changes have been made in this update.

| Operations |
|---|
| CostSheetPercent.NoOfDecimalsIsExtensible |
| WHSCycleCountingWarehouseWorkLineEntity.IsPublic |


## Refactored methods

These methods have been refactored to support extensibility.

| Operations |
|---|
| /Forms/ProjJournalTable/datasource/ProjJournalTable.initValue |
| /Forms/PurchReqTable.instantiatePurchReqTableForm |
| /Forms/PurchReqTable/DataSource/PurchReqTable.init |
| /Forms/SalesQuotationProjLinkWizard/Controls/ProjInvoiceId.lookup |
| /Tables/SalesTable.lastQuotation |
| AccPolicyProductReceipt.isAccountingRequiredForSourceDocLine |
| AssetFixedAssetEntity.overrideDataSource |
| AssetProposalDepreciation.run |
| AssetTableMethod.init |
| BankAccountReconcile.validate |
| Class\BomCalcCost.calcCostModel |
| Class\MCRLoadContinuityCustInfo.insertLineData |
| Class\McrPriceHistoryUpdate.insertNewlyFoundReferences |
| Class\McrPriceHistoryUpdate.update |
| Class\McrPriceHistoryUpdate.updatePriceHistoryLineReferences |
| Class\ProjCopyItemEstimates.copyToItemRequirment |
| Class\PurchAutoCreate_RFQ.createPurchOrderRFQLineReference |
| Class\ReqEventProcessDeleteUnusedKanban.deleteUnusedKanban |
| Class\ReqEventProcessDeleteUnusedKanban.run |
| Class\ReqTransUpdate.updateLogAddQty |
| Class\SalesCancelOrder.run |
| Class\SalesCreateOrderFromCustomer.main |
| Class\TAMVendRebateCorrectClaims.rebateAlreadyGiven |
| Class\tamVendRebateTableStatusType_Approved.runPayment |
| Class\TamVendRebateTableStatusType_Calculated.inserted |
| Class\TamVendRebateTableStatusType_Calculated.runPayment |
| Classes\TaxWithhold.createAllTaxWithholdTrans |
| Classes\TaxWithhold.isCalculateTaxWithholdingNeeded_TH |
| Classes\TaxWithhold.postTaxWithhold |
| Classes\TaxWithhold.totalInvoiceLineAmountSettled_TH |
| CustDirectDebitMandate.setDefaultMandate |
| CustDueReportDetailDP.class declaration |
| CustDueReportDetailDP.insertCustDueReportDetailTmp |
| CustQuotationConfirmJour.printJournal |
| CustVendCreatePaymJournal.pack |
| CustVendCreatePaymJournal.parmHasBatchBeenSplit |
| CustVendEditTaxBranch_TH.init |
| CustVendSumForPaym.run |
| CustVendTransSettlement.post |
| DimDerDistRuleSalesComplInvoice_BR.createDimAllocForProjRevenue |
| EcoResProductCreateExtended.SetAllowEditField |
| EcoResProductVariantEntity.findDataSource |
| FBSpedFileCreator_Fiscal_BR.createRecordC195 |
| Form\ProdTableCreate.canContinueWithEmptyDim |
| Form\PurchCreateFromSalesOrder\DataSource\SalesLine.included |
| Form\PurchCreateFromSalesOrder\DataSource\SalesLine.specifyVendAccount |
| Forms\TaxWithholdTable.init |
| FreeTextInvoiceDP.setSysDocuBrandDetails |
| InventItemOrderSetupMap.checkNotStopped |
| InventNonConformanceTable.InventNonConformanceTable.Create |
| InventUpd_Estimated.updateAutoDimBatchId |
| InventUpdateReserveMore.InventUpdateReserveMore |
| InventValueReportPopulateItem.updateReportLinePL |
| JmgCalcApproveDateView.viewDate member |
| JmgCalcApproveWeekView.viewDate member |
| JmgPayAdjustment.payAdjustLoop |
| LedgerJournalPeriodicCopy.journalTransCopy |
| LedgerTransStatementDP.populateTempTableLedgerInStaging |
| MCRCustpaym.validateWrite |
| MCRFullTextSearch.buildSearchText |
| MCRFullTextSearch.truncate |
| MCRHoldCodeTrans.insert |
| MCRHoldCodeTrans.setOrderStoppedFlag |
| MCRHoldCodeTrans.unreserve |
| McrPriceHistoryForm.calcPotential |
| McrPriceHistoryForm.insertPotentialTradeAgreements |
| PaymTerm.validateWrite |
| PdsRebateAgreement.checkLineBreaks |
| PdsRebateAgreement.groupChangeCheckValid |
| PdsRebateAgreement.lineAmountHasGapOrOverlap |
| PdsRebateAgreement.lineQuantityHasGapOrOverlap |
| PdsRebateAgreementLine.selectRebateAgreementLineMax |
| PriceDisc.mcrCalcPostageDisc |
| PriceDiscLinePolicyRule.retrieveSystemPolicyFieldList |
| ProdUpdCostEstimation.updateSubPurchLine |
| ProjBudgetManager.createBudgetLineDetail |
| ProjBudgetManager.getQuery |
| ProjForecastCost.validateWrite |
| ProjForecastEmpl.validateWrite |
| ProjForecastRevenue.validateWrite |
| ProjLedgerUpdate.insert |
| ProjPlanVersionsManager.importHierarchy |
| ProjPlanVersionsManager.importProjPlanVersionRecords |
| ProjPost.PostCost |
| ProjPost.PostCost |
| ProjWorkBreakdownStructureHelper.addQuotationRelatedRecordsForTask |
| ProjWorkBreakdownStructureHelper.Addtask |
| ProjWorkBreakdownStructureHelper.Addtask |
| ProjWorkBreakdownStructureHelper.Addtask |
| ProjWorkBreakdownStructureV2FormHelper.IndentTaskV2 |
| ProjWorkBreakdownStructureV2FormHelper.MoveTasks |
| PurchFormletterParmDataInvoice.createParmLinesAndTable |
| PurchLine.delete |
| PurchLine.distributionUpdateNeeded |
| PurchLine.initFromPriceDisc |
| PurchLine.insert |
| PurchLine.update |
| PurchLineType.statusChangeAllowed |
| ReqEventProcessKanban.newStandard |
| ReqTransNeutralTracker.trackReqTrans |
| ReqTransPoMarkFirm.create |
| Retail channel: CartWorkflowHelper.AllowAggregation |
| RetailEcoResProductReleaseManager_Extension.setAndSaveRetailProductProperties |
| RetailMassUpdateUploadDBManager.insertIntoProductProperty |
| RetailPeriodicDiscount.validatePriceGroup |
| RetailTransactionServiceCustomer.newCustomer |
| RetailTransactionTransformer.ReadDiscountLines |
| SalesInvoiceDP.setSysDocuBrandDetails |
| SalesInvoiceJournalPost.run |
| SalesInvoiceJournalPostBase.run |
| SalesLine.CheckItemId |
| Table\InventTable.purchPriceAgreement |
| Tables\TaxWithholdTrans.copyTaxWithholdTrans, initFromTaxWithholdTable, insert, validateWrite,  |amountTotalWHT, existPeriod_TH
| TAMVendRebatePaymentPost.main |
| TAMVendRebateTableProcess.runProcess |
| TrvPostExpenseHeader.postCustVendTransactions |
| TrvPostExpenseHeader.postCustVendTransactions |
| WhsControlLicensePlateId.process |
| WhsLicensePlateLabelBuild.insertSingleLabelMenuItem |
| WhsLicensePlateLabelBuild.insertSingleLabelPrintLine |
| WhsrfControlData.processLegacyControl |
| WhsWorkCreateProdPut.createReportFinishedParameters |
| WhsWorkCreateProdPut.insertProdParmforCoByProduct |
| WhsWorkCreateProdPut.insertProdParmForProdItem |
| WhsWorkCreateProdPut.setAcceptError |
| WHSWorkCreateReplenishment.checkExistingReplenWork |
| WhsWorkExecuteDisplay.buildPick |
| whsWorkExecuteDisplayInquiryLocation.buildLocationInquiry |
| WmsArrivalOverviewGeneration.buildInventTransId |
| WmsOrderTransType_OutputDontPostTransfer.decreaseQty |
| WmsOrderTransType_OutputDontPostTransfer.increaseQtyOverdelivery |


## Other extensibility enhancements

| Operations |
|---|
| Classes\BankPositivePayExport.Class variable accessModifier changed from private to protected |
| Map InventItemOrderSetupMap made extensible |
| Retail channel: Custom columns on the RetailTransactionView |
| Retail channel: Overridable login request |
| Retail channel: Shipping view extension controller class. |
| Retail channel: Support for AppBar button in AddressAddEditView |
| Retail channel: Support for overriding the Bank deposit amount key in dialog |
