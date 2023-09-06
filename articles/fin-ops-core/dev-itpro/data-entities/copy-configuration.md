---
# required metadata

title: Copy configuration data between companies or legal entities overview
description: This article describes how to use a data project and data templates to move configuration data for a company or legal entity between app instances.
author: Peakerbl
ms.date: 07/25/2019
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.search.region: Global
# ms.search.industry: 
ms.author: peakerbl
ms.search.validFrom: 2017-07-31
ms.dyn365.ops.version: Platform update 7

---
# Copy configuration data between companies or legal entities overview

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-3.md)]

There are two options for copying configuration data in finance and operations:

- To move data between instances, you must first export it from one company and then import it to another company.
- To move data from one legal entity to another legal entity in the same instance, you can use the **Copy into legal entity** feature.

## Export a configuration

The **Data management** workspace is your hub for managing configuration data projects and exporting data packages. To build a configuration, you must define a data project and export the information that is represented by entities.

To create an export configuration data project, follow these step.

1. Open the **Data management** workspace. If you're in Standard view, select **Enhanced view**.
2. Select the **Export** tile.
3. Select **New** to create an export configuration data project, and enter an ID and name for the configuration.
4. Set the operation type for the data project to **Export**, and set the project category to **Configuration**.
5. Add the entities that represent the information that you want to export. You can add entities by using several methods:

    - **Add one entity** – Enter the first part of the name of the entity until it appears in the lookup.
    - **Add multiple entities** – Enter any part of the entity name, use the lookup for the module, enter any part of the tag name, or use the lookup for the entity category to show a list of entities. Press Tab to move focus away from the **Lookup** field and activate the filter. In the grid, select the entities to add.
    - **Add a file** – Browse to a file that contains a name that matches the name of an entity and a file name extension that matches the file name extension that is in your data sources.
    - **Add a template** – Select from a list of templates that you've loaded in your instance.

6. Select a target data format. The system stores the last data format that you selected. Alternatively, if you select a file, the system automatically sets the data format to the data source that matches the file name extension.

    > [!NOTE]
    > Composite entities require XML format.

7. Select **Add**. If you load a template, and the project already includes an entity that matches an entity in the template, the entity in the project will be replaced by the entity in the template. Some templates are very large, and they might take a few seconds to be loaded.
8. Select **Remove entity** to remove one or more selected entities.
9. When you've completed the configuration, select **Export** to start the export. You can monitor the results on the **Execution summary** page that appears.

Before you export a configuration, you might want to use some additional features that can help control the export process:

- To organize the list, use the **Sort by** button to reorder the entities by unit, level, and sequence.
- To change the execution sequence of any of the entities, you can manually edit the unit, level, or sequence. Alternatively, you can use the **Resequence** button to update any entities that you've selected. The **Resequence** button appears only if you select more than one entity. You can change the unit, level, and sequence individually. Alternatively, you can enable multiple changes and make them all at the same time. If you want the unit, level, or sequence to remain unchanged when you change multiple parts of the sequence, set the increment to **0** (zero).
- To add filters to the entity, use the **Filter** button. If you add a filter, the **Filter** button changes to an **Edit** button. The data will be filtered before it's exported. If you've added a template, and the template includes filters, those filters will be added to your project. However, you can modify or remove them as you require.
- If you must change the entity mappings, use the **View map** button. If you've added a template, and the template includes mapping changes, those changes will be applied to your project. However, you can modify them as you require.
- To temporarily prevent the entity from being used when you export a data project, use the check box in the **Disable** column.
- To open the contents of the grid in a Microsoft Excel workbook, use the **Open in Excel** button. Modify the entities as you require, and then use the **Publish** button to upload the changes back.

When the export is completed, complete the following tasks:

- Use the **Download** button on the **Export** page to download the configuration settings.
- Use the **Download package** button in the **Data management** workspace or on the **Execution summary** page to download the configuration settings and the data that was exported.

## Setup considerations for some entities that are used to export configurations

