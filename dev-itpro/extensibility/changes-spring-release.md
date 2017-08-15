---

# required metadata
title: Extensibility changes for Dynamics 365 for Finance and Operations, Enterprise edition July 2017 update
description: This is a list of extensibility features that were implemented with the July 2017 update.
author: RobinARH
manager: AnnBe
ms.date: 08/13/2017
ms.topic: index-page
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata
# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations, Platform, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 268724
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2017-02-28
ms.dyn365.ops.version: Platform update 4

---

# Extensibility changes for Dynamics 365 for Finance and Operations, Enterprise edition July 2017 update

[!include[banner](../includes/banner.md)]

This is a list of extensibility features that were implemented with the July 2017 update which has build number 7.2.11792.56024. For more information about the schedule of changes that support extensbility, see [Application extensibility plans](extensibility-roadmap.md).

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

A few application middle-tier models were hard-sealed in this release. Overlayered code in these models will generate errors on compilation.

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

Some changes were made to support extending enumerations:
- Many enumerations in the standard application were made extensible in this release. An enumeration is made extensible by setting two properties on the enumeration. The **IsExtensible** property is set to **Yes**, and the **UseEnumValue** property is set to **No**. 
- Some enums represents state. We added new façade methods in some places to help enable adding enumeration values by extension. For information about extending an enumeration, see [Add an enum value](add-enum-value.md).
- Some application code that uses enumerations was changed to support extensibility. Common changes included:
    + Removing **throw** exception statements in the default case of a switch to allow post-event subscription.
    + Adding **SysExtension** support for extension.
    + Adding explicit delegates.


| Enum|
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
|ChequeFormType|
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

We removed these enumerations rather than make them extensible:

| Enumeration removed |
| --------------- |
|BackorderLinesListPageMode|
|BackorderPurchLinesListPageMode |
|EcoResProductPerCompanyListPageType |
|ReturnTableListPageType |
|SMAAgreementTableListPageType|

We hade to make some foundation changes to improve support for extensible enumerations. The **SysPlugin** framework was enabled for enumerations where **IsExtensible** is set to **Yes**. Views were enabled with new name based syntax for enumerations.

Data manipulation methods that do not raise DataEvents or Missing Insert, Update, Delete pre-/post-data events.

As a general rule, data methods on tables raise events that can be used for extending the application.  There were exceptions to this practice in the code base, however.  Two examples are doDelete data methods and certain table implementations that did not make a super() in the data method.

Type methods have been added to table objects like inserting and inserted which we call with the matching data method insert, similar to other data methods. Changes were made so that super() was called more consistently in data methods. These changes enable extensions to be added to these methods.

| Table |
| :-------------|
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

## Exposing class member

Private members have been made available for customization in some cases through changing the access modifier and/or adding parm methods.  Note that the upcoming Chain of Command platform feature will enable extension class access to protected methods and members.

| Object & Member|
| :-------------|
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

## Construct with throw

Some construct methods were implemented with throw statements if there is a missing implementation for a given type. This does not work well with extensibility and to mitigate this we changed such construct methods to remove throwing behavior to open up for extensibility through class augmentation or by post event subscription.

| Object |
| :-------------|
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

## Find with throw

Very similar to construct with throw, these are just with find methods.

| Object & Method |
| :-------------|
|JournalStatic.findJournalTableFromTrans|
|JournalStatic.findJournalTableId|

## Methods made hookable

Extensibility support has been extended for some methods that were not public and as such were not enabling hookable event. These were enabled by explicitly decorating the methods with hookable behavior.

| Object & Method |
| :-------------|
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

Several requests for inline delegates have been met in this release. The most common approach was splitting the method into more granular methods and enabling extensibility events in the smaller methods.

| Object & Method |
| :-------------|
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

## Various other extensibility features

Completing the list of features that have been added are those that don't fit in the categories above. The titles of these features follow:

| Title|
| :-------------|
|Add indirection for existing product dimensions|
|Class FormLetterParmDataOutputContract is not extensible|
|Create an instantiation strategy for the SysExtensionFramework that supports one or more arguments|
|Customization: TableField: Extension Model: Change EDT type of on a table field|
|CustVendOpenTransBalances - initAccountNumCurrencies() switch statement|
|CustVendOpenTransBalances - new() switch statement|
|CustVendOutPaym (Class) needs extensibility improvement|
|CustVendPaymReconciliationSetStatus (Class) needs extensibility improvement|
|CustVendSumForPaym (Class) needs extensibility improvement|
|Decouple AddressCountyId and AddressStateId EDTs from SysGroup|
|Document Management event handling needs improved extensibility support|
|Exchange rate provider framework requires custom built providers to be placed in the Currency Model|
|Extending GS-128|
|Extension model: Allow customizations on the CountryRegionCodes property.|
|Form extension - Extension of "extended" form elements with new controls are not working|
|InventDim: Condition with throw|
|InventDimRenameDimValue|
|Method overlayering - Class VendInvoiceTableToLineUpdate.convertPurchTableFieldToVendInvoice|
|Method overlayering: class Markup - method delete|
|Method overlayering: class McrPriceHistoryForm.insertPotentialTradeAgreements|
|Method overlayering: Class OffsetVoucher - method markTransaction|
|Method overlayering: Form LedgerJournalTransDimension.init|
|Method overlayering: Form LedgerTransVoucher - method init|
|Method overlayering: Table CustInvoiceTable - method validateWrite|
|Method signature changed: RetailCreateLinesFromProductsToAdd.parmCallerCommon|
|Method signature changed: WHSInvent.getCommonFromWorkTransType|
|Method signature changed: WHSPoolProdBom.movementBuffer|
|Missing construct method: class SMAServiceOrderTableButtonStateProvi|
|Number sequence scope extensibility needed|
|Runbase needs a way for class extensions to pack/unpack their members|
|String EDT size extension issues|
|Support opening Inventory on-hand form based on custom InventDim|
|SysExtension framework: SysExtensionIInstantiationStrategy and SysExtensionIAttribute are not compatible|
|Variations of EventHandlerResult are requested to ensure that delegates used in Request/response scenarios are more robust|
|WHS Mobile Framework: passes|
|WhsLocationDirectiveLine To/FromQty not extensible|
|WHSMobileApp Extensibility|
|WHSMobileAppAttachedImageDetails.removeLabelFromDimValue() is not generic enough about Product dimensions|
|WHSMobileAppAttachedImageDetails.removeLabelFromDimValue() is not generic enough about Product dimensions|
|WhsRFControlData.processControl must reference WhsControl.data instead of _data in the switch block|
