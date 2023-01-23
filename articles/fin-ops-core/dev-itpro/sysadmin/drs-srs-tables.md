---
title: Tables supported for duplicate record data sharing
description: This article describes the tables supported for duplicate record data sharing. This is a mechanism for sharing reference and group data among companies in a deployment.
author: RamaKrishnamoorthy
ms.date: 01/23/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: ramasri
ms.search.validFrom: 2022-01-27
ms.dyn365.ops.version: Platform update 1
ms.custom: 89071
ms.assetid: 0bbe7453-624f-4551-a1d0-842484067311
ms.search.form: SysDataSharingConfiguration
---

# Tables supported for duplicate record data sharing
This article describes the tables supported for duplicate record data sharing. Duplicate record data sharing is a mechanism for sharing reference and group data among companies in a deployment. It might be possible to add additional tables to duplicate record data sharing policies, however, any table not listed in the following tables is not officially supported.

**Dynamics 365 Finance**

| **Table object Name**        | **Table description (Label)**   |
|------------------------------|---------------------------------|
| AssetCondition               | Fixed asset condition           |
| BankCentralBankPurpose       | Payment purpose codes           |
| BankChequeLayout             | Check layout                    |
| BankGroup                    | Bank groups                     |
| BankParameters               | Bank parameters                 |
| BankTransType                | Bank transaction type           |
| CompanyNAFCode               | NAF codes                       |
| CredManAccountStatusTable    | Account statuses                |
| CredManCollectionsGroupTable | Collection groups               |
| CredManGroup                 | Credit management groups        |
| CredManReasonTable           | Reason table                    |
| CustBankAccount              | Customer bank accounts          |
| CustCollectionLetterTable    | Collection letter setup         |
| CustDefaultLocation          | Customer default locations      |
| CustGroup                    | Customer groups                 |
| CustLedger                   | Customer posting profiles       |
| CustPaymModeTable            | Methods of payment – customers  |
| CustStaticsGroup             | Statistics group                |
| CustTable                    | Customers                       |
| CustTradingPartnerCode       | Trading partner code            |
| CustVendItemGroup            | External item description group |
| LedgerJournalName            | Name of journal                 |
| LineOfBusiness               | Line of business                |
| PaymDay                      | Payment days                    |
| PaymDayLine                  | Payment day lines               |
| PaymSched                    | Payment schedule                |
| PaymSchedLine                | Payment schedule lines          |
| PaymTerm                     | Terms of payment                |
| ReasonTable                  | Reasons                         |
| Tax1099Fields                | 1099 fields                     |
| VendExceptionGroup           | Vendor exception groups         |
| VendLedger                   | Vendor posting profile          |
| VendPriceToleranceGroup      | Vendor price tolerance groups   |

**Tax**

| **Table object Name**           | **Table description (Label)** |
|---------------------------------|-------------------------------|
| TaxAuthorityAddress             | Authority                     |
| TaxAuthorityAddressRegistration | Authority registration number |
| TaxGroupHeading                 | Sales tax group description   |
| TaxItemGroupHeading             | Item sales tax group          |
| TaxParameters                   | Sales tax parameters          |
| TaxPeriodHead                   | Sales tax period description  |

**Dynamics 365 Supply Chain Management**

