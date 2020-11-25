---
# required metadata

title: Set up and use wave process method for Schedule work creation
description: This topic describes wave method processing using Schedule work creation.
author: perlynne
manager: mirzaab
ms.date: 12/01/2020
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: WHSPostMethod, WHSWavePostMethodTaskConfig, WHSWaveTemplateTable, WHSParameters, WHSWaveTableListPage, WHSWorkTableListPage, WHSWorkTable, BatchJobEnhanced, WHSPlannedWorkOrder

# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: 
ms.search.scope: Core, Operations
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: kamaybac
ms.search.validFrom: 2021-02-01
ms.dyn365.ops.version: 10.0.17

---

# Set up and use schedule work creation processes

[!include [banner](../includes/banner.md)]

**Schedule work creation** is used as part of the waving process and helps increase the wave processing throughput by having the system create work using parallel processing.

When the feature is enabled, you will create planned work, which the system will eventually process to create actual work. If the number of wave lines reaches the threshold parameter setting, the system will create actual work more quickly by applying parallel, asynchronous processing.


## Enable the Schedule work creation feature

### 1. Feature management

Before you can use the *Schedule work creation* feature, it must be turned on in your system. Admins can use the [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace to check the status of the feature and turn it on if it's required. There, the feature is listed in the following way:

- **Module:** *Warehouse management*
- **Feature name:** *Schedule work creation*

> [!NOTE]
> The feature **Organization-wide work blocking** must get enabled before **Schedule work creation**

### 2. Enable batch processing of waves

To create warehouse work based on a parallel asynchronously processing method the wave process must be running in batch.

1. Go to **Warehouse management > Setup > Warehouse management parameters**. 

2. On the **General** tab, set **Process waves in batch** to *Yes*. Optionally, you can also select a dedicated **Wave processing batch group** to optimize your batch queue processing from running at the same time as other processes.

3. Set the **Wait for lock (ms) time**, which is used when processing several waves at the same time. For most larger waving processes, we recommend a value of *60000*. 
 
### 3. Enable the new wave step method for existing wave templates 
First you need to get the new wave step method created and enabled for parallel asynchronously task processing.

1. Go to **Warehouse management > Setup > Waves > Wave process methods**. 

2. Select **Regenerate method** and note that *WHSScheduleWorkCreationWaveStepMethod* has been added to the list of wave process methods you can use in your shipping Wave templates. 

3. Set the **Method name** to *WHSScheduleWorkCreationWaveStepMethod* and select **Task configuration**.

4. In the **Task configuration** select **New** on the Action Pane to add a new row to the grid and make the following settings for it:

    - **Warehouse** - Select the warehouse you will use to schedule work creation processing. 
    - **Maximum number of batch tasks**  - Specify a maximum number of batch tasks. In most cases, this value shouldn't be larger than 16 (two times the number of supported cores). 
    - **Wave processing batch group** - Select a dedicated **Wave processing batch group** to optimize your batch queue processing.

Now you are ready to update a existing wave template (or create a new) using the **Schedule work creation** wave processing method.

5. Go to **Warehouse management > Setup > Waves > Wave templates**. 

6. Select **Edit** on the Action Pane. 

7. In the list pane, select the one you would like to update (such as demo data *24 Shipping default*). 

8. Expand the **Methods** FastTab and select the row with the **Name** *Schedule work creation* in the **Remaining methods** grid. 

9. Select the arrow pointing to the **Selected methods** column to move the selected row to that column. (You can only have one selected method at a time that uses either *WHSScheduleWorkCreationWaveStepMethod* or *createWork*, so the existing row with **Method name** *createWork* is automatically moved to the **Remaining methods** grid.) 

## Set wave task processing threshold data

The system will create default wave task processing threshold data the first time a wave process runs using any task-based processing. The data is used to control when wave processing will run asynchronously and task-based, which enables it to process and create work in parallel. The default data will initially use a threshold value of 15 for the minimum number of load lines (MINIMUMWAVELOADLINES). This means that when the system processes a wave with more than 15 loads lines, it will use asynchronous task processing. You can manually insert/update this data in the *WHSWaveTaskProcessingThresholdParameters* table in your testing environments, but in case you need to change this setting in a production environment you need to request the update via a support request.

# Working with the feature

When having the **Schedule work creation** feature enabled, wave processing will create planned work, which is the data used for the new work creation process. During the work creation process, the work will be in a blocking state using the **Organization-wide work blocking** feature.
![Schedule work creation](media/schedule-work-creation-process.png)
## Planned work

The **Warehouse management > Work > Planned work details** page shows the planned work information, which is initially created as part of the waving processing. The following **Process status** values are used:

- **Queued** - The planned work is waiting to be used to create work. 
- **Completed** - The planned work has been used to create the work. 
- **Failed** - The planned work has been used to create work, but the wave processing failed. Note that the created work remains in status **Cancelled**.

## Batch job for the work creation process 

You can view the batch jobs for processing waves by selecting **Batch jobs** on the **All waves** page.  

From here, you can view all the batch task details for each of the batch job IDs.