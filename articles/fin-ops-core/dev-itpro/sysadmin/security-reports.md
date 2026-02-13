---
title: Out-of-box security reports
description: Learn about the security reports that help you understand the set of security roles running in your environment and the users assigned to each role.
author: pnghub
ms.author: johnmichalak
ms.topic: article
ms.date: 01/21/2026
ms.reviewer: johnmichalak 
ms.search.region: Global
ms.search.validFrom: 2017-06-30
ms.search.form:  SysSecConfiguration, SrsReportViewerForm
ms.dyn365.ops.version: Platform update 8
ms.custom:
  - bap-template
  - sfi-image-nochange
---

# Out-of-box security reports

[!include [banner](../includes/banner.md)]

Finance and operations apps provide a set of rich security reports to help you understand the set of security roles running in your environment and the set of users assigned to each role. In addition to the reports noted in this article, developers can generate a workbook containing all user security privileges for all roles by using **Visual Studio > Dynamics 365 > Addins > View related objects and licenses for all roles**.

You can find each of the security reports under **System administration \> Inquiries \> Security.** A description of each report is provided in the following sections.

## User role assignments

The **User role assignments** report shows the current user role assignments in your system. By default, the report includes all users with roles assigned. You can optionally limit the report to a specific set of users by entering a list of users when generating the report. On the **User role assignments** parameters pane, go to **Records to include** > **Filter.** From here, you can add or remove filters to the list of users the report generates.

:::image type="content" source="media/User-role-assignments.PNG" alt-text="Screenshot of the User role assignments report showing users and their assigned roles.":::

For each user in the report, the report provides a list of roles, along with any restrictions at the legal entity or organization level.

## Role to user assignments 

The **Role to user assignment** report provides an aggregation of role assignments. Expanding a role in the report shows the list of users assigned to the role, and expanding the user name shows any restrictions the role has applied. You can apply the same method for filtering the set of users to this report as described for the **User role assignments** report.

:::image type="content" source="media/role-to-user-assignments.png" alt-text="Screenshot of the Role to user assignment report showing roles and their assigned users.":::

## Security role access

The **Security role access** report shows the effective permissions for each security role. This report provides a flattened list of permissions grouped by type across all sub-roles, duties, and privileges contained in the role.

The data set that supports the **Security role access** report can be very large, which can cause the report to take some time to run. If there are no changes to security roles since the last time the report ran, you can skip building the report by setting the **Rebuild collection** option to **No** in the report parameters pane. This setting renders the report from the existing data set. If it's the first time the report runs, or there might be changes to the role definitions, set the **Rebuild collection** option to **Yes**. You can optionally limit the roles to include in the report by adding a filter under **Records to include**.

:::image type="content" source="media/security-role-access.png" alt-text="Screenshot of the Security role access report showing effective permissions for security roles.":::

Expanding a role shows the category of objects the role has access to. Expanding one of the object types shows a detailed list of each object of that type included in the role.

## Security duty assignments

The **Security duty assignments** report shows all the duties contained within a role. You can configure this report to run on any collection of roles to ensure that segregation of duties is maintained between roles. By default, the report includes all roles. To limit the roles included, use the filtering provided in the **Records to include** section.

:::image type="content" source="media/security-duty-assignments.png" alt-text="Screenshot of the Security duty assignments report showing duties contained within roles.":::

Expanding a role in the **Security duty assignments** report shows each duty assigned to the role, along with details of the duty.

## Batch processing of reports
You can set any of the preceding reports to run as a batch job. Go to the **Run in the background** section of the report's parameter pane. Set **Batch processing** to **Yes**, and then provide a batch task job name, batch group, and whether the job should run as Private or Critical. The batch task creates the report when it runs.

:::image type="content" source="media/a6142c903497381171bf6c6b27495895.png" alt-text="Screenshot of the batch processing configuration options for security reports.":::



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
