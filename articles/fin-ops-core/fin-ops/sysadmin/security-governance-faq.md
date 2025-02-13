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

## Can I add an existing standard duty to a newly created role within security governance module and be able to see it on security configuration?

Yes, this is one of the core supported functionality of security governance. When adding existing duty to a role while creating task/ entry points, make sure to select the toggle button of **Add as a reference** and this will create a reference between newly created role with duty. You will be able to verify it under the **security configuration** page by selecting the particular role. 

## Regional or company specific localizations may be applied to different areas. I presume each legal entity with these localizations would need to have it's own task recordings to be able to create roles using task recordings?

It depends. If the task recording strictly depends on the security objects and AOT names only, then the same task recording can work for multiple localizations but if there are user inputs involved in specific language, it might not work for other languages. 

## In a hypothetical situation where there is a process P1 and in country A process P1 is responsibility of role 'Sales rep'. In country B, same responsibility is for role 'Customer service assistant'. The same for process P2 where in the country A it is done by security role 'Accountant' and in the country B, by security role 'Logistics'. It seems if there is no standardized organizational hierarchy in a multi-national company, administering roles made through task recording will be hard and complex.

Using same task recording files in such situation should not be difficult. The purpose of task recordings is to generate tasks and duties under a role. While defining the security hierarchy for each country, it is totally up to the system administrator to give desired name to the **security role** while still using the same task reording file between different countries. The task recording helps in creating a template for the role, it does not create the role. 

##  Can we get user logging in and out date/time stamp from the security governance reports?

No. We are showing the total count of unique log-in sessions by each date for each user. 

## Is there any relation between security governance audit logs and Microsoft Sentinel product? 

No, both these products are indepent and are not utilizing each other.

## What impact does the task recording of privileged user management feature have on overall database size?

To keep the file size per session under control, we have limited the duration of each privileged user management session to maximum 24 hours. Also, if the system administrators want, they can download the recording file locally to archieve it and then delete from the database. 

## Is there a way to run a temporary role assignment session with a different role without assigning it to my current user? Something similar to what was possible in AX 2012 test as role option?

Not supported within security governance module. 

## Are there any automated reminders about temporary role assignment functionality?

Currently, there are no notifications generated from temporary role management or privileged user management features. 

## Is there a way to test security roles without assigning them to a user and logging in?

To test a role, it must be assigned to user and then validated. But, with security governance process hierarhy, system administrator can design all roles and without publishing, still review their entry points and duties. 

## Can a batch job be setup from the User aging report screen to disable users based on 30-60-90 day rules?

This sounds like a good scenario to explore but at this moment, there is no direct feature available to setup the batch job through the user interface on this report. 

## Is there a scenario supported where a role has direct access to privileges instead of through duties?

Not within security governance feature.

## In some cases, it is required to go to a lower level for access to work. Does this work to the finer level?

Security roles defined in security governance goes at the lowest level, which is entry point. 

## Do the old task recording files (from before the launch of security governance feature) work with the new interface or customers have to record them again?

Previous task recordings will also work. In fact, there is no impact of security governance feature on the task recording tool. Security governance simply uses the task recording file to extract entry points. 

## If I understand correctly, Process view creates a 1:1 relationship between Duty and Privilege. Isn't this in conflict with the Role-Duty-Privilege hierarchical structure?

With the security governance feature, the vision is to have unique duties performing very specific tasks. We recommend creating duty per task and eventually, a role can be bundle of multiple duties. Keeping a duty as narrow as possible will help in ensuring the segregation of duty. 

## For finance users who run multiple processes throughout the month, will it create one role for their entire job or will they need to have multiple role for each process?

It is up to the system administrator to define a single role with multiple tasks and duties which is a collection of all processes done by Finance user or to split it into multiple roles and duties and assign all such roles to a given user.

## How does it handle the scenario where different data scenarios call different code in the back end. Would you literally have to record every possible scenario to ensure that the task recordings capture all possible permutations of permissions to back end features and branches of code?

You do not have to record every scenario. You can start with one base scenario and then manually assign more entry points to the role based on your expectation from this role. You can also utilize the feature **explore entry points** to find surrounding entry points. 

## Will the current way of licensing be deprecated once this new features are GA or will they co-exist for some time?

Licensing is still defined at the entry point level and security governance feature utilizes the entry points. These two features utilize each other and there is no negative impact on each other. 

## Will there be a possibility to check which role was not used by user in last weeks/months and therefore can be removed?

You will be able to see the data for active users And, through the user name, you can find out the roles assigned to that particular user, which is not using the F&O app in weeks/ months. So, Yes, you can find this data now. 

## For the audit and elevated privilege information capture - is there a process to archive this for future audit and clean to avoid it becoming too large. Is there a performance hit with this auditing?

The sessions being recorded as part of Privileged user management are available to System administrators. It is up to the company and sys admins on how they would like to archive these files. We have verified at our end and knowingly limited the Privileged management session max. 24 hours long, hence keeping these recordings size under control.

## To optimize licensing, we would like to be able to get a log of user activity for a given time period, which would contain used entry points - menu items. Currently there is nothing like that, except for Task recorder. Are you planning to make some such user activity log part of Security Governance?

Based on all the new reports being provided as part of USG module, I am pretty sure you will be able to obtain the data you are looking for here. You will be able to see the usage of entry points by roles, which is 1-1 mapped to a user. 

## Are we also getting the information of failed login attempt as part of compliance reports ask?

No, this is not monitoring the 2-FA step and whether the auth was successful or not. This will monitor user log-in activity once they are in the F&O module. 

