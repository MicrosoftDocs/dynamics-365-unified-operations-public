---

# required metadata
title: Extensibility changes in the Finance and Operations version 8.0
description: This is a list of extensibility features that were implemented in Dynamics 365 for Finance and Operations version 8.0.
author: FrankDahl
ms.date: 04/13/2018
ms.topic: index-page
ms.prod: 
ms.technology: 

# optional metadata
# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
ms.custom: 268724
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: fdahl
ms.search.validFrom: 2018-04-04
ms.dyn365.ops.version: Platform update 15

---

# Extensibility changes in the Finance and Operations version 8.0

[!include[banner](../includes/banner.md)]

## Hard-sealed application models

In Dynamics 365 for Finance and Operations version 8.0, all of Microsoft's application models have been hard-sealed. Overlayered code in these models will now produce compilation errors. The only supported customization model is through extensions. If you cannot customize these models through extension, then you will have to make a request to Microsoft to enable extensibility by changing the standard application.

The following table includes a list of models that are now hard-sealed with this release.

| Module | Model         |
| --------------- |-------------|
|ApplicationCommon | ApplicationCommon |
|ApplicationSuite | Electronic Reporting Application Suite Integration |
|ApplicationSuite | Foundation Upgrade |
|ApplicationSuite | Foundation |
|ApplicationSuite | SCMControls |
|ApplicationSuite | Tax Books Application Suite Integration |
|ApplicationSuite | Tax Engine Application Suite Integration |
|CaseManagement | CaseManagement |
|Currency | Currency |
|DataImpExpApplication | DataImpExpApplication |
|DataUpgrade | DataUpgrade |
|Directory | Directory |
|Directory | SecurityReports |
|GeneralLedger | GeneralLedger |
|Ledger | Ledger |
|PersonnelManagement | PersonnelManagement |
|ProcessGuide | ProcessGuide |
|Retail | Retail |
|SourceDocumentation | SourceDocumentation |
|SourceDocumentationTypes | SourceDocumentationTypes |
|Subledger | Subledger |
|Tax | Tax |

## Enumerations that have been made extensible

The following changes were made to support extending enumerations:
- Many enumerations in the standard application have been made extensible. An enumeration is made extensible by setting two properties on the enumeration. The **IsExtensible** property is set to **Yes**, and the **UseEnumValue** property is set to **No**. 
- Some enumerations represent state. New façade methods have been added to help enable adding enumeration values by extension. For information about how to extend an enumeration, see [Add values to enums through extension](add-enum-value.md).
- Some application code that uses enumerations was changed to support extensibility. Common changes include:
    + Removing **throw** exception statements in the default case of a switch to allow post-event subscription.
    + Adding **SysExtension** support for extension.
    + Adding explicit delegates.

| Enumeration|
| --------------- |
|BOMConsumpType|
|BOMFormula|
|BOMType|
|ChequeFormType|
|CostGroupType|
|CustAccountStatement|
|CustMandateScheme|
|CustVendDisputeStatus|
|DispositionAction|
|ItemCalcType|
|KMCollectionAnswerStatus|
|KanbanEventType|
|LedgerAccrualPeriod|
|LogisticsAddressElement|
|LogisticsLocationEntityType|
|NoneBeginTransEnd|
|PSAInvoiceFormats|
|PdsCumulationPeriod|
|PdsRebateProgramType|
|PdsRebateTransaction|
|PdsUnitType|
|PriceDiscSystemSource|
|ProdFlushingPrincipBOM|
|ProdFlushingPrincipItem|
|ProdReservation|
|ProjAccountTypeCost|
|ProjAccountTypeSales|
|ProjAccountType|
|ProjJournalType|
|RevenueContributionMargin|
|SMATransactionType|
|SysPolicyRuleEnum|
|SysPolicyRuleTypeEnum|
|SysPolicyTypeEnum|
|TAMRebateAmtType|
|TAMVendRebateStatus|
|TMSRecordType|
|Voided|
|WMSJointShippingType|
|WMSReferenceType|

