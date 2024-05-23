---
title: How to move screen point of sale layouts to a new environment
description: This article describes how to move screen layouts to a new environment in the Microsoft Dynamics 365 Commerce.
ms.author: anvenkat 
ms.topic: article 
ms.date: 05/23/2024
ms.custom: 
  - bap-template
ms.reviewer:
---

# How to move POS screenlayouts to a new environment
The following document describes the procedure to export and import POS screen layouts to a new enviroment.

## Export Layout related data
- From the HQ enviroment you need to export, go to **Data management** > **Framework parameters** and select **Entity settings**
- Under **Advanced entity configuration settings** select **Refresh entity list**. You will see a message **The refresh entity list job is added to the queue** as an information message
   on the top of the screen.
- Go to **Batch jobs** > **System Administration** > **Inquiries** and verify that the **Refresh entity list job was successfully completed**
- Go to **Data management** > **Export** and create a new record with group name  **Export POS layouts**.
- Under **Selected entities** select **Add multiple** .
- On the pop up screen, select target data format as **XML-Element**, ensure to select **skip staging** to **No**
- Filter **Entity** columnand select below list of entities and **add selected**. You will then see all the entities added.
    - **Layout sizes** (include this only when you are exporting new layout sizes that dont exist in the new enviroment.)
    - **RetailTillLayoutConfigurationEntity**
    - **POS button grid**
    - **POS button grid buttons**
    - **POs layout images**
    - **POS screen layouts**
    - **POS screen layout button grid zones**
    - **POS screen layout image zones**
    - **POS visual profiles**
- Use **filter** column to only select specific layouts for export. Example **SCO**. 
- select the following entities and apply the filter as follows. In the example we are trying to filter all the screenlayouts and button grids that begin with **SCO**
    - **RetailTillLayoutConfigurationEntity** - select **filter** and enter **SCO** against **screen layout ID**
    - **POS button grid** - select **filter** and enter **SCO** against **Button grid ID** 
    - **POS button grid buttons** - select **filter** and enter **SCO** against **Button grid ID**
    - **POS screen layouts** - select **filter** and enter **SCO** against **Screen layout ID**
    - **POS visual profiles** - select **filter** and enter **SCO** against **Profile number**
**Note** - Filtering by specific values will mitigate the risk of accidental override in the import environments. 
- Additionally if you want to filter specific range of images select the **Image ID** in **POS layout images** table and specify the image range example **6001..6019**.
   This selection will export all images from 6001 to 6019.

### Adding related tables
If additional filters are needed you can also add related tables . Example Add layout sizes to export only a particular size or sizes from selected list of layouts.
To do this you would need to add Layout size in the entity through a table join.
- Select **POS screen layout button grid zones** , **POS screen layout image zones** and **Retailtilllayoutconfigurationentity** one at a time.
- Select **filter** on the row and select **joins** tab
- Highlight the entity and select **+Add table join**
- Select **Layout sizes (Name)**
- Select **Select** to confirm and select **OK**
- Repeat this for the other 2 entities.
- Go to each of the 3 entities , select **filter**
- Then **+Add** and select from drop down **Layout sizes** on the table column.
- Select **Name** on the field column and input the layout size in the criteria (Example **1536*864-Full**). This will only export this layout size.

  ### Export and download package
  Once all of the entities are updated with right filters, you can select **export** from the top menu bar. This will initiate a batch job.
  Once the batch job is complete, verify the status of all the entities which should be **successful**
  Now select **download package** to download the xml package on to your machine. Verify the package contens from the download location.

  

  


  

  
  

    

    

    
    
    
