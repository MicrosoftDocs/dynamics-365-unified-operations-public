---
title: Build a custom archive scenario
description: Learn how to build a complete custom archive scenario using only custom tables.
author: kehoej99 
ms.author: Weijiesa 
ms.topic: how-to
ms.date: 03/26/2026
ms.custom:
  - bap-template
ms.reviewer: twheeloc

---

# Build your own custom archive scenario

[!include [banner](../includes/banner.md)]

This article describes how to build a complete custom archive scenario from scratch using only custom tables. By using this approach, you can archive custom business transactions independently of Microsoft-managed archive scenarios.

## Overview

Use this scenario to archive custom transaction data that isn't related to Microsoft-managed tables. You create a complete new archive scenario with its own job type, UI, and archive scope.

> [!IMPORTANT]
> Custom scenarios must include **only custom tables**. Custom scenarios must not reference Microsoft-managed tables at all, even as join or lookup dependencies. If your custom tables are related to Microsoft tables, use [Scenario 2: Add custom tables to standard scenarios](archive-custom-add-tables.md) instead.

Components involved:

- Custom source link table (transaction header)
- Custom table hierarchy (headers, lines, details)
- Custom history tables (one per live table)
- Custom finance and operations data entities (one per live table)
- Job contract creator class (two separate classes required)
- Archive service type registration
- Optional UI components

Extensive X++ development for table structure, job contracts, and type registration.

### Prerequisites

- Access to Visual Studio with Dynamics 365 finance and operations development tools
- Development environment with Archive framework deployed
- Understanding of archive framework architecture
- Understanding of table relationships and hierarchy design
- System Administrator role in Dynamics 365 finance and operations
- Familiarity with X++ programming

### Design planning

Before starting development, plan your archive scenario structure.

- Identify source link table - The **source link table** is the root table that defines what gets archived. Think of it as the "header" table for your archive scope.
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

### Create source link table

To create the root table that defines your archive scope, follow these steps:

1. Right-click the project, and then select **Add** > **New Item** > **Table**.
1. Name your source link table:
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

1. In Visual Studio, select your source link table.
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

Index design rules:

- First field: Primary segregation (`DataAreaId` or `Partition`)
- Next fields: Criteria fields used in WHERE conditions, such as status or dates
- Included columns: `RecId` (if not clustered), `SysRowVersion`, `SysDataStateCode` for performance

### Add reconciliation index for LTR

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
> Both indexes are mandatory on the source link table and all related child tables. Missing indexes cause job failures or poor LTR performance.

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
| `Auto Create` | **Yes** | Autocreates virtual entity in Dataverse |
| `Auto Refresh` | **Yes** | Synchronizes metadata automatically |
| `Allow Retention` | **Yes** | **Required for LTR** |
| `Allow Row Version Change Tracking` | **Yes** | **Required for change tracking** |
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

#### Create job contract creator (Base class)

To create the base job contract creator that defines your archive scope, follow these steps:

1. Create a new class in your model.
1. Name: `Custom[ScenarioName]ArchiveAutomationJobRequestCreator`
   - Example: `CustomWorkflowArchiveAutomationJobRequestCreator`
1. Extend: `ArchiveAutomationJobRequestCreator`

Implement class structure

