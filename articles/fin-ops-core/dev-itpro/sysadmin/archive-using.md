---
title: Work with the Archive workspace
description: This article describes how to use the archive processes.
author: alexeiantao
ms.author: alexeiantao
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 06/01/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Work with the Archive workspace

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!--KFM: This topic seems to repeat the info we provide in the record-specific topics fro SO and GL. I think we should expand the other two topics to include the reverse operation and then remove this topic.-->

## Job Scheduling

After the features have been enabled, you will find the workspace named **Archive** to schedule archive/reversal jobs and view historical data already moved.

From the Archive dropdown button, select the appropriate automation job for archive you wish to schedule.  For example, to archive general ledger data, select LedgerArchiveAutomation.

Pressing the Archive button will display the schedule wizard for the ledger archive process automation. Enter a name and optional description before setting the schedule time to run.

You can also schedule an "occurrence runtime limit" to define the total amount of time an archive job runs in a day. If an archive job does not finish executing within the occurrence runtime limits, the job will be paused and picked up at the next execution occurrence.

## Progress results and logs

Once an archive job is scheduled and running, the progress and log information can be viewed by pressing the 'View Results' button. Additional details can be found by viewing the detailed logs.  

## Reverse an archive job

To reverse a job, select the reverse button from the workspace with the archive job selected you intend to reverse. A dialog will appear requesting the start time for the reverse job to begin. After entering a start time and pressing OK, a message will appear verifying your approval to proceed.
