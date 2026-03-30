---
title: SysTest filtering using class and method attributes
description: Learn about attributes that can be used with SysTest classes and methods for the purpose of test filtering, including the Category, Priority, and Owner attributes.
author: josaw1
ms.author: josaw
ms.topic: article
ms.date: 03/16/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2017-11-15
ms.dyn365.ops.version: AX 7.0.0
---

# SysTest filtering by using class and method attributes

[!include [banner](../includes/banner.md)]

Starting with Platform update 12, the SysTest framework contains improvements to the SysTest class and method attributes in X++. These improvements also change how these attributes work in the Visual Studio test window as well as the Visual Studio Test Console, which is the tool used in the automated build process. The SysTest framework now supports the major test attributes in the adaptor to be on par with the MSTest framework adaptor. This support includes attributes like **Category**, **Owner**, **Priority**, and **Test Property**.

## TestCategory

Previous platform updates already supported the **Category** attribute, **SysTestCategory**. Starting with Platform update 12, you can specify multiple categories on both the class level and the individual method level. Additionally, **TestCategory** is enabled for filtering in the Visual Studio Test Console. This feature means that you can create build pipelines with test filters on specific categories. Use the **TestFilter** variable in the build pipeline. For example, to run tests only with a category **Nightly**, set the variable to **TestCategory=Nightly**.

## Priority

The **Priority** attribute **SysTestPriority**, which requires an integer value, is now available. You can only specify a priority once, but the attribute supports both the class and method level, with method level taking precedence over class level. The priority is also exposed as a test filter. This feature means that you can use the **TestFilter** variable in the build pipeline. For example, to only run tests with a priority of **1**, set the variable to **Priority=1**.

## Owner

The **Owner** attribute, **SysTestOwner**, is also available. The **Test Toolbox** window technically already supports this attribute for filtering, but the attribute itself was missing in X++. Similar to **Priority**, you can only specify an owner once and the attribute supports both the class and method level, with the method level taking precedence. **Owner** isn't available as a test filter for the console, which aligns with the MSTest adaptor for Visual Studio Test Console. However, **Owner** appears in the **Test Toolbox** window in Visual Studio.

## Test Property

Previous releases of the platform already included the **Test Property** attribute, **SysTestProperty**, but it wasn't fully functional. Unfortunately, the **SysTestProperty** attribute exists in the **Application Foundation** package as opposed to the other attributes which exist in the **Test Essentials** package. Because of Microsoft's commitment to backward compatibility of the platform, it currently can't move this attribute to its expected location, so your code needs a reference to the **Application Foundation** package to use it. **SysTestProperty** specifies a property and a value (two strings), and you can now use it in the **Test Toolbox** window in Visual Studio. You can specify **Test Property** multiple times, and it can exist on both the class and method level. **Test Property** isn't available for test filtering in the Visual Studio Test Console, in line with the MSTest adaptor.

For advanced filtering syntax that you can use with the Visual Studio Test Console and to review the filtering example for the MSTest framework, see [Running selective unit tests](/dotnet/core/testing/selective-unit-tests). 

> [!NOTE]
> For test filtering purposes, the SysTest framework allows you to filter on **FullyQualifiedName** and **Name**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
