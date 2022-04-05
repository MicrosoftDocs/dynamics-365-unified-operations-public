---

# required metadata
title: Extensibility changes in Finance and Operations, Enterprise edition (July 2017)
description: This is a list of extensibility features that were implemented in the (July 2017).
author: FrankDahl
ms.date: 11/08/2017
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
ms.search.validFrom: 2017-02-28
ms.dyn365.ops.version: Platform update 4

---

# Extensibility changes in Finance and Operations, Enterprise edition (July 2017)

[!include [banner](../includes/banner.md)]

This is a list of extensibility features that were implemented in the Dynamics 365 for Finance and Operations, Enterprise edition (July 2017). This version was released in July 2017 and has a build number of 7.2.11792.56024. For more information about the schedule of changes that support extensibility, see [Application extensibility roadmap](extensibility-roadmap.md).

## Soft-sealed application models

The following application middle-tier models were soft-sealed in this release. Overlayered code in these models will generate warnings on compilation.

| Category       | Model         |
| --------------- |-------------|
| Application Frameworks | CaseManagement |
| Application Frameworks | Dimensions |
| Application Frameworks | Directory |
| Application Frameworks | Organization |
| Application Frameworks | Currency|
| Application Frameworks | ApplicationCommon|
| HCM Core Models| 3817938
|Tax Models |Tax |
|Tax Models |Tax Books |
|Tax Models |Tax Books Application Suite Integration |
|Tax Models |Tax Engine Application Suite Integration |
|Tax Models |Tax Engine Configuration |
|Tax Models |Tax Engine Interface |
|Tax Models |Tax Engine Runtime Generation |
|Tax Models |TaxEngine |
| Source Document Models |SourceDocumentation |
| Source Document Models |SourceDocumentationTypes |
| Ledger Models |GeneralLedger |
| Ledger Models |Ledger |
| Ledger Models |Subledger |
| Middle Tier SCM Models | CostAccounting |
| Middle Tier SCM Models | CostAccountingAX |
| Middle Tier SCM Models | SCMControls |
| Middle Tier SCM Models | SCMMobile |
| Middle Tier SCM Models | UnitOfMeasure |
| Middle Tier SCM Models | WMSAdvancedMigration|
| Middle Tier SCM Models | InventoryDimensionConversion|
| Workspaces| ApplicationWorkspaces |
| Finance| Fiscalbooks |
| Management tools | DataUpgrade |

## Hard-sealed application models

The following application middle-tier models were hard-sealed in this release. Overlayered code in these models will generate errors on compilation.

| Category       | Model         |
| --------------- |-------------|
| Accounts Payable | AccountsPayableMobile |
| Finance | FinancialReportingEntityStore|
| Tools | PerformanceTool |
| Expenses | ExpenseMobile |
| GER | ElectronicReporting|
|GER | ElectronicReportingCore|
|GER | Electronic Reporting Application Suite Integration|

## Enumerations that are now extensible

The following changes were made to support extending enumerations:
- Many enumerations in the standard application have been made extensible. An enumeration is made extensible by setting two properties on the enumeration. The **IsExtensible** property is set to **Yes**, and the **UseEnumValue** property is set to **No**. 
- Some enumerations represent state. New façade methods have been added to help enable adding enumeration values by extension. For information about how to extend an enumeration, see [Add values to enums through extension](add-enum-value.md).
- Some application code that uses enumerations was changed to support extensibility. Common changes include:
    + Removing **throw** exception statements in the default case of a switch to allow post-event subscription.
    + Adding **SysExtension** support for extension.
    + Adding explicit delegates.


