---
# required metadata

title: Regression suite automation tool
description: The Regression suite automation tool lets you record business tasks using the task recorder and convert them into a suite of automated tests without the need to write source code.
author: robadawy
manager: AnnBe
ms.date: 08/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 21631
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.search.validFrom: 2019-08-01
ms.dyn365.ops.version: AX 7.0.0

---

# Regression Suite Automation Tool

[!include [banner](../../includes/banner.md)]

## Overview
The Regression suite automation tool (RSAT) significantly reduces the time and cost of user acceptance testing. User acceptance testing is typically required before taking a  Microsoft application update or applying custom code and configurations to your production environment.

This tool enables functional power users to record business tasks using the Task recorder and convert these recordings into a suite of automated tests without the need to write source code. Test libraries are stored and distributed in Lifecycle Services (LCS) using the Business Process Modeler (BPM) libraries. These libraries are also fully integrated with Azure DevOps Services (Azure DevOps) for test execution, reporting and investigation. Test parameters are decoupled from test steps and stored in Microsoft Excel files.

RSAT usage is described in these topics:

+ [Regression Suite Automation Tool (this topic)](rsat-overview.md)
+ [Regression Suite Automation Tool installation and configuration](rsat-install-configure.md)
+ [Run Regression Suite Automation Tool test cases](rsat-run.md)
+ [Validate expected values](rsat-validate-expected.md)
+ [Chain test cases](rsat-chain-test-cases.md)
+ [Derived test cases](rsat-derived-test-cases.md)
+ [Regression Suite Automation Tool best practices](rsat-best-practices.md)
+ [Troubleshoot the Regression Suite Atomation Tool](rsat-troubleshooting.md)


## End-to-end flow
This tool is part of the end to end flow described below. The application, along with LCS and Azure DevOps, provide a set of tools for test case authoring (using Task recorder), configuration, execution, investigation, and reporting.

![Author, configure, and execute](media/end-to-end.png)

To learn more about this this process, see [Create and automate user acceptance tests](../../lifecycle-services/using-task-guides-and-bpm-to-create-user-acceptance-tests.md).

## Lifecycle Services
Using Lifecycle Services (LCS) and BPM is recommended but not required. BPM is enables management and distribution of test libraries across projects and tenants, this is especially useful for Microsoft partners and independent software vendors. 

If you are not using BPM, you can manually create test cases in Azure DevOps and attach developer recording files to your Azure DevOps test cases. Developer recording files can be created directly from the Task recorder pane.

![Save task recording as developer](media/save-as-developer.png)

You must name the developer recording file **Recording.xml** before attaching it to the Azure DevOps test case. Alterntively, the recording file can also be named **-Test Case Title-.xml** where **-Test Case Title-** is the DevOps title of the test case.

![Add attachment](media/attachments.png)

## Intended usage and test classification

### Business cycle (business process) testing
The Regression suite automation tool is intended to be used for business cycle tests and scenario tests (multiple component tests) that usually occur at the end of the development lifecycle. This is also referred to as *user acceptance testing*. Business cycle testing consists of a smaller number of test cases than component or unit testing. This is illustrated in the following graphic.

![Unit tests, component tests, multiple component tests, business cycle tests](media/business-cycle.png)

### Unit and component testing
For unit tests, we do not recommend that you use RSAT. Instead, use the SysTest framework and the build/test automation tools. For component tests, take advantage of the [Acceptance Test Library](../acceptance-test-library.md) (ATL). ATL is a library of X++ test helpers. When used with the SysTest framework, it offers the following benefits:
+ Lets you create consistent test data.
+ Increases the readability of test code.
+ Provides improved discoverability of the methods that are used to create test data.
+ Hides the complexity of setting up prerequisites.
+ Supports high performance of test cases.

For more details, see [Continuous delivery home page](../../dev-tools/continuous-delivery-home-page.md).

### Data integration testing
Do not use RSAT for integration tests, instead rely on the data management framework (also known as DIXF). The [Data task automation](../../data-entities/data-task-automation.md) framework enables you to configure and automate the testing of your data integration scenarios.
