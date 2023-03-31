--- 
# required metadata 
 
title: Identify and resolve conflicts in segregation of duties
description: This article explains how to identify and resolve conflicts in segregation of duties.
author: peakerbl
ms.date: 01/04/2021
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SysSecSegregationOfDutiesConflict, SysSecSegregationOfDutiesRule   
audience: Application User 
# ms.devlang:  
ms.reviewer: sericks
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: peakerbl
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Identify and resolve conflicts in segregation of duties

[!include [banner](../../includes/banner.md)]

This article explains how to identify and resolve conflicts in segregation of duties. You can set up rules to separate duties that must be performed by different users. This concept is named segregation of duties. When the definition of a security role or the role assignments of a user violate the rules, the conflict is logged. All conflicts must be resolved by the administrator. Complete the following procedure to identify and resolve conflicts.

After a rule has been added, verify that all existing roles are compliant. 

## Verify that existing roles and duties comply with new rules for segregation of duties
1. Go to **System administration** > **Security** > **Segregation of duties** > **Segregation of duties rules**.
3. Select **Validate duties and roles**. If any roles violate the rules, a message is displayed that contains the name of the rule, the role, and the names of the conflicting duties. Conflicting roles must be modified using **Security configuration** and can't include conflicting duties. If no roles violate the selected rule, a message indicates that all roles comply.   

> [!NOTE]
> The validation is only performed for the selected rule. It is important to validate compliance for each rule.   

When you create or modify a role, the rules for segregation of duties are automatically enforced. You cannot assign conflicting duties to a role.

Next, verify that all existing role assignments are compliant.

## Verify that user role assignments comply with new rules for segregation of duties
1. Go to **System administration > Security > Segregation of duties > Verify compliance of user-role assignments**.
2. Select **OK**. A notification displays the results of the validation. Conflicts are logged on the **Segregation of duties unresolved conflicts** page.   

When you assign users to roles, the rules for segregation of duties are automatically enforced. If you try to assign a user to roles that contain conflicting duties, you receive an error message. You must then resolve the conflict by denying or allowing the additional role assignment. The additional role will be assigned after the assignment is allowed. 

> [!NOTE]
> Conflicts are currently not verified for users that are assigned roles based on the Active Directory Domain groups.

## View and resolve conflicting user role assignments
1. Go to **System administration** > **Security** > **Segregation of duties** > **Segregation of duties unresolved conflicts**. 
2. Select a conflict, and then select one of the following actions: 

  - **Deny assignment**: This will deny the assignment of the user to the additional security role. If you deny an automatic role assignment, the user is marked as excluded from the role. The excluded user isn't granted the access associated with the role and can't be assigned to the role until the administrator removes the exclusion. 
-  **Allow assignment**: This will override the conflict and allow the user to be assigned to the additional security role. If you override a conflict, you must enter a reason in the **Reason for override** field. All overridden role assignments can be viewed on the **Segregation of duties conflicts** page.  

> [!NOTE]
> If several conflicts are listed for the same user, select the user record and evaluate assigned roles on the **Users** page. To avoid this conflict, validate each rule after it's added or modified.


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]