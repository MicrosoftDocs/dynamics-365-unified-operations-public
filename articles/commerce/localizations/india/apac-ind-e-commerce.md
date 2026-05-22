---
title: Goods and Services Tax (GST) integration for e-commerce sites for India
description: This article provides an overview of the Microsoft Dynamics 365 Commerce e-commerce functionality that's available for India. It also provides guidelines for setting up the functionality.
author: EvgenyPopovMBS
ms.date: 02/26/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: India
ms.author: anupamar
ms.search.validFrom: 2021-12-10
ms.custom: 
  - bap-template
---

# Goods and Services Tax (GST) integration for e-commerce sites for India

[!include [banner](../../../finance/includes/banner.md)]

This article provides an overview of the Microsoft Dynamics 365 Commerce e-commerce functionality that's available for India. It also provides guidelines for setting up the functionality.

For more information about the e-commerce capabilities that are available in Dynamics 365 Commerce, see [E-commerce site overview](../../online-store-overview.md). For more information about how Goods and Services Tax (GST) is supported in Commerce, see [Goods and Services Tax (GST) integration for cash registers for India](apac-ind-cash-registers.md).

## E-commerce capabilities for India

The Commerce e-commerce functionality for India provides the following capabilities:

- GST can be calculated for an e-commerce order based on the delivery and invoice information that you specify on the order.
- GST can also be calculated for shipping charges that are included in an e-commerce order at the line level.
- Customer registration numbers, such as the Goods and Services Tax Identification Number (GSTIN) or Permanent Account Number (PAN), can be specified in a customer profile on an e-commerce site.

### GST calculation for e-commerce orders

GST calculation for an e-commerce order is based on the customer's invoice address that you specify on the **Checkout** page of the e-commerce site. By default, the shipping address of the order is used as the invoice address. However, you can select the invoice address from the list of other addresses for the customer, or add a new address.

To enable GST calculation for e-commerce orders that is based on invoice information, add the **Invoice address for India** module to the checkout page. You must also enable the **(India) Calculate GST based on invoice address for e-commerce orders** feature in the **Feature management** workspace in Commerce headquarters. For more information, see the [Setting up e-commerce for India](#setting-up-e-commerce-for-india) section later in this article.

### GST calculation for shipping charges

GST can also be calculated for shipping charges that you add to an e-commerce order based on the delivery option that you select for the order. The calculation of GST for shipping charges is also based on the invoice address that you specify in the e-commerce order.

> [!NOTE]
> GST calculation currently supports only order line–level shipping charges. However, GST calculation for header-level shipping charges might be added in future updates.

### Customer registration numbers

Customers can enter their registration numbers and other information on the **My profile** page of the e-commerce site. The following registration information can be entered:

- PAN.
- GST registration number type. The registration number can be the GSTIN, Government Department Unique ID (GDI), or unique identification (UID) number.
- GST registration number.
- Business vertical.
- Value-added tax (VAT) registration number. This number is known as the Tax Identification Number (TIN).

Customers specify the PAN at the profile level. They specify the other registration information at the address level.

To enable customers to enter registration information in their profiles, add the **Tax registration numbers for India** module to the **My profile** page. For more information, see the [Setting up e-commerce for India](#setting-up-e-commerce-for-india) section.

## Setting up e-commerce for India

### Prerequisites

Before you set up e-commerce capabilities for India, configure a Commerce environment that includes Retail Cloud Scale Unit (RCSU), the Commerce online software development kit (SDK), and the Commerce module library. For information about how to install the Commerce SDK and module library, see [SDK and module library updates](../../e-commerce-extensibility/sdk-updates.md).

### Install modules

The following packages in the **dynamics365-commerce** feed include India-specific modules:

- **@msdyn365-commerce-marketplace/address-extensions** – This package includes the **Invoice address for India** module.
- **@msdyn365-commerce-marketplace/tax-registration-numbers** – This package includes the **Tax registration numbers for India** module.

However, these packages use a different namespace. To use these packages, add registry entries for the namespace.

1. Update the **.npmrc** file to include the following registry entry (if the entry isn't already included):

    `@msdyn365-commerce-marketplace:registry=https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/npm/registry/`

1. Update the **.yarnrc** file to include the following registry entry (if the entry isn't already included):

    `"@msdyn365-commerce-marketplace:registry" "https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/npm/registry/"`

To install the packages in your local environment, run the following commands from the command prompt. These commands automatically update the **package.json** file to include the dependencies.

```bash
yarn add @msdyn365-commerce-marketplace/address-extensions
yarn add @msdyn365-commerce-marketplace/tax-registration-numbers
```

In the **package.json** file, update the package version to a specific version.

> [!IMPORTANT]
> - The package version should match the module library version to ensure that all features work as expected.
> - The minimum version for the Commerce module library and SDK should be 10.0.23 (9.33).

### Pull updates and validate

For information about how to pull the latest SDK, module library, and other dependency updates, see [Pull updates](../../e-commerce-extensibility/sdk-updates.md#pull-updates).

After you pull the latest dependencies, run the **yarn start** command to start the Node server in your development environment and test the new modules. Browse the application locally (for example, `https://localhost:4000`).

### Build your site

Add the India-specific modules to the following pages of your e-commerce site:

- Add the **Invoice address for India** module to the checkout page.
- Add the **Tax registration numbers for India** module to the **My profile** page.

For more information about how to create e-commerce sites and work with e-commerce modules, see [Create an e-commerce site](../../create-ecommerce-site.md) and [Module library overview](../../starter-kit-overview.md).

### Configure GST for e-commerce

To work with GST in e-commerce, enable the India-specific functionality on the Commerce channel side:

- If you're using Commerce version 10.0.33 or earlier, configure extensions for channel components. For more information, see the [deployment guidelines](apac-ind-loc-deployment-guidelines.md).
- If you're using Commerce version 10.0.34 or later, enable the feature, **(India) Enable Tax engine for Commerce for India** in the **Feature management** workspace in Commerce headquarters. This feature ensures that the [Tax engine](../../../finance/general-ledger/tax-engine.md) is used to calculate India GST for in-store and e-commerce transactions.
- If you're using Commerce version 10.0.33 or earlier and are migrating to Commerce version 10.0.34 or later, follow the steps in [Migrate to Commerce version 10.0.34 or later](apac-ind-loc-deployment-guidelines.md#migrate-to-commerce-version-10034-or-later).

Also, enable the **(India) Calculate GST based on invoice address for e-commerce orders** feature in the **Feature management** workspace in Commerce headquarters.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]