Currently, several entities require additional steps when you build configurations. Follow these recommendations as you build your configurations.

> [!IMPORTANT]
> This list will be updated as the Copy configuration feature is improved.

### Using special-purpose entities

The following entities require special handling when they are used in configurations.

| Area | Entity | Action |
|------|--------|--------|
| System setup | Global address book | The entity no longer exports the records that are created automatically when a company is created. The import no longer accepts those records. |
| GL Shared | Account structures active group | This composite entity will export and import only the active account structures. If you use any other account structure entities, the status of the active account structures will be changed to **Draft**, and you must activate them before they can be used. |
| | Advanced rule structures active group | This composite entity is used in combination with the account structures active group entity. It will export and import only the active advanced rule structures. If you use any other advanced rule structure entities, the status of the advanced rule structures will be changed to **Draft**, and you must activate them before they can be used. |
| | Financial dimension values | All dimension values will be exported, even values that are based on system-defined entities such as projects or customers. Remove the system-defined values before you import them. If you leave the system-defined values in the package, they won't be imported. However, they will be filled as you import the data that backs the system-defined dimension. |
| Workflow | Workflow version | Change the owner for every record in the package data to **Admin**, unless the users in the workflow are already imported. |
| | Workflow expression | Some workflow expressions might be too long for an Excel cell. Use XML instead of Excel as the export format. |
| Tax | Sales tax parameters | The default value for the marginal base calculations method is **Total** for sales tax parameters. The Ledger Parameters entity doesn't set that value. However, the marginal base that some tax codes use, **Line**, will fail validation. A new entity that is named the Sales tax parameters preset entity was created so that you can import the marginal base calculation method first. You can then import tax codes. | 
| Accounts receivable | Customers | The Customers entity was designed to be used for OData scenarios. For configurations, use the Customer definitions entity and the Customer details entity. The Customer definitions entities let you import the basic information about a customer. In this way, you enable entities that require that a customer have that information earlier in the import process. The Customer details entity contains additional information about a customer that you can add after parameters and reference data have been set up. |
| Inventory management | Warehouse locations | Some warehouse locations require a location profile ID. Location profile IDs require a location format. Currently, the location format information must be manually added before the warehouse location. The entities for the location format and location profile were added in version 7.2.3, (App update 3 of the July 2017 release). | 
| Product information management | Products | The Products and Released Products entities should be used for configurations. The Product master and Released product master entities should be used for OData scenarios. |
| | Product document attachments | For attachments to product documents released product documents, you must never skip staging, because additional steps are performed in the staging environment. You must use a data package for export and import, because the export file must be accompanied by a resources folder that contains the attachments. The entities support images, documents, notes, and links. When you export, you will see an image file that has a name that resembles a globally unique identifier (GUID). This file is a valid data package that is required in order to complete the import. |
| | Product attribute values | Product attribute values are assigned only when a user opens the **Attribute values** page from the **Products details** page. Currently, you can't import the values unless this step was performed in the golden build. |
| Procurement | Vendor catalog | See the "Vendor catalogs import" section of [Vendor catalogs in Dynamics AX](https://blogs.msdn.microsoft.com/dynamicsaxscm/2016/05/25/vendor-catalogs-in-dynamics-ax/) on the Supply Chain Management blog. |
| Project | Shared category | The Shared category entity now exposes the following fields: **CATEGORYID**, **CATEGORYNAME**, **EXPENSETYPE**, **USINEXPENSE**, **USINPRODUCTION**, and **USEINPROJECT**. If you change the value of the **USEINEXPENSE** field to **yes**, the **EXPENSETYPE** should be set to one of the valid values that are available in the **Expense type** field on the **Shared category** page. |

### Remove the mapping and apply filters for specific entity fields

In a golden build, customer-specific fields might not be set up. To help guarantee that the import works, you should unmap those fields. For example, workers are stored in many tables, but they might not be set up in a golden build. Filters might also be required for some fields in an entity.

The following entities might have to be unmapped or filtered.

| Area | Entity | Action |
|------|--------|--------|
| System setup | Operating unit | Unmap Manager personnel number unless workers have been imported. |
| | User information | Apply a filter where **ID** isn't equal to **Admin**. Unmap Person name, and use the User to person relationship entity to map system users to directory users. |
| Accounts payable | Vendors | Unmap Purchase site (DefaultPurchaseSite) and Warehouse (DefaultProcurementWarehouseID) unless they are set up. Unmap the vendor bank account ID. The Vendor bank account entity will set up the link to the bank account when it's imported. |
| Accounts receivable | Customer details | Unmap Employee responsible number unless workers have been imported. Unmap Collections contact person (CollectionsContactPersonID) unless workers and their contact information have been imported. Unmap the site (SiteID) and warehouse (WarehouseID) unless they have already been imported. |
| Inventory management | Warehouse current postal address | Unmap Picking store area and Input store area unless Commerce information has been imported. | 
| Product information management | Products | Unmap NMFCCode and STCCCode unless you are adding the transportation management template to your data project. |
| | Released products | Unmap the project category, default product color, default configuration, default product size, and default product style. This entity is self-referencing and hasn't yet been updated to load these fields in a single pass. |
| | Period template | The Period template entity is a shared entity. Although it can be filtered by legal entity, the Period template lines entity doesn't have a **Legal entity** field. To import a single legal entity, you can filter the period template. However, you must currently remove the period template lines that aren't related to that legal entity. |
| | Item coverage group | Unmap Period template ID unless it has already been added manually. |
| Procurement | Vendors | Unmap Purchase site (DefaultPurchaseSite) and Warehouse (DefaultProcurementWarehouseID) unless they are set up. Unmap the vendor bank account ID. The Vendor bank account entity will set up the link to the bank account when it's imported. |
| Sales and marketing | Leads | Unmap LeadOpeningPersonnelNumber, LeadClosingPersonnelNumber, and LeadResponsiblePersonnelNumber unless workers have been imported. |
| | Sales type document entry policies | Unmap IsAtpGenrallyIncludingPlannedOrders. The default for Master planning was changed to be Yes for Disable all planning processes when a legal entity is created. |
| Project management | Projects | Unmap WorkerArchitectPersonelNumber, WorkerRespFinancialPersonelNumber, WorkerResponsiblePersonnelNumber, and WorkerRespSalesPersonelNumber unless workers have been imported. |
| Retail | POS visual profiles | Unmap Pallet because no entity is available at this time. The POS visual profiles entity was added to the Retail template in version 7.2.3, (App update 3 of the July 2017 release). |
| | Retail channel | Unmap Channel profile name (ChannelProfileName) and Live database connection profile name (LiveDatabaseConnectionProfileName) because no entity is available at this time. The Retail channel entity was added to the Retail template in version 7.2.3, (App update 3 of the July 2017 release). |

### Golden builds that have multiple legal entities

The templates can be used to export data from any company in your golden build. When you export both shared data and company data, the templates first export the shared data for all legal entities. They then export the data for the legal entity that you're currently using. You can then switch companies and export the company data for additional legal entities by using projects that don't include the shared entities.

If you're exporting from a golden build that contains multiple legal entities, but you want to import the data from only one of those legal entities, you must apply a filter on the legal entity fields, so that only the data that you require for that legal entity is exported. This filter must remove all data for all legal entities except the legal entity that you want. In some cases, you must complete additional steps to clean up the exported data.

Most of the changes that are listed in the following table occur in the **System setup** and **General ledger** areas. If you export a golden build that uses a single legal entity, you should not require these filters.

The following entities require filters or special handling when you export the data.

| Area | Entity | Action |
|------|--------|--------|
| System setup | Legal entities | Apply a filter to Company. |
| | Number sequence code | The number sequence codes can be shared, or they can be specific to a legal entity. To import all number sequences, you must have the legal entities setup for the number sequences that are stored for a specific legal entity. If you want only shared number sequences, apply a filter to remove the number sequences that are specific to a legal entity. If you want the number sequences only for a specific legal entity, apply a filter to Company.<p>Number sequences can also have scope. You must delete number sequences when the following conditions are met:</p><ul><li>The **SCOPETYPE** value is **DataArea**, and the **SCOPEVALUE** value either isn't equal to the legal entity or is blank.</li><li>The **SCOPETYPE** value is **LegalEntity**, and the **SCOPEVALUE** value isn't equal to the legal entity.</li><li>The **SCOPETYPE** value is **DataAreaFiscalCalendar**, and the **SCOPEVALUE** value isn't equal to the legal entity.</li></ul> |
| | Number sequence references | Number sequence references can also have scope. You must delete the number sequence references when the following conditions are met:<ul><li>The **SCOPETYPE** value is equal to **DataArea**, **DataAreaFiscalCalendar**, or **LegalEntity**.</li><li>The **SCOPEVALUE** value either isn't equal to the legal entity that you want in the data or is blank.</li></ul> |
| | Organization hierarchies | There is no legal entity filter. Manually remove any references to the other legal entities that you aren't importing. For example, if you've set up centralized payments, but you're loading only one legal entity, you must not import the Centralized payments hierarchy. |
| Global address book | Multiple entities | The global address book contains data for all legal entities. All legal entities will be created when you import the data, unless you remove the data for the legal entities that you don't want to load. To help guarantee that other legal entities aren't created, delete all records for those other legal entities. Alternatively, apply a filter to the Legal entity data area (&lt;&gt; blank). You must also remove global address book records that are used in the other legal entities. |
| | Party postal addresses | Address records for legal entities other than the legal entity that you're importing must be manually deleted before import. |
| | Party contacts | Contact records for legal entities other than the legal entity that you're importing must be manually deleted before import. |
| | Workflow | Apply a filter on DataAreaID. Many of the workflow entities can't be filtered for legal entity. Therefore, import failures might occur if you don't remove the data in all workflow entities that are related to legal entities that you don't want. We recommend that you manually set up workflows for this scenario. |
| General ledger | Ledger | Apply a filter to Company. |
| | Ledger fiscal calendar year | Apply a filter to Ledger name. |
| | Ledger fiscal calendar period | Apply a filter to Ledger name. |
| | Main account legal entity overrides | Apply a filter to Company. |
| | Financial dimension value legal entity | Apply a filter to Legal entity. |
| | Financial dimension values | Apply a filter to Legal entity. However, you can't filter out system-defined dimension values. Therefore, you must delete them. Those system-defined dimension values will be restored when you import data for the tables that back the system-defined dimensions. |
| | Journal names | Apply a filter to Voucher series company ID. |
| | Ledger allocation basis source | Apply a filter to Legal entity. |
| | Ledger allocation rule destination | Apply a filter to Company. |
| Accounts receivable | Customer write-off reason code | Apply a filter to Company. |
| Budget | Budget control configuration | Apply a filter to Legal entity. |
| | Budget control configuration activation | Apply a filter to Legal entity. |
| | Budget control cycle model | Apply a filter to Legal entity. |
| | Budget control dimension attribute | Apply a filter to Legal entity. |
| | Budget control documents and journals | Apply a filter to Legal entity. |
| | Budget control group | Apply a filter to Legal entity. |
| | Budget control group criteria | Apply a filter to Legal entity. |
| | Budget control message level | Apply a filter to Legal entity. |
| | Budget control over budget permissions | Apply a filter to Legal entity. |
| | Budget control rule | Apply a filter to Legal entity. |
| | Budget control rule criteria | Apply a filter to Legal entity. |
| | Budget cost elements | Apply a filter to Cost element data area ID. |
| | Budget dimensions | Apply a filter to Legal entity. |
| | Budget plan allocation schedule | Apply a filter to Ledger. |
| | Budget plan process | Apply a filter to Ledger. |
| | Budget plan stage rule | If you applied a filter to Budget plan process, errors might occur when you import stage rules. Because the entity doesn't currently contain a ledger name that can be filtered, it will contain all companies. |
| | Budget plan priority constraint | You will experience the same issue that is described for the Budget plan stage rule entity. |
| | Budget plan process administration | You will experience the same issue that is described for the Budget plan stage rule entity. |
| | Budget transfer rules | Apply a filter to Legal entity. |
| Inventory management | Warehouse current postal address | Apply a filter to Company. |
| | Site current postal address | Apply a filter to Company. |
| | Tracking number groups | The entity automatically filters the Number sequence scope data area by the legal entity. Therefore, you don't require a filter. However, if you must change the legal entity, the legal entity is stored in the table. |
| Retail | POS registers | Apply a filter to Legal entity. This entity was added to the Retail template version 7.2.3, (App update 3 of the July 2017 release). | 
| | Retail store address book | There is no legal entity filter for this entity so the export will include records for all legal entities. This entity was added to the Retail template inversion 7.2.3, (App update 3 of the July 2017 release). |
| | Retail locator group member | There is no legal entity filter for this entity so the export will include records for all legal entities. This entity was added to the Retail template in version 7.2.3, (App update 3 of the July 2017 release). |
| | Retail locator group owner | There is no legal entity filter for this entity so the export will include records for all legal entities. This entity was added to the Retail template in version 7.2.3, (App update 3 of the July 2017 release). |
| | Retail devices | There is no legal entity filter for this entity so the export will include records for all legal entities. This entity was added to the Retail template in version 7.2.3, (App update 3 of the July 2017 release). |

### Changing the legal entity value before import

If you want to change the legal entity ID to another value, the value of all fields that resemble the fields that were listed earlier must be changed to the value of the new legal entity. For example, for Legal entities, change Company from the exported value to a new value in the exported file.

The legal entity ID is stored in many places. Therefore, it can be difficult to make this change, and you might cause errors if you try.

> [!NOTE]
> When you set up a data project to copy into a legal entity, a legal entity filter for the source legal entity is automatically added to any entity field that is determined to be a legal entity field.

### Selecting a single legal entity for export

To export a single legal entity, you can create a Copy into legal entity data project and specify the legal entity to copy as the source legal entity. When you add entities or load templates, that type of project will automatically add legal entity filters. You can then download the package or create a template from it on the **Templates** page. The package or template can then be added to an export project and used to export the legal entity.

## Import a configuration

The **Data management** workspace is also your hub for importing configuration data projects. You can build a configuration project from an existing data project that you exported. Alternatively, you can build a configuration project from individual files that contain data that is formatted correctly for import.

To import a configuration, follow these steps.

1. Open the **Data management** workspace. If you're in Standard view, select **Enhanced view**.
2. Select the **Import** tile.
3. Select **New** to create a configuration data project, and enter an ID and name for the configuration.
4. Set the operation type for the data project to **Import**, and set the project category to **Configuration**.
5. Add the entities that represent the information that you want to copy. You can add entities by using several methods:

    - **Add one entity** – Enter the first part of the name of the entity until it appears in the lookup.
    - **Add multiple entities** – Enter any part of the entity name, use the lookup for the module, enter any part of the tag name, or use the lookup for the entity category to show a list of entities. Press Tab to move focus away from the **Lookup** field and activate the filter. In the grid, select the entities to add.
    - **Add a file** – Browse to a file that contains a name that matches the name of an entity and a file name extension that matches the file name extension that is in your data sources, and the source data format will be set automatically. If you haven't set up the default file name extensions, you must select a source data format before you select the file.
    - **Add a template** – Select from a list of templates that you've loaded in your instance.

    When you load a package, the **Import** page first reads the list of entities from the package. A progress indicator shows how much of the package has been read. After the list of entities is read, the **Import** page starts to load the data in the package. This process can take some time.

6. Select **Remove entity** to remove any selected entities, as required.
7. After you've completed the configuration, select **Import** to start the import. You can monitor the results on the **Execution details** page that appears.

Before you import a configuration, you might want to use some additional features that can help control the import process:

- To organize the list, use the **Sort by** button to reorder the entities by unit, level, or sequence.
- To change the execution sequence of any of the entities, you can manually edit the unit, level, or sequence. Alternatively, you can use the **Resequence** button to update any entities that you've selected.
- If you must change the entity mappings, use the **View map** button.
- To temporarily prevent the entity from being used when you export a data project, use the check box in the **Disable** column.

## Copy into a legal entity

The **Data management** workspace is also your hub for copying configuration information from one legal entity to another. The process resembles an export and import that occur in one step. As in an import, if information that exists in the source legal entity doesn't exist in the destination legal entity, the copy process adds it. If information already exists in the destination legal entity, the copy process updates it.

To copy a configuration from one legal entity to another legal entity in the same instance, follow these steps.

1. Open the **Data management** workspace. If you're in Standard view, select **Enhanced view**.
2. Select the **Copy into legal entity** tile.
3. Select **New** to create a configuration data project, and enter an ID and name for the configuration.
4. Set the operation type for the data project to **Copy into legal entity**, and set the project category to **Configuration**.
5. Select the legal entity that should be the source of the data to copy. By default, the legal entity that you're currently using is selected.
6. On the **Legal entities** FastTab, you can select existing legal entities as a destination, or you can create new legal entities:

    - **Select** – Select one or more legal entities in the list, and then select **Add selected**. The legal entities are added to the list of destination legal entities.
    - **Create** – Enter the legal entity ID, the legal entity name, and the region that the legal entity belongs in. Then select **Create legal entity**. The legal entity is created and added to the list of destination legal entities.

    > [!NOTE]
    > The functionality for creating destination legal entities is available in finance and operations 7.2.3.

7. After you've added the destination legal entities, select **Yes** if the number sequences should be copied. The entities that are required in order to copy the number sequence codes and number sequence references will be added to the project. The execution unit, level, and sequence number for these entities are set to the numbers in the default System and Shared templates. If you aren't using the default templates, adjust the entity sequences so that they are first in the list.
8. If you selected **Yes** for number sequences, select **Yes** or **No** to specify whether those number sequences should be reset to the smallest value.
9. Add the entities that represent the information that you want to copy. You can add entities by using several methods:

    - **Add one entity** – Enter the first part of the name of the entity until it appears in the lookup.
    - **Add multiple entities** – Enter any part of the entity name, use the lookup for the module, enter any part of the tag name, or use the lookup for the entity category to show a list of entities. Press Tab to move focus away from the **Lookup** field and activate the filter. In the grid, select the entities to add.
    - **Add a file** – Browse to a file that contains a name that matches the name of an entity and a file name extension that matches the file name extension that is in your data sources.
    - **Add a template** – Select from a list of templates that you've loaded in your instance.

    To help guarantee that the correct order is maintained, we recommend that you use the default templates. Then add and remove entities to match the data that you want to copy. You can remove the entities that you don't want to copy.

    > [!NOTE]
    > - If an entity has a field that represents the legal entity, a filter will be applied to that entity, so that only the data for the source legal entity is included. The value for that field will be changed to the destination legal entity.
    > - Document, transaction, and composite entities aren't available when you copy to a legal entity.

10. Select **Remove entity** to remove any selected entities, as required.
11. After you've completed the configuration, select **Copy into legal entity** to start the import. The copy process will export the data from the source legal entity into the destination legal entity. Each destination legal entity will have its own import data project. You can monitor the results on the **Execution summary** page that appears. All import projects that are related to the Copy into legal entity project will appear in a list on the left of the page.

Any errors that occur are shown on the **Execution summary** page, just as they are for an import project. You can edit the errors in the staging tables and resubmit the values for each data project.

### Special considerations when you copy into a legal entity

When you copy into a legal entity, you have the same validation that occurs when you import a file. It's important that you test your copy in a test environment, so that you can identify any dependencies that will cause failures. If dependent information isn't included in your list of entities to copy, the entity will show errors when it tries to copy into the legal entity. For example, if a customer has a default site or warehouse, you must use one of these approaches:

- Import the sites and warehouses as part of the copy.
- Manually load the sites and warehouses before you copy the legal entity.
- Unmap the site and warehouse fields before you copy the information.

You might also experience import errors if you copy from one region to another region. For example, you can have 1099 fields in a legal entity in the US region. However, if you try to import those values into a legal entity in a German region, you will see errors on the import. If a template that you load has entities that are incorrect for a region, you will receive an error message that states that the incorrect entity wasn't loaded. However, the rest of the template will continue to be loaded. You should copy only information that is appropriate for the destination region.

The following entities require special handling when they are used to copy into a legal entity.

| Area | Entity | Action |
|------|--------|--------|
| System setup | Number sequences | If you use a number sequence for vendors and customers on the parameters forms and then you copy customers and vendors, you need to make sure that the "Allow user to change to a lower number" settings on the number sequences to Yes. The "No" settings will cause the import to reject vendor and customer numbers since they were created before using numbers lower than the next available number sequence. If you use the Reset to smallest feature, you need to change the "Allow user to change to a higher number" since the vendor and customer numbers are higher than the next available number sequence. |
| System setup | Workflow | Workflow requires additional changes before it can be copied. Workflow copies are not supported at this time. |
| Accounts payable | Vendors | Vendors have many settings that are dependent on the values that come from other entities. For example, if you update the matching settings to require three-way matching but you have vendors set for two-way matching, the vendor will fail validation. If you use auto sequencing for new vendor, you will need to unmap the vendor account before you do the copy into legal entity. In addition, if an auto-sequenced vendor has an invoice account, that vendor account is not transformed and may fail. You may see similar issues in other areas such as vendors in posting accounts and approved vendor list by products. |
| Accounts receivable | Customers | Customers have many settings that are dependent on the values that come from other entities. For example, if you have a default warehouse and site for a customer, you must add sites and warehouses first or the customer will fail validation. The collections contact will also fail if the contact is not available in the new company. If you use auto sequencing for new customers, you will need to unmap the customer account before you do the copy into legal entity. In addition, if an auto-sequenced customer has an invoice account, that invoice account is not transformed and may fail. You may see similar issues in other areas such as customers in posting accounts.|
| Budget | Budget cost elements| There is an issue when importing budget cost elements when using an annual amount and there are budget cost elements in the Earnings basis tab. The issue will be addressed in a future release.|
| Fixed assets | Fixed assets depreciation profile manual schedule| The fixed asset depreciation profile must be processed first. Change the sequence on your data project for fixed asset depreciation profile to 15 (instead of 10). We will update the default templates in the monthly application release 4 to this value.|
| General ledger | Intercompany accounting | The copy into legal entity feature does not support intercompany accounting at this time. The issue will be addressed in a future release.|
| General ledger | Journal names| Only the journal names for the source legal entity will be copied to the destination companies. If you select the lookup in the journal names form, you will only see the number sequences that are available for that legal entity. However, if you choose to enter a number sequence manually that is not on that list, it will not be included in the copy process.|
| General ledger | Ledger allocation rules destination| If you are running a version earlier than version 7.3, if you have cross company allocation rules, you will not see the destination rules for legal entities that do not match the source legal entity. The copy into legal entity feature will only copy the destination records when the destination is equal to the source. The issue has been resolved in version 7.3.|
| General ledger | Ledger fiscal calendar year/period| The process is currently exporting all of the legal entities instead of just the source legal entity. The copy process works correctly. The issue has been resolved in version 7.3.|
| General ledger | Ledger parameters | If you check for continuous number sequences but you have number sequences that are used on journal names and are not continuous, the imports will fail. You should temporarily turn off that setting in the ledger parameters. In addition, the ledger parameters must be processed first. Change the sequence on your data project for ledger parameters to 15 (instead of 40). We will update the default templates in the monthly application release 3 to this value. |
| Inventory management | Inventory dimension parameters | There is an issue where an error on import is shown but the correct number of parameters are imported. The issue will be addressed in a future release.|
| Inventory management | Warehouse locations | Some warehouse locations require a location profile ID. Location profile IDs require a location format. Currently, the location format information must be manually added before the warehouse location. The entities for the location format and location profile were added in version 7.2.3, (App update 3 of the July 2017 release). |
| Master planning | Intercompany master plan associations | The copy into legal entity feature does not support intercompany master plan associations at this time. The issue will be addressed in a future release.|
| Retail | POS registers | This entity is global and cannot be copied to another legal entity.|
| Retail | Retail channel | This entity is global and cannot be copied to another legal entity.|
| Retail | Retail store address book | This entity has a dependency on Retail channel so it cannot be used.|
| Sales and marketing | Intercompany trading partnerships | The copy into legal entity feature does not support intercompany trading partnerships at this time. The issue will be addressed in a future release.|

### Rules

The Copy into legal entity feature supports rules, which let you modify data before it's added to the import staging table. For example, rules are used to change the target legal entity to the destination legal entity and modify number sequences. You can extend rules.

Rule extensions require three changes:

1. Add the name of the rule to the extensible **DMFRulesType** enumeration (enum).
2. For each project definition group, insert the enum that you just created (for example, **DMFRulesType::NewRule**) into the DMFRules table. Use your source legal entity, your rule type, and the definition group name. If you require that more data be stored, such as various options for your rule, you can create your own table and extend the DMFRules table.
3. Create your own class to handle the data that the rule acts on. For the DMFRules framework to instantiate the rule, you must decorate the class with the **\[DMFRulesBaseFactoryAttribute(DMFRulesType::NewRule)\]** attribute.

The class must also extend the **DMFRulesBase** class. This extension will require an implementation of the **DMFRulesBase.runRule(Common\_staging)** method. The \_staging record will be the buffer of the staging record that the rule is applied to.

## Additional information about entities

### Obsolete entities

As the application is updated, the functionality of an entity might have to be updated. A new entity might be created that has a different name. In this case, the original entity will be marked as obsolete. You will no longer be able to add obsolete entities to a new data project or template.

If you load a data package that contains an obsolete entity, you will receive a warning about the existence of obsolete entities. However, you will still be able to import your data. You can find the obsolete entity by selecting the **Obsolete** column and filtering on **Yes**.

### Self-referencing entities

Some entities represent tables that have references to themselves. For example, when you create a cash discount, you can refer to a related cash discount that creates a tiered discount calculation. To import data, you must sequence the data so that the cash discount that is referred to in the **Next cash discount** field is imported before the cash discount that uses that cash discount.

A new **DMFImportExportSequencer** class sequences the data in self-referencing entities and enables the data to be loaded in a single pass. In the Cash Discount entity (CashDiscountEntity), you can view the code that is required in order to update entities.

The class has been added to several self-referencing entities. It will be added to more entities as required. Here are some other examples of self-referencing entities:

- Customers
- Customer definitions
- Customer details
- Tax codes
- Budget control groups
- Projects
- Product categories
- Warehouses
- Budget plan workflow stage
- Sales units

### Adding entities in the appropriate country/region context

When you add entities, the mappings are created in the context of the country or region of the company that is currently active. If there are any issues with the mappings, a red *X* appears in the **View map** column. Select the red *X*, and repair the mappings as required.

> [!NOTE]
> By default, the DAT company doesn't have a country/region context. Some entities, such as the entities that are used for transaction codes and 1099 fields, won't be mapped correctly if they are added to a data project for the DAT company, because a country/region context is expected.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