## Data manipulation methods that do not raise DataEvents or missing insert, update, delete pre- and post-data events

As a general practice, you use data methods on tables to raise events that can be used for extending the application. The code base has not always followed this practice. For example, the **doInsert**, **doUpdate**, and **doDelete** data methods and certain table implementations did not make a call to **super()** in the data method.

The **insert**, **update**, and **delete** methods on the type classes have been refactored. Changes were made so that **super()** is called more consistently in data methods. These changes enable extensions to be added to these methods, so that pre- and post-events are now available for extension. The tables where the **insert**, **update**, and **delete** events were enabled for extension are listed in the following table.

| Type, name, data source, and method |
| ----------------------|
|Form ProjTableCreate.ProjTable.write|
|Form ReturnTable.ReturnTable.leaveRecord|
|Form SalesQuotationProjTable.SalesQuotationTable.leaveRecord|
|Form SalesQuotationTable.SalesQuotationTable.leaveRecord|
|Form SalesTable.SalesTable.leaveRecord|

## Refactored methods to support extensibility

These methods have been refactored to support extensibility through chain of command, delegates, or by providing access to members.

| Type, name, and method |
| ----------------------|
|Class AgreementConfirm_Sales.startConfirm|
|Class AssetChangeGroup.updateAssetGroupInfo|
|Class AssetPost.createAssetTransForPost|
|Class AssetSplit.getUpdatedSplitValueModel|
|Class AssetTableMethod.init|
|Class AssetTableMethod_SL.calc|
|Class AxSalesLine|
|Class BankPaymCancel.serverRun|
|Class BomSearch.New|
|Class BomSearch_BOMCopyType.New|
|Class Commission.run|
|Class CostSheetPanel.build|
|Class CreateInvoiceJournalPost.createFixedAsset|
|Class CustAccountStatementIntDP.printingAmountMST|
|Class CustCreditLimit.balanceEstimate|
|Class CustCreditLimit.calculateBalance|
|Class CustCreditLimit_SalesTable.New|
|Class CustInterestCreate|
|Class CustVoucher.post|
|Class DimensionDerivationRule.buildDimensionCombination|
|Class EcoResProductInformation.main|
|Class EcoResProductReleaseManager.setAndSaveRetailProductProperties|
|Class EcoResProductValidator.isEssentialFieldValuesSet|
|Class FormLetterServiceController.newFromContract|
|Class FormletterJournalPost.postLineDiscount|
|Class Graphics_WrkCtrCapBooking.insertLoad|
|Class Graphics_WrkCtrCapBooking.loadGroupReservations|
|Class Graphics_WrkCtrCapBooking.loadNumReservations|
|Class InterCompanyPostPurch.construct|
|Class InterCompanySyncPurchLineType|
|Class InterCompanySyncPurchTableType.setSalesTableData|
|Class InterCompanySyncPurchTableType|
|Class InventAgeDimDP.createOrMergeInventAgeDimTmp|
|Class InventAgeDimDP.insertOrMergeInventAgeDimTmp|
|Class InventAgingCmdAggregateSelected.execute|
|Class InventCostItemDim.initInventSettlement|
|Class InventCostReport.newInventCostReport_CostBaseType|
|Class InventCountCreateItems.run|
|Class InventDimCtrl_Frm.clearInvisibleRanges|
|Class InventItemPriceActivationTaskActivateSim.activateOneInventItemPriceSim|
|Class InventItemPriceSim.moveSimulatedToCurrent|
|Class InventLedgerPostingDefinitionEntityHelper.inventAccountTypeX2InventAccountType|
|Class InventMov_SalesQuotation.isQuotationQtyEditable|
|Class InventProductDimensionLookup.dimEDT2FieldId|
|Class InventProductDimension|
|Class InventQualityManagementBlock.actOnAssociations|
|Class InventQualityManagementCreate.createOnRegistration|
|Class InventQualityManagementCreate.createQualityOrder|
|Class InventQualityManagementCreate.generateQualityOrders|
|Class InventQualityManagementCreateInvent.generateQualityOrdersWithDiscrimination|
|Class InventQualityMgmtCreateNonInvent.generateQualityOrdersWithDiscrimination|
|Class InventQualityOrderReopen.main|
|Class InventQualityOrderReopen.run|
|Class InventQualityOrderValidate.main|
|Class InventQualityOrderValidate.run|
|Class InventQualityReferenceTypeSales.isEligibleForQualityManagement|
|Class InventQualityReferenceTypeSales.supportsInventoryBlocking|
|Class InventQualitymanagementCreate.createPerQualityAssociations|
|Class InventSumReCalcItem.updateActualInventSum|
|Class InventTestAssociationTable.checkAccountRelation|
|Class InventTestAssociationTable.initRecord|
|Class InventTrackingDimTracingCriteria.initFromArgs|
|Class InventTransLine.insert|
|Class InventTransferMulti.run|
|Class InventTransferMultiReceive::main|
|Class InventTransferMultiShip.buildParmFromWMSShipment|
|Class InventTransferMultiShip.runUpdate|
|Class InventTransferOrderOverviewDP.insertTmpTable|
|Class InventTransferUpdShip.updateInventTransferLine|
|Class InventUpd_Physical.updatePhysicalIssue|
|Class InventUpd_Physical.updatePhysicalReturnedReceipt|
|Class InventUpd_Picked.updatePickInventTrans|
|Class InventUpd_Reservation.whsUpdateReserveMore|
|Class InventUpdate.raiseOnHandChangingOnPhysicalStatusUpd|
|Class InventUpdate.updateDimReservePhysical|
|Class InventUpdate.updateTransDimTransferReceipt|
|Class InventUpdate.writeInventTransAutoDim|
|Class InventValueReportDP.processInventValueReportTmpLine|
|Class InventoryMainAccDimensionListProvider.populateMainAccountDimensionList|
|Class LedgerBalanceQueryGeneralJournal.addToBalanceTotals|
|Class LedgerBalanceQueryGeneralJournal.createQuery|
|Class LedgerJournalCheckPost.checkJournal|
|Class LedgerJournalCheckPost.postJournal|
|Class LedgerJournalDP.insertJournalTransForLedgerJournalTable|
|Class LedgerJournalDP.insertLedgerJournalTmp|
|Class LedgerJournalGetTrans.createLedgerJournalTrans|
|Class LedgerVoucherObject.addTrans|
|Class LedgerVoucherTransObject.check|
|Class LogisticsLocationSelectForm.construct|
|Class LogisticsLocationSelectForm.main|
|Class LogisticsPostalAddressFormHandlerExt.onNewParameters_delegate|
|Class MCRItemListGeneration.generateItemListLines|
|Class MCRItemListGeneration.generateItemListLines|
|Class MCRMarginAlert.skipMarginCalc|
|Class Markup.mcrDeleteNonUser|
|Class MarkupAllocationSelectionManager.setQueryRanges|
|Class PSAProjInvoiceDP.insertPSAProjInvoiceTmp|
|Class PSAProjInvoiceDP.insertProformaPSAProjInvoiceTmp |
|Class PdsApprovedVendorListCheck.newBasedOnTableType|
|Class PlanActivityTimeCalculation.calculatePlanActivityTime|
|Class PordJournalCreateBOM.createLinesProdBOM|
|Class PriceDisc.accountRelation|
|Class PriceDisc.findDiscAgreement|
|Class PriceDisc.findDisc|
|Class PriceDisc.findPriceAgreement|
|Class PriceTypeConverter.priceTypeToPriceGroupType|
|Class PrintMgmtReportFormatSubscriber.add|
|Class PrintMgmtReportFormatSubscriber.populate|
|Class ProdBOM.prodFlushingPrincipItem2BOM|
|Class ProdJournalCreateBOM.createLinesInventTrans|
|Class ProdJournalCreateBOM.createLinesInventTrans|
|Class ProdJournalCreateBOM.createLinesProdBOM|
|Class ProdJournalCreateBOM.dialog|
|Class ProdJournalCreateBOM.validate|
|Class ProdJournalFormTransBOM.setupCWFormControl|
|Class ProdPickListController.prePromptModifyContract|
|Class ProdPicklistDP.insertValues|
|Class ProdStatusType_Released.checkPostJournal|
|Class ProdTableListPageInteraction.getEnabledControls|
|Class ProdUpdReportFinished.updateBomConsumption|
|Class ProdUpdReportFinished.updateRouteConsumption|
|Class ProdUpdSplit.createSplitToProduction|
|Class ProdUpdStartUp.getListOfBOMJournals|
|Class ProdUpdStartUp.updateBOMConsmption|
|Class ProjInvoiceDP.insertIntoProjInvoiceTmp|
|Class ProjInvoiceProposalInsertLines.run|
|Class ProjInvoiceProposalInsertLines::run()|
|Class ProjPlanVersionsManager|
|Class ProjPostItemJournal::projTransCreate|
|Class ProjProposalTotals.calc|
|Class PsaProjInvoiceDP::insertProformaPSAProjInvoiceTmp|
|Class PsacustomerRetention.createFeeTransactionForProposal|
|Class PurchAgreementGenerateReleaseOrder.check|
|Class PurchAgreementGenerateReleaseOrder.validatePurchLinesWithPurchQty|
|Class PurchAutoCreate.construct|
|Class PurchAutoCreate.construct|
|Class PurchAutoCreate_RFQ.construct|
|Class PurchAutoCreate_SalesProjectItemReq.createLine|
|Class PurchAutoCreate_SalesProjectItemReq.createPurchLine|
|Class PurchCancel.parmPurchTable|
|Class PurchCancel.run|
|Class PurchCopying.deleteLines|
|Class PurchCreateFromSalesOrder|
|Class PurchFormLetterParmData.createParmLine|
|Class PurchFormLetterParmDataInvoice.createParmLineAndSubLines|
|Class PurchFormletterParmData.reSelectLines|
|Class PurchFormletterParmDataApproveJournal.updateQueryBuild|
|Class PurchFormletterParmDataInvoice|
|Class PurchInvoiceCreate.createJournalLine|
|Class PurchInvoiceJournalCreate.checkInvoicePolicies|
|Class PurchInvoiceJournalCreate.checkMatching|
|Class PurchInvoiceJournalPost.createFixedAsset|
|Class PurchInvoiceJournalPost.lateMatchPackingSlip|
|Class PurchLineType.validateWrite|
|Class PurchLineVersioningFieldSet.isChangeConfirmationRequired|
|Class PurchOrderLineSourceDocumentLineItem.calculateSourceDocumentAmountMap|
|Class PurchOrderLineSourceDocumentLineItem.calculateSourceDocumentAmountMap|
|Class PurchOrderLineSourceDocumentLineItem.calculateSourceDocumentAmountMap|
|Class PurchPackingSlipDP.createProductReceiptLines|
|Class PurchPackingSlipJournalPost.selectFormletterJournalTrans|
|Class PurchRFQCaseAutoCreate.newAutoCreate|
|Class PurchReApprovalPolicyRuleFieldList.addTable2Hierarchy|
|Class PurchReApprovalPolicyRuleFieldList.addTable2Hierarchy|
|Class PurchSelectLinesManager.passSets|
|Class PurchTableInteraction.enableHeaderPurchase|
|Class PurchTableInteractionHelper.getJournalEnquiryButtons|
|Class PurchTableInteractionHelper.getUpdateJournalButtons|
|Class PurchaseOrderResponseConsume.checkIfPurchLinesRequireUpdate|
|Class PurchaseOrderResponseConsume.checkIfResponseLineCannotBeConsumedAndUpdateConsumptionState|
|Class PurchaseOrderResponseConsume.consumeFirstPurchaseOrderResponeLineAndInitiateArchivingOnPurchLine|
|Class PurchaseOrderResponseConsume.consumeRemainingPurchaseOrderResponseLines|
|Class PurchaseOrderResponseConsumeLine.checkIfSelectedPurchLinesRequireUpdate|
|Class ReqCalc.covCodeQty|
|Class ReqCalc.insertItemInventSum|
|Class ReqCalc.insertItemInventTrans|
|Class ReqTransFormPo.validateFromInventLocationId|
|Class ReqTransPoMarkChangeToRFQ.DialogPostRun|
|Class ReqTransPoMarkFirm.createPurchLine|
|Class ReqTransPoMarkFirm.setPurchTable|
|Class RetailAssortmentLookupTask.explodeAssortments|
|Class RetailCreateLinesFromProductsToAdd.createPeriodicDiscount|
|Class RetailCreateLinesFromProductsToAdd.loadLines|
|Class RetailPackagePurchManagement.createLines|
|Class RetailProductPropertyManager.saveInventTableAndRelated|
|Class RetailProductPropertyManager.validateWriteOnInventTable|
|Class RetailSalesOrderCalculator.saveSalesOrder|
|Class RetailSalesOrderCalculator.setPriceOnCurrentLine|
|Class RetailSalesQuotationCalculator.saveSalesQuote|
|Class RetailSalesQuotationCalculator.setPricesOnCurrentLine|
|Class ReturnTableInteraction.enableControl|
|Class RouteCopyToRoute.insertRouteOpr|
|Class SMAServiceFunctionLine_Transfer.checkJournalType|
|Class SMAServiceFunctionLine_Transfer.postJournalType|
|Class SMAServiceFunctionLine_Transfer.sumjournals|
|Class SMAServiceOrderCreate.createServiceOrderLine|
|Class SalesAutoCreate_ReleaseFromAgreement.createSalesTable|
|Class SalesCancelOrder.run|
|Class SalesCopying.copy|
|Class SalesCreateOrderFromCutomer.main|
|Class SalesFormLetter.mainOnServer|
|Class SalesFormLetterParmData.createParmLine|
|Class SalesFormLetterReport.construct|
|Class SalesFormletterParmData.reSelectLines|
|Class SalesFormletterParmDataInvoice.reSelectInit|
|Class SalesInvoiceDP.invoiceTxt|
|Class SalesInvoiceDP.itemId|
|Class SalesLineCopyFromSource.updateCopiedLine|
|Class SalesLineType.setReservation|
|Class SalesLineType.setSalesStatus|
|Class SalesLineType.syncPurchLine|
|Class SalesPackingSlipDP.createSalesPackingSlipLines|
|Class SalesPackingSlipJournalPost.addToInventReportDimHistory|
|Class SalesPurchLineInterface.setPriceAgreement|
|Class SalesQuotationCopying.copyHeader|
|Class SalesQuotationEditLinesForm_Sales_Confir.createSalesTable|
|Class SalesQuotationEditLinesForm|
|Class SalesQuotationLineType_Sales.validateWrite|
|Class SalesTableListPageInteraction.setButtonInterCompany|
|Class SalesTableType.checkUpdate|
|Class SalesTableType.interCompanyMirror|
|Class SmmCampaignQueries|
|Class SmmLeadUpdate|
|Class SmmOpportunityLink|
|Class SmmUpdateBusRel.updateFromCustTableSFA2|
|Class TradeCurrencyConversionPrompt.construct|
|Class TradeLineRenumbering.renumber|
|Class TradeTotals.calc|
|Class VendDocumentLineInterface.setPurchaseQty|
|Class VendInvoicePolicyValidation.policyViolationMessage|
|Class VendProvisionalBalanceDP.processReport|
|Class WHSPool.pickFromWorkCenter|
|Class WHSShipConfirm.createUOMStructure|
|Class WHSWorkExecute.pickLicensePlateHandledByLP|
|Class WhsInventOnHandReserve.changeReservation|
|Class WhsInventOnHandReserve.setMovement|
|Class WhsPackForm.buttonPack_clicked|
|Class WhsPostEngineBase.createLoadFromShipment|
|Class WhsShipConfirm.createInventTransferParmLineTMS|
|Class WhsShipConfirm.createInventTransferParmLine|
|Class WhsWorkExecute|
|Class WmsBillOfLadingDP::insertIntoTempTable|
|Class WmsOrderTransType_OutputDontPostTransfer.updateParentMovement|
|Class WrkCtrCapResHandler.hasNewCapacityReservation|
|Class WrkCtrCapResHandler.loadCapacityReservations|
|Class WrkCtrReservedSum.calcReservationSumGroupId|
|Class WrkCtrReservedSum.calcReservationSumGroupId|
|Class WrkCtrReservedSum.calcReservationSumWrkCtrId|
|Class WrkCtrReservedSum.calcReservationSumWrkCtrId|
|Class WrkCtrScheduler_Prod.saveOperation|
|Class createParmLinesFromTransferLinesOnLoad|
|Class smmCampaignQueries.lookupClass|
|Entity EcoResProductDimensionGroupEntity.dataSourceDimensionFieldId|
|Entity InventProductDefaultOrderSettingsEntity.insertEntityDataSource|
|Entity InventProductSiteSpecificOrderSettingsEntity.insertEntityDataSource|
|Entity PSAActualEntity.createQuery_LaborConsumptionQty|
|Entity PSAActualEntity.createQuery_LaborConsumption|
|Entity PSAActualEntity.createQuery_PlLaborCost|
|Entity PSAActualEntity.createQuery_PlLaborQty|
|Entity PSAForecastEntity.createQuery_LaborConsumptionForecastQty|
|Entity PSAForecastEntity.createQuery_LaborConsumptionForecast|
|Entity PSAForecastEntity.createQuery_PlLaborForecastCost|
|Entity PSAForecastEntity.createQuery_PlLaborForecastQty|
|Form BOMCalcDialog.updateDesign|
|Form EcoResProductCreate.releaseProductToCompany|
|Form InventItemOrderSetup.InventItemSetupSupplyType.editOrderType|
|Form InventLocationIdLookup.InventDim_DS.init|
|Form InventLocationIdLookup.InventLocation_DS.init|
|Form InventNonConformanceTable.init|
|Form InventNonConformanceTableCreate.InventNonConformanceTable.write|
|Form InventQualityOrderTableCreate.allowEdit|
|Form InventQualityOrderTableCreate.refreshCaller|
|Form InventTestAssociationTable.initRecord|
|Form InventTransPick\TmpInventTransWMS.validateWrite|
|Form LedgerTransVoucher.updateQueryForProject|
|Form MarkupAllocation.init|
|Form MarkupAllocation_VendInvoiceTrans|
|Form PdsBatchAttributes.PdsBatchAttributes.linkActive|
|Form PriceDiscAdmTable.init|
|Form PriceDiscTable.appendInventCriteria|
|Form PriceDiscTable.buildOrderLineFilter|
|Form PriceDiscTable.buildSearchFilter|
|Form PriceDiscTable.isLineFilterEnabled|
|Form PriceDiscTable.retrieveRelationType|
|Form ProdParmStartUp.ProdParmStartUp.active|
|Form ProjCreditNoteSelect.editMark|
|Form ProjTableCreate.ProjTable.write|
|Form PurchCreateFromSalesOrder.initFields|
|Form PurchUpdateRemain.closeOk|
|Form ReqTransPoMarkFirm.init|
|Form RetailAddItems.closeOk|
|Form RetailColorGroupTable.RetailColorGroupTrans.recordHasChanges|
|Form RouteLookupOprNum.init|
|Form VendEditInvoice.invoiceAccountModified|
|Form VendEditInvoice.run|
|Form VendOpenTrans.editMarkTrans|
|Form WrkCtrCapResGraphDialog.setParm|
|Map BomCalcTransMap.displayUnitId|
|Table AssetTable.lookupAccountNum|
|Table AssetTrans|
|Table CaseDetailBase.validateWrite|
|Table EcoResProductMasterConfiguration.existWithSameConfigUnit|
|Table FormletterJournalTrans.getLinePrefix|
|Table InventItemPriceSim.autoSalesPrice|
|Table InventQualityOrderLine.adjustInt|
|Table InventQualityOrderTable.createInventQualityOrderLines|
|Table InventQualityOrderTable.initFromReference|
|Table InventQualityOrderTable.initQtyFromAssocation|
|Table InventTestAssocationTable.checkAccountRelation|
|Table InventTestAssocationTable.validateWrite|
|Table InventTrans.insertReturnTransOrigin|
|Table InventTransOrigin.createOrigin|
|Table InventTransferParmLine.createPickLines|
|Table InventTransferParmLine.createReceiveLines|
|Table InventTransferParmLine.createShipLines|
|Table JmgStampjournalTrans|
|Table JmgTermReg.createJournalSignIn|
|Table JmgTermReg.update|
|Table LedgerJournalTrans.delete|
|Table LedgerJournalTrans.validateWrite_Server|
|Table PriceDiscAdm.getEntityAutoReportFieldGroupName|
|Table PriceDiscAdm.getEntityJournalNumberFieldName|
|Table PriceDiscAdmTrans.CheckAccountRelation|
|Table PriceDiscAdmTrans.checkItemRelation|
|Table PurchLine.setPriceDisc|
|Table RouteVersion.selectRouteVersion|
|Table SalesLine.checkItemId|
|Table SalesLine.getSourcingFields|
|Table SalesLine.setPriceAgreement|
|Table SalesLine.setPriceDisc|
|Table SalesLine.setSourcingFields|
|Table SalesQuotationLine.IsCategoryBased|
|Table SalesQuotationLine.mcrCreateFromTmpFrmVirtualFromContract|
|Table SalesQuotationLine.setPriceAgreement|
|Table SalesQuotationLine.setPriceDisc|
|Table Salesline.splitReturnLine|
|Table SuppItemCreate.createLine|
|Table TmpInventTransMark.packTmpMark|
|Table VendInvoiceMatchingLine.initFromPurchLine|
|Table VendTable.updateOnHold|
|Table WHSInvent.checkNonPhysicalDims|
|Table WHSShipmentTable.consolidateShipments|
|Table WHSShipmentTable.transferShipment|
|Table WHSTmpPackingLine.addTmpPackLine|
|Table salesLine.initFromProjTable|
|Table smmBusRelTable.updateReferences|
|Table smmLeadTable|
|Table smmOpportunityTable|


