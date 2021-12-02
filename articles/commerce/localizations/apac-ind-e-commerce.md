---
# required metadata
title: Goods and Services Tax (GST) integration for e-commerce sites for India
description: This topic provides an overview of the e-commerce functionality that is available for India. It also provides guidelines for setting up the functionality.
author: EvgenyPopovMBS
ms.date: 12/01/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

# ms.search.form:
audience: IT Pro
# ms.devlang:
ms.reviewer: josaw
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: India
ms.search.industry: Retail
ms.author: epopov
ms.search.validFrom: 2021-12-10
ms.dyn365.ops.version: 10.0.23
---
# Goods and Services Tax (GST) integration for e-commerce sites for India

This topic provides an overview of the e-commerce functionality that is available for India. It also provides guidelines for setting up the functionality. For more information about the e-commerce capabilities that are available in Dynamics 365 Commerce, see [E-commerce site overview](../online-store-overview.md). For more information about how GST is supported in Commerce, see [Goods and Services Tax (GST) integration for cash registers for India](apac-ind-cash-registers.md).

## E-commerce capabilities for India

The e-commerce functionality for India provides the following capabilities:

- Goods and Services Tax (GST) can be calculated for an e-commerce order based on the delivery and invoice information specified on the order.
- GST can also be calculated for shipping charges included in an e-commerce order on the line level.
- Customer registration numbers (such as GSTIN or PAN) can be specified in a customer profile on an e-commerce site.

### GST calculation for e-commerce orders

GST calculation for an e-commerce order is based on the customer's invoice address that can be specified on the **Checkout** page of the e-commerce site. The invoice address is defaulted from the shipping address of the order. It is possible to pick the invoice address from the list of other addresses of the customer, or to add a new address.

To enable GST calculation for e-commerce orders based on invoice information, you must add the **Invoice address for India** module to the checkout page and enable the **(India) Calculate GST based on invoice address for e-commerce orders** feature in the **Feature management** workspace in Commerce Headquarters. For more details, see the [Setting up e-commerce for India](#setting-up-e-commerce-for-india) section.

### GST calculation for shipping charges

GST can also be calculated for shipping charges that can be added to an e-commerce order based on the delivery option that is selected for the order. The calculation of GST for shipping charges is also based on the invoice address that is specified in the e-commerce order.

> [!NOTE]
> GST calculation is currently supported only for order line-level shipping charges. GST calculation for header level shipping charges may be added in future updates.

### Customer registration numbers

It is possible to specify customer's registration numbers and other information on the **My profile** page of the e-commerce site. The following registration information can be entered:

- Permanent Account Number (PAN).
- GST registration number type. It can be Goods and Services Taxpayer Identification Number (GSTIN), Government department unique ID (GDI), or Unique Identification Number (UID).
- GST registration number.
- Business vertical.
- Value-added tax registration number (Tax Identification Number \[TIN\]).

The PAN number can be specified on the customer profile level, while other registration information can be specified on the customer address level.

To enable the possibility to enter customer registration information in customer profile, you must add the **Tax registration numbers for India** module to the **My profile** page. For more details, see the [Setting up e-commerce for India](#setting-up-e-commerce-for-india) section.

## Setting up e-commerce for India

### Prerequisites

Before you set up e-commerce capabilities for India, you must configure a Commerce environment that includes Retail Cloud Scale Unit (RCSU), the Commerce online software development kit (SDK), and the Commerce module library. For information about how to install the Commerce SDK and module library, see [SDK and module library updates](../e-commerce-extensibility/sdk-updates.md).

### Install modules

The following packages that are available in the **dynamics365-commerce** feed include India-specific modules:

- **@msdyn365-commerce-marketplace/address-extensions**. The package includes the **Invoice address for India** module.

- **@msdyn365-commerce-marketplace/tax-registration-numbers**. The package includes the **Tax registration numbers for India** module.

However, although the packages are part of that feed, they are under a different namespace. Therefore, you must follow these steps to add registry entries for the namespace.

1. Update the **.npmrc** file so that it includes the following registry entry (if the entry isn't already included):

    ```
    @msdyn365-commerce-marketplace:registry=https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/npm/registry/
    ```

1. Update the **.yarnrc** file so that it includes the following registry entry (if the entry isn't already included):

    ```
    "@msdyn365-commerce-marketplace:registry" "https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/npm/registry/"
    ```
	
To install the packages in your local environment, run the following commands from the command prompt. These commands automatically update the **package.json** file so that it includes the dependencies.

```
yarn add @msdyn365-commerce-marketplace/address-extensions
yarn add @msdyn365-commerce-marketplace/tax-registration-numbers
```

In the **package.json** file, you should update the package version to a specific version.

> [!IMPORTANT]
> - The packages version should match the module library version to ensure that all features work as expected. 
> - The minimum version for the Commerce module library and SDK should be 10.0.23 (9.33). 

### Pull updates and validate

For information about how to pull the latest SDK, module library, and other dependency updates, see the "Pull updates" section of [SDK and module library updates](../e-commerce-extensibility/sdk-updates.md#pull-updates).

After the latest dependencies are pulled down, you can run the **yarn start** command to start the Node server in your development environment and test the new modules. Browse the application locally (for example, `https://localhost:4000`).

### Build your site

You must add the India-specific modules to the following pages of your e-commerce site:

- The **Invoice address for India** module must be added to the checkout page.
- The **Tax registration numbers for India** module must be added to the **My profile** page.

For more information on how to create e-commerce sites and work with e-commerce modules, see [Create an e-commerce site](../create-ecommerce-site.md) and [Module library overview](../starter-kit-overview.md).

### Configure GST for e-commerce

See [Deployment guidelines for cash registers for India](apac-ind-loc-deployment-guidelines.md) for detailed information on how to configure GST for Commerce.

You must also enable the following feature in the **Feature management** workspace in Commerce Headquarters:

- (India) Calculate GST based on invoice address for e-commerce orders.
