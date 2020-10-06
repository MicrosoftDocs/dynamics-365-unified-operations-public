--- 
# required metadata 
 
title: Identify and resolve conflicts in segregation of duties
description: This topic explains how to identify and resolve conflicts in segregation of duties.
author: maertenm
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
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: maertenm
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Identify and resolve conflicts in segregation of duties

[!include [banner](../../includes/banner.md)]

This topic explains how to identify and resolve conflicts in segregation of duties. You can set up rules to separate tasks that must be performed by different users. This concept is named segregation of duties. When the definition of a security role or the role assignments of a user violate the rules, the conflict is logged. All conflicts must be resolved by the administrator. Complete the following procedure to identify and resolve conflicts. The demo data company used to create this procedure is USMF.


## Verify whether user role assignments comply with new rules for segregation of duties
1. Go to **Navigation pane > Modules > System administration > Security > Segregation of duties > Verify compliance of user-role assignments**.
2. Select **OK**. A notification displays the results of the validation. If there is a conflict, you can open the **Users** page and change the user's role assignments. Conflicts are also logged on the **Segregation of duties conflicts** page. To run the verification process as a batch job, select **Batch processing**, and then set the other batch parameters. After the batch job runs, you can review the conflicts in the **Segregation of duties conflicts** page.  

## View and resolve conflicting user role assignments
1. Go to **Navigation pane > Modules > System administration > Security > Segregation of duties > Segregation of duties conflicts.** Select a conflict, and then select one of the following buttons: **Deny assignment – Deny the assignment of the user to the additional security role**. If you deny an automatic role assignment, the user is marked as excluded from the role. The excluded user is not granted the access that is associated with the role, and the user cannot be assigned to the role until the administrator removes the exclusion. Allow assignment – **Override** the conflict, and allow the user to be assigned to both security roles. If you override a conflict, you must enter a reason in the **Reason for override** field.  
2. Close the page.
3. Go to **Navigation pane > Modules > System administration > Security > Segregation of duties > Segregation of duties unresolved conflicts.** Select a conflict, and then select one of the following buttons: **Deny assignment – Deny the assignment of the user to the additional security role**. If you deny an automatic role assignment, the user is marked as excluded from the role. The excluded user is not granted the access that is associated with the role, and the user cannot be assigned to the role until the administrator removes the exclusion. Allow assignment – **Override** the conflict, and allow the user to be assigned to both security roles. If you override a conflict, you must enter a reason in the **Reason for override field**.    
4. Close the page.

## Verify whether existing roles comply with new rules for segregation of duties
1. Go to **Navigation pane > Modules > System administration > Security > Segregation of duties > Segregation of duties rules**. Select a rule.  
2. Select **Validate duties and roles**. If any existing roles violate the selected rule, a message is displayed that contains the name of the role and the names of the conflicting duties. The administrator must either indicate the mitigation for the security risk or modify the role so that it does not violate the rules for segregation of duties. If no roles violate the selected rule, a message indicates that all roles are in compliance.  

