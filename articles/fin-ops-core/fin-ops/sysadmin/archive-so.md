---
title: Archive sales orders in Dynamics 365 Supply Chain Management with Dataverse (preview) 
description: This article explains how to create a data archival job for sales orders.   
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 2/09/2024
ms.custom:

---

# Archive sales orders in Dynamics 365 Supply Chain Management with Dataverse (preview) 

[!INCLUDE [preview-banner](../../../supply-chain/includes/preview-banner.md)]

This article explains how to create a data archival job for sales orders.  

## Prerequisites

The following prerequisites must be met before sales orders can be archived:
 - The sales orders are fully invoiced.
 - The sales orders shouldn't be part of an intercompany order chain.  


## Install solution in Power platform  
To install the solution in Power platform, see [Set up and management](archive-setup.md).

### Turn on the features in your Dynamics 365 Supply Chain Management  
The **Archive with Dataverse long term retention** feature should be enabled.  

### Schedule long term retention job  

To schedule a long term retention job, follow these steps:
1. In Dynamics 365 Supply Chain Management, go to **System administration** > **Archive with Dataverse long term retention workspace**
2. Select **Sales orders scenario**.
3. Select **New long term retention**. This opens a wizard to schedule a new **Sales order archival job with Dataverse long term retention**.
4. Enter job name and click **Next**.
5. Select the date of the oldest sales order (from date) required to be archived. Select the date of the newest sales orders (To date) required to be archived.
6. Select the legal entity (company) that for the sales orders to be archived.
7. Click **Next**.   

Two types of scheduling are supported:  
 - **Single run** - Long term retention and saving to history jobs run continuously until both are completed. Data is always archived in long term retention in Dataverse, followed by save to history tables.
 - **Daily during allotted time** - Long term retention to Dataverse runs continuously until completed. The **Save to history** process only runs during the start and stop archiving time indicated.  

8. Confirm the details on the last step of the wizard. Click **Finish** to schedule the Sales orders archive with Dataverse long term retention job for the selected time interval and company.   
The archive jobs will be visible in the dashboard.  


### View long term retention job status  
Select **View progress** on the archival job dashboard to view job status details.   


### Restore long term retention job  

Archived Sales orders from a completed archive job can be optionally restored back to live tables from the history tables. After the restore job is complete, the retained status is reset in Dataverse managed data lake. 
1. To restore, click **Restore** on the toolbar.
2. In the dialog, select the period and company with job status completed.
3. Select the start date and time of job execution.
4. Click **Ok**.  

### View historical data  

The **Archive with Dataverse long term retention** workspace displays full archiving history. Each row in the grid shows information such as the date when the archive was created, the user who created it, and its
status. 

To view details about a selected archive, follow these steps:
1. Select the job and select **View history data** on the toolbar.  
The **Archived sales orders** page displays every sales order that's included in the archive job. 
2. To view an order, including its header and all its order lines, select it in the grid.
3. On the Action Pane, select **Archived sales order details**. From the order details, you can view more related information about the order.
4. Select **Inquiry**.
5. On the menu, select the type of records to view.   
