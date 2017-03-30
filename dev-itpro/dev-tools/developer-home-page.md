---
# required metadata

title: Developer home page
description: This topic provides links to topics about development with Microsoft Dynamics 365 for Operations.
author: RobinARH
manager: AnnBe
ms.date: 2015-12-10 20 - 47 - 56
ms.topic: index-page
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 21631
ms.assetid: 06e26767-6056-4755-b47e-0bda71833581
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Developer home page

This topic provides links to topics about development with Microsoft Dynamics 365 for Operations.

Overview
--------

Microsoft Dynamics 365 for Operations represents the next-generation enterprise resource planning (ERP) offering from Microsoft. It is designed to enable the entire ERP application suite as a cloud-based solution, for both public and private clouds, as well as on-premises. It leverages the speed, simplicity, and cost-effectiveness of working in the cloud, while building on the latest technology from Microsoft. This release introduces significant changes to the development experience. These changes include:

-   Development tools that are decoupled from any running environment. You develop against local, XML-based files, not the online database.
-   Microsoft Visual Studio replaces MorphX as the development environment. Dynamics 365 for Operations customizes the Visual Studio environment to provide you with a smooth and familiar experience.
-   The X++ compiler generates Common Intermediate Language (CIL) for all features. CIL is the same intermediate language used by other .NET-based (managed) languages, such as the C\# programming language.
-   New browser-based client and new design patterns for forms that you can leverage to provide an improved end-user experience.
-   The new Application Lifecycle Model (ALM) for build automation, test automation, and deployment of models to the cloud.

## Architecture
-   [Application stack and server architecture](application-stack-server-architecture.md)

