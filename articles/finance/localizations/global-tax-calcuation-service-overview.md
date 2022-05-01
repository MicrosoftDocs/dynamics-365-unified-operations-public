---
# required metadata

title: Tax Calculation overview
description: This topic explains the overall scope and features of the Tax Calculation capability.
author: wangchen
ms.date: 03/02/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: TaxIntegrationTaxServiceParameters
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 

ms.search.region: Global
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.18

---

# Tax Calculation overview

[!include [banner](../includes/banner.md)]

Tax Calculation is a hyper-scalable multitenant service that enables the global tax engine to automate and simplify the tax determination and calculation process. The tax engine is fully configurable. The elements that can be configured include, but aren't limited to, the taxable data model, tax code, tax applicability matrix, and tax calculation formula. The tax engine runs on the Microsoft Azure core services platform, and offers modern technology and exponential scalability.

Tax Calculation integrates with Dynamics 365 Finance and Dynamics 365 Supply Chain Management. Eventually, it will also integrate with Dynamics 365 Project Operations, Dynamics 365 Commerce, and other first-party and third-party applications.

> [!IMPORTANT]
> When you enable Tax Calculation, some operations on related data might be performed in a data center other than the data center that maintains your service data. Review the [Terms and Conditions](../../fin-ops-core/fin-ops/get-started/public-preview-terms.md) before you enable Tax Calculation. Your privacy is important to us. To learn more, read our [Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=521839).

Tax Calculation is a microservice-based tax engine that offers exponential scalability and can help you perform the following tasks:

- Automatically determine the correct sales tax group, item sales tax group, and tax codes through an enhanced determination mechanism.
- Support multiple tax registration numbers in one legal entity, and automatically determine the correct tax registration number on taxable transactions.
- Support tax determination, calculation, posting, and settlement for transfer orders.
- Define configurable tax calculation formulas and conditions for your specific business requirements.
- Share the tax determination and calculation solution across legal entities to save maintenance effort and avoid errors.
- Support customer and vendor tax registration number determination.
- Support list code determination.
- Support tax calculation parameters at the tax jurisdiction level.

To use Tax Calculation, install the Tax Calculation add-in from your project in Microsoft Dynamics Lifecycle Services. Then complete the setup in [Regulatory Configuration Service](https://marketing.configure.global.dynamics.com/), and enable Tax Calculation in Finance and Supply Chain Management. For more information, see [Get started with tax service](global-get-started-with-tax-calculation-service.md).

## Availability

Tax Calculation is generally available in production environments to all customers as of version 10.0.21.

New features will continue to be delivered. Check the most up-to-date release plan often to learn about the coverage and scope of supported features.

Tax Calculation is deployed in the following Azure geographies. More Azure geographies will be added based on customer needs.

- Asia Pacific
- Australia
- Canada
- Europe
- Japan
- Switzerland
- United Kingdom
- United States

> [!NOTE]
> Tax Calculation doesn't support earlier version of Dynamics 365, such as Dynamics AX 2012, or on-premises deployments of Dynamics 365.

## Versions
We recommend that you import and set up your Tax Calculation configuration with the version that matches your Finance or Supply Chain Management version.

| Finance or Supply Chain Management version | Tax configuration version               |
| --------------- | --------------------------------------- |
| 10.0.18         | Tax Configuration - Europe 30.12.82     |
| 10.0.19         | Tax Calculation Configuration 36.38.193 |
| 10.0.20         | Tax Calculation Configuration 40.43.208 |
| 10.0.21         | Tax Calculation Configuration 40.48.215 |
| 10.0.22         | Tax Calculation Configuration 40.48.215 |
| 10.0.23         | Tax Calculation Configuration 40.50.221 |
| 10.0.24         | Tax Calculation Configuration 40.50.225 |
| 10.0.25         | Tax Calculation Configuration 40.50.225 |
| 10.0.26         | Tax Calculation Configuration 40.54.234 |
| 10.0.27         | Tax Calculation Configuration 40.54.234 |


## Data flow

Here is an outline of the data flow process for Tax Calculation. 

1. In RCS, view and import taxable document model configurations and model mapping configurations. If you must extend configurations for an advanced scenario, see [Add data fields in tax configurations](tax-service-add-data-fields-tax-configurations.md).
2. In RCS, create or maintain tax features. You can use tax features to maintain tax rates and tax applicability rules.
3. After the tax feature setup is completed, publish the tax configurations and tax features from RCS to the Global repository.
4. In Finance, select which tax feature setup version to use for a specific legal entity.
5. In Finance and Supply Chain Management, operate transactions as usual. When Tax Calculation is needed, the client will collect information from the transaction, such as the sales order or purchase order, and package the information as payload. A request will then be sent to calculate the tax.
6. The tax calculation request is received from the client and the calculation is completed. The tax result is then returned to the client.
7. The Dynamics 365 client receives the tax result and presents the tax calculation result on a sales tax page.

## Supported transactions

Tax Calculation can be enabled by transactions. 

The following transactions are supported in version 10.0.21: 

- Sales

    - Sales quotation
    - Sales order
    - Confirmation
    - Picking list
    - Packing slip
    - Sales invoice
    - Credit note
    - Return order
    - Header miscellaneous charge
    - Line miscellaneous charge

- Purchase

    - Purchase order
    - Confirmation
    - Receipts list
    - Product receipt
    - Purchase invoice
    - Header miscellaneous charge
    - Line miscellaneous charge
    - Credit note
    - Return order
    - Purchase requisition
    - Purchase requisition line miscellaneous charge
    - Request for quotation
    - Request for quotation header miscellaneous charge
    - Request for quotation line miscellaneous charge

- Inventory

    - Transfer order – ship
    - Transfer order – receive

The following transactions are supported in version 10.0.23: 

- Free text invoice

The following transactions are supported in version 10.0.26: 

- General journals
- Vendor invoice journal

## Supported countries/regions

Tax Calculation can be enabled by legal entity. 

The following countries/regions for a legal entity's primary address are supported in version 10.0.21:

- Austria
- Belgium
- Denmark
- Estonia
- Finland
- France
- Germany
- Hungary
- Iceland
- Italy
- Latvia
- Lithuania
- Netherlands
- Norway
- Poland
- Sweden
- Switzerland
- United Kingdom
- United States

The following countries/regions for a legal entity's primary address are supported in version 10.0.22:

- Australia
- Bahrain
- Canada
- Egypt
- Hong Kong SAR
- Kuwait
- New Zealand
- Oman
- Qatar
- Saudi Arabic
- South Africa
- United Arab Emirates

The following countries/regions for a legal entity's primary address are supported in version 10.0.23:

- Thailand
- Japan
- Malaysia
- Singapore

The following countries/regions for a legal entity's primary address are supported in version 10.0.24:

- Mexico

The following countries/regions for a legal entity's primary address are supported in version 10.0.26:

- China
- Czech Republic
- Spain

## Related resources

[Get started with tax service](./global-get-started-with-tax-calculation-service.md)

[Multiple VAT registration number](./emea-multiple-vat-registration-numbers.md)

[Tax feature support for transfer order](./tasks/tax-feature-support-for-transfer-order.md)

[How to build extension in tax service](./tax-service-add-data-fields-tax-integration-by-extension.md)
