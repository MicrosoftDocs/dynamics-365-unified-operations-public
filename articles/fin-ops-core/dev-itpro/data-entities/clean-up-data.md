---
title: Clean up data management job history
description: This article describes how to clean up data management job history.
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 9/28/2023
ms.custom:

---

# Clean up data management job history

[!include [banner](../includes/banner.md)]

Starting September 2023, Data Management job history entries and related staging table data older than 90 days will be automatically deleted. To configure a job history retention period of less than 90 days,
customers can use **Job history cleanup**. 

## Clean up data

1. Go to **Data management** > **Job history cleanup**.
2. In the **Job history** pane, configure the **Number of days to retain history**, **Number of hours to execute the job**, and **Batch job recurrence** fields. 
3. To schedule the job to run regularly in the background, select the **Batch processing** field.
4. To define a recurrance, click **Recurrance** and select **No End Date** in the **Recurrence definition**.   

>[!Recommendation:]
>To clean large staging tables, an execution time of 6 hours with a batch recurrence of at least once per day is recommended.  

### Execution history cleanup batch error

If a job history cleanup batch job has already been scheduled, the existing batch job will need to be deleted before rescheduling a new recurrence.  
If you attempt to schedule a batch recurrence when one has already been scheduled will result in an error.   

To address this error:

1. Go to **System administration** > **Inquiries** > **Batch jobs**.
2. Search for the description **Job history cleanup**.
3. Delete batch jobs with a **Waiting** state.
4. If the batch job has a **Executing** state, you can either cancel it or **Remove recurrence**. **Remove recurraence** will remove the batch job schedule after the current cleanup execution completes.
5. After the job is either deleted or in an **Ended** state, create a new batch job recurrence.  

 