| **Table object name**                        | **Table description (Label)**                          |
|----------------------------------------------|--------------------------------------------------------|
| BarcodeSetup                                 | Barcode setup                                          |
| BOMCalcGroup                                 | Calculation groups                                     |
| BOMCostGroup                                 | Cost group                                             |
| CommissionCustomerGroup                      | Commission customer group                              |
| CommissionSalesGroup                         | Commission sales group                                 |
| CommissionItemGroup                          | Commission item group                                  |
| CommissionSalesRep                           | Commission sales rep.                                  |
| CustClassificationGroup                      | Customer classification groups                         |
| DlvMode                                      | Mode of delivery                                       |
| DlvReason                                    | Reason of delivery                                     |
| DlvTerm                                      | Terms of delivery                                      |
| ForecastItemAllocation                       | Item allocation keys                                   |
| InventBuyerGroup                             | Buyer groups                                           |
| InventCountingReasonCodePolicy               | Counting reason code policies                          |
| InventFiscalLIFOGroup                        | Fiscal LIFO reporting group                            |
| InventItemGroup                              | Item groups                                            |
| InventItemPriceToleranceGroup                | Item price tolerance groups                            |
| InventJournalName                            | Inventory journal names                                |
| InventLocationInventCountingReasonCodePolicy | Inventory counting reason code policy for warehouse    |
| InventModelGroup                             | Item model groups                                      |
| InventNumGroup                               | Number groups                                          |
| InventOrderEntryDeadlineGroup                | Order entry deadline groups                            |
| InventPackagingGroup                         | Packing groups                                         |
| InventProblemType                            | Problem types                                          |
| InventProblemTypeSetup                       | Problem/Non conformance types validation               |
| KittingGroupTable                            | Kit groups                                             |
| MarkupGroup                                  | Charges groups                                         |
| PdsBatchAttrib                               | Batch attributes                                       |
| PdsBatchAttribByAttribGroup                  | Group attributes                                       |
| PdsBatchAttribEnumValues                     | Attribute enumerate values                             |
| PdsBatchAttribGroup                          | Batch attribute groups                                 |
| PdsCustRebateGroup                           | Customer rebate groups                                 |
| PdsDispositionMaster                         | Batch disposition master                               |
| PdsFreightGroup                              | Freight allocation group                               |
| PdsItemRebateGroup                           | Item rebate group                                      |
| PdsRebateProgramTMATable                     | TMA groups                                             |
| PersonTitleTable                             | Titles/occupations                                     |
| PlSADRateGroup                               | Duty rates groups                                      |
| PriceDiscGroup                               | Price groups                                           |
| PriceDiscSmartRoundingGroup                  | Rounding version                                       |
| PriceDiscSmartRoundingGroupCurrency          | Rounding version members                               |
| PriceDiscSmartRoundingRule                   | Rounding rules                                         |
| ProdGroup                                    | Production groups                                      |
| ProdPool                                     | Production pools                                       |
| PurchPool                                    | Purchase pools                                         |
| ReasonTable                                  | Reasons                                                |
| ReqGroup                                     | Item coverage groups                                   |
| ReqReduceKey                                 | Reduction keys                                         |
| ReqReduceLine                                | Reduction lines                                        |
| ReqSitePolicy                                | Master planning site policies                          |
| RetailBarcodeMaskCharacter                   | Bar code mask characters                               |
| RetailBarcodeMaskSegment                     | Bar code mask segment                                  |
| RetailBarcodeMaskTable                       | Bar code mask                                          |
| RetailInventoryLevelProfile                  | Inventory level profile                                |
| RetailInventoryLevelProfileProcessingRange   | Inventory level processing range                       |
| RetailInventoryLevelProfileRange             | Inventory level range                                  |
| RetailPricingPriorityTable                   | Pricing priority                                       |
| RetailSeasonTable                            | Season                                                 |
| RevRecRevenueSchedule                        | Revenue schedules                                      |
| RevRecRevenueScheduleDetail                  | Revenue schedule details                               |
| RouteCostCategory                            | Cost categories                                        |
| SalesOrigin                                  | Order origin codes                                     |
| SalesPool                                    | Order pools                                            |
| smmBusRelChainGroup                          | Company chains                                         |
| smmBusRelDefaultLocation                     | Prospect default locations                             |
| smmBusRelSalesDistrictGroup                  | Sales districts                                        |
| smmBusRelSectorTable                         | Prospect sector table                                  |
| smmBusRelSegmentGroup                        | Segment table                                          |
| smmBusRelStatusGroup                         | Status table                                           |
| smmBusRelSubSegmentGroup                     | Subsegment table                                       |
| smmBusRelTable                               | Prospects                                              |
| smmBusRelTypeGroup                           | Type table                                             |
| smmBusSectorGroup                            | Business classification table                          |
| smmCharacterGroup                            | Contact characters                                     |
| smmContactGreetingsGroup                     | Complimentary close                                    |
| smmContactInterest                           | Contact interests                                      |
| smmContactIntroGroup                         | Salutation texts                                       |
| smmConvertedBusRel                           | Converted prospects                                    |
| smmDecisionGroup                             | Decision table                                         |
| smmFunctionGroup                             | Function                                               |
| smmInterestGroup                             | Interests                                              |
| smmLeadPriorityTable                         | Lead priority                                          |
| smmLeadRatingTable                           | Lead rating                                            |
| smmLeadTable                                 | Leads                                                  |
| smmLeadTypeTable                             | Lead type                                              |
| smmLoyaltyGroup                              | Loyalties                                              |
| smmOpportunityTable                          | Opportunities                                          |
| smmQuotationProbabilityGroup                 | Quotation probability                                  |
| smmQuotationPrognosisGroup                   | Quotation prognosis                                    |
| smmQuotationReasonGroup                      | Quotation reason                                       |
| smmSalesUnit                                 | Sales management units                                 |
| smmSalesUnitMembers                          | Sales unit members                                     |
| smmSourceTypeOptions                         | Source type option                                     |
| smmSourceTypeTable                           | Source type                                            |
| SuppItemGroup                                | Supplementary item groups                              |
| TAMItemVendRebateGroup                       | Item rebate groups                                     |
| TAMVendRebateGroup                           | Vendor rebate group                                    |
| TMSBillingGroup                              | Billing group                                          |
| TMSBreakDetail                               | Break Detail                                           |
| TMSBreakMaster                               | Break master                                           |
| TMSDlvTerm                                   | Terms of delivery related to transportation management |
| TMSNumberSequence                            | Number sequences                                       |
| TMSRateBase                                  | Rate base                                              |
| TMSRateBaseAssignment                        | Rate base assignment                                   |
| TMSRateBaseDetail                            | Rate Base Detail                                       |
| TMSRateBaseType                              | Rate base types                                        |
| TMSRateBaseTypeField                         | Rate Base Type Field                                   |
| TMSRateEngine                                | Rate engine                                            |
| TMSRateMaster                                | Rate master                                            |
| TMSTransitTimeDetail                         | Transit Time Detail                                    |
| TMSTransitTimeEngine                         | Transit time engine                                    |
| TMSTransitTimeField                          | Transit time field                                     |
| TMSZoneEngine                                | Zone engine                                            |
| VendGroup                                    | Vendor groups                                          |
| WHSClusterProfile                            | Cluster profiles                                       |
| WHSClusterSort                               | Cluster sorting                                        |
| WHSContainerAttributes                       | Container attributes                                   |
| WHSContainerGroup                            | Container groups                                       |
| WHSContainerGroupLine                        | Container Group Detail                                 |
| WHSDocumentRoutingLayout                     | Document routing layouts                               |
| WHSFilterParm                                | Required filters                                       |
| WHSFilters                                   | Product filters                                        |
| WHSLoadTemplate                              | Load templates                                         |
| WHSLocationFormat                            | Location Formats                                       |
| WHSLocationFormatLine                        | Location Format Detail                                 |
| WHSLocationType                              | Location types                                         |
| WHSLocDirHint                                | Directive codes                                        |
| WHSMovementType                              | Movement types                                         |
| WHSPackageClass                              | Package classes                                        |
| WHSPackSizeCategory                          | Pack size categories                                   |
| WHSPhysDimGroupTable                         | Physical Dimension by Group                            |
| WHSRequestType                               | Request types                                          |
| WHSUOMSeqGroupLine                           | Unit Sequence Group Detail                             |
| WHSUOMSeqGroupTable                          | Unit sequence groups                                   |
| WHSWaveAttributes                            | Wave attributes                                        |
| WHSWaveLabelType                             | Wave label type                                        |
| WHSWorkClassTable                            | Work classes                                           |
| WHSWorkClassValidLocType                     | Valid put location types                               |
| WHSWorkPool                                  | Work pools                                             |
| WHSZone                                      | Warehouse zones                                        |
| WHSZoneGroup                                 | Warehouse zone groups                                  |
| WorkCalendarDate                             | Working times                                          |
| WorkCalendarDateLine                         | Working time                                           |
| WorkCalendarTable                            | Calendar                                               |
| WrkCtrProperty                               | Properties                                             |
| WrkCtrPropertyLine                           | Property                                               |

