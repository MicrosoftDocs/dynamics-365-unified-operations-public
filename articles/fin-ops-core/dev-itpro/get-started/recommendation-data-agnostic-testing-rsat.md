---
title: Data agnostic testing using the Regression Suite Automation Tool
description: Learn about the recommendations for data agnostic testing using the Regression Suite Automation Tool, including overviews on various frameworks.
author: FrankDahl
ms.author: johnmichalak
ms.topic: article
ms.date: 01/20/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2019-09-11
ms.dyn365.ops.version: AX 7.0.0, Operations
---

# Data agnostic testing by using the Regression Suite Automation Tool

[!include [banner](../../../finance/includes/banner.md)]

While you can't make the functional validation of an ERP application fully data agnostic, you can use multiple phases and approaches for testing. These testing phases include:  

- SysTest framework
- ATL framework
- Regression Suite Automation Tool (RSAT)

:::image type="content" source="../../fin-ops/get-started/media/rsat-data-agnostic-testing-01.PNG" alt-text="Screenshot of the test classification pyramid.":::

## Overview

- **SysTest framework** – The SysTest framework is reliable for writing unit tests. Because unit tests generally test a method or function, they should always be data agnostic and dependent only on the input data that the test provides.
- **ATL framework** – Microsoft provides an ATL framework that is an abstraction on the SysTest framework. It makes functional test writing simpler and more reliable. Use this framework for writing component tests or simple integration tests.
- **RSAT** – Use RSAT for integration tests and business cycle tests. The business cycle tests, which are also called the regression validation tests, depend on existing data. However, you can make these tests data agnostic if you consider additional factors.

  - Unit tests and component tests are low level and can be fully data agnostic (not dependent on existing dataset). The business cycle or regression validation tests depend on some existing data. This data includes setup, configuration settings (parameters), and master data (customer, vendors, items, and more), but never transaction data. Make sure that if the test changes any of these values, it reverts them back as part of the final test.
  - Select master data based on certain criteria instead of selecting a particular record. For example, if you want to select an item based on its dimension values and stock availability, filter the product list with those values, select the first item, and copy the number to use for future tests. If it's a simple master data line such as customer, vendor, or item, create it as part of the automation and use it in future tests through chaining.
  - Enter the unique identifiers, such as invoice numbers, through the number sequence or by using Microsoft Excel functions such as `=TEXT(NOW(),"yyyymmddhhmm")`. This function provides a unique number every minute, which allows you to track when the action happened. Use this value for variables such as product receipt numbers and vendor invoice numbers. These tests continue to work on the same database again and again, without requiring any restoration.
  - Always set the **Edit mode** of the environment to **Read** or **Edit** as the first test case because the default option is **Auto**. The **Auto** option always uses the previous setting and can cause unreliable tests.

    :::image type="content" source="../../fin-ops/get-started/media/rsat-data-agnostic-testing-02.PNG" alt-text="Screenshot of the Options page Performance tab.":::

  - Only validate after you filter on a particular transaction instead of generic validation. For example, for the number of records, filter for the transaction number or the transaction date so that the validation excludes all other transactions.
  - If you're checking a customer balance or budget check, save the value first and then add your transaction value to validate the expected result instead of validating a fixed expected value.

[!INCLUDE [footer-include](../../../includes/footer-banner.md)]
