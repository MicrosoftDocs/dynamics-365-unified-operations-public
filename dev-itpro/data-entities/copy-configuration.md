---
# required metadata

title: Copy configuration data from one company to another
description: This topic describes how to use a configuration data project, and configuration data templates to move company configuration data between instances of Dynamics 365 for Operations.
author: mfalkner
manager: AnnBe
ms.date: 06/15/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
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
To copy configuration data, you must first export it from one company, and then import it to another.  

## Export a configuration
The Data management workspace is your hub for managing configuration data projects and for exporting data packages. To build a configuration, you need to define a data project and export the information represented by entities.

The process for creating a configuration data project is as follows:

1. Open the Data management workspace and, if you are in Standard view, click the **Enhanced view** button.
2. Click the **Export** tile.
3. Click **New** to create a configuration data project and add an ID and name that represent the configuration.
4. Set the operation type for the data project to **Export** and the project category to **Configuration**.
5. Add the entities that represent the information that you want to export. You can add entities using several methods:
> - Add entity – enter the first part of name of the entity until it appears in the lookup.
> - Add multiple – enter any part of the entity name, use the lookup for application module, enter any part of the tag name, or use the lookup for the entity category to show a list of entities. Tab away from the Lookup field to activate the filter. Select the entities in the grid that you want to add.
> - Add a file – browse to a file that contains a name that matches an entity and a file extension that matches the file extension that is in your data sources.
> - Add a template – select from a list of templates that you have loaded in your instance. 
6. Select a target data format. The system remembers that last data format that you selected or, if you select a file, it will default to the data format to the data source that matches the file extension. 
> **Note** Composite entities require an XML format.
7. Click the **Add** button. If you load a template and there is already an existing entity in the project that matches an entity in the template, the entity will be replaced by the enity in the template that you loaded. Some templates are very large and it may take a few seconds to load them.
8. Click **Remove entity** to remove one or more selected entities.

You are ready to export a configuration. However, you may want to use
some additional features to control the export process:

1. Organize your list by using the Sort by button to reorder your
    entities by unit, level and sequence
2. If want to change the execution sequence of any of the entities,
    you can edit the unit, level, or sequence manually or you can use the Resequence
    button to update any entities that you have selected. You must
    select more than one entity for the Resequence button to appear. You
    can change the unit, level and sequence individually or enable
    multiple changes and do them all at once. If you want the unit,
    level or sequence to remain unchanged when change multiple parts of
    the sequence, set the increment to zero.
3. Add filters to the entity with the **Filter** button. The icon will change when 
    you add a filter to an Edit button. The data will be
    filtered before it is exported. If you have added a template and the template 
    included filters, those filters will be added to your project. You can still modify
    or remove them if needed.
4. If necessary, change the entity mappings using the **View map** button. If you have added a template and the template 
    included mapping changes, those changes will be applied to your project. You can still modify
    them if needed.
5. Use the checkbox in the **Disable** column to temporarily stop the
    entity from being used when exporting a data project
6. Use the **Open in Excel** button to open the contents of the grid in an
    Excel spreadsheet. Modify the entities as needed and use Publish to
    upload the changes back into Dynamics 365 for Finance and
    Operations.

Now that you have completed your configuration, use the export button to
start the export. You can monitor your results on the execution details
page that is displayed. 

When the export is completed, perform the following tasks:

-   Use the Download button on the export page to download the
    configuration settings.

-   Use the Download package button on the data management workspace or
    on the execution details form to download the configuration settings
    and the data that was exported.

## Setup considerations for certain entities used to export configurations

There are several entities that currently require some additional steps when you
are doing configurations. Please follow these recommendations as you build 
your configurations. 

> ![IMPORTANT]
> We will continue to update this list as we improve the copy configuration feature.

### Using special purpose entities
The following entities require special handling when used in configurations: 

