---
title: Build a custom archive scenario
description: Learn how to build a complete custom archive scenario using only custom tables.
author: kehoej99 
ms.author: Weijiesa 
ms.topic: how-to
ms.date: 03/09/2026
ms.custom:
ms.reviewer: twheeloc

---
# Scenario 3: Build your own custom archive scenario

This article describes how to build a complete custom archive scenario from scratch using only custom tables. This allows you to archive custom business transactions independently of Microsoft-managed archive scenarios.

## Overview

This scenario is for archiving custom transaction data that isn't related to Microsoft-managed tables. You create a complete new archive scenario with its own job type, UI, and archive scope.

> [!IMPORTANT]
> Custom scenarios must include **only custom tables**. Custom scenarios must not reference Microsoft-managed tables at all, even as join/lookup dependencies. If your custom tables are related to Microsoft tables, use [Scenario 2: Add custom tables to standard scenarios](archive-custom-add-tables.md) instead.

**Components involved:**
- Custom source link table (transaction header)
- Custom table hierarchy (headers, lines, details)
- Custom history tables (one per live table)
- Custom BI entities (one per live table)
- Job contract creator class (two separate classes required)
- Archive service type registration
- Optional UI components

**Code required:** Yes - Extensive X++ development for table structure, job contracts, and type registration.

## Prerequisites

- Access to Visual Studio with Dynamics 365 finance and operations development tools
- Development environment with Archive framework deployed
- Understanding of archive framework architecture
- Understanding of table relationships and hierarchy design
- System Administrator role in Dynamics 365 finance and operations
- Familiarity with X++ programming

## Design planning

Before starting development, plan your archive scenario structure.

### Identify source link table

The **source link table** is the root table that defines what gets archived. Think of it as the "header" table for your archive scope.

### Design table hierarchy

Map out your table relationships:

```
CustomWorkflowHeader (Source Link)
├── CustomWorkflowLine (1-to-many)
│   └── CustomWorkflowLineDetail (1-to-many)
├── CustomWorkflowAttachment (1-to-many)
└── CustomWorkflowComment (1-to-many)
```

**Design principles:**
- Parent-child relationships via `RecId` foreign keys
- Clear relationship cardinality (1-to-1, 1-to-many)
- No circular dependencies

### Define archive criteria

What makes a record eligible for archive?

**Common criteria patterns:**
- Age-based: Records older than X days/months/years
- Status-based: Records with "Completed", "Closed", or "Finalized" status
- Volume-based: Records beyond retention threshold

**Example criteria:**
```xpp
// Workflow completed over 2 years ago
CompletedDate < (today() - 730)
&& WorkflowStatus == WorkflowStatus::Completed
&& DataAreaId == _selectedLegalEntity
```

## Step 1: Create source link table

**Objective:** Create the root table that defines your archive scope.

### Create table

1. Right-click project > **Add** > **New Item** > **Table**
2. Name your source link table:
   - Example: `CustomWorkflowHeader`
   - Example: `IntegrationBatchHeader`
   - Example: `TelemetrySessionHeader`

### Add required fields

**Mandatory fields:**
- `RecId` (Int64, Primary Key) - Automatically added

**Business fields:**
- Transaction identifier (for example, `WorkflowId`, `BatchId`, `SessionId`)
- Status field (for example, `WorkflowStatus`)
- Date fields for criteria (for example, `CreatedDate`, `CompletedDate`)
- Other relevant transaction data

**Example structure:**
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
> On the **source (live) table**, set the property **`ChangeTrackingEnabled`** to **`Yes`**. This enables change tracking required for archive operations.

1. In Visual Studio, select your source link table
2. In Properties window, find **ChangeTrackingEnabled**
3. Set value to **Yes**

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

**Index design rules:**
- First field: Primary segregation (`DataAreaId` or `Partition`)
- Next fields: Criteria fields used in WHERE conditions (status, dates, etc.)
- Included columns: `RecId` (If not clustered), `SysRowVersion`, `SysDataStateCode` (for performance)

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
> **Both indexes are mandatory** on the source link table and all related child tables. Missing indexes cause job failures or poor LTR performance.

## Step 2: Create related child tables

**Objective:** Create all tables in your table hierarchy.

### Create each child table

For each child table in your hierarchy:
1. Create table with appropriate name (for example, `CustomWorkflowLine`, `CustomWorkflowAttachment`)
2. Add foreign key field to parent (for example, `WorkflowHeaderRecId`)
3. Add segregation fields (`DataAreaId`, `Partition`, etc) matching parent
4. Add business-specific fields
5. **Set `ChangeTrackingEnabled` property to `Yes`** on each child table

