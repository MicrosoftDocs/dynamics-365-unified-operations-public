---
title: Extensibility changes in Dynamics 365 for Finance and Operations version 10.0.2
description: Learn about the extensibility features that were released in Microsoft Dynamics 365 for Finance and Operations version 10.0.2.
author: FrankDahl
ms.author: fdahl
ms.topic: article
ms.date: 05/10/2019
ms.custom:
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2019-05-10
ms.dyn365.ops.version: App 10.0
---

# Extensibility changes in Dynamics 365 for Finance and Operations version 10.0.2

[!include [banner](../includes/banner.md)]

This article lists the extensibility features that were implemented in Microsoft Dynamics 365 for Finance and Operations version 10.0.2. For more information about the schedule of changes that support extensibility, see [Application extensibility plans](extensibility-roadmap.md).

## Enumerations made extensible

The following enumerations have been made extensible in this update:

- MarkupModuleType
- MCRCustPaymType
- PaymSchedBy

## SQL operations made extensible

The following SQL operations have been made extensible in this update:

- JmgPayAdjustment.payAdjustLoop
- ProjPosting.ExtensionHash.New field
- WmsArrivalOverviewGeneration.buildPurch
- WmsArrivalOverviewGeneration.buildTransferOrder

## Metadata changes

The following metadata changes have been made in this update:

- CostSheetPercent.NoOfDecimalsIsExtensible
- WHSCycleCountingWarehouseWorkLineEntity.IsPublic

## Refactored methods

The following methods have been refactored to support extensibility:

