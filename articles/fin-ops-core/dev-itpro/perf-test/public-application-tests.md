---
title: Public application tests
description: This article describes a collection of tests that cover the standard functionality of finance and operations apps.
author: MichaelFruergaardPontoppidan
ms.author: mfp
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 04/21/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Public application tests

This article describes a collection of tests that cover the standard functionality of finance and operations apps. The following table lists the tests that are available.

| Name | Description |
|---|---|
| Acceptance Test Library - Test Case Common (`AtlTestCaseCommon`) | A collection of abstract classes that make it easier to create tests that are focused on a specific area. |
| Warehouse Public Tests (`WHSTests`) | A collection of scenario and performance tests for [Warehouse Management](../../../supply-chain/warehousing/warehouse-management-overview.md). |

The tests serve the following purposes:

- Enable engineers to detect eventual regressions early. For example, they can identify an extension that breaks a standard scenario.
- Serve as inspiration for the creation of test coverage for your own scenarios. For example, you can find a test that covers a similar scenario, copy it, and modify it to cover your variant of the scenario.

## Run the tests

You'll typically use one of the following methods to run tests:

- **Run related tests in Visual Studio.** If you select and hold (or right-click) a project in Microsoft Visual Studio and then select **Discover tests**, the system automatically finds any test that's related to the other files in your project, and adds it to your project. This approach makes it easy to quickly run the most important tests by using Test Explorer.
- **Run all tests.** The easiest approach is to add all tests from a model to a new project and then use Test Explorer to run the tests. It can take a long time to run the tests.
- **Integrate test automation in your build pipeline.** By running tests as often as possible, you help minimizes the time that's required to detect a regression. Ideally, a pull request that contains a regression will be rejected.

For more information about how to configure build pipelines, see [Deploy and use a continuous build and test automation environment](continuous-build-test-automation.md).

## Notes

Here are a few notes about the tests:

- The tests are also used by Microsoft during regular engineering. They're typically marked as internal and subject to change, like any other internal X++ class or method.
- The tests are implemented by using SysTest, Form adaptors, Acceptance Test Library, and other available frameworks. They can all be run in Visual Studio.
- The test methods are grouped in classes and typically use the *when_given_then* naming standard. For example, if a test validates an exception that's thrown when an attempt is made to reserve an item that isn't available, the name might be `reservingItem_noOnhand_exception`.
- The tests don't have data dependencies. They set up and tear down everything that they need to pass. Therefore, you don't need a demo data set to use the tests.
- The tests should be used only during development and quality assurance. They should not be used on production systems. Execution of test automation on production systems can have undesirable consequences, including loss of production data.
- The tests are also powerful tools for learning how an area is implemented and debugging the implementation. The tests are repeatable, and the debugger gives you full insights. It even lets you alter the variables and execution on the fly.
