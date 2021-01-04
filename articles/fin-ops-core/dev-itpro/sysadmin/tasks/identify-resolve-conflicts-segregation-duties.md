--- 
# required metadata 
 
title: Identify and resolve conflicts in segregation of duties
description: This topic explains how to identify and resolve conflicts in segregation of duties.
author: peakerbl
manager: AnnBe 
ms.date: 07/08/2019
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
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

This topic explains how to identify and resolve conflicts in segregation of duties. You can set up rules to separate duties that must be performed by different users. This concept is named segregation of duties. When the definition of a security role or the role assignments of a user violate the rules, the conflict is logged. All conflicts must be resolved by the administrator. Complete the following procedure to identify and resolve conflicts.

After a rule has been added it is required to validate that all existing roles are compliant. 

## Verify whether existing roles and duties comply with new rules for segregation of duties
1. Go to **System administration > Security > Segregation of duties > Segregation of duties rules**
3. Select **Validate duties and roles**. If any roles violate the rules, a message is displayed that contains the name of the rule, the role and the names of the conflicting duties. Conflicting roles must be modified using **Security configuration** and cannot include conflicting duties. If no roles violate the selected rule, a message indicates that all roles are in compliance.   

> [!NOTE]
> The validation is only performed for the selected rule. It is important to validate compliance for each rule.   

When you create or modify a role, the rules for segregation of duties are automatically enforced. You cannot assign conflicting duties to a role.

Next it is time to verify that all existing role assignments are compliant.

## Verify whether user role assignments comply with new rules for segregation of duties
1. Go to **System administration > Security > Segregation of duties > Verify compliance of user-role assignments**.
2. Select **OK**. A notification displays the results of the validation. Conflicts are logged in the **Segregation of duties unresolved conflicts** form.   

When you assign users to roles, the rules for segregation of duties are automatically enforced. If you try to assign a user to roles that contain conflicting duties, you receive an error message. You must then resolve the conflict either by denying or allowing the additional role assignment. The additional role will first be assigned after allowing the assignment. 

> [!NOTE]
> Conflicts are currently not verified for users that are assigned roles based on the Active Directory Domain groups.

## View and resolve conflicting user role assignments
1. Go to **System administration > Security > Segregation of duties > Segregation of duties unresolved conflicts.** 
2. Select a conflict, and then select one of the following actions: 
-  **Deny assignment**. This will deny the assignment of the user to the additional security role. 
   
     If you deny an automatic role assignment, the user is marked as excluded from the role. The excluded user is not granted the access that is associated with the role, and   the user cannot be assigned to the role until the administrator removes the exclusion. 
-  **Allow assignment**. This will override the conflict and allow the user to be assigned to the additional security role. 
    
     If you override a conflict, you must enter a reason in    the **Reason for override** field. All overridden role assignments can be viewed in the **Segregation of duties     conflicts** from.  

> [!NOTE]
>If several conflicts are listed for the same user it is required to go to click on the user and evaluate assigned roles in the user form. To avoid this make sure to validate each rule after it has been added or modified.