| Area                           | Entity                                 | Action to take                                            |  
|--------------------------------|----------------------------------------|-----------------------------------------------------------
| GL Shared                      | Account structures active group        | This is a composite entity that will export and import only the active account structures. If you use any other account structure entities, the active account structures will be changed to draft and you will need to activate them before they can be used. |
|                                | Advanced rule structures active group  | Used in combination with account structures active group entity, this composite entity will export and import only the active advanced rule structures active. If you use any other advanced rule structures entities, the advanced rule structures will be changed to draft and you will need to activate them before they can be used. |
|                                | Financial dimension values             | All dimension values, including values based on system defined entities like projects or customers, will be exported. Remove the system defined values before importing them. If you leave them in the package, they will not import. However, the system defined values will be populated as you import the data that backs the system defined dimension. |
| Workflow                       | Workflow version                       | Change the owner for every record in the package data to Admin unless the users in the workflow are already imported |  
|                                | Workflow expression                    | Some workflow expressions may be too long for an Excel cell. Use XML as the export format instead of Excel |  
| Tax                            | Sales tax parameters                   | The default value for the marginal base calculations method is "Total" for sales tax parameters. The Ledger Parameters entity does not set that value. However, some tax codes use a marginal base of "Line", which will fail validation. A new entity called Sales tax parameters preset entity was created to allow you to import the marginal base calculation method first so you can then import tax codes | 
| Accounts receivable            | Customers                              | The Customers entity was designed for use with Odata scenarios. For configurations, use the Customer definitions entity and the Customer details entity. The Customer definitions entities allows you to import the basic information about a customer, enabling entities that require a customer to have that information earlier in the import process. The Customer details entity contains additional information about a customer that you can add after parameters and reference data has been set up. |
| Inventory management           | Warehouse locations                    | Some warehouses locations require a Location profile ID. Location profile ids require a Location format. The location format information must be added manually before the warehouse location at this time  | 
| Product information management | Products                               | The Products and Released Products entities should be used for configurations. The Product master and Released product master entities should be used for Odata scenarios |
|                                | Product document attachments           | For Product document attachments and Released product document attachments, you must never skip staging because additional steps are performed in the staging environment. You must use a data package for export and for import  because the export file needs to be accompanied by a resources folder with the attechments. The entities support images, documents, notes, and links. When you export, you will see an image file with a name that looks like a GUID. It is a valid data package needed to complete the import |
|                                | Product attribute values               | Product attribute values are assigned only when a user opens up the Attribute values page from the Products details page. At this time, you cannot import the values at this time unless this step was performed in the golden build. |
| Procurement                    | Vendor catalog                         | Please refer to the discussion for importing vendor catalogs in the Supply Chain Management blog https://blogs.msdn.microsoft.com/dynamicsaxscm/2016/05/25/vendor-catalogs-in-dynamics-ax/  |


### Remove the mapping for specific fields
A golden build may not have customer-specific fields set up. These fields should be unmapped to ensure that the import works. For example, workers are stored in many tables but they may not be set up in a golden build. 

The following entities may need to be unmapped:

| Area                           | Entity                                 | Action to take                                            |  
|--------------------------------|----------------------------------------|-----------------------------------------------------------
| System setup                   | Operating unit                         | Unmap ManagerPersonnelNumber unless you have imported workers |
|                                | User information                       | Apply a filter where the ID is not equal to Admin. Unmap PersonName and use the User to person relationship entity to map system users to directory users. |
| Accounts payable               | Vendors                                | Unmap purchase site (DefaultPurchaseSite) and warehouse (DefaultProcurementWarehouseID) unless they are set up. Unmap the 1099 box id (Tax1099BoxID) and 1099 type (Tax1099Type) unless you have opened the 1099 form. Unmap the vendor bank account ID. The vendor bank account entity will set up the link to the bank account when it is imported |
| Accounts receivable            | Customer details                       | Unmap EmployeeResponsibleNumber unless workers have been imported. Unmap CollectionsContactPersonID unless workers and their contact information has been imported |
| Inventory management           | Warehouse current postal address       | Unmap the Picking store area and Input store area unless Retail information has been imported | 
| Product information management | Products                               | Unmap NMFCCode and STCCCode. There are no entities available for those codes at this time |
|                                | Released products                      | Unmap project category, default product color, default configuration, default product size, and default product style. This entity is self-referencing and has not yet been updated to load these fields in a single pass |
|                                | Period template                        | The Period template entity is a shared entity. It can be filtered by Legal entity but the Period template lines entity does not have a Legal entity field. If you want to import a single legal entity, you can filter the period template. However, at this time, you must remove the period template lines that are not related to that legal entity |
|                                | Item coverage group                    | Unmap Period template ID unless they were already imported |
| Procurement                    | Vendors                                | Unmap purchase site and warehouse unless they are set up. Unmap the 1099 box id and 1099 type unless you have opened the 1099 form. Unmap the vendor bank acccount ID. The vendor bank account entity will set up the link to the bank account in the vendor record when it is imported |
| Sales and marketing            | Leads                                  | Unmap LeadOpeningPersonnelNumber, LeadClosingPersonnelNumber, LeadResponsiblePersonnelNumber unless workers have been imported |


