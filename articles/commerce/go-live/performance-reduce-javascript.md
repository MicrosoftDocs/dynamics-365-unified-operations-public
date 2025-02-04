---
# required metadata

title: Reduce JavaScript by excluding unused modules
description: This article describes how you can help improve performance by reducing the amount of JavaScript that is used in your Microsoft Dynamics 365 Commerce implementation.
author: mssle
ms.date: 07/26/2024
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2021-09-20
ms.custom: 
  - bap-template
---

# Reduce JavaScript by excluding unused modules

[!include[banner](../includes/banner.md)]

This article describes how you can help improve performance by reducing the amount of JavaScript that is used in your Microsoft Dynamics 365 Commerce implementation.

Dynamics 365 Commerce includes a large set of modules that is referred to as the Commerce [module library](../starter-kit-overview.md). If any modules won't be used on your e-commerce site, you can exclude them to help reduce the JavaScript chunk size. Excluded modules won't be rendered on the live e-commerce site. They also won't be available in Commerce site builder when you create pages.

## Applies to

This article applies to the following configurations:

- **Version:** Commerce 10.0.16 or later
- **Component:** Business to consumer (B2C) or business to business (B2B)
- **Feature area:** Commerce website performance

## Prerequisites

Install the Dynamics 365 Commerce online software development kit (SDK). For more information, see [Install the online SDK](../dev-itpro/ecommerce-platform-sdk.md).

## Steps to reduce JavaScript

To exclude unused modules, follow these steps to add the module names to the **excludeModules** property in the SDK's **platform.settings.json** file (/src/settings/platform.settings.json).

1. Open a Windows Command Prompt window.
1. Go to the **/src/settings** directory in your SDK installation location.
1. Open the **platform.settings.json** file in a text editor.
1. Insert the following code in JavaScript Object Notation (JSON) format. Replace **\<EXCLUDED\_MODULE\_NAME...\>** with the name of the module to exclude. Each module name must be enclosed in double quotation marks. If you're excluding multiple modules, separate the module names with commas.

    ```json
    {
        "excludedModules": ["<EXCLUDED_MODULE_NAME1>","<EXCLUDED_MODULE_NAME2>"]
    }
    ```

## Validate

Use one or both of the following methods to validate that a module was successfully excluded.

### Method 1

- **Description or purpose:** Verify that the module was successfully excluded.
- **Steps to run:** Compare the chunk size that is shown after a build.
- **Passing result:** The chunk size is smaller after a new build.

### Method 2

- **Description or purpose:** Verify that the module was successfully excluded.
- **Steps to run:** Test the module in a development environment by following these steps:

    1. Run the Node server by using the **yarn start** command.
    1. Visit the following URL: `http://localhost:4000/modules?type=<YOUR-MODULE-NAME>`.

- **Passing result:** The excluded module isn't rendered on the webpage.

## Additional resources

[Install the online SDK](../dev-itpro/ecommerce-platform-sdk.md)

[Set up a development environment](../e-commerce-extensibility/setup-dev-environment.md)
