---
# required metadata

title: Create and process a conformance
description: This topic explains how to perform nonconformance management, based on an existing quality order.
author: perlynne
manager: tfehr
ms.date: 08/07/2019
ms.topic: business-process
ms.prod:  
ms.service: dynamics-ax-applications
ms.technology:  

# optional metadata

# ms.search.form:   
audience: Application User
# ms.devlang:  
ms.reviewer: kamaybac
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

[!include [banner](../../includes/banner.md)]

This topic explains how to perform nonconformance management, based on an existing quality order. You can run this recording in the USMF demo company and can use the suggested values. Typically, this procedure is performed by a quality clerk.  As a prerequisite, complete the instructions in [Inspect the quality of goods](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/master/articles/supply-chain/inventory/tasks/inspect-quality-goods.md). To process the approval of a nonconformance, the user who runs the task recording must have a "Name" value assigned on the Users page. To use the document notes, the user must also have Document handling activated in the user options.


## Select a quality order
1. In the navigation pane, go to **Modules > Inventory management > Periodic tasks > Quality management > Quality orders**.
2. In the list, select the quality order that was created in [Inspect the quality of goods](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/master/articles/supply-chain/inventory/tasks/inspect-quality-goods.md).  

## Create a nonconformance
1. In the action pane, select **Inquiries**.
2. Select **Non conformances**.
3. Select **New**.
4. In the drop-down menu of the **Problem type** field, select the problem that was found during the inspection process.  
5. Select **OK**.

## Approve/reject a nonconformance
1. Select **Functions**.
2. Select **Approve non conformance**. For this example, approve the nonconformance. Approved nonconformances can be associated with related operations to record work that is done as part of the nonconformance handling and, as in this topic, the processing of correction handling.  
3. Select **Yes**.

## Create a correction action
1. Select **Corrections**.
2. Select **New**.
3. In the **Personnel number** field of the new row, select the desired record from the drop down menu.
4. Click **Select**.
5. Select **Attach**. Create a note about the correction. For this example, the action is to contact the vendor to discuss the nonconformance case.  
6. Select **New**.
7. Select **Note**. Depending on the report setup, different document types can be printed on the reports that are related to nonconformance management.  
8. In the **Description** field, type a value.
9. Close the page.

## Maintain a correction
1. Select **Mark complete**.
2. Select **OK**.
3. Close the page.

## Close a nonconformance
1. Select **Functions**.
2. Select **Close non conformance**.
3. Select **Yes**.
4. Close the pages.
