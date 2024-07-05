---
title: Extensibility changes in Finance and Operations, Enterprise edition 7.3
description: Learn about the extensibility features that were released in Dynamics 365 for Finance and Operations, Enterprise edition 7.3.
author: FrankDahl
ms.author: fdahl
ms.topic: article
ms.date: 04/10/2018
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2017-12-20
ms.dyn365.ops.version: Platform update 4
---

# Extensibility changes in Finance and Operations, Enterprise edition 7.3

[!include [banner](../includes/banner.md)]

This article lists the extensibility features that were released in Dynamics 365 for Finance and Operations, Enterprise edition 7.3. For more information about the schedule of changes that support extensibility, see [Application extensibility plans](extensibility-roadmap.md).

## Soft-sealed application models

This release marks the last release before all models will become hard-sealed, and as a step toward this all application models are now soft-sealed. Soft-sealed models still allow for making overlayered code, but warnings will be generated when you compile the overlayered code. 

> [!NOTE]
> You can still overlayer code, but extension is the recommended approach.

The following table includes a list of the models that are soft-sealed with this release.

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
|Retail | Retail |
|SourceDocumentation | SourceDocumentation |
|SourceDocumentationTypes | SourceDocumentationTypes |
|Subledger | Subledger |
|Tax | Tax |

## Hard-sealed application models

With this release, almost all application core models have been hard-sealed. Overlayered code in these models will now produce compilation errors. The only supported customization model is through extensions. If you cannot customize these models through extension, then you will have to make a request to Microsoft to enable extensibility by changing the standard application.

TThe following table includes a list of models that are now hard-sealed with this release.

| Module| Model         |
| --------------- |-------------|
| AccountsPayableMobile | AccountsPayableMobile |
| ApplicationWorkspaces | ApplicationWorkspaces |
| BankTypes | BankTypes |
| BusinessProcess | BusinessProcess |
| Calendar | Calendar |
| ContactPerson | ContactPerson |
| CostAccounting | CostAccounting |
| CostAccountingAX | CostAccountingAX |
| Dimensions | Dimensions |
| DirectoryUpgrade | DirectoryUpgrade |
| DOM | DOM |
| ElectronicReporting | ElectronicReporting |
| ElectronicReportingAppSuiteIntegration | ElectronicReportingAppSuiteIntegration |
| ElectronicReportingCore | ElectronicReportingCore |
| ElectronicReportingDotNetUtils | ElectronicReportingDotNetUtils |
| ElectronicReportingForAx | ElectronicReportingForAx |
| ElectronicReportingMapping | ElectronicReportingMapping |
| ExpenseMobile | ExpenseMobile |
| FinancialReporting | FinancialReporting |
| FinancialReportingEntityStore | FinancialReportingEntityStore |
| FiscalBooks | FiscalBooks |
| InventoryDimensionConversion | InventoryDimensionConversion |
| Measurement | Measurement |
| PaymentPredictor | PaymentPredictor |
| PerformanceTool | PerformanceTool |
| Personnel | Personnel |
| PersonnelCore | PersonnelCore |
| PersonnelMobile | PersonnelMobile |
| PersonnelUpgrade | PersonnelUpgrade |
| Policy | Policy |
| Project | Project |
| ProjectMobile | ProjectMobile |
| RegulatoryServices | RegulatoryServices |
| SCMMobile | SCMMobile |
| SelfHealing | SelfHealing |
| SelfHealingRules | SelfHealingRules |
| SystemHealth | SystemHealth |
| TaxEngine | TaxEngine |
| UnitOfMeasure | UnitOfMeasure |
| WMSAdvancedMigration | WMSAdvancedMigration |

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
|AssetCalendarYearType|
|AssetDepreciationConvention|
|AssetDepreciationMethod|
|AssetPeriodMonth|
|AssetSoldScrap|
|AssetStatusLVPFilter|
|AssetTransType|
|BaseDataProd|
|BOMRouteVersionSelect|
|BudgetPlanGenerateSource|
|BudgetPlanScenarioAccessLevel|
|BudgetPlanScenarioAttribute|
|BudgetTransactionColumnType|
|BusinessEvent_ActivityJournal|
|BusinessEvent_CustomerInvoice|
|BusinessEventRelievingMethod|
|CollabSiteEntityType|
|CollabSiteSharePointType|
|CostSheetNodeType|
|CreditCardAddEdit|
|CreditCardApprovalType|
|CreditCardDupCheckResult|
|CreditCardPaymType|
|CustAssessment|
|CustCollectionLetterCode|
|CustInterestFeeType|
|CustomerTransactionType|
|CustSettlementPriorityAttribute|
|CustSettlementTrans|
|CustTransRefType|
|CustVendDisputeStatus|
|CustVendForeignExchRefIndicator_US|
|CustVendGatewayOperatorOFACIndicator_US|
|CustVendorBlocked|
|CustVendOutPaymTrade|
|CustVendPaymStatus|
|CustVendSecondaryOFACIndicator_US|
|DimensionCacheScope|
|DirPartyRoleType|
|DirPartyRoleView|
|DistributionProcess|
|DistributionProcessingState|
|DistributionStatus|
|EPProjUpdateSubProjStage|
|HcmPositionForecastStatusSelection|
|JournalizingDefinitionLedgerEntryTypeId|
|LedgerBalanceExportFieldSeparator|
|LedgerBalanceExportHeaders|
|LedgerBalanceExportHiddenFields|
|LedgerBalanceExportInvertSign|
|LedgerBalanceExportSubcomponents|
|LedgerBalanceExportSubtotals|
|LedgerColumnType|
|LedgerConsDim|
|LedgerConsolidateAccountSource|
|LedgerDataExportFormat|
|LedgerReconciliationStatus|
|LedgerShowCurrency|
|LedgerSIEFileType|
|LedgerTransactionType|
|LedgerTransEnigneBuildQuery|
|LogisticsAddressElement|
|LogisticsAddrZipCodeImportCountryRegion|
|LogisticsLocationEntityType|
|LogisticsLocationSelectSourceType|
|MCROrderEventType|
|PaymManDocType|
|ProjAccountType|
|ProjAccountTypeCost|
|ProjAccountTypeSales|
|ProjActualVsForecastCategory|
|ProjActualVsForecastValue|
|ProjAlertType|
|ProjAssignConflictStatus|
|ProjCategoryType|
|ProjChoose|
|ProjContractType|
|ProjCostSales|
|ProjDimensionStrType|
|ProjectReportingAnalyticsWorkspaces|
|ProjEstimateMethod|
|ProjExportToExcelDimension|
|ProjFoundMethod|
|ProjFunctionType|
|ProjFundingRuleType|
|ProjInvoiceFrequency|
|ProjInvoiceProposalsTransSelectionTypes|
|ProjLevelFilterOption|
|ProjListLedgerTransType|
|ProjOrigin|
|ProjOriginOnAcc|
|projPostedProjectTransactionsListFilter|
|ProjProdTableListPageFilter|
|projProjectsListFilter|
|ProjQuotationTransTypeFilter|
|ProjResourceCapacityBooking|
|ProjResourceViewType|
|ProjSelectTransOnAcc|
|ProjServerProcessStatus|
|ProjStatementTypeSub|
|ProjStatus|
|ProjTransType|
|ProjValConnection|
|ProjValidateType|
|ProjViewSubProjects|
|ProjYearEndOptions|
|PSAActivityDisplayDefault|
|PSAActivityParent|
|PSADetailLevel|
|PSAExpenseProjValCategoryType|
|PSAInvoiceFormats|
|PSAProjInvoiceDetailGrouping|
|PSAProjInvoiceDetailSortBy|
|PSAProjOriginakVsCurrent|
|PSAPWPAssessment|
|PSAResAssignView|
|PSAResSchedStatus|
|PurchStatus|
|QuotationProjTransType|
|ReasonCodeAccountType|
|ResBasicSearchType|
|ResRollUpResourceType|
|ResTransferType|
|ResUtilizationCategoryEnum|
|RetailEventNotificationType|
|SourceDocument_ActivityJournal|
|SourceDocumentLine_ActivityJournalLine|
|SpecType|
|SyncProjTableAddSubProj|
|SyncProjTableDeleteSubProj|
|TrvCarRentalChargeType|
|TrvExpenseFilter|
|TrvExpenseReportGroupBy|
|TrvIntermediatePageOnCreateExpenseReport|
|TrvPayrollQtyOrDayes|
|TrvPBSTxtType|
|TrvPolicyViolationAction|
|TrvPosting|
|TrvPostStatus|
|TrvTaxType|
|TrvUDFDisplayOption|
|TSApprovalLevel|
|TSDocumentStatusReset|
|TSTimesheetFilter|
|TSTimesheetLineFilterType|
|TSTimesheetListPageFilters|
|TSVendorPerformanceThreshold|
|TypeOfCreditmaxCheck|
|VendInvoiceCloseCommand|
|VendorInvoiceSearchOptions|
|VendOutPaymFeeDistribution|

Foundation changes were made to improve support for extensible enumerations. The **SysPlugin** framework was enabled for enumerations where **IsExtensible** is set to **Yes**. Views were enabled with new name-based syntax for enumerations.

## Data manipulation methods that do not raise DataEvents or missing insert, update, delete pre- and post-data events

As a general practice, you use data methods on tables to raise events that can be used for extending the application. The code base has not always followed this practice. For example, the **doInsert**, **doUpdate**, and **doDelete** data methods and certain table implementations did not make a call to **super()** in the data method.

The **insert**, **update**, and **delete** methods on the type classes have been refactored. Changes were made so that **super()** is called more consistently in data methods. These changes enable extensions to be added to these methods, so that pre- and post-events are now available for extension. The tables where the **insert**, **update**, and **delete** events were enabled for extension are listed in the following table.

| Table and method |
| ----------------------|
|BOM|
|BOMTable|
|BOMVersion|
|ProjTableType.delete|
|ProjTableType.update|
|Route|
|RouteOpr|
|RouteTable|
|RouteVersion|
|SalesLineType::interCompanyResetDeliverNow|
|Table ForecastSales|