```xpp
using Microsoft.Dynamics.Archive.Contracts;

/// <summary>
/// Creates archive job contracts for custom workflow scenario.
/// </summary>
public class CustomWorkflowArchiveAutomationJobRequestCreator extends ArchiveAutomationJobRequestCreator
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
    
    // Initialize builder
    ArchiveServiceArchiveJobPostRequestBuilder builder = 
        ArchiveServiceArchiveJobPostRequestBuilder::construct();
    
    // Set job metadata
    builder.setArchiveType(ArchiveType::[YourArchiveType]);  // Enum value for your scenario
    builder.setJobName(strFmt("Custom Workflow Archive - %1", _criteria.DataAreaId));
    
    // Add source link table (root of hierarchy)
    builder.addSourceLinkTable(
        ArchiveServiceSourceLinkTableConfiguration::newForSourceTable(
            tableStr(CustomWorkflowHeader),              // Live table
            tableStr(CustomWorkflowHeaderHistory)))      // History table
        
        // Add WHERE conditions (archive criteria)
        .addWhereCondition(
            fieldStr(CustomWorkflowHeader, DataAreaId),
            ArchiveServiceOperator::Equals,
            _criteria.DataAreaId)
        
        .addWhereCondition(
            fieldStr(CustomWorkflowHeader, CompletedDate),
            ArchiveServiceOperator::LessThan,
            _criteria.ArchiveBeforeDate)
        
        .addWhereCondition(
            fieldStr(CustomWorkflowHeader, WorkflowStatus),
            ArchiveServiceOperator::Equals,
            WorkflowStatus::Completed);
    
    // Add child tables
    this.addChildTables(builder);
    
    // Finalize and return
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
        ArchiveServiceSourceTableConfiguration::newForSourceTable(
            tableStr(CustomWorkflowLine),
            tableStr(CustomWorkflowLineHistory),
            tableStr(mserp_customworkflowlinebientity),  // Dataverse entity name
            tableStr(CustomWorkflowHeader)))             // Parent table
        
        .addJoinCondition(
            fieldStr(CustomWorkflowLine, WorkflowHeaderRecId),
            ArchiveServiceOperator::Equals,
            fieldStr(CustomWorkflowHeader, RecId))
        
        .addWhereCondition(
            fieldStr(CustomWorkflowLine, DataAreaId),
            ArchiveServiceOperator::Equals,
            fieldStr(CustomWorkflowHeader, DataAreaId));
    
    // Add workflow line details
    _builder.addSourceTableForLongTermRetention(
        ArchiveServiceSourceTableConfiguration::newForSourceTable(
            tableStr(CustomWorkflowLineDetail),
            tableStr(CustomWorkflowLineDetailHistory),
            tableStr(mserp_customworkflowlinedetailbientity),
            tableStr(CustomWorkflowLine)))               // Parent is CustomWorkflowLine
        
        .addJoinCondition(
            fieldStr(CustomWorkflowLineDetail, WorkflowLineRecId),
            ArchiveServiceOperator::Equals,
            fieldStr(CustomWorkflowLine, RecId))
        
        .addWhereCondition(
            fieldStr(CustomWorkflowLineDetail, DataAreaId),
            ArchiveServiceOperator::Equals,
            fieldStr(CustomWorkflowLine, DataAreaId));
    
    // Add workflow attachments
    _builder.addSourceTableForLongTermRetention(
        ArchiveServiceSourceTableConfiguration::newForSourceTable(
            tableStr(CustomWorkflowAttachment),
            tableStr(CustomWorkflowAttachmentHistory),
            tableStr(mserp_customworkflowattachmentbientity),
            tableStr(CustomWorkflowHeader)))
        
        .addJoinCondition(
            fieldStr(CustomWorkflowAttachment, WorkflowHeaderRecId),
            ArchiveServiceOperator::Equals,
            fieldStr(CustomWorkflowHeader, RecId))
        
        .addWhereCondition(
            fieldStr(CustomWorkflowAttachment, DataAreaId),
            ArchiveServiceOperator::Equals,
            fieldStr(CustomWorkflowHeader, DataAreaId));
}
```

#### Key implementation rules

Parent table specification:

- For source link table: Use `.newForSourceTable(liveTable, historyTable)` (no parent)
- For child tables: Use `.newForSourceTable(liveTable, historyTable, entityName, parentTable)`

JOIN conditions:

- Must match foreign key relationships exactly
- Only `Equals` operator supported for JOINs
- Field names must be exact (case-sensitive)

WHERE conditions:

- Include segregation fields that match the parent
- Use field references for dynamic values: `fieldStr(ParentTable, FieldName)`
- Use literal values for static criteria: `WorkflowStatus::Completed`

Entity names:

- Use Dataverse virtual entity name (starts with `mserp_`)
- Use all lowercase
- Example: `tableStr(mserp_customworkflowheaderbientity)`

#### Create job contract creator (BI Extension)

To create BI extension class to add LTR configuration, follow these steps:
> [!IMPORTANT]
> You must create this extension in the **BusinessIntelligence** model. Don't create it in your main model.

1. Switch to the BusinessIntelligence model project.
1. Create a new class.
1. Set the name to `Custom[ScenarioName]ArchiveAutomationJobRequestCreator_BI_Extension`.
1. Add the extension attribute.

```xpp
using Microsoft.Dynamics.Archive.Contracts;

[ExtensionOf(classStr(CustomWorkflowArchiveAutomationJobRequestCreator))]
public final class CustomWorkflowArchiveAutomationJobRequestCreator_BI_Extension
{
    // Extension logic
}
```

#### Extend createPostJobRequest with LTR configuration

```xpp
public ArchiveJobPostRequest createPostJobRequest(var _criteria)
{
    // Call base implementation (gets job contract with tables)
    ArchiveJobPostRequest postRequest = next createPostJobRequest(_criteria);
    
    // Add LTR configuration for source link table
    postRequest = this.addSourceLinkTableForLongTermRetention(postRequest, _criteria);
    
    return postRequest;
}
```

#### Implement LTR configuration method

