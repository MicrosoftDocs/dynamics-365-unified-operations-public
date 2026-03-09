---
title: Add custom tables to archive scenarios
description: Learn how to add related custom tables to existing Microsoft archive scenarios.
author: kehoej99 
ms.author: Weijiesa 
ms.topic: how-to
ms.date: 03/09/2026
ms.custom:
ms.reviewer: twheeloc

---
# Scenario 2: Add custom tables to standard archive scenarios

This article describes how to add related custom tables to existing Microsoft archive scenarios. For example, adding a custom settlement table to the General Ledger archive scenario, or adding custom shipment tracking tables to the Sales Order archive scenario.

## Overview

This scenario applies when you have custom tables that are related to Microsoft-managed tables and should be archived together. The custom tables have foreign key relationships to the standard tables.

**Example scenarios:**
- Custom ledger settlement table related to `GeneralJournalAccountEntry`
- Custom shipment tracking table related to `SalesTable`
- Custom quality inspection table related to `InventJournalTable`

**Components involved:**
- Custom live tables (new)
- Custom history tables (new)
- Custom BI entities (new)
- Job contract creator extension (code required)
- Dataverse configuration

**Code required:** Yes - You must extend the scenario's job contract creator class to add your tables to the archive scope.

## Prerequisites

- Access to Visual Studio with Dynamics 365 finance and operations development tools
- Development environment with Archive framework deployed
- Understanding of parent-child table relationships
- Understanding of job contract builder API
- System Administrator role in Dynamics 365 finance and operations

## Step 1: Create custom live table

**Objective:** Create your custom transaction table that will be included in the archive scope.

### Design table structure

Before creating the table, identify:
1. **Parent table**: Which Microsoft table does this relate to? (for example, `GeneralJournalAccountEntry`, `SalesTable`, `InventJournalTable`)
2. **Relationship type**: One-to-one or one-to-many?
3. **Foreign key**: Which field links to the parent?
4. **Business data**: What additional fields are needed?

### Create table in Visual Studio

1. Right-click project > **Add** > **New Item** > **Table**
2. Name your table using your naming convention:
   - Example: `CustomLedgerTransSettlement`
   - Example: `CustomShipmentTracking`
   - Example: `CustomQualityInspection`

### Add required fields

**Foreign key to parent table:**
- Field name convention: `[ParentTable]RecId` (for example, `TransRecId`, `SalesRecId`)
- Type: Int64
- Relation to parent table's `RecId`

**Segregation fields if needed(match parent table):**
- `DataAreaId` (EDT: DataAreaId) - For legal entity segregation
- `Partition` (EDT: PartitionKey) - For multi-tenant scenarios

**Business-specific fields:**
- Add your custom transaction fields
- Follow Dynamics 365 finance and operations field naming conventions
- Use appropriate Extended Data Types (EDTs)

### Add relation to parent table

1. Expand **Relations** in table designer
2. Right-click > **New** > **Relation**
3. Configure relation:
   - **Name**: Descriptive name (for example, `GeneralJournalAccountEntry`)
   - **Related Table**: Parent table name
   - **Cardinality**: ZeroMore (typically)
4. Add relation constraint:
   - **Field**: Your foreign key field (for example, `TransRecId`)
   - **Related Field**: `RecId` on parent table

**Example table structure:**
```
CustomLedgerTransSettlement
├── RecId (Int64, Primary Key)
├── TransRecId (Int64, Foreign Key to GeneralJournalAccountEntry)
├── DataAreaId (DataAreaId)
├── Partition (PartitionKey)
├── SettlementDate (TransDate)
├── SettlementAmount (AmountMST)
└── SettlementStatus (Enum)
```

### Configure table properties

1. In Visual Studio, select your live table
2. In Properties window, find **ChangeTrackingEnabled**
3. Set value to **Yes**

### Add archive criteria index (Required)

This index is critical for archive job performance and validation.

