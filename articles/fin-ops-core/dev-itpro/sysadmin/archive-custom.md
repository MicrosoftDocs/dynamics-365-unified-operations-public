---
title: Archive customization
description: Learn about how the archive feature in Microsoft Dynamics 365 finance and operations apps supports table customizations, including code examples.
author: kehoej99 
ms.author: Weijiesa 
ms.topic: how-to
ms.date: 01/27/2026
ms.custom:
ms.reviewer: twheeloc

---
# Archive customization

This article explains how the archive feature in Microsoft Dynamics 365 finance and operations apps supports customization. The archival framework is extensible and allows you to include custom table fields and custom tables within supported functional scenarios.

## Customization scenarios

The archive framework supports three customization scenarios:

- **Scenario 1: Add custom fields** to Microsoft-managed tables in standard archive scenarios (for example, General Ledger, Sales Order)
- **Scenario 2: Add custom tables** to standard archive scenarios
- **Scenario 3: Build your own custom archive scenario** using custom tables (Preview)

> [!NOTE]  
> **Custom scenario limitation**: When building your own custom archive scenario (Scenario 3), you must use only custom tables. Custom scenarios can't reference Microsoft-managed tables, even as join or lookup dependencies.

## Step-by-step: Creating archive objects

Implementing archive customization requires creating and configuring multiple interconnected objects. Understanding this complete architecture helps you plan and execute your customization successfully.

### Object creation sequence

Follow this sequence to ensure dependencies are correctly established:

### 1. Tables in Dynamics 365 finance and operations

**Live tables** - The source transaction tables containing active business data

**Implementation approach by scenario:**
- **Scenario 1 (Custom fields)**: Use table extensions to add fields to existing Microsoft-managed tables
- **Scenario 2 & 3 (Custom tables)**: Create new table definitions from scratch

**Required table property:**
- Set **`ChangeTrackingEnabled`** property to **`Yes`** on all source (live) tables to enable change tracking for archive operations

**History tables** - Mirror tables that store archived historical data

**Purpose**: Store archived data that is finalized but still needed for infrequent access, reporting, or analytics. History tables use less storage optimization and reduced indexing compared to live tables.

**Critical requirements:**
1. **Field mirroring**: Must contain all fields from the live table except `SysRowVersion` and `SysDataState` (these are platform-managed)
2. **Naming convention**: Live table name + "History" suffix (for example, `SalesTable` → `SalesTableHistory`)

**Common mistake to avoid**: Forgetting to add indexes on criteria fields in history tables prevents reversal job scheduling. The framework validates these indexes exist before allowing reversal operations.

### 2. Indexes on live tables

All source (live) tables participating in archive jobs require two types of indexes for optimal performance and proper framework operation.

**Archive criteria index** - Optimizes archive job filtering and data retrieval

**Purpose**: Enables efficient identification and processing of records that meet archive criteria.

**Structure requirements:**

For **root/parent table**:
- Include all fields used in WHERE conditions for this table
- Recommended: Place primary segregation field (`DataAreaId`, `Ledger`) as first field
- Add as included columns (not index fields): `RecId`, `SysRowVersion`, `SysDataStateCode`

For **child tables**:
- Include fields used in JOIN conditions to parent table
- Include fields used in WHERE conditions for this table
- Add as included columns: `RecId`, `SysRowVersion`, `SysDataStateCode`

**Why this matters**: Without proper criteria indexes, archive jobs will perform poorly or fail validation checks during job creation.

**Reconciliation index (ArchiveSysVersionIdx)** - Required for long-term retention

**Purpose**: Enables efficient reconciliation during the LTR marking stage when data is prepared for movement to Dataverse.

**Critical requirements:**
- **Must exist on ALL tables** (both root and child tables) participating in LTR scenarios
- **Exact field sequence**: `SysDataStateCode` followed by `SysRowVersion`
- **Index type**: Non-clustered index
- **Naming**: Use `ArchiveSysVersionIdx` for consistency

**Structure:**
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

**Impact if missing**: LTR reconciliation operations will experience severe performance degradation, potentially causing archive jobs to timeout or fail.

