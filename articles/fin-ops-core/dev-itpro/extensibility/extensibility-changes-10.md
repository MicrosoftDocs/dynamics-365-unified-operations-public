---
title: Extensibility changes in Dynamics 365 for Finance and Operations version 10.0
description: Learn about the extensibility features that were released in Dynamics 365 for Finance and Operations version 10.0.
author: FrankDahl
ms.author: fdahl
ms.topic: article
ms.date: 03/05/2019
ms.custom:
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2019-02-11
ms.dyn365.ops.version: App 10.0
---

# Extensibility changes in Dynamics 365 for Finance and Operations version 10.0

[!include [banner](../includes/banner.md)]


This is a list of extensibility features that were implemented in Dynamics 365 for Finance and Operations version 10.0. For more information about the schedule of changes that support extensibility, see [Application extensibility plans](extensibility-roadmap.md).

## Enumerations made extensible

These enumerations have been made extensible in this update.

| Enumeration|
| --------------- |
|AssetAccrualCalendar|
|AssetYear|
|BankReconciliationReportType|
|BudgetPlanColumnPeriodLength|
|BudgetPlanHCMReportGroupOption|
|CurrencyTypeBrief_RU|
|EInvoiceStatus_IT|
|EInvoiceStatus_IT|
|HRPAuthorityBasis|
|HuExchOutflowType|
|InventJournalTagStatus|
|InvoiceAssociationType|
|MCRClaimType|
|MCRMerchandisingEventCategory|
|PaymAttribute|
|PaymProposalReportedBy|
|PayrollCategory|
|projActualVsBudget|
|ProjListStateId|
|ProjTransLayout|
|ProjType|
|RCashCheckContract|
|RCashDocRepresType|
|RCashDocType|
|RCashRemainLimitType|
|RCashTableAll|
|RCashTransStatus|
|SMARelationType|
|smmActivityTaskTimeType|
|TaxIdType|
|TrvAirlineServiceClassEnum|
|TrvFieldVisibility|
|TSPeriodFrequency|
|TSPerWeekMth|
|VendPaymentValidate|

## SQL operations made extensible

These SQL operations have been made extensible in this update.

| Operation|
| --------------- |
|JmgStampJournalTable.makeLines|
|MCRDropShipStatusUpdate_PurchLine.updatePurchDropShipStatusOnRecord|
|MCRDropShipStatusUpdate_PurchTable.updatePurchDropShipStatusOnRecord|
|SalesInvoiceJournalCreate.checkDocumentData_PL|
|SalesInvoiceJournalPost.postFailed|

## Metadata changes

These metadata changes have been made in this update.

| Operation |
| --------------- |
|/Data Model/Data Entities/BOMBillOfMaterialsVersionV2Entity.IsPublic|
|/Data Model/Data Entities/InventItemBatchEntity.IsPublic|
|/Data Model/Data Entities/InventProductSpecificOrderSettingsV2Entity.IsPublic|
|/Data Model/Data Entities/InventQualityGroupItemAssignmentEntity.IsPublic|
|/Data Model/Data Entities/InventQualityTestGroupEntity.IsPublic|
|/Data Model/Data Entities/ProductionPoolEntity.IsPublic|
|/Data Model/Data Entities/WMSItemArrivalJournalHeaderEntity.IsPublic, PublicCollectionName, PublicEntityName|
|/DataModel/Tables/WMSStorageLoadUnitReqTrans.WMSStorageLoadUnitReqTran|
|DimensionHierarchyType/EnumValue/RDeferrals|
|AOT/Data Model/Tables/CategoryTable.Create RecId Index|
|EcoResProductCategoryHierarchyEntity.Property.IsPublic|
|EcoResProductSpecificUnitOfMeasureConversionEntity.Property.IsPublic|
|EcoResReleasedProductVariantExternalCodeEntity.Property.IsPublic|
|InventProductSpecificOrderSettingsV2Entity.Property.IsPublic|
|"No of Decimals is Extensible" property on several EDTs|
|RetailLoyaltyRewardPoint.Replacement Key|
|Tables/CustTrans/Relations/ThirdPartyBankAccountId.Validate|
|Tables/EInvoicePropertyTable/Relations/EInvoicePropertyTypeTable.RelationshipType|
|Tables/ResourceSetup.FormRef|
|Tables/WHSTmpWorkExecuteListBoxItems/Fields/Elements.EDT|

