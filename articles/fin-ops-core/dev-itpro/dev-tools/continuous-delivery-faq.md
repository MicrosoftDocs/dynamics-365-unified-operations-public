---
title: Development and continuous delivery FAQ
description: Access answers to questions that are frequently asked by ISVs and partners about development, testing, delivery, and lifecycle management.
author: laneswenka
ms.author: laswenka
ms.topic: article
ms.date: 01/21/2020
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 2
---

# Development and continuous delivery FAQ

[!include [banner](../includes/banner.md)]

This article summarizes answers to questions that are frequently asked by ISVs and partners, especially regarding guidelines about development, testing, delivery, and lifecycle management.

## Customization

### Do I customize (overlayer) or use extensions?

Extensibility is the only customization framework in Finance, Supply Chain, and Commerce. Overlayering isn't supported.

Dynamics 365 Finance, Supply Chain, and Commerce are extensively customized by partners, value added resellers (VARs), and even some customers. The ability to customize the product is a strength that has historically been supported through overlayering of the application code. The move to the cloud, together with more agile servicing and frequent updates, requires a less intrusive customization model, so that updates are less likely to affect custom solutions. This new model is called *extensibility* and has replaced customization through overlayering.

For more information, see [Extensibility home page](../extensibility/extensibility-home-page.md) and the [Develop and customize home page](developer-home-page.md).

### How do I prevent my models from being customized by customers or other partners?

You can block customizations of your model as described in [Turn off model customization and deprecate functionality](lock-models.md), or you can distribute deployable packages to your customers instead of distributing model files. See the section titled "How do I distribute my application to customers" later in this article.

### How can I define the scope of my models? How many models or packages should I create?

Designing models and model elements is no different than designing other types of software libraries. You should apply [SOLID (object-oriented design)](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)) design principles. In addition, we recommend the following tips that are specific to the platform:

- If there are components in your solution that you want to ship and service more frequent than the rest, they are good candidates to place in a separate model and package.
- It is common practice to start with two packages (each with one model) at the initial stage of an implementation, one foundation package that contains extensions to the Microsoft platform packages and one application package that contains extensions to the Microsoft application packages. More models can be introduced on an as-needed basis.
- Existing packages can be subdivided into smaller packages when necessary. If your implementation is already live using one of your packages, avoid renaming a package, to help simplify lifecycle management.

## Continuous delivery

### Do I need build environments?

Yes, you should take advantage of the build and test automation tools provided in the build environments. You can deploy build environments from your Lifecycle Services (LCS) project. Creating daily builds and daily regression tests are key tools to enable the continuous delivery and maintain the quality of your application. Refer to [Deploy and use an environment that supports continuous build and test automation](../perf-test/continuous-build-test-automation.md) for more details.

Do not use build environments for development activities. Do not keep a backup of your test database on these build VMs. Build VMs are designed to reset themselves to a known state with every build and whenever they are updated with a Microsoft binary or platform updates from LCS.
For example, if you apply a binary hotfix or platform update to a build VM, the VM prepares itself for the next build as part of the update. This will remove your customizations and also trigger a database synchronization.

### What strategy do I use for test automation?

For test automation, concentrate on unit tests (use the SysTest framework) that are data independent or create their own data. Use a smaller number of functional scenario tests (based on Task Recorder) that rely on test data to execute. Scenario tests are more expensive to maintain. Unit tests can then be executed on any development environment easily and quickly. Review the [Test Automation Pyramid](/archive/blogs/dave_froslie/test-automation-pyramid) blog article and refer to [Automated testing guidance](/archive/blogs/axdevalm/automated-testing-guidance-for-ax-7).

![media/testautomationpyramid1.png.](media/testautomationpyramid1.png) Some key concepts to keep in mind:

- Write tests that run independently and do not assume any kind of ordering.
- Task recorder tests should be limited to functional scenarios tests.
- Write scenario tests after scenarios are complete and after completing unit tests.
- Create test helper classes when possible, so others on your team can leverage that as well.
- SysTest framework supports role-based testing, leverage this feature.

### How can I be more agile in my development?

Deliver incremental features every sprint (2 weeks, preferred) or cycle (1 month). Maintain shippable quality of your application at the end of each sprint. Use Azure DevOps for work item tracking and always prioritize bugs over new features. A large bug backlog will quickly become a burden on your efficient delivery of new features and on the quality of your application.

### How do I manage test data?

Create and manage your test database as follows:

- Start on a clean environment.
- Create all base data as required. Base data will serve as the starting point for all the tests.
- Take a backup (.bak) of your AxDB database.
- Share this backup with developers.

On a build environment, copy this backup over to the I:\\DynamicsBackupDatabases (on some environment it may be a different drive than i:). This database will be restored at the beginning of every build. This step is executed as part of the first step of the build definition called **Prepare for build**.

![media/prepareforbuild.png.](media/prepareforbuild.png)

### How do I distribute my application to customers?