**Dynamics 365 Project Operations**

| **Table object name** | **Table description (Label)** | **Release details/Additional information** |
|-----------------------|-------------------------------|-------------------------------|
| CategoryTable         | Category table                ||
| ProjLineProperty      | Line property                 ||
|ProjCategory|Project category|Dynamics 365 Finance 10.0.32 <br/>DRS is not enabled for Categories for control types (ProjControlCategory) in Dynamics 365 Finance 10.0.32, records must be manually created for Categories for control types (ProjControlCategory) in the legal entities where data is duplicated for Project categories. |
|ProjCategoryGroup|Category group|Dynamics 365 Finance 10.0.32 <br/>|
|ProjPeriodLine|Project period lines|Dynamics 365 Finance 10.0.32 <br/>|
|ProjPeriodTable|Project periods|Dynamics 365 Finance 10.0.32 <br/>|
|ProjPeriodTimesheetWeek|Timesheet weekly periods|Dynamics 365 Finance 10.0.32 <br/>This table should be shared in the same policy as Project periods(ProjPeriodTable). |
|PSACustomerRetentionTermLine|Customer retention term lines|Dynamics 365 Finance 10.0.32 <br/>|
|PSACustomerRetentionTermTable|Customer retention terms|Dynamics 365 Finance 10.0.32 <br/>|
|PSAIndirectComponent|Indirect cost component|Dynamics 365 Finance 10.0.32 <br/>This table has a reference to Project Category. It needs to be shared within the same policy as the Project Category table to ensure the data integrity.|
|PSAIndirectComponentGroup|Indirect cost component groups|Dynamics 365 Finance 10.0.32 <br/>|
|PSAIndirectCompoundingRules|Compounding rules|Dynamics 365 Finance 10.0.32 <br/>|
|PSAIndirectCompoundingRulesSelection|Indirect cost component compounding rule|Dynamics 365 Finance 10.0.32 <br/>|
|PSAIndirectCompoundingSetup|Assigned indirect cost components|Dynamics 365 Finance 10.0.32 <br/>|
|PSAVendorRetentionTermsLine|Retainage schedule line|Dynamics 365 Finance 10.0.32 <br/>|
|PSAVendorRetentionTermsTable|Retainage schedule|Dynamics 365 Finance 10.0.32 <br/>|

