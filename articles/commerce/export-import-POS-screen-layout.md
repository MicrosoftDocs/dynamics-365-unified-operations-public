---
title: Export point of sale screen layouts for import to a new environment
description: This article describes how to export point of sale screen layouts for import to a new environment in Microsoft Dynamics 365 Commerce.
author: anush6121
ms.author: anvenkat 
ms.topic: article 
ms.date: 05/29/2024
ms.custom: 
  - bap-template
ms.reviewer: v-chrgriffin
ms.search.validFrom: 2024-01-20
---

# Export POS screen layouts for import to a new environment

[!include [banner](includes/banner.md)]

This article describes how to export point of sale screen (POS) layouts for import to a new environment in Microsoft Dynamics 365 Commerce.

## Export screen layout data

To export screen layout data from an environment, follow these steps.

1. In the Commerce headquarters environment from which you want to export data, go to **Data management \> Framework parameters**.
1. Select **Entity settings**.
1. Under **Advanced entity configuration settings**, select **Refresh entity list**. The message "The refresh entity list job is added to the queue" appears at the top of the screen.
1. Go to **Batch jobs \> System Administration \> Inquiries** and verify that the refresh entity list job has completed successfully.
  
    ![batchjob.](media/batchjobentity.png)
  
1. Go to **Data management \> Export** and under **Group name**, enter a name for the export (for example, "Export POS layouts").
1. Under **Selected entities** select **+Add multiple**.
  
    ![selecting entities.](media/selectentities.png)
  
1. In the **Add multiple** dialog, in the **Target data format** drop-down list, select **XML-Element**.
1. Set the **Skip staging** option to **No**.
1. For each of the following entities, filter for the entity in the **Entities** box, select the entity result in the **Entity** column, and select **Add selected**.
    - **Layout sizes** (Include this entity only when you're exporting new layout sizes that don't exist in the new environment.)
    - **RetailTillLayoutConfigurationEntity**
    - **POS button grid**
    - **POS button grid buttons**
    - **POS layout images**
    - **POS screen layouts**
    - **POS screen layout button grid zones**
    - **POS screen layout image zones**
    - **POS visual profiles**
1. Select **Close** to close the dialog.     
    ![POS export entities.](media/POSexportedentities.png)    
1. For the **RetailTillLayoutConfigurationEntity** entity, in the **Filter** column, select the funnel symbol.
1. In the **Inquiry** dialog, for the entity where the **Field** value is **Screen layout ID**, in the **Criteria** column, enter criteria text (for example, "SCO"), and then select **OK**. 
1. For the **POS button grid** entity, in the **Filter** column, select the funnel symbol.
1. In the **Inquiry** dialog, for the entity where the **Field** value is **Button grid ID**, in the **Criteria** column, enter criteria text (for example, "SCO"), and then select **OK**.
1. For the **POS button grid buttons** entity, in the **Filter** column, select the funnel symbol.
1. In the **Inquiry** dialog, for the entity where the **Field** value is **Button grid ID**, in the **Criteria** column, enter criteria text (for example, "SCO"), and then select **OK**.
1. For the **POS screen layouts** entity, in the **Filter** column, select the funnel symbol.
1. In the **Inquiry** dialog, for the entity where the **Field** value is **Screen layout ID**, in the **Criteria** column, enter criteria text (for example, "SCO"), and then select **OK**.
1. For the **POS visual profiles** entity, in the **Filter** column, select the funnel symbol.
1. In the **Inquiry** dialog, for the entity where the **Field** value is **Profile number**, in the **Criteria** column, enter criteria text (for example, "SCO"), and then select **OK**.

    > [!NOTE]
    > Filtering by specific criteria mitigates the risk of accidental override in the import environment.

    ![Buttongridbutton.](media/buttongridbuttons.png)
    ![Buttongridfilter.](media/buttongridfilter.png)
    ![retailtilllayout.](media/retailtilllayout.png)
    ![screenlayoutfilter.](media/screenlayoutfilter.png)
    ![visualprofile.](media/visualprofilefilter.png)

