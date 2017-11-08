---
# required metadata

title: Tax engine
description: This topic provides an overview of the tax engine functionality in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.
author: RichardLuan
manager: AnnBe
ms.date: 11/08/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

#ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: riluan
ms.search.validFrom:
ms.dyn365.ops.version: 

---

# Tax engine overview

[!include[banner](../includes/banner.md)]

The Tax Engine is an essential part of the configurable business application experience in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. It is highly customizable and lets the business user, a functional consultant, or a power user to configure tax rules that determine tax applicability,tax calculation, posting, and settlement, based on legal and business requirements.

## Key concepts

|Concept| Description |
|-------|-----|
|**Taxable document**|A taxable document is an abstract representation of document which allows tax calculation in ERP system.
|**Tax document**|A transaction with tax details (lines, amounts) and the tax amount distributed in a manner which is ready for consumption by any accounting system/framework.|
|**Tax applicability**|**Tax type**: Tax type is analogous to a Tax Regime. Sales Tax and Value Added Tax (VAT) are some of the most common example of sales tax types. Tax types are applicable only when certain conditions (applicability rules) are met. **Tax components**: Tax components are like sub-tax types which could be levied by a tax authority within the same or a different jurisdiction. For example, in US, Sales Tax is levied at different levels of jurisdiction: State, Country or City for example. Different tax components may have different treatment from an accounting, tax reporting, tax settlement and other perspectives. |
|**Tax calculation**| See [Tax calulation](#tax-calculation).|
|**Tax accounting**| See [Tax accounting](#tax-accounting).|

## Tax calculation

### Measures

Measures are the computation blocks for tax calculation. Measures can be of different types (Measure types) which have different behavior and are used for different computational purposes. 

The below Measure Types are available:

|Measure type               |Additional information                                                                                 |
|---------------------------|-------------------------------------------------------------------------------------------------------|
|**Base Amount**            |This should be used for holding the amount which is the basis for tax calculation. Typically, Base Amount*Rate should give yield the Tax Amount.|
|**Rate**                   |is a special measure type which is used to provide the applicable tax rate. This is a compound measure type and can also be used for holding threshold amount values if necessary.|
|**Factor**:                | is a special measure type as subset measure type of ‘Rate’. This can be used for holding threshold amount values if necessary.|
|**Tax Amount**             | is Base Amount*Rate. This amount should then be distributed for accounting purposes if necessary.|
|**Amount**                 |This should be used for distributed tax amounts. For example, tax recoverable amount, load on inventory amount etc.|
|**Percentage**             |This is a simple measure type to hold any percentage values. Normally this should be used for cases like Load on Inventory percentage, or expense percentage etc.|

#### Formulas

Once the measures have been defined, you can use them to write the tax calculation formula. You can write the formula in two notations:

-	Simple Assignment Notation: for normal scenarios.
-	Advanced Linear Equations: specifically, for price inclusive tax calculation scenarios, like M.R.P.

Additionally, formulas may need to be used conditionally in which case the user should add appropriate business conditions.

#### Key Model Attributes that should be assigned for Calculation

The following table lists keywords that are reserved for attributes. When you create a new taxable document model, ensure that the model’s attributes are defined as specified in the following table.

| Attribute Name               | Data Type |
|------------------------------|-----------|
| Base Amount                  | Real      |
| Price includes tax           | Real      |
| Tax amount included in price | Real      |
| Line tax amount              | Real      |

These attributes are available in the Taxable Document (India) model provided by Microsoft.

- Base Amount: This attribute is an output attribute, and it is used as base amount for tax calculation.
- Price includes tax: This attribute is more like a flag which tell the engine that the tax amount is included in the line amount.
- Tax amount included in price: The tax amount that should be considered as included in price as per the business practice or statutory laws. The engine uses this value to determine the invoice line amount and the amount that should be considered during accounting.
- Line tax amount: The tax amount computed for the line. This value would remain the same across the price exclusive and price inclusive scenarios. Withholding tax amounts should not be considered while initializing this attribute, normally.

These should be initialized and used in the below manner in the tax document configuration:

##### Price inclusive scenario:

EXAMPLE:

>'Base Amount' = 'Assessable Value' - CGST.'Tax Amount' - 'SGST'.'Tax Amount' - 'IGST'.'Tax Amount' - CESS.'Tax Amount' - CGST_TDS.'Tax Amount' - SGST_TDS.'Tax Amount' - IGST_TDS.'Tax Amount' - CESS_TDS.'Tax Amount'
>
>'Price includes tax' = 1.0
>
>'Line tax amount' = CGST.'Tax Amount' + 'SGST'.'Tax Amount' + 'IGST'.'Tax Amount' + 'CESS'.'Tax Amount' + CGST_TDS.'Tax Amount' + SGST_TDS.'Tax Amount' + IGST_TDS.'Tax Amount' + CESS_TDS.'Tax Amount'
>
>'Tax amount included in price' = CGST.'Tax Amount' + 'SGST'.'Tax Amount' + 'IGST'.'Tax Amount' + 'CESS'.'Tax Amount' + CGST_TDS.'Tax Amount' + SGST_TDS.'Tax Amount' + IGST_TDS.'Tax Amount' + CESS_TDS.'Tax Amount'

##### Price exclusive scenario:

>'Base Amount'='Assessable Value'
>
>'Price includes tax' = 0.0
>
>'Line tax amount'=CGST.'Tax Amount' + 'SGST'.'Tax Amount' + 'IGST'.'Tax Amount'+BCD.'Tax Amount' + 'ECESS C'.'Tax Amount' + 'SHECESS C'.'Tax Amount' + 'CESS'.'Tax Amount' + CGST_TDS.'Tax Amount' + SGST_TDS.'Tax Amount' + IGST_TDS.'Tax Amount' + CESS_TDS.'Tax Amount'

The ‘Tax amount included in price’ is initialized to zero implicitly by the engine for the price exclusive scenario and therefore the equation need not be written explicitly.

### Tax accounting

#### Tax accounting provider

It is the sub-ledger which will be impacted for the tax accounting scenario. For example, in the purchase flow if tax must be paid to the vendor as part of the vendor invoice the tax accounting provider will be Party/Vendor. This list will depend on the underlying ERP system. From an AX perspective, these are the providers which are currently supported:

-	Party
-	Inventory
-	Tax
-	Ledger

#### Posting types

When the Tax sub-ledger is impacted as part of the tax accounting process, the tax amount needs to be distrusted further for settlement, reporting, costing and similar purposes. This list could also vary based on the country specific regulations based on tax types. For India, below is a list of posting types that is supported:

-	Tax Recoverable
-	Tax Payable
-	Tax Expense
-	Deferred Tax Recoverable
-	Interim Tax Payable
-	Interim Tax Recoverable

#### Tax credit pool

When configured as above, the tax recoverable and payable amount will be accumulated on each of the Tax credit pool. 

#### Set off rule

Set-off rule indicates how the tax recoverable should be utilized to set-off tax payable. Details setup are as below for Indian GST: 

| Recoverable side | Payable side             |
|------------------|--------------------------|
|    IGST          |    IGST   CGST   SGST    |
|    CGST          |    CGST   IGST           |
|    SGST          |    SGST   IGST           |
|    CESS          |    CESS                  |
|    CGST_TDS      |    CGST                  |
|    SGST_TDS      |    SGST                  |
|    IGST_TDS      |    IGST                  |
|    CESS_TDS      |    CESS_TDS              |
