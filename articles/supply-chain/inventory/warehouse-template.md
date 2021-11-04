---
# required metadata

title: Set up a warehouse by using a warehouse configuration template
description: This topic explains how to set up a warehouse by using a warehouse configuration template.
author: yufeihuang
ms.date: 11/16/2017
ms.topic: article
ms.prod:
ms.technology:

# optional metadata
ms.search.form: DataManagementWorkspace, DMFQuickImportExportEnhanced, DMFDefinitionGroupTemplate, DMFEntityTemplateDefinitionLoadDialog
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
# ms.tgt_pltfrm:
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Distribution
ms.author: yufeihuang
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3

---

# Set up a warehouse by using a warehouse configuration template

[!include [banner](../includes/banner.md)]

This topic explains how to set up a warehouse by using a warehouse configuration template. There are several predefined configuration templates that you can use. For information about how to use these templates, see [Configuration data templates](../../fin-ops-core/dev-itpro/data-entities/configuration-data-templates.md).

## Scenarios where configuration templates can be helpful

Configuration templates can be helpful in many scenarios. Here are some examples:

- You've completed and tested a configuration setup in a test environment, and you now want to copy the setup to a production environment.
- You want to roll the warehouse setup out to several legal entities or create a new warehouse in the same legal entity.
- You want to quickly prepare for a demo of the warehouse functionality.
- You want existing items and warehouses to use the functionality in Warehouse management instead of the functionality in Inventory management.

This topic focuses on the first of these scenarios. It shows how you can use a configuration template to copy a configuration setup from a test environment to a production environment.

## Copy a configuration setup from a test environment to a production environment

For this scenario, the configuration setup for a warehouse and some transaction processes already exist in a test environment. You now want to copy the configuration setup for the warehouse from the test environment to a production environment.

> [!NOTE]
> It's important that you include other related setup data when you copy a configuration setup. For example, you want to set up products by copying the setup from a test environment. However, you can't set up a fixed picking location for a product before that product is created. Although individual configuration templates don't support this type of dependency, there are default data templates that support it. You can easily include these default data templates in a configuration process.

### Export a default warehouse template 

1. Open the **Data management** workspace.

    > [!NOTE]
    > If you're using this workspace for the first time, you must load all the data entities before you continue.

2. Select the **Templates** tile, and then select **Load default templates** to load the default templates.

    > [!NOTE]
    > **Load default templates** is available only in the **Enhanced** view. Select **Framework parameters**, and then, in the **View defaults** field, select **Enhanced view**.

3. After the default templates are loaded, you can change them so that they meet your business requirements.

    > [!NOTE]
    > To load default templates and import templates, you must have system administrator access. This requirement helps guarantee that all entities are correctly loaded into the template.

4. Make sure that you're in the legal entity that you want to export the company-specific data from.
5. In the workspace, select **Export**.
6. Create a new export project.
7. Select **+ Add template**, and find the **400 - WMS** default warehouse template. This template adds data entities for warehouse configuration.

    > [!NOTE]
    > If the data that you're exporting must be filtered (for example, you want to export only the data that is related to a specific warehouse), you must evaluate each data entity and add filtering via a query. Alternatively, you can export all data and then delete the records that aren't required in the destination files.

8. Select **Export**. Data that is related to all the data entities in the project is exported.

You can download a zip file for the data package. This file contains all the data in the selected format (for example, Excel format). As has been mentioned, some records in the data package files might have to be updated before you can import them into the production environment. If you update a record, make sure that you don't change the file name.

### Import a warehouse configuration setup

1. In the destination environment, make sure that you're in the company that you want to import the warehouse data into.

    > [!NOTE]
    > Before you do the import, you should identify any data dependencies. For example, the **Warehouse management** template includes a data entity that is named **Warehouse disposition codes**. This entity contains data that is related to the **Disposition codes** setup page (**Warehouse management** > **Setup** > **Mobile device** > **Disposition codes**). If an existing setup already handles the return process for sales orders, the **Return disposition code** field contains a value. The disposition code in this field is related to the **Disposition code** data entity, which is part of the **Sales and marketing** template. If the data from the **Disposition code** data entity isn't imported before the data from the **Warehouse disposition codes** field, the import will fail.

2. In the **Data management** workspace, select **Import**.
3. Create a new import project.
4. Select **+ Add file**, and upload the zip file for the data package.
5. Select **Import**. In the **Enhanced** view, you can use the **Filter** option to quickly get an overview of issues that might occur during the import.

The **View execution** log provides detailed information about each data entity that is imported. You can use the staging data view to quickly get to the target data. In this way, you can see what the imported data looks like on the related pages in the application. When you use the default data templates, the import sequence for each data entity works in the predefined manner, to help guarantee that all dependent data is imported first. If custom data entities are part of the project, you must make sure that the correct sequence is defined. For more information, see [Configuration data templates](../../fin-ops-core/dev-itpro/data-entities/configuration-data-templates.md).

To learn more about how to use warehouse template to copy the configuration of a warehouse from one company to a new company within the same instance, see this 3-minute video on YouTube about [how to use warehouse template to copy the configuration for Finance and Operations](https://www.youtube.com/watch?v=K2WIfFlqJYs).

## Related topic

[Configuration data templates](../../fin-ops-core/dev-itpro/data-entities/configuration-data-templates.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]