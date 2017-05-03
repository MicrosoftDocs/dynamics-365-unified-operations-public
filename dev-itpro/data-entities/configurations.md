---
# required metadata

title: Copy configuration data to another company
description: Configurations are used to manage the movement of company configuration
38
data between instances of Dynamics 365 for Finance and Operations
author: mfalkner
manager: AnnBe
ms.date: 06/01/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 77523
ms.assetid: 62232067-9999-4045-ad24-7a6c44e7e641
ms.search.region: Global
# ms.search.industry: 
ms.author: mfalkner
ms.search.validFrom: 2017-04-30
ms.dyn365.ops.version: Platfrom update 7

---
# Copy configuration data to another company

Overview
--------

Configurations are used to manage the movement of company configuration
data between instances of Dynamics 365 for Finance and Operations. The
feature supports the following scenarios:

-   Export configurations, where you can create configurations of
    entities and use the data management framework to export it

-   Import configurations with rules, where you can upload a
    configuration package, add rules, and use the data management
    framework to import it

Configurations are created using the data import and export projects
that you can access from the data management workspace. The import and export pages allow
you to add and remove the entities that you need to manage the movement
of company and shared data. Once you create the list of entities in your
configuration, you can export or import the configuration using the data
management framework for processing. You can export packages locally or
move them to your LCS library for import into another instance.

Configuration templates are a predefined list of entities for each
module area that can be used in a data project. You can create, view and
modify these templates using the template page in the data management
workspace.

Preparing data management for configurations
--------------------------------------------

### Standard and enhanced views

The data management workspace, the template page, and the import/export
pages have been enhanced to better support configurations. These pages
are still delivered in the standard view to provide consistency with our
prior releases. However, you should switch them by using the Enhanced
view menu button on each page for configurations.

The view settings are saved for each user per each legal entity.
However, if you would like to change the system default to the enhanced
view, you can select the Framework parameters tile on the data
management workspace and change the view default from standard to
enhanced for all users and legal entities.

### Default data sources file extensions

The template page and import/export page now allow you to add entities
by selecting a file in addition to searching by the entity name. To use
this feature, we have populated some default file extensions with the
data sources that are available to you. If you have additional file
extensions that you want to use, you must update your data sources with
a default file extension that will be used as the target data format.

Use the Configure data sources tile on the data management workspace to
open the data sources page. Add a default file extension to the
appropriate data source. For example, we have added the following
defaults:

-   XLSX for the Excel data source

-   ZIP for the package data source

-   XML for the XML data source

-   CSV for the comma separated values data source

-   TXT for the delimited data source

### Templates for configurations

Predefined templates are automatically loaded in Dynamics 365 when an instance is created. New templates and updates
will be delivered in new releases or through periodic updates. You can update your existing instance by using the refresh button in the framework parameters found on the data management workspace.

The templates are sequenced so that the data managed by the entities
will be processed in the correct sequence. The
predefined templates are designed to maintain the correct sequence when
they are merged. You can also add multiple templates to a single data project. See the section on sequencing philosophy for more
information.

Export a configuration
----------------------

The data management workspace is your hub for managing configuration
data projects and exporting data packages. To build a configuration, you
need to define a data project and export the information represented by
entities.

The process for creating configurations is as follows:

1)  Open the data management workspace and switch to the Enhanced view.

2)  Select the Export tile in the data management workspace.

3)  Select New to create the configuration project and add an ID and
    name that represents the configuration

4)  Select the data project operation type (Export) and project category
    (Configuration).

5)  Now add the entities that represent the information that you want to
    export. You can add entities using several methods:

    a.  Add entity – enter the first part of name of the entity until it
        appears in the lookup.

    b.  Add multiple – enter any part of the entity name, use the lookup
        for application module, enter any part of the tag name, and/or
        use the lookup for the entity category to show a list of
        entities. Select the entities in the grid that you want to add

    c.  Add file – browse to a file that has a name that matches an
        entity and a file extension that matches the file extensions that were added in the data sources.

    d.  Add template – select from a list of templates that you have
        added to your instance or were automatically created when your installation was created

6)  Select a target data format. The system remembers that last data
    format that you selected or, if you select a file, it will default
    the data format to the data sources that matches the file extension. 
    Note that some entities like composite entities require a specific format like XML.

