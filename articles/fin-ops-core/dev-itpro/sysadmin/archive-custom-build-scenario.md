---
title: Build a custom archive scenario
description: Learn how to build a complete custom archive scenario using only custom tables.
author: git-kiran 
ms.author: Weijiesa 
ms.topic: how-to
ms.date: 07/20/2026
ms.custom:
  - bap-template
ms.reviewer: twheeloc

---

# Build your own custom archive scenario

[!INCLUDE [banner](../includes/banner.md)]

This article describes how to build a complete custom archive scenario from scratch by using only custom tables. By using this approach, you can archive custom business transactions independently of Microsoft-managed archive scenarios.

## Overview

Use this scenario to archive custom transaction data that isn't related to Microsoft-managed tables. You create a complete new archive scenario with its own job type, UI, and archive scope.

> [!IMPORTANT]
> Custom scenarios must include only custom tables. Custom scenarios must not reference Microsoft-managed tables at all, even as join or lookup dependencies. If your custom tables are related to Microsoft tables, see [Add custom tables to standard scenarios](archive-custom-add-tables.md) instead.

The components involved in this scenario are:

- Custom root table and related child tables
- Custom history tables (one per live table)
- Custom finance and operations data entities (one per live table)
- Job contract creator class
- Archive service type registration

Don't create archive classes in the BusinessIntelligence model. Put all custom archive code in a customer-owned model.

### Prerequisites

- Access to Visual Studio with Dynamics 365 finance and operations development tools
- Development environment with Archive framework deployed
- Understanding of archive framework architecture
- Understanding of table relationships and hierarchy design
- System Administrator role in Dynamics 365 finance and operations
- Familiarity with X++ programming

### Design planning

Before starting development, plan your archive scenario structure.

- Identify the root table - This table defines what gets archived. Think of it as the header table for your archive scope.
- Design table hierarchy - Map out your table relationships:

```
CustomWorkflowHeader (Source Link)
├── CustomWorkflowLine (1-to-many)
│   └── CustomWorkflowLineDetail (1-to-many)
├── CustomWorkflowAttachment (1-to-many)
└── CustomWorkflowComment (1-to-many)
```

Design principles:

- Parent-child relationships through `RecId` foreign keys
- Clear relationship cardinality (one-to-one, one-to-many)
- No circular dependencies

### Define archive criteria

Common criteria patterns include:

- Age-based: Records older than a specific number of days, months, or years.
- Status-based: Records with **Completed**, **Closed**, or **Finalized** status.
- Volume-based: Records that exceed the retention threshold.

Example criteria:

```xpp
// Workflow completed over 2 years ago
CompletedDate < (today() - 730)
&& WorkflowStatus == WorkflowStatus::Completed
&& DataAreaId == _selectedLegalEntity
```

### Create root table

To create the root table that defines your archive scope, follow these steps:

1. Right-click the project, and then select **Add** > **New Item** > **Table**.
1. Name your root table:
   - Example: `CustomWorkflowHeader`
   - Example: `IntegrationBatchHeader`
   - Example: `TelemetrySessionHeader`

### Add required fields

Mandatory fields:

- `RecId` (Int64, Primary Key) - Automatically added
Business fields:
- Transaction identifier (for example, `WorkflowId`, `BatchId`, `SessionId`)
- Status field (for example, `WorkflowStatus`)
- Date fields for criteria (for example, `CreatedDate`, `CompletedDate`)
- Other relevant transaction data

Example structure:

```
CustomWorkflowHeader
├── RecId (Int64)
├── WorkflowId (String)
├── WorkflowType (Enum)
├── WorkflowStatus (Enum: Created, InProgress, Completed)
├── InitiatedBy (UserId)
├── CreatedDate (TransDate)
├── CompletedDate (TransDate)
├── DataAreaId (DataAreaId)
└── Partition (PartitionKey)
```

### Configure table properties

> [!IMPORTANT]
> On the **source (live) table**, set the property **`ChangeTrackingEnabled`** to **`Yes`**. This setting enables change tracking required for archive operations.

1. In Visual Studio, select your root table.
1. In the Properties window, find **ChangeTrackingEnabled**.
1. Set the value to **Yes**.

### Add archive criteria index

This index is **critical** for archive job query performance.

