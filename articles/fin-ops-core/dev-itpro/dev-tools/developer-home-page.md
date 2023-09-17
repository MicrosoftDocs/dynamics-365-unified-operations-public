---
title: Develop and customize home page
description: This article provides links to topics about development.
author: josaw1
ms.date: 06/13/2022
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.collection: get-started
---

# Develop and customize home page

[!include [banner](../includes/banner.md)]

This article provides links to topics about development.

## Overview

The finance and operations apps enable the entire enterprise resource planning (ERP) application suite as a cloud-based solution, for both public and private clouds, as well as on-premises. The apps leverage the speed, simplicity, and cost-effectiveness of working in the cloud, while building on the latest technology from Microsoft. The development experience includes:

- Development tools that are decoupled from any running environment. You develop against local, XML-based files, not the online database.
- Microsoft Visual Studio is the development environment. The Visual Studio environment is customized to provide you with a smooth and familiar experience.
- The X++ compiler generates Common Intermediate Language (CIL) for all features. CIL is the same intermediate language used by other .NET-based (managed) languages, such as the C\# programming language.
- You can leverage the browser-based client and the design patterns for forms to provide an improved end-user experience.
- The Application Lifecycle Model (ALM) supports build automation, test automation, and deployment of models to the cloud.

## Architecture

- [Application stack and server architecture](application-stack-server-architecture.md)

## Getting started

- [Get evaluation copies](get-evaluation-copy.md)
- [Sign up for preview subscriptions](sign-up-preview-subscription.md)
- [Deploy and access development environments](../dev-tools/access-instances.md)
- [Development system requirements](development-system-requirements.md)
- [Removed or deprecated features](../migration-upgrade/deprecated-features.md)
- [Deprecated APIs](../migration-upgrade/deprecated-apis.md)
- [Rename a local development (VHD) environment](../migration-upgrade/vso-machine-renaming.md)
- [Introduction to Azure DevOps (Video)](https://channel9.msdn.com/Events/Build/2014/2-575)

## Fleet Management

- [Fleet Management sample application](introduction-fleet-management-sample.md)
- [End-to-end scenario for the Fleet Management sample application](fleet-management-sample.md)

## Development tools

### Tutorials for development tools

- [Development tools tutorial](introduction-visual-studio.md)
- [Create models and data model elements overview](create-data-model-elements.md)
- [Build and debug projects](build-debug-project.md)
- [Version control, metadata search, and navigation](version-control-metadata-navigation.md)

### Tools, models, and VMs

- [Development tools in Visual Studio](development-tools-overview.md)
- [Application Explorer](application-explorer.md)
- [Finance and operations project type in Visual Studio](projects.md)
- [Element designers](element-designers.md)
- [Commands for determining how elements are used](element-usage.md)
- [Models and packages](models.md)
- [Build operations](build-operations.md)
- [Code editor features](code-editor.md)
- [Tools add-ins for Visual Studio](developer-tools-add-ins.md)
- [Export and import models](models-export-import.md)
- [Metadata search in Visual Studio](metadata-search-visual-studio.md)
- [Create new users on development machines](/d365F-O/fin-ops-core/dev-itpro/dev-tools/access-instances)
- [Update the Visual Studio development tools](update-development-tools.md)
- [Development and build VMs that don't allow admin access FAQ](../sysadmin/VMs-no-admin-access.md)

## Build automation using Azure

- [Build automation using Microsoft-hosted agents and Azure Pipelines](hosted-build-automation.md)
- [Add license files to a deployable package in Azure Pipelines](pipeline-add-license-package.md)
- [Create deployable packages in Azure Pipelines](pipeline-create-deployable-package.md)
- [X++ model-versioning in Azure Pipelines](pipeline-model-version.md)
- [Download assets by using Azure Pipelines](pipeline-asset-download.md)
- [Upload assets by using Azure Pipelines](pipeline-asset-upload.md)
- [Deploy assets by using Azure Pipelines](pipeline-deploy-asset.md)
- [Create a Lifecycle Services (LCS) connection in Azure Pipelines](pipeline-lcs-connection.md)
- [Update the hosted Azure Pipeline for new NuGet packages](pipeline-nuget-split.md)
- [Update a legacy pipeline in Azure Pipelines](pipeline-msbuild-update.md)

## X++ programming language

### Reference

- [X++ language reference](../dev-ref/xpp-language-reference.md)

### Overviews

- [Write business logic by using C\# and X++ source code](write-business-logic.md)
- [Visual Studio requirements for X++](developer-tools-vs2017.md)

### Language support

- [EventHandlerResult classes in request or response scenarios](event-handler-result-class.md)
- [Debug X++ code by using the debugger in Visual Studio](debug-xpp.md)
- [Language Integrated Query (LINQ) provider for C\#](linq-provider-c.md)
- [Write best practice rules](author-best-practice-rules.md)
- [SysSetupConfigAttribute attribute](syssetupconfigattribute.md)

## Customize with extensions and overlayering

- [Extensibility home page](../extensibility/extensibility-home-page.md)
- [Customize App Suite reports by using extensions](../analytics/customize-app-suite-reports-with-extensions.md)

## Code migration

- [Code migration and upgrade home page](../migration-upgrade/code-migration-home-page.md)

## Move packages between environments

- [Create deployable packages of models](../deployment/create-apply-deployable-package.md)

## Performance

- [Take traces by using Trace parser](../perf-test/trace-trace-tutorial.md)
- [Diagnose issues and analyze performance by using Trace parser](../perf-test/trace-parser.md)
- [Performance timer](../perf-test/performance-timer.md)

## User interface concepts

The client is an HTML web client that runs in all major browsers. For information about developing and customizing the user interface, see the [User interface development home page](../user-interface/user-interface-development-home-page.md).

## Analytics

- [Analytics, aggregate measurements, and KPI modeling](../analytics/analytics.md)

## Reporting services

- [Electronic reporting (ER) overview](../analytics/general-electronic-reporting.md)

## Data entities and OData

- [Data entities overview](../data-entities/data-entities.md)
- [Open Data Protocol (OData)](../data-entities/odata.md)

## Testing support in Visual Studio

- [Testing and validations](../perf-test/testing-validation.md)
- [Test projects in Visual Studio](../perf-test/testing-support.md)
- [Deploy and use a continuous build and test automation environment](../perf-test/continuous-build-test-automation.md)
- [Task recorder resources](../user-interface/task-recorder.md)

## Office integration

- [Office integration overview](../office-integration/office-integration.md)

## Intelligence

- [Business intelligence (BI) and reporting home page](../analytics/bi-reporting-home-page.md)

## Mobile platform

- [Mobile platform resources](../mobile-apps/platform/mobile-platform-home-page.md)

## Global finance management

- [Development for Dynamics 365 Finance home page](../financial/financial-dev-home-page.md)

## Development for independent software vendors

- [Independent software vendor (ISV) development home page](isv-dev-home-page.md)

## Supply Chain Management

- [Gantt control development guide](../user-interface/gantt-development-guide.md)
- [Create a new transportation management engine](../../../supply-chain/transportation/create-new-transportation-management-engine.md)

## Additional resources

[Insider tips on development](https://community.dynamics.com/ax/b/newdynamicsax)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

