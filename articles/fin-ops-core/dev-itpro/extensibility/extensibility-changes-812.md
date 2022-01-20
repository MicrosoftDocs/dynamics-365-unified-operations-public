---
title: Extensibility changes in Dynamics 365 for Finance and Operations version 8.1.2
description: This topic lists the extensibility features that were released in Dynamics 365 for Finance and Operations version 8.1.2
author: FrankDahl
ms.date: 12/18/2018
ms.topic: article
ms.prod: 
ms.technology: 


# ms.search.form: 
# ROBOTS: NOINDEX, NOFOLLOW
audience: Developer
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: fdahl
ms.search.validFrom: 2018-11-02
ms.dyn365.ops.version: App 8.1.2

---

# Extensibility changes in Dynamics 365 for Finance and Operations version 8.1.2

[!include [banner](../includes/banner.md)]

This is a list of extensibility features that were implemented in Dynamics 365 for Finance and Operations version 8.1.2. For more information about the schedule of changes that support extensibility, see [Application extensibility plans](extensibility-roadmap.md).

## Enumerations made extensible

These enumerations have been made extensible in this update.

| Enumeration|
| --------------- |
|DimensionHierarchyType|
|DirPartyType|
|DirPersonMaritalStatus|
|PrintPostCancel|
|INSAffiliate|
|LedgerJournalLinesDisplayOption|
|LedgerTransPerJournal|
|ProjDortValue|
|ProjPaymentStatus|
|RequisitionReleaseType|
|RetailPOSSeedDataType|
|SysDimension|
|TrvExpType|
|TSTimesheetEntryGridView|
|VendProspectiveVendorRegistrationWizardTab

## Metadata changes

These metadata changes have been made in this update.

| Operation |
| --------------- |
|DataEntities/LedgerJournalNameEntity/Fields/DeleteLinesAfterPosting.Allow Edit|
|DataEntities/LedgerJournalNameEntity/Fields/DeleteLinesAfterPosting.AllowEditOnCreate|
|Forms/AssetProposalDepreciation/Design/Tab/ParametersTabPage/ParametersGroup/SummarizedDepreciationControl.Value|
|Data manipulation method not raising event: PriceDiscAdmDeleteTradeAgreements.run|
|Data Types/Base Enums/WHSReverseWorkMode.Label|
|DataEntity smmProspectEntity is not public|
|DataEntityView/GeneralJournalAccountEntryEntity.PublicCollectionName, PublicEntityName and IsPublic|
|Enum/HcmPersonGender/EnumValue/NonSpecific.Label|
|LedgerJournalEngine.shouldOverwriteAmountWithSettledAmount|
|Query/LedgerDerivedFinHierarchy/EcoResCategoryHierarchyRole_1/Ranges/NamedCategoryHierarchyRole.Range/Value|
|Table/TSTimesheetLine/TableFieldEnum|
|Tables/InventTransPosting.DateVoucherTransIdx|
|Update unique indexes in pricing tables for project|

## Refactored methods

These methods have been refactored to support extensibility.

