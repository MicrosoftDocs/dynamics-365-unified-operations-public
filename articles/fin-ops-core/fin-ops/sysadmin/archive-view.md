---
title: View archived data in Dataverse long term retention (preview)  
description: This article describes how to view archived data in Dataverse long term retention.  
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 2/06/2024
ms.custom:

---
# View archived data in Dataverse long term retention 

[!INCLUDE [preview-banner](../../../supply-chain/includes/preview-banner.md)]

This article describes how to view archived data in Dataverse long term retention. 

## Microsoft Fabric for viewing data 

You can view the live(active) and archived (inactive long term retained) Dynamics 365 Finance application data using Microsoft Fabric. You're required to link your Dataverse environment to Fabric.  

If the link to Fabric setup isn't working, follow these steps: [Link to Microsoft Fabric](/power-apps/maker/data-platform/azure-synapse-link-view-in-fabric#link-to-microsoft-fabric).  
Confirm that Microsoft Fabric is enabled. If Microsoft Fabric isn't enabled, go to https://app.fabric.microsoft.com/. 

>[!Note]
>If you don't have a Fabric subscription, you can use Fabric trial to access a Dataverse managed data lake data. After the trial period expires, you'll be required to have Fabric capacity or Premium per capacity PowerBI SKU for users. 

### Viewing archived data in Dataverse managed data lake 

To view the archived data in Dataverse, follow these steps:
1. After the archival job completes, go to the Power Apps maker portal.
2. Select **Azure synapse** > **Microsoft one Lake**.
3. Select **View in Microsoft Fabric**. 

The data in the Dataverse managed data lake is available in Dataverse tables prefixed by **mserp_**. The Dataverse table column msft_datastate, available in the Dataverse tables prefixed by **mserp**_ can be used to filter the data with the SQL WHERE clause: 
 - Inactive(archived) application data: WHERE msft_datastate=1
 - Active (live) application data: WHERE msft_datastate=0 


You can also access archived data using a model driven Power App that uses Dataverse Advanced Find or build canvas Power Apps. 
To view limitations with these options, see [Viewing archive data limitations](/power-apps/maker/data-platform/data-retention-view#limitations-for-retrieval-of-retained-data).  

 

