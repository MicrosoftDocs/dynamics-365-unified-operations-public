---
# required metadata

title: Developer home page
description: This topic provides links to topics about development with Microsoft Dynamics 365 for Operations.
author: annbe
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
ms.assetid: d72eb555-379f-4559-ba4e-bae41148a326
ms.search.region: Global
# ms.search.industry: 
ms.author: annbe
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

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
[Architecture changes](architecture-changes.md)

## Getting started
[Get an evaluation copy](get-evaluation-copy.md) [LCS101 – Sign up for a Preview Subscription](sign-up-preview-subscription.md) [Access Development Instances](access-instances.md) [Development System Requirements](development-system-requirements.md) [Deprecated Features](deprecated-features.md) [Deprecated API’s](deprecated-apis.md) [Feedback and Support (Office Mix)](https://mix.office.com/watch/92azzna59jj6) [Rename and reboot machines for Visual Studio Online (Office Mix)](vso-machine-renaming.md) [Configuring your Developer VM (Office Mix)](configure-developer-vm.md) [Introduction to Visual Studio Online (Video)](http://channel9.msdn.com/Events/Build/2014/2-575)

## Fleet Management
[Fleet Management sample](introduction-fleet-management-sample.md) [INT101: Introduction to Fleet Management](fleet-management-sample.md)

## Development tools
### Tutorials

[DEV101: Introduction to Visual Studio Development](introduction-visual-studio.md) [DEV102: Create a Simple Data Model](create-data-model-elements.md) [DEV103: Building and debugging a project](build-debug-project.md) [DEV105: Version control, metadata search, navigation, and other features](development-tools.md)

### Concepts

[Development Tools](development-tools.md) [Introduction to the Development Environment (Office Mix)](https://mix.office.com/watch/1tz7194y62m3s) [Enable a new user account to develop on a development VM](enable-development-machine.md) [Application Explorer](application-explorer.md) [Projects](projects.md) [Element designers](element-designers.md) [Element usage](element-usage.md) [Models](models.md) [Build operations](build-operations.md) [Visual Studio Code Editor](code-editor.md) [Developer Tools Add-ins](developer-tools-add-ins.md) [Distribution of Models: How to Export and Import a Model](models-export-import.md) [Configuring Your Developer VM](configure-developer-vm.md) [Metadata Search in Visual Studio](metadata-search-visual-studio.md) [Learn about Packages, Models and Visual Studio (Office Mix)](https://mix.office.com/watch/ies6lyit6773) [Development Tools Performance Tips (Office Mix)](https://mix.office.com/watch/rnp6ng9wu8kx) [Resolve conflicts using Visual Studio](https://mix.office.com/watch/1rl75ei2cs6d7)

## X++ programming language
### Tutorials

[DEV104: New X++ and Debugger Features](new-x-debugger-features.md) [Dev106: C\# and X++ Interoperability and LINQ](write-business-logic.md)

### Concepts

[Programming language support](programming-language-support.md) [Debugging X++ code](debug-xpp.md) [LINQ Provider for use in C\#](linq-provider-c.md) [Authoring best practice rules](author-best-practice-rules.md)

### Reference

X++ Language Reference

## Customizing with extensions and overlayering
[DEV107: Customize model elements using extensions](customize-model-elements-extensions.md) [Customize: Extensions and Overlayering](customization-overlayering-extensions.md) [Class extensions](class-extensions.md) [Customize by Overlayering Metadata source code (Office Mix)](https://mix.office.com/watch/1ol6ov90jrd4w)

## Code migration
### Migrate your code

To migrate your code to Dynamics 365 for Operations, use the "Migrate and Create Dynamics 365 for Operations Solutions" methodology in Lifecycle Services.

### Key concepts

The following links (also included in the methodology) describe key concepts and steps in the migration process. The links are listed here in the order that we recommend you read them. [Overview: Prepare to migrate to Microsoft Dynamics 365 for Operations](prepare-migration.md) [Migrate from AX 2012 to Dynamics 365 for Operations (Office Mix)](https://mix.office.com/watch/4gsvk592c685) [Migrate between versions (Office Mix)](https://mix.office.com/watch/os2wff38zi6f) [Configure your VSTS mapping after a code upgrade](configure-vso-solution.md) [Configure version control with VSTS (Office Mix)](https://mix.office.com/watch/1ftubtqzp3xxl) [Resolve conflicts using Visual Studio (Office Mix)](https://mix.office.com/watch/1rl75ei2cs6d7) [Understanding the Model split](model-split.md) [Deprecated APIs](deprecated-apis.md) [Deprecated Features](deprecated-features.md) [Development tools performance tips](https://mix.office.com/watch/rnp6ng9wu8kx) [Configuring your developer VM](configure-developer-vm.md)

### Additional concepts

[Delegates for migration](delegates-migration.md) [How to import a SQL Server Analysis Services Project into the AOT](https://technet.microsoft.com/en-us/library/dn754850.aspx) [Database synchronization](database-synchronization.md) [Understand the Migration Task List (Office Mix)](https://mix.office.com/watch/kcek55rc5cau) [Generating the form patterns report (Office Mix)](https://mix.office.com/watch/jqzesi1uuosz)

## Moving packages between environments
[Create and Apply a Deployable Package](create-apply-deployable-package.md)

## Performance
[PERF101: Take a trace with the Trace Parser and analyze it](trace-trace-tutorial.md) [PERF103: Introduction to the PerfSDK and multiuser testing with Visual Studio Online](perfsdk-tutorial.md) [Using the desktop version of trace parser to diagnose problems and analyze performance issues](trace-parser.md) [Performance timer](performance-timer.md) [Expanding Data with the Data Expansion tool (Office Mix)](https://mix.office.com/watch/11cet1u4nmn64) [Analyzing Performance Issues with Trace Parser (Office Mix)](https://mix.office.com/watch/17d76cll0npyw) [The performance timer and other tools (Office Mix)](https://mix.office.com/watch/ij5cqidra5q3) [Using Task Recorder to create a single user performance test (Office Mix)](https://mix.office.com/watch/qtdlasy2rcf3) [The Performance Timer and other tools (Office Mix)](https://mix.office.com/watch/ij5cqidra5q3) [Analyzing Performance Issues with Trace Parser (Office Mix)](https://mix.office.com/watch/17d76cll0npyw)

## User interface concepts
The client is an HTML web client that runs in all major browsers. For information about developing and customizing the user interface, see the [User interface development home page](user-interface-development-home-page.md).

## Analytics
### Tutorials

[BIR104: How to create a PowerBI reporting](create-powerbi-report-data.md) [BIR105: Create a Power BI report and dashboard](create-powerbi-report-dashboard.md)

### Concepts

[Analytics](analytics.md) [PowerBI integration](power-bi-integration.md) [Configuring Power BI integration for workspaces](configure-power-bi-integration.md)

## Reporting services
[BIR103: Creating NextGen Reporting Solutions](create-nextgen-reporting-solutions.md) [Document Reporting Services overview](document-reporting-services.md) [Tips to Help Prevent Long-running Reports from Timing Out](prevent-long-running-reports-timing-out.md) [Power BI Integration](power-bi-integration.md) [Extending the list of electronic reporting functions](general-electronic-reporting-formulas-list-extension.md) [Introduction to Advanced Reporting Solutions (Office Mix)](https://mix.office.com/watch/wdl1dquy2tve) [Demo of Advanced Reporting Solutions (Office Mix)](https://mix.office.com/watch/1hkvtnc8sc7l6)

## Data entities and OData
### Tutorials

[DM101: Building and Consuming Data Entities](build-consuming-data-entities.md) [DM102: Developing an entity and using it for data migration](develop-entity-for-data-migration.md)

### Concepts

[Data entities home page](data-entities-home-page.md) [OData](odata.md) [Data Entities](data-entities.md) [Introduction to Data Entity (Office Mix)](https://mix.office.com/watch/1brkpjvhf851m) [Building Basic Data Entity (Office Mix)](https://mix.office.com/watch/i53efq3ddtjy) [Introduction to OData (Office Mix)](https://mix.office.com/watch/i53efq3ddtjy) [Introduction to Import/Export and Integration (Office Mix)](https://mix.office.com/watch/1qplbdkxu5u4d) [JSON Based Endpout for Custom Services (Office Mix)](https://mix.office.com/watch/12e4fejbgj429)

## Workflow
[Workflow subsystem](workflow-subsystem.md)

## Testing support in Visual Studio
[TST101: Testing and Validations](testing-validation.md) [Support for testing in Visual Studio](testing-support.md) [Developer topology deployment with continuous build and test automation](continuous-build-test-automation.md) [Task Recorder](task-recorder.md)

## Office integration
[Office Integration](office-integration.md) [Office Integration lab and walkthroughs](office-integration-tutorial.md) [Create Open in Excel experiences](office-integration-edit-excel.md) [Office integration troubleshooting](office-integration-troubleshooting.md) [Office Integration – Overview (Office Mix)](https://mix.office.com/watch/17wcym7cmc6ui) [Office Integration – Static Export to Excel (Office Mix)](https://mix.office.com/watch/jkyxad5xv6n2) [Office Integration – Open in Excel (Office Mix)](https://mix.office.com/watch/1pf13dlhilys8) [Office Integration – Document Management (Office Mix)](https://mix.office.com/watch/1gcybbejqv87s)

## Servicing environments
[Download Hotfixes from Lifecycle Services](download-hotfix-lcs.md) [Install a Binary Hotfix or Install a Deployable Package](apply-deployable-package-system.md) [Install an Application Metadata Hotfix](install-metadata-hotfix-package.md) [Install retail hotfixes](install-retail-hotfix.md) [Installing a Financial Reporting Binary hotfix](install-financial-reporting-binary-hotfix.md) [Patching the reporting service](patch-reporting-service-environment.md) [Updating the Visual Studio development tools](update-development-tools.md)

## Building workspaces
### Tutorials

[BIR100: Modeling and using aggregate data](model-aggregate-data.md) [BIR101: Adding KPI’s to Workspaces](add-bi-workspaces.md) [CLI104: Building Navigation](build-navigation.md)

### Concepts

[In-memory, real-time aggregate models replace SSAS cubes](in-memory-real-time-aggregate-models.md) [Building operational workspaces](build-workspaces.md) [Tile and List Caching for Workspaces](tile-list-caching-workspaces.md) [Overiew of Aggregate Data (Office Mix)](https://mix.office.com/watch/16yvvnw45kzhf)

## Mobile platform
[Dynamics 365 for Operations mobile platform](mobile-platform.md)

## Global finance management
[Dimension entry control dialog support](dimension-entry-control-dialog-support.md) [Dimension entry control migration](dimension-entry-control-migration.md) [Dimension entry control uptake](dimension-entry-control-uptake.md) [Add dimensions to the Microsoft Excel template](dimensions-overview.md) [Create Open in Office experiences for Excel and Word](office-integration-edit-excel.md) [Add templates to Open lines in Excel menu](add-templates-open-lines-excel-menu.md) [Segmented entry control dialog support](segmented-entry-control-dialog-support.md) [Segmented entry control Metadata Specification](segmented-entry-control-metadata-specification.md) [Segmented entry control - Migration guidance](segmented-entry-control-migration-guidance.md) [Segmented Entry control migration walkthrough](segmented-entry-control-conversion.md) [Segmented entry control Parm Specification](segmented-entry-control-parm-method-specification.md) [Creating exchange rate providers](create-exchange-rate-providers.md) [Financial dimension configuration for integrating applications](financial-dimension-configuration-integration.md) [Activating financial dimensions](activate-financial-dimensions.md) [Add the ability to look up values for financial dimensions in Microsoft Excel templates](add-dimensions-excel-templates.md)

## Licensing
[ISV Licensing](isv-licensing.md)

## Supply chain management
[Gantt Development Guide](gantt-development-guide.md)

See also
--------

[Insider tips on development](https://community.dynamics.com/ax/b/newdynamicsax)

