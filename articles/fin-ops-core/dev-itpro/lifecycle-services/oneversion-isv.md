---
title: Delivering ISV solutions using One Version
description: Learn about how independent software vendors (ISVs) can use One Version to deliver their solutions, including overviews of servicing customers and compatibility.
author: FrankDahl
ms.author: fdahl
ms.topic: article
ms.date: 05/03/2022
ms.reviewer: twheeloc
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2019-04-12
ms.dyn365.ops.version: Platform update 24
---

# Delivering ISV solutions using One Version

[!include [banner](../includes/banner.md)]

Thanks to One Version, new updates are now automatically broadcast, downtime is minimal, and customers enjoy the benefits of staying current with recent features and fixes without having to go through expensive upgrades.

Feature management lets customers control when new features are applied. Therefore, as an independent software vendor (ISV) partner, you can innovate together with Microsoft to take advantage of new features without having to handle the waiting times that come with long release cycles. When all your customers run on current versions, you have fewer versions to maintain. You can focus instead on building quality into the solutions that you provide for your customers.

The process of servicing current versions is also more seamless and safer than it was in earlier versions. Previously, patching required that individual fixes be combined and merged into a customer environment.

Extensibility allows for deployment of side-by-side solutions that give customers more choices about how they configure their solutions.

In the One Version model, customer user acceptance testing (UAT) environments and production environments are updated several times a year. It's critical that updates not cause issues. However, Microsoft acknowledges that both technical issues and functional issues may arise when environments are updated.

+ Technical issues include breaking changes in application programming interfaces (APIs) that customizations in your solutions use.
+ Functional issues that customers experience can be caused by the untimely introduction of new features. Microsoft will put any new functionality that might affect existing processes under feature management. In this way, customers can control when new functionality is adopted. Therefore, they have time to validate, document, and train their users about the new features.
+ Functional issues might also be unintended changes that cause functional regressions.

Prevention of technical and functional issues is difficult and requires close coordination between Microsoft and you as an ISV partner. The Microsoft goal is that you will adopt practices that resemble Microsoft practices. This article explains how you and Microsoft can achieve this goal together. Over the next several months, Microsoft will release new practices and tools to help you. This article will be updated as the tools and practices evolve.

This article includes the following sections:

