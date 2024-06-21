---
title: Tax Calculation overview
description: Learn about the overall scope and features of the Tax Calculation capability, including outlines on versions, data flows, and supported transactions.
author: EricWangChen
ms.author: wangchen
ms.topic: overview
ms.custom: 
  - bap-template
ms.date: 06/21/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2021-04-01
ms.search.form: TaxIntegrationTaxServiceParameters
ms.dyn365.ops.version: 10.0.18
---

# Tax Calculation overview

[!include [banner](../../includes/banner.md)]

Tax Calculation helps automate and simplify the tax determination and calculation process. The tax engine is fully configurable. The elements that can be configured include, but aren't limited to, the taxable data model, tax code, tax applicability matrix, and tax calculation formula. The tax engine runs on the Microsoft Azure core services platform, and offers modern technology and exponential scalability.

> [!IMPORTANT]
> When you enable Tax Calculation, some operations on related data might be performed in a data center other than the data center that maintains your service data. Review the [Terms and Conditions](https://go.microsoft.com/fwlink/?linkid=2156043) before you enable Tax Calculation. Your privacy is important to us. To learn more, read our [Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=521839).

Tax Calculation is a highly scalable tax engine that's designed to support you in performing the following tasks:

- Automatically determine the correct sales tax group, item sales tax group, and tax codes through an enhanced determination mechanism.
- Support multiple tax registration numbers in one legal entity, and automatically determine the correct tax registration number on taxable transactions.
- Support tax determination, calculation, posting, and settlement for transfer orders.
- Define configurable tax calculation formulas and conditions for your specific business requirements.
- Share the tax determination and calculation solution across legal entities to save maintenance effort and avoid errors.
- Support customer and vendor tax registration number determination.
- Support list code determination.
- Support tax calculation parameters at the tax jurisdiction level.

To use Tax Calculation, install the Tax Calculation add-in from your project in Microsoft Dynamics Lifecycle Services. Then complete the setup in [Regulatory Configuration Service](https://marketing.configure.global.dynamics.com/) (RCS), and enable Tax Calculation in Finance and Supply Chain Management. For more information, see [Get started with tax service](global-get-started-with-tax-calculation-service.md).

> [!NOTE]
> For new environments that have version 10.0.39 and later, installation of the TCS add-in in Lifecycle Services isn't required.

> [!IMPORTANT]
> The functionality of RCS is merged to the **Globalization Studio** workspace in Finance in version 10.0.39. For more information, see [Regulatory Configuration Service merge to the Globalization Studio workspace](workspace/merge-rcs-to-gsw.md).
>
> If you're using version 10.0.39 or later, use the **Globalization Studio** workspace in Finance instead of RCS.

## Availability

Tax Calculation is generally available in production environments to all customers as of version 10.0.21.

New features will continue to be delivered. Check the most up-to-date release plan often to learn about the coverage and scope of supported features.

Tax Calculation is deployed in the following Azure geographies. More Azure geographies will be added based on customer needs.

- Asia Pacific
- Australia
- Brazil
- Canada
- Europe
- France
- Germany
- India
- Japan
- Korea
- Norway
- South Africa
- Switzerland
- United Arab Emirates
- United Kingdom
- United States

> [!NOTE]
> Tax Calculation doesn't support earlier versions of Dynamics 365, such as Dynamics AX 2012, or on-premises deployments of Dynamics 365.

## Versions
We recommend that you import and set up your Tax Calculation configuration with the version that matches your Finance or Supply Chain Management version.

| Finance or Supply Chain Management version | Tax configuration version |
| --------------- | --------------------------------------- |
| 10.0.40         | Tax Calculation Configuration 43.68.254 |
| 10.0.39         | Tax Calculation Configuration 40.65.249 |
| 10.0.38         | Tax Calculation Configuration 40.61.246 |
| 10.0.33         | Tax Calculation Configuration 40.60.244 |
| 10.0.32         | Tax Calculation Configuration 40.60.244 |
| 10.0.31         | Tax Calculation Configuration 40.56.240 |
| 10.0.30         | Tax Calculation Configuration 40.55.239 |

## Data flow

Here is an outline of the data flow process for Tax Calculation. 

> [!IMPORTANT]
> The functionality of RCS is merged to the **Globalization Studio** workspace in Finance in version 10.0.39. For more information, see [Regulatory Configuration Service merge to the Globalization Studio workspace](workspace/merge-rcs-to-gsw.md).
>
> If you're using version 10.0.39 or later, use the **Globalization Studio** workspace in Finance instead of RCS.

1. In RCS, view and import taxable document model configurations and model mapping configurations. If you must extend configurations for an advanced scenario, see [Add data fields in tax configurations](tax-service-add-data-fields-tax-configurations.md).
2. In RCS, create or maintain tax features. You can use tax features to maintain tax rates and tax applicability rules.
3. After the tax feature setup is completed, publish the tax configurations and tax features from RCS to the Global repository.
4. In Finance, select which tax feature setup version to use for a specific legal entity.
5. In Finance and Supply Chain Management, operate transactions as usual. When Tax Calculation is needed, the client will collect information from the transaction, such as the sales order or purchase order, and package the information as payload. A request will then be sent to calculate the tax.
6. The tax calculation request is received from the client and the calculation is completed. The tax result is then returned to the client.
7. The Dynamics 365 client receives the tax result and presents the tax calculation result on a sales tax page.

## Supported transactions

Tax Calculation can be enabled by transactions. 

The following table lists the transactions supported in the corresponding version.

| Version | Transactions |
|---------|--------------|
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
| 10.0.24 | Mexico |
| 10.0.23 | <ul><li>Thailand</li><li>>Japan</li><li>Malaysia</li><li>Singapore</li></ul> |
| 10.0.22 | <ul><li>Australia</li><li>Bahrain</li><li>Canada</li><li>Egypt</li><li>Hong Kong SAR</li><li>Kuwait</li><li>New Zealand</li><li>Oman</li><li>Qatar</li><li>Saudi Arabic</li><li>South Africa</li><li>United Arab Emirates</li></ul> |
| 10.0.21 | <ul><li>Austria</li><li>Belgium</li><li>Denmark</li><li>Estonia</li><li>Finland</li><li>France</li><li>Germany</li><li>Hungary</li><li>Iceland</li><li>Ireland</li><li>Italy</li><li>Latvia</li><li>Lithuania</li><li>Netherlands</li><li>Norway</li><li>Poland</li><li>Sweden</li><li>Switzerland</li><li>United Kingdom</li><li>United States</li></ul> |

For any country/region not localized by Microsoft, Tax Calculation can also be enabled and run with other global features.

## Related resources

[Get started with tax service](global-get-started-with-tax-calculation-service.md)

[Multiple VAT registration number](emea-multiple-vat-registration-numbers.md)

[Tax feature support for transfer order](Tax-feature-support-for-transfer-order.md)

[How to build extension in tax service](tax-service-add-data-fields-tax-integration-by-extension.md)
