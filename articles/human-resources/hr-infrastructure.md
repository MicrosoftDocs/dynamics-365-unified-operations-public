---
# required metadata

title: Dynamics 365 Human Resources infrastructure merge - Release 10.0.25 update
description: Microsoft Dynamics 365 Human Resources release 10.0.25 brings the first wave of capabilities in the infrastructure merge.
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

# Infrastructure Merge – Release 10.0.25 update

The 10.0.25 release brings forth the first wave of capabilities in the infrastructure merge.  With the infrastructure merge, Dynamics 365 Human Resources will be merged with the 
Finance and Operations infrastructure, but will continue to be licensed as an independent application, like Finance and Supply Chain Management.  
To learn more about the infrastructure merge, see [Dynamics 365 Human Resources infrastructure merge FAQ](../../../human-resources/hr-infrastructure-merge-faq.md).

The merge will provide consistency for Human Resources users in the following ways:
[Consistent environment management and integrations between Human Resources and Finance and Operations apps](../../../dynamics365-release-plan/2021wave2/human-resources/dynamics365-human-resources/consistent-environment-management-integrations-between-human-resources-finance-operations-apps).
•	Management of environments within Dynamics 365 Lifecycle services, issue search, and Regression Suite Automation Tool
•	Single code base where new functionality for Human Resources is released as part of the regular One Version updated process
•	Consistency in how upgrades, updates, and hotfixes are applied to environments

[Improved extensibility options](../../../dynamics365-release-plan/2021wave2/human-resources/dynamics365-human-resources/improve-extensibility-options.md) 
•	Continue to use Microsoft Power Platform tools to extend where needed
•	Ability to extend functionality via forms, tables, methods, and APIs
•	Ability to create and extend entities
•	For more information on the extension options available, see [Overview of extensibility in Dynamics 365](../fin-ops-core/dev-itpro/extensibility/extensibility-home-page.md).

[Create one set of human resources capabilities within Dynamics 365](../../../dynamics365-release-plan/2021wave2/human-resources/create-one-set-human-resources-capabilities-within-dynamics-365.md)
In the 10.0.25 release, functional capabilities that existed only in Dynamics 365 Human Resources have been made available on the Finance and Operations infrastructure.  
In order for customers take advantage of these capabilities on a Finance and Operations environment, the Human Resources features will need to be enabled in Feature Management.  
These features include:  

| Feature name                          | Overview                                          | Release state                        |
|---------------------------------------|---------------------------------------------------|--------------------------------------|
| Years of service calculation       | Setup option to select the date used for determining **Years of service** calculation.    | Generally available|
| Workflow experience enhancements    |Enhanced user experience for workflow submissions and approvals.      | Generally available    |
| Print performance reviews            | Ability print performance reviews to PDF. | Generally available    |
|Custom links in **Manager self service**  | This feature allows you to create custom links that display in the **Related links** section of **Manager self service**. | Generally available  |
|Cross company compensation view|	Allows users to view compensation plans in **Manager self service** across all legal entities, without having to switch companies.|	Generally available|
|Configure multiple compensation levels by job*+	|Jobs now support multiple compensation levels	|Generally available|
|Task Management*|	Ability to create checklists and tasks for the onboarding, offboarding, and transition process.  |	Preview|
|Streamlined employee entry|	Updated user experience on the existing **Worker** page.	|Preview|
|Human resources user experience enhancements| See table below|	Preview|

\*Must be turned on prior to turning on the Human resources user experience enhancements.

\+ Cannot be disabled once it's enabled.

## Human resource user experience enhancements

| Feature name                          | Overview                                          |
|---------------------------------------|---------------------------------------------------|
|Advanced access|	Restricts access to employees based on legal entity.|
|Delete employment|	The ability to delete an employment of an employee.|
|Job families	|Ability to track a group of jobs that involve similar work, and require similar training, skills, knowledge, and expertise.|
|Additional employment fields	|The following fields were added: **Employment category**, **Employment type**, and **Employment status**.|
|**Workers without employment** page|	A list of workers that do not have an employment record.  |
|Position dimension user experience update|	Enhanced user experience for assigning position dimensions per legal entity.|
|Address changes in **Personnel management** workspace|	Provides a count of all address changes that occurred during a specified number of days, as defined in **Human resources parameters**.|
|Expiring records in **Personnel management** workspace|	Provides a list of items that have expired or will expire for **Certificates**, **Identifications**, **Probations**, **Screenings**, or **Tests**.|
|**Position hierarchy validation** page|	A check for circular references within the **Position line hierarchy**.|
|Country specific payroll information|	Additional payroll fields are available on the **Worker employment** page depending on country location of legal entity that they are employed in.|
|Compliance reporting enhancements|	Additional reporting options for EEO-1, Vets 4212, and OSHA300a.|
|Updates to the **Personnel management** workspace |	Updates to track address changes and expiring records.  New tabs that list worker and position actions. |

