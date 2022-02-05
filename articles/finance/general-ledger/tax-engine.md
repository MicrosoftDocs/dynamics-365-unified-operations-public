---
# required metadata

title: Tax engine overview
description: This topic provides an overview of the Tax engine functionality in Microsoft Dynamics 365 Finance.
author: kailiang
ms.date: 12/15/2017
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ERSolutionTable, ERDataModelDesigner, ERModelMappingTable
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 

ms.search.region: India
# ms.search.industry: 
ms.author: kailiang
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3

---

# Tax engine overview

[!include [banner](../includes/banner.md)]

The Tax engine is an essential part of the configurable business application experience in Dynamics 365 Finance. It's highly customizable and lets a business user, functional consultant, or power user configure tax rules that determine tax applicability, calculation, posting, and settlement, based on legal and business requirements. 

> [!NOTE]
> The Tax engine functionality is only available for legal entities with a primary address in India.

For a quick overview of the tax engine, watch the following video.

- [Tax engine overview (YouTube video)](https://www.youtube.com/watch?v=jAFpEBOtNWI&feature=youtu.be)

## Key concepts

| Concept           | Description |
|-------------------|-------------|
| Taxable document  | A taxable document is an abstract representation of a document that enables tax calculation in an enterprise resource planning (ERP) system. |
| Tax document      | A tax document is a transaction that has tax details (lines and amounts), where the tax amount is distributed in a manner that is ready for consumption by any accounting system or framework. |
| Tax applicability | <ul><li>**Tax type** – A tax type is analogous to a tax regime. Sales tax and value-added tax (VAT) are two typical types of sales tax. Tax types apply only when specific conditions (applicability rules) are met.</li><li>**Tax components** – Tax components are like sub-tax types that a tax authority can levy in the same jurisdiction or a different jurisdiction. For example, in the US, sales tax is levied at various levels of jurisdiction, such as the state, county, or city level. Different tax components can have a different treatment from an accounting, tax reporting, tax settlement, or other perspective.</li></ul> |
| Tax calculation   | See [Tax calculation](#tax-calculation). |
| Tax accounting    | See [Tax accounting](#tax-accounting). |

## Tax calculation

### Measures

Measures are the computation blocks for tax calculation. Measures can be of various types (measure types) that have different behavior and are used for different computational purposes.

The following measure types are available.

| Measure type | Description |
|--------------|-------------|
| Base Amount  | This measure type should be used to hold the amount that is the basis for tax calculation. Typically, **Base Amount** × **Rate** = **Tax Amount**. |
| Rate         | This special measure type is used to provide the applicable tax rate. It's a compound measure type and can also be used to hold threshold amount values, as required. |
| Factor       | This special measure type is a subset of the **Rate** measure type. It can be used to hold threshold amount values, as required. |
| Tax Amount   | This measure type equals **Base Amount** × **Rate**. This amount should then be distributed for accounting purposes, as required. |
| Amount       | This measure type should be used for distributed tax amounts, such as the tax recoverable amount or the load on inventory amount. |
| Percentage   | This simple measure type is used to hold any percentage value. Typically, it should be used for cases such as the load on inventory percentage or the expense percentage. |

### Formulas

After the measures have been defined, you can use them to write the tax calculation formula. You can write the formula in two notations:

- **Simple Assignment Notation** – Use this notation for normal scenarios.
- **Advanced Linear Equations** – Use this notation specifically for price-inclusive tax calculation scenarios, such as maximum retail price (MRP).

Formulas might have to be used conditionally. In this case, the user should add appropriate business conditions.

### Key model attributes that should be assigned for calculation

The following table lists the keywords that are reserved for attributes. When you create a new taxable document model, make sure that you define the model's attributes according to the information in this table.

| Attribute name               | Data type |
|------------------------------|-----------|
| Base Amount                  | Real      |
| Price includes tax           | Real      |
| Tax amount included in price | Real      |
| Line tax amount              | Real      |

These attributes are available in the Taxable Document (India) model that Microsoft provides:

- **Base Amount** – This attribute is an output attribute and is used as the base amount for tax calculation.
- **Price includes tax** – This attribute is more like a flag that tells the Tax engine that the tax amount is included in the line amount.
- **Tax amount included in price** – This attribute is the tax amount that should be considered included in the price, per the business practice or statutory laws. The Tax engine uses this value to determine the invoice line amount and the amount that should be considered during accounting.
- **Line tax amount** – This attribute is the tax amount that is computed for the line. This value remains the same across the price-exclusive and price-inclusive scenarios. Typically, withholding tax amounts should not be considered when this attribute is initialized.

These attributes should be initialized and used in the following manner in the tax document configuration.

#### Example: Price-inclusive scenario

> 'Base Amount' = 'Assessable Value' – CGST.'Tax Amount' – 'SGST'.'Tax Amount' – 'IGST'.'Tax Amount' – CESS.'Tax Amount' – CGST\_TDS.'Tax Amount' – SGST\_TDS.'Tax Amount' – IGST\_TDS.'Tax Amount' – CESS\_TDS.'Tax Amount'
>
> 'Price includes tax' = 1.0
>
> 'Line tax amount' = CGST.'Tax Amount' + 'SGST'.'Tax Amount' + 'IGST'.'Tax Amount' + 'CESS'.'Tax Amount' + CGST\_TDS.'Tax Amount' + SGST\_TDS.'Tax Amount' + IGST\_TDS.'Tax Amount' + CESS\_TDS.'Tax Amount'
>
> 'Tax amount included in price' = CGST.'Tax Amount' + 'SGST'.'Tax Amount' + 'IGST'.'Tax Amount' + 'CESS'.'Tax Amount' + CGST\_TDS.'Tax Amount' + SGST\_TDS.'Tax Amount' + IGST\_TDS.'Tax Amount' + CESS\_TDS.'Tax Amount'

#### Example: Price-exclusive scenario

> 'Base Amount'='Assessable Value'
>
> 'Price includes tax' = 0.0
>
> 'Line tax amount' = CGST.'Tax Amount' + 'SGST'.'Tax Amount' + 'IGST'.'Tax Amount' + BCD.'Tax Amount' + 'ECESS C'.'Tax Amount' + 'SHECESS C'.'Tax Amount' + 'CESS'.'Tax Amount' + CGST\_TDS.'Tax Amount' + SGST\_TDS.'Tax Amount' + IGST\_TDS.'Tax Amount' + CESS\_TDS.'Tax Amount'

For the price-exclusive scenario, the engine implicitly initializes the **Tax amount included in price** attribute to **0** (zero). Therefore, the equation doesn't have to be written explicitly.

## Tax accounting

### Tax accounting provider

The tax accounting provider is the sub-ledger that the tax accounting scenario affects. For example, in the purchase flow, if tax must be paid to the vendor as part of the vendor invoice, the tax accounting provider is **Party/Vendor**. The list of tax accounting providers depends on the underlying ERP system. For Finance, the following tax accounting providers are available:

- Party
- Inventory
- Tax
- Ledger

### Posting types

When the tax accounting process affects the Tax sub-ledger, the tax amount must be distrusted further for settlement, reporting, costing, and similar purposes. The list of posting types can vary, based on country/region-specific regulations about tax types. For India, the following posting types are available:

- Tax Recoverable
- Tax Payable
- Tax Expense
- Deferred Tax Recoverable
- Interim Tax Payable
- Interim Tax Recoverable

### Tax credit pool

The following illustration shows an example of the tax credit pool for India Goods and Services Tax (GST).

![India GST Example.](../localizations/media/ind-gst.png)

When the preceding configuration is used, the tax recoverable amount and the tax payable amount will be accumulated on each tax credit pool.

### Set-off rule

The set-off rule determines how the tax recoverable should be used to set off the tax payable. The example in the following table shows how the set-off rule might be set up for India GST.

| Recoverable side | Payable side     |
|------------------|------------------|
| IGST             | IGST, CGST, SGST |
| CGST             | CGST, IGST       |
| SGST             | SGST, IGST       |
| CESS             | CESS             |
| CGST\_TDS        | CGST             |
| SGST\_TDS        | SGST             |
| IGST\_TDS        | IGST             |
| CESS\_TDS        | CESS\_TDS        |

## Additional resources

- [Extend tax engine configurations](extend-tax-engine-configurations.md)
- [Tax engine integration](tax-engine-integration.md)



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
