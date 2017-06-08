---
# required metadata

title: Copying and comparing entity data between companies (AX 2012)
description: 
author: kfend
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: dynamics-ax-2012 
ms.service:
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 17841
ms.assetid: 6b2d300e-daec-441d-b19f-d3701296623d
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Copying and comparing entity data between companies (AX 2012)

[!include[banner](../../includes/banner.md)]




This process for copying entity data between companies is supported only for Microsoft Dynamics AX 2012 R2 and Microsoft Dynamics AX 2012 R3. If you are running an earlier version of the Data Import/Export Framework, see the instructions in [Walkthrough: Copy data between companies (DIXF, DMF)](copy-data-between-companies-dixf.md). This topic describes the following processes:

-   Copy entity data between companies
-   Compare entity data between companies

## Copy entity data between companies
To copy entity data between companies or legal entities, use the Copy entity data between companies wizard.

1.  Click **Data import export framework** &gt; **Common** &gt; **Copy entity data between companies**. The **Copy entity data between companies** **Wizard** opens.
2.  Click **Next &gt;**.
3.  On the **Name the comparison processing group** page, provide a name for the processing group, so that you can identify it later, and then click **Next &gt;**.
4.  On the **Select entities to compare** page, select one or more source entities to copy, click **&gt;** to add them to the list of entities to copy, and then click **Next &gt;**.
5.  On the **Select source and target companies** page, select one source company, and one or more target companies to copy the data to.
6.  Enter parameters for the batch job, enter the number of batch tasks to use when the batch is run, and then click **Next &gt;**.
7.  Click **Finish** to copy the entity data to the other companies. An Infolog message is displayed that describes how many records were inserted into staging then into the target company. The **Copy processing group** form opens.
8.  Click **Execution history** to review the entities that have been copied.

## Compare entity data between companies
To compare entity data between companies or legal entities, use the **Compare entity data between companies** **Wizard**. After you have compared data, you can select specific values to copy to the other system.

1.  Click **Data import export framework** &gt; **Common** &gt; **Compare entity data between companies**. The **Compare entity data between companies** wizard opens.
2.  Click **Next &gt;**.
3.  On the **Name the comparison processing group** page, provide a name for the comparison processing group, so that you can identify it later, and then click **Next &gt;**.
4.  On the **Select entities to compare** page, in the list of available entities, select one or more source entities to compare. Click **&gt;** to add the selected entities to the list of entities to compare, and then click **Next &gt;**.
5.  On the **Select source and target companies** page, select one source company, and one or more target companies to compare the data to.
6.  Enter parameters for the batch job, enter the number of batch tasks to use when the batch is run, and then click **Next &gt;**.
7.  Click **Finish** to create the processing group that compares the entity data to the information in the other companies. The **Comparison processing group** form opens.

    | **Note**                                                                                                                                                   |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | If the **Comparison processing group** does not list a processing group, then close it, and click **Compare entity data between companies** to re-open it. |

8.  Click **&gt;&gt;**, and then click **Comparison results**. The **Comparison results** form opens. This form lists the source company and the entities that were compared, and indicates whether an entity appears only in the source or only in the target, and whether identical values exist or different values exist.
9.  To view details, and copy specific rows of data from one company to another, select an entity from one company in the list, and then click **Details**. The **Comparison** form opens. It lists the entities being compared in the title, and has **Only in source**, **Only in target**, **Identical**, and **Different** tabs. On all tabs, except **Identical**, there is a **Transfer status** column, followed by the columns for the entity. Each record that meets the criteria is listed on the appropriate tab. On the **Different** tab, each column in the entity is listed twice. Data from the source system is on the left, and data from the target system is on the right.
10. To copy a record from source to target, select the records that you want to copy in the **Only in source** tab.
11. To copy a record from target to source, select the records that you want to copy in the **Only in target** tab.
12. To update a record that exists in both systems to match the source system, select the records that you want to copy in the **Different** tab.
13. When you have selected all of the records that you would like to modify, click **Update**.
14. In the **Write data from source to target** form, determine whether to use batch processing, identify a batch group, and then click **OK**. The data will be written to the specified systems. After the data has been modified, the **Transfer status** for a row will change to **Completed**.




