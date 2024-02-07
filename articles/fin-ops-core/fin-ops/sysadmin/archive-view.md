---
title: Viewing archived data in Dataverse long term retention  
description: This article describes how to Viewing archived data in Dataverse long term retention  
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 2/06/2024
ms.custom:

---
# Viewing archived data in Dataverse long term retention  

Microsoft Fabric for viewing data 

You can view the live(active) and archived (inactive long term retained) F&O application data using Microsoft Fabric. To do this, you will require to link your Dataverse environment to Fabric.  

 

 
Important: If Link to Fabric setup is not working even with the steps followed in the public document, make sure to confirm that Microsoft Fabric is enabled. If not enabled, using the Azure Global Admin user account go to https://app.fabric.microsoft.com/ and follow the 5 steps highlighted below. 

A screenshot of a computer

Description automatically generated 

 

 

Note: For accessing DV managed data lake data with Fabric, if you do not have a Fabric subscription, you can use Fabric trial. Post trial period, you will require to have Fabric capacity (F SKUs) or Premium per capacity PowerBI SKU for users. 

 

Viewing archived data in Dataverse managed data lake 

After the archival job is completed, go to the Power Apps maker portal and select Azure Synapse Link -> Microsoft one Lake. Select “View in Microsoft Fabric”. 

 

 

A screenshot of a computer

Description automatically generated  

 

The data in the Dataverse managed data lake is available in Dataverse tables prefixed by “mserp_”. The Dataverse table column msft_datastate, available in the Dataverse tables prefixed by “mserp”_ can be used to filter the data with the SQL WHERE clause: 

Inactive(archived) application data: WHERE msft_datastate=1 

Active (live) application data: WHERE msft_datastate=0 

 

More information: View Dataverse long term retained data with Microsoft Fabric 

Sample query with Finance GL table below 

 

 

Access archived data in Dataverse long term retention – using a model driven Power App that uses Dataverse Advanced Find or build canvas Power apps. View limitations with these options.  

 

