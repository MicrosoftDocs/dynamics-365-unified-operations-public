---
title: Security governance FAQ
description: Get answers to frequently asked questions about security governance.
author: saurabhgupta
ms.author: saurabhgupta
ms.topic: faq
ms.date: 02/13/2025
ms.custom: 
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2025-01-20
ms.search.form: SysSecRolesEditUsers, SysSecAssignmentQueryLookup, SysQueryForm, SysSecRoleExcludeUsers
ms.dyn365.ops.version: Version 7.0.0
---

# Security governance FAQ

[!include [banner](../../../finance/includes/banner.md)]

This article provides answers to the most frequently asked questions about setting up and using the security governance feature.

## Can the feature be used to hide specific fields on a page or control the ability of some roles to edit specific fields on a page?

For most fields, you must do a custom implementation of the business logic to control the permissions. However, if there's an entry point behind the selected field, it can be controlled through the user security governance feature.

## Is the feature integrated with any version control system to maintain the various XML or AXTR files that are generated during use?

No, security governance isn't integrated directly with any version control. We recommend that you control all files through version control, so that system administrators can maintain copies of files or task recording files. This approach is helpful for compliance audits, because users just have to compare the security versions with the approved security architecture.

## Does the process hierarchy work with customized menu items that are mapped to privileges?

Yes, the process hierarchy works with custom menu items.

## Is temporary role management captured in the security audit trail?

Yes. Any role changes that are made for an active user account are captured on the **Security audit trail** report.

## Does the feature work with user groups or user access that is assigned through Microsoft Azure Active Directory (Azure AD)?

No. Security governance uses the user that is created directly in the **Security administration** module in Dynamics 365 finance and operations apps.

## If a user is disabled in the Microsoft Entra app, is that user also disabled in finance and operations apps?

No, the two user management systems aren't currently integrated.

## Is the task recording functionality in security governance session recording similar to the Dynamics AX 2012 Security development tool?

Yes, the task recording functionality is similar to the Security development tool, but includes some new technical changes.

## Is there any feature that includes usage information by user, and that shows not only users who have the correct licenses, but also how often those users sign in and use the system?

Yes, the **User aging** report provides this information.

## Where can I view information about user license utilization?

The **License summary** report shows license use by factors such as role, user, duty, or privilege.

## Can I add an existing standard duty to a newly created role in the security governance module and view it in the security configuration?

Yes, security governance supports this functionality. When you add an existing duty to a role while you create a task or entry points, confirm that the **Add as a reference** option is selected. This setting creates a reference between the newly created role and the duty. To verify the reference, select the role to open the **Security configuration** page. 

## Regional or company-specific localizations might be applied to different areas. To create roles through task recordings, does each legal entity that has localizations need to have its own task recordings?

The answer depends on the specific task recording. If the task recording strictly depends only on the security objects and Application Object Tree (AOT), the same task recording can work for multiple localizations. However, if user inputs in a specific language are involved, the task recording might not work for other languages. 

## There seems to be no standard organizational hierarchy in multinational companies. For example, process P1 is the responsibility of the "Sales rep" role in country A but the "Customer service assistant" role in country B. Likewise, process P2 is the responsibility of the "Accountant" role in country A but the "Logistics" role in country B. In these situations, won't it be difficult and complex to administer roles that are created through task recordings?

It should not be difficult to use the same task recording files in situations of this type. The purpose of task recordings is to generate tasks and duties under a role. When the security hierarchy is being defined for each country, the system administrator gives the security role the appropriate name. The same task recording file is used between countries. The task recording helps create a template for the role but doesn't create the role itself. 

## Can I get a date/time stamp for user sign-in and sign-out from the security governance reports?

No, the reports show only the total number of unique sign-in sessions for each user by date.

## Is there any relation between security governance audit logs and Microsoft Sentinel? 

No, the two products are independent and don't use each other.

## What impact does the task recording of privileged user management feature have on the overall database size?

To help keep the file size per session under control, the length of each privileged user management session is limited to 24 hours. System administrators can download the recording file locally to archive it, and then delete it from the database. 

## Is there a way to run a temporary role assignment session with a different role without assigning that role to my current user? In Dynamics AX 2012, something similar was possible through the test as role option.

No, security governance doesn't support this functionality. 

## Are there any automated reminders about temporary role assignment functionality?

Currently, no notifications are generated from the temporary role management and privileged user management features. 

## Is there a way to test security roles without assigning them to a user and signing in?

A role can be tested only if it's assigned to a user and then validated. With the security governance process hierarchy, system administrators can design the roles, without publishing them, and review their entry points and duties. 

## Can a batch job be set up from the User aging report page to disable users based on 30-60-90 day rules?

No, a batch job can't be set up through the user interface (UI) for this report. 

## Is there a supported scenario where a role has direct access to privileges instead of having access through duties?

No, the security governance feature supports no such scenario.

## In some cases, it's necessary to go to a lower level before access works. Does this work to a lower level?

Security roles that are defined in security governance go at the lowest level, which is the entry point. 

## Do task recording files from before the launch of the security governance feature work with the new interface, or do customers have to record them again?

Previous task recordings will work. The security governance feature has no impact on the task recording tool. Security governance uses the task recording file just to extract entry points. 

## If I understand correctly, the process view creates a 1:1 relationship between a duty and a privilege. Doesn't this behavior conflict with the Role-Duty-Privilege hierarchical structure?

For the security governance feature, the goal is to have unique duties perform very specific tasks. We recommend that you create a duty per task. Then, eventually, a role can be a bundle of multiple duties. By keeping a duty as narrow as possible, you help ensure the segregation of duty. 

## Some Dynamics 365 Finance users run multiple processes throughout the month. Is one role created for their whole job, or do multiple roles have to be created for each process?

The system administrator is responsible for defining a single role that has multiple tasks and duties, and that is a collection of all processes that the Finance user performs. System administrators can split a process into multiple roles and duties, and assign all those roles to a specific user.

## How does security governance handle a case where different data scenarios call different code in the back end? Do I have to record every possible scenario to ensure that the task recordings capture all possible permutations of permissions to back-end features and branches of code?

You don't have to record every scenario. Start with one base scenario, and then manually assign more entry points to the role based on your expectation about this role. Use the **Explore entry points** feature to find surrounding entry points. 

## Will the current way of licensing be deprecated after this new feature becomes generally available, or will they coexist for some time?

Licensing is still defined at the entry point level, and security governance uses the entry points. The two features use each other and have no negative impact on each other. 

## Can I determine which role hasn't been used by a user in previous weeks or months, and remove it?

Yes. Through the user name, you can view data for active users that aren't using Dynamics 365 finance and operations apps. 

## For the capture of audit and elevated privilege information, is there a process to archive the information for future audits and prevent it from becoming too large? Is there a performance hit from this auditing?

The sessions that are recorded as part of privileged user management are available to system administrators. The length of privileged management sessions is limited to 24 hours. The purpose of this limit is to help keep the size of recordings under control.

## To optimize licensing, I want to be able to get a log of user activity for a given period, which shows entry points/menu items that are used. Does security governance include a user activity log?

New reports that are available in User governance provide information about entry point use by role, which is mapped to a user. 

## Can I get information about failed sign-in attempts as part of the compliance reports?

No, security governance doesn't monitor whether the authorization is successful. It monitors user sign-in activity after users are using finance and operations apps.