```xml
<AxTableIndex>
    <Name>ArchiveCriteriaIdx</Name>
    <Fields>
        <AxTableIndexField>
            <DataField>DataAreaId</DataField><!-- Match parent segregation if needed-->
        </AxTableIndexField>
        <AxTableIndexField>
            <DataField>TransRecId</DataField><!-- Foreign key for JOIN -->
        </AxTableIndexField>
    </Fields>
    <IncludedColumns>
        <AxTableIndexIncludedColumn>
            <DataField>RecId</DataField><!-- If not clustered key -->
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

###Add reconciliation index for LTR (Required)

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
> Both indexes are mandatory. Without the criteria index, archive jobs fail validation. Without the reconciliation index, LTR operations perform poorly.

## Step 2: Create history table

**Objective:** Create the corresponding history table for archived data storage.

### Create history table

1. Right-click project > **Add** > **New Item** > **Table**
2. Name: `[YourTable]History`
   - Example: `CustomLedgerTransSettlementHistory`
   - Example: `CustomShipmentTrackingHistory`

### Mirror all fields from live table

Copy all fields from your live table **except**:
- `SysRowVersion` (system-managed)
- `SysDataState` (system-managed)

**All other fields must be identical:**
- Same field names
- Same data types
- Same EDTs
- Same lengths (for strings)

### Configure history table properties

In table properties:
1. **Don't copy unique indexes** from live table

### Add indexes for criteria fields

Add indexes on fields used in archive criteria and queries:

```xml
<AxTableIndex>
    <Name>TransRecIdIdx</Name>
    <Fields>
        <AxTableIndexField>
            <DataField>TransRecId</DataField>
        </AxTableIndexField>
    </Fields>
</AxTableIndex>

<AxTableIndex>
    <Name>SettlementDateIdx</Name>
    <Fields>
        <AxTableIndexField>
            <DataField>SettlementDate</DataField>
        </AxTableIndexField>
    </Fields>
