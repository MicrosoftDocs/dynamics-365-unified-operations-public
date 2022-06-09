---
# required metadata

title: Pre-servicing and post-servicing
description: This article explains new changes that have been introduced for the servicing process.
author: matapg007
ms.date: 05/19/2022
ms.topic: article
audience: ADeveloper, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: matgupta
ms.search.validFrom: 2022-05-19

---

# Pre-servicing and post-servicing

[!include[banner](../includes/banner.md)]

This article explains new changes that have been introduced for the servicing process.

Microsoft has introduced new steps for servicing pipeline pre-servicing and post-servicing to enable database synchronization precheck and index creation on tables to occur outside offline servicing. Therefore, the environment remains up and running, and accessible so that users can perform regular activities. However, servicing can't be done, because all servicing operations are restricted during pre-servicing and post-servicing. The main benefit of the change is that it helps reduce the overall servicing downtime.

## Pre-servicing

For service updates, the pre-servicing step runs when the servicing operation is triggered. During this step, Microsoft Dynamics Lifecycle Services (LCS) shows the environment state as **Pre-servicing**. This status indicates that the environment is online and accessible, but no other service operations are allowed.

The pre-servicing step helps identify the predefined set of errors that will cause servicing to fail. Precheck failure immediately triggers a soft rollback, without point-in-time recovery (PITR), and the environment is brought back to a deployed state. By fetching precheck errors from the environment history logs, you can apply the required mitigation before you retrigger the update.

![Environment in Pre-servicing status in LCS.](https://user-images.githubusercontent.com/90061039/170361108-a669f070-5001-44b0-8e0b-81c5edca51cd.png)

When pre-servicing succeeds, the environment state is updated to **Servicing**. During the servicing step, the system goes offline and remains inaccessible until the environment state is updated to **Post-servicing**. After the servicing step is completed, email notifications are sent to environment admins.

## Post-servicing

While the post-processing step is occurring, after offline servicing is completed, LCS shows the environment state as **Post-servicing**. During this time, the index creation and modification that weren't done during offline servicing steps are done in online mode. The environment remains accessible so that users can perform regular activities. However, performance might be degraded for the changes that are involved in the update package. During post-servicing, users can't cancel existing service requests or trigger new service requests. There is an option that lets you download the logs to check the process.

![Environment in Post-servicing status in LCS.](https://user-images.githubusercontent.com/90061039/170360282-65acc76f-e7d9-4980-86c3-d8d9224fb08c.png)

If any failure occurs during the post-servicing step, LCS shows the environment state as **Post-servicing failed**. During this time, the environment remains accessible so that users can perform regular activities. However, performance might be degraded for the specific table where the index change failed. If the issue isn't resolved in 24 hours, contact Microsoft Support.

## Recommended best practices for reduced servicing downtime

We recommend that you restrict table schema changes to support faster schema synchronization. Eventually, this synchronization can be done online. All the schema change operations that are described in this section either require that an index be dropped and re-created, or require a considerable amount of downtime and therefore a longer servicing window.

### Field property changes

- The **Scale** property is changed for a field of the **Real Number** type.
- The **Size** property is changed from **(Memo)** to some fixed size *n*, or from some fixed size *n* to **(Memo)**, for a field of the **String** type.

### Index-related changes

- The **Primary Index** property of a table is changed.
- The **Clustered Index** property of a table is changed
- Fields are added to or removed from the columnstore index.
- Fields are added to or removed from the primary index.

## FAQ

### What are the most common errors that can cause pre-servicing to fail?

The following list shows some common errors that can cause pre-servicing to fail. We recommend that you review the environment history logs before you retrigger the update.

- The CREATE UNIQUE INDEX statement terminated because of a duplicate key.
- Please drop the original field, sync the table.
- Extension cannot be applied to the base element.
- Is missing the following dependencies.
- Database storage quota about to exceed.