| Enumeration|
| --------------- |
|AgreementState|
|AssetAccountType|
|AssetTransTypeJournal|
|BankAccountType|
|BankFormat|
|BarcodeContentType|
|BarcodeCoverPageEntityType|
|BarcodeType|
|BOMCalcCostingVersionUpdate|
|BOMCalcCostPriceUsed|
|BOMCalcSalesPriceUsed|
|BOMCalcType|
|BOMCheckLevel|
|BOMCopyContext|
|BOMCopyMethod|
|BOMCopyType|
|BOMCostCalculationMethod|
|BOMExplode|
|BOMRouteCopyDataType|
|BOMVersionFilter|
|BudgetReservation_BusinessEvent_PSN|
|BudgetReservation_SourceDocument_PSN|
|BudgetReservation_SourceDocumentLine_PSN|
|CatCallMethod|
|CatContentType|
|CatImportStatus|
|CatMaintenanceRequestWfStatus|
|CatProcurementErrorCode|
|CatPurchaseStatus|
|CatUserReviewApprovalStatus|
|CatVendorCatalogFileUploadType|
|CatVendorCatalogTemplateCategory|
|CatVendorCategoryHierarchyType|
|CatVendorConfigurationForImport|
|CatVendorLegalEntityStatus|
|CatVendorSiteType|
|ConsignmentReplenishmentOrderLineStatus|
|ConsignmentReplenishmentOrderStatus|
|CostBreakdown|
|CostCalculationCompareProductType|
|CostCalculationRole|
|CostCalculationState|
|CostCalculationSurchargeSubtype|
|CostingActivationType|
|CostingVersionCompareTo|
|CostingVersionPriceType|
|CostPriceBase|
|CostProfitSet|
|CostSalesPriceDisplay|
|CostSheetNodeListType|
|CostSheetPanelView|
|CostSheetProdFlowMode|
|CostStatementCacheAggregationAfter|
|CostWIPStatementCategory|
|CustPaymentValidate|
|CustSpecTransOverviewFormMode|
|CustTransRefType|
|CustVendPaymentStatus|
|CustVendTransportPointTypeTransfer|
|DlvScheduleMarkupConversionMode|
|EcoResAttributeModifier|
|EcoResCategoryAttributeModifier|
|EcoResCategoryChangeStatus|
|EcoResCategoryHierarchyModifier|
|EcoResCategoryNamedHierarchyRole|
|EcoResProductImageUsage|
|EcoResProductListPage|
|EcoResProductPerCompanyListPageType|
|EcoResProductTemplateType|
|EcoResReleaseProductToCompany|
|EcoResVariantConfigurationTechnologyType|
|ECPsalesOrdersViewType|
|EPCSSProductViewType|
|EUSalesTransMethod|
|FormLetterType|
|GanttCallerWrkCtr|
|GanttSetupType|
|GanttTimeUnit|
|GanttWrkCtrDisplayColumnsType|
|IntercompanyGoodsInTransitLineType|
|InterCompanyGoodsInTransitOrigin|
|InventAccountType|
|InventAccountTypeStdCostVariance|
|InventAdjustmentBy|
|InventAgingView|
|InventBatchJournalType|
|InventCostBundleState|
|InventCostCostDistribution|
|InventCostTransactionCategory|
|InventCostTransRefType|
|InventCountCode|
|InventItemCostingType|
|InventItemLookupDefaultTab|
|InventItemOrderSetupCallerType|
|InventItemOrderSetupType|
|InventItemPriceCompareLevel|
|InventItemPriceFilterType|
|InventItemPriceType|
|InventJournalOwnershipChangeLineCreateQueryStatusIssue|
|InventJournalType|
|InventLedgerConflictModule|
|InventLocationType|
|InventMovSubType|
|InventNonConformanceApproval|
|InventNonConformanceHistoryType|
|InventNonConformanceType|
|InventParameters|
|InventPhysicalReduction|
|InventRefType|
|InventReleaseOrderPickingType|
|InventReportDimHistoryLogType|
|InventStdCostConvItemStatus|
|InventStdCostPeriodType|
|InventSumFields|
|InventSupplyDlvModeSelectCust|
|InventSupplyDlvModeSelectSupply|
|InventSupplyLeadTimeSource|
|InventSupplyTmpLeadtimeType|
|InventTestActionOnFailure|
|InventTestBlockProcess|
|InventTestCorrectionPriority|
|InventTestCorrectionStatus|
|InventTestDocumentStatus|
|InventTestOrderStatusDisplay|
|InventTestOutcomeStatus|
|InventTestQtySpecification|
|InventTestQuarantineType|
|InventTestReferenceType|
|InventTestReport|
|InventTestType|
|InventTrackingDimNodeType|
|InventTrackingProductType|
|InventTrackingRegisterTransRegStatus|
|InventTransChildType|
|InventTransferRemainStatus|
|InventTransferStatus|
|InventTransferUpdateType|
|InventTransPickRegisterLineStatus|
|InventTransType|
|InventUpdType|
|InventValueReportLedgerAccountCategory|
|InventValueReportLedgerLineType|
|InventValueReportResourceType|
|ItemGroupLedgerDimensionGroup|
|ItemReservation|
|JmgAbsenceColumnLayout|
|JmgAbsenceMethodEnum|
|JmgAttendanceRegistrationType|
|JmgAttendanceReportType|
|JmgBarCodeType|
|JmgBreakDropEnum|
|JmgClockStyle|
|JmgControlType|
|JmgDaysTotalWorkflowStatus|
|JmgEmployeeSignInStatus|
|JmgFeedbackButtonFunction|
|JmgFeedbackStyle|
|JmgFieldName|
|JmgGetRegistrationTimeFrom|
|JmgGridAppearance|
|JmgJobTableSynchronizationMode|
|JmgJournalRegWorkflowStatus|
|JmgMark|
|JmgMessageType|
|JmgPayAdjustType|
|JmgPayEventsExportType|
|JmgPaySpecTypeEnum|
|JmgPaySpecTypeEnumPick|
|JmgPostAutomatically|
|JmgProdStatusUpdate|
|JmgProdStatusUpdateReportFinished|
|JmgProfileSpecTypeEnum|
|JmgProfileStartCodeBlankPrev|
|JmgProjStatusUpdate|
|JmgRegistrationTouchJobStatus|
|JmgSecondPresentationEnum|
|JmgShopFloorServiceStatus|
|JmgSignInButtonFunction|
|JmgStoppedCompletedStatus|
|JmgTermBaudeRate|
|JmgTermComPort|
|JmgTermDataBit|
|JmgTerminalInsertMode|
|JmgTermStopBit|
|KanbanBoardRefreshCycle|
|KanbanBoardType|
|KanbanCardAssignmentType|
|KanbanControlActionState|
|KanbanControlLegendFormat|
|KanbanControlSelectionChanged|
|KanbanDemandOriginType|
|KanbanJobPeggingType|
|KanbanJobPickingListLineType|
|KanbanLineEventType|
|KanbanMultiMode|
|KanbanPrintInstructions|
|KanbanProdBOMLineEventType|
|KanbanQuantityCalculationStatus|
|KanbanSalesLineEventType|
|KanbanStockReplenishmentEventType|
|LeanBOMLineReservationMethod|
|LeanCostingUnusedQtyType|
|LeanHandlingUnitEmptyPolicy|
|LeanInventoryControl|
|LeanPeggedEventType|
|LeanPlanJobReferenceTypes|
|LeanProductionFlowCostingStatus|
|LeanProductionFlowVisualizationViewMode|
|LeanProductTypes|
|LeanTaktStatus|
|LedgerPostingType|
|LedgerTransTxt|
|MarkupAllocateAfter|
|MarkupCategory|
|MCRBrokerContractStatus|
|MCRCustSearchType|
|MCRFullTextSearchType|
|MCRInstallPlanApplyMiscCharge|
|MCRItemListGenerationType|
|MCRPickingPrompt|
|MCRPickingSessionStatus|
|MCRPickingWaveStatus|
|MCRPriceHistoryType|
|MCRRoyaltyLineBreakType|
|MCRRoyaltyTakenFrom|
|MCRRoyaltyTransactionType|
|MCRRoyaltyUnitType|
|MCRRoyaltyUOMOption|
|MCRSalesOrderDetailStatus|
|ModuleInventCustVend|
|ModuleInventPurchSales|
|OriginalDocument|
|PaymDocumentType|
|PCExpressionEditorSymbolType|
|PCLookupMethod|
|PCNewSelectComponent|
|PCRequirement|
|PCTableConstraintType|
|PDSAdjustmentPrinciple|
|PdsBatchAttribToleranceAction|
|PdsBatchAttribUpdateType|
|PDSCalcElementBase|
|PDSCompensationPrincipleEnum|
|PDSElementTypeEnum|
|PDSIngredientTypeEnum|
|PdsMRCDocumentStatus|
|PdsMRCEffectiveDateBasis|
|PdsMRCEventModule|
|PdsMRCEventType|
|PdsMRCListType|
|PdsPaymtType|
|PDSPotencyAttribRecordingEnum|
|PdsRebateCalcDateType|
|PdsRebateTakenFrom|
|PdsRebateUOMOption|
|PdsSameLotError|
|pdsTMAJournalPosting|
|PdsUpdateBatchDate|
|PdsUpdateDispositionStatus_Quality|
|PlanActivityCreateRelationType|
|PlanActivityProductionFlowActivityType|
|PlanTypes|
|PmfCostAllocationMethod|
|PmfOrderType|
|PmfOrderTypeFilter|
|PmfProdType|
|PMFSeqCalendarPeriod|
|PriceBase|
|PriceDiscPurchasePromptSystemSource|
|PriceDiscSalesPromptSystemSource|
|PriceGroupType|
|PriceSalesPurch|
|PriceType|
|ProcCategoryAdministrationActivity|
|ProdBOMConsumpProposal|
|ProdBOMJournalQty|
|ProdBOMJournalSplit|
|ProdErrorCause|
|ProdGanttJobColorType|
|ProdGanttLoad|
|ProdGanttRouteColorType|
|ProdJournalCleanUpMode|
|ProdMode|
|ProdNotificationLevel|
|ProdParamInventDimLookup|
|ProdParmType|
|ProdRefLookUp|
|ProdRouteJobCurrentFormTabId|
|ProdSchedDirection|
|ProdScrapMethod|
|ProdStandardCostVariance|
|ProdStatusAll|
|ProdStatusType|
|ProductionTransType|
|ProdUpdateJour|
|ProdWHSReleasePolicy|
|ProdWIPType_NA|
|PurchaseOrderResponseAction|
|PurchaseType|
|PurchasingTransactionType|
|PurchCORReceivingMethod|
|PurchCORRejectStatus|
|PurchCovRef|
|PurchDlvAddr|
|PurchLineBackOrderViews|
|PurchLineDeliveryFulfillment|
|PurchLineDeliveryPrecision|
|PurchMatchingPolicyOverrideOption|
|PurchPrepayApplicationPolicy|
|PurchPriceDateType|
|PurchPurchaseOrderCreationMethod|
|PurchReApprovalPolicyRuleViewType|
|PurchReqAuthorizationSpecificReporting|
|PurchReqAutoCreatePurch|
|PurchReqCatalogAllNon|
|PurchReqConsolidationActiveStatus|
|PurchReqConsolidationPriority|
|PurchReqConsolidationStatus|
|PurchReqCreationStatus|
|PurchReqItemDescriptionTransfer|
|PurchReqItemFilterType|
|PurchReqOnBehalfReports|
|PurchReqOriginationAuthorizationView|
|PurchReqProcessingState|
|PurchReqQuestionnaireAggregateStatus|
|PurchReqQuestionnaireStatus|
|PurchReqReportSortOrder|
|PurchReqReportStatus|
|PurchReqReviewStatus|
|PurchReqRFQRequirement|
|PurchReqRFQType|
|PurchReqSaveChanges|
|PurchReqStatus|
|PurchReqType|
|PurchReqWorkflowState|
|PurchRFQQuestionnaireStatus|
|PurchRFQStatusVendor|
|PurchRFQType|
|PurchTableFormId|
|PurchTableListPage|
|PurchTableMode|
|PurchTotalsCachingMethod|
|PurchUpdate|
|PurchVendorPortalShowResponseType|
|QuotationType|
|ReqBOMRouteCreated|
|ReqCurrentDaySchedFrom|
|ReqDemPlanDataSourceType|
|ReqDemPlanDemandCategory|
|ReqDemPlanForecastAttributeType|
|ReqDemPlanForecastingStrategy|
|ReqDemPlanForecastType|
|ReqDisplayDelay|
|ReqForecastReducedBy|
|ReqGanttColorType|
|ReqGanttShow|
|ReqItemJournalType|
|ReqItemTableWizardPurpose|
|ReqMarkUpdate|
|ReqPeggingAssignmentType|
|ReqPeggingType|
|ReqPlannedOrderLeveling|
|ReqPlanType|
|ReqPOStatus|
|ReqQtyAmount|
|ReqRefType|
|ReqRefTypeShort|
|ReqRefTypeTrunc|
|ReqTraceMessageType|
|ReqTransFuturesActionPartType|
|ReturnCodeType|
|ReturnCycleTimeScope|
|ReturnReasonCodeDispExtended|
|ReturnReasonDispCode|
|ReturnUpdateAction|
|RouteFormula|
|RouteOprPriority|
|SalesBasketType|
|SalesBatch|
|SalesCheckForPickup|
|SalesCheckQtyCachKey|
|SalesDeliveryTimeState|
|SalesDocumentTimezonePreference|
|SalesPriceDateType|
|SalesPriceModelBasic|
|SalesPurchCopy|
|SalesPurchCycleAction|
|SalesPurchGroup|
|SalesPurchParmCleanUpMode|
|SalesQuotationFilter|
|SalesQuotationLinkToProject|
|SalesQuotationListPage|
|SalesQuotationPriceConversion|
|SalesQuotationPriceSimResult|
|SalesQuotationTypeListPage|
|SalesShipping|
|SalesSourcingOrigin|
|SalesStatus|
|SalesTableFormId|
|SalesTableListPage|
|SalesTableMode|
|SalesType|
|SalesUpdate|
|ShipCarrierDlvType|
|ShipCarrierFreightApplied|
|ShipCarrierMkUpFreight|
|SMAInvoiceProjectSelection|
|SMAItemSetupType|
|SMAProjectSelection|
|SMAReasonType|
|SMAServiceBOMChangeAction|
|SMAServiceFunctionType|
|SMAServiceLevelAgreementLogType|
|SMAServiceOrderActionType|
|SMAServiceOrderFilter|
|SMAServiceOrderOrigin|
|SMAServiceOrderProgress|
|SMAServiceTaskTitleOption|
|SMASubscriptionPeriodType|
|SMAWizardCreateType|
|smmAccountNumToCreate|
|smmActivityParentType|
|smmAppointmentNThInstance|
|smmBusinessRelationsListFilter|
|smmBusRelTypeSourceTable|
|smmCampaignBroadcastType|
|smmCampaignProjectJournalType|
|smmCampaignResponse|
|smmCampaignsListFilter|
|smmContactsListFilter|
|smmCreateOpportunityOptions|
|smmDisplayEMailInOutlook|
|smmDragDropObjectType|
|smmDupMethods|
|smmEMailSMS|
|smmEntityToCreate|
|smmFieldDelimiters|
|smmLeadsListFilter|
|smmLogType|
|smmOpportunitiesListFilter|
|smmOpportunityAssociation|
|smmOutlookContactDeleteAction|
|smmOutlookRecurrenceType|
|smmOutlookSyncPrinciple|
|smmOutlookUpdateAction|
|smmProjectNewExisting|
|smmQuotationAccountType|
|smmQuotationStatus|
|smmRecordDelimiters|
|smmSalesUnitMemberRelation|
|SmmSourceTypeList|
|smmSwotType|
|smmTransLogUpdateAction|
|smmUpdateOpportunityOptions|
|smmWarningError|
|SMAActiveAll|
|SMAAgreementFilter|
|SMAAgreementTableListPageType|
|TAMCustRebateApprovalStatus|
|TAMFundStatus|
|TAMFundType|
|TAMPromoCustomerType|
|TAMPromoMerchEvent|
|TAMPromoMgmtApprovalStatus|
|TAMPromotionDate|
|TAMPromotionMode|
|TAMRebateCustInclusive|
|TAMRebateLineBreakType|
|TAMRebateStatus|
|TAMRebateUnitType|
|TAMRebateUOMOption|
|TAMVendRebateApprovalStatus|
|TAMVendRebateCalcDateType|
|TAMVendRebateTakenFrom|
|TAMVendRebateTransactionType|
|TaxModuleType|
|TaxSourceType|
|TMSAccessorialAssignmentLevel|
|TMSAccessorialAssignmentTarget|
|TMSAccessorialDeliveryType|
|TMSAccessorialType|
|TMSAppointmentAlert|
|TMSDiscountResultType|
|TMSDiscountType|
|TMSFeeType|
|TMSFreightBillMatchStatus|
|TMSFreightBillReconcileType|
|TMSFwkErrorType|
|TMSHubPosition|
|TMSInvoiceAccountType|
|TMSLineType|
|TMSLoadBuildSessionState|
|TMSLoadTender|
|TMSLookupType|
|TMSNumberSequenceType|
|TMSOverrideLocationType|
|TMSRecurrenceDays|
|TMSRecurrenceType|
|TMSRecurrenceWeeks|
|TMSResponsibleForPayment|
|TMSRouteStatus|
|TMSSalesPurchTransfer|
|TMSTableRef|
|TMSTransportationType|
|TMSTransportRefType|
|TMSTransportTypeFilter|
|TMSUOM|
|TMSZoneType|
|TradeCurencyConversion|
|TradeLineDlvType|
|TradeNonStockedConversionChangeType|
|TradeNonStockedConversionIssue|
|TradeNonStockedConversionResolveUndo|
|TradePrintType|
|TradeTable2LineUpdate|
|VendNotificationCategorySelection|
|VendNotificationStatus|
|VendPackingSlipTransTimeStatus|
|VendRequestCompanyType|
|VendRequestOriginatedByType|
|VendRequestQuestionnairesCompleted|
|VendRequestRoleType|
|VendReviewRatingScore|
|VersioningAction|
|WHSAllowMaterialOverPick|
|WHSApplicableDemand|
|WHSAutoReleaseContainerAtContainerClose|
|WHSAutoReleaseOrderType|
|WHSBreakCluster|
|WHSContainerizationQueryType|
|WHSContainerPackingStrategy|
|WHSContainerTableFormViewType|
|WHSCrossDockFulfillmentStrategy|
|WHSCustJourType|
|WHSCycleCountPlanStatus|
|WHSDefaultDataField|
|WHSFilterModule|
|WHSHistoryEvent|
|WHSLoadPlanning|
|WHSLoadPostMethodsBase|
|WhsLoadReplenishment|
|WHSLoadTable|
|WHSLocDirStrategy|
|WHSLPAssignment|
|WHSLPWFilterType|
|WHSManifestAt|
|WHSManifestRequirementContainerGroup|
|WHSMenuItemDirectedBy|
|WHSMixedLPReceivingMode|
|WHSMixingLogicTables|
|WHSMobileAppPagePattern|
|WHSOriginType|
|WHSPickOldestBatch|
|WHSPostMethodBaseKanban|
|WHSPostMethodBaseKanbanOptional|
|WHSPostMethodBaseOptional|
|WHSPostMethodBaseProd|
|WHSPostMethodBaseProdOptional|
|WHSPostMethodsBase|
|WHSQtyPct|
|WHSReleaseQuantitySpecification|
|WHSReplenishmentDependentWorkBlockingPolicy|
|WHSReservationHierarchyLevelStrategyType|
|WHSReservationStatus|
|WHSUseFixedLocations|
|WHSWorkActivity|
|WHSWorkClusterStatus|
|WHSWorkCreationProcess|
|WHSWorkExceptionLogStatus|
|WHSWorkExecuteMode|
|WHSWorkListPageFilter|
|WHSWorkPrintOption|
|WHSWorkPutFlow|
|WHSWorkTransType|
|WHSWorkType|
|WHSWorkTypePickPut|
|WMSAutoAddStop|
|WMSFreightChargeTerms|
|WMSFreightCounted|
|WMSHandlingType|
|WMSLocationType|
|WMSPackageType|
|WMSPalletMovementProcessing|
|WMSPhysicalUpdateStatus|
|WMSReceiptStatus|
|WMSReservationMethod|
|WMSReservationMethodInternal|
|WMSShipmentStatus|
|WMSShipmentType|
|WMSSpaceUtilInconsistencyGroup|
|WMSSpaceUtilShowBy|
|WMSSpaceUtilStorageLoadUnitType|
|WMSStoreAreaType|
|WMSTrailerLoaded|
|WrkCtrActivityType|
|WrkCtrBulkResReqSearchType|
|WrkCtrCapacityType|
|WrkCtrCapRefType|
|WrkCtrCommitState|
|WrkCtrGroupWrkCtr|
|WrkCtrSchedulerCommand|
|WrkCtrSchedulerConstraintType|
|WrkCtrSchedulerLoggerMode|
|WrkCtrType|
|WrkCtrTypeFilter|

