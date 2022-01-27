---
# required metadata

title: Tables officially supported for Duplicate Record Data sharing  
description: This topic describes cross-company data sharing, which is a mechanism for sharing reference and group data among companies in a deployment.
author: ramasri
ms.date: 01/27/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SysDataSharingConfiguration
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 89071
ms.assetid: 0bbe7453-624f-4551-a1d0-842484067311
ms.search.region: Global
# ms.search.industry: 
ms.author: ramasri
ms.search.validFrom: 2022-01-27
ms.dyn365.ops.version: Platform update 1

---

# Tables officially supported for Duplicate Record Data sharing
Even if it might be possible to add other tables to Duplicate Record Data sharing policies, than the ones listed below, they are not officially supported.

Finance
-------

| **Table Object Name**        | **Table Description (Label)**   |
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

Tax
| **Table Object Name**           | **Table Description (Label)** |
|---------------------------------|-------------------------------|
| TaxAuthorityAddress             | Authority                     |
| TaxAuthorityAddressRegistration | Authority registration number |
| TaxGroupHeading                 | Sales tax group description   |
| TaxItemGroupHeading             | Item sales tax group          |
| TaxParameters                   | Sales tax parameters          |
| TaxPeriodHead                   | Sales tax period description  |

Supply Chain
| **Table Object Name**                        | **Table Description (Label)**                          |
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

Project Operations
| **Table Object Name** | **Table Description (Label)** |
|-----------------------|-------------------------------|
| CategoryTable         | Category table                |
| ProjLineProperty      | Line property                 |

Additional tables when the Customer and vendor master sharing feature is enabled
| **Table Object Name**              | **Table Description (Label)**                                                    |
|------------------------------------|----------------------------------------------------------------------------------|
| BankConstantSymbol                 |  Bank constant symbols                                                           |
| BankCustPaymIdTable                |  Payment ID                                                                      |
| BankTransactionTypeGroupHeader     |  Bank transaction groups                                                         |
| ContactPerson                      |  Contacts                                                                        |
| CreditCardCust                     |   Customer credit card                                                           |
| CustFineSetup_BR                   |  Fine codes                                                                      |
| CustInterestSetup_BR               |  Interest codes                                                                  |
| CustomChequeLayout_BR              |   Custom check layout                                                            |
| CustomsTariffCodeTable_IN          |   Customs tariff codes                                                           |
| ExciseTariffCodes_IN               |   Excise tariff codes                                                            |
| LvPaymTransCodes                   |   Payment transaction code                                                       |
| PaymentFormatCodeSets_W            |   Payment format code sets                                                       |
| RetailCustTable                    |   Customers (Retail)                                                             |
| RetailVendTable                    |   Product import vendor setup                                                    |
| SalesTaxFormTypes_IN               |   India sales tax form types                                                     |
| smmResponsibilitiesEmpTable        |   Responsibility assignments                                                     |
| StatRepInterval                    |   Statistics                                                                     |
| StatRepIntervalLine                |   Aging periods                                                                  |
| TaxBranch                          |   Tax branch                                                                     |
| TaxComponentTable_IN               | Tax components                                                                   |
| TaxInformationCustTable_IN         |   Tax Information of Customer                                                    |
| TaxInformationVendTable_IN         |   Tax Information of Vendor                                                      |
| TaxLedgerAccountGroup_IN           |   Tax ledger posting group                                                       |
| TaxVatNumTable                     | Tax exempt number table                                                          |
| TaxWithholdComponentGroupTable_IN  |   Withholding tax component groups                                               |
| TaxWithholdComponentTable_IN       |   Withholding tax components                                                     |
| TaxWithholdTable                   |   Withholding tax codes                                                          |
| VendBankAccount                    |   Vendor bank accounts                                                           |
| VendContractZakat_SA               |   Contractor                                                                     |
| VendDefaultAccounts                |   Default ledger accounts for vendors                                            |
| VendDefaultLocation                |   The VendDefaultLocation contains the default locations by purpose for a vendor |
| VendFineSetup_BR                   |   Fine codes                                                                     |
| VendInfoZakat_SA                   |  Vendors                                                                         |
| VendInterestSetup_BR               |   Interest codes                                                                 |
| VendStateTaxID                     |   Vendor state tax IDs                                                           |
| VendTable                          | Vendors                                                                          |

Available duplicate records data sharing templates
| **Package name on LCS**             | **Data sharing policies** |
|-------------------------------------|---------------------------|
| Financial data sharing templates    | Bank parameters           |
| Supply chain data sharing templates | Barcode parameters        |

•	Ledger journal names
•	Payment days
•	Payment schedules
•	Payment terms
•	Tax exempt codes
•	Barcode setup
•	Buyer group
•	Charges group
•	Commission
•	Destination code
•	Non-conformance type
•	Order entry deadline group
•	Order origin code
•	Order pool
•	Production group
•	Production pool
•	Reason for delivery
•	Supplementary item group
•	Terms of delivery
•	Work time calendar


Download a cross-company data sharing template from LCS
1.	Sign in to LCS.
2.	On the home page, click Shared asset library.
3.	In the Asset type list, click Data package.
4.	Click any of the available data package files to download them.
For details about how to use a template, see Configure financial cross-company data sharing.


Tables officially supported for Master Company Data sharing
Even if it might be possible to add other tables to Master Company Data sharing policies, than the once listed below, they are not officially supported.
Finance
| **Table Object Name**          | **Table Description (Label)**   |
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

Tax
| **Table Object Name**           | **Table Description (Label)** |
|---------------------------------|-------------------------------|
| TaxAuthorityAddress             | Authority                     |
| TaxAuthorityAddressRegistration | Authority registration number |
| TaxGroupHeading                 | Sales tax group description   |
| TaxItemGroupHeading             | Item sales tax group          |
| TaxParameters                   | Sales tax parameters          |
| TaxPeriodHead                   | Sales tax period description  |

Supply Chain
| **Table Name**                       | **Table Description (Label)**              |
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

Additional Supply chain tables when the (Private Preview) Cross-company data sharing for products feature is enabled.
Note: The below tables can be added to a Master Company Data sharing policy but are only supported when the “Cross-company data sharing for products” feature is enabled, which is currently in Private Preview.
| **Table Name**                            | **Table Description (Label)**                  |
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

Project Operations
| **Table Object Name** | **Table Description (Label)** |
|-----------------------|-------------------------------|
| CategoryTable         | Category table                |
| ProjLineProperty      | Line Property                 |