1. If you want to filter for a specific range of images, follow these steps:
    1. For the **POS layout images** entity, in the **Filter** column, select the funnel symbol.
    1. In the **Inquiry** dialog, for the entity where the **Field** value is **Image ID**, in the **Criteria** column, enter a number range for the image IDs in the format \<Image ID start\>..\<Image ID end\> (for example "60000..60026"), and then select **OK**. For this example, the selection exports all images with image IDs from 60000 to 60026.

    ![Screenlayout image filter.](media/screenlayoutimagefilter.png)

### Add related tables

If you require additional filters, you can add related tables. For example, you can add the **Layout sizes** table to export only a specific size or sizes from the selected list of layouts. You add this table to the entity using a table join.

To add the **Layout sizes** table, follow these steps.

1. Select the rows for **POS screen layout button grid zones**, **POS screen layout image zones**, and **RetailTillLayoutConfigurationEntity**.
1. For the **POS screen layout button grid zones** entity, in the **Filter** column, select the funnel symbol.
1. In the **Inquiry** dialog, select the **Joins** tab.
1. Highlight the entity name, and then select **+Add table join**.
1. Select **Layout sizes (Name)**, and select **Select** to confirm, and then and select **OK**
1. For the **POS screen layout image zones** entity, in the **Filter** column, select the funnel symbol.
1. In the **Inquiry** dialog, select the **Joins** tab.
1. Highlight the entity name, and then select **+Add table join**.
1. Select **Layout sizes (Name)**, and select **Select** to confirm, and then and select **OK**
1. For the **RetailTillLayoutConfigurationEntity** entity, in the **Filter** column, select the funnel symbol.
1. In the **Inquiry** dialog, select the **Joins** tab.
1. Highlight the entity name, and then select **+Add table join**.
1. Select **Layout sizes (Name)**, and select **Select** to confirm, and then and select **OK**
1. For each of the three entity rows, do the following:
    1. In the **Filter** column, select the funnel symbol.
    1. Select **+Add**, and on the **Table** column drop-down list, select **Layout sizes**.
    1. On the **Field** column drop-down list, select **Name**. 
    1. On the **Criteria** column, enter the layout size in the format \<image width in pixels\>\*\<image height in pixels\>-Full (for example, "1536*864-Full"). The system then only exports this layout size.

  ![Filter layout size.](media/filterlayoutsizes.png)

### Export and download package

Once all of the entities are updated with right filters, on the Action Pane, select **Export**. This action initiates a batch job.

![export.](media/export.png)

Once the batch job is completes, verify that the **Execution status** for all the entities is **Successful**. Next, select **Download package** to download the XML package to your local machine. Verify that the package contents from the download location are correct.
  
![Download package.](media/download-package.png)

## Import screen layout data to a new environment

To import the screen layout data you exported to a new environment, follow these steps.

1. In headquarters for the new environment, go to **Data management \> Import**.
1. For **Group name**, enter a name (for example, "Import POS layouts").
1. Under **Selected entities**, select **+Add file**.
1. In the **Add file** dialog, in the **Source data format** drop-down list, select **Package**.
1. Under **UPLOAD IMPORT FILES**, select **Upload and add**, find and select the package that you exported, and select **Open**.
1. In the **Add file** dialog, select **Close**.
   
    ![Import.](media/POSimport.png)
   
1. After the entities are loaded, on the Action Pane, select **Entity sequence**.
1. Select **Auto sequence** to sequence the entities considering the dependencies, and then select **OK**.

    ![autosequence.](media/autosequence.png)
   
1. On the Action Pane, select **Import**.
1. Verify the **Execution summary** and confirm that the status for all entities is **Succeeded**.
1. Verify that the screen layouts, button grids, and visual profiles are updated.
1. Run scheduler jobs after assigning the layouts to the store, register, or user levels.
1. Sign in to the POS and verify the layouts.


[!INCLUDE[footer-include](../includes/footer-banner.md)]

    

    
    
    
