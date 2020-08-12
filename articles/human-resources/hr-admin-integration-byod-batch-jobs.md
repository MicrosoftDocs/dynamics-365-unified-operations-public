---
# required metadata

title: Optimize BYOD scheduled batch jobs
description: This topic explains best practices when setting up and scheduling BYOD batch jobs with Microsoft Dynamics 365 Human Resources.
author: andreabichsel
manager: AnnBe
ms.date: 08/10/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-human-resources
ms.technology: 

# optional metadata

# ms.search.form: BatchJob, BatchJobEnhanced
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Core, Human Resources
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-08-10
ms.dyn365.ops.version: Platform update 36
---

# BYOD scheduling and performance

## Data export/Performance considerations

After entities are published to the destination database, you can use the Export function in the Data management workspace to move data. The Export function lets you define a Data movement job that contains one or more entities.

You can use the Export page to export data into many target data formats, such as a comma-separated values (CSV) file. This page also supports SQL databases as another destination.
 
You can create a data project that has multiple entities. You can schedule this data project to run by using the batch framework. You also schedule the data export job to run on a periodic basis by selecting the Export in batch option.

Adding multiple entities to an export project for BYOD must be done carefully to ensure the overall reliability of the BYOD export is not compromised. Different parameters must be taken into consideration when deciding the number of entities that are added to the same project. Some of these parameters should be the degree of complexity of the entities, data volume per entity that is expected, and the overall time for export to complete at the job level. Adding hundreds of entities must be avoided, therefore creating multiple jobs with smaller number of entities is recommended.

## Scheduling 

BYOD batch jobs should run at night or after hours if possible. Be sure to check the time zone for these recurring batch jobs. Some batch jobs might use Pacific Standard Time (PST).

| Batch job | Recommended occurrence |
| --- | --- |
| BYOD Batch Jobs | Scheduling frequency of BYOD batch jobs should be configured based on the length of time each batch job takes to execute. The execution time, along with the business need for the data in BYOD will help to avoid any performance issues. Frequency of running these jobs should only be set to a value where the job can complete well before its next scheduled run time. Running multiple jobs in parallel is also not recommended as this may also cause performance issues. |

Use of recurring exports in Manage > Manage recurring data jobs for BYOD is discouraged. You must use the Export in batch option.

### Incremental export

When you add an entity for data export, you can select to do an incremental export (which is also known as incremental push) or a full push. For incremental push to work, you must enable the Change tracking option in the database and specify an appropriate change tracking option, as described earlier in this topic.

A full push deletes all existing records from an entity and then inserts the current set of records from the selected entity.

If you select an incremental push, the first push is always going to be a full push. This is because SQL needs to know which records have been 'tracked' in order to be able to track subsequent changes. Whenever a new record is inserted, or a record is added or deleted, the corresponding change will be reflected in the destination entity.

Because the first push is always a full push, we do not recommend that you do an explicit full push before you enable change tracking.

We recommend that you first enable change tracking and schedule a export job with incremental push. This will take care of the first full push and the subsequent incremental exports.

## Timeouts

The default timeouts for BYOD exports are set to ten minutes for truncation operations and one hour for actual bulk insert operations. When volumes are high, these timeout settings may not be sufficient and must be updated. Starting with the release of Platform update 18, you can update the timeout settings by navigating to Data management > Framework parameters > Bring your own database. These timeouts are company specific and must be set separately for each company.

## Known limitations

The BYOD feature has the following limitations.
There should be no active locks on your database during synchronization
Because BYOD is your own database, you must ensure that there are no active locks on your Azure SQL database when data is being synced. Having active locks on your database during synchronization can result in slow writes or even failure to export to your Azure SQL database.

You can't export composite entities into your own database. Currently, composite entities aren't supported. You must export individual entities that make up the composite entity. However, you can export both the entities in the same data project.

Entities that don't have unique keys can't be exported by using incremental push. You might face this limitation especially when you try to incrementally export records from a few ready-made entities. Because these entities were designed to enable the import of data, they don't have a unique key. However, you can enable change tracking only for entities that have a unique key. Therefore, there is a limitation on incremental push. One workaround is to extend the required entity and define a unique key.

## Troubleshooting

### Incremental push not working correctly

Issue - When a full push occurs for some entity then a large set of records can be seen in BYOD using a select statement. However, an incremental push results in only a few records in BYOD. It seems as if the incremental push deleted all the records and added only the changed records in BYOD.

Solution - In cases like this it is recommended to disable and re-enable change tracking for the entity in question. The state of the SQL change tracking tables might not be in the expected state. 