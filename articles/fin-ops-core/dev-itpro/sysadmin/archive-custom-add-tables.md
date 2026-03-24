---
title: Add custom tables to archive scenarios
description: Learn how to add related custom tables to existing Microsoft archive scenarios.
author: kehoej99 
ms.author: Weijiesa 
ms.topic: how-to
ms.date: 03/24/2026
ms.custom:
  - bap-template
ms.reviewer: twheeloc

---

# Add custom tables to standard archive scenarios

[!include [banner](../includes/banner.md)]

This article describes how to add related custom tables to existing Microsoft archive scenarios. For example, you can add a custom settlement table to the General Ledger archive scenario or add custom shipment tracking tables to the Sales Order archive scenario.

## Overview

This scenario applies when you have custom tables that are related to Microsoft-managed tables and should be archived together. The custom tables have foreign key relationships to the standard tables.

Example scenarios:

- Custom ledger settlement table related to `GeneralJournalAccountEntry`
- Custom shipment tracking table related to `SalesTable`
- Custom quality inspection table related to `InventJournalTable`

Components involved:

- Custom live tables (new)
- Custom history tables (new)
- Custom finance and operations data entities (new)
- Job contract creator extension (code required)
- Dataverse configuration

Code required - Yes, you must extend the scenario's job contract creator class to add your tables to the archive scope.

## Prerequisites

- Access to Visual Studio with Dynamics 365 finance and operations development tools.
- Development environment with Archive framework deployed.
- Understanding of parent-child table relationships.
- Understanding of job contract builder API.
- System Administrator role in Dynamics 365 finance and operations.

### Create custom live table

Create your custom transaction table that you include in the archive scope.

### Design table structure

Before creating the table, identify:

1. **Parent table**: Which Microsoft table does this table relate to? (for example, `GeneralJournalAccountEntry`, `SalesTable`, `InventJournalTable`)
1. **Relationship type**: Is it one-to-one or one-to-many?
1. **Foreign key**: Which field links to the parent table?
1. **Business data**: What other fields do you need?

### Create table in Visual Studio

1. Right-click the project, and then select **Add** > **New Item** > **Table**.
1. Name your table using your naming convention:
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
- `Partition` (EDT: PartitionKey) - For multitenant scenarios

**Business-specific fields:**

- Add your custom transaction fields
- Follow Dynamics 365 finance and operations field naming conventions
- Use appropriate Extended Data Types (EDTs)

### Add relation to parent table

1. Expand **Relations** in table designer.
1. Right-click, select **New**, and then select **Relation**.
1. Configure relation:
   - **Name**: Descriptive name (for example, `GeneralJournalAccountEntry`).
   - **Related Table**: Parent table name.
   - **Cardinality**: ZeroMore (typically).
1. Add relation constraint:
   - **Field**: Your foreign key field (for example, `TransRecId`).
   - **Related Field**: `RecId` on parent table.

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

1. In Visual Studio, select your live table.
1. In the **Properties** window, find **ChangeTrackingEnabled**.
1. Set the value to **Yes**.

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

### Add reconciliation index for LTR (Required)

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

1. Right-click the project, and then select **Add** > **New Item** > **Table**.
1. Enter a name: `[YourTable]History`.
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

1. **Don't copy unique indexes** from live table.

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

## Step 3: Create finance and operations data entity

**Objective:** Create a finance and operations data entity to enable Dataverse virtual entity for long-term retention.

### Create data entity

1. Right-click the project, and then select **Add** > **New Item** > **Data Entity**.
1. Enter a name: `[YourTable]BiEntity`
   - Example: `CustomLedgerTransSettlementBiEntity`
   - Example: `CustomShipmentTrackingBiEntity`

### Configure primary data source

1. In entity designer, set **Data Sources**:
   - Set **Primary Data Source** to your live table.
   - Ensure all fields are included.
1. Set field visibility:
   - Set all fields to **Public** visibility.
   - Keep fields that are inaccessible externally as public for archive.

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

Follow the steps in [Entity change tracking](../data-entities/entity-change-track.md).

**Quick steps:**

1. Add change tracking to data source.
1. Enable rowversion on entity.
1. Test entity in Data Management workspace.

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

### Automatic publishing (recommended)

When you set `Auto Create` to `Yes`:

1. The virtual entity publishes automatically after the first entity sync.
1. Automatic publication might take 24 to 48 hours.
1. No manual action is required.

### Manual publishing (if needed)

If you need immediate publishing or automatic publishing didn't work:

