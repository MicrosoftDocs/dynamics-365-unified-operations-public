---
title: Goods and Services Tax (GST) integration for e-commerce sites for India
description: This article gives an overview of the Microsoft Dynamics 365 Commerce e-commerce functionality that is available for India. It also provides guidelines for setting up the functionality.
author: EvgenyPopovMBS
ms.date: 04/13/2023
ms.topic: article
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: v-chgriffin
ms.search.region: India
ms.author: josaw
ms.search.validFrom: 2021-12-10
ms.dyn365.ops.version: 10.0.23
ms.search.industry: Retail
---

# Goods and Services Tax (GST) integration for e-commerce sites for India

[!include [banner](../includes/banner.md)]

This article gives an overview of the Microsoft Dynamics 365 Commerce e-commerce functionality that is available for India. It also provides guidelines for setting up the functionality. 

For more information about the e-commerce capabilities that are available in Dynamics 365 Commerce, see [E-commerce site overview](../online-store-overview.md). For more information about how Goods and Services Tax (GST) is supported in Commerce, see [Goods and Services Tax (GST) integration for cash registers for India](apac-ind-cash-registers.md).

## E-commerce capabilities for India

The Commerce e-commerce functionality for India provides the following capabilities:

- GST can be calculated for an e-commerce order based on the delivery and invoice information that is specified on the order.
- GST can also be calculated for shipping charges that are included in an e-commerce order at the line level.
- Customer registration numbers, such as the Goods and Services Tax Identification Number (GSTIN) or Permanent Account Number (PAN), can be specified in a customer profile on an e-commerce site.

### GST calculation for e-commerce orders

GST calculation for an e-commerce order is based on the customer's invoice address that can be specified on the **Checkout** page of the e-commerce site. By default, the shipping address of the order is used as the invoice address. However, the invoice address can also be selected in the list of other addresses for the customer, or a new address can be added.

To enable GST calculation for e-commerce orders that is based on invoice information, you must add the **Invoice address for India** module to the checkout page. You must also enable the **(India) Calculate GST based on invoice address for e-commerce orders** feature in the **Feature management** workspace in Commerce headquarters. For more information, see the [Setting up e-commerce for India](#setting-up-e-commerce-for-india) section later in this article.

### GST calculation for shipping charges

GST can also be calculated for shipping charges that can be added to an e-commerce order based on the delivery option that is selected for the order. The calculation of GST for shipping charges is also based on the invoice address that is specified in the e-commerce order.

> [!NOTE]
> GST calculation is currently supported only for order line–level shipping charges. However, GST calculation for header-level shipping charges might be added in future updates.

### Customer registration numbers

A customer's registration numbers and other information can be specified on the **My profile** page of the e-commerce site. The following registration information can be entered:

- PAN.
- GST registration number type. The registration number can be the GSTIN, Government Department Unique ID (GDI), or unique identification (UID) number.
- GST registration number.
- Business vertical.
- Value-added tax (VAT) registration number. This number is known as the Tax Identification Number (TIN).

The PAN can be specified at the customer profile level. The other registration information can be specified at the customer address level.

To enable customer registration information to be entered in a customer profile, you must add the **Tax registration numbers for India** module to the **My profile** page. For more information, see the [Setting up e-commerce for India](#setting-up-e-commerce-for-india) section that follows.

## Setting up e-commerce for India

### Prerequisites

Before you set up e-commerce capabilities for India, you must configure a Commerce environment that includes Retail Cloud Scale Unit (RCSU), the Commerce online software development kit (SDK), and the Commerce module library. For information about how to install the Commerce SDK and module library, see [SDK and module library updates](../e-commerce-extensibility/sdk-updates.md).

### Install modules

The following packages that are available in the **dynamics365-commerce** feed include India-specific modules:

- **@msdyn365-commerce-marketplace/address-extensions** – This package includes the **Invoice address for India** module.
- **@msdyn365-commerce-marketplace/tax-registration-numbers** – This package includes the **Tax registration numbers for India** module.

However, although the packages are part of that feed, they are under a different namespace. Therefore, you must follow these steps to add registry entries for the namespace.

1. Update the **.npmrc** file so that it includes the following registry entry (if the entry isn't already included):

    `@msdyn365-commerce-marketplace:registry=https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/npm/registry/`

1. Update the **.yarnrc** file so that it includes the following registry entry (if the entry isn't already included):

    `"@msdyn365-commerce-marketplace:registry" "https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/npm/registry/"`
	
To install the packages in your local environment, run the following commands from the command prompt. These commands automatically update the **package.json** file so that it includes the dependencies.

```bash
yarn add @msdyn365-commerce-marketplace/address-extensions
yarn add @msdyn365-commerce-marketplace/tax-registration-numbers
```

In the **package.json** file, you should update the package version to a specific version.

> [!IMPORTANT]
> - The package version should match the module library version to ensure that all features work as expected. 
> - The minimum version for the Commerce module library and SDK should be 10.0.23 (9.33). 

### Pull updates and validate

For information about how to pull the latest SDK, module library, and other dependency updates, see [Pull updates](../e-commerce-extensibility/sdk-updates.md#pull-updates).

After the latest dependencies are pulled down, you can run the **yarn start** command to start the Node server in your development environment and test the new modules. Browse the application locally (for example, `https://localhost:4000`).

### Build your site

You must add the India-specific modules to the following pages of your e-commerce site:

- Add the **Invoice address for India** module to the checkout page.
- Add the **Tax registration numbers for India** module to the **My profile** page.

For more information about how to create e-commerce sites and work with e-commerce modules, see [Create an e-commerce site](../create-ecommerce-site.md) and [Module library overview](../starter-kit-overview.md).

### Configure GST for e-commerce

To work with GST in e-commerce, you must enable the India-specific functionality on the Commerce channel side:

- If you are using Commerce version 10.0.33 or earlier, you must configure extensions for channel components. For more information, see the [deployment guidelines](./apac-ind-loc-deployment-guidelines.md).
- If you are using Commerce version 10.0.34 or later, you must enable the feature, **(India) Enable Tax engine for Commerce for India** in the **Feature management** workspace in Commerce headquarters. This feature ensures that the [Tax engine](../../finance/general-ledger/tax-engine.md) is used to calculate India GST for in-store and e-commerce transactions.
- If you are using Commerce version 10.0.33 or earlier and are migrating to Commerce version 10.0.34 or later, follow the steps in [Migrate to Commerce version 10.0.34 or later](./apac-ind-loc-deployment-guidelines.md#migrate-to-commerce-version-10034-or-later).

You must also enable the **(India) Calculate GST based on invoice address for e-commerce orders** feature in the **Feature management** workspace in Commerce headquarters.
