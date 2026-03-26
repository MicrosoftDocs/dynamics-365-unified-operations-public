---
title: Archive customization
description: Learn about how the archive feature in Microsoft Dynamics 365 finance and operations apps supports table customizations, including code examples.
author: kehoej99 
ms.author: Weijiesa 
ms.topic: how-to
ms.date: 03/26/2026
ms.custom:
  - bap-template
ms.reviewer: twheeloc

---

# Archive customization

[!include [banner](../includes/banner.md)]

This article explains how the archive feature in Microsoft Dynamics 365 finance and operations apps supports customization. The archival framework is extensible, and you can include custom table fields and custom tables within supported functional scenarios.

## Customization scenarios

The archive framework supports three customization scenarios:

1. Add custom fields to Microsoft-managed tables in standard archive scenarios. For example, General ledger or Sales order.
2. Add custom tables to standard archive scenarios.
3. Build your own custom archive scenario by using custom tables.

> [!NOTE]  
> When building your own custom archive scenario, you only use custom tables. Custom scenarios can't reference Microsoft-managed tables, even as join or lookup dependencies.

## Create archive objects

To implement archive customization, create and configure multiple interconnected objects. 

Follow this sequence to ensure dependencies are correctly established:
 - Tables in Dynamics 365 finance and operations. Live tables are the source transaction tables that contain active business data.
 - Set the **`ChangeTrackingEnabled`** property to **`Yes`** on all source (live) tables to enable change tracking for archive operations.
 - Mirror tables that store archived historical data. These tables store archived data that's finalized but are still needed for infrequent access, reporting, or analytics. History tables use less storage optimization and reduced indexing compared to live tables.
 - Field mirroring - Must contain all fields from the live table except `SysRowVersion` and `SysDataState` (the platform manages these fields).
 - Naming convention - Live table name plus "History" suffix (for example, `SalesTable` → `SalesTableHistory`).

If there are no indexes on criteria fields in history tables, this prevents reversal job scheduling. The framework validates these indexes exist before allowing reversal operations.

### Indexes on live tables
All source (live) tables that participate in archive jobs need two types of indexes for optimal performance and proper framework operation.
 - Archive criteria index - Optimizes archive job filtering, data retrieval and enables efficient identification and processing of records that meet archive criteria.

The structure requirements for root or parent tables:
- Include all fields used in WHERE conditions for this table
- Place primary segregation field (`DataAreaId`, `Ledger`) as first field
- Add as included columns (not index fields): `RecId`, `SysRowVersion`, `SysDataStateCode`

The structure requirements for child tables:
- Include fields used in JOIN conditions to parent table
- Include fields used in WHERE conditions for this table
- Add as included columns: `RecId`, `SysRowVersion`, `SysDataStateCode`

Without proper criteria indexes, archive jobs perform poorly or fail validation checks during job creation.

Reconciliation index (ArchiveSysVersionIdx) - Required for long-term retention and enables efficient reconciliation during the LTR marking stage when data is prepared for movement to Dataverse.

### Requirements
- Must exist on all tables - both root and child tables that participate in LTR scenarios
- Exact field sequence - `SysDataStateCode` followed by `SysRowVersion`
- Index type - Nonclustered index
- Naming - Use `ArchiveSysVersionIdx` for consistency

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

If this is missing, LTR reconciliation operations experience severe performance degradation, potentially causing archive jobs to time out or fail.

### Finance and operations data entities for Dataverse integration

Finance and operations data entities are the data entities that expose table data as virtual entities in Dataverse. By using virtual entities, Dataverse can access Dynamics 365 finance and operations data. You can store archive data in Dataverse for long-term retention with a minimal SQL Server footprint.

Entity naming convention - `[TableName]BiEntity`. For example, `SalesTableBiEntity`, `CustomModuleHeaderBiEntity`.

