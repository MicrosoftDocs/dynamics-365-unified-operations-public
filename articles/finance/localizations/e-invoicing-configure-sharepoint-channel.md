---
# required metadata

title: Configure SharePoint channel
description: This topic explains how to configure the SharePoint channel for processing incoming electronic invoices.
author: dkalyuzh
ms.date: 02/09/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: ["97423", "intro-internal"]
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.12

---

# Configure SharePoint channel

[!include [banner](../includes/banner.md)]


As a prerequisite to configuring the SharePoint channel for processing incoming documents, complete the steps described in the topic, [Configure SharePoint connection](e-invoicing-create-sharepoint-connection.md). 

You can use the SharePoint channel to import electronic vendor invoices from files stored in your SharePoint folders.

 1. In your SharePoint site, create the follwoing folders:
 
    - Main folder - This is the folder from which the service will process files.
    - Archive folder - Processed files are stored in this folder.
    - Error folder - If the processing fails, the system moves the file to this folder.
 
 2. In RCS, select the Electronic invoicing feature that you created. Make sure you select the version with a status of **Draft**.
 3. On **Setups** tab, in the grid, select **Add**. 
 4. Select **Custom setup** , and in the **Setup type** section, select **Data channel**.
 5. In the **Select data channel** field. select **SharePoint folder**, and then select **Create**.
 7. Focus the cursor on the create line, and then select **Edit**.
 8. On the **Data channel** tab, in the **Parameters** field group, configure the following required parameters.
 
    |**Name** |**Description** |**Details** |
    |----------------|----------------------------------|-----------------------------------------------------|
    |Data channel|Data channel identifier|Enter the unique name of the data channel up to 10 symbols. This name will be referenced in the Applicability rules and in connected applications during the communication process.|
    |SharePoint address|SharePoint web URL|Example: `<domain>.sharepoint.com`|
    |Application Id|Application Id|Enter the name of the Key vault secret that contains the ID of the SharePoint user account. This secret must be created in Azure key vault and set up in your service environment. This is the **Application (client) ID** in the topic, [Configure SharePoint connection](e-invoicing-create-sharepoint-connection.md). |
    |Application secret|Application client secret value|Enter the name of the Key vault secret that contains the password of the SharePoint user account. This is **App Registration secret** in the topic, [Configure SharePoint connection](e-invoicing-create-sharepoint-connection.md).|
    |Site name|SharePoint site name|The site name.|
    |Document library name|SharePoint document library name|The library name.|
    |Timeout|The maximum time to wait for a response in milliseconds.|The default is 10 seconds.|
    |Main folder|File import source|This is the folder from which the service will process the file.|
    |Archive folder|File archive folder|Processed files are stored in this folder.|
    |Error folder|File error folder|If the processing failed, the system moves the file to this folder.|
    |Max file size|Maximum size of a single file to process in bytes|The default value is 20000000. You can limit the size.|
    |Max files number|Maximun amount of files to process for a single action|Set zero (0) if you don't limit this number.|
    |File filter|String to filter by file name. Simple mask of type `*smth*.ext` is supported where `"*"` means 0 or more of any symbol|Optional - Example: `*.pdf` to configure the channel for reading PDF files|
    |Custom file name|Custom file name from the client| &nbsp;|
    
 9. On the **Applicability rules** tab, review and update the criteria as necessary. The **Channel** field must be equal to the **Data channel** provided above. 
 10. Select **Save** and close the page.
