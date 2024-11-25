---

title: Schema changes for shorter downtime during custom package deployments
description: Learn how to make schema changes for shorter downtime when you deploy custom packages, including an outline on deployment phases.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.date: 11/09/2023
ms.reviewer: twheeloc
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Schema changes for shorter downtime during custom package deployments

[!include [banner](../includes/banner.md)]

This article describes best practices and guidelines that can help you achieve near-zero downtime while you apply table schema changes when you plan custom package deployments.

## Deployment phases

During any custom package deployment, environments go through the following phases:

1. **Pre-servicing** – The system is accessible to the users, and the environment can be used. Many online table schema changes can be made.
2. **Servicing** – The downtime starts, and all the online unsupported schema changes are made.
3. **Post-servicing** – Index-related schema changes are applied with online options. The customer can start to use their environment.

## Online supported changes

SQL provides online schema change that can be done without exclusive locks on the table. Finance and operations app deployments are modified so that they use these online options to make most of the schema changes without causing downtime for the users.

The following table lists the changes that are supported online and the related phase.

| Supported changes | Phase |
|------------|-----------|
| All new field additions to the table. | Pre-servicing |
| All field changes that involve increases in the string size. Decreases in the string size are ignored, because they can cause data truncation. | Pre-servicing |
| All string to memo field changes that don't require dependent index drops. | Pre-servicing |
| All memo to string field changes that don't cause data truncation. | Pre-servicing |
| All additions and modifications of nonclustered indexes. | Post-servicing |
| Nonprimary clustered index changes that don't require clustered index drops, including adding fields to a nonprimary clustered index, removing fields from it, and changing it from one index to another. | Post-servicing |
| Nonclustered primary key changes from one index to another. | Post-servicing |
| Columnstore index changes that don't require index drops. | Post-servicing |

> [!NOTE]
> These changes occur during the **Pre-servicing** and **Post-servicing** phases with online options. The execution time of these phases depends on numerous factors, such as the type of schema change, the number of changes, the size of the tables, and any transient blockers.
>
> Field changes, such as memo to string field changes, and clustered index changes can be time consuming, because the table must be rebuilt. Explore options to add a new field or a new table. Alternatively, if the table is a staging table, determine whether the data can be removed before the change.
> 
> String size decrease changes are ignored during database synchronization, because they cause data loss.

## Online unsupported changes

Any schema changes that aren't covered in the previous section aren't yet supported online in finance and operations app deployments and should be avoided. These changes run in the **Servicing** phase of deployments when the environment is down.

Here's a list of changes and suggestions:

 - **Clustered primary key changes** – Changes to a clustered primary key for a table can't be done online. We don't recommend that you change the primary key of the table, because it's likely used in multiple other indexes. Instead, we recommend that you add a new table that has a corrected primary index.
 - **Numeric field scale changes** – In finance and operations apps, changes to the scale of a numeric field aren't allowed and aren't supported online. We recommend that you add a new field instead of modifying the existing one if the table size is larger.
 - **Index drops** – Index drops aren't supported online. Avoid changes that can cause clustered and/or primary index drops.
 - **String to memo field changes when the field is the single field in the index, resulting in an index drop** – SQL restricts any memo field from being part of the index. If any index has this single field, the index must be dropped, and this change isn't supported. In such cases, the index can be changed so that it includes more fields. Those fields can then be removed later if they aren't required in future deployments.
 - **Fulltext index changes** – This type of change isn't supported online.
 - **Table and field drops** – These changes are non-additive and are done during downtime.
 - **Field renames** – This type of change is considered a drop of the old field and the creation of a new field that has an updated name. The new named field is added during the **Pre-servicing** phase, but the drop of the old field still occurs during downtime.
 - **Table renames** – This type of change is considered a drop of the old table and the creation of a new table that has an updated name. Creation of the new named table occurs during the **Pre-servicing** phase, and the old named table is dropped during downtime in the **Servicing** phase.

## Effectively plan custom deployments for production environments

Consider the following points before you apply a custom package to a production environment:

- Apply the package to a sandbox environment, on a production copy, to determine the time that's required for each phase. Production deployments can be scheduled based on the time that's required. Customers can continue to use their environment in the **Pre-servicing** and **Post-servicing** phases.
- Avoid online unsupported changes whenever you can. If you must make these changes, avoid adding multiple changes in a single package, because they can increase the deployment downtime.
