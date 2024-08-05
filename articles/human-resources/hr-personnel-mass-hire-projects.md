---
# required metadata

title: Mass hire projects
description: This article describes mass hire projects, which allow human resources specialists to create multiple positions and efficiently hire workers into those positions.
author: twheeloc
ms.date: 07/02/2024
ms.topic: article
# optional metadata

ms.search.form: HRMMassHireProject, HcmPersonnelManagementWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 5f5eb271-76eb-4305-bd1c-5d171dafccc9
ms.search.region: Global
# ms.search.industry: 
ms.author: anisagrawal
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Mass hire projects

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

Mass hire projects allow human resources specialists to create multiple positions and efficiently hire workers into those positions.

## Overview

Use mass hire projects when you hire multiple workers at one time, such as when you hire to meet a seasonal demand. Creating a mass hire project is useful because you can create position records, worker records, and worker assignments for positions at the same time. When you create positions for a mass hire project, you can specify the following information:

- The number of positions to create
- The worker type of the people that you will hire for the positions
- The department and the job that are associated with the positions
- The full-time equivalent value of the position

## Example

In the summer, you usually hire 15-20 part-time college students to fill available internships in your company. This year, you want to hire five accountants, five order processors, and five cashiers. Instead of creating each position record and worker record separately, you create one mass hire project called "SummerInterns". The project start and end dates correlate with the start and end dates of the position durations for the positions you create for the mass hire project.

On the **Mass hire projects** page, select the **SummerInterns** project, and then select **Open project**. In the open mass hire project, select **Create positions**, and enter information about the accountant position. You can indicate that five accountant positions should be created and that the same information should be used for each one. Then select **OK**. Repeat this process for the order processor and cashier positions.

After you select students to hire for the internship positions, you will enter each student's information in the position details of the position that you're hiring them for. When you've entered all the position details, select the position on the **Mass hire projects** page, and then select **Hire**. A position record will be created for each position, and a worker record will be created and assigned to the correct position for each person that you hire.

## Mass hire project statuses

A mass hire project can have the following statuses.

- Created
- Open
- Closed

On the **Mass hire project** page, select **Open project** or **Close project** to change the status of a mass hire project. The following table describes what you can do with a project according to its status.

<table>
<thead>
<tr>
<th>Status</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Created</td>
<td>You can create and modify information, but can't create positions for the project. This is the default status for new projects.</td>
</tr>
<tr>
<td>Open</td>
<td>You can modify the project details, create positions for the mass hire project, and hire people for the positions. This is the status for active projects.</td>
</tr>
<tr>
<td>Closed</td>
<td><p>You cannot add positions to the project. To add positions to the mass hire project, open the project again. This is the status for completed projects.</p>
<p><strong>Note:</strong> Before you can close a mass hire project, all positions in the project must have a status of either <b>Created</b> or <b>Closed</b>.</p>
</td>
</tr>
</tbody>
</table>


[!INCLUDE[footer-include](../includes/footer-banner.md)]
