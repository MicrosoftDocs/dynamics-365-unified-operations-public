---
title: Access application metadata by using connected applications
description: The steps in this article explain how a Regulatory configuration service user can design a new Electronic reporting model mapping by using metadata.
author: kfend
ms.date: 06/29/2019
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
# Access application metadata by using connected applications

[!include [banner](../../includes/banner.md)]

The following steps explain how a Regulatory configuration service (RCS) user in the System Administrator or Electronic Reporting Developer role can design a new Electronic reporting (ER) model mapping by using metadata in finance and operations. Application metadata will be accessed online by using the RCS connected application. Sample ER model mapping will be configured to access foreign trade transactions. To complete these steps, in RCS you must first complete the steps in the article, [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md). If you have not completed the steps in the article, [Access application metadata by using ER configuration](access-application-metadata-er-configuration.md), download the [Electronic reporting examples](https://download.microsoft.com/download/0/4/e/04e13839-e423-442b-a6c2-dd35b1045c2d/Dynamics%20365%20for%20Finance%20and%20Operations%208.1%20Electronic%20reporting%20task%20guides.zip) and save the following ER configurations: Foreign trade metadata.xml; Foreign trade model.xml; Foreign trade mapping.xml, and then complete the steps in the procedure.

## Prerequisites
1. Go to **All workspaces** > **Electronic reporting**. 
2. Make sure that the configuration provider for the sample company, Litware, Inc., is available and marked as **Active**. If you don't see this configuration provider, complete the steps in the procedure [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md). 

## Get required ER configurations
1. Click **Reporting configurations**. 
2. If you already completed the steps in the [Access application metadata by using ER configuration](access-application-metadata-er-configuration.md) procedure, you already have all necessary ER configurations (foreign trade metadata, model and mapping configurations) in the current RCS instance. You can skip all the remaining steps of this sub-task. 
3. Click **Exchange**. 
4. Click **Load from XML file**. 
5. Click **Browse** and select the **Foreign trade metadata.xml** file. 
6. Click **OK**. 
7. Click **Exchange**. 
8. Click **Load from XML file**. 
9. Click **Browse** and select the **Foreign trade model.xml** file. 
10. Click **OK**. 
11. Click **Exchange**. 
12. Click **Load from XML file**. 
13. Click **Browse** and select the **Foreign trade mapping.xml** file. 
14. Click **OK**. 

## Register a connected application
1. Close the page. 
2. Close the page. 
3. Go to **All workspaces** > **Electronic reporting**. 
4. Click **Connected applications**. 
5. Make sure that the configured application is Azure based and accessible for the current RCS user. It is also required that the current RCS user has access to the selected application and has been registered as a user of this application playing a role giving them privileges to access application's metadata. 
6. Click **New**. 
7. In the **Name** field, type 'MyConnectedApp'. 
8. In the **Application** field, type 'https:// mycompany.operations.dynamics.com'. 
9. In the **Tenant** field, type 'mycompany.onmicrosoft.com'. 
10. Click **Save**. 
11. When you check connection to configured application, on the **Connect to remote application** page click **Click here to connect to selected remote application** link. 
12. Click **Check connection**. 
13. Click **Close**. 
14. When the connection validation succeeded, version and tenant details will be updated for the configured application in the current grid. 

## Review existing model mapping configuration
1. Close the page. 
2. Click **Reporting configurations**. 
3. In the tree, expand **Foreign trade model**. 
4. In the tree, select **Foreign trade model\Foreign trade mapping**. 
5. Expand the **Prerequisites** section. 

    > [!NOTE]
    > Currently, this mapping refers to the metadata configuration. Application metadata from this configuration will be offered while this model mapping will be designed. 

6. Click **Designer**. 
7. Click **Designer**. 
8. In the tree, select **Dynamics 365 for Operations\Table records**. 
9. Click **Add root**. 
10. In the **Table** field, enter or select a value. 

    > [!NOTE]
    > Currently, this mapping refers to the metadata configuration. Application metadata from this configuration will be offered while this model mapping will be designed. 

11. Click **Cancel**. 
12. Close the page. 
13. Close the page. 

## Assign connected application to model mapping 
1. Click **Edit**. 
2. Select **MyConnectedApp** application. 

    > [!NOTE]
    > Currently, this mapping refers to the metadata of the selected connected application. When the same mapping refers to metadata configuration and connected application at the same time, metadata of the connected application will be used. 

3. Click **Designer**. 
4. Click **Designer**. 
5. In the tree, select **Dynamics 365 for Operations\Table records**. 
6. Click **Add root**. 
7. In the **Table** field, enter or select a value. 

    > [!NOTE]
    > More than two application tables were offered now as this mapping uses all the metadata of the connected application that has been assigned for it. 

8. Click **Cancel**. 
9. Click **Validate**. 

    > [!NOTE]
    > We successfully bound elements of data model with items of data sources that are described by using details of metadata of the connected application that has been assigned for this mapping. 

10. Close the page. 
11. Close the page. 

When you need to evaluate this model mapping by using metadata of a different version application, register another connected application, assign it to this model mapping and validate it against new metadata.


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]

