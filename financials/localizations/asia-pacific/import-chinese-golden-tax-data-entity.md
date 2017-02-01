---
# required metadata

title: Import the Chinese Golden Tax data entity | Microsoft Docs
description: This topic explains how to import the Chinese Golden Tax data entity into Microsoft Dynamics 365 for Operations.
author: ShylaThompson
manager: AnnBe
ms.date: 2016-12-02 21:05:44
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: 81
ms.suite: Released- Dynamics 365 for Operations version 1611
# ms.tgt_pltfrm: 
ms.custom: 261394
ms.assetid: cc3c6b26-efd3-4fbd-84b0-9ae64e71d5b5
ms.region: China (PRC)
# ms.industry: 
ms.author: leguo

---

# Import the Chinese Golden Tax data entity

This topic explains how to import the Chinese Golden Tax data entity into Microsoft Dynamics 365 for Operations.

To import the Chinese Golden Tax data entity, complete the following steps.

1.  Go to **System administration** &gt; **Data management**.
2.  Click the **Import** tile to create a new import project.
3.  Enter a name for the project.
4.  Select the source data format **XML-Element**.
5.  In the **Entity name** field, select **Tax integration import** entity.
6.  Click upload and then browse to the location of your golden tax data file.
7.  Click **View map** on the **Tax integration import** tile.
8.  On the **Transformations** tab, click **New**.
9.  Click **Upload file** and browse to the location of the .xlst file.

For specific steps that show how to import a data entity, refer to [Importing data by using entities](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/data-entities/building-and-consuming-data-entities#importing-data-by-using-entities). To practice the Chinese Golden Tax data entity import using the demo data company CNMF, download the following files from [CustomerSource](https://mbs.microsoft.com/customersource/global/ax/learning/samplefilestaximportchina).

-   **ImportSampleFile.xml** - This file is the Chinese Golden Tax data entity composite.
-   **Tax-Import-to-XML.xslt** - This file is used as the transformational file mapping.

The following screenshot shows an example mapping visualization for the Chinese Golden Tax data entity. [![This image shows a sample mapping visualization for the Chinese Golden Tax data entity.](./media/goldentaximportmappingvisualization.png)](./media/goldentaximportmappingvisualization.png)      

