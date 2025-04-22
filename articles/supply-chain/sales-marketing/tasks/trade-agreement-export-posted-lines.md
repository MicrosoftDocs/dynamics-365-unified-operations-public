---
title: How to export Posted Trade Agreement Lines
description: Learn step-by-step instructions on how to export posted tradeagreement lines.
author: Sumit Gaur
ms.author: sugaur
ms.reviewer: kamaybac
ms.search.form: TradeNonStockedConversion, TradeNonStockedConversionChangeWizard, TradeNonStockedConversionCheckWorksheet, TradeNonStockedConversionWizard, TradeNonStockedRegister
ms.topic: how-to
ms.date: 04/22/2025
ms.custom: 
  - bap-template
---
# How to export Posted Trade Agreement Lines

This article provides step-by-step instructions on how to export posted tradeagreement lines. Microsoft Dynamics 365 standard data entities do not support the direct export of posted trade agreement lines. By following these steps, you can convert the posted lines to unposted ones, making them exportable.


## Convert and export posted trade agreement lines

Follow these steps to convert posted trade agreement lines into unposted lines and export them:
1. **Access active trade agreement lines:**
   
   For Purchase trade agreements
    1. Navigate Accounts Payable -> Vendors -> All vendors
    2. Select Procurement -> Agreements -> Trade agreements
   
   For Sales trade agreements
    1. Account receivable -> Customers -> All customers 
    2. Sell -> Trade agreements -> Agreement 
3. **Select and edit the lines:**
    - Select all the lines or a subset of lines you want to export.
    - Click on the **Edit selected lines** button in the ribbon.
    ![image](https://github.com/user-attachments/assets/5845e27f-4654-4f43-8be5-9164ee168320)

4. **Assign to a journal:**
    - In the slider dialog that appears, select a journal name.
    - Click **OK**.

    This action converts the active price trade agreement lines into open trade agreement lines, which are now exportable.
![image](https://github.com/user-attachments/assets/aefa21fe-071f-47bc-81ce-6c3ac8d38078)

5. **Export the open trade agreement lines:**
      
   Once the lines have been converted to open trade agreements, you can proceed to export them. You can use the standard data management features of Supply Chain Management to export data from this entity to any supported data format, such as CSV or Excel format.
   
   1. Go to **System administration \> Workspaces \> Data management**.
   1. In the **Import / Export** section, select the **Export** tile.
   1. On the **Export** page, enter a **Group name** for the job.
   1. On the **Selected entities** FastTab, select **Add entity**.
   1. In the **Add entity** drop-down dialog, set the following fields:
   
       - **Entity name** – Select *Open purchase price journal lines V2* or *Open sales price journal lines V2*
       - **Target data format** – Select the format to export data to.
   ![image](https://github.com/user-attachments/assets/c703927f-a80a-4331-b960-73cb5efa8958)
   1. Select **Add** to add the new row, and then select **Close** to close the dialog box.
   1. Usually, you'll export one report at a time. To export a single report, select the button in the **Filter** column for the row that you just added to **Selected entities** FastTab. Then use the query designer to set up the following filter:
       - **Table** – Select *Open purchase price journal lines V2* or *Open sales price journal lines V2*
       - **Field** – Select *Execution name*.
       - **Criteria** – Enter the name of the report that you want to export.
   
   1. On the Action Pane, select **Save**.
   1. On the Action Pane, open the **Export options** tab and select **Export now**.
   1. The **Execution summary** page opens. Here you can view the status of your export job and a list of the entities that were exported. In the **Entity processing status** section, select the *Open purchase price journal lines V2* or *Open sales price journal lines V2* entity in the list, and then select **Download file** to download the data that was exported from that entity.
   
   For more information about how to use data management to export data, see [Data import and export jobs overview](../../../fin-ops-core/fin-ops/data-entities/data-import-export-job.md)
   


## Clean up resources

After exporting the data, ensure that any temporary journal entries used for the conversion process are deleted or archived to maintain data integrity and avoid clutter in your system.
