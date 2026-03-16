---
title: Add custom fields to archive 
description: Learn how to extend existing Microsoft archive scenarios by adding custom fields to tables, history tables, and entities.
author: kehoej99 
ms.author: Weijiesa 
ms.topic: how-to
ms.date: 03/09/2026
ms.custom:
ms.reviewer: twheeloc

---
# Add custom fields to Microsoft-managed tables

This article describes how to extend existing Microsoft archive scenarios, such as General ledger, Sales order, Inventory journal, by adding custom fields to live tables and ensuring proper synchronization with history tables and finance and operations data entities.

## Overview

This scenario applies when you need to add custom fields to standard Microsoft tables that are already part of an archive scenario. For example, adding a custom status field to `SalesTable` or a custom reference field to `GeneralJournalAccountEntry`.

Components involved:
- Table extensions for live tables
- Table extensions for history tables  
- Entity extensions for finance and operations data entities
- Dataverse virtual entity refresh

No code changes needed - You don't need to modify job contract creator classes. The framework automatically includes your custom fields in archive operations.

## Prerequisites

- Access to Visual Studio with Dynamics 365 finance and operations development tools
- Development environment with Archive framework deployed
- Understanding of X++ extensibility patterns
- System administrator role in Dynamics 365 finance and operations

### Add the custom field to live table
Add your custom field to the source table using table extension.

### Create table extension

To create table extension, follow these steps:
1. In Visual Studio, right-click your project. Click **Add** > **New item**.
2. Select **Dynamics 365 items** > **Data model** > **Table extension**.
3. Name the extension using the pattern: `[TableName]_[YourCompany]_Extension`
   - Example: `SalesTable_Contoso_Extension`
   - Example: `GeneralJournalAccountEntry_Fabrikam_Extension`

### Add your custom field

To add your custom field, follow these steps:
1. Right-click the table extension, click **New** > **Field**.
2. Choose appropriate field type. For example, String, Integer, Date, Enum.
3. Configure field properties:
   - In the **Label** field, enter a descriptive name.
   - In the **Help text** field, explain the custom field's purpose.
   - Configure **Extended Data Type** or base type.
   - Set **Mandatory** property if required.

Example fields:
- `CustomStatus` (Enum) - Custom status tracking.
- `CustomDate` (Date) - Additional date field.
- `CustomReference` (String) - External system reference.
- `CustomAmount` (Real) - Additional calculated amount.

### Configure table properties

> [!IMPORTANT]
> On the source (live) table, set the property **`ChangeTrackingEnabled`** to **`Yes`**. This is required for archive operations to track data changes.

If the Microsoft-managed table doesn't already have this property enabled, you may need to verify with the owning team or check if it's already configured.

### Build and synchronize

```powershell
# Build your model
# Synchronize database to create the field in SQL Server
```

For more information, see [Add fields to tables through extension](../extensibility/add-field-extension.md).

### Add custom fields to history table
Mirror the custom field in the corresponding history table so archived data includes your field.

### Create history table extension

To create a history table extension, follow these steps:
1. In Visual Studio, add new item and select **Table extension**.
2. Name: `[TableName]History_[YourCompany]_Extension`.
   - Example: `SalesTableHistory_Contoso_Extension`.
   - Example: `GeneralJournalAccountEntryHistory_Fabrikam_Extension`.

### Add matching field

To add a matching field, follow these steps:
1. Add the exact same field with identical properties.
2. The **Field name**, **type**, and **metadata** fields must match the live table fields.
3. Don't add indexes to history table extensions.
4. Don't add unique constraints.

> [!IMPORTANT]
> Field matching is critical - The field name, data type, extended data type, and length must be identical between live and history tables. Any mismatch causes archive jobs to fail with schema validation errors.

### Build and synchronize

```powershell
# Build your model
# Synchronize database
```

During archive operations, the framework copies data from live tables to history tables using identical field mappings. If fields don't match, the data copy operation fails.

### Add custom fields to finance and operations data entity

Ensure the Dynamics 365 finance and operations data entity includes your custom field so it's available for Dataverse virtual entities and long-term retention.

### Create entity extension

