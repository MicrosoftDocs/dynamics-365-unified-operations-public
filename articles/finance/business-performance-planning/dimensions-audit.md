---
title: Dimensions audit in Business performance planning 
description: Learn how to audit dimensions in Business performance planning.
author: ShielaSogge
ms.author: twheeloc
ms.topic: how-to
ms.date: 07/10/2025
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-12-03
ms.search.form: 
ms.dyn365.ops.version: 
---

# Audit dimensions in Business performance planning 

Business performance planning  provides audit tracking for dimension data to enhance transparency, governance, and accountability during planning setup and master data management. This feature is available both in Business performance planning and in the Table edit visual within Power BI. Users can review changes made to dimension records via a side panel showing who made the change, when it occurred, and what was modified.

## Prerequisites
To enable dimension-level audit tracking, ensure the following configurations are in place:
1.	Environment-level audit - In the Power Platform Admin Center, turn on auditing in Dataverse for the environment where Business performance planning is installed. 
2.	Table-level audit - In the Maker Portal, go to the Cube table. Click **Edit table** > **Properties**. Select the **Audit changes to its data** checkbox.
3.	Dimension-level auditing enabled in Business performance planning - In Business performance planning, open the target dimension from the Dimension list, and ensure that audit tracking is turned on.
All three levels must be active for the side panel to show audit logs.

### Audit tracking feature capabilities 
The current release of the audit tracking feature in Business performance planning captures:
 - Creation, update, and deletion of dimension records
 - The user who performed the action
 - The timestamp
 - Field-level changes

To view the audit logs, go to:
 - In Business performance planning, select a dimension record.
 - In Power BI Table edit visual, in the right-side panel next to the editable grid.

Users open the audit summary panel:
 - See all changes chronologically from the most recent changes
 - Review field-level modifications in a structured format
 - Go the log using the **Filter** function within the side panel

### Benefits
Benefits of the audit feature are:
 - Clear traceability of who changed what and when
 - Improves data governance and audit readiness
 - Enables collaborative, and transparent master data management
 - Allows troubleshooting and rollback validation for dimension record changes

### Limitations
Some limitations of the audit tracking feature are:
 - Comments on dimension edits isn't tracked or versioned
 - Users can't filter or export the dimension audit logs directly
 - Only available per-row	Bulk audit viewing or search isn't supported 

### Access the audit feature
To access the audit feature, follow these steps:
1. In Business performance planning, go to **Dimensions**.
2. Select a dimension.
3. Click **Audit Summary** to open the right-side panel.
4. Use the **Filter** function to navigate the logs.

In Power BI Table edit visual, click **Audit summary**.
 - The Audit Log side panel displays a list of changes from the most recent change.
 - Use the **Filter** function to navigate the logs.
 - Dimension changes are written to the Dataverse audit tables
 - The side panel fetches and securely displays the data, scoped to the selected record
 - The experience is optimized for real-time visibility during planning or dimension editing workflows



Additional Resources
To learn more about audit capabilities in the Power Platform and Dataverse, see the following:
•	Auditing overview - Power Apps | Microsoft Learn 
•	Enable and configure auditing in Power Platform environments
•	Retrieve the history of audited data changes - Power Apps | Microsoft Learn
