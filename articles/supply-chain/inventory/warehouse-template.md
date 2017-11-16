---
# required metadata

title: Set up warehouse using warehouse configuration template
description: This topic discusses how you can set up warehouse by using the warehouse configuration template.
author: perlynne
manager: AnnBe
ms.date: 11/16/2017
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata
ms.search.form: DataManagementWorkspace, DMFQuickImportExportEnhanced, DMFDefinitionGroupTemplate, DMFEntityTemplateDefinitionLoadDialog
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: YuyuScheller
ms.search.scope: Core, Operations
# ms.tgt_pltfrm:
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Distribution
ms.author: perlynne
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: AX 7.3

---


# Set up warehouse using warehouse configuration template

[!include[banner](../includes/banner.md)]


This topic discusses how you can set up warehouse by using the warehouse configuration template. Several predefined configuration templates already exist. For information about how to 
use these templates, see [Configuration data templates](../../dev-itpro/data-entities/configuration-data-templates.md)

## Scenarios that can benefit from using the configuration templates

Many different scenarios can benefit from using the configuration templates. For example,  

-  You have completed and tested setup in a test environment. You want to copy this setup to a production environment. 
-	 You want to be able to roll out the warehouse setup to several legal entities or create a new warehouse within the same legal entity.
-	 You want to quickly prepare for a demo of the warehouse functionality.
-	 You want to enable the existing items and warehouses to use the functionality in Warehouse management instead of Inventory management.

This topic focuses on how you can copy the setup from a test environment to a production environment. 

## Copy configuration setup from a test environment to a production environment

Let’s consider a scenario where the configuration setup for warehouse and some transaction processes already exist in a test environment. Now you want to copy the configuration setup for warehouse from a test environment to a production environment. 

> [!NOTE]
> It is important that you must include other related setup data when you copy the configuration setup. For example, you want to set up products by copying the setup from a test environment. It won’t’ be possible for you to set up fixed picking location for a product before the product is created. This kind of dependency is not supported by each individual configuration template, but default data templates exist for the dependency and can easily be included in a configuration process.

### Export the default warehouse template 

1.	Go to **Data management workspace**. 
> [!NOTE]
> If this is the first use, you need to load all the data entities first. 
2.	Select the "**emplates** tile in the **Data management** workspace, and then select **Load default templates** to load the templates. 
> [!NOTE]
> To see the **Load default templates** menu, you must use **Enhanced view**. Click **Framework parameters** to select **Enhanced view** in the **View defaults** field.
3.	After the templates are loaded, you can change them to suit your business requirements. 
> [!NOTE]
> The system administrator access is required to load default templates and import templates. This requirement helps guarantee that all entities are correctly loaded into the template.
4.	Make sure you are in the legal entity from which you want to export the company specific data.
5.	In the workspace, select Export and create a new export project. 
6.	Then select **+Add template** and find the default warehouse template **400 - WMS**. This adds data entities for warehouse configuration. 
> [Note]
> If the data that will be exported needs to be filtered, for example, the data related to a specific warehouse, each data entity will need to be evaluated, and filtering will be added via a query. Alternatively, you can export all data and then delete the records that are not needed in the destination files.
7.	When you click **Export**, data related to all the data entities in the project will be exported. 
8.	It will be possible to download a .zip data package file that contains all the data in the selected format, for example, Excel. As discussed above, some records in the data package files might need to be updated before they can be imported to the production environment. If you update a record, make sure that you don’t change the file name. 

### Import warehouse configuration setup

1.	In the destination environment, make sure that you are in the company to which the warehouse data will be imported.
> [!NOTE]
> Another thing to consider before you do the import is to identify whether there are data dependencies. Here is an example. The data entity called **Warehouse disposition codes** exists in the **Warehouse management** template. This entity contains data related to the setup form **Warehouse management** > **Setup** > **Mobile device** > **Disposition codes**. If a setup exists for handling a sales order return process, the field **Return disposition code** will contain a value. This identification code happens to be related to the **Disposition code** data entity, which is part of the **Sales and marketing** template. If the data from the **Disposition code** don’t get imported before the data from the **Warehouse disposition codes** get imported, the import will fail. 

2.	Click **Import** in the **Data management** workspace. 
3.	After you have created a new import project, select **+Add file** and upload the .zip data package file.
4.	Click **Import**. When using the **Enhanced view**, you can quickly get an overview of the potential problems that might happen during the import via the **Filter** option. 
5.	The **View execution log** provides detailed information about each imported data entity. You can quickly come to the target data via the staging data view to see how the imported data looks like in the related application forms. When using the default data templates, the import sequence for each data entity will work as predefined to make sure that all the dependent data get imported first. In case custom build data entities are part of the project you will need to make sure to get the right sequence defined. See [Configuration data templates](../../dev-itpro/data-entities/configuration-data-templates.md)

## Related topic

[Configuration data templates](../../dev-itpro/data-entities/configuration-data-templates.md)

