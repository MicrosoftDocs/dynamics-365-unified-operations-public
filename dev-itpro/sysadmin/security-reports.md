---
# required metadata

title: Out-of-the-box security reports
description: Dynamics 365 for Finance and Operations, Enterprise edition provides a set of rich, security reports to help you understand the set of security roles running in your environment and the set of users assigned to each role.
author: sericks
manager: AnnBe
ms.date: 06/23/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
# ms.reviewer: sericks
# ms.search.scope: Operations Platform, Core
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: maertenm
ms.dyn365.intro: 2017-06-30
ms.dyn365.version: Platform update 8
---

# Out-of-the-box security reports

[!include[banner](../includes/banner.md)]

Dynamics 365 for Finance and Operations, Enterprise edition provides a set of rich, security reports to help you understand the set of security roles running in your environment and the set of users assigned to each role. Each of these reports can be found under **System administration \> Inquiries \> Security.** A description of each report is provided below.

User role assignments
----------------------------

The **User role assignments** report generates a view of the current user role assignments in your system. By default, the report includes all users with roles assigned. You can optionally limit the report to a specific set of users by entering a list of users when generating the report. On the **User role assignments** parameters pane, go to **Records to include** > **Filter.** From here you can add or remove filters to the list of users the report will be generated for.

![User role assignments](media/User-role-assignments.PNG)

For each user in the report a list of roles given, along with any restrictions at the legal entity or organization level.

Role to User Assignments 
-------------------------

The security role access report provides an aggregation of user role assignments group by the security role, rather than by user. The same method for filtering the set of users can be applied to this report as described for the User role assignments report.

![](media/cc339ed5f8b39f4bc9908a16f450f44d.png)

Expanding a role shows the list of users assigned to the role and expanding the user shows any restrictions the role has applied.

Security Role Access
--------------------

The Security role access report provides a view of the effective permissions provided by each security role. This report will provide a flattened list of permissions grouped by type across all sub-roles, duties, and privileges contained in the role.

The data set backing the Security role access report can be very large, causing the report to take longer to run. If there have been no changes to security roles since the last time the report was run, you can skip building the report by setting the “Rebuild collection” option to No on the report parameters form. This will render the report from the existing data set. If it is the first time the report has run, or there could be changes to the role definitions, the “Rebuild collection” should be set to yes. You can optionally limit the roles to be included in the report by adding a filter under “Records to include.”

![](media/95065a2382fb72c9d771ac6314006f4d.png)

Expanding a role shows the category of objects the role has access to. Expanding one of the object types will show a detailed list of each object of that type included in the role.

Security Duty Assignments
-------------------------

The Security duty assignments report provides a view of all the duties contained within a role. This role can be configured to run on any collection of roles to ensure that segregation of duties is maintained between roles. By default, the report will include all roles, to limit the roles included leverage the filtering provided in the “Records to include” section.

![](media/9d71783ca5d3003a6837438429e71ff9.png)

Expanding a role in the Security duty assignments report will show each duty assigned to the role, along with details of the duty.

![](media/a6142c903497381171bf6c6b27495895.png)

Any of the above reports can be set to run as a batch job by going to the “Run in the background” section of the reports parameter form. From the parameters for set “Batch processing” to Yes, then provide a batch task job name, batch group, and whether the job should run as Private or Critical. The report will then be created when the batch task runs.