## Getting started
-   [Get an evaluation copy](get-evaluation-copy.md)
-   [LCS101 – Sign up for a subscription](sign-up-preview-subscription.md)
-   [Access development instances](..\dev-tools\access-instances.md)
-   [Development system requirements](development-system-requirements.md)
-   [Deprecated features](..\migration-upgrade\deprecated-features.md)
-   [Deprecated API’s](..\migration-upgrade\deprecated-apis.md)
-   [Feedback and support (Office Mix)](https://mix.office.com/watch/92azzna59jj6)
-   [Rename and reboot machines for Visual Studio Online (Office Mix)](..\migration-upgrade\vso-machine-renaming.md)
-   [Configure your developer VM (Office Mix)](configure-developer-vm.md)
-   [Introduction to Visual Studio Online (Video)](http://channel9.msdn.com/Events/Build/2014/2-575)

## Fleet Management
-   [Fleet Management sample](introduction-fleet-management-sample.md)
-   [INT101: Introduction to Fleet Management](fleet-management-sample.md)

## Development tools
### Tutorials

-   [Introduction to Visual Studio development](introduction-visual-studio.md)
-   [Create a simple data model](create-data-model-elements.md)
-   [Building and debugging a project](build-debug-project.md)
-   [Version control, metadata search, navigation, and other features](development-tools.md)

### Tools, models, and VMs

-   [Development tools](development-tools.md)
-   [Introduction to the development environment (Office Mix)](https://mix.office.com/watch/1tz7194y62m3s)
-   [Enable a new user account to develop on a development VM](enable-development-machine.md)
-   [Application Explorer](application-explorer.md)
-   [Projects](projects.md)
-   [Element designers](element-designers.md)
-   [Element usage](element-usage.md)
-   [Models](models.md)
-   [Build operations](build-operations.md)
-   [Visual Studio code editor](code-editor.md)
-   [Developer tools add-ins](developer-tools-add-ins.md)
-   [Distribution of models: How to export and import a model](models-export-import.md)
-   [Configure your developer VM](configure-developer-vm.md)
-   [Metadata search in Visual Studio](metadata-search-visual-studio.md)
-   [Learn about packages, models and Visual Studio (Office Mix)](https://mix.office.com/watch/ies6lyit6773)
-   [Development tools performance tips (Office Mix)](https://mix.office.com/watch/rnp6ng9wu8kx)
-   [Resolve conflicts using Visual Studio](https://mix.office.com/watch/1rl75ei2cs6d7)

## X++ programming language
### Tutorials

-   [New X++ and debugger features](new-x-debugger-features.md)
-   [C\# and X++ interoperability and LINQ](write-business-logic.md)

### Language support

-   [Programming language support](programming-language-support.md)
-   [EventHandlerResult classes in request or response scenarios](event-handler-result-class.md)
-   [Debugging X++ code](debug-xpp.md)
-   [LINQ provider for use in C\#](linq-provider-c.md)
-   [Authoring best practice rules](author-best-practice-rules.md)

### Reference

-   [X++ language reference](..\dev-ref\xpp-language-reference.md)

## Customize with extensions and overlayering
-   [Extensibility home page](..\extensibility\extensibility-home-page.md)

## Code migration
### Migrate your code

To migrate your code to Dynamics 365 for Operations, use the "Migrate and Create Dynamics 365 for Operations Solutions" methodology in Lifecycle Services.

### Key concepts

The following links (also included in the methodology) describe key concepts and steps in the migration process. The links are listed here in the order that we recommend you read them.

-   [Overview: Prepare to migrate to Microsoft Dynamics 365 for Operations](..\migration-upgrade\prepare-migration.md)
-   [Migrate from AX 2012 to Dynamics 365 for Operations (Office Mix)](https://mix.office.com/watch/4gsvk592c685)
-   [Migrate between versions (Office Mix)](https://mix.office.com/watch/os2wff38zi6f)
-   [Configure your VSTS mapping after a code upgrade](..\migration-upgrade\configure-vso-solution.md)
-   [Configure version control with VSTS (Office Mix)](https://mix.office.com/watch/1ftubtqzp3xxl)
-   [Resolve conflicts using Visual Studio (Office Mix)](https://mix.office.com/watch/1rl75ei2cs6d7)
-   [Understanding the model split](model-split.md)
-   [Deprecated features](..\migration-upgrade\deprecated-features.md)
-   [Deprecated API’s](..\migration-upgrade\deprecated-apis.md)
-   [Development tools performance tips](https://mix.office.com/watch/rnp6ng9wu8kx)
-   [Configuring your developer VM](configure-developer-vm.md)

### Additional concepts

-   [Delegates for migration](..\migration-upgrade\delegates-migration.md)
-   [How to import a SQL Server Analysis Services Project into the AOT](https://technet.microsoft.com/en-us/library/dn754850.aspx)
-   [Database synchronization](database-synchronization.md)
-   [Understand the migration task list (Office Mix)](https://mix.office.com/watch/kcek55rc5cau)
-   [Generating the form patterns report (Office Mix)](https://mix.office.com/watch/jqzesi1uuosz)

## Move packages between environments
-   [Create and apply a deployable package](..\deployment\create-apply-deployable-package.md)

## Service environments
-   [Configure and execute the code upgrade service in Lifecycle Services](..\lifecycle-services\configure-execute-code-upgrade.md)
-   [Download hotfixes from Lifecycle Services](..\migration-upgrade\download-hotfix-lcs.md)
-   [Install a binary hotfix or install a deployable package](..\deployment\apply-deployable-package-system.md)
-   [Install an application metadata hotfix](..\migration-upgrade\install-metadata-hotfix-package.md)
-   [Install retail hotfixes](/dynamics365/operations/retail/dev-itpro/install-retail-hotfix?toc=/dynamics365/operations/dev-itpro/toc.json)
-   [Installing a financial reporting binary hotfix](..\migration-upgrade\install-financial-reporting-binary-hotfix.md)
-   [Patching the reporting service](..\migration-upgrade\patch-reporting-service-environment.md)
-   [Updating the Visual Studio development tools](update-development-tools.md)

## Performance
-   [Take a trace with the Trace Parser and analyze it](..\perf-test\trace-trace-tutorial.md)
-   [Introduction to the PerfSDK and multiuser testing with Visual Studio Online](..\perf-test\perfsdk-tutorial.md)
-   [Using the desktop version of trace parser to diagnose problems and analyze performance issues](..\perf-test\trace-parser.md)
-   [Performance timer](..\perf-test\performance-timer.md)
-   [Expanding data with the Data Expansion tool (Office Mix)](https://mix.office.com/watch/11cet1u4nmn64)
-   [Analyzing performance Issues with Trace Parser (Office Mix)](https://mix.office.com/watch/17d76cll0npyw)
-   [The performance timer and other tools (Office Mix)](https://mix.office.com/watch/ij5cqidra5q3)
-   [Using Task Recorder to create a single user performance test (Office Mix)](https://mix.office.com/watch/qtdlasy2rcf3)
-   [The performance timer and other tools (Office Mix)](https://mix.office.com/watch/ij5cqidra5q3)
-   [Analyzing performance Issues with Trace Parser (Office Mix)](https://mix.office.com/watch/17d76cll0npyw)

## User interface concepts
The client is an HTML web client that runs in all major browsers. For information about developing and customizing the user interface, see the [User interface development home page](..\user-interface\user-interface-development-home-page.md).

## Analytics
### Tutorials

-   [How to create a Power BI report](..\analytics\create-powerbi-report-data.md)
-   [Create a Power BI report and dashboard](..\analytics\create-powerbi-report-dashboard.md)
-   [Migrate an upgraded Dynamics AX 2012 R3 sales cube to the entity store](..\migration-upgrade\migrate-upgraded-cube-entity-store.md)
-   [Customize App Suite reports using extensions](..\analytics\customize-app-suite-reports-with-extensions.md)

### Concepts

-   [Analytics](..\analytics\analytics.md)
-   [Power BI integration](..\analytics\power-bi-integration.md)
-   [Configuring Power BI integration for workspaces](..\analytics\configure-power-bi-integration.md)

## Reporting services
-   [Create next-generation reporting solutions](..\analytics\create-nextgen-reporting-solutions.md)
-   [Document Reporting Services overview](..\analytics\document-reporting-services.md)
-   [Tips to help prevent long-running reports from timing out](..\analytics\prevent-long-running-reports-timing-out.md)
-   [Power BI integration](..\analytics\power-bi-integration.md)
-   [Extending the list of electronic reporting functions](..\analytics\general-electronic-reporting-formulas-list-extension.md)
-   [Introduction to Advanced Reporting Solutions (Office Mix)](https://mix.office.com/watch/wdl1dquy2tve)
-   [Demo of Advanced Reporting Solutions (Office Mix)](https://mix.office.com/watch/1hkvtnc8sc7l6)

## Data entities and OData
-   [Data entities home page](..\data-entities\data-entities.md)
-   [OData](..\data-entities\odata.md)

## Workflow
-   [Workflow subsystem](..\migration-upgrade\workflow-subsystem.md)

## Testing support in Visual Studio
-   [Testing and validation](..\perf-test\testing-validation.md)
-   [Support for testing in Visual Studio](..\perf-test\testing-support.md)
-   [Developer topology deployment with continuous build and test automation](..\perf-test\continuous-build-test-automation.md)
-   [Task Recorder](..\user-interface\task-recorder.md)

## Office integration
-   [Office integration](..\office-integration\office-integration.md)

## Build workspaces
### Tutorials

-   [Modeling and using aggregate data](..\analytics\model-aggregate-data.md)
-   [Adding KPI’s to workspaces](..\analytics\add-bi-workspaces.md)
-   [Building navigation](..\user-interface\build-navigation.md)

### Concepts

-   [In-memory, real-time aggregate models replace SSAS cubes](..\migration-upgrade\in-memory-real-time-aggregate-models.md)
-   [Building operational workspaces](..\user-interface\build-workspaces.md)
-   [Tile and lit-caching for workspaces](..\user-interface\tile-list-caching-workspaces.md)
-   [Overview of aggregate data (Office Mix)](https://mix.office.com/watch/16yvvnw45kzhf)

## Mobile platform
-   [Dynamics 365 for Operations mobile platform](..\mobile-apps\mobile-platform.md)

## Global finance management
-   [Dimension entry control dialog support](..\financial\dimension-entry-control-dialog-support.md)
-   [Dimension entry control migration](..\financial\dimension-entry-control-migration.md)
-   [Dimension entry control uptake](..\financial\dimension-entry-control-uptake.md)
-   [Add dimensions to the Microsoft Excel template](..\financial\dimensions-overview.md)
-   [Create Open in Office experiences for Excel and Word](..\office-integration\office-integration-edit-excel.md)
-   [Add templates to open lines in Excel menu](..\user-interface\add-templates-open-lines-excel-menu.md)
-   [Segmented entry control dialog support](..\financial\segmented-entry-control-dialog-support.md)
-   [Segmented entry control metadata specification](..\financial\segmented-entry-control-metadata-specification.md)
-   [Segmented entry control - migration guidance](..\financial\segmented-entry-control-migration-guidance.md)
-   [Segmented Entry control migration walkthrough](..\financial\segmented-entry-control-conversion.md)
-   [Segmented entry control parm Specification](..\financial\segmented-entry-control-parm-method-specification.md)
-   [Creating exchange rate providers](..\financial\create-exchange-rate-providers.md)
-   [Financial dimension configuration for integrating applications](..\financial\financial-dimension-configuration-integration.md)
-   [Activating financial dimensions](..\financial\activate-financial-dimensions.md)
-   [Add the ability to look up values for financial dimensions in Microsoft Excel templates](..\financial\add-dimensions-excel-templates.md)

## Licensing
-   [ISV licensing](isv-licensing.md)

## Supply chain management
-   [Gantt development guide](..\user-interface\gantt-development-guide.md)


# See also

[Insider tips on development](https://community.dynamics.com/ax/b/newdynamicsax)

