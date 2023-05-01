---
title: Commerce Scale Unit extensions health check
description: This article explains how to use the Commerce Scale Unit extensions health check feature.
author: aneesa
ms.date: 05/1/2023
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: aneesa
ms.search.validFrom: 2023-05-01
ms.dyn365.ops.version: AX 10.0.30
---

# Runtime extensions health check

Developers building Commerce Scale Unit extensions can use the health check feature to run tests built into the framework and validate if their extensions meet current requirements.

The Commerce Scale Unit extensions health check feature can be accessed using the following URL format.
```
https://[CommerceScaleUnitURL]/healthcheck?testname=extensions
```
Replace *CommerceScaleUnitURL* with the URL for your Commerce Scale Unit instance.

Commerce Scale Unit extension health check includes the following tests in two main categories.
1. Assembly tests
    1. Target framework tests
    2. Unsupported dependencies test
2. Extension export tests
    1. Extension types tests
    2. Route prefix test
    3. Entity binding test

Details on the categories and the tests they include are given below.

## Assembly tests
Assembly tests validate assemblies in an extension to ensure they meet current requirements. The top-level assemblies of an extension are validated first. All dependent assemblies are validated next in a recursive manner until the entire dependency tree is traversed. And finally, all unused assemblies in the extension folders are validated. Assembly tests do not validate `System` and `Microsoft.Dynamics` assemblies.

To preserve security by default, the tests do not display assembly names in the results. Developers can change this if needed by using the following app setting.
``` xml
<appSettings>
  <add key="HealthCheck.Extensions.ShowAssemblyFiles" value="true" />
</appSettings>
```

### Target framework tests
Target framework tests validate the target framework of the assembiles to ensure it is supported.

The results output by the target framework tests is summarized in the table below.

| Column | Value |
|--------|-------|
| Test Names | Target framework (extensions) - This test validates the top-level extension assemblies.<br/><br/>Target framework (dependencies) - This test validates assembiles that the extension depends on, both direct and indirect.<br/><br/>Target framework (others) - This test validates all unused assemblies located in the extension folders. |
| Data | Count - The number of assemblies with the same target framework (as specified by the *Target framework name* in the *Result Text* column).<br/><br/> Assembly names - If `HealthCheck.Extensions.ShowAssemblyFiles` is enabled a comma-separated list of assembly names will be displayed. |
| Result Text | Target framework name - The name of the target framework of the validated assemblies.<br/><br/>Not specified - The assembly is not marked with `TargetFrameworkAttribute` or the value is empty.<br/><br/>Assembly not found - The assembly file was not found.<br/><br/>Failed to load assembly - The assembly failed to load, possibly due to incompatibility. |
| Test Status | Succeeded - The target framework is supported.<br/><br/>Failed - The target framework is not supported or could not be retrieved. |
| Test Severity | Normal |

### Unsupported dependencies test
Unsupported dependencies test checks to see if the assemblies in an extension or their dependencies are referencing Commerce assemblies that are not a part of the Commerce SDK.
The results output by the unsupported dependencies test is summarized in the table below. Results are only displayed if the test fails.

| Column | Value |
|--------|-------|
| Test Name | Unsupported dependencies (Commerce) |
| Data | Count - The number of referenced Commerce assemblies that are not part of Commerce SDK.<br/><br/> Assembly names - If `HealthCheck.Extensions.ShowAssemblyFiles` is enabled a comma-separated list of assembly names will be displayed.|
| Result Text | - |
| Test Status | Failed - Extensions or their dependencies are referencing Commerce assemblies that are not a part of the Commerce SDK.|
| Test Severity | Normal |

## Extension export tests
Extension export tests validate types exported by extension assemblies.

### Extension types tests
Extension types tests validate exported types to ensure they are not implementing obsolete contracts.

The results output by the extension types tests are summarized in the table below. Results always include tests for the four different types of contracts.

| Column | Value |
|--------|-------|
| Test Names | Controllers (IController) - Checks for extensions implementing `IController`.<br/><br/>Obsolete extensions (ICommerceController) - Checks for extensions implementing `ICommerceController`.<br/><br/>Obsolete extensions (IRequestHandler) - Checks for extensions implementing `IRequestHandler`.<br/><br/>Obsolete extensions (IRequestTrigger) - Checks for extensions implementing `IRequestTrigger`.|
| Data | Count - The number of exported types that implement the contract specified in the test name.<br/><br/> Assembly names - If `HealthCheck.Extensions.ShowAssemblyFiles` is enabled a comma-separated list of assembly names will be displayed.|
| Result Text | - |
| Test Status | Succeeded - If no types are implementing any of the obsolete contracts. Additionally, the test for `IController` always succeeds.<br/><br/>Failed - If one or more types are implementing any of the obsolete contracts.|
| Test Severity | Normal |

### Route prefix test
Route prefix test validates if an extension is using one of the reserved route prefixes via the `RoutePrefix` attribute. If extensions use one of the reserved route prefixes, it may cause the Retail Server to work incorrectly.

The results output by the route prefix test is summarized in the table below. Results are only displayed if the test fails.

| Column | Value |
|--------|-------|
| Test Name | Controllers (Invalid route prefix) |
| Data | Count - The number of controllers with an incorrect route prefix.<br/><br/> Assembly names - If `HealthCheck.Extensions.ShowAssemblyFiles` is enabled a comma-separated list of assembly names will be displayed.|
| Result Text | - |
| Test Status | Failed. |
| Test Severity | Normal |

### Entity binding test
Entity binding test validates if an extension is bound to a Commerce entity via the `BindEntity` attribute. If extensions are bound to one of the Commerce entities, it may cause the Retail Server to work incorrectly.

The results output by the entity binding test is summarized in the table below. Results are only displayed if the test fails.

| Column | Value |
|--------|-------|
| Test Name | Controllers (Invalid entity binding) |
| Data | Count - The number of controllers incorrectly bound to a Commerce entity.<br/><br/> Assembly names - If 'HealthCheck.Extensions.ShowAssemblyFiles' is enabled a comma-separated list of assembly names will be displayed.|
| Result Text | - |
| Test Status | Failed. |
| Test Severity | Normal |

If you are a developer building Commerce Scale Unit extensions, you must use the health check feature to run the built-in validation tests and ensure that your extensions are compliant with current requirements.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