### Define parent-child relationships

**For each child table, add relation to parent:**

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

**Archive criteria index (includes foreign key):**

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

**Reconciliation index (same on every table):**

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

## Step 3: Create history tables

**Objective:** Create history tables for archived data storage.

### Create history table for each live table

For **every** table in your hierarchy (source link + all children):

1. Create corresponding history table
2. Name: `[LiveTableName]History`
   - Example: `CustomWorkflowHeaderHistory`
   - Example: `CustomWorkflowLineHistory`

### Mirror all fields from live table

Copy all fields from the live table **except**:
- `SysRowVersion` (system-managed, changes on move)
- `SysDataState` (system-managed, changes on move)

**All other fields must be identical:**
- Same names
- Same data types
- Same EDTs
- Same lengths

### Configure history table properties

For each history table:
1. **Don't copy unique indexes** from live table (archived data doesn't need uniqueness)

### Add indexes for query performance

Add indexes on foreign keys and commonly queried fields:

**Why these indexes:** They enable efficient querying of archived data and are required for reversal scheduling.

## Step 4: Create BI entities

**Objective:** Create BI entities to enable Dataverse virtual entities for long-term retention.

### Create entity for each live table

For **every** live table (source link + all children):

1. Right-click project > **Add** > **New Item** > **Data Entity**
2. Name: `[TableName]BiEntity`
   - Example: `CustomWorkflowHeaderBiEntity`
   - Example: `CustomWorkflowLineBiEntity`

### Configure primary data source

1. Set **Data Sources**:
   - **Primary Data Source**: Corresponding live table
   - Include all fields
2. Set field visibility:
   - All fields = **Public**

### Configure mandatory entity properties

These properties are **required** for archive and LTR:

| Property | Value | Purpose |
|----------|-------|---------|
| `IsPublic` | Yes | Exposes entity to Dataverse |
| `PublicEntityName` | Entity name | OData/Virtual Entity name |
| `PublicCollectionName` | Entity name + 's' | OData collection endpoint |
| `Auto Create` | **Yes** | Auto-creates virtual entity in Dataverse |
| `Auto Refresh` | **Yes** | Synchronizes metadata automatically |
| `Allow Retention` | **Yes** | **Required for LTR** |
| `Allow Row Version Change Tracking` | **Yes** | **Required for change tracking** |
| `ChangeTrackingEnabled` | Yes | Enables change detection |

### Enable rowversion support

For each entity, follow: [Entity change tracking](../data-entities/entity-change-track.md)

**Quick steps:**
1. Add change tracking to data source
2. Enable rowversion on entity
3. Test entity in Data Management workspace

## Step 5: Publish virtual entities to Dataverse

**Objective:** Make entities available in Dataverse for LTR.

### Automatic publishing (recommended)

With `Auto Create = Yes` configured:
- Virtual entities publish automatically after entity sync
- May take 24-48 hours
- No manual action required

### Verify entities in Dataverse