These enumerations were removed, and not made extensible.

| Enumeration removed |
| --------------- |
|BackorderLinesListPageMode|
|BackorderPurchLinesListPageMode |
|EcoResProductPerCompanyListPageType |
|ReturnTableListPageType |
|SMAAgreementTableListPageType|

Foundation changes were made to improve support for extensible enumerations. The **SysPlugin** framework was enabled for enumerations where **IsExtensible** is set to **Yes**. Views were enabled with new name-based syntax for enumerations.

## Data manipulation methods that do not raise DataEvents or missing insert, update, delete pre- and post-data events

As a general practice, you use data methods on tables to raise events that can be used for extending the application. The code base has not always followed this practice. For example, the **doInsert**, **doUpdate**, and **doDelete** data methods and certain table implementations did not make a call to **super()** in the data method.

The **insert**, **update**, and **delete** methods on the type classes have been refactored. Changes were made so that **super()** is called more consistently in data methods. These changes enable extensions to be added to these methods, so that pre- and post-events are now available for extension. The tables where the **insert**, **update**, and **delete** events were enabled for extension are listed in the following table.

| Table |
| -------------|
| InventBlocking|
| InventTransferLine|
| Kanban|
| KanbanJob|
| KanbanJobPickingList|
| MCRRoyaltyVendTable|
| PdsRebateTable|
| PmfProdCoBy|
| ProdBOM|
| ProdRoute|
| ProdTable|
| PurchLine|
| PurchRFQCaseLine|
| PurchRFQCaseTable|
| PurchRFQLine|
| PurchTable|
| SalesLine|
| SalesQuotationLine|
| SalesQuotationTable|
| SalesTable|
| TAMVendRebateTable|
| WMSOrder|
| WMSOrderTrans|