7)  Select the appropriate Add button and the entities will be added to
    your data project. If you load a template and there is already an
    existing entity in the project that matches an entity in the
    template, the entity will be replaced by the latest template that
    you loaded

8)  Use Remove entity to remove one or more selected entities

You are ready to export a configuration. However, you may want to use
some additional features to control the export process:

1)  Organize your list by using the Sort by button to reorder your
    entities by unit, level and sequence

2)  If want to change the execution sequence of any of the entities,
    you can edit the unit, level, or sequence manually or you can use the Resequence
    button to update any entities that you have selected. You must
    select more than one entity for the Resequence button to appear. You
    can change the unit, level and sequence individually or enable
    multiple changes and do them all at once. If you want the unit,
    level or sequence to remain unchanged when change multiple parts of
    the sequence, set the increment to zero

3)  Add filters to the entity with the Filter icon. The data will be
    filtered before it is exported.

4)  If necessary, change the entity mappings using the View map icon.

5)  Use the check box in the Disable column to temporarily stop the
    entity from being used when exporting a data project

6)  Use the Open in Excel button to open the contents of the grid in an
    Excel spreadsheet. Modify the entities as needed and use Publish to
    upload the changes back into Dynamics 365 for Finance and
    Operations.

Now that you have completed your configuration, use the export button to
start the export. You can monitor your results on the execution details
page that is displayed. When the export is completed, do the following
tasks:

-   Use the Download button on the export page to download the
    configuration settings.

-   Use the Download package button on the data management workspace or
    on the execution details form to download the configuration settings
    and the data that was exported.

Setup considerations for certain entities used to export configurations
------------------------------------------------------------------------------

There are several entities that require some additional steps when you
are doing configurations. In many cases, these steps occur if you are exporting from a 
golden build that has multiple legal entities in it but you only want to import the data 
from one of those legal entities. Entities with shared data will require a filter to remove
all other entities except the one that you want.

Please follow these recommendations as you build your configurations. We will continue to eliminate special 
steps as we improve the configuration feature.