| Property | Required value | Purpose |
|----------|---------------|---------|
| `IsPublic` | Yes | Makes the entity available outside Dynamics 365 finance and operations. |
| `PublicEntityName` | Entity name | Name exposed to external systems. |
| `PublicCollectionName` | Entity name + 's' | Collection name for OData endpoints. |
| `Allow Retention` | Yes | Enables long-term retention capability. |
| `Allow Row Version Change Tracking` | Yes | Enables change tracking for incremental sync. |
| `Auto Create` | Yes | Automatically creates virtual entity in Dataverse. |
| `Auto Refresh` | Yes | Keeps metadata synchronized with Dataverse. |

### Job contract creator classes

Archive job request creator - X++ classes that build the archive job contract specifying what to archive. This constructs the job contract tells the Archive service which tables to process, how they're related, what criteria to use for filtering, and which entities to use for Dataverse.

Two-class pattern for proper layering:
1. Base class in your module
     - Contains business logic for archive scenario
     - Defines table relationships
     - Handles criteria validation
     - Doesn't reference entity names to avoid circular dependencies
2. Extension class in BusinessIntelligence model
    - Extends the base class by using chain of command
    - Adds finance and operations data entity references
    - Configures Dataverse integration
    - Uses `ArchiveServiceArchiveJobPostRequestBuilder` API

BusinessIntelligence model references data entities and your base module shouldn't have dependencies on BusinessIntelligence. This layering approach prevents circular dependencies and maintains clean architecture.

### Key builder methods

- `addSourceTableForLongTermRetention()` - Adds a table to archive scope with its history table and finance and operations data entity.
- `addWhereCondition()` - Adds filtering criteria, such as date ranges or status.
- `addJoinCondition()` - Defines parent-child table relationships.
- `setJobCriteriaKey()` - Sets partition key for parallel execution.
- `finalizeArchiveJobPostRequest()` - Builds final contract.

### Parent-child relationships
- Root tables have no parent specified.
- Child tables must specify their parent table name.
- Framework validates that relationships exist.
- JOIN conditions must match actual foreign key relationships.

### Dataverse configuration

After you create all Dynamics 365 finance and operations objects, configure Dataverse to enable long-term retention. You have two options: manual configuration (simpler) or automated solution deployment (for multiple environments).