1. Navigate to [Power Apps Maker Portal](https://make.powerapps.com)
2. Select environment > **Tables**
3. Search for your entities (for example, `mserp_customworkflowheaderbientity`)
4. Verify all entities in your hierarchy are present

### Refresh virtual entity metadata (If needed)

If you need to refresh entity metadata for any entities in your hierarchy:

**Option 1: Manual refresh via Advanced Find**

1. Navigate to **Advanced Find** in your Dataverse environment
2. Select **Available Finance and Operation entities**
3. Filter **Name** contains your entity name (for example, `customworkflowheaderbientity`)
4. From results, open the record
5. Click the **Refresh** checkbox
6. Save the record
7. Repeat for all entities in your hierarchy

**Option 2: Using Power Apps Maker Portal**

1. Navigate to [Power Apps Maker Portal](https://make.powerapps.com)
2. Go to **Tables** and find each entity
3. Open the entity and trigger refresh
4. Repeat for all entities in your hierarchy

**Troubleshooting:** See [Virtual entity refresh troubleshooting](archive-faq.md#case-3-virtual-entity-that-isnt-eligible-for-archival)

### Configure change tracking and LTR

Third parties (ISVs, partners, and customers) have two approaches to configure entities for long-term retention:

#### Approach 1: Manual configuration

This simpler approach is suitable for most implementations. Manually enable change tracking and LTR for each entity in Power Apps Maker.

**Steps:**

1. Navigate to [Power Apps Maker Portal](https://make.powerapps.com)
2. For each virtual entity in your hierarchy (source link + all children):
   - Find the entity (for example, `mserp_customworkflowheaderbientity`)
   - Enable change tracking
   - Enable long-term retention
3. Repeat for **all entities** in your table hierarchy

> [!IMPORTANT]
> If you skip any entity in the hierarchy, LTR for that table won't work, and archive jobs may fail validation.

**Detailed instructions:**
- [Enable a table for long-term retention](/power-apps/maker/data-platform/data-retention-set#enable-a-table-for-long-term-retention)
- [Enable change tracking for entities](../data-entities/entity-change-track.md)

**Advantages:**
- Simple and straightforward
- No solution management expertise required
- Quick to implement

#### Approach 2: Automated solution deployment (Advanced)

This approach involves building Dataverse solutions that package your entity configurations for automated deployment across multiple environments.

**Best for:**
- Multiple environments requiring consistent configuration
- Organizations with established ALM processes
- Scenarios requiring version-controlled configurations
- Custom scenarios with many entities

For complete instructions on building and deploying Dataverse solutions, see [Configure Dataverse for long-term retention - Option 2](archive-custom.md#option-2-automated-solution-deployment-advanced).

## Step 6: Create job contract creator (Base class)

**Objective:** Create the base job contract creator that defines your archive scope.

### Create base job contract creator class

1. Create new class in your model
2. Name: `Custom[ScenarioName]ArchiveAutomationJobRequestCreator`
   - Example: `CustomWorkflowArchiveAutomationJobRequestCreator`
3. Extend: `ArchiveAutomationJobRequestCreator`

### Implement class structure

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

### Implement createPostJobRequest method

This method constructs the job contract using the builder API:

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

### Implement addChildTables method

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

### Key implementation rules

**Parent table specification:**
- For source link table: Use `.newForSourceTable(liveTable, historyTable)` (no parent)
- For child tables: Use `.newForSourceTable(liveTable, historyTable, entityName, parentTable)`

**JOIN conditions:**
- Must match foreign key relationships exactly
- Only `Equals` operator supported for JOINs
- Field names must be exact (case-sensitive)

**WHERE conditions:**
- Include segregation fields matching parent
- Use field references for dynamic values: `fieldStr(ParentTable, FieldName)`
- Use literal values for static criteria: `WorkflowStatus::Completed`

**Entity names:**
- Use Dataverse virtual entity name (starts with `mserp_`)
- All lowercase
- Example: `tableStr(mserp_customworkflowheaderbientity)`

## Step 7: Create job contract creator (BI Extension)

**Objective:** Create BI extension class to add LTR configuration.

### Create extension in BusinessIntelligence model

> [!IMPORTANT]
> This extension must be in the **BusinessIntelligence** model. Do not create it in your main model.

1. Switch to BusinessIntelligence model project
2. Create new class
3. Name: `Custom[ScenarioName]ArchiveAutomationJobRequestCreator_BI_Extension`
4. Add extension attribute:

```xpp
using Microsoft.Dynamics.Archive.Contracts;

[ExtensionOf(classStr(CustomWorkflowArchiveAutomationJobRequestCreator))]
public final class CustomWorkflowArchiveAutomationJobRequestCreator_BI_Extension
{
    // Extension logic
}
```

### Extend createPostJobRequest with LTR configuration

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

### Implement LTR configuration method

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

### Why two separate classes?

**Base class (in your model):**
- Defines archive scope (what tables)
- Specifies relationships (JOINs)
- No BI entity references

**BI Extension class (in BusinessIntelligence model):**
- Adds LTR configuration
- Links BI entities to tables
- Enables managed data lake access

**This separation enables:**
- Clear dependency management
- Model layering best practices
- Independent testing of archive vs LTR

## Step 8: Register archive service type

**Objective:** Register your custom archive type so it appears in the archive framework.

### Create type registration class

1. Create new class in your model
2. Name: `Custom[ScenarioName]ArchiveServiceTypeRegistration`
3. Implement `ArchiveServiceTypeRegistration` interface

### Implement registration logic

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

### Add archive type to enum

1. Extend `ArchiveType` enum
2. Add new enum value for your scenario:
   - Name: `CustomWorkflow`
   - Label: "Custom workflow archive"

### Ensure registration runs on startup

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

## Step 9: Build and deploy

**Objective:** Compile and deploy all components.

### Build solution

1. Build your main model (tables, base job creator, type registration)
2. Build BusinessIntelligence model (BI entities, extension class)
3. Resolve any compilation errors

### Synchronize database

```powershell
# Sync database to create tables and indexes
# Use Visual Studio: Dynamics 365 > Synchronize Database
```

### Deploy to environment

1. Create deployable package
2. Deploy to target environment
3. Verify deployment success

### Synchronize entities

After deployment:
1. Navigate to **Data Management** workspace
2. Go to **Framework parameters** > **Entity settings**
3. Click **Refresh entity list**
4. Verify your BI entities appear

### Verify virtual entities in Dataverse

1. Wait 24-48 hours for automatic publishing (or manually publish)
2. Verify entities appear in Power Apps Maker
3. Configure change tracking and LTR for each entity

## Step 10: Test end-to-end

**Objective:** Validate complete archive scenario functionality.

### Create test data

1. Create test header record in source link table
2. Create related child records (lines, details, attachments)
3. Ensure segregation fields match (`DataAreaId`, etc.)
4. Set status/date fields to meet archive criteria

### Test archive job creation

1. Navigate to archive workspace
2. Select your custom archive type
3. Create archive job with test criteria
4. Verify job details show correct table count

### Execute archive job

1. Run the archive job
2. Monitor job progress
3. Verify job completes successfully

### Validate data movement

**Check history tables:**
```sql
-- Verify header moved to history
SELECT * FROM CustomWorkflowHeaderHistory WHERE WorkflowId = '[TestID]'

-- Verify child records moved
SELECT * FROM CustomWorkflowLineHistory WHERE WorkflowHeaderRecId = [TestHeaderRecId]
```

**Check managed data lake:**
- Navigate to Dataverse managed data lake
- Find CSV files for all tables
- Verify records present with correct data

**Verify live table cleanup:**
```sql
-- Confirm records removed from live tables
SELECT * FROM CustomWorkflowHeader WHERE WorkflowId = '[TestID]'  -- Should return no rows
```

### Test restore operation

1. Create reversal job
2. Execute restore
3. Verify data returns to live tables
4. Validate parent-child relationships intact

## Validation and troubleshooting

### Common issues and solutions

| Issue | Cause | Solution |
|-------|-------|----------|
| Archive type not appearing in UI | Type registration didn't run | Verify `registerTypes()` is called on startup |
| Job creation fails validation | Missing indexes on live tables | Add `ArchiveCriteriaIdx` and `ArchiveSysVersionIdx` to all tables |
| Child table data not archiving | JOIN conditions incorrect | Verify foreign key field names match exactly |
| Managed data lake missing tables | Entity not configured for LTR | Verify `Allow Retention = Yes` on all BI entities |
| Change tracking failures | Rowversion not enabled | Enable rowversion and `Allow Row Version Change Tracking` on entities |
| Reversal jobs blocked | Missing indexes on history tables | Add foreign key and criteria indexes to history tables |
| Performance issues | Missing reconciliation indexes | Add `ArchiveSysVersionIdx` to all live tables |
| Job contract null reference | Base class method not called | Ensure `next createPostJobRequest()` in extension |

### Pre-deployment checklist

Before deploying to production:

**Tables:**
- [ ] Source link table created with all fields
- [ ] All child tables created with foreign keys
- [ ] Parent-child relationships defined on all child tables
- [ ] `ArchiveCriteriaIdx` added to all tables
- [ ] `ArchiveSysVersionIdx` added to all tables
- [ ] History tables mirror all live tables (except `SysRowVersion`/`SysDataState`)
- [ ] History tables have foreign key indexes
- [ ] No references to Microsoft-managed tables

**BI Entities:**
- [ ] BI entity created for each live table
- [ ] All required properties set (`Auto Create`, `Allow Retention`, etc.)
- [ ] Rowversion enabled on all entities
- [ ] Virtual entities published to Dataverse
- [ ] Change tracking enabled on all virtual entities
- [ ] LTR enabled on all virtual entities in Dataverse

**Code:**
- [ ] Base job contract creator class created
- [ ] `createPostJobRequest` implements archive criteria
- [ ] All child tables added with correct JOINs
- [ ] BI extension class created in BusinessIntelligence model
- [ ] LTR configuration added for source link table
- [ ] Type registration class created
- [ ] Archive type added to `ArchiveType` enum
- [ ] Type registration runs on startup
- [ ] No compilation errors

**Testing:**
- [ ] Test data created for all tables
- [ ] Archive job created successfully
- [ ] Job contract includes all tables
- [ ] Archive job moves data to history tables
- [ ] Managed data lake contains CSV for all tables
- [ ] Live tables cleaned after archive
- [ ] Reversal job restores data correctly
- [ ] Parent-child relationships maintained

## Related articles

- [Archive customization overview](archive-custom.md)
- [Scenario 1: Add custom fields to Microsoft-managed tables](archive-custom-add-fields.md)
- [Scenario 2: Add custom tables to standard scenarios](archive-custom-add-tables.md)
- [Configure Dataverse for long-term retention](archive-custom.md#configure-dataverse-for-long-term-retention)
