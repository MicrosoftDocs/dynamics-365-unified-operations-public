---
# required metadata

title: Data import and export jobs
description: 
author: Sunil-Garg
manager: AnnBe
ms.date: 08/17/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Data import and export jobs

[!include[banner](../includes/banner.md)]

To create and manage data import and export jobs, use the Data management workspace. By default, the data import and export process creates a staging table for each entity in the target database. Staging tables let you verify, cleanup, or convert data before moving it.  

## Data import/export framework process 
When you export or import data, you perform the following steps: 
1. Before you begin, define the format of the data to export or import. You can define formats using the Data sources setup tile.
2. Create an import or export job that: 
 - Defines the type of import or export job
 - Identifies the entities to import or export
 - Organizes the entities, so that they are processed in logical groups, and in an order that makes sense
 - Sets the data format for the job
 - Determines whether to use staging tables
3. Validate that source and target data are mapped correctly.
4. Verify the security for your import or export job. 
5. Run the import or export job.

## Sequencing entities
Entities can be sequenced in a data template, or in import and export jobs. When you are running a job that contains more than one data entity, it is important to ensure that the data entities are properly sequenced. The primary reason for sequencing entities is to address any functional dependencies among entities. If entities don’t have any functional dependencies, then they can be scheduled for parallel import or export.

### Execution units, levels, and sequences
The execution unit, level in execution unit, and sequence of an entity are used to control the order that the data is exported or imported in.
•	Entities in different execution units are processed in parallel.
•	Within a unit, entities are processed in parallel if they have the same level.
•	Within the same level, entities are processed by the sequence order within the level.
•	After processing of one level is completed, the next level is processed

#### Resequencing
You may want to resequence in the following situations: 
- If only one data job is used for all of your changes, you can use resequencing options to optimize the execution time for the full job. In such cases, you can use the execution unit to represent modules, level to represent a feature area in a module, and sequence to represent the entity. Using this approach, you can operate across modules in parallel while still working in sequence within a module. All dependencies must have been taken into account to ensure that parallel operations will succeed.
- If multiple data jobs are used, one for each module, for example, then, sequencing can be used to affect the level and sequence of entities for optimal execution.
- If there are no dependencies at all, then entities can be sequenced at different execution units for maximum optimization.

The **Resequencing** menu is enabled when multiple entities are selected. You can re-sequence based on execution unit, level or sequence options. You can set an Increment to resequence the entities that have been selected. Each chosen entity’s unit, level and/or sequence number is updated by the specified increment.

#### Sorting
Use can use the **Sort by** option to view the entity list in sequential order.

Use cases
Following are some of the use cases when resequencing is useful.

## Mapping
Mapping is a function that is applicable to both import and export jobs. 
- In the context of an import job, mapping describes which columns in the source file become the columns in the staging table. This helps the system know which column data in the source file must be copied into which column of the staging table. 
- In the context of an export job, mapping describes which columns of the staging table (source) become the columns of the target file.

If the column names in the staging table and the file are same, then the system will automatically establish the mapping based on the names. However, if the names are different, then such columns will not be mapped automatically. In such cases, you must complete the mapping by clicking the **View map** option on the entity in the data job.

There are two mapping views: **Mapping visualization**, the default view, and **Mapping details**. A red asterisk (\*) identifies any required fields in the entity. These fields must be mapped to work with the entity. Other fields can be unmapped as required when working with the entity. To un-map a field, highlight the field in either column (Entity or Source), and then click **Delete selection**. Click **Save** to save your changes. After saving, close the form to return to the project. The field mapping from source to staging can also be edited after import using the same process.

Mapping can be regenerated in the form by clicking **Generate source mapping**. Note that generated mapping behaves like the automatic mapping, so any un-mapped fields must be manually mapped.

