---
title: Archive sales orders in Dynamics 365 finance and operations with Dataverse (preview) 
description: This article explains how to create a data archival job for sales orders.   
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 2/09/2024
ms.custom:

---

# Archive sales orders in Dynamics 365 finance and operations with Dataverse (preview) 

[!INCLUDE [preview-banner](../../../supply-chain/includes/preview-banner.md)]

This article explains how to create a data archival job for sales orders.  

Important 

Sales orders can be archived only if all the following conditions are met:  

The sales orders required to be archived are fully invoiced.  
The sales orders should not be part of an Intercompany orders chain.  


Install solution in your Power platform  

Refer to Setup and Management for details.   


Turn on the features in your Dynamics 365 Supply Chain Management  
The Archive with Dataverse long term retention feature should be enabled.  

Refer to Setup and Management for details.  

## Schedule long term retention job  

Go to System administration -> Archive with Dataverse long term retention workspace and select Sales orders scenario.  

Select “New long term retention” to open the wizard to schedule a new Sales order archival job with Dataverse long term retention.  

Enter job name and click on Next button.  


Select the date of the oldest sales order (from date) required to be archived. Select the date of the newest sales orders(To date) required to be archived. Select the legal entity (company) that for the sales
orders to be archived. Click on Next Button.   

  

There are two types of scheduling that are supported:  

Single Run: long term retention and saving to history will run continuously until both are completed. Data is always archived in long term retention in Dataverse, followed by save to history tables.  



Daily during allotted time: In this scheduling option long term retention to Dataverse will run continuously until completed. The Save to History process will run only during the start and stop archiving time
indicated.  

Confirm the details on the last step of the wizard and click Finish to schedule the Sales orders archive, with Dataverse long term retention, job for the selected time interval and company.   
The archive jobs will be visible in the dashboard.  


### View long term retention job status  

Select “View progress” on the archival job dashboard to see the details of the job status.   


### Restore long term retention job  

Archived Sales orders from a completed archive job can be optionally restored back to live tables from the history tables. On completion of restore job, the retained status is reset in Dataverse managed data lake.
To restore, click on the Restore on the toolbar.   

In the dialog, select period and company with job status completed, choose start date and time of job execution and click Ok.  

### View historical data  

The Archive with Dataverse long term retention workspace shows your full archiving history. Each row in the grid shows information such as the date when the archive was created, the user who created it, and its
status. Follow these steps to view details about a selected archive.  

To view details about the sales orders that are included in an archive job, select the job, and then select View history data on the toolbar.  

 

The Archived sales orders page lists every sales order that's included in the archive job. To view an order, including its header and all its order lines, select it in the grid, and then, on the Action Pane, 
select Archived sales order details. From the order details, you can view more related information about the order. On the Action Pane, select Inquiry, and then, on the menu, select the type of records that you 
want to inspect Sent sales quotations, Sales order confirmations, picking list, Packing slip or Invoice journal.  
