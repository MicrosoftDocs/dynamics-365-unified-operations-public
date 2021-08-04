---
# required metadata

title: Tax Calculation Overview
description: This topic explains the overall scope and features of the Tax Calculation capability.
author: wangchen
ms.date: 06/03/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: TaxIntegrationTaxServiceParameters
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: "intro-internal"
ms.search.region: Global
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.18

---

# Tax Calculation Overview

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

Tax Calculation is a hyper-scalable multitenant service that enables the global tax engine to automate and simplify the tax determination and calculation process. The tax engine is fully configurable. The elements that can be configured include, but aren't limited to, the taxable data model, tax code, tax applicability matrix, and tax calculation formula. The tax engine runs on the Microsoft Azure core services platform, and offers modern technology and exponential scalability.

Tax Calculation integrates with Dynamics 365 Finance and Dynamics 365 Supply Chain Management. Eventually, it will also integrate with Dynamics 365 Project Operations, Dynamics 365 Commerce, and other first-party and third-party applications.

> [!IMPORTANT]
> When you enable the Tax Calculation service, some operations on related data might be performed in a data center other than the data center that maintains your service data. Review the [Terms and Conditions](../../fin-ops-core/fin-ops/get-started/public-preview-terms.md) before you enable the Tax Calculation service. Your privacy is important to us. To learn more, read our [Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=521839).

Tax Calculation is a microservice-based tax engine that offers exponential scalability. It can help you perform the following tasks:

- Automatically determine correct sales tax group, item sales tax group and tax codes with enhanced determination mechanism.
- Support multiple tax registration numbers in one legal entity and automatically determine the correct tax registration number on taxable transactions.
- Support tax determination, calculation, posting and settlement in transfer order
- Define configurable tax calculation formulas and conditions for your specific business requirements
- Share the tax determination and calculation solution across legal entities to save maintenance effort and avoid errors.
- Support customer/vendor tax registration number determination
- Support list code determination
- Support tax calculation parameters at tax jurisdiction level

To use the tax calculation service, install the tax calculation add-in from your project in Microsoft Dynamics Lifecycle Services, then complete the setup in [Regulatory Configuration Service](https://marketing.configure.global.dynamics.com/), and enable the tax calculation service in Dynamics 365 Finance and Supply Chain Management. For more information, see [Get started with tax service](./global-get-started-with-tax-calculation-service.md).



## Availability

Tax Calculation is generally available in production environments to all customers since 10.0.21.

New features will continue to be delivered, so be sure to check the most up-to-date release plan often to learn about the coverage and scope of supported features.

Tax Calculation is deployed in the following Azure geographies. It will also be deployed to more Azure geographies, based on customer needs:

- Asia Pacific
- Australia
- Canada
- Europe
- Japan
- United Kingdom
- United States

> [!NOTE]
> Tax Calculation doesn't support on-premises deployments of Dynamics 365. It also doesn't support earlier versions, such as Dynamics AX 2012.



## Data flow

- User views/imports taxable document model configurations, model mapping configurations in Regulatory Configuration Service. (If user need to extend configurations for advanced scenario, read more [here](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/tax-service-add-data-fields-tax-configurations?toc=/dynamics365/finance/toc.json)).
- User creates or maintains tax features in Regulatory Configuration Service. Tax feature is the place where user maintain tax rates, tax applicability rules, etc.
- After user completes tax feature setup, user publishes tax configurations, tax features from Regulatory Configuration Service to Global repo.
- In Dynamics 365 Finance, user selects which tax feature setup version to be used for certain legal entity.
- In Dynamics 365 Finance and Dynamics 365 Supply Chain Management, user operates transactions as usual, when Tax Calculation service is needed, client will collect information from transaction, e.g. from Sales order and Purchase order, and package the information as payload, and send request to Tax Calculation service to calculate tax.
- Tax Calculation service gets tax calculate request from client, doing calculations (get configuration/feature from Global repo for first time calculation), and returns tax result back to client (Dynamics 365 Finance for this case).
- Dynamics 365 client receives the tax result and presents the tax calculation result to sales tax form.

## Supported transactions

Tax Calculation can be enabled by transactions. 

Following transactions are supported in 10.0.21: 

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

More transactions will be supported in future releases:

- Free text invoice
- General journal
- Payment journal
- Invoice register
- Invoice approval
- Invoice pool
- Project invoice
- Project billing rule
- Expense
- Budget
- Quality order
- Service order
- Agreement

## Supported countries/regions

Tax Calculation can be enabled by legal entity. 

Following legal entity primary address countries/regions are supported in 10.0.21:

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

Following legal entity primary address countries/regions will be supported in future releases:
- Australia
- Bahrain
- Canada
- Czech Republic
- Egypt
- Hong Kong SAR
- Japan 
- Kuwait
- Malaysia
- Mexico
- New Zealand 
- Oman
- Qatar
- Saudi Arabic
- Singapore
- South Africa
- Spain
- Thailand
- United Arab Emirates

Following legal entity primary address counties/regions are not supported:
- Brazil
- China
- India
- Russia

## Related resources

[Get started with tax service](./global-get-started-with-tax-calculation-service.md)

[Multiple VAT registration number](./emea-multiple-vat-registration-numbers.md)

[Tax feature support for transfer order](./tasks/tax-feature-support-for-transfer-order.md)

[How to build extension in tax service](./tax-service-add-data-fields-tax-integration-by-extension.md)