**Additional tables when the customer and vendor master sharing feature is enabled**

| **Table object name**              | **Table description (Label)**             | 
|------------------------------------|-------------------------------------------|
| BankConstantSymbol                 | Bank constant symbols                     |
| BankCustPaymIdTable                | Payment ID                                | 
| BankTransactionTypeGroupHeader     | Bank transaction groups                   |
| ContactPerson                      | Contacts                                  |
| CreditCardCust                     | Customer credit card                      |
| CustFineSetup_BR                   | Fine codes                                |
| CustInterestSetup_BR               | Interest codes                            |
| CustomChequeLayout_BR              | Custom check layout                       |
| CustomsTariffCodeTable_IN          | Customs tariff codes                      |
| ExciseTariffCodes_IN               | Excise tariff codes                       |
| LvPaymTransCodes                   | Payment transaction code                  |
| PaymentFormatCodeSets_W            | Payment format code sets                  |
| RetailCustTable                    | Customers (Retail)                        |
| RetailVendTable                    | Product import vendor setup               |
| SalesTaxFormTypes_IN               | India sales tax form types                |
| smmResponsibilitiesEmpTable        | Responsibility assignments                |
| StatRepInterval                    | Statistics                                |
| StatRepIntervalLine                | Aging periods                             |
| TaxBranch                          | Tax branch                                |
| TaxComponentTable_IN               | Tax components                            |
| TaxInformationCustTable_IN         | Tax Information of Customer               |
| TaxInformationVendTable_IN         | Tax Information of Vendor                 |
| TaxLedgerAccountGroup_IN           | Tax ledger posting group                  |
| TaxVatNumTable                     | Tax exempt number table                   |
| TaxWithholdComponentGroupTable_IN  | Withholding tax component groups          |
| TaxWithholdComponentTable_IN       | Withholding tax components                |
| TaxWithholdTable                   | Withholding tax codes                     |
| VendBankAccount                    | Vendor bank accounts                      |
| VendContractZakat_SA               | Contractor                                |
| VendDefaultAccounts                | Default ledger accounts for vendors       |
| VendDefaultLocation                | Vendor Default Location                   |
| VendFineSetup_BR                   | Fine codes                                |
| VendInfoZakat_SA                   | Vendors                                   | 
| VendInterestSetup_BR               | Interest codes                            |
| VendStateTaxID                     | Vendor state tax IDs                      |
| VendTable                          | Vendors                                   |