- /Forms/ProjJournalTable/datasource/ProjJournalTable.initValue
- /Forms/PurchReqTable.instantiatePurchReqTableForm
- /Forms/PurchReqTable/DataSource/PurchReqTable.init
- /Forms/SalesQuotationProjLinkWizard/Controls/ProjInvoiceId.lookup
- /Tables/SalesTable.lastQuotation
- AccPolicyProductReceipt.isAccountingRequiredForSourceDocLine
- AssetFixedAssetEntity.overrideDataSource
- AssetProposalDepreciation.run
- AssetTableMethod.init
- BankAccountReconcile.validate
- Class\\BomCalcCost.calcCostModel
- Class\\MCRLoadContinuityCustInfo.insertLineData
- Class\\McrPriceHistoryUpdate.insertNewlyFoundReferences
- Class\\McrPriceHistoryUpdate.update
- Class\\McrPriceHistoryUpdate.updatePriceHistoryLineReferences
- Class\\ProjCopyItemEstimates.copyToItemRequirment
- Class\\PurchAutoCreate\_RFQ.createPurchOrderRFQLineReference
- Class\\ReqEventProcessDeleteUnusedKanban.deleteUnusedKanban
- Class\\ReqEventProcessDeleteUnusedKanban.run
- Class\\ReqTransUpdate.updateLogAddQty
- Class\\SalesCancelOrder.run
- Class\\SalesCreateOrderFromCustomer.main
- Class\\TAMVendRebateCorrectClaims.rebateAlreadyGiven
- Class\\tamVendRebateTableStatusType\_Approved.runPayment
- Class\\TamVendRebateTableStatusType\_Calculated.inserted
- Class\\TamVendRebateTableStatusType\_Calculated.runPayment
- Classes\\TaxWithhold.createAllTaxWithholdTrans
- Classes\\TaxWithhold.isCalculateTaxWithholdingNeeded\_TH
- Classes\\TaxWithhold.postTaxWithhold
- Classes\\TaxWithhold.totalInvoiceLineAmountSettled\_TH
- CustDirectDebitMandate.setDefaultMandate
- CustDueReportDetailDP.class declaration
- CustDueReportDetailDP.insertCustDueReportDetailTmp
- CustQuotationConfirmJour.printJournal
- CustVendCreatePaymJournal.pack
- CustVendCreatePaymJournal.parmHasBatchBeenSplit
- CustVendEditTaxBranch\_TH.init
- CustVendSumForPaym.run
- CustVendTransSettlement.post
- DimDerDistRuleSalesComplInvoice\_BR.createDimAllocForProjRevenue
- EcoResProductCreateExtended.SetAllowEditField
- EcoResProductVariantEntity.findDataSource
- FBSpedFileCreator\_Fiscal\_BR.createRecordC195
- Form\\ProdTableCreate.canContinueWithEmptyDim
- Form\\PurchCreateFromSalesOrder\\DataSource\\SalesLine.included
- Form\\PurchCreateFromSalesOrder\\DataSource\\SalesLine.specifyVendAccount
- Forms\\TaxWithholdTable.init
- FreeTextInvoiceDP.setSysDocuBrandDetails
- InventItemOrderSetupMap.checkNotStopped
- InventNonConformanceTable.InventNonConformanceTable.Create
- InventUpd\_Estimated.updateAutoDimBatchId
- InventUpdateReserveMore.InventUpdateReserveMore
- InventValueReportPopulateItem.updateReportLinePL
- JmgCalcApproveDateView.viewDate member
- JmgCalcApproveWeekView.viewDate member
- JmgPayAdjustment.payAdjustLoop
- LedgerJournalPeriodicCopy.journalTransCopy
- LedgerTransStatementDP.populateTempTableLedgerInStaging
- MCRCustpaym.validateWrite
- MCRFullTextSearch.buildSearchText
- MCRFullTextSearch.truncate
- MCRHoldCodeTrans.insert
- MCRHoldCodeTrans.setOrderStoppedFlag
- MCRHoldCodeTrans.unreserve
- McrPriceHistoryForm.calcPotential
- McrPriceHistoryForm.insertPotentialTradeAgreements
- PaymTerm.validateWrite
- PdsRebateAgreement.checkLineBreaks
- PdsRebateAgreement.groupChangeCheckValid
- PdsRebateAgreement.lineAmountHasGapOrOverlap
- PdsRebateAgreement.lineQuantityHasGapOrOverlap
- PdsRebateAgreementLine.selectRebateAgreementLineMax
- PriceDisc.mcrCalcPostageDisc
- PriceDiscLinePolicyRule.retrieveSystemPolicyFieldList
- ProdUpdCostEstimation.updateSubPurchLine
- ProjBudgetManager.createBudgetLineDetail
- ProjBudgetManager.getQuery
- ProjForecastCost.validateWrite
- ProjForecastEmpl.validateWrite
- ProjForecastRevenue.validateWrite
- ProjLedgerUpdate.insert
- ProjPlanVersionsManager.importHierarchy
- ProjPlanVersionsManager.importProjPlanVersionRecords
- ProjPost.PostCost
- ProjPost.PostCost
- ProjWorkBreakdownStructureHelper.addQuotationRelatedRecordsForTask
- ProjWorkBreakdownStructureHelper.Addtask
- ProjWorkBreakdownStructureHelper.Addtask
- ProjWorkBreakdownStructureHelper.Addtask
- ProjWorkBreakdownStructureV2FormHelper.IndentTaskV2
- ProjWorkBreakdownStructureV2FormHelper.MoveTasks
- PurchFormletterParmDataInvoice.createParmLinesAndTable
- PurchLine.delete
- PurchLine.distributionUpdateNeeded
- PurchLine.initFromPriceDisc
- PurchLine.insert
- PurchLine.update
- PurchLineType.statusChangeAllowed
- ReqEventProcessKanban.newStandard
- ReqTransNeutralTracker.trackReqTrans
- ReqTransPoMarkFirm.create
- Retail channel: CartWorkflowHelper.AllowAggregation
- RetailEcoResProductReleaseManager\_Extension.setAndSaveRetailProductProperties
- RetailMassUpdateUploadDBManager.insertIntoProductProperty
- RetailPeriodicDiscount.validatePriceGroup
- RetailTransactionServiceCustomer.newCustomer
- RetailTransactionTransformer.ReadDiscountLines
- SalesInvoiceDP.setSysDocuBrandDetails
- SalesInvoiceJournalPost.run
- SalesInvoiceJournalPostBase.run
- SalesLine.CheckItemId
- Table\\InventTable.purchPriceAgreement
- Tables\\TaxWithholdTrans.copyTaxWithholdTrans, initFromTaxWithholdTable, insert, validateWrite, amountTotalWHT, existPeriod\_TH
- TAMVendRebatePaymentPost.main
- TAMVendRebateTableProcess.runProcess
- TrvPostExpenseHeader.postCustVendTransactions
- TrvPostExpenseHeader.postCustVendTransactions
- WhsControlLicensePlateId.process
- WhsLicensePlateLabelBuild.insertSingleLabelMenuItem
- WhsLicensePlateLabelBuild.insertSingleLabelPrintLine
- WhsrfControlData.processLegacyControl
- WhsWorkCreateProdPut.createReportFinishedParameters
- WhsWorkCreateProdPut.insertProdParmforCoByProduct
- WhsWorkCreateProdPut.insertProdParmForProdItem
- WhsWorkCreateProdPut.setAcceptError
- WHSWorkCreateReplenishment.checkExistingReplenWork
- WhsWorkExecuteDisplay.buildPick
- whsWorkExecuteDisplayInquiryLocation.buildLocationInquiry
- WmsArrivalOverviewGeneration.buildInventTransId
- WmsOrderTransType\_OutputDontPostTransfer.decreaseQty
- WmsOrderTransType\_OutputDontPostTransfer.increaseQtyOverdelivery

## Other extensibility enhancements

- The accessModifier of Classes\\BankPositivePayExport.Class changed from private to protected.
- The InventItemOrderSetupMap map was made extensible.
- **Retail channel:** Custom columns in RetailTransactionView.
- **Retail channel:** The sign-in request can be overridden.
- **Retail channel:** Shipping view extension controller class.
- **Retail channel:** Support for the AppBar button in AddressAddEditView.
- **Retail channel:** Support for overriding the Bank deposit amount key in the dialog box.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
