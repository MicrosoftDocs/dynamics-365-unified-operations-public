--- 
# required metadata 
 
title: Configure and run job to calculate statements
description: Learn how to configure and run recurrent batch jobs to create and calculate statements for a selected store or group of stores in Microsoft Dynamics 365 Commerce. 
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
# Configure and run job to calculate statements

[!INCLUDE [banner](../includes/banner.md)]

This article explains how to configure and run recurring batch jobs to create and calculate statements for a selected store or group of stores in Microsoft Dynamics 365 Commerce.

The following procedure walks through configuring and running recurring batch jobs to create and calculate statements for a selected store or group of stores. The procedure uses the USRT company in demo data.

To configure and run a job to calculate statements, follow these steps.

1. In Commerce headquarters, go to All workspaces > Store financials.
1. Select **Calculate statements**.
1. Select either a specific store, or a node if you want to create the batch job for a group of stores.  
1. Select the arrow to add your selection.  
1. Select the **Run in the background** tab.
1. Under **Batch processing**, select **Yes**.
1. Select **Recurrence**.
1. In the **Start date** field, enter a date.
1. In the **Start time** field, enter a time.
1. Select the **No end date** option.
1. In the **PatternUnit** field, enter **Days**.
1. In the **Per** field, enter a number.
1. Select **OK**.
1. Select **OK**.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]