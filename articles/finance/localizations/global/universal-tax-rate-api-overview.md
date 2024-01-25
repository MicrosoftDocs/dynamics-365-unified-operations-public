---
title: Connect to an external tax solution provider via Universal Tax Rate API
description: This article explains the overall scope of Universal Tax Rate API feature for the Tax Calculation.
author: Kai-Cloud
ms.date: 01/22/2024
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.prod: 
ms.technology: 
audience: Application user
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: kailiang
ms.search.validFrom: 2024-02-01
ms.dyn365.ops.version: 10.0.39
ms.search.form: 
---

# Connect to an external tax solution provider via Universal Tax Rate API

The connection to an external tax solution provider simplifies and reduces the effort of maintaining the tax rates and tax applicability rules for Tax calculation. This is especially critical when you implement Tax calculation for countries/regions where a significant number of tax jurisdictions need to be covered.

The Universal Tax Rate API is a set of standard application programming interfaces defined by Microsoft in Tax calculation based on the taxable document data model. It's an extended feature of Tax calculation which enables external tax services to be connected under the same framework.

With this extension, external tax solution providers can now provide tax rate determination, tax calculations, and extended tax functionalities via standardized APIs. It introduces the following benefits:

- **Seamless integration with Dynamics 365 applications**: The external tax solution is seamlessly integrated into Dynamics 365 applications, ensuring a smooth and unified experience across Dynamics applications.
- **Improved scalability**: By connecting to an external tax solution provider, you can leverage their infrastructure and expertise to handle large-scale tax calculations efficiently.
- **Reduced maintenance overhead**: External tax solution providers are responsible for maintaining up-to-date tax rates and tax applicability rules, which saves you time and effort.
- **Enhanced accuracy**: External tax services often have access to comprehensive tax databases and advanced algorithms, resulting in more accurate tax calculations.
- **Flexibility and customization**: The standardized APIs allow you to integrate with various external tax solution providers, giving you the flexibility to choose the one that best fits your business needs.
- **Compliance with local regulations**: External tax solution providers are well-versed in local tax laws and regulations, ensuring that your tax calculations are compliant with the specific requirements of each jurisdiction.

> [!NOTE]
> The Universal Tax Rate API shares the same integration of Tax calculation. Different tax solution providers may have different supported regions, scopes, scenarios, and extended functionalities. For more information, please contact the [tax solution providers](#available-tax-solution-providers).

The following functionalities are available via Universal Tax Rate API supported by the tax solution providers.

- **Encrypted connection**: Universal Tax Rate API supports an encrypted connection via Azure Key Vault to ensure the security and privacy of data transmitted between the API and external tax solution providers.
- **Address validation**: This functionality allows you to validate addresses maintained in global address book. It helps ensure accurate tax calculations by confirming that the address is valid and complete.
- **Sales tax calculation**: External tax solution providers can use Universal Tax Rate API to calculate sales tax based on various factors such as location, product type, and etc.
- **Posted tax transaction**: This functionality allows the tax transaction postings in the external tax solution system of the tax solution providers. Tax reporting is to be generated after the posting in the external tax solution system.
- **Accrue use tax**: The API enables external tax solution providers to accrue use tax, which is a type of tax imposed on the use, storage, or consumption of taxable items or services that were not taxed at the time of purchase in United States.

## Availability

Universal Tax Rate API is available on Dynamics Finance or Supply Chain Management version 10.0.38 and later.

## Versions

We recommend that you import and set up your Tax calculation configuration with the version that matches your Finance or Supply Chain Management version.

| Finance or Supply Chain Management version | Tax configuration version               |
| --------------- | --------------------------------------- |
| 10.0.39         | Tax Calculation Data Model for ISV Integration 40.61.4 |

## Steps to enable a tax solution provider

To enable a tax solution provider, follow these steps.

 1. Enable the following features in **Feature management**.
    - Tax calculation service
    - Enable external tax solution providers for Tax calculation service
    - Globalization features
    - Enable Globalization feature setup for Tax calculation service
    - Electronic reporting globalization feature Json import/export

 2. Engage and select one [tax solution provider](#available-tax-solution-providers), install the ISV application when required by the tax solution provider for the complete and extended functionality.
 3. [Setup ClientId and ClientSecret](./universal-tax-rate-api-how-to-setup-clientId-and-clientsecret.md) for the application access credential provided by your tax solution provider.
 4. Follow the implementation guidance provided by your tax solution provider to import the ISV related tax data model and tax features via **Globalization Studio**.
     - **Tax configurations > Exchange > Load from XML**
        - Tax Calculation Data Model for ISV integration.xml (version 40.61.4)
        - ISV tax configuration.xml (version 40.61.4.x)
     - **Tax calculation > Import from JSON**
        - ISV tax solution.json (version x)
      >[!NOTE]
      >Above xml and Json files are distributed by the ISV for load and import to the Tax Calculation setup.

 5. Follow the implementation guidance provided by your tax solution provider to create and configure the customer ISV tax feature for your credentials, parameter values, mapping rules, etc. via **Globalization Studio > Tax calculation > Add**.

 6. Enable the **Enable tax solution provider** option in the Tax calculation parameters under Tax module. [Configure the tax solution provider](#available-tax-solution-providers) in the Tax calculation parameters.

 7. You can now operate transactions as usual. When Tax Calculation is needed, the client will collect information from the transaction, such as the sales order or purchase order, and package the information as payload. A request will then be sent to your tax solution provider to calculate the tax.
 8. The calculation result is returned from your tax solution provider to your Finance system and presented on the sales tax transaction page.
 9. When you post a sales tax related voucher in Finance, a Posted tax transaction request will be sent to your tax solution provider to record the necessary tax information in their tax solution system for tax reporting.

## Supported countries/regions

Universal Tax Rate API can be run for supported localization features. The following table lists the countries/regions for a legal entity's primary address.

| Version | Country/region |
|---------|----------------|
| 10.0.39 | United States |

For supported countries/regions details, contact your tax solution providers.

## Available tax solution providers

- [Vertex](https://go.microsoft.com/fwlink/?linkid=2258342)
- [Avalara](https://go.microsoft.com/fwlink/?linkid=2258284)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