```xml
<AxTableIndex>
    <Name>ArchiveCriteriaIdx</Name>
    <Fields>
        <AxTableIndexField>
            <DataField>WorkflowStatus</DataField><!-- Criteria field -->
        </AxTableIndexField>
        <AxTableIndexField>
            <DataField>CompletedDate</DataField><!-- Date criteria field -->
        </AxTableIndexField>
    </Fields>
    <IncludedColumns>
        <AxTableIndexIncludedColumn>
            <DataField>RecId</DataField><!-- If not clustered -->
        </AxTableIndexIncludedColumn>
        <AxTableIndexIncludedColumn>
            <DataField>SysRowVersion</DataField>
        </AxTableIndexIncludedColumn>
        <AxTableIndexIncludedColumn>
            <DataField>SysDataStateCode</DataField>
        </AxTableIndexIncludedColumn>
    </IncludedColumns>
</AxTableIndex>
```

Follow these index design rules:

- Use primary segregation (`DataAreaId` or `Partition`) as the first field.
- Use criteria fields in WHERE conditions, such as status or dates, for the next fields.
- Include `RecId` (if not clustered), `SysRowVersion`, and `SysDataStateCode` for performance.

### Add reconciliation index for long-term retention

```xml
<AxTableIndex>
    <Name>ArchiveSysVersionIdx</Name>
    <Fields>
        <AxTableIndexField>
            <DataField>SysDataStateCode</DataField>
        </AxTableIndexField>
        <AxTableIndexField>
            <DataField>SysRowVersion</DataField>
        </AxTableIndexField>
    </Fields>
</AxTableIndex>
```

> [!IMPORTANT]
> Both indexes are mandatory on the root table and all related child tables. Missing indexes cause job failures or poor LTR performance.

#### Create related child tables

To create all tables in your table hierarchy, follow these steps:

1. Create the table with an appropriate name, such as `CustomWorkflowLine` or `CustomWorkflowAttachment`.
1. Add a foreign key field to the parent, such as `WorkflowHeaderRecId`.
1. Add segregation fields like `DataAreaId` or `Partition` that match the parent.
1. Add business-specific fields.
1. **Set the `ChangeTrackingEnabled` property to `Yes`** on each child table.

### Define parent-child relationships

Add relation to parent for each child table:

```xml
<AxTableRelation>
    <Name>CustomWorkflowHeader</Name>
    <RelatedTable>CustomWorkflowHeader</RelatedTable>
    <Cardinality>ZeroMore</Cardinality>
    <RelationshipType>Association</RelationshipType>
    <Constraints>
        <AxTableRelationConstraint>
            <Field>WorkflowHeaderRecId</Field>
            <RelatedField>RecId</RelatedField>
        </AxTableRelationConstraint>
    </Constraints>
</AxTableRelation>
```

### Add required indexes to each child table

Archive criteria index (includes foreign key):

```xml
<AxTableIndex>
    <Name>ArchiveCriteriaIdx</Name>
    <Fields>
        <AxTableIndexField>
            <DataField>WorkflowHeaderRecId</DataField><!-- Foreign key for JOIN -->
        </AxTableIndexField>
    </Fields>
    <IncludedColumns>
        <AxTableIndexIncludedColumn>
            <DataField>RecId</DataField><!-- If not clustered -->
        </AxTableIndexIncludedColumn>
        <AxTableIndexIncludedColumn>
            <DataField>SysRowVersion</DataField>
        </AxTableIndexIncludedColumn>
        <AxTableIndexIncludedColumn>
            <DataField>SysDataStateCode</DataField>
        </AxTableIndexIncludedColumn>
    </IncludedColumns>
</AxTableIndex>
```

Reconciliation index (same on every table):

```xml
<AxTableIndex>
    <Name>ArchiveSysVersionIdx</Name>
    <Fields>
        <AxTableIndexField>
            <DataField>SysDataStateCode</DataField>
        </AxTableIndexField>
        <AxTableIndexField>
            <DataField>SysRowVersion</DataField>
        </AxTableIndexField>
    </Fields>
</AxTableIndex>
```

#### Create history tables

To create history tables for archived data storage, follow these steps:

1. Create corresponding history table
1. Name: `[LiveTableName]History`
   - Example: `CustomWorkflowHeaderHistory`
   - Example: `CustomWorkflowLineHistory`

### Mirror all fields from live table

Copy all fields from the live table **except**:

- `SysRowVersion` (system-managed, changes on move)
- `SysDataState` (system-managed, changes on move)

Make sure all other fields are identical:

- Same names
- Same data types
- Same EDTs
- Same lengths

#### Configure history table properties

For each history table, don't copy unique indexes from live table (archived data doesn't need uniqueness).

### Add indexes for query performance

Add indexes on foreign keys and commonly queried fields as they enable efficient querying of archived data and are required for reversal scheduling.

#### Create finance and operations data entities

To create finance and operations data entities to enable Dataverse virtual entities for long-term retention, follow these steps:

1. Right-click the project, and then select **Add** > **New Item** > **Data Entity**.
1. Enter a name: `[TableName]BiEntity`
   - Example: `CustomWorkflowHeaderBiEntity`
   - Example: `CustomWorkflowLineBiEntity`

#### Configure primary data source

1. Set **Data sources**:
   - **Primary Data Source**: Corresponding live table
   - Include all fields
1. Set field visibility:
   - All fields = **Public**

#### Configure mandatory entity properties

These properties are required for archive and LTR:

| Property | Value | Purpose |
|----------|-------|---------|
| `IsPublic` | Yes | Exposes entity to Dataverse |
| `PublicEntityName` | Entity name | OData/Virtual Entity name |
| `PublicCollectionName` | Entity name + 's' | OData collection endpoint |
| `Is Read Only` | **Yes** | Archive entities must be read-only |
| `Auto Create` | **Yes** | Autocreates virtual entity in Dataverse |
| `Auto Refresh` | **Yes** | Synchronizes metadata automatically |
| `Allow Retention` | **Yes** | Required for LTR |
| `Allow Row Version Change Tracking` | **Yes** | Required for change tracking |
| `ChangeTrackingEnabled` | Yes | Enables change detection |

#### Enable rowversion support

For each entity, see [Entity change tracking](../data-entities/entity-change-track.md).

1. Add change tracking to data source.
1. Enable rowversion on entity.
1. Test entity in Data Management workspace.

#### Publish virtual entities to Dataverse

To make entities available in Dataverse for LTR using one of the following solutions:

- Automatic publishing (recommended) - When you set `Auto Create` to `Yes`:
  - Virtual entities publish automatically after entity sync.
  - This process might take 24 to 48 hours.
  - No manual action is required.

### Verify entities in Dataverse