## Maps enabled for extensibility

New patterns have been introduced for maps implementation that will allow you to add fields and methods by extensions. Details on how this is done is available in the documentation both with maps that are used as interfaces and for versioning implementations.

The following table lists the maps and related tables where changes have been applied for enabling extensibility.

| Maps |
| -------------------|
|CustVendSettlement|
|JmgStampTransMap|
|PriceDiscResultFields|
|SalesPurchLine|

## Inventory dimensions

This release made minor improvements to the new model for adding inventory dimensions, all targeted at supporting more scenarios through extensions. 

| Change |
| -------------|
|BOM hierarchy works only with the config dimension|
|Form BOMDesigner should use field group for showing dimensions|
|Form EcoResProductSearchLookup should use field group for showing dimensions|
|Form FactureJournal_RU should use field group for showing dimensions|
|Form InventDimParmFixed.InventDimensionXXFlag.Style is incorrect|
|Form InventItemOrderSetup should use field group for showing dimensions|
|Form InventTransferParmPick should use field group for showing dimensions|
|Form InventTransferReleaseOrderPicking should use field group for showing dimensions|
|Form KanbanCreateScheduled should use field group for showing dimensions|
|Form KanbanJobPickingListPart should use field group for showing dimensions|
|Form KanbanRules should use field group for showing dimensions |
|Form LeanPeggingTree should use field group for showing dimensions |
|Form MCRItemDisplay should use field group for showing dimensions|
|Form MCRPriceDiscGroupItem should use field group for showing dimensions|
|Form PlanActivityServiceWizard should use field group for showing dimensions |
|Form ProdBOMVendor should use field group for showing dimensions |
|Form PurchAgreementGenerateReleaseOrder should use field group for showing dimensions |
|Form PurchAgreementHistory should use field group for showing dimensions|
|Form PurchComplementaryInvoice should use field group for showing dimensions|
|Form PurchRFQCompareLineDimensions should use field group for showing dimensions|
|Form PurchTable.TrackingDimesions has incorrect spelling|
|Form PurchVendorPortalAllResponse should use field group for showing dimensions|
|Form PurchVendorPortalConfirmedOrders should use field group for showing dimensions|
|Form PurchVendorPortalOriginalOrder should use field group for showing dimensions|
|Form PurchVendorPortalRequests should use field group for showing dimensions|
|Form PurchVendorPortalResponses should use field group for showing dimensions|
|Form ReqDemPlanEasyItemAllocator should use field group for showing dimensions|
|Form ReqOutboundIntercompanyDemand should use field group for showing dimensions |
|Form ReqSupplyDemandScheduleFilters should use field group for showing dimensions|
|Form RetailVariantLookup should use field group for showing dimensions |
|Form RouteVersionFeasibility should use field group for showing dimensions|
|Form SMAAgreementTable should use field group for showing dimensions |
|Form SalesAgreementGenerateReleaseOrder should use field group for showing dimensions |
|Form SalesAgreementHistory should use field group for showing dimensions |
|Form SalesComplementaryInvoice should use field group for showing dimensions|
|Form SalesLineDeliveryDetails should use field group for showing dimensions|
|Form SalesQuotationProjTable should use field group for showing dimensions |
|Form SalesQuotationTable should use field group for showing dimensions|
|Form SalesTable should use field group for showing dimensions |
|Form TAMFundManagement should use field group for showing dimensions|
|Form TAMTradePromotions should use field group for showing dimensions|
|Form VendEditInvoice should use field group for showing dimensions |
|Form VendJournalMatch_PackingSlip should use field group for showing dimensions |
|Form WHSLoadPlanningWorkBench should use field group for showing dimensions |
|Form WHSLoadPlanningWorkbench should use field group for showing dimensions|
|Form WHSLoadTable should use field group for showing dimensions |
|Form WHSLoadTable should use field group for showing dimensions|
|Form WHSProdWaveTableManageBOMPool should use field group for showing dimensions|
|Form WHSWorkTable should use field group for showing dimensions |
|Form WMSOrderTransUnPick should use field group for showing dimensions|
|Form WMSPickingRegistration should use field group for showing dimensions |
|Report InventAging does not support extra dimensions|
|Table EcoResProductVariantStaging.StagingIdx need extra dimension fields|

## Other changes

The following table lists additional changes that have been made for extensibility.

| Change |
| -------------|
|Add filter interface: form InventQualityOrderTable|
|Address management: Adding new address fields|
|AxMaps - TradePostalAddress - partyTable|
|Bank Trans Comments - BankReconciliationDataInitializer|
|Cancellation Log Requirements - Update Sales Deliver Remainder|
|Extend the grouping mechanisme from purch req line to purch line|
|Extend the splitting mechanisme from purch req line to purch line|
|Allow multiple funding sources in conjunction with item requirements|
|Implementing exchange rate provider framework|
|Make the PriceDiscPartyCodeType extensible in all usages|
|Make the PriceDiscProductCodeType extensible in all usages|
|Table RetailChannelTable does not have ReplacementKey|
|Table RetailSeasonTable CreateRecIdIndex True|
|Modify index: table InventTestAssociationTable|
|Entity UnitOfMeasureEntity switched to public|
|Entity UnitOfMeasureTranslationEntity switched to public|


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]