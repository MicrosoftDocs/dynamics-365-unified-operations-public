---
# required metadata

title: Kanban transfer board support for bar code scanners
description: The Kanban transfer board supports scanner input from a widget bar code scanner to Select, Start, Complete, and Empty a kanban job.
author: johanhoffmann
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: KanbanBoardTransferJob
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: a426f645-d59b-4c98-8d78-eba8d64a562e
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: johanho
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Kanban transfer board support for bar code scanners

[!include [banner](../includes/banner.md)]

The Kanban transfer board supports scanner input from a widget bar code scanner to Select, Start, Complete, and Empty a kanban job.

## Registration modes

On the **Scanner registration** FastTab you can select the registration mode, which controls the action when you scan a kanban card number or manually type the number in the Kanban card number field.

| Set registration mode | Description                                                                                     |
|-----------------------|-------------------------------------------------------------------------------------------------|
| Start                 | Registers a Kanban transfer job as in progress.                                                 |
| Complete              | Registers a Kanban transfer job as completed.                                                   |
| Empty                 | Registers the material handling unit that is referenced by a Kanban card as empty.              |
| Select                | Registers a Kanban card number and automatically selects the referenced job in the Kanban list. |

 
## Registration mode Select

When you use a bar code reader to select a job, the display mode of the kanban board changes. In this mode, the following conditions apply:

-   Only the scanned kanban job is displayed.
-   The details of the selected job are displayed in the **Details** FastTab.
-   The **Messages** FastTab displays messages only for the selected job.
-   You can change the status of the job by using the functions that are available on the Action Pane. The Kanban transfer board continues to display only a single job during this time.
-   You can update the information in the list of jobs manually by clicking **Refresh** (Shift+F5) on the Action Pane. After you refresh the information, the full results for the job filter are displayed again.

## Job status and possible actions
The status of the selected job and the status of any pegged jobs for event kanbans, determine whether you can process the job further. The following table displays information about these statuses and tasks:
-   The statuses that are available for jobs, or for the handling units that are referenced by the jobs.
-   Each task that you can perform for the job.

<table>
<colgroup>
<col width="12%" />
<col width="12%" />
<col width="12%" />
<col width="12%" />
<col width="12%" />
<col width="12%" />
<col width="12%" />
<col width="12%" />
</colgroup>
<thead>
<tr class="header">
<th>Job type</th>
<th>Job status or handling unit status</th>
<th>Update picking list</th>
<th>Start</th>
<th>Update registration</th>
<th>Complete</th>
<th>Empty</th>
<th>Create event kanbans</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Transfer</td>
<td><ul>
<li>Not planned</li>
<li>No pegged jobs, or pegged jobs are Completed</li>
</ul></td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>Yes</td>
<td>No</td>
<td>Yes</td>
</tr>
<tr class="even">
<td>Transfer</td>
<td><ul>
<li>Not planned</li>
<li>The pegged job is not Completed</li>
</ul></td>
<td>Yes</td>
<td>No</td>
<td>Yes</td>
<td>No</td>
<td>No</td>
<td>No</td>
</tr>
<tr class="odd">
<td>Transfer</td>
<td>In progress</td>
<td>Yes</td>
<td>No</td>
<td>Yes</td>
<td>Yes</td>
<td>No</td>
<td>No</td>
</tr>
<tr class="even">
<td>Transfer</td>
<td>Completed</td>
<td>No</td>
<td>No</td>
<td>No</td>
<td>No</td>
<td>Yes</td>
<td>No</td>
</tr>
<tr class="odd">
<td>Transfer or process</td>
<td>Empty</td>
<td>No</td>
<td>No</td>
<td>No</td>
<td>No</td>
<td>No</td>
<td>No</td>
</tr>
<tr class="even">
<td>Transfer or process</td>
<td>A kanban card is not found</td>
<td>No</td>
<td>No</td>
<td>No</td>
<td>No</td>
<td>No</td>
<td>No</td>
</tr>
<tr class="odd">
<td>Transfer or process</td>
<td>A kanban card is found, but it is not assigned to a kanban</td>
<td>No</td>
<td>No</td>
<td>No</td>
<td>No</td>
<td>No</td>
<td>No</td>
</tr>
<tr class="even">
<td>Process</td>
<td><ul>
<li>Not planned</li>
<li>Prepared</li>
<li>In progress</li>
</ul></td>
<td>No</td>
<td>No</td>
<td>No</td>
<td>No</td>
<td>No</td>
<td>No</td>
</tr>
<tr class="odd">
<td>Process</td>
<td>Completed</td>
<td>No</td>
<td>No</td>
<td>No</td>
<td>No</td>
<td>No</td>
<td>No</td>
</tr>
</tbody>
</table>







[!INCLUDE[footer-include](../../includes/footer-banner.md)]