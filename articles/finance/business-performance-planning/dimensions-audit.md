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

Overview
Business Performance Planning (BPP) provides audit tracking for dimension data to enhance transparency, governance, and accountability during planning setup and master data management. This feature is available both in the BPP application (when viewing a dimension) and in the Table Edit visual within Power BI.
Users can review changes made to dimension records via a side panel showing who made the change, when it occurred, and what was modified.

🔧 Prerequisites
To enable dimension-level audit tracking, ensure the following configurations are in place:
1.	Environment-level auditing enabled
In the Power Platform Admin Center (PPAC), turn on auditing for the environment where BPP is installed.
2.	Table-level auditing enabled
In the Maker Portal, locate the dimension table (e.g., msdyn_xpnadim_product, msdyn_xpnadim_costcenter, etc.):
o	Click Edit Table
o	In the Properties pane, enable the checkbox "Audit Changes to Its Data"
3.	Dimension-level auditing enabled in BPP
In the BPP application, open the target dimension from the Dimension list, and ensure that audit tracking is turned on.
📌 All three levels must be active for the side panel to show audit logs.

🔧 What the Feature Does
This feature captures and displays:
•	Creation, update, and deletion of dimension records
•	The user who performed the action
•	The timestamp
•	Field-level changes (old value → new value)
Audit logs are available:
•	In the BPP App, when selecting a dimension record
•	In the Power BI Table Edit visual, in a right-side panel next to the editable grid
Users can:
•	Open the audit summary panel
•	See all changes chronologically from the most recent changes
•	Review field-level modifications in a structured format
•	Navigate the log using Filter function within the side panel

✅ Benefits
•	Clear traceability of who changed what and when
•	Improves data governance and audit readiness
•	Enables collaborative, transparent master data management
•	Allows troubleshooting and rollback validation for dimension record changes

⚠ Limitations
Limitation	Description
❌ No comment history	Commenting on dimension edits is not tracked or versioned
❌ No filtering or export	Currently, users cannot filter or export the dimension audit logs directly
❌ Only available per-row	Bulk audit viewing or search is not supported at this time

📍 Where to Access It
In the BPP Application:
•	Navigate to Dimensions
•	Select a dimension 
•	Click Audit Summary to open the right-side panel
•	You can use the Filter function to navigate the logs
In Power BI Table Edit Visual:
•	In the table Edit visual when connected to a dimension table
•	Click on Audit Summary
•	The Audit Log side panel appears on the right showing list of changes from most recent
•	You can use the Filter function to navigate the logs
🔐 Behind the Scenes
•	Dimension changes are written to the Dataverse audit tables
•	The side panel fetches and displays this data securely, scoped to the selected record
•	The experience is optimized for real-time visibility during planning or dimension editing workflows

Feedback & Roadmap
We’re continuously improving this experience based on your feedback. Upcoming enhancements include:
•	Export dimension audit log to Excel
•	Integration with comment history

Let us know how you’re using audit tracking for dimension and what you'd like to see next!
Please visit the Idea Portal to submit your ideas.

Additional Resources
To learn more about audit capabilities in the Power Platform and Dataverse, see the following:
•	Auditing overview - Power Apps | Microsoft Learn 
•	Enable and configure auditing in Power Platform environments
•	Retrieve the history of audited data changes - Power Apps | Microsoft Learn
