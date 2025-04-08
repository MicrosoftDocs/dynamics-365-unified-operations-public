---
title: SysTest filtering using class and method attributes
description: Learn about attributes that can be used with SysTest classes and methods for the purpose of test filtering, including the Category, Priority, and Owner attributes.
author: josaw1
ms.author: josaw
ms.topic: article
ms.date: 01/22/2019
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2017-11-15
ms.dyn365.ops.version: AX 7.0.0
---

# SysTest Filtering using class and method attributes

[!include [banner](../includes/banner.md)]

Starting with Platform update 12, the SysTest framework contains improvements to the SysTest class and method attributes in X++. These improvements also change how these attributes work in the Visual Studio test window as well as the Visual Studio Test Console, which is the tool used in the automated build process. The SysTest framework now supports the major test attributes in the adaptor to be on par with the MSTest framework adaptor. This includes attributes like **Category**, **Owner**, **Priority**, and **Test Property**.

## TestCategory

The **Category** attribute, **SysTestCategory**, was already available in previous platform updates using the **SysTestCategory** attribute. Starting with Platform update 12, you can specify multiple categories on both the class level and the individual method level. Additionally, **TestCategory** is enabled for filtering in the Visual Studio Test Console. This means that you can create build pipelines with test filters on specific categories. You can use the **TestFilter** variable in the build pipeline. For example, to run tests only with a category **Nightly**, set the variable to **TestCategory=Nightly**.

## Priority

The **Priority** attribute **SysTestPriority**, which requires an integer value, is now available. A priority can only be specified once, but is supported on both the class and method level, with method level taking precedence over class level. The priority is also exposed as a test filter. This means that you can use the **TestFilter** variable in the build pipeline. For example, to only run tests with a priority of **1**, set the variable to **Priority=1**.

## Owner

The **Owner** attribute, **SysTestOwner**, has also been added. This attribute was technically already supported for filtering in the **Test Toolbox** window, but the attribute itself was missing in X++. Similar to **Priority**, an owner can only be specified once and is supported on both the class and method level, with the method level taking precedence. **Owner** is not available as a test filter for the console, which aligns with the MSTest adaptor for Visual Studio Test Console. However, **Owner** will appear in the **Test Toolbox** window in Visual Studio.

## Test Property

The **Test Property** attribute, **SysTestProperty**, has existed in previous releases of the platform, but wasn't fully functional. Unfortunately, the **SysTestProperty** attribute exists in the **Application Foundation** package as opposed to the other attributes which exist in the **Test Essentials** package. Because of our commitment to backward compatibility of the platform, we currently cannot move this attribute to its expected location, so your code will need a reference to the **Application Foundation** package to use it. **SysTestProperty** specifies a property and a value (two strings), and can now be used in the **Test Toolbox** window in Visual Studio. **Test Property** can be specified multiple times, and can exist on both the class and method level. **Test Property** is not available for test filtering in the Visual Studio Test Console, in line with the MSTest adaptor.

For advanced filtering syntax that can be used with the Visual Studio Test Console and to review the filtering example for the MSTest framework, see [Running selective unit tests](/dotnet/core/testing/selective-unit-tests). 

> [!NOTE]
> For test filtering purposes, the SysTest framework allows you to filter on **FullyQualifiedName** and **Name**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