| Refactored methods                                                                             |
|------------------------------------------------------------------------------------------------|
|AgreementConfirmationDP.getAgreementLine|
|AgreementConfirmationDP.getAgreementLineHistory|
|AssetBook.initDepreciationProfile|
|AssetPost.createTrueUpDepreciation|
|AssetPost.reduceLastDepreciation|
|Bank_CA.checkBankAccount|
|Bank_CA.checkBankRegNum|
|BankReconMatchingRuleAutoProcessor.doProcessMatchRule|
|BankReconMatchingRuleAutoProcessor.performMatchAction|
|BomCalcItem.calcCostSheet|
|ChequeCopy.printCheque|
|ChequeDP.fetch|
|Coupons.AddCouponTrigger|
|Cust.initLedgerVoucher|
|CustAgingReportDP.heading|
|CustBalanceList.constructAgingCalculation|
|CustCollectionLetterCreate.createJournal|
|CustCollectionLetterCreate.run|
|CustCollectionLetterPost.updateQuery|
|CustCollections.showAgingIndicator|
|CustCollectionsExcelStatement.setTransactionWorksheetHeader|
|CustDirectDebitMandate.lookupReference|
|CustDirectDebitMandate.validateMandate|
|CustDirectDebitMandate.validateMandate|
|CustFreeInvoiceCorrection.createAdjustingCorrectedInvoice|
|CustFreeInvoiceCorrection.createTaxes|
|CustFreeInvoiceCorrectionPost.postAdjustingInvoice|
|CustFreeInvoiceCorrectionPost.validate|
|CustinvoiceLine.insert|
|CustInvoicePrintJob.buildQueryForFreeText|
|CustInvoicePrintJob.processFreeText|
|CustOpenTrans.editMarkTrans|
|CustOpenTransReverse.markTrans|
|CustOverPaym.run|
|CustPackingSlipJour.printJournal|
|CustPaymEntry.hasMultipleOpenTransReferences|
|CustPaymEntry.isInvalidOpenTransReference|
|CustPostInvoice.allocateNumAndVoucher|
|CustPostInvoice.createJournalHeader|
|CustRecurrenceInvoicePostService.postRecurrenceInvoice|
|CustSettlementPriorityProcessing.initCustTransOpen|
|CustStatistics.TmpStatPer.linkActive|
|CustTable.createRecord|
|CustTable.CustTable_DS/fields/CustGroup/modified|
|CustVendCheque.checkDataOk|
|CustVendCheque.output|
|CustVendChequeSlipTextCalculator.getMaxSlipLines|
|CustVendChequeSlipTextCalculator.getUnprintableReportArea|
|CustVendCreatePaymJournal.runPaymentProposalGenerationProcess|
|CustVendCreatePaymJournal.runPaymentProposalGenerationProcess|
|CustVendOpenTransManager.createTaxWithholding|
|CustVendPaymProposal.addCustVendTransOpen|
|CustVendReversePosting.restoreCustVendTransOpen|
|CustWriteOff.calcSalesTaxOnOpenTrans|
|CustWriteOff.generateSummarizedTmpTaxTrans|
|DataEntityView/ExpenseJournalLineEntity.DataEntityView/ExpenseJournalLineEntity|
|DirPartyPostalAddressFormHandlerExt.onUpdateTransactionCaller_delegate|
|Extensible class method: PriceDisc.mcrPriceDiscTableFound|
|FBSpedFileCreator_Contabil_BR.createRecordI052|
|FiscalDocumentDate_BR.lastIssueDateForSeries|
|HrpSigningLimitPolicyUtil.createDefaultLimit|
|HrpSigningLimitPolicyUtil.insertJobOrCompensationRule|
|HrpSigningLimitPolicyUtil.private RefRecId checkLimitAgreementDetail(HRPTmpLimitAgreementRule _tmpLimitAgreementRule,HRPAuthorityBasis _authorityBasis)|
|HrpWorkerLimit.private recId getAuthBaseRecId(HRPAuthorityBasis _authBasis, RefRecId _positionId)|
|InterCompanySyncPurchTableType.setSalesTableData|
|InventCountCreate_Base.doCountingBasedOnCountCode|
|InventMov_Purch.updateAutoLossProfit|
|InventMov_Purch.updateLedgerFinancial|
|InventMovement.addLedgerPhysicalAmounts|
|InventMovement.addLedgerVoucherRevenueTransactionAmountsForFinancialUpdate|
|InventMovement.addLedgerVoucherRevenueTransactionAmountsForPhysicalUpdate|
|InventMovement.addLedgerVoucherTransactionAmountsForFinancialUpdate|
|InventMovement.addLedgerVoucherTransactionAmountsForPhysicalUpdate|
|InventMovement.checkUpdatePhysical|
|InventMovement.processLedgerPhysicalAmountList|
|InventMovement.setAutoReserving|
|InventMovement.setCostAmountPhysical|
|InventMovement.updateLedgerAdjust|
|InventMovement.updateLedgerFinancial|
|InventOnhandReserve.updateReserveLot|
|InventUpd_Estimated|
|InventUpd_Estimated.updateFieldsChange|
|JmgPayEventsExport_Std.run|
|JmgStampJournalTable.approve|
|JmgStampJournalTable.transfer|
|LedgerAccrualTrans.post|
|LedgerAllocationBasisRules.createGeneralJournalAccountEntrySumQuery|
|LedgerAllocationController.allocateAmounts|
|LedgerAllocationProcessRequest.allocate|
|LedgerJournalCheckPost.checkJournal|
|LedgerJournalCheckPost.postJournal|
|LedgerJournalDistribute.createNewJournal|
|LedgerJournalEngine.calculateTaxForCompleteJournal|
|LedgerJournalEngine.initValue|
|LedgerJournalTable.deleteAllLines|
|LedgerJournalTrans.deleteTaxUncommitted|
|LedgerJournalTransDaily.LedgerJournalTrans.AmountCurCredit.validate|
|LedgerJournalTransDaily.LedgerJournalTrans.AmountCurDebit.validate|
|LedgerJournalTransType.validateVoucher|
|LedgerJournalTransUpdate.updateIntercompany|
|LedgerJournalTransVendPaym./Forms/LedgerJournalTransVendPaym/Design/ActionPane(ActionPane)/ButtonGroup(ButtonGroup)/buttonCreatePayment(MenuFunctionButton)/Clicked|
|LedgerTransListReportHelper.buildFieldMap|
|LedgerTransPerJournalDP.insertForLedgerBase|
|LedgerVoucherObject.checkBalance|
|LedgerVoucherObject.checkBalanceRound|
|LogisticsLocationFormHandler.callerResearch|
|LoyaltyCardBlance.MPOS_ExtensibleViews|
|Macros.InventSumFields|
|MainAccount.DimensionAttributeValue_ds/dimensionAttributeValueIsSuspended|
|NumberSeqModuleProject.loadModule|
|PcSourceDocumentLineUtility.initialize|
|PdsRebateFindAndCreate.findPdsRebateAgreementAndCreateClaim + run|
|PriceDisc.findPriceAgreement|
|PriceDisc.FindPriceAgreement.mcrPriceDiscTablefound|
|PriceDiscResultFields.NA|
|ProdJournalBOM.insertJournalCreate|
|ProjAdjustment.splitLine|
|ProjAdjustmentSplit.calculateQty|
|ProjAdjustmentSplit.getNewTotalSaleAmount|
|ProjAdjustmentUpdate.newPostAdjustment|
|ProjAdjustmentUpdate.run|
|ProjAdjustmentUpdate.transCostNew / transEmplNew / transItemNew methods|
|ProjAdjustmentUpdate.transItemNew|
|ProjAdjustmentUpdate.updateAdjusted|
|ProjBudgetImport.SourceType - modified|
|ProjBudgetRevision.updateGridHelper|
|ProjectPosting.getProjectLedgerDimension|
|ProjForecastEmpl.initValue|
|ProjFormletterParmData.updateQueryBuild|
|ProjGrant.canSubmitToWorkflow|
|ProjInvoiceChoose.doCost|
|ProjInvoiceChoose.doEmpl|
|ProjInvoiceChoose.doItem|
|ProjInvoiceChoose.doOnAccount|
|ProjInvoiceChoose.doRevenue|
|ProjInvoiceChoose.doSalesLine|
|ProjInvoiceChoose.psaAddEndDateToProposalJour|
|ProjInvoiceEditLines.Choose.clicked|
|ProjInvoiceEditLines.closeOk|
|ProjInvoiceProposalCreateLines.modifiedTransFilter|
|ProjInvoiceProposalCreateLines.run|
|ProjInvoiceProposalCreateLines.runSalesLineQuery|
|ProjInvoiceProposalInsertLines.doSalesLine|
|ProjInvoiceProposalInsertLines.setProjProposalJour|
|ProjInvoiceTable.createProposalJour|
|ProjLedgerUpdate.insert|
|ProjListTransDP.insertTmpTable|
|ProjPostItemPackingSlip .projTransCreate|
|ProjPostItemTransCost_Adj.projTransUpdate|
|ProjSplitBill.maxAllowedByLimits|
|ProjStatusTypeRule.enableRule|
|ProjTable.isCustomerTransferNeeded|
|ProjTableType.validateWrite|
|ProjValCheckTrans.validateMandatory|
|PsaProjAndContractInvoiceController.runPrintMgmt|
|PSAProjRetainerInvoicing.createTrans|
|PSAProjRetainerInvoicing.run|
|PurchAutoCreate_PurchReq.getPurchLineName|
|PurchAutoCreate_Sales.createLine|
|PurchCopying.updatePriceDiscLineChangePolicy|
|PurchCreateFromSalesOrder.run|
|PurchCreateOrder.PurchTable.write|
|PurchEditLines.Choose_Button.clicked|
|PurchEditLines.run|
|PurchFormLetter.prePromptInit|
|PurchFormLetter.reSelect|
|PurchFormLetter::main|
|PurchFormletterParmDataInvoice.reSelectLines|
|PurchInvoiceJournalCreate.allocateNumAndVoucher|
|PurchReqAddItem.N/A: Variable Change, not Method|
|PurchRFQCaseTable.isCalledFromPurchRFQCTListPageProject|
|PurchTable.ConvertCurrencyCode|
|PurchTable.create|
|PurchTable.create (PurchTable datasource)|
|PurchTableType.validateDelete|
|ReqCalc.actionCalcItem|
|ReqCalc.covCalcDim|
|ReqCalc.covCodeQtyMinMax|
|ReqCalc.covCreatePlannedOrder|
|ReqCalc.covCreateSafetyInvent|
|ReqCalc.createSafetyInvent|
|ReqCalc.createSafetyInventKey|
|ReqCalc.deleteTransactionAndCoverage|
|ReqCalc.setParameters|
|ReqCalc.writeInventSum|
|ReqTransCache.listCovDimSorted|
|ReqTransPoMarkFirm.create|
|RequisitionPurchaseOrderGeneration.updateEmptyVendAccountsForManualCreation|
|RequisitionPurchaseOrderGeneration.validatePurchReqLine|
|RetailInternalOrganization.insert|
|RetailKitAssemblyOrder.createOrUpdateBOMJournal|
|RetailKitAssemblyOrder.createOrUpdateBOMJournalLine|
|RetailStatementPost.postRetailSpecific|
|RetailStoresToDeploy.setAllowEditTrue|
|RetailTransactionSalesTransMark.findInventDimIdFromWorkingTable|
|RetailTransactionSalesTransMark.populateTransactionSalesLineWorkingTable|
|RetailTransactionServiceOrders.cancelCustomerOrder|
|RetailTransactionServiceOrders.createCustomerOrder|
|RetailTransactionServiceOrders.createLedgerJournalTransForPayment|
|RetailTransactionServiceOrders.createRetailOrderPayment|
|RetailTransactionServiceOrders.invoiceSalesOrder|
|RetailTransactionServiceOrders.settleCustomerOrder|
|SalesCopying.canClose|
|SalesCreateOrder.updateDeliveryAddress|
|SalesFormLetter.main|
|SalesFormLetter.mainOnServer|
|SalesFormLetter.reSelect|
|SalesInvoiceJournalCreateBase.createJournalHeader|
|SalesInvoiceJournalPostBase.postLine|
|SalesInvoiceJournalPostBase.updateInventory|
|SalesLine.createLinesFromTmpFrmVirtual|
|SalesLine.runPriceDiscPolicyDialog|
|SalesLineType_ProjectSales.canBeInvoiced|
|SalesPurchLine.setPriceAgreement|
|SalesPurchLineInterface.setPriceAgreement|
|SalesPurchLineInterface.setPriceDisc|
|SalesQuotationEditLinesForm method createParmLine|
|SalesQuotationListPageInteraction.linkActive|
|SalesQuotationProjLinkWizard.endUpdate|
|SalesQuotationTable.convertCurrencyCode|
|SalesQuotationTable.modified (SalesQuotationLine_ItemId form control)|
|SalesQuotationTableType.numberSeqFormHandlerQuotationId|
|SalesQuotationTransferToProject.createForecastOnAcc|
|SalesQuotationTransferToProject.createProject|
|SalesTable.convertCurrencyCode|
|SalesTable.modified|
|SalesTable.updateDeliveryAddress|
|SmaServiceFunctionLine.getFromDialog|
|smmBusRelTable.updateCustTable|
|smmBusRelTable.updateVendTable|
|SourceDocumentBalanceProvider.calculateEncumberedAmount|
|Table/MyAddressBook.xds|
|Table/TrvExpTrans.update|
|Tax.allocateInTaxWorkTrans|
|TaxCalculationJournal.saveTaxTransfer|
|TaxCashDisc.calcAndInsertTaxes|
|TaxData.find|
|TaxInventTransferInvoice_BR.post|
|TaxReversePrePayment.calcPostAndInsertTaxes|
|TaxReverseTax.insertTaxWorkTrans|
|TaxReverseTax.newTrans|
|TaxSettlement.retailCalcAndInsertTaxes|
|TaxWithHold.createTaxWithholdTrans|
|TaxWithhold.postTaxWithhold|
|TransactionReversal.updateTaxTrans|
|TransactionReversal_Vend.reversal|
|TransactionTxt.setKey1|
|TransactionTxt.setKey2|
|TransactionTxt.setKey3|
|TrvExpTrans.insertPerDiemDataLines|
|TrvPbsMainDataLines.clicked|
|TrvPostExpenseHeader.postCustVendTransactions|
|TSTimesheetTrans.getCostPrice|
|VendOutPaym_Cheque.generatePaymentLines|
|VendOutPaym_RBC.generatePaymentLines|
|VendOutPaymRecord_RBC_Credit.fillField03|
|VendOutPaymRecord_RBC_Credit.fillField07|
|WhsControlItemId.populate|
|WHSCycleCountCreatePlan.insertWorkLine|
|WHSLoadLineAllocationProcessor.validateBatchDisposition|
|WhsLoadLineUpdater.initLoadLine|
|WHSMobileAppServiceXMLTranslator.createXML|
|WHSPack.packFromScanningFields|
|WhsrfControlData.allowMixedBatch|
|WhsrfControlData.allowMixedItem|
|WHSRFControlData.processLegacyControl|
|WhsWorkExecuteDisplay.buildGetVendBatchDetails|
|WHSWorkExecuteDisplay.buildLPControlFromPass|
|WHSWorkExecuteDisplay.buildPORecTrackingDimensions|
|WHSWorkExecuteDisplay.buildRemainingReceiptQtyCurrentLPLabel|
|WHSWorkExecuteDisplay.buildTrackingDimensions|
|WHSWorkExecuteDisplay.processWorkLine|
|WHSWorkExecuteDisplay.setBatchDetails|
|WhsWorkExecuteDisplayClusterPicking.clusterCompleted|
|WhsWorkExecuteDisplayMenu.buildMenu|
|WHSWorkExecuteDisplayPOReceiving.displayForm|
|WHSWorkExecuteDisplayUserDirected.displayForm|
|WhsWorkExecuteDisplayWarehouseTransfer.displayForm|
|WrkCtrScheduler_Proj.insertOrder|


## Other changes

The following table lists additional changes that have been made for extensibility.

| Change |
| -------------|
- Create a SysQueryUpdateRecordSet class in AppCommon.
- Enable percent controlled for a catch weight item.




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]