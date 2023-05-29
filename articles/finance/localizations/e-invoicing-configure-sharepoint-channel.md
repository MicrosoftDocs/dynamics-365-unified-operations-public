---
title: Configure a SharePoint channel
description: This article explains how to configure a Microsoft SharePoint channel to process incoming electronic invoices.
author: gionoder
ms.date: 02/09/2022
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: gionoder
ms.search.validFrom: 2020-07-08
ms.dyn365.ops.version: AX 10.0.12
ms.collection: get-started
ms.assetid: 
ms.search.form: 
---

# Configure a SharePoint channel

[!include [banner](../includes/banner.md)]

As a prerequisite to configuring a Microsoft SharePoint channel to process incoming documents, complete the steps described that are described in [Configure a SharePoint connection](e-invoicing-create-sharepoint-connection.md).

You can then use the SharePoint channel to import electronic vendor invoices from files that are stored in your SharePoint folders.

1. On your SharePoint site, create the following folders:

    - **Main folder** – The folder that the service will process files from.
    - **Archive folder** – The folder where processed files will be stored.
    - **Error folder** – The folder that the system will move files to if the processing fails.

2. In Regulatory Configuration Service (RCS), select the Electronic invoicing feature that you created. Make sure that you select the version that has a status of **Draft**.
3. On **Setups** tab, select **Add**.
4. In the **Create feature setup** drop-down dialog box, in the **New** field group, select the **Custom setup** option.
5. In the **Setup type** field group, select the **Data channel** option.
6. In the **Select data channel** field, select **SharePoint folder**.
7. Select **Create**.
8. Select the line that you created, and then select **Edit**.
9. On the **Data channel** tab, in the **Parameters** section, set the following required fields.

    | Field                 | Description |
    |-----------------------|-------------|
    | Data channel          | Enter a unique name to identify the data channel. The name can have a maximum of 10 characters. It will be referenced in the applicability rules and in connected applications during the communication process. |
    | SharePoint address    | Enter the SharePoint URL. For example, enter `<domain>.sharepoint.com`. |
    | Application Id        | Enter the name of the Azure Key Vault secret that contains the ID of the SharePoint user account. This secret must be created in Key Vault and set up in your service environment. The value is the **Application (client) ID** value from [Configure SharePoint connection](e-invoicing-create-sharepoint-connection.md). |
    | Application secret    | Enter the name of the Key Vault secret that contains the password of the SharePoint user account. The value is the **App Registration secret** value from [Configure SharePoint connection](e-invoicing-create-sharepoint-connection.md). |
    | Site name             | Enter the name of the SharePoint site. |
    | Document library name | Enter the name of the SharePoint document library. |
    | Timeout               | Enter the maximum time, in milliseconds (ms), that the system should wait for a response. The default value is 10,000 ms (10 seconds). |
    | Main folder           | Specify the file import source, or the folder that the service should process files from. |
    | Archive folder        | Specify the folder where processed files should be stored. |
    | Error folder          | Specify the folder that the system should move files to if the processing fails. |
    | Max file size         | Enter the maximum size, in bytes, of a single file that is processed. The default value is 20,000,000 bytes. |
    | Max files number      | Enter the maximum number of files to process for a single action. If you don't want to limit the number of files, set the value to **0** (zero). |
    | File filter           | Enter a string to filter by file name. This field is optional. A simple mask such as **\*smth\*.ext** is supported, where each asterisk (\*) represents zero or more occurrences of any character. For example, enter **\*.pdf** to configure the channel to read PDF files. |
    | Custom file name      | Enter the custom file name from the client. |

10. On the **Applicability rules** tab, review and update the criteria as required. The value of the **Channel** field must equal the value that you entered in the **Data channel** field in the previous step.
11. Select **Save**, and close the page.
