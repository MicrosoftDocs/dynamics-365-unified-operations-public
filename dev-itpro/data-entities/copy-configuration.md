---
# required metadata

title: Copy configuration data from one company to another
description: This topic describes how to use a configuration data project and configuration data templates to move company configuration data between instances of Dynamics 365 for Finance and Operations.
author: mfalkner
manager: AnnBe
ms.date: 05/23/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 77523
ms.search.region: Global
# ms.search.industry: 
ms.author: mfalkner
ms.search.validFrom: 2017-07-31
ms.dyn365.ops.version: Platform update 7

---
# Copy configuration data from one company to another

To copy configuration data, you must first export it from one company. You can then import it to another company.  

## Export a configuration

The **Data management** workspace is your hub for managing configuration data projects and exporting data packages. To build a configuration, you must define a data project and export the information that is represented by entities.

To create a configuration data project, follow these steps.

1. Open the **Data management** workspace. If you're in Standard view, click **Enhanced view**.
2. Click the **Export** tile.
3. Click **New** to create a configuration data project, and enter an ID and name for the configuration.
4. Set the operation type for the data project to **Export**, and set the project category to **Configuration**.
5. Add the entities that represent the information that you want to export. You can add entities by using several methods:

    - **Add one entity** – Enter the first part of the name of the entity until it appears in the lookup.
    - **Add multiple entities** – Enter any part of the entity name, use the lookup for the module, enter any part of the tag name, or use the lookup for the entity category to show a list of entities. Press Tab to move focus away from the **Lookup** field and activate the filter. In the grid, select the entities to add.
    - **Add a file** – Browse to a file that contains a name that matches the name of an entity and a file name extension that matches the file name extension that is in your data sources.
    - **Add a template** – Select from a list of templates that you've loaded in your instance. 

6. Select a target data format. The system stores that last data format that you selected. Alternatively, if you select a file, the system automatically sets the data format to the data source that matches the file name extension.

    **Note:** Composite entities require an XML format.

7. Click **Add**. If you load a template, and there is already an existing entity in the project that matches an entity in the template, the entity in the project will be replaced by the entity in the template. Some templates are very large, and they might take a few seconds to be loaded.
8. Click **Remove entity** to remove one or more selected entities.

You're now ready to export a configuration. However, you might want to use some additional features to help control the export process:

- To organize the list, use the **Sort by** button to reorder your entities by unit, level, and sequence.
- To change the execution sequence of any of the entities, you can manually edit the unit, level, or sequence. Alternatively, you can use the **Resequence** button to update any entities that you've selected. The **Resequence** button appears only if you select more than one entity. You can change the unit, level, and sequence individually. Alternatively, you can enable multiple changes and do them all at the same time. If you want the unit, level, or sequence to remain unchanged when you change multiple parts of the sequence, set the increment to **0** (zero).
- To add filters to the entity, use the **Filter** button. If you add a filter, the **Filter** button changes to an **Edit** button. The data will be filtered before it's exported. If you've added a template, and the template includes filters, those filters will be added to your project. However, you can modify or remove them as you require.
- If you must change the entity mappings, use the **View map** button. If you've added a template, and the template includes mapping changes, those changes will be applied to your project. However, you can modify them as you require.
- To temporarily prevent the entity from being used when you export a data project, use the check box in the **Disable** column.
- To open the contents of the grid in a Microsoft Excel workbook, use the **Open in Excel** button. Modify the entities as you require, and then use **Publish** to upload the changes back into Microsoft Dynamics 365 for Finance and Operations.

When you've completed your configuration, click **Export** to start the export. You can monitor the results on the **Execution details** page that appears. 

When the export is completed, complete the following tasks:

- Use the **Download** button on the **Export** page to download the configuration settings.
- Use the **Download package** button in the **Data management** workspace or on the **Execution details** page to download the configuration settings and the data that was exported.

## Setup considerations for some entities that are used to export configurations

Currently, several entities require additional steps when you build configurations. Follow these recommendations as you build your configurations.

> ![IMPORTANT]
> We will continue to update this list as we improve the Copy configuration feature.

### Using special-purpose entities

The following entities require special handling when they are used in configurations.

