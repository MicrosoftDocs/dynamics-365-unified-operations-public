---
title: (ER) Import configurations from RCS
description: This article provides information about how a user can import a new version of an ER configuration from RCS.
author: kfend
ms.date: 07/03/2019
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2019-07-28
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: 
---
# (ER) Import configurations from RCS

[!include [banner](../../includes/banner.md)]

The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can import a new version of an Electronic reporting (ER) configuration from Microsoft Regulatory Configuration Services (RCS). In this example, you will select the version of the ER configuration that has been configured in an RCS instance and import it into the current instance for sample company, Litware, Inc. These steps can be performed in any company because ER configurations are shared among companies. To complete these steps, you must first complete the steps in the article, [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md). To complete these steps, you must also have access to an RCS instance containing at least one ER configuration in either **Completed** or **Shared** status.

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**. 
2. Make sure that the configuration provider for the sample company, Litware, Inc., is available and marked as **Active**. If you don't see this configuration provider, complete the steps in the article, [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md). 
3. If you have no RCS environment provisioned to your company, select **Regulatory services – Configuration** external link and follow the instructions to provision an RCS environment. 
4. Select **Electronic reporting parameters**. 
5. Select the **RCS** tab. 
6. If RCS environment has been already provisioned to your company, use presented on the page URLs to access it. 
7. Close the page. 

## Register a new ER repository. 
1. In the list, mark the selected row. 
2. Select Litware, Inc. provider. 
3. Select Repositories. 
4. Select Add to open the drop dialog. 
5. In the Configuration repository type field, enter 'RCS'. 
6. Select Create repository. 
7. In the RCS environment display name field, enter or select a value. 
8. Select the desired RCS instance. You can have several of them. 
9. Select OK. 

## Import ER configurations from RCS-based repository
1. Select **Show filters**. 
2. Enter a filter value of "RCS" on the **Name** field using the **begins with** filter operator. 
3. When you open the selected repository, on the **Connect to Regulatory Configuration Services** page, select **Select here to connect to Regulatory Configuration Services** link. 
4. Select **Open**. 
5. Select **Close**. 
6. Select the desired version of ER configuration and select **Import** to bring it in the current instance.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
