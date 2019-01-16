---
# required metadata

title: SysTest Filtering using Class and Method Attributes
description: This topic outlines attributes that can be used with SysTest classes and methods for the purpose of test filtering.
author: jorisdg
manager: AnnBe
ms.date: 01/16/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jorisde
ms.search.validFrom: 2017-11-15
ms.dyn365.ops.version: AX 7.0.0

---

# SysTest Filtering using Class and Method Attributes

[!include [banner](../includes/banner.md)]

Starting with Platform Update 12, the SysTest framework contains improvements on SysTest class and method attributes in X++, and how they behave in the Visual Studio test window as well as the Visual Studio Test Console, which is the tool used in the automated build process. The SysTest framework now supports the major test attributes in our adaptor to be on par with the MSTest framework adaptor. This includes attributes like Category, Owner, Priority and Test Property.

## TestCategory

The Category attribute (**SysTestCategory**) was already available in previous platform update using the **SysTestCategory** attribute. Starting with platform update 12 however, you are now able to specify multiple categories on both the class level and the individual method level. Additionally, the **TestCategory** is enabled for filtering in the Visual Studio Test Console, which means you can create build pipelines with test filters on specific categories. You can use the **TestFilter** variable in the build pipeline for this, for example set the variable to "TestCategory=Nightly" to only run tests with a category "Nightly".

## Priority

The Priority attribute (**SysTestPriority**) has been added, requiring an integer value. A priority can only be specified once but is supported on both class and method level, with method level taking precedence over class level. It is also exposed as a test filter so you can use the **TestFilter** variable in the build pipeline for this, for example set the variable to "Priority=1" to only run tests with a priority of 1.

## Owner

The owner attribute (**SysTestOwner**) has been added as well. This attribute was technically already supported for filtering in the **Test Toolbox** window but the attribute itself was missing in X++. Similar to priority, an owner can only be specified once and is supported on both class and method level, with the method level taking precedence. Owner is not available as a test filter for the console, which is in line with the MSTest adaptor for Visual Studio Test Console. Owner will show up in the **Test Toolbox** window in Visual Studio, however.

## Test Property

The test property attribute (**SysTestProperty**) has existed in previous releases of the platform, but wasn't fully functional. Unfortunately the **SysTestProperty** attribute exists in the **Application Foundation** package as opposed to the other attributes which exist in package **Test Essentials**. Due to our commitment to backwards compatibility of the platform we cannot currently move this attribute to its expected location, so your code will need a reference to the **Application Foundation** package to use it. **SysTestProperty** specifies a property and a value (two strings) and can now be used in the Test toolbox window in Visual Studio. Test properties can be specified multiple times, and can exist on both class and method level. Test property is not available for test filtering in the Visual Studio Test Console, in line with the MSTest adaptor.

 
For advanced filtering syntax that can be used with the Visual Studio Test Console, see [Running selective unit tests](https://docs.microsoft.com/en-us/dotnet/core/testing/selective-unit-tests) on Microsoft Docs for .NET and review the filtering examples for the MSTest framework.

Note that for test filtering purposes the SysTest framework has also always allowed you to filter on **FullyQualifiedName** and **Name**, and those features continue to exist.
