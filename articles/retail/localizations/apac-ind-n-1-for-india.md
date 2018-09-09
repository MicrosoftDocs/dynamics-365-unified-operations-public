---
# required metadata

title: Support for upgrade and N-1 for India
description: This topic provides an overview N-1 support for Retail customers in India
author: DmitryAkimoff 
manager: ezubov
ms.date: 10/01/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
ms.search.industry: Retail
ms.author: dmakimo
ms.search.validFrom: 2018-10-01
ms.dyn365.ops.version: 8.1
---
# Support for upgrade and N-1 for India

This topic describes additional steps to set up and use Phased Rollout (N-1) retail components for India. For general information about N-1 installation and usage, see [Upgrade and N-1 support for Retail](../dev-itpro/overview-upgrade-n-minus1.md).

> [!NOTE]
> This topic applies to both Microsoft Dynamics 365 for Finance and Operations, and Microsoft Dynamics 365 for Retail.

## Prerequisites

- Update AX 2013 R3 retail components to GST Update 2, [KB4058327](https://fix.lcs.dynamics.com/Issue/Details?kb=4058327&bugId=3898178&qc=acbe1a0b3f5d9240d56a94a633fa69fbfe4be0cf98587fd05a7807e082210a12). For details, please, see [India GST Update 2 - Release Notes](https://mbs.microsoft.com/Files/customer/AX/Downloads/Taxupdates/Release-Note-India-GST-Update-2.pdf).
- Set up basic N-1 environment. For more information, please, refer to [Phased Rollout (N-1) installation, configuration, and cutover guide](../dev-itpro/n-1-installation-configuration.md).
- Set up Goods and Services Tax (GST) for Retail in Microsoft Dynamics 365 headquarters according to the guide [Goods and Services Tax (GST) integration for cash registers for India](./apac-ind-cash-registers.md)

## Periodic procedure to downgrade tax configuration

GST tax configuration data differs between AX 2012 and Dynamics 365 versions. Special periodic procedure shoud be launched to transfrom data. 

1. Sign in to Retail headquarters, and go to Retail \> Retail IT \> Process tax configuration from N-1


Each time tax configuration changes are applied and completed the above operation should be launched before sending the data to AX 2012 channel.

## Additional distribution jobs for AX 2012 retail scheduler

Add the following list of fields and tables to AX 2012 Commerce Data Exchange (CDX) syncronization:

- Upload distribution
 
|Table Name                             |Field name                          |
|----                                   |----                                |
|RetailTransactionMarkupTrans           |Exempt_IN                           |
|                                       |HSNCode_IN                          |
|                                       |ITCCategory_IN                      |
|                                       |ServiceAccountingCode_IN            |
|                                       |ServiceCategory_IN                  |
|RetailTransactionSalesTrans            |Exempt_IN                           |
|                                       |HSNCode_IN                          |
|                                       |ServiceAccountingCode_IN            |
|RetailTransactionTable                 |TaxCalculationType                  |
|RetailTransactionTaxMeasure            |Channel                             |
|                                       |Path                                |
|                                       |ReplicationCounterFromOrigin        |
|                                       |SaleLineNum                         |
|                                       |StoreId                             |
|                                       |TerminalId                          |
|                                       |TransactionId                       |
|                                       |Value                               |
|RetailTransactionTaxTransGTE           |Channel                             |
|                                       |IsIncludedInPrice                   |
|                                       |ReplicationCounterFromOrigin        |
|                                       |SaleLineNum                         |
|                                       |StoreId                             |
|                                       |TaxAmount                           |
|                                       |TaxBasis                            |
|                                       |TaxComponent                        |
|                                       |TaxPercentage                       |
|                                       |TerminalId                          |
|                                       |TransactionId                       |

- Download distribution  

|Table Name                             |Field name                          |
|----                                   |---                                 |
|ERSolutionTable                        |Base                                |
|                                       |Description                         |
|                                       |GUID                                |
|                                       |Name                                |
|                                       |RecId                               |
|                                       |SolutionTypeLegacy, target field SolutionType|
|ERSolutionVersionComponentTableLegacy, target table ERSolutionVersionComponentTable|ComponentGUID|
|                                       |ComponentName                       |
|                                       |ComponentType                       |
|                                       |ComponentVersionNumber              |
|                                       |RecId                               |
|                                       |SolutionVersion                     |
|ERSolutionVersionTable                 |Base                                |
|                                       |RecId                               |
|                                       |Solution                            |
|                                       |VersionNumber                       |
|                                       |XmlLegacy ToName=XML                |
|HSNCodeTable_IN                        |Code                                |
|                                       |RecId                               |
|InventTable                            |Exempt_IN                           |
|                                       |HSNCodeTable_IN                     |
|                                       |ServiceAccountingCodeTable_IN       |
|MarkupTable_IN                         |Exempt                              |
|                                       |HSNCodeTable                        |
|                                       |ITCCategory                         |
|                                       |MarkupTable                         |
|                                       |RecId                               |
|                                       |ServiceAccountingCodeTable          |
|                                       |ServiceCategory                     |
|TaxDocumentRowDeterminedComponent      |DeterminedInfo                      |
|                                       |DocComponentPath                    |
|                                       |RecId                               |
|TaxDocumentRowMeasureAdjustment        |AdjustAmount                        |
|                                       |AdjustAmount_AccCur                 |
|                                       |AdjustAmount_Trans                  |
|                                       |Path                                |
|                                       |RecId                               |
|                                       |SourceRecId                         |
|                                       |SourceTableId                       |
|TaxDocumentRowTaxDeterminedInfo        |IsManualDetermined                  |
|                                       |OriginSourceRecId                   |
|                                       |OriginSourceTableId                 |
|                                       |RecId                               |
|TaxEngineSQLDictionary                 |Name                                |
|                                       |RecId                               |
|                                       |RefFieldId                          |
|                                       |RefTableId                          |
|                                       |SQLName                             |
|TaxInformation_IN                      |GSTIN                               |
|TaxInformationCustTable_IN             |CustTable                           |
|                                       |IsForeign                           |
|                                       |IsPreferential                      |
|                                       |NatureOfAssessee                    |
|                                       |RecId                               |
|TaxMeasureType                         |AllowLedgerPosting                  |
|                                       |AllowRounding                       |
|                                       |ClassName                           |
|                                       |Description                         |
|                                       |DisplayName                         |
|                                       |ERDataItemType                      |
|                                       |IsEvaluable                         |
|                                       |IsRawType                           |
|                                       |isStructural                        |
|                                       |Master                              |
|                                       |RecId                               |
|TaxMeasureTypeDetail                   |ParentType                          |
|                                       |RecId                               |
|                                       |Type                                |
|TaxPeriodHeader                        |Name                                |
|                                       |RecId                               |
|                                       |TaxPeriodId                         |
|TaxRtDocCompFormulaCompMeasure         |IsNativeInput                       |
|                                       |RecId                               |
|                                       |TaxRuntimeDocComponentFormulaVersion|
|                                       |TaxRuntimeDocComponentMeasureVersion|
|TaxRtDocCompPostingProfDetVersion      |CreditAccountingProvider            |
|                                       |CreditAccountType                   |
|                                       |CreditPostingTypeVersion            |
|                                       |DebitAccountingProvider             |
|                                       |DebitAccountType                    |
|                                       |DebitPostingTypeVersion             |
|                                       |Description                         |
|                                       |DistributionSide                    |
|                                       |DocContextVersion                   |
|                                       |DocMeasureVersion                   |
|                                       |PostingProfileDet                   |
|                                       |PostingProfileVersion               |
|                                       |RecId                               |
|                                       |SettlementAccountingOption          |
|TaxRtDocCompPostingProfVersion         |Description                         |
|                                       |DocContextVersion                   |
|                                       |PostingProfile                      |
|                                       |RecId                               |
|                                       |TaxRuntimeDocComponentVersion       |
|                                       |TaxRuntimeDocModelRowVersion        |
|TaxRtLookupStructFieldBindingVersion   |BindingSourcePath                   |
|                                       |Description                         |
|                                       |DocContextVersion                   |
|                                       |ERDataItemType                      |
|                                       |LookupStructureBindingVersion       |
|                                       |LookupStructureFieldBinding         |
|                                       |LookupStructureFieldVersion         |
|                                       |RecId                               |
|                                       |ReferenceModelName                  |
|TaxRtLookupStructFieldCondColumnLink   |DocContextVersion                   |
|                                       |LookupConditionIdx                  |
|                                       |LookupStructure                     |
|                                       |LookupStructureField                |
|                                       |LookupStructureFieldType            |
|                                       |RecId                               |
|TaxRuntimeComponent                    |DefContext                          |
|                                       |Name                                |
|                                       |RecId                               |
|                                       |ReferenceId                         |
|                                       |TaxRuntimeTaxType                   |
|TaxRuntimeComponentMeasure             |DefContext                          |
|                                       |Name                                |
|                                       |ParentMeasure                       |
|                                       |RecId                               |
|                                       |ReferenceId                         |
|                                       |Root                                |
|                                       |TaxMeasureType                      |
|                                       |TaxRuntimeComponent                 |
|                                       |TaxRuntimeMeasure                   |
|TaxRuntimeComponentMeasureVersion      |DefContextVersion                   |
|                                       |Description                         |
|                                       |LeftId                              |
|                                       |Level                               |
|                                       |ParentMeasureVersion                |
|                                       |RecId                               |
|                                       |RightId                             |
|                                       |RootVersion                         |
|                                       |TaxRuntimeComponentMeasure          |
|                                       |TaxRuntimeComponentVersion          |
|                                       |TaxRuntimeMeasureVersion            |
|TaxRuntimeComponentVersion             |DefContextVersion                   |
|                                       |Description                         |
|                                       |RecId                               |
|                                       |TaxRuntimeComponent                 |
|                                       |TaxRuntimeTaxTypeVersion            |
|TaxRuntimeDefContext                   |Name                                |
|                                       |RecId                               |
|                                       |ReferenceId                         |
|                                       |Solution                            |
|                                       |TaxSolutionScope                    |
|TaxRuntimeDefContextVersion            |Description                         |
|                                       |RecId                               |
|                                       |SolutionVersion                     |
|                                       |TaxRuntimeDefContext                |
|TaxRuntimeDocComponent                 |DocContext                          |
|                                       |Name                                |
|                                       |Path                                |
|                                       |RecId                               |
|                                       |ReferenceId                         |
|                                       |TaxRuntimeComponent                 |
|                                       |TaxRuntimeDocTaxType                |
|TaxRuntimeDocComponentMeasure          |DocContext                          |
|                                       |FullPath                            |
|                                       |Name                                |
|                                       |ParentMeasure                       |
|                                       |Path                                |
|                                       |RecId                               |
|                                       |ReferenceId                         |
|                                       |Root                                |
|                                       |TaxMeasureType                      |
|                                       |TaxRuntimeComponentMeasure          |
|                                       |TaxRuntimeDocComponent              |
|                                       |TaxRuntimeMeasure                   |
|TaxRuntimeDocComponentMeasureVersion   |Description                         |
|                                       |DocContextVersion                   |
|                                       |LeftId                              |
|                                       |Level                               |
|                                       |ParentMeasureVersion                |
|                                       |RecId                               |
|                                       |RightId                             |
|                                       |RootVersion                         |
|                                       |RoundingTo                          |
|                                       |RoundingType                        |
|                                       |SettlementRoundingTo                |
|                                       |SettlementRoundingType              |
|                                       |TaxRuntimeComponentMeasureVersion   |
|                                       |TaxRuntimeDocComponentMeasure       |
|                                       |TaxRuntimeDocComponentVersion       |
|                                       |TaxRuntimeDocModelRowVersion        |
|                                       |TaxRuntimeMeasureVersion            |
|TaxRuntimeDocComponentPostingProfile   |DocContext                          |
|                                       |Name                                |
|                                       |RecId                               |
|                                       |ReferenceId                         |
|                                       |TaxRuntimeDocComponent              |
|TaxRuntimeDocComponentPostingProfileDet|CreditPostingType                   |
|                                       |DebitPostingType                    |
|                                       |DocContext                          |
|                                       |Name                                |
|                                       |PostingProfile                      |
|                                       |RecId                               |
|                                       |ReferenceId                         |
|TaxRuntimeDocComponentPostingType      |DocComponent                        |
|                                       |DocContextVersion                   |
|                                       |PostingType                         |
|                                       |RecId                               |
|TaxRuntimeDocComponentVersion          |Description                         |
|                                       |DocContextVersion                   |
|                                       |RecId                               |
|                                       |TaxRuntimeComponentVersion          |
|                                       |TaxRuntimeDocComponent              |
|                                       |TaxRuntimeDocModelRowVersion        |
|                                       |TaxRuntimeDocTaxTypeVersion         |
|TaxRuntimeDocContext                   |Name                                |
|                                       |RecId                               |
|                                       |ReferenceId                         |
|                                       |Solution                            |
|                                       |TaxSolutionScope                    |
|TaxRuntimeDocContextVersion            |Description                         |
|                                       |RecId                               |
|                                       |SolutionVersion                     |
|                                       |TaxRuntimeDocContext                |
|TaxRuntimeDocModel                     |DocContext                          |
|                                       |Name                                |
|                                       |RecId                               |
|                                       |ReferenceId                         |
|                                       |TaxRuntimeModel                     |
|TaxRuntimeDocModelAttr                 |DataItemType                        |
|                                       |DefPath                             |
|                                       |DocContext                          |
|                                       |FullPath                            |
|                                       |Name                                |
|                                       |Path                                |
|                                       |RecId                               |
|                                       |ReferenceId                         |
|                                       |TaxRuntimeDocModelRow               |
|                                       |TaxRuntimeModelAttr                 |
|TaxRuntimeDocModelAttrVersion          |DocContextVersion                   |
|                                       |IsSystem                            |
|                                       |RecId                               |
|                                       |TaxRuntimeDocModelAttr              |
|                                       |TaxRuntimeDocModelRowVersion        |
|                                       |TaxRuntimeModelAttrVersion          |
|TaxRuntimeDocModelRow                  |DefPath                             |
|                                       |DocContext                          |
|                                       |FullPath                            |
|                                       |Name                                |
|                                       |Parent                              |
|                                       |Path                                |
|                                       |RecId                               |
|                                       |ReferenceId                         |
|                                       |Root                                |
|                                       |TaxRuntimeDocModel                  |
|                                       |TaxRuntimeModelRow                  |
|TaxRuntimeDocModelRowVersion           |DocContextVersion                   |
|                                       |LeftId                              |
|                                       |Level                               |
|                                       |ParentVersion                       |
|                                       |RecId                               |
|                                       |RightId                             |
|                                       |RootVersion                         |
|                                       |Skipped                             |
|                                       |TaxRuntimeDocModelRow               |
|                                       |TaxRuntimeDocModelVersion           |
|                                       |TaxRuntimeModelRowVersion           |
|                                       |TemplateRowVersion                  |
|TaxRuntimeDocModelVersion              |Description                         |
|                                       |DocContextVersion                   |
|                                       |RecId                               |
|                                       |TaxRuntimeDocModel                  |
|                                       |TaxRuntimeModelVersion              |
|TaxRuntimeDocTaxType                   |DocContext                          |
|                                       |Name                                |
|                                       |Path                                |
|                                       |RecId                               |
|                                       |ReferenceId                         |
|                                       |TaxRuntimeDocModelRow               |
|                                       |TaxRuntimeTaxType                   |
|TaxRuntimeDocTaxTypePostingType        |DocContextVersion                   |
|                                       |DocTaxType                          |
|                                       |PostingType                         |
|                                       |RecId                               |
|TaxRuntimeDocTaxTypeVersion            |Description                         |
|                                       |DocContextVersion                   |
|                                       |RecId                               |
|                                       |RoundingTo                          |
|                                       |RoundingType                        |
|                                       |SettlementRoundingTo                |
|                                       |SettlementRoundingType              |
|                                       |TaxRuntimeDocModelRowVersion        |
|                                       |TaxRuntimeDocTaxType                |
|                                       |TaxRuntimeTaxTypeVersion            |
|TaxRuntimeLookup                       |DocContext                          |
|                                       |LookupOwnerRecId                    |
|                                       |LookupOwnerTableId                  |
|                                       |LookupRefType                       |
|                                       |Name                                |
|                                       |RecId                               |
|                                       |ReferenceId                         |
|TaxRuntimeLookupAccountingResult       |LookupCondition                     |
|                                       |OwnerRecId                          |
|                                       |OwnerTableId                        |
|                                       |RecId                               |
|TaxRuntimeLookupAccountingResultDetail |LedgerDimension                     |
|                                       |LookupAccountingResult              |
|                                       |PostingType                         |
|                                       |RecId                               |
|TaxRuntimeLookupCondition              |DateRangeFrom1                      |
|                                       |DateRangeFrom2                      |
|                                       |DateRangeFrom3                      |
|                                       |DateRangeFrom4                      |
|                                       |DateRangeFrom5                      |
|                                       |DateRangeTo1                        |
|                                       |DateRangeTo2                        |
|                                       |DateRangeTo3                        |
|                                       |DateRangeTo4                        |
|                                       |DateRangeTo5                        |
|                                       |DimValue1                           |
|                                       |DimValue10                          |
|                                       |DimValue11                          |
|                                       |DimValue12                          |
|                                       |DimValue13                          |
|                                       |DimValue14                          |
|                                       |DimValue15                          |
|                                       |DimValue2                           |
|                                       |DimValue3                           |
|                                       |DimValue4                           |
|                                       |DimValue5                           |
|                                       |DimValue6                           |
|                                       |DimValue7                           |
|                                       |DimValue8                           |
|                                       |DimValue9                           |
|                                       |Ledger                              |
|                                       |Lookup                              |
|                                       |LookupVersion                       |
|                                       |NotEmptyDimValueColumnCount         |
|                                       |RecId                               |
|                                       |SortNumber                          |
|                                       |ValueRangeFrom1                     |
|                                       |ValueRangeFrom2                     |
|                                       |ValueRangeFrom3                     |
|                                       |ValueRangeFrom4                     |
|                                       |ValueRangeFrom5                     |
|                                       |ValueRangeTo1                       |
|                                       |ValueRangeTo2                       |
|                                       |ValueRangeTo3                       |
|                                       |ValueRangeTo4                       |
|                                       |ValueRangeTo5                       |
|TaxRuntimeLookupMeasureResult          |LookupCondition                     |
|                                       |OwnerRecId                          |
|                                       |OwnerTableId                        |
|                                       |RecId                               |
|TaxRuntimeLookupMeasureResultDetail    |LookupMeasureResult                 |
|                                       |Measure                             |
|                                       |RecId                               |
|                                       |Value                               |
|TaxRuntimeLookupStructure              |DocContext                          |
|                                       |Name                                |
|                                       |RecId                               |
|                                       |ReferenceId                         |
|TaxRuntimeLookupStructureBinding       |BindingModelRowPath                 |
|                                       |DocContext                          |
|                                       |LookupStructure                     |
|                                       |Name                                |
|                                       |RecId                               |
|                                       |ReferenceId                         |
|TaxRuntimeLookupStructureBindingVersion|Description                         |
|                                       |DocContextVersion                   |
|                                       |LookupStructureBinding              |
|                                       |LookupStructureVersion              |
|                                       |RecId                               |
|TaxRuntimeLookupStructureField         |DocContext                          |
|                                       |Name                                |
|                                       |RecId                               |
|                                       |ReferenceId                         |
|                                       |TaxRuntimeLookupStructure           |
|                                       |Type                                |
|TaxRuntimeLookupStructureFieldBinding  |DocContext                          |
|                                       |LookupStructureBinding              |
|                                       |LookupStructureField                |
|                                       |Name                                |
|                                       |RecId                               |
|                                       |ReferenceId                         |
|TaxRuntimeLookupStructureFieldVersion  |Description                         |
|                                       |DocContextVersion                   |
|                                       |LookupStructureField                |
|                                       |LookupStructureVersion              |
|                                       |RecId                               |
|                                       |Sequence                            |
|TaxRuntimeLookupStructureVersion       |Description                         |
|                                       |DocContextVersion                   |
|                                       |RecId                               |
|                                       |TaxRuntimeLookupStructure           |
|TaxRuntimeLookupTaxPeriodResult        |LookupCondition                     |
|                                       |OwnerRecId                          |
|                                       |OwnerTableId                        |
|                                       |RecId                               |
|                                       |TaxPeriodHeader                     |
|TaxRuntimeLookupVersion                |ConditionSourceType                 |
|                                       |Description                         |
|                                       |DocContextVersion                   |
|                                       |Lookup                              |
|                                       |LookupStructure                     |
|                                       |LookupStructureVersion              |
|                                       |RecId                               |
|TaxRuntimeMeasure                      |DefContext                          |
|                                       |FullPath                            |
|                                       |Name                                |
|                                       |ParentMeasure                       |
|                                       |RecId                               |
|                                       |ReferenceId                         |
|                                       |Root                                |
|                                       |TaxMeasureType                      |
|TaxRuntimeMeasureVersion               |DefContextVersion                   |
|                                       |Description                         |
|                                       |DisplayMode                         |
|                                       |LeftId                              |
|                                       |Level                               |
|                                       |ParentMeasureVersion                |
|                                       |RecId                               |
|                                       |RightId                             |
|                                       |RootVersion                         |
|                                       |TaxRuntimeMeasure                   |
|TaxRuntimeModel                        |DefContext                          |
|                                       |Name                                |
|                                       |RecId                               |
|                                       |ReferenceId                         |
|TaxRuntimeModelAttr                    |DataItemType                        |
|                                       |DefContext                          |
|                                       |FullPath                            |
|                                       |Name                                |
|                                       |Path                                |
|                                       |RecId                               |
|                                       |TaxRuntimeModelRow                  |
|TaxRuntimeModelAttrVersion             |DefContextVersion                   |
|                                       |IsSystem                            |
|                                       |RecId                               |
|                                       |TaxRuntimeModelAttr                 |
|                                       |TaxRuntimeModelRowVersion           |
|TaxRuntimeModelRow                     |DefContext                          |
|                                       |FullPath                            |
|                                       |Name                                |
|                                       |Parent                              |
|                                       |Path                                |
|                                       |RecId                               |
|                                       |Root                                |
|                                       |TaxRuntimeModel                     |
|TaxRuntimeModelRowVersion              |DefContextVersion                   |
|                                       |LeftId                              |
|                                       |Level                               |
|                                       |ParentVersion                       |
|                                       |RecId                               |
|                                       |RightId                             |
|                                       |RootVersion                         |
|                                       |TaxRuntimeModelRow                  |
|                                       |TaxRuntimeModelVersion              |
|TaxRuntimeModelVersion                 |DefContextVersion                   |
|                                       |Description                         |
|                                       |RecId                               |
|                                       |TaxRuntimeModel                     |
|TaxRuntimePostingType                  |DefContext                          |
|                                       |Name                                |
|                                       |RecId                               |
|                                       |ReferenceId                         |
|TaxRuntimePostingTypeVersion           |AccountingProvider                  |
|                                       |AccountType                         |
|                                       |DefContextVersion                   |
|                                       |Description                         |
|                                       |PostingType                         |
|                                       |RecId                               |
|TaxRuntimeReferenceModel               |DefContext                          |
|                                       |IsEnum                              |
|                                       |Name                                |
|                                       |RecId                               |
|TaxRuntimeReferenceModelAttr           |DataItemType                        |
|                                       |DefContext                          |
|                                       |Name                                |
|                                       |Path                                |
|                                       |RecId                               |
|                                       |TaxRuntimeReferenceModel            |
|                                       |TaxRuntimeReferenceModelRow         |
|TaxRuntimeReferenceModelAttrVersion    |DefContextVersion                   |
|                                       |RecId                               |
|                                       |TaxRuntimeReferenceModelAttr        |
|                                       |TaxRuntimeReferenceModelRowVersion  |
|                                       |TaxRuntimeReferenceModelVersion     |
|TaxRuntimeReferenceModelRow            |DefContext                          |
|                                       |Name                                |
|                                       |Parent                              |
|                                       |Path                                |
|                                       |RecId                               |
|                                       |Root                                |
|                                       |TaxRuntimeReferenceModel            |
|TaxRuntimeReferenceModelRowVersion     |DefContextVersion                   |
|                                       |LeftId                              |
|                                       |Level                               |
|                                       |ParentVersion                       |
|                                       |RecId                               |
|                                       |RightId                             |
|                                       |RootVersion                         |
|                                       |TaxRuntimeReferenceModelRow         |
|                                       |TaxRuntimeReferenceModelVersion     |
|TaxRuntimeReferenceModelVersion        |DefContextVersion                   |
|                                       |Description                         |
|                                       |NaturalKey                          |
|                                       |NaturalKeyPath                      |
|                                       |RecId                               |
|                                       |TaxRuntimeReferenceModel            |
|TaxRuntimeTaxType                      |DefContext                          |
|                                       |Name                                |
|                                       |RecId                               |
|                                       |ReferenceId                         |
|TaxRuntimeTaxTypeVersion               |DefContextVersion                   |
|                                       |Description                         |
|                                       |RecId                               |
|                                       |TaxRuntimeTaxType                   |
|TaxSolutionScope                       |Description                         |
|                                       |Name                                |
|                                       |RecId                               |
|                                       |Solution                            |
|                                       |SolutionVersion                     |
|                                       |VersionStatus                       |
|TaxSolutionScopeSetup                  |Ledger                              |
|                                       |RecId                               |
|                                       |Status                              |
|                                       |TaxSolutionScope                    |