--- 
# required metadata 
 
title: Assign users to security roles
description: To access Finance and Operations apps, users must be assigned to security roles. 
author: ChrisGarty
manager: AnnBe 
ms.date: 11/14/2019
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: SysSecRolesEditUsers, SysSecAssignmentQueryLookup, SysQueryForm, SysSecRoleExcludeUsers   
audience: Application User 
# ms.devlang:  
ms.reviewer: sericks
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: cgarty
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Assign users to security roles

[!include [banner](../../includes/banner.md)]

To use anything other than common capabilities, users must be assigned to security roles. This procedure explains how system administrators can automatically assign users to roles, based on business data. 

## Automatically assign users to roles
1. Go to **Navigation pane > Modules > System administration > Security > Assign users to roles**.
2. In the tree, select 'Accounting supervisor'. Select the role that you want to configure the rule for. In this example, select Accounting supervisor. 
3. Click **Add rule** to open the drop dialog.
4. In the **Select a query**list, find and select the desired record. Select the query to use for this rule.  
5. In the **Membership rule name** list, click the link in the selected row.
6. Click **Edit query**. Edit the query, as needed.  
7. Click **OK**.
8. Click **Run automatic role assignment**.
9. Go to **Navigation pane > Modules > System administration > Users > Users** (ideally in a separate browser tab).
10. Review the roles assigned to various users to confirm that the role assignment query was correct. Adjust and re-run if needed.

## Exclude users from automatic role assignment
1. Close the page.
2. Go to **Navigation pane > Modules > System administration > Security > Assign users to roles**.
3. In the tree, select 'Accounting supervisor'. Select a role. For this example, select Accounting supervisor.  
4. In the **Users assigned to role** menu, select **Manually assign / exclude users**.
5. In the **Assign users to or exclude users from role** list, mark the selected row. Select a user.  
6. On the **Action pane**, select **Exclude from role**.
    
    Click **Exclude from role** to exclude the selected users from the role. To remove exclusions, select the users that you want to remove exclusions for, and then click **Reset status**. When you remove an exclusion by resetting the user's status, the user's role is again assigned automatically. However, the user is not immediately assigned to the role or excluded from the role when you reset the status. Instead, the user is either assigned to the role or removed from the role the next time that the rules for automatic role assignment are run.  
