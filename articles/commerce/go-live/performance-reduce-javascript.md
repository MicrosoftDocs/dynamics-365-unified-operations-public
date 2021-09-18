---
# required metadata

title: Optimize Performance by Reducing JavaScript
description: This article discusses how to optimize performance by reducing the JavaScript used in your implementation.
author: mssle
ms.date: 09/17/2021
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: sheaton
ms.search.validFrom: 2021-09-20
---

# Optimize performance by reducing JavaScript

[!include[banner](../includes/banner.md)]


This topic describes how to improve website performance by excluding unused JavaScript modules in Microsoft Dynamics 365 Commerce. 

Dynamics 365 Commerce comes with a large set of modules referred to as the Commerce [module library](https://docs.microsoft.com/en-us/dynamics365/commerce/starter-kit-overview). If there are modules that won't be used on an e-Commerce site, they can be excluded to reduce the JavaScript chunk size. The excluded modules will not be rendered on the live e-Commerce site or available within Commerce site builder when authoring pages.

## When should I use this topic?
This topic applies to the following configurations:

<table>
<tr>
    <th>When your...</th>
    <th>is...</th>
<tr>
    <th>Process</th>
    <td>Upgrade or Go Live</td>
</tr>
<tr>
    <th>Component</th>
    <td>B2C eCommerce or B2B eCommerce</td>
</tr>
<tr>
    <th>Feature Area</th>
    <td>eCommerce Website Performance</td>
</tr>
<tr>
    <th>Version</th>
    <td>eCommerce version 10.0.16 or later</td>
</tr>
</table> 

## How do I perform this operation?

### Pre-conditions:

- You have installed the Online SDK. Read more: https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/ecommerce-platform-sdk

### Steps to complete:

Exclude unused modules by adding the module name to the **excludeModules** property in the SDK's "/src/settings/platform.settings.json" file using the instructions below. 
1.	Open a Windows command prompt. 
1.	Navigate to the directory **/src/settings** in the SDK install location. 
1.	Open the file **platform.settings.json** in a text editor. 
1.	Insert the following json-formatted content, replacing ```<EXCLUDED_MODULE_NAME1>``` with the name of the module you wish to exclude. The module name must be in double quotes. Separate multiple module names with a comma.
```json
{
    "excludedModules": ["<EXCLUDED_MODULE_NAME1>","<EXCLUDED_MODULE_NAME2>"]
}
```

## Validation Steps

You have two options to validate that the module was successfully excluded.

### Method 1: 

- **Description or Purpose:** Verify the module was successfully excluded
- **Steps to Run:**  Compare the chunk size displayed after a build
- **Passing Result:** Chunk size is smaller after a new build

### Method 2: 

- **Description or Purpose:** Verify the module was successfully excluded
- **Steps to Run:**  Test the module in a development environment: 
    1. Run the Node server by using the "yarn start" command
    1. Visit the URL http://localhost:4000/modules?type=&lt;your-module-name&rt;  
- **Passing Result:** The excluded module is not rendered

## Additional resources
-	e-Commerce platform software development kit (SDK): https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/ecommerce-platform-sdk 
-	Set up a development environment: https://docs.microsoft.com/en-us/dynamics365/commerce/e-commerce-extensibility/setup-dev-environment 
  
