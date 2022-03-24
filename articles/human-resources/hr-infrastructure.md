---
# required metadata

title: Dynamics 365 Human Resources infrastructure merge - Release 10.0.25 update
description: This topic provides information about Microsoft Dynamics 365 Human Resources release 10.0.25, which brings the first wave of capabilities in the infrastructure merge.
author: twheeloc
ms.date: 01/19/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-27
ms.dyn365.ops.version: Human Resources

---

# Dynamics 365 Human Resources infrastructure merge - Release 10.0.25 update

The 10.0.25 release brings the first wave of capabilities in the infrastructure merge. During the infrastructure merge, Microsoft Dynamics 365 Human Resources will be merged with the Finance and Operations infrastructure. However, it will continue to be licensed as an independent application, like Dynamics 365 Finance and Dynamics 365 Supply Chain Management. For more information about the infrastructure merge, see [Dynamics 365 Human Resources infrastructure merge FAQ](../human-resources/hr-infrastructure-merge-faq.md).

The merge will provide consistency for Human Resources users in the following ways:

- [Environment management and integrations are consistent between Human Resources and Finance and Operations apps.](/dynamics365-release-plan/2021wave2/human-resources/dynamics365-human-resources/consistent-environment-management-integrations-between-human-resources-finance-operations-apps)

    - Manage environments in Microsoft Dynamics Lifecycle Services, issue search, and Regression Suite Automation Tool.
    - There is a single code base, where new functionality for Human Resources is released as part of the regular One Version update process.
    - The way that upgrades, updates, and hotfixes are applied to environments is consistent.

- [Extensibility options are improved.](/dynamics365-release-plan/2021wave2/human-resources/dynamics365-human-resources/improve-extensibility-options)

    - You can continue to use Microsoft Power Platform tools to extend as required.
    - You can extend functionality via forms, tables, methods, and application programming interfaces (APIs).
    - You can create and extend entities.

    For more information about the extension options that are available, see [Overview of extensibility in Dynamics 365](../fin-ops-core/dev-itpro/extensibility/extensibility-home-page.md).

- [Create one set of human resources capabilities in Dynamics 365.](/dynamics365-release-plan/2021wave2/human-resources/dynamics365-human-resources/create-one-set-human-resources-capabilities-within-dynamics-365)

    In the 10.0.25 release, functional capabilities that existed only in Human Resources have been made available on the Finance and Operations infrastructure. For customers to take advantage of these capabilities in a Finance and Operations environment, the following Human Resources features must be enabled in Feature Management.

    | Feature name | Overview | Release status | 
    |--------------|----------|----------------| 
    | Years of service calculation | A setup option lets you select the date that is used for the **Years of service** calculation. | Generally available | 
    | Workflow experience enhancements | This feature provides an enhanced user experience for workflow submissions and approvals. | Generally available | 
    | Print performance reviews | You can print performance reviews in PDF format. | Generally available | 
    | Custom links in **Manager self service** | You can create custom links that appear in the **Related links** section of **Manager self service**. | Generally available | 
    | Cross company compensation view | Users can view compensation plans in **Manager self service** across all legal entities, without having to switch companies. | Generally available | 
    | Configure multiple compensation levels by job\*&dagger; | Jobs now support multiple compensation levels. | Preview | 
    | Task Management\* | You can create checklists and tasks for the onboarding, offboarding, and transition process. | Preview | 
    | Streamlined employee entry | This feature provides an updated user experience on the existing **Worker** page. | Preview | 
    | Human resources user experience enhancements | See the table in the next section.  | Preview | 

\* This feature must be turned on before the **Human resources user experience enhancements** feature.

&dagger; This feature can't be disabled after it's enabled.

## Human resource user experience enhancements

| Feature name | Overview | 
|--------------|----------| 
| Delete employment | You can delete an employment of an employee. | 
| Job families | You can track a group of jobs that involve similar work, and that require similar training, skills, knowledge, and expertise. | 
| Additional employment fields | The following fields were added: **Employment category**, **Employment type**, and **Employment status**. | 
| **Workers without employment** page | A page shows a list of workers who don't have an employment record. | 
| Position dimension user experience update | There is an enhanced user experience for assigning position dimensions per legal entity. | 
| Address changes in **Personnel management** workspace | This feature provides a count of all address changes that occurred during a specified number of days, as defined on the **Human resources parameters** page. | 
| Expiring records in **Personnel management** workspace | This feature provides a list of items that have expired or will expire for certificates, identifications, probations, screenings, or tests. | 
| **Position hierarchy validation** page | A check is done for circular references in the position line hierarchy. | 
| Country specific payroll information | Additional payroll fields are available on the **Worker employment** page, depending on the country or region of the legal entity where the workers are employed. | 
| Compliance reporting enhancements | Additional reporting options are available for EEO-1, Vets 4212, and OSHA300a. | 
| Updates to the **Personnel management** workspace | Updates have been made to track address changes and expiring records. Additionally, new tabs list worker and position actions. | 
