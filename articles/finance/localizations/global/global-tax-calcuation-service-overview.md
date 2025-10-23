---
title: Tax Calculation overview
description: Learn about the overall scope and features of the Tax Calculation capability, including outlines on versions, data flows, and supported transactions.
author: epodkolzina
ms.author: epodkolzina
ms.topic: overview
ms.custom: 
  - bap-template
ms.date: 10/14/2025
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2021-04-01
ms.search.form: TaxIntegrationTaxServiceParameters
ms.dyn365.ops.version: 10.0.18
---

# Tax Calculation overview

[!include [banner](../../includes/banner.md)]

Tax Calculation helps automate and simplify the tax determination and calculation process. The tax engine is fully configurable. The elements that can be configured include, but aren't limited to, the taxable data model, tax code, tax applicability matrix, and tax calculation formula. 

Tax Calculation is a highly scalable tax engine that's designed to support you in performing the following tasks:

- Automatically determine the correct sales tax group, item sales tax group, and tax codes through an enhanced determination mechanism.
- Support multiple tax registration numbers in one legal entity, and automatically determine the correct tax registration number on taxable transactions.
- Support tax determination, calculation, posting, and settlement for transfer orders.
- Define configurable tax calculation formulas and conditions for your specific business requirements.
- Share the tax determination and calculation solution across legal entities to save maintenance effort and avoid errors.
- Support customer and vendor tax registration number determination.
- Support list code determination.
- Support tax calculation parameters at the tax jurisdiction level.

For more information, see [Get started with tax service](global-get-started-with-tax-calculation-service.md).

## Versions
We recommend that you import and set up your Tax Calculation configuration with the version that matches your Microsoft Dynamics 365 Finance or Microsoft Dynamics 365 Supply Chain Management version.

| Finance or Supply Chain Management version | Tax configuration version |
| --------------- | --------------------------------------- |
| 10.0.45         | Tax Calculation Configuration 47.73.265 |
| 10.0.44         | Tax Calculation Configuration 47.73.265 |
| 10.0.43         | Tax Calculation Configuration 47.73.265 |
| 10.0.42         | Tax Calculation Configuration 44.70.262 |


## Data flow

Here is an outline of the data flow process for Tax Calculation. 

1. In the **Globalization Studio** workspace in Finance, view and import taxable document model configurations and model mapping configurations. If you must extend configurations for an advanced scenario, see [Add data fields in tax configurations](tax-service-add-data-fields-tax-configurations.md).
2. In the **Globalization Studio** workspace in Finance, create or maintain tax features. You can use tax features to maintain tax rates and tax applicability rules.
3. After the tax feature setup is finalized, change the **Feature version status** to _Completed_. 
4. In **Tax calculation parameters**, select which tax feature setup version to use for a specific legal entity.
5. In Finance and Supply Chain Management, operate transactions as usual. When Tax Calculation is needed, the client collects information from the transaction, such as the sales order or purchase order, and packages the information as payload. A request is then sent to calculate the tax.
6. The tax calculation request is received from the client and the calculation is completed. The tax result is then returned to the client.
7. The Dynamics 365 client receives the tax result and presents the tax calculation result on a sales tax page.

## Supported transactions

Tax Calculation can be enabled by transactions. 

The following table lists the transactions supported in the corresponding version.

| Version | Transactions |
|---------|--------------|
| 10.0.43 | Customer advance invoice<br>Vendor advance invoice<br>Interest note<br>Collection letter |
| 10.0.42 | Slip journal (Cash)<br>[ITA] Customs declaration journal |
| 10.0.41 | Write-off journal<br>Prepayment customer invoice (Sales order) |
| 10.0.40 | [POL] Single Administrative Document (SAD) |
| 10.0.39 | Prepayment handling |
| 10.0.38 | Project invoice proposal<br> Journals (Hour/Expense/Item/Fee)<br> Project quotations<br> Intercompany customer invoice<br> Microsoft Dynamics 365 Project Operations integration journal |
| 10.0.36 | Invoice register<br>Invoice approval<br>Invoice pool |
| 10.0.29 | Periodic journals |
| 10.0.28 | Vendor payment journal<br>Customer payment journal | 
| 10.0.26 | General journals<br>Vendor invoice journal |
| 10.0.23 | Free text invoice |
| 10.0.21| <p>Sales</p><ul><li>Sales quotation</li><li>Sales order</li><li>Confirmation</li><li>Picking list</li><li>Packing slip</li><li>Sales invoice</li><li>Credit note</li><li>Return order</li><li>Header miscellaneous charge</li><li>Line miscellaneous charge</li></ul><p>Purchase</p><ul><li>Purchase order</li><li>Confirmation</li><li>Receipts list</li><li>Product receipt</li><li>Purchase invoice</li><li>Header miscellaneous charge</li><li>Line miscellaneous charge</li><li>Credit note</li><li>Return order</li><li>Purchase requisition</li><li>Purchase requisition line miscellaneous charge</li><li>Request for quotation</li><li>Request for quotation header miscellaneous charge</li><li>Request for quotation line miscellaneous charge</li></ul><p>Inventory</p><ul><li>Transfer order – ship</li><li>Transfer order – receive</li></ul>|

## Supported countries/regions

Tax Calculation can be run with supported localization features. The following table lists the countries/regions for a legal entity's primary address.

| Version | Country/region |
|---------|----------------|
| 10.0.26 | <ul><li>China</li><li>Czech Republic</li><li>Spain</li></ul> |
| 10.0.24 | <ul><li>Mexico</li></ul> |
| 10.0.23 | <ul><li>Thailand</li><li>Japan</li><li>Malaysia</li><li>Singapore</li><li>Indonesia</li></ul> |
| 10.0.22 | <ul><li>Australia</li><li>Bahrain</li><li>Canada</li><li>Egypt</li><li>Hong Kong SAR</li><li>Kuwait</li><li>New Zealand</li><li>Oman</li><li>Qatar</li><li>Saudi Arabic</li><li>South Africa</li><li>United Arab Emirates</li></ul> |
| 10.0.21 | <ul><li>Austria</li><li>Belgium</li><li>Denmark</li><li>Estonia</li><li>Finland</li><li>France</li><li>Germany</li><li>Hungary</li><li>Iceland</li><li>Ireland</li><li>Italy</li><li>Latvia</li><li>Lithuania</li><li>Netherlands</li><li>Norway</li><li>Poland</li><li>Sweden</li><li>Switzerland</li><li>United Kingdom</li><li>United States</li></ul> |

> [!NOTE]
> For any country/region not localized by Microsoft, Tax Calculation can also be enabled and run with other global features.

## Related resources

[Get started with tax service](global-get-started-with-tax-calculation-service.md)

[Multiple VAT registration number](emea-multiple-vat-registration-numbers.md)

[Tax feature support for transfer order](Tax-feature-support-for-transfer-order.md)

[How to build extension in tax service](tax-service-add-data-fields-tax-integration-by-extension.md)
