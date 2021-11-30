---
# required metadata
title: Goods and Services Tax (GST) integration for e-commerce sites for India
description: This topic provides an overview of the e-commerce functionality that is available for India. It also provides guidelines for setting up the functionality.
author: EvgenyPopovMBS
ms.date: 11/30/2021
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

This topic provides an overview of the e-commerce functionality that is available for India. It also provides guidelines for setting up the functionality. For more information about the e-commerce capabilities that are available in Dynamics 365 Commerce, see [E-commerce site overview](../online-store-overview).

## India-specific e-commerce capabilities

The e-commerce functionality for India provides the following capabilities:

- Goods and Services Tax (GST) can be calculated for an e-commerce order based on the delivery and invoice information specified on the order.
- GST can also be calculated for shipping charges included in an e-commerce order on the line level.
- Customer registration numbers (such as GSTIN or PAN) can be specified in a customer profile on an e-commerce site.

### GST calculation for e-commerce orders

### GST calculation for shipping charges

> [!NOTE]
> Only line-level shipping charges are currently supported. GST calculation for header level shipping charges may be added in future updates.

### Customer registration numbers

## Install modules for India

[!include [banner](../includes/banner.md)]

This topic describes how to install the modules for India in Microsoft Dynamics 365 Commerce. 

> [!IMPORTANT]
> The modules are available as of the Dynamics 365 Commerce version 10.0.23 release.

### Prerequisites

Before you install the modules for India, you must have the following items.
- Dynamics 365 Commerce environment (Commerce version 10.0.23 or later) that includes Retail Cloud Scale Unit (RCSU), the Commerce online software development kit (SDK), and the Commerce module library. For information about how to install the Commerce SDK and module library, see [SDK and module library updates](../e-commerce-extensibility/sdk-updates.md). 
- [Deployment guidelines for cash registers for India](apac-ind-loc-deployment-guidelines.md).

### Installation steps

#### Install the modules for India in your application

The packages for India are available in the **dynamics365-commerce** feed, as **@msdyn365-commerce-marketplace/address-extensions** and **@msdyn365-commerce-marketplace/tax-registration-numbers**. However, although the packages are part of that feed, it's under a different namespace. Therefore, you must follow these steps to add registry entries for the namespace.

1. Update the **.npmrc** file so that it includes the following registry entry (if the entry isn't already included):

    `@msdyn365-commerce-marketplace:registry=https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/npm/registry/`

1. Update the **.yarnrc** file so that it includes the following registry entry (if the entry isn't already included):

    `"@msdyn365-commerce-marketplace:registry" "https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/npm/registry/"`	
	
To install the package in your local environment, run the following command from the command prompt. This command automatically updates the package.json file so that it includes the dependency.

- `yarn add @msdyn365-commerce-marketplace/address-extensions`
- `yarn add @msdyn365-commerce-marketplace/tax-registration-numbers`

In the **package.json** file, you should update the packages version to a specific version.

> [!IMPORTANT]
> - The packages version should match the module library version to ensure that all features work as expected. 
> - The minimum version for the Commerce module library and SDK should be 10.0.23 (9.33). 

#### Pull updates and validate

For information about how to pull the latest SDK, module library, and other dependency updates, see the "Pull updates" section of [SDK and module library updates](../e-commerce-extensibility/sdk-updates.md#pull-updates).

After the latest dependencies are pulled down, you can run the **yarn start** command to start the Node server in your development environment and test the new modules. Browse the application locally (for example, `https://localhost:4000`).

### Additional resources

[Module library overview](../starter-kit-overview.md)

[SDK and module library updates](../e-commerce-extensibility/sdk-updates.md)