### Golden builds with multiple legal entities
The templates can be used to export data from any company in your golden build. When you export both shared data and
company data, the templates will export the shared data for all legal entities and then export the data for the legal
entity that you are currently using. You can then switch companies and export the company data for additional legal entities 
by using projects that do not included the shared entities. 

If you are exporting from a golden build that has multiple legal entities in it 
but you only want to import the data from one of those legal entities, you will need 
to apply a filter on the legal entity fields to export the only the data that you need for that legal entity. 
This filter must remove all data for other legal entities except the one that you want.
In some cases, you will need to take some additional steps to clean up the exported data.

Most of the changes listed below occur in the system setup and general ledger areas. If you export a golden build that uses a single legal entity, you should not need these filters. 

The following entities need filters or special handling when you export the data:

| Area                           | Entity                                 | Action to take                                            |  
|--------------------------------|----------------------------------------|-----------------------------------------------------------
| System setup                   | Legal entities                         | Apply a filter to Company  |
|                                | Number sequence code                   | The number sequence codes can be shared or be specific to a legal entity. If you want to import all number sequences, you must have the legal entities setup for the number sequences that are stored for a specific legal entity. If you only want the shared sequences, apply a filter to remove the number sequences that are specific to a legal entity. If you only want number sequences for a legal entity, apply a filter to Company |
|                                |                                        | Number sequences can also have scope. You must delete number sequences where 1) the SCOPETYPE is DataArea and SCOPEVALUE is not equal to the legal entity or is blank, 2) the SCOPETYPE is LegalEntity and SCOPEVALUE is not equal to the legal entity and 3) the SCOPETYPE is DataAreaFiscalCalendar and SCOPEVALUE is not equal to the legal entity |
|                                | Number sequence references             | Number sequences references can also have scope. You must delete the number sequence references where 1) the SCOPETYPE = DataArea, DataAreaFiscalCalendar, or Legal Entity and 2) the SCOPEVALUE   is blank or is not the legal entity that you want in the data  |
|                                | Organization hierarchies               | There is no legal entity filter. Manually remove any references to the other legal entities that are not being imported. For example, if you have set up Centralized payments but you are only loading one legal entity, then you must not import the Centralized payments hierarchy  |
| Global address book            | Multiple entities                      | The global address book contains data for all legal entities. All legal entities will be created when you import the data unless you remove the data for the legal entities that you do not want to load.  Delete all records for other legal entities to ensure that those legal entities are not created or apply a filter to the Legal entity data area (<> blank). You will also need to remove global address book records that are used in the other legal entities |
|                                | Party postal addresses                 | Address records for legal entities other than the one being imported must be manually be deleted before import |
|                                | Party contacts                         | Contact records for legal entities other than the one being imported must be manually be deleted before import |
|                                | Workflow                               | Apply a filter on DataAreaID. Many of the workflow entities cannot be filtered for legal entity so you may see import failures if you do not remove the data in all workflow entities related to other legal entities that you do not want. We recommend setting up workflows manually for this scenario.|
| General ledger                 | Ledger                                 | Apply a filter to Company  |  
|                                | Ledger fiscal calendar year            | Apply a filter to Ledger name  |
|                                | Ledger fiscal calendar period          | Apply a filter to Ledger name  |
|                                | Main account legal entity overrides    | Apply a filter to Company |
|                                | Financial dimension value legal entity | Apply a filter to Legal entity |
|                                | Financial dimension values             | Apply a filter to Legal entity. However, you cannot filter out system defined dimension values so you will need to delete them. They will be restored when you import data for the tables that are backing the system defined dimensions |
|                                | Journal names                          | Apply a filter to Voucher series company ID |
|                                | Ledger allocation basis source         | Apply a filter to Legal entity |
|                                | Ledger allocation rule destination     | Apply a filter to Company |
| Accounts receivable            | Customer write-off reason code         | Apply a filter to Company  |
| Budget                         | Budget control configuration           | Apply a filter to Legal entity              |
|                                | Budget control configuration activation| Apply a filter to Legal entity              |
|                                | Budget control cycle model             | Apply a filter to Legal entity              |
|                                | Budget control dimension attribute     | Apply a filter to Legal entity              |
|                                | Budget control documents and journals  | Apply a filter to Legal entity              |
|                                | Budget control group                   | Apply a filter to Legal entity              |
|                                | Budget control group criteria          | Apply a filter to Legal entity              |
|                                | Budget control message level           | Apply a filter to Legal entity              |
|                                | Budget control over budget permissions | Apply a filter to Legal entity              |
|                                | Budget control rule                    | Apply a filter to Legal entity              |
|                                | Budget control rule criteria           | Apply a filter to Legal entity              |
|                                | Budget cost elements                   | Apply a filter to Cost element data area id |
|                                | Budget dimensions                      | Apply a filter to Legal entity              |
|                                | Budget plan allocation schedule        | Apply a filter to Ledger                    |
|                                | Budget plan process                    | Apply a filter to Ledger                    |
|                                | Budget plan stage rule                 | If you applied a filter to Budget plan process, you may see errors when importing stage rules. The entity currently does not have a Ledger name in it that can be filtered so it will contain all companies | 
|                                | Budget plan priority constraint        | You will see the same issue described for stage rules | 
|                                | Budget plan process administration     | You will see the same issue described for stage rules | 
|                                | Budget transfer rules                  | Apply a filter to Legal entity              |
| Inventory management           | Warehouse current postal address       | Apply a filter to Company |
|                                | Site current postal address            | Apply a filter to Company | 
|                                | Tracking number groups                 | The entity automatically filters the Number sequence scope data area by the legal entity so you do not need a filter. However, if you need to change the legal entity, the legal entity is stored in the table.  | 
                         
