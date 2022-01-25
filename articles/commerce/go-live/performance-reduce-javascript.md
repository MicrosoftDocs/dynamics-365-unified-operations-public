---
# required metadata

title: Reduce JavaScript by excluding unused modules
description: This topic describes how to improve performance by reducing the JavaScript used in your Microsoft Dynamics 365 Commerce implementation.
author: mssle
ms.date: 01/13/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: sheaton
ms.search.validFrom: 2021-09-20
---

# Reduce JavaScript by excluding unused modules

[!include[banner](../includes/banner.md)]

This topic describes how to improve performance by reducing the JavaScript used in your Microsoft Dynamics 365 Commerce implementation. 

Dynamics 365 Commerce comes with a large set of modules referred to as the Commerce [module library](../starter-kit-overview.md). If there are modules that won't be used on your e-commerce site, they can be excluded to reduce the JavaScript chunk size. The excluded modules will not be rendered on the live e-commerce site or be available in Commerce site builder when authoring pages.

## Configuration

This topic applies to the following configurations:

- **Version**: Commerce 10.0.16 or later.
- **Component**: Business to consumer (B2C) or business to business (B2B). 
- **Feature area**: Commerce website performance.

## Prerequisites

Install the Dynamics 365 Commerce online software development kit (SDK). For more information, see [Install the online SDK](../dev-itpro/ecommerce-platform-sdk.md).

## Steps to reduce JavaScript

Exclude unused modules by adding the module name to the **excludeModules** property in the SDK's "/src/settings/platform.settings.json" file using the instructions below. 

1.	Open a Windows command prompt. 
1.	Navigate to the **/src/settings** directory in your SDK installation location. 
1.	Open the **platform.settings.json** file in a text editor. 
1.	Insert the following JSON-formatted code, replacing ```<EXCLUDED_MODULE_NAME1>``` with the name of the module you want to exclude. The module name must be in double quotes. Separate multiple module names with commas.

```json
{
    "excludedModules": ["<EXCLUDED_MODULE_NAME1>","<EXCLUDED_MODULE_NAME2>"]
}
```

## Validate

Use one or more of the following methods to validate that the module was successfully excluded.

### Method 1: 

- **Description or Purpose:** Verify the module was successfully excluded.
- **Steps to Run:**  Compare the chunk size displayed after a build.
- **Passing Result:** Chunk size is smaller after a new build.

### Method 2: 

- **Description or Purpose:** Verify the module was successfully excluded.
- **Steps to Run:**  Test the module in a development environment by following these steps: 
    1. Run the Node server by using the **yarn start** command.
    1. Visit the URL `http://localhost:4000/modules?type=<YOUR-MODULE-NAME>`.  
- **Passing Result:** The excluded module is not rendered on the webpage.

## Additional resources

[Install the online SDK](../dev-itpro/ecommerce-platform-sdk.md)

[Set up a development environment](../e-commerce-extensibility/setup-dev-environment.md) 
  