## Exposing class members

Additional private members are now available for customization as a result of changes to access modifiers and parm methods. The chain of command platform feature enables extension class access to protected methods and members. For more information about chain of command, see [Extensible X++: Chain of Command](https://community.dynamics.com/365/financeandoperations/b/mfp/posts/extensible-x-chain-of-command).

| Member |
| -------------|
|BankPaymCancel.custTransToCancel|
|CustCollectionLetterCancel - method queryBuildUpdate|
|CustCollectionLetterPost - method queryBuildUpdate|
|CustCollectionLetterPost - method updateFee|
|CustCollectionLetterPost - method validateCollectionLetter|
|CustInterestCancel - method updateQuery|
|CustInterestHelper - method getFeeLedgerAccount|
|CustInterestHelper - method getInterestRecord|
|CustInterestHelper - method getPostingProfile|
|CustInterestHelper - method getTransLedgerAccount|
|CustInterestHelper - method getTransLineLedgerAccount|
|CustInterestHelper - method getVerDetailLedgerDimensionByIntTrans|
|CustInterestPost - method postVoucher|
|CustOutPaymControlController|
|CustVendCreatePaymJournal - method dialogAddInvoiceSelectionCriteriaFields|
|CustVendPaymProposal - method createProposalLine|
|CustVendPaymProposal - method parmLedgerJournalId|
|CustVendPaymProposalLineInsertSetManager - variables|
|CustVendPaymProposalOrg - variables|
|CustVendPaymProposalTransferToJournal - method trackSpecTransForUpdate|
|CustVendPaymProposalTransferToJournal - variables|
|Form ProjWorkBreakdownStructure|
|Form/Class CustPaymModeSpec|
|Form/Class VendPaymModeSpec|
|InventUpd_ChildReference.initUpdate|
|InventUpd_ChildReference.parmInventDimId|
|LogisticsLocationFormHandler.callerGetAddressRecord|
|ProjAdjustmentSelect.newQuery.addAdditionalHeaderRange|
|ProjAdjustmentSelect.processProjCostTrans|
|ProjAdjustmentSplit.deleteTransaction|
|ProjAdjustmentSplit.splitTransaction|
|ProjInvoiceChoose.parmprojInvoiceProjId|
|ProjProposalTotals.projInvoiceExchRate|
|SalesInvoiceJournalCreateBase|
|smmActivityCreate.createOrPrompt|
|Table SalesQuotationTable.canSubmitToWorkflow|
|VendorInvoiceLineSourceDocLineItem.initializeProjectFields|
|WHSWorkUserSession.WorkExecuteMode|

## Construct methods with throw statements

Some **construct** methods were implemented with **throw** statements if there was a missing implementation for a given type. This doesn't work well with extensibility, so to mitigate this, **construct** methods were changed so that they do not throw exceptions. These methods are now to open for extensibility through class augmentation or by post-event subscription.

| Object |
| -------------|
|AddressZipCodeImport|
|CaseCategoryHierarchyTree|
|CustInterestCancel|
|CustInterestHelper|
|CustInterestPost|
|CustOutPaymControlController|
|CustTransQueryBuild|
|CustVendCreatePaymJournal_Cust|
|CustVendFindSettlements|
|CustVendOpenTransBalances.new|
|CustVendOpenTransManager.initFromCaller|
|CustVendPaymProposalTransferToJournal|
|CustVendTransQueryBuild|
|Form PdsApprovedVendorList|
|Form WhsContainerTable.init|
|FormletterJournalCreate.newSalesJournalCreate|
|FormLetterJournalPost.newPostSales|
|InventUpd_Physical::newInventMovement|
|InventUpd_Physical::newProdReleaseLossProfit_RU|
|LogisticsLocationSelectForm|
|PdsApprovedVendorListCheck.newBasedOnTableType|
|ProjInvoiceChoose|
|ProjTrans|
|PurchReqAutoCreate.newAutoCreate|
|PurchTableForm_Project|
|SalesQuantity|
|SalesTotals|
|WHSReservation|

## Find methods with throw statements

Some **find** methods were implemented with **throw** statements if there was a missing implementation for a given type. This does not work well with extensibility, so to mitigate this, **find** methods were changed so that they do not throw exceptions. These methods are now to open for extensibility through class augmentation or by post-event subscription.

| Methods |
| -------------|
|TradePostalAddress.partyTable|

## Extracted method to open for class extensions

The **Chain of Command** feature lets you create extension classes. Extensions classes offer a stronger way of extending than other options because they allow access to both protected and public methods and members. This provides more flexibility than extending through delegates or by pre or post event.

Within this group of changes, longer methods are extracted into smaller methods. The new methods have a more specific focus and you have more control over the scope of your extensions.

After the introduction of the **Chain of Command** feature, we suggest using extensibility by extracting methods instead of adding delegates because this approach provides a more versatile solution.

The following table lists the new methods that have been extracted and opened for building extension classes.

| Method |
| -------------|
|AssetPost|
|BankPrintTestCheque|
|CustCreditLimit.showErrorMsg|
|CustVendCheque|
|CustVendChequeSlipTextCalculator|
|Form CustBankAccounts|
|Form DirPartyQuickCreateForm.init|
|Form HierarchyDetail.contextChanged|
|Form HierarchyDetail: smmActiviate:  initValue|
|Form HierarchyNameLookoup: Hierarchy: init|
|Form LedgerJournalTransDimension.init|
|Form ProjInvoiceProposalDetail.editInvoiceFormat|
|Form SalesCopying.upDateRemainderCache|
|Form SalesQuotationProjLinkWizard-> changeType|
|Form smmActivities: ResponsibleWorker_Overview: lookupReference|
|Form smmActivities: smmActivities::initValue|
|FormletterJournalPrint|
|HierarchyTemplateCopying.run|
|HierarchyTemplateCopying_CRM.copyActivity|
|HierarchyTemplateCopyingDialog.main|
|HierarchyTree|
|HierarchyTree.buildSubTree|
|InventDimCtrl_Frm_Mov_QualityOrder.mustEnableField|
|InventDistinctProductValidator.checkProductNotStopped|
|InventMovement.createProjLedgerForUpdateLedgerAdjust|
|InventTransferUpdShip::populateIssueReceiptDimensions|
|JournalFormTable|
|JournalizingDefinitionManager.newJournalizingDefinitionManagerCustomer|
|LedgerJournalCheckPost.checkJournal|
|LedgerJournalCheckPost.postJournal|
|LedgerJournalEngine.parmLedgerJournalTrans_Project|
|LedgerJournalEngine_Server.addVoucher|
|LedgerJournalEngine_VendApprove.cancelVoucher|
|LedgerJournalizeReportDP_DE.processReport|
|LedgerJournalTransUpdateCust.checkAccountBlocked|
|LedgerJournalTransUpdateVend.checkVendorBlocked|
|LogisticsAddressFormatProcess.run|
|ProjAdjustmentUpdate.journalTableInsert|
|ProjAdjustmentUpdate_Post|
|projCategoryLookup.buildQuery_PSA_impl|
|ProjEstimate.add|
|ProjFormLetter_invoice.projPrintFormLetter|
|ProjIntercompanyVendorInvoiceCreator.createVendorInvoiceLine|
|ProjListTransDP.insertTmpProjTransList|
|ProjPostRevenueProposal.projTransCreate|
|projUnpostedTransactionsListPage.populateMenuFunction|
|PSAProjAndContractInvoiceController.preRunModifyContract|
|PSARetenetionRelease.run|
|PurchAutoCreate_SalesLine.setPurchTable|
|PurchCreateFromSalesOrder.run|
|PurchFormletterParmDataInvoice.createParmLinesAndTable|
|PurchTableForm_DlvScheduleSyncEnabled.syncDeliveryScheduleCommercialAttributes|
|ReqCalc.deleteItemRequirement|
|ReturnAcknowledgmentAndDocumentDP.insertIntoTempTable|
|ReturnAcknowledgmentAndDocumentDP.setReturnAckAndDocumentTemplate|
|SalesAgreementFormDatasourceManager.transferCustAccount|
|SalesCopying.copy|
|SalesFormLetterParmData.createParmSubTable|
|SalesFormLetterParmDataInvoice.reSelectInit|
|SalesQuotationConfirmationDP.processReport|
|SalesQuotationConfirmationDP.setSalesQuotationDetailsTmp|
|SalesQuotationEditLinesForm.createParmLine|
|SalesQuotationEditLinesForm_Sales_Confir.createSalesLines|
|SalesQuotationTableForm_Sales.syncDeliveryScheduleCommercialAttributes|
|SalesQuotationTableType.validateField|
|SalesTable2LineUpdate.update|
|SalesTableForm.interCompanySetLineAccess|
|SalesTableForm_DlvScheduleSyncEnabled.syncDeliveryScheduleCommercialAttributes|
|SalesUpdateRemain.updateICDeliverRemainder|
|SmmProcessInstance.openForm|
|SubledgerJournalizerProjectExtension.createProjectActualHeader|
|Table CustTable.createOneTimeAccount|
|Table CustTable.lookupCustomer|
|Table InventPosting.salesAccount2AccountType|
|Table InventTable.lookupItem|
|Table ReqPO.update|
|Table SalesLine -> createFromSalesQuotationLine|
|Table SalesTable::initFromCustTableIL|
|Table smmBusRelTable.relation2Customer|
|Table smmBusRelTable.updateCustTable|
|Table TSTimesheetTrans.updateCommentsFromLineWeekUpdateTSTimesheetTrans|
|Table TSTimesheetTrans.updateFromTimesheetLineWeekUpdateTSTimesheetTrans|
|Table VendTable.lookupVendor|
|Table WHSWorkTable ->deleteAndCleanupWorkLines|
|Table WHSWorkTable ->SetBlankFields|
|Table WHSWorkTable ->SetFields|
|Table WrkCtrActivity.getCompanyContext|
|Tax.insertLineInInternal|
|TransactionReversal_Cust.fld900_1_modified|
|whsLoadTemplateAssignmentForm: WHSLoadTable::clicked|
|WhsWorkExecuteDisplay.getNextFormState|
|WHSWorkExecuteDisplay.setBatchDetails|
|WhsWorkExecuteDisplayReturnOrder.buildReturnOrder|
|WhsWorkExecuteDisplayReturnOrder.displayForm|

## Changes using other methods to support extensibility

The group of changes in this section includes several different approaches to extensibility and represents the extensibilty changes made before **Chain of Command** was introduced. Some of the approaches used are extracting methods, adding "stub" methods, adding delegates, changing access modifiers on methods, and using the SysExtension framework. Please consult the implementation in places required for your customization to determine if the approach taken will work for your customization. In future releases, this group will be small, because we will primarily be using **Chain of Command**.

| Method |
| -------------|
|AccDistRuleSaleOfProductExtendedPrice.parmLedgerDimensionAllocList|
|AssetPost.createInventorySoldTransaction|
|AssetSplit.validate|
|AxSalesLine.doSave|
|AxSalesLine.setLineAmount|
|AxSalesQuotationLine.setLineAmount|
|BankPaymCancel.main|
|BankPaymCancel.run|
|BankPaymCancel.serverRun|
|BomCalcJob.main|
|CustCollectionLetterCancel.main|
|CustCollectionLetterCancel.run|
|CustCollectionLetterCreate.checkCustTransOpen|
|CustCollectionLetterCreate.createJournal|
|CustCollectionLetterPost.updateFee|
|CustCollectionLetterPost.validate|
|CustCollectionsExcelStatement.setTransactionWorksheetRow|
|CustInterestCancel.run|
|CustInterestCreate|
|CustInterestCreate.dialog|
|CustInterestCreate.runOnce|
|CustInterestHelper.getFeeLedgerAccount|
|CustInterestHelper.getVerDetailLedgerDimensionByIntTrans|
|CustInterestPost.postVoucher|
|CustInterestPost.run|
|CustInterestPost.updateFee|
|CustInterestPost.validateInterestTrans|
|CustInvoiceSpecDP::insertIntoTempTable|
|CustOutPaymControlController.init|
|CustPostInvoiceJob.custPostInvoiceUpdate()|
|CustSettlementPriorityProcessing|
|CustSettlementPriorityProcessing.markAllSelected|
|CustSettlementPriorityProcessing.markTransByCreditNoteOnBillingClasses|
|CustVendCreatePaymJournal.initBalances|
|CustVendOpenTransManager::updateOriginatorForMarkedTrans|
|CustVendPaymProposalCalcPaym.calcPaymDueDate|
|CustVendReversePosting.updateNow|
|CustVendSettle.mustOffsetOriginalSummaryDistributions|
|CustVendVoucher.initLedgerPosting|
|DimensionDerivationRule.buildDimensionCombination|
|DimensionDerivationRule.initialize|
|EcoResProductReleaseManager.release|
|EcoResProductReleaseSessionBatch.runJob|
|EcoResProductReleaseSessionManager.executeOnServer|
|EcoResProductVariantCreationMgr.buildVariantSuggestions()|
|Form BankPaymCancel.closeOK|
|Form BOMChangeLine.init|
|Form BOMConsistOf: BOMCreate|
|Form ConfigPartOf: EcoResConfiguration|
|Form CustBankAccounts.write|
|Form CustCollections.showAgingIndicator|
|Form CustOpenTrans.editMarkTrans|
|Form CustOpenTrans.updateDesignStatic|
|Form CustPaymEntry.editIsMarkedForSettlement|
|Form CustPaymEntry.write|
|Form CustSettlementPrioritySetup.active|
|Form CustTable.PrintManagement.clicked|
|Form EcoResProductImage.init|
|Form EcoResProductImage.setProductRecId|
|Form HRMAbsenceRequest.init|
|Form LedgerJournalTransAccrual.enableFields|
|Form LedgerJournalTransAccrual.LedgerJournalTransAccrual.clicked|
|Form LedgerJournalTransCustPaym: LedgerJournalTrans.active|
|Form LedgerJournalTransDaily: SettlementButton.clicked|
|Form LedgerJournalTransDimension.init|
|Form MarkupTable.init|
|Form MCRItemListCopying.copyLines|
|Form PCProductModelVersion|
|Form ProjInvoiceProposalCreateLines.modifiedTransFilter|
|Form ProjTransItem: ProjItemTrans.salesAmount|
|Form PurchCreateFromSalesOrder.SalesLine.included|
|Form ReqItemTable.init|
|Form SalesCopying.canClose|
|Form SalesCreateQuotation.setFieldsActive|
|Form SalesQuotationTable.init|
|Form SalesTable: SalesLine.write|
|Form SalesTable: SalesLine_DS.ItemId.lookup|
|Form: VendEditInvoice|
|FormletterJournalPos::newPostSales|
|FormLetterJournalPost.post|
|FormletterService.run|
|From ProjTable.init|
|HierarchyTemplateCopying.copyHierarchy|
|HrmAbsenceRequestAction.run|
|InterCompanyUpdateRemPhys_PurchLine::synchronizeExternal|
|InterCompanyUpdateRemPhys_PurchLine::synchronizeInternal|
|InterCompanyUpdateStatus_PurchLine::synchronizeExternal|
|InterCompanyUpdateStatus_PurchLine::synchronizeInternal|
|IntrastatTransfer::calcCustVendInvoiceTransQty|
|InventDim::dimReportStr|
|InventMov_Transfer::checkUpdateEstimated|
|InventMov_Transfer::defaultDimension|
|InventMovement::checkNotSubDelivery|
|InventQualityManagementCreate.createQualityOrder|
|InventTransferParmLine::createShipLines|
|InventTransferParmLine::initFromInventTransferParmTable|
|InventTransferUpdShip::updateInventTransferLine|
|InventUpd_Estimated::createEstimatedInventTrans|
|InventUpd_Financial::newInventTransferLineReceive|
|InventUpd_Financial::newInventTransferLineShip|
|InventUpd_Financial::updateFinancialIssue|
|InventUpd_Financial::updateFinancialReceipt|
|InventUpd_Physical::newInventMovement|
|InventUpd_Reservation::updateReserveBuffer|
|InventUpd_Reservation::updateReserveFromForm|
|InventUpdate::whsUpdateDimReservePhysical|
|InventUpdate::whsUpdateWorkTransDimIssue|
|LedgerJournalCheckPost.postJournal|
|LedgerJournalEngine - method preDelete|
|LedgerJournalEngine::findSettledAmount|
|LedgerJournalEngine_CustPayment.allowEditTrans|
|LedgerJournalEngine_CustPayment.initDefaultDimension|
|LedgerJournalEngine_CustPayment.write|
|LedgerJournalFormTable.verifyCanDelete|
|LedgerVoucherTransObject.newTransLedgerJournal|
|LogisticsPostalAddressFormHandler.main|
|Map SalesPurchLine.calcPrice2LineAmount|
|Map SalesPurchLine.setPriceAgreement|
|Markup.calc|
|MarkupAdjustment::main|
|McrPriceHistoryForm.insertPotentialTradeAgreements|
|OffsetVoucherCust.updateNow|
|PcGenerateBOMTableAndVersion.generate|
|PriceDisc.findDisc|
|PriceDisc::findItemLineDiscAgreement|
|PriceDisc::findItemPriceAgreement|
|PriceDisc::findMultiLineDiscServer|
|PriceDisc::newFromPriceDiscHeading|
|PriceDisc_LineDisc::findLineDiscAgreement|
|PriceDisc_Price::findPriceAgreement|
|PriceDiscAdmCheckPost.checkJournal|
|PrintMgmtHierarchy_Project.getParentImplementation|
|ProjAdjustmentSplit.createNewTrans.getNewTotalCostAmount|
|ProjInvoiceJournalPost.createProjInvoiceRevenue|
|ProjInvoiceProposalInsertLines.doSalesLine|
|ProjPost.postCost|
|ProjPostCostJournal.projTransCreate|
|ProjPostCostTrans_AdjNeg.projTransCreate|
|PurchAutoCreate_PurchReq.prepareSort|
|PurchCalcItem.initListBOM|
|PurchFormLetter.mainOnServer|
|PurchFormLetterParmData::newChooseLines|
|PurchFormletterParmDataInvoice.createParmLineAndSubLines|
|PurchInvoiceJournalPost.checkSourceLine|
|PurchInvoiceJournalPost.postCustVend|
|PurchInvoiceJournalPost.postInventory|
|PurchLineType.initDimensionsSpecificDefaulting|
|PurchLineType.interCompanyMirror|
|ReqCalcExplodeSales.run|
|SalesAutoCreate_ReleaseOrder.createSalesLine|
|SalesConfirmDP::createData|
|SalesConfirmDP::printDimHistory|
|SalesConfirmDP::setSalesConfirmDetailsTmp|
|SalesCopying.copy|
|SalesFormLetter.mainOnServer|
|SalesFormletterParmData.calcAutomaticTotalDiscount|
|SalesFormletterParmDataPickingList.insertParmLine|
|SalesInvoiceController::main|
|SalesInvoiceDP.insertIntoSalesInvoiceTmp|
|SalesInvoiceDP::insertIntoSalesInvoiceTmp|
|SalesInvoiceDP::loadCustPackingSlipTrans|
|SalesInvoiceDPBase::createData|
|SalesInvoiceJournalCreate::initInvoiceLineFromSourceLine|
|SalesInvoiceJournalPost::postCustVend|
|SalesLine::initReleasedProductSpecificDefaulting|
|SalesLineType.initDimensionsSpecificDefaulting|
|SalesLineType.interCompanyMirror|
|SalesLineType::checkDelete|
|SalesLineType::delete|
|SalesLineType::insert|
|SalesLineType::interCompanyMirror|
|SalesLineType::setSalesStatus|
|SalesLineType::update|
|SalesLineType::validateWrite|
|SalesPickingListJournalCreate::createJournalLine|
|SalesQuotationConfirmationDP::processReport|
|SalesQuotationCopying.copy|
|SalesQuotationDP::processReport|
|SalesQuotationLine.modifySalesQty|
|SalesQuotationLineType.initReleasedProductSpecificDefaulting|
|SalesQuotationToLineField.getFieldDescription|
|SalesTable2LineUpdate.update|
|SalesTableListPageInteraction.setButtonInterCompany|
|SalesTableListPageInteraction.setButtonInvoice|
|SalesTableListPageInteraction.setButtonPickAndPack|
|SalesUpdateRemain|
|SalesUpdateRemain::updateDeliveryRemainder|
|smmActivityCreate.setup|
|smmAttendeeTable.insert|
|smmSalesCustItemStatisticsDP::processReport|
|SpecTransManager.updateFullSettlement|
|SubledgerJournalizer.loadAccDistTmpRelieveAccrual|
|SubledgerJournalizer.loadaccountingDistributionTmp|
|SubledgerJournalizer.recordSubledgerJourAccEntriesForRounding|
|SubledgerJournalizer.recordSubledgerJournalAccountEntries|
|SubLedgerJournalTransferUIBuilder::build|
|SuppItemCreate_SalesQuotation::createLine|
|Table - PurchLine.Insert|
|Table - PurchLine.Update|
|Table CostingVersion.validateField|
|Table CustBankAccount.lookupBankAccount|
|Table CustCollectionLetterJour.cancelCollectionLetterCodeCustTrans|
|Table CustInterestJour.feeLedgerDimension|
|Table CustInvoiceTable - method validateWrite|
|Table CustTable.blocked|
|Table CustTrans.reverseTransact|
|Table InventNonConformanceTable.setEditableFields|
|Table InventPosting.accountItemLedgerDimension|
|Table InventTable.updateAutoSalesPrice|
|Table InventTestAssociationTable.checkDocumentType|
|Table InventTrans.accountLossProfitLedgerDimension|
|Table LedgerJournalTrans.checkVATNumJournal|
|Table MarkupTrans.checkMarkCode|
|Table PurchLine.convertCurrencyCode|
|Table ReqPO.validateWrite|
|Table SalesLine.checkAndUpdateLoadLines|
|Table SalesLine.setPriceDisc|
|Table SalesQuotationLine.setPriceDisc|
|Table SalesTable.createMarkupTrans|
|Table TmpInventTransMark.updateTmpMark|
|Table TMSAppointment.validateWrite|
|Table WHSLoadLine::inventTransferLine|
|Table WHSLoadLine::purchLine|
|Table WHSLoadLine::salesLine|
|Table WHSRFMenuItemTable.validateWrite|
|Tax.distributeTotalTax|
|TradeInterCompany::insertInterCompanyInventDim|
|TransactionReversal_Asset.checkStatusApplicable|
|TransactionReversal_Cust.main|
|TransactionReversal_Cust.reversal|
|TransactionReversal_CustVend.createCustVendTrans|
|TSTimesheetLineWeek.loadFromLine|
|VendInvoiceInfoListPageMultiSelect.determineSelectState|
|WHSInventReserveDeltaLevelsEnumerator::moveNext|
|WhsPostEngineBase::createLoadFromShipment|
|WHSWorkCreateProdPut.insertProdParmforProdItem|
|WmsArrivalCreateJournal.createWMSJournalTransFromTmp|
|WMSPickingList_OrderPick.RunPrintMgmt|
|WrkCtrlScheduler_Prod.loadJobsDetail|

## Methods made hookable

Extensibility support has been extended for some methods that were not public and were not hookable. The following methods have been explicitly decorated with hookable behavior.

| Method |
| -------------|
|Bank.checkBankIBAN|
|BankDepositCreateCancelJour.initValues|
|BankDepositCreateCancelJour.newDepositCreateCancelJour|
|BankPaymCancel.initParms|
|BankPaymCancel.updateCollectionsStatusAutomation|
|CustAccountStatementExtController|
|CustAccountStatementIntDP.insertCustAccountStatementIntTmp()|
|CustCollectionLetterPost.updateFee|
|CustInterestCreate.construct|
|CustProvisionalBalanceDP.insertCustProvisionalBalanceTmp()|
|CustSettlementPriorityProcessing|
|CustVendCreatePaymJournal.dialogAddDateSelectionFields|
|CustVendPaymReconciliationSetStatus|
|CustVendReversePosting.updateCustVendTrans|
|DataEntity EcoResTrackingDimensionGroupEntity.dataSourceDimensionFieldId|
|EcoResProductCrossTableManager.saveValuesToProduct|
|EcoResProductImage.getImageFrom2Records|
|EUSalesListTransfer - 3 methods|
|Form EcoResProductCreate.applyTemplate|
|Form EcoResProductCreate.createData2Controls|
|Form PriceDiscTable.initFromCallerTable|
|Form ProjCostControl.setButtonVisibility|
|Form projPostedTransRelInfoFormPart: ProjPostTransView:  costPrice|
|Form ProjTable.lookup Reference|
|Form ProjWorkBreakdownStructure|
|Form WHSPack.updateSummaryFields|
|FormletterJournalPost|
|FreeTextInvoiceDP.bankGroupIdName_CH|
|FreeTextInvoiceDP.bankZipCode_CH|
|FreeTextInvoiceDP.insertGiroInformation|
|FreeTextInvoiceDP.insertIntoFreeTextInvoiceHeaderFooterTmp|
|FreeTextInvoiceDP.insertIntoFreeTextInvoiceLocalizationTmp|
|FreeTextInvoiceDP.insertIntoFreeTextInvoiceTmp|
|HierarchyCreate_CRM.initHierarchy|
|HierarchyTemplateCopying_Proj.copyEstimates|
|InventDimGroupSetup.combineInventDimParms|
|InventLookupItemIdByDefaultOrder.initializeQuery|
|InventStorageDimMap.modifiedInventSiteFromParent|
|InventUpd_Physical.updatePhysicalReceiptTrans|
|JournalFormTable.initJournalTypeFromCaller|
|LedgerJournalCheckPost.runInternal|
|Map SalesPurchLine.setPriceAgreement|
|Maps VendDocumentLineMap.setPurchaseInventReceiveNow|
|OffsetVoucherCust.getAutoSettlementQuery|
|ProjAdjustmentSelect.doTransCost|
|ProjAdjustmentSelect.doTransSale|
|ProjAdjustmentSelect.processProjEmplTrans|
|ProjAdjustmentSelect.validate|
|ProjAdjustmentSplit|
|ProjAdjustmentSplit.createNewTrans|
|ProjAdjustmentSplit.run|
|ProjAdjustmentUpdate.newPostAdjustment|
|ProjBegBalJournalTrans_CostSales.createProjTransPosting|
|ProjBegBalJournalTrans_Fee.createProjTransPosting|
|ProjBegBalJournalTrans_OnAcc.createProjTransPosting|
|projCostControl.progressUpdate|
|ProjEstimatesDataContract.setRevenueSalesPrice|
|ProjForecastBudget.forecastCopy|
|ProjForecastBudget.forecastDelete|
|ProjForecastPostItemFixedInvest.checkEnterCost|
|ProjForecastTransferFromWBS.transferToForecast|
|ProjFormLetter. mainOnServer|
|ProjFormLetter.printPreview|
|ProjInvoiceDP.insertIntoProjInvoiceLocalizationTmp|
|ProjInvoiceDP.insertIntoProjInvoiceTmp|
|ProjInvoiceJournalCreate.creditMaxOk|
|ProjInvoiceJournalPost.initProposalUpdate|
|ProjLedger.newInventCost|
|ProjPlanVersionManager.copyActivityData|
|ProjPlanVersionsMananger.createDraftVersion|
|ProjProjectTransListPageInteraction.linkActive|
|Projtask.getCorrespondingTaskElementNumber|
|ProjValCheckTrans.validateMandatory|
|projWbsUpdateController.getNodesMapSortedByPath|
|PSAProjInvoiceDP.processLinesFromInvoiceJournal|
|psaProjQuotationSubmitSend.validateProjectDates|
|PSAQuotationsDP.insertPSAQuotationsTmp|
|PurchaseOrderResponseCreate.createPurchaseOrderResponseLines|
|PurchCancel.cancelMarkup|
|PurchCreateFromSalesOrder.preMatchIncludedLinesWithAgreements|
|PurchPackingSlipDP.setPurchPackingSlipDetailsTmp|
|PurchPackingSlipDP.setPurchPackingSlipHeaderTmp|
|PurchReceiptsListDP.setPurchReceiptsListDetailsTmp|
|PurchReceiptsListDP.setPurchReceiptsListHeaderTmp|
|PurchSummary.checkFormLetterId|
|ReqPlanCopy.insertLog|
|ResRollupActivityWriter::updateRollupTableWithLockedCapacityForActivityResource()|
|ResRollupAvailabilityWriter.updateRollupTableWithLockedCapacityForNamedResource()|
|SalesConfirmDP.setSalesConfirmDetailsTmp|
|SalesConfirmDP.setSalesConfirmHeaderTmp|
|SalesInvoiceController::main|
|SalesInvoiceDP.bankGroupIdName_CH|
|SalesInvoiceDP.bankZipCode_CH|
|SalesInvoiceDP.insertIntoSalesInvoiceHeaderFooterTmp|
|SalesInvoiceDP.insertIntoSalesInvoiceLocalizationTmp|
|SalesInvoiceDP.insertIntoSalesInvoiceTmp|
|SalesPackingSlipDP.setSalesPackingSlipDetailsTmp|
|SalesPackingSlipDP.setSalesPackingSlipHeaderTmp|
|SalesQuotationLineType.validateDelete|
|SalesQuotationLineType.validateWrite|
|SalesQuotationTableForm.CreateABSFromTemplate|
|salesQuotationTransferToProject.initParameters|
|SalesTable.initFromCustTableMandatoryFields|
|SalesTableListPageInteraction.setButtonSell|
|smmActivityCreate.createActivity|
|smmActivityCreate.new|
|smmActivityParentLinkTablee.insert|
|SubledgerJournalizerProjectExtension.createLedgerUpdate|
|Table CustBankAccount.validatePreNote|
|Table InventItemGTIN.formatGTIN|
|Table PriceDiscAdmTrans.checkItemRelation|
|Table PriceDiscAdmTrans.checkproductDimensions|
|Table ProjCategory.lookupProjCategoryType|
|Table ProjTable.validateWriteServer|
|Table PSAActivityEstimates.checkUpdateQuotationLine|
|Table PSAActivityEstimates.setSalesPriceFromCostPrice|
|Table PurchLine.setPriceDisc|
|Table PurchTable.internalTableIdToTableId_W|
|Table SalesLine.setPriceAgreement|
|Table Salesline.setPriceDisc|
|Table SalesQuotationLine.setPriceAgreement|
|Table SalesQuotationLine.setPriceDisc|
|Table SalesTable.setSalesOrderReleaseStatus|
|Table TmpCustVendTrans.createLineCreditLimit|
|Table TmpCustVendTrans.createLineCreditRemain|
|Table TmpCustVendTrans.createLineOrdered|
|Table TmpCustVendTrans.createLinePackingSlip|
|Table TmpCustVendTrans.createLineTotal|
|Table TmpCustVendTrans.insertTmpCustVendTransForCustBalance|
|Table TSTimeSheetLine.checkActivity|
|TSTimesheetLine::buildQuerySmmActivities|
|TsTimesheetPost.validatePost|
|VendProvisionalBalanceDP.insertVendProvisionalBalanceTmp()|
|VendTransQueryBuild::construct|
|VersioningPurchaseOrderResponse.archiveResponseLines|
|VersioningPurchaseOrderResponse.restoreLines|
|WhsCycleCountCreateLocation.run|
|WhsLoadReplenishment.calculateReplenishQty|
|WHSLoadTable::initPurchOriginDestination|
|WhsReplenishment.calculateReplenishQty|
|WhsRFControlData.validateAndUpdateWorkClusterLPScan|
|WhsShipConfirm.tmsRouteConfirmation|
|WhsWarehouseRelease.buildReleaseQuery|
|WhsWarehouseRelease.createLoadLines|
|WHSWaveTable.createWaveTableFromTemplate|
|WHSWorkExecute.createAdjustmentWork|
|WHSWorkExecute.createCountingJournal|
|WHSWorkExecute.createInventLine|
|WHSWorkExecute.executeShortPick|
|WHSWorkExecute.shortPickAdjustOut|
|WHSWorkExecuteDisplayPOReceiving.createWork|
|WorkTimeTable.lookupTime|

## Inline delegates

Inline delegates are now available. The most common way to use inline delegates is to split the method into more granular methods and enable extensibility events in the smaller methods.

|  Method |
| -------------|
|AssetCopy.run|
|AssetPost.post|
|AssetSplit.createTrans|
|AssetSplit.run|
|BankDepositCreateCancelJour.createDepositCancelJournal|
|BankPaymCancel.createCancellingCustTrans|
|BankPaymCancel.reverseSettlement|
|BankPaymCancel.run|
|BankPositivePayExport.initPositivePayQuery|
|BankPrintTestCheque.createTestCheque|
|BOMCalcItem.initListBOM|
|BOMCalcJob.runBOMCalculation|
|BOMRouteCopyJob.checkTo|
|BOMRouteCopyJob.main|
|BomRouteCopyJob::main|
|BomSearch.init|
|bomVersionActivate.run|
|CaseDetailForm.lookupParentCase|
|CaseDetailFormCreate.main|
|CaseUpdateStatus.changeStatus|
|CaseUpdateStatus_Close.updateStatus|
|ChequeDP.insertChequeTmp|
|Class SalesLineType.intercompanyMirror|
|Commission.run|
|CostControlPostingSourceDocumentLine.createCommittedCost|
|CostSheetPanel.build|
|CustAccountStatementExtController.insertCustAccountStatementExtTmp|
|CustAgingReportController.getReportName|
|CustAgingReportDP.insertCustAgingReportTmp|
|CustCollectionJourDP.collectionLetterTitle|
|CustCollectionJourDP.insertCustCollectionJourTmp|
|CustCollectionLetterCancel.main|
|CustCollectionLetterCreate.createJournal|
|CustCollectionLetterCreate.updateCreatedCollectionLetter|
|CustCollectionLetterPost.run|
|CustCollectionLetterPost.updateFee|
|CustInterestCancel.run|
|CustInterestCreate.createJournal|
|CustInterestCreate.insertCustInterestTrans|
|CustInterestCreate.insertCustInterestTransLine|
|CustInterestPost.updateCustInterestTransVoucherRef|
|CustInterestPost.updateFee|
|CustInvoiceDP::insertCustInvoiceTmp|
|CustInvoiceSpecDP::insertIntoTempTable|
|CustNsf.createFeeJournalTrans|
|CustOutPaymControlController.insert|
|CustPostInvoice.createJournalHeader|
|CustPostInvoice::createJournalHeader|
|CustSettlementPriorityProcessing.createTempData|
|CustSettlementPriorityProcessing.markTransByCreditNoteOnBillingClasses|
|CustTransOpenPerDateDP.insertCustTransOpenPerDateTmp|
|CustVendCreatePaymJournal.checkBlocked|
|CustVendCreatePaymJournal.dialogAddInvoiceSelectionCriteriaFields|
|CustVendCreatePaymJournal.runPaymentProposalGenerationProcess|
|CustVendCreatePaymJournal_Vend.UpdateQuery|
|CustVendFindSettlements.findSettledSettlements|
|CustVendOpenTransBalances.initAccountNumCurrencies|
|CustVendOpenTransBalances.new|
|CustVendOpenTransManager.initFromCaller|
|CustVendOpenTransManager.updateOriginatorForMarkedTrans|
|CustVendPaymProposal.createProposalLine|
|CustVendPaymProposalTransferToJournal.initLedgerJournalTransFromPaymLine|
|CustVendPaymProposalTransferToJournal.run|
|CustVendPaymProposalTransferToJournal.transferProposal|
|CustVendReversePosting.updateCustVendTrans|
|CustVendSettle.createSettlementForDebitOrCreditTrans|
|CustVendSumForPaym::Validate|
|CustVendVoucher.post|
|CustVoucher.createInvoiceJournal|
|DataEntityView FreeTextInvoiceEntity.insertFreeTextInvoiceLines|
|DataEntityView FreeTextInvoiceEntity.preTargetProcessSetBased|
|DimensionHierarchyHelper::getHierarchyTypeByAccountType|
|EcoResProductMasterManager.addProductDimensionValue|
|EcoResProductReleaseManager.createInventITable|
|EcoResProductReleaseManager.createInventItemSetupSupplyType|
|EcoResProductReleaseManager.setInventTableFields|
|EcoResProductTemplateManager.getBufferByDataSourceName|
|EcoResProductVariantManager.createProductVariant|
|Extend delegatestr(DirPartyPostalAddressFormHandler, defaultLocationRoles_delegate)|
|Form BankReconciliation: BankAccountReconcile::clicked|
|Form CustCreditLimitCreditPart.totalAgingByCompany|
|Form CustDirectDebitMandate.run|
|Form CustFormletterParameters.PrintMgMt.clicked|
|Form CustOpenTrans.init|
|Form CustOpenTrans.updateDesignStatic|
|Form CustOpenTrans: Button UpdateNow::clicked|
|Form CustOpenTrans::doesCallerAllowEdit|
|Form CustTable: CustTable::write|
|Form EcoResProductCreate.writeMoreFields|
|Form EcoResProductVariantsPerCompany: InventDimCombination::write|
|Form HierarchyTemplateCopying_Proj.copyEstimates|
|Form InventDimParmFixed: InventDimParm::create|
|Form InventOnhandReserve: InventSum::reserveNow|
|Form InventOnhandReserve: InventTransOriginMovement::movementOnOrderUnit|
|Form InventOnhandReserve: InventTransOriginMovement::movementReservOrderedUnit|
|Form InventOnhandReserve: InventTransOriginMovement::movementReservPhysicalUnit|
|Form InventTransRegister: TmpInventTransWMS::setEnabled|
|Form LedgerJournalTransCustPaym.accountNumModifiedPost|
|Form LedgerJournalTransCustPaym: Button ButtonSettlement::clicked|
|Form LedgerJournalTransVendPaym: buttonPaymReconciliation::Clicked|
|Form LedgerJournalTransVendPaym: PaymReconciliationReject::Clicked|
|Form MarkupTrans.MarkupTrans_DS.active()|
|Form MCRSalesQuickQuote.init|
|Form MCRSalesQuickQuote.prepareSearch|
|Form MCRSalesQuickQuote.tmpFrmVirtualInventDimId|
|Form MRCSalesQuickQuote.createLines|
|Form PriceDiscActual::init|
|Form ProcCategoryHierarchyManagement.init|
|Form ProjAdjustment.init|
|Form ProjAdjustment.selectAdjRecords|
|Form ProjCreditNoteSelect.canClose|
|Form ProjCreditNoteSelect.writeTmpFrmVirtual|
|Form ProjInvoiceProposalCreateLines.TransTypeSelectionCtrl.lookup|
|Form PurchTable: PurchTable::enableJournalButtons|
|Form SalesATP.SalesATP|
|Form SalesQuickQuote: InventDimCombination::getSetQuantyties|
|Form SalesQuickQuote: InventDimCombination::salesQty|
|Form SalesQuotationProjTable::SalesQuotationLine::ItemId::modified|
|Form SalesQuotationTable: SalesQuotationTable::write|
|Form SalesTable.modified|
|Form SalesTable.SalesTable_DS.linkActive|
|Form SalesTable.write|
|Form SalesTable: SalesLine::write|
|Form SalesTable: SalesTable::write|
|Form TMSRateRouteWorkbench.updateRoutes|
|Form VendEditInvoice: VendInvoiceInfoTable.write|
|Form WhsWorkTable.setFilter|
|FormLetterJournalPost.post|
|FormLetterService.run|
|Forms WHSLoadPlanningWorkbench.init|
|Forms WHSLoadPlanningWorkbench.restoreQuery|
|FreeTextInvoiceDP::insertIntoFreeTextInvoiceHeaderFooterTmp|
|From ProjTableCreate.init|
|HierarchyCreate.run|
|HierarchyTemplateCopyingDialog_proj.main|
|InterCompanyPost.formLetterCollect|
|InventAgeDimDP.calcAllDim|
|InventAgeDimDP.insertInventAgeDimTmp|
|InventAgeDimDP.insertOrMergeInventAgeDimTmp|
|InventCountCreate.dialog|
|InventDimCtrl_Frm_Lookup.initDisplayOrderDataSource|
|InventDimPhysDP.processReport|
|InventDimViewContract|
|InventMovement.updateSerialNumIssue|
|InventMovement.updateSerialNumReceipt|
|InventMovement::updateLedgerPhysical|
|InventOnhandReserve.updateReserveNow|
|InventSumDateEngine.clearNotSelectedDimensions|
|InventTransferMulti.insert|
|InventUpd_Picked.updatePickMore|
|InventUpd_Reservation.updateReserveLess|
|InventUpdateOnhand.checkOnHand|
|InventValueReportContract|
|InventValueReportController|
|InventValueReportPopulateResource.initReportLines|
|JmgPostStandardSystem.postProjTime|
|JournalFormTable.designLookupJournalName|
|JournalFormTable.initAllOpenPostedFromCaller|
|LedgerBalancesBase.CalculateBalance|
|LedgerInAccountStatement.main|
|LedgerJournalCheckPost.createReverseEntryJournalLine|
|LedgerJournalCheckPost.postJournal|
|LedgerJournalCheckPost.runInternal|
|LedgerJournalCheckPost::updateSystemBlockCheckedPostedJournal|
|LedgerJournalMultiPost.multiSelectPost|
|LedgerJournalTrans table.checkBankAccounts|
|LedgerJournalTransUpdateVend::postNewVendorVoucher|
|Map ProjTableWizardCtrl::insertDB|
|Map SalesPurchLine.calcPrice2LineAmount|
|Map SalesPurchLine.resetPriceAgreement|
|Map SalesPurchLine.setPriceAgreement|
|MarkupAllocation.sumValue|
|MCRInventSearch.executeSearch|
|MCROrderEventTable.Insert|
|McrPriceHistoryForm.insertPriceHistory|
|PmfFormCtrl.initPost|
|PriceDiscAdmCheckPost.checkForOverlapsAndGaps|
|PriceDiscAdmCopy.updateNow|
|ProdJournalCheckPostProd::checkTrans|
|ProdJournalCheckPostProd::postTransLedger|
|ProdJournalCheckPostProd::postVoucher|
|ProdJournalCheckPostRoute.updateProdRouteScheduling|
|ProdJournalCreateProd.createLines|
|ProdJournalCreateRoute.createLinesProdRoute|
|ProdJournalFormTable.datasourceExecuteQueryPre|
|ProdMultiBOMCalc.run|
|ProdMultiCostEstimation.run|
|ProdMultiHistoricalCost.run|
|ProdMultiRelease.insert|
|ProdMultiRelease.run|
|ProdMultiReportFinished.main|
|ProdMultiReportFinished.run|
|ProdMultiSchedulingJob.run|
|ProdMultiSchedulingOperation.run|
|ProdMultiStartUp.run|
|ProdPurch.createPurchTable|
|prodTableChangeQtySched.performActionFromDefaultValues|
|prodTableChangeQtySched.performActionFromPrompt|
|ProdUpdCostEstimation.costEstimateOperations|
|ProdUpdCostEstimation.createPurchLine|
|ProdUpdReportFinished.run|
|ProdUpdReportFinished.updateBOMConsumption|
|ProdUpdStartUp.updateBOMConsumption|
|ProdUpdStartUp.updateRouteConsumption|
|ProjAdjustmentSelect.doTrans|
|ProjAdjustmentSelect.newQuery|
|ProjAdjustmentSelect.Run|
|ProjAdjustmentUpdate.checkTransChanged|
|ProjBudgetTransactionsManager.adjustBudget|
|ProjCopyForecastItem.copyToSalesLine|
|ProjCOstControl.createActualCosts|
|ProjCOstControl.createActuals|
|ProjCostControl.createAverageForRemaining|
|ProjCostControl.createCommittedCosts|
|ProjCostControl.createForecastCosts|
|ProjCostControl.queryCommittedCosts|
|ProjCostControl.queryProjTransPosting|
|ProjCostControl.run|
|ProjCostControl.validate|
|ProjForecastBudgetCopy.do_cost|
|ProjForecastBudgetCopy.do_empl|
|ProjForecastBudgetCopy.do_OnaCC|
|ProjForecastBudgetCopy.do_Revenue|
|ProjForecastBudgetCopy.do_Sales|
|ProjForecastBudgetCopy.initQuery|
|ProjForecastBudgetCopy.validate|
|ProjForecastBudgetDelete.initQuery|
|ProjForecastTransferFromWbs. transferItemToForecast|
|ProjFundingEngine.allocate|
|ProjFundingEngine.isAmountWithinFundingLimits|
|ProjFundingEngine.updateFundingLimits|
|ProjInvoiceChooseNormal.dialog|
|ProjInvoiceJournalCreate.initTotals|
|ProjInvoiceJournalPost.createProjInvoiceCost|
|ProjInvoiceJournalPost.createProjInvoiceEmpl|
|ProjInvoiceJournalPost.createProjInvoiceItem|
|ProjInvoiceJournalPost.createProjInvoiceOnAcc|
|ProjInvoiceJournalPost.createProjInvoiceRevenue|
|ProjInvoiceJournalPost.postCustVend|
|ProjInvoiceProposalCreateLines.runSalesLineQuery|
|ProjInvoiceProposalCreateLines.runTransactions|
|ProjInvoiceProposalInsertLines.run|
|ProjInvoiceProposalNormalPeriodic.createParameters|
|ProjInvoiceProposalPeriodic.dialog|
|ProjJournalCheckPost.processHourJournalResourceRateCost|
|ProjLedger.initFromProjectPostingTransaction|
|ProjLedgerUpdate.insert|
|ProjPlanVersionsManager.copyTasks|
|ProjProposalTotals.calc|
|ProjSplitBill.buildRuleQR|
|ProjSplitBill.split|
|ProjStatisticCalc.mapPSAEntityToTmpProjStatistic|
|ProjValCheckTrans.setVariablesFromBuffer|
|PsaCustomerRetention.createFeeTransaction|
|PsaGenerateQuotationLines.createSalesQuotationLines|
|PsaProjInvoiceDP::insertPSAProjInvoiceHeaderTmp|
|PsaProjInvoiceDP::insertPSAProjInvoiceTmp|
|PSARetentionRelease.insertLineRecords|
|PurchAgreementGenerateReleaseOrder.check|
|PurchAutoCreate_RFQ.createPurchLine|
|PurchAutoCreate_Sales.createLine|
|PurchCancel.cancelMarkup|
|PurchCancel.run|
|PurchCopying.copyLine|
|PurchCreateFromSalesOrder.mcrDropChipCreateTmpFrmVirtual|
|PurchCreateFromSalesOrder.preMatchIncludedLinesWithAgreements|
|PurchFormLetter.PrePromptInit|
|PurchformLetter::Main|
|PurchFormLetter::MainOnServer|
|PurchFormletterParmData.createParmTable|
|PurchFormletterParmDataInvoice.chooseLinesFromPurchSelectLinesManager|
|PurchLineType.intercompanyMirror|
|PurchLineType_Project.initFromInventTable|
|PurchLineType_WithMultipleDeliveries.recalculateDeliveryScheduleOrderLine|
|PurchPackingSlipDP::setPurchPackingSlipDetailsTmp|
|PurchPackingSlipDP::setPurchPackingSlipHeaderTmp|
|PurchPurchaseOrderDP.createData|
|PurchPurchaseOrderDP.initializePurchPurchaseOrderHeader|
|PurchPurchaseOrderDP.processReport|
|PurchPurchaseOrderDP.setPurchPurchaseOrderDetails|
|PurchPurchaseOrderDP::setPurchPurchaseOrderDetails|
|PurchPurchaseOrderDP::setPurchPurchaseOrderHeader|
|PurchReceiptsListDP::setPurchReceiptsListDetailsTmp|
|PurchReceiptsListDP::setPurchReceiptsListHeaderTmp|
|PurchReqTable2LineField.lineUpdateDescription|
|PurchRFQCaseAutoCreate.newAutoCreate|
|PurchRFQCompare.BuildReplyLineList|
|PurchRFQSendDP::processReport|
|PurchRFQSendJournalCreate.createOrUpdateRFQ|
|PurchTable2LineField.getFieldDescription|
|PurchTableType.intercompanyMirror|
|ReqActionApplyPurchaseOrder.applyActionToReferencedOrder|
|ReqBOMCreate.createBOM|
|ReqCalc.mcrInsertItemContinuitySales|
|ReqCalcScheduleItemTable.run|
|ReqSetupDim.setReqItemTableGrouped|
|ReqSupplyDemandScheduleModel.executeQuery|
|ReqSupplyDemandScheduleModel.insertPeriodValue|
|ReqTransPoMarkChangeToRFQ.change2RFQ|
|ReqTransPoMarkFirm.create|
|ReqTransPoMarkFirm.createInventTransferLine|
|ReqTransPoMarkFirm.createPurchLine|
|ReqTransPoMarkFirm.createPurchTable|
|ReqTransPoMarkFirm.firmSelectedPlannedOrders|
|RouteCopyToProd.copyTo|
|SalesAgreementGenerateReleaseOrder.check|
|SalesAgreementGenerateReleaseOrder.main|
|SalesAutoCreate_ReleaseFromAgreement.createSalesLine|
|SalesAutoCreate_ReleaseFromAgreement.createSalesTable|
|SalesAutoCreate_ReleaseOrder.createSalesTable|
|SalesConfirmDP.setSalesConfirmDetailsTmp|
|SalesConfirmDP.setSalesConfirmHeaderTmp|
|SalesConfirmDP::setSalesConfirmDetailsTmp|
|SalesConfirmDP::setSalesConfirmHeaderTmp|
|SalesCopying.copy|
|SalesCopying.copyHeader|
|SalesCopying.deleteLines|
|SalesCopying_CreditNote.copy|
|SalesCopying_CreditNote.copyHeader|
|SalesFormLetter.mainOnServer|
|SalesFormLetter.reselect|
|SalesFormletterParmData.createParmLine|
|SalesFormletterParmData::createParmTable|
|SalesInvoiceController::outputReport|
|SalesInvoiceDP.useExistingReportData|
|SalesInvoiceDP::insertIntoSalesInvoiceHeaderFooterTmp|
|SalesInvoiceDP::insertIntoSalesInvoiceTmp|
|SalesLineExplodeBOM.explode|
|SalesLineType.canPickingListBeRegistered|
|SalesLineType.delete|
|SalesLineType.initDimensionsSpecificDefaulting|
|SalesLineType.initFromSalesLine|
|SalesLineType.interCompanyMirror|
|SalesLineType.setSalesStatus|
|SalesLineType.validateField field  ShippingDateRequested and ShippingDateConfirmed|
|SalesPackingSlipDP.printDimHistory|
|SalesPackingSlipDP::setSalesPackingSlipDetailsTmp|
|SalesPackingSlipDP::setSalesPackingSlipHeaderTmp|
|SalesPurchTableToLineUpdate.update|
|SalesQuantity_PackingSlip.calcQtySales|
|SalesQuantity_PickingList.calcQtySales|
|SalesQuotationConfirmationDP::setSalesQuotationDetailsTmp|
|SalesQuotationConfirmationDP::setSalesQuotationHeaderTmp|
|SalesQuotationCopying.buildTreeControl|
|SalesQuotationCopying.Copy|
|SalesQuotationDP::setSalesQuotationDetailsTmp|
|SalesQuotationDP::setSalesQuotationHeaderTmp|
|SalesQuotationEditLinesForm.mainOnServer|
|SalesQuotationEditLinesForm_Proj_Confirm.queryBuildSalesQuotationTable|
|SalesQuotationEditLinesForm_Proj_Send.queryBuildSalesQuotationTable|
|SalesQuotationEditLinesForm_Sales_Confir.updateNow|
|SalesQuotationEditLinesForm_Sales_Confirm.createSalesLine|
|SalesQuotationEditLinesForm_Sales_Send.checkLines|
|SalesQuotationJumpRef.main|
|SalesQuotationLineType.initFromSalesQuotationLine|
|SalesQuotationLineType_Proj.validateWrite|
|SalesQuotationProjLinkWizard.transferForecastToProject|
|SalesQuotationProjLinkWizard.transferItemReq|
|SalesQuotationTransferToProject.transferItemsToForecast|
|SalesQuotationTransferToProject.transferItemsToItemReq|
|SalesQuotationUpdate.getCallerModuleFromParm|
|SalesTableForm.initValues|
|SalesTableForm_DeliverySchedule.updateSalesLineTable|
|SalesTableType.intercompanyMirror|
|SalesTableType.update|
|SalesTableType.validateDelete|
|smmSalesCustItemStatisticsDP::processReport|
|Table CaseDetailBase.validateWrite|
|Table CustCollectionLetterJour.updateCollectionLetterCodeCustTrans()|
|Table EcoResProductTranslation.queryAddCompanyLanguage|
|Table InventLocation::lookupBySiteIdAllTypes|
|Table InventPosting.accountGroup|
|Table InventPosting.accountItemLedgerDimension|
|Table InventPosting.deleteFromCust|
|Table InventPosting.deleteFromVend|
|Table InventTable.defaultProductDescription|
|Table InventTable.defaultProductName|
|Table InventTable.lookupBOMId|
|Table InventTrans.updateMarkReqTransCov|
|Table PaymTerm.due|
|Table ProdBOM.updateStartUp|
|Table ProdBOM.updateSubPurch|
|Table ProdJournalBOM.insertJournalCreate|
|Table ProdJournalBOM.lookupTransId|
|Table ProdTable.validateRouteId|
|Table ProjBegBalJournalTrans_CostSales.postProjTransactionCost|
|Table ProjBegBalJournalTrans_CostSales.postProjTransactionHour|
|Table ProjBegBalJournalTrans_CostSales.postProjTransactionItem|
|Table ProjBegBalJournalTrans_Fee.postProjTransaction|
|Table ProjBegBalJournalTrans_OnAcc.postProjTransactionCost|
|Table PurchLine.initBarCode|
|Table PurchLine.priceDateDelegate|
|Table PurchLine.setPriceDisc|
|Table PurchTable.updateFromPurchReqLineMap|
|Table ReqPO.updateBOMRoute|
|Table ReqTrans.bulkInitFromInventTransOrigin|
|Table RouteOpr.validateFieldValue|
|Table RouteVersion.checkExistInventSiteId|
|Table SalesLine.checkPriceDate|
|Table Salesline.convertCurrencyCode|
|Table SalesLine.convertToDeliverySchedule|
|Table SalesLine.createFromTmpFrmVirtualIL|
|Table SalesLine.createReplacement|
|Table SalesLine.createSalesLine|
|Table SalesLine.expandBOM|
|Table Salesline.modifyInventDimSet|
|Table SalesLine.priceDateDelegate|
|Table salesLine.setPriceAgreement|
|Table Salesline.splitReturnLine|
|Table SalesLine::createFromSalesQuotationLine|
|Table SalesQuotationLine.createFromTmpFrmVirtual|
|Table SalesQuotationLine.modifiedField|
|Table SalesQuotationLine.modifyInventDim|
|Table SalesQuotationTable.copyAddressToLine|
|Table SalesQuotationTable.lookupTemplateName|
|Table SalesTable.copyAddressToLine|
|Table SalesTable.copyRMALines|
|Table SalesTable.copyThirdPartyBillingAddressToLine|
|Table SalesTable.existingJournals|
|Table SalesTable.initFromCustTableIL|
|Table SalesTable.initFromProjTable|
|Table SalesTable.initFromSalesQuotationTable|
|Table SalesTable.unlinkAgreement|
|Table WHSAccountItemStatusDefault.checkModuleAccountNum|
|Table WHSLoadLine.delete|
|Table WHSLoadLine.updateReleaseQty|
|Table WhsLoadLine.validateQty|
|Table WHSLoadTable.assignOriginInfo|
|Table WHSProdTable.pickMore|
|Table WhsWorkTabke.lockUnLockWork|
|Table WMSBillOfLading.constructFromInvoice|
|Table WMSBillOfLading.constructFromPackingSlip|
|Table WMSBillOfLading.constructFromShipment|
|Table WMSOrderTrans.loopWMSOrderTransMulti|
|Table WrkCtrActivityRequirementSet.copyRequirements|
|Table WrkCtrActivityRequirementSet.schedulingProperties|
|Tables SalesLine/Methods/setPriceDisc|
|TamDeductionUpdate_Deny.update|
|TmsProcessXML_Container.readShipContainer|
|TmsProcessXML_Shipment.readShipContainer|
|TradeInterCompany.insertInterCompanyInventDim|
|TradeInterCompanyConv.axPurchItemId|
|TradeInterCompanyConv.axSalesItemId|
|TransactionReversal_Asset.reversalBook|
|TransactionReversal_Cust::reversal|
|TransactionReversal_CustVend.createCustVendTrans|
|VendInvoiceDocumentDP::insertVendInvoiceDocumentTmp|
|VendInvoiceTableToLineUpdate.convertPurchTableFieldToVendInvoice|
|VendorInvoiceLineSourceDocLineItem.calculateSourceDocumentAmountMap|
|VersioningDocument.change|
|VersioningPurchaseOrder.createChangeRequest|
|WhsCycleCountCreateThreshold.processCycleCountThresholdItem|
|WHSInventOnHandReserve.changeReservation|
|WHSLaborStandards.findLaborStandardByItem|
|WHSLoadLine.update|
|WHSLoadTable.tmsLoadConfirmation|
|WHSLocationBuild|
|WHSLocationDirective.findLocation|
|WHSLocationDirective.findPickPutLocation|
|WHSLocationDirectiveActionQuery.modifyPickLocDirActionQuery|
|WHSPool.pickFromWorkCenter|
|WHSPostEngineBase.prodCreateWork|
|WHSPostEngineBase.prodPickQty|
|WhsRfControlData.getClusterPickQty|
|WHSRFControlData.processControl|
|WhsShipConfirm.canShipConfirm|
|WHSShipConfirm.createInventTransferParmLineFromContainerTable|
|WHSShipConfirm.runTransferShip|
|WhsShipConfirn.validateAllAllowedForOverOrUnderdeliveryWorkQtyHasBeenPicked|
|WHSSplitWork.splitWork|
|WHSWorkClusterTable.cleanupCluster|
|WHSWorkCreateProdPut.insertProdParmforCoByProduct|
|WHSWorkCreateProdPut.insertProdParmforProdItem|
|WhsWorkExecute.getFirstOpenLineSystemDirected|
|WHSWorkExecute.overPickByItem|
|WHSWorkExecute.putAwayToLocation|
|WHSWorkExecute.scanLicensePlate|
|WHSWorkExecuteDisplay.buildPORecTrackingDimensions|
|WhsWorkExecuteDisplayCycleCount.findOrCreateCycleCountWorkLines|
|WhsWorkExecuteDisplayLPReceiving.displayForm|
|WHSWorkExecuteDisplayMixedLPReceiving.displayForm|
|WHSWorkLine.cancelLineMultiPick|
|WHSWorkLine.cancelLinePartial|
|WMSArrivalCreateJournal.createWMSJournalTrans|
|WMSArrivalCreateJournal.createWMSJournalTransFromTmp|
|WMSArrivalOverviewGeneration.buildReturnOrderFromSalesLine|
|WMSJournalCheckPostReception.checkReference|
|WMSJournalTransUpdateSerialId.dialog|
|WmsPickingList_OrderPickDP::insertIntoTempTable|
|WrkCrtScheduler.writeJobCapacityReservations|
|WrkCtrApplicableResourceQuery.query|
|WrkCtrlScheduler_Prod.loadJobsDetail|
|WrkCtrlScheduler_Prod.saveOrder|
|WrkCtrlScheduler_Proj.saveOrder|
|WrkCtrlScheduler_Proj.writeJobData|
|WrkCtrReservedSum.find|
|WrkCtrScheduler.computeJobTimes|
|WrkCtrScheduler.insertWrkCtrCapResUsingInsertList|
|WrkCtrScheduler.writeJobCapacityReservations|
|WrkCtrScheduler.writeJobData|

## SQL operations made extensible

Application code with embedded SQL statements cannot be modified through extensions. Changes have been made to the standard application to enable extensibility in the methods listed in the following table. This has commonly been enabled by transforming embedded SQL statements into query objects that support extending how SQL statements are built in these methods.

|  Method |
| -------------|
|CustCollectionLetterCreate.updateAllExisting|
|CustCollectionLetterCreate.updateExisting|
|CustProvisionalBalanceDP.insertCustProvisionalBalanceTmp|
|CustProvisionalBalanceDP.processReport|
|CustSettlementPriorityProcessing.createTempData|
|DirPartyTable.getLocationFromRole|
|InventQualityOrderTable.createInventQualityOrderLines|
|InventTransIdSum::calcSum|
|InventTransIdSum_InventLocation::calcSum|
|InventTransReference::setRefTrans|
|Markup.insertMarkupTrans|
|Markup.mcrCopyForReturn|
|PriceDisc.findDisc|
|PriceDisc.findPriceAgreement|
|PurchFormLetterParmDataInvoice.createLineProject|
|ReqPlanCopy.copyReqTransAndReqTransCov|
|ReqPlanCopy.copyReqTransKeep|
|ReqPlanCopy.copyWrkCtrCapRes|
|ReqPlanCopy.copyWrkCtrCapResForReqPO|
|SalesCopying.deleteLines|
|SalesLineType::deliveredInTotal|
|SalesTableType.parmPickingListRegistrationEnumerable|
|SalesTableType_Sales.canPickingListBeUpdated|
|SalesUpdateRemain.canclRemainderOnOpenSalesLines|
|SubledgerJournalizer.createSummaryFromJournalAccountEntry|
|SubledgerJournalizer.loadAccountingDistributionTmpJournalize|
|SubledgerJournalizer.loadFinalizeSubledgerJournalTmpDetail|
|SubledgerJournalizer.loadStandardSubledgerLedgerJournalTmpDetail|
|SubledgerJournalizer.loadSubledgerJourTmpDetailWithRelieving|
|SubledgerJournalizer.recordSubledgerJourAccEntriesForRounding|
|SubledgerJournalizer.summarizeJourAccountEntryDetailForRound|
|SubledgerJournalTransferCommand.insertGeneralJournalAccountEntryRelatedDetail|
|TmsProcessXML_Base.writeShipDeliveryAccessorials|
|VendProvisionalBalanceDP.insertVendProvisionalBalanceTmp|
|VersioningPurchaseOrder.archivePurchLine|
|WhsLoadPostEngineBase::createShipments|
|WHSPackForm.getShipmentId|
|WHSPostEngineBase.executeWaveSteps|
|WhsPostPackingSlip.preparePackingSlipPosting|
|WhsWarehouseRelease.createShipments|
|WhsWarehouseRelease::createOrConsolidateShipmentForSalesOrder|

## Maps enabled for extensibility

New patterns have been introduced for maps implementation that will allow you to add field and methods by extensions. Details on how this is done is available in the documentation both with maps that are used as interfaces and for versioning implementations.

The following table lists the maps and related tables where changes have been applied for enabling extensibility.

| Maps and tables|
| -------------------|
|Map CustVendInvoiceTrans|
|Map SalesPurchLine extensions or inheritance|
|Map SalesPurchTable|
|Map VendDocumentLineMap|
|Table PurchLine mappings|
|Table PurchLineHistory mappings|

## Inventory dimensions

This release introduces a new model for adding inventory dimensions. In previous releases it was not practical to support customization for new inventory dimensions if that required extending every SQL statement that included inventory dimensions. Instead, we have added 10 inventory dimensions without any specific designated usage. Partner solutions will code through indirection models that hold their code, and other models are made for individual implementation projects that deploy one or more of the prefabricated inventory dimensions toward use in a partner solution. Documentation will be available on how to implement with inventory dimensions under this model, and release of a sample app with a Flavor dimension will help you learn about the new model. The new inventory dimension can be freely deployed and used as either product dimensions or tracking dimensions.

The changes have led to changing multiple places across the application, including what is shown in the following list.

| Change |
| -------------|
|Extensible Product Dimensions|
|Form WHSInventOnHandReserve.updateInventDimFixedControls|
|InterCompanyInventDim: Condition with throw|
|InventDimFieldsMap - Added field|
|Inventory dimension InventUpdateOnhand::checkOnHand|
|Inventory Dimensions - Table InventDim.create|
|InventTransferUpdShip.populateIssueReceiptDimensions|
|Map InventInventoryDimensionEntityFieldsMapping::resolveInventDim()|
|Rename InventDimFieldsMap::getFieldIdForDimensionOnMappedTable to inventoryDimensionFieldIdOnMappedTable()|
|Table BOMConsistOfTmp mappings|
|Table BOMPartOfTmp mappings|
|Table EcoResTrackingDimensionGroup.isDimFieldTrackingDimension|
|Table InterCompanyInventDim mappings|
|Table InventAgeGroupDimTmp mappings|
|Table InventCheckRecieptCostPricePcsTmp mappings|
|Table InventCostTmpTransBreakdown mappings|
|Table InventCountStatisticsTmp mappings|
|Table InventDim mappings|
|Table InventOnhandTmp mappings|
|Table InventPhysicalPerWarehouseTransTmp_IT mappings|
|Table InventPriceOverviewTmp mappings|
|Table InventSumCriticalTmp mappings|
|Table InventSumDateTransReport mappings|
|Table InventSumDeltaDim mappings|
|Table InventTable mappings|
|Table InventTransferOrderOverviewTmp mappings|
|Table InventValueReportTmpLine mappings|
|Table ProdPickList mappings|
|Table SalesInvoiceTmp mappings|
|Table WHSPurchLine.registerPurchaseLine|
|Table WHSTmpCompleteWorkLine.lookupBatch|
|Table WHSTmpCompleteWorkLine.lookupTargetLicensePlateId|
|Table WMSCheckABCZonesTmp mappings|
|Table WMSPickingList_OrderPickTmp mappings|
|Table WMSPickingListReportTmp mappings|

## Metadata changes to enable extensibility

The following table lists changes made for enabling extensibility for specific metadata on these objects. These changes vary from instance to instance, you can consult the specific implementation to review the changes.

| Change |
| -------------|
|CountryRegionCodes property|
|CustCustomerEntity|
|EcoResProductCategoryAssignmentEntity made public|
|Form AssetSplit : FormControls|
|Form CustCollections.Cases|
|Form CustGroup|
|Form LedgerJournalTransCustPaym - menu item button auto declaration|
|Form LedgerJournalTransVendPaym - menu item button auto declaration|
|Table DimensionAttributeValueSetItem|
|Table EcoResReleasedProductCreationStaging missing ReplacementKey like other staging tables.|
|Tables SubledgerJournalAccountEntry(Tmp...)|
|View SubLedgerJournalAccountEntryView|

## Other changes

The following table lists additional changes that have been made for extensibility.

| Change |
| -------------|
|CustCollectionLetterCreate|
|CustCollectionLetterPost|
|Extensibility approach for number of decimal places for currency|
|Extensible edt decimal places:  AssetDepreciationAmountUnit|
|Form Extension - DirPartyTable - registerOverrideMethod jumpRef|
|Form ProjCategoryLookup|
|Method signature changed: InventPostingSetupCache|
|Method signature changed: Table ProjCostPriceExpense.find|
|Method signature changed: Table ProjCostPriceExpense.findCostPrice|
|Method signature changed: Table ProjCostSalesPrice.find|
|Method signature changed: Table ProjCostSalesPrice.findCostSalesPrice|
|Method signature changed: Table ProjHourCostPrice.Find|
|Method signature changed: Table ProjHourCostPrice.FindCostPrice|
|Method signature changed: Table ProjHourSalesPrice.find|
|Method signature changed: Table ProjHourSalesPrice.findHourSalesPrice|
|New Quantity EDT added to ApplicationCommon|
|Other: New base enum for Price & Discount framework|
|Set Alternative Key = Yes to enable reference group lookups|
|Use of interface EcoResIProductCrossTableData|

## Bugs

The following table lists changes that were requested for extensibility but were acknowledged as bugs and fixed in the standard application.


|                                   Change                                   |
|----------------------------------------------------------------------------|
|             class CaseUpdateStatus_Close, method changeStatus              |
|               Incorrect relation on CustCollectionLetterJour               |
|            Other: Bug fix on CompanyHelper.testCreateParameter             |
| Table CustCollectionLetterJour - class cancelCollectionLetterCodeCustTrans |



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
