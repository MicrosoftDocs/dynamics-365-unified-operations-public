---
# required metadata

title: Data import/export framework entities (AX 2012)
description: This topic lists the entities that can be imported by using the Data Import/Export Framework, the application module that each entity is associated with, and the class, staging table, and target table for each entity.
author: kfend
manager: AnnBe
ms.date: 2015-12-04 22 - 27 - 09
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 18011
ms.assetid: 46b9d56e-8692-45af-8e86-22ec0192444f
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Data import/export framework entities (AX 2012)

This topic lists the entities that can be imported by using the Data Import/Export Framework, the application module that each entity is associated with, and the class, staging table, and target table for each entity.

|                                                                             |                        |                                         |                                      |                                          |
|-----------------------------------------------------------------------------|------------------------|-----------------------------------------|--------------------------------------|------------------------------------------|
| **Entity(Entity type)**                                                     | **Application module** | **Entity class**                        | **Staging table**                    | **Target table**                         |
| Customer(Master data)                                                       | Customer               | DMFCustomerEntityClass                  | DMFCustomerEntity                    | DMFCustomerTargetEntity                  |
| Customer address(Master data)                                               | Customer               | DMFCustomerAddressEntityClass           | DMFCustomerAddressEntity             | DMFCustomerAddressTargetEntity           |
| Outbound ports for electronic payments(System configuration)                | Customer               | DMFCustVendAifPaymTableEntityClass      | DMFCustVendAifPaymTableEntity        | DMFCustVendAifPaymTableTargetEntity      |
| Audit policy(Documents)                                                     | Expense                | DMFSysPolicySourceDocuRuleEntityClass   | DMFSysPolicySourceDocumentRuleEntity | DMFSysPolicySourceDocuRuleTargetEntity   |
| Credit card codes(Reference data)                                           | Expense                | DMFTrvPBSCatCodesEntityClass            | DMFTrvPBSCatCodesEntity              | DMFTrvPBSCatCodesTargetEntity            |
| Delegates(Setup)                                                            | Expense                | DMFTrvAppEmplSubEntityClass             | DMFTrvAppEmplSubEntity               | DMFTrvAppEmplSubTargetEntity             |
| Expense category(Setup)                                                     | Expense                | DMFTrvCostTypeEntityClass               | DMFTrvCostTypeEntity                 | DMFTrvCostTypeTargetEntity               |
| Expense subcategory(Setup)                                                  | Expense                | DMFTrvExpSubCategoryEntityClass         | DMFTrvExpSubCategoryEntity           | DMFTrvExpSubCategoryTargetEntity         |
| Mileage rate tiers(Setup)                                                   | Expense                | DMFTrvCostTypeRatesEntityClass          | DMFTrvCostTypeRatesEntity            | DMFTrvCostTypeRatesTargetEntity          |
| Payment method(Reference data)                                              | Expense                | DMFTrvPayMethodEntityClass              | DMFTrvPayMethodEntity                | DMFTrvPayMethodTargetEntity              |
| Valid payment methods(Reference data)                                       | Expense                | DMFTrvValidatePaymentEntityClass        | DMFTrvValidatePaymentEntity          | DMFTrvValidatePaymentTargetEntity        |
| Asset(Master data)                                                          | Fixed assets           | DMFAssetEntityClass                     | DMFAssetEntity                       | DMFAssetTargetEntity                     |
| Employee(Master data)                                                       | Human resources        | DMFEmployeeEntityClass                  | DMFEmployeeEntity                    | DMFEmployeeTargetEntity                  |
| Employee address(Master data)                                               | Human resources        | DMFEmployeeAddressEntityClass           | DMFEmployeeAddressEntity             | DMFEmployeeAddressTargetEntity           |
| Job detail(Master data)                                                     | Human resources        | DMFHcmJobDetailEntityClass              | DMFHcmJobDetailEntity                | DMFHcmJobDetailTargetEntity              |
| Organization hierarchy(Documents)                                           | Human resources        | DMFOMHierarchyEntityClass               | DMFOMHierarchyEntity                 | DMFOMHierarchyTargetEntity               |
| Personnel parameters(Parameter)                                             | Human resources        | DMFHRMParametersEntityClass             | DMFHRMParametersEntity               | DMFHRMParametersTargetEntity             |
| Positions(Master data)                                                      | Human resources        | DMFHcmPositionDetailEntityClass         | DMFHcmPositionDetailEntity           | DMFHcmPositionDetailTargetEntity         |
| Shared human resources parameters(Parameter)                                | Human resources        | DMFHCmSharedParametersEntityClass       | DMFHCmSharedParametersEntity         | DMFHCmSharedParametersTargetEntity       |
| Barcode setup(Setup)                                                        | Inventory              | DMFBarcodeSetupEntityClass              | DMFBarcodeSetupEntity                | DMFBarcodeSetupTargetEntity              |
| Category table(Setup)                                                       | Inventory              | DMFCategoryTableEntityClass             | DMFCategoryTableEntity               | DMFCategoryTableTargetEntity             |
| Inventory journal(Journal)                                                  | Inventory              | DMFInventJournalEntityClass             | DMFInventJournalEntity               | DMFInventJournalTargetEntity             |
| Items(Master data)                                                          | Inventory              | DMFInventTableEntityClass               | DMFInventTableEntity                 | DMFInventTableTargetEntity               |
| Price discount agreement journal(Journal)                                   | Inventory              | DMFPriceDiscAdmTransEntityClass         | DMFPriceDiscAdmTransEntity           | DMFPriceDiscAdmTransTargetEntity         |
| Product(Master data)                                                        | Inventory              | DMFProductEntityClass                   | DMFProductEntity                     | DMFProductTargetEntity                   |
| Product attribute(Setup)                                                    | Inventory              | DMFEcoResAttributeEntityClass           | DMFEcoResAttributeEntity             | DMFEcoResAttributeTargetEntity           |
| Product attribute type(Setup)                                               | Inventory              | DMFEcoResAttributeTypeEntityClass       | DMFEcoResAttributeTypeEntity         | DMFEcoResAttributeTypeTargetEntity       |
| Product category hierarchy(Setup)                                           | Inventory              | DMFEcoResCategoryHierarchyEntityClass   | DMFEcoResCategoryHierarchyEntity     | DMFEcoResCategoryHierarchyTargetEntity   |
| Product category hierarchy role(Setup)                                      | Inventory              | DMFEcoResCategoryHierarcRoleEntityClass | DMFEcoResCategoryHierarchyRoleEntity | DMFEcoResCategoryHierarcRoleTargetEntity |
| Product master(Master data)                                                 | Inventory              | DMFProductMasterEntityClass             | DMFProductMasterEntity               | DMFProductMasterTargetEntity             |
| Dimension(Reference data)                                                   | Ledger                 | DMFDimensionEntityClass                 | DMFDimensionAttributeValueEntity     | DMFDimensionAttributeValueTargetEntity   |
| Dimension set(Setup)                                                        | Ledger                 | DMFDimensionHierarchyEntityClass        | DMFDimensionHierarchyEntity          | DMFDimensionHierarchyTargetEntity        |
| Ledger parameters(Parameter)                                                | Ledger                 | DMFLedgerParametersEntityClass          | DMFLedgerParametersEntity            | DMFLedgerParametersTargetEntity          |
| Main account(Master data)                                                   | Ledger                 | DMFMainAccountEntityClass               | DMFMainAccountEntity                 | DMFMainAccountTargetEntity               |
| Opening balance(Journal)                                                    | Ledger                 | DMFLedgerBalanceEntityClass             | DMFLedgerJournalEntity               | DMFLedgerJournalTransEntity              |
| Operating unit(Master data)                                                 | Ledger                 | DMFOMOperatingUnitEntityClass           | DMFOMOperatingUnitEntity             | DMFOMOperatingUnitTargetEntity           |
| Payroll parameter(Parameter)                                                | Payroll                | DMFPRLPayrollParametersEntityClass      | DMFPRLPayrollParametersEntity        | DMFPRLPayrollParametersTargetEntity      |
| BOM (bill of materials)(Master data)                                        | Production             | DMFBOMEntityClass                       | DMFBOMEntity                         | DMFBOMTargetEntity                       |
| BOM version(Master data)                                                    | Production             | DMFBOMVersionEntityClass                | DMFBOMVersionEntity                  | DMFBOMVersionTargetEntity                |
| Route(Master data)                                                          | Production             | DMFRouteEntityClass                     | DMFRouteEntity                       | DMFRouteTargetEntity                     |
| Route operations(Master data)                                               | Production             | DMFRouteOperationEntityClass            | DMFRouteOperationEntity              | DMFRouteOperationTragetEntity            |
| Budget parameters(Parameter)                                                | Project                | DMFBudgetParametersEntityClass          | DMFBudgetParametersEntity            | DMFBudgetParametersTargetEntity          |
| Budget register entries(Documents)                                          | Project                | DMFBudgetEntityClass                    | DMFBudgetTransactionLineEntity       | DMFBudgetTransactionTargetEntity         |
| On-account(Documents)                                                       | Project                | DMFProjOnAccTransEntityClass            | DMFProjOnAccTransEntity              | DMFProjOnAccTransTargetEntity            |
| Project(Master data)                                                        | Project                | DMFProjTableEntityClass                 | DMFProjTableEntity                   | DMFProjTableTargetEntity                 |
| Project contracts(Documents)                                                | Project                | DMFProjInvoiceTableEntityClass          | DMFProjInvoiceTableEntity            | DMFProjInvoiceTableTargetEntity          |
| Project journal(Journal)                                                    | Project                | DMFProjJournalTransEntityClass          | DMFProjJournalTransEntity            | DMFProjJournalTransTargetEntity          |
| Working time calendars(Setup)                                               | Project                | DMFWorkCalendarTableEntityClass         | DMFWorkCalendarTableEntity           | DMFWorkCalendarTableTargetEntity         |
| Working times(Setup)                                                        | Project                | DMFWorkCalendarDateEntityClass          | DMFWorkCalendarDateEntity            | DMFWorkCalendarDateTargetEntity          |
| Working times line(Setup)                                                   | Project                | DMFWorkCalendarDateLineEntityClass      | DMFWorkCalendarDateLineEntity        | DMFWorkCalendarDateLineTargetEntity      |
| Purchase order header(Documents)                                            | Purchase order         | DMFPurchTableEntityClass                | DMFPurchTableEntity                  | DMFPurchTableTargetEntity                |
| Purchase order line(Documents)                                              | Purchase order         | DMFPurchLineEntityClass                 | DMFPurchLineEntity                   | DMFPurchLineTargetEntity                 |
| Contact address(Master data)                                                | Sales and marketing    | DMFContactPersonAddressEntityClass      | DMFContactPersonAddressEntity        | DMFContactPersonAddressTargetEntity      |
| Contact person(Master data)                                                 | Sales and marketing    | DMFContactPersonEntityClass             | DMFContactPersonEntity               | DMFContactPersonTargetEntity             |
| Sales order header(Documents)                                               | Sales order            | DMFSalesTableEntityClass                | DMFSalesTableEntity                  | DMFSalesTableTargetEntity                |
| Sales order line(Documents)                                                 | Sales order            | DMFSalesLineEntityClass                 | DMFSalesLineEntity                   | DMFSalesLineTargetEntity                 |
| Item sales tax group(Setup)                                                 | Sales tax              | DMFTaxItemGroupHeadingEntityClass       | DMFTaxItemGroupHeadingEntity         | DMFTaxItemGroupHeadingTargetEntity       |
| Item sales tax group setup(Setup)                                           | Sales tax              | DMFTaxOnItemEntityClass                 | DMFTaxOnItemEntity                   | DMFTaxOnItemTargetEntity                 |
| Ledger posting groups(Setup)                                                | Sales tax              | DMFTaxLedgerAccountGroupEntityClass     | DMFTaxLedgerAccountGroupEntity       | DMFTaxLedgerAccountGroupTargetEntity     |
| Sales tax codes(Setup)                                                      | Sales tax              | DMFTaxTableEntityClass                  | DMFTaxTableEntity                    | DMFTaxTableTargetEntity                  |
| Sales tax details(Setup)                                                    | Sales tax              | DMFTaxDataEntityClass                   | DMFTaxDataEntity                     | DMFTaxDataTargetEntity                   |
| Sales tax group(Setup)                                                      | Sales tax              | DMFTaxGroupDataEntityClass              | DMFTaxGroupDataEntity                | DMFTaxGroupDataTargetEntity              |
| Sales tax group header(Setup)                                               | Sales tax              | DMFTaxGroupHeadingEntityClass           | DMFTaxGroupHeadingEntity             | DMFTaxGroupHeadingTargetEntity           |
| Sales tax parameters(Parameter)                                             | Sales tax              | DMFTaxParametersEntityClass             | DMFTaxParametersEntity               | DMFTaxParametersTargetEntity             |
| Sales tax period(Setup)                                                     | Sales tax              | DMFTaxPeriodHeadEntityClass             | DMFTaxPeriodHeadEntity               | DMFTaxPeriodHeadTargetEntity             |
| Tax authority(Setup)                                                        | Sales tax              | DMFTaxAuthorityAddressEntityClass       | DMFTaxAuthorityAddressEntity         | DMFTaxAuthorityAddressTargetEntity       |
| Active document tables(Setup)                                               | System                 | DMFDocuTableEnabledEntityClass          | DMFDocuTableEnabledEntity            | DMFDocuTableEnabledTargetEntity          |
| Approved vendor list(Reference data)                                        | System                 | DMFPdsApprovedVendorListEntityClass     | DMFPdsApprovedVendorListEntity       | DMFPdsApprovedVendorListTargetEntity     |
| Assortment header(Documents)                                                | System                 | DMFRetailAssortmentHeaderEntityClass    | DMFRetailAssortmentHeaderEntity      | DMFRetailAssortmentHeaderTargetEntity    |
| Assortment line(Documents)                                                  | System                 | DMFRetailAssortmentLineEntityClass      | DMFRetailAssortmentLineEntity        | DMFRetailAssortmentLineTargetEntity      |
| Assortments(Documents)                                                      | System                 | DMFRetailAssortmentPublishEntityClass   | DMFRetailAssortmentPublishEntity     | DMFRetailAssortmentHeaderTargetEntity    |
| Bank parameters(Parameter)                                                  | System                 | DMFBankParametersEntityClass            | DMFBankParametersEntity              | DMFBankParametersTargetEntity            |
| Barcode(Setup)                                                              | System                 | DMFProductBarcodeEntityClass            | DMFProductBarcodeEntity              | DMFProductBarcodeTargetEntity            |
| Batch groups(System configuration)                                          | System                 | DMFbatchGroupEntityClass                | DMFbatchGroupEntity                  | DMFbatchGroupTargetEntity                |
| Business intelligence report servers(System configuration)                  | System                 | DMFSRSServersEntityClass                | DMFSRSServersEntity                  | DMFSRSServersTargetEntity                |
| Card setup(Setup)                                                           | System                 | DMFRetailStoreTenderTypeCardEntityClass | DMFRetailStoreTenderTypeCardEntity   | DMFRetailStoreTenderTypeCardTargetEntity |
| Card type(Setup)                                                            | System                 | DMFRetailTenderTypeCardEntityClass      | DMFRetailTenderTypeCardEntity        | DMFRetailTenderTypeCardTargetEntity      |
| Case workflow(Documents)                                                    | System                 | DMFWorkflowTableEntityClass             | DMFWorkflowTableEntity               | DMFWorkflowTableTargetEntity             |
| Cash denominations(Setup)                                                   | System                 | DMFStoreCashDeclarationEntityClass      | DMFStoreCashDeclarationEntity        | DMFStoreCashDeclarationTargetEntity      |
| Category(Setup)                                                             | System                 | DMFEcoResCategoryEntityClass            | DMFEcoResCategoryEntity              | DMFEcoResCategoryTargetEntity            |
| Configuration(System configuration)                                         | System                 | DMFBIConfigurationEntityClass           | DMFBIConfigurationEntity             | DMFBIConfigurationTargetEntity           |
| Content types(Setup)                                                        | System                 | DMFContentTypeEntityClass               | DMFContentTypeEntity                 | DMFContentTypeTargetEntity               |
| Cost accounting parameter(Parameter)                                        | System                 | DMFCOSParametersEntityClass             | DMFCOSParametersEntity               | DMFCOSParametersTargetEntity             |
| Delivery mode(Setup)                                                        | System                 | DMFDlvModeEntityClass                   | DMFDlvModeEntity                     | DMFDlvModeTargetEntity                   |
| Document data sources(Setup)                                                | System                 | DMFDocuDataSourceEntityClass            | DMFDocuDataSourceEntity              | DMFDocuDataSourceTargetEntity            |
| Document management parameters(Parameter)                                   | System                 | DMFDocuParametersEntityClass            | DMFDocuParametersEntity              | DMFDocuParametersTargetEntity            |
| Document types(Setup)                                                       | System                 | DMFDocuTypeEntityClass                  | DMFDocuTypeEntity                    | DMFDocuTypeTargetEntity                  |
| Electronic signature parameters(Parameter)                                  | System                 | DMFSIGParametersEntityClass             | DMFSIGParametersEntity               | DMFSIGParametersTargetEntity             |
| Email parameters(System configuration                                       | System                 | DMFSysEmailParametersEntityClass        | DMFSysEmailParametersEntity          | DMFSysEmailParametersTargetEntity        |
|  Enterprise Portal for Microsoft Dynamics AX document parameters(Parameter) | System                 | DMFEPDocuParametersEntityClass          | DMFEPDocuParametersEntity            | DMFEPDocuParametersTargetEntity          |
| Environmental parameters(Parameter)                                         | System                 | DMFEMSParameterEntityClass              | DMFEMSParameterEntity                | DMFEMSParameterTargetEntity              |
| Expense policy(Documents)                                                   | System                 | DMFTrvPolicyRuleEntityClass             | DMFTrvPolicyRuleEntity               | DMFTrvPolicyRuleTargetEntity             |
| Fixed asset parameters(Parameter)                                           | System                 | DMFAssetParametersClass                 | DMFAssetParametersEntity             | DMFAssetParametersTargetEntity           |
| General settings for collaboration workspaces(System configuration)         | System                 | DMFCollabSiteParametersEntityClass      | DMFCollabSiteParametersEntity        | DMFCollabSiteParametersTargetEntity      |
| Gift card(Document)                                                         | System                 | DMFRetailGiftCardEntityClass            | DMFRetailGiftCardEntity              | DMFRetailGiftCardTargetEntity            |
| Global address book parameters(Parameter)                                   | System                 | DMFDirParametersEntityClass             | DMFDirParametersEntity               | DMFDirParametersTargetEntity             |
| Hardware profiles(Master data)                                              | System                 | DMFRetailHardwareProfileEntityClass     | DMFRetailHardwareProfileEntity       | DMFRetailHardwareProfileTargetEntity     |
| Inbound port(System configuration)                                          | System                 | DMFAifInboundPortEntityClass            | DMFAifInboundPortEntity              | DMFAifInboundPorEntity                   |
| Intrastat code(Setup)                                                       | System                 | DMFIntrastatStateParametersEntityClass  | DMFIntrastatStateParametersEntity    | DMFIntrastatStateParametersTargetEntity  |
| Inventory parameters(Parameter)                                             | System                 | DMFInventParametersEntityClass          | DMFInventParametersEntity            | DMFInventParametersTargetEntity          |
| Linked product(Setup)                                                       | System                 | DMFRetailLinkedProductEntityClass       | DMFRetailLinkedProductEntity         | DMFRetailLinkedProductTargetEntity       |
| Lookup entry(Setup)                                                         | System                 | DMFAifLookupEntryEntityClass            | DMFAifLookupEntryEntity              | DMFAifLookupEntryTargetEntity            |
| Microsoft Project Server applications(Setup)                                | System                 | DMFProjServerSettingsEntityClass        | DMFProjServerSettingsEntity          | DMFProjServerSettingsEntity              |
| Mix and match discount header(Documents)                                    | System                 | DMFRetailMixAndMatchEntityClass         | DMFRetailMixAndMatchEntity           | DMFRetailMixAndMatchTargetEntity         |
| Mix and match discount line(Documents)                                      | System                 | DMFRetailMixAndMatchLineEntityClass     | DMFRetailMixAndMatchLineEntity       | DMFRetailMixAndMatchLineTargetEntity     |
| Number sequence code(Master data)                                           | System                 | DMFNumberSequenceTableEntityClass       | DMFNumberSequenceTableEntity         | DMFNumberSequenceTableTargetEntity       |
| Operations(Reference data)                                                  | System                 | DMFRouteOprTableEntityClass             | DMFRouteOprTableEntity               | DMFRouteOprTableTargetEntity             |
| Organization hierarchies(Documents)                                         | System                 | DMFOrganizationHierarchyEntityClass     | DMFOrganizationHierarchyEntity       | DMFOrganizationHierarchyTargetEntity     |
| Outbound port(System configuration)                                         | System                 | DMFAifOutboundPortEntityClass           | DMFAifoutboundPortEntity             | DMFAifoutboundPorEntity                  |
| Party relationships(Setup)                                                  | System                 | DMFDirPartyRelationshipEntityClass      | DMFDirPartyRelationshipEntity        | DMFDirPartyRelationshipTargetEntity      |
| Payment method to store(Setup)                                              | System                 | DMFRetailStoreTenderTypeEntityClass     | DMFRetailStoreTenderTypeEntity       | DMFRetailStoreTenderTypeTargetEntity     |
| Price groups(Setup)                                                         | System                 | DMFPriceDiscGroupEntityClass            | DMFPriceDiscGroupEntity              | DMFPriceDiscGroupTargetEntity            |
| Product category(Setup)                                                     | System                 | DMFProductCategoryEntityClass           | DMFProductCategoryEntity             | DMFProductCategoryTargetEntity           |
| Product dimension group(Setup)                                              | System                 | DMFProductDimensionGroupEntityClass     | DMFProductDimensionGroupEntity       | DMFProductDimensionGroupTargetEntity     |
| Product receipt(Setup)                                                      | System                 | DMFProductReceiptEntityClass            | DMFProductReceiptEntity              | DMFProductReceiptTargetEntity            |
| Production parameters(Parameter)                                            | System                 | DMFprodparametersEntityClass            | DMFprodparametersEntity              | DMFprodparametersTargetEntity            |
| Related products(Reference data)                                            | System                 | DMFProductRelationEntityClass           | DMFProductRelationEntity             | DMFProductRelationTargetEntity           |
| Report deployment settings(System configuration)                            | System                 | DMFSRSReportDeploymentEntityClass       | DMFSRSReportDeploymentEntity         | DMFSRSReportDeploymentTargetEntity       |
| Resource parameters(Parameter)                                              | System                 | DMFWrkCtrParametersEntityClass          | DMFWrkCtrParametersEntity            | DMFWrkCtrParametersTargetEntity          |
| Resource requirements(Reference data)                                       | System                 | DMFWrkCtrActivityRequirementEntityClass | DMFWrkCtrActivityRequirementEntity   | DMFWrkCtrActivityRequirementTargetEntity |
| Route relation(Reference data)                                              | System                 | DMFRouteRelationEntityClass             | DMFRouteRelationEntity               | DMFRouteRelationTargetEntity             |
| Sales and marketing parameters(Parameter)                                   | System                 | DMFsmmParametersTableEntityClass        | DMFsmmParametersTableEntity          | DMFsmmParametersTableTargetEntity        |
| Scheduler parameters(Parameter)                                             | System                 | DMFRetailConnParametersEntityClass      | DMFRetailConnParametersEntity        | DMFRetailConnParametersTargetEntity      |
| Server configuration(System configuration)                                  | System                 | DMFSysServerConfigEntityClass           | DMFSysServerConfigEntity             | DMFSysServerConfigTargetEntity           |
| Service management parameters(Parameter)                                    | System                 | DMFsmaParametersEntityClass             | DMFsmaParametersEntity               | DMFsmaParametersTargetEntity             |
| Shared category(Setup)                                                      | System                 | DMFSharedCategoryEntityClass            | DMFSharedCategoryEntity              | DMFSharedCategoryTargetEntity            |
| Store(Setup)                                                                | System                 | DMFRetailStoreEntityClass               | DMFRetailStoreEntity                 | DMFRetailStoreTargetEntity               |
| Subscription parameters(Parameter)                                          | System                 | DMFSMAParametersSubscriptionClass       | DMFSMAParametersSubscriptionEntity   | DMFSMAParametersSubscriptionTargetEntity |
| Synchronization parameters(Parameter)                                       | System                 | DMFSyncParametersEntityClass            | DMFSyncParametersEntity              | DMFSyncParametersTargetEntity            |
| System parameters(System configuration)                                     | System                 | DMFSystemParametersEntityClass          | DMFSystemParametersEntity            | DMFSystemParametersTargetEntity          |
| Terminals(Setup)                                                            | System                 | DMFRetailTerminalEntityClass            | DMFRetailTerminalEntity              | DMFRetailTerminalTargetEntity            |
| Time periods(Setup)                                                         | System                 | DMFBITimePeriodsMDXEntityClass          | DMFBITimePeriodsMDXEntity            | DMFBITimePeriodsMDXTargetEntity          |
| Time transactions(Setup)                                                    | System                 | DMFWorkTimeLineEntityClass              | DMFWorkTimeLineEntity                | DMFWorkTimeLineTargetEntity              |
| Transfer lines(Journal)                                                     | System                 | DMFTransferOrderLineEntityClass         | DMFTransferOrderLineEntity           | DMFTransferOrderLineTargetEntity         |
| Transfer order receive(Documents)                                           | System                 | DMFTransferOrderReceiveEntityClass      | DMFTransferOrderReceiveEntity        | DMFTransferOrderShipReceiveTargetEntity  |
| Transfer order shipment(Documents)                                          | System                 | DMFTransferOrderShipmentEntityClass     | DMFTransferOrderShipmentEntity       | DMFTransferOrderShipReceiveTargetEntity  |
| Transfer orders(Journal)                                                    | System                 | DMFTransferOrderEntityClass             | DMFTransferOrderEntity               | DMFTransferOrderTargetEntity             |
| Travel and expense parameters(Parameter)                                    | System                 | DMFTrvParametersClass                   | DMFTrvParametersEntity               | DMFTrvParametersTargetEntity             |
| Units(Reference data)                                                       | System                 | DMFUnitOfMeasureEntityClass             | DMFUnitOfMeasureEntity               | DMFUnitOfMeasureTragetEntity             |
| User information(Master data)                                               | System                 | DMFUserEntityClass                      | DMFUserEntity                        | DMFUserTargetEntity                      |
| Variant(Setup)                                                              | System                 | DMFProductVariantEntityClass            | DMFProductVariantEntity              | DMFProductVariantTargetEntity            |
| Vendor parameters(Parameter)                                                | System                 | DMFVendparametersEntityClass            | DMFVendparametersEntity              | DMFVendparametersTargetEntity            |
| Websites(System configuration)                                              | System                 | DMFAifWebsitesEntityClass               | DMFAifWebsitesEntity                 | DMFAifWebsitesTargetEntity               |
| Workflow work item queue(Setup)                                             | System                 | DMFWorkflowWorkItemQueueEntityClass     | DMFWorkflowWorkItemQueueEntity       | DMFWorkflowWorkItemQueueTargetEntity     |
| Working time templates(Master data)                                         | System                 | DMFWorkTimeTableEntityClass             | DMFWorkTimeTableEntity               | DMFWorkTimeTableTargetEntity             |
| Vendor(Master data)                                                         | Vendor                 | DMFVendorEntityClass                    | DMFVendorEntity                      | DMFVendorTargetEntity                    |
| Vendor address(Master data)                                                 | Vendor                 | DMFVendorAddressEntityClass             | DMFVendorAddressEntity               | DMFVendorAddressTargetEntity             |
| Vendor groups(Reference data)                                               | Vendor                 | DMFVendGroupEntityClass                 | DMFVendGroupEntity                   | DMFVendGroupTargetEntity                 |
| Vendor invoice header(Documents)                                            | Vendor                 | DMFVendInvoiceInfoTableEntityClass      | DMFVendInvoiceInfoTableEntity        | DMFVendInvoiceInfoTableTargetEntity      |
| Vendor invoice line(Documents)                                              | Vendor                 | DMFVendInvoiceInfoLineEntityClass       | DMFVendInvoiceInfoLineEntity         | DMFVendInvoiceInfoLineTargetEntity       |

 

