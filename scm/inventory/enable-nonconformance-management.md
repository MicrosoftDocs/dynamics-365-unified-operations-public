---
# required metadata

title: Nonconformance management
description: This article describes the basic setup that is required in order to use nonconformances. Additional setup is required if you want to use quality orders. 
author: YuyuScheller
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: InventParameters, InventProblemType, InventProblemTypeSetup, InventQuarantineZone, InventTestDiagnosticType, InventTestReportSetup, SysUserManagement
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2084
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 28951
ms.assetid: a62d4ba8-eebc-4b14-b587-630be7298522
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Nonconformance management

This article describes the basic setup that is required in order to use nonconformances. Additional setup is required if you want to use quality orders. 

To enable nonconformance management, follow these steps:

1.  Define the Inventory and warehouse management parameters that are related to nonconformances:
    -   Set the **Use quality management** option to **Yes**.
    -   In the **Hourly rate** field, enter an hourly labor rate in the local currency. The hourly rate is used to calculate costs for operations that are related to a nonconformance. The hourly rate and calculated costs provide reference information for a nonconformance. They don't interact with other functionality.
    -   Use the **Quality management** tab on the **Report setup** page to define the type of document to print. You can print a nonconformance report, a nonconformance tag, or a correction report. You can define more than one record to print different document types on a report, or to print internal and external notes. You might find it helpful to use the **Document type** page to define a unique document type for nonconformances and a unique document type for corrections. For example, want to enter notes about a nonconformance by using the unique document type for nonconformances. In this case, identify the unique document type in the report options.
    -   Enable number sequences for nonconformance and correction references.

2.  Enable user approval of nonconformances. Use the **Name** field on the **Users** page to assign an employee to each user who must approve a nonconformance. The system uses the employees who change the status of a noncomformance to track the nonconformance history. Users can't approve a nonconformance unless they have been assigned an employee identifier.
3.  Define the problem types that will be assigned to nonconformances. Use the **Problem types** page to define a classification of quality problems that are encountered for the various nonconformance types. You can set up the following nonconformance types: **Internal**, **Customer**, **Vendor**, **Service request**, **Production**, and **Co-product production**. Use the **Non conformance types** page to authorize a problem type to be used in one or more nonconformance types. For example, a problem type that is related to a defect code might apply to all nonconformance types, whereas a problem type that is related to customer complaints might apply only to the **Customer** and **Service request** nonconformance types.
4.  Define quarantine zones to provide guidance about defective material should be handled. Use the **Quarantine zones** page to define zones that can be assigned to a nonconformance. The printed nonconformance tag will show the assigned quarantine zone and information about usage, to provide guidance about how to handle defective material. The zones might correspond to inventory locations or operations resources.
5.  Define the diagnostic types that will be assigned to corrections. Use the **Diagnostic types** page to define a classification of diagnostic actions. A correction specifies what type of diagnostic action should be taken for an approved nonconformance, and who should take that action. It also specifies the requested completion date and the planned completion date.
6.  Define the related operations that will be assigned to nonconformances. Use the **Operations** page to define a classification of the work that can be performed for an approved nonconformance. When you assign a related operation to a nonconformance, you can provide detailed information, such as information about the associated material, labor hours, and miscellaneous charges that are required in order to perform the operation. This information is used to calculate an estimated cost for the operation. The detailed information and estimated costs are for reference. The related operations for quality differ from the operations that can be defined for a production route.


See also
--------

[Create and process a non conformance (task guide)](https://ax.help.dynamics.com/en/wiki/create-and-process-a-nonconformance/)

[Quality management processes](quality-management-processes.md)

[Set up prerequisites for non-conformance management (task guide)](https://ax.help.dynamics.com/en/wiki/set-up-prequisites-for-nonconformance-management/)

