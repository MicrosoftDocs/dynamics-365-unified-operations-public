---
title: Prepare application metadata to be used in RCS
description: This article describes how to create a new reporting configuration that contains application metadata.
author: kfend
ms.date: 06/28/2019
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2019-06-28
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: 
---
# Prepare application metadata to be used in RCS
[!include [banner](../../includes/banner.md)]

The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can create a new Electronic reporting (ER) configuration that contains application metadata for designing ER model mapping configurations in Regulatory configuration service (RCS). This configuration will be used for designing a sample ER model mapping configuration to access foreign trade transactions. In this example, you will create a configuration for sample company, Litware, Inc. These steps can be performed in any company. To complete these steps, you must first complete the steps in the article, [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md).

## Prerequisites
1.    Go to **Organization administration** > **Workspaces** > **Electronic reporting**. 
2.    Make sure that the configuration provider for the sample company, Litware, Inc., is available and marked as **Active**. If you don't see this configuration provider, complete the steps in the procedure [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md). 
3.    Click **Metadata configurations**. 
4.    Assume that RCS will be used to design an ER solution for a Finance and Operation application that will generate electronic documents that contain information from foreign trade business domain. To specify the mapping between ER data model and sources of required data, in RCS we need to have access to metadata of the Finance and Operation application. Therefore, as part of designing ER solution we configure a new ER metadata configuration containing all metadata that is currently required for generation ER reports for selected business domain. 

## Add metadata configuration 
1.    Click **Create configuration** to open the drop dialog. 
2.    In the **Name** field, type 'Foreign trade metadata'. 
3.    Click **Create configuration**. 
4.    Click **Designer**. 
5.    Click **Add**. 
  
> [!NOTE]
> You can select all metadata for the entire application or selected models or selected modules. Be aware that in this case the following metadata will be automatically added: tables of records, enumerations, and extended data types. When additional types of metadata are needed, they must be added manually. 
 
We have some foreign trade transactions related metadata by selecting metadata items manually. 
  
6.    Click **Add data source**. 
7.    Click **Table records**. 
8.    Use the Quick Filter to filter on the **Name** field with a value of 'Intrastat'. 
9.    Select the **Intrastat** table record. 
10.    Click **OK**.
  
We added metadata information about the Intrastat table of records. 
  
11.    In the tree, expand **Table records Intrastat**\>**Relations**. 
12.    In the tree, select **Table records Intrastat**\>**Relations\IntrastatCommodity (Table records EcoResCategory)**.     
13.    Click **Add metadata**. 
  
> [!NOTE]
> Metadata about required relations for selected table of records must be added manually. 
  
16.    Click **Add data source**. 
17.    Click **Enumeration**. 
18.    Use the Quick Filter to filter on the **Name** field with a value of 'IntrastatDirection'. 
19.    Select the **IntrastatDirection enumeration** record. 
20.    Click **OK**. 
21.    Click **Save**.  
22.    Close the page. 
  
## Complete the draft version of metadata configuration
1.    Click **Change status**. 
2.    Click **Complete**. 
3.    Click **OK**. 
4.    Select the completed version **1**. 
  
## Export the completed version of metadata configuration from application as XML file
1.    Click **Exchange**. 
2.    Click **Export as XML file**. 
3.    Click **OK**. 
    
The created ER metadata configuration has been saved as XML file that can be imported to RCS and used as the source of information about metadata for the foreign trade business domain. Based on this information, we can specify the mapping between application metadata and ER data model.


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
