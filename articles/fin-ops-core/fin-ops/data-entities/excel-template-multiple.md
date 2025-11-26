---
title: Data templates with multiple worksheets
description: Learn about how to import data using Excel data entity templates into finance and operations, including an outline on how to upload a file and map it to all entities.
author: johnmichalak
ms.author: johnmichalak
ms.topic: article
ms.date: 11/20/2025
ms.custom:
ms.reviewer: twheeloc
audience: Application user
ms.search.region: Global
ms.search.validFrom: 2018-01-01
ms.search.form: 
ms.dyn365.ops.version: Platform update 13
---

# Data templates with multiple worksheets

[!include [banner](../../../finance/includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-3.md)]

Data management in the application supports Microsoft Excel-based templates for data entities. These templates can contain one or more worksheets. You often use templates with multiple worksheets when it's convenient to manage data in a single file and import it to multiple data entities. An example would be sites and warehouses.

## Upload a file once and map it to all entities
Let's take an example where one Excel file has worksheets called **Sites** and **Warehouses**. To set up the data import project, you add the first data entity, **Sites**, and then upload the file. You can select **Sites** as the worksheet to use for this entity.

If you add the second entity **Warehouses** without leaving the **Add file** form, the worksheet lookup lets you select the **Warehouses** worksheet without having to upload the file again. The only reason to upload a new file would be if the **Warehouses** data was in a different file.

![Multiple worksheets.](../../dev-itpro/data-entities/media/AddFileMultipleWorkSheets.png)

## Fix worksheet to entity mapping

You can fix the mapping of the worksheet to a data entity in the import job from the grid. The **Worksheet** column in the grid shows the worksheets from the file that you mapped. You can choose a different worksheet from the drop-down menu. If the chosen worksheet is already mapped to an entity in the data project, the system asks you to confirm the change. Fix all mappings in the grid.

![Update worksheet mapping.](../../dev-itpro/data-entities/media/UpdateMappings.png)

## Re-map to a new file

If you need to upload a new version of the same file or a completely new file for existing entities in a data project, use the **Add file** experience, and add the entities again as if you're adding them for the first time. The system confirms that you want to overwrite the existing entities in the data project before proceeding. Entities that you don't add again (or overwrite) keep the previous mappings from the previous file.

## Upload a file by using Run project

You can upload an Excel file when you select **Run project** to execute an import project. Be sure to upload only files that have the same worksheets as the existing mappings on the data entities in the data project. If the newly uploaded file doesn't contain a worksheet, the system displays an error and stops the import. If you need to change the mapping to the worksheet for an entity, first update the mappings in the data project before using the file in the **Run project** experience.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