1. Go to [Power Platform Admin Center](https://admin.powerplatform.microsoft.com).
1. Select your environment.
1. Go to **Settings** > **Product** > **Features**.
1. Find **Dynamics 365 Finance and Operations Virtual Entities**.
1. Search for your entity.
1. Select **Enable** to publish.

### Refresh virtual entity metadata (if needed)

If you need to refresh entity metadata after making changes, use one of the following options:

**Option 1: Manual refresh via Advanced Find**

1. Go to **Advanced Find** in your Dataverse environment.
1. Select **Available Finance and Operation entities**.
1. Filter **Name** to include your entity name (for example, `customledgertranssettlementbientity`).
1. From the results, open the record.
1. Select the **Refresh** checkbox.
1. Save the record.

**Option 2: Using Power Apps Maker Portal**

1. Go to [Power Apps Maker Portal](https://make.powerapps.com).
1. Go to **Tables** and find your entity.
1. Open the entity and trigger refresh.

**Troubleshooting:** See [Virtual entity refresh troubleshooting](archive-faq.md#case-3-virtual-entity-that-isnt-eligible-for-archival).

### Configure change tracking and LTR

Third parties (ISVs, partners, and customers) use two approaches to configure entities for long-term retention:

#### Approach 1: Manual configuration (Recommended for most scenarios)

Use this simpler approach for most implementations. Manually enable change tracking and LTR for each entity in Power Apps Maker.

**Steps:**

1. Go to [Power Apps Maker Portal](https://make.powerapps.com).
1. Select your environment > **Tables**.
1. Find your virtual entity (for example, `mserp_customledgertranssettlementbientity`).
1. Enable change tracking and long-term retention for the entity.

**Detailed instructions:**

- [Enable a table for long-term retention](/power-apps/maker/data-platform/data-retention-set#enable-a-table-for-long-term-retention).
- [Enable change tracking for entities](../data-entities/entity-change-track.md).

**Advantages:**

- Simple and straightforward.
- No solution management expertise required.
- Quick to implement.

#### Approach 2: Automated solution deployment (Advanced)

Build Dataverse solutions that package your entity configurations for automated deployment across multiple environments.

**Best for:**

- Multiple environments requiring consistent configuration.
- Organizations with established ALM processes.
- Scenarios requiring version-controlled configurations.

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
> Create this extension in the **BusinessIntelligence** model, not your base model. This approach ensures proper layering and dependency management.

1. In the BusinessIntelligence model project, create a new class.
1. Name: `[ExistingCreator]_[YourModel]_Extension`.
1. Add the extension attribute.

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
            tableStr(mserp_customledgertranssettlementbientity), // Finance and operations data entity (Dataverse name)
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
- Other filters are optional
- Use appropriate operators (`Equals`, `GreaterThan`, `LessThan`, etc.)

**Entity name in Dataverse:**

- Use the Dataverse virtual entity name (starts with `mserp_`)
- Use all lowercase in code
- Example: `tableStr(mserp_customledgertranssettlementbientity)`

## Step 6: Test archive with custom table

**Objective:** Verify custom table is properly included in archive jobs.

### Create test data

1. Create parent table record, such as a journal entry.
1. Create related custom table record with foreign key reference.
1. Ensure segregation fields match, like `DataAreaId`.
1. Add meaningful data to test fields.

### Create test archive job

1. Go to the Dynamics 365 Finance and Operations archive workspace.
1. Select the archive type you extended.
1. Create archive job with criteria that includes your test data.
1. Review job detail to verify table count includes your custom table.

### Verify job contract

Check archive service logs for job creation:

- Verify custom table appears in job contract.
- Confirm JOIN conditions are correct.
- Validate WHERE conditions match criteria.

### Test data movement

**Execute archive job:**

1. Run the archive job.
1. Monitor job progress.
1. Verify the job completes successfully.

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

- Go to Dataverse managed data lake.
- Find CSV files for your custom table.
- Verify records are present.
- Check field values are correct.

### Test restore operation

1. Create reversal job for archived data.
1. Run the restore job.
1. Verify custom table data returns to live table.
1. Validate parent-child relationships are intact.

```sql
SELECT * FROM CustomLedgerTransSettlement WHERE TransRecId = [TestParentRecId]
```

## Related articles

- [Archive customization overview](archive-custom.md).
- [Scenario 1: Add custom fields to Microsoft-managed tables](archive-custom-add-fields.md).
- [Scenario 3: Build your own custom archive scenario](archive-custom-build-scenario.md).
- [Configure Dataverse for long-term retention](archive-custom.md#configure-dataverse-for-long-term-retention).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