For complete configuration steps and considerations, see [Configure Dataverse for long-term retention](#configure-dataverse-for-long-term-retention).

### Development workflow summary

1. Design phase - Identify tables, relationships, and archive criteria.
1. Create live tables - Extend existing or create new tables with proper fields.
1. Create history tables - Mirror live tables with appropriate indexes.
1. Add indexes - Both criteria and reconciliation indexes on live tables.
1. Create finance and operations data entities - With all required properties configured.
1. Publish entities - Let `Auto Create` publish to Dataverse automatically or manually publish.
1. Create job contract - Base class plus finance and operations data entity extension.
1. Configure Dataverse - Enable CT and LTR (manual or solution-based).
1. Test - Create test archive job and verify data movement.

For additional information about the implementation steps, see the following:
- [Add custom fields to Microsoft-managed tables](archive-custom-add-fields.md)
- [Add custom tables to standard scenarios](archive-custom-add-tables.md)
- [Build your own custom archive scenario](archive-custom-build-scenario.md).

#### Implementation scenarios

Choose the scenario that matches your customization needs:
 - Add custom fields to Microsoft-managed tables - Extend existing archive tables, such as General ledger or Sales order, by adding custom fields through table and entity extensions. For more information, see [View detailed implementation guide](archive-custom-add-fields.md).
 - Add custom tables to standard scenarios - Add your custom tables as related data to existing Microsoft archive scenarios, such as custom settlement tables linked to General ledger. This is can be used when you have custom tables with foreign key relationships to Microsoft-managed tables. For more information, see [View detailed implementation guide](archive-custom-add-tables.md).
 - Build custom archive scenario - Create a new archive scenario for your custom business data, independent of Microsoft scenarios. Use this when you have standalone custom transaction data unrelated to Microsoft tables. For more information, see [View detailed implementation guide](archive-custom-build-scenario.md).

> [!IMPORTANT]
> Custom scenarios must include **only custom tables**. Custom scenarios must not reference Microsoft-managed tables at all, even as join or lookup dependencies.

### Configure Dataverse for long-term retention

After you create your custom tables, entities, and indexes in Dynamics 365 finance and operations, configure Dataverse to enable long-term retention. Third parties (ISVs, partners, and customers) have two options:
1. Manual configuration (Simpler) - Manually enable change tracking and LTR from Power Apps Maker portal.
2. Automated solution (Advanced) - Build and deploy Dataverse solutions that carry entity configurations.

### Manual configuration - recommended for most scenarios
This approach is simpler and doesn't require solution management expertise. You manually configure each entity in the Power Apps Maker portal.

The following prerequisites are required to configure an entity:
- You must publish virtual entities from Dynamics 365 finance and operations with `Auto Create = Yes`.
- Your environment must have long-term retention enabled.
- You must have appropriate permissions in Power Apps.

To manually configure an entity, follow these steps:
1. Go to [Power Apps Maker Portal](https://make.powerapps.com).
1. Select your target environment.
1. Go to **Tables**. Filter by **Available Finance and Operations Entities**.
1. Find your custom virtual entities (for example, `mserp_customtablebientity`).
1. For each entity, enable change tracking and long-term retention.
1. Repeat for all entities in your archive scope.

For more information, see:
- [Enable a table for long-term retention](/power-apps/maker/data-platform/data-retention-set#enable-a-table-for-long-term-retention).
- [Enable change tracking for entities](../data-entities/entity-change-track.md).

### Automated solution deployment
This approach involves creating a Dataverse solution that packages your entity configurations for automated deployment across environments.

Required prerequisites:
- Understanding of Dataverse solutions
- Development environment for solution creation
- Deployment pipeline for solution distribution

#### Create a new Dataverse solution

To create a new Dataverse solution, follow these steps:
1. Go to [Power Apps](https://make.powerapps.com).
1. Select your development environment.
1. Go to **Solutions** > **New solution**.
1. Enter solution details:
   - **Display name** - `[Your Company] Archive Solution` (for example, "Contoso WHS Archive Solution").
   - **Name** - Technical name (for example, `ContosoWHSArchive`).
   - **Publisher** - Select or create a custom publisher for your organization.
   - **Version** - Start with 1.0.0.0.
1. Select **Create**.

#### Add virtual tables and configure settings

1. Open your solution.
1. Select **Add existing** > **Table** > **Virtual table**.
1. Search for and select your finance and operations data tables.
1. Add all tables related to your archive scope.
1. For each table:
   - Go to table **Settings** > **Advanced options**.
   - Enable **Track changes**.
   - Enable **Long-term retain this table**.
1. Save all changes.

> [!NOTE]
> When you complete step 5, Power Apps automatically updates your solution's `Customizations.xml` file with the change tracking and LTR metadata. You don't need to manually edit XML files unless you're building advanced automation pipelines or want to bypass the UI configuration.

<details>
<summary><b>Understanding Customizations.xml (Reference)</b></summary>

When you enable change tracking and LTR through the Power Apps UI (step 5), the system stores these settings in your solution's `Customizations.xml` file. This section shows what that file contains for reference and troubleshooting purposes.

**The Customizations.xml file contains two critical sections:**

1. **Entity change tracking configuration** - Enables change tracking for each entity
1. **LTR metadata configuration** - Enables long-term retention for each entity

**Example Customizations.xml structure:**

```xml
<?xml version="1.0" encoding="utf-8"?>
<ImportExportXml xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <Entities>
    <!-- Configure change tracking for each entity -->
    <Entity>
      <Name LocalizedName="Custom Workflow Header (mserp)" OriginalName="Custom Workflow Header (mserp)">mserp_customworkflowheaderbientity</Name>
      <EntityInfo>
        <entity Name="mserp_customworkflowheaderbientity">
          <ChangeTrackingEnabled>1</ChangeTrackingEnabled>
        </entity>
      </EntityInfo>
    </Entity>
    <Entity>
      <Name LocalizedName="Custom Workflow Line (mserp)" OriginalName="Custom Workflow Line (mserp)">mserp_customworkflowlinebientity</Name>
      <EntityInfo>
        <entity Name="mserp_customworkflowlinebientity">
          <ChangeTrackingEnabled>1</ChangeTrackingEnabled>
        </entity>
      </EntityInfo>
    </Entity>
    <!-- Add more entities as needed -->
  </Entities>
  
  <!-- Other standard solution sections -->
  <Roles />
  <Workflows />
  <FieldSecurityProfiles />
  <Templates />
  <EntityMaps />
  <EntityRelationships />
  <OrganizationSettings />
  <optionsets />
  <CustomControls />
  <SolutionPluginAssemblies />
  <SdkMessageProcessingSteps />
  <EntityDataProviders />
  
  <!-- Configure LTR metadata for each entity -->
  <metadataforarchivals>
    <metadataforarchival extensionofrecordid.logicalname="mserp_customworkflowheaderbientity">
      <isavailableforarchival>1</isavailableforarchival>
      <iscustomizable>1</iscustomizable>
      <name>mserp_customworkflowheaderbientity</name>
      <statecode>0</statecode>
      <statuscode>1</statuscode>
    </metadataforarchival>
    <metadataforarchival extensionofrecordid.logicalname="mserp_customworkflowlinebientity">
      <isavailableforarchival>1</isavailableforarchival>
      <iscustomizable>1</iscustomizable>
      <name>mserp_customworkflowlinebientity</name>
      <statecode>0</statecode>
      <statuscode>1</statuscode>
    </metadataforarchival>
    <!-- Add more entities as needed -->
  </metadataforarchivals>
  
  <EntityAnalyticsConfigs />
  <Languages>
    <Language>1033</Language>
  </Languages>
</ImportExportXml>
```

**Key XML elements:**

| Element | Value | Purpose |
|---------|-------|---------|
| `<ChangeTrackingEnabled>` | `1` | Enables change tracking for the entity |
| `<isavailableforarchival>` | `1` | Enables LTR capability for the entity |
| `<iscustomizable>` | `1` | Allows customization |
| `<statecode>` | `0` | Active state |
| `<statuscode>` | `1` | Active status |

Manually edit Customizations.xml under the following conditions:
- Building CI/CD pipelines that need to programmatically configure entities
- Bulk-configuring many entities without using the UI
- Troubleshooting solution deployment problems
- Advanced ALM scenarios requiring version control of exact XML structure


#### Export and package your solution

1. In your solution, select **Export**.
1. Choose **Managed** solution (recommended for production deployments).
1. Select **Next** and wait for the export to complete.
1. Download the solution file (`.zip`).

#### Deploy to target environments

1. Go to the target environment in Power Apps.
1. Go to **Solutions** > **Import**.
1. Upload your solution `.zip` file.
1. Follow the import wizard.

#### Version management and updates

When you need to update your archive solution:

1. Increment the solution version (for example, 1.0.0.0 → 1.1.0.0).
1. Make necessary changes to entities in your Dynamics 365 finance and operations environment.
1. Synchronize virtual entities in Dataverse.
1. Export the solution again as managed.
1. Import the updated solution to target environments.

### Integration with archive framework

Your custom solution integrates with the Archive framework through:
- Virtual entities - The Archive framework discovers and uses your virtual entities automatically when you reference them in your job contract.
- Type registration - Your X++ type registration references your entities.
- Job contract - Your `ArchiveAutomationJobRequestCreator` classes reference your finance and operations data entities by name.
- No code changes needed - The Archive framework doesn't require modifications to recognize external solutions.

#### Partner solution structure example

```
ContosoWHSArchiveSolution (Managed)
├── Tables (Virtual Entities)
│   ├── mserp_whsloadtableentity (Change Tracking: On, LTR: Enabled)
│   ├── mserp_whsloadlineentity (Change Tracking: On, LTR: Enabled)
│   ├── mserp_whsshipmenttableentity (Change Tracking: On, LTR: Enabled)
│   └── ... (additional entities)
├── Publisher: Contoso (prefix: contoso_)
├── Dependencies
│   └── Archive Service (msdyn_ArchiveService)
└── Version: 1.0.0.0
```

## Table naming reference

For a complete mapping of Microsoft-provided table names across live, history, finance and operations data entity, and Dataverse layers, see [Archive table naming reference](archive-tables-reference.md). This reference is useful when implementing customizations and verifying entity names for archive job contracts.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