1. Go to the [Power Apps Maker Portal](https://make.powerapps.com).
1. Select your environment and choose **Tables**.
1. Search for your entities, such as `mserp_customworkflowheaderbientity`.
1. Verify that all entities in your hierarchy are present.

#### Refresh virtual entity metadata (if needed)

If you need to refresh entity metadata for any entities in your hierarchy, use one of the following options:

Manual refresh using advanced find:

1. Go to **Advanced Find** in your Dataverse environment.
1. Select **Available finance and operation entities**.
1. Filter **Name** to include your entity name (for example, `customworkflowheaderbientity`).
1. From the results, open the record.
1. Select the **Refresh** checkbox.
1. Save the record.
1. Repeat for all entities in your hierarchy.

Using Power Apps Maker Portal:

1. Go to the [Power Apps Maker Portal](https://make.powerapps.com).
1. Go to **Tables** and find each entity.
1. Open the entity and trigger refresh.
1. Repeat for all entities in your hierarchy.

For more information, see [Virtual entity refresh troubleshooting](archive-faq.md#case-3-virtual-entity-that-isnt-eligible-for-archival).

#### Configure change tracking and LTR

Third parties (ISVs, partners, and customers) can use two approaches to configure entities for long-term retention:

Manual configuration - This simpler approach is suitable for most implementations. Manually enable change tracking and LTR for each entity in Power Apps Maker.

1. Go to the [Power Apps Maker Portal](https://make.powerapps.com).
1. For each virtual entity in your hierarchy (source link plus all children):
   - Find the entity (for example, `mserp_customworkflowheaderbientity`).
   - Enable change tracking.
   - Enable long-term retention.
1. Repeat for **all entities** in your table hierarchy.

> [!IMPORTANT]
> If you skip any entity in the hierarchy, LTR for that table doesn't work, and archive jobs might fail validation.

For more information, see:

- [Enable a table for long-term retention](/power-apps/maker/data-platform/data-retention-set#enable-a-table-for-long-term-retention)
- [Enable change tracking for entities](../data-entities/entity-change-track.md)

#### Automated solution deployment (Advanced)

This approach involves building Dataverse solutions that package your entity configurations for automated deployment across multiple environments.
For complete instructions on building and deploying Dataverse solutions, see [Configure Dataverse for long-term retention](archive-custom.md#automated-solution-deployment).

#### Create job contract creator

Create a new class in your customer-owned model.

```xpp
using Microsoft.Dynamics.Archive.Contracts;

/// <summary>
/// Creates archive job contracts for custom workflow scenario.
/// </summary>
public class CustomWorkflowArchiveAutomationJobRequestCreator
{
    // Class implementation
}
```

#### Implement createPostJobRequest method

Use this method to build the job contract by using the builder API:

```xpp
public ArchiveJobPostRequest createPostJobRequest(var _criteria)
{
    // Validate criteria
    if (!_criteria)
    {
        throw error(Error::wrongUseOfFunction(funcName()));
    }
    
    ArchiveServiceArchiveJobPostRequestBuilder builder = 
        ArchiveServiceArchiveJobPostRequestBuilder::construct(
            "@YourModel:CustomWorkflowArchiveDescription",
            CustomWorkflowArchiveConstants::RegisteredTypeName);

    var rootCfg = ArchiveServiceSourceTableConfiguration::newForSourceTable(
        tableStr(CustomWorkflowHeader),
        tableStr(CustomWorkflowHeaderHistory),
        tableStr(CustomWorkflowHeaderBiEntity));

    builder.addSourceTableForLongTermRetention(rootCfg)
        .addDateTimeWhereConditionToDataSource(
            tableStr(CustomWorkflowHeader),
            fieldStr(CustomWorkflowHeader, CompletedDate),
            _criteria.ArchiveBeforeDateTime,
            Microsoft.Dynamics.Archive.Contracts.Operator::LessThanOrEquals)
        .addDataAreaIdWhereCondition(tableStr(CustomWorkflowHeader), _criteria.DataAreaId)
        .addPartitionWhereCondition(tableStr(CustomWorkflowHeader));

    this.addChildTables(builder, _criteria);

    return builder.finalizeArchiveJobPostRequest();
}
```

#### Implement addChildTables method

Add each child table to the archive scope:

```xpp
private void addChildTables(ArchiveServiceArchiveJobPostRequestBuilder _builder)
{
    // Add workflow lines
    _builder.addSourceTableForLongTermRetention(
        ArchiveServiceSourceTableConfiguration::newForChildSourceTable(
            tableStr(CustomWorkflowLine),
            tableStr(CustomWorkflowLineHistory),
            tableStr(CustomWorkflowLineBiEntity),
            tableStr(CustomWorkflowHeader)))
        .addJoinCondition(
            tableStr(CustomWorkflowLine),
            fieldStr(CustomWorkflowLine, WorkflowHeaderRecId),
            fieldStr(CustomWorkflowHeader, RecId))
        .addDataAreaIdWhereCondition(tableStr(CustomWorkflowLine), _criteria.DataAreaId)
        .addPartitionWhereCondition(tableStr(CustomWorkflowLine));
    
    // Add workflow line details
    _builder.addSourceTableForLongTermRetention(
        ArchiveServiceSourceTableConfiguration::newForChildSourceTable(
            tableStr(CustomWorkflowLineDetail),
            tableStr(CustomWorkflowLineDetailHistory),
            tableStr(CustomWorkflowLineDetailBiEntity),
            tableStr(CustomWorkflowLine)))
        .addJoinCondition(
            tableStr(CustomWorkflowLineDetail),
            fieldStr(CustomWorkflowLineDetail, WorkflowLineRecId),
            fieldStr(CustomWorkflowLine, RecId))
        .addDataAreaIdWhereCondition(tableStr(CustomWorkflowLineDetail), _criteria.DataAreaId)
        .addPartitionWhereCondition(tableStr(CustomWorkflowLineDetail));
    
    // Add workflow attachments
    _builder.addSourceTableForLongTermRetention(
        ArchiveServiceSourceTableConfiguration::newForChildSourceTable(
            tableStr(CustomWorkflowAttachment),
            tableStr(CustomWorkflowAttachmentHistory),
            tableStr(CustomWorkflowAttachmentBiEntity),
            tableStr(CustomWorkflowHeader)))
        .addJoinCondition(
            tableStr(CustomWorkflowAttachment),
            fieldStr(CustomWorkflowAttachment, WorkflowHeaderRecId),
            fieldStr(CustomWorkflowHeader, RecId))
        .addDataAreaIdWhereCondition(tableStr(CustomWorkflowAttachment), _criteria.DataAreaId)
        .addPartitionWhereCondition(tableStr(CustomWorkflowAttachment));
}
```

#### Key implementation rules

Root table specification:

- For root table: Use `ArchiveServiceSourceTableConfiguration::newForSourceTable(liveTable, historyTable, entityName)`.
- For child tables: Use `ArchiveServiceSourceTableConfiguration::newForChildSourceTable(liveTable, historyTable, entityName, parentTable)`.

JOIN conditions:

- Must match foreign key relationships exactly.
- Use the table name, child field, and parent field.

WHERE conditions:

- Include segregation fields that match the root and child tables.
- Use `addDataAreaIdWhereCondition()` and `addPartitionWhereCondition()` where applicable.

Entity names:

- Use the customer-owned or existing finance and operations entity name.
- The entity must correspond to the live table being archived.

#### Enable parallel processing with a job criteria key

[Parallel processing for archive jobs](archive-parallel-process.md) lets multiple archive jobs run at the same time. A custom scenario participates in parallel execution only when it assigns a **job criteria key** to each job it creates. If you don't set a job criteria key, your custom scenario's jobs still run correctly, but they run **sequentially**, one at a time, and don't benefit from parallel execution.

The scheduler uses the job criteria key to decide whether two jobs can run at the same time. The key is a partitioning identifier that describes the scope of a job&mdash;most commonly the legal entity (`DataAreaId`). Two jobs that have different keys are treated as non-overlapping and can run in parallel. Jobs that share the same key, or that have no key at all, run sequentially.

To set the job criteria key, call `setJobCriteriaKey()` on the builder in your `createPostJobRequest` method. Set it early in the builder chain, before you add source tables:

```xpp
// Initialize builder
ArchiveServiceArchiveJobPostRequestBuilder builder = 
    ArchiveServiceArchiveJobPostRequestBuilder::construct();

// Set the job criteria key - typically the legal entity (DataAreaId)
if (strLen(_criteria.DataAreaId) > 0)
{
    builder.setJobCriteriaKey(_criteria.DataAreaId);
}
```

A value is suitable as a job criteria key when it meets all of the following conditions:

- **Represents a logical partition** of your data, such as legal entity, ledger, customer, or project.
- **Matches the scope of the job's query.** The key is a label, not a filter;it doesn't change which records are archived. Your `WHERE` conditions must filter by the same field or fields named in the key, so that two jobs with different keys never touch the same records (zero overlap).
- **Consistent within a job.** A single job must archive records for only one value of the key. For example, if the key is the legal entity, each job should process just one legal entity. A job that spans multiple legal entities at once can't use the legal entity as its key, because the key would no longer describe the job's true scope.
- **Non-null and string-compatible.** Validate that the value exists before you set it, and convert numeric values to a string (for example, use `int642Str()` for a `RecId`).

> [!TIP]
> Use `DataAreaId` (legal entity) unless your scenario genuinely needs finer-grained partitioning. It's usually the safest choice, but it guarantees zero overlap only when each job's `WHERE` conditions filter by `DataAreaId` and a single job processes just one legal entity at a time. You can use a composite key (for example, `_criteria.DataAreaId + '|' + region`) to gain more parallelism, but only if your `WHERE` conditions filter by every field in that key. Otherwise, jobs with different keys could process overlapping records.


#### Keep job contract logic in one class

For custom scenarios, keep archive scope and long-term retention table configuration in the same job creator class in your customer-owned model.

Use `addSourceTableForLongTermRetention()` for the root table and each child table. Don't add a BusinessIntelligence extension layer for this scenario.

#### Register archive service type

Register the custom archive type in your customer-owned model by implementing `ArchiveServiceIManagedArchiveType` and exporting it through MEF.

Use `ArchiveServiceManagedTypeRegistration` in `getManagedTypeRegistration()` to set type name, label, enabled state, and job name support.

#### Build and deploy

To build your solution, follow these steps:

1. Build your customer-owned model (tables, entities, job creator, and type registration).
1. Resolve any compilation errors.

#### Synchronize database

```powershell
# Sync database to create tables and indexes
# Use Visual Studio: Dynamics 365 > Synchronize Database
```

#### Deploy to environment

1. Create deployable package.
1. Deploy to target environment.
1. Verify deployment success.

#### Synchronize entities

After deployment:

1. Go to the **Data Management** workspace.
1. Go to **Framework parameters** > **Entity settings**.
1. Select **Refresh entity list**.
1. Verify your finance and operations data entities appear.

#### Verify virtual entities in Dataverse

1. Wait for automatic publishing or publish manually.
1. Verify entities appear in Power Apps Maker.
1. Configure change tracking and LTR for each entity.

#### Test end-to-end

To create test data, follow these steps:

1. Create test header record in the root table.
1. Create related child records (lines, details, attachments).
1. Ensure segregation fields match (`DataAreaId`, etc.).
1. Set status and date fields to meet archive criteria.

#### Test archive job creation

1. Go to the archive workspace.
1. Select your custom archive type.
1. Create an archive job with test criteria.
1. Verify the job details show the correct table count.

#### Execute archive job

1. Run the archive job.
1. Monitor job progress.
1. Verify the job completes successfully.

#### Validate data movement

Check history tables:

```sql
-- Verify header moved to history
SELECT * FROM CustomWorkflowHeaderHistory WHERE WorkflowId = '[TestID]'

-- Verify child records moved
SELECT * FROM CustomWorkflowLineHistory WHERE WorkflowHeaderRecId = [TestHeaderRecId]
```

Check managed data lake:

- Go to Dataverse managed data lake.
- Find CSV files for all tables.
- Verify records are present with correct data.

Verify live table cleanup:

```sql
-- Confirm records removed from live tables
SELECT * FROM CustomWorkflowHeader WHERE WorkflowId = '[TestID]'  -- Should return no rows
```

#### Test restore operation

1. Create reversal job.
1. Execute restore.
1. Verify data returns to live tables.
1. Validate parent-child relationships are intact.

#### Common issues and solutions

| Issue | Cause | Solution |
|-------|-------|----------|
| Archive type doesn't appear in UI | Type registration didn't run | Verify `registerTypes()` is called on startup |
| Job creation fails validation | Missing indexes on live tables | Add `ArchiveCriteriaIdx` and `ArchiveSysVersionIdx` to all tables |
| Child table data not archiving | JOIN conditions incorrect | Verify foreign key field names match exactly |
| Managed data lake missing tables | Entity not configured for LTR | Verify `Allow Retention = Yes` on all finance and operations data entities |
| Change tracking failures | Rowversion not enabled | Enable rowversion and `Allow Row Version Change Tracking` on entities |
| Reversal jobs blocked | Missing indexes on history tables | Add foreign key and criteria indexes to history tables |
| Performance issues | Missing reconciliation indexes | Add `ArchiveSysVersionIdx` to all live tables |
| Job contract null reference | Base class method not called | Ensure `next createPostJobRequest()` in extension |

#### Predeployment checklist

Before deploying to production:

Tables:

- Root table created with all fields.
- All child tables created with foreign keys.
- Parent-child relationships defined on all child tables.
- `ArchiveCriteriaIdx` added to all tables.
- Added `ArchiveSysVersionIdx` to all tables.
- History tables mirror all live tables, except for `SysRowVersion` and `SysDataState`.
- History tables have foreign key indexes.
- No references to Microsoft-managed tables.

Finance and operations data entities:

- Finance and operations data entity created for each live table.
- Set all required properties, such as `Auto Create` and `Allow Retention`.
- Enabled rowversion on all entities.
- Published virtual entities to Dataverse.
- Enabled change tracking on all virtual entities.
- Enabled LTR on all virtual entities in Dataverse.

Code:

- Created job contract creator class in customer-owned model.
- Implemented archive criteria in `createPostJobRequest`.
- Added root and child tables with correct JOINs and segregation filters.
- Created managed type registration class using `ArchiveServiceIManagedArchiveType`.
- No compilation errors.

Testing:

- Created test data for all tables.
- Created archive job successfully.
- Job contract includes all tables.
- Archive job moves data to history tables.
- Managed data lake contains CSV for all tables.
- Live tables cleaned after archive.
- Reversal job restores data correctly.
- Maintained parent-child relationships.

#### Related articles

- [Archive customization overview](archive-custom.md)
- [Add custom fields to Microsoft-managed tables](archive-custom-add-fields.md)
- [Add custom tables to standard scenarios](archive-custom-add-tables.md)
- [Configure Dataverse for long-term retention](archive-custom.md#configure-dataverse-for-long-term-retention)
- [Parallel processing for archive jobs](archive-parallel-process.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