## Refactored methods

These methods have been refactored to support extensibility.

| Refactored methods                                                                             |
|------------------------------------------------------------------------------------------------|
|AdvancedLedgerEntryLine.setProjInvoiceLineLedgerDimension|
|AgreementConfirmationDP.getSalesAgreementHeader|
|AgreementConfirmationDP.getSalesAgreementHeaderHistory|
|PurchAutoCreate_Sales.createPurchLine|
|PurchCreateFromSalesOrder.run|
|InventItemPrice.insert|
|InventJournalTrans.setCostPrice|
|PurchLine.initFromReqPO|
|AssetBook.initDepreciationProfile|
|AssetDepreciationProfile.validateStraightLine|
|AssetProposalDepreciation.run|
|BankPaymAdvicePrint.BankPaymAdvicePrint (variable)|
|BankReconciliationMatchingMatchProcessor.constructMatch|
|BankReconMatchingMatchStmtReversalDoc.Multiple|
|BankStatementDocumentEntity.postGetStagingData|
|BankVoucher.post|
|BomCalcItemLine.mustExplodePrice|
|BOMCopyToProd.delete|
|BOMCreateDialog.promptCreateBOMDialog|
|BomRouteCopyJob.initFromItemId|
|BudgetPlanningConfiguration.displayYearOffset|
|BudgetPlanningConfiguration.updateColumnPeriodLengthValueLabel|
|CatVendorCatalogProductApproval.getApprovedProductForRetail|
|LedgerJournalTransType.validateAccountType|
|LedgerTransferOpening.processQuery|
|BankPositivePayExport.generatePositivePayFile|
|BankPositivePayExport.updateBankPositivePay|
|CaseSendEmail.getEmailMessage|
|ContactPerson.insert|
|CostSheetModeStrategyStaging.createCostSheetNodes|
|CreditCard.recordAuthorization|
|CreditCard.recordCapture|
|CreditCardPaymentJournal.createJournal|
|CreditCardPaymentJournal.Init|
|CreditCardPaymentJournal.run|
|CustAgingReportContract.Validate|
|CustAgingReportDP.CustAgingReportTmp|
|CustAgingReportDPclass.insertCustAgingReportTmp|
|CustAgingReportDPclass.setCustAgingReportTmpInReverse|
|CustBalanceList.insertIntoTmpAccountSumV2|
|CustBillOfExchangePostRemit.postSettlingStep|
|CustCollectionsSetTransactionStatusHelper.createActions|
|CustCustomerBaseEntity/CustCustomerEntity/CustCustomerV2Entity/CustCustomerV3Entity.processChangesForApproval|
|CustCustomerDetailEntity/CustCustomerDetailV2Entity.processChangesForApproval|
|CustInvoiceJour.setInvoiceAddress|
|CustInvoiceLine.getCustBillingCodeLedgerAccount|
|CustInvoiceLine.setProjInvoiceLineLedgerDimension|
|CustInvoiceLine.setProjInvoiceLineLedgerDimensionBase|
|CustInvoiceLine.shouldDefaultLedgerDimensionFromProject|
|CustOutPaymRecord_Cheque.checkValues|
|CustPostInvoiceJob.custPostInvoiceUpdate|
|CustVendAgingCalculation.process|
|CustVendChequeSlipTextCalculator.getChequeDocLength|
|CustVendChequeSlipTextCalculator.getMinimumSlipLines|
|CustVendChequeSlipTextCalculator.fillSlipText|
|CustVendChequeSlipTextCalculator.Property |
|CustVendEditTaxBranch_TH.init|
|CustVendOutPaym.getSumByCurrency|
|CustVendPaymInvoiceWithJournal.createJournal|
|CustVendPaymInvoiceWithJournal.createPayment|
|CustVendPaymProposal.resolvePaymAccountAndType|
|CustVendPaymProposalLine.paymTransactionAmountMST|
|CustVendPaymProposalTransferToJournal.getVoucherNum|
|CustVendReversePosting.restoreCustVendTransOpen|
|CustVendSettle.postDueToAndFromCreateTrans|
|CustVendSettle.postExchRateLedgerTrans|
|CustVendSettle.settleNow|
|CustVendSettle.updateCustTaxInvoice_TH|
|CustVendSumUpJournal.createTrans|
|CustVendSumUpJournal.createVoucher|
|CustVendTransreorg.end|
|CustVoucher.updateProjTransPosting|
|DimDerDistRuleProjectRevenueExt.processRegularTransactions|
|DimDerDistRuleProjectRevenueExt.processIntercompanyTransCustInvoice|
|DimDerDistRuleProjectRevenueExt.processIntercompanyTransExpense|
|DimDerDistRuleProjectRevenueExt.processIntercompanyTransTimesheet|
|DimDerJourRuleProjectTimesheetsExt.getDefaultDimensionAllocation|
|EcoResEnumerationAttributeTypeValue.createAttributeValuesFromEnum|
|EcoResProductReleaseForm.addProductsToRelease|
|EInvoice_IT.newCustInvoice|
|EInvoice_IT.newProjInvoice|
|EUSalesListReportingEngine.Construct|
|FiscalDocument_BR.lastIssueDateForSeries|
|FormletterJournalPost.docuRefCopyByRecId|
|ForecastSales.Update|
|HcmActionState.lookupReferenceActionTypeSetup|
|HcmWorker.init|
|HcmWorker.updateEmploymentControls|
|HcmWorkerActionHireCompletion.getHrmApplication|
|HcmWorkerTransition.createHcmEmployment|
|HRCCompGridView.initCompRecord|
|HRMCompFixedEmpl.enforcePayRateTolerance|
|HRPDefaultSigningLimitRule.insertFormDataSourceJobDetail|
|HRPDefaultSigningLimitRule.populateDetailGrid|
|HRPDefaultSigningLimitRule.SaveValidation|
|HRPDefaultSigningLimitRule.insertOrUpdateFormDataSource|
|HRPDefaultSigningLimitRuleCompensation.getSelectedCompensation|
|HRPDefaultSigningLimitRuleCompensation.getAvailableCompensation|
|HRPDefaultSigningLimitRuleCompensation.selectRecords|
|HRPDefaultSigningLimitRuleCompensation.unselectRecords|
|HrpWorkerLimit.getActiveDefaultSLRule, |
|HrpWorkerLimit.getDefaultSigningLimits|
|HrpWorkerLimit.getWorkerSigningLimit|
|HrpWorkerLimitr.getSigningLimitsIfRequestNotRequired|
|InterCompanyTransferInventDim.Entire class|
|InterCompanyTransferInventDim.transfer|
|InventBatch.update|
|InventCountCreate_Base.createInventJournalTrans|
|InventInventoryDimensionEntityFieldsMapping.resolveInventDim|
|InventMov_Jour_BOM.journalCheckTrans|
|InventMov_Jour_Loss_Project.checkAccountOperations|
|InventMov_Journal.journalSetItemId|
|InventMov_Statement.pdsCWRemainPhysical|
|InventMovement.performFinancialLedgerUpdate|
|InventProcessGuideAdjustInController.initialStepName|
|InventQualityManagementBlock.run|
|InventQualityManagementCreateHandler.purchFormLetterBeforeHelper|
|InventQualityOrderTableValidator.checkQty|
|InventSum.retrieveMatchingInventSumDeltaForTTSId()|
|InventTrackingRegisterTransForm.construct|
|InventTransAdjust.updateNow|
|InventTransferUpdReceive.updateInventTransferLine|
|InventTransWms_Register.updateInventFromMovementServer|
|InventUpd_ChildReference updateLess* methods|
|InventUpd_ChildReference.updateMoreIssue|
|InventUpd_Estimated.updateAutoDimMovement|
|InventUpd_Physical.UpdatePhysicalReturnedIssue|
|InventUpd_Physical.updatePhysicalReturnedReceipt|
|InventUpd_WHSReservation.continueInventTransUpdateReserveMoveLoop|
|InventUpdateOnhand.checkOnhand()|
|InventUpdateReserveMore.buildQueries|
|JmgMESDocuHandling.openFile|
|JmgProfiles.insertTimeGapsPlannedAbs|
|JmgStampJournalCalculate.run|
|JmgStampJournalTransfer.cancelExecute|
|JmgStampJournalTransfer.cancelExecute|
|LeanCost_Init.execute|
|LedgerAllocationController.allocateAmounts|
|LedgerAllocationProcessRequest.createVoucherDestinations|
|LedgerJournalCheckPost.replaceTmpVoucher|
|LedgerJournalDeleteTransaction.deleteLedgerJournalTransRelated|
|LedgerJournalEngine.currencyModified|
|LedgerJournalPeriodicCopy.journalVoucherCopy|
|LedgerJournalTrans.initForCurrency|
|LedgerJournalTrans.validateWrite_Server|
|LedgerTransModule.insertTransactionList|
|LedgerTrialBalanceContract.DataMemberAttribute|
|LedgerVoucherObject.allocateTransaction|
|LedgerAllocationController.allocateRecursive|
|MCRCheckHoldWB\Release.clicked|
|MCROrderEventSetup.find|
|MCRSalesOrderRecap.Control:SubmitButton.clicked|
|MCRSalesQuickQuote.Modified|
|MCRTmpPickingWorkbenchTrans.initFromSessionCriteria|
|MultilineString.POSDeveloperSupport|
|OriginalDocuments.insertDocument|
|PaymSchedCalc_Amount.createTransaction|
|PdsRebateFindAndCreate.findPdsRebateAgreementAndCreateClaim|
|PdsRebateFindAndCreate.findPdsRebateAgreementAndCreateClaim()|
|PdsRebatePaymentPost.insertRebateEntryForGrouping|
|PmfFormCtrl_BOM_BOMVersion.modifiedFormulaSize|
|PriceDiscAdmCheckPost.postJournal|
|ProdJournalCheckPostProd.postTransLedger|
|ProdJournalTransBOM.inventBatchId.validate|
|ProdMultiReportFinished.insert|
|ProdUPDCostEstimation.CreateProdBOM|
|ProdUpdReportFinished.updateBOMConsumption|
|ProdUpdStartUp.createJournals|
|ProjBegBalJournalTrans_CostSales.validateField, validateWrite|
|ProjBudgetManager.deleteBudgetLinesBeforeImportForRevs|
|ProjBudgetManager.getQuery|
|ProjBudgetRevisionManager.createBudgetLines|
|ProjBudgetTransactionManager.isOverrunAllowed|
|ProjectCommitmentFacade.updateProjectCommitmentsMap|
|ProjectMainAccDimensionListProvider.populateMainAccountDimensionList|
|ProjForecastBudgetCopy.do_Cost|
|ProjForecastBudgetCopy.do_empl|
|ProjForecastBudgetCopy.do_onAcc|
|ProjForecastBudgetCopy.do_sales|
|ProjGroupChange.checkPostedTrxAccounts|
|ProjIntercompanyCustomerInvoiceCreator.createInvoiceLine|
|ProjInvoiceJournalPost.postCustVend|
|ProjInvoiceJournalPost.validateNoTax|
|ProjInvoiceProposalInsertLines.run|
|ProjJournalTrans.validateWrite|
|ProjPlanVersionCopyHierarchy.addProjPlanVersionFields|
|ProjPlanVersionCopyHierarchy.insertProjPlanVersionRecords|
|ProjPlanVersionCopyHierarchy.ProjPlanVersionCopyHierarchy|
|ProjPlanVersionsManager.importProjPlanVersionRecords|
|ProjPost.PostNeverLedger|
|ProjPost.PostTurnover|
|ProjPosting.updateDatasourceRanges|
|ProjTable.validateWrite|
|ProjTable.validateWriteServer|
|ProjTask.addTask|
|ProjValSetupEmplProj.ProjValSetupEmplProj.AddResourceButton.Click|
|ProjWBSDataEntityHelper.postInsertOperation|
|PurchAutoCreate_ReleaseFromAgreement.createLines|
|PurchInvoiceJournalPost.calcLastPurchPrice|
|PurchPackingSlipJournalPost.updateSourceLineBeforePosting|
|PurchReqLine.defaultBuyingLegalEntity|
|PurchRFQCaseAutoCreate_PurchReq.calcRFQHeaderValues|
|PurchTable/InventDim/InventBatchId.modified|
|ReqTransPoMarkFirm.executeAction|
|ReqTransPOMarkFirm.CreateProdBOM|
|ReqTransPoMarkFirm.purchTablePostProcessing|
|ReqTransPoMarkFirm.setDeliveryDateAndPriceDisc|
|ReqTransPoMarkFirm.setGroupingIndicators|
|RequisitionPurchaseOrderGeneration.Create|
|RequisitionPurchaseOrderGeneration.createPurch|
|RequisitionPurchaseOrderGeneration.getVendors|
|ResReserveCapacity.getCapacityPercentage|
|RetailCreateLinesFromProductsToAdd.loadDiscountLines|
|RetailMassUpdateValidator.validateWriteOnInventModelGroupItem|
|RetailMediaAssociationHelper.populateMediaAssociationTable|
|RetailOENInfo.parseEmailTemplate|
|RetailPrintLabels.loadFromArgs|
|RetailPrintLabels.loadLines|
|RetailTransactionServiceOrders.createOrUpdateRetailOrderHeader|
|RetailTransactionServiceOrders.createOrUpdateRetailOrderLines|
|SalesConfirmJournalPost.createReportData|
|SalesFormLetter_Invoice.checkInvoicePrices|
|SalesInvoiceDP.setPackingSlipDetails|
|SalesInvoiceJournalPostBase.updateInventory|
|SalesInvoiceJournalPostBase.updateInventoryFinancialForSalesInvoiceLine|
|SalesLine.CheckItemId|
|SalesLine.getInventQtyFromCWUnit|
|SalesLine.setInventDeliverNow|
|SalesLineType.validateWrite|
|SalesQuotationDP.createTaxLines|
|SalesQuotationDP.itemId|
|SalesQuotationLine.PriceDate|
|SalesQuotationTable.active|
|SalesTable-DataSource_mcrSalesTable-DataField_SourceId.modified|
|ShipOrderForm.POS.ChangeOriginOnShipOrders|
|SmabomDesignerCtrl.listInsertHistory|
|SmabomDesignerCtrl.treeSubstituteBOMonNode, treeDeleteNode, treeDeleteChildrenCollect|
|SMAServiceObjectrelation.jumpRefBOMTable|
|SubledgerJournalizerProjectExtension.createProjectActualCostDetail|
|SubledgerJournalizerProjectExtension.createProjectActualSalesDetail|
|SubledgerJournalTransferCommand.insertGeneralJournalAccountEntryRelated|
|SubledgerJournalTransferCommand.insertGeneralJournalAccountEntryRelatedDetail|
|SubledgerJournalTransferCommand.insertGeneralJournalAccountEntryRelatedDetail|
|SubledgerJournalTransferCommand.insertGeneralJournalAccountEntryRelatedSummarized|
|SubledgerJournalTransferCommand.insertGeneralJournalAccountEntryRelatedSummarized|
|SubledgerJournalTransferCommand.insertGeneralJournalEntryRelated|
|SuppItem.calcSuppItem|
|TaxProformaSpec.parmTaxSpec|
|TaxWithhold.postTaxWithhold|
|TaxWithholdSlipDP_TH.createTaxWithholdSlipTmp|
|TaxWithholdSlipDP_TH.createTaxWithholdSlipTmp|
|TmsProcessXML_Base.readRateShipment|
|TMSRouteHelper.getShipDates|
|TradeLineNumberManager.checkLineNumber|
|TrvCreditCardReminder.mail |
|TrvCreditCardReminder.runQT|
|TrvExpenditureParticipantProvider.resolveFromDimensions|
|TrvExpenditureParticipantProvider.resolve|
|TrvExpenditureParticipantProvider.resolveProjectAuthorities|
|TrvExpenses.openSplitDetailsForm|
|TrvExpTable.validateSubmit|
|VendAgingReportController.getReportName|
|VendBalanceList.insertIntoTmpAccountSum|
|VendInvoiceInfoListPage.postInvoice|
|VendOutPaymRecord_Cheque.checkValues|
|VendVendorEntity/VendVendorV2Entity.processChangesForApproval|
|VestingID.Table: HRMCompVarAward|
|WhsContainerization.packTmpWorkLine|
|WhsControlBatchId.process|
|WHSPostPackingSlip.canShipConfirm|
|WHSPostPackingSlip.shipConfirmLoad|
|WHSProcessGuideStartChangeWarehouseStep.doExecute|
|WhsrfControlData.batchExistInLocation|
|WhsShipConfirm.tmsMultiLoadShipConfirm|
|WHSSplitWork.handleOrignalWorkLine|
|WHSSplitWork.handleRemainingPickTrans|
|WHSSplitWork.processRemainingTransaction|
|WHSSplitWork.updateClosedPickTrans|
|WhsUnShip.cleanUpTOInventTransDims|
|WhsWarehouseRelease.createShipmentsForTransferOrders|
|WHSWorkCreate.createWorkInventTrans|
|WHSWorkCreate.createWorkTable|
|WhsWorkCreateProdPut.createReportFinished|
|WhsWorkCreateReceiving.createBatch|
|WHSWorkExecute.putAwayToLocation()|
|WHSWorkExecuteDisplay.buildInventoryStatus|
|WhsWorkExecuteDisplay.getNextFormState|
|WhsWorkExecuteDisplay.processTrackingDimDetails|
|WhsWorkExecuteDisplay.processVendorBatchDetails|
|WhsWorkExecuteDisplay.processWorkLine|
|WHSWorkExecuteDisplay.setBatchDetails|
|WhsWorkExecuteDisplayLoadItemReceiving.buildPOReceiving|
|WHSWorkExecuteDisplayLPReceiving.generateItemInfoForReceiving|
|WhsWorkExecuteDisplayPOLineReceiving.buildPOReceiving|
|WhsWorkExecuteDisplayPOLineReceiving.buildPOReceiving|
|WhsWorkExecuteDisplayReportAsFinished.displayForm|
|WHSWorkTable.satisfyDemandWorkLine|
|WmsArrivalCreateJournal.createWMSJournalTransFromArrivalDetails|
|WmsJournalCheckPostReception.returnOrderUpdate|
|WmsOrderCreate.updateCreatewmsOrder|
|WorkflowHierarchyProviderHelperEventHandler.addDataSourceFieldsDelegate|
|WorkflowHierarchyProviderHelperEventHandler.loadLimits|
|WrkCtrScheduler_Prod.saveOperation|

## Other changes

The following additional changes have been made for extensibility.

- Convert queries where InventSumFields is used to SysDa.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