### Changing the legal entity value before importing
If you want to change the legal entity ID to another value, you must change the values in all fields like those listed above to the new legal entity value. For example, for Legal entities, change Company from the exported value to a new value in the exported file. 

There are many places where the legal entity ID is stored so making this change can be difficult and cause errors. We are considering a feature to help do this work in a future release.

## Import a configuration

The data management workspace is also your hub for importing
configuration data projects. You can build a configuration project from
an existing data project that you exported or from individual files that
contain data formatted correctly for import into Dynamics 365 for
Finance and Operations.

The process for importing a configuration is as follows:

1. Open the Data management workspace and, if you are in Standard view, click the **Enhanced view** button.
2. Click the **Import** tile.
3. Click **New** to create a configuration data project and add an ID and name that represent the configuration.
4. Set the operation type for the data project to **Import** and the project category to **Configuration**.
5. Click Add file to select the file that has your entity
    information and data. For data packages, the file will have a ZIP file extension.
    The extension of the file name will be matched
    to the default file extensions in your data sources and the source
    data format will be populated automatically. If you have not set up
    the default file extensions, you must first select a source data format 
    before you select the file.
5.  When you load a package, the import page reads the list of entities from the package first. 
    A progress bar displays how much of the package has been read. Once the list of entities is read, 
    the import page starts loading the data in the package. This process can take some time to execute.
6.  Click **Remove entity** to remove any selected entities, if necessary.
7. Now that you have completed your configuration, click **Import** button to start the import. You can monitor your results on the execution details page that is displayed.

You are ready to import a configuration. However, you may want to use
some additional features to control the export process:

1. Organize your list by using the Sort by button to reorder your entities by unit, level or sequence.
2. If you want to change the execution sequence of any of the entities,
    edit the unit, level, or sequence manually or use the resequence
    button to update any entities that you have selected.
3. If necessary, change the entity mappings using the **View map** button.
4. Use the checkbox in the **Disable** column to temporarily stop the
    entity from being used when exporting a data project

## Additional information about entities


### Obsolete entities

As we update Dynamics 365 for Finance and Operations, we may need to update the functionality of an entity. A new entity may be created with a different name and the original entity will be marked as obsolete. You will no longer be able to add the obsolete entities to a new data project or template. 

If you load a data package that has the obsolete entity in it, you will be warned about the existence of an obsolete entity but you will be able to still import your data. You can find the obsolete entities by selecting the Obsolete column and filtering on Yes.

### Self referencing entities

There are entities that represent tables that have references to themselves. For example, when you create a cash discount, you can refer to related cash discount that creates a tiered discount calculation. To import data, it is necessary to sequence the data so that the cash discount referred to in the Next cash discount field is imported first, followed by the cash discount that uses it. 

We have added a class called DMFImportExportSequencer that will sequence the data in self referencing entities and enable the data to load in a single pass. You can view the code required to update entities in the Cash Discount entity (CashDiscountEntity).

We have added the class to a number of self referencing entities and we will add it to more entities as needed. Further examples of this type of entity includes:
-   Customers
-   Customer definitions
-   Customer details
-   Tax codes
-   Budget control groups
-   Projects
-   Product categories
-   Warehouses
-   Budget plan workflow stage
-   Sales units