### 3. BI entities for Dataverse integration

**Business Intelligence (BI) entities** - Data entities that expose table data as virtual entities in Dataverse

**Purpose**: Enable Dataverse to access Dynamics 365 finance and operations data through virtual entities, allowing archive data to be stored in Dataverse long-term retention with minimal SQL Server footprint.

**Entity naming convention**: `[TableName]BiEntity` (for example, `SalesTableBiEntity`, `CustomModuleHeaderBiEntity`)

**Critical entity properties that must be configured:**

| Property | Required Value | Purpose |
|----------|---------------|---------|
| `IsPublic` | Yes | Makes entity available outside Dynamics 365 finance and operations |
| `PublicEntityName` | Entity name | Name exposed to external systems |
| `PublicCollectionName` | Entity name + 's' | Collection name for OData endpoints |
| `Allow Retention` | Yes | Enables long-term retention capability |
| `Allow Row Version Change Tracking` | Yes | Enables change tracking for incremental sync |
| `Auto Create` | Yes | Automatically creates virtual entity in Dataverse |
| `Auto Refresh` | Yes | Keeps metadata synchronized with Dataverse |

### 4. Job contract creator classes

**Archive job request creator** - X++ classes that build the archive job contract specifying what to archive and how

**Purpose**: Constructs the job contract that tells the Archive service which tables to process, how they're related, what criteria to use for filtering, and which entities to use for Dataverse.

**Two-class pattern for proper layering:**

**Base class** (in your module):
- Contains business logic for archive scenario
- Defines table relationships
- Handles criteria validation
- Does NOT reference entity names (to avoid circular dependencies)

**Extension class** (in BusinessIntelligence model):
- Extends the base class using Chain of Command
- Adds entity (BI entity) references
- Configures Dataverse integration
- Uses `ArchiveServiceArchiveJobPostRequestBuilder` API

**Why this split?** BusinessIntelligence model references data entities. Your base module shouldn't have dependencies on BusinessIntelligence. This layering prevents circular dependencies and maintains clean architecture.

**Key builder methods:**
- `addSourceTableForLongTermRetention()` - Adds a table to archive scope with its history table and BI entity
- `addWhereCondition()` - Adds filtering criteria (for example, date ranges, status)
- `addJoinCondition()` - Defines parent-child table relationships
- `setJobCriteriaKey()` - Sets partition key for parallel execution
- `finalizeArchiveJobPostRequest()` - Builds final contract

**Parent-child relationships:**
- Root tables have no parent specified
- Child tables must specify their parent table name
- Framework validates relationships exist
- JOIN conditions must match actual foreign key relationships

### 5. Dataverse configuration

After creating all Dynamics 365 finance and operations objects, configure Dataverse to enable long-term retention. You have two options: manual configuration (simpler) or automated solution deployment (for multiple environments).

