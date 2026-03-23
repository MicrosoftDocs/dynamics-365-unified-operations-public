---
title: Reduce JavaScript by excluding unused modules
description: Learn how you can help improve performance by reducing the amount of JavaScript used in your Microsoft Dynamics 365 Commerce implementation.
author: mssle
ms.date: 01/30/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2021-09-20
ms.custom: 
  - bap-template
---

# Reduce JavaScript by excluding unused modules

[!include[banner](../includes/banner.md)]

This article describes how you can help improve performance by reducing the amount of JavaScript used in your Microsoft Dynamics 365 Commerce implementation.

Dynamics 365 Commerce includes a large set of modules referred to as the Commerce [module library](../starter-kit-overview.md). If you don't use some modules on your e-commerce site, exclude them to help reduce the JavaScript chunk size. The live e-commerce site doesn't render excluded modules. Commerce site builder doesn't make them available when you create pages.

## Applies to

This article applies to the following configurations:

- **Version:** Commerce 10.0.16 or later
- **Component:** Business to consumer (B2C) or business to business (B2B)
- **Feature area:** Commerce website performance

## Prerequisites

Install the Dynamics 365 Commerce online software development kit (SDK). For more information, see [Install the online SDK](../dev-itpro/ecommerce-platform-sdk.md).

## Steps to reduce JavaScript

To exclude unused modules, add the module names to the **excludeModules** property in the SDK's **platform.settings.json** file (/src/settings/platform.settings.json).

1. Open a Windows Command Prompt window.
1. Go to the **/src/settings** directory in your SDK installation location.
1. Open the **platform.settings.json** file in a text editor.
1. Insert the following code in JavaScript Object Notation (JSON) format. Replace **\<EXCLUDED\_MODULE\_NAME...\>** with the name of the module to exclude. Enclose each module name in double quotation marks. If you exclude multiple modules, separate the module names with commas.

    ```json
    {
        "excludedModules": ["<EXCLUDED_MODULE_NAME1>","<EXCLUDED_MODULE_NAME2>"]
    }
    ```

## Validate

Use one or both of the following methods to validate that a module was successfully excluded.

### Method 1

- **Description or purpose:** Verify that the module is excluded.
- **Steps to run:** Compare the chunk size that appears after a build.
- **Passing result:** The chunk size is smaller after a new build.

### Method 2

- **Description or purpose:** Verify that the module is excluded.
- **Steps to run:** Test the module in a development environment by following these steps:

    1. Run the Node server by using the **yarn start** command.
    1. Visit the following URL: `http://localhost:4000/modules?type=<YOUR-MODULE-NAME>`.

- **Passing result:** The excluded module doesn't render on the webpage.

## Additional resources

[Install the online SDK](../dev-itpro/ecommerce-platform-sdk.md)

[Set up a development environment](../e-commerce-extensibility/setup-dev-environment.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
