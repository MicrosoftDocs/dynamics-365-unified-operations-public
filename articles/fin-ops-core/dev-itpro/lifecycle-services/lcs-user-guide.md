---
# required metadata

title: Lifecycle Services (LCS) user guide
description: This topic provides information about the tools that are available in Lifecycle Services (LCS) and when to use them as you move through the phases of your work in LCS.
author: angelmarshall
manager: AnnBe
ms.date: 07/02/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 6034
ms.assetid: 3bebecd6-a72e-48b2-9eec-8c19eafe5dad
ms.search.region: Global
# ms.search.industry: 
ms.author: tsmarsha
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Lifecycle Services (LCS) user guide

[!include [banner](../includes/banner.md)]

Microsoft Dynamics Lifecycle Services (LCS) provides regularly updated services. The goal of LCS is to deliver the right information, at the right time, to the right people, and to help ensure repeatable, predictable success with each roll-out of an implementation, update, or upgrade. LCS is available to customers and partners as part of their support plans. If you're a Microsoft Dynamics AX 2012 customer, you can sign in by using your CustomerSource or PartnerSource credentials. If you're a customer of the newest version of the Dynamics 365 Finance and Operations apps, you can sign in by using your Microsoft Azure Active Directory (Azure AD) credentials. [Go to LCS](https://lcs.dynamics.com/Logon/Index).

## Tools that are provided in LCS
The following table lists the tools that are provided in LCS and describes the phases that each tool applies to.

| Tool                                     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Projects](ax-2012/projects-lcs.md)                                 | Projects are the key organizer for your experience in LCS. Projects let you invite your partners to collaborate with you, and they also let you track progress.                                                                                                                                                                                                                                                                                                                                                   |
| [Methodologies](ax-2012/methodologies-lcs.md)                            | Methodologies provide a tool that you can use to ensure more repeatable, predictable implementation projects. You can use one of our methodologies or create your own. By using a methodology, you can easily track and report on your progress.                                                                                                                                                                                                                                                                  |
| [Business process modeler](ax-2012/business-process-modeler-lcs.md)                 | Business process modeler lets you create, view, and modify standard process flows. By using Business process modeler, you can achieve the following goals: standardize process flows; align your business processes with industry-standard processes, as described by the American Productivity & Quality Center (APQC); identify fit and gaps between user requirements and the default functionality that Microsoft Dynamics products provides.                                                                 |
| [Cloud-hosted environments](ax-2012/cloud-hosted-environments-lcs.md)                | Cloud-hosted environments is a tool that you can use to deploy Microsoft Dynamics environments on Azure. When you use Cloud-hosted environments, you must select the type of environment to deploy, such as a demo, developer/test, or production environment. Based on your selection, the Cloud-hosted environments tool provisions the appropriate number of virtual machines (VMs) in Azure. These VMs have Microsoft Dynamics components (and all their prerequisites) already installed on them.                                       |
| [Cloud-powered support](cloud-powered-support-lcs.md)                    | Cloud-powered support helps you manage support incidents. It lets you create a VM in Azure that has the same hotfixes installed as your local environment. You can reproduce and record an incident on the VM, and then submit the incident to our support team. Support follows up by investigating and, if possible, testing a fix on the VM, and then sends the fix back to you for verification.                                                                                                              |
| [Configuration and data manager (preview)](configuration-manager-lcs.md) | Configuration and data manager (preview) lets you copy a configuration from one instance to another. You can copy from and to environments that meet the following criteria: they are managed as part of an LCS project; they run the Data Import/Export Framework.                                                                                                                                                                                                                                               |
| [Customization analysis](ax-2012/customization-analysis-lcs.md)                   | Customization analysis validates model files against best practices and provides a report of potential areas for improvement.                                                                                                                                                                                                                                             |
| [Issue search](issue-search-lcs.md)                             | Issue search helps you find existing solutions and workarounds for known issues in Microsoft Dynamics products. You can see which issues have been fixed, which issues remain open, and which issues have been resolved as "won't fix."                                            |
| [Asset library](asset-library.md)                             | The Asset library is a storage location for the various assets that are associated with a tenant in LCS.                                                                                                                                                                      |
| [Get updates](../migration-upgrade/download-hotfix-lcs.md)                            | Get updates is a tool that customers to access the updates that are available for their environments.                            |
| [Environment monitoring](monitoring-diagnostics.md)                            | Environment monitoring is a set of tools that helps you monitor, diagnose, and analyze the health of the environments that you manage.                                               |
| [Translation service](translation-service-overview.md)                      | The Microsoft Dynamics 365 Translation Service (DTS) is hosted in LCS. It's designed to enhance the experience for partners and independent software vendors (ISVs) when they translate their solutions or add a new language for the supported Dynamics products.                                                                  |
| [Regulatory updates](../lcs-solutions/regulatory-watch-communication.md)                      | Regulatory updates is a tool that lets customers, partners, and ISV solution providers stay up to date about regulatory updates by setting up alerts through LCS.                                        |
| [System diagnostics](ax-2012/system-diagnostics-lcs.md)                       | System diagnostics is a tool that helps administrators monitor AX 2012 environments.                                                                                                                                                                                                                                                                                      |
| [Updates](ax-2012/update-2012-r3-lcs.md)                                  | The **Updates** page hosts the details of updates that are available for an AX 2012 environment. It also provides access to groups of updates that can be used for slipstream installations.                                                                                                                                                                                                                                                                                                                               |
| [Upgrade analysis](ax-2012/upgrade-analysis-lcs.md)                         | Upgrade analysis helps you plan your upgrade to the latest version by analyzing code artifacts from Microsoft Dynamics AX 4.0, Microsoft Dynamics AX 2009, or AX 2012.                                                                                                                                                                                                                                                                                                    |
| [Usage profiler](ax-2012/usage-profiler-lcs.md)                           | Usage profiler is a data-gathering tool that helps you describe your projected or current usage of an. The usage profile that is generated can be used for various purposes, such as hardware sizing and support.                                                                                                                                                                                                                                                                                                 |
| [Downloadable tools](ax-2012/lcs-downloadable-tools-formerly-informationsource.md)                       | The **Downloadable tools** page provides a set of tools that were previously hosted on Microsoft Dynamics InformationSource.                                      |
| [License sizing estimator](ax-2012/license-sizing-estimator-lcs.md)                 | License sizing estimator helps you estimate the number of licenses that are required. It provides a shared workspace that lets you model default and customized roles, and then automatically calculate the required client access licenses (CALs).

Additional resources
--------

The LCS team is also blogging on the [Lifecycle Services Engineering blog](https://cloudblogs.microsoft.com/dynamics365/?s=lcs). Subscribe to our RSS feed to keep up with our posts and announcements.

[Access Lifecycle Services](https://lcs.dynamics.com/)
