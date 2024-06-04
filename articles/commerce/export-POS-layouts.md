---
title: Export POS screen layouts for import to a new environment
description: This article describes how to export point of sale (POS) screen layouts for import to a new environment in Microsoft Dynamics 365 Commerce.
author: anush6121
ms.author: anvenkat 
ms.topic: article 
ms.date: 06/04/2024
ms.custom: 
  - bap-template
ms.reviewer: v-chrgriffin
ms.search.validFrom: 2024-01-20
---

# Export POS screen layouts for import to a new environment

[!include [banner](includes/banner.md)]

This article describes how to export point of sale (POS) screen layouts for import to a new environment in Microsoft Dynamics 365 Commerce.

## Export screen layout data

To export screen layout data from an environment, follow these steps.

1. In the Commerce headquarters environment that you want to export data from, go to **Data management** \> **Framework parameters**.
1. Select **Entity settings**.
1. Under **Advanced entity configuration settings**, select **Refresh entity list**. The following message appears at the top of the page: "The refresh entity list job is added to the queue."
1. Go to **Batch jobs** \> **System Administration** \> **Inquiries**, and verify that the refresh entity list job was successfully completed.
1. Go to **Data management** \> **Export**.
1. Under **Group name**, enter a name for the export (for example, **Export POS layouts**).
1. Under **Selected entities**, select **Add multiple**.
1. In the **Add multiple** dialog box, in the **Target data format** dropdown list, select **XML-Element**.
1. Set the **Skip staging** option to **No**.
1. For each of the following entities, filter for the entity in the **Entities** box, select the entity result in the **Entity** column, and then select **Add selected**.

    - **Layout sizes** (Include this entity only when you're exporting new layout sizes that don't exist in the new environment.)
    - **RetailTillLayoutConfigurationEntity**
    - **POS button grid**
    - **POS button grid buttons**
    - **POS layout images**
    - **POS screen layouts**
    - **POS screen layout button grid zones**
    - **POS screen layout image zones**
    - **POS visual profiles**

1. Select **Close** to close the dialog box.
1. For the **RetailTillLayoutConfigurationEntity** entity, in the **Filter** column, select the funnel symbol.
1. In the **Inquiry** dialog box, for the entity where the **Field** value is **Screen layout ID**, in the **Criteria** column, enter criteria text (for example, **SCO\***), and then select **OK**.
1. For the **POS button grid** entity, in the **Filter** column, select the funnel symbol.
1. In the **Inquiry** dialog box, for the entity where the **Field** value is **Button grid ID**, in the **Criteria** column, enter criteria text (for example, **SCO\***), and then select **OK**.
1. For the **POS button grid buttons** entity, in the **Filter** column, select the funnel symbol.
1. In the **Inquiry** dialog box, for the entity where the **Field** value is **Button grid ID**, in the **Criteria** column, enter criteria text (for example, **SCO\***), and then select **OK**.
1. For the **POS screen layouts** entity, in the **Filter** column, select the funnel symbol.
1. In the **Inquiry** dialog box, for the entity where the **Field** value is **Screen layout ID**, in the **Criteria** column, enter criteria text (for example, **SCO\***), and then select **OK**.
1. For the **POS visual profiles** entity, in the **Filter** column, select the funnel symbol.
1. In the **Inquiry** dialog box, for the entity where the **Field** value is **Profile number**, in the **Criteria** column, enter criteria text (for example, **SCO\***), and then select **OK**.

    > [!NOTE]
    > Filtering by specific criteria helps reduce the risk of accidental overrides in the import environment.

1. To filter for a specific range of images, follow these steps:

    1. For the **POS layout images** entity, in the **Filter** column, select the funnel symbol.
    1. In the **Inquiry** dialog box, for the entity where the **Field** value is **Image ID**, in the **Criteria** column, enter a number range for the image IDs in the format **\<*image ID start*\>..\<*image ID end*\>**, and then select **OK**. For example, enter **60000..60026** to export all images that have image IDs from 60000 through 60026.

### Add related tables

If you require additional filters, you can add related tables. For example, you can add the **Layout sizes** table to export only a specific size or sizes from the selected list of layouts. You add this table to the entity using a table join.

To add the **Layout sizes** table, follow these steps.

1. Select the rows for **POS screen layout button grid zones**, **POS screen layout image zones**, and **RetailTillLayoutConfigurationEntity**.
1. For the **POS screen layout button grid zones** entity, in the **Filter** column, select the funnel symbol.
1. In the **Inquiry** dialog box, on the **Joins** tab, highlight the entity name, and then select **Add table join**.
1. Select **Layout sizes (Name)**, select **Select** to confirm, and then select **OK**.
1. For the **POS screen layout image zones** entity, in the **Filter** column, select the funnel symbol.
1. In the **Inquiry** dialog box, on the **Joins** tab, highlight the entity name, and then select **Add table join**.
1. Select **Layout sizes (Name)**, select **Select** to confirm, and then select **OK**.
1. For the **RetailTillLayoutConfigurationEntity** entity, in the **Filter** column, select the funnel symbol.
1. In the **Inquiry** dialog box, on the **Joins** tab, highlight the entity name, and then select **Add table join**.
1. Select **Layout sizes (Name)**, select **Select** to confirm, and then select **OK**.
1. For each of the three entity rows, follow these steps:

    1. In the **Filter** column, select the funnel symbol.
    1. Select **Add**, and then, in the **Table** column dropdown list, select **Layout sizes**.
    1. In the **Field** column dropdown list, select **Name**. 
    1. On the **Criteria** column, enter the layout size in the format **\<*image width in pixels*\>x\<*image height in pixels*\> – Full** (for example, **1536x864 – Full**). The system then exports only this layout size.

### Export and download package

After all the entities are updated with correct filters, on the Action Pane, select **Export**. This action initiates a batch job.

After the batch job is completed, verify that the **Execution status** value for all the entities is **Successful**. Then select **Download package** to download the XML package to your local machine. Verify that the package contents from the download location are correct.

## Import screen layout data to a new environment

To import the screen layout data that you exported to a new environment, follow these steps.

1. In headquarters for the new environment, go to **Data management** \> **Import**.
1. In the **Group name** field, enter a name (for example, **Import POS layouts**).
1. Under **Selected entities**, select **Add file**.
1. In the **Add file** dialog box, in the **Source data format** dropdown list, select **Package**.
1. Under **Upload import files**, select **Upload and add**, find and select the package that you exported, and then select **Open**.
1. In the **Add file** dialog box, select **Close**.
1. After the entities are loaded, on the Action Pane, select **Entity sequence**.
1. Select **Auto sequence** to sequence the entities in a way that considers the dependencies, and then select **OK**.
1. On the Action Pane, select **Import**.
1. Verify the **Execution summary** value, and confirm that the status for all the entities is **Succeeded**.
1. Verify that the screen layouts, button grids, and visual profiles are updated.
1. After you assign the layouts to the store, register, or user level, run scheduler jobs.
1. Sign in to the POS, and verify the layouts.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