| Area                           | Entity                                 | Action to take                                                                                                                                                                                        
|--------------------------------|----------------------------------------|-----------------------------------------------------------
| System setup                   | Legal entities                         | Apply a filter to Company if you only want one legal entity |
|                                | Number sequence code                   | The number sequence codes can be shared or specific to a legal entity. If you want all number sequences, you must have the legal entities setup for the number sequences that are stored for a specific legal entity. If you only want the shared sequences, apply a filter to remove the number sequences that are specific to a legal entity |
|                                | Number sequence references             | The number sequence references follow the same pattern as number sequence codes |
|                                | Operating unit                         | Unmap ManagerPersonnelNumber unless you have imported workers |
|                                | Organization hierarchy - published     | There is one entity for exporting hierarchies (Organization hierarchy - published) and a different one for importing them (Organization hierarchy). Remove the export entity and add the import entity when you import |
|                                | User information                       | Apply a filter where ID is not equal to Admin. Unmap PersonName because there is no mapping to the directory. |
| Global address book            | Multiple entities                      | If your source environment contains multiple legal entities, the global address book will contain data for each legal entity. All of those legal entities will be created when you import the data unless you remove the data for the legal entities that you do not want to load |
| GL Shared                      | Account structures active group        | This is a composite entity that will export and import only the active account structures. If you use the other account structure entities, the active account structures will be changed to draft and you will need to activate them before they can be used. |
|                                | Advanced rule structures active group  | Used in combination with account structures active group entity, this composite entity will export and import only the active advanced rule structures active. If you use the other advanced rule structures entities, the advanced rule structures will be changed to draft and you will need to activate them before they can be used. |
|                                | Financial dimension values             | All values, including custom values, will be exported. Remove the custom values before importing them. If you leave them in the package, they will not import but the custom values will be populated as you import the data that backs the custom dimension. |
| Workflow                       | Workflow version                       | Change the owner for every record in the package data to Admin unless the users in the workflow are already imported |  
|                                | Workflow expression                    | Some workflow expressions may be too long for an Excel cell. Use XML as the export format instead of Excel |  
| General ledger                 | Ledger                                 | Apply a filter to Company if you only want one legal entity |  
|                                | Ledger fiscal Calendar year            | Apply a filter to Ledger name if you only want one legal entity |
|                                | Ledger fiscal calendar period          | Apply a filter to Ledger name if you only want one legal entity |
|                                | Main account legal entity overrides    | Apply a filter to Company if you only want one legal entity |
|                                | Financial dimension value legal entity | Apply a filter to Legal entity if you only want one legal entity |
| Accounts payable               | Vendors                                | Unmap purchase site and warehouse unless they are set up. Unmap the 1099 box id and 1099 type unless you have opened the 1099 form. Unmap the vendor bank acccount ID. The vendor bank account entity will set up the link to the bank account when the vendor when it is imported |
| Tax                            | Sales tax parameters                   | The default value for the marginal base calculations method is "Total" for sales tax parameters. The Ledger Parameters entity does not set that value. However, some tax codes use a marginal base of "Line", which will fail validation. A new entity called Sales tax parameters preset entity was created to allow you to import the marginal base calculation method first so you can then import tax codes | 
| Accounts receivable            | Customer write-off reason code         | Apply a filter to Company if you only want one legal entity |
|                                | Customer details                       | Unmap EmployeeResponsibleNumber unless workers have been imported. Unmap CollectionsContactPersonID unless workers and their contact information has been imported |
|                                | Customers                              | The Customers entity was designed for use with Odata scenarios. For configurations, use the Customer definitions entity and the Customer details entity. The Customer definitions entities allows you to import the basic information about a customer so entities that require a customer will have that information. The Customer details entity contains addition information about a customer that you can add after parameters and reference data has been set up |
| Budget                         | Budget cost elements                   | Apply a filter to Legal entity if you only want one legal entity | 
|                                | Budget plan process                    | Apply a filter to Ledger if you only want one legal entity | 
|                                | Budget plan allocation schedule        | Apply a filter to Ledger if you only want one legal entity | 
|                                | Budget plan stage Rule                 | If you applied a filter to Budget plan process, you may see errors when importing stage rules. The entity currently does not have a Ledger name in it that can be filtered so it will contain all companies | 
|                                | Budget plan priority constraint        | You will see the same issue described for stage rules | 
|                                | Budget plan process administration     | You will see the same issue described for stage rules | 
| Inventory                      | Warehouse current postal address       | Apply a filter to Company if you only want one legal entity |
|                                | Site current postal address            | Apply a filter to Company if you only want one legal entity | 
|                                | Warehouse current postal address       | Apply a filter to Company if you only want one legal entity. Unmap the Picking store area and Input store area unless Retail information has been imported | 
|                                | Warehouse locations                    | Some warehouses locations require a Location profile ID.   Location profile ids require a Location format. This information must be imported before the warehouse location  | 
| Product information management | Products                               | Unmap NMFCCode and STCCCode. There are no entities available for those codes at this time |
|                                | Products                               | The EcoResProduct and EcoResReleasedProduct entities should be used for configurations. The EcoResProductMaster, EcoResDistinctProduct, EcoResReleasedProductMaster, EcoResReleasedDistinctProduct entities should be used for Odata scenarios |
|                                | Released products                      | Unmap project category, default product color, default configuration, default product size, and default product style. This entity is self-referencing and has not yet been updated to load these fields in a single pass |
|                                | Product document attachments           | For Product documents (EcoResProductDocumentAttachmentEntity) and released product documents (EcoResReleasedProductDocumentAttachmentEntity, you must never skip staging because additional steps are performed in the staging environment. You must use a data package for export and for import  because the export file needs to be accompanied by a resources folder with the attechments. The entities support images, documents, notes, and links. When you export, you will see an image file with a name that looks like a GUID. It is a valid data package needed to complete the import |
|                                | Period template                        | The Period template entity is a shared entity. It can be filtered by Legal entity but the Period template lines entity does not have a Legal entity field. If you want to import a single legal entity, you can filter the period template. However, you must remove the period template lines that are not related to that legal entity |
|                                | Item coverage group                    | Unmap Period template ID unless they were already imported |
| Procurement                    | Vendors                                | Unmap purchase site and warehouse unless they are set up. Unmap the 1099 box id and 1099 type unless you have opened the 1099 form. Unmap the vendor bank acccount ID. The vendor bank account entity will set up the link to the bank account when the vendor when it is imported |
|                                | Vendor catalog                         | Please refer to the discussion for importing vendor catalogs in the Supply Chain Management blog https://blogs.msdn.microsoft.com/dynamicsaxscm/2016/05/25/vendor-catalogs-in-dynamics-ax/  |
| Sales and marketing            | Leads                                  | Unmap LeadOpeningPersonnelNumber, LeadClosingPersonnelNumber, LeadResponsiblePersonnelNumber unless workers have been imported |
                                 
                                 
Import a configuration
----------------------

The data management workspace is also your hub for importing
configuration data projects. You can build a configuration project from
an existing data project that you exported or from individual files that
contain data formatted correctly for import into Dynamics 365 for
Finance and Operations.

The process for importing a configuration is as follows:

1)  Open the data management workspace and switch to the Enhanced view.