For complete configuration steps and considerations, see [Configure Dataverse for long-term retention](#configure-dataverse-for-long-term-retention).

### Development workflow summary

**Typical development sequence:**

1. **Design phase**: Identify tables, relationships, and archive criteria
2. **Create live tables**: Extend existing or create new tables with proper fields
3. **Create history tables**: Mirror live tables with appropriate indexes
4. **Add indexes**: Both criteria and reconciliation indexes on live tables
5. **Create BI entities**: With all required properties configured
6. **Publish entities**: Let `Auto Create` publish to Dataverse automatically (or manual publish)
7. **Create job contract**: Base class + BI extension
8. **Configure Dataverse**: Enable CT and LTR (manual or solution-based)
9. **Test**: Create test archive job and verify data movement

**For detailed implementation steps, see the scenario-specific guides:**
- [Add custom fields to Microsoft-managed tables](archive-custom-add-fields.md)
- [Add custom tables to standard scenarios](archive-custom-add-tables.md)
- [Build your own custom archive scenario](archive-custom-build-scenario.md)

## Implementation scenarios

Choose the scenario that matches your customization needs:

### Scenario 1: Add custom fields to Microsoft-managed tables

Extend existing archive tables (like General Ledger or Sales Order) by adding custom fields through table and entity extensions.

**Use when:** You need to archive additional fields on standard Microsoft tables.

[View detailed implementation guide →](archive-custom-add-fields.md)

### Scenario 2: Add custom tables to standard scenarios

Add your custom tables as related data to existing Microsoft archive scenarios (for example, custom settlement tables linked to General Ledger).

**Use when:** You have custom tables with foreign key relationships to Microsoft-managed tables.

[View detailed implementation guide →](archive-custom-add-tables.md)

### Scenario 3: Build custom archive scenario

Create a complete new archive scenario for your custom business data, independent of Microsoft scenarios.

> [!IMPORTANT]
> Custom scenarios must include **only custom tables**. Custom scenarios must not reference Microsoft-managed tables at all, even as join or lookup dependencies.

**Use when:** You have standalone custom transaction data unrelated to Microsoft tables.

[View detailed implementation guide →](archive-custom-build-scenario.md)

## Configure Dataverse for long-term retention

After creating your custom tables, entities, and indexes in Dynamics 365 finance and operations, you need to configure Dataverse to enable long-term retention. Third parties (ISVs, partners, and customers) have two options:

- **Option 1: Manual configuration (Simpler)** - Manually enable change tracking and LTR from Power Apps Maker portal
- **Option 2: Automated solution (Advanced)** - Build and deploy Dataverse solutions that carry entity configurations

### Option 1: Manual configuration (Recommended for most scenarios)

This approach is simpler and doesn't require solution management expertise. You manually configure each entity in the Power Apps Maker portal.

**Prerequisites:**
- Virtual entities must be published from Dynamics 365 finance and operations with `Auto Create = Yes`
- Environment must have Long-Term Retention enabled
- You must have appropriate permissions in Power Apps

**Steps:**

1. Navigate to [Power Apps Maker Portal](https://make.powerapps.com)
2. Select your target environment
3. Go to **Tables** and filter by "Available Finance and Operations Entities"
4. Find your custom virtual entities (for example, `mserp_customtablebientity`)
5. For each entity, enable change tracking and long-term retention
6. Repeat for all entities in your archive scope

**Detailed instructions:**
- [Enable a table for long-term retention](/power-apps/maker/data-platform/data-retention-set#enable-a-table-for-long-term-retention)
- [Enable change tracking for entities](../data-entities/entity-change-track.md)

**Advantages:**
- Simple and straightforward
- No solution management required
- Quick to implement
- Easy to modify configurations

**Disadvantages:**
- Manual configuration needed for each environment
- No automated deployment across environments
- Configuration not tracked in source control

### Option 2: Automated solution deployment (Advanced)

This approach involves creating a Dataverse solution that packages your entity configurations for automated deployment across environments.

**Prerequisites:**
- Understanding of Dataverse solutions
- Development environment for solution creation
- Deployment pipeline for solution distribution

**Steps:**

#### Create a new Dataverse solution

1. Navigate to [Power Apps](https://make.powerapps.com)
2. Select your development environment
3. Go to **Solutions** > **New solution**
4. Provide solution details:
   - **Display name**: `[Your Company] Archive Solution` (for example, "Contoso WHS Archive Solution")
   - **Name**: Technical name (for example, `ContosoWHSArchive`)
   - **Publisher**: Select or create a custom publisher for your organization
   - **Version**: Start with 1.0.0.0
5. Click **Create**

#### Add virtual entities and configure settings

1. Open your solution
2. Click **Add existing** > **Table** > **Virtual table**
3. Search for and select your BI entities
4. Add all entities related to your archive scope
5. For each entity:
   - Go to table **Settings** > **Advanced options**
   - Enable **Track changes**
   - Enable **Long-term retain this table**
6. Save all changes

> [!NOTE]
> When you complete step 5 above, Power Apps automatically updates your solution's `Customizations.xml` file with the change tracking and LTR metadata. You don't need to manually edit XML files unless you're building advanced automation pipelines or want to bypass the UI configuration.

<details>
<summary><b>Understanding Customizations.xml (Reference)</b></summary>

When you enable change tracking and LTR through the Power Apps UI (step 5 above), these settings are stored in your solution's `Customizations.xml` file. This section shows what that file contains for reference and troubleshooting purposes.

**The Customizations.xml file contains two critical sections:**

1. **Entity change tracking configuration** - Enables change tracking for each entity
2. **LTR metadata configuration** - Enables long-term retention for each entity

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

**When to manually edit Customizations.xml:**
- Building CI/CD pipelines that need to programmatically configure entities
- Bulk-configuring many entities without using the UI
- Troubleshooting solution deployment issues
- Advanced ALM scenarios requiring version control of exact XML structure

</details>

#### Export and package your solution

1. In your solution, click **Export**.
2. Choose **Managed** solution (recommended for production deployments).
3. Click **Next** and wait for the export to complete.
4. Download the solution file (`.zip`).

#### Deploy to target environments

1. Navigate to the target environment in Power Apps.
2. Go to **Solutions** > **Import**.
3. Upload your solution `.zip` file.
4. Follow the import wizard.

#### Version management and updates

When you need to update your archive solution:
1. Increment the solution version (for example, 1.0.0.0 → 1.1.0.0).
2. Make necessary changes to entities in your Dynamics 365 finance and operations environment.
3. Synchronize virtual entities in Dataverse.
4. Export the solution again as managed.
5. Import the updated solution to target environments.

**Advantages:**
- Automated deployment across environments
- Configuration tracked in solution
- Consistent configuration across environments
- Easier to manage multiple entities

**Disadvantages:**
- Requires solution management expertise
- More complex setup process
- Requires versioning and lifecycle management

### Integration with archive framework

Your custom solution integrates with the Archive framework through:
 - Virtual entities - The Archive framework discovers and uses your virtual entities automatically when referenced in your job contract.
 - Type registration - Your X++ type registration (created in F&O) references your entities.
 - Job contract - Your `ArchiveAutomationJobRequestCreator` classes reference your BI entities by name.
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

## Dynamics 365 finance and operations table names in live, history, and Dataverse-managed data lake tables

| Scenario | Live table | History table | BI entity | Dataverse-managed data lake table |
|---|---|---|---|---|
| Finance General ledger | GENERALJOURNALACCOUNTENTRY | GENERALJOURNALACCOUNTENTRYHISTORY | GeneraljournalaccountentryBiEntity | mserp\_GeneraljournalaccountentryBiEntity |
| | GENERALJOURNALACCOUNTENTRY\_W | GENERALJOURNALACCOUNTENTRYHISTORY\_W | GeneraljournalaccountentrywBiEntity | mserp\_GeneraljournalaccountentrywBiEntity |
| | GENERALJOURNALENTRY | GENERALJOURNALENTRYHISTORY | GeneraljournalentryBiEntity | mserp\_GeneraljournalentryBiEntity |
| | GENERALJOURNALENTRY\_W | GENERALJOURNALENTRYHISTORY\_W | GeneraljournalentrywBiEntity | mserp\_GeneraljournalentrywBiEntity |
| | LEDGERCONSOLIDATEHISTREF | LEDGERCONSOLIDATEHISTREFHISTORY | LedgerconsolidatehistrefBiEntity | mserp\_LedgerconsolidatehistrefBiEntity |
| | LEDGERENTRY | LEDGERENTRYHISTORY | LedgerentryBiEntity | mserp\_LedgerentryBiEntity |
| | LEDGERENTRYJOURNAL | LEDGERENTRYJOURNALHISTORY | LedgerentryjournalBiEntity | mserp\_LedgerentryjournalBiEntity |
| | LEDGERENTRYJOURNALIZING | LEDGERENTRYJOURNALIZINGHISTORY | LedgerentryjournalizingBiEntity | mserp\_LedgerentryjournalizingBiEntity |
| | LEDGERTRANSSETTLEMENT | LEDGERTRANSSETTLEMENTHISTORY | LedgertranssettlementBiEntity | mserp\_LedgertranssettlementBiEntity |
| | SUBLEDGERVOUCHERGENERALJOURNALENTRY | SUBLEDGERVOUCHERGENERALJOURNALENTRYHISTORY | SubledgervouchergeneraljournalentryBiEntity |mserp\_SubledgervouchergeneraljournalentryBiEntity |
| Supply Chain Management Sales order | MCRRETURNSALESTABLE | MCRRETURNSALESTABLEHISTORY | McrreturnsalestableBiEntity | mserp\_McrreturnsalestableBiEntity |
| | MCRSALESLINE | MCRSALESLINEHISTORY | McrsaleslineBiEntity | mserp\_McrsaleslineBiEntity |
| | MCRSALESTABLE | MCRSALESTABLEHISTORY | McrsalestableBiEntity | mserp\_McrsalestableBiEntity |
| | RETAILSALESLINE | RETAILSALESLINEHISTORY | RetailsaleslineBiEntity | mserp\_RetailsaleslineBiEntity |
| | RETAILSALESTABLE | RETAILSALESTABLEHISTORY | RetailsalestableBiEntity | mserp\_RetailsalestableBiEntity |
| | SALESLINE | SALESLINEHISTORY | SaleslineBiEntity | mserp\_SaleslineBiEntity |
| | SALESLINE\_BR | SALESLINEHISTORY\_BR | SaleslinebrBiEntity | mserp\_SaleslinebrBiEntity |
| | SALESLINE\_IN | SALESLINEHISTORY\_IN | SaleslineinBiEntity | mserp\_SaleslineinBiEntity |
| | SALESLINE\_W | SALESLINEHISTORY\_W | SaleslinewBiEntity | mserp\_SaleslinewBiEntity |
| | SALESTABLE | SALESTABLEHISTORY | SalestableBiEntity | mserp\_SalestableBiEntity |
| | SALESTABLE\_BR | SALESTABLEHISTORY\_BR | SalestablebrBiEntity | mserp\_SalestablebrBiEntity |
| | SALESTABLE\_RU | SALESTABLEHISTORY\_RU | SalestableruBiEntity | mserp\_SalestableruBiEntity |
| | SALESTABLE\_W | SALESTABLEHISTORY\_W | SalestablewBiEntity | mserp\_SalestablewBiEntity |
| Supply Chain Management Inventory transaction | INVENTTRANSARCHIVE | INVENTTRANSARCHIVEHISTORY | InventtransarchiveBiEntity | mserp\_InventTransArchiveBiEntity |
| Supply Chain Management Inventory Journal | INVENTJOURNALTABLE | INVENTJOURNALTABLEHISTORY | InventjournaltableBiEntity | mserp\_InventjournaltableBiEntity |
| | INVENTJOURNALTABLE_IN | INVENTJOURNALTABLE_INHISTORY | InventjournaltableinBiEntity | mserp\_InventjournaltableinBiEntity |
| | INVENTJOURNALTRANS | INVENTJOURNALTRANSHISTORY | InventjournaltransBiEntity | mserp\_InventjournaltransBiEntity |
| | INVENTJOURNALTRANS_IN | INVENTJOURNALTRANS_INHISTORY | InventjournaltransinBiEntity | mserp\_InventjournaltransinBiEntity |
| Finance Tax Trans | TAXTRANS | TAXTRANSHISTORY | TaxtransBiEntity | mserp\_TaxtransBiEntity |
| | TAXTRANS\_BR | TAXTRANSHISTORY\_BR | TaxtransbrBiEntity | mserp\_TaxtransbrBiEntity |
| | TAXTRANSGENERALJOURNALACCOUNTENTRY | TAXTRANSGENERALJOURNALACCOUNTENTRYHISTORY | TaxtransgeneraljournalaccountentryBiEntity | mserp\_TaxtransgeneraljournalaccountentryBiEntity |
| | TAXTRANS\_IN | TAXTRANSHISTORY\_IN | TaxtransinBiEntity | mserp\_TaxtransinBiEntity |
| | TAXTRANS_IT | TAXTRANSHISTORY\_IT | TaxtransitBiEntity | mserp\_TaxtransitBiEntity |
| | TAXTRANS_REPORTING | TAXTRANSHISTORY_REPORTING | TaxtransreportingBiEntity | mserp\_TaxtransreportingBiEntity |
| | TAXTRANS\_RU | TAXTRANSHISTORY\_RU | TaxtransruBiEntity | mserp\_TaxtransruBiEntity |
| | TAXTRANSSUBLEDGERJOURNALACCOUNTENTRY | TAXTRANSSUBLEDGERJOURNALACCOUNTENTRYHISTORY | TaxtranssubledgerjournalaccountentryBiEntity | mserp\_TaxtranssubledgerjournalaccountentryBiEntity |
| | TAXTRANS\_TH | TAXTRANSHISTORY\_TH | TaxtransthBiEntity | mserp\_TaxtransthBiEntity |
| | TAXTRANS\_W | TAXTRANSHISTORY\_W | TaxtranswBiEntity | mserp\_TaxtranswBiEntity | 
| Commerce transaction | RetailTransactionTable | RetailTransactionTableHistory | RetailTransactionTableBIEntity | mserp\_RetailTransactionTableBIEntity |
| | RetailTransactionCashManagementTrans | RetailTransactionCashManagementTransHistory | RetailTransactionCashManagementTransBIEntity | mserp\_RetailTransactionCashManagementTransBIEntity |
| | RetailTransactionFiscalCustomer | RetailTransactionFiscalCustomerHistory | RetailTransactionFiscalCustomerBIEntity | mserp\_RetailTransactionFiscalCustomerBIEntity |
| | RetailTransactionSupplementaryInvoice | RetailTransactionSupplementaryInvoiceHistory | RetailTransactionSupplementaryInvoiceBIEntity | mserp\_RetailTransactionSupplementaryInvoiceBIEntity |
| | RetailTransactionTable\_RU | RetailTransactionTable\_RUHistory | RetailTransactionTable\_RUBIEntity | mserp\_RetailTransactionTable\_RUBIEntity |
| | RetailTransactionBankedTenderTrans | RetailTransactionBankedTenderTransHistory | RetailTransactionBankedTenderTransBIEntity | mserp\_RetailTransactionBankedTenderTransBIEntity |
| | RetailTransactionValidationError | RetailTransactionValidationErrorHistory | RetailTransactionValidationErrorBIEntity | mserp\_RetailTransactionValidationErrorBIEntity |
| | RetailTransactionTenderDeclarationTrans | RetailTransactionTenderDeclarationTransHistory | RetailTransactionTenderDeclarationTransBIEntity | mserp\_RetailTransactionTenderDeclarationTransBIEntity |
| | RetailTransactionTaxMeasure | RetailTransactionTaxMeasureHistory | RetailTransactionTaxMeasureBIEntity | mserp\_RetailTransactionTaxMeasureBIEntity |
| | RetailTransactionSalesTrans | RetailTransactionSalesTransHistory | RetailTransactionSalesTransBIEntity | mserp\_RetailTransactionSalesTransBIEntity |
| | RetailTransactionPaymentTrans | RetailTransactionPaymentTransHistory | RetailTransactionPaymentTransBIEntity | mserp\_RetailTransactionPaymentTransBIEntity |
| | RetailTransactionPaymentTrans\_BR | RetailTransactionPaymentTrans\_BRHistory | RetailTransactionPaymentTrans\_BRBIEntity | mserp\_RetailTransactionPaymentTrans\_BRBIEntity |
| | RetailTransactionSafeTenderTrans | RetailTransactionSafeTenderTransHistory | RetailTransactionSafeTenderTransBIEntity | mserp\_RetailTransactionSafeTenderTransBIEntity |
| | RetailTransactionPaymentRefundableAmounts | RetailTransactionPaymentRefundableAmountsHistory | RetailTransactionPaymentRefundableAmountsBIEntity | mserp\_RetailTransactionPaymentRefundableAmountsBIEntity |
| | RetailTransactionAdditionalAddressTrans | RetailTransactionAdditionalAddressTransHistory | RetailTransactionAdditionalAddressTransBIEntity | mserp\_RetailTransactionAdditionalAddressTransBIEntity |
| | RetailTransactionAddressTrans | RetailTransactionAddressTransHistory | RetailTransactionAddressTransBIEntity | mserp\_RetailTransactionAddressTransBIEntity |
| | RetailTransactionAffiliationTrans | RetailTransactionAffiliationTransHistory | RetailTransactionAffiliationTransBIEntity | mserp\_RetailTransactionAffiliationTransBIEntity |
| | RetailTransactionAttributeTrans | RetailTransactionAttributeTransHistory | RetailTransactionAttributeTransBIEntity | mserp\_RetailTransactionAttributeTransBIEntity |
| | RetailTransactionChargeTaxMeasure | RetailTransactionChargeTaxMeasureHistory | RetailTransactionChargeTaxMeasureBIEntity | mserp\_RetailTransactionChargeTaxMeasureBIEntity |
| | RetailTransactionChargeTaxTrans | RetailTransactionChargeTaxTransHistory | RetailTransactionChargeTaxTransBIEntity | mserp\_RetailTransactionChargeTaxTransBIEntity |
| | RetailTransactionChargeTaxTransGTE | RetailTransactionChargeTaxTransGTEHistory | RetailTransactionChargeTaxTransGTEBIEntity | mserp\_RetailTransactionChargeTaxTransGTEBIEntity |
| | RetailTransactionCustomerAccountDepositTrans | RetailTransactionCustomerAccountDepositTransHistory | RetailTransactionCustomerAccountDepositTransBIEntity | mserp\_RetailTransactionCustomerAccountDepositTransBIEntity |
| | RetailTransactionDiscountTrans | RetailTransactionDiscountTransHistory | RetailTransactionDiscountTransBIEntity | mserp\_RetailTransactionDiscountTransBIEntity |
| | RetailTransactionFiscalTrans | RetailTransactionFiscalTransHistory | RetailTransactionFiscalTransBIEntity | mserp\_RetailTransactionFiscalTransBIEntity |
| | RetailTransactionFiscalTransExtendedData | RetailTransactionFiscalTransExtendedDataHistory | RetailTransactionFiscalTransExtendedDataBIEntity | mserp\_RetailTransactionFiscalTransExtendedDataBIEntity |
| | RetailTransactionIncomeExpenseTrans | RetailTransactionIncomeExpenseTransHistory | RetailTransactionIncomeExpenseTransBIEntity | mserp\_RetailTransactionIncomeExpenseTransBIEntity |
| | RetailTransactionInfocodeTrans | RetailTransactionInfocodeTransHistory | RetailTransactionInfocodeTransBIEntity | mserp\_RetailTransactionInfocodeTransBIEntity |
| | RetailTransactionKitsDisassemblyTrans | RetailTransactionKitsDisassemblyTransHistory | RetailTransactionKitsDisassemblyTransBIEntity | mserp\_RetailTransactionKitsDisassemblyTransBIEntity |
| | RetailTransactionLoyaltyRewardPointTrans | RetailTransactionLoyaltyRewardPointTransHistory | RetailTransactionLoyaltyRewardPointTransBIEntity | mserp\_RetailTransactionLoyaltyRewardPointTransBIEntity |
| | RetailTransactionMarkupTrans | RetailTransactionMarkupTransHistory | RetailTransactionMarkupTransBIEntity | mserp\_RetailTransactionMarkupTransBIEntity |
| | RetailTransactionNoteTrans | RetailTransactionNoteTransHistory | RetailTransactionNoteTransBIEntity | mserp\_RetailTransactionNoteTransBIEntity |
| | RetailTransactionOrderInvoiceTrans | RetailTransactionOrderInvoiceTransHistory | RetailTransactionOrderInvoiceTransBIEntity | mserp\_RetailTransactionOrderInvoiceTransBIEntity |
| | RetailTransactionTaxTrans\_IN | RetailTransactionTaxTrans\_INHistory | RetailTransactionTaxTrans\_INBIEntity | mserp\_RetailTransactionTaxTrans\_INBIEntity |
| | RetailTransactionTaxTrans | RetailTransactionTaxTransHistory | RetailTransactionTaxTransBIEntity | mserp\_RetailTransactionTaxTransBIEntity |
| | RetailTransactionTaxTransGTE | RetailTransactionTaxTransGTEHistory | RetailTransactionTaxTransGTEBIEntity | mserp\_RetailTransactionTaxTransGTEBIEntity |
| | RetailEodStatementControllerLog | RetailEodStatementControllerLogHistory | RetailEodStatementControllerLogBIEntity | mserp\_RetailEodStatementControllerLogBIEntity |
| | RetailEodStatementEventLog | RetailEodStatementEventLogHistory | RetailEodStatementEventLogBIEntity | mserp\_RetailEodStatementEventLogBIEntity |
| | RetailEodTransactionAggregationHeader | RetailEodTransactionAggregationHeaderHistory | RetailEodTransactionAggregationHeaderBIEntity | mserp\_RetailEodTransactionAggregationHeaderBIEntity |
| | RetailEodTransactionAggregationTrans | RetailEodTransactionAggregationTransHistory | RetailEodTransactionAggregationTransBIEntity | mserp\_RetailEodTransactionAggregationTransBIEntity |
| | RetailEodTransactionError | RetailEodTransactionErrorHistory | RetailEodTransactionErrorBIEntity | mserp\_RetailEodTransactionErrorBIEntity |
| | RetailEodTransactionBankedTenderTrans | RetailEodTransactionBankedTenderTransHistory | RetailEodTransactionBankedTenderTransBIEntity | mserp\_RetailEodTransactionBankedTenderTransBIEntity |
| | RetailEodTransactionIncomeExpenseTrans | RetailEodTransactionIncomeExpenseTransHistory | RetailEodTransactionIncomeExpenseTransBIEntity | mserp\_RetailEodTransactionIncomeExpenseTransBIEntity |
| | RetailEodTransactionInfocodeTrans | RetailEodTransactionInfocodeTransHistory | RetailEodTransactionInfocodeTransBIEntity | mserp\_RetailEodTransactionInfocodeTransBIEntity |
| | RetailEodTransactionOrderInvoiceTrans | RetailEodTransactionOrderInvoiceTransHistory | RetailEodTransactionOrderInvoiceTransBIEntity | mserp\_RetailEodTransactionOrderInvoiceTransBIEntity |
| | RetailEodTransactionPaymentTrans | RetailEodTransactionPaymentTransHistory | RetailEodTransactionPaymentTransBIEntity | mserp\_RetailEodTransactionPaymentTransBIEntity |
| | RetailEodTransactionSafeTenderTrans | RetailEodTransactionSafeTenderTransHistory | RetailEodTransactionSafeTenderTransBIEntity | mserp\_RetailEodTransactionSafeTenderTransBIEntity |
| | RetailEodTransactionSalesTrans | RetailEodTransactionSalesTransHistory | RetailEodTransactionSalesTransBIEntity | mserp\_RetailEodTransactionSalesTransBIEntity |
| | RetailEodTransactionTable | RetailEodTransactionTableHistory | RetailEodTransactionTableBIEntity | mserp\_RetailEodTransactionTableBIEntity |
| | RetailEodTransactionTenderDeclarationTrans | RetailEodTransactionTenderDeclarationTransHistory | RetailEodTransactionTenderDeclarationTransBIEntity | mserp\_RetailEodTransactionTenderDeclarationTransBIEntity |
| | RetailStatementJour | RetailStatementJourHistory | RetailStatementJourBIEntity | mserp\_RetailStatementJourBIEntity |
| | RetailStatementTrans | RetailStatementTransHistory | RetailStatementTransBIEntity | mserp\_RetailStatementTransBIEntity |
| | RetailStatementVoucher | RetailStatementVoucherHistory | RetailStatementVoucherBIEntity | mserp\_RetailStatementVoucherBIEntity |