**Available duplicate records data sharing templates**
<table>
<thead>
<tr class="header">
<th>Package name on LCS</th>
<th>Data sharing policies</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Financial data sharing templates</td>
<td><ul>
<li>Bank parameters</li>
<li>Ledger journal names</li>
<li>Payment days</li>
<li>Payment schedules</li>
<li>Payment terms</li>
<li>Tax exempt codes</li>
</ul></td>
</tr>
<tr class="even">
<td>Supply chain data sharing templates</td>
<td><ul>
<li>Barcode parameters</li>
<li>Barcode setup</li>
<li>Buyer group</li>
<li>Charges group</li>
<li>Commission</li>
<li>Destination code</li>
<li>Non-conformance type</li>
<li>Order entry deadline group</li>
<li>Order origin code</li>
<li>Order pool</li>
<li>Production group</li>
<li>Production pool</li>
<li>Reason for delivery</li>
<li>Supplementary item group</li>
<li>Terms of delivery</li>
<li>Work time calendar</li>
</ul></td>
</tr>
</tbody>
</table>


## Download a cross-company data sharing template from LCS
To download a cross-company data sharing template from Lifecycle Services (LCS), follow these steps: 
1.	Sign in to LCS.
2.	On the home page, select Shared asset library.
3.	In the Asset type list, select Data package.
4.	Select any of the available data package files that you want to download.
For details about how to use a template, see [Configure financial cross-company data sharing](../data-entities/tasks/configure-financial-cross-company-data-sharing.md).

## Tables supported for master company data sharing
It might be possible to add additional tables for master company data sharing policies, however, any table not listed in the following tables is not officially supported.

**Dynamics 365 Finance**

| **Table object name**          | **Table description (Label)**   |
|--------------------------------|---------------------------------|
| AssetCondition                 | Fixed asset condition           |
| BankCentralBankPurpose         | Payment purpose codes           |
| BankChequeLayout               | Check layout                    |
| BankGroup                      | Bank groups                     |
| BankParameters                 | Bank parameters                 |
| BankTransType                  | Bank transaction type           |
| BankTransactionTypeGroupHeader | Bank transaction groups         |
| CompanyNAFCode                 | NAF codes                       |
| CreditCardCust                 | Customer credit card            |
| CreditCardProcessors           | Payment services                |
| CreditCardTypeCurrency         | Credit card type currency       |
| CreditCardTypeSetup            | Credit card type setup          |
| CredManAccountStatusTable      | Account statuses                |
| CredManCollectionsGroupTable   | Collection groups               |
| CredManGroup                   | Credit management groups        |
| CredManReasonTable             | Reason table                    |
| CustBankAccount                | Customer bank accounts          |
| CustCollectionLetterTable      | Collection letter setup         |
| CustDefaultLocation            | Customer default locations      |
| CustGroup                      | Customer groups                 |
| CustLedger                     | Customer posting profiles       |
| CustPaymModeTable              | Methods of payment – customers  |
| CustStaticsGroup               | Statistics group                |
| CustTable                      | Customers                       |
| CustTradingPartnerCode         | Trading partner code            |
| CustVendItemGroup              | External item description group |
| LedgerJournalName              | Name of journal                 |
| LineOfBusiness                 | Line of business                |
| PaymDay                        | Payment days                    |
| PaymDayLine                    | Payment day lines               |
| PaymSched                      | Payment schedule                |
| PaymSchedLine                  | Payment schedule lines          |
| PaymTerm                       | Terms of payment                |
| ReasonTable                    | Reasons                         |
| ReasonTableRef                 | Reason references               |
| StatRepInterval                | Statistics                      |
| StatRepIntervalLine            | Aging periods                   |
| Tax1099Fields                  | 1099 fields                     |
| VendExceptionGroup             | Vendor exception groups         |
| VendLedger                     | Vendor posting profile          |
| VendPriceToleranceGroup        | Vendor price tolerance groups   |
| VendStateTaxID                 | Vendor state tax IDs            |