</AxTableIndex>
```

**Why these indexes matter:** They enable efficient querying of archived data and are required for reversal job scheduling to work properly.

## Step 3: Create BI entity

**Objective:** Create a BI entity to enable Dataverse virtual entity for long-term retention.

### Create data entity

1. Right-click project > **Add** > **New Item** > **Data Entity**
2. Name: `[YourTable]BiEntity`
   - Example: `CustomLedgerTransSettlementBiEntity`
   - Example: `CustomShipmentTrackingBiEntity`

### Configure primary data source

1. In entity designer, set **Data Sources**:
   - **Primary Data Source**: Your live table
   - Ensure all fields are included
2. Set field visibility:
   - All fields must have **Public** visibility
   - Fields inaccessible externally should still be public for archive

### Configure critical entity properties

These properties are mandatory for archive and LTR:

| Property | Value | Why Required |
|----------|-------|--------------|
| `IsPublic` | Yes | Makes entity available to Dataverse |
| `PublicEntityName` | Your entity name | External name for OData/Virtual Entity |
| `PublicCollectionName` | Entity name + 's' | OData collection endpoint |
| `Auto Create` | **Yes** | Automatically creates virtual entity in Dataverse |
| `Auto Refresh` | **Yes** | Keeps metadata synchronized |
| `Allow Retention` | **Yes** | Enables LTR capability |
| `Allow Row Version Change Tracking` | **Yes** | Required for change tracking |
| `ChangeTrackingEnabled` | Yes | Tracks data changes |

### Enable rowversion support

Follow the steps in: [Entity change tracking](../data-entities/entity-change-track.md)

**Quick steps:**
1. Add change tracking to data source
2. Enable rowversion on entity
3. Test entity in Data Management workspace

### Build and test entity

```powershell
# Build your model
# Test in Dynamics 365 finance and operations:
# - Navigate to Data Management
# - Export/Import using your entity
# - Verify all fields are accessible
```

## Step 4: Publish virtual entity to Dataverse

**Objective:** Make your entity available in Dataverse for long-term retention.

### Automatic publishing (Recommended)

With `Auto Create = Yes` configured:
1. Virtual entity publishes automatically after first entity sync
2. May take 24-48 hours for automatic publication
3. No manual action required

### Manual publishing (If needed)

If you need immediate publishing or automatic didn't work:

1. Navigate to [Power Platform Admin Center](https://admin.powerplatform.microsoft.com)
2. Select your environment
3. Go to **Settings** > **Product** > **Features**
4. Find **Dynamics 365 Finance and Operations Virtual Entities**
5. Search for your entity
6. Click **Enable** to publish

### Refresh virtual entity metadata (If needed)

If you need to refresh entity metadata after making changes:

**Option 1: Manual refresh via Advanced Find**

1. Navigate to **Advanced Find** in your Dataverse environment
2. Select **Available Finance and Operation entities**
3. Filter **Name** contains your entity name (for example, `customledgertranssettlementbientity`)
4. From results, open the record
5. Click the **Refresh** checkbox
6. Save the record

**Option 2: Using Power Apps Maker Portal**

1. Navigate to [Power Apps Maker Portal](https://make.powerapps.com)
2. Go to **Tables** and find your entity
3. Open the entity and trigger refresh

**Troubleshooting:** See [Virtual entity refresh troubleshooting](https://learn.microsoft.com/dynamics365/fin-ops-core/dev-itpro/sysadmin/archive-faq#case-3-virtual-entity-that-isnt-eligible-for-archival)

### Configure change tracking and LTR

Third parties (ISVs, partners, and customers) have two approaches to configure entities for long-term retention:

#### Approach 1: Manual configuration (Recommended for most scenarios)

This simpler approach is suitable for most implementations. Manually enable change tracking and LTR for each entity in Power Apps Maker.

**Steps:**

1. Navigate to [Power Apps Maker Portal](https://make.powerapps.com)
2. Select your environment > **Tables**
3. Find your virtual entity (for example, `mserp_customledgertranssettlementbientity`)
4. Enable change tracking and long-term retention for the entity

**Detailed instructions:**
- [Enable a table for long-term retention](https://learn.microsoft.com/power-apps/maker/data-platform/data-retention-set#enable-a-table-for-long-term-retention)
- [Enable change tracking for entities](https://learn.microsoft.com/dynamics365/fin-ops-core/dev-itpro/data-entities/entity-change-track)

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

For complete instructions on building and deploying Dataverse solutions, see [Configure Dataverse for long-term retention - Option 2](archive-custom.md#option-2-automated-solution-deployment-advanced).

## Step 5: Extend job contract to include custom table

**Objective:** Modify the archive job contract to include your custom table in the archive scope.

### Locate existing job contract creator

Find the contract creator class for the scenario you're extending:
- General Ledger: `LedgerArchiveAutomationJobRequestCreator`
- Sales Order: `SalesOrderArchiveAutomationJobRequestCreator`
- Inventory Journal: `InventJournalArchiveAutomationJobRequestCreator`

### Create extension in BusinessIntelligence model

> [!IMPORTANT]
> Create this extension in the **BusinessIntelligence** model, not your base model. This ensures proper layering and dependency management.

1. In BusinessIntelligence model project, create new class
2. Name: `[ExistingCreator]_[YourModel]_Extension`
3. Add extension attribute:

```xpp
using Microsoft.Dynamics.Archive.Contracts;

