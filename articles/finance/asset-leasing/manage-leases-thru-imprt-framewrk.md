---
# required metadata

title: Manage leases through the Lease import framework
description: This topic explains how to use the Lease import framework to adjust multiple leases at the same time.
author: moaamer
ms.date: 04/12/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: AssetLeaseLeaseImportHeader
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2020-10-28
ms.dyn365.ops.version: 10.0.14
---

# Manage leases through the Lease import framework

[!include [banner](../includes/banner.md)]

This topic explains how to use the Lease import framework to adjust multiple leases in one step. By using this capability, you can save time, and you can also ensure more accurate adjustments by reducing the chance of human error. Additionally, this capability can connect Microsoft Dynamics 365 Finance with external data entities to efficiently upload data.

The following data entities can be used to integrate Asset leasing with external systems:

- Lease staging
- Payment contract staging
- Executory contract staging

You can use the import process to adjust a lease, update non-financial information, or add new leases. You can view and edit the leasing data before you import it.

The system can run the following three processes through the lease import suite.

| Process type  | Description |
|---------------|-------------|
| Add record    | Migrated leases that have this process type create a lease in the system. The payment schedule must be manually confirmed, and the initial recognition journal entry must be manually posted after the migration. |
| Update record | Migrated leases that have this process type update field values for a lease that is already in the system. Only the fields that have been selected on the **Update fields selection** page are updated. We recommended that you select non-financial fields on the **Update fields selection** page, because this process type doesn't adjust the lease. |
| Adjust record | Migrated leases that have this process type adjust the lease. This adjustment causes a financial lease modification of the lease. After the lease is processed, the system creates a new payment schedule by using the new data from the lease import suite. The system doesn't confirm the payment schedule or post the adjustment journal entry. |

After information is uploaded through the **Data management** workspace, open the **Import header** page (**Asset leasing \> Lease import framework \> Import header**). This page lists all imports of the three data entities that were listed earlier.

To view the lease staging data before processing is run, select **Staging data**.

The compare function lets you compare a record that you're importing with the corresponding record that's already in your system. To compare an individual lease record, select a lease, and then select **Compare**. You should complete this step to generate a **Differences** report before you migrate the lease records. The Compare functionality compares the values in the staging data to the values for leases that are currently in the system.

> [!NOTE]
> The Compare functionality won't work for leases that have the **Add record** process type, because there is nothing to compare against that lease.
>
> To compare multiple leases at the same time, go to **Asset leasing \> Lease import framework \> Periodic**, and select **Compare**.

For each entity, you can view the differences between what is currently in the system and what is in the staging tables. For each entity in the staging tables, select **See differences**. The dialog box that appears shows the current value and the proposed staging value.

You can also update the staging value by changing it in the **New Value** column and then selecting **Update staging**.

You can validate leases to ensure that the records can be brought into the system without introducing errors. Before a lease record is migrated, the system runs several validations to ensure that the record will be successfully imported. To validate an individual lease, select **Validate**.

> [!NOTE]
> To validate multiple leases at the same time, go to **Asset leasing \> Lease import framework \> Periodic**, and select **Validate**.

To process an individual lease, select **Migrate lease records** on the **Import header** page. When a lease is migrated, the system performs the action that is specified in the **Process type** field.

> [!NOTE]
> To migrate multiple leases at the same time, go to **Asset leasing \> Lease import framework \> Periodic**, and select **Migrate**.

After the leases are compared, you can run a report to view the differences for each lease that is included in the import ID. To run the report for one lease, select that lease in the staging data, and then select **Compare and view report \> Differences report**.

> [!NOTE]
> To compare multiple leases at the same time, go to **Asset leasing \> Lease import framework \> Periodic** and select **Compare**. 

## Set up update fields

If you're using the Lease import framework to update leases, and the process type is **Update record**, you can select specific fields to update.

1. Go to **Asset leasing \> Lease import framework \> Setup \> Update field selection**.
2. On the page that appears, select the fields to update, and then select the green arrow to move them to the **Selected fields** list. Only fields in the **Selected fields** list can be updated by using the lease import suite.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