2)  Select the Import tile in the data management workspace.

3)  Select New to create the configuration project and add an ID and
    name that represents the configuration

4)  Select the data project operation type (Import) and project category
    (Configuration).

5)  Use the Add file button to select the file that has your entity
    information and data. The extension of the file name will be matched
    to the default file extensions in the data sources and the source
    data format will be populated automatically. If you have not set up
    the default file extensions, then select a source data format first
    before you select the file.

6)  Use Remove entity to remove one or more selected entities

You are ready to import a configuration. However, you may want to use
some additional features to control the export process:

1)  Organize your list by using the Sort by button to reorder your
    entities by unit, level and sequence

2)  If want to change the execution sequence of any of the entities,
    edit the unit, level, or sequence manually or use the resequence
    button to update any entities that you have selected.

3)  If necessary, change the entity mappings using the View map icon.

4)  Use the check box in the Disable column to temporarily stop the
    entity from being used when exporting a data project

Now that you have completed your configuration, use the import button to
start the import. You can monitor your results on the execution details
page that is displayed.

Using the data management workspace
-----------------------------------

The data management workspace provides access
to key tasks for data management while providing information on projects
and project execution tasks. For configurations, you should be using the
enhanced view, which you can enable using the enhanced view button. If
your system default in the framework parameters has been changed to
enhanced, that view will open by default.

The first list on the page is the project list. Each project is
displayed with the type of configuration (import or export) and a
project category (project, configuration, integration, and other). Use
the selections to the left of the grid to filter by the appropriate
project. To open a project, select the project and click on load project
to launch the import or export form. You can also download the project
definitions with the download button.

The second list provides details about the projects that you have
executed. Use the selections to the left of the grid to filter by the
data range that was executed for the job. You can view the execution
details by selecting a job and clicking on the execution details menu.
For export tasks, you can download the data from the workspace using the
download page button.

Templates
---------

The templates page provides you with the tools to create a template of
entities. The form is very similar to the configurations form and the
features work in much the same way. The process for creating templates
is:

1)  Use New button to create the template. Add an ID and name that
    represents the template. Note that the status is set to “Draft”

2)  Add entities or remove them as needed.

3)  Organize your list by using the Sort by button to reorder your
    entities by entity group or by unit, level and sequence

4)  If want to change the sequence of any of the entities, edit the
    unit, level, or sequence manually or use the resequence button to
    update any entities that you have selected. You must select more
    than one entity for that button to appear

5)  Add filters to the entity with the Filter icon. Then review the
    results of the filters using the Preview icon. If you add a filter, the filter icon will change to an edit icon.

6)  If necessary, change the entity mappings using the View map icon.

7)  Use the Validate template button to change the status to Validated.

Your template is ready to be used in a project. However, you may want to
use some additional features to control the export process:

1)  If you already have a list of entities that you want to add quickly,
    use the Open in Excel button to open Excel. Copy and paste your
    entities in Excel and click on the Publish button

2)  If you exported a template and you want to bring that template back
    into Dynamics, select Import template, browse to the template file,
    click on Upload, and then click on OK to load it

3)  If you want to replace the contents of an existing template, select
    the replace template button, browse to the template file that has
    the entities that you want to import, click on Upload, and then
    click on OK to load it. The template values in the current template
    will be replaced by the new template