There are two artifacts you can use to distribute your application to your customers or partners: model files or deployable packages. Model files are design time artifacts that contain source code. Use model files if your customer is integrating your application with other third-party models or when you want to allow customization of your models. For more information, see [Export and import models](models-export-import.md). Model files are the most common methods for ISVs to distribute solutions. Deployable packages are final applications. Use deployable packages with customers that will not be customizing or integrating your application with other third-party models. If you use deployable packages, your customer can only use or extend your application. They will not see or have access to your source code. To create a deployable package use the Visual Studio tools (**Dynamics 365**&gt;  **Deploy** &gt; **Create Deployment package**) or use a build environment. Build environments generate a deployable package with every successful build.

## Development topologies

### Should I develop on premises or in the cloud?

There are two modes of development: Cloud VMs and on-premises VMs available via a downloadable VHD. Use a combination of on premise VMs and cloud VMs for development.

- On premise dev VMs are cost effective if you already have the hardware, IT infrastructure, and Windows server licenses to support it.
- Use cloud VMs to scale out when projects require additional resources for a limited period of time. It is more cost effective than planning for worst-case capacity on premise.
- Connect all VMs (on premise and cloud VMs) to Azure DevOps for version control.

Use cloud VMs for build, functional testing, and demos. If you are running on your own Microsoft Azure subscription, turn them off when not in use.

### Should I use a customer's dev environment?

If you are a partner, use your own VMs for development of your own intellectual property (IP), this is code and configuration data packages that are reusable across different customer implementations. For customer-specific implementations, you can use the customer's dev VM. All customer subscriptions come with at least one development VM. Customers can pay for add-on dev VMs or run local dev VMs.

### What are the benefits of MSDN subscriptions with respect to development?

The following is a summary of a Visual Studio (VS) with MSDN subscriptions benefits:

- Includes a Microsoft Azure subscription with a $50 monthly credit for Visual Studio Professional with MSDN and $150 for VS Enterprise with MSDN.
- Subscriptions come with lower dev/test rate, you will pay the Linux rates instead of the Windows rates.
- For more details, visit <https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/>

As a Microsoft partner, acquire Microsoft core competencies to earn free VS Enterprise with MSDN subscriptions. For example, an application development competency for a gold partner will earn 25 free MSDN Enterprise licenses in addition to the 10 licenses that come with the core benefits. For more details, visit [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/). These benefits make cloud development very economical, for example:

- D12v2 VM list price = $470/month (4 core, 28 Gigs)
- D12v2 VM price if running on MSDN Azure subscription or any other dev/test subscription = $276/month
- Turn off 12 hours per day: 276/2 =&gt; $138/month
- Monthly credit (VS Professional with MSDN) =&gt; 138 - 50 = **$88/month**
- Monthly credit (VS Enterprise with MSDN) =&gt; 138 – 150 = **Free**

Here is another example:

- D13v2 machine list price = $843/month (8 core, 56 Gigs)
- D13v2 machine price if running on MSDN Azure subscription = $551/month
- Turn off 12 hours per day: 551/2 = $275.5/month
- Monthly credit (VS Professional with MSDN): 275.5 - 50 = **$225.5/month**
- Monthly credit (VS Enterprise with MSDN) =&gt; 275.5 – 150 = **$125.5/month**

Add an average of $15 monthly for storage (non premium) per VM.

### Can more than one developer develop concurrently on the same VM?

This is not supported. However, you can provision more than one developer account on the same VM, they just cannot develop concurrently. For details, see [Create new users on development machines](access-instances.md).

If you are a Microsoft partner developing code for more than one customer, we recommend having at least one development VM per customer. You will need one addittional VM for every additional developer working on a customer project. Development VMs can be thought of as disposable assets as long as your source code is checked into version control (Azure DevOps) and you keep a backup of test databases.

## Customer implementation LCS projects

### How many sandbox environments do I need within an LCS customer implementation project?

A customer subscription comes with two environments by default: a tier-2 sandbox environment and a production environment. You can use the tier-2 sandbox environment as a configuration and a UAT environment before the application goes live in production. After configuring the sandbox with the code and data that you need to go live (also known as your *gold configuration*), you can run your validation on the same environment. When your validation passes, restore your sandbox database to the point in time of its gold configuration. You can then deploy your code to production and copy the sandbox database to your production environment. You can also choose to have more than one sandbox environment that is tier-2 or higher, especially after your application is live. One sandbox can be used as a pre-production UAT environment, and the other sandboxes can be used for configuration, upgrade or other scenarios. You can purchase additional tier-2 or higher sandboxes.

The following servicing requests and tools are supported by LCS, which may help you decide whether one tier-2 sandbox is sufficient for your implementation.

1. Restore a sandbox database to a point in time.
2. Copy a sandbox database to a production environment (only allowed before the application is live in production).
3. Apply configuration data packages on a sandbox environment.
4. Apply configuration data packages on a production environment.
5. Refresh a sandbox database from production. Copy the production environment's database to a tier-2 sandbox environment. This is typical after the application is live and you want to debug an issue or validate upcoming updates.
6. Apply updates (Hotfixes, customizations) to a sandbox environments for validation before applying them to a production environment.

For more information about planning an environment, see [Environment planning](../../fin-ops/imp-lifecycle/environment-planning.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
