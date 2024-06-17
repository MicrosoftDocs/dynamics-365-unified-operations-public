---
title: Extensibility changes in Dynamics 365 for Finance and Operations update 8.0.3
description: Learn about the extensibility features that were released in Dynamics 365 for Finance and Operations update 8.0.3.
author: FrankDahl
ms.author: fdahl
ms.topic: article
ms.date: 08/03/2018
ms.custom:
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2018-08-31
ms.dyn365.ops.version: App 8.0.3
---

# Extensibility changes in Dynamics 365 for Finance and Operations update 8.0.3

[!include [banner](../includes/banner.md)]

This is a list of extensibility features that were implemented in Dynamics 365 for Finance and Operations update 8.0.3. For more information about the schedule of changes that support extensibility, see [Application extensibility plans](extensibility-roadmap.md).

## Refactored methods to support extensibility

These methods have been refactored to support extensibility through chain of command, delegates, or by providing access to members.

| Method |
|---------------|
|AccountingSourceExplorerProcessor.filterEntries|
|AgreementClassification.init|
|AgreementConfirm.createLineVolumeCommittmentHistory|
|AgreementConfirm.newAgreementConfirm|
|Agreementline.findLineForAutoMatch|
|Agreementline.getAgreementLinesForOrderLine|
|AgreementLine.getAgreementLinesForPurchReqLine|
|Agreementline.getAgreementLinesList|
|Bank_FR.checkControlText|
|Bank_IT.checkCIN|
|Bank_IT.checkRegistrationNum|
|BankAccountTrans.insert|
|BankAccountTrans.update|
|BankChequeCopy.fillTmpChequePrintout|
|BankChequePrint.printDocument|
|BankPaymAdviceReportGeneratorVend|
|BankReconciliationMatchRuleLine.getFieldsOfSysGenMatchRuleLineOfDoc|
|BankReconciliationMatchRuleLine.getFieldsOfSysGenMatchRuleLineOfDoc|
|BankReconMatchingRuleAutoProcessor.getSearchedDocumentIdList|
|BankReconMatchingRuleAutoProcessor.getSearchedDocumentIdList|
|BankVoucher.createBankAccountTrans|
|BankVoucher.createBankAccountTrans|
|BomCopyToProd.copyTo|
|BudgetPlanLineFieldActiveViewMapping.getBudgetPlanLineFieldName|
|BudgetTransaction.openLinesInExcel|
|ChequeController.init|
|CustAccountStatementExt.main|
|CustAccountStatementExtController.includeOnStatement|
|CustAccountStatementExtController.insertCustAccountStatementExtTmp|
|CustAccountStatementExtController.setCommonData|
|CustAccountStatementExtController.tmpCustVendTrans|
|CustAccountStatementExtUIBuilder.build|
|CustAuditorDP.setCustAuditorTmp|
|CustCollectionJourDP.insertCustCollectionJourDP|
|CustCreditLimit.Balance|
|CustInterestNoteDp.processReport|
|CustInvoiceJour.printJournal|
|CustInvoiceTable.checkCreditLimit|
|CustPackingSlipJour.interCompanyUpdate|
|CustPaymEntry.updateConditionalControls|
|custPostInvoicejob.custPostInvoiceUpdate|
|CustTrans.reverseTransact|
|CustVendCheque.createBankChequePaymentTrans|
|CustVendCheque.createBankChequePaymentTrans|
|CustVendCheque.initTmpChequePrintout|
|CustVendCheque.output|
|CustVendCheque.output|
|CustVendChequeSlipTextCalculator.getChequeDocLength|
|CustVendSumForPaym.validateSEPATransaction|
|CustVendSumUpJournal.createTrans|
|CustVendVoucher.post|
|DimDerDistRuleProjectTimesheetsExt.populateDimAllocListIntercompany|
|DimDerJourRuleProjectTimesheetsExt.getDefaultDimensionAllocation|
|DirPartyVerification.selectionChanged|
|EcoResCategoryTreeDatasource.initializeAvailableCategoriesMap|
|EcoResProductCreate.writeMoreFields|
|EcoResProductDetailsExtended.initInventDimensionsMetadataEntries|
|ElectronicPaymentRemitExport_BR.construct|
|ForecastPuch|
|ForecastSales.accountConsumption|
|ForecastSales.accountDisc|
|ForecastSales.accountIssue|
|ForecastSales.accountSales|
|InventPosting.accountItemLedgerDimension|
|InventSupply.init|
|InventTrans.insertReturnTransOrigin|
|InventTransferParmLine - several methods|
|InventTransferUpd::updateLines|
|InventTransFormHelper.formQueryAddDynalink|
|InventTransWMS_Pick::updateInventServer|
|InventUpd_Physical::updatePhysicalReceiptTrans|
|InventUpdate.writeInventTrans|
|InventUpdate::createInventTransOriginAndReferences|
|InventValueReportPopulateItem::findReportLine|
|JmgRegistration.JmgJobTable|
|JournalizingDefinitionManager.newJournalizingDefinitionManagerPurch|
|JournalStatic.initializeDataModel|
|LedgerFinancialJournalReportDPBE.calcDebCredTotals|
|LedgerFinancialJournalReportDPBE.processReport|
|LedgerJournalDP.insertJournalTransForLedgerJournalTable|
|LedgerJournalDP.insertLedgerJournalTmp|
|LedgerJournalEngine.newJournalActive|
|LedgerJournalTrans checkAllowPosting|
|LedgerJournalTransUpdateBank.setBankVoucherSource|
|LedgerJournalTransUpdateBank.updateNow|
|LedgerJournalTransUpdateBankLC.addBankVoucher|
|LedgerPostingGeneralJournalController.transferLines|
|LedgerPurchaseJournalReportDPBE.insertIntoTempTable|
|LedgerSalesJournalReportDPBE.processReport|
|LedgerTransFurtherPosting.createLedgerJournalTransFromGenJour|
|LedgerTransVoucher.getSubledgerVoucherLinkDataSource|
|LedgerTransVoucher.getSubledgerVoucherLinkDataSource|
|LedgerTransVoucher.getVoucherDateRange|
|LedgerVoucherObject.updateLedgerPostingJournal|
|LedgerVoucherTransObject.checkRounding|
|Markup.insertMarkupTrans|
|MarkupTrans.MarkupTable.MarkupCode.Lookup|
|PaymSchedCalc::init*|
|PaymSchedCalc_Line::createTransaction|
|PdsApprovedVendorListCheck.newBasedOnTableType|
|PmfFormulaCoBy.run|
|PmfFormulaCoBy.ValidateField|
|PmfProdCoBy.ValidateField|
|PmfProdCoBy.ValidateWrite|
|PriceDiscAdmSearch|
|PriceDiscPolicyDialog.runPolicyDialog|
|ProdBOM.checkIsItemsReleased|
|ProdBOM::update|
|ProdJournalProd.Insert|
|ProdPurch.createPurchTable|
|ProdUpdHistoricalCost_Process.checkValidCoBy|
|ProdUpdReportFinished::updateBOMConsumption|
|ProdUpdStartUp,getListOfBOMJournals|
|ProdUpdStatusDecrease_StartUp.reverseBOMStartUp|
|ProjBudgetParticipantProvider.resolveByProject|
|ProjBudgetParticipantProvider.resolveByProjectHierarchy|
|ProjBudgetParticipantProvider.resolveByRootProject|
|ProjCaseActivitiesHandler.smmActivities_onValidatedDelete|
|ProjControlPeriod.forecast|
|ProjControlPeriod.forecast|
|ProjControlPeriodCostGroup.totalBudgetMinusActual|
|ProjControlPeriodCostGroup.totalBudgetMinusActual|
|ProjectPosting.costLedgerDimension.|
|ProjectPosting.getProjectLedgerDimension.|
|ProjForecastEmpl.initValue|
|ProjForecastReduceHour.constructQuery|
|ProjFundingSource.setInvoiceLocation|
|ProjGroup.initFromProjType|
|ProjIntercompanyCustomerInvoiceCreator.createInvoiceLine|
|ProjIntercompanyTransactionSelection.runQuery|
|ProjIntercompanyTransQuery.buildExpenseQuery|
|ProjIntercompanyTransQuery.buildHoursQuery|
|ProjIntercompanyTransQuery.buildVendorInvoiceLinesQuery|
|ProjInventJournalTransMapForm.checkActivity|
|projInvoiceChooose.setProposalJour|
|ProjInvoiceChoose.doRevenue|
|ProjInvoiceChoose.updateInvoiceTotal|
|ProjInvoiceProposalCreateLines.isRevenueTrans|
|ProjInvoiceProposalCreateLinesBase.createProposalTrans|
|ProjInvoiceProposalCreateLinesBase.doOnAccount|
|ProjInvoiceTable|
|ProjLedger.classdeclaration|
|ProjPostItemJournal.projTransCreate|
|ProjProjectsListPage.CtrlStages|
|ProjProjectsListPageInteraction.enableButton|
|ProjProjectsListPageInteraction.showButton|
|ProjStatusUpd.main|
|ProjStatusUpd.new|
|ProjTable - ProjTable datasource.write|
|ProjTable.clicked|
|ProjTable.editSubProj|
|ProjTable.editSubProj|
|ProjTableCreate.close|
|ProjTableCreate.run|
|ProjTableCreate.write|
|ProjTableCreate.write|
|ProjTableLookup.ProjProjectLookup.init|
|PSAProjInvoiceDP.insertPSAProjInvoiceHeaderTmp|
|PSAProjInvoiceTaxTmp.insertPSAProjInvoiceTmpForTax|
|PsaProjProposalSelection|
|PurchAgreementAutoCreate::construct|
|PurchAutoCreate.setPurchTable|
|PurchAutoCreate_PurchReq.initializeAndCreatePurchLine|
|PurchAutoCreate_PurchReq.initializeAndCreatePurchLine|
|PurchAutoCreate_ReleaseFromAgreement.updateFinDimFromAgreemHeader|
|PurchCreateFromSalesOrder.shouldCreatePurchOrder|
|PurchFormLetter::main|
|PurchFormLetter::main|
|PurchFormletterParmDataPackingSlip::reSelectLines|
|PurchFormletterParmDataPackingSlip::selectChooseLines|
|PurchFormletterParmDataPurchOrder::selectChooseLines|
|PurchInvoiceJournalPost.checkBeforePostingLine |
|PurchInvoiceJournalPost.updateSourceLine |
|Purchline.createline|
|PurchOrderLineBudgetControlPolicy.canCheckBudget|
|PurchReceiptsListDP.setPurchReceiptsListDetailsTmp|
|PurchReceiptsListDP.setPurchReceiptsListHeaderTmp|
|PurchRFQAcceptJournalPost.updatePurchReq|
|ReqCalc.covCalcDim|
|ReqTrans.createTransferDemand|
|ReqTransPoMarkFirm.createProdRoute|
|RetailPeriodicDiscount.ClassDeclaration|
|RetailTransactionServiceOrders.cancelCustomerOrder|
|Return.ReturnDispositionCodeId::validate|
|SalesAutoCreate::construct|
|SalesFormLetter.mainOnServer|
|SalesFormLetter.mainOnServer|
|SalesFormLetter::main|
|SalesFormletterParmDataConfirm::selectChooseLines|
|SalesFormletterParmDataInvoice::mayJournalTransBePosted|
|SalesFormletterParmDataInvoice::selectChooseLines|
|SalesFormletterParmDataPackingslip::selectChooseLines|
|SalesInvoiceDP.insertIntoSalesInvoiceTmp,insertIntoSalesInvoiceHeaderFooterTmp|
|SalesInvoiceJournalCreate.createJournalLine|
|SalesLine.CheckItemId|
|SalesLine.ValidateWrite_Server|
|SalesLine::calcLineAvailQty|
|SalesLine::createFromTmpFrmVirtualIL|
|SalesLineType.SalesLineType|
|SalesPackingSlipDP.setSalesPackingSlipDetailsTmp|
|SalesPackingSlipDP.setSalesPackingSlipHeaderTmp|
|SalesPackingSlipDP.setSysDocuBrandDetailsRegular|
|SalesPackingSlipDP.setSysDocuBrandDetailsRegular|
|SalesPackingSlipJournalPost.updateInventory|
|SalesQuotationLineType_Proj.validateProjTransTypeItem|
|SalesQuotationProjTable data source SalesQuotationline|
|SalesQuotationTableForm.createABSFromTemplate|
|SalesTable.setLocation|
|SalesTable2LineUpdate.update|
|SalesTable2LineUpdate.update|
|SalesTable2LineUpdatePrompt.initpriceDiscUpdateTriggers|
|smmActivitiesEventHandler|
|SuppitemTable Table Cache Lookup property|
|Table PurchPrepayTable.updateAdvanceApplicationRemaining|
|TransactionReversal_Cust.reversal|
|TransactionReversal_Cust.reversal|
|TransactionReversal_Vend.reversal|
|TransactionReversal_Vend.reversal|
|TransactionReversal_Vend.reversal|
|TsTimesheetAddFavorites.addToFavorites|
|TsTimesheetCreate.createTimesheetLine|
|TSTimesheetEntry.initFields|
|TSTimesheetFavorites.createTimesheetLines|
|TSTimesheetLine.setCategoryIdFromActivity|
|VendInvoiceDocumentDP.insertVendInvoiceDocumentTmp|
|WHSLoadLine.validateStatus|
|WHSLoadLineAllocationProcessor.allocateLoadLine|
|WHSPostEngine.validateAnyDimAboveLocationMissing|
|WhsWarehouseRelease.createShipmentsForAllSalesOrders|
|WhsWarehouseRelease.createShipmentsForTransferOrders|
|WhsWorkCreateLP.createTempTable|
|WHSWorkCreateProdPut.createTempTable|
|WHSWorkExecuteDisplay.buildNextDimensionCaptureControl|
|WHSWorkLine::cancelLine|
|WmsArrivalCreateJournal::createWMSJournalTransFromTmp|
|WmsArrivalOverviewGeneration::updateOverviewInformation|
|WmsJournalCheckPostReception::initJournal|
|WMSOrderTrans::adjustQtyWMSOrderTrans|
|WMSOrderTrans::createNewWMSOrderTrans|
|WMSOrderTrans::insertOrUpdate|
|WMSOrderTrans::updateWMSOrderTrans|
|WmsPickingList_OrderPickDP.insertIntoTempTable,setWMSPickingList_OrderPickTmpTemplate|
|WmsPickingList_OrderPickDP.setWMSPickingList_OrderPickTmpTemplate|
|WrkCtrlScheduler_Proj.loadJob|
|WrkCtrScheduler_Prod.saveOperation|
|WrkCtrScheduler_Prod.saveOrder|

## Enumerations made extensible

These enumerations have been made extensible in this update.

| Enumeration|
| --------------- |
|BankReconMatchRuleLineSysGeneratedType|
|BankReconMatchRuleLineSysGeneratedType|
|BankReconMatchRuleLineSysGeneratedType|
|ItemNumAlternative|
|JmgRegistrationErrorMode|
|MCRCustSearchType|
|ModuleSalesPurch|
|ModuleSalesPurch|
|ProjStatusRule|
|PurchRFQUpdateType|
|TAMVendRebateItemCode|
|TMSLoadBuildSupplyDemandType|


## Additional extensibility enhancements

In addition to the refactored methods, the following extensibility enhancements have been made.

- Increase EDT string size for EcoResProductSearchName
- Change CacheLookup property to NotInTTS for AssetLedgerAccounts
- Change CacheLookup property to Found on TaxOnItem, TaxJurisdiction, TaxGroupData, and TaxData, and AssetLedgerAcounts


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
