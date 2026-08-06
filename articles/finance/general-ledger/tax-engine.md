---
title: Tax engine overview
description: Learn about the Tax engine functionality in Microsoft Dynamics 365 Finance, a table that defines various key concepts and an outline on tax calculations.
author: kailiang
ms.author: kailiang
ms.topic: overview
ms.date: 07/30/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: India
ms.search.validFrom: 2017-12-31
ms.search.form: ERSolutionTable, ERDataModelDesigner, ERModelMappingTable
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

Measures are the computation blocks for tax calculation. Measures come in various types, each with different behaviors and computational purposes.

The following measure types are available:

| Measure type | Description |
|--------------|-------------|
| Base Amount  | Use this measure type to hold the amount that serves as the basis for tax calculation. Typically, **Base Amount** × **Rate** = **Tax Amount**. |
| Rate         | Use this special measure type to provide the applicable tax rate. It's a compound measure type and can also hold threshold amount values, as required. |
| Factor       | This special measure type is a subset of the **Rate** measure type. It can hold threshold amount values, as required. |
| Tax Amount   | This measure type equals **Base Amount** × **Rate**. Distribute this amount for accounting purposes, as required. |
| Amount       | Use this measure type for distributed tax amounts, such as the tax recoverable amount or the load on inventory amount. |
| Percentage   | Use this simple measure type to hold any percentage value. Typically, use it for cases such as the load on inventory percentage or the expense percentage. |

### Formulas

After you define the measures, use them to write the tax calculation formula. You can write the formula in two notations:

- **Simple Assignment Notation** – Use this notation for normal scenarios.
- **Advanced Linear Equations** – Use this notation specifically for price-inclusive tax calculation scenarios, such as maximum retail price (MRP).

You might need to use formulas conditionally. In this case, add appropriate business conditions.

### Key model attributes for calculation

The following table lists the keywords reserved for attributes. When you create a new taxable document model, make sure that you define the model's attributes according to the information in this table.

| Attribute name               | Data type |
|------------------------------|-----------|
| Base Amount                  | Real      |
| Price includes tax           | Real      |
| Tax amount included in price | Real      |
| Line tax amount              | Real      |

These attributes are available in the Taxable Document (India) model that Microsoft provides:

- **Base Amount** – This attribute is an output attribute and is used as the base amount for tax calculation.
- **Price includes tax** – This attribute acts as a flag that tells the Tax engine that the tax amount is included in the line amount.
- **Tax amount included in price** – This attribute is the tax amount that should be considered included in the price, per the business practice or statutory laws. The Tax engine uses this value to determine the invoice line amount and the amount that should be considered during accounting.
- **Line tax amount** – This attribute is the tax amount that is computed for the line. This value remains the same across the price-exclusive and price-inclusive scenarios. Typically, withholding tax amounts aren't considered when this attribute is initialized.

Initialize and use these attributes in the following manner in the tax document configuration.

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

For the price-exclusive scenario, the engine implicitly initializes the **Tax amount included in price** attribute to **0** (zero). Therefore, you don't need to write the equation explicitly.

## Tax accounting

### Tax accounting provider

The tax accounting provider is the sub-ledger that the tax accounting scenario affects. For example, in the purchase flow, if you pay tax to the vendor as part of the vendor invoice, the tax accounting provider is **Party/Vendor**. The list of tax accounting providers depends on the underlying ERP system. For Finance, the following tax accounting providers are available:

- Party
- Inventory
- Tax
- Ledger

### Posting types

When the tax accounting process affects the Tax sub-ledger, you must distribute the tax amount further for settlement, reporting, costing, and similar purposes. The list of posting types can vary, based on country or region-specific regulations about tax types. For India, the following posting types are available:

- Tax Recoverable
- Tax Payable
- Tax Expense
- Deferred Tax Recoverable
- Interim Tax Payable
- Interim Tax Recoverable

### Tax credit pool

The following illustration shows an example of the tax credit pool for India Goods and Services Tax (GST).

:::image type="content" source="../localizations/media/ind-gst.png" alt-text="Screenshot of an example tax credit pool setup for India GST.":::

When you use the preceding configuration, each tax credit pool accumulates the tax recoverable amount and the tax payable amount.

### Set-off rule

The set-off rule determines how to use the tax recoverable to set off the tax payable. The following table shows an example of how to set up the set-off rule for India GST.

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

- [Extend tax engine configurations](../dev-itpro/extend-tax-engine-configurations.md)
- [Tax engine integration](../dev-itpro/tax-engine-integration.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
