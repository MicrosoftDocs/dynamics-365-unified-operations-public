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
# Archive customization (preview)

This article explains how the archive feature in Microsoft Dynamics 365 Finance and Operations apps supports customization. The archival framework is extensible and allows you to include **custom table fields** and **custom tables** within supported functional scenarios.

### Customization options

- Add custom fields to Microsoft managed tables in standard archive scenarios.  
- Add custom tables to standard archive scenarios.  
- Build your own custom archive scenario using custom tables.  

> [!NOTE]  
> Only custom tables can be included when building your own custom archive scenario.


## Add custom fields in history tables and business intelligence entities

Custom fields that are added to a standard table must be added to the corresponding history table and the business intelligence (BI) entity. The customized BI entity must be refreshed in Dataverse to archive data with Dataverse long term retention.

### History tables

Transactions records are moved to the history tables. The schema of a history table must match its corresponding live table. All columns in the live table must be present in its mirrored history table.

<a id="excl-rule"></a>**Column exclusion rule:** `SysRowVersion` and `SysDataState` columns are added by the platform and managed by using table metadata properties. These columns don't have to be added to the history tables.

### Business entity

Dataverse interacts with finance and Operations through virtual entities. These virtual entities are used to retrieve data from the finance and operations database and save it to the corresponding tables in the Dataverse long term retention.

> [!IMPORTANT]
> Don't add relationships between the entities.

### Required fields on tables

Tables, both live and history, that participate in archive scenarios must include:

- Fields used in WHERE conditions: Any fields that will be used to filter data in your archive job (e.g., `DataAreaId`, `Ledger`, date ranges, status fields)
- Fields used in JOIN conditions: Any fields that relate child tables to parent tables
- **`Partition`**: Typically included for multi-tenant scenarios

> [!NOTE]
> **Virtual entity field naming**: When Dynamics 365 finance and operations tables are published as virtual entities in Dataverse, the Dynamics 365 finance and operations `DataAreaId` column appears as `SysDataAreaId` on the virtual entity. The Archive service automatically handles this naming difference when moving data between Dynamics 365 finance and operations and Dataverse.

### Step 1: Add fields to the history table via extensions

The archival framework requires that all live table columns are mirrored in the corresponding history tables. Use table extensions to add the custom fields to history tables. For more information about how to add fields to history tables through extension in finance and operations apps, see [Add fields to tables through extension](../../dev-itpro/extensibility/add-field-extension.md).

Critical requirements for history tables:
1. All fields from the live table must be present (except `SysRowVersion` and `SysDataState`).
2. Ensure fields used in your archive scenario's join and where conditions are present.
3. Create a clustered index on `RecId`.
4. **Add indexes on fields used in join and where conditions** - these are required for reversal job scheduling.
   - The framework validates that these indexes exist when scheduling reversal jobs.
   - Users can't schedule reversal jobs if these indexes are missing.

### Step 2: Add fields to BI entities via extensions

