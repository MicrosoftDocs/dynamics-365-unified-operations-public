---
title: Derived test cases
description: Learn about how you can use the Regression suite automation tool to execute the same test case with multiple configurations.
author: FrankDahl
ms.author: fdahl
ms.topic: how-to
ms.date: 11/27/2023
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2019-08-01
ms.dyn365.ops.version: AX 7.0.0
---


# Derived test cases

[!include [banner](../../includes/banner.md)]

The Regression suite automation tool (RSAT) lets you use the same task recording with multiple test cases, so that you can run a task with different data configurations. Select a test case in the Regression suite automation tool and then select **Generate > Create Derived Test Case**. This creates a child test case in Azure DevOps. The resulting derived test case is linked to its parent test case in Azure DevOps. It has an Excel parameters file attached but no recording file. The derived test case appears in the Regression suite automation tool grid under the same test suite with the **Derived** column selected. By default, derived test cases are named after their parent test case with a numeric suffix.

In the following image, a derived test case was created from a test case named **Create a Sales Order and Validate - v2**. The derived test case was renamed (in Azure DevOps) to **Create a Sales Order and Validate - v2 (Fail validation)**.

![Example of derived test case.](media/derived-test-case.png)

In Azure DevOps, a derived test case is a child item of the **Create a Sales Order and Validate - v2** test case and is tagged with the special keyword **RSAT:DerivedTestSteps**.

![Example of derived test case that is automatically created.](media/derived-1.png)

When you run a derived test case, it uses the recording of its parent test case and its own copy of the Excel parameters file. This allows you to run the same test with different parameters without the need to maintain more than one recording.

A derived test case doesn't need to be part of the same test suite as its parent test case, and you can use it in another suite. You can also rename a derived test case. You can edit the Excel parameters file of a derived test case to run it with a different user, a different company, or with different input and validation parameters than its parent test case.


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
