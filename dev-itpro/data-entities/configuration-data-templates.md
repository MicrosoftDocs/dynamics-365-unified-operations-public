---
# required metadata

title: Configuration data templates
description: This topic describes configuration data templates and explains how to create them. 
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
# Configuration data templates
Configuration data templates are predefined lists of entities for each module area that can be used in a data project. You can create, view, and modify these templates by using the **Template** page in the **Data management** workspace.

> [!IMPORTANT]
> Default configuration templates are on the roadmap for the July 2017 release of Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. The Configuration data project feature is available in Platform update 7. You can create and use your own templates in the current product release.

## Create a new configuration data template
The **Template** page in the **Data management** workspace provides tools that let you create a template of entities. This page resembles the configurations page, and the two features work in a similar manner.

To create a template, follow these steps.

1. Click **New** to create a template. Enter an ID and name for the template. Notice that the status is set to **Draft**.
2. Add or remove entities as you require.
3. Organize the list by using the **Sort by** button to reorder your entities by entity group, or by unit, level, and sequence.
4. To change the sequence of any of the entities, manually edit the unit, level, or sequence. Alternatively, use the **Resequence** button to update any entities that you've selected. The **Resequence** button appears only if you select more than one entity.
5. To add filters to an entity, use the **Filter** button. Then review the results of the filters by using the **Preview** button. If you add a filter, the **Filter** button changes to an **Edit** button.
6. If you don't want all fields to be mapped, you can use the **View map** button to exclude fields from the mapping.
7. Click **Validate template** to change the status to **Validated**.

Your template can now be used in a project. However, you might want to use some additional features to control the export process.

- Use the **Open in Excel** button to open the contents of the grid in a Microsoft Excel workbook. Modify the entities as you require, and then use **Publish** to upload the changes back into Dynamics 365 for Finance and Operations.
- If you exported a template and want to bring that template back into Dynamics 365 for Finance and Operations, Enterprise edition, click **Import template**, browse to the template file, and then click **Create template** to load it.
- To replace the contents of an open template, click **Replace from template** button, browse to the template file that has the entities that you want to import, and then click **Create template** to load the template file. The values in the open template will be overwritten.
- To create a template from a project, click **New** to create a template. Enter an ID and name for the template, and then click **Replace template from project**. In the list of projects that appears, select a project, and then click **Create template** to bring the project entities from that project into the open template. The values in the open template will be overwritten.

## (Coming in the July 2017 release) Default data templates
In the spring release of Dynamics 365 for Finance and Operations, Enterprise edition, we plan to release predefined templates to help you create configuration data projects. The templates will be sequenced, so that the data that the entities generate will be processed in the correct sequence. Our predefined templates are also designed to maintain the correct sequence when more than one template is added to the same data project. For more information, see the "Sequencing in the default templates" section.

Default templates will be delivered together with each new release of Dynamics 365 for Finance and Operations. Our long-term goal is to provide the templates in Microsoft Dynamics Lifecycle Services (LCS), so that you can push them to an instance of Dynamics 365 for Financial and Operations. However, for the current releases, click the **Templates** tile in the **Data management** workspace, and then click **Load default templates** to load the templates.

After the templates are loaded, you can change them to suit your business requirements. If you ever want to retrieve the original default templates, you can use the **Load default templates** button to add them back to your system. This step will replace the templates with the latest versions. If you have made changes to the templates, you can make a copy of the old templates by exporting them. Please note that loading default templates and importing templates required system administrator access to ensure that all entities are correctly loaded into the template.

### How entities are sequenced for processing
Whether you're creating your own templates or using the default templates, it's important that you understand how templates are sequenced for processing during export and import.

#### Units, levels, and sequences
The unit, level, and sequence of an entity are used to control the order that the data is exported or imported in.

- Entities that have two different units are processed in parallel.
- Within a unit, entities are processed in parallel if they have the same level.
- Within the same level, entities are processed by the sequence order within the level.
- After processing of one level is completed, the next level is processed.
- We use only unit 1 to to help guarantee that all dependencies are handled in the correct order.

Entities are categorized by module name, entity category, and tag.

- The module represents the module that the entity is typically used for. 
- The entity category represents the type of information in the category. For example, a category might include parameters or reference data.
- Tags provide additional details about the function of the entity in that feature area. For example, entities for the general ledger have a module name of **General ledger**. There are several tasks within the General ledger, and the tags represent those tasks. For example, **Setup** and **Journals** are tags that represent tasks that can be done for the General ledger.

#### Sequencing in the default templates
Our long-term goal for sequencing is to automatically sequence all the entities for every configuration. Until we reach that goal, we have created, for the entities in each of our default templates, sequences that represent the dependency order between entities.

