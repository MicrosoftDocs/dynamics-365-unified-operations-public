---
# required metadata

title: Copy configuration data to another company
description: 
author: mfalkner
manager: AnnBe
ms.date: 04/18/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, Implementer
# ms.devlang: 
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
that you can access from the data management workspace. The page allows
you to add and remove the entities that you need to manage the movement
of company and shared data. Once you create the list of entities in your
configuration, you can export or import the configuration using the data
management framework for processing. You can export packages locally or
move them to your LCS library for import into another instance.

Configuration **templates** are a predefined list of entities for each
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

The enhanced settings are saved for each user per each legal entity.
However, if you would like to change the system default to the enhanced
view, you can select the Framework parameters tile on the data
management workspace and change the page default from standard to
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

### Templates in LCS

Predefined templates are available in Life Cycle Services (LCS) as
shared assets for download and import into a Dynamics 365 installation.
These templates are sequenced so that the data managed by the entities
will be processed in the correct sequence. New templates and updates
will be released through Life Cycle Services (LCS) in between releases.

You can also add multiple templates to a single data project. The
predefined templates are designed to maintain the correct sequence when
they are merged. See the section on **sequencing philosophy** for more
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
    export. You can add entities using several methods

    a.  Add entity – enter the first part of name of the entity until it
        appears in the lookup.

    b.  Add multiple – enter any part of the entity name, use the lookup
        for application module, enter any part of the tag name, and/or
        use the lookup for the entity category to show a list of
        entities. Select the entities in the grid that you want to add

    c.  Add file – browse to a file that has a name that matches an
        entity and a file extension that matches the values that you
        entered in the data sources.

    d.  Add template – select from a list of **templates** that you have
        added to your instance

6)  Select a target data format. The system remembers that last data
    format that you selected or, if you select a file, it will default
    the data format to the file extension found in the data sources

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
    edit the unit, level, or sequence manually or use the Resequence
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

3)  Add filters to the entity with the Filter icon. The data will be
    filtered as it is imported.

4)  If necessary, change the entity mappings using the View map icon.

5)  Use the check box in the Disable column to temporarily stop the
    entity from being used when exporting a data project

Now that you have completed your configuration, use the import button to
start the import. You can monitor your results on the execution details
page that is displayed.

Special entity setup considerations for exporting and importing configurations
------------------------------------------------------------------------------

There are several entities that require some additional steps when you
are doing configurations. Please follow these recommendations as you
build your configurations

  Entity name   Technical name   Action needed
  ------------- ---------------- ---------------
                                 
                                 

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
    results of the filters using the Preview icon

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

Sequencing philosophy
---------------------

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
configuration. In the interim, we have assigned the sequences to
entities in each of the templates to make it easier to process
configurations.

The following list shows how the templates were set up to handle the
dependencies. Please note that the entities do *not* require these
sequences to work. They have been created to help you create better
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

Master data
-----------

Included in templates

Marked as disabled?
