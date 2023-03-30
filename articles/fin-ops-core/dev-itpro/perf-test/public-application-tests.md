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
| Acceptance Test Library - Test Case Common (`AtlTestCaseCommon`) | A collection of abstract classes making it easier to create tests focused on a particular area. |
| Warehouse Public Tests (`WHSTests`) | A collection of scenario and performance tests for [Warehouse Management](../../../supply-chain/warehousing/warehouse-management-overview.md). |

The tests serve the following purposes:

- Enable engineers to detect eventual regressions early. For example, to identify an extension that breaks a standard scenario.
- Serve as inspiration for authoring test coverage of your own scenarios. For example, find a test covering a similar scenario, copy it, and modify it to cover your variant of the scenario.

## Run the tests

You'll typically run tests using one of the following methods:

- **Run related tests in Visual Studio**. If you right-click a project in Visual Studio and select **Discover tests**, the system will automatically add any test to your project that is related to the other files in your project. This makes is easy to run the most important tests quickly using the Test Explorer.
- **Run all tests**. The simplest approach is to add all tests from a model to a new project and then use Test Explorer to run the tests. Running the tests can take a long time.
- **Integrate test automation in your build pipeline**. Running tests as frequently as possible minimizes the time needed to detect a regression. Ideally, a pull request containing a regression would be rejected.

For more information about how to configure build pipelines, see [Deploy and use a continuous build and test automation environment](continuous-build-test-automation.md).

## Notes

Here are a few notes about the tests:

- The tests are also used by Microsoft during regular engineering. They are typically marked as internal, and subject to change, like any other internal X++ class or method.
- The tests are implemented using SysTest, Form adaptors, Acceptance Test Library and other available frameworks. They can all be run in Microsoft Visual Studio.
- The test methods are grouped in classes, and typically follow a naming standard of *when_given_then*. For example, a test that validates an exception thrown when attempting to reserve an item that isn't available could be named `reservingItem_noOnhand_exception`.
- The tests don't have data dependencies. They set up and tear down everything they need to pass. This means that you don't need a demo data set to use the tests.
- The tests should be used during development and quality assurance, not on production systems. Running test automation on production systems can have undesirable consequences, including loss of production data.
- The tests are also powerful for learning about and debugging how an area is implemented. The tests are repeatable, the debugger gives you full insights, and even the possibility to alter variables and execution on the fly.
