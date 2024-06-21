---
title: Pre-servicing and post-servicing
description: Learn about new changes that have been introduced for the servicing process, including outlines on preservicing, post-servicing, and best practices.
author: matapg007
ms.author: matgupta
ms.topic: article
ms.date: 12/19/2022
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2022-05-19
---

# Pre-servicing and post-servicing

[!include[banner](../../../finance/includes/banner.md)]

This article explains new changes that have been introduced for the servicing process.

Microsoft has introduced new steps for servicing pipeline preservicing and post-servicing to enable database synchronization precheck and index creation on tables to occur outside offline servicing. Therefore, the environment remains up and running, and accessible so that users can perform regular activities. However, servicing can't be done, because all servicing operations are restricted during preservicing and post-servicing. The main benefit of the change is it helps reduce the overall servicing downtime.

## Preservicing

For service updates, the preservicing step runs when the servicing operation is triggered. During this step, Microsoft Dynamics Lifecycle Services (LCS) shows the environment state as **Preservicing**. This status indicates that the environment is online and accessible, but no other service operations are allowed.

The preservicing step identifies the predefined set of errors that causes servicing to fail. Precheck failure immediately triggers a soft rollback, without point-in-time recovery (PITR), and the environment is brought back to a deployed state. By fetching precheck errors from the environment history logs, you can apply the required mitigation before you retrigger the update.

![Environment in preservicing status in LCS.](https://user-images.githubusercontent.com/90061039/170361108-a669f070-5001-44b0-8e0b-81c5edca51cd.png)

When preservicing succeeds, the environment state is updated to **Servicing**. During the servicing step, the system goes offline and remains inaccessible until the environment state is updated to **Post-servicing**. After the servicing step is completed, email notifications are sent to environment admins.

## Post-servicing

While the post-processing step is occurring, after offline servicing is completed, LCS shows the environment state as **Post-servicing**. During this time, the index creation and modification that weren't done during offline servicing steps are done in online mode. The environment remains accessible so that users can perform regular activities. However, performance might be degraded for the changes that are involved in the update package. During post-servicing, users can't cancel existing service requests or trigger new service requests. There's an option to download the logs to check the process.

![Environment in Post-servicing status in LCS.](https://user-images.githubusercontent.com/90061039/170360282-65acc76f-e7d9-4980-86c3-d8d9224fb08c.png)

If any failure occurs during the post-servicing step, LCS shows the environment state as **Post-servicing failed**. During this time, the environment remains accessible so that users can perform regular activities. However, performance might be degraded for the specific table where the index change failed. If the issue isn't resolved in 24 hours, contact Microsoft Support.

## Recommended best practices for reduced servicing downtime

We recommend that you restrict table schema changes to support faster schema synchronization. Eventually, this synchronization can be done online. All the schema change operations that are described in this section either require that an index be dropped and recreated, or require a considerable amount of downtime and therefore a longer servicing window.

### Field property changes

- The **Scale** property is changed for a field of the **Real number** type.
- The **Size** property is changed from **(Memo)** to some fixed size *n*, or from some fixed size *n* to **(Memo)**, for a field of the **String** type.

### Index-related changes

- The **Primary Index** property of a table is changed.
- The **Clustered Index** property of a table is changed
- Fields are added to or removed from the columnstore index.
- Fields are added to or removed from the primary index.

### Common failures
This section provides troubleshooting and mitigation guidance for the most common issues faced during preservicing or that are caused due to custom integrations. We recommend reviewing the logs of a service action from the environment's Lifecycle Services portal. Go to the environment history and select target service action to download the logs. After you download the logs, in zip format containing multiple files, locate the file that starts with “dbsyncadhoc_precheck_error”. This file provides precheck failure logs. If there are multiple files with the same name, select any one for troubleshooting.

Precheck servicing may fail due to various reasons. Below are few common generic patterns commonly faced. If you see any of the below errors in the error file, the servicing deployment won't succeed unless either the package or database issues are fixed. See below most common reason of failures and recommended actions to perform before retrying servicing.

- Error message contains **"Database execution failed: The CREATE UNIQUE INDEX statement terminated because a duplicate key was found for the object name 'Table name' and the index name 'Index name' ".** This error occurs when a user attempts to create a unique index, but more than one row in the table contains duplicate values. If there are duplicates, the Dbsync fails and the error logs contain the details about the failed index.

**Recommended action:** Connect to the environment's database axDB and remove duplicate values in the unique index columns from [table name] found in error logs and the retry.

- Error message contains **"Package deployment failed with error like 'Converting Field XXX of Type 'AxTableFieldXXX' to 'AxTableFieldXXX' is not supported. Drop the original field, sync the table and add new field with same name if needed'**. This error occurs when a user creates a table and changes the column type to one that isn't supported. 
 
**Recommended action:** Specific field type conversion isn't supported and the table in question is a customer created table. We recommend fixing it by converting the field type to the original type and then retry the servicing.

- Error Message contains **“The enum value ‘XXX’ on the extension ‘YYY.ZZZ’ already exists. This extension can't be applied to the base element.”** This error occurs if an ISV or a user has added an enumeration value to an extensible enum, and then a subsequent addition to the same extensible enumeration with the same name from the Microsoft-shipped application collides with it. The naming guidelines require that ISV and customer extensions are prefixed in order to avoid this type of collision. For more information, see [Naming guidelines for extensions](../../dev-itpro/extensibility/naming-guidelines-extensions.md#naming-model-elements).

**Recommended action:** If it does occur, the only workaround is to rename the customer or ISV enumeration value to follow naming guidelines and not collide with the new application value.
 
## FAQ

### What are the most common errors that can cause pre-servicing to fail?

The following list shows some common errors that can cause pre-servicing to fail. We recommend that you review the environment history logs before you retrigger the update.

- The CREATE UNIQUE INDEX statement terminated because of a duplicate key.
- Please drop the original field, sync the table.
- Extension cannot be applied to the base element.
- Is missing the following dependencies.

