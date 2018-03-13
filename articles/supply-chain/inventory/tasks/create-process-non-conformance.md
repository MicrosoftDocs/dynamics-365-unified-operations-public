---
# required metadata

title: Create and process a conformance
description: Use this procedure to perform nonconformance management, based on an existing quality order.
author: perlynne
manager: AnnBe
ms.date: 11/14/2016
ms.topic: business-process
ms.prod:  
ms.service: dynamics-ax-applications
ms.technology:  

# optional metadata

# ms.search.form:   
audience: Application User
# ms.devlang:  
ms.reviewer: yuyus
ms.search.scope: Operations
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: perlynne
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---
# Create and process a conformance

[!include[task guide banner](../../includes/task-guide-banner.md)]

Use this procedure to perform nonconformance management, based on an existing quality order. You can run this recording in the USMF demo company and can use the suggested values. Typically, this procedure is performed by a quality clerk.  As a prerequisite, run the “Inspect the quality of goods” task recording. To process the approval of a nonconformance, the user who runs the task recording must have a “Name” value assigned on the Users page. To use the document notes, the user must also have Document handling activated in the user options.


## Select a quality order
1. Go to Quality orders.
2. In the list, mark the selected row.
    * Select the quality order that was created from the "Inspect the quality of goods" task recording.  

## Create a nonconformance
1. Click Inquiries.
2. Click Non conformances.
3. Click New.
4. In the Problem type field, click the drop-down button to open the lookup.
    * Select the problem that was found during the inspection process.  
5. In the Problem type field, click the drop-down button to open the lookup.
6. In the list, find and select the desired record.
7. In the list, click the link in the selected row.
8. Click OK.

## Approve/reject a nonconformance
1. Click Functions.
2. Click Approve non conformance.
    * For this example, approve the nonconformance. Approved nonconformances can be associated with related operations to record work that is done as part of the nonconformance handling and, as in this task recording, the processing of correction handling.  
3. Click Yes.

## Create a correction action
1. Click Corrections.
2. Click New.
3. In the list, mark the selected row.
4. In the Personnel number field, click the drop-down button to open the lookup.
5. In the list, click the link in the selected row.
6. Click Select.
7. Click Attach.
    * Create a note about the correction. For this example, the action is to contact the vendor to discuss the nonconformance case.  
8. Click New.
9. Click Note.
    * Note that, depending on the report setup, different document types can be printed on the reports that are related to nonconformance management.  
10. In the Description field, type a value.
11. Close the page.

## Maintain a correction
1. Click Mark complete.
2. Click OK.
3. Close the page.

## Close a nonconformance
1. Click Functions.
2. Click Close non conformance.
3. Click Yes.
4. Close the page.
5. Close the page.