4)  If you want to create a template from a project, follow the steps
    above to create a new template. Use the replace template from
    project button to display a list of projects to choose from. Select
    a project and click on Ok to bring the project entities into the
    template. The existing entities will be removed before the project
    entities are copied into the template.

### Loading default templates
-----------------------------

Default templates are delivered with each new release in the product. These templates are automatically loaded when you first install your instance of Dynamics 365 for Finance and Operations. 

Once they are loaded, you can change them to suit your business needs. However, if you want to retrieve the default templates, you can use the reload default templates button to add them back to your system. You can either replace the templates with the latest versions or select an option to make a copy the old templates first and then add the default templates.

### Merged templates
--------------------

We created larger templates that are a combination of the smaller module templates for convenience. You can use the larger templates or add any combination of smaller templates to build a data project. 
-   System and Shared includes system setup, global address book, shared general ledger, and workflow
-   Financials includes general ledger, bank, accounts payable, tax, accounts receivable, fixed assets, and budgeting
-   Supply chain includes inventory management, product management, procurement, sales and marketing, warehouse management, production control, and costing
 
### Master data in the templates
--------------------------------

Many of the templates include entities for master data such as customers, vendors, and released products. These are included to indicate the proper sequence of entities that you will need once you have loaded parameters and reference data. Master entities are most often sequenced in the module bands number from 100 and up (see sequencing philosophy) and they will shown in the grid under entity category as master.

### Templates with the same entity
----------------------------------

There are entities that are needed in more than one template. For example, you need payment terms in both Accounts payable and Accounts receivable. However, you may only need the Accounts receivable template so we added the entity to both templates.

A data project can only have one instance of an entity in it. If you add a template that contains an entity that already exists in a data project, the entity in that template will replace the entity in the project. 

You can use this capability to override the default templates without changing them. For example, if the worker field has been unmapped in your data project but you have your own template that adds workers, you can build a template that includes the entities that have the worker field. In that template, you can map the worker field and it will replace the entities in the data project that unmapped the field.

Sequencing philosophy for templates
-----------------------------------

### Units, levels and sequences

The unit, level and sequence is used in data management to control the
order in which the data is exported or imported.

-   Entities with two different units are processed in parallel.

-   Within a unit, entities are processed in parallel if they have the
    same level.

-   Within the same level, they are processed by the sequence order
    within the level.

-   Once a level is completed, the next level is processed.

-   We use only unit 1 to ensure that all dependencies are handled in
    the correct order.

Entities are categorized by module name, entity category, and a tag. The
module represents the module that the entity is normally used for. The
entity category represents the type of information in the category, like
parameters or reference data.

Tags provide additional details about the function of the entity in that
feature area. For example, entities for the general ledger have a module
name of General Ledger. There are several tasks within the general
ledger and tags represent those tasks. For example, Setup and Journals
are tags that represenet tasks that can be done for the general ledger.

### Sequencing philosophy

The long term goal for sequencing is to have Dynamics 365 for Finance
and Operations to sequence all of the entities automatically for every
configuration. In the interim, we have created the sequences for the
entities in each of the templates to make it easier to process
configurations.

The following list shows how the templates were set up to handle the
dependencies. Please note that the entities do *not* require these
sequences to work. They have been created to help you build better
configurations.
 