+ [Servicing customers](#servicing-customers)
+ [Compatibility](#compatibility)

    - [Runtime compatibility](#runtime-compatibility)
    - [Design-time compatibility](#design-time-compatibility)

+ [Developing new releases](#developing-new-releases)

    - [Designing for extensibility](#designing-for-extensibility)
    - [Data upgrade](#data-upgrade)
    - [Feature exposure](#feature-exposure)

+ [Branches and builds](#branches-and-builds)
+ [Testing](#testing)
+ [Deploying updates](#deploying-updates)
+ [ISV solutions as part of One Version automated deployment](#isv-solutions-as-part-of-one-version-automated-deployment)
+ [Should I release binaries or source code?](#should-i-release-binaries-or-source-code)

## Servicing customers

Dynamics 365 finance and operations apps run on Microsoft Azure. Therefore, it's a solution that runs as a service. Microsoft services companies 24/7, either proactively from alerts that report unusual behavior, or from support tickets that are submitted by customers or their partners. Microsoft has a range of tools to help support the services that are running. These tools include usage data that is collected from the services. To help safeguard customer data, Microsoft is also careful about who can access customer systems.

When Microsoft analyzes an issue, it might determine that the issue is related to your ISV solution. Microsoft reports this type of issue to you, so that you can follow up offline.

Companies can opt out of updates for two consecutive service updates before the next service update is applied to their environments. Therefore, at any time, Microsoft can expect that companies will be running one of the last three monthly updates.

When Microsoft resolves an issue that requires a code fix, it generally includes that code fix in the next monthly update. However, very critical issues that are reported, such as production outage, might require that a fix be provided for the version that customers are currently running.

Similar policies apply to your ISV solution, and you might also have to provide a code update. For your solution to be binary-compatible with all your customers, it must be built on the oldest platform release that you want to support. All new updates that Microsoft releases are intended to be binary backward-compatible. This compatibility gives you the option of maintaining only one servicing version of your solution that is based on the oldest of the three most recent updates. Therefore, you must maintain just one released solution. You can then use that solution to update all your customers, regardless of which of the three most recent updates they are running. As your customers adopt new Microsoft updates, you can rebase your maintained solution to a newer release to remain current with the three most recent updates.

This recommendation applies to servicing and maintaining your released solution. You will use a different approach to develop new releases of your solution. For more information, see the [Developing new releases](#developing-new-releases) section of this article.

## Compatibility

Microsoft diligently tries to guarantee compatibility with existing customizations. To achieve this goal, Microsoft uses strict practices in its engineering processes, together with tool and automation support that helps identify API contracts that are unintentionally broken. Telemetry lets Microsoft engineers determine customizations that reference or extend a Microsoft API.

Updates to finance and operations apps that are applied to customer environments are intended to be functionally compatible and binary-compatible with existing customizations. This compatibility covers not only APIs, but also functionality and the user experience. Customers must explicitly opt in to all new experiences.

Any deprecation or breaking change in binary or functional compatibility will be announced 12 months in advance. Therefore, you will have enough time to align your customizations with an alternative design. You must pay attention to the monthly updates to Microsoft documentation, and you must review the APIs that are marked as obsolete (deprecated) or internal. In this way, you will be able to manage changes in a timely manner.

The following sections define and describe the aspects of backward compatibility: runtime compatibility and design-time compatibility.

### Runtime compatibility

All new updates are intended to be runtime backward-compatible. This compatibility covers both binary compatibility and functional compatibility. Runtime compatibility means that customizations that exist in production and sandbox environments will continue to work after new updates are deployed in those environments. These updates include both service updates and quality updates.

Runtime compatibility also means that changes made by Microsoft to the platform will be backward-compatible with customizations that were compiled on an earlier platform.

Binary compatibility is backwards only. You can compile a customization on an older platform, and deploy it to a customer environment that has been updated to a later version. You cannot deploy code compiled on a later version than the one running on the environment you deploy to.

### Design-time compatibility

Design-time backward compatibility (that is, compile-time compatibility) means that developers can apply updates to their development environments and successfully compile their code without having to make any changes.

You must be aware of how APIs in your solution are used in your customers' implementations, and how you can use these APIs without causing breaking changes. As part of this effort, you must pay careful attention to what is changed and rely on engineering best practices. For examples of changes that you should avoid, see [Breaking changes](../extensibility/breaking-changes.md).

You should try to meet a bar that resembles the bar that Microsoft sets. In that way, both you and Microsoft can help avoid creating regressions.

All Microsoft updates are intended to be binary (runtime) compatible, and Microsoft also aims for design-time compatibility. However, there is one category of required changes that is **not** design time–compatible but remains binary-compatible. After an update is applied, new errors or warnings might occur when your code is compiled. Here are some examples of these changes:

- Microsoft makes an enumeration extensible.
- Microsoft marks an API as obsolete or internal.
- Microsoft introduces a new compiler error to help avoid unsafe coding practices.

All these changes might require work on your solution.

Design-time breaking changes that are binary-compatible don't require a 12-month deprecation notice.

## Developing new releases

Together, One Version and the fact that the finance and operations apps run as a service provides a great vehicle for collecting feedback. Feedback is useful, because it helps Microsoft decide which new features it should add to upcoming updates. Historically, the Microsoft approach has been to release major releases that include many new features. However, the new model encourages a different approach. Therefore, Microsoft has moved to a series of continuous updates that gradually build on the available capabilities of the system. In many cases, one update contains an initial small feature that Microsoft then enriches in later updates. In some cases, Microsoft must provide staging for new features, and must use feature exposure to hide the new features or control modifications to them.

We recommend that you follow a similar approach for your ISV solutions. You will benefit from quicker integration and extension of new standard features.

As the following illustration shows, the frequency of your new releases can be independent of Microsoft releases. You should consider adopting a strategy for source code branching, as described in the [Branches and builds](#branches-and-builds) section of this article.

![Branching strategy.](media/oneversion-isv-branch.png)

What is essential is the quality of every update that is released. Although testing helps guarantee quality, quality must also be built in during the design and implementation phases. In the One Version model, there are some new dimensions to consider, as described in the following sections.

### Designing for extensibility

To design your solution for extensibility, you must consider now only how you will customize by extending the standard application, but also how you will enable customization of your ISV solutions by your customers and partners.

Make sure that customizations are additive instead of intrusive, and follow the guidance on the [Extensibility home page](../extensibility/extensibility-home-page.md).

Don't be too creative about the way that you build your customization. Otherwise, you might extend an API that is questionable and increase the risk that later updates will break your solution. Instead, log an [extensibility request](../extensibility/extensibility-requests.md), and ask that Microsoft create a more explicit API that is more resilient to breakage.

Design solutions that are extensible. For inspiration, see [Write extensible code](../extensibility/writing-extensible-code.md).

Design for backward compatibility to avoid breaking customer implementations. A good strategy is to be explicit about what you offer for hooking and wrapping extension code. The way that you decorate your methods gives you lots of control over which methods you enable extensions for. For more information, see [Attributes that make methods extensible](../extensibility/extensibility-attributes.md).

### Data upgrade

The types of data upgrade jobs that existed in earlier versions are no longer supported. This change was made because Microsoft wants to provide minimum downtime while a production environment is updated.

Database synchronization is still run during upgrade, and it supports basic operations such as adding new tables, field, and indexes.

To prevent downtime, Microsoft is introducing new ways of driving data upgrade that are run asynchronously. For example, data upgrade will sometimes be triggered when a feature is turned on through a feature flag. This new approach for data upgrade differs significantly from earlier approaches and will become available in upcoming updates. Documentation resources will also be available.

### Feature exposure

In the One Version model, updates are managed by Microsoft and pushed to customer environments. Pushed updates should not require that customers adjust to functional changes, or that they train their users about new or changed features every month. Pushed updates also should not cause customers to delay updates to their environment.

Feature management is a new concept that puts customers in control of deciding when new or changed features are used. Customers can review, validate, and document new or changed features before they are adopted. They can also train users before new or changed processes are adopted, to reduce the impact on daily operations.

Feature management will be released in upcoming monthly updates.

You should consider using feature management with your ISV solution to let customers control when new features are adopted.

## Branches and builds

As an ISV, you should plan on a minimum of two source code branches: a servicing branch and a development branch.

### Servicing branch

The servicing branch is used to produce bug fixes for your ISV solution. As the ISV, you specify the frequency of releases from the branch and distribution of the releases. The expectation is that these releases from the servicing branch will be binary cumulative releases.

The base Microsoft version that you use to build your ISV solution should match the oldest version that customers use with the solution. In the One Version model, that version starts with version 8.1 and is a maximum of three months old.

### Development branch

The development branch is used to develop new capabilities for the ISV solution. As the ISV, you determine the frequency of releases from the development branch. You don't have to synchronize your releases with the monthly Microsoft releases. The best approach might be to decouple your release schedule from the Microsoft release schedule and deliver releases less often. A quarterly or biannual cadence is a good starting point.

The base Microsoft version in the development branch should be either the latest released version that is available or the released version that you plan to use for servicing when your new release goes out. The goals are that you innovate together with Microsoft by staying as current as is feasible, and that your development model allows for uptake of recent feature work.

## Testing

Microsoft has several checks and balances in its development process to help guarantee functional and binary compatibility. ISV solutions must be validated with each Microsoft release to help guarantee this compatibility. The expectation is that you will do this validation during the Preview phase of each release.

It's very important that you provide quick turnaround for feedback, so that you will have time to fix any issues before the monthly updates are deployed in customer environments.

Test automation is important for quick validation of new updates. Microsoft plans to release the test framework and libraries to support you as you build your test automation.

Microsoft has an extensive suite of tests that support our validation. The expectation is that you, as an ISV, will create your own suites of automated tests.

In addition to the SysTest automation framework that is aimed at developers, the [Regression Suite Automation Tool (RSAT)](using-task-guides-and-bpm-to-create-user-acceptance-tests.md) enables automation of business processes without requiring that code be written. Functional users can use the RSAT to record their critical tests and automate part of their UAT. You can also use the RSAT as you start to build your test automation.

Recently, Microsoft released the [Acceptance test library resources](../perf-test/acceptance-test-library.md) and accompanying libraries. This framework is aimed at developers and lets them build tests that are more comprehensive than unit tests. The libraries that accompany the framework help make it a seamless way to build suites of tests.

### Currently released products – Testing binary and functional compatibility

The currently released product that is maintained in the servicing branch should first be tested for binary and functional compatibility. Your suite of automated developer tests, automated functional tests, and manual tests for your ISV solution should be run on an environment that has the new version from Microsoft and your existing ISV solution. Because this test run is testing for binary and functional compatibility, the ISV solution should **not** be recompiled.

If the testing is successful, this step will validate that a customer installation of the current version of your ISV solution won't have to be updated when Microsoft broadcasts the new release to the customer.

If the testing isn't successful, you, as the ISV, must immediately notify Microsoft through the [Preview communication process](../../fin-ops/get-started/one-version.md#how-can-i-get-early-access-to-non-released-platform-updates). This process uses Yammer and an issue notification process. The issue will require either a fix from Microsoft or a fix in your ISV solution. A fix in your solution might, in turn, require that customers be updated from the servicing branch. In both cases, Microsoft must know about the issue, so that it can become more proactive in its processes for future releases.

### Currently released products – Testing design-time compatibility

Next, the currently released product that is maintained in the servicing branch should be tested for design-time compatibility. To do this testing, you should compile the solution against a deployment of the new Microsoft release. Although the goal of Microsoft is to minimize design-time compatibility issues, they might occur in some situations. One example is when Microsoft makes an enumeration extensible, and the solution uses it in a manner that assumes an underlying integer representation (for example, it uses the enumeration value in a logical comparison or mathematical function). Although the code will continue to work in a customer deployment because the underlying values are maintained, a compiler error is generated and addressed in future releases. Another example of a design-time compatibility issue is when Microsoft introduces a new compiler error to protect against unsafe coding patterns. To learn about more categories of design-time compatibility issues, see [Breaking changes](../extensibility/breaking-changes.md).

You should run your suite of automated developer tests, automated functional tests, and manual tests on an environment that has the new version from Microsoft and your compiled ISV solution.

If the testing is successful, this step will validate that your ISV solution won't have to be updated even if source code is supplied to the customer and the customer recompiles the ISV solution.

If the testing isn't successful, and the issue isn't one of the categories that are described in [Breaking changes](../extensibility/breaking-changes.md), you, as the ISV, must immediately notify Microsoft through the [Preview communication process](../../fin-ops/get-started/one-version.md#how-can-i-get-early-access-to-non-released-platform-updates). This process uses Yammer and an issue notification process. The issue will require either a fix from Microsoft or a fix in your ISV solution. A fix in your solution might, in turn, require that customers be updated from the servicing branch. In both cases, Microsoft must know about the issue, so that it can become more proactive in its processes for future releases.

### Currently released products – Updating the base build

As Microsoft updates your customers to new releases, you should periodically update the base build, so that it matches the oldest version that is used by customers who run your ISV solution.

### Solutions that are in development

You validate your new solution development on either the latest released version or the released version that you plan for to use for servicing when your new release goes out. However, in both cases, consider doing validation on the most current version. This validation will help with early discovery of issues or uptake work that you must do.

If an unexpected break occurs, then you, as the ISV, must immediately notify Microsoft through the [Preview communication process](../../fin-ops/get-started/one-version.md#how-can-i-get-early-access-to-non-released-platform-updates). This process uses Yammer and an issue notification process.

## Deploying updates

For Microsoft standard platform and application updates, One Version servicing includes a process for automated updates of customer environments. However, this automation isn't currently available for ISV solutions. For more information, see [ISV's as part of One Version service updates](#isv-solutions-as-part-of-one-version-automated-deployment).

ISV solutions are manually updated, and you control your release cadence. The binary backward compatibility allows for safe updates of the standard platform and application.

The update process includes database synchronization (for example, the addition of new fields and indexes).

## ISV solutions as part of One Version automated deployment

Although Microsoft doesn't currently plan to release ISV solutions as part of the One Version automated deployment process, this option might become available at some point. However, Microsoft must first align engineering processes to make this option feasible.

Here are some areas where alignment will be required:

+ **Feature management** – The user must be able to control when a new feature is turned on.
+ **Backward compatibility and compliance** – Compliance with API customization usage is required.
+ **Feature deprecation** – Advanced notice about deprecation of features or APIs must be provided.
+ **Test automation suite** 
+ **Testing during the preview phase**
+ **ISV solution sign-off and upload** 
+ **Automated deployment scripts**
+ **Zero downtime** – Deployment of updates must be instantaneous.
+ **Data migration without downtime**
+ **Support for on-call duty, for servicing of critical production issues**

## Should I release binaries or source code?

Binary compatibility is supported, provided that you don't recompile. We recommend that your ISV solution not be compiled in customer environments. Instead, you should deploy precompiled binaries that you've prepared and validated. Your solution binaries can then be created from your servicing branch, based on an earlier version, when this approach is practical.

If an implementation partner or customer compiles your solution in an updated environment, new warnings and errors might occur, as was mentioned in the [Design-time compatibility](#design-time-compatibility) section of this article. Therefore, we recommend that implementation partners not compile your solution. However, this recommendation doesn't mean that you shouldn't share your source code to help support debugging, for example. You should just consider taking steps to avoid compilation of your code, so that implementation partners aren't exposed to design-time issues.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

