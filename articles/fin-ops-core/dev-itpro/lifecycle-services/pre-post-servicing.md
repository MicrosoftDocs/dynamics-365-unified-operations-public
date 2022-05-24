---
# required metadata

title: Pre- and post-servicing information
description: This template contains examples of Markdown syntax, as well as guidance on setting the metadata.
author: matapg007
ms.date: 05/19/2022
ms.topic: article
audience: ADeveloper, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: matgupta
ms.search.validFrom: 2022-05-19

---

# Pre- and post-servicing information

[!include[banner](../includes/banner.md)]

This topic explains new changes introduced to the servicing process.  

Microsoft has introduced new steps in pre-servicing and post-servicing that enables DB sync precheck and index creation on tables out of offline servicing. This means the environment will be up and running, accessible to perform regular activities but it cannot service as all servicing operations are restricted during pre-servicing and post-servicing. The main benefit of the change is to help reduce the overall servicing downtime. 

## Pre-servicing

For service updates, Db sync precheck will run once the servicing operation is triggered and status in the LCS dashboard will show the environment state as **Pre-servicing**. This means the environment will be online and accessible during this time, but no other service operation allowed.

DB Sync precheck helps to identify the pre-defined set of errors that will cause the servicing to fail. Precheck failure will immediately trigger a soft rollback (no PITR) and env will be brought back to deployed state. From the environment history logs, precheck errors can be fetched to apply the required mitigation before re-triggering the update.

Once pre-servicing succeeds, the environment state will change to **Servicing** where the system goes offline and remains inaccessible until state changes to **Post-servicing**. 

## Post-servicing

While the post-processing step is occurring, the LCS dashboard will show **Post-servicing** after offline servicing is completed. During this time, the index creation and modification that are not done during offline servicing steps will be done in online mode. The environment will be accessible so that users can perform regular activities, but performance on the package changes that are involved might be degraded. During post-servicing, users won't be able to cancel or trigger new service requests. There is option to download the logs to check the process.

If any failure occurs during the post-processing step, the LCS dashboard will display post-servicing failed. The environment will still be accessible so that users can perform regular activities, but performance might be degraded. If you experience that the issue is not resolved in 24 hours, then contact Microsoft Support.

## Recommended best practices for servicing custom packages to reduce downtime 

We recommend restricting table schema changes to support schema synchronization in online mode. All operations below require either index to be dropped and recreated which is not supported in online mode. 

### Field property changes

- 'Size' property decrease for String type field 
- 'Scale'property changes for Real Number type field 
- 'Size' property changes from '(Memo)' to 'n' (some fixed size) or vice versa in String type field 

### Index-related changes

- Changing 'Primary Index' property of a table 
- Changing 'Clustered Index' property of a table 
- Adding or removing fields from ColumnStore Index 
- Adding or removing fields from Primary Index 

## FAQs

### What are the most common failures that can cause pre-servicing failure? 

Below are some common errors that could cause pre-servicing to fail, and we recommend reviewing environment history logs before re-triggering the update again. 

- The CREATE UNIQUE INDEX statement terminated because of a duplicate key 
- Please drop the original field, sync the table 
- Extension cannot be applied to the base element 
- Is missing the following dependencies 
- Database storage quota about to exceed 



