---
# required metadata

title: Set up prerequisites for management
description: Use this procedure to enable nonconformance management processes.
author: perlynne
manager: AnnBe
ms.date: 11/02/2017
ms.topic: business-process
ms.prod:  
ms.service: dynamics-ax-applications
ms.technology:  

# optional metadata

# ms.search.form:   
audience: Application User
# ms.devlang:  
ms.reviewer: YuyuScheller
ms.search.scope: Operations
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: perlynne
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---
# Set up prerequisites for management

[!include[task guide banner](../../includes/task-guide-banner.md)]

Use this procedure to enable nonconformance management processes. A nonconformance describes a procedure or item that has a quality problem, where the descriptive information includes the source and type of problem. This procedure uses the USMF demo data company. This procedure is typically performed by a quality manager.


## Enable quality management processes within the company
1. Go to Inventory management > Setup > Inventory and warehouse management parameters.
2. Click the Quality management tab.
3. Select Yes in the Use quality management field.
    * Select this parameter to enable quality management processes for the company.  
4. In the Hourly rate field, enter a number.
    * Use the Hourly rate field to enter an hourly labor rate in the local currency. The hourly rate is used for calculating costs for operations that are related to a nonconformance. The hourly rate and calculated costs provide reference information for a nonconformance, and they do not interact with other functionality.  
5. Click Report setup.
    * This page allows you to define the quality report note types that will be used on different kinds of quality management reports.  
6. Close the page.
7. Close the page.

## Enable user for nonconformance processing
1. Go to System administration > Users > Users.
    * To process the approval of a nonconformance the user who  approves or rejects nonconformances must have a “Name” value assigned on the Users page. To use the document notes, the user must also have Document handling activated in the user options.  
2. Use the Quick Filter to find records. For example, filter on the Name field with a value of 'Ricardo'.
    * Use the filter to find the user who will be approving or rejecting the nonconformance records.  
3. In the list, click the link in the selected row.
    * To process the approval of a nonconformance, make sure the user who approves or rejects nonconformances has a “Name” value assigned on the Users page.  
4. Click User options.
5. Click the Preferences tab.
6. Select Yes in the Enable document handling field.
    * To use the document notes, the user must also have Document handling activated in the user options.  
7. Close the page.
8. Close the page.
9. Close the page.

## Define diagnostic types for nonconformance processing
1. Go to Inventory management > Setup > Quality management > Diagnostic types.
    * Use the Diagnostic types page to define a classification of diagnostic actions. A correction identifies what type of diagnostic action should be taken on an approved nonconformance, who should perform it, and the requested and planned completion date.  
2. Click New.
3. In the Diagnostic field, type a value.
4. In the Description field, type a value.
5. Close the page.

## Define quality charges for nonconformance processing
1. Go to Inventory management > Setup > Quality management > Quality charges.
    * Use the Quality charges page to define a classification of charges that will used in operations related to nonconformances.  
2. Click New.
3. In the Charges code field, type a value.
4. In the Description field, type a value.
5. Close the page.

## Define the operations for nonconformance processing
1. Go to Inventory management > Setup > Quality management > Operations.
    * Use the Operations page to define a classification of the work that may be performed for an approved nonconformance. When you relate an operation to a nonconformance, you can define information about the associated material, labor hours, and miscellaneous charges that are required to perform the operation. This information provides the basis for calculating an estimated cost for performing the operation.  
2. Click New.
3. In the Operation field, type a value.
4. In the Description field, type a value.
5. Close the page.

## Define problem types for nonconformance processing
1. Go to Inventory management > Setup > Quality management > Problem types.
    * Use the Problem types page to define a classification of quality problems that are encountered in the various nonconformance types. The nonconformance types include Internal, Customer, Vendor, Service request, Production, and Co-product production. A single problem type can be associated with multiple nonconformance types.  
2. Click New.
3. In the Problem type field, type a value.
4. In the Description field, type a value.
5. Click Non conformance types.
    * Use the Non conformance types page to authorize the use of a problem type for one or more of the nonconformance types. For example, a problem type regarding a defect code could apply to all nonconformance types, whereas a problem type about customer complaints may only apply to the customer and service request nonconformance types.  
6. Click New.
7. In the list, mark the selected row.
8. In the Non conformance type field, select an option.
9. Close the page.
10. Close the page.

## Define quarantine zones for nonconformance processing
1. Go to Inventory management > Setup > Quality management > Quarantine zones.
2. Click New.
3. In the Quarantine zone field, type a value.
4. In the Description field, type a value.
5. Close the page.