Additional fields that are added to live tables must be added to the corresponding BI entities.
The following requirements are needed for the BI entities:
1. Follow the standard entity creation process: [Building an entity](../data-entities/data-entities.md#building-an-entity).
2. Include all fields from the source table.
3. Enable change tracking and rowversion support - critical:
   - Archive and LTR require change tracking on entities.
   - Enable rowversion support on the entity.
   - Follow: [Entity change tracking](../data-entities/entity-change-track.md).

### Step 3: Refresh the virtual entity in Dataverse

The customized business entity must be refreshed in Dataverse to archive data in the Dataverse long-term retention store.

## Add indexes to source tables for archive criteria

Archive scenarios require specific indexes on source (live) tables for optimal performance and proper validation.

### Index structure requirements

For root or parent tables requirements:

1. Include all fields used in WHERE conditions for this table.
2. Recommended: Place the primary segregation field (e.g., `DataAreaId`, `Ledger`) as the first field if used.
3. Add as **included columns** (not index fields):
   - `RecId` (only if table doesn't use RecId as clustered key)
   - `SysRowVersion`
   - `SysDataStateCode`

**Example** (Root table with DataAreaId, LoadId, CreatedDateTime, LoadStatus in WHERE conditions):

```xml
<AxTableIndex>
    <Name>ArchiveCriteriaIdx</Name>
    <Fields>
        <AxTableIndexField>
            <DataField>DataAreaId</DataField><!-- Used in WHERE condition -->
        </AxTableIndexField>
        <AxTableIndexField>
            <DataField>LoadId</DataField><!-- Used in WHERE condition -->
        </AxTableIndexField>
        <AxTableIndexField>
            <DataField>CreatedDateTime</DataField>
        </AxTableIndexField>
        <AxTableIndexField>
            <DataField>LoadStatus</DataField>
        </AxTableIndexField>
    </Fields>
    <IncludedColumns>
        <AxTableIndexIncludedColumn>
            <DataField>RecId</DataField>
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

For child tables:

1. Include all fields used in JOIN conditions to the parent table.
2. Include all fields used in WHERE conditions for this table.
3. Recommended: Place the primary segregation field (e.g., `DataAreaId`, `Ledger`) as the first field if used.
4. Add as **included columns** (not index fields):
   - `RecId` (only if table doesn't use RecId as clustered key)
   - `SysRowVersion`
   - `SysDataStateCode`

**Example** (Child table with DataAreaId in WHERE and LoadId in JOIN):

```xml
<AxTableIndex>
    <Name>ArchiveCriteriaIdx</Name>
    <Fields>
        <AxTableIndexField>
            <DataField>DataAreaId</DataField><!-- Used in WHERE condition -->
        </AxTableIndexField>
        <AxTableIndexField>
            <DataField>LoadId</DataField><!-- Used in JOIN to parent -->
        </AxTableIndexField>
    </Fields>
    <IncludedColumns>
        <AxTableIndexIncludedColumn>
            <DataField>RecId</DataField>
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

> [!IMPORTANT]
> These indexes are added to SOURCE (live) tables, NOT to history tables.

## Add new tables to the archive scenario

Additional tables can be included in the archive scenario if they have a direct or indirect relationship with the main live table.

To create a history table that corresponds to the live table in the archive scope, follow these steps:

1. Create a new history table that mirrors all fields from the corresponding live table, including all metadata properties on the live table. See the [column exclusion rule](#excl-rule) earlier in this article.
2. Confirm that fields used in your archive scenario's join and where conditions are present.
3. Don't mirror indexes from the live table in the history table. For most history tables, a clustered index on the `RecId` column is sufficient.
4. **Add indexes on criteria fields** (required for reversal jobs) - include fields used in archive criteria such as date ranges, status fields, etc.
5. Create additional indexes to improve query performance as required and to maintain foreign key relationships.
6. Extend the `ArchiveAutomationJobRequestCreator` class for a scenario to add the new table to archive table chart.

### Code example

The following example shows how to customize the General ledger archive job request creator class to add a new table.

```csharp
using Microsoft.Dynamics.Archive.Contracts;
[ExtensionOf(classStr(LedgerArchiveAutomationJobRequestCreator))]
final class LedgerArchiveAutomationJobRequestCreator_GeneralLedger_Extension
{
    public ArchiveJobPostRequest createPostJobRequestForArchiveTrans(LedgerArchiveTrans _archiveTrans)
    {
        ArchiveJobPostRequest postRequest = next createPostJobRequestForArchiveTrans(_archiveTrans);
        ArchiveServiceArchiveJobPostRequestBuilder builder =
            ArchiveServiceArchiveJobPostRequestBuilder::constructFromArchiveJobPostRequest(postRequest);

        // Use builder to add more live tables, history tables, join conditions and where conditions (if needed)
        // Example: Adding my new general ledger table to archive table graph
        DictTable generalJournalAccountEntryTable = new DictTable(tableNum(GeneralJournalAccountEntry));
        str generalJournalAccountEntryTableName = generalJournalAccountEntryTable.name(DbBackend::Sql);

        DictTable newMyNewGeneralLedgerTable = new DictTable(tableNum(MyNewGeneralLedgerTable));
        str newMyNewGeneralLedgerTableName = newMyNewGeneralLedgerTable.name(DbBackend::Sql);
        DictTable newMyNewGeneralLedgerTableHistory = new DictTable(tableNum(MyNewGeneralLedgerTableHistory));
        str newMyNewGeneralLedgerTableHistoryName = newMyNewGeneralLedgerTableHistory.name(DbBackend::Sql);

        ArchiveServiceSourceTableConfiguration myNewGeneralLedgerTableSourceTable = 
            ArchiveServiceSourceTableConfiguration::newForSourceTable(
                newMyNewGeneralLedgerTableName,
                newMyNewGeneralLedgerTableHistoryName,
                tableStr(MyNewGeneralLedgerTableBiEntity));

        // Add parent table
        myNewGeneralLedgerTableSourceTable.parmParentSourceTableName(generalJournalAccountEntryTableName);

        builder.addSourceTableForLongTermRetention(myNewGeneralLedgerTableSourceTable)
            .addJoinCondition(newMyNewGeneralLedgerTableName,
                newMyNewGeneralLedgerTable.fieldName(fieldNum(MyNewGeneralLedgerTable, GeneralJournalAccountEntryRecId), DbBackend::Sql),
                generalJournalAccountEntryTable.fieldName(fieldNum(GeneralJournalAccountEntry, RecId), DbBackend::Sql));

        return builder.finalizeArchiveJobPostRequest();
    }
}
```

## Setting the job criteria key (Recommended)

The Job criteria key is a partitioning identifier that enables parallel execution of archive jobs. By explicitly providing a job criteria key when building your archive job contract, you enable better performance, scheduling, and observability for your archive scenario.

### What is job criteria key?

The job criteria key identifies the scope or partition of an archive job, allowing the Dataverse scheduler to run multiple archive jobs in parallel for different partitions (typically different legal entities or ledgers). Without a job criteria key, archive jobs may be processed sequentially, impacting performance.

### Common values
- **DataAreaId** - Legal entity identifier (e.g., "USMF", "DEMF") for most archive scenarios.
- **Ledger RecId** - Ledger identifier (converted to string) for ledger-specific archive jobs.
- **Custom partition key** - Any field that represents a logical partition in your scenario.

### How to set job criteria key

Use the **setJobCriteriaKey()** method on the ArchiveServiceArchiveJobPostRequestBuilder.

### Example - Sales order archive using DataAreaId

```csharp
private ArchiveJobPostRequest configurePostRequestWithSalesOrderEntities(
    ArchiveJobPostRequest _postRequest,
    SalesOrderArchiveTrans _archiveTrans)
{
    var builder = ArchiveServiceArchiveJobPostRequestBuilder::constructFromArchiveJobPostRequest(_postRequest);

    // Set job criteria key - typically the DataAreaId for sales orders
    if (strLen(_archiveTrans.DataAreaId) > 0)
    {
        builder.setJobCriteriaKey(_archiveTrans.DataAreaId);
    }

    // Build root source for SalesTable
    builder.addSourceTableForLongTermRetention(
        this.newSourceTableConfiguration(
            tableStr(SalesTable),
            tableStr(SalesTableHistory),
            tableStr(mserp_salestablebiEntity)))
        .addWhereCondition(
            fieldStr(SalesTable, DataAreaId),
            ArchiveServiceOperator::Equals,
            _archiveTrans.DataAreaId);
        // ... additional configuration

    return builder.finalizeArchiveJobPostRequest();
}
```

### Example 2: General Ledger Archive (Using Ledger RecId)

```csharp
private ArchiveJobPostRequest configurePostRequestWithGeneralLedgerEntities(
    ArchiveJobPostRequest _postRequest,
    LedgerArchiveTrans _archiveTrans)
{
    var builder = ArchiveServiceArchiveJobPostRequestBuilder::constructFromArchiveJobPostRequest(_postRequest);

    // Set job criteria key - use Ledger RecId as the partitioning key for general ledger
    if (_archiveTrans.Ledger > 0)
    {
        builder.setJobCriteriaKey(int642Str(_archiveTrans.Ledger));
    }

    // Build root source for GeneralJournalEntry
    builder.addSourceTableForLongTermRetention(
        this.newSourceTableConfiguration(
            tableStr(GeneralJournalEntry),
            tableStr(GeneralJournalEntryHistory),
            tableStr(mserp_generaljournalentrybiEntity)))
        .addWhereCondition(
            fieldStr(GeneralJournalEntry, Ledger),
            ArchiveServiceOperator::Equals,
            _archiveTrans.Ledger);
        // ... additional configuration

    return builder.finalizeArchiveJobPostRequest();
}
```

### Best practices

 - Always include a conditional check** before calling `setJobCriteriaKey()` to ensure the value exists.
 - Convert non-string values** to string (e.g., use `int642Str()` for Int64 values like Ledger RecId).
 - Add a comment explaining what partition key you're using and why.
 - Call setJobCriteriaKey()** early in your builder chain, before adding source tables.

### Conditions for a valid job criteria key

A value is suitable as a job criteria key if it meets these criteria:
 - Represents a logical partition - The value should identify a distinct partition of your data (e.g., legal entity, ledger, customer, project).
 - Consistent within a job - All records processed by the archive job should share the same criteria key value.
 - String-compatible - Must be convertible to string (use `int642Str()`, `int2Str()`, etc. for numeric values).
 - Present in root table - The field should exist in your root source table's where conditions.
 - Non-null and non-empty - Always validate the value exists before passing it to `setJobCriteriaKey()`.

### What is a job criteria key 

The job criteria key is fundamentally a partitioning mechanism that ensures no overlapping records between concurrent archive jobs. When choosing a value for the job criteria key, it must satisfy this critical condition: when running multiple archive jobs within the same scenario, sales orders, each job with a different job criteria key must process completely distinct sets of records with zero overlap.

For example, if you run two sales order archive jobs simultaneously. One with job criteria key "USMF" and another with "DEMF". The records archived by the USMF job must not overlap with records archived by the DEMF job. This is why `DataAreaId` is the ideal choice for most scenarios: it naturally partitions data by legal entity, guaranteeing no overlap.

## Creating a custom Dataverse solution for archive

ISVs, partners, and customers need to create and manage their own Dataverse solutions for their custom archival scenarios, which will be installed and managed separately from the official Microsoft Archival package.

### Create a new Dataverse solution

1. Navigate to [Power Apps](https://make.powerapps.com)
2. Select your target environment (must have Long-Term Retention enabled).
3. Go to **Solutions** > **New solution**.
4. Provide solution details:
   - Display name: `[Your Company] Archive Solution`. For example, Contoso WHS Archive Solution. 
   - Name: Technical name. For example, ContosoWHSArchive.
   - Publisher: Select or create a custom publisher for your organization.
   - Version: Start with 1.0.0.0.
5. Click **Create**.

### Add virtual entities to your solution

1. Open your newly created solution.
2. Click **Add existing** > **Table** > **Virtual table**.
3. Search for and select the BI entities you created in F&O for your archive scenario.
4. Add all entities related to your archive scope.
5. Ensure each entity has:
   - Change tracking enabled
   - Rowversion support configured
   - All required fields from source tables

### Configure table settings for long-term retention

For each virtual entity added:

1. Select the table in your solution.
2. Go to **Settings** > **Advanced options**.
3. Enable **Track changes**. 
4. Under **Data retention**, configure:
   - Enable **Long-term retain this table**
   - Set retention policies as needed
5. Save changes.

### Security permissions

The Archive service uses a first-party application user to perform archival operations, including deleting archived records from active tables.
Archive service first-party application permissions are handled automatically.

> [!IMPORTANT]
> The Archive service first-party application user is safelisted for archive operations in Dataverse. This means you don't need to configure any custom security roles or permissions in Dataverse for the Archive service to perform delete operations on your archive entities.

- The Archive service first-party application user automatically has the required delete permissions for all virtual entities published from Dynamics 365 finance and operations.
- No manual security role configuration is required in Power Platform Admin Center (PPAC) for the Archive service.
- Delete operations on root entities automatically cascade to child entities through Dataverse relationship configurations.

### Dynamics 365 finance and operations end user required permissions

End users who create and manage archive jobs in Dynamics 365 finance and operations must have **System Administrator** role in Dynamics 365 finance and operations. The safelisting mentioned above only applies to the Archive service application performing automated delete operations, not to end users.

Your action - Nothing is required for Archive service permissions and confirm: 
 - Your virtual entities are properly published from Dynamics 365 finance and operations with the correct relationships configured.
 - End users have System Administrator role in Dynamics 365 finance and operations to create and manage archive jobs.

### Export and package your solution

1. In your solution, click **Export**.
2. Choose **Managed** solution (recommended for production deployments).
3. Click **Next** and wait for the export to complete.
4. Download the solution file (`.zip`).

### Deploy to target environments

1. Navigate to the target environment in Power Apps.
2. Go to **Solutions** > **Import**.
3. Upload your solution `.zip` file.
4. Follow the import wizard.

### Version management and updates

When you need to update your archive solution:
1. Increment the solution version (e.g., 1.0.0.0 → 1.1.0.0).
2. Make necessary changes to entities in your F&O environment.
3. Synchronize virtual entities in Dataverse.
4. Export the solution again as managed.
5. Import the updated solution to target environments.

### Considerations for external solutions
- Independent lifecycle - Your custom archive solution operates independently from Microsoft's official Archive package.
- No internal dependencies - Don't reference or depend on Microsoft internal packages.
- Publisher prefix - Use your own publisher prefix for all customizations.
- Field requirements - Ensure all Dynamics 365 finance and operations source tables have `DataAreaId` and `Partition` fields.
- Index requirements - Add proper indexes to source tables with `DataAreaId` as first key column.
- History table indexes - Add indexes on criteria fields to support reversal job scheduling.
- Testing - Test thoroughly in sandbox/dev environments before production deployment.
- Documentation - Maintain documentation of your solution components and deployment process.
- Compatibility - Ensure compatibility with Archive framework version installed in your Dynamics 365 finance and operations environment.

### Integration with archive framework

Your custom solution integrates with the Archive framework through:
 - Virtual entities - The Archive framework discovers and uses your virtual entities automatically when referenced in your job contract.
 - Type registration - Your X++ type registration (created in F&O) references your entities.
 - Job contract - Your `ArchiveAutomationJobRequestCreator` classes reference your BI entities by name.
 - No code changes needed - The Archive framework doesn't require modifications to recognize external solutions.

### Troubleshooting

| Issue | Solution |
|-------|----------|
| Reversal job scheduling fails/blocked | Ensure all history tables have indexes on criteria fields (date ranges, status fields, etc.). The framework validates these indexes exist before allowing reversal job scheduling. |
| Archive job fails with field validation errors | Verify that all source and history tables have required fields: `DataAreaId` and `Partition`. |
| Archive job fails with index validation errors | Ensure source tables have proper indexes with `DataAreaId` as the first key column. Include `RecId`, `Partition`, `SysRowVersion`, and `SysDataStateCode` as included columns. |
| Entities not appearing in Dataverse | Ensure virtual entities are properly published from Dynamics 365 finance and operations and the environment has Virtual Entity provider configured |
| Long-term retention not available | Verify the environment is configured as a managed environment and LTR is enabled. |
| Archive job fails with entity errors | Check that entity names in X++ code exactly match the Dataverse entity names. |
| Permission/security errors | The Archive Service is safelisted - no configuration needed. Ensure end users have System Administrator role in Dynamics 365 finance and operations. |
| User can't create archive jobs | Ensure the end user has System Administrator role in Dynamics 365 finance and operations. |
| Version conflicts | Use semantic versioning and test compatibility before upgrading. |
| Import failures | Ensure all dependencies (Archive Service package, Virtual Entity provider) are installed first. |

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