[ExtensionOf(classStr(LedgerArchiveAutomationJobRequestCreator))]
public final class LedgerArchiveAutomationJobRequestCreator_CustomExtension
{
    // Extension logic here
}
```

### Extend createPostJobRequest method

Use Chain of Command to extend the method that builds job contracts:

```xpp
public ArchiveJobPostRequest createPostJobRequest(var _criteria)
{
    // Call base implementation to get existing contract
    ArchiveJobPostRequest postRequest = next createPostJobRequest(_criteria);
    
    // Add your custom table
    postRequest = this.addCustomTableForLongTermRetention(postRequest, _criteria);
    
    return postRequest;
}
```

### Implement method to add custom table

```xpp
private ArchiveJobPostRequest addCustomTableForLongTermRetention(
    ArchiveJobPostRequest _postRequest,
    var _criteria)
{
    // Construct builder from existing request
    ArchiveServiceArchiveJobPostRequestBuilder builder = 
        ArchiveServiceArchiveJobPostRequestBuilder::constructFromArchiveJobPostRequest(_postRequest);
    
    // Add custom table with parent, history, and entity
    builder.addSourceTableForLongTermRetention(
        ArchiveServiceSourceTableConfiguration::newForSourceTable(
            tableStr(CustomLedgerTransSettlement),              // Live table
            tableStr(CustomLedgerTransSettlementHistory),       // History table
            tableStr(mserp_customledgertranssettlementbientity), // BI entity (Dataverse name)
            tableStr(GeneralJournalAccountEntry)))              // Parent table
        
        // Define JOIN condition to parent
        .addJoinCondition(
            fieldStr(CustomLedgerTransSettlement, TransRecId),
            ArchiveServiceOperator::Equals,
            fieldStr(GeneralJournalAccountEntry, RecId))
        
        // Add WHERE conditions (match parent table criteria)
        .addWhereCondition(
            fieldStr(CustomLedgerTransSettlement, DataAreaId),
            ArchiveServiceOperator::Equals,
            _criteria.DataAreaId)
        
        // Add Partition condition if parent uses it
        .addPartitionWhereCondition();
    
    // Finalize and return updated contract
    return builder.finalizeArchiveJobPostRequest();
}
```

### Key implementation points

**Parent table specification:**
- Must match exactly the parent table name in the scenario
- Typos in parent table name cause validation failures

**JOIN conditions:**
- Must match actual foreign key relationships
- Use exact field names from both tables
- Only `Equals` operator supported for JOINs

**WHERE conditions:**
- Must include same segregation fields as parent (for example, `DataAreaId`)
- Additional filters are optional
- Use appropriate operators (`Equals`, `GreaterThan`, `LessThan`, etc.)

**Entity name in Dataverse:**
- Use the Dataverse virtual entity name (starts with `mserp_`)
- All lowercase in code
- Example: `tableStr(mserp_customledgertranssettlementbientity)`

## Step 6: Test archive with custom table

**Objective:** Verify custom table is properly included in archive jobs.

### Create test data

1. Create parent table record (for example, journal entry)
2. Create related custom table record with foreign key reference
3. Ensure segregation fields match (`DataAreaId`, etc.)
4. Add meaningful data to test fields

### Create test archive job

1. Navigate to Dynamics 365 finance and operations archive workspace
2. Select the archive type you extended
3. Create archive job with criteria that includes your test data
4. Review job details to verify table count includes your custom table

### Verify job contract

Check Archive service logs for job creation:
- Verify custom table appears in job contract
- Confirm JOIN conditions are correct
- Validate WHERE conditions match criteria

### Test data movement

**Execute archive job:**
1. Run the archive job
2. Monitor job progress
3. Verify job completes successfully

**Verify data in history table:**
```sql
-- Check custom table data moved to history
SELECT * FROM CustomLedgerTransSettlementHistory
WHERE TransRecId = [TestParentRecId]

-- Verify parent-child relationship maintained
SELECT c.*, p.* 
FROM CustomLedgerTransSettlementHistory c
INNER JOIN GeneralJournalAccountEntryHistory p ON c.TransRecId = p.RecId
```

**Verify data in managed data lake:**
- Navigate to Dataverse managed data lake
- Find CSV files for your custom table
- Verify records are present
- Check field values are correct

### Test restore operation

1. Create reversal job for archived data
2. Execute restore
3. Verify custom table data returns to live table
4. Validate parent-child relationships are intact

```sql
SELECT * FROM CustomLedgerTransSettlement WHERE TransRecId = [TestParentRecId]
```

## Related articles

- [Archive customization overview](archive-custom.md)
- [Scenario 1: Add custom fields to Microsoft-managed tables](archive-custom-add-fields.md)
- [Scenario 3: Build your own custom archive scenario](archive-custom-build-scenario.md)
- [Configure Dataverse for long-term retention](archive-custom.md#configure-dataverse-for-long-term-retention)
