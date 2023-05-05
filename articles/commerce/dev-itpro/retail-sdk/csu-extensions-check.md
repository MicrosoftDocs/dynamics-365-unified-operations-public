---
title: Commerce Scale Unit extensions health check
description: This article explains how to use the Commerce Scale Unit extensions health check feature in Microsoft Dynamics 365 Commerce.
author: aneesmsft
ms.date: 05/05/2023
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: aneesa
ms.search.validFrom: 2023-05-01
ms.dyn365.ops.version: AX 10.0.30
---

# Commerce Scale Unit extensions health check

[!include [banner](../../includes/banner.md)]

This article explains how to use the Commerce Scale Unit (CSU) extensions health check feature in Microsoft Dynamics 365 Commerce.

Developers who build CSU extensions can use the Commerce health check feature to run tests that are built into the framework and validate that their extensions meet current requirements. Microsoft highly recommends that developers use the health check feature to ensure that their CSU extensions are compliant.

The CSU extensions health check feature can be accessed by using the following URL format. Replace *CommerceScaleUnitURL* with the URL of your CSU instance.

`https://<CommerceScaleUnitURL>/healthcheck?testname=extensions`

The CSU extensions health check includes the following tests in two main categories:

- **Assembly tests:**

    - Target framework tests
    - Unsupported dependencies test

- **Extension export tests:**

    - Extension types tests
    - Route prefix test
    - Entity binding test

The rest of this article provides details about these categories and the tests that they include.

## Assembly tests

Assembly tests validate assemblies in an extension to ensure that they meet current requirements. The top-level assemblies of an extension are validated first. Next, all dependent assemblies are validated recursively, until the whole dependency tree is traversed. Finally, all unused assemblies in the extension folders are validated. Assembly tests don't validate **System** and **Microsoft.Dynamics** assemblies.

By default, the tests don't show assembly names in the results, to help preserve security. If you require that tests show assembly names in the results, you can implement the following app setting.

``` xml
<appSettings>
    <add key="HealthCheck.Extensions.ShowAssemblyFiles" value="true" />
</appSettings>
```

### Target framework tests

Target framework tests validate the target framework of the assemblies to ensure that it's supported.

The following table summarizes the results that are the output of the target framework tests.

| Column | Value |
|--------|-------|
| Test Name | <p>**Target framework (extensions)** – This test validates the top-level extension assemblies.</p><p>**Target framework (dependencies)** – This test validates assemblies that the extension depends on, both directly and indirectly.</p><p>**Target framework (others)** – This test validates all unused assemblies in the extension folders.</p> |
| Data | <p>**Count** – The number of assemblies that have the same target framework (as specified by the target framework name in the **Result Text** column).</p><p> **Assembly names** – If `HealthCheck.Extensions.ShowAssemblyFiles` is enabled, a comma-separated list of assembly names is shown.</p> |
| Result Text | <p>**Target framework name** – The name of the target framework of the validated assemblies.</p><p>**Not specified** – The assembly isn't marked with `TargetFrameworkAttribute`, or the value is blank.</p><p>**Assembly not found** – The assembly file wasn't found.</p><p>**Failed to load assembly** – The assembly failed to load, possibly because of incompatibility.</p> |
| Test Status | <p>**Succeeded** – The target framework is supported.</p><p>**Failed** – The target framework isn't supported or couldn't be retrieved.</p> |
| Test Severity | **Normal** |

### Unsupported dependencies test

The unsupported dependencies test validates whether the assemblies in an extension or their dependencies reference Commerce assemblies that aren't part of the Commerce software development kit (SDK).

The following table summarizes the results that are the output of the unsupported dependencies test. Results are shown only if the test fails.

| Column | Value |
|--------|-------|
| Test Name | **Unsupported dependencies (Commerce)** |
| Data | <p>**Count** – The number of referenced Commerce assemblies that aren't part of the Commerce SDK.</p><p>**Assembly names** – If `HealthCheck.Extensions.ShowAssemblyFiles` is enabled, a comma-separated list of assembly names is shown.</p> |
| Result Text | Not applicable |
| Test Status | **Failed** – Extensions or their dependencies reference Commerce assemblies that aren't part of the Commerce SDK. |
| Test Severity | **Normal** |

## Extension export tests

Extension export tests validate types that are exported by extension assemblies.

### Extension types tests

Extension types tests validate exported types to ensure that they don't implement obsolete contracts.

The following table summarizes the results that are the output of the extension types tests. Results always include tests for the four different types of contracts.

| Column | Value |
|--------|-------|
| Test Name | <p>**Controllers (IController)** – This test checks for extensions that implement `IController`.</p><p>**Obsolete extensions (ICommerceController)** – This test checks for extensions that implement `ICommerceController`.</p><p>**Obsolete extensions (IRequestHandler)** – This test checks for extensions that implement `IRequestHandler`.</p><p>**Obsolete extensions (IRequestTrigger)** – This test checks for extensions that implement `IRequestTrigger`.</p> |
| Data | <p>**Count** – The number of exported types that implement the contract that's specified in the test name.</p><p>**Assembly names** – If `HealthCheck.Extensions.ShowAssemblyFiles` is enabled, a comma-separated list of assembly names is shown.</p> |
| Result Text | Not applicable |
| Test Status | <p>**Succeeded** – No types implement any of the obsolete contracts. The test for `IController` always succeeds.</p><p>**Failed** – One or more types implement any of the obsolete contracts.</p> |
| Test Severity | **Normal** |

### Route prefix test

The route prefix test validates whether an extension uses one of the reserved route prefixes via the `RoutePrefix` attribute. Extensions that use a reserved route prefix might cause Retail Server to work incorrectly.

The following table summarizes the results that are the output of the route prefix test. Results are shown only if the test fails.

| Column | Value |
|--------|-------|
| Test Name | **Controllers (Invalid route prefix)** |
| Data | <p>**Count** – The number of controllers that have an incorrect route prefix.</p><p>**Assembly names** – If `HealthCheck.Extensions.ShowAssemblyFiles` is enabled, a comma-separated list of assembly names is shown.</p> |
| Result Text | Not applicable |
| Test Status | **Failed** |
| Test Severity | **Normal** |

### Entity binding test

The entity binding test validates whether an extension is bound to a Commerce entity via the `BindEntity` attribute. Extensions that are bound to a Commerce entity might cause Retail Server to work incorrectly.

The following table summarizes the results that are the output of the entity binding test. Results are shown only if the test fails.

| Column | Value |
|--------|-------|
| Test Name | **Controllers (Invalid entity binding)** |
| Data | <p>**Count** – The number of controllers that are incorrectly bound to a Commerce entity.</p><p>**Assembly names** – If `HealthCheck.Extensions.ShowAssemblyFiles` is enabled, a comma-separated list of assembly names is shown.</p> |
| Result Text | Not applicable |
| Test Status | **Failed** |
| Test Severity | **Normal** |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
