--- 
# required metadata 
 
title: (ER) Import configurations from RCS
description: This topic provides information about how a user can import a new version of an ER configuration from RCS.
author: NickSelin
manager: AnnBe 
ms.date: 07/03/2019
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form:  
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2019-07-28 
ms.dyn365.ops.version: Version 7.0.0 
---
# (ER) Import configurations from RCS

[!include [banner](../../includes/banner.md)]

The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can import a new version of an Electronic reporting (ER) configuration from Microsoft Regulatory Configuration Services (RCS). In this example, you will select the version of the ER configuration that has been configured in an RCS instance and import it into the current instance for sample company, Litware, Inc. These steps can be performed in any company because ER configurations are shared among companies. To complete these steps, you must first complete the steps in the topic, [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md). To complete these steps, you must also have access to an RCS instance containing at least one ER configuration in either **Completed** or **Shared** status.

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**. 
2. Make sure that the configuration provider for the sample company, Litware, Inc., is available and marked as **Active**. If you don't see this configuration provider, complete the steps in the topic, [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md). 
3. If you have no RCS environment provisioned to your company, click **Regulatory services – Configuration** external link and follow the instructions to provision an RCS environment. 
4. Click **Electronic reporting parameters**. 
5. Click the **RCS** tab. 
6. If RCS environment has been already provisioned to your company, use presented on the page URLs to access it. 
7. Close the page. 

## Register a new ER repository. 
1. In the list, mark the selected row. 
2. Select Litware, Inc. provider. 
3. Click Repositories. 
4. Click Add to open the drop dialog. 
5. In the Configuration repository type field, enter 'RCS'. 
6. Click Create repository. 
7. In the RCS environment display name field, enter or select a value. 
8. Select the desired RCS instance. Note that you can have several of them. 
9. Click OK. 

## Import ER configurations from RCS based repository
1. Click **Show filters**. 
2. Enter a filter value of "RCS" on the **Name** field using the **begins with** filter operator. 
3. When you open the selected repository, on the **Connect to Regulatory Configuration Services** page, click **Click here to connect to Regulatory Configuration Services** link. 
4. Click **Open**. 
5. Click **Close**. 
6. Select the desired version of ER configuration and click **Import** to bring it in the current instance.

