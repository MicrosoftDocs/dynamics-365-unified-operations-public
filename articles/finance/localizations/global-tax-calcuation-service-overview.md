---
# required metadata

title: Tax Calculation (Preview)
description: This topic explains the overall scope and features of the Tax Calculation capability.
author: wangchen
ms.date: 04/12/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.18

---

# Tax Calculation (Preview)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

Tax Calculation is a hyper-scalable multitenant service that enables the global tax engine to automate and simplify the tax determination and calculation process. The tax engine is fully configurable. The elements that can be configured include, but aren't limited to, the taxable data model, tax code, tax applicability matrix, and tax calculation formula. The tax engine runs on the Microsoft Azure core services platform, and offers modern technology and exponential scalability.

Tax Calculation integrates with Dynamics 365 Finance and Dynamics 365 Supply Chain Management. Eventually, it will also integrate with Dynamics 365 Project Operations, Dynamics 365 Commerce, and other first-party and third-party applications.

> [!IMPORTANT]
> When you enable the Tax Calculation service, some related data might be performed in a data center other than the data center that maintains your service data. Review the [Terms and Conditions](../../fin-ops-core/fin-ops/get-started/public-preview-terms.md) before you enable the Tax Calculation service. Your privacy is important to us. To learn more, read our [Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=521839).

Tax Calculation is a microservice-based tax engine that offers exponential scalability. It can help you perform the following tasks:

- Configure Tax Calculation through Regulatory Configuration Service (RCS). RCS is an enhanced version of the Electronic reporting (ER) designer and is available as a standalone service.
- Configure the tax matrix to automatically determine tax codes and rates.
- Configure the tax matrix to automatically determine the tax registration number.
- Configure the tax calculation designer to define formulas and conditions.
- Share the tax determination and calculation solution across legal entities.

To use the tax calculation service, install the tax calculation service add-in from your project in Microsoft Dynamics Lifecycle Services (LCS). Then complete the setup in RCS, and enable the tax calculation service in Finance and Supply Chain Management. For more information, see [Get started with tax service](./global-get-started-with-tax-calculation-service.md).

## Availability

Tax Calculation is available only in sandbox environments and to selected customers, through a public preview program. Eventually, it will become generally available to all customers and in production environments.

New features will continue to be delivered, so be sure to check the most up-to-date documentation often to learn about the coverage and scope of supported features.

Tax Calculation is deployed in the following Azure geographies. It will also be deployed to more Azure geographies, based on customer needs:

- United States
- Europe

> [!NOTE]
> Tax Calculation doesn't support on-premises deployments of Dynamics 365. It also doesn't support earlier versions, such as Dynamics AX 2012.

## Feature highlights

- A configurable tax matrix to automatically determine and calculate tax
- Support for multiple tax registration numbers
- Transfer order support for tax determination and calculation
- Transfer order support for determination of multiple tax registration numbers

## Supported transactions

Tax Calculation can be enabled by legal entity and transaction. The following transactions are supported:

- Sales process

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

- Purchase process

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

- Inventory process

    - Transfer order – ship
    - Transfer order – receive

## Related resources

[Get started with tax service](./global-get-started-with-tax-calculation-service.md)

[Multiple VAT registration number](./emea-multiple-vat-registration-numbers.md)

[Tax feature support for transfer order](./tasks/tax-feature-support-for-transfer-order.md)

[How to build extension in tax service](./tax-service-add-data-fields-tax-integration-by-extension.md)
