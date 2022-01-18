---
# required metadata

title: Configure SharePoint channel
description: This topic provides description of the configuring SharePoint channel for processing incoming electronic invoices.
author: dkalyuzh
ms.date: 12/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
---

[!include [banner](../includes/banner.md)]


As the prerequisite of the configuring the SharePoint channel for incoming documents processing, you must complete the steps described in the article: [Configure SharePoint connection](e-inv_tut-setup-electronic-invoicing_azure_configure-sharepoint.md). 

The channel allows you to import electronic vendor invoices from files stored in your SharePoint folders.

 1. In SharePoint site, create folders to operate with:
   - Main folder - This is the folder from which service will process file
   - Archive folder - Processed files will be stored in this folder
   - Error folder - If the processing resulted with failure, system will move the file to this folder
 2. In RCS, select the Electronic invoicing feature that you created. Make sure you selected the Version with status Draft.
 3. On **Setups** tab, in the grid, select **Add**. 
 4. Select the **Custom setup** radio button, and in the **Setup type** section, select the **Data channel** radio button.
 5. In the **Select data channel** field. select **SharePoint folder** and then select **Create**.
 7. Locate cursor on the create line and select **Edit**.
 8. On the **Data channel** tab, in the **Parameters** field group, configure required parameters:
    |**Name** |**Description** |**Details** |
    |----------------|----------------------------------|-----------------------------------------------------|
    |Data channel|Data channel identifier|Enter unique name of Data channel up to 10 symbols. It will be referenced to in Applicability rules, and in connected applications during communication process.|
    |SharePoint address|SharePoint web URL|Example: `<domain>.sharepoint.com`|
    |Application Id|Application Id|Enter the name of the Key vault secret that contains the ID of the SharePoint user account. This secret must be created in Azure key vault and setup in your service environment. This is ***Application (client) ID*** in [Configure SharePoint connection](e-inv_tut-setup-electronic-invoicing_azure_configure-sharepoint.md). |
    |Application secret|Application client secret value|Enter the name of the Key vault secret that contains the password of the SharePoint user account. This is ***App Registration secret*** in [Configure SharePoint connection](e-inv_tut-setup-electronic-invoicing_azure_configure-sharepoint.md).|
    |Site name|SharePoint site name|Site name|
    |Document library name|SharePoint document library name|Library name|
    |Timeout|It limits the max time to wait for a response in milliseconds|Default is 10 sec|
    |Main folder|File import source|This is the folder from which service will process file|
    |Archive folder|File archive folder|Processed files will be stored in this folder.|
    |Error folder|File error folder|If the processing resulted with failure, system will move the file to this folder.|
    |Max file size|Max size of a single file to process in bytes|Default value is 20000000. You can limit the size.|
    |Max files number|Max amount of files to process for a single action|Set 0 if you don't limit this number.|
    |File filter|String to filter by file name. Simple mask of type `*smth*.ext` is supported where `"*"` means 0 or more of any symbol|Optional. Example: `*.pdf` to configure the channel for reading PDF files|
    |Custom file name|Custom file name from the client||
    
 9. On the **Applicability rules** tab, review and update the criteria as necessary. The **Channel** field must be equal to the **Data channel** provided above. 
 10. Select **Save** and close the page.
