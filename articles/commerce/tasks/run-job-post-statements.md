--- 
title: Configure and run job to post statements
description: Learn how to configure and run a recurrent batch job to post statements for a selected store or group of stores in Microsoft Dynamics 365 Commerce. 
author: josaw1
ms.date: 02/11/2026
ms.topic: how-to 
ms.search.form: RetailChannelOperationsWorkspace, RetailOperatingUnitPicker, SysRecurrence   
ms.author: josaw 
ms.reviewer: v-griffinc
ms.search.region: Global
ms.search.validFrom: 2016-06-30 
ms.custom: 
  - bap-template
---
# Configure and run job to post statements

[!include [banner](../includes/banner.md)]

Learn how to configure and run a recurring batch job to post statements for a selected store or group of stores in Microsoft Dynamics 365 Commerce.

The following procedure walks through configuring and running a recurring batch job to post statements for a selected store or group of stores. The procedure uses the USRT company in demo data.

To configure and run job to post statements, follow these steps.

1. In Commerce headquarters, go to All workspaces > .. > Store financials.
1. Select **Post statements in batch**.
1. Select an organizational hierarchy. In the organization nodes tree, select either an individual store or a node. Select a node if you want to create the batch job for a group of stores.  
1. Select the arrow to add your selection.  
1. Select the **Run in the background** tab.

    :::image type="content" source="../dev-itpro/media/runbackground.png" alt-text="Screenshot of the Run in the background tab.":::

1. Check or uncheck the **Batch processing** checkbox.

    :::image type="content" source="../dev-itpro/media/batchprocessing.png" alt-text="Screenshot of the Batch Processing and Recurrence settings.":::

1. Select **Recurrence**.
1. In the **Start date** field, enter a date.
1. In the **Start time** field, enter a time. Choose whether you want to end the recurrence after a specific number of runs, at a specific date, or never. Then choose the various options to define how frequently you want the job to run.  
1. Select **OK**.
1. Select **OK**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]