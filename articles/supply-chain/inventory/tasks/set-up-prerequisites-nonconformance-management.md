--- 
# required metadata 
 
title: Set up prerequisites for nonconformance management
description: Use this topic to enable nonconformance management processes. 
author: perlynne
manager: AnnBe 
ms.date: 08/19/2019
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: InventParameters, InventTestReportSetup, SysUserManagement, SysUserSetup, InventTestDiagnosticType, InventTestMiscCharges, InventTestOperation, InventProblemType, InventProblemTypeSetup, InventQuarantineZone   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: perlynne
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up prerequisites for nonconformance management

[!include [banner](../../includes/banner.md)]

Use this topic to enable nonconformance management processes. A nonconformance describes a procedure or item that has a quality problem, where the descriptive information includes the source and type of problem. This procedure uses the USMF demo data company. This procedure is typically performed by a quality manager.


## Enable quality management processes within the company
1. In the navigation pane, go to **Modules > Inventory management > Setup > Inventory and warehouse management parameters**.
2. Select the **Quality management** tab.
3. Select **Yes** in the **Use quality management** field to enable quality management processes for the company.
4. In the **Hourly rate** field, enter a number in the local currency. The hourly rate is used for calculating costs for operations that are related to a nonconformance. The hourly rate and calculated costs provide reference information for a nonconformance, and they do not interact with other functionality.  
5. Select **Report setup** to define the quality report note types that will be used on different kinds of quality management reports.

## Enable user for nonconformance processing
1. In the navigation pane, go to **Modules > System administration > Users > Users**. 
2. Use the Quick Filter to find the user who will be approving or rejecting the nonconformance records. For example, filter on the **Name** field with a value of `Ricardo`. To process the approval of a nonconformance, the user who approves or rejects nonconformances must have a "Name" value assigned on the **Users** page. To use the document notes, the user must also have Document handling activated in the user options.  
3. Mark the row of the desired record.
4. Select **User options**.
5. Select the **Preferences** tab.
6. Select **Yes** in the **Enable document handling** field.

## Define diagnostic types for nonconformance processing
1. In the navigation pane, go to **Modules > Inventory management > Setup > Quality management > Diagnostic types**. Use the **Diagnostic types** page to define a classification of diagnostic actions. A correction identifies what type of diagnostic action should be taken on an approved nonconformance, who should perform it, and the requested and planned completion date.  
2. Select **New**.
3. In the **Diagnostic** field, type a value.
4. In the **Description** field, type a value.

## Define quality charges for nonconformance processing
1. In the navigation pane, go to **Modules > Inventory management > Setup > Quality management > Quality charges**. Use the **Quality charges** page to define a classification of charges that will used in operations related to nonconformances.  
2. Select **New**.
3. In the **Charges code** field, type a value.
4. In the **Description** field, type a value.

## Define the operations for nonconformance processing
1. In the navigation pane, go to **Modules > Inventory management > Setup > Quality management > Operations**. Use the **Operations** page to define a classification of the work that may be performed for an approved nonconformance. When you relate an operation to a nonconformance, you can define information about the associated material, labor hours, and miscellaneous charges that are required to perform the operation. This information provides the basis for calculating an estimated cost for performing the operation.  
2. Select **New**.
3. In the **Operation** field, type a value.
4. In the **Description** field, type a value.

## Define problem types for nonconformance processing
1. In the navigation pane, go to **Modules > Inventory management > Setup > Quality management > Problem types**. Use the **Problem types** page to define a classification of quality problems that are encountered in the various nonconformance types. The nonconformance types include **Internal**, **Customer**, **Vendor**, **Service request**, **Production**, and **Co-product production**. A single problem type can be associated with multiple nonconformance types.  
2. Select **New**.
3. In the **Problem type** field, type a value.
4. In the **Description** field, type a value.
5. Select **Non conformance types**. Use the **Non conformance types** page to authorize the use of a problem type for one or more of the nonconformance types. For example, a problem type regarding a defect code could apply to all nonconformance types, whereas a problem type about customer complaints may only apply to the customer and service request nonconformance types.  
6. Select **New**.
7. In the **Non conformance type** field of the new row, select an option.

## Define quarantine zones for nonconformance processing
1. In the navigation pane, go to **Modules > Inventory management > Setup > Quality management > Quarantine zones**.
2. Select **New**.
3. In the **Quarantine zone** field, type a value.
4. In the **Description** field, type a value.
5. Close the page.