The following table shows how the templates were set up to handle dependencies. Note that the entities do **not** have to be processed in the order that we have sequenced them in. You can sequence them differently if you want. However, you might inadvertently change the order that entities are processed in. If an entity requires data that hasn't been imported by another entity, you might receive errors because of missing dependent data.

| Module                  | Unit | Level |
|-------------------------|------|-------|
| System setup            | 1    |  10 	 | 
| Global address book     | 1    |  15 	 |
| General ledger shared   | 1    |  20   |
| Workflow                | 1    |  22 	 | 
| General ledger          | 1    |  25 	 | 
| Band 1 for dependencies | 1    |  30 	 | 
| Band 2 for dependencies | 1    |  40 	 | 
| Band 3 for dependencies | 1    |  50 	 | 
| Band 4 for dependencies | 1    |  60 	 | 
| Band 5 for dependencies | 1    |  70 	 |
| Band 6 for dependencies | 1    |  80 	 | 
| Band 7 for dependencies | 1    |  90 	 | 
| Bank                    | 1    | 100 	 |
| Accounts payable        | 1    | 120 	 |
| Tax                     | 1    | 130 	 |
| Accounts receivable     | 1    | 140 	 |
| Fixed assets            | 1    | 150 	 |
| Budgeting               | 1    | 160 	 |
| Inventory management    | 1    | 300 	 |
| Product management      | 1    | 310 	 |
| Procurement             | 1    | 320 	 | 
| Sales and Marketing     | 1    | 330 	 |
| Warehouse management    | 1    | 400 	 |
| Production control      | 1    | 410 	 |
| Costing                 | 1    | 420 	 |
| Retail                  | 1    | 500 	 | 
| Expense management      | 1    | 600 	 |
| Project accounting      | 1    | 650 	 |
| Human resources         | 1    | 700 	 |
| Payroll                 | 1    | 800 	 |

We reserved levels 10 through 22 for shared system entities, so that those entities are processed first. Almost all systems also use the company-specific general ledger entities. Therefore, we reserved level 25 for those entities. These levels represent the minimum basic setup that is required for most shared data in a configuration.

After the basic setup is completed, many entities can be loaded in parallel across all the modules. These entities don't have to be loaded in silos by module. Instead, we set up bands of dependencies between the data for different entities. We added the entities that have no dependencies to band 30. We then added band 40 for entities that have a dependency on the entities in band 30. We continued the process for bands 50 through 90.

After we organized the basic entities so that they can be processed in parallel, we organized the remaining entities by module, in the order that the modules should be processed in. However, many entities have many dependencies, some of which are complex. For example, the Vendor posting profiles entity might require Vendors or Items entities. Although the Vendor posting profiles entity is in the **Accounts payable** module, it must be processed after the **Product management** module. In that case, if Vendors entities are 1.130.10 and Items entities are 1.300.10, the Vendor posting profiles entity must be moved so that it's after that sequence (for example, 1.310.20).

The sequences that we have implemented are a guideline, not a requirement. There is no required relationship between a level and a module. You can rearrange the entities if the sequence doesn’t work for your implementation. To add your own templates to a configuration, you can follow the preceding guidelines to help guarantee that your template is correctly merged into a project that uses default templates.

#### Templates that have the same entity
Some entities are required in more than one template. For example, you must have payment terms in both the Accounts Payable and Accounts Receivable templates. However, you might require only the Accounts Receivable template. We added the entity to both templates for situations where you require only one of them.

A data project can include only one instance of an entity. If you add a template, and the template contains an entity that already exists in a data project, the entity in that template replaces the entity that is currently in the project.

You can use this capability to override the default templates without changing them. For example, the **worker** field hasn't been mapped in your data project, but you have your own template that adds workers. In this case, you can build a template that includes the entities that have the **worker** field. In that template, you can map the **worker** field. Entities in the data project that don’t have the field mapped will then be replaced.

#### Merged templates
We have created larger templates that cover multiple module areas. You can use the larger templates or any combination of smaller templates to build a data project. The following combined templates are available:

- System and Shared, which include system setup, global address book, shared general ledger, and workflow
- Financials, which includes general ledger, bank, accounts payable, tax, accounts receivable, fixed assets, and budgeting
- Supply chain management, which includes inventory management, product management, procurement, sales and marketing, limited warehouse management, production control, and costing

The Expense and Project Management templates aren't included in a larger template. However, they are designed so that they can easily be merged into a project that uses other templates.
 
#### Master data
Many default templates include entities for master data such as customers, vendors, and released products. These entities are included to indicate the proper sequence of entities that you will require after you've loaded parameters and reference data. Master entities are most often sequenced in the module bands that are numbered 100 and above. In the grid, the entity category for these entities will be **Master**.

If you don't want to include master data in your configuration, remove those entities from your project.
