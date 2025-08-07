---
title: Cube audit in Business performance planning 
description: Learn how to audit cubes in Business performance planning.
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

Business performance planning includes a built-in cube audit tracking capability that delivers visibility into recent changes made during planning. Available in the Power BI Matrix visual, this feature provides an inline tooltip experience for user-driven changes and supports export of recent audit logs. This helps improve governance, collaboration, and limited transparency, especially in multi-user planning and writeback workflows.

## Prerequisites

### Required versions
The audit tracking feature is available beginning in these versions:
- Business performance planning app version: 1.13.03109.3
- Power BI Matrix visual version: 1.13.03109.3

If you don't see the tooltip or audit export options, confirm your environment is using the correct app and visual versions.

To enable the audit tracking feature, follow these steps:
1. **Environment-level audit**: In the Power Platform admin center, turn on auditing in Dataverse for the environment where Business performance planning is installed. 
2. **Table-level audit**: In the Maker Portal, go to the Cube table. Select **Edit table** > **Properties**. Select the **Audit changes to its data** checkbox.
3. **Cube-level audit in Business performance planning**: In Business performance planning, go to **Cubes**. Select a Cube and then select the **Enable auditing** toggle.

All three levels must be enabled for audit tracking to function. If any of them is skipped, the tooltip and export won't reflect changes.

### Audit tracking feature capabilities 
The current release of the audit tracking feature in Business performance planning captures:
- A tooltip on the Power BI Matrix visual that displays:
  - The most recent change made to a cell.
  - Who made the change.
  - When the change occurred.
  - The previous and new value (if available at that level).
- An Excel export option allows users to download the last 10,000 audit entries.

### Limitations
The cube audit features have the following limitations:
- The feature doesn't track action type. 
- Changes are made at granular levels and aren't rolled up. 

### Key benefits 
Some benefits of the cube audit feature are:
- View audit info inline in Power BI using a Matrix tooltip.
- Export up to 10,000 recent audit entries to Excel for offline analysis.
- Offers non-admin access to audit trail compared to Dataverse audit logs.
- The audit feature consumes audit storage and not database storage.

### Access audit tracking
To access audit tracking, follow these steps:
1. In Power BI Matrix visual, hover over a cell to display the tooltip with the last recorded change.
2. The tooltip displays: 
   - User
   - Timestamp
   - Previous value (if tracked at that level)
   - New value

> [!Note]
> If the last change was made at a more detailed level, the tooltip displays: "Can’t show previous value here. This number was changed at a lower level. To view the previous value, drill down to a lower granularity."
>
> Changes across hierarchical levels aren't reconciled. Displaying a previous value at the rolled-up level could be misleading if the change was made at a more detailed level.

### Export audit logs
To export audit logs, follow these steps:
1. In Business performance planning, go to the cube to export audit logs.
2. In the ribbon menu, select **Export**.
3. Select **Export audit history**. This generates an Excel file containing the last 10,000 recorded changes for that cube.

The export includes details such as:
- Audit ID
- Object ID
- Date and time
- Dimension combination
- Previous value
- New value


### Security and governance
- Audit logs are stored in secure Dataverse audit log tables.
- Logs are immutable.
- Only users with specific roles (BPPAdmin, Contributor, Viewer, and so on) can view logs of the data they have access to.
- Audit tracking can be toggled on/off by administrators.



### Additional resources
To learn more about audit capabilities in Power Platform and Dataverse, see the following:
- [Auditing overview](/power-apps/developer/data-platform/auditing/overview)
- [Microsoft Dataverse and model-driven apps activity logging](/power-platform/admin/enable-use-comprehensive-auditing?tabs=new)
- [Retrieve the history of audited data changes](/power-apps/developer/data-platform/auditing/retrieve-audit-data?tabs=webapi)