|  **Module**               |**Unit**   |**Level**   |**Sequence**|
|-------------------------	|--:	|----:	|---:	|
| System setup            	| 1 	|  10 	| 10 	|
| Global address book     	| 1 	|  15 	| 10 	|
| General ledger shared   	| 1 	|  20 	| 10 	|
| Workflow                	| 1 	|  22 	| 10 	|
| General ledger          	| 1 	|  25 	| 10 	|
| Band 1 for dependencies 	| 1 	|  30 	| 10 	|
| Band 2 for dependencies 	| 1 	|  40 	| 10 	|
| Band 3 for dependencies 	| 1 	|  50 	| 10 	|
| Band 4 for dependencies 	| 1 	|  60 	| 10 	|
| Band 5 for dependencies 	| 1 	|  70 	| 10 	|
| Band 6 for dependencies 	| 1 	|  80 	| 10 	|
| Band 7 for dependencies 	| 1 	|  90 	| 10 	|
| Bank                    	| 1 	| 100 	| 10 	|
| Accounts payable        	| 1 	| 120 	| 10 	|
| Tax                     	| 1 	| 130 	| 10 	|
| Accounts receivable     	| 1 	| 140 	| 10 	|
| Fixed assets            	| 1 	| 150 	| 10 	|
| Budgeting               	| 1 	| 160 	| 10 	|
| Inventory management    	| 1 	| 300 	| 10 	|
| Product management      	| 1 	| 310 	| 10 	|
| Procurement             	| 1 	| 320 	| 10 	|
| Sales and Marketing     	| 1 	| 330 	| 10 	|
| Warehouse management    	| 1 	| 400 	| 10 	|
| Production control      	| 1 	| 410 	| 10 	|
| Costing                 	| 1 	| 420 	| 10 	|
| Retail                  	| 1 	| 500 	| 10 	|
| Expense management      	| 1 	| 600 	| 10 	|
| Project accounting      	| 1 	| 650 	| 10 	|
| Human resources         	| 1 	| 700 	| 10 	|
| Payroll                 	| 1 	| 800 	| 10 	|
| Sales and Marketing     	| 1 	| 330 	| 10 	|
| Warehouse management    	| 1 	| 400 	| 10 	|
| Production control      	| 1 	| 410 	| 10 	|
| Costing                 	| 1 	| 420 	| 10 	|
| Retail                  	| 1 	| 500 	| 10 	|
| Expense management      	| 1 	| 600 	| 10 	|
| Project accounting      	| 1 	| 650 	| 10 	|
| Human resources         	| 1 	| 700 	| 10 	|
| Payroll                 	| 1 	| 800 	| 10 	|

We reserved levels 10-22 for the shared system entities so that they are
processed first. Almost all systems also use the company specific
general ledger entities so we reserved level 25 for those entities.
These levels represent the minimum basic setup required for most
configurations.

Once the basic setup is complete, there are a lot of entities that can
be loaded in parallel across all the modules. Instead of forcing them to
be loaded in silos by module, we set up bands of dependencies between
the data for different entities. We added entities that have no
dependencies to band 30. We then added band 40 for entities that have a
dependency on the entities in band 30. We continued the process for
bands 50 to 90.

After organizing the basic entities so that they can process in
parallel, we organized the remaining entities by module in the order
that the modules should be processed. However, there are a lot of
entities that have many dependencies, some of which are complex. For
example, the vendor posting profiles may need vendors or items. Although
that entity would be in the accounts payable module, it needs to happen
after product management. In that case, if vendors are 1.130.10 and
items are 1.300.10, then vendor posting profiles must be moved to
something after that sequence like 1.310.20.

In short, the sequences described are a guideline, not a requirement.
There is no required relationship between a level and a module. You can
rearrange the entities if the sequence doesn’t work for your
installation. If you want to add your own templates to a configuration,
you can follow the guidelines above to ensure that your template merges
correctly into a project that uses other templates.

Additional information about entities
---------

### Obsolete entities
-----------------

As we create newer versions of Dynamics 365 for Finance and Operations, we may need to update the functionality of an entity. A new entity may be created with a modified name for it and the original entity will be marked as obsolete. You will no longer be able to add the obsolete entities to a new data project or template. However, if you load a data package that has the obsolete entity in it, you will be warned about the existence of an obsolete entity but you will be able to still import your data.

### Self referencing entities
-------------------------

There are entities that represent tables that have references to themselves. For example, when you create a cash discount, you can refer to a next cash discount. To import data, it is necessary to sequence the data so that the cash discount referred to in the next cash discount field is imported first, followed by the cash discount that uses it. 

We have added a class called DMFImportExportSequencer that you can add to an entity that will sequence your data in self referencing entities and enable the data to load in a single pass. You can view the code required to update your entities in the Cash Discount entity (CashDiscountEntity).

We have added the class to a number of entities that are self referencing. The list includes:
-   Cash discounts
-   Customers
-   Tax codes
-   Budget control groups
-   Projects
-   Product categories
-   Warehouses
-   Budget plan workflow stage
-   Sales units
