---
# required metadata

title: Reset Dataverse synchronization
description: This article describes how to troubleshoot records that don't synchronize correctly between Microsoft Dynamics 365 Human Resources and the Human capital management (HCM) Common solution in Microsoft Dataverse.
author: jaredha
ms.date: 05/13/2026
ms.topic: how-to
# optional metadata

# ms.search.form: BatchJob, BatchJobEnhanced
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2021-09-27
ms.dyn365.ops.version: Platform update 42
---

# Reset Dataverse synchronization

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

## Issue

Records aren't synchronized between Microsoft Dynamics 365 Human Resources and the entities in the Human capital management (HCM) Common solution in Microsoft Dataverse. For more information about synchronization, go to [Configure Dataverse integration](hr-admin-integration-common-data-service.md). Failure to synchronize correctly can occur when the **Dataverse integration retry** or **Dataverse integration missed request sync** batch jobs are stuck in an **Executing** state.

## Resolution

When the **Dataverse Integration retry** or **Dataverse integration missed request sync** batch jobs are stuck in an **Executing** or **Canceling** state, you can reset the status. This can be done by canceling the batch job by following the guidance in [Reset stuck batch jobs](hr-admin-troubleshooting-batch-execution.md). After you cancel the batch job, you can reset the batch job by setting it to a **Waiting** status. The batch job will then run during the next scheduled run time.

1. If you didn't already, enable the **Enhanced batch abort** feature in **Feature management**.
   1. Go to the **Feature management** page (**System administration** > **Summary** > **Feature management**).
   1. Select the **All** tab.
   1. Select the **Feature name** column and filter by **Enhanced batch abort**.
   1. Select the **Enable** action if it's not already enabled.

1. Turn off the Dataverse integration.
   1. Go to the **Microsoft Dataverse integration** page (**System administration** go to **Links** > **Integrations** > **Dataverse configuration**).
   1. Set **Enable Dataverse integration** to **No**.

1. Cancel the **Dataverse integration retry** batch job.
   1. Go to the **Batch jobs** page (**System administration** go to **Links** > **Batch jobs** > **Batch jobs**).
   1. Filter the **Job description** column by **Integration**.
   1. Select the **Dataverse integration retry** batch job.
   1. On the action ribbon, select **Batch Job**, **Force cancel**, and then select **Yes** to confirm.

   > [!NOTE]
   > Depending on when the integration was first enabled, the batch job may have the description **Common Data Service integration retry**. Select this batch job if it's listed, instead of the **Dataverse integration retry** batch job.

1. Delete all Dataverse integration batch jobs.
   1. On the **Batch jobs** page, select the **Dataverse integration missed request sync**, **Dataverse integration retry**, and **Dataverse integration initial sync** batch jobs.
   1. On the action ribbon, select the **Change status** action. 
   1. Select **Withhold**, and select **OK**.
   1. On the action ribbon, select the **Delete** action, and then select **Yes** to confirm the action.

1. Turn on the Dataverse integration batch jobs.
   1. Go to the **Microsoft Dataverse integration** page (**System administration** > **Links** > **Integration** > **Dataverse configuration**).
   1. Set **Enable Dataverse integration** to **Yes**.

1. Go to the **Batch jobs** page and confirm that the **Dataverse integration retry** and **Dataverse integration missed request sync** batch jobs are created.

With the batch jobs recreated, you can now monitor the **Dataverse integration retry** batch job to see how long the job takes to execute. You can then verify that the records are synchronizing correctly to the HCM Common solution in Microsoft Dataverse.

## See also

[Configure Dataverse integration](hr-admin-integration-common-data-service.md)<br>
[Reset stuck batch jobs](hr-admin-troubleshooting-batch-execution.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
