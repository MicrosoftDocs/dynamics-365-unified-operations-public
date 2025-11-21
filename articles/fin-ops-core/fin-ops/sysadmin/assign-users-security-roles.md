--- 
title: Assign users to security roles
description: Learn about how to manage users and security roles, including outlines on autoatically assigning users to roles and manually assigning users to roles.
author: johnmichalak
ms.author: johnmichalak
ms.topic: how-to
ms.date: 11/21/2025
ms.custom:
ms.reviewer: johnmichalak  
audience: Application User 
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: SysSecRolesEditUsers, SysSecAssignmentQueryLookup, SysQueryForm, SysSecRoleExcludeUsers
ms.dyn365.ops.version: Version 7.0.0 
---

# Manage users and security roles

[!include [banner](../../../finance/includes/banner.md)]

To use anything other than common capabilities in finance and operations apps, assign users to security roles. You can assign users to roles automatically, based on rules and business data, exclude users from automatic role assignment, or add users to roles manually.

## Automatically assign users to roles
This procedure explains how system administrators can automatically assign users to roles, based on business data. 
1. Go to **Navigation pane > Modules > System administration > Security > Assign users to roles**.
1. In the tree, select 'Accounting supervisor'. Select the role that you want to configure the rule for. In this example, select Accounting supervisor. 
1. Select **Add rule** to open the dialog menu.
1. In the **Select a query** list, find and select the desired record. Select the query to use for this rule.  
1. In the **Membership rule name** list, select the link in the selected row.
1. Select **Edit query**. Edit the query, as needed.  
1. Select **OK**.
1. Select **Run automatic role assignment**.
1. Go to **Navigation pane > Modules > System administration > Users > Users** (ideally in a separate browser tab).
1. Review the roles assigned to various users to confirm that the role assignment query was correct. Adjust and re-run if needed.

## Exclude users from automatic role assignment
This procedure explains how to exclude users from automatic role assignment.

1. Close the page.
1. Go to **Navigation pane > Modules > System administration > Security > Assign users to roles**.
1. In the tree, select 'Accounting supervisor'. Select a role. For this example, select Accounting supervisor.  
1. In the **Users assigned to role** menu, select **Manually assign/exclude users**.
1. In the **Assign users to or exclude users from role** list, mark the selected row. Select a user.  
1. On the **Action pane**, select **Exclude from role**.
1. Select **Exclude from role** to exclude the selected users from the role. To remove exclusions, select the users that you want to remove exclusions for, and then select **Reset status**. When you remove an exclusion by resetting the user's status, the user's role is assigned automatically. However, the user isn't immediately assigned to the role or excluded from the role when you reset the status. Instead, the user is either assigned to the role or removed from the role the next time that the rules for automatic role assignment run.  

## Manually assign users to roles
Users who are manually assigned to security roles must also be manually removed by the administrator. These users are not removed from roles by rules for automatic role assignment.

1. Go to **Navigation pane > Modules > System administration > Security > Assign users to roles**.
1. In the tree, select a role, and in the **Users assigned to role** menu, select **Manually assign/exclude users**.
1. In the **Assign users to or exclude users from role**, users that have not been assigned the role are listed with the **Assignment mode** set to **None**. Select one or more users that should be assigned the role.
1. On the **Action pane**, select **Assign to role**. The **Assignment mode** is updated to **Manual** and the users now have a new role assigned.

## Manually remove users from roles
Users who are manually assigned to security roles must also be manually removed by the administrator. These users are not removed from roles by rules for automatic role assignment.

1. Go to **Navigation pane > Modules > System administration > Security > Assign users to roles**.
1. To remove one user, follow these steps:
   1. In the tree, select a role. 
   1. In the **Users assigned to role** area, select the user that should be removed.
   1. Select **Remove** and the user is removed from the role.
1. To remove multiple users, follow these steps:
   1. In the tree, select a role. 
   1. In the **Users assigned to role** area, select **Manually assign/exclude users**.
   1. In the **Assign users to or exclude users from role** page, users that have not been assigned to the role have **None** in the **Assignment mode** column. Select the users that should be excluded from the role.
   1. On the **Action pane**, select **Exclude from role**. The **Assignment mode** column is now updated to **Manual** and the users are now excluded from the role.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

