---
title: Cube audit in Business performance planning 
description: Learn how to use audit cubes in Business performance planning.
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

# Audit cubes in Business performance planning 

Business performance planning includes a built-in cube audit tracking capability that delivers visibility into recent changes made during planning. Available in the Power BI Matrix visual, this feature provides
an inline tooltip experience for user-driven changes and supports export of recent audit logs.
This helps improve governance, collaboration, and limited transparency, especially in multi-user planning and writeback workflows.

## Prerequisites

### Required versions
The audit tracking feature is available starting with these versions:
 - Business performance planning app version: 1.13.03109.3
 - Power BI Matrix visual version: 1.13.03109.3
If you don't see the tooltip or audit export options, ensure your environment is using the correct app and visual versions.

To enable the audit tracking feature, you must enable three levels of audit toggles:
1.	Environment-level audit toggle
Turn on auditing in Dataverse (via Power Platform Admin Center), enable auditing for the environment where Business performance planning is installed. This step is required to allow auditing functionality in
Dataverse.
Manage Dataverse auditing – Microsoft Learn
2.	Table-level audit toggle
In the Maker Portal, navigate to the Cube table:
Click Edit Table
Go to the Properties pane
Enable the checkbox "Audit Changes to Its Data"
3.	Cube-level audit toggle in the BPP App
Within the Business performance planning application, Go to Cubes page, Select a Cube, Use the “Enable auditing” toggle to activate tracking for this Cube.

All three levels must be enabled for audit tracking to function. If any of them is skipped, the tooltip and export will not reflect changes.

### Audit tracking feature capabilities 
The current release of the audit tracking feature in Business performance planning captures:
 - A tooltip on the Power BI Matrix visual that displays:
    - The most recent change made to a cell
    - Who made the change
    - When the change occurred
    - The previous and new value (if available at that level)
•	An Excel export option that allows users to download the last 10,000 audit entries

### Limitations
 - The feature doesn't track action type (e.g., whether the change was due to manual input, or allocation)
 - Changes made at granular levels are not rolled up — tooltips at higher levels may show stale or misleading information

### Key benefits 
 - View audit info inline in Power BI via Matrix tooltip
 - Export up to 10,000 recent audit entries to Excel for offline analysis
 - Offers non-admin access to audit trail compared to Dataverse audit logs
 - The Audit feature consume Audit storage and not Database storage

### Access audit tracking
In Power BI Matrix Visual:
•	Hover a cell to display tooltip with last recorded change
•	Tooltip will show:
o	User
o	Timestamp
o	Previous value (if tracked at that level)
o	New value
Note: If the last change was made at a more detailed level, the tooltip will display:
"Can’t show previous value here
This number was changed at a lower level. To view the previous value, drill down to a lower granularity."
Why this happens: The system currently does not reconcile changes across hierarchical levels. Displaying a previous value at the rolled-up level could be misleading if the change was made at a more detailed
level.

### Export audit logs
•	In the Business performance planning application, navigate to the cube for which you want to export audit logs.
•	In the ribbon menu, click on the Export dropdown.
•	Select the Export audit history option.
•	This action generates an Excel file containing the last 10,000 recorded changes for that cube.
The export includes details such as:
•	Audit ID
•	Object ID
•	Date and time
•	dimension combination
•	Previous value
•	New value

In Dataverse Admin Portal
Access the Audit Summary view (comprehensive list of all audit logs in the environment): Manage Dataverse auditing - Power Platform | Microsoft Learn

### Security and governance
•	Audit logs are stored in secure Dataverse Audit Log tables
•	Logs are immutable
•	Only users with specific roles (BPPAdmin, Contributor, Viewer, etc.) can view logs of the data they have access to
•	Audit tracking can be toggled on/off by admins

### Feedback and roadmap
We’re continuously improving this experience based on your feedback. Upcoming enhancements include:
•	Visual cell change highlighting
•	Tracking action types (e.g. splash, copy-paste, import)
•	Expand to other visuals and Excel Add-In 
•	Comment history and change trace
•	Copilot audit log queries
•	Advanced filtering and search
Let us know how you’re using audit tracking for cuve and what you'd like to see next!
Please visit the Idea Portal to submit your ideas.

### Additional resources
To learn more about audit capabilities in the Power Platform and Dataverse, see the following:
•	Auditing overview - Power Apps | Microsoft Learn 
•	Enable and configure auditing in Power Platform environments
•	Retrieve the history of audited data changes - Power Apps | Microsoft Learn
