---
# required metadata

title: Reset Dataverse synchronization
description: This topic describes how to troubleshoot when records do not synchronize correctly with the HCM Common solution in Dataverse
author: jaredha
ms.date: 09/27/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: BatchJob, BatchJobEnhanced
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2021-09-27
ms.dyn365.ops.version: Platform update 42
---

# Reset Dataverse synchronization

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

## Issue

Records are not being synchronized between Microsoft Dynamics 365 Human Resources and the entities in the HCM Common solution in Microsoft Dataverse. Synchronization should occur as defined in the [Configure Dataverse integration](hr-admin-integration-common-data-service.md) documentation. Failure to synchronize correctly can occur when the **Dataverse integration retry** or **Dataverse integration missed request sync** batch job is stuck in **Executing** state.

## Resolution

When the **Dataverse Integration retry** or **Dataverse integration missed request sync** batch job is stuck in an **Executing** or **Canceling** state, you can reset the status by forcing the cancellation of the job using the functionality to [Reset stuck batch jobs](hr-admin-troubleshooting-batch-execution.md). After you cancel the batch job, you can reset the batch job by setting it to a **Waiting** status. It will then be picked up again for execution in the next scheduled batch run.

1. If you haven't done so already, enable the **Enhanced batch abort** feature in **Feature management**.
   1. Navigate to the **Feature management** form (System administration > Summary > Feature management).
   2. Select the **All** tab.
   3. Select the **Feature name** column and filter by **Enhanced batch abort**.
   4. Select the **Enable** action if it is not already enabled.

2. Turn off the Dataverse integration
   1. Navigate to the **Microsoft Dataverse integration** form (System administration > Links > Integration > Dataverse configuration).
   2. Set the **Enable Dataverse integration** toggle to **No**.

3. Cancel the **Dataverse integration retry** batch job.
   1. Navigate to the **Batch jobs** form (System administration > Links > Batch jobs > Batch jobs).
   2. Filter the **Job description** column by **Integration**.
   3. Select the **Dataverse integration retry** batch job.
   4. On the action ribbon, select the **Force cancel** action, and select **Yes** to confirm the action.

   > [!NOTE]
   > Depending on when the integraton was first enabled, the batch job may have the description **Common Data Service integration retry**. Select this batch job if it is listed rather than the **Dataverse integration retry** batch job.

4. Delete all Dataverse integration batch jobs.
   1. In the **Batch jobs** form, select the **Dataverse integration missed request sync**, **Dataverse integration retry**, and **Dataverse integration initial sync** batch jobs.
   2. On the action ribbon, select the **Change status** action. 
   3. Select **Withhold**, and select **OK**.
   4. On the action ribbon, select the **Delete** action, and select **Yes** to confirm the action.

5. Turn on the Dataverse integration batch jobs.
   1. Navigate to the **Microsoft Dataverse integration** form (System administration > Links > Integration > Dataverse configuration).
   2. Set the **Enable Dataverse integration** toggle to **Yes**.

6. Navigate to the **Batch jobs** form and validate that the **Dataverse integration retry** and **Dataverse integration missed request sync** batch jobs have been created.

With the batch jobs recreated, you can now monitor the **Dataverse integration retry** batch job to see how long the job takes to execute, and verify that the records are synchronizing correctly to the HCM Common solution in Microsoft Dataverse.

## See also

[Configure Dataverse integration](hr-admin-integration-common-data-service.md)<br>
[Reset stuck batch jobs](hr-admin-troubleshooting-batch-execution.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