| Area | Entity | Action |  
|------|--------|--------|
| GL Shared | Account structures active group | This composite entity will export and import only the active account structures. If you use any other account structure entities, the status of the active account structures will be changed to **Draft**, and you must activate them before they can be used. |
| | Advanced rule structures active group | This composite entity is used in combination with the account structures active group entity. It will export and import only the active advanced rule structures. If you use any other advanced rule structure entities, the status of the advanced rule structures will be changed to **Draft**, and you must activate them before they can be used. |
| | Financial dimension values | All dimension values will be exported, even values that are based on system-defined entities such as projects or customers. Remove the system-defined values before you import them. If you leave the system-defined values in the package, they won't be imported. However, they will be filled as you import the data that backs the system-defined dimension. |
| Workflow | Workflow version | Change the owner for every record in the package data to **Admin**, unless the users in the workflow are already imported. |  
| | Workflow expression | Some workflow expressions might be too long for an Excel cell. Use XML instead of Excel as the export format. |  
| Tax | Sales tax parameters | The default value for the marginal base calculations method is **Total** for sales tax parameters. The Ledger Parameters entity doesn't set that value. However, the marginal base that some tax codes use, **Line**, will fail validation. A new entity that is named the Sales tax parameters preset entity was created so that you can import the marginal base calculation method first. You can then import tax codes. | 
| Accounts receivable | Customers | The Customers entity was designed to be used for OData scenarios. For configurations, use the Customer definitions entity and the Customer details entity. The Customer definitions entities let you import the basic information about a customer. In this way, you enable entities that require that a customer have that information earlier in the import process. The Customer details entity contains additional information about a customer that you can add after parameters and reference data have been set up. |
| Inventory management | Warehouse locations | Some warehouse locations require a location profile ID. Location profile IDs require a location format. Currently, the location format information must be manually added before the warehouse location. | 
| Product information management | Products | The Products and Released Products entities should be used for configurations. The Product master and Released product master entities should be used for OData scenarios. |
| | Product document attachments | For Product document attachments and Released product document attachments, you must never skip staging, because additional steps are performed in the staging environment. You must use a data package for export and import, because the export file must be accompanied by a resources folder that contains the attachments. The entities support images, documents, notes, and links. When you export, you will see an image file that has a name that looks like a globally unique identifier (GUID). This file is a valid data package that is required in order to complete the import. |
| | Product attribute values | Product attribute values are assigned only when a user opens the **Attribute values** page from the **Products details** page. Currently, you can't import the values unless this step was performed in the golden build. |
| Procurement | Vendor catalog | See the "Vendor catalogs import" section of [Vendor catalogs in Dynamics AX](https://blogs.msdn.microsoft.com/dynamicsaxscm/2016/05/25/vendor-catalogs-in-dynamics-ax/) on the Supply Chain Management blog. |

### Remove the mapping and apply filters for specific entity fields

In a golden build, customer-specific fields might not be set up. To help guarantee that the import works, you should unmap these fields. For example, workers are stored in many tables, but they might not be set up in a golden build. Filters might also be required for some fields in an entity.

The following entities might have to be unmapped or filtered.

| Area | Entity | Action |  
|------|--------|--------|
| System setup | Operating unit | Unmap Manager personnel number unless workers have been imported. |
| | User information | Apply a filter where **ID** isn't equal to **Admin**. Unmap Person name, and use the User to person relationship entity to map system users to directory users. |
| | Global address book | Apply a filter where **Name** isn't equal to blank. |
| Accounts payable | Vendors | Unmap Purchase site (DefaultPurchaseSite) and Warehouse (DefaultProcurementWarehouseID) unless they are set up. Unmap the 1099 box ID (Tax1099BoxID) and 1099 type (Tax1099Type) unless you've opened the 1099 form. Unmap the vendor bank account ID. The Vendor bank account entity will set up the link to the bank account when it's imported. |
| Accounts receivable | Customer details | Unmap Employee responsible number unless workers have been imported. Unmap Collections contact person (CollectionsContactPersonID) unless workers and their contact information have been imported. Unmap the site (SiteID) and warehouse (WarehouseID) unless they have already been imported. |
| Inventory management | Warehouse current postal address | Unmap Picking store area and Input store area unless Retail information has been imported. | 
| Product information management | Products | Unmap NMFCCode and STCCCode. Currently, no entities are available for those codes. |
| | Released products | Unmap the project category, default product color, default configuration, default product size, and default product style. This entity is self-referencing and hasn't yet been updated to load these fields in a single pass. |
| | Period template | The Period template entity is a shared entity. Although it can be filtered by legal entity, the Period template lines entity doesn't have a **Legal entity** field. To import a single legal entity, you can filter the period template. However, you must currently remove the period template lines that aren't related to that legal entity. |
| | Item coverage group | Unmap Period template ID unless it has already been added manually. |
| Procurement | Vendors | Unmap Purchase site (DefaultPurchaseSite) and Warehouse (DefaultProcurementWarehouseID) unless they are set up. Unmap the 1099 box ID (Tax1099BoxID) and 1099 type (Tax1099Type) unless you've opened the 1099 form. Unmap the vendor bank account ID. The Vendor bank account entity will set up the link to the bank account when it's imported. |
| Sales and marketing | Leads | Unmap LeadOpeningPersonnelNumber, LeadClosingPersonnelNumber, and LeadResponsiblePersonnelNumber unless workers have been imported. |
| Project management | Projects | Unmap WorkerArchitectPersonelNumber, WorkerRespFinancialPersonelNumber, WorkerResponsiblePersonnelNumber, and WorkerRespSalesPersonelNumber unless workers have been imported. |

### Golden builds that have multiple legal entities

The templates can be used to export data from any company in your golden build. When you export both shared data and company data, the templates first export the shared data for all legal entities. They then export the data for the legal entity that you're currently using. You can then switch companies and export the company data for additional legal entities by using projects that don't included the shared entities. 

If you're exporting from a golden build that contains multiple legal entities, but you want to import the data from only one of those legal entities, you must apply a filter on the legal entity fields, so that only the data that you require for that legal entity is exported. This filter must remove all data for all legal entities except the legal entity that you want. In some cases, you must complete some additional steps to clean up the exported data.

Most of the changes that are listed in the following table occur in the System setup and General ledger areas. If you export a golden build that uses a single legal entity, you should not require these filters. 

The following entities require filters or special handling when you export the data.

| Area | Entity | Action |  
|------|--------|--------|
| System setup | Legal entities | Apply a filter to Company. |
| | Number sequence code | <p>The number sequence codes can be shared, or they can be specific to a legal entity. To import all number sequences, you must have the legal entities setup for the number sequences that are stored for a specific legal entity. If you want only shared number sequences, apply a filter to remove the number sequences that are specific to a legal entity. If you want only the number sequences for a legal entity, apply a filter to Company.</p><p>Number sequences can also have scope. You must delete number sequences when the following conditions are met:<ol><li>The **SCOPETYPE** value is **DataArea**, and the **SCOPEVALUE** value isn't equal to the legal entity, or it's blank.</li><li>The **SCOPETYPE** value is **LegalEntity**, and the **SCOPEVALUE** value isn't equal to the legal entity.</li><li>The **SCOPETYPE** value is **DataAreaFiscalCalendar**, and the **SCOPEVALUE** value isn't equal to the legal entity.</li></ol> |
| | Number sequence references | Number sequences references can also have scope. You must delete the number sequence references when the following conditions are met:<ol><li>The **SCOPETYPE** value is equal to **DataArea**, **DataAreaFiscalCalendar**, or **LegalEntity**.</li><li>The **SCOPEVALUE** value isn't equal to the legal entity that you want in the data, or it's blank.</li></ol> |
| | Organization hierarchies | There is no legal entity filter. Manually remove any references to the other legal entities that you aren't importing. For example, if you've set up Centralized payments, but you're loading only one legal entity, you must not import the Centralized payments hierarchy. |
| Global address book | Multiple entities | The global address book contains data for all legal entities. All legal entities will be created when you import the data, unless you remove the data for the legal entities that you don't want to load. Delete all records for other legal entities to help guarantee that those legal entities aren't created. Alternatively, apply a filter to the Legal entity data area (<> blank). You must also remove global address book records that are used in the other legal entities. |
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
|| Budget dimensions | Apply a filter to Legal entity. |
| | Budget plan allocation schedule | Apply a filter to Ledger. |
| | Budget plan process | Apply a filter to Ledger. |
| | Budget plan stage rule | If you applied a filter to Budget plan process, errors might occur when you import stage rules. Because the entity doesn't currently contain a Ledger name that can be filtered, it will contain all companies. | 
| | Budget plan priority constraint | You will experience the same issue that is described for Budget plan stage rule. | 
| | Budget plan process administration | You will experience the same issue that is described for Budget plan stage rules. | 
| | Budget transfer rules | Apply a filter to Legal entity. |
| Inventory management | Warehouse current postal address | Apply a filter to Company. |
| | Site current postal address | Apply a filter to Company. | 
| | Tracking number groups | The entity automatically filters the Number sequence scope data area by the legal entity. Therefore, you don't require a filter. However, if you must change the legal entity, the legal entity is stored in the table. | 
                         
### Changing the legal entity value before import

If you want to change the legal entity ID to another value, you must change the values in all fields that resemble the fields that were listed earlier to the new legal entity value. For example, for Legal entities, change Company from the exported value to a new value in the exported file. 

The legal entity ID is stored in many places. Therefore, it can be difficult to make this change, and you might cause errors if you try. We are considering adding a feature in a feature release to help you complete this task.

## Import a configuration

The **Data management** workspace is also your hub for importing configuration data projects. You can build a configuration project from an existing data project that you exported. Alternatively, you can build a configuration project from individual files that contain data that is formatted correctly for import into Dynamics 365 for Finance and Operations.

To import a configuration, follow these steps.

1. Open the **Data management** workspace. If you're in Standard view, click **Enhanced view**.
2. Click the **Import** tile.
3. Click **New** to create a configuration data project, and enter an ID and name for the configuration.
4. Set the operation type for the data project to **Import**, and set the project category to **Configuration**.
5. Click **Add file** to select the file that has your entity information and data. For data packages, the file will have a .zip file name extension.

    The file name extension of the file will be matched to the default file name extensions in your data sources, and the source data format will be set automatically. If you haven't set up the default file name extensions, you must select a source data format before you select the file.

    When you load a package, the **Import** page first reads the list of entities from the package.

    A progress indicator shows how much of the package has been read. After the list of entities is read, the **Import** page starts to load the data in the package. This process can take some time.

7. Click **Remove entity** to remove any selected entities, as required.
8. After you've completed your configuration, click **Import** to start the import. You can monitor your results on the **Execution details** page that appears.

You're now ready to import a configuration. However, you might want to use some additional features to help control the export process:

- To organize your list, use the **Sort by** button to reorder your entities by unit, level, or sequence.
- To change the execution sequence of any of the entities, manually edit the unit, level, or sequence. Alternatively, use the **Resequence** button to update any entities that you've selected.
- If you must change the entity mappings, use the **View map** button.
- To temporarily prevent the entity from being used when you export a data project, use the check box in the **Disable** column.

## Additional information about entities

### Obsolete entities

As we update Dynamics 365 for Finance and Operations, we might have to update the functionality of an entity. We might create a new entity that has a different name. In this case, the original entity will be marked as obsolete. You will no longer be able to add obsolete entities to a new data project or template. 

If you load a data package that contains an obsolete entity, you will be warned about the existence of obsolete entities. However, you will still be able to import your data. You can find the obsolete entity by selecting the **Obsolete** column and filtering on **Yes**.

### Self-referencing entities

Some entities represent tables that have references to themselves. For example, when you create a cash discount, you can refer to a related cash discount that creates a tiered discount calculation. To import data, you must sequence the data so that the cash discount that is referred to in the **Next cash discount** field is imported before the cash discount that uses it. 

We have added a **DMFImportExportSequencer** class that will sequence the data in self-referencing entities and enable the data to be loaded in a single pass. In the Cash Discount entity (CashDiscountEntity), you can view the code that is required in order to update entities.

We have added the class to several self-referencing entities, and we will add it to more entities as required. Here are some other examples of self-referencing entities:

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
