---
# required metadata

title: Import data from a CSV data source (AX 2012)
description: You can use the Microsoft Dynamics AX 2012 Data Import/Export Framework to import data from a CSV file into Microsoft Dynamics AX.
author: kfend
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 18801
ms.assetid: f358a897-31c0-46fe-a554-3798afa2f65d
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Import data from a CSV data source (AX 2012)

[!include[banner](../includes/banner.md)]


You can use the Microsoft Dynamics AX 2012 Data Import/Export Framework to import data from a CSV file into Microsoft Dynamics AX.

This walkthrough provides examples to illustrate the following tasks:

-   Find a CSV file to use as a source
-   Define the format of your source data
-   Define a processing group
-   Process data from source to staging
-   Validate the data in staging
-   Process data from staging to target
-   Validate the data in target

## Prerequisites
To complete this walkthrough you will need:

-   Microsoft Dynamics AX 2012, Microsoft Dynamics AX 2012 R2, or Microsoft Dynamics AX 2012 R3
-   Data Import/Export Framework

## Find a CSV file to use as a source
To work through this example, use any of the delimited demo files that are shipped with the Data Import/Export Framework. For more information on the demo files, see [Demo files for the Data import/export framework (DIXF, DMF)](demo-files-dixf.md).

## Define the format of your source data
1.  Open **Data Import/Export Framework**, and then click **Setup** &gt; **Source data formats**.
2.  Click **New** and enter the name CSV for the source.
3.  Verify that the source type is **File**.
4.  Configure the following options:

    | **Setting**                     | **Value**                                                                                    |
    |---------------------------------|----------------------------------------------------------------------------------------------|
    | **File format**                 | Delimited                                                                                    |
    | **First row header**            | Selected                                                                                     |
    | **Row delimiter**               | {CR}{LF}                                                                                     |
    | **Column delimiter**            | Comma {,}                                                                                    |
    | **Text qualifier**              | "                                                                                            |
    | **Code page**                   | 1252 Western European (Windows)                                                              |
    | **Unicode**                     | Not selected                                                                                 |
    | **Language locale**             | en-us                                                                                        |
    | **Dimension code**              | The dimension code you choose will vary, based on which demo file you have chosen to import. |
    | **Chart of accounts delimiter** | -                                                                                            |

## Define a processing group
1.  In **Data Import/Export Framework**, click &gt; **Common** &gt; **Processing group**, and then click **New** to create a new processing group.
2.  Set the group name and description.
3.  Click **Entities** to select the entities to include in the processing group, and enter the following information.
    1.  In the **Select entities for processing group** form, click **New**, and then, for **Entity name**, enter a name.
    2.  Set the **Source data format** to CSV.
    3.  In the **Sample file path field**, locate the file to import from the demo files at the following location: Program Files/Microsoft Dynamics AX 2012/Data Import/Export Framework Client Component&lt;version&gt;DemoFilesDelimited .
    4.  Click **Generate source mapping**.
    5.  To view the source mapping, click **Modify source mapping**. Close the **Map source to staging** form.
    6.  Click **Validate**.
    7.  Click **Preview source file**, and then close the **Select entities for processing group** form.

## Process data from source to staging
1.  In the **Processing group** form, select the group that you created, and click **Get staging data**.The **Create a job ID for the staging data job** form opens.
2.  By default, an ID for the job is generated. You can optionally modify the ID and add a description. Click **OK**.The **Staging data execution** form opens.
3.  Under **Entity details**, enter the path of the file that contains all of your source data, and then click **Run**. **Note:** If your sample file and full source file are different from each other, you would change to your full source file at this point.
4.  In the **Get data from source to staging** form, click **OK** to run immediately. The source data is copied to the staging tables.

## Validate the data in staging
1.  In **Data Import/Export Framework**, click **Common** &gt; **Processing group** &gt; **Execution history**, and then select the job that ran.
2.  Click **View staging data**.
3.  Review the staging data to validate that it matches the source file.
4.  Click **Validate all** to verify that all the related reference data is correct and present in the system.

## Process data from staging to target
1.  In **Data Import/Export Framework**, click **Common** &gt; **Processing group**, and then select the processing group to work with.
2.  Click **Copy data to target**.The **Select a job ID to run** dialog box opens.
3.  Select the job that you created in the previous procedure, and click **OK**. The **Target data execution** dialog box opens.
4.  Click **Run**, and then click **OK**.The data is copied to the target entities.

## Validate the data in target
View staging data:

1.  In **Data Import/Export Framework**, click **Common** &gt; **Processing group** &gt; **Execution history** &gt; **View staging data**, and then select the job that ran.
2.  Click **Target**.
3.  Verify that the data is correct.