To create entity extension, follow these steps:
1. In Visual Studio, add new item and select **Data entity extension**.
2. Name: `[EntityName]_[YourCompany]_Extension`.
   - Example: `SalesTableBiEntity_Contoso_Extension`.
   - Example: `GeneraljournalaccountentryBiEntity_Fabrikam_Extension`.

### Add data source field

To add the data source field, follow these steps:
1. In the entity extension designer, expand **Data sources**.
2. Find the data source table that matches your live table.
3. Right-click data source and select **New** > **Field**.
4. Map the field to your custom field from the source table:
   - Set **Data Field** to match your custom field name.
   - Set **Data Method** if using computed fields.
5. Configure field visibility:
   - Set **Visible** = **Yes** for the field to appear in the entity

### Verify entity properties on the base entity

The following properties should already be set correctly on Microsoft-managed entities. Verify they're configured:

- `IsPublic` = Yes 
- `PublicEntityName` = Entity name 
- `Allow Retention` = Yes 
- `Allow Row Version Change Tracking` = Yes 
- `Auto Create` = Yes (enables automatic Dataverse sync)
- `Auto Refresh` = Yes (keeps metadata in sync)

> [!NOTE]
> These properties are on the base entity, not your extension. Microsoft-managed entities already have these configured. You only need to add your field to the entity extension.

### Build and test

```powershell
# Build your model
# Test entity in Data Management workspace
```

### Refresh virtual entity in Dataverse

Update the Dataverse virtual entity metadata to include your custom field.

### Automatic refresh (Recommended)

If the base entity has `Auto Create = Yes` and `Auto Refresh = Yes`:
- Virtual entity metadata synchronizes automatically.
- Changes may take 24-48 hours to propagate.
- No manual action required.

### Manual refresh

If automatic sync hasn't occurred or you need immediate refresh, use one of these methods:

Manual refresh via advanced find
1. Go to **Advanced find** in your Dataverse environment.
2. Select **Available Finance and Operation entities**.
3. Filter the **Name** field to contain your entity name (for example, `generaljournalaccountentrybientity`).
4. From the results, open the record.
5. Select **Refresh**. 
6. Save the record.
7. Wait for refresh to complete.


Using Power Apps Maker Portal
1. Navigate to [Power Apps Maker Portal](https://make.powerapps.com).
2. Select your environment.
3. Go to **Tables** and filter by **Available Finance and Operations entities**.
4. Search for your entity (for example, `mserp_salestablebiEntity`).
5. Open the entity and trigger refresh.

If the refresh doesn't work, see [Virtual entity refresh troubleshooting](archive-faq.md#case-3-virtual-entity-that-isnt-eligible-for-archival).

#### Verify field appears in entity

1. In Power Apps, open the virtual entity.
2. Go to **Columns** tab.
3. Search for your custom field.
4. Verify field type matches your Dynamics 365 finance and operations field.

#### Test archive and restore
Verify that archive jobs include your custom field data throughout the archive lifecycle.

Create test archive job

1. Go to the Dynamics 365 finance and operations archive workspace.
2. Select the relevant archive type. For example, **Sales order archive** or **General ledger archive**.
3. Create a test archive job with criteria that includes records containing your custom field.
4. Ensure test data has values in your custom field.
5. Execute the archive job.

### Verify data movement

Check history table
```sql
-- Verify custom field moved to history
SELECT CustomField, * FROM SalesTableHistory WHERE RecId = [TestRecId]
SELECT CustomField, * FROM GeneralJournalAccountEntryHistory WHERE RecId = [TestRecId]
```

Test restore operation:
1. Create a reversal (restore) job for the archived data.
2. Execute the restore.
3. Verify custom field data returns to live table.
4. Validate field values match original data.

```sql
-- Compare before and after restore
SELECT CustomField, * FROM SalesTable WHERE RecId = [TestRecId]
```

#### Validation and troubleshooting

Validate field synchronization:
- Live table has the custom field. 
- History table has matching field with identical properties.
- Finance and operations data entity extension includes the field.
- Virtual entity in Dataverse shows the field. 

#### Related articles

- [Archive customization overview](archive-custom.md)
- [Add custom tables to standard scenarios](archive-custom-add-tables.md)
- [Build your own custom archive scenario](archive-custom-build-scenario.md)
- [Add fields to tables through extension](../extensibility/add-field-extension.md)
- [Entity change tracking](../data-entities/entity-change-track.md)
