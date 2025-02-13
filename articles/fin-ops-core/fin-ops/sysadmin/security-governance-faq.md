---
title: Security governance FAQ
description: Get answers to frequently asked questions about security governance.
author: saurabhgupta
ms.author: saurabhgupta
ms.topic: article
ms.date: 01/25/2025
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
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article provides answers to the most frequently asked questions about the security governance feature, how it's set up, and how it's used.

## Can the feature be used to hide specific fields on a page or control the ability of some roles to edit specific fields on a page?

For most fields, you must do a custom implementation of the business logic to control the permissions. However, if there is an entry point behind the selected field, it can be controlled through the user security governance feature.

## Is the feature integrated with any version control system to maintain the various XML or AXTR files that are generated during use?

No, security governance isn't integrated directly with any version control. We recommend that you control all files through version control, so that system administrators can maintain copies of files or task recording files. This approach is helpful for compliance audits, because users just have to compare the security versions with the approved security architecture.

## Does the process hierarchy work with customized menu items that are mapped to privileges?

Yes, the process hierarchy works with custom menu items.

## Is temporary role management captured in the security audit trail?

Yes. Any role changes that are made for an active user account are captured on the **Security audit trail** report.

## Does the feature work with user groups or user access that is assigned through Microsoft Azure Active Directory (Azure AD)?

No. Security governance uses the user that is created directly in the **Security administration** module in Dynamics 365 finance and operations apps.

## If a user is disabled in the Microsoft Entra app, is that user also disabled in finance and operations apps?

No. The two user management systems aren't currently integrated.

## Is the task recording functionality in security governance session recording similar to the Dynamics AX 2012 Security development tool?

Yes, the task recording functionality is similar to the Security development tool. However, it includes some new technical changes.

## Is there any feature that includes usage information by user, and that shows not only users who have the correct licenses, but also how often those users sign in and use the system?

Yes. The **User aging** report provides this information.

## Where can I view information about user license utilization?

The **License summary** report shows license use by factors such as role, user, duty, or privilege.

## Can I add an existing standard duty to a newly created role within security governance module and see it on the security configuration?

Yes, this is supported functionality of security governance. When adding existing duty to a role while creating task or entry points, confirm to toggle **Add as a reference**. This creates a reference between newly created role with the duty. You can verify it by going to the **Security configuration** page by selecting the particular role. 

## Regional or company specific localizations may be applied to different areas. Does each legal entity with localizations need to have it's own task recordings to be able to create roles using task recordings?

It depends. If the task recording strictly depends on the security objects and AOT names only, then the same task recording can work for multiple localizations. If there are user inputs involved in specific language, it might not work for other languages. 

## In a hypothetical situation where there is a process P1, in country A, process P1 is responsibility of the 'Sales rep' role. In country B, same responsibility is for the 'Customer service assistant' role. The same for process P2, in country A it's done by the 'Accountant' role and in the country B, by the 'Logistics' role. It seems there's no standard organizational hierarchy in a multi-national company, administering roles made through task recording will be hard and complex.

Using same task recording files in such situation shouldn't be difficult. The purpose of task recordings is to generate tasks and duties under a role. While defining the security hierarchy for each country, the system administrator name the **Security role** the appropriate name while using the same task recording file between different countries. The task recording helps in creating a template for the role, it doesn't create the role. 

##  Can we get user logging in and out date/time stamp from the security governance reports?

No. We are showing the total count of unique log-in sessions by each date for each user. 

## Is there any relation between security governance audit logs and Microsoft Sentinel product? 

No, both these products are independent and don't utilize each other.

## What impact does the task recording of privileged user management feature have on the overall database size?

To keep the file size per session under control, each privileged user management session is limited to maximum 24 hours. System administrators can download the recording file locally to archieve it and delete from the database. 

## Is there a way to run a temporary role assignment session with a different role without assigning it to my current user? Something similar to what was possible in AX 2012 test as role option?

This is not supported within security governance module. 

## Are there any automated reminders about temporary role assignment functionality?

Currently, there's no notifications generated from temporary role management or privileged user management features. 

## Is there a way to test security roles without assigning them to a user and logging in?

To test a role, it must be assigned to user and then validated. With security governance process hierarhy, system administrators can design the roles, without publishing, and review their entry points and duties. 

## Can a batch job be set up from the User aging report screen to disable users based on 30-60-90 day rules?

There is no feature available to set up a batch job through the user interface on this report. 

## Is there a scenario supported where a role has direct access to privileges instead of through duties?

Not within security governance feature.

## In some cases, it is required to go to a lower level for access to work. Does this work to the finer level?

Security roles defined in security governance goes at the lowest level, which is the entry point. 

## Do the old task recording files (from before the launch of security governance feature) work with the new interface or customers have to record them again?

Previous task recordings will work. There is no impact of security governance feature on the task recording tool. Security governance simply uses the task recording file to extract entry points. 

## If I understand correctly, process view creates a 1:1 relationship between Duty and Privilege. Isn't this in conflict with the Role-Duty-Privilege hierarchical structure?

With the security governance feature, the vision is to have unique duties performing very specific tasks. We recommend creating duty per task and eventually, a role can be bundle of multiple duties. Keeping a duty as narrow as possible will help in ensuring the segregation of duty. 

## For finance users who run multiple processes throughout the month, will one role for their entire job be created or will they need to have multiple roles for each process?

It is up to the system administrator to define a single role with multiple tasks and duties which is a collection of all processes done by the Finance user. Systam administrators can split it into multiple roles and duties and assign all such roles to a given user.

## How does it handle the scenario where different data scenarios call different code in the back end. Do you have to record every possible scenario to ensure that the task recordings capture all possible permutations of permissions to back end features and branches of code?

You don't have to record every scenario. Start with one base scenario and then manually assign more entry points to the role based on your expectation from this role. Utilize the **Explore entry points** feature to find surrounding entry points. 

## Will the current way of licensing be deprecated after this new feature are Generally available or will they co-exist for some time?

Licensing is still defined at the entry point level and security governance utilizes the entry points. These two features utilize each other and there is no negative impact on each other. 

## Can you check which role isn't used by user in last weeks or months and can be removed?

Yes, you can see data for active users, through the user name, that isn't using the Dynamics 365 finance and operations. 

## For the audit and elevated privilege information capture, is there a process to archive this for future audits and avoid it becoming too large. Is there a performance hit with this auditing?

The sessions being recorded as part of privileged user management are available to system administrators. We have limited the privileged management session to a maximum 24 hours long, keeping these recordings size under control.

## To optimize licensing, we would like to be able to get a log of user activity for a given time period, which would contain used entry points - menu items. Is there a user activity log part of Security governance?

New reports that are availble in User governance provide information about usage of entry points by roles, which is mapped to a user. 

## Can we get information about failed login attempt as part of the compliance reports?

No, this doesn't monitor if the authurization was successful or not. This monitors user log-in activity after they are using Dynamics 365 finance and operations.  

