--- 
title: Identify and resolve conflicts in segregation of duties
description: Learn about how to identify and resolve conflicts in segregation of duties, including an outline on verifying compliance with new rules.
author: johnmichalak
ms.author: johnmichalak
ms.topic: how-to
ms.date: 11/21/2025
ms.custom:
ms.reviewer: johnmichalak  
audience: Application User 
ms.search.region: Global
ms.search.validFrom: 2016-06-30 
ms.search.form: SysSecSegregationOfDutiesConflict, SysSecSegregationOfDutiesRule   
ms.dyn365.ops.version: Version 7.0.0 
---

# Identify and resolve conflicts in segregation of duties

[!include [banner](../../../finance/includes/banner.md)]

This article explains how to identify and resolve conflicts in segregation of duties. You can set up rules to separate duties that different users must perform. This concept is named segregation of duties. When the definition of a security role or the role assignments of a user violate the rules, the conflict is logged. The administrator must resolve all conflicts. Complete the following procedure to identify and resolve conflicts.

After you add a rule, verify that all existing roles are compliant. 

## Verify that existing roles and duties comply with new rules for segregation of duties
1. Go to **System administration** > **Security** > **Segregation of duties** > **Segregation of duties rules**.
1. Select **Validate duties and roles**. If any roles violate the rules, a message displays that contains the name of the rule, the role, and the names of the conflicting duties. You must modify conflicting roles by using **Security configuration** and can't include conflicting duties. If no roles violate the selected rule, a message indicates that all roles comply.   

> [!NOTE]
> The validation only occurs for the selected rule. It's important to validate compliance for each rule.   

When you create or modify a role, the rules for segregation of duties are automatically enforced. You can't assign conflicting duties to a role.

Next, verify that all existing role assignments are compliant.

## Verify that user role assignments comply with new rules for segregation of duties
1. Go to **System administration > Security > Segregation of duties > Verify compliance of user-role assignments**.
1. Select **OK**. A notification displays the results of the validation. The **Segregation of duties unresolved conflicts** page logs conflicts.   

When you assign users to roles, the rules for segregation of duties are automatically enforced. If you try to assign a user to roles that contain conflicting duties, you receive an error message. You must then resolve the conflict by denying or allowing the additional role assignment. The additional role is assigned after the assignment is allowed. 

> [!NOTE]
> Conflicts aren't currently verified for users that are assigned roles based on the Active Directory Domain groups.

## View and resolve conflicting user role assignments
1. Go to **System administration** > **Security** > **Segregation of duties** > **Segregation of duties unresolved conflicts**. 
1. Select a conflict, then select one of the following actions: 

  - **Deny assignment**: This action denies the assignment of the user to the additional security role. If you deny an automatic role assignment, the user is marked as excluded from the role. The excluded user isn't granted the access associated with the role and can't be assigned to the role until the administrator removes the exclusion. 
-  **Allow assignment**: This action overrides the conflict and allows the user to be assigned to the additional security role. If you override a conflict, you must enter a reason in the **Reason for override** field. You can view all overridden role assignments on the **Segregation of duties conflicts** page.  

> [!NOTE]
> If several conflicts are listed for the same user, select the user record and evaluate assigned roles on the **Users** page. To avoid this conflict, validate each rule after you add or modify it.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]