**Tax**

| **Table object name**           | **Table description (Label)** |
|---------------------------------|-------------------------------|
| TaxAuthorityAddress             | Authority                     |
| TaxAuthorityAddressRegistration | Authority registration number |
| TaxGroupHeading                 | Sales tax group description   |
| TaxItemGroupHeading             | Item sales tax group          |
| TaxParameters                   | Sales tax parameters          |
| TaxPeriodHead                   | Sales tax period description  |

**Dynamics 365 Supply Chain Management**

| **Table name**                       | **Table description (Label)**              |
|--------------------------------------|--------------------------------------------|
| BarcodeSetup                         | Barcode setup                              |
| ContactPerson                        | Contacts                                   |
| CustClassificationGroup              | Customer classification groups             |
| DlvMode                              | Mode of delivery                           |
| DlvReason                            | Reason of delivery                         |
| DlvTerm                              | Terms of delivery                          |
| InventProblemType                    | Problem types                              |
| InventProblemTypeSetup               | Problem/ Non conformance types validation  |
| PriceDiscGroup                       | Price groups                               |
| PriceDiscSmartRoundingGroup          | Rounding version                           |
| PriceDiscSmartRoundingGroupCurrency  | Rounding version members                   |
| PriceDiscSmartRoundingRule           | Rounding rules                             |
| smmBusRelDefaultLocation             | Prospect default locations                 |
| smmBusRelSectorTable                 | Prospect sector table                      |
| smmBusRelTable                       | Prospects                                  |
| smmLeadTable                         | Leads                                      |
| smmOpportunityTable                  | Opportunities                              |
| smmQuotationPrognosisGroup           | Quotation prognosis                        |
| smmQuotationReasonGroup              | Quotation reason                           |
| smmResponsibilitiesEmplTable         | Responsibility assignments                 |
| smmSalesUnit                         | Sales management units                     |
| smmSalesUnitMembers                  | Sales unit members                         |
| smmSourceTypeOptions                 | Source type option                         |
| smmSourceTypeTable                   | Source type                                |
| TAMVendRebateGroup                   | Vendor rebate group                        |
| WorkCalendarDate                     | Working times                              |
| WorkCalendarDateLine                 | Working time                               |
| WorkCalendarTable                    | Calendar                                   |
| WrkCtrPropertyLine                   | Property                                   |

Additional Supply Chain Management tables when the (Private Preview) cross-company data sharing for products feature is enabled.

>[!NOTE]
> The following tables can be added to a master company data sharing policy but are only supported when the “Cross-company data sharing for products” feature is enabled, which is currently in Private Preview.

| **Table name**                            | **Table description (Label)**                  |
|-------------------------------------------|------------------------------------------------|
| InventStdCostConv                         | Standard cost conversion                       |
| InventStdCostConvItem                     | Standard cost conversion items                 |
| InventTable                               | Items                                          |
| InventTableInventCountingReasonCodePolicy | Inventory counting reason code policy for item |
| InventTableModule                         | Inventory module parameters                    |
| KittingInventTable                        | Manage kit structure                           |
| MCRInventTable                            | Inventory table retail information             |
| PdsBatchAttribByItem                      | Product specific                               |
| RetailInventTable                         | Item table                                     |
| TMSInventEnabled                          | Transportation item number                     |
| WarrantyInventTable                       | Warranty items                                 |
| WHSInventEnabled                          | List of warehouse management items             |
| WHSInventTable                            | Warehouse item number                          |
| WHSPhysDimUOM                             | Physical Dimension by Unit                     |

**Dynamcis 365 Project Operations**

| **Table object name** | **Table description (Label)** |
|-----------------------|-------------------------------|
| CategoryTable         | Category table                |
| ProjLineProperty      | Line Property                 |
