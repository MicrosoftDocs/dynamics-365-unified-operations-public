---
title: Runtime extensions health check
description: This article explains how to use the runtime extensions health check feature.
author: aneesa
ms.date: 03/17/2023
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: aneesa
ms.search.validFrom: 2023-03-17
ms.dyn365.ops.version: AX 10.0.30
---

# Runtime extensions health check

Developers building Commerce runtime extensions can use the health check feature to run tests built into the framework and validate if their extensions meet current requirements.

The health check feature can be accessed using a URL with the following format.
```
https://[CommerceScaleUnitURL]/healthcheck?testname=extensions
```
Replace *CommerceScaleUnitURL* with the URL for your Commerce Scale Unit instance.

## Assembly tests
Assembly tests validate assembiles in an extension to ensure they meet current requirements. The top-level assemblies of an extension are validated first. All dependent assembiles are validated next in a recursive manner until the entire dependency tree is traversed. And finally, all unused assemblies in the extension folders are also validated. Assembly tests do not validate *System* and *Microsoft.Dynamics* assemblies.

To preserve security be default, the tests do not display assembly names in the results. Developers can override this if needed by using the following app setting.
``` xml
<appSettings>
  <add key="HealthCheck.Extensions.ShowAssemblyFiles" value="true" />
</appSettings>
```

### Target framework tests
Target framework tests are a type of assembly test that validate the target framework of the assembiles to ensure it is supported.

The results output by the target framework tests is summarized in the table below.
| Column | Value |
|-----------|----------|
| Test Name | Target framework (extensions) - This test validates the top-level extension assemblies<br/>Target framework (dependencies) - This test validates assembiles that the extension depends on, both direct and indirect.<br/>Target framework (others) - This test validates all unused assemblies located in extension folders. |
| Data | Count - The number of assemblies with the same target framework (as specified in the *Target framework name* in the *Result Text* column).<br/> Assembly names - If *HealthCheck.Extensions.ShowAssemblyFiles* is enabled a comma-separated list of assembly names will be displayed. |
| Result Text | Target framework name - The name of the target framework of the validated assemblies.<br/>Not specified - The assembly is not marked with *TargetFrameworkAttribute* or the value is empty.<br/>Assembly not found - The assembly file was not found<br/>Failed to load assembly - The assembly failed to load, possibly due to incompatibility. |
| Test Status | Succeeded - The target framework is supported.<br/>Failed - The target framework is not supported or could not be retrieved. |
| Test Severity | Normal |

### Unsupported dependencies test
Unsupported dependencies is a type of assembly test that checks to see if the assembiles in an extension or their dependencies are referencing Commerce assemblies that are not a part of the Commerce SDK. Only Commerce assemblies that are a part of the Commerce SDK and marked with the following key can be referenced 
``` csharp
[assembly: AssemblyMetadata("CommercePublicContract", "")]
```
The results output by the unsupported dependencies test is summarized in the table below. Results are only displayed if the test fails.
| Column | Value |
|-----------|:-----------|
| Test Name | Unsupported dependencies (Commerce) |
| Data | Count - The number of referenced Commerce assemblies that are not part of Commerce SDK.<br/> Assembly names - If *HealthCheck.Extensions.ShowAssemblyFiles* is enabled a comma-separated list of assembly names will be displayed.|
| Result Text | - |
| Test Status | Failed - Extensions or their dependencies are referencing Commerce assemblies that are not a part of the Commerce SDK.|
| Test Severity | Normal |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