## Exposing class members

Additional private members are now available for customization as a result of the changes to the access modifier or new parm methods. The chain of command platform feature enables extension class access to protected methods and members. For more information about chain of command, see [Extensible X++: Chain of Command](https://community.dynamics.com/365/financeandoperations/b/mfp/posts/extensible-x-chain-of-command).

| Member |
| -------------|
|AssetPost.ledgerJournalTrans|
|Class DimensionDerivationRule.ledgerDimensionAllocationList|
|Class PurchInvoiceJournalCreate.purchTable|
|Class PurchTableType.purchTable|
|Class SalesInvoiceJournalPost.salesLine|
|Class SalesQuotationLineType|
|Class SalesQuotationTableType|
|Class VendorInvoiceLineSourceDocLineItem.purchLine|
|CustCreditLimit.balanceTotalsCalculated|
|CustCreditLimit_SalesTable.salesTable|
|Form LedgerJournalTransCustPaym.ledgerJournalEngine|
|PurchLineType.purchLine|
|PurchLineType.purchLine_orig|
|SalesLineType.salesLine|
|SalesLineType.salesLine_orig|
|SalesTableType.checkSalesQty|
|SalesTableType.SalesTable_orig|
|WHSControl.data|
|WHSLocationDirective.targetLicensePlateId|

## Construct methods with throw statements

Some **construct** methods were implemented with **throw** statements if there was a missing implementation for a given type. This doesn't work well with extensibility, so to mitigate this, **construct** methods were changed so that they do not throw exceptions. These methods are now to open for extensibility through class augmentation or by post-event subscription.

| Object |
| -------------|
|BarcodeEAN128.string()|
|CustCreditLimit.Construct|
|FormLetterReport|
|JournalStatic|
|MarkupAllocation|
|PurchTable2LineField|
|SalesCalcTax|
|SalesEditLinesForm|
|SalesFormLetter|
|SalesFormLetterContract.newFromPackedVersion|
|SalesFormletterParmData.newData|
|SalesQuantity|
|SalesQuotationEditLinesForm.construct|
|SalesSummaryFields|
|SalesTable2LineField|
|VendInvoiceTableToLineUpdate|

## Find methods with throw statements

Some **find** methods were implemented with **throw** statements if there was a missing implementation for a given type. This does not work well with extensibility, so to mitigate this, **find** methods were changed so that they do not throw exceptions. These methods are now to open for extensibility through class augmentation or by post-event subscription.

| Methods |
| -------------|
|JournalStatic.findJournalTableFromTrans|
|JournalStatic.findJournalTableId|

## Methods made hookable

Extensibility support has been extended for some methods that were not public and were not hookable. The following methods have been explicitly decorated with hookable behavior.

| Method |
| -------------|
|Class CustVendReversePosting.updateCustVendTrans|
|Class JournalTableData.construct|
|Class PriceDisc.makeKey|
|Class PurchInvoiceJournalCreate.initJournalHeader|
|Class SalesInvoiceJournalPost.checkSourceLine|
|Class SalesInvoiceJournalPost.postCustVend|
|Form LedgerTransVoucher.addDynaLink|
|ReqCalc.deleteItemRequirement|
|ReqCalc.initTransFromInventTrans|
|ReqCalcForecastItemTable.deleteRequirement|
|Table TmpCustVendTrans.createLineCreditLimit|
|Table TmpCustVendTrans.createLineCreditRemain|
|Table TmpCustVendTrans.createLineOrdered|
|Table TmpCustVendTrans.createLinePackingSlip|
|WHSLocationDirective.addRangeByTransType|
|WhsWorkCreate.createWorkLine|

## Inline delegates

Inline delegates are now available. The most common way to use inline delegates is to split the method into more granular methods and enable extensibility events in the smaller methods.

|  Method |
| -------------|
|AxClass - ChequeDP - Method - insertChequeTmp|
|AxClass - VendInvoiceTableToLineUpdate - Method - convertPurchTableFieldToVendInvoice|
|class JournalStatic.findJournalTableFromTrans|
|class JournalStatic.findJournalTableId|
|Class WhsLocationDirective.findLocationMultiSKU|
|EcoResReleasedProductVariantEntity.insertEntityDataSource|
|ForecastSales.ForecastSales_ds.updateForecastSalesFields|
|Form SalesTable - method updateDesign|
|ReqTransPoMarkFirm.firmSelectedPlannedOrders|
|SalesLineType.insert|
|SalesLineType.update|
|SalesTable2LineUpdatePrompt.dialog|
|table ExtCodeTable|
|table InventItemGroup.getGroupForAccountType|
|table InventItemGroup.ledgerDimensionDescription|
|table InventTestAssociationTable|
|Table LedgerJournalName - method validateWrite|
|Table PaymTerm - method due|
|TaxCalculation.newForSourceType|
|TaxCalculation.newForSourceTypeWithTaxUncommitted|
|WHSLoadLine.getOrderCommonFromLoadLine|
|WhsLocationDirective.findLocation|
|WHSRFControlData.populateData|
|WHSRFControLData.processControl|
|WHSRFMenuItemTable.getWHSWorkExecuteMode|

## Other changes

The following table lists additional changes that have been made for extensibility.


|                                                           Change                                                           |
|----------------------------------------------------------------------------------------------------------------------------|
|                                      Add indirection for existing product dimensions                                       |
|                                  Class FormLetterParmDataOutputContract is not extensible                                  |
|             Create an instantiation strategy for the SysExtensionFramework that supports one or more arguments             |
|                      Customization: TableField: Extension Model: Change EDT type of on a table field                       |
|                          CustVendOpenTransBalances - initAccountNumCurrencies() switch statement                           |
|                                     CustVendOpenTransBalances - new() switch statement                                     |
|                                  CustVendOutPaym (Class) needs extensibility improvement                                   |
|                        CustVendPaymReconciliationSetStatus (Class) needs extensibility improvement                         |
|                                 CustVendSumForPaym (Class) needs extensibility improvement                                 |
|                               Decouple AddressCountyId and AddressStateId EDTs from SysGroup                               |
|                          Document Management event handling needs improved extensibility support                           |
|            Exchange rate provider framework requires custom built providers to be placed in the Currency Model             |
|                                                      Extending GS-128                                                      |
|                         Extension model: Allow customizations on the CountryRegionCodes property.                          |
|                  Form extension - Extension of "extended" form elements with new controls are not working                  |
|                                              InventDim: Condition with throw                                               |
|                                                  InventDimRenameDimValue                                                   |
|                Method overlayering - Class VendInvoiceTableToLineUpdate.convertPurchTableFieldToVendInvoice                |
|                                     Method overlayering: class Markup - method delete                                      |
|                       Method overlayering: class McrPriceHistoryForm.insertPotentialTradeAgreements                        |
|                             Method overlayering: Class OffsetVoucher - method markTransaction                              |
|                                 Method overlayering: Form LedgerJournalTransDimension.init                                 |
|                                 Method overlayering: Form LedgerTransVoucher - method init                                 |
|                             Method overlayering: Table CustInvoiceTable - method validateWrite                             |
|                       Method signature changed: RetailCreateLinesFromProductsToAdd.parmCallerCommon                        |
|                               Method signature changed: WHSInvent.getCommonFromWorkTransType                               |
|                                  Method signature changed: WHSPoolProdBom.movementBuffer                                   |
|                          Missing construct method: class SMAServiceOrderTableButtonStateProvider                           |
|                                         Number sequence scope extensibility needed                                         |
|                           Runbase needs a way for class extensions to pack/unpack their members                            |
|                                              String EDT size extension issues                                              |
|                              Support opening Inventory on-hand form based on custom InventDim                              |
|          SysExtension framework: SysExtensionIInstantiationStrategy and SysExtensionIAttribute are not compatible          |
| Variations of EventHandlerResult are requested to ensure that delegates used in Request/response scenarios are more robust |
|                                                WHS Mobile Framework: passes                                                |
|                                     WhsLocationDirectiveLine To/FromQty not extensible                                     |
|                                                 WHSMobileApp Extensibility                                                 |
|         WHSMobileAppAttachedImageDetails.removeLabelFromDimValue() is not generic enough about Product dimensions          |
|         WHSMobileAppAttachedImageDetails.removeLabelFromDimValue() is not generic enough about Product dimensions          |
|            WhsRFControlData.processControl must reference WhsControl.data instead of _data in the switch block             |



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]