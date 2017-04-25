---
# required metadata

title: Mass hire projects
description: Mass hire projects allow human resources specialists to create multiple positions and efficiently hire workers into those positions.
author: twheeloc
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: HRMMassHireProject
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 7481
ms.assetid: 5f5eb271-76eb-4305-bd1c-5d171dafccc9
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Mass hire projects

[!include[banner](includes/banner.md)


Mass hire projects allow human resources specialists to create multiple positions and efficiently hire workers into those positions.

Overview
--------

Use mass hire projects when you hire multiple workers at one time, such as when you hire to meet a seasonal demand. Creating a mass hire project is useful because you can create position records, worker records, and worker assignments for positions at the same time. When you create positions for a mass hire project, you can specify the following information:
-   The number of positions to create
-   The worker type of the people that you will hire for the positions
-   The department and the job that are associated with the positions
-   The full-time equivalent value of the position

## Example
In the summer, you usually hire 15-20 part-time college students to fill available internships in your company. This year, you want to hire five accountants, five order processors, and five cashiers. Instead of creating each position record and worker record separately, you create one mass hire project called “SummerInterns”. The project start and end dates correlate with the start and end dates of the position durations for the positions you create for the mass hire project. 

In the **Mass hire projects** page, select the “SummerInterns” project and then click **Open project**. In the open mass hire project, click **Create positions** and enter information about the accountant position. You can indicate that five accountant positions should be created using the same information for each one, and then click OK. Repeat this process for the order processor and cashier positions. 

After selecting students to hire for the internship positions, you'll enter each student’s information in the **Position details** for the position that you're hiring them for. When you have entered all of the position details, select the position in the Mass hire projects page, and then click **Hire**. A position record will be created for each position and a worker record will be created and assigned to the correct position for each person who you hire.

## Mass hire project statuses
A mass hire project can have the following statuses.
-   Created
-   Open
-   Closed

On the **Mass hire project** page, click **Open project** or **Close project** to change the status of a mass hire project. The following table describes what you can do with a project according to its status.

<table>
<thead>
<tr class="header">
<th>Status</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Created</td>
<td>You can create and modify information, but cannot create positions for the project. This is the default status for new projects.</td>
</tr>
<tr class="even">
<td>Open</td>
<td>You can modify the project details, create positions for the mass hire project, and hire people for the positions. This is the status for active projects.</td>
</tr>
<tr class="odd">
<td>Closed</td>
<td>You cannot add positions to the project. To add positions to the mass hire project, open the project again. This is the status for completed projects.
<div class="alert">
<table>
<thead>
<tr class="header">
<th><strong>Note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Before you can close a mass hire project, all positions in the project must have a status of either Created or Closed.</td>
</tr>
</tbody>
</table>
</div></td>
</tr>
</tbody>
</table>

 