```xpp
private ArchiveJobPostRequest addSourceLinkTableForLongTermRetention(
    ArchiveJobPostRequest _postRequest,
    var _criteria)
{
    // Construct builder from existing contract
    ArchiveServiceArchiveJobPostRequestBuilder builder = 
        ArchiveServiceArchiveJobPostRequestBuilder::constructFromArchiveJobPostRequest(_postRequest);
    
    // Add LTR configuration for source link table
    builder.addSourceLinkTableForLongTermRetention(
        ArchiveServiceSourceLinkTableConfiguration::newForSourceTable(
            tableStr(CustomWorkflowHeader),
            tableStr(CustomWorkflowHeaderHistory),
            tableStr(mserp_customworkflowheaderbientity))  // Dataverse entity name
        
        // WHERE conditions must match base class criteria
        .addWhereCondition(
            fieldStr(CustomWorkflowHeader, DataAreaId),
            ArchiveServiceOperator::Equals,
            _criteria.DataAreaId)
        
        .addWhereCondition(
            fieldStr(CustomWorkflowHeader, CompletedDate),
            ArchiveServiceOperator::LessThan,
            _criteria.ArchiveBeforeDate)
        
        .addWhereCondition(
            fieldStr(CustomWorkflowHeader, WorkflowStatus),
            ArchiveServiceOperator::Equals,
            WorkflowStatus::Completed));
    
    // Finalize and return updated contract
    return builder.finalizeArchiveJobPostRequest();
}
```

#### Why two separate classes?

Base class (in your model):

- Defines archive scope (what tables)
- Specifies relationships (JOINs)
- No finance and operations data entity references

Finance and operations data entity extension class (in BusinessIntelligence model):

- Adds LTR configuration
- Links finance and operations data entities to tables
- Enables managed data lake access

This separation enables:

- Clear dependency management
- Model layering best practices
- Independent testing of archive vs. LTR

#### Register archive service type

To register your custom archive type so it appears in the archive framework, follow these steps:

1. Create a new class in your model.
1. Name: `Custom[ScenarioName]ArchiveServiceTypeRegistration`
1. Implement `ArchiveServiceTypeRegistration` interface

#### Implement registration logic

```xpp
using Microsoft.Dynamics.Archive.Contracts;

/// <summary>
/// Registers custom workflow archive type with archive framework.
/// </summary>
public class CustomWorkflowArchiveServiceTypeRegistration implements ArchiveServiceTypeRegistration
{
    public void registerTypes()
    {
        ArchiveServiceTypeRegistry registry = ArchiveServiceTypeRegistry::singleton();
        
        // Register archive type
        registry.registerArchiveType(
            ArchiveType::[YourCustomArchiveType],        // Enum value (add to ArchiveType enum)
            classStr(CustomWorkflowArchiveAutomationJobRequestCreator),
            "@YourLabel:CustomWorkflowArchiveTypeLabel", // Label for UI
            "@YourLabel:CustomWorkflowArchiveTypeHelp"); // Help text for UI
    }
}
```

#### Add archive type to enum

1. Extend `ArchiveType` enum
1. Add new enum value for your scenario:
   - Name: `CustomWorkflow`
   - Label: "Custom workflow archive"

#### Ensure registration runs on startup

The type registration must run during application startup. Register it in your module startup:

```xpp
public class CustomWorkflowModule
{
    public static void initialize()
    {
        // Register archive type
        CustomWorkflowArchiveServiceTypeRegistration registration = new CustomWorkflowArchiveServiceTypeRegistration();
        registration.registerTypes();
    }
}
```

#### Build and deploy

To build your solution, follow these steps:

1. Build your main model (tables, base job creator, type registration)
1. Build BusinessIntelligence model (finance and operations data entities, extension class)
1. Resolve any compilation errors

#### Synchronize database

```powershell
# Sync database to create tables and indexes
# Use Visual Studio: Dynamics 365 > Synchronize Database
```

#### Deploy to environment

1. Create deployable package
1. Deploy to target environment
1. Verify deployment success

#### Synchronize entities

After deployment:

1. Navigate to **Data Management** workspace.
1. Go to **Framework parameters** > **Entity settings**.
1. Select **Refresh entity list**.
1. Verify your finance and operations data entities appear.

#### Verify virtual entities in Dataverse

1. Wait 24-48 hours for automatic publishing (or manually publish).
1. Verify entities appear in Power Apps Maker.
1. Configure change tracking and LTR for each entity.

#### Test end-to-end

To create test data, follow these steps:

1. Create test header record in source link table.
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

- Source link table created with all fields.
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

- Created base job contract creator class.
- Implemented archive criteria in `createPostJobRequest`.
- Added all child tables with correct JOINs.
- Created BI extension class in BusinessIntelligence model.
- Added LTR configuration for source link table.
- Created type registration class.
- Added archive type to `ArchiveType` enum.
- Type registration runs on startup.
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

